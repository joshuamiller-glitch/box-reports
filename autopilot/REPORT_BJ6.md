# REPORT BJ6 - VIX-settlement Wednesday (BJ batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 14 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.14; best pair-window standalone Sharpe +0.99.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. VIX-settlement Wednesday. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      12 |         12 |         4 |               1.241 |                2 |          4 |            3 |
| NQ    |      12 |         12 |         4 |               1.705 |                2 |          4 |            3 |
| RTY   |      12 |         12 |         3 |               0.728 |                2 |          3 |            3 |
| YM    |      12 |         12 |         3 |               0.736 |                2 |          3 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    4 |            2.09  |               6 |      0.13  |                       1.096 |            0.775 |           1.336 |    0.15  |       1.241 |                1.707 |
| NQ    |     200 |                    4 |            2.295 |               6 |      0.165 |                       1.302 |            0.785 |           1.282 |    0.04  |       1.705 |                1.695 |
| RTY   |     200 |                    3 |            2.315 |               7 |      0.44  |                       0.531 |            0.759 |           1.232 |    0.755 |       0.728 |                1.635 |
| YM    |     200 |                    3 |            2.19  |               6 |      0.36  |                       0.724 |            0.784 |           1.325 |    0.475 |       0.736 |                1.754 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | VIX settlement Wednesday offset +1d dir=short hold=rth | 24 | 2 | 1.24 | -0.15 | 0.86 | 0.54 / 1.19 | 0.20 / -0.01 / -0.17 | 0.11 | 0.05 | 0.98 | -0.06 | 0.00 | 38 S | NO |
| ES 2 | VIX settlement Wednesday offset +0d dir=short hold=rth | 24 | 2 | 1.21 | -0.08 | 0.99 | 0.63 / 1.41 | 0.16 / -0.06 / 0.15 | 0.12 | -0.59 | 0.98 | -0.03 | 0.00 | 38 S | NO |
| ES 3 | VIX settlement Wednesday offset -1d dir=short hold=c2c | 23 | 2 | 1.13 | -0.09 | 0.80 | 0.29 / 1.27 | 0.14 / -0.07 / 0.07 | 0.08 | -0.60 | 0.98 | -0.09 | 0.00 | 37 S | NO |
| ES 4 | VIX settlement Wednesday offset +1d dir=short hold=c2c | 23 | 2 | 0.81 | 0.33 | -0.24 | -1.79 / 1.26 | 0.10 / -0.80 / -0.16 | -0.10 | -0.12 | 0.49 | -0.26 | 0.00 | 36 S | NO |
| ES 5 (diag) | VIX settlement Wednesday offset -1d dir=short hold=rth | 24 | 1 | 0.13 | -0.56 | 0.43 | 0.91 / 1.27 | 0.03 / 0.47 / 0.09 | 0.09 | -0.41 | 0.81 | -0.09 | 0.00 | 38 S | diag |
| ES 6 (diag) | VIX settlement Wednesday offset +0d dir=short hold=c2c | 22 | 1 | 0.13 | 0.46 | 0.02 | -0.09 / 1.09 | 0.02 / -0.44 / -0.12 | -0.07 | 0.61 | 0.65 | -0.29 | 0.00 | 36 S | diag |
| ES 7 (diag) | VIX settlement Wednesday offset +0d dir=long hold=c2c | 22 | 1 | -0.22 | -0.60 | -0.10 | 0.03 / 1.60 | -0.09 / 0.21 / -0.14 | -0.09 | -0.61 | 0.34 | -0.32 | 0.00 | 36 S | diag |
| NQ 1 | VIX settlement Wednesday offset +1d dir=short hold=rth | 24 | 2 | 1.70 | -0.14 | 0.92 | 0.34 / 1.22 | 0.29 / -0.07 / -0.32 | 0.13 | 0.26 | 0.99 | -0.05 | 0.00 | 38 S | NO |
| NQ 2 | VIX settlement Wednesday offset +0d dir=short hold=rth | 24 | 2 | 1.38 | -0.18 | 0.94 | 0.36 / 1.33 | 0.20 / -0.06 / 0.09 | 0.13 | -0.59 | 0.96 | -0.04 | 0.00 | 38 S | NO |
| NQ 3 | VIX settlement Wednesday offset -1d dir=short hold=c2c | 23 | 2 | 1.20 | -0.11 | 0.82 | 0.29 / 1.17 | 0.16 / 0.07 / -0.02 | 0.11 | -0.55 | 0.97 | -0.08 | 0.00 | 37 S | NO |
| NQ 4 | VIX settlement Wednesday offset +1d dir=short hold=c2c | 23 | 2 | 0.92 | 0.52 | -0.06 | -1.42 / 1.36 | 0.13 / -0.88 / -0.03 | -0.05 | -0.13 | 0.54 | -0.22 | 0.00 | 36 S | NO |
| NQ 5 (diag) | VIX settlement Wednesday offset +0d dir=short hold=c2c | 22 | 1 | 0.28 | 0.30 | -0.11 | -0.42 / 1.27 | 0.06 / -0.59 / -0.39 | -0.12 | 0.64 | 0.56 | -0.41 | 0.00 | 36 S | diag |
| NQ 6 (diag) | VIX settlement Wednesday offset -1d dir=short hold=rth | 24 | 1 | 0.21 | -0.84 | 0.53 | 0.88 / 1.36 | 0.04 / 0.41 / 0.24 | 0.14 | -0.57 | 0.90 | -0.09 | 0.00 | 38 S | diag |
| NQ 7 (diag) | VIX settlement Wednesday offset -1d dir=long hold=rth | 24 | 1 | -0.25 | 0.77 | -0.57 | -0.91 / 1.45 | -0.10 / -0.64 / -0.47 | -0.26 | 0.56 | 0.14 | -0.52 | 0.00 | 38 S | diag |
| RTY 1 | VIX settlement Wednesday offset -1d dir=short hold=c2c | 23 | 2 | 0.73 | 0.18 | 0.54 | 0.20 / 1.23 | 0.06 / -0.07 / -0.02 | 0.01 | -0.40 | 0.92 | -0.16 | 0.00 | 37 S | NO |
| RTY 2 | VIX settlement Wednesday offset +0d dir=short hold=rth | 24 | 2 | 0.58 | -0.09 | 0.54 | 0.46 / 1.49 | 0.04 / -0.02 / 0.01 | 0.02 | -0.37 | 0.86 | -0.12 | 0.00 | 38 S | NO |
| RTY 3 | VIX settlement Wednesday offset +1d dir=short hold=c2c | 23 | 2 | 0.28 | 0.40 | -0.29 | -0.92 / 1.39 | -0.00 / -0.62 / -0.06 | -0.12 | -0.13 | 0.37 | -0.35 | 0.00 | 36 S | NO |
| RTY 4 (diag) | VIX settlement Wednesday offset -1d dir=long hold=rth | 24 | 1 | 0.72 | 0.05 | 0.39 | -0.34 / 1.58 | 0.11 / 0.08 / -0.18 | 0.03 | 0.47 | 0.78 | -0.14 | 0.00 | 38 S | diag |
| RTY 5 (diag) | VIX settlement Wednesday offset +1d dir=short hold=rth | 24 | 1 | 0.58 | 0.51 | 0.02 | -0.56 / 1.23 | 0.05 / -0.31 / -0.49 | -0.11 | 0.27 | 0.51 | -0.31 | 0.00 | 38 S | diag |
| RTY 6 (diag) | VIX settlement Wednesday offset +0d dir=short hold=c2c | 22 | 1 | 0.07 | 0.89 | -0.46 | -1.19 / 1.24 | -0.01 / -0.66 / -0.34 | -0.17 | 0.61 | 0.28 | -0.37 | 0.00 | 36 S | diag |
| YM 1 | VIX settlement Wednesday offset -1d dir=short hold=c2c | 23 | 2 | 0.74 | 0.01 | 0.62 | 0.46 / 1.09 | 0.07 / -0.21 / 0.09 | 0.03 | -0.54 | 0.96 | -0.15 | 0.00 | 37 S | NO |
| YM 2 | VIX settlement Wednesday offset +1d dir=short hold=c2c | 23 | 2 | 0.73 | 0.42 | -0.39 | -1.91 / 1.27 | 0.08 / -0.67 / -0.30 | -0.12 | -0.11 | 0.36 | -0.30 | 0.00 | 36 S | NO |
| YM 3 | VIX settlement Wednesday offset +0d dir=short hold=rth | 24 | 2 | 0.71 | 0.06 | 0.82 | 1.00 / 1.23 | 0.08 / -0.10 / 0.16 | 0.07 | -0.45 | 0.98 | -0.09 | 0.00 | 38 S | NO |
| YM 4 (diag) | VIX settlement Wednesday offset +0d dir=short hold=c2c | 22 | 1 | 0.15 | 0.53 | 0.31 | 0.59 / 0.99 | 0.02 / -0.23 / 0.14 | 0.02 | 0.43 | 0.84 | -0.15 | 0.00 | 36 S | diag |
| YM 5 (diag) | VIX settlement Wednesday offset +1d dir=short hold=rth | 24 | 1 | 0.13 | -0.14 | 0.31 | 0.58 / 1.11 | 0.00 / 0.02 / -0.06 | 0.00 | -0.34 | 0.78 | -0.17 | 0.00 | 38 S | diag |
| YM 6 (diag) | VIX settlement Wednesday offset -1d dir=short hold=rth | 24 | 1 | 0.05 | -0.13 | 0.12 | 0.27 / 1.40 | -0.00 / 0.01 / -0.06 | -0.01 | 0.31 | 0.69 | -0.18 | 0.00 | 38 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 14 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 15 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 8 |
| worst-decile corr <= +0.30 | 19 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 6 |
| small-sample (<100 trades pair window) | 26 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES VIX settlement Wednesday offset +0d dir=short hold=rth | clean | 1.20 | 3.62 | -76368 | -43343 | 214539 | -144561 | 5.08 | 8.6 | 1.62 | -83366 | 314100 | -100265 |
| ES VIX settlement Wednesday offset +0d dir=short hold=rth | H1 | 0.23 | 0.34 | -151843 | -101229 | 164422 | -164422 | 0.33 | 7.1 | 2.77 | -82688 | 170517 | -109817 |
| ES VIX settlement Wednesday offset +0d dir=short hold=rth | H2 | 0.91 | 2.05 | -109802 | -79016 | 219605 | -117416 | 1.32 | 11.1 | 2.64 | -78535 | 217425 | -79653 |
| ES VIX settlement Wednesday offset +0d dir=short hold=rth | all | 0.99 | 2.30 | -106087 | -64502 | 222946 | -164422 | 6.43 | 8.9 | 2.02 | -85247 | 314100 | -109817 |
| NQ VIX settlement Wednesday offset +0d dir=short hold=rth | clean | 1.37 | 4.68 | -65717 | -37242 | 213554 | -137050 | 5.82 | 7.6 | 1.66 | -83366 | 300401 | -96096 |
| NQ VIX settlement Wednesday offset +0d dir=short hold=rth | H1 | 0.35 | 0.54 | -199964 | -133309 | 208665 | -208665 | 0.53 | 7.1 | 2.76 | -82642 | 175885 | -115185 |
| NQ VIX settlement Wednesday offset +0d dir=short hold=rth | H2 | 0.37 | 0.61 | -160383 | -115758 | 320765 | -202967 | 0.40 | 11.1 | 2.58 | -78535 | 217425 | -79653 |
| NQ VIX settlement Wednesday offset +0d dir=short hold=rth | all | 0.94 | 1.94 | -127467 | -74860 | 397712 | -208665 | 3.73 | 8.3 | 2.03 | -85844 | 300401 | -115185 |
| RTY VIX settlement Wednesday offset +0d dir=short hold=rth | clean | 0.58 | 1.24 | -103965 | -71274 | 344034 | -205633 | 1.52 | 12.4 | 1.50 | -85088 | 312517 | -104919 |
| RTY VIX settlement Wednesday offset +0d dir=short hold=rth | H1 | 0.32 | 0.47 | -83922 | -58004 | 135965 | -135965 | 0.35 | 10.7 | 2.81 | -80875 | 164826 | -104126 |
| RTY VIX settlement Wednesday offset +0d dir=short hold=rth | H2 | 0.56 | 0.76 | -113987 | -62993 | 219680 | -195681 | 0.58 | 8.3 | 2.49 | -78535 | 217425 | -79653 |
| RTY VIX settlement Wednesday offset +0d dir=short hold=rth | all | 0.54 | 1.01 | -112282 | -71737 | 344034 | -205633 | 2.03 | 11.3 | 1.92 | -85763 | 312517 | -104919 |
| YM VIX settlement Wednesday offset +0d dir=short hold=rth | clean | 0.71 | 1.46 | -112272 | -70129 | 376108 | -192180 | 1.70 | 9.5 | 1.54 | -82397 | 312725 | -99281 |
| YM VIX settlement Wednesday offset +0d dir=short hold=rth | H1 | -0.06 | -0.08 | -126987 | -90106 | 193670 | -193670 | -0.06 | 10.7 | 2.73 | -81885 | 176367 | -115667 |
| YM VIX settlement Wednesday offset +0d dir=short hold=rth | H2 | 1.64 | 4.45 | -90292 | -45146 | 150456 | -150456 | 3.78 | 5.6 | 2.64 | -78535 | 217425 | -79653 |
| YM VIX settlement Wednesday offset +0d dir=short hold=rth | all | 0.82 | 1.67 | -119784 | -71901 | 376108 | -193670 | 3.18 | 8.9 | 1.97 | -85235 | 312725 | -115667 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES VIX settlement Wednesday offset +0d dir=short hold=rth | -14.3 | -25.0 | 16.8 | 11.8 | -8.2 / 19.5 | -31.8 / 14.2 | NO |
| NQ VIX settlement Wednesday offset +0d dir=short hold=rth | -13.8 | -34.8 | 16.7 | 19.1 | -0.5 / 21.1 | -42.1 / 9.0 | NO |
| RTY VIX settlement Wednesday offset +0d dir=short hold=rth | -22.4 | -15.8 | 13.6 | 12.6 | -16.7 / 17.8 | -20.9 / 19.7 | NO |
| YM VIX settlement Wednesday offset +0d dir=short hold=rth | -16.9 | -35.7 | 15.0 | 12.5 | -6.3 / 20.7 | -43.0 / 8.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 VIX settlement Wednesday offset +1d dir=short hold=rth | negative pre-2023 | 126 | -19.4 | -48.8 | -34.6 | 29.4 | -0.06 / -0.15 / -0.10 | 653.6 / 624.3 |
| ES 2 VIX settlement Wednesday offset +0d dir=short hold=rth | negative pre-2023 | 125 | -1.2 | -30.6 | -16.4 | 29.4 | -0.00 / -0.08 / -0.04 | 886.5 / 857.1 |
| ES 3 VIX settlement Wednesday offset -1d dir=short hold=c2c | negative pre-2023 | 126 | -10.4 | -39.8 | -25.6 | 29.4 | -0.02 / -0.09 / -0.06 | 978.3 / 948.9 |
| ES 4 VIX settlement Wednesday offset +1d dir=short hold=c2c | positive pre-2023 | 125 | 178.4 | 149.0 | 163.3 | 29.4 | 0.40 / 0.33 / 0.36 | 603.8 / 574.4 |
| ES 5 (diag) VIX settlement Wednesday offset -1d dir=short hold=rth | negative pre-2023 | 126 | -131.4 | -160.8 | -146.6 | 29.4 | -0.46 / -0.56 / -0.51 | 84.4 / 55.0 |
| ES 6 (diag) VIX settlement Wednesday offset +0d dir=short hold=c2c | positive pre-2023 | 125 | 216.0 | 186.6 | 200.8 | 29.4 | 0.53 / 0.46 / 0.49 | 105.7 / 76.3 |
| ES 7 (diag) VIX settlement Wednesday offset +0d dir=long hold=c2c | negative pre-2023 | 125 | -216.0 | -245.4 | -231.2 | 29.4 | -0.53 / -0.60 / -0.56 | -105.7 / -135.0 |
| NQ 1 VIX settlement Wednesday offset +1d dir=short hold=rth | negative pre-2023 | 126 | -73.5 | -87.8 | -79.2 | 14.4 | -0.12 / -0.14 / -0.13 | 1641.7 / 1627.3 |
| NQ 2 VIX settlement Wednesday offset +0d dir=short hold=rth | negative pre-2023 | 125 | -88.6 | -103.0 | -94.4 | 14.4 | -0.15 / -0.18 / -0.16 | 1695.4 / 1681.1 |
| NQ 3 VIX settlement Wednesday offset -1d dir=short hold=c2c | negative pre-2023 | 126 | -58.3 | -72.6 | -64.1 | 14.4 | -0.09 / -0.11 / -0.10 | 1861.5 / 1847.2 |
| NQ 4 VIX settlement Wednesday offset +1d dir=short hold=c2c | positive pre-2023 | 125 | 355.2 | 340.8 | 349.4 | 14.4 | 0.55 / 0.52 / 0.54 | 1140.9 / 1126.5 |
| NQ 5 (diag) VIX settlement Wednesday offset +0d dir=short hold=c2c | positive pre-2023 | 125 | 229.8 | 215.4 | 224.0 | 14.4 | 0.32 / 0.30 / 0.31 | 338.9 / 324.5 |
| NQ 6 (diag) VIX settlement Wednesday offset -1d dir=short hold=rth | negative pre-2023 | 126 | -365.6 | -379.9 | -371.3 | 14.4 | -0.81 / -0.84 / -0.82 | 157.3 / 142.9 |
| NQ 7 (diag) VIX settlement Wednesday offset -1d dir=long hold=rth | positive pre-2023 | 126 | 365.6 | 351.2 | 359.8 | 14.4 | 0.81 / 0.77 / 0.79 | -157.3 / -171.7 |
| RTY 1 VIX settlement Wednesday offset -1d dir=short hold=c2c | positive pre-2023 | 72 | 83.7 | 69.3 | 71.5 | 14.4 | 0.21 / 0.18 / 0.18 | 377.4 / 363.0 |
| RTY 2 VIX settlement Wednesday offset +0d dir=short hold=rth | negative pre-2023 | 71 | -11.4 | -25.8 | -23.6 | 14.4 | -0.04 / -0.09 / -0.08 | 277.3 / 262.9 |
| RTY 3 VIX settlement Wednesday offset +1d dir=short hold=c2c | positive pre-2023 | 71 | 151.8 | 137.5 | 139.7 | 14.4 | 0.44 / 0.40 / 0.41 | 132.4 / 118.0 |
| RTY 4 (diag) VIX settlement Wednesday offset -1d dir=long hold=rth | positive pre-2023 | 71 | 29.4 | 15.0 | 17.2 | 14.4 | 0.10 / 0.05 / 0.06 | 265.6 / 251.3 |
| RTY 5 (diag) VIX settlement Wednesday offset +1d dir=short hold=rth | positive pre-2023 | 72 | 157.8 | 143.5 | 145.7 | 14.4 | 0.56 / 0.51 / 0.52 | 189.8 / 175.4 |
| RTY 6 (diag) VIX settlement Wednesday offset +0d dir=short hold=c2c | positive pre-2023 | 71 | 335.8 | 321.5 | 323.7 | 14.4 | 0.92 / 0.89 / 0.89 | 43.0 / 28.6 |
| YM 1 VIX settlement Wednesday offset -1d dir=short hold=c2c | positive pre-2023 | 126 | 16.1 | 1.8 | 7.5 | 14.4 | 0.05 / 0.01 / 0.02 | 410.9 / 396.5 |
| YM 2 VIX settlement Wednesday offset +1d dir=short hold=c2c | positive pre-2023 | 125 | 158.4 | 144.0 | 149.7 | 14.4 | 0.46 / 0.42 / 0.43 | 407.0 / 392.6 |
| YM 3 VIX settlement Wednesday offset +0d dir=short hold=rth | positive pre-2023 | 125 | 31.9 | 17.5 | 23.2 | 14.4 | 0.11 / 0.06 / 0.08 | 372.7 / 358.3 |
| YM 4 (diag) VIX settlement Wednesday offset +0d dir=short hold=c2c | positive pre-2023 | 125 | 173.6 | 159.2 | 165.0 | 14.4 | 0.58 / 0.53 / 0.55 | 89.1 / 74.7 |
| YM 5 (diag) VIX settlement Wednesday offset +1d dir=short hold=rth | negative pre-2023 | 126 | -18.8 | -33.2 | -27.5 | 14.4 | -0.08 / -0.14 / -0.12 | 65.6 / 51.3 |
| YM 6 (diag) VIX settlement Wednesday offset -1d dir=short hold=rth | negative pre-2023 | 126 | -16.1 | -30.4 | -24.7 | 14.4 | -0.07 / -0.13 / -0.10 | 30.8 / 16.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 4 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.13, p(top) = 0.15); NQ: 4 cells pass the clean rule against a replicate mean of 2.3 (p(count) = 0.17, p(top) = 0.04); RTY: 3 cells pass the clean rule against a replicate mean of 2.3 (p(count) = 0.44, p(top) = 0.76); YM: 3 cells pass the clean rule against a replicate mean of 2.2 (p(count) = 0.36, p(top) = 0.47).
- Of 14 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.14 (NQ VIX settlement Wednesday offset +0d dir=short hold=rth); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 5; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 7, 'positive pre-2023': 7}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_6.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj6/ (`BJ6_CO_all_selected_scored.csv`).

DONE BJ6
