# REPORT BJ4 - open location vs prior-day range (BJ batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 5 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.11; best pair-window standalone Sharpe +0.88.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. open location vs prior-day range. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |       8 |          8 |         1 |               0.516 |                2 |          1 |            3 |
| NQ    |       8 |          8 |         2 |               0.627 |                2 |          2 |            3 |
| RTY   |       8 |          8 |         2 |               1.13  |                2 |          2 |            3 |
| YM    |       8 |          4 |         0 |               0.454 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            1.405 |               4 |      0.775 |                       0.39  |            0.755 |           1.483 |    0.655 |       0.39  |                1.739 |
| NQ    |     200 |                    2 |            1.89  |               5 |      0.62  |                       0.604 |            0.795 |           1.287 |    0.66  |       0.627 |                1.703 |
| RTY   |     200 |                    2 |            1.31  |               4 |      0.35  |                       0.997 |            0.786 |           1.557 |    0.195 |       1.13  |                1.632 |
| YM    |     200 |                    0 |            1.57  |               5 |      1     |                     nan     |            0.747 |           1.307 |  nan     |     nan     |                1.678 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | 158 | 2 | 0.39 | -0.55 | 0.34 | 0.16 / 1.29 | 0.09 / -0.01 / -0.13 | 0.01 | 0.20 | 0.83 | -0.14 | 0.67 | 257 | NO |
| ES 2 (diag) | RTH open beyond prior-day high/low by 0.0ADR dir=against hold=flat | 158 | 1 | 0.52 | -0.16 | 0.45 | 0.16 / 1.22 | 0.11 / 0.04 / -0.10 | 0.04 | -0.36 | 0.90 | -0.10 | 0.00 | 257 | diag |
| ES 3 (diag) | RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | 116 | 1 | 0.34 | -0.59 | 0.29 | 0.08 / 1.48 | 0.09 / -0.03 / -0.23 | -0.00 | -0.21 | 0.81 | -0.14 | 0.75 | 184 | diag |
| ES 4 (diag) | RTH open beyond prior-day high/low by 0.1ADR dir=against hold=flat | 116 | 1 | 0.04 | -0.14 | 0.14 | 0.11 / 1.40 | 0.02 / 0.00 / -0.19 | -0.02 | -0.41 | 0.68 | -0.17 | 0.00 | 184 | diag |
| NQ 1 | RTH open beyond prior-day high/low by 0.1ADR dir=against hold=flat | 104 | 2 | 0.63 | 0.10 | 0.39 | -0.04 / 1.38 | 0.17 / 0.15 / -0.25 | 0.09 | -0.30 | 0.86 | -0.09 | 0.50 | 176 | NO |
| NQ 2 | RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | 104 | 2 | 0.58 | -0.04 | 0.48 | 0.23 / 1.37 | 0.16 / -0.09 / -0.02 | 0.10 | -0.06 | 0.80 | -0.08 | 1.00 | 176 | NO |
| NQ 3 (diag) | RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | 174 | 1 | 0.25 | 0.24 | 0.31 | 0.21 / 1.35 | 0.11 / 0.20 / -0.13 | 0.08 | -0.09 | 0.71 | -0.10 | 1.00 | 284 | diag |
| NQ 4 (diag) | RTH open beyond prior-day high/low by 0.0ADR dir=against hold=flat | 174 | 1 | -0.01 | 0.14 | -0.04 | -0.31 / 1.34 | 0.05 / 0.13 / -0.20 | 0.01 | -0.18 | 0.49 | -0.15 | 1.00 | 284 | diag |
| NQ 5 (diag) | RTH open beyond prior-day high/low by 0.0ADR dir=with hold=flat | 174 | 1 | -0.06 | -0.27 | -0.02 | 0.25 / 1.54 | -0.11 / -0.27 / 0.05 | -0.11 | 0.19 | 0.48 | -0.28 | 0.00 | 284 | diag |
| RTY 1 | RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | 111 | 2 | 1.13 | -0.36 | 0.57 | -0.27 / 1.36 | 0.16 / -0.32 / 0.02 | 0.04 | -0.44 | 0.90 | -0.13 | 0.75 | 178 | NO |
| RTY 2 | RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | 164 | 2 | 0.86 | -0.19 | 0.63 | 0.24 / 1.59 | 0.11 / -0.34 / 0.12 | 0.03 | -0.42 | 0.93 | -0.14 | 1.00 | 264 | NO |
| RTY 3 (diag) | RTH open beyond prior-day high/low by 0.1ADR dir=against hold=flat | 111 | 1 | 1.08 | 0.15 | 0.88 | 0.52 / 1.44 | 0.16 / 0.01 / 0.12 | 0.12 | -0.67 | 0.97 | -0.05 | 1.00 | 178 | diag |
| RTY 4 (diag) | RTH open beyond prior-day high/low by 0.0ADR dir=against hold=flat | 164 | 1 | 0.67 | 0.18 | 0.81 | 0.97 / 1.29 | 0.10 / -0.05 / 0.25 | 0.10 | -0.70 | 0.96 | -0.06 | 1.00 | 264 | diag |
| RTY 5 (diag) | RTH open beyond prior-day high/low by 0.0ADR dir=with hold=flat | 164 | 1 | -0.88 | -0.42 | -1.02 | -1.18 / 1.31 | -0.20 / -0.19 / -0.36 | -0.25 | 0.70 | 0.06 | -0.42 | 0.00 | 264 | diag |
| YM 1 (diag) | RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | 89 | 1 | 0.45 | -0.43 | 0.79 | 1.19 / 1.21 | 0.03 / -0.03 / 0.27 | 0.08 | -0.27 | 0.96 | -0.10 | 1.00 | 162 | diag |
| YM 2 (diag) | RTH open beyond prior-day high/low by 0.1ADR dir=against hold=flat | 89 | 1 | 0.18 | 0.10 | 0.55 | 1.25 / 1.60 | -0.02 / 0.06 / 0.21 | 0.03 | -0.42 | 0.85 | -0.10 | 0.50 | 162 | diag |
| YM 3 (diag) | RTH open beyond prior-day high/low by 0.0ADR dir=with hold=flat | 143 | 1 | 0.05 | -0.36 | -0.26 | -0.92 / 1.62 | -0.02 / 0.07 / -0.24 | -0.07 | 0.37 | 0.30 | -0.24 | 0.00 | 237 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 5 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 13 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 3 |
| worst-decile corr <= +0.30 | 15 |
| plateau >= 0.75 | 9 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | clean | 0.45 | 0.69 | -133520 | -106753 | 322810 | -171448 | 1.27 | 39.0 | 1.55 | -86570 | 256835 | -92928 |
| ES RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | H1 | 0.88 | 1.46 | -93622 | -89030 | 172695 | -98615 | 1.10 | 42.9 | 2.82 | -82335 | 148830 | -98010 |
| ES RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | H2 | -0.26 | -0.37 | -160589 | -121821 | 593506 | -167448 | -0.16 | 50.0 | 2.35 | -95180 | 251808 | -95651 |
| ES RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | all | 0.34 | 0.52 | -135657 | -108562 | 593506 | -171448 | 0.85 | 42.3 | 1.94 | -90174 | 256835 | -98010 |
| NQ RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | clean | 0.68 | 1.11 | -120560 | -101643 | 423902 | -131226 | 1.46 | 33.3 | 1.62 | -82636 | 233648 | -92870 |
| NQ RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | H1 | 0.68 | 1.22 | -123256 | -109440 | 283169 | -126394 | 0.69 | 32.1 | 2.74 | -85236 | 160674 | -102311 |
| NQ RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | H2 | -0.07 | -0.10 | -170940 | -151558 | 551689 | -179254 | -0.05 | 41.7 | 2.47 | -90513 | 211693 | -101287 |
| NQ RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | all | 0.48 | 0.77 | -138947 | -118385 | 551689 | -179254 | 1.42 | 34.5 | 2.00 | -86573 | 233648 | -102311 |
| RTY RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | clean | 1.19 | 1.92 | -130922 | -109220 | 461876 | -137816 | 2.33 | 23.8 | 1.62 | -84884 | 242581 | -92811 |
| RTY RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | H1 | -0.58 | -0.73 | -189889 | -155494 | 424442 | -288106 | -0.43 | 39.3 | 2.50 | -72579 | 144900 | -88281 |
| RTY RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | H2 | 0.00 | 0.00 | -129673 | -114673 | 483220 | -151623 | 0.00 | 41.7 | 2.50 | -83114 | 246660 | -89081 |
| RTY RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | all | 0.57 | 0.85 | -148109 | -121924 | 483220 | -288106 | 1.86 | 30.4 | 1.96 | -84972 | 246660 | -92811 |
| YM RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m (diag) | clean | 0.45 | 0.71 | -135483 | -102878 | 518389 | -215138 | 0.79 | 32.4 | 1.49 | -83384 | 244315 | -88235 |
| YM RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m (diag) | H1 | 0.74 | 1.17 | -166115 | -138783 | 344786 | -233809 | 0.67 | 17.9 | 2.80 | -85843 | 151713 | -95111 |
| YM RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m (diag) | H2 | 1.48 | 2.57 | -140271 | -135957 | 239627 | -141913 | 2.94 | 33.3 | 2.75 | -95920 | 257509 | -105798 |
| YM RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m (diag) | all | 0.79 | 1.27 | -158598 | -124433 | 518389 | -233809 | 2.59 | 30.4 | 1.99 | -87473 | 257509 | -105798 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | -24.5 | -2.3 | 5.5 | 27.3 | 2.3 / 9.1 | -7.8 / 20.9 | NO |
| NQ RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | -21.4 | -10.1 | 14.7 | 38.9 | 5.1 / 21.0 | -16.0 / 15.3 | NO |
| RTY RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | -20.2 | 6.0 | 14.3 | 30.0 | 5.2 / 14.9 | 10.9 / 25.3 | NO |
| YM RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m (diag) | -15.3 | -17.3 | 7.4 | 24.2 | -13.7 / 13.1 | -2.2 / 14.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | negative pre-2023 | 902 | -18.3 | -47.6 | -33.6 | 29.4 | -0.21 / -0.55 / -0.39 | 102.0 / 72.6 |
| ES 2 (diag) RTH open beyond prior-day high/low by 0.0ADR dir=against hold=flat | gross-positive, cost-negative pre-2023 | 902 | 7.6 | -21.7 | -7.7 | 29.4 | 0.05 / -0.16 / -0.06 | 181.3 / 152.0 |
| ES 3 (diag) RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | negative pre-2023 | 630 | -33.4 | -62.8 | -48.7 | 29.4 | -0.31 / -0.59 / -0.46 | 108.5 / 79.2 |
| ES 4 (diag) RTH open beyond prior-day high/low by 0.1ADR dir=against hold=flat | gross-positive, cost-negative pre-2023 | 630 | 6.2 | -23.1 | -9.1 | 29.4 | 0.04 / -0.14 / -0.05 | 74.0 / 44.7 |
| NQ 1 RTH open beyond prior-day high/low by 0.1ADR dir=against hold=flat | positive pre-2023 | 606 | 43.8 | 29.5 | 37.9 | 14.4 | 0.15 / 0.10 / 0.13 | 470.5 / 456.1 |
| NQ 2 RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | gross-positive, cost-negative pre-2023 | 606 | 7.0 | -7.4 | 1.0 | 14.4 | 0.04 / -0.04 / 0.01 | 284.1 / 269.8 |
| NQ 3 (diag) RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | positive pre-2023 | 865 | 49.8 | 35.4 | 43.9 | 14.4 | 0.33 / 0.24 / 0.29 | 127.2 / 112.9 |
| NQ 4 (diag) RTH open beyond prior-day high/low by 0.0ADR dir=against hold=flat | positive pre-2023 | 865 | 46.8 | 32.4 | 40.9 | 14.4 | 0.21 / 0.14 / 0.18 | 75.5 / 61.1 |
| NQ 5 (diag) RTH open beyond prior-day high/low by 0.0ADR dir=with hold=flat | negative pre-2023 | 865 | -46.8 | -61.1 | -52.7 | 14.4 | -0.21 / -0.27 / -0.24 | -75.5 / -89.8 |
| RTY 1 RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | negative pre-2023 | 295 | -24.4 | -38.8 | -36.5 | 14.4 | -0.23 / -0.36 / -0.34 | 141.4 / 127.0 |
| RTY 2 RTH open beyond prior-day high/low by 0.0ADR dir=against hold=120m | negative pre-2023 | 488 | -1.2 | -15.5 | -13.4 | 14.4 | -0.01 / -0.19 / -0.16 | 91.4 / 77.1 |
| RTY 3 (diag) RTH open beyond prior-day high/low by 0.1ADR dir=against hold=flat | positive pre-2023 | 295 | 38.3 | 24.0 | 26.2 | 14.4 | 0.24 / 0.15 / 0.17 | 186.1 / 171.7 |
| RTY 4 (diag) RTH open beyond prior-day high/low by 0.0ADR dir=against hold=flat | positive pre-2023 | 488 | 36.2 | 21.8 | 24.0 | 14.4 | 0.30 / 0.18 / 0.20 | 107.8 / 93.5 |
| RTY 5 (diag) RTH open beyond prior-day high/low by 0.0ADR dir=with hold=flat | negative pre-2023 | 488 | -36.2 | -50.5 | -48.4 | 14.4 | -0.30 / -0.42 / -0.40 | -107.8 / -122.2 |
| YM 1 (diag) RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m | negative pre-2023 | 664 | -21.7 | -36.1 | -30.4 | 14.4 | -0.26 / -0.43 / -0.36 | 83.5 / 69.1 |
| YM 2 (diag) RTH open beyond prior-day high/low by 0.1ADR dir=against hold=flat | positive pre-2023 | 664 | 27.9 | 13.5 | 19.3 | 14.4 | 0.20 / 0.10 / 0.14 | 72.0 / 57.6 |
| YM 3 (diag) RTH open beyond prior-day high/low by 0.0ADR dir=with hold=flat | negative pre-2023 | 937 | -26.0 | -40.3 | -34.6 | 14.4 | -0.23 / -0.36 / -0.31 | 25.3 / 10.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 1 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.78, p(top) = 0.66); NQ: 2 cells pass the clean rule against a replicate mean of 1.9 (p(count) = 0.62, p(top) = 0.66); RTY: 2 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.35, p(top) = 0.20); YM: 0 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 1.00).
- Of 5 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.11 (NQ RTH open beyond prior-day high/low by 0.1ADR dir=against hold=120m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 3, 'positive pre-2023': 1, 'gross-positive, cost-negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_4.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj4/ (`BJ4_CO_all_selected_scored.csv`).

DONE BJ4
