# REPORT SW12 - frozen LightGBM direction model, 60/120/240-min horizons (D12 H3)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 9 selected cells (+10 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.13; best pair-window standalone Sharpe +0.79.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Model: LightGBM (150 trees, 8 leaves, lr 0.05, min 500 per leaf, subsample 0.7, colsample 0.8, L2 5, seed 11), FROZEN, trained once on label days <= 2022-12-31 (BTC: <= 2023-07-31, its history starts 2022) on causal 1-min-bar features sampled at 5-min bar ends (returns 1-120 min in sigma units, abs-move ratios, signed-volume imbalances 15/60, VWAP z, minute-of-day, day of week, prior-day range percentile, day return/ADR20). No retraining, no tuning on clean. Target: sign of the forward return from the next open over the horizon. Trade when P >= th (long) or <= 1-th (short) at 5-min bar ends, exact hold H or 2H.
- Instruments: RTY, YM, GC, BTC. Grid: 36 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      36 |         36 |         0 |               0.662 |                1 |          0 |            3 |
| GC    |      36 |         35 |         0 |               0.333 |                1 |          0 |            3 |
| RTY   |      36 |         36 |         0 |               0.327 |                1 |          0 |            3 |
| YM    |      36 |         36 |         9 |               1.11  |                2 |          9 |            1 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| RTY   |     100 |                    0 |             2.46 |               7 |          1 |                     nan     |            0.629 |           1.069 |   nan    |      nan    |                1.457 |
| YM    |     100 |                    9 |             2.49 |               7 |          0 |                       0.676 |            0.64  |           1.142 |     0.36 |        1.11 |                1.673 |
| GC    |     100 |                    0 |             1.64 |               5 |          1 |                     nan     |            0.602 |           1.108 |   nan    |      nan    |                1.465 |
| BTC   |     100 |                    0 |             3.58 |               9 |          1 |                     nan     |            0.665 |           1.029 |   nan    |      nan    |                1.539 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTY 1 (diag) | LGBM(<=2022) fwd240m P>=0.56 hold=480m all | 514 | 1 | 0.33 | 3.36 | 0.56 | 1.14 / 0.91 | -0.00 / 0.27 / 0.15 | 0.02 | 0.08 | 0.97 | -0.11 | 0.50 | 810 | diag |
| RTY 2 (diag) | LGBM(<=2022) fwd240m P>=0.54 hold=480m day | 210 | 1 | 0.07 | 2.86 | 0.19 | 0.37 / 1.55 | -0.05 / 0.06 / 0.14 | -0.03 | -0.36 | 0.70 | -0.19 | 0.00 | 322 | diag |
| RTY 3 (diag) | LGBM(<=2022) fwd240m P>=0.52 hold=480m day | 332 | 1 | 0.02 | 2.58 | 0.09 | 0.17 / 1.07 | -0.05 / 0.24 / -0.03 | -0.04 | -0.01 | 0.67 | -0.18 | 0.00 | 523 | diag |
| YM 1 | LGBM(<=2022) fwd240m P>=0.54 hold=480m all | 856 | 2 | 1.11 | 1.77 | 0.63 | 0.21 / 1.34 | 0.15 / 0.80 / -0.21 | 0.08 | 0.21 | 0.94 | -0.11 | 0.50 | 1342 | NO |
| YM 2 | LGBM(<=2022) fwd240m P>=0.54 hold=480m day | 295 | 2 | 1.10 | 1.85 | 0.58 | -0.35 / 1.13 | 0.14 / 0.48 / -0.24 | 0.07 | 0.16 | 0.92 | -0.06 | 0.50 | 461 | NO |
| YM 3 | LGBM(<=2022) fwd240m P>=0.56 hold=480m day | 128 | 2 | 0.96 | 1.71 | 0.79 | 0.43 / 1.32 | 0.11 / 0.27 / -0.02 | 0.08 | 0.24 | 0.93 | -0.03 | 0.50 | 204 | NO |
| YM 4 | LGBM(<=2022) fwd240m P>=0.52 hold=480m day | 411 | 2 | 0.82 | 1.45 | 0.11 | -1.21 / 1.58 | 0.08 / 0.15 / -0.34 | -0.03 | 0.30 | 0.65 | -0.17 | 0.00 | 660 | NO |
| YM 5 | LGBM(<=2022) fwd240m P>=0.52 hold=480m all | 1010 | 2 | 0.61 | 1.02 | 0.55 | 0.50 / 1.31 | 0.04 / 0.21 / 0.16 | 0.02 | 0.26 | 0.95 | -0.14 | 0.50 | 1614 | NO |
| YM 6 | LGBM(<=2022) fwd120m P>=0.52 hold=240m all | 2439 | 2 | 0.59 | 0.94 | 0.27 | -0.31 / 0.54 | 0.07 / 0.12 / 0.05 | -0.03 | 0.33 | 0.93 | -0.11 | 0.50 | 3911 | NO |
| YM 7 | LGBM(<=2022) fwd240m P>=0.56 hold=480m all | 515 | 2 | 0.38 | 1.95 | 0.21 | 0.06 / 1.18 | -0.01 / 0.27 / -0.06 | -0.04 | 0.16 | 0.91 | -0.19 | 0.00 | 814 | NO |
| YM 8 | LGBM(<=2022) fwd240m P>=0.52 hold=240m day | 875 | 2 | 0.31 | 1.18 | -0.31 | -1.50 / 1.27 | 0.00 / -0.02 / -0.24 | -0.10 | 0.12 | 0.42 | -0.23 | 0.00 | 1411 | NO |
| YM 9 | LGBM(<=2022) fwd240m P>=0.56 hold=240m all | 1051 | 2 | 0.20 | 2.18 | 0.14 | 0.14 / 0.57 | -0.02 / 0.00 / 0.05 | -0.07 | 0.25 | 0.96 | -0.18 | 0.00 | 1661 | NO |
| YM 10 (diag) | LGBM(<=2022) fwd240m P>=0.52 hold=240m all | 2366 | 1 | 0.39 | 1.26 | 0.13 | -0.21 / 0.71 | 0.01 / 0.15 / -0.14 | -0.11 | 0.29 | 0.96 | -0.20 | 0.00 | 3753 | diag |
| GC 1 (diag) | LGBM(<=2022) fwd120m P>=0.56 hold=120m day | 297 | 1 | 0.33 | 0.97 | 0.69 | 1.03 / 0.91 | 0.04 / 2.26 / -0.69 | 0.08 | 0.14 | 0.97 | -0.30 | 1.00 | 441 | diag |
| GC 2 (diag) | LGBM(<=2022) fwd120m P>=0.56 hold=120m all | 757 | 1 | 0.11 | 1.68 | -0.42 | -0.77 / 0.79 | 0.01 / -0.49 / -1.47 | -0.46 | 0.09 | 0.69 | -0.95 | 0.00 | 1211 | diag |
| GC 3 (diag) | LGBM(<=2022) fwd60m P>=0.54 hold=120m day | 1018 | 1 | -0.12 | -0.01 | 0.42 | 0.81 / 1.09 | -0.03 / 1.36 / -0.85 | -0.07 | -0.25 | 0.98 | -0.30 | 0.00 | 1634 | diag |
| BTC 1 (diag) | LGBM(<=2022) fwd120m P>=0.52 hold=240m day | 939 | 1 | 0.66 | 2.21 | 0.16 | -0.52 / 1.24 | 0.06 / -0.63 / -0.05 | -0.10 | -0.07 | 0.78 | -0.24 | 0.00 | 1462 | diag |
| BTC 2 (diag) | LGBM(<=2022) fwd240m P>=0.52 hold=480m day | 463 | 1 | 0.57 | 2.27 | 0.35 | 0.13 / 1.46 | 0.04 / -0.19 / 0.04 | -0.01 | -0.51 | 0.78 | -0.15 | 0.50 | 722 | diag |
| BTC 3 (diag) | LGBM(<=2022) fwd240m P>=0.54 hold=480m day | 431 | 1 | 0.47 | 2.35 | 0.29 | 0.14 / 1.86 | 0.03 / -0.17 / 0.01 | -0.02 | -0.55 | 0.74 | -0.16 | 0.00 | 669 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 9 |
| diagnostic cells read | 10 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 10 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 6 |
| worst-decile corr <= +0.30 | 17 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC LGBM(<=2022) fwd240m P>=0.52 hold=480m day (diag) | clean | 0.46 | 0.71 | -127448 | -104868 | 537003 | -170582 | 0.78 | 46.7 | 1.50 | -87247 | 248515 | -93871 |
| BTC LGBM(<=2022) fwd240m P>=0.52 hold=480m day (diag) | H1 | 0.19 | 0.28 | -127586 | -110880 | 281914 | -138096 | 0.17 | 42.9 | 2.64 | -84722 | 176170 | -84939 |
| BTC LGBM(<=2022) fwd240m P>=0.52 hold=480m day (diag) | H2 | 0.04 | 0.06 | -78104 | -59864 | 272912 | -78148 | 0.03 | 44.4 | 2.34 | -82119 | 222797 | -82519 |
| BTC LGBM(<=2022) fwd240m P>=0.52 hold=480m day (diag) | all | 0.35 | 0.53 | -126867 | -102671 | 537003 | -170582 | 0.89 | 45.2 | 1.86 | -86541 | 248515 | -93871 |
| GC LGBM(<=2022) fwd120m P>=0.56 hold=120m day (diag) | clean | 0.33 | 0.52 | -121433 | -102888 | 674862 | -158125 | 0.45 | 37.1 | 1.50 | -84009 | 246583 | -108884 |
| GC LGBM(<=2022) fwd120m P>=0.56 hold=120m day (diag) | H1 | 3.05 | 8.74 | -252366 | -178855 | 506453 | -266223 | 4.57 | 17.9 | 5.09 | -57693 | 159024 | -73516 |
| GC LGBM(<=2022) fwd120m P>=0.56 hold=120m day (diag) | H2 | -0.35 | -0.44 | -619765 | -457490 | 1389601 | -752812 | -0.27 | 30.6 | 1.61 | -168233 | 446059 | -210767 |
| GC LGBM(<=2022) fwd120m P>=0.56 hold=120m day (diag) | all | 0.69 | 1.05 | -324657 | -220598 | 1389601 | -752812 | 1.61 | 32.7 | 1.98 | -103934 | 446059 | -210767 |
| RTY LGBM(<=2022) fwd240m P>=0.56 hold=480m all (diag) | clean | 0.30 | 0.45 | -121315 | -100326 | 518619 | -179809 | 0.52 | 49.5 | 1.46 | -89308 | 314957 | -99240 |
| RTY LGBM(<=2022) fwd240m P>=0.56 hold=480m all (diag) | H1 | 1.19 | 1.89 | -92864 | -82386 | 326178 | -104945 | 0.72 | 39.3 | 3.10 | -76001 | 157523 | -76884 |
| RTY LGBM(<=2022) fwd240m P>=0.56 hold=480m all (diag) | H2 | 1.07 | 1.79 | -80520 | -73810 | 227887 | -86057 | 1.10 | 41.7 | 2.44 | -86794 | 213425 | -92144 |
| RTY LGBM(<=2022) fwd240m P>=0.56 hold=480m all (diag) | all | 0.56 | 0.87 | -111075 | -93209 | 518619 | -179809 | 1.46 | 46.4 | 1.91 | -87503 | 314957 | -99240 |
| YM LGBM(<=2022) fwd240m P>=0.54 hold=480m all | clean | 1.07 | 1.78 | -112213 | -91175 | 355568 | -174553 | 2.73 | 39.0 | 1.61 | -87101 | 309503 | -100411 |
| YM LGBM(<=2022) fwd240m P>=0.54 hold=480m all | H1 | 1.34 | 2.40 | -183190 | -153494 | 400691 | -223183 | 1.35 | 46.4 | 3.62 | -67509 | 130025 | -78750 |
| YM LGBM(<=2022) fwd240m P>=0.54 hold=480m all | H2 | -0.76 | -1.11 | -152448 | -139903 | 641302 | -152770 | -0.56 | 58.3 | 2.09 | -90568 | 263259 | -99231 |
| YM LGBM(<=2022) fwd240m P>=0.54 hold=480m all | all | 0.63 | 1.02 | -149354 | -124963 | 641302 | -223183 | 1.80 | 44.0 | 1.99 | -87165 | 309503 | -100411 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| RTY LGBM(<=2022) fwd240m P>=0.56 hold=480m all (diag) | -21.6 | -5.7 | 9.6 | 11.3 | -6.5 / 4.1 | 31.3 / 33.1 | NO |
| YM LGBM(<=2022) fwd240m P>=0.54 hold=480m all | -17.1 | -7.6 | 6.1 | 13.5 | -8.5 / 7.8 | 27.7 / 43.7 | NO |
| GC LGBM(<=2022) fwd120m P>=0.56 hold=120m day (diag) | -5.0 | -224.7 | -32.3 | -88.7 | -24.0 / 19.7 | -14.5 / 23.4 | NO |
| BTC LGBM(<=2022) fwd240m P>=0.52 hold=480m day (diag) | -24.7 | 4.1 | 9.6 | 32.0 | 3.3 / 4.7 | 15.9 / 16.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| RTY 1 (diag) LGBM(<=2022) fwd240m P>=0.56 hold=480m all | positive pre-2023 | 1540 | 191.0 | 176.7 | 179.1 | 14.4 | 3.62 / 3.36 / 3.40 | 30.6 / 16.2 |
| RTY 2 (diag) LGBM(<=2022) fwd240m P>=0.54 hold=480m day | positive pre-2023 | 614 | 352.9 | 338.5 | 341.1 | 14.4 | 2.97 / 2.86 / 2.88 | 27.5 / 13.1 |
| RTY 3 (diag) LGBM(<=2022) fwd240m P>=0.52 hold=480m day | positive pre-2023 | 1040 | 230.5 | 216.1 | 218.6 | 14.4 | 2.75 / 2.58 / 2.61 | 20.3 / 5.9 |
| YM 1 LGBM(<=2022) fwd240m P>=0.54 hold=480m all | positive pre-2023 | 4425 | 79.5 | 65.2 | 71.0 | 14.4 | 2.16 / 1.77 / 1.93 | 54.1 / 39.7 |
| YM 2 LGBM(<=2022) fwd240m P>=0.54 hold=480m day | positive pre-2023 | 1589 | 177.1 | 162.7 | 168.6 | 14.4 | 2.01 / 1.85 / 1.91 | 194.9 / 180.6 |
| YM 3 LGBM(<=2022) fwd240m P>=0.56 hold=480m day | positive pre-2023 | 720 | 229.9 | 215.6 | 221.6 | 14.4 | 1.82 / 1.71 / 1.76 | 351.9 / 337.6 |
| YM 4 LGBM(<=2022) fwd240m P>=0.52 hold=480m day | positive pre-2023 | 2215 | 130.9 | 116.6 | 122.4 | 14.4 | 1.63 / 1.45 / 1.53 | 118.9 / 104.6 |
| YM 5 LGBM(<=2022) fwd240m P>=0.52 hold=480m all | positive pre-2023 | 5257 | 47.1 | 32.7 | 38.5 | 14.4 | 1.47 / 1.02 / 1.20 | 35.9 / 21.6 |
| YM 6 LGBM(<=2022) fwd120m P>=0.52 hold=240m all | positive pre-2023 | 12780 | 29.0 | 14.7 | 20.4 | 14.4 | 1.87 / 0.94 / 1.31 | 26.8 / 12.5 |
| YM 7 LGBM(<=2022) fwd240m P>=0.56 hold=480m all | positive pre-2023 | 2863 | 112.2 | 97.8 | 103.7 | 14.4 | 2.23 / 1.95 / 2.07 | 31.4 / 17.1 |
| YM 8 LGBM(<=2022) fwd240m P>=0.52 hold=240m day | positive pre-2023 | 4679 | 62.3 | 47.9 | 53.7 | 14.4 | 1.53 / 1.18 / 1.32 | 29.3 / 14.9 |
| YM 9 LGBM(<=2022) fwd240m P>=0.56 hold=240m all | positive pre-2023 | 5743 | 76.0 | 61.6 | 67.5 | 14.4 | 2.68 / 2.18 / 2.39 | 20.1 / 5.7 |
| YM 10 (diag) LGBM(<=2022) fwd240m P>=0.52 hold=240m all | positive pre-2023 | 12334 | 35.2 | 20.9 | 26.6 | 14.4 | 2.12 / 1.26 / 1.60 | 21.6 / 7.2 |
| GC 1 (diag) LGBM(<=2022) fwd120m P>=0.56 hold=120m day | positive pre-2023 | 1416 | 82.3 | 58.0 | 67.7 | 24.4 | 1.37 / 0.97 / 1.13 | 48.6 / 24.3 |
| GC 2 (diag) LGBM(<=2022) fwd120m P>=0.56 hold=120m all | positive pre-2023 | 4025 | 72.1 | 47.7 | 57.6 | 24.4 | 2.47 / 1.68 / 2.01 | 29.5 / 5.2 |
| GC 3 (diag) LGBM(<=2022) fwd60m P>=0.54 hold=120m day | gross-positive, cost-negative pre-2023 | 5384 | 24.2 | -0.2 | 9.7 | 24.4 | 1.02 / -0.01 / 0.41 | 18.2 / -6.2 |
| BTC 1 (diag) LGBM(<=2022) fwd120m P>=0.52 hold=240m day | positive pre-2023 | 695 | 335.5 | 281.1 | 313.6 | 54.4 | 2.63 / 2.21 / 2.46 | 196.3 / 142.0 |
| BTC 2 (diag) LGBM(<=2022) fwd240m P>=0.52 hold=480m day | positive pre-2023 | 343 | 564.4 | 510.1 | 542.6 | 54.4 | 2.51 / 2.27 / 2.41 | 316.4 / 262.0 |
| BTC 3 (diag) LGBM(<=2022) fwd240m P>=0.54 hold=480m day | positive pre-2023 | 294 | 638.8 | 584.4 | 617.0 | 54.4 | 2.56 / 2.35 / 2.48 | 253.9 / 199.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 3.6 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 1.00); RTY: 0 cells pass the clean rule against a replicate mean of 2.5 (p(count) = 1.00); YM: 9 cells pass the clean rule against a replicate mean of 2.5 (p(count) = 0.00, p(top) = 0.36).
- Of 9 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.13 (YM LGBM(<=2022) fwd240m P>=0.54 hold=480m all); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 9}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_12.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw12/ (`SW12_CO_all_selected_scored.csv`).

DONE SW12
