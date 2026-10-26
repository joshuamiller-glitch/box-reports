# REPORT SW6 - relative-volume spike bar continuation/reversal (D02 H1-H3, D01)

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 0.** 29 selected cells (+18 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.35; best pair-window standalone Sharpe +1.72.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: tf bar volume / median of the same clock slot over the prior 20 label days >= k (2/3/4) and body fraction >= bf (0/0.6): enter with or against the bar direction, exact hold 15/30/60/120 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 96 cells per instrument = 2 bar sizes x 3 k x 2 bf x 2 directions x 4 holds.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |         3 |               0.787 |                2 |          3 |            3 |
| CL    |      96 |         96 |         0 |               0.056 |                1 |          0 |            3 |
| ES    |      96 |         96 |         2 |               0.812 |                2 |          2 |            3 |
| GC    |      96 |         96 |         3 |               1.305 |                2 |          3 |            3 |
| NQ    |      96 |         96 |        11 |               0.79  |                2 |         10 |            0 |
| RTY   |      96 |         96 |         1 |               0.366 |                2 |          1 |            3 |
| YM    |      96 |         96 |        13 |               1.394 |                2 |         10 |            0 |
| ZN    |      96 |         96 |         0 |              -2.588 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    2 |             0.53 |               3 |       0.12 |                       0.616 |            0.516 |           0.957 |     0.16 |       0.761 |                1.139 |
| NQ    |     100 |                   11 |             6.5  |              12 |       0.06 |                       0.496 |            0.696 |           0.922 |     0.88 |       0.787 |                1.904 |
| RTY   |     100 |                    1 |             0.71 |               3 |       0.52 |                       0.366 |            0.589 |           1.088 |     0.39 |       0.366 |                1.256 |
| YM    |     100 |                   13 |             1.01 |               5 |       0    |                       0.935 |            0.633 |           1.228 |     0.09 |       1.394 |                1.652 |
| GC    |     100 |                    3 |             0.62 |               3 |       0.01 |                       0.953 |            0.55  |           1.06  |     0.07 |       1.305 |                1.158 |
| CL    |     100 |                    0 |             0.18 |               1 |       1    |                     nan     |            0.53  |           1.151 |   nan    |     nan     |                1.151 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                    3 |             2.13 |               8 |       0.33 |                       0.491 |            0.581 |           1.144 |     0.57 |       0.787 |                1.535 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 5m relvol>=4.0 body>=0.6 dir=with hold=120m | 615 | 2 | 0.76 | -1.38 | 0.45 | -0.15 / 0.83 | 0.06 / -0.07 / -0.02 | -0.07 | -0.53 | 0.99 | -0.15 | 0.33 | 983 | NO |
| ES 2 | 5m relvol>=3.0 body>=0.6 dir=with hold=120m | 1102 | 2 | 0.47 | -1.98 | 0.20 | -0.19 / 0.22 | 0.01 / -0.06 / 0.01 | -0.13 | -0.46 | 1.00 | -0.20 | 0.00 | 1739 | NO |
| ES 3 (diag) | 15m relvol>=4.0 body>=0.6 dir=with hold=60m | 225 | 1 | 0.81 | -1.29 | 0.46 | -0.01 / 1.13 | 0.06 / -0.04 / -0.07 | -0.05 | 0.55 | 1.00 | -0.16 | 0.17 | 367 | diag |
| ES 4 (diag) | 15m relvol>=3.0 body>=0.6 dir=with hold=60m | 486 | 1 | 0.54 | -2.03 | -0.29 | -1.27 / 0.31 | 0.07 / 0.15 / -0.71 | -0.22 | 0.28 | 0.95 | -0.32 | 0.00 | 782 | diag |
| ES 5 (diag) | 15m relvol>=3.0 body>=0.6 dir=with hold=120m | 428 | 1 | 0.44 | -1.45 | -0.26 | -1.63 / 0.61 | 0.05 / -0.14 / -0.44 | -0.17 | 0.01 | 0.80 | -0.28 | 0.00 | 677 | diag |
| NQ 1 | 5m relvol>=3.0 body>=0.0 dir=with hold=120m | 1454 | 2 | 0.79 | -0.78 | 0.26 | -0.20 / 1.03 | 0.07 / -0.26 / 0.09 | -0.02 | -0.27 | 0.88 | -0.23 | 0.50 | 2321 | NO |
| NQ 2 | 5m relvol>=4.0 body>=0.0 dir=with hold=120m | 771 | 2 | 0.78 | -0.79 | 0.26 | -0.21 / 1.23 | 0.03 / -0.25 / -0.19 | -0.09 | 0.43 | 0.87 | -0.29 | 0.00 | 1253 | NO |
| NQ 3 | 15m relvol>=2.0 body>=0.0 dir=with hold=30m | 2226 | 2 | 0.67 | -1.17 | 0.44 | 0.24 / 0.65 | 0.11 / -0.29 / 0.16 | -0.01 | 0.01 | 1.00 | -0.13 | 0.25 | 3676 | NO |
| NQ 4 | 15m relvol>=4.0 body>=0.6 dir=with hold=60m | 163 | 2 | 0.61 | -0.75 | 0.21 | -0.26 / 1.60 | 0.08 / 0.07 / -0.06 | 0.03 | -0.24 | 0.74 | -0.14 | 0.33 | 273 | NO |
| NQ 5 | 15m relvol>=3.0 body>=0.0 dir=with hold=60m | 613 | 2 | 0.55 | -1.27 | 0.42 | 0.23 / 1.20 | 0.06 / -0.12 / 0.02 | 0.00 | -0.17 | 0.94 | -0.16 | 0.50 | 1032 | NO |
| NQ 6 | 15m relvol>=2.0 body>=0.6 dir=with hold=30m | 1238 | 2 | 0.45 | -0.83 | 0.05 | -0.41 / 1.26 | 0.06 / -0.31 / 0.11 | -0.05 | 0.09 | 0.83 | -0.19 | 0.50 | 2028 | NO |
| NQ 7 | 15m relvol>=2.0 body>=0.0 dir=with hold=120m | 1384 | 2 | 0.45 | -1.20 | 0.22 | -0.09 / 0.96 | 0.02 / 0.19 / -0.05 | -0.02 | -0.53 | 0.81 | -0.19 | 0.25 | 2252 | NO |
| NQ 8 | 5m relvol>=2.0 body>=0.6 dir=with hold=120m | 2123 | 2 | 0.26 | -0.81 | 0.24 | 0.25 / 1.19 | -0.02 / 0.21 / -0.04 | -0.04 | 0.03 | 0.90 | -0.18 | 0.00 | 3429 | NO |
| NQ 9 | 5m relvol>=3.0 body>=0.6 dir=with hold=60m | 1234 | 2 | 0.26 | -1.08 | 0.54 | 0.89 / 1.14 | -0.01 / -0.10 / 0.38 | 0.01 | 0.08 | 0.96 | -0.17 | 0.50 | 1991 | NO |
| NQ 10 | 5m relvol>=3.0 body>=0.6 dir=with hold=30m | 1462 | 2 | 0.14 | -1.63 | 0.44 | 0.77 / 0.99 | 0.04 / 0.26 / 0.04 | 0.02 | 0.11 | 0.99 | -0.12 | 0.33 | 2346 | NO |
| RTY 1 | 15m relvol>=2.0 body>=0.0 dir=with hold=120m | 1869 | 2 | 0.37 | -1.84 | 0.01 | -0.93 / 0.12 | 0.04 / -0.20 / -0.22 | -0.13 | -0.49 | 0.98 | -0.18 | 0.00 | 3051 | NO |
| RTY 2 (diag) | 15m relvol>=4.0 body>=0.6 dir=against hold=60m | 393 | 1 | 0.36 | -0.89 | 0.07 | -0.57 / 0.42 | 0.02 / -0.26 / -0.02 | -0.07 | 0.02 | 0.92 | -0.16 | 0.00 | 618 | diag |
| RTY 3 (diag) | 15m relvol>=3.0 body>=0.0 dir=with hold=60m | 1228 | 1 | 0.05 | -2.07 | 0.57 | 1.40 / 0.30 | -0.02 / -0.18 / 0.43 | -0.06 | 0.22 | 1.00 | -0.11 | 0.25 | 2020 | diag |
| RTY 4 (diag) | 15m relvol>=4.0 body>=0.6 dir=against hold=120m | 343 | 1 | 0.05 | -0.07 | 0.02 | -0.05 / 1.29 | -0.01 / -0.11 / -0.01 | -0.05 | 0.49 | 0.86 | -0.17 | 0.00 | 540 | diag |
| YM 1 | 15m relvol>=3.0 body>=0.6 dir=with hold=60m | 509 | 2 | 1.39 | -1.18 | 0.92 | 0.40 / 0.45 | 0.20 / 0.16 / 0.15 | 0.10 | -0.44 | 1.00 | -0.01 | 0.17 | 875 | LEAD |
| YM 2 | 15m relvol>=4.0 body>=0.6 dir=with hold=120m | 241 | 2 | 1.31 | -0.68 | 1.06 | 0.68 / 0.83 | 0.15 / 0.09 / 0.25 | 0.12 | -0.68 | 1.00 | -0.02 | 0.33 | 410 | NO |
| YM 3 | 15m relvol>=4.0 body>=0.0 dir=with hold=120m | 410 | 2 | 1.17 | -0.39 | 0.92 | 0.47 / 0.88 | 0.13 / 0.01 / 0.13 | 0.07 | -0.31 | 1.00 | -0.04 | 0.50 | 726 | NO |
| YM 4 | 15m relvol>=4.0 body>=0.6 dir=with hold=30m | 296 | 2 | 1.12 | -1.05 | 0.24 | -1.09 / 0.37 | 0.15 / -0.44 / -0.07 | -0.05 | -0.11 | 0.95 | -0.15 | 0.00 | 508 | NO |
| YM 5 | 15m relvol>=4.0 body>=0.6 dir=with hold=60m | 267 | 2 | 1.03 | -0.72 | 0.76 | 0.26 / 0.90 | 0.11 / -0.05 / 0.19 | 0.06 | -0.34 | 1.00 | -0.03 | 0.33 | 458 | NO |
| YM 6 | 15m relvol>=3.0 body>=0.0 dir=with hold=120m | 735 | 2 | 0.82 | -1.06 | 1.72 | 2.96 / 0.66 | 0.09 / 0.06 / 1.10 | 0.23 | -0.45 | 1.00 | 0.09 | 0.50 | 1279 | NO |
| YM 7 | 15m relvol>=3.0 body>=0.0 dir=with hold=60m | 912 | 2 | 0.69 | -1.37 | 1.21 | 1.82 / 0.14 | 0.07 / 0.13 / 0.63 | 0.10 | 0.03 | 1.00 | 0.00 | 0.25 | 1588 | NO |
| YM 8 | 15m relvol>=4.0 body>=0.0 dir=with hold=60m | 479 | 2 | 0.66 | -0.70 | 0.31 | -0.24 / 0.62 | 0.05 / -0.15 / -0.07 | -0.07 | 0.05 | 0.97 | -0.20 | 0.00 | 856 | NO |
| YM 9 | 15m relvol>=3.0 body>=0.6 dir=with hold=30m | 572 | 2 | 0.58 | -1.10 | 0.01 | -0.58 / 0.55 | 0.06 / -0.18 / -0.10 | -0.15 | -0.12 | 0.98 | -0.23 | 0.00 | 992 | NO |
| YM 10 | 15m relvol>=4.0 body>=0.6 dir=with hold=15m | 323 | 2 | 0.58 | -1.50 | -0.65 | -2.04 / 0.60 | 0.04 / -0.75 / -0.68 | -0.35 | 0.46 | 0.86 | -0.45 | 0.00 | 542 | NO |
| GC 1 | 15m relvol>=4.0 body>=0.6 dir=against hold=120m | 296 | 2 | 1.30 | -0.48 | 1.63 | 2.09 / 1.32 | 0.16 / 1.88 / 0.25 | 0.32 | 0.04 | 1.00 | 0.14 | 0.33 | 462 | LEAD |
| GC 2 | 15m relvol>=3.0 body>=0.6 dir=against hold=120m | 589 | 2 | 0.91 | -0.82 | 1.05 | 1.24 / 1.05 | 0.14 / -0.19 / 0.86 | 0.19 | -0.40 | 0.99 | -0.02 | 0.33 | 914 | NO |
| GC 3 | 5m relvol>=4.0 body>=0.6 dir=against hold=120m | 972 | 2 | 0.64 | -1.23 | 0.54 | 0.53 / 0.99 | 0.13 / 0.33 / -0.07 | 0.05 | -0.09 | 0.96 | -0.18 | 0.17 | 1495 | NO |
| GC 4 (diag) | 15m relvol>=4.0 body>=0.0 dir=against hold=120m | 514 | 1 | 0.49 | -1.17 | -0.45 | -1.17 / 0.92 | 0.03 / -0.80 / -0.64 | -0.28 | 0.17 | 0.40 | -0.55 | 0.00 | 773 | diag |
| GC 5 (diag) | 15m relvol>=2.0 body>=0.6 dir=against hold=120m | 1232 | 1 | 0.34 | -1.30 | 0.02 | -0.17 / 1.02 | 0.05 / -0.06 / -0.42 | -0.15 | -0.42 | 0.81 | -0.39 | 0.00 | 1943 | diag |
| GC 6 (diag) | 5m relvol>=3.0 body>=0.6 dir=against hold=120m | 1562 | 1 | 0.26 | -1.35 | -0.17 | -0.55 / 1.08 | 0.08 / -0.64 / -0.12 | -0.18 | -0.12 | 0.72 | -0.34 | 0.00 | 2427 | diag |
| CL 1 (diag) | 15m relvol>=4.0 body>=0.0 dir=with hold=15m | 639 | 1 | 0.06 | -2.91 | -0.99 | -1.83 / -0.08 | -0.02 / -0.89 / -1.12 | -0.71 | -0.09 | 0.97 | -0.76 | 0.00 | 1334 | diag |
| CL 2 (diag) | 15m relvol>=4.0 body>=0.6 dir=with hold=30m | 312 | 1 | 0.05 | -1.28 | 0.12 | 0.18 / 0.68 | 0.03 / -0.33 / 0.22 | -0.11 | -0.36 | 0.99 | -0.26 | 0.17 | 635 | diag |
| CL 3 (diag) | 15m relvol>=3.0 body>=0.6 dir=with hold=120m | 461 | 1 | -0.16 | -0.75 | -0.55 | -0.99 / 0.84 | -0.07 / -0.44 / -0.24 | -0.29 | -0.26 | 0.67 | -0.39 | 0.00 | 872 | diag |
| ZN 1 (diag) | 15m relvol>=4.0 body>=0.6 dir=against hold=120m | 331 | 0 | -2.59 | -3.24 | -3.23 | -4.36 / -3.97 | -0.54 / -0.96 / -0.70 | -1.06 | 0.67 | 1.00 | -0.85 | 0.00 | 554 | diag |
| ZN 2 (diag) | 15m relvol>=4.0 body>=0.6 dir=with hold=120m | 331 | 0 | -3.00 | -3.03 | -3.09 | -3.41 / -3.71 | -0.60 / -0.46 / -0.55 | -0.94 | -0.33 | 1.00 | -0.74 | 0.00 | 554 | diag |
| ZN 3 (diag) | 15m relvol>=4.0 body>=0.0 dir=against hold=120m | 518 | 0 | -3.40 | -3.98 | -4.42 | -6.50 / -6.28 | -0.68 / -1.35 / -1.03 | -1.36 | 0.60 | 1.00 | -1.06 | 0.00 | 889 | diag |
| BTC 1 | 15m relvol>=2.0 body>=0.0 dir=with hold=120m | 2545 | 2 | 0.79 | -1.10 | -0.35 | -1.95 / 0.95 | 0.13 / -0.64 / -0.47 | -0.23 | -0.07 | 0.73 | -0.31 | 0.00 | 3989 | NO |
| BTC 2 | 15m relvol>=4.0 body>=0.6 dir=with hold=120m | 730 | 2 | 0.50 | 0.09 | 0.19 | -0.43 / 1.18 | 0.07 / 0.30 / -0.22 | -0.04 | 0.14 | 0.89 | -0.17 | 0.50 | 1138 | NO |
| BTC 3 | 15m relvol>=4.0 body>=0.6 dir=with hold=30m | 977 | 2 | 0.19 | 1.37 | 0.12 | 0.01 / 0.31 | 0.02 / 0.37 / -0.12 | -0.10 | -0.20 | 0.95 | -0.19 | 0.33 | 1481 | NO |
| BTC 4 (diag) | 15m relvol>=3.0 body>=0.6 dir=against hold=60m | 1376 | 1 | 0.64 | -1.74 | 0.25 | -0.38 / 0.53 | 0.09 / -0.42 / 0.02 | -0.10 | -0.02 | 0.93 | -0.18 | 0.00 | 2126 | diag |
| BTC 5 (diag) | 5m relvol>=2.0 body>=0.0 dir=against hold=120m | 3879 | 1 | 0.33 | -1.36 | -0.34 | -1.70 / 0.44 | 0.10 / -0.48 / -0.17 | -0.18 | -0.11 | 0.83 | -0.25 | 0.00 | 6094 | diag |
| BTC 6 (diag) | 15m relvol>=4.0 body>=0.0 dir=with hold=30m | 1766 | 1 | 0.33 | 0.26 | -0.04 | -0.88 / 0.21 | -0.01 / -0.23 / -0.04 | -0.16 | 0.51 | 0.98 | -0.26 | 0.00 | 2695 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 29 |
| diagnostic cells read | 18 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 2 / 2 / 1 |
| all-in uplift @20% > 0 (all scored) | 25 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 3 |
| standalone pair-window Sharpe above own random-entry null p95 | 28 |
| worst-decile corr <= +0.30 | 40 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m relvol>=4.0 body>=0.6 dir=with hold=120m | clean | 0.49 | 0.69 | -143510 | -113426 | 585817 | -297961 | 0.77 | 40.0 | 1.53 | -91188 | 389837 | -106530 |
| BTC 15m relvol>=4.0 body>=0.6 dir=with hold=120m | H1 | 0.21 | 0.31 | -109378 | -98016 | 418899 | -115240 | 0.11 | 57.1 | 3.12 | -60444 | 175645 | -61710 |
| BTC 15m relvol>=4.0 body>=0.6 dir=with hold=120m | H2 | -1.04 | -1.31 | -97174 | -86206 | 379841 | -103123 | -0.64 | 52.8 | 2.07 | -89400 | 212155 | -90608 |
| BTC 15m relvol>=4.0 body>=0.6 dir=with hold=120m | all | 0.19 | 0.26 | -131819 | -106871 | 623676 | -297961 | 0.41 | 45.2 | 1.87 | -89269 | 389837 | -106530 |
| CL 15m relvol>=4.0 body>=0.6 dir=with hold=30m (diag) | clean | 0.07 | 0.15 | -90561 | -76184 | 509309 | -125787 | 0.12 | 43.8 | 1.49 | -80169 | 301030 | -85353 |
| CL 15m relvol>=4.0 body>=0.6 dir=with hold=30m (diag) | H1 | -1.73 | -2.13 | -100761 | -89699 | 304722 | -114562 | -1.00 | 64.3 | 2.50 | -68029 | 169792 | -76982 |
| CL 15m relvol>=4.0 body>=0.6 dir=with hold=30m (diag) | H2 | 0.53 | 1.27 | -283623 | -222994 | 864708 | -287763 | 0.66 | 63.9 | 2.52 | -95133 | 218440 | -100959 |
| CL 15m relvol>=4.0 body>=0.6 dir=with hold=30m (diag) | all | 0.12 | 0.28 | -166180 | -126697 | 864708 | -287763 | 0.38 | 51.8 | 1.88 | -83853 | 301030 | -100959 |
| ES 5m relvol>=4.0 body>=0.6 dir=with hold=120m | clean | 0.79 | 1.85 | -79361 | -66786 | 355421 | -108410 | 2.01 | 52.4 | 1.52 | -84352 | 272567 | -93922 |
| ES 5m relvol>=4.0 body>=0.6 dir=with hold=120m | H1 | -0.60 | -0.89 | -91201 | -80446 | 289882 | -97547 | -0.39 | 64.3 | 2.76 | -69322 | 163070 | -84805 |
| ES 5m relvol>=4.0 body>=0.6 dir=with hold=120m | H2 | 0.12 | 0.18 | -128898 | -115754 | 360910 | -133086 | 0.11 | 55.6 | 2.28 | -78082 | 207293 | -81298 |
| ES 5m relvol>=4.0 body>=0.6 dir=with hold=120m | all | 0.45 | 0.85 | -103500 | -84255 | 483974 | -133086 | 1.32 | 55.4 | 1.86 | -83507 | 272567 | -93922 |
| GC 15m relvol>=4.0 body>=0.6 dir=against hold=120m | clean | 1.30 | 2.81 | -89759 | -74252 | 191627 | -176817 | 6.14 | 33.3 | 1.62 | -89376 | 280937 | -112622 |
| GC 15m relvol>=4.0 body>=0.6 dir=against hold=120m | H1 | 3.88 | 21.93 | -45786 | -43301 | 173262 | -50118 | 7.79 | 25.0 | 4.71 | -46963 | 123561 | -49699 |
| GC 15m relvol>=4.0 body>=0.6 dir=against hold=120m | H2 | 1.37 | 3.63 | -201854 | -153210 | 527475 | -261263 | 1.99 | 33.3 | 2.55 | -86707 | 212959 | -87161 |
| GC 15m relvol>=4.0 body>=0.6 dir=against hold=120m | all | 1.63 | 4.29 | -121069 | -89988 | 527475 | -261263 | 6.78 | 32.1 | 2.20 | -88274 | 280937 | -112622 |
| NQ 5m relvol>=3.0 body>=0.6 dir=with hold=30m | clean | 0.19 | 0.23 | -158861 | -111655 | 489498 | -460789 | 0.36 | 43.8 | 1.50 | -80672 | 280247 | -84918 |
| NQ 5m relvol>=3.0 body>=0.6 dir=with hold=30m | H1 | 1.54 | 3.53 | -94702 | -79674 | 203832 | -103668 | 2.05 | 50.0 | 3.09 | -74114 | 120307 | -88211 |
| NQ 5m relvol>=3.0 body>=0.6 dir=with hold=30m | H2 | 0.27 | 0.43 | -154850 | -132156 | 559571 | -170678 | 0.20 | 47.2 | 2.33 | -91515 | 204614 | -94340 |
| NQ 5m relvol>=3.0 body>=0.6 dir=with hold=30m | all | 0.44 | 0.60 | -160589 | -120082 | 559571 | -460789 | 1.26 | 45.2 | 1.93 | -84012 | 280247 | -94340 |
| RTY 15m relvol>=2.0 body>=0.0 dir=with hold=120m | clean | 0.41 | 0.93 | -85529 | -65996 | 499357 | -151890 | 0.74 | 51.4 | 1.50 | -79386 | 280505 | -83917 |
| RTY 15m relvol>=2.0 body>=0.0 dir=with hold=120m | H1 | -0.43 | -0.60 | -78019 | -69768 | 194389 | -88192 | -0.33 | 60.7 | 2.63 | -84296 | 162425 | -88940 |
| RTY 15m relvol>=2.0 body>=0.0 dir=with hold=120m | H2 | -1.25 | -1.45 | -124492 | -93136 | 388666 | -177561 | -0.76 | 50.0 | 2.07 | -84045 | 231711 | -91245 |
| RTY 15m relvol>=2.0 body>=0.0 dir=with hold=120m | all | 0.01 | 0.01 | -97129 | -75829 | 499762 | -177561 | 0.02 | 52.4 | 1.81 | -81854 | 280505 | -91245 |
| YM 15m relvol>=3.0 body>=0.0 dir=with hold=120m | clean | 0.86 | 1.62 | -101842 | -88120 | 347608 | -124956 | 2.26 | 50.5 | 1.55 | -87036 | 325958 | -92024 |
| YM 15m relvol>=3.0 body>=0.0 dir=with hold=120m | H1 | 0.62 | 0.87 | -107490 | -89526 | 198525 | -130260 | 0.56 | 42.9 | 2.89 | -69802 | 177909 | -74945 |
| YM 15m relvol>=3.0 body>=0.0 dir=with hold=120m | H2 | 4.32 | 9.07 | -152743 | -109222 | 205987 | -156144 | 8.80 | 22.2 | 3.39 | -65782 | 202206 | -66926 |
| YM 15m relvol>=3.0 body>=0.0 dir=with hold=120m | all | 1.72 | 3.34 | -116324 | -95372 | 347608 | -156144 | 7.79 | 43.5 | 2.14 | -84406 | 325958 | -92024 |
| ZN 15m relvol>=4.0 body>=0.6 dir=with hold=120m (diag) | clean | -2.99 | -3.01 | -184344 | -151645 | 2748474 | -322451 | -0.99 | 61.0 | 0.86 | -90894 | 368760 | -102442 |
| ZN 15m relvol>=4.0 body>=0.6 dir=with hold=120m (diag) | H1 | -2.01 | -2.30 | -108339 | -96506 | 493399 | -127908 | -0.74 | 60.7 | 2.36 | -90056 | 161486 | -90695 |
| ZN 15m relvol>=4.0 body>=0.6 dir=with hold=120m (diag) | H2 | -4.80 | -4.18 | -120862 | -95204 | 950649 | -156631 | -0.96 | 75.0 | 1.75 | -83140 | 232361 | -85580 |
| ZN 15m relvol>=4.0 body>=0.6 dir=with hold=120m (diag) | all | -3.09 | -3.08 | -168927 | -136144 | 4048604 | -322451 | -0.99 | 63.7 | 1.29 | -90118 | 368760 | -102442 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 5m relvol>=4.0 body>=0.6 dir=with hold=120m | -22.9 | 4.2 | 20.7 | 34.0 | 3.4 / 18.0 | 17.5 / 34.4 | NO |
| NQ 5m relvol>=3.0 body>=0.6 dir=with hold=30m | -22.1 | -13.1 | 13.8 | 16.8 | 1.1 / 18.7 | 11.0 / 19.2 | NO |
| RTY 15m relvol>=2.0 body>=0.0 dir=with hold=120m | -29.9 | 9.2 | 22.6 | 29.6 | 21.6 / 26.2 | 9.6 / 17.1 | NO |
| YM 15m relvol>=3.0 body>=0.0 dir=with hold=120m | 0.3 | 7.7 | 18.0 | 5.4 | 7.0 / 12.7 | 27.0 / 27.9 | NO |
| GC 15m relvol>=4.0 body>=0.6 dir=against hold=120m | 10.0 | -29.8 | 8.7 | 29.6 | -30.8 / 7.6 | 59.1 / 71.7 | NO |
| CL 15m relvol>=4.0 body>=0.6 dir=with hold=30m (diag) | -26.4 | -8.7 | 16.4 | 5.7 | 19.0 / 23.5 | 31.1 / 36.7 | NO |
| ZN 15m relvol>=4.0 body>=0.6 dir=with hold=120m (diag) | -74.6 | -11.3 | 7.9 | -32.4 | -12.2 / 5.9 | 6.2 / 5.9 | NO |
| BTC 15m relvol>=4.0 body>=0.6 dir=with hold=120m | -27.2 | -18.3 | 4.4 | -28.8 | -19.2 / -2.0 | 61.8 / 63.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 5m relvol>=4.0 body>=0.6 dir=with hold=120m | negative pre-2023 | 4831 | -2.6 | -31.9 | -16.7 | 29.4 | -0.11 / -1.38 / -0.72 | 76.5 / 47.2 |
| ES 2 5m relvol>=3.0 body>=0.6 dir=with hold=120m | negative pre-2023 | 7742 | -9.6 | -39.0 | -24.0 | 29.4 | -0.49 / -1.98 / -1.22 | 47.7 / 18.3 |
| ES 3 (diag) 15m relvol>=4.0 body>=0.6 dir=with hold=60m | negative pre-2023 | 1829 | -11.9 | -41.3 | -26.0 | 29.4 | -0.38 / -1.29 / -0.82 | 100.0 / 70.6 |
| ES 4 (diag) 15m relvol>=3.0 body>=0.6 dir=with hold=60m | negative pre-2023 | 3453 | -13.0 | -42.3 | -27.3 | 29.4 | -0.64 / -2.03 / -1.33 | 48.1 / 18.8 |
| ES 5 (diag) 15m relvol>=3.0 body>=0.6 dir=with hold=120m | negative pre-2023 | 2959 | -19.8 | -49.1 | -34.1 | 29.4 | -0.58 / -1.45 / -1.01 | 59.9 / 30.6 |
| NQ 1 5m relvol>=3.0 body>=0.0 dir=with hold=120m | negative pre-2023 | 10536 | -0.7 | -15.0 | -5.9 | 14.4 | -0.04 / -0.78 / -0.31 | 53.3 / 39.0 |
| NQ 2 5m relvol>=4.0 body>=0.0 dir=with hold=120m | negative pre-2023 | 6881 | -5.1 | -19.5 | -10.1 | 14.4 | -0.21 / -0.79 / -0.41 | 67.5 / 53.1 |
| NQ 3 15m relvol>=2.0 body>=0.0 dir=with hold=30m | gross-positive, cost-negative pre-2023 | 16255 | 1.6 | -12.7 | -3.7 | 14.4 | 0.15 / -1.17 / -0.35 | 29.7 / 15.3 |
| NQ 4 15m relvol>=4.0 body>=0.6 dir=with hold=60m | negative pre-2023 | 1868 | -13.9 | -28.3 | -18.7 | 14.4 | -0.37 / -0.75 / -0.50 | 115.9 / 101.5 |
| NQ 5 15m relvol>=3.0 body>=0.0 dir=with hold=60m | negative pre-2023 | 5620 | -14.1 | -28.5 | -19.2 | 14.4 | -0.64 / -1.27 / -0.86 | 57.4 / 43.1 |
| NQ 6 15m relvol>=2.0 body>=0.6 dir=with hold=30m | gross-positive, cost-negative pre-2023 | 9467 | 3.3 | -11.0 | -2.0 | 14.4 | 0.25 / -0.83 / -0.15 | 27.8 / 13.5 |
| NQ 7 15m relvol>=2.0 body>=0.0 dir=with hold=120m | negative pre-2023 | 9212 | -16.4 | -30.8 | -21.8 | 14.4 | -0.64 / -1.20 / -0.85 | 46.1 / 31.8 |
| NQ 8 5m relvol>=2.0 body>=0.6 dir=with hold=120m | negative pre-2023 | 13466 | -1.6 | -16.0 | -7.1 | 14.4 | -0.09 / -0.81 / -0.36 | 25.4 / 11.1 |
| NQ 9 5m relvol>=3.0 body>=0.6 dir=with hold=60m | negative pre-2023 | 10633 | -3.4 | -17.7 | -8.4 | 14.4 | -0.21 / -1.08 / -0.51 | 23.3 / 8.9 |
| NQ 10 5m relvol>=3.0 body>=0.6 dir=with hold=30m | negative pre-2023 | 13183 | -2.4 | -16.7 | -7.4 | 14.4 | -0.24 / -1.63 / -0.73 | 20.8 / 6.4 |
| RTY 1 15m relvol>=2.0 body>=0.0 dir=with hold=120m | negative pre-2023 | 6079 | -9.7 | -24.0 | -21.7 | 14.4 | -0.74 / -1.84 / -1.66 | 24.2 / 9.9 |
| RTY 2 (diag) 15m relvol>=4.0 body>=0.6 dir=against hold=60m | negative pre-2023 | 1491 | -0.0 | -14.4 | -11.8 | 14.4 | -0.01 / -0.89 / -0.73 | 29.5 / 15.1 |
| RTY 3 (diag) 15m relvol>=3.0 body>=0.0 dir=with hold=60m | negative pre-2023 | 4216 | -9.4 | -23.8 | -21.3 | 14.4 | -0.84 / -2.07 / -1.85 | 16.2 / 1.9 |
| RTY 4 (diag) 15m relvol>=4.0 body>=0.6 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 1306 | 12.7 | -1.7 | 0.9 | 14.4 | 0.49 / -0.07 / 0.03 | 17.2 / 2.8 |
| YM 1 15m relvol>=3.0 body>=0.6 dir=with hold=60m | negative pre-2023 | 3833 | -4.1 | -18.5 | -12.2 | 14.4 | -0.26 / -1.18 / -0.78 | 56.0 / 41.6 |
| YM 2 15m relvol>=4.0 body>=0.6 dir=with hold=120m | negative pre-2023 | 1839 | -7.8 | -22.1 | -15.8 | 14.4 | -0.24 / -0.68 / -0.49 | 127.1 / 112.7 |
| YM 3 15m relvol>=4.0 body>=0.0 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 2787 | 3.2 | -11.2 | -4.9 | 14.4 | 0.11 / -0.39 / -0.17 | 92.2 / 77.8 |
| YM 4 15m relvol>=4.0 body>=0.6 dir=with hold=30m | negative pre-2023 | 2352 | -2.3 | -16.6 | -10.2 | 14.4 | -0.14 / -1.05 / -0.64 | 55.9 / 41.6 |
| YM 5 15m relvol>=4.0 body>=0.6 dir=with hold=60m | negative pre-2023 | 2111 | -2.0 | -16.4 | -10.0 | 14.4 | -0.09 / -0.72 / -0.44 | 93.6 / 79.3 |
| YM 6 15m relvol>=3.0 body>=0.0 dir=with hold=120m | negative pre-2023 | 4831 | -7.2 | -21.5 | -15.4 | 14.4 | -0.35 / -1.06 / -0.76 | 43.1 / 28.7 |
| YM 7 15m relvol>=3.0 body>=0.0 dir=with hold=60m | negative pre-2023 | 6079 | -2.5 | -16.9 | -10.7 | 14.4 | -0.21 / -1.37 / -0.88 | 30.4 / 16.0 |
| YM 8 15m relvol>=4.0 body>=0.0 dir=with hold=60m | gross-positive, cost-negative pre-2023 | 3347 | 0.9 | -13.5 | -7.1 | 14.4 | 0.05 / -0.70 / -0.38 | 42.1 / 27.7 |
| YM 9 15m relvol>=3.0 body>=0.6 dir=with hold=30m | gross-positive, cost-negative pre-2023 | 4350 | 2.2 | -12.1 | -5.9 | 14.4 | 0.20 / -1.10 / -0.54 | 23.7 / 9.3 |
| YM 10 15m relvol>=4.0 body>=0.6 dir=with hold=15m | negative pre-2023 | 2579 | -2.2 | -16.6 | -10.1 | 14.4 | -0.21 / -1.50 / -0.95 | 24.3 / 10.0 |
| GC 1 15m relvol>=4.0 body>=0.6 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 1877 | 1.5 | -22.8 | -12.5 | 24.4 | 0.03 / -0.48 / -0.27 | 170.1 / 145.7 |
| GC 2 15m relvol>=3.0 body>=0.6 dir=against hold=120m | negative pre-2023 | 3340 | -3.2 | -27.6 | -17.5 | 24.4 | -0.10 / -0.82 / -0.52 | 80.4 / 56.1 |
| GC 3 5m relvol>=4.0 body>=0.6 dir=against hold=120m | negative pre-2023 | 6035 | -3.1 | -27.4 | -17.3 | 24.4 | -0.14 / -1.23 / -0.78 | 55.0 / 30.7 |
| GC 4 (diag) 15m relvol>=4.0 body>=0.0 dir=against hold=120m | negative pre-2023 | 3305 | -13.3 | -37.6 | -27.3 | 24.4 | -0.42 / -1.17 / -0.86 | 54.7 / 30.3 |
| GC 5 (diag) 15m relvol>=2.0 body>=0.6 dir=against hold=120m | negative pre-2023 | 6818 | -1.0 | -25.4 | -15.4 | 24.4 | -0.05 / -1.30 / -0.79 | 37.1 / 12.7 |
| GC 6 (diag) 5m relvol>=3.0 body>=0.6 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 9051 | 3.0 | -21.4 | -11.4 | 24.4 | 0.19 / -1.35 / -0.72 | 33.9 / 9.5 |
| CL 1 (diag) 15m relvol>=4.0 body>=0.0 dir=with hold=15m | gross-positive, cost-negative pre-2023 | 3701 | 0.6 | -23.8 | -21.5 | 24.4 | 0.07 / -2.91 / -2.66 | 24.8 / 0.4 |
| CL 2 (diag) 15m relvol>=4.0 body>=0.6 dir=with hold=30m | negative pre-2023 | 1879 | -0.8 | -25.1 | -22.6 | 24.4 | -0.04 / -1.28 / -1.15 | 26.9 / 2.5 |
| CL 3 (diag) 15m relvol>=3.0 body>=0.6 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 3024 | 5.3 | -19.1 | -16.7 | 24.4 | 0.21 / -0.75 / -0.66 | 18.5 / -5.9 |
| ZN 1 (diag) 15m relvol>=4.0 body>=0.6 dir=against hold=120m | negative pre-2023 | 2162 | -1.6 | -37.2 | -42.3 | 35.6 | -0.15 / -3.24 / -3.62 | 3.3 / -32.3 |
| ZN 2 (diag) 15m relvol>=4.0 body>=0.6 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 2162 | 1.6 | -34.0 | -39.1 | 35.6 | 0.15 / -3.03 / -3.42 | -3.3 / -38.9 |
| ZN 3 (diag) 15m relvol>=4.0 body>=0.0 dir=against hold=120m | negative pre-2023 | 3328 | -0.1 | -35.7 | -40.8 | 35.6 | -0.01 / -3.98 / -4.43 | 3.3 / -32.3 |
| BTC 1 15m relvol>=2.0 body>=0.0 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 1951 | 1.0 | -53.3 | -20.9 | 54.4 | 0.02 / -1.10 / -0.42 | 113.5 / 59.2 |
| BTC 2 15m relvol>=4.0 body>=0.6 dir=with hold=120m | positive pre-2023 | 603 | 65.1 | 10.7 | 43.1 | 54.4 | 0.56 / 0.09 / 0.37 | 142.4 / 88.0 |
| BTC 3 15m relvol>=4.0 body>=0.6 dir=with hold=30m | positive pre-2023 | 821 | 112.7 | 58.3 | 90.7 | 54.4 | 2.54 / 1.37 / 2.08 | 71.0 / 16.7 |
| BTC 4 (diag) 15m relvol>=3.0 body>=0.6 dir=against hold=60m | negative pre-2023 | 1091 | -47.5 | -101.9 | -69.5 | 54.4 | -0.82 / -1.74 / -1.20 | 114.4 / 60.0 |
| BTC 5 (diag) 5m relvol>=2.0 body>=0.0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2902 | 7.3 | -47.0 | -14.6 | 54.4 | 0.20 / -1.36 / -0.42 | 83.1 / 28.7 |
| BTC 6 (diag) 15m relvol>=4.0 body>=0.0 dir=with hold=30m | positive pre-2023 | 1528 | 61.8 | 7.5 | 40.0 | 54.4 | 2.07 / 0.26 / 1.36 | 84.8 / 30.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 3 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.33, p(top) = 0.57); CL: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); ES: 2 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 0.12, p(top) = 0.16); GC: 3 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.01, p(top) = 0.07); NQ: 11 cells pass the clean rule against a replicate mean of 6.5 (p(count) = 0.06, p(top) = 0.88); RTY: 1 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.52, p(top) = 0.39); YM: 13 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.00, p(top) = 0.09); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 29 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.35 (GC 15m relvol>=4.0 body>=0.6 dir=against hold=120m); bootstrap lower bound > 0 for 3 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 5; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell YM 15m relvol>=3.0 body>=0.6 dir=with hold=60m: uplift +0.20/+0.16/+0.15, boot lo -0.01, plateau 0.17, 2x-slip +0.10, wd corr -0.44, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell GC 15m relvol>=4.0 body>=0.6 dir=against hold=120m: uplift +0.16/+1.88/+0.25, boot lo +0.14, plateau 0.33, 2x-slip +0.32, wd corr +0.04, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 20, 'gross-positive, cost-negative pre-2023': 7, 'positive pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_6.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw6/ (`SW6_CO_all_selected_scored.csv`).

DONE SW6
