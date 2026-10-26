# REPORT SW33 - scheduled-release event bars on BTC (D10 H2-H4 M1-M3, BTC only)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 9 selected cells (+1 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.09; best pair-window standalone Sharpe +0.61.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Sets THU/TNC/ALL as SW7; enter k = 1/5/15 min after release with/against the move since the minute before it; hold 5-240 min or to the 16:55 flatten.
- Instruments: BTC. Grid: 126 cells.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV); multi-day holds carry overnight and weekend gap risk (no stop). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     126 |         84 |         9 |               1.416 |                2 |          9 |            1 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| BTC   |     200 |                    9 |            9.815 |              16 |       0.65 |                       0.327 |            0.768 |            1.04 |        1 |       0.639 |                1.998 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 1 | BTC ALL release+15m dir=with hold=240m | 104 | 2 | 0.64 | -1.71 | 0.34 | -0.03 / 1.32 | 0.07 / -0.38 / 0.06 | -0.01 | 0.32 | 0.83 | -0.19 | 0.25 | 169 | NO |
| BTC 2 | BTC TNC release+15m dir=with hold=240m | 106 | 2 | 0.55 | -1.71 | 0.29 | -0.03 / 1.15 | 0.06 / -0.38 / 0.06 | -0.01 | 0.32 | 0.77 | -0.19 | 0.00 | 171 | NO |
| BTC 3 | BTC ALL release+1m dir=with hold=flat | 141 | 2 | 0.49 | -2.49 | 0.01 | -0.90 / 1.63 | 0.02 / -0.68 / 0.11 | -0.08 | 0.37 | 0.51 | -0.25 | 0.00 | 219 | NO |
| BTC 4 | BTC ALL release+5m dir=with hold=flat | 134 | 2 | 0.40 | -2.15 | -0.47 | -2.14 / 1.80 | -0.01 / -1.27 / 0.09 | -0.19 | 0.46 | 0.17 | -0.37 | 0.00 | 207 | NO |
| BTC 5 | BTC TNC release+1m dir=against hold=240m | 126 | 2 | 0.30 | 0.77 | 0.33 | 0.35 / 1.25 | 0.04 / 0.27 / -0.22 | 0.01 | -0.51 | 0.75 | -0.17 | 0.00 | 196 | NO |
| BTC 6 | BTC ALL release+15m dir=with hold=60m | 120 | 2 | 0.24 | -0.78 | 0.38 | 0.33 / 1.31 | 0.02 / 0.00 / -0.02 | -0.01 | 0.14 | 0.80 | -0.15 | 0.75 | 193 | NO |
| BTC 7 | BTC TNC release+5m dir=against hold=15m | 120 | 2 | 0.21 | 0.21 | -0.06 | -0.55 / 1.32 | 0.01 / 0.12 / -0.40 | -0.13 | -0.43 | 0.73 | -0.27 | 0.00 | 185 | NO |
| BTC 8 | BTC TNC release+5m dir=against hold=240m | 119 | 2 | 0.09 | 1.00 | 0.55 | 1.25 / 1.49 | 0.03 / 0.82 / -0.24 | 0.08 | -0.36 | 0.88 | -0.10 | 0.25 | 184 | NO |
| BTC 9 | BTC TNC release+5m dir=with hold=flat | 120 | 2 | 0.02 | -1.98 | -0.76 | -2.13 / 1.26 | -0.07 / -1.33 / 0.06 | -0.24 | 0.50 | 0.13 | -0.43 | 0.00 | 185 | NO |
| BTC 10 (diag) | BTC THU release+15m dir=with hold=240m | 67 | 2 | 1.42 | -1.72 | 0.61 | -0.25 / 1.43 | 0.23 / -0.32 / -0.15 | 0.07 | 0.10 | 0.84 | -0.14 | 0.25 | 111 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 9 |
| diagnostic cells read | 1 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 5 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 0 |
| worst-decile corr <= +0.30 | 5 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC BTC TNC release+5m dir=against hold=240m | clean | 0.11 | 0.15 | -145909 | -119598 | 543095 | -265269 | 0.19 | 40.0 | 1.49 | -89607 | 246120 | -130112 |
| BTC BTC TNC release+5m dir=against hold=240m | H1 | 3.63 | 11.28 | -74945 | -63000 | 111269 | -97308 | 9.09 | 14.3 | 3.65 | -74362 | 145613 | -83722 |
| BTC BTC TNC release+5m dir=against hold=240m | H2 | -1.38 | -1.69 | -121222 | -92929 | 480028 | -127172 | -0.66 | 52.8 | 2.24 | -92687 | 242860 | -102850 |
| BTC BTC TNC release+5m dir=against hold=240m | all | 0.55 | 0.83 | -135243 | -109034 | 543095 | -265269 | 1.46 | 38.7 | 1.99 | -89637 | 246120 | -130112 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| BTC BTC TNC release+5m dir=against hold=240m | -21.3 | -61.8 | 9.2 | 28.3 | -63.1 / 8.3 | 18.2 / 36.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| BTC 1 BTC ALL release+15m dir=with hold=240m | negative pre-2023 | 79 | -618.4 | -672.7 | -640.6 | 54.4 | -1.57 / -1.71 / -1.63 | 575.2 / 520.9 |
| BTC 2 BTC TNC release+15m dir=with hold=240m | negative pre-2023 | 79 | -618.4 | -672.7 | -640.6 | 54.4 | -1.57 / -1.71 / -1.63 | 494.3 / 440.0 |
| BTC 3 BTC ALL release+1m dir=with hold=flat | negative pre-2023 | 96 | -1103.9 | -1158.3 | -1125.7 | 54.4 | -2.37 / -2.49 / -2.42 | 540.2 / 485.9 |
| BTC 4 BTC ALL release+5m dir=with hold=flat | negative pre-2023 | 94 | -970.2 | -1024.6 | -991.9 | 54.4 | -2.04 / -2.15 / -2.08 | 534.3 / 480.0 |
| BTC 5 BTC TNC release+1m dir=against hold=240m | positive pre-2023 | 84 | 398.8 | 344.4 | 377.0 | 54.4 | 0.90 / 0.77 / 0.85 | 304.6 / 250.2 |
| BTC 6 BTC ALL release+15m dir=with hold=60m | negative pre-2023 | 91 | -94.2 | -148.6 | -116.3 | 54.4 | -0.50 / -0.78 / -0.61 | 225.6 / 171.3 |
| BTC 7 BTC TNC release+5m dir=against hold=15m | positive pre-2023 | 82 | 83.2 | 28.9 | 61.5 | 54.4 | 0.59 / 0.21 / 0.44 | 96.5 / 42.1 |
| BTC 8 BTC TNC release+5m dir=against hold=240m | positive pre-2023 | 82 | 466.2 | 411.8 | 444.4 | 54.4 | 1.14 / 1.00 / 1.08 | 148.9 / 94.6 |
| BTC 9 BTC TNC release+5m dir=with hold=flat | negative pre-2023 | 82 | -999.1 | -1053.4 | -1020.8 | 54.4 | -1.88 / -1.98 / -1.92 | 157.3 / 102.9 |
| BTC 10 (diag) BTC THU release+15m dir=with hold=240m | negative pre-2023 | 57 | -750.4 | -804.8 | -772.7 | 54.4 | -1.61 / -1.72 / -1.66 | 1397.0 / 1342.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 9 cells pass the clean rule against a replicate mean of 9.8 (p(count) = 0.65, p(top) = 1.00).
- Of 9 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.09 (BTC BTC TNC release+5m dir=against hold=240m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 6, 'positive pre-2023': 3}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_33.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw33/ (`SW33_CO_all_selected_scored.csv`).

DONE SW33
