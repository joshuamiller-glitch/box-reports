# DS3_OPEN_B2_OR_DRIVE_B3 - T-OPEN blocks (iii), (iv), (vi-lite) for the 3.1 / 3.2 top signals + DR5m cluster checks (D3O1, 2026-10-28)
Research only; nothing is live. Harness: README_OPEN2.md; block (ii) results: DS3_OPEN_B2_OR_DRIVE.md. Interim report for the lead's overnight item A.

## 1. Block (iii): section-4 grid on the top signals (prereg B3GRID, master sha256 f40efca3...; 40 groups, 896 cells registered, 894 scored, 40 holdout looks)
Signals chosen on WFPRE numbers only (score = min over bases of the mean PRE stack d_Sharpe of the signal's 3 best bracket cells; >= 100 PRE trades; distinct (length, entry) pairs): 3.1 OR3m_c1 (0.523), OR3m_c2 (0.479), OR30s_c2_le1.5 (0.469); 3.2 DR15m_pb3_mv10 (0.492), DR15m_hl_mv10 (0.492), plus by lead instruction the DR5m cluster: DR5m_pb3_rm0.5 (0.365), DR5m_pb1_rm0.5 (0.346), DR10m_pb1_rm0.5 (0.287). 112 cells per signal: fixed grid 7 stops x 12 targets (84), 10 time exits, 3 chandelier, 6 scale-out, 5 height multiples, 4 ATR20 multiples (structural stops, other structural targets, swing/SAR/breakeven/profit-lock trails, overnight hold are NOT in this block).
**Harness-primary result: 12 PASS + 11 CANDIDATE (final = lower tier of M/T) of 894 cells; all 23 are DR5m_pb1_rm0.5 / DR5m_pb3_rm0.5 cells. 0 PASS / 0 CANDIDATE among the OR signals and among DR15m_*, DR10m_pb1.** HEALTH WARNING (same as the lead noted for T-CLOSE): the block-(iii) best-of-N family has only 896 cells (null p95 16 pts) although the 8 signals were picked out of 9,972 block-(ii) cells. Secondary and program-level columns: per-bracket-class null (grid 10.7/11.5, time 14.6/14.3, chandelier 5, scale 6.4/7.1, height 7.4/7.7, ATR 12.7/13.6 pts for M/T): all 12 PASS pass it, 5 of 11 CANDIDATE pass it (both bases); PROGRAM-level null (all block-(ii) + (iii) placebo cells pooled, N_total = 9,972 + 896; p95 140 / 140 pts): all 23 FAIL. Cell-level bootstrap z of the effect vs the random clock: 1.9-2.9 (Bonferroni over ~10,900 cells needs ~4.4). Reading: PASS(primary, small family) / secondary PASS / program-level FAIL: one idea (5-minute drive >= 0.5 x median 5-min range, first pullback) whose exit shape variants reproduce the block-(ii) cluster; promotion is the lead's decision, my recommendation is forward-register only.
The PASS(primary) cells: DR5m_pb1_rm0.5 with X60_75 (stop 60 / target 75), TM1100, TM1130, TM1200, TM1300, AT0.75, AT1; DR5m_pb3_rm0.5 with TM1100, TM1130, TM1200, TM1600 (hold), AT1 (both bases); CANDIDATE: X60_50 / X60_60 / X40_45, TM1015 / TM1030, SO33_0.75 / SO33_1 / SO50_1, AT0.25. The fixed 60/75 cell is the cleanest (small bracket beta, a real target): WF stack d_Sharpe +0.19 (M) / +0.22 (T), d_mean +4.7k / +5.3k $/wk [HOLD +2.4k / +3.8k; 2023 span +2.0k / +2.1k], maxDD 76k / 81k better, 2.3 trades/wk, effect vs random clock +17.0 pts (rank 1.00), vs random direction +11.9 / +13.0, vs in-regime random direction +12.8 / +13.4; bootstrap z 2.9; PRE stack d_Sharpe +0.29 / +0.28; 2x cost PRE +5.5k / +6.0k $/wk.
Surface (basis T; DR5m_pb1_rm0.5; full tables below): stack d_Sharpe rises monotonically with target and with stop: stop 60 / target 120 +0.32, stop 60 / target 60 +0.25, stops 10-20 with small targets are negative: i.e. it behaves like a trend-capture (convex) payoff; the high-win-rate shapes (stop 60-75, target 15-30) are positive but small (win rate 0.73-0.88 vs required 0.67-0.86).
#### DR5m_pb1_rm0.5: fixed grid, basis T, stack d_Sharpe (WF) by stop (rows) x target (cols)

|   S |    10 |    15 |    20 |    25 |    30 |    40 |    45 |    50 |   60 |    75 |   90 |   120 |
|----:|------:|------:|------:|------:|------:|------:|------:|------:|-----:|------:|-----:|------:|
|  10 | -0.04 | -0.04 | -0.06 | -0.05 | -0.04 | -0.03 | -0.02 | -0.01 | 0.02 | -0    | 0.03 |  0.06 |
|  15 | -0.01 | -0.02 | -0.02 | -0.01 | -0    |  0.02 |  0.02 |  0.03 | 0.07 |  0.05 | 0.07 |  0.09 |
|  20 | -0    | -0.01 | -0.01 |  0.01 |  0.02 |  0.05 |  0.05 |  0.06 | 0.11 |  0.08 | 0.1  |  0.12 |
|  30 |  0.01 |  0.02 |  0.03 |  0.04 |  0.05 |  0.09 |  0.1  |  0.1  | 0.15 |  0.14 | 0.17 |  0.2  |
|  40 |  0.04 |  0.03 |  0.06 |  0.08 |  0.08 |  0.12 |  0.13 |  0.14 | 0.17 |  0.17 | 0.2  |  0.27 |
|  60 |  0.04 |  0.05 |  0.1  |  0.11 |  0.14 |  0.19 |  0.19 |  0.18 | 0.25 |  0.22 | 0.26 |  0.32 |
|  75 |  0.04 |  0.06 |  0.1  |  0.1  |  0.16 |  0.21 |  0.21 |  0.19 | 0.23 |  0.18 | 0.23 |  0.29 |

DR5m_pb1_rm0.5: WFPRE standalone $/wk

|   S |   10 |   15 |   20 |   25 |   30 |   40 |   45 |   50 |   60 |   75 |   90 |   120 |
|----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|------:|
|  10 | -760 | -716 | -804 | -808 | -678 | -602 | -336 | -258 |  302 |  472 | 1125 |  1799 |
|  15 | -492 | -489 | -537 | -690 | -266 |   49 | -114 |  111 |  602 |  742 | 1180 |  1884 |
|  20 |  -13 |   16 |   48 |  364 |  626 |  993 |  802 | 1014 | 1410 | 1709 | 2547 |  2990 |
|  30 |  -84 |  536 | 1185 | 1647 | 1762 | 2850 | 2632 | 2869 | 3237 | 4176 | 5413 |  6295 |
|  40 |  404 |  797 | 1566 | 1828 | 1876 | 3044 | 3240 | 3544 | 3805 | 5318 | 6234 |  7302 |
|  60 |  490 | 1072 | 2109 | 1903 | 2420 | 3855 | 4012 | 4329 | 5258 | 6542 | 7818 |  8555 |
|  75 |  332 |  914 | 2099 | 1600 | 2264 | 3579 | 3295 | 3185 | 3259 | 4744 | 6048 |  7617 |

DR5m_pb1_rm0.5: observed win rate / required win rate (WF)

|   S | 10        | 15        | 20        | 25        | 30        | 40        | 45        | 50        | 60        | 75        | 90        | 120       |
|----:|:----------|:----------|:----------|:----------|:----------|:----------|:----------|:----------|:----------|:----------|:----------|:----------|
|  10 | 0.45/0.52 | 0.35/0.42 | 0.28/0.35 | 0.25/0.3  | 0.23/0.26 | 0.19/0.21 | 0.18/0.19 | 0.17/0.17 | 0.16/0.15 | 0.13/0.12 | 0.12/0.1  | 0.11/0.08 |
|  15 | 0.6/0.61  | 0.49/0.51 | 0.41/0.44 | 0.37/0.38 | 0.35/0.34 | 0.3/0.28  | 0.27/0.26 | 0.26/0.24 | 0.24/0.21 | 0.21/0.17 | 0.19/0.15 | 0.16/0.12 |
|  20 | 0.67/0.68 | 0.57/0.58 | 0.5/0.51  | 0.47/0.45 | 0.43/0.41 | 0.38/0.34 | 0.35/0.31 | 0.33/0.29 | 0.31/0.26 | 0.26/0.22 | 0.24/0.19 | 0.2/0.15  |
|  30 | 0.77/0.76 | 0.69/0.67 | 0.64/0.61 | 0.6/0.55  | 0.55/0.51 | 0.5/0.43  | 0.47/0.41 | 0.44/0.38 | 0.41/0.34 | 0.36/0.29 | 0.33/0.26 | 0.29/0.21 |
|  40 | 0.83/0.81 | 0.75/0.73 | 0.71/0.67 | 0.67/0.62 | 0.62/0.58 | 0.57/0.5  | 0.54/0.47 | 0.51/0.45 | 0.47/0.4  | 0.43/0.35 | 0.4/0.31  | 0.35/0.26 |
|  60 | 0.88/0.86 | 0.83/0.8  | 0.8/0.75  | 0.76/0.71 | 0.73/0.67 | 0.68/0.6  | 0.65/0.57 | 0.62/0.55 | 0.59/0.5  | 0.53/0.45 | 0.5/0.41  | 0.44/0.35 |
|  75 | 0.9/0.89  | 0.86/0.84 | 0.83/0.79 | 0.79/0.75 | 0.77/0.72 | 0.73/0.66 | 0.7/0.63  | 0.67/0.6  | 0.63/0.56 | 0.57/0.51 | 0.54/0.46 | 0.48/0.4  |

#### DR5m_pb3_rm0.5: fixed grid, basis T, stack d_Sharpe (WF) by stop (rows) x target (cols)

|   S |    10 |    15 |    20 |    25 |   30 |   40 |   45 |   50 |   60 |    75 |   90 |   120 |
|----:|------:|------:|------:|------:|-----:|-----:|-----:|-----:|-----:|------:|-----:|------:|
|  10 | -0.01 |  0    | -0.01 |  0.01 | 0.02 | 0.03 | 0.03 | 0.03 | 0.03 |  0.02 | 0.05 |  0.05 |
|  15 | -0.02 | -0.01 | -0.02 | -0.01 | 0.01 | 0.02 | 0.01 | 0    | 0.02 | -0    | 0.02 |  0.04 |
|  20 | -0    |  0.01 | -0    |  0.01 | 0.04 | 0.07 | 0.07 | 0.05 | 0.06 |  0.05 | 0.08 |  0.09 |
|  30 | -0.05 | -0.02 | -0.03 | -0.02 | 0.03 | 0.06 | 0.06 | 0.05 | 0.05 |  0.04 | 0.06 |  0.1  |
|  40 | -0.03 |  0.01 |  0.01 |  0.02 | 0.07 | 0.13 | 0.15 | 0.13 | 0.16 |  0.14 | 0.15 |  0.2  |
|  60 | -0.03 |  0.01 |  0    |  0.01 | 0.09 | 0.17 | 0.21 | 0.17 | 0.19 |  0.2  | 0.22 |  0.26 |
|  75 |  0    |  0.05 |  0.05 |  0.08 | 0.15 | 0.21 | 0.25 | 0.25 | 0.28 |  0.28 | 0.28 |  0.37 |

#### OR3m_c1: fixed grid, basis T, stack d_Sharpe (WF) by stop (rows) x target (cols)

|   S |    10 |    15 |    20 |    25 |    30 |    40 |    45 |    50 |    60 |    75 |    90 |   120 |
|----:|------:|------:|------:|------:|------:|------:|------:|------:|------:|------:|------:|------:|
|  10 | -0.08 | -0.09 | -0.09 | -0.11 | -0.11 | -0.08 | -0.06 | -0.07 | -0.06 | -0.09 | -0.06 | -0.06 |
|  15 | -0.04 | -0.05 | -0.05 | -0.06 | -0.04 | -0.01 |  0    | -0.02 |  0.02 | -0.02 |  0.02 |  0.04 |
|  20 | -0.04 | -0.06 | -0.05 | -0.04 | -0.02 |  0.02 |  0.03 |  0    |  0.05 | -0.01 |  0.04 |  0.04 |
|  30 | -0.02 | -0.05 | -0.04 | -0.02 |  0    |  0.05 |  0.07 |  0.06 |  0.13 |  0.08 |  0.14 |  0.14 |
|  40 | -0.03 | -0.04 | -0.01 | -0.04 |  0.01 |  0.09 |  0.13 |  0.07 |  0.16 |  0.08 |  0.16 |  0.12 |
|  60 | -0.03 | -0.02 | -0.03 | -0.07 | -0.02 |  0.08 |  0.11 |  0.05 |  0.16 |  0.14 |  0.26 |  0.21 |
|  75 | -0.04 | -0.03 | -0.03 | -0.05 |  0.04 |  0.13 |  0.13 |  0.11 |  0.17 |  0.16 |  0.27 |  0.26 |

#### High-win-rate shapes (wide stop, small target), basis T: WF stack dSh / WFPRE $/wk / win vs required

| signal          |   X40_15 |   X60_15 |   X60_20 |   X60_30 |   X75_15 |   X75_20 |   X75_30 |
|:----------------|---------:|---------:|---------:|---------:|---------:|---------:|---------:|
| DR10m_pb1_rm0.5 |    0.067 |    0.02  |    0.033 |    0.102 |    0.009 |    0.001 |    0.072 |
| DR15m_hl_mv10   |    0.037 |    0.017 |    0.038 |    0.075 |   -0.033 |   -0.014 |    0.024 |
| DR15m_pb3_mv10  |    0.009 |   -0.028 |    0.007 |    0.077 |   -0.043 |   -0.018 |    0.092 |
| DR5m_pb1_rm0.5  |    0.033 |    0.053 |    0.103 |    0.143 |    0.055 |    0.097 |    0.159 |
| DR5m_pb3_rm0.5  |    0.007 |    0.007 |    0.005 |    0.088 |    0.053 |    0.055 |    0.152 |
| OR30s_c2_le1.5  |   -0.076 |   -0.076 |   -0.073 |   -0.012 |   -0.072 |   -0.093 |   -0.022 |
| OR3m_c1         |   -0.044 |   -0.025 |   -0.031 |   -0.025 |   -0.025 |   -0.031 |    0.038 |
| OR3m_c2         |   -0.077 |   -0.061 |   -0.061 |   -0     |   -0.082 |   -0.081 |    0.041 |

#### DR5m_pb1_rm0.5 time exits (basis T)

| b      | verdict   |   dS_pre |   dS_wf |   dS_hold |   pre_mean |   hold_mean |   tpw |
|:-------|:----------|---------:|--------:|----------:|-----------:|------------:|------:|
| TM0945 | DEAD      |     0.08 |    0.05 |      0.02 |    1578.94 |     1050.06 |  2.31 |
| TM1000 | DEAD      |     0.16 |    0.18 |      0.19 |    3420.29 |     4701.54 |  2.32 |
| TM1015 | CANDIDATE |     0.25 |    0.2  |      0.14 |    5569.63 |     4280.21 |  2.32 |
| TM1030 | CANDIDATE |     0.26 |    0.2  |      0.13 |    6338.29 |     4602.27 |  2.32 |
| TM1100 | PASS      |     0.34 |    0.23 |      0.12 |    8146.29 |     4390.51 |  2.32 |
| TM1130 | PASS      |     0.36 |    0.23 |      0.09 |    8154.29 |     4168.45 |  2.32 |
| TM1200 | PASS      |     0.38 |    0.23 |      0.07 |    8680.29 |     4016.24 |  2.32 |
| TM1300 | PASS      |     0.39 |    0.27 |      0.15 |    9210.96 |     5814.77 |  2.32 |
| TM1550 | DEAD      |     0.36 |    0.29 |      0.21 |    9452.96 |     7428.74 |  2.32 |
| TM1600 | DEAD      |     0.36 |    0.29 |      0.19 |    9729.63 |     7165.51 |  2.32 |

#### DR5m_pb1_rm0.5 chandelier (basis T)

| b     | verdict   |   dS_pre |   dS_wf |   dS_hold |   pre_mean |   hold_mean |   tpw |
|:------|:----------|---------:|--------:|----------:|-----------:|------------:|------:|
| CH2   | DEAD      |     0.02 |    0.02 |      0.01 |     641.29 |     1316.3  |  2.32 |
| CH2.5 | DEAD      |     0.13 |    0.06 |     -0.01 |    2671.48 |     1068.44 |  2.32 |
| CH3   | DEAD      |     0.21 |    0.17 |      0.13 |    3870.09 |     3088.82 |  2.32 |

#### DR5m_pb1_rm0.5 scale-out (basis T)

| b         | verdict   |   dS_pre |   dS_wf |   dS_hold |   pre_mean |   hold_mean |   tpw |
|:----------|:----------|---------:|--------:|----------:|-----------:|------------:|------:|
| SO33_0.5  | DEAD      |     0.12 |    0.08 |      0.03 |    1987.04 |     1802.27 |  4.63 |
| SO33_0.75 | CANDIDATE |     0.28 |    0.18 |      0.09 |    4800.57 |     3130.79 |  4.63 |
| SO33_1    | CANDIDATE |     0.31 |    0.22 |      0.12 |    5621.07 |     3925.92 |  4.63 |
| SO50_0.5  | DEAD      |     0.12 |    0.08 |      0.04 |    1934.41 |     1614.03 |  4.63 |
| SO50_0.75 | DEAD      |     0.25 |    0.17 |      0.08 |    4283.06 |     2775.05 |  4.63 |
| SO50_1    | CANDIDATE |     0.29 |    0.2  |      0.11 |    5190.71 |     3573.28 |  4.63 |

#### DR5m_pb1_rm0.5 height multiples (basis T)

| b     | verdict   |   dS_pre |   dS_wf |   dS_hold |   pre_mean |   hold_mean |   tpw |
|:------|:----------|---------:|--------:|----------:|-----------:|------------:|------:|
| OH0.5 | DEAD      |     0.1  |    0.17 |      0.25 |    1582.63 |     5017.71 |  2.32 |
| OH1   | DEAD      |     0.1  |    0.23 |      0.36 |    2238.96 |     6489.77 |  2.32 |
| OH1.5 | DEAD      |     0.15 |    0.22 |      0.28 |    3677.29 |     6636.09 |  2.32 |
| OH2   | DEAD      |     0.2  |    0.27 |      0.33 |    4889.63 |     8242.71 |  2.32 |
| OH3   | DEAD      |     0.37 |    0.32 |      0.27 |    8588.29 |     7678.01 |  2.32 |

#### DR5m_pb1_rm0.5 ATR20 multiples (basis T)

| b      | verdict   |   dS_pre |   dS_wf |   dS_hold |   pre_mean |   hold_mean |   tpw |
|:-------|:----------|---------:|--------:|----------:|-----------:|------------:|------:|
| AT0.25 | CANDIDATE |     0.21 |    0.18 |      0.14 |    5130.92 |     3890.73 |  2.32 |
| AT0.5  | DEAD      |     0.4  |    0.3  |      0.2  |    9484.88 |     7019.15 |  2.32 |
| AT0.75 | PASS      |     0.4  |    0.33 |      0.25 |   10253.8  |     8621.99 |  2.32 |
| AT1    | PASS      |     0.36 |    0.31 |      0.25 |    9676.66 |     9172.6  |  2.32 |


## 2. 3.10 / 3.11 confirmations (prereg CONF, master sha256 dab61169...; 8 groups, 160 cells, 8 holdout looks)
Rules (side-aligned, tape rows <= arrival-1): D0 / D3 delta share over 180 s > 0 / >= +0.03 (NT8-ticks), I10 5-level book imbalance >= +0.1, O0 OFI over 10 s > 0 (EXEC-ONLY L2), D0I10 both; the directive's 60/70% one-sided delta never occurs at the open (0 of 432 events). Result: 0 PASS, 2 CANDIDATE (DR5m_pb1_rm0.5 + D0 with F60 and SCALE), 158 DEAD. The confirmation keeps 35-65% of the trades; weekly P&L is NOT improved over the unconfirmed parent (D0+F60: PRE +5.2k vs parent +5.3k $/wk, stack d_Sharpe WF 0.20 vs 0.245): honest-null reading: a filter that removes trades without adding weekly dollars; per-trade means rise, the weekly stack effect does not. Book-based rules (I10, O0) and the combined rule have median stack d_Sharpe 0.03-0.12 over the grid, no cell beats its parent. The delta cells that leave < 30 PRE trades fail min_n by design.

## 3. Block (iv): 09:29 classifier with V2 guards + gated P&L (prereg CLS0929 sha256 32d9422b...; 1 holdout look)
Target dir30_0930 (+30 before -30 to 11:00), 48 numeric 09:29 features, LightGBM / logistic, monthly walk-forward, 7-day embargo, isotonic on the last 20%, 8 noise columns, 100-permutation null, no-volume control. PRE: AUC 0.483 [0.42,0.54] (LGB), 0.486 (LR), 0.518 (no-volume); permutation p = 0.50; noise-column importance (0.067 max) above the best real feature (0.056); calibration slope -0.25; hit rate at P >= 0.55 / 0.60: 0.481 / 0.496 (no better than a coin). HOLD (read once after the logged look): AUC 0.448 / 0.490 / 0.456, hit 0.469 / 0.422 at >= 0.55 / 0.60 for LGB. No skill: DEAD. Gated P&L (calibrated P that the trade side wins >= 0.55 / 0.60) on DR5m_pb3_rm0.5 {F60,T1200,HOLD,SCALE}, DR5m_pb1_rm0.5 {F60,T1200}, OR3m_c1 and DR15m_pb3_mv10 {F60,T1200}: PRE gated minus ungated per trade is negative for all four DR5m_pb3 brackets (-7.6 to -22.6 pts, CIs include 0 except DR5m_pb1 F60 at 0.55: -17.6 [-31.0,-3.9]), positive but inside noise for OR3m_c1 / DR15m T1200 (+5 to +28 pts, CI includes 0), and the HOLD signs are mixed on 12-81 gated trades (a few CI above 0 at 12-17 trades, PRE sign opposite): the classifier is not a predictor and the gate is not an edge. The opening-type target (4-class) was not scored (disclosed). Opening-type / pre-open interaction tables (every pre-open feature as a tercile or side-aligned column with CIs) are inside each variant result (`cond`), summarised in DS3_OPEN_B2_OR_DRIVE.md section 4/7; D3O4 pmxa_cond tables were not duplicated.

## 4. DR5m cluster: concurrency with the live stack, capacity, cost check
- Concurrency replay (`o2_conc.py`, `conc.json`; post-lock exits of ST10, HM10, WT7, KB, SM, PB with the DS3 weights, live windows, WF trades): gross stack lots open during the candidate's holds: median 0-10, p95 32-37, max 45-48; with the candidate's 10 lots the 50-lot cap is exceeded on 2.4-2.7% of trades (max 55-58 lots). Capping the candidate to the remaining room costs 4.7% of its WF P&L (60/75), 3.5% (T1200), 6.4% (HOLD): the cap barely binds. Margin: no margin schedule on disk; the 5%-of-notional proxy gives about $1.2M at the 57-lot peak against the $700k account (flag for the lead; the broker intraday margin must be checked before any sizing).
- Cost check (NOT a direct replay: `o2_walk.py`): walking 10 lots through the 1-s 10-level book at the arrival second for the 432 DR5m_pb3 entries: extra 1.27 ticks beyond the touch at entry (p50 1.2, p90 2.0; 09:35-09:39 1.34, 09:40-09:44 1.18, 09:45-09:59 1.22) and 1.00 ticks at a 15:59:59 market exit (p90 1.8): about $113 per round trip at 10 lots, about $263/wk for the HOLD cell, well inside the harness friction (0.5 pt RT = $100 + commission) and the cell's +5k to +9k/wk. A real direct replay was not launched (the replay orchestrator open_direct.py is a block (iii)+ item for the lead's replay queue; I did not start replay workers). The static snapshot ignores hidden size and queue effects: treat as a lower bound.

## 5. Addendum: secondary best-of-N column for block (ii): see DS3_OPEN_B2_OR_DRIVE.md section 10 (all 10 block-(ii) CANDIDATEs FAIL it).

## 6. Deviations and disclosures
Block (iii) uses `X{S}_{T}` / TM / CH / SO / OH / AT bracket grammar added to the harness (o2_gen.legs); TM exits earlier than the entry are marked invalid; per-group text for B3GRID says "12 core brackets" in its template line (the master lists the real 112-cell chunks). Signals DR5m_* were included by the lead's instruction, not by PRE rank. The classifier thresholds follow the prereg; the 4-class opening-type target was not run. CONF delta thresholds were changed from the directive's 60/70% to >0 / >=0.03 BEFORE scoring because the directive's thresholds never fire. Placebo (b) events for confirmation variants drop out when the arrival is after 12:00 (tape end). No replay workers, no live files, no deletions.
