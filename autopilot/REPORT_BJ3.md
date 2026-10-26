# REPORT BJ3 - RTH-open magnet fade (BJ batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 3 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.12; best pair-window standalone Sharpe +0.70.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. RTH-open magnet fade. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      16 |          8 |         0 |               1.018 |                2 |          0 |            3 |
| NQ    |      16 |          8 |         2 |               0.551 |                2 |          2 |            3 |
| RTY   |      16 |          8 |         1 |               0.448 |                2 |          1 |            3 |
| YM    |      16 |          8 |         0 |               0.598 |                2 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            1.03  |               4 |       1    |                     nan     |            0.693 |           1.234 |  nan     |     nan     |                1.434 |
| NQ    |     200 |                    2 |            1.765 |               5 |       0.59 |                       0.517 |            0.768 |           1.222 |    0.675 |       0.551 |                1.573 |
| RTY   |     200 |                    1 |            0.93  |               4 |       0.66 |                       0.232 |            0.698 |           1.319 |    0.615 |       0.232 |                1.417 |
| YM    |     200 |                    0 |            1.24  |               5 |       1    |                     nan     |            0.736 |           1.31  |  nan     |     nan     |                1.583 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | 65 | 2 | 1.02 | -0.28 | 0.50 | -0.14 / 1.13 | 0.14 / -0.53 / 0.18 | 0.01 | 0.16 | 0.89 | -0.15 | 0.00 | 109 | diag |
| ES 2 (diag) | clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=120m | 65 | 2 | 0.48 | -0.32 | 0.45 | 0.44 / 1.33 | 0.07 / 0.14 / 0.15 | 0.06 | 0.10 | 0.86 | -0.12 | 0.00 | 109 | diag |
| ES 3 (diag) | clock 11:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | 38 | 1 | 0.36 | -0.72 | -0.11 | -0.71 / 1.31 | 0.07 / 0.35 / -0.56 | -0.07 | -0.36 | 0.52 | -0.27 | 0.00 | 60 S | diag |
| NQ 1 | clock 13:00 |px-RTHopen|>=0.3ADR dir=with hold=60m | 241 | 2 | 0.55 | 0.32 | 0.39 | -0.19 / 1.51 | 0.06 / 0.14 / -0.11 | 0.02 | -0.31 | 0.76 | -0.09 | 0.50 | 388 | NO |
| NQ 2 | clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=120m | 196 | 2 | 0.48 | 0.30 | 0.62 | 0.81 / 1.58 | 0.03 / -0.28 / 0.20 | 0.03 | 0.11 | 0.87 | -0.19 | 0.25 | 308 | NO |
| NQ 3 (diag) | clock 13:00 |px-RTHopen|>=0.6ADR dir=with hold=60m | 83 | 2 | 0.53 | 0.09 | 0.15 | -0.58 / 1.16 | 0.09 / 0.46 / -0.55 | -0.02 | 0.01 | 0.71 | -0.21 | 0.00 | 141 | diag |
| NQ 4 (diag) | clock 13:00 |px-RTHopen|>=0.6ADR dir=with hold=120m | 83 | 2 | 0.50 | 0.23 | 0.14 | -0.39 / 1.43 | 0.07 / -0.24 / -0.39 | -0.08 | -0.05 | 0.64 | -0.32 | 0.00 | 141 | diag |
| NQ 5 (diag) | clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=60m | 196 | 1 | 0.40 | 0.43 | 0.70 | 1.07 / 1.66 | 0.03 / -0.32 / 0.37 | 0.06 | 0.17 | 0.88 | -0.16 | 0.50 | 308 | diag |
| RTY 1 | clock 13:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | 221 | 2 | 0.23 | -0.16 | 0.62 | 1.05 / 1.19 | 0.02 / 0.10 / 0.42 | 0.07 | -0.14 | 0.94 | -0.11 | 0.50 | 377 | NO |
| RTY 2 (diag) | clock 11:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | 53 | 1 | 0.45 | 0.23 | -0.33 | -1.78 / 1.51 | 0.04 / -0.52 / -0.30 | -0.13 | 0.05 | 0.41 | -0.28 | 0.00 | 82 S | diag |
| RTY 3 (diag) | clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | 74 | 1 | 0.17 | 0.02 | 0.48 | 0.88 / 1.25 | -0.04 / -0.38 / 0.44 | -0.02 | -0.03 | 0.87 | -0.19 | 0.00 | 128 | diag |
| RTY 4 (diag) | clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m | 198 | 1 | 0.03 | -0.29 | -0.04 | -0.05 / 1.21 | -0.04 / -0.50 / 0.13 | -0.12 | -0.41 | 0.71 | -0.28 | 0.00 | 334 | diag |
| YM 1 (diag) | clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m | 177 | 1 | 0.60 | -0.80 | -0.10 | -1.02 / 1.22 | 0.16 / -0.04 / -0.35 | -0.03 | -0.26 | 0.59 | -0.19 | 0.50 | 292 | diag |
| YM 2 (diag) | clock 11:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | 44 | 2 | 0.28 | -0.34 | -0.21 | -1.05 / 1.28 | 0.08 / -0.57 / -0.00 | -0.04 | 0.12 | 0.44 | -0.19 | 0.00 | 72 S | diag |
| YM 3 (diag) | clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | 176 | 1 | 0.22 | -0.58 | -0.18 | -0.74 / 1.48 | 0.06 / -0.36 / -0.15 | -0.06 | -0.19 | 0.43 | -0.23 | 0.00 | 290 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 3 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 8 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 0 |
| worst-decile corr <= +0.30 | 15 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=120m (diag) | clean | 0.48 | 0.77 | -137920 | -107576 | 614211 | -193798 | 0.71 | 21.9 | 1.53 | -85473 | 317179 | -96240 |
| ES clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=120m (diag) | H1 | 0.07 | 0.11 | -111508 | -92681 | 374858 | -127976 | 0.04 | 28.6 | 2.96 | -77610 | 145879 | -78287 |
| ES clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=120m (diag) | H2 | 0.61 | 1.06 | -274585 | -187027 | 498666 | -293929 | 0.75 | 16.7 | 2.64 | -83264 | 224012 | -84003 |
| ES clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=120m (diag) | all | 0.45 | 0.75 | -172428 | -126874 | 614211 | -293929 | 1.34 | 22.0 | 1.99 | -84358 | 317179 | -96240 |
| NQ clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=120m | clean | 0.47 | 0.65 | -156958 | -110717 | 589450 | -263644 | 0.72 | 41.0 | 1.49 | -86416 | 354244 | -97752 |
| NQ clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=120m | H1 | 0.09 | 0.12 | -299397 | -229628 | 468573 | -351157 | 0.08 | 32.1 | 2.55 | -100123 | 176205 | -126460 |
| NQ clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=120m | H2 | 1.50 | 3.07 | -147282 | -118607 | 318736 | -158455 | 2.15 | 38.9 | 2.69 | -97436 | 244647 | -111344 |
| NQ clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=120m | all | 0.62 | 0.92 | -198740 | -139434 | 615604 | -351157 | 1.86 | 38.7 | 1.93 | -93314 | 354244 | -126460 |
| RTY clock 13:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | clean | 0.23 | 0.35 | -133343 | -107888 | 509518 | -159957 | 0.41 | 43.8 | 1.48 | -92624 | 277258 | -113865 |
| RTY clock 13:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | H1 | 0.44 | 0.81 | -113956 | -99583 | 293929 | -130267 | 0.44 | 57.1 | 2.93 | -73046 | 163516 | -89054 |
| RTY clock 13:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | H2 | 1.39 | 2.58 | -203648 | -163629 | 427328 | -206817 | 1.86 | 47.2 | 2.90 | -85126 | 231638 | -87421 |
| RTY clock 13:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | all | 0.62 | 1.05 | -153595 | -123532 | 509518 | -206817 | 2.22 | 46.4 | 2.02 | -90561 | 277258 | -113865 |
| YM clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m (diag) | clean | 0.57 | 0.87 | -126463 | -104264 | 745377 | -200705 | 0.69 | 36.2 | 1.62 | -82624 | 252543 | -89506 |
| YM clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m (diag) | H1 | -0.40 | -0.49 | -190199 | -165106 | 640767 | -240115 | -0.19 | 42.9 | 2.79 | -60517 | 181408 | -67646 |
| YM clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m (diag) | H2 | -1.58 | -1.83 | -168413 | -149698 | 734222 | -184509 | -0.74 | 52.8 | 2.13 | -93298 | 208466 | -104072 |
| YM clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m (diag) | all | -0.10 | -0.13 | -162057 | -132950 | 1214472 | -240115 | -0.13 | 40.5 | 1.91 | -84265 | 252543 | -104072 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=120m (diag) | -21.0 | -12.3 | 17.8 | 10.1 | -13.2 / 14.9 | 30.0 / 30.0 | NO |
| NQ clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=120m | -17.5 | -55.3 | -4.4 | -9.7 | -7.9 / 8.6 | -63.7 / -20.5 | NO |
| RTY clock 13:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | -17.6 | -27.6 | 5.6 | 24.3 | -28.6 / 0.4 | 9.4 / 17.5 | NO |
| YM clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m (diag) | -31.7 | -14.4 | 17.2 | 19.3 | 11.3 / 18.8 | 32.9 / 41.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | gross-positive, cost-negative pre-2023 | 377 | 6.2 | -23.2 | -8.6 | 29.4 | 0.08 / -0.28 / -0.10 | 155.2 / 125.8 |
| ES 2 (diag) clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=120m | negative pre-2023 | 377 | -5.2 | -34.6 | -20.0 | 29.4 | -0.05 / -0.32 / -0.19 | 111.2 / 81.8 |
| ES 3 (diag) clock 11:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | negative pre-2023 | 203 | -57.4 | -86.7 | -72.3 | 29.4 | -0.48 / -0.72 / -0.60 | 112.2 / 82.8 |
| NQ 1 clock 13:00 |px-RTHopen|>=0.3ADR dir=with hold=60m | positive pre-2023 | 1215 | 34.0 | 19.7 | 28.2 | 14.4 | 0.55 / 0.32 / 0.46 | 160.5 / 146.2 |
| NQ 2 clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=120m | positive pre-2023 | 941 | 40.7 | 26.4 | 35.0 | 14.4 | 0.47 / 0.30 / 0.40 | 108.0 / 93.6 |
| NQ 3 (diag) clock 13:00 |px-RTHopen|>=0.6ADR dir=with hold=60m | positive pre-2023 | 443 | 23.8 | 9.5 | 18.2 | 14.4 | 0.23 / 0.09 / 0.17 | 168.4 / 154.0 |
| NQ 4 (diag) clock 13:00 |px-RTHopen|>=0.6ADR dir=with hold=120m | positive pre-2023 | 443 | 45.1 | 30.7 | 39.4 | 14.4 | 0.33 / 0.23 / 0.29 | 176.3 / 162.0 |
| NQ 5 (diag) clock 11:00 |px-RTHopen|>=0.3ADR dir=with hold=60m | positive pre-2023 | 941 | 45.6 | 31.2 | 39.9 | 14.4 | 0.63 / 0.43 / 0.55 | 68.1 / 53.8 |
| RTY 1 clock 13:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | gross-positive, cost-negative pre-2023 | 729 | 7.0 | -7.3 | -5.2 | 14.4 | 0.16 / -0.16 / -0.11 | 24.6 / 10.2 |
| RTY 2 (diag) clock 11:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | positive pre-2023 | 150 | 35.1 | 20.7 | 22.9 | 14.4 | 0.39 / 0.23 / 0.26 | 52.7 / 38.4 |
| RTY 3 (diag) clock 13:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | positive pre-2023 | 251 | 15.7 | 1.3 | 3.5 | 14.4 | 0.25 / 0.02 / 0.06 | 22.8 / 8.4 |
| RTY 4 (diag) clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m | gross-positive, cost-negative pre-2023 | 615 | 2.9 | -11.5 | -9.3 | 14.4 | 0.07 / -0.29 / -0.24 | 13.3 / -1.1 |
| YM 1 (diag) clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=60m | negative pre-2023 | 824 | -20.6 | -35.0 | -29.3 | 14.4 | -0.47 / -0.80 / -0.67 | 42.3 / 28.0 |
| YM 2 (diag) clock 11:00 |px-RTHopen|>=0.6ADR dir=against(to open) hold=60m | negative pre-2023 | 205 | -15.5 | -29.9 | -24.3 | 14.4 | -0.18 / -0.34 / -0.28 | 54.0 / 39.6 |
| YM 3 (diag) clock 11:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m | negative pre-2023 | 824 | -18.2 | -32.6 | -26.9 | 14.4 | -0.33 / -0.58 / -0.48 | 31.8 / 17.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 0 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 1.00); NQ: 2 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 0.59, p(top) = 0.68); RTY: 1 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.66, p(top) = 0.61); YM: 0 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 1.00).
- Of 3 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.12 (RTY clock 13:00 |px-RTHopen|>=0.3ADR dir=against(to open) hold=120m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 2, 'gross-positive, cost-negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_3.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj3/ (`BJ3_CO_all_selected_scored.csv`).

DONE BJ3
