# REPORT Q14 - Q14: range-squeeze breakout of the n-bar range, with/against, time exit

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 35 selected cells (+18 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.24; best pair-window standalone Sharpe +1.07.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: range-squeeze breakout of the n-bar range, with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        12 |               1.653 |                2 |         10 |            0 |
| CL    |      96 |         96 |         1 |               0.666 |                2 |          1 |            3 |
| ES    |      96 |         96 |         2 |               0.607 |                2 |          2 |            3 |
| GC    |      96 |         96 |         2 |               1.079 |                2 |          2 |            3 |
| HO    |      96 |         96 |         8 |               1.672 |                2 |          8 |            2 |
| NQ    |      96 |         96 |         9 |               0.858 |                2 |          9 |            1 |
| RTY   |      96 |         96 |         3 |               0.972 |                2 |          3 |            3 |
| ZN    |      96 |         96 |         0 |              -1.629 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    2 |            3.475 |               9 |      0.875 |                       0.431 |            0.609 |           0.963 |    0.77  |       0.607 |                1.566 |
| NQ    |     200 |                    9 |           13.745 |              22 |      0.94  |                       0.445 |            0.851 |           1.101 |    0.995 |       0.802 |                2.039 |
| RTY   |     200 |                    3 |            5.12  |              13 |      0.85  |                       0.733 |            0.66  |           0.99  |    0.33  |       0.972 |                1.897 |
| GC    |     200 |                    2 |            4.165 |              10 |      0.915 |                       0.586 |            0.613 |           0.99  |    0.505 |       1.079 |                1.745 |
| CL    |     200 |                    1 |            2.205 |               8 |      0.895 |                       0.656 |            0.588 |           1.116 |    0.315 |       0.656 |                1.536 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| BTC   |     200 |                   12 |            9.715 |              19 |      0.245 |                       0.943 |            0.726 |           0.965 |    0.075 |       1.653 |                1.946 |
| HO    |     200 |                    8 |            9.155 |              17 |      0.725 |                       0.795 |            0.711 |           0.951 |    0.26  |       1.672 |                1.957 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m compress(12,4.0) dir=against hold 240m all | 1538 | 2 | 0.61 | -0.66 | 0.10 | -0.36 / 0.62 | 0.10 / -0.35 / 0.06 | -0.13 | -0.15 | 0.96 | -0.19 | 0.00 | 2494 | NO |
| ES 2 | 15m compress(12,3.0) dir=against hold 240m all | 1318 | 2 | 0.25 | -0.51 | 0.08 | -0.00 / 0.62 | 0.03 / -0.36 / 0.11 | -0.13 | 0.15 | 0.91 | -0.21 | 0.00 | 2137 | NO |
| ES 3 (diag) | 15m compress(12,4.0) dir=against hold 180m day | 643 | 1 | 0.44 | -0.42 | 0.31 | 0.16 / 0.88 | 0.12 / -0.18 / 0.13 | 0.03 | -0.09 | 0.91 | -0.09 | 0.00 | 1009 | diag |
| ES 4 (diag) | 15m compress(6,2.0) dir=with hold 60m day | 709 | 1 | 0.33 | -1.04 | -0.17 | -0.92 / 0.38 | -0.01 / -0.19 / -0.33 | -0.22 | -0.11 | 0.97 | -0.29 | 0.00 | 1122 | diag |
| ES 5 (diag) | 5m compress(12,3.0) dir=with hold 120m day | 1131 | 1 | 0.25 | -1.23 | 0.34 | 0.46 / 1.00 | -0.01 / 0.22 / -0.07 | -0.08 | -0.53 | 0.95 | -0.14 | 0.00 | 1805 | diag |
| NQ 1 | 5m compress(6,2.0) dir=with hold 240m all | 2200 | 2 | 0.80 | -0.24 | 0.48 | 0.17 / 1.42 | 0.05 / 0.07 / 0.01 | -0.00 | -0.49 | 0.86 | -0.17 | 0.00 | 3516 | NO |
| NQ 2 | 15m compress(6,2.0) dir=against hold 240m all | 1500 | 2 | 0.54 | 0.03 | 0.07 | -0.27 / 1.22 | 0.06 / -0.25 / -0.20 | -0.06 | 0.59 | 0.62 | -0.26 | 0.00 | 2404 | NO |
| NQ 3 | 15m compress(6,2.0) dir=with hold 120m all | 2349 | 2 | 0.53 | -0.69 | -0.10 | -0.76 / 1.20 | 0.04 / -0.46 / -0.26 | -0.16 | -0.36 | 0.64 | -0.32 | 0.00 | 3747 | NO |
| NQ 4 | 15m compress(6,2.0) dir=with hold 120m day | 605 | 2 | 0.51 | -0.12 | -0.00 | -0.65 / 1.19 | -0.00 / 0.13 / -0.45 | -0.11 | -0.09 | 0.52 | -0.30 | 0.00 | 973 | NO |
| NQ 5 | 5m compress(12,4.0) dir=with hold 120m all | 4036 | 2 | 0.51 | -1.09 | -0.40 | -1.29 / 1.41 | -0.01 / -0.45 / -0.58 | -0.28 | 0.06 | 0.49 | -0.45 | 0.00 | 6459 | NO |
| NQ 6 | 15m compress(12,4.0) dir=with hold 120m all | 2410 | 2 | 0.46 | -0.95 | 0.09 | -0.32 / 1.35 | -0.01 / -0.11 / -0.14 | -0.11 | -0.31 | 0.74 | -0.28 | 0.00 | 3861 | NO |
| NQ 7 | 5m compress(12,4.0) dir=with hold 120m day | 1395 | 2 | 0.34 | -0.28 | 0.12 | -0.18 / 1.39 | -0.04 / -0.06 / -0.20 | -0.12 | 0.26 | 0.75 | -0.26 | 0.00 | 2227 | NO |
| NQ 8 | 15m compress(6,2.0) dir=with hold 60m day | 741 | 2 | 0.21 | -0.23 | 0.44 | 0.77 / 1.18 | -0.04 / 0.53 / -0.25 | -0.03 | -0.04 | 0.91 | -0.19 | 0.00 | 1213 | NO |
| NQ 9 | 5m compress(6,2.0) dir=with hold 240m day | 684 | 2 | 0.09 | -0.34 | 0.35 | 0.89 / 1.39 | -0.06 / 0.20 / 0.05 | -0.01 | -0.11 | 0.84 | -0.17 | 0.50 | 1086 | NO |
| NQ 10 (diag) | 5m compress(12,3.0) dir=with hold 120m day | 1150 | 1 | 0.86 | -0.20 | -0.20 | -1.47 / 1.10 | 0.06 / -0.10 / -0.74 | -0.18 | -0.14 | 0.48 | -0.34 | 0.00 | 1853 | diag |
| RTY 1 | 5m compress(12,3.0) dir=against hold 240m all | 1979 | 2 | 0.97 | -0.23 | 0.54 | 0.01 / 0.67 | 0.13 / -0.23 / -0.07 | -0.06 | 0.27 | 0.98 | -0.14 | 0.00 | 3182 | NO |
| RTY 2 | 15m compress(12,4.0) dir=against hold 240m day | 487 | 2 | 0.69 | 0.41 | 0.27 | -0.32 / 1.10 | 0.12 / -0.50 / 0.03 | -0.03 | -0.05 | 0.90 | -0.20 | 0.25 | 780 | NO |
| RTY 3 | 5m compress(12,4.0) dir=against hold 240m all | 2226 | 2 | 0.54 | 0.27 | 0.19 | -0.37 / 0.87 | 0.13 / -0.57 / -0.05 | -0.11 | 0.36 | 0.94 | -0.17 | 0.25 | 3567 | NO |
| RTY 4 (diag) | 5m compress(12,3.0) dir=against hold 240m day | 574 | 1 | 0.82 | -0.03 | 1.00 | 1.17 / 1.42 | 0.11 / -0.18 / 0.33 | 0.08 | -0.24 | 0.98 | -0.07 | 0.25 | 923 | diag |
| RTY 5 (diag) | 15m compress(12,4.0) dir=against hold 180m day | 631 | 1 | 0.82 | 0.08 | 0.27 | -0.60 / 0.92 | 0.16 / -0.67 / 0.11 | -0.02 | 0.05 | 0.93 | -0.19 | 0.25 | 984 | diag |
| RTY 6 (diag) | 5m compress(12,3.0) dir=against hold 180m day | 879 | 1 | 0.58 | 0.17 | 0.71 | 0.81 / 1.20 | 0.05 / -0.34 / 0.25 | -0.01 | -0.29 | 0.96 | -0.14 | 0.25 | 1402 | diag |
| GC 1 | 5m compress(12,3.0) dir=against hold 240m day | 597 | 2 | 1.08 | -0.47 | 1.07 | 1.35 / 1.23 | 0.20 / -0.36 / 0.54 | 0.19 | 0.10 | 1.00 | -0.14 | 0.25 | 955 | NO |
| GC 2 | 15m compress(12,3.0) dir=with hold 240m day | 348 | 2 | 0.09 | -0.20 | -0.45 | -0.95 / 1.61 | -0.06 / -0.59 / -0.97 | -0.37 | -0.05 | 0.31 | -0.67 | 0.00 | 572 | NO |
| GC 3 (diag) | 5m compress(12,3.0) dir=against hold 180m day | 861 | 1 | 0.84 | -0.51 | 0.77 | 0.94 / 1.27 | 0.15 / -0.50 / 0.34 | 0.07 | -0.56 | 0.96 | -0.27 | 0.25 | 1381 | diag |
| GC 4 (diag) | 15m compress(12,4.0) dir=with hold 240m all | 1567 | 1 | 0.56 | -1.15 | 0.05 | -0.21 / 1.56 | 0.06 / -1.16 / -0.08 | -0.24 | -0.31 | 0.74 | -0.47 | 0.00 | 2538 | diag |
| GC 5 (diag) | 5m compress(12,3.0) dir=against hold 120m day | 1146 | 1 | 0.41 | -0.72 | 0.90 | 1.39 / 1.12 | 0.04 / 0.65 / 0.18 | 0.07 | -0.72 | 1.00 | -0.11 | 0.25 | 1862 | diag |
| CL 1 | 15m compress(12,3.0) dir=with hold 120m day | 504 | 2 | 0.66 | -0.72 | -0.77 | -2.77 / 0.84 | 0.12 / -0.58 / -0.96 | -0.32 | 0.17 | 0.54 | -0.46 | 0.00 | 815 | NO |
| CL 2 (diag) | 5m compress(6,2.0) dir=against hold 240m day | 651 | 1 | 0.67 | 0.11 | 0.52 | 0.41 / 0.73 | 0.10 / -0.21 / 0.29 | 0.01 | -0.06 | 0.96 | -0.10 | 0.50 | 1053 | diag |
| CL 3 (diag) | 5m compress(12,3.0) dir=against hold 240m day | 585 | 1 | 0.45 | 0.12 | -0.34 | -0.98 / 1.05 | 0.08 / -0.28 / -0.56 | -0.20 | 0.06 | 0.52 | -0.42 | 0.00 | 931 | diag |
| CL 4 (diag) | 15m compress(12,3.0) dir=with hold 240m day | 359 | 1 | 0.38 | -0.73 | -0.48 | -1.40 / 1.18 | 0.07 / -0.78 / -0.56 | -0.25 | 0.17 | 0.48 | -0.45 | 0.00 | 573 | diag |
| ZN 1 (diag) | 15m compress(12,3.0) dir=with hold 240m day | 348 | 0 | -1.63 | -2.11 | -1.86 | -2.44 / -1.84 | -0.34 / -0.47 / -0.48 | -0.69 | 0.32 | 0.91 | -0.57 | 0.00 | 537 | diag |
| ZN 2 (diag) | 5m compress(12,4.0) dir=against hold 240m day | 648 | 0 | -1.84 | -2.15 | -2.51 | -3.98 / -2.61 | -0.38 / -0.28 / -0.63 | -0.85 | -0.32 | 0.95 | -0.62 | 0.00 | 998 | diag |
| ZN 3 (diag) | 15m compress(12,4.0) dir=against hold 240m day | 473 | 0 | -1.87 | -2.03 | -2.06 | -2.53 / -1.79 | -0.36 / -0.40 / -0.28 | -0.71 | -0.43 | 0.89 | -0.54 | 0.00 | 741 | diag |
| BTC 1 | 5m compress(12,3.0) dir=with hold 240m day | 538 | 2 | 1.65 | 1.78 | 0.77 | -0.32 / 1.59 | 0.28 / -0.01 / -0.15 | 0.10 | 0.60 | 0.96 | -0.07 | 0.25 | 841 | NO |
| BTC 2 | 5m compress(12,4.0) dir=with hold 240m day | 666 | 2 | 1.14 | -0.66 | 0.55 | -0.34 / 1.44 | 0.17 / 0.12 / -0.22 | 0.03 | 0.53 | 0.96 | -0.13 | 0.50 | 1044 | NO |
| BTC 3 | 5m compress(12,4.0) dir=with hold 120m day | 1344 | 2 | 1.06 | -0.20 | 0.13 | -1.57 / 1.16 | 0.17 / -0.30 / -0.28 | -0.07 | 0.57 | 0.83 | -0.20 | 0.00 | 2119 | NO |
| BTC 4 | 15m compress(12,3.0) dir=with hold 120m all | 1601 | 2 | 1.04 | -0.99 | -0.01 | -1.84 / 0.89 | 0.16 / -0.09 / -0.50 | -0.12 | 0.30 | 0.84 | -0.22 | 0.00 | 2494 | NO |
| BTC 5 | 5m compress(12,3.0) dir=with hold 180m all | 2194 | 2 | 0.96 | 1.03 | 0.49 | -0.04 / 1.14 | 0.13 / 0.79 / -0.34 | -0.02 | 0.37 | 0.96 | -0.13 | 0.25 | 3435 | NO |
| BTC 6 | 5m compress(12,3.0) dir=with hold 180m day | 762 | 2 | 0.86 | 0.86 | 0.47 | 0.04 / 1.01 | 0.10 / 0.28 / -0.18 | 0.01 | 0.65 | 0.91 | -0.15 | 0.25 | 1196 | NO |
| BTC 7 | 5m compress(12,4.0) dir=with hold 180m day | 945 | 2 | 0.82 | -0.68 | 0.11 | -0.88 / 1.17 | 0.10 / -0.21 / -0.31 | -0.08 | 0.59 | 0.72 | -0.23 | 0.00 | 1488 | NO |
| BTC 8 | 15m compress(12,3.0) dir=against hold 240m day | 324 | 2 | 0.65 | 1.57 | 0.53 | 0.36 / 1.35 | 0.10 / -0.43 / 0.27 | 0.05 | -0.48 | 0.93 | -0.15 | 0.00 | 530 | NO |
| BTC 9 | 15m compress(12,3.0) dir=with hold 60m all | 1845 | 2 | 0.64 | -1.10 | -0.68 | -3.20 / 0.68 | 0.12 / -0.81 / -0.39 | -0.26 | 0.37 | 0.59 | -0.32 | 0.00 | 2861 | NO |
| BTC 10 | 5m compress(12,4.0) dir=with hold 240m all | 2173 | 2 | 0.60 | 1.14 | -0.33 | -1.49 / 0.88 | 0.13 / -0.25 / -0.35 | -0.13 | 0.24 | 0.52 | -0.26 | 0.00 | 3409 | NO |
| HO 1 | 5m compress(12,4.0) dir=against hold 240m day | 699 | 2 | 1.67 | 0.16 | 0.35 | -0.87 / 1.22 | 0.32 / -0.07 / -0.50 | 0.05 | 0.16 | 0.88 | -0.16 | 0.75 | 1103 | NO |
| HO 2 | 5m compress(12,4.0) dir=against hold 120m day | 1435 | 2 | 1.35 | -0.45 | 0.78 | 0.45 / 1.08 | 0.22 / 0.21 / 0.14 | 0.14 | 0.02 | 0.97 | -0.06 | 0.25 | 2270 | LEAD |
| HO 3 | 5m compress(12,4.0) dir=against hold 180m day | 999 | 2 | 0.97 | -0.46 | 0.06 | -0.91 / 1.61 | 0.20 / -0.15 / -0.45 | -0.03 | 0.20 | 0.68 | -0.24 | 0.75 | 1586 | NO |
| HO 4 | 5m compress(12,3.0) dir=against hold 240m day | 570 | 2 | 0.84 | 0.06 | 0.84 | 0.81 / 1.55 | 0.17 / 0.35 / 0.07 | 0.14 | 0.07 | 0.93 | -0.04 | 0.25 | 906 | NO |
| HO 5 | 15m compress(12,3.0) dir=with hold 240m day | 334 | 2 | 0.63 | 0.22 | 0.42 | 0.35 / 1.28 | 0.14 / -0.61 / 0.31 | 0.07 | -0.05 | 0.87 | -0.16 | 0.25 | 529 | NO |
| HO 6 | 15m compress(6,2.0) dir=against hold 180m day | 404 | 2 | 0.37 | -0.26 | 0.13 | 0.01 / 1.34 | 0.06 / -0.04 / -0.06 | -0.00 | 0.37 | 0.80 | -0.22 | 0.00 | 688 | NO |
| HO 7 | 15m compress(6,2.0) dir=against hold 120m day | 573 | 2 | 0.36 | -0.43 | -0.06 | -0.29 / 1.22 | 0.04 / -0.05 / -0.25 | -0.07 | 0.38 | 0.68 | -0.34 | 0.00 | 969 | NO |
| HO 8 | 5m compress(6,2.0) dir=with hold 180m all | 2523 | 2 | 0.17 | -0.83 | 0.92 | 1.65 / 1.09 | -0.02 / -0.22 / 0.67 | 0.05 | 0.02 | 0.99 | -0.11 | 0.00 | 4081 | NO |
| HO 9 (diag) | 5m compress(6,2.0) dir=against hold 240m day | 640 | 1 | 0.70 | -0.26 | 0.01 | -0.47 / 1.41 | 0.15 / 0.36 / -0.79 | -0.08 | -0.30 | 0.60 | -0.33 | 0.00 | 1031 | diag |
| HO 10 (diag) | 15m compress(6,2.0) dir=against hold 240m day | 266 | 1 | 0.68 | -0.31 | 0.07 | -0.36 / 1.46 | 0.11 / 0.07 / -0.47 | -0.05 | 0.09 | 0.60 | -0.30 | 0.00 | 468 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 35 |
| diagnostic cells read | 18 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 1 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 26 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 16 |
| worst-decile corr <= +0.30 | 40 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 4 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 5m compress(12,3.0) dir=with hold 240m day | clean | 1.59 | 2.95 | -102177 | -85941 | 367292 | -117509 | 3.94 | 42.9 | 1.74 | -84747 | 285059 | -105376 |
| BTC 5m compress(12,3.0) dir=with hold 240m day | H1 | -0.42 | -0.60 | -165041 | -155468 | 589295 | -180321 | -0.26 | 64.3 | 2.82 | -69683 | 137074 | -87999 |
| BTC 5m compress(12,3.0) dir=with hold 240m day | H2 | -0.20 | -0.31 | -98912 | -88120 | 272906 | -111009 | -0.23 | 55.6 | 2.14 | -96221 | 217357 | -97017 |
| BTC 5m compress(12,3.0) dir=with hold 240m day | all | 0.77 | 1.25 | -130674 | -107568 | 589295 | -180321 | 2.09 | 48.8 | 1.99 | -87658 | 285059 | -105376 |
| CL 15m compress(12,3.0) dir=with hold 120m day | clean | 0.75 | 1.12 | -130174 | -109318 | 437885 | -188459 | 1.56 | 41.9 | 1.58 | -84128 | 322586 | -95687 |
| CL 15m compress(12,3.0) dir=with hold 120m day | H1 | -4.61 | -4.07 | -94965 | -84012 | 594313 | -95203 | -1.00 | 75.0 | 2.25 | -76570 | 152154 | -81003 |
| CL 15m compress(12,3.0) dir=with hold 120m day | H2 | -2.68 | -2.93 | -227253 | -202733 | 1531575 | -272139 | -0.89 | 72.2 | 1.34 | -111668 | 220836 | -134081 |
| CL 15m compress(12,3.0) dir=with hold 120m day | all | -0.77 | -0.97 | -174059 | -145199 | 1983188 | -272139 | -0.64 | 53.6 | 1.63 | -90108 | 322586 | -134081 |
| ES 15m compress(12,4.0) dir=against hold 240m all | clean | 0.49 | 0.75 | -121357 | -103682 | 604853 | -161430 | 0.74 | 50.5 | 1.56 | -87698 | 289264 | -90390 |
| ES 15m compress(12,4.0) dir=against hold 240m all | H1 | -0.97 | -1.16 | -213265 | -181027 | 448158 | -265420 | -0.71 | 50.0 | 2.48 | -85504 | 165010 | -91539 |
| ES 15m compress(12,4.0) dir=against hold 240m all | H2 | 0.09 | 0.14 | -143441 | -136354 | 444127 | -155998 | 0.09 | 47.2 | 2.36 | -94012 | 218706 | -103592 |
| ES 15m compress(12,4.0) dir=against hold 240m all | all | 0.10 | 0.14 | -155732 | -129815 | 1254597 | -265420 | 0.13 | 50.0 | 1.89 | -89528 | 289264 | -103592 |
| GC 5m compress(12,3.0) dir=against hold 240m day | clean | 1.03 | 1.83 | -103237 | -89592 | 449422 | -130899 | 2.08 | 51.4 | 1.66 | -85707 | 246693 | -93695 |
| GC 5m compress(12,3.0) dir=against hold 240m day | H1 | 0.37 | 0.47 | -438823 | -342949 | 809942 | -712334 | 0.33 | 39.3 | 2.47 | -129125 | 235971 | -153687 |
| GC 5m compress(12,3.0) dir=against hold 240m day | H2 | 2.02 | 5.08 | -252294 | -215093 | 556387 | -257198 | 3.75 | 50.0 | 2.83 | -94056 | 249882 | -98675 |
| GC 5m compress(12,3.0) dir=against hold 240m day | all | 1.07 | 1.85 | -239055 | -174922 | 1149715 | -712334 | 2.86 | 48.8 | 2.09 | -97928 | 293494 | -153687 |
| HO 5m compress(12,4.0) dir=against hold 120m day | clean | 1.29 | 2.22 | -116295 | -90149 | 600108 | -182963 | 1.95 | 46.7 | 1.68 | -81963 | 263067 | -88404 |
| HO 5m compress(12,4.0) dir=against hold 120m day | H1 | 0.90 | 1.44 | -112645 | -105824 | 232590 | -113280 | 0.92 | 50.0 | 3.03 | -66080 | 151954 | -75268 |
| HO 5m compress(12,4.0) dir=against hold 120m day | H2 | 0.37 | 0.52 | -357268 | -303177 | 649557 | -368221 | 0.46 | 47.2 | 2.44 | -92150 | 231903 | -96267 |
| HO 5m compress(12,4.0) dir=against hold 120m day | all | 0.78 | 1.15 | -212442 | -159846 | 649557 | -368221 | 2.59 | 47.0 | 2.05 | -84487 | 263067 | -96267 |
| NQ 5m compress(6,2.0) dir=with hold 240m all | clean | 0.73 | 1.34 | -104284 | -84430 | 432911 | -177495 | 1.54 | 45.7 | 1.51 | -90225 | 327376 | -99954 |
| NQ 5m compress(6,2.0) dir=with hold 240m all | H1 | 0.23 | 0.37 | -80881 | -76312 | 381424 | -94439 | 0.12 | 57.1 | 2.89 | -75344 | 132778 | -80016 |
| NQ 5m compress(6,2.0) dir=with hold 240m all | H2 | 0.16 | 0.27 | -192328 | -149414 | 731813 | -213906 | 0.11 | 55.6 | 2.30 | -84633 | 226196 | -87382 |
| NQ 5m compress(6,2.0) dir=with hold 240m all | all | 0.48 | 0.83 | -132168 | -103305 | 731813 | -213906 | 1.09 | 50.0 | 1.88 | -88171 | 327376 | -99954 |
| RTY 5m compress(12,3.0) dir=against hold 240m all | clean | 0.90 | 1.62 | -100610 | -87967 | 441198 | -164644 | 1.86 | 46.7 | 1.59 | -83156 | 285727 | -88071 |
| RTY 5m compress(12,3.0) dir=against hold 240m all | H1 | -0.22 | -0.30 | -143736 | -124760 | 392522 | -144792 | -0.15 | 53.6 | 2.60 | -83521 | 164880 | -87205 |
| RTY 5m compress(12,3.0) dir=against hold 240m all | H2 | 0.18 | 0.25 | -156546 | -121966 | 596155 | -212317 | 0.11 | 50.0 | 2.23 | -87208 | 223675 | -93082 |
| RTY 5m compress(12,3.0) dir=against hold 240m all | all | 0.54 | 0.86 | -124908 | -105109 | 810027 | -212317 | 1.02 | 48.8 | 1.89 | -84534 | 285727 | -93082 |
| ZN 15m compress(12,4.0) dir=against hold 240m day (diag) | clean | -1.87 | -2.19 | -148707 | -126131 | 2182674 | -183132 | -0.78 | 61.9 | 1.10 | -91419 | 278884 | -106654 |
| ZN 15m compress(12,4.0) dir=against hold 240m day (diag) | H1 | -3.15 | -3.10 | -112321 | -105516 | 561240 | -119446 | -0.92 | 64.3 | 2.43 | -77946 | 163881 | -79264 |
| ZN 15m compress(12,4.0) dir=against hold 240m day (diag) | H2 | -2.08 | -2.63 | -77516 | -75674 | 578731 | -78136 | -0.86 | 72.2 | 2.02 | -81672 | 227240 | -82006 |
| ZN 15m compress(12,4.0) dir=against hold 240m day (diag) | all | -2.06 | -2.38 | -135649 | -115356 | 3273448 | -183132 | -0.83 | 64.3 | 1.50 | -88608 | 278884 | -106654 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m compress(12,4.0) dir=against hold 240m all | -28.1 | -18.9 | 2.6 | 14.5 | -2.5 / 9.8 | -25.3 / -11.3 | NO |
| NQ 5m compress(6,2.0) dir=with hold 240m all | -21.1 | -6.7 | 11.9 | 4.7 | -7.6 / 7.5 | 26.7 / 34.4 | NO |
| RTY 5m compress(12,3.0) dir=against hold 240m all | -20.7 | 8.0 | 16.7 | 25.1 | 14.3 / 17.8 | 12.9 / 16.2 | NO |
| GC 5m compress(12,3.0) dir=against hold 240m day | 6.7 | -168.5 | -19.8 | -27.4 | 3.5 / 15.3 | -183.0 / -103.4 | NO |
| CL 15m compress(12,3.0) dir=with hold 120m day | -44.3 | -66.5 | -1.1 | 7.3 | 0.1 / 9.7 | 24.8 / 31.9 | NO |
| ZN 15m compress(12,4.0) dir=against hold 240m day (diag) | -60.3 | -19.2 | 10.5 | -0.1 | -20.2 / 4.4 | 28.1 / 29.4 | NO |
| BTC 5m compress(12,3.0) dir=with hold 240m day | -16.2 | -12.2 | 10.4 | 27.3 | -13.1 / 15.1 | 10.0 / 18.3 | NO |
| HO 5m compress(12,4.0) dir=against hold 120m day | -11.2 | -7.2 | 8.7 | 11.7 | 13.8 / 20.8 | 35.8 / 42.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m compress(12,4.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 7876 | 13.4 | -16.0 | -1.9 | 29.4 | 0.55 / -0.66 / -0.08 | 44.7 / 15.4 |
| ES 2 15m compress(12,3.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 6750 | 16.4 | -12.9 | 1.2 | 29.4 | 0.65 / -0.51 / 0.05 | 35.2 / 5.9 |
| ES 3 (diag) 15m compress(12,4.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 3167 | 8.4 | -21.0 | -6.8 | 29.4 | 0.16 / -0.42 / -0.14 | 62.2 / 32.8 |
| ES 4 (diag) 15m compress(6,2.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 4157 | 6.7 | -22.7 | -8.4 | 29.4 | 0.31 / -1.04 / -0.39 | 42.7 / 13.3 |
| ES 5 (diag) 5m compress(12,3.0) dir=with hold 120m day | negative pre-2023 | 6135 | -5.3 | -34.7 | -20.5 | 29.4 | -0.19 / -1.23 / -0.72 | 48.1 / 18.7 |
| NQ 1 5m compress(6,2.0) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 11314 | 6.9 | -7.4 | 1.1 | 14.4 | 0.23 / -0.24 / 0.03 | 60.9 / 46.6 |
| NQ 2 15m compress(6,2.0) dir=against hold 240m all | positive pre-2023 | 7733 | 15.5 | 1.2 | 9.7 | 14.4 | 0.46 / 0.03 / 0.28 | 37.9 / 23.6 |
| NQ 3 15m compress(6,2.0) dir=with hold 120m all | negative pre-2023 | 11972 | -1.5 | -15.9 | -7.3 | 14.4 | -0.07 / -0.69 / -0.32 | 31.5 / 17.2 |
| NQ 4 15m compress(6,2.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 3276 | 6.5 | -7.9 | 0.7 | 14.4 | 0.10 / -0.12 / 0.01 | 72.2 / 57.8 |
| NQ 5 5m compress(12,4.0) dir=with hold 120m all | negative pre-2023 | 20483 | -2.8 | -17.1 | -8.6 | 14.4 | -0.18 / -1.09 / -0.55 | 27.2 / 12.9 |
| NQ 6 15m compress(12,4.0) dir=with hold 120m all | negative pre-2023 | 11984 | -7.9 | -22.2 | -13.7 | 14.4 | -0.33 / -0.95 / -0.59 | 31.4 / 17.1 |
| NQ 7 5m compress(12,4.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 7265 | 2.6 | -11.7 | -3.2 | 14.4 | 0.07 / -0.28 / -0.07 | 39.6 / 25.2 |
| NQ 8 15m compress(6,2.0) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 4122 | 6.2 | -8.2 | 0.3 | 14.4 | 0.17 / -0.23 / 0.01 | 30.1 / 15.7 |
| NQ 9 5m compress(6,2.0) dir=with hold 240m day | negative pre-2023 | 3455 | -13.3 | -27.7 | -19.2 | 14.4 | -0.16 / -0.34 / -0.23 | 16.4 / 2.0 |
| NQ 10 (diag) 5m compress(12,3.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 6026 | 5.0 | -9.4 | -0.9 | 14.4 | 0.11 / -0.20 / -0.02 | 89.4 / 75.1 |
| RTY 1 5m compress(12,3.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 5800 | 10.4 | -3.9 | -1.7 | 14.4 | 0.61 / -0.23 / -0.10 | 32.3 / 17.9 |
| RTY 2 15m compress(12,4.0) dir=against hold 240m day | positive pre-2023 | 1454 | 36.5 | 22.1 | 24.4 | 14.4 | 0.67 / 0.41 / 0.45 | 56.4 / 42.0 |
| RTY 3 5m compress(12,4.0) dir=against hold 240m all | positive pre-2023 | 6492 | 19.1 | 4.7 | 7.0 | 14.4 | 1.13 / 0.27 / 0.41 | 24.0 / 9.7 |
| RTY 4 (diag) 5m compress(12,3.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 1719 | 12.7 | -1.6 | 0.6 | 14.4 | 0.25 / -0.03 / 0.01 | 59.3 / 45.0 |
| RTY 5 (diag) 15m compress(12,4.0) dir=against hold 180m day | positive pre-2023 | 1796 | 17.6 | 3.3 | 5.5 | 14.4 | 0.39 / 0.08 / 0.13 | 54.6 / 40.2 |
| RTY 6 (diag) 5m compress(12,3.0) dir=against hold 180m day | positive pre-2023 | 2609 | 20.1 | 5.8 | 8.0 | 14.4 | 0.57 / 0.17 / 0.23 | 36.4 / 22.1 |
| GC 1 5m compress(12,3.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 3024 | 1.6 | -22.8 | -13.1 | 24.4 | 0.03 / -0.47 / -0.27 | 100.5 / 76.1 |
| GC 2 15m compress(12,3.0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 1740 | 10.9 | -13.5 | -3.7 | 24.4 | 0.16 / -0.20 / -0.05 | 47.7 / 23.4 |
| GC 3 (diag) 5m compress(12,3.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 4420 | 6.7 | -17.7 | -7.9 | 24.4 | 0.19 / -0.51 / -0.23 | 64.1 / 39.7 |
| GC 4 (diag) 15m compress(12,4.0) dir=with hold 240m all | negative pre-2023 | 8004 | -2.3 | -26.7 | -16.9 | 24.4 | -0.10 / -1.15 / -0.73 | 44.5 / 20.1 |
| GC 5 (diag) 5m compress(12,3.0) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 5876 | 7.7 | -16.7 | -7.0 | 24.4 | 0.33 / -0.72 / -0.30 | 39.5 / 15.2 |
| CL 1 15m compress(12,3.0) dir=with hold 120m day | negative pre-2023 | 2710 | -3.3 | -27.7 | -24.8 | 24.4 | -0.08 / -0.72 / -0.65 | 56.4 / 32.1 |
| CL 2 (diag) 5m compress(6,2.0) dir=against hold 240m day | positive pre-2023 | 3256 | 30.1 | 5.7 | 8.5 | 24.4 | 0.57 / 0.11 / 0.16 | 54.3 / 29.9 |
| CL 3 (diag) 5m compress(12,3.0) dir=against hold 240m day | positive pre-2023 | 2946 | 30.7 | 6.3 | 9.0 | 24.4 | 0.61 / 0.12 / 0.18 | 42.8 / 18.5 |
| CL 4 (diag) 15m compress(12,3.0) dir=with hold 240m day | negative pre-2023 | 1821 | -25.8 | -50.2 | -47.6 | 24.4 | -0.38 / -0.73 / -0.70 | 52.9 / 28.5 |
| ZN 1 (diag) 15m compress(12,3.0) dir=with hold 240m day | negative pre-2023 | 1820 | -2.0 | -37.6 | -42.7 | 35.6 | -0.11 / -2.11 / -2.39 | 5.2 / -30.4 |
| ZN 2 (diag) 5m compress(12,4.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 3307 | 5.2 | -30.4 | -35.5 | 35.6 | 0.36 / -2.15 / -2.51 | 8.4 / -27.2 |
| ZN 3 (diag) 15m compress(12,4.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2435 | 3.6 | -32.0 | -37.1 | 35.6 | 0.23 / -2.03 / -2.36 | 3.1 / -32.5 |
| BTC 1 5m compress(12,3.0) dir=with hold 240m day | positive pre-2023 | 392 | 313.7 | 259.4 | 291.7 | 54.4 | 2.15 / 1.78 / 2.00 | 565.0 / 510.6 |
| BTC 2 5m compress(12,4.0) dir=with hold 240m day | negative pre-2023 | 478 | -40.8 | -95.2 | -62.6 | 54.4 | -0.27 / -0.66 / -0.43 | 408.8 / 354.5 |
| BTC 3 5m compress(12,4.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 977 | 42.4 | -12.0 | 20.4 | 54.4 | 0.76 / -0.20 / 0.37 | 225.3 / 170.9 |
| BTC 4 15m compress(12,3.0) dir=with hold 120m all | negative pre-2023 | 1159 | -10.6 | -65.0 | -32.5 | 54.4 | -0.16 / -0.99 / -0.49 | 171.5 / 117.2 |
| BTC 5 5m compress(12,3.0) dir=with hold 180m all | positive pre-2023 | 1646 | 105.0 | 50.6 | 83.2 | 54.4 | 2.14 / 1.03 / 1.70 | 143.5 / 89.1 |
| BTC 6 5m compress(12,3.0) dir=with hold 180m day | positive pre-2023 | 579 | 146.8 | 92.5 | 124.9 | 54.4 | 1.37 / 0.86 / 1.16 | 243.5 / 189.2 |
| BTC 7 5m compress(12,4.0) dir=with hold 180m day | negative pre-2023 | 697 | -7.2 | -61.5 | -29.1 | 54.4 | -0.07 / -0.68 / -0.31 | 222.8 / 168.4 |
| BTC 8 15m compress(12,3.0) dir=against hold 240m day | positive pre-2023 | 249 | 385.3 | 331.0 | 363.8 | 54.4 | 1.83 / 1.57 / 1.73 | 396.3 / 341.9 |
| BTC 9 15m compress(12,3.0) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 1327 | 15.7 | -38.6 | -6.1 | 54.4 | 0.46 / -1.10 / -0.17 | 99.3 / 44.9 |
| BTC 10 5m compress(12,4.0) dir=with hold 240m all | positive pre-2023 | 1560 | 116.9 | 62.6 | 95.0 | 54.4 | 2.09 / 1.14 / 1.71 | 120.4 / 66.0 |
| HO 1 5m compress(12,4.0) dir=against hold 240m day | positive pre-2023 | 3442 | 24.3 | 11.6 | 13.1 | 12.8 | 0.36 / 0.16 / 0.19 | 125.3 / 112.6 |
| HO 2 5m compress(12,4.0) dir=against hold 120m day | negative pre-2023 | 7302 | -1.2 | -13.9 | -12.4 | 12.8 | -0.04 / -0.45 / -0.40 | 50.7 / 38.0 |
| HO 3 5m compress(12,4.0) dir=against hold 180m day | negative pre-2023 | 5102 | -9.5 | -22.3 | -20.8 | 12.8 | -0.20 / -0.46 / -0.43 | 61.8 / 49.0 |
| HO 4 5m compress(12,3.0) dir=against hold 240m day | positive pre-2023 | 2858 | 18.4 | 5.7 | 7.2 | 12.8 | 0.22 / 0.06 / 0.08 | 79.3 / 66.6 |
| HO 5 15m compress(12,3.0) dir=with hold 240m day | positive pre-2023 | 1703 | 33.4 | 20.6 | 22.1 | 12.8 | 0.35 / 0.22 / 0.24 | 64.4 / 51.7 |
| HO 6 15m compress(6,2.0) dir=against hold 180m day | negative pre-2023 | 2129 | -6.0 | -18.8 | -17.3 | 12.8 | -0.09 / -0.26 / -0.24 | 34.7 / 22.0 |
| HO 7 15m compress(6,2.0) dir=against hold 120m day | negative pre-2023 | 3120 | -7.2 | -20.0 | -18.4 | 12.8 | -0.16 / -0.43 / -0.40 | 25.5 / 12.8 |
| HO 8 5m compress(6,2.0) dir=with hold 180m all | negative pre-2023 | 12759 | -5.2 | -17.9 | -16.4 | 12.8 | -0.24 / -0.83 / -0.75 | 15.0 / 2.3 |
| HO 9 (diag) 5m compress(6,2.0) dir=against hold 240m day | negative pre-2023 | 3302 | -4.2 | -16.9 | -15.4 | 12.8 | -0.07 / -0.26 / -0.24 | 50.8 / 38.0 |
| HO 10 (diag) 15m compress(6,2.0) dir=against hold 240m day | negative pre-2023 | 1450 | -24.7 | -37.5 | -36.0 | 12.8 | -0.21 / -0.31 / -0.30 | 88.6 / 75.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 12 cells pass the clean rule against a replicate mean of 9.7 (p(count) = 0.24, p(top) = 0.07); CL: 1 cells pass the clean rule against a replicate mean of 2.2 (p(count) = 0.90, p(top) = 0.32); ES: 2 cells pass the clean rule against a replicate mean of 3.5 (p(count) = 0.88, p(top) = 0.77); GC: 2 cells pass the clean rule against a replicate mean of 4.2 (p(count) = 0.92, p(top) = 0.51); HO: 8 cells pass the clean rule against a replicate mean of 9.2 (p(count) = 0.72, p(top) = 0.26); NQ: 9 cells pass the clean rule against a replicate mean of 13.7 (p(count) = 0.94, p(top) = 0.99); RTY: 3 cells pass the clean rule against a replicate mean of 5.1 (p(count) = 0.85, p(top) = 0.33); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 35 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.24 (GC 5m compress(12,3.0) dir=against hold 240m day); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 4; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell HO 5m compress(12,4.0) dir=against hold 120m day: uplift +0.22/+0.21/+0.14, boot lo -0.06, plateau 0.25, 2x-slip +0.14, wd corr +0.02, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 13, 'gross-positive, cost-negative pre-2023': 11, 'positive pre-2023': 11}.

- Manual note: the best all-in uplift (+0.24) is again a FADE of a fresh 5-minute breakout (GC squeeze-breakout against, 240-minute hold, day session) and the only gate-3 cell is HO's squeeze-breakout fade, 120-minute hold (+0.22/+0.21/+0.14, bootstrap lower bound -0.06, plateau 0.25). Together with GC's Supertrend-flip fade (B7), RB/HO's Donchian fade (Q2) and the opening-range fades (CL, SI), this is the fifth rule form in which 'fade a fresh 5-minute trend event in the day session and hold two to four hours' shows up in gold or energy; each form fails plateau/bootstrap/replication on its own, which is why the family-level evidence (not any single cell) is recorded in CANDIDATES.md.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q14.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q14/ (`Q14_CO_all_selected_scored.csv`).

DONE Q14
