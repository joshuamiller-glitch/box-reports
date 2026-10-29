# DS3_SESSION2_Q_BOOKS - running table of new session books found by the replay queue (D3SQ)
Updated after each wave. One row per independent cluster (best MEASURED PRE-t cell-session among MEASURED-gate cell-sessions). MEASURED = tier basis (V0, cell lot class at $1,000 risk); break-even = MEASURED mean net pts/trade (extra adverse pts that zero it). Beta placebo = same entries with side flipped (see SSA_Q_addendum). Non-replayable survivors are MEASURED-ANALYTIC (counts below, in cs_analytic_q*.csv).

## PARTIAL waves (killed workers, no retry without user OK)
- q6 sb3: month 2025-10 (H25 HOLD) missing (worker killed); HOLD/H25 gates INCOMPLETE; tiers are SESSION-CANDIDATE-PARTIAL at most; missing month not imputed
- q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete)
- q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed

## New session books found per session (clusters)
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |            92 |        18 |            17 |                          17 |                         0 |                     0 |                   0 |
| LONDON    |            25 |         6 |             6 |                           3 |                         0 |                     0 |                   0 |
| PREOPEN   |            21 |         7 |             7 |                           6 |                         0 |                     0 |                   0 |
| NY-AM     |           455 |       331 |            43 |                          42 |                         8 |                   525 |                  37 |
| NY        |            32 |        10 |            10 |                           9 |                         0 |                     0 |                   0 |
| NY-PM     |            32 |        10 |            10 |                           7 |                         0 |                     0 |                   0 |
| CLOSE     |             9 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

## Books
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q1 | NY-AM | TOPEN_B2_OR30m_stp_ge0.5_F60 | W3_1000-1030 | 277 | SESSION-CANDIDATE | 4.44 | 5.38 [-5.21, 15.97] | 14.54 | 3.18 / 15.14 | 1.62 | 1 / 0.83 | 13.31 / 5.38 | -2.98 | 8.37 | yes | no | yes | yes |
| q7 | NY-AM | ba2/HM_t75_s90 | NY-AM | 4 | SESSION-PASS |  | 7.25 [-6.64, 21.14] | 19.07 | 2.56 / 32.33 | 11.04 | 1 / 1.00 | 12.90 / 7.25 | -3.63 | 10.88 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR15m_stp_le1_F60 | NY-AM | 272 | SESSION-CANDIDATE | 7.80 | 6.94 [-4.02, 17.90] | 15.04 | 3.91 / 23.75 | -7.20 | 1 / 0.83 | 13.42 / 6.94 | -3.52 | 10.46 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR15m_pb3_mv10__c2_X20_120 | W2_0945-1000 | 2 | SESSION-CANDIDATE | 10.12 | 8.77 [-3.60, 21.13] | 16.97 | 3.97 / 30.93 | -2.25 | 2 / 2.50 | 11.22 / 8.77 | 3.49 | 5.28 | no | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR15m_hl_mv10__c3_X60_120 | NY-AM | 3 | SESSION-CANDIDATE | 4.24 | 2.41 [-15.48, 20.30] | 24.56 | 0.14 / 12.07 | -2.53 | 1 / 0.83 | 17.55 / 2.41 | -4.62 | 7.03 | yes | no | yes | yes |
| q7 | NY-AM | ba2/HM_t90_s90 | NY-AM | 5 | SESSION-PASS |  | 7.64 [-6.83, 22.10] | 19.86 | 2.28 / 36.56 | 14.89 | 1 / 1.00 | 13.09 / 7.64 | -3.32 | 10.96 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR10m_pb1_rm0.5__c3_X40_90 | W1_0930-0945 | 6 | SESSION-CANDIDATE | 20.12 | 17.81 [5.30, 30.32] | 17.17 | 12.15 / 38.97 | -2.31 | 1 / 1.25 | 11.22 / 17.81 | 1.92 | 15.89 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR5m_stp_ge1_F60 | NY-AM | 259 | SESSION-CANDIDATE | 1.81 | 2.12 [-11.73, 15.98] | 19.02 | 1.53 / 4.61 | -3.43 | 1 / 0.83 | 11.57 / 2.12 | -2.85 | 4.97 | yes | no | no | no |
| q7 | ASIA | ba2/SM_t75_sst | ASIA | 1 | SESSION-PASS |  | 6.01 [-3.63, 15.65] | 13.24 | 5.88 / 6.87 | 4.78 | 2 / 2.00 | 8.09 / 6.01 | 0.36 | 5.65 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_LV_RN_BH_F60 | W1_0930-0945 | 601 | SESSION-CANDIDATE | 7.06 | 4.41 [-5.82, 14.64] | 14.04 | 3.22 / 10.37 | -1.63 | 1 / 0.83 | 11.57 / 4.41 | -2.90 | 7.31 | yes | no | yes | yes |
| q3 | ASIA | FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 8, "tf": -9500}|none|B60/60|S | ASIA | 76 | SESSION-CANDIDATE |  | 3.33 [-1.59, 8.25] | 6.76 | 0.06 / 12.33 | -1.32 | 1 / 1.00 | 3.93 / 3.33 | -2.33 | 5.66 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR5m_c1_ge1_F45 | W1_0930-0945 | 258 | SESSION-CANDIDATE | 5.65 | 3.18 [-8.97, 15.32] | 16.68 | 3.10 / 3.43 | -3.42 | 1 / 1.11 | 8.92 / 3.18 | -3.54 | 6.72 | yes | no | yes | yes |
| q3 | NY-PM | CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R | NY-PM | 85 | SESSION-CANDIDATE |  | 5.34 [-1.93, 12.62] | 9.98 | 3.37 / 13.29 | -3.08 | 1 / 1.00 | 4.73 / 5.34 | -2.77 | 8.12 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR10m_hl_rm0.5_F60 | NY-AM | 57 | SESSION-CANDIDATE | 18.23 | 15.25 [3.18, 27.33] | 16.57 | 11.55 / 32.28 | 4.08 | 1 / 0.83 | 10.92 / 15.25 | -3.42 | 18.67 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR3m_c2__O0_F60 | W1_0930-0945 | 0 | SESSION-CANDIDATE | 5.69 | 3.20 [-9.37, 15.77] | 17.25 | 3.57 / 1.32 | 0.74 | 1 / 0.83 | 9.68 / 3.20 | -3.39 | 6.59 | yes | no | yes | yes |
| q7 | ASIA | ba2/SM_t90_sst | ASIA | 2 | SESSION-PASS |  | 5.20 [-5.36, 15.76] | 14.49 | 4.22 / 11.85 | 7.10 | 2 / 2.00 | 8.52 / 5.20 | -0.17 | 5.36 | yes |  | yes | yes |
| q7 | PREOPEN | pb4:tick_1000|ST10|SW62|T2|60/60 | PREOPEN | 10 | SESSION-CANDIDATE |  | 8.62 [-8.99, 26.24] | 24.18 | 4.55 / 19.05 | 1.90 | 1 / 0.83 | 12.15 / 8.62 | -2.68 | 11.30 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR5m_hl_rm0.5_F60 | W1_0930-0945 | 51 | SESSION-CANDIDATE | 11.66 | 8.74 [-6.47, 23.95] | 20.88 | 6.72 / 16.79 | 4.82 | 1 / 0.83 | 12.54 / 8.74 | -2.94 | 11.68 | yes | yes | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR3m_hl_mv20_F60 | W1_0930-0945 | 44 | SESSION-CANDIDATE | 15.36 | 12.19 [-0.69, 25.07] | 17.68 | 14.10 / 5.22 | -3.17 | 1 / 0.83 | 11.40 / 12.19 | -2.88 | 15.06 | yes | no | yes | yes |
| q6 | NY-AM | WO_TE1B_emax_5m_pb_b5_x1.5_k10 | NY-AM | 88 | SESSION-CANDIDATE-PARTIAL | 6.84 | 6.41 [-11.25, 24.08] | 24.25 | 6.63 / 5.55 | 4.62 | 1 / 1.00 | 8.38 / 6.41 | -2.83 | 9.25 | yes |  | yes | yes |
| q6 | NY-PM | TE7_kelt3m_n14_m1.0|wide | NY-PM | 116 | SESSION-CANDIDATE-PARTIAL | 1.12 | 4.52 [-5.73, 14.76] | 14.06 | 4.79 / 3.76 | 0.92 | 1 / 1.00 | 10.97 / 4.52 | -2.56 | 7.08 | yes |  | yes | yes |
| q6 | NY-PM | R5_QUIET_KB | NY-PM | 19 | SESSION-CANDIDATE-PARTIAL | 1.69 | 4.52 [-5.73, 14.76] | 14.06 | 4.79 / 3.76 | 1.62 | 1 / 1.00 | 11.02 / 4.52 | -2.56 | 7.08 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR60m_stp_ge0.5_F60 | W4_1030-1100 | 287 | SESSION-CANDIDATE | 1.49 | 7.49 [-4.54, 19.52] | 16.52 | 8.49 / 2.63 | -0.61 | 1 / 0.83 | 9.14 / 7.49 | -2.53 | 10.02 | yes | no | no | no |
| q3 | PREOPEN | CRT|PRE|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R | PREOPEN | 83 | SESSION-CANDIDATE |  | 3.93 [-3.98, 11.85] | 10.86 | 3.90 / 4.08 | -6.03 | 1 / 1.00 | 6.05 / 3.93 | -3.63 | 7.56 | yes |  | yes | yes |
| q6 | NY | C5M1_NQ_819 | NY | 241 | SESSION-CANDIDATE-PARTIAL | 6.58 | 8.54 [-10.02, 27.09] | 25.48 | 5.02 / 28.74 | -0.11 | 1 / 1.00 | 13.62 / 8.54 | -2.25 | 10.79 | yes |  | yes | yes |
| q6 | NY-AM | C5M1_NQ_188 | NY-AM | 175 | SESSION-CANDIDATE-PARTIAL | 2.51 | 0.58 [-12.55, 13.72] | 18.04 | 0.45 / 1.32 | 1.25 | 1 / 1.00 | 7.92 / 0.58 | -3.92 | 4.51 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_PB_M50_T_F45 | W1_0930-0945 | 570 | SESSION-CANDIDATE | 9.66 | 7.01 [-6.08, 20.11] | 17.98 | 7.70 / 4.61 | -5.21 | 1 / 1.11 | 9.30 / 7.01 | -4.22 | 11.23 | yes | no | yes | no |
| q6 | NY-AM | WO_TE7_kelt3m_n14_m1.5_cci_b3_n40_k10 | NY-AM | 108 | SESSION-CANDIDATE-PARTIAL | 5.58 | 6.67 [-10.46, 23.80] | 23.52 | 5.25 / 11.93 | -9.82 | 1 / 1.00 | 10.18 / 6.67 | -2.56 | 9.23 | yes |  | yes | yes |
| q2 | ASIA | PRO_ER4_n40_EMA5 | ASIA | 829 | SESSION-CANDIDATE | 14.45 | 10.64 [-6.98, 28.26] | 24.19 | 5.15 / 38.91 | -2.57 | 1 / 0.83 | 11.98 / 10.64 | -2.82 | 13.46 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR30s_c2_le1.5__D3_F60 | W1_0930-0945 | 1 | SESSION-CANDIDATE | 11.76 | 9.02 [-4.71, 22.76] | 18.86 | 7.99 / 16.35 | -6.15 | 1 / 0.83 | 9.89 / 9.02 | -3.45 | 12.48 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR15m_c2_le1_F60 | NY-AM | 271 | SESSION-CANDIDATE | 12.46 | 9.69 [-3.40, 22.78] | 17.97 | 5.93 / 32.27 | -6.57 | 1 / 0.83 | 8.71 / 9.69 | -3.02 | 12.71 | yes | no | yes | yes |
| q6 | NY | C5M1_NQ_303 | NY | 183 | SESSION-CANDIDATE-PARTIAL | 3.55 | 4.73 [-10.38, 19.84] | 20.75 | 0.96 / 21.38 | 4.62 | 1 / 1.00 | 11.03 / 4.73 | -2.41 | 7.14 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR30m_c2_le1_F60 | W3_1000-1030 | 278 | SESSION-CANDIDATE | 3.65 | 1.26 [-15.87, 18.39] | 23.52 | 0.24 / 8.55 | 1.21 | 1 / 0.83 | 8.59 / 1.26 | -3.03 | 4.29 | yes | no | yes | yes |
| q8 | LONDON | PBX4_PBS_f60_T3_DFLIP | LONDON | 1 | SESSION-CANDIDATE |  | 16.34 [-4.96, 37.64] | 29.24 | 17.14 / 13.97 | 11.59 | 1 / 1.00 | 14.95 / 16.34 | 5.89 | 10.45 | yes |  | yes | yes |
| q6 | NY | WO_TE1B_emax_5m_cci_b5_n27_k18 | NY | 88 | SESSION-CANDIDATE-PARTIAL | 7.38 | 4.84 [-8.93, 18.61] | 18.90 | 3.27 / 11.79 | -0.28 | 1 / 1.00 | 6.14 / 4.84 | -2.80 | 7.64 | yes |  | yes | yes |
| q7 | PREOPEN | pb4:volume_1000|ST10|SW62|T2|60/60 | PREOPEN | 11 | SESSION-CANDIDATE |  | 9.39 [-5.71, 24.50] | 20.74 | 4.33 / 21.31 | 8.57 | 1 / 0.83 | 9.04 / 9.39 | -4.84 | 14.23 | yes |  | yes | yes |
| q2 | NY | TR1A_ens_s1.5_k4 | NY | 969 | SESSION-CANDIDATE | 6.42 | 3.96 [-3.50, 11.42] | 10.24 | 4.39 / 2.35 | 4.48 | 1 / 0.83 | 5.71 / 3.96 | -3.00 | 6.96 | yes |  | yes | yes |
| q7 | PREOPEN | pb4:volume_1000|ST5|SW62|T2|60/60 | PREOPEN | 12 | SESSION-CANDIDATE |  | 11.35 [-3.68, 26.38] | 20.64 | 8.34 / 19.69 | 15.25 | 1 / 0.83 | 10.61 / 11.35 | -3.86 | 15.21 | yes |  | yes | yes |
| q6 | NY-AM | WO_TE1B_emax_5m_cci_b5_n40_k10 | NY-AM | 87 | SESSION-CANDIDATE-PARTIAL | 7.74 | 7.35 [-13.65, 28.36] | 28.84 | 3.35 / 20.58 | -9.92 | 1 / 1.00 | 8.69 / 7.35 | -2.62 | 9.98 | yes |  | yes | yes |
| q6 | NY-AM | C5M1_NQ_818 | NY-AM | 241 | SESSION-CANDIDATE-PARTIAL | 8.41 | 6.03 [-16.39, 28.46] | 30.78 | 5.90 / 6.78 | -2.23 | 1 / 1.00 | 14.31 / 6.03 | -3.90 | 9.93 | yes |  | yes | yes |
| q5 | NY-AM | sd56/NY-AM/X:SB_HM_st_vw_5/t60s40/run | NY-AM | 12 | SESSION-CANDIDATE |  | 4.56 [-4.88, 14.00] | 12.96 | 3.74 / 9.43 | -1.11 | 1 / 1.00 | 4.46 / 4.56 | 0.27 | 4.29 | yes |  | yes | yes |
| q3 | NY-AM | BOS|NYAM|tf2|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|R | NY-AM | 49 | SESSION-CANDIDATE |  | 1.41 [-6.21, 9.04] | 10.47 | 0.06 / 7.71 | -3.77 | 1 / 1.00 | 5.60 / 1.41 | -2.84 | 4.25 | yes |  | yes | yes |
| q7 | ASIA | ba2/EM_t60_s40 | ASIA | 0 | SESSION-PASS |  | 3.75 [-9.75, 17.25] | 18.53 | 0.11 / 34.06 | -4.12 | 1 / 1.00 | 5.40 / 3.75 | -0.75 | 4.50 | yes |  | yes | yes |
| q6 | ASIA | WO_PRO2_RIB1m_q30_cci_b1_n14_k10 | ASIA | 56 | SESSION-CANDIDATE-PARTIAL | 8.17 | 10.85 [-3.39, 25.08] | 19.54 | 2.09 / 37.13 | 0.65 | 1 / 1.00 | 8.21 / 10.85 | -2.75 | 13.60 | yes |  | yes | yes |
| q2 | NY | PRO3B_OPEN0930_DRV38_T1 | NY | 954 | SESSION-CANDIDATE | 10.45 | 7.20 [-5.45, 19.85] | 17.36 | 4.33 / 21.21 | -5.69 | 1 / 0.83 | 8.61 / 7.20 | -4.88 | 12.08 | yes |  | yes | yes |
| q2 | NY-AM | PRO3B_OPEN0930_DRV38_T1 | NY-AM | 954 | SESSION-CANDIDATE | 10.45 | 7.20 [-5.45, 19.85] | 17.36 | 4.33 / 21.21 | -5.69 | 1 / 0.83 | 8.61 / 7.20 | -4.88 | 12.08 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR2m_c5p_le1.5_F60 | NY-AM | 243 | SESSION-CANDIDATE | 8.08 | 5.37 [-2.86, 13.60] | 11.30 | 6.25 / 0.31 | -3.45 | 1 / 0.83 | 6.36 / 5.37 | -3.37 | 8.74 | yes | no | yes | no |
| q1 | NY-AM | TOPEN_B2_DR3m_pb1_mv20_F60 | NY-AM | 42 | SESSION-CANDIDATE | 10.00 | 7.24 [-5.23, 19.71] | 17.12 | 4.10 / 23.77 | -0.57 | 1 / 0.83 | 8.31 / 7.24 | -3.98 | 11.22 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_PB_M50_H_F60 | NY-AM | 557 | SESSION-CANDIDATE | 4.26 | 1.69 [-12.71, 16.09] | 19.77 | 1.66 / 1.85 | 0.43 | 1 / 0.83 | 8.97 / 1.69 | -3.72 | 5.41 | yes | yes | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR2m_hl_mv10_F60 | W1_0930-0945 | 36 | SESSION-CANDIDATE | 8.81 | 6.06 [-4.85, 16.97] | 14.97 | 4.36 / 13.71 | 1.07 | 1 / 0.83 | 8.22 / 6.06 | -2.75 | 8.81 | yes | no | yes | yes |
| q6 | ASIA | WO_HM_cci_b1_n14_k10 | ASIA | 5 | SESSION-CANDIDATE-PARTIAL | 6.21 | 3.30 [-3.24, 9.84] | 8.98 | 2.56 / 5.37 | -2.13 | 1 / 1.00 | 6.13 / 3.30 | -3.19 | 6.50 | yes |  | yes | yes |
| q2 | NY-PM | PRO1_AGG_RL3_EMA200_VWAP | NY-PM | 748 | SESSION-CANDIDATE | 6.61 | 6.72 [-7.64, 21.08] | 19.72 | 3.56 / 16.78 | -10.10 | 1 / 0.83 | 8.37 / 6.72 | -3.78 | 10.50 | yes |  | yes | yes |
| q6 | LONDON | C5M1_NQ_775 | LONDON | 238 | SESSION-CANDIDATE-PARTIAL | 4.59 | 5.41 [-12.01, 22.82] | 23.91 | 5.31 / 5.86 | 4.22 | 1 / 1.00 | 10.92 / 5.41 | -2.44 | 7.85 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR15m_rt5_le1.5_F60 | NY-AM | 274 | SESSION-CANDIDATE | 11.90 | 9.59 [-6.86, 26.04] | 22.58 | 8.47 / 16.87 | -2.74 | 1 / 0.83 | 10.42 / 9.59 | -3.49 | 13.08 | yes | no | yes | no |
| q1 | NY-AM | TOPEN_B2_DR3m_pb3_mv20_F60 | NY-AM | 46 | SESSION-CANDIDATE | 9.19 | 6.57 [-5.31, 18.45] | 16.31 | 3.20 / 24.34 | -2.63 | 1 / 0.83 | 8.15 / 6.57 | -2.66 | 9.23 | yes | no | yes | yes |
| q3 | NY-PM | CRT|NYPM|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R | NY-PM | 68 | SESSION-CANDIDATE |  | 1.72 [-5.12, 8.57] | 9.40 | 0.91 / 5.16 | 0.15 | 1 / 1.00 | 2.96 / 1.72 | -2.58 | 4.30 | yes |  | yes | yes |
| q7 | ASIA | tsoHM10/r1.5 | ASIA | 3 | SESSION-PASS |  | 2.88 [-6.68, 12.44] | 13.13 | 1.46 / 12.39 | -3.65 | 1 / 1.00 | 5.57 / 2.88 | -0.41 | 3.29 | yes |  | yes | yes |
| q8 | LONDON | PB3E_C_R3_P2_60_1.5R | LONDON | 4 | SESSION-CANDIDATE |  | 4.73 [-9.89, 19.35] | 20.07 | 4.45 / 5.44 | -8.81 | 1 / 1.00 | 7.63 / 4.73 | -2.26 | 6.98 | no |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR3m_mark_mv20_F60 | NY-AM | 40 | SESSION-CANDIDATE | 9.93 | 7.31 [-3.92, 18.55] | 15.42 | 6.99 / 9.01 | 0.79 | 1 / 0.83 | 7.84 / 7.31 | -2.80 | 10.12 | yes | no | yes | yes |
| q2 | ASIA | PB6_ST3m_EMA20_2m_T1 | ASIA | 37 | SESSION-CANDIDATE | 5.63 | 2.73 [-4.56, 10.03] | 10.02 | 0.38 / 10.14 | -0.70 | 1 / 0.83 | 4.47 / 2.73 | -2.99 | 5.72 | yes |  | yes | yes |
| q2 | NY | PB7_PB_HMA55_EMA1_T2_W60_s-3 | NY | 76 | SESSION-CANDIDATE | 5.03 | 1.60 [-4.63, 7.82] | 8.55 | 0.34 / 7.37 | 0.70 | 1 / 0.83 | 3.55 / 1.60 | -3.21 | 4.81 | yes |  | yes | yes |
| q6 | ASIA | WO_PRO2_Z20_t1.0_cci_b5_n20_k30 | ASIA | 65 | SESSION-CANDIDATE-PARTIAL | 5.42 | 2.69 [-4.38, 9.75] | 9.70 | 0.42 / 7.88 | 1.65 | 1 / 1.00 | 3.53 / 2.69 | -3.18 | 5.86 | yes |  | yes | yes |
| q2 | NY-PM | PRO_ST10_AVWAP_flip_T2 | NY-PM | 872 | SESSION-CANDIDATE | 8.19 | 5.78 [-7.52, 19.08] | 18.26 | 6.18 / 3.55 | -1.80 | 1 / 0.83 | 6.29 / 5.78 | -2.64 | 8.42 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR15m_pb1_mv20_F60 | NY-AM | 63 | SESSION-CANDIDATE | 9.65 | 6.89 [-1.97, 15.75] | 12.16 | 4.16 / 18.17 | -0.50 | 1 / 0.83 | 5.75 / 6.89 | -3.33 | 10.22 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR10m_c5p_le1.5_F60 | NY-AM | 265 | SESSION-CANDIDATE | 4.65 | 2.10 [-6.55, 10.75] | 11.87 | 2.31 / 0.76 | -3.56 | 1 / 0.83 | 5.47 / 2.10 | -3.70 | 5.81 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR10m_c5_le1.5_F60 | NY-AM | 266 | SESSION-CANDIDATE | 3.78 | 1.42 [-7.83, 10.66] | 12.70 | 0.48 / 6.66 | -4.53 | 1 / 0.83 | 5.83 / 1.42 | -3.43 | 4.85 | yes | no | yes | yes |
| q2 | PREOPEN | TB4B_tick_17_tick_1000_ST60_SW38_T3 | PREOPEN | 2126 | SESSION-CANDIDATE | 12.99 | 10.07 [-6.86, 26.99] | 23.24 | 4.22 / 29.56 | -2.33 | 1 / 0.83 | 8.10 / 10.07 | -2.63 | 12.70 | yes |  | yes | yes |
| q7 | NY-AM | pb4:min_1|ST3|VWAP|T2|60/60 | NY-AM | 8 | SESSION-CANDIDATE |  | 1.83 [-6.16, 9.83] | 10.98 | 1.92 / 1.47 | 0.41 | 1 / 0.83 | 5.06 / 1.83 | -4.48 | 6.31 | yes |  | yes | yes |
| q6 | NY-PM | TE4_vwb_k1.5_ny|wide | NY-PM | 99 | SESSION-CANDIDATE-PARTIAL | 7.20 | 4.87 [-6.03, 15.77] | 14.96 | 5.39 / 2.34 | -2.80 | 1 / 1.00 | 6.24 / 4.87 | -2.22 | 7.09 | yes |  | yes | yes |
| q2 | ASIA | TR1E_bos_1m_c2 | ASIA | 1060 | SESSION-CANDIDATE | 5.36 | 2.43 [-3.05, 7.91] | 7.53 | 1.18 / 5.85 | -8.08 | 1 / 0.83 | 2.88 / 2.43 | -3.05 | 5.48 | yes |  | yes | yes |
| q7 | PREOPEN | pb4:tick_1000|ST10|SW62|T2|40/40 | PREOPEN | 9 | SESSION-CANDIDATE |  | 5.60 [-1.62, 12.82] | 9.91 | 3.70 / 10.14 | -1.52 | 1 / 1.25 | 4.40 / 5.60 | -2.58 | 8.18 | yes |  | yes | yes |
| q6 | NY | WO_EM_cci_b5_n27_k30 | NY | 1 | SESSION-CANDIDATE-PARTIAL | 5.48 | 3.37 [-6.57, 13.31] | 13.65 | 1.97 / 9.11 | 0.02 | 1 / 1.00 | 4.41 / 3.37 | -4.21 | 7.58 | yes |  | yes | yes |
| q6 | NY-AM | C5M1_NQ_8 | NY-AM | 166 | SESSION-CANDIDATE-PARTIAL | 5.78 | 7.16 [-3.41, 17.72] | 14.50 | 5.33 / 14.27 | -1.32 | 1 / 1.00 | 4.04 / 7.16 | -3.40 | 10.56 | yes |  | yes | yes |
| q2 | ASIA | PB_HMA55_EMA1_T2 | ASIA | 104 | SESSION-CANDIDATE | 4.17 | 2.01 [-5.03, 9.05] | 9.66 | 0.63 / 7.04 | 1.68 | 1 / 0.83 | 3.34 / 2.01 | -2.87 | 4.88 | yes |  | yes | yes |
| q6 | NY-AM | TE3_ofi_w5_q0.97|wide | NY-AM | 89 | SESSION-CANDIDATE-PARTIAL | 2.06 | 1.01 [-5.46, 7.48] | 8.88 | 0.06 / 3.35 | -0.72 | 1 / 1.00 | 2.36 / 1.01 | -3.13 | 4.14 | yes |  | yes | yes |
| q6 | LONDON | WO_TE7_boll3m_n20_m1.5_pb_b5_x1.5_k10 | LONDON | 101 | SESSION-CANDIDATE-PARTIAL | 6.49 | 2.72 [-3.93, 9.38] | 9.13 | 3.80 / 0.01 | -5.32 | 1 / 1.00 | 2.88 / 2.72 | -3.17 | 5.89 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR10m_pb3_F45 | NY-AM | 59 | SESSION-CANDIDATE | 4.40 | 1.62 [-5.00, 8.25] | 9.10 | 0.05 / 9.54 | -4.10 | 1 / 1.11 | 2.51 / 1.62 | -3.20 | 4.82 | yes | no | yes | yes |
| q2 | PREOPEN | TR1A_vnr_30m_s0.5 | PREOPEN | 982 | SESSION-CANDIDATE | 7.97 | 2.58 [-15.55, 20.71] | 24.89 | 1.83 / 8.41 | 22.92 | 1 / 0.83 | 6.93 / 2.58 | -3.97 | 6.55 | no |  | yes | yes |
| q3 | ASIA | FV|ASIA|tf-9500|{"entry": "c", "sing": 10, "size": 8, "tf": -9500}|none|B50/50|S | ASIA | 74 | SESSION-CANDIDATE |  | 0.64 [-4.27, 5.54] | 6.73 | 0.17 / 1.92 | -1.14 | 1 / 1.00 | 1.32 / 0.64 | -2.65 | 3.28 | yes |  | yes | yes |
| q2 | ASIA | TR1A_ens_s1.0_k3 | ASIA | 966 | SESSION-CANDIDATE | 3.20 | 0.57 [-6.67, 7.81] | 9.94 | 0.44 / 1.02 | -1.74 | 1 / 0.83 | 2.81 / 0.57 | -3.74 | 4.31 | yes |  | yes | yes |
| q3 | NY-AM | BOS|NYAM|tf2|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|R | NY-AM | 52 | SESSION-CANDIDATE |  | 3.81 [-8.24, 15.86] | 16.54 | 3.91 / 3.40 | -8.30 | 1 / 1.00 | 3.80 / 3.81 | -2.65 | 6.46 | no |  | yes | no |
| q8 | ASIA | T4A_PB3B_R5_P1_t45_s60 | ASIA | 23 | SESSION-CANDIDATE |  | 1.80 [-4.03, 7.64] | 8.01 | 0.96 / 4.43 | -4.28 | 1 / 1.00 | 1.69 / 1.80 | -3.45 | 5.25 | yes |  | yes | yes |
| q2 | LONDON | TR1B_reg1m_n60_t3_r0.5 | LONDON | 991 | SESSION-CANDIDATE | 9.01 | 5.12 [-2.82, 13.05] | 10.90 | 2.78 / 11.44 | 1.55 | 1 / 0.83 | 2.98 / 5.12 | -3.61 | 8.72 | no |  | yes | yes |
| q8 | NY | T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | NY | 11 | SESSION-CANDIDATE |  | 1.99 [-1.43, 5.42] | 4.70 | 2.13 / 1.33 | -2.75 | 1 / 1.00 | 1.47 / 1.99 | -3.04 | 5.03 | yes |  | yes | yes |
| q8 | NY | T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | NY | 8 | SESSION-CANDIDATE |  | 1.42 [-2.97, 5.81] | 6.03 | 1.35 / 1.75 | -3.73 | 1 / 1.00 | 1.50 / 1.42 | -5.27 | 6.69 | no |  | no | yes |
| q8 | NY | T4A_PB3D_R3_P2_t30_s40 | NY | 27 | SESSION-CANDIDATE |  | 0.18 [-2.56, 2.93] | 3.76 | 0.18 / 0.19 | -1.82 | 1 / 1.00 | 0.86 / 0.18 | -3.29 | 3.47 | yes |  | yes | yes |
| q8 | ASIA | T4A_PRO_Z20_t1.0_t60_s50 | ASIA | 34 | SESSION-CANDIDATE |  | 1.85 [-3.29, 7.00] | 7.06 | 0.17 / 8.23 | -0.14 | 1 / 1.00 | 1.26 / 1.85 | -3.55 | 5.40 | yes |  | yes | yes |
| q2 | NY-AM | TB4C_range_00_range_40_ST3_E20_1_T1 | NY-AM | 2139 | SESSION-CANDIDATE | 4.57 | 1.26 [-2.99, 5.50] | 5.83 | 0.68 / 3.07 | 0.68 | 1 / 0.83 | 0.96 / 1.26 | -3.11 | 4.37 | yes |  | yes | yes |
| q3 | LONDON | CRT|LONDON|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 240, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|S | LONDON | 81 | SESSION-CANDIDATE |  | 1.57 [-5.42, 8.57] | 9.61 | 1.51 / 1.83 | -1.38 | 5 / 5.00 | -0.92 / 1.57 | -3.59 | 5.16 | no |  | yes | yes |
