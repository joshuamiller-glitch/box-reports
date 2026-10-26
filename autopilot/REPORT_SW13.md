# REPORT SW13 - frozen daily LightGBM on RTH-open features, open-to-close direction (D12 H4)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 18 selected cells (+18 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.30; best pair-window standalone Sharpe +1.15.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Model: LightGBM (100 trees, 4 leaves, min 40 per leaf), frozen, trained on daily rows (label days <= 2022; BTC <= 2023-07-31) with the SW11 features at RTH open + d; target sign(16:55 open - entry open). Trade P >= th long / <= 1-th short, hold to flatten or 240 min.
- Instruments: ES, NQ, RTY, YM, GC, ZN, BTC. Grid: 16 cells per instrument = 2 delays x 4 th x 2 holds.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      16 |          0 |         0 |              -9     |                0 |          0 |            0 |
| ES    |      16 |         16 |         4 |               0.827 |                2 |          4 |            3 |
| GC    |      16 |         12 |         1 |               0.732 |                2 |          1 |            3 |
| NQ    |      16 |         16 |         5 |               0.984 |                2 |          5 |            3 |
| RTY   |      16 |         16 |         5 |               1.68  |                2 |          5 |            3 |
| YM    |      16 |         16 |         3 |               0.714 |                2 |          3 |            3 |
| ZN    |      16 |         12 |         0 |              -0.609 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    4 |             2.7  |               6 |       0.27 |                       0.524 |            0.731 |           1.221 |     0.71 |       0.827 |                1.71  |
| NQ    |     100 |                    5 |             3.7  |               8 |       0.33 |                       0.623 |            0.782 |           1.087 |     0.72 |       0.984 |                1.761 |
| RTY   |     100 |                    5 |             2.89 |               7 |       0.15 |                       1.008 |            0.726 |           1.152 |     0.16 |       1.68  |                1.707 |
| YM    |     100 |                    3 |             2.95 |               6 |       0.59 |                       0.522 |            0.733 |           1.089 |     0.77 |       0.714 |                1.653 |
| GC    |     100 |                    1 |             1.76 |               4 |       0.88 |                       0.732 |            0.674 |           1.226 |     0.31 |       0.732 |                1.564 |
| ZN    |     100 |                    0 |             0.16 |               2 |       1    |                     nan     |            0.493 |           1.063 |   nan    |     nan     |                1.291 |
| BTC   |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | 141 | 2 | 0.83 | 2.42 | 0.31 | -0.36 / 1.09 | 0.16 / -0.03 / -0.26 | 0.02 | 0.07 | 0.77 | -0.16 | 0.50 | 232 | NO |
| ES 2 | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | 198 | 2 | 0.71 | 1.45 | 0.27 | -0.30 / 1.07 | 0.06 / -0.21 / -0.14 | -0.06 | -0.26 | 0.87 | -0.24 | 0.00 | 308 | NO |
| ES 3 | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=flat | 212 | 2 | 0.44 | 2.04 | 0.26 | -0.01 / 1.22 | 0.03 / -0.07 / -0.14 | -0.05 | 0.24 | 0.76 | -0.21 | 0.00 | 325 | NO |
| ES 4 | daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=flat | 426 | 2 | 0.12 | 1.79 | 0.18 | 0.18 / 1.52 | -0.01 / 0.16 / -0.07 | -0.03 | 0.48 | 0.76 | -0.17 | 0.00 | 674 | NO |
| ES 5 (diag) | daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=240m | 130 | 1 | 0.38 | 1.68 | -0.01 | -0.47 / 0.85 | 0.08 / -0.19 / -0.30 | -0.07 | -0.04 | 0.67 | -0.27 | 0.00 | 215 | diag |
| ES 6 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=240m | 251 | 1 | -0.00 | 1.10 | -0.28 | -0.86 / 1.18 | -0.02 / -0.13 / -0.12 | -0.09 | -0.46 | 0.44 | -0.25 | 0.00 | 401 | diag |
| ES 7 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.54 hold=240m | 323 | 1 | -0.01 | 1.14 | -0.01 | -0.01 / 1.51 | -0.02 / -0.05 / 0.08 | -0.05 | -0.31 | 0.73 | -0.20 | 0.00 | 526 | diag |
| NQ 1 | daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=flat | 452 | 2 | 0.98 | 1.93 | 0.55 | 0.03 / 1.49 | 0.14 / -0.41 / 0.14 | 0.05 | -0.78 | 0.83 | -0.14 | 0.50 | 718 | NO |
| NQ 2 | daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=240m | 433 | 2 | 0.75 | 1.19 | 0.32 | -0.16 / 1.32 | 0.08 / -0.34 / 0.05 | -0.00 | -0.72 | 0.82 | -0.21 | 0.50 | 691 | NO |
| NQ 3 | daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=flat | 295 | 2 | 0.65 | 2.08 | 0.56 | 0.47 / 1.54 | 0.11 / -0.36 / 0.24 | 0.07 | -0.59 | 0.87 | -0.12 | 1.00 | 469 | NO |
| NQ 4 | daily LGBM(<=2022) RTHopen+30m P>=0.54 hold=flat | 393 | 2 | 0.49 | 2.24 | 0.51 | 0.53 / 1.19 | 0.08 / -0.26 / 0.20 | 0.05 | -0.56 | 0.84 | -0.12 | 0.50 | 606 | NO |
| NQ 5 | daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | 412 | 2 | 0.24 | 1.61 | 0.76 | 1.35 / 1.39 | 0.01 / -0.05 / 0.59 | 0.11 | 0.09 | 0.93 | -0.11 | 0.50 | 659 | NO |
| NQ 6 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=flat | 203 | 1 | 0.39 | 2.01 | 0.46 | 0.55 / 1.26 | 0.07 / -0.23 / 0.24 | 0.06 | -0.47 | 0.86 | -0.13 | 0.50 | 322 | diag |
| NQ 7 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=240m | 280 | 1 | 0.38 | 1.66 | 0.50 | 0.69 / 1.18 | 0.03 / -0.29 / 0.27 | 0.04 | -0.62 | 0.85 | -0.16 | 0.75 | 450 | diag |
| NQ 8 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.54 hold=240m | 377 | 1 | 0.34 | 1.63 | 0.48 | 0.71 / 1.32 | 0.02 / -0.12 / 0.18 | 0.03 | -0.59 | 0.88 | -0.15 | 0.50 | 582 | diag |
| RTY 1 | daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=240m | 374 | 2 | 1.68 | 2.71 | 0.33 | -1.00 / 1.11 | 0.22 / 0.11 / -0.56 | -0.02 | -0.49 | 0.88 | -0.22 | 0.25 | 607 | NO |
| RTY 2 | daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=flat | 388 | 2 | 1.37 | 3.40 | 0.35 | -0.93 / 1.72 | 0.17 / -0.19 / -0.30 | -0.02 | -0.45 | 0.82 | -0.19 | 0.50 | 629 | NO |
| RTY 3 | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=flat | 108 | 2 | 0.86 | 3.26 | 0.42 | -0.19 / 1.19 | 0.13 / -0.31 / 0.02 | 0.03 | -0.44 | 0.88 | -0.14 | 0.50 | 177 | NO |
| RTY 4 | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | 102 | 2 | 0.76 | 2.36 | 0.50 | 0.15 / 1.13 | 0.10 / 0.17 / -0.08 | 0.05 | -0.60 | 0.89 | -0.12 | 0.25 | 169 | NO |
| RTY 5 | daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | 166 | 2 | 0.38 | 3.76 | 0.13 | -0.19 / 1.68 | 0.06 / 0.23 / -0.19 | 0.01 | -0.09 | 0.60 | -0.19 | 0.50 | 268 | NO |
| RTY 6 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=240m | 171 | 1 | 1.44 | 2.54 | 0.52 | -0.59 / 1.32 | 0.22 / 0.38 / -0.54 | 0.04 | -0.60 | 0.88 | -0.16 | 0.00 | 288 | diag |
| RTY 7 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.54 hold=240m | 262 | 1 | 1.33 | 3.04 | 0.29 | -0.87 / 1.37 | 0.18 / 0.44 / -0.64 | -0.02 | -0.40 | 0.90 | -0.22 | 0.25 | 437 | diag |
| RTY 8 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=flat | 178 | 1 | 1.29 | 3.31 | 0.51 | -0.55 / 1.13 | 0.19 / 0.07 / -0.34 | 0.03 | -0.43 | 0.88 | -0.15 | 0.00 | 300 | diag |
| YM 1 | daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | 413 | 2 | 0.71 | 1.20 | 0.13 | -0.67 / 0.98 | 0.09 / 0.59 / -0.48 | -0.01 | -0.12 | 0.71 | -0.18 | 0.25 | 657 | NO |
| YM 2 | daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=240m | 328 | 2 | 0.55 | 1.48 | 0.19 | -0.26 / 1.27 | 0.08 / 0.55 / -0.31 | 0.02 | -0.06 | 0.74 | -0.16 | 0.25 | 517 | NO |
| YM 3 | daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=240m | 182 | 2 | 0.30 | 1.97 | 0.15 | 0.04 / 1.40 | 0.01 / 0.54 / -0.18 | -0.00 | -0.14 | 0.67 | -0.21 | 0.25 | 285 | NO |
| YM 4 (diag) | daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=flat | 430 | 1 | 0.27 | 2.07 | 0.02 | -0.40 / 1.39 | -0.00 / 0.38 / -0.24 | -0.03 | 0.23 | 0.47 | -0.18 | 0.00 | 683 | diag |
| YM 5 (diag) | daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=flat | 339 | 1 | 0.09 | 2.46 | -0.12 | -0.34 / 1.26 | -0.03 / 0.42 / -0.28 | -0.05 | 0.26 | 0.47 | -0.22 | 0.00 | 535 | diag |
| YM 6 (diag) | daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | 190 | 1 | 0.07 | 2.98 | 0.03 | 0.02 / 1.34 | -0.04 / 0.38 / -0.18 | -0.04 | 0.26 | 0.56 | -0.22 | 0.00 | 298 | diag |
| GC 1 | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | 105 | 2 | 0.73 | 1.72 | 0.74 | 0.98 / 1.49 | 0.17 / 0.97 / 0.20 | 0.27 | -0.11 | 0.95 | -0.00 | 0.25 | 166 | LEAD |
| GC 2 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=flat | 105 | 1 | 0.43 | 2.18 | 0.47 | 0.68 / 1.32 | 0.11 / 1.29 / -0.36 | 0.15 | 0.05 | 0.83 | -0.18 | 0.00 | 166 | diag |
| GC 3 (diag) | daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=240m | 42 | 2 | 0.36 | 2.06 | 1.15 | 1.83 / 1.73 | -0.01 / 0.37 / 0.66 | 0.27 | 0.05 | 0.98 | -0.07 | 0.75 | 64 S | diag |
| GC 4 (diag) | daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=flat | 190 | 1 | 0.23 | 3.09 | 1.06 | 1.76 / 1.48 | -0.05 / 0.68 / 0.42 | 0.18 | -0.19 | 0.98 | -0.09 | 0.50 | 289 | diag |
| ZN 1 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=flat | 365 | 0 | -0.61 | 1.33 | -0.82 | -1.44 / -0.08 | -0.13 / -0.25 / -0.27 | -0.44 | -0.18 | 0.74 | -0.34 | 0.00 | 579 | diag |
| ZN 2 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=flat | 150 | 0 | -0.79 | 1.98 | -0.62 | -0.26 / 0.20 | -0.18 / -0.17 / -0.11 | -0.33 | -0.11 | 0.74 | -0.34 | 0.00 | 232 | diag |
| ZN 3 (diag) | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | 88 | 0 | -0.84 | 0.97 | -0.47 | 0.46 / -0.20 | -0.18 / -0.10 / 0.09 | -0.26 | -0.25 | 0.93 | -0.29 | 0.00 | 133 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 18 |
| diagnostic cells read | 18 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 0 |
| all-in uplift @20% > 0 (all scored) | 24 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 3 |
| worst-decile corr <= +0.30 | 35 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 1 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | clean | 0.85 | 1.43 | -126798 | -101291 | 396340 | -190799 | 1.94 | 34.3 | 1.62 | -78834 | 254623 | -81874 |
| ES daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | H1 | 0.13 | 0.20 | -162056 | -128081 | 456070 | -230630 | 0.09 | 42.9 | 2.79 | -85543 | 175977 | -90314 |
| ES daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | H2 | -0.71 | -0.93 | -215809 | -156356 | 464558 | -294704 | -0.65 | 47.2 | 2.03 | -82982 | 265000 | -84928 |
| ES daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | all | 0.31 | 0.47 | -158381 | -123380 | 711019 | -294704 | 0.71 | 38.7 | 1.89 | -81461 | 265000 | -90314 |
| GC daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | clean | 0.55 | 0.84 | -149544 | -115532 | 564954 | -191236 | 0.91 | 30.5 | 1.63 | -82823 | 301116 | -89962 |
| GC daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | H1 | 1.47 | 3.47 | -231103 | -200313 | 513678 | -307240 | 1.87 | 25.0 | 3.79 | -69567 | 140198 | -85003 |
| GC daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | H2 | 0.54 | 0.98 | -251792 | -221982 | 904433 | -259152 | 0.45 | 38.9 | 2.50 | -87363 | 216736 | -87983 |
| GC daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | all | 0.74 | 1.38 | -206368 | -165542 | 1117246 | -307240 | 1.69 | 31.5 | 2.15 | -84074 | 301116 | -89962 |
| NQ daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | clean | 0.22 | 0.31 | -143370 | -117102 | 679140 | -208678 | 0.30 | 47.6 | 1.47 | -91779 | 288891 | -102916 |
| NQ daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | H1 | -0.73 | -0.98 | -187624 | -179602 | 781179 | -201650 | -0.35 | 42.9 | 2.78 | -71852 | 131526 | -72234 |
| NQ daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | H2 | 2.99 | 6.58 | -168397 | -118568 | 397425 | -177850 | 3.72 | 33.3 | 2.88 | -89464 | 205981 | -95774 |
| NQ daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | all | 0.76 | 1.19 | -168713 | -135904 | 781179 | -208678 | 1.80 | 43.5 | 1.98 | -90220 | 288891 | -102916 |
| RTY daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | clean | 0.75 | 1.14 | -147385 | -112800 | 449128 | -202340 | 1.52 | 29.5 | 1.56 | -89607 | 271749 | -102695 |
| RTY daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | H1 | 0.78 | 1.36 | -126176 | -116961 | 494054 | -151207 | 0.44 | 28.6 | 3.00 | -61970 | 179193 | -64725 |
| RTY daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | H2 | -0.35 | -0.46 | -161667 | -149992 | 444654 | -162788 | -0.28 | 33.3 | 2.21 | -89433 | 208674 | -92314 |
| RTY daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | all | 0.50 | 0.75 | -155757 | -126594 | 717575 | -202340 | 1.08 | 30.4 | 1.92 | -88244 | 271749 | -102695 |
| YM daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=240m | clean | 0.49 | 0.71 | -138863 | -111921 | 311059 | -193036 | 1.43 | 47.6 | 1.54 | -86569 | 263981 | -95398 |
| YM daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=240m | H1 | 1.45 | 2.66 | -109589 | -94421 | 217891 | -134125 | 1.74 | 39.3 | 3.38 | -68445 | 132612 | -69552 |
| YM daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=240m | H2 | -1.60 | -1.98 | -149660 | -126311 | 575793 | -156708 | -0.92 | 61.1 | 1.98 | -91511 | 222530 | -100227 |
| YM daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=240m | all | 0.19 | 0.28 | -140736 | -118997 | 575793 | -193036 | 0.50 | 48.8 | 1.90 | -86838 | 263981 | -100227 |
| ZN daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m (diag) | clean | -0.83 | -1.00 | -179499 | -130120 | 1007281 | -293321 | -0.75 | 33.3 | 1.28 | -92817 | 286819 | -136222 |
| ZN daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m (diag) | H1 | -1.52 | -1.84 | -57862 | -54204 | 209306 | -64677 | -0.72 | 32.1 | 2.73 | -80636 | 143263 | -84339 |
| ZN daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m (diag) | H2 | 1.34 | 2.85 | -72992 | -60230 | 122878 | -77149 | 2.52 | 25.0 | 2.38 | -81737 | 217425 | -83820 |
| ZN daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m (diag) | all | -0.47 | -0.59 | -145715 | -106818 | 1122033 | -293321 | -0.53 | 31.5 | 1.74 | -89413 | 286819 | -136222 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | -24.3 | 11.1 | 17.8 | 8.2 | 16.1 / 21.2 | 7.0 / 14.7 | NO |
| NQ daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | -14.3 | -15.7 | 5.2 | 15.9 | -8.6 / 3.3 | 41.6 / 41.1 | NO |
| RTY daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | -21.3 | -11.9 | 9.4 | 34.5 | -12.7 / 8.4 | 52.2 / 52.7 | NO |
| YM daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=240m | -26.8 | -5.0 | 12.4 | 29.8 | 0.5 / 12.8 | 44.3 / 44.4 | NO |
| GC daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | -9.0 | 11.3 | 15.9 | 5.4 | 10.6 / 18.8 | 15.7 / 18.8 | NO |
| ZN daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m (diag) | -36.6 | -72.4 | 4.5 | 1.4 | -73.8 / -6.1 | 18.4 / 24.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | positive pre-2023 | 902 | 371.8 | 342.4 | 356.7 | 29.4 | 2.61 / 2.42 / 2.51 | 219.1 / 189.8 |
| ES 2 daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | positive pre-2023 | 977 | 159.1 | 129.8 | 144.1 | 29.4 | 1.77 / 1.45 / 1.61 | 128.5 / 99.2 |
| ES 3 daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=flat | positive pre-2023 | 1013 | 258.1 | 228.8 | 243.1 | 29.4 | 2.29 / 2.04 / 2.16 | 102.4 / 73.0 |
| ES 4 daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=flat | positive pre-2023 | 2233 | 201.6 | 172.2 | 186.5 | 29.4 | 2.10 / 1.79 / 1.94 | 65.8 / 36.5 |
| ES 5 (diag) daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=240m | positive pre-2023 | 859 | 217.8 | 188.4 | 202.7 | 29.4 | 1.94 / 1.68 / 1.81 | 101.1 / 71.7 |
| ES 6 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=240m | positive pre-2023 | 1372 | 113.3 | 84.0 | 98.3 | 29.4 | 1.48 / 1.10 / 1.29 | 30.3 / 0.9 |
| ES 7 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.54 hold=240m | positive pre-2023 | 1783 | 108.5 | 79.1 | 93.4 | 29.4 | 1.56 / 1.14 / 1.35 | 29.0 / -0.3 |
| NQ 1 daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=flat | positive pre-2023 | 2328 | 237.8 | 223.4 | 232.0 | 14.4 | 2.05 / 1.93 / 2.00 | 230.9 / 216.5 |
| NQ 2 daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=240m | positive pre-2023 | 2261 | 119.8 | 105.4 | 114.0 | 14.4 | 1.36 / 1.19 / 1.29 | 158.6 / 144.3 |
| NQ 3 daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=flat | positive pre-2023 | 1513 | 312.5 | 298.1 | 306.6 | 14.4 | 2.18 / 2.08 / 2.14 | 197.9 / 183.6 |
| NQ 4 daily LGBM(<=2022) RTHopen+30m P>=0.54 hold=flat | positive pre-2023 | 1952 | 297.4 | 283.0 | 291.6 | 14.4 | 2.35 / 2.24 / 2.31 | 139.6 / 125.2 |
| NQ 5 daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | positive pre-2023 | 2176 | 194.7 | 180.4 | 188.8 | 14.4 | 1.74 / 1.61 / 1.69 | 56.0 / 41.6 |
| NQ 6 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=flat | positive pre-2023 | 1033 | 379.4 | 365.1 | 373.5 | 14.4 | 2.09 / 2.01 / 2.06 | 143.0 / 128.6 |
| NQ 7 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=240m | positive pre-2023 | 1474 | 184.2 | 169.9 | 178.4 | 14.4 | 1.80 / 1.66 / 1.75 | 97.2 / 82.9 |
| NQ 8 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.54 hold=240m | positive pre-2023 | 1892 | 161.1 | 146.7 | 155.3 | 14.4 | 1.79 / 1.63 / 1.73 | 84.1 / 69.7 |
| RTY 1 daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=240m | positive pre-2023 | 1169 | 156.5 | 142.2 | 144.4 | 14.4 | 2.98 / 2.71 / 2.76 | 115.8 / 101.4 |
| RTY 2 daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=flat | positive pre-2023 | 1206 | 234.2 | 219.8 | 222.0 | 14.4 | 3.62 / 3.40 / 3.44 | 119.3 / 104.9 |
| RTY 3 daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=flat | positive pre-2023 | 441 | 329.5 | 315.2 | 317.5 | 14.4 | 3.40 / 3.26 / 3.29 | 123.3 / 108.9 |
| RTY 4 daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | positive pre-2023 | 429 | 208.1 | 193.8 | 196.2 | 14.4 | 2.52 / 2.36 / 2.39 | 104.0 / 89.6 |
| RTY 5 daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | positive pre-2023 | 578 | 399.4 | 385.0 | 387.2 | 14.4 | 3.88 / 3.76 / 3.78 | 61.8 / 47.4 |
| RTY 6 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=240m | positive pre-2023 | 624 | 184.9 | 170.5 | 172.8 | 14.4 | 2.74 / 2.54 / 2.57 | 145.2 / 130.8 |
| RTY 7 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.54 hold=240m | positive pre-2023 | 886 | 185.2 | 170.8 | 173.1 | 14.4 | 3.29 / 3.04 / 3.08 | 114.5 / 100.1 |
| RTY 8 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=flat | positive pre-2023 | 646 | 279.5 | 265.2 | 267.5 | 14.4 | 3.48 / 3.31 / 3.34 | 153.0 / 138.6 |
| YM 1 daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=240m | positive pre-2023 | 2175 | 84.9 | 70.6 | 76.4 | 14.4 | 1.44 / 1.20 / 1.30 | 68.2 / 53.8 |
| YM 2 daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=240m | positive pre-2023 | 1741 | 111.9 | 97.5 | 103.4 | 14.4 | 1.69 / 1.48 / 1.57 | 55.7 / 41.4 |
| YM 3 daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=240m | positive pre-2023 | 929 | 170.4 | 156.0 | 161.9 | 14.4 | 2.15 / 1.97 / 2.05 | 39.8 / 25.4 |
| YM 4 (diag) daily LGBM(<=2022) RTHopen+0m P>=0.52 hold=flat | positive pre-2023 | 2246 | 154.6 | 140.2 | 146.0 | 14.4 | 2.28 / 2.07 / 2.15 | 40.4 / 26.0 |
| YM 5 (diag) daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=flat | positive pre-2023 | 1794 | 205.3 | 191.0 | 196.8 | 14.4 | 2.65 / 2.46 / 2.54 | 15.9 / 1.6 |
| YM 6 (diag) daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=flat | positive pre-2023 | 947 | 298.2 | 283.8 | 289.7 | 14.4 | 3.13 / 2.98 / 3.05 | 20.6 / 6.2 |
| GC 1 daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | positive pre-2023 | 515 | 264.3 | 240.0 | 249.8 | 24.4 | 1.89 / 1.72 / 1.79 | 125.8 / 101.4 |
| GC 2 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=flat | positive pre-2023 | 515 | 387.7 | 363.4 | 373.2 | 24.4 | 2.32 / 2.18 / 2.24 | 76.3 / 51.9 |
| GC 3 (diag) daily LGBM(<=2022) RTHopen+0m P>=0.58 hold=240m | positive pre-2023 | 230 | 486.6 | 462.2 | 472.1 | 24.4 | 2.15 / 2.06 / 2.10 | 112.9 / 88.5 |
| GC 4 (diag) daily LGBM(<=2022) RTHopen+0m P>=0.54 hold=flat | positive pre-2023 | 997 | 375.0 | 350.7 | 360.5 | 24.4 | 3.29 / 3.09 / 3.17 | 79.9 / 55.6 |
| ZN 1 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.52 hold=flat | positive pre-2023 | 1902 | 66.2 | 30.6 | 25.5 | 35.6 | 2.87 / 1.33 / 1.11 | 21.7 / -13.9 |
| ZN 2 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.56 hold=flat | positive pre-2023 | 769 | 99.0 | 63.3 | 58.3 | 35.6 | 3.02 / 1.98 / 1.83 | 8.8 / -26.9 |
| ZN 3 (diag) daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | positive pre-2023 | 448 | 67.3 | 31.7 | 26.6 | 35.6 | 2.01 / 0.97 / 0.82 | 3.4 / -32.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ES: 4 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.27, p(top) = 0.71); GC: 1 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 0.88, p(top) = 0.31); NQ: 5 cells pass the clean rule against a replicate mean of 3.7 (p(count) = 0.33, p(top) = 0.72); RTY: 5 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 0.15, p(top) = 0.16); YM: 3 cells pass the clean rule against a replicate mean of 3.0 (p(count) = 0.59, p(top) = 0.77); ZN: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00).
- Of 18 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.30 (GC daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 2; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell GC daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m: uplift +0.17/+0.97/+0.20, boot lo -0.00, plateau 0.25, 2x-slip +0.27, wd corr -0.11, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 18}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_13.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw13/ (`SW13_CO_all_selected_scored.csv`).

DONE SW13
