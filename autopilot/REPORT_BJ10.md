# REPORT BJ10 - Globex volume share and overnight move (BJ batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 3 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.05; best pair-window standalone Sharpe +0.81.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. Globex volume share and overnight move. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |       8 |          4 |         1 |               1.041 |                2 |          1 |            3 |
| NQ    |       8 |          4 |         1 |               0.635 |                2 |          1 |            3 |
| RTY   |       8 |          4 |         1 |               0.958 |                2 |          1 |            3 |
| YM    |       8 |          4 |         0 |               0.525 |                2 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            0.71  |               3 |      0.535 |                       1.041 |            0.713 |           1.334 |    0.085 |       1.041 |                1.492 |
| NQ    |     200 |                    1 |            0.97  |               4 |      0.67  |                       0.505 |            0.782 |           1.6   |    0.475 |       0.505 |                1.882 |
| RTY   |     200 |                    1 |            0.705 |               3 |      0.535 |                       0.522 |            0.757 |           1.393 |    0.35  |       0.522 |                1.636 |
| YM    |     200 |                    0 |            0.69  |               4 |      1     |                     nan     |            0.815 |           1.405 |  nan     |     nan     |                1.552 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | 136 | 2 | 1.04 | 0.24 | 0.59 | -0.32 / 1.33 | 0.17 / -0.53 / 0.06 | 0.02 | 0.13 | 0.94 | -0.12 | 0.75 | 216 | NO |
| ES 2 (diag) | Globex volume/20d mean>=1.2 dir=against overnight move hold=flat | 136 | 1 | 0.94 | 0.38 | 0.69 | -0.19 / 1.38 | 0.14 / -0.13 / -0.06 | 0.05 | -0.60 | 0.95 | -0.04 | 1.00 | 216 | diag |
| ES 3 (diag) | Globex volume/20d mean>=1.5 dir=against overnight move hold=flat | 64 | 2 | 0.75 | 0.17 | 0.57 | 0.08 / 1.51 | 0.11 / -0.27 / 0.11 | 0.05 | -0.54 | 0.87 | -0.07 | 1.00 | 104 | diag |
| ES 4 (diag) | Globex volume/20d mean>=1.5 dir=against overnight move hold=120m | 64 | 2 | 0.35 | 0.13 | 0.33 | 0.29 / 1.46 | 0.03 / -0.42 / 0.25 | 0.00 | 0.44 | 0.85 | -0.17 | 0.75 | 104 | diag |
| NQ 1 | Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | 125 | 2 | 0.50 | 0.21 | 0.31 | -0.14 / 1.51 | 0.09 / -0.36 / 0.03 | 0.01 | -0.15 | 0.80 | -0.16 | 1.00 | 204 | NO |
| NQ 2 (diag) | Globex volume/20d mean>=1.5 dir=against overnight move hold=120m | 35 | 1 | 0.64 | 0.15 | 0.68 | 0.73 / 1.72 | 0.08 / -0.40 / 0.34 | 0.08 | 0.30 | 0.88 | -0.10 | 0.50 | 68 S | diag |
| NQ 3 (diag) | Globex volume/20d mean>=1.5 dir=against overnight move hold=flat | 35 | 1 | 0.63 | 0.41 | 0.57 | 0.45 / 1.36 | 0.07 / -0.31 / 0.17 | 0.04 | -0.54 | 0.86 | -0.08 | 0.50 | 68 S | diag |
| NQ 4 (diag) | Globex volume/20d mean>=1.2 dir=against overnight move hold=flat | 125 | 1 | 0.58 | 0.51 | 0.30 | -0.53 / 1.72 | 0.08 / -0.17 / -0.09 | 0.01 | -0.59 | 0.65 | -0.11 | 1.00 | 204 | diag |
| RTY 1 | Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | 137 | 2 | 0.52 | 0.14 | 0.18 | -0.46 / 1.26 | 0.05 / -0.17 / -0.22 | -0.05 | -0.18 | 0.77 | -0.21 | 0.00 | 225 | NO |
| RTY 2 (diag) | Globex volume/20d mean>=1.5 dir=against overnight move hold=flat | 69 | 1 | 0.96 | 0.29 | 0.81 | 0.42 / 1.31 | 0.13 / -0.10 / 0.14 | 0.09 | -0.61 | 0.95 | -0.01 | 0.50 | 113 | diag |
| RTY 3 (diag) | Globex volume/20d mean>=1.2 dir=against overnight move hold=flat | 137 | 1 | 0.95 | 0.43 | 0.77 | 0.29 / 1.60 | 0.14 / -0.09 / -0.01 | 0.07 | -0.51 | 0.95 | -0.05 | 1.00 | 225 | diag |
| RTY 4 (diag) | Globex volume/20d mean>=1.5 dir=against overnight move hold=120m | 69 | 2 | 0.52 | 0.15 | 0.04 | -0.78 / 1.33 | 0.03 / -0.30 / -0.14 | -0.06 | 0.40 | 0.68 | -0.23 | 0.00 | 113 | diag |
| YM 1 (diag) | Globex volume/20d mean>=1.5 dir=against overnight move hold=flat | 59 | 1 | 0.53 | 0.06 | 0.48 | 0.34 / 1.67 | 0.06 / -0.09 / 0.00 | 0.02 | -0.47 | 0.78 | -0.07 | 0.50 | 102 | diag |
| YM 2 (diag) | Globex volume/20d mean>=1.2 dir=against overnight move hold=flat | 131 | 1 | 0.52 | 0.24 | 0.32 | -0.33 / 1.41 | 0.06 / -0.14 / -0.11 | -0.01 | -0.47 | 0.73 | -0.12 | 0.00 | 218 | diag |
| YM 3 (diag) | Globex volume/20d mean>=1.5 dir=against overnight move hold=120m | 59 | 2 | 0.39 | -0.07 | 0.35 | 0.20 / 1.51 | 0.06 / -0.18 / -0.11 | -0.01 | -0.05 | 0.80 | -0.19 | 0.25 | 102 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 3 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 12 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 2 |
| worst-decile corr <= +0.30 | 12 |
| plateau >= 0.75 | 7 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 2 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | clean | 1.10 | 1.91 | -126799 | -96361 | 289132 | -203362 | 3.47 | 24.8 | 1.63 | -87413 | 287636 | -103361 |
| ES Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | H1 | -0.80 | -0.99 | -189033 | -158495 | 422681 | -258372 | -0.55 | 35.7 | 2.30 | -81313 | 187745 | -84339 |
| ES Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | H2 | 0.28 | 0.44 | -81544 | -74379 | 297778 | -85313 | 0.21 | 27.8 | 2.55 | -84769 | 232494 | -87013 |
| ES Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | all | 0.59 | 0.91 | -136019 | -103353 | 512517 | -258372 | 1.62 | 27.4 | 1.95 | -86506 | 287636 | -103361 |
| NQ Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | clean | 0.59 | 0.90 | -144554 | -106936 | 486336 | -214456 | 1.10 | 26.7 | 1.55 | -81155 | 302712 | -90517 |
| NQ Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | H1 | -0.41 | -0.56 | -148368 | -123152 | 370850 | -220724 | -0.29 | 35.7 | 2.47 | -77708 | 185725 | -78287 |
| NQ Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | H2 | 0.10 | 0.13 | -139832 | -109208 | 415033 | -179197 | 0.07 | 33.3 | 2.51 | -80939 | 209919 | -82524 |
| NQ Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | all | 0.31 | 0.46 | -154509 | -113321 | 486336 | -220724 | 0.94 | 29.2 | 1.92 | -80789 | 302712 | -90517 |
| RTY Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | clean | 0.52 | 0.78 | -139093 | -112280 | 701021 | -217994 | 0.68 | 31.4 | 1.51 | -84539 | 269098 | -95567 |
| RTY Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | H1 | 0.32 | 0.45 | -124881 | -108911 | 332064 | -168340 | 0.21 | 21.4 | 2.66 | -75576 | 173011 | -78287 |
| RTY Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | H2 | -1.04 | -1.28 | -112428 | -105278 | 339421 | -115155 | -0.87 | 38.9 | 2.26 | -95583 | 234977 | -96199 |
| RTY Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | all | 0.18 | 0.25 | -136417 | -116129 | 701021 | -217994 | 0.35 | 31.5 | 1.87 | -86299 | 269098 | -96199 |
| YM Globex volume/20d mean>=1.5 dir=against overnight move hold=flat (diag) | clean | 0.55 | 1.75 | -61673 | -45142 | 193970 | -161076 | 2.56 | 19.0 | 1.52 | -79732 | 255993 | -85327 |
| YM Globex volume/20d mean>=1.5 dir=against overnight move hold=flat (diag) | H1 | -0.03 | -0.04 | -64869 | -52902 | 144247 | -79901 | -0.02 | 17.9 | 2.74 | -82594 | 162943 | -86900 |
| YM Globex volume/20d mean>=1.5 dir=against overnight move hold=flat (diag) | H2 | 0.71 | 1.07 | -52597 | -40939 | 131898 | -56361 | 0.59 | 13.9 | 2.48 | -85472 | 217425 | -88419 |
| YM Globex volume/20d mean>=1.5 dir=against overnight move hold=flat (diag) | all | 0.48 | 1.32 | -64784 | -47291 | 235879 | -161076 | 2.42 | 17.3 | 1.92 | -82098 | 255993 | -88419 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | -20.9 | -16.3 | 5.0 | 11.6 | -9.4 / 5.9 | -22.6 / -3.7 | NO |
| NQ Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | -25.0 | -2.6 | 16.4 | 17.9 | 5.7 / 17.5 | -8.2 / 10.1 | NO |
| RTY Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | -27.3 | -0.1 | 12.0 | 19.7 | 4.9 / 15.8 | 28.4 / 28.6 | NO |
| YM Globex volume/20d mean>=1.5 dir=against overnight move hold=flat (diag) | -23.8 | 14.1 | 23.1 | 41.6 | 21.7 / 26.5 | 12.1 / 20.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | positive pre-2023 | 657 | 59.3 | 29.9 | 44.0 | 29.4 | 0.48 / 0.24 / 0.36 | 217.2 / 187.8 |
| ES 2 (diag) Globex volume/20d mean>=1.2 dir=against overnight move hold=flat | positive pre-2023 | 657 | 109.2 | 79.8 | 93.9 | 29.4 | 0.51 / 0.38 / 0.44 | 615.3 / 586.0 |
| ES 3 (diag) Globex volume/20d mean>=1.5 dir=against overnight move hold=flat | positive pre-2023 | 298 | 87.3 | 58.0 | 72.0 | 29.4 | 0.26 / 0.17 / 0.22 | 698.6 / 669.3 |
| ES 4 (diag) Globex volume/20d mean>=1.5 dir=against overnight move hold=120m | positive pre-2023 | 298 | 55.4 | 26.1 | 40.1 | 29.4 | 0.28 / 0.13 / 0.20 | 157.2 / 127.9 |
| NQ 1 Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | positive pre-2023 | 666 | 56.5 | 42.2 | 50.8 | 14.4 | 0.29 / 0.21 / 0.26 | 242.4 / 228.1 |
| NQ 2 (diag) Globex volume/20d mean>=1.5 dir=against overnight move hold=120m | positive pre-2023 | 290 | 62.7 | 48.4 | 56.9 | 14.4 | 0.19 / 0.15 / 0.17 | 665.4 / 651.1 |
| NQ 3 (diag) Globex volume/20d mean>=1.5 dir=against overnight move hold=flat | positive pre-2023 | 290 | 203.1 | 188.8 | 197.3 | 14.4 | 0.44 / 0.41 / 0.43 | 1705.9 / 1691.5 |
| NQ 4 (diag) Globex volume/20d mean>=1.2 dir=against overnight move hold=flat | positive pre-2023 | 666 | 179.8 | 165.5 | 174.1 | 14.4 | 0.56 / 0.51 / 0.54 | 696.4 / 682.0 |
| RTY 1 Globex volume/20d mean>=1.2 dir=against overnight move hold=120m | positive pre-2023 | 421 | 27.8 | 13.5 | 15.9 | 14.4 | 0.30 / 0.14 / 0.17 | 68.3 / 54.0 |
| RTY 2 (diag) Globex volume/20d mean>=1.5 dir=against overnight move hold=flat | positive pre-2023 | 200 | 81.6 | 67.2 | 69.6 | 14.4 | 0.35 / 0.29 / 0.30 | 435.7 / 421.4 |
| RTY 3 (diag) Globex volume/20d mean>=1.2 dir=against overnight move hold=flat | positive pre-2023 | 421 | 77.9 | 63.6 | 66.0 | 14.4 | 0.53 / 0.43 / 0.45 | 247.1 / 232.8 |
| RTY 4 (diag) Globex volume/20d mean>=1.5 dir=against overnight move hold=120m | positive pre-2023 | 200 | 38.8 | 24.4 | 26.8 | 14.4 | 0.24 / 0.15 / 0.16 | 101.8 / 87.5 |
| YM 1 (diag) Globex volume/20d mean>=1.5 dir=against overnight move hold=flat | positive pre-2023 | 277 | 29.4 | 15.0 | 20.9 | 14.4 | 0.11 / 0.06 / 0.08 | 518.0 / 503.6 |
| YM 2 (diag) Globex volume/20d mean>=1.2 dir=against overnight move hold=flat | positive pre-2023 | 664 | 48.1 | 33.7 | 39.6 | 14.4 | 0.34 / 0.24 / 0.28 | 250.3 / 236.0 |
| YM 3 (diag) Globex volume/20d mean>=1.5 dir=against overnight move hold=120m | gross-positive, cost-negative pre-2023 | 277 | 3.7 | -10.7 | -4.8 | 14.4 | 0.02 / -0.07 / -0.03 | 124.7 / 110.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 1 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.54, p(top) = 0.09); NQ: 1 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.67, p(top) = 0.47); RTY: 1 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.54, p(top) = 0.35); YM: 0 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 1.00).
- Of 3 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.05 (ES Globex volume/20d mean>=1.2 dir=against overnight move hold=120m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 3}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_10.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj10/ (`BJ10_CO_all_selected_scored.csv`).

DONE BJ10
