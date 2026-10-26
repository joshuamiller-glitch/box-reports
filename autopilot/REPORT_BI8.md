# REPORT BI8 - range-shock day next-day drift (BI batch)

**Verdict: LEAD at the time of the BI run; WITHDRAWN as NO (long beta) by REPORT_BI8B. FOUND 0, LEAD 1, INSURANCE 0.** 4 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.12; best pair-window standalone Sharpe +1.45.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BI', before the first run)
- Rule: see IDEAS_BI.md / PREREG_AUTOPILOT.md BATCH BI (frozen before the first run). range-shock day next-day drift
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      12 |          3 |         1 |               1.023 |                2 |          1 |            3 |
| NQ    |      12 |          3 |         2 |               0.978 |                2 |          2 |            3 |
| RTY   |      12 |          0 |         0 |               1.165 |                2 |          0 |            3 |
| YM    |      12 |          3 |         1 |               1.595 |                2 |          1 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            0.695 |               3 |      0.52  |                       0.761 |            0.827 |           1.715 |    0.265 |       0.761 |                1.715 |
| NQ    |     200 |                    2 |            0.655 |               3 |      0.155 |                       0.936 |            0.759 |           1.409 |    0.145 |       0.978 |                1.599 |
| RTY   |     200 |                    0 |            0.115 |               2 |      1     |                     nan     |            0.831 |           1.565 |  nan     |     nan     |                1.565 |
| YM    |     200 |                    1 |            0.47  |               2 |      0.4   |                       0.557 |            0.794 |           1.364 |    0.305 |       0.557 |                1.398 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | prior-day range>=1.5xATR20 mode=long hold=1d | 70 | 2 | 0.76 | -0.53 | 0.83 | 1.42 / 1.51 | 0.14 / 0.10 / 0.08 | 0.11 | -0.02 | 0.95 | 0.01 | 0.50 | 114 | LEAD(gate3-7 fail: plateau ) |
| ES 2 (diag) | prior-day range>=2.0xATR20 mode=against hold=2d | 16 | 2 | 1.02 | 0.17 | 1.07 | 1.34 / 1.45 | 0.13 / 0.40 / -0.00 | 0.13 | -0.55 | 0.95 | 0.03 | 0.00 | 27 S | diag |
| ES 3 (diag) | prior-day range>=2.0xATR20 mode=long hold=2d | 16 | 2 | 0.92 | -0.00 | 0.90 | 0.97 / 1.49 | 0.15 / 0.01 / 0.07 | 0.11 | -0.55 | 0.96 | -0.00 | 0.50 | 27 S | diag |
| ES 4 (diag) | prior-day range>=1.5xATR20 mode=against hold=1d | 70 | 1 | 0.78 | -0.11 | 0.79 | 1.31 / 1.36 | 0.11 / 0.23 / -0.04 | 0.08 | -0.40 | 0.96 | 0.01 | 0.50 | 114 | diag |
| NQ 1 | prior-day range>=1.5xATR20 mode=long hold=1d | 65 | 2 | 0.98 | -0.12 | 0.60 | -0.10 / 1.55 | 0.19 / -0.30 / -0.06 | 0.07 | -0.55 | 0.85 | -0.07 | 0.50 | 102 | NO |
| NQ 2 | prior-day range>=1.5xATR20 mode=against hold=1d | 65 | 2 | 0.89 | 0.36 | 0.81 | 0.81 / 1.38 | 0.11 / 0.00 / 0.02 | 0.07 | -0.01 | 0.94 | 0.00 | 0.50 | 102 | NO |
| NQ 3 (diag) | prior-day range>=2.0xATR20 mode=against hold=1d | 20 | 1 | 0.71 | 0.33 | 0.50 | -0.54 / 1.59 | 0.08 / 0.03 / -0.08 | 0.03 | -0.54 | 0.80 | -0.03 | 0.50 | 29 S | diag |
| NQ 4 (diag) | prior-day range>=2.0xATR20 mode=against hold=2d | 16 | 1 | 0.68 | 0.19 | 0.77 | 1.18 / 1.45 | 0.07 / 0.20 / 0.04 | 0.07 | -0.54 | 0.91 | -0.02 | 0.00 | 24 S | diag |
| NQ 5 (diag) | prior-day range>=2.0xATR20 mode=long hold=1d | 20 | 1 | 0.57 | 0.30 | 0.41 | -0.07 / 1.54 | 0.09 / -0.04 / -0.12 | 0.03 | -0.54 | 0.70 | -0.07 | 0.50 | 29 S | diag |
| RTY 1 (diag) | prior-day range>=1.5xATR20 mode=long hold=1d | 54 | 2 | 1.17 | -0.34 | 1.45 | 1.90 / 1.25 | 0.21 / 0.45 / 0.08 | 0.22 | -0.50 | 1.00 | 0.08 | 0.00 | 86 S | diag |
| RTY 2 (diag) | prior-day range>=2.0xATR20 mode=long hold=1d | 20 | 2 | 0.66 | -0.27 | 0.86 | 1.17 / 1.37 | 0.11 / 0.31 / -0.04 | 0.11 | -0.45 | 0.96 | -0.03 | 0.50 | 30 S | diag |
| RTY 3 (diag) | prior-day range>=1.5xATR20 mode=against hold=1d | 54 | 1 | 0.63 | -0.38 | 0.33 | -0.30 / 1.48 | 0.11 / -0.15 / -0.12 | 0.03 | -0.50 | 0.70 | -0.10 | 1.00 | 86 S | diag |
| YM 1 | prior-day range>=1.5xATR20 mode=long hold=1d | 60 | 2 | 0.56 | -0.33 | 0.52 | 0.47 / 1.27 | 0.08 / 0.12 / -0.03 | 0.06 | -0.41 | 0.83 | -0.05 | 1.00 | 93 S | NO |
| YM 2 (diag) | prior-day range>=1.5xATR20 mode=with hold=2d | 49 | 2 | 1.59 | 0.55 | 0.69 | -0.99 / 1.58 | 0.27 / -0.27 / -0.13 | 0.09 | -0.33 | 0.86 | -0.05 | 0.00 | 76 S | diag |
| YM 3 (diag) | prior-day range>=2.0xATR20 mode=long hold=2d | 14 | 2 | 1.29 | -0.18 | 0.77 | -0.70 / 1.43 | 0.20 / -0.04 / -0.06 | 0.10 | 0.00 | 0.91 | 0.00 | 0.50 | 22 S | diag |
| YM 4 (diag) | prior-day range>=2.0xATR20 mode=against hold=2d | 14 | 2 | 1.22 | -0.20 | 1.25 | 1.41 / 1.46 | 0.19 / 0.25 / 0.11 | 0.17 | 0.00 | 0.97 | 0.08 | 0.00 | 22 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 4 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 16 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 7 |
| standalone pair-window Sharpe above own random-entry null p95 | 7 |
| worst-decile corr <= +0.30 | 16 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 6 |
| small-sample (<100 trades pair window) | 12 |
| gate_add PASS at any share (non-diag) | 1 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES prior-day range>=1.5xATR20 mode=long hold=1d | clean | 0.75 | 1.83 | -95178 | -62268 | 365080 | -159373 | 1.87 | 19.0 | 1.60 | -78887 | 270164 | -82780 |
| ES prior-day range>=1.5xATR20 mode=long hold=1d | H1 | 1.22 | 2.55 | -33531 | -27860 | 128393 | -48812 | 0.84 | 21.4 | 2.93 | -68023 | 144255 | -69030 |
| ES prior-day range>=1.5xATR20 mode=long hold=1d | H2 | 1.54 | 3.20 | -46083 | -34420 | 161288 | -52460 | 1.23 | 13.9 | 2.57 | -82689 | 222863 | -82853 |
| ES prior-day range>=1.5xATR20 mode=long hold=1d | all | 0.83 | 1.98 | -79116 | -52550 | 365080 | -159373 | 2.71 | 18.5 | 2.02 | -79539 | 270164 | -82853 |
| NQ prior-day range>=1.5xATR20 mode=against hold=1d | clean | 0.89 | 6.08 | -31753 | -26320 | 75800 | -38320 | 10.66 | 18.1 | 1.57 | -77884 | 264945 | -79868 |
| NQ prior-day range>=1.5xATR20 mode=against hold=1d | H1 | 0.90 | 1.66 | -37321 | -34686 | 77361 | -44296 | 1.07 | 21.4 | 2.83 | -79269 | 147690 | -83889 |
| NQ prior-day range>=1.5xATR20 mode=against hold=1d | H2 | 0.72 | 1.36 | -37357 | -29203 | 115324 | -41963 | 0.62 | 19.4 | 2.51 | -83371 | 217425 | -84217 |
| NQ prior-day range>=1.5xATR20 mode=against hold=1d | all | 0.81 | 4.07 | -35027 | -29736 | 146485 | -44296 | 6.57 | 19.0 | 1.97 | -79800 | 264945 | -84217 |
| RTY prior-day range>=1.5xATR20 mode=long hold=1d (diag) | clean | 1.16 | 3.02 | -89738 | -65495 | 390307 | -135385 | 2.69 | 15.2 | 1.67 | -77884 | 257862 | -79868 |
| RTY prior-day range>=1.5xATR20 mode=long hold=1d (diag) | H1 | 2.72 | 7.65 | -76778 | -69649 | 133930 | -91860 | 5.41 | 14.3 | 3.28 | -67411 | 143034 | -78287 |
| RTY prior-day range>=1.5xATR20 mode=long hold=1d (diag) | H2 | 1.15 | 2.32 | -98000 | -71976 | 246829 | -101111 | 1.30 | 8.3 | 2.57 | -81476 | 217425 | -82524 |
| RTY prior-day range>=1.5xATR20 mode=long hold=1d (diag) | all | 1.45 | 3.61 | -94465 | -72601 | 390307 | -135385 | 5.37 | 13.7 | 2.13 | -79032 | 257862 | -82524 |
| YM prior-day range>=1.5xATR20 mode=long hold=1d | clean | 0.55 | 1.31 | -90498 | -55460 | 422526 | -204952 | 1.19 | 14.3 | 1.54 | -78795 | 278938 | -80143 |
| YM prior-day range>=1.5xATR20 mode=long hold=1d | H1 | 1.28 | 2.86 | -41596 | -38483 | 75122 | -48314 | 1.93 | 21.4 | 2.95 | -71461 | 140770 | -77518 |
| YM prior-day range>=1.5xATR20 mode=long hold=1d | H2 | 0.07 | 0.09 | -114345 | -83485 | 393969 | -156945 | 0.04 | 13.9 | 2.45 | -88812 | 226138 | -91496 |
| YM prior-day range>=1.5xATR20 mode=long hold=1d | all | 0.52 | 1.09 | -95927 | -63353 | 422526 | -204952 | 1.57 | 15.5 | 1.96 | -81458 | 278938 | -91496 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior-day range>=1.5xATR20 mode=long hold=1d | -19.2 | 24.5 | 28.8 | 35.3 | 28.3 / 29.4 | 47.7 / 48.5 | NO |
| NQ prior-day range>=1.5xATR20 mode=against hold=1d | -19.5 | 23.4 | 28.3 | 38.1 | 31.7 / 30.8 | 19.3 / 26.8 | NO |
| RTY prior-day range>=1.5xATR20 mode=long hold=1d (diag) | -7.1 | 12.2 | 27.9 | 27.0 | 31.7 / 30.8 | 30.0 / 35.0 | NO |
| YM prior-day range>=1.5xATR20 mode=long hold=1d | -22.8 | 8.5 | 23.9 | 30.6 | 29.0 / 29.1 | 30.1 / 41.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 prior-day range>=1.5xATR20 mode=long hold=1d | negative pre-2023 | 364 | -89.5 | -118.9 | -104.7 | 29.4 | -0.40 / -0.53 / -0.47 | 496.6 / 467.2 |
| ES 2 (diag) prior-day range>=2.0xATR20 mode=against hold=2d | positive pre-2023 | 87 | 183.3 | 154.0 | 168.0 | 29.4 | 0.20 / 0.17 / 0.19 | 2211.7 / 2182.4 |
| ES 3 (diag) prior-day range>=2.0xATR20 mode=long hold=2d | gross-positive, cost-negative pre-2023 | 87 | 30.5 | 1.1 | 15.2 | 29.4 | 0.03 / -0.00 / 0.01 | 1994.5 / 1965.2 |
| ES 4 (diag) prior-day range>=1.5xATR20 mode=against hold=1d | gross-positive, cost-negative pre-2023 | 364 | 0.8 | -28.6 | -14.5 | 29.4 | 0.01 / -0.11 / -0.05 | 984.8 / 955.5 |
| NQ 1 prior-day range>=1.5xATR20 mode=long hold=1d | negative pre-2023 | 352 | -33.9 | -48.2 | -39.6 | 14.4 | -0.09 / -0.12 / -0.10 | 1023.5 / 1009.1 |
| NQ 2 prior-day range>=1.5xATR20 mode=against hold=1d | positive pre-2023 | 352 | 147.8 | 133.4 | 142.1 | 14.4 | 0.40 / 0.36 / 0.38 | 1823.3 / 1808.9 |
| NQ 3 (diag) prior-day range>=2.0xATR20 mode=against hold=1d | positive pre-2023 | 101 | 233.1 | 218.7 | 227.4 | 14.4 | 0.35 / 0.33 / 0.35 | 4155.5 / 4141.1 |
| NQ 4 (diag) prior-day range>=2.0xATR20 mode=against hold=2d | positive pre-2023 | 87 | 231.9 | 217.5 | 226.2 | 14.4 | 0.20 / 0.19 / 0.20 | 2418.8 / 2404.4 |
| NQ 5 (diag) prior-day range>=2.0xATR20 mode=long hold=1d | positive pre-2023 | 101 | 193.7 | 179.3 | 188.0 | 14.4 | 0.32 / 0.30 / 0.31 | 1535.5 / 1521.1 |
| RTY 1 (diag) prior-day range>=1.5xATR20 mode=long hold=1d | negative pre-2023 | 168 | -61.2 | -75.5 | -73.1 | 14.4 | -0.28 / -0.34 / -0.33 | 307.7 / 293.3 |
| RTY 2 (diag) prior-day range>=2.0xATR20 mode=long hold=1d | negative pre-2023 | 44 | -66.5 | -80.8 | -78.1 | 14.4 | -0.22 / -0.27 / -0.26 | 328.2 / 313.9 |
| RTY 3 (diag) prior-day range>=1.5xATR20 mode=against hold=1d | negative pre-2023 | 168 | -64.2 | -78.6 | -76.2 | 14.4 | -0.31 / -0.38 / -0.37 | 213.4 / 199.1 |
| YM 1 prior-day range>=1.5xATR20 mode=long hold=1d | negative pre-2023 | 342 | -53.0 | -67.4 | -61.8 | 14.4 | -0.26 / -0.33 / -0.30 | 270.2 / 255.8 |
| YM 2 (diag) prior-day range>=1.5xATR20 mode=with hold=2d | positive pre-2023 | 261 | 209.4 | 195.1 | 200.7 | 14.4 | 0.59 / 0.55 / 0.57 | 871.9 / 857.6 |
| YM 3 (diag) prior-day range>=2.0xATR20 mode=long hold=2d | negative pre-2023 | 85 | -106.5 | -120.8 | -115.1 | 14.4 | -0.16 / -0.18 / -0.17 | 2047.5 / 2033.1 |
| YM 4 (diag) prior-day range>=2.0xATR20 mode=against hold=2d | negative pre-2023 | 85 | -116.0 | -130.4 | -124.7 | 14.4 | -0.18 / -0.20 / -0.20 | 1951.1 / 1936.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 1 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.52, p(top) = 0.27); NQ: 2 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.15, p(top) = 0.14); RTY: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00); YM: 1 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 0.40, p(top) = 0.30).
- Of 4 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.12 (ES prior-day range>=1.5xATR20 mode=long hold=1d same-day); bootstrap lower bound > 0 for 2 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 1 (cell-share pairs).
- ERA flags: {'negative pre-2023': 3, 'positive pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bi_8.py, ap_bi_pipe.py (= ap_b_pipe2 with module swap), ap_bi_job.sh, ap_sw_common.py, ap_bi_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bi8/ (`BI8_CO_all_selected_scored.csv`).

## LEAD detail (added by worker BK after the pipeline run; the pipeline marks a cell LEAD when the Sharpe-uplift gate holds at any of 10/20/30/50% share)
- Cell: ES, previous label day range >= 1.5 x ATR20, go LONG at the next RTH open, flatten the same day at the 16:55 ET (cell 'hold=1d' = same-day hold; corrected, see REPORT_BI8B), 70 clean / 129 pair-window trades (not small-sample). Standalone weekly Sharpe clean 0.75 / H1 1.22 / H2 1.54 / all-in 0.83 (own random-entry null p95 0.79, rank 0.955). Additive uplift (sleeve scaled to the pair's clean weekly sigma): at 20% +0.14 / +0.10 / +0.08 (all-in +0.12; 2x slippage all-in +0.11; bootstrap lo +0.014); at 30% +0.18 / +0.15 / +0.12 (gate_add PASS: uplift >= 0.10 on all three spans, worst week change +0.4%, null, bootstrap lo +0.009, worst-decile corr -0.02); at 50% +0.22 / +0.22 / +0.18; at 10% +0.08 / +0.05 / +0.04. FAILED: plateau 0.50 (needs 0.75); uplift at 10% and H2 at 20% (+0.08); ERA FLAG negative pre-2023 (gross -$89 per trade, net -$119, price-scaled net -$105; 2013-22 Sharpe -0.53); the false-selection test p(count)=see fs table (ES: 1 cell passes against a replicate mean of 0.7, p=0.52, i.e. chance level).
- Insurance metrics of pair + 20% sleeve vs pair alone (weekly, USD): clean Sharpe 1.6 vs 1.46, Sortino 3.1, MAR 5.4, CVaR5 -78.9k, CVaR10 -78.0k, maxDD 270k, worst week -82.8k, %neg weeks 41.9; H1 Sharpe 2.9, CVaR5 -68.0k, maxDD 144k, worst week -69.0k; H2 Sharpe 2.6, CVaR5 -82.7k, maxDD 223k, worst week -82.9k; all-in Sharpe 2.0, CVaR5 -79.5k, CVaR10 -77.6k, maxDD 270k, worst week -82.9k, %neg weeks 41.7 (pair alone all-in worst week -82.9k, maxDD 280k).
- Sized dollars: sleeve scale 20.8 ES contracts = the pair's clean weekly sigma; 20% share = 4.2 ES contracts, 30% = 6.3. Worst single 1-contract trade in the pair window -$13,142 (a same-day hold) so about -$55k at 4.2 contracts and -$82k at 6.3 contracts; the sleeve adds exposure on the same days the pair is volatile.
- Replication (ap_bi_rep.py, 30% share): H0 2023-02..07 uplift -0.13 (FAILS; sleeve Sharpe -1.02 on 26 weeks); alternating months odd/even +0.07 / +0.21 (needs >= 50% of the clean +0.18, i.e. 0.09: odd borderline fails); the same cell on other instruments, all-in uplift at 20%: NQ +0.07 (H1 -0.30), YM +0.06 (H2 -0.03), RTY +0.23 (diagnostic row, passes all three spans +0.21/+0.45/+0.08): same sign on 4 of 4 and each >= 50% of ES's +0.12 all-in only for RTY. Replications that hold: cross-instrument sign yes, magnitude partial; H0 no; alt-month borderline. Fewer than 2 clean replications, so this is a LEAD, not FOUND-PENDING.
- Caveat: this is a LONG-ONLY rule in a bull sample (the null alternates sides, so long-only beta is not removed by it); ERA negative pre-2023 and the H0 failure say the effect may be the 2023-26 up-trend, not a range-shock premium. The mechanism (liquidity restoration after volatility shock, Nagel 2012) predicts the pre-registered sign (long), which is the sign observed.
- Executability: NT8 daily strategy on ES (or MES): at 09:30 ET after a day with range >= 1.5 x ATR20 go long, flatten same day 16:55; margin ES intraday ~$1.2-1.5k per contract, overnight ~$12-15k (unverified); separate from DualStrat; separate account not required (different instrument, but the ES hold overlaps the pair's sessions).

DONE BI8
