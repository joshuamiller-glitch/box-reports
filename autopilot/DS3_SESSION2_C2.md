# DS3_SESSION2_C2 - the 2023 gate on everything alive after the replay queue (D3SQC, T-SESSION-2 item C re-run), 2026-10-29
Research only. No replay run, no worker launched, no process killed, no live/execution/chart change, no credentials. UNTOUCHED never read; no trade date after 2026-02-06 read. Fees per FEES.md (NQ $4.84 RT = 0.242 pt, inside the MEASURED net points). Prereg l2vast/ds3/prereg/SSC2_prereg.md sha256 `3abe36a0ff304fd01e5f4735fcb157de5d0d8794a1a0392f2ba5dbe539004875` (recorded in autopilot/DECISIONS.md before any gated number). Method = DS3_SESSION2_C (SSC_prereg, sha256 0337ce87...63923db) unchanged: prior-session range F known at the open, gate q in {0,33,50,67} percentile of F chosen on PRE $/wk after the session-book lock, ONE HOLD look (logged out/ssa/looks_c2.json), X = 2023-04-01..2024-01-31 printed never selected. Code l2vast/ds3/code/ssc2/ssc2.py + ssc2_md.py; per-cell data out/ssa/c2_cells.csv (378 rows), c2_analytic.csv, c2_proxy.csv. Trade series = the existing q1-q9 replay outputs, rebuilt, not re-run.

Universe: all 378 cell-sessions with gate_M0 (MEASURED HOLD, H25, H26 > 0) and a MEASURED (market-entry) basis across q1..q9 = 93 wave-namespaced clusters; q1 312, q2 16, q3 8, q5 1, q6 20, q7 12, q8 9, q4 0, q9 0 (q4 and q9 had no MEASURED-gate survivor). Not gated here: 4 q3 market-fallback PROXY cell-sessions (limit/stop-entry proxy, not a tier) and 525 MEASURED-ANALYTIC q1 cell-sessions (37 clusters, all NY-AM; no trade series, so no F gate is possible; their stored X-span mean is given below). Best-of label F_C = 4 x 378 = 1512 gate cells; best-of is a label, no tier is changed by this item, nobody is killed for being one-session.

## PARTIAL waves (months missing, not imputed, no re-run)
q2 sd2a: 2023-12 missing, so the X span of its 16 cell-sessions is 9 of 10 months (PRE and HOLD complete; tier text unchanged, X flagged PARTIAL). q4 sd34: 2025-06 (PRE) and 2025-10/11 (HOLD) missing - it contributed 0 MEASURED-gate cell-sessions, so nothing to gate (PARTIAL, no tier). q6 sb3: 2025-10 (H25 HOLD) missing - its 20 cell-sessions carry SESSION-CANDIDATE-PARTIAL and the gated HOLD numbers for them are INCOMPLETE. The q2 and q6 rows are labelled in the `partial` column of c2_cells.csv and as -PARTIAL in the tier column.

## Verdict (plain)
1. **2023 is a low-range regime for every session, and the ungated MEASURED result in it is a mild loss that the sample cannot distinguish from zero.** Median session range 2023-04..2024-01 vs 2024-26 (pts): NY-AM 133 vs 193, ASIA 51 vs 94, LONDON 75 vs 112, PREOPEN 46 vs 62, NY-PM 99 vs 126. Median raw X mean over the 378 cell-sessions -1.63 pts/trade (2024-26 median +7.43); 125 of 378 are positive in X. Median X MDE is 13.9 pts/trade (X n median 113 trades): 0 cell-sessions are significantly negative in X (mean + MDE < 0) and only 1 is significantly positive (mean - MDE > 0). So 2023 is a power-limited null with a negative point estimate, not a proven sign flip. Nobody is demoted on it.
2. **Gate result (PRE-selected, one HOLD look): the gate is not worth using.** q = 0 (no gate) was chosen for 345 of 378; 33 chose a gate (q33 25, q50 3, q67 5). 4 gated cell-sessions 'fix 2023' (gated X mean > 0 and > ungated): see list below; 0 are flagged 'costs 2024-26' (every HOLD $/wk drop is smaller than that cell's HOLD MDE in $/wk) - read as unproven, not free. Summed over the 378, HOLD $/wk goes 188,063 (ungated) -> 185,210 (as selected), PRE 198,809 -> 200,861. The gate does not repair 2023 as a class: X mean median of gated cells where a gate was chosen moves -0.56 -> -4.13 pts (X n kept median 34 of 141).
3. **Range-normalised view (new here): range does not explain the X-span loss.** (a) pts per trade per 100 F-points: X median -2.03 vs 2024-26 +5.06 - the gap stays (NY-AM -2.18 vs +5.34); 105 of 378 positive in X. (b) Range-scaled X mean (X mean x 2024-26 median range / X median range, i.e. what X would be at 2024-26 volatility, if P&L scaled with range): median -2.35, 125 positive - scaling a loss scales it up, so the loss is not a pure range-scale effect. By the SSC rule 219 of 378 are 'volatility-regime' cells (X range or F below 2024-26 AND mean pts rising from F tercile 1 to 3), but for most the normalised X is still below the 2024-26 normalised mean, so the low-range explanation is descriptive only.
4. **Where 2023 holds up (no gate needed):** the 7 SESSION-PASS cell-sessions (all q7): 5 of 7 positive in X (median +7.10 pts), the NY-AM ba2/HM cells at +11 to +15 and ba2/SM ASIA +4.8 to +7.1. Positive-in-X sessions by cluster-best: PREOPEN, LONDON (3 of 6, median +0.1); negative: NY-PM, NY-AM (median -1.3), ASIA (-1.3). Everything is inside its X MDE, with the one exception noted.

## By session (all 378 cell-sessions)

| session   |   cells |   X_pos |   X_mean_med |   X_mde_med |   y_2024_26_med |   range_X |   range_Y |   nrm_X |   nrm_Y |   scaled_X |   vol_regime |   gated |   fixes_2023 |   costs_2024_26 |   PRE_wk_u |   PRE_wk_g |   HOLD_wk_u |   HOLD_wk_g |
|:----------|--------:|--------:|-------------:|------------:|----------------:|----------:|----------:|--------:|--------:|-----------:|-------------:|--------:|-------------:|----------------:|-----------:|-----------:|------------:|------------:|
| ASIA      |      17 |       5 |        -1.32 |       11.05 |            3.74 |     51.25 |     93.50 |    0.01 |    1.94 |      -2.41 |           11 |       1 |            0 |               0 |    8745.80 |    8803.13 |     6421.44 |     6179.33 |
| LONDON    |       6 |       3 |         0.09 |       18.42 |            5.14 |     74.50 |    111.62 |    2.04 |    4.52 |       0.13 |            5 |       2 |            0 |               0 |    1770.78 |    2079.74 |     1835.99 |     1579.25 |
| NY        |      10 |       4 |        -0.20 |       10.77 |            4.67 |    133.25 |    192.62 |   -0.99 |    2.88 |      -0.28 |           10 |       3 |            1 |               0 |    4674.77 |    4742.80 |     2847.09 |     2782.47 |
| NY-AM     |     331 |     106 |        -1.69 |       14.23 |            7.61 |    133.25 |    192.62 |   -2.18 |    5.34 |      -2.44 |          181 |      25 |            2 |               0 |  178442.44 |  179936.32 |   173386.24 |   170883.68 |
| NY-PM     |       7 |       3 |        -1.80 |       12.91 |            6.13 |     99.00 |    125.50 |   -2.13 |    3.83 |      -2.28 |            6 |       0 |            0 |               0 |    3210.97 |    3210.97 |     1886.56 |     1886.56 |
| PREOPEN   |       7 |       4 |         1.90 |       21.53 |            8.59 |     46.50 |     62.25 |    8.43 |    4.41 |       2.55 |            6 |       2 |            1 |               0 |    1964.73 |    2087.82 |     1685.98 |     1898.27 |

(X_mean_med = raw X-span mean pts/trade, median over cell-sessions; nrm = pts per 100 F-pts; scaled_X = X mean x range_Y/range_X; PRE/HOLD $/wk summed over cell-sessions at their own lots, session-book lock, ungated u vs as-selected g. CLOSE: no MEASURED-gate survivor. NY = 09:30-16:00 combined sessions use the NY-AM feature.)

## By tier
| tier                      |   cells |   X_pos |   X_mean_med |
|:--------------------------|--------:|--------:|-------------:|
| SESSION-CANDIDATE         |     335 |     104 |        -1.72 |
| SESSION-CANDIDATE-PARTIAL |      36 |      16 |        -0.49 |
| SESSION-PASS              |       7 |       5 |         7.10 |

## By wave
| wave   |   cells |   X_pos |   X_mean_med |   gated |   fixes |
|:-------|--------:|--------:|-------------:|--------:|--------:|
| q1     |     312 |      97 |        -1.74 |      20 |       2 |
| q2     |      16 |       7 |        -1.22 |       4 |       1 |
| q3     |       8 |       1 |        -2.23 |       3 |       0 |
| q5     |       1 |       0 |        -1.11 |       0 |       0 |
| q6     |      20 |       9 |        -0.20 |       4 |       1 |
| q7     |      12 |       9 |         5.94 |       0 |       0 |
| q8     |       9 |       2 |        -2.75 |       2 |       0 |

## Gate sensitivity over all cell-sessions (descriptive, not used for selection)
|     q |   median_X_mean |   cells_X_mean_pos |   median_X_n |
|------:|----------------:|-------------------:|-------------:|
|  0.00 |           -1.63 |             125.00 |       113.00 |
| 33.00 |           -4.39 |              98.00 |        31.00 |
| 50.00 |           -0.65 |             182.00 |        13.00 |
| 67.00 |            0.11 |              23.00 |         2.00 |

(q0 row is the raw all-trades X mean; q>0 rows are the lock-kept gated X mean. The q67 gate keeps ~2 trades of X: the positive count is small-n noise, as in DS3_SESSION2_C.)

## Per cluster (best MEASURED PRE-t cell-session of each of the 93 wave-namespaced clusters): summary by session
| sess    |   clusters |   X_pos |   X_mean_med |   gated |   fixes_2023 |
|:--------|-----------:|--------:|-------------:|--------:|-------------:|
| ASIA    |         17 |       5 |        -1.32 |       1 |            0 |
| LONDON  |          6 |       3 |         0.09 |       2 |            0 |
| NY      |          9 |       4 |        -0.11 |       2 |            0 |
| NY-AM   |         47 |      18 |        -1.32 |       5 |            0 |
| NY-PM   |          7 |       3 |        -1.80 |       0 |            0 |
| PREOPEN |          7 |       4 |         1.90 |       2 |            1 |

### Cluster bests (X_mean = ungated MEASURED pts/trade 2023-04..2024-01, MDE beside it; q = PRE-chosen gate)
| cluster   | cell                                             | session      | tier                      |   pre_t |   HOLD_pts |   HOLD_MDE |   X_mean |   X_n |   X_MDE |   Y2024_26 |   nrm_X |   nrm_Y |   q |   X_gated | fixes_2023   |
|:----------|:-------------------------------------------------|:-------------|:--------------------------|--------:|-----------:|-----------:|---------:|------:|--------:|-----------:|--------:|--------:|----:|----------:|:-------------|
| q7:1      | ba2/SM_t75_sst                                   | ASIA         | SESSION-PASS              |    2.77 |       6.01 |      13.24 |     4.78 |   126 |    8.97 |       7.52 |    0.01 |    5.20 |   0 |      4.44 | False        |
| q3:76     | FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size" | ASIA         | SESSION-CANDIDATE         |    2.68 |       3.33 |       6.76 |    -1.32 |   202 |    4.92 |       3.74 |   -0.41 |    2.07 |   0 |     -1.46 | False        |
| q7:2      | ba2/SM_t90_sst                                   | ASIA         | SESSION-PASS              |    2.55 |       5.20 |      14.49 |     7.10 |   126 |    9.76 |       7.60 |    1.17 |    5.56 |   0 |      6.67 | False        |
| q2:829    | PRO_ER4_n40_EMA5                                 | ASIA         | SESSION-CANDIDATE-PARTIAL |    2.19 |      10.64 |      24.19 |    -2.57 |    41 |   24.88 |      11.54 |    2.98 |    6.05 |   0 |     -2.57 | False        |
| q7:0      | ba2/EM_t60_s40                                   | ASIA         | SESSION-PASS              |    1.97 |       3.75 |      18.53 |    -4.12 |   139 |   10.15 |       4.97 |   -5.84 |    3.57 |   0 |     -4.57 | False        |
| q6:56     | WO_PRO2_RIB1m_q30_cci_b1_n14_k10                 | ASIA         | SESSION-CANDIDATE-PARTIAL |    1.96 |      10.85 |      19.54 |     0.65 |    86 |   17.32 |       8.91 |    4.03 |    3.54 |   0 |      1.36 | False        |
| q6:5      | WO_HM_cci_b1_n14_k10                             | ASIA         | SESSION-CANDIDATE-PARTIAL |    1.89 |       3.30 |       8.98 |    -2.13 |   141 |   15.17 |       5.33 |   -0.03 |    3.35 |   0 |     -1.72 | False        |
| q7:3      | tsoHM10/r1.5                                     | ASIA         | SESSION-PASS              |    1.78 |       2.88 |      13.13 |    -3.65 |   226 |   13.67 |       4.90 |   -2.60 |    2.94 |   0 |     -3.40 | False        |
| q2:37     | PB6_ST3m_EMA20_2m_T1                             | ASIA         | SESSION-CANDIDATE-PARTIAL |    1.73 |       2.73 |      10.02 |    -0.70 |   203 |   12.14 |       3.95 |    0.35 |    1.94 |   0 |     -0.41 | False        |
| q6:65     | WO_PRO2_Z20_t1.0_cci_b5_n20_k30                  | ASIA         | SESSION-CANDIDATE-PARTIAL |    1.72 |       2.69 |       9.70 |     1.65 |   181 |   11.05 |       3.29 |    2.89 |    1.89 |   0 |      1.99 | False        |
| q2:1060   | TR1E_bos_1m_c2                                   | ASIA         | SESSION-CANDIDATE-PARTIAL |    1.55 |       2.43 |       7.53 |    -8.08 |   192 |   12.69 |       2.73 |   -8.63 |    1.17 |   0 |     -8.43 | False        |
| q2:104    | PB_HMA55_EMA1_T2                                 | ASIA         | SESSION-CANDIDATE-PARTIAL |    1.39 |       2.01 |       9.66 |     1.68 |   184 |   12.78 |       2.92 |    4.43 |    1.84 |   0 |      2.01 | False        |
| q3:74     | FV|ASIA|tf-9500|{"entry": "c", "sing": 10, "size | ASIA         | SESSION-CANDIDATE         |    1.16 |       0.64 |       6.73 |    -1.14 |   212 |    4.78 |       1.10 |   -0.36 |    1.20 |   0 |     -1.27 | False        |
| q2:966    | TR1A_ens_s1.0_k3                                 | ASIA         | SESSION-CANDIDATE-PARTIAL |    1.16 |       0.57 |       9.94 |    -1.74 |   200 |   11.70 |       2.09 |    1.58 |    0.76 |  67 |    -20.97 | False        |
| q8:23     | T4A_PB3B_R5_P1_t45_s60                           | ASIA         | SESSION-CANDIDATE         |    1.05 |       1.80 |       8.01 |    -4.28 |   237 |    8.61 |       1.73 |   -0.70 |    0.61 |   0 |     -4.41 | False        |
| q8:2      | PB3B_R5_P1                                       | ASIA         | SESSION-CANDIDATE         |    0.89 |       3.16 |       8.75 |    -4.84 |   217 |    9.46 |       2.36 |   -0.59 |    1.35 |   0 |     -4.59 | False        |
| q8:34     | T4A_PRO_Z20_t1.0_t60_s50                         | ASIA         | SESSION-CANDIDATE         |    0.63 |       1.85 |       7.06 |    -0.14 |   255 |    9.69 |       1.45 |    2.39 |    0.87 |   0 |      0.02 | False        |
| q8:1      | PBX4_PBS_f60_T3_DFLIP                            | LONDON       | SESSION-CANDIDATE         |    2.08 |      16.34 |      29.24 |    11.59 |    44 |   39.43 |      15.36 |    6.91 |   14.36 |   0 |     11.59 | False        |
| q6:238    | C5M1_NQ_775                                      | LONDON       | SESSION-CANDIDATE-PARTIAL |    1.84 |       5.41 |      23.91 |     4.22 |    53 |   21.79 |       9.37 |   11.68 |    7.92 |   0 |      4.22 | False        |
| q8:4      | PB3E_C_R3_P2_60_1.5R                             | LONDON       | SESSION-CANDIDATE         |    1.77 |       4.73 |      20.07 |    -8.81 |    66 |   23.72 |       6.68 |  -20.38 |    4.63 |   0 |     -8.81 | False        |
| q6:101    | WO_TE7_boll3m_n20_m1.5_pb_b5_x1.5_k10            | LONDON       | SESSION-CANDIDATE-PARTIAL |    1.34 |       2.72 |       9.13 |    -5.32 |   141 |   13.26 |       2.84 |   -7.55 |    2.16 |  50 |    nan    | False        |
| q2:991    | TR1B_reg1m_n60_t3_r0.5                           | LONDON       | SESSION-CANDIDATE-PARTIAL |    1.04 |       5.12 |      10.90 |     1.55 |   115 |   15.05 |       3.60 |   11.79 |    4.41 |   0 |      1.55 | False        |
| q3:81     | CRT|LONDON|tf-9500|{"L": 3, "buf": 0, "etf": -95 | LONDON       | SESSION-CANDIDATE         |   -0.59 |       1.57 |       9.61 |    -1.38 |    62 |    4.16 |      -0.17 |   -2.83 |   -1.84 |  50 |     -2.05 | False        |
| q6:241    | C5M1_NQ_819                                      | NY           | SESSION-CANDIDATE-PARTIAL |    2.23 |       8.54 |      25.48 |    -0.11 |    81 |   23.38 |      12.28 |    4.93 |    5.41 |   0 |     -0.11 | False        |
| q6:183    | C5M1_NQ_303                                      | NY           | SESSION-CANDIDATE-PARTIAL |    2.14 |       4.73 |      20.75 |     4.62 |   148 |   17.53 |       9.49 |    4.30 |    6.26 |   0 |      5.26 | False        |
| q2:969    | TR1A_ens_s1.5_k4                                 | NY           | SESSION-CANDIDATE-PARTIAL |    2.02 |       3.96 |      10.24 |     4.48 |   160 |   10.30 |       5.20 |    1.98 |    2.99 |   0 |      4.48 | False        |
| q2:954    | PRO3B_OPEN0930_DRV38_T1                          | NY           | SESSION-CANDIDATE-PARTIAL |    1.96 |       7.20 |      17.36 |    -5.69 |   113 |   18.50 |       8.17 |   -8.12 |    5.15 |   0 |     -5.69 | False        |
| q2:76     | PB7_PB_HMA55_EMA1_T2_W60_s-3                     | NY           | SESSION-CANDIDATE-PARTIAL |    1.73 |       1.60 |       8.55 |     0.70 |   326 |    7.97 |       2.93 |   -0.01 |    1.75 |   0 |      1.15 | False        |
| q6:1      | WO_EM_cci_b5_n27_k30                             | NY           | SESSION-CANDIDATE-PARTIAL |    1.47 |       3.37 |      13.65 |     0.02 |   142 |   11.24 |       4.13 |   -0.45 |    2.78 |   0 |      0.09 | False        |
| q8:11     | T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40           | NY           | SESSION-CANDIDATE         |    1.03 |       1.99 |       4.70 |    -2.75 |   328 |    6.69 |       1.64 |   -3.61 |    1.45 |   0 |     -2.93 | False        |
| q8:8      | T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40           | NY           | SESSION-CANDIDATE         |    0.78 |       1.42 |       6.03 |    -3.73 |   297 |    7.96 |       1.47 |   -3.95 |    0.93 |  33 |     -4.09 | False        |
| q8:27     | T4A_PB3D_R3_P2_t30_s40                           | NY           | SESSION-CANDIDATE         |    0.69 |       0.18 |       3.76 |    -1.82 |   396 |    4.81 |       0.64 |   -2.02 |    0.09 |  33 |     -3.18 | False        |
| q1:277    | TOPEN_B2_OR30m_stp_ge0.5_F60                     | W3_1000-1030 | SESSION-CANDIDATE         |    3.99 |       5.38 |      14.54 |     1.62 |   172 |   11.51 |      10.96 |    2.48 |    7.74 |   0 |      1.62 | False        |
| q7:4      | ba2/HM_t75_s90                                   | NY-AM        | SESSION-PASS              |    3.99 |       7.25 |      19.07 |    11.04 |   228 |   17.03 |      11.52 |   10.14 |    6.99 |   0 |     11.36 | False        |
| q1:272    | TOPEN_B2_OR15m_stp_le1_F60                       | NY-AM        | SESSION-CANDIDATE         |    3.88 |       6.94 |      15.04 |    -7.20 |   110 |   13.86 |      11.56 |   -8.76 |    9.42 |   0 |     -7.20 | False        |
| q1:2      | TOPEN_B2_DR15m_pb3_mv10__c2_X20_120              | W2_0945-1000 | SESSION-CANDIDATE         |    3.74 |       8.77 |      16.97 |    -2.25 |   160 |   10.97 |      10.51 |   -2.42 |    6.36 |   0 |     -2.25 | False        |
| q1:3      | TOPEN_B2_DR15m_hl_mv10__c3_X60_120               | NY-AM        | SESSION-CANDIDATE         |    3.46 |       2.41 |      24.56 |    -2.53 |   151 |   17.28 |      13.21 |   -1.99 |    7.37 |   0 |     -2.53 | False        |
| q7:5      | ba2/HM_t90_s90                                   | NY-AM        | SESSION-PASS              |    3.35 |       7.64 |      19.86 |    14.89 |   139 |   15.43 |      11.67 |   14.31 |    5.68 |   0 |     14.89 | False        |
| q1:5      | TOPEN_B2_DR5m_pb1_rm0.5__c3_X40_90               | W1_0930-0945 | SESSION-CANDIDATE         |    3.18 |       9.42 |      16.85 |     3.79 |    91 |   17.71 |      14.18 |    2.84 |   11.38 |   0 |      3.79 | False        |
| q1:6      | TOPEN_B2_DR10m_pb1_rm0.5__c3_X40_90              | W1_0930-0945 | SESSION-CANDIDATE         |    3.14 |      17.81 |      17.17 |    -2.31 |   106 |   16.03 |      13.26 |   -4.52 |    9.49 |   0 |     -2.31 | False        |
| q1:259    | TOPEN_B2_OR5m_stp_ge1_F60                        | NY-AM        | SESSION-CANDIDATE         |    2.95 |       2.12 |      19.02 |    -3.43 |   109 |   17.73 |       8.68 |   -4.62 |    4.22 |   0 |     -3.43 | False        |
| q1:601    | TOPEN_B2_LV_RN_BH_F60                            | W1_0930-0945 | SESSION-CANDIDATE         |    2.72 |       4.41 |      14.04 |    -1.63 |    81 |   17.78 |       8.94 |   -3.42 |    7.40 |   0 |     -1.63 | False        |
| q1:4      | TOPEN_B2_DR5m_pb3_rm0.5__c3_X40_90               | NY-AM        | SESSION-CANDIDATE         |    2.70 |       9.53 |      17.39 |    -1.76 |    91 |   18.37 |      11.41 |   -2.40 |   10.56 |   0 |     -1.76 | False        |
| q1:258    | TOPEN_B2_OR5m_c1_ge1_F45                         | W1_0930-0945 | SESSION-CANDIDATE         |    2.66 |       3.18 |      16.68 |    -3.42 |    84 |   13.60 |       7.24 |   -4.14 |    4.13 |   0 |     -3.42 | False        |
| q1:57     | TOPEN_B2_DR10m_hl_rm0.5_F60                      | NY-AM        | SESSION-CANDIDATE         |    2.58 |      15.25 |      16.57 |     4.08 |    92 |   17.98 |      12.28 |   -1.02 |    7.19 |   0 |      4.08 | False        |
| q1:0      | TOPEN_B2_OR3m_c2__O0_F60                         | W1_0930-0945 | SESSION-CANDIDATE         |    2.55 |       3.20 |      17.25 |     0.74 |   126 |   15.29 |       7.68 |   -3.08 |    4.81 |   0 |      0.74 | False        |
| q1:51     | TOPEN_B2_DR5m_hl_rm0.5_F60                       | W1_0930-0945 | SESSION-CANDIDATE         |    2.45 |       8.74 |      20.88 |     4.82 |    56 |   22.77 |      11.31 |    6.91 |    8.32 |   0 |      4.82 | False        |
| q1:44     | TOPEN_B2_DR3m_hl_mv20_F60                        | W1_0930-0945 | SESSION-CANDIDATE         |    2.45 |      12.19 |      17.68 |    -3.17 |    66 |   23.07 |      11.66 |   -3.90 |    7.61 |   0 |     -3.17 | False        |
| q6:88     | WO_TE1B_emax_5m_pb_b5_x1.5_k10                   | NY-AM        | SESSION-CANDIDATE-PARTIAL |    2.43 |       6.41 |      24.25 |     4.62 |   101 |   17.71 |       7.89 |    2.82 |    4.40 |  33 |      2.23 | False        |
| q1:287    | TOPEN_B2_OR60m_stp_ge0.5_F60                     | W4_1030-1100 | SESSION-CANDIDATE         |    2.36 |       7.49 |      16.52 |    -0.61 |   132 |   13.75 |       8.61 |   -0.18 |    7.25 |   0 |     -0.61 | False        |
| q6:175    | C5M1_NQ_188                                      | NY-AM        | SESSION-CANDIDATE-PARTIAL |    2.23 |       0.58 |      18.04 |     1.25 |   148 |   11.19 |       5.96 |   -1.88 |    5.03 |   0 |      0.80 | False        |
| q1:570    | TOPEN_B2_PB_M50_T_F45                            | W1_0930-0945 | SESSION-CANDIDATE         |    2.21 |       7.01 |      17.98 |    -5.21 |    55 |   19.24 |       8.57 |   -8.47 |    5.35 |   0 |     -5.21 | False        |
| q6:108    | WO_TE7_kelt3m_n14_m1.5_cci_b3_n40_k10            | NY-AM        | SESSION-CANDIDATE-PARTIAL |    2.20 |       6.67 |      23.52 |    -9.82 |    79 |   17.32 |       9.05 |   -8.31 |    4.99 |   0 |     -9.82 | False        |
| q1:1      | TOPEN_B2_OR30s_c2_le1.5__D3_F60                  | W1_0930-0945 | SESSION-CANDIDATE         |    2.16 |       9.02 |      18.86 |    -6.15 |   112 |   17.87 |       9.64 |   -9.13 |    6.17 |   0 |     -6.15 | False        |
| q1:271    | TOPEN_B2_OR15m_c2_le1_F60                        | NY-AM        | SESSION-CANDIDATE         |    2.14 |       9.69 |      17.97 |    -6.57 |   104 |   12.30 |       8.99 |   -7.24 |    7.44 |   0 |     -6.57 | False        |
| q1:278    | TOPEN_B2_OR30m_c2_le1_F60                        | W3_1000-1030 | SESSION-CANDIDATE         |    2.13 |       1.26 |      23.52 |     1.21 |    84 |   13.32 |       6.75 |    1.53 |    6.34 |   0 |      1.21 | False        |
| q8:0      | PBX_PB3B_R5_P2_f60_T3                            | NY-AM        | SESSION-CANDIDATE         |    2.11 |       5.71 |      21.59 |     0.00 |    93 |   21.84 |       8.87 |   -2.31 |    5.26 |   0 |     -0.62 | False        |
| q7:6      | ba2/KB_t90_s90                                   | NY-AM        | SESSION-PASS              |    2.01 |       6.72 |      15.55 |     8.10 |   295 |   18.08 |       7.82 |    5.07 |    4.29 |   0 |      7.18 | False        |
| q6:87     | WO_TE1B_emax_5m_cci_b5_n40_k10                   | NY-AM        | SESSION-CANDIDATE-PARTIAL |    2.01 |       7.35 |      28.84 |    -9.92 |    51 |   24.47 |       8.32 |  -10.45 |    4.94 |  33 |    -19.82 | False        |
| q5:12     | sd56/NY-AM/X:SB_HM_st_vw_5/t60s40/run            | NY-AM        | SESSION-CANDIDATE         |    1.98 |       4.56 |      12.96 |    -1.11 |   180 |   10.00 |       4.49 |   -1.07 |    2.65 |   0 |     -0.95 | False        |
| q3:49     | BOS|NYAM|tf2|{"L": 3, "box": "N12", "buf": 1, "n | NY-AM        | SESSION-CANDIDATE         |    1.98 |       1.41 |      10.47 |    -3.77 |   219 |    8.97 |       4.33 |   -3.96 |    1.37 |  33 |     -8.83 | False        |
| q1:243    | TOPEN_B2_OR2m_c5p_le1.5_F60                      | NY-AM        | SESSION-CANDIDATE         |    1.95 |       5.37 |      11.30 |    -3.45 |   192 |   12.42 |       6.07 |   -6.58 |    4.07 |   0 |     -3.45 | False        |
| q1:42     | TOPEN_B2_DR3m_pb1_mv20_F60                       | NY-AM        | SESSION-CANDIDATE         |    1.94 |       7.24 |      17.12 |    -0.57 |    85 |   19.46 |       7.95 |   -0.88 |    5.53 |   0 |     -0.57 | False        |
| q1:557    | TOPEN_B2_PB_M50_H_F60                            | NY-AM        | SESSION-CANDIDATE         |    1.92 |       1.69 |      19.77 |     0.43 |    71 |   20.68 |       6.64 |    2.31 |    5.83 |   0 |      0.43 | False        |
| q6:2      | R5_DW_HM                                         | NY-AM        | SESSION-CANDIDATE-PARTIAL |    1.92 |       5.19 |      14.66 |    -2.51 |   101 |   13.97 |       6.27 |   -1.16 |    2.58 |   0 |     -2.51 | False        |
| q1:36     | TOPEN_B2_DR2m_hl_mv10_F60                        | W1_0930-0945 | SESSION-CANDIDATE         |    1.92 |       6.06 |      14.97 |     1.07 |    98 |   17.72 |       7.58 |    0.89 |    3.32 |   0 |      1.07 | False        |
| q1:274    | TOPEN_B2_OR15m_rt5_le1.5_F60                     | NY-AM        | SESSION-CANDIDATE         |    1.83 |       9.59 |      22.58 |    -2.74 |    71 |   20.88 |      10.18 |   -2.75 |    9.09 |   0 |     -2.74 | False        |
| q1:46     | TOPEN_B2_DR3m_pb3_mv20_F60                       | NY-AM        | SESSION-CANDIDATE         |    1.81 |       6.57 |      16.31 |    -2.63 |    85 |   19.24 |       7.61 |   -3.96 |    6.29 |   0 |     -2.63 | False        |
| q1:40     | TOPEN_B2_DR3m_mark_mv20_F60                      | NY-AM        | SESSION-CANDIDATE         |    1.74 |       7.31 |      15.42 |     0.79 |    85 |   18.60 |       7.66 |    0.44 |    5.01 |   0 |      0.79 | False        |
| q1:63     | TOPEN_B2_DR15m_pb1_mv20_F60                      | NY-AM        | SESSION-CANDIDATE         |    1.64 |       6.89 |      12.16 |    -0.50 |   131 |   15.92 |       6.12 |   -2.64 |    4.01 |   0 |     -0.50 | False        |
| q1:265    | TOPEN_B2_OR10m_c5p_le1.5_F60                     | NY-AM        | SESSION-CANDIDATE         |    1.61 |       2.10 |      11.87 |    -3.56 |   176 |    9.02 |       4.43 |   -5.62 |    3.51 |   0 |     -3.56 | False        |
| q1:266    | TOPEN_B2_OR10m_c5_le1.5_F60                      | NY-AM        | SESSION-CANDIDATE         |    1.60 |       1.42 |      12.70 |    -4.53 |   179 |   10.18 |       4.47 |   -6.04 |    3.13 |   0 |     -4.53 | False        |
| q7:8      | pb4:min_1|ST3|VWAP|T2|60/60                      | NY-AM        | SESSION-CANDIDATE         |    1.59 |       1.83 |      10.98 |     0.41 |   129 |   12.80 |       4.08 |   -1.48 |    2.59 |   0 |     -0.48 | False        |
| q6:166    | C5M1_NQ_8                                        | NY-AM        | SESSION-CANDIDATE-PARTIAL |    1.46 |       7.16 |      14.50 |    -1.32 |   203 |   10.85 |       4.89 |   -2.17 |    2.93 |   0 |     -2.95 | False        |
| q6:89     | TE3_ofi_w5_q0.97|wide                            | NY-AM        | SESSION-CANDIDATE-PARTIAL |    1.37 |       1.01 |       8.88 |    -0.72 |   335 |    7.42 |       1.90 |   -0.21 |    1.51 |   0 |     -1.30 | False        |
| q2:63     | PB7_PB_HMA55_EMA1_T1_W15_s-3                     | NY-AM        | SESSION-CANDIDATE-PARTIAL |    1.34 |       3.35 |       9.65 |     1.30 |   218 |    8.20 |       3.45 |   -0.37 |    1.65 |  33 |     -0.67 | False        |
| q1:59     | TOPEN_B2_DR10m_pb3_F45                           | NY-AM        | SESSION-CANDIDATE         |    1.28 |       1.62 |       9.10 |    -4.10 |   214 |    9.15 |       2.24 |   -6.26 |    1.53 |   0 |     -4.10 | False        |
| q3:52     | BOS|NYAM|tf2|{"L": 3, "box": "dev", "buf": 1, "n | NY-AM        | SESSION-CANDIDATE         |    1.10 |       3.81 |      16.54 |    -8.30 |   144 |   11.34 |       3.80 |   -8.84 |    0.50 |  33 |     -6.70 | False        |
| q2:2139   | TB4C_range_00_range_40_ST3_E20_1_T1              | NY-AM        | SESSION-CANDIDATE-PARTIAL |    0.56 |       1.26 |       5.83 |     0.68 |   323 |    7.32 |       1.05 |   -1.16 |    0.91 |   0 |      0.01 | False        |
| q3:85     | CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500 | NY-PM        | SESSION-CANDIDATE         |    2.64 |       5.34 |       9.98 |    -3.08 |   250 |    7.92 |       4.91 |   -2.87 |    1.86 |   0 |     -2.89 | False        |
| q6:116    | TE7_kelt3m_n14_m1.0|wide                         | NY-PM        | SESSION-CANDIDATE-PARTIAL |    2.39 |       4.52 |      14.06 |     0.92 |    89 |   13.12 |       9.34 |    0.62 |    5.11 |   0 |      0.92 | False        |
| q6:19     | R5_QUIET_KB                                      | NY-PM        | SESSION-CANDIDATE-PARTIAL |    2.38 |       4.52 |      14.06 |     1.62 |    88 |   12.91 |       9.37 |    1.68 |    5.12 |   0 |      1.62 | False        |
| q2:748    | PRO1_AGG_RL3_EMA200_VWAP                         | NY-PM        | SESSION-CANDIDATE-PARTIAL |    1.87 |       6.72 |      19.72 |   -10.10 |    65 |   14.50 |       7.95 |   -9.22 |    2.90 |   0 |    -10.10 | False        |
| q3:68     | CRT|NYPM|tf1|{"L": 3, "buf": 0, "etf": 1, "etype | NY-PM        | SESSION-CANDIDATE         |    1.81 |       1.72 |       9.40 |     0.15 |   275 |    7.35 |       2.62 |    0.65 |    1.17 |   0 |     -0.03 | False        |
| q2:872    | PRO_ST10_AVWAP_flip_T2                           | NY-PM        | SESSION-CANDIDATE-PARTIAL |    1.66 |       5.78 |      18.26 |    -1.80 |    92 |   12.67 |       6.13 |   -2.13 |    3.83 |   0 |     -1.80 | False        |
| q6:99     | TE4_vwb_k1.5_ny|wide                             | NY-PM        | SESSION-CANDIDATE-PARTIAL |    1.56 |       4.87 |      14.96 |    -2.80 |    69 |   18.10 |       5.86 |   -2.84 |    4.11 |   0 |     -2.80 | False        |
| q7:10     | pb4:tick_1000|ST10|SW62|T2|60/60                 | PREOPEN      | SESSION-CANDIDATE         |    2.52 |       8.62 |      24.18 |     1.90 |    49 |   22.88 |      11.05 |    8.43 |    8.54 |   0 |      0.75 | False        |
| q3:83     | CRT|PRE|tf-9500|{"L": 3, "buf": 0, "etf": -9500, | PREOPEN      | SESSION-CANDIDATE         |    2.26 |       3.93 |      10.86 |    -6.03 |   100 |   11.47 |       5.42 |   -6.91 |    6.06 |   0 |     -6.03 | False        |
| q7:11     | pb4:volume_1000|ST10|SW62|T2|60/60               | PREOPEN      | SESSION-CANDIDATE         |    2.04 |       9.39 |      20.74 |     8.57 |    43 |   23.19 |       9.15 |   16.53 |    4.32 |   0 |      8.57 | False        |
| q7:12     | pb4:volume_1000|ST5|SW62|T2|60/60                | PREOPEN      | SESSION-CANDIDATE         |    2.02 |      11.35 |      20.64 |    15.25 |    37 |   23.53 |      10.84 |   24.42 |    6.85 |   0 |     15.25 | False        |
| q2:2126   | TB4B_tick_17_tick_1000_ST60_SW38_T3              | PREOPEN      | SESSION-CANDIDATE-PARTIAL |    1.59 |      10.07 |      23.24 |    -2.33 |    51 |   21.53 |       8.59 |   -8.11 |    2.55 |  33 |     18.67 | True         |
| q7:9      | pb4:tick_1000|ST10|SW62|T2|40/40                 | PREOPEN      | SESSION-CANDIDATE         |    1.49 |       5.60 |       9.91 |    -1.52 |    72 |   12.13 |       4.73 |   -1.37 |    4.41 |   0 |     -0.98 | False        |
| q2:982    | TR1A_vnr_30m_s0.5                                | PREOPEN      | SESSION-CANDIDATE-PARTIAL |    1.27 |       2.58 |      24.89 |    22.92 |    47 |   19.28 |       5.77 |   31.91 |    2.24 |  33 |     20.78 | False        |

## Gate cells that fix 2023 (gated X mean > 0 and > ungated), PRE-selected
| wave   | cell_s                              | sess    |   q |   x_mean_u |   x_mean_g |   x_n_u |   x_n_g |   hold_dwk_u |   hold_dwk_g |   hold_mde_dwk |
|:-------|:------------------------------------|:--------|----:|-----------:|-----------:|--------:|--------:|-------------:|-------------:|---------------:|
| q1     | TOPEN_B2_DR15m_pb3_mv20_F60         | NY-AM   |  33 |      -0.56 |       2.39 |     131 |      34 |       119.74 |        35.03 |         877.30 |
| q1     | TOPEN_B2_DR2m_hl_mv5_F60            | NY-AM   |  33 |       0.17 |       2.03 |     130 |      38 |       305.97 |       503.69 |         761.97 |
| q2     | TB4B_tick_17_tick_1000_ST60_SW38_T3 | PREOPEN |  33 |      -2.33 |      18.67 |      51 |      21 |       245.41 |       324.48 |         566.38 |
| q6     | WO_TE1B_emax_5m_cci_b5_n27_k18      | NY      |  33 |      -1.76 |       2.06 |     123 |      42 |       323.63 |        87.09 |         900.11 |

Each has a gated X n of 21-42 trades and X MDE far above the gain; the HOLD $/wk change is inside its MDE. None is a promotion: the gate was one of 4 per cell and the result is a best-of label.

## MEASURED-ANALYTIC (no series, not gateable)
| sess   |   cells |   clusters |   X_pos |   X_mean_med |   HOLD_mean_med |   HOLD_MDE_med |
|:-------|--------:|-----------:|--------:|-------------:|----------------:|---------------:|
| NY-AM  |     525 |         37 |     221 |        -0.76 |           10.46 |          23.11 |
(q1 T-OPEN analytic family; stored X mean from the family columns, V0 basis; a gate cannot be built without entry-level data. Their 2023 picture matches the replayed NY-AM: X mean median negative, 221 of 525 positive.)

## PROXY (q3 market-fallback, not a tier, not gated)
|   wave | cell                                                                            | session   | tier                    |
|-------:|:--------------------------------------------------------------------------------|:----------|:------------------------|
|      3 | IF|ASIA|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|deliv|B60/60|R   | ASIA      | PROXY-SESSION-CANDIDATE |
|      3 | IF|NYPM|tf-15|{"entry": "b", "sing": 0, "size": 16, "tf": -15}|none|B60/60|R    | NY-PM     | PROXY-SESSION-CANDIDATE |
|      3 | IF|NYPM|tf-15|{"entry": "b", "sing": 10, "size": 16, "tf": -15}|none|B60/60|R   | NY-PM     | PROXY-SESSION-CANDIDATE |
|      3 | OB|NYPM|tf-30|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": -30}|none|B60/60|R | NY-PM     | PROXY-SESSION-CANDIDATE |

## Caveats
- Lock-kept X means (gated table) differ slightly from the raw all-trades X mean (c2_cells x_mean_chk vs x_mean_u); the raw one is used for sign counts and tiers of 2023.
- Sub-window sessions (W1-W4) and NY use the NY-AM prior-session range feature (declared mapping). CLOSE has no survivor.
- MDE = 2.8 x week-clustered SE of the trade mean; every null above has its MDE beside it, and the typical X MDE (14 pts) is larger than the typical X effect (-1.6), so 2023 cannot confirm or reject any single cell.
- HOLD gated numbers were read once (looks_c2.json); q6 gated HOLD is INCOMPLETE (2025-10).
