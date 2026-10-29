# DS3_SESSION2_Q_sb2 - live-latency replay of the sb2 survivors (D3SQ), q8
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q8.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q8/, scores out/ssa/cs_scores_q8.csv (replayed) and cs_analytic_q8.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 56; MEASURED V0 gate (HOLD, H25, H26 > 0) 9; at 1 s 8; CONSERVATIVE stress yes 31; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 25; gate_M0 AND edge-beyond-beta 7. Source beats_beta flag true for 0 replayed cell-sessions (false 0, NA 56). Non-replayable (MEASURED-ANALYTIC, label only): 0 cell-sessions, 0 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=9): median beta HOLD -3.13 pts, median edge HOLD +5.40, median MEASURED HOLD +1.99; HOLD edge > 0 for 9, HOLD edge 95% CI lower bound > 0 for 4 (4 clusters); MEASURED HOLD CI lower bound > 0 for 0. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |            32 |         3 |             3 |                           3 |                         0 |                     0 |                   0 |
| LONDON    |             5 |         2 |             2 |                           1 |                         0 |                     0 |                   0 |
| PREOPEN   |             1 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-AM     |             9 |         1 |             1 |                           1 |                         0 |                     0 |                   0 |
| NY        |             9 |         3 |             3 |                           2 |                         0 |                     0 |                   0 |
| NY-PM     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q8 | NY-AM | PBX_PB3B_R5_P2_f60_T3 | NY-AM | 0 | SESSION-CANDIDATE |  | 5.71 [-10.01, 21.43] | 21.59 | 5.09 / 7.76 | 0.00 | 1 / 1.00 | 10.24 / 5.71 | 1.42 | 4.29 | yes |  | yes | yes |
| q8 | LONDON | PBX4_PBS_f60_T3_DFLIP | LONDON | 1 | SESSION-CANDIDATE |  | 16.34 [-4.96, 37.64] | 29.24 | 17.14 / 13.97 | 11.59 | 1 / 1.00 | 14.95 / 16.34 | 5.89 | 10.45 | yes |  | yes | yes |
| q8 | LONDON | PB3E_C_R3_P2_60_1.5R | LONDON | 4 | SESSION-CANDIDATE |  | 4.73 [-9.89, 19.35] | 20.07 | 4.45 / 5.44 | -8.81 | 1 / 1.00 | 7.63 / 4.73 | -2.26 | 6.98 | no |  | yes | yes |
| q8 | ASIA | T4A_PB3B_R5_P1_t45_s60 | ASIA | 23 | SESSION-CANDIDATE |  | 1.80 [-4.03, 7.64] | 8.01 | 0.96 / 4.43 | -4.28 | 1 / 1.00 | 1.69 / 1.80 | -3.45 | 5.25 | yes |  | yes | yes |
| q8 | NY | T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | NY | 11 | SESSION-CANDIDATE |  | 1.99 [-1.43, 5.42] | 4.70 | 2.13 / 1.33 | -2.75 | 1 / 1.00 | 1.47 / 1.99 | -3.04 | 5.03 | yes |  | yes | yes |
| q8 | ASIA | PB3B_R5_P1 | ASIA | 2 | SESSION-CANDIDATE |  | 3.16 [-3.21, 9.53] | 8.75 | 3.89 / 0.66 | -4.84 | 1 / 1.00 | 1.99 / 3.16 | -3.13 | 6.29 | yes |  | yes | yes |
| q8 | NY | T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | NY | 8 | SESSION-CANDIDATE |  | 1.42 [-2.97, 5.81] | 6.03 | 1.35 / 1.75 | -3.73 | 1 / 1.00 | 1.50 / 1.42 | -5.27 | 6.69 | no |  | no | yes |
| q8 | NY | T4A_PB3D_R3_P2_t30_s40 | NY | 27 | SESSION-CANDIDATE |  | 0.18 [-2.56, 2.93] | 3.76 | 0.18 / 0.19 | -1.82 | 1 / 1.00 | 0.86 / 0.18 | -3.29 | 3.47 | yes |  | yes | yes |
| q8 | ASIA | T4A_PRO_Z20_t1.0_t60_s50 | ASIA | 34 | SESSION-CANDIDATE |  | 1.85 [-3.29, 7.00] | 7.06 | 0.17 / 8.23 | -0.14 | 1 / 1.00 | 1.26 / 1.85 | -3.55 | 5.40 | yes |  | yes | yes |

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T4A_PRO_KAL_k0.0_t60_s50 | NY | NOT-MEASURED-CANDIDATE |  / 3.82 / 5.80 |  / 0.44 / 2.00 | 374 | -0.32 / 5.02 | 7.71 | 2.05 | -2.99 / 3.43 | yes |  | no |
| PBX_PB3B_R5_P2_f60_T3 | NY-AM | SESSION-CANDIDATE |  / 10.24 / 9.97 |  / 5.71 / 6.12 | 150 | 5.09 / 7.76 | 21.59 | 0.00 | 1.42 / 4.29 | yes |  | yes |
| PBX4_PBS_f60_T3_DFLIP | LONDON | SESSION-CANDIDATE |  / 14.95 / 17.30 |  / 16.34 / 18.10 | 75 | 17.14 / 13.97 | 29.24 | 11.59 | 5.89 / 10.45 | yes |  | yes |
| PB3E_C_R3_P2_60_1.5R | LONDON | SESSION-CANDIDATE |  / 7.63 / 9.09 |  / 4.73 / 5.54 | 117 | 4.45 / 5.44 | 20.07 | -8.81 | -2.26 / 6.98 | no |  | yes |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s75 | NY | NOT-MEASURED-CANDIDATE |  / 5.05 / 6.07 |  / 0.02 / 2.57 | 152 | -1.00 / 7.61 | 13.51 | -3.84 | -3.93 / 3.95 | yes |  | no |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | LONDON | NOT-MEASURED-CANDIDATE |  / 3.12 / 5.51 |  / -1.82 / 0.09 | 207 | -1.82 / -1.81 | 7.28 | -6.23 | -2.82 / 1.00 | yes |  | no |
| T4A_PB3D_R3_P2_t45_s90 | ASIA | NOT-MEASURED-CANDIDATE |  / 4.38 / 6.51 |  / -3.79 / -1.54 | 210 | -4.60 / 0.14 | 10.87 | -2.41 | -3.43 / -0.36 | no |  | no |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s90 | ASIA | NOT-MEASURED-CANDIDATE |  / 4.38 / 6.51 |  / -3.79 / -1.54 | 210 | -4.60 / 0.14 | 10.87 | -2.41 | -3.43 / -0.36 | no |  | no |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s75 | ASIA | NOT-MEASURED-CANDIDATE |  / 4.01 / 5.58 |  / -4.43 / -1.87 | 217 | -4.62 / -3.51 | 8.51 | -0.46 | -3.71 / -0.72 | no |  | no |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s50 | ASIA | NOT-MEASURED-CANDIDATE |  / 2.90 / 4.03 |  / 0.49 / 2.46 | 234 | -1.17 / 8.58 | 6.85 | 1.14 | -2.02 / 2.51 | yes |  | no |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s60 | ASIA | NOT-MEASURED-CANDIDATE |  / 3.38 / 4.70 |  / -2.11 / 0.49 | 227 | -3.72 / 5.91 | 7.42 | 0.47 | -3.15 / 1.04 | no |  | no |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s60 | ASIA | NOT-MEASURED-CANDIDATE |  / 3.30 / 4.62 |  / -2.11 / 0.49 | 227 | -3.72 / 5.91 | 7.42 | 0.47 | -3.15 / 1.04 | no |  | no |
| T4A_PB3D_R3_P2_t45_s60 | ASIA | NOT-MEASURED-CANDIDATE |  / 3.30 / 4.62 |  / -2.11 / 0.49 | 227 | -3.72 / 5.91 | 7.42 | 0.47 | -3.15 / 1.04 | no |  | no |
| T4A_PB3D_R3_P2_t45_s50 | ASIA | NOT-MEASURED-CANDIDATE |  / 2.68 / 3.82 |  / 0.66 / 2.64 | 235 | -0.96 / 8.58 | 6.81 | 1.14 | -2.03 / 2.70 | yes |  | no |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | ASIA | NOT-MEASURED-CANDIDATE |  / 2.68 / 3.82 |  / 0.66 / 2.64 | 235 | -0.96 / 8.58 | 6.81 | 1.14 | -2.03 / 2.70 | yes |  | no |
| T4A_PB3D_R3_P2_t60_s90 | ASIA | NOT-MEASURED-CANDIDATE |  / 4.81 / 6.24 |  / -3.92 / -2.14 | 191 | -4.45 / -1.21 | 13.51 | -6.53 | -2.08 / -1.84 | no |  | no |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s90 | ASIA | NOT-MEASURED-CANDIDATE |  / 4.81 / 6.24 |  / -3.92 / -2.14 | 191 | -4.45 / -1.21 | 13.51 | -6.53 | -2.08 / -1.84 | no |  | no |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s90 | ASIA | NOT-MEASURED-CANDIDATE |  / 3.89 / 6.28 |  / -3.11 / -0.93 | 195 | -4.11 / 1.63 | 10.86 | -2.41 | -3.73 / 0.62 | no |  | no |
| T4A_PRO_Z20_t1.0_t60_s40 | ASIA | NOT-MEASURED-CANDIDATE |  / 1.99 / 3.61 |  / -0.55 / 0.25 | 466 | -0.98 / 0.83 | 5.49 | 2.96 | -4.55 / 4.00 | yes |  | no |
| T4A_PB3B_R5_P1_t60_s50 | ASIA | NOT-MEASURED-CANDIDATE |  / 2.41 / 3.16 |  / 1.68 / 3.86 | 321 | 2.34 / -0.61 | 8.80 | -4.67 | -3.43 / 5.11 | yes |  | no |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | ASIA | NOT-MEASURED-CANDIDATE |  / 2.53 / 3.03 |  / -3.41 / -1.66 | 234 | -5.64 / 7.43 | 7.39 | 2.22 | -4.21 / 0.80 | no |  | no |
| T4A_PB3B_R5_P1_t60_s40 | ASIA | NOT-MEASURED-CANDIDATE |  / 1.87 / 2.93 |  / 2.31 / 4.01 | 368 | 3.11 / -0.61 | 7.86 | -4.08 | -3.63 / 5.95 | yes |  | no |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s60 | ASIA | NOT-MEASURED-CANDIDATE |  / 3.45 / 4.03 |  / -5.49 / -3.27 | 203 | -7.06 / 2.61 | 9.24 | -2.09 | -2.73 / -2.75 | no |  | no |
| T4A_PRO_KAL_k0.0_t60_s40 | NY | NOT-MEASURED-CANDIDATE |  / 1.57 / 2.24 |  / -2.42 / -0.75 | 512 | -2.53 / -1.60 | 5.52 | 0.85 | -3.39 / 0.97 | yes |  | no |
| T4A_PB3B_R5_P1_t45_s60 | ASIA | SESSION-CANDIDATE |  / 1.69 / 3.65 |  / 1.80 / 4.79 | 371 | 0.96 / 4.43 | 8.01 | -4.28 | -3.45 / 5.25 | yes |  | yes |

All cell-sessions with every column: out/ssa/cs_scores_q8.csv.
