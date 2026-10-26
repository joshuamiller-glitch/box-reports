# REPORT BI5 - prior-week high/low break or rejection (BI batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 11 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.21; best pair-window standalone Sharpe +1.01.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BI', before the first run)
- Rule: see IDEAS_BI.md / PREREG_AUTOPILOT.md BATCH BI (frozen before the first run). prior-week high/low break or rejection
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      12 |         12 |         4 |               1.484 |                2 |          4 |            3 |
| NQ    |      12 |         12 |         1 |               0.522 |                2 |          1 |            3 |
| RTY   |      12 |         12 |         4 |               1.366 |                2 |          4 |            3 |
| YM    |      12 |         12 |         2 |               0.647 |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    4 |            1.665 |               5 |      0.05  |                       1.095 |            0.683 |           1.186 |    0.08  |       1.484 |                1.405 |
| NQ    |     200 |                    1 |            2.42  |               7 |      0.955 |                       0.522 |            0.737 |           1.197 |    0.765 |       0.522 |                1.604 |
| RTY   |     200 |                    4 |            2.065 |               6 |      0.125 |                       0.967 |            0.704 |           1.125 |    0.155 |       1.366 |                1.459 |
| YM    |     200 |                    2 |            1.915 |               6 |      0.59  |                       0.535 |            0.716 |           1.192 |    0.675 |       0.548 |                1.54  |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | prior-week high/low break buffer=0.1ATR dir=with hold=120m | 139 | 2 | 1.48 | -0.48 | 0.80 | -0.12 / 1.28 | 0.17 / -0.26 / -0.04 | 0.03 | -0.21 | 0.98 | -0.10 | 1.00 | 229 | NO |
| ES 2 | prior-week high/low break buffer=0.0ATR dir=with hold=120m | 153 | 2 | 1.35 | -0.54 | 1.01 | 0.64 / 1.17 | 0.15 / -0.05 / 0.06 | 0.07 | 0.60 | 0.99 | -0.07 | 0.33 | 259 | NO |
| ES 3 | prior-week high/low break buffer=0.1ATR dir=with hold=60m | 147 | 2 | 1.09 | -0.79 | 0.14 | -1.00 / 0.91 | 0.11 / -0.52 / -0.29 | -0.12 | 0.30 | 0.85 | -0.28 | 0.00 | 243 | NO |
| ES 4 | prior-week high/low break buffer=0.1ATR dir=with hold=flat | 147 | 2 | 0.46 | -0.29 | 0.19 | -0.15 / 1.28 | 0.03 / -0.16 / 0.01 | -0.02 | 0.43 | 0.74 | -0.17 | 0.00 | 242 | NO |
| ES 5 (diag) | prior-week high/low break buffer=0.0ATR dir=with hold=flat | 160 | 1 | 0.49 | -0.24 | 0.39 | 0.45 / 1.33 | 0.03 / -0.22 / 0.17 | 0.01 | 0.53 | 0.83 | -0.15 | 1.00 | 268 | diag |
| ES 6 (diag) | prior-week high/low break buffer=0.0ATR dir=with hold=60m | 159 | 1 | 0.28 | -0.53 | 0.23 | 0.24 / 1.07 | -0.03 / -0.12 / -0.11 | -0.11 | 0.83 | 0.88 | -0.25 | 0.00 | 268 | diag |
| ES 7 (diag) | prior-week high/low break buffer=0.1ATR dir=against hold=flat | 147 | 0 | -0.65 | -0.18 | -0.40 | -0.13 / 1.46 | -0.13 / -0.02 / -0.07 | -0.12 | -0.44 | 0.34 | -0.23 | 0.00 | 242 | diag |
| NQ 1 | prior-week high/low break buffer=0.0ATR dir=with hold=60m | 171 | 2 | 0.52 | -0.07 | 1.00 | 1.57 / 1.26 | 0.07 / 0.70 / 0.36 | 0.20 | -0.05 | 0.98 | -0.01 | 0.67 | 271 | NO |
| NQ 2 (diag) | prior-week high/low break buffer=0.1ATR dir=against hold=flat | 156 | 1 | 0.41 | -0.40 | 0.33 | 0.15 / 1.57 | 0.02 / -0.36 / 0.32 | 0.01 | -0.77 | 0.71 | -0.11 | 0.50 | 256 | diag |
| NQ 3 (diag) | prior-week high/low break buffer=0.1ATR dir=with hold=120m | 149 | 1 | 0.36 | 0.06 | 0.25 | 0.14 / 1.21 | 0.07 / 0.65 / -0.55 | 0.00 | 0.37 | 0.73 | -0.19 | 0.50 | 247 | diag |
| NQ 4 (diag) | prior-week high/low break buffer=0.1ATR dir=against hold=60m | 156 | 1 | 0.13 | -0.18 | -0.59 | -1.49 / 1.26 | -0.04 / -0.44 / -0.43 | -0.19 | -0.53 | 0.20 | -0.38 | 0.00 | 255 | diag |
| RTY 1 | prior-week high/low break buffer=0.0ATR dir=with hold=120m | 141 | 2 | 1.37 | -0.18 | 0.44 | -1.08 / 1.18 | 0.20 / 0.02 / -0.46 | 0.00 | -0.12 | 0.93 | -0.15 | 0.33 | 240 | NO |
| RTY 2 | prior-week high/low break buffer=0.0ATR dir=with hold=60m | 148 | 2 | 1.10 | -0.00 | 0.53 | -0.43 / 0.86 | 0.19 / 0.20 / -0.30 | 0.05 | -0.32 | 0.96 | -0.08 | 0.67 | 252 | NO |
| RTY 3 | prior-week high/low break buffer=0.0ATR dir=with hold=flat | 148 | 2 | 0.87 | 0.10 | 0.24 | -0.75 / 1.50 | 0.15 / -0.06 / -0.56 | -0.05 | 0.34 | 0.69 | -0.22 | 0.00 | 252 | NO |
| RTY 4 | prior-week high/low break buffer=0.1ATR dir=with hold=120m | 150 | 2 | 0.53 | -0.51 | -0.25 | -1.65 / 1.01 | 0.04 / -0.33 / -0.39 | -0.14 | -0.29 | 0.54 | -0.29 | 0.00 | 238 | NO |
| RTY 5 (diag) | prior-week high/low break buffer=0.1ATR dir=with hold=60m | 155 | 1 | 0.50 | -0.63 | -0.01 | -0.80 / 0.94 | 0.03 / -0.15 / -0.16 | -0.08 | -0.23 | 0.76 | -0.22 | 0.00 | 247 | diag |
| RTY 6 (diag) | prior-week high/low break buffer=0.1ATR dir=against hold=flat | 155 | 1 | 0.13 | -0.37 | 0.23 | 0.54 / 1.43 | -0.00 / 0.11 / 0.17 | 0.03 | 0.12 | 0.71 | -0.11 | 1.00 | 247 | diag |
| RTY 7 (diag) | prior-week high/low break buffer=0.1ATR dir=with hold=flat | 155 | 0 | -0.34 | 0.09 | -0.47 | -0.80 / 1.51 | -0.10 / -0.23 / -0.24 | -0.16 | -0.13 | 0.28 | -0.32 | 0.00 | 247 | diag |
| YM 1 | prior-week high/low break buffer=0.1ATR dir=against hold=120m | 156 | 2 | 0.55 | 0.30 | 0.27 | -0.06 / 1.09 | 0.01 / -0.68 / 0.32 | -0.05 | -0.22 | 0.81 | -0.20 | 0.00 | 236 | NO |
| YM 2 | prior-week high/low break buffer=0.0ATR dir=against hold=60m | 177 | 2 | 0.52 | -0.16 | 0.38 | 0.14 / 1.15 | 0.04 / -0.44 / 0.22 | -0.02 | -0.32 | 0.91 | -0.15 | 0.33 | 271 | NO |
| YM 3 (diag) | prior-week high/low break buffer=0.1ATR dir=against hold=60m | 161 | 1 | 0.65 | -0.07 | 0.67 | 0.64 / 0.96 | 0.06 / -0.17 / 0.20 | 0.03 | -0.26 | 0.96 | -0.09 | 0.50 | 242 | diag |
| YM 4 (diag) | prior-week high/low break buffer=0.1ATR dir=against hold=flat | 160 | 1 | 0.33 | 0.09 | 0.16 | -0.16 / 1.50 | -0.01 / -0.28 / 0.20 | -0.03 | -0.30 | 0.67 | -0.16 | 0.00 | 241 | diag |
| YM 5 (diag) | prior-week high/low break buffer=0.0ATR dir=against hold=flat | 176 | 1 | 0.17 | -0.09 | 0.02 | -0.22 / 1.34 | -0.02 / -0.31 / 0.13 | -0.05 | -0.38 | 0.52 | -0.19 | 0.00 | 271 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 11 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 5 |
| worst-decile corr <= +0.30 | 17 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES prior-week high/low break buffer=0.0ATR dir=with hold=120m | clean | 1.27 | 2.93 | -88517 | -75032 | 375607 | -113215 | 3.09 | 32.4 | 1.61 | -81107 | 285602 | -84649 |
| ES prior-week high/low break buffer=0.0ATR dir=with hold=120m | H1 | 0.16 | 0.22 | -225404 | -189648 | 490949 | -312805 | 0.12 | 32.1 | 2.78 | -76720 | 159949 | -78693 |
| ES prior-week high/low break buffer=0.0ATR dir=with hold=120m | H2 | 1.29 | 2.38 | -101503 | -84218 | 219801 | -106886 | 1.69 | 36.1 | 2.54 | -91724 | 221708 | -101749 |
| ES prior-week high/low break buffer=0.0ATR dir=with hold=120m | all | 1.01 | 1.79 | -130099 | -98761 | 848440 | -312805 | 1.88 | 33.3 | 1.99 | -83305 | 285602 | -101749 |
| NQ prior-week high/low break buffer=0.0ATR dir=with hold=60m | clean | 0.53 | 0.81 | -124334 | -105453 | 455015 | -188285 | 1.06 | 36.2 | 1.53 | -85325 | 245849 | -96225 |
| NQ prior-week high/low break buffer=0.0ATR dir=with hold=60m | H1 | 1.59 | 3.16 | -123807 | -119218 | 360705 | -130677 | 1.44 | 35.7 | 3.53 | -67456 | 138610 | -93396 |
| NQ prior-week high/low break buffer=0.0ATR dir=with hold=60m | H2 | 1.54 | 3.11 | -144624 | -124435 | 299735 | -158492 | 2.47 | 30.6 | 2.84 | -81920 | 217425 | -86423 |
| NQ prior-week high/low break buffer=0.0ATR dir=with hold=60m | all | 1.00 | 1.75 | -137286 | -114082 | 517481 | -188285 | 3.36 | 35.1 | 2.11 | -85539 | 245849 | -96225 |
| RTY prior-week high/low break buffer=0.0ATR dir=with hold=60m | clean | 1.04 | 1.63 | -133718 | -95934 | 482534 | -290515 | 1.95 | 27.6 | 1.65 | -77696 | 231698 | -81771 |
| RTY prior-week high/low break buffer=0.0ATR dir=with hold=60m | H1 | 1.09 | 2.13 | -74341 | -69771 | 189586 | -84675 | 1.31 | 39.3 | 3.03 | -80341 | 160261 | -82394 |
| RTY prior-week high/low break buffer=0.0ATR dir=with hold=60m | H2 | -1.83 | -1.97 | -148102 | -124495 | 596435 | -163498 | -0.76 | 44.4 | 2.18 | -83741 | 192169 | -92286 |
| RTY prior-week high/low break buffer=0.0ATR dir=with hold=60m | all | 0.53 | 0.79 | -138308 | -102517 | 734085 | -290515 | 1.00 | 33.3 | 1.98 | -80031 | 231698 | -92286 |
| YM prior-week high/low break buffer=0.0ATR dir=against hold=60m | clean | 0.55 | 1.11 | -91008 | -76005 | 422249 | -150390 | 1.17 | 35.2 | 1.50 | -87928 | 259547 | -94388 |
| YM prior-week high/low break buffer=0.0ATR dir=against hold=60m | H1 | -1.77 | -2.27 | -97076 | -96010 | 489617 | -99601 | -0.77 | 50.0 | 2.39 | -81455 | 156256 | -85861 |
| YM prior-week high/low break buffer=0.0ATR dir=against hold=60m | H2 | 1.23 | 2.56 | -84556 | -80527 | 270017 | -88743 | 1.70 | 38.9 | 2.71 | -87296 | 213217 | -92067 |
| YM prior-week high/low break buffer=0.0ATR dir=against hold=60m | all | 0.38 | 0.72 | -96860 | -84590 | 527988 | -150390 | 1.09 | 38.7 | 1.91 | -87732 | 259547 | -94388 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior-week high/low break buffer=0.0ATR dir=with hold=120m | -12.6 | -4.9 | 19.8 | 27.1 | 21.5 / 22.7 | 23.5 / 25.7 | NO |
| NQ prior-week high/low break buffer=0.0ATR dir=with hold=60m | -11.0 | -3.1 | 12.2 | 35.3 | -3.9 / 10.5 | 1.1 / 34.0 | NO |
| RTY prior-week high/low break buffer=0.0ATR dir=with hold=60m | -22.0 | 9.5 | 24.4 | 35.7 | 25.6 / 30.2 | 20.7 / 24.7 | NO |
| YM prior-week high/low break buffer=0.0ATR dir=against hold=60m | -23.7 | 3.1 | 11.6 | 22.8 | 2.4 / 10.8 | 15.5 / 22.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 prior-week high/low break buffer=0.1ATR dir=with hold=120m | negative pre-2023 | 827 | -19.2 | -48.5 | -34.4 | 29.4 | -0.19 / -0.48 / -0.34 | 254.0 / 224.6 |
| ES 2 prior-week high/low break buffer=0.0ATR dir=with hold=120m | negative pre-2023 | 861 | -16.9 | -46.3 | -32.0 | 29.4 | -0.20 / -0.54 / -0.37 | 234.9 / 205.5 |
| ES 3 prior-week high/low break buffer=0.1ATR dir=with hold=60m | negative pre-2023 | 881 | -34.9 | -64.2 | -50.1 | 29.4 | -0.43 / -0.79 / -0.62 | 138.7 / 109.3 |
| ES 4 prior-week high/low break buffer=0.1ATR dir=with hold=flat | negative pre-2023 | 880 | -7.2 | -36.6 | -22.5 | 29.4 | -0.06 / -0.29 / -0.18 | 132.0 / 102.6 |
| ES 5 (diag) prior-week high/low break buffer=0.0ATR dir=with hold=flat | gross-positive, cost-negative pre-2023 | 907 | 1.5 | -27.9 | -13.7 | 29.4 | 0.01 / -0.24 / -0.12 | 123.8 / 94.4 |
| ES 6 (diag) prior-week high/low break buffer=0.0ATR dir=with hold=60m | negative pre-2023 | 908 | -13.7 | -43.0 | -28.9 | 29.4 | -0.17 / -0.53 / -0.36 | 51.0 / 21.7 |
| ES 7 (diag) prior-week high/low break buffer=0.1ATR dir=against hold=flat | gross-positive, cost-negative pre-2023 | 880 | 7.2 | -22.1 | -8.0 | 29.4 | 0.06 / -0.18 / -0.06 | -132.0 / -161.3 |
| NQ 1 prior-week high/low break buffer=0.0ATR dir=with hold=60m | gross-positive, cost-negative pre-2023 | 888 | 7.9 | -6.4 | 2.3 | 14.4 | 0.08 / -0.07 / 0.02 | 104.1 / 89.7 |
| NQ 2 (diag) prior-week high/low break buffer=0.1ATR dir=against hold=flat | negative pre-2023 | 860 | -63.8 | -78.2 | -69.5 | 14.4 | -0.32 / -0.40 / -0.35 | 230.0 / 215.6 |
| NQ 3 (diag) prior-week high/low break buffer=0.1ATR dir=with hold=120m | positive pre-2023 | 813 | 21.6 | 7.3 | 16.0 | 14.4 | 0.17 / 0.06 / 0.12 | 89.1 / 74.7 |
| NQ 4 (diag) prior-week high/low break buffer=0.1ATR dir=against hold=60m | negative pre-2023 | 861 | -3.6 | -18.0 | -9.3 | 14.4 | -0.04 / -0.18 / -0.09 | 28.1 / 13.8 |
| RTY 1 prior-week high/low break buffer=0.0ATR dir=with hold=120m | gross-positive, cost-negative pre-2023 | 476 | 2.0 | -12.3 | -10.1 | 14.4 | 0.03 / -0.18 / -0.14 | 137.5 / 123.2 |
| RTY 2 prior-week high/low break buffer=0.0ATR dir=with hold=60m | gross-positive, cost-negative pre-2023 | 497 | 14.2 | -0.1 | 2.1 | 14.4 | 0.24 / -0.00 / 0.04 | 89.9 / 75.5 |
| RTY 3 prior-week high/low break buffer=0.0ATR dir=with hold=flat | positive pre-2023 | 495 | 23.8 | 9.4 | 11.7 | 14.4 | 0.25 / 0.10 / 0.12 | 112.8 / 98.4 |
| RTY 4 prior-week high/low break buffer=0.1ATR dir=with hold=120m | negative pre-2023 | 458 | -21.5 | -35.9 | -33.7 | 14.4 | -0.31 / -0.51 / -0.48 | 61.1 / 46.8 |
| RTY 5 (diag) prior-week high/low break buffer=0.1ATR dir=with hold=60m | negative pre-2023 | 475 | -21.8 | -36.2 | -34.0 | 14.4 | -0.38 / -0.63 / -0.59 | 43.8 / 29.5 |
| RTY 6 (diag) prior-week high/low break buffer=0.1ATR dir=against hold=flat | negative pre-2023 | 474 | -23.0 | -37.4 | -35.2 | 14.4 | -0.23 / -0.37 / -0.35 | 27.2 / 12.9 |
| RTY 7 (diag) prior-week high/low break buffer=0.1ATR dir=with hold=flat | positive pre-2023 | 474 | 23.0 | 8.7 | 10.8 | 14.4 | 0.23 / 0.09 / 0.11 | -27.2 / -41.6 |
| YM 1 prior-week high/low break buffer=0.1ATR dir=against hold=120m | positive pre-2023 | 716 | 34.9 | 20.5 | 26.3 | 14.4 | 0.52 / 0.30 / 0.39 | 60.4 / 46.1 |
| YM 2 prior-week high/low break buffer=0.0ATR dir=against hold=60m | gross-positive, cost-negative pre-2023 | 830 | 6.9 | -7.4 | -1.6 | 14.4 | 0.15 / -0.16 / -0.03 | 56.0 / 41.6 |
| YM 3 (diag) prior-week high/low break buffer=0.1ATR dir=against hold=60m | gross-positive, cost-negative pre-2023 | 756 | 10.7 | -3.7 | 2.1 | 14.4 | 0.22 / -0.07 / 0.04 | 78.9 / 64.5 |
| YM 4 (diag) prior-week high/low break buffer=0.1ATR dir=against hold=flat | positive pre-2023 | 757 | 24.0 | 9.6 | 15.4 | 14.4 | 0.24 / 0.09 / 0.15 | 65.4 / 51.0 |
| YM 5 (diag) prior-week high/low break buffer=0.0ATR dir=against hold=flat | gross-positive, cost-negative pre-2023 | 831 | 5.2 | -9.2 | -3.4 | 14.4 | 0.05 / -0.09 / -0.03 | 35.4 / 21.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 4 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.05, p(top) = 0.08); NQ: 1 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.95, p(top) = 0.77); RTY: 4 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.12, p(top) = 0.15); YM: 2 cells pass the clean rule against a replicate mean of 1.9 (p(count) = 0.59, p(top) = 0.68).
- Of 11 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.21 (NQ prior-week high/low break buffer=0.0ATR dir=with hold=60m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 5, 'gross-positive, cost-negative pre-2023': 4, 'positive pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bi_5.py, ap_bi_pipe.py (= ap_b_pipe2 with module swap), ap_bi_job.sh, ap_sw_common.py, ap_bi_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bi5/ (`BI5_CO_all_selected_scored.csv`).

DONE BI5
