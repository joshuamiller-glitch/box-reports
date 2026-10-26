# REPORT BI7 - semi-monthly payday windows (BI batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe +1.64.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BI', before the first run)
- Rule: see IDEAS_BI.md / PREREG_AUTOPILOT.md BATCH BI (frozen before the first run). semi-monthly payday windows
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      24 |          0 |         0 |               0.648 |                2 |          0 |            3 |
| NQ    |      24 |          0 |         0 |               1.282 |                2 |          0 |            3 |
| RTY   |      24 |          0 |         0 |               1.068 |                2 |          0 |            3 |
| YM    |      24 |          0 |         0 |               0.775 |                2 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| NQ    |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| RTY   |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| YM    |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | anchor 15th offset +1d hold=1d dir=short | 24 | 1 | 0.65 | -0.60 | 1.39 | 2.24 / 1.43 | 0.11 / 0.54 / 0.54 | 0.26 | -0.43 | 0.99 | 0.08 | 0.00 | 39 S | diag |
| ES 2 (diag) | anchor 15th offset -1d hold=2d dir=long | 22 | 2 | 0.58 | 0.56 | 0.56 | 0.53 / 1.27 | 0.05 / 0.08 / 0.16 | 0.06 | -0.42 | 0.84 | -0.12 | 0.00 | 36 S | diag |
| ES 3 (diag) | anchor 15th offset +0d hold=2d dir=short | 24 | 2 | 0.44 | -1.04 | 1.04 | 2.05 / 1.54 | 0.11 / 0.41 / 0.21 | 0.19 | -0.15 | 0.99 | 0.04 | 0.00 | 39 S | diag |
| NQ 1 (diag) | anchor 15th offset +1d hold=1d dir=short | 24 | 2 | 1.28 | -0.37 | 1.64 | 2.16 / 1.26 | 0.22 / 0.34 / 0.96 | 0.42 | -0.57 | 1.00 | 0.18 | 0.00 | 39 S | diag |
| NQ 2 (diag) | anchor 15th offset +0d hold=2d dir=short | 24 | 2 | 0.84 | -0.89 | 1.32 | 1.89 / 1.40 | 0.21 / 0.31 / 0.49 | 0.31 | -0.43 | 0.98 | 0.12 | 0.00 | 39 S | diag |
| NQ 3 (diag) | anchor 15th offset +1d hold=2d dir=short | 22 | 2 | 0.77 | 0.19 | 1.02 | 1.34 / 1.35 | 0.05 / 0.28 / 0.58 | 0.18 | -0.66 | 0.99 | -0.02 | 0.00 | 35 S | diag |
| RTY 1 (diag) | anchor 1st offset -1d hold=2d dir=short | 23 | 2 | 1.07 | -0.59 | 0.48 | -0.37 / 1.35 | 0.16 / 0.21 / -0.32 | 0.04 | -0.28 | 0.79 | -0.15 | 0.00 | 37 S | diag |
| RTY 2 (diag) | anchor 1st offset -1d hold=1d dir=short | 24 | 2 | 0.83 | -0.07 | 0.58 | -0.03 / 1.62 | 0.17 / 0.21 / -0.28 | 0.06 | -0.13 | 0.84 | -0.15 | 0.00 | 38 S | diag |
| RTY 3 (diag) | anchor 15th offset -1d hold=2d dir=long | 22 | 2 | 0.78 | 0.26 | 0.54 | 0.18 / 1.41 | 0.10 / 0.05 / 0.06 | 0.07 | -0.29 | 0.85 | -0.12 | 0.00 | 36 S | diag |
| YM 1 (diag) | anchor 15th offset -1d hold=2d dir=long | 22 | 2 | 0.78 | 0.52 | 0.55 | 0.17 / 1.35 | 0.10 / 0.00 / 0.17 | 0.08 | -0.28 | 0.85 | -0.10 | 0.00 | 36 S | diag |
| YM 2 (diag) | anchor 1st offset +1d hold=2d dir=short | 22 | 1 | 0.43 | -0.53 | -0.70 | -2.51 / 1.71 | 0.05 / -0.91 / -0.41 | -0.19 | -0.18 | 0.12 | -0.39 | 0.00 | 35 S | diag |
| YM 3 (diag) | anchor 1st offset -1d hold=1d dir=long | 24 | 1 | 0.38 | -0.31 | 0.25 | 0.43 / 1.54 | -0.01 / -0.07 / 0.13 | 0.00 | 0.14 | 0.67 | -0.18 | 0.00 | 38 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 4 |
| standalone pair-window Sharpe above own random-entry null p95 | 5 |
| worst-decile corr <= +0.30 | 12 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 12 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES anchor 15th offset +1d hold=1d dir=short (diag) | clean | 0.64 | 1.23 | -126082 | -85683 | 478092 | -173242 | 1.22 | 11.4 | 1.57 | -79612 | 265108 | -82569 |
| ES anchor 15th offset +1d hold=1d dir=short (diag) | H1 | 2.33 | 38.17 | -12481 | -8320 | 24961 | -24961 | 28.01 | 3.6 | 3.36 | -77610 | 151713 | -78287 |
| ES anchor 15th offset +1d hold=1d dir=short (diag) | H2 | 2.24 | 10.22 | -94340 | -47170 | 143314 | -143314 | 8.92 | 5.6 | 3.02 | -78535 | 217425 | -79653 |
| ES anchor 15th offset +1d hold=1d dir=short (diag) | all | 1.39 | 3.87 | -113688 | -68357 | 478092 | -173242 | 5.36 | 8.9 | 2.17 | -79225 | 265108 | -82569 |
| NQ anchor 15th offset +1d hold=1d dir=short (diag) | clean | 1.28 | 3.25 | -96579 | -61348 | 420786 | -128785 | 2.75 | 8.6 | 1.68 | -80739 | 254297 | -89334 |
| NQ anchor 15th offset +1d hold=1d dir=short (diag) | H1 | 1.89 | 6.07 | -79326 | -52884 | 129360 | -129360 | 4.57 | 7.1 | 3.17 | -77610 | 151713 | -78287 |
| NQ anchor 15th offset +1d hold=1d dir=short (diag) | H2 | 2.43 | 20.20 | -74151 | -43176 | 172706 | -116420 | 11.98 | 8.3 | 3.44 | -78535 | 217425 | -79653 |
| NQ anchor 15th offset +1d hold=1d dir=short (diag) | all | 1.64 | 6.88 | -98145 | -59188 | 420786 | -129360 | 9.07 | 8.3 | 2.32 | -79977 | 254297 | -89334 |
| RTY anchor 15th offset -1d hold=2d dir=long (diag) | clean | 0.78 | 1.27 | -134298 | -78125 | 316966 | -283947 | 2.22 | 7.6 | 1.56 | -91749 | 241517 | -133848 |
| RTY anchor 15th offset -1d hold=2d dir=long (diag) | H1 | 0.47 | 0.87 | -148757 | -109270 | 270670 | -241542 | 0.59 | 14.3 | 2.88 | -77610 | 151713 | -78287 |
| RTY anchor 15th offset -1d hold=2d dir=long (diag) | H2 | -0.19 | -0.22 | -163540 | -83800 | 250101 | -250101 | -0.20 | 8.3 | 2.54 | -78535 | 217425 | -79653 |
| RTY anchor 15th offset -1d hold=2d dir=long (diag) | all | 0.54 | 0.85 | -154268 | -91265 | 316966 | -283947 | 2.57 | 8.9 | 1.98 | -87317 | 241517 | -133848 |
| YM anchor 15th offset -1d hold=2d dir=long (diag) | clean | 0.77 | 1.44 | -128264 | -84766 | 298811 | -185404 | 2.34 | 9.5 | 1.56 | -89776 | 239960 | -114139 |
| YM anchor 15th offset -1d hold=2d dir=long (diag) | H1 | -0.05 | -0.07 | -143328 | -111746 | 286656 | -173872 | -0.04 | 10.7 | 2.83 | -77610 | 151713 | -78287 |
| YM anchor 15th offset -1d hold=2d dir=long (diag) | H2 | 0.32 | 0.48 | -150341 | -101029 | 217777 | -186339 | 0.45 | 8.3 | 2.65 | -78535 | 217425 | -79653 |
| YM anchor 15th offset -1d hold=2d dir=long (diag) | all | 0.55 | 0.93 | -141978 | -98340 | 298811 | -186339 | 2.63 | 9.5 | 1.98 | -86001 | 239960 | -114139 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES anchor 15th offset +1d hold=1d dir=short (diag) | -2.0 | 20.6 | 27.6 | 19.4 | 20.0 / 25.6 | 30.0 / 30.0 | NO |
| NQ anchor 15th offset +1d hold=1d dir=short (diag) | 11.7 | 8.3 | 26.4 | 24.3 | 7.6 / 23.8 | 30.0 / 30.0 | NO |
| RTY anchor 15th offset -1d hold=2d dir=long (diag) | -21.1 | -68.6 | 14.1 | 28.7 | -69.9 / 5.2 | 30.0 / 30.0 | NO |
| YM anchor 15th offset -1d hold=2d dir=long (diag) | -21.4 | -32.8 | 16.5 | 30.6 | -33.8 / 8.9 | 30.0 / 30.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) anchor 15th offset +1d hold=1d dir=short | negative pre-2023 | 126 | -156.6 | -186.0 | -171.8 | 29.4 | -0.51 / -0.60 / -0.56 | 253.1 / 223.8 |
| ES 2 (diag) anchor 15th offset -1d hold=2d dir=long | positive pre-2023 | 117 | 303.1 | 273.7 | 288.1 | 29.4 | 0.62 / 0.56 / 0.59 | 559.7 / 530.3 |
| ES 3 (diag) anchor 15th offset +0d hold=2d dir=short | negative pre-2023 | 122 | -548.0 | -577.3 | -563.1 | 29.4 | -0.99 / -1.04 / -1.02 | 347.4 / 318.0 |
| NQ 1 (diag) anchor 15th offset +1d hold=1d dir=short | negative pre-2023 | 126 | -190.5 | -204.9 | -196.3 | 14.4 | -0.35 / -0.37 / -0.36 | 852.5 / 838.1 |
| NQ 2 (diag) anchor 15th offset +0d hold=2d dir=short | negative pre-2023 | 122 | -745.8 | -760.2 | -751.6 | 14.4 | -0.87 / -0.89 / -0.88 | 1037.9 / 1023.6 |
| NQ 3 (diag) anchor 15th offset +1d hold=2d dir=short | positive pre-2023 | 123 | 171.7 | 157.3 | 165.9 | 14.4 | 0.20 / 0.19 / 0.20 | 1111.4 / 1097.0 |
| RTY 1 (diag) anchor 1st offset -1d hold=2d dir=short | negative pre-2023 | 68 | -263.9 | -278.3 | -276.0 | 14.4 | -0.56 / -0.59 / -0.59 | 497.4 / 483.0 |
| RTY 2 (diag) anchor 1st offset -1d hold=1d dir=short | negative pre-2023 | 72 | -20.6 | -35.0 | -32.7 | 14.4 | -0.02 / -0.07 / -0.07 | 305.8 / 291.5 |
| RTY 3 (diag) anchor 15th offset -1d hold=2d dir=long | positive pre-2023 | 66 | 125.6 | 111.2 | 113.5 | 14.4 | 0.29 / 0.26 / 0.27 | 425.9 / 411.5 |
| YM 1 (diag) anchor 15th offset -1d hold=2d dir=long | positive pre-2023 | 117 | 227.8 | 213.5 | 219.3 | 14.4 | 0.56 / 0.52 / 0.54 | 524.3 / 510.0 |
| YM 2 (diag) anchor 1st offset +1d hold=2d dir=short | negative pre-2023 | 114 | -254.0 | -268.4 | -262.6 | 14.4 | -0.50 / -0.53 / -0.52 | 310.0 / 295.6 |
| YM 3 (diag) anchor 1st offset -1d hold=1d dir=long | negative pre-2023 | 126 | -70.8 | -85.1 | -79.4 | 14.4 | -0.26 / -0.31 / -0.29 | 81.9 / 67.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); NQ: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); RTY: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); YM: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bi_7.py, ap_bi_pipe.py (= ap_b_pipe2 with module swap), ap_bi_job.sh, ap_sw_common.py, ap_bi_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bi7/ (`BI7_CO_all_selected_scored.csv`).

DONE BI7
