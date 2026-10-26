# REPORT BI3 - intraday NQ/ES relative-move mean reversion (BI batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 20 selected cells (+10 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.26; best pair-window standalone Sharpe +1.38.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BI', before the first run)
- Rule: see IDEAS_BI.md / PREREG_AUTOPILOT.md BATCH BI (frozen before the first run). intraday NQ/ES relative-move mean reversion
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      36 |         24 |         7 |               1.412 |                2 |          7 |            3 |
| NQ    |      36 |         24 |         9 |               2.145 |                2 |          9 |            1 |
| RTY   |      36 |         36 |         2 |               0.865 |                2 |          2 |            3 |
| YM    |      36 |         36 |         2 |               0.888 |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    7 |            0.595 |               3 |      0     |                       1.086 |            0.559 |           1.106 |    0.035 |       1.412 |                1.295 |
| NQ    |     200 |                    9 |            3.735 |               8 |      0     |                       1.53  |            0.704 |           1.104 |    0.01  |       2.145 |                1.642 |
| RTY   |     200 |                    2 |            0.22  |               2 |      0.02  |                       0.67  |            0.475 |           1.039 |    0.06  |       0.865 |                1.039 |
| YM    |     200 |                    2 |            1.26  |               4 |      0.345 |                       0.525 |            0.584 |           1.062 |    0.345 |       0.551 |                1.308 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | L=30m |own-drv z|>=1.5 dir=against(convergence) hold=30m | 463 | 2 | 1.41 | -1.21 | 0.49 | -0.77 / 0.05 | 0.24 / 0.15 / -0.46 | -0.05 | 0.52 | 1.00 | -0.12 | 0.33 | 715 | NO |
| ES 2 | L=30m |own-drv z|>=2.5 dir=against(convergence) hold=30m | 116 | 2 | 1.39 | -0.88 | 0.71 | -0.14 / 0.82 | 0.23 / 0.23 / -0.32 | 0.04 | 0.17 | 1.00 | -0.09 | 0.50 | 181 | NO |
| ES 3 | L=30m |own-drv z|>=1.5 dir=against(convergence) hold=60m | 392 | 2 | 1.37 | -0.80 | 1.16 | 0.68 / 0.20 | 0.26 / 0.08 / 0.12 | 0.11 | 0.14 | 1.00 | 0.01 | 0.67 | 610 | NO |
| ES 4 | L=120m |own-drv z|>=1.5 dir=against(convergence) hold=60m | 153 | 2 | 1.14 | -0.51 | 0.73 | 0.24 / 0.52 | 0.22 / 0.07 / -0.14 | 0.04 | 0.16 | 1.00 | -0.08 | 0.33 | 243 | NO |
| ES 5 | L=30m |own-drv z|>=2.5 dir=against(convergence) hold=15m | 130 | 2 | 1.12 | -1.08 | 0.57 | 0.26 / 0.36 | 0.17 / 0.01 / -0.26 | -0.05 | 0.22 | 1.00 | -0.14 | 0.67 | 201 | NO |
| ES 6 | L=30m |own-drv z|>=2.5 dir=against(convergence) hold=60m | 114 | 2 | 0.73 | -0.55 | 0.28 | -0.42 / 0.82 | 0.10 / 0.24 / -0.42 | -0.05 | -0.00 | 0.97 | -0.18 | 1.00 | 174 | NO |
| ES 7 | L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | 265 | 2 | 0.44 | -0.91 | 0.27 | 0.03 / 0.35 | 0.03 / 0.22 / -0.18 | -0.09 | 0.05 | 0.99 | -0.20 | 0.67 | 405 | NO |
| ES 8 (diag) | L=120m |own-drv z|>=1.5 dir=against(convergence) hold=30m | 190 | 1 | 0.71 | -1.03 | 0.29 | -0.29 / 0.54 | 0.13 / -0.15 / -0.08 | -0.07 | 0.56 | 0.99 | -0.16 | 0.17 | 297 | diag |
| ES 9 (diag) | L=30m |own-drv z|>=1.5 dir=against(convergence) hold=15m | 560 | 1 | 0.58 | -1.68 | -0.26 | -1.26 / -0.56 | 0.07 / 0.13 / -0.81 | -0.32 | 0.42 | 1.00 | -0.31 | 0.00 | 874 | diag |
| ES 10 (diag) | L=60m |own-drv z|>=2.5 dir=against(convergence) hold=30m | 54 | 1 | 0.43 | -0.41 | 0.32 | 0.21 / 0.75 | 0.03 / 0.08 / -0.07 | -0.04 | -0.12 | 0.98 | -0.20 | 0.17 | 89 S | diag |
| NQ 1 | L=30m |own-drv z|>=2.5 dir=with(own rel move) hold=30m | 116 | 2 | 2.15 | -0.11 | 1.24 | 0.35 / 1.26 | 0.38 / 0.44 / -0.24 | 0.23 | 0.20 | 1.00 | 0.03 | 0.50 | 181 | NO |
| NQ 2 | L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=30m | 463 | 2 | 1.88 | -0.00 | 0.78 | -0.50 / 1.02 | 0.33 / 0.27 / -0.54 | 0.11 | 0.51 | 0.99 | -0.09 | 0.67 | 715 | NO |
| NQ 3 | L=30m |own-drv z|>=2.5 dir=with(own rel move) hold=15m | 130 | 2 | 1.83 | 0.12 | 0.94 | 0.39 / 1.20 | 0.32 / 0.36 / -0.33 | 0.17 | 0.20 | 0.98 | -0.05 | 0.67 | 201 | NO |
| NQ 4 | L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | 392 | 2 | 1.61 | 0.04 | 1.38 | 0.97 / 1.23 | 0.31 / 0.06 / 0.20 | 0.24 | 0.17 | 1.00 | 0.05 | 0.83 | 610 | NO |
| NQ 5 | L=120m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | 153 | 2 | 1.58 | 0.32 | 1.05 | 0.66 / 1.19 | 0.29 / 0.28 / -0.08 | 0.19 | 0.10 | 1.00 | -0.01 | 0.50 | 243 | NO |
| NQ 6 | L=30m |own-drv z|>=2.5 dir=with(own rel move) hold=60m | 114 | 2 | 1.42 | 0.07 | 0.77 | 0.11 / 1.34 | 0.23 / 0.36 / -0.38 | 0.10 | 0.04 | 0.93 | -0.10 | 1.00 | 174 | NO |
| NQ 7 | L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=15m | 560 | 2 | 1.41 | 0.00 | 0.63 | -0.19 / 0.80 | 0.25 / 0.40 / -0.59 | 0.05 | 0.55 | 0.99 | -0.14 | 0.50 | 874 | NO |
| NQ 8 | L=60m |own-drv z|>=1.5 dir=with(own rel move) hold=30m | 315 | 2 | 1.03 | 0.05 | 0.80 | 0.53 / 1.07 | 0.12 / 0.42 / 0.02 | 0.10 | 0.50 | 0.99 | -0.07 | 0.50 | 492 | NO |
| NQ 9 | L=60m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | 265 | 2 | 0.86 | -0.12 | 0.74 | 0.61 / 1.23 | 0.12 / 0.18 / 0.07 | 0.09 | -0.20 | 0.97 | -0.10 | 0.50 | 405 | NO |
| NQ 10 (diag) | L=120m |own-drv z|>=1.5 dir=with(own rel move) hold=30m | 190 | 1 | 1.08 | 0.17 | 0.65 | 0.22 / 1.42 | 0.19 / 0.15 / -0.16 | 0.09 | 0.58 | 0.94 | -0.11 | 0.67 | 297 | diag |
| RTY 1 | L=60m |own-drv z|>=2.5 dir=against(convergence) hold=60m | 467 | 2 | 0.87 | -0.79 | 0.02 | -1.02 / 0.86 | 0.11 / -0.52 / -0.37 | -0.14 | -0.29 | 0.94 | -0.28 | 0.00 | 708 | NO |
| RTY 2 | L=120m |own-drv z|>=2.5 dir=against(convergence) hold=60m | 328 | 2 | 0.47 | -0.63 | -0.03 | -0.98 / 0.80 | 0.01 / -0.33 / -0.29 | -0.15 | -0.25 | 0.92 | -0.27 | 0.00 | 500 | NO |
| RTY 3 (diag) | L=60m |own-drv z|>=2.5 dir=against(convergence) hold=30m | 589 | 1 | 0.78 | -1.14 | -0.22 | -1.57 / 0.10 | 0.14 / -0.01 / -0.75 | -0.19 | 0.07 | 0.98 | -0.29 | 0.00 | 888 | diag |
| RTY 4 (diag) | L=30m |own-drv z|>=2.5 dir=against(convergence) hold=60m | 579 | 1 | 0.76 | -0.98 | -0.42 | -2.13 / 0.48 | 0.09 / -0.72 / -0.55 | -0.23 | -0.33 | 0.91 | -0.36 | 0.00 | 874 | diag |
| RTY 5 (diag) | L=120m |own-drv z|>=2.5 dir=against(convergence) hold=30m | 407 | 1 | 0.18 | -1.73 | -0.34 | -1.10 / 0.57 | -0.02 / -0.17 / -0.41 | -0.21 | -0.00 | 0.93 | -0.32 | 0.00 | 622 | diag |
| YM 1 | L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | 570 | 2 | 0.55 | -0.28 | 0.28 | -0.09 / 0.99 | 0.07 / -0.75 / 0.21 | -0.07 | -0.20 | 0.96 | -0.20 | 0.00 | 944 | NO |
| YM 2 | L=30m |own-drv z|>=2.5 dir=against(convergence) hold=60m | 318 | 2 | 0.50 | -0.18 | 0.33 | 0.12 / 1.32 | 0.04 / -0.66 / 0.21 | -0.06 | -0.13 | 0.86 | -0.20 | 0.00 | 534 | NO |
| YM 3 (diag) | L=30m |own-drv z|>=2.5 dir=against(convergence) hold=30m | 377 | 1 | 0.89 | -0.21 | -0.01 | -1.16 / 0.93 | 0.13 / -0.74 / -0.13 | -0.12 | 0.22 | 0.85 | -0.25 | 0.00 | 637 | diag |
| YM 4 (diag) | L=120m |own-drv z|>=1.5 dir=against(convergence) hold=60m | 443 | 1 | 0.19 | 0.02 | -0.36 | -1.16 / 0.82 | 0.01 / -0.43 / -0.34 | -0.18 | -0.10 | 0.68 | -0.31 | 0.00 | 743 | diag |
| YM 5 (diag) | L=120m |own-drv z|>=1.5 dir=against(convergence) hold=30m | 556 | 1 | 0.01 | -0.31 | -0.55 | -1.32 / 0.73 | -0.02 / -0.39 / -0.44 | -0.24 | -0.06 | 0.71 | -0.36 | 0.00 | 930 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 20 |
| diagnostic cells read | 10 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 19 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 3 |
| standalone pair-window Sharpe above own random-entry null p95 | 20 |
| worst-decile corr <= +0.30 | 23 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 7 |
| small-sample (<100 trades pair window) | 1 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES L=30m |own-drv z|>=1.5 dir=against(convergence) hold=60m | clean | 1.48 | 2.52 | -120681 | -101348 | 462362 | -172151 | 2.96 | 44.8 | 1.72 | -90156 | 248999 | -105402 |
| ES L=30m |own-drv z|>=1.5 dir=against(convergence) hold=60m | H1 | 0.97 | 1.90 | -105636 | -90031 | 177944 | -130152 | 1.52 | 42.9 | 2.91 | -79723 | 144613 | -82513 |
| ES L=30m |own-drv z|>=1.5 dir=against(convergence) hold=60m | H2 | 0.46 | 0.65 | -163781 | -136137 | 596863 | -172587 | 0.29 | 41.7 | 2.60 | -88623 | 228309 | -98100 |
| ES L=30m |own-drv z|>=1.5 dir=against(convergence) hold=60m | all | 1.16 | 1.89 | -133636 | -112660 | 596863 | -172587 | 3.03 | 44.0 | 2.11 | -88966 | 248999 | -105402 |
| NQ L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | clean | 1.71 | 2.95 | -116832 | -94514 | 466773 | -188210 | 3.38 | 41.9 | 1.77 | -90339 | 229694 | -104182 |
| NQ L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | H1 | 0.68 | 1.13 | -88215 | -84324 | 185076 | -89348 | 0.75 | 46.4 | 2.89 | -79452 | 146379 | -81971 |
| NQ L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | H2 | 1.14 | 1.68 | -249518 | -175828 | 545071 | -258840 | 1.03 | 30.6 | 2.69 | -89854 | 227011 | -96332 |
| NQ L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | all | 1.38 | 2.20 | -146419 | -115747 | 545071 | -258840 | 4.18 | 40.5 | 2.15 | -89301 | 229694 | -104182 |
| RTY L=60m |own-drv z|>=2.5 dir=against(convergence) hold=60m | clean | 0.78 | 1.29 | -105069 | -93519 | 434137 | -124236 | 1.65 | 44.8 | 1.57 | -88846 | 308625 | -98276 |
| RTY L=60m |own-drv z|>=2.5 dir=against(convergence) hold=60m | H1 | -1.24 | -1.46 | -159537 | -142081 | 648770 | -181245 | -0.53 | 50.0 | 2.31 | -86014 | 185428 | -104498 |
| RTY L=60m |own-drv z|>=2.5 dir=against(convergence) hold=60m | H2 | -0.86 | -1.14 | -139681 | -127736 | 491662 | -157062 | -0.69 | 52.8 | 2.11 | -99795 | 232301 | -101607 |
| RTY L=60m |own-drv z|>=2.5 dir=against(convergence) hold=60m | all | 0.02 | 0.03 | -130911 | -117035 | 906225 | -181245 | 0.04 | 47.6 | 1.82 | -93363 | 308625 | -104498 |
| YM L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | clean | 0.55 | 0.83 | -136873 | -107908 | 450038 | -190806 | 1.10 | 41.9 | 1.53 | -89206 | 307226 | -104872 |
| YM L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | H1 | -1.91 | -2.41 | -148041 | -131458 | 588181 | -157032 | -0.93 | 64.3 | 2.08 | -86912 | 184676 | -87175 |
| YM L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | H2 | 1.35 | 2.54 | -96796 | -89506 | 280236 | -104557 | 1.73 | 52.8 | 2.69 | -86407 | 208900 | -87475 |
| YM L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | all | 0.28 | 0.42 | -135764 | -112640 | 897387 | -190806 | 0.48 | 48.2 | 1.88 | -88729 | 307226 | -104872 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES L=30m |own-drv z|>=1.5 dir=against(convergence) hold=60m | -10.2 | -12.2 | 10.5 | 23.6 | -13.1 / 8.0 | 21.9 / 25.9 | NO |
| NQ L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | -5.1 | -10.0 | 8.7 | 20.2 | -10.9 / 7.0 | 22.9 / 26.4 | NO |
| RTY L=60m |own-drv z|>=2.5 dir=against(convergence) hold=60m | -29.6 | -15.4 | -4.0 | 14.7 | -4.3 / 7.2 | -21.6 / -8.0 | NO |
| YM L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | -25.3 | -16.0 | 10.8 | 15.5 | -17.0 / 8.9 | 12.6 / 12.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 L=30m |own-drv z|>=1.5 dir=against(convergence) hold=30m | gross-positive, cost-negative pre-2023 | 3008 | 5.9 | -23.5 | -9.6 | 29.4 | 0.31 / -1.21 / -0.50 | 79.7 / 50.3 |
| ES 2 L=30m |own-drv z|>=2.5 dir=against(convergence) hold=30m | negative pre-2023 | 777 | -4.5 | -33.9 | -20.6 | 29.4 | -0.12 / -0.88 / -0.53 | 113.4 / 84.0 |
| ES 3 L=30m |own-drv z|>=1.5 dir=against(convergence) hold=60m | gross-positive, cost-negative pre-2023 | 2442 | 6.6 | -22.8 | -8.8 | 29.4 | 0.23 / -0.80 / -0.31 | 103.9 / 74.5 |
| ES 4 L=120m |own-drv z|>=1.5 dir=against(convergence) hold=60m | gross-positive, cost-negative pre-2023 | 1080 | 10.3 | -19.0 | -5.5 | 29.4 | 0.28 / -0.51 / -0.15 | 99.6 / 70.2 |
| ES 5 L=30m |own-drv z|>=2.5 dir=against(convergence) hold=15m | gross-positive, cost-negative pre-2023 | 892 | 1.2 | -28.1 | -14.8 | 29.4 | 0.05 / -1.08 / -0.58 | 61.2 / 31.8 |
| ES 6 L=30m |own-drv z|>=2.5 dir=against(convergence) hold=60m | negative pre-2023 | 714 | -0.4 | -29.7 | -16.3 | 29.4 | -0.01 / -0.55 / -0.30 | 94.0 / 64.6 |
| ES 7 L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | gross-positive, cost-negative pre-2023 | 1711 | 0.1 | -29.2 | -15.5 | 29.4 | 0.00 / -0.91 / -0.48 | 53.4 / 24.0 |
| ES 8 (diag) L=120m |own-drv z|>=1.5 dir=against(convergence) hold=30m | gross-positive, cost-negative pre-2023 | 1322 | 3.5 | -25.8 | -12.3 | 29.4 | 0.14 / -1.03 / -0.49 | 60.5 / 31.1 |
| ES 9 (diag) L=30m |own-drv z|>=1.5 dir=against(convergence) hold=15m | gross-positive, cost-negative pre-2023 | 3726 | 5.5 | -23.9 | -10.0 | 29.4 | 0.40 / -1.68 / -0.72 | 40.3 / 11.0 |
| ES 10 (diag) L=60m |own-drv z|>=2.5 dir=against(convergence) hold=30m | gross-positive, cost-negative pre-2023 | 421 | 10.2 | -19.2 | -6.3 | 29.4 | 0.22 / -0.41 / -0.14 | 64.1 / 34.8 |
| NQ 1 L=30m |own-drv z|>=2.5 dir=with(own rel move) hold=30m | gross-positive, cost-negative pre-2023 | 777 | 5.6 | -8.7 | -0.8 | 14.4 | 0.07 / -0.11 / -0.01 | 314.5 / 300.1 |
| NQ 2 L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=30m | gross-positive, cost-negative pre-2023 | 3007 | 14.3 | -0.0 | 8.3 | 14.4 | 0.41 / -0.00 / 0.23 | 156.4 / 142.1 |
| NQ 3 L=30m |own-drv z|>=2.5 dir=with(own rel move) hold=15m | positive pre-2023 | 892 | 20.6 | 6.2 | 14.1 | 14.4 | 0.41 / 0.12 / 0.28 | 158.3 / 143.9 |
| NQ 4 L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | positive pre-2023 | 2441 | 16.4 | 2.1 | 10.5 | 14.4 | 0.32 / 0.04 / 0.20 | 193.3 / 179.0 |
| NQ 5 L=120m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | positive pre-2023 | 1079 | 36.3 | 21.9 | 29.9 | 14.4 | 0.53 / 0.32 / 0.44 | 232.2 / 217.8 |
| NQ 6 L=30m |own-drv z|>=2.5 dir=with(own rel move) hold=60m | positive pre-2023 | 714 | 21.6 | 7.3 | 15.3 | 14.4 | 0.21 / 0.07 / 0.15 | 264.3 / 249.9 |
| NQ 7 L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=15m | positive pre-2023 | 3725 | 14.4 | 0.0 | 8.3 | 14.4 | 0.58 / 0.00 / 0.33 | 82.2 / 67.8 |
| NQ 8 L=60m |own-drv z|>=1.5 dir=with(own rel move) hold=30m | positive pre-2023 | 2140 | 16.2 | 1.9 | 10.0 | 14.4 | 0.45 / 0.05 / 0.28 | 105.0 / 90.7 |
| NQ 9 L=60m |own-drv z|>=1.5 dir=with(own rel move) hold=60m | gross-positive, cost-negative pre-2023 | 1711 | 7.1 | -7.3 | 1.0 | 14.4 | 0.12 / -0.12 / 0.02 | 115.9 / 101.6 |
| NQ 10 (diag) L=120m |own-drv z|>=1.5 dir=with(own rel move) hold=30m | positive pre-2023 | 1320 | 21.9 | 7.6 | 15.6 | 14.4 | 0.49 / 0.17 / 0.35 | 117.4 / 103.1 |
| RTY 1 L=60m |own-drv z|>=2.5 dir=against(convergence) hold=60m | negative pre-2023 | 1161 | -9.2 | -23.6 | -21.7 | 14.4 | -0.31 / -0.79 / -0.72 | 36.1 / 21.7 |
| RTY 2 L=120m |own-drv z|>=2.5 dir=against(convergence) hold=60m | negative pre-2023 | 770 | -6.5 | -20.9 | -19.2 | 14.4 | -0.20 / -0.63 / -0.58 | 29.7 / 15.3 |
| RTY 3 (diag) L=60m |own-drv z|>=2.5 dir=against(convergence) hold=30m | negative pre-2023 | 1457 | -7.9 | -22.2 | -20.4 | 14.4 | -0.41 / -1.14 / -1.05 | 26.6 / 12.2 |
| RTY 4 (diag) L=30m |own-drv z|>=2.5 dir=against(convergence) hold=60m | negative pre-2023 | 1633 | -14.3 | -28.6 | -26.6 | 14.4 | -0.50 / -0.98 / -0.92 | 35.1 / 20.8 |
| RTY 5 (diag) L=120m |own-drv z|>=2.5 dir=against(convergence) hold=30m | negative pre-2023 | 958 | -24.3 | -38.6 | -36.9 | 14.4 | -1.10 / -1.73 / -1.66 | 17.4 / 3.1 |
| YM 1 L=60m |own-drv z|>=1.5 dir=against(convergence) hold=60m | gross-positive, cost-negative pre-2023 | 1012 | 4.7 | -9.6 | -5.1 | 14.4 | 0.14 / -0.28 / -0.15 | 32.4 / 18.1 |
| YM 2 L=30m |own-drv z|>=2.5 dir=against(convergence) hold=60m | gross-positive, cost-negative pre-2023 | 375 | 3.6 | -10.7 | -6.8 | 14.4 | 0.07 / -0.18 / -0.11 | 35.9 / 21.6 |
| YM 3 (diag) L=30m |own-drv z|>=2.5 dir=against(convergence) hold=30m | gross-positive, cost-negative pre-2023 | 393 | 4.3 | -10.1 | -6.2 | 14.4 | 0.10 / -0.21 / -0.13 | 41.6 / 27.2 |
| YM 4 (diag) L=120m |own-drv z|>=1.5 dir=against(convergence) hold=60m | positive pre-2023 | 609 | 15.0 | 0.7 | 4.9 | 14.4 | 0.35 / 0.02 / 0.11 | 21.3 / 6.9 |
| YM 5 (diag) L=120m |own-drv z|>=1.5 dir=against(convergence) hold=30m | gross-positive, cost-negative pre-2023 | 739 | 4.6 | -9.8 | -5.6 | 14.4 | 0.14 / -0.31 / -0.18 | 14.8 / 0.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 7 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.00, p(top) = 0.04); NQ: 9 cells pass the clean rule against a replicate mean of 3.7 (p(count) = 0.00, p(top) = 0.01); RTY: 2 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 0.02, p(top) = 0.06); YM: 2 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.34, p(top) = 0.34).
- Of 20 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.26 (NQ L=30m |own-drv z|>=1.5 dir=with(own rel move) hold=60m); bootstrap lower bound > 0 for 3 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 7; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 10, 'positive pre-2023': 6, 'negative pre-2023': 4}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bi_3.py, ap_bi_pipe.py (= ap_b_pipe2 with module swap), ap_bi_job.sh, ap_sw_common.py, ap_bi_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bi3/ (`BI3_CO_all_selected_scored.csv`).

DONE BI3
