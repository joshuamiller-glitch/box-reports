# REPORT SW35 - weekly-horizon POOLED-TRANSFER frozen LightGBM (trained on the other seven instruments only) (D12 H6 M1-M3)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 3 selected cells (+0 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.23; best pair-window standalone Sharpe +1.55.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- As SW34 but the model is trained on the OTHER seven of ES NQ RTY YM GC CL ZN BTC (label days <= 2022-12-31); the target instrument is never in its own training set. MINTR 60, small-sample flag as SW34.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 18 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV); multi-day holds carry overnight and weekend gap risk (no stop). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      18 |         13 |        11 |               1.408 |                2 |          2 |            0 |
| CL    |      18 |         13 |         2 |               0.737 |                2 |          0 |            0 |
| ES    |      18 |         13 |        11 |               1.113 |                2 |          0 |            0 |
| GC    |      18 |         13 |        12 |               1.831 |                2 |          0 |            0 |
| NQ    |      18 |         13 |         9 |               1.232 |                2 |          0 |            0 |
| RTY   |      18 |         13 |         7 |               0.509 |                2 |          0 |            0 |
| YM    |      18 |         13 |         5 |               0.767 |                2 |          0 |            0 |
| ZN    |      18 |         13 |         4 |               1.804 |                2 |          1 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   11 |            2.585 |               8 |      0     |                       0.594 |            0.783 |           1.325 |    0.685 |       0.798 |                1.751 |
| NQ    |     200 |                    9 |            2.79  |               7 |      0     |                       0.629 |            0.791 |           1.281 |    0.655 |       1.232 |                1.861 |
| RTY   |     200 |                    7 |            2.85  |               8 |      0.015 |                       0.313 |            0.833 |           1.329 |    0.95  |       0.509 |                1.888 |
| YM    |     200 |                    5 |            2.915 |               7 |      0.17  |                       0.51  |            0.773 |           1.252 |    0.775 |       0.767 |                1.772 |
| GC    |     200 |                   12 |            2.745 |               7 |      0     |                       0.902 |            0.755 |           1.243 |    0.295 |       1.667 |                1.809 |
| CL    |     200 |                    2 |            2.515 |               7 |      0.735 |                       0.6   |            0.783 |           1.376 |    0.7   |       0.737 |                1.779 |
| ZN    |     200 |                    4 |            1.43  |               5 |      0.045 |                       1.265 |            0.727 |           1.335 |    0.055 |       1.804 |                1.462 |
| BTC   |     200 |                   11 |            2.64  |               6 |      0     |                       0.92  |            0.839 |           1.319 |    0.335 |       1.408 |                1.793 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZN 1 | pooled LGBM(<=2022) 2d P>=0.52 entries=week | 67 | 2 | 1.80 | -0.61 | 1.55 | 0.93 / 0.47 | 0.33 / 0.15 / 0.03 | 0.18 | -0.23 | 1.00 | 0.08 | 0.50 | 99 S | NO |
| BTC 1 | pooled LGBM(<=2022) 2d P>=0.55 entries=day | 75 | 2 | 1.41 | -0.07 | 1.24 | 0.89 / 1.51 | 0.24 / 0.23 / 0.04 | 0.18 | 0.00 | 0.97 | -0.00 | 0.50 | 103 | NO |
| BTC 2 | pooled LGBM(<=2022) 2d P>=0.52 entries=day | 154 | 2 | 1.19 | 0.26 | 0.58 | -0.26 / 1.50 | 0.21 / -0.67 / 0.18 | 0.08 | 0.31 | 0.80 | -0.11 | 0.00 | 227 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 3 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 3 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 2 |
| worst-decile corr <= +0.30 | 2 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 1 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC pooled LGBM(<=2022) 2d P>=0.55 entries=day | clean | 1.40 | 2.14 | -129112 | -91250 | 440242 | -353101 | 2.89 | 20.0 | 1.70 | -86738 | 281013 | -122785 |
| BTC pooled LGBM(<=2022) 2d P>=0.55 entries=day | H1 | 1.23 | 3.19 | -49581 | -35563 | 106689 | -65006 | 1.62 | 10.7 | 3.06 | -63000 | 151713 | -76514 |
| BTC pooled LGBM(<=2022) 2d P>=0.55 entries=day | H2 | 0.61 | 0.85 | -92924 | -72601 | 169349 | -94801 | 0.64 | 16.7 | 2.52 | -85574 | 203127 | -88623 |
| BTC pooled LGBM(<=2022) 2d P>=0.55 entries=day | all | 1.24 | 1.91 | -113947 | -81960 | 440242 | -353101 | 3.52 | 17.9 | 2.08 | -85414 | 281013 | -122785 |
| ZN pooled LGBM(<=2022) 2d P>=0.52 entries=week | clean | 1.84 | 4.06 | -100162 | -78510 | 197588 | -129578 | 8.43 | 23.8 | 1.79 | -84980 | 268600 | -97401 |
| ZN pooled LGBM(<=2022) 2d P>=0.52 entries=week | H1 | 2.01 | 4.56 | -26149 | -23935 | 55256 | -30894 | 2.82 | 21.4 | 2.98 | -74057 | 141571 | -76932 |
| ZN pooled LGBM(<=2022) 2d P>=0.52 entries=week | H2 | 0.51 | 0.78 | -81185 | -69324 | 191586 | -87827 | 0.49 | 19.4 | 2.51 | -84767 | 227020 | -87010 |
| ZN pooled LGBM(<=2022) 2d P>=0.52 entries=week | all | 1.55 | 3.27 | -92255 | -71193 | 197588 | -129578 | 9.69 | 22.6 | 2.13 | -84063 | 268600 | -97401 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ZN pooled LGBM(<=2022) 2d P>=0.52 entries=week | -9.1 | -1.9 | 19.9 | 36.2 | -2.7 / 17.3 | 31.2 / 36.9 | NO |
| BTC pooled LGBM(<=2022) 2d P>=0.55 entries=day | -13.0 | -72.6 | 14.3 | 9.6 | -74.0 / 9.4 | 32.0 / 46.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ZN 1 pooled LGBM(<=2022) 2d P>=0.52 entries=week | negative pre-2023 | 397 | -16.0 | -51.6 | -56.8 | 35.6 | -0.19 / -0.61 / -0.67 | 240.2 / 204.6 |
| BTC 1 pooled LGBM(<=2022) 2d P>=0.55 entries=day | negative pre-2023 | 64 | -14.1 | -68.4 | -33.5 | 54.4 | -0.01 / -0.07 / -0.03 | 3663.7 / 3609.3 |
| BTC 2 pooled LGBM(<=2022) 2d P>=0.52 entries=day | positive pre-2023 | 105 | 225.0 | 170.6 | 204.8 | 54.4 | 0.34 / 0.26 / 0.31 | 1746.9 / 1692.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 11 cells pass the clean rule against a replicate mean of 2.6 (p(count) = 0.00, p(top) = 0.34); CL: 2 cells pass the clean rule against a replicate mean of 2.5 (p(count) = 0.73, p(top) = 0.70); ES: 11 cells pass the clean rule against a replicate mean of 2.6 (p(count) = 0.00, p(top) = 0.69); GC: 12 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.00, p(top) = 0.29); NQ: 9 cells pass the clean rule against a replicate mean of 2.8 (p(count) = 0.00, p(top) = 0.66); RTY: 7 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 0.01, p(top) = 0.95); YM: 5 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 0.17, p(top) = 0.78); ZN: 4 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.04, p(top) = 0.06).
- Of 3 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.23 (ZN pooled LGBM(<=2022) 2d P>=0.52 entries=week); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 2; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 2, 'positive pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_35.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw35/ (`SW35_CO_all_selected_scored.csv`).

DONE SW35
