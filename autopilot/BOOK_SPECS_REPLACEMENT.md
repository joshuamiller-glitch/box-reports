# BOOK_SPECS_REPLACEMENT: spec + two test vectors for each of the six exact-confirmed replacement books (W-SPECS, order 2242Z items 4 and 5; page 1 written 27 Nov 23:xxZ)

Research note, nothing live touched. Written for the relay that codes the next build: every line says what is SPEC (read from code or config on the box, file named) and what is my READING. Nothing here is rounded or approximated; where a thing cannot be given exactly it is listed in section 8 ("CANNOT BE GIVEN EXACTLY").

## ANSWER FIRST

1. **Each book is defined by its EVENT FILE** (`/mnt/l2/l2vast/_dynexit/ev/REPL_<S>_c<k>.parquet`: ts = signal second, side, stop_pts, tgt_pts, lots = 2, exit_ts = bell), which the exact engine trades. I regenerated every file by running the book code on the stored bar rows on this box and compared event by event. Result: **LO outside 934 / 934 identical; NY AM fibr_or break_native 1,243 / 1,243 identical; NY PM canc_follow 9,547 / 9,547 identical; Asia mmove retest_native 1,448 / 1,448 identical (the same cell on a second row, trb_25000, adds 161 events that are NOT in the tested file); NY AM prior_day false_break 33,082 / 33,082 identical as the UNION of three bar rows; NY PM trendline reject_native: the tested file (82,118 events) = UNION of three bar rows (time_m_1, time_s_45, vol_750) minus 92 last-second events that have no entry second.**
2. **Four books are single-bar-row books (bar type = one row). Two are NOT: NY PM trendline reject (3 rows: 1-minute time bars, 45-second time bars, volume bars 750) and NY AM prior_day false_break (rows dchg_20 = kagi_20, which are the SAME bars, and swing_atr_0.25: two distinct bar series).** For those two the signal is true when ANY of the listed rows signals, one position shared by all (section 0.4). "Bar type" for them is a set, not one bar; the screen page REPLACE_CANDIDATES.md does not say so.
3. **Twelve test vectors (two per book, real data from 1-4 Oct 2026, taken from the exact engine A-set trades) all replay: the book's own module run on the printed rows (plus the stored line / feature values printed beside them) fires exactly the stated side on exactly the last row.** Rows and inputs are in `autopilot/book_vectors/*.csv` (24 files). For the five level / structure books an independent re-implementation written from the rule text also agrees (section of each vector).
4. **One thing is not reproducible from NQ bars alone: NY PM canc_follow needs per-bar add / cancel sizes from the 10-level book history (mbp-10, 100 ms grid)**; the vectors give the stored per-bar values, not a recipe from bars (section 1, section 8).
5. **Item 5 (BE / PL / NT keys): EXIT_MGMT_SUNDAY_MATCH.md is the match file for EXIT_MGMT_SUNDAY.md; all 13 books on the page agree between the two files (S0 / T0, arm and trail numbers).** But the six replacement books are NOT on either page; strings for them are derived below by the page's own rule and are UNTESTED. Mismatches found (page text only, no effect on the tested numbers): "12 edge books" vs 13 rows; trail 11.2 printed for 11.25; BE offset unit written "pt" but the engine key is ticks; raw engine keys use risk units, the page strings use target units (conversion in sun_build.py). Section 9.

## 0. WHAT ALL SIX SHARE (SPEC unless marked)

0.1 **Sessions (ET, `th_bars/common.py` sessionize, `th_grid/gcore2.py` _TH)**: Asia 18:00-02:00 (code 0), London 02:00-08:30 (1), pre 08:30-09:30 (2, never traded), NY AM 09:30-12:00 (3), NY PM 12:00-16:00 (4), close 16:00-17:00 and halt 17:00-18:00 (5). Trading date = ET + 6 h. The session of a signal = the session code of the signal bar (`sess_id % 10`). The bar series of a row resets (bar index 0, new bar) at every session change and every contract change; the harness hands the signal code ONE continuous series (all sessions of all days concatenated in time order, as a chart would), so indicator state (EMA, rolling windows, levels) runs across session breaks.

0.2 **Which bars may signal**: `part == 0` only (the unfinished last bar of a session, part = 1, is dropped), signal bar not the first bar of the row, session code in (0, 1, 3, 4) and equal to the book's session. Signal time = `t_close` of the signal bar = the time the bar is KNOWN (event bars: timestamp of the closing print; time bars: the bucket end). Whole seconds.
**Cross-session consequence (matters for a live build)**: because the series is continuous, look-back conditions (n = 3 hold bars, M-bar windows, previous-bar compares, EMA, rolling std) reach into the previous session's bars, and the decision time T0 used to read a level for bar j is `t_close` of bar j-1 EVEN WHEN THAT IS HOURS EARLIER (the harness frame has no bar open time, so `max(t_close[j-1], t_open[j])` reduces to `t_close[j-1]`). Vector AS1-1 is exactly this case (signal bar = first Asia bar, closing 19:03:37 ET, line read as of 16:59:59 ET, the last bar before the halt); NY5-2 is the second bar of its session (bidx 1), so its 3-bar hold takes bar j-2 from the previous session. What the live chart does with a bar open time is NOT settled here (OPEN, section 8 item 9).

0.3 **Entry and exit in the exact engine (`th_combo/mf_multi.py`, set JSON `_th_sz/ijk/exact/sets/TL3_DX_<S>_REPL_c<k>_A.json`)**: market entry at the signal second + 1.000 s (LAT_FILL 1.0 s; engine trades.parquet shows entry_ns = sig_ns + 1 s exactly), fill model 'through', hair 0.5, wait 10; **2 lots**; stop_pts and tgt_pts from the event file (bracket as in the headings; LONDON is stop 60 / target 10); exit at the bell (`exit_ts` = session end, 'UWTime' exits show 1 s after the bell); one stream tag RPL. Day caps in the A-sets: NY PM [84,000, 25,200] and NY AM [72,000, 21,600] dollars (max day profit / max day loss, `replica/sim.py` L50), London / Asia effectively none (2e12 / 3e12). A-set = candidate alone, bare (no Trade Health, zone, stack caps, BookLock, NTZ; ec_hooks empty; `lin.ntz = off`). The PLAYBOOK variants use the `_safe15` files (stop x 1.5, no target): not the exact-confirmed rows.

0.4 **One-position rule**: the engine takes a signal only when the book's position is flat; signals arriving while it is open are ignored (both sides share the one slot; no queueing, no add). Checked on the data: in every vector below the events falling between entry and exit opened no trade (counts printed per vector; non-vacuous, i.e. with events actually skipped, in AS1-1: 1, NP2-1: 48, NP2-2: 66, NY1-1: 68). For multi-row books (NP2, NY1) the union is deduplicated on (second, side) before the engine sees it; a long on one row and a short on another in the same second are two events and same-second opposite-side events were not checked exhaustively (OPEN, not needed by the vectors).

0.5 **Events with no entry**: extraction (`th_negbook/ev_extract.py`) drops signals with no tape between signal + 1 s and the bell (e.g. the last second of a session). 92 such events removed from NP2; none removed from the other five files (counts equal).

0.6 **Exact results of the A-sets (trades.parquet, 42 months 2023-04 .. 2026-10, 2 lots; my sums of `net_fee`; the page REPL_EXACT_SCORES.md prints per-trade figures about 3% lower, definition of its "net" not re-derived: OPEN)**:

| book | trades | net / trade | total | exit mix |
|---|---|---|---|---|
| NY PM book_cancel canc_follow 90/90 (page: 1749 / $242 / $423,170) | 1749 | $249 | $435,972 | {'UWTime': 0.41, 'Target': 0.32, 'Stop': 0.27} |
| NY PM levels_trendline reject_native 90/90 (page: 1792 / $146 / $262,203) | 1792 | $154 | $275,321 | {'UWTime': 0.41, 'Target': 0.31, 'Stop': 0.28} |
| Asia levels_mmove retest_native 60/60 (page: 974 / $280 / $272,297) | 974 | $287 | $279,426 | {'UWTime': 0.56, 'Target': 0.27, 'Stop': 0.17} |
| London structure_inside outside 10/60 (page: 864 / $100 / $86,476) | 864 | $107 | $92,801 | {'Target': 0.83, 'UWTime': 0.1, 'Stop': 0.07} |
| NY AM levels_fibr_or break_native 60/60 (page: (not on that page)) | 1014 | $248 | $251,427 | {'UWTime': 0.38, 'Target': 0.35, 'Stop': 0.27} |
| NY AM levels_prior_day false_break 120/120 (page: 1024 / $385 / $394,688) | 1024 | $393 | $402,183 | {'UWTime': 0.49, 'Target': 0.29, 'Stop': 0.23} |


## 1. NY PM `book_cancel canc_follow` {L 100, z 2.0}, bracket 90/90 (stop 90, target 90), both sides (set TL3_DX_NP_REPL_c1_A, event file REPL_NP_c1)

**Bar type: ONE row, `vol_1100`** (volume bar). SPEC `th_bars/build_month.py` L87-88 + `kernels.py` k_cum: a bar closes at the print where the cumulative size of the bar reaches **1100 x s_vol** contracts (mode 0, metric = size); the closing print stays in that bar (no split); OHLC from all prints; bar index restarts at 0 at each session change or contract change; `t_close` (known time) = timestamp of the closing print; the last bar of a session, if unfinished, is emitted with part = 1 (dropped for signals). **s_vol** = (median of the daily volumes of the 20 PRIOR trading dates, needing at least 5 non-zero days, else R0) / R0, R0 = median of the first 60 trading dates' daily volume (Apr-Jun 2023); fixed for the whole trading date (`build_month.py` scales(), table `/mnt/l2/l2vast/_bars/stats_day.parquet`). Values for the vector days are printed under each vector.

**Session window**: NY PM 12:00-16:00 ET (code 4). **Bell exit** 16:00 ET.

**Signal (SPEC `triggers_c/defs.py` L88-97 `_canc`, `core.py` `thr_signal` / `emit`)**: per bar x = `b_cancA - b_cancB` (ask-side non-trade cancels minus bid-side non-trade cancels: ask pulled = bullish). y = x / rstd(x, 100) with rstd = pandas rolling std (ddof 1) over the last 100 bars INCLUDING the current one, `min_periods = max(5, 100 // 3) = 33`, over the continuous row (not reset at session breaks). Long level-true when y >= 2.0, short level-true when y <= -2.0; the event is the EDGE (level true now, false on the previous bar). A bar with both sides true is dropped; bars where the stored features do not align (NaN) give no signal. Variant `follow` = trade in the direction of the reading (no sign flip). No smoothing (no `sm`), not a `_native` variant, so no seconds-to-bars conversion and no warm-up cut-off beyond the 33-bar minimum.
Parameters: `L = 100`, `z = 2.0`. Nothing else (the module has no other parameter).

**Feature definition (SPEC `triggers_c/featc.py`)**: `b_addB / b_cancB / b_addA / b_cancA` for a bar = the increase in the cumulative add / cancel counters between the last 100-ms book record at or before the PREVIOUS bar's known time and the last at or before THIS bar's known time (first bar of a session: from `t0 - 1`). Counters (`_addcanc` L32-66, L113-119): for consecutive valid 10-level snapshots, per side: add = size at prices that exist in both snapshots and grew, plus size at prices that appear new at or beyond the old worst level; dec = size that shrank at common prices plus the size of old prices that disappeared on the near side of the new worst price; **cancel = max(0, dec - aggressor volume of that side in the interval)**, where bid-side cancels subtract trades with side code 65 and ask-side cancels subtract side code 66 (`p_side` of the history file). Source = raw mbp-10 history `/mnt/l2/l2vast/_hist_replica/days/<Y>/NQ_<date>.npz` (2023-02-01 .. 2026-10-30), book records with `ts_recv <= known_ts` only. Store: `/mnt/l2/l2vast/_bars/feat_c/vol_1100/<YYYYMM>.parquet`, float16 clipped (so the stored x values are float16-rounded: the vectors use the stored values).
**Live need (SPEC `defs.py` NEED string)**: "L2 depth snapshots (100 ms); exact add/cancel/modify split needs MBO". **This book cannot be run from NQ bars + 1-s data: it needs the 10-level book stream and trade aggressor side live.** The 92 live cuts corrupted by ES/RTY levels in the live NQ book (project note "Depth pollution") are a warning for any live build of this feature (not re-checked here).

**Warm-up**: 33 bars of the continuous row (rolling std minimum); the store starts 2023-02.
**One position**: section 0.4. **Bracket**: stop 90 pt, target 90 pt, 2 lots, bell exit 16:00.


### Test vectors for NP1 (real data on this box, both replayed)

**Vector NP1-1 (LONG)**: signal 2026-10-01 13:11:53 ET (epoch s 1790874713, bar row `vol_1100`, bar index 494357 in the continuous row, sess_id 202610014); engine entry 2026-10-01 13:11:54 ET at **30664.125** (2 lots, A-set trade), exit 2026-10-01 13:23:10 ET at 30754.250 (Target).
Signal-bar close (the price at which the signal is true) = 30664.50; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 0 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 494353 | 13:07:01 | 30649.25 | 30657.25 | 30643.25 | 30647.25 | 927 | -85 | 0 |
| 494354 | 13:08:30 | 30647.25 | 30652.50 | 30642.25 | 30651.75 | 931 | -115 | 0 |
| 494355 | 13:09:38 | 30651.75 | 30656.75 | 30635.75 | 30642.75 | 927 | -37 | 0 |
| 494356 | 13:10:56 | 30641.75 | 30652.50 | 30636.75 | 30647.00 | 927 | 39 | 0 |
| 494357 | 13:11:53 | 30647.00 | 30664.50 | 30645.25 | 30664.50 | 927 | 97 | 0 |

Full replay window (140 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/book_cancel_canc_follow_NYPM_v1_bars.csv`; per-bar inputs `book_cancel_canc_follow_NYPM_v1_inputs.csv`.
Feature inputs (stored per-bar values, `b_cancA` / `b_cancB` = non-trade cancelled size on the ask / bid side in the bar window, from the 100-ms mbp-10 grid): last 3 bars x = cancA - cancB = -118, -24, 515; rolling std over the last 100 values (ddof 1) = 210.786, 210.768, 213.222; **z = x / std = -0.560, -0.114, 2.415**; threshold 2.0: previous bar z < 2.0 and this bar z >= 2.0 (long edge). Independent numpy check: z[-1] = 2.4153, z[-2] = -0.1139.
The 140 (A, B) pairs: `book_cancel_canc_follow_NYPM_v1_inputs.csv` (columns b_cancA, b_cancB).
Replay of the book code (module `signal_fn` on exactly these rows + the stored feature values): fires **[1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `vol_1100` on that day: closes at cumulative volume >= 1100 x s_vol = 1100 x 0.8424 = **926.64** contracts (trading date 20261001).

**Vector NP1-2 (SHORT)**: signal 2026-10-01 13:32:33 ET (epoch s 1790875953, bar row `vol_1100`, bar index 494398 in the continuous row, sess_id 202610014); engine entry 2026-10-01 13:32:34 ET at **30824.000** (2 lots, A-set trade), exit 2026-10-01 14:05:51 ET at 30734.000 (Target).
Signal-bar close (the price at which the signal is true) = 30826.25; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 0 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 494394 | 13:31:11 | 30847.25 | 30855.75 | 30843.00 | 30852.00 | 927 | -173 | 0 |
| 494395 | 13:31:31 | 30851.25 | 30853.25 | 30838.75 | 30850.50 | 937 | -33 | 0 |
| 494396 | 13:31:52 | 30850.50 | 30854.25 | 30834.25 | 30846.75 | 927 | -77 | 0 |
| 494397 | 13:32:12 | 30846.75 | 30862.00 | 30846.75 | 30855.00 | 927 | -41 | 0 |
| 494398 | 13:32:33 | 30854.75 | 30855.75 | 30823.50 | 30826.25 | 927 | -113 | 0 |

Full replay window (140 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/book_cancel_canc_follow_NYPM_v2_bars.csv`; per-bar inputs `book_cancel_canc_follow_NYPM_v2_inputs.csv`.
Feature inputs (stored per-bar values, `b_cancA` / `b_cancB` = non-trade cancelled size on the ask / bid side in the bar window, from the 100-ms mbp-10 grid): last 3 bars x = cancA - cancB = -28, 12, -361; rolling std over the last 100 values (ddof 1) = 176.411, 175.979, 178.987; **z = x / std = -0.159, 0.068, -2.017**; threshold 2.0: previous bar z < 2.0 and this bar z >= 2.0 (long edge). Independent numpy check: z[-1] = -2.0169, z[-2] = 0.0682.
The 140 (A, B) pairs: `book_cancel_canc_follow_NYPM_v2_inputs.csv` (columns b_cancA, b_cancB).
Replay of the book code (module `signal_fn` on exactly these rows + the stored feature values): fires **[-1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `vol_1100` on that day: closes at cumulative volume >= 1100 x s_vol = 1100 x 0.8424 = **926.64** contracts (trading date 20261001).


## 2. NY PM `levels_trendline reject` (variant `reject_native`) {conf body, tol 1.0}, bracket 90/90, both sides (set TL3_DX_NP_REPL_c2_A, event file REPL_NP_c2)

NOTE ON THE NAME: the screen pages say `levels_trendline reject`; the cell that was extracted, traded and confirmed is **`reject_native`** (tolerance in units of the bar's own median range). The plain `reject` (tolerance in fixed points, u0 = 5) is a different cell and was NOT the tested one (extraction cell string `trig_levels_trendline|reject_native|{"conf": "body", "tol": 1.0}`, `th_planas/repl_extract.py`).

**Bar type: a SET of THREE rows; the event is true when ANY of them signals (union, deduplicated on second and side)**:
- `time_m_1`: 1-minute time bars, bucket = floor((ts - first print of the session)/60 s), a bucket with no print gives no bar, bar known at the bucket end (`build_month.py` time_bars L52-65, P = 60 s); the last bucket of a session is part = 1 if truncated.
- `time_s_45`: the same builder with P = 45 s.
- `vol_750`: volume bar as in section 1 with N = 750 (threshold 750 x s_vol).
Replay evidence: events of the three rows = 27,100 + 30,878 + 28,592 (+ coincident seconds) = the file's 82,118 exactly, except 92 last-second signals of vol_750 (section 0.5). The ev library also holds `tm60` and `tib_1200` events for this cell (27,207 and 44,369); **they are not in the tested file** (1,471 tm60 events and 42,563 tib_1200 events are absent from it; the rest coincide with other rows' seconds). READING: those rows were extracted after the file was cut.

**Session window**: NY PM 12:00-16:00 ET (code 4). Bell 16:00.

**Signal (SPEC `triggers_d/lv_base.py` + `fd_common.py` `level_events`, `lv_trendline.py`)**: level set `TRENDLINE` = four lines `TL5_L`, `TL5_H`, `TL15_L`, `TL15_H`; variant `reject_native`, params conf = body, tol = 1.0. With u = bar-native unit (`fd_common.unit`: median of (h - l) over the PREVIOUS 100 bars of the row, `min_periods = 20`, shifted by one bar so the current bar is excluded, floor 0.5 pt; no signal while u is NaN), tol_pts = 1.0 x u, pc = previous bar close, L = the line value at the bar's decision time:
 - short event bar: `pc < L and h >= L - tol_pts and c < L and c < o` (touches / pierces the line from below within tolerance, closes back below it, red body);
 - long event bar: `pc > L and l <= L + tol_pts and c > L and c > o`;
 - EDGE: the condition is true now and was false on the previous bar; first firing line wins `fired`; a bar that is long on one line and short on another gives no signal.
**Lines (SPEC `fd_levels2.py`)**: aggregate the 1-minute NQ grid (`feat_d/nq1m.npz`) to 5-minute / 15-minute bars; fractal pivots with strength 2 (a bar whose high / low is the unique extreme of itself +- 2 bars), a pivot at bar j counts from the END of bar j+2; `TL<s>_L` = straight line through the last two confirmed pivot LOWS extrapolated in time to the minute, **kept only when the slope is positive** (ascending support); `TL<s>_H` through the last two confirmed pivot HIGHS, **kept only when the slope is negative** (descending resistance); not available when the newest pivot is older than 4,320 minutes (5 m) / 14,400 minutes (15 m). Each minute-grid entry i uses information up to minute i - 1 only; the harness looks up the last grid minute whose start <= the decision second T0 = `t_close` of the previous bar, stale limit 120 s (older = NaN). Prices are the raw front-month price (lines are computed back-adjusted and converted back).
**Warm-up**: 20 prior bars of the row for u; the lines need two confirmed pivots (about 25 minutes of 5-minute bars).
**Bracket**: stop 90, target 90, 2 lots, bell exit 16:00.


### Test vectors for NP2 (real data on this box, both replayed)

**Vector NP2-1 (SHORT)**: signal 2026-10-01 12:04:00 ET (epoch s 1790870640, bar row `vol_750`, bar index 723253 in the continuous row, sess_id 202610014); engine entry 2026-10-01 12:04:01 ET at **30628.250** (2 lots, A-set trade), exit 2026-10-01 13:20:25 ET at 30718.250 (Stop).
Signal-bar close (the price at which the signal is true) = 30628.50; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 48 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 723249 | 12:02:11 | 30614.75 | 30615.75 | 30608.25 | 30611.25 | 632 | -4 | 0 |
| 723250 | 12:02:40 | 30611.50 | 30626.00 | 30606.75 | 30625.75 | 632 | 40 | 0 |
| 723251 | 12:03:00 | 30626.00 | 30627.75 | 30617.00 | 30627.50 | 632 | 96 | 0 |
| 723252 | 12:03:19 | 30627.25 | 30633.50 | 30624.75 | 30628.75 | 632 | 16 | 0 |
| 723253 | 12:04:00 | 30629.00 | 30637.00 | 30626.75 | 30628.50 | 632 | -28 | 0 |

Full replay window (130 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/levels_trendline_reject_NYPM_v1_bars.csv`; per-bar inputs `levels_trendline_reject_NYPM_v1_inputs.csv`.
Level inputs: firing line `TL5_H`; unit u (trailing median bar range over the previous 100 bars, floor 0.5) at the signal bar = 14.125 pt; decision second (t_close of the previous bar) = 1790870599 (12:03:19 ET).
Line `TL5_H` at each shown bar (value at that bar's decision time): 723249: 30646.256, 723250: 30645.232, 723251: 30645.232, 723252: 30644.211, 723253: 30644.211.
Independent re-implementation (written from the rule text, not the module) on the 130 rows x 4 lines: side at the signal bar = -1 (module: -1); signals at the 9 bars before it: [].
Replay of the book code (module `signal_fn` on exactly these rows + the stored line values): fires **[-1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `vol_750` on that day: closes at cumulative volume >= 750 x s_vol = 750 x 0.8424 = **631.80** contracts (trading date 20261001).

**Vector NP2-2 (LONG)**: signal 2026-10-01 14:44:15 ET (epoch s 1790880255, bar row `time_s_45`, bar index 1652608 in the continuous row, sess_id 202610014); engine entry 2026-10-01 14:44:16 ET at **30800.000** (2 lots, A-set trade), exit 2026-10-01 16:00:01 ET at 30769.500 (UWTime).
Signal-bar close (the price at which the signal is true) = 30799.50; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 66 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 1652604 | 14:41:15 | 30806.25 | 30810.25 | 30803.75 | 30809.75 | 309 | 37 | 0 |
| 1652605 | 14:42:00 | 30810.50 | 30816.75 | 30807.25 | 30808.50 | 332 | -34 | 0 |
| 1652606 | 14:42:45 | 30808.00 | 30810.75 | 30794.75 | 30800.25 | 614 | -136 | 0 |
| 1652607 | 14:43:30 | 30799.50 | 30804.00 | 30795.50 | 30797.75 | 455 | -7 | 0 |
| 1652608 | 14:44:15 | 30797.00 | 30800.25 | 30792.50 | 30799.50 | 385 | 45 | 0 |

Full replay window (130 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/levels_trendline_reject_NYPM_v2_bars.csv`; per-bar inputs `levels_trendline_reject_NYPM_v2_inputs.csv`.
Level inputs: firing line `TL5_L`; unit u (trailing median bar range over the previous 100 bars, floor 0.5) at the signal bar = 16.500 pt; decision second (t_close of the previous bar) = 1790880210 (14:43:30 ET).
Line `TL5_L` at each shown bar (value at that bar's decision time): 1652604: 30774.295, 1652605: 30776.428, 1652606: 30778.559, 1652607: 30778.559, 1652608: 30780.691.
Independent re-implementation (written from the rule text, not the module) on the 130 rows x 4 lines: side at the signal bar = 1 (module: 1); signals at the 9 bars before it: [].
Replay of the book code (module `signal_fn` on exactly these rows + the stored line values): fires **[1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `time_s_45` on that day: time bar 45 s, bucket = floor((ts - first print of the session)/45 s); known at bucket end.


## 3. Asia `levels_mmove retest` (variant `retest_native`) {M 3, tol 0.0}, bracket 60/60, both sides (set TL3_DX_AS_REPL_c1_A, event file REPL_AS_c1)

NOTE ON THE NAME: tested cell = **`retest_native`** (the screen page prints `retest`). Plain `retest` is a different cell.

**Bar type: ONE row, `tsf_5_400`** (trade-size-filtered volume bar, minimum print 5 lots, threshold 400). SPEC `build_month.py` L97-100, `kernels.py` k_cum, TSF table `{5: [50, 100, 200, 400, 700, 1200]}`: metric per print = size if size >= 5 else 0; a bar closes at the print where the cumulative metric >= **400 x s_vol** (s_vol as in section 1). **The kernel updates open / high / low / close / volume with EVERY print, not only prints >= 5 lots**, although BAR_REGISTRY.md says "bar OHLC still uses only counted prints": registry text and kernel disagree; the stored bars (and so all results) follow the kernel. Closing print stays in its bar; known time = closing print timestamp; reset at session / contract change.
Extra row in the library: the same cell on `trb_25000` gives 161 Asia events; they are NOT in the tested file (replay: 1,448 events from tsf_5_400 = the file exactly).

**Session window**: Asia 18:00-02:00 ET (code 0; the trading date rolls at 18:00). Bell 02:00 ET.

**Signal (SPEC `lv_base.py` / `fd_common.py` `level_events`, `lv_mmove.py`)**: level set `MMOVE` = lines `MM5`, `MM15`, `MM60`. Variant `retest_native`, M = 3, tol = 0.0. u = bar-native unit as in section 2. With Ls = L (level at the bar's decision time), k = 0 (retest uses `k = p.get('k', 0.0)` = 0):
 - up(j) = `c[j] > L[j]`, dn(j) = `c[j] < L[j]` (k = 0);
 - EDGE(up) = up now and not up on the previous bar (a fresh close beyond the line); `ru` = EDGE(up) occurred in bars j-3 .. j-1 (the three bars BEFORE the signal bar; the signal bar itself excluded);
 - long event bar: `ru and l <= L + 0 and c > L and c >= o`; short: `rd and h >= L - 0 and c < L and c <= o`; (tol = 0.0 x u = 0);
 - the event is again the EDGE of that condition; first firing line recorded; both-sided bars dropped.
**Lines (SPEC `fd_levels2.py` L48-60)**: zigzag of confirmed fractal pivots (strength 2) on 5 / 15 / 60-minute aggregated bars (a pivot counts from the end of bar j + 2; alternate high / low; a later pivot of the same type replaces the earlier one only if more extreme, decided at its confirmation); with A, B, C the last three alternating pivots (C newest): `MM = C + (B - A)` when legs A->B and B->C have opposite signs, else NaN (AB = CD projection); available from the confirmation time of C; expires after 4,320 min (MM5) / 14,400 (MM15) / 43,200 (MM60). Lookup as in section 2.
**Warm-up**: 20 prior bars (u) plus three confirmed pivots on the line's aggregation.
**Bracket**: stop 60, target 60, 2 lots, bell exit 02:00.


### Test vectors for AS1 (real data on this box, both replayed)

**Vector AS1-1 (LONG)**: signal 2026-09-30 19:03:37 ET (epoch s 1790809417, bar row `tsf_5_400`, bar index 184236 in the continuous row, sess_id 202610010); engine entry 2026-09-30 19:03:38 ET at **30780.250** (2 lots, A-set trade), exit 2026-09-30 21:25:30 ET at 30840.250 (Target).
Signal-bar close (the price at which the signal is true) = 30780.25; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 1 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 184228 | 16:05:20 | 30675.00 | 30702.25 | 30648.25 | 30702.25 | 3583 | 215 | 0 |
| 184229 | 16:07:23 | 30702.25 | 30710.50 | 30675.00 | 30705.00 | 3016 | 168 | 0 |
| 184230 | 16:11:40 | 30705.00 | 30707.00 | 30662.00 | 30699.25 | 3231 | -367 | 0 |
| 184231 | 16:19:25 | 30699.75 | 30728.25 | 30690.00 | 30720.00 | 4249 | 61 | 0 |
| 184232 | 16:25:13 | 30720.50 | 30744.50 | 30715.25 | 30739.25 | 2270 | 224 | 0 |
| 184233 | 16:36:14 | 30739.25 | 30750.00 | 30732.50 | 30750.00 | 2676 | 42 | 0 |
| 184234 | 16:58:56 | 30750.75 | 30751.50 | 30712.00 | 30724.75 | 3360 | -264 | 0 |
| 184235 | 16:59:59 | 30724.75 | 30732.25 | 30716.00 | 30725.75 | 265 | 33 | 1 |
| 184236 | 19:03:37 | 30707.00 | 30794.75 | 30684.50 | 30780.25 | 6453 | 277 | 0 |

Full replay window (130 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/levels_mmove_retest_ASIA_v1_bars.csv`; per-bar inputs `levels_mmove_retest_ASIA_v1_inputs.csv`.
Level inputs: firing line `MM15`; unit u (trailing median bar range over the previous 100 bars, floor 0.5) at the signal bar = 20.250 pt; decision second (t_close of the previous bar) = 1790801999 (16:59:59 ET).
Line `MM15` at each shown bar (value at that bar's decision time): 184228: 30894.750, 184229: 30894.750, 184230: 30894.750, 184231: 30894.750, 184232: 30784.000, 184233: 30784.000, 184234: 30784.000, 184235: 30704.250, 184236: 30704.250.
Independent re-implementation (written from the rule text, not the module) on the 130 rows x 3 lines: side at the signal bar = 1 (module: 1); signals at the 9 bars before it: [].
Replay of the book code (module `signal_fn` on exactly these rows + the stored line values): fires **[1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `tsf_5_400` on that day: closes at cumulative qualifying volume (prints >= 5 lots) >= 400 x s_vol = 400 x 0.8424 = **336.96** (trading date 20261001).

**Vector AS1-2 (SHORT)**: signal 2026-10-05 00:18:42 ET (epoch s 1791173922, bar row `tsf_5_400`, bar index 184554 in the continuous row, sess_id 202610050); engine entry 2026-10-05 00:18:43 ET at **31067.500** (2 lots, A-set trade), exit 2026-10-05 02:00:01 ET at 31046.500 (UWTime).
Signal-bar close (the price at which the signal is true) = 31065.75; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 0 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 184546 | 16:58:00 | 31072.00 | 31073.75 | 31045.50 | 31052.25 | 2015 | -273 | 0 |
| 184547 | 16:59:58 | 31051.00 | 31057.00 | 31043.75 | 31049.00 | 212 | -18 | 1 |
| 184548 | 18:37:01 | 31059.00 | 31163.00 | 31059.00 | 31159.50 | 5170 | 813 | 0 |
| 184549 | 19:33:21 | 31159.25 | 31169.00 | 31142.00 | 31154.00 | 4459 | -193 | 0 |
| 184550 | 20:40:09 | 31155.00 | 31194.50 | 31120.00 | 31168.25 | 9425 | -63 | 0 |
| 184551 | 22:07:21 | 31169.75 | 31221.25 | 31167.00 | 31190.00 | 8320 | -130 | 0 |
| 184552 | 22:46:11 | 31189.00 | 31202.25 | 31138.50 | 31147.00 | 4846 | -328 | 0 |
| 184553 | 23:28:17 | 31147.00 | 31152.25 | 31075.75 | 31123.00 | 7164 | -126 | 0 |
| 184554 | 00:18:42 | 31122.75 | 31129.50 | 31059.00 | 31065.75 | 5666 | -350 | 0 |

Full replay window (130 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/levels_mmove_retest_ASIA_v2_bars.csv`; per-bar inputs `levels_mmove_retest_ASIA_v2_inputs.csv`.
Level inputs: firing line `MM5`; unit u (trailing median bar range over the previous 100 bars, floor 0.5) at the signal bar = 32.375 pt; decision second (t_close of the previous bar) = 1791170897 (23:28:17 ET).
Line `MM5` at each shown bar (value at that bar's decision time): 184546: 31042.750, 184547: 31042.750, 184548: 31042.750, 184549: 31097.500, 184550: 31144.250, 184551: 31145.500, 184552: 31163.000, 184553: 31161.500, 184554: 31097.500.
Independent re-implementation (written from the rule text, not the module) on the 130 rows x 3 lines: side at the signal bar = -1 (module: -1); signals at the 9 bars before it: [].
Replay of the book code (module `signal_fn` on exactly these rows + the stored line values): fires **[-1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `tsf_5_400` on that day: closes at cumulative qualifying volume (prints >= 5 lots) >= 400 x s_vol = 400 x 0.8571 = **342.85** (trading date 20261005).


## 4. London `structure_inside outside` {cf 0.75, filt 20}, bracket target 10 / stop 60 ("10/60"), both sides (set TL3_DX_LO_REPL_c1_A, event file REPL_LO_c1)

**Bracket order**: the screen label "10/60" is TARGET 10 / STOP 60 (event file columns: stop_pts 60, tgt_pts 10; `repl_extract.py` splits the label as target / stop; engine trades confirm: v1 stop at +60.1 pt, v2 target at +10.1 pt). A different reading ("stop 10") would be wrong by 6x.

**Bar type: ONE row, `dol_2600`** (dollar bar). SPEC `build_month.py` L93-94: closes when the cumulative of `px_ticks x 5.0 x size` (= price x 20 x size dollars) >= **2600 x 300,000 x s_dol**, s_dol = scale built like s_vol from the daily dollar volume (trailing median of the 20 prior dates / R0); closing print stays in the bar; known time = closing print; reset at session / contract change; part = 1 last bar dropped.

**Session window**: London 02:00-08:30 ET (code 1). Bell 08:30 ET.

**Signal (SPEC `triggers_b/impl_st.py` `inside_sig`, variant `outside`; `triggers_b/core.py` prep / out)**: bars of the row, back-adjusted for contract rolls through the stored `iid` (older bars shifted by the roll gap; comparisons are relative so the signal is unchanged), continuous series. For bar i with previous bar i-1: `outside = h[i] > h[i-1] and l[i] < l[i-1]`; `pos = (c - l) / (h - l)` (NaN when h = l); EMA f = EMA of the CLOSES with alpha = 2 / (20 + 1), seeded with the first close of the row, run over the whole continuous row (all sessions); **long**: outside and pos >= 0.75 and c > f; **short**: outside and pos <= 0.25 (= 1 - 0.75) and c < f; **no edge filter**: every qualifying bar is a signal (consecutive qualifying bars each signal; the one-position rule then ignores those during a trade). `part == 1` bars and bar 0 give nothing. Parameters: `cf = 0.75`, `filt = 20` (filt = 0 would disable the EMA test).
**Warm-up**: the EMA has no cut-off; a 400-bar window reproduces the full-series value to better than 1e-9 (0.905^400), so any implementation must seed the EMA with the first close and run at least ~400 bars before trading to match.
**Bracket**: stop 60, target 10, 2 lots, bell exit 08:30 (83% of trades exit on target).


### Test vectors for LO1 (real data on this box, both replayed)

**Vector LO1-1 (SHORT)**: signal 2026-10-02 02:53:44 ET (epoch s 1790924024, bar row `dol_2600`, bar index 196246 in the continuous row, sess_id 202610021); engine entry 2026-10-02 02:53:45 ET at **30847.750** (2 lots, A-set trade), exit 2026-10-02 03:10:55 ET at 30907.875 (Stop).
Signal-bar close (the price at which the signal is true) = 30849.25; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 0 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 196243 | 01:59:59 | 30885.00 | 30894.00 | 30864.25 | 30874.50 | 1081 | -69 | 1 |
| 196244 | 02:18:23 | 30874.00 | 30902.75 | 30865.50 | 30865.50 | 2284 | -22 | 0 |
| 196245 | 02:37:48 | 30865.25 | 30877.00 | 30853.50 | 30864.00 | 2286 | 14 | 0 |
| 196246 | 02:53:44 | 30864.75 | 30879.75 | 30839.50 | 30849.25 | 2286 | -6 | 0 |

Full replay window (400 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/structure_inside_outside_LONDON_v1_bars.csv`.
Rule check from the printed rows: outside bar = high 30879.75 > prior high 30877.00 and low 30839.50 < prior low 30853.50 -> True; close position (c-l)/(h-l) = 0.2422 (cf 0.75: long needs >= 0.75, short needs <= 0.25); EMA(20) of closes over the continuous series (seeded at the first bar of the row; 400-bar window replay equals the full-series value to 1e-9) = 30859.036; close 30849.25 is below the EMA -> side -1. Adjustment for contract rolls inside the window: 0.00 pt.
Replay of the book code (module `signal_fn` on exactly these rows): fires **[-1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [(392, 1)].
Bar row `dol_2600` on that day: closes at cumulative price x 5 x size >= 2600 x 300000 x s_dol = 2600 x 300000 x 1.8083 = **1410501169.0** (price in ticks; trading date 20261002).

**Vector LO1-2 (LONG)**: signal 2026-10-06 06:16:10 ET (epoch s 1791281770, bar row `dol_2600`, bar index 196709 in the continuous row, sess_id 202610061); engine entry 2026-10-06 06:16:11 ET at **31430.375** (2 lots, A-set trade), exit 2026-10-06 06:21:45 ET at 31440.500 (Target).
Signal-bar close (the price at which the signal is true) = 31431.50; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 0 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 196706 | 05:05:50 | 31382.00 | 31413.50 | 31380.75 | 31408.25 | 2283 | 251 | 0 |
| 196707 | 05:23:08 | 31408.50 | 31418.00 | 31387.25 | 31408.75 | 2282 | -6 | 0 |
| 196708 | 05:51:46 | 31407.00 | 31426.75 | 31402.50 | 31425.25 | 2282 | 174 | 0 |
| 196709 | 06:16:10 | 31425.75 | 31435.00 | 31393.00 | 31431.50 | 2282 | 218 | 0 |

Full replay window (400 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/structure_inside_outside_LONDON_v2_bars.csv`.
Rule check from the printed rows: outside bar = high 31435.00 > prior high 31426.75 and low 31393.00 < prior low 31402.50 -> True; close position (c-l)/(h-l) = 0.9167 (cf 0.75: long needs >= 0.75, short needs <= 0.25); EMA(20) of closes over the continuous series (seeded at the first bar of the row; 400-bar window replay equals the full-series value to 1e-9) = 31385.492; close 31431.50 is above the EMA -> side 1. Adjustment for contract rolls inside the window: 0.00 pt.
Replay of the book code (module `signal_fn` on exactly these rows): fires **[1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `dol_2600` on that day: closes at cumulative price x 5 x size >= 2600 x 300000 x s_dol = 2600 x 300000 x 1.8374 = **1433205027.8** (price in ticks; trading date 20261006).


## 5. NY AM `levels_fibr_or break_native` {k 0.25, n 3}, bracket 60/60, both sides (set TL3_DX_NY_REPL_c5_A, event file REPL_NY_c5)

**Bar type: ONE row, `vrb_40000`** (volume-run bar, Lopez de Prado run bar on volume). SPEC `build_month.py` L114-117 and `kernels.py` `k_imb` (wmode 1 = volume, run = 1): w = trade size; side b = aggressor side of the print (tick rule from the price change when the side is 0, else the previous side); trade-level EWMAs with alpha = 1 / max(T0, 10); a bar closes when `max(sum of w over buys, sum over sells) >= E[T] x max(P(buy) x E[w|buy], P(sell) x E[w|sell])`; **T0 = max(10, 40000 x s_n)** where s_n = scale of the daily print count (trailing median of the 20 prior dates / R0); E[T] starts at T0 and after every closed bar is updated `E[T] = 0.8 x E[T] + 0.2 x (prints in the closed bar)` and clamped to [0.25 x T0, 4 x T0]; per print: a = 1 / max(T0, 10), P(buy) += a x (1 - P(buy)) on a buy print and += a x (0 - P(buy)) on a sell print, E[w|buy] (init 1) and E[w|sell] (init 1) are EWMAs of w over buy / sell prints, P(buy) starts 0.5; the bar sums thb / ths (sum of w over buys / sells) restart at 0 with each bar while the EWMAs and E[T] carry over inside the session; all state re-initialised at every session change and contract change; the first bar of a session starts with E[T] = T0. Closing print stays in the bar. The bars are very large (about 100 pt range): the vector days show bars of 1-2 hours. **This is a stateful bar type that exists only in this research code (BAR_REGISTRY: "custom BarsType (new code)"); it needs the aggressor side per print; I give the rule from the kernel docstring, the exact arithmetic is the kernel (`kernels.py` L97-160) and has to be ported, not re-derived.**

**Session window**: NY AM 09:30-12:00 ET (code 3). Bell 12:00 ET. In practice the lines exist only from 09:45 ET (opening range), so no signal before 09:45.

**Signal (SPEC `lv_base.py`, `fd_common.py`, `lv_fibr_or.py`, `fd_levels2.py` L132-137)**: level set = 18 lines of the 15-minute opening range: OR15 = high / low of the minutes 09:30-09:45 ET of the day, R = H - L, **only when R >= 8 pt**, available from 09:45 ET (minute i uses minutes < i): `FIBR_OR_DN{236,382,500,618,650,786}` = H - r x R; `FIBR_OR_UP{...}` = L + r x R; `FIBR_OR_XU{1272,1618,2000}` = H + (e - 1) x R; `FIBR_OR_XD{1272,1618,2000}` = L - (e - 1) x R. Variant `break_native`, k = 0.25, n = 3, u = native unit (section 2). For a line value L at the signal bar (frozen at its decision time):
 - long: the last 3 closes (bars j-2, j-1, j) are all > L + 0.25 x u AND the close of bar j-3 is <= L + 0.25 x u (the hold sequence started fresh); short mirror with `< L - 0.25 x u` and `c[j-3] >= L - 0.25 x u`; every close is compared against the SAME L (the level at bar j), not each bar's own line value;
 - EDGE of that condition, first firing line recorded, both-sided dropped. No signal when u or L is NaN.
**Warm-up**: 20 prior bars of the row for u (the row is continuous across sessions, so only at row start), plus the opening range of the day.
**Bracket**: stop 60, target 60, 2 lots, bell exit 12:00.


### Test vectors for NY5 (real data on this box, both replayed)

**Vector NY5-1 (SHORT)**: signal 2026-10-01 10:30:59 ET (epoch s 1790865059, bar row `vrb_40000`, bar index 13295 in the continuous row, sess_id 202610013); engine entry 2026-10-01 10:31:00 ET at **30636.750** (2 lots, A-set trade), exit 2026-10-01 10:37:05 ET at 30693.625 (Stop).
Signal-bar close (the price at which the signal is true) = 30639.25; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 0 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 13290 | 08:29:59 | 30885.25 | 30908.75 | 30830.00 | 30858.75 | 9320 | -264 | 1 |
| 13291 | 09:29:59 | 30856.75 | 30878.50 | 30790.00 | 30797.00 | 19026 | -516 | 1 |
| 13292 | 09:39:01 | 30796.50 | 30856.00 | 30734.25 | 30830.50 | 43796 | -200 | 0 |
| 13293 | 09:55:42 | 30830.50 | 30841.25 | 30700.50 | 30783.50 | 44685 | -1047 | 0 |
| 13294 | 10:10:50 | 30783.50 | 30785.00 | 30590.00 | 30701.25 | 46306 | -270 | 0 |
| 13295 | 10:30:59 | 30701.50 | 30705.00 | 30560.75 | 30639.25 | 46345 | -807 | 0 |

Full replay window (130 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/levels_fibr_or_break_NYAM_v1_bars.csv`; per-bar inputs `levels_fibr_or_break_NYAM_v1_inputs.csv`.
Level inputs: firing line `FIBR_OR_DN236`; unit u (trailing median bar range over the previous 100 bars, floor 0.5) at the signal bar = 109.625 pt; decision second (t_close of the previous bar) = 1790863850 (10:10:50 ET).
Line `FIBR_OR_DN236` at each shown bar (value at that bar's decision time): 13290: nan, 13291: nan, 13292: nan, 13293: nan, 13294: 30827.268, 13295: 30827.268.
Independent re-implementation (written from the rule text, not the module) on the 130 rows x 18 lines: side at the signal bar = -1 (module: -1); signals at the 9 bars before it: [].
Replay of the book code (module `signal_fn` on exactly these rows + the stored line values): fires **[-1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `vrb_40000` on that day: run-bar start expectation T0 = max(10, 40000 x s_n) = 40000 x 0.9817 = **39266.2** prints (trading date 20261001).

**Vector NY5-2 (LONG)**: signal 2026-10-05 10:18:32 ET (epoch s 1791209912, bar row `vrb_40000`, bar index 13330 in the continuous row, sess_id 202610053); engine entry 2026-10-05 10:18:33 ET at **31194.000** (2 lots, A-set trade), exit 2026-10-05 10:57:58 ET at 31254.000 (Target).
Signal-bar close (the price at which the signal is true) = 31191.00; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 0 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 13325 | 01:59:59 | 31061.75 | 31090.50 | 31021.00 | 31044.75 | 12209 | -291 | 1 |
| 13326 | 07:14:37 | 31045.50 | 31099.25 | 30957.50 | 31000.50 | 43769 | -139 | 0 |
| 13327 | 08:29:59 | 31000.75 | 31070.25 | 30982.75 | 31000.25 | 11398 | 24 | 1 |
| 13328 | 09:29:59 | 31000.25 | 31060.00 | 30965.00 | 31055.75 | 16060 | 1286 | 1 |
| 13329 | 09:47:11 | 31055.50 | 31229.50 | 31044.25 | 31172.25 | 44162 | 338 | 0 |
| 13330 | 10:18:32 | 31172.50 | 31214.75 | 31115.00 | 31191.00 | 46362 | -6 | 0 |

Full replay window (130 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/levels_fibr_or_break_NYAM_v2_bars.csv`; per-bar inputs `levels_fibr_or_break_NYAM_v2_inputs.csv`.
Level inputs: firing line `FIBR_OR_XD1272`; unit u (trailing median bar range over the previous 100 bars, floor 0.5) at the signal bar = 106.500 pt; decision second (t_close of the previous bar) = 1791208031 (09:47:11 ET).
Line `FIBR_OR_XD1272` at each shown bar (value at that bar's decision time): 13325: nan, 13326: nan, 13327: nan, 13328: nan, 13329: nan, 13330: 30998.758.
Independent re-implementation (written from the rule text, not the module) on the 130 rows x 18 lines: side at the signal bar = 1 (module: 1); signals at the 9 bars before it: [(13322, -1)].
Replay of the book code (module `signal_fn` on exactly these rows + the stored line values): fires **[1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [(121, -1)].
Bar row `vrb_40000` on that day: run-bar start expectation T0 = max(10, 40000 x s_n) = 40000 x 0.9868 = **39472.9** prints (trading date 20261005).


## 6. NY AM `levels_prior_day false_break` {M 1, k 0.0}, bracket 120/120, both sides (set TL3_DX_NY_REPL_c1_A, event file REPL_NY_c1)

Plain variant `false_break` (tolerances in fixed points, u0 = 5.0 pt; NOT `_native`). With k = 0 the unit does not matter for this cell.

**Bar type: a SET of rows; true when ANY signals (union)**: `dchg_20`, `kagi_20` and `swing_atr_0.25`. **`dchg_20` and `kagi_20` are the SAME bars** (`build_month.py` L127-128 call the same kernel `k_dchg` with the same theta; their event sets are identical, 25,753 each), so there are TWO distinct bar series:
- `dchg_20` = `kagi_20`: directional-change legs (`kernels.py` k_dchg L197-230): reversal theta = **max(2, round(20 x s_rng)) ticks** where s_rng = trailing median of the 20 prior dates' daily range / R0; a bar = the leg from one confirmed extreme to the next (open = leg start, close = leg end; an up leg has h = c, an down leg has l = c), known at the print that confirms the reversal by theta ticks; reset at session / contract change; the unfinished leg at the session end is emitted as nothing.
- `swing_atr_0.25`: the same kernel with theta = **max(2, round(0.25 x ATR))** ticks, ATR = max(1, 4 x abs_rng / 10), abs_rng = trailing median of the 20 prior dates' daily range (`scales()['abs_rng']`); (on 2026-10-01 theta = 41 ticks = 10.25 pt, the minimum leg in the vector window is 10.25 pt: consistent).
Replay evidence: union of the three rows = 33,082 = the file; per row 25,753 / 25,753 / 26,957.

**Session window**: NY AM 09:30-12:00 ET (code 3). Bell 12:00 ET.

**Signal (SPEC `fd_common.py` `level_events` variant `false_break`, `lv_prior_day.py`)**: level set `PRIOR_DAY` = `PD_RTH__H`, `PD_RTH__L` (high / low of the prior RTH session 09:30-16:00 ET), `PD_FULL__H`, `PD_FULL__L` (high / low of the whole prior trading date, 18:00-18:00 ET), `PD_C__C` (close of the minute 15:59 ET of the prior trading date); "prior" = the previous trading date present in the minute file; values are known all day. Params M = 1, k = 0.0:
 - up(j) = `c[j] > L[j]` (L at bar j's own decision time), dn(j) = `c[j] < L[j]`;
 - `ru` = up true in any of the M = 1 bars before j (bar j-1 only), `rd` likewise;
 - short event bar: `ru and c[j] < L[j]` (a close above the level on the previous bar, a close back below it now: failed upside break -> short); long: `rd and c[j] > L[j]`;
 - EDGE of that condition, first firing line recorded, both-sided bars dropped.
**Warm-up**: previous bar and the prior trading date's levels (the first day of data has none).
**Bracket**: stop 120, target 120, 2 lots, bell exit 12:00.


### Test vectors for NY1 (real data on this box, both replayed)

**Vector NY1-1 (SHORT)**: signal 2026-10-01 10:01:06 ET (epoch s 1790863266, bar row `swing_atr_0.25`, bar index 792511 in the continuous row, sess_id 202610013); engine entry 2026-10-01 10:01:07 ET at **30676.500** (2 lots, A-set trade), exit 2026-10-01 11:08:07 ET at 30556.500 (Target).
Signal-bar close (the price at which the signal is true) = 30667.00; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
One-position check: 68 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 792508 | 10:00:10 | 30733.00 | 30744.00 | 30733.00 | 30744.00 | 119 | -33 | 0 |
| 792509 | 10:00:12 | 30744.00 | 30744.00 | 30721.50 | 30721.50 | 208 | -72 | 0 |
| 792510 | 10:00:15 | 30721.50 | 30741.25 | 30721.50 | 30741.25 | 200 | 18 | 0 |
| 792511 | 10:01:06 | 30741.25 | 30741.25 | 30667.00 | 30667.00 | 3995 | -639 | 0 |

Full replay window (130 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/levels_prior_day_false_break_NYAM_v1_bars.csv`; per-bar inputs `levels_prior_day_false_break_NYAM_v1_inputs.csv`.
Level inputs: firing line `PD_RTH__L`; unit u (fixed 5.0 pt) at the signal bar = 5.000 pt; decision second (t_close of the previous bar) = 1790863215 (10:00:15 ET).
Line `PD_RTH__L` at each shown bar (value at that bar's decision time): 792508: 30680.750, 792509: 30680.750, 792510: 30680.750, 792511: 30680.750.
Independent re-implementation (written from the rule text, not the module) on the 130 rows x 5 lines: side at the signal bar = -1 (module: -1); signals at the 9 bars before it: [].
Replay of the book code (module `signal_fn` on exactly these rows + the stored line values): fires **[-1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `swing_atr_0.25` on that day: reversal theta = max(2, round(0.25 x ATR)), ATR = max(1, 4 x abs_rng/10) = 164.0 (abs_rng 410.00) -> **41 ticks** (trading date 20261001).

**Vector NY1-2 (LONG)**: signal 2026-10-05 09:31:48 ET (epoch s 1791207108, bar row `dchg_20`, bar index 727023 in the continuous row, sess_id 202610053); engine entry 2026-10-05 09:31:49 ET at **31087.875** (2 lots, A-set trade), exit 2026-10-05 09:43:00 ET at 31208.000 (Target).
Signal-bar close (the price at which the signal is true) = 31098.00; engine entry = signal second + 1.000 s (market, tape fill, 2 lots, slippage as the engine fill model).
This signal second also appears in rows: `dchg_20,kagi_20,swing_atr_0.25` (same event, union stream; counted once).
One-position check: 0 further events of the stream fall between this entry and its exit; trades opened on any of them in the engine run: 0.

| idx | t_close (ET) | o | h | l | c | v | dlt | part |
|---|---|---|---|---|---|---|---|---|
| 727020 | 09:30:08 | 31067.50 | 31067.50 | 31051.50 | 31051.50 | 954 | -98 | 0 |
| 727021 | 09:30:21 | 31051.50 | 31069.00 | 31051.50 | 31069.00 | 1134 | -144 | 0 |
| 727022 | 09:30:58 | 31069.00 | 31069.00 | 31044.25 | 31044.25 | 2254 | -218 | 0 |
| 727023 | 09:31:48 | 31044.25 | 31098.00 | 31044.25 | 31098.00 | 3677 | 195 | 0 |

Full replay window (130 bars, o h l c v dlt t_close sess_id bidx part): `autopilot/book_vectors/levels_prior_day_false_break_NYAM_v2_bars.csv`; per-bar inputs `levels_prior_day_false_break_NYAM_v2_inputs.csv`.
Level inputs: firing line `PD_C__C`; unit u (fixed 5.0 pt) at the signal bar = 5.000 pt; decision second (t_close of the previous bar) = 1791207058 (09:30:58 ET).
Line `PD_C__C` at each shown bar (value at that bar's decision time): 727020: 31070.000, 727021: 31070.000, 727022: 31070.000, 727023: 31070.000.
Independent re-implementation (written from the rule text, not the module) on the 130 rows x 5 lines: side at the signal bar = 1 (module: 1); signals at the 9 bars before it: [].
Replay of the book code (module `signal_fn` on exactly these rows + the stored line values): fires **[1]** on the last bar, nothing else on it: PASS; other signals in the 9 bars before: [].
Bar row `dchg_20` on that day: reversal theta = max(2, round(20 x s_rng)) = max(2, round(20 x 2.2885)) = **46 ticks** (trading date 20261005).


## 7. DAILY SCALE CONSTANTS used by the bar rows (SPEC `th_bars/build_month.py` scales(); computed with the code, checked against the stored bars)

R0 (median of the first 60 trading dates, Apr-Jun 2023): daily volume 610,702; daily print count 373,169; daily dollar volume 169,605,053,025; daily range 191.5 (ticks, kernel units); scale s_c = (median of the 20 PRIOR trading dates' daily value, at least 5 non-zero days, else R0) / R0. The same scales applied on one trading date for every session of that date (the date rolls at 18:00 ET).

| trading date | s_vol | s_n | s_dol | s_rng | abs_rng (ticks) | abs_vol |
|---|---|---|---|---|---|---|
| 2026-10-01 | 0.8424 | 0.9817 | 1.8083 | 2.1410 | 410.00 | 514,458 |
| 2026-10-02 | 0.8424 | 0.9817 | 1.8083 | 2.1410 | 410.00 | 514,458 |
| 2026-10-05 | 0.8571 | 0.9868 | 1.8374 | 2.2885 | 438.25 | 523,444 |
| 2026-10-06 | 0.8571 | 0.9868 | 1.8374 | 2.2885 | 438.25 | 523,444 |

Check against the stored bars: vol_1100 on 2026-10-01 NY PM: threshold 1100 x 0.8424 = 926.64; the stored bars have volume 927 (min = median, max 934 in the 69 bars): consistent. vol_750 on the same date: 631.80 -> stored 632. READING: identical scales on 1-2 Oct and on 5-6 Oct look odd (all five series equal on consecutive dates); the stored bars agree with them, so they are what was used; I did not investigate why consecutive dates repeat.
The full per-date table = `/mnt/l2/l2vast/_bars/stats_day.parquet` (812 trading dates, 2023-04-03 .. 2026-11-13, file dated 17 Nov 18:16Z) fed through `scales()`; **a build in NT8 needs this table or the same formula over the same daily statistics (volume / prints / dollar volume / range per trading date, defined in `th_bars/stats.py`)**.

## 8. WHAT CANNOT BE GIVEN EXACTLY (said plainly)

1. **NY PM canc_follow feature** (`b_cancA`, `b_cancB`): defined by `featc.py` `_addcanc` over 10-level mbp-10 snapshots at 100-ms record resolution and the print aggressor sides; I describe it (section 1) but the exact per-case arithmetic is the numba function; a Mono port must port that function, and it needs the same 10-level book stream live. The vectors give stored float16 values, not a recomputation from raw book records (not done here: raw history days are large; OPEN, can be run on request).
2. **Level lines** (PD, FIBR_OR, TL5 / TL15, MM5 / MM15 / MM60) are minute-grid arrays from `fd_levels.py` / `fd_levels2.py`: the rules are stated in sections 2, 3, 5, 6 but the pivot / zigzag details (tie handling in the fractal test, the "later same-type pivot replaces only if more extreme" rule, age limits) are code; the vectors give the stored values and the module replay uses them. I did NOT recompute the lines from the 1-minute grid for the vectors (OPEN, quick to do if wanted).
3. **Run-bar `vrb_40000`, trade-size-filtered `tsf_5_400`, dollar `dol_2600`, leg bars `dchg_20` / `swing_atr_0.25`, scaled volume bars** are research-built custom bar types (BAR_REGISTRY.csv "nt8_fidelity" column: vol differs from NT8 native by the closing-print split; dol / tsf / vrb / dchg / swing have no native counterpart). Their rules are given from the kernels; reproducing the same bars outside this code base needs the kernels ported and the daily scale table (section 7).
4. **The `tsf` OHLC convention**: BAR_REGISTRY.md says OHLC uses only counted prints; the kernel uses all prints (section 3). The bars on disk follow the kernel.
5. **Entry price**: the engine entry price in the vectors includes the engine fill model on the 2-lot order (market, first tape print at or after signal + 1 s, slippage); it is not a simple function of the bar rows. The vectors give the engine price plus the signal-bar close.
6. **Event-file membership of multi-row books** (NP2, NY1) is what the files contain (section 0 and the book sections); whether the build should use the union of rows or one row is a decision for the lead, not something the code settles. The screen statistics on REPLACE_CANDIDATES.md for these two cells were computed per bar-row event file (`th_planas/cand2.py` takes one EVFILE; counts n L / S there, 4,138 / 4,356 for NP2 and 1,501 / 1,540 for NY1, versus 1,792 and 1,024 trades in the exact one-slot union runs): READING that they are per-file sums, NOT verified by re-running the screen. OPEN: the "exact-confirmed" label is for the union stream.
7. **Net dollars**: my `net_fee` sums are about 3% above the figures on REPL_EXACT_SCORES.md (trade counts equal); the page's "net" definition was not re-derived (OPEN).
8. Two other pieces of the build are not in this page: the layer stack around the book (Trade Health / zones / caps) in the mixes, and lots in the mixes; the A-set (alone, bare, 2 lots) is what is specified here.
9. **Bar open time live**: the tested harness never sees a bar open time (section 0.2, cross-session consequence); a live port that uses the real bar open time for the level lookup would read different line values on the first bar after a break or a long bar (AS1-1). Which convention the live build should follow is a lead decision, not settled by the tests (OPEN).

## 9. ITEM 5: BE / PL / NT KEYS PER BOOK (own units)

**Which file is the match file**: `autopilot/EXIT_MGMT_SUNDAY.md` section 5 itself names `autopilot/EXIT_MGMT_SUNDAY_MATCH.md` ("W-DYNA, DONE") as the per-bar match rows; the match file's own header reads "EXIT_MGMT_SUNDAY_MATCH (W-DYNA for W-SUNDAY; generated 27 Nov 20:42Z UTC): per-second match rows for BE70 / PL70K50 / NT70K25" (335,120 bytes, 30 trade sections: BE70 SAVED + COST for each of 13 books, plus PL70K50 and NT70K25 for NY-FIB and NY-NODE). **Confirmed: it is the match file.**

**Cross-check of the 13 books** (programmatic): for each of AS-NR7, AS-RSI, AS-VWAPBRK, LO-CRUDE, LO-ZB, NP-ZN, NP-YM, NP-CONF, NP-MACD, NY-FIB, NY-VALUE, NY-NODE, NY-OFI the stop / target on the section 5 table (S0 / T0) equals the S0 / T0 in both match sections' headers, the BE70 arm = 0.70 x T0, and NT70K25 trail = 0.25 x T0 to the printed precision. The key strings are the same three for every book (`BE=0.70:0`, `PL=0.70:0.50`, `NT=0.70:0.25`; only the arm / trail points differ because they are fractions of the book's own target): **no mismatch between the two files.**

**The six replacement books are NOT on either file** (the word REPL appears once in EXIT_MGMT_SUNDAY.md, in no table; zero times in the match file or the keys file). Their strings by the same rule, **DERIVED, UNTESTED** (arm = 0.70 x target distance; PL stop = entry + 0.5 x best; NT trail = 0.25 x target distance behind the best):

| replacement book | stop / target pts | BE70 | PL70K50 | NT70K25 |
|---|---|---|---|---|
| NY PM canc_follow (NP c1) | 90 / 90 | BE=0.70:0 (arm 63.0 pt) | PL=0.70:0.50 (arm 63.0 pt) | NT=0.70:0.25 (arm 63.0 pt, trail 22.5 pt) |
| NY PM trendline reject_native (NP c2) | 90 / 90 | BE=0.70:0 (arm 63.0 pt) | PL=0.70:0.50 (arm 63.0 pt) | NT=0.70:0.25 (arm 63.0 pt, trail 22.5 pt) |
| Asia mmove retest_native (AS c1) | 60 / 60 | BE=0.70:0 (arm 42.0 pt) | PL=0.70:0.50 (arm 42.0 pt) | NT=0.70:0.25 (arm 42.0 pt, trail 15.0 pt) |
| London structure_inside outside (LO c1) | **60 / 10** (stop / target) | BE=0.70:0 (arm 7.0 pt) | PL=0.70:0.50 (arm 7.0 pt) | NT=0.70:0.25 (arm 7.0 pt, trail 2.5 pt = 10 ticks) |
| NY AM fibr_or break_native (NY c5) | 60 / 60 | BE=0.70:0 (arm 42.0 pt) | PL=0.70:0.50 (arm 42.0 pt) | NT=0.70:0.25 (arm 42.0 pt, trail 15.0 pt) |
| NY AM prior_day false_break (NY c1) | 120 / 120 | BE=0.70:0 (arm 84.0 pt) | PL=0.70:0.50 (arm 84.0 pt) | NT=0.70:0.25 (arm 84.0 pt, trail 30.0 pt) |

The page table orders "stop / target"; so does this table (London 60 / 10; the screen label "10/60" is target / stop). Whether BE70 on a 10-pt target (arm 7 pt) has ever been run on London: no.

**Mismatches / unit traps found on the page (none changes a tested number)**:
1. EXIT_MGMT_SUNDAY.md says "12 edge books" (answer-first lines 1, 2, 5; "PY filter on 7 of the 12") but its section 1 / 5 tables and the match file carry **13** books (11 live plus NP-MACD and NP-CONF, as its own sentence says). The count 12 is a text slip or one book is excluded from the sums: OPEN, ask W-SUNDAY.
2. AS-VWAPBRK NT trail is printed "11.2 pt"; 0.25 x 45 = 11.25 exactly (rounding to one decimal, half-even). The engine uses 11.25. Build with the fraction, not the printed number.
3. The new key `BE=<pct>:<offset_pts>` is written with the offset in POINTS, but the engine recipe `be50 [pct, off]` takes the offset in TICKS (`dx_multi.py` L138: stop = entry + off x 0.25). All tested rows use offset 0, so nothing differs; any non-zero offset typed in points would be 4x wrong.
4. Unit trap between the page strings and the raw engine keys: the page strings are in TARGET units (arm = 70% of the target distance; trail = 0.25 x target), the raw engine recipes `peaklock [arm_R, frac]` and `neartgt [pct, k_R]` take the arm / trail in units of the stop distance (RISK) (`dx_multi.py` L133-137); the Sunday sets convert (`th_sunday/sun_build.py` L17, L19: `peaklock = [a/100 x T/S, k/100]`, `neartgt = [p/100, k/100 x T/S]`). The page and the match file follow the converted (target-unit) meaning, so they agree with each other; anyone feeding the page's numbers straight into the raw engine keys on a book with stop != target (AS-NR7 40/80, LO-CRUDE 90/30, LO-ZB 120/60, NP-YM 80/40, NP-MACD 90/30, NY-NODE 90/30, and the London replacement 60/10) would get a different arm and trail.

## 10. FILES

Page: `autopilot/BOOK_SPECS_REPLACEMENT.md` (this). Vectors: `autopilot/book_vectors/<book>_v<1|2>_bars.csv` (replay window: abs_idx, sess_id, bidx, t_close, t_close_et, o, h, l, c, v, dlt, part) and `_inputs.csv` (stored line values per bar, or `b_cancA` / `b_cancB` for NP c1; none for London, whose EMA is derived from the rows). Code used: `th_grid/gjob.py` load_bars, the six modules above, `th_swap/iface.py`; event files `_dynexit/ev/REPL_*.parquet`; engine trades `_th_sz/ijk/exact/runs_rf/TL3_DX_*_REPL_c*_A/<YYYYMM>/trades.parquet`. Replay was run at nice 15 on box 1 (read only; one 10-minute read on server C to list which bar rows hold each cell's events: `_negbook/ev/*.parquet`).
