# DS3_SESSION2_Q_sd1 - live-latency replay of the sd1 survivors (D3SQ), q3
Research only; UNTOUCHED never read. Prereg SSA_prereg.md 73f0a1ca...e762 + SSA_Q_addendum.md 1ad023193ef99ac3313423a581969025a376b52707f25b2a8d83f008fc00b31f (hashed in DECISIONS.md before any fill). Entries out/ssa/entries_q3.parquet (real + side-flipped beta placebo), fills in /mnt/l2/l2vast/ds3_ssa_q3/, scores out/ssa/cs_scores_q3.csv (replayed) and cs_analytic_q3.csv (non-replayable, MEASURED-ANALYTIC).

## 1. Counts
Replayed cell-sessions 103; MEASURED V0 gate (HOLD, H25, H26 > 0) 12; at 1 s 12; CONSERVATIVE stress yes 36; EDGE-BEYOND-BETA (PRE edge CI lo > 0, HOLD edge > 0, H25 edge > 0) 44; gate_M0 AND edge-beyond-beta 7. Source beats_beta flag true for 0 replayed cell-sessions (false 0, NA 103). Non-replayable (MEASURED-ANALYTIC, label only): 0 cell-sessions, 0 alive on the analytic MEASURED basis.

Beta check on the MEASURED-gate cell-sessions (n=8): median beta HOLD -2.71 pts, median edge HOLD +5.41, median MEASURED HOLD +2.53; HOLD edge > 0 for 8, HOLD edge 95% CI lower bound > 0 for 3 (3 clusters); MEASURED HOLD CI lower bound > 0 for 0. NOTE the EDGE-BEYOND-BETA label uses the PRE edge CI, which is selection-biased (cells were PRE-selected on the real mean); the HOLD edge columns are the honest part. The flip placebo (same entries, opposite side) differs from the harness beats_beta gate (random direction on the 09:31 clock, all days), so the two flags need not agree.

## 2. New session books found (independent overlap clusters, cluster50 of the source) per session
| session   |   replayed_cs |   gate_M0 |   clusters_M0 |   clusters_edge_beyond_beta |   clusters_beats_beta_src |   analytic_only_alive |   analytic_clusters |
|:----------|--------------:|----------:|--------------:|----------------------------:|--------------------------:|----------------------:|--------------------:|
| ASIA      |            25 |         3 |             3 |                           3 |                         0 |                     0 |                   0 |
| LONDON    |            13 |         1 |             1 |                           0 |                         0 |                     0 |                   0 |
| PREOPEN   |            13 |         1 |             1 |                           1 |                         0 |                     0 |                   0 |
| NY-AM     |            19 |         2 |             2 |                           1 |                         0 |                     0 |                   0 |
| NY        |             0 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |
| NY-PM     |            24 |         5 |             5 |                           2 |                         0 |                     0 |                   0 |
| CLOSE     |             9 |         0 |             0 |                           0 |                         0 |                     0 |                   0 |

"clusters_M0" = clusters with at least one cell-session passing MEASURED (replayed); "edge_beyond_beta" = the same with the EDGE-BEYOND-BETA label (directional edge net of the flip placebo); beta = (real+flip)/2, edge = (real-flip)/2, both net of cost on MEASURED.

## 3. One representative per cluster (best MEASURED PRE t among MEASURED-gate cell-sessions), pts/trade net
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q3 | ASIA | FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 8, "tf": -9500}|none|B60/60|S | ASIA | q3:76 | SESSION-CANDIDATE |  | 3.33 [-1.59, 8.25] | 6.76 | 0.06 / 12.33 | -1.32 | 1 / 1.00 | 3.93 / 3.33 | -2.33 | 5.66 | yes |  | yes | yes |
| q3 | NY-PM | CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R | NY-PM | q3:85 | SESSION-CANDIDATE |  | 5.34 [-1.93, 12.62] | 9.98 | 3.37 / 13.29 | -3.08 | 1 / 1.00 | 4.73 / 5.34 | -2.77 | 8.12 | yes |  | yes | yes |
| q3 | PREOPEN | CRT|PRE|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R | PREOPEN | q3:83 | SESSION-CANDIDATE |  | 3.93 [-3.98, 11.85] | 10.86 | 3.90 / 4.08 | -6.03 | 1 / 1.00 | 6.05 / 3.93 | -3.63 | 7.56 | yes |  | yes | yes |
| q3 | NY-AM | BOS|NYAM|tf2|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|R | NY-AM | q3:49 | SESSION-CANDIDATE |  | 1.41 [-6.21, 9.04] | 10.47 | 0.06 / 7.71 | -3.77 | 1 / 1.00 | 5.60 / 1.41 | -2.84 | 4.25 | yes |  | yes | yes |
| q3 | NY-PM | CRT|NYPM|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R | NY-PM | q3:68 | SESSION-CANDIDATE |  | 1.72 [-5.12, 8.57] | 9.40 | 0.91 / 5.16 | 0.15 | 1 / 1.00 | 2.96 / 1.72 | -2.58 | 4.30 | yes |  | yes | yes |
| q3 | ASIA | FV|ASIA|tf-9500|{"entry": "c", "sing": 10, "size": 8, "tf": -9500}|none|B50/50|S | ASIA | q3:74 | SESSION-CANDIDATE |  | 0.64 [-4.27, 5.54] | 6.73 | 0.17 / 1.92 | -1.14 | 1 / 1.00 | 1.32 / 0.64 | -2.65 | 3.28 | yes |  | yes | yes |
| q3 | NY-AM | BOS|NYAM|tf2|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|R | NY-AM | q3:52 | SESSION-CANDIDATE |  | 3.81 [-8.24, 15.86] | 16.54 | 3.91 / 3.40 | -8.30 | 1 / 1.00 | 3.80 / 3.81 | -2.65 | 6.46 | no |  | yes | no |
| q3 | LONDON | CRT|LONDON|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 240, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|S | LONDON | q3:81 | SESSION-CANDIDATE |  | 1.57 [-5.42, 8.57] | 9.61 | 1.51 / 1.83 | -1.38 | 5 / 5.00 | -0.92 / 1.57 | -3.59 | 5.16 | no |  | yes | yes |

## 4. Top 25 replayed cell-sessions by MEASURED PRE t regardless of gate: stored vs MEASURED vs CONSERVATIVE
| cell | window | tier MEAS | PRE S / M0 / C | HOLD S / M0 / C | HOLD n | H25 / H26 (M0) | MDE | 2023 span M0 | beta / edge HOLD | EBB | beats_beta | gate_M0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IF|NYAM|tf2|{"entry": "d", "sing": 10, "size": 16, "tf": 2}|deliv|B40/40|R | NY-AM | PROXY-NOT-MEASURED-CANDIDATE |  / 9.50 / 9.22 |  / 0.73 / -0.20 | 51 | -1.35 / 13.78 | 12.43 | -0.01 | -3.31 / 4.04 | yes |  | no |
| FV|ASIA|tf-15|{"entry": "d", "sing": 10, "size": 8, "tf": -15}|deliv|B60/60|R | ASIA | PROXY-NOT-MEASURED-CANDIDATE |  / 5.48 / 4.97 |  / 0.61 / 1.55 | 413 | 1.13 / -0.80 | 7.67 | 1.43 | -3.59 / 4.21 | yes |  | no |
| FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 8, "tf": -9500}|none|B60/60|S | ASIA | SESSION-CANDIDATE |  / 3.93 / 5.27 |  / 3.33 / 4.53 | 285 | 0.06 / 12.33 | 6.76 | -1.32 | -2.33 / 5.66 | yes |  | yes |
| CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R | NY-PM | SESSION-CANDIDATE |  / 4.73 / 5.28 |  / 5.34 / 6.71 | 211 | 3.37 / 13.29 | 9.98 | -3.08 | -2.77 / 8.12 | yes |  | yes |
| FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 16, "tf": -9500}|none|B60/60|R | ASIA | NOT-MEASURED-CANDIDATE |  / 5.51 / 8.38 |  / 0.43 / 2.82 | 258 | -2.12 / 7.30 | 10.35 | -4.07 | -3.02 / 3.45 | yes |  | no |
| CRT|PRE|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R | PREOPEN | SESSION-CANDIDATE |  / 6.05 / 6.62 |  / 3.93 / 4.61 | 82 | 3.90 / 4.08 | 10.86 | -6.03 | -3.63 / 7.56 | yes |  | yes |
| CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R | NY-PM | NOT-MEASURED-CANDIDATE |  / 2.93 / 4.35 |  / 3.01 / 6.44 | 228 | -0.09 / 14.95 | 8.47 | -3.79 | -3.19 / 6.20 | yes |  | no |
| IF|ASIA|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|deliv|B60/60|R | ASIA | PROXY-SESSION-CANDIDATE |  / 4.53 / 6.70 |  / 3.01 / 5.95 | 374 | 1.69 / 6.61 | 10.41 | -0.84 | -3.20 / 6.21 | yes |  | yes |
| FV|ASIA|tf-9500|{"entry": "c", "sing": 10, "size": 16, "tf": -9500}|none|B60/60|R | ASIA | NOT-MEASURED-CANDIDATE |  / 4.28 / 6.94 |  / 0.32 / 2.73 | 247 | -2.10 / 7.11 | 10.45 | -4.92 | -3.28 / 3.60 | yes |  | no |
| FV|NYPM|tf2|{"entry": "b", "sing": 0, "size": 4, "tf": 2}|mom|B60/60|R | NY-PM | PROXY-NOT-MEASURED-CANDIDATE |  / 4.62 / 7.69 |  / -1.75 / 1.55 | 226 | -1.72 / -1.88 | 9.53 | -0.32 | -2.40 / 0.65 | yes |  | no |
| BOS|NYAM|tf2|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|R | NY-AM | SESSION-CANDIDATE |  / 5.60 / 7.88 |  / 1.41 / 3.06 | 175 | 0.06 / 7.71 | 10.47 | -3.77 | -2.84 / 4.25 | yes |  | yes |
| FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 16, "tf": -9500}|deliv|B60/60|R | ASIA | NOT-MEASURED-CANDIDATE |  / 5.39 / 7.75 |  / 0.12 / 2.41 | 180 | -0.61 / 2.03 | 9.26 | 1.98 | -3.05 / 3.18 | yes |  | no |
| CRT|PRE|tf-10|{"L": 3, "buf": 0, "etf": -10, "etype": "csd", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|R | PREOPEN | NOT-MEASURED-CANDIDATE |  / 6.75 / 7.64 |  / -0.90 / 1.48 | 84 | -0.51 / -2.59 | 19.74 | -9.20 | -3.37 / 2.47 | yes |  | no |
| CRT|NYPM|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R | NY-PM | SESSION-CANDIDATE |  / 2.96 / 3.07 |  / 1.72 / 3.45 | 225 | 0.91 / 5.16 | 9.40 | 0.15 | -2.58 / 4.30 | yes |  | yes |
| SWEEP|ASIA|tf1|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "A"}|none|STR|S | ASIA | NOT-MEASURED-CANDIDATE |  / 5.19 / 5.57 |  / -0.83 / -0.64 | 135 | -1.86 / 11.99 | 7.74 | -2.76 | -0.10 / -0.73 | no |  | no |
| BOS|NYAM|tf1|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "B"}|none|B60/60|R | NY-AM | NOT-MEASURED-CANDIDATE |  / 4.32 / 5.40 |  / -1.90 / 0.08 | 216 | -2.27 / -0.11 | 9.34 | -2.51 | -2.59 / 0.70 | yes |  | no |
| CRT|NYPM|tf-10|{"L": 3, "buf": 0, "etf": -10, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R | NY-PM | NOT-MEASURED-CANDIDATE |  / 2.75 / 3.91 |  / -1.36 / 1.50 | 213 | -2.55 / 4.31 | 8.51 | 2.37 | -3.38 / 2.03 | yes |  | no |
| CRT|NYPM|tf-30|{"L": 3, "buf": 0, "etf": -30, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R | NY-PM | NOT-MEASURED-CANDIDATE |  / 2.77 / 3.68 |  / -1.53 / 1.90 | 214 | -2.78 / 3.60 | 8.25 | 0.88 | -2.98 / 1.46 | yes |  | no |
| BOS|LONDON|tf-9500|{"L": 3, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -9500, "tmode": "T1"}|none|B60/60|S | LONDON | NOT-MEASURED-CANDIDATE |  / 5.56 / 7.09 |  / 0.50 / 2.82 | 46 | -1.41 / 8.37 | 17.00 | -0.02 | -2.79 / 3.30 | yes |  | no |
| FV|NYPM|tf2|{"entry": "b", "sing": 0, "size": 8, "tf": 2}|mom|B60/60|R | NY-PM | PROXY-NOT-MEASURED-CANDIDATE |  / 4.09 / 7.04 |  / -2.14 / 1.17 | 221 | -2.20 / -1.88 | 9.49 | -1.12 | -2.40 / 0.26 | yes |  | no |
| CRT|NYAM|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "csd", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|S | NY-AM | NOT-MEASURED-CANDIDATE |  / 4.76 / 5.23 |  / 0.11 / 1.16 | 100 | -0.04 / 1.08 | 13.11 | -1.56 | -2.45 / 2.56 | yes |  | no |
| FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 8, "tf": -9500}|none|B50/50|S | ASIA | NOT-MEASURED-CANDIDATE |  / 1.67 / 2.55 |  / 0.53 / 1.45 | 339 | -0.62 / 3.63 | 7.29 | -1.06 | -2.95 / 3.48 | yes |  | no |
| FV|ASIA|tf-9500|{"entry": "c", "sing": 10, "size": 8, "tf": -9500}|none|B50/50|S | ASIA | SESSION-CANDIDATE |  / 1.32 / 2.06 |  / 0.64 / 1.03 | 326 | 0.17 / 1.92 | 6.73 | -1.14 | -2.65 / 3.28 | yes |  | yes |
| SWEEP|NYPM|tf1|{"L": 8, "bracket": "struct", "nb": 1, "s": 1, "tf": 1}|none|B40/40|R | NY-PM | NOT-MEASURED-CANDIDATE |  / 1.63 / 3.09 |  / -0.29 / 3.07 | 287 | -0.03 / -1.31 | 6.10 | -0.62 | -3.21 / 2.91 | yes |  | no |
| BOS|NYAM|tf2|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|R | NY-AM | SESSION-CANDIDATE |  / 3.80 / 4.65 |  / 3.81 / 3.05 | 126 | 3.91 / 3.40 | 16.54 | -8.30 | -2.65 / 6.46 | no |  | yes |

## 5. Limit/stop-entry cell-sessions replayed as MARKET-FALLBACK stress (labelled proxy, not a tier, not in the books table): passing the MEASURED gates as market entries
| wave | session | cell | window | cluster | tier (MEASURED) | HOLD stored | HOLD MEAS V0 [CI] | MDE | H25 / H26 | 2023 span | lots $1k (class/exact) | break-even slip PRE / HOLD (pts) | beta HOLD | edge HOLD | edge beyond beta | beats_beta (src) | 1s | stress |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| q3 | ASIA | IF|ASIA|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|deliv|B60/60|R | ASIA | q3:98 | PROXY-SESSION-CANDIDATE |  | 3.01 [-4.57, 10.59] | 10.41 | 1.69 / 6.61 | -0.84 | 1 / 1.00 | 4.53 / 3.01 | -3.20 | 6.21 | yes |  | yes | yes |
| q3 | NY-PM | IF|NYPM|tf-15|{"entry": "b", "sing": 10, "size": 16, "tf": -15}|none|B60/60|R | NY-PM | q3:87 | PROXY-SESSION-CANDIDATE |  | 1.10 [-3.47, 5.68] | 6.28 | 1.11 / 1.05 | -1.86 | 1 / 1.00 | -0.01 / 1.10 | -2.99 | 4.10 | no |  | yes | yes |
| q3 | NY-PM | OB|NYPM|tf-30|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": -30}|none|B60/60|R | NY-PM | q3:23 | PROXY-SESSION-CANDIDATE |  | 3.76 [-1.89, 9.40] | 7.75 | 3.13 / 6.51 | -6.13 | 1 / 1.00 | -0.06 / 3.76 | -2.87 | 6.62 | no |  | yes | yes |
| q3 | NY-PM | IF|NYPM|tf-15|{"entry": "b", "sing": 0, "size": 16, "tf": -15}|none|B60/60|R | NY-PM | q3:88 | PROXY-SESSION-CANDIDATE |  | 0.26 [-4.60, 5.13] | 6.68 | 0.28 / 0.21 | -1.64 | 1 / 1.00 | -0.71 / 0.26 | -2.91 | 3.17 | no |  | yes | yes |

All cell-sessions with every column: out/ssa/cs_scores_q3.csv.
