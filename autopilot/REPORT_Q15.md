# REPORT Q15 - Q15: volume-spike bar (volume > k x recent mean), bar direction with/against, time exit

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 63 selected cells (+9 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.18; best pair-window standalone Sharpe +1.07.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: volume-spike bar (volume > k x recent mean), bar direction with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |         6 |               1.081 |                2 |          6 |            3 |
| CL    |      96 |         96 |         9 |               1.501 |                2 |          9 |            1 |
| ES    |      96 |         96 |         8 |               0.93  |                2 |          8 |            2 |
| GC    |      96 |         96 |        18 |               1.296 |                2 |         10 |            0 |
| HO    |      96 |         96 |        13 |               1.619 |                2 |         10 |            0 |
| NQ    |      96 |         96 |        30 |               1.558 |                2 |         10 |            0 |
| RTY   |      96 |         96 |        17 |               1.236 |                2 |         10 |            0 |
| ZN    |      96 |         96 |         0 |              -0.27  |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    8 |            4.01  |              10 |      0.025 |                       0.354 |            0.61  |           0.947 |    0.9   |       0.836 |                1.526 |
| NQ    |     200 |                   30 |           15.045 |              24 |      0     |                       1.149 |            0.893 |           1.141 |    0.05  |       1.558 |                2.009 |
| RTY   |     200 |                   17 |            5.835 |              13 |      0     |                       0.851 |            0.655 |           0.929 |    0.125 |       1.236 |                1.811 |
| GC    |     200 |                   18 |            6.195 |              14 |      0     |                       0.901 |            0.639 |           0.942 |    0.075 |       1.296 |                1.829 |
| CL    |     200 |                    9 |            3.015 |               8 |      0     |                       0.87  |            0.591 |           0.99  |    0.145 |       1.501 |                1.698 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| BTC   |     200 |                    6 |           10.425 |              20 |      0.935 |                       0.568 |            0.734 |           1.02  |    0.855 |       1.081 |                1.964 |
| HO    |     200 |                   13 |            9.38  |              18 |      0.11  |                       0.95  |            0.72  |           0.989 |    0.07  |       1.619 |                1.982 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m volspike(20,3.0) dir=with hold 60m day | 890 | 2 | 0.84 | -1.31 | 0.08 | -0.99 / 0.33 | 0.07 / -0.35 / -0.17 | -0.17 | 0.31 | 1.00 | -0.23 | 0.00 | 1420 | NO |
| ES 2 | 15m volspike(40,4.0) dir=against hold 240m day | 504 | 2 | 0.45 | -0.51 | 0.46 | 0.42 / 1.05 | 0.11 / -0.24 / 0.10 | 0.01 | 0.15 | 0.95 | -0.11 | 0.25 | 807 | NO |
| ES 3 | 5m volspike(20,3.0) dir=against hold 240m day | 509 | 2 | 0.40 | -0.66 | 0.04 | -0.51 / 1.05 | 0.07 / -0.31 / -0.13 | -0.08 | -0.48 | 0.76 | -0.21 | 0.00 | 817 | NO |
| ES 4 | 5m volspike(40,4.0) dir=against hold 240m day | 504 | 2 | 0.37 | -0.87 | 0.24 | 0.04 / 0.93 | 0.06 / -0.31 / 0.02 | -0.04 | -0.37 | 0.85 | -0.18 | 0.25 | 809 | NO |
| ES 5 | 15m volspike(40,4.0) dir=against hold 240m all | 655 | 2 | 0.31 | -0.77 | 0.36 | 0.38 / 1.04 | 0.10 / -0.12 / -0.01 | -0.01 | 0.23 | 0.95 | -0.15 | 0.50 | 1016 | NO |
| ES 6 | 5m volspike(20,3.0) dir=with hold 120m day | 652 | 2 | 0.21 | -0.71 | -0.12 | -0.72 / 0.51 | -0.00 / -0.05 / -0.28 | -0.14 | 0.15 | 0.81 | -0.25 | 0.00 | 1018 | NO |
| ES 7 | 5m volspike(40,4.0) dir=with hold 120m day | 566 | 2 | 0.20 | -0.27 | -0.32 | -1.15 / 0.37 | -0.02 / 0.03 / -0.41 | -0.18 | -0.07 | 0.75 | -0.29 | 0.00 | 897 | NO |
| ES 8 | 15m volspike(20,5.0) dir=against hold 120m day | 513 | 2 | 0.05 | -0.67 | -0.13 | -0.25 / 0.87 | -0.01 / -0.08 / -0.15 | -0.13 | -0.14 | 0.73 | -0.27 | 0.00 | 817 | NO |
| ES 9 (diag) | 15m volspike(40,4.0) dir=with hold 60m day | 1071 | 1 | 0.93 | -1.28 | 0.49 | -0.10 / 0.05 | 0.10 / 0.05 / -0.31 | -0.13 | -0.03 | 1.00 | -0.18 | 0.00 | 1699 | diag |
| ES 10 (diag) | 15m volspike(40,4.0) dir=with hold 60m all | 1270 | 1 | 0.33 | -1.58 | 0.17 | -0.03 / -0.46 | -0.01 / 0.11 / -0.28 | -0.19 | -0.08 | 1.00 | -0.25 | 0.00 | 1983 | diag |
| NQ 1 | 5m volspike(20,5.0) dir=with hold 120m all | 755 | 2 | 1.56 | -0.24 | 0.21 | -1.25 / 1.31 | 0.28 / -0.18 / -0.56 | -0.00 | -0.05 | 0.80 | -0.21 | 0.50 | 1207 | NO |
| NQ 2 | 5m volspike(20,5.0) dir=with hold 120m day | 526 | 2 | 1.26 | -0.05 | 0.16 | -1.13 / 1.42 | 0.23 / -0.09 / -0.45 | 0.01 | -0.10 | 0.67 | -0.19 | 0.25 | 837 | NO |
| NQ 3 | 5m volspike(20,3.0) dir=with hold 120m all | 1650 | 2 | 1.20 | -0.60 | 0.26 | -0.92 / 1.22 | 0.18 / 0.23 / -0.71 | -0.06 | -0.31 | 0.91 | -0.24 | 0.00 | 2566 | NO |
| NQ 4 | 15m volspike(20,5.0) dir=with hold 60m all | 654 | 2 | 1.20 | -0.43 | -0.03 | -1.42 / 1.34 | 0.23 / 0.18 / -1.07 | -0.08 | 0.11 | 0.72 | -0.28 | 0.00 | 1021 | NO |
| NQ 5 | 15m volspike(20,3.0) dir=with hold 60m day | 818 | 2 | 1.18 | -0.60 | -0.15 | -1.65 / 1.52 | 0.15 / -0.50 / -0.77 | -0.16 | -0.16 | 0.45 | -0.36 | 0.00 | 1293 | NO |
| NQ 6 | 5m volspike(20,5.0) dir=with hold 60m all | 798 | 2 | 1.14 | -0.04 | 0.14 | -0.93 / 1.03 | 0.20 / 0.03 / -0.55 | -0.04 | 0.03 | 0.94 | -0.25 | 0.00 | 1283 | NO |
| NQ 7 | 15m volspike(20,5.0) dir=with hold 60m day | 590 | 2 | 1.14 | -0.47 | 0.00 | -1.23 / 1.13 | 0.22 / 0.24 / -1.06 | -0.08 | 0.14 | 0.64 | -0.28 | 0.00 | 936 | NO |
| NQ 8 | 15m volspike(40,4.0) dir=with hold 60m day | 912 | 2 | 0.95 | -0.73 | 0.03 | -0.99 / 1.29 | 0.12 / 0.10 / -0.92 | -0.13 | 0.17 | 0.77 | -0.33 | 0.00 | 1434 | NO |
| NQ 9 | 5m volspike(20,5.0) dir=with hold 60m day | 561 | 2 | 0.93 | 0.20 | 0.13 | -0.79 / 1.19 | 0.15 / 0.01 / -0.44 | -0.03 | 0.09 | 0.68 | -0.24 | 0.00 | 897 | NO |
| NQ 10 | 15m volspike(40,4.0) dir=with hold 60m all | 1052 | 2 | 0.93 | -0.80 | -0.11 | -1.44 / 1.09 | 0.13 / -0.15 / -0.84 | -0.14 | 0.16 | 0.80 | -0.32 | 0.00 | 1619 | NO |
| RTY 1 | 15m volspike(20,5.0) dir=against hold 180m day | 511 | 2 | 1.24 | -0.21 | 0.50 | -0.34 / 1.14 | 0.24 / -0.40 / 0.09 | 0.08 | -0.15 | 0.94 | -0.09 | 0.25 | 816 | NO |
| RTY 2 | 15m volspike(20,3.0) dir=against hold 240m day | 503 | 2 | 1.07 | 0.70 | 0.88 | 0.65 / 0.98 | 0.17 / 0.02 / 0.36 | 0.14 | 0.07 | 0.98 | -0.03 | 0.50 | 810 | NO |
| RTY 3 | 15m volspike(20,5.0) dir=against hold 240m day | 500 | 2 | 0.90 | 0.11 | 0.44 | -0.12 / 0.95 | 0.16 / -0.19 / 0.10 | 0.06 | -0.12 | 0.86 | -0.09 | 0.50 | 800 | NO |
| RTY 4 | 15m volspike(20,5.0) dir=against hold 120m day | 518 | 2 | 0.89 | -0.07 | 0.29 | -0.51 / 0.97 | 0.15 / -0.39 / 0.12 | 0.03 | -0.08 | 0.93 | -0.12 | 0.50 | 828 | NO |
| RTY 5 | 15m volspike(20,3.0) dir=against hold 180m day | 525 | 2 | 0.83 | 0.57 | 0.82 | 0.82 / 1.20 | 0.14 / 0.08 / 0.35 | 0.14 | 0.08 | 0.98 | -0.04 | 0.25 | 839 | NO |
| RTY 6 | 5m volspike(20,5.0) dir=against hold 180m day | 520 | 2 | 0.80 | -0.18 | 0.19 | -0.67 / 0.99 | 0.13 / -0.81 / 0.10 | -0.04 | -0.02 | 0.84 | -0.21 | 0.00 | 837 | NO |
| RTY 7 | 15m volspike(20,5.0) dir=against hold 180m all | 792 | 2 | 0.77 | -0.53 | 0.48 | 0.27 / 0.71 | 0.14 / -0.44 / 0.40 | 0.06 | -0.11 | 1.00 | -0.11 | 0.50 | 1209 | NO |
| RTY 8 | 5m volspike(20,5.0) dir=against hold 240m day | 499 | 2 | 0.76 | -0.10 | 0.26 | -0.58 / 1.14 | 0.13 / -0.60 / 0.03 | -0.02 | -0.11 | 0.82 | -0.18 | 0.50 | 805 | NO |
| RTY 9 | 15m volspike(20,5.0) dir=against hold 240m all | 774 | 2 | 0.67 | -0.26 | 0.40 | 0.18 / 1.04 | 0.11 / -0.27 / 0.19 | 0.02 | -0.16 | 0.96 | -0.12 | 0.75 | 1181 | NO |
| RTY 10 | 15m volspike(40,4.0) dir=against hold 240m all | 766 | 2 | 0.59 | -0.02 | 0.25 | -0.16 / 0.75 | 0.13 / -0.09 / -0.06 | 0.01 | -0.31 | 0.92 | -0.15 | 0.25 | 1175 | NO |
| GC 1 | 15m volspike(20,5.0) dir=against hold 120m day | 221 | 2 | 1.30 | -0.78 | -0.55 | -1.73 / 1.23 | 0.25 / -1.91 / -0.74 | -0.35 | 0.05 | 0.21 | -0.75 | 0.00 | 320 | NO |
| GC 2 | 5m volspike(20,3.0) dir=with hold 180m all | 1906 | 2 | 1.15 | -2.02 | 0.36 | -0.08 / 1.05 | 0.22 / -0.44 / -0.43 | -0.17 | 0.42 | 0.95 | -0.34 | 0.00 | 2985 | NO |
| GC 3 | 15m volspike(40,4.0) dir=against hold 120m all | 690 | 2 | 0.99 | -0.82 | 0.21 | -0.40 / 1.28 | 0.15 / -0.74 / -0.07 | -0.07 | -0.19 | 0.86 | -0.27 | 0.00 | 978 | NO |
| GC 4 | 15m volspike(20,5.0) dir=against hold 120m all | 370 | 2 | 0.94 | -0.88 | -0.25 | -1.04 / 1.09 | 0.19 / -0.07 / -1.05 | -0.18 | 0.00 | 0.54 | -0.48 | 0.00 | 536 | NO |
| GC 5 | 15m volspike(20,5.0) dir=against hold 60m day | 232 | 2 | 0.91 | -0.57 | -0.47 | -1.16 / 1.27 | 0.18 / -2.38 / -0.24 | -0.47 | 0.09 | 0.45 | -1.09 | 0.00 | 331 | NO |
| GC 6 | 15m volspike(40,4.0) dir=against hold 120m day | 457 | 2 | 0.89 | -0.81 | -0.20 | -0.98 / 1.22 | 0.16 / -1.65 / -0.02 | -0.21 | -0.14 | 0.52 | -0.47 | 0.00 | 675 | NO |
| GC 7 | 5m volspike(20,3.0) dir=with hold 240m all | 1540 | 2 | 0.77 | -1.57 | 0.77 | 0.90 / 1.26 | 0.12 / -0.04 / 0.11 | -0.00 | 0.17 | 0.98 | -0.20 | 0.50 | 2440 | NO |
| GC 8 | 15m volspike(20,3.0) dir=against hold 120m day | 482 | 2 | 0.75 | -0.80 | 0.17 | -0.09 / 1.13 | 0.14 / -0.90 / -0.06 | -0.09 | -0.20 | 0.79 | -0.39 | 0.00 | 752 | NO |
| GC 9 | 5m volspike(20,3.0) dir=with hold 120m all | 2280 | 2 | 0.73 | -2.48 | 0.13 | -0.19 / 1.26 | 0.12 / -1.55 / 0.09 | -0.28 | 0.48 | 0.90 | -0.56 | 0.00 | 3544 | NO |
| GC 10 | 15m volspike(20,3.0) dir=against hold 180m day | 458 | 2 | 0.59 | -0.65 | -0.29 | -0.88 / 1.25 | 0.09 / -1.66 / 0.07 | -0.22 | -0.34 | 0.42 | -0.50 | 0.00 | 707 | NO |
| CL 1 | 15m volspike(20,5.0) dir=with hold 60m day | 175 | 2 | 1.50 | -0.04 | 0.15 | -1.81 / 0.79 | 0.34 / -0.36 / -0.47 | -0.01 | -0.10 | 0.96 | -0.13 | 0.25 | 261 | NO |
| CL 2 | 15m volspike(20,5.0) dir=with hold 120m day | 166 | 2 | 1.30 | -0.18 | 0.36 | -0.79 / 0.94 | 0.23 / -0.34 / -0.25 | -0.01 | -0.02 | 0.98 | -0.15 | 0.75 | 249 | NO |
| CL 3 | 15m volspike(20,5.0) dir=with hold 240m all | 419 | 2 | 1.14 | -0.30 | 0.71 | 0.18 / 1.09 | 0.22 / -0.27 / 0.18 | 0.08 | -0.30 | 0.98 | -0.05 | 0.25 | 649 | NO |
| CL 4 | 15m volspike(20,5.0) dir=with hold 120m all | 437 | 2 | 0.79 | -0.50 | 0.11 | -0.64 / 0.94 | 0.13 / -0.35 / -0.21 | -0.12 | -0.30 | 0.93 | -0.23 | 0.00 | 675 | NO |
| CL 5 | 15m volspike(20,5.0) dir=with hold 180m all | 426 | 2 | 0.79 | -0.36 | 0.35 | -0.10 / 1.20 | 0.12 / -0.24 / -0.00 | -0.03 | -0.30 | 0.96 | -0.15 | 0.25 | 658 | NO |
| CL 6 | 15m volspike(20,5.0) dir=with hold 240m day | 157 | 2 | 0.77 | -0.00 | 0.35 | -0.07 / 1.33 | 0.13 / -0.26 / -0.03 | 0.01 | -0.02 | 0.89 | -0.15 | 0.25 | 237 | NO |
| CL 7 | 15m volspike(20,5.0) dir=with hold 180m day | 161 | 2 | 0.69 | -0.13 | 0.26 | -0.20 / 1.08 | 0.10 / -0.24 / -0.07 | -0.03 | -0.09 | 0.92 | -0.18 | 0.50 | 241 | NO |
| CL 8 | 15m volspike(40,4.0) dir=with hold 180m all | 961 | 2 | 0.48 | -0.71 | 0.08 | -0.32 / 0.85 | 0.10 / -0.14 / -0.45 | -0.17 | 0.43 | 0.98 | -0.27 | 0.00 | 1463 | NO |
| CL 9 | 15m volspike(20,3.0) dir=with hold 120m day | 580 | 2 | 0.38 | -0.28 | -0.49 | -1.67 / 0.75 | 0.09 / -0.53 / -0.54 | -0.23 | 0.19 | 0.79 | -0.34 | 0.00 | 898 | NO |
| CL 10 (diag) | 15m volspike(20,5.0) dir=with hold 60m all | 455 | 1 | 0.53 | -0.49 | -0.31 | -1.15 / 0.69 | 0.12 / -0.50 / -0.27 | -0.20 | -0.37 | 0.94 | -0.28 | 0.00 | 701 | diag |
| ZN 1 (diag) | 5m volspike(20,5.0) dir=with hold 240m day | 307 | 1 | -0.27 | -2.01 | -0.75 | -2.01 / -2.11 | -0.06 / -0.28 / -0.45 | -0.44 | 0.18 | 1.00 | -0.35 | 0.00 | 477 | diag |
| ZN 2 (diag) | 5m volspike(20,5.0) dir=with hold 180m day | 328 | 1 | -0.82 | -2.21 | -1.13 | -2.04 / -2.97 | -0.15 / -0.31 / -0.38 | -0.51 | 0.18 | 1.00 | -0.39 | 0.00 | 506 | diag |
| ZN 3 (diag) | 5m volspike(20,5.0) dir=with hold 120m day | 361 | 1 | -0.99 | -2.36 | -1.44 | -2.77 / -4.35 | -0.19 / -0.30 / -0.47 | -0.61 | 0.13 | 1.00 | -0.43 | 0.00 | 572 | diag |
| BTC 1 | 15m volspike(20,5.0) dir=with hold 240m all | 606 | 2 | 1.08 | -1.18 | 0.47 | -0.30 / 1.22 | 0.26 / -0.18 / -0.18 | 0.07 | -0.06 | 0.90 | -0.11 | 0.25 | 981 | NO |
| BTC 2 | 5m volspike(40,4.0) dir=with hold 240m all | 1261 | 2 | 0.67 | 0.12 | 0.06 | -0.78 / 1.46 | 0.13 / -0.44 / -0.01 | -0.04 | 0.06 | 0.75 | -0.19 | 0.25 | 1982 | NO |
| BTC 3 | 15m volspike(20,5.0) dir=with hold 120m all | 677 | 2 | 0.48 | -1.17 | 0.06 | -0.61 / 1.03 | 0.11 / -0.07 / -0.28 | -0.04 | 0.18 | 0.78 | -0.20 | 0.75 | 1083 | NO |
| BTC 4 | 5m volspike(20,3.0) dir=with hold 120m day | 907 | 2 | 0.48 | 1.75 | -0.27 | -1.42 / 0.92 | 0.05 / -0.07 / -0.45 | -0.13 | 0.22 | 0.62 | -0.26 | 0.00 | 1419 | NO |
| BTC 5 | 5m volspike(40,4.0) dir=against hold 240m day | 494 | 2 | 0.45 | -0.02 | 0.69 | 0.95 / 1.38 | 0.05 / 0.23 / -0.01 | 0.05 | -0.24 | 0.89 | -0.12 | 0.25 | 769 | NO |
| BTC 6 | 5m volspike(40,4.0) dir=with hold 180m all | 1437 | 2 | 0.25 | -0.00 | -0.18 | -0.76 / 0.87 | 0.03 / -0.23 / -0.13 | -0.10 | 0.32 | 0.71 | -0.23 | 0.00 | 2250 | NO |
| BTC 7 (diag) | 5m volspike(20,3.0) dir=with hold 180m all | 2078 | 1 | 0.83 | 0.70 | 0.11 | -0.84 / 0.87 | 0.10 / -0.51 / -0.22 | -0.14 | -0.07 | 0.89 | -0.23 | 0.00 | 3263 | diag |
| BTC 8 (diag) | 5m volspike(20,3.0) dir=with hold 60m day | 1255 | 1 | 0.60 | 0.69 | 0.20 | -0.32 / 0.68 | 0.10 / -0.10 / -0.33 | -0.09 | 0.41 | 0.96 | -0.20 | 0.00 | 1966 | diag |
| BTC 9 (diag) | 15m volspike(20,5.0) dir=with hold 180m all | 637 | 1 | 0.57 | -0.92 | 0.21 | -0.34 / 0.82 | 0.13 / -0.12 / -0.18 | -0.01 | 0.24 | 0.82 | -0.18 | 0.50 | 1021 | diag |
| HO 1 | 15m volspike(40,4.0) dir=against hold 240m day | 526 | 2 | 1.62 | -0.00 | 0.67 | -0.06 / 1.82 | 0.31 / 0.09 / -0.55 | 0.04 | 0.41 | 0.91 | -0.20 | 0.50 | 840 | NO |
| HO 2 | 15m volspike(20,3.0) dir=against hold 240m day | 515 | 2 | 1.32 | -0.35 | 0.87 | 0.63 / 1.28 | 0.24 / 0.12 / -0.19 | 0.10 | 0.41 | 0.97 | -0.14 | 0.25 | 823 | NO |
| HO 3 | 5m volspike(20,3.0) dir=against hold 180m day | 609 | 2 | 1.06 | -0.20 | 0.64 | 0.39 / 1.53 | 0.18 / -0.09 / -0.20 | 0.04 | 0.06 | 0.91 | -0.20 | 0.25 | 985 | NO |
| HO 4 | 15m volspike(20,3.0) dir=against hold 180m day | 531 | 2 | 0.96 | -0.35 | 1.07 | 1.27 / 1.37 | 0.17 / -0.03 / 0.26 | 0.15 | 0.39 | 1.00 | -0.06 | 0.25 | 854 | NO |
| HO 5 | 15m volspike(20,3.0) dir=against hold 180m all | 1237 | 2 | 0.92 | -0.49 | 0.87 | 0.96 / 1.30 | 0.17 / -0.05 / 0.32 | 0.15 | 0.20 | 0.98 | -0.07 | 0.00 | 1950 | NO |
| HO 6 | 5m volspike(20,3.0) dir=against hold 120m day | 1103 | 2 | 0.88 | -0.28 | -0.01 | -0.54 / 1.09 | 0.14 / 0.05 / -0.92 | -0.19 | 0.02 | 0.72 | -0.47 | 0.00 | 1764 | NO |
| HO 7 | 15m volspike(40,4.0) dir=against hold 180m day | 609 | 2 | 0.81 | -0.13 | 0.88 | 1.02 / 1.32 | 0.15 / 0.11 / -0.06 | 0.07 | 0.36 | 0.98 | -0.15 | 0.50 | 958 | NO |
| HO 8 | 5m volspike(20,3.0) dir=against hold 240m day | 528 | 2 | 0.75 | -0.08 | 0.07 | -0.51 / 1.39 | 0.09 / -0.11 / -0.69 | -0.14 | 0.36 | 0.67 | -0.35 | 0.00 | 839 | NO |
| HO 9 | 5m volspike(20,5.0) dir=against hold 240m day | 385 | 2 | 0.66 | -0.07 | 0.81 | 0.99 / 1.53 | 0.09 / -0.08 / 0.34 | 0.11 | 0.08 | 0.95 | -0.13 | 0.50 | 575 | NO |
| HO 10 | 5m volspike(20,5.0) dir=with hold 60m all | 2161 | 2 | 0.53 | -1.53 | -0.65 | -1.58 / 0.99 | 0.09 / -0.42 / -1.30 | -0.47 | 0.24 | 0.44 | -0.66 | 0.00 | 3367 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 63 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 34 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 24 |
| worst-decile corr <= +0.30 | 61 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m volspike(20,5.0) dir=with hold 240m all | clean | 1.08 | 1.87 | -102314 | -91426 | 347430 | -126121 | 2.83 | 48.6 | 1.72 | -86510 | 252958 | -102267 |
| BTC 15m volspike(20,5.0) dir=with hold 240m all | H1 | -0.34 | -0.46 | -225552 | -189685 | 677410 | -245687 | -0.20 | 50.0 | 2.64 | -87046 | 151892 | -100523 |
| BTC 15m volspike(20,5.0) dir=with hold 240m all | H2 | -0.27 | -0.38 | -120901 | -99587 | 559260 | -149449 | -0.14 | 50.0 | 2.12 | -92354 | 209644 | -97589 |
| BTC 15m volspike(20,5.0) dir=with hold 240m all | all | 0.47 | 0.72 | -140676 | -115489 | 922641 | -245687 | 0.84 | 48.8 | 1.96 | -90002 | 252958 | -102267 |
| CL 15m volspike(20,5.0) dir=with hold 240m all | clean | 1.11 | 2.13 | -90286 | -77577 | 484232 | -114918 | 2.09 | 50.5 | 1.68 | -84951 | 283201 | -92633 |
| CL 15m volspike(20,5.0) dir=with hold 240m all | H1 | -2.26 | -2.49 | -72178 | -61452 | 371530 | -78662 | -0.68 | 64.3 | 2.56 | -82123 | 157662 | -91426 |
| CL 15m volspike(20,5.0) dir=with hold 240m all | H2 | 0.76 | 1.09 | -237662 | -164678 | 564668 | -350064 | 0.67 | 50.0 | 2.47 | -87379 | 242477 | -102468 |
| CL 15m volspike(20,5.0) dir=with hold 240m all | all | 0.71 | 1.15 | -125868 | -98564 | 564668 | -350064 | 2.02 | 53.0 | 2.00 | -86971 | 283201 | -102468 |
| ES 15m volspike(40,4.0) dir=against hold 240m day | clean | 0.50 | 0.79 | -123783 | -99928 | 512993 | -160067 | 0.88 | 50.5 | 1.57 | -87573 | 256662 | -98077 |
| ES 15m volspike(40,4.0) dir=against hold 240m day | H1 | -0.52 | -0.74 | -144245 | -133816 | 315830 | -163874 | -0.52 | 57.1 | 2.59 | -77217 | 152007 | -81377 |
| ES 15m volspike(40,4.0) dir=against hold 240m day | H2 | 1.25 | 2.08 | -119024 | -103023 | 294123 | -142460 | 1.52 | 44.4 | 2.39 | -93821 | 248506 | -96533 |
| ES 15m volspike(40,4.0) dir=against hold 240m day | all | 0.46 | 0.72 | -135190 | -112784 | 512993 | -163874 | 1.43 | 50.6 | 1.92 | -89312 | 256662 | -98077 |
| GC 5m volspike(20,3.0) dir=with hold 240m all | clean | 0.76 | 1.38 | -99409 | -82981 | 592210 | -148584 | 1.16 | 50.5 | 1.58 | -90804 | 309072 | -107028 |
| GC 5m volspike(20,3.0) dir=with hold 240m all | H1 | -0.31 | -0.45 | -269721 | -229738 | 967192 | -337478 | -0.18 | 57.1 | 2.78 | -67332 | 184693 | -73251 |
| GC 5m volspike(20,3.0) dir=with hold 240m all | H2 | 1.70 | 3.22 | -248712 | -239613 | 429225 | -251865 | 3.34 | 44.4 | 2.40 | -106122 | 232510 | -108517 |
| GC 5m volspike(20,3.0) dir=with hold 240m all | all | 0.77 | 1.33 | -215619 | -167454 | 967192 | -337478 | 2.02 | 50.6 | 1.94 | -95035 | 309072 | -108517 |
| HO 15m volspike(20,3.0) dir=against hold 180m all | clean | 0.83 | 1.33 | -112419 | -95644 | 367749 | -177599 | 2.06 | 48.6 | 1.63 | -85090 | 299601 | -93608 |
| HO 15m volspike(20,3.0) dir=against hold 180m all | H1 | 0.15 | 0.21 | -81980 | -67627 | 267414 | -100616 | 0.08 | 50.0 | 2.78 | -78984 | 162545 | -79295 |
| HO 15m volspike(20,3.0) dir=against hold 180m all | H2 | 1.28 | 2.40 | -222262 | -179267 | 439618 | -255530 | 1.95 | 41.7 | 2.62 | -89751 | 197938 | -102721 |
| HO 15m volspike(20,3.0) dir=against hold 180m all | all | 0.87 | 1.51 | -144453 | -118335 | 472719 | -255530 | 3.46 | 47.0 | 2.04 | -85750 | 299601 | -102721 |
| NQ 5m volspike(20,5.0) dir=with hold 120m day | clean | 1.24 | 2.12 | -107405 | -94535 | 333094 | -148387 | 3.39 | 42.9 | 1.69 | -82743 | 222907 | -97394 |
| NQ 5m volspike(20,5.0) dir=with hold 120m day | H1 | -0.68 | -1.03 | -106223 | -105292 | 696856 | -106368 | -0.31 | 60.7 | 2.73 | -64248 | 158482 | -71082 |
| NQ 5m volspike(20,5.0) dir=with hold 120m day | H2 | -1.43 | -1.71 | -189370 | -173982 | 899066 | -207584 | -0.71 | 50.0 | 1.84 | -82597 | 243708 | -88475 |
| NQ 5m volspike(20,5.0) dir=with hold 120m day | all | 0.16 | 0.24 | -147953 | -125341 | 1180023 | -207584 | 0.24 | 47.0 | 1.88 | -81950 | 243708 | -97394 |
| RTY 15m volspike(20,3.0) dir=against hold 240m day | clean | 1.08 | 1.98 | -95801 | -84758 | 551356 | -114822 | 1.77 | 50.5 | 1.63 | -85668 | 236777 | -94479 |
| RTY 15m volspike(20,3.0) dir=against hold 240m day | H1 | -0.29 | -0.38 | -150098 | -140627 | 390247 | -163984 | -0.22 | 46.4 | 2.84 | -68398 | 126020 | -70637 |
| RTY 15m volspike(20,3.0) dir=against hold 240m day | H2 | 1.25 | 2.35 | -142037 | -125038 | 436985 | -165421 | 1.33 | 44.4 | 2.65 | -101158 | 212664 | -101758 |
| RTY 15m volspike(20,3.0) dir=against hold 240m day | all | 0.88 | 1.49 | -128177 | -109922 | 551356 | -165421 | 2.68 | 48.2 | 2.03 | -88407 | 236777 | -101758 |
| ZN 5m volspike(20,5.0) dir=with hold 240m day (diag) | clean | -0.23 | -0.33 | -117767 | -103040 | 970344 | -144772 | -0.22 | 51.4 | 1.40 | -89540 | 284322 | -106013 |
| ZN 5m volspike(20,5.0) dir=with hold 240m day (diag) | H1 | -1.19 | -1.69 | -53849 | -50298 | 252806 | -57706 | -0.59 | 67.9 | 2.55 | -84591 | 169637 | -88286 |
| ZN 5m volspike(20,5.0) dir=with hold 240m day (diag) | H2 | -2.49 | -2.63 | -145808 | -103830 | 748924 | -215254 | -0.84 | 63.9 | 1.84 | -88219 | 215815 | -90780 |
| ZN 5m volspike(20,5.0) dir=with hold 240m day (diag) | all | -0.75 | -1.01 | -122098 | -101199 | 1514806 | -215254 | -0.65 | 57.1 | 1.68 | -89860 | 284322 | -106013 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m volspike(40,4.0) dir=against hold 240m day | -21.8 | -3.6 | 8.6 | 29.0 | -4.4 / 12.1 | 22.7 / 25.0 | NO |
| NQ 5m volspike(20,5.0) dir=with hold 120m day | -26.9 | -2.3 | 20.7 | 23.3 | -3.2 / 22.1 | 36.0 / 36.5 | NO |
| RTY 15m volspike(20,3.0) dir=against hold 240m day | -13.5 | -8.0 | 9.9 | 34.7 | 2.1 / 13.6 | 32.0 / 35.8 | NO |
| GC 5m volspike(20,3.0) dir=with hold 240m all | -8.2 | -30.2 | -17.3 | 14.5 | -20.5 / 6.2 | -34.5 / -5.7 | NO |
| CL 15m volspike(20,5.0) dir=with hold 240m all | -17.3 | -11.2 | 14.0 | 27.4 | 10.3 / 17.4 | 4.8 / 21.3 | NO |
| ZN 5m volspike(20,5.0) dir=with hold 240m day (diag) | -41.0 | -18.0 | 7.2 | 4.2 | -18.9 / 8.7 | 10.8 / 16.5 | NO |
| BTC 15m volspike(20,5.0) dir=with hold 240m all | -21.4 | -11.2 | 8.5 | 31.4 | -12.1 / 14.0 | -14.0 / 5.7 | NO |
| HO 15m volspike(20,3.0) dir=against hold 180m all | -11.7 | -6.7 | 8.4 | 19.6 | 6.5 / 16.8 | 27.9 / 27.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m volspike(20,3.0) dir=with hold 60m day | negative pre-2023 | 4231 | -9.8 | -39.2 | -24.8 | 29.4 | -0.33 / -1.31 / -0.83 | 60.8 / 31.4 |
| ES 2 15m volspike(40,4.0) dir=against hold 240m day | negative pre-2023 | 2626 | -0.4 | -29.8 | -15.5 | 29.4 | -0.00 / -0.51 / -0.26 | 76.3 / 46.9 |
| ES 3 5m volspike(20,3.0) dir=against hold 240m day | negative pre-2023 | 2656 | -13.2 | -42.6 | -28.3 | 29.4 | -0.20 / -0.66 / -0.44 | 70.2 / 40.8 |
| ES 4 5m volspike(40,4.0) dir=against hold 240m day | negative pre-2023 | 2629 | -26.0 | -55.4 | -41.1 | 29.4 | -0.41 / -0.87 / -0.64 | 68.3 / 38.9 |
| ES 5 15m volspike(40,4.0) dir=against hold 240m all | negative pre-2023 | 3787 | -3.6 | -32.9 | -18.1 | 29.4 | -0.08 / -0.77 / -0.43 | 55.4 / 26.1 |
| ES 6 5m volspike(20,3.0) dir=with hold 120m day | negative pre-2023 | 3372 | -1.4 | -30.8 | -16.4 | 29.4 | -0.03 / -0.71 / -0.38 | 44.4 / 15.1 |
| ES 7 5m volspike(40,4.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 2927 | 16.4 | -13.0 | 1.3 | 29.4 | 0.34 / -0.27 / 0.03 | 42.0 / 12.6 |
| ES 8 15m volspike(20,5.0) dir=against hold 120m day | negative pre-2023 | 2660 | -1.6 | -31.0 | -16.7 | 29.4 | -0.04 / -0.67 / -0.36 | 28.0 / -1.3 |
| ES 9 (diag) 15m volspike(40,4.0) dir=with hold 60m day | negative pre-2023 | 5068 | -2.0 | -31.4 | -17.0 | 29.4 | -0.08 / -1.28 / -0.69 | 61.2 / 31.8 |
| ES 10 (diag) 15m volspike(40,4.0) dir=with hold 60m all | negative pre-2023 | 6705 | -0.6 | -30.0 | -15.1 | 29.4 | -0.03 / -1.58 / -0.80 | 39.1 / 9.7 |
| NQ 1 5m volspike(20,5.0) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 5959 | 4.3 | -10.1 | -0.9 | 14.4 | 0.10 / -0.24 / -0.02 | 181.4 / 167.0 |
| NQ 2 5m volspike(20,5.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 2801 | 10.4 | -4.0 | 4.6 | 14.4 | 0.12 / -0.05 / 0.05 | 200.4 / 186.0 |
| NQ 3 5m volspike(20,3.0) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 10813 | 0.3 | -14.1 | -5.2 | 14.4 | 0.01 / -0.60 / -0.22 | 81.1 / 66.8 |
| NQ 4 15m volspike(20,5.0) dir=with hold 60m all | negative pre-2023 | 4249 | -2.2 | -16.6 | -7.4 | 14.4 | -0.05 / -0.43 / -0.19 | 125.5 / 111.2 |
| NQ 5 15m volspike(20,3.0) dir=with hold 60m day | negative pre-2023 | 4193 | -14.9 | -29.2 | -20.5 | 14.4 | -0.31 / -0.60 / -0.42 | 99.7 / 85.3 |
| NQ 6 5m volspike(20,5.0) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 6677 | 13.3 | -1.1 | 8.2 | 14.4 | 0.47 / -0.04 / 0.29 | 94.3 / 80.0 |
| NQ 7 15m volspike(20,5.0) dir=with hold 60m day | negative pre-2023 | 2939 | -10.4 | -24.7 | -16.1 | 14.4 | -0.19 / -0.47 / -0.30 | 129.2 / 114.8 |
| NQ 8 15m volspike(40,4.0) dir=with hold 60m day | negative pre-2023 | 4913 | -15.5 | -29.8 | -21.0 | 14.4 | -0.38 / -0.73 / -0.51 | 88.4 / 74.0 |
| NQ 9 5m volspike(20,5.0) dir=with hold 60m day | positive pre-2023 | 3120 | 25.6 | 11.2 | 19.9 | 14.4 | 0.45 / 0.20 / 0.35 | 105.5 / 91.1 |
| NQ 10 15m volspike(40,4.0) dir=with hold 60m all | negative pre-2023 | 6468 | -11.2 | -25.5 | -16.4 | 14.4 | -0.35 / -0.80 / -0.52 | 83.2 / 68.9 |
| RTY 1 15m volspike(20,5.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 1522 | 3.9 | -10.4 | -8.2 | 14.4 | 0.08 / -0.21 / -0.17 | 77.6 / 63.3 |
| RTY 2 15m volspike(20,3.0) dir=against hold 240m day | positive pre-2023 | 1501 | 54.3 | 39.9 | 42.2 | 14.4 | 0.95 / 0.70 / 0.74 | 75.3 / 60.9 |
| RTY 3 15m volspike(20,5.0) dir=against hold 240m day | positive pre-2023 | 1493 | 20.1 | 5.7 | 8.0 | 14.4 | 0.37 / 0.11 / 0.15 | 66.4 / 52.1 |
| RTY 4 15m volspike(20,5.0) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 1534 | 11.1 | -3.2 | -1.0 | 14.4 | 0.26 / -0.07 / -0.02 | 58.8 / 44.4 |
| RTY 5 15m volspike(20,3.0) dir=against hold 180m day | positive pre-2023 | 1558 | 44.6 | 30.2 | 32.5 | 14.4 | 0.85 / 0.57 / 0.62 | 56.3 / 41.9 |
| RTY 6 5m volspike(20,5.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 1543 | 5.1 | -9.3 | -7.0 | 14.4 | 0.10 / -0.18 / -0.13 | 58.8 / 44.5 |
| RTY 7 15m volspike(20,5.0) dir=against hold 180m all | negative pre-2023 | 2437 | -2.8 | -17.2 | -14.9 | 14.4 | -0.09 / -0.53 / -0.46 | 36.4 / 22.0 |
| RTY 8 5m volspike(20,5.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 1499 | 8.5 | -5.9 | -3.6 | 14.4 | 0.15 / -0.10 / -0.06 | 68.9 / 54.5 |
| RTY 9 15m volspike(20,5.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 2380 | 5.3 | -9.1 | -6.9 | 14.4 | 0.15 / -0.26 / -0.19 | 35.4 / 21.0 |
| RTY 10 15m volspike(40,4.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 2185 | 13.8 | -0.6 | 1.7 | 14.4 | 0.37 / -0.02 / 0.04 | 36.8 / 22.4 |
| GC 1 15m volspike(20,5.0) dir=against hold 120m day | negative pre-2023 | 1357 | -23.9 | -48.3 | -38.3 | 24.4 | -0.39 / -0.78 / -0.62 | 168.9 / 144.6 |
| GC 2 5m volspike(20,3.0) dir=with hold 180m all | negative pre-2023 | 10649 | -10.2 | -34.6 | -24.7 | 24.4 | -0.60 / -2.02 / -1.44 | 56.2 / 31.8 |
| GC 3 15m volspike(40,4.0) dir=against hold 120m all | negative pre-2023 | 4558 | -0.2 | -24.5 | -14.6 | 24.4 | -0.01 / -0.82 / -0.49 | 79.2 / 54.9 |
| GC 4 15m volspike(20,5.0) dir=against hold 120m all | negative pre-2023 | 2764 | -7.9 | -32.3 | -22.0 | 24.4 | -0.21 / -0.88 / -0.60 | 91.9 / 67.6 |
| GC 5 15m volspike(20,5.0) dir=against hold 60m day | negative pre-2023 | 1447 | -2.9 | -27.3 | -17.3 | 24.4 | -0.06 / -0.57 / -0.36 | 101.6 / 77.2 |
| GC 6 15m volspike(40,4.0) dir=against hold 120m day | negative pre-2023 | 2616 | -14.0 | -38.3 | -28.5 | 24.4 | -0.29 / -0.81 / -0.60 | 85.3 / 60.9 |
| GC 7 5m volspike(20,3.0) dir=with hold 240m all | negative pre-2023 | 8508 | -10.4 | -34.8 | -24.9 | 24.4 | -0.47 / -1.57 / -1.12 | 54.5 / 30.1 |
| GC 8 15m volspike(20,3.0) dir=against hold 120m day | negative pre-2023 | 2724 | -13.1 | -37.4 | -27.5 | 24.4 | -0.28 / -0.80 / -0.59 | 75.2 / 50.8 |
| GC 9 5m volspike(20,3.0) dir=with hold 120m all | negative pre-2023 | 13015 | -6.5 | -30.9 | -20.9 | 24.4 | -0.53 / -2.48 / -1.69 | 41.4 / 17.0 |
| GC 10 15m volspike(20,3.0) dir=against hold 180m day | negative pre-2023 | 2461 | -12.0 | -36.4 | -26.5 | 24.4 | -0.21 / -0.65 / -0.48 | 66.7 / 42.4 |
| CL 1 15m volspike(20,5.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 1683 | 22.7 | -1.6 | -0.5 | 24.4 | 0.60 / -0.04 / -0.01 | 100.1 / 75.7 |
| CL 2 15m volspike(20,5.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 1512 | 14.0 | -10.4 | -9.0 | 24.4 | 0.25 / -0.18 / -0.16 | 112.7 / 88.3 |
| CL 3 15m volspike(20,5.0) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 3006 | 12.2 | -12.2 | -10.0 | 24.4 | 0.30 / -0.30 / -0.24 | 86.4 / 62.0 |
| CL 4 15m volspike(20,5.0) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 3233 | 8.9 | -15.5 | -13.5 | 24.4 | 0.29 / -0.50 / -0.43 | 50.4 / 26.0 |
| CL 5 15m volspike(20,5.0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 3064 | 10.6 | -13.8 | -11.6 | 24.4 | 0.28 / -0.36 / -0.31 | 58.5 / 34.1 |
| CL 6 15m volspike(20,5.0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 1419 | 24.1 | -0.3 | 1.2 | 24.4 | 0.32 / -0.00 / 0.02 | 98.6 / 74.2 |
| CL 7 15m volspike(20,5.0) dir=with hold 180m day | gross-positive, cost-negative pre-2023 | 1424 | 14.7 | -9.6 | -8.2 | 24.4 | 0.21 / -0.13 / -0.11 | 83.7 / 59.3 |
| CL 8 15m volspike(40,4.0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 5208 | 3.5 | -20.9 | -18.5 | 24.4 | 0.11 / -0.71 / -0.63 | 39.5 / 15.1 |
| CL 9 15m volspike(20,3.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 3330 | 14.1 | -10.2 | -8.1 | 24.4 | 0.40 / -0.28 / -0.22 | 42.3 / 18.0 |
| CL 10 (diag) 15m volspike(20,5.0) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 3609 | 13.7 | -10.6 | -8.8 | 24.4 | 0.65 / -0.49 / -0.40 | 37.1 / 12.8 |
| ZN 1 (diag) 5m volspike(20,5.0) dir=with hold 240m day | negative pre-2023 | 1344 | -9.4 | -45.0 | -50.0 | 35.6 | -0.43 / -2.01 / -2.23 | 30.5 / -5.1 |
| ZN 2 (diag) 5m volspike(20,5.0) dir=with hold 180m day | negative pre-2023 | 1505 | -6.1 | -41.7 | -46.7 | 35.6 | -0.33 / -2.21 / -2.47 | 19.8 / -15.8 |
| ZN 3 (diag) 5m volspike(20,5.0) dir=with hold 120m day | negative pre-2023 | 1718 | -4.0 | -39.6 | -44.6 | 35.6 | -0.24 / -2.36 / -2.64 | 18.3 / -17.3 |
| BTC 1 15m volspike(20,5.0) dir=with hold 240m all | negative pre-2023 | 512 | -136.7 | -191.1 | -158.6 | 54.4 | -0.84 / -1.18 / -0.97 | 354.7 / 300.4 |
| BTC 2 5m volspike(40,4.0) dir=with hold 240m all | positive pre-2023 | 975 | 61.4 | 7.0 | 39.4 | 54.4 | 0.81 / 0.12 / 0.53 | 167.9 / 113.6 |
| BTC 3 15m volspike(20,5.0) dir=with hold 120m all | negative pre-2023 | 608 | -70.9 | -125.2 | -92.9 | 54.4 | -0.66 / -1.17 / -0.87 | 167.0 / 112.6 |
| BTC 4 5m volspike(20,3.0) dir=with hold 120m day | positive pre-2023 | 747 | 202.3 | 148.0 | 180.4 | 54.4 | 2.39 / 1.75 / 2.14 | 135.1 / 80.7 |
| BTC 5 5m volspike(40,4.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 370 | 53.9 | -0.5 | 32.0 | 54.4 | 0.32 / -0.02 / 0.18 | 231.8 / 177.4 |
| BTC 6 5m volspike(40,4.0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 1131 | 52.0 | -2.3 | 30.0 | 54.4 | 0.75 / -0.00 / 0.44 | 83.2 / 28.9 |
| BTC 7 (diag) 5m volspike(20,3.0) dir=with hold 180m all | positive pre-2023 | 1586 | 88.9 | 34.6 | 67.0 | 54.4 | 1.79 / 0.70 / 1.35 | 134.7 / 80.3 |
| BTC 8 (diag) 5m volspike(20,3.0) dir=with hold 60m day | positive pre-2023 | 1024 | 101.6 | 47.2 | 79.7 | 54.4 | 1.49 / 0.69 / 1.17 | 118.3 / 64.0 |
| BTC 9 (diag) 15m volspike(20,5.0) dir=with hold 180m all | negative pre-2023 | 546 | -80.6 | -134.9 | -102.5 | 54.4 | -0.54 / -0.92 / -0.69 | 212.6 / 158.2 |
| HO 1 15m volspike(40,4.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2690 | 13.0 | 0.3 | 1.8 | 12.8 | 0.15 / -0.00 / 0.01 | 139.9 / 127.1 |
| HO 2 15m volspike(20,3.0) dir=against hold 240m day | negative pre-2023 | 2660 | -14.8 | -27.5 | -26.1 | 12.8 | -0.19 / -0.35 / -0.33 | 115.4 / 102.7 |
| HO 3 5m volspike(20,3.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 3169 | 1.0 | -11.8 | -10.4 | 12.8 | 0.01 / -0.20 / -0.17 | 74.8 / 62.1 |
| HO 4 15m volspike(20,3.0) dir=against hold 180m day | negative pre-2023 | 2823 | -10.7 | -23.5 | -22.0 | 12.8 | -0.16 / -0.35 / -0.33 | 78.3 / 65.6 |
| HO 5 15m volspike(20,3.0) dir=against hold 180m all | negative pre-2023 | 6570 | -5.7 | -18.5 | -17.0 | 12.8 | -0.16 / -0.49 / -0.45 | 47.8 / 35.1 |
| HO 6 5m volspike(20,3.0) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 5934 | 4.2 | -8.6 | -7.1 | 12.8 | 0.14 / -0.28 / -0.23 | 39.3 / 26.6 |
| HO 7 15m volspike(40,4.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 3295 | 4.9 | -7.9 | -6.5 | 12.8 | 0.07 / -0.13 / -0.11 | 63.0 / 50.2 |
| HO 8 5m volspike(20,3.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2721 | 7.4 | -5.3 | -3.9 | 12.8 | 0.09 / -0.08 / -0.06 | 68.6 / 55.8 |
| HO 9 5m volspike(20,5.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2063 | 5.8 | -6.9 | -5.5 | 12.8 | 0.06 / -0.07 / -0.06 | 70.2 / 57.5 |
| HO 10 5m volspike(20,5.0) dir=with hold 60m all | negative pre-2023 | 11312 | -6.4 | -19.2 | -17.7 | 12.8 | -0.51 / -1.53 / -1.40 | 20.0 / 7.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 6 cells pass the clean rule against a replicate mean of 10.4 (p(count) = 0.94, p(top) = 0.85); CL: 9 cells pass the clean rule against a replicate mean of 3.0 (p(count) = 0.00, p(top) = 0.14); ES: 8 cells pass the clean rule against a replicate mean of 4.0 (p(count) = 0.03, p(top) = 0.90); GC: 18 cells pass the clean rule against a replicate mean of 6.2 (p(count) = 0.00, p(top) = 0.07); HO: 13 cells pass the clean rule against a replicate mean of 9.4 (p(count) = 0.11, p(top) = 0.07); NQ: 30 cells pass the clean rule against a replicate mean of 15.0 (p(count) = 0.00, p(top) = 0.05); RTY: 17 cells pass the clean rule against a replicate mean of 5.8 (p(count) = 0.00, p(top) = 0.12); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 63 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.18 (HO 15m volspike(20,3.0) dir=against hold 180m all); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 5; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 29, 'gross-positive, cost-negative pre-2023': 28, 'positive pre-2023': 6}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q15.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q15/ (`Q15_CO_all_selected_scored.csv`).

DONE Q15
