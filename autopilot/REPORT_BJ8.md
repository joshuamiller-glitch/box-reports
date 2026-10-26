# REPORT BJ8 - month-of-year (Nov-Apr) (BJ batch)

**Verdict: NO (pipeline flags one cell at gate-3, direction opposite to the pre-registered sign and failing the drift-matched null; see Lead note). FOUND 0.** 9 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.19; best pair-window standalone Sharpe +1.05.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. month-of-year (Nov-Apr). Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |       8 |          8 |         2 |               0.976 |                2 |          2 |            3 |
| NQ    |       8 |          8 |         3 |               1.003 |                2 |          3 |            3 |
| RTY   |       8 |          8 |         2 |               0.666 |                2 |          2 |            3 |
| YM    |       8 |          8 |         2 |               1.182 |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    2 |            1.925 |               5 |      0.625 |                       0.656 |            0.706 |           1.207 |    0.525 |       0.976 |                1.593 |
| NQ    |     200 |                    3 |            1.97  |               5 |      0.32  |                       0.453 |            0.74  |           1.222 |    0.78  |       1.003 |                1.663 |
| RTY   |     200 |                    2 |            1.4   |               5 |      0.425 |                       0.555 |            0.653 |           1.15  |    0.455 |       0.666 |                1.375 |
| YM    |     200 |                    2 |            1.845 |               6 |      0.565 |                       0.874 |            0.659 |           1.256 |    0.19  |       1.182 |                1.441 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | season MayOct dir=long hold=c2c | 125 | 2 | 0.98 | 0.02 | 0.82 | 0.65 / 1.76 | 0.16 / 0.04 / 0.15 | 0.12 | 0.15 | 0.79 | -0.05 | 0.00 | 215 | NO |
| ES 2 | season NovApr dir=long hold=rth | 252 | 2 | 0.34 | 0.04 | 0.43 | 0.62 / 1.64 | 0.01 / 0.10 / 0.09 | 0.01 | 0.07 | 0.69 | -0.12 | 0.00 | 378 | NO |
| ES 3 (diag) | season NovApr dir=short hold=c2c | 120 | 1 | 0.09 | -0.42 | -0.03 | -0.20 / 0.42 | -0.01 / -0.51 / 0.09 | -0.07 | -0.02 | 0.92 | -0.22 | 0.00 | 179 | diag |
| ES 4 (diag) | season MayOct dir=short hold=rth | 264 | 1 | -0.08 | -0.82 | 0.13 | 0.22 / 0.86 | -0.04 / -0.26 / 0.13 | -0.08 | -0.60 | 0.88 | -0.23 | 0.00 | 451 | diag |
| ES 5 (diag) | season NovApr dir=long hold=c2c | 120 | 1 | -0.25 | 0.20 | -0.12 | 0.08 / 1.88 | -0.08 / 0.34 / -0.20 | -0.07 | 0.02 | 0.16 | -0.24 | 0.00 | 179 | diag |
| NQ 1 | season MayOct dir=long hold=c2c | 125 | 2 | 1.00 | 0.18 | 0.72 | 0.40 / 1.61 | 0.18 / 0.04 / 0.01 | 0.13 | 0.02 | 0.76 | -0.07 | 0.00 | 215 | NO |
| NQ 2 | season NovApr dir=long hold=rth | 252 | 2 | 0.30 | 0.13 | 0.36 | 0.45 / 1.56 | -0.00 / -0.07 / 0.17 | 0.01 | 0.12 | 0.68 | -0.15 | 0.00 | 378 | NO |
| NQ 3 | season MayOct dir=short hold=rth | 264 | 2 | 0.05 | -0.78 | 0.13 | 0.12 / 0.88 | -0.02 / -0.11 / 0.03 | -0.03 | -0.54 | 0.78 | -0.22 | 0.00 | 451 | NO |
| NQ 4 (diag) | season NovApr dir=short hold=c2c | 120 | 1 | 0.20 | -0.21 | 0.05 | -0.13 / 0.61 | 0.02 / -0.49 / 0.03 | -0.05 | -0.09 | 0.79 | -0.22 | 0.00 | 179 | diag |
| NQ 5 (diag) | season MayOct dir=long hold=rth | 264 | 0 | -0.15 | 0.59 | -0.22 | -0.20 / 1.62 | -0.06 / -0.04 / -0.27 | -0.10 | 0.54 | 0.20 | -0.29 | 0.00 | 451 | diag |
| NQ 6 (diag) | season NovApr dir=long hold=c2c | 120 | 1 | -0.24 | 0.13 | -0.09 | 0.10 / 2.02 | -0.08 / 0.23 / -0.14 | -0.06 | 0.09 | 0.18 | -0.26 | 0.00 | 179 | diag |
| RTY 1 | season NovApr dir=short hold=c2c | 120 | 2 | 0.67 | 0.05 | 0.30 | -0.35 / 0.99 | 0.11 / -0.49 / 0.12 | 0.02 | 0.01 | 0.89 | -0.15 | 0.00 | 179 | NO |
| RTY 2 | season MayOct dir=short hold=rth | 264 | 2 | 0.45 | -0.33 | 0.77 | 0.89 / 0.94 | 0.08 / -0.41 / 0.35 | 0.05 | -0.63 | 0.98 | -0.11 | 0.00 | 451 | NO |
| RTY 3 (diag) | season MayOct dir=long hold=c2c | 125 | 1 | 0.61 | -0.20 | 0.31 | -0.06 / 1.58 | 0.07 / 0.08 / -0.05 | 0.03 | 0.04 | 0.71 | -0.16 | 0.00 | 215 | diag |
| RTY 4 (diag) | season NovApr dir=long hold=rth | 252 | 1 | -0.02 | -0.49 | 0.40 | 1.24 / 1.52 | -0.03 / 0.27 / 0.11 | 0.02 | -0.07 | 0.84 | -0.14 | 0.00 | 378 | diag |
| RTY 5 (diag) | season NovApr dir=short hold=rth | 252 | 1 | -0.24 | 0.20 | -0.66 | -1.48 / 0.92 | -0.08 / -0.45 / -0.19 | -0.17 | 0.07 | 0.13 | -0.33 | 0.00 | 378 | diag |
| YM 1 | season MayOct dir=long hold=c2c | 125 | 2 | 1.18 | 0.05 | 1.05 | 1.01 / 1.93 | 0.17 / 0.34 / 0.22 | 0.18 | 0.14 | 0.94 | -0.01 | 0.00 | 215 | LEAD |
| YM 2 | season NovApr dir=long hold=rth | 252 | 2 | 0.57 | 0.14 | 0.59 | 0.64 / 1.59 | 0.07 / 0.46 / -0.10 | 0.06 | -0.04 | 0.80 | -0.09 | 0.00 | 378 | NO |
| YM 3 (diag) | season NovApr dir=short hold=c2c | 120 | 1 | 0.19 | -0.40 | 0.10 | -0.04 / 0.69 | 0.00 / -0.47 / 0.14 | -0.04 | 0.13 | 0.87 | -0.21 | 0.00 | 179 | diag |
| YM 4 (diag) | season MayOct dir=long hold=rth | 264 | 1 | 0.07 | 0.22 | -0.51 | -1.04 / 1.62 | -0.03 / 0.24 / -0.56 | -0.14 | 0.46 | 0.04 | -0.33 | 0.00 | 451 | diag |
| YM 5 (diag) | season NovApr dir=long hold=c2c | 120 | 1 | -0.30 | 0.27 | -0.21 | -0.05 / 1.94 | -0.08 / 0.30 / -0.21 | -0.07 | -0.13 | 0.12 | -0.25 | 0.00 | 179 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 9 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 10 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 1 |
| worst-decile corr <= +0.30 | 19 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES season MayOct dir=long hold=c2c | clean | 0.94 | 1.59 | -132187 | -96739 | 535540 | -238683 | 1.59 | 21.9 | 1.62 | -87740 | 280110 | -101505 |
| ES season MayOct dir=long hold=c2c | H1 | 0.01 | 0.01 | -113053 | -105943 | 388925 | -118972 | 0.01 | 25.0 | 2.86 | -72286 | 151713 | -76932 |
| ES season MayOct dir=long hold=c2c | H2 | 1.11 | 1.74 | -139262 | -121731 | 448868 | -144553 | 0.86 | 25.0 | 2.63 | -78484 | 227827 | -79653 |
| ES season MayOct dir=long hold=c2c | all | 0.82 | 1.33 | -140514 | -111864 | 535540 | -238683 | 2.32 | 22.6 | 2.04 | -84551 | 280110 | -101505 |
| NQ season MayOct dir=long hold=c2c | clean | 1.01 | 1.78 | -124158 | -94089 | 560290 | -195856 | 1.64 | 24.8 | 1.64 | -85513 | 280110 | -97856 |
| NQ season MayOct dir=long hold=c2c | H1 | 0.29 | 0.49 | -118478 | -107919 | 417779 | -127662 | 0.19 | 25.0 | 2.86 | -71775 | 151713 | -76932 |
| NQ season MayOct dir=long hold=c2c | H2 | 0.47 | 0.71 | -226907 | -186839 | 785461 | -266090 | 0.30 | 30.6 | 2.49 | -80783 | 235143 | -81907 |
| NQ season MayOct dir=long hold=c2c | all | 0.72 | 1.18 | -162591 | -123691 | 785461 | -266090 | 1.57 | 26.2 | 2.03 | -83811 | 280110 | -97856 |
| RTY season MayOct dir=short hold=rth | clean | 0.68 | 1.15 | -129282 | -108213 | 362997 | -145309 | 1.76 | 22.9 | 1.54 | -82313 | 280110 | -100137 |
| RTY season MayOct dir=short hold=rth | H1 | -0.91 | -1.36 | -157798 | -143982 | 574116 | -186203 | -0.48 | 35.7 | 2.42 | -78679 | 151713 | -80425 |
| RTY season MayOct dir=short hold=rth | H2 | 2.39 | 4.38 | -142988 | -114804 | 367264 | -158792 | 2.42 | 27.8 | 2.84 | -81814 | 196001 | -83975 |
| RTY season MayOct dir=short hold=rth | all | 0.77 | 1.29 | -140838 | -119472 | 586108 | -186203 | 2.14 | 26.2 | 1.97 | -81993 | 280110 | -100137 |
| YM season MayOct dir=long hold=c2c | clean | 1.10 | 1.82 | -130311 | -98379 | 412303 | -251059 | 2.43 | 20.0 | 1.63 | -89897 | 280110 | -112772 |
| YM season MayOct dir=long hold=c2c | H1 | 0.58 | 1.02 | -91944 | -87367 | 306677 | -105270 | 0.47 | 25.0 | 3.16 | -69859 | 151713 | -76932 |
| YM season MayOct dir=long hold=c2c | H2 | 1.27 | 2.25 | -145272 | -125195 | 496740 | -149218 | 1.01 | 25.0 | 2.71 | -84062 | 227047 | -88470 |
| YM season MayOct dir=long hold=c2c | all | 1.05 | 1.76 | -143304 | -109434 | 496740 | -251059 | 3.32 | 21.4 | 2.09 | -87247 | 280110 | -112772 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES season MayOct dir=long hold=c2c | -16.4 | -31.0 | 13.3 | 27.4 | -32.1 / 7.8 | 26.5 / 28.2 | NO |
| NQ season MayOct dir=long hold=c2c | -16.5 | -8.7 | 14.8 | 24.8 | -9.5 / 11.9 | 31.2 / 32.5 | NO |
| RTY season MayOct dir=short hold=rth | -16.3 | -7.3 | 20.6 | 30.0 | -8.2 / 18.3 | 25.9 / 27.9 | NO |
| YM season MayOct dir=long hold=c2c | -12.0 | -35.5 | 8.3 | 24.7 | -36.6 / 2.9 | 31.2 / 35.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 season MayOct dir=long hold=c2c | positive pre-2023 | 664 | 33.2 | 3.9 | 18.1 | 29.4 | 0.18 / 0.02 / 0.10 | 300.1 / 270.7 |
| ES 2 season NovApr dir=long hold=rth | positive pre-2023 | 1316 | 34.6 | 5.3 | 19.4 | 29.4 | 0.29 / 0.04 / 0.16 | 107.4 / 78.1 |
| ES 3 (diag) season NovApr dir=short hold=c2c | negative pre-2023 | 632 | -81.3 | -110.6 | -96.4 | 29.4 | -0.31 / -0.42 / -0.37 | 61.2 / 31.9 |
| ES 4 (diag) season MayOct dir=short hold=rth | negative pre-2023 | 1370 | -47.4 | -76.7 | -62.5 | 29.4 | -0.51 / -0.82 / -0.67 | 37.8 / 8.5 |
| ES 5 (diag) season NovApr dir=long hold=c2c | positive pre-2023 | 632 | 81.3 | 51.9 | 66.1 | 29.4 | 0.31 / 0.20 / 0.25 | -61.2 / -90.6 |
| NQ 1 season MayOct dir=long hold=c2c | positive pre-2023 | 664 | 70.2 | 55.9 | 64.4 | 14.4 | 0.23 / 0.18 / 0.21 | 587.7 / 573.4 |
| NQ 2 season NovApr dir=long hold=rth | positive pre-2023 | 1317 | 39.1 | 24.8 | 33.4 | 14.4 | 0.20 / 0.13 / 0.17 | 144.3 / 129.9 |
| NQ 3 season MayOct dir=short hold=rth | negative pre-2023 | 1370 | -101.6 | -116.0 | -107.4 | 14.4 | -0.68 / -0.78 / -0.72 | 55.4 / 41.1 |
| NQ 4 (diag) season NovApr dir=short hold=c2c | negative pre-2023 | 632 | -63.1 | -77.4 | -68.9 | 14.4 | -0.17 / -0.21 / -0.18 | 138.9 / 124.6 |
| NQ 5 (diag) season MayOct dir=long hold=rth | positive pre-2023 | 1370 | 101.6 | 87.2 | 95.8 | 14.4 | 0.68 / 0.59 / 0.64 | -55.4 / -69.8 |
| NQ 6 (diag) season NovApr dir=long hold=c2c | positive pre-2023 | 632 | 63.1 | 48.7 | 57.3 | 14.4 | 0.17 / 0.13 / 0.15 | -138.9 / -153.3 |
| RTY 1 season NovApr dir=short hold=c2c | positive pre-2023 | 361 | 24.9 | 10.6 | 12.7 | 14.4 | 0.12 / 0.05 / 0.06 | 153.1 / 138.8 |
| RTY 2 season MayOct dir=short hold=rth | negative pre-2023 | 783 | -11.0 | -25.3 | -23.0 | 14.4 | -0.13 / -0.33 / -0.30 | 69.1 / 54.8 |
| RTY 3 (diag) season MayOct dir=long hold=c2c | negative pre-2023 | 379 | -14.8 | -29.1 | -26.7 | 14.4 | -0.10 / -0.20 / -0.18 | 97.7 / 83.3 |
| RTY 4 (diag) season NovApr dir=long hold=rth | negative pre-2023 | 753 | -34.4 | -48.7 | -46.6 | 14.4 | -0.35 / -0.49 / -0.47 | 12.0 / -2.4 |
| RTY 5 (diag) season NovApr dir=short hold=rth | positive pre-2023 | 753 | 34.4 | 20.0 | 22.1 | 14.4 | 0.35 / 0.20 / 0.22 | -12.0 / -26.3 |
| YM 1 season MayOct dir=long hold=c2c | positive pre-2023 | 665 | 21.8 | 7.4 | 13.2 | 14.4 | 0.15 / 0.05 / 0.09 | 212.8 / 198.4 |
| YM 2 season NovApr dir=long hold=rth | positive pre-2023 | 1316 | 27.2 | 12.9 | 18.6 | 14.4 | 0.30 / 0.14 / 0.21 | 103.7 / 89.4 |
| YM 3 (diag) season NovApr dir=short hold=c2c | negative pre-2023 | 631 | -71.8 | -86.1 | -80.4 | 14.4 | -0.33 / -0.40 / -0.37 | 59.7 / 45.3 |
| YM 4 (diag) season MayOct dir=long hold=rth | positive pre-2023 | 1375 | 31.0 | 16.6 | 22.4 | 14.4 | 0.42 / 0.22 / 0.30 | 2.7 / -11.7 |
| YM 5 (diag) season NovApr dir=long hold=c2c | positive pre-2023 | 631 | 71.8 | 57.4 | 63.1 | 14.4 | 0.33 / 0.27 / 0.29 | -59.7 / -74.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 2 cells pass the clean rule against a replicate mean of 1.9 (p(count) = 0.62, p(top) = 0.53); NQ: 3 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.32, p(top) = 0.78); RTY: 2 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.42, p(top) = 0.46); YM: 2 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 0.56, p(top) = 0.19).
- Of 9 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.19 (YM season MayOct dir=long hold=c2c); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell YM season MayOct dir=long hold=c2c: uplift +0.17/+0.34/+0.22, boot lo -0.01, plateau 0.00, 2x-slip +0.18, wd corr +0.14, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 7, 'negative pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_8.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj8/ (`BJ8_CO_all_selected_scored.csv`).

## Lead note (pipeline flag)
- The pipeline flags YM 'season May-Oct, LONG, close-to-close' (additive gate-3 at 20/30/50%: +0.17/+0.34/+0.22 at 20%). It is the OPPOSITE of the pre-registered sign (long Nov-Apr), it fails the drift-matched own null (rank 0.94 < 0.95; p95 1.08 vs 1.05), the bootstrap (lo -0.012), the plateau (no neighbours defined, 0.0), and the other instruments are weaker (ES +0.14, NQ +0.13, RTY +0.04 all-in); long-only ERA: positive pre-2023 (Sharpe +0.05, gross +$22 per trade). The pre-registered Nov-Apr long cell does not get selected. Verdict: NO (long beta / sign opposite to prior); no sized dollars.

DONE BJ8
