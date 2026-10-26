# REPORT Q20 - Q20: distance from the prior-day close in ADR20 units, with/against, time exit

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 60 selected cells (+9 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.28; best pair-window standalone Sharpe +1.24.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: distance from the prior-day close in ADR20 units, with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         86 |        15 |               1.224 |                2 |         10 |            0 |
| CL    |      96 |         80 |         3 |               0.846 |                2 |          3 |            3 |
| ES    |      96 |         78 |        20 |               1.051 |                2 |         10 |            0 |
| GC    |      96 |         90 |         7 |               1.116 |                2 |          7 |            3 |
| HO    |      96 |         82 |        21 |               1.391 |                2 |         10 |            0 |
| NQ    |      96 |         80 |        14 |               1.037 |                2 |         10 |            0 |
| RTY   |      96 |         72 |        22 |               1.505 |                2 |         10 |            0 |
| ZN    |      96 |         80 |         0 |               0.173 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   20 |            9.14  |              20 |      0.005 |                       0.894 |            0.69  |           0.941 |    0.075 |       1.051 |                1.821 |
| NQ    |     200 |                   14 |           19.055 |              32 |      0.95  |                       0.641 |            1.038 |           1.305 |    0.995 |       0.978 |                2.169 |
| RTY   |     200 |                   22 |           11.755 |              22 |      0.005 |                       1.28  |            0.757 |           1.013 |    0     |       1.505 |                1.976 |
| GC    |     200 |                    7 |           10.62  |              19 |      0.905 |                       0.457 |            0.74  |           1.044 |    0.97  |       0.819 |                1.946 |
| CL    |     200 |                    3 |            6.72  |              16 |      0.96  |                       0.323 |            0.648 |           0.936 |    0.975 |       0.513 |                1.831 |
| ZN    |     200 |                    0 |            0.105 |               2 |      1     |                     nan     |            0.502 |           0.886 |  nan     |     nan     |                1.145 |
| BTC   |     200 |                   15 |           15.525 |              24 |      0.58  |                       0.669 |            0.89  |           1.163 |    0.9   |       0.985 |                2.095 |
| HO    |     200 |                   21 |           15.595 |              25 |      0.07  |                       0.926 |            0.918 |           1.194 |    0.495 |       1.259 |                2.089 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m priorclose(0,0.5) dir=against hold 180m all | 386 | 2 | 1.05 | -0.79 | -0.25 | -2.05 / 1.06 | 0.18 / -1.04 / -0.04 | -0.12 | -0.11 | 0.67 | -0.27 | 0.00 | 653 | NO |
| ES 2 | 5m priorclose(0,1.0) dir=with hold 60m all | 161 | 2 | 1.04 | -0.18 | 0.09 | -1.17 / 0.57 | 0.12 / -0.19 / -0.34 | -0.10 | 0.27 | 0.90 | -0.23 | 0.00 | 276 | NO |
| ES 3 | 5m priorclose(0,0.75) dir=with hold 60m all | 336 | 2 | 1.03 | -0.17 | 0.11 | -0.61 / 0.74 | 0.11 / -0.12 / -0.52 | -0.18 | -0.27 | 0.95 | -0.35 | 0.00 | 602 | NO |
| ES 4 | 5m priorclose(0,0.75) dir=with hold 60m day | 284 | 2 | 1.02 | 0.15 | 0.50 | -0.20 / 0.94 | 0.10 / -0.20 / -0.19 | -0.10 | 0.06 | 0.99 | -0.20 | 0.00 | 489 | NO |
| ES 5 | 15m priorclose(0,0.5) dir=against hold 240m all | 337 | 2 | 0.92 | -0.57 | 0.01 | -1.52 / 1.08 | 0.16 / -0.83 / 0.12 | -0.04 | -0.29 | 0.78 | -0.16 | 0.00 | 576 | NO |
| ES 6 | 5m priorclose(0,1.0) dir=with hold 120m all | 127 | 2 | 0.90 | 0.03 | -0.07 | -1.50 / 0.99 | 0.08 / -0.82 / -0.09 | -0.12 | 0.09 | 0.71 | -0.26 | 0.00 | 219 | NO |
| ES 7 | 15m priorclose(0,0.5) dir=against hold 240m day | 224 | 2 | 0.78 | -0.91 | 0.38 | -0.18 / 1.27 | 0.15 / -0.44 / 0.27 | 0.05 | -0.52 | 0.82 | -0.10 | 0.25 | 371 | NO |
| ES 8 | 5m priorclose(0,0.5) dir=against hold 240m all | 367 | 2 | 0.78 | -0.61 | -0.17 | -1.99 / 0.87 | 0.12 / -0.74 / -0.07 | -0.09 | -0.16 | 0.62 | -0.21 | 0.00 | 628 | NO |
| ES 9 | 5m priorclose(0,1.0) dir=with hold 120m day | 109 | 2 | 0.75 | 0.04 | -0.05 | -1.23 / 1.06 | 0.06 / -0.69 / -0.07 | -0.11 | 0.10 | 0.55 | -0.25 | 0.00 | 176 | NO |
| ES 10 | 5m priorclose(0,1.0) dir=with hold 60m day | 137 | 2 | 0.67 | -0.05 | 0.23 | -0.29 / 0.91 | 0.05 / -0.10 / -0.10 | -0.07 | 0.15 | 0.92 | -0.22 | 0.00 | 220 | NO |
| NQ 1 | 5m priorclose(0,1.0) dir=with hold 120m all | 131 | 2 | 0.98 | -0.24 | 0.24 | -0.92 / 1.37 | 0.11 / -0.81 / 0.01 | -0.05 | -0.23 | 0.82 | -0.21 | 0.00 | 236 | NO |
| NQ 2 | 5m priorclose(0,1.0) dir=with hold 120m day | 111 | 2 | 0.93 | -0.32 | 0.12 | -1.13 / 1.78 | 0.10 / -0.78 / -0.12 | -0.08 | -0.18 | 0.62 | -0.24 | 0.00 | 194 | NO |
| NQ 3 | 5m priorclose(0,1.0) dir=with hold 60m day | 143 | 2 | 0.81 | -0.12 | 0.24 | -0.46 / 1.45 | 0.07 / -0.08 / -0.37 | -0.06 | 0.08 | 0.74 | -0.24 | 0.00 | 252 | NO |
| NQ 4 | 5m priorclose(0,1.0) dir=with hold 60m all | 169 | 2 | 0.73 | -0.14 | 0.10 | -0.77 / 1.66 | 0.05 / -0.23 / -0.31 | -0.08 | 0.02 | 0.68 | -0.26 | 0.00 | 305 | NO |
| NQ 5 | 15m priorclose(0,0.75) dir=with hold 120m day | 197 | 2 | 0.59 | 0.77 | 0.60 | 0.57 / 1.51 | 0.01 / 0.25 / -0.16 | -0.00 | 0.40 | 0.81 | -0.18 | 0.00 | 314 | NO |
| NQ 6 | 15m priorclose(0,0.75) dir=with hold 120m all | 231 | 2 | 0.59 | 0.52 | 0.41 | 0.16 / 1.14 | 0.01 / 0.15 / -0.19 | -0.03 | 0.40 | 0.88 | -0.21 | 0.00 | 403 | NO |
| NQ 7 | 5m priorclose(0,0.5) dir=with hold 120m all | 534 | 2 | 0.49 | -0.08 | 1.05 | 1.67 / 1.47 | 0.02 / 0.78 / 0.30 | 0.16 | -0.18 | 0.98 | -0.07 | 0.50 | 905 | NO |
| NQ 8 | 5m priorclose(0,0.75) dir=with hold 120m day | 227 | 2 | 0.45 | 0.78 | 0.44 | 0.39 / 1.37 | -0.01 / 0.38 / -0.25 | -0.02 | 0.34 | 0.80 | -0.22 | 0.00 | 367 | NO |
| NQ 9 | 15m priorclose(0,0.75) dir=with hold 180m all | 193 | 2 | 0.43 | 0.43 | 0.18 | -0.20 / 1.13 | 0.01 / -0.02 / -0.28 | -0.07 | 0.43 | 0.71 | -0.26 | 0.00 | 341 | NO |
| NQ 10 | 5m priorclose(0,0.5) dir=with hold 120m day | 396 | 2 | 0.40 | 0.05 | 0.91 | 1.49 / 1.20 | 0.00 / 0.78 / 0.10 | 0.12 | -0.12 | 0.96 | -0.12 | 0.00 | 625 | NO |
| RTY 1 | 15m priorclose(0,0.5) dir=against hold 240m day | 253 | 2 | 1.50 | -0.01 | 1.24 | 0.92 / 1.52 | 0.29 / -0.07 / 0.44 | 0.25 | -0.70 | 1.00 | 0.07 | 0.25 | 411 | NO |
| RTY 2 | 5m priorclose(0,0.5) dir=against hold 240m day | 292 | 2 | 1.47 | -0.14 | 1.14 | 0.71 / 1.57 | 0.28 / -0.19 / 0.43 | 0.22 | -0.64 | 1.00 | 0.04 | 0.00 | 464 | NO |
| RTY 3 | 5m priorclose(0,0.5) dir=against hold 180m all | 451 | 2 | 1.37 | 0.08 | 0.49 | -0.97 / 1.27 | 0.28 / -0.45 / -0.17 | 0.03 | -0.25 | 0.94 | -0.11 | 0.25 | 731 | NO |
| RTY 4 | 15m priorclose(0,0.5) dir=against hold 180m day | 294 | 2 | 1.30 | -0.13 | 1.06 | 0.58 / 1.19 | 0.30 / -0.30 / 0.43 | 0.20 | -0.43 | 0.99 | 0.05 | 0.25 | 469 | NO |
| RTY 5 | 5m priorclose(0,0.5) dir=against hold 240m all | 387 | 2 | 1.28 | -0.02 | 0.80 | 0.10 / 1.08 | 0.25 / -0.34 / 0.24 | 0.13 | -0.48 | 0.97 | -0.03 | 0.25 | 631 | NO |
| RTY 6 | 5m priorclose(0,0.5) dir=against hold 180m day | 349 | 2 | 1.28 | -0.01 | 0.93 | 0.24 / 1.13 | 0.26 / -0.27 / 0.19 | 0.14 | -0.37 | 0.99 | -0.01 | 0.25 | 553 | NO |
| RTY 7 | 15m priorclose(0,0.75) dir=against hold 240m day | 125 | 2 | 1.20 | 0.46 | 1.21 | 1.21 / 1.25 | 0.13 / 0.29 / 0.14 | 0.13 | -0.55 | 1.00 | -0.01 | 0.25 | 216 | LEAD |
| RTY 8 | 15m priorclose(0,0.5) dir=against hold 60m day | 447 | 2 | 1.20 | -0.15 | 0.82 | 0.22 / 0.91 | 0.19 / -0.08 / 0.05 | 0.06 | -0.36 | 0.99 | -0.05 | 0.25 | 715 | NO |
| RTY 9 | 15m priorclose(0,0.5) dir=against hold 120m day | 360 | 2 | 1.11 | 0.23 | 1.12 | 0.92 / 1.27 | 0.19 / 0.05 / 0.23 | 0.14 | -0.03 | 1.00 | 0.03 | 0.50 | 574 | NO |
| RTY 10 | 15m priorclose(0,0.5) dir=against hold 180m all | 390 | 2 | 1.10 | 0.16 | 0.56 | -0.36 / 0.77 | 0.25 / -0.49 / 0.11 | 0.07 | -0.34 | 0.92 | -0.09 | 0.75 | 633 | NO |
| GC 1 | 5m priorclose(0,0.5) dir=with hold 120m day | 372 | 2 | 0.82 | 0.13 | -0.19 | -0.94 / 1.09 | 0.09 / -1.45 / -0.16 | -0.24 | -0.21 | 0.64 | -0.47 | 0.00 | 576 | NO |
| GC 2 | 5m priorclose(0,0.5) dir=with hold 240m day | 272 | 2 | 0.71 | 0.13 | 0.06 | -0.40 / 1.24 | 0.10 / -1.05 / 0.05 | -0.10 | -0.05 | 0.58 | -0.37 | 0.00 | 412 | NO |
| GC 3 | 5m priorclose(0,0.5) dir=with hold 180m all | 530 | 2 | 0.61 | -0.60 | -0.67 | -1.66 / 1.09 | 0.06 / -1.49 / -0.62 | -0.38 | 0.22 | 0.30 | -0.64 | 0.00 | 873 | NO |
| GC 4 | 15m priorclose(0,0.75) dir=against hold 180m all | 249 | 2 | 0.41 | -0.28 | 0.72 | 0.99 / 1.46 | 0.05 / 0.65 / -0.01 | 0.09 | -0.08 | 0.95 | -0.13 | 0.25 | 392 | NO |
| GC 5 | 15m priorclose(0,0.75) dir=with hold 120m day | 206 | 2 | 0.33 | 0.28 | -0.32 | -0.72 / 1.41 | -0.05 / -0.33 / -0.88 | -0.31 | 0.07 | 0.40 | -0.62 | 0.00 | 302 | NO |
| GC 6 | 15m priorclose(0,0.75) dir=with hold 240m day | 149 | 2 | 0.16 | 0.02 | -0.72 | -1.54 / 1.28 | -0.06 / -0.88 / -0.85 | -0.37 | -0.09 | 0.14 | -0.62 | 0.00 | 218 | NO |
| GC 7 | 5m priorclose(0,0.75) dir=against hold 240m all | 242 | 2 | 0.16 | -0.11 | -0.23 | -0.57 / 1.46 | 0.03 / -0.65 / -0.11 | -0.12 | -0.18 | 0.43 | -0.36 | 0.00 | 386 | NO |
| GC 8 (diag) | 5m priorclose(0,0.5) dir=with hold 180m day | 312 | 1 | 1.12 | 0.11 | 0.13 | -0.52 / 1.21 | 0.16 / -1.27 / -0.02 | -0.13 | 0.07 | 0.79 | -0.39 | 0.00 | 477 | diag |
| GC 9 (diag) | 15m priorclose(0,0.5) dir=with hold 240m all | 416 | 1 | 0.86 | -0.33 | 0.27 | -0.08 / 1.34 | 0.09 / -0.12 / -0.02 | -0.03 | -0.10 | 0.80 | -0.29 | 0.50 | 680 | diag |
| GC 10 (diag) | 15m priorclose(0,1.0) dir=with hold 240m day | 79 | 1 | 0.75 | 0.11 | -0.26 | -0.87 / 1.46 | 0.05 / -1.86 / -0.23 | -0.33 | -0.12 | 0.39 | -0.71 | 0.00 | 120 | diag |
| CL 1 | 5m priorclose(0,1.0) dir=with hold 120m day | 103 | 2 | 0.51 | -0.20 | -0.53 | -1.08 / 1.10 | 0.06 / -0.18 / -1.87 | -0.59 | -0.01 | 0.46 | -1.26 | 0.00 | 187 | NO |
| CL 2 | 15m priorclose(0,0.75) dir=against hold 240m day | 127 | 2 | 0.32 | -0.60 | 0.39 | 0.48 / 1.32 | 0.03 / -0.12 / 0.06 | -0.02 | -0.19 | 0.86 | -0.16 | 0.25 | 208 | NO |
| CL 3 | 15m priorclose(0,0.5) dir=against hold 240m all | 376 | 2 | 0.13 | -0.60 | -0.58 | -1.47 / 1.40 | -0.04 / -0.27 / -0.43 | -0.23 | 0.54 | 0.42 | -0.35 | 0.00 | 631 | NO |
| CL 4 (diag) | 15m priorclose(0,1.0) dir=with hold 180m all | 97 | 1 | 0.85 | -0.67 | -0.36 | -0.99 / 1.10 | 0.15 / -0.21 / -1.44 | -0.38 | -0.20 | 0.34 | -0.96 | 0.00 | 193 | diag |
| CL 5 (diag) | 15m priorclose(0,1.0) dir=with hold 180m day | 73 | 2 | 0.81 | -0.65 | -0.31 | -0.78 / 1.59 | 0.13 / -0.18 / -1.70 | -0.52 | 0.09 | 0.43 | -1.26 | 0.00 | 133 | diag |
| CL 6 (diag) | 15m priorclose(0,1.0) dir=with hold 120m day | 92 | 1 | 0.63 | -0.38 | -0.47 | -1.12 / 1.18 | 0.07 / -0.23 / -1.51 | -0.44 | -0.28 | 0.38 | -0.94 | 0.00 | 163 | diag |
| ZN 1 (diag) | 5m priorclose(0,1.0) dir=against hold 240m all | 86 | 1 | 0.17 | -0.82 | -0.03 | -0.46 / -1.50 | -0.03 / -0.18 / -0.03 | -0.20 | -0.23 | 1.00 | -0.19 | 0.00 | 131 | diag |
| ZN 2 (diag) | 5m priorclose(0,1.0) dir=against hold 180m all | 109 | 1 | -0.07 | -0.69 | -0.44 | -1.25 / -2.01 | -0.07 / -0.17 / -0.18 | -0.31 | -0.23 | 1.00 | -0.26 | 0.00 | 159 | diag |
| ZN 3 (diag) | 5m priorclose(0,0.75) dir=against hold 240m day | 151 | 1 | -0.14 | -1.53 | -0.68 | -1.77 / -1.18 | -0.08 / -0.28 / -0.26 | -0.40 | -0.38 | 1.00 | -0.32 | 0.00 | 239 | diag |
| BTC 1 | 15m priorclose(0,1.0) dir=against hold 60m all | 193 | 2 | 0.99 | -1.32 | 0.40 | -0.52 / 1.24 | 0.20 / -0.42 / 0.08 | 0.05 | 0.04 | 0.89 | -0.09 | 0.50 | 299 | NO |
| BTC 2 | 15m priorclose(0,1.0) dir=with hold 180m all | 135 | 2 | 0.90 | 0.31 | 0.55 | -0.17 / 1.29 | 0.13 / 0.05 / -0.21 | 0.03 | -0.03 | 0.91 | -0.13 | 0.25 | 211 | NO |
| BTC 3 | 15m priorclose(0,0.75) dir=with hold 240m day | 113 | 2 | 0.84 | 0.98 | 0.71 | 0.54 / 1.41 | 0.12 / 0.43 / -0.09 | 0.10 | -0.42 | 0.92 | -0.08 | 0.50 | 194 | NO |
| BTC 4 | 15m priorclose(0,1.0) dir=against hold 60m day | 123 | 2 | 0.73 | -1.71 | -0.05 | -1.25 / 1.39 | 0.16 / -0.63 / -0.01 | -0.02 | 0.12 | 0.63 | -0.17 | 0.50 | 192 | NO |
| BTC 5 | 5m priorclose(0,0.75) dir=against hold 180m day | 168 | 2 | 0.71 | -1.64 | 0.09 | -0.76 / 1.31 | 0.14 / -0.57 / -0.08 | -0.02 | -0.11 | 0.64 | -0.20 | 0.25 | 283 | NO |
| BTC 6 | 5m priorclose(0,0.75) dir=against hold 60m day | 282 | 2 | 0.60 | -0.30 | 0.19 | -0.39 / 0.85 | 0.12 / -0.25 / -0.12 | -0.01 | 0.01 | 0.81 | -0.17 | 0.50 | 479 | NO |
| BTC 7 | 15m priorclose(0,0.75) dir=against hold 60m day | 226 | 2 | 0.55 | -0.60 | 0.03 | -1.01 / 0.95 | 0.12 / -0.40 / -0.13 | -0.03 | 0.18 | 0.71 | -0.17 | 0.25 | 380 | NO |
| BTC 8 | 15m priorclose(0,0.75) dir=against hold 60m all | 388 | 2 | 0.50 | -0.65 | 0.16 | -0.59 / 1.27 | 0.13 / -0.29 / -0.03 | 0.00 | -0.17 | 0.82 | -0.12 | 0.00 | 609 | NO |
| BTC 9 | 5m priorclose(0,0.75) dir=against hold 120m day | 210 | 2 | 0.46 | -0.83 | 0.03 | -0.59 / 1.04 | 0.11 / -0.54 / -0.08 | -0.04 | 0.07 | 0.71 | -0.21 | 0.00 | 354 | NO |
| BTC 10 | 5m priorclose(0,0.5) dir=with hold 120m all | 698 | 2 | 0.40 | -0.08 | 0.34 | 0.36 / 1.34 | 0.01 / -0.09 / 0.06 | -0.04 | 0.43 | 0.90 | -0.16 | 0.50 | 1080 | NO |
| HO 1 | 5m priorclose(0,0.75) dir=against hold 180m all | 261 | 2 | 1.26 | 0.11 | 0.23 | -0.50 / 1.20 | 0.26 / -0.43 / -0.63 | -0.09 | 0.24 | 0.78 | -0.39 | 0.00 | 445 | NO |
| HO 2 | 15m priorclose(0,1.0) dir=against hold 60m all | 152 | 2 | 1.22 | 0.02 | 0.35 | -0.08 / 1.67 | 0.23 / -0.10 / -0.47 | -0.00 | 0.13 | 0.75 | -0.35 | 0.25 | 269 | NO |
| HO 3 | 5m priorclose(0,1.0) dir=against hold 120m all | 140 | 2 | 1.08 | 0.10 | -0.68 | -1.89 / 1.27 | 0.22 / -0.22 / -1.73 | -0.33 | 0.10 | 0.18 | -0.69 | 0.00 | 255 | NO |
| HO 4 | 5m priorclose(0,0.75) dir=against hold 180m day | 198 | 2 | 0.97 | 0.19 | 0.02 | -0.74 / 1.24 | 0.17 / -0.28 / -0.74 | -0.14 | 0.03 | 0.64 | -0.39 | 0.00 | 314 | NO |
| HO 5 | 5m priorclose(0,0.75) dir=against hold 120m all | 314 | 2 | 0.95 | -0.02 | -0.41 | -1.48 / 1.11 | 0.20 / -0.52 / -1.12 | -0.27 | 0.18 | 0.38 | -0.58 | 0.00 | 532 | NO |
| HO 6 | 15m priorclose(0,0.75) dir=against hold 240m day | 150 | 2 | 0.94 | -0.12 | 0.22 | -0.43 / 1.16 | 0.18 / -0.28 / -0.43 | -0.06 | -0.10 | 0.76 | -0.29 | 0.00 | 235 | NO |
| HO 7 | 15m priorclose(0,0.75) dir=against hold 180m day | 174 | 2 | 0.73 | -0.06 | 0.05 | -0.41 / 1.13 | 0.15 / -0.31 / -0.64 | -0.14 | 0.10 | 0.61 | -0.44 | 0.00 | 276 | NO |
| HO 8 | 15m priorclose(0,1.0) dir=against hold 120m all | 125 | 2 | 0.73 | 0.17 | -0.37 | -1.08 / 1.37 | 0.15 / 0.02 / -1.25 | -0.23 | 0.11 | 0.26 | -0.59 | 0.00 | 220 | NO |
| HO 9 | 15m priorclose(0,0.75) dir=against hold 120m all | 266 | 2 | 0.69 | -0.06 | -0.72 | -1.75 / 1.37 | 0.16 / -0.54 / -1.58 | -0.42 | 0.29 | 0.19 | -0.81 | 0.00 | 456 | NO |
| HO 10 | 15m priorclose(0,1.0) dir=against hold 60m day | 122 | 2 | 0.69 | 0.28 | -0.22 | -0.80 / 1.38 | 0.12 / -0.16 / -0.78 | -0.15 | -0.18 | 0.46 | -0.51 | 0.00 | 202 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 60 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 28 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 4 |
| standalone pair-window Sharpe above own random-entry null p95 | 16 |
| worst-decile corr <= +0.30 | 63 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 9 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m priorclose(0,0.75) dir=with hold 240m day | clean | 0.83 | 1.39 | -136550 | -99985 | 386218 | -193070 | 1.95 | 28.6 | 1.58 | -86254 | 217206 | -115673 |
| BTC 15m priorclose(0,0.75) dir=with hold 240m day | H1 | 1.17 | 1.98 | -170939 | -149535 | 264556 | -229969 | 1.66 | 28.6 | 3.26 | -72216 | 165573 | -78287 |
| BTC 15m priorclose(0,0.75) dir=with hold 240m day | H2 | -0.37 | -0.56 | -90459 | -77094 | 310664 | -94767 | -0.28 | 52.8 | 2.21 | -81937 | 212400 | -82524 |
| BTC 15m priorclose(0,0.75) dir=with hold 240m day | all | 0.71 | 1.18 | -141906 | -109646 | 386218 | -229969 | 2.86 | 33.9 | 1.97 | -84410 | 217206 | -115673 |
| CL 15m priorclose(0,0.75) dir=against hold 240m day | clean | 0.33 | 0.58 | -112538 | -92797 | 495654 | -139751 | 0.61 | 38.1 | 1.49 | -82049 | 284790 | -86608 |
| CL 15m priorclose(0,0.75) dir=against hold 240m day | H1 | -1.25 | -1.52 | -84256 | -74991 | 229681 | -92596 | -0.77 | 50.0 | 2.71 | -84255 | 145427 | -88919 |
| CL 15m priorclose(0,0.75) dir=against hold 240m day | H2 | 1.12 | 1.88 | -146305 | -136208 | 273499 | -155557 | 1.67 | 36.1 | 2.36 | -96026 | 233211 | -101883 |
| CL 15m priorclose(0,0.75) dir=against hold 240m day | all | 0.39 | 0.66 | -125709 | -102348 | 495654 | -155557 | 1.17 | 39.9 | 1.87 | -86093 | 284790 | -101883 |
| ES 15m priorclose(0,0.5) dir=against hold 240m day | clean | 0.78 | 1.22 | -122746 | -105751 | 607581 | -153631 | 1.16 | 38.1 | 1.61 | -84145 | 264327 | -91975 |
| ES 15m priorclose(0,0.5) dir=against hold 240m day | H1 | -1.69 | -2.20 | -128157 | -109781 | 490556 | -183286 | -0.83 | 60.7 | 2.39 | -86939 | 170511 | -89062 |
| ES 15m priorclose(0,0.5) dir=against hold 240m day | H2 | 0.70 | 1.21 | -170077 | -118119 | 335135 | -181462 | 0.86 | 52.8 | 2.57 | -85889 | 210734 | -90312 |
| ES 15m priorclose(0,0.5) dir=against hold 240m day | all | 0.38 | 0.59 | -139990 | -112006 | 647624 | -183286 | 0.91 | 45.2 | 1.94 | -85572 | 264327 | -91975 |
| GC 15m priorclose(0,0.75) dir=against hold 180m all | clean | 0.48 | 0.89 | -102880 | -87576 | 719182 | -172775 | 0.60 | 44.8 | 1.51 | -82770 | 252958 | -98226 |
| GC 15m priorclose(0,0.75) dir=against hold 180m all | H1 | 1.81 | 4.99 | -113408 | -97354 | 459151 | -153845 | 1.58 | 39.3 | 3.48 | -73636 | 171065 | -107702 |
| GC 15m priorclose(0,0.75) dir=against hold 180m all | H2 | 0.41 | 0.55 | -253551 | -217382 | 861894 | -282977 | 0.27 | 30.6 | 2.29 | -106532 | 301080 | -111934 |
| GC 15m priorclose(0,0.75) dir=against hold 180m all | all | 0.72 | 1.20 | -177691 | -133746 | 861894 | -282977 | 1.62 | 40.5 | 1.97 | -92035 | 301080 | -111934 |
| HO 15m priorclose(0,1.0) dir=against hold 60m all | clean | 1.22 | 2.78 | -91972 | -70316 | 304550 | -145694 | 3.62 | 25.7 | 1.69 | -83381 | 266859 | -109007 |
| HO 15m priorclose(0,1.0) dir=against hold 60m all | H1 | 0.15 | 0.27 | -105535 | -91675 | 313419 | -141542 | 0.12 | 46.4 | 2.72 | -81841 | 159355 | -84900 |
| HO 15m priorclose(0,1.0) dir=against hold 60m all | H2 | -0.14 | -0.19 | -622929 | -446139 | 1340079 | -877875 | -0.12 | 36.1 | 1.82 | -144167 | 289188 | -163405 |
| HO 15m priorclose(0,1.0) dir=against hold 60m all | all | 0.35 | 0.49 | -267593 | -173145 | 1340079 | -877875 | 0.73 | 31.5 | 1.88 | -97773 | 289188 | -163405 |
| NQ 5m priorclose(0,0.5) dir=with hold 120m all | clean | 0.47 | 0.66 | -137178 | -114481 | 523172 | -235891 | 0.81 | 44.8 | 1.48 | -85439 | 306913 | -93293 |
| NQ 5m priorclose(0,0.5) dir=with hold 120m all | H1 | 3.81 | 9.52 | -78247 | -72544 | 162395 | -86228 | 5.91 | 28.6 | 3.61 | -62403 | 157663 | -66137 |
| NQ 5m priorclose(0,0.5) dir=with hold 120m all | H2 | 0.98 | 1.47 | -299645 | -237636 | 429004 | -315134 | 1.53 | 36.1 | 2.60 | -80275 | 215406 | -83581 |
| NQ 5m priorclose(0,0.5) dir=with hold 120m all | all | 1.05 | 1.60 | -185650 | -141743 | 523172 | -315134 | 3.90 | 39.9 | 2.04 | -83427 | 306913 | -93293 |
| RTY 15m priorclose(0,0.5) dir=against hold 240m day | clean | 1.50 | 2.83 | -95604 | -82323 | 557680 | -140602 | 2.44 | 40.0 | 1.75 | -81512 | 261101 | -91803 |
| RTY 15m priorclose(0,0.5) dir=against hold 240m day | H1 | 0.17 | 0.27 | -127078 | -105651 | 310055 | -144156 | 0.15 | 50.0 | 2.76 | -78732 | 180224 | -87708 |
| RTY 15m priorclose(0,0.5) dir=against hold 240m day | H2 | 1.38 | 3.29 | -92923 | -82084 | 327553 | -103249 | 1.84 | 44.4 | 2.74 | -89159 | 245415 | -91115 |
| RTY 15m priorclose(0,0.5) dir=against hold 240m day | all | 1.24 | 2.40 | -104350 | -88229 | 557680 | -144156 | 3.60 | 42.9 | 2.13 | -84278 | 261101 | -91803 |
| ZN 5m priorclose(0,1.0) dir=against hold 240m all (diag) | clean | 0.17 | 0.35 | -101129 | -82433 | 479141 | -137657 | 0.33 | 26.7 | 1.43 | -83738 | 288290 | -92951 |
| ZN 5m priorclose(0,1.0) dir=against hold 240m all (diag) | H1 | -0.39 | -0.53 | -109585 | -87543 | 272757 | -153389 | -0.27 | 25.0 | 2.65 | -77610 | 150493 | -78287 |
| ZN 5m priorclose(0,1.0) dir=against hold 240m all (diag) | H2 | -0.51 | -0.67 | -113223 | -93730 | 246011 | -140705 | -0.49 | 27.8 | 2.26 | -81089 | 217425 | -82524 |
| ZN 5m priorclose(0,1.0) dir=against hold 240m all (diag) | all | -0.03 | -0.05 | -109754 | -89211 | 479141 | -153389 | -0.08 | 26.8 | 1.81 | -82543 | 288290 | -92951 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m priorclose(0,0.5) dir=against hold 240m day | -23.4 | 7.5 | 13.9 | 18.5 | 6.8 / 14.6 | 9.4 / 12.0 | NO |
| NQ 5m priorclose(0,0.5) dir=with hold 120m all | -7.2 | -26.0 | 10.5 | 15.6 | -25.9 / 10.6 | 43.9 / 45.3 | NO |
| RTY 15m priorclose(0,0.5) dir=against hold 240m day | -7.6 | 7.8 | 17.5 | 20.3 | 7.1 / 21.2 | 11.9 / 27.8 | NO |
| GC 15m priorclose(0,0.75) dir=against hold 180m all | -14.4 | -29.2 | -0.1 | -14.1 | -4.7 / 20.9 | -27.7 / 11.6 | NO |
| CL 15m priorclose(0,0.75) dir=against hold 240m day | -23.5 | -10.4 | 13.9 | 27.5 | 19.4 / 22.2 | 9.6 / 17.2 | NO |
| ZN 5m priorclose(0,1.0) dir=against hold 240m all (diag) | -30.4 | 5.9 | 23.6 | 15.3 | 5.2 / 20.3 | 30.0 / 30.0 | NO |
| BTC 15m priorclose(0,0.75) dir=with hold 240m day | -17.6 | -35.6 | 18.9 | 34.9 | -36.6 / 13.9 | 30.0 / 32.4 | NO |
| HO 15m priorclose(0,1.0) dir=against hold 60m all | -19.1 | -208.8 | -17.7 | -33.0 | -21.7 / 19.7 | 15.9 / 21.8 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m priorclose(0,0.5) dir=against hold 180m all | negative pre-2023 | 2034 | -12.9 | -42.3 | -28.0 | 29.4 | -0.24 / -0.79 / -0.52 | 108.3 / 78.9 |
| ES 2 5m priorclose(0,1.0) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 984 | 17.3 | -12.0 | 2.4 | 29.4 | 0.26 / -0.18 / 0.04 | 122.2 / 92.8 |
| ES 3 5m priorclose(0,0.75) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 1777 | 22.4 | -7.0 | 7.5 | 29.4 | 0.55 / -0.17 / 0.18 | 76.6 / 47.2 |
| ES 4 5m priorclose(0,0.75) dir=with hold 60m day | positive pre-2023 | 1415 | 36.2 | 6.8 | 21.2 | 29.4 | 0.79 / 0.15 / 0.46 | 89.8 / 60.5 |
| ES 5 15m priorclose(0,0.5) dir=against hold 240m all | negative pre-2023 | 1786 | -11.7 | -41.0 | -26.8 | 29.4 | -0.16 / -0.57 / -0.37 | 139.4 / 110.0 |
| ES 6 5m priorclose(0,1.0) dir=with hold 120m all | positive pre-2023 | 742 | 32.2 | 2.8 | 17.3 | 29.4 | 0.33 / 0.03 / 0.18 | 236.0 / 206.7 |
| ES 7 15m priorclose(0,0.5) dir=against hold 240m day | negative pre-2023 | 1117 | -56.4 | -85.7 | -71.5 | 29.4 | -0.60 / -0.91 / -0.76 | 138.4 / 109.0 |
| ES 8 5m priorclose(0,0.5) dir=against hold 240m all | negative pre-2023 | 2000 | -12.6 | -41.9 | -27.7 | 29.4 | -0.18 / -0.61 / -0.40 | 130.4 / 101.1 |
| ES 9 5m priorclose(0,1.0) dir=with hold 120m day | positive pre-2023 | 597 | 33.0 | 3.6 | 18.0 | 29.4 | 0.35 / 0.04 / 0.19 | 224.3 / 195.0 |
| ES 10 5m priorclose(0,1.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 804 | 25.9 | -3.5 | 10.9 | 29.4 | 0.37 / -0.05 / 0.16 | 84.8 / 55.4 |
| NQ 1 5m priorclose(0,1.0) dir=with hold 120m all | negative pre-2023 | 734 | -20.9 | -35.3 | -26.6 | 14.4 | -0.14 / -0.24 / -0.18 | 391.5 / 377.1 |
| NQ 2 5m priorclose(0,1.0) dir=with hold 120m day | negative pre-2023 | 633 | -35.1 | -49.4 | -40.7 | 14.4 | -0.23 / -0.32 / -0.27 | 393.9 / 379.6 |
| NQ 3 5m priorclose(0,1.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 837 | 1.7 | -12.7 | -4.0 | 14.4 | 0.02 / -0.12 / -0.04 | 192.0 / 177.6 |
| NQ 4 5m priorclose(0,1.0) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 962 | 1.2 | -13.1 | -4.5 | 14.4 | 0.01 / -0.14 / -0.05 | 171.9 / 157.5 |
| NQ 5 15m priorclose(0,0.75) dir=with hold 120m day | positive pre-2023 | 964 | 97.3 | 82.9 | 91.5 | 14.4 | 0.90 / 0.77 / 0.85 | 150.3 / 136.0 |
| NQ 6 15m priorclose(0,0.75) dir=with hold 120m all | positive pre-2023 | 1179 | 63.2 | 48.9 | 57.4 | 14.4 | 0.68 / 0.52 / 0.61 | 129.0 / 114.6 |
| NQ 7 5m priorclose(0,0.5) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 2802 | 9.4 | -5.0 | 3.5 | 14.4 | 0.16 / -0.08 / 0.06 | 64.2 / 49.8 |
| NQ 8 5m priorclose(0,0.75) dir=with hold 120m day | positive pre-2023 | 1135 | 93.9 | 79.5 | 88.1 | 14.4 | 0.92 / 0.78 / 0.87 | 110.5 / 96.1 |
| NQ 9 15m priorclose(0,0.75) dir=with hold 180m all | positive pre-2023 | 975 | 65.1 | 50.7 | 59.3 | 14.4 | 0.55 / 0.43 / 0.50 | 124.7 / 110.4 |
| NQ 10 5m priorclose(0,0.5) dir=with hold 120m day | positive pre-2023 | 2009 | 18.2 | 3.9 | 12.4 | 14.4 | 0.23 / 0.05 / 0.16 | 65.1 / 50.7 |
| RTY 1 15m priorclose(0,0.5) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 792 | 13.6 | -0.7 | 1.5 | 14.4 | 0.20 / -0.01 / 0.02 | 117.5 / 103.1 |
| RTY 2 5m priorclose(0,0.5) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 856 | 4.5 | -9.9 | -7.7 | 14.4 | 0.06 / -0.14 / -0.11 | 111.3 / 97.0 |
| RTY 3 5m priorclose(0,0.5) dir=against hold 180m all | positive pre-2023 | 1358 | 17.7 | 3.4 | 5.7 | 14.4 | 0.40 / 0.08 / 0.13 | 78.6 / 64.2 |
| RTY 4 15m priorclose(0,0.5) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 903 | 6.8 | -7.6 | -5.4 | 14.4 | 0.12 / -0.13 / -0.09 | 90.1 / 75.7 |
| RTY 5 5m priorclose(0,0.5) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 1148 | 13.0 | -1.4 | 0.9 | 14.4 | 0.23 / -0.02 / 0.02 | 85.9 / 71.6 |
| RTY 6 5m priorclose(0,0.5) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 1024 | 13.7 | -0.6 | 1.6 | 14.4 | 0.25 / -0.01 / 0.03 | 89.7 / 75.3 |
| RTY 7 15m priorclose(0,0.75) dir=against hold 240m day | positive pre-2023 | 411 | 56.8 | 42.4 | 44.7 | 14.4 | 0.62 / 0.46 / 0.49 | 151.4 / 137.1 |
| RTY 8 15m priorclose(0,0.5) dir=against hold 60m day | gross-positive, cost-negative pre-2023 | 1372 | 10.4 | -4.0 | -1.7 | 14.4 | 0.37 / -0.15 / -0.06 | 53.4 / 39.1 |
| RTY 9 15m priorclose(0,0.5) dir=against hold 120m day | positive pre-2023 | 1105 | 24.7 | 10.3 | 12.6 | 14.4 | 0.54 / 0.23 / 0.28 | 77.8 / 63.5 |
| RTY 10 15m priorclose(0,0.5) dir=against hold 180m all | positive pre-2023 | 1205 | 21.7 | 7.4 | 9.7 | 14.4 | 0.46 / 0.16 / 0.21 | 71.1 / 56.7 |
| GC 1 5m priorclose(0,0.5) dir=with hold 120m day | positive pre-2023 | 1836 | 31.2 | 6.8 | 16.6 | 24.4 | 0.62 / 0.13 / 0.33 | 82.8 / 58.4 |
| GC 2 5m priorclose(0,0.5) dir=with hold 240m day | positive pre-2023 | 1274 | 35.3 | 10.9 | 20.6 | 24.4 | 0.44 / 0.13 / 0.26 | 100.6 / 76.2 |
| GC 3 5m priorclose(0,0.5) dir=with hold 180m all | negative pre-2023 | 2485 | -2.0 | -26.4 | -16.6 | 24.4 | -0.05 / -0.60 / -0.38 | 64.3 / 39.9 |
| GC 4 15m priorclose(0,0.75) dir=against hold 180m all | negative pre-2023 | 1028 | -2.0 | -26.3 | -16.6 | 24.4 | -0.02 / -0.28 / -0.18 | 78.6 / 54.2 |
| GC 5 15m priorclose(0,0.75) dir=with hold 120m day | positive pre-2023 | 889 | 45.3 | 21.0 | 30.7 | 24.4 | 0.61 / 0.28 / 0.42 | 54.0 / 29.7 |
| GC 6 15m priorclose(0,0.75) dir=with hold 240m day | positive pre-2023 | 652 | 26.3 | 1.9 | 11.6 | 24.4 | 0.24 / 0.02 / 0.11 | 58.6 / 34.2 |
| GC 7 5m priorclose(0,0.75) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 1023 | 12.9 | -11.5 | -1.7 | 24.4 | 0.12 / -0.11 / -0.02 | 43.0 / 18.6 |
| GC 8 (diag) 5m priorclose(0,0.5) dir=with hold 180m day | positive pre-2023 | 1501 | 31.4 | 7.1 | 16.8 | 24.4 | 0.49 / 0.11 / 0.26 | 119.3 / 94.9 |
| GC 9 (diag) 15m priorclose(0,0.5) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 1914 | 3.6 | -20.8 | -11.0 | 24.4 | 0.06 / -0.33 / -0.18 | 88.2 / 63.8 |
| GC 10 (diag) 15m priorclose(0,1.0) dir=with hold 240m day | positive pre-2023 | 359 | 40.1 | 15.7 | 25.4 | 24.4 | 0.27 / 0.11 / 0.17 | 171.4 / 147.0 |
| CL 1 5m priorclose(0,1.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 614 | 7.9 | -16.4 | -13.9 | 24.4 | 0.10 / -0.20 / -0.17 | 66.9 / 42.5 |
| CL 2 15m priorclose(0,0.75) dir=against hold 240m day | negative pre-2023 | 678 | -37.3 | -61.7 | -59.1 | 24.4 | -0.37 / -0.60 / -0.58 | 63.2 / 38.9 |
| CL 3 15m priorclose(0,0.5) dir=against hold 240m all | negative pre-2023 | 1841 | -11.3 | -35.7 | -33.3 | 24.4 | -0.19 / -0.60 / -0.55 | 25.4 / 1.0 |
| CL 4 (diag) 15m priorclose(0,1.0) dir=with hold 180m all | negative pre-2023 | 488 | -67.8 | -92.2 | -89.7 | 24.4 | -0.50 / -0.67 / -0.65 | 145.3 / 120.9 |
| CL 5 (diag) 15m priorclose(0,1.0) dir=with hold 180m day | negative pre-2023 | 402 | -72.2 | -96.6 | -94.2 | 24.4 | -0.48 / -0.65 / -0.63 | 123.0 / 98.7 |
| CL 6 (diag) 15m priorclose(0,1.0) dir=with hold 120m day | negative pre-2023 | 528 | -11.8 | -36.1 | -33.5 | 24.4 | -0.12 / -0.38 / -0.35 | 76.3 / 51.9 |
| ZN 1 (diag) 5m priorclose(0,1.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 474 | 2.7 | -32.9 | -38.2 | 35.6 | 0.07 / -0.82 / -0.94 | 42.3 / 6.7 |
| ZN 2 (diag) 5m priorclose(0,1.0) dir=against hold 180m all | gross-positive, cost-negative pre-2023 | 585 | 15.1 | -20.5 | -25.8 | 35.6 | 0.50 / -0.69 / -0.86 | 32.5 / -3.1 |
| ZN 3 (diag) 5m priorclose(0,0.75) dir=against hold 240m day | negative pre-2023 | 759 | -8.9 | -44.5 | -49.7 | 35.6 | -0.31 / -1.53 / -1.71 | 31.5 / -4.2 |
| BTC 1 15m priorclose(0,1.0) dir=against hold 60m all | negative pre-2023 | 120 | -182.7 | -237.1 | -204.5 | 54.4 | -1.02 / -1.32 / -1.15 | 331.9 / 277.5 |
| BTC 2 15m priorclose(0,1.0) dir=with hold 180m all | positive pre-2023 | 83 | 166.9 | 112.5 | 145.3 | 54.4 | 0.46 / 0.31 / 0.40 | 614.6 / 560.3 |
| BTC 3 15m priorclose(0,0.75) dir=with hold 240m day | positive pre-2023 | 57 | 679.8 | 625.5 | 657.1 | 54.4 | 1.06 / 0.98 / 1.02 | 628.8 / 574.4 |
| BTC 4 15m priorclose(0,1.0) dir=against hold 60m day | negative pre-2023 | 79 | -257.0 | -311.3 | -278.8 | 54.4 | -1.42 / -1.71 / -1.54 | 290.9 / 236.5 |
| BTC 5 5m priorclose(0,0.75) dir=against hold 180m day | negative pre-2023 | 97 | -499.5 | -553.8 | -521.8 | 54.4 | -1.50 / -1.64 / -1.56 | 442.1 / 387.8 |
| BTC 6 5m priorclose(0,0.75) dir=against hold 60m day | gross-positive, cost-negative pre-2023 | 160 | 6.2 | -48.1 | -16.1 | 54.4 | 0.04 / -0.30 / -0.10 | 229.6 / 175.2 |
| BTC 7 15m priorclose(0,0.75) dir=against hold 60m day | negative pre-2023 | 125 | -69.8 | -124.2 | -92.0 | 54.4 | -0.34 / -0.60 / -0.45 | 264.5 / 210.1 |
| BTC 8 15m priorclose(0,0.75) dir=against hold 60m all | negative pre-2023 | 223 | -38.0 | -92.4 | -60.1 | 54.4 | -0.27 / -0.65 / -0.42 | 183.2 / 128.9 |
| BTC 9 5m priorclose(0,0.75) dir=against hold 120m day | negative pre-2023 | 128 | -194.9 | -249.3 | -217.3 | 54.4 | -0.65 / -0.83 / -0.72 | 261.1 / 206.7 |
| BTC 10 5m priorclose(0,0.5) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 396 | 41.7 | -12.7 | 19.2 | 54.4 | 0.25 / -0.08 / 0.11 | 113.3 / 58.9 |
| HO 1 5m priorclose(0,0.75) dir=against hold 180m all | positive pre-2023 | 1207 | 24.1 | 11.3 | 12.7 | 12.8 | 0.23 / 0.11 / 0.12 | 137.2 / 124.5 |
| HO 2 15m priorclose(0,1.0) dir=against hold 60m all | positive pre-2023 | 790 | 14.3 | 1.6 | 3.0 | 12.8 | 0.19 / 0.02 / 0.04 | 100.1 / 87.3 |
| HO 3 5m priorclose(0,1.0) dir=against hold 120m all | positive pre-2023 | 787 | 24.0 | 11.2 | 12.7 | 12.8 | 0.20 / 0.10 / 0.11 | 123.2 / 110.5 |
| HO 4 5m priorclose(0,0.75) dir=against hold 180m day | positive pre-2023 | 980 | 32.6 | 19.8 | 21.1 | 12.8 | 0.31 / 0.19 / 0.20 | 126.0 / 113.3 |
| HO 5 5m priorclose(0,0.75) dir=against hold 120m all | gross-positive, cost-negative pre-2023 | 1520 | 11.4 | -1.3 | -0.0 | 12.8 | 0.14 / -0.02 / -0.00 | 83.0 / 70.3 |
| HO 6 15m priorclose(0,0.75) dir=against hold 240m day | negative pre-2023 | 731 | -3.5 | -16.2 | -14.8 | 12.8 | -0.03 / -0.12 / -0.11 | 148.6 / 135.8 |
| HO 7 15m priorclose(0,0.75) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 840 | 5.4 | -7.4 | -6.0 | 12.8 | 0.05 / -0.06 / -0.05 | 95.7 / 82.9 |
| HO 8 15m priorclose(0,1.0) dir=against hold 120m all | positive pre-2023 | 680 | 31.3 | 18.5 | 20.1 | 12.8 | 0.28 / 0.17 / 0.18 | 94.2 / 81.4 |
| HO 9 15m priorclose(0,0.75) dir=against hold 120m all | gross-positive, cost-negative pre-2023 | 1297 | 7.3 | -5.5 | -4.2 | 12.8 | 0.08 / -0.06 / -0.05 | 68.2 / 55.4 |
| HO 10 15m priorclose(0,1.0) dir=against hold 60m day | positive pre-2023 | 661 | 33.2 | 20.5 | 21.9 | 12.8 | 0.45 / 0.28 / 0.29 | 71.0 / 58.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 15 cells pass the clean rule against a replicate mean of 15.5 (p(count) = 0.58, p(top) = 0.90); CL: 3 cells pass the clean rule against a replicate mean of 6.7 (p(count) = 0.96, p(top) = 0.97); ES: 20 cells pass the clean rule against a replicate mean of 9.1 (p(count) = 0.01, p(top) = 0.07); GC: 7 cells pass the clean rule against a replicate mean of 10.6 (p(count) = 0.91, p(top) = 0.97); HO: 21 cells pass the clean rule against a replicate mean of 15.6 (p(count) = 0.07, p(top) = 0.49); NQ: 14 cells pass the clean rule against a replicate mean of 19.1 (p(count) = 0.95, p(top) = 0.99); RTY: 22 cells pass the clean rule against a replicate mean of 11.8 (p(count) = 0.01, p(top) = 0.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00).
- Of 60 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.28 (RTY 15m priorclose(0,0.5) dir=against hold 240m day); bootstrap lower bound > 0 for 4 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 9; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell RTY 15m priorclose(0,0.75) dir=against hold 240m day: uplift +0.13/+0.29/+0.14, boot lo -0.01, plateau 0.25, 2x-slip +0.13, wd corr -0.55, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 24, 'gross-positive, cost-negative pre-2023': 19, 'negative pre-2023': 17}.

- **Manual review: RTY prior-close-distance fade (15-minute bars; price at least 0.75 x ADR20 away from the prior trading day's close; trade AGAINST the distance; hold 240 minutes; day session; no stop).** Standalone Sharpe 1.19 / 1.59 / 0.86 on clean / H1 / H2 (out-of-selection 1.21 against null p95 1.25: a hair under); uplift at 20% share +0.13 / +0.29 / +0.14; worst-decile correlation -0.55 (17 weeks); worst week +8.3% at 20%; bootstrap lower bound -0.01 (fails by 0.01); plateau 0.25; 2x slippage +0.13; ERA flag POSITIVE pre-2023 (RTY 2017-22 net weekly Sharpe +0.46). Its 0.5-ADR sibling (best all-in uplift +0.28; bootstrap lower bound +0.07) has +0.29 / -0.07 / +0.44. Replication (amendment 2): 2 of 4 hold - cross-instrument ES +0.15 (>= 50% of RTY's +0.15), alternating months odd +0.20 / even +0.09 against +0.15 (even half 56%); H0 2023-02..07 standalone Sharpe 0.00 on 37 trades (fails); live weeks N/A. The same cell run on other markets (no selection on them; all-in uplift at 20%): ES +0.15, YM +0.12, GC +0.16, CL +0.02, HO -0.05, NQ -0.03, ZN -0.19, BTC -0.23: positive on four of the five US-index/gold markets. Sizing: 62.9 RTY contracts at 100% of pair volatility, 12.6 at 20% share (because the RTY point value is $50 and the sleeve has to match the pair's volatility); worst single trade -$3.3k per contract, about -$41k at 12.6 contracts, no stop. Verdict LEAD (gate 3, replication 2 of 4, bootstrap and OOS null just missed, plateau fails). Because ES, YM and GC independently show the same sign, an equal-risk ensemble across the family is pre-registered and run as Q20-ENS (REPORT_Q20_ENS.md; its neighbourhood is NOT independent evidence for the RTY cell).

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q20.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q20/ (`Q20_CO_all_selected_scored.csv`).

DONE Q20
