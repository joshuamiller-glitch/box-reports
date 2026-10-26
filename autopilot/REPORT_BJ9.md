# REPORT BJ9 - opening-drive continuation (BJ batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 11 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.18; best pair-window standalone Sharpe +0.86.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. opening-drive continuation. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      12 |         12 |         1 |               0.407 |                2 |          1 |            3 |
| NQ    |      12 |         12 |         5 |               1.857 |                2 |          5 |            3 |
| RTY   |      12 |         12 |         3 |               0.778 |                2 |          3 |            3 |
| YM    |      12 |         12 |         2 |               0.518 |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            1.21  |               4 |      0.7   |                       0.407 |            0.613 |           1.195 |    0.5   |       0.407 |                1.421 |
| NQ    |     200 |                    5 |            2.42  |               6 |      0.06  |                       1.292 |            0.706 |           1.295 |    0.05  |       1.857 |                1.899 |
| RTY   |     200 |                    3 |            1.57  |               5 |      0.225 |                       0.49  |            0.666 |           1.292 |    0.565 |       0.514 |                1.639 |
| YM    |     200 |                    2 |            1.555 |               5 |      0.475 |                       0.473 |            0.689 |           1.327 |    0.56  |       0.518 |                1.62  |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | 390 | 2 | 0.41 | -0.21 | -0.21 | -1.06 / 1.07 | 0.06 / 0.32 / -0.59 | -0.15 | 0.39 | 0.61 | -0.29 | 0.00 | 636 | NO |
| ES 2 (diag) | first 5m (09:30-09:34) move>=0.03ADR dir=with hold=120m | 390 | 1 | 0.11 | 0.05 | -0.11 | -0.46 / 1.47 | 0.00 / 0.39 / -0.33 | -0.11 | 0.36 | 0.66 | -0.26 | 0.00 | 636 | diag |
| ES 3 (diag) | first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | 390 | 1 | 0.10 | -0.76 | -0.45 | -1.28 / 0.94 | 0.04 / -0.03 / -0.46 | -0.18 | 0.10 | 0.56 | -0.30 | 0.00 | 636 | diag |
| ES 4 (diag) | first 5m (09:30-09:34) move>=0.0ADR dir=with hold=120m | 509 | 1 | -0.02 | -0.12 | -0.10 | -0.31 / 0.99 | -0.00 / 0.30 / -0.29 | -0.11 | 0.41 | 0.66 | -0.25 | 0.00 | 819 | diag |
| NQ 1 | first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | 402 | 2 | 1.86 | 0.45 | 0.71 | -0.54 / 1.43 | 0.34 / -0.04 / -0.50 | 0.08 | 0.26 | 0.92 | -0.14 | 0.75 | 669 | NO |
| NQ 2 | first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | 402 | 2 | 1.67 | 0.17 | 0.86 | 0.03 / 1.42 | 0.36 / 0.12 / -0.28 | 0.16 | 0.24 | 0.94 | -0.06 | 0.75 | 669 | NO |
| NQ 3 | first 5m (09:30-09:34) move>=0.03ADR dir=with hold=120m | 402 | 2 | 1.27 | 0.45 | 0.86 | 0.44 / 1.53 | 0.26 / 0.17 / -0.15 | 0.15 | 0.27 | 0.95 | -0.06 | 0.75 | 669 | NO |
| NQ 4 | first 5m (09:30-09:34) move>=0.0ADR dir=with hold=60m | 515 | 2 | 1.05 | 0.31 | 0.35 | -0.43 / 1.51 | 0.18 / 0.05 / -0.52 | -0.01 | 0.06 | 0.81 | -0.22 | 1.00 | 827 | NO |
| NQ 5 | first 5m (09:30-09:34) move>=0.0ADR dir=with hold=120m | 515 | 2 | 0.62 | 0.19 | 0.45 | 0.26 / 1.42 | 0.15 / 0.20 / -0.20 | 0.08 | 0.00 | 0.85 | -0.13 | 0.67 | 827 | NO |
| NQ 6 (diag) | first 5m (09:30-09:34) move>=0.0ADR dir=with hold=30m | 515 | 1 | 0.97 | -0.05 | 0.36 | -0.27 / 1.56 | 0.22 / 0.17 / -0.49 | 0.03 | 0.34 | 0.80 | -0.18 | 0.67 | 827 | diag |
| NQ 7 (diag) | first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | 515 | 0 | -0.83 | -0.57 | -0.62 | -0.41 / 1.28 | -0.23 / -0.56 / 0.02 | -0.24 | -0.00 | 0.14 | -0.44 | 0.00 | 827 | diag |
| NQ 8 (diag) | first 5m (09:30-09:34) move>=0.0ADR dir=against hold=60m | 515 | 0 | -1.30 | -0.76 | -0.57 | 0.25 / 1.40 | -0.29 / -0.30 / 0.33 | -0.18 | -0.06 | 0.19 | -0.39 | 0.00 | 827 | diag |
| RTY 1 | first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | 434 | 2 | 0.51 | -0.84 | 0.13 | -0.29 / 1.37 | 0.05 / -0.94 / 0.47 | -0.05 | -0.38 | 0.77 | -0.20 | 0.00 | 695 | NO |
| RTY 2 | first 5m (09:30-09:34) move>=0.03ADR dir=against hold=60m | 434 | 2 | 0.49 | -0.79 | -0.30 | -1.41 / 1.37 | 0.04 / -0.96 / 0.12 | -0.14 | -0.50 | 0.49 | -0.29 | 0.00 | 695 | NO |
| RTY 3 | first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | 509 | 2 | 0.47 | -1.03 | 0.06 | -0.42 / 1.09 | 0.04 / -0.80 / 0.29 | -0.07 | -0.23 | 0.72 | -0.22 | 0.00 | 820 | NO |
| RTY 4 (diag) | first 5m (09:30-09:34) move>=0.0ADR dir=against hold=30m | 509 | 1 | 0.78 | -0.99 | -0.31 | -1.79 / 0.92 | 0.11 / -0.69 / -0.37 | -0.16 | -0.15 | 0.65 | -0.30 | 0.00 | 820 | diag |
| RTY 5 (diag) | first 5m (09:30-09:34) move>=0.0ADR dir=against hold=60m | 509 | 1 | 0.48 | -0.92 | -0.53 | -1.94 / 0.98 | 0.03 / -0.87 / -0.20 | -0.20 | -0.43 | 0.34 | -0.35 | 0.00 | 820 | diag |
| RTY 6 (diag) | first 5m (09:30-09:34) move>=0.03ADR dir=against hold=30m | 434 | 1 | 0.47 | -0.87 | -0.35 | -1.42 / 1.26 | 0.05 / -0.79 / -0.17 | -0.17 | -0.16 | 0.55 | -0.31 | 0.00 | 695 | diag |
| YM 1 | first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | 511 | 2 | 0.52 | -0.42 | 0.69 | 0.94 / 1.24 | 0.13 / -0.30 / 0.22 | 0.08 | -0.18 | 0.92 | -0.11 | 0.67 | 822 | NO |
| YM 2 | first 5m (09:30-09:34) move>=0.0ADR dir=against hold=60m | 511 | 2 | 0.43 | -0.42 | 0.61 | 0.84 / 1.13 | 0.08 / -0.31 / 0.26 | 0.04 | -0.27 | 0.94 | -0.15 | 1.00 | 822 | NO |
| YM 3 (diag) | first 5m (09:30-09:34) move>=0.0ADR dir=against hold=30m | 511 | 1 | 0.29 | -0.43 | 0.67 | 1.18 / 1.21 | 0.02 / -0.07 / 0.37 | 0.03 | 0.24 | 0.98 | -0.11 | 0.67 | 822 | diag |
| YM 4 (diag) | first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | 423 | 1 | 0.00 | -0.55 | 0.68 | 1.41 / 1.50 | 0.05 / -0.23 / 0.44 | 0.10 | -0.45 | 0.96 | -0.10 | 0.50 | 688 | diag |
| YM 5 (diag) | first 5m (09:30-09:34) move>=0.03ADR dir=against hold=30m | 423 | 1 | -0.03 | -0.59 | 0.62 | 1.42 / 1.13 | -0.02 / -0.11 / 0.54 | 0.04 | -0.07 | 0.96 | -0.11 | 0.75 | 688 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 11 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 4 |
| worst-decile corr <= +0.30 | 19 |
| plateau >= 0.75 | 6 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | clean | 0.40 | 0.54 | -149241 | -115112 | 555652 | -292145 | 0.65 | 46.7 | 1.52 | -94253 | 302955 | -109183 |
| ES first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | H1 | 0.20 | 0.28 | -146303 | -131577 | 437038 | -152613 | 0.12 | 50.0 | 3.15 | -73169 | 145779 | -80050 |
| ES first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | H2 | -1.91 | -2.25 | -171683 | -150331 | 888323 | -187954 | -0.84 | 66.7 | 1.89 | -90667 | 228961 | -91287 |
| ES first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | all | -0.21 | -0.28 | -165044 | -136406 | 1196110 | -292145 | -0.28 | 51.2 | 1.82 | -92203 | 302955 | -109183 |
| NQ first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | clean | 1.62 | 3.12 | -96653 | -83209 | 499953 | -114237 | 2.95 | 45.7 | 1.82 | -85514 | 247952 | -95675 |
| NQ first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | H1 | 0.31 | 0.47 | -135103 | -126640 | 363434 | -140886 | 0.27 | 46.4 | 2.95 | -82131 | 165672 | -102796 |
| NQ first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | H2 | -0.15 | -0.19 | -240120 | -181158 | 739647 | -342401 | -0.10 | 55.6 | 2.20 | -104395 | 236767 | -128685 |
| NQ first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | all | 0.86 | 1.31 | -148278 | -125286 | 739647 | -342401 | 2.03 | 47.6 | 2.08 | -91630 | 247952 | -128685 |
| RTY first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | clean | 0.44 | 0.68 | -110160 | -100322 | 483674 | -138438 | 0.83 | 47.6 | 1.51 | -86002 | 330417 | -99034 |
| RTY first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | H1 | -2.68 | -2.92 | -149858 | -141270 | 784153 | -172132 | -1.00 | 67.9 | 1.88 | -81061 | 206261 | -102449 |
| RTY first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | H2 | 1.75 | 2.89 | -139183 | -108742 | 359645 | -173363 | 1.65 | 41.7 | 2.96 | -88657 | 209788 | -90164 |
| RTY first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | all | 0.13 | 0.19 | -130566 | -116296 | 937778 | -173363 | 0.23 | 49.4 | 1.89 | -88420 | 330417 | -102449 |
| YM first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | clean | 0.48 | 0.73 | -118164 | -98083 | 560074 | -152763 | 0.77 | 49.5 | 1.59 | -81587 | 264789 | -99181 |
| YM first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | H1 | 0.87 | 1.37 | -187115 | -172392 | 320612 | -210330 | 1.14 | 46.4 | 2.52 | -101387 | 157005 | -111067 |
| YM first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | H2 | 0.98 | 1.67 | -143514 | -136153 | 445311 | -152574 | 1.08 | 47.2 | 2.70 | -96855 | 238139 | -97071 |
| YM first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | all | 0.69 | 1.09 | -151256 | -127951 | 560074 | -210330 | 2.29 | 48.2 | 2.02 | -91964 | 264789 | -111067 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | -33.6 | -21.0 | -2.2 | 15.5 | -22.0 / -7.0 | 25.2 / 31.5 | NO |
| NQ first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | -13.6 | -75.5 | 2.4 | 14.5 | 3.4 / 15.3 | -18.3 / 9.1 | NO |
| RTY first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | -27.7 | -11.6 | 7.8 | 3.1 | -6.2 / 10.0 | -17.7 / 5.8 | NO |
| YM first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | -16.0 | -26.0 | 3.0 | 33.7 | -6.2 / 23.0 | -32.8 / -16.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | gross-positive, cost-negative pre-2023 | 1981 | 20.7 | -8.7 | 5.6 | 29.4 | 0.49 / -0.21 / 0.13 | 57.0 / 27.7 |
| ES 2 (diag) first 5m (09:30-09:34) move>=0.03ADR dir=with hold=120m | positive pre-2023 | 1981 | 32.0 | 2.7 | 16.9 | 29.4 | 0.57 / 0.05 / 0.30 | 41.9 / 12.6 |
| ES 3 (diag) first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | gross-positive, cost-negative pre-2023 | 1981 | 4.1 | -25.3 | -11.0 | 29.4 | 0.12 / -0.76 / -0.33 | 35.0 / 5.6 |
| ES 4 (diag) first 5m (09:30-09:34) move>=0.0ADR dir=with hold=120m | gross-positive, cost-negative pre-2023 | 2593 | 23.4 | -6.0 | 8.2 | 29.4 | 0.47 / -0.12 / 0.16 | 33.3 / 4.0 |
| NQ 1 first 5m (09:30-09:34) move>=0.03ADR dir=with hold=60m | positive pre-2023 | 2113 | 47.3 | 32.9 | 41.4 | 14.4 | 0.65 / 0.45 / 0.57 | 253.6 / 239.3 |
| NQ 2 first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m | positive pre-2023 | 2113 | 24.5 | 10.2 | 18.7 | 14.4 | 0.42 / 0.17 / 0.32 | 176.1 / 161.7 |
| NQ 3 first 5m (09:30-09:34) move>=0.03ADR dir=with hold=120m | positive pre-2023 | 2113 | 54.6 | 40.2 | 48.7 | 14.4 | 0.61 / 0.45 / 0.55 | 217.5 / 203.1 |
| NQ 4 first 5m (09:30-09:34) move>=0.0ADR dir=with hold=60m | positive pre-2023 | 2654 | 33.6 | 19.2 | 27.7 | 14.4 | 0.54 / 0.31 / 0.44 | 128.2 / 113.9 |
| NQ 5 first 5m (09:30-09:34) move>=0.0ADR dir=with hold=120m | positive pre-2023 | 2654 | 29.3 | 14.9 | 23.5 | 14.4 | 0.38 / 0.19 / 0.31 | 99.5 / 85.2 |
| NQ 6 (diag) first 5m (09:30-09:34) move>=0.0ADR dir=with hold=30m | gross-positive, cost-negative pre-2023 | 2654 | 12.3 | -2.0 | 6.5 | 14.4 | 0.25 / -0.05 / 0.13 | 93.8 / 79.4 |
| NQ 7 (diag) first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | negative pre-2023 | 2654 | -29.3 | -43.6 | -35.1 | 14.4 | -0.38 / -0.57 / -0.46 | -99.5 / -113.9 |
| NQ 8 (diag) first 5m (09:30-09:34) move>=0.0ADR dir=against hold=60m | negative pre-2023 | 2654 | -33.6 | -47.9 | -39.4 | 14.4 | -0.54 / -0.76 / -0.63 | -128.2 / -142.6 |
| RTY 1 first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | negative pre-2023 | 1239 | -29.5 | -43.9 | -41.7 | 14.4 | -0.56 / -0.84 / -0.79 | 36.9 / 22.6 |
| RTY 2 first 5m (09:30-09:34) move>=0.03ADR dir=against hold=60m | negative pre-2023 | 1239 | -18.7 | -33.1 | -30.8 | 14.4 | -0.45 / -0.79 / -0.74 | 34.4 / 20.0 |
| RTY 3 first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | negative pre-2023 | 1525 | -31.7 | -46.1 | -43.8 | 14.4 | -0.71 / -1.03 / -0.98 | 32.3 / 17.9 |
| RTY 4 (diag) first 5m (09:30-09:34) move>=0.0ADR dir=against hold=30m | negative pre-2023 | 1525 | -13.4 | -27.7 | -25.5 | 14.4 | -0.47 / -0.99 / -0.91 | 37.2 / 22.9 |
| RTY 5 (diag) first 5m (09:30-09:34) move>=0.0ADR dir=against hold=60m | negative pre-2023 | 1525 | -18.4 | -32.7 | -30.5 | 14.4 | -0.52 / -0.92 / -0.85 | 31.3 / 17.0 |
| RTY 6 (diag) first 5m (09:30-09:34) move>=0.03ADR dir=against hold=30m | negative pre-2023 | 1239 | -13.7 | -28.1 | -25.9 | 14.4 | -0.42 / -0.87 / -0.80 | 28.6 / 14.3 |
| YM 1 first 5m (09:30-09:34) move>=0.0ADR dir=against hold=120m | negative pre-2023 | 2648 | -1.6 | -15.9 | -10.2 | 14.4 | -0.04 / -0.42 / -0.27 | 36.8 / 22.5 |
| YM 2 first 5m (09:30-09:34) move>=0.0ADR dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2648 | 2.1 | -12.3 | -6.6 | 14.4 | 0.07 / -0.42 / -0.23 | 29.6 / 15.3 |
| YM 3 (diag) first 5m (09:30-09:34) move>=0.0ADR dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2649 | 4.5 | -9.8 | -4.1 | 14.4 | 0.20 / -0.43 / -0.18 | 22.5 / 8.1 |
| YM 4 (diag) first 5m (09:30-09:34) move>=0.03ADR dir=against hold=120m | negative pre-2023 | 2075 | -10.1 | -24.4 | -18.8 | 14.4 | -0.23 / -0.55 / -0.42 | 14.1 / -0.3 |
| YM 5 (diag) first 5m (09:30-09:34) move>=0.03ADR dir=against hold=30m | negative pre-2023 | 2076 | -1.0 | -15.3 | -9.6 | 14.4 | -0.04 / -0.59 / -0.37 | 12.8 / -1.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 1 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 0.70, p(top) = 0.50); NQ: 5 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.06, p(top) = 0.05); RTY: 3 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.23, p(top) = 0.56); YM: 2 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.47, p(top) = 0.56).
- Of 11 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.18 (NQ first 5m (09:30-09:34) move>=0.03ADR dir=with hold=30m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 5; 2x-slippage all-in uplift >= +0.10 for 2; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 5, 'negative pre-2023': 4, 'gross-positive, cost-negative pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_9.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj9/ (`BJ9_CO_all_selected_scored.csv`).

DONE BJ9
