# DS3_SESSION2_Q_sd6b - live-latency replay of the sd6b survivors (D3SQ), q7
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q7.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q7/, scores out/ssa/cs_scores_q7.csv (replayed) and cs_analytic_q7.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 13; MEASURED V0 gate (HOLD, H25, H26 > 0) 12; at 1 s 11; CONSERVATIVE stress yes 13; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 13; gate_M0 AND edge-beyond-beta 12. Source beats_beta flag true for 0 replayed cell-sessions (false 0, NA 13). Non-replayable (MEASURED-ANALYTIC, label only): 0 cell-sessions, 0 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=12): median beta HOLD -2.67 pts, median edge HOLD +8.78, median MEASURED HOLD +6.36; HOLD edge > 0 for 12, HOLD edge 95% CI lower bound > 0 for 2 (2 clusters); MEASURED HOLD CI lower bound > 0 for 0. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |             5 |         4 |             4 |                           4 |                         0 |                     0 |                   0 |
| LONDON    |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| PREOPEN   |             4 |         4 |             4 |                           4 |                         0 |                     0 |                   0 |
| NY-AM     |             4 |         4 |             4 |                           4 |                         0 |                     0 |                   0 |
| NY        |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-PM     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q7 | NY-AM | ba2/HM_t75_s90 | NY-AM | q7:4 | SESSION-PASS |  | 7.25 [-6.64, 21.14] | 19.07 | 2.56 / 32.33 | 11.04 | 1 / 1.00 | 12.90 / 7.25 | -3.63 | 10.88 | yes |  | yes | yes |
| q7 | NY-AM | ba2/HM_t90_s90 | NY-AM | q7:5 | SESSION-PASS |  | 7.64 [-6.83, 22.10] | 19.86 | 2.28 / 36.56 | 14.89 | 1 / 1.00 | 13.09 / 7.64 | -3.32 | 10.96 | yes |  | yes | yes |
| q7 | ASIA | ba2/SM_t75_sst | ASIA | q7:1 | SESSION-PASS |  | 6.01 [-3.63, 15.65] | 13.24 | 5.88 / 6.87 | 4.78 | 2 / 2.00 | 8.09 / 6.01 | 0.36 | 5.65 | yes |  | yes | yes |
| q7 | ASIA | ba2/SM_t90_sst | ASIA | q7:2 | SESSION-PASS |  | 5.20 [-5.36, 15.76] | 14.49 | 4.22 / 11.85 | 7.10 | 2 / 2.00 | 8.52 / 5.20 | -0.17 | 5.36 | yes |  | yes | yes |
| q7 | PREOPEN | pb4:tick_1000|ST10|SW62|T2|60/60 | PREOPEN | q7:10 | SESSION-CANDIDATE |  | 8.62 [-8.99, 26.24] | 24.18 | 4.55 / 19.05 | 1.90 | 1 / 0.83 | 12.15 / 8.62 | -2.68 | 11.30 | yes |  | yes | yes |
| q7 | PREOPEN | pb4:volume_1000|ST10|SW62|T2|60/60 | PREOPEN | q7:11 | SESSION-CANDIDATE |  | 9.39 [-5.71, 24.50] | 20.74 | 4.33 / 21.31 | 8.57 | 1 / 0.83 | 9.04 / 9.39 | -4.84 | 14.23 | yes |  | yes | yes |
| q7 | PREOPEN | pb4:volume_1000|ST5|SW62|T2|60/60 | PREOPEN | q7:12 | SESSION-CANDIDATE |  | 11.35 [-3.68, 26.38] | 20.64 | 8.34 / 19.69 | 15.25 | 1 / 0.83 | 10.61 / 11.35 | -3.86 | 15.21 | yes |  | yes | yes |
| q7 | NY-AM | ba2/KB_t90_s90 | NY-AM | q7:6 | SESSION-PASS |  | 6.72 [-4.61, 18.04] | 15.55 | 5.18 / 15.43 | 8.10 | 1 / 1.00 | 8.17 / 6.72 | -2.66 | 9.38 | yes |  | yes | yes |
| q7 | ASIA | ba2/EM_t60_s40 | ASIA | q7:0 | SESSION-PASS |  | 3.75 [-9.75, 17.25] | 18.53 | 0.11 / 34.06 | -4.12 | 1 / 1.00 | 5.40 / 3.75 | -0.75 | 4.50 | yes |  | yes | yes |
| q7 | ASIA | tsoHM10/r1.5 | ASIA | q7:3 | SESSION-PASS |  | 2.88 [-6.68, 12.44] | 13.13 | 1.46 / 12.39 | -3.65 | 1 / 1.00 | 5.57 / 2.88 | -0.41 | 3.29 | yes |  | yes | yes |
| q7 | NY-AM | pb4:min_1|ST3|VWAP|T2|60/60 | NY-AM | q7:8 | SESSION-CANDIDATE |  | 1.83 [-6.16, 9.83] | 10.98 | 1.92 / 1.47 | 0.41 | 1 / 0.83 | 5.06 / 1.83 | -4.48 | 6.31 | yes |  | yes | yes |
| q7 | PREOPEN | pb4:tick_1000|ST10|SW62|T2|40/40 | PREOPEN | q7:9 | SESSION-CANDIDATE |  | 5.60 [-1.62, 12.82] | 9.91 | 3.70 / 10.14 | -1.52 | 1 / 1.25 | 4.40 / 5.60 | -2.58 | 8.18 | yes |  | yes | yes |

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ba2/HM_t75_s90 | NY-AM | SESSION-PASS |  / 12.90 / 15.20 |  / 7.25 / 10.33 | 184 | 2.56 / 32.33 | 19.07 | 11.04 | -3.63 / 10.88 | yes |  | yes |
| ba2/HM_t90_s90 | NY-AM | SESSION-PASS |  / 13.09 / 16.99 |  / 7.64 / 11.13 | 128 | 2.28 / 36.56 | 19.86 | 14.89 | -3.32 / 10.96 | yes |  | yes |
| ba2/SM_t75_sst | ASIA | SESSION-PASS |  / 8.09 / 7.21 |  / 6.01 / 5.94 | 86 | 5.88 / 6.87 | 13.24 | 4.78 | 0.36 / 5.65 | yes |  | yes |
| ba2/SM_t90_sst | ASIA | SESSION-PASS |  / 8.52 / 7.69 |  / 5.20 / 6.28 | 86 | 4.22 / 11.85 | 14.49 | 7.10 | -0.17 / 5.36 | yes |  | yes |
| pb4:tick_1000|ST10|SW62|T2|60/60 | PREOPEN | SESSION-CANDIDATE |  / 12.15 / 11.94 |  / 8.62 / 11.14 | 57 | 4.55 / 19.05 | 24.18 | 1.90 | -2.68 / 11.30 | yes |  | yes |
| pb4:volume_1000|ST10|SW62|T2|60/60 | PREOPEN | SESSION-CANDIDATE |  / 9.04 / 8.55 |  / 9.39 / 18.24 | 57 | 4.33 / 21.31 | 20.74 | 8.57 | -4.84 / 14.23 | yes |  | yes |
| pb4:volume_1000|ST5|SW62|T2|60/60 | PREOPEN | SESSION-CANDIDATE |  / 10.61 / 8.78 |  / 11.35 / 16.39 | 49 | 8.34 / 19.69 | 20.64 | 15.25 | -3.86 / 15.21 | yes |  | yes |
| ba2/KB_t90_s90 | NY-AM | SESSION-PASS |  / 8.17 / 8.34 |  / 6.72 / 7.73 | 327 | 5.18 / 15.43 | 15.55 | 8.10 | -2.66 / 9.38 | yes |  | yes |
| ba2/EM_t60_s40 | ASIA | SESSION-PASS |  / 5.40 / 5.43 |  / 3.75 / 5.73 | 84 | 0.11 / 34.06 | 18.53 | -4.12 | -0.75 / 4.50 | yes |  | yes |
| pb4:min_1|ST3|E20_1|T1|60/60 | ASIA | NOT-MEASURED-CANDIDATE |  / 3.26 / 4.05 |  / 0.25 / 2.53 | 371 | -0.43 / 2.19 | 7.54 | -1.96 | -4.02 / 4.27 | yes |  | no |
| tsoHM10/r1.5 | ASIA | SESSION-PASS |  / 5.57 / 6.78 |  / 2.88 / 4.03 | 169 | 1.46 / 12.39 | 13.13 | -3.65 | -0.41 / 3.29 | yes |  | yes |
| pb4:min_1|ST3|VWAP|T2|60/60 | NY-AM | SESSION-CANDIDATE |  / 5.06 / 6.13 |  / 1.83 / 6.11 | 148 | 1.92 / 1.47 | 10.98 | 0.41 | -4.48 / 6.31 | yes |  | yes |
| pb4:tick_1000|ST10|SW62|T2|40/40 | PREOPEN | SESSION-CANDIDATE |  / 4.40 / 6.94 |  / 5.60 / 6.77 | 61 | 3.70 / 10.14 | 9.91 | -1.52 | -2.58 / 8.18 | yes |  | yes |

All cell-sessions with every column: out/ssa/cs_scores_q7.csv.
