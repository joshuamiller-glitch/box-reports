# DS3_SESSION2_Q_BOOKS - running table of new session books found by the replay queue (D3SQ)
Updated after each wave. One row per independent cluster (best MEASURED PRE-t cell-session among MEASURED-gate cell-sessions). MEASURED = tier basis (V0, cell lot class at $1,000 risk); break-even = MEASURED mean net pts/trade (extra adverse pts that zero it). Beta placebo = same entries with side flipped (see SSA_Q_addendum). Non-replayable survivors are MEASURED-ANALYTIC (counts below, in cs_analytic_q*.csv).

## New session books found per session (clusters)
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |            14 |         5 |             5 |                           5 |                         0 |                     0 |                   0 |
| LONDON    |             3 |         1 |             1 |                           0 |                         0 |                     0 |                   0 |
| PREOPEN   |             2 |         2 |             2 |                           1 |                         0 |                     0 |                   0 |
| NY-AM     |           391 |       315 |            32 |                          32 |                         8 |                   525 |                  37 |
| NY        |             3 |         3 |             3 |                           3 |                         0 |                     0 |                   0 |
| NY-PM     |             5 |         2 |             2 |                           2 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

## Books
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q1 | NY-AM | TOPEN_B2_OR30m_stp_ge0.5_F60 | W3_1000-1030 | 277 | SESSION-CANDIDATE | 4.44 | 5.38 [-5.21, 15.97] | 14.54 | 3.18 / 15.14 | 1.62 | 1 / 0.83 | 13.31 / 5.38 | -2.98 | 8.37 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR15m_stp_le1_F60 | NY-AM | 272 | SESSION-CANDIDATE | 7.80 | 6.94 [-4.02, 17.90] | 15.04 | 3.91 / 23.75 | -7.20 | 1 / 0.83 | 13.42 / 6.94 | -3.52 | 10.46 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR15m_pb3_mv10__c2_X20_120 | W2_0945-1000 | 2 | SESSION-CANDIDATE | 10.12 | 8.77 [-3.60, 21.13] | 16.97 | 3.97 / 30.93 | -2.25 | 2 / 2.50 | 11.22 / 8.77 | 3.49 | 5.28 | no | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR15m_hl_mv10__c3_X60_120 | NY-AM | 3 | SESSION-CANDIDATE | 4.24 | 2.41 [-15.48, 20.30] | 24.56 | 0.14 / 12.07 | -2.53 | 1 / 0.83 | 17.55 / 2.41 | -4.62 | 7.03 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR5m_pb1_rm0.5__c3_X40_90 | NY-AM | 5 | SESSION-CANDIDATE | 10.06 | 9.42 [-2.86, 21.69] | 16.85 | 8.31 / 13.85 | 3.79 | 1 / 1.25 | 16.42 / 9.42 | -3.80 | 13.22 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR10m_pb1_rm0.5__c3_X40_90 | W1_0930-0945 | 6 | SESSION-CANDIDATE | 20.12 | 17.81 [5.30, 30.32] | 17.17 | 12.15 / 38.97 | -2.31 | 1 / 1.25 | 11.22 / 17.81 | 1.92 | 15.89 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR5m_stp_ge1_F60 | NY-AM | 259 | SESSION-CANDIDATE | 1.81 | 2.12 [-11.73, 15.98] | 19.02 | 1.53 / 4.61 | -3.43 | 1 / 0.83 | 11.57 / 2.12 | -2.85 | 4.97 | yes | no | no | no |
| q1 | NY-AM | TOPEN_B2_LV_RN_BH_F60 | W1_0930-0945 | 601 | SESSION-CANDIDATE | 7.06 | 4.41 [-5.82, 14.64] | 14.04 | 3.22 / 10.37 | -1.63 | 1 / 0.83 | 11.57 / 4.41 | -2.90 | 7.31 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR5m_pb3_rm0.5__c3_X40_90 | NY-AM | 4 | SESSION-CANDIDATE | 11.63 | 9.53 [-3.14, 22.19] | 17.39 | 8.31 / 14.41 | -1.76 | 1 / 1.25 | 12.30 / 9.53 | -1.30 | 10.83 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR5m_c1_ge1_F45 | W1_0930-0945 | 258 | SESSION-CANDIDATE | 5.65 | 3.18 [-8.97, 15.32] | 16.68 | 3.10 / 3.43 | -3.42 | 1 / 1.11 | 8.92 / 3.18 | -3.54 | 6.72 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR10m_hl_rm0.5_F60 | NY-AM | 57 | SESSION-CANDIDATE | 18.23 | 15.25 [3.18, 27.33] | 16.57 | 11.55 / 32.28 | 4.08 | 1 / 0.83 | 10.92 / 15.25 | -3.42 | 18.67 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR3m_c2__O0_F60 | W1_0930-0945 | 0 | SESSION-CANDIDATE | 5.69 | 3.20 [-9.37, 15.77] | 17.25 | 3.57 / 1.32 | 0.74 | 1 / 0.83 | 9.68 / 3.20 | -3.39 | 6.59 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR5m_hl_rm0.5_F60 | W1_0930-0945 | 51 | SESSION-CANDIDATE | 11.66 | 8.74 [-6.47, 23.95] | 20.88 | 6.72 / 16.79 | 4.82 | 1 / 0.83 | 12.54 / 8.74 | -2.94 | 11.68 | yes | yes | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR3m_hl_mv20_F60 | W1_0930-0945 | 44 | SESSION-CANDIDATE | 15.36 | 12.19 [-0.69, 25.07] | 17.68 | 14.10 / 5.22 | -3.17 | 1 / 0.83 | 11.40 / 12.19 | -2.88 | 15.06 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR60m_stp_ge0.5_F60 | NY-AM | 287 | SESSION-CANDIDATE | 1.49 | 7.49 [-4.54, 19.52] | 16.52 | 8.49 / 2.63 | -0.61 | 1 / 0.83 | 9.14 / 7.49 | -2.53 | 10.02 | yes | no | no | no |
| q1 | NY-AM | TOPEN_B2_PB_M50_T_F45 | W1_0930-0945 | 570 | SESSION-CANDIDATE | 9.66 | 7.01 [-6.08, 20.11] | 17.98 | 7.70 / 4.61 | -5.21 | 1 / 1.11 | 9.30 / 7.01 | -4.22 | 11.23 | yes | no | yes | no |
| q2 | ASIA | PRO_ER4_n40_EMA5 | ASIA | 829 | SESSION-CANDIDATE | 14.45 | 10.64 [-6.98, 28.26] | 24.19 | 5.15 / 38.91 | -2.57 | 1 / 0.83 | 11.98 / 10.64 | -2.82 | 13.46 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR30s_c2_le1.5__D3_F60 | NY-AM | 1 | SESSION-CANDIDATE | 11.44 | 8.72 [-4.49, 21.93] | 18.13 | 7.68 / 16.35 | -5.51 | 1 / 0.83 | 9.89 / 8.72 | -3.43 | 12.14 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR15m_c2_le1_F60 | NY-AM | 271 | SESSION-CANDIDATE | 12.46 | 9.69 [-3.40, 22.78] | 17.97 | 5.93 / 32.27 | -6.57 | 1 / 0.83 | 8.71 / 9.69 | -3.02 | 12.71 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR30m_c2_le1_F60 | W3_1000-1030 | 278 | SESSION-CANDIDATE | 3.65 | 1.26 [-15.87, 18.39] | 23.52 | 0.24 / 8.55 | 1.21 | 1 / 0.83 | 8.59 / 1.26 | -3.03 | 4.29 | yes | no | yes | yes |
| q2 | NY | TR1A_ens_s1.5_k4 | NY | 969 | SESSION-CANDIDATE | 6.42 | 3.96 [-3.50, 11.42] | 10.24 | 4.39 / 2.35 | 4.48 | 1 / 0.83 | 5.71 / 3.96 | -3.00 | 6.96 | yes |  | yes | yes |
| q2 | NY-AM | PRO3B_OPEN0930_DRV38_T1 | NY-AM | 954 | SESSION-CANDIDATE | 10.45 | 7.20 [-5.45, 19.85] | 17.36 | 4.33 / 21.21 | -5.69 | 1 / 0.83 | 8.61 / 7.20 | -4.88 | 12.08 | yes |  | yes | yes |
| q2 | NY | PRO3B_OPEN0930_DRV38_T1 | NY | 954 | SESSION-CANDIDATE | 10.45 | 7.20 [-5.45, 19.85] | 17.36 | 4.33 / 21.21 | -5.69 | 1 / 0.83 | 8.61 / 7.20 | -4.88 | 12.08 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR2m_c5p_le1.5_F60 | NY-AM | 243 | SESSION-CANDIDATE | 8.08 | 5.37 [-2.86, 13.60] | 11.30 | 6.25 / 0.31 | -3.45 | 1 / 0.83 | 6.36 / 5.37 | -3.37 | 8.74 | yes | no | yes | no |
| q1 | NY-AM | TOPEN_B2_DR3m_pb1_mv20_F60 | NY-AM | 42 | SESSION-CANDIDATE | 10.00 | 7.24 [-5.23, 19.71] | 17.12 | 4.10 / 23.77 | -0.57 | 1 / 0.83 | 8.31 / 7.24 | -3.98 | 11.22 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_PB_M50_H_F60 | NY-AM | 557 | SESSION-CANDIDATE | 4.26 | 1.69 [-12.71, 16.09] | 19.77 | 1.66 / 1.85 | 0.43 | 1 / 0.83 | 8.97 / 1.69 | -3.72 | 5.41 | yes | yes | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR2m_hl_mv10_F60 | W1_0930-0945 | 36 | SESSION-CANDIDATE | 8.81 | 6.06 [-4.85, 16.97] | 14.97 | 4.36 / 13.71 | 1.07 | 1 / 0.83 | 8.22 / 6.06 | -2.75 | 8.81 | yes | no | yes | yes |
| q2 | NY-PM | PRO1_AGG_RL3_EMA200_VWAP | NY-PM | 748 | SESSION-CANDIDATE | 6.61 | 6.72 [-7.64, 21.08] | 19.72 | 3.56 / 16.78 | -10.10 | 1 / 0.83 | 8.37 / 6.72 | -3.78 | 10.50 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR15m_rt5_le1.5_F60 | NY-AM | 274 | SESSION-CANDIDATE | 11.90 | 9.59 [-6.86, 26.04] | 22.58 | 8.47 / 16.87 | -2.74 | 1 / 0.83 | 10.42 / 9.59 | -3.49 | 13.08 | yes | no | yes | no |
| q1 | NY-AM | TOPEN_B2_DR3m_pb3_mv20_F60 | NY-AM | 46 | SESSION-CANDIDATE | 9.19 | 6.57 [-5.31, 18.45] | 16.31 | 3.20 / 24.34 | -2.63 | 1 / 0.83 | 8.15 / 6.57 | -2.66 | 9.23 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR3m_mark_mv20_F60 | W1_0930-0945 | 40 | SESSION-CANDIDATE | 9.93 | 7.31 [-3.92, 18.55] | 15.42 | 6.99 / 9.01 | 0.79 | 1 / 0.83 | 7.84 / 7.31 | -2.80 | 10.12 | yes | no | yes | yes |
| q2 | ASIA | PB6_ST3m_EMA20_2m_T1 | ASIA | 37 | SESSION-CANDIDATE | 5.63 | 2.73 [-4.56, 10.03] | 10.02 | 0.38 / 10.14 | -0.70 | 1 / 0.83 | 4.47 / 2.73 | -2.99 | 5.72 | yes |  | yes | yes |
| q2 | NY | PB7_PB_HMA55_EMA1_T2_W60_s-3 | NY | 76 | SESSION-CANDIDATE | 5.03 | 1.60 [-4.63, 7.82] | 8.55 | 0.34 / 7.37 | 0.70 | 1 / 0.83 | 3.55 / 1.60 | -3.21 | 4.81 | yes |  | yes | yes |
| q2 | NY-PM | PRO_ST10_AVWAP_flip_T2 | NY-PM | 872 | SESSION-CANDIDATE | 8.19 | 5.78 [-7.52, 19.08] | 18.26 | 6.18 / 3.55 | -1.80 | 1 / 0.83 | 6.29 / 5.78 | -2.64 | 8.42 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR15m_pb1_mv20_F60 | W2_0945-1000 | 63 | SESSION-CANDIDATE | 9.65 | 6.89 [-1.97, 15.75] | 12.16 | 4.16 / 18.17 | -0.50 | 1 / 0.83 | 5.75 / 6.89 | -3.33 | 10.22 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR10m_c5p_le1.5_F60 | NY-AM | 265 | SESSION-CANDIDATE | 4.65 | 2.10 [-6.55, 10.75] | 11.87 | 2.31 / 0.76 | -3.56 | 1 / 0.83 | 5.47 / 2.10 | -3.70 | 5.81 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR10m_c5_le1.5_F60 | NY-AM | 266 | SESSION-CANDIDATE | 3.78 | 1.42 [-7.83, 10.66] | 12.70 | 0.48 / 6.66 | -4.53 | 1 / 0.83 | 5.83 / 1.42 | -3.43 | 4.85 | yes | no | yes | yes |
| q2 | PREOPEN | TB4B_tick_17_tick_1000_ST60_SW38_T3 | PREOPEN | 2126 | SESSION-CANDIDATE | 12.99 | 10.07 [-6.86, 26.99] | 23.24 | 4.22 / 29.56 | -2.33 | 1 / 0.83 | 8.10 / 10.07 | -2.63 | 12.70 | yes |  | yes | yes |
| q2 | ASIA | TR1E_bos_1m_c2 | ASIA | 1060 | SESSION-CANDIDATE | 5.36 | 2.43 [-3.05, 7.91] | 7.53 | 1.18 / 5.85 | -8.08 | 1 / 0.83 | 2.88 / 2.43 | -3.05 | 5.48 | yes |  | yes | yes |
| q2 | ASIA | PB_HMA55_EMA1_T2 | ASIA | 104 | SESSION-CANDIDATE | 4.17 | 2.01 [-5.03, 9.05] | 9.66 | 0.63 / 7.04 | 1.68 | 1 / 0.83 | 3.34 / 2.01 | -2.87 | 4.88 | yes |  | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR10m_pb3_F45 | NY-AM | 59 | SESSION-CANDIDATE | 4.40 | 1.62 [-5.00, 8.25] | 9.10 | 0.05 / 9.54 | -4.10 | 1 / 1.11 | 2.51 / 1.62 | -3.20 | 4.82 | yes | no | yes | yes |
| q2 | PREOPEN | TR1A_vnr_30m_s0.5 | PREOPEN | 982 | SESSION-CANDIDATE | 7.97 | 2.58 [-15.55, 20.71] | 24.89 | 1.83 / 8.41 | 22.92 | 1 / 0.83 | 6.93 / 2.58 | -3.97 | 6.55 | no |  | yes | yes |
| q2 | ASIA | TR1A_ens_s1.0_k3 | ASIA | 966 | SESSION-CANDIDATE | 3.20 | 0.57 [-6.67, 7.81] | 9.94 | 0.44 / 1.02 | -1.74 | 1 / 0.83 | 2.81 / 0.57 | -3.74 | 4.31 | yes |  | yes | yes |
| q2 | LONDON | TR1B_reg1m_n60_t3_r0.5 | LONDON | 991 | SESSION-CANDIDATE | 9.01 | 5.12 [-2.82, 13.05] | 10.90 | 2.78 / 11.44 | 1.55 | 1 / 0.83 | 2.98 / 5.12 | -3.61 | 8.72 | no |  | yes | yes |
| q2 | NY-AM | TB4C_range_00_range_40_ST3_E20_1_T1 | NY-AM | 2139 | SESSION-CANDIDATE | 4.57 | 1.26 [-2.99, 5.50] | 5.83 | 0.68 / 3.07 | 0.68 | 1 / 0.83 | 0.96 / 1.26 | -3.11 | 4.37 | yes |  | yes | yes |
