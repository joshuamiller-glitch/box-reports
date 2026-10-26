# REPORT Q8C - Q8C: B10 grid on ETH (ETH)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 10 selected cells (+0 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.14; best pair-window standalone Sharpe +1.00.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Windows (ET): Asia entries 19:00-01:30 flat 02:00; London entries 02:30-07:30 flat 08:25. Strategies: ST(14,2), EMA 9/21, Donchian 20, window opening-range breakout (first 30 min), VWAP-z 2.0 fade, RSI(14,30) fade. Exits: bracket stop=target or trail at 0.25/0.5 x SR (SR = the window's own 20-day mean range).
- Instruments: ETH. Grid: 144 cells per instrument = 2 windows x 3 bar sizes x 6 strategies x 4 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 5 per instrument per window (Asia, London separately) by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ETH   |     144 |        144 |        18 |               1.434 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ETH   |     100 |                   18 |             9.32 |              20 |       0.01 |                       1.041 |            0.706 |           0.958 |     0.01 |       1.434 |                1.853 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH 1 | asia 5m emax[9, 21] exit=trail0.25xSR | 860 | 2 | 1.20 | 0.70 | 0.26 | -0.74 / 0.69 | 0.15 / 0.03 / -0.42 | -0.24 | -0.03 | 0.96 | -0.23 | 0.00 | 1509 | NO |
| ETH 2 | asia 5m emax[9, 21] exit=trail0.5xSR | 595 | 2 | 0.88 | 1.17 | 0.10 | -0.57 / 0.27 | 0.10 / -0.45 / 0.04 | -0.14 | -0.16 | 0.94 | -0.26 | 0.00 | 982 | NO |
| ETH 3 | asia 15m emax[9, 21] exit=trail0.25xSR | 358 | 2 | 0.70 | -0.64 | 0.19 | -0.15 / 0.92 | 0.03 / 0.11 / -0.22 | -0.18 | -0.01 | 0.89 | -0.24 | 0.00 | 652 | NO |
| ETH 4 | asia 5m st[14, 2.0] exit=trail0.25xSR | 1347 | 2 | 0.67 | 0.24 | -0.07 | -1.38 / 0.43 | 0.09 / -0.18 / -0.26 | -0.26 | 0.24 | 0.93 | -0.21 | 0.00 | 2215 | NO |
| ETH 5 | asia 30m emax[9, 21] exit=trail0.5xSR | 155 | 2 | 0.58 | -1.11 | 0.72 | 0.83 / 0.53 | 0.07 / 0.14 / 0.02 | -0.01 | -0.47 | 0.98 | -0.14 | 0.50 | 293 | NO |
| ETH 6 | lon 15m emax[9, 21] exit=bracket0.5xSR | 230 | 2 | 1.43 | 0.05 | 0.39 | -0.87 / 0.63 | 0.24 / -0.17 / -0.49 | -0.06 | -0.16 | 0.99 | -0.20 | 1.00 | 419 | NO |
| ETH 7 | lon 15m emax[9, 21] exit=trail0.5xSR | 236 | 2 | 1.41 | -0.09 | 0.80 | -0.08 / 0.42 | 0.22 / 0.20 / -0.26 | 0.02 | -0.28 | 0.99 | -0.08 | 0.67 | 434 | NO |
| ETH 8 | lon 15m st[14, 2.0] exit=trail0.5xSR | 401 | 2 | 1.25 | -0.97 | 1.00 | 0.53 / 0.46 | 0.22 / 0.07 / -0.10 | 0.04 | -0.26 | 1.00 | -0.02 | 0.50 | 646 | NO |
| ETH 9 | lon 5m don[20] exit=trail0.5xSR | 773 | 2 | 1.20 | 0.02 | 0.36 | -1.40 / 0.35 | 0.23 / -0.27 / -0.25 | -0.08 | -0.19 | 0.93 | -0.12 | 0.25 | 1230 | NO |
| ETH 10 | lon 15m don[20] exit=trail0.5xSR | 475 | 2 | 1.10 | 0.25 | 0.04 | -2.01 / 0.53 | 0.18 / -0.71 / -0.30 | -0.16 | -0.17 | 0.92 | -0.23 | 0.00 | 727 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 5 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 5 |
| worst-decile corr <= +0.30 | 10 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH lon 15m st[14, 2.0] exit=trail0.5xSR | clean | 1.23 | 2.37 | -95059 | -80989 | 177019 | -173993 | 6.29 | 47.6 | 1.68 | -83533 | 248710 | -92028 |
| ETH lon 15m st[14, 2.0] exit=trail0.5xSR | H1 | 1.59 | 3.12 | -82902 | -73653 | 331957 | -103973 | 1.13 | 39.3 | 2.90 | -75954 | 167794 | -79493 |
| ETH lon 15m st[14, 2.0] exit=trail0.5xSR | H2 | -0.97 | -1.21 | -86677 | -64060 | 257214 | -110356 | -0.60 | 55.6 | 2.20 | -80266 | 216860 | -82782 |
| ETH lon 15m st[14, 2.0] exit=trail0.5xSR | all | 1.00 | 1.85 | -95195 | -78938 | 456631 | -173993 | 2.92 | 48.2 | 2.00 | -82426 | 248710 | -92028 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ETH lon 15m st[14, 2.0] exit=trail0.5xSR | -15.1 | 2.1 | 17.4 | 37.5 | 1.3 / 13.1 | 22.7 / 23.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ETH 1 asia 5m emax[9, 21] exit=trail0.25xSR | positive pre-2023 | 599 | 83.5 | 29.1 | 45.0 | 54.4 | 2.07 / 0.70 / 1.11 | 106.3 / 52.0 |
| ETH 2 asia 5m emax[9, 21] exit=trail0.5xSR | positive pre-2023 | 420 | 138.1 | 83.8 | 100.2 | 54.4 | 1.93 / 1.17 / 1.40 | 107.9 / 53.5 |
| ETH 3 asia 15m emax[9, 21] exit=trail0.25xSR | gross-positive, cost-negative pre-2023 | 242 | 12.6 | -41.7 | -25.3 | 54.4 | 0.19 / -0.64 / -0.39 | 90.3 / 35.9 |
| ETH 4 asia 5m st[14, 2.0] exit=trail0.25xSR | positive pre-2023 | 868 | 62.8 | 8.4 | 24.5 | 54.4 | 1.88 / 0.24 / 0.74 | 81.6 / 27.3 |
| ETH 5 asia 30m emax[9, 21] exit=trail0.5xSR | negative pre-2023 | 101 | -77.8 | -132.2 | -115.7 | 54.4 | -0.66 / -1.11 / -0.97 | 137.4 / 83.0 |
| ETH 6 lon 15m emax[9, 21] exit=bracket0.5xSR | positive pre-2023 | 189 | 52.3 | 4.7 | 18.9 | 47.6 | 0.60 / 0.05 / 0.21 | 218.0 / 171.0 |
| ETH 7 lon 15m emax[9, 21] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 194 | 47.3 | -7.1 | 8.8 | 54.4 | 0.58 / -0.09 / 0.11 | 236.0 / 181.6 |
| ETH 8 lon 15m st[14, 2.0] exit=trail0.5xSR | negative pre-2023 | 277 | -18.5 | -72.9 | -57.8 | 54.4 | -0.25 / -0.97 / -0.77 | 171.8 / 117.4 |
| ETH 9 lon 5m don[20] exit=trail0.5xSR | positive pre-2023 | 547 | 55.2 | 0.8 | 16.6 | 54.4 | 1.11 / 0.02 / 0.34 | 141.0 / 86.7 |
| ETH 10 lon 15m don[20] exit=trail0.5xSR | positive pre-2023 | 329 | 74.6 | 20.3 | 36.0 | 54.4 | 0.91 / 0.25 / 0.44 | 146.9 / 92.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ETH: 18 cells pass the clean rule against a replicate mean of 9.3 (p(count) = 0.01, p(top) = 0.01).
- Of 10 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.14 (ETH lon 15m st[14, 2.0] exit=trail0.5xSR); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 6, 'gross-positive, cost-negative pre-2023': 2, 'negative pre-2023': 2}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat. Overnight liquidity (Asia) is thin for ZN/RTY/CL; slippage of 1 tick may be optimistic there.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q8c.py (= ap_b10.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q8c/ (`Q8C_CO_all_selected_scored.csv`).

DONE Q8C
