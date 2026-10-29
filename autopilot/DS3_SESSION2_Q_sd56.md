# DS3_SESSION2_Q_sd56 - live-latency replay of the sd56 survivors (D3SQ), q5
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q5.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q5/, scores out/ssa/cs_scores_q5.csv (replayed) and cs_analytic_q5.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 13; MEASURED V0 gate (HOLD, H25, H26 > 0) 1; at 1 s 3; CONSERVATIVE stress yes 5; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 9; gate_M0 AND edge-beyond-beta 1. Source beats_beta flag true for 0 replayed cell-sessions (false 0, NA 13). Non-replayable (MEASURED-ANALYTIC, label only): 0 cell-sessions, 0 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=1): median beta HOLD +0.27 pts, median edge HOLD +4.29, median MEASURED HOLD +4.56; HOLD edge > 0 for 1, HOLD edge 95% CI lower bound > 0 for 0 (0 clusters); MEASURED HOLD CI lower bound > 0 for 0. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |             7 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| LONDON    |             1 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| PREOPEN   |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-AM     |             5 |         1 |             1 |                           1 |                         0 |                     0 |                   0 |
| NY        |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-PM     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q5 | NY-AM | sd56/NY-AM/X:SB_HM_st_vw_5/t60s40/run | NY-AM | 12 | SESSION-CANDIDATE |  | 4.56 [-4.88, 14.00] | 12.96 | 3.74 / 9.43 | -1.11 | 1 / 1.00 | 4.46 / 4.56 | 0.27 | 4.29 | yes |  | yes | yes |

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd56/ASIA/EM/t40s60/flat | ASIA | NOT-MEASURED-CANDIDATE |  / 5.47 / 5.42 |  / 0.97 / 2.63 | 134 | -1.86 / 13.30 | 8.35 | -0.62 | -3.20 / 4.17 | yes |  | no |
| sd56/ASIA/EM/s40/run | ASIA | NOT-MEASURED-CANDIDATE |  / 5.64 / 5.06 |  / 0.50 / 2.86 | 145 | -1.36 / 9.04 | 9.30 | -2.21 | -4.24 / 4.75 | yes |  | no |
| sd56/NY-AM/X:SB_HM_st_sig0/t60s40/run | NY-AM | NOT-MEASURED-CANDIDATE |  / 7.36 / 7.59 |  / 2.96 / 2.91 | 99 | -0.73 / 15.90 | 17.71 | 6.36 | -0.04 / 3.00 | no |  | no |
| sd56/NY-AM/X:SB_HM_st_sig0/t60s40/carry | NY-AM | NOT-MEASURED-CANDIDATE |  / 7.36 / 7.59 |  / 2.96 / 2.91 | 99 | -0.73 / 15.90 | 17.71 | 6.36 | -0.04 / 3.00 | no |  | no |
| sd56/NY-AM/X:SB_HM_st_sig0/t60s40/flat | NY-AM | NOT-MEASURED-CANDIDATE |  / 6.83 / 7.12 |  / 1.55 / 1.48 | 99 | -2.28 / 14.93 | 17.25 | 6.21 | -0.50 / 2.05 | no |  | no |
| sd56/ASIA/HM/t40s60/flat | ASIA | NOT-MEASURED-CANDIDATE |  / 3.08 / 3.82 |  / -0.07 / 1.86 | 344 | -1.32 / 4.41 | 5.35 | -0.54 | -3.83 / 3.76 | yes |  | no |
| sd56/NY-AM/X:SB_HM_st_sig0/s60/run | NY-AM | NOT-MEASURED-CANDIDATE |  / 6.72 / 8.20 |  / 1.95 / 1.33 | 99 | -2.72 / 18.28 | 19.45 | 3.73 | -4.27 / 6.21 | yes |  | no |
| sd56/NY-AM/X:SB_HM_st_vw_5/t60s40/run | NY-AM | SESSION-CANDIDATE |  / 4.46 / 4.72 |  / 4.56 / 4.54 | 146 | 3.74 / 9.43 | 12.96 | -1.11 | 0.27 / 4.29 | yes |  | yes |
| sd56/ASIA/PE/t60s40/flat | ASIA | NOT-MEASURED-CANDIDATE |  / 2.46 / 2.98 |  / -0.68 / 0.13 | 318 | -0.57 / -1.06 | 6.82 | -2.13 | -3.18 / 2.50 | yes |  | no |
| sd56/LONDON/X:IF_5m_tg_pd/s60/run | LONDON | NOT-MEASURED-CANDIDATE |  / 6.69 / 7.64 |  / -3.53 / -0.92 | 111 | -7.20 / 21.92 | 17.60 | 0.35 | -2.93 / -0.60 | no |  | no |
| sd56/ASIA/PE/t60s40/run | ASIA | NOT-MEASURED-CANDIDATE |  / 2.93 / 3.61 |  / 1.48 / 3.39 | 318 | 2.08 / -0.51 | 7.40 | -4.87 | -2.81 / 4.29 | yes |  | no |
| sd56/ASIA/HM/t40s60/run | ASIA | NOT-MEASURED-CANDIDATE |  / 2.96 / 4.21 |  / 0.77 / 3.62 | 344 | -0.28 / 4.55 | 5.90 | -0.96 | -4.96 / 5.73 | yes |  | no |
| sd56/ASIA/SM/s60/run | ASIA | NOT-MEASURED-CANDIDATE |  / 5.89 / 7.12 |  / -0.89 / 2.32 | 113 | 0.21 / -5.19 | 16.39 | 2.23 | -4.79 / 3.90 | yes |  | no |

All cell-sessions with every column: out/ssa/cs_scores_q5.csv.
