# REPORT Q12 - Q12: Bollinger-band cross-out (n, k) with/against, time exit

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 49 selected cells (+15 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.25; best pair-window standalone Sharpe +1.03.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: Bollinger-band cross-out (n, k) with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |         9 |               0.951 |                2 |          9 |            1 |
| CL    |      96 |         96 |         2 |               0.456 |                2 |          2 |            3 |
| ES    |      96 |         96 |         8 |               0.628 |                2 |          8 |            2 |
| GC    |      96 |         96 |         3 |               0.997 |                2 |          3 |            3 |
| HO    |      96 |         96 |        14 |               1.341 |                2 |         10 |            0 |
| NQ    |      96 |         96 |        26 |               1.186 |                2 |         10 |            0 |
| RTY   |      96 |         96 |         7 |               1.078 |                2 |          7 |            3 |
| ZN    |      96 |         96 |         0 |              -1.446 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    8 |            4.505 |              10 |      0.09  |                       0.388 |            0.608 |           0.974 |    0.89  |       0.628 |                1.574 |
| NQ    |     200 |                   26 |           15.445 |              26 |      0.015 |                       0.869 |            0.9   |           1.178 |    0.545 |       1.186 |                2.025 |
| RTY   |     200 |                    7 |            6.61  |              15 |      0.465 |                       0.58  |            0.655 |           0.922 |    0.635 |       1.078 |                1.921 |
| GC    |     200 |                    3 |            5.31  |              14 |      0.89  |                       0.45  |            0.635 |           0.894 |    0.865 |       0.535 |                1.629 |
| CL    |     200 |                    2 |            2.95  |               7 |      0.8   |                       0.174 |            0.584 |           0.942 |    0.92  |       0.177 |                1.479 |
| ZN    |     200 |                    0 |            0.005 |               1 |      1     |                     nan     |            0.255 |           0.255 |  nan     |     nan     |                0.255 |
| BTC   |     200 |                    9 |           11.13  |              19 |      0.83  |                       0.52  |            0.737 |           0.979 |    0.94  |       0.951 |                1.903 |
| HO    |     200 |                   14 |           10.66  |              20 |      0.185 |                       0.818 |            0.742 |           1.018 |    0.295 |       1.341 |                1.961 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m boll(40,2.5) dir=against hold 180m all | 802 | 2 | 0.63 | -0.77 | 0.06 | -0.51 / 0.79 | 0.16 / -0.57 / 0.02 | -0.06 | -0.17 | 0.92 | -0.19 | 0.25 | 1231 | NO |
| ES 2 | 15m boll(40,2.5) dir=against hold 240m day | 372 | 2 | 0.61 | -0.51 | 0.08 | -0.49 / 1.19 | 0.13 / -0.55 / 0.06 | -0.01 | 0.02 | 0.68 | -0.17 | 0.25 | 595 | NO |
| ES 3 | 15m boll(20,2.5) dir=against hold 180m all | 926 | 2 | 0.48 | -0.74 | -0.06 | -0.67 / 0.57 | 0.13 / -0.64 / -0.09 | -0.13 | 0.19 | 0.83 | -0.23 | 0.00 | 1445 | NO |
| ES 4 | 15m boll(40,2.5) dir=against hold 240m all | 697 | 2 | 0.38 | -0.73 | -0.11 | -0.60 / 1.39 | 0.11 / -0.52 / -0.07 | -0.08 | 0.12 | 0.73 | -0.22 | 0.00 | 1101 | NO |
| ES 5 | 15m boll(40,2.5) dir=against hold 120m day | 525 | 2 | 0.35 | -0.35 | -0.07 | -0.75 / 0.94 | 0.10 / -0.44 / 0.06 | -0.05 | 0.17 | 0.76 | -0.16 | 0.50 | 802 | NO |
| ES 6 | 15m boll(20,2.0) dir=against hold 180m day | 574 | 2 | 0.33 | -0.58 | 0.08 | -0.13 / 0.79 | 0.07 / -0.33 / 0.11 | -0.03 | -0.04 | 0.79 | -0.16 | 0.00 | 893 | NO |
| ES 7 | 15m boll(40,2.5) dir=against hold 120m all | 923 | 2 | 0.19 | -0.77 | -0.07 | -0.57 / 0.52 | 0.07 / -0.33 / 0.03 | -0.09 | 0.37 | 0.92 | -0.16 | 0.50 | 1412 | NO |
| ES 8 | 15m boll(20,2.5) dir=against hold 120m day | 459 | 2 | 0.14 | -0.36 | -0.13 | -0.52 / 0.99 | 0.06 / -0.34 / -0.01 | -0.07 | 0.02 | 0.78 | -0.19 | 0.00 | 712 | NO |
| ES 9 (diag) | 15m boll(40,2.5) dir=against hold 180m day | 440 | 1 | 0.34 | -0.37 | -0.09 | -0.49 / 0.95 | 0.09 / -0.61 / 0.08 | -0.06 | 0.10 | 0.71 | -0.22 | 0.75 | 675 | diag |
| ES 10 (diag) | 5m boll(20,2.0) dir=with hold 180m day | 880 | 1 | 0.32 | -1.44 | -0.15 | -0.99 / 0.95 | 0.02 / -0.50 / -0.15 | -0.17 | -0.54 | 0.74 | -0.27 | 0.00 | 1396 | diag |
| NQ 1 | 5m boll(20,2.0) dir=with hold 120m day | 1141 | 2 | 1.19 | -0.27 | 0.48 | -0.38 / 1.25 | 0.15 / 0.12 / -0.36 | -0.01 | 0.20 | 0.88 | -0.18 | 0.25 | 1809 | NO |
| NQ 2 | 5m boll(20,2.0) dir=with hold 240m day | 573 | 2 | 1.02 | -0.48 | 0.04 | -0.87 / 1.21 | 0.13 / 0.12 / -0.66 | -0.08 | 0.17 | 0.63 | -0.31 | 0.00 | 916 | NO |
| NQ 3 | 15m boll(20,2.5) dir=against hold 240m all | 890 | 2 | 0.94 | -0.12 | 0.50 | 0.16 / 1.24 | 0.25 / -0.23 / 0.33 | 0.19 | 0.55 | 0.90 | -0.05 | 0.50 | 1424 | NO |
| NQ 4 | 15m boll(20,2.0) dir=against hold 120m day | 696 | 2 | 0.86 | -0.14 | 0.32 | -0.34 / 1.34 | 0.25 / -0.39 / 0.14 | 0.12 | 0.13 | 0.80 | -0.06 | 0.25 | 1079 | NO |
| NQ 5 | 15m boll(20,2.0) dir=against hold 180m all | 1445 | 2 | 0.84 | -0.16 | 0.05 | -0.71 / 1.49 | 0.25 / -0.59 / -0.08 | 0.03 | 0.15 | 0.59 | -0.19 | 0.50 | 2335 | NO |
| NQ 6 | 5m boll(20,2.5) dir=with hold 120m day | 728 | 2 | 0.82 | -0.37 | 0.14 | -0.86 / 1.26 | 0.08 / -0.08 / -0.43 | -0.08 | -0.33 | 0.66 | -0.26 | 0.00 | 1114 | NO |
| NQ 7 | 15m boll(20,2.5) dir=against hold 180m all | 953 | 2 | 0.81 | -0.24 | 0.62 | 0.50 / 1.76 | 0.26 / -0.21 / 0.35 | 0.21 | 0.58 | 0.92 | -0.02 | 0.50 | 1511 | NO |
| NQ 8 | 15m boll(20,2.5) dir=against hold 120m all | 1034 | 2 | 0.75 | -0.21 | 0.72 | 0.71 / 1.29 | 0.22 / 0.09 / 0.13 | 0.17 | 0.21 | 0.93 | -0.01 | 0.25 | 1623 | NO |
| NQ 9 | 15m boll(40,2.5) dir=against hold 240m all | 724 | 2 | 0.75 | -0.41 | 0.63 | 0.68 / 1.27 | 0.22 / -0.28 / 0.60 | 0.23 | -0.14 | 0.95 | -0.01 | 0.25 | 1148 | NO |
| NQ 10 | 15m boll(20,2.5) dir=against hold 120m day | 471 | 2 | 0.72 | -0.03 | 0.76 | 0.85 / 1.60 | 0.19 / 0.17 / 0.28 | 0.21 | 0.15 | 0.92 | 0.02 | 0.00 | 746 | LEAD |
| RTY 1 | 5m boll(20,2.5) dir=against hold 240m day | 474 | 2 | 1.08 | 0.59 | 0.44 | -0.62 / 1.15 | 0.17 / -0.48 / -0.06 | -0.01 | -0.27 | 0.92 | -0.17 | 0.50 | 758 | NO |
| RTY 2 | 5m boll(20,2.5) dir=against hold 180m day | 593 | 2 | 0.93 | 0.41 | 0.42 | -0.38 / 1.31 | 0.13 / -0.44 / 0.11 | 0.00 | -0.27 | 0.91 | -0.15 | 0.00 | 931 | NO |
| RTY 3 | 15m boll(20,2.5) dir=against hold 240m all | 938 | 2 | 0.64 | -0.33 | 0.53 | 0.32 / 1.06 | 0.07 / -0.24 / 0.25 | 0.01 | -0.40 | 0.96 | -0.11 | 0.25 | 1455 | NO |
| RTY 4 | 5m boll(20,2.5) dir=against hold 240m all | 1392 | 2 | 0.49 | -0.44 | 1.03 | 1.60 / 0.85 | 0.07 / 0.28 / 0.37 | 0.09 | 0.08 | 1.00 | -0.03 | 0.00 | 2237 | NO |
| RTY 5 | 15m boll(20,2.0) dir=against hold 240m all | 1299 | 2 | 0.46 | 0.34 | 0.18 | -0.31 / 1.07 | 0.10 / -0.35 / 0.09 | -0.03 | -0.17 | 0.85 | -0.14 | 0.50 | 2093 | NO |
| RTY 6 | 5m boll(20,2.0) dir=against hold 180m day | 889 | 2 | 0.38 | 0.04 | 0.21 | -0.25 / 1.26 | 0.05 / -0.36 / 0.01 | -0.07 | 0.38 | 0.81 | -0.20 | 0.00 | 1393 | NO |
| RTY 7 | 5m boll(20,2.0) dir=against hold 240m day | 564 | 2 | 0.08 | 0.04 | 0.37 | 0.54 / 1.10 | 0.02 / -0.00 / 0.07 | -0.01 | 0.28 | 0.88 | -0.16 | 0.00 | 912 | NO |
| RTY 8 (diag) | 5m boll(40,2.5) dir=against hold 240m day | 487 | 1 | 0.59 | 0.30 | 0.28 | -0.14 / 1.20 | 0.07 / -0.57 / 0.17 | -0.04 | -0.05 | 0.79 | -0.21 | 0.00 | 775 | diag |
| RTY 9 (diag) | 15m boll(20,2.5) dir=against hold 120m day | 455 | 1 | 0.45 | 0.13 | 0.07 | -0.43 / 1.12 | 0.01 / -0.66 / 0.21 | -0.09 | -0.51 | 0.77 | -0.23 | 0.00 | 710 | diag |
| RTY 10 (diag) | 15m boll(20,2.5) dir=against hold 240m day | 410 | 1 | 0.45 | -0.09 | 0.05 | -0.47 / 1.31 | 0.02 / -0.64 / 0.07 | -0.10 | -0.34 | 0.72 | -0.26 | 0.00 | 649 | diag |
| GC 1 | 15m boll(20,2.5) dir=against hold 120m day | 374 | 2 | 0.53 | -0.47 | -0.32 | -0.86 / 1.58 | 0.10 / -0.66 / -0.42 | -0.17 | -0.13 | 0.46 | -0.45 | 0.00 | 597 | NO |
| GC 2 | 15m boll(40,2.5) dir=against hold 120m day | 389 | 2 | 0.42 | -0.71 | -0.36 | -0.93 / 1.42 | 0.05 / -1.40 / 0.10 | -0.22 | 0.06 | 0.42 | -0.47 | 0.00 | 606 | NO |
| GC 3 | 5m boll(20,2.0) dir=with hold 240m day | 588 | 2 | 0.39 | -0.33 | -0.10 | -0.43 / 1.49 | 0.06 / 0.12 / -0.85 | -0.16 | 0.36 | 0.58 | -0.48 | 0.00 | 925 | NO |
| GC 4 (diag) | 15m boll(20,2.0) dir=with hold 180m all | 1581 | 1 | 1.00 | -1.37 | 0.34 | -0.11 / 1.13 | 0.08 / -0.12 / -0.34 | -0.15 | 0.22 | 0.89 | -0.31 | 0.00 | 2511 | diag |
| GC 5 (diag) | 15m boll(20,2.0) dir=against hold 120m day | 584 | 1 | 0.40 | -1.27 | 0.18 | 0.10 / 1.28 | 0.08 / -0.41 / 0.32 | 0.00 | -0.57 | 0.77 | -0.28 | 0.00 | 941 | diag |
| GC 6 (diag) | 5m boll(40,2.5) dir=with hold 180m all | 1628 | 1 | 0.38 | -1.25 | 0.16 | 0.04 / 1.33 | -0.02 / 1.14 / -0.89 | -0.19 | 0.22 | 0.84 | -0.40 | 0.00 | 2615 | diag |
| CL 1 | 15m boll(20,2.5) dir=against hold 240m day | 311 | 2 | 0.18 | -0.31 | 0.46 | 0.77 / 0.99 | -0.00 / 0.19 / 0.11 | -0.00 | -0.32 | 0.94 | -0.16 | 0.75 | 456 | NO |
| CL 2 | 15m boll(20,2.0) dir=against hold 180m day | 515 | 2 | 0.17 | -0.76 | 0.53 | 0.98 / 1.07 | -0.00 / -0.09 / 0.50 | 0.02 | -0.24 | 0.97 | -0.11 | 0.75 | 807 | NO |
| CL 3 (diag) | 15m boll(20,2.0) dir=against hold 240m day | 467 | 1 | 0.46 | -0.79 | 0.78 | 1.17 / 1.04 | 0.07 / 0.11 / 0.42 | 0.09 | -0.21 | 0.99 | -0.05 | 0.00 | 716 | diag |
| CL 4 (diag) | 15m boll(20,2.5) dir=against hold 180m day | 328 | 1 | 0.34 | -0.27 | 0.59 | 0.91 / 0.87 | 0.05 / 0.16 / 0.21 | 0.04 | -0.35 | 0.96 | -0.10 | 0.50 | 484 | diag |
| CL 5 (diag) | 5m boll(20,2.0) dir=against hold 240m day | 567 | 1 | 0.13 | 0.17 | -0.07 | -0.20 / 0.73 | -0.04 / -0.05 / 0.00 | -0.11 | 0.02 | 0.77 | -0.25 | 0.00 | 919 | diag |
| ZN 1 (diag) | 15m boll(20,2.0) dir=against hold 240m day | 470 | 0 | -1.45 | -2.04 | -1.82 | -2.75 / -1.82 | -0.30 / -0.43 / -0.32 | -0.70 | -0.67 | 0.91 | -0.51 | 0.00 | 734 | diag |
| ZN 2 (diag) | 5m boll(20,2.0) dir=against hold 240m day | 598 | 0 | -1.46 | -2.08 | -1.93 | -2.77 / -2.54 | -0.30 / -0.29 / -0.34 | -0.72 | -0.29 | 0.99 | -0.50 | 0.00 | 948 | diag |
| ZN 3 (diag) | 15m boll(40,2.5) dir=against hold 240m day | 350 | 0 | -1.51 | -1.53 | -2.01 | -3.37 / -1.46 | -0.29 / -0.32 / -0.43 | -0.68 | -0.51 | 0.75 | -0.51 | 0.00 | 565 | diag |
| BTC 1 | 5m boll(20,2.5) dir=with hold 60m all | 2299 | 2 | 0.95 | -0.14 | 0.03 | -1.41 / 0.70 | 0.18 / -0.14 / -0.35 | -0.15 | 0.34 | 0.94 | -0.18 | 0.50 | 3608 | NO |
| BTC 2 | 5m boll(20,2.5) dir=with hold 120m all | 1962 | 2 | 0.71 | -1.23 | -0.25 | -1.73 / 1.07 | 0.07 / -0.08 / -0.36 | -0.15 | 0.28 | 0.69 | -0.25 | 0.00 | 3068 | NO |
| BTC 3 | 15m boll(20,2.5) dir=with hold 120m all | 940 | 2 | 0.61 | -0.49 | 0.23 | -0.23 / 1.03 | 0.09 / 0.18 / -0.31 | -0.05 | 0.22 | 0.86 | -0.17 | 0.50 | 1487 | NO |
| BTC 4 | 15m boll(40,2.5) dir=with hold 240m all | 664 | 2 | 0.58 | 1.42 | 1.02 | 1.61 / 1.20 | 0.12 / 0.87 / -0.03 | 0.15 | 0.38 | 0.98 | -0.00 | 0.25 | 1055 | NO |
| BTC 5 | 15m boll(20,2.5) dir=with hold 180m all | 881 | 2 | 0.57 | -0.33 | 0.41 | 0.25 / 1.12 | 0.07 / 0.51 / -0.29 | -0.01 | 0.15 | 0.89 | -0.14 | 0.75 | 1402 | NO |
| BTC 6 | 5m boll(20,2.5) dir=with hold 180m all | 1630 | 2 | 0.52 | -0.53 | 0.01 | -0.84 / 0.93 | 0.06 / 0.18 / -0.23 | -0.06 | -0.04 | 0.70 | -0.17 | 0.00 | 2550 | NO |
| BTC 7 | 15m boll(40,2.5) dir=with hold 180m all | 724 | 2 | 0.39 | 0.97 | 0.82 | 1.43 / 1.15 | 0.07 / 0.84 / -0.10 | 0.09 | 0.25 | 0.99 | -0.06 | 0.25 | 1141 | NO |
| BTC 8 | 5m boll(20,2.5) dir=with hold 60m day | 907 | 2 | 0.21 | -0.83 | -0.16 | -0.71 / 0.64 | 0.07 / 0.17 / -0.50 | -0.13 | 0.29 | 0.83 | -0.25 | 0.00 | 1415 | NO |
| BTC 9 | 5m boll(40,2.5) dir=with hold 120m all | 1747 | 2 | 0.14 | -1.15 | -0.20 | -0.73 / 1.03 | 0.01 / 0.35 / -0.32 | -0.11 | 0.19 | 0.69 | -0.21 | 0.00 | 2740 | NO |
| BTC 10 (diag) | 5m boll(20,2.0) dir=with hold 120m day | 1164 | 1 | 0.61 | -0.59 | -0.57 | -2.52 / 1.36 | 0.09 / -0.74 / -0.30 | -0.18 | 0.40 | 0.46 | -0.32 | 0.00 | 1809 | diag |
| HO 1 | 5m boll(20,2.0) dir=against hold 240m day | 576 | 2 | 1.34 | -0.03 | 0.60 | -0.01 / 1.33 | 0.23 / 0.20 / -0.33 | 0.07 | 0.10 | 0.90 | -0.15 | 0.75 | 925 | NO |
| HO 2 | 5m boll(20,2.0) dir=against hold 180m day | 873 | 2 | 1.29 | -0.21 | 0.64 | 0.17 / 1.25 | 0.23 / 0.12 / -0.19 | 0.08 | -0.14 | 0.93 | -0.15 | 0.25 | 1392 | NO |
| HO 3 | 5m boll(20,2.0) dir=against hold 120m day | 1213 | 2 | 1.24 | -0.34 | 0.32 | -0.42 / 0.99 | 0.21 / 0.66 / -0.56 | 0.03 | 0.09 | 0.87 | -0.18 | 0.75 | 1936 | NO |
| HO 4 | 15m boll(40,2.5) dir=with hold 180m all | 812 | 2 | 1.12 | -0.13 | 0.43 | 0.07 / 1.34 | 0.19 / 0.25 / -0.18 | 0.08 | -0.07 | 0.84 | -0.23 | 0.25 | 1261 | NO |
| HO 5 | 15m boll(40,2.5) dir=with hold 120m all | 928 | 2 | 0.97 | -0.37 | 0.16 | -0.36 / 1.43 | 0.15 / -0.37 / -0.28 | -0.06 | 0.03 | 0.73 | -0.32 | 0.00 | 1433 | NO |
| HO 6 | 15m boll(40,2.5) dir=with hold 240m all | 740 | 2 | 0.55 | -0.14 | -0.21 | -0.67 / 1.55 | 0.08 / -0.01 / -0.58 | -0.12 | -0.05 | 0.57 | -0.44 | 0.00 | 1148 | NO |
| HO 7 | 5m boll(20,2.0) dir=against hold 240m all | 1919 | 2 | 0.52 | 0.19 | -0.28 | -0.86 / 1.28 | 0.05 / -0.24 / -0.95 | -0.29 | 0.42 | 0.54 | -0.54 | 0.00 | 3088 | NO |
| HO 8 | 5m boll(20,2.5) dir=with hold 240m all | 1369 | 2 | 0.44 | -0.04 | 0.12 | -0.02 / 1.34 | 0.03 / -0.08 / 0.07 | -0.04 | -0.13 | 0.78 | -0.36 | 0.50 | 2222 | NO |
| HO 9 | 5m boll(40,2.5) dir=with hold 180m day | 503 | 2 | 0.41 | -0.13 | -0.36 | -0.82 / 1.47 | 0.01 / -0.06 / -0.99 | -0.27 | 0.35 | 0.30 | -0.57 | 0.00 | 788 | NO |
| HO 10 | 5m boll(20,2.5) dir=with hold 180m all | 1587 | 2 | 0.30 | -0.01 | 0.04 | -0.15 / 1.13 | -0.02 / 0.05 / -0.17 | -0.11 | 0.21 | 0.68 | -0.34 | 0.00 | 2588 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 49 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 1 / 1 / 0 |
| all-in uplift @20% > 0 (all scored) | 35 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 9 |
| worst-decile corr <= +0.30 | 54 |
| plateau >= 0.75 | 6 |
| all-in uplift at 2x slippage >= +0.10 | 7 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m boll(40,2.5) dir=with hold 240m all | clean | 0.64 | 1.01 | -127915 | -100066 | 854936 | -215928 | 0.68 | 50.5 | 1.58 | -83273 | 285610 | -85282 |
| BTC 15m boll(40,2.5) dir=with hold 240m all | H1 | 2.48 | 5.18 | -110074 | -101669 | 279526 | -123967 | 2.92 | 32.1 | 3.69 | -85721 | 156482 | -93173 |
| BTC 15m boll(40,2.5) dir=with hold 240m all | H2 | 0.55 | 0.93 | -67985 | -61934 | 167686 | -72116 | 0.71 | 50.0 | 2.27 | -86471 | 216950 | -94223 |
| BTC 15m boll(40,2.5) dir=with hold 240m all | all | 1.02 | 1.75 | -119166 | -96379 | 854936 | -215928 | 1.77 | 47.6 | 2.04 | -85358 | 285610 | -94223 |
| CL 15m boll(20,2.0) dir=against hold 180m day | clean | 0.14 | 0.21 | -132405 | -105934 | 732474 | -188879 | 0.18 | 47.6 | 1.46 | -83848 | 288580 | -88553 |
| CL 15m boll(20,2.0) dir=against hold 180m day | H1 | 0.35 | 0.68 | -59593 | -52024 | 259612 | -75736 | 0.23 | 71.4 | 2.73 | -75445 | 159745 | -79679 |
| CL 15m boll(20,2.0) dir=against hold 180m day | H2 | 1.28 | 2.56 | -193026 | -134467 | 469584 | -269391 | 1.55 | 50.0 | 2.79 | -84406 | 223549 | -90200 |
| CL 15m boll(20,2.0) dir=against hold 180m day | all | 0.53 | 0.90 | -140732 | -108629 | 762888 | -269391 | 1.20 | 51.8 | 1.95 | -83509 | 288580 | -90200 |
| ES 15m boll(40,2.5) dir=against hold 180m all | clean | 0.55 | 0.89 | -115608 | -95991 | 479740 | -162019 | 1.05 | 48.6 | 1.62 | -86428 | 257090 | -93913 |
| ES 15m boll(40,2.5) dir=against hold 180m all | H1 | -1.12 | -1.50 | -163825 | -135241 | 490333 | -243655 | -0.72 | 57.1 | 2.25 | -87532 | 197860 | -92605 |
| ES 15m boll(40,2.5) dir=against hold 180m all | H2 | -0.09 | -0.15 | -117478 | -112738 | 429369 | -118867 | -0.10 | 50.0 | 2.31 | -94575 | 248882 | -99447 |
| ES 15m boll(40,2.5) dir=against hold 180m all | all | 0.06 | 0.10 | -132280 | -115243 | 690199 | -243655 | 0.16 | 50.0 | 1.89 | -89208 | 257090 | -99447 |
| GC 5m boll(20,2.0) dir=with hold 240m day | clean | 0.48 | 0.75 | -121936 | -100885 | 464087 | -154810 | 0.94 | 49.5 | 1.52 | -86360 | 307369 | -92873 |
| GC 5m boll(20,2.0) dir=with hold 240m day | H1 | 0.96 | 1.56 | -342897 | -320204 | 533712 | -406004 | 1.37 | 42.9 | 2.95 | -110952 | 241821 | -158133 |
| GC 5m boll(20,2.0) dir=with hold 240m day | H2 | -1.64 | -1.88 | -424160 | -359295 | 1958060 | -426044 | -0.75 | 55.6 | 1.45 | -106449 | 261085 | -112059 |
| GC 5m boll(20,2.0) dir=with hold 240m day | all | -0.10 | -0.13 | -322434 | -257926 | 1958060 | -426044 | -0.15 | 50.0 | 1.75 | -100346 | 307369 | -158133 |
| HO 15m boll(40,2.5) dir=with hold 180m all | clean | 1.15 | 2.04 | -96090 | -83992 | 459929 | -136813 | 2.26 | 45.7 | 1.65 | -87396 | 290218 | -93093 |
| HO 15m boll(40,2.5) dir=with hold 180m all | H1 | 2.37 | 5.43 | -62592 | -51748 | 170598 | -71211 | 2.47 | 39.3 | 3.08 | -70523 | 154656 | -72811 |
| HO 15m boll(40,2.5) dir=with hold 180m all | H2 | -0.27 | -0.32 | -653532 | -451969 | 1535326 | -993590 | -0.20 | 50.0 | 2.11 | -103275 | 246245 | -110625 |
| HO 15m boll(40,2.5) dir=with hold 180m all | all | 0.43 | 0.53 | -281303 | -190401 | 1535326 | -993590 | 0.75 | 45.8 | 1.98 | -89915 | 290218 | -110625 |
| NQ 15m boll(40,2.5) dir=against hold 240m all | clean | 0.63 | 0.97 | -117786 | -101523 | 618106 | -133931 | 0.93 | 42.9 | 1.68 | -85417 | 242216 | -93747 |
| NQ 15m boll(40,2.5) dir=against hold 240m all | H1 | -0.75 | -1.03 | -195759 | -163967 | 623016 | -230979 | -0.44 | 57.1 | 2.55 | -85237 | 211056 | -87008 |
| NQ 15m boll(40,2.5) dir=against hold 240m all | H2 | 1.55 | 3.48 | -139341 | -124345 | 276028 | -154207 | 3.43 | 50.0 | 2.90 | -93710 | 188363 | -102401 |
| NQ 15m boll(40,2.5) dir=against hold 240m all | all | 0.63 | 1.07 | -146396 | -124962 | 623016 | -230979 | 2.01 | 46.4 | 2.10 | -88217 | 242216 | -102401 |
| RTY 5m boll(20,2.5) dir=against hold 240m all | clean | 0.58 | 1.02 | -102643 | -88561 | 543459 | -117861 | 0.97 | 52.4 | 1.53 | -88969 | 262578 | -100514 |
| RTY 5m boll(20,2.5) dir=against hold 240m all | H1 | 1.46 | 2.26 | -139582 | -122131 | 193088 | -167563 | 2.11 | 39.3 | 3.11 | -75218 | 143592 | -90540 |
| RTY 5m boll(20,2.5) dir=against hold 240m all | H2 | 1.68 | 4.31 | -97112 | -82126 | 395863 | -111986 | 1.95 | 58.3 | 2.66 | -86598 | 202856 | -91803 |
| RTY 5m boll(20,2.5) dir=against hold 240m all | all | 1.03 | 1.95 | -111890 | -94592 | 543459 | -167563 | 3.14 | 51.2 | 2.03 | -88617 | 262578 | -100514 |
| ZN 5m boll(20,2.0) dir=against hold 240m day (diag) | clean | -1.55 | -1.84 | -139947 | -123485 | 1758357 | -172791 | -0.80 | 55.2 | 1.16 | -91967 | 261073 | -102317 |
| ZN 5m boll(20,2.0) dir=against hold 240m day (diag) | H1 | -2.24 | -2.57 | -97173 | -92431 | 615699 | -107324 | -0.63 | 64.3 | 2.53 | -78627 | 148258 | -80502 |
| ZN 5m boll(20,2.0) dir=against hold 240m day (diag) | H2 | -3.16 | -3.33 | -99297 | -93203 | 798202 | -105826 | -0.87 | 72.2 | 1.95 | -84466 | 219758 | -84669 |
| ZN 5m boll(20,2.0) dir=against hold 240m day (diag) | all | -1.93 | -2.22 | -130404 | -113744 | 2921634 | -172791 | -0.85 | 60.1 | 1.53 | -89430 | 261073 | -102317 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m boll(40,2.5) dir=against hold 180m all | -28.8 | -11.0 | 4.0 | 23.7 | 3.5 / 12.1 | -17.0 / -8.1 | NO |
| NQ 15m boll(40,2.5) dir=against hold 240m all | -16.0 | -6.3 | 7.8 | 24.1 | 3.5 / 15.0 | -12.1 / -0.3 | NO |
| RTY 5m boll(20,2.5) dir=against hold 240m all | -10.9 | -8.1 | 8.5 | 26.8 | -9.0 / 8.1 | 6.5 / 8.6 | NO |
| GC 5m boll(20,2.0) dir=with hold 240m day | -33.2 | -112.9 | -22.4 | -8.8 | 7.4 / 14.0 | -124.4 / -60.2 | NO |
| CL 15m boll(20,2.0) dir=against hold 180m day | -19.8 | 10.8 | 20.0 | 25.5 | 13.0 / 18.9 | 25.9 / 34.2 | NO |
| ZN 5m boll(20,2.0) dir=against hold 240m day (diag) | -57.8 | -10.8 | 9.5 | 32.5 | -11.7 / 3.3 | 25.8 / 28.0 | NO |
| BTC 15m boll(40,2.5) dir=with hold 240m all | -13.1 | 5.2 | 16.5 | 25.0 | 14.1 / 19.2 | 0.1 / 14.3 | NO |
| HO 15m boll(40,2.5) dir=with hold 180m all | -17.1 | -147.5 | -15.4 | -28.0 | 5.7 / 12.1 | 35.3 / 37.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m boll(40,2.5) dir=against hold 180m all | gross-positive, cost-negative pre-2023 | 4001 | 2.1 | -27.2 | -12.9 | 29.4 | 0.06 / -0.77 / -0.36 | 58.4 / 29.0 |
| ES 2 15m boll(40,2.5) dir=against hold 240m day | negative pre-2023 | 1806 | -5.5 | -34.9 | -20.8 | 29.4 | -0.08 / -0.51 / -0.30 | 92.8 / 63.5 |
| ES 3 15m boll(20,2.5) dir=against hold 180m all | gross-positive, cost-negative pre-2023 | 4874 | 6.7 | -22.6 | -8.3 | 29.4 | 0.22 / -0.74 / -0.27 | 48.9 / 19.5 |
| ES 4 15m boll(40,2.5) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 3641 | 0.5 | -28.9 | -14.6 | 29.4 | 0.01 / -0.73 / -0.37 | 49.4 / 20.0 |
| ES 5 15m boll(40,2.5) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 2385 | 13.1 | -16.3 | -2.0 | 29.4 | 0.28 / -0.35 / -0.04 | 57.2 / 27.8 |
| ES 6 15m boll(20,2.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 2844 | 2.6 | -26.7 | -12.5 | 29.4 | 0.05 / -0.58 / -0.27 | 48.8 / 19.4 |
| ES 7 15m boll(40,2.5) dir=against hold 120m all | gross-positive, cost-negative pre-2023 | 4562 | 7.5 | -21.9 | -7.5 | 29.4 | 0.26 / -0.77 / -0.27 | 39.2 / 9.8 |
| ES 8 15m boll(20,2.5) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 2242 | 12.4 | -17.0 | -2.8 | 29.4 | 0.26 / -0.36 / -0.06 | 39.4 / 10.1 |
| ES 9 (diag) 15m boll(40,2.5) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 2026 | 6.9 | -22.5 | -8.3 | 29.4 | 0.11 / -0.37 / -0.14 | 51.5 / 22.1 |
| ES 10 (diag) 5m boll(20,2.0) dir=with hold 180m day | negative pre-2023 | 4652 | -30.3 | -59.6 | -45.3 | 29.4 | -0.73 / -1.44 / -1.10 | 55.1 / 25.8 |
| NQ 1 5m boll(20,2.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 6139 | 2.5 | -11.9 | -3.3 | 14.4 | 0.06 / -0.27 / -0.07 | 120.3 / 106.0 |
| NQ 2 5m boll(20,2.0) dir=with hold 240m day | negative pre-2023 | 2947 | -30.0 | -44.3 | -35.8 | 14.4 | -0.32 / -0.48 / -0.38 | 190.3 / 176.0 |
| NQ 3 15m boll(20,2.5) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 4767 | 8.0 | -6.4 | 2.2 | 14.4 | 0.15 / -0.12 / 0.04 | 107.5 / 93.2 |
| NQ 4 15m boll(20,2.0) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 3511 | 5.9 | -8.5 | 0.1 | 14.4 | 0.09 / -0.14 / -0.00 | 119.5 / 105.1 |
| NQ 5 15m boll(20,2.0) dir=against hold 180m all | gross-positive, cost-negative pre-2023 | 7617 | 8.4 | -6.0 | 2.6 | 14.4 | 0.22 / -0.16 / 0.07 | 68.9 / 54.5 |
| NQ 6 5m boll(20,2.5) dir=with hold 120m day | negative pre-2023 | 3974 | -8.5 | -22.8 | -14.1 | 14.4 | -0.13 / -0.37 / -0.23 | 117.7 / 103.3 |
| NQ 7 15m boll(20,2.5) dir=against hold 180m all | gross-positive, cost-negative pre-2023 | 5002 | 2.9 | -11.5 | -2.8 | 14.4 | 0.06 / -0.24 / -0.06 | 80.5 / 66.1 |
| NQ 8 15m boll(20,2.5) dir=against hold 120m all | gross-positive, cost-negative pre-2023 | 5373 | 6.3 | -8.0 | 0.6 | 14.4 | 0.17 / -0.21 / 0.02 | 72.2 / 57.8 |
| NQ 9 15m boll(40,2.5) dir=against hold 240m all | negative pre-2023 | 3717 | -11.1 | -25.5 | -16.9 | 14.4 | -0.18 / -0.41 / -0.27 | 78.0 / 63.6 |
| NQ 10 15m boll(20,2.5) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 2328 | 12.3 | -2.0 | 6.6 | 14.4 | 0.16 / -0.03 / 0.09 | 121.2 / 106.8 |
| RTY 1 5m boll(20,2.5) dir=against hold 240m day | positive pre-2023 | 1442 | 46.8 | 32.4 | 34.6 | 14.4 | 0.85 / 0.59 / 0.63 | 88.2 / 73.9 |
| RTY 2 5m boll(20,2.5) dir=against hold 180m day | positive pre-2023 | 1735 | 33.2 | 18.8 | 21.0 | 14.4 | 0.71 / 0.41 / 0.45 | 63.2 / 48.9 |
| RTY 3 15m boll(20,2.5) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 2672 | 5.0 | -9.4 | -7.1 | 14.4 | 0.18 / -0.33 / -0.25 | 36.9 / 22.6 |
| RTY 4 5m boll(20,2.5) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 4230 | 5.1 | -9.3 | -7.1 | 14.4 | 0.25 / -0.44 / -0.33 | 28.5 / 14.2 |
| RTY 5 15m boll(20,2.0) dir=against hold 240m all | positive pre-2023 | 3856 | 22.2 | 7.8 | 10.1 | 14.4 | 0.95 / 0.34 / 0.43 | 28.8 / 14.4 |
| RTY 6 5m boll(20,2.0) dir=against hold 180m day | positive pre-2023 | 2583 | 15.7 | 1.3 | 3.6 | 14.4 | 0.41 / 0.04 / 0.10 | 32.8 / 18.4 |
| RTY 7 5m boll(20,2.0) dir=against hold 240m day | positive pre-2023 | 1710 | 16.4 | 2.0 | 4.3 | 14.4 | 0.30 / 0.04 / 0.08 | 26.8 / 12.4 |
| RTY 8 (diag) 5m boll(40,2.5) dir=against hold 240m day | positive pre-2023 | 1469 | 30.6 | 16.3 | 18.5 | 14.4 | 0.56 / 0.30 / 0.34 | 50.8 / 36.4 |
| RTY 9 (diag) 15m boll(20,2.5) dir=against hold 120m day | positive pre-2023 | 1369 | 19.9 | 5.6 | 7.8 | 14.4 | 0.46 / 0.13 / 0.18 | 33.3 / 19.0 |
| RTY 10 (diag) 15m boll(20,2.5) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 1227 | 9.0 | -5.3 | -3.1 | 14.4 | 0.17 / -0.09 / -0.05 | 40.1 / 25.8 |
| GC 1 15m boll(20,2.5) dir=against hold 120m day | negative pre-2023 | 2009 | -0.4 | -24.7 | -14.9 | 24.4 | -0.01 / -0.47 / -0.28 | 58.4 / 34.0 |
| GC 2 15m boll(40,2.5) dir=against hold 120m day | negative pre-2023 | 1911 | -13.5 | -37.9 | -28.1 | 24.4 | -0.25 / -0.71 / -0.53 | 47.8 / 23.4 |
| GC 3 5m boll(20,2.0) dir=with hold 240m day | gross-positive, cost-negative pre-2023 | 3089 | 8.5 | -15.8 | -6.0 | 24.4 | 0.17 / -0.33 / -0.13 | 57.8 / 33.4 |
| GC 4 (diag) 15m boll(20,2.0) dir=with hold 180m all | negative pre-2023 | 8194 | -3.6 | -28.0 | -18.2 | 24.4 | -0.18 / -1.37 / -0.89 | 61.1 / 36.8 |
| GC 5 (diag) 15m boll(20,2.0) dir=against hold 120m day | negative pre-2023 | 3145 | -22.9 | -47.3 | -37.4 | 24.4 | -0.61 / -1.27 / -1.00 | 44.5 / 20.1 |
| GC 6 (diag) 5m boll(40,2.5) dir=with hold 180m all | negative pre-2023 | 8795 | -1.0 | -25.3 | -15.5 | 24.4 | -0.05 / -1.25 / -0.76 | 37.3 / 13.0 |
| CL 1 15m boll(20,2.5) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 1702 | 3.4 | -21.0 | -18.4 | 24.4 | 0.05 / -0.31 / -0.27 | 39.7 / 15.3 |
| CL 2 15m boll(20,2.0) dir=against hold 180m day | negative pre-2023 | 2677 | -16.0 | -40.3 | -37.8 | 24.4 | -0.30 / -0.76 / -0.71 | 31.7 / 7.3 |
| CL 3 (diag) 15m boll(20,2.0) dir=against hold 240m day | negative pre-2023 | 2384 | -23.0 | -47.4 | -44.8 | 24.4 | -0.38 / -0.79 / -0.74 | 51.9 / 27.5 |
| CL 4 (diag) 15m boll(20,2.5) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 1796 | 6.7 | -17.6 | -15.0 | 24.4 | 0.10 / -0.27 / -0.23 | 46.9 / 22.5 |
| CL 5 (diag) 5m boll(20,2.0) dir=against hold 240m day | positive pre-2023 | 2984 | 33.7 | 9.3 | 11.9 | 24.4 | 0.62 / 0.17 / 0.22 | 27.1 / 2.7 |
| ZN 1 (diag) 15m boll(20,2.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2391 | 3.5 | -32.1 | -37.3 | 35.6 | 0.22 / -2.04 / -2.37 | 11.6 / -24.0 |
| ZN 2 (diag) 5m boll(20,2.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 3114 | 5.5 | -30.1 | -35.2 | 35.6 | 0.37 / -2.08 / -2.43 | 11.2 / -24.5 |
| ZN 3 (diag) 15m boll(40,2.5) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 1651 | 4.8 | -30.9 | -36.0 | 35.6 | 0.24 / -1.53 / -1.78 | 7.7 / -27.9 |
| BTC 1 5m boll(20,2.5) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 1849 | 49.9 | -4.5 | 28.1 | 54.4 | 1.61 / -0.14 / 0.91 | 113.3 / 58.9 |
| BTC 2 5m boll(20,2.5) dir=with hold 120m all | negative pre-2023 | 1549 | -3.4 | -57.7 | -25.2 | 54.4 | -0.07 / -1.23 / -0.53 | 117.8 / 63.5 |
| BTC 3 15m boll(20,2.5) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 757 | 7.1 | -47.3 | -14.8 | 54.4 | 0.09 / -0.49 / -0.14 | 142.7 / 88.4 |
| BTC 4 15m boll(40,2.5) dir=with hold 240m all | positive pre-2023 | 484 | 276.2 | 221.8 | 254.4 | 54.4 | 1.77 / 1.42 / 1.63 | 231.6 / 177.2 |
| BTC 5 15m boll(20,2.5) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 690 | 19.0 | -35.4 | -2.8 | 54.4 | 0.22 / -0.33 / -0.00 | 156.0 / 101.7 |
| BTC 6 5m boll(20,2.5) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 1240 | 21.4 | -32.9 | -0.3 | 54.4 | 0.34 / -0.53 / -0.01 | 128.7 / 74.3 |
| BTC 7 15m boll(40,2.5) dir=with hold 180m all | positive pre-2023 | 534 | 180.7 | 126.4 | 158.8 | 54.4 | 1.38 / 0.97 / 1.21 | 145.4 / 91.0 |
| BTC 8 5m boll(20,2.5) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 794 | 7.9 | -46.4 | -13.8 | 54.4 | 0.13 / -0.83 / -0.25 | 78.7 / 24.4 |
| BTC 9 5m boll(40,2.5) dir=with hold 120m all | negative pre-2023 | 1355 | -4.1 | -58.5 | -25.9 | 54.4 | -0.07 / -1.15 / -0.50 | 65.4 / 11.0 |
| BTC 10 (diag) 5m boll(20,2.0) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 885 | 7.9 | -46.5 | -14.0 | 54.4 | 0.11 / -0.59 / -0.17 | 137.4 / 83.0 |
| HO 1 5m boll(20,2.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 2956 | 11.8 | -0.9 | 0.5 | 12.8 | 0.13 / -0.03 / -0.01 | 120.6 / 107.8 |
| HO 2 5m boll(20,2.0) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 4484 | 1.9 | -10.9 | -9.4 | 12.8 | 0.02 / -0.21 / -0.19 | 76.4 / 63.7 |
| HO 3 5m boll(20,2.0) dir=against hold 120m day | gross-positive, cost-negative pre-2023 | 6459 | 1.0 | -11.8 | -10.3 | 12.8 | 0.01 / -0.34 / -0.30 | 54.3 / 41.5 |
| HO 4 15m boll(40,2.5) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 4163 | 6.2 | -6.6 | -5.1 | 12.8 | 0.12 / -0.13 / -0.10 | 60.3 / 47.6 |
| HO 5 15m boll(40,2.5) dir=with hold 120m all | negative pre-2023 | 4775 | -1.3 | -14.1 | -12.6 | 12.8 | -0.03 / -0.37 / -0.33 | 44.1 / 31.3 |
| HO 6 15m boll(40,2.5) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 3796 | 4.2 | -8.6 | -7.1 | 12.8 | 0.06 / -0.14 / -0.12 | 37.2 / 24.5 |
| HO 7 5m boll(20,2.0) dir=against hold 240m all | positive pre-2023 | 9398 | 18.7 | 5.9 | 7.5 | 12.8 | 0.62 / 0.19 / 0.24 | 25.3 / 12.5 |
| HO 8 5m boll(20,2.5) dir=with hold 240m all | gross-positive, cost-negative pre-2023 | 6836 | 10.9 | -1.9 | -0.3 | 12.8 | 0.28 / -0.04 / -0.00 | 27.7 / 14.9 |
| HO 9 5m boll(40,2.5) dir=with hold 180m day | gross-positive, cost-negative pre-2023 | 2752 | 4.2 | -8.6 | -7.1 | 12.8 | 0.06 / -0.13 / -0.11 | 30.8 / 18.0 |
| HO 10 5m boll(20,2.5) dir=with hold 180m all | gross-positive, cost-negative pre-2023 | 8039 | 12.4 | -0.4 | 1.2 | 12.8 | 0.42 / -0.01 / 0.04 | 21.3 / 8.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 9 cells pass the clean rule against a replicate mean of 11.1 (p(count) = 0.83, p(top) = 0.94); CL: 2 cells pass the clean rule against a replicate mean of 3.0 (p(count) = 0.80, p(top) = 0.92); ES: 8 cells pass the clean rule against a replicate mean of 4.5 (p(count) = 0.09, p(top) = 0.89); GC: 3 cells pass the clean rule against a replicate mean of 5.3 (p(count) = 0.89, p(top) = 0.86); HO: 14 cells pass the clean rule against a replicate mean of 10.7 (p(count) = 0.18, p(top) = 0.29); NQ: 26 cells pass the clean rule against a replicate mean of 15.4 (p(count) = 0.01, p(top) = 0.55); RTY: 7 cells pass the clean rule against a replicate mean of 6.6 (p(count) = 0.47, p(top) = 0.64); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 49 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.25 (NQ 15m boll(40,2.5) dir=against hold 240m all); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 5; 2x-slippage all-in uplift >= +0.10 for 7; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell NQ 15m boll(20,2.5) dir=against hold 120m day: uplift +0.19/+0.17/+0.28, boot lo +0.02, plateau 0.00, 2x-slip +0.21, wd corr +0.15, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'gross-positive, cost-negative pre-2023': 31, 'negative pre-2023': 10, 'positive pre-2023': 8}.

- **Manual review of the lead: NQ 15-minute Bollinger(20, 2.5 SD) cross-out traded AGAINST (fade), held 120 minutes, no stop, day session.** Standalone Sharpe 0.70 / 0.65 / 1.01 on clean / H1 / H2; uplift at 20% share +0.19 / +0.17 / +0.28 (10%: +0.10/+0.12/+0.16; 30%: +0.27/+0.14/+0.37; 50%: +0.36/-0.06/+0.44); bootstrap lower bound +0.02; 2x slippage all-in +0.21; worst-decile correlation +0.15; ERA flag gross-positive, cost-negative pre-2023. It fails the worst-week gate (the pair's worst week gets 24.0% worse at 20% share and 12.0% at 10%, above the share allowance), the plateau (0.00), and the out-of-selection sub-gate (Sharpe 0.85 against null p95 1.60). Replication (amendment 2): 2 of 4 hold - H0 2023-02..07 standalone Sharpe +0.74 on 116 trades; alternating months odd +0.22 / even +0.18 against +0.22 overall; ES -0.01 and RTY -0.05 fail. Sizing: about 12.6 NQ contracts at 100% of pair volatility, 2.5 NQ at 20% share; worst single trade $15.0k per NQ contract, i.e. about $38k at 2.5 contracts (no stop). It trades NQ, so it needs a separate account. It is the NQ appearance of the 'fade a fresh extension in the day session and hold two hours' pattern (see CANDIDATES family entry), and the NQ Bollinger fade at 240 minutes (NQ 15m boll(40,2.5) against, all-hours) has the best all-in uplift of the family (+0.25).

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q12.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q12/ (`Q12_CO_all_selected_scored.csv`).

DONE Q12
