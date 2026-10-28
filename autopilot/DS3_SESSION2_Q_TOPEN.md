# DS3_SESSION2_Q_TOPEN - live-latency replay of the TOPEN survivors (D3SQ), q1
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q1.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q1/, scores out/ssa/cs_scores_q1.csv (replayed) and cs_analytic_q1.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 381; MEASURED V0 gate (HOLD, H25, H26 > 0) 312; at 1 s 279; CONSERVATIVE stress yes 329; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 347; gate_M0 AND edge-beyond-beta 280. Source beats_beta flag true for 89 replayed cell-sessions (false 292, NA 0). Non-replayable (MEASURED-ANALYTIC, label only): 557 cell-sessions, 525 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=312): median beta HOLD -2.97 pts, median edge HOLD +9.11, median MEASURED HOLD +6.49; HOLD edge > 0 for 312, HOLD edge 95% CI lower bound > 0 for 157 (15 clusters); MEASURED HOLD CI lower bound > 0 for 61. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| LONDON    |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| PREOPEN   |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-AM     |           381 |       312 |            30 |                          30 |                         8 |                   525 |                  37 |
| NY        |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-PM     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q1 | NY-AM | TOPEN_B2_OR30m_stp_ge0.5_F60 | NY-AM | 277 | SESSION-CANDIDATE | 4.44 | 5.38 [-5.21, 15.97] | 14.54 | 3.18 / 15.14 | 1.62 | 1 / 0.83 | 13.31 / 5.38 | -2.98 | 8.37 | yes | no | yes | yes |
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
| q1 | NY-AM | TOPEN_B2_OR60m_stp_ge0.5_F60 | W4_1030-1100 | 287 | SESSION-CANDIDATE | 1.49 | 7.49 [-4.54, 19.52] | 16.52 | 8.49 / 2.63 | -0.61 | 1 / 0.83 | 9.14 / 7.49 | -2.53 | 10.02 | yes | no | no | no |
| q1 | NY-AM | TOPEN_B2_PB_M50_T_F45 | W1_0930-0945 | 570 | SESSION-CANDIDATE | 9.66 | 7.01 [-6.08, 20.11] | 17.98 | 7.70 / 4.61 | -5.21 | 1 / 1.11 | 9.30 / 7.01 | -4.22 | 11.23 | yes | no | yes | no |
| q1 | NY-AM | TOPEN_B2_OR30s_c2_le1.5__D3_F60 | NY-AM | 1 | SESSION-CANDIDATE | 11.44 | 8.72 [-4.49, 21.93] | 18.13 | 7.68 / 16.35 | -5.51 | 1 / 0.83 | 9.89 / 8.72 | -3.43 | 12.14 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR15m_c2_le1_F60 | NY-AM | 271 | SESSION-CANDIDATE | 12.46 | 9.69 [-3.40, 22.78] | 17.97 | 5.93 / 32.27 | -6.57 | 1 / 0.83 | 8.71 / 9.69 | -3.02 | 12.71 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR30m_c2_le1_F60 | W3_1000-1030 | 278 | SESSION-CANDIDATE | 3.65 | 1.26 [-15.87, 18.39] | 23.52 | 0.24 / 8.55 | 1.21 | 1 / 0.83 | 8.59 / 1.26 | -3.03 | 4.29 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR2m_c5p_le1.5_F60 | NY-AM | 243 | SESSION-CANDIDATE | 8.08 | 5.37 [-2.86, 13.60] | 11.30 | 6.25 / 0.31 | -3.45 | 1 / 0.83 | 6.36 / 5.37 | -3.37 | 8.74 | yes | no | yes | no |
| q1 | NY-AM | TOPEN_B2_DR3m_pb1_mv20_F60 | W1_0930-0945 | 42 | SESSION-CANDIDATE | 10.00 | 7.24 [-5.23, 19.71] | 17.12 | 4.10 / 23.77 | -0.57 | 1 / 0.83 | 8.31 / 7.24 | -3.98 | 11.22 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_PB_M50_H_F60 | NY-AM | 557 | SESSION-CANDIDATE | 4.26 | 1.69 [-12.71, 16.09] | 19.77 | 1.66 / 1.85 | 0.43 | 1 / 0.83 | 8.97 / 1.69 | -3.72 | 5.41 | yes | yes | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR2m_hl_mv10_F60 | W1_0930-0945 | 36 | SESSION-CANDIDATE | 8.81 | 6.06 [-4.85, 16.97] | 14.97 | 4.36 / 13.71 | 1.07 | 1 / 0.83 | 8.22 / 6.06 | -2.75 | 8.81 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR15m_rt5_le1.5_F60 | NY-AM | 274 | SESSION-CANDIDATE | 11.90 | 9.59 [-6.86, 26.04] | 22.58 | 8.47 / 16.87 | -2.74 | 1 / 0.83 | 10.42 / 9.59 | -3.49 | 13.08 | yes | no | yes | no |
| q1 | NY-AM | TOPEN_B2_DR3m_pb3_mv20_F60 | NY-AM | 46 | SESSION-CANDIDATE | 9.19 | 6.57 [-5.31, 18.45] | 16.31 | 3.20 / 24.34 | -2.63 | 1 / 0.83 | 8.15 / 6.57 | -2.66 | 9.23 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR3m_mark_mv20_F60 | W1_0930-0945 | 40 | SESSION-CANDIDATE | 9.93 | 7.31 [-3.92, 18.55] | 15.42 | 6.99 / 9.01 | 0.79 | 1 / 0.83 | 7.84 / 7.31 | -2.80 | 10.12 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR15m_pb1_mv20_F60 | W2_0945-1000 | 63 | SESSION-CANDIDATE | 9.65 | 6.89 [-1.97, 15.75] | 12.16 | 4.16 / 18.17 | -0.50 | 1 / 0.83 | 5.75 / 6.89 | -3.33 | 10.22 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR10m_c5p_le1.5_F60 | NY-AM | 265 | SESSION-CANDIDATE | 4.65 | 2.10 [-6.55, 10.75] | 11.87 | 2.31 / 0.76 | -3.56 | 1 / 0.83 | 5.47 / 2.10 | -3.70 | 5.81 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_OR10m_c5_le1.5_F60 | NY-AM | 266 | SESSION-CANDIDATE | 3.78 | 1.42 [-7.83, 10.66] | 12.70 | 0.48 / 6.66 | -4.53 | 1 / 0.83 | 5.83 / 1.42 | -3.43 | 4.85 | yes | no | yes | yes |
| q1 | NY-AM | TOPEN_B2_DR10m_pb3_F45 | NY-AM | 59 | SESSION-CANDIDATE | 4.40 | 1.62 [-5.00, 8.25] | 9.10 | 0.05 / 9.54 | -4.10 | 1 / 1.11 | 2.51 / 1.62 | -3.20 | 4.82 | yes | no | yes | yes |

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TOPEN_B2_OR30m_stp_ge0.5_F60 | W3_1000-1030 | SESSION-CANDIDATE | 10.91 / 13.31 / 7.97 | 4.44 / 5.38 / 2.73 | 125 | 3.18 / 15.14 | 14.54 | 1.62 | -2.98 / 8.37 | yes | no | yes |
| TOPEN_B2_OR30m_stp_ge0.5_F60 | NY-AM | SESSION-CANDIDATE | 10.91 / 13.31 / 7.97 | 4.44 / 5.38 / 2.73 | 125 | 3.18 / 15.14 | 14.54 | 1.62 | -2.98 / 8.37 | yes | no | yes |
| TOPEN_B2_OR30m_stp_F60 | NY-AM | SESSION-CANDIDATE | 10.35 / 12.57 / 8.34 | 4.88 / 5.78 / 3.18 | 126 | 3.69 / 15.14 | 14.35 | 0.71 | -2.99 / 8.77 | yes | no | yes |
| TOPEN_B2_OR30m_stp_F60 | W3_1000-1030 | SESSION-CANDIDATE | 10.35 / 12.57 / 8.34 | 4.88 / 5.78 / 3.18 | 126 | 3.69 / 15.14 | 14.35 | 0.71 | -2.99 / 8.77 | yes | no | yes |
| TOPEN_B2_OR30m_stp_le1.5_F60 | W3_1000-1030 | SESSION-CANDIDATE | 9.64 / 12.59 / 9.10 | 8.83 / 9.34 / 6.69 | 98 | 9.68 / 7.73 | 14.72 | 2.66 | -2.51 / 11.86 | yes | no | yes |
| TOPEN_B2_OR30m_stp_le1.5_F60 | NY-AM | SESSION-CANDIDATE | 9.64 / 12.59 / 9.10 | 8.83 / 9.34 / 6.69 | 98 | 9.68 / 7.73 | 14.72 | 2.66 | -2.51 / 11.86 | yes | no | yes |
| TOPEN_B2_OR15m_stp_le1_F60 | NY-AM | SESSION-CANDIDATE | 12.89 / 13.42 / 10.52 | 7.80 / 6.94 / 5.96 | 72 | 3.91 / 23.75 | 15.04 | -7.20 | -3.52 / 10.46 | yes | no | yes |
| TOPEN_B2_DR15m_pb3_mv10__c2_X20_120 | W2_0945-1000 | SESSION-CANDIDATE | 12.48 / 11.22 / 9.62 | 10.12 / 8.77 / 5.45 | 118 | 3.97 / 30.93 | 16.97 | -2.25 | 3.49 / 5.28 | no | no | yes |
| TOPEN_B2_DR15m_pb3_mv10__c2_X20_120 | NY-AM | SESSION-CANDIDATE | 11.95 / 10.69 / 8.75 | 9.29 / 7.99 / 4.90 | 126 | 3.63 / 28.59 | 16.39 | -2.19 | 3.03 / 4.96 | yes | no | yes |
| TOPEN_B2_DR15m_pb3_mv10__c2_X30_90 | W2_0945-1000 | SESSION-CANDIDATE | 10.31 / 9.29 / 8.50 | 5.50 / 3.70 / 5.34 | 118 | 0.39 / 18.99 | 14.01 | -0.55 | -1.11 / 4.80 | yes | no | yes |
| TOPEN_B2_DR15m_pb3_mv10__c3_X40_120 | NY-AM | SESSION-CANDIDATE | 15.00 / 13.83 / 14.33 | 9.11 / 7.38 / 8.60 | 126 | 4.11 / 22.85 | 22.42 | 1.01 | 0.43 / 6.95 | yes | no | yes |
| TOPEN_B2_DR15m_pb3_mv10__c3_X40_120 | W2_0945-1000 | SESSION-CANDIDATE | 15.13 / 13.94 / 13.88 | 8.93 / 7.16 / 8.42 | 118 | 3.11 / 25.86 | 22.15 | 0.83 | -0.51 / 7.66 | yes | no | yes |
| TOPEN_B2_DR15m_hl_mv10__c3_X60_120 | NY-AM | SESSION-CANDIDATE | 18.77 / 17.55 / 18.93 | 4.24 / 2.41 / 4.12 | 105 | 0.14 / 12.07 | 24.56 | -2.53 | -4.62 / 7.03 | yes | no | yes |
| TOPEN_B2_OR15m_stp_le1.5_F60 | NY-AM | SESSION-CANDIDATE | 10.45 / 10.13 / 8.42 | 2.95 / 2.52 / 1.81 | 123 | 0.14 / 14.81 | 13.97 | -3.08 | -3.27 / 5.79 | yes | no | yes |
| TOPEN_B2_DR15m_pb3_mv10__c2_X30_90 | NY-AM | SESSION-CANDIDATE | 9.88 / 8.86 / 8.15 | 5.82 / 4.05 / 5.64 | 126 | 1.37 / 16.72 | 13.92 | -0.39 | -0.34 / 4.39 | yes | no | yes |
| TOPEN_B2_OR30m_stp_re_F60 | W3_1000-1030 | SESSION-CANDIDATE | 8.73 / 10.80 / 6.79 | 5.96 / 6.66 / 4.35 | 133 | 4.42 / 16.82 | 13.64 | -0.31 | -2.97 / 9.63 | yes | no | yes |
| TOPEN_B2_OR30m_stp_re_F60 | NY-AM | SESSION-CANDIDATE | 8.73 / 10.80 / 6.79 | 5.96 / 6.66 / 4.35 | 133 | 4.42 / 16.82 | 13.64 | -0.11 | -2.97 / 9.63 | yes | no | yes |
| TOPEN_B2_OR10m_stp_ge1_F45 | NY-AM | NOT-MEASURED-CANDIDATE | 10.01 / 10.30 / 6.04 | 1.78 / 0.44 / -0.49 | 84 | 0.58 / -0.08 | 11.61 | 7.84 | -2.78 / 3.22 | yes | no | no |
| TOPEN_B2_LV_RN_BH_F60 | NY-AM | NOT-MEASURED-CANDIDATE | 13.50 / 11.95 / 12.67 | 3.45 / 0.97 / 1.93 | 89 | -1.38 / 13.58 | 14.49 | 0.98 | -2.84 / 3.81 | yes | no | no |
| TOPEN_B2_DR15m_pb3_mv10__c2_X30_120 | W2_0945-1000 | SESSION-CANDIDATE | 12.18 / 11.19 / 13.14 | 5.75 / 5.13 / 7.69 | 118 | 0.89 / 24.71 | 18.85 | 0.04 | -0.95 / 6.08 | yes | no | yes |
| TOPEN_B2_DR15m_pb3_mv10__c2_X30_120 | NY-AM | SESSION-CANDIDATE | 11.94 / 10.98 / 12.86 | 6.47 / 5.88 / 8.33 | 126 | 2.43 / 22.21 | 18.28 | 0.54 | -0.16 / 6.04 | yes | no | yes |
| TOPEN_B2_DR15m_pb3_mv10__c1_X15_120 | W2_0945-1000 | SESSION-CANDIDATE | 9.96 / 9.20 / 10.24 | 6.29 / 4.92 / 6.08 | 118 | 1.35 / 21.40 | 14.65 | 0.09 | 3.12 / 1.79 | yes | no | yes |
| TOPEN_B2_DR5m_pb1_rm0.5__c3_X40_90 | W1_0930-0945 | SESSION-CANDIDATE | 17.45 / 16.42 / 14.37 | 10.06 / 9.42 / 9.83 | 80 | 8.31 / 13.85 | 16.85 | 3.79 | -3.80 / 13.22 | yes | no | yes |
| TOPEN_B2_DR5m_pb1_rm0.5__c3_X40_90 | NY-AM | SESSION-CANDIDATE | 17.45 / 16.42 / 14.37 | 10.06 / 9.42 / 9.83 | 80 | 8.31 / 13.85 | 16.85 | 3.79 | -3.80 / 13.22 | yes | no | yes |
| TOPEN_B2_OR30m_stp_le1_F60 | W3_1000-1030 | SESSION-CANDIDATE | 10.89 / 13.29 / 10.81 | 8.70 / 9.07 / 7.24 | 61 | 9.96 / 3.91 | 20.34 | -5.27 | -2.49 / 11.56 | yes | no | yes |

All cell-sessions with every column: out/ssa/cs_scores_q1.csv.
