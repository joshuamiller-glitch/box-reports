# DS3 T-BRACKET-PM section A (D3BA): bracket shape on ST, HM, KB, SM, EM - FINAL (2026-10-28 00:51Z)

**STATUS: FINAL for stage 1 (direct basis). Stage 2 (54-cell grids per entry) is a calibrated-mapped screen; cells not replayed directly are SCREENED, not PASS/CANDIDATE.**

**Verdict line (stage 1, DIRECT): {'DEAD': 21}.** No bracket shape is a PASS or CANDIDATE where the paired CI excludes zero upward; see tables.

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

## 3. Stage 1 results (DIRECT)
| cell | n trades | trades/wk | cost pt | required win | observed win [gap CI] | avg win / avg loss (pts) | P(tgt)/P(stop)/P(time) |
|--|--|--|--|--|--|--|--|
| A_t20_s60 | 24089 | 124.2 | 0.76 | 0.759 | 0.735 (-0.025) [-0.03, -0.02] | 18.6 / -50.7 | 0.76/0.23/0.01 |
| A_t30_s60 | 20380 | 105.1 | 0.80 | 0.676 | 0.665 (-0.011) [-0.02, -0.00] | 27.9 / -53.6 | 0.67/0.31/0.02 |
| A_t40_s60 | 17857 | 92.0 | 0.66 | 0.607 | 0.605 (-0.001) [-0.01, 0.01] | 37.3 / -54.7 | 0.60/0.37/0.02 |
| A_t45_s60 | 16879 | 87.0 | 0.66 | 0.578 | 0.578 (+0.000) [-0.01, 0.01] | 41.9 / -55.1 | 0.57/0.40/0.03 |
| A_t50_s60 | 16041 | 82.7 | 0.61 | 0.551 | 0.554 (+0.003) [-0.01, 0.01] | 46.4 / -55.4 | 0.54/0.42/0.03 |
| A_t20_s75 | 22078 | 113.8 | 0.74 | 0.797 | 0.770 (-0.028) [-0.03, -0.02] | 18.6 / -61.3 | 0.79/0.19/0.01 |
| A_t30_s75 | 18469 | 95.2 | 0.90 | 0.723 | 0.704 (-0.019) [-0.03, -0.01] | 28.0 / -65.5 | 0.71/0.26/0.02 |
| A_t40_s75 | 16078 | 82.9 | 0.68 | 0.658 | 0.652 (-0.006) [-0.02, 0.00] | 37.4 / -67.3 | 0.65/0.32/0.03 |
| A_t45_s75 | 15116 | 77.9 | 0.68 | 0.631 | 0.623 (-0.007) [-0.02, 0.00] | 42.0 / -67.6 | 0.62/0.34/0.04 |
| A_t50_s75 | 14284 | 73.6 | 0.64 | 0.605 | 0.598 (-0.007) [-0.02, 0.00] | 46.5 / -67.8 | 0.59/0.37/0.04 |
| A_t20_s90 | 20662 | 106.5 | 0.82 | 0.826 | 0.794 (-0.032) [-0.04, -0.03] | 18.6 / -71.1 | 0.82/0.17/0.02 |
| A_t30_s90 | 17045 | 87.9 | 0.82 | 0.757 | 0.734 (-0.023) [-0.03, -0.02] | 28.0 / -76.7 | 0.74/0.23/0.03 |
| A_t40_s90 | 14758 | 76.1 | 0.76 | 0.698 | 0.684 (-0.014) [-0.02, -0.01] | 37.5 / -79.1 | 0.68/0.28/0.04 |
| A_t45_s90 | 13830 | 71.3 | 0.71 | 0.672 | 0.657 (-0.015) [-0.02, -0.00] | 42.1 / -79.4 | 0.65/0.30/0.05 |
| A_t50_s90 | 13047 | 67.3 | 0.62 | 0.647 | 0.634 (-0.013) [-0.02, -0.00] | 46.6 / -79.7 | 0.62/0.32/0.05 |
| KB_t30_s60 | 12769 | 65.8 | 0.74 | 0.675 | 0.667 (-0.008) [-0.02, 0.00] | 28.1 / -54.5 | 0.67/0.31/0.02 |
| KB_t40_s60 | 10888 | 56.1 | 0.74 | 0.607 | 0.602 (-0.005) [-0.01, 0.00] | 37.5 / -55.6 | 0.60/0.38/0.02 |
| SM_t30_s60 | 2651 | 13.7 | 0.83 | 0.676 | 0.679 (+0.003) [-0.01, 0.02] | 27.8 / -54.5 | 0.68/0.30/0.02 |
| SM_t40_s60 | 2551 | 13.1 | 0.71 | 0.607 | 0.628 (+0.020) [0.00, 0.04] | 37.2 / -55.8 | 0.62/0.36/0.02 |
| EM_t30_s60 | 2585 | 13.3 | 1.12 | 0.679 | 0.682 (+0.003) [-0.02, 0.02] | 28.1 / -55.0 | 0.69/0.29/0.02 |
| EM_t40_s60 | 2472 | 12.7 | 1.19 | 0.612 | 0.620 (+0.008) [-0.01, 0.03] | 37.5 / -55.6 | 0.62/0.35/0.03 |

| cell | paired pts/trade WF [CI] | MDE | n pairs | PRE | HOLD | SPAN2 (2023-04..24-01) | 2x cost | placebo rank (raw / recentred) | neighbours | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| A_t20_s60 | -1.35 [-2.33, -0.36] | 1.42 | 11915 | -1.44 | -1.28 | +0.52 | -1.67 | 0.45 / 0.00 | agree | DEAD |
| A_t30_s60 | -0.84 [-1.68, +0.01] | 1.21 | 11701 | -0.92 | -0.78 | +0.56 | -1.11 | 0.60 / 0.05 | agree | DEAD |
| A_t40_s60 | -0.61 [-1.25, +0.08] | 0.96 | 11394 | -0.62 | -0.60 | +0.93 | -0.75 | 0.50 / 0.10 | agree | DEAD |
| A_t45_s60 | -0.46 [-1.00, +0.09] | 0.78 | 11360 | -0.53 | -0.41 | +0.23 | -0.59 | 0.65 / 0.05 | agree | DEAD |
| A_t50_s60 | -0.20 [-0.61, +0.22] | 0.60 | 11525 | -0.23 | -0.18 | +0.48 | -0.19 | 0.70 / 0.20 | agree | DEAD |
| A_t20_s75 | -1.65 [-2.61, -0.74] | 1.38 | 11012 | -1.87 | -1.48 | +0.62 | -1.91 | 0.50 / 0.00 | agree | DEAD |
| A_t30_s75 | -1.19 [-2.09, -0.21] | 1.34 | 10556 | -1.39 | -1.03 | +0.39 | -1.60 | 0.70 / 0.00 | agree | DEAD |
| A_t40_s75 | -0.86 [-1.62, -0.04] | 1.16 | 10032 | -0.87 | -0.86 | +1.29 | -1.17 | 0.70 / 0.00 | agree | DEAD |
| A_t45_s75 | -0.69 [-1.40, +0.04] | 1.06 | 9869 | -0.91 | -0.54 | +0.50 | -0.99 | 0.80 / 0.05 | agree | DEAD |
| A_t50_s75 | -0.56 [-1.22, +0.12] | 0.97 | 9837 | -0.66 | -0.49 | +0.29 | -0.76 | 0.80 / 0.05 | agree | DEAD |
| A_t20_s90 | -1.78 [-2.95, -0.66] | 1.59 | 10411 | -1.83 | -1.73 | +0.32 | -2.04 | 0.60 / 0.00 | agree | DEAD |
| A_t30_s90 | -1.29 [-2.31, -0.24] | 1.45 | 9843 | -1.22 | -1.35 | -0.23 | -1.64 | 0.75 / 0.05 | agree | DEAD |
| A_t40_s90 | -0.87 [-1.80, +0.09] | 1.38 | 9229 | -0.49 | -1.15 | +0.20 | -1.19 | 0.80 / 0.05 | agree | DEAD |
| A_t45_s90 | -0.67 [-1.58, +0.28] | 1.31 | 9032 | -0.63 | -0.70 | -0.90 | -0.91 | 0.90 / 0.10 | agree | DEAD |
| A_t50_s90 | -0.44 [-1.32, +0.38] | 1.22 | 8954 | -0.62 | -0.30 | -1.00 | -0.48 | 0.85 / 0.40 | agree | DEAD |
| KB_t30_s60 | -0.71 [-1.66, +0.24] | 1.34 | 6724 | -0.95 | -0.53 | +1.17 | -0.74 | 0.80 / 0.10 | agree | DEAD |
| KB_t40_s60 | -0.20 [-0.99, +0.61] | 1.15 | 6364 | -0.28 | -0.14 | -0.12 | -0.33 | 0.80 / 0.25 | agree | DEAD |
| SM_t30_s60 | -1.81 [-3.81, -0.13] | 2.56 | 1858 | -2.15 | -1.49 | +2.11 | -1.94 | 0.05 / 0.00 | agree | DEAD |
| SM_t40_s60 | -0.26 [-1.79, +1.25] | 2.14 | 1857 | -0.42 | -0.11 | +1.68 | -0.34 | 0.75 / 0.35 | agree | DEAD |
| EM_t30_s60 | -0.73 [-2.58, +1.00] | 2.58 | 1810 | -1.15 | -0.33 | +0.23 | -1.02 | 0.70 / 0.20 | agree | DEAD |
| EM_t40_s60 | -0.09 [-1.57, +1.35] | 2.08 | 1810 | +0.42 | -0.57 | -0.05 | -0.44 | 0.75 / 0.40 | agree | DEAD |

| cell | WF mean $/wk | SD | maxDD | d mean vs base | d SD | d maxDD | CI of d mean | 2x d mean | HOLD d mean | SPAN2 d mean | R-scaled locks WF mean | const-risk lots WF mean (peak lots) | peak lots |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| A_t20_s60 | 5,778 | 91,350 | 596,262 | -19,203 | -13,173 | 194,944 | [-35,116, -3,065] | -36,549 | -20,834 | -17,650 | 5,778 | 5,778 (28) | 28 |
| A_t30_s60 | 7,736 | 95,097 | 942,747 | -17,245 | -9,426 | 541,429 | [-32,809, -2,095] | -32,051 | -15,672 | -11,061 | 7,736 | 7,736 (28) | 28 |
| A_t40_s60 | 10,674 | 95,245 | 620,127 | -14,307 | -9,279 | 218,809 | [-28,689, 102] | -19,308 | -18,677 | 5,483 | 10,674 | 10,674 (28) | 28 |
| A_t45_s60 | 11,224 | 101,662 | 595,826 | -13,756 | -2,862 | 194,508 | [-27,615, -989] | -20,225 | -18,689 | -2,615 | 11,224 | 11,224 (28) | 28 |
| A_t50_s60 | 17,777 | 105,264 | 551,482 | -7,203 | 741 | 150,163 | [-20,570, 5,757] | -12,405 | -11,913 | -3,148 | 17,777 | 17,777 (28) | 28 |
| A_t20_s75 | 2,186 | 104,024 | 943,267 | -22,795 | -500 | 541,949 | [-41,310, -6,236] | -34,523 | -28,345 | -16,825 | 579 | 3,443 (22) | 28 |
| A_t30_s75 | -165 | 104,743 | 1,014,349 | -25,146 | 219 | 613,031 | [-41,549, -8,484] | -34,275 | -31,818 | -17,272 | 3,154 | 6,328 (22) | 28 |
| A_t40_s75 | 3,029 | 109,775 | 1,299,358 | -21,952 | 5,252 | 898,040 | [-39,366, -6,022] | -25,230 | -29,799 | 148 | 6,986 | 7,142 (22) | 28 |
| A_t45_s75 | 2,846 | 106,626 | 995,765 | -22,134 | 2,102 | 594,447 | [-38,656, -5,919] | -25,792 | -28,661 | -4,317 | 6,822 | 6,807 (22) | 28 |
| A_t50_s75 | 4,146 | 109,802 | 853,035 | -20,835 | 5,279 | 451,717 | [-37,013, -5,562] | -28,457 | -19,277 | -3,472 | 7,206 | 6,668 (22) | 28 |
| A_t20_s90 | 2,132 | 99,338 | 1,341,858 | -22,848 | -5,186 | 940,539 | [-41,029, -6,719] | -37,155 | -23,478 | -32,290 | 6,945 | 9,031 (19) | 28 |
| A_t30_s90 | -3,627 | 104,283 | 1,548,011 | -28,607 | -241 | 1,146,693 | [-45,460, -11,101] | -35,677 | -37,386 | -21,507 | 794 | 4,174 (19) | 28 |
| A_t40_s90 | 4,379 | 102,874 | 1,287,038 | -20,602 | -1,649 | 885,720 | [-36,792, -2,847] | -28,306 | -26,029 | -19,321 | 9,313 | 8,360 (19) | 28 |
| A_t45_s90 | -4,044 | 109,233 | 1,857,337 | -29,024 | 4,710 | 1,456,019 | [-45,890, -11,667] | -31,512 | -31,653 | -21,021 | -2,011 | 2,078 (19) | 28 |
| A_t50_s90 | -1,454 | 103,894 | 1,732,373 | -26,434 | -629 | 1,331,055 | [-42,367, -10,968] | -30,741 | -28,635 | -10,371 | -1,801 | 1,202 (19) | 28 |
| KB_t30_s60 | 11,284 | 51,270 | 321,301 | -5,554 | -8,302 | -15,324 | [-14,500, 3,358] | -8,909 | -6,764 | 6,296 | 11,284 | 11,284 (10) | 10 |
| KB_t40_s60 | 12,341 | 49,569 | 299,055 | -4,497 | -10,003 | -37,571 | [-12,665, 3,401] | -2,145 | -2,666 | -5,422 | 12,341 | 12,341 (10) | 10 |
| SM_t30_s60 | 4,118 | 28,266 | 176,396 | -5,013 | -7,264 | -21,026 | [-9,754, -177] | -5,692 | -5,344 | -1,368 | 4,118 | 4,118 (10) | 10 |
| SM_t40_s60 | 7,290 | 31,233 | 155,386 | -1,841 | -4,297 | -42,036 | [-5,676, 2,355] | -1,922 | -1,922 | -580 | 7,290 | 7,290 (10) | 10 |
| EM_t30_s60 | 6,375 | 26,860 | 269,682 | -1,217 | -7,039 | 92,600 | [-6,379, 3,434] | -1,547 | -279 | -1,613 | 6,375 | 6,375 (10) | 10 |
| EM_t40_s60 | 8,284 | 28,979 | 148,444 | 692 | -4,921 | -28,639 | [-3,542, 4,863] | 390 | -217 | -1,647 | 8,284 | 8,284 (10) | 10 |

| cell | ASIA pts [CI] (n) | LONDON | NY | ASIA hurdle req/obs | LONDON | NY | LONG | SHORT | QUIET | WIDE |
|--|--|--|--|--|--|--|--|--|--|--|
| A_t20_s60 | -1.60 [-3.47, +0.21] (5346) | -0.41 [-2.30, +1.62] (6311) | -1.76 [-3.05, -0.46] (7991) | 0.76/0.76 | 0.76/0.74 | 0.76/0.72 | -0.79 [-2.12, +0.55] | -1.89 [-3.11, -0.50] | -1.89 [-3.37, -0.48] | -0.90 [-2.20, +0.33] |
| A_t30_s60 | -0.83 [-2.55, +0.73] (4513) | -0.65 [-2.43, +1.19] (5143) | -0.96 [-2.13, +0.17] (7142) | 0.68/0.69 | 0.68/0.66 | 0.68/0.66 | -0.22 [-1.33, +0.93] | -1.42 [-2.59, -0.22] | -1.27 [-2.50, -0.08] | -0.48 [-1.55, +0.62] |
| A_t40_s60 | -1.04 [-2.40, +0.26] (3975) | -0.37 [-1.75, +1.02] (4374) | -0.49 [-1.32, +0.43] (6477) | 0.61/0.62 | 0.61/0.60 | 0.61/0.60 | -0.02 [-0.95, +0.93] | -1.15 [-2.04, -0.31] | -0.96 [-1.87, -0.04] | -0.31 [-1.16, +0.56] |
| A_t45_s60 | -0.76 [-1.83, +0.29] (3779) | -0.39 [-1.42, +0.63] (4081) | -0.33 [-1.07, +0.40] (6215) | 0.58/0.60 | 0.58/0.57 | 0.58/0.58 | +0.06 [-0.70, +0.83] | -0.95 [-1.71, -0.19] | -0.66 [-1.43, +0.15] | -0.29 [-1.04, +0.43] |
| A_t50_s60 | -0.51 [-1.36, +0.42] (3604) | -0.01 [-0.84, +0.86] (3821) | -0.13 [-0.68, +0.47] (5952) | 0.55/0.57 | 0.55/0.55 | 0.55/0.55 | +0.26 [-0.34, +0.87] | -0.63 [-1.22, -0.06] | -0.20 [-0.85, +0.42] | -0.20 [-0.74, +0.33] |
| A_t20_s75 | -2.10 [-4.09, -0.12] (5022) | -1.09 [-3.10, +1.03] (5634) | -1.70 [-3.05, -0.37] (7431) | 0.80/0.79 | 0.80/0.77 | 0.80/0.75 | -1.29 [-2.71, +0.17] | -1.99 [-3.39, -0.56] | -2.42 [-4.01, -0.96] | -0.99 [-2.39, +0.34] |
| A_t30_s75 | -1.73 [-3.56, +0.05] (4209) | -1.41 [-3.33, +0.40] (4533) | -0.74 [-1.93, +0.56] (6565) | 0.72/0.72 | 0.72/0.71 | 0.72/0.70 | -0.91 [-2.21, +0.36] | -1.44 [-2.73, -0.23] | -1.82 [-3.12, -0.46] | -0.65 [-1.77, +0.56] |
| A_t40_s75 | -1.74 [-3.38, -0.19] (3691) | -1.35 [-3.04, +0.51] (3841) | -0.10 [-1.19, +1.06] (5887) | 0.66/0.66 | 0.66/0.65 | 0.66/0.65 | -0.75 [-1.87, +0.41] | -0.97 [-2.03, +0.13] | -1.37 [-2.55, -0.18] | -0.43 [-1.40, +0.62] |
| A_t45_s75 | -1.42 [-2.86, +0.10] (3493) | -1.38 [-2.98, +0.31] (3558) | +0.09 [-0.89, +1.13] (5615) | 0.63/0.64 | 0.63/0.62 | 0.63/0.62 | -0.57 [-1.53, +0.53] | -0.81 [-1.77, +0.17] | -0.97 [-2.10, +0.12] | -0.46 [-1.40, +0.55] |
| A_t50_s75 | -0.91 [-2.25, +0.51] (3315) | -1.33 [-2.71, +0.20] (3307) | +0.04 [-0.89, +0.97] (5345) | 0.61/0.62 | 0.61/0.59 | 0.60/0.60 | -0.59 [-1.56, +0.36] | -0.54 [-1.37, +0.37] | -0.68 [-1.70, +0.39] | -0.46 [-1.32, +0.45] |
| A_t20_s90 | -2.86 [-4.96, -0.84] (4834) | -1.35 [-3.50, +0.98] (5168) | -1.36 [-2.84, +0.16] (6982) | 0.83/0.81 | 0.82/0.80 | 0.82/0.78 | -1.76 [-3.27, -0.26] | -1.79 [-3.22, -0.12] | -2.78 [-4.38, -1.12] | -0.92 [-2.33, +0.33] |
| A_t30_s90 | -2.71 [-4.78, -0.61] (3991) | -1.48 [-3.63, +0.82] (4075) | -0.35 [-1.73, +1.03] (6084) | 0.76/0.75 | 0.76/0.73 | 0.76/0.73 | -1.40 [-2.85, +0.04] | -1.19 [-2.52, +0.19] | -2.14 [-3.68, -0.67] | -0.57 [-1.98, +0.74] |
| A_t40_s90 | -2.63 [-4.62, -0.58] (3467) | -1.36 [-3.16, +0.69] (3422) | +0.43 [-0.81, +1.71] (5429) | 0.70/0.70 | 0.70/0.69 | 0.70/0.68 | -0.99 [-2.36, +0.38] | -0.76 [-2.07, +0.51] | -1.77 [-3.28, -0.38] | -0.10 [-1.33, +1.18] |
| A_t45_s90 | -2.45 [-4.41, -0.42] (3275) | -1.11 [-2.94, +0.83] (3170) | +0.62 [-0.66, +1.84] (5153) | 0.67/0.67 | 0.67/0.66 | 0.67/0.66 | -1.00 [-2.35, +0.33] | -0.36 [-1.61, +0.99] | -1.54 [-2.95, -0.07] | +0.07 [-1.06, +1.29] |
| A_t50_s90 | -1.56 [-3.32, +0.23] (3122) | -0.90 [-2.72, +0.80] (2928) | +0.49 [-0.70, +1.64] (4889) | 0.65/0.65 | 0.65/0.63 | 0.65/0.64 | -0.85 [-2.11, +0.33] | -0.04 [-1.22, +1.22] | -0.87 [-2.18, +0.43] | -0.07 [-1.25, +1.17] |
| KB_t30_s60 | -1.19 [-3.14, +0.68] (2898) | -0.35 [-2.29, +1.81] (3017) | -0.62 [-1.87, +0.59] (4719) | 0.68/0.69 | 0.67/0.67 | 0.67/0.65 | -0.88 [-2.23, +0.44] | -0.53 [-1.83, +0.90] | -0.36 [-1.81, +0.98] | -1.01 [-2.37, +0.20] |
| KB_t40_s60 | -0.65 [-2.16, +0.86] (2456) | +0.57 [-1.21, +2.40] (2504) | -0.32 [-1.38, +0.67] (4175) | 0.61/0.63 | 0.61/0.60 | 0.61/0.59 | +0.24 [-0.86, +1.41] | -0.66 [-1.72, +0.35] | +0.27 [-0.94, +1.47] | -0.60 [-1.62, +0.47] |
| SM_t30_s60 | -1.89 [-5.22, +1.45] (588) | -0.70 [-3.80, +2.55] (787) | -2.93 [-5.75, -0.05] (647) | 0.68/0.72 | 0.68/0.68 | 0.67/0.64 | -3.16 [-5.63, -0.61] | -0.51 [-3.04, +1.95] | -1.15 [-3.88, +1.52] | -2.35 [-4.68, +0.02] |
| SM_t40_s60 | -0.14 [-2.85, +2.81] (577) | +0.55 [-1.88, +3.08] (746) | -1.23 [-3.57, +1.20] (640) | 0.61/0.66 | 0.60/0.63 | 0.61/0.61 | -1.33 [-3.30, +0.80] | +0.78 [-1.28, +2.94] | +0.23 [-2.12, +2.61] | -0.65 [-2.61, +1.30] |
| EM_t30_s60 | -0.82 [-3.99, +2.59] (618) | -1.03 [-4.04, +2.51] (690) | -0.35 [-3.53, +2.81] (661) | 0.68/0.71 | 0.68/0.70 | 0.68/0.66 | -1.30 [-4.00, +1.18] | -0.19 [-2.80, +2.46] | -1.54 [-4.21, +1.19] | -0.04 [-2.63, +2.66] |
| EM_t40_s60 | +0.27 [-2.63, +3.25] (606) | -0.67 [-3.38, +2.03] (649) | +0.12 [-2.14, +2.47] (649) | 0.61/0.65 | 0.61/0.64 | 0.61/0.61 | -0.09 [-2.18, +1.91] | -0.09 [-2.17, +2.07] | -0.10 [-2.32, +2.25] | -0.09 [-2.16, +1.99] |

## 4. Nulls and caveats
- Placebo: same bracket on random-time entries (hour/side matched, 20 draws, mapped basis, paired vs the 60/60 base on identical random entries). The null mean is itself negative in the mapped basis (bias), so the recentred rank is reported next to the raw rank.
- Label permutation of brackets across trades leaves the paired mean invariant and is not informative for the mean.
- D3NT overlap: targets 45/50 (and 40) are a shorter fixed target, conceptually the near-target "fixed target 55/57" comparison; same rule family, not re-tested under another name. Nearest scored cells: FAILPRED STEP2 C1/C2 (bracket x0.5, DEAD), STRUCT48 T1.4 (direction-asymmetric stop/target; short stop 50 nearest miss), T4/SO2/HB.

## 5. Stage 2 (calibrated-mapped screen of the 9 x 6 grids, SCREENED only)
**EM**: 53 cells; best calibrated paired effect +0.47 pt (BA2_EM_t40_s60, CI [-0.94,+1.94], MDE 2.10); cells with CI above 0: 0; cells with positive effect and positive hold and span2: 2.
**HM**: 53 cells; best calibrated paired effect +0.30 pt (BA2_HM_t60_s90, CI [-0.79,+1.52], MDE 1.66); cells with CI above 0: 0; cells with positive effect and positive hold and span2: 0.
**KB**: 53 cells; best calibrated paired effect +0.61 pt (BA2_KB_t90_s90, CI [-1.39,+2.56], MDE 2.80); cells with CI above 0: 0; cells with positive effect and positive hold and span2: 7.
**SM**: 53 cells; best calibrated paired effect +0.10 pt (BA2_SM_t60_s90, CI [-1.63,+1.95], MDE 2.60); cells with CI above 0: 0; cells with positive effect and positive hold and span2: 2.
**ST**: 53 cells; best calibrated paired effect +0.26 pt (BA2_ST_t50_s60, CI [-0.24,+0.81], MDE 0.77); cells with CI above 0: 0; cells with positive effect and positive hold and span2: 5.
Full table: l2vast/ds3/out/ba/stage2_screen.csv
