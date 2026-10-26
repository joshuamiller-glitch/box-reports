# REPORT BJ7 - lunar cycle (BJ batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 3 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.04; best pair-window standalone Sharpe +1.27.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. lunar cycle. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      16 |          4 |         0 |               1.264 |                2 |          0 |            3 |
| NQ    |      16 |          4 |         1 |               1.255 |                2 |          1 |            3 |
| RTY   |      16 |          4 |         0 |               1.239 |                2 |          0 |            3 |
| YM    |      16 |          4 |         2 |               0.869 |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            0.8   |               4 |       1    |                     nan     |            0.742 |           1.321 |   nan    |     nan     |                1.48  |
| NQ    |     200 |                    1 |            1.025 |               4 |       0.65 |                       0.346 |            0.769 |           1.428 |     0.57 |       0.346 |                1.718 |
| RTY   |     200 |                    0 |            0.925 |               4 |       1    |                     nan     |            0.749 |           1.316 |   nan    |     nan     |                1.457 |
| YM    |     200 |                    2 |            0.96  |               4 |       0.24 |                       0.638 |            0.793 |           1.493 |     0.47 |       0.869 |                1.72  |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | full moon +-3.5d dir=long hold=c2c | 69 | 2 | 1.26 | 0.33 | 1.27 | 1.30 / 1.56 | 0.22 / 0.54 / 0.13 | 0.22 | 0.06 | 0.97 | 0.05 | 0.00 | 111 | diag |
| ES 2 (diag) | full moon +-2.0d dir=long hold=c2c | 40 | 2 | 0.99 | 0.30 | 0.45 | -0.30 / 1.94 | 0.15 / -0.13 / -0.17 | 0.03 | -0.28 | 0.63 | -0.15 | 0.50 | 62 S | diag |
| ES 3 (diag) | full moon +-2.0d dir=long hold=rth | 72 | 1 | 0.65 | -0.29 | 1.09 | 1.67 / 1.65 | 0.07 / 0.09 / 0.42 | 0.14 | -0.03 | 0.98 | -0.01 | 0.00 | 113 | diag |
| NQ 1 | full moon +-3.5d dir=short hold=rth | 123 | 2 | 0.35 | -0.51 | 0.32 | 0.30 / 1.20 | 0.03 / 0.50 / -0.39 | 0.01 | -0.05 | 0.83 | -0.19 | 0.00 | 196 | NO |
| NQ 2 (diag) | full moon +-3.5d dir=long hold=c2c | 69 | 2 | 1.26 | 0.46 | 1.17 | 1.10 / 1.67 | 0.21 / 0.25 / 0.17 | 0.21 | 0.06 | 0.98 | 0.01 | 0.00 | 111 | diag |
| NQ 3 (diag) | full moon +-2.0d dir=long hold=c2c | 40 | 2 | 0.86 | 0.34 | 0.47 | -0.08 / 1.94 | 0.11 / -0.26 / 0.05 | 0.04 | -0.20 | 0.67 | -0.17 | 0.00 | 62 S | diag |
| NQ 4 (diag) | new moon +-3.5d dir=short hold=c2c | 69 | 2 | 0.56 | 0.49 | -0.51 | -2.07 / 1.17 | 0.14 / -0.68 / -0.53 | -0.12 | 0.09 | 0.35 | -0.32 | 0.00 | 110 | diag |
| RTY 1 (diag) | new moon +-3.5d dir=short hold=c2c | 69 | 2 | 1.24 | -0.14 | 0.19 | -2.04 / 0.98 | 0.29 / -0.53 / -0.24 | 0.05 | -0.19 | 0.77 | -0.13 | 0.50 | 110 | diag |
| RTY 2 (diag) | full moon +-3.5d dir=long hold=c2c | 69 | 2 | 0.99 | 0.33 | 1.02 | 1.09 / 1.57 | 0.20 / 0.90 / -0.10 | 0.21 | 0.12 | 0.95 | 0.00 | 0.00 | 111 | diag |
| RTY 3 (diag) | full moon +-2.0d dir=long hold=c2c | 40 | 2 | 0.64 | 0.07 | -0.02 | -0.77 / 1.64 | 0.10 / 0.25 / -0.55 | -0.04 | -0.15 | 0.41 | -0.25 | 0.00 | 62 S | diag |
| YM 1 | new moon +-3.5d dir=long hold=rth | 124 | 2 | 0.87 | 0.03 | 0.36 | -0.48 / 1.58 | 0.13 / 0.23 / -0.29 | 0.03 | 0.43 | 0.61 | -0.14 | 0.00 | 199 | NO |
| YM 2 | full moon +-3.5d dir=short hold=rth | 123 | 2 | 0.41 | -0.30 | 0.17 | -0.19 / 0.99 | 0.03 / -0.28 / -0.10 | -0.05 | -0.02 | 0.81 | -0.21 | 0.00 | 196 | NO |
| YM 3 (diag) | full moon +-3.5d dir=long hold=c2c | 69 | 1 | 0.71 | 0.28 | 1.01 | 1.37 / 1.81 | 0.11 / 1.13 / 0.01 | 0.20 | 0.05 | 0.93 | -0.01 | 0.00 | 111 | diag |
| YM 4 (diag) | new moon +-2.0d dir=long hold=rth | 72 | 2 | 0.68 | -0.00 | 0.23 | -0.55 / 1.64 | 0.13 / 0.11 / -0.20 | 0.04 | 0.06 | 0.60 | -0.13 | 0.00 | 113 | diag |
| YM 5 (diag) | full moon +-2.0d dir=long hold=rth | 72 | 1 | 0.60 | -0.29 | 1.17 | 2.02 / 1.69 | 0.08 / 0.75 / 0.34 | 0.20 | -0.02 | 0.99 | 0.04 | 0.00 | 113 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 3 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 12 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 4 |
| standalone pair-window Sharpe above own random-entry null p95 | 5 |
| worst-decile corr <= +0.30 | 14 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 6 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES full moon +-3.5d dir=long hold=c2c (diag) | clean | 1.26 | 3.30 | -84717 | -65414 | 257463 | -116288 | 4.43 | 19.0 | 1.68 | -85905 | 239638 | -100569 |
| ES full moon +-3.5d dir=long hold=c2c (diag) | H1 | 1.22 | 2.09 | -172299 | -128530 | 264616 | -264616 | 1.63 | 21.4 | 3.37 | -77610 | 140983 | -78287 |
| ES full moon +-3.5d dir=long hold=c2c (diag) | H2 | 1.35 | 2.58 | -156478 | -112988 | 252359 | -186517 | 2.13 | 11.1 | 2.62 | -90397 | 244956 | -98270 |
| ES full moon +-3.5d dir=long hold=c2c (diag) | all | 1.27 | 2.62 | -127729 | -89739 | 264616 | -264616 | 7.97 | 17.9 | 2.13 | -86323 | 244956 | -100569 |
| NQ full moon +-3.5d dir=short hold=rth | clean | 0.35 | 0.49 | -168350 | -113883 | 510266 | -267855 | 0.62 | 16.2 | 1.49 | -84228 | 326440 | -98588 |
| NQ full moon +-3.5d dir=short hold=rth | H1 | 1.98 | 6.47 | -101656 | -83089 | 237421 | -124308 | 3.19 | 17.9 | 3.33 | -77610 | 161256 | -78287 |
| NQ full moon +-3.5d dir=short hold=rth | H2 | -1.28 | -1.55 | -259699 | -178266 | 986635 | -287083 | -0.53 | 25.0 | 2.10 | -90094 | 229205 | -97323 |
| NQ full moon +-3.5d dir=short hold=rth | all | 0.32 | 0.49 | -183757 | -129396 | 986635 | -287083 | 0.56 | 18.5 | 1.91 | -85689 | 326440 | -98588 |
| RTY full moon +-3.5d dir=long hold=c2c (diag) | clean | 0.98 | 2.06 | -105858 | -83722 | 443974 | -135376 | 2.01 | 19.0 | 1.66 | -84619 | 257971 | -99094 |
| RTY full moon +-3.5d dir=long hold=c2c (diag) | H1 | 1.89 | 3.37 | -186858 | -134615 | 244722 | -244722 | 2.81 | 10.7 | 3.72 | -77610 | 136632 | -78287 |
| RTY full moon +-3.5d dir=long hold=c2c (diag) | H2 | 0.45 | 0.71 | -212817 | -156776 | 350729 | -283297 | 0.60 | 22.2 | 2.39 | -92460 | 265151 | -100148 |
| RTY full moon +-3.5d dir=long hold=c2c (diag) | all | 1.02 | 1.83 | -153693 | -114342 | 443974 | -283297 | 4.03 | 18.5 | 2.12 | -86500 | 265151 | -100148 |
| YM new moon +-3.5d dir=long hold=rth | clean | 0.86 | 1.38 | -140634 | -91808 | 596104 | -253643 | 1.30 | 16.2 | 1.59 | -79997 | 281962 | -85125 |
| YM new moon +-3.5d dir=long hold=rth | H1 | 0.44 | 0.60 | -150012 | -108989 | 331976 | -217094 | 0.31 | 17.9 | 3.06 | -56609 | 161474 | -58291 |
| YM new moon +-3.5d dir=long hold=rth | H2 | -1.22 | -1.49 | -147934 | -131679 | 466703 | -173732 | -0.77 | 22.2 | 2.19 | -93303 | 233645 | -106952 |
| YM new moon +-3.5d dir=long hold=rth | all | 0.36 | 0.53 | -160445 | -112965 | 596104 | -253643 | 0.87 | 17.9 | 1.94 | -82667 | 281962 | -106952 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES full moon +-3.5d dir=long hold=c2c (diag) | -6.9 | -7.9 | 16.1 | 30.9 | -8.7 / 15.7 | 30.0 / 30.0 | NO |
| NQ full moon +-3.5d dir=short hold=rth | -23.9 | -4.5 | 13.0 | 5.2 | -5.4 / 12.4 | 30.0 / 30.0 | NO |
| RTY full moon +-3.5d dir=long hold=c2c (diag) | -10.4 | -7.0 | 13.3 | 20.1 | -6.3 / 18.6 | 30.0 / 30.0 | NO |
| YM new moon +-3.5d dir=long hold=rth | -24.3 | -14.4 | 18.8 | 22.8 | -0.4 / 21.1 | 51.3 / 56.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) full moon +-3.5d dir=long hold=c2c | positive pre-2023 | 351 | 132.7 | 103.4 | 117.7 | 29.4 | 0.43 / 0.33 / 0.38 | 545.3 / 515.9 |
| ES 2 (diag) full moon +-2.0d dir=long hold=c2c | positive pre-2023 | 187 | 159.6 | 130.2 | 144.5 | 29.4 | 0.36 / 0.30 / 0.33 | 419.4 / 390.0 |
| ES 3 (diag) full moon +-2.0d dir=long hold=rth | negative pre-2023 | 357 | -24.2 | -53.6 | -39.3 | 29.4 | -0.13 / -0.29 / -0.21 | 198.3 / 168.9 |
| NQ 1 full moon +-3.5d dir=short hold=rth | negative pre-2023 | 627 | -115.1 | -129.4 | -120.9 | 14.4 | -0.45 / -0.51 / -0.47 | 164.5 / 150.2 |
| NQ 2 (diag) full moon +-3.5d dir=long hold=c2c | positive pre-2023 | 351 | 235.3 | 221.0 | 229.6 | 14.4 | 0.49 / 0.46 / 0.48 | 966.4 / 952.1 |
| NQ 3 (diag) full moon +-2.0d dir=long hold=c2c | positive pre-2023 | 187 | 220.9 | 206.5 | 215.1 | 14.4 | 0.36 / 0.34 / 0.35 | 693.4 / 679.0 |
| NQ 4 (diag) new moon +-3.5d dir=short hold=c2c | positive pre-2023 | 357 | 242.5 | 228.2 | 236.8 | 14.4 | 0.52 / 0.49 / 0.51 | 466.3 / 451.9 |
| RTY 1 (diag) new moon +-3.5d dir=short hold=c2c | negative pre-2023 | 201 | -18.3 | -32.6 | -30.4 | 14.4 | -0.08 / -0.14 / -0.13 | 344.3 / 329.9 |
| RTY 2 (diag) full moon +-3.5d dir=long hold=c2c | positive pre-2023 | 198 | 98.2 | 83.8 | 86.1 | 14.4 | 0.38 / 0.33 / 0.34 | 237.5 / 223.1 |
| RTY 3 (diag) full moon +-2.0d dir=long hold=c2c | positive pre-2023 | 109 | 37.8 | 23.5 | 25.8 | 14.4 | 0.11 / 0.07 / 0.07 | 164.6 / 150.3 |
| YM 1 new moon +-3.5d dir=long hold=rth | positive pre-2023 | 643 | 17.9 | 3.5 | 9.3 | 14.4 | 0.16 / 0.03 / 0.08 | 165.8 / 151.4 |
| YM 2 full moon +-3.5d dir=short hold=rth | negative pre-2023 | 629 | -24.4 | -38.8 | -33.1 | 14.4 | -0.19 / -0.30 / -0.26 | 90.7 / 76.4 |
| YM 3 (diag) full moon +-3.5d dir=long hold=c2c | positive pre-2023 | 352 | 79.6 | 65.2 | 71.0 | 14.4 | 0.34 / 0.28 / 0.30 | 207.9 / 193.5 |
| YM 4 (diag) new moon +-2.0d dir=long hold=rth | gross-positive, cost-negative pre-2023 | 369 | 13.7 | -0.6 | 5.1 | 14.4 | 0.09 / -0.00 / 0.03 | 161.0 / 146.7 |
| YM 5 (diag) full moon +-2.0d dir=long hold=rth | negative pre-2023 | 359 | -28.1 | -42.4 | -36.7 | 14.4 | -0.20 / -0.29 / -0.26 | 114.7 / 100.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 0 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 1.00); NQ: 1 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.65, p(top) = 0.57); RTY: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); YM: 2 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.24, p(top) = 0.47).
- Of 3 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.04 (YM new moon +-3.5d dir=long hold=rth); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 2, 'positive pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_7.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj7/ (`BJ7_CO_all_selected_scored.csv`).

DONE BJ7
