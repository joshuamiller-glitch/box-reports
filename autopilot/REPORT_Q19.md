# REPORT Q19 - Q19: EMA distance z (in bar ATRs) cross-out, with/against, time exit

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 44 selected cells (+17 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.36; best pair-window standalone Sharpe +1.45.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: EMA distance z (in bar ATRs) cross-out, with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        23 |               2.26  |                2 |         10 |            0 |
| CL    |      96 |         96 |         0 |               0.526 |                1 |          0 |            3 |
| ES    |      96 |         96 |         8 |               1.076 |                2 |          8 |            2 |
| GC    |      96 |         96 |         3 |               1.368 |                2 |          3 |            3 |
| HO    |      96 |         96 |         7 |               1.16  |                2 |          7 |            3 |
| NQ    |      96 |         96 |        20 |               1.229 |                2 |         10 |            0 |
| RTY   |      96 |         96 |         6 |               1.337 |                2 |          6 |            3 |
| ZN    |      96 |         96 |         0 |              -1.341 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    8 |            4.38  |              11 |      0.09  |                       0.47  |            0.631 |           0.944 |    0.805 |       1.076 |                1.676 |
| NQ    |     200 |                   20 |           15.135 |              24 |      0.115 |                       0.911 |            0.891 |           1.155 |    0.43  |       1.229 |                1.929 |
| RTY   |     200 |                    6 |            6.265 |              14 |      0.58  |                       0.799 |            0.645 |           0.895 |    0.17  |       1.337 |                1.736 |
| GC    |     200 |                    3 |            4.97  |              11 |      0.875 |                       0.97  |            0.624 |           0.955 |    0.05  |       1.171 |                1.693 |
| CL    |     200 |                    0 |            2.875 |               9 |      1     |                     nan     |            0.616 |           1.12  |  nan     |     nan     |                1.583 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| BTC   |     200 |                   23 |           10.445 |              20 |      0     |                       1.267 |            0.726 |           0.996 |    0     |       2.26  |                1.884 |
| HO    |     200 |                    7 |            9.645 |              18 |      0.88  |                       0.472 |            0.717 |           0.975 |    0.975 |       1.16  |                1.933 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m emaz(100,3.0) dir=against hold 180m day | 403 | 2 | 1.08 | -0.38 | 0.76 | 0.43 / 0.83 | 0.26 / -0.32 / 0.31 | 0.13 | -0.29 | 1.00 | -0.01 | 0.00 | 643 | NO |
| ES 2 | 5m emaz(50,3.0) dir=against hold 240m day | 467 | 2 | 0.69 | -1.08 | 0.42 | 0.25 / 1.21 | 0.14 / -0.26 / 0.16 | 0.05 | -0.20 | 0.87 | -0.13 | 0.25 | 736 | NO |
| ES 3 | 15m emaz(100,3.0) dir=against hold 240m all | 796 | 2 | 0.68 | -1.10 | 0.50 | 0.16 / 0.70 | 0.10 / -0.26 / 0.18 | -0.01 | 0.35 | 0.99 | -0.09 | 0.25 | 1321 | NO |
| ES 4 | 15m emaz(50,2.0) dir=against hold 240m all | 1108 | 2 | 0.40 | -1.25 | 0.27 | 0.21 / 0.90 | 0.17 / -0.46 / 0.47 | 0.04 | 0.06 | 0.94 | -0.06 | 0.50 | 1792 | NO |
| ES 5 | 15m emaz(100,3.0) dir=against hold 240m day | 337 | 2 | 0.26 | -0.45 | 0.12 | -0.11 / 1.39 | 0.03 / -0.58 / 0.21 | -0.05 | 0.34 | 0.80 | -0.19 | 0.00 | 539 | NO |
| ES 6 | 15m emaz(100,3.0) dir=against hold 120m day | 502 | 2 | 0.24 | -0.73 | 0.55 | 0.96 / 0.89 | 0.10 / -0.11 / 0.36 | 0.07 | 0.06 | 0.99 | -0.05 | 0.25 | 791 | NO |
| ES 7 | 5m emaz(100,3.0) dir=with hold 120m day | 864 | 2 | 0.23 | -0.99 | 0.32 | 0.36 / 0.79 | -0.04 / 0.31 / -0.28 | -0.13 | 0.06 | 0.98 | -0.22 | 0.00 | 1371 | NO |
| ES 8 | 15m emaz(50,2.0) dir=against hold 240m day | 417 | 2 | 0.18 | -0.55 | 0.12 | 0.14 / 1.36 | 0.08 / -0.60 / 0.41 | 0.02 | 0.03 | 0.80 | -0.15 | 0.25 | 673 | NO |
| ES 9 (diag) | 15m emaz(50,3.0) dir=with hold 120m day | 448 | 1 | 0.68 | -0.57 | -0.23 | -1.46 / 1.02 | 0.01 / -0.35 / -0.62 | -0.25 | -0.52 | 0.71 | -0.40 | 0.00 | 724 | diag |
| ES 10 (diag) | 5m emaz(50,2.0) dir=with hold 120m day | 1127 | 1 | 0.45 | -1.19 | 0.27 | -0.09 / 0.63 | 0.02 / 0.03 / -0.21 | -0.13 | 0.13 | 0.97 | -0.20 | 0.00 | 1788 | diag |
| NQ 1 | 5m emaz(100,3.0) dir=against hold 240m day | 490 | 2 | 1.23 | -0.04 | 0.87 | 0.64 / 1.25 | 0.28 / -0.56 / 0.68 | 0.25 | 0.12 | 0.96 | 0.00 | 0.25 | 795 | NO |
| NQ 2 | 5m emaz(50,3.0) dir=against hold 180m day | 620 | 2 | 1.14 | -0.62 | 1.18 | 1.30 / 1.15 | 0.30 / -0.11 / 0.78 | 0.35 | 0.16 | 0.98 | 0.14 | 0.25 | 982 | NO |
| NQ 3 | 15m emaz(50,2.0) dir=against hold 240m all | 1093 | 2 | 0.99 | -0.64 | 0.54 | 0.08 / 1.07 | 0.33 / -0.41 / 0.40 | 0.23 | 0.54 | 0.85 | 0.01 | 0.00 | 1785 | NO |
| NQ 4 | 15m emaz(50,2.0) dir=against hold 240m day | 425 | 2 | 0.97 | -0.38 | 0.86 | 0.84 / 1.44 | 0.24 / -0.72 / 0.87 | 0.24 | 0.43 | 0.96 | 0.01 | 0.50 | 689 | NO |
| NQ 5 | 15m emaz(100,3.0) dir=against hold 120m all | 1059 | 2 | 0.95 | -0.38 | 0.01 | -1.18 / 1.28 | 0.28 / 0.03 / -0.63 | 0.02 | 0.14 | 0.71 | -0.16 | 0.50 | 1737 | NO |
| NQ 6 | 5m emaz(100,3.0) dir=against hold 180m day | 660 | 2 | 0.90 | -0.47 | 0.79 | 0.72 / 1.52 | 0.21 / -0.47 / 0.66 | 0.21 | 0.36 | 0.92 | 0.00 | 0.75 | 1057 | NO |
| NQ 7 | 15m emaz(100,3.0) dir=against hold 120m day | 485 | 2 | 0.86 | -0.04 | 0.66 | 0.42 / 1.34 | 0.23 / 0.24 / 0.01 | 0.18 | 0.39 | 0.91 | -0.00 | 0.00 | 767 | NO |
| NQ 8 | 15m emaz(50,2.0) dir=against hold 180m all | 1293 | 2 | 0.73 | -0.76 | 0.19 | -0.35 / 1.48 | 0.26 / -0.88 / 0.53 | 0.13 | 0.21 | 0.76 | -0.08 | 0.25 | 2094 | NO |
| NQ 9 | 5m emaz(100,3.0) dir=against hold 240m all | 1495 | 2 | 0.70 | -0.26 | 0.23 | -0.15 / 1.37 | 0.22 / -0.22 / 0.21 | 0.14 | 0.24 | 0.74 | -0.10 | 0.50 | 2430 | NO |
| NQ 10 | 15m emaz(50,3.0) dir=against hold 180m day | 375 | 2 | 0.63 | -0.23 | 0.36 | 0.08 / 1.61 | 0.16 / -0.19 / 0.15 | 0.10 | 0.12 | 0.78 | -0.10 | 0.50 | 615 | NO |
| RTY 1 | 5m emaz(50,3.0) dir=against hold 240m day | 479 | 2 | 1.34 | 0.20 | 0.28 | -0.90 / 1.14 | 0.21 / -0.77 / -0.22 | -0.07 | -0.18 | 0.84 | -0.25 | 0.00 | 767 | NO |
| RTY 2 | 15m emaz(50,3.0) dir=against hold 240m day | 334 | 2 | 1.06 | -0.25 | 0.82 | 0.53 / 1.64 | 0.18 / -0.43 / 0.30 | 0.10 | -0.46 | 0.93 | -0.08 | 1.00 | 547 | NO |
| RTY 3 | 15m emaz(50,3.0) dir=against hold 180m day | 396 | 2 | 0.83 | -0.19 | 0.89 | 0.89 / 1.55 | 0.14 / -0.35 / 0.56 | 0.12 | -0.58 | 0.99 | -0.04 | 0.25 | 650 | NO |
| RTY 4 | 5m emaz(50,3.0) dir=against hold 120m all | 2400 | 2 | 0.70 | -0.23 | -0.10 | -0.98 / 0.35 | 0.07 / -0.89 / 0.11 | -0.24 | -0.45 | 0.98 | -0.28 | 0.00 | 3805 | NO |
| RTY 5 | 5m emaz(50,2.0) dir=against hold 180m day | 823 | 2 | 0.52 | -0.18 | 0.10 | -0.50 / 1.17 | 0.01 / -0.20 / -0.09 | -0.10 | 0.08 | 0.79 | -0.24 | 0.00 | 1313 | NO |
| RTY 6 | 15m emaz(100,3.0) dir=against hold 180m day | 414 | 2 | 0.34 | 0.60 | 0.73 | 0.92 / 1.01 | 0.08 / -0.16 / 0.43 | 0.08 | -0.54 | 0.99 | -0.09 | 0.25 | 655 | NO |
| RTY 7 (diag) | 5m emaz(100,3.0) dir=against hold 240m day | 519 | 1 | 0.96 | 0.27 | 0.57 | -0.06 / 1.14 | 0.12 / -0.15 / -0.03 | 0.01 | -0.27 | 0.96 | -0.14 | 1.00 | 832 | diag |
| RTY 8 (diag) | 5m emaz(50,3.0) dir=against hold 240m all | 1542 | 1 | 0.94 | -0.43 | 0.62 | 0.11 / 0.92 | 0.18 / -0.35 / 0.34 | 0.05 | -0.35 | 1.00 | -0.05 | 0.25 | 2449 | diag |
| RTY 9 (diag) | 5m emaz(50,2.0) dir=against hold 240m day | 577 | 1 | 0.88 | -0.07 | 0.52 | -0.03 / 1.10 | 0.10 / -0.09 / 0.01 | 0.01 | -0.25 | 0.95 | -0.14 | 0.25 | 923 | diag |
| GC 1 | 15m emaz(50,2.0) dir=with hold 180m all | 1362 | 2 | 1.17 | -1.01 | 0.36 | -0.11 / 0.84 | 0.13 / 0.89 / -0.66 | -0.09 | 0.12 | 0.98 | -0.30 | 0.00 | 2183 | NO |
| GC 2 | 5m emaz(100,3.0) dir=with hold 240m all | 1533 | 2 | 1.07 | -0.93 | -0.08 | -0.83 / 1.12 | 0.08 / 0.87 / -1.31 | -0.26 | 0.43 | 0.72 | -0.44 | 0.00 | 2475 | NO |
| GC 3 | 5m emaz(50,2.0) dir=with hold 180m all | 2379 | 2 | 0.67 | -1.67 | 0.23 | 0.01 / 1.08 | 0.06 / 1.01 / -0.82 | -0.22 | 0.29 | 0.86 | -0.40 | 0.00 | 3826 | NO |
| GC 4 (diag) | 15m emaz(100,3.0) dir=with hold 180m all | 978 | 1 | 1.37 | -0.75 | 0.39 | -0.27 / 1.08 | 0.18 / -0.60 / -0.27 | -0.11 | -0.20 | 0.93 | -0.33 | 0.00 | 1549 | diag |
| GC 5 (diag) | 5m emaz(50,2.0) dir=with hold 240m all | 1905 | 1 | 1.26 | -1.36 | 0.25 | -0.30 / 1.43 | 0.13 / 0.98 / -1.16 | -0.18 | 0.09 | 0.85 | -0.36 | 0.00 | 3050 | diag |
| GC 6 (diag) | 15m emaz(100,3.0) dir=with hold 240m all | 863 | 1 | 1.23 | -0.36 | 0.16 | -0.63 / 1.36 | 0.12 / -0.96 / -0.10 | -0.14 | -0.14 | 0.81 | -0.36 | 0.00 | 1377 | diag |
| CL 1 (diag) | 5m emaz(50,3.0) dir=against hold 240m day | 460 | 1 | 0.53 | -0.54 | 0.52 | 0.60 / 1.35 | 0.10 / 0.11 / 0.12 | 0.03 | -0.25 | 0.93 | -0.14 | 0.25 | 727 | diag |
| CL 2 (diag) | 5m emaz(100,3.0) dir=against hold 240m day | 495 | 1 | 0.30 | -0.35 | 0.42 | 0.62 / 1.21 | 0.03 / -0.01 / 0.25 | 0.01 | -0.16 | 0.90 | -0.19 | 0.25 | 780 | diag |
| CL 3 (diag) | 5m emaz(50,2.0) dir=against hold 240m day | 567 | 1 | 0.17 | -0.10 | 0.04 | -0.02 / 0.78 | -0.01 / -0.08 / -0.11 | -0.11 | -0.18 | 0.83 | -0.26 | 0.00 | 893 | diag |
| ZN 1 (diag) | 15m emaz(50,3.0) dir=against hold 240m day | 292 | 0 | -1.34 | -1.50 | -1.38 | -1.50 / -1.62 | -0.26 / -0.39 / 0.04 | -0.50 | -0.16 | 0.98 | -0.40 | 0.00 | 448 | diag |
| ZN 2 (diag) | 15m emaz(50,3.0) dir=against hold 180m day | 370 | 0 | -1.44 | -1.94 | -1.93 | -3.41 / -2.77 | -0.31 / -0.52 / -0.24 | -0.67 | -0.14 | 1.00 | -0.51 | 0.00 | 553 | diag |
| ZN 3 (diag) | 5m emaz(100,3.0) dir=against hold 240m day | 495 | 0 | -1.50 | -2.81 | -1.91 | -2.84 / -2.20 | -0.30 / -0.47 / -0.33 | -0.71 | -0.31 | 0.96 | -0.51 | 0.00 | 757 | diag |
| BTC 1 | 15m emaz(50,3.0) dir=with hold 180m all | 990 | 2 | 2.26 | 0.53 | 1.45 | 0.32 / 1.38 | 0.40 / 0.13 / 0.04 | 0.21 | -0.23 | 1.00 | 0.08 | 0.25 | 1594 | NO |
| BTC 2 | 5m emaz(50,2.0) dir=with hold 240m all | 1923 | 2 | 1.58 | -0.04 | 1.36 | 1.34 / 0.96 | 0.31 / 1.28 / -0.15 | 0.23 | -0.06 | 1.00 | 0.11 | 0.00 | 3022 | NO |
| BTC 3 | 15m emaz(50,3.0) dir=with hold 240m all | 886 | 2 | 1.52 | 1.06 | 1.21 | 0.83 / 1.13 | 0.29 / 0.70 / -0.08 | 0.20 | -0.27 | 1.00 | 0.04 | 0.50 | 1420 | NO |
| BTC 4 | 15m emaz(50,3.0) dir=with hold 120m all | 1175 | 2 | 1.51 | 0.10 | 0.54 | -0.50 / 0.91 | 0.26 / 0.24 / -0.22 | 0.03 | -0.14 | 0.95 | -0.09 | 0.50 | 1890 | NO |
| BTC 5 | 5m emaz(50,2.0) dir=with hold 180m all | 2485 | 2 | 1.27 | -1.42 | 0.79 | 0.14 / 1.32 | 0.21 / 0.47 / -0.36 | -0.00 | 0.12 | 0.98 | -0.09 | 0.50 | 3908 | NO |
| BTC 6 | 5m emaz(50,3.0) dir=with hold 240m all | 1700 | 2 | 1.03 | -0.11 | 0.74 | 0.52 / 1.10 | 0.13 / 1.28 / -0.36 | 0.06 | -0.13 | 0.95 | -0.06 | 0.50 | 2671 | NO |
| BTC 7 | 15m emaz(100,3.0) dir=with hold 240m day | 315 | 2 | 0.97 | 0.08 | 0.89 | 0.77 / 1.37 | 0.17 / 0.50 / -0.20 | 0.13 | 0.08 | 0.98 | -0.06 | 0.50 | 495 | NO |
| BTC 8 | 15m emaz(50,3.0) dir=with hold 180m day | 382 | 2 | 0.87 | 0.76 | 0.51 | 0.09 / 1.21 | 0.14 / 0.04 / -0.10 | 0.04 | 0.33 | 0.91 | -0.14 | 0.00 | 606 | NO |
| BTC 9 | 15m emaz(100,3.0) dir=with hold 180m day | 375 | 2 | 0.84 | -0.44 | 0.79 | 0.71 / 0.97 | 0.13 / 0.38 / -0.08 | 0.10 | 0.02 | 0.97 | -0.08 | 0.25 | 594 | NO |
| BTC 10 | 15m emaz(100,3.0) dir=with hold 120m day | 473 | 2 | 0.81 | -0.70 | 0.49 | -0.06 / 0.79 | 0.13 / 0.26 / -0.21 | 0.03 | -0.00 | 0.94 | -0.13 | 0.25 | 747 | NO |
| HO 1 | 15m emaz(50,2.0) dir=with hold 120m all | 1678 | 2 | 1.16 | -0.48 | 0.55 | 0.36 / 1.14 | 0.19 / -0.45 / 0.29 | 0.06 | 0.11 | 0.96 | -0.23 | 0.00 | 2677 | NO |
| HO 2 | 15m emaz(50,2.0) dir=with hold 120m day | 652 | 2 | 0.72 | -0.04 | 0.14 | -0.12 / 1.39 | 0.14 / -0.46 / -0.31 | -0.09 | 0.35 | 0.68 | -0.40 | 0.00 | 1026 | NO |
| HO 3 | 5m emaz(50,2.0) dir=against hold 180m day | 823 | 2 | 0.70 | -0.33 | 0.51 | 0.23 / 1.51 | 0.17 / -0.10 / -0.20 | 0.02 | -0.07 | 0.89 | -0.17 | 0.25 | 1312 | NO |
| HO 4 | 5m emaz(50,2.0) dir=against hold 120m day | 1146 | 2 | 0.24 | -0.55 | 0.18 | 0.08 / 1.43 | 0.03 / 0.19 / -0.35 | -0.08 | -0.20 | 0.75 | -0.30 | 0.00 | 1834 | NO |
| HO 5 | 15m emaz(100,3.0) dir=against hold 240m all | 877 | 2 | 0.17 | -0.59 | -0.62 | -1.32 / 1.26 | 0.02 / -0.55 / -1.22 | -0.40 | 0.24 | 0.19 | -0.68 | 0.00 | 1384 | NO |
| HO 6 | 15m emaz(50,3.0) dir=against hold 120m day | 460 | 2 | 0.16 | -0.42 | 0.61 | 1.02 / 1.48 | 0.01 / -0.21 / 0.28 | 0.02 | -0.36 | 0.91 | -0.22 | 0.50 | 727 | NO |
| HO 7 | 15m emaz(50,3.0) dir=against hold 120m all | 1268 | 2 | 0.15 | -0.69 | 0.05 | -0.00 / 1.39 | -0.01 / -0.17 / -0.56 | -0.24 | 0.13 | 0.67 | -0.49 | 0.00 | 2011 | NO |
| HO 8 (diag) | 5m emaz(50,2.0) dir=against hold 240m day | 568 | 1 | 0.97 | -0.33 | 0.52 | 0.17 / 1.06 | 0.19 / -0.17 / -0.24 | 0.02 | -0.20 | 0.94 | -0.19 | 0.25 | 918 | diag |
| HO 9 (diag) | 15m emaz(50,2.0) dir=with hold 240m day | 431 | 1 | 0.83 | -0.04 | 0.18 | -0.14 / 1.31 | 0.14 / 0.04 / -0.42 | -0.03 | 0.46 | 0.63 | -0.32 | 0.00 | 672 | diag |
| HO 10 (diag) | 15m emaz(50,2.0) dir=with hold 180m day | 520 | 1 | 0.53 | -0.04 | 0.15 | 0.02 / 1.08 | 0.08 / -0.14 / -0.25 | -0.06 | 0.31 | 0.75 | -0.36 | 0.00 | 819 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 44 |
| diagnostic cells read | 17 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 38 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 8 |
| standalone pair-window Sharpe above own random-entry null p95 | 27 |
| worst-decile corr <= +0.30 | 50 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 16 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 5m emaz(50,2.0) dir=with hold 240m all | clean | 1.35 | 2.22 | -128318 | -97021 | 320770 | -232416 | 3.96 | 45.7 | 1.77 | -82820 | 232566 | -88273 |
| BTC 5m emaz(50,2.0) dir=with hold 240m all | H1 | 2.64 | 4.70 | -141491 | -117240 | 303627 | -206952 | 2.87 | 39.3 | 4.11 | -64470 | 139451 | -77693 |
| BTC 5m emaz(50,2.0) dir=with hold 240m all | H2 | -0.13 | -0.20 | -100700 | -79946 | 259161 | -125617 | -0.13 | 50.0 | 2.15 | -89681 | 239025 | -91391 |
| BTC 5m emaz(50,2.0) dir=with hold 240m all | all | 1.36 | 2.25 | -130971 | -99500 | 581970 | -232416 | 3.62 | 45.2 | 2.17 | -84636 | 239025 | -91391 |
| CL 5m emaz(50,3.0) dir=against hold 240m day (diag) | clean | 0.48 | 0.74 | -121176 | -102277 | 447905 | -156251 | 0.97 | 45.7 | 1.56 | -82509 | 248261 | -90316 |
| CL 5m emaz(50,3.0) dir=against hold 240m day (diag) | H1 | 0.50 | 0.97 | -47729 | -43369 | 235523 | -58382 | 0.31 | 42.9 | 2.94 | -75646 | 149329 | -78755 |
| CL 5m emaz(50,3.0) dir=against hold 240m day (diag) | H2 | 0.71 | 1.22 | -234737 | -199987 | 729668 | -250096 | 0.68 | 52.8 | 2.41 | -97047 | 243460 | -107847 |
| CL 5m emaz(50,3.0) dir=against hold 240m day (diag) | all | 0.52 | 0.86 | -160032 | -130574 | 881750 | -250096 | 1.14 | 46.4 | 1.96 | -86364 | 248261 | -107847 |
| ES 15m emaz(100,3.0) dir=against hold 180m day | clean | 1.04 | 1.85 | -101815 | -84710 | 392766 | -183283 | 2.40 | 45.7 | 1.72 | -81211 | 271139 | -90122 |
| ES 15m emaz(100,3.0) dir=against hold 180m day | H1 | -0.34 | -0.54 | -152283 | -148469 | 449154 | -157498 | -0.27 | 60.7 | 2.51 | -78070 | 160309 | -91703 |
| ES 15m emaz(100,3.0) dir=against hold 180m day | H2 | 1.12 | 2.35 | -115630 | -93645 | 286953 | -150340 | 1.55 | 41.7 | 2.60 | -84019 | 233405 | -85513 |
| ES 15m emaz(100,3.0) dir=against hold 180m day | all | 0.76 | 1.34 | -129457 | -101880 | 601668 | -183283 | 2.11 | 47.6 | 2.05 | -83617 | 271139 | -91703 |
| GC 15m emaz(50,2.0) dir=with hold 180m all | clean | 1.18 | 2.01 | -120695 | -93201 | 369478 | -216869 | 2.89 | 44.8 | 1.59 | -81021 | 274610 | -86987 |
| GC 15m emaz(50,2.0) dir=with hold 180m all | H1 | 0.97 | 1.92 | -191446 | -162636 | 651641 | -242763 | 0.81 | 50.0 | 3.72 | -52995 | 151824 | -60683 |
| GC 15m emaz(50,2.0) dir=with hold 180m all | H2 | -0.81 | -1.00 | -451459 | -319612 | 1485914 | -616891 | -0.46 | 52.8 | 1.63 | -108774 | 258137 | -121191 |
| GC 15m emaz(50,2.0) dir=with hold 180m all | all | 0.36 | 0.52 | -243727 | -185028 | 1485914 | -616891 | 0.61 | 47.6 | 1.86 | -89853 | 274610 | -121191 |
| HO 15m emaz(50,2.0) dir=with hold 120m all | clean | 1.12 | 1.74 | -123530 | -107014 | 585319 | -141596 | 1.73 | 43.8 | 1.65 | -83601 | 280088 | -91823 |
| HO 15m emaz(50,2.0) dir=with hold 120m all | H1 | -0.57 | -0.68 | -193874 | -152096 | 366964 | -269286 | -0.43 | 53.6 | 2.37 | -85441 | 186550 | -90640 |
| HO 15m emaz(50,2.0) dir=with hold 120m all | H2 | 0.62 | 0.92 | -568256 | -435895 | 899655 | -631352 | 0.84 | 44.4 | 2.58 | -91828 | 251896 | -102094 |
| HO 15m emaz(50,2.0) dir=with hold 120m all | all | 0.55 | 0.80 | -291211 | -210443 | 899655 | -631352 | 1.79 | 45.2 | 1.99 | -86751 | 280088 | -102094 |
| NQ 5m emaz(50,3.0) dir=against hold 180m day | clean | 1.10 | 1.59 | -146489 | -103568 | 422470 | -313204 | 2.37 | 46.7 | 1.76 | -81263 | 236516 | -86592 |
| NQ 5m emaz(50,3.0) dir=against hold 180m day | H1 | 0.05 | 0.06 | -157301 | -126880 | 385043 | -222924 | 0.03 | 46.4 | 2.72 | -75997 | 180881 | -81026 |
| NQ 5m emaz(50,3.0) dir=against hold 180m day | H2 | 1.98 | 4.27 | -122303 | -112095 | 350924 | -137219 | 2.96 | 38.9 | 3.07 | -95845 | 193440 | -109968 |
| NQ 5m emaz(50,3.0) dir=against hold 180m day | all | 1.18 | 1.92 | -154064 | -119783 | 422470 | -313204 | 4.86 | 44.6 | 2.22 | -84477 | 236516 | -109968 |
| RTY 15m emaz(50,3.0) dir=against hold 180m day | clean | 0.91 | 1.49 | -119770 | -97336 | 582335 | -165314 | 1.43 | 42.9 | 1.60 | -90859 | 268543 | -105453 |
| RTY 15m emaz(50,3.0) dir=against hold 180m day | H1 | -0.02 | -0.02 | -158058 | -148980 | 323805 | -171738 | -0.02 | 46.4 | 2.47 | -80459 | 184414 | -87557 |
| RTY 15m emaz(50,3.0) dir=against hold 180m day | H2 | 1.46 | 3.12 | -148445 | -122958 | 473349 | -179648 | 1.60 | 50.0 | 2.85 | -88139 | 231336 | -97595 |
| RTY 15m emaz(50,3.0) dir=against hold 180m day | all | 0.89 | 1.51 | -142573 | -119540 | 582335 | -179648 | 2.72 | 45.2 | 2.02 | -89961 | 268543 | -105453 |
| ZN 15m emaz(50,3.0) dir=against hold 240m day (diag) | clean | -1.38 | -1.79 | -130849 | -112437 | 1359416 | -167959 | -0.92 | 63.8 | 1.20 | -90060 | 307078 | -95386 |
| ZN 15m emaz(50,3.0) dir=against hold 240m day (diag) | H1 | -3.89 | -3.62 | -82022 | -78275 | 470281 | -92893 | -1.00 | 60.7 | 2.44 | -74780 | 167033 | -76932 |
| ZN 15m emaz(50,3.0) dir=against hold 240m day (diag) | H2 | -0.21 | -0.30 | -83159 | -69511 | 281373 | -105272 | -0.16 | 44.4 | 2.33 | -79169 | 211818 | -79653 |
| ZN 15m emaz(50,3.0) dir=against hold 240m day (diag) | all | -1.38 | -1.76 | -122929 | -104260 | 2089592 | -167959 | -0.85 | 58.9 | 1.64 | -86753 | 307078 | -95386 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m emaz(100,3.0) dir=against hold 180m day | -15.8 | 9.2 | 18.1 | 16.1 | 10.4 / 21.4 | 4.3 / 9.4 | NO |
| NQ 5m emaz(50,3.0) dir=against hold 180m day | -7.0 | -19.9 | 14.8 | 32.9 | 16.6 / 23.6 | -9.0 / 7.1 | NO |
| RTY 15m emaz(50,3.0) dir=against hold 180m day | -12.3 | -17.0 | 8.4 | 10.7 | -17.9 / 6.3 | 12.2 / 19.9 | NO |
| GC 15m emaz(50,2.0) dir=with hold 180m all | -19.8 | -56.0 | -11.5 | -28.5 | 15.9 / 21.1 | 26.5 / 38.4 | NO |
| CL 5m emaz(50,3.0) dir=against hold 240m day (diag) | -18.8 | -21.2 | 12.1 | 26.1 | 10.5 / 20.8 | 27.7 / 33.8 | NO |
| ZN 15m emaz(50,3.0) dir=against hold 240m day (diag) | -49.7 | 1.3 | 13.4 | 1.6 | 0.5 / 7.4 | 31.2 / 35.5 | NO |
| BTC 5m emaz(50,2.0) dir=with hold 240m all | -6.4 | 13.9 | 16.6 | 31.2 | 13.7 / 18.6 | 29.8 / 50.5 | NO |
| HO 15m emaz(50,2.0) dir=with hold 120m all | -12.0 | -91.6 | -8.4 | -14.3 | 7.3 / 15.5 | -26.8 / -11.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m emaz(100,3.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 1911 | 5.8 | -23.6 | -9.4 | 29.4 | 0.09 / -0.38 / -0.15 | 112.5 / 83.2 |
| ES 2 5m emaz(50,3.0) dir=against hold 240m day | negative pre-2023 | 2243 | -36.7 | -66.1 | -52.1 | 29.4 | -0.60 / -1.08 / -0.85 | 84.7 / 55.4 |
| ES 3 15m emaz(100,3.0) dir=against hold 240m all | negative pre-2023 | 4259 | -6.6 | -36.0 | -21.8 | 29.4 | -0.21 / -1.10 / -0.67 | 74.0 / 44.6 |
| ES 4 15m emaz(50,2.0) dir=against hold 240m all | negative pre-2023 | 5845 | -6.7 | -36.1 | -21.8 | 29.4 | -0.24 / -1.25 / -0.76 | 45.2 / 15.8 |
| ES 5 15m emaz(100,3.0) dir=against hold 240m day | negative pre-2023 | 1618 | -6.5 | -35.9 | -21.7 | 29.4 | -0.08 / -0.45 / -0.27 | 62.0 / 32.7 |
| ES 6 15m emaz(100,3.0) dir=against hold 120m day | negative pre-2023 | 2351 | -3.8 | -33.2 | -19.0 | 29.4 | -0.09 / -0.73 / -0.42 | 47.6 / 18.3 |
| ES 7 5m emaz(100,3.0) dir=with hold 120m day | negative pre-2023 | 4331 | -2.1 | -31.5 | -17.3 | 29.4 | -0.07 / -0.99 / -0.54 | 46.0 / 16.7 |
| ES 8 15m emaz(50,2.0) dir=against hold 240m day | negative pre-2023 | 2168 | -7.3 | -36.6 | -22.4 | 29.4 | -0.11 / -0.55 / -0.33 | 39.8 / 10.5 |
| ES 9 (diag) 15m emaz(50,3.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 2144 | 0.7 | -28.6 | -14.5 | 29.4 | 0.02 / -0.57 / -0.29 | 82.7 / 53.3 |
| ES 10 (diag) 5m emaz(50,2.0) dir=with hold 120m day | negative pre-2023 | 5768 | -2.3 | -31.7 | -17.5 | 29.4 | -0.09 / -1.19 / -0.66 | 52.2 / 22.9 |
| NQ 1 5m emaz(100,3.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2535 | 10.8 | -3.6 | 5.0 | 14.4 | 0.12 / -0.04 / 0.05 | 238.3 / 224.0 |
| NQ 2 5m emaz(50,3.0) dir=against hold 180m day | negative pre-2023 | 3242 | -33.9 | -48.3 | -39.7 | 14.4 | -0.43 / -0.62 / -0.51 | 182.8 / 168.5 |
| NQ 3 15m emaz(50,2.0) dir=against hold 240m all | negative pre-2023 | 5788 | -13.3 | -27.7 | -19.1 | 14.4 | -0.31 / -0.64 / -0.44 | 96.8 / 82.5 |
| NQ 4 15m emaz(50,2.0) dir=against hold 240m day | negative pre-2023 | 2221 | -25.3 | -39.7 | -31.1 | 14.4 | -0.25 / -0.38 / -0.30 | 183.8 / 169.5 |
| NQ 5 15m emaz(100,3.0) dir=against hold 120m all | gross-positive, cost-negative pre-2023 | 5509 | 2.8 | -11.6 | -3.0 | 14.4 | 0.08 / -0.38 / -0.10 | 74.7 / 60.3 |
| NQ 6 5m emaz(100,3.0) dir=against hold 180m day | negative pre-2023 | 3419 | -18.5 | -32.9 | -24.3 | 14.4 | -0.27 / -0.47 / -0.35 | 157.4 / 143.1 |
| NQ 7 15m emaz(100,3.0) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 2388 | 11.9 | -2.5 | 6.1 | 14.4 | 0.16 / -0.04 / 0.08 | 126.5 / 112.1 |
| NQ 8 15m emaz(50,2.0) dir=against hold 180m all | negative pre-2023 | 6775 | -12.4 | -26.8 | -18.2 | 14.4 | -0.36 / -0.76 / -0.52 | 67.4 / 53.0 |
| NQ 9 5m emaz(100,3.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 7710 | 4.7 | -9.7 | -1.1 | 14.4 | 0.12 / -0.26 / -0.03 | 64.4 / 50.1 |
| NQ 10 15m emaz(50,3.0) dir=against hold 180m day | negative pre-2023 | 1897 | -7.0 | -21.3 | -12.8 | 14.4 | -0.08 / -0.23 / -0.14 | 126.5 / 112.2 |
| RTY 1 5m emaz(50,3.0) dir=against hold 240m day | positive pre-2023 | 1451 | 24.8 | 10.4 | 12.7 | 14.4 | 0.46 / 0.20 / 0.24 | 81.3 / 67.0 |
| RTY 2 15m emaz(50,3.0) dir=against hold 240m day | negative pre-2023 | 1015 | -1.4 | -15.8 | -13.6 | 14.4 | -0.02 / -0.25 / -0.21 | 78.8 / 64.4 |
| RTY 3 15m emaz(50,3.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 1188 | 4.5 | -9.9 | -7.6 | 14.4 | 0.10 / -0.19 / -0.14 | 59.5 / 45.1 |
| RTY 4 5m emaz(50,3.0) dir=against hold 120m all | gross-positive, cost-negative pre-2023 | 7062 | 11.6 | -2.8 | -0.5 | 14.4 | 0.97 / -0.23 / -0.04 | 21.6 / 7.2 |
| RTY 5 5m emaz(50,2.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 2505 | 7.7 | -6.7 | -4.4 | 14.4 | 0.23 / -0.18 / -0.12 | 37.3 / 23.0 |
| RTY 6 15m emaz(100,3.0) dir=against hold 180m day | positive pre-2023 | 1252 | 46.3 | 31.9 | 34.2 | 14.4 | 0.86 / 0.60 / 0.64 | 39.7 / 25.4 |
| RTY 7 (diag) 5m emaz(100,3.0) dir=against hold 240m day | positive pre-2023 | 1543 | 28.1 | 13.8 | 16.0 | 14.4 | 0.53 / 0.27 / 0.31 | 72.9 / 58.6 |
| RTY 8 (diag) 5m emaz(50,3.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 4598 | 5.6 | -8.7 | -6.5 | 14.4 | 0.28 / -0.43 / -0.32 | 36.5 / 22.1 |
| RTY 9 (diag) 5m emaz(50,2.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 1731 | 10.4 | -3.9 | -1.7 | 14.4 | 0.21 / -0.07 / -0.02 | 68.4 / 54.0 |
| GC 1 15m emaz(50,2.0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 7103 | 1.6 | -22.7 | -13.0 | 24.4 | 0.07 / -1.01 / -0.58 | 73.6 / 49.2 |
| GC 2 5m emaz(100,3.0) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 8119 | 3.4 | -21.0 | -11.2 | 24.4 | 0.14 / -0.93 / -0.50 | 65.3 / 41.0 |
| GC 3 5m emaz(50,2.0) dir=with hold 180m all | negative pre-2023 | 12341 | -0.2 | -24.6 | -14.8 | 24.4 | -0.02 / -1.67 / -1.01 | 42.6 / 18.3 |
| GC 4 (diag) 15m emaz(100,3.0) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 5010 | 4.6 | -19.8 | -10.1 | 24.4 | 0.17 / -0.75 / -0.39 | 90.9 / 66.5 |
| GC 5 (diag) 5m emaz(50,2.0) dir=with hold 240m all | negative pre-2023 | 9811 | -2.8 | -27.2 | -17.4 | 24.4 | -0.15 / -1.36 / -0.87 | 69.9 / 45.5 |
| GC 6 (diag) 15m emaz(100,3.0) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 4406 | 12.6 | -11.8 | -2.1 | 24.4 | 0.37 / -0.36 / -0.07 | 97.6 / 73.2 |
| CL 1 (diag) 5m emaz(50,3.0) dir=against hold 240m day | negative pre-2023 | 2292 | -6.3 | -30.7 | -28.0 | 24.4 | -0.11 / -0.54 / -0.49 | 50.0 / 25.6 |
| CL 2 (diag) 5m emaz(100,3.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2451 | 4.8 | -19.6 | -16.9 | 24.4 | 0.08 / -0.35 / -0.30 | 38.9 / 14.5 |
| CL 3 (diag) 5m emaz(50,2.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2876 | 18.9 | -5.5 | -2.8 | 24.4 | 0.34 / -0.10 / -0.05 | 29.5 / 5.1 |
| ZN 1 (diag) 15m emaz(50,3.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 1386 | 5.2 | -30.4 | -35.5 | 35.6 | 0.25 / -1.50 / -1.75 | 6.2 / -29.5 |
| ZN 2 (diag) 15m emaz(50,3.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 1680 | 4.3 | -31.3 | -36.4 | 35.6 | 0.26 / -1.94 / -2.25 | 9.4 / -26.2 |
| ZN 3 (diag) 5m emaz(100,3.0) dir=against hold 240m day | negative pre-2023 | 2438 | -6.9 | -42.5 | -47.6 | 35.6 | -0.46 / -2.81 / -3.15 | 11.4 / -24.2 |
| BTC 1 15m emaz(50,3.0) dir=with hold 180m all | positive pre-2023 | 684 | 109.4 | 55.0 | 87.5 | 54.4 | 1.05 / 0.53 / 0.84 | 471.9 / 417.6 |
| BTC 2 5m emaz(50,2.0) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 1413 | 51.4 | -3.0 | 29.6 | 54.4 | 0.83 / -0.04 / 0.48 | 222.3 / 167.9 |
| BTC 3 15m emaz(50,3.0) dir=with hold 240m all | positive pre-2023 | 600 | 187.8 | 133.5 | 165.9 | 54.4 | 1.49 / 1.06 / 1.32 | 392.8 / 338.4 |
| BTC 4 15m emaz(50,3.0) dir=with hold 120m all | positive pre-2023 | 792 | 63.3 | 8.9 | 41.3 | 54.4 | 0.73 / 0.10 / 0.48 | 237.9 / 183.5 |
| BTC 5 5m emaz(50,2.0) dir=with hold 180m all | negative pre-2023 | 1773 | -19.2 | -73.5 | -41.0 | 54.4 | -0.37 / -1.42 / -0.79 | 169.1 / 114.7 |
| BTC 6 5m emaz(50,3.0) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 1192 | 47.3 | -7.0 | 25.4 | 54.4 | 0.79 / -0.11 / 0.43 | 183.1 / 128.7 |
| BTC 7 15m emaz(100,3.0) dir=with hold 240m day | positive pre-2023 | 201 | 71.4 | 17.0 | 49.5 | 54.4 | 0.32 / 0.08 / 0.22 | 491.5 / 437.1 |
| BTC 8 15m emaz(50,3.0) dir=with hold 180m day | positive pre-2023 | 240 | 213.1 | 158.8 | 191.2 | 54.4 | 1.01 / 0.76 / 0.91 | 357.8 / 303.4 |
| BTC 9 15m emaz(100,3.0) dir=with hold 180m day | negative pre-2023 | 251 | -26.0 | -80.4 | -47.8 | 54.4 | -0.14 / -0.44 / -0.26 | 346.2 / 291.8 |
| BTC 10 15m emaz(100,3.0) dir=with hold 120m day | negative pre-2023 | 320 | -42.7 | -97.1 | -64.5 | 54.4 | -0.30 / -0.70 / -0.46 | 267.9 / 213.6 |
| HO 1 15m emaz(50,2.0) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 8286 | 2.1 | -10.7 | -9.1 | 12.8 | 0.10 / -0.48 / -0.41 | 35.4 / 22.7 |
| HO 2 15m emaz(50,2.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 3440 | 11.1 | -1.7 | -0.3 | 12.8 | 0.24 / -0.04 / -0.01 | 42.0 / 29.2 |
| HO 3 5m emaz(50,2.0) dir=against hold 180m day | negative pre-2023 | 4271 | -7.5 | -20.2 | -18.7 | 12.8 | -0.12 / -0.33 / -0.31 | 54.6 / 41.9 |
| HO 4 5m emaz(50,2.0) dir=against hold 120m day | negative pre-2023 | 5929 | -6.8 | -19.6 | -18.1 | 12.8 | -0.19 / -0.55 / -0.51 | 24.3 / 11.5 |
| HO 5 15m emaz(100,3.0) dir=against hold 240m all | negative pre-2023 | 4175 | -18.0 | -30.7 | -29.2 | 12.8 | -0.35 / -0.59 / -0.56 | 26.1 / 13.4 |
| HO 6 15m emaz(50,3.0) dir=against hold 120m day | negative pre-2023 | 2330 | -14.9 | -27.7 | -26.2 | 12.8 | -0.23 / -0.42 / -0.40 | 18.7 / 6.0 |
| HO 7 15m emaz(50,3.0) dir=against hold 120m all | negative pre-2023 | 5930 | -7.4 | -20.2 | -18.6 | 12.8 | -0.25 / -0.69 / -0.63 | 16.5 / 3.7 |
| HO 8 (diag) 5m emaz(50,2.0) dir=against hold 240m day | negative pre-2023 | 2945 | -16.0 | -28.7 | -27.2 | 12.8 | -0.19 / -0.33 / -0.31 | 86.3 / 73.6 |
| HO 9 (diag) 15m emaz(50,2.0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 2158 | 9.4 | -3.4 | -2.0 | 12.8 | 0.10 / -0.04 / -0.02 | 69.4 / 56.6 |
| HO 10 (diag) 15m emaz(50,2.0) dir=with hold 180m day | gross-positive, cost-negative pre-2023 | 2621 | 10.3 | -2.4 | -1.1 | 12.8 | 0.14 / -0.04 / -0.02 | 36.6 / 23.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 23 cells pass the clean rule against a replicate mean of 10.4 (p(count) = 0.00, p(top) = 0.00); CL: 0 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 1.00); ES: 8 cells pass the clean rule against a replicate mean of 4.4 (p(count) = 0.09, p(top) = 0.81); GC: 3 cells pass the clean rule against a replicate mean of 5.0 (p(count) = 0.88, p(top) = 0.05); HO: 7 cells pass the clean rule against a replicate mean of 9.6 (p(count) = 0.88, p(top) = 0.97); NQ: 20 cells pass the clean rule against a replicate mean of 15.1 (p(count) = 0.12, p(top) = 0.43); RTY: 6 cells pass the clean rule against a replicate mean of 6.3 (p(count) = 0.58, p(top) = 0.17); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 44 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.36 (NQ 5m emaz(50,3.0) dir=against hold 180m day); bootstrap lower bound > 0 for 8 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 16; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 23, 'gross-positive, cost-negative pre-2023': 14, 'positive pre-2023': 7}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q19.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q19/ (`Q19_CO_all_selected_scored.csv`).

DONE Q19
