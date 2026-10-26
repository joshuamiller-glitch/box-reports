# REPORT SW4 - RTH-open entries gated by the overnight range percentile (D08 H4)

**Verdict: FOUND-PENDING-REPLICATION (one RTY cell, section 7; the automatic 'FOUND-CANDIDATE' tag was downgraded after verification). FOUND 0, FOUND-PENDING 1, LEAD 5, INSURANCE 1.** 69 selected cells (+6 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.43; best pair-window standalone Sharpe +1.65.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: one entry per day at RTH open + d min (0/15/30), direction = sign of a reference move (overnight return since 18:00 / first-d-minutes return / prior-day return) with or against, taken only if the overnight (18:00 to RTH open) range/open percentile (vs the prior 250 days) is hi (>=0.67), lo (<=0.33) or any; hold to the 16:55 flatten or 120 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 96 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        24 |               1.378 |                2 |         10 |            0 |
| CL    |      96 |         96 |         7 |               1.114 |                2 |          7 |            3 |
| ES    |      96 |         96 |        16 |               1.514 |                2 |         10 |            0 |
| GC    |      96 |         96 |        16 |               2.034 |                2 |         10 |            0 |
| NQ    |      96 |         96 |        24 |               1.986 |                2 |         10 |            0 |
| RTY   |      96 |         96 |        20 |               2.164 |                2 |         10 |            0 |
| YM    |      96 |         96 |        14 |               1.533 |                2 |         10 |            0 |
| ZN    |      96 |         96 |         2 |               0.42  |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   16 |            14.31 |              23 |       0.38 |                       1.027 |            0.867 |           1.074 |     0.08 |       1.514 |                1.848 |
| NQ    |     100 |                   24 |            20.5  |              30 |       0.24 |                       1.254 |            1.06  |           1.277 |     0.11 |       1.986 |                2.188 |
| RTY   |     100 |                   20 |            16.33 |              26 |       0.18 |                       1.06  |            0.942 |           1.187 |     0.25 |       2.164 |                2     |
| YM    |     100 |                   14 |            16.6  |              27 |       0.82 |                       0.781 |            0.952 |           1.138 |     0.88 |       1.533 |                2.094 |
| GC    |     100 |                   16 |            16.71 |              29 |       0.59 |                       1.647 |            0.94  |           1.194 |     0    |       2.034 |                2.005 |
| CL    |     100 |                    7 |            13.19 |              22 |       0.99 |                       0.677 |            0.846 |           1.099 |     0.86 |       1.015 |                1.892 |
| ZN    |     100 |                    2 |             1.33 |               4 |       0.38 |                       0.29  |            0.523 |           0.99  |     0.59 |       0.42  |                1.057 |
| BTC   |     100 |                   24 |            16.18 |              27 |       0.05 |                       1.013 |            0.974 |           1.271 |     0.39 |       1.378 |                2.106 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | 175 | 2 | 1.51 | -0.52 | 1.31 | 1.01 / 1.00 | 0.26 / 0.14 / 0.29 | 0.22 | 0.38 | 1.00 | 0.07 | 0.25 | 267 | LEAD |
| ES 2 | RTHopen+15m ref=on onrange any0.0 dir=against hold=120m | 516 | 2 | 1.38 | -0.91 | 0.56 | -0.39 / 1.01 | 0.25 / -0.11 / -0.12 | 0.05 | 0.25 | 0.98 | -0.08 | 0.50 | 825 | NO |
| ES 3 | RTHopen+0m ref=on onrange hi0.67 dir=against hold=120m | 174 | 2 | 1.33 | -0.31 | 0.93 | 0.23 / 1.05 | 0.27 / -0.31 / 0.25 | 0.16 | 0.09 | 0.98 | 0.03 | 0.25 | 266 | NO |
| ES 4 | RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | 514 | 2 | 1.18 | -0.44 | 0.58 | -0.15 / 1.18 | 0.27 / -0.29 / 0.00 | 0.07 | -0.07 | 0.97 | -0.05 | 0.50 | 824 | NO |
| ES 5 | RTHopen+30m ref=ft onrange lo0.33 dir=with hold=120m | 174 | 2 | 1.07 | -0.53 | 1.10 | 1.10 / 0.87 | 0.17 / 0.31 / 0.07 | 0.10 | -0.25 | 1.00 | -0.05 | 0.75 | 276 | NO |
| ES 6 | RTHopen+0m ref=on onrange hi0.67 dir=against hold=flat | 174 | 2 | 1.00 | -0.16 | 0.67 | -0.31 / 1.16 | 0.15 / -0.04 / -0.05 | 0.07 | -0.64 | 0.93 | -0.03 | 0.50 | 266 | NO |
| ES 7 | RTHopen+30m ref=on onrange any0.0 dir=against hold=120m | 514 | 2 | 0.76 | -0.49 | 0.39 | -0.04 / 1.00 | 0.13 / -0.32 / 0.03 | -0.03 | 0.23 | 0.95 | -0.16 | 1.00 | 824 | NO |
| ES 8 | RTHopen+15m ref=ft onrange any0.0 dir=against hold=120m | 509 | 2 | 0.70 | -1.02 | 0.13 | -0.47 / 1.44 | 0.12 / -0.30 / -0.11 | -0.06 | -0.14 | 0.85 | -0.19 | 0.00 | 815 | NO |
| ES 9 | RTHopen+30m ref=on onrange lo0.33 dir=with hold=120m | 175 | 2 | 0.68 | -0.51 | 0.72 | 0.87 / 1.32 | 0.07 / 0.37 / -0.01 | 0.03 | -0.14 | 0.99 | -0.15 | 0.25 | 278 | NO |
| ES 10 | RTHopen+30m ref=on onrange hi0.67 dir=against hold=120m | 175 | 2 | 0.66 | -0.15 | 0.97 | 1.43 / 1.10 | 0.07 / 0.10 / 0.46 | 0.12 | 0.20 | 1.00 | -0.02 | 0.75 | 267 | NO |
| NQ 1 | RTHopen+15m ref=ft onrange any0.0 dir=with hold=flat | 516 | 2 | 1.99 | 0.41 | 1.06 | -0.31 / 1.53 | 0.33 / -0.04 / -0.35 | 0.12 | -0.08 | 0.97 | -0.06 | 0.00 | 824 | NO |
| NQ 2 | RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | 516 | 2 | 1.47 | -0.43 | 0.63 | -0.27 / 1.05 | 0.35 / -0.63 / 0.09 | 0.15 | 0.27 | 0.95 | -0.07 | 1.00 | 826 | NO |
| NQ 3 | RTHopen+15m ref=ft onrange hi0.67 dir=with hold=flat | 170 | 2 | 1.30 | 0.31 | 0.04 | -1.71 / 1.52 | 0.19 / -0.43 / -0.62 | -0.09 | -0.19 | 0.53 | -0.28 | 0.00 | 288 | NO |
| NQ 4 | RTHopen+0m ref=on onrange hi0.67 dir=against hold=120m | 170 | 2 | 1.27 | 0.18 | 0.42 | -0.56 / 1.15 | 0.27 / -0.35 / -0.02 | 0.12 | 0.37 | 0.86 | -0.08 | 1.00 | 289 | NO |
| NQ 5 | RTHopen+30m ref=on onrange any0.0 dir=with hold=flat | 514 | 2 | 1.22 | 0.18 | 0.94 | 0.44 / 1.42 | 0.19 / -0.05 / 0.12 | 0.12 | -0.17 | 0.96 | -0.06 | 0.00 | 824 | NO |
| NQ 6 | RTHopen+30m ref=ft onrange any0.0 dir=with hold=120m | 515 | 2 | 1.18 | 0.21 | 0.28 | -0.53 / 1.55 | 0.17 / -0.16 / -0.45 | -0.03 | -0.02 | 0.72 | -0.26 | 0.00 | 825 | NO |
| NQ 7 | RTHopen+0m ref=on onrange lo0.33 dir=against hold=120m | 171 | 2 | 1.09 | -0.76 | 0.42 | -0.48 / 1.28 | 0.29 / 0.37 / -0.47 | 0.12 | -0.04 | 0.82 | -0.11 | 0.25 | 255 | NO |
| NQ 8 | RTHopen+30m ref=ft onrange any0.0 dir=with hold=flat | 515 | 2 | 1.01 | 0.31 | 0.46 | -0.27 / 1.42 | 0.16 / -0.01 / -0.24 | 0.03 | -0.32 | 0.81 | -0.17 | 0.00 | 825 | NO |
| NQ 9 | RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | 170 | 2 | 1.01 | -0.08 | 0.70 | 0.32 / 0.97 | 0.14 / 0.09 / 0.06 | 0.11 | 0.61 | 0.95 | -0.08 | 0.75 | 289 | NO |
| NQ 10 | RTHopen+0m ref=on onrange hi0.67 dir=against hold=flat | 170 | 2 | 1.00 | 0.16 | 0.25 | -1.25 / 1.55 | 0.16 / -0.11 / -0.25 | 0.03 | -0.38 | 0.74 | -0.11 | 0.50 | 289 | NO |
| RTY 1 | RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | 199 | 2 | 2.16 | -0.63 | 1.65 | 0.99 / 1.39 | 0.38 / 0.30 / 0.40 | 0.34 | -0.18 | 1.00 | 0.17 | 0.75 | 290 | FOUND-CAND |
| RTY 2 | RTHopen+15m ref=ft onrange any0.0 dir=against hold=120m | 512 | 2 | 1.38 | -1.03 | 0.80 | 0.17 / 1.24 | 0.23 / -0.27 / 0.18 | 0.11 | -0.39 | 0.99 | -0.06 | 0.50 | 820 | NO |
| RTY 3 | RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | 201 | 2 | 1.16 | -0.19 | 1.06 | 0.90 / 1.07 | 0.14 / -0.11 / 0.31 | 0.12 | 0.33 | 1.00 | -0.04 | 1.00 | 293 | NO |
| RTY 4 | RTHopen+15m ref=ft onrange hi0.67 dir=against hold=flat | 199 | 2 | 1.10 | -0.42 | 0.83 | 0.39 / 1.62 | 0.20 / 0.22 / 0.14 | 0.17 | 0.29 | 0.95 | 0.01 | 0.50 | 290 | LEAD(gate3-7 fail: plateau ) |
| RTY 5 | RTHopen+15m ref=on onrange lo0.33 dir=with hold=flat | 158 | 2 | 0.95 | 0.44 | -0.33 | -1.41 / 1.61 | 0.12 / -1.11 / -0.27 | -0.17 | 0.61 | 0.31 | -0.40 | 0.00 | 272 | NO |
| RTY 6 | RTHopen+0m ref=on onrange lo0.33 dir=with hold=flat | 156 | 2 | 0.88 | 0.71 | -0.09 | -1.04 / 1.33 | 0.11 / -0.81 / -0.01 | -0.07 | 0.47 | 0.48 | -0.26 | 0.00 | 266 | NO |
| RTY 7 | RTHopen+15m ref=on onrange any0.0 dir=against hold=120m | 515 | 2 | 0.81 | -0.76 | 0.64 | 0.37 / 1.19 | 0.10 / -0.06 / 0.09 | 0.03 | -0.21 | 0.97 | -0.13 | 0.50 | 824 | NO |
| RTY 8 | RTHopen+30m ref=pd onrange hi0.67 dir=with hold=120m | 201 | 2 | 0.79 | -0.12 | 0.22 | -0.47 / 1.15 | 0.16 / -0.43 / -0.22 | -0.02 | 0.07 | 0.69 | -0.22 | 0.50 | 292 | NO |
| RTY 9 | RTHopen+30m ref=on onrange hi0.67 dir=against hold=120m | 201 | 2 | 0.72 | 0.00 | 0.98 | 1.31 / 1.05 | 0.12 / 0.03 / 0.54 | 0.17 | -0.52 | 0.98 | -0.01 | 0.75 | 293 | NO |
| RTY 10 | RTHopen+30m ref=ft onrange hi0.67 dir=with hold=flat | 199 | 2 | 0.64 | 0.24 | 0.28 | -0.54 / 1.51 | 0.08 / 0.16 / -0.29 | -0.01 | 0.41 | 0.71 | -0.14 | 1.00 | 291 | NO |
| YM 1 | RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | 185 | 2 | 1.53 | -0.25 | 0.90 | -0.02 / 1.41 | 0.28 / -0.20 / -0.01 | 0.13 | 0.11 | 0.99 | -0.03 | 0.25 | 291 | NO |
| YM 2 | RTHopen+30m ref=ft onrange lo0.33 dir=with hold=flat | 171 | 2 | 1.01 | -0.53 | 0.58 | 0.14 / 1.43 | 0.15 / 0.28 / -0.14 | 0.08 | 0.49 | 0.92 | -0.11 | 0.50 | 266 | NO |
| YM 3 | RTHopen+0m ref=pd onrange hi0.67 dir=with hold=120m | 182 | 2 | 0.92 | 0.12 | 0.03 | -1.32 / 1.30 | 0.18 / -0.48 / -0.23 | -0.02 | -0.39 | 0.69 | -0.19 | 0.00 | 288 | NO |
| YM 4 | RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | 184 | 2 | 0.92 | -0.06 | 1.25 | 1.66 / 1.49 | 0.20 / 0.10 / 0.67 | 0.28 | -0.60 | 1.00 | 0.07 | 0.50 | 289 | NO |
| YM 5 | RTHopen+15m ref=pd onrange lo0.33 dir=against hold=120m | 172 | 2 | 0.69 | 0.02 | 0.21 | -0.16 / 1.51 | 0.09 / -0.18 / -0.24 | -0.04 | 0.34 | 0.81 | -0.22 | 0.00 | 267 | NO |
| YM 6 | RTHopen+30m ref=on onrange hi0.67 dir=against hold=120m | 185 | 2 | 0.63 | 0.08 | 0.41 | 0.06 / 1.02 | 0.12 / -0.14 / 0.04 | 0.05 | -0.01 | 0.89 | -0.10 | 0.75 | 291 | NO |
| YM 7 | RTHopen+30m ref=on onrange any0.0 dir=against hold=120m | 515 | 2 | 0.62 | -0.22 | 0.22 | -0.27 / 0.82 | 0.12 / -0.40 / -0.01 | -0.01 | 0.06 | 0.83 | -0.17 | 0.00 | 824 | NO |
| YM 8 | RTHopen+30m ref=ft onrange hi0.67 dir=against hold=120m | 185 | 2 | 0.58 | -0.21 | 0.60 | 0.65 / 1.23 | 0.17 / -0.53 / 0.42 | 0.13 | -0.37 | 0.92 | -0.06 | 0.75 | 291 | NO |
| YM 9 | RTHopen+15m ref=ft onrange lo0.33 dir=with hold=flat | 172 | 2 | 0.48 | -0.22 | 0.42 | 0.21 / 1.06 | 0.09 / 0.09 / -0.15 | 0.02 | 0.36 | 0.84 | -0.21 | 1.00 | 266 | NO |
| YM 10 | RTHopen+15m ref=on onrange hi0.67 dir=against hold=flat | 185 | 2 | 0.41 | -0.15 | 0.05 | -0.55 / 1.39 | 0.08 / -0.15 / -0.17 | -0.01 | -0.50 | 0.49 | -0.18 | 0.00 | 291 | NO |
| GC 1 | RTHopen+15m ref=on onrange any0.0 dir=with hold=flat | 513 | 2 | 2.03 | -0.33 | 1.26 | 0.96 / 1.66 | 0.33 / 0.08 / 0.28 | 0.26 | -0.14 | 0.99 | -0.00 | 0.00 | 822 | LEAD |
| GC 2 | RTHopen+30m ref=on onrange any0.0 dir=with hold=flat | 513 | 2 | 2.03 | -0.32 | 0.63 | -0.10 / 1.53 | 0.32 / -0.47 / -0.19 | 0.05 | 0.53 | 0.91 | -0.24 | 0.00 | 822 | NO |
| GC 3 | RTHopen+30m ref=ft onrange hi0.67 dir=with hold=flat | 221 | 2 | 1.87 | -0.51 | 0.10 | -0.99 / 1.55 | 0.26 / -0.92 / -0.55 | -0.12 | 0.16 | 0.65 | -0.44 | 0.00 | 348 | NO |
| GC 4 | RTHopen+0m ref=on onrange any0.0 dir=with hold=flat | 514 | 2 | 1.83 | -0.20 | 1.54 | 1.66 / 1.17 | 0.29 / -0.19 / 1.19 | 0.39 | 0.05 | 1.00 | 0.13 | 0.00 | 820 | NO |
| GC 5 | RTHopen+30m ref=on onrange hi0.67 dir=with hold=flat | 224 | 2 | 1.60 | -0.27 | 0.76 | 0.24 / 1.50 | 0.23 / 0.51 / -0.12 | 0.14 | 0.29 | 0.91 | -0.11 | 1.00 | 352 | NO |
| GC 6 | RTHopen+30m ref=ft onrange any0.0 dir=with hold=flat | 510 | 2 | 1.55 | -0.86 | -0.22 | -1.30 / 1.73 | 0.19 / -1.16 / -0.89 | -0.29 | 0.36 | 0.44 | -0.62 | 0.00 | 814 | NO |
| GC 7 | RTHopen+0m ref=on onrange hi0.67 dir=with hold=flat | 224 | 2 | 1.52 | -0.23 | 1.30 | 1.37 / 1.12 | 0.22 / 0.96 / 0.25 | 0.31 | 0.30 | 0.99 | 0.06 | 1.00 | 350 | LEAD |
| GC 8 | RTHopen+0m ref=on onrange hi0.67 dir=with hold=120m | 224 | 2 | 1.47 | -0.47 | 0.98 | 0.79 / 1.40 | 0.22 / 0.25 / 0.21 | 0.19 | -0.11 | 0.96 | -0.04 | 0.75 | 350 | LEAD |
| GC 9 | RTHopen+15m ref=on onrange hi0.67 dir=with hold=flat | 223 | 2 | 1.42 | -0.16 | 0.90 | 0.58 / 1.44 | 0.22 / 1.15 / -0.34 | 0.17 | 0.18 | 0.96 | -0.06 | 1.00 | 351 | NO |
| GC 10 | RTHopen+15m ref=on onrange hi0.67 dir=with hold=120m | 223 | 2 | 1.15 | -0.23 | 0.08 | -0.39 / 1.26 | 0.17 / -1.40 / -0.07 | -0.15 | 0.00 | 0.61 | -0.63 | 0.00 | 351 | NO |
| CL 1 | RTHopen+30m ref=pd onrange any0.0 dir=against hold=120m | 517 | 2 | 1.02 | -0.23 | 0.41 | -0.45 / 0.81 | 0.20 / -0.36 / -0.06 | -0.02 | 0.27 | 0.97 | -0.15 | 0.00 | 827 | NO |
| CL 2 | RTHopen+15m ref=pd onrange any0.0 dir=against hold=120m | 517 | 2 | 0.82 | -0.38 | -0.01 | -0.92 / 1.12 | 0.15 / -0.50 / -0.25 | -0.11 | 0.12 | 0.90 | -0.26 | 0.00 | 826 | NO |
| CL 3 | RTHopen+30m ref=on onrange lo0.33 dir=against hold=flat | 187 | 2 | 0.79 | -1.11 | 0.72 | 0.84 / 1.54 | 0.10 / 0.04 / 0.14 | 0.06 | 0.12 | 0.95 | -0.07 | 0.50 | 237 | NO |
| CL 4 | RTHopen+0m ref=pd onrange hi0.67 dir=against hold=120m | 165 | 2 | 0.76 | 0.26 | -0.08 | -0.83 / 1.28 | 0.16 / -0.23 / -0.50 | -0.10 | -0.05 | 0.70 | -0.31 | 0.00 | 325 | NO |
| CL 5 | RTHopen+0m ref=on onrange lo0.33 dir=against hold=flat | 185 | 2 | 0.52 | -0.93 | 0.36 | 0.18 / 1.20 | 0.06 / -0.17 / 0.14 | 0.01 | 0.20 | 0.83 | -0.12 | 0.50 | 235 | NO |
| CL 6 | RTHopen+0m ref=on onrange hi0.67 dir=against hold=120m | 164 | 2 | 0.44 | -0.19 | -0.27 | -1.00 / 1.11 | 0.08 / -0.04 / -0.46 | -0.11 | -0.08 | 0.47 | -0.28 | 0.00 | 324 | NO |
| CL 7 | RTHopen+15m ref=ft onrange lo0.33 dir=with hold=120m | 184 | 2 | 0.39 | -0.29 | 0.11 | -0.81 / 1.25 | 0.05 / -0.20 / 0.02 | -0.05 | 0.05 | 0.81 | -0.17 | 0.75 | 233 | NO |
| CL 8 (diag) | RTHopen+0m ref=pd onrange hi0.67 dir=against hold=flat | 165 | 1 | 1.11 | -0.01 | -0.36 | -1.63 / 1.35 | 0.21 / -0.20 / -1.06 | -0.19 | 0.03 | 0.34 | -0.41 | 0.00 | 325 | diag |
| CL 9 (diag) | RTHopen+0m ref=pd onrange any0.0 dir=against hold=flat | 517 | 1 | 0.97 | -0.32 | -0.38 | -1.80 / 1.21 | 0.18 / -0.34 / -0.79 | -0.19 | 0.11 | 0.33 | -0.36 | 0.00 | 827 | diag |
| CL 10 (diag) | RTHopen+30m ref=pd onrange hi0.67 dir=against hold=flat | 165 | 1 | 0.94 | -0.20 | -0.35 | -1.55 / 1.52 | 0.16 / 0.06 / -1.01 | -0.18 | 0.05 | 0.31 | -0.39 | 0.00 | 325 | diag |
| ZN 1 | RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | 138 | 2 | 0.42 | -1.64 | -0.17 | -1.25 / -1.72 | 0.07 / 0.05 / -0.43 | -0.29 | -0.17 | 1.00 | -0.23 | 0.00 | 238 | NO |
| ZN 2 | RTHopen+0m ref=pd onrange lo0.33 dir=with hold=120m | 215 | 2 | 0.16 | -1.74 | -0.67 | -2.84 / -1.87 | -0.03 / -0.54 / -0.24 | -0.37 | 0.01 | 0.99 | -0.32 | 0.00 | 328 | NO |
| ZN 3 (diag) | RTHopen+0m ref=pd onrange lo0.33 dir=with hold=flat | 215 | 1 | 0.10 | -1.50 | -0.83 | -3.30 / 0.50 | -0.06 / -0.65 / -0.34 | -0.38 | 0.15 | 0.61 | -0.38 | 0.00 | 328 | diag |
| ZN 4 (diag) | RTHopen+15m ref=ft onrange lo0.33 dir=with hold=flat | 200 | 1 | 0.06 | -1.02 | -0.50 | -1.93 / 0.41 | -0.01 / -0.43 / -0.16 | -0.30 | 0.40 | 0.75 | -0.28 | 0.00 | 304 | diag |
| ZN 5 (diag) | RTHopen+30m ref=ft onrange hi0.67 dir=against hold=flat | 128 | 1 | -0.02 | -0.94 | -0.37 | -1.00 / 0.34 | 0.02 / -0.24 / -0.14 | -0.23 | -0.46 | 0.83 | -0.23 | 0.00 | 219 | diag |
| BTC 1 | RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | 170 | 2 | 1.38 | -1.32 | 0.52 | -0.63 / 1.34 | 0.22 / 0.20 / -0.28 | 0.07 | 0.28 | 0.86 | -0.11 | 0.25 | 251 | NO |
| BTC 2 | RTHopen+30m ref=ft onrange lo0.33 dir=against hold=120m | 131 | 2 | 1.19 | 0.44 | 0.74 | 0.33 / 1.01 | 0.17 / -0.10 / 0.19 | 0.10 | 0.39 | 0.96 | -0.08 | 0.25 | 218 | NO |
| BTC 3 | RTHopen+30m ref=pd onrange hi0.67 dir=against hold=flat | 172 | 2 | 1.14 | 0.48 | 0.59 | -0.81 / 1.55 | 0.19 / -0.35 / 0.10 | 0.08 | 0.47 | 0.79 | -0.07 | 0.00 | 254 | NO |
| BTC 4 | RTHopen+15m ref=pd onrange lo0.33 dir=with hold=flat | 144 | 2 | 1.09 | 0.49 | 1.00 | 0.61 / 1.67 | 0.23 / -0.07 / 0.19 | 0.16 | -0.52 | 0.97 | -0.01 | 1.00 | 234 | NO |
| BTC 5 | RTHopen+30m ref=ft onrange hi0.67 dir=against hold=120m | 168 | 2 | 0.98 | -0.92 | 0.98 | 0.98 / 1.19 | 0.15 / 0.13 / 0.08 | 0.12 | -0.31 | 0.99 | -0.05 | 0.50 | 247 | LEAD |
| BTC 6 | RTHopen+15m ref=pd onrange hi0.67 dir=against hold=flat | 171 | 2 | 0.94 | 0.31 | 0.44 | -0.81 / 1.30 | 0.15 / -0.37 / 0.09 | 0.05 | 0.52 | 0.83 | -0.10 | 0.00 | 252 | NO |
| BTC 7 | RTHopen+0m ref=pd onrange lo0.33 dir=with hold=flat | 119 | 2 | 0.92 | 0.19 | 1.00 | 0.87 / 1.44 | 0.19 / -0.04 / 0.22 | 0.16 | -0.68 | 0.97 | -0.01 | 1.00 | 193 | NO |
| BTC 8 | RTHopen+30m ref=pd onrange lo0.33 dir=with hold=flat | 144 | 2 | 0.89 | 0.71 | 0.82 | 0.42 / 1.35 | 0.20 / -0.09 / 0.17 | 0.13 | -0.56 | 0.95 | -0.06 | 0.50 | 233 | NO |
| BTC 9 | RTHopen+30m ref=on onrange hi0.67 dir=against hold=120m | 170 | 2 | 0.83 | -1.54 | 0.47 | -0.06 / 1.09 | 0.15 / 0.15 / -0.11 | 0.08 | -0.34 | 0.88 | -0.11 | 0.50 | 249 | NO |
| BTC 10 | RTHopen+15m ref=ft onrange hi0.67 dir=against hold=flat | 170 | 2 | 0.77 | 0.36 | 0.64 | 0.35 / 1.21 | 0.14 / 0.25 / -0.00 | 0.10 | 0.32 | 0.88 | -0.04 | 0.50 | 251 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 69 |
| diagnostic cells read | 6 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 4 / 5 / 6 / 4 |
| all-in uplift @20% > 0 (all scored) | 55 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 7 |
| standalone pair-window Sharpe above own random-entry null p95 | 34 |
| worst-decile corr <= +0.30 | 58 |
| plateau >= 0.75 | 20 |
| all-in uplift at 2x slippage >= +0.10 | 30 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 5 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC RTHopen+15m ref=pd onrange lo0.33 dir=with hold=flat | clean | 1.29 | 2.60 | -112008 | -90034 | 310602 | -140525 | 4.05 | 32.4 | 1.69 | -83313 | 298524 | -92712 |
| BTC RTHopen+15m ref=pd onrange lo0.33 dir=with hold=flat | H1 | -0.15 | -0.21 | -240240 | -196207 | 405827 | -331248 | -0.15 | 42.9 | 2.76 | -80579 | 133426 | -82871 |
| BTC RTHopen+15m ref=pd onrange lo0.33 dir=with hold=flat | H2 | 1.87 | 4.90 | -69992 | -58197 | 229262 | -73475 | 2.17 | 22.2 | 2.49 | -76794 | 215353 | -77416 |
| BTC RTHopen+15m ref=pd onrange lo0.33 dir=with hold=flat | all | 1.00 | 1.75 | -140074 | -105177 | 405827 | -331248 | 4.17 | 32.1 | 2.03 | -82084 | 298524 | -92712 |
| CL RTHopen+30m ref=on onrange lo0.33 dir=against hold=flat | clean | 0.71 | 1.03 | -138251 | -114202 | 417383 | -233892 | 1.55 | 30.5 | 1.56 | -82138 | 281548 | -96524 |
| CL RTHopen+30m ref=on onrange lo0.33 dir=against hold=flat | H1 | 0.58 | 0.86 | -54324 | -48736 | 116409 | -65937 | 0.52 | 32.1 | 2.87 | -77610 | 138625 | -78287 |
| CL RTHopen+30m ref=on onrange lo0.33 dir=against hold=flat | H2 | 0.99 | 1.58 | -81285 | -40643 | 151799 | -142409 | 1.24 | 5.6 | 2.43 | -81089 | 206594 | -82524 |
| CL RTHopen+30m ref=on onrange lo0.33 dir=against hold=flat | all | 0.72 | 1.05 | -129816 | -99246 | 417383 | -233892 | 2.14 | 25.6 | 1.95 | -82121 | 281548 | -96524 |
| ES RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | clean | 1.51 | 2.81 | -120272 | -86169 | 360740 | -174400 | 3.79 | 30.5 | 1.72 | -87127 | 294912 | -108964 |
| ES RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | H1 | 1.43 | 2.66 | -93949 | -71377 | 232845 | -123492 | 1.22 | 25.0 | 2.97 | -79000 | 161373 | -80106 |
| ES RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | H2 | 0.82 | 1.76 | -97463 | -94182 | 278118 | -98446 | 1.20 | 36.1 | 2.59 | -87388 | 210597 | -89120 |
| ES RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | all | 1.31 | 2.53 | -119240 | -92866 | 360740 | -174400 | 5.50 | 31.0 | 2.10 | -87170 | 294912 | -108964 |
| GC RTHopen+0m ref=on onrange any0.0 dir=with hold=flat | clean | 1.87 | 3.28 | -117389 | -93637 | 310562 | -189430 | 5.47 | 39.0 | 1.75 | -85190 | 263590 | -102507 |
| GC RTHopen+0m ref=on onrange any0.0 dir=with hold=flat | H1 | 0.26 | 0.46 | -264881 | -253376 | 1482844 | -276333 | 0.13 | 57.1 | 2.64 | -99837 | 216367 | -127618 |
| GC RTHopen+0m ref=on onrange any0.0 dir=with hold=flat | H2 | 2.91 | 6.36 | -238404 | -194871 | 492523 | -268699 | 4.88 | 38.9 | 3.49 | -95299 | 189387 | -98854 |
| GC RTHopen+0m ref=on onrange any0.0 dir=with hold=flat | all | 1.54 | 2.97 | -214914 | -169345 | 1482844 | -276333 | 2.89 | 42.3 | 2.28 | -92847 | 263590 | -127618 |
| NQ RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | clean | 1.55 | 2.58 | -119814 | -94834 | 333607 | -169723 | 4.23 | 39.0 | 1.81 | -84326 | 270518 | -93390 |
| NQ RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | H1 | -1.12 | -1.34 | -190241 | -185617 | 397590 | -199469 | -1.00 | 53.6 | 2.19 | -100527 | 193089 | -114490 |
| NQ RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | H2 | 0.28 | 0.44 | -205405 | -186757 | 681295 | -211857 | 0.23 | 47.2 | 2.39 | -94791 | 211989 | -98763 |
| NQ RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | all | 0.63 | 0.93 | -179889 | -146453 | 761923 | -211857 | 1.53 | 42.9 | 2.02 | -91362 | 270518 | -114490 |
| RTY RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | clean | 2.15 | 5.19 | -89567 | -68223 | 204602 | -141857 | 9.54 | 27.6 | 1.84 | -79572 | 250265 | -84636 |
| RTY RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | H1 | 0.94 | 1.58 | -109091 | -97539 | 253390 | -131874 | 0.84 | 28.6 | 3.12 | -79701 | 177224 | -82747 |
| RTY RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | H2 | 1.03 | 2.07 | -163778 | -120152 | 528871 | -197911 | 0.89 | 33.3 | 2.69 | -85554 | 217425 | -90102 |
| RTY RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | all | 1.65 | 3.47 | -119772 | -88426 | 528871 | -197911 | 4.98 | 29.2 | 2.21 | -81295 | 250265 | -90102 |
| YM RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | clean | 0.92 | 1.55 | -124823 | -97945 | 319604 | -191823 | 2.60 | 32.4 | 1.66 | -83093 | 281826 | -92472 |
| YM RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | H1 | 0.41 | 0.63 | -153634 | -139806 | 240611 | -167279 | 0.50 | 28.6 | 2.92 | -82556 | 136808 | -88673 |
| YM RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | H2 | 2.37 | 6.65 | -113719 | -98672 | 314788 | -118004 | 4.24 | 36.1 | 2.97 | -86974 | 225213 | -90996 |
| YM RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | all | 1.25 | 2.46 | -135187 | -108531 | 441749 | -191823 | 5.17 | 32.7 | 2.16 | -84604 | 281826 | -92472 |
| ZN RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | clean | 0.42 | 0.65 | -130600 | -104904 | 530675 | -189690 | 0.71 | 30.5 | 1.53 | -81850 | 302815 | -89905 |
| ZN RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | H1 | 1.91 | 4.80 | -30757 | -24750 | 55462 | -43809 | 3.19 | 17.9 | 2.88 | -78884 | 150593 | -79480 |
| ZN RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | H2 | -2.32 | -2.74 | -127544 | -118104 | 1277331 | -139196 | -0.62 | 58.3 | 1.87 | -90088 | 230744 | -94827 |
| ZN RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | all | -0.17 | -0.24 | -128959 | -109393 | 1277331 | -189690 | -0.18 | 34.5 | 1.81 | -83720 | 302815 | -94827 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | -7.8 | -18.7 | 14.3 | 10.6 | -19.6 / 13.2 | 26.5 / 27.2 | NO |
| NQ RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | -17.0 | -32.2 | 5.3 | 26.8 | 8.9 / 18.4 | -39.4 / -14.3 | NO |
| RTY RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | -0.6 | 13.4 | 25.3 | 34.6 | 20.5 / 27.4 | 20.1 / 26.0 | INSURANCE |
| YM RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | -4.5 | 6.9 | 18.4 | 29.1 | 6.1 / 20.4 | 10.1 / 20.4 | NO |
| GC RTHopen+0m ref=on onrange any0.0 dir=with hold=flat | 17.9 | -57.4 | 0.4 | -18.9 | -12.3 / 16.8 | -65.9 / -31.7 | NO |
| CL RTHopen+30m ref=on onrange lo0.33 dir=against hold=flat | -20.0 | -0.6 | 19.4 | 27.0 | -1.4 / 14.0 | 30.0 / 30.0 | NO |
| ZN RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | -32.6 | 7.6 | 18.3 | 4.7 | 10.8 / 22.6 | 26.3 / 27.5 | NO |
| BTC RTHopen+15m ref=pd onrange lo0.33 dir=with hold=flat | -11.1 | -5.9 | 21.2 | 20.1 | -6.7 / 18.5 | 19.8 / 21.5 | NO |

INSURANCE count: 1.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | negative pre-2023 | 837 | -36.1 | -65.5 | -51.5 | 29.4 | -0.29 / -0.52 / -0.41 | 279.9 / 250.6 |
| ES 2 RTHopen+15m ref=on onrange any0.0 dir=against hold=120m | negative pre-2023 | 2444 | -17.6 | -47.0 | -33.4 | 29.4 | -0.34 / -0.91 / -0.65 | 126.0 / 96.6 |
| ES 3 RTHopen+0m ref=on onrange hi0.67 dir=against hold=120m | negative pre-2023 | 828 | -7.7 | -37.0 | -23.1 | 29.4 | -0.06 / -0.31 / -0.19 | 247.1 / 217.7 |
| ES 4 RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2428 | 7.3 | -22.0 | -8.4 | 29.4 | 0.15 / -0.44 / -0.17 | 115.4 / 86.1 |
| ES 5 RTHopen+30m ref=ft onrange lo0.33 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 842 | 2.3 | -27.0 | -13.9 | 29.4 | 0.05 / -0.53 / -0.27 | 114.8 / 85.4 |
| ES 6 RTHopen+0m ref=on onrange hi0.67 dir=against hold=flat | negative pre-2023 | 828 | -4.3 | -33.7 | -19.7 | 29.4 | -0.02 / -0.16 / -0.10 | 519.2 / 489.8 |
| ES 7 RTHopen+30m ref=on onrange any0.0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2442 | 5.1 | -24.3 | -10.7 | 29.4 | 0.10 / -0.49 / -0.21 | 78.3 / 48.9 |
| ES 8 RTHopen+15m ref=ft onrange any0.0 dir=against hold=120m | negative pre-2023 | 2408 | -21.0 | -50.4 | -36.8 | 29.4 | -0.43 / -1.02 / -0.74 | 75.3 / 45.9 |
| ES 9 RTHopen+30m ref=on onrange lo0.33 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 855 | 3.8 | -25.5 | -12.5 | 29.4 | 0.08 / -0.51 / -0.25 | 70.7 / 41.4 |
| ES 10 RTHopen+30m ref=on onrange hi0.67 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 839 | 11.5 | -17.8 | -3.8 | 29.4 | 0.10 / -0.15 / -0.03 | 127.1 / 97.7 |
| NQ 1 RTHopen+15m ref=ft onrange any0.0 dir=with hold=flat | positive pre-2023 | 2442 | 65.7 | 51.3 | 59.6 | 14.4 | 0.52 / 0.41 / 0.47 | 524.5 / 510.2 |
| NQ 2 RTHopen+0m ref=on onrange any0.0 dir=against hold=120m | negative pre-2023 | 2442 | -23.2 | -37.6 | -29.4 | 14.4 | -0.27 / -0.43 / -0.34 | 226.3 / 211.9 |
| NQ 3 RTHopen+15m ref=ft onrange hi0.67 dir=with hold=flat | positive pre-2023 | 880 | 95.5 | 81.2 | 89.6 | 14.4 | 0.36 / 0.31 / 0.34 | 790.6 / 776.3 |
| NQ 4 RTHopen+0m ref=on onrange hi0.67 dir=against hold=120m | positive pre-2023 | 881 | 46.6 | 32.3 | 40.7 | 14.4 | 0.26 / 0.18 / 0.23 | 394.5 / 380.1 |
| NQ 5 RTHopen+30m ref=on onrange any0.0 dir=with hold=flat | positive pre-2023 | 2456 | 35.9 | 21.5 | 29.7 | 14.4 | 0.30 / 0.18 / 0.25 | 289.6 / 275.2 |
| NQ 6 RTHopen+30m ref=ft onrange any0.0 dir=with hold=120m | positive pre-2023 | 2451 | 29.5 | 15.1 | 23.4 | 14.4 | 0.40 / 0.21 / 0.32 | 152.3 / 138.0 |
| NQ 7 RTHopen+0m ref=on onrange lo0.33 dir=against hold=120m | negative pre-2023 | 807 | -73.0 | -87.4 | -79.4 | 14.4 | -0.64 / -0.76 / -0.69 | 242.3 / 228.0 |
| NQ 8 RTHopen+30m ref=ft onrange any0.0 dir=with hold=flat | positive pre-2023 | 2451 | 49.8 | 35.4 | 43.6 | 14.4 | 0.43 / 0.31 / 0.38 | 250.3 / 236.0 |
| NQ 9 RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | negative pre-2023 | 886 | -0.3 | -14.6 | -6.2 | 14.4 | -0.00 / -0.08 / -0.03 | 331.0 / 316.7 |
| NQ 10 RTHopen+0m ref=on onrange hi0.67 dir=against hold=flat | positive pre-2023 | 881 | 59.8 | 45.4 | 53.9 | 14.4 | 0.21 / 0.16 / 0.19 | 813.6 / 799.2 |
| RTY 1 RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | negative pre-2023 | 444 | -49.6 | -63.9 | -61.1 | 14.4 | -0.49 / -0.63 / -0.60 | 196.2 / 181.8 |
| RTY 2 RTHopen+15m ref=ft onrange any0.0 dir=against hold=120m | negative pre-2023 | 1306 | -36.9 | -51.2 | -49.3 | 14.4 | -0.74 / -1.03 / -0.99 | 74.2 / 59.9 |
| RTY 3 RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | negative pre-2023 | 444 | -3.8 | -18.1 | -15.3 | 14.4 | -0.04 / -0.19 / -0.16 | 113.4 / 99.1 |
| RTY 4 RTHopen+15m ref=ft onrange hi0.67 dir=against hold=flat | negative pre-2023 | 444 | -43.9 | -58.3 | -55.4 | 14.4 | -0.31 / -0.42 / -0.40 | 159.8 / 145.5 |
| RTY 5 RTHopen+15m ref=on onrange lo0.33 dir=with hold=flat | positive pre-2023 | 439 | 61.1 | 46.7 | 47.9 | 14.4 | 0.58 / 0.44 / 0.46 | 77.3 / 63.0 |
| RTY 6 RTHopen+0m ref=on onrange lo0.33 dir=with hold=flat | positive pre-2023 | 436 | 89.0 | 74.7 | 75.8 | 14.4 | 0.84 / 0.71 / 0.72 | 79.1 / 64.7 |
| RTY 7 RTHopen+15m ref=on onrange any0.0 dir=against hold=120m | negative pre-2023 | 1304 | -21.4 | -35.7 | -33.8 | 14.4 | -0.45 / -0.76 / -0.72 | 52.7 / 38.4 |
| RTY 8 RTHopen+30m ref=pd onrange hi0.67 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 446 | 1.7 | -12.6 | -9.7 | 14.4 | 0.02 / -0.12 / -0.10 | 74.0 / 59.7 |
| RTY 9 RTHopen+30m ref=on onrange hi0.67 dir=against hold=120m | positive pre-2023 | 447 | 14.7 | 0.4 | 3.3 | 14.4 | 0.15 / 0.00 / 0.03 | 60.8 / 46.5 |
| RTY 10 RTHopen+30m ref=ft onrange hi0.67 dir=with hold=flat | positive pre-2023 | 446 | 51.8 | 37.4 | 40.3 | 14.4 | 0.33 / 0.24 / 0.26 | 116.0 / 101.7 |
| YM 1 RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | negative pre-2023 | 837 | -9.0 | -23.3 | -17.7 | 14.4 | -0.10 / -0.25 / -0.19 | 158.0 / 143.6 |
| YM 2 RTHopen+30m ref=ft onrange lo0.33 dir=with hold=flat | negative pre-2023 | 862 | -25.2 | -39.5 | -34.5 | 14.4 | -0.34 / -0.53 / -0.46 | 107.0 / 92.6 |
| YM 3 RTHopen+0m ref=pd onrange hi0.67 dir=with hold=120m | positive pre-2023 | 833 | 26.4 | 12.0 | 17.7 | 14.4 | 0.26 / 0.12 / 0.18 | 137.9 / 123.6 |
| YM 4 RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 830 | 8.5 | -5.8 | -0.2 | 14.4 | 0.08 / -0.06 / -0.00 | 106.8 / 92.4 |
| YM 5 RTHopen+15m ref=pd onrange lo0.33 dir=against hold=120m | positive pre-2023 | 871 | 15.3 | 0.9 | 6.0 | 14.4 | 0.32 / 0.02 / 0.12 | 46.8 / 32.4 |
| YM 6 RTHopen+30m ref=on onrange hi0.67 dir=against hold=120m | positive pre-2023 | 841 | 21.2 | 6.8 | 12.5 | 14.4 | 0.24 / 0.08 / 0.14 | 75.0 / 60.7 |
| YM 7 RTHopen+30m ref=on onrange any0.0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2457 | 5.9 | -8.4 | -3.0 | 14.4 | 0.15 / -0.22 / -0.08 | 44.7 / 30.3 |
| YM 8 RTHopen+30m ref=ft onrange hi0.67 dir=against hold=120m | negative pre-2023 | 837 | -8.0 | -22.3 | -16.7 | 14.4 | -0.08 / -0.21 / -0.16 | 76.1 / 61.7 |
| YM 9 RTHopen+15m ref=ft onrange lo0.33 dir=with hold=flat | negative pre-2023 | 860 | -1.0 | -15.4 | -10.3 | 14.4 | -0.02 / -0.22 / -0.15 | 78.2 / 63.8 |
| YM 10 RTHopen+15m ref=on onrange hi0.67 dir=against hold=flat | negative pre-2023 | 837 | -9.3 | -23.6 | -18.0 | 14.4 | -0.06 / -0.15 / -0.12 | 79.0 / 64.6 |
| GC 1 RTHopen+15m ref=on onrange any0.0 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2428 | 3.0 | -21.3 | -11.6 | 24.4 | 0.05 / -0.33 / -0.18 | 243.9 / 219.6 |
| GC 2 RTHopen+30m ref=on onrange any0.0 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2425 | 3.9 | -20.4 | -10.7 | 24.4 | 0.06 / -0.32 / -0.17 | 227.9 / 203.5 |
| GC 3 RTHopen+30m ref=ft onrange hi0.67 dir=with hold=flat | negative pre-2023 | 752 | -40.9 | -65.3 | -55.7 | 24.4 | -0.32 / -0.51 / -0.43 | 362.4 / 338.0 |
| GC 4 RTHopen+0m ref=on onrange any0.0 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2426 | 9.5 | -14.8 | -5.1 | 24.4 | 0.14 / -0.20 / -0.07 | 227.8 / 203.5 |
| GC 5 RTHopen+30m ref=on onrange hi0.67 dir=with hold=flat | negative pre-2023 | 762 | -12.3 | -36.7 | -27.1 | 24.4 | -0.09 / -0.27 / -0.20 | 304.7 / 280.4 |
| GC 6 RTHopen+30m ref=ft onrange any0.0 dir=with hold=flat | negative pre-2023 | 2395 | -31.5 | -55.9 | -46.2 | 24.4 | -0.49 / -0.86 / -0.71 | 183.7 / 159.4 |
| GC 7 RTHopen+0m ref=on onrange hi0.67 dir=with hold=flat | negative pre-2023 | 763 | -9.8 | -34.1 | -24.5 | 24.4 | -0.07 / -0.23 / -0.17 | 326.6 / 302.2 |
| GC 8 RTHopen+0m ref=on onrange hi0.67 dir=with hold=120m | negative pre-2023 | 763 | -23.1 | -47.5 | -37.8 | 24.4 | -0.23 / -0.47 / -0.37 | 178.8 / 154.4 |
| GC 9 RTHopen+15m ref=on onrange hi0.67 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 761 | 2.1 | -22.3 | -12.7 | 24.4 | 0.02 / -0.16 / -0.09 | 286.0 / 261.6 |
| GC 10 RTHopen+15m ref=on onrange hi0.67 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 761 | 1.0 | -23.4 | -13.8 | 24.4 | 0.01 / -0.23 / -0.14 | 152.9 / 128.6 |
| CL 1 RTHopen+30m ref=pd onrange any0.0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2453 | 13.5 | -10.8 | -7.2 | 24.4 | 0.30 / -0.23 / -0.15 | 72.4 / 48.0 |
| CL 2 RTHopen+15m ref=pd onrange any0.0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2452 | 6.6 | -17.8 | -14.2 | 24.4 | 0.14 / -0.38 / -0.31 | 59.2 / 34.8 |
| CL 3 RTHopen+30m ref=on onrange lo0.33 dir=against hold=flat | negative pre-2023 | 826 | -75.1 | -99.5 | -96.4 | 24.4 | -0.84 / -1.11 / -1.08 | 88.4 / 64.0 |
| CL 4 RTHopen+0m ref=pd onrange hi0.67 dir=against hold=120m | positive pre-2023 | 842 | 48.3 | 23.9 | 28.3 | 24.4 | 0.53 / 0.26 / 0.31 | 96.7 / 72.4 |
| CL 5 RTHopen+0m ref=on onrange lo0.33 dir=against hold=flat | negative pre-2023 | 827 | -67.6 | -91.9 | -88.8 | 24.4 | -0.68 / -0.93 / -0.90 | 65.3 / 40.9 |
| CL 6 RTHopen+0m ref=on onrange hi0.67 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 841 | 4.1 | -20.2 | -15.9 | 24.4 | 0.04 / -0.19 / -0.15 | 69.0 / 44.6 |
| CL 7 RTHopen+15m ref=ft onrange lo0.33 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 821 | 5.4 | -19.0 | -15.9 | 24.4 | 0.09 / -0.29 / -0.24 | 49.4 / 25.0 |
| CL 8 (diag) RTHopen+0m ref=pd onrange hi0.67 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 842 | 23.5 | -0.9 | 3.5 | 24.4 | 0.15 / -0.01 / 0.02 | 171.9 / 147.5 |
| CL 9 (diag) RTHopen+0m ref=pd onrange any0.0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2453 | 0.5 | -23.8 | -20.2 | 24.4 | 0.01 / -0.32 / -0.27 | 79.2 / 54.9 |
| CL 10 (diag) RTHopen+30m ref=pd onrange hi0.67 dir=against hold=flat | negative pre-2023 | 843 | -4.1 | -28.4 | -24.0 | 24.4 | -0.03 / -0.20 / -0.17 | 143.9 / 119.5 |
| ZN 1 RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | negative pre-2023 | 887 | -4.1 | -39.7 | -44.7 | 35.6 | -0.18 / -1.64 / -1.83 | 46.6 / 11.0 |
| ZN 2 RTHopen+0m ref=pd onrange lo0.33 dir=with hold=120m | negative pre-2023 | 797 | -9.3 | -44.9 | -50.2 | 35.6 | -0.37 / -1.74 / -1.93 | 38.5 / 2.9 |
| ZN 3 (diag) RTHopen+0m ref=pd onrange lo0.33 dir=with hold=flat | negative pre-2023 | 798 | -17.1 | -52.7 | -58.0 | 35.6 | -0.49 / -1.50 / -1.65 | 35.7 / 0.1 |
| ZN 4 (diag) RTHopen+15m ref=ft onrange lo0.33 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 741 | 2.8 | -32.8 | -38.0 | 35.6 | 0.09 / -1.02 / -1.18 | 35.6 / 0.0 |
| ZN 5 (diag) RTHopen+30m ref=ft onrange hi0.67 dir=against hold=flat | negative pre-2023 | 839 | -3.8 | -39.4 | -44.4 | 35.6 | -0.09 / -0.94 / -1.06 | 34.8 / -0.8 |
| BTC 1 RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m | negative pre-2023 | 22 | -631.8 | -686.2 | -653.6 | 54.4 | -1.23 / -1.32 / -1.27 | 680.6 / 626.2 |
| BTC 2 RTHopen+30m ref=ft onrange lo0.33 dir=against hold=120m | positive pre-2023 | 68 | 142.3 | 87.9 | 122.2 | 54.4 | 0.67 / 0.44 / 0.59 | 534.4 / 480.0 |
| BTC 3 RTHopen+30m ref=pd onrange hi0.67 dir=against hold=flat | positive pre-2023 | 22 | 456.8 | 402.5 | 435.0 | 54.4 | 0.54 / 0.48 / 0.51 | 1163.8 / 1109.4 |
| BTC 4 RTHopen+15m ref=pd onrange lo0.33 dir=with hold=flat | positive pre-2023 | 72 | 243.1 | 188.7 | 222.6 | 54.4 | 0.62 / 0.49 / 0.57 | 931.9 / 877.6 |
| BTC 5 RTHopen+30m ref=ft onrange hi0.67 dir=against hold=120m | negative pre-2023 | 22 | -410.2 | -464.6 | -432.0 | 54.4 | -0.82 / -0.92 / -0.86 | 589.6 / 535.2 |
| BTC 6 RTHopen+15m ref=pd onrange hi0.67 dir=against hold=flat | positive pre-2023 | 22 | 342.0 | 287.7 | 320.2 | 54.4 | 0.36 / 0.31 / 0.34 | 1009.2 / 954.9 |
| BTC 7 RTHopen+0m ref=pd onrange lo0.33 dir=with hold=flat | positive pre-2023 | 64 | 125.0 | 70.6 | 104.6 | 54.4 | 0.29 / 0.19 / 0.25 | 929.4 / 875.1 |
| BTC 8 RTHopen+30m ref=pd onrange lo0.33 dir=with hold=flat | positive pre-2023 | 74 | 346.6 | 292.3 | 326.5 | 54.4 | 0.83 / 0.71 / 0.78 | 784.9 / 730.5 |
| BTC 9 RTHopen+30m ref=on onrange hi0.67 dir=against hold=120m | negative pre-2023 | 22 | -789.8 | -844.1 | -811.6 | 54.4 | -1.47 / -1.54 / -1.50 | 468.1 / 413.7 |
| BTC 10 RTHopen+15m ref=ft onrange hi0.67 dir=against hold=flat | positive pre-2023 | 22 | 430.7 | 376.3 | 408.9 | 54.4 | 0.41 / 0.36 / 0.39 | 743.8 / 689.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 24 cells pass the clean rule against a replicate mean of 16.2 (p(count) = 0.05, p(top) = 0.39); CL: 7 cells pass the clean rule against a replicate mean of 13.2 (p(count) = 0.99, p(top) = 0.86); ES: 16 cells pass the clean rule against a replicate mean of 14.3 (p(count) = 0.38, p(top) = 0.08); GC: 16 cells pass the clean rule against a replicate mean of 16.7 (p(count) = 0.59, p(top) = 0.00); NQ: 24 cells pass the clean rule against a replicate mean of 20.5 (p(count) = 0.24, p(top) = 0.11); RTY: 20 cells pass the clean rule against a replicate mean of 16.3 (p(count) = 0.18, p(top) = 0.25); YM: 14 cells pass the clean rule against a replicate mean of 16.6 (p(count) = 0.82, p(top) = 0.88); ZN: 2 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.38, p(top) = 0.59).
- Of 69 selected cells, 5 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.43 (GC RTHopen+0m ref=on onrange any0.0 dir=with hold=flat); bootstrap lower bound > 0 for 7 cells; plateau >= 0.75 for 20; 2x-slippage all-in uplift >= +0.10 for 30; gate_add PASS at some share: 5 (cell-share pairs).
- Gate-3 cell ES RTHopen+15m ref=on onrange hi0.67 dir=against hold=120m: uplift +0.26/+0.14/+0.29, boot lo +0.07, plateau 0.25, 2x-slip +0.22, wd corr +0.38, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell RTY RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m: uplift +0.38/+0.30/+0.40, boot lo +0.17, plateau 0.75, 2x-slip +0.34, wd corr -0.18, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell RTY RTHopen+15m ref=ft onrange hi0.67 dir=against hold=flat: uplift +0.20/+0.22/+0.14, boot lo +0.01, plateau 0.50, 2x-slip +0.17, wd corr +0.29, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell GC RTHopen+0m ref=on onrange hi0.67 dir=with hold=flat: uplift +0.22/+0.96/+0.25, boot lo +0.06, plateau 1.00, 2x-slip +0.31, wd corr +0.30, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell GC RTHopen+0m ref=on onrange hi0.67 dir=with hold=120m: uplift +0.22/+0.25/+0.21, boot lo -0.04, plateau 0.75, 2x-slip +0.19, wd corr -0.11, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 30, 'positive pre-2023': 22, 'gross-positive, cost-negative pre-2023': 17}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_4.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw4/ (`SW4_CO_all_selected_scored.csv`).

## 7. FOUND-CANDIDATE verification: RTY cell 39 (RTHopen+15m, reference = first-15-min move, overnight-range percentile >= 0.67, FADE the move, hold 120 min)
Status after verification: **FOUND-PENDING-REPLICATION (not FOUND).** Registered as SW4-REPL in PREREG_AUTOPILOT.md (post-hoc disclosure: the battery was run in one step before its text was written).
- Pipeline gates (all pass at 10/20/30/50% share): additive uplift clean/H1/H2 +0.38/+0.30/+0.40 at 20% (0.20/0.16/0.22 at 10%, 0.78/0.47/0.60 at 50%); worst week change +9.2% at 20% share (limit 20%); standalone pair-window Sharpe 1.65 vs own timing-destroyed null p95 0.84 (rank 1.00); bootstrap 90% lower bound +0.17; plateau 3 of 4 neighbours (0.75, exactly at the threshold); all-in uplift at 2x slippage +0.34; worst-decile-week correlation -0.18; trades in the pair window 290 (not small-sample).
- Caveats that keep it from FOUND: (a) ERA: pre-2023 (2017-07..2023-07) weekly Sharpe -0.63 net (-0.49 gross; 444 trades, -$64 net per trade at 1 contract), per-year standalone Sharpe 2018 -2.81, 2019 -1.89, 2020 -0.64, 2021 +0.29, 2022 -0.80, 2023 +0.59, 2024 +2.39, 2025 +1.97, 2026 +1.04: the effect exists only from 2023-08; (b) standalone out-of-sample (H1+H2) Sharpe 0.99 is BELOW the random-entry null p95 of 1.39 for that span (rank 0.85); (c) selection-aware test for this instrument: best clean Sharpe in the grid 2.16 vs 2.00 (p95 of the best cell in 100 timing-destroyed replicates), p(count of passing cells) 0.18, p(top mean) 0.25; (d) H0 (2023-02-10..2023-07-31, 25 weeks) FAILS: sleeve Sharpe -1.28, uplift -0.10; (e) no stop: worst single trade -$2,674 per RTY contract (the sleeve is sized 54 contracts at 100% of pair sigma, 10.8 at 20%); (f) 20+ comparable SW grids were run in this sweep, so one cell clearing the pipeline gates is inside the chance-pass expectation (see the final summary).
- Replication battery (ap_sw_repl.py; criteria R1 H0 sleeve Sharpe > 0 and uplift > 0 -> FAIL; R2 odd and even calendar months each uplift >= +0.18 -> PASS (odd +0.43, even +0.29); R3 same cell on ES / NQ / YM with positive clean, H1 and H2 uplift and positive standalone Sharpe -> ES PASS (+0.07/+0.11/+0.64), YM PASS (+0.20/+0.08/+0.76), NQ FAIL on clean (-0.04); 2 of 3 instruments). Two of the three replications pass, but R3 is not independent of the RTY H1/H2 read (correlated index futures, same days), H0 fails and the ERA is negative.
```
== R1/R2 on RTY cell 39 RTHopen+15m ref=ft onrange hi0.67 dir=against hold=120m scale 54.2
                        n_wk  sleeve_sh  pair_sh  uplift
H0 2023-02..07          25.0      -1.28     0.72   -0.10
clean                  104.0       2.16     1.39    0.39
H1                      28.0       0.94     3.09    0.29
H2                      35.0       1.05     2.40    0.41
odd months 2023-08..    85.0       2.09     2.22    0.43
even months 2023-08..   83.0       1.28     1.46    0.29
per-year weekly Sharpe (sleeve standalone): {2017: nan, 2018: -2.81, 2019: -1.89, 2020: -0.64, 2021: 0.29, 2022: -0.8, 2023: 0.59, 2024: 2.39, 2025: 1.97, 2026: 1.04}
== R3 same cell, other instruments (no re-selection)
   sym  scale  sh_pre2023  sh_clean  sh_H1  sh_H2  up_clean  up_H1  up_H2  H0_sh
0   ES   29.5       -0.41      0.41   0.66   2.53      0.07   0.11   0.64  -1.12
1   NQ   18.9       -0.24     -0.25   1.42   2.80     -0.04   0.29   0.90   2.21
2   YM   49.0       -0.06      0.92   0.41   2.60      0.20   0.08   0.76  -0.30
3   GC   36.6       -0.38     -0.13  -0.74  -0.45     -0.08  -1.74  -0.66  -0.28
4   CL   65.0       -0.49     -0.61  -1.44   0.72     -0.16  -0.18   0.03   2.33
5   ZN  324.3       -1.56     -0.28  -1.73  -0.51     -0.09  -0.33  -0.30  -1.03
6  BTC    8.2        0.37      0.63   1.61   1.21      0.08   0.45   0.16   0.55

```
- Reading: after a wide overnight range (top third of the prior 250 days) the first 15 minutes of the RTH session tend to reverse over the next two hours in the 2024-26 sample, on all four US equity index futures (GC, CL, ZN, BTC do not show it). It is the same mechanism family as the ES/YM 09:30 pre-open-move fades in SW5 (YM clock 09:30 ret30m against, gate-3). Fill model as stated above. NT8 spec: RTY (or M2K for small size) market buy/sell at RTH open + 15 min (one-minute bar open), direction opposite to the 09:30-09:44 return, only if the overnight (18:00-09:30 ET) range / open is in the top third of the prior 250 label days, time exit 120 minutes after entry, flatten by 16:55 ET. Executable at NinjaTrader Brokerage via Rithmic (CME). Margin unverified (RTY intraday ~$0.8-1k per contract; 11 contracts at 20% share).
- Next step for the lead: forward test (E8 weekly extension) on weeks after 2026-10-13; this cell was selected on clean and read on H1/H2 once.

DONE SW4
