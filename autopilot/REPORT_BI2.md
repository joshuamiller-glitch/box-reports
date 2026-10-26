# REPORT BI2 - overnight/RTH tug-of-war (BI batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 9 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.17; best pair-window standalone Sharpe +0.89.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BI', before the first run)
- Rule: see IDEAS_BI.md / PREREG_AUTOPILOT.md BATCH BI (frozen before the first run). overnight/RTH tug-of-war
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      12 |         12 |         2 |               1.179 |                2 |          2 |            3 |
| NQ    |      12 |         12 |         2 |               1.466 |                2 |          2 |            3 |
| RTY   |      12 |         12 |         3 |               1.193 |                2 |          3 |            3 |
| YM    |      12 |         12 |         2 |               0.763 |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    2 |            1.705 |               5 |      0.52  |                       1.175 |            0.691 |           1.25  |    0.065 |       1.179 |                1.562 |
| NQ    |     200 |                    2 |            2.41  |               6 |      0.725 |                       0.941 |            0.764 |           1.289 |    0.215 |       1.466 |                1.644 |
| RTY   |     200 |                    3 |            1.935 |               6 |      0.265 |                       0.866 |            0.728 |           1.28  |    0.27  |       1.193 |                1.591 |
| YM    |     200 |                    2 |            1.99  |               7 |      0.58  |                       0.499 |            0.754 |           1.377 |    0.695 |       0.546 |                1.732 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | RTH leg sign thr=0.0ATR dir=against hold=120m | 514 | 2 | 1.18 | -0.50 | 0.62 | -0.07 / 0.87 | 0.27 / -0.29 / 0.04 | 0.08 | -0.07 | 0.99 | -0.04 | 0.50 | 827 | NO |
| ES 2 | RTH leg sign thr=0.15ATR dir=against hold=120m | 310 | 2 | 1.17 | -0.54 | 0.52 | -0.25 / 1.42 | 0.25 / -0.41 / -0.11 | 0.03 | 0.11 | 0.90 | -0.12 | 0.75 | 510 | NO |
| ES 3 (diag) | RTH leg sign thr=0.15ATR dir=against hold=flat | 310 | 1 | 0.68 | -0.15 | 0.40 | -0.40 / 1.48 | 0.10 / -0.02 / -0.13 | 0.02 | -0.55 | 0.81 | -0.09 | 0.50 | 510 | diag |
| ES 4 (diag) | RTH leg sign thr=0.0ATR dir=against hold=flat | 514 | 1 | 0.60 | -0.18 | 0.39 | -0.17 / 1.30 | 0.10 / 0.07 / -0.02 | 0.04 | -0.76 | 0.85 | -0.07 | 0.00 | 827 | diag |
| ES 5 (diag) | ON leg sign thr=0.15ATR dir=against hold=924m | 375 | 1 | 0.17 | -0.32 | 0.02 | -0.25 / 1.34 | 0.01 / -0.74 / 0.15 | -0.11 | 0.04 | 0.60 | -0.26 | 0.00 | 598 | diag |
| NQ 1 | RTH leg sign thr=0.0ATR dir=against hold=120m | 516 | 2 | 1.47 | -0.42 | 0.59 | -0.34 / 1.26 | 0.35 / -0.63 / 0.06 | 0.14 | 0.27 | 0.91 | -0.08 | 1.00 | 829 | NO |
| NQ 2 | RTH leg sign thr=0.15ATR dir=against hold=120m | 317 | 2 | 0.42 | -0.14 | 0.44 | 0.34 / 1.66 | 0.13 / -0.25 / 0.25 | 0.11 | 0.32 | 0.81 | -0.10 | 1.00 | 524 | NO |
| NQ 3 (diag) | RTH leg sign thr=0.0ATR dir=against hold=flat | 516 | 1 | 0.77 | -0.27 | 0.18 | -0.92 / 1.60 | 0.16 / -0.15 / -0.23 | 0.03 | -0.27 | 0.64 | -0.13 | 0.00 | 829 | diag |
| NQ 4 (diag) | ON leg sign thr=0.0ATR dir=against hold=924m | 494 | 1 | 0.61 | -0.27 | 0.45 | 0.33 / 1.45 | 0.12 / -0.64 / 0.28 | 0.05 | -0.09 | 0.85 | -0.19 | 0.00 | 796 | diag |
| NQ 5 (diag) | ON leg sign thr=0.15ATR dir=against hold=924m | 378 | 1 | 0.41 | -0.33 | 0.19 | -0.00 / 1.42 | 0.06 / -0.60 / -0.00 | -0.04 | -0.01 | 0.67 | -0.29 | 0.00 | 614 | diag |
| RTY 1 | RTH leg sign thr=0.15ATR dir=against hold=120m | 332 | 2 | 1.19 | -0.46 | 0.84 | 0.38 / 1.13 | 0.15 / -0.01 / 0.01 | 0.07 | -0.36 | 0.98 | -0.10 | 0.75 | 535 | NO |
| RTY 2 | ON leg sign thr=0.0ATR dir=against hold=924m | 493 | 2 | 0.80 | -0.81 | 0.89 | 0.95 / 1.32 | 0.20 / -0.39 / 0.34 | 0.13 | 0.07 | 0.96 | -0.02 | 0.00 | 793 | NO |
| RTY 3 | RTH leg sign thr=0.0ATR dir=against hold=120m | 513 | 2 | 0.60 | -0.36 | 0.38 | 0.01 / 1.21 | 0.11 / -0.11 / -0.06 | 0.00 | -0.28 | 0.92 | -0.15 | 1.00 | 822 | NO |
| RTY 4 (diag) | RTH leg sign thr=0.15ATR dir=against hold=flat | 332 | 1 | 0.97 | -0.06 | 0.79 | 0.30 / 1.35 | 0.10 / 0.03 / 0.04 | 0.05 | -0.60 | 0.96 | -0.09 | 0.00 | 535 | diag |
| RTY 5 (diag) | RTH leg sign thr=0.0ATR dir=against hold=flat | 513 | 1 | 0.38 | -0.05 | 0.41 | 0.29 / 1.40 | 0.05 / 0.00 / 0.07 | 0.02 | -0.62 | 0.88 | -0.12 | 0.00 | 822 | diag |
| RTY 6 (diag) | ON leg sign thr=0.15ATR dir=against hold=924m | 368 | 1 | 0.32 | -0.74 | 0.46 | 0.60 / 1.46 | 0.09 / -0.30 / 0.19 | 0.04 | -0.01 | 0.83 | -0.12 | 0.50 | 591 | diag |
| YM 1 | RTH leg sign thr=0.15ATR dir=against hold=flat | 298 | 2 | 0.55 | 0.11 | 0.20 | -0.60 / 1.49 | 0.06 / -0.28 / -0.05 | -0.03 | -0.59 | 0.71 | -0.14 | 0.00 | 500 | NO |
| YM 2 | RTH leg sign thr=0.15ATR dir=against hold=120m | 298 | 2 | 0.45 | -0.29 | -0.03 | -0.63 / 1.26 | 0.06 / -0.89 / -0.01 | -0.11 | -0.17 | 0.68 | -0.29 | 0.00 | 500 | NO |
| YM 3 (diag) | RTH leg sign thr=0.0ATR dir=against hold=flat | 512 | 1 | 0.76 | 0.08 | 0.58 | 0.19 / 1.44 | 0.08 / -0.27 / 0.14 | 0.03 | -0.62 | 0.90 | -0.10 | 0.00 | 825 | diag |
| YM 4 (diag) | RTH leg sign thr=0.0ATR dir=against hold=120m | 512 | 1 | 0.47 | -0.30 | 0.31 | 0.06 / 1.13 | 0.07 / -0.57 / 0.13 | -0.04 | -0.04 | 0.92 | -0.20 | 0.50 | 825 | diag |
| YM 5 (diag) | ON leg sign thr=0.15ATR dir=against hold=924m | 364 | 1 | 0.10 | -0.62 | 0.03 | -0.16 / 1.34 | 0.01 / 0.06 / -0.20 | -0.06 | -0.09 | 0.55 | -0.23 | 0.00 | 588 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 9 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 16 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 4 |
| worst-decile corr <= +0.30 | 20 |
| plateau >= 0.75 | 5 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES RTH leg sign thr=0.0ATR dir=against hold=120m | clean | 1.26 | 1.96 | -125483 | -97042 | 479482 | -230730 | 2.39 | 42.9 | 1.73 | -85165 | 303598 | -96036 |
| ES RTH leg sign thr=0.0ATR dir=against hold=120m | H1 | -0.27 | -0.36 | -171165 | -149907 | 341268 | -174726 | -0.24 | 42.9 | 2.53 | -81413 | 174503 | -85975 |
| ES RTH leg sign thr=0.0ATR dir=against hold=120m | H2 | 0.04 | 0.07 | -185085 | -174807 | 580656 | -192531 | 0.04 | 50.0 | 2.53 | -97497 | 257922 | -107699 |
| ES RTH leg sign thr=0.0ATR dir=against hold=120m | all | 0.62 | 0.92 | -177855 | -136654 | 580656 | -230730 | 1.87 | 44.0 | 2.05 | -87995 | 303598 | -107699 |
| NQ RTH leg sign thr=0.0ATR dir=against hold=120m | clean | 1.55 | 2.58 | -119814 | -94834 | 333607 | -169723 | 4.23 | 39.0 | 1.81 | -84326 | 270518 | -93390 |
| NQ RTH leg sign thr=0.0ATR dir=against hold=120m | H1 | -1.12 | -1.34 | -190241 | -185617 | 397590 | -199469 | -1.00 | 53.6 | 2.19 | -100527 | 193089 | -114490 |
| NQ RTH leg sign thr=0.0ATR dir=against hold=120m | H2 | 0.16 | 0.25 | -205405 | -186757 | 681295 | -211857 | 0.13 | 47.2 | 2.54 | -94791 | 211989 | -98763 |
| NQ RTH leg sign thr=0.0ATR dir=against hold=120m | all | 0.59 | 0.87 | -179889 | -146965 | 761923 | -211857 | 1.45 | 42.9 | 2.05 | -91362 | 270518 | -114490 |
| RTY ON leg sign thr=0.0ATR dir=against hold=924m | clean | 0.84 | 1.24 | -140982 | -109499 | 433523 | -209548 | 1.76 | 43.8 | 1.66 | -81645 | 227913 | -89504 |
| RTY ON leg sign thr=0.0ATR dir=against hold=924m | H1 | -1.76 | -2.04 | -110251 | -98215 | 484507 | -123166 | -0.72 | 57.1 | 2.44 | -93402 | 151834 | -96400 |
| RTY ON leg sign thr=0.0ATR dir=against hold=924m | H2 | 2.60 | 5.18 | -98823 | -85143 | 300970 | -109630 | 2.95 | 27.8 | 2.83 | -96770 | 230914 | -101580 |
| RTY ON leg sign thr=0.0ATR dir=against hold=924m | all | 0.89 | 1.36 | -130669 | -105359 | 484507 | -209548 | 2.68 | 42.9 | 2.06 | -88365 | 230914 | -101580 |
| YM RTH leg sign thr=0.15ATR dir=against hold=flat | clean | 0.55 | 1.26 | -88518 | -71030 | 316833 | -152057 | 1.59 | 49.5 | 1.52 | -83423 | 246766 | -92143 |
| YM RTH leg sign thr=0.15ATR dir=against hold=flat | H1 | -0.84 | -1.11 | -111329 | -93858 | 247935 | -156385 | -0.65 | 60.7 | 2.54 | -81149 | 168732 | -81690 |
| YM RTH leg sign thr=0.15ATR dir=against hold=flat | H2 | -0.36 | -0.49 | -83006 | -75857 | 370019 | -86337 | -0.20 | 44.4 | 2.44 | -88994 | 233974 | -92287 |
| YM RTH leg sign thr=0.15ATR dir=against hold=flat | all | 0.20 | 0.38 | -95280 | -78463 | 429363 | -156385 | 0.62 | 50.6 | 1.88 | -84468 | 246766 | -92287 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES RTH leg sign thr=0.0ATR dir=against hold=120m | -18.1 | -20.7 | 10.1 | 6.0 | 4.1 / 14.1 | 15.3 / 18.4 | NO |
| NQ RTH leg sign thr=0.0ATR dir=against hold=120m | -17.9 | -32.2 | 5.3 | 26.8 | 8.9 / 18.4 | -39.4 / -14.3 | NO |
| RTY ON leg sign thr=0.0ATR dir=against hold=924m | -15.8 | -7.4 | 10.3 | 37.0 | 11.3 / 23.6 | -6.1 / -0.5 | NO |
| YM RTH leg sign thr=0.15ATR dir=against hold=flat | -27.1 | 7.2 | 16.7 | 36.8 | 6.4 / 19.7 | 16.5 / 19.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 RTH leg sign thr=0.0ATR dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2650 | 6.7 | -22.7 | -8.5 | 29.4 | 0.14 / -0.50 / -0.19 | 115.4 / 86.1 |
| ES 2 RTH leg sign thr=0.15ATR dir=against hold=120m | negative pre-2023 | 1705 | -5.7 | -35.1 | -20.9 | 29.4 | -0.09 / -0.54 / -0.32 | 136.5 / 107.1 |
| ES 3 (diag) RTH leg sign thr=0.15ATR dir=against hold=flat | gross-positive, cost-negative pre-2023 | 1705 | 12.9 | -16.4 | -2.2 | 29.4 | 0.12 / -0.15 / -0.02 | 218.2 / 188.9 |
| ES 4 (diag) RTH leg sign thr=0.0ATR dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2650 | 14.5 | -14.9 | -0.7 | 29.4 | 0.18 / -0.18 / -0.01 | 147.8 / 118.5 |
| ES 5 (diag) ON leg sign thr=0.15ATR dir=against hold=924m | gross-positive, cost-negative pre-2023 | 1939 | 4.8 | -24.5 | -10.4 | 29.4 | 0.07 / -0.32 / -0.14 | 50.2 / 20.9 |
| NQ 1 RTH leg sign thr=0.0ATR dir=against hold=120m | negative pre-2023 | 2671 | -19.1 | -33.5 | -25.0 | 14.4 | -0.24 / -0.42 / -0.31 | 226.3 / 211.9 |
| NQ 2 RTH leg sign thr=0.15ATR dir=against hold=120m | gross-positive, cost-negative pre-2023 | 1619 | 0.1 | -14.3 | -5.7 | 14.4 | 0.00 / -0.14 / -0.06 | 108.4 / 94.0 |
| NQ 3 (diag) RTH leg sign thr=0.0ATR dir=against hold=flat | negative pre-2023 | 2671 | -22.6 | -37.0 | -28.4 | 14.4 | -0.16 / -0.27 / -0.21 | 267.7 / 253.4 |
| NQ 4 (diag) ON leg sign thr=0.0ATR dir=against hold=924m | negative pre-2023 | 2598 | -8.5 | -22.8 | -14.3 | 14.4 | -0.10 / -0.27 / -0.17 | 103.4 / 89.0 |
| NQ 5 (diag) ON leg sign thr=0.15ATR dir=against hold=924m | negative pre-2023 | 1970 | -17.8 | -32.2 | -23.7 | 14.4 | -0.18 / -0.33 / -0.24 | 85.9 / 71.5 |
| RTY 1 RTH leg sign thr=0.15ATR dir=against hold=120m | negative pre-2023 | 927 | -11.7 | -26.1 | -23.8 | 14.4 | -0.20 / -0.46 / -0.42 | 84.4 / 70.1 |
| RTY 2 ON leg sign thr=0.0ATR dir=against hold=924m | negative pre-2023 | 1467 | -21.3 | -35.7 | -33.4 | 14.4 | -0.48 / -0.81 / -0.76 | 63.3 / 49.0 |
| RTY 3 RTH leg sign thr=0.0ATR dir=against hold=120m | negative pre-2023 | 1526 | -1.9 | -16.3 | -14.0 | 14.4 | -0.03 / -0.36 / -0.31 | 42.9 / 28.6 |
| RTY 4 (diag) RTH leg sign thr=0.15ATR dir=against hold=flat | gross-positive, cost-negative pre-2023 | 927 | 8.8 | -5.5 | -3.3 | 14.4 | 0.10 / -0.06 / -0.04 | 133.3 / 119.0 |
| RTY 5 (diag) RTH leg sign thr=0.0ATR dir=against hold=flat | gross-positive, cost-negative pre-2023 | 1526 | 10.4 | -4.0 | -1.7 | 14.4 | 0.16 / -0.05 / -0.02 | 54.2 / 39.9 |
| RTY 6 (diag) ON leg sign thr=0.15ATR dir=against hold=924m | negative pre-2023 | 1168 | -23.2 | -37.6 | -35.3 | 14.4 | -0.46 / -0.74 / -0.69 | 38.0 / 23.6 |
| YM 1 RTH leg sign thr=0.15ATR dir=against hold=flat | positive pre-2023 | 1698 | 22.8 | 8.4 | 14.1 | 14.4 | 0.29 / 0.11 / 0.18 | 117.4 / 103.0 |
| YM 2 RTH leg sign thr=0.15ATR dir=against hold=120m | negative pre-2023 | 1698 | -0.2 | -14.6 | -8.8 | 14.4 | -0.00 / -0.29 / -0.18 | 47.3 / 32.9 |
| YM 3 (diag) RTH leg sign thr=0.0ATR dir=against hold=flat | positive pre-2023 | 2672 | 18.8 | 4.4 | 10.1 | 14.4 | 0.31 / 0.08 / 0.17 | 111.8 / 97.4 |
| YM 4 (diag) RTH leg sign thr=0.0ATR dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2671 | 2.7 | -11.6 | -5.9 | 14.4 | 0.07 / -0.30 / -0.15 | 39.9 / 25.5 |
| YM 5 (diag) ON leg sign thr=0.15ATR dir=against hold=924m | negative pre-2023 | 1889 | -23.0 | -37.3 | -31.6 | 14.4 | -0.38 / -0.62 / -0.52 | 24.4 / 10.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 2 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.52, p(top) = 0.07); NQ: 2 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.72, p(top) = 0.21); RTY: 3 cells pass the clean rule against a replicate mean of 1.9 (p(count) = 0.27, p(top) = 0.27); YM: 2 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.58, p(top) = 0.69).
- Of 9 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.17 (RTY ON leg sign thr=0.0ATR dir=against hold=924m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 5; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 6, 'gross-positive, cost-negative pre-2023': 2, 'positive pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bi_2.py, ap_bi_pipe.py (= ap_b_pipe2 with module swap), ap_bi_job.sh, ap_sw_common.py, ap_bi_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bi2/ (`BI2_CO_all_selected_scored.csv`).

DONE BI2
