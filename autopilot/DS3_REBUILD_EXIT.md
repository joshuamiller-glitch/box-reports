# DS3_REBUILD_EXIT - T-REBUILD addendum 3: EXIT CONFLUENCE (W-RX). Parts A, B, C1, C2 built; C3 / D / E: see section 4. Updated 2026-11-17 07:21Z
> VALIDATION (W-RX, FIRST PASS, 2026-11-16): trials counted = C1 about 6,200 cell-conditions per source (190 conditions x 36 cells x pooled view; per-checkpoint views are descriptive) x 2 sources, C2 264-282 cells per source, C3 72 variants x 7 books x 2 sources + 9 give-back comparators (TRIALS_LEDGER.csv REX1 REX2 REX3); correction = nonsense bar (99th percentile of |t| of 33 controls per cell: 3 shifted 11/23/37 trading days + 30 persistent-draw random flags, realised share within 0.05) + Benjamini-Hochberg 10% per cell for C1, percentile among 33 controls for C2, White RC / Hansen SPA + deflated Sharpe + BH + CSCV PBO (12/14/16 blocks, 1-week purge) for C3; PBO is computed on the 72-variant weekly-difference matrix; C1 / C2 are in-sample descriptive tests (nothing fitted), C3 scores are WALK-FORWARD (trailing 26 weeks -> next 2) and every number is out of sample from 2023-10, nothing untouched yet (the HOLD path is inside the walk-forward span but was never used to choose anything). Prereg: REXIT_PREREG.md, REXIT_C3_PREREG.md (sha lines in DECISIONS.md, one correction and one deviation logged there).

VERDICT (data ends 2026-10-30; FIRST PASS; exact-engine D run on the 8 best-by-DD / best-by-mean schedules, controls still landing, see section 4.8): while a trade is open, no re-read condition and no count of conditions against the trade tells the desk to get out, and no walk-forward exit score does either. (1) The average remaining result is +0.03 to +0.06 R in every state we can build, including 4 or more of 16 independent clusters against (+0.03 R); it is negative only at 9+ clusters against (-0.03 R, SE 0.02). The count is not a staircase in the frozen 0..4+ bins (JL2 raw slope t -2.0, adjusted for open profit / give-back / time in trade t -1.2, percentile among nonsense counts 73; raw base t -0.8 / -0.2); the only cells with an adjusted t <= -2 are P7 Asia and U7 (P7 Asia: +0.12 R at 0 clusters against falling to +0.03 R at 4+, on both bases), still never negative: the reading says tighten, not exit. (2) C1, about 6,100-6,200 cell-conditions per source: the frozen survivor rule keeps 6 on JL2 (P7 15-minute trend against, H7 RTY flip) and 0 on the raw base; three shuffled-outcome nulls keep 3 / 15 / 4 (JL2) and 2 / 4 / 0 (raw): the real counts sit inside the null range. Leads only: 15-minute trend / VWAP / day vote against (lift -0.03 to -0.06 R pooled, -0.1 to -0.2 R in P7 / U7 / H7 cells; HOLD sign flips for P7), M7 adverse-aggressor tape ratio at 5 s (-0.05 to -0.13 R at every checkpoint on raw, t -3.1, JL2 -0.1 t -2.1). (3) C3: the walk-forward exit score has an out-of-sample rank IC of -0.05 to +0.02 (ridge), -0.03 to +0.10 (boosted; only A7 reaches t 2.3-2.9), path-only baseline negative, null runs -0.01 +- 0.02: no information. Best of 72 actions per book (path arithmetic, $1.2 pt slip): +$0 to +$245/week on JL2 (U7 X in loss at -0.2 R, t 1.9) and +$17 to +$377/week on the raw base, against stack-book means of $0.6k-3.9k/week; White RC p 0.53-0.98 and SPA p 0.19-0.94 over the 72, DSR 0.00-0.31, BH discoveries 0 in all 12 book x source families, PBO above 0.5 for P7 and A7 on JL2 and K7 on raw. The simple give-back rule on the same trades is negative in $ on 11 of 12 book x source cells (U7 raw +$147; others -$147 to -$3,677/week). Max drawdown: the best-of-72 DD cut is 19-40% of the unchanged out-of-sample max DD for JL2 M7 / U7 / H7 / A7 and 12-40% for raw M7 / U7 / H7 / A7, above the 3 permutation nulls in several (JL2 U7 40% vs 0-28%, raw M7 40% vs 1-11%) but at a mean of -$510 / -$146 to +$166 per week and with random-exit controls (matched share, minutes and open profit) mostly worse than the real variants only because every random exit pays the slip; the DD cuts are LEADS, not results (3 nulls per book cannot support a percentile). The planted-edge check recovers a +0.15 R in-trade signal in 7 of 8 cells (all but O7, 417 trades; O7 has no walk-forward window with enough rows and is not scored in C3), so the nulls are not a power failure for effects of that size. Exits are priced at 1.2 pt (0.02 R); nothing found pays for itself as a full exit. D (exact engine, JL2 stack, 43 months, hook rx_hooks): the DD leads do NOT survive. U7 best-by-DD: L6M stack max DD -$33.9k vs -$22.6k, ulcer 20% worse, mean -$1.9k/week (FAIL); A7 best-by-DD: L6M ulcer 5.6% worse, mean -$0.4k/week (FAIL); M7 best-by-DD: ulcer 1.4% better in L6M / 2.4% in HOLD, mean +$0.2k / -$0.1k per week, bootstrap P(ulcer lower) 0.89 / 0.54 (LEAD at most, controls pending); H7 best-by-DD: no effect (94 / 414 $ per week). Best-by-mean: A7 +$770/week in L6M (+3.5%), nothing in HOLD (no actions), U7 +$315 / +$205, M7 -$88, H7 -$25 / +$279. White RC over the 8 cells p 0.35 (L6M), 0.22 (HOLD); DSR (N=288) 0.006 (L6M). Verdict: no DD lead is confirmed on the engine; at best two small LEADS (M7 best-by-DD DD/ulcer, A7 best-by-mean mean), tier scoring against >= 30 engine random-exit draws still landing. Stage 2 / stage 3 joint step not run (do not exist on this box).
## 1. Parts A and B: the in-trade state table and the remaining-R label (built)
**What exists.** Two tables built from the same code (code/th_rexit: build_grid.py, add_z.py, features.py, build_rows.py, run_all.py): (1) SOURCE raw = every trade of the T-REBUILD stage-0 raw base (one book alone, no layers, hold to bracket), the 7 live books K7 M7 U7 P7 H7 A7 O7, built from /mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/TL3_RB_S0_<BOOK> for the months that had landed at 20:30Z on 16 Nov (listed in the first table; the shadow books X3-X5 not built yet); (2) SOURCE jl2 = TL3_EV_JN05W2JL2, all 43 months (2023-04..2026-10), all 7 live books. Files: /mnt/l2/l2vast/_rexit/rows/<source>/<BOOK>_<YYYYMM>.parquet (one row per closed minute in trade, decision times T_j = (floor(entry/60)+1+j)*60 so the first decision is 60-120 s after the entry, cap 480 minutes in trade, about 2.4 million rows JL2 and 2.6 million raw), E_<BOOK>_<YYYYMM>.parquet (one row per trade with the ENTRY readings e_*, the exit and the path pointer) and U_<BOOK>_<YYYYMM>.npy (the 1-second path u = side x (mid - entry) from entry to the real exit, pointer p_off / p_len). The grid of per-minute readings is /mnt/l2/l2vast/_rexit/grid1m.parquet (1.94 million minutes, 187 columns).

**A. State, once per closed minute; no look-ahead.** Price at T = last 1-s mid at or before T-1; every reading comes from the last COMPLETE minute (row m = T-60). (A1) trade path: open profit in points and R, best, worst, give-back from best (points), minutes in trade, minutes since the best, distance to the stop and to the target (stop 60 / target 60 for K7 M7 U7 P7 H7 A7, O7 40 / 90; the per-trade bracket of JL2 is not in the trade file, so the distance to the target on JL2 is for the default bracket: approximate), nearest session / overnight / prior-day / VWAP-band level ahead and behind and the number within 20 pt (same function as the entry-time room feature, bd_room). (A2) the entry readings RE-READ now, signed with the trade (negative = against): day-direction vote and its four members (session open, 18:00 open, session VWAP, 60-minute slope; d10_core.day_dir at T), NQ trend / momentum / MACD / squeeze / VWAP states on 1, 5 and 15-minute bars (B5 columns of the W-CF2 minute grid: EMA stack, hold of the 21, supertrend, ADX/DI, RSI, CCI, MACD sign and rising, squeeze fired direction, squeeze momentum, squeeze on, VWAP side), atr_rel (live definition), range used versus the HAR forecast (and the room left in points). (A3) flow, per minute from the W-CF2 per-second tables: aggressor delta (1, 5, 15 min) and big-print net against the trade, own-side support pulled / added (5-minute sums, robust z against the previous 20 days), wall ahead versus own wall within 10 ticks, tape speed (z of the 5-minute print rate) and acceleration, L2 imbalance and microprice, L3 arrival imbalance (counts and sizes, 1/2/5 min) and own-side cancel-to-trade ratio. (A4) other markets: ES / RTY / YM / NQ 1, 5 and 15-minute moves (z of the move), NQ-lead-over-ES/RTY, ZN / 6E z at 5-60 min, NKD return 5-60 min, all signed with the trade; the T-ALPHA walk-forward core forecast at 5 / 15 / 60 min now (sign and strength, signed with the trade). 1-minute moves for ZN / NKD are NOT available (their columns are 5-minute and longer): marked not available. (A5) what changed since entry: for every item the flag 'was with or neutral at entry, against now' (flip), and the cluster-level version; the count of flips and the count of clusters against are the confluence counts of C2. The 5-second table for the flow items (W-CF2 tape_intrade rebuilt on these trades: adverse / favourable aggressor trades and contracts over 5 and 15 s, acceleration of the adverse side, message-rate acceleration) is built for the first 60 minutes in trade at /mnt/l2/l2vast/_rexit/tape5s_<source>_TAPE_INTRADE.parquet and scored in section 2.4 when it lands.

**B. Label.** rem_pts = side x (real exit price - price at T); rem_R = rem_pts / stop (clipped +-3 in the tests); exit_better = rem < 0; exit_better_slip = rem < -1.2 pt. Exiting now would have been better in the share of rows shown below (it is the base rate of a coin that has to beat the 1.2 pt cost, not a signal).

**JL2: rows per book, months present, share of rows where exiting now beat the real exit** (rows = closed minutes in trade, cap 480 min; exit_better = remaining result < 0; slip = < -1.2 pt)

| book | trades | rows | mean_mins | exit_better_pct | exit_better_slip_pct | mean_rem_R | n_months | first | last | missing_months |
|--|--|--|--|--|--|--|--|--|--|--|
| A7 | 1151 | 243404 | 185 | 45.3 | 45.2 | 0.079 | 43 | 202304 | 202610 |  |
| H7 | 1033 | 204974 | 183 | 48.7 | 48.6 | 0.061 | 43 | 202304 | 202610 |  |
| K7 | 7147 | 765542 | 136 | 51.2 | 50.9 | 0.038 | 43 | 202304 | 202610 |  |
| M7 | 3872 | 362123 | 117 | 51.8 | 51.5 | 0.029 | 43 | 202304 | 202610 |  |
| O7 | 417 | 17100 | 91 | 50.7 | 50.4 | 0.088 | 43 | 202304 | 202610 |  |
| P7 | 3690 | 536908 | 155 | 52.6 | 52.4 | 0.034 | 43 | 202304 | 202610 |  |
| U7 | 1308 | 259355 | 170 | 48.5 | 48.4 | 0.037 | 43 | 202304 | 202610 |  |

By state: loss: 1,062,472 rows, exiting now better in 65.6% (65.3% after the 1.2 pt slip), mean remaining R +0.041; profit: 1,326,934 rows, exiting now better in 38.4% (38.3% after the 1.2 pt slip), mean remaining R +0.043

**RAW: rows per book, months present, share of rows where exiting now beat the real exit** (rows = closed minutes in trade, cap 480 min; exit_better = remaining result < 0; slip = < -1.2 pt)

| book | trades | rows | mean_mins | exit_better_pct | exit_better_slip_pct | mean_rem_R | n_months | first | last | missing_months |
|--|--|--|--|--|--|--|--|--|--|--|
| A7 | 1046 | 239295 | 188 | 44.9 | 44.9 | 0.066 | 41 | 202304 | 202610 | 202607,202609 |
| H7 | 1050 | 217340 | 185 | 48.1 | 48.0 | 0.048 | 42 | 202304 | 202610 | 202607 |
| K7 | 6675 | 796075 | 143 | 47.6 | 47.3 | 0.042 | 41 | 202304 | 202610 | 202607,202609 |
| M7 | 3533 | 421208 | 131 | 49.8 | 49.6 | 0.008 | 41 | 202304 | 202610 | 202607,202609 |
| O7 | 439 | 20780 | 97 | 49.4 | 49.2 | 0.096 | 40 | 202304 | 202610 | 202606,202608,202609 |
| P7 | 5135 | 687909 | 154 | 48.4 | 48.3 | 0.023 | 41 | 202304 | 202610 | 202608,202609 |
| U7 | 1232 | 257292 | 172 | 47.1 | 47.1 | 0.043 | 40 | 202304 | 202610 | 202309,202606,202607 |

By state: loss: 1,299,911 rows, exiting now better in 62.1% (61.9% after the 1.2 pt slip), mean remaining R +0.033; profit: 1,339,988 rows, exiting now better in 34.1% (34.0% after the 1.2 pt slip), mean remaining R +0.036

**Feature-family availability (share of checkpoint rows with every member present, JL2 / raw; same by construction)**

| cluster | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|
| K_TREND | 1.00 | 1.00 | 1.00 | 1.00 |
| K_TREND15 | 1.00 | 1.00 | 1.00 | 1.00 |
| K_OSC | 1.00 | 1.00 | 1.00 | 1.00 |
| K_MACD | 1.00 | 1.00 | 1.00 | 1.00 |
| K_SQZ | 1.00 | 1.00 | 1.00 | 1.00 |
| K_VWAP | 1.00 | 1.00 | 1.00 | 1.00 |
| K_DAY | 1.00 | 1.00 | 1.00 | 1.00 |
| K_XIND | 1.00 | 1.00 | 1.00 | 1.00 |
| K_XMOVE | 0.98 | 0.97 | 0.98 | 0.98 |
| K_NKD | 0.87 | 0.90 | 0.92 | 0.94 |
| K_ALPHA | 0.99 | 1.00 | 1.00 | 0.99 |
| K_TAPE | 1.00 | 1.00 | 1.00 | 1.00 |
| K_BOOK | 1.00 | 1.00 | 1.00 | 1.00 |
| K_WALL | 1.00 | 1.00 | 1.00 | 1.00 |
| K_L3 | 0.99 | 1.00 | 1.00 | 1.00 |
| K_RANGE | 0.27 | 1.00 | 1.00 | 1.00 |
| K_PATH | 1.00 | 1.00 | 1.00 | 1.00 |

Single readings:

| reading | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|
| atr_rel | 1.00 | 1.00 | 1.00 | 1.00 |
| rng_used | 0.27 | 1.00 | 1.00 | 1.00 |
| lvl_ahead | 1.00 | 1.00 | 1.00 | 1.00 |
| mk_NKD_ret5 | 0.98 | 0.99 | 0.99 | 0.99 |
| mk_ZN_z5 | 0.82 | 0.81 | 0.79 | 0.85 |
| mk_6E_z5 | 0.42 | 0.42 | 0.43 | 0.42 |
| mv_NQ_z1 | 0.98 | 0.98 | 0.98 | 0.98 |
| tape_speed5 | 1.00 | 1.00 | 1.00 | 1.00 |
| l2_imb5 | 1.00 | 1.00 | 1.00 | 1.00 |
| l3_n5_1m | 0.99 | 1.00 | 1.00 | 1.00 |
| alpha_avg_5 | 0.99 | 1.00 | 1.00 | 0.99 |

Not available / partly available (never filled): megacap and breadth items (B14) exist only from 2024-10 and the CBOE / macro day context (B15) and options (J) are day-level, so none of them is in the in-trade table; 6E 5-minute z exists in 42% of minutes (6E session), 6J only from 2026-05 (not used); ZN 5-minute z in about 80% of minutes (bond hours); range used versus forecast (HAR) exists from late 2023 (27% of 2023 rows); L3 (MBO) starts 2023-04-02 and the T-ALPHA forecast has a test span of 2023-04-03..2026-10-30; nothing exists for these items before. The 5-s flow items need L3 messages for the message-rate acceleration (flagged: D7's live feed has no L3). UW / dealer-direction items are not part of this page (closed by order 11-13).

## 2. Part C1: single in-trade conditions vs remaining R
Method (frozen in REXIT_PREREG.md). Condition = a reading re-read in trade, in the AGAINST state (signed value below -0.5: items already in {-1,0,1} unchanged, continuous items are robust z against the previous 20 days), the 'flipped since entry' version, the 16 cluster votes (cluster against = mean of its members' votes <= -0.5, flipped version) and the trade-path items (marked PATH, mechanical: near the stop, give-back, never green). 205-210 conditions per cell after dropping those with < 15 rows in a group. Outcome rem_R at the checkpoints 5/15/30/60/120 minutes in trade, one row per trade-checkpoint, cells = book x session (60+ rows), book, ALL. Lift = mean rem_R when the condition is on minus off; t = week-clustered (calendar weeks of the trade entry). A useful exit reading has a NEGATIVE lift. Controls beside every condition: the flag taken from the trade 11 / 23 / 37 trading days earlier in the same book x session x checkpoint and 30 persistent-draw random flags (hash of seed, trade, 5-minute bucket) with the same share; realised share vs real share printed in the parquet (sh_share_diff), more than 0.05 apart = invalid and redrawn (n_redraw). pct_useful = share of controls with a LESS useful (higher) lift than the real; pct_abs = share of controls with a smaller |t| than the real (use this one: random flags carry no week-level co-movement, so the lift percentile flatters real flags that are regime-persistent; the survivor rule uses both). Windows: all months, L6M (2026-05-01..2026-10-30), HOLD (2025-11-17..2025-12-10), W44-removed; per-checkpoint lifts in the parquet. Data: /mnt/l2/l2vast/_rexit/res/c1_<source>.parquet (every cell-condition with all columns).

**Real vs the same pipeline on shuffled outcomes (null)**

| source | run | tests | abs_t_ge_bar | neg_t_le_minus_bar | pct_ge95_lift | pct_abs_ge95 | BH10 | survivors | survivors_w44rm |
|--|--|--|--|--|--|--|--|--|--|
| jl2 | REAL | 6143 | 107 | 90 | 795 | 458 | 18 | 6 | 6 |
| jl2 | null y-shuffle 1 | 6143 | 45 | 24 | 330 | 262 | 15 | 3 | 3 |
| jl2 | null y-shuffle 2 | 6143 | 168 | 133 | 618 | 569 | 74 | 15 | 15 |
| jl2 | null y-shuffle 3 | 6143 | 142 | 78 | 428 | 491 | 17 | 4 | 4 |
| raw | REAL | 6205 | 124 | 81 | 877 | 511 | 16 | 0 | 0 |
| raw | null y-shuffle 1 | 6205 | 110 | 35 | 239 | 424 | 14 | 2 | 2 |
| raw | null y-shuffle 2 | 6205 | 81 | 40 | 307 | 360 | 7 | 4 | 4 |
| raw | null y-shuffle 3 | 6205 | 51 | 24 | 330 | 385 | 2 | 0 | 0 |

Reading the table: 'tests' are the cell-conditions that had enough rows; 'abs_t_ge_bar' counts tests whose |t| reached the 99th percentile of the 33 controls of their own cell (about 1% expected per independent test; the conditions are highly correlated so null runs swing from 45 to 168). The null runs are the same pipeline with rem_R permuted inside book x session x checkpoint (seeds 1..n). The real JL2 counts (107 bar-passing, 6 survivors) sit inside the null range (45-168, 3-15); the raw base real counts (117, 0) sit inside its null range as well. That is the verdict on C1 at the level of the whole table: the conditions as a family do not separate from nonsense. Individual cells (below) are leads.

**Survivors of the frozen rule (lift < 0, |t| >= nonsense bar, percentile >= 95 among the 33 controls, BH q <= 0.10 in the cell, L6M negative, >= 3 of 4 years negative)**

| source | cell_book | cell_sess | cond | share | lift_all | t_all | pct_useful | pct_abs | bar99 | bh_q | lift_L6M | lift_HOLD | lift_w44rm | yr_lifts |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| jl2 | H7 | ALL | flip_mk_RTY_z15 | 0.098 | -0.177 | -3.287 | 100.000 | 100.000 | 2.376 | 0.074 | -0.064 | -0.208 | -0.181 | -0.220;-0.080;-0.191;-0.206 |
| jl2 | H7 | ALL | flip_mv_RTY_z15 | 0.115 | -0.172 | -3.272 | 100.000 | 100.000 | 2.376 | 0.074 | -0.130 | -0.217 | -0.175 | -0.299;0.009;-0.177;-0.248 |
| jl2 | P7 | ALL | ag_nq_15m_ema_stack | 0.198 | -0.125 | -3.873 | 100.000 | 100.000 | 2.851 | 0.015 | -0.185 | 0.086 | -0.125 | -0.185;-0.124;-0.123;-0.108 |
| jl2 | P7 | ALL | ag_nq_15m_adx_di | 0.138 | -0.137 | -3.754 | 100.000 | 100.000 | 2.851 | 0.016 | -0.138 | 0.285 | -0.135 | -0.181;-0.183;-0.144;-0.073 |
| jl2 | P7 | ALL | ag_nq_15m_rsi | 0.183 | -0.107 | -3.287 | 100.000 | 100.000 | 2.851 | 0.069 | -0.162 | 0.110 | -0.106 | -0.112;-0.136;-0.107;-0.080 |
| jl2 | P7 | ALL | clu_K_TREND15 | 0.165 | -0.137 | -4.051 | 100.000 | 100.000 | 2.851 | 0.014 | -0.183 | 0.153 | -0.137 | -0.168;-0.162;-0.128;-0.117 |

**Best 12 conditions in the pooled ALL cell per source (by week-clustered t; negative lift = the reading against the trade lowers the remaining R)**

JL2

| cond | family | share | n1_all | lift_all | t_all | pct_abs | bar99 | bh_q | lift_L6M | lift_HOLD | lift_w44rm | yr_lifts |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| flip_mk_NQ_z15 | OTHER | 0.124 | 7373 | -0.034 | -3.205 | 100.000 | 2.734 | 0.187 | -0.006 | -0.049 | -0.035 | -0.049;-0.046;-0.021;-0.022 |
| pth_dist_tgt_lt15 | PATH | 0.015 | 935 | -0.056 | -3.158 | 100.000 | 2.734 | 0.187 | -0.094 | 0.092 | -0.057 | 0.013;-0.040;-0.067;-0.081 |
| flip_mv_NQ_z15 | OTHER | 0.130 | 7549 | -0.033 | -3.076 | 100.000 | 2.734 | 0.187 | 0.002 | -0.036 | -0.034 | -0.057;-0.045;-0.014;-0.022 |
| pth_open_lt_m0.5R | PATH | 0.031 | 1899 | -0.048 | -2.982 | 93.939 | 2.734 | 0.187 | -0.029 | -0.045 | -0.048 | -0.090;-0.040;-0.044;-0.032 |
| clu_K_TREND15 | K_TREND15 | 0.188 | 11492 | -0.061 | -2.936 | 100.000 | 2.734 | 0.187 | -0.142 | 0.239 | -0.060 | -0.063;-0.059;-0.040;-0.085 |
| ag_nq_5m_rsi | K_OSC | 0.145 | 8907 | -0.038 | -2.809 | 100.000 | 2.734 | 0.219 | -0.060 | 0.042 | -0.038 | -0.002;-0.070;-0.038;-0.026 |
| ag_nq_15m_rsi | OTHER | 0.192 | 11730 | -0.053 | -2.772 | 100.000 | 2.734 | 0.219 | -0.136 | 0.150 | -0.051 | -0.041;-0.045;-0.053;-0.068 |
| ag_nq_15m_cci | OTHER | 0.166 | 10177 | -0.046 | -2.736 | 100.000 | 2.734 | 0.219 | -0.104 | 0.067 | -0.045 | -0.052;-0.035;-0.052;-0.048 |
| ag_mv_RTY_z5 | K_XMOVE | 0.266 | 16090 | -0.022 | -2.631 | 96.667 | 2.734 | 0.240 | -0.011 | -0.063 | -0.023 | -0.044;0.010;-0.036;-0.023 |
| flip_dd_vwap | K_VWAP | 0.111 | 6801 | -0.042 | -2.631 | 100.000 | 2.734 | 0.240 | -0.056 | 0.014 | -0.043 | -0.000;-0.029;-0.073;-0.059 |
| ag_nq_15m_adx_di | K_TREND15 | 0.167 | 10217 | -0.054 | -2.553 | 96.970 | 2.734 | 0.271 | -0.116 | 0.192 | -0.052 | -0.025;-0.072;-0.039;-0.071 |
| ag_mk_NQ_z15 | OTHER | 0.187 | 11428 | -0.021 | -2.415 | 93.333 | 2.734 | 0.271 | 0.015 | -0.060 | -0.021 | -0.032;-0.028;-0.024;0.003 |

RAW

| cond | family | share | n1_all | lift_all | t_all | pct_abs | bar99 | bh_q | lift_L6M | lift_HOLD | lift_w44rm | yr_lifts |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ag_l2_own_net5 | K_BOOK | 0.025 | 1709 | -0.089 | -3.001 | 100.000 | 2.217 | 0.322 | -0.123 | -0.101 | -0.079 | -0.073;0.053;-0.015;-0.118 |
| pth_open_lt_m0.5R | PATH | 0.074 | 5131 | -0.040 | -2.927 | 100.000 | 2.217 | 0.322 | -0.038 | 0.094 | -0.042 | -0.087;-0.071;-0.015;-0.032 |
| pth_dist_stop_lt15 | PATH | 0.017 | 1152 | -0.053 | -2.670 | 100.000 | 2.217 | 0.404 | -0.006 | 0.130 | -0.055 | -0.128;-0.101;-0.024;-0.030 |
| cluflip_K_NKD | K_NKD | 0.150 | 10285 | -0.034 | -2.628 | 100.000 | 2.217 | 0.404 | -0.052 | -0.036 | -0.035 | -0.069;-0.033;-0.020;-0.029 |
| pth_dist_tgt_lt15 | PATH | 0.016 | 1113 | -0.051 | -2.509 | 100.000 | 2.217 | 0.474 | 0.011 | 0.133 | -0.052 | -0.031;-0.042;-0.124;-0.010 |
| ag_nq_15m_adx_di | K_TREND15 | 0.157 | 10827 | -0.060 | -2.468 | 100.000 | 2.217 | 0.474 | -0.109 | 0.185 | -0.058 | -0.055;-0.010;-0.077;-0.091 |
| flip_nq_15m_supertrend | K_TREND15 | 0.002 | 127 | -0.195 | -2.324 | 96.970 | 2.217 | 0.525 |  | -0.786 | -0.196 | 0.147;-0.391;-0.347;na |
| clu_K_NKD | K_NKD | 0.173 | 11966 | -0.028 | -2.318 | 96.875 | 2.217 | 0.525 | -0.042 | -0.014 | -0.030 | -0.060;-0.021;-0.028;-0.017 |
| ag_rty_5m_sqz_fired_dir | OTHER | 0.024 | 1686 | -0.065 | -2.272 | 96.970 | 2.217 | 0.537 | -0.122 | 0.148 | -0.066 | -0.070;-0.033;-0.083;-0.084 |
| clu_K_TREND15 | K_TREND15 | 0.170 | 11729 | -0.052 | -2.111 | 93.939 | 2.217 | 0.537 | -0.110 | 0.254 | -0.051 | -0.095;0.010;-0.044;-0.084 |
| ag_nq_5m_hold21 | K_TREND | 0.084 | 5849 | -0.038 | -2.094 | 100.000 | 2.217 | 0.537 | 0.067 | 0.184 | -0.038 | 0.004;-0.104;-0.044;0.017 |
| ag_mk_NKD_ret60 | K_NKD | 0.305 | 19936 | -0.027 | -2.084 | 96.667 | 2.217 | 0.537 | -0.048 | 0.007 | -0.029 | -0.026;-0.020;-0.034;-0.029 |

**Excess of bar-passing negative lifts by family, real vs mean of the null runs (all cells)**

| source | family | tests | real_neg_t_le_bar | null_mean | excess |
|--|--|--|--|--|--|
| jl2 | K_TREND15 | 163 | 12 | 4.3 | 7.7 |
| jl2 | PATH | 216 | 6 | 3.0 | 3.0 |
| jl2 | K_NKD | 184 | 5 | 2.3 | 2.7 |
| jl2 | K_L3 | 386 | 5 | 3.0 | 2.0 |
| jl2 | BOOK | 45 | 2 | 1.0 | 1.0 |
| jl2 | K_BOOK | 252 | 3 | 2.0 | 1.0 |
| jl2 | OTHER | 1509 | 20 | 19.0 | 1.0 |
| jl2 | K_XIND | 414 | 6 | 6.0 | 0.0 |
| jl2 | K_TREND | 391 | 7 | 7.3 | -0.3 |
| jl2 | K_DAY | 222 | 6 | 6.5 | -0.5 |
| jl2 | K_MACD | 230 | 5 | 6.0 | -1.0 |
| jl2 | K_TAPE | 271 | 1 | 3.0 | -2.0 |
| jl2 | K_XMOVE | 411 | 4 | 6.0 | -2.0 |
| jl2 | K_SQZ | 190 | 0 | 2.5 | -2.5 |
| jl2 | K_VWAP | 228 | 4 | 7.0 | -3.0 |
| jl2 | K_WALL | 92 | 0 | 3.0 | -3.0 |
| jl2 | TAPE | 161 | 0 | 3.5 | -3.5 |
| jl2 | K_ALPHA | 183 | 0 | 4.0 | -4.0 |
| jl2 | K_OSC | 230 | 3 | 7.5 | -4.5 |
| jl2 | K_PATH | 23 | 0 |  |  |
| jl2 | K_RANGE | 69 | 0 |  |  |
| jl2 | LEVELS | 92 | 0 |  |  |
| jl2 | RANGE | 112 | 1 |  |  |
| jl2 | SQZ | 69 | 0 |  |  |
| raw | PATH | 227 | 12 | 2.3 | 9.7 |
| raw | OTHER | 1527 | 17 | 9.3 | 7.7 |
| raw | K_TREND15 | 167 | 10 | 4.0 | 6.0 |
| raw | K_L3 | 393 | 7 | 3.5 | 3.5 |
| raw | K_VWAP | 228 | 4 | 1.0 | 3.0 |
| raw | K_DAY | 228 | 4 | 2.0 | 2.0 |
| raw | K_BOOK | 252 | 3 | 1.5 | 1.5 |
| raw | K_XIND | 414 | 3 | 2.0 | 1.0 |
| raw | K_XMOVE | 412 | 4 | 3.0 | 1.0 |
| raw | K_ALPHA | 184 | 1 | 1.0 | 0.0 |
| raw | RANGE | 112 | 1 | 1.7 | -0.7 |
| raw | BOOK | 46 | 0 | 1.0 | -1.0 |
| raw | K_RANGE | 69 | 0 | 1.0 | -1.0 |
| raw | K_TAPE | 273 | 1 | 2.0 | -1.0 |
| raw | LEVELS | 92 | 0 | 1.0 | -1.0 |
| raw | K_PATH | 23 | 0 | 2.0 | -2.0 |
| raw | K_SQZ | 192 | 1 | 3.0 | -2.0 |
| raw | K_MACD | 230 | 0 | 2.3 | -2.3 |
| raw | K_TREND | 400 | 0 | 3.0 | -3.0 |
| raw | TAPE | 161 | 0 | 3.5 | -3.5 |
| raw | K_NKD | 184 | 5 |  |  |
| raw | K_OSC | 230 | 2 |  |  |
| raw | K_WALL | 92 | 5 |  |  |
| raw | SQZ | 69 | 1 |  |  |

**Replicated on both bases (t <= -2.5 on JL2 and on raw, L6M lift negative on both; the two bases share most trades, so this is consistency, not independent confirmation): 21 of 6141 cell-conditions**

| cell_book | cell_sess | cond | share_jl2 | lift_all_jl2 | t_all_jl2 | lift_all_raw | t_all_raw | lift_L6M_jl2 | lift_L6M_raw | pct_abs_jl2 | pct_abs_raw |
|--|--|--|--|--|--|--|--|--|--|--|--|
| H7 | ALL | pth_dist_stop_lt15 | 0.007 | -0.218 | -6.424 | -0.208 | -6.555 | -0.213 | -0.144 | 100.000 | 100.000 |
| P7 | ALL | clu_K_TREND15 | 0.165 | -0.137 | -4.051 | -0.090 | -2.535 | -0.183 | -0.105 | 100.000 | 100.000 |
| P7 | ALL | ag_nq_15m_ema_stack | 0.198 | -0.125 | -3.873 | -0.089 | -2.707 | -0.185 | -0.141 | 100.000 | 96.970 |
| P7 | ALL | ag_nq_15m_adx_di | 0.138 | -0.137 | -3.754 | -0.110 | -3.137 | -0.138 | -0.142 | 100.000 | 100.000 |
| M7 | nyam | flip_l3_n5_1m | 0.017 | -0.357 | -3.532 | -0.443 | -4.327 | -0.621 | -0.463 | 100.000 | 100.000 |
| H7 | asia | flip_es_5m_macd | 0.260 | -0.135 | -3.222 | -0.125 | -2.891 | -0.193 | -0.126 | 100.000 | 100.000 |
| U7 | ALL | ag_nq_15m_cci | 0.091 | -0.170 | -3.086 | -0.161 | -3.000 | -0.147 | -0.107 | 100.000 | 100.000 |
| H7 | asia | flip_tape_bignet10_5 | 0.026 | -0.332 | -3.076 | -0.357 | -2.810 | -0.383 | -0.491 | 100.000 | 93.939 |
| U7 | ALL | ag_mv_RTY_z5 | 0.288 | -0.081 | -3.055 | -0.081 | -3.048 | -0.044 | -0.014 | 100.000 | 100.000 |
| ALL | ALL | pth_open_lt_m0.5R | 0.031 | -0.048 | -2.982 | -0.040 | -2.927 | -0.029 | -0.038 | 93.939 | 100.000 |
| H7 | asia | flip_nq_1m_adx_di | 0.170 | -0.120 | -2.851 | -0.116 | -2.580 | -0.052 | -0.006 | 100.000 | 100.000 |
| O7 | ALL | ag_mk_NKD_ret15 | 0.347 | -0.274 | -2.720 | -0.238 | -2.566 | -0.106 | -0.085 | 100.000 | 100.000 |
| O7 | nyam | ag_mk_NKD_ret15 | 0.347 | -0.274 | -2.720 | -0.238 | -2.566 | -0.106 | -0.085 | 100.000 | 100.000 |
| U7 | asia | flip_nq_1m_vwap | 0.083 | -0.208 | -2.700 | -0.232 | -2.985 | -0.297 | -0.315 | 100.000 | 100.000 |
| U7 | asia | flip_dd_vwap | 0.083 | -0.208 | -2.700 | -0.232 | -2.985 | -0.297 | -0.315 | 100.000 | 100.000 |
| U7 | ALL | ag_mk_RTY_z5 | 0.273 | -0.074 | -2.674 | -0.073 | -2.665 | -0.061 | -0.028 | 96.667 | 100.000 |
| U7 | asia | cluflip_K_VWAP | 0.077 | -0.214 | -2.672 | -0.231 | -2.857 | -0.359 | -0.355 | 100.000 | 100.000 |
| U7 | ALL | flip_mk_RTY_z5 | 0.161 | -0.098 | -2.658 | -0.101 | -2.564 | -0.013 | -0.001 | 100.000 | 100.000 |
| U7 | ALL | flip_nq_1m_vwap | 0.116 | -0.139 | -2.575 | -0.153 | -2.705 | -0.128 | -0.150 | 96.667 | 100.000 |
| A7 | ALL | ag_mk_NQlead_RTY15 | 0.125 | -0.112 | -2.531 | -0.120 | -2.661 | -0.041 | -0.043 | 100.000 | 100.000 |
| A7 | asia | ag_mk_NQlead_RTY15 | 0.125 | -0.112 | -2.531 | -0.120 | -2.661 | -0.041 | -0.043 | 100.000 | 100.000 |

**Planted-edge check (run before any real result was read; flag at 15% share lowers rem_R by delta when on; 20 seeds per cell)**

| source | cell | delta | lift | t | pct | found |
|--|--|--|--|--|--|--|
| jl2 | A7 | 0.000 | 0.009 | 0.238 | 48.485 | 0.000 |
| jl2 | A7 | 0.080 | -0.071 | -1.909 | 95.455 | 0.200 |
| jl2 | A7 | 0.150 | -0.141 | -3.787 | 100.000 | 0.950 |
| jl2 | ALL | 0.000 | 0.003 | 0.282 | 44.394 | 0.000 |
| jl2 | ALL | 0.080 | -0.077 | -8.340 | 100.000 | 1.000 |
| jl2 | ALL | 0.150 | -0.147 | -15.885 | 100.000 | 1.000 |
| jl2 | H7 | 0.000 | 0.025 | 0.667 | 30.909 | 0.000 |
| jl2 | H7 | 0.080 | -0.055 | -1.468 | 90.455 | 0.100 |
| jl2 | H7 | 0.150 | -0.125 | -3.335 | 99.545 | 0.750 |
| jl2 | K7 | 0.000 | 0.001 | 0.055 | 49.848 | 0.000 |
| jl2 | K7 | 0.080 | -0.079 | -5.376 | 100.000 | 1.000 |
| jl2 | K7 | 0.150 | -0.149 | -10.128 | 100.000 | 1.000 |
| jl2 | M7 | 0.000 | 0.001 | 0.053 | 45.606 | 0.000 |
| jl2 | M7 | 0.080 | -0.079 | -3.826 | 99.848 | 0.950 |
| jl2 | M7 | 0.150 | -0.149 | -7.220 | 100.000 | 1.000 |
| jl2 | O7 | 0.000 | 0.005 | 0.049 | 51.212 | 0.000 |
| jl2 | O7 | 0.080 | -0.075 | -0.558 | 68.788 | 0.000 |
| jl2 | O7 | 0.150 | -0.145 | -1.088 | 79.848 | 0.050 |
| jl2 | P7 | 0.000 | -0.005 | -0.251 | 57.121 | 0.000 |
| jl2 | P7 | 0.080 | -0.085 | -4.496 | 100.000 | 0.950 |
| jl2 | P7 | 0.150 | -0.155 | -8.210 | 100.000 | 1.000 |
| jl2 | U7 | 0.000 | 0.010 | 0.290 | 47.727 | 0.000 |
| jl2 | U7 | 0.080 | -0.070 | -2.038 | 92.121 | 0.200 |
| jl2 | U7 | 0.150 | -0.140 | -4.075 | 99.848 | 0.950 |
| raw | A7 | 0.000 | -0.019 | -0.452 | 64.091 | 0.000 |
| raw | A7 | 0.080 | -0.099 | -2.453 | 93.182 | 0.550 |
| raw | A7 | 0.150 | -0.169 | -4.204 | 99.545 | 0.850 |
| raw | ALL | 0.000 | -0.003 | -0.295 | 68.182 | 0.000 |
| raw | ALL | 0.080 | -0.083 | -8.057 | 100.000 | 1.000 |
| raw | ALL | 0.150 | -0.153 | -14.850 | 100.000 | 1.000 |
| raw | H7 | 0.000 | 0.012 | 0.307 | 47.879 | 0.000 |
| raw | H7 | 0.080 | -0.068 | -1.663 | 97.727 | 0.100 |
| raw | H7 | 0.150 | -0.138 | -3.387 | 99.848 | 0.850 |
| raw | K7 | 0.000 | -0.004 | -0.258 | 61.970 | 0.000 |
| raw | K7 | 0.080 | -0.084 | -4.911 | 100.000 | 0.950 |
| raw | K7 | 0.150 | -0.154 | -8.982 | 100.000 | 1.000 |
| raw | M7 | 0.000 | -0.004 | -0.179 | 58.333 | 0.000 |
| raw | M7 | 0.080 | -0.084 | -3.600 | 99.697 | 0.850 |
| raw | M7 | 0.150 | -0.154 | -6.594 | 100.000 | 1.000 |
| raw | O7 | 0.000 | -0.025 | -0.209 | 61.061 | 0.000 |
| raw | O7 | 0.080 | -0.105 | -0.818 | 75.303 | 0.000 |
| raw | O7 | 0.150 | -0.175 | -1.352 | 85.606 | 0.050 |
| raw | P7 | 0.000 | -0.003 | -0.129 | 52.121 | 0.000 |
| raw | P7 | 0.080 | -0.083 | -4.160 | 99.848 | 0.950 |
| raw | P7 | 0.150 | -0.153 | -7.687 | 100.000 | 1.000 |
| raw | U7 | 0.000 | 0.011 | 0.316 | 40.909 | 0.000 |
| raw | U7 | 0.080 | -0.069 | -1.857 | 93.030 | 0.300 |
| raw | U7 | 0.150 | -0.139 | -3.758 | 99.848 | 0.950 |

Planted edge (run first, shuffled before any real result was read): the +0.15 R plant is found (lift < 0, |t| >= 2.6, percentile >= 95) in 95-100% of seeds in ALL, K7, M7, P7, U7 and A7, 75-85% in H7, 5% in O7 (417 trades); +0.08 R in 100% in ALL and K7, 85-95% in M7 and P7, 10-55% in the small books; zero plant never found (0%). So 'nothing found' means: nothing of 0.15 R or larger in books with 1,000+ trades, nothing of 0.08 R in the pooled and K7 / M7 / P7 cells.
### 2.4 The 5-second flow items (adverse / favourable aggressor trades and contracts over 5 and 15 s, acceleration of the adverse side, message-rate acceleration), checkpoints entry + 60 / 300 / 900 / 1800 / 3600 s, first 60 minutes only; 16 thresholded items x cells, same controls

JL2: 131 cell-items, 0 reach their cell bar

| cell | cond | n | share | lift | t | pct_abs | bar99 | lift_k60 | lift_k300 | lift_k900 | lift_k1800 | lift_k3600 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| O7 | acc_mps_ge1.5 | 1205 | 0.028 | -0.570 | -2.589 | 96.970 | 3.874 | -0.328 | -0.697 | -0.365 | -0.792 |  |
| M7 | ratio_adv_fav_15_tn_ge5 | 14631 | 0.015 | -0.115 | -2.149 | 100.000 | 2.622 | -0.251 | -0.039 | -0.053 | -0.020 | -0.305 |
| M7 | ratio_adv_fav_15_cps_ge5 | 14631 | 0.023 | -0.076 | -1.703 | 93.939 | 2.622 | -0.162 | -0.011 | -0.020 | -0.071 | -0.201 |
| H7 | adv5_ge10_fav_le2 | 4436 | 0.008 | -0.253 | -1.690 | 90.909 | 2.647 | -0.566 | -0.393 | 0.282 | -0.349 | -0.361 |
| M7 | ratio_adv_fav_15_cps_ge2 | 14631 | 0.146 | -0.035 | -1.632 | 87.879 | 2.622 | -0.021 | -0.004 | -0.039 | -0.063 | -0.082 |
| M7 | ratio_adv_fav_15_tn_ge3 | 14631 | 0.041 | -0.045 | -1.324 | 78.788 | 2.622 | -0.085 | 0.054 | -0.038 | -0.099 | -0.121 |
| P7 | ratio_adv_fav_15_cps_ge2 | 15452 | 0.231 | -0.018 | -1.220 | 66.667 | 2.963 | 0.018 | -0.015 | -0.035 | -0.012 | -0.069 |
| ALL | adv5_ge10_fav_le2 | 74397 | 0.008 | -0.036 | -1.105 | 72.727 | 2.369 | 0.087 | -0.108 | -0.098 | -0.070 | 0.012 |

RAW: 132 cell-items, 4 reach their cell bar

| cell | cond | n | share | lift | t | pct_abs | bar99 | lift_k60 | lift_k300 | lift_k900 | lift_k1800 | lift_k3600 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| M7 | combo_cps5_ge3_acc_ge2 | 14219 | 0.043 | -0.131 | -3.202 | 100.000 | 2.709 | -0.059 | -0.160 | -0.188 | -0.089 | -0.164 |
| M7 | ratio_adv_fav_5_cps_ge3 | 14219 | 0.096 | -0.087 | -3.123 | 100.000 | 2.709 | -0.075 | -0.054 | -0.163 | -0.033 | -0.106 |
| M7 | ratio_adv_fav_5_tn_ge2 | 14219 | 0.166 | -0.069 | -3.087 | 100.000 | 2.709 | -0.066 | -0.065 | -0.090 | -0.054 | -0.066 |
| O7 | acc_mps_ge1.5 | 1299 | 0.028 | -0.543 | -2.527 | 96.970 | 2.936 | -0.462 | -0.767 | -0.141 | -0.578 |  |
| M7 | ratio_adv_fav_5_cps_ge5 | 14219 | 0.045 | -0.108 | -2.518 | 96.970 | 2.709 | -0.104 | -0.110 | -0.161 | -0.083 | -0.062 |
| M7 | ratio_adv_fav_5_tn_ge3 | 14219 | 0.070 | -0.078 | -2.479 | 100.000 | 2.709 | -0.067 | -0.089 | -0.110 | -0.009 | -0.123 |
| M7 | ratio_adv_fav_5_cps_ge2 | 14219 | 0.204 | -0.048 | -2.370 | 93.939 | 2.709 | -0.064 | -0.059 | -0.021 | -0.013 | -0.090 |
| M7 | ratio_adv_fav_15_cps_ge2 | 14219 | 0.135 | -0.055 | -1.972 | 93.939 | 2.709 | 0.026 | -0.089 | -0.062 | -0.091 | -0.073 |

## 3. Part C2: exit confluence count (clusters against now / flipped since entry)
Method (frozen). 16 clusters (code/th_rexit/features.py CLUSTERS: TREND 1-5 min, TREND15, OSC, MACD, SQZ, VWAP, DAY, XIND (ES / RTY states), XMOVE, NKD, ALPHA, TAPE, BOOK, WALL, L3, RANGE); cluster vote = mean of its members' ternary votes; against when <= -0.5. 'now' = number of clusters against now; 'flip' = number that were not against at entry and are now (the directive's 'count of flips'). Rows with fewer than 12 known clusters are dropped (on average 15.9 of 16 known). Table: mean remaining R by count 0, 1, 2, 3, 4+; the main statistic is the slope of the remaining R on min(count, 4) AFTER regressing both on open R, give-back R, ln(minutes in trade) and book x session effects (profit / loss state and time in trade are mechanically tied to how many readings are against), week-clustered t; raw slope beside; controls = the same count built from the shifted flags (11/23/37) and from 30 persistent-draw random cluster flags with each cluster's realised share matched within 0.05; pct_abs_t = share of controls with a smaller |t|. A staircase flag needs >= 3 of 4 steps down, adjusted slope < 0 and slope percentile >= 95. By state: open < 0 (loss) and open >= 0 (profit) separately, because the thresholds are separate.
**Pooled ALL cell: mean remaining R by number of clusters against (0,1,2,3,4+), all months**

| source | count_def | state | n | mean0 | mean1 | mean2 | mean3 | mean4plus | steps_down | slope_raw | t_raw | slope_adj | t_adj | pct_abs_t |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| jl2 | now | all | 61372 | 0.058 | 0.065 | 0.043 | 0.064 | 0.030 | 2 | -0.007 | -2.036 | -0.005 | -1.196 | 72.727 |
| jl2 | now | loss | 28846 | 0.071 | 0.056 | 0.037 | 0.065 | 0.025 | 3 | -0.009 | -1.827 | -0.006 | -1.091 | 69.697 |
| jl2 | now | profit | 32526 | 0.054 | 0.069 | 0.047 | 0.062 | 0.046 | 2 | -0.003 | -0.532 | -0.005 | -0.805 | 51.515 |
| jl2 | flip | all | 61363 | 0.054 | 0.052 | 0.053 | 0.055 | 0.030 | 2 | -0.004 | -1.510 | -0.002 | -0.454 | 33.333 |
| jl2 | flip | loss | 28840 | 0.049 | 0.047 | 0.053 | 0.044 | 0.024 | 3 | -0.006 | -1.496 | -0.004 | -0.714 | 57.576 |
| jl2 | flip | profit | 32523 | 0.056 | 0.055 | 0.054 | 0.080 | 0.082 | 2 | 0.004 | 0.812 | 0.001 | 0.194 | 12.121 |
| raw | now | all | 69375 | 0.056 | 0.057 | 0.040 | 0.058 | 0.038 | 2 | -0.004 | -1.094 | -0.003 | -0.619 | 36.364 |
| raw | now | loss | 35409 | 0.066 | 0.052 | 0.039 | 0.062 | 0.033 | 3 | -0.006 | -1.060 | -0.003 | -0.514 | 39.394 |
| raw | now | profit | 33966 | 0.053 | 0.059 | 0.041 | 0.052 | 0.056 | 1 | -0.001 | -0.187 | -0.003 | -0.432 | 30.303 |
| raw | flip | all | 69367 | 0.059 | 0.044 | 0.055 | 0.040 | 0.034 | 3 | -0.005 | -1.582 | -0.005 | -1.061 | 75.758 |
| raw | flip | loss | 35401 | 0.062 | 0.041 | 0.063 | 0.033 | 0.030 | 3 | -0.007 | -1.526 | -0.005 | -0.874 | 69.697 |
| raw | flip | profit | 33966 | 0.058 | 0.046 | 0.044 | 0.058 | 0.080 | 2 | -0.001 | -0.092 | -0.004 | -0.593 | 33.333 |

**JL2: finer bins, pooled (exploratory, the frozen bins stop at 4+); se_week = week-clustered standard error of the bin mean**

| count | n_flip | n_now | mean_rem_R_flip | mean_rem_R_now | se_week_flip | se_week_now |
|--|--|--|--|--|--|--|
| 0.000 | 17954.000 | 7799.000 | 0.054 | 0.058 | 0.010 | 0.015 |
| 1.000 | 17786.000 | 14551.000 | 0.052 | 0.065 | 0.009 | 0.011 |
| 2.000 | 10965.000 | 13458.000 | 0.053 | 0.043 | 0.013 | 0.011 |
| 3.000 | 5933.000 | 9701.000 | 0.055 | 0.064 | 0.014 | 0.012 |
| 4.000 | 3394.000 | 5793.000 | 0.044 | 0.056 | 0.016 | 0.014 |
| 5.000 | 2169.000 | 3703.000 | 0.025 | 0.029 | 0.019 | 0.016 |
| 6.000 | 1381.000 | 2383.000 | 0.037 | -0.003 | 0.020 | 0.019 |
| 7.000 | 818.000 | 1532.000 | 0.027 | 0.043 | 0.028 | 0.022 |
| 8.000 | 549.000 | 1090.000 | -0.001 | 0.022 | 0.032 | 0.023 |
| 9.000 | 414.000 | 1362.000 | -0.026 | -0.031 | 0.036 | 0.024 |

**Cells (all months) with an adjusted slope t <= -1.8, either count definition and state**

| source | cdef | stratum | cell_book | cell_sess | n | mean0 | mean1 | mean2 | mean3 | mean4 | slope_adj | t_adj | slope_raw | t_raw | pct_abs_t | steps_down |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| jl2 | now | profit | K7 | asia | 4668 | 0.110 | 0.098 | 0.058 | 0.038 | 0.022 | -0.027 | -2.214 | -0.024 | -2.120 | 100.000 | 4 |
| jl2 | now | loss | M7 | london | 4043 | 0.143 | -0.022 | 0.001 | 0.014 | -0.002 | -0.024 | -1.836 | -0.013 | -1.223 | 84.848 | 2 |
| jl2 | now | all | P7 | ALL | 13103 | 0.073 | 0.070 | 0.029 | 0.064 | 0.021 | -0.016 | -2.030 | -0.012 | -1.914 | 90.909 | 3 |
| jl2 | now | profit | P7 | ALL | 7190 | 0.070 | 0.077 | 0.039 | 0.048 | 0.004 | -0.022 | -2.239 | -0.017 | -1.749 | 93.939 | 2 |
| jl2 | now | all | P7 | asia | 7472 | 0.118 | 0.089 | 0.060 | 0.082 | 0.036 | -0.023 | -2.255 | -0.017 | -2.023 | 100.000 | 3 |
| jl2 | now | profit | P7 | asia | 4100 | 0.125 | 0.097 | 0.072 | 0.033 | 0.027 | -0.035 | -2.717 | -0.026 | -2.195 | 96.970 | 4 |
| jl2 | now | profit | P7 | nyam | 371 | 0.204 | 0.171 | -0.121 | 0.163 | -0.362 | -0.079 | -2.169 | -0.092 | -2.680 | 100.000 | 3 |
| jl2 | flip | all | U7 | ALL | 5267 | 0.078 | 0.081 | 0.070 | 0.040 | -0.017 | -0.024 | -1.911 | -0.022 | -2.421 | 100.000 | 3 |
| jl2 | now | all | U7 | london | 2457 | 0.180 | 0.073 | 0.029 | 0.026 | -0.008 | -0.041 | -1.958 | -0.037 | -2.365 | 93.939 | 4 |
| jl2 | flip | all | U7 | london | 2457 | 0.109 | 0.055 | 0.057 | -0.034 | -0.023 | -0.045 | -2.444 | -0.033 | -2.597 | 96.970 | 2 |
| jl2 | flip | loss | U7 | london | 1276 | 0.050 | 0.028 | 0.060 | -0.035 | -0.032 | -0.047 | -2.021 | -0.023 | -1.204 | 87.879 | 2 |
| raw | flip | loss | H7 | nyam | 573 | 0.178 | 0.027 | -0.126 | -0.018 | -0.030 | -0.062 | -1.828 | -0.040 | -1.344 | 96.667 | 3 |
| raw | now | all | P7 | asia | 8329 | 0.118 | 0.099 | 0.055 | 0.036 | 0.042 | -0.027 | -2.440 | -0.019 | -2.108 | 100.000 | 3 |
| raw | now | profit | P7 | asia | 3994 | 0.083 | 0.110 | 0.061 | -0.056 | 0.047 | -0.028 | -1.845 | -0.029 | -1.959 | 90.000 | 2 |

**Real vs shuffled-outcome null (staircase_flag counts all windows and strata, frozen rule; the t columns count win = all only)**

| source | run | cells | staircase_flag | cells_t_adj_le_m2 | cells_t_adj_ge_2 |
|--|--|--|--|--|--|
| jl2 | REAL | 138 | 28 | 8 | 3 |
| jl2 | null 1 | 138 | 6 | 3 | 0 |
| jl2 | null 2 | 138 | 10 | 3 | 2 |
| jl2 | null 3 | 138 | 9 | 6 | 0 |
| raw | REAL | 138 | 22 | 1 | 4 |
| raw | null 1 | 138 | 1 | 0 | 0 |
| raw | null 2 | 138 | 1 | 0 | 5 |
| raw | null 3 | 138 | 9 | 1 | 0 |

Reading: the pooled bins are flat (JL2 now: +0.058, +0.065, +0.043, +0.064, +0.030 R for 0, 1, 2, 3, 4+; raw: +0.053, +0.055, +0.041, +0.058, +0.039): not a staircase on either base. The finer bins show only a soft decline above 5 clusters and a negative mean at 9+ (-0.03 R, SE 0.02), where the trade is typically already deep against the entry. Minimum detectable slope: the pooled adjusted slope has a standard error of 0.0045 R per cluster (0.018 R over the 4 steps), so a slope under about 0.013 per cluster step (0.05 R over 0..4+) cannot be seen in the pooled cell, and 0.03-0.06 per step in single book x session cells. The slope percentile of the frozen rule (pct_adj in the parquet) is high in many cells because random controls are far less noisy than a regime-persistent real count; pct_abs_t (shown) is the fair comparison. Frozen-rule staircase flags (all windows and strata): JL2 28 vs 6 / 10 / 9 in the three nulls, raw 22 vs 1 / 1 / 9; cells with adjusted t <= -2 (win all): JL2 8 vs 3 / 3 / 6, raw 1 vs 0 / 0 / 1. JL2 shows a mild excess carried by P7 Asia and U7 (overlapping cells), the raw base none. Treat P7 Asia and U7 as LEADS.
## 4. Parts C3, D, E: one exit score per book, walk-forward, actions, controls
Method (frozen in REXIT_C3_PREREG.md). Rows = every 5th closed minute in trade (5, 10, ..., 480), per book, target rem_R. Features: the signed readings, 16 cluster votes, count against, count flipped, path state, missing-block indicators (about 160 columns). Walk-forward: 2-week test blocks, training = the trailing 26 weeks of trades that were entered AND closed before the block (label known), ridge (alpha from {1,000, 10,000, 100,000}, chosen on the last 4 training weeks; deviation from the frozen grid logged) and LightGBM (150 trees, 8 leaves) as the boosted check, and a path-only ridge as the baseline for what the readings add; scores exist from 2023-10. Actions on the predicted remaining R, thresholds separate in profit (open > 0) and in loss: X = exit the trade, H = take half and move the stop of the rest to breakeven (in profit) / cut half (in loss), B = tighten the stop (profit: to breakeven; loss: 20 pt below the price); grid {off, -0.05, -0.10, -0.20, -0.30} R in each state = 24 per family, 72 per book; cost 1.2 pt per exit; path arithmetic on the stored 1-s paths (no re-entry, no engine).
**4.1 Out-of-sample information coefficient (Spearman, score vs remaining R, all out-of-sample rows 2023-10..2026-10; t = mean/SE of the weekly ICs)**

| source | book | oos_rows | ridge_ic_all | ridge_t | ridge_ic_profit | ridge_ic_loss | ridge_ic_L6M | gbm_ic_all | gbm_t | gbm_ic_profit | gbm_ic_loss | pathonly_ic_all | pathonly_t | null_ic_mean | null_ic_sd | n_null |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| jl2 | K7 | 126758 | -0.029 | -0.681 | -0.031 | -0.022 | 0.008 | 0.003 | 1.040 | 0.010 | 0.001 | -0.030 | -0.004 | -0.003 | 0.018 | 9 |
| jl2 | M7 | 57557 | -0.018 | -0.431 | -0.025 | -0.016 | -0.016 | -0.004 | 0.450 | 0.001 | 0.018 | -0.037 | -2.182 | -0.009 | 0.013 | 9 |
| jl2 | U7 | 42624 | -0.052 | -3.331 | -0.071 | -0.025 | -0.073 | -0.013 | 0.587 | -0.050 | 0.040 | -0.061 | -3.999 | -0.004 | 0.017 | 9 |
| jl2 | P7 | 89281 | 0.002 | -0.255 | -0.004 | 0.016 | -0.002 | 0.013 | -0.072 | 0.004 | 0.039 | -0.031 | -1.183 | 0.008 | 0.011 | 9 |
| jl2 | H7 | 33329 | 0.006 | -1.652 | 0.005 | -0.001 | -0.127 | -0.004 | 1.935 | -0.017 | -0.005 | -0.025 | -2.760 | 0.001 | 0.011 | 9 |
| jl2 | A7 | 35011 | 0.023 | 1.277 | -0.039 | 0.067 | 0.029 | 0.070 | 2.258 | 0.035 | 0.106 | 0.033 | 1.122 |  |  | 9 |
| jl2 | O7 | 0 |  |  |  |  |  |  |  |  |  |  |  |  |  | 6 |
| raw | K7 | 140707 | -0.003 | 0.333 | 0.008 | -0.009 | 0.027 | -0.002 | 0.723 | 0.013 | -0.012 | 0.012 | 1.222 | 0.007 | 0.010 | 9 |
| raw | M7 | 71584 | -0.013 | -3.390 | -0.021 | -0.019 | -0.043 | -0.015 | -1.611 | 0.012 | -0.031 | -0.021 | -3.674 | -0.004 | 0.013 | 9 |
| raw | U7 | 44847 | -0.040 | -1.090 | -0.042 | -0.029 | -0.049 | -0.007 | 0.908 | -0.032 | 0.033 | -0.038 | -1.551 | -0.004 | 0.015 | 9 |
| raw | P7 | 121736 | -0.040 | -1.982 | -0.054 | -0.046 | -0.011 | -0.024 | -0.630 | -0.050 | -0.008 | -0.040 | -1.608 | -0.003 | 0.024 | 9 |
| raw | H7 | 36066 | -0.026 | -2.662 | -0.027 | -0.030 | -0.227 | -0.025 | -0.227 | -0.040 | -0.026 | -0.024 | -3.400 | -0.008 | 0.017 | 9 |
| raw | A7 | 35661 | 0.031 | 1.053 | -0.025 | 0.065 | 0.026 | 0.099 | 3.003 | 0.068 | 0.116 | 0.043 | 1.197 |  |  | 9 |
| raw | O7 | 0 |  |  |  |  |  |  |  |  |  |  |  |  |  | 6 |

Reading: an exit score is useful only if its out-of-sample rank correlation with the remaining R is clearly positive; the IC of a score that tells the desk when to leave is about 0.01-0.03 at best in this problem. null_ic = the same ridge pipeline with the outcome permuted inside session x checkpoint (3 seeds) and with the readings taken from the trade 11 / 23 / 37 trading days earlier (3 shifts), mean and sd of those six runs.

**4.2 JL2: best of the 72 variants per book (path arithmetic on the stored 1-s paths, base lots, out-of-sample weeks; d_usd = weekly P&L difference vs the unchanged trade; family tests over all 72; control percentile = share of the 30 random-exit draws that are worse than the real variant; dd in $ of weekly cumulative P&L)**

| book | weeks | trades_oos | best_by_mean | d_usd_week | d_usd_week_x175 | real_usd_week | t_week | RC_p | SPA_p | DSR | BH_disc | PBO16 | PBO12 | dd_real | dd_best_mean | dd_best_dd | best_by_dd | ctl_pct_mean | ctl_pct_dd | ctl_n | ctl_share |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 | 161 | 6049 | B pNone l-0.3 | 0 | 0 | 3522 | 1.000 | 0.980 | 0.699 | 0.000 | 0 | 0.004 | 0.001 | 32592 | 32592 | 32592 | H p-0.1 lNone |  |  | 0 | 0.000 |
| M7 | 161 | 3186 | B p-0.2 l-0.05 | 60 | 105 | 604 | 0.676 | 0.800 | 0.803 | 0.261 | 0 | 0.280 | 0.301 | 42530 | 34057 | 32516 | B p-0.1 l-0.05 | 97 | 87 | 30 | 0.230 |
| U7 | 161 | 1155 | X pNone l-0.2 | 245 | 429 | 1450 | 1.888 | 0.532 | 0.260 | 0.216 | 0 | 0.025 | 0.052 | 42266 | 31317 | 25233 | X pNone l-0.05 | 100 | 100 | 29 | 0.086 |
| P7 | 161 | 3289 | B p-0.1 l-0.05 | 28 | 48 | 3922 | 0.135 | 0.922 | 0.938 | 0.147 | 0 | 0.544 | 0.604 | 36379 | 35159 | 33863 | H pNone l-0.05 | 90 | 73 | 30 | 0.208 |
| H7 | 161 | 871 | B pNone l-0.2 | 33 | 58 | 1204 | 1.659 | 0.929 | 0.242 | 0.311 | 0 | 0.139 | 0.126 | 35057 | 33388 | 26772 | X p-0.3 l-0.2 | 75 | 62 | 24 | 0.040 |
| A7 | 134 | 818 | B p-0.1 l-0.05 | 50 | 87 | 803 | 0.579 | 0.842 | 0.898 | 0.066 | 0 | 0.583 | 0.552 | 7738 | 7617 | 6263 | X p-0.05 l-0.05 | 90 | 63 | 30 | 0.286 |

**4.3 JL2: drawdown as a distribution (stationary block bootstrap of the out-of-sample weekly P&L, 3,000 resamples, block length from the autocorrelation; thresholds = multiples of the average weekly profit of the unchanged book)**

| book | real_median_dd | real_p95_dd | real_p_gt_1x | real_p_gt_3x | bestmean_median_dd | bestmean_p95 | bestdd_median_dd | bestdd_p95 | block_len |
|--|--|--|--|--|--|--|--|--|--|
| K7 | 30981 | 52546 | 1.000 | 1.000 | 30981 | 52546 | 31337 | 53212 | 1.0 |
| M7 | 42928 | 82455 | 1.000 | 1.000 | 41586 | 79862 | 42289 | 81381 | 1.6 |
| U7 | 44261 | 79705 | 1.000 | 1.000 | 38956 | 69231 | 42791 | 81925 | 1.0 |
| P7 | 36379 | 54441 | 1.000 | 1.000 | 40209 | 70161 | 33863 | 51448 | 13.2 |
| H7 | 25744 | 46116 | 1.000 | 1.000 | 25244 | 45179 | 24911 | 45057 | 1.0 |
| A7 | 13053 | 23345 | 1.000 | 1.000 | 11140 | 19659 | 11128 | 20584 | 1.0 |

**4.4 JL2: simple give-back rule on the same trades (exit when give-back >= F of best, best >= B pts; 9 variants per book; 1-s paths; best by d_usd_week shown per book; all 9 in c3_ctl_jl2.json)**

| book | F | B_pts | share_exited | d_usd_week | d_dd | d_worst_week |
|--|--|--|--|--|--|--|
| H7 | 0.600 | 40.000 | 0.262 | -145 | -10446 | -774 |
| U7 | 0.500 | 40.000 | 0.313 | -156 | -6147 | 2408 |
| M7 | 0.600 | 40.000 | 0.234 | -161 | -6574 | 1832 |
| A7 | 0.400 | 40.000 | 0.399 | -327 | 4401 | 1916 |
| P7 | 0.600 | 40.000 | 0.230 | -641 | 2439 | 3306 |
| K7 | 0.600 | 40.000 | 0.251 | -803 | -1503 | 1909 |

**4.5 JL2 (part E): which trades the best-by-mean variant helps (groups exclusive: winner that gave it back = MFE >= 30 pt and final < 25% of MFE; loser that never went green = MFE <= 2 pt and a loss; cut by the current loss lines = StateCut / EarlyCut / StackCut / BookLock exits; other)**

| book | variant | group | n_trades | n_fired | d_usd_total | d_usd_per_fired | real_usd_total |
|--|--|--|--|--|--|--|--|
| K7 | B None -0.3 | winner_gave_back | 1886 | 2 | 42 | 21 | -1682855 |
| K7 | B None -0.3 | loser_never_green | 308 | 0 | 0 |  | -275668 |
| K7 | B None -0.3 | cut_by_loss_line | 1122 | 0 | 0 |  | -1040498 |
| K7 | B None -0.3 | other | 2733 | 1 | 0 | 0 | 3566055 |
| M7 | B -0.2 -0.05 | winner_gave_back | 1035 | 286 | 70687 | 247 | -934835 |
| M7 | B -0.2 -0.05 | loser_never_green | 170 | 47 | 6409 | 136 | -151406 |
| M7 | B -0.2 -0.05 | cut_by_loss_line | 535 | 138 | 20311 | 147 | -462984 |
| M7 | B -0.2 -0.05 | other | 1446 | 261 | -87736 | -336 | 1646492 |
| U7 | X None -0.2 | winner_gave_back | 328 | 44 | 58650 | 1333 | -747532 |
| U7 | X None -0.2 | loser_never_green | 46 | 5 | 7360 | 1472 | -104164 |
| U7 | X None -0.2 | cut_by_loss_line | 41 | 6 | 3708 | 618 | -60917 |
| U7 | X None -0.2 | other | 740 | 44 | -30216 | -687 | 1146063 |
| P7 | B -0.1 -0.05 | winner_gave_back | 1001 | 222 | 143391 | 646 | -1458670 |
| P7 | B -0.1 -0.05 | loser_never_green | 173 | 33 | 8983 | 272 | -208857 |
| P7 | B -0.1 -0.05 | cut_by_loss_line | 687 | 140 | 52461 | 375 | -965031 |
| P7 | B -0.1 -0.05 | other | 1428 | 289 | -200376 | -693 | 3264020 |
| H7 | B None -0.2 | winner_gave_back | 255 | 13 | 4936 | 380 | -375009 |
| H7 | B None -0.2 | loser_never_green | 33 | 1 | -11 | -11 | -43760 |
| H7 | B None -0.2 | cut_by_loss_line | 64 | 4 | 226 | 57 | -76474 |
| H7 | B None -0.2 | other | 519 | 17 | 193 | 11 | 689143 |
| A7 | B -0.1 -0.05 | winner_gave_back | 228 | 75 | 54359 | 725 | -240407 |
| A7 | B -0.1 -0.05 | loser_never_green | 38 | 4 | 1058 | 264 | -42136 |
| A7 | B -0.1 -0.05 | cut_by_loss_line | 32 | 5 | 2200 | 440 | -26974 |
| A7 | B -0.1 -0.05 | other | 520 | 150 | -50942 | -340 | 417145 |

**4.6 JL2: HOLD path 2025-11-17..12-10 alone (3.5 weeks, trade-order cumulative drawdown in $, base lots)**

| book | pick | variant | trades_in_HOLD | fired | d_usd | real_usd | policy_usd | dd_real | dd_policy | worst_trade_real | worst_trade_policy |
|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 | best_mean | B None -0.3 | 144 | 0 | 0 | -16920 | -16920 | 34366 | 34366 | -1932 | -1932 |
| K7 | best_dd | H -0.1 None | 144 | 0 | 0 | -16920 | -16920 | 34366 | 34366 | -1932 | -1932 |
| M7 | best_mean | B -0.2 -0.05 | 79 | 11 | 784 | 2616 | 3401 | 13078 | 12534 | -2152 | -2152 |
| M7 | best_dd | B -0.1 -0.05 | 79 | 11 | 784 | 2616 | 3401 | 13078 | 12534 | -2152 | -2152 |
| U7 | best_mean | X None -0.2 | 25 | 0 | 0 | -17595 | -17595 | 21235 | 21235 | -5080 | -5080 |
| U7 | best_dd | X None -0.05 | 25 | 0 | 0 | -17595 | -17595 | 21235 | 21235 | -5080 | -5080 |
| P7 | best_mean | B -0.1 -0.05 | 87 | 14 | -1017 | -4435 | -5452 | 14907 | 14330 | -3914 | -3914 |
| P7 | best_dd | H None -0.05 | 87 | 14 | -2991 | -4435 | -7426 | 14907 | 15180 | -3914 | -3914 |
| H7 | best_mean | B None -0.2 | 17 | 0 | 0 | -4370 | -4370 | 6960 | 6960 | -2954 | -2954 |
| H7 | best_dd | X -0.3 -0.2 | 17 | 0 | 0 | -4370 | -4370 | 6960 | 6960 | -2954 | -2954 |
| A7 | best_mean | B -0.1 -0.05 | 14 | 0 | 0 | 3429 | 3429 | 2400 | 2400 | -1215 | -1215 |
| A7 | best_dd | X -0.05 -0.05 | 14 | 0 | 0 | 3429 | 3429 | 2400 | 2400 | -1215 | -1215 |

**4.2 RAW: best of the 72 variants per book (path arithmetic on the stored 1-s paths, base lots, out-of-sample weeks; d_usd = weekly P&L difference vs the unchanged trade; family tests over all 72; control percentile = share of the 30 random-exit draws that are worse than the real variant; dd in $ of weekly cumulative P&L)**

| book | weeks | trades_oos | best_by_mean | d_usd_week | d_usd_week_x175 | real_usd_week | t_week | RC_p | SPA_p | DSR | BH_disc | PBO16 | PBO12 | dd_real | dd_best_mean | dd_best_dd | best_by_dd | ctl_pct_mean | ctl_pct_dd | ctl_n | ctl_share |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 | 161 | 6345 | X p-0.1 lNone | 147 | 258 | 3369 | 0.638 | 0.689 | 0.823 | 0.140 | 0 | 0.517 | 0.555 | 83875 | 83875 | 83875 | X pNone l-0.05 | 30 | 23 | 30 | 0.057 |
| M7 | 161 | 3231 | B pNone l-0.2 | 56 | 99 | -1 | 0.866 | 0.904 | 0.774 | 0.213 | 0 | 0.359 | 0.326 | 108840 | 99996 | 65056 | B p-0.1 l-0.05 | 75 | 80 | 20 | 0.037 |
| U7 | 161 | 1207 | B pNone l-0.05 | 377 | 660 | 1671 | 1.179 | 0.627 | 0.558 | 0.083 | 0 | 0.054 | 0.189 | 90375 | 78888 | 62182 | X pNone l-0.05 | 100 | 77 | 30 | 0.316 |
| P7 | 161 | 4809 | B p-0.3 l-0.2 | 271 | 475 | 7866 | 0.845 | 0.839 | 0.630 | 0.034 | 0 | 0.014 | 0.019 | 234532 | 227568 | 216893 | X p-0.1 l-0.2 | 62 | 88 | 8 | 0.025 |
| H7 | 161 | 928 | B pNone l-0.2 | 17 | 29 | 1757 | 0.162 | 0.917 | 0.887 | 0.207 | 0 | 0.209 | 0.275 | 63718 | 57330 | 53011 | X p-0.1 l-0.3 | 71 | 82 | 28 | 0.051 |
| A7 | 134 | 833 | B p-0.3 l-0.2 | 79 | 138 | 756 | 1.584 | 0.618 | 0.193 | 0.253 | 0 | 0.173 | 0.149 | 10430 | 10430 | 9134 | X p-0.1 l-0.05 | 96 | 36 | 28 | 0.106 |

**4.3 RAW: drawdown as a distribution (stationary block bootstrap of the out-of-sample weekly P&L, 3,000 resamples, block length from the autocorrelation; thresholds = multiples of the average weekly profit of the unchanged book)**

| book | real_median_dd | real_p95_dd | real_p_gt_1x | real_p_gt_3x | bestmean_median_dd | bestmean_p95 | bestdd_median_dd | bestdd_p95 | block_len |
|--|--|--|--|--|--|--|--|--|--|
| K7 | 66999 | 120030 | 1.000 | 1.000 | 59541 | 107078 | 69452 | 129196 | 1.0 |
| M7 | 119530 | 238091 |  |  | 114366 | 229788 | 115125 | 233215 | 1.0 |
| U7 | 89981 | 175388 | 1.000 | 1.000 | 80814 | 154405 | 100425 | 204280 | 1.2 |
| P7 | 206190 | 378279 | 1.000 | 1.000 | 200453 | 363627 | 201796 | 367086 | 1.0 |
| H7 | 59538 | 110031 | 1.000 | 1.000 | 58107 | 106584 | 55444 | 102864 | 1.6 |
| A7 | 14605 | 26650 | 1.000 | 1.000 | 13340 | 23390 | 13010 | 24310 | 1.0 |

**4.4 RAW: simple give-back rule on the same trades (exit when give-back >= F of best, best >= B pts; 9 variants per book; 1-s paths; best by d_usd_week shown per book; all 9 in c3_ctl_raw.json)**

| book | F | B_pts | share_exited | d_usd_week | d_dd | d_worst_week |
|--|--|--|--|--|--|--|
| U7 | 0.500 | 40.000 | 0.316 | 147 | 757 | 700 |
| M7 | 0.500 | 25.000 | 0.586 | -147 | -25238 | -2830 |
| H7 | 0.600 | 40.000 | 0.284 | -187 | -11192 | -490 |
| A7 | 0.600 | 40.000 | 0.317 | -352 | 8608 | 1394 |
| K7 | 0.600 | 40.000 | 0.275 | -910 | -12374 | 5838 |
| P7 | 0.500 | 40.000 | 0.323 | -3677 | 9764 | 12821 |

**4.5 RAW (part E): which trades the best-by-mean variant helps (groups exclusive: winner that gave it back = MFE >= 30 pt and final < 25% of MFE; loser that never went green = MFE <= 2 pt and a loss; cut by the current loss lines = StateCut / EarlyCut / StackCut / BookLock exits; other)**

| book | variant | group | n_trades | n_fired | d_usd_total | d_usd_per_fired | real_usd_total |
|--|--|--|--|--|--|--|--|
| K7 | X -0.1 None | winner_gave_back | 1856 | 127 | 282367 | 2223 | -3728427 |
| K7 | X -0.1 None | loser_never_green | 280 | 1 | 2492 | 2492 | -604924 |
| K7 | X -0.1 None | cut_by_loss_line | 58 | 0 | 0 |  | -114313 |
| K7 | X -0.1 None | other | 4151 | 231 | -261130 | -1130 | 4990060 |
| M7 | B None -0.2 | winner_gave_back | 986 | 42 | 35832 | 853 | -1895045 |
| M7 | B None -0.2 | loser_never_green | 149 | 5 | 3385 | 677 | -300775 |
| M7 | B None -0.2 | cut_by_loss_line | 0 | 0 | 0 |  | 0 |
| M7 | B None -0.2 | other | 2096 | 72 | -30130 | -418 | 2195715 |
| U7 | B None -0.05 | winner_gave_back | 327 | 131 | 285215 | 2177 | -1559505 |
| U7 | B None -0.05 | loser_never_green | 63 | 17 | 31272 | 1840 | -303293 |
| U7 | B None -0.05 | cut_by_loss_line | 1 | 0 | 0 |  | -4514 |
| U7 | B None -0.05 | other | 816 | 233 | -255793 | -1098 | 2136270 |
| P7 | B -0.3 -0.2 | winner_gave_back | 1370 | 49 | 142738 | 2913 | -8314840 |
| P7 | B -0.3 -0.2 | loser_never_green | 169 | 1 | 1519 | 1519 | -1023332 |
| P7 | B -0.3 -0.2 | cut_by_loss_line | 0 | 0 | 0 |  | 0 |
| P7 | B -0.3 -0.2 | other | 3270 | 69 | -100551 | -1457 | 10604532 |
| H7 | B None -0.2 | winner_gave_back | 262 | 17 | 27018 | 1589 | -855046 |
| H7 | B None -0.2 | loser_never_green | 46 | 5 | 4158 | 832 | -164592 |
| H7 | B None -0.2 | cut_by_loss_line | 17 | 1 | 157 | 157 | -64171 |
| H7 | B None -0.2 | other | 603 | 24 | -28670 | -1195 | 1366740 |
| A7 | B -0.3 -0.2 | winner_gave_back | 228 | 28 | 21456 | 766 | -266040 |
| A7 | B -0.3 -0.2 | loser_never_green | 40 | 1 | 136 | 136 | -46565 |
| A7 | B -0.3 -0.2 | cut_by_loss_line | 0 | 0 | 0 |  | 0 |
| A7 | B -0.3 -0.2 | other | 565 | 59 | -10988 | -186 | 413855 |

**4.6 RAW: HOLD path 2025-11-17..12-10 alone (3.5 weeks, trade-order cumulative drawdown in $, base lots)**

| book | pick | variant | trades_in_HOLD | fired | d_usd | real_usd | policy_usd | dd_real | dd_policy | worst_trade_real | worst_trade_policy |
|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 | best_mean | X -0.1 None | 167 | 57 | -764 | -37779 | -38542 | 54835 | 49154 | -2895 | -2895 |
| K7 | best_dd | X None -0.05 | 167 | 59 | 11020 | -37779 | -26759 | 54835 | 51152 | -2895 | -2895 |
| M7 | best_mean | B None -0.2 | 86 | 0 | 0 | 445 | 445 | 29670 | 29670 | -2545 | -2545 |
| M7 | best_dd | B -0.1 -0.05 | 86 | 7 | 3158 | 445 | 3603 | 29670 | 27189 | -2545 | -2545 |
| U7 | best_mean | B None -0.05 | 30 | 0 | 0 | -8675 | -8675 | 28205 | 28205 | -4925 | -4925 |
| U7 | best_dd | X None -0.05 | 30 | 0 | 0 | -8675 | -8675 | 28205 | 28205 | -4925 | -4925 |
| P7 | best_mean | B -0.3 -0.2 | 131 | 6 | 10994 | 3707 | 14702 | 67985 | 59574 | -9285 | -9285 |
| P7 | best_dd | X -0.1 -0.2 | 131 | 18 | -7042 | 3707 | -3335 | 67985 | 61777 | -9285 | -9285 |
| H7 | best_mean | B None -0.2 | 17 | 0 | 0 | -3085 | -3085 | 16375 | 16375 | -4825 | -4825 |
| H7 | best_dd | X -0.1 -0.3 | 17 | 1 | -4846 | -3085 | -7931 | 16375 | 16375 | -4825 | -4825 |
| A7 | best_mean | B -0.3 -0.2 | 14 | 1 | 473 | 2420 | 2894 | 2400 | 2380 | -1215 | -1215 |
| A7 | best_dd | X -0.1 -0.05 | 14 | 3 | 450 | 2420 | 2870 | 2400 | 2380 | -1215 | -1215 |

**4.7 Selection null: the whole pipeline (walk-forward ridge on PERMUTED outcomes, same 72-variant search) vs the real run; best-of-72 mean gain ($/week, base lots) and best-of-72 max-drawdown cut (% of the unchanged out-of-sample weekly max DD); 3 permutation seeds per book**

| source | book | run | best_mean | best_dd_cut_pct | dd0 |
|--|--|--|--|--|--|
| jl2 | K7 | REAL | 0.300 | 0.000 | 32592.500 |
| jl2 | K7 | null11 | 48.900 | 0.000 | 32592.500 |
| jl2 | K7 | null12 | 0.000 | 0.000 | 32592.500 |
| jl2 | K7 | null13 | 8.500 | 0.000 | 32592.500 |
| jl2 | M7 | REAL | 60.100 | 23.500 | 42530.000 |
| jl2 | M7 | null11 | 41.300 | 20.900 | 42530.000 |
| jl2 | M7 | null12 | 63.800 | 14.000 | 42530.000 |
| jl2 | M7 | null13 | 18.000 | 4.400 | 42530.000 |
| jl2 | U7 | REAL | 245.400 | 40.300 | 42266.500 |
| jl2 | U7 | null11 | 149.600 | 27.500 | 42266.500 |
| jl2 | U7 | null12 | 60.200 | 25.900 | 42266.500 |
| jl2 | U7 | null13 | 90.100 | 0.000 | 42266.500 |
| jl2 | P7 | REAL | 27.700 | 6.900 | 36379.000 |
| jl2 | P7 | null11 | 99.000 | 5.100 | 36379.000 |
| jl2 | P7 | null12 | 49.100 | 9.000 | 36379.000 |
| jl2 | P7 | null13 | 153.000 | 0.000 | 36379.000 |
| jl2 | H7 | REAL | 33.200 | 23.600 | 35057.500 |
| jl2 | H7 | null11 | 23.000 | 8.500 | 35057.500 |
| jl2 | H7 | null12 | 50.300 | 6.900 | 35057.500 |
| jl2 | H7 | null13 | 0.000 | 17.800 | 35057.500 |
| jl2 | A7 | REAL | 49.800 | 19.100 | 7738.500 |
| jl2 | A7 | null13 | 0.000 | 0.000 | 5828.000 |
| raw | K7 | REAL | 134.400 | 0.000 | 83875.000 |
| raw | K7 | null11 | 10.500 | 3.000 | 83875.000 |
| raw | K7 | null12 | 60.000 | 0.000 | 83875.000 |
| raw | K7 | null13 | 116.300 | 0.000 | 83875.000 |
| raw | M7 | REAL | 166.300 | 40.200 | 108840.000 |
| raw | M7 | null11 | 78.900 | 1.400 | 108840.000 |
| raw | M7 | null12 | 47.800 | 4.900 | 108840.000 |
| raw | M7 | null13 | 120.600 | 10.600 | 108840.000 |
| raw | U7 | REAL | 207.200 | 25.800 | 90375.000 |
| raw | U7 | null11 | 53.800 | 10.100 | 90375.000 |
| raw | U7 | null12 | 42.800 | 4.500 | 90375.000 |
| raw | U7 | null13 | 105.100 | 11.500 | 90375.000 |
| raw | P7 | REAL | 366.600 | 7.500 | 234531.700 |
| raw | P7 | null11 | 137.900 | 22.100 | 234531.700 |
| raw | P7 | null12 | 217.200 | 4.900 | 234531.700 |
| raw | P7 | null13 | 68.400 | 24.900 | 234531.700 |
| raw | H7 | REAL | 133.500 | 29.400 | 75071.000 |
| raw | H7 | null11 | 82.800 | 12.400 | 75071.000 |
| raw | H7 | null12 | 41.900 | 17.400 | 75071.000 |
| raw | H7 | null13 | 29.600 | 15.100 | 75071.000 |
| raw | A7 | REAL | 120.700 | 31.200 | 8160.000 |

**4.8 EXACT ENGINE (JL2 stack, daily path, base lots, engine fee; $4.84 and x1.75 columns = d_mean repriced; positive ulcer_cut_pct = shallower; bootstrap = week-clustered, 2,000 resamples)**

| cell | window | d_mean_wk | d_mean_wk_484 | d_mean_wk_x175 | ulcer | ulcer_ref | ulcer_cut_pct | maxdd | maxdd_ref | worst_week | worst_week_ref | P_ulcer_lower | P_dd_shallower | P_ww_better |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TL3_RX_U7_bestdd | L3M | -3777 | -3759 | -6578 | 12841 | 9798 | -31.1 | -33946 | -22565 | -15620 | -13430 | 0.29 | 0.36 | 0.34 |
| TL3_RX_U7_bestdd | L6M | -1926 | -1924 | -3367 | 10043 | 8356 | -20.2 | -33946 | -22565 | -15620 | -13430 | 0.20 | 0.27 | 0.24 |
| TL3_RX_U7_bestdd | HOLD | 632 | 631 | 1104 | 24860 | 24530 | -1.3 | -74402 | -74402 | -31211 | -31211 | 0.40 | 0.42 | 0.50 |
| TL3_RX_U7_bestdd | GAP | -1330 | -1340 | -2345 | 26606 | 21125 | -25.9 | -72533 | -55206 | -49145 | -43527 | 0.13 | 0.11 | 0.08 |
| TL3_RX_U7_bestdd | PREUW | -222 | -224 | -393 | 24483 | 24609 | 0.5 | -70931 | -70931 | -28958 | -28958 | 0.47 | 0.51 | 0.39 |
| TL3_RX_U7_bestmean | L3M | 31 | 31 | 54 | 9804 | 9798 | -0.1 | -22565 | -22565 | -13430 | -13430 | 0.03 | 0.50 | 0.50 |
| TL3_RX_U7_bestmean | L6M | 315 | 313 | 548 | 8367 | 8356 | -0.1 | -22565 | -22565 | -13430 | -13430 | 0.13 | 0.50 | 0.50 |
| TL3_RX_U7_bestmean | HOLD | 205 | 206 | 360 | 24462 | 24530 | 0.3 | -74402 | -74402 | -31211 | -31211 | 0.90 | 0.70 | 0.51 |
| TL3_RX_U7_bestmean | GAP | 481 | 476 | 833 | 21223 | 21125 | -0.5 | -55206 | -55206 | -43527 | -43527 | 0.74 | 0.64 | 0.51 |
| TL3_RX_U7_bestmean | PREUW | 92 | 92 | 161 | 24604 | 24609 | 0.0 | -70931 | -70931 | -28958 | -28958 | 0.60 | 0.60 | 0.50 |
| TL3_RX_M7_bestdd | L3M | 316 | 316 | 553 | 9653 | 9798 | 1.5 | -22508 | -22565 | -13430 | -13430 | 0.63 | 0.70 | 0.62 |
| TL3_RX_M7_bestdd | L6M | 208 | 206 | 361 | 8239 | 8356 | 1.4 | -22508 | -22565 | -13430 | -13430 | 0.89 | 0.75 | 0.63 |
| TL3_RX_M7_bestdd | HOLD | -102 | -101 | -177 | 23936 | 24530 | 2.4 | -72249 | -74402 | -30852 | -31211 | 0.54 | 0.63 | 0.84 |
| TL3_RX_M7_bestdd | GAP | 525 | 521 | 912 | 19102 | 21125 | 9.6 | -47325 | -55206 | -40144 | -43527 | 0.98 | 0.99 | 1.00 |
| TL3_RX_M7_bestdd | PREUW | -408 | -410 | -718 | 24298 | 24609 | 1.3 | -68919 | -70931 | -28958 | -28958 | 0.34 | 0.49 | 0.39 |
| TL3_RX_M7_bestmean | L3M | 53 | 54 | 94 | 9816 | 9798 | -0.2 | -22807 | -22565 | -13430 | -13430 | 0.01 | 0.30 | 0.39 |
| TL3_RX_M7_bestmean | L6M | -88 | -89 | -155 | 8371 | 8356 | -0.2 | -22807 | -22565 | -13430 | -13430 | 0.02 | 0.32 | 0.39 |
| TL3_RX_M7_bestmean | HOLD | -114 | -113 | -198 | 24045 | 24530 | 2.0 | -72249 | -74402 | -30852 | -31211 | 0.53 | 0.65 | 0.85 |
| TL3_RX_M7_bestmean | GAP | 868 | 865 | 1513 | 19091 | 21125 | 9.6 | -48237 | -55206 | -40589 | -43527 | 0.99 | 0.99 | 1.00 |
| TL3_RX_M7_bestmean | PREUW | -325 | -326 | -571 | 24214 | 24609 | 1.6 | -68919 | -70931 | -28958 | -28958 | 0.39 | 0.48 | 0.39 |
| TL3_RX_H7_bestdd | L3M | -116 | -116 | -202 | 9798 | 9798 | 0.0 | -22565 | -22565 | -13430 | -13430 | 0.00 | 0.50 | 0.50 |
| TL3_RX_H7_bestdd | L6M | 94 | 95 | 165 | 8260 | 8356 | 1.2 | -22565 | -22565 | -13430 | -13430 | 0.13 | 0.50 | 0.50 |
| TL3_RX_H7_bestdd | HOLD | 414 | 415 | 727 | 24217 | 24530 | 1.3 | -74402 | -74402 | -31211 | -31211 | 0.97 | 0.87 | 0.63 |
| TL3_RX_H7_bestdd | GAP | -361 | -361 | -632 | 21182 | 21125 | -0.3 | -55206 | -55206 | -43527 | -43527 | 0.00 | 0.35 | 0.49 |
| TL3_RX_H7_bestdd | PREUW | -38 | -38 | -67 | 24609 | 24609 | 0.0 | -70931 | -70931 | -28958 | -28958 | 0.32 | 0.53 | 0.50 |
| TL3_RX_H7_bestmean | L3M | 0 | 0 | 0 | 9798 | 9798 | 0.0 | -22565 | -22565 | -13430 | -13430 | 0.00 | 0.50 | 0.50 |
| TL3_RX_H7_bestmean | L6M | -25 | -25 | -44 | 8314 | 8356 | 0.5 | -22565 | -22565 | -13430 | -13430 | 0.12 | 0.51 | 0.50 |
| TL3_RX_H7_bestmean | HOLD | 279 | 279 | 488 | 24269 | 24530 | 1.1 | -74402 | -74402 | -31211 | -31211 | 0.73 | 0.58 | 0.51 |
| TL3_RX_H7_bestmean | GAP | 24 | 24 | 42 | 21125 | 21125 | 0.0 | -55206 | -55206 | -43527 | -43527 | 0.20 | 0.52 | 0.50 |
| TL3_RX_H7_bestmean | PREUW | 0 | 0 | 0 | 24609 | 24609 | 0.0 | -70931 | -70931 | -28958 | -28958 | 0.00 | 0.50 | 0.50 |
| TL3_RX_A7_bestdd | L3M | -814 | -824 | -1442 | 10435 | 9798 | -6.5 | -23449 | -22565 | -12321 | -13430 | 0.66 | 0.79 | 0.84 |
| TL3_RX_A7_bestdd | L6M | -439 | -443 | -775 | 8824 | 8356 | -5.6 | -23449 | -22565 | -12321 | -13430 | 0.66 | 0.76 | 0.82 |
| TL3_RX_A7_bestdd | HOLD | 0 | 0 | 0 | 24530 | 24530 | 0.0 | -74402 | -74402 | -31211 | -31211 | 0.03 | 0.51 | 0.50 |
| TL3_RX_A7_bestdd | GAP | 41 | 39 | 69 | 21451 | 21125 | -1.5 | -56535 | -55206 | -44459 | -43527 | 0.40 | 0.41 | 0.22 |
| TL3_RX_A7_bestdd | PREUW | 41 | 41 | 71 | 25105 | 24609 | -2.0 | -70931 | -70931 | -28958 | -28958 | 0.71 | 0.61 | 0.50 |
| TL3_RX_A7_bestmean | L3M | 1632 | 1615 | 2827 | 9313 | 9798 | 5.0 | -22565 | -22565 | -11721 | -13430 | 0.73 | 0.81 | 0.84 |
| TL3_RX_A7_bestmean | L6M | 770 | 762 | 1333 | 8114 | 8356 | 2.9 | -22565 | -22565 | -11721 | -13430 | 0.73 | 0.77 | 0.83 |
| TL3_RX_A7_bestmean | HOLD | 0 | 0 | 0 | 24530 | 24530 | 0.0 | -74402 | -74402 | -31211 | -31211 | 0.05 | 0.51 | 0.50 |
| TL3_RX_A7_bestmean | GAP | -845 | -847 | -1482 | 21637 | 21125 | -2.4 | -64890 | -55206 | -39817 | -43527 | 0.39 | 0.51 | 0.71 |
| TL3_RX_A7_bestmean | PREUW | -117 | -120 | -211 | 23646 | 24609 | 3.9 | -70931 | -70931 | -28958 | -28958 | 0.40 | 0.46 | 0.50 |

**Family tests over the 8 engine cells (N_engine 8, N_total 288 = the 72-variant searches of 4 books)**

| window | weeks | mean_RC_p | mean_SPA_p | mean_winner | tail_RC_p | tail_SPA_p | DSR_N8 | DSR_N288 |
|--|--|--|--|--|--|--|--|--|
| L6M | 27 | 0.348 | 0.249 | TL3_RX_A7_bestmean | 0.480 | 0.097 | 0.281 | 0.006 |
| HOLD | 26 | 0.220 | 0.154 | TL3_RX_U7_bestdd | 0.125 | 0.194 | 0.165 | 0.002 |
| ALL | 162 | 0.674 | 0.413 | TL3_RX_U7_bestmean | 0.537 | 0.330 | 0.372 | 0.036 |

**Ulcer-tier scoring against engine random-exit controls:** TL3_RX_U7_bestdd: NOT FINISHED (recent months landed 1 of 12)


**D, engine verdict (section 4.8).** The exit schedules of the best-by-mean and best-by-DD variants for JL2 U7 / M7 / H7 / A7 were run on the exact engine (set base TL3_EV_JN05W2JL2 + hook code/th_rexit_hook/rx_hooks.py, cells TL3_RX_<book>_<pick>, all 43 months; the 6 months before 2023-10 have no schedule and are copies of JL2, identity proved by TL3_RX_ID 202610). Engine mechanics differ from the path arithmetic (real stack lots, latency, slip, path dependence: other books and later entries move), which is why the engine verdict is the one that counts. Engine-exact random-exit controls (X family: pc_hooks rx draws with the real share and minutes / open-profit pairs; tighten / half families: random schedules from the same rows with the same share and template distribution; 30 draws each, 12 months L6M + HOLD) are queued on server 2 as TL3_RX_C_*; the ulcer-tier scoring (code/th_rexit_hook/rx_score.py) runs when they have landed. Interim result (no controls needed): see 4.8.
Part E reading (4.5, 4.6): the best-by-mean variants earn their small gain on winners that gave it back (e.g. JL2 P7 +$143k over the out-of-sample span, +$646 per action) and on trades already cut by the loss lines (+$52k) and lose it on the 'other' trades (-$200k): the same signal that rescues a give-back also exits trades that would have run, so the net is about zero. Losers that never went green are 5-10% of trades and the gains there are +$1-9k per book. HOLD 2025-11-17..12-10: the best-by-mean variant fires on 0-14 trades per book, net -$1.0k to +$11.0k, DD effects within a few % (14-167 trades per book).
## 5. Status, files, what is next
Code: code/th_rexit (build_grid.py, add_z.py, features.py, conds.py, build_rows.py, run_all.py, c12lib.py, c1.py, c2.py, c2_fine.py, c1_plant.py, c3.py, c3_eval.py, c3_ctl.py, c3_e.py, tape5s.py, tape5s_eval.py, page.py). Results: /mnt/l2/l2vast/_rexit/res (c1_*.parquet, c2_*.parquet, null*_c*.parquet, c3/ and c3_*.json). Re-run when more raw months land: run_all.py raw (idempotent), then run_c12.sh raw, then page.py.
