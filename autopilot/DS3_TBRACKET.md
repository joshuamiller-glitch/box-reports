# DS3 T-BRACKET-PM section A (D3BA): bracket shape on ST, HM, KB, SM, EM - INTERIM (2026-10-27 03:58Z)

**STATUS: INTERIM.** The DIRECT L2 replay of the 21 stage-1 cells is running (months done: 20/45; the box memory governor throttles replay workers). Everything below marked MAPPED is a screen on the year x exit-type mapped table, which the directive allows only as a screen, and which we show to be biased for non-60-pt brackets (random-time-entry placebos reproduce the same negative drift). No stage-1 verdict is issued on the mapped basis; the verdict column is the V2 reading of the mapped screen and is NOT a verdict of record. A driver (code/ba/ba_driver.sh) re-scores on the direct basis when the replay completes and rewrites this file.

**Mapped screen (stage 1): {'DEAD': 21}; not a verdict of record.**

## 1. What was run
- Prereg stage 1: l2vast/ds3/prereg/BA_stage1_prereg.md, sha256 bb08c97608fe426afb384ea79883a8fbfe66e4d34caa558ddf2a02e5e763d5f3 (21 cells: Set A target {20,30,40,45,50} x stop {60,75,90} = 15, plus KB/SM/EM target {30,40} stop 60 = 6). Stage 2: ten preregs l2vast/ds3/prereg/BA_S2_<E><a|b>_prereg.md (sha256 in autopilot/DECISIONS.md), 9 targets {20,30,40,45,50,60,75,90,120} x 6 stops {40,50,60,75,90,structure} per entry minus the 60/60 base = 53 cells per entry (26 + 27), 265 cells. Ledger: 21 + 265 = 286 cells counted (trials.jsonl tracks DS3_BA_S1, DS3_BA_S2_*). Holdout look logged once (track DS3_BA, pre-holdout text autopilot/DS3_TBRACKET_PREHOLD.md).
- Entries: Set A (ST+HM 14/14 live locks, stage 1), ST10 / HM10 (single-book 10-lot DS2 books, stage 2), KB = TE7_kelt3m_n14_m1.0, SM = TE6_st10m_n7_m3.0, EM = TE7_emax5m_f30_s50 (10 lots, per-book locks). The registry is l2vast/ds3/out/BRACKET_ENTRIES.json; per the tier-1 order only these five entries are run.
- Rows: the 1-s path bracket sim (firmlib.sim_rrt, busy logic) per cell; identical entries = same (book, entry bar, side) as the 60/60 base; trades that appear/disappear because the busy interval changes are in the full-sequence weekly but not in the paired mean (counts: n_new_vs_base, n_dropped_vs_base per cell in rows). Pricing basis: DIRECT = exec_engine_l2 replay of S14x1_g2 slices (10 slices for KB/SM/EM) with OCO stop/target ticks from each fill + XJ3 stop-join on EM stop triggers (code/ba/ba_replay.py, templates t4_replay/te_direct); MAPPED = year x exit-type table.
- Lock-dollar convention: the live DualStrat.cs per-book day-loss limit is a FIXED DOLLAR input (19,200), not scaled by lots or stop; primary runs keep dollar lock values at the live Set A values (rscale 1; KB/SM/EM at their 10-lot R = $12,000 values) with lots fixed as in Set A, so dollar risk per trade scales with the stop. Sensitivities per cell: R-scaled locks (R = lots x stop x $20) and constant-dollar-risk lots (60/stop), columns in table 3. Set A rebuilt through the same pipeline reproduces WF $24,980/wk, SD 104,523, maxDD 401,318 (official 24,975 / 104,523 / 401,293).
- Cost model of the hurdle: required win rate = (stop + cost_pts)/(target + stop) with cost_pts = $4.84 RT/$20 per point (0.242) minus the exit-type execution correction (stop-join 1.01 pt, market 0.995 pt, entry-slice cost inside the corrected-P9 mapping) averaged over the cell trades; observed win = net P&L after cost > 0; the gap CI is a session-block bootstrap.
- Sessions: firmlib convention, entry time ASIA 18:00-02:00, LONDON 02:00-09:30, NY 09:30-15:00 ET. Quiet/wide = trailing 60-minute range at entry below/above its median. 2x cost: execution correction and commission doubled.
- Replay identity (2024-03, base bracket replayed with the stage-1 machinery vs corrected P9): 198 trades, median difference 0.00 pt, 79% within 0.26 pt, mean -0.21 pt/trade, SD 5.2 pt (tails -38..+24). Paired deltas vs the P9 base therefore carry a method residual of about -0.2 pt/trade; a replayed-base run (code/ba, cells *_t60_s60) is queued to remove it.

## 2. Prediction (before scoring) and MDE
In a driftless gross path a 1R-fixed bracket has zero gross edge, so the change is cost-driven: fewer stop-joins (1.01 pt) with a tighter target or wider stop gives a small POSITIVE (+0.05 to +0.30 pt/trade, flat-cost model); the mapped table gives large negative numbers because its target correction (-4 pt in 2025-26) is specific to the 60-pt bracket. Both are below the trade-level MDE of 0.6-2.4 pt/trade (bootstrap MDE in the tables), i.e. none of these cells could show its predicted effect. Weekly MDE for a Set A difference series is about $15-25k/wk.

## 3. Stage 1 results (MAPPED (screen only))
| cell | n trades | trades/wk | cost pt | required win | observed win [gap CI] | avg win / avg loss (pts) | P(tgt)/P(stop)/P(time) |
|--|--|--|--|--|--|--|--|
| A_t20_s60 | 24089 | 124.2 | 2.05 | 0.776 | 0.758 (-0.018) [-0.02, -0.01] | 16.5 / -56.4 | 0.76/0.23/0.01 |
| A_t30_s60 | 20380 | 105.1 | 1.59 | 0.684 | 0.677 (-0.007) [-0.01, 0.00] | 26.4 / -56.2 | 0.67/0.31/0.02 |
| A_t40_s60 | 17857 | 92.0 | 1.21 | 0.612 | 0.612 (-0.000) [-0.01, 0.01] | 36.2 / -56.0 | 0.60/0.37/0.02 |
| A_t45_s60 | 16879 | 87.0 | 1.04 | 0.581 | 0.583 (+0.001) [-0.01, 0.01] | 41.0 / -55.9 | 0.57/0.40/0.03 |
| A_t50_s60 | 16041 | 82.7 | 0.88 | 0.553 | 0.557 (+0.003) [-0.01, 0.01] | 45.8 / -55.8 | 0.54/0.42/0.03 |
| A_t20_s75 | 22078 | 113.8 | 2.28 | 0.813 | 0.793 (-0.020) [-0.03, -0.01] | 16.5 / -69.8 | 0.79/0.19/0.01 |
| A_t30_s75 | 18469 | 95.2 | 1.87 | 0.732 | 0.718 (-0.014) [-0.02, -0.01] | 26.4 / -69.5 | 0.71/0.26/0.02 |
| A_t40_s75 | 16078 | 82.9 | 1.53 | 0.665 | 0.658 (-0.007) [-0.02, 0.00] | 36.1 / -69.2 | 0.65/0.32/0.03 |
| A_t45_s75 | 15116 | 77.9 | 1.35 | 0.636 | 0.628 (-0.008) [-0.02, 0.00] | 40.9 / -69.1 | 0.62/0.34/0.04 |
| A_t50_s75 | 14284 | 73.6 | 1.20 | 0.610 | 0.602 (-0.008) [-0.02, 0.00] | 45.7 / -68.9 | 0.59/0.37/0.04 |
| A_t20_s90 | 20662 | 106.5 | 2.45 | 0.840 | 0.818 (-0.023) [-0.03, -0.02] | 16.5 / -82.5 | 0.82/0.17/0.02 |
| A_t30_s90 | 17045 | 87.9 | 2.06 | 0.767 | 0.747 (-0.020) [-0.03, -0.01] | 26.4 / -82.2 | 0.74/0.23/0.03 |
| A_t40_s90 | 14758 | 76.1 | 1.76 | 0.706 | 0.690 (-0.015) [-0.02, -0.01] | 36.1 / -81.8 | 0.68/0.28/0.04 |
| A_t45_s90 | 13830 | 71.3 | 1.60 | 0.678 | 0.663 (-0.016) [-0.02, -0.01] | 40.9 / -81.7 | 0.65/0.30/0.05 |
| A_t50_s90 | 13047 | 67.3 | 1.45 | 0.653 | 0.637 (-0.016) [-0.03, -0.01] | 45.7 / -81.5 | 0.62/0.32/0.05 |
| KB_t30_s60 | 12769 | 65.8 | 1.58 | 0.684 | 0.677 (-0.007) [-0.02, 0.00] | 26.4 / -56.1 | 0.67/0.31/0.02 |
| KB_t40_s60 | 10888 | 56.1 | 1.17 | 0.612 | 0.608 (-0.003) [-0.01, 0.01] | 36.1 / -56.0 | 0.60/0.38/0.02 |
| SM_t30_s60 | 2651 | 13.7 | 1.59 | 0.684 | 0.688 (+0.004) [-0.01, 0.02] | 26.6 / -56.7 | 0.68/0.30/0.02 |
| SM_t40_s60 | 2551 | 13.1 | 1.29 | 0.613 | 0.630 (+0.017) [-0.00, 0.04] | 36.4 / -56.6 | 0.62/0.36/0.02 |
| EM_t30_s60 | 2585 | 13.3 | 1.66 | 0.685 | 0.692 (+0.007) [-0.01, 0.02] | 26.6 / -56.1 | 0.69/0.29/0.02 |
| EM_t40_s60 | 2472 | 12.7 | 1.32 | 0.613 | 0.628 (+0.015) [-0.00, 0.03] | 36.4 / -56.1 | 0.62/0.35/0.03 |

| cell | paired pts/trade WF [CI] | MDE | n pairs | PRE | HOLD | SPAN2 (2023-04..24-01) | 2x cost | placebo rank (raw / recentred) | neighbours | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| A_t20_s60 | -2.70 [-3.64, -1.76] | 1.35 | 12045 | -2.41 | -2.91 | -0.23 | -4.40 | nan / nan | agree | DEAD |
| A_t30_s60 | -1.69 [-2.53, -0.88] | 1.21 | 11833 | -1.53 | -1.81 | -0.03 | -2.85 | nan / nan | agree | DEAD |
| A_t40_s60 | -1.14 [-1.79, -0.53] | 0.93 | 11520 | -1.18 | -1.10 | +0.25 | -1.83 | nan / nan | agree | DEAD |
| A_t45_s60 | -0.84 [-1.36, -0.33] | 0.73 | 11487 | -0.99 | -0.74 | -0.78 | -1.34 | nan / nan | agree | DEAD |
| A_t50_s60 | -0.54 [-0.95, -0.14] | 0.59 | 11652 | -0.76 | -0.38 | -0.17 | -0.85 | nan / nan | agree | DEAD |
| A_t20_s75 | -3.26 [-4.26, -2.31] | 1.38 | 11133 | -3.00 | -3.46 | -0.20 | -5.21 | nan / nan | agree | DEAD |
| A_t30_s75 | -2.19 [-3.09, -1.28] | 1.29 | 10676 | -2.08 | -2.26 | -0.14 | -3.65 | nan / nan | agree | DEAD |
| A_t40_s75 | -1.60 [-2.41, -0.82] | 1.11 | 10138 | -1.54 | -1.65 | +0.73 | -2.65 | nan / nan | agree | DEAD |
| A_t45_s75 | -1.29 [-2.02, -0.54] | 1.07 | 9975 | -1.52 | -1.12 | -0.46 | -2.15 | nan / nan | agree | DEAD |
| A_t50_s75 | -1.10 [-1.76, -0.43] | 0.97 | 9942 | -1.27 | -0.98 | -0.38 | -1.78 | nan / nan | agree | DEAD |
| A_t20_s90 | -3.54 [-4.58, -2.48] | 1.51 | 10524 | -3.01 | -3.92 | -0.42 | -5.66 | nan / nan | agree | DEAD |
| A_t30_s90 | -2.58 [-3.56, -1.50] | 1.46 | 9952 | -2.10 | -2.92 | -0.79 | -4.26 | nan / nan | agree | DEAD |
| A_t40_s90 | -1.86 [-2.76, -0.84] | 1.36 | 9326 | -1.39 | -2.19 | -0.53 | -3.18 | nan / nan | agree | DEAD |
| A_t45_s90 | -1.60 [-2.46, -0.70] | 1.29 | 9126 | -1.52 | -1.67 | -1.95 | -2.75 | nan / nan | agree | DEAD |
| A_t50_s90 | -1.41 [-2.24, -0.59] | 1.21 | 9046 | -1.45 | -1.39 | -1.74 | -2.39 | nan / nan | agree | DEAD |
| KB_t30_s60 | -1.85 [-2.73, -0.95] | 1.32 | 6802 | -1.90 | -1.81 | +0.94 | -2.99 | 0.05 / 0.00 | agree | DEAD |
| KB_t40_s60 | -0.78 [-1.54, -0.06] | 1.07 | 6434 | -0.87 | -0.72 | -0.13 | -1.50 | 0.30 / 0.00 | agree | DEAD |
| SM_t30_s60 | -2.72 [-4.42, -1.09] | 2.46 | 1873 | -2.94 | -2.52 | +2.28 | -3.78 | nan / nan | agree | DEAD |
| SM_t40_s60 | -0.82 [-2.36, +0.57] | 2.12 | 1872 | -0.92 | -0.72 | +1.57 | -1.50 | nan / nan | agree | DEAD |
| EM_t30_s60 | -1.51 [-3.31, +0.22] | 2.56 | 1830 | -1.95 | -1.12 | -0.23 | -2.69 | nan / nan | agree | DEAD |
| EM_t40_s60 | -0.48 [-1.96, +0.94] | 2.12 | 1830 | -0.01 | -0.91 | -0.15 | -1.21 | nan / nan | agree | DEAD |

| cell | WF mean $/wk | SD | maxDD | d mean vs base | d SD | d maxDD | CI of d mean | 2x d mean | HOLD d mean | SPAN2 d mean | R-scaled locks WF mean | const-risk lots WF mean (peak lots) | peak lots |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| A_t20_s60 | -30,760 | 85,425 | 4,426,661 | -60,686 | -22,394 | 3,977,534 | [-78,036, -44,209] | -98,091 | -76,520 | -30,965 | -30,760 | -30,760 (28) | 28 |
| A_t30_s60 | 152 | 100,643 | 1,038,204 | -29,774 | -7,177 | 589,077 | [-46,098, -13,574] | -56,028 | -30,996 | -24,178 | 152 | 152 (28) | 28 |
| A_t40_s60 | 8,587 | 96,748 | 587,778 | -21,338 | -11,072 | 138,651 | [-35,627, -8,010] | -28,967 | -22,046 | -4,682 | 8,587 | 8,587 (28) | 28 |
| A_t45_s60 | 6,176 | 98,074 | 689,627 | -23,749 | -9,745 | 240,501 | [-36,467, -11,693] | -29,486 | -27,689 | -10,736 | 6,176 | 6,176 (28) | 28 |
| A_t50_s60 | 10,157 | 106,543 | 599,485 | -19,768 | -1,277 | 150,358 | [-32,449, -7,345] | -19,742 | -20,299 | -13,778 | 10,157 | 10,157 (28) | 28 |
| A_t20_s75 | -33,048 | 90,932 | 4,933,999 | -62,974 | -16,888 | 4,484,872 | [-81,094, -44,517] | -92,259 | -79,957 | -33,558 | -37,683 | -27,269 (22) | 28 |
| A_t30_s75 | -5,003 | 102,934 | 1,776,551 | -34,928 | -4,886 | 1,327,424 | [-50,836, -19,016] | -60,294 | -48,286 | -24,823 | -15,798 | -8,970 (22) | 28 |
| A_t40_s75 | 810 | 103,246 | 1,292,907 | -29,116 | -4,574 | 843,780 | [-46,187, -13,650] | -38,668 | -33,912 | -7,461 | -4,540 | -1,598 (22) | 28 |
| A_t45_s75 | -4,721 | 102,151 | 1,510,551 | -34,647 | -5,669 | 1,061,424 | [-51,041, -19,116] | -39,753 | -43,687 | -12,977 | -2,368 | -686 (22) | 28 |
| A_t50_s75 | -3,320 | 103,966 | 1,302,967 | -33,245 | -3,854 | 853,840 | [-49,049, -16,752] | -36,969 | -35,811 | -16,689 | 122 | 1,221 (22) | 28 |
| A_t20_s90 | -28,597 | 88,208 | 4,535,804 | -58,522 | -19,612 | 4,086,678 | [-77,270, -41,236] | -95,073 | -65,351 | -41,900 | -38,329 | -21,707 (19) | 28 |
| A_t30_s90 | -11,396 | 104,490 | 2,797,722 | -41,321 | -3,329 | 2,348,595 | [-58,912, -22,771] | -63,647 | -52,237 | -34,304 | -25,051 | -12,965 (19) | 28 |
| A_t40_s90 | 807 | 98,984 | 1,450,177 | -29,118 | -8,836 | 1,001,050 | [-45,585, -11,712] | -43,273 | -32,139 | -25,458 | -4,252 | 861 (19) | 28 |
| A_t45_s90 | -3,838 | 103,974 | 1,882,926 | -33,764 | -3,845 | 1,433,799 | [-51,224, -16,452] | -45,844 | -38,959 | -27,675 | -2,024 | -406 (19) | 28 |
| A_t50_s90 | -9,136 | 100,149 | 2,166,109 | -39,061 | -7,670 | 1,716,982 | [-54,945, -22,248] | -39,749 | -43,668 | -21,129 | -3,306 | -852 (19) | 28 |
| KB_t30_s60 | 5,144 | 49,440 | 525,071 | -11,088 | -9,661 | 147,379 | [-20,193, -1,557] | -27,657 | -13,198 | 4,723 | 5,144 | 5,144 (10) | 10 |
| KB_t40_s60 | 12,102 | 46,944 | 379,629 | -4,130 | -12,156 | 1,937 | [-13,504, 5,004] | -13,052 | -4,236 | -2,863 | 12,102 | 12,102 (10) | 10 |
| SM_t30_s60 | 1,989 | 28,649 | 167,938 | -7,148 | -7,411 | -24,179 | [-11,524, -2,381] | -10,114 | -8,140 | -2,341 | 1,989 | 1,989 (10) | 10 |
| SM_t40_s60 | 5,861 | 30,297 | 155,150 | -3,277 | -5,764 | -36,967 | [-6,911, 559] | -4,857 | -3,763 | -1,077 | 5,861 | 5,861 (10) | 10 |
| EM_t30_s60 | 4,530 | 25,573 | 214,135 | -3,217 | -8,962 | 41,576 | [-8,607, 2,172] | -6,361 | -2,712 | -3,007 | 4,530 | 4,530 (10) | 10 |
| EM_t40_s60 | 7,610 | 28,712 | 192,927 | -137 | -5,823 | 20,368 | [-4,837, 4,302] | -2,161 | -1,539 | -2,016 | 7,610 | 7,610 (10) | 10 |

| cell | ASIA pts [CI] (n) | LONDON | NY | ASIA hurdle req/obs | LONDON | NY | LONG | SHORT | QUIET | WIDE |
|--|--|--|--|--|--|--|--|--|--|--|
| A_t20_s60 | -3.00 [-4.94, -1.03] (5418) | -1.76 [-3.69, +0.12] (6387) | -3.07 [-4.44, -1.78] (8053) | 0.78/0.78 | 0.78/0.75 | 0.78/0.75 | -1.93 [-3.21, -0.53] | -3.42 [-4.69, -2.17] | -3.21 [-4.57, -1.79] | -2.27 [-3.38, -1.04] |
| A_t30_s60 | -2.00 [-3.66, -0.41] (4573) | -1.49 [-3.01, +0.12] (5203) | -1.63 [-2.84, -0.43] (7201) | 0.69/0.70 | 0.68/0.67 | 0.68/0.68 | -0.79 [-1.98, +0.39] | -2.53 [-3.63, -1.39] | -2.35 [-3.48, -1.24] | -1.14 [-2.30, -0.08] |
| A_t40_s60 | -1.76 [-3.06, -0.55] (4031) | -0.72 [-2.00, +0.66] (4422) | -1.00 [-2.01, -0.01] (6535) | 0.61/0.63 | 0.61/0.61 | 0.61/0.61 | -0.28 [-1.25, +0.65] | -1.93 [-2.76, -1.14] | -1.58 [-2.45, -0.58] | -0.76 [-1.66, +0.12] |
| A_t45_s60 | -1.34 [-2.42, -0.33] (3832) | -0.68 [-1.77, +0.40] (4121) | -0.64 [-1.41, +0.14] (6266) | 0.58/0.60 | 0.58/0.58 | 0.58/0.58 | -0.14 [-0.90, +0.65] | -1.49 [-2.21, -0.80] | -1.08 [-1.88, -0.29] | -0.65 [-1.38, +0.13] |
| A_t50_s60 | -0.90 [-1.73, -0.09] (3656) | -0.44 [-1.21, +0.48] (3860) | -0.39 [-1.00, +0.28] (6001) | 0.55/0.57 | 0.55/0.55 | 0.55/0.56 | +0.22 [-0.50, +0.89] | -1.25 [-1.80, -0.68] | -0.51 [-1.12, +0.14] | -0.57 [-1.13, -0.01] |
| A_t20_s75 | -3.60 [-5.79, -1.59] (5092) | -2.93 [-4.87, -0.93] (5705) | -3.25 [-4.59, -1.79] (7483) | 0.82/0.81 | 0.81/0.79 | 0.82/0.79 | -2.62 [-4.04, -1.21] | -3.87 [-5.14, -2.48] | -3.99 [-5.54, -2.50] | -2.64 [-3.97, -1.39] |
| A_t30_s75 | -2.88 [-4.76, -1.07] (4265) | -2.64 [-4.55, -0.94] (4589) | -1.53 [-2.89, -0.36] (6614) | 0.73/0.73 | 0.73/0.71 | 0.73/0.72 | -1.47 [-2.70, -0.29] | -2.85 [-4.11, -1.55] | -2.98 [-4.31, -1.63] | -1.51 [-2.82, -0.24] |
| A_t40_s75 | -2.47 [-4.14, -0.86] (3741) | -1.95 [-3.67, -0.29] (3882) | -0.90 [-1.99, +0.26] (5931) | 0.67/0.67 | 0.67/0.65 | 0.67/0.66 | -1.03 [-2.18, +0.22] | -2.14 [-3.20, -1.01] | -2.05 [-3.17, -0.90] | -1.22 [-2.35, -0.06] |
| A_t45_s75 | -2.04 [-3.58, -0.56] (3541) | -1.81 [-3.17, -0.28] (3593) | -0.58 [-1.64, +0.49] (5654) | 0.64/0.64 | 0.64/0.62 | 0.64/0.63 | -0.84 [-1.90, +0.19] | -1.71 [-2.77, -0.68] | -1.41 [-2.49, -0.39] | -1.19 [-2.19, -0.15] |
| A_t50_s75 | -1.36 [-2.71, -0.01] (3362) | -1.69 [-3.16, -0.26] (3341) | -0.64 [-1.63, +0.33] (5385) | 0.61/0.62 | 0.61/0.59 | 0.61/0.60 | -0.65 [-1.56, +0.32] | -1.52 [-2.49, -0.60] | -0.87 [-1.96, +0.11] | -1.29 [-2.18, -0.37] |
| A_t20_s90 | -4.49 [-6.67, -2.43] (4900) | -3.31 [-5.43, -1.13] (5235) | -3.08 [-4.62, -1.58] (7032) | 0.84/0.83 | 0.84/0.82 | 0.84/0.82 | -3.09 [-4.59, -1.50] | -3.95 [-5.42, -2.52] | -4.46 [-5.93, -2.91] | -2.75 [-4.14, -1.39] |
| A_t30_s90 | -4.06 [-6.05, -2.06] (4045) | -2.89 [-4.94, -0.79] (4126) | -1.51 [-3.01, -0.00] (6130) | 0.77/0.76 | 0.77/0.75 | 0.77/0.75 | -2.11 [-3.48, -0.65] | -3.01 [-4.39, -1.64] | -3.56 [-5.07, -2.08] | -1.74 [-3.06, -0.33] |
| A_t40_s90 | -3.35 [-5.35, -1.45] (3515) | -2.14 [-3.94, -0.06] (3460) | -0.81 [-2.05, +0.48] (5470) | 0.71/0.70 | 0.71/0.69 | 0.71/0.69 | -1.41 [-2.85, -0.12] | -2.28 [-3.47, -0.84] | -2.71 [-3.99, -1.34] | -1.14 [-2.33, +0.17] |
| A_t45_s90 | -3.14 [-5.06, -1.27] (3320) | -1.83 [-3.74, +0.25] (3202) | -0.55 [-1.83, +0.73] (5189) | 0.68/0.68 | 0.68/0.67 | 0.68/0.66 | -1.65 [-3.02, -0.36] | -1.56 [-2.87, -0.21] | -2.31 [-3.62, -0.97] | -1.00 [-2.30, +0.14] |
| A_t50_s90 | -2.07 [-3.91, -0.28] (3166) | -1.81 [-3.52, +0.11] (2958) | -0.81 [-2.01, +0.43] (4927) | 0.65/0.66 | 0.65/0.63 | 0.65/0.64 | -1.44 [-2.70, -0.16] | -1.39 [-2.62, -0.10] | -1.42 [-2.77, -0.07] | -1.41 [-2.60, -0.18] |
| KB_t30_s60 | -2.55 [-4.35, -0.80] (2944) | -1.49 [-3.56, +0.40] (3059) | -1.63 [-2.86, -0.25] (4758) | 0.69/0.70 | 0.68/0.68 | 0.68/0.66 | -2.06 [-3.42, -0.79] | -1.63 [-2.99, -0.20] | -1.67 [-3.10, -0.26] | -2.00 [-3.26, -0.60] |
| KB_t40_s60 | -1.29 [-2.81, +0.06] (2494) | -0.13 [-1.80, +1.66] (2541) | -0.81 [-1.88, +0.27] (4211) | 0.61/0.64 | 0.61/0.60 | 0.61/0.60 | -0.40 [-1.48, +0.74] | -1.18 [-2.21, -0.03] | -0.68 [-1.76, +0.51] | -0.87 [-1.96, +0.25] |
| SM_t30_s60 | -2.46 [-5.95, +1.07] (593) | -1.55 [-4.62, +1.33] (793) | -4.23 [-7.06, -1.31] (651) | 0.69/0.72 | 0.68/0.69 | 0.68/0.66 | -3.94 [-6.41, -1.64] | -1.55 [-3.99, +0.97] | -1.53 [-4.17, +1.23] | -3.68 [-5.99, -1.23] |
| SM_t40_s60 | -0.43 [-3.34, +2.67] (582) | -0.48 [-2.93, +2.11] (752) | -1.53 [-3.92, +0.91] (644) | 0.61/0.66 | 0.61/0.63 | 0.61/0.62 | -1.95 [-3.83, +0.08] | +0.28 [-1.86, +2.48] | +0.15 [-2.08, +2.48] | -1.58 [-3.43, +0.58] |
| EM_t30_s60 | -1.72 [-4.95, +1.63] (626) | -2.04 [-5.15, +0.74] (696) | -0.83 [-3.87, +2.37] (667) | 0.69/0.71 | 0.69/0.71 | 0.69/0.69 | -1.89 [-4.55, +0.46] | -1.17 [-3.55, +1.21] | -2.16 [-4.90, +0.46] | -0.98 [-3.46, +1.60] |
| EM_t40_s60 | -0.24 [-2.95, +2.65] (614) | -1.30 [-3.69, +1.09] (655) | +0.07 [-2.25, +2.58] (655) | 0.61/0.65 | 0.61/0.64 | 0.61/0.63 | -0.70 [-2.86, +1.25] | -0.28 [-2.40, +1.77] | -0.39 [-2.64, +2.03] | -0.56 [-2.49, +1.44] |

## 4. Nulls and caveats
- Placebo: same bracket on random-time entries (hour/side matched, 20 draws, mapped basis, paired vs the 60/60 base on identical random entries). The null mean is itself negative in the mapped basis (bias), so the recentred rank is reported next to the raw rank.
- Label permutation of brackets across trades leaves the paired mean invariant and is not informative for the mean.
- D3NT overlap: targets 45/50 (and 40) are a shorter fixed target, conceptually the near-target "fixed target 55/57" comparison; same rule family, not re-tested under another name. Nearest scored cells: FAILPRED STEP2 C1/C2 (bracket x0.5, DEAD), STRUCT48 T1.4 (direction-asymmetric stop/target; short stop 50 nearest miss), T4/SO2/HB.

## 5. Stage 2
Preregistered (10 preregs, 265 cells, ledger counted); scoring waits for the stage-1 direct replay because the calibrated-mapped screen is calibrated on it.
