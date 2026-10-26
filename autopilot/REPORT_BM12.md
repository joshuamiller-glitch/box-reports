# REPORT BM12 - BM1 reference-price test (BL3)

**Verdict: FOUND-CANDIDATE (needs full verification). FOUND 1, LEAD 1, INSURANCE 0.** 8 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.29; best pair-window standalone Sharpe +1.47.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see PREREG_AUTOPILOT.md BL3. Entry 15:20 against, six reference prices.
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      12 |          6 |         1 |               0.502 |                2 |          1 |            3 |
| NQ    |      12 |          6 |         4 |               1.364 |                2 |          4 |            3 |
| RTY   |      12 |          6 |         3 |               0.7   |                2 |          3 |            3 |
| YM    |      12 |          6 |         0 |               0.476 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            0.65  |               4 |      0.505 |                       0.501 |            0.608 |           1.24  |    0.27  |       0.501 |                1.378 |
| NQ    |     200 |                    4 |            1.185 |               4 |      0.01  |                       1.116 |            0.733 |           1.233 |    0.085 |       1.333 |                1.525 |
| RTY   |     200 |                    3 |            0.59  |               4 |      0.02  |                       0.426 |            0.647 |           1.324 |    0.315 |       0.673 |                1.403 |
| YM    |     200 |                    0 |            0.72  |               4 |      1     |                     nan     |            0.675 |           1.332 |  nan     |     nan     |                1.343 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 131 | 2 | 0.50 | -0.94 | 0.26 | -0.12 / 1.08 | 0.07 / -0.20 / 0.02 | -0.05 | 0.19 | 0.89 | -0.16 | 0.50 | 207 | NO |
| ES 2 (diag) | ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 76 | 2 | 0.50 | -1.00 | 0.54 | 0.79 / 0.99 | 0.10 / 0.21 / -0.02 | 0.06 | -0.09 | 0.96 | -0.09 | 0.00 | 109 | diag |
| ES 3 (diag) | ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 208 | 1 | 0.15 | -1.21 | 0.22 | 0.49 / 0.83 | 0.02 / 0.31 / -0.05 | -0.04 | -0.09 | 0.91 | -0.14 | 1.00 | 329 | diag |
| ES 4 (diag) | ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 228 | 1 | 0.14 | -1.21 | -0.06 | -0.39 / 1.13 | 0.01 / 0.15 / -0.19 | -0.13 | 0.66 | 0.74 | -0.22 | 0.00 | 387 | diag |
| NQ 1 | ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 243 | 2 | 1.33 | -1.48 | 1.47 | 1.67 / 1.34 | 0.23 / 0.40 / 0.45 | 0.27 | -0.20 | 1.00 | 0.10 | 1.00 | 404 | FOUND-CAND |
| NQ 2 | ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 138 | 2 | 1.33 | -1.24 | 0.78 | 0.10 / 1.29 | 0.19 / -0.32 / 0.17 | 0.08 | 0.65 | 0.94 | -0.08 | 1.00 | 227 | NO |
| NQ 3 | ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 219 | 2 | 1.00 | -1.08 | 1.12 | 1.42 / 1.39 | 0.18 / 0.38 / 0.29 | 0.21 | 0.17 | 0.99 | 0.01 | 1.00 | 350 | LEAD |
| NQ 4 | ref=gap_only |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 130 | 2 | 0.80 | -0.60 | 0.60 | 0.10 / 1.34 | 0.15 / -0.10 / -0.13 | 0.04 | 0.40 | 0.91 | -0.13 | 0.00 | 226 | NO |
| NQ 5 (diag) | ref=today_open |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 84 | 2 | 1.36 | -0.77 | 1.24 | 1.24 / 1.41 | 0.24 / 0.28 / 0.33 | 0.25 | -0.55 | 0.99 | 0.06 | 0.50 | 135 | diag |
| NQ 6 (diag) | ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 74 | 2 | 0.78 | -0.85 | 1.18 | 1.99 / 1.53 | 0.14 / 0.61 / 0.22 | 0.21 | -0.55 | 0.97 | 0.04 | 0.50 | 108 | diag |
| NQ 7 (diag) | ref=prior_vwap |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 146 | 1 | 0.67 | -0.89 | 0.83 | 1.04 / 1.48 | 0.10 / -0.26 / 0.65 | 0.14 | 0.32 | 0.96 | -0.02 | 0.50 | 245 | diag |
| RTY 1 | ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 119 | 2 | 0.67 | -0.60 | 0.34 | -0.23 / 1.37 | 0.10 / -0.17 / -0.10 | -0.03 | 0.22 | 0.91 | -0.15 | 0.50 | 195 | NO |
| RTY 2 | ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 244 | 2 | 0.38 | -1.07 | 0.22 | -0.01 / 1.12 | 0.02 / -0.27 / 0.12 | -0.09 | 0.32 | 0.90 | -0.19 | 0.00 | 399 | NO |
| RTY 3 | ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 198 | 2 | 0.22 | -0.74 | 0.38 | 0.63 / 1.05 | 0.03 / -0.16 / 0.23 | -0.02 | -0.28 | 0.97 | -0.13 | 0.50 | 328 | NO |
| RTY 4 (diag) | ref=today_open |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 83 | 2 | 0.70 | -0.79 | 0.64 | 0.47 / 1.19 | 0.14 / -0.28 / 0.14 | 0.05 | -0.47 | 0.94 | -0.08 | 0.00 | 134 | diag |
| RTY 5 (diag) | ref=gap_only |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 37 | 1 | 0.20 | -0.10 | -0.26 | -0.89 / 1.13 | 0.01 / -0.48 / -0.31 | -0.15 | 0.68 | 0.49 | -0.33 | 0.00 | 57 S | diag |
| RTY 6 (diag) | ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 58 | 2 | 0.16 | -1.07 | 0.30 | 0.45 / 1.24 | 0.05 / -0.32 / 0.17 | 0.01 | -0.50 | 0.83 | -0.15 | 0.50 | 92 S | diag |
| YM 1 (diag) | ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 | 81 | 1 | 0.48 | -0.92 | 0.30 | -0.10 / 1.23 | 0.14 / 0.01 / -0.11 | 0.04 | -0.11 | 0.81 | -0.12 | 1.00 | 117 | diag |
| YM 2 (diag) | ref=gap_only |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 36 | 1 | 0.11 | -0.01 | -0.31 | -0.81 / 1.30 | -0.02 / -0.43 / -0.35 | -0.16 | -0.23 | 0.40 | -0.37 | 0.00 | 64 S | diag |
| YM 3 (diag) | ref=today_open |dist|>=0.7ADR against, entry 15:20 exit 15:55 | 88 | 1 | 0.01 | -0.42 | 0.03 | -0.06 / 1.07 | 0.04 / -0.21 / 0.02 | -0.03 | 0.05 | 0.74 | -0.17 | 0.00 | 133 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 8 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 2 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 16 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 4 |
| standalone pair-window Sharpe above own random-entry null p95 | 7 |
| worst-decile corr <= +0.30 | 14 |
| plateau >= 0.75 | 5 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 4 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | clean | 0.50 | 0.68 | -145193 | -103477 | 548501 | -360644 | 0.82 | 33.3 | 1.53 | -83598 | 269199 | -90480 |
| ES ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | H1 | -0.85 | -1.16 | -166430 | -143909 | 421313 | -188245 | -0.56 | 53.6 | 2.63 | -73253 | 130334 | -79236 |
| ES ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | H2 | 0.54 | 0.89 | -113818 | -94137 | 547397 | -124920 | 0.30 | 41.7 | 2.50 | -87472 | 219144 | -95655 |
| ES ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | all | 0.26 | 0.36 | -156407 | -113014 | 1000102 | -360644 | 0.38 | 38.7 | 1.92 | -83974 | 269199 | -95655 |
| NQ ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | clean | 1.33 | 2.34 | -114820 | -90919 | 299800 | -195300 | 4.01 | 41.0 | 1.69 | -83888 | 259402 | -90910 |
| NQ ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | H1 | 0.78 | 1.44 | -117976 | -99570 | 242525 | -123923 | 0.91 | 50.0 | 3.23 | -67139 | 134123 | -71370 |
| NQ ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | H2 | 2.31 | 5.51 | -80833 | -72887 | 383592 | -88332 | 2.33 | 41.7 | 2.93 | -92538 | 228505 | -94729 |
| NQ ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | all | 1.47 | 2.80 | -112578 | -90725 | 536585 | -195300 | 4.32 | 42.9 | 2.19 | -85143 | 259402 | -94729 |
| RTY ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | clean | 0.23 | 0.40 | -106923 | -91217 | 671569 | -123477 | 0.32 | 46.7 | 1.49 | -85615 | 263996 | -101754 |
| RTY ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | H1 | -1.44 | -1.91 | -82923 | -72883 | 330972 | -107382 | -0.77 | 57.1 | 2.67 | -71762 | 136527 | -74048 |
| RTY ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | H2 | 1.88 | 3.11 | -121490 | -83875 | 190885 | -190885 | 2.96 | 38.9 | 2.72 | -87369 | 221014 | -91281 |
| RTY ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | all | 0.38 | 0.62 | -113277 | -90678 | 671569 | -190885 | 0.78 | 47.0 | 1.94 | -85201 | 263996 | -101754 |
| YM ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 (diag) | clean | 0.52 | 0.85 | -143693 | -99972 | 489882 | -202197 | 0.97 | 22.9 | 1.60 | -79394 | 220511 | -85533 |
| YM ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 (diag) | H1 | -0.47 | -0.66 | -115352 | -105021 | 180247 | -117128 | -0.51 | 21.4 | 2.84 | -75318 | 168413 | -78287 |
| YM ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 (diag) | H2 | 0.13 | 0.16 | -202734 | -122434 | 362916 | -222270 | 0.11 | 11.1 | 2.38 | -99409 | 229108 | -119164 |
| YM ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 (diag) | all | 0.30 | 0.45 | -157177 | -110655 | 630238 | -222270 | 0.67 | 20.2 | 1.96 | -83748 | 229108 | -119164 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | -25.8 | 0.6 | 16.1 | 33.4 | -0.2 / 14.9 | 28.2 / 32.8 | NO |
| NQ ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | -4.7 | 7.8 | 15.4 | 35.1 | 8.7 / 17.5 | 43.3 / 47.4 | NO |
| RTY ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | -24.3 | -10.3 | 15.3 | 25.5 | -11.1 / 12.0 | 36.7 / 37.5 | NO |
| YM ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 (diag) | -25.4 | -36.6 | 18.9 | 28.8 | 21.3 / 27.2 | 30.0 / 30.8 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 667 | -27.7 | -57.1 | -42.9 | 29.4 | -0.46 / -0.94 / -0.71 | 63.0 / 33.6 |
| ES 2 (diag) ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 347 | -57.5 | -86.8 | -72.7 | 29.4 | -0.67 / -1.00 / -0.84 | 78.6 / 49.3 |
| ES 3 (diag) ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 969 | -27.1 | -56.4 | -42.4 | 29.4 | -0.58 / -1.21 / -0.91 | 32.8 / 3.4 |
| ES 4 (diag) ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1217 | -19.8 | -49.2 | -34.9 | 29.4 | -0.49 / -1.21 / -0.86 | 38.3 / 9.0 |
| NQ 1 ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1253 | -65.5 | -79.8 | -71.3 | 14.4 | -1.22 / -1.48 / -1.33 | 124.9 / 110.6 |
| NQ 2 ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 684 | -80.0 | -94.4 | -85.8 | 14.4 | -1.05 / -1.24 / -1.13 | 156.7 / 142.3 |
| NQ 3 ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1053 | -49.9 | -64.3 | -55.8 | 14.4 | -0.84 / -1.08 / -0.93 | 101.0 / 86.7 |
| NQ 4 ref=gap_only |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 656 | -37.7 | -52.1 | -43.5 | 14.4 | -0.44 / -0.60 / -0.51 | 123.3 / 108.9 |
| NQ 5 (diag) ref=today_open |dist|>=0.7ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 481 | -52.3 | -66.7 | -58.2 | 14.4 | -0.61 / -0.77 / -0.67 | 249.4 / 235.0 |
| NQ 6 (diag) ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 380 | -82.9 | -97.2 | -88.7 | 14.4 | -0.73 / -0.85 / -0.78 | 164.1 / 149.7 |
| NQ 7 (diag) ref=prior_vwap |dist|>=0.7ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 812 | -47.6 | -62.0 | -53.4 | 14.4 | -0.68 / -0.89 / -0.77 | 90.6 / 76.2 |
| RTY 1 ref=prior_close |dist|>=0.7ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 364 | -14.1 | -28.5 | -26.2 | 14.4 | -0.30 / -0.60 / -0.55 | 40.2 / 25.8 |
| RTY 2 ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 734 | -19.0 | -33.4 | -31.1 | 14.4 | -0.61 / -1.07 / -1.00 | 23.3 / 9.0 |
| RTY 3 ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 644 | -8.2 | -22.5 | -20.4 | 14.4 | -0.27 / -0.74 / -0.67 | 21.9 / 7.6 |
| RTY 4 (diag) ref=today_open |dist|>=0.7ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 256 | -22.6 | -37.0 | -34.7 | 14.4 | -0.49 / -0.79 / -0.74 | 53.4 / 39.1 |
| RTY 5 (diag) ref=gap_only |dist|>=0.7ADR against, entry 15:20 exit 15:55 | gross-positive, cost-negative pre-2023 | 78 | 3.2 | -11.2 | -8.4 | 14.4 | 0.03 / -0.10 / -0.07 | 28.2 / 13.9 |
| RTY 6 (diag) ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 198 | -51.3 | -65.6 | -63.4 | 14.4 | -0.84 / -1.07 / -1.03 | 29.1 / 14.8 |
| YM 1 (diag) ref=sess_vwap |dist|>=0.4ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 318 | -59.9 | -74.3 | -68.5 | 14.4 | -0.75 / -0.92 / -0.85 | 55.6 / 41.3 |
| YM 2 (diag) ref=gap_only |dist|>=0.7ADR against, entry 15:20 exit 15:55 | gross-positive, cost-negative pre-2023 | 222 | 13.3 | -1.1 | 5.0 | 14.4 | 0.13 / -0.01 / 0.05 | 24.2 / 9.8 |
| YM 3 (diag) ref=today_open |dist|>=0.7ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 387 | -15.2 | -29.6 | -23.7 | 14.4 | -0.22 / -0.42 / -0.34 | 18.8 / 4.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 1 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.51, p(top) = 0.27); NQ: 4 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 0.01, p(top) = 0.09); RTY: 3 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.02, p(top) = 0.32); YM: 0 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 1.00).
- Of 8 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.29 (NQ ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55); bootstrap lower bound > 0 for 2 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 2; gate_add PASS at some share: 4 (cell-share pairs).
- Gate-3 cell NQ ref=prior_close |dist|>=0.4ADR against, entry 15:20 exit 15:55: uplift +0.23/+0.40/+0.45, boot lo +0.10, plateau 1.00, 2x-slip +0.27, wd corr -0.20, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ ref=today_open |dist|>=0.4ADR against, entry 15:20 exit 15:55: uplift +0.18/+0.38/+0.29, boot lo +0.01, plateau 1.00, 2x-slip +0.21, wd corr +0.17, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 8}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_12.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm12/ (`BM12_CO_all_selected_scored.csv`).

DONE BM12
