# REPORT SW24 - pooled-transfer frozen LightGBM (trained on the other seven instruments only) direction models, 15/60/120 min (D12 H1-H3)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 15 selected cells (+15 diagnostic) scored on 5 instruments; best non-diagnostic all-in additive uplift at 20% share +0.21; best pair-window standalone Sharpe +1.26.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Model: as SW11/SW12 hyper-parameters (200 trees, min 1000 per leaf), trained on label days <= 2022-12-31 on 15-min-sampled rows of the OTHER seven instruments among ES NQ RTY YM GC CL ZN BTC; the target is never in its own training set. Frozen. Trade P >= th / <= 1-th at 5-min bar ends, hold H or 2H.
- Instruments: RTY, GC, CL, ZN, BTC. Grid: 36 cells per instrument = 3 horizons x 3 th x 2 hold multiples x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      36 |         32 |         6 |               1.062 |                2 |          6 |            3 |
| CL    |      36 |         33 |         3 |               0.846 |                2 |          3 |            3 |
| GC    |      36 |         33 |         4 |               0.484 |                2 |          4 |            3 |
| RTY   |      36 |         35 |         2 |               0.563 |                2 |          2 |            3 |
| ZN    |      36 |         33 |         0 |              -0.565 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| RTY   |     100 |                    2 |             1.12 |               5 |       0.28 |                       0.429 |            0.647 |           1.176 |     0.51 |       0.482 |                1.345 |
| GC    |     100 |                    4 |             0.8  |               4 |       0.01 |                       0.338 |            0.649 |           1.374 |     0.47 |       0.484 |                1.394 |
| CL    |     100 |                    3 |             0.35 |               2 |       0    |                       0.495 |            0.61  |           1.21  |     0.19 |       0.846 |                1.394 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                    6 |             2.39 |               6 |       0.03 |                       0.809 |            0.727 |           1.356 |     0.31 |       1.062 |                1.841 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTY 1 | POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=60m day | 123 | 2 | 0.48 | 0.43 | -0.18 | -1.03 / 1.26 | 0.04 / -0.68 / -0.16 | -0.14 | -0.03 | 0.84 | -0.31 | 0.00 | 184 | NO |
| RTY 2 | POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m all | 408 | 2 | 0.38 | 0.76 | 0.37 | 0.35 / 0.71 | -0.01 / -0.12 / 0.18 | -0.06 | 0.31 | 0.97 | -0.20 | 0.00 | 660 | NO |
| RTY 3 (diag) | POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m day | 99 | 2 | 0.56 | 0.74 | 0.15 | -0.33 / 0.97 | 0.04 / -0.27 / -0.09 | -0.06 | 0.11 | 0.91 | -0.27 | 0.00 | 149 | diag |
| RTY 4 (diag) | POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=60m all | 497 | 1 | -0.05 | 0.38 | -0.40 | -0.81 / 0.57 | -0.07 / -0.80 / -0.10 | -0.29 | 0.03 | 0.91 | -0.41 | 0.00 | 801 | diag |
| RTY 5 (diag) | POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | 561 | 0 | -0.17 | -0.70 | -0.44 | -0.79 / -0.67 | -0.05 / 0.00 / -0.34 | -0.21 | 0.14 | 1.00 | -0.30 | 0.00 | 882 | diag |
| GC 1 | POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | 334 | 2 | 0.48 | -0.46 | 0.23 | 0.14 / 0.41 | 0.07 / 0.19 / -0.33 | -0.09 | 0.04 | 1.00 | -0.29 | 0.50 | 525 | NO |
| GC 2 | POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m day | 853 | 2 | 0.42 | -0.33 | 0.10 | 0.05 / 1.08 | 0.07 / 0.16 / -0.76 | -0.14 | 0.25 | 0.75 | -0.47 | 0.00 | 1378 | NO |
| GC 3 | POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | 2392 | 2 | 0.28 | -1.32 | 0.39 | 0.57 / 1.08 | 0.07 / 1.48 / -0.77 | -0.02 | -0.26 | 0.91 | -0.21 | 0.50 | 3837 | NO |
| GC 4 | POOLED-LGBM(<=2022) fwd60m P>=0.52 hold=120m day | 1682 | 2 | 0.17 | -1.43 | -0.03 | -0.06 / 0.96 | -0.02 / 1.60 / -1.21 | -0.22 | -0.24 | 0.83 | -0.41 | 0.00 | 2710 | NO |
| GC 5 (diag) | POOLED-LGBM(<=2022) fwd60m P>=0.54 hold=120m day | 535 | 1 | 0.42 | -0.60 | -0.61 | -1.26 / 1.42 | 0.07 / 1.12 / -2.13 | -0.39 | 0.14 | 0.38 | -0.72 | 0.00 | 853 | diag |
| GC 6 (diag) | POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=120m day | 1725 | 1 | 0.07 | -1.11 | -0.16 | -0.21 / 1.06 | -0.02 / 0.59 / -1.17 | -0.30 | 0.27 | 0.74 | -0.49 | 0.00 | 2788 | diag |
| GC 7 (diag) | POOLED-LGBM(<=2022) fwd120m P>=0.54 hold=240m day | 356 | 1 | 0.05 | 0.13 | -0.16 | -0.25 / 1.19 | -0.05 / 0.71 / -1.07 | -0.22 | 0.36 | 0.55 | -0.48 | 0.00 | 587 | diag |
| CL 1 | POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m all | 548 | 2 | 0.85 | -0.51 | -0.07 | -1.19 / 0.94 | 0.18 / 0.05 / -0.56 | -0.11 | 0.01 | 0.85 | -0.21 | 0.00 | 896 | NO |
| CL 2 | POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m all | 736 | 2 | 0.46 | -0.71 | -0.35 | -1.41 / 0.56 | 0.11 / -0.09 / -0.73 | -0.26 | 0.05 | 0.94 | -0.34 | 0.00 | 1214 | NO |
| CL 3 | POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | 126 | 2 | 0.18 | -0.14 | 0.39 | 0.72 / 0.76 | 0.05 / -0.19 / 0.19 | 0.01 | 0.17 | 0.99 | -0.14 | 0.00 | 190 | NO |
| CL 4 (diag) | POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m day | 76 | 1 | 0.09 | 0.50 | 0.15 | 0.27 / 1.05 | -0.02 / 0.03 / 0.10 | -0.03 | 0.11 | 0.96 | -0.21 | 0.50 | 114 | diag |
| CL 5 (diag) | POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day | 76 | 2 | 0.08 | -0.04 | 0.78 | 1.47 / 1.11 | 0.01 / -0.15 / 0.77 | 0.14 | 0.10 | 1.00 | -0.07 | 0.50 | 114 | diag |
| CL 6 (diag) | POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | 2437 | 0 | -0.67 | -1.10 | -0.63 | -0.67 / 0.40 | -0.14 / -0.33 / -0.44 | -0.43 | 0.05 | 0.73 | -0.48 | 0.00 | 3916 | diag |
| ZN 1 (diag) | POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day | 66 | 0 | -0.56 | -0.91 | -1.00 | -2.01 / -2.20 | -0.15 / -0.42 / -0.16 | -0.32 | 0.46 | 1.00 | -0.38 | 0.00 | 103 | diag |
| ZN 2 (diag) | POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | 118 | 0 | -1.32 | -1.96 | -1.95 | -3.49 / -5.17 | -0.30 / -0.40 / -0.45 | -0.59 | 0.46 | 1.00 | -0.56 | 0.00 | 193 | diag |
| ZN 3 (diag) | POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=30m day | 223 | 0 | -1.51 | -3.06 | -2.11 | -3.36 / -14.26 | -0.33 / -0.69 / -0.45 | -0.80 | 0.02 | 1.00 | -0.60 | 0.00 | 374 | diag |
| BTC 1 | POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | 246 | 2 | 1.06 | -1.52 | 1.26 | 1.54 / 0.39 | 0.18 / 0.02 / 0.35 | 0.15 | -0.03 | 1.00 | 0.02 | 0.50 | 385 | NO |
| BTC 2 | POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=30m all | 792 | 2 | 0.99 | -1.98 | 0.85 | 0.60 / 0.53 | 0.17 / -0.20 / 0.05 | 0.00 | 0.36 | 1.00 | -0.08 | 0.50 | 1326 | NO |
| BTC 3 | POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=30m day | 228 | 2 | 0.93 | -1.18 | 0.92 | 0.93 / 0.81 | 0.13 / 0.00 / 0.12 | 0.08 | 0.13 | 1.00 | -0.05 | 0.50 | 355 | NO |
| BTC 4 | POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m all | 871 | 2 | 0.80 | -2.50 | 0.89 | 1.09 / 0.28 | 0.15 / -0.28 / 0.27 | -0.01 | 0.20 | 1.00 | -0.05 | 0.50 | 1458 | NO |
| BTC 5 | POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | 2008 | 2 | 0.54 | -1.11 | -0.65 | -2.62 / 1.11 | 0.05 / -0.84 / -0.38 | -0.24 | 0.39 | 0.41 | -0.37 | 0.00 | 3187 | NO |
| BTC 6 | POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m all | 232 | 2 | 0.53 | -0.35 | 0.01 | -1.11 / 1.45 | 0.04 / -0.60 / 0.09 | -0.07 | 0.21 | 0.60 | -0.23 | 0.00 | 390 | NO |
| BTC 7 (diag) | POOLED-LGBM(<=2022) fwd60m P>=0.52 hold=120m day | 1455 | 1 | 0.10 | -1.53 | -0.18 | -0.43 / 0.93 | -0.02 / -0.18 / -0.10 | -0.13 | 0.13 | 0.64 | -0.24 | 0.00 | 2256 | diag |
| BTC 8 (diag) | POOLED-LGBM(<=2022) fwd15m P>=0.54 hold=30m day | 1645 | 1 | 0.04 | -2.52 | -0.15 | -0.39 / 0.37 | -0.02 / -0.50 / 0.07 | -0.19 | 0.41 | 0.92 | -0.23 | 0.00 | 2563 | diag |
| BTC 9 (diag) | POOLED-LGBM(<=2022) fwd120m P>=0.54 hold=240m all | 956 | 1 | 0.01 | -0.92 | -0.34 | -0.98 / 1.27 | -0.04 / -0.63 / 0.12 | -0.14 | 0.44 | 0.51 | -0.27 | 0.00 | 1548 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 15 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 9 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 13 |
| worst-decile corr <= +0.30 | 22 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | clean | 1.06 | 1.62 | -149557 | -106517 | 665188 | -229768 | 1.44 | 30.5 | 1.64 | -89618 | 232183 | -113525 |
| BTC POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | H1 | 0.83 | 1.62 | -157600 | -138614 | 380555 | -206477 | 0.89 | 42.9 | 2.85 | -73928 | 187939 | -78348 |
| BTC POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | H2 | 3.36 | 10.13 | -45478 | -37415 | 79760 | -47058 | 8.74 | 33.3 | 2.84 | -80968 | 226837 | -86827 |
| BTC POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | all | 1.26 | 2.17 | -148240 | -105747 | 665188 | -229768 | 3.00 | 33.3 | 2.11 | -86758 | 232183 | -113525 |
| CL POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | clean | 0.16 | 0.20 | -156015 | -117334 | 746729 | -423666 | 0.20 | 24.8 | 1.51 | -91603 | 293540 | -103224 |
| CL POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | H1 | -1.54 | -1.88 | -73827 | -58222 | 195220 | -92640 | -0.82 | 39.3 | 2.64 | -78676 | 153714 | -81240 |
| CL POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | H2 | 1.36 | 2.53 | -156078 | -126109 | 455054 | -203767 | 1.34 | 27.8 | 2.67 | -101466 | 222004 | -120407 |
| CL POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | all | 0.39 | 0.55 | -151169 | -116757 | 761898 | -423666 | 0.79 | 28.0 | 1.95 | -92665 | 293540 | -120407 |
| GC POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | clean | 0.21 | 0.28 | -156713 | -115667 | 576357 | -299354 | 0.34 | 51.4 | 1.53 | -86401 | 291669 | -90349 |
| GC POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | H1 | 2.75 | 6.94 | -239706 | -186227 | 652714 | -312593 | 2.90 | 39.3 | 4.31 | -90873 | 179739 | -140806 |
| GC POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | H2 | -1.64 | -2.10 | -284698 | -243752 | 1561892 | -320737 | -0.69 | 72.2 | 1.71 | -110210 | 278478 | -126879 |
| GC POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | all | 0.39 | 0.64 | -228885 | -176903 | 1561892 | -320737 | 0.64 | 53.6 | 1.99 | -99013 | 291669 | -140806 |
| RTY POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m all | clean | 0.38 | 0.67 | -112178 | -89831 | 613318 | -169948 | 0.56 | 50.5 | 1.45 | -86773 | 284309 | -92747 |
| RTY POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m all | H1 | -0.95 | -1.05 | -237904 | -200797 | 610382 | -344802 | -0.50 | 42.9 | 2.71 | -74787 | 194804 | -76063 |
| RTY POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m all | H2 | 1.53 | 2.05 | -175685 | -107324 | 431054 | -308317 | 1.27 | 30.6 | 2.66 | -103621 | 260463 | -121868 |
| RTY POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m all | all | 0.37 | 0.52 | -167912 | -117683 | 613318 | -344802 | 0.96 | 45.2 | 1.89 | -89806 | 284309 | -121868 |
| ZN POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day (diag) | clean | -0.56 | -0.79 | -152105 | -124647 | 960552 | -197661 | -0.53 | 24.8 | 1.31 | -85729 | 345775 | -111861 |
| ZN POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day (diag) | H1 | -3.73 | -3.36 | -133540 | -105338 | 537588 | -170418 | -1.00 | 46.4 | 2.41 | -77610 | 161500 | -78287 |
| ZN POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day (diag) | H2 | -1.07 | -1.49 | -123298 | -98351 | 572801 | -141258 | -0.48 | 36.1 | 2.33 | -81089 | 235890 | -82524 |
| ZN POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day (diag) | all | -1.00 | -1.34 | -148220 | -120455 | 2000815 | -197661 | -0.66 | 31.0 | 1.69 | -83871 | 345775 | -111861 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| RTY POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m all | -23.6 | -63.1 | 5.3 | 10.6 | 9.8 / 11.8 | 27.2 / 30.1 | NO |
| GC POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | -19.0 | -80.0 | -11.2 | 7.3 | 9.7 / 13.7 | -89.8 / -13.7 | NO |
| CL POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | -23.5 | -41.6 | -0.8 | 22.5 | -13.7 / 1.0 | 24.3 / 27.9 | NO |
| ZN POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day (diag) | -44.5 | -24.0 | 17.3 | -5.2 | -24.9 / 13.4 | 30.0 / 30.0 | NO |
| BTC POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | -8.2 | -31.6 | 12.1 | 23.7 | -32.7 / 6.3 | 23.1 / 25.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| RTY 1 POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=60m day | positive pre-2023 | 301 | 48.8 | 34.4 | 36.7 | 14.4 | 0.60 / 0.43 / 0.46 | 49.5 / 35.2 |
| RTY 2 POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m all | positive pre-2023 | 1172 | 36.2 | 21.9 | 24.3 | 14.4 | 1.26 / 0.76 / 0.85 | 27.9 / 13.6 |
| RTY 3 (diag) POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m day | positive pre-2023 | 255 | 92.9 | 78.5 | 80.8 | 14.4 | 0.87 / 0.74 / 0.76 | 75.9 / 61.5 |
| RTY 4 (diag) POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=60m all | positive pre-2023 | 1348 | 22.1 | 7.8 | 10.2 | 14.4 | 1.06 / 0.38 / 0.49 | 13.8 / -0.6 |
| RTY 5 (diag) POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | gross-positive, cost-negative pre-2023 | 1571 | 5.1 | -9.3 | -7.1 | 14.4 | 0.38 / -0.70 / -0.54 | 11.0 / -3.3 |
| GC 1 POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | gross-positive, cost-negative pre-2023 | 1951 | 14.5 | -9.8 | -0.1 | 24.4 | 0.69 / -0.46 / -0.00 | 40.1 / 15.8 |
| GC 2 POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m day | gross-positive, cost-negative pre-2023 | 4497 | 13.2 | -11.2 | -1.4 | 24.4 | 0.37 / -0.33 / -0.05 | 36.5 / 12.1 |
| GC 3 POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | gross-positive, cost-negative pre-2023 | 12424 | 0.7 | -23.7 | -13.9 | 24.4 | 0.04 / -1.32 / -0.78 | 31.4 / 7.0 |
| GC 4 POOLED-LGBM(<=2022) fwd60m P>=0.52 hold=120m day | negative pre-2023 | 8835 | -1.5 | -25.9 | -16.1 | 24.4 | -0.09 / -1.43 / -0.89 | 25.0 / 0.7 |
| GC 5 (diag) POOLED-LGBM(<=2022) fwd60m P>=0.54 hold=120m day | gross-positive, cost-negative pre-2023 | 2756 | 3.8 | -20.6 | -10.8 | 24.4 | 0.12 / -0.60 / -0.31 | 41.6 / 17.3 |
| GC 6 (diag) POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=120m day | gross-positive, cost-negative pre-2023 | 9055 | 4.2 | -20.1 | -10.4 | 24.4 | 0.23 / -1.11 / -0.57 | 21.1 / -3.2 |
| GC 7 (diag) POOLED-LGBM(<=2022) fwd120m P>=0.54 hold=240m day | positive pre-2023 | 1792 | 31.5 | 7.1 | 16.8 | 24.4 | 0.55 / 0.13 / 0.30 | 17.8 / -6.6 |
| CL 1 POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m all | gross-positive, cost-negative pre-2023 | 2771 | 7.7 | -16.7 | -14.0 | 24.4 | 0.24 / -0.51 / -0.43 | 58.4 / 34.1 |
| CL 2 POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m all | gross-positive, cost-negative pre-2023 | 3653 | 7.1 | -17.2 | -14.5 | 24.4 | 0.29 / -0.71 / -0.61 | 36.2 / 11.8 |
| CL 3 POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | gross-positive, cost-negative pre-2023 | 614 | 11.8 | -12.6 | -9.2 | 24.4 | 0.13 / -0.14 / -0.10 | 37.8 / 13.4 |
| CL 4 (diag) POOLED-LGBM(<=2022) fwd60m P>=0.56 hold=120m day | positive pre-2023 | 409 | 71.5 | 47.1 | 50.5 | 24.4 | 0.76 / 0.50 / 0.54 | 27.0 / 2.6 |
| CL 5 (diag) POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day | gross-positive, cost-negative pre-2023 | 405 | 19.6 | -4.8 | -1.1 | 24.4 | 0.15 / -0.04 / -0.01 | 25.5 / 1.2 |
| CL 6 (diag) POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | gross-positive, cost-negative pre-2023 | 12569 | 4.3 | -20.0 | -17.4 | 24.4 | 0.23 / -1.10 / -0.96 | 11.2 / -13.2 |
| ZN 1 (diag) POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m day | negative pre-2023 | 272 | -13.9 | -49.5 | -54.6 | 35.6 | -0.26 / -0.91 / -1.00 | 7.8 / -27.8 |
| ZN 2 (diag) POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=120m day | negative pre-2023 | 537 | -11.5 | -47.1 | -52.3 | 35.6 | -0.51 / -1.96 / -2.14 | 2.6 / -33.0 |
| ZN 3 (diag) POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=30m day | gross-positive, cost-negative pre-2023 | 1257 | 2.8 | -32.8 | -37.9 | 35.6 | 0.28 / -3.06 / -3.49 | 13.0 / -22.6 |
| BTC 1 POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day | negative pre-2023 | 165 | -84.4 | -138.8 | -107.3 | 54.4 | -0.94 / -1.52 / -1.19 | 222.9 / 168.5 |
| BTC 2 POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=30m all | negative pre-2023 | 431 | -65.4 | -119.7 | -87.3 | 54.4 | -1.09 / -1.98 / -1.45 | 155.2 / 100.9 |
| BTC 3 POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=30m day | negative pre-2023 | 155 | -79.0 | -133.4 | -101.9 | 54.4 | -0.71 / -1.18 / -0.91 | 317.7 / 263.3 |
| BTC 4 POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m all | negative pre-2023 | 473 | -84.6 | -139.0 | -106.5 | 54.4 | -1.58 / -2.50 / -1.97 | 109.1 / 54.7 |
| BTC 5 POOLED-LGBM(<=2022) fwd120m P>=0.52 hold=240m all | negative pre-2023 | 1427 | -18.5 | -72.9 | -40.2 | 54.4 | -0.28 / -1.11 / -0.61 | 127.5 / 73.1 |
| BTC 6 POOLED-LGBM(<=2022) fwd120m P>=0.56 hold=240m all | negative pre-2023 | 78 | -61.9 | -116.2 | -84.0 | 54.4 | -0.19 / -0.35 / -0.26 | 290.7 / 236.4 |
| BTC 7 (diag) POOLED-LGBM(<=2022) fwd60m P>=0.52 hold=120m day | negative pre-2023 | 1058 | -39.9 | -94.2 | -61.8 | 54.4 | -0.64 / -1.53 / -0.99 | 51.7 / -2.7 |
| BTC 8 (diag) POOLED-LGBM(<=2022) fwd15m P>=0.54 hold=30m day | negative pre-2023 | 1112 | -32.5 | -86.9 | -54.5 | 54.4 | -0.97 / -2.52 / -1.58 | 52.6 / -1.8 |
| BTC 9 (diag) POOLED-LGBM(<=2022) fwd120m P>=0.54 hold=240m all | negative pre-2023 | 604 | -50.0 | -104.4 | -71.9 | 54.4 | -0.44 / -0.92 / -0.63 | 58.3 / 4.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 6 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.03, p(top) = 0.31); CL: 3 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.00, p(top) = 0.19); GC: 4 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 0.01, p(top) = 0.47); RTY: 2 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 0.28, p(top) = 0.51); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 15 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.21 (BTC POOLED-LGBM(<=2022) fwd15m P>=0.56 hold=15m day); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 7, 'gross-positive, cost-negative pre-2023': 6, 'positive pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_24.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw24/ (`SW24_CO_all_selected_scored.csv`).

DONE SW24
