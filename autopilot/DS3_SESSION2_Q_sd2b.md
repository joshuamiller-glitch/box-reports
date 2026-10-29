# DS3_SESSION2_Q_sd2b - live-latency replay of the sd2b survivors (D3SQ), q9
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q9.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q9/, scores out/ssa/cs_scores_q9.csv (replayed) and cs_analytic_q9.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 6; MEASURED V0 gate (HOLD, H25, H26 > 0) 0; at 1 s 0; CONSERVATIVE stress yes 0; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 3; gate_M0 AND edge-beyond-beta 0. Source beats_beta flag true for 0 replayed cell-sessions (false 0, NA 6). Non-replayable (MEASURED-ANALYTIC, label only): 0 cell-sessions, 0 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=0): median beta HOLD +nan pts, median edge HOLD +nan, median MEASURED HOLD +nan; HOLD edge > 0 for 0, HOLD edge 95% CI lower bound > 0 for 0 (0 clusters); MEASURED HOLD CI lower bound > 0 for 0. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |             2 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| LONDON    |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| PREOPEN   |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-AM     |             2 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY        |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-PM     |             2 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| MA|k=10,fast=0.75,slow=0.05 | NY-AM | NOT-MEASURED-CANDIDATE |  / 6.06 / 6.24 |  / -2.75 / -1.36 | 135 | -3.62 / 2.27 | 15.55 | 0.50 | -3.45 / 0.70 | no |  | no |
| PE|R=3,P=1,ptype=1,ttype=1 | ASIA | NOT-MEASURED-CANDIDATE |  / 4.53 / 6.56 |  / -4.90 / -1.44 | 221 | -6.91 / 5.14 | 9.20 | -4.69 | -5.31 / 0.42 | no |  | no |
| HM|f=15,s=35,ema=100 | ASIA | NOT-MEASURED-CANDIDATE |  / 3.37 / 5.62 |  / -1.38 / 0.79 | 324 | -3.94 / 7.77 | 10.88 | -4.64 | -4.30 / 2.93 | yes |  | no |
| KB|k=2,n=30,m=2.0,na=20 | NY-PM | NOT-MEASURED-CANDIDATE |  / 1.44 / 2.96 |  / -0.85 / 1.28 | 218 | -2.31 / 6.09 | 9.94 | -4.81 | -3.34 / 2.50 | yes |  | no |
| MV|lbs=(5, 10, 20, 40, 80),thr=0.25,k=3 | NY-AM | NOT-MEASURED-CANDIDATE |  / 0.75 / 1.71 |  / -2.26 / -0.09 | 551 | -3.11 / 0.69 | 6.03 | -1.32 | -3.94 / 1.68 | yes |  | no |
| PE|R=15,P=1,ptype=0,ttype=0 | NY-PM | NOT-MEASURED-CANDIDATE |  / -1.56 / -0.67 |  / -3.79 / -1.82 | 313 | -4.25 / -1.91 | 6.50 | 0.99 | -3.93 / 0.14 | no |  | no |

All cell-sessions with every column: out/ssa/cs_scores_q9.csv.
