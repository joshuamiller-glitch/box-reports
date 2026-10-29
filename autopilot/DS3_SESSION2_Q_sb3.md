# DS3_SESSION2_Q_sb3 - live-latency replay of the sb3 survivors (D3SQ), q6
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q6.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q6/, scores out/ssa/cs_scores_q6.csv (replayed) and cs_analytic_q6.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 56; MEASURED V0 gate (HOLD, H25, H26 > 0) 20; at 1 s 22; CONSERVATIVE stress yes 37; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 46; gate_M0 AND edge-beyond-beta 20. Source beats_beta flag true for 0 replayed cell-sessions (false 0, NA 56). Non-replayable (MEASURED-ANALYTIC, label only): 0 cell-sessions, 0 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=20): median beta HOLD -2.81 pts, median edge HOLD +7.61, median MEASURED HOLD +4.86; HOLD edge > 0 for 20, HOLD edge 95% CI lower bound > 0 for 1 (1 clusters); MEASURED HOLD CI lower bound > 0 for 0. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |             9 |         3 |             3 |                           3 |                         0 |                     0 |                   0 |
| LONDON    |             2 |         2 |             2 |                           2 |                         0 |                     0 |                   0 |
| PREOPEN   |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-AM     |            22 |         8 |             8 |                           8 |                         0 |                     0 |                   0 |
| NY        |            20 |         4 |             4 |                           4 |                         0 |                     0 |                   0 |
| NY-PM     |             3 |         3 |             3 |                           3 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q6 | NY-AM | WO_TE1B_emax_5m_pb_b5_x1.5_k10 | NY-AM | q6:88 | SESSION-CANDIDATE-PARTIAL | 6.84 | 6.41 [-11.25, 24.08] | 24.25 | 6.63 / 5.55 | 4.62 | 1 / 1.00 | 8.38 / 6.41 | -2.83 | 9.25 | yes |  | yes | yes |
| q6 | NY-PM | TE7_kelt3m_n14_m1.0|wide | NY-PM | q6:116 | SESSION-CANDIDATE-PARTIAL | 1.12 | 4.52 [-5.73, 14.76] | 14.06 | 4.79 / 3.76 | 0.92 | 1 / 1.00 | 10.97 / 4.52 | -2.56 | 7.08 | yes |  | yes | yes |
| q6 | NY-PM | R5_QUIET_KB | NY-PM | q6:19 | SESSION-CANDIDATE-PARTIAL | 1.69 | 4.52 [-5.73, 14.76] | 14.06 | 4.79 / 3.76 | 1.62 | 1 / 1.00 | 11.02 / 4.52 | -2.56 | 7.08 | yes |  | yes | yes |
| q6 | NY | C5M1_NQ_819 | NY | q6:241 | SESSION-CANDIDATE-PARTIAL | 6.58 | 8.54 [-10.02, 27.09] | 25.48 | 5.02 / 28.74 | -0.11 | 1 / 1.00 | 13.62 / 8.54 | -2.25 | 10.79 | yes |  | yes | yes |
| q6 | NY-AM | C5M1_NQ_188 | NY-AM | q6:175 | SESSION-CANDIDATE-PARTIAL | 2.51 | 0.58 [-12.55, 13.72] | 18.04 | 0.45 / 1.32 | 1.25 | 1 / 1.00 | 7.92 / 0.58 | -3.92 | 4.51 | yes |  | yes | yes |
| q6 | NY-AM | WO_TE7_kelt3m_n14_m1.5_cci_b3_n40_k10 | NY-AM | q6:108 | SESSION-CANDIDATE-PARTIAL | 5.58 | 6.67 [-10.46, 23.80] | 23.52 | 5.25 / 11.93 | -9.82 | 1 / 1.00 | 10.18 / 6.67 | -2.56 | 9.23 | yes |  | yes | yes |
| q6 | NY | C5M1_NQ_303 | NY | q6:183 | SESSION-CANDIDATE-PARTIAL | 3.55 | 4.73 [-10.38, 19.84] | 20.75 | 0.96 / 21.38 | 4.62 | 1 / 1.00 | 11.03 / 4.73 | -2.41 | 7.14 | yes |  | yes | yes |
| q6 | NY | WO_TE1B_emax_5m_cci_b5_n27_k18 | NY | q6:88 | SESSION-CANDIDATE-PARTIAL | 7.38 | 4.84 [-8.93, 18.61] | 18.90 | 3.27 / 11.79 | -0.28 | 1 / 1.00 | 6.14 / 4.84 | -2.80 | 7.64 | yes |  | yes | yes |
| q6 | NY-AM | WO_TE1B_emax_5m_cci_b5_n40_k10 | NY-AM | q6:87 | SESSION-CANDIDATE-PARTIAL | 7.74 | 7.35 [-13.65, 28.36] | 28.84 | 3.35 / 20.58 | -9.92 | 1 / 1.00 | 8.69 / 7.35 | -2.62 | 9.98 | yes |  | yes | yes |
| q6 | NY-AM | C5M1_NQ_818 | NY-AM | q6:241 | SESSION-CANDIDATE-PARTIAL | 8.41 | 6.03 [-16.39, 28.46] | 30.78 | 5.90 / 6.78 | -2.23 | 1 / 1.00 | 14.31 / 6.03 | -3.90 | 9.93 | yes |  | yes | yes |
| q6 | ASIA | WO_PRO2_RIB1m_q30_cci_b1_n14_k10 | ASIA | q6:56 | SESSION-CANDIDATE-PARTIAL | 8.17 | 10.85 [-3.39, 25.08] | 19.54 | 2.09 / 37.13 | 0.65 | 1 / 1.00 | 8.21 / 10.85 | -2.75 | 13.60 | yes |  | yes | yes |
| q6 | NY-AM | R5_DW_HM | NY-AM | q6:2 | SESSION-CANDIDATE-PARTIAL | 6.18 | 5.19 [-5.49, 15.87] | 14.66 | 3.14 / 16.57 | -2.51 | 1 / 1.00 | 6.56 / 5.19 | -3.90 | 9.09 | yes |  | yes | yes |
| q6 | ASIA | WO_HM_cci_b1_n14_k10 | ASIA | q6:5 | SESSION-CANDIDATE-PARTIAL | 6.21 | 3.30 [-3.24, 9.84] | 8.98 | 2.56 / 5.37 | -2.13 | 1 / 1.00 | 6.13 / 3.30 | -3.19 | 6.50 | yes |  | yes | yes |
| q6 | LONDON | C5M1_NQ_775 | LONDON | q6:238 | SESSION-CANDIDATE-PARTIAL | 4.59 | 5.41 [-12.01, 22.82] | 23.91 | 5.31 / 5.86 | 4.22 | 1 / 1.00 | 10.92 / 5.41 | -2.44 | 7.85 | yes |  | yes | yes |
| q6 | ASIA | WO_PRO2_Z20_t1.0_cci_b5_n20_k30 | ASIA | q6:65 | SESSION-CANDIDATE-PARTIAL | 5.42 | 2.69 [-4.38, 9.75] | 9.70 | 0.42 / 7.88 | 1.65 | 1 / 1.00 | 3.53 / 2.69 | -3.18 | 5.86 | yes |  | yes | yes |
| q6 | NY-PM | TE4_vwb_k1.5_ny|wide | NY-PM | q6:99 | SESSION-CANDIDATE-PARTIAL | 7.20 | 4.87 [-6.03, 15.77] | 14.96 | 5.39 / 2.34 | -2.80 | 1 / 1.00 | 6.24 / 4.87 | -2.22 | 7.09 | yes |  | yes | yes |
| q6 | NY | WO_EM_cci_b5_n27_k30 | NY | q6:1 | SESSION-CANDIDATE-PARTIAL | 5.48 | 3.37 [-6.57, 13.31] | 13.65 | 1.97 / 9.11 | 0.02 | 1 / 1.00 | 4.41 / 3.37 | -4.21 | 7.58 | yes |  | yes | yes |
| q6 | NY-AM | C5M1_NQ_8 | NY-AM | q6:166 | SESSION-CANDIDATE-PARTIAL | 5.78 | 7.16 [-3.41, 17.72] | 14.50 | 5.33 / 14.27 | -1.32 | 1 / 1.00 | 4.04 / 7.16 | -3.40 | 10.56 | yes |  | yes | yes |
| q6 | NY-AM | TE3_ofi_w5_q0.97|wide | NY-AM | q6:89 | SESSION-CANDIDATE-PARTIAL | 2.06 | 1.01 [-5.46, 7.48] | 8.88 | 0.06 / 3.35 | -0.72 | 1 / 1.00 | 2.36 / 1.01 | -3.13 | 4.14 | yes |  | yes | yes |
| q6 | LONDON | WO_TE7_boll3m_n20_m1.5_pb_b5_x1.5_k10 | LONDON | q6:101 | SESSION-CANDIDATE-PARTIAL | 6.49 | 2.72 [-3.93, 9.38] | 9.13 | 3.80 / 0.01 | -5.32 | 1 / 1.00 | 2.88 / 2.72 | -3.17 | 5.89 | yes |  | yes | yes |

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| WO_TE7_boll3m_n30_m1.5_rsi_b5_k18 | NY-AM | NOT-MEASURED-CANDIDATE | 13.65 / 12.04 / 12.13 | 5.20 / 0.05 / 2.46 | 68 | 0.35 / -1.24 | 21.52 | -8.42 | -3.24 / 3.29 | yes |  | no |
| WO_TE1B_emax_5m_pb_b5_x1.5_k10 | NY-AM | SESSION-CANDIDATE-PARTIAL | 9.92 / 8.38 / 8.66 | 6.84 / 6.41 / 6.25 | 70 | 6.63 / 5.55 | 24.25 | 4.62 | -2.83 / 9.25 | yes |  | yes |
| CF_ST_SI44_t500_k5 | NY-AM | NOT-MEASURED-CANDIDATE | 8.62 / 6.88 / 7.24 | 2.32 / -3.72 / 0.46 | 220 | -5.70 / 1.92 | 10.73 | -0.10 | -3.50 / -0.23 | no |  | no |
| WO_KB_rsi_b3_k10 | NY | NOT-MEASURED-CANDIDATE | 14.41 / 13.36 / 12.71 | 1.67 / -0.16 / 2.17 | 35 | -1.57 / 3.91 | 25.92 | -4.20 | -2.58 / 2.42 | yes |  | no |
| WO_TE7_kelt3m_n14_m1.5_cci_b5_n20_k18 | ASIA | NOT-MEASURED-CANDIDATE | 8.77 / 7.82 / 9.16 | 1.33 / -3.29 / -1.92 | 153 | -3.95 / -0.88 | 12.25 | -9.01 | -3.09 / -0.20 | no |  | no |
| TE7_kelt3m_n14_m1.0|wide | NY-PM | SESSION-CANDIDATE-PARTIAL | 11.09 / 10.97 / 11.18 | 1.12 / 4.52 / 4.50 | 64 | 4.79 / 3.76 | 14.06 | 0.92 | -2.56 / 7.08 | yes |  | yes |
| R5_QUIET_KB | NY-PM | SESSION-CANDIDATE-PARTIAL | 11.13 / 11.02 / 11.24 | 1.69 / 4.52 / 4.50 | 64 | 4.79 / 3.76 | 14.06 | 1.62 | -2.56 / 7.08 | yes |  | yes |
| C5M1_NQ_819 | NY | SESSION-CANDIDATE-PARTIAL | 12.23 / 13.62 / 14.42 | 6.58 / 8.54 / 6.62 | 54 | 5.02 / 28.74 | 25.48 | -0.11 | -2.25 / 10.79 | yes |  | yes |
| C5M1_NQ_188 | NY-AM | SESSION-CANDIDATE-PARTIAL | 7.39 / 7.92 / 9.07 | 2.51 / 0.58 / 3.92 | 97 | 0.45 / 1.32 | 18.04 | 1.25 | -3.92 / 4.51 | yes |  | yes |
| WO_TE7_kelt3m_n14_m1.5_cci_b3_n40_k10 | NY-AM | SESSION-CANDIDATE-PARTIAL | 11.44 / 10.18 / 10.73 | 5.58 / 6.67 / 10.61 | 75 | 5.25 / 11.93 | 23.52 | -9.82 | -2.56 / 9.23 | yes |  | yes |
| WO_SM_cci_b5_n27_k10 | NY-AM | NOT-MEASURED-CANDIDATE | 14.30 / 11.51 / 12.96 | 3.40 / -0.23 / -1.49 | 56 | -1.10 / 5.86 | 23.27 | -2.31 | -4.05 / 3.82 | yes |  | no |
| C5M1_NQ_303 | NY | SESSION-CANDIDATE-PARTIAL | 10.21 / 11.03 / 11.99 | 3.55 / 4.73 / 4.78 | 103 | 0.96 / 21.38 | 20.75 | 4.62 | -2.41 / 7.14 | yes |  | yes |
| TE1B_volclimax_5m|wide | ASIA | NOT-MEASURED-CANDIDATE | 13.76 / 11.58 / 12.03 | 5.65 / 2.91 / 5.25 | 42 | -0.96 / 22.28 | 18.61 | -4.27 | -2.74 / 5.65 | yes |  | no |
| WO_KB_rsi_b3_k18 | NY | NOT-MEASURED-CANDIDATE | 9.03 / 7.37 / 6.08 | 2.28 / -2.22 / -0.04 | 82 | -3.56 / 2.23 | 13.51 | -0.33 | -2.61 / 0.39 | no |  | no |
| WO_SM_cci_b5_n20_k30 | ASIA | NOT-MEASURED-CANDIDATE | 11.66 / 9.00 / 9.93 | 1.63 / -7.42 / -5.53 | 71 | -10.91 / 4.59 | 18.34 | 2.49 | -3.52 / -3.90 | no |  | no |
| WO_TE1B_emax_5m_cci_b5_n27_k18 | NY | SESSION-CANDIDATE-PARTIAL | 7.19 / 6.14 / 6.13 | 7.38 / 4.84 / 5.03 | 87 | 3.27 / 11.79 | 18.90 | -0.28 | -2.80 / 7.64 | yes |  | yes |
| C5M1_NQ_258 | NY | NOT-MEASURED-CANDIDATE | 5.86 / 5.77 / 5.70 | 3.41 / 2.50 / 2.66 | 153 | -0.59 / 15.15 | 12.05 | 1.02 | -2.55 / 5.05 | yes |  | no |
| WO_TE7_kelt3m_n30_m1.0_cci_b3_n14_k18 | ASIA | NOT-MEASURED-CANDIDATE | 7.76 / 5.65 / 7.62 | 2.18 / -1.77 / 1.29 | 181 | -1.89 / -1.37 | 13.26 | -1.93 | -3.75 / 1.97 | yes |  | no |
| WO_TE1B_emax_5m_cci_b5_n40_k10 | NY-AM | SESSION-CANDIDATE-PARTIAL | 9.77 / 8.69 / 8.04 | 7.74 / 7.35 / 9.94 | 43 | 3.35 / 20.58 | 28.84 | -9.92 | -2.62 / 9.98 | yes |  | yes |
| WO_TE1_kelt_3m_rsi_b5_k18 | NY-AM | NOT-MEASURED-CANDIDATE | 10.43 / 8.63 / 9.02 | 8.62 / 5.30 / 9.75 | 57 | 6.73 / -0.69 | 23.61 | -5.70 | -2.51 / 7.81 | yes |  | no |
| C5M1_NQ_818 | NY-AM | SESSION-CANDIDATE-PARTIAL | 12.50 / 14.31 / 14.37 | 8.41 / 6.03 / 7.54 | 51 | 5.90 / 6.78 | 30.78 | -2.23 | -3.90 / 9.93 | yes |  | yes |
| WO_PRO2_RIB1m_q30_cci_b1_n14_k10 | ASIA | SESSION-CANDIDATE-PARTIAL | 10.57 / 8.21 / 8.81 | 8.17 / 10.85 / 13.48 | 76 | 2.09 / 37.13 | 19.54 | 0.65 | -2.75 / 13.60 | yes |  | yes |
| WO_PB3E_R3_P2_40_1.5R_pb_b5_x1.5_k10 | ASIA | NOT-MEASURED-CANDIDATE | 5.79 / 3.99 / 5.09 | 1.65 / -0.32 / 1.07 | 182 | -1.29 / 3.49 | 9.16 | 1.40 | -4.23 / 3.91 | yes |  | no |
| TB3_cdb_ofi_W3 | NY | NOT-MEASURED-CANDIDATE | 6.45 / 4.68 / 6.64 | 3.45 / -0.17 / 0.96 | 251 | 0.04 / -0.81 | 9.83 | 0.01 | -3.12 / 2.95 | yes |  | no |
| R5_DW_HM | NY-AM | SESSION-CANDIDATE-PARTIAL | 7.50 / 6.56 / 8.47 | 6.18 / 5.19 / 3.56 | 59 | 3.14 / 16.57 | 14.66 | -2.51 | -3.90 / 9.09 | yes |  | yes |

All cell-sessions with every column: out/ssa/cs_scores_q6.csv.

FLAG PARTIAL: q6 sb3: month 2025-10 (H25 HOLD) missing (worker killed); HOLD/H25 gates INCOMPLETE; tiers are SESSION-CANDIDATE-PARTIAL at most; missing month not imputed
