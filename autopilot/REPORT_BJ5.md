# REPORT BJ5 - prior-day close vs RTH VWAP (BJ batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 3 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.10; best pair-window standalone Sharpe +0.60.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. prior-day close vs RTH VWAP. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |       8 |          8 |         2 |               0.752 |                2 |          2 |            3 |
| NQ    |       8 |          8 |         1 |               0.701 |                2 |          1 |            3 |
| RTY   |       8 |          8 |         0 |               0.789 |                1 |          0 |            3 |
| YM    |       8 |          8 |         0 |               0.039 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    2 |            1.045 |               4 |       0.24 |                       0.59  |            0.743 |           1.42  |    0.455 |       0.752 |                1.438 |
| NQ    |     200 |                    1 |            1.575 |               4 |       0.83 |                       0.701 |            0.764 |           1.354 |    0.435 |       0.701 |                1.763 |
| RTY   |     200 |                    0 |            1.27  |               4 |       1    |                     nan     |            0.715 |           1.251 |  nan     |     nan     |                1.425 |
| YM    |     200 |                    0 |            1.29  |               4 |       1    |                     nan     |            0.686 |           1.399 |  nan     |     nan     |                1.522 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | 496 | 2 | 0.75 | -0.46 | 0.40 | -0.04 / 0.80 | 0.13 / -0.26 / 0.25 | 0.02 | -0.39 | 0.94 | -0.12 | 0.50 | 798 | NO |
| ES 2 | prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | 419 | 2 | 0.43 | -0.41 | 0.49 | 0.52 / 1.34 | 0.09 / -0.20 / 0.39 | 0.05 | -0.43 | 0.95 | -0.11 | 0.75 | 664 | NO |
| ES 3 (diag) | prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat | 496 | 1 | -0.05 | -0.49 | -0.39 | -1.05 / 1.29 | -0.03 / -0.40 / -0.04 | -0.13 | 0.33 | 0.33 | -0.27 | 0.00 | 798 | diag |
| ES 4 (diag) | prior-day (close-RTH VWAP)/ADR>=0.05 dir=against hold=flat | 419 | 1 | -0.06 | -0.14 | -0.11 | -0.13 / 1.40 | -0.04 / 0.08 / -0.21 | -0.08 | -0.22 | 0.57 | -0.19 | 0.00 | 664 | diag |
| ES 5 (diag) | prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=flat | 419 | 1 | -0.23 | -0.49 | -0.20 | -0.21 / 1.55 | -0.07 / -0.24 / 0.10 | -0.09 | 0.21 | 0.40 | -0.25 | 0.00 | 664 | diag |
| NQ 1 | prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | 496 | 2 | 0.70 | -0.33 | 0.42 | 0.13 / 1.19 | 0.13 / -0.49 / 0.30 | 0.06 | 0.01 | 0.85 | -0.15 | 0.50 | 798 | NO |
| NQ 2 (diag) | prior-day (close-RTH VWAP)/ADR>=0.05 dir=against hold=flat | 419 | 1 | 0.33 | 0.45 | 0.60 | 1.00 / 1.56 | 0.03 / 0.23 / 0.10 | 0.08 | -0.58 | 0.88 | -0.07 | 0.50 | 660 | diag |
| NQ 3 (diag) | prior-day (close-RTH VWAP)/ADR>=0.0 dir=against hold=flat | 496 | 1 | 0.15 | 0.25 | 0.45 | 0.94 / 1.60 | -0.02 / 0.23 / 0.06 | 0.03 | -0.51 | 0.82 | -0.12 | 0.00 | 798 | diag |
| NQ 4 (diag) | prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | 419 | 1 | 0.13 | -0.34 | 0.24 | 0.36 / 1.36 | 0.01 / -0.36 / 0.33 | 0.02 | -0.06 | 0.71 | -0.20 | 0.50 | 660 | diag |
| RTY 1 (diag) | prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | 496 | 1 | 0.79 | -0.53 | 0.49 | 0.10 / 1.12 | 0.17 / -0.27 / 0.21 | 0.08 | -0.15 | 0.95 | -0.09 | 1.00 | 798 | diag |
| RTY 2 (diag) | prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat | 496 | 1 | 0.53 | -0.72 | 0.09 | -0.65 / 1.51 | 0.08 / -0.13 / -0.23 | -0.05 | 0.10 | 0.60 | -0.22 | 0.00 | 798 | diag |
| RTY 3 (diag) | prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | 404 | 1 | 0.40 | -0.50 | 0.06 | -0.31 / 1.20 | 0.08 / -0.42 / 0.08 | -0.02 | -0.21 | 0.79 | -0.20 | 0.75 | 653 | diag |
| YM 1 (diag) | prior-day (close-RTH VWAP)/ADR>=0.05 dir=against hold=flat | 422 | 1 | 0.04 | -0.05 | -0.08 | -0.23 / 1.24 | -0.03 / -0.07 / -0.07 | -0.06 | -0.42 | 0.52 | -0.19 | 0.00 | 659 | diag |
| YM 2 (diag) | prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat | 496 | 1 | -0.08 | -0.48 | 0.18 | 0.52 / 1.38 | -0.04 / 0.17 / -0.04 | -0.03 | 0.28 | 0.66 | -0.19 | 0.00 | 798 | diag |
| YM 3 (diag) | prior-day (close-RTH VWAP)/ADR>=0.0 dir=against hold=flat | 496 | 1 | -0.16 | 0.05 | -0.44 | -0.81 / 1.27 | -0.07 / -0.35 / -0.07 | -0.12 | -0.28 | 0.34 | -0.26 | 0.00 | 798 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 3 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 8 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 1 |
| worst-decile corr <= +0.30 | 14 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | clean | 0.47 | 0.64 | -141802 | -112242 | 468770 | -315636 | 0.91 | 41.9 | 1.55 | -83029 | 254159 | -92926 |
| ES prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | H1 | -1.19 | -1.46 | -200337 | -190614 | 598778 | -222226 | -0.68 | 64.3 | 2.63 | -72437 | 142876 | -90401 |
| ES prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | H2 | 1.93 | 3.47 | -142411 | -115620 | 183463 | -157218 | 4.37 | 41.7 | 2.88 | -86684 | 200226 | -94356 |
| ES prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | all | 0.49 | 0.69 | -169980 | -129728 | 686919 | -315636 | 1.20 | 45.8 | 2.00 | -84660 | 254159 | -94356 |
| NQ prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | clean | 0.72 | 1.07 | -132678 | -106377 | 391941 | -226695 | 1.67 | 45.7 | 1.59 | -82874 | 267468 | -86846 |
| NQ prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | H1 | -1.46 | -1.69 | -227110 | -204267 | 747560 | -265948 | -0.71 | 57.1 | 2.34 | -85709 | 151546 | -85834 |
| NQ prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | H2 | 1.25 | 2.11 | -184620 | -144520 | 333133 | -227110 | 1.95 | 47.2 | 2.79 | -86973 | 195225 | -96643 |
| NQ prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | all | 0.42 | 0.60 | -177781 | -142654 | 747560 | -265948 | 1.03 | 48.2 | 1.97 | -85034 | 267468 | -96643 |
| RTY prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m (diag) | clean | 0.79 | 1.17 | -132912 | -108956 | 407989 | -164134 | 1.75 | 43.8 | 1.63 | -85939 | 244747 | -106513 |
| RTY prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m (diag) | H1 | -0.84 | -1.08 | -167924 | -146265 | 463873 | -217560 | -0.58 | 50.0 | 2.56 | -70553 | 162377 | -71210 |
| RTY prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m (diag) | H2 | 0.91 | 1.53 | -112423 | -100826 | 428110 | -113957 | 0.79 | 47.2 | 2.69 | -79227 | 205182 | -84905 |
| RTY prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m (diag) | all | 0.49 | 0.71 | -139449 | -116677 | 903373 | -217560 | 0.86 | 45.8 | 2.01 | -83213 | 244747 | -106513 |
| YM prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat (diag) | clean | -0.01 | -0.01 | -154663 | -107792 | 789941 | -484606 | -0.01 | 41.9 | 1.42 | -86878 | 319011 | -104033 |
| YM prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat (diag) | H1 | 1.43 | 2.39 | -101506 | -89897 | 203602 | -124236 | 1.52 | 32.1 | 3.00 | -71948 | 150511 | -83091 |
| YM prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat (diag) | H2 | -0.23 | -0.32 | -110796 | -92690 | 392346 | -118781 | -0.15 | 50.0 | 2.45 | -75924 | 217534 | -75945 |
| YM prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat (diag) | all | 0.18 | 0.22 | -142307 | -105895 | 789941 | -484606 | 0.31 | 42.3 | 1.89 | -84962 | 319011 | -104033 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | -21.0 | 5.7 | 16.0 | 27.2 | 5.2 / 17.4 | 5.4 / 29.6 | NO |
| NQ prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | -21.6 | 1.6 | 13.3 | 23.6 | 16.0 / 18.1 | 4.3 / 8.7 | NO |
| RTY prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m (diag) | -21.5 | -18.9 | 13.6 | 22.8 | -19.9 / 11.6 | -7.0 / 15.2 | NO |
| YM prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat (diag) | -27.3 | -9.7 | 12.6 | 9.2 | -10.6 / 8.1 | 19.4 / 32.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 2602 | 7.7 | -21.7 | -7.5 | 29.4 | 0.16 / -0.46 / -0.16 | 91.1 / 61.7 |
| ES 2 prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 2185 | 8.6 | -20.8 | -6.6 | 29.4 | 0.17 / -0.41 / -0.13 | 71.5 / 42.1 |
| ES 3 (diag) prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat | negative pre-2023 | 2602 | -11.8 | -41.2 | -26.9 | 29.4 | -0.14 / -0.49 / -0.32 | 22.1 / -7.3 |
| ES 4 (diag) prior-day (close-RTH VWAP)/ADR>=0.05 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2185 | 15.9 | -13.5 | 0.7 | 29.4 | 0.17 / -0.14 / 0.01 | 10.8 / -18.5 |
| ES 5 (diag) prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=flat | negative pre-2023 | 2185 | -15.9 | -45.3 | -31.1 | 29.4 | -0.17 / -0.49 / -0.34 | -10.8 / -40.2 |
| NQ 1 prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | negative pre-2023 | 2603 | -13.5 | -27.8 | -19.3 | 14.4 | -0.16 / -0.33 / -0.23 | 125.5 / 111.2 |
| NQ 2 (diag) prior-day (close-RTH VWAP)/ADR>=0.05 dir=against hold=flat | positive pre-2023 | 2220 | 77.5 | 63.1 | 71.7 | 14.4 | 0.55 / 0.45 / 0.51 | 142.4 / 128.1 |
| NQ 3 (diag) prior-day (close-RTH VWAP)/ADR>=0.0 dir=against hold=flat | positive pre-2023 | 2603 | 46.4 | 32.0 | 40.6 | 14.4 | 0.36 / 0.25 / 0.31 | 55.0 / 40.6 |
| NQ 4 (diag) prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | negative pre-2023 | 2220 | -15.4 | -29.7 | -21.2 | 14.4 | -0.17 / -0.34 / -0.24 | 37.2 / 22.9 |
| RTY 1 (diag) prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=120m | negative pre-2023 | 1483 | -8.1 | -22.5 | -20.2 | 14.4 | -0.20 / -0.53 / -0.48 | 54.3 / 39.9 |
| RTY 2 (diag) prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat | negative pre-2023 | 1483 | -31.4 | -45.8 | -43.6 | 14.4 | -0.50 / -0.72 / -0.68 | 57.0 / 42.6 |
| RTY 3 (diag) prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m | negative pre-2023 | 1217 | -10.0 | -24.4 | -22.2 | 14.4 | -0.21 / -0.50 / -0.46 | 34.9 / 20.5 |
| YM 1 (diag) prior-day (close-RTH VWAP)/ADR>=0.05 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2162 | 10.6 | -3.8 | 1.9 | 14.4 | 0.14 / -0.05 / 0.03 | 13.2 / -1.2 |
| YM 2 (diag) prior-day (close-RTH VWAP)/ADR>=0.0 dir=with hold=flat | negative pre-2023 | 2606 | -18.1 | -32.4 | -26.7 | 14.4 | -0.27 / -0.48 / -0.40 | 13.7 / -0.6 |
| YM 3 (diag) prior-day (close-RTH VWAP)/ADR>=0.0 dir=against hold=flat | positive pre-2023 | 2606 | 18.1 | 3.7 | 9.5 | 14.4 | 0.27 / 0.05 / 0.14 | -13.7 / -28.1 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 2 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.24, p(top) = 0.46); NQ: 1 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.83, p(top) = 0.43); RTY: 0 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 1.00); YM: 0 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 1.00).
- Of 3 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.10 (ES prior-day (close-RTH VWAP)/ADR>=0.05 dir=with hold=120m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 2, 'negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_5.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj5/ (`BJ5_CO_all_selected_scored.csv`).

DONE BJ5
