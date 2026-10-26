# DS3 PRO3 - T-PULLBACK PRO P4 (trend quality) and P8 (context families)

Generated 2026-10-26T18:42:55Z. Research only. Preregs: l2vast/ds3/prereg/PRO3_PRO3A.md (19 cells, sha256 69818f8a...cdc3), PRO3_PRO3B.md (26 cells, sha256 3183654f...f22); a first PRO3A prereg line (sha 6f698ae2...) carried a placeholder header by a driver slip and was superseded before any scoring (DECISIONS.md; ledger counts those 19 cells twice). Ledger: +19 +26 +17 (interaction tests) +19 (slip). Pre-holdout text: autopilot/DS3_PRO3_PREHOLD.md (holdout look + second-holdout look logged under track DS3_PRO3, one look). DS2 bracket and execution fixed; MAPPED pricing for all 45 cells (3 had <25 trades and were not run); DIRECT L2 replay of the 10 selected cells (4 PASS/CANDIDATE + top 10 by mapped holdout Sharpe) is RUNNING at the time of this text (2 workers, memory-limited; ~45 monthly files); section 4 is filled in when it finishes.

## Verdict line
PRO3 (mapped): 2 PASS, 2 CANDIDATE, 41 DEAD of 45. PASS: PRO3A_VOL, PRO3A_REL. CANDIDATE: PRO3A_X30, PRO3A_P3. All P8 context families are DEAD or UNDERPOWERED. Best-of-N honesty: the 4 survivors are the best of 19 overlapping filters of one base cell (best-of-19 within the P4 test, N=45 in the track, ~35.5k cumulative ledger); each survivor is a SUBSET of the base cell's trades, so their agreement with each other is mechanical.

## Key findings
1. The pullback entry itself carries the paired edge vs ST10 (about +10 to +12 pt/trade, CI excluding 0 at MDE 6-8 pt, in every P4 slice that has >100 pairs, including the base cell); the P4 conditions do NOT move it: paired vs the BASE cell the delta is -1.4..+0.9 pt/trade with MDE 0.3-2.3 pt for all 19 filter cells except a few small slices (dBase column). The filters change the standalone level (which trades survive the one-trade-at-a-time book and the locks), not the per-trade quality relative to the unfiltered pullback.
2. Interaction regression (OLS, 17 indicators, PRE-fitted, session-block bootstrap) on the paired delta: on the base cell no coefficient excludes 0 at 95%; in the 43-cell ST10 pool 3 of 17 do (I20 impulse>=2 ATR +9.7 pt, D62 shallow pullback -7.3 pt, R60 R2>=0.6 -5.5 pt) which is about what 17 tests give by chance (0.85 expected) and the signs are not stable out of sample (HOLD re-fit sign agreement 24% for the pool, 29% for the base; PRE-fit predictions correlate -0.003 / -0.03 with HOLD paired delta). On net $/trade REL (NQ pulled back less than ES) is +3.9 pt (CI 1.4..6.3) in the pool and +8.9 (2.9..14.7) on the base, and VOL (healthy retrace volume) +7.4 (1.1..13.7) on the base; those are the two PASS cells. LightGBM with grouped CV has out-of-sample R2 around 0 (-0.23..+0.03) with noise-column-level permutation importances: no tree-detectable interaction. Verdict: no condition is established as moving the paired delta; REL and VOL are the only ones with a PRE net-per-trade signal and they also hold in HOLD and SPAN2 for the cells.
3. Contexts (P8): opening, gap-and-go, news, end-of-day are 2-4 trades/wk or fewer (LOW-FREQUENCY, never dropped) and none passes; 02:00 and 18:00 openings and all news cells have negative PRE/HOLD means; the 09:30 DRV38 cell has positive PRE/HOLD/WF (+$5.5k/wk WF, 2.9 trades/wk, CI includes 0) but fails SPAN2 (-$1.6k) and the 3/wk bar: DEAD under the rule, flagged as a lead worth a longer sample. News cells: 16-95 events total, UNDERPOWERED, MDE far above any effect.
4. Cross-asset: 'ES holds' (NQ pulling back alone) is NEGATIVE (EMA5 -$3.4k PRE, EMA1 -$0.6k) and 'both pull back' is positive but not significant (WF +$6.2k and +$8.7k, CI includes 0, placebo rank .82/.75): the opposite of the P8/P4 hypothesis that leader-led dips resume more often. REL (NQ pulled back less than ES over 60 bars) is positive as a P4 net condition though; the two measure different things (REL is a % drawdown difference at the signal bar, XA uses ES drawdown in ES-ATR units).

## 1. All cells (MAPPED, 10 lots, DS2 bracket/locks; $/wk; tpw = trades/wk WF; < 3 = LOW-FREQUENCY; plc/condnull = placebo and conditioning-null rank on PRE; MDE weekly WF about $8-13k at SD 30-56k)

| cell                    | verdict   | failed                                               |   tpw_wf |      pre |     hold |    span2 |       wf |   wf_ci_lo |   hold_sh |   plc_raw |   condnull |    x2_wf | pairST (pts, WF)                | pairBase (pts, WF)                |
|:------------------------|:----------|:-----------------------------------------------------|---------:|---------:|---------:|---------:|---------:|-----------:|----------:|----------:|-----------:|---------:|:--------------------------------|:----------------------------------|
| PRO3A_A1                | DEAD      | WF_CI>0,HOLD>0                                       |    12.62 |  7027.22 | -2738.02 |  3649.17 |  2364.46 |   -4336.72 |     -0.47 |      0.95 |       1    |  1026.3  | 7.2 [2.9,11.7] n=297 MDE 6.3    | -0.1 [-0.7,0.4] n=1143 MDE 0.8    |
| PRO3A_A2                | DEAD      | PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0        |    10.47 | -2148.03 |  -762.21 | -2542.9  | -1494.37 |   -7860.49 |     -0.14 |      0.35 |       0.15 | -2431.89 | 10.3 [4.2,16.9] n=161 MDE 9.0   | 0.9 [0.1,1.9] n=484 MDE 1.3       |
| PRO3A_A3                | DEAD      | WF_CI>0,plc>=.95                                     |    18.83 |   745.93 |  9500.04 |  1686.64 |  4975.16 |   -3204.62 |      1.41 |      0.6  |       0.2  |  2222.05 | 9.1 [5.2,12.9] n=459 MDE 5.7    | -0.3 [-0.7,0.0] n=1759 MDE 0.5    |
| PRO3A_X20               | DEAD      | WF_CI>0,HOLD>0                                       |    22.1  |  8790.9  | -1374.66 |  1641.7  |  3947.32 |   -4468.81 |     -0.17 |      0.98 |       0.98 |  1339.98 | 7.9 [4.7,11.2] n=632 MDE 4.6    | 0.0 [-0.3,0.4] n=2718 MDE 0.5     |
| PRO3A_X25               | DEAD      | WF_CI>0,SPAN2>0                                      |    18.2  |  8981.12 |  1383.28 | -2864.56 |  5377.83 |   -2056.71 |      0.21 |      1    |       1    |  3266.97 | 8.6 [4.9,12.6] n=524 MDE 5.6    | 0.0 [-0.2,0.4] n=2091 MDE 0.4     |
| PRO3A_X30               | CANDIDATE | plc>=.95                                             |    13.26 |  7389.72 |  7712.8  |    41.18 |  7597.29 |    1032.82 |      1.41 |      0.92 |       1    |  5240.57 | 9.5 [5.0,14.3] n=371 MDE 6.6    | 0.1 [-0.2,0.4] n=1494 MDE 0.5     |
| PRO3A_TS3               | DEAD      | WF_CI>0,SPAN2>0,plc>=.95                             |    21.86 |  4186.41 |  3187.73 | -2473.53 |  3733.8  |   -3608.03 |      0.46 |      0.85 |       0.82 |   112.66 | 9.6 [6.3,12.8] n=616 MDE 4.6    | -0.0 [-0.4,0.3] n=2433 MDE 0.5    |
| PRO3A_R60               | DEAD      | WF_CI>0,SPAN2>0,plc>=.95                             |    16.78 |  5864.41 |  7553.45 | -5982.47 |  6720.42 |    -374.8  |      1.38 |      0.88 |       0.95 |  3925.55 | 9.1 [5.9,12.7] n=406 MDE 4.9    | -0.2 [-0.7,0.2] n=1686 MDE 0.6    |
| PRO3A_I10               | DEAD      | WF_CI>0,plc>=.95                                     |    24.36 |  3129.6  |  3237.56 |  1006.68 |  3203.58 |   -5873.43 |      0.37 |      0.85 |       0.6  |   781.94 | 9.5 [6.6,12.4] n=722 MDE 4.1    | 0.1 [-0.1,0.2] n=3269 MDE 0.2     |
| PRO3A_I15               | DEAD      | WF_CI>0,plc>=.95                                     |    23.8  |  2581.12 |  4306.02 |  1243.43 |  3431.46 |   -5619.69 |      0.51 |      0.72 |       0.52 |   677.57 | 9.9 [6.8,12.9] n=686 MDE 4.3    | -0.1 [-0.3,0.1] n=2990 MDE 0.3    |
| PRO3A_I20               | DEAD      | PRE>0,WF_CI>0,plc>=.95,x2_WF>0                       |    22.94 |   -90.95 |   956.77 |  1684.34 |   413.96 |   -7509.21 |      0.13 |      0.65 |       0.15 | -2245.84 | 9.7 [6.9,12.5] n=642 MDE 4.1    | -0.1 [-0.4,0.2] n=2590 MDE 0.4    |
| PRO3A_D62               | DEAD      | WF_CI>0,plc>=.95                                     |    11.86 |  2132.93 |  4677.77 |  3724.6  |  3375.77 |   -3719.41 |      0.81 |      0.85 |       0.8  |  2264.48 | 15.0 [8.8,21.0] n=161 MDE 8.7   | -0.7 [-1.8,0.4] n=583 MDE 1.6     |
| PRO3A_D100              | DEAD      | WF_CI>0,plc>=.95                                     |    19.2  |  5244.88 |  2358.52 |  1274.11 |  3888.84 |   -3152.76 |      0.39 |      0.88 |       0.9  |  1275.86 | 10.7 [7.2,14.1] n=472 MDE 5.0   | -0.1 [-0.6,0.3] n=1641 MDE 0.7    |
| PRO3A_VOL               | PASS      |                                                      |    16.09 | 10171.8  |  6324.35 |   593.32 |  8386.45 |    1253.34 |      0.9  |      1    |       1    |  5749.31 | 10.4 [6.1,15.2] n=336 MDE 6.3   | 0.2 [-0.5,0.8] n=1243 MDE 0.9     |
| PRO3A_P3                | CANDIDATE | WF_CI>0                                              |    18.88 |  6080.06 |  8928.5  |  2221.5  |  7497    |    -134.85 |      1.24 |      0.95 |       0.95 |  5324.44 | 9.0 [5.3,12.8] n=518 MDE 5.3    | -0.1 [-0.4,0.3] n=2143 MDE 0.5    |
| PRO3A_P2                | DEAD      | PRE>0,WF_CI>0,plc>=.95                               |    22.59 |  -548.52 |  9597.44 |   842.1  |  4343.25 |   -4540.49 |      1.15 |      0.52 |       0.1  |  1924.6  | 9.7 [6.2,13.1] n=655 MDE 4.7    | -0.0 [-0.3,0.3] n=2796 MDE 0.4    |
| PRO3A_REL               | PASS      |                                                      |    14.9  |  5712.63 |  9937.04 |   374.1  |  7790.93 |     326.52 |      1.55 |      1    |       0.98 |  5813.3  | 13.1 [8.3,18.3] n=257 MDE 7.3   | 0.0 [-0.8,0.9] n=969 MDE 1.2      |
| PRO3A_A1X25             | DEAD      | WF_CI>0,HOLD>0                                       |     8.97 |  5327.33 |  -348.5  |  3948.52 |  2625.9  |   -2765.38 |     -0.07 |      0.98 |       0.95 |  1865.93 | 8.0 [2.8,13.0] n=223 MDE 7.5    | -0.2 [-0.9,0.5] n=852 MDE 0.9     |
| PRO3A_A1P3              | DEAD      | WF_CI>0,HOLD>0                                       |     8.02 |  9728.36 | -2396.35 |  5790.99 |  3946    |   -1147.35 |     -0.55 |      1    |       1    |  3131.03 | 5.5 [-0.4,11.3] n=187 MDE 8.7   | -0.0 [-0.7,0.6] n=720 MDE 1.0     |
| PRO3B_OPEN0930_VWAP_T1  | DEAD      | tpw>=3,WF_CI>0,SPAN2>0,plc>=.95                      |     2.08 |  1520.73 |   515.68 |  -865.49 |  1046.41 |   -1658.61 |      0.27 |      0.85 |     nan    |   794.92 | 17.9 [6.4,28.7] n=77 MDE 16.0   | 4.6 [-5.5,13.7] n=81 MDE 13.9     |
| PRO3B_OPEN0930_EMA1_T1  | DEAD      | WF_CI>0,plc>=.95                                     |     3.98 |  3207.36 |  1652.73 |  1677.6  |  2479.66 |   -1231.65 |      0.59 |      0.92 |     nan    |  1999.52 | 5.8 [-0.6,12.1] n=167 MDE 9.2   | -17.9 [-26.8,-8.5] n=96 MDE 13.1  |
| PRO3B_OPEN0930_DRV38_T1 | DEAD      | tpw>=3,SPAN2>0                                       |     2.95 |  5622.66 |  5215.72 | -1566.48 |  5465.63 |    2050.7  |      1.87 |      1    |     nan    |  4882.3  | 5.2 [-2.3,13.9] n=126 MDE 11.3  | -29.9 [-43.3,-17.7] n=59 MDE 18.2 |
| PRO3B_OPEN0930_EMA1_T2  | DEAD      | tpw>=3,WF_CI>0,HOLD>0                                |     2.96 |  3931.16 |  -650.97 |  1195.78 |  1747.69 |   -1268.58 |     -0.24 |      0.98 |     nan    |  1400.63 | -3.0 [-11.7,4.9] n=125 MDE 11.5 | -37.4 [-50.9,-25.3] n=58 MDE 18.0 |
| PRO3B_OPEN1800_EMA1_T1  | DEAD      | tpw>=3,WF_CI>0,HOLD>0,SPAN2>0                        |     2.95 |  3878.26 | -3414.16 | -3323.03 |   386.66 |   -3112.64 |     -1.09 |      0.98 |     nan    |   145.69 | 6.6 [-1.4,16.3] n=61 MDE 12.5   |                                   |
| PRO3B_OPEN1800_DRV38_T1 | DEAD      | tpw>=3,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0       |     2.26 |   167.59 | -1794.09 | -1707.1  |  -777.79 |   -3636.91 |     -0.67 |      0.62 |     nan    |  -939.49 | 1.1 [-8.3,11.9] n=49 MDE 14.3   |                                   |
| PRO3B_OPEN0200_EMA1_T1  | DEAD      | tpw>=3,PRE>0,WF_CI>0,plc>=.95,x2_WF>0                |     2.75 | -5543.83 |   474.16 |  2146.09 | -2678.81 |   -5552.14 |      0.19 |      0    |     nan    | -2824.75 | 5.7 [-5.1,17.0] n=41 MDE 16.3   |                                   |
| PRO3B_OPEN0200_DRV38_T1 | DEAD      | tpw>=3,PRE>0,WF_CI>0,plc>=.95,x2_WF>0                |     2.17 | -2893.83 |  1145.83 |  2636.01 |  -964.86 |   -3682.67 |      0.53 |      0.08 |     nan    | -1152.1  |                                 |                                   |
| PRO3B_GAP0.5_VWAP_T1    | DEAD      | tpw>=3,PRE>0,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0         |     0.78 |  -240    | -1521.22 |   645.58 |  -859.89 |   -2361    |     -1.07 |      0.5  |     nan    |  -880.62 |                                 |                                   |
| PRO3B_GAP0.5_VWAP_T2    | DEAD      | tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 |     0.57 | -1267.51 |   -47.21 |  -920.52 |  -687.56 |   -2014.27 |     -0.03 |      0.02 |     nan    |  -703.78 |                                 |                                   |
| PRO3B_GAP1.0_VWAP_T1    | DEAD      | tpw>=3,WF_CI>0,plc>=.95                              |     0.22 |   127.39 |   142.18 |   254.75 |   135.42 |    -658.95 |      0.17 |    nan    |     nan    |   103    |                                 |                                   |
| PRO3B_GAP1.0_VWAP_T2    | DEAD      | too few trades (<25)                                 |     0    |   nan    |   nan    |   nan    |   nan    |     nan    |    nan    |    nan    |     nan    |   nan    |                                 |                                   |
| PRO3B_NEWS0830_EMA1_T1  | DEAD      | tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 |     0.38 |  -501.85 |  -668.24 | -2149.72 |  -585.65 |   -1772.26 |     -0.73 |      0.25 |     nan    |  -583.88 |                                 |                                   |
| PRO3B_NEWS0830_DRV38_T1 | DEAD      | tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 |     0.23 |  -312.16 |  -822.08 | -1394.14 |  -560.39 |   -1437.7  |     -1.07 |      0.38 |     nan    |  -533.37 |                                 |                                   |
| PRO3B_NEWS1400_EMA1_T1  | DEAD      | too few trades (<25)                                 |     0    |   nan    |   nan    |   nan    |   nan    |     nan    |    nan    |    nan    |     nan    |   nan    |                                 |                                   |
| PRO3B_NEWS1400_DRV38_T1 | DEAD      | too few trades (<25)                                 |     0    |   nan    |   nan    |   nan    |   nan    |     nan    |    nan    |    nan    |     nan    |   nan    |                                 |                                   |
| PRO3B_NEWSALL_EMA1_T1   | DEAD      | tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 |     0.48 |  -354.27 | -1483.07 | -2439.24 |  -901.41 |   -2178.71 |     -1.5  |      0.42 |     nan    |  -879.75 | 17.7 [4.7,33.9] n=31 MDE 21.3   |                                   |
| PRO3B_NEWSALL_DRV38_T1  | DEAD      | tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 |     0.3  |  -177.08 | -1311.47 | -1683.66 |  -725.68 |   -1830.12 |     -1.45 |      0.42 |     nan    |  -696.12 |                                 |                                   |
| PRO3B_EOD_EMA5_T1       | DEAD      | tpw>=3,WF_CI>0,SPAN2>0,plc>=.95                      |     2.28 |   912.74 |   248.49 |    -8.56 |   598.61 |   -1779.23 |      0.13 |      0.8  |     nan    |   189.18 |                                 | 1.4 [-0.7,4.2] n=101 MDE 3.5      |
| PRO3B_EOD_EMA5_T2       | DEAD      | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95                |     1.68 |  -354.57 |  1364.37 |  -991.79 |   472.37 |   -1426.04 |      0.91 |      0.52 |     nan    |   158.03 |                                 | -15.4 [-24.0,-7.7] n=68 MDE 11.8  |
| PRO3B_EOD_VWAP_T1       | DEAD      | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95,x2_WF>0        |     0.57 | -1069.17 |   979.41 |  -401.79 |   -88.17 |   -1293.33 |      0.85 |      0.08 |     nan    |  -162.36 |                                 |                                   |
| PRO3B_EOD_VWAP_T2       | DEAD      | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95                |     0.4  |  -461.01 |   680.71 |   -89.83 |    86.67 |    -950.51 |      0.63 |      0.28 |     nan    |    31.73 |                                 |                                   |
| PRO3B_XA_hold_EMA5      | DEAD      | PRE>0,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0                |     8.99 | -3352    | -4781.81 |  5732.94 | -4065.35 |   -8901.87 |     -1.13 |      0.22 |       0.08 | -4859.44 | 8.4 [3.6,14.4] n=122 MDE 7.9    | -2.4 [-4.7,-0.4] n=375 MDE 3.0    |
| PRO3B_XA_pull_EMA5      | DEAD      | WF_CI>0,plc>=.95                                     |    23.26 |  4910.6  |  7500.16 |  3852.73 |  6194.45 |   -3476.39 |      0.84 |      0.82 |       0.85 |  3339.83 | 9.4 [6.3,12.4] n=676 MDE 4.5    | 0.5 [0.2,0.8] n=2693 MDE 0.5      |
| PRO3B_XA_hold_EMA1      | DEAD      | PRE>0,WF_CI>0,plc>=.95                               |    23.04 |  -616.85 |  9778.91 |  1545.28 |  4394.97 |   -4749.42 |      1.09 |      0.62 |       0.05 |  2066.38 | -1.3 [-3.7,1.2] n=616 MDE 3.5   | -2.8 [-4.1,-1.5] n=1146 MDE 1.9   |
| PRO3B_XA_pull_EMA1      | DEAD      | WF_CI>0,plc>=.95                                     |    26.26 |  4423.04 | 13160.9  |  8226.84 |  8670.14 |    -956.49 |      1.55 |      0.88 |       0.75 |  4812.82 | 4.4 [2.5,6.4] n=1072 MDE 2.8    | 0.4 [-0.4,1.1] n=1692 MDE 1.0     |

## 2. Interaction table (P4), PRE-fitted
Coefficient = change in pt per 10-lot trade (1 pt = $200) when the condition is true, others held; 95% session-block bootstrap CI; 'oos' columns re-estimate the same model in HOLD (coef and CI) as a once-only out-of-sample sign check.

### pool base, outcome paired_delta_pts (n_fit 326; HOLD n 414, corr(PRE-fit pred, HOLD actual) -0.031, HOLD sign agreement 0.29; SPAN2 corr 0.067)

| cond   |   coef |     lo |    hi |   p_pos | excl0   |   n_true |   uni_diff |   HOLD_coef |   HOLD_lo |   HOLD_hi |
|:-------|-------:|-------:|------:|--------:|:--------|---------:|-----------:|------------:|----------:|----------:|
| const  |   7.73 |  -5.63 | 22.3  |    0.87 | False   |      nan |     nan    |       -4.56 |    -20.24 |      9.91 |
| A1     |   1.76 |  -7.16 | 10.89 |    0.64 | False   |      112 |      -2.22 |       -8.31 |    -17.28 |     -0.77 |
| A2     |   1.34 |  -6.52 |  9.26 |    0.62 | False   |       41 |      -2.96 |        8.93 |     -0.77 |     19.8  |
| A3     |   4.63 |  -2.63 | 12.08 |    0.89 | False   |      173 |       3.32 |       -5.18 |    -12.12 |      1.93 |
| X20    |  -5.03 | -17.82 |  8.21 |    0.22 | False   |      260 |       0.64 |        2.16 |    -12.67 |     18.69 |
| X25    |   3.56 | -12.99 | 19.95 |    0.67 | False   |      204 |       2.54 |       -9.95 |    -23.04 |      3.48 |
| X30    |   0.48 | -14.52 | 14.3  |    0.52 | False   |      155 |       1.87 |        3.68 |     -7.22 |     14.15 |
| TS3    |  10.24 |  -3.26 | 24.84 |    0.93 | False   |      241 |       4.94 |        7.38 |     -5.57 |     20.46 |
| R60    |  -6.88 | -18.09 |  4.88 |    0.12 | False   |      149 |      -1.87 |        3.64 |     -6.07 |     13.81 |
| I10    |  -2.63 | -28.33 | 21.67 |    0.43 | False   |      304 |       1.99 |       -3.16 |    -20.51 |     17.01 |
| I15    |  -3.82 | -31.49 | 26.38 |    0.39 | False   |      282 |       3.61 |       20.77 |     -2.11 |     43.64 |
| I20    |  10.6  |  -6.01 | 26.74 |    0.89 | False   |      256 |       5.83 |      -17.72 |    -40.63 |      4.07 |
| D62    |  -1.79 | -17.79 | 15.54 |    0.41 | False   |       36 |       1.21 |       22.24 |      6.21 |     40.03 |
| D100   |  -3.75 | -15.87 |  7.56 |    0.27 | False   |      169 |       0.44 |       10.92 |     -0.33 |     21.25 |
| VOL    |  -2.71 | -11.14 |  6.04 |    0.28 | False   |       92 |      -2.44 |        4.95 |     -5.42 |     13.66 |
| P3     |   2.72 |  -7.96 | 12.57 |    0.71 | False   |      205 |       0.5  |       -4.94 |    -14.31 |      3.28 |
| P2     |  -5.9  | -19.81 |  8.58 |    0.2  | False   |      268 |      -2.84 |        4.85 |    -10.73 |     19.4  |
| REL    |   4.48 |  -5.04 | 14.67 |    0.81 | False   |       84 |       3.29 |        6.02 |     -2.59 |     14.34 |

### pool base, outcome net_pts (n_fit 1621; HOLD n 1911, corr(PRE-fit pred, HOLD actual) -0.003, HOLD sign agreement 0.47; SPAN2 corr -0.025)

| cond   |   coef |     lo |    hi |   p_pos | excl0   |   n_true |   uni_diff |   HOLD_coef |   HOLD_lo |   HOLD_hi |
|:-------|-------:|-------:|------:|--------:|:--------|---------:|-----------:|------------:|----------:|----------:|
| const  | -16.04 | -26.02 | -6.08 |    0    | True    |      nan |     nan    |        3.48 |     -4.76 |     12.2  |
| A1     |  -1.29 |  -6.82 |  4.08 |    0.33 | False   |      549 |       5.12 |       -1.58 |     -6.49 |      3.23 |
| A2     | -10.43 | -16.73 | -3.53 |    0    | True    |      227 |      -7.18 |        0.49 |     -5.03 |      6.45 |
| A3     |  -4.33 |  -9.19 |  0.61 |    0.04 | False   |      845 |      -1.13 |        4.57 |      0.1  |      9.2  |
| X20    |   7.09 |  -2    | 16.06 |    0.93 | False   |     1320 |       9.58 |       -2.61 |    -10.27 |      5.41 |
| X25    |  -0.32 |  -9.55 |  8.73 |    0.48 | False   |     1044 |       6.08 |       -3.22 |    -11.31 |      4.54 |
| X30    |   1.36 |  -6.14 |  9.15 |    0.65 | False   |      763 |       5.29 |        3.73 |     -3.29 |     10.71 |
| TS3    |  -1.11 |  -8.95 |  6.19 |    0.38 | False   |     1191 |       4.35 |       -2.05 |     -9.82 |      5.33 |
| R60    |   4.34 |  -2.36 | 10.54 |    0.9  | False   |      815 |       6    |        5.53 |     -0.28 |     11.16 |
| I10    |   6.7  |  -8.06 | 21.85 |    0.81 | False   |     1504 |      10.04 |       -5.03 |    -20.09 |      8.81 |
| I15    |   7.12 |  -7.31 | 21.03 |    0.84 | False   |     1400 |       6.61 |       -0.23 |    -13.02 |     13.45 |
| I20    |  -6.94 | -17.45 |  3.91 |    0.09 | False   |     1239 |       0.69 |       -0.65 |     -9.85 |      8.77 |
| D62    |   4.52 |  -6.3  | 15.64 |    0.77 | False   |      238 |       1.92 |       -1.5  |    -10.01 |      6.59 |
| D100   |   1.7  |  -5.54 |  8.79 |    0.68 | False   |      797 |       0.69 |       -1.76 |     -8.21 |      4.62 |
| VOL    |   7.44 |   1.11 | 13.72 |    0.99 | True    |      505 |       7.29 |        2.69 |     -2.29 |      7.36 |
| P3     |   6.83 |  -0.46 | 13.84 |    0.96 | False   |     1053 |       4.89 |       -2.42 |     -9.19 |      4.45 |
| P2     |  -5.54 | -14.06 |  4.02 |    0.12 | False   |     1365 |       0.43 |        3.75 |     -3.45 |     11.55 |
| REL    |   8.87 |   2.94 | 14.73 |    1    | True    |      462 |       7.67 |        2.56 |     -4.2  |      8.69 |

GBM base/paired_delta_pts: grouped-CV OOS R2 [-0.026, -0.195, -0.113, -0.029, -0.229]; permutation importance (MSE increase) {"age": -19.73, "adx": -36.12, "t": 5.66, "r2": -17.3, "imp_atr": -22.42, "dep_frac": -12.76, "vol_ratio": 7.13, "agree": -2.31, "relstr": 24.65, "dd_es_atr": 5.7, "noise": -6.68}

GBM base/net_pts: grouped-CV OOS R2 [-0.033, -0.024, 0.029, -0.03, -0.04]; permutation importance (MSE increase) {"age": -2.7, "adx": -14.23, "t": 4.56, "r2": 7.31, "imp_atr": 13.89, "dep_frac": 23.65, "vol_ratio": 55.11, "agree": -5.1, "relstr": 58.01, "dd_es_atr": -16.27, "noise": -9.7}

### pool ST10pool, outcome paired_delta_pts (n_fit 10582; HOLD n 12779, corr(PRE-fit pred, HOLD actual) -0.003, HOLD sign agreement 0.24; SPAN2 corr 0.013)

| cond   |   coef |     lo |    hi |   p_pos | excl0   |   n_true |   uni_diff |   HOLD_coef |   HOLD_lo |   HOLD_hi |
|:-------|-------:|-------:|------:|--------:|:--------|---------:|-----------:|------------:|----------:|----------:|
| const  |  -1.67 |  -8.56 |  5.85 |    0.33 | False   |      nan |     nan    |       -0.35 |     -7.91 |      8.12 |
| A1     |   3.61 |  -1.25 |  8.96 |    0.92 | False   |     2362 |       2.92 |        1.77 |     -4.53 |      7.62 |
| A2     |   1.67 |  -4.57 |  8.1  |    0.7  | False   |     1089 |       0.26 |        8.94 |      1.87 |     16.06 |
| A3     |   1.67 |  -2.73 |  6.03 |    0.77 | False   |     4793 |       0.72 |        0.43 |     -4.83 |      5.39 |
| X20    |  -1.34 |  -6.88 |  4.57 |    0.3  | False   |     8775 |      -0.24 |        0.73 |     -4.74 |      6.37 |
| X25    |   1.12 |  -5.11 |  6.79 |    0.65 | False   |     6889 |      -0.03 |       -2.83 |     -8.62 |      3.73 |
| X30    |   0.12 |  -5.01 |  5    |    0.51 | False   |     4988 |      -0.57 |        2.99 |     -2.36 |      8.25 |
| TS3    |   2.47 |  -2.6  |  7.65 |    0.82 | False   |     7648 |       0.82 |       -0.05 |     -5.62 |      5.53 |
| R60    |  -5.47 | -10.29 | -0.78 |    0.01 | True    |     4624 |      -3.24 |        0.44 |     -3.05 |      4.39 |
| I10    |   6.81 |  -1.53 | 14.91 |    0.95 | False   |     9921 |       4.37 |       -1.25 |    -10    |      5.64 |
| I15    |  -5.26 | -13.42 |  2.75 |    0.11 | False   |     9446 |       2    |        5.26 |     -3.49 |     15.28 |
| I20    |   9.66 |   3.04 | 16.04 |    1    | True    |     8866 |       3.3  |       -1.73 |     -9.24 |      5.88 |
| D62    |  -7.27 | -13.04 | -1.84 |    0    | True    |     4949 |      -4.39 |        0.83 |     -4.74 |      6.76 |
| D100   |  -2.74 |  -9.05 |  3.33 |    0.21 | False   |     3101 |       4    |        1.16 |     -4.21 |      6.65 |
| VOL    |  -0.12 |  -3.33 |  3.32 |    0.48 | False   |     2751 |       0.12 |        6.3  |      3    |      9.92 |
| P3     |   2.07 |  -2.4  |  6.67 |    0.82 | False   |     6793 |       1.15 |       -2.17 |     -7.1  |      2.52 |
| P2     |  -0.39 |  -6.54 |  5.39 |    0.43 | False   |     8730 |       0.63 |        0.46 |     -6.03 |      6.42 |
| REL    |   2.42 |  -1.77 |  6.66 |    0.88 | False   |     3024 |       1.51 |       -0.37 |     -3.27 |      2.83 |

### pool ST10pool, outcome net_pts (n_fit 59549; HOLD n 68031, corr(PRE-fit pred, HOLD actual) 0.018, HOLD sign agreement 0.47; SPAN2 corr 0.011)

| cond   |   coef |     lo |    hi |   p_pos | excl0   |   n_true |   uni_diff |   HOLD_coef |   HOLD_lo |   HOLD_hi |
|:-------|-------:|-------:|------:|--------:|:--------|---------:|-----------:|------------:|----------:|----------:|
| const  |  -7.19 | -12.74 | -1.58 |    0    | True    |      nan |     nan    |       -1.74 |     -6.53 |      3.03 |
| A1     |   0.36 |  -3.16 |  3.98 |    0.58 | False   |    14646 |       1.06 |       -2.19 |     -5.06 |      0.73 |
| A2     |  -0.39 |  -4.71 |  4.24 |    0.44 | False   |     7580 |      -0.39 |       -1.85 |     -5.46 |      1.74 |
| A3     |  -0.7  |  -4.87 |  3.63 |    0.37 | False   |    27526 |      -1.31 |        0.96 |     -2.34 |      4.25 |
| X20    |   2.61 |  -0.33 |  5.46 |    0.96 | False   |    45627 |       3.33 |       -0.08 |     -2.55 |      2.73 |
| X25    |  -1.29 |  -4.1  |  1.51 |    0.19 | False   |    34583 |       2.05 |        0.1  |     -2.68 |      2.58 |
| X30    |   0.9  |  -1.73 |  3.45 |    0.75 | False   |    24147 |       2.35 |        2.05 |     -0.48 |      4.73 |
| TS3    |   2.58 |  -0.82 |  5.97 |    0.93 | False   |    34395 |       3.65 |       -0.02 |     -3.04 |      2.71 |
| R60    |   0.47 |  -1.85 |  2.86 |    0.66 | False   |    25799 |       2.34 |        1.29 |     -0.76 |      3.4  |
| I10    |   2.78 |  -0.82 |  6.14 |    0.93 | False   |    54583 |       3.65 |       -1.27 |     -4.21 |      1.96 |
| I15    |   2.05 |  -1.75 |  5.82 |    0.86 | False   |    51122 |       2.32 |        1.1  |     -2.37 |      4.15 |
| I20    |  -3.08 |  -6.11 |  0.05 |    0.03 | False   |    46167 |       0.39 |        0.46 |     -2.16 |      3.36 |
| D62    |   1.31 |  -1.41 |  4.17 |    0.81 | False   |    23917 |       1.31 |        0.35 |     -2.33 |      2.81 |
| D100   |  -0.02 |  -2.35 |  2.31 |    0.49 | False   |    16851 |      -0.46 |       -1.83 |     -4.14 |      0.41 |
| VOL    |   1.67 |  -0.24 |  3.45 |    0.95 | False   |    16853 |       1.55 |        0.82 |     -0.78 |      2.54 |
| P3     |   3.2  |  -0.76 |  7.31 |    0.94 | False   |    32031 |       2.89 |       -1.03 |     -5.05 |      2.52 |
| P2     |  -2.02 |  -6.74 |  3.06 |    0.21 | False   |    43012 |       1.33 |        2.74 |     -1.15 |      7.2  |
| REL    |   3.88 |   1.35 |  6.32 |    1    | True    |    18141 |       3.61 |        2.05 |     -0.47 |      4.18 |

GBM ST10pool/paired_delta_pts: grouped-CV OOS R2 [-0.016, 0.025, 0.013, 0.029, -0.003]; permutation importance (MSE increase) {"age": 6.14, "adx": 4.43, "t": 6.27, "r2": 5.98, "imp_atr": 2.38, "dep_frac": 6.27, "vol_ratio": 7.73, "agree": -0.85, "relstr": 14.77, "dd_es_atr": 49.55, "noise": 0.53}

GBM ST10pool/net_pts: grouped-CV OOS R2 [-0.001, -0.001, 0.003, -0.009, -0.01]; permutation importance (MSE increase) {"age": -5.43, "adx": 3.02, "t": 6.44, "r2": -0.25, "imp_atr": 5.36, "dep_frac": 2.89, "vol_ratio": 0.65, "agree": 0.03, "relstr": 5.79, "dd_es_atr": 0.25, "noise": 0.38}

Conditions are the prereg'd thresholds (A1-A3 age, X20/25/30 ADX, TS3 slope t>=3, R60 R2>=0.6, I10/15/20 impulse ATR, D62/D100 depth bins, VOL pullback/impulse volume<0.8, P3/P2 peers 3-of-3/2-of-3, REL NQ pulled back less than ES). Pool = every T-PULLBACK ST10-regime cell trade list (PB1 ST10 group + PB5 depth/time/fade cells + PB6 grid); PRO1/PRO2 trade lists were not on disk when this ran (their results were not available), so they are NOT in the pool; the pool trades overlap heavily (same entries in many cells), so only the day-block bootstrap CIs are meaningful.

## 3. Survivors (MAPPED) with long/short, quiet/wide, equal risk and DS3 marginal Sharpe

### PRO3A_X30: CANDIDATE (failed: plc>=.95)
cond, {"base": "PB_ST10_EMA5_T1", "cond": "X30"}. 13.3 trades/wk, win 0.525, avg win $11,083 / avg loss $-11,034; PRE $7,390/wk, HOLD $7,713, SPAN2 $41, WF $7,597 CI [1,033,14,022], SD $39,096, maxDD $231,957, corr ST 0.43, HM 0.26; placebo 0.93, conditioning-null 1.00, 2x-cost WF $5,241; MDE weekly $9,154. Paired vs ST10 (WF) 9.5 [5.0,14.3] n=371 MDE 6.6; HOLD 7.9 [1.3,14.6] n=207 MDE 9.6; vs base 0.1 [-0.2,0.4] n=1494 MDE 0.5.

| slice       |    n |   tpw |      wk |   win | pair_ST                        |
|:------------|-----:|------:|--------:|------:|:-------------------------------|
| all|both    | 1896 | 13.26 | 7597.29 |  0.52 | 9.5 [5.0,14.3] n=371 MDE 6.6   |
| all|long    |  860 |  6.01 | 2191    |  0.52 | 11.2 [5.2,17.4] n=173 MDE 8.5  |
| all|short   | 1036 |  7.24 | 5406.29 |  0.53 | 8.1 [1.7,14.6] n=198 MDE 9.4   |
| quiet|both  |  544 |  3.8  | 1684.71 |  0.52 | 11.0 [2.5,19.7] n=86 MDE 12.4  |
| quiet|long  |  254 |  1.78 | 1739.7  |  0.54 | 12.9 [-0.9,26.7] n=40 MDE 19.9 |
| quiet|short |  290 |  2.03 |  -54.99 |  0.49 | 9.3 [1.2,19.7] n=46 MDE 13.4   |
| wide|both   | 1341 |  9.38 | 5683.48 |  0.53 | 9.3 [3.6,14.7] n=279 MDE 7.8   |
| wide|long   |  601 |  4.2  |  531.44 |  0.51 | 10.6 [4.3,17.4] n=133 MDE 9.3  |
| wide|short  |  740 |  5.17 | 5152.04 |  0.54 | 8.0 [-0.4,17.3] n=146 MDE 12.5 |

Equal risk (mapped series, helper equal_risk.py): $/wk at equal lots (10) 7,420; lots at equal risk (weekly SD = ST10's $57,331) 14.6; $/wk at equal risk 10,727 vs ST10 14,350 (delta -3,623); capacity lots (mean>0) 108.0, practical ceiling 24.0; 50-cap feasible True; DS3 marginal Sharpe add-one (KB+SM+EM base) WF-PRE 0.30, WF 0.24, HOLD 0.17.

### PRO3A_VOL: PASS (failed: none)
cond, {"base": "PB_ST10_EMA5_T1", "cond": "VOL"}. 16.1 trades/wk, win 0.520, avg win $11,057 / avg loss $-10,902; PRE $10,172/wk, HOLD $6,324, SPAN2 $593, WF $8,386 CI [1,253,15,818], SD $45,973, maxDD $268,265, corr ST 0.37, HM 0.32; placebo 1.00, conditioning-null 1.00, 2x-cost WF $5,749; MDE weekly $10,764. Paired vs ST10 (WF) 10.4 [6.1,15.2] n=336 MDE 6.3; HOLD 13.0 [7.2,20.1] n=193 MDE 9.5; vs base 0.2 [-0.5,0.8] n=1243 MDE 0.9.

| slice       |    n |   tpw |      wk |   win | pair_ST                        |
|:------------|-----:|------:|--------:|------:|:-------------------------------|
| all|both    | 2301 | 16.09 | 8386.45 |  0.52 | 10.4 [6.1,15.2] n=336 MDE 6.3  |
| all|long    | 1196 |  8.36 | 3372.42 |  0.52 | 11.0 [5.3,17.3] n=178 MDE 8.7  |
| all|short   | 1105 |  7.73 | 5014.03 |  0.53 | 9.8 [4.0,15.6] n=158 MDE 8.5   |
| quiet|both  |  634 |  4.43 | 2531.49 |  0.52 | 12.1 [5.3,20.7] n=84 MDE 10.7  |
| quiet|long  |  316 |  2.21 |  582.08 |  0.51 | 15.4 [4.7,28.8] n=40 MDE 16.7  |
| quiet|short |  318 |  2.22 | 1949.4  |  0.53 | 9.0 [0.7,19.8] n=44 MDE 13.7   |
| wide|both   | 1647 | 11.52 | 5382.16 |  0.52 | 9.6 [4.6,15.5] n=246 MDE 7.8   |
| wide|long   |  869 |  6.08 | 2703.44 |  0.52 | 9.1 [2.0,16.3] n=134 MDE 10.3  |
| wide|short  |  778 |  5.44 | 2678.72 |  0.52 | 10.2 [3.3,17.5] n=112 MDE 10.4 |

Equal risk (mapped series, helper equal_risk.py): $/wk at equal lots (10) 7,969; lots at equal risk (weekly SD = ST10's $57,331) 12.5; $/wk at equal risk 9,962 vs ST10 14,350 (delta -4,388); capacity lots (mean>0) 95.0, practical ceiling 23.0; 50-cap feasible True; DS3 marginal Sharpe add-one (KB+SM+EM base) WF-PRE 0.54, WF 0.32, HOLD 0.07.

### PRO3A_P3: CANDIDATE (failed: WF_CI>0)
cond, {"base": "PB_ST10_EMA5_T1", "cond": "P3"}. 18.9 trades/wk, win 0.515, avg win $11,036 / avg loss $-10,908; PRE $6,080/wk, HOLD $8,928, SPAN2 $2,221, WF $7,497 CI [-135,15,365], SD $48,068, maxDD $323,267, corr ST 0.44, HM 0.51; placebo 0.95, conditioning-null 0.95, 2x-cost WF $5,324; MDE weekly $11,255. Paired vs ST10 (WF) 9.0 [5.3,12.8] n=518 MDE 5.3; HOLD 7.3 [2.2,12.5] n=299 MDE 7.2; vs base -0.1 [-0.4,0.3] n=2143 MDE 0.5.

| slice       |    n |   tpw |      wk |   win | pair_ST                       |
|:------------|-----:|------:|--------:|------:|:------------------------------|
| all|both    | 2700 | 18.88 | 7497    |  0.52 | 9.0 [5.3,12.8] n=518 MDE 5.3  |
| all|long    | 1333 |  9.32 | 4492.02 |  0.52 | 8.2 [3.9,12.9] n=250 MDE 6.5  |
| all|short   | 1367 |  9.56 | 3004.98 |  0.51 | 9.8 [4.0,16.2] n=268 MDE 8.5  |
| quiet|both  |  699 |  4.89 | 2592.79 |  0.52 | 12.0 [6.8,17.7] n=118 MDE 7.8 |
| quiet|long  |  341 |  2.38 | 1538.5  |  0.52 | 13.1 [5.4,22.0] n=54 MDE 11.9 |
| quiet|short |  358 |  2.5  | 1054.28 |  0.51 | 11.2 [3.4,19.8] n=64 MDE 11.6 |
| wide|both   | 2001 | 13.99 | 4904.21 |  0.51 | 8.2 [4.0,12.8] n=398 MDE 6.5  |
| wide|long   |  992 |  6.94 | 2953.51 |  0.52 | 6.8 [1.1,12.3] n=196 MDE 7.9  |
| wide|short  | 1009 |  7.06 | 1950.69 |  0.51 | 9.5 [2.3,16.7] n=202 MDE 10.7 |

Equal risk (mapped series, helper equal_risk.py): $/wk at equal lots (10) 7,550; lots at equal risk (weekly SD = ST10's $57,331) 11.9; $/wk at equal risk 8,974 vs ST10 14,350 (delta -5,376); capacity lots (mean>0) 75.0, practical ceiling 21.0; 50-cap feasible True; DS3 marginal Sharpe add-one (KB+SM+EM base) WF-PRE -0.03, WF 0.05, HOLD 0.15.

### PRO3A_REL: PASS (failed: none)
cond, {"base": "PB_ST10_EMA5_T1", "cond": "REL"}. 14.9 trades/wk, win 0.519, avg win $10,995 / avg loss $-10,766; PRE $5,713/wk, HOLD $9,937, SPAN2 $374, WF $7,791 CI [327,15,792], SD $46,206, maxDD $312,051, corr ST 0.38, HM 0.34; placebo 1.00, conditioning-null 0.97, 2x-cost WF $5,813; MDE weekly $10,819. Paired vs ST10 (WF) 13.1 [8.3,18.3] n=257 MDE 7.3; HOLD 14.7 [8.4,21.4] n=126 MDE 9.2; vs base 0.0 [-0.8,0.9] n=969 MDE 1.2.

| slice       |    n |   tpw |      wk |   win | pair_ST                         |
|:------------|-----:|------:|--------:|------:|:--------------------------------|
| all|both    | 2130 | 14.9  | 7790.93 |  0.52 | 13.1 [8.3,18.3] n=257 MDE 7.3   |
| all|long    | 1141 |  7.98 | 2688.93 |  0.51 | 9.8 [3.1,17.0] n=136 MDE 9.8    |
| all|short   |  989 |  6.92 | 5101.99 |  0.53 | 16.8 [10.2,24.2] n=121 MDE 10.2 |
| quiet|both  |  543 |  3.8  | 1815.89 |  0.51 | 6.8 [-1.0,15.9] n=58 MDE 11.9   |
| quiet|long  |  283 |  1.98 |  516.92 |  0.5  | 9.3 [-3.1,24.4] n=30 MDE 19.9   |
| quiet|short |  260 |  1.82 | 1298.97 |  0.52 |                                 |
| wide|both   | 1572 | 10.99 | 6042.67 |  0.52 | 15.2 [9.2,20.9] n=196 MDE 8.4   |
| wide|long   |  848 |  5.93 | 2315.43 |  0.52 | 10.1 [2.5,18.7] n=104 MDE 11.5  |
| wide|short  |  724 |  5.06 | 3727.24 |  0.53 | 20.9 [12.3,30.0] n=92 MDE 12.5  |

Equal risk (mapped series, helper equal_risk.py): $/wk at equal lots (10) 7,914; lots at equal risk (weekly SD = ST10's $57,331) 12.4; $/wk at equal risk 9,789 vs ST10 14,350 (delta -4,560); capacity lots (mean>0) 103.0, practical ceiling 24.0; 50-cap feasible True; DS3 marginal Sharpe add-one (KB+SM+EM base) WF-PRE -0.14, WF 0.10, HOLD 0.39.

Earning less than ST10 at equal lots is not a death criterion (user addendum): at equal risk every survivor is below ST10's WF level but with positive marginal Sharpe in DS3 (table above). They are subsets of one pullback entry, not independent books; add at most one of them.

## 4. DIRECT L2 replay

PENDING: replay of the 10 selected cells is running (/mnt/l2/l2vast/ds3_pro3/, code pro3_direct.py, S10x1 slices + XJ3, 2 workers because the box memory floor is 40 GB). The verdicts above are MAPPED and labelled so; no cell is reported as a final PASS until the direct numbers are in.

## 5. Executability and what is not done
- PRO3A cells: NT8-deliverable from 1/5/10-min bars of NQ plus the 10-min Supertrend of ES, RTY, YM from the CME feed (multi-instrument strategy); ADX, regression and volume features are bar indicators. No L2 at runtime. exec_status in the rows.
- PRO3B cells: NT8-deliverable (bars, session clock, calendar); nothing PASSes, so no spec.
- 10:00 releases: no free calendar on the box, no purchase made; the 10:00 news variant was NOT scored (PRO3B has 6 news cells on 08:30 and 14:00 only; 14:00-only cells had 16-20 trades and were not run).
- YM 1-min ends 2026-10-16 (not extended): 2026-10-19..23 uses ES+RTY only for the peer vote.
- T-BRACKET-PM treatment (A-D, G) for the survivors: NOT run in this track; the direct series are written to l2vast/ds3/out/SERIES/PRO3_<cell>_mapped.parquet (and _direct after the replay) for the T-BRACKET-PM agent; the 3x3 widening applies to a final PASS only and is not run until the direct verdict confirms one.
- Registration in PAPER-ALL (l2vast/struct48/paper_all/ds3_<cell>.json) follows the direct verdict.
- Not done: PRO1/PRO2 cells in the interaction pool (not available), P4 conditions on non-ST10 regimes.
