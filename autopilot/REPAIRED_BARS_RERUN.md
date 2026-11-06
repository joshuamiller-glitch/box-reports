# REPAIRED_BARS_RERUN - re-simulation of finalists on bad-print-repaired 1-minute bars (coordination page; CHAR-C, 2026-11-06; prereg-free audit; research only, no PASS, nothing live)
Trigger: ZL-1's GC reconciliation (1,334 bad bars = 0.028% flatter the GC integer-lot book by ~$6.15k through spurious target/stop hits). Repaired bars, sha256 and the helper: REPAIRED_BARS_PATHS.md (rule cc_audit v1, K = 10 sigma + 4 ticks; originals untouched). Template for the companion note: WATCH_GC_TREND_SPEC_COMPANION.md.
Split (lead): CHAR-C = T-INSTR-2 stage-2 finalists 6E/6J/CL/ES/RTY/YM + this page; S4a = daily + R6 + CL Donchian watch cell; CHAR-A = T-FIND map / learned-rule finalists ES/RTY/YM/NQ; ZL-1 = GC/ZN/ZB/MBT/BTC/NKD books and LRS finalists; Z1 = block-B survivors + native books; ZL-2 = watch specs / plugin thresholds. Other owners: append your section below with `>>` (one table in the same columns).

## 1. CHAR-C results: T-INSTR-2 stage-2 finalists (30 / 30 / 30 / 30 / 12 / 12 cells)
Method: for every finalist in the owner's stage2.pkl (6E, 6J, CL: /mnt/l2/l2vast/instr2_<sym>/stage2.pkl, pipeline t2cl; ES: ds3_instr2_z1/ES/stage2.pkl; RTY, YM: ds3_instr2_z2/<sym>/stage2.pkl), the SIGNALS are regenerated from the bars with the owners' own code (ATR, Keltner/Supertrend bands, sessions) and the bracket trades are re-simulated with the same trade rules and costs (E.build_trades / the owner's cell_trades), once on the ORIGINAL bars and once on the REPAIRED bars; windows and gate come from instr2_eval.evaluate (equal-risk lots, carry weeks dropped). Reproduction check: my rerun on the original bars equals the saved stage-2 window means (L6M, HOLD, PRE, X', within 0.5% or $1) in 30/30, 30/30, 30/30, 30/30, 12/12, 12/12 cells, so the engine is the owners' engine. Code: l2vast/ds3/code/find_c/{rb_t2.py, rb_t2_full.py, rb_z.py, rb_cmp.py, rb_cmp2.py}; outputs /mnt/l2/l2vast/find_c/review/rb_*.pkl. This is the fast pass (windows + gate flags, no placebo / walk-forward / family p); a full evaluate with placebos was run for the one cell whose gate changed to PASS.
| instrument (pipeline, bars) | finalists | repro | tolerant-gate passers orig -> repaired | cells with a gate-flag change | cells with a different trade count | median / max abs change $/wk: L6M | HOLD | PRE | X' | saved labels (all FAILS) change? |
|--|--|--|--|--|--|--|--|--|--|--|
| 6E (t2cl, te2 raw + roll offsets) | 30 | 30/30 | 6 -> 4 | 3 | 12 | 0 / 12 | 5 / 48 | 15 / 46 | 19 / 115 | no: all 30 FAIL before and after (the 2 tolerant losses are cell 21 and are already failing placebo p .54-.63) |
| 6J (t2cl, te2) | 30 | 30/30 | 5 -> 3 | 2 | 30 (median +4 trades) | 2 / 146 | 4 / 74 | 3 / 37 | 6 / 70 | no: all FAIL; the 2 tolerant losses are 6J cell 129 keltner london (already FAILS: min sample PRE 45/60) |
| CL (t2cl, te2) | 30 | 30/30 | 13 -> 14 | 1 | 12 | 0 / 134 | 0 / 59 | 0 / 14 | 0 / 97 | no: cell 7 keltner_flip nyam T120 becomes a tolerant PASS (L6M -53 -> +81, HOLD +389 -> +442), full evaluate on repaired bars: FAILS, placebo p_book 0.65 > .10, family p 0.74 (saved 0.89), walk-forward not positive (6m +30/wk p_rand .06, 12m -81/wk) |
| ES (Z1, xbars = te2 raw) | 30 | 30/30 | 22 -> 22 | 0 | 19 | 0 / 153 | 0 / 111 | 13 / 80 | 0 / 126 | no (all FAIL; the 'K b1 ema34 atr20 m1.0 against close' PRE +175 -> +101 and the PB 'b5 st10_3 ema10 pre' L6M +858 -> +705 are the largest) |
| RTY (Z2, xbars; 3.07M bars, longer than te2: the rule is applied to the xbars themselves) | 12 | 12/12 | 10 -> 10 | 0 | 4 | 0 / 206 | 1 / 78 | 6 / 85 | 0 / 52 | no (RTY 'K b10 ema8 atr14 m2.0 nyam A2 1.5 T30' L6M +986 -> +780 largest) |
| YM (Z2, xbars = te2 raw) | 12 | 12/12 | 9 -> 9 | 0 | 5 | 0 / 72 | 1 / 189 | 44 / 141 | 1 / 158 | no (YM 'b2 ema13 atr10 m0.5 against pre A2 2.0 T120' HOLD +318 -> +129, PRE -361 -> -221 largest) |
Reading: (1) the effect of bad prints on the 2023-26 windows is small for the median finalist (median change $0-19/wk) but not negligible for individual cells (up to $100-200/wk in a window, mostly where a wide ATR stop or a Keltner band was set by a spike); on the 6J finalists every cell gets +0 to +9 trades because the repaired ATR moves the bands. (2) No label changes: no finalist was cleared before, and none is after. The 6 gate flips are 3 cells losing the tolerant pass (6E 21, 6J 129, 6E 4 min-sample) and 1 cell gaining it (CL 7), none of them survives the placebo/walk-forward/family tests. (3) The ES, RTY, YM window numbers on the repaired bars are within $200/wk of the originals in every window of every cell.
Cells whose gate flags change (all in the rb_cmp output): 6E keltner_flip pre T120 cell 21 (two parameter sets; tolerant True -> False: X' -216 < -0.5 MDE; persistence .75 -> .625), 6E keltner_flip pre T120 cell 4 (min sample), 6J keltner_flip london 120 and 60 cell 129 (NOW-ONLY fails after repair: L6M +29 -> -8, +27 -> -10), CL keltner_flip nyam T120 cell 7 (False -> True, see above; still FAILS).

## 2. Other owners (append below)
| owner | scope | status |
|--|--|--|
| S4a | daily + R6 + CL Donchian watch cell | pending (CL Donchian is a daily 15:55 rule on 1-min closes/highs/lows: the repaired CL bars are feed `te2`/`t2min`; the spec thresholds come from the S4a CL series) |
| CHAR-A | T-FIND map / learned-rule finalists ES RTY YM NQ | pending (frame mapping: T2F tick-map frames = te2 raw; NQ/RTY LRS frames partly instr1m adjusted; see REPAIRED_BARS_PATHS.md) |
| ZL-1 | GC ZN ZB MBT BTC NKD books + LRS | GC done (ZL-1 reconciliation); others pending |
| Z1 | block-B survivors, native books | pending |
| ZL-2 | watch specs / plugin thresholds | pending |

## 3. Frozen specs that need a dated companion note (so far)
* GC trend: already done by ZL-1 (WATCH_GC_TREND_SPEC_COMPANION.md; thresholds unchanged, PRE/X' header figures differ).
* From the CHAR-C share: none. No frozen spec is built on a 6E/6J/CL/ES/RTY/YM stage-2 finalist; all finalists above are FAILS or REGIME-less leads, so nothing needs a companion note from this part.
* The frozen watches that sit outside this share are assessed by their owners; my read from the specs, to be confirmed by them: RTY premarket (1-s mid from mbp-10, price not from 1-min bars: not affected by 1-min bad prints), NQ PDL (L2 mid version unaffected; the bar-based replay uses 1-s bars: bad-print rule not defined for 1-s, flag to CHAR-A), Monday long (open of the first minute and the 16:55 bar: need a check of whether those two bars were flagged on any Monday), CL Donchian (daily rule on 15:54 close and day high/low through 15:54: a spike high changes the channel for 20 days: S4a to rerun), MBT Keltner (10-minute bars from MBT 1-min, additively adjusted instr1m feed: ZL-1/S4b to rerun on instr1m repaired).
## Caveats
* Fast pass without placebo/walk-forward/family p; the verdict labels of the saved stage-2 results were not recomputed except for CL cell 7, so a label change is excluded only for cells without a gate flip by the argument that the saved labels all fail on placebo/family tests that a $0-20/wk change would not flip (verified for the flipped cells; not individually rerun for the other 114 cells).
* Entry prices are the next-bar open (unchanged by the repair except when the open itself was clamped); the repair clamps only isolated >10 sigma excursions.
* 13-year percent-frame year tables were not rerun here.

## NOTICE (CHAR-C, 2026-11-06T06:19Z): my write at 06:17:48Z replaced this file and DROPPED sections that other owners had already appended (CHAR-A REPAIRED-FIND, ZL-2 six-spec rerun, possibly S4a). My error (I wrote with `>` after an existence check that I did not act on). Owners: please re-append your section below with `>>`; your MORNING.md / DECISIONS.md lines of 06:16-06:17Z still carry the summaries (CHAR-A: 126 book + 18 LRS finalists, 30 tick cells, NQ_PDL replay; ZL-2: six specs, only NQ_PDL needs a companion note, 551->553 trades; S4a: FIND_DAILY 42/408 cells move, 6J Donchian-60 -> NULL). Section 2 table above is superseded by those.

## REPAIRED-FIND (CHAR-A slice, 2026-11-06T06:17Z): T-FIND books and WATCH cells re-run on repaired bars. Method: 1-min = CHAR-C repaired copies /mnt/l2/l2vast/find_c/cache_c/<SYM>.npz (DATA_BAD_PRINTS.md rule); 1-s = my scan of instr_1s with the same rule (neighbours within 3 s, sigma = 1.4826 x block median |close change| of the previous 3,600 bars), clamped copies in /mnt/l2/l2vast/ds3/out/find/instr1s_repaired/. Same signals, specs, costs, seeds, 100 placebo worlds; originals untouched.
**Verdict: no label, family result or frozen spec moves; only marginal gate flips and learned-rule retrains.**

### 1-s bad-print scan (2023-08..2026-10-16)
| product | bars | confirmed-neighbour bars | BAD | share | max excursion (ticks) |
|--|--|--|--|--|--|
| ES | 36.1M | 30.0M | 6,293 | 0.021% | 90 |
| NQ | 40.1M | 34.4M | 4,714 | 0.014% | 203 |
| RTY | 21.0M | 15.4M | 1,094 | 0.007% | 122 |
Some flagged bars on a prints-only 1-s tape may be genuine one-lot spikes; the repair clamps into the 10-sigma band, so it is conservative.

### Map statistics on the repaired 1-min bars (descriptive pages not recomputed in full)
ES / NQ / RTY / YM: max |change| of the pooled lag correlation over horizons 1/5/15/30 min x 6 sessions = 0.0004 / 0.0014 / 0.0050 / 0.0011 (all at the 1-minute pre-market cell); max |change| of a variance ratio 0.0008 / 0.0017 / 0.0037 / 0.0013; max |change| of a level-reaction / continuation / gap / day-type event rate 0.0069 / 0.0047 / 0.0086 / 0.0077. The Monday legs of ES and NQ (label-day open to 16:55 close) are identical to the last digit (NQ Monday FULL mean 17.54 bps, sd 120.57, 2023+ mean 31.52; ES 12.71 / 97.85 / 23.62), so WATCH_MONDAY_LONG_SPEC.md and AMENDMENT_1 stand.

### 1-min finalists re-run on repaired bars: 126 book cells (top-30 by min(L6M,HOLD) + all tolerant cells per instrument, ES/RTY/YM) and 18 learned-rule cells (top-6 per instrument, instr2/lrs.py)
* Books (126): median |change| in L6M / HOLD / PRE / X' = 0 / 0 / 0 / 0 $/wk; maximum |change| L6M 76, HOLD 206 $/wk; 37 books have a different trade count (max 6 trades). Sign flips: L6M 0, HOLD 2 (all marginal cells near zero, listed below); tolerant-gate flips 4.
* Learned rules (18; trees retrained on repaired features, so the trade set changes): maximum |change| L6M 831, HOLD 477 $/wk; sign flips L6M 8, HOLD 5; tolerant flips 0. This is the sensitivity of a retrained tree to 0.003% of its input bars, not a result.
* The four tolerant flips are YM NY-PM 5-minute fades at the gate's edge (PRE -216 -> -215 $/wk against the -0.5 MDE line; L6M and HOLD unchanged); the best-family-p cells of ES, RTY and YM that are in the finalist list (the YM VR NY-PM 5-min z1.5 f0.5 cell, p .15, is) do not change tolerance or sign. None of these was ever a lead.

Every cell that flips sign in L6M or HOLD, or flips the tolerant gate (original -> repaired, $/wk, carry dropped):
| cell | L6M | HOLD | PRE | tolerant |
|--|--|--|--|--|
| T2F_ES|LRS_nyam_rev_h30|seed0 | +539 -> +346 | +81 -> -44 | -636 -> -958 | False -> False |
| T2F_ES|LRS_pre_rev_h15|seed2 | +258 -> -111 | -21 -> -229 | -642 -> -779 | False -> False |
| T2F_ES|LRS_nyam_rev_h15|seed2 | +349 -> -106 | -94 -> -115 | -1870 -> -1601 | False -> False |
| T2F_RTY|LRS_pre_rev_h60|seed0 | +628 -> +941 | +264 -> -160 | -0 -> -63 | True -> True |
| T2F_RTY|LRS_close_rev_h30|seed2 | +42 -> -44 | +59 -> -169 | -437 -> -354 | False -> False |
| T2F_RTY|LRS_pre_rev_h30|seed2 | +121 -> -128 | -77 -> -183 | -130 -> -387 | False -> False |
| T2F_YM|AC_nypm_5m_all|fade|z02.0_f0.5_tm2.0 | +458 -> +458 | +238 -> +238 | -216 -> -215 | True -> False |
| T2F_YM|VR_nypm_5m|fade|z02.0_f0.5_tm2.0 | +458 -> +458 | +238 -> +238 | -216 -> -215 | True -> False |
| T2F_YM|VR_nypm_15m|fade|z01.5_f0.5_tm2.0 | +328 -> +261 | +40 -> -5 | -465 -> -469 | False -> False |
| T2F_YM|VR_nypm_5m|fade|z02.0_f1.0_tm2.0 | +166 -> +166 | +34 -> +34 | -150 -> -150 | True -> False |
| T2F_YM|AC_nypm_5m_all|fade|z02.0_f1.0_tm2.0 | +166 -> +166 | +34 -> +34 | -150 -> -150 | True -> False |
| T2F_YM|VR_nypm_15m|fade|z01.5_f0.5_tm1.0 | +422 -> +355 | +31 -> -36 | -481 -> -485 | False -> False |
| T2F_YM|LRS_nyam_rev_h60|seed2 | +98 -> -426 | +397 -> +250 | -528 -> -580 | False -> False |
| T2F_YM|LRS_london_mom_h60|seed0 | -45 -> -133 | +76 -> -205 | -299 -> -290 | False -> False |
| T2F_YM|LRS_pre_rev_h15|seed0 | -47 -> +5 | +103 -> +258 | -402 -> -428 | False -> False |
| T2F_YM|LRS_london_mom_h60|seed2 | -11 -> +74 | -83 -> +122 | -334 -> -353 | False -> False |
| T2F_YM|LRS_london_mom_h60|seed1 | +1 -> -55 | -115 -> -222 | -354 -> -274 | False -> False |

### 1-s WATCH-relevant cells (T2F1B books with the corrected simulator; originals = the '_1sfix' cells)
| cell | L6M | HOLD | PRE | X' | n |
|--|--|--|--|--|--|
| ES b_PD_nyam_burst_h60|m1.0_tNone | +474 -> +474 | +605 -> +605 | -971 -> -971 | -779 -> -779 | 414 -> 414 |
| RTY b_PD_pre_burst_h1800|m1.5_t1.0 | +375 -> +375 | +82 -> +82 | +13 -> +13 | +35 -> +35 | 95 -> 95 |
| NQ b_PD_pre_burst_h1800|m1.0_tNone | -341 -> -341 | -330 -> -330 | -12 -> +141 | +61 -> +61 | 94 -> 94 |
| NQ b_PD_pre_burst_h1800|m1.0_t1.0 | +130 -> +130 | -35 -> -99 | +26 -> +63 | +86 -> +86 | 94 -> 94 |
| NQ b_PD_pre_burst_h1800|m1.5_tNone | -82 -> -82 | -192 -> -192 | +13 -> +13 | +107 -> +107 | 94 -> 94 |
| NQ b_PD_pre_burst_h1800|m1.5_t1.0 | -70 -> -70 | -45 -> -45 | +92 -> +92 | +149 -> +149 | 94 -> 94 |
| NQ b_PD_pre_burst_h1800|m2.0_tNone | -48 -> -48 | -93 -> -93 | -39 -> +4 | +107 -> +107 | 94 -> 94 |
| NQ b_PD_pre_burst_h1800|m2.0_t1.0 | -45 -> -45 | -36 -> -36 | -30 -> -7 | +107 -> +107 | 94 -> 94 |
| NQ b_PD_nyam_all_h30|m1.0_t1.0 | +199 -> +199 | +418 -> +418 | +8 -> +8 | -120 -> -120 | 578 -> 578 |
All 30 tick-scale book cells (ES 6, RTY 12, NQ 12): trade counts identical, L6M and X' identical, HOLD changes <= $64/wk (NQ), PRE changes <= $153/wk (NQ pre-market 1800 s variants, all with negative HOLD), tolerant flips 0, placebo p_book changes <= .05 on every cell. ES prior-day-burst 60 s, RTY pre-market 1800 s and NQ NY-AM 30 s keep their windows exactly. NQ_PDL bar-based replay on repaired bars: events 561 (unchanged), trades 551, L6M -404 / HOLD -119 / PRE -254 (was -239) / X' -325, per-trade -$8.5 (was -$8.9), MNQ sd $12.86 (was $12.91), overlap with the L2 version 78.2% (was 77.9%), weekly corr to the L2 version .561 (was .573): the frozen thresholds of WATCH_NQ_PDL_SPEC.md (sd $12.91, kill -2 sigma sqrt(n)) change by 0.4% and are NOT amended.
**Which labels or frozen specs move: none.** WATCH_RTY_PREMARKET_SPEC.md (tick h1800 cells identical), WATCH_NQ_PDL_SPEC.md (thresholds unchanged), WATCH_MONDAY_LONG_SPEC.md and AMENDMENT_1 (Monday legs identical); the corrected 1S-FIX labels and every 'does not clear' conclusion stand. Files: /mnt/l2/l2vast/ds3/out/find/{ES,RTY,YM}/repaired_rerun.csv, repaired_rerun_all.csv, repaired_tickb.csv; code rerun_1min.py, repair_1s.py, scan_1s_badprints.py, tick_books_rep.py, nq_pdl_replay_rep.py in l2vast/ds3/code/find/.

## ZL-2: the six WATCH specs re-derived on repaired bars (2026-11-06; rule cc_audit v1, loader find_c/repaired.py; plugin backtests, no spec file touched; code l2vast/ds3/code/watch/rerun_repaired_monday*.py plus the blocks in README_WATCH.md) [RE-APPENDED after the 06:17:48Z overwrite]
| watch (spec) | bar source the spec/plugin uses | repaired-bar rerun | delta to the frozen history number / threshold | companion note needed? |
|--|--|--|--|--|
| RTY_PREMARKET | tick / 1-s tables (spread-masked quote rows) | N/A: no 1-min bars; the cc_audit rule is defined on 1-min bars with 60-s neighbours | none | no |
| MONDAY_LONG (+AMEND1) | tables/NQ/1min (mid, mid_first, mid_lo, mid_hi) | rule applied to the table front-month series 2023-01..2026-10: 355 bars flagged and clamped; 185 Mondays rerun | 0 of 185 Mondays change (max abs delta 0.0 bps; mean 30.216 bps both; sd 104.18 both; variant B mean 25.42 both; B stops 8 both). Frozen sigma 120.6 input: Monday FULL-leg sd on te2 raw vs repaired, 677 Mondays 2013-2026, identical (120.34 both; 2023+ gross mean 31.52 both) | no |
| CL_DONCHIAN | find_c/cache_c/CL.npz (already the repaired te2) | plugin run on RAW cache_te2 vs repaired, 2013-2026: 3,547 days both | identical to the cent: cum $147,485, maxDD $48,338, 0 days differ. History maxDD is above K1 $47,782 by construction of the like-for-like comparison (S4a: K1 is 1-5% conservative); README's earlier '$156.0k' predates the 2026-11-06 plugin fix | no |
| MBT_ASIA_KELTNER | ds3_instr/MBT_1m.npz adjusted frame (oa..ca) | plugin run on cache_c_feeds/instr1m/MBT.npz (142 bars flagged) | PRIMARY: 165 trades both, cum $22.83 both, mean $0.138/trade, max per-trade change $0.002. S1 $27 -> $26, S2 $14 -> $14, CTRL -$9 -> -$12, S3 250 -> 252 trades, $23.46 -> $24.33 (secondary, never decisive) | optional |
| NQ_PDL | ohlcv-1s bars (NQ_S*.npy) | 265 flagged 1-min minutes since 2023-08 clamped into the 1-s history (approximation); plugin rerun 2023-08..2026-10-16 | trades 551 -> 553 (9 only-raw, 11 only-repaired, 156 of 542 common change net); mean -$8.93 -> -$9.90 per NQ lot (-$1.69 -> -$1.79 per MNQ); total MNQ -$930.5 -> -$987.6; sd 12.92 -> 12.90 (kill constant 12.91 unchanged) | YES: written, autopilot/WATCH_NQ_PDL_SPEC_COMPANION.md sha256 9385ff11b2ce193bb0b52a36f984d67072d3e3454d35aeda7d49ab0da0a00cdf |
| GC_TREND | find_c/cache_c/GC.npz (repaired te2) | cite ZL-1 (WATCH_GC_TREND_SPEC_COMPANION.md; DS3_INSTR2_GC.md); my plugin: integer-lot net 2023-04..2026-10-16 -$10,952 repaired vs -$4,799 raw | thresholds identical within $1/wk; PRE -$337, X' -$265 | already written by ZL-1 |
Caveat: the NQ_PDL clamp is a 1-s analogue of the 1-min rule (1-s bars inside a flagged 1-min bar clipped to the repaired band); a native 1-s bad-print rule would be needed for a final figure.

# S4a section (daily programs) - re-appended 2026-11-06 after the page was overwritten with '>' at 06:17:48Z


## REPAIRED-DAILY (S4a, 2026-11-06): the daily programs on original vs repaired bars
Read first: the repaired 1-minute copy that CHAR-C publishes for the te2 feed (find_c/cache_c_feeds/te2/<SYM>.npz) is byte-identical to find_c/cache_c/<SYM>.npz (REPAIRED_BARS_PATHS.md), which is the file all of my daily programs (FIND_DAILY, rates momentum, CL stress, REPLICATION R4/R5, COSTCAL daily) were built from; DAILY-R6 repaired its 16 products in the build with the same rule (cc_audit v1). So the published daily numbers are already the REPAIRED numbers; this block runs the daily books on the ORIGINAL bars (cache_te2 for the 11 FIND_DAILY instruments; the raw ohlcv1m for the 16 R6 products, repair switched off) and reports original vs repaired. Code l2vast/ds3/code/t2s4a/repaired_cmp.py, repaired_k.py (env DAILY_OUT / DAILY_SRC / DAILY6_OUT / DAILY6_REPAIR); data /mnt/l2/l2vast/ds3_daily_orig, ds3_daily6_orig (originals untouched).
#### FIND_DAILY (408 cells; 200 worlds; family p random-side)
Tolerant cells (union of the original and the repaired set; 37 cells):
| cell | net orig $ | net repaired $ | delta $ | maxDD orig $ | maxDD repaired $ | years+ orig / repaired | tolerant orig / repaired | family p orig / repaired |
|--|--|--|--|--|--|--|--|--|
| PORT DON_N100_SAR | 606517 | 609699 | +3183 | 306947 | 306947 | 11 / 11 | T / T | 1.000 / 1.000 |
| PORT MA_10_50 | 497372 | 497372 | +0 | 189882 | 189882 | 9 / 9 | T / T | 1.000 / 1.000 |
| PORT TSMOM_L126_vol | 476785 | 476785 | +0 | 455128 | 455128 | 9 / 9 | T / T | 1.000 / 1.000 |
| PORT TSMOM_L252_1lot | 273820 | 273820 | +0 | 247134 | 247134 | 9 / 9 | T / T | 1.000 / 1.000 |
| PORT MA_20_100 | 240421 | 240421 | +0 | 369628 | 369628 | 9 / 9 | T / T | 1.000 / 1.000 |
| PORT TSMOM_L63_vol | 225486 | 225486 | +0 | 564881 | 564881 | 10 / 10 | T / T | 1.000 / 1.000 |
| GC TSMOM_L126_vol | 219368 | 219368 | +0 | 158996 | 158996 | 9 / 9 | T / T | 1.000 / 1.000 |
| GC MA_10_50 | 169464 | 169464 | +0 | 124339 | 124339 | 10 / 10 | T / T | 1.000 / 1.000 |
| CL DON_N20_SAR | 145271 | 145271 | +0 | 47782 | 47782 | 9 / 9 | T / T | 1.000 / 1.000 |
| NKD DON_N100_SAR | 137664 | 137664 | +0 | 91162 | 91162 | 10 / 10 | T / T | 1.000 / 1.000 |
| GC NIGHT_L | 137365 | 137365 | +0 | 100944 | 100944 | 9 / 9 | T / T | 1.000 / 1.000 |
| GC DON_N20_SAR | 130307 | 132367 | +2060 | 161181 | 159121 | 9 / 9 | T / T | 1.000 / 1.000 |
| 6J DON_N60_SAR | 126374 | 109191 | -17183 | 51125 | 63536 | 9 / 8 | T / - | 1.000 / 1.000 |
| NKD MA_50_200 | 104423 | 104423 | +0 | 120103 | 120103 | 9 / 9 | T / T | 1.000 / 1.000 |
| 6E TSMOM_L126_vol | 98358 | 98358 | +0 | 83688 | 83688 | 10 / 10 | T / T | 1.000 / 1.000 |
| ES MR_k5_th1.5 | 89003 | 89003 | +0 | 26869 | 26869 | 11 / 11 | T / T | 0.343 / 0.333 |
| GC DON_N40_SAR | 85382 | 85382 | +0 | 158468 | 158468 | 9 / 9 | T / T | 1.000 / 1.000 |
| CL DON_N40_SAR | 82103 | 82103 | +0 | 74715 | 74715 | 9 / 9 | T / T | 1.000 / 1.000 |
| ES MR_k3_th1.5 | 80292 | 80292 | +0 | 35589 | 35589 | 9 / 9 | T / T | 0.985 / 0.985 |
| ES MR_k5_th1 | 76573 | 76573 | +0 | 50330 | 50330 | 11 / 11 | T / T | 0.990 / 0.990 |
| RTY NIGHT_L | 67037 | 67037 | +0 | 30912 | 30912 | 7 / 7 | T / T | 0.468 / 0.473 |
| CL TSMOM_L252_vol | 64771 | 64771 | +0 | 107253 | 107253 | 9 / 9 | T / T | 1.000 / 1.000 |
| CL TSMOM_L252_1lot | 63692 | 63692 | +0 | 107253 | 107253 | 9 / 9 | T / T | 1.000 / 1.000 |
| YM NIGHT_L | 59193 | 59193 | +0 | 62198 | 62198 | 9 / 9 | T / T | 0.955 / 0.955 |
| CL DON_N60_EX | 57678 | 57678 | +0 | 55494 | 55494 | 9 / 9 | T / T | 1.000 / 1.000 |
| 6E DON_N100_SAR | 55060 | 57335 | +2275 | 70191 | 70191 | 9 / 9 | T / T | 1.000 / 1.000 |
| MBT TSMOM_L126_vol | 53533 | 53533 | +0 | 14137 | 14137 | 4 / 4 | T / T | 1.000 / 1.000 |
| RTY DON_N60_SAR | 50432 | 50432 | +0 | 50034 | 50034 | 6 / 6 | T / T | 1.000 / 1.000 |
| 6E TSMOM_L126_1lot | 33583 | 33583 | +0 | 41958 | 41958 | 9 / 9 | T / T | 1.000 / 1.000 |
| MBT TSMOM_L252_vol | 28499 | 28499 | +0 | 18290 | 18290 | 3 / 3 | T / T | 1.000 / 1.000 |
| RTY WKND_L | 27739 | 27739 | +0 | 15544 | 15544 | 7 / 7 | T / T | 1.000 / 1.000 |
| MBT DON_N20_EX | 15056 | 11848 | -3209 | 31278 | 31278 | 3 / 3 | T / T | 1.000 / 1.000 |
| MBT DON_N100_SAR | 11558 | 11558 | +0 | 27760 | 27760 | 4 / 4 | T / T | 1.000 / 1.000 |
| MBT DON_N40_EX | 10585 | 10585 | +0 | 27146 | 27146 | 5 / 5 | T / T | 1.000 / 1.000 |
| MBT TSMOM_L126_1lot | 9442 | 9442 | +0 | 3398 | 3398 | 4 / 4 | T / T | 1.000 / 1.000 |
| MBT MR_k1_th1.5 | 5556 | 5556 | +0 | 7645 | 7645 | 3 / 3 | T / T | 1.000 / 1.000 |
| MBT TSMOM_L252_1lot | 4662 | 4662 | +0 | 3638 | 3638 | 4 / 4 | T / T | 1.000 / 1.000 |
Other cells with |delta net| > $5,000 (16):
| cell | net orig $ | net repaired $ | delta $ | maxDD orig $ | maxDD repaired $ | years+ orig / repaired | tolerant orig / repaired | family p orig / repaired |
|--|--|--|--|--|--|--|--|--|
| 6J DON_N60_EX | 134185 | 118451 | -15734 | 36088 | 42997 | 9 / 9 | - / - | 0.856 / 0.990 |
| 6J DON_N40_EX | 50761 | 35803 | -14958 | 46535 | 46535 | 8 / 8 | - / - | 1.000 / 1.000 |
| 6J DON_N20_SAR | -5066 | -19605 | -14539 | 55701 | 59498 | 7 / 6 | - / - | 1.000 / 1.000 |
| ZB DON_N60_SAR | -523 | 13614 | +14137 | 114410 | 109153 | 8 / 8 | - / - | 1.000 / 1.000 |
| PORT DON_N20_EX | -9497 | -23319 | -13822 | 277213 | 266654 | 7 / 7 | - / - | 1.000 / 1.000 |
| 6J DON_N20_EX | 3634 | -7527 | -11162 | 65120 | 69874 | 8 / 7 | - / - | 1.000 / 1.000 |
| ZB DON_N60_EX | -2296 | 8706 | +11001 | 72058 | 69198 | 7 / 7 | - / - | 1.000 / 1.000 |
| PORT DON_N40_EX | 275707 | 267129 | -8578 | 220599 | 224712 | 7 / 7 | - / - | 1.000 / 1.000 |
| ZB DON_N100_SAR | 64352 | 72857 | +8504 | 64655 | 64655 | 8 / 9 | - / - | 1.000 / 1.000 |
| ZN DON_N20_EX | 22924 | 14873 | -8051 | 49236 | 52130 | 9 / 9 | - / - | 1.000 / 1.000 |
| GC DON_N100_SAR | 143384 | 135787 | -7597 | 193476 | 193476 | 7 / 7 | - / - | 1.000 / 1.000 |
| PORT DON_N40_SAR | 342180 | 349685 | +7504 | 271126 | 271126 | 7 / 7 | - / - | 1.000 / 1.000 |
| ZB DON_N40_SAR | 60872 | 68376 | +7504 | 64094 | 64094 | 8 / 8 | - / - | 1.000 / 1.000 |
| PORT DON_N20_SAR | 171023 | 163819 | -7204 | 279813 | 275353 | 8 / 8 | - / - | 1.000 / 1.000 |
| ZB DON_N100_EX | 99429 | 105734 | +6305 | 45137 | 45137 | 8 / 8 | - / - | 1.000 / 1.000 |
| GC DON_N100_EX | 73586 | 67462 | -6125 | 141510 | 141510 | 6 / 6 | - / - | 1.000 / 1.000 |

#### DAILY-R6 (578 cells; 1,000 worlds; family p random-side, new-set family A)
Tolerant cells (union of the original and the repaired set; 14 cells):
| cell | net orig $ | net repaired $ | delta $ | maxDD orig $ | maxDD repaired $ | years+ orig / repaired | tolerant orig / repaired | family p orig / repaired |
|--|--|--|--|--|--|--|--|--|
| PORT16 MA_50_200 | 289523 | 289523 | +0 | 548873 | 548873 | 9 / 9 | T / T | 1.000 / 1.000 |
| HO NIGHT_L | 244468 | 244468 | +0 | 56974 | 56974 | 10 / 10 | T / T | 0.830 / 0.833 |
| HG TSMOM_L252_vol | 114230 | 114230 | +0 | 87587 | 87587 | 9 / 9 | T / T | 1.000 / 1.000 |
| HO NIGHT_MOM20 | 113942 | 113942 | +0 | 60092 | 60092 | 9 / 9 | T / T | 1.000 / 1.000 |
| SI MR_k1_th1.5 | 88594 | 88594 | +0 | 69804 | 69804 | 9 / 9 | T / T | 1.000 / 1.000 |
| HO DON_N100_EX | 87274 | 87274 | +0 | 139808 | 139808 | 9 / 9 | T / T | 1.000 / 1.000 |
| ZT DON_N100_EX | 93363 | 84139 | -9224 | 36320 | 36046 | 9 / 9 | T / T | 1.000 / 1.000 |
| NG TSMOM_L21_1lot | 76886 | 76886 | +0 | 42301 | 42301 | 9 / 9 | T / T | 1.000 / 1.000 |
| NG MR_k5_th1.5 | 69331 | 69331 | +0 | 27453 | 27453 | 11 / 11 | T / T | 0.777 / 0.776 |
| HE DON_N40_SAR | 52799 | 52799 | +0 | 76740 | 76740 | 9 / 9 | T / T | 1.000 / 1.000 |
| HE DON_N40_EX | 39440 | 39440 | +0 | 40490 | 40490 | 10 / 10 | T / T | 1.000 / 1.000 |
| NG MR_k2_th1 | 35253 | 35253 | +0 | 55442 | 55442 | 9 / 9 | T / T | 1.000 / 1.000 |
| NG MR_k3_th1 | 26320 | 26320 | +0 | 56052 | 56052 | 9 / 9 | T / T | 1.000 / 1.000 |
| ZW MR_k3_th1.5 | 8103 | 8103 | +0 | 29398 | 29398 | 9 / 9 | T / T | 1.000 / 1.000 |
Other cells with |delta net| > $5,000 (21):
| cell | net orig $ | net repaired $ | delta $ | maxDD orig $ | maxDD repaired $ | years+ orig / repaired | tolerant orig / repaired | family p orig / repaired |
|--|--|--|--|--|--|--|--|--|
| ZT DON_N40_SAR | 71667 | 50364 | -21304 | 53406 | 69549 | 7 / 7 | - / - | 1.000 / 1.000 |
| PORT16 DON_N100_EX | -4939 | -17737 | -12798 | 639812 | 638953 | 6 / 6 | - / - | 1.000 / 1.000 |
| PORT16 DON_N40_SAR | -354029 | -366345 | -12317 | 773720 | 768847 | 5 / 5 | - / - | 1.000 / 1.000 |
| PORT16 DON_N60_SAR | -414424 | -425660 | -11236 | 914724 | 910928 | 4 / 4 | - / - | 1.000 / 1.000 |
| PORT16 DON_N40_EX | -114699 | -125920 | -11222 | 685740 | 682874 | 4 / 4 | - / - | 1.000 / 1.000 |
| HG DON_N20_EX | -44697 | -55787 | -11090 | 99917 | 103822 | 6 / 6 | - / - | 1.000 / 1.000 |
| PORT16 DON_N60_EX | -224269 | -234960 | -10691 | 695501 | 693603 | 4 / 4 | - / - | 1.000 / 1.000 |
| 6C DON_N20_SAR | 36882 | 27344 | -9538 | 60895 | 60895 | 7 / 7 | - / - | 1.000 / 1.000 |
| 6A DON_N60_EX | -79807 | -89200 | -9393 | 120865 | 130258 | 2 / 2 | - / - | 1.000 / 1.000 |
| SI DON_N60_SAR | -186570 | -195942 | -9373 | 349607 | 349607 | 6 / 6 | - / - | 1.000 / 1.000 |
| HG DON_N20_SAR | -31848 | -41158 | -9310 | 143415 | 143415 | 7 / 7 | - / - | 1.000 / 1.000 |
| ZT DON_N20_SAR | -10150 | -1478 | +8672 | 58342 | 58342 | 6 / 6 | - / - | 1.000 / 1.000 |
| ZF DON_N100_EX | 104268 | 96323 | -7945 | 55101 | 54515 | 10 / 10 | - / - | 1.000 / 1.000 |
| ZT DON_N60_SAR | 87724 | 79978 | -7746 | 37811 | 35186 | 8 / 8 | - / - | 1.000 / 1.000 |
| HG DON_N40_EX | -29670 | -37400 | -7730 | 123829 | 123829 | 5 / 5 | - / - | 1.000 / 1.000 |
| 6C DON_N40_EX | 21931 | 15212 | -6719 | 47473 | 47473 | 7 / 7 | - / - | 1.000 / 1.000 |
| ZF DON_N60_EX | 64957 | 58389 | -6568 | 42990 | 50144 | 8 / 8 | - / - | 1.000 / 1.000 |
| ZF DON_N20_SAR | 15526 | 21901 | +6375 | 67667 | 67667 | 10 / 10 | - / - | 1.000 / 1.000 |
| SI DON_N20_EX | -67073 | -61719 | +5355 | 367869 | 367869 | 6 / 6 | - / - | 1.000 / 1.000 |
| NG DON_N40_SAR | -1427 | 3613 | +5040 | 82574 | 82574 | 9 / 9 | - / - | 1.000 / 1.000 |
| 6B DON_N20_EX | -68385 | -73398 | -5013 | 107031 | 113526 | 6 / 6 | - / - | 1.000 / 1.000 |
#### Watch cell, frozen thresholds, plateau counts, walk-forward
* **CL Donchian-20 stop-and-reverse (watch cell): identical on original and repaired bars** (all three bases): vol lots raw $ net $145,270.5, maxDD $47,781.8, annual sigma $26,760.8; 1 lot raw $ $132,163.6 / $42,946.5 / $25,716.1; 1 lot adjusted $ (forward-dollar basis) $147,485.1 / $48,338.4 / $25,148.8; ex-2020 $97.8k. **K1 ($47,782) and K2 (-$26,761) and the reconciliation table of WATCH_CL_DONCHIAN_RECON.md do not move; no amendment.** The ZL-2 plugin reads cache_c (repaired) as well.
* CL 96-cell surface: 2 of 96 cells change (N = 10, exit N/4, no-filter and high-vol: +$24.7k vs +$12.7k and -$12.9k vs -$24.9k), the plateau count stays 3 of 8, neighbour median Calmar 0.114 both, top-3-trades share 89.1% both.
* Rates momentum (ZF, ZT, ZN, ZB): 0 of 512 surface cells change (TSMOM uses the closes only; no bad print reaches them); plateau counts identical (ZF a 2 / b 1, ZT 3 / 2, ZN 2 / 2, ZB 1 / 1), L189 cells identical ($140.9k, $135.8k, $132.1k), so the ZF / ZT verdict, the WATCH_ZF_MOM decision (none written) and the S5 / S6 numbers stand.
* Walk-forward groups: FIND_DAILY 60 groups, positive with p <= .10: 3 original, 3 repaired (RTY F5, CL F2, NKD F1, same totals); the repaired F2 (Donchian) refits differ by +$28.9k (GC), +$5.5k (6J), +$44.2k (PORT); DAILY-R6 85 groups, 7 positive with p <= .10 in both (SI F1, HG F1, NG F3, HO F2, ZF F1, ZT F1, 6B F2 with +$6.0k vs +$6.9k, p .066 vs .056); the largest change is ZF F2 (+$12.1k, p .67 -> .50).
#### Labels moved
FIND_DAILY: one: 6J Donchian-60 stop-and-reverse is tolerant on the ORIGINAL bars (13-year net $126.4k, 9 years positive) and NOT on the repaired bars (net $109.2k, 8 years positive, maxDD $51.1k -> $63.5k): best-of-F -> NULL; it was never a family-p candidate (p 1.00 both). Counts: best-of-F 37 -> 36 (the published figure), NULL 282 -> 283, REGIME 89 = 89. DAILY-R6: no tolerant flag moves (14 = 14); two NULL cells (ZT Donchian-20 SAR and EX) become REGIME on the repaired bars; best tolerant family p 0.777 -> 0.776 (A); no LEAD either way.
**Plain sentence: the repair moves 42 of 408 FIND_DAILY cells and 73 of 578 DAILY-R6 cells by more than $1 (up to $17k and $21k over 13 years), but only the Donchian cells (the ones that read daily highs and lows), a handful of closes-based cells and the portfolios built from them; one tolerant flag moves (6J Donchian-60, to NULL), no family p crosses .10, no LEAD appears or disappears, and the frozen CL watch thresholds (K1 $47,782, K2 -$26,761), the CL plateau count and the rates plateau counts are unchanged. Since the published daily results were already computed on the repaired copy, nothing published needs a correction.**
