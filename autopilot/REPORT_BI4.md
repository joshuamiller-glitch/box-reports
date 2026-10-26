# REPORT BI4 - high-volume-day premium (BI batch)

**Verdict: NO (pipeline flags one weak gate-3-at-50% cell, mode opposite to the pre-registered sign; see Lead note). FOUND 0.** 7 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.23; best pair-window standalone Sharpe +1.55.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BI', before the first run)
- Rule: see IDEAS_BI.md / PREREG_AUTOPILOT.md BATCH BI (frozen before the first run). high-volume-day premium
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      12 |         12 |         1 |               0.776 |                2 |          1 |            3 |
| NQ    |      12 |         12 |         4 |               1.465 |                2 |          4 |            3 |
| RTY   |      12 |         12 |         0 |               0.908 |                1 |          0 |            3 |
| YM    |      12 |         12 |         2 |               1.18  |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |             2.1  |               6 |      0.905 |                       0.581 |            0.774 |           1.327 |    0.66  |       0.581 |                1.717 |
| NQ    |     200 |                    4 |             2.63 |               7 |      0.27  |                       0.827 |            0.759 |           1.273 |    0.33  |       1.465 |                1.738 |
| RTY   |     200 |                    0 |             2.39 |               6 |      1     |                     nan     |            0.777 |           1.273 |  nan     |     nan     |                1.675 |
| YM    |     200 |                    2 |             2.46 |               7 |      0.69  |                       1.079 |            0.798 |           1.277 |    0.145 |       1.18  |                1.781 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | prior-day volume pct>=80 of 20d mode=long RTH open hold flat | 134 | 2 | 0.58 | -0.21 | 0.58 | 0.77 / 1.42 | 0.07 / 0.35 / -0.14 | 0.05 | -0.06 | 0.88 | -0.08 | 0.75 | 219 | NO |
| ES 2 (diag) | prior-day volume pct>=90 of 60d mode=against RTH open hold flat | 71 | 1 | 0.78 | 0.02 | 0.76 | 0.77 / 1.13 | 0.11 / 0.20 / -0.09 | 0.07 | -0.43 | 0.96 | -0.05 | 0.67 | 115 | diag |
| ES 3 (diag) | prior-day volume pct>=80 of 60d mode=against RTH open hold flat | 113 | 1 | 0.61 | -0.03 | 0.58 | 0.59 / 1.61 | 0.07 / 0.14 / -0.06 | 0.04 | -0.46 | 0.84 | -0.05 | 1.00 | 193 | diag |
| ES 4 (diag) | prior-day volume pct>=80 of 20d mode=against RTH open hold flat | 134 | 1 | 0.52 | 0.08 | 0.56 | 0.68 / 1.40 | 0.07 / 0.12 / -0.02 | 0.05 | -0.44 | 0.87 | -0.04 | 0.75 | 219 | diag |
| NQ 1 | prior-day volume pct>=90 of 20d mode=long RTH open hold flat | 89 | 2 | 1.46 | 0.13 | 1.55 | 1.57 / 1.55 | 0.23 / 0.68 / -0.09 | 0.22 | 0.36 | 1.00 | 0.05 | 0.33 | 146 | NO |
| NQ 2 | prior-day volume pct>=80 of 20d mode=long RTH open hold flat | 132 | 2 | 0.81 | -0.22 | 0.52 | 0.19 / 1.43 | 0.08 / 0.14 / -0.16 | 0.03 | 0.27 | 0.85 | -0.13 | 0.75 | 216 | NO |
| NQ 3 | prior-day volume pct>=90 of 20d mode=against RTH open hold flat | 89 | 2 | 0.69 | 0.39 | 0.78 | 1.19 / 1.50 | 0.10 / 0.09 / 0.06 | 0.08 | -0.31 | 0.93 | -0.01 | 0.33 | 146 | LEAD |
| NQ 4 | prior-day volume pct>=80 of 60d mode=long RTH open hold flat | 118 | 2 | 0.35 | -0.21 | 0.37 | 0.54 / 1.53 | 0.01 / 0.20 / -0.08 | 0.02 | 0.25 | 0.74 | -0.13 | 0.75 | 189 | NO |
| NQ 5 (diag) | prior-day volume pct>=90 of 60d mode=long RTH open hold flat | 70 | 1 | 0.94 | -0.13 | 0.99 | 1.11 / 1.61 | 0.13 / 0.28 / -0.01 | 0.12 | 0.40 | 0.96 | -0.01 | 0.33 | 114 | diag |
| NQ 6 (diag) | prior-day volume pct>=80 of 60d mode=against RTH open hold flat | 118 | 1 | 0.89 | 0.33 | 1.05 | 1.30 / 1.23 | 0.14 / 0.17 / 0.08 | 0.13 | -0.51 | 0.97 | 0.03 | 0.50 | 189 | diag |
| NQ 7 (diag) | prior-day volume pct>=90 of 60d mode=against RTH open hold flat | 70 | 1 | 0.68 | 0.29 | 0.82 | 1.36 / 1.55 | 0.09 / 0.10 / 0.10 | 0.09 | -0.43 | 0.92 | 0.00 | 1.00 | 114 | diag |
| RTY 1 (diag) | prior-day volume pct>=90 of 60d mode=long RTH open hold flat | 67 | 1 | 0.91 | -0.34 | 1.11 | 1.66 / 1.49 | 0.15 / 0.30 / 0.21 | 0.17 | -0.34 | 0.96 | 0.04 | 0.67 | 113 | diag |
| RTY 2 (diag) | prior-day volume pct>=80 of 60d mode=against RTH open hold flat | 114 | 1 | 0.56 | 0.26 | 1.06 | 2.68 / 1.26 | 0.06 / 0.31 / 0.29 | 0.13 | -0.54 | 0.99 | 0.02 | 0.50 | 189 | diag |
| RTY 3 (diag) | prior-day volume pct>=90 of 20d mode=against RTH open hold flat | 83 | 1 | 0.55 | -0.33 | 0.71 | 1.19 / 1.36 | 0.05 / 0.16 / 0.16 | 0.08 | -0.34 | 0.93 | -0.03 | 1.00 | 135 | diag |
| YM 1 | prior-day volume pct>=80 of 20d mode=long RTH open hold flat | 137 | 2 | 1.18 | -0.22 | 1.13 | 1.23 / 1.32 | 0.18 / 0.87 / -0.12 | 0.19 | -0.03 | 0.98 | 0.05 | 0.00 | 223 | NO |
| YM 2 | prior-day volume pct>=90 of 20d mode=long RTH open hold flat | 84 | 2 | 0.98 | -0.18 | 0.92 | 0.81 / 1.48 | 0.15 / 0.44 / -0.06 | 0.13 | 0.35 | 0.94 | 0.01 | 0.67 | 144 | NO |
| YM 3 (diag) | prior-day volume pct>=80 of 60d mode=against RTH open hold flat | 103 | 1 | 0.65 | -0.09 | 0.95 | 2.10 / 1.24 | 0.08 / 0.28 / 0.18 | 0.12 | -0.41 | 0.96 | 0.02 | 0.50 | 182 | diag |
| YM 4 (diag) | prior-day volume pct>=80 of 20d mode=against RTH open hold flat | 136 | 1 | 0.63 | 0.01 | 0.69 | 1.20 / 1.62 | 0.06 / 0.17 / 0.08 | 0.07 | -0.37 | 0.93 | -0.03 | 1.00 | 222 | diag |
| YM 5 (diag) | prior-day volume pct>=90 of 60d mode=against RTH open hold flat | 70 | 1 | 0.62 | -0.07 | 0.67 | 1.13 / 1.51 | 0.07 / 0.16 / 0.06 | 0.07 | -0.40 | 0.88 | -0.02 | 0.67 | 116 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 7 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 1 |
| all-in uplift @20% > 0 (all scored) | 19 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 8 |
| standalone pair-window Sharpe above own random-entry null p95 | 8 |
| worst-decile corr <= +0.30 | 16 |
| plateau >= 0.75 | 8 |
| all-in uplift at 2x slippage >= +0.10 | 8 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES prior-day volume pct>=80 of 20d mode=long RTH open hold flat | clean | 0.50 | 0.86 | -132153 | -100983 | 460052 | -196221 | 0.99 | 22.9 | 1.53 | -80876 | 284314 | -90984 |
| ES prior-day volume pct>=80 of 20d mode=long RTH open hold flat | H1 | 2.02 | 3.13 | -106095 | -85174 | 209173 | -164384 | 1.94 | 17.9 | 3.18 | -69100 | 157784 | -70070 |
| ES prior-day volume pct>=80 of 20d mode=long RTH open hold flat | H2 | -0.38 | -0.45 | -136474 | -92987 | 307834 | -182344 | -0.27 | 27.8 | 2.34 | -89599 | 218353 | -96673 |
| ES prior-day volume pct>=80 of 20d mode=long RTH open hold flat | all | 0.58 | 0.91 | -140420 | -102638 | 460052 | -196221 | 1.69 | 22.6 | 1.96 | -82545 | 284314 | -96673 |
| NQ prior-day volume pct>=90 of 20d mode=long RTH open hold flat | clean | 1.51 | 3.38 | -96040 | -63274 | 373523 | -216011 | 3.68 | 16.2 | 1.69 | -81178 | 271661 | -92175 |
| NQ prior-day volume pct>=90 of 20d mode=long RTH open hold flat | H1 | 3.43 | 10.53 | -66274 | -63923 | 100540 | -67303 | 8.58 | 14.3 | 3.51 | -64594 | 136037 | -65951 |
| NQ prior-day volume pct>=90 of 20d mode=long RTH open hold flat | H2 | 0.43 | 0.55 | -224130 | -148668 | 593918 | -331654 | 0.29 | 19.4 | 2.39 | -104530 | 241811 | -126535 |
| NQ prior-day volume pct>=90 of 20d mode=long RTH open hold flat | all | 1.55 | 2.81 | -129479 | -84799 | 593918 | -331654 | 4.05 | 16.7 | 2.13 | -85910 | 271661 | -126535 |
| RTY prior-day volume pct>=90 of 60d mode=long RTH open hold flat (diag) | clean | 0.87 | 2.02 | -93087 | -74256 | 359341 | -143302 | 2.19 | 18.1 | 1.61 | -79268 | 293572 | -85069 |
| RTY prior-day volume pct>=90 of 60d mode=long RTH open hold flat (diag) | H1 | 2.32 | 6.13 | -57938 | -46859 | 228627 | -66735 | 1.71 | 17.9 | 3.13 | -72802 | 151856 | -77808 |
| RTY prior-day volume pct>=90 of 60d mode=long RTH open hold flat (diag) | H2 | 1.21 | 2.07 | -121861 | -71439 | 210777 | -126554 | 1.45 | 8.3 | 2.70 | -81089 | 217425 | -82524 |
| RTY prior-day volume pct>=90 of 60d mode=long RTH open hold flat (diag) | all | 1.11 | 2.43 | -96553 | -74943 | 359341 | -143302 | 4.13 | 15.5 | 2.08 | -79522 | 293572 | -85069 |
| YM prior-day volume pct>=80 of 20d mode=long RTH open hold flat | clean | 1.07 | 2.18 | -111081 | -82724 | 322520 | -180953 | 3.05 | 20.0 | 1.64 | -81921 | 254854 | -90151 |
| YM prior-day volume pct>=80 of 20d mode=long RTH open hold flat | H1 | 3.04 | 19.27 | -30288 | -29541 | 91099 | -30794 | 8.76 | 28.6 | 3.70 | -64744 | 139380 | -66913 |
| YM prior-day volume pct>=80 of 20d mode=long RTH open hold flat | H2 | -0.58 | -0.77 | -126740 | -100732 | 529520 | -138567 | -0.27 | 27.8 | 2.36 | -81992 | 224908 | -82524 |
| YM prior-day volume pct>=80 of 20d mode=long RTH open hold flat | all | 1.13 | 2.30 | -115579 | -83537 | 529520 | -180953 | 3.10 | 22.6 | 2.10 | -81863 | 254854 | -90151 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior-day volume pct>=80 of 20d mode=long RTH open hold flat | -21.5 | -17.4 | 20.8 | 22.3 | 8.6 / 25.0 | 45.7 / 46.4 | NO |
| NQ prior-day volume pct>=90 of 20d mode=long RTH open hold flat | -3.7 | -71.6 | 14.6 | 20.6 | 11.1 / 24.7 | 53.6 / 55.2 | NO |
| RTY prior-day volume pct>=90 of 60d mode=long RTH open hold flat (diag) | -13.8 | 16.1 | 28.3 | 7.9 | 15.4 / 27.5 | 29.5 / 39.3 | NO |
| YM prior-day volume pct>=80 of 20d mode=long RTH open hold flat | -12.1 | 6.9 | 22.1 | 30.4 | 6.1 / 22.6 | 50.3 / 50.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 prior-day volume pct>=80 of 20d mode=long RTH open hold flat | negative pre-2023 | 666 | -6.3 | -35.6 | -21.3 | 29.4 | -0.04 / -0.21 / -0.13 | 212.3 / 183.0 |
| ES 2 (diag) prior-day volume pct>=90 of 60d mode=against RTH open hold flat | positive pre-2023 | 311 | 34.4 | 5.1 | 19.3 | 29.4 | 0.12 / 0.02 / 0.06 | 519.5 / 490.2 |
| ES 3 (diag) prior-day volume pct>=80 of 60d mode=against RTH open hold flat | gross-positive, cost-negative pre-2023 | 565 | 22.9 | -6.5 | 7.7 | 29.4 | 0.10 / -0.03 / 0.03 | 510.2 / 480.8 |
| ES 4 (diag) prior-day volume pct>=80 of 20d mode=against RTH open hold flat | positive pre-2023 | 663 | 44.2 | 14.8 | 29.1 | 29.4 | 0.22 / 0.08 / 0.15 | 408.4 / 379.0 |
| NQ 1 prior-day volume pct>=90 of 20d mode=long RTH open hold flat | positive pre-2023 | 445 | 57.1 | 42.8 | 51.4 | 14.4 | 0.18 / 0.13 / 0.16 | 1027.9 / 1013.5 |
| NQ 2 prior-day volume pct>=80 of 20d mode=long RTH open hold flat | negative pre-2023 | 690 | -42.3 | -56.7 | -48.0 | 14.4 | -0.16 / -0.22 / -0.18 | 469.3 / 455.0 |
| NQ 3 prior-day volume pct>=90 of 20d mode=against RTH open hold flat | positive pre-2023 | 444 | 138.9 | 124.5 | 133.1 | 14.4 | 0.43 / 0.39 / 0.41 | 1021.2 / 1006.9 |
| NQ 4 prior-day volume pct>=80 of 60d mode=long RTH open hold flat | negative pre-2023 | 629 | -47.0 | -61.4 | -52.9 | 14.4 | -0.16 / -0.21 / -0.18 | 229.5 / 215.1 |
| NQ 5 (diag) prior-day volume pct>=90 of 60d mode=long RTH open hold flat | negative pre-2023 | 359 | -33.5 | -47.8 | -39.2 | 14.4 | -0.09 / -0.13 / -0.10 | 952.4 / 938.0 |
| NQ 6 (diag) prior-day volume pct>=80 of 60d mode=against RTH open hold flat | positive pre-2023 | 628 | 122.0 | 107.6 | 116.1 | 14.4 | 0.37 / 0.33 / 0.35 | 1170.7 / 1156.3 |
| NQ 7 (diag) prior-day volume pct>=90 of 60d mode=against RTH open hold flat | positive pre-2023 | 359 | 123.6 | 109.3 | 118.0 | 14.4 | 0.33 / 0.29 / 0.31 | 1335.8 / 1321.4 |
| RTY 1 (diag) prior-day volume pct>=90 of 60d mode=long RTH open hold flat | negative pre-2023 | 192 | -65.1 | -79.5 | -77.0 | 14.4 | -0.28 / -0.34 / -0.33 | 213.7 / 199.4 |
| RTY 2 (diag) prior-day volume pct>=80 of 60d mode=against RTH open hold flat | positive pre-2023 | 358 | 56.5 | 42.1 | 44.4 | 14.4 | 0.35 / 0.26 / 0.28 | 187.9 / 173.5 |
| RTY 3 (diag) prior-day volume pct>=90 of 20d mode=against RTH open hold flat | negative pre-2023 | 263 | -43.4 | -57.8 | -55.4 | 14.4 | -0.25 / -0.33 / -0.32 | 209.9 / 195.6 |
| YM 1 prior-day volume pct>=80 of 20d mode=long RTH open hold flat | negative pre-2023 | 689 | -15.1 | -29.5 | -23.7 | 14.4 | -0.11 / -0.22 / -0.18 | 262.4 / 248.0 |
| YM 2 prior-day volume pct>=90 of 20d mode=long RTH open hold flat | negative pre-2023 | 437 | -20.6 | -34.9 | -29.2 | 14.4 | -0.11 / -0.18 / -0.15 | 373.5 / 359.1 |
| YM 3 (diag) prior-day volume pct>=80 of 60d mode=against RTH open hold flat | negative pre-2023 | 587 | -2.9 | -17.3 | -11.5 | 14.4 | -0.02 / -0.09 / -0.06 | 388.1 / 373.7 |
| YM 4 (diag) prior-day volume pct>=80 of 20d mode=against RTH open hold flat | positive pre-2023 | 687 | 15.3 | 0.9 | 6.7 | 14.4 | 0.10 / 0.01 / 0.04 | 265.7 / 251.3 |
| YM 5 (diag) prior-day volume pct>=90 of 60d mode=against RTH open hold flat | negative pre-2023 | 335 | -5.2 | -19.5 | -13.7 | 14.4 | -0.02 / -0.07 / -0.05 | 525.6 / 511.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 1 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.91, p(top) = 0.66); NQ: 4 cells pass the clean rule against a replicate mean of 2.6 (p(count) = 0.27, p(top) = 0.33); RTY: 0 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 1.00); YM: 2 cells pass the clean rule against a replicate mean of 2.5 (p(count) = 0.69, p(top) = 0.14).
- Of 7 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.23 (NQ prior-day volume pct>=90 of 20d mode=long RTH open hold flat); bootstrap lower bound > 0 for 3 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 5, 'positive pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bi_4.py, ap_bi_pipe.py (= ap_b_pipe2 with module swap), ap_bi_job.sh, ap_sw_common.py, ap_bi_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bi4/ (`BI4_CO_all_selected_scored.csv`).

## Lead note (pipeline flag)
- The pipeline flags BI4 NQ 'prior-day volume pct>=90 of 20d, against the prior day's sign' as the only gate-3 cell (uplift >= +0.10 on clean/H1/H2 at 50% share only: +0.14/+0.15/+0.12; at 20% +0.10/+0.09/+0.06). It is the mode OPPOSITE to the pre-registered sign (long), fails the own null (rank 0.93 < 0.95), the bootstrap (lo -0.007 at 20%), the plateau (0.33) and every gate_add test; the pre-registered long-mode cells fail H2 (NQ 90/20 long: +0.23/+0.68/-0.09). ERA: positive pre-2023 (net +$125 per trade). Verdict: NO (weak lead, not carried); no sized dollars.

DONE BI4
