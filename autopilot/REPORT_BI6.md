# REPORT BI6 - daily cross-index lead-lag (BI batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 5 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.10; best pair-window standalone Sharpe +0.59.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BI', before the first run)
- Rule: see IDEAS_BI.md / PREREG_AUTOPILOT.md BATCH BI (frozen before the first run). daily cross-index lead-lag
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      16 |         16 |         0 |               0.34  |                1 |          0 |            3 |
| NQ    |      16 |         16 |         4 |               0.422 |                2 |          4 |            3 |
| RTY   |      16 |         16 |         0 |               0.55  |                1 |          0 |            3 |
| YM    |      16 |         16 |         1 |               0.621 |                2 |          1 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            2.325 |               5 |      1     |                     nan     |            0.702 |           1.143 |  nan     |     nan     |                1.556 |
| NQ    |     200 |                    4 |            3.245 |               7 |      0.445 |                       0.276 |            0.773 |           1.224 |    0.965 |       0.422 |                1.911 |
| RTY   |     200 |                    0 |            2.375 |               6 |      1     |                     nan     |            0.742 |           1.147 |  nan     |     nan     |                1.543 |
| YM    |     200 |                    1 |            2.66  |               7 |      0.92  |                       0.276 |            0.726 |           1.191 |    0.905 |       0.276 |                1.645 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | driver#1=RTY prior-day RTH ret z>=0.0 dir=against hold=flat | 514 | 1 | 0.34 | -0.14 | 0.01 | -0.68 / 1.23 | 0.00 / -0.32 / -0.01 | -0.08 | 0.09 | 0.60 | -0.17 | 0.00 | 826 | diag |
| ES 2 (diag) | driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat | 297 | 1 | 0.34 | 0.00 | 0.22 | 0.08 / 1.26 | 0.01 / -0.01 / -0.05 | -0.03 | 0.05 | 0.78 | -0.12 | 0.00 | 473 | diag |
| ES 3 (diag) | driver#2=YM prior-day RTH ret z>=0.5 dir=against hold=flat | 300 | 1 | 0.31 | 0.19 | 0.09 | -0.38 / 1.36 | 0.01 / -0.07 / -0.08 | -0.05 | -0.52 | 0.69 | -0.15 | 0.00 | 487 | diag |
| NQ 1 | driver#1=RTY prior-day RTH ret z>=0.0 dir=against hold=flat | 514 | 2 | 0.42 | 0.38 | 0.28 | 0.10 / 1.41 | 0.03 / -0.37 / 0.11 | -0.02 | 0.01 | 0.72 | -0.16 | 0.00 | 826 | NO |
| NQ 2 | driver#2=YM prior-day RTH ret z>=0.0 dir=with hold=120m | 513 | 2 | 0.31 | -0.58 | 0.20 | 0.02 / 1.22 | 0.07 / -0.09 / -0.04 | 0.01 | -0.37 | 0.72 | -0.21 | 0.50 | 825 | NO |
| NQ 3 | driver#2=YM prior-day RTH ret z>=0.5 dir=against hold=120m | 300 | 2 | 0.22 | 0.31 | 0.08 | 0.02 / 1.34 | -0.03 / -0.17 / -0.23 | -0.09 | 0.11 | 0.63 | -0.31 | 0.00 | 487 | NO |
| NQ 4 | driver#1=RTY prior-day RTH ret z>=0.0 dir=with hold=120m | 514 | 2 | 0.15 | -0.53 | 0.27 | 0.33 / 1.31 | 0.08 / 0.22 / 0.07 | 0.09 | -0.42 | 0.81 | -0.12 | 0.50 | 826 | NO |
| NQ 5 (diag) | driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat | 297 | 1 | 0.42 | 0.37 | 0.52 | 0.83 / 1.72 | 0.03 / 0.01 / 0.08 | 0.04 | -0.07 | 0.81 | -0.09 | 0.50 | 473 | diag |
| NQ 6 (diag) | driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=120m | 297 | 1 | 0.28 | 0.18 | -0.00 | -0.20 / 1.21 | -0.03 / -0.16 / -0.32 | -0.11 | 0.38 | 0.58 | -0.31 | 0.00 | 473 | diag |
| NQ 7 (diag) | driver#2=YM prior-day RTH ret z>=0.5 dir=against hold=flat | 300 | 1 | 0.25 | 0.57 | 0.28 | 0.43 / 1.38 | 0.00 / -0.04 / 0.06 | 0.00 | -0.65 | 0.70 | -0.13 | 1.00 | 487 | diag |
| RTY 1 (diag) | driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat | 296 | 1 | 0.55 | 0.57 | 0.59 | 0.74 / 1.52 | 0.07 / 0.01 / 0.05 | 0.05 | -0.55 | 0.92 | -0.09 | 1.00 | 478 | diag |
| RTY 2 (diag) | driver#1=YM prior-day RTH ret z>=0.5 dir=against hold=flat | 300 | 1 | 0.36 | 0.68 | 0.28 | 0.22 / 1.11 | 0.01 / -0.06 / -0.01 | -0.02 | -0.49 | 0.79 | -0.17 | 0.00 | 487 | diag |
| RTY 3 (diag) | driver#2=ES prior-day RTH ret z>=0.0 dir=with hold=120m | 513 | 1 | 0.33 | -0.62 | -0.15 | -0.72 / 0.97 | 0.08 / -0.30 / 0.04 | -0.05 | 0.10 | 0.73 | -0.23 | 0.00 | 823 | diag |
| YM 1 | driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=120m | 296 | 2 | 0.28 | -0.31 | -0.10 | -0.44 / 1.15 | -0.01 / -0.25 / -0.47 | -0.16 | 0.35 | 0.66 | -0.35 | 0.00 | 478 | NO |
| YM 2 (diag) | driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat | 296 | 1 | 0.62 | 0.19 | 0.35 | -0.15 / 1.67 | 0.08 / 0.06 / -0.13 | 0.02 | 0.03 | 0.74 | -0.09 | 1.00 | 478 | diag |
| YM 3 (diag) | driver#2=ES prior-day RTH ret z>=0.0 dir=against hold=flat | 513 | 1 | 0.58 | 0.11 | 0.21 | -0.49 / 1.63 | 0.04 / -0.01 / -0.17 | -0.03 | -0.29 | 0.69 | -0.15 | 0.00 | 823 | diag |
| YM 4 (diag) | driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=120m | 297 | 1 | 0.28 | -0.07 | -0.50 | -1.47 / 1.29 | -0.04 / -0.28 / -0.53 | -0.21 | 0.21 | 0.32 | -0.37 | 0.00 | 473 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 5 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 6 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 0 |
| worst-decile corr <= +0.30 | 15 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | clean | 0.28 | 0.75 | -68389 | -60062 | 429933 | -82864 | 0.59 | 53.3 | 1.47 | -81503 | 293068 | -85919 |
| ES driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | H1 | -0.01 | -0.02 | -89282 | -75109 | 246603 | -95386 | -0.01 | 42.9 | 2.81 | -76794 | 159576 | -78639 |
| ES driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | H2 | 0.15 | 0.24 | -78092 | -60506 | 166605 | -82111 | 0.17 | 47.2 | 2.44 | -88701 | 217321 | -97339 |
| ES driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | all | 0.22 | 0.49 | -76368 | -64259 | 429933 | -95386 | 0.65 | 50.6 | 1.89 | -82785 | 293068 | -97339 |
| NQ driver#1=RTY prior-day RTH ret z>=0.0 dir=with hold=120m | clean | 0.24 | 0.33 | -140717 | -114631 | 614410 | -217321 | 0.35 | 48.6 | 1.54 | -81201 | 245858 | -86451 |
| NQ driver#1=RTY prior-day RTH ret z>=0.0 dir=with hold=120m | H1 | 1.14 | 1.69 | -142551 | -128664 | 206120 | -180676 | 1.57 | 39.3 | 3.05 | -67339 | 147632 | -70805 |
| NQ driver#1=RTY prior-day RTH ret z>=0.0 dir=with hold=120m | H2 | -0.10 | -0.16 | -175405 | -152467 | 598470 | -204783 | -0.09 | 55.6 | 2.55 | -82118 | 198080 | -93884 |
| NQ driver#1=RTY prior-day RTH ret z>=0.0 dir=with hold=120m | all | 0.27 | 0.40 | -159438 | -132148 | 614410 | -217321 | 0.79 | 48.8 | 2.00 | -81494 | 245858 | -93884 |
| RTY driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | clean | 0.50 | 1.14 | -89135 | -72398 | 554403 | -106638 | 0.82 | 46.7 | 1.53 | -84403 | 283957 | -96292 |
| RTY driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | H1 | 0.75 | 1.37 | -106811 | -94938 | 247612 | -127008 | 0.73 | 46.4 | 2.84 | -73156 | 169766 | -75283 |
| RTY driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | H2 | 0.72 | 1.19 | -99315 | -87462 | 227281 | -114549 | 0.94 | 50.0 | 2.53 | -80485 | 221366 | -82816 |
| RTY driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | all | 0.59 | 1.19 | -98101 | -82152 | 554403 | -127008 | 1.53 | 47.0 | 1.96 | -82805 | 283957 | -96292 |
| YM driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=120m | clean | 0.21 | 0.36 | -110889 | -87477 | 512562 | -181407 | 0.37 | 55.2 | 1.45 | -87490 | 323488 | -107101 |
| YM driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=120m | H1 | 0.20 | 0.33 | -141184 | -129885 | 562006 | -150084 | 0.13 | 42.9 | 2.58 | -91747 | 170373 | -108304 |
| YM driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=120m | H2 | -0.95 | -1.20 | -225255 | -187208 | 505904 | -228738 | -0.86 | 55.6 | 2.01 | -97679 | 246366 | -104559 |
| YM driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=120m | all | -0.10 | -0.15 | -162284 | -132329 | 783015 | -228738 | -0.22 | 53.0 | 1.76 | -93201 | 323488 | -108304 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | -26.9 | 3.1 | 20.4 | 22.3 | 13.9 / 21.1 | 27.9 / 31.6 | NO |
| NQ driver#1=RTY prior-day RTH ret z>=0.0 dir=with hold=120m | -24.7 | 6.6 | 18.0 | 32.0 | 10.5 / 20.2 | 7.2 / 24.4 | NO |
| RTY driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat (diag) | -20.7 | -0.3 | 20.5 | 14.8 | -1.1 / 16.5 | 35.8 / 38.6 | NO |
| YM driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=120m | -31.9 | -31.7 | 0.9 | 6.8 | -16.2 / 12.3 | -27.5 / -1.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) driver#1=RTY prior-day RTH ret z>=0.0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 1530 | 10.0 | -19.4 | -8.5 | 29.4 | 0.08 / -0.14 / -0.06 | 84.8 / 55.4 |
| ES 2 (diag) driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat | positive pre-2023 | 952 | 29.7 | 0.3 | 11.2 | 29.4 | 0.17 / 0.00 / 0.06 | 109.2 / 79.9 |
| ES 3 (diag) driver#2=YM prior-day RTH ret z>=0.5 dir=against hold=flat | positive pre-2023 | 1508 | 50.5 | 21.1 | 35.2 | 29.4 | 0.45 / 0.19 / 0.31 | 109.1 / 79.8 |
| NQ 1 driver#1=RTY prior-day RTH ret z>=0.0 dir=against hold=flat | positive pre-2023 | 1531 | 96.6 | 82.2 | 88.8 | 14.4 | 0.44 / 0.38 / 0.41 | 137.2 / 122.9 |
| NQ 2 driver#2=YM prior-day RTH ret z>=0.0 dir=with hold=120m | negative pre-2023 | 2675 | -32.4 | -46.7 | -38.2 | 14.4 | -0.40 / -0.58 / -0.47 | 72.2 / 57.9 |
| NQ 3 driver#2=YM prior-day RTH ret z>=0.5 dir=against hold=120m | positive pre-2023 | 1509 | 47.5 | 33.2 | 41.7 | 14.4 | 0.45 / 0.31 / 0.40 | 45.4 / 31.1 |
| NQ 4 driver#1=RTY prior-day RTH ret z>=0.0 dir=with hold=120m | negative pre-2023 | 1531 | -58.0 | -72.4 | -65.8 | 14.4 | -0.43 / -0.53 / -0.49 | 51.2 / 36.8 |
| NQ 5 (diag) driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=flat | positive pre-2023 | 953 | 121.2 | 106.8 | 113.4 | 14.4 | 0.42 / 0.37 / 0.39 | 190.2 / 175.8 |
| NQ 6 (diag) driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=120m | positive pre-2023 | 953 | 45.8 | 31.4 | 37.9 | 14.4 | 0.26 / 0.18 / 0.22 | 50.1 / 35.7 |
| NQ 7 (diag) driver#2=YM prior-day RTH ret z>=0.5 dir=against hold=flat | positive pre-2023 | 1509 | 119.1 | 104.7 | 113.2 | 14.4 | 0.64 / 0.57 / 0.61 | 120.9 / 106.5 |
| RTY 1 (diag) driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat | positive pre-2023 | 879 | 63.5 | 49.2 | 51.4 | 14.4 | 0.74 / 0.57 / 0.60 | 81.2 / 66.9 |
| RTY 2 (diag) driver#1=YM prior-day RTH ret z>=0.5 dir=against hold=flat | positive pre-2023 | 867 | 75.5 | 61.1 | 63.3 | 14.4 | 0.84 / 0.68 / 0.70 | 54.9 / 40.6 |
| RTY 3 (diag) driver#2=ES prior-day RTH ret z>=0.0 dir=with hold=120m | negative pre-2023 | 1516 | -14.6 | -29.0 | -26.7 | 14.4 | -0.32 / -0.62 / -0.57 | 30.6 / 16.2 |
| YM 1 driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=120m | negative pre-2023 | 1530 | -1.0 | -15.4 | -9.7 | 14.4 | -0.02 / -0.31 / -0.20 | 29.9 / 15.5 |
| YM 2 (diag) driver#2=ES prior-day RTH ret z>=0.5 dir=against hold=flat | positive pre-2023 | 1531 | 29.9 | 15.6 | 21.3 | 14.4 | 0.36 / 0.19 / 0.25 | 134.2 / 119.8 |
| YM 3 (diag) driver#2=ES prior-day RTH ret z>=0.0 dir=against hold=flat | positive pre-2023 | 2649 | 21.2 | 6.8 | 12.6 | 14.4 | 0.32 / 0.11 / 0.19 | 82.5 / 68.1 |
| YM 4 (diag) driver#1=RTY prior-day RTH ret z>=0.5 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 950 | 9.1 | -5.2 | -1.3 | 14.4 | 0.12 / -0.07 / -0.02 | 27.3 / 12.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 0 cells pass the clean rule against a replicate mean of 2.3 (p(count) = 1.00); NQ: 4 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 0.45, p(top) = 0.96); RTY: 0 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 1.00); YM: 1 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.92, p(top) = 0.91).
- Of 5 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.10 (NQ driver#1=RTY prior-day RTH ret z>=0.0 dir=with hold=120m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 3, 'positive pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bi_6.py, ap_bi_pipe.py (= ap_b_pipe2 with module swap), ap_bi_job.sh, ap_sw_common.py, ap_bi_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bi6/ (`BI6_CO_all_selected_scored.csv`).

DONE BI6
