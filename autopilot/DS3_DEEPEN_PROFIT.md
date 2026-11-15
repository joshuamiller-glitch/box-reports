# DS3_DEEPEN_PROFIT - T-DEEPEN part 2, profit side (W-PA)

**VERDICT (plain, not a PASS): first-order screens done for items 1, 2, 3, 5; the exact engine has 0 of 158 queued set-months done (the box is at load 70 and tag PA has quota 1, so exact results are hours away). First-order leads: the Asia P7 pyramid (add 0.5 x lots after +15 pts) cuts equal-mean drawdown in every window but a random-time add after +15 does as well (placebo p 0.25), runner lots only help on a with-trend call and still fail X', structure trails help only in the recent windows (RECENT-ONLY) and fail HOLD/PRE mean, the ER trend sizer is inside its time-shift placebo band. Nothing is promoted.**

Rebuilt 2026-11-14 23:45Z by code/th_deepen_pa/pa_page.py. Prereg autopilot/DEEPEN_PA_PREREG.md (sha line in DECISIONS.md 2026-11-14T23:32Z). Tag PA, sets TL3_PA_* (56 sets), queue /mnt/l2/l2vast/_deepen_pa/pending.txt, code code/th_deepen_pa, bulk /mnt/l2/l2vast/_deepen_pa. Hook pa_hooks.py (ladders/trails modes 0-3, runner, ER sizer, sub-session gate, pyramid add, session-lot override); identity sets TL3_PA_ID, TL3_PA_SB_ID, TL3_PA_ID_R, TL3_PA_ID_ALL queued first (202610 must give 598 trades / 25,943.82).

**LOT BASIS**: engine dollars are BASE lots (live user lots x1.75; live caps = engine caps x1.75, JN05W2 P7 8,400 engine = 14,700 live); the engine charges $1.18/contract RT with its measured fills, FEES.md says $4.84. Every first-order $ column is on base lots with the engine's own net (fee $1.18); added contracts (pyramid) are charged $4.84 RT; a $4.84 repricing of a lot change = net - lots x $3.66 per trade.

Method note: sections 1-5 are FIRST-ORDER screens on the exact JN05W2 trades (43 months, entry-to-exit 1-second mid paths, nt_paths) with the live fill conventions (market exits at 1-s mid -1.0 pt, adds +0.5 pt). Re-entry flow, caps and the state cut are not modelled; the exact engine decides. Tolerant gate = maxDD not worse > 2%, worst week not worse > 2%, mean not lower > 3% of the stack mean; LEAD = passes in L3M, L6M, HOLD, PRE and X'; RECENT-ONLY = passes L3M and L6M, fails an older window.

**Prereg status**: the first prereg (sha 23:32Z) is frozen; addendum autopilot/DEEPEN_PA_PREREG_ADD1.md (new sha line in DECISIONS.md, before any exact cell was scored). Cells designed AFTER the first sha: ID_ALL, ADD_*, ER_*, PRESS_*, ADDM_*, ADDL_*, SS_*. First-order screens were used only to order the queue; no exact number is read until ID, SB_ID, ID_R, ID_ALL, SS_ID pass (598 / 25,943.82). The exact table has a $4.84 column (d484 = dmean repriced, net - lots x 3.66 per trade). P7 Asia pyramid is labelled TIMING ADDS NOTHING (random-time placebo p .25); its mirror (ADDM reduce at the pullback) and loss-side versions (ADDL cut / average-down) are queued, as are exact sub-session books SS_* (A7/P7/K7 Asia-late, M7 London-open, U7 Asia-open, M7 NY-AM-rest: the only first-order rows positive in all five windows) right after the identities.

dead_lookup: the five family specs (trail/lock/runner/session-book/EMA) returned NOT FOUND within tolerance (no EXACT/NEAR hit); append_cells for the scored first-order cells follows when a cell is promoted to exact.

## 1. Near-target lock ladders and structure trails (item 1)

Existing W-NT cells reused, not duplicated: fixed ladders (trig x lock x persist) for all books are in /mnt/l2/l2vast/_neartarget/ladder_grid*.parquet and their exact sets TL3_NT_* (U7 70/40 persist 3 is the only exact lead there: +1,220/wk L6M, DD +7.6% worse). NEW here: trails after a 60-90% trigger that follow the market: give-back from the running max (g .05-.3 T), EMA "Keltner mid" (span 120-1200 s), Donchian "swing" low (60-900 s), floors 0/.3 T, persist 1/3 s: 188 configs x 23 scopes x 7 windows = 30268 rows.

Cells 4324; recent gate (L3M and L6M) 911; LEAD 3 (all windows). Take on a book reading turning against a winner: the K7/M7/U7 profit-side state rules exist, P7/H7/A7 fits wait for the exact trail results (queued as part of the next block).

LEAD rows (mode 1 give-back, 2 EMA, 3 Donchian; d = delta mean $/wk base lots; cut = DD cut %):

| book | sess | mode | trig | pers | par | g | d3 | d6 | dh | dp | dx | cut3 | cut6 | cuth | cutp | cutx | nf |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7 | nyam | 3 | 0.8 | 3 | 900 | 0.0 | 153.2 | 41.1 | 127.8 | -9.3 | 44.6 | 0.0 | 0.0 | 0.1 | 0.0 | -1.4 | 0.6 |
| M7 | nyam | 1 | 0.9 | 1 | 0 | 0.3 | 139.0 | 117.9 | 272.2 | 7.2 | 12.5 | 0.0 | 0.0 | 0.9 | -1.5 | 0.2 | 0.7 |

RECENT-ONLY, top by L6M DD cut (stack and P7; every one of them LOSES mean in HOLD and PRE, i.e. the recent windows only):

| book | sess | mode | trig | pers | par | g | d3 | d6 | dh | dp | dx | cut3 | cut6 | cuth | cutp | cutx | nf |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | all | 3 | 0.7 | 1 | 900 | 0.0 | 5954.9 | 2319.4 | -1598.5 | -3205.5 | 433.1 | 29.4 | 29.4 | 5.2 | 8.7 | -3.6 | 33.9 |
| ALL | all | 1 | 0.7 | 1 | 0 | 0.3 | 4605.2 | 1195.9 | -1850.0 | -2845.6 | 700.0 | 25.1 | 25.1 | 10.5 | 14.4 | -0.0 | 45.9 |
| ALL | all | 3 | 0.7 | 3 | 900 | 0.0 | 5577.1 | 1594.0 | -1551.6 | -2736.8 | 201.1 | 24.7 | 24.7 | 4.4 | 15.3 | 5.5 | 31.8 |
| ALL | all | 1 | 0.7 | 3 | 0 | 0.3 | 4660.9 | 798.5 | -2152.5 | -2418.6 | 526.9 | 22.2 | 22.2 | 9.9 | 15.9 | 8.4 | 43.1 |
| ALL | all | 3 | 0.7 | 1 | 600 | 0.0 | 4531.0 | 1527.9 | -1489.4 | -3254.6 | 195.3 | 21.2 | 21.2 | 7.9 | 13.2 | -2.2 | 36.6 |
| ALL | all | 2 | 0.7 | 1 | 600 | 0.0 | 4504.2 | 1018.2 | -1357.6 | -2437.6 | -42.3 | 18.1 | 18.1 | 26.7 | 25.2 | -24.7 | 76.6 |
| ALL | all | 2 | 0.7 | 1 | 1200 | 0.0 | 4586.5 | 1104.9 | -1340.6 | -2424.2 | -75.4 | 18.1 | 18.1 | 26.6 | 25.0 | -25.0 | 76.3 |
| ALL | all | 3 | 0.7 | 1 | 180 | 0.0 | 4697.3 | 645.6 | -2501.2 | -2756.6 | -155.6 | 16.9 | 16.9 | 12.2 | 15.2 | -8.0 | 50.2 |
| ALL | all | 3 | 0.7 | 3 | 600 | 0.0 | 4444.3 | 1004.3 | -1433.6 | -2715.5 | -5.8 | 16.5 | 16.5 | 7.2 | 17.9 | 6.8 | 34.4 |
| ALL | all | 2 | 0.7 | 1 | 300 | 0.0 | 4313.8 | 802.8 | -1337.6 | -2497.3 | -64.6 | 14.8 | 14.8 | 26.7 | 25.3 | -24.8 | 77.2 |
| ALL | all | 2 | 0.7 | 1 | 120 | 0.0 | 4592.8 | 935.8 | -1334.1 | -2523.4 | -91.5 | 14.8 | 14.8 | 26.3 | 23.4 | -24.6 | 77.6 |
| P7 | all | 1 | 0.7 | 3 | 0 | 0.3 | 4952.6 | 2565.9 | -1198.9 | -39.2 | 62.8 | 13.4 | 13.4 | -9.1 | 10.0 | -5.6 | 10.4 |
| P7 | asia | 1 | 0.7 | 1 | 0 | 0.3 | 4758.4 | 2892.9 | -1107.7 | 198.2 | 519.2 | 13.4 | 13.4 | -9.1 | 13.3 | -1.2 | 6.8 |
| P7 | all | 1 | 0.7 | 1 | 0 | 0.3 | 4852.1 | 2822.3 | -1259.0 | -272.9 | 38.9 | 13.4 | 13.4 | -11.5 | 10.1 | -6.6 | 11.1 |

Reading: the M7 NY-AM trails are the only rows that hold in all five windows and they are tiny ($40-150/wk, DD cut ~0). The big recent numbers (ALL scope Donchian-900 from 70%: +4344/wk L3M, +1037 L6M, DD -29%) reverse in HOLD (-1643) and PRE (-3154): the L3M and L6M DD cuts are identical, i.e. one drawdown episode (probably week 2026-W44) sits in both; the W44-removed check of the trails is not run yet and is part of the exact scoring. Exact sets queued: TL3_PA_TR_ALL_D900/G30/E1200, TR_P7_G30, TR_P7ASIA_G30, TR_M7NY_D900, TR_M7NY_L90_30 (L3M first).

## 3. Target distance and runner logic, split by the trend-day call (item 3)

What is different from the dead staggered targets (DS3_BUILD_ON / code/th_bo, resting rungs below the target) and from W-TD tgt x1.5 (whole position, call at entry): here the target lots stay at the NORMAL target (engine fill untouched) and only the runner lots (1/3 or 1/2, at least one) ride on with a trail/extended limit, and ONLY when the W-TD K3K4 trend-day call is on with the trade side at the Target fill second (causal). The nearer-on-chop side is W-CH2 (chop_hooks tgt x.67): not repeated. First-order on all Target exits with lots >= 2 (post-fill 1-s mid path up to 2 h, cut at tape gaps), 1512 cells.

Best with-trend rows (call on, positive in L3M/L6M/HOLD/GAP/PRE; X' is the failing window), tolerant gate recent:

| book | sess | dtype | frac | mode | g | f | m | d3 | d6 | dh | dg | dp | dx | cut6 | nf | hit |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7 | all | with | 0.5 | 0 | 40.0 | 0.8 | 0.0 | 1147.1 | 387.4 | 311.1 | 354.9 | 88.8 | -189.0 | 0.0 | 1.9 | 0.2 |
| ALL | all | with | 0.5 | 0 | 40.0 | 0.8 | 0.0 | 1298.3 | 366.7 | 529.2 | 302.1 | 170.4 | -238.6 | 0.0 | 3.6 | 0.2 |
| M7 | all | with | 0.5 | 0 | 40.0 | 0.8 | 0.0 | 181.0 | 81.8 | -46.3 | -28.4 | 36.0 | -35.9 | 0.0 | 0.5 | 0.2 |
| K7 | all | with | 0.5 | 0 | 10.0 | 0.8 | 0.0 | -5.0 | 17.5 | 12.0 | -75.9 | -36.1 | -3.2 | 0.0 | 1.1 | 0.3 |
| H7 | all | with | 0.5 | 1 | 0.0 | 1.0 | 2.0 | 0.0 | -4.0 | -4.1 | -8.7 | -2.9 | -0.7 | 0.0 | 0.0 | 0.0 |
| U7 | all | with | 0.3 | 1 | 0.0 | 0.8 | 2.0 | 0.0 | -12.1 | 34.8 | 46.8 | -8.8 | -9.1 | 0.0 | 0.0 | 0.0 |

Without the call (dtype any / notwith) every runner cell loses in all windows (hit rate of a continuation 20-40%): best "any" rows are ALL -1481/wk L6M. So the runner is a trend-day-only tool. Cells positive in ALL six windows: 0 (X' is negative for P7/ALL). Exact sets queued: TL3_PA_RUN_P7_W, TL3_PA_RUN_ALL_W (bank lots-r at the engine Target fill, r = half the lots, trail 40 pts from the running max, floor 0.8 T, 2 h cap; exit name PaRun).

## 2. Trend sizer (efficiency) and adding to a winner (item 2)

Efficiency-ratio sizer at the signal minute (live: 20 x 5-min bars, thr .30, x0.5 below): lookbacks 5-240 min, bar sizes 1/5/15 min, thr .2-.6, lots x(1/1.5/2) with the move, x(1/.5/0) against, x(1/.5/0) in chop, per book and session; equal-mean scaling (global factor so the L6M mean equals the base), 29900 cells, LEAD (DD cut > 0 in all five windows, mean-eq within 150) 710. Time-shift placebo (features from the same minute 11/23/37 days earlier) on the 80 best leads:

| book | sess | N | bar | thr | mh | ml | mc | real_L6M | real_HOLD | real_PRE | x44_L6M | pl11_L6M | pl23_L6M | pl37_L6M | pl11_HOLD | pl23_HOLD | pl37_HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7 | asia | 120 | 15 | 0.6 | 2.0 | 0.0 | 1.0 | 9.3 | 29.6 | 18.3 | 9.3 | -5.8 | 18.2 | -7.9 | -10.3 | 7.1 | 20.1 |
| P7 | asia | 120 | 15 | 0.6 | 2.0 | 0.5 | 1.0 | 8.7 | 27.3 | 17.8 | 8.8 | -6.1 | 12.5 | 11.4 | -8.4 | 13.5 | 15.0 |
| P7 | asia | 120 | 15 | 0.6 | 2.0 | 1.0 | 1.0 | 8.1 | 23.8 | 17.3 | 8.3 | -6.5 | 7.1 | 14.6 | -6.6 | 19.5 | 8.2 |
| P7 | asia | 120 | 15 | 0.2 | 2.0 | 1.0 | 0.0 | 14.4 | 16.1 | 8.9 | 0.3 | 8.4 | 0.5 | 6.4 | -15.1 | 10.7 | 17.6 |
| K7 | asia | 240 | 15 | 0.4 | 2.0 | 1.0 | 0.0 | 17.3 | 11.2 | 6.8 | 8.3 | -10.0 | -6.8 | 18.3 | 0.3 | -6.6 | 2.3 |
| K7 | asia | 240 | 15 | 0.4 | 2.0 | 0.5 | 0.0 | 19.0 | 10.9 | 6.4 | 9.6 | -7.3 | -7.0 | 12.2 | -0.7 | -6.1 | 3.8 |
| K7 | asia | 240 | 15 | 0.4 | 2.0 | 0.0 | 0.0 | 20.7 | 10.6 | 6.0 | 10.9 | -4.5 | -7.3 | 3.9 | -1.6 | -5.5 | 5.4 |
| P7 | asia | 120 | 15 | 0.2 | 2.0 | 0.5 | 0.0 | 14.1 | 16.7 | 12.3 | -3.2 | -15.1 | -22.7 | -2.5 | -22.1 | 8.0 | 22.0 |
| P7 | asia | 120 | 15 | 0.6 | 1.5 | 0.0 | 1.0 | 5.8 | 20.9 | 10.8 | 13.1 | -2.5 | 15.0 | 2.0 | -7.0 | -3.3 | 17.5 |
| K7 | asia | 240 | 15 | 0.4 | 2.0 | 1.0 | 0.5 | 11.8 | 7.0 | 5.3 | 7.4 | -7.7 | -6.8 | 9.0 | -1.4 | -5.6 | 1.3 |

Reading: the P7 Asia 120m/15-min thr .6 row cuts equal-mean DD 9/30/18%% (L6M/HOLD/PRE) but the placebos reach +18%%, +20%% in single shifts, so it is inside the placebo band; K7 Asia 240m/15 (17/11/7%%) beats two of three placebos only. Not promoted; exact sets TL3_PA_ER_P7ASIA_120_15_6/_2, TL3_PA_ER_K7ASIA_240_15_4 are queued so the engine (with lot rounding and the live sizer underneath) decides.

**Pyramiding (add on the first pullback after +a pts, stop kept; base stops and target unchanged)**. Grid a 10-50, pullback q 3-20, add 0.25/0.5/1.0 x lots, 126 cells x 28 scopes x 7 windows, equal-mean DD cut, W44-removed, call split, random-time placebo (add at a uniform random second after the trade reached +a, 100 draws). AUTO-EXPANSION of the parent (P7 Asia a=15 q=12 f=0.5): other books/sessions, finer grid, call split, W44, placebo all run:

| book | sess | dtype | a | q | f | cuteq_L3M | cuteq_L6M | cuteq_HOLD | cuteq_GAP | cuteq_PRE | cuteq_X' | x44_L6M | dmean_L6M | dmean_HOLD | dmean_PRE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7 | asia | any | 15 | 12 | 0.5 | 8.2 | 8.2 | 11.5 | 1.6 | 2.3 | 20.4 | 12.0 | 4398.7 | 1969.4 | 1161.7 |

Call split of the parent: nocall (the call is off at 95%% of entries) 7.7/7.7/14.5/1.1/1.7/20.9, with 0.6, notwith 0.1: the call carries no information for the add. Random-time placebo (same eligibility +15, same lots, uniform time): the parent's L6M/HOLD/PRE equal-mean cuts sit at placebo percentiles p = 0.25 / 0.18 / 0.50 (P7 asia): the DD cut is the effect of adding size to trades that have reached +15, NOT of waiting for a pullback. Other books and sessions: best min-window cut below 1%% (U7 Asia, O7 NY-AM), nothing. Day-type, context and fresh/rechase splits of the add wait for the exact trade logs.

Exact sets queued: TL3_PA_ADD_P7ASIA_15_12_5 (parent), _15_8_5, _20_12_5, ADD_P7_15_12_5 (all P7 sessions); the hook re-uses the engine add (l2_add_stage), restores the original target and stop, and logs adds. Caveat: the engine state cut and the P7 day cap act on the added lots.

## 5. Session books and sub-sessions (item 5)

Observed live-session trades only (a book trades only in sessions with lots > 0), $/wk per window, base lots, by entry clock (ET). Rows positive in all five of L3M, L6M, HOLD, PRE, X' are registered as session-book candidates; rows negative in the four recent windows are loss-side candidates for W-LA/W-EB.

| book | sub | n | L3M | L6M | HOLD | GAP | PRE | X' | pos_wk_pct |
|---|---|---|---|---|---|---|---|---|---|
| A7 | asia_open | 226 | 399 | 3 | 333 | -49 | 222 | 144 | 59 |
| A7 | asia_late | 251 | 856 | 1030 | 235 | -288 | 386 | 45 | 67 |
| H7 | ny_first_hr | 124 | 61 | 19 | 266 | -7 | 121 | 38 | 57 |
| K7 | asia_late | 382 | 629 | 250 | 576 | 416 | 215 | 120 | 54 |
| M7 | london_open | 870 | 459 | 558 | 487 | -240 | 424 | 400 | 58 |
| M7 | ny_am_rest | 879 | 299 | 744 | 25 | 344 | 417 | 164 | 56 |
| P7 | asia_late | 291 | 3416 | 5882 | 1241 | -633 | 966 | 601 | 55 |
| U7 | asia_open | 103 | 404 | 449 | 88 | -94 | 363 | 438 | 58 |

Sub-sessions that lose in at least 3 of L3M/L6M/HOLD/PRE (sent to the loss side):

| book | sub | n | L3M | L6M | HOLD | GAP | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| K7 | ny_am_rest | 993 | -295 | -36 | -639 | -454 | 90 | 143 |
| K7 | ny_pm_rest | 700 | -229 | 233 | -149 | 879 | -202 | 205 |
| M7 | london_rest | 1619 | -884 | -1151 | -553 | -258 | -377 | -46 |
| P7 | ny_first_hr | 327 | 201 | -23 | -345 | 522 | -688 | -327 |

The OFF sessions (22 book x session cells: K7 pre/close, U7 pre/nyam/nypm/close, P7 pre/nypm/close, H7 london/pre/nypm/close, M7 asia/pre/nypm/close, A7 london/pre/nyam/nypm/close) cannot be read from the live trades: they are queued as exact sets TL3_PA_SB_<book>_<session> (the book on in that one session, 1 lot, P7 2, everything else live), identity TL3_PA_SB_ID (the live session strings reproduce JN05W2). Results: see the exact table.

## 6. Exact engine status and results

Done set-months: none yet (queue 158 lines, PA waiting on admission: MemAvail ~48 GB, 50 workers, load 70 on 32 cores, quota PA = 1 in PRIORITY.txt although the brief says 2).

## 4. Press rules (item 4)

First-order (equal-mean DD cut, W44-removed beside, base lots), 1932 cells: (a) TWO BOOKS AGREE: another book entered the same side within N = 5/15/30/60 min before the signal, lots x1.25/1.5/2 (x1/.5/0 when the nearest other-book entry was opposite); (b) STRONG SESSION START: NQ move from the session open >= k = 20/30/50/80 pts with the trade (at least 20/40 min into the session), lots x1.5/2, x1/.5/0 against. Stack-level (ALL) presses all have NEGATIVE equal-mean DD cuts in L3M/L6M/HOLD/PRE (agree: -4 to -9%; start: -0.3 to -4% with a +21% X' only), i.e. pressing the whole stack is no better than the plain size line. Single book-session survivors (min over L3M/L6M/HOLD/PRE/X' > 3%: 10 cells of 1932):

| kind | book | sess | N | k | mh | ml | cuteq_L3M | cuteq_L6M | cuteq_HOLD | cuteq_PRE | cuteq_X' | cuteq44_L6M | dmean_L6M | dmean_HOLD | dmean_PRE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| agree | U7 | asia | 60 | 0 | 2.0 | 0.0 | 5.4 | 5.4 | 7.4 | 10.9 | 10.8 | 13.1 | 1672.3 | 121.2 | 443.5 |
| agree | U7 | asia | 60 | 0 | 2.0 | 0.5 | 5.1 | 5.1 | 7.1 | 10.6 | 8.1 | 10.2 | 1580.1 | 172.0 | 533.4 |
| agree | U7 | asia | 60 | 0 | 2.0 | 1.0 | 4.7 | 4.7 | 6.7 | 10.3 | 5.4 | 7.3 | 1487.9 | 222.8 | 623.4 |
| start | U7 | asia | 20 | 80 | 2.0 | 0.0 | 10.0 | 10.0 | 8.0 | 4.2 | 4.2 | 3.5 | 1159.5 | 90.7 | 423.0 |
| start | U7 | asia | 40 | 80 | 2.0 | 0.0 | 9.7 | 9.7 | 7.7 | 3.9 | 3.9 | 3.2 | 1063.6 | 1.9 | 423.0 |
| start | U7 | asia | 20 | 80 | 1.5 | 0.0 | 10.6 | 10.6 | 5.2 | 3.3 | 3.3 | -1.2 | 885.0 | -155.8 | 183.7 |
| agree | H7 | asia | 60 | 0 | 1.2 | 0.0 | 5.5 | 5.5 | 4.0 | 3.3 | 3.2 | 4.9 | 506.2 | 395.3 | 134.0 |
| start | U7 | asia | 20 | 80 | 2.0 | 0.5 | 4.6 | 4.6 | 6.9 | 3.2 | 3.2 | 2.9 | 854.2 | 291.9 | 450.9 |

Reading: only U7 (4-lot Asia/London book) and H7 Asia carry it, with +0.5 to +1.7k/wk of base-lot mean; with 1,932 cells searched the best are within what chance yields (no placebo run yet: PRESS needs a time-shift placebo of the agree flag and the session open; queued with the exact sets). The QQQ gamma press parent (DS3_UWREGIME.md section "size x1.5 (press) / x0.5 (half) / skip, best gated cell per book") is the UW-dependent variant and stays W-UW's; its gate re-run on today's windows is the next job here once the UW day file is accessible. Exact sets queued: TL3_PA_PRESS_U7ASIA_AGR60, _U7ASIA_ST80, _H7ASIA_AGR60 (hook: press agree/start inside trend_size).

## 6. Bracket scaling
Belongs to W-D9/W-D10; cross-check only when their results land (DS3_DIAL10.md: 0 of 35 cells scored through L3M at last look).
