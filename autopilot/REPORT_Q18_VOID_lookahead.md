# REPORT Q18 - Q18: distance from the RTH open in ADR20 units, with/against, time exit

**Verdict: FOUND-CANDIDATE (needs full verification). FOUND 55, LEAD 4, INSURANCE 58.** 70 selected cells (+0 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +1.48; best pair-window standalone Sharpe +5.72.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: distance from the RTH open in ADR20 units, with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         56 |        22 |               5.131 |                2 |         10 |            0 |
| CL    |      96 |         56 |        18 |               3.509 |                2 |         10 |            0 |
| ES    |      96 |         58 |        16 |               3.275 |                2 |         10 |            0 |
| GC    |      96 |         54 |        17 |               4.803 |                2 |         10 |            0 |
| HO    |      96 |         56 |        17 |               4.27  |                2 |         10 |            0 |
| NQ    |      96 |         60 |        24 |               3.105 |                2 |         10 |            0 |
| RTY   |      96 |         56 |        20 |               3.751 |                2 |         10 |            0 |
| ZN    |      96 |         60 |         3 |               1.516 |                2 |          0 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   16 |            9.955 |              19 |      0.045 |                       1.999 |            0.719 |           0.965 |    0     |       3.275 |                1.86  |
| NQ    |     200 |                   24 |           19.065 |              32 |      0.145 |                       1.953 |            1.043 |           1.298 |    0     |       3.105 |                2.16  |
| RTY   |     200 |                   20 |           11.76  |              21 |      0.025 |                       2.542 |            0.786 |           1.027 |    0     |       3.751 |                1.93  |
| GC    |     200 |                   17 |           10.83  |              23 |      0.01  |                       3.458 |            0.743 |           1.043 |    0     |       4.803 |                1.876 |
| CL    |     200 |                   18 |            6.18  |              17 |      0     |                       2.593 |            0.646 |           0.969 |    0     |       3.509 |                1.709 |
| ZN    |     200 |                    3 |            0.06  |               1 |      0     |                       1.235 |            0.532 |           1.356 |    0.005 |       1.453 |                1.356 |
| BTC   |     200 |                   22 |           15.25  |              26 |      0.04  |                       3.841 |            0.896 |           1.192 |    0     |       5.131 |                2.086 |
| HO    |     200 |                   17 |           13.705 |              25 |      0.21  |                       3.146 |            0.878 |           1.135 |    0     |       4.27  |                2.058 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m openDist(0,0.5) dir=against hold 240m all | 333 | 2 | 3.27 | 2.14 | 3.10 | 2.94 / 1.10 | 0.62 / 0.58 / 0.80 | 0.62 | -0.46 | 1.00 | 0.46 | 0.75 | 526 | FOUND-CAND |
| ES 2 | 5m openDist(0,0.5) dir=against hold 180m all | 446 | 2 | 3.16 | 1.98 | 3.20 | 3.32 / 0.67 | 0.58 / 0.30 / 0.80 | 0.54 | -0.50 | 1.00 | 0.43 | 1.00 | 710 | FOUND-CAND |
| ES 3 | 15m openDist(0,0.5) dir=against hold 180m all | 380 | 2 | 3.07 | 1.92 | 2.85 | 2.73 / 0.72 | 0.65 / 0.45 / 0.82 | 0.61 | -0.37 | 1.00 | 0.46 | 0.75 | 603 | FOUND-CAND |
| ES 4 | 5m openDist(0,0.5) dir=against hold 240m all | 381 | 2 | 2.41 | 2.16 | 2.94 | 3.78 / 1.20 | 0.50 / 0.63 / 1.07 | 0.61 | -0.55 | 1.00 | 0.45 | 1.00 | 610 | FOUND-CAND |
| ES 5 | 5m openDist(0,0.75) dir=against hold 240m all | 127 | 2 | 2.00 | 1.53 | 2.11 | 2.31 / 0.73 | 0.35 / 0.39 / 0.64 | 0.39 | -0.56 | 1.00 | 0.24 | 1.00 | 219 | FOUND-CAND |
| ES 6 | 15m openDist(0,0.75) dir=against hold 240m all | 113 | 2 | 1.49 | 1.25 | 1.69 | 2.04 / 1.23 | 0.32 / 0.36 / 0.61 | 0.37 | -0.55 | 0.99 | 0.20 | 1.00 | 193 | FOUND-CAND |
| ES 7 | 5m openDist(0,0.5) dir=against hold 120m all | 552 | 2 | 1.33 | 1.47 | 1.83 | 2.87 / 0.80 | 0.31 / 0.20 / 0.68 | 0.32 | -0.53 | 1.00 | 0.22 | 1.00 | 875 | FOUND-CAND |
| ES 8 | 15m openDist(0,0.5) dir=against hold 120m all | 476 | 2 | 1.21 | 1.30 | 1.55 | 2.04 / 0.83 | 0.33 / 0.04 / 0.62 | 0.30 | -0.23 | 1.00 | 0.17 | 0.50 | 739 | NO |
| ES 9 | 5m openDist(0,0.75) dir=against hold 180m all | 161 | 2 | 1.10 | 1.26 | 1.61 | 2.52 / 0.93 | 0.21 / 0.70 / 0.45 | 0.29 | -0.27 | 1.00 | 0.14 | 1.00 | 267 | FOUND-CAND |
| ES 10 | 15m openDist(0,0.75) dir=against hold 180m all | 137 | 2 | 0.95 | 1.14 | 1.48 | 2.31 / 1.21 | 0.21 / 0.62 / 0.71 | 0.34 | -0.44 | 1.00 | 0.17 | 1.00 | 230 | FOUND-CAND |
| NQ 1 | 5m openDist(0,0.5) dir=against hold 180m all | 447 | 2 | 3.10 | 1.41 | 3.09 | 3.28 / 1.27 | 0.63 / 0.52 / 1.16 | 0.73 | -0.54 | 1.00 | 0.51 | 0.50 | 736 | LEAD(gate3-7 fail: plateau ) |
| NQ 2 | 15m openDist(0,0.5) dir=against hold 240m all | 344 | 2 | 2.92 | 1.70 | 3.15 | 3.65 / 1.23 | 0.58 / 0.60 / 1.26 | 0.74 | -0.46 | 1.00 | 0.51 | 0.75 | 560 | FOUND-CAND |
| NQ 3 | 5m openDist(0,0.5) dir=against hold 240m all | 390 | 2 | 2.69 | 1.89 | 3.23 | 4.13 / 1.63 | 0.57 / 0.59 / 1.31 | 0.74 | -0.49 | 1.00 | 0.53 | 1.00 | 635 | FOUND-CAND |
| NQ 4 | 15m openDist(0,0.5) dir=against hold 180m all | 389 | 2 | 2.39 | 1.56 | 2.56 | 2.92 / 1.39 | 0.52 / 0.56 / 0.87 | 0.61 | -0.50 | 1.00 | 0.38 | 0.75 | 638 | FOUND-CAND |
| NQ 5 | 15m openDist(0,0.5) dir=against hold 120m all | 471 | 2 | 1.59 | 0.99 | 1.72 | 1.90 / 1.23 | 0.39 / 0.08 / 0.62 | 0.40 | -0.51 | 1.00 | 0.20 | 0.75 | 751 | NO |
| NQ 6 | 5m openDist(0,0.5) dir=against hold 120m all | 555 | 2 | 1.56 | 1.16 | 1.74 | 2.03 / 1.32 | 0.39 / 0.16 / 0.51 | 0.39 | -0.38 | 1.00 | 0.21 | 1.00 | 883 | FOUND-CAND |
| NQ 7 | 5m openDist(0,0.5) dir=against hold 60m all | 709 | 2 | 1.40 | 0.87 | 1.65 | 2.05 / 1.30 | 0.32 / 0.06 / 0.86 | 0.38 | -0.68 | 1.00 | 0.20 | 1.00 | 1116 | NO |
| NQ 8 | 5m openDist(0,0.75) dir=against hold 240m all | 132 | 2 | 1.36 | 1.26 | 1.94 | 3.15 / 1.21 | 0.22 / 0.37 / 0.64 | 0.32 | -0.22 | 1.00 | 0.19 | 1.00 | 231 | FOUND-CAND |
| NQ 9 | 5m openDist(0,0.75) dir=against hold 180m all | 161 | 2 | 1.36 | 1.06 | 2.05 | 3.03 / 1.04 | 0.25 / 0.57 / 0.97 | 0.45 | -0.04 | 1.00 | 0.24 | 0.75 | 280 | FOUND-CAND |
| NQ 10 | 15m openDist(0,0.75) dir=against hold 240m all | 117 | 2 | 1.16 | 1.15 | 1.57 | 2.20 / 1.21 | 0.20 / 0.34 / 0.61 | 0.30 | -0.23 | 1.00 | 0.13 | 1.00 | 201 | FOUND-CAND |
| RTY 1 | 5m openDist(0,0.5) dir=against hold 240m all | 391 | 2 | 3.75 | 2.46 | 3.48 | 3.20 / 1.12 | 0.71 / 0.06 / 1.26 | 0.71 | -0.57 | 1.00 | 0.54 | 0.75 | 638 | NO |
| RTY 2 | 15m openDist(0,0.5) dir=against hold 240m all | 334 | 2 | 3.69 | 2.67 | 3.58 | 3.52 / 1.31 | 0.72 / 0.26 / 1.23 | 0.74 | -0.47 | 1.00 | 0.56 | 0.75 | 554 | FOUND-CAND |
| RTY 3 | 15m openDist(0,0.5) dir=against hold 180m all | 381 | 2 | 3.43 | 2.55 | 3.05 | 2.68 / 1.43 | 0.68 / 0.00 / 1.14 | 0.65 | -0.50 | 1.00 | 0.47 | 0.75 | 630 | NO |
| RTY 4 | 5m openDist(0,0.5) dir=against hold 180m all | 443 | 2 | 3.12 | 2.51 | 3.02 | 2.96 / 1.06 | 0.63 / 0.05 / 1.25 | 0.64 | -0.61 | 1.00 | 0.47 | 0.75 | 731 | NO |
| RTY 5 | 15m openDist(0,0.75) dir=against hold 240m all | 114 | 2 | 2.16 | 1.77 | 1.66 | 0.97 / 1.07 | 0.37 / -0.31 / 0.58 | 0.30 | -0.27 | 1.00 | 0.13 | 0.75 | 185 | NO |
| RTY 6 | 15m openDist(0,0.75) dir=against hold 60m all | 206 | 2 | 2.15 | 0.79 | 1.67 | 0.96 / 1.08 | 0.43 / -0.31 / 0.41 | 0.29 | -0.22 | 1.00 | 0.15 | 0.75 | 323 | NO |
| RTY 7 | 5m openDist(0,0.75) dir=against hold 240m all | 125 | 2 | 1.93 | 1.75 | 1.71 | 1.31 / 1.09 | 0.32 / -0.08 / 0.53 | 0.28 | -0.30 | 1.00 | 0.14 | 0.75 | 210 | NO |
| RTY 8 | 5m openDist(0,0.75) dir=against hold 180m all | 156 | 2 | 1.81 | 1.55 | 1.64 | 1.44 / 1.00 | 0.31 / -0.22 / 0.79 | 0.30 | -0.02 | 1.00 | 0.13 | 0.75 | 251 | NO |
| RTY 9 | 15m openDist(0,0.75) dir=against hold 180m all | 132 | 2 | 1.71 | 1.37 | 1.57 | 1.41 / 0.82 | 0.29 / -0.28 / 0.79 | 0.29 | 0.05 | 1.00 | 0.10 | 0.75 | 211 | NO |
| RTY 10 | 5m openDist(0,0.5) dir=against hold 120m all | 536 | 2 | 1.66 | 1.84 | 2.24 | 3.27 / 0.98 | 0.36 / 0.10 / 1.02 | 0.42 | -0.86 | 1.00 | 0.29 | 1.00 | 888 | FOUND-CAND |
| GC 1 | 5m openDist(0,0.5) dir=against hold 240m all | 417 | 2 | 4.80 | 3.92 | 4.20 | 5.22 / 1.25 | 0.89 / 2.42 / 2.47 | 1.46 | 0.28 | 1.00 | 1.18 | 0.75 | 663 | FOUND-CAND |
| GC 2 | 15m openDist(0,0.5) dir=against hold 240m all | 374 | 2 | 4.39 | 3.46 | 3.74 | 4.44 / 1.37 | 0.81 / 2.37 / 1.98 | 1.29 | 0.23 | 1.00 | 1.03 | 0.75 | 589 | FOUND-CAND |
| GC 3 | 5m openDist(0,0.5) dir=against hold 180m all | 473 | 2 | 4.16 | 3.18 | 4.19 | 5.46 / 1.55 | 0.73 / 2.65 / 2.30 | 1.31 | -0.31 | 1.00 | 1.05 | 0.75 | 749 | FOUND-CAND |
| GC 4 | 15m openDist(0,0.5) dir=against hold 180m all | 414 | 2 | 3.91 | 2.87 | 3.64 | 4.31 / 1.19 | 0.69 / 2.14 / 1.75 | 1.11 | -0.34 | 1.00 | 0.87 | 1.00 | 650 | FOUND-CAND |
| GC 5 | 5m openDist(0,0.5) dir=against hold 120m all | 570 | 2 | 3.61 | 2.39 | 3.88 | 5.28 / 1.24 | 0.65 / 2.32 / 2.18 | 1.22 | -0.39 | 1.00 | 0.98 | 1.00 | 899 | FOUND-CAND |
| GC 6 | 15m openDist(0,0.5) dir=against hold 120m all | 481 | 2 | 2.96 | 1.88 | 3.21 | 4.24 / 1.17 | 0.51 / 2.17 / 1.70 | 0.99 | -0.47 | 1.00 | 0.74 | 0.75 | 757 | FOUND-CAND |
| GC 7 | 5m openDist(0,0.5) dir=against hold 60m all | 686 | 2 | 2.85 | 1.26 | 3.22 | 4.48 / 1.17 | 0.53 / 2.61 / 1.84 | 1.06 | -0.35 | 1.00 | 0.83 | 0.75 | 1107 | FOUND-CAND |
| GC 8 | 5m openDist(0,0.75) dir=against hold 240m all | 150 | 2 | 2.81 | 2.19 | 2.40 | 2.98 / 1.12 | 0.43 / 1.49 / 1.25 | 0.81 | 0.28 | 1.00 | 0.56 | 1.00 | 251 | FOUND-CAND |
| GC 9 | 15m openDist(0,0.5) dir=against hold 60m all | 556 | 2 | 2.56 | 0.85 | 2.56 | 3.23 / 1.54 | 0.43 / 0.95 / 1.50 | 0.71 | -0.25 | 1.00 | 0.49 | 0.75 | 890 | FOUND-CAND |
| GC 10 | 15m openDist(0,0.75) dir=against hold 240m all | 129 | 2 | 2.54 | 2.25 | 2.53 | 3.15 / 1.28 | 0.37 / 1.95 / 0.94 | 0.73 | 0.27 | 1.00 | 0.48 | 1.00 | 214 | FOUND-CAND |
| CL 1 | 5m openDist(0,0.5) dir=against hold 240m all | 461 | 2 | 3.51 | 3.32 | 4.37 | 5.81 / 1.04 | 0.73 / 0.94 / 2.40 | 1.06 | -0.24 | 1.00 | 0.87 | 1.00 | 768 | FOUND-CAND |
| CL 2 | 5m openDist(0,0.5) dir=against hold 180m all | 525 | 2 | 3.37 | 2.79 | 4.09 | 5.52 / 0.94 | 0.70 / 1.20 / 2.50 | 1.08 | -0.23 | 1.00 | 0.90 | 1.00 | 882 | FOUND-CAND |
| CL 3 | 15m openDist(0,0.5) dir=against hold 180m all | 468 | 2 | 2.77 | 2.42 | 3.35 | 4.40 / 1.02 | 0.59 / 0.96 / 2.11 | 0.91 | -0.30 | 1.00 | 0.73 | 1.00 | 776 | FOUND-CAND |
| CL 4 | 15m openDist(0,0.5) dir=against hold 240m all | 411 | 2 | 2.76 | 3.07 | 3.73 | 5.17 / 0.98 | 0.58 / 0.89 / 2.22 | 0.93 | -0.29 | 1.00 | 0.74 | 1.00 | 679 | FOUND-CAND |
| CL 5 | 5m openDist(0,0.5) dir=against hold 120m all | 616 | 2 | 2.56 | 2.07 | 2.97 | 3.97 / 0.75 | 0.51 / 0.96 / 2.38 | 0.88 | -0.20 | 1.00 | 0.70 | 1.00 | 1022 | FOUND-CAND |
| CL 6 | 5m openDist(0,0.75) dir=against hold 240m all | 150 | 2 | 2.44 | 1.86 | 3.06 | 3.99 / 1.14 | 0.51 / 0.67 / 1.37 | 0.73 | -0.41 | 1.00 | 0.52 | 0.75 | 267 | FOUND-CAND |
| CL 7 | 15m openDist(0,0.5) dir=against hold 120m all | 529 | 2 | 2.24 | 1.65 | 2.85 | 3.80 / 1.01 | 0.47 / 0.98 / 1.97 | 0.77 | -0.31 | 1.00 | 0.61 | 1.00 | 871 | FOUND-CAND |
| CL 8 | 5m openDist(0,0.75) dir=against hold 120m all | 231 | 2 | 2.21 | 1.46 | 2.50 | 3.17 / 1.11 | 0.45 / 0.55 / 1.54 | 0.68 | -0.35 | 1.00 | 0.47 | 0.75 | 391 | FOUND-CAND |
| CL 9 | 15m openDist(0,0.75) dir=against hold 240m all | 132 | 2 | 2.16 | 1.80 | 2.98 | 4.11 / 1.01 | 0.45 / 0.79 / 1.46 | 0.71 | -0.43 | 1.00 | 0.50 | 0.50 | 236 | LEAD(gate3-7 fail: plateau ) |
| CL 10 | 5m openDist(0,0.75) dir=against hold 180m all | 182 | 2 | 1.90 | 1.69 | 2.60 | 3.56 / 0.81 | 0.39 / 0.54 / 1.27 | 0.59 | -0.40 | 1.00 | 0.40 | 0.75 | 316 | FOUND-CAND |
| BTC 1 | 5m openDist(0,0.5) dir=against hold 240m all | 404 | 2 | 5.13 | 3.51 | 5.72 | 6.81 / 1.27 | 0.84 / 1.84 / 0.97 | 0.94 | -0.14 | 1.00 | 0.79 | 1.00 | 644 | FOUND-CAND |
| BTC 2 | 5m openDist(0,0.5) dir=against hold 180m all | 465 | 2 | 4.97 | 3.14 | 5.43 | 6.25 / 1.63 | 0.88 / 1.64 / 0.92 | 0.94 | -0.38 | 1.00 | 0.78 | 1.00 | 729 | FOUND-CAND |
| BTC 3 | 15m openDist(0,0.5) dir=against hold 240m all | 320 | 2 | 4.54 | 3.34 | 4.98 | 5.69 / 1.29 | 0.73 / 1.55 / 0.93 | 0.84 | -0.23 | 1.00 | 0.68 | 1.00 | 517 | FOUND-CAND |
| BTC 4 | 15m openDist(0,0.5) dir=against hold 180m all | 363 | 2 | 3.96 | 2.64 | 4.31 | 4.88 / 1.19 | 0.65 / 1.13 / 0.90 | 0.72 | -0.36 | 1.00 | 0.57 | 1.00 | 578 | FOUND-CAND |
| BTC 5 | 5m openDist(0,0.75) dir=against hold 240m all | 154 | 2 | 3.59 | 3.22 | 3.67 | 3.82 / 1.28 | 0.68 / 0.97 / 0.53 | 0.67 | 0.06 | 1.00 | 0.50 | 1.00 | 234 | FOUND-CAND |
| BTC 6 | 5m openDist(0,0.75) dir=against hold 180m all | 190 | 2 | 3.57 | 2.89 | 3.69 | 3.88 / 1.09 | 0.66 / 1.01 / 0.64 | 0.68 | 0.11 | 1.00 | 0.51 | 0.75 | 283 | FOUND-CAND |
| BTC 7 | 15m openDist(0,0.75) dir=against hold 240m all | 125 | 2 | 3.35 | 2.99 | 3.26 | 3.11 / 1.40 | 0.60 / 1.05 / 0.50 | 0.61 | -0.37 | 1.00 | 0.44 | 0.75 | 188 | FOUND-CAND |
| BTC 8 | 5m openDist(0,0.5) dir=against hold 120m all | 556 | 2 | 3.21 | 2.23 | 4.06 | 5.71 / 1.33 | 0.52 / 1.17 / 0.83 | 0.63 | -0.29 | 1.00 | 0.50 | 1.00 | 864 | FOUND-CAND |
| BTC 9 | 5m openDist(0,0.75) dir=against hold 120m all | 224 | 2 | 3.07 | 2.33 | 3.39 | 3.90 / 1.14 | 0.56 / 1.11 / 0.60 | 0.61 | 0.46 | 1.00 | 0.44 | 0.50 | 337 | LEAD |
| BTC 10 | 15m openDist(0,0.75) dir=against hold 180m all | 151 | 2 | 3.02 | 2.66 | 3.14 | 3.42 / 1.68 | 0.57 / 0.85 / 0.49 | 0.57 | -0.11 | 1.00 | 0.41 | 0.75 | 224 | FOUND-CAND |
| HO 1 | 5m openDist(0,0.5) dir=against hold 240m all | 460 | 2 | 4.27 | 3.08 | 3.96 | 5.31 / 1.32 | 0.83 / 1.80 / 3.06 | 1.46 | -0.30 | 1.00 | 1.15 | 0.75 | 756 | FOUND-CAND |
| HO 2 | 5m openDist(0,0.5) dir=against hold 180m all | 507 | 2 | 4.03 | 2.94 | 3.67 | 4.72 / 1.29 | 0.80 / 1.56 / 2.63 | 1.31 | -0.30 | 1.00 | 1.02 | 0.75 | 846 | FOUND-CAND |
| HO 3 | 5m openDist(0,0.5) dir=against hold 120m all | 601 | 2 | 3.58 | 2.85 | 3.16 | 4.03 / 1.38 | 0.70 / 1.26 / 2.54 | 1.19 | -0.29 | 1.00 | 0.89 | 0.75 | 997 | FOUND-CAND |
| HO 4 | 15m openDist(0,0.5) dir=against hold 240m all | 401 | 2 | 3.50 | 2.76 | 3.63 | 4.67 / 1.39 | 0.70 / 1.40 / 2.20 | 1.14 | -0.23 | 1.00 | 0.88 | 1.00 | 653 | FOUND-CAND |
| HO 5 | 15m openDist(0,0.5) dir=against hold 180m all | 437 | 2 | 3.37 | 2.26 | 3.13 | 3.91 / 1.14 | 0.67 / 1.48 / 1.92 | 1.06 | -0.23 | 1.00 | 0.77 | 1.00 | 721 | FOUND-CAND |
| HO 6 | 15m openDist(0,0.5) dir=against hold 120m all | 513 | 2 | 3.07 | 1.89 | 2.85 | 3.56 / 1.40 | 0.59 / 1.17 / 2.00 | 0.98 | -0.24 | 1.00 | 0.69 | 0.75 | 840 | FOUND-CAND |
| HO 7 | 5m openDist(0,0.75) dir=against hold 240m all | 152 | 2 | 2.84 | 1.50 | 2.83 | 3.55 / 1.32 | 0.57 / 0.57 / 1.83 | 0.88 | -0.22 | 1.00 | 0.62 | 0.75 | 255 | FOUND-CAND |
| HO 8 | 15m openDist(0,0.75) dir=against hold 240m all | 124 | 2 | 2.55 | 1.25 | 2.46 | 3.00 / 1.26 | 0.53 / 0.27 / 1.76 | 0.79 | -0.26 | 1.00 | 0.51 | 0.75 | 204 | FOUND-CAND |
| HO 9 | 5m openDist(0,0.75) dir=against hold 180m all | 180 | 2 | 2.14 | 1.37 | 2.37 | 3.09 / 1.90 | 0.41 / 0.49 / 1.63 | 0.72 | -0.23 | 1.00 | 0.45 | 0.75 | 297 | FOUND-CAND |
| HO 10 | 5m openDist(0,0.75) dir=against hold 120m all | 222 | 2 | 2.11 | 1.15 | 2.50 | 3.42 / 1.22 | 0.41 / 0.66 / 1.95 | 0.82 | -0.21 | 1.00 | 0.54 | 0.75 | 363 | LEAD |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 70 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 58 / 58 / 59 / 58 |
| all-in uplift @20% > 0 (all scored) | 70 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 70 |
| standalone pair-window Sharpe above own random-entry null p95 | 70 |
| worst-decile corr <= +0.30 | 69 |
| plateau >= 0.75 | 66 |
| all-in uplift at 2x slippage >= +0.10 | 70 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 210 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 5m openDist(0,0.5) dir=against hold 180m all | clean | 4.95 | 23.26 | -50307 | -36489 | 134882 | -69253 | 33.31 | 20.0 | 2.34 | -80323 | 213938 | -86373 |
| BTC 5m openDist(0,0.5) dir=against hold 180m all | H1 | 5.27 | 14.46 | -76676 | -58259 | 150574 | -124772 | 9.35 | 17.9 | 4.47 | -42781 | 132441 | -53463 |
| BTC 5m openDist(0,0.5) dir=against hold 180m all | H2 | 7.88 | 141.34 | -8520 | -2209 | 65934 | -13285 | 24.62 | 5.6 | 3.40 | -74859 | 200232 | -75775 |
| BTC 5m openDist(0,0.5) dir=against hold 180m all | all | 5.43 | 21.98 | -54408 | -36955 | 150574 | -124772 | 49.97 | 16.7 | 2.86 | -79081 | 213938 | -86373 |
| CL 5m openDist(0,0.5) dir=against hold 180m all | clean | 3.36 | 8.74 | -84618 | -64760 | 225113 | -118728 | 13.56 | 28.6 | 2.16 | -76641 | 259404 | -82593 |
| CL 5m openDist(0,0.5) dir=against hold 180m all | H1 | 6.39 | 26.59 | -40266 | -32467 | 41009 | -41009 | 28.63 | 21.4 | 4.03 | -61106 | 130624 | -62097 |
| CL 5m openDist(0,0.5) dir=against hold 180m all | H2 | 6.59 | 64.71 | -52090 | -26404 | 294220 | -87313 | 16.28 | 8.3 | 4.98 | -72543 | 167072 | -82811 |
| CL 5m openDist(0,0.5) dir=against hold 180m all | all | 4.09 | 18.73 | -77095 | -56938 | 294220 | -118728 | 30.64 | 23.2 | 3.07 | -75775 | 259404 | -82811 |
| ES 15m openDist(0,0.5) dir=against hold 180m all | clean | 3.00 | 7.09 | -89630 | -68979 | 586465 | -165828 | 4.66 | 35.2 | 2.11 | -77678 | 194638 | -78875 |
| ES 15m openDist(0,0.5) dir=against hold 180m all | H1 | 1.15 | 2.55 | -128175 | -106705 | 236484 | -152485 | 1.65 | 42.9 | 3.28 | -64713 | 162263 | -83909 |
| ES 15m openDist(0,0.5) dir=against hold 180m all | H2 | 4.02 | 10.46 | -129076 | -90180 | 217815 | -135324 | 7.98 | 22.2 | 3.12 | -84897 | 197322 | -87269 |
| ES 15m openDist(0,0.5) dir=against hold 180m all | all | 2.85 | 6.85 | -110152 | -83050 | 586465 | -165828 | 8.29 | 33.9 | 2.52 | -79974 | 197322 | -87269 |
| GC 5m openDist(0,0.5) dir=against hold 240m all | clean | 4.81 | 21.58 | -47846 | -37583 | 115422 | -68183 | 37.78 | 21.0 | 2.35 | -77792 | 253397 | -81964 |
| GC 5m openDist(0,0.5) dir=against hold 240m all | H1 | 3.90 | 59.82 | -46547 | -40444 | 152774 | -60890 | 22.65 | 14.3 | 5.25 | -49174 | 151713 | -54981 |
| GC 5m openDist(0,0.5) dir=against hold 240m all | H2 | 6.91 | 73.17 | -54326 | -33154 | 162287 | -76143 | 32.33 | 8.3 | 4.95 | -79835 | 189858 | -80017 |
| GC 5m openDist(0,0.5) dir=against hold 240m all | all | 4.20 | 39.94 | -50972 | -39123 | 162287 | -76143 | 80.52 | 17.3 | 3.38 | -77599 | 253397 | -81964 |
| HO 5m openDist(0,0.5) dir=against hold 240m all | clean | 4.39 | 12.66 | -80228 | -57763 | 208873 | -114994 | 19.17 | 27.6 | 2.29 | -79688 | 246516 | -92746 |
| HO 5m openDist(0,0.5) dir=against hold 240m all | H1 | 7.53 | 174.76 | -11138 | -7855 | 40117 | -11647 | 50.58 | 14.3 | 4.62 | -56087 | 125102 | -60872 |
| HO 5m openDist(0,0.5) dir=against hold 240m all | H2 | 6.22 | 41.74 | -160406 | -95011 | 324096 | -194059 | 25.60 | 11.1 | 5.55 | -72783 | 187335 | -77724 |
| HO 5m openDist(0,0.5) dir=against hold 240m all | all | 3.96 | 24.40 | -95541 | -62835 | 324096 | -194059 | 44.21 | 21.4 | 3.37 | -77748 | 246516 | -92746 |
| NQ 5m openDist(0,0.5) dir=against hold 180m all | clean | 3.02 | 8.31 | -71766 | -59516 | 237520 | -103230 | 11.60 | 32.4 | 2.09 | -78891 | 216120 | -85766 |
| NQ 5m openDist(0,0.5) dir=against hold 180m all | H1 | 1.84 | 4.09 | -145557 | -123537 | 287751 | -207914 | 2.68 | 35.7 | 3.35 | -78779 | 163097 | -89592 |
| NQ 5m openDist(0,0.5) dir=against hold 180m all | H2 | 4.91 | 16.36 | -76842 | -66475 | 239653 | -84594 | 8.08 | 19.4 | 3.64 | -78655 | 214321 | -83867 |
| NQ 5m openDist(0,0.5) dir=against hold 180m all | all | 3.09 | 8.15 | -94427 | -75190 | 287751 | -207914 | 18.99 | 30.4 | 2.64 | -80133 | 216120 | -89592 |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | clean | 3.65 | 11.71 | -67411 | -50696 | 144848 | -116343 | 22.90 | 26.7 | 2.18 | -80694 | 208995 | -87876 |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | H1 | 0.71 | 1.07 | -115758 | -113180 | 346903 | -118930 | 0.51 | 32.1 | 3.09 | -62409 | 165307 | -75450 |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | H2 | 5.60 | 35.13 | -44237 | -39958 | 102105 | -49116 | 23.14 | 16.7 | 3.71 | -78097 | 202517 | -82524 |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | all | 3.58 | 10.51 | -88623 | -65137 | 346903 | -118930 | 16.88 | 25.6 | 2.67 | -79534 | 208995 | -87876 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m openDist(0,0.5) dir=against hold 240m all | 25.6 | 26.3 | 28.4 | 43.7 | 25.7 / 26.5 | 31.6 / 45.8 | INSURANCE |
| ES 5m openDist(0,0.5) dir=against hold 180m all | 20.4 | 26.4 | 31.0 | 38.2 | 31.4 / 30.7 | 22.4 / 30.6 | INSURANCE |
| ES 15m openDist(0,0.5) dir=against hold 180m all | 24.3 | -0.3 | 24.2 | 39.4 | 26.5 / 28.8 | 19.2 / 37.4 | INSURANCE |
| ES 5m openDist(0,0.5) dir=against hold 240m all | 21.4 | 22.3 | 27.9 | 53.7 | 21.7 / 25.1 | 29.3 / 42.2 | INSURANCE |
| ES 5m openDist(0,0.75) dir=against hold 240m all | 5.6 | 18.6 | 29.2 | 44.7 | 18.0 / 28.4 | 30.0 / 33.8 | INSURANCE |
| ES 15m openDist(0,0.75) dir=against hold 240m all | -2.0 | 17.3 | 29.0 | 46.8 | 16.7 / 28.2 | 30.0 / 29.9 | INSURANCE |
| ES 5m openDist(0,0.5) dir=against hold 120m all | -1.9 | 26.0 | 28.9 | 36.0 | 27.0 / 29.9 | 24.0 / 42.0 | INSURANCE |
| ES 5m openDist(0,0.75) dir=against hold 180m all | -4.1 | 16.8 | 27.2 | 33.9 | 16.1 / 25.2 | 41.9 / 50.1 | INSURANCE |
| ES 15m openDist(0,0.75) dir=against hold 180m all | -4.5 | 8.7 | 28.2 | 43.7 | 8.0 / 26.7 | 45.3 / 53.5 | INSURANCE |
| NQ 5m openDist(0,0.5) dir=against hold 180m all | 29.8 | 2.0 | 18.5 | 45.0 | 18.8 / 26.0 | -3.3 / 1.7 | NO |
| NQ 15m openDist(0,0.5) dir=against hold 240m all | 30.7 | 6.7 | 21.0 | 44.3 | 18.9 / 24.8 | 1.7 / 11.1 | INSURANCE |
| NQ 5m openDist(0,0.5) dir=against hold 240m all | 27.5 | 18.1 | 23.4 | 48.0 | 19.9 / 24.4 | 13.6 / 16.1 | INSURANCE |
| NQ 5m openDist(0,0.5) dir=against hold 60m all | -2.4 | 18.3 | 24.0 | 31.8 | 25.0 / 25.4 | 13.9 / 15.7 | INSURANCE |
| NQ 5m openDist(0,0.75) dir=against hold 240m all | -0.9 | 24.9 | 28.9 | 24.8 | 24.3 / 27.8 | 36.3 / 44.6 | INSURANCE |
| NQ 5m openDist(0,0.75) dir=against hold 180m all | 8.0 | 14.3 | 24.2 | 9.3 | 13.6 / 20.9 | 39.3 / 42.4 | INSURANCE |
| NQ 15m openDist(0,0.75) dir=against hold 240m all | -2.6 | 15.2 | 27.3 | 20.5 | 14.5 / 25.5 | 30.0 / 36.4 | INSURANCE |
| RTY 5m openDist(0,0.5) dir=against hold 240m all | 32.3 | 4.0 | 24.1 | 45.3 | 3.2 / 19.1 | 31.0 / 36.9 | INSURANCE |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | 34.0 | 2.9 | 26.2 | 49.8 | 2.1 / 22.7 | 35.4 / 34.9 | INSURANCE |
| RTY 15m openDist(0,0.5) dir=against hold 180m all | 25.5 | 8.9 | 27.8 | 46.8 | 8.2 / 24.9 | 34.5 / 43.9 | INSURANCE |
| RTY 5m openDist(0,0.5) dir=against hold 180m all | 24.6 | 12.8 | 24.2 | 42.7 | 12.1 / 20.8 | 18.2 / 41.0 | INSURANCE |
| RTY 15m openDist(0,0.75) dir=against hold 240m all | -1.5 | 5.9 | 23.4 | 31.1 | 6.0 / 24.7 | 0.8 / 14.7 | INSURANCE |
| RTY 15m openDist(0,0.75) dir=against hold 60m all | -2.0 | 17.5 | 26.8 | 32.7 | 20.2 / 29.2 | 13.0 / 24.5 | INSURANCE |
| RTY 5m openDist(0,0.75) dir=against hold 240m all | -3.7 | 11.3 | 26.6 | 35.1 | 10.6 / 26.0 | 21.1 / 28.6 | INSURANCE |
| RTY 5m openDist(0,0.5) dir=against hold 120m all | 5.1 | 19.6 | 27.7 | 43.6 | 19.0 / 25.3 | 31.7 / 41.7 | INSURANCE |
| GC 5m openDist(0,0.5) dir=against hold 240m all | 112.9 | 26.4 | 32.5 | 44.3 | 25.8 / 31.3 | 62.6 / 68.3 | INSURANCE |
| GC 15m openDist(0,0.5) dir=against hold 240m all | 93.7 | 28.0 | 32.6 | 48.3 | 27.4 / 32.6 | 62.2 / 62.0 | INSURANCE |
| GC 5m openDist(0,0.5) dir=against hold 180m all | 100.5 | 25.2 | 31.3 | 39.4 | 24.6 / 28.8 | 33.0 / 46.4 | INSURANCE |
| GC 15m openDist(0,0.5) dir=against hold 180m all | 76.8 | 28.0 | 32.0 | 39.1 | 27.4 / 31.6 | 44.3 / 51.1 | INSURANCE |
| GC 5m openDist(0,0.5) dir=against hold 120m all | 96.2 | 22.1 | 33.6 | 50.0 | 21.5 / 32.1 | 55.7 / 58.1 | INSURANCE |
| GC 15m openDist(0,0.5) dir=against hold 120m all | 71.2 | 9.3 | 24.7 | 41.8 | 23.4 / 26.2 | 35.7 / 47.1 | INSURANCE |
| GC 5m openDist(0,0.5) dir=against hold 60m all | 85.6 | -11.0 | 29.4 | 50.1 | 10.9 / 31.7 | 55.1 / 58.5 | INSURANCE |
| GC 5m openDist(0,0.75) dir=against hold 240m all | 62.7 | 7.2 | 23.6 | 38.9 | 20.5 / 26.7 | 20.8 / 33.5 | INSURANCE |
| GC 15m openDist(0,0.75) dir=against hold 240m all | 47.1 | 13.8 | 25.7 | 38.5 | 19.9 / 27.0 | 62.6 / 65.1 | INSURANCE |
| CL 5m openDist(0,0.5) dir=against hold 240m all | 63.7 | 26.4 | 31.3 | 37.8 | 25.8 / 28.5 | 46.5 / 54.3 | INSURANCE |
| CL 5m openDist(0,0.5) dir=against hold 180m all | 68.6 | 20.2 | 31.7 | 41.1 | 19.5 / 28.5 | 59.6 / 61.9 | INSURANCE |
| CL 15m openDist(0,0.5) dir=against hold 180m all | 54.1 | 26.9 | 33.1 | 39.9 | 26.3 / 30.9 | 46.8 / 54.7 | INSURANCE |
| CL 15m openDist(0,0.5) dir=against hold 240m all | 51.6 | 28.6 | 32.0 | 38.5 | 28.0 / 29.1 | 48.6 / 54.5 | INSURANCE |
| CL 5m openDist(0,0.5) dir=against hold 120m all | 62.4 | 9.1 | 22.4 | 41.1 | 8.4 / 18.5 | 43.4 / 52.1 | INSURANCE |
| CL 5m openDist(0,0.75) dir=against hold 240m all | 35.8 | 28.6 | 29.7 | 41.3 | 28.0 / 28.2 | 41.7 / 43.5 | INSURANCE |
| CL 15m openDist(0,0.5) dir=against hold 120m all | 46.4 | 23.9 | 28.0 | 42.2 | 23.3 / 25.9 | 40.8 / 52.6 | INSURANCE |
| CL 5m openDist(0,0.75) dir=against hold 120m all | 34.8 | 21.3 | 27.4 | 40.3 | 20.6 / 27.5 | 41.5 / 51.6 | INSURANCE |
| CL 15m openDist(0,0.75) dir=against hold 240m all | 30.9 | 27.2 | 29.6 | 43.5 | 26.6 / 28.1 | 46.3 / 46.3 | INSURANCE |
| CL 5m openDist(0,0.75) dir=against hold 180m all | 24.2 | 20.0 | 27.4 | 34.4 | 19.4 / 24.7 | 45.2 / 46.7 | INSURANCE |
| BTC 5m openDist(0,0.5) dir=against hold 180m all | 52.3 | 18.7 | 26.9 | 44.9 | 18.1 / 23.4 | 65.5 / 71.3 | INSURANCE |
| BTC 15m openDist(0,0.5) dir=against hold 240m all | 50.5 | 8.8 | 25.8 | 44.4 | 8.1 / 21.5 | 41.2 / 63.2 | INSURANCE |
| BTC 15m openDist(0,0.5) dir=against hold 180m all | 37.3 | 12.6 | 26.6 | 42.8 | 11.9 / 22.0 | 37.0 / 53.0 | INSURANCE |
| BTC 5m openDist(0,0.75) dir=against hold 240m all | 25.6 | 19.7 | 30.0 | 44.8 | 19.0 / 28.3 | 33.5 / 49.6 | INSURANCE |
| BTC 5m openDist(0,0.75) dir=against hold 180m all | 26.7 | 24.4 | 29.1 | 50.2 | 23.8 / 27.7 | 33.5 / 51.7 | INSURANCE |
| BTC 15m openDist(0,0.75) dir=against hold 240m all | 21.8 | 20.3 | 28.9 | 46.0 | 19.7 / 27.7 | 34.0 / 48.3 | INSURANCE |
| BTC 5m openDist(0,0.5) dir=against hold 120m all | 31.6 | 18.6 | 22.1 | 34.0 | 17.9 / 19.8 | 17.0 / 28.3 | INSURANCE |
| BTC 15m openDist(0,0.75) dir=against hold 180m all | 16.6 | 27.9 | 29.7 | 48.6 | 27.3 / 28.9 | 33.3 / 51.4 | INSURANCE |
| HO 5m openDist(0,0.5) dir=against hold 240m all | 126.7 | 6.1 | 28.5 | 48.0 | 5.3 / 26.3 | 62.0 / 61.9 | INSURANCE |
| HO 5m openDist(0,0.5) dir=against hold 180m all | 110.4 | 13.9 | 30.5 | 49.8 | 13.3 / 29.6 | 62.6 / 68.6 | INSURANCE |
| HO 5m openDist(0,0.5) dir=against hold 120m all | 98.2 | 4.1 | 25.1 | 48.2 | 11.9 / 24.9 | 58.9 / 58.6 | INSURANCE |
| HO 15m openDist(0,0.5) dir=against hold 240m all | 82.5 | 12.1 | 28.1 | 44.5 | 11.4 / 25.1 | 60.0 / 60.9 | INSURANCE |
| HO 15m openDist(0,0.5) dir=against hold 180m all | 80.4 | 17.2 | 29.0 | 38.5 | 16.5 / 30.2 | 62.6 / 68.1 | INSURANCE |
| HO 15m openDist(0,0.5) dir=against hold 120m all | 70.7 | 2.1 | 21.4 | 39.9 | 1.4 / 21.3 | 62.6 / 65.8 | INSURANCE |
| HO 5m openDist(0,0.75) dir=against hold 240m all | 60.8 | 10.9 | 26.7 | 41.5 | 10.1 / 23.9 | 36.3 / 42.2 | INSURANCE |
| HO 15m openDist(0,0.75) dir=against hold 240m all | 48.4 | 2.6 | 24.5 | 38.2 | 1.8 / 21.1 | 34.9 / 42.9 | INSURANCE |

INSURANCE count: 58.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1691 | 221.7 | 192.3 | 206.5 | 29.4 | 2.43 / 2.14 / 2.29 | 406.2 / 376.8 |
| ES 2 5m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 2220 | 179.0 | 149.6 | 163.8 | 29.4 | 2.33 / 1.98 / 2.16 | 353.3 / 324.0 |
| ES 3 15m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 1906 | 161.8 | 132.5 | 146.6 | 29.4 | 2.30 / 1.92 / 2.11 | 279.0 / 249.7 |
| ES 4 5m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1941 | 224.5 | 195.2 | 209.4 | 29.4 | 2.45 / 2.16 / 2.30 | 295.6 / 266.3 |
| ES 5 5m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 712 | 312.9 | 283.5 | 297.7 | 29.4 | 1.66 / 1.53 / 1.59 | 468.7 / 439.3 |
| ES 6 15m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 603 | 299.9 | 270.6 | 284.8 | 29.4 | 1.37 / 1.25 / 1.31 | 410.1 / 380.7 |
| ES 7 5m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2776 | 99.0 | 69.7 | 83.9 | 29.4 | 2.04 / 1.47 / 1.75 | 126.7 / 97.4 |
| ES 8 15m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2280 | 94.2 | 64.9 | 79.1 | 29.4 | 1.85 / 1.30 / 1.57 | 112.3 / 83.0 |
| ES 9 5m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 839 | 207.3 | 178.0 | 192.1 | 29.4 | 1.44 / 1.26 / 1.35 | 194.4 / 165.0 |
| ES 10 15m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 711 | 199.2 | 169.9 | 184.1 | 29.4 | 1.31 / 1.14 / 1.22 | 176.6 / 147.2 |
| NQ 1 5m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 2192 | 173.5 | 159.1 | 167.6 | 14.4 | 1.53 / 1.41 / 1.48 | 446.0 / 431.7 |
| NQ 2 15m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1697 | 239.3 | 224.9 | 233.4 | 14.4 | 1.80 / 1.70 / 1.76 | 590.4 / 576.0 |
| NQ 3 5m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1914 | 252.7 | 238.3 | 246.7 | 14.4 | 1.99 / 1.89 / 1.95 | 522.6 / 508.2 |
| NQ 4 15m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 1880 | 176.6 | 162.3 | 170.7 | 14.4 | 1.69 / 1.56 / 1.64 | 386.4 / 372.0 |
| NQ 5 15m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2285 | 94.3 | 79.9 | 88.4 | 14.4 | 1.16 / 0.99 / 1.09 | 216.3 / 201.9 |
| NQ 6 5m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2709 | 93.1 | 78.7 | 87.2 | 14.4 | 1.36 / 1.16 / 1.28 | 215.9 / 201.5 |
| NQ 7 5m openDist(0,0.5) dir=against hold 60m all | positive pre-2023 | 3381 | 56.3 | 42.0 | 50.4 | 14.4 | 1.16 / 0.87 / 1.04 | 122.9 / 108.6 |
| NQ 8 5m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 720 | 321.5 | 307.1 | 315.8 | 14.4 | 1.31 / 1.26 / 1.29 | 771.8 / 757.4 |
| NQ 9 5m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 856 | 209.2 | 194.8 | 203.5 | 14.4 | 1.13 / 1.06 / 1.10 | 351.5 / 337.1 |
| NQ 10 15m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 621 | 309.8 | 295.5 | 304.2 | 14.4 | 1.20 / 1.15 / 1.18 | 487.2 / 472.8 |
| RTY 1 5m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1128 | 169.3 | 154.9 | 157.2 | 14.4 | 2.65 / 2.46 / 2.49 | 231.1 / 216.8 |
| RTY 2 15m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1002 | 183.9 | 169.6 | 171.8 | 14.4 | 2.86 / 2.67 / 2.70 | 247.1 / 232.7 |
| RTY 3 15m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 1109 | 140.6 | 126.2 | 128.5 | 14.4 | 2.80 / 2.55 / 2.59 | 193.2 / 178.9 |
| RTY 4 5m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 1291 | 135.4 | 121.1 | 123.4 | 14.4 | 2.77 / 2.51 / 2.56 | 166.1 / 151.7 |
| RTY 5 15m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 340 | 276.1 | 261.7 | 263.9 | 14.4 | 1.85 / 1.77 / 1.78 | 265.3 / 250.9 |
| RTY 6 15m openDist(0,0.75) dir=against hold 60m all | positive pre-2023 | 645 | 51.4 | 37.1 | 39.3 | 14.4 | 1.09 / 0.79 / 0.84 | 112.7 / 98.3 |
| RTY 7 5m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 401 | 254.1 | 239.8 | 242.0 | 14.4 | 1.83 / 1.75 / 1.76 | 306.5 / 292.2 |
| RTY 8 5m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 469 | 166.9 | 152.5 | 154.8 | 14.4 | 1.67 / 1.55 / 1.57 | 168.3 / 154.0 |
| RTY 9 15m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 413 | 154.9 | 140.5 | 142.8 | 14.4 | 1.50 / 1.37 / 1.39 | 164.5 / 150.1 |
| RTY 10 5m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 1581 | 76.0 | 61.6 | 63.9 | 14.4 | 2.24 / 1.84 / 1.91 | 91.1 / 76.7 |
| GC 1 5m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 2119 | 253.3 | 229.0 | 238.7 | 24.4 | 4.28 / 3.92 / 4.07 | 562.9 / 538.5 |
| GC 2 15m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1865 | 244.9 | 220.5 | 230.2 | 24.4 | 3.79 / 3.46 / 3.59 | 605.2 / 580.8 |
| GC 3 5m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 2375 | 173.7 | 149.3 | 159.0 | 24.4 | 3.64 / 3.18 / 3.37 | 408.5 / 384.1 |
| GC 4 15m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 2057 | 177.0 | 152.6 | 162.3 | 24.4 | 3.28 / 2.87 / 3.04 | 458.7 / 434.4 |
| GC 5 5m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2820 | 108.5 | 84.1 | 93.9 | 24.4 | 3.02 / 2.39 / 2.65 | 266.8 / 242.4 |
| GC 6 15m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2370 | 100.3 | 76.0 | 85.7 | 24.4 | 2.44 / 1.88 / 2.11 | 258.0 / 233.6 |
| GC 7 5m openDist(0,0.5) dir=against hold 60m all | positive pre-2023 | 3456 | 54.8 | 30.4 | 40.2 | 24.4 | 2.23 / 1.26 / 1.65 | 127.3 / 102.9 |
| GC 8 5m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 786 | 262.8 | 238.5 | 248.0 | 24.4 | 2.38 / 2.19 / 2.26 | 692.7 / 668.4 |
| GC 9 15m openDist(0,0.5) dir=against hold 60m all | positive pre-2023 | 2769 | 47.5 | 23.1 | 32.9 | 24.4 | 1.71 / 0.85 / 1.20 | 137.1 / 112.7 |
| GC 10 15m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 693 | 269.1 | 244.7 | 254.2 | 24.4 | 2.44 / 2.25 / 2.32 | 707.6 / 683.2 |
| CL 1 5m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 2231 | 220.3 | 196.0 | 198.3 | 24.4 | 3.67 / 3.32 / 3.36 | 208.6 / 184.2 |
| CL 2 5m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 2512 | 150.4 | 126.0 | 128.4 | 24.4 | 3.27 / 2.79 / 2.85 | 163.7 / 139.4 |
| CL 3 15m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 2155 | 138.2 | 113.9 | 116.2 | 24.4 | 2.89 / 2.42 / 2.48 | 157.1 / 132.8 |
| CL 4 15m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1944 | 215.0 | 190.6 | 193.0 | 24.4 | 3.42 / 3.07 / 3.12 | 195.5 / 171.1 |
| CL 5 5m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 3050 | 89.2 | 64.9 | 67.2 | 24.4 | 2.79 / 2.07 / 2.15 | 100.0 / 75.7 |
| CL 6 5m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 733 | 281.9 | 257.6 | 260.5 | 24.4 | 2.01 / 1.86 / 1.88 | 365.9 / 341.5 |
| CL 7 15m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2554 | 82.9 | 58.6 | 61.0 | 24.4 | 2.30 / 1.65 / 1.72 | 98.8 / 74.4 |
| CL 8 5m openDist(0,0.75) dir=against hold 120m all | positive pre-2023 | 1094 | 121.1 | 96.8 | 99.6 | 24.4 | 1.78 / 1.46 / 1.50 | 175.4 / 151.0 |
| CL 9 15m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 631 | 264.4 | 240.0 | 243.0 | 24.4 | 1.96 / 1.80 / 1.82 | 352.1 / 327.8 |
| CL 10 5m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 857 | 207.1 | 182.8 | 185.7 | 24.4 | 1.88 / 1.69 / 1.71 | 237.0 / 212.7 |
| BTC 1 5m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 222 | 1291.4 | 1237.1 | 1268.3 | 54.4 | 3.62 / 3.51 / 3.58 | 2035.8 / 1981.4 |
| BTC 2 5m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 248 | 839.2 | 784.9 | 816.3 | 54.4 | 3.30 / 3.14 / 3.24 | 1642.5 / 1588.2 |
| BTC 3 15m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 173 | 1349.4 | 1295.1 | 1326.6 | 54.4 | 3.45 / 3.34 / 3.40 | 1939.8 / 1885.5 |
| BTC 4 15m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 199 | 730.2 | 675.8 | 707.3 | 54.4 | 2.80 / 2.64 / 2.74 | 1455.1 / 1400.7 |
| BTC 5 5m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 101 | 2140.6 | 2086.2 | 2118.8 | 54.4 | 3.26 / 3.22 / 3.24 | 2948.2 / 2893.9 |
| BTC 6 5m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 117 | 1213.7 | 1159.3 | 1191.8 | 54.4 | 2.98 / 2.89 / 2.95 | 1960.1 / 1905.8 |
| BTC 7 15m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 80 | 2089.1 | 2034.7 | 2067.5 | 54.4 | 3.03 / 2.99 / 3.01 | 2992.6 / 2938.2 |
| BTC 8 5m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 302 | 425.9 | 371.6 | 402.9 | 54.4 | 2.50 / 2.23 / 2.39 | 918.9 / 864.6 |
| BTC 9 5m openDist(0,0.75) dir=against hold 120m all | positive pre-2023 | 142 | 782.9 | 728.6 | 760.6 | 54.4 | 2.45 / 2.33 / 2.40 | 1319.4 / 1265.1 |
| BTC 10 15m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 88 | 1344.9 | 1290.5 | 1323.3 | 54.4 | 2.74 / 2.66 / 2.71 | 2179.3 / 2124.9 |
| HO 1 5m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 2176 | 294.6 | 281.8 | 283.3 | 12.8 | 3.21 / 3.08 / 3.10 | 301.8 / 289.1 |
| HO 2 5m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 2423 | 232.6 | 219.9 | 221.3 | 12.8 | 3.09 / 2.94 / 2.96 | 233.6 / 220.8 |
| HO 3 5m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2960 | 149.0 | 136.3 | 137.7 | 12.8 | 3.10 / 2.85 / 2.89 | 158.3 / 145.5 |
| HO 4 15m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 1767 | 256.2 | 243.5 | 245.0 | 12.8 | 2.89 / 2.76 / 2.78 | 314.4 / 301.6 |
| HO 5 15m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 1932 | 180.3 | 167.5 | 169.0 | 12.8 | 2.42 / 2.26 / 2.28 | 241.0 / 228.3 |
| HO 6 15m openDist(0,0.5) dir=against hold 120m all | positive pre-2023 | 2338 | 116.8 | 104.0 | 105.5 | 12.8 | 2.12 / 1.89 / 1.92 | 156.4 / 143.6 |
| HO 7 5m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 702 | 358.6 | 345.9 | 347.3 | 12.8 | 1.55 / 1.50 / 1.51 | 505.6 / 492.8 |
| HO 8 15m openDist(0,0.75) dir=against hold 240m all | positive pre-2023 | 573 | 338.4 | 325.6 | 327.1 | 12.8 | 1.29 / 1.25 / 1.26 | 518.4 / 505.7 |
| HO 9 5m openDist(0,0.75) dir=against hold 180m all | positive pre-2023 | 830 | 261.2 | 248.5 | 249.9 | 12.8 | 1.44 / 1.37 / 1.38 | 321.2 / 308.4 |
| HO 10 5m openDist(0,0.75) dir=against hold 120m all | positive pre-2023 | 1061 | 154.0 | 141.2 | 142.6 | 12.8 | 1.25 / 1.15 / 1.16 | 202.4 / 189.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 22 cells pass the clean rule against a replicate mean of 15.2 (p(count) = 0.04, p(top) = 0.00); CL: 18 cells pass the clean rule against a replicate mean of 6.2 (p(count) = 0.00, p(top) = 0.00); ES: 16 cells pass the clean rule against a replicate mean of 10.0 (p(count) = 0.04, p(top) = 0.00); GC: 17 cells pass the clean rule against a replicate mean of 10.8 (p(count) = 0.01, p(top) = 0.00); HO: 17 cells pass the clean rule against a replicate mean of 13.7 (p(count) = 0.21, p(top) = 0.00); NQ: 24 cells pass the clean rule against a replicate mean of 19.1 (p(count) = 0.14, p(top) = 0.00); RTY: 20 cells pass the clean rule against a replicate mean of 11.8 (p(count) = 0.03, p(top) = 0.00); ZN: 3 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 0.00, p(top) = 0.01).
- Of 70 selected cells, 58 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +1.48 (GC 5m openDist(0,0.5) dir=against hold 240m all); bootstrap lower bound > 0 for 70 cells; plateau >= 0.75 for 66; 2x-slippage all-in uplift >= +0.10 for 70; gate_add PASS at some share: 210 (cell-share pairs).
- Gate-3 cell ES 15m openDist(0,0.5) dir=against hold 240m all: uplift +0.62/+0.58/+0.80, boot lo +0.46, plateau 0.75, 2x-slip +0.62, wd corr -0.46, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 5m openDist(0,0.5) dir=against hold 180m all: uplift +0.58/+0.30/+0.80, boot lo +0.43, plateau 1.00, 2x-slip +0.54, wd corr -0.50, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 15m openDist(0,0.5) dir=against hold 180m all: uplift +0.65/+0.45/+0.82, boot lo +0.46, plateau 0.75, 2x-slip +0.61, wd corr -0.37, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 5m openDist(0,0.5) dir=against hold 240m all: uplift +0.50/+0.63/+1.07, boot lo +0.45, plateau 1.00, 2x-slip +0.61, wd corr -0.55, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 5m openDist(0,0.75) dir=against hold 240m all: uplift +0.35/+0.39/+0.64, boot lo +0.24, plateau 1.00, 2x-slip +0.39, wd corr -0.56, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 15m openDist(0,0.75) dir=against hold 240m all: uplift +0.32/+0.36/+0.61, boot lo +0.20, plateau 1.00, 2x-slip +0.37, wd corr -0.55, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 5m openDist(0,0.5) dir=against hold 120m all: uplift +0.31/+0.20/+0.68, boot lo +0.22, plateau 1.00, 2x-slip +0.32, wd corr -0.53, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 5m openDist(0,0.75) dir=against hold 180m all: uplift +0.21/+0.70/+0.45, boot lo +0.14, plateau 1.00, 2x-slip +0.29, wd corr -0.27, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 15m openDist(0,0.75) dir=against hold 180m all: uplift +0.21/+0.62/+0.71, boot lo +0.17, plateau 1.00, 2x-slip +0.34, wd corr -0.44, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ 5m openDist(0,0.5) dir=against hold 180m all: uplift +0.63/+0.52/+1.16, boot lo +0.51, plateau 0.50, 2x-slip +0.73, wd corr -0.54, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ 15m openDist(0,0.5) dir=against hold 240m all: uplift +0.58/+0.60/+1.26, boot lo +0.51, plateau 0.75, 2x-slip +0.74, wd corr -0.46, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ 5m openDist(0,0.5) dir=against hold 240m all: uplift +0.57/+0.59/+1.31, boot lo +0.53, plateau 1.00, 2x-slip +0.74, wd corr -0.49, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ 15m openDist(0,0.5) dir=against hold 180m all: uplift +0.52/+0.56/+0.87, boot lo +0.38, plateau 0.75, 2x-slip +0.61, wd corr -0.50, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ 5m openDist(0,0.5) dir=against hold 120m all: uplift +0.39/+0.16/+0.51, boot lo +0.21, plateau 1.00, 2x-slip +0.39, wd corr -0.38, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ 5m openDist(0,0.75) dir=against hold 240m all: uplift +0.22/+0.37/+0.64, boot lo +0.19, plateau 1.00, 2x-slip +0.32, wd corr -0.22, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ 5m openDist(0,0.75) dir=against hold 180m all: uplift +0.25/+0.57/+0.97, boot lo +0.24, plateau 0.75, 2x-slip +0.45, wd corr -0.04, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ 15m openDist(0,0.75) dir=against hold 240m all: uplift +0.20/+0.34/+0.61, boot lo +0.13, plateau 1.00, 2x-slip +0.30, wd corr -0.23, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell RTY 15m openDist(0,0.5) dir=against hold 240m all: uplift +0.72/+0.26/+1.23, boot lo +0.56, plateau 0.75, 2x-slip +0.74, wd corr -0.47, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 5m openDist(0,0.5) dir=against hold 240m all: uplift +0.89/+2.42/+2.47, boot lo +1.18, plateau 0.75, 2x-slip +1.46, wd corr +0.28, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 15m openDist(0,0.5) dir=against hold 240m all: uplift +0.81/+2.37/+1.98, boot lo +1.03, plateau 0.75, 2x-slip +1.29, wd corr +0.23, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 5m openDist(0,0.5) dir=against hold 180m all: uplift +0.73/+2.65/+2.30, boot lo +1.05, plateau 0.75, 2x-slip +1.31, wd corr -0.31, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 15m openDist(0,0.5) dir=against hold 180m all: uplift +0.69/+2.14/+1.75, boot lo +0.87, plateau 1.00, 2x-slip +1.11, wd corr -0.34, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 5m openDist(0,0.5) dir=against hold 120m all: uplift +0.65/+2.32/+2.18, boot lo +0.98, plateau 1.00, 2x-slip +1.22, wd corr -0.39, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 15m openDist(0,0.5) dir=against hold 120m all: uplift +0.51/+2.17/+1.70, boot lo +0.74, plateau 0.75, 2x-slip +0.99, wd corr -0.47, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 5m openDist(0,0.5) dir=against hold 60m all: uplift +0.53/+2.61/+1.84, boot lo +0.83, plateau 0.75, 2x-slip +1.06, wd corr -0.35, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 5m openDist(0,0.75) dir=against hold 240m all: uplift +0.43/+1.49/+1.25, boot lo +0.56, plateau 1.00, 2x-slip +0.81, wd corr +0.28, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 15m openDist(0,0.5) dir=against hold 60m all: uplift +0.43/+0.95/+1.50, boot lo +0.49, plateau 0.75, 2x-slip +0.71, wd corr -0.25, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 15m openDist(0,0.75) dir=against hold 240m all: uplift +0.37/+1.95/+0.94, boot lo +0.48, plateau 1.00, 2x-slip +0.73, wd corr +0.27, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 5m openDist(0,0.5) dir=against hold 240m all: uplift +0.73/+0.94/+2.40, boot lo +0.87, plateau 1.00, 2x-slip +1.06, wd corr -0.24, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 5m openDist(0,0.5) dir=against hold 180m all: uplift +0.70/+1.20/+2.50, boot lo +0.90, plateau 1.00, 2x-slip +1.08, wd corr -0.23, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 15m openDist(0,0.5) dir=against hold 180m all: uplift +0.59/+0.96/+2.11, boot lo +0.73, plateau 1.00, 2x-slip +0.91, wd corr -0.30, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 15m openDist(0,0.5) dir=against hold 240m all: uplift +0.58/+0.89/+2.22, boot lo +0.74, plateau 1.00, 2x-slip +0.93, wd corr -0.29, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 5m openDist(0,0.5) dir=against hold 120m all: uplift +0.51/+0.96/+2.38, boot lo +0.70, plateau 1.00, 2x-slip +0.88, wd corr -0.20, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 5m openDist(0,0.75) dir=against hold 240m all: uplift +0.51/+0.67/+1.37, boot lo +0.52, plateau 0.75, 2x-slip +0.73, wd corr -0.41, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 15m openDist(0,0.5) dir=against hold 120m all: uplift +0.47/+0.98/+1.97, boot lo +0.61, plateau 1.00, 2x-slip +0.77, wd corr -0.31, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 5m openDist(0,0.75) dir=against hold 120m all: uplift +0.45/+0.55/+1.54, boot lo +0.47, plateau 0.75, 2x-slip +0.68, wd corr -0.35, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 15m openDist(0,0.75) dir=against hold 240m all: uplift +0.45/+0.79/+1.46, boot lo +0.50, plateau 0.50, 2x-slip +0.71, wd corr -0.43, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL 5m openDist(0,0.75) dir=against hold 180m all: uplift +0.39/+0.54/+1.27, boot lo +0.40, plateau 0.75, 2x-slip +0.59, wd corr -0.40, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 5m openDist(0,0.5) dir=against hold 240m all: uplift +0.84/+1.84/+0.97, boot lo +0.79, plateau 1.00, 2x-slip +0.94, wd corr -0.14, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 5m openDist(0,0.5) dir=against hold 180m all: uplift +0.88/+1.64/+0.92, boot lo +0.78, plateau 1.00, 2x-slip +0.94, wd corr -0.38, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 15m openDist(0,0.5) dir=against hold 240m all: uplift +0.73/+1.55/+0.93, boot lo +0.68, plateau 1.00, 2x-slip +0.84, wd corr -0.23, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 15m openDist(0,0.5) dir=against hold 180m all: uplift +0.65/+1.13/+0.90, boot lo +0.57, plateau 1.00, 2x-slip +0.72, wd corr -0.36, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 5m openDist(0,0.75) dir=against hold 240m all: uplift +0.68/+0.97/+0.53, boot lo +0.50, plateau 1.00, 2x-slip +0.67, wd corr +0.06, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 5m openDist(0,0.75) dir=against hold 180m all: uplift +0.66/+1.01/+0.64, boot lo +0.51, plateau 0.75, 2x-slip +0.68, wd corr +0.11, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 15m openDist(0,0.75) dir=against hold 240m all: uplift +0.60/+1.05/+0.50, boot lo +0.44, plateau 0.75, 2x-slip +0.61, wd corr -0.37, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 5m openDist(0,0.5) dir=against hold 120m all: uplift +0.52/+1.17/+0.83, boot lo +0.50, plateau 1.00, 2x-slip +0.63, wd corr -0.29, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 5m openDist(0,0.75) dir=against hold 120m all: uplift +0.56/+1.11/+0.60, boot lo +0.44, plateau 0.50, 2x-slip +0.61, wd corr +0.46, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 15m openDist(0,0.75) dir=against hold 180m all: uplift +0.57/+0.85/+0.49, boot lo +0.41, plateau 0.75, 2x-slip +0.57, wd corr -0.11, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 5m openDist(0,0.5) dir=against hold 240m all: uplift +0.83/+1.80/+3.06, boot lo +1.15, plateau 0.75, 2x-slip +1.46, wd corr -0.30, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 5m openDist(0,0.5) dir=against hold 180m all: uplift +0.80/+1.56/+2.63, boot lo +1.02, plateau 0.75, 2x-slip +1.31, wd corr -0.30, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 5m openDist(0,0.5) dir=against hold 120m all: uplift +0.70/+1.26/+2.54, boot lo +0.89, plateau 0.75, 2x-slip +1.19, wd corr -0.29, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 15m openDist(0,0.5) dir=against hold 240m all: uplift +0.70/+1.40/+2.20, boot lo +0.88, plateau 1.00, 2x-slip +1.14, wd corr -0.23, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 15m openDist(0,0.5) dir=against hold 180m all: uplift +0.67/+1.48/+1.92, boot lo +0.77, plateau 1.00, 2x-slip +1.06, wd corr -0.23, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 15m openDist(0,0.5) dir=against hold 120m all: uplift +0.59/+1.17/+2.00, boot lo +0.69, plateau 0.75, 2x-slip +0.98, wd corr -0.24, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 5m openDist(0,0.75) dir=against hold 240m all: uplift +0.57/+0.57/+1.83, boot lo +0.62, plateau 0.75, 2x-slip +0.88, wd corr -0.22, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 15m openDist(0,0.75) dir=against hold 240m all: uplift +0.53/+0.27/+1.76, boot lo +0.51, plateau 0.75, 2x-slip +0.79, wd corr -0.26, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 5m openDist(0,0.75) dir=against hold 180m all: uplift +0.41/+0.49/+1.63, boot lo +0.45, plateau 0.75, 2x-slip +0.72, wd corr -0.23, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell HO 5m openDist(0,0.75) dir=against hold 120m all: uplift +0.41/+0.66/+1.95, boot lo +0.54, plateau 0.75, 2x-slip +0.82, wd corr -0.21, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 70}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q18.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q18/ (`Q18_CO_all_selected_scored.csv`).

DONE Q18
