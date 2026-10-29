# DS3_SESSION2_Q_sd34 - live-latency replay of the sd34 survivors (D3SQ), q4
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q4.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q4/, scores out/ssa/cs_scores_q4.csv (replayed) and cs_analytic_q4.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 7; MEASURED V0 gate (HOLD, H25, H26 > 0) 0; at 1 s 0; CONSERVATIVE stress yes 2; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 1; gate_M0 AND edge-beyond-beta 0. Source beats_beta flag true for 0 replayed cell-sessions (false 0, NA 7). Non-replayable (MEASURED-ANALYTIC, label only): 0 cell-sessions, 0 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=0): median beta HOLD +nan pts, median edge HOLD +nan, median MEASURED HOLD +nan; HOLD edge > 0 for 0, HOLD edge 95% CI lower bound > 0 for 0 (0 clusters); MEASURED HOLD CI lower bound > 0 for 0. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| LONDON    |             1 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| PREOPEN   |             1 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-AM     |             5 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY        |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-PM     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| CLOSE     |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRNG|LONDON|NY-AM|BC|p0|1m|60/60 | NY-AM | NOT-MEASURED-CANDIDATE |  / 6.62 / 5.86 |  / -1.72 / -4.49 | 128 | -4.96 / 9.83 | 13.26 | -4.52 | -3.04 / 1.32 | no |  | no |
| PRNG|LONDON|NY-AM|BC|p0|30s|60/60 | NY-AM | NOT-MEASURED-CANDIDATE |  / 4.81 / 3.84 |  / -2.62 / -3.44 | 132 | -6.57 / 11.42 | 11.11 | -2.37 | -3.10 / 0.48 | no |  | no |
| SOPEN|own|LONDON|EX|k1|1m|40/40 | LONDON | NOT-MEASURED-CANDIDATE |  / 5.00 / 2.89 |  / -5.55 / -3.37 | 28 | -9.67 / 0.81 | 26.70 | -8.81 | -2.88 / -2.67 | no |  | no |
| PRNG|LONDON|NYKZ|BC|p0|30s|30/60 | NY-AM | NOT-MEASURED-CANDIDATE |  / 4.18 / 3.30 |  / 0.13 / 4.81 | 84 | 0.37 / -0.66 | 13.37 | -0.21 | -2.06 / 2.18 | yes |  | no |
| PRNG|LONDON|NY-AM|BC|p0|1m|30/60 | NY-AM | NOT-MEASURED-CANDIDATE |  / 2.76 / 3.47 |  / 0.11 / 0.90 | 128 | -3.34 / 12.44 | 11.20 | -4.67 | -0.19 / 0.30 | no |  | no |
| PRNG|LONDON|NYKZ|BC|p0|1m|30/60 | NY-AM | NOT-MEASURED-CANDIDATE |  / 3.05 / 3.14 |  / 0.83 / 3.47 | 82 | -0.12 / 3.78 | 14.38 | -1.18 | -1.37 / 2.20 | no |  | no |
| PVWAP|LONDON|PRE|BC|p0|1m|30/60 | PREOPEN | NOT-MEASURED-CANDIDATE |  / 0.97 / 1.48 |  / -1.44 / -0.89 | 97 | 0.22 / -8.26 | 8.77 | -0.69 | -2.37 / 0.93 | no |  | no |

All cell-sessions with every column: out/ssa/cs_scores_q4.csv.

FLAG PARTIAL: q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed
