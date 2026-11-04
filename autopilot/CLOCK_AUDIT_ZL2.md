# CLOCK_AUDIT_ZL2: path-index vs real-seconds audit of ZL-2's analyses and of the engine's time hooks

Author ZL-2, 2026-11-04. Scope note l2vast/ds3/prereg/CLOCKAUDIT_scope.md sha256 82c8c1fb0ee1866fbbdd6b661f38726f36a462a0921291486d512ae4173af12c (DECISIONS.md). Documentation of an error class and its re-checks; no PASS claims; nothing live.
**The fact:** the 1-second path of the reference engine (SS, SH, SL, SC in /mnt/l2/l2vast/ds3_g2_redo, d.kin, d.kflat, R['kx0'], trade te/tx) holds ONLY seconds with prints, about 1,430 rows per real hour overall. An index difference is therefore NOT a duration: 1,800 indices after a cut span a median 60.2 real minutes in Asia, 47.6 London, 30.1 pre, 30.1 NY-AM, 30.9 NY-PM, 30.8 close (10,128 / 8,462 / 2,223 / 10,145 / 6,838 / 110 cuts). Real seconds are SS[idx] (epoch). Index arithmetic is fine for ORDER (which row comes first, overlap tests) and wrong for DURATION.
**Method:** grep of all ZL-2 scripts (zones3/discover q4/q5/q8/q9/q10/q12/dist_zl2 modules and fade_tools/multi_harness/book_harness; dis_x; scratchpad scripts) for index plus 60 / 3600 / N-minutes arithmetic, division of index differences, and windows compared with clock quantities; each hit was read; the engine hooks were read in code (section 2).

## 1. Analyses
| analysis | time quantity | unit used | correct? | effect if wrong / action |
|---|---|---|---|---|
| T-FADE FadeHarness, MultiHarness, BookHarness (zones3/discover fade_tools.py, multi_harness.py, book_harness.py) | time stops (tstop_s), flat time, entry delay (+1 s), ATR bars | real epoch seconds: np.searchsorted(SS, sec + 1 + tstop_s), flat via epoch of 16:55 ET, idx_at = searchsorted(SS, sec) - 1, bars from SS // 60 | correct | none |
| DIS-T bundle, DIS-V rows, dist_zl2_* (candidate time stops 1,800 / 3,600 / 7,200 s) | time stops | real seconds through tstop_s | correct | none |
| Q4 (q4_tools.py) | weekly change-point statistics | label weeks | correct | none |
| Q5 hold shapes (q5_zl2_run.py, _prep.py, _kernel.py) | hold bound, 8-hour cap, hold seconds | t_bound and t_in + 8 x 3600 converted by searchsorted(SS, epoch); hold_s = SS[kx] - t_in | correct | none |
| Q8 day-type switch (q8_zl2_feat.py, _series.py) | entry minute of day, label day | ET minutes from epoch; labday(ets + 60) | correct | none |
| Q9 session chain, Q10 earnings books (q9_zl2_*.py, q10_zl2_*.py) | signal times, shifted-trigger placebo shifts | 1-minute bar epoch + 60; shift = minutes x 60 added to epoch seconds | correct (the signed-shift look-ahead is a different issue, AUDIT_PLC.md) | none |
| Q12 bar types (q12_zl2_sim.py) | decision second, 30-300 s shifts, ET minute | tsig // 1e9 + shift (seconds), ET minute from epoch | correct | none |
| DIS-V forward drawdown | block length | weeks | correct | none |
| DIS-X APX (apx_*.py) | 1-min fills, busy-until, 5-min ER, flat time | epoch seconds of the box 1-minute series (ts + 60, ts // 300) | correct | none |
| DIS-Y / DIS-Z (disy*, disz_*) | state variables, autocorrelation lags, quarters | 1-minute bars (epoch), label days | correct | none |
| DIS-AB attribution (ab_lib.py, ab_run.py) | A06 half-hour slots, B02 overnight range, switches | engine hooks (real ET from SS[kin]; overnight windows by searchsorted on epoch) | correct | none |
| DIS-AE TH out-of-sample (ae_*.py) | TH window 5 s / 10 s / 30 s, arm in points, periods | th_loss_w selects pulled-support columns built on TIMESTAMPS (l2feat W(c, Tn, w): searchsorted(ts, Tn - w x 1e9)); periods are label days | correct | none |
| **DIS-AI mechanism (ai_path.py, ai_dec.py, ai_reg.py)** | minutes to the -30 arm (t30), mean hold (tx - te) | **path-index difference divided by 60** | **WRONG for durations**; probabilities, outcomes, per-cut deltas and the decomposition tables use order only and are correct | recomputed: mean real minutes to arm 205 / 125 / 78 / 37 (2023-26; was 89 / 51 / 31 / 18); mean hold real: cut ON 251 / 158 / 95 / 48 min vs OFF 310 / 214 / 145 / 77 (ratio 0.81 / 0.74 / 0.65 / 0.62; was 119 / 70 / 42 / 24 vs 160 / 103 / 67 / 39, ratio 0.74 / 0.68 / 0.62 / 0.62); notices appended to DS3_TH_MECHANISM (and the SLOT_CHANNEL mean-hold sentence) |
| **DIS-AK slot channel (ak_run.py tstop, skipmask)** | time stops N minutes after entry; pause after a cut | **kx = kin + 60 N; window (kx, kx + 60 N] in index units** | **WRONG** (time stops and pause); the extra-trade classification, (c) emulation (window = cut exit to plain exit, order only) and decompositions are correct | time stops rerun with real seconds (ak_fix.py): conditional totals $1.24M / 1.63M / 1.26M / 1.61M for 20 / 30 / 45 / 60 min (was 1.40 / 1.49 / 1.78 / 1.89); conclusion unchanged (all below cut and TH off); pause rows rebuilt (RECON_PAUSE.md); amendment appended to DS3_SLOT_CHANNEL |
| **DIS-AR gates (ar_stage2.py pause, via ak_run.skipmask)** | pause 15 / 30 / 60 min after a cut | index units | **WRONG for the pause rows only**; gate grid, blocked-entry value, placebo, rolling-origin do not use durations | pause rows restated (real clock) in the DS3_GATES amendment |
| **DIS-BA frontier (rf_lib.pause_mask, rf_fix.py, rf_an.py)** | pause 15 / 30 min | index units | **WRONG for the 60 pause cells** (30 min = 60 real min in Asia) | all pause cells rerun with the real clock (rp_front.py, 131 cells on two bases); frontier membership 14 -> 18 cells; DS3_RISK_FRONTIER amendment 2, v3 CSVs |
| DIS-BA other dials (PE weight, net-lot cap, gate) | none | lots, points, R multiples | correct | none |
| DIS-BJ live windows (bj_lib.py) | entry windows 09:30-09:59, 18:00-18:04 | ET hour-minute of the signal epoch second | correct | none |
| DIS-BE config audit, DIS-AX (BASE-4's) | n/a / latency k seconds | n/a / dense per-second price array | not ZL-2's; DIS-AX adds k seconds to a trigger second and searches SS for the fill | none found |

## 2. Engine hooks that take time arguments
| hook | time argument | unit in the engine | evidence |
|---|---|---|---|
| ov extra_skip | none (row mask); any window is built by the caller | n/a | d7lib._engine; callers must convert minutes with SS (RECON_PAUSE.md) |
| ov inject (T.inject kind 'time', 'cut', 'take') | kx = exit SECOND INDEX into SS; px = path price at kx | path INDEX, no clock logic | d7_v13t.inject docstring; a caller turning "N minutes" into kx must use searchsorted(SS, SS[kin] + 60 N) (ak_fix.py) |
| th_loss_w (5 s / 10 s / 30 s) and th_loss_mult | trailing window of pulled support | REAL seconds: window sums by searchsorted on the feature timestamps in ns | l2feat/l2f_build.py:65-66 (W), :186 (pulled_sup{w}); lc_rows.fire_mask uses p{w} columns |
| th_loss_arm | adverse points | points (no time) | d7lib._exits_l2sl |
| U7 blackout (u7min = 30) | minutes after a cut | REAL seconds: SS[kin] < SS[cut] + minutes x 60 | d7_v13x._blackout_side |
| A06 half-hour slots, B02 range | ET clock | REAL (epoch from SS[kin]; overnight window by searchsorted on epoch) | lots_ts2.py:17-48 |
| kflat (16:55 flat), session labels | ET clock | REAL (library built from epoch) | ss2/thp library; book_harness.flat_idx |
| 70/30 add fill ("the second after price trades through"), PE 45-s confirmation | next path row; 45 s events | next ROW with prints (a fill needs a print, so approximately a real "next second"); 45-s events come from epoch-based bar/event tables | ss2_lib._b73 / pe_kernel; not a duration error but a semantic note |
| lock engine (_trig_book) | loops over path indices to find the trigger index | order only; day / week keys are label day / ISO week | oc_lib.py:17-31 |
| ov lock phase (week-key shift) | days | label days | sizer_harness phase |

## 3. Verdict and what was re-run
The error class occurs in four of my own analyses, all through one idiom (index plus 60 x minutes): the TH-mechanism durations (AI), the time stops and the re-entry pause (AK), the pause rows of the gate study (AR) and of the risk frontier (BA). Everything else uses epoch seconds or order only. Re-runs: time stops (ak_fix.py), pause cells on two bases (rp_front.py), time-to-arm and hold durations (this audit), all with real seconds; corrections appended to DS3_TH_MECHANISM, DS3_SLOT_CHANNEL, DS3_GATES, DS3_RISK_FRONTIER; headline numbers that moved by more than 2%: the pause-30 cells (HOLD maxDD $62.4k -> $84.5k), the pause-15 cells (mean +6%), frontier membership; unchanged: every pause-0 result and every conclusion about the gate interaction, the time-stop verdict, the TH decomposition.
Remaining exposure outside ZL-2's files: any other analysis that adds minutes to d.kin or R['kx0'] (for example Z3's DIS-AT outage replay, whose exit-type mislabel was already corrected); I did not audit other agents' code.
