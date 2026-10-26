# REPORT Q11 - Q11: volatility-burst (bar range > k x its recent mean, bar direction) with/against, time exit

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 60 selected cells (+12 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.16; best pair-window standalone Sharpe +0.97.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: volatility-burst (bar range > k x its recent mean, bar direction) with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        18 |               2.176 |                2 |         10 |            0 |
| CL    |      96 |         96 |         7 |               1.363 |                2 |          7 |            3 |
| ES    |      96 |         96 |        16 |               1.41  |                2 |         10 |            0 |
| GC    |      96 |         96 |        11 |               1.202 |                2 |         10 |            0 |
| HO    |      96 |         96 |         7 |               1.037 |                2 |          7 |            3 |
| NQ    |      96 |         96 |        18 |               1.792 |                2 |         10 |            0 |
| RTY   |      96 |         96 |         6 |               0.737 |                2 |          6 |            3 |
| ZN    |      96 |         96 |         0 |               0.004 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   16 |            5.4   |              12 |      0     |                       0.779 |            0.626 |           0.926 |    0.175 |       1.41  |                1.673 |
| NQ    |     200 |                   18 |           15.815 |              25 |      0.335 |                       1.244 |            0.903 |           1.179 |    0.01  |       1.792 |                2.118 |
| RTY   |     200 |                    6 |            6.765 |              14 |      0.67  |                       0.536 |            0.658 |           0.911 |    0.79  |       0.737 |                1.774 |
| GC    |     200 |                   11 |            5.955 |              12 |      0.035 |                       0.639 |            0.625 |           0.867 |    0.455 |       1.202 |                1.697 |
| CL    |     200 |                    7 |            2.94  |               8 |      0.01  |                       0.468 |            0.601 |           0.983 |    0.69  |       1.032 |                1.588 |
| ZN    |     200 |                    0 |            0.005 |               1 |      1     |                     nan     |            0.766 |           0.766 |  nan     |     nan     |                0.766 |
| BTC   |     200 |                   18 |           10.02  |              18 |      0.005 |                       1.292 |            0.716 |           0.95  |    0     |       2.176 |                1.984 |
| HO    |     200 |                    7 |            9.505 |              16 |      0.86  |                       0.67  |            0.711 |           0.939 |    0.62  |       1.037 |                1.937 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 5m burst(10,2.0) dir=with hold 120m day | 929 | 2 | 1.41 | -0.75 | 0.65 | -0.63 / 0.68 | 0.23 / 0.10 / -0.28 | -0.01 | -0.43 | 0.99 | -0.09 | 0.00 | 1455 | NO |
| ES 2 | 15m burst(10,3.0) dir=with hold 120m all | 565 | 2 | 0.90 | -0.90 | 0.35 | -0.36 / 0.87 | 0.16 / -0.36 / 0.01 | -0.02 | -0.38 | 0.96 | -0.15 | 0.75 | 880 | NO |
| ES 3 | 15m burst(10,3.0) dir=with hold 60m all | 598 | 2 | 0.80 | -0.78 | 0.55 | 0.18 / 0.54 | 0.18 / -0.03 / -0.15 | -0.01 | -0.03 | 1.00 | -0.12 | 0.50 | 937 | NO |
| ES 4 | 5m burst(10,2.0) dir=with hold 180m day | 754 | 2 | 0.77 | -0.58 | 0.40 | -0.33 / 0.98 | 0.09 / 0.28 / -0.29 | -0.06 | -0.39 | 0.94 | -0.18 | 0.25 | 1176 | NO |
| ES 5 | 15m burst(10,2.0) dir=with hold 180m all | 1314 | 2 | 0.74 | -1.15 | 0.45 | 0.04 / 0.45 | 0.07 / -0.27 / -0.06 | -0.13 | -0.23 | 1.00 | -0.22 | 0.00 | 2092 | NO |
| ES 6 | 15m burst(10,3.0) dir=with hold 120m day | 332 | 2 | 0.73 | -0.58 | 0.37 | -0.10 / 0.61 | 0.13 / -0.23 / -0.01 | 0.01 | -0.08 | 0.93 | -0.14 | 0.75 | 522 | NO |
| ES 7 | 15m burst(10,2.0) dir=with hold 180m day | 546 | 2 | 0.63 | -0.03 | 0.45 | 0.11 / 0.93 | 0.04 / 0.26 / -0.32 | -0.06 | 0.06 | 0.93 | -0.19 | 0.00 | 864 | NO |
| ES 8 | 15m burst(10,3.0) dir=with hold 60m day | 354 | 2 | 0.62 | -0.48 | 0.65 | 0.59 / 0.73 | 0.14 / 0.07 / -0.11 | 0.03 | 0.22 | 0.97 | -0.11 | 0.25 | 559 | NO |
| ES 9 | 15m burst(10,2.0) dir=with hold 240m all | 1184 | 2 | 0.61 | -1.41 | 0.02 | -0.62 / 0.78 | 0.03 / -0.42 / -0.43 | -0.24 | 0.14 | 0.87 | -0.36 | 0.00 | 1886 | NO |
| ES 10 | 15m burst(10,2.0) dir=with hold 120m day | 654 | 2 | 0.58 | -0.55 | 0.32 | -0.06 / 0.70 | 0.04 / 0.38 / -0.52 | -0.12 | 0.23 | 0.97 | -0.22 | 0.00 | 1013 | NO |
| NQ 1 | 5m burst(10,3.0) dir=with hold 120m all | 1219 | 2 | 1.79 | -0.22 | 0.90 | 0.04 / 1.04 | 0.28 / 0.30 / -0.27 | 0.12 | -0.32 | 0.98 | -0.07 | 0.75 | 1944 | NO |
| NQ 2 | 5m burst(10,2.0) dir=with hold 120m all | 2855 | 2 | 1.64 | -0.89 | 0.78 | -0.20 / 1.08 | 0.24 / 0.36 / -0.42 | 0.04 | -0.20 | 0.98 | -0.12 | 0.25 | 4535 | NO |
| NQ 3 | 5m burst(20,2.5) dir=with hold 120m day | 655 | 2 | 1.53 | -0.19 | 0.54 | -0.68 / 1.07 | 0.26 / 0.44 / -0.66 | 0.05 | 0.12 | 0.90 | -0.14 | 0.25 | 1027 | NO |
| NQ 4 | 5m burst(20,2.5) dir=with hold 120m all | 1671 | 2 | 1.45 | -0.62 | 0.97 | 0.44 / 1.17 | 0.22 / 0.33 / -0.16 | 0.11 | -0.30 | 1.00 | -0.07 | 0.00 | 2642 | NO |
| NQ 5 | 5m burst(10,3.0) dir=with hold 120m day | 523 | 2 | 1.37 | -0.03 | 0.43 | -0.43 / 1.32 | 0.20 / 0.65 / -0.68 | 0.03 | 0.01 | 0.91 | -0.19 | 0.50 | 844 | NO |
| NQ 6 | 15m burst(10,3.0) dir=with hold 120m all | 671 | 2 | 1.11 | -0.30 | 0.02 | -0.88 / 0.94 | 0.15 / -0.50 / -0.55 | -0.11 | -0.39 | 0.77 | -0.36 | 0.00 | 1034 | NO |
| NQ 7 | 15m burst(10,3.0) dir=with hold 120m day | 408 | 2 | 1.03 | -0.18 | -0.08 | -1.01 / 1.58 | 0.14 / -0.40 / -0.71 | -0.14 | -0.24 | 0.51 | -0.39 | 0.00 | 643 | NO |
| NQ 8 | 5m burst(10,3.0) dir=with hold 60m all | 1327 | 2 | 0.91 | 0.04 | 0.27 | -0.41 / 1.06 | 0.14 / -0.04 / -0.30 | -0.03 | -0.11 | 0.88 | -0.21 | 0.50 | 2141 | NO |
| NQ 9 | 5m burst(10,3.0) dir=with hold 60m day | 566 | 2 | 0.81 | 0.31 | 0.29 | -0.34 / 1.16 | 0.12 / 0.39 / -0.46 | -0.01 | 0.12 | 0.83 | -0.20 | 0.50 | 927 | NO |
| NQ 10 | 15m burst(10,2.0) dir=with hold 120m day | 631 | 2 | 0.81 | -0.46 | -0.07 | -0.89 / 1.09 | 0.06 / 0.38 / -0.85 | -0.12 | -0.21 | 0.68 | -0.35 | 0.00 | 984 | NO |
| RTY 1 | 5m burst(20,2.5) dir=against hold 240m all | 1365 | 2 | 0.74 | -0.58 | 0.45 | 0.09 / 0.88 | 0.07 / -0.11 / 0.20 | -0.01 | -0.34 | 0.97 | -0.12 | 0.00 | 2172 | NO |
| RTY 2 | 15m burst(10,3.0) dir=with hold 60m day | 457 | 2 | 0.59 | -0.22 | 0.72 | 0.83 / 0.94 | 0.08 / 0.16 / -0.07 | 0.01 | 0.41 | 1.00 | -0.11 | 0.00 | 730 | NO |
| RTY 3 | 15m burst(10,3.0) dir=with hold 60m all | 771 | 2 | 0.57 | -0.36 | 0.55 | 0.43 / 0.72 | 0.09 / -0.04 / -0.03 | -0.04 | 0.33 | 1.00 | -0.15 | 0.00 | 1223 | NO |
| RTY 4 | 5m burst(20,2.5) dir=against hold 240m day | 506 | 2 | 0.54 | -0.36 | -0.05 | -0.69 / 1.39 | 0.07 / -0.31 / 0.01 | -0.04 | -0.18 | 0.68 | -0.21 | 0.00 | 810 | NO |
| RTY 5 | 5m burst(20,2.5) dir=against hold 180m all | 1540 | 2 | 0.50 | -0.82 | 0.06 | -0.34 / 0.60 | 0.02 / -0.68 / 0.41 | -0.11 | -0.23 | 0.93 | -0.24 | 0.00 | 2446 | NO |
| RTY 6 | 5m burst(20,2.5) dir=against hold 60m day | 795 | 2 | 0.27 | -0.51 | -0.49 | -1.41 / 0.33 | 0.01 / -0.50 / -0.11 | -0.17 | -0.43 | 0.86 | -0.31 | 0.00 | 1275 | NO |
| RTY 7 (diag) | 5m burst(20,2.5) dir=against hold 180m day | 572 | 1 | 0.42 | -0.36 | -0.07 | -0.65 / 0.98 | 0.06 / -0.36 / 0.14 | -0.03 | -0.29 | 0.71 | -0.19 | 0.25 | 904 | diag |
| RTY 8 (diag) | 5m burst(10,3.0) dir=against hold 240m day | 457 | 1 | 0.36 | -0.30 | 0.08 | -0.20 / 1.22 | 0.02 / -0.57 / 0.28 | -0.05 | -0.14 | 0.73 | -0.21 | 0.00 | 741 | diag |
| RTY 9 (diag) | 15m burst(10,3.0) dir=with hold 120m all | 735 | 1 | 0.32 | -0.38 | -0.10 | -0.82 / 0.95 | 0.05 / -0.34 / -0.31 | -0.15 | -0.02 | 0.81 | -0.31 | 0.00 | 1164 | diag |
| GC 1 | 15m burst(10,3.0) dir=against hold 120m day | 256 | 2 | 1.20 | -0.90 | 0.12 | -0.62 / 1.31 | 0.22 / -1.24 / 0.02 | -0.06 | -0.52 | 0.78 | -0.35 | 0.00 | 372 | NO |
| GC 2 | 15m burst(10,3.0) dir=against hold 120m all | 602 | 2 | 0.85 | -1.27 | -0.68 | -1.66 / 1.02 | 0.14 / -1.60 / -1.04 | -0.45 | -0.50 | 0.24 | -0.80 | 0.00 | 946 | NO |
| GC 3 | 15m burst(10,3.0) dir=against hold 240m all | 564 | 2 | 0.74 | -0.57 | -0.77 | -1.85 / 1.05 | 0.12 / -1.74 / -0.84 | -0.42 | -0.18 | 0.14 | -0.74 | 0.00 | 870 | NO |
| GC 4 | 15m burst(20,2.5) dir=against hold 120m day | 408 | 2 | 0.68 | -0.66 | -0.25 | -1.04 / 1.25 | 0.13 / -1.27 / -0.08 | -0.17 | -0.03 | 0.54 | -0.42 | 0.00 | 629 | NO |
| GC 5 | 15m burst(10,3.0) dir=against hold 180m day | 239 | 2 | 0.64 | -0.67 | -0.42 | -1.15 / 1.61 | 0.11 / -1.64 / -0.18 | -0.24 | -0.45 | 0.32 | -0.56 | 0.00 | 342 | NO |
| GC 6 | 15m burst(10,2.0) dir=against hold 120m day | 534 | 2 | 0.64 | -0.96 | 0.54 | 0.62 / 1.14 | 0.09 / -0.86 / 0.64 | 0.04 | -0.54 | 0.95 | -0.25 | 0.50 | 859 | NO |
| GC 7 | 15m burst(10,2.0) dir=against hold 180m day | 486 | 2 | 0.60 | -0.66 | 0.42 | 0.45 / 0.88 | 0.10 / -1.18 / 0.73 | 0.01 | -0.49 | 0.86 | -0.31 | 0.50 | 774 | NO |
| GC 8 | 15m burst(10,2.0) dir=against hold 60m day | 664 | 2 | 0.40 | -1.02 | 0.07 | -0.13 / 0.93 | 0.05 / -1.08 / 0.16 | -0.17 | -0.16 | 0.90 | -0.39 | 0.00 | 1065 | NO |
| GC 9 | 15m burst(20,2.5) dir=against hold 180m day | 386 | 2 | 0.33 | -0.35 | -0.55 | -1.31 / 1.36 | 0.04 / -1.66 / 0.08 | -0.25 | -0.09 | 0.27 | -0.51 | 0.00 | 588 | NO |
| GC 10 | 15m burst(10,3.0) dir=against hold 240m day | 234 | 2 | 0.31 | -0.53 | -0.64 | -1.41 / 1.55 | 0.07 / -1.61 / -0.38 | -0.30 | -0.04 | 0.20 | -0.59 | 0.00 | 330 | NO |
| CL 1 | 15m burst(10,3.0) dir=with hold 60m day | 153 | 2 | 1.03 | -0.30 | 0.18 | -0.79 / 0.74 | 0.24 / -0.19 / -0.51 | -0.06 | 0.38 | 0.97 | -0.20 | 0.00 | 257 | NO |
| CL 2 | 5m burst(10,3.0) dir=with hold 180m day | 257 | 2 | 0.78 | -0.62 | -0.32 | -1.32 / 1.14 | 0.15 / -0.42 / -0.83 | -0.22 | 0.55 | 0.62 | -0.43 | 0.00 | 454 | NO |
| CL 3 | 15m burst(20,2.5) dir=with hold 60m day | 373 | 2 | 0.63 | -0.61 | -0.28 | -1.55 / 0.43 | 0.20 / -0.26 / -0.49 | -0.12 | 0.14 | 0.99 | -0.23 | 0.00 | 563 | NO |
| CL 4 | 15m burst(20,2.5) dir=with hold 120m day | 345 | 2 | 0.38 | -0.43 | -0.89 | -2.33 / 0.67 | 0.07 / -0.27 / -1.16 | -0.34 | 0.42 | 0.41 | -0.52 | 0.00 | 513 | NO |
| CL 5 | 15m burst(10,2.0) dir=with hold 240m day | 441 | 2 | 0.24 | -0.60 | -0.53 | -1.37 / 1.10 | 0.02 / -0.45 / -0.70 | -0.27 | 0.07 | 0.37 | -0.45 | 0.00 | 675 | NO |
| CL 6 | 15m burst(20,2.5) dir=with hold 240m day | 308 | 2 | 0.17 | -0.34 | -0.11 | -0.51 / 1.33 | 0.02 / -0.28 / -0.22 | -0.13 | 0.30 | 0.68 | -0.26 | 0.00 | 448 | NO |
| CL 7 | 5m burst(10,2.0) dir=against hold 180m day | 703 | 2 | 0.04 | -0.36 | 0.01 | -0.03 / 1.09 | 0.00 / -0.08 / 0.04 | -0.11 | -0.32 | 0.88 | -0.21 | 0.00 | 1164 | NO |
| CL 8 (diag) | 5m burst(10,3.0) dir=with hold 60m day | 327 | 1 | 1.36 | -0.52 | 0.08 | -1.10 / 0.27 | 0.34 / -0.27 / -0.62 | -0.09 | -0.20 | 0.99 | -0.22 | 0.50 | 596 | diag |
| CL 9 (diag) | 15m burst(10,3.0) dir=with hold 120m day | 148 | 1 | 0.57 | -0.39 | -0.09 | -0.82 / 1.05 | 0.09 / -0.27 / -0.46 | -0.14 | 0.15 | 0.74 | -0.29 | 0.00 | 245 | diag |
| CL 10 (diag) | 15m burst(10,3.0) dir=with hold 240m day | 131 | 1 | 0.50 | -0.31 | 0.61 | 0.72 / 1.14 | 0.07 / -0.24 / 0.21 | 0.03 | 0.15 | 0.92 | -0.14 | 0.00 | 211 | diag |
| ZN 1 (diag) | 5m burst(10,3.0) dir=with hold 240m day | 275 | 1 | 0.00 | -1.87 | -0.44 | -1.67 / -1.91 | 0.01 / -0.23 / -0.31 | -0.32 | -0.01 | 1.00 | -0.25 | 0.00 | 408 | diag |
| ZN 2 (diag) | 5m burst(20,2.5) dir=with hold 240m day | 374 | 0 | -0.61 | -2.31 | -0.90 | -1.53 / -1.39 | -0.14 / -0.11 / -0.38 | -0.47 | -0.06 | 1.00 | -0.35 | 0.00 | 565 | diag |
| ZN 3 (diag) | 15m burst(10,2.0) dir=with hold 240m day | 414 | 0 | -0.74 | -2.25 | -1.15 | -2.17 / -1.92 | -0.17 / -0.50 / -0.35 | -0.56 | 0.05 | 1.00 | -0.44 | 0.00 | 643 | diag |
| BTC 1 | 5m burst(10,3.0) dir=with hold 120m all | 2313 | 2 | 2.18 | -0.16 | 0.71 | -1.17 / 1.45 | 0.40 / -0.45 / -0.22 | 0.02 | 0.53 | 0.99 | -0.07 | 0.50 | 3697 | NO |
| BTC 2 | 15m burst(10,3.0) dir=with hold 180m all | 751 | 2 | 1.74 | -1.08 | 0.69 | -0.55 / 1.23 | 0.35 / -0.20 / -0.15 | 0.11 | -0.19 | 0.97 | -0.05 | 0.50 | 1198 | NO |
| BTC 3 | 15m burst(10,3.0) dir=with hold 120m all | 802 | 2 | 1.66 | -1.16 | 0.72 | -0.63 / 1.32 | 0.30 / 0.15 / -0.28 | 0.09 | -0.07 | 0.97 | -0.05 | 0.75 | 1287 | NO |
| BTC 4 | 15m burst(10,3.0) dir=with hold 240m all | 713 | 2 | 1.55 | -0.85 | 0.65 | -0.20 / 1.33 | 0.30 / 0.06 / -0.19 | 0.11 | -0.29 | 0.89 | -0.07 | 0.75 | 1139 | NO |
| BTC 5 | 15m burst(20,2.5) dir=with hold 120m all | 1123 | 2 | 1.22 | -0.34 | 0.36 | -0.87 / 0.62 | 0.19 / -0.30 / -0.16 | -0.03 | -0.05 | 0.90 | -0.15 | 0.75 | 1786 | NO |
| BTC 6 | 5m burst(20,2.5) dir=with hold 120m all | 2588 | 2 | 1.17 | -1.18 | 0.05 | -1.32 / 0.87 | 0.24 / -0.54 / -0.13 | -0.07 | 0.17 | 0.90 | -0.18 | 0.50 | 4146 | NO |
| BTC 7 | 15m burst(10,2.0) dir=with hold 120m all | 1784 | 2 | 1.10 | -0.49 | 0.46 | -0.56 / 0.77 | 0.20 / 0.30 / -0.37 | -0.01 | 0.11 | 0.96 | -0.12 | 0.25 | 2846 | NO |
| BTC 8 | 5m burst(10,3.0) dir=with hold 240m all | 1536 | 2 | 0.91 | -1.95 | 0.42 | -0.02 / 1.03 | 0.12 / -0.04 / 0.01 | -0.00 | 0.36 | 0.89 | -0.13 | 0.25 | 2452 | NO |
| BTC 9 | 15m burst(20,2.5) dir=with hold 180m all | 999 | 2 | 0.72 | -0.82 | 0.15 | -0.40 / 1.02 | 0.10 / -0.24 / -0.05 | -0.05 | -0.00 | 0.89 | -0.22 | 0.50 | 1587 | NO |
| BTC 10 | 15m burst(10,3.0) dir=with hold 240m day | 275 | 2 | 0.69 | -1.20 | 0.12 | -0.40 / 1.43 | 0.11 / -0.61 / 0.08 | -0.01 | -0.43 | 0.72 | -0.22 | 0.50 | 462 | NO |
| HO 1 | 5m burst(10,2.0) dir=against hold 240m day | 556 | 2 | 1.04 | 0.37 | 0.52 | 0.08 / 1.68 | 0.17 / 0.03 / -0.15 | 0.05 | -0.00 | 0.87 | -0.17 | 0.25 | 892 | NO |
| HO 2 | 5m burst(10,2.0) dir=against hold 120m day | 1029 | 2 | 1.01 | -0.00 | -0.20 | -1.30 / 1.64 | 0.18 / 0.34 / -0.87 | -0.12 | -0.04 | 0.54 | -0.33 | 0.00 | 1669 | NO |
| HO 3 | 15m burst(20,2.5) dir=with hold 120m day | 352 | 2 | 0.81 | -0.14 | -0.14 | -0.92 / 1.65 | 0.16 / -0.27 / -0.61 | -0.10 | 0.38 | 0.61 | -0.36 | 0.00 | 519 | NO |
| HO 4 | 15m burst(10,3.0) dir=with hold 240m day | 130 | 2 | 0.63 | 0.38 | 0.67 | 0.79 / 1.33 | 0.13 / -0.18 / 0.16 | 0.10 | 0.64 | 0.93 | -0.10 | 0.00 | 196 | NO |
| HO 5 | 15m burst(20,2.5) dir=with hold 60m day | 390 | 2 | 0.61 | -0.26 | 0.56 | 0.51 / 1.13 | 0.16 / 0.05 / 0.05 | 0.10 | 0.26 | 0.98 | -0.09 | 0.50 | 571 | NO |
| HO 6 | 15m burst(10,2.0) dir=with hold 180m all | 1620 | 2 | 0.36 | -0.60 | 0.65 | 0.92 / 1.23 | 0.06 / -0.26 / 0.58 | 0.08 | 0.17 | 0.97 | -0.12 | 0.00 | 2616 | NO |
| HO 7 | 5m burst(20,2.5) dir=against hold 240m day | 433 | 2 | 0.24 | -0.26 | 0.16 | 0.12 / 1.33 | 0.04 / 0.05 / -0.16 | -0.03 | -0.38 | 0.75 | -0.30 | 0.00 | 683 | NO |
| HO 8 (diag) | 15m burst(10,3.0) dir=with hold 120m day | 144 | 1 | 0.84 | 0.23 | 0.22 | -0.28 / 1.16 | 0.17 / -0.20 / -0.35 | -0.01 | 0.35 | 0.79 | -0.25 | 0.00 | 224 | diag |
| HO 9 (diag) | 15m burst(10,3.0) dir=with hold 60m day | 148 | 1 | 0.65 | -0.17 | 0.15 | -0.31 / 1.51 | 0.17 / 0.10 / -0.43 | -0.00 | 0.49 | 0.72 | -0.24 | 0.75 | 237 | diag |
| HO 10 (diag) | 5m burst(10,2.0) dir=against hold 180m day | 747 | 1 | 0.61 | 0.46 | 0.22 | -0.16 / 1.55 | 0.13 / 0.11 / -0.17 | 0.01 | 0.04 | 0.67 | -0.22 | 0.25 | 1227 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 60 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 39 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 25 |
| worst-decile corr <= +0.30 | 61 |
| plateau >= 0.75 | 7 |
| all-in uplift at 2x slippage >= +0.10 | 4 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m burst(10,3.0) dir=with hold 180m all | clean | 1.72 | 3.31 | -97995 | -83732 | 264302 | -127264 | 5.90 | 41.9 | 1.81 | -86890 | 248815 | -102496 |
| BTC 15m burst(10,3.0) dir=with hold 180m all | H1 | -0.61 | -0.77 | -275281 | -241403 | 701915 | -331019 | -0.38 | 57.1 | 2.62 | -83844 | 164756 | -88108 |
| BTC 15m burst(10,3.0) dir=with hold 180m all | H2 | -0.56 | -0.75 | -104023 | -93510 | 519245 | -108340 | -0.27 | 55.6 | 2.15 | -94165 | 202943 | -101322 |
| BTC 15m burst(10,3.0) dir=with hold 180m all | all | 0.69 | 1.04 | -151830 | -117272 | 945765 | -331019 | 1.22 | 47.0 | 2.01 | -88915 | 248815 | -102496 |
| CL 15m burst(10,3.0) dir=with hold 60m day | clean | 1.07 | 2.06 | -102951 | -87956 | 396224 | -130959 | 2.45 | 36.2 | 1.70 | -79204 | 235714 | -82969 |
| CL 15m burst(10,3.0) dir=with hold 60m day | H1 | -1.26 | -1.39 | -117683 | -102909 | 386034 | -128886 | -0.53 | 35.7 | 2.63 | -85226 | 151783 | -99584 |
| CL 15m burst(10,3.0) dir=with hold 60m day | H2 | -0.75 | -1.13 | -253088 | -198705 | 971716 | -274457 | -0.46 | 55.6 | 1.79 | -102363 | 243312 | -105989 |
| CL 15m burst(10,3.0) dir=with hold 60m day | all | 0.18 | 0.29 | -153403 | -124102 | 971716 | -274457 | 0.33 | 40.5 | 1.86 | -89002 | 243312 | -105989 |
| ES 15m burst(10,3.0) dir=with hold 60m all | clean | 0.88 | 1.35 | -138135 | -102405 | 554677 | -218240 | 1.44 | 43.8 | 1.64 | -86121 | 256103 | -96563 |
| ES 15m burst(10,3.0) dir=with hold 60m all | H1 | 1.08 | 1.71 | -140776 | -130995 | 214439 | -156697 | 1.66 | 39.3 | 2.79 | -68103 | 156575 | -70309 |
| ES 15m burst(10,3.0) dir=with hold 60m all | H2 | -0.45 | -0.62 | -197824 | -167928 | 838431 | -239987 | -0.25 | 55.6 | 2.14 | -85693 | 245461 | -90311 |
| ES 15m burst(10,3.0) dir=with hold 60m all | all | 0.55 | 0.81 | -164974 | -133464 | 838431 | -239987 | 1.12 | 45.2 | 1.95 | -85213 | 256103 | -96563 |
| GC 15m burst(10,2.0) dir=against hold 120m day | clean | 0.55 | 0.92 | -111995 | -95035 | 427729 | -168515 | 1.18 | 51.4 | 1.55 | -87177 | 252817 | -96735 |
| GC 15m burst(10,2.0) dir=against hold 120m day | H1 | -0.73 | -0.91 | -367941 | -348142 | 863957 | -379777 | -0.51 | 53.6 | 1.97 | -121168 | 205426 | -139996 |
| GC 15m burst(10,2.0) dir=against hold 120m day | H2 | 1.62 | 2.78 | -261079 | -247683 | 587078 | -278080 | 2.25 | 41.7 | 2.94 | -102934 | 159918 | -109020 |
| GC 15m burst(10,2.0) dir=against hold 120m day | all | 0.54 | 0.81 | -265349 | -194361 | 1451035 | -379777 | 0.96 | 49.4 | 1.94 | -99147 | 263642 | -139996 |
| HO 15m burst(10,2.0) dir=with hold 180m all | clean | 0.40 | 0.59 | -124349 | -103894 | 1029352 | -198009 | 0.35 | 44.8 | 1.52 | -89940 | 280236 | -103920 |
| HO 15m burst(10,2.0) dir=with hold 180m all | H1 | -1.01 | -1.47 | -96056 | -89070 | 432348 | -107338 | -0.52 | 64.3 | 2.56 | -75968 | 181446 | -76181 |
| HO 15m burst(10,2.0) dir=with hold 180m all | H2 | 1.60 | 2.87 | -245832 | -205351 | 437768 | -259095 | 2.77 | 44.4 | 2.88 | -92048 | 201820 | -106274 |
| HO 15m burst(10,2.0) dir=with hold 180m all | all | 0.65 | 1.08 | -168072 | -136234 | 1029352 | -259095 | 1.31 | 47.6 | 1.99 | -88879 | 280236 | -106274 |
| NQ 5m burst(10,3.0) dir=with hold 120m all | clean | 1.78 | 3.48 | -97623 | -80889 | 383765 | -128217 | 4.20 | 37.1 | 1.74 | -81525 | 259605 | -90275 |
| NQ 5m burst(10,3.0) dir=with hold 120m all | H1 | 0.97 | 1.79 | -114152 | -105115 | 361260 | -121632 | 0.81 | 53.6 | 3.13 | -68601 | 165573 | -73025 |
| NQ 5m burst(10,3.0) dir=with hold 120m all | H2 | -0.46 | -0.59 | -235869 | -226322 | 1064934 | -243513 | -0.24 | 50.0 | 2.02 | -69939 | 227010 | -71784 |
| NQ 5m burst(10,3.0) dir=with hold 120m all | all | 0.90 | 1.39 | -170977 | -132094 | 1064934 | -243513 | 1.54 | 42.9 | 2.01 | -79002 | 259605 | -90275 |
| RTY 15m burst(10,3.0) dir=with hold 60m day | clean | 0.65 | 1.13 | -111656 | -89113 | 488355 | -189492 | 1.21 | 52.4 | 1.54 | -84685 | 250565 | -90645 |
| RTY 15m burst(10,3.0) dir=with hold 60m day | H1 | 1.18 | 2.10 | -94655 | -90967 | 376497 | -100215 | 0.77 | 39.3 | 2.99 | -73752 | 160724 | -95006 |
| RTY 15m burst(10,3.0) dir=with hold 60m day | H2 | 0.53 | 0.89 | -96424 | -83667 | 324901 | -104498 | 0.49 | 50.0 | 2.23 | -93718 | 226071 | -100195 |
| RTY 15m burst(10,3.0) dir=with hold 60m day | all | 0.72 | 1.24 | -110803 | -90021 | 488355 | -189492 | 2.14 | 50.0 | 1.92 | -88420 | 250565 | -100195 |
| ZN 5m burst(10,3.0) dir=with hold 240m day (diag) | clean | 0.02 | 0.03 | -106457 | -94539 | 611589 | -124662 | 0.03 | 50.5 | 1.47 | -88742 | 310088 | -96898 |
| ZN 5m burst(10,3.0) dir=with hold 240m day (diag) | H1 | -0.94 | -1.24 | -59510 | -57838 | 249515 | -61294 | -0.47 | 50.0 | 2.60 | -83706 | 174803 | -83910 |
| ZN 5m burst(10,3.0) dir=with hold 240m day (diag) | H2 | -2.12 | -2.23 | -144362 | -99862 | 553620 | -194588 | -0.84 | 55.6 | 1.99 | -89258 | 213741 | -91083 |
| ZN 5m burst(10,3.0) dir=with hold 240m day (diag) | all | -0.44 | -0.62 | -112525 | -95222 | 822413 | -194588 | -0.69 | 51.8 | 1.77 | -89234 | 310088 | -96898 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m burst(10,3.0) dir=with hold 60m all | -19.5 | -0.3 | 14.3 | 16.1 | -1.1 / 13.7 | 16.9 / 17.7 | NO |
| NQ 5m burst(10,3.0) dir=with hold 120m all | -11.6 | 9.5 | 23.7 | -5.3 | 9.9 / 24.4 | 38.7 / 44.8 | NO |
| RTY 15m burst(10,3.0) dir=with hold 60m day | -18.3 | -2.1 | 10.5 | 27.9 | 11.8 / 15.3 | -2.0 / 19.7 | NO |
| GC 15m burst(10,2.0) dir=against hold 120m day | -14.5 | -78.6 | -23.7 | -36.1 | -2.0 / 12.6 | -88.2 / -80.2 | NO |
| CL 15m burst(10,3.0) dir=with hold 60m day | -26.4 | -12.6 | 8.6 | 31.0 | 23.5 / 28.2 | -10.8 / 15.3 | NO |
| ZN 5m burst(10,3.0) dir=with hold 240m day (diag) | -36.3 | -1.4 | 8.2 | -7.7 | -2.2 / 9.8 | 18.6 / 18.2 | NO |
| BTC 15m burst(10,3.0) dir=with hold 180m all | -17.1 | -11.6 | 8.6 | 32.5 | -12.5 / 10.8 | 9.8 / 18.0 | NO |
| HO 15m burst(10,2.0) dir=with hold 180m all | -14.9 | -13.2 | 5.7 | 12.2 | -10.4 / 8.0 | 32.7 / 33.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 5m burst(10,2.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 4660 | 0.7 | -28.7 | -14.5 | 29.4 | 0.02 / -0.75 / -0.38 | 103.2 / 73.8 |
| ES 2 15m burst(10,3.0) dir=with hold 120m all | negative pre-2023 | 3098 | -0.2 | -29.6 | -15.3 | 29.4 | -0.00 / -0.90 / -0.47 | 86.5 / 57.1 |
| ES 3 15m burst(10,3.0) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 3213 | 7.7 | -21.6 | -7.4 | 29.4 | 0.28 / -0.78 / -0.26 | 67.9 / 38.6 |
| ES 4 5m burst(10,2.0) dir=with hold 180m day | negative pre-2023 | 3689 | -0.5 | -29.8 | -15.6 | 29.4 | -0.01 / -0.58 / -0.30 | 88.1 / 58.8 |
| ES 5 15m burst(10,2.0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 7048 | 1.3 | -28.0 | -13.8 | 29.4 | 0.05 / -1.15 / -0.57 | 57.7 / 28.3 |
| ES 6 15m burst(10,3.0) dir=with hold 120m day | negative pre-2023 | 1592 | -5.2 | -34.6 | -20.5 | 29.4 | -0.08 / -0.58 / -0.34 | 103.8 / 74.5 |
| ES 7 15m burst(10,2.0) dir=with hold 180m day | gross-positive, cost-negative pre-2023 | 2703 | 27.5 | -1.9 | 12.3 | 29.4 | 0.49 / -0.03 / 0.22 | 88.0 / 58.7 |
| ES 8 15m burst(10,3.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 1663 | 6.6 | -22.7 | -8.7 | 29.4 | 0.14 / -0.48 / -0.18 | 78.1 / 48.7 |
| ES 9 15m burst(10,2.0) dir=with hold 240m all | negative pre-2023 | 6494 | -7.3 | -36.7 | -22.4 | 29.4 | -0.28 / -1.41 / -0.86 | 57.2 / 27.9 |
| ES 10 15m burst(10,2.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 3169 | 6.0 | -23.3 | -9.1 | 29.4 | 0.14 / -0.55 / -0.21 | 65.5 / 36.1 |
| NQ 1 5m burst(10,3.0) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 7557 | 7.7 | -6.6 | 2.2 | 14.4 | 0.25 / -0.22 / 0.07 | 124.3 / 109.9 |
| NQ 2 5m burst(10,2.0) dir=with hold 120m all | negative pre-2023 | 15519 | -3.5 | -17.8 | -9.2 | 14.4 | -0.18 / -0.89 / -0.46 | 77.9 / 63.6 |
| NQ 3 5m burst(20,2.5) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 3321 | 0.3 | -14.1 | -5.4 | 14.4 | 0.00 / -0.19 / -0.07 | 212.4 / 198.1 |
| NQ 4 5m burst(20,2.5) dir=with hold 120m all | negative pre-2023 | 9880 | -3.3 | -17.7 | -8.9 | 14.4 | -0.12 / -0.62 / -0.32 | 103.4 / 89.0 |
| NQ 5 5m burst(10,3.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 2757 | 12.4 | -2.0 | 6.6 | 14.4 | 0.16 / -0.03 / 0.08 | 187.9 / 173.6 |
| NQ 6 15m burst(10,3.0) dir=with hold 120m all | negative pre-2023 | 4042 | -1.5 | -15.9 | -7.1 | 14.4 | -0.03 / -0.30 / -0.13 | 112.6 / 98.3 |
| NQ 7 15m burst(10,3.0) dir=with hold 120m day | negative pre-2023 | 2225 | -1.7 | -16.1 | -7.4 | 14.4 | -0.02 / -0.18 / -0.08 | 159.3 / 144.9 |
| NQ 8 5m burst(10,3.0) dir=with hold 60m all | positive pre-2023 | 8633 | 15.3 | 1.0 | 9.9 | 14.4 | 0.73 / 0.04 / 0.47 | 53.1 / 38.7 |
| NQ 9 5m burst(10,3.0) dir=with hold 60m day | positive pre-2023 | 3064 | 31.5 | 17.2 | 25.7 | 14.4 | 0.58 / 0.31 / 0.47 | 88.9 / 74.5 |
| NQ 10 15m burst(10,2.0) dir=with hold 120m day | negative pre-2023 | 3207 | -20.8 | -35.2 | -26.6 | 14.4 | -0.27 / -0.46 / -0.34 | 97.5 / 83.2 |
| RTY 1 5m burst(20,2.5) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 4289 | 1.6 | -12.8 | -10.5 | 14.4 | 0.07 / -0.58 / -0.47 | 34.8 / 20.5 |
| RTY 2 15m burst(10,3.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 1387 | 6.1 | -8.3 | -6.0 | 14.4 | 0.16 / -0.22 / -0.16 | 41.6 / 27.3 |
| RTY 3 15m burst(10,3.0) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 2482 | 6.6 | -7.8 | -5.5 | 14.4 | 0.30 / -0.36 / -0.25 | 29.8 / 15.4 |
| RTY 4 5m burst(20,2.5) dir=against hold 240m day | negative pre-2023 | 1492 | -6.2 | -20.5 | -18.3 | 14.4 | -0.11 / -0.36 / -0.32 | 39.0 / 24.7 |
| RTY 5 5m burst(20,2.5) dir=against hold 180m all | negative pre-2023 | 4880 | -1.7 | -16.0 | -13.7 | 14.4 | -0.09 / -0.82 / -0.71 | 23.2 / 8.8 |
| RTY 6 5m burst(20,2.5) dir=against hold 60m day | gross-positive, cost-negative pre-2023 | 2361 | 0.8 | -13.5 | -11.3 | 14.4 | 0.02 / -0.51 / -0.43 | 18.6 / 4.2 |
| RTY 7 (diag) 5m burst(20,2.5) dir=against hold 180m day | negative pre-2023 | 1620 | -3.3 | -17.7 | -15.4 | 14.4 | -0.07 / -0.36 / -0.31 | 32.7 / 18.3 |
| RTY 8 (diag) 5m burst(10,3.0) dir=against hold 240m day | negative pre-2023 | 1362 | -3.9 | -18.2 | -16.0 | 14.4 | -0.06 / -0.30 / -0.27 | 30.9 / 16.6 |
| RTY 9 (diag) 15m burst(10,3.0) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 2347 | 3.8 | -10.6 | -8.3 | 14.4 | 0.13 / -0.38 / -0.30 | 29.6 / 15.3 |
| GC 1 15m burst(10,3.0) dir=against hold 120m day | negative pre-2023 | 1390 | -32.5 | -56.8 | -46.8 | 24.4 | -0.51 / -0.90 / -0.74 | 157.6 / 133.3 |
| GC 2 15m burst(10,3.0) dir=against hold 120m all | negative pre-2023 | 3722 | -13.5 | -37.9 | -27.8 | 24.4 | -0.46 / -1.27 / -0.94 | 73.6 / 49.3 |
| GC 3 15m burst(10,3.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 3325 | 2.2 | -22.1 | -12.1 | 24.4 | 0.04 / -0.57 / -0.32 | 82.1 / 57.8 |
| GC 4 15m burst(20,2.5) dir=against hold 120m day | negative pre-2023 | 2164 | -10.9 | -35.3 | -25.4 | 24.4 | -0.20 / -0.66 / -0.47 | 85.4 / 61.0 |
| GC 5 15m burst(10,3.0) dir=against hold 180m day | negative pre-2023 | 1227 | -27.2 | -51.5 | -41.6 | 24.4 | -0.35 / -0.67 / -0.54 | 97.8 / 73.5 |
| GC 6 15m burst(10,2.0) dir=against hold 120m day | negative pre-2023 | 3015 | -13.8 | -38.2 | -28.2 | 24.4 | -0.34 / -0.96 / -0.71 | 68.4 / 44.0 |
| GC 7 15m burst(10,2.0) dir=against hold 180m day | negative pre-2023 | 2621 | -7.3 | -31.6 | -21.7 | 24.4 | -0.15 / -0.66 / -0.45 | 70.0 / 45.7 |
| GC 8 15m burst(10,2.0) dir=against hold 60m day | negative pre-2023 | 3657 | -4.6 | -29.0 | -19.1 | 24.4 | -0.16 / -1.02 / -0.67 | 41.1 / 16.7 |
| GC 9 15m burst(20,2.5) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 1936 | 1.4 | -22.9 | -13.1 | 24.4 | 0.03 / -0.35 / -0.20 | 57.6 / 33.2 |
| GC 10 15m burst(10,3.0) dir=against hold 240m day | negative pre-2023 | 1155 | -20.2 | -44.5 | -34.6 | 24.4 | -0.24 / -0.53 / -0.41 | 62.1 / 37.8 |
| CL 1 15m burst(10,3.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 1146 | 9.2 | -15.2 | -11.9 | 24.4 | 0.18 / -0.30 / -0.23 | 89.5 / 65.2 |
| CL 2 5m burst(10,3.0) dir=with hold 180m day | negative pre-2023 | 1536 | -19.2 | -43.5 | -40.6 | 24.4 | -0.27 / -0.62 / -0.57 | 80.4 / 56.0 |
| CL 3 15m burst(20,2.5) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 2490 | 4.9 | -19.5 | -17.1 | 24.4 | 0.15 / -0.61 / -0.54 | 51.4 / 27.0 |
| CL 4 15m burst(20,2.5) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 2126 | 3.1 | -21.3 | -18.9 | 24.4 | 0.06 / -0.43 / -0.38 | 45.0 / 20.7 |
| CL 5 15m burst(10,2.0) dir=with hold 240m day | negative pre-2023 | 2325 | -15.4 | -39.8 | -37.3 | 24.4 | -0.23 / -0.60 / -0.56 | 40.6 / 16.3 |
| CL 6 15m burst(20,2.5) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 1832 | 1.5 | -22.8 | -20.6 | 24.4 | 0.02 / -0.34 / -0.31 | 38.6 / 14.2 |
| CL 7 5m burst(10,2.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 3934 | 9.8 | -14.6 | -12.0 | 24.4 | 0.24 / -0.36 / -0.30 | 26.3 / 1.9 |
| CL 8 (diag) 5m burst(10,3.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 2207 | 6.6 | -17.7 | -14.4 | 24.4 | 0.20 / -0.52 / -0.43 | 80.0 / 55.7 |
| CL 9 (diag) 15m burst(10,3.0) dir=with hold 120m day | negative pre-2023 | 1106 | -3.4 | -27.8 | -24.5 | 24.4 | -0.05 / -0.39 / -0.35 | 74.1 / 49.8 |
| CL 10 (diag) 15m burst(10,3.0) dir=with hold 240m day | negative pre-2023 | 926 | -6.7 | -31.0 | -28.1 | 24.4 | -0.07 / -0.31 / -0.28 | 85.7 / 61.4 |
| ZN 1 (diag) 5m burst(10,3.0) dir=with hold 240m day | negative pre-2023 | 1086 | -14.3 | -49.9 | -54.7 | 35.6 | -0.55 / -1.87 / -2.05 | 36.1 / 0.5 |
| ZN 2 (diag) 5m burst(20,2.5) dir=with hold 240m day | negative pre-2023 | 1762 | -12.0 | -47.6 | -52.7 | 35.6 | -0.59 / -2.31 / -2.54 | 22.3 / -13.3 |
| ZN 3 (diag) 15m burst(10,2.0) dir=with hold 240m day | negative pre-2023 | 1980 | -7.5 | -43.1 | -48.1 | 35.6 | -0.39 / -2.25 / -2.51 | 21.6 / -14.1 |
| BTC 1 5m burst(10,3.0) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 1965 | 47.3 | -7.1 | 25.4 | 54.4 | 1.16 / -0.16 / 0.64 | 233.8 / 179.4 |
| BTC 2 15m burst(10,3.0) dir=with hold 180m all | negative pre-2023 | 730 | -53.8 | -108.1 | -76.0 | 54.4 | -0.55 / -1.08 / -0.76 | 442.8 / 388.5 |
| BTC 3 15m burst(10,3.0) dir=with hold 120m all | negative pre-2023 | 810 | -52.0 | -106.3 | -74.2 | 54.4 | -0.57 / -1.16 / -0.81 | 380.7 / 326.3 |
| BTC 4 15m burst(10,3.0) dir=with hold 240m all | negative pre-2023 | 654 | -52.6 | -107.0 | -74.8 | 54.4 | -0.43 / -0.85 / -0.60 | 406.4 / 352.0 |
| BTC 5 15m burst(20,2.5) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 980 | 25.2 | -29.2 | 3.0 | 54.4 | 0.29 / -0.34 / 0.03 | 232.2 / 177.9 |
| BTC 6 5m burst(20,2.5) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 2122 | 8.4 | -46.0 | -13.6 | 54.4 | 0.23 / -1.18 / -0.34 | 144.9 / 90.5 |
| BTC 7 15m burst(10,2.0) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 1497 | 24.4 | -30.0 | 2.3 | 54.4 | 0.43 / -0.49 / 0.06 | 176.8 / 122.5 |
| BTC 8 5m burst(10,3.0) dir=with hold 240m all | negative pre-2023 | 1247 | -58.5 | -112.8 | -80.4 | 54.4 | -1.02 / -1.95 / -1.40 | 166.8 / 112.4 |
| BTC 9 15m burst(20,2.5) dir=with hold 180m all | negative pre-2023 | 843 | -33.1 | -87.5 | -55.2 | 54.4 | -0.31 / -0.82 / -0.52 | 169.8 / 115.4 |
| BTC 10 15m burst(10,3.0) dir=with hold 240m day | negative pre-2023 | 224 | -216.0 | -270.3 | -237.4 | 54.4 | -0.96 / -1.20 / -1.05 | 376.4 / 322.0 |
| HO 1 5m burst(10,2.0) dir=against hold 240m day | positive pre-2023 | 2855 | 42.2 | 29.4 | 30.9 | 12.8 | 0.54 / 0.37 / 0.39 | 98.3 / 85.5 |
| HO 2 5m burst(10,2.0) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 6011 | 12.5 | -0.3 | 1.2 | 12.8 | 0.37 / -0.00 / 0.04 | 51.3 / 38.5 |
| HO 3 15m burst(20,2.5) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 2163 | 3.3 | -9.4 | -8.1 | 12.8 | 0.05 / -0.14 / -0.12 | 63.7 / 50.9 |
| HO 4 15m burst(10,3.0) dir=with hold 240m day | positive pre-2023 | 862 | 71.0 | 58.3 | 59.8 | 12.8 | 0.46 / 0.38 / 0.39 | 116.8 / 104.0 |
| HO 5 15m burst(20,2.5) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 2536 | 1.3 | -11.5 | -10.2 | 12.8 | 0.03 / -0.26 / -0.23 | 43.6 / 30.8 |
| HO 6 15m burst(10,2.0) dir=with hold 180m all | negative pre-2023 | 8326 | -5.0 | -17.7 | -16.2 | 12.8 | -0.17 / -0.60 / -0.55 | 24.1 / 11.4 |
| HO 7 5m burst(20,2.5) dir=against hold 240m day | negative pre-2023 | 2328 | -10.8 | -23.5 | -22.1 | 12.8 | -0.12 / -0.26 / -0.24 | 32.3 / 19.5 |
| HO 8 (diag) 15m burst(10,3.0) dir=with hold 120m day | positive pre-2023 | 1075 | 33.6 | 20.9 | 22.4 | 12.8 | 0.37 / 0.23 / 0.25 | 110.9 / 98.2 |
| HO 9 (diag) 15m burst(10,3.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 1116 | 1.5 | -11.3 | -9.7 | 12.8 | 0.02 / -0.17 / -0.15 | 75.8 / 63.1 |
| HO 10 (diag) 5m burst(10,2.0) dir=against hold 180m day | positive pre-2023 | 4015 | 37.5 | 24.7 | 26.1 | 12.8 | 0.69 / 0.46 / 0.49 | 54.2 / 41.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 18 cells pass the clean rule against a replicate mean of 10.0 (p(count) = 0.01, p(top) = 0.00); CL: 7 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 0.01, p(top) = 0.69); ES: 16 cells pass the clean rule against a replicate mean of 5.4 (p(count) = 0.00, p(top) = 0.17); GC: 11 cells pass the clean rule against a replicate mean of 6.0 (p(count) = 0.04, p(top) = 0.46); HO: 7 cells pass the clean rule against a replicate mean of 9.5 (p(count) = 0.86, p(top) = 0.62); NQ: 18 cells pass the clean rule against a replicate mean of 15.8 (p(count) = 0.34, p(top) = 0.01); RTY: 6 cells pass the clean rule against a replicate mean of 6.8 (p(count) = 0.67, p(top) = 0.79); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 60 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.16 (BTC 15m burst(10,3.0) dir=with hold 180m all); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 6; 2x-slippage all-in uplift >= +0.10 for 4; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 29, 'gross-positive, cost-negative pre-2023': 27, 'positive pre-2023': 4}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q11.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q11/ (`Q11_CO_all_selected_scored.csv`).

DONE Q11
