# DS3_SESSION2_Q_sd2a - live-latency replay of the sd2a survivors (D3SQ), q2
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q2.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q2/, scores out/ssa/cs_scores_q2.csv (replayed) and cs_analytic_q2.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 37; MEASURED V0 gate (HOLD, H25, H26 > 0) 16; at 1 s 22; CONSERVATIVE stress yes 33; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 33; gate_M0 AND edge-beyond-beta 14. Source beats_beta flag true for 0 replayed cell-sessions (false 0, NA 37). Non-replayable (MEASURED-ANALYTIC, label only): 0 cell-sessions, 0 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=16): median beta HOLD -3.16 pts, median edge HOLD +6.91, median MEASURED HOLD +3.66; HOLD edge > 0 for 16, HOLD edge 95% CI lower bound > 0 for 3 (3 clusters); MEASURED HOLD CI lower bound > 0 for 0. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |            14 |         5 |             5 |                           5 |                         0 |                     0 |                   0 |
| LONDON    |             3 |         1 |             1 |                           0 |                         0 |                     0 |                   0 |
| PREOPEN   |             2 |         2 |             2 |                           1 |                         0 |                     0 |                   0 |
| NY-AM     |            10 |         3 |             3 |                           3 |                         0 |                     0 |                   0 |
| NY        |             3 |         3 |             3 |                           3 |                         0 |                     0 |                   0 |
| NY-PM     |             5 |         2 |             2 |                           2 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q2 | ASIA | PRO_ER4_n40_EMA5 | ASIA | q2:829 | SESSION-CANDIDATE | 14.45 | 10.64 [-6.98, 28.26] | 24.19 | 5.15 / 38.91 | -2.57 | 1 / 0.83 | 11.98 / 10.64 | -2.82 | 13.46 | yes |  | yes | yes |
| q2 | NY | TR1A_ens_s1.5_k4 | NY | q2:969 | SESSION-CANDIDATE | 6.42 | 3.96 [-3.50, 11.42] | 10.24 | 4.39 / 2.35 | 4.48 | 1 / 0.83 | 5.71 / 3.96 | -3.00 | 6.96 | yes |  | yes | yes |
| q2 | NY-AM | PRO3B_OPEN0930_DRV38_T1 | NY-AM | q2:954 | SESSION-CANDIDATE | 10.45 | 7.20 [-5.45, 19.85] | 17.36 | 4.33 / 21.21 | -5.69 | 1 / 0.83 | 8.61 / 7.20 | -4.88 | 12.08 | yes |  | yes | yes |
| q2 | NY | PRO3B_OPEN0930_DRV38_T1 | NY | q2:954 | SESSION-CANDIDATE | 10.45 | 7.20 [-5.45, 19.85] | 17.36 | 4.33 / 21.21 | -5.69 | 1 / 0.83 | 8.61 / 7.20 | -4.88 | 12.08 | yes |  | yes | yes |
| q2 | NY-PM | PRO1_AGG_RL3_EMA200_VWAP | NY-PM | q2:748 | SESSION-CANDIDATE | 6.61 | 6.72 [-7.64, 21.08] | 19.72 | 3.56 / 16.78 | -10.10 | 1 / 0.83 | 8.37 / 6.72 | -3.78 | 10.50 | yes |  | yes | yes |
| q2 | ASIA | PB6_ST3m_EMA20_2m_T1 | ASIA | q2:37 | SESSION-CANDIDATE | 5.63 | 2.73 [-4.56, 10.03] | 10.02 | 0.38 / 10.14 | -0.70 | 1 / 0.83 | 4.47 / 2.73 | -2.99 | 5.72 | yes |  | yes | yes |
| q2 | NY | PB7_PB_HMA55_EMA1_T2_W60_s-3 | NY | q2:76 | SESSION-CANDIDATE | 5.03 | 1.60 [-4.63, 7.82] | 8.55 | 0.34 / 7.37 | 0.70 | 1 / 0.83 | 3.55 / 1.60 | -3.21 | 4.81 | yes |  | yes | yes |
| q2 | NY-PM | PRO_ST10_AVWAP_flip_T2 | NY-PM | q2:872 | SESSION-CANDIDATE | 8.19 | 5.78 [-7.52, 19.08] | 18.26 | 6.18 / 3.55 | -1.80 | 1 / 0.83 | 6.29 / 5.78 | -2.64 | 8.42 | yes |  | yes | yes |
| q2 | PREOPEN | TB4B_tick_17_tick_1000_ST60_SW38_T3 | PREOPEN | q2:2126 | SESSION-CANDIDATE | 12.99 | 10.07 [-6.86, 26.99] | 23.24 | 4.22 / 29.56 | -2.33 | 1 / 0.83 | 8.10 / 10.07 | -2.63 | 12.70 | yes |  | yes | yes |
| q2 | ASIA | TR1E_bos_1m_c2 | ASIA | q2:1060 | SESSION-CANDIDATE | 5.36 | 2.43 [-3.05, 7.91] | 7.53 | 1.18 / 5.85 | -8.08 | 1 / 0.83 | 2.88 / 2.43 | -3.05 | 5.48 | yes |  | yes | yes |
| q2 | ASIA | PB_HMA55_EMA1_T2 | ASIA | q2:104 | SESSION-CANDIDATE | 4.17 | 2.01 [-5.03, 9.05] | 9.66 | 0.63 / 7.04 | 1.68 | 1 / 0.83 | 3.34 / 2.01 | -2.87 | 4.88 | yes |  | yes | yes |
| q2 | NY-AM | PB7_PB_HMA55_EMA1_T1_W15_s-3 | NY-AM | q2:63 | SESSION-CANDIDATE | 5.41 | 3.35 [-3.68, 10.38] | 9.65 | 2.69 / 6.01 | 1.30 | 1 / 0.83 | 3.50 / 3.35 | -3.50 | 6.85 | yes |  | yes | yes |
| q2 | PREOPEN | TR1A_vnr_30m_s0.5 | PREOPEN | q2:982 | SESSION-CANDIDATE | 7.97 | 2.58 [-15.55, 20.71] | 24.89 | 1.83 / 8.41 | 22.92 | 1 / 0.83 | 6.93 / 2.58 | -3.97 | 6.55 | no |  | yes | yes |
| q2 | ASIA | TR1A_ens_s1.0_k3 | ASIA | q2:966 | SESSION-CANDIDATE | 3.20 | 0.57 [-6.67, 7.81] | 9.94 | 0.44 / 1.02 | -1.74 | 1 / 0.83 | 2.81 / 0.57 | -3.74 | 4.31 | yes |  | yes | yes |
| q2 | LONDON | TR1B_reg1m_n60_t3_r0.5 | LONDON | q2:991 | SESSION-CANDIDATE | 9.01 | 5.12 [-2.82, 13.05] | 10.90 | 2.78 / 11.44 | 1.55 | 1 / 0.83 | 2.98 / 5.12 | -3.61 | 8.72 | no |  | yes | yes |
| q2 | NY-AM | TB4C_range_00_range_40_ST3_E20_1_T1 | NY-AM | q2:2139 | SESSION-CANDIDATE | 4.57 | 1.26 [-2.99, 5.50] | 5.83 | 0.68 / 3.07 | 0.68 | 1 / 0.83 | 0.96 / 1.26 | -3.11 | 4.37 | yes |  | yes | yes |

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB7_PB5_depth_atr0.5_W15_s+0 | ASIA | NOT-MEASURED-CANDIDATE | 12.36 / 9.74 / 10.32 | 5.03 / 1.42 / 3.02 | 191 | 2.50 / -1.54 | 11.17 | 3.94 | -3.27 / 4.69 | yes |  | no |
| PB7_PB_HMA55_EMA1_T2_W60_s-3 | NY-AM | NOT-MEASURED-CANDIDATE | 7.81 / 6.23 / 7.04 | 3.77 / -0.06 / 2.27 | 204 | -1.11 / 4.10 | 11.49 | 2.48 | -3.31 / 3.25 | yes |  | no |
| TR1A_ens_s0.5_k4 | NY-AM | NOT-MEASURED-CANDIDATE | 7.42 / 6.03 / 6.44 | 2.46 / -1.08 / -0.33 | 210 | -2.57 / 5.46 | 10.69 | -10.47 | -3.46 / 2.38 | yes |  | no |
| PB7_PB5_depth_atr0.5_W15_s-3 | ASIA | NOT-MEASURED-CANDIDATE | 9.75 / 7.36 / 8.43 | 8.35 / 3.51 / 5.84 | 214 | 5.60 / -2.68 | 11.97 | 3.70 | -3.56 / 7.07 | yes |  | no |
| FP_CDnop_t500_N_K60 | ASIA | NOT-MEASURED-CANDIDATE | 3.73 / 5.65 / 6.35 | 5.24 / 4.93 / 7.02 | 231 | 6.64 / -0.93 | 9.83 | -5.04 | -3.29 / 8.23 | yes |  | no |
| PRO_ER4_n40_EMA5 | ASIA | SESSION-CANDIDATE | 14.15 / 11.98 / 12.20 | 14.45 / 10.64 / 10.63 | 43 | 5.15 / 38.91 | 24.19 | -2.57 | -2.82 / 13.46 | yes |  | yes |
| TR1A_ens_s1.5_k4 | NY | SESSION-CANDIDATE | 6.15 / 5.71 / 7.20 | 6.42 / 3.96 / 3.61 | 148 | 4.39 / 2.35 | 10.24 | 4.48 | -3.00 / 6.96 | yes |  | yes |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | ASIA | NOT-MEASURED-CANDIDATE | 6.69 / 3.95 / 4.61 | 2.97 / 0.34 / 2.37 | 367 | -1.81 / 6.86 | 9.19 | -1.76 | -3.23 / 3.57 | yes |  | no |
| PRO3B_OPEN0930_DRV38_T1 | NY-AM | SESSION-CANDIDATE | 10.13 / 8.61 / 12.34 | 10.45 / 7.20 / 8.60 | 100 | 4.33 / 21.21 | 17.36 | -5.69 | -4.88 / 12.08 | yes |  | yes |
| PRO3B_OPEN0930_DRV38_T1 | NY | SESSION-CANDIDATE | 10.13 / 8.61 / 12.34 | 10.45 / 7.20 / 8.60 | 100 | 4.33 / 21.21 | 17.36 | -5.69 | -4.88 / 12.08 | yes |  | yes |
| PB_HMA55_SWZ_T3 | ASIA | NOT-MEASURED-CANDIDATE | 5.81 / 4.11 / 5.77 | 3.51 / 0.38 / 2.68 | 279 | 1.12 / -1.97 | 9.44 | -6.90 | -2.73 / 3.11 | yes |  | no |
| PRO1_AGG_RL3_EMA200_VWAP | NY-PM | SESSION-CANDIDATE | 10.86 / 8.37 / 11.65 | 6.61 / 6.72 / 11.50 | 46 | 3.56 / 16.78 | 19.72 | -10.10 | -3.78 / 10.50 | yes |  | yes |
| TR1B_reg5m_n20_t2_r0.5 | NY-AM | NOT-MEASURED-CANDIDATE | 7.63 / 4.83 / 6.45 | 1.34 / -0.91 / 4.51 | 140 | -0.93 / -0.79 | 11.72 | 4.35 | -3.99 / 3.08 | yes |  | no |
| PB6_ST3m_EMA20_2m_T1 | ASIA | SESSION-CANDIDATE | 6.22 / 4.47 / 6.57 | 5.63 / 2.73 / 3.86 | 278 | 0.38 / 10.14 | 10.02 | -0.70 | -2.99 / 5.72 | yes |  | yes |
| PB7_PB_HMA55_EMA1_T2_W60_s-3 | NY | SESSION-CANDIDATE | 5.17 / 3.55 / 4.54 | 5.03 / 1.60 / 4.60 | 313 | 0.34 / 7.37 | 8.55 | 0.70 | -3.21 / 4.81 | yes |  | yes |
| PRO_ST10_AVWAP_flip_T2 | NY-PM | SESSION-CANDIDATE | 8.78 / 6.29 / 9.13 | 8.19 / 5.78 / 6.24 | 73 | 6.18 / 3.55 | 18.26 | -1.80 | -2.64 / 8.42 | yes |  | yes |
| PB_HMA55_SWZ_T1 | ASIA | NOT-MEASURED-CANDIDATE | 7.20 / 4.06 / 5.51 | 2.51 / -0.55 / 1.22 | 259 | -2.54 / 5.89 | 10.84 | -1.54 | -3.63 / 3.07 | yes |  | no |
| TB4B_tick_17_tick_1000_ST60_SW38_T3 | PREOPEN | SESSION-CANDIDATE | 12.20 / 8.10 / 10.74 | 12.99 / 10.07 / 12.54 | 39 | 4.22 / 29.56 | 23.24 | -2.33 | -2.63 / 12.70 | yes |  | yes |
| PB7_PB_HMA55_EMA1_T2_W15_s+0 | NY-AM | NOT-MEASURED-CANDIDATE | 6.18 / 4.25 / 4.25 | 2.63 / -0.34 / 1.16 | 198 | -0.60 / 1.15 | 13.46 | 0.78 | -3.33 / 2.99 | yes |  | no |
| PB_EMA200_VWAP_T3 | NY-PM | NOT-MEASURED-CANDIDATE | 9.97 / 7.49 / 9.02 | 2.32 / 2.29 / 5.76 | 53 | 3.40 / -0.80 | 18.55 | -6.74 | -2.53 / 4.82 | yes |  | no |
| TR1E_bos_1m_c2 | ASIA | SESSION-CANDIDATE | 4.87 / 2.88 / 4.43 | 5.36 / 2.43 / 4.39 | 306 | 1.18 / 5.85 | 7.53 | -8.08 | -3.05 / 5.48 | yes |  | yes |
| PB_HMA55_EMA1_T3 | ASIA | NOT-MEASURED-CANDIDATE | 5.75 / 3.44 / 5.10 | 4.09 / 0.20 / 3.23 | 304 | 0.42 / -0.47 | 10.62 | -7.18 | -3.84 / 4.04 | yes |  | no |
| TB4C_range_24_range_80_ST5_SW38_T1 | ASIA | NOT-MEASURED-CANDIDATE | 6.84 / 3.94 / 5.22 | 4.14 / 0.97 / 4.24 | 265 | -0.48 / 6.03 | 10.83 | -0.79 | -3.67 / 4.64 | yes |  | no |
| TB4B_tick_28_tick_2000_ST10_E20_1_T3 | NY-PM | NOT-MEASURED-CANDIDATE | 6.32 / 3.34 / 4.31 | 8.28 / 4.31 / 7.08 | 170 | 5.68 / -0.98 | 11.01 | -2.24 | -2.93 / 7.24 | yes |  | no |
| PB_HMA55_EMA1_T2 | ASIA | SESSION-CANDIDATE | 6.24 / 3.34 / 4.22 | 4.17 / 2.01 / 4.78 | 278 | 0.63 / 7.04 | 9.66 | 1.68 | -2.87 / 4.88 | yes |  | yes |

All cell-sessions with every column: out/ssa/cs_scores_q2.csv.

FLAG PARTIAL: q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete)
