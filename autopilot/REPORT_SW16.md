# REPORT SW16 - scheduled-release event bars with 1-4 h holds (D10 H3/H4)

**Verdict: LEAD. FOUND 0, LEAD 5, INSURANCE 0.** 59 selected cells (+4 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.26; best pair-window standalone Sharpe +1.18.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Same release sets and direction rule as SW7 (THU/TNC/ALL), enter k = 5/15/30 min after the release, hold 60/120/240 min or to the 16:55 flatten.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN. Grid: 72 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| CL    |      72 |         64 |        18 |               1.228 |                2 |         10 |            0 |
| ES    |      72 |         62 |        10 |               0.836 |                2 |         10 |            0 |
| GC    |      72 |         72 |        15 |               1.217 |                2 |         10 |            0 |
| NQ    |      72 |         70 |         9 |               1.337 |                2 |          9 |            1 |
| RTY   |      72 |         70 |        14 |               0.665 |                2 |         10 |            0 |
| YM    |      72 |         72 |        19 |               1.282 |                2 |         10 |            0 |
| ZN    |      72 |         62 |         0 |              -0.145 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   10 |             6.87 |              12 |       0.16 |                       0.493 |            0.689 |           0.936 |     0.96 |       0.836 |                1.725 |
| NQ    |     100 |                    9 |            11.73 |              20 |       0.89 |                       0.651 |            0.84  |           1.117 |     0.87 |       1.337 |                2.055 |
| RTY   |     100 |                   14 |             8.18 |              14 |       0.02 |                       0.479 |            0.743 |           1.032 |     0.97 |       0.665 |                1.847 |
| YM    |     100 |                   19 |             8.68 |              14 |       0    |                       0.821 |            0.762 |           1.007 |     0.29 |       1.282 |                1.914 |
| GC    |     100 |                   15 |             8.03 |              14 |       0    |                       0.848 |            0.714 |           0.923 |     0.19 |       1.217 |                2.06  |
| CL    |     100 |                   18 |             5.57 |              11 |       0    |                       0.987 |            0.698 |           0.964 |     0.05 |       1.228 |                1.754 |
| ZN    |     100 |                    0 |             0.53 |               3 |       1    |                     nan     |            0.602 |           1.312 |   nan    |     nan     |                1.382 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | TNC release+30m dir=against hold=240m | 139 | 2 | 0.84 | 0.09 | 0.66 | 0.37 / 1.29 | 0.17 / -0.18 / 0.02 | 0.07 | 0.00 | 0.92 | -0.08 | 0.25 | 218 | NO |
| ES 2 | ALL release+30m dir=against hold=240m | 137 | 2 | 0.81 | 0.08 | 0.64 | 0.37 / 1.25 | 0.16 / -0.18 / 0.02 | 0.07 | 0.00 | 0.94 | -0.08 | 0.25 | 216 | NO |
| ES 3 | THU release+15m dir=against hold=60m | 101 | 2 | 0.59 | -0.52 | 0.15 | -0.47 / 1.02 | 0.14 / -0.22 / -0.27 | -0.07 | -0.45 | 0.85 | -0.23 | 0.00 | 160 | NO |
| ES 4 | TNC release+30m dir=against hold=flat | 143 | 2 | 0.58 | 0.35 | 0.56 | 0.37 / 1.65 | 0.12 / -0.10 / -0.00 | 0.06 | -0.12 | 0.89 | -0.10 | 0.50 | 223 | NO |
| ES 5 | TNC release+15m dir=against hold=60m | 141 | 2 | 0.56 | -0.30 | 0.36 | 0.02 / 1.21 | 0.12 / 0.02 / -0.15 | -0.03 | -0.46 | 0.92 | -0.18 | 0.50 | 220 | NO |
| ES 6 | TNC release+5m dir=against hold=240m | 137 | 2 | 0.40 | -0.13 | 0.99 | 1.92 / 1.34 | 0.04 / 0.64 / 0.13 | 0.13 | -0.59 | 0.99 | -0.01 | 0.50 | 217 | NO |
| ES 7 | ALL release+5m dir=against hold=240m | 135 | 2 | 0.38 | -0.14 | 0.97 | 1.92 / 1.17 | 0.04 / 0.64 / 0.13 | 0.13 | -0.59 | 1.00 | -0.01 | 0.50 | 215 | NO |
| ES 8 | THU release+15m dir=with hold=240m | 101 | 2 | 0.38 | -0.09 | -0.02 | -0.44 / 1.33 | -0.04 / -0.73 / 0.14 | -0.13 | 0.10 | 0.60 | -0.31 | 0.00 | 160 | NO |
| ES 9 | ALL release+30m dir=against hold=flat | 157 | 2 | 0.21 | 0.41 | 0.27 | 0.21 / 1.88 | 0.06 / -0.09 / -0.04 | 0.01 | -0.04 | 0.74 | -0.14 | 0.50 | 246 | NO |
| ES 10 | TNC release+5m dir=against hold=flat | 138 | 2 | 0.19 | 0.23 | 0.65 | 1.42 / 1.65 | -0.04 / 0.57 / 0.14 | 0.07 | -0.38 | 0.90 | -0.10 | 1.00 | 219 | NO |
| NQ 1 | TNC release+15m dir=against hold=60m | 145 | 2 | 1.34 | 0.21 | 0.38 | -0.44 / 1.06 | 0.25 / -0.47 / -0.10 | 0.05 | -0.41 | 0.83 | -0.16 | 0.75 | 226 | NO |
| NQ 2 | TNC release+5m dir=against hold=60m | 145 | 2 | 1.09 | 0.11 | 1.18 | 1.51 / 1.24 | 0.18 / -0.04 / 0.38 | 0.20 | -0.46 | 0.98 | 0.01 | 0.25 | 226 | NO |
| NQ 3 | THU release+15m dir=against hold=60m | 104 | 2 | 0.99 | -0.27 | -0.06 | -0.89 / 1.28 | 0.18 / -0.83 / -0.21 | -0.06 | -0.44 | 0.46 | -0.28 | 0.00 | 164 | NO |
| NQ 4 | TNC release+15m dir=against hold=flat | 146 | 2 | 0.62 | 0.17 | 0.69 | 0.95 / 1.13 | 0.12 / 0.40 / 0.01 | 0.14 | 0.04 | 0.95 | -0.05 | 0.00 | 227 | NO |
| NQ 5 | ALL release+15m dir=against hold=60m | 159 | 2 | 0.50 | 0.41 | -0.17 | -0.68 / 1.47 | 0.09 / -0.40 / -0.11 | -0.04 | -0.45 | 0.47 | -0.23 | 0.00 | 249 | NO |
| NQ 6 | TNC release+5m dir=against hold=240m | 145 | 2 | 0.39 | -0.02 | 0.66 | 1.09 / 1.22 | 0.05 / 0.42 / 0.05 | 0.11 | -0.75 | 0.93 | -0.07 | 0.50 | 226 | NO |
| NQ 7 | ALL release+15m dir=against hold=flat | 160 | 2 | 0.38 | 0.32 | 0.60 | 0.98 / 1.67 | 0.10 / 0.41 / 0.01 | 0.14 | 0.17 | 0.88 | -0.04 | 0.50 | 250 | NO |
| NQ 8 | ALL release+5m dir=against hold=240m | 143 | 2 | 0.35 | -0.04 | 0.64 | 1.09 / 1.59 | 0.05 / 0.42 / 0.05 | 0.11 | -0.75 | 0.89 | -0.07 | 0.50 | 224 | NO |
| NQ 9 | TNC release+5m dir=against hold=flat | 146 | 2 | 0.21 | 0.10 | 0.36 | 0.68 / 1.57 | -0.02 / 0.41 / -0.04 | 0.04 | -0.62 | 0.70 | -0.16 | 1.00 | 228 | NO |
| NQ 10 (diag) | THU release+5m dir=against hold=60m | 104 | 1 | 0.74 | -0.28 | 0.67 | 0.78 / 1.25 | 0.09 / -0.15 / 0.05 | 0.05 | -0.36 | 0.93 | -0.14 | 0.25 | 164 | diag |
| RTY 1 | THU release+30m dir=with hold=flat | 103 | 2 | 0.67 | -0.39 | -0.20 | -1.14 / 1.37 | 0.09 / -0.77 / -0.16 | -0.10 | 0.06 | 0.35 | -0.31 | 0.00 | 162 | NO |
| RTY 2 | TNC release+30m dir=against hold=60m | 144 | 2 | 0.63 | -0.56 | 0.41 | 0.26 / 1.35 | 0.08 / -0.11 / -0.08 | 0.00 | -0.38 | 0.88 | -0.18 | 0.00 | 224 | NO |
| RTY 3 | TNC release+15m dir=against hold=120m | 142 | 2 | 0.57 | 0.19 | 0.54 | 0.55 / 1.43 | 0.07 / 0.37 / -0.03 | 0.07 | -0.06 | 0.94 | -0.11 | 0.75 | 222 | NO |
| RTY 4 | TNC release+15m dir=against hold=240m | 142 | 2 | 0.48 | 0.20 | 0.66 | 0.92 / 1.34 | 0.05 / 0.52 / 0.07 | 0.11 | -0.37 | 0.94 | -0.07 | 1.00 | 222 | NO |
| RTY 5 | ALL release+5m dir=against hold=240m | 141 | 2 | 0.46 | -0.20 | 0.95 | 1.61 / 1.17 | 0.03 / 0.51 / 0.34 | 0.15 | -0.39 | 0.97 | -0.02 | 0.75 | 222 | NO |
| RTY 6 | ALL release+15m dir=against hold=240m | 140 | 2 | 0.46 | 0.16 | 0.65 | 0.92 / 1.25 | 0.05 / 0.52 / 0.07 | 0.11 | -0.37 | 0.93 | -0.08 | 1.00 | 220 | NO |
| RTY 7 | TNC release+5m dir=against hold=240m | 143 | 2 | 0.45 | -0.17 | 0.95 | 1.61 / 1.49 | 0.03 / 0.51 / 0.35 | 0.15 | -0.39 | 0.99 | -0.02 | 0.75 | 224 | NO |
| RTY 8 | TNC release+5m dir=against hold=120m | 143 | 2 | 0.43 | -0.05 | 0.79 | 1.29 / 1.19 | 0.04 / 0.43 / 0.22 | 0.11 | -0.17 | 0.97 | -0.05 | 0.50 | 224 | NO |
| RTY 9 | THU release+5m dir=against hold=120m | 102 | 2 | 0.38 | -0.36 | 0.87 | 1.57 / 1.01 | 0.01 / 0.52 / 0.37 | 0.13 | 0.11 | 0.96 | -0.04 | 0.50 | 162 | NO |
| RTY 10 | THU release+5m dir=with hold=flat | 103 | 2 | 0.26 | -0.31 | -1.25 | -3.18 / 1.59 | 0.03 / -1.17 / -0.86 | -0.35 | 0.19 | 0.01 | -0.57 | 0.00 | 163 | NO |
| YM 1 | ALL release+15m dir=with hold=60m | 156 | 2 | 1.28 | -0.09 | 0.39 | -0.81 / 1.07 | 0.21 / -0.42 / -0.36 | -0.02 | 0.12 | 0.88 | -0.19 | 0.50 | 244 | NO |
| YM 2 | THU release+15m dir=with hold=flat | 103 | 2 | 1.02 | -0.32 | 0.20 | -0.92 / 1.59 | 0.18 / -0.58 / -0.36 | -0.05 | -0.03 | 0.67 | -0.26 | 0.00 | 161 | NO |
| YM 3 | ALL release+30m dir=with hold=60m | 158 | 2 | 0.89 | 0.09 | 1.06 | 1.53 / 0.97 | 0.10 / 0.52 / 0.33 | 0.18 | 0.03 | 0.99 | 0.00 | 0.75 | 248 | LEAD |
| YM 4 | THU release+30m dir=with hold=flat | 104 | 2 | 0.85 | -0.54 | 0.65 | 0.29 / 0.95 | 0.14 / -0.14 / -0.01 | 0.07 | -0.04 | 0.91 | -0.13 | 0.50 | 164 | NO |
| YM 5 | TNC release+5m dir=against hold=240m | 142 | 2 | 0.78 | 0.20 | 1.16 | 1.69 / 1.04 | 0.11 / 0.45 / 0.39 | 0.21 | -0.35 | 0.99 | 0.02 | 0.75 | 223 | LEAD |
| YM 6 | ALL release+5m dir=against hold=240m | 140 | 2 | 0.73 | 0.19 | 1.14 | 1.69 / 1.37 | 0.10 / 0.45 / 0.39 | 0.20 | -0.35 | 1.00 | 0.01 | 0.75 | 221 | LEAD |
| YM 7 | TNC release+5m dir=against hold=120m | 142 | 2 | 0.68 | -0.09 | 1.12 | 1.68 / 1.45 | 0.11 / 0.50 / 0.37 | 0.21 | 0.14 | 0.99 | 0.01 | 0.25 | 223 | LEAD |
| YM 8 | ALL release+15m dir=with hold=flat | 157 | 2 | 0.68 | -0.44 | 0.07 | -0.81 / 1.61 | 0.10 / -0.34 / -0.38 | -0.07 | -0.23 | 0.64 | -0.28 | 0.00 | 245 | NO |
| YM 9 | THU release+5m dir=against hold=120m | 101 | 2 | 0.68 | -0.32 | 1.16 | 1.75 / 1.64 | 0.10 / 0.79 / 0.47 | 0.24 | 0.36 | 0.99 | 0.04 | 0.00 | 161 | LEAD |
| YM 10 | ALL release+5m dir=with hold=60m | 156 | 2 | 0.62 | -0.69 | -0.05 | -1.48 / 0.95 | 0.11 / -0.39 / -0.35 | -0.09 | 0.45 | 0.76 | -0.24 | 0.00 | 246 | NO |
| GC 1 | ALL release+15m dir=against hold=60m | 157 | 2 | 1.22 | -0.42 | -0.23 | -1.50 / 1.41 | 0.20 / -0.73 / -0.54 | -0.13 | 0.12 | 0.52 | -0.35 | 0.00 | 245 | NO |
| GC 2 | TNC release+15m dir=against hold=60m | 144 | 2 | 1.18 | -0.36 | 0.05 | -0.94 / 1.45 | 0.21 / -0.64 / -0.30 | -0.06 | -0.07 | 0.62 | -0.29 | 0.00 | 223 | NO |
| GC 3 | ALL release+15m dir=against hold=120m | 157 | 2 | 1.09 | -0.66 | 0.02 | -1.08 / 1.59 | 0.18 / -1.00 / -0.09 | -0.07 | 0.26 | 0.56 | -0.28 | 0.00 | 245 | NO |
| GC 4 | TNC release+15m dir=against hold=120m | 144 | 2 | 1.08 | -0.47 | 0.36 | -0.36 / 1.50 | 0.19 / -0.69 / 0.02 | 0.01 | 0.07 | 0.81 | -0.21 | 0.75 | 223 | NO |
| GC 5 | TNC release+5m dir=against hold=120m | 144 | 2 | 0.87 | -0.48 | 0.42 | -0.01 / 1.06 | 0.18 / -0.36 / 0.03 | 0.06 | 0.18 | 0.83 | -0.19 | 0.50 | 224 | NO |
| GC 6 | THU release+15m dir=against hold=60m | 103 | 2 | 0.72 | -0.51 | 0.16 | -0.29 / 1.38 | 0.11 / -0.38 / -0.10 | -0.04 | -0.08 | 0.66 | -0.28 | 0.00 | 161 | NO |
| GC 7 | THU release+30m dir=against hold=120m | 102 | 2 | 0.69 | -0.61 | 1.11 | 1.53 / 1.34 | 0.14 / -0.02 / 0.53 | 0.20 | 0.11 | 0.97 | -0.00 | 0.50 | 161 | NO |
| GC 8 | TNC release+30m dir=against hold=120m | 143 | 2 | 0.66 | -0.57 | 0.99 | 1.32 / 1.37 | 0.13 / -0.40 / 0.77 | 0.19 | 0.17 | 0.99 | -0.04 | 0.25 | 223 | NO |
| GC 9 | TNC release+5m dir=against hold=60m | 144 | 2 | 0.50 | -0.58 | 0.42 | 0.39 / 1.39 | 0.09 / -0.26 / 0.35 | 0.07 | -0.13 | 0.86 | -0.16 | 0.50 | 224 | NO |
| GC 10 | THU release+15m dir=against hold=120m | 103 | 2 | 0.47 | -0.54 | 0.40 | 0.31 / 1.45 | 0.06 / -0.38 / 0.13 | 0.00 | 0.03 | 0.73 | -0.22 | 0.75 | 161 | NO |
| CL 1 | TNC release+15m dir=with hold=120m | 141 | 2 | 1.23 | -0.68 | -0.02 | -1.54 / 1.08 | 0.22 / -0.45 / -0.57 | -0.09 | -0.01 | 0.71 | -0.27 | 0.00 | 221 | NO |
| CL 2 | ALL release+15m dir=with hold=120m | 155 | 2 | 1.12 | -0.73 | -0.18 | -1.64 / 1.24 | 0.20 / -0.37 / -0.69 | -0.13 | 0.08 | 0.55 | -0.32 | 0.00 | 244 | NO |
| CL 3 | THU release+15m dir=with hold=60m | 101 | 2 | 1.09 | -0.67 | -0.34 | -2.13 / 1.22 | 0.21 / 0.01 / -1.17 | -0.21 | 0.33 | 0.56 | -0.37 | 0.00 | 160 | NO |
| CL 4 | THU release+15m dir=with hold=120m | 101 | 2 | 1.07 | -0.71 | -0.06 | -1.32 / 1.27 | 0.21 / -0.12 / -0.64 | -0.07 | 0.07 | 0.60 | -0.26 | 0.00 | 160 | NO |
| CL 5 | ALL release+5m dir=against hold=flat | 152 | 2 | 1.01 | -0.14 | 0.43 | -0.11 / 1.53 | 0.17 / -0.16 / 0.02 | 0.06 | -0.05 | 0.84 | -0.15 | 0.50 | 234 | NO |
| CL 6 | ALL release+5m dir=against hold=120m | 152 | 2 | 0.93 | -0.32 | 0.42 | -0.13 / 1.24 | 0.17 / -0.11 / -0.17 | -0.00 | 0.46 | 0.92 | -0.17 | 0.00 | 234 | NO |
| CL 7 | TNC release+5m dir=against hold=flat | 138 | 2 | 0.93 | -0.14 | 0.37 | -0.15 / 1.31 | 0.17 / -0.13 / 0.04 | 0.07 | -0.12 | 0.78 | -0.14 | 0.50 | 213 | NO |
| CL 8 | TNC release+5m dir=against hold=120m | 138 | 2 | 0.86 | -0.31 | 0.36 | -0.21 / 1.25 | 0.17 / -0.06 / -0.16 | 0.01 | 0.47 | 0.88 | -0.16 | 0.00 | 213 | NO |
| CL 9 | THU release+15m dir=with hold=240m | 101 | 2 | 0.82 | -0.57 | 0.17 | -0.63 / 1.53 | 0.16 / 0.03 / -0.40 | -0.02 | 0.14 | 0.71 | -0.20 | 0.00 | 160 | NO |
| CL 10 | TNC release+15m dir=with hold=60m | 141 | 2 | 0.79 | -0.58 | -0.56 | -2.34 / 1.07 | 0.14 / -0.20 / -1.12 | -0.27 | 0.06 | 0.47 | -0.43 | 0.00 | 221 | NO |
| ZN 1 (diag) | ALL release+5m dir=with hold=flat | 153 | 1 | -0.14 | -0.48 | -0.52 | -1.22 / 0.39 | -0.05 / -0.08 / -0.42 | -0.30 | 0.05 | 0.66 | -0.31 | 0.00 | 235 | diag |
| ZN 2 (diag) | TNC release+5m dir=with hold=flat | 140 | 1 | -0.33 | -0.52 | -0.58 | -1.16 / 0.58 | -0.08 / -0.02 / -0.42 | -0.30 | 0.03 | 0.69 | -0.31 | 0.00 | 214 | diag |
| ZN 3 (diag) | THU release+5m dir=with hold=flat | 99 | 1 | -0.48 | -0.31 | -0.49 | -0.51 / 0.36 | -0.13 / -0.01 / -0.30 | -0.29 | 0.15 | 0.65 | -0.32 | 0.00 | 151 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 59 |
| diagnostic cells read | 4 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 4 / 5 / 5 |
| all-in uplift @20% > 0 (all scored) | 42 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 6 |
| standalone pair-window Sharpe above own random-entry null p95 | 15 |
| worst-decile corr <= +0.30 | 58 |
| plateau >= 0.75 | 13 |
| all-in uplift at 2x slippage >= +0.10 | 20 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CL TNC release+5m dir=against hold=flat | clean | 0.91 | 1.54 | -106956 | -90134 | 224312 | -148241 | 3.67 | 45.7 | 1.63 | -76382 | 296989 | -82984 |
| CL TNC release+5m dir=against hold=flat | H1 | -0.30 | -0.40 | -75317 | -64491 | 274123 | -103479 | -0.16 | 39.3 | 2.70 | -80785 | 149865 | -85345 |
| CL TNC release+5m dir=against hold=flat | H2 | -0.14 | -0.21 | -258530 | -199147 | 677721 | -369359 | -0.14 | 52.8 | 2.33 | -79509 | 235870 | -82040 |
| CL TNC release+5m dir=against hold=flat | all | 0.37 | 0.57 | -157005 | -126558 | 677721 | -369359 | 1.01 | 46.4 | 1.96 | -78451 | 296989 | -85345 |
| ES TNC release+5m dir=against hold=240m | clean | 0.37 | 0.62 | -109847 | -91464 | 456093 | -155132 | 0.73 | 44.8 | 1.50 | -87725 | 264895 | -95616 |
| ES TNC release+5m dir=against hold=240m | H1 | 3.51 | 12.03 | -57727 | -47723 | 77827 | -77827 | 11.08 | 28.6 | 3.47 | -71041 | 153003 | -72089 |
| ES TNC release+5m dir=against hold=240m | H2 | 0.84 | 1.15 | -171115 | -142671 | 418213 | -204743 | 0.72 | 27.8 | 2.43 | -88823 | 230493 | -97724 |
| ES TNC release+5m dir=against hold=240m | all | 0.99 | 1.66 | -127349 | -101704 | 475168 | -204743 | 3.15 | 38.1 | 2.01 | -86826 | 264895 | -97724 |
| GC THU release+30m dir=against hold=120m | clean | 0.75 | 1.26 | -112691 | -93340 | 846909 | -187337 | 0.80 | 45.7 | 1.60 | -79431 | 238516 | -90209 |
| GC THU release+30m dir=against hold=120m | H1 | 0.51 | 0.86 | -166914 | -159632 | 601786 | -176413 | 0.37 | 53.6 | 2.81 | -75414 | 164144 | -99797 |
| GC THU release+30m dir=against hold=120m | H2 | 2.30 | 4.45 | -189949 | -146492 | 200636 | -200636 | 6.61 | 30.6 | 2.82 | -88825 | 203925 | -101448 |
| GC THU release+30m dir=against hold=120m | all | 1.11 | 1.97 | -156307 | -127186 | 846909 | -200636 | 2.63 | 44.0 | 2.08 | -83781 | 238516 | -101448 |
| NQ TNC release+5m dir=against hold=60m | clean | 0.95 | 1.60 | -103137 | -93471 | 504307 | -108625 | 1.74 | 44.8 | 1.64 | -83964 | 241968 | -97531 |
| NQ TNC release+5m dir=against hold=60m | H1 | 0.37 | 0.62 | -91211 | -87450 | 373057 | -97097 | 0.25 | 50.0 | 2.79 | -73627 | 168330 | -82568 |
| NQ TNC release+5m dir=against hold=60m | H2 | 2.20 | 3.91 | -138917 | -124438 | 330348 | -152039 | 2.90 | 33.3 | 2.68 | -92608 | 231436 | -107555 |
| NQ TNC release+5m dir=against hold=60m | all | 1.18 | 2.00 | -118531 | -104544 | 504307 | -152989 | 3.82 | 42.9 | 2.07 | -85730 | 241968 | -107555 |
| RTY ALL release+5m dir=against hold=240m | clean | 0.43 | 0.70 | -112349 | -96911 | 339144 | -149547 | 1.16 | 49.5 | 1.49 | -87241 | 268313 | -93429 |
| RTY ALL release+5m dir=against hold=240m | H1 | 2.40 | 4.29 | -124912 | -107916 | 238772 | -145049 | 2.77 | 35.7 | 3.34 | -78279 | 139778 | -89223 |
| RTY ALL release+5m dir=against hold=240m | H2 | 1.13 | 1.71 | -220248 | -162237 | 492243 | -221240 | 1.04 | 33.3 | 2.64 | -74901 | 222809 | -79287 |
| RTY ALL release+5m dir=against hold=240m | all | 0.95 | 1.52 | -146249 | -116260 | 492243 | -221240 | 3.18 | 43.5 | 2.02 | -85920 | 268313 | -93429 |
| YM THU release+5m dir=against hold=120m | clean | 0.66 | 1.00 | -125190 | -102492 | 333698 | -172990 | 1.78 | 41.9 | 1.56 | -91215 | 263277 | -98283 |
| YM THU release+5m dir=against hold=120m | H1 | 1.36 | 2.29 | -165180 | -150960 | 504644 | -192217 | 1.05 | 35.7 | 3.62 | -68707 | 166413 | -72108 |
| YM THU release+5m dir=against hold=120m | H2 | 2.06 | 3.41 | -205836 | -148857 | 456176 | -253102 | 2.12 | 36.1 | 2.77 | -81802 | 235914 | -82212 |
| YM THU release+5m dir=against hold=120m | all | 1.16 | 1.86 | -159816 | -127185 | 504644 | -253102 | 4.14 | 39.9 | 2.12 | -88028 | 263277 | -98283 |
| ZN ALL release+5m dir=with hold=flat (diag) | clean | -0.19 | -0.27 | -133765 | -112520 | 704231 | -163787 | -0.25 | 48.6 | 1.41 | -80984 | 262810 | -94594 |
| ZN ALL release+5m dir=with hold=flat (diag) | H1 | 0.12 | 0.17 | -91481 | -78983 | 303087 | -95286 | 0.07 | 42.9 | 2.75 | -87209 | 151996 | -95822 |
| ZN ALL release+5m dir=with hold=flat (diag) | H2 | -2.14 | -2.38 | -127914 | -106526 | 552364 | -148564 | -0.98 | 58.3 | 1.88 | -93046 | 226842 | -96174 |
| ZN ALL release+5m dir=with hold=flat (diag) | all | -0.52 | -0.69 | -128674 | -108635 | 1211928 | -163787 | -0.57 | 49.4 | 1.72 | -87288 | 262810 | -96174 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES TNC release+5m dir=against hold=240m | -13.3 | -2.6 | 13.2 | 37.9 | 0.1 / 11.7 | 40.5 / 42.7 | NO |
| NQ TNC release+5m dir=against hold=60m | -8.5 | -20.7 | 13.4 | 33.2 | -2.7 / 18.5 | 20.4 / 25.5 | NO |
| RTY ALL release+5m dir=against hold=240m | -12.5 | 4.8 | 14.7 | 23.2 | 4.1 / 12.4 | 7.7 / 28.7 | NO |
| YM THU release+5m dir=against hold=120m | -6.7 | -2.2 | 9.5 | 23.8 | -3.0 / 1.7 | 41.8 / 47.2 | NO |
| GC THU release+30m dir=against hold=120m | -5.1 | -7.2 | 20.4 | 39.2 | 10.0 / 27.6 | -11.2 / 13.2 | NO |
| CL TNC release+5m dir=against hold=flat | -22.4 | 10.9 | 21.9 | 21.0 | 10.2 / 25.4 | 16.5 / 23.9 | NO |
| ZN ALL release+5m dir=with hold=flat (diag) | -37.8 | -5.1 | 6.1 | 27.3 | 2.0 / 19.0 | -3.6 / 11.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 TNC release+30m dir=against hold=240m | positive pre-2023 | 630 | 40.6 | 11.3 | 25.4 | 29.4 | 0.31 / 0.09 / 0.19 | 201.7 / 172.3 |
| ES 2 ALL release+30m dir=against hold=240m | positive pre-2023 | 628 | 39.3 | 9.9 | 24.1 | 29.4 | 0.30 / 0.08 / 0.18 | 198.6 / 169.3 |
| ES 3 THU release+15m dir=against hold=60m | negative pre-2023 | 511 | -6.2 | -35.6 | -21.5 | 29.4 | -0.09 / -0.52 / -0.31 | 86.1 / 56.8 |
| ES 4 TNC release+30m dir=against hold=flat | positive pre-2023 | 640 | 92.1 | 62.7 | 76.9 | 29.4 | 0.52 / 0.35 / 0.43 | 200.1 / 170.7 |
| ES 5 TNC release+15m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 635 | 11.5 | -17.9 | -3.8 | 29.4 | 0.19 / -0.30 / -0.06 | 79.3 / 49.9 |
| ES 6 TNC release+5m dir=against hold=240m | gross-positive, cost-negative pre-2023 | 625 | 12.1 | -17.3 | -3.2 | 29.4 | 0.09 / -0.13 / -0.02 | 107.9 / 78.6 |
| ES 7 ALL release+5m dir=against hold=240m | gross-positive, cost-negative pre-2023 | 623 | 11.1 | -18.2 | -4.2 | 29.4 | 0.08 / -0.14 / -0.03 | 104.8 / 75.5 |
| ES 8 THU release+15m dir=with hold=240m | gross-positive, cost-negative pre-2023 | 511 | 16.3 | -13.1 | 1.0 | 29.4 | 0.11 / -0.09 / 0.01 | 101.9 / 72.5 |
| ES 9 ALL release+30m dir=against hold=flat | positive pre-2023 | 719 | 101.3 | 72.0 | 86.1 | 29.4 | 0.58 / 0.41 / 0.49 | 106.1 / 76.7 |
| ES 10 TNC release+5m dir=against hold=flat | positive pre-2023 | 628 | 72.2 | 42.9 | 56.9 | 29.4 | 0.38 / 0.23 / 0.30 | 47.0 / 17.7 |
| NQ 1 TNC release+15m dir=against hold=60m | positive pre-2023 | 654 | 34.7 | 20.3 | 28.8 | 14.4 | 0.35 / 0.21 / 0.29 | 190.9 / 176.6 |
| NQ 2 TNC release+5m dir=against hold=60m | positive pre-2023 | 650 | 23.1 | 8.7 | 17.2 | 14.4 | 0.29 / 0.11 / 0.21 | 137.6 / 123.2 |
| NQ 3 THU release+15m dir=against hold=60m | negative pre-2023 | 528 | -14.7 | -29.0 | -20.5 | 14.4 | -0.14 / -0.27 / -0.19 | 153.9 / 139.6 |
| NQ 4 TNC release+15m dir=against hold=flat | positive pre-2023 | 654 | 64.2 | 49.8 | 58.3 | 14.4 | 0.22 / 0.17 / 0.20 | 242.0 / 227.6 |
| NQ 5 ALL release+15m dir=against hold=60m | positive pre-2023 | 734 | 61.8 | 47.4 | 55.9 | 14.4 | 0.54 / 0.41 / 0.49 | 64.3 / 50.0 |
| NQ 6 TNC release+5m dir=against hold=240m | gross-positive, cost-negative pre-2023 | 650 | 8.9 | -5.4 | 3.0 | 14.4 | 0.04 / -0.02 / 0.01 | 142.7 / 128.3 |
| NQ 7 ALL release+15m dir=against hold=flat | positive pre-2023 | 734 | 104.1 | 89.7 | 98.2 | 14.4 | 0.38 / 0.32 / 0.35 | 150.7 / 136.3 |
| NQ 8 ALL release+5m dir=against hold=240m | gross-positive, cost-negative pre-2023 | 647 | 5.9 | -8.5 | -0.0 | 14.4 | 0.03 / -0.04 / -0.00 | 127.1 / 112.7 |
| NQ 9 TNC release+5m dir=against hold=flat | positive pre-2023 | 653 | 45.9 | 31.6 | 40.0 | 14.4 | 0.15 / 0.10 / 0.13 | 51.5 / 37.2 |
| NQ 10 (diag) THU release+5m dir=against hold=60m | negative pre-2023 | 529 | -11.2 | -25.6 | -17.1 | 14.4 | -0.12 / -0.28 / -0.19 | 103.7 / 89.3 |
| RTY 1 THU release+30m dir=with hold=flat | negative pre-2023 | 304 | -47.7 | -62.1 | -59.9 | 14.4 | -0.30 / -0.39 / -0.37 | 104.4 / 90.1 |
| RTY 2 TNC release+30m dir=against hold=60m | negative pre-2023 | 377 | -26.5 | -40.9 | -38.7 | 14.4 | -0.36 / -0.56 / -0.53 | 47.7 / 33.3 |
| RTY 3 TNC release+15m dir=against hold=120m | positive pre-2023 | 371 | 32.9 | 18.5 | 20.7 | 14.4 | 0.34 / 0.19 / 0.22 | 62.4 / 48.1 |
| RTY 4 TNC release+15m dir=against hold=240m | positive pre-2023 | 371 | 37.3 | 23.0 | 25.2 | 14.4 | 0.32 / 0.20 / 0.21 | 65.7 / 51.3 |
| RTY 5 ALL release+5m dir=against hold=240m | negative pre-2023 | 362 | -10.2 | -24.6 | -22.4 | 14.4 | -0.08 / -0.20 / -0.18 | 63.6 / 49.3 |
| RTY 6 ALL release+15m dir=against hold=240m | positive pre-2023 | 369 | 33.0 | 18.7 | 20.9 | 14.4 | 0.28 / 0.16 / 0.18 | 64.5 / 50.1 |
| RTY 7 TNC release+5m dir=against hold=240m | negative pre-2023 | 364 | -6.3 | -20.6 | -18.4 | 14.4 | -0.05 / -0.17 / -0.15 | 61.6 / 47.2 |
| RTY 8 TNC release+5m dir=against hold=120m | gross-positive, cost-negative pre-2023 | 364 | 9.2 | -5.1 | -2.9 | 14.4 | 0.09 / -0.05 / -0.03 | 50.1 / 35.7 |
| RTY 9 THU release+5m dir=against hold=120m | negative pre-2023 | 292 | -25.5 | -39.9 | -37.6 | 14.4 | -0.23 / -0.36 / -0.34 | 49.5 / 35.1 |
| RTY 10 THU release+5m dir=with hold=flat | negative pre-2023 | 292 | -37.9 | -52.2 | -50.0 | 14.4 | -0.22 / -0.31 / -0.30 | 48.9 / 34.5 |
| YM 1 ALL release+15m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 733 | 9.9 | -4.5 | 1.2 | 14.4 | 0.19 / -0.09 / 0.02 | 105.2 / 90.8 |
| YM 2 THU release+15m dir=with hold=flat | negative pre-2023 | 531 | -34.3 | -48.7 | -42.9 | 14.4 | -0.23 / -0.32 / -0.29 | 219.8 / 205.4 |
| YM 3 ALL release+30m dir=with hold=60m | positive pre-2023 | 735 | 20.0 | 5.6 | 11.3 | 14.4 | 0.31 / 0.09 / 0.17 | 62.5 / 48.2 |
| YM 4 THU release+30m dir=with hold=flat | negative pre-2023 | 530 | -66.1 | -80.4 | -74.7 | 14.4 | -0.44 / -0.54 / -0.50 | 186.4 / 172.1 |
| YM 5 TNC release+5m dir=against hold=240m | positive pre-2023 | 643 | 35.8 | 21.5 | 27.2 | 14.4 | 0.33 / 0.20 / 0.25 | 122.4 / 108.0 |
| YM 6 ALL release+5m dir=against hold=240m | positive pre-2023 | 640 | 35.3 | 20.9 | 26.6 | 14.4 | 0.33 / 0.19 / 0.25 | 116.4 / 102.0 |
| YM 7 TNC release+5m dir=against hold=120m | gross-positive, cost-negative pre-2023 | 643 | 6.5 | -7.9 | -2.2 | 14.4 | 0.07 / -0.09 / -0.02 | 79.9 / 65.5 |
| YM 8 ALL release+15m dir=with hold=flat | negative pre-2023 | 733 | -40.2 | -54.5 | -48.9 | 14.4 | -0.32 / -0.44 / -0.39 | 127.7 / 113.3 |
| YM 9 THU release+5m dir=against hold=120m | negative pre-2023 | 518 | -16.0 | -30.3 | -24.6 | 14.4 | -0.17 / -0.32 / -0.26 | 87.8 / 73.5 |
| YM 10 ALL release+5m dir=with hold=60m | negative pre-2023 | 723 | -23.3 | -37.7 | -32.0 | 14.4 | -0.43 / -0.69 / -0.59 | 67.1 / 52.7 |
| GC 1 ALL release+15m dir=against hold=60m | negative pre-2023 | 725 | -3.6 | -28.0 | -18.2 | 24.4 | -0.05 / -0.42 / -0.27 | 162.6 / 138.3 |
| GC 2 TNC release+15m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 651 | 0.3 | -24.0 | -14.3 | 24.4 | 0.00 / -0.36 / -0.21 | 159.7 / 135.4 |
| GC 3 ALL release+15m dir=against hold=120m | negative pre-2023 | 725 | -34.6 | -58.9 | -49.2 | 24.4 | -0.39 / -0.66 / -0.55 | 218.9 / 194.5 |
| GC 4 TNC release+15m dir=against hold=120m | negative pre-2023 | 651 | -19.9 | -44.3 | -34.6 | 24.4 | -0.21 / -0.47 / -0.37 | 210.2 / 185.8 |
| GC 5 TNC release+5m dir=against hold=120m | negative pre-2023 | 652 | -24.5 | -48.8 | -39.1 | 24.4 | -0.24 / -0.48 / -0.38 | 174.6 / 150.2 |
| GC 6 THU release+15m dir=against hold=60m | negative pre-2023 | 526 | -11.9 | -36.2 | -26.5 | 24.4 | -0.17 / -0.51 / -0.37 | 110.1 / 85.7 |
| GC 7 THU release+30m dir=against hold=120m | negative pre-2023 | 529 | -34.5 | -58.9 | -49.1 | 24.4 | -0.36 / -0.61 / -0.51 | 165.0 / 140.6 |
| GC 8 TNC release+30m dir=against hold=120m | negative pre-2023 | 655 | -29.8 | -54.1 | -44.4 | 24.4 | -0.31 / -0.57 / -0.47 | 132.0 / 107.6 |
| GC 9 TNC release+5m dir=against hold=60m | negative pre-2023 | 652 | -16.1 | -40.4 | -30.7 | 24.4 | -0.23 / -0.58 / -0.44 | 81.9 / 57.6 |
| GC 10 THU release+15m dir=against hold=120m | negative pre-2023 | 526 | -29.0 | -53.3 | -43.6 | 24.4 | -0.29 / -0.54 / -0.44 | 121.4 / 97.0 |
| CL 1 TNC release+15m dir=with hold=120m | negative pre-2023 | 648 | -40.1 | -64.4 | -61.9 | 24.4 | -0.42 / -0.68 / -0.65 | 122.0 / 97.6 |
| CL 2 ALL release+15m dir=with hold=120m | negative pre-2023 | 728 | -38.5 | -62.9 | -60.3 | 24.4 | -0.45 / -0.73 / -0.70 | 108.6 / 84.3 |
| CL 3 THU release+15m dir=with hold=60m | negative pre-2023 | 522 | -28.5 | -52.8 | -50.3 | 24.4 | -0.36 / -0.67 / -0.64 | 97.5 / 73.2 |
| CL 4 THU release+15m dir=with hold=120m | negative pre-2023 | 522 | -53.8 | -78.2 | -75.6 | 24.4 | -0.49 / -0.71 / -0.69 | 122.5 / 98.1 |
| CL 5 ALL release+5m dir=against hold=flat | gross-positive, cost-negative pre-2023 | 708 | 4.7 | -19.6 | -17.1 | 24.4 | 0.03 / -0.14 / -0.12 | 136.6 / 112.2 |
| CL 6 ALL release+5m dir=against hold=120m | negative pre-2023 | 708 | -3.1 | -27.5 | -25.0 | 24.4 | -0.04 / -0.32 / -0.30 | 91.6 / 67.2 |
| CL 7 TNC release+5m dir=against hold=flat | gross-positive, cost-negative pre-2023 | 630 | 3.1 | -21.2 | -18.7 | 24.4 | 0.02 / -0.14 / -0.12 | 134.9 / 110.6 |
| CL 8 TNC release+5m dir=against hold=120m | negative pre-2023 | 630 | -4.2 | -28.6 | -26.1 | 24.4 | -0.05 / -0.31 / -0.28 | 90.1 / 65.8 |
| CL 9 THU release+15m dir=with hold=240m | negative pre-2023 | 522 | -56.0 | -80.4 | -77.8 | 24.4 | -0.40 / -0.57 / -0.55 | 127.0 / 102.7 |
| CL 10 TNC release+15m dir=with hold=60m | negative pre-2023 | 648 | -14.1 | -38.5 | -35.9 | 24.4 | -0.21 / -0.58 / -0.54 | 75.7 / 51.4 |
| ZN 1 (diag) ALL release+5m dir=with hold=flat | gross-positive, cost-negative pre-2023 | 690 | 15.7 | -19.9 | -24.9 | 35.6 | 0.38 / -0.48 / -0.60 | 28.6 / -7.0 |
| ZN 2 (diag) TNC release+5m dir=with hold=flat | gross-positive, cost-negative pre-2023 | 614 | 13.0 | -22.6 | -27.6 | 35.6 | 0.30 / -0.52 / -0.63 | 22.9 / -12.7 |
| ZN 3 (diag) THU release+5m dir=with hold=flat | gross-positive, cost-negative pre-2023 | 488 | 21.0 | -14.6 | -19.7 | 35.6 | 0.44 / -0.31 / -0.41 | 16.6 / -19.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): CL: 18 cells pass the clean rule against a replicate mean of 5.6 (p(count) = 0.00, p(top) = 0.05); ES: 10 cells pass the clean rule against a replicate mean of 6.9 (p(count) = 0.16, p(top) = 0.96); GC: 15 cells pass the clean rule against a replicate mean of 8.0 (p(count) = 0.00, p(top) = 0.19); NQ: 9 cells pass the clean rule against a replicate mean of 11.7 (p(count) = 0.89, p(top) = 0.87); RTY: 14 cells pass the clean rule against a replicate mean of 8.2 (p(count) = 0.02, p(top) = 0.97); YM: 19 cells pass the clean rule against a replicate mean of 8.7 (p(count) = 0.00, p(top) = 0.29); ZN: 0 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 1.00).
- Of 59 selected cells, 4 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.26 (YM THU release+5m dir=against hold=120m); bootstrap lower bound > 0 for 6 cells; plateau >= 0.75 for 13; 2x-slippage all-in uplift >= +0.10 for 20; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell YM ALL release+30m dir=with hold=60m: uplift +0.10/+0.52/+0.33, boot lo +0.00, plateau 0.75, 2x-slip +0.18, wd corr +0.03, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell YM TNC release+5m dir=against hold=240m: uplift +0.11/+0.45/+0.39, boot lo +0.02, plateau 0.75, 2x-slip +0.21, wd corr -0.35, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell YM TNC release+5m dir=against hold=120m: uplift +0.11/+0.50/+0.37, boot lo +0.01, plateau 0.25, 2x-slip +0.21, wd corr +0.14, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- Gate-3 cell YM THU release+5m dir=against hold=120m: uplift +0.10/+0.79/+0.47, boot lo +0.04, plateau 0.00, 2x-slip +0.24, wd corr +0.36, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 30, 'positive pre-2023': 17, 'gross-positive, cost-negative pre-2023': 12}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_16.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw16/ (`SW16_CO_all_selected_scored.csv`).

DONE SW16
