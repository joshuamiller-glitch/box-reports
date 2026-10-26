# REPORT SW10 - signed-volume imbalance persistence proxy from 1-min bars (D01/D02 H2/H3)

**Verdict: LEAD. FOUND 0, LEAD 3, INSURANCE 0.** 41 selected cells (+15 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.27; best pair-window standalone Sharpe +1.94.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: imbalance I_W = sum(sign(close-open) x volume)/sum(volume) over W (15/30/60) minutes at 5-min bar ends; I crossing +-theta (0.15/0.25/0.35), optionally with the previous W-window imbalance of the same sign (persistence), enter with or against, exact hold 30/60/120 min. No tick data is used (bar proxy; the real signed-volume tests are NQ trade-based, D01/D02 NQ cells stay separate).
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 216 cells per instrument = 3 W x 3 theta x 2 persistence x 2 directions x 3 holds x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     216 |        214 |        31 |               2.013 |                2 |         10 |            0 |
| CL    |     216 |        216 |         2 |               0.638 |                2 |          2 |            3 |
| ES    |     216 |        216 |         7 |               1.096 |                2 |          7 |            3 |
| GC    |     216 |        216 |         0 |               0.565 |                1 |          0 |            3 |
| NQ    |     216 |        216 |        39 |               2.682 |                2 |         10 |            0 |
| RTY   |     216 |        216 |         2 |               1.141 |                2 |          2 |            3 |
| YM    |     216 |        216 |        22 |               1.647 |                2 |         10 |            0 |
| ZN    |     216 |        216 |         0 |              -1.32  |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    7 |             1.97 |               8 |       0.01 |                       0.614 |            0.599 |           1.034 |     0.34 |       0.954 |                1.269 |
| NQ    |     100 |                   39 |            20.26 |              30 |       0    |                       1.914 |            0.97  |           1.202 |     0    |       2.682 |                2.075 |
| RTY   |     100 |                    2 |             3.88 |              11 |       0.91 |                       0.545 |            0.563 |           0.853 |     0.51 |       1.034 |                1.607 |
| YM    |     100 |                   22 |             4.57 |              10 |       0    |                       1.192 |            0.591 |           1.04  |     0    |       1.647 |                1.585 |
| GC    |     100 |                    0 |             2.37 |              10 |       1    |                     nan     |            0.53  |           0.895 |   nan    |     nan     |                1.389 |
| CL    |     100 |                    2 |             0.77 |               3 |       0.19 |                       0.591 |            0.519 |           0.982 |     0.21 |       0.638 |                1.303 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                   31 |            15.79 |              26 |       0    |                       1.339 |            0.825 |           1.069 |     0.01 |       2.013 |                1.972 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | imbalance W=60m theta=0.35 persist=1 dir=with hold=30m day | 182 | 2 | 0.95 | -1.07 | 0.85 | 0.67 / 0.23 | 0.10 / -0.11 / -0.04 | 0.01 | -0.58 | 1.00 | -0.07 | 0.33 | 293 | NO |
| ES 2 | imbalance W=60m theta=0.35 persist=0 dir=with hold=60m day | 372 | 2 | 0.91 | -0.79 | 0.35 | -0.53 / 0.53 | 0.08 / -0.19 / -0.33 | -0.10 | -0.35 | 0.99 | -0.18 | 0.00 | 595 | NO |
| ES 3 | imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | 528 | 2 | 0.76 | -1.22 | 0.73 | 0.74 / 0.26 | 0.08 / 0.19 / -0.04 | -0.01 | -0.30 | 1.00 | -0.10 | 0.17 | 832 | NO |
| ES 4 | imbalance W=60m theta=0.35 persist=1 dir=with hold=60m day | 174 | 2 | 0.67 | -0.71 | 0.53 | 0.22 / 1.18 | 0.04 / -0.23 / -0.02 | -0.04 | -0.03 | 0.97 | -0.13 | 0.00 | 280 | NO |
| ES 5 | imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | 439 | 2 | 0.47 | -0.62 | 0.45 | 0.47 / 0.64 | 0.06 / -0.14 / -0.03 | -0.04 | -0.19 | 0.98 | -0.16 | 0.17 | 697 | NO |
| ES 6 | imbalance W=60m theta=0.15 persist=0 dir=with hold=120m day | 1338 | 2 | 0.28 | -1.35 | 0.21 | 0.22 / 0.52 | -0.01 / -0.11 / -0.15 | -0.16 | 0.26 | 0.95 | -0.23 | 0.00 | 2144 | NO |
| ES 7 | imbalance W=60m theta=0.25 persist=0 dir=with hold=60m day | 1115 | 2 | 0.25 | -1.34 | 0.21 | 0.06 / 0.12 | 0.00 / 0.25 / -0.26 | -0.14 | -0.22 | 1.00 | -0.18 | 0.00 | 1751 | NO |
| ES 8 (diag) | imbalance W=60m theta=0.35 persist=1 dir=with hold=30m all | 546 | 1 | 1.10 | -2.48 | 0.71 | -0.08 / 0.16 | 0.13 / -0.07 / -0.17 | -0.09 | -0.57 | 1.00 | -0.10 | 0.00 | 928 | diag |
| ES 9 (diag) | imbalance W=60m theta=0.35 persist=0 dir=with hold=30m day | 386 | 1 | 0.78 | -1.40 | 0.20 | -1.01 / -0.01 | 0.09 / -0.24 / -0.34 | -0.11 | -0.45 | 1.00 | -0.18 | 0.00 | 624 | diag |
| ES 10 (diag) | imbalance W=60m theta=0.35 persist=1 dir=with hold=60m all | 515 | 1 | 0.76 | -1.79 | 0.39 | -0.37 / 0.33 | 0.06 / -0.14 / -0.20 | -0.11 | -0.38 | 1.00 | -0.17 | 0.00 | 873 | diag |
| NQ 1 | imbalance W=60m theta=0.25 persist=1 dir=with hold=60m all | 1674 | 2 | 2.68 | -0.96 | 1.28 | -0.02 / 0.96 | 0.41 / -0.02 / -0.18 | 0.15 | -0.05 | 1.00 | -0.02 | 0.33 | 2694 | NO |
| NQ 2 | imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | 589 | 2 | 2.64 | -0.71 | 1.55 | 0.53 / 0.95 | 0.38 / 0.42 / -0.20 | 0.21 | -0.34 | 1.00 | 0.03 | 0.33 | 941 | NO |
| NQ 3 | imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | 470 | 2 | 2.39 | -0.30 | 1.65 | 0.91 / 1.31 | 0.38 / 0.37 / 0.00 | 0.26 | -0.18 | 0.99 | 0.07 | 0.33 | 765 | NO |
| NQ 4 | imbalance W=60m theta=0.25 persist=1 dir=with hold=30m day | 650 | 2 | 1.92 | -0.94 | 1.52 | 1.26 / 1.12 | 0.27 / 0.58 / 0.12 | 0.22 | 0.02 | 1.00 | 0.06 | 0.67 | 1034 | LEAD(gate3-7 fail: plateau ) |
| NQ 5 | imbalance W=60m theta=0.25 persist=1 dir=with hold=30m all | 1876 | 2 | 1.88 | -1.29 | 1.05 | 0.18 / 1.01 | 0.29 / 0.00 / 0.12 | 0.11 | 0.15 | 1.00 | -0.01 | 0.50 | 3007 | NO |
| NQ 6 | imbalance W=60m theta=0.25 persist=1 dir=with hold=120m all | 1400 | 2 | 1.60 | -0.59 | 1.12 | 0.57 / 1.24 | 0.25 / 0.08 / -0.01 | 0.11 | -0.06 | 0.99 | -0.05 | 0.33 | 2247 | NO |
| NQ 7 | imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day | 190 | 2 | 1.59 | 0.02 | 1.52 | 1.33 / 1.37 | 0.20 / -0.15 / 0.22 | 0.16 | -0.44 | 1.00 | -0.02 | 0.67 | 303 | NO |
| NQ 8 | imbalance W=60m theta=0.35 persist=1 dir=with hold=30m all | 690 | 2 | 1.54 | -0.32 | 1.36 | 1.11 / 0.95 | 0.26 / 0.14 / 0.01 | 0.15 | -0.24 | 1.00 | -0.01 | 0.33 | 1101 | NO |
| NQ 9 | imbalance W=30m theta=0.35 persist=0 dir=with hold=60m day | 1514 | 2 | 1.47 | 0.12 | 1.94 | 2.83 / 1.04 | 0.18 / 0.34 / 0.46 | 0.23 | -0.18 | 1.00 | 0.10 | 0.17 | 2351 | LEAD(gate3-7 fail: plateau ) |
| NQ 10 | imbalance W=60m theta=0.35 persist=1 dir=with hold=30m day | 223 | 2 | 1.42 | -0.24 | 1.59 | 1.76 / 1.44 | 0.23 / 0.10 / 0.26 | 0.22 | -0.18 | 1.00 | 0.03 | 0.50 | 354 | LEAD(gate3-7 fail: plateau ) |
| RTY 1 | imbalance W=30m theta=0.25 persist=1 dir=against hold=120m day | 950 | 2 | 1.03 | -0.65 | 0.25 | -0.85 / 1.00 | 0.17 / -0.90 / 0.03 | -0.09 | -0.10 | 0.94 | -0.22 | 0.00 | 1507 | NO |
| RTY 2 | imbalance W=30m theta=0.15 persist=0 dir=with hold=120m day | 1557 | 2 | 0.06 | 0.21 | -0.02 | -0.01 / 0.76 | -0.03 / -0.26 / 0.28 | -0.09 | -0.38 | 0.88 | -0.18 | 0.00 | 2493 | NO |
| RTY 3 (diag) | imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | 647 | 1 | 1.14 | 0.02 | 0.77 | 0.00 / 0.85 | 0.14 / -0.50 / 0.33 | 0.02 | 0.23 | 0.97 | -0.10 | 0.33 | 1025 | diag |
| RTY 4 (diag) | imbalance W=60m theta=0.25 persist=1 dir=against hold=120m day | 511 | 1 | 0.75 | -0.09 | 0.30 | -0.31 / 1.14 | 0.13 / -0.76 / 0.40 | 0.00 | -0.08 | 0.91 | -0.15 | 0.17 | 835 | diag |
| RTY 5 (diag) | imbalance W=60m theta=0.35 persist=0 dir=against hold=120m day | 482 | 1 | 0.68 | -0.05 | 0.33 | -0.31 / 0.62 | 0.08 / -0.31 / 0.15 | -0.02 | -0.01 | 0.90 | -0.15 | 0.17 | 762 | diag |
| YM 1 | imbalance W=30m theta=0.25 persist=0 dir=with hold=120m day | 1436 | 2 | 1.65 | -0.26 | 0.66 | -0.66 / 1.20 | 0.26 / -0.56 / -0.13 | -0.01 | 0.32 | 1.00 | -0.14 | 0.33 | 2294 | NO |
| YM 2 | imbalance W=15m theta=0.35 persist=0 dir=with hold=120m day | 1534 | 2 | 1.57 | -0.75 | 0.96 | 0.31 / 0.78 | 0.25 / -0.30 / 0.34 | 0.10 | -0.33 | 0.99 | -0.02 | 0.33 | 2442 | NO |
| YM 3 | imbalance W=60m theta=0.25 persist=0 dir=with hold=120m day | 948 | 2 | 1.52 | -0.44 | 0.75 | -0.50 / 0.71 | 0.20 / -0.34 / -0.18 | -0.01 | 0.07 | 0.99 | -0.12 | 0.17 | 1502 | NO |
| YM 4 | imbalance W=60m theta=0.15 persist=0 dir=with hold=120m day | 1376 | 2 | 1.40 | -0.60 | 0.54 | -0.59 / 0.74 | 0.21 / -0.45 / -0.18 | -0.04 | 0.06 | 0.99 | -0.16 | 0.33 | 2202 | NO |
| YM 5 | imbalance W=15m theta=0.25 persist=0 dir=with hold=120m day | 1630 | 2 | 1.32 | -0.97 | 0.89 | 0.27 / 1.44 | 0.22 / -0.33 / 0.30 | 0.07 | 0.16 | 0.98 | -0.04 | 0.33 | 2624 | NO |
| YM 6 | imbalance W=15m theta=0.15 persist=1 dir=with hold=120m day | 1326 | 2 | 1.20 | -1.17 | 0.04 | -1.48 / 0.94 | 0.18 / -0.99 / -0.13 | -0.13 | -0.35 | 0.85 | -0.26 | 0.00 | 2114 | NO |
| YM 7 | imbalance W=60m theta=0.25 persist=0 dir=with hold=120m all | 2645 | 2 | 0.96 | -1.10 | 0.27 | -0.75 / 0.36 | 0.11 / -0.23 / -0.33 | -0.16 | -0.02 | 1.00 | -0.21 | 0.00 | 4209 | NO |
| YM 8 | imbalance W=15m theta=0.25 persist=1 dir=with hold=120m day | 1252 | 2 | 0.85 | -0.76 | 0.71 | 0.40 / 1.02 | 0.12 / 0.20 / -0.15 | 0.00 | -0.30 | 0.98 | -0.11 | 0.33 | 1984 | NO |
| YM 9 | imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | 533 | 2 | 0.74 | -0.20 | 0.30 | -0.44 / 1.11 | 0.08 / -0.02 / -0.40 | -0.08 | 0.48 | 0.87 | -0.22 | 0.00 | 809 | NO |
| YM 10 | imbalance W=30m theta=0.25 persist=1 dir=with hold=60m day | 1265 | 2 | 0.72 | -0.94 | 0.35 | -0.24 / 0.87 | 0.06 / 0.09 / -0.34 | -0.12 | -0.24 | 0.98 | -0.20 | 0.00 | 1987 | NO |
| GC 1 (diag) | imbalance W=60m theta=0.35 persist=0 dir=against hold=30m day | 525 | 1 | 0.57 | -1.66 | -0.79 | -2.03 / 0.92 | 0.06 / -0.66 / -1.20 | -0.43 | 0.39 | 0.51 | -0.62 | 0.00 | 818 | diag |
| GC 2 (diag) | imbalance W=15m theta=0.35 persist=1 dir=against hold=120m day | 1088 | 1 | 0.39 | -0.87 | 0.37 | 0.44 / 1.38 | 0.09 / 1.81 / -1.18 | -0.04 | -0.06 | 0.92 | -0.26 | 0.50 | 1756 | diag |
| GC 3 (diag) | imbalance W=60m theta=0.35 persist=1 dir=with hold=120m all | 622 | 1 | 0.37 | -1.21 | 0.04 | -0.18 / 1.47 | 0.02 / -0.71 / -0.05 | -0.17 | -0.07 | 0.64 | -0.40 | 0.00 | 1000 | diag |
| CL 1 | imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | 646 | 2 | 0.64 | -0.21 | 0.70 | 0.90 / 0.99 | 0.06 / 0.05 / 0.64 | 0.04 | 0.07 | 1.00 | -0.07 | 0.17 | 1043 | NO |
| CL 2 | imbalance W=30m theta=0.25 persist=1 dir=against hold=120m day | 947 | 2 | 0.54 | -0.69 | 0.32 | 0.22 / 0.76 | 0.12 / 0.10 / -0.03 | -0.07 | 0.30 | 1.00 | -0.18 | 0.67 | 1524 | NO |
| CL 3 (diag) | imbalance W=60m theta=0.35 persist=1 dir=against hold=120m day | 200 | 1 | 0.23 | -0.29 | -0.07 | -0.29 / 1.02 | -0.02 / -0.12 / -0.01 | -0.12 | -0.19 | 0.76 | -0.29 | 0.00 | 348 | diag |
| CL 4 (diag) | imbalance W=15m theta=0.25 persist=1 dir=against hold=120m day | 1263 | 1 | 0.21 | -0.94 | -0.03 | -0.12 / 0.57 | 0.05 / 0.49 / -0.35 | -0.16 | 0.35 | 0.96 | -0.21 | 0.17 | 2022 | diag |
| CL 5 (diag) | imbalance W=30m theta=0.15 persist=1 dir=against hold=120m day | 1127 | 1 | 0.18 | -0.50 | -0.21 | -0.52 / 1.00 | 0.03 / 0.03 / -0.25 | -0.19 | 0.19 | 0.81 | -0.24 | 0.00 | 1783 | diag |
| ZN 1 (diag) | imbalance W=60m theta=0.35 persist=1 dir=against hold=120m day | 130 | 0 | -1.32 | -1.62 | -1.95 | -3.07 / -2.26 | -0.30 / -0.49 / -0.75 | -0.69 | 0.45 | 0.99 | -0.62 | 0.00 | 244 | diag |
| ZN 2 (diag) | imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day | 130 | 0 | -1.75 | -2.15 | -1.67 | -1.51 / -2.46 | -0.35 / -0.35 / -0.23 | -0.63 | -0.61 | 1.00 | -0.51 | 0.00 | 244 | diag |
| ZN 3 (diag) | imbalance W=60m theta=0.35 persist=0 dir=with hold=120m day | 273 | 0 | -2.29 | -2.45 | -2.73 | -3.29 / -4.15 | -0.48 / -0.94 / -0.42 | -1.10 | -0.58 | 1.00 | -0.74 | 0.00 | 548 | diag |
| BTC 1 | imbalance W=60m theta=0.25 persist=0 dir=against hold=60m all | 1065 | 2 | 2.01 | -1.39 | 1.44 | 0.52 / 0.53 | 0.34 / 0.14 / -0.01 | 0.16 | 0.37 | 1.00 | 0.05 | 0.17 | 1649 | NO |
| BTC 2 | imbalance W=60m theta=0.25 persist=0 dir=against hold=60m day | 901 | 2 | 1.51 | -1.19 | 0.97 | 0.11 / 1.03 | 0.24 / -0.22 / 0.08 | 0.08 | 0.38 | 0.99 | -0.04 | 0.33 | 1387 | NO |
| BTC 3 | imbalance W=60m theta=0.25 persist=0 dir=against hold=120m all | 799 | 2 | 1.48 | -1.89 | 0.77 | -0.22 / 1.18 | 0.26 / -0.20 / 0.09 | 0.10 | -0.05 | 0.96 | -0.03 | 0.33 | 1245 | NO |
| BTC 4 | imbalance W=60m theta=0.25 persist=1 dir=against hold=60m all | 268 | 2 | 1.45 | -0.83 | 0.68 | -0.72 / 1.01 | 0.27 / -0.39 / -0.13 | 0.06 | 0.27 | 0.96 | -0.09 | 0.67 | 412 | NO |
| BTC 5 | imbalance W=60m theta=0.25 persist=1 dir=against hold=60m day | 247 | 2 | 1.39 | -0.94 | 0.56 | -0.84 / 1.05 | 0.26 / -0.39 / -0.19 | 0.04 | 0.35 | 0.94 | -0.12 | 0.50 | 384 | NO |
| BTC 6 | imbalance W=60m theta=0.25 persist=0 dir=against hold=120m day | 656 | 2 | 1.38 | -1.90 | 0.68 | -0.37 / 1.01 | 0.22 / -0.31 / 0.10 | 0.07 | 0.01 | 0.95 | -0.08 | 0.33 | 1013 | NO |
| BTC 7 | imbalance W=60m theta=0.35 persist=0 dir=against hold=60m all | 482 | 2 | 1.17 | -1.40 | 0.63 | -0.19 / 1.08 | 0.21 / -0.05 / -0.02 | 0.06 | 0.05 | 0.97 | -0.08 | 0.83 | 742 | NO |
| BTC 8 | imbalance W=60m theta=0.25 persist=1 dir=against hold=30m all | 291 | 2 | 1.01 | -0.24 | 0.98 | 0.89 / 1.06 | 0.19 / 0.08 / -0.00 | 0.09 | 0.25 | 1.00 | -0.02 | 0.17 | 455 | NO |
| BTC 9 | imbalance W=60m theta=0.35 persist=1 dir=against hold=60m all | 119 | 2 | 1.01 | -1.00 | 0.42 | -1.17 / 1.30 | 0.19 / -0.20 / -0.14 | 0.04 | 0.37 | 0.86 | -0.12 | 0.50 | 181 | NO |
| BTC 10 | imbalance W=60m theta=0.35 persist=0 dir=against hold=30m all | 521 | 2 | 0.99 | -0.23 | 0.25 | -1.26 / 1.20 | 0.20 / -0.38 / -0.16 | -0.02 | 0.34 | 0.95 | -0.13 | 0.83 | 804 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 41 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 3 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 37 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 6 |
| standalone pair-window Sharpe above own random-entry null p95 | 43 |
| worst-decile corr <= +0.30 | 45 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 12 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 6 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC imbalance W=60m theta=0.25 persist=0 dir=against hold=60m all | clean | 1.96 | 3.94 | -104428 | -81486 | 225747 | -143961 | 7.88 | 43.8 | 1.80 | -85983 | 240724 | -106230 |
| BTC imbalance W=60m theta=0.25 persist=0 dir=against hold=60m all | H1 | 0.66 | 1.31 | -80899 | -74636 | 410188 | -98347 | 0.42 | 60.7 | 2.97 | -84686 | 168767 | -88758 |
| BTC imbalance W=60m theta=0.25 persist=0 dir=against hold=60m all | H2 | 0.39 | 0.57 | -123205 | -93759 | 291280 | -149477 | 0.35 | 55.6 | 2.29 | -90611 | 227373 | -92714 |
| BTC imbalance W=60m theta=0.25 persist=0 dir=against hold=60m all | all | 1.44 | 2.70 | -107925 | -85435 | 410188 | -149477 | 5.01 | 48.8 | 2.09 | -88633 | 240724 | -106230 |
| CL imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | clean | 0.53 | 0.89 | -103975 | -93863 | 370328 | -126805 | 1.32 | 55.2 | 1.52 | -87519 | 291432 | -94755 |
| CL imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | H1 | 0.47 | 0.70 | -100515 | -83835 | 238643 | -106897 | 0.39 | 46.4 | 2.88 | -68925 | 163680 | -72965 |
| CL imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | H2 | 1.13 | 1.77 | -463731 | -290922 | 1232348 | -535111 | 0.84 | 36.1 | 2.93 | -90509 | 231661 | -102624 |
| CL imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | all | 0.70 | 1.10 | -189797 | -140862 | 1232348 | -535111 | 1.31 | 50.0 | 2.03 | -87159 | 291432 | -102624 |
| ES imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | clean | 0.72 | 1.50 | -88134 | -75112 | 240636 | -130411 | 2.73 | 47.6 | 1.54 | -82025 | 281145 | -86866 |
| ES imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | H1 | 0.77 | 1.16 | -107360 | -95599 | 229083 | -121646 | 0.72 | 46.4 | 3.02 | -70195 | 136791 | -73312 |
| ES imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | H2 | 0.71 | 1.15 | -140546 | -90438 | 232333 | -185421 | 0.94 | 52.8 | 2.25 | -88348 | 220682 | -89426 |
| ES imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | all | 0.73 | 1.33 | -108536 | -86527 | 318749 | -185421 | 3.26 | 48.2 | 1.92 | -83168 | 281145 | -89426 |
| GC imbalance W=15m theta=0.35 persist=1 dir=against hold=120m day (diag) | clean | 0.37 | 0.56 | -122772 | -100162 | 712115 | -180397 | 0.48 | 52.4 | 1.55 | -83536 | 255403 | -93556 |
| GC imbalance W=15m theta=0.35 persist=1 dir=against hold=120m day (diag) | H1 | 3.06 | 15.20 | -114142 | -106278 | 313184 | -115718 | 7.95 | 35.7 | 4.64 | -59008 | 147758 | -68489 |
| GC imbalance W=15m theta=0.35 persist=1 dir=against hold=120m day (diag) | H2 | -2.24 | -2.49 | -324053 | -298484 | 1949455 | -370220 | -0.89 | 58.3 | 1.11 | -126146 | 319747 | -132993 |
| GC imbalance W=15m theta=0.35 persist=1 dir=against hold=120m day (diag) | all | 0.37 | 0.63 | -252406 | -201469 | 2242568 | -370220 | 0.49 | 50.6 | 1.92 | -97545 | 319747 | -132993 |
| NQ imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | clean | 2.42 | 5.16 | -95925 | -74910 | 268894 | -145366 | 8.15 | 41.0 | 1.84 | -82056 | 255725 | -88921 |
| NQ imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | H1 | 0.51 | 0.93 | -124651 | -115020 | 570632 | -125541 | 0.31 | 50.0 | 3.19 | -62712 | 173227 | -63716 |
| NQ imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | H2 | 1.17 | 2.14 | -167779 | -142740 | 276657 | -197243 | 2.18 | 47.2 | 2.30 | -88438 | 251822 | -89867 |
| NQ imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | all | 1.65 | 3.16 | -131266 | -106372 | 623848 | -197243 | 4.77 | 44.0 | 2.13 | -83932 | 255725 | -89867 |
| RTY imbalance W=30m theta=0.15 persist=0 dir=with hold=120m day | clean | -0.03 | -0.05 | -104163 | -88841 | 505286 | -169542 | -0.05 | 54.3 | 1.43 | -81776 | 300201 | -85826 |
| RTY imbalance W=30m theta=0.15 persist=0 dir=with hold=120m day | H1 | -2.06 | -2.42 | -99726 | -93184 | 656832 | -106228 | -0.64 | 64.3 | 2.56 | -78949 | 170681 | -82504 |
| RTY imbalance W=30m theta=0.15 persist=0 dir=with hold=120m day | H2 | 1.26 | 2.34 | -101030 | -84649 | 286767 | -105875 | 1.46 | 50.0 | 2.58 | -84754 | 224403 | -90079 |
| RTY imbalance W=30m theta=0.15 persist=0 dir=with hold=120m day | all | -0.02 | -0.03 | -104896 | -91485 | 823121 | -169542 | -0.04 | 54.8 | 1.85 | -82519 | 300201 | -90079 |
| YM imbalance W=15m theta=0.35 persist=0 dir=with hold=120m day | clean | 1.47 | 2.37 | -119518 | -99358 | 437201 | -187370 | 3.08 | 41.0 | 1.71 | -87867 | 223971 | -99890 |
| YM imbalance W=15m theta=0.35 persist=0 dir=with hold=120m day | H1 | -1.31 | -1.65 | -145503 | -126169 | 571103 | -147301 | -0.61 | 60.7 | 2.53 | -78426 | 184682 | -90603 |
| YM imbalance W=15m theta=0.35 persist=0 dir=with hold=120m day | H2 | 1.31 | 2.34 | -143272 | -114022 | 219908 | -189313 | 2.58 | 50.0 | 2.63 | -71902 | 209319 | -77681 |
| YM imbalance W=15m theta=0.35 persist=0 dir=with hold=120m day | all | 0.96 | 1.53 | -133968 | -110067 | 645635 | -189313 | 2.42 | 46.4 | 2.04 | -86097 | 223971 | -99890 |
| ZN imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day (diag) | clean | -1.74 | -2.01 | -162578 | -135648 | 1813049 | -260436 | -0.87 | 48.6 | 1.11 | -90409 | 333795 | -100504 |
| ZN imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day (diag) | H1 | -2.22 | -2.49 | -123335 | -102650 | 501995 | -161524 | -0.78 | 57.1 | 2.47 | -79308 | 155461 | -80329 |
| ZN imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day (diag) | H2 | -1.13 | -1.58 | -118561 | -107155 | 708922 | -123335 | -0.51 | 52.8 | 2.06 | -81156 | 236630 | -81767 |
| ZN imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day (diag) | all | -1.67 | -1.98 | -153062 | -127619 | 2602446 | -260436 | -0.90 | 51.2 | 1.53 | -87291 | 333795 | -100504 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | -18.4 | 17.0 | 20.0 | 29.4 | 16.3 / 22.7 | 38.1 / 42.2 | NO |
| NQ imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | 3.2 | 5.6 | 14.1 | 26.0 | 12.5 / 22.2 | 25.6 / 30.2 | NO |
| RTY imbalance W=30m theta=0.15 persist=0 dir=with hold=120m day | -30.3 | 13.5 | 21.6 | 19.2 | 18.3 / 22.0 | 20.5 / 26.3 | NO |
| YM imbalance W=15m theta=0.35 persist=0 dir=with hold=120m day | -12.5 | -6.7 | 14.0 | 40.4 | -7.5 / 9.9 | 5.0 / 19.3 | NO |
| GC imbalance W=15m theta=0.35 persist=1 dir=against hold=120m day (diag) | -17.8 | -66.7 | -14.4 | -38.7 | 4.9 / 17.9 | 32.1 / 39.9 | NO |
| CL imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | -12.0 | -9.3 | 12.1 | -12.7 | 6.4 / 12.5 | 40.2 / 40.7 | NO |
| ZN imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day (diag) | -56.1 | -29.9 | 8.4 | 1.3 | -30.9 / -0.3 | 24.7 / 26.7 | NO |
| BTC imbalance W=60m theta=0.25 persist=0 dir=against hold=60m all | -7.0 | -13.7 | 11.6 | 38.0 | -14.6 / 15.3 | 9.9 / 16.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 imbalance W=60m theta=0.35 persist=1 dir=with hold=30m day | negative pre-2023 | 1115 | -10.0 | -39.4 | -24.7 | 29.4 | -0.27 / -1.07 / -0.67 | 136.3 / 107.0 |
| ES 2 imbalance W=60m theta=0.35 persist=0 dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 2040 | 0.8 | -28.6 | -14.0 | 29.4 | 0.02 / -0.79 / -0.39 | 99.7 / 70.3 |
| ES 3 imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | negative pre-2023 | 2884 | -1.3 | -30.6 | -16.2 | 29.4 | -0.05 / -1.22 / -0.65 | 73.1 / 43.7 |
| ES 4 imbalance W=60m theta=0.35 persist=1 dir=with hold=60m day | negative pre-2023 | 1051 | -7.1 | -36.4 | -21.7 | 29.4 | -0.14 / -0.71 / -0.42 | 137.8 / 108.4 |
| ES 5 imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 2451 | 2.7 | -26.7 | -12.3 | 29.4 | 0.06 / -0.62 / -0.29 | 63.2 / 33.8 |
| ES 6 imbalance W=60m theta=0.15 persist=0 dir=with hold=120m day | negative pre-2023 | 7052 | -4.1 | -33.4 | -19.2 | 29.4 | -0.17 / -1.35 / -0.78 | 38.3 / 8.9 |
| ES 7 imbalance W=60m theta=0.25 persist=0 dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 5868 | 2.9 | -26.4 | -12.1 | 29.4 | 0.15 / -1.34 / -0.62 | 41.5 / 12.2 |
| ES 8 (diag) imbalance W=60m theta=0.35 persist=1 dir=with hold=30m all | negative pre-2023 | 3568 | -3.9 | -33.2 | -18.4 | 29.4 | -0.29 / -2.48 / -1.38 | 72.8 / 43.4 |
| ES 9 (diag) imbalance W=60m theta=0.35 persist=0 dir=with hold=30m day | negative pre-2023 | 2205 | -8.7 | -38.1 | -23.5 | 29.4 | -0.32 / -1.40 / -0.86 | 82.7 / 53.4 |
| ES 10 (diag) imbalance W=60m theta=0.35 persist=1 dir=with hold=60m all | negative pre-2023 | 3310 | -7.5 | -36.8 | -22.0 | 29.4 | -0.36 / -1.79 / -1.07 | 74.1 / 44.7 |
| NQ 1 imbalance W=60m theta=0.25 persist=1 dir=with hold=60m all | negative pre-2023 | 7464 | -5.6 | -19.9 | -11.7 | 14.4 | -0.27 / -0.96 / -0.56 | 108.9 / 94.5 |
| NQ 2 imbalance W=60m theta=0.25 persist=1 dir=with hold=60m day | negative pre-2023 | 3170 | -14.8 | -29.1 | -20.4 | 14.4 | -0.36 / -0.71 / -0.50 | 235.9 / 221.6 |
| NQ 3 imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | negative pre-2023 | 2627 | -6.5 | -20.9 | -12.2 | 14.4 | -0.10 / -0.30 / -0.18 | 317.2 / 302.8 |
| NQ 4 imbalance W=60m theta=0.25 persist=1 dir=with hold=30m day | negative pre-2023 | 3484 | -15.4 | -29.8 | -21.1 | 14.4 | -0.49 / -0.94 / -0.67 | 108.5 / 94.2 |
| NQ 5 imbalance W=60m theta=0.25 persist=1 dir=with hold=30m all | negative pre-2023 | 8303 | -6.9 | -21.3 | -13.1 | 14.4 | -0.42 / -1.29 / -0.79 | 55.2 / 40.8 |
| NQ 6 imbalance W=60m theta=0.25 persist=1 dir=with hold=120m all | negative pre-2023 | 6265 | -4.6 | -18.9 | -10.7 | 14.4 | -0.14 / -0.59 / -0.33 | 93.4 / 79.0 |
| NQ 7 imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day | positive pre-2023 | 1049 | 16.4 | 2.1 | 10.9 | 14.4 | 0.17 / 0.02 / 0.11 | 410.3 / 396.0 |
| NQ 8 imbalance W=60m theta=0.35 persist=1 dir=with hold=30m all | gross-positive, cost-negative pre-2023 | 3283 | 8.2 | -6.1 | 2.3 | 14.4 | 0.42 / -0.32 / 0.11 | 73.9 / 59.5 |
| NQ 9 imbalance W=30m theta=0.35 persist=0 dir=with hold=60m day | positive pre-2023 | 7750 | 17.3 | 3.0 | 11.6 | 14.4 | 0.68 / 0.12 / 0.46 | 102.5 / 88.1 |
| NQ 10 imbalance W=60m theta=0.35 persist=1 dir=with hold=30m day | gross-positive, cost-negative pre-2023 | 1227 | 3.5 | -10.9 | -2.0 | 14.4 | 0.08 / -0.24 / -0.05 | 157.0 / 142.6 |
| RTY 1 imbalance W=30m theta=0.25 persist=1 dir=against hold=120m day | negative pre-2023 | 2761 | -2.9 | -17.2 | -15.0 | 14.4 | -0.10 / -0.65 / -0.57 | 43.7 / 29.3 |
| RTY 2 imbalance W=30m theta=0.15 persist=0 dir=with hold=120m day | positive pre-2023 | 4676 | 19.0 | 4.6 | 6.8 | 14.4 | 0.87 / 0.21 / 0.31 | 13.6 / -0.7 |
| RTY 3 (diag) imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | positive pre-2023 | 1884 | 14.6 | 0.2 | 2.5 | 14.4 | 0.44 / 0.02 / 0.08 | 59.3 / 45.0 |
| RTY 4 (diag) imbalance W=60m theta=0.25 persist=1 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 1528 | 10.8 | -3.6 | -1.4 | 14.4 | 0.27 / -0.09 / -0.03 | 44.9 / 30.6 |
| RTY 5 (diag) imbalance W=60m theta=0.35 persist=0 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 1378 | 11.7 | -2.7 | -0.4 | 14.4 | 0.28 / -0.05 / -0.00 | 50.9 / 36.5 |
| YM 1 imbalance W=30m theta=0.25 persist=0 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 7453 | 9.3 | -5.1 | 0.7 | 14.4 | 0.47 / -0.26 / 0.03 | 57.6 / 43.3 |
| YM 2 imbalance W=15m theta=0.35 persist=0 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 8013 | 0.9 | -13.4 | -7.7 | 14.4 | 0.05 / -0.75 / -0.43 | 48.5 / 34.1 |
| YM 3 imbalance W=60m theta=0.25 persist=0 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 4665 | 3.5 | -10.8 | -5.1 | 14.4 | 0.14 / -0.44 / -0.21 | 71.9 / 57.6 |
| YM 4 imbalance W=60m theta=0.15 persist=0 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 7163 | 2.8 | -11.6 | -5.8 | 14.4 | 0.14 / -0.60 / -0.30 | 48.5 / 34.2 |
| YM 5 imbalance W=15m theta=0.25 persist=0 dir=with hold=120m day | negative pre-2023 | 8593 | -3.6 | -18.0 | -12.2 | 14.4 | -0.20 / -0.97 / -0.66 | 43.8 / 29.4 |
| YM 6 imbalance W=15m theta=0.15 persist=1 dir=with hold=120m day | negative pre-2023 | 6887 | -9.1 | -23.4 | -17.7 | 14.4 | -0.45 / -1.17 / -0.88 | 48.0 / 33.6 |
| YM 7 imbalance W=60m theta=0.25 persist=0 dir=with hold=120m all | gross-positive, cost-negative pre-2023 | 12424 | 3.4 | -10.9 | -5.4 | 14.4 | 0.34 / -1.10 / -0.55 | 28.8 / 14.5 |
| YM 8 imbalance W=15m theta=0.25 persist=1 dir=with hold=120m day | negative pre-2023 | 6461 | -2.5 | -16.9 | -11.2 | 14.4 | -0.11 / -0.76 / -0.50 | 43.1 / 28.7 |
| YM 9 imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 2515 | 7.0 | -7.4 | -1.6 | 14.4 | 0.19 / -0.20 / -0.04 | 57.3 / 42.9 |
| YM 10 imbalance W=30m theta=0.25 persist=1 dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 6394 | 0.7 | -13.7 | -8.0 | 14.4 | 0.05 / -0.94 / -0.54 | 30.3 / 15.9 |
| GC 1 (diag) imbalance W=60m theta=0.35 persist=0 dir=against hold=30m day | negative pre-2023 | 3315 | -4.2 | -28.5 | -18.4 | 24.4 | -0.24 / -1.66 / -1.06 | 46.8 / 22.4 |
| GC 2 (diag) imbalance W=15m theta=0.35 persist=1 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 5700 | 3.0 | -21.3 | -11.5 | 24.4 | 0.13 / -0.87 / -0.47 | 38.7 / 14.3 |
| GC 3 (diag) imbalance W=60m theta=0.35 persist=1 dir=with hold=120m all | negative pre-2023 | 3567 | -6.8 | -31.1 | -21.3 | 24.4 | -0.27 / -1.21 / -0.83 | 41.6 / 17.3 |
| CL 1 imbalance W=30m theta=0.35 persist=1 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 3313 | 17.9 | -6.4 | -4.0 | 24.4 | 0.58 / -0.21 / -0.13 | 40.1 / 15.7 |
| CL 2 imbalance W=30m theta=0.25 persist=1 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 4828 | 5.8 | -18.6 | -16.0 | 24.4 | 0.21 / -0.69 / -0.60 | 36.0 / 11.6 |
| CL 3 (diag) imbalance W=60m theta=0.35 persist=1 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 1122 | 8.5 | -15.9 | -13.7 | 24.4 | 0.15 / -0.29 / -0.25 | 34.5 / 10.1 |
| CL 4 (diag) imbalance W=15m theta=0.25 persist=1 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 6580 | 3.7 | -20.7 | -18.2 | 24.4 | 0.16 / -0.94 / -0.82 | 26.0 / 1.6 |
| CL 5 (diag) imbalance W=30m theta=0.15 persist=1 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 5845 | 11.5 | -12.9 | -10.3 | 24.4 | 0.43 / -0.50 / -0.40 | 26.2 / 1.8 |
| ZN 1 (diag) imbalance W=60m theta=0.35 persist=1 dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 847 | 5.1 | -30.5 | -35.7 | 35.6 | 0.28 / -1.62 / -1.88 | 4.2 / -31.4 |
| ZN 2 (diag) imbalance W=60m theta=0.35 persist=1 dir=with hold=120m day | negative pre-2023 | 847 | -5.1 | -40.7 | -45.9 | 35.6 | -0.28 / -2.15 / -2.41 | -4.2 / -39.8 |
| ZN 3 (diag) imbalance W=60m theta=0.35 persist=0 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 1644 | 1.8 | -33.8 | -39.0 | 35.6 | 0.13 / -2.45 / -2.81 | 5.6 / -30.1 |
| BTC 1 imbalance W=60m theta=0.25 persist=0 dir=against hold=60m all | negative pre-2023 | 659 | -35.7 | -90.1 | -57.4 | 54.4 | -0.54 / -1.39 / -0.88 | 325.3 / 271.0 |
| BTC 2 imbalance W=60m theta=0.25 persist=0 dir=against hold=60m day | negative pre-2023 | 582 | -31.3 | -85.7 | -53.3 | 54.4 | -0.43 / -1.19 / -0.74 | 285.3 / 231.0 |
| BTC 3 imbalance W=60m theta=0.25 persist=0 dir=against hold=120m all | negative pre-2023 | 512 | -127.7 | -182.0 | -149.3 | 54.4 | -1.32 / -1.89 / -1.55 | 321.6 / 267.2 |
| BTC 4 imbalance W=60m theta=0.25 persist=1 dir=against hold=60m all | negative pre-2023 | 150 | -67.2 | -121.5 | -89.1 | 54.4 | -0.46 / -0.83 / -0.61 | 413.3 / 359.0 |
| BTC 5 imbalance W=60m theta=0.25 persist=1 dir=against hold=60m day | negative pre-2023 | 146 | -83.6 | -137.9 | -105.6 | 54.4 | -0.57 / -0.94 / -0.72 | 404.3 / 349.9 |
| BTC 6 imbalance W=60m theta=0.25 persist=0 dir=against hold=120m day | negative pre-2023 | 443 | -149.9 | -204.2 | -171.8 | 54.4 | -1.39 / -1.90 / -1.59 | 345.0 / 290.6 |
| BTC 7 imbalance W=60m theta=0.35 persist=0 dir=against hold=60m all | negative pre-2023 | 326 | -83.5 | -137.9 | -105.7 | 54.4 | -0.86 / -1.40 / -1.08 | 272.8 / 218.4 |
| BTC 8 imbalance W=60m theta=0.25 persist=1 dir=against hold=30m all | gross-positive, cost-negative pre-2023 | 166 | 27.9 | -26.5 | 6.0 | 54.4 | 0.25 / -0.24 / 0.05 | 261.2 / 206.8 |
| BTC 9 imbalance W=60m theta=0.35 persist=1 dir=against hold=60m all | negative pre-2023 | 81 | -129.0 | -183.4 | -151.1 | 54.4 | -0.71 / -1.00 / -0.83 | 463.4 / 409.1 |
| BTC 10 imbalance W=60m theta=0.35 persist=0 dir=against hold=30m all | gross-positive, cost-negative pre-2023 | 357 | 41.9 | -12.4 | 19.9 | 54.4 | 0.77 / -0.23 / 0.37 | 216.1 / 161.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 31 cells pass the clean rule against a replicate mean of 15.8 (p(count) = 0.00, p(top) = 0.01); CL: 2 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 0.19, p(top) = 0.21); ES: 7 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.01, p(top) = 0.34); GC: 0 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 1.00); NQ: 39 cells pass the clean rule against a replicate mean of 20.3 (p(count) = 0.00, p(top) = 0.00); RTY: 2 cells pass the clean rule against a replicate mean of 3.9 (p(count) = 0.91, p(top) = 0.51); YM: 22 cells pass the clean rule against a replicate mean of 4.6 (p(count) = 0.00, p(top) = 0.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 41 selected cells, 3 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.27 (NQ imbalance W=60m theta=0.25 persist=1 dir=with hold=120m day); bootstrap lower bound > 0 for 6 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 12; gate_add PASS at some share: 6 (cell-share pairs).
- Gate-3 cell NQ imbalance W=60m theta=0.25 persist=1 dir=with hold=30m day: uplift +0.27/+0.58/+0.12, boot lo +0.06, plateau 0.67, 2x-slip +0.22, wd corr +0.02, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ imbalance W=30m theta=0.35 persist=0 dir=with hold=60m day: uplift +0.18/+0.34/+0.46, boot lo +0.10, plateau 0.17, 2x-slip +0.23, wd corr -0.18, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ imbalance W=60m theta=0.35 persist=1 dir=with hold=30m day: uplift +0.23/+0.10/+0.26, boot lo +0.03, plateau 0.50, 2x-slip +0.22, wd corr -0.18, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 22, 'gross-positive, cost-negative pre-2023': 16, 'positive pre-2023': 3}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_10.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw10/ (`SW10_CO_all_selected_scored.csv`).

DONE SW10
