# REPORT Q8A - Q8A: B4 grid on ETH (ETH)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 4 selected cells (+3 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.08; best pair-window standalone Sharpe +0.55.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: fade a bar close that crosses from inside to outside session VWAP +- k sigma (sigma = volume-weighted std of typical price about the session VWAP; anchor = globex 18:00 ET or the instrument RTH open). Stop s x sigma from entry, target = VWAP level at the signal (or halfway), time stop 60/180 min, flat 16:55.
- Instruments: ETH. Grid: 192 cells per instrument = 4 bar sizes x 3 band widths x 2 anchors x 2 stops x 2 targets x 2 time stops.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ETH   |     192 |        176 |         4 |               0.525 |                2 |          4 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ETH   |     100 |                    4 |             1.72 |               6 |       0.08 |                       0.396 |            0.555 |           0.947 |     0.62 |       0.525 |                1.311 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH 1 | 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | 216 | 2 | 0.52 | -0.92 | -0.25 | -1.99 / -0.48 | 0.07 / -0.66 / -0.00 | -0.10 | 0.07 | 1.00 | -0.22 | 0.00 | 302 | NO |
| ETH 2 | 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | 439 | 2 | 0.50 | -1.43 | 0.55 | 0.29 / 0.32 | 0.12 / -0.09 / 0.06 | -0.02 | -0.03 | 1.00 | -0.11 | 0.67 | 665 | NO |
| ETH 3 | 5m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 200 | 2 | 0.35 | -0.78 | 0.34 | 0.06 / -0.79 | 0.09 / -0.22 / 0.05 | -0.00 | 0.16 | 1.00 | -0.11 | 0.67 | 280 | NO |
| ETH 4 | 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=60m | 442 | 2 | 0.21 | -2.19 | 0.13 | -0.48 / 0.26 | 0.08 / -0.04 / -0.09 | -0.12 | 0.23 | 0.99 | -0.15 | 0.50 | 670 | NO |
| ETH 5 (diag) | 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 96 | 1 | 0.45 | -0.35 | 0.28 | 0.04 / 0.01 | 0.08 / -0.03 / 0.08 | -0.00 | 0.23 | 0.98 | -0.14 | 0.67 | 138 | diag |
| ETH 6 (diag) | 15m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 93 | 1 | 0.42 | -1.10 | 0.23 | -0.16 / 0.05 | 0.06 / -0.09 / -0.02 | -0.02 | 0.26 | 0.99 | -0.15 | 0.50 | 134 | diag |
| ETH 7 (diag) | 30m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | 219 | 1 | 0.39 | -1.03 | -0.49 | -2.23 / -0.46 | 0.02 / -0.75 / -0.11 | -0.19 | -0.09 | 0.99 | -0.30 | 0.00 | 309 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 4 |
| diagnostic cells read | 3 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 5 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 7 |
| worst-decile corr <= +0.30 | 7 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | clean | 0.70 | 1.34 | -110313 | -87309 | 625592 | -146784 | 1.07 | 55.2 | 1.58 | -83053 | 336517 | -88195 |
| ETH 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | H1 | 0.27 | 0.47 | -145481 | -126839 | 347737 | -173798 | 0.28 | 53.6 | 2.74 | -77432 | 172678 | -86301 |
| ETH 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | H2 | 0.36 | 0.70 | -64323 | -47405 | 209157 | -65194 | 0.33 | 55.6 | 2.36 | -82872 | 190865 | -86090 |
| ETH 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | all | 0.55 | 1.00 | -115822 | -91928 | 625592 | -173798 | 1.33 | 55.4 | 1.94 | -83503 | 336517 | -88195 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ETH 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | -20.7 | 14.4 | 18.4 | -0.2 | 13.7 / 19.3 | 9.8 / 11.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ETH 1 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 174 | -48.6 | -97.2 | -84.7 | 48.6 | -0.46 / -0.92 / -0.80 | 131.0 / 84.2 |
| ETH 2 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 234 | -42.4 | -92.8 | -76.4 | 50.4 | -0.67 / -1.43 / -1.19 | 107.4 / 58.3 |
| ETH 3 5m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 166 | -41.7 | -89.9 | -76.9 | 48.2 | -0.37 / -0.78 / -0.67 | 117.9 / 72.5 |
| ETH 4 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=60m | negative pre-2023 | 234 | -65.4 | -117.4 | -100.5 | 52.0 | -1.25 / -2.19 / -1.88 | 79.6 / 28.1 |
| ETH 5 (diag) 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | gross-positive, cost-negative pre-2023 | 83 | 7.4 | -42.4 | -30.4 | 49.8 | 0.06 / -0.35 / -0.25 | 106.3 / 58.7 |
| ETH 6 (diag) 15m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 80 | -129.6 | -179.0 | -166.3 | 49.4 | -0.81 / -1.10 / -1.03 | 135.8 / 90.3 |
| ETH 7 (diag) 30m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 178 | -31.4 | -81.2 | -68.2 | 49.9 | -0.41 / -1.03 / -0.87 | 88.7 / 40.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ETH: 4 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.08, p(top) = 0.62).
- Of 4 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.08 (ETH 10m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 4}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q8a.py (= ap_b4.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q8a/ (`Q8A_CO_all_selected_scored.csv`).

DONE Q8A
