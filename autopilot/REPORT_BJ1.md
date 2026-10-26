# REPORT BJ1 - FOMC-cycle weeks (BJ batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 4 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.05; best pair-window standalone Sharpe +0.42.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. FOMC-cycle weeks. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |       8 |          8 |         0 |               0.492 |                1 |          0 |            3 |
| NQ    |       8 |          8 |         1 |               0.38  |                2 |          1 |            3 |
| RTY   |       8 |          8 |         1 |               0.26  |                2 |          1 |            3 |
| YM    |       8 |          8 |         2 |               0.549 |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            1.935 |               6 |      1     |                     nan     |            0.728 |           1.211 |   nan    |     nan     |                1.529 |
| NQ    |     200 |                    1 |            2.01  |               6 |      0.88  |                       0.38  |            0.719 |           1.273 |     0.78 |       0.38  |                1.579 |
| RTY   |     200 |                    1 |            1.59  |               7 |      0.875 |                       0.26  |            0.635 |           1.164 |     0.82 |       0.26  |                1.337 |
| YM    |     200 |                    2 |            1.845 |               4 |      0.605 |                       0.342 |            0.705 |           1.279 |     0.83 |       0.549 |                1.441 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | FOMC cycle even weeks dir=long hold=c2c | 145 | 1 | 0.49 | 0.42 | 0.35 | 0.13 / 1.94 | 0.04 / -0.12 / 0.15 | 0.02 | 0.34 | 0.45 | -0.13 | 0.00 | 234 | diag |
| ES 2 (diag) | FOMC cycle odd weeks dir=long hold=c2c | 136 | 1 | 0.31 | -0.35 | 0.20 | 0.08 / 2.09 | -0.02 / 0.51 / -0.40 | -0.06 | 0.23 | 0.24 | -0.23 | 0.00 | 218 | diag |
| ES 3 (diag) | FOMC cycle odd weeks dir=long hold=rth | 241 | 1 | 0.21 | 0.04 | 0.17 | 0.16 / 1.71 | -0.04 / 0.09 / -0.01 | -0.05 | -0.25 | 0.48 | -0.18 | 0.00 | 385 | diag |
| NQ 1 | FOMC cycle odd weeks dir=long hold=rth | 241 | 2 | 0.38 | 0.24 | 0.25 | 0.09 / 1.36 | -0.01 / -0.05 / -0.01 | -0.03 | -0.13 | 0.60 | -0.20 | 0.00 | 385 | NO |
| NQ 2 (diag) | FOMC cycle even weeks dir=long hold=c2c | 145 | 1 | 0.37 | 0.60 | 0.26 | 0.14 / 1.51 | 0.02 / -0.21 / 0.18 | 0.01 | 0.05 | 0.36 | -0.17 | 0.00 | 234 | diag |
| NQ 3 (diag) | FOMC cycle odd weeks dir=long hold=c2c | 136 | 1 | 0.30 | -0.07 | 0.23 | 0.12 / 1.69 | -0.02 / 0.51 / -0.42 | -0.05 | 0.23 | 0.45 | -0.24 | 0.00 | 218 | diag |
| NQ 4 (diag) | FOMC cycle even weeks dir=short hold=rth | 275 | 1 | 0.09 | -0.54 | 0.00 | -0.22 / 1.21 | -0.04 / -0.04 / -0.13 | -0.07 | -0.56 | 0.74 | -0.23 | 0.00 | 444 | diag |
| RTY 1 | FOMC cycle odd weeks dir=short hold=rth | 241 | 2 | 0.26 | 0.04 | -0.08 | -0.72 / 0.62 | 0.07 / -0.74 / -0.02 | -0.07 | 0.11 | 0.60 | -0.25 | 0.00 | 385 | NO |
| RTY 2 (diag) | FOMC cycle even weeks dir=long hold=c2c | 145 | 1 | -0.04 | 0.04 | -0.08 | -0.05 / 1.57 | -0.06 / -0.23 / 0.14 | -0.06 | 0.23 | 0.41 | -0.22 | 0.00 | 234 | diag |
| RTY 3 (diag) | FOMC cycle odd weeks dir=short hold=c2c | 136 | 1 | -0.09 | 0.33 | -0.09 | -0.15 / 1.03 | -0.01 / -0.86 / 0.31 | -0.06 | -0.01 | 0.60 | -0.24 | 0.00 | 218 | diag |
| RTY 4 (diag) | FOMC cycle odd weeks dir=long hold=c2c | 136 | 1 | -0.10 | -0.50 | -0.09 | -0.02 / 1.75 | -0.08 / 0.76 / -0.43 | -0.08 | 0.01 | 0.35 | -0.26 | 0.00 | 218 | diag |
| YM 1 | FOMC cycle even weeks dir=long hold=c2c | 145 | 2 | 0.55 | 0.29 | 0.42 | 0.27 / 1.84 | 0.05 / 0.09 / 0.10 | 0.05 | 0.28 | 0.53 | -0.11 | 0.00 | 234 | NO |
| YM 2 | FOMC cycle odd weeks dir=long hold=c2c | 136 | 2 | 0.13 | -0.23 | -0.33 | -0.87 / 1.85 | -0.05 / 0.38 / -0.66 | -0.14 | 0.14 | 0.07 | -0.34 | 0.00 | 218 | NO |
| YM 3 (diag) | FOMC cycle even weeks dir=long hold=rth | 275 | 1 | 0.53 | 0.03 | 0.02 | -0.61 / 1.71 | 0.10 / 0.41 / -0.45 | -0.00 | 0.48 | 0.37 | -0.17 | 0.00 | 444 | diag |
| YM 4 (diag) | FOMC cycle odd weeks dir=long hold=rth | 241 | 1 | 0.20 | 0.26 | 0.17 | 0.19 / 1.59 | -0.03 / 0.32 / -0.11 | -0.03 | -0.32 | 0.43 | -0.17 | 0.00 | 385 | diag |
| YM 5 (diag) | FOMC cycle odd weeks dir=short hold=c2c | 136 | 0 | -0.29 | 0.05 | 0.19 | 0.74 / 0.52 | -0.04 / -0.55 / 0.49 | 0.00 | -0.15 | 0.94 | -0.18 | 0.00 | 218 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 4 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 5 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 0 |
| worst-decile corr <= +0.30 | 14 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES FOMC cycle even weeks dir=long hold=c2c (diag) | clean | 0.47 | 0.81 | -107001 | -85775 | 376499 | -244893 | 1.13 | 46.7 | 1.50 | -85035 | 284116 | -88239 |
| ES FOMC cycle even weeks dir=long hold=c2c (diag) | H1 | -0.52 | -0.68 | -98717 | -88324 | 409521 | -116197 | -0.23 | 35.7 | 2.71 | -72243 | 149168 | -73647 |
| ES FOMC cycle even weeks dir=long hold=c2c (diag) | H2 | 0.55 | 0.80 | -111110 | -97819 | 301065 | -121520 | 0.51 | 44.4 | 2.63 | -79989 | 205254 | -80310 |
| ES FOMC cycle even weeks dir=long hold=c2c (diag) | all | 0.35 | 0.57 | -112280 | -91149 | 703497 | -244893 | 0.69 | 44.6 | 1.93 | -83298 | 284116 | -88239 |
| NQ FOMC cycle odd weeks dir=long hold=rth | clean | 0.36 | 0.61 | -110731 | -93983 | 524111 | -166366 | 0.62 | 42.9 | 1.45 | -85071 | 315039 | -92192 |
| NQ FOMC cycle odd weeks dir=long hold=rth | H1 | -0.47 | -0.58 | -139511 | -128534 | 376562 | -161479 | -0.29 | 35.7 | 2.77 | -76209 | 162036 | -76766 |
| NQ FOMC cycle odd weeks dir=long hold=rth | H2 | 0.42 | 0.59 | -188791 | -144184 | 460941 | -239213 | 0.35 | 38.9 | 2.48 | -83996 | 248521 | -85468 |
| NQ FOMC cycle odd weeks dir=long hold=rth | all | 0.25 | 0.37 | -141795 | -115565 | 524111 | -239213 | 0.72 | 41.1 | 1.87 | -84218 | 315039 | -92192 |
| RTY FOMC cycle odd weeks dir=short hold=rth | clean | 0.34 | 0.46 | -136775 | -107396 | 515588 | -331848 | 0.59 | 44.8 | 1.53 | -87047 | 228365 | -94869 |
| RTY FOMC cycle odd weeks dir=short hold=rth | H1 | -2.06 | -2.31 | -157643 | -156140 | 639481 | -160761 | -0.90 | 46.4 | 2.08 | -81754 | 219520 | -88295 |
| RTY FOMC cycle odd weeks dir=short hold=rth | H2 | 0.50 | 0.68 | -139474 | -117827 | 268984 | -160935 | 0.57 | 33.3 | 2.46 | -87058 | 227070 | -90825 |
| RTY FOMC cycle odd weeks dir=short hold=rth | all | -0.08 | -0.10 | -157840 | -125815 | 1191119 | -331848 | -0.10 | 42.9 | 1.84 | -87485 | 228365 | -94869 |
| YM FOMC cycle even weeks dir=long hold=c2c | clean | 0.49 | 0.83 | -113292 | -89794 | 346236 | -237003 | 1.29 | 43.8 | 1.51 | -86375 | 265060 | -93965 |
| YM FOMC cycle even weeks dir=long hold=c2c | H1 | 0.26 | 0.36 | -105721 | -96508 | 301162 | -125786 | 0.16 | 42.9 | 2.92 | -72261 | 146155 | -75615 |
| YM FOMC cycle even weeks dir=long hold=c2c | H2 | 0.28 | 0.43 | -125890 | -111252 | 317449 | -130098 | 0.29 | 52.8 | 2.58 | -83552 | 215086 | -84537 |
| YM FOMC cycle even weeks dir=long hold=c2c | all | 0.42 | 0.67 | -122094 | -98547 | 531093 | -237003 | 1.11 | 45.8 | 1.95 | -85064 | 265060 | -93965 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES FOMC cycle even weeks dir=long hold=c2c (diag) | -24.7 | 13.2 | 21.5 | 24.1 | 12.5 / 17.0 | 38.9 / 40.4 | NO |
| NQ FOMC cycle odd weeks dir=long hold=rth | -25.9 | 3.0 | 16.5 | 11.3 | 4.8 / 14.9 | 31.5 / 32.7 | NO |
| RTY FOMC cycle odd weeks dir=short hold=rth | -31.3 | 2.2 | 11.4 | 24.9 | 1.5 / 12.5 | 9.4 / 12.8 | NO |
| YM FOMC cycle even weeks dir=long hold=c2c | -23.6 | 3.9 | 18.1 | 24.0 | 3.1 / 14.0 | 35.1 / 40.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) FOMC cycle even weeks dir=long hold=c2c | positive pre-2023 | 763 | 112.9 | 83.5 | 97.8 | 29.4 | 0.56 / 0.42 / 0.49 | 192.6 / 163.2 |
| ES 2 (diag) FOMC cycle odd weeks dir=long hold=c2c | negative pre-2023 | 715 | -41.1 | -70.5 | -56.3 | 29.4 | -0.20 / -0.35 / -0.28 | 109.9 / 80.6 |
| ES 3 (diag) FOMC cycle odd weeks dir=long hold=rth | positive pre-2023 | 1253 | 34.2 | 4.8 | 19.0 | 29.4 | 0.31 / 0.04 / 0.17 | 70.5 / 41.1 |
| NQ 1 FOMC cycle odd weeks dir=long hold=rth | positive pre-2023 | 1254 | 58.2 | 43.9 | 52.4 | 14.4 | 0.32 / 0.24 / 0.29 | 161.3 / 146.9 |
| NQ 2 (diag) FOMC cycle even weeks dir=long hold=c2c | positive pre-2023 | 763 | 188.9 | 174.5 | 183.1 | 14.4 | 0.65 / 0.60 / 0.63 | 236.0 / 221.7 |
| NQ 3 (diag) FOMC cycle odd weeks dir=long hold=c2c | negative pre-2023 | 715 | -7.3 | -21.6 | -13.0 | 14.4 | -0.02 / -0.07 / -0.04 | 192.1 / 177.7 |
| NQ 4 (diag) FOMC cycle even weeks dir=short hold=rth | negative pre-2023 | 1409 | -77.3 | -91.7 | -83.1 | 14.4 | -0.45 / -0.54 / -0.49 | 62.3 / 47.9 |
| RTY 1 FOMC cycle odd weeks dir=short hold=rth | positive pre-2023 | 716 | 17.5 | 3.2 | 5.4 | 14.4 | 0.21 / 0.04 / 0.06 | 50.8 / 36.4 |
| RTY 2 (diag) FOMC cycle even weeks dir=long hold=c2c | positive pre-2023 | 435 | 23.5 | 9.2 | 11.4 | 14.4 | 0.13 / 0.04 / 0.06 | -4.8 / -19.2 |
| RTY 3 (diag) FOMC cycle odd weeks dir=short hold=c2c | positive pre-2023 | 403 | 70.6 | 56.2 | 58.4 | 14.4 | 0.41 / 0.33 / 0.34 | 7.8 / -6.5 |
| RTY 4 (diag) FOMC cycle odd weeks dir=long hold=c2c | negative pre-2023 | 403 | -70.6 | -85.0 | -82.8 | 14.4 | -0.41 / -0.50 / -0.49 | -7.8 / -22.2 |
| YM 1 FOMC cycle even weeks dir=long hold=c2c | positive pre-2023 | 761 | 63.7 | 49.4 | 55.1 | 14.4 | 0.38 / 0.29 / 0.33 | 124.5 / 110.1 |
| YM 2 FOMC cycle odd weeks dir=long hold=c2c | negative pre-2023 | 716 | -23.0 | -37.3 | -31.6 | 14.4 | -0.14 / -0.23 / -0.20 | 26.2 / 11.9 |
| YM 3 (diag) FOMC cycle even weeks dir=long hold=rth | positive pre-2023 | 1411 | 17.1 | 2.8 | 8.5 | 14.4 | 0.20 / 0.03 / 0.10 | 62.3 / 47.9 |
| YM 4 (diag) FOMC cycle odd weeks dir=long hold=rth | positive pre-2023 | 1256 | 35.9 | 21.5 | 27.2 | 14.4 | 0.43 / 0.26 / 0.33 | 40.3 / 26.0 |
| YM 5 (diag) FOMC cycle odd weeks dir=short hold=c2c | positive pre-2023 | 716 | 23.0 | 8.6 | 14.4 | 14.4 | 0.14 / 0.05 / 0.09 | -26.2 / -40.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 0 cells pass the clean rule against a replicate mean of 1.9 (p(count) = 1.00); NQ: 1 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.88, p(top) = 0.78); RTY: 1 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.88, p(top) = 0.82); YM: 2 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 0.60, p(top) = 0.83).
- Of 4 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.05 (YM FOMC cycle even weeks dir=long hold=c2c); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 3, 'negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_1.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj1/ (`BJ1_CO_all_selected_scored.csv`).

DONE BJ1
