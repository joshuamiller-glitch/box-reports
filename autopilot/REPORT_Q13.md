# REPORT Q13 - Q13: N consecutive same-direction closes, with/against, time exit

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 56 selected cells (+12 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.23; best pair-window standalone Sharpe +1.09.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: N consecutive same-direction closes, with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        12 |               1.824 |                2 |         10 |            0 |
| CL    |      96 |         96 |         6 |               1.178 |                2 |          6 |            3 |
| ES    |      96 |         96 |         9 |               1.007 |                2 |          9 |            1 |
| GC    |      96 |         96 |         3 |               0.824 |                2 |          3 |            3 |
| HO    |      96 |         96 |        13 |               1.896 |                2 |         10 |            0 |
| NQ    |      96 |         96 |        14 |               1.092 |                2 |         10 |            0 |
| RTY   |      96 |         96 |         8 |               1.657 |                2 |          8 |            2 |
| ZN    |      96 |         96 |         0 |              -1.133 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    9 |            4.6   |              10 |      0.035 |                       0.575 |            0.628 |           0.931 |    0.64  |       1.007 |                1.618 |
| NQ    |     200 |                   14 |           14.58  |              24 |      0.64  |                       0.641 |            0.858 |           1.126 |    0.915 |       1.092 |                2.024 |
| RTY   |     200 |                    8 |            6.14  |              12 |      0.26  |                       1.248 |            0.634 |           0.892 |    0     |       1.657 |                1.79  |
| GC    |     200 |                    3 |            4.885 |              11 |      0.885 |                       0.336 |            0.616 |           0.967 |    0.935 |       0.363 |                1.739 |
| CL    |     200 |                    6 |            2.8   |               7 |      0.06  |                       0.695 |            0.603 |           1.027 |    0.275 |       1.178 |                1.535 |
| ZN    |     200 |                    0 |            0.025 |               1 |      1     |                     nan     |            0.395 |           0.597 |  nan     |     nan     |                0.597 |
| BTC   |     200 |                   12 |           10.41  |              18 |      0.31  |                       0.899 |            0.739 |           1     |    0.16  |       1.824 |                2.054 |
| HO    |     200 |                   13 |            9.76  |              18 |      0.205 |                       1.101 |            0.725 |           1.002 |    0.02  |       1.896 |                1.977 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m run(4,0) dir=with hold 240m day | 386 | 2 | 1.01 | -0.38 | 0.60 | -0.14 / 1.26 | 0.14 / 0.36 / -0.26 | 0.02 | 0.01 | 0.94 | -0.11 | 0.00 | 611 | NO |
| ES 2 | 5m run(5,0) dir=with hold 120m day | 724 | 2 | 0.93 | -0.36 | 0.22 | -0.75 / 0.83 | 0.05 / -0.46 / -0.18 | -0.17 | 0.38 | 0.93 | -0.27 | 0.00 | 1189 | NO |
| ES 3 | 5m run(5,0) dir=with hold 180m all | 1511 | 2 | 0.85 | -0.79 | -0.28 | -1.53 / 0.75 | 0.10 / -0.84 / -0.37 | -0.30 | -0.15 | 0.80 | -0.36 | 0.00 | 2515 | NO |
| ES 4 | 5m run(4,0) dir=with hold 240m all | 1835 | 2 | 0.74 | -1.18 | -0.41 | -1.85 / 0.88 | 0.05 / -1.01 / -0.35 | -0.35 | -0.01 | 0.71 | -0.38 | 0.00 | 2992 | NO |
| ES 5 | 5m run(4,0) dir=with hold 240m day | 557 | 2 | 0.43 | -0.56 | 0.13 | -0.14 / 1.04 | -0.06 / -0.28 / -0.01 | -0.15 | 0.01 | 0.82 | -0.28 | 0.00 | 906 | NO |
| ES 6 | 15m run(3,0) dir=with hold 240m day | 510 | 2 | 0.40 | -0.80 | -0.40 | -1.30 / 1.08 | 0.04 / -0.30 / -0.74 | -0.24 | 0.09 | 0.41 | -0.40 | 0.00 | 816 | NO |
| ES 7 | 5m run(5,0) dir=with hold 180m day | 550 | 2 | 0.39 | -0.22 | 0.28 | 0.21 / 1.25 | 0.00 / -0.34 / 0.12 | -0.08 | -0.17 | 0.87 | -0.21 | 0.00 | 904 | NO |
| ES 8 | 5m run(3,0) dir=with hold 120m day | 1487 | 2 | 0.23 | -1.74 | -0.55 | -1.66 / 0.58 | -0.01 / -1.10 / 0.00 | -0.29 | -0.11 | 0.66 | -0.36 | 0.00 | 2385 | NO |
| ES 9 | 15m run(4,0) dir=with hold 60m day | 854 | 2 | 0.20 | -0.62 | -0.38 | -1.55 / 0.48 | -0.04 / 0.11 / -0.60 | -0.27 | 0.18 | 0.83 | -0.31 | 0.00 | 1338 | NO |
| ES 10 (diag) | 5m run(3,0) dir=with hold 240m day | 729 | 1 | 0.71 | -0.93 | 0.16 | -0.58 / 0.96 | 0.06 / -0.61 / 0.07 | -0.10 | -0.46 | 0.80 | -0.21 | 0.00 | 1176 | diag |
| NQ 1 | 5m run(3,0) dir=with hold 240m all | 2408 | 2 | 1.09 | -0.96 | 1.09 | 1.08 / 1.16 | 0.11 / -0.13 / 0.35 | 0.10 | -0.02 | 1.00 | -0.06 | 0.00 | 3862 | NO |
| NQ 2 | 5m run(5,0) dir=with hold 60m day | 1080 | 2 | 0.85 | 0.58 | 0.07 | -1.20 / 1.22 | 0.05 / -0.48 / -0.31 | -0.13 | 0.28 | 0.74 | -0.28 | 0.00 | 1744 | NO |
| NQ 3 | 15m run(4,0) dir=with hold 180m day | 530 | 2 | 0.84 | -0.34 | 0.79 | 0.66 / 1.65 | 0.08 / 0.10 / 0.04 | 0.06 | -0.48 | 0.97 | -0.10 | 0.00 | 821 | NO |
| NQ 4 | 15m run(3,0) dir=with hold 180m day | 786 | 2 | 0.68 | 0.14 | 0.27 | -0.31 / 1.61 | 0.06 / 0.07 / -0.15 | -0.02 | -0.56 | 0.74 | -0.19 | 0.00 | 1252 | NO |
| NQ 5 | 15m run(5,0) dir=with hold 240m day | 255 | 2 | 0.62 | -0.01 | 0.84 | 1.15 / 1.59 | 0.06 / 0.29 / 0.16 | 0.10 | -0.07 | 0.95 | -0.05 | 0.00 | 406 | NO |
| NQ 6 | 15m run(5,0) dir=against hold 60m all | 1261 | 2 | 0.56 | -1.18 | -0.05 | -1.04 / 1.46 | 0.14 / -0.46 / -0.36 | -0.10 | 0.10 | 0.62 | -0.25 | 0.00 | 2030 | NO |
| NQ 7 | 15m run(4,0) dir=with hold 240m day | 397 | 2 | 0.48 | -0.39 | 0.45 | 0.35 / 1.43 | 0.01 / -0.05 / 0.10 | -0.00 | -0.16 | 0.81 | -0.16 | 0.50 | 623 | NO |
| NQ 8 | 15m run(4,0) dir=with hold 120m day | 682 | 2 | 0.48 | -0.19 | 0.87 | 1.50 / 1.03 | 0.00 / 0.20 / 0.23 | 0.05 | -0.21 | 0.96 | -0.09 | 0.50 | 1064 | NO |
| NQ 9 | 5m run(5,0) dir=with hold 120m day | 824 | 2 | 0.42 | 0.74 | -0.51 | -1.49 / 1.68 | -0.03 / -1.00 / -0.39 | -0.27 | 0.34 | 0.26 | -0.49 | 0.00 | 1328 | NO |
| NQ 10 | 5m run(4,0) dir=against hold 180m day | 878 | 2 | 0.39 | -0.74 | 0.52 | 0.63 / 1.05 | 0.06 / 0.15 / -0.03 | 0.04 | 0.40 | 0.88 | -0.12 | 0.50 | 1412 | NO |
| RTY 1 | 15m run(5,0) dir=against hold 180m all | 876 | 2 | 1.66 | 0.03 | 0.94 | 0.01 / 1.10 | 0.22 / -0.49 / 0.34 | 0.06 | 0.07 | 1.00 | -0.06 | 0.50 | 1415 | NO |
| RTY 2 | 15m run(4,0) dir=against hold 180m day | 483 | 2 | 1.55 | 0.35 | 1.00 | 0.08 / 1.05 | 0.25 / -0.55 / 0.23 | 0.09 | -0.13 | 1.00 | -0.05 | 0.50 | 759 | NO |
| RTY 3 | 15m run(4,0) dir=against hold 240m day | 381 | 2 | 1.50 | 0.23 | 0.90 | -0.09 / 1.11 | 0.27 / -0.47 / 0.08 | 0.10 | -0.33 | 0.98 | -0.04 | 1.00 | 601 | NO |
| RTY 4 | 15m run(5,0) dir=against hold 180m day | 296 | 2 | 1.32 | 0.00 | 0.99 | 0.35 / 1.39 | 0.19 / -0.25 / 0.27 | 0.11 | -0.24 | 0.97 | -0.02 | 1.00 | 469 | NO |
| RTY 5 | 15m run(5,0) dir=against hold 120m all | 992 | 2 | 1.19 | -0.66 | 0.09 | -1.55 / 0.84 | 0.14 / -0.69 / -0.15 | -0.13 | 0.24 | 0.90 | -0.24 | 0.00 | 1594 | NO |
| RTY 6 | 15m run(5,0) dir=against hold 120m day | 365 | 2 | 1.02 | -0.13 | 0.39 | -0.69 / 1.01 | 0.13 / -0.43 / 0.02 | -0.02 | 0.11 | 0.93 | -0.15 | 0.50 | 573 | NO |
| RTY 7 | 15m run(5,0) dir=against hold 240m day | 246 | 2 | 1.00 | -0.10 | 0.85 | 0.53 / 1.52 | 0.18 / -0.14 / 0.27 | 0.13 | -0.49 | 0.94 | -0.02 | 0.50 | 375 | NO |
| RTY 8 | 15m run(5,0) dir=against hold 240m all | 785 | 2 | 0.74 | 0.09 | 0.93 | 1.21 / 0.96 | 0.09 / 0.13 / 0.48 | 0.11 | -0.12 | 1.00 | -0.02 | 0.50 | 1249 | LEAD |
| RTY 9 (diag) | 15m run(4,0) dir=against hold 120m day | 640 | 1 | 1.48 | 0.40 | 0.34 | -1.06 / 1.09 | 0.24 / -0.89 / -0.13 | -0.06 | -0.30 | 0.93 | -0.21 | 0.00 | 999 | diag |
| RTY 10 (diag) | 15m run(4,0) dir=against hold 120m all | 1838 | 1 | 0.63 | -0.13 | -0.47 | -1.65 / 0.82 | 0.11 / -1.11 / -0.37 | -0.33 | 0.11 | 0.80 | -0.42 | 0.00 | 2916 | diag |
| GC 1 | 15m run(4,0) dir=with hold 240m day | 389 | 2 | 0.36 | -0.10 | 0.07 | -0.14 / 1.69 | 0.00 / -0.06 / -0.70 | -0.20 | 0.64 | 0.64 | -0.47 | 0.00 | 616 | NO |
| GC 2 | 5m run(4,0) dir=against hold 240m all | 1930 | 2 | 0.36 | -1.35 | -0.07 | -0.27 / 1.02 | 0.06 / -1.45 / 0.02 | -0.28 | 0.41 | 0.70 | -0.54 | 0.00 | 3125 | NO |
| GC 3 | 15m run(5,0) dir=with hold 180m day | 285 | 2 | 0.29 | -0.28 | -0.03 | -0.17 / 1.27 | 0.00 / -0.97 / -0.26 | -0.22 | 0.30 | 0.69 | -0.61 | 0.00 | 456 | NO |
| GC 4 (diag) | 5m run(3,0) dir=with hold 240m all | 2341 | 1 | 0.82 | -1.32 | 0.32 | -0.00 / 1.26 | 0.11 / 1.00 / -0.81 | -0.09 | 0.17 | 0.87 | -0.25 | 0.50 | 3765 | diag |
| GC 5 (diag) | 5m run(3,0) dir=with hold 240m day | 760 | 1 | 0.64 | -0.62 | -0.20 | -0.74 / 1.43 | 0.07 / -0.02 / -1.05 | -0.27 | -0.06 | 0.52 | -0.56 | 0.00 | 1225 | diag |
| GC 6 (diag) | 15m run(3,0) dir=with hold 180m all | 2260 | 1 | 0.47 | -1.45 | -0.19 | -0.59 / 0.96 | 0.03 / -0.95 / -0.60 | -0.37 | -0.17 | 0.70 | -0.64 | 0.00 | 3670 | diag |
| CL 1 | 15m run(5,0) dir=against hold 240m all | 730 | 2 | 1.18 | -0.33 | 0.38 | -0.09 / 0.92 | 0.16 / -0.04 / -0.37 | -0.09 | -0.14 | 0.90 | -0.25 | 0.50 | 1163 | NO |
| CL 2 | 15m run(5,0) dir=against hold 180m all | 832 | 2 | 1.10 | -0.72 | 0.11 | -0.58 / 0.72 | 0.16 / -0.25 / -0.59 | -0.20 | 0.02 | 0.91 | -0.33 | 0.00 | 1336 | NO |
| CL 3 | 5m run(4,0) dir=against hold 240m all | 1781 | 2 | 0.78 | -0.92 | 0.64 | 0.60 / 1.05 | 0.14 / -0.41 / 0.03 | -0.12 | 0.36 | 1.00 | -0.18 | 0.00 | 2892 | NO |
| CL 4 | 5m run(5,0) dir=against hold 180m day | 554 | 2 | 0.63 | -0.77 | -0.39 | -1.30 / 1.16 | 0.11 / -0.08 / -0.98 | -0.28 | 0.14 | 0.59 | -0.44 | 0.00 | 905 | NO |
| CL 5 | 5m run(3,0) dir=against hold 120m day | 1500 | 2 | 0.35 | -1.15 | -0.23 | -0.80 / 0.74 | 0.07 / -0.25 / -0.28 | -0.22 | 0.08 | 0.88 | -0.28 | 0.00 | 2402 | NO |
| CL 6 | 5m run(5,0) dir=against hold 120m day | 737 | 2 | 0.14 | -0.81 | -0.21 | -0.55 / 0.76 | 0.04 / -0.00 / -0.40 | -0.22 | -0.11 | 0.80 | -0.33 | 0.00 | 1192 | NO |
| CL 7 (diag) | 15m run(5,0) dir=against hold 180m day | 295 | 1 | 1.09 | -0.61 | 0.61 | 0.42 / 1.09 | 0.15 / -0.08 / 0.19 | 0.05 | -0.02 | 0.99 | -0.11 | 0.00 | 463 | diag |
| CL 8 (diag) | 15m run(5,0) dir=against hold 240m day | 237 | 1 | 0.98 | -0.47 | 0.69 | 0.47 / 1.52 | 0.15 / 0.14 / 0.24 | 0.11 | -0.28 | 0.92 | -0.05 | 0.50 | 367 | diag |
| CL 9 (diag) | 5m run(4,0) dir=against hold 240m day | 566 | 1 | 0.75 | -0.64 | 0.05 | -0.68 / 1.28 | 0.10 / -0.13 / -0.43 | -0.13 | -0.01 | 0.73 | -0.26 | 0.00 | 913 | diag |
| ZN 1 (diag) | 5m run(5,0) dir=with hold 240m day | 201 | 0 | -1.13 | -0.97 | -1.06 | -0.71 / -0.99 | -0.21 / -0.25 / -0.13 | -0.43 | -0.23 | 0.99 | -0.36 | 0.00 | 294 | diag |
| ZN 2 (diag) | 15m run(5,0) dir=with hold 240m day | 143 | 0 | -1.24 | -0.96 | -1.40 | -2.28 / -0.81 | -0.28 / -0.32 / -0.23 | -0.47 | -0.06 | 0.72 | -0.45 | 0.00 | 210 | diag |
| ZN 3 (diag) | 15m run(4,0) dir=against hold 240m day | 287 | 0 | -1.30 | -2.17 | -1.51 | -2.10 / -1.77 | -0.25 / -0.30 / -0.24 | -0.55 | -0.29 | 0.95 | -0.43 | 0.00 | 430 | diag |
| BTC 1 | 15m run(4,0) dir=with hold 180m day | 468 | 2 | 1.82 | 0.07 | 0.52 | -1.20 / 1.09 | 0.31 / -0.64 / -0.24 | 0.02 | 0.24 | 0.93 | -0.14 | 0.00 | 725 | NO |
| BTC 2 | 15m run(5,0) dir=with hold 180m day | 263 | 2 | 1.42 | 0.31 | 0.16 | -1.64 / 1.62 | 0.32 / -0.73 / -0.35 | 0.00 | 0.17 | 0.61 | -0.19 | 0.50 | 407 | NO |
| BTC 3 | 15m run(4,0) dir=with hold 240m day | 369 | 2 | 1.24 | -0.20 | 0.20 | -1.20 / 1.57 | 0.21 / -0.54 / -0.31 | -0.03 | 0.30 | 0.67 | -0.20 | 0.00 | 568 | NO |
| BTC 4 | 15m run(4,0) dir=with hold 240m all | 1172 | 2 | 0.92 | -0.72 | 0.08 | -1.22 / 1.13 | 0.15 / -0.07 / -0.43 | -0.07 | 0.05 | 0.79 | -0.21 | 0.00 | 1834 | NO |
| BTC 5 | 15m run(4,0) dir=with hold 120m day | 595 | 2 | 0.77 | 0.44 | -0.03 | -1.26 / 1.18 | 0.10 / -0.28 / -0.20 | -0.07 | -0.04 | 0.71 | -0.20 | 0.00 | 929 | NO |
| BTC 6 | 15m run(4,0) dir=with hold 180m all | 1382 | 2 | 0.73 | -0.59 | -0.18 | -1.42 / 1.25 | 0.11 / -0.42 / -0.35 | -0.14 | -0.11 | 0.58 | -0.27 | 0.00 | 2153 | NO |
| BTC 7 | 15m run(5,0) dir=with hold 120m day | 318 | 2 | 0.71 | 0.82 | 0.02 | -0.77 / 1.16 | 0.13 / -0.49 / -0.27 | -0.07 | -0.08 | 0.72 | -0.25 | 0.00 | 489 | NO |
| BTC 8 | 15m run(5,0) dir=with hold 120m all | 845 | 2 | 0.69 | 0.40 | -0.13 | -0.95 / 1.13 | 0.14 / -0.25 / -0.53 | -0.12 | 0.20 | 0.63 | -0.28 | 0.00 | 1335 | NO |
| BTC 9 | 5m run(4,0) dir=with hold 240m all | 1824 | 2 | 0.48 | 0.41 | 0.27 | -0.13 / 1.02 | 0.05 / 0.14 / -0.22 | -0.06 | 0.26 | 0.88 | -0.18 | 0.00 | 2872 | NO |
| BTC 10 | 5m run(3,0) dir=with hold 180m all | 2876 | 2 | 0.18 | -1.07 | -0.58 | -1.84 / 0.91 | -0.04 / 0.01 / -0.60 | -0.26 | 0.35 | 0.36 | -0.36 | 0.00 | 4535 | NO |
| HO 1 | 15m run(5,0) dir=against hold 240m day | 255 | 2 | 1.90 | -0.40 | 0.43 | -0.98 / 1.18 | 0.42 / 0.18 / -0.79 | 0.10 | -0.16 | 0.83 | -0.14 | 1.00 | 411 | NO |
| HO 2 | 15m run(5,0) dir=against hold 180m day | 308 | 2 | 1.85 | -0.28 | 0.91 | -0.13 / 1.38 | 0.39 / 0.14 / -0.20 | 0.21 | -0.30 | 0.95 | -0.00 | 0.00 | 502 | NO |
| HO 3 | 5m run(5,0) dir=against hold 180m day | 599 | 2 | 1.29 | 0.09 | 0.05 | -0.93 / 1.16 | 0.20 / -0.60 / -0.56 | -0.12 | 0.00 | 0.64 | -0.34 | 0.00 | 968 | NO |
| HO 4 | 5m run(5,0) dir=against hold 240m day | 470 | 2 | 1.18 | 0.13 | -0.45 | -2.08 / 1.24 | 0.17 / -0.27 / -1.11 | -0.22 | 0.01 | 0.21 | -0.43 | 0.00 | 747 | NO |
| HO 5 | 15m run(3,0) dir=against hold 240m day | 521 | 2 | 0.87 | -0.51 | 0.39 | 0.14 / 0.97 | 0.14 / 0.24 / -0.21 | 0.05 | -0.42 | 0.92 | -0.21 | 1.00 | 839 | NO |
| HO 6 | 15m run(4,0) dir=against hold 180m day | 508 | 2 | 0.85 | 0.20 | 0.59 | 0.50 / 1.33 | 0.18 / 0.25 / -0.13 | 0.11 | -0.36 | 0.90 | -0.20 | 0.00 | 836 | NO |
| HO 7 | 15m run(4,0) dir=against hold 240m day | 399 | 2 | 0.80 | -0.10 | 0.15 | -0.25 / 1.05 | 0.19 / 0.53 / -0.87 | -0.04 | -0.14 | 0.71 | -0.36 | 0.00 | 650 | NO |
| HO 8 | 15m run(5,0) dir=against hold 240m all | 753 | 2 | 0.79 | -0.57 | -0.30 | -1.23 / 1.64 | 0.23 / 0.19 / -1.11 | -0.12 | 0.32 | 0.44 | -0.36 | 0.00 | 1192 | NO |
| HO 9 | 15m run(3,0) dir=against hold 180m day | 764 | 2 | 0.76 | -0.56 | 0.97 | 1.19 / 1.26 | 0.11 / 0.05 / 0.33 | 0.13 | -0.21 | 0.98 | -0.09 | 0.00 | 1227 | NO |
| HO 10 | 15m run(5,0) dir=against hold 180m all | 851 | 2 | 0.75 | -0.43 | -0.35 | -1.26 / 1.35 | 0.19 / -0.03 / -1.02 | -0.16 | 0.07 | 0.38 | -0.40 | 0.00 | 1360 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 56 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 1 / 0 |
| all-in uplift @20% > 0 (all scored) | 27 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 15 |
| worst-decile corr <= +0.30 | 59 |
| plateau >= 0.75 | 4 |
| all-in uplift at 2x slippage >= +0.10 | 8 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m run(4,0) dir=with hold 180m day | clean | 1.70 | 2.78 | -126414 | -106065 | 346578 | -140089 | 4.51 | 38.1 | 1.77 | -80817 | 230234 | -100297 |
| BTC 15m run(4,0) dir=with hold 180m day | H1 | -1.92 | -2.28 | -166812 | -157115 | 709903 | -185190 | -0.87 | 57.1 | 2.18 | -87358 | 169821 | -97054 |
| BTC 15m run(4,0) dir=with hold 180m day | H2 | -0.44 | -0.66 | -108055 | -92709 | 651545 | -121504 | -0.20 | 52.8 | 2.25 | -96097 | 234008 | -106825 |
| BTC 15m run(4,0) dir=with hold 180m day | all | 0.52 | 0.76 | -143693 | -123932 | 881109 | -185190 | 0.93 | 44.0 | 1.95 | -87499 | 234008 | -106825 |
| CL 5m run(4,0) dir=against hold 240m all | clean | 0.76 | 1.32 | -108257 | -89868 | 510189 | -143667 | 1.36 | 49.5 | 1.60 | -86621 | 271181 | -108601 |
| CL 5m run(4,0) dir=against hold 240m all | H1 | -3.22 | -3.55 | -58117 | -57543 | 441333 | -58626 | -0.98 | 75.0 | 2.42 | -82965 | 148591 | -87354 |
| CL 5m run(4,0) dir=against hold 240m all | H2 | 1.34 | 2.61 | -237771 | -208124 | 915679 | -290489 | 1.23 | 47.2 | 2.52 | -114179 | 226697 | -137751 |
| CL 5m run(4,0) dir=against hold 240m all | all | 0.64 | 1.17 | -163713 | -129534 | 915679 | -290489 | 1.51 | 53.0 | 1.95 | -94669 | 271181 | -137751 |
| ES 15m run(4,0) dir=with hold 240m day | clean | 1.07 | 1.91 | -108789 | -90587 | 348690 | -158432 | 2.80 | 41.0 | 1.60 | -84198 | 245292 | -108997 |
| ES 15m run(4,0) dir=with hold 240m day | H1 | 0.84 | 1.08 | -190779 | -158904 | 393350 | -246863 | 0.61 | 28.6 | 3.19 | -70913 | 145656 | -80181 |
| ES 15m run(4,0) dir=with hold 240m day | H2 | -1.06 | -1.35 | -134915 | -111043 | 564355 | -138046 | -0.57 | 55.6 | 2.04 | -89246 | 220361 | -91582 |
| ES 15m run(4,0) dir=with hold 240m day | all | 0.60 | 0.90 | -138213 | -110210 | 564355 | -246863 | 1.59 | 42.3 | 1.92 | -85011 | 245292 | -108997 |
| GC 5m run(4,0) dir=against hold 240m all | clean | 0.29 | 0.45 | -122225 | -105114 | 672011 | -181469 | 0.39 | 52.4 | 1.52 | -80210 | 255925 | -85906 |
| GC 5m run(4,0) dir=against hold 240m all | H1 | -1.84 | -2.09 | -382982 | -341884 | 2085178 | -498728 | -0.55 | 53.6 | 1.37 | -148349 | 239294 | -178033 |
| GC 5m run(4,0) dir=against hold 240m all | H2 | 0.57 | 0.87 | -418713 | -350752 | 1194180 | -425004 | 0.54 | 44.4 | 2.50 | -116499 | 268703 | -137570 |
| GC 5m run(4,0) dir=against hold 240m all | all | -0.07 | -0.10 | -327986 | -257108 | 2242024 | -498728 | -0.10 | 50.6 | 1.74 | -104030 | 268703 | -178033 |
| HO 15m run(5,0) dir=against hold 180m day | clean | 1.88 | 4.32 | -89530 | -72834 | 262854 | -107376 | 6.49 | 42.9 | 1.85 | -79714 | 245816 | -83344 |
| HO 15m run(5,0) dir=against hold 180m day | H1 | 1.39 | 2.05 | -73955 | -73059 | 306383 | -75810 | 0.69 | 32.1 | 2.97 | -69192 | 152161 | -71895 |
| HO 15m run(5,0) dir=against hold 180m day | H2 | -0.54 | -0.69 | -292818 | -233931 | 852828 | -331754 | -0.37 | 50.0 | 2.28 | -98874 | 230058 | -107081 |
| HO 15m run(5,0) dir=against hold 180m day | all | 0.91 | 1.40 | -168338 | -126785 | 852828 | -331754 | 1.87 | 42.9 | 2.13 | -83791 | 245816 | -107081 |
| NQ 5m run(3,0) dir=with hold 240m all | clean | 1.12 | 2.11 | -100009 | -85977 | 343767 | -119385 | 2.95 | 45.7 | 1.57 | -88915 | 281968 | -97252 |
| NQ 5m run(3,0) dir=with hold 240m all | H1 | 0.47 | 0.81 | -154995 | -130184 | 479783 | -216180 | 0.35 | 53.6 | 2.70 | -89567 | 171934 | -91504 |
| NQ 5m run(3,0) dir=with hold 240m all | H2 | 1.53 | 2.38 | -162931 | -147001 | 363995 | -179812 | 1.94 | 30.6 | 2.65 | -67759 | 198880 | -69650 |
| NQ 5m run(3,0) dir=with hold 240m all | all | 1.09 | 1.85 | -139485 | -115984 | 479783 | -216180 | 3.94 | 44.0 | 1.99 | -88136 | 281968 | -97252 |
| RTY 15m run(5,0) dir=against hold 240m all | clean | 0.72 | 1.09 | -128220 | -104648 | 454157 | -218321 | 1.45 | 43.8 | 1.55 | -91446 | 275016 | -104910 |
| RTY 15m run(5,0) dir=against hold 240m all | H1 | 0.88 | 1.65 | -99245 | -94408 | 236815 | -105823 | 1.06 | 53.6 | 2.96 | -72281 | 160123 | -95234 |
| RTY 15m run(5,0) dir=against hold 240m all | H2 | 1.43 | 2.36 | -144844 | -124111 | 606651 | -146786 | 0.93 | 38.9 | 2.78 | -76307 | 215865 | -80449 |
| RTY 15m run(5,0) dir=against hold 240m all | all | 0.93 | 1.47 | -132318 | -110313 | 606651 | -218321 | 2.43 | 44.0 | 2.03 | -90237 | 275016 | -104910 |
| ZN 5m run(5,0) dir=with hold 240m day (diag) | clean | -1.21 | -1.45 | -170836 | -133457 | 1284571 | -212857 | -0.86 | 49.5 | 1.25 | -86591 | 278391 | -104881 |
| ZN 5m run(5,0) dir=with hold 240m day (diag) | H1 | -2.83 | -3.11 | -56138 | -50184 | 372621 | -68755 | -0.74 | 57.1 | 2.58 | -78390 | 160927 | -79847 |
| ZN 5m run(5,0) dir=with hold 240m day (diag) | H2 | 0.08 | 0.14 | -69180 | -65494 | 437547 | -69605 | 0.05 | 47.2 | 2.36 | -90878 | 225591 | -92448 |
| ZN 5m run(5,0) dir=with hold 240m day (diag) | all | -1.06 | -1.32 | -145803 | -110362 | 1875502 | -212857 | -0.73 | 50.6 | 1.71 | -88003 | 278391 | -104881 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m run(4,0) dir=with hold 240m day | -20.0 | -23.2 | 16.4 | 35.6 | -24.2 / 17.8 | 25.0 / 42.9 | NO |
| NQ 5m run(3,0) dir=with hold 240m all | -8.9 | 2.6 | 8.3 | 26.8 | 1.8 / 7.6 | 3.3 / 6.9 | NO |
| RTY 15m run(5,0) dir=against hold 240m all | -13.6 | -16.0 | 8.1 | 7.3 | -17.0 / 5.5 | -2.5 / 22.2 | NO |
| GC 5m run(4,0) dir=against hold 240m all | -32.5 | -147.7 | -28.3 | -38.1 | 18.9 / 21.9 | -161.1 / -106.7 | NO |
| CL 5m run(4,0) dir=against hold 240m all | -14.9 | -73.2 | -3.2 | 26.2 | -20.9 / 9.5 | 12.6 / 19.7 | NO |
| ZN 5m run(5,0) dir=with hold 240m day (diag) | -44.9 | -15.3 | 10.6 | -0.8 | -16.2 / 10.9 | 27.0 / 28.5 | NO |
| BTC 15m run(4,0) dir=with hold 180m day | -21.1 | -14.2 | 8.7 | 32.3 | -8.0 / 18.3 | -7.3 / 11.2 | NO |
| HO 15m run(5,0) dir=against hold 180m day | -12.5 | -40.1 | 13.3 | 28.2 | 23.2 / 24.8 | 42.2 / 46.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m run(4,0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 1821 | 1.9 | -27.5 | -13.7 | 29.4 | 0.03 / -0.38 / -0.19 | 148.8 / 119.4 |
| ES 2 5m run(5,0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 2944 | 13.6 | -15.8 | -2.3 | 29.4 | 0.32 / -0.36 / -0.05 | 81.2 / 51.8 |
| ES 3 5m run(5,0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 5605 | 4.7 | -24.7 | -11.6 | 29.4 | 0.15 / -0.79 / -0.37 | 52.3 / 23.0 |
| ES 4 5m run(4,0) dir=with hold 240m all | negative pre-2023 | 8010 | -1.6 | -31.0 | -17.4 | 29.4 | -0.05 / -1.18 / -0.66 | 50.5 / 21.2 |
| ES 5 5m run(4,0) dir=with hold 240m day | negative pre-2023 | 2681 | -5.5 | -34.8 | -20.8 | 29.4 | -0.08 / -0.56 / -0.33 | 57.7 / 28.3 |
| ES 6 15m run(3,0) dir=with hold 240m day | negative pre-2023 | 2597 | -16.1 | -45.4 | -31.3 | 29.4 | -0.28 / -0.80 / -0.55 | 64.5 / 35.1 |
| ES 7 5m run(5,0) dir=with hold 180m day | gross-positive, cost-negative pre-2023 | 2267 | 15.7 | -13.7 | -0.1 | 29.4 | 0.26 / -0.22 / 0.00 | 56.8 / 27.4 |
| ES 8 5m run(3,0) dir=with hold 120m day | negative pre-2023 | 7406 | -9.9 | -39.3 | -25.2 | 29.4 | -0.44 / -1.74 / -1.11 | 38.7 / 9.3 |
| ES 9 15m run(4,0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 3796 | 12.6 | -16.8 | -3.2 | 29.4 | 0.46 / -0.62 / -0.12 | 38.0 / 8.6 |
| ES 10 (diag) 5m run(3,0) dir=with hold 240m day | negative pre-2023 | 3511 | -23.0 | -52.3 | -38.4 | 29.4 | -0.41 / -0.93 / -0.68 | 76.4 / 47.0 |
| NQ 1 5m run(3,0) dir=with hold 240m all | negative pre-2023 | 11944 | -17.3 | -31.6 | -23.2 | 14.4 | -0.52 / -0.96 / -0.70 | 70.7 / 56.4 |
| NQ 2 5m run(5,0) dir=with hold 60m day | positive pre-2023 | 4867 | 36.5 | 22.2 | 30.5 | 14.4 | 0.95 / 0.58 / 0.79 | 74.4 / 60.1 |
| NQ 3 15m run(4,0) dir=with hold 180m day | negative pre-2023 | 2540 | -13.6 | -28.0 | -19.5 | 14.4 | -0.17 / -0.34 / -0.24 | 171.1 / 156.7 |
| NQ 4 15m run(3,0) dir=with hold 180m day | positive pre-2023 | 3979 | 22.9 | 8.5 | 17.0 | 14.4 | 0.36 / 0.14 / 0.27 | 110.9 / 96.5 |
| NQ 5 15m run(5,0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 1172 | 12.4 | -2.0 | 6.3 | 14.4 | 0.08 / -0.01 / 0.04 | 236.5 / 222.2 |
| NQ 6 15m run(5,0) dir=against hold 60m all | negative pre-2023 | 5286 | -13.5 | -27.8 | -19.7 | 14.4 | -0.57 / -1.18 / -0.83 | 41.3 / 27.0 |
| NQ 7 15m run(4,0) dir=with hold 240m day | negative pre-2023 | 1995 | -29.1 | -43.4 | -35.0 | 14.4 | -0.26 / -0.39 / -0.31 | 139.7 / 125.4 |
| NQ 8 15m run(4,0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 3287 | 3.6 | -10.8 | -2.4 | 14.4 | 0.06 / -0.19 / -0.04 | 80.6 / 66.2 |
| NQ 9 5m run(5,0) dir=with hold 120m day | positive pre-2023 | 3705 | 59.3 | 45.0 | 53.3 | 14.4 | 0.98 / 0.74 / 0.88 | 58.9 / 44.6 |
| NQ 10 5m run(4,0) dir=against hold 180m day | negative pre-2023 | 4326 | -31.9 | -46.3 | -37.9 | 14.4 | -0.51 / -0.74 / -0.61 | 72.8 / 58.4 |
| RTY 1 15m run(5,0) dir=against hold 180m all | positive pre-2023 | 2453 | 14.9 | 0.6 | 2.8 | 14.4 | 0.59 / 0.03 / 0.12 | 58.8 / 44.4 |
| RTY 2 15m run(4,0) dir=against hold 180m day | positive pre-2023 | 1482 | 29.5 | 15.1 | 17.4 | 14.4 | 0.68 / 0.35 / 0.40 | 92.1 / 77.7 |
| RTY 3 15m run(4,0) dir=against hold 240m day | positive pre-2023 | 1170 | 27.5 | 13.1 | 15.4 | 14.4 | 0.48 / 0.23 / 0.27 | 110.8 / 96.5 |
| RTY 4 15m run(5,0) dir=against hold 180m day | positive pre-2023 | 856 | 13.7 | -0.6 | 1.7 | 14.4 | 0.26 / 0.00 / 0.04 | 112.0 / 97.6 |
| RTY 5 15m run(5,0) dir=against hold 120m all | gross-positive, cost-negative pre-2023 | 2811 | 1.3 | -13.1 | -10.8 | 14.4 | 0.07 / -0.66 / -0.55 | 40.5 / 26.1 |
| RTY 6 15m run(5,0) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 1065 | 8.6 | -5.7 | -3.4 | 14.4 | 0.22 / -0.13 / -0.07 | 67.7 / 53.3 |
| RTY 7 15m run(5,0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 692 | 6.7 | -7.6 | -5.3 | 14.4 | 0.11 / -0.10 / -0.07 | 105.5 / 91.2 |
| RTY 8 15m run(5,0) dir=against hold 240m all | positive pre-2023 | 2176 | 16.7 | 2.4 | 4.6 | 14.4 | 0.59 / 0.09 / 0.16 | 36.7 / 22.4 |
| RTY 9 (diag) 15m run(4,0) dir=against hold 120m day | positive pre-2023 | 1926 | 25.2 | 10.8 | 13.1 | 14.4 | 0.92 / 0.40 / 0.49 | 64.2 / 49.9 |
| RTY 10 (diag) 15m run(4,0) dir=against hold 120m all | gross-positive, cost-negative pre-2023 | 5302 | 12.6 | -1.8 | 0.5 | 14.4 | 1.02 / -0.13 / 0.04 | 22.7 / 8.3 |
| GC 1 15m run(4,0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 1854 | 18.9 | -5.5 | 4.2 | 24.4 | 0.36 / -0.10 / 0.09 | 61.6 / 37.2 |
| GC 2 5m run(4,0) dir=against hold 240m all | negative pre-2023 | 9126 | -4.2 | -28.6 | -19.0 | 24.4 | -0.21 / -1.35 / -0.90 | 33.1 / 8.8 |
| GC 3 15m run(5,0) dir=with hold 180m day | gross-positive, cost-negative pre-2023 | 1242 | 5.9 | -18.4 | -8.8 | 24.4 | 0.09 / -0.28 / -0.14 | 44.0 / 19.6 |
| GC 4 (diag) 5m run(3,0) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 11711 | 0.1 | -24.3 | -14.6 | 24.4 | 0.00 / -1.32 / -0.79 | 55.5 / 31.1 |
| GC 5 (diag) 5m run(3,0) dir=with hold 240m day | negative pre-2023 | 3780 | -2.8 | -27.2 | -17.5 | 24.4 | -0.05 / -0.62 / -0.39 | 75.1 / 50.7 |
| GC 6 (diag) 15m run(3,0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 11379 | 0.9 | -23.5 | -13.8 | 24.4 | 0.06 / -1.45 / -0.85 | 38.6 / 14.2 |
| CL 1 15m run(5,0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 3171 | 11.9 | -12.5 | -10.1 | 24.4 | 0.30 / -0.33 / -0.26 | 66.7 / 42.3 |
| CL 2 15m run(5,0) dir=against hold 180m all | gross-positive, cost-negative pre-2023 | 3548 | 2.4 | -22.0 | -19.6 | 24.4 | 0.07 / -0.72 / -0.64 | 56.1 / 31.7 |
| CL 3 5m run(4,0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 8826 | 4.0 | -20.3 | -17.8 | 24.4 | 0.19 / -0.92 / -0.81 | 41.3 / 17.0 |
| CL 4 5m run(5,0) dir=against hold 180m day | negative pre-2023 | 2553 | -12.4 | -36.7 | -34.2 | 24.4 | -0.26 / -0.77 / -0.72 | 49.9 / 25.5 |
| CL 5 5m run(3,0) dir=against hold 120m day | negative pre-2023 | 7738 | -3.4 | -27.7 | -25.2 | 24.4 | -0.14 / -1.15 / -1.05 | 31.7 / 7.3 |
| CL 6 5m run(5,0) dir=against hold 120m day | negative pre-2023 | 3371 | -2.4 | -26.8 | -24.1 | 24.4 | -0.07 / -0.81 / -0.73 | 30.4 / 6.0 |
| CL 7 (diag) 15m run(5,0) dir=against hold 180m day | negative pre-2023 | 1258 | -16.2 | -40.6 | -38.1 | 24.4 | -0.24 / -0.61 / -0.57 | 78.2 / 53.9 |
| CL 8 (diag) 15m run(5,0) dir=against hold 240m day | negative pre-2023 | 1035 | -15.3 | -39.7 | -37.2 | 24.4 | -0.18 / -0.47 / -0.44 | 92.2 / 67.8 |
| CL 9 (diag) 5m run(4,0) dir=against hold 240m day | negative pre-2023 | 2820 | -11.3 | -35.7 | -33.1 | 24.4 | -0.20 / -0.64 / -0.59 | 58.2 / 33.8 |
| ZN 1 (diag) 5m run(5,0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 937 | 8.6 | -27.0 | -31.9 | 35.6 | 0.31 / -0.97 / -1.15 | 7.4 / -28.2 |
| ZN 2 (diag) 15m run(5,0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 656 | 7.0 | -28.6 | -33.7 | 35.6 | 0.24 / -0.96 / -1.12 | 3.4 / -32.2 |
| ZN 3 (diag) 15m run(4,0) dir=against hold 240m day | negative pre-2023 | 1420 | -6.1 | -41.7 | -46.7 | 35.6 | -0.32 / -2.17 / -2.42 | 9.5 / -26.1 |
| BTC 1 15m run(4,0) dir=with hold 180m day | positive pre-2023 | 327 | 70.5 | 16.1 | 48.1 | 54.4 | 0.37 / 0.07 / 0.24 | 494.3 / 440.0 |
| BTC 2 15m run(5,0) dir=with hold 180m day | positive pre-2023 | 187 | 128.9 | 74.5 | 107.0 | 54.4 | 0.54 / 0.31 / 0.45 | 543.7 / 489.4 |
| BTC 3 15m run(4,0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 261 | 13.9 | -40.5 | -8.6 | 54.4 | 0.05 / -0.20 / -0.05 | 458.8 / 404.4 |
| BTC 4 15m run(4,0) dir=with hold 240m all | negative pre-2023 | 757 | -14.3 | -68.7 | -36.5 | 54.4 | -0.14 / -0.72 / -0.38 | 204.8 / 150.5 |
| BTC 5 15m run(4,0) dir=with hold 120m day | positive pre-2023 | 438 | 103.8 | 49.5 | 81.4 | 54.4 | 0.93 / 0.44 / 0.72 | 198.4 / 144.0 |
| BTC 6 15m run(4,0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 887 | 5.4 | -49.0 | -16.9 | 54.4 | 0.08 / -0.59 / -0.20 | 131.1 / 76.7 |
| BTC 7 15m run(5,0) dir=with hold 120m day | positive pre-2023 | 233 | 196.8 | 142.4 | 174.6 | 54.4 | 1.14 / 0.82 / 1.01 | 203.3 / 148.9 |
| BTC 8 15m run(5,0) dir=with hold 120m all | positive pre-2023 | 529 | 97.0 | 42.6 | 74.8 | 54.4 | 0.93 / 0.40 / 0.71 | 121.8 / 67.5 |
| BTC 9 5m run(4,0) dir=with hold 240m all | positive pre-2023 | 1172 | 88.1 | 33.7 | 65.9 | 54.4 | 1.07 / 0.41 / 0.80 | 130.1 / 75.8 |
| BTC 10 5m run(3,0) dir=with hold 180m all | negative pre-2023 | 2036 | -5.6 | -60.0 | -27.7 | 54.4 | -0.10 / -1.07 / -0.49 | 69.0 / 14.7 |
| HO 1 15m run(5,0) dir=against hold 240m day | negative pre-2023 | 1231 | -31.8 | -44.6 | -43.1 | 12.8 | -0.29 / -0.40 / -0.39 | 230.0 / 217.3 |
| HO 2 15m run(5,0) dir=against hold 180m day | negative pre-2023 | 1502 | -10.4 | -23.1 | -21.7 | 12.8 | -0.13 / -0.28 / -0.26 | 181.4 / 168.7 |
| HO 3 5m run(5,0) dir=against hold 180m day | positive pre-2023 | 3027 | 20.4 | 7.7 | 9.1 | 12.8 | 0.27 / 0.09 / 0.11 | 84.2 / 71.4 |
| HO 4 5m run(5,0) dir=against hold 240m day | positive pre-2023 | 2312 | 25.1 | 12.3 | 13.9 | 12.8 | 0.27 / 0.13 / 0.15 | 108.0 / 95.2 |
| HO 5 15m run(3,0) dir=against hold 240m day | negative pre-2023 | 2707 | -23.5 | -36.2 | -34.7 | 12.8 | -0.33 / -0.51 / -0.48 | 71.0 / 58.2 |
| HO 6 15m run(4,0) dir=against hold 180m day | positive pre-2023 | 2600 | 26.7 | 13.9 | 15.4 | 12.8 | 0.39 / 0.20 / 0.22 | 67.3 / 54.6 |
| HO 7 15m run(4,0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2045 | 4.9 | -7.9 | -6.4 | 12.8 | 0.05 / -0.10 / -0.09 | 81.8 / 69.0 |
| HO 8 15m run(5,0) dir=against hold 240m all | negative pre-2023 | 3272 | -21.3 | -34.0 | -32.4 | 12.8 | -0.35 / -0.57 / -0.54 | 59.9 / 47.1 |
| HO 9 15m run(3,0) dir=against hold 180m day | negative pre-2023 | 4048 | -15.1 | -27.9 | -26.3 | 12.8 | -0.31 / -0.56 / -0.53 | 55.5 / 42.7 |
| HO 10 15m run(5,0) dir=against hold 180m all | negative pre-2023 | 3707 | -7.2 | -19.9 | -18.3 | 12.8 | -0.16 / -0.43 / -0.40 | 45.0 / 32.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 12 cells pass the clean rule against a replicate mean of 10.4 (p(count) = 0.31, p(top) = 0.16); CL: 6 cells pass the clean rule against a replicate mean of 2.8 (p(count) = 0.06, p(top) = 0.28); ES: 9 cells pass the clean rule against a replicate mean of 4.6 (p(count) = 0.04, p(top) = 0.64); GC: 3 cells pass the clean rule against a replicate mean of 4.9 (p(count) = 0.89, p(top) = 0.94); HO: 13 cells pass the clean rule against a replicate mean of 9.8 (p(count) = 0.20, p(top) = 0.02); NQ: 14 cells pass the clean rule against a replicate mean of 14.6 (p(count) = 0.64, p(top) = 0.92); RTY: 8 cells pass the clean rule against a replicate mean of 6.1 (p(count) = 0.26, p(top) = 0.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 56 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.23 (HO 15m run(5,0) dir=against hold 180m day); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 4; 2x-slippage all-in uplift >= +0.10 for 7; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 21, 'gross-positive, cost-negative pre-2023': 18, 'positive pre-2023': 17}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q13.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q13/ (`Q13_CO_all_selected_scored.csv`).

DONE Q13
