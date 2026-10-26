# REPORT SW11 - frozen LightGBM direction model, 5/15/30-min horizons (D12 H1/H2)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+15 diagnostic) scored on 5 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe +0.45.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Model: LightGBM (150 trees, 8 leaves, lr 0.05, min 500 per leaf, subsample 0.7, colsample 0.8, L2 5, seed 11), FROZEN, trained once on label days <= 2022-12-31 (BTC: <= 2023-07-31, its history starts 2022) on causal 1-min-bar features sampled at 5-min bar ends (returns 1-120 min in sigma units, abs-move ratios, signed-volume imbalances 15/60, VWAP z, minute-of-day, day of week, prior-day range percentile, day return/ADR20). No retraining, no tuning on clean. Target: sign of the forward return from the next open over the horizon. Trade when P >= th (long) or <= 1-th (short) at 5-min bar ends, exact hold H or 2H.
- Instruments: ES, RTY, GC, CL, BTC. Grid: 36 cells per instrument = 3 horizons x 3 th (0.52/0.54/0.56) x 2 hold multiples x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      36 |         36 |         0 |              -0.797 |                0 |          0 |            3 |
| CL    |      36 |         34 |         0 |              -0.512 |                1 |          0 |            3 |
| ES    |      36 |         36 |         0 |              -0.434 |                1 |          0 |            3 |
| GC    |      36 |         36 |         0 |              -0.575 |                1 |          0 |            3 |
| RTY   |      36 |         34 |         0 |               0.832 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |
| RTY   |     100 |                    0 |             0.17 |               2 |          1 |                         nan |            0.511 |           1.181 |      nan |         nan |                1.181 |
| GC    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |
| CL    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |
| BTC   |     100 |                    0 |             0.16 |               2 |          1 |                         nan |            0.418 |           0.915 |      nan |         nan |                0.915 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | LGBM(<=2022) fwd15m P>=0.56 hold=30m day | 483 | 1 | -0.43 | -0.10 | -0.82 | -1.10 / 0.03 | -0.11 / -0.80 / -0.15 | -0.38 | -0.32 | 0.92 | -0.47 | 0.00 | 757 | diag |
| ES 2 (diag) | LGBM(<=2022) fwd15m P>=0.56 hold=15m day | 584 | 1 | -0.45 | -0.70 | -1.40 | -2.35 / -0.83 | -0.13 / -1.10 / -0.43 | -0.56 | -0.35 | 0.96 | -0.58 | 0.00 | 904 | diag |
| ES 3 (diag) | LGBM(<=2022) fwd30m P>=0.52 hold=60m day | 3208 | 0 | -0.76 | -0.78 | -1.20 | -1.85 / -0.39 | -0.18 / -0.34 / -0.35 | -0.50 | 0.50 | 0.82 | -0.43 | 0.00 | 5154 | diag |
| RTY 1 (diag) | LGBM(<=2022) fwd5m P>=0.56 hold=5m day | 45 | 1 | 0.83 | 0.96 | 0.45 | -0.27 / 0.39 | 0.15 / 0.04 / -0.18 | 0.02 | -0.42 | 1.00 | -0.11 | 0.50 | 69 S | diag |
| RTY 2 (diag) | LGBM(<=2022) fwd5m P>=0.56 hold=5m all | 119 | 1 | 0.35 | 0.52 | -0.22 | -1.11 / 0.07 | 0.07 / -0.30 / -0.25 | -0.16 | -0.21 | 0.99 | -0.24 | 0.00 | 187 | diag |
| RTY 3 (diag) | LGBM(<=2022) fwd5m P>=0.56 hold=10m day | 44 | 1 | -0.44 | 0.48 | -0.29 | 0.24 / 0.56 | -0.08 / -0.01 / 0.01 | -0.06 | -0.44 | 0.77 | -0.22 | 0.00 | 67 S | diag |
| GC 1 (diag) | LGBM(<=2022) fwd15m P>=0.56 hold=30m day | 1199 | 1 | -0.57 | -0.34 | -0.05 | 0.32 / 0.39 | -0.11 / 0.86 / -0.46 | -0.24 | -0.36 | 1.00 | -0.38 | 0.00 | 1936 | diag |
| GC 2 (diag) | LGBM(<=2022) fwd30m P>=0.56 hold=60m day | 668 | 0 | -1.29 | 0.01 | 0.04 | 0.85 / 0.74 | -0.23 / 1.20 / -0.55 | -0.19 | -0.47 | 0.96 | -0.40 | 0.00 | 1074 | diag |
| GC 3 (diag) | LGBM(<=2022) fwd30m P>=0.54 hold=60m day | 1987 | 0 | -1.36 | -0.39 | -0.60 | -0.11 / 0.89 | -0.27 / 0.45 / -0.49 | -0.37 | -0.58 | 0.61 | -0.49 | 0.00 | 3173 | diag |
| CL 1 (diag) | LGBM(<=2022) fwd30m P>=0.56 hold=30m day | 68 | 1 | -0.51 | 0.43 | -0.25 | -0.19 / -0.51 | -0.10 / 0.14 / -0.83 | -0.35 | -0.25 | 1.00 | -0.62 | 0.00 | 108 | diag |
| CL 2 (diag) | LGBM(<=2022) fwd15m P>=0.56 hold=30m day | 105 | 1 | -0.54 | 0.83 | -0.09 | 0.22 / -0.62 | -0.07 / -0.01 / -0.07 | -0.15 | -0.11 | 1.00 | -0.30 | 0.00 | 175 | diag |
| CL 3 (diag) | LGBM(<=2022) fwd30m P>=0.56 hold=60m day | 63 | 0 | -0.92 | 1.09 | 0.17 | 0.79 / 0.09 | -0.20 / -0.01 / -0.01 | -0.19 | 0.06 | 1.00 | -0.43 | 0.00 | 100 | diag |
| BTC 1 (diag) | LGBM(<=2022) fwd30m P>=0.56 hold=60m day | 1777 | 0 | -0.80 | 5.61 | -0.60 | -0.37 / 0.44 | -0.16 / -0.33 / 0.05 | -0.25 | -0.36 | 0.67 | -0.36 | 0.00 | 2764 | diag |
| BTC 2 (diag) | LGBM(<=2022) fwd5m P>=0.56 hold=10m day | 4349 | 0 | -0.91 | 1.81 | -0.61 | -0.06 / -1.27 | -0.24 / -0.10 / -0.04 | -0.49 | 0.51 | 1.00 | -0.37 | 0.00 | 6697 | diag |
| BTC 3 (diag) | LGBM(<=2022) fwd30m P>=0.54 hold=60m day | 2641 | 0 | -1.36 | 4.68 | -0.79 | -0.01 / 0.69 | -0.32 / -0.32 / 0.22 | -0.34 | -0.16 | 0.58 | -0.43 | 0.00 | 4096 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 1 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 9 |
| worst-decile corr <= +0.30 | 13 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 2 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC LGBM(<=2022) fwd30m P>=0.56 hold=60m day (diag) | clean | -0.77 | -1.03 | -132072 | -115529 | 1332614 | -190992 | -0.52 | 57.1 | 1.30 | -90063 | 273062 | -115457 |
| BTC LGBM(<=2022) fwd30m P>=0.56 hold=60m day (diag) | H1 | -0.69 | -0.79 | -288069 | -228635 | 877688 | -352128 | -0.30 | 39.3 | 2.50 | -79687 | 200598 | -88189 |
| BTC LGBM(<=2022) fwd30m P>=0.56 hold=60m day (diag) | H2 | 0.15 | 0.21 | -90944 | -79847 | 422910 | -91711 | 0.08 | 44.4 | 2.34 | -85347 | 216166 | -89577 |
| BTC LGBM(<=2022) fwd30m P>=0.56 hold=60m day (diag) | all | -0.60 | -0.76 | -164260 | -130640 | 1332614 | -352128 | -0.70 | 51.8 | 1.72 | -88807 | 273062 | -115457 |
| CL LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | clean | -0.49 | -0.62 | -169406 | -134331 | 1029005 | -279030 | -0.44 | 36.2 | 1.39 | -84854 | 280977 | -93532 |
| CL LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | H1 | -0.76 | -0.90 | -97809 | -80198 | 219871 | -98435 | -0.46 | 21.4 | 2.82 | -72445 | 171196 | -78287 |
| CL LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | H2 | 0.42 | 0.79 | -335643 | -230346 | 706664 | -394759 | 0.50 | 30.6 | 2.23 | -104382 | 263012 | -104948 |
| CL LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | all | -0.09 | -0.14 | -202970 | -155544 | 1392243 | -394759 | -0.14 | 32.7 | 1.80 | -89529 | 280977 | -104948 |
| ES LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | clean | -0.58 | -0.73 | -164097 | -130084 | 987656 | -240710 | -0.55 | 47.6 | 1.35 | -87674 | 265945 | -94193 |
| ES LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | H1 | -1.39 | -1.51 | -379788 | -304483 | 1043088 | -598072 | -0.73 | 50.0 | 2.03 | -84100 | 228741 | -97574 |
| ES LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | H2 | -0.80 | -1.00 | -201478 | -175144 | 634720 | -217277 | -0.54 | 52.8 | 2.14 | -83503 | 210567 | -92137 |
| ES LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | all | -0.82 | -0.96 | -224516 | -180409 | 1882905 | -598072 | -0.87 | 49.4 | 1.64 | -88356 | 265945 | -97574 |
| GC LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | clean | -0.61 | -0.85 | -129626 | -110758 | 1111147 | -185240 | -0.50 | 55.2 | 1.35 | -89775 | 277120 | -104332 |
| GC LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | H1 | 1.87 | 3.77 | -193235 | -159953 | 508580 | -200874 | 1.75 | 32.1 | 3.69 | -63801 | 155180 | -75635 |
| GC LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | H2 | -0.52 | -0.67 | -325348 | -304160 | 1719851 | -326828 | -0.26 | 36.1 | 1.83 | -123032 | 311639 | -130420 |
| GC LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | all | -0.05 | -0.07 | -263454 | -204953 | 1719851 | -326828 | -0.07 | 47.6 | 1.80 | -99339 | 311639 | -130420 |
| RTY LGBM(<=2022) fwd5m P>=0.56 hold=5m day (diag) | clean | 0.83 | 1.25 | -154275 | -98259 | 578731 | -274925 | 1.30 | 11.4 | 1.61 | -80899 | 252179 | -88200 |
| RTY LGBM(<=2022) fwd5m P>=0.56 hold=5m day (diag) | H1 | 0.61 | 0.86 | -54054 | -49043 | 137287 | -57523 | 0.40 | 10.7 | 2.87 | -78476 | 151713 | -88404 |
| RTY LGBM(<=2022) fwd5m P>=0.56 hold=5m day (diag) | H2 | -0.54 | -0.67 | -215949 | -137818 | 448624 | -261048 | -0.40 | 13.9 | 2.12 | -79307 | 217425 | -79653 |
| RTY LGBM(<=2022) fwd5m P>=0.56 hold=5m day (diag) | all | 0.45 | 0.64 | -161309 | -104152 | 705768 | -274925 | 0.88 | 11.9 | 1.92 | -81391 | 252179 | -88404 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | -48.4 | -61.1 | 0.8 | -21.7 | 2.9 / 12.1 | -69.8 / -40.3 | NO |
| RTY LGBM(<=2022) fwd5m P>=0.56 hold=5m day (diag) | -23.0 | -17.6 | 19.5 | 34.6 | 14.7 / 25.7 | 10.6 / 28.3 | NO |
| GC LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | -31.3 | -62.0 | -16.8 | -45.6 | -15.7 / 7.1 | 33.7 / 40.3 | NO |
| CL LGBM(<=2022) fwd15m P>=0.56 hold=30m day (diag) | -32.2 | -16.0 | 1.8 | 4.1 | 1.1 / 11.8 | 30.0 / 40.0 | NO |
| BTC LGBM(<=2022) fwd30m P>=0.56 hold=60m day (diag) | -40.4 | -35.0 | 6.3 | 20.5 | -36.0 / 6.9 | -9.4 / -0.8 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) LGBM(<=2022) fwd15m P>=0.56 hold=30m day | gross-positive, cost-negative pre-2023 | 2203 | 27.1 | -2.3 | 12.2 | 29.4 | 1.20 / -0.10 / 0.54 | 12.3 / -17.1 |
| ES 2 (diag) LGBM(<=2022) fwd15m P>=0.56 hold=15m day | gross-positive, cost-negative pre-2023 | 2628 | 18.3 | -11.1 | 3.4 | 29.4 | 1.14 / -0.70 / 0.21 | 16.6 / -12.8 |
| ES 3 (diag) LGBM(<=2022) fwd30m P>=0.52 hold=60m day | gross-positive, cost-negative pre-2023 | 17147 | 20.1 | -9.3 | 5.0 | 29.4 | 1.70 / -0.78 / 0.42 | 12.8 / -16.5 |
| RTY 1 (diag) LGBM(<=2022) fwd5m P>=0.56 hold=5m day | positive pre-2023 | 163 | 33.1 | 18.7 | 20.9 | 14.4 | 1.63 / 0.96 / 1.07 | 50.4 / 36.1 |
| RTY 2 (diag) LGBM(<=2022) fwd5m P>=0.56 hold=5m all | positive pre-2023 | 403 | 19.7 | 5.4 | 7.5 | 14.4 | 1.89 / 0.52 / 0.73 | 21.0 / 6.6 |
| RTY 3 (diag) LGBM(<=2022) fwd5m P>=0.56 hold=10m day | positive pre-2023 | 159 | 27.6 | 13.3 | 15.5 | 14.4 | 0.99 / 0.48 / 0.56 | -38.4 / -52.8 |
| GC 1 (diag) LGBM(<=2022) fwd15m P>=0.56 hold=30m day | gross-positive, cost-negative pre-2023 | 6631 | 20.0 | -4.3 | 5.6 | 24.4 | 1.60 / -0.34 / 0.45 | 11.4 / -13.0 |
| GC 2 (diag) LGBM(<=2022) fwd30m P>=0.56 hold=60m day | positive pre-2023 | 3541 | 24.5 | 0.1 | 10.0 | 24.4 | 0.99 / 0.01 / 0.40 | -21.5 / -45.9 |
| GC 3 (diag) LGBM(<=2022) fwd30m P>=0.54 hold=60m day | gross-positive, cost-negative pre-2023 | 10195 | 19.1 | -5.2 | 4.6 | 24.4 | 1.48 / -0.39 / 0.36 | -7.3 / -31.7 |
| CL 1 (diag) LGBM(<=2022) fwd30m P>=0.56 hold=30m day | positive pre-2023 | 379 | 40.8 | 16.5 | 19.8 | 24.4 | 1.05 / 0.43 / 0.51 | 6.6 / -17.7 |
| CL 2 (diag) LGBM(<=2022) fwd15m P>=0.56 hold=30m day | positive pre-2023 | 809 | 52.9 | 28.5 | 29.9 | 24.4 | 1.50 / 0.83 / 0.87 | 0.8 / -23.6 |
| CL 3 (diag) LGBM(<=2022) fwd30m P>=0.56 hold=60m day | positive pre-2023 | 361 | 81.9 | 57.6 | 60.9 | 24.4 | 1.51 / 1.09 / 1.15 | -17.3 / -41.7 |
| BTC 1 (diag) LGBM(<=2022) fwd30m P>=0.56 hold=60m day | positive pre-2023 | 1069 | 347.0 | 292.6 | 325.3 | 54.4 | 6.52 / 5.61 / 6.18 | -10.6 / -65.0 |
| BTC 2 (diag) LGBM(<=2022) fwd5m P>=0.56 hold=10m day | positive pre-2023 | 2092 | 81.8 | 27.4 | 60.2 | 54.4 | 5.04 / 1.81 / 3.84 | 27.0 / -27.4 |
| BTC 3 (diag) LGBM(<=2022) fwd30m P>=0.54 hold=60m day | positive pre-2023 | 1781 | 217.5 | 163.1 | 195.5 | 54.4 | 6.14 / 4.68 / 5.59 | -46.5 / -100.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); RTY: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_11.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw11/ (`SW11_CO_all_selected_scored.csv`).

DONE SW11
