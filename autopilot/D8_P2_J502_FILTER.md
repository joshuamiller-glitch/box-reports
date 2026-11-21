# D8_P2_J502_FILTER: the exact entry filter of L385f4f2e.J502 (pass-2 final book of W-P2A) = confluence C1 setting 5 + time window C3 setting 2, with per-event values (W-D8SPEC, relay order 0750Z)

Documentation only. Everything below was recomputed by me from the stored `_CANC` vol_2600 bars, the 1-minute level store, the other-market store and the module code, and checked against the engine's own flag file `/mnt/l2/l2vast/_pass2c/flags/TL3_ASI_L385f4f2e_RA7.parquet` (W-P2A): **my count of true conditions per event equals the stored `nconf_C1_X10_5_084f2c` on all 1,507 parent events (0 mismatches)**, and my C3 flag equals the stored one on all of them. The filtered event file is `/mnt/l2/l2vast/_pass2/jev/L385f4f2e_CX502.parquet` (815 events) = set `TL3_ALN_AS_L385f4f2e_P2JCX502`.

## 0. Summary: what J502 is, and the counts
- **Parent book:** L385f4f2e = vol_2600 bars (D8 `_CANC` print rule) + trig_momentum_rsi mom (RSI 14, cross up through 60 = long, cross down through 40 = short), bracket plain 60/60, Asia session only (D8_TRIGDEBUG_L385f4f2e.md).
- **Filter J502 = C1 setting `C1_X10_5_084f2c` AND C3 setting `C3_dropblk10`. No C2 component (no market-type gate), no flips.** A parent event survives iff (number of true conditions among the 10 listed in section 1) >= 5 AND (the signal time is NOT in Asia 30-minute block 10). A surviving event is traded exactly as the parent (same side, same bracket); nothing is flipped, resized or retimed. Skipped events free the one-position slot, so later parent events can be traded instead (the walker re-blocks).
- **Counts over the whole history (Asia sessions 2023-04 to 2026-11-13): parent events 1,507; after C1 alone 847; after C3 alone 1,446; after both 815.** Per year:

| year | parent | C1 | C3 | both |
|---|---|---|---|---|
| 2023 | 227 | 102 | 217 | 98 |
| 2024 | 316 | 179 | 306 | 173 |
| 2025 | 428 | 246 | 409 | 237 |
| 2026 | 536 | 320 | 514 | 307 |

- Distribution of the number of true C1 conditions per parent event (C1 needs >= 5):

| events with nconf = k | count |
|---|---|
| 0 | 5 |
| 1 | 27 |
| 2 | 82 |
| 3 | 203 |
| 4 | 343 |
| 5 | 373 |
| 6 | 273 |
| 7 | 155 |
| 8 | 44 |
| 9 | 2 |

## 1. C1 setting 5: "5 of these 10 conditions" (setting id `C1_X10_5_084f2c`, k = 5, N = 10)
Each condition is a yes/no value ORIENTED to the event side s (+1 long, -1 short): true = the condition supports a trade in that direction. All values are evaluated at the **signal bar close** (the bar whose close produced the RSI cross; known time t_c); nothing later is used. A condition whose data are missing counts as FALSE. **u** = the bar-native unit = trailing median of (high - low) of the last 50 vol_2600 bars including the signal bar (at least 10 bars, floor 0.25 point). **c** = close of the signal bar. Line values are read from the 1-minute store: the value at the last minute whose START is <= t_c (the stored value at minute i uses minutes < i only), valid only if t_c - minute_start <= 120 s, prices <= 0 invalid.

| # | condition | plain words | formula | data it reads | NinjaTrader from last/bid/ask ticks alone? | 10-level depth needed? |
|---|---|---|---|---|---|---|
| c1 | LV_OPENS_near_back_1u | an opening price or the prior RTH close sits just behind the trade | lines L in {OPEN_DAY (open of the 18:00 ET minute), OPEN_0000 (00:00 ET minute open), OPEN_0200 (02:00 ET minute open), OPEN_WEEK (open of the first minute of the ISO week, Sunday 18:00 ET), OPEN_MONTH (first minute of the month), PD_C (close of the 15:59 ET minute of the previous RTH day)}; D = s x (c - L); dback = smallest D among lines with D > 0 (lines BELOW a long, ABOVE a short); true if dback <= 1.0 x u | 1-minute opens/closes built from last ticks | YES (minute bars from ticks; OPEN_MONTH needs a month of history, engine artefact: November 2026 is anchored at 2026-11-05 16:00 UTC) | no |
| c2 | LV_FIB_react_0.5u | the signal bar's extreme just touched a Fibonacci retracement level behind the trade | levels = FIB15_R382/R500/R618/R786 and FIB60_R382/R500/R618/R786: for 15-min and 60-min bars aggregated from the 1-minute grid, fractal pivots (strength k = 2 bars each side, confirmed 2 bars after the pivot), alternating-pivot zig-zag, last leg B -> C, level = C - r x (C - B), valid for 10 days (15 min) / 30 days (60 min); ext = the signal bar's LOW for a long, HIGH for a short; true if some level with D = s x (c - L) > 0 has abs(ext - L) <= 0.5 x u | 1-minute bars aggregated to 15/60 min | YES in principle (pivot/zig-zag code must be ported exactly; the hardest condition) | no |
| c3 | LV_ROUND50_near_back_0.5u | a 50-point round number is just behind the trade | L in {floor(c/50) x 50, that + 50}; dback as in c1; true if dback <= 0.5 x u | price only | YES | no |
| c4 | LV_ROUND50_near_back_2u | the same round numbers within 2 units | as c3 with 2.0 x u | price only | YES | no |
| c5 | LV_SESSRUN_near_back_0.5u | the running high or low of the CURRENT session (before the signal bar) is just behind the trade | L in {highest high, lowest low of the session's vol_2600 bars BEFORE the signal bar (NaN on the first bar)}; dback as in c1; true if dback <= 0.5 x u | the bar series | YES | no |
| c6 | LV_side_PRF1__VAL | price is on the trade side of the previous RTH day's value-area low | s x (c - PRF1_VAL) > 0 (long: close above VAL; short: close below VAL); PRF1_VAL = the 70% value-area low of the previous RTH day's volume profile (D8_TRIGDEBUG_B7bfd33b7.md section 2) | RTH volume-by-price from ticks | YES (volume profile from last ticks, 1-tick bins) | no |
| c7 | GRID_trend_libstack:ema_stack | the 10/20/50 EMA stack of the bar closes points the trade's way | state = +1 if EMA10 > EMA20 > EMA50, -1 if reversed, else 0, on the vol_2600 closes of the continuous series (alpha = 2/(n+1), seed = first close of the series, no reset; D8_TRIGDEBUG_La010c3eb.md); true if s x state > 0 at the signal bar. Engine artefact: the closes are back-adjusted at instrument-id changes taken from the original store (up to 0.7% signal effect, D8_TRIGDEBUG note); a port should back-adjust only at the 14 real rolls | the bar series | YES (about 200 bars of history for 3 digits, 345 for 6) | no |
| c8 | DLTFRAC_gt0.1 | the signal bar's net aggressor volume leans the trade's way | s x (bar delta / bar volume) > 0.1, delta = buy-aggressor minus sell-aggressor contracts of the bar (D8 side rule) | last/bid/ask side per tick | YES (quote-rule side = the D8 rule) | no |
| c9 | XM_ES_own5_agree_gt1 | ES moved the trade's way over the last 5 minutes by more than 1 own-sigma | z = r5 / sigma where r5 = ES close(k) / ES close(k-5) - 1 on the 1-minute grid (k = the last COMPLETED minute before t_c; NaN if any of the two closes is missing or the contract changed inside the window), sigma = trailing std of r5 over the previous 4,320 grid minutes (72 clock hours, at least 600 valid values, shifted one minute); true if s x z > 1 | ES 1-minute closes (continuous front month) | NO from NQ ticks: needs ES 1-minute data (CQG subscription to ES; tick or minute bars) and 3 days of its history | no |
| c10 | XM_YM_own15_agree_gt0 | YM moved the trade's way over the last 15 minutes | same with YM and 15 minutes; true if s x z > 0 (the sign of the 15-minute YM return) | YM 1-minute closes | NO from NQ ticks: needs YM data | no |

**Combining:** nconf = c1 + ... + c10 (each 0/1); **C1 flag = (nconf >= 5)**. Pass rates over the whole history (parent events 1,507):

| condition | events passing (of 1507, whole history) | pass rate % |
|---|---|---|
| c1 LV_OPENS_near_back_1u | 401 | 26.6 |
| c2 LV_FIB_react_0.5u | 1110 | 73.7 |
| c3 LV_ROUND50_near_back_0.5u | 315 | 20.9 |
| c4 LV_ROUND50_near_back_2u | 1100 | 73.0 |
| c5 LV_SESSRUN_near_back_0.5u | 263 | 17.5 |
| c6 LV_side_PRF1__VAL | 1069 | 70.9 |
| c7 GRID_trend_libstack:ema_stack | 1017 | 67.5 |
| c8 DLTFRAC_gt0.1 | 532 | 35.3 |
| c9 XM_ES_own5_agree_gt1 | 309 | 20.5 |
| c10 XM_YM_own15_agree_gt0 | 1014 | 67.3 |

## 2. C3 setting 2: time window `C3_dropblk10` = drop Asia 30-minute block 10
- **Rule:** the Asia session is cut into 30-minute blocks counted from its start at **18:00 ET** (block 0 = 18:00-18:30 ET ... block 10 = **23:00:00 to 23:29:59 ET**). An event is dropped if the SIGNAL BAR'S KNOWN TIME (before the +2 s), converted to America/New_York clock time with daylight saving applied, falls in block 10 (61 of the 1,507 parent events do; C3 flag = block != 10 = 1,446 events kept). All other blocks pass.
- **UTC equivalents:** while New York is on standard time (EST, UTC-5; early November to mid March) block 10 is **04:00:00-04:29:59 UTC**; while on daylight time (EDT, UTC-4; mid March to early November) it is **03:00:00-03:29:59 UTC**. The window follows the New York clock, so it moves one hour in UTC at the two changeovers (the engine uses the tz database; NT8 should use Eastern Standard/Daylight time conversion of the tick timestamp, not a fixed UTC offset).
- Data: the clock only. NT8: yes. Sensitivity: only events whose known time lies within the feed lag of 23:00:00 or 23:30:00 ET can flip (measured below: 0 of 1,507 at a 0.26 s lag).

## 3. Sensitivity to the measured feed-clock differences (CQG stamps lag the exchange stamps: median about 0, p99 +43 ms, max +0.26 s in Asia; NY AM p99 +0.59 s, max +1.58 s)
I re-evaluated the conditions with the signal bar's known time shifted LATER by the lag (what an NT8 stamped by CQG would see), keeping the bars themselves exact (bars are built from the identical contract stream; D8_FEED_CHECK.md section 7):

| lag (s) | conditions that change (number of events, out of 1,507) | events whose C1 flag changes | events whose C3 flag changes | events whose survival changes | survivors |
|---|---|---|---|---|---|
| 0.26 | XM_YM 2 | 0 | 0 | 0 | 815 |
| 0.6 | XM_ES 2, XM_YM 6 | 1 | 0 | 0 | 815 |
| 1.58 | XM_ES 7, XM_YM 9 | 3 | 0 | 2 | 817 |

Reading: with the Asia maximum lag of 0.26 s only c10 (YM) changes, on 2 events, and no survival changes; at 1.58 s (the NY AM maximum, not relevant to Asia) 2 survival changes. The conditions c1-c6 read minute-grid lines, so they can only change when the event falls within the lag of a minute boundary; c9/c10 read the last COMPLETED other-market minute, with the same boundary exposure; c7, c8 and the bar rule do not depend on the clock at all, and C3 depends on it only at 23:00 and 23:30 ET. The conditions whose values lie close to their thresholds (for example c8 at 0.096 against 0.1 in the sample event) are fragile to ANY difference in the data (one contract of delta), not to the clock.

## 4. Per-event table for the sample sessions
Sessions: trading date 20261110 (the one event of J502 that date), 20261109 and 20261106 (the two most recent Asia sessions with at least 2 surviving events: 2 of 4 and 4 of 4). Each row is a PARENT event; columns give the underlying number of every condition and its pass flag, then nconf, C1, C3 and whether the event SURVIVES. 'none' = no backing line / no data. Times: signal bar known time UTC, event time = floor(known second) + 2.

| td | bar idx | signal bar known UTC | event UTC (+2 s) | side | close | u (50-bar median range, pts) | ET time | 30-min block (Asia, 0=18:00 ET) | c1 OPENS nearest backing distance (pts) / pass if <= 1u | c1 pass | c2 FIB touch distance of bar extreme (pts) / pass if <= 0.5u | c2 pass | c3 ROUND50 back dist (pts) / pass <= 0.5u | c3 pass | c4 ROUND50 pass <= 2u | c5 SESSRUN back dist (pts) / pass <= 0.5u | c5 pass | c6 side*(close - PRF1 VAL) pts, pass if > 0 | c6 pass | c7 libstack ema_stack aligned | c8 side*delta/volume (pass > 0.1) | c8 pass | c9 ES zown5 x side (pass > 1) | c9 pass | c10 YM zown15 x side (pass > 0) | c10 pass | nconf (of 10) | C1 (nconf>=5) | C3 (block != 10) | SURVIVES |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 20261106 | 216855 | 2026-11-05T23:11:41.119895303Z | 2026-11-05T23:11:43.000000000Z | -1 | 26521.25 | 62.875 | 18:11:41 | 0 | 119.00 | 0 | 145.27 | 0 | 28.75 | 1 | 1 | 62.75 | 0 | 301.75 | 1 | 1 | 0.161 | 1 | 2.44 | 1 | nan | 0 | 6 | 1 | 1 | 1 |
| 20261106 | 216865 | 2026-11-06T00:12:00.003905877Z | 2026-11-06T00:12:02.000000000Z | 1 | 26802.25 | 70.25 | 19:12:00 | 2 | 56.00 | 1 | 36.75 | 0 | 2.25 | 1 | 1 | 52.25 | 0 | -20.75 | 0 | 0 | 0.149 | 1 | 0.84 | 0 | 2.11 | 1 | 5 | 1 | 1 | 1 |
| 20261106 | 216874 | 2026-11-06T01:08:26.443508731Z | 2026-11-06T01:08:28.000000000Z | 1 | 26981.75 | 75.5 | 20:08:26 | 4 | 7.50 | 1 | 44.50 | 0 | 31.75 | 1 | 1 | 615.25 | 0 | 158.75 | 1 | 1 | 0.19 | 1 | 1.38 | 1 | -0.62 | 0 | 7 | 1 | 1 | 1 |
| 20261106 | 216879 | 2026-11-06T01:54:02.977539673Z | 2026-11-06T01:54:04.000000000Z | 1 | 26984.25 | 81.875 | 20:54:02 | 5 | 10.00 | 1 | 120.42 | 0 | 34.25 | 1 | 1 | 617.75 | 0 | 161.25 | 1 | 1 | 0.102 | 1 | 0.9 | 0 | 0.79 | 1 | 7 | 1 | 1 | 1 |
| 20261109 | 217158 | 2026-11-08T23:01:52.304836919Z | 2026-11-08T23:01:54.000000000Z | -1 | 26881.5 | 34.375 | 18:01:52 | 0 | 92.75 | 0 | 166.55 | 0 | 18.50 | 0 | 1 | none | 0 | 232.0 | 1 | 1 | -0.077 | 0 | nan | 0 | nan | 0 | 3 | 0 | 1 | 0 |
| 20261109 | 217164 | 2026-11-08T23:50:56.425341269Z | 2026-11-08T23:50:58.000000000Z | -1 | 26926.0 | 34.875 | 18:50:56 | 1 | 48.25 | 0 | 15.91 | 1 | 24.00 | 0 | 1 | 273.00 | 0 | 187.5 | 1 | 1 | 0.007 | 0 | 0.32 | 0 | 0.24 | 1 | 5 | 1 | 1 | 1 |
| 20261109 | 217169 | 2026-11-09T00:38:26.025150561Z | 2026-11-09T00:38:28.000000000Z | -1 | 26891.5 | 37.375 | 19:38:26 | 3 | 82.75 | 0 | 9.25 | 1 | 8.50 | 1 | 1 | 307.50 | 0 | 222.0 | 1 | 1 | 0.021 | 0 | 1.01 | 1 | 0.62 | 1 | 7 | 1 | 1 | 1 |
| 20261109 | 217180 | 2026-11-09T02:19:43.197817051Z | 2026-11-09T02:19:45.000000000Z | 1 | 27246.75 | 44.5 | 21:19:43 | 6 | 172.25 | 0 | 11.09 | 1 | 46.75 | 0 | 1 | 37.50 | 0 | 133.25 | 1 | 0 | 0.088 | 0 | 0.88 | 0 | 0.52 | 1 | 4 | 0 | 1 | 0 |
| 20261110 | 217448 | 2026-11-10T03:38:50.137134655Z | 2026-11-10T03:38:52.000000000Z | -1 | 27918.25 | 33.5 | 22:38:50 | 9 | 86.50 | 0 | 1.62 | 1 | 31.75 | 0 | 1 | 13.00 | 1 | -118.75 | 0 | 1 | 0.096 | 0 | 0.86 | 0 | 0.49 | 1 | 5 | 1 | 1 | 1 |

## 5. Which conditions NinjaTrader can compute (summary)
- **From last/bid/ask ticks of NQ alone:** c1 (minute opens), c3, c4 (price), c5 (bar series), c6 (volume profile of the previous RTH day), c7 (EMA stack of the bar closes), c8 (aggressor delta by the quote rule), C3 (clock), and c2 in principle (1-minute bars aggregated to 15/60 minutes plus a fractal-pivot zig-zag port; the most complex piece, needs about 10 to 30 days of history for the levels to exist).
- **Not from NQ ticks:** c9 (ES) and c10 (YM): they need the other markets' 1-minute closes (CQG data for ES and YM) and about 3 days of their history to form the 4,320-minute sigma. A J502 port without them cannot reach the engine's nconf: with only the 8 NQ conditions the threshold of 5 would have to be re-tested (each of c9/c10 alone passes 309 and 1014 of 1,507 events).
- **From 10-level depth:** none of the ten conditions reads the order book.
- **History NT8 must load:** the vol_2600 bar series (200-350 bars before the first bar tested, see the debug tables), the previous RTH day and 5-day profile are not needed (only PRF1_VAL), the weekly/monthly opens (up to 31 days of minutes; November 2026 anchored at 2026-11-05 16:00 UTC in the engine), the FIB swings (up to 10 days of 15-minute and 30 days of 60-minute bars from 1-minute data), ES and YM minutes for 72 hours, the previous RTH close.
