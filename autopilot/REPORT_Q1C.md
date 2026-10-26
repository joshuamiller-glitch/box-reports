# REPORT Q1C - Q1C: B10 grid on NQ index (NQ)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 10 selected cells (+0 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.12; best pair-window standalone Sharpe +0.81.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Windows (ET): Asia entries 19:00-01:30 flat 02:00; London entries 02:30-07:30 flat 08:25. Strategies: ST(14,2), EMA 9/21, Donchian 20, window opening-range breakout (first 30 min), VWAP-z 2.0 fade, RSI(14,30) fade. Exits: bracket stop=target or trail at 0.25/0.5 x SR (SR = the window's own 20-day mean range).
- Instruments: NQ. Grid: 144 cells per instrument = 2 windows x 3 bar sizes x 6 strategies x 4 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 5 per instrument per window (Asia, London separately) by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| NQ    |     144 |        136 |        23 |                 2.1 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| NQ    |     100 |                   23 |            13.83 |              22 |          0 |                       1.289 |            0.812 |           1.093 |        0 |         2.1 |                1.914 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ 1 | asia 15m st[14, 2.0] exit=bracket0.25xSR | 224 | 2 | 1.43 | -1.08 | 0.10 | -0.61 / 1.01 | 0.34 / -0.13 / -0.79 | -0.04 | -0.50 | 0.87 | -0.38 | 0.67 | 494 | NO |
| NQ 2 | asia 15m st[14, 2.0] exit=bracket0.5xSR | 215 | 2 | 1.25 | -0.98 | 0.22 | -0.36 / 1.52 | 0.28 / -0.08 / -0.53 | 0.01 | -0.50 | 0.87 | -0.31 | 0.50 | 449 | NO |
| NQ 3 | asia 15m st[14, 2.0] exit=trail0.25xSR | 225 | 2 | 1.12 | -1.75 | 0.37 | -0.01 / 1.96 | 0.27 / 0.17 / -0.47 | 0.04 | -0.70 | 0.73 | -0.27 | 0.50 | 500 | NO |
| NQ 4 | asia 15m emax[9, 21] exit=bracket0.25xSR | 358 | 2 | 1.11 | -1.07 | 0.52 | 0.06 / 0.94 | 0.19 / -0.48 / 0.08 | 0.02 | 0.36 | 0.95 | -0.22 | 0.50 | 633 | NO |
| NQ 5 | asia 30m emax[9, 21] exit=bracket0.25xSR | 150 | 2 | 1.01 | -1.19 | 0.57 | 0.37 / 1.06 | 0.16 / 0.07 / 0.04 | 0.07 | -0.20 | 0.95 | -0.21 | 0.50 | 285 | NO |
| NQ 6 | lon 30m rsi[14, 30] exit=bracket0.5xSR | 111 | 2 | 2.10 | -0.07 | 0.81 | -0.50 / 1.21 | 0.36 / -0.69 / -0.06 | 0.10 | -0.30 | 0.96 | -0.12 | 0.67 | 188 | NO |
| NQ 7 | lon 30m rsi[14, 30] exit=bracket0.25xSR | 119 | 2 | 1.78 | 0.02 | 0.35 | -1.06 / 0.96 | 0.28 / -0.35 / -0.33 | 0.04 | -0.52 | 0.94 | -0.17 | 0.67 | 201 | NO |
| NQ 8 | lon 15m rsi[14, 30] exit=trail0.5xSR | 268 | 2 | 1.21 | -0.61 | 0.13 | -1.14 / 1.10 | 0.22 / -0.59 / -0.25 | -0.02 | -0.43 | 0.74 | -0.22 | 0.67 | 444 | NO |
| NQ 9 | lon 5m rsi[14, 30] exit=trail0.5xSR | 561 | 2 | 1.02 | -0.52 | -0.11 | -1.88 / 1.22 | 0.21 / -0.27 / -0.49 | -0.05 | -0.03 | 0.66 | -0.21 | 0.00 | 900 | NO |
| NQ 10 | lon 15m vwz[2.0] exit=trail0.5xSR | 384 | 2 | 0.87 | -0.78 | -0.13 | -1.62 / 1.19 | 0.15 / -0.21 / -0.50 | -0.08 | -0.46 | 0.64 | -0.25 | 0.00 | 585 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 8 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 3 |
| worst-decile corr <= +0.30 | 9 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ lon 30m rsi[14, 30] exit=bracket0.5xSR | clean | 2.14 | 4.63 | -92178 | -78476 | 363859 | -149613 | 5.33 | 23.8 | 1.82 | -81290 | 279526 | -85522 |
| NQ lon 30m rsi[14, 30] exit=bracket0.5xSR | H1 | -2.10 | -2.33 | -202734 | -165956 | 888392 | -268717 | -0.70 | 50.0 | 2.14 | -78923 | 206757 | -79558 |
| NQ lon 30m rsi[14, 30] exit=bracket0.5xSR | H2 | 0.32 | 0.49 | -224405 | -188888 | 437822 | -283878 | 0.42 | 38.9 | 2.23 | -108192 | 244869 | -111526 |
| NQ lon 30m rsi[14, 30] exit=bracket0.5xSR | all | 0.81 | 1.30 | -174664 | -131077 | 888392 | -283878 | 1.69 | 31.5 | 1.97 | -90055 | 279526 | -111526 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| NQ lon 30m rsi[14, 30] exit=bracket0.5xSR | -13.2 | -49.6 | -0.5 | 15.8 | 14.6 / 23.4 | -26.1 / 1.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| NQ 1 asia 15m st[14, 2.0] exit=bracket0.25xSR | negative pre-2023 | 1353 | -14.5 | -27.0 | -19.7 | 12.5 | -0.58 / -1.08 / -0.79 | 78.7 / 66.7 |
| NQ 2 asia 15m st[14, 2.0] exit=bracket0.5xSR | negative pre-2023 | 1266 | -24.4 | -37.8 | -30.0 | 13.4 | -0.64 / -0.98 / -0.78 | 87.4 / 74.1 |
| NQ 3 asia 15m st[14, 2.0] exit=trail0.25xSR | negative pre-2023 | 1363 | -24.1 | -38.5 | -30.2 | 14.4 | -1.10 / -1.75 / -1.37 | 69.1 / 54.8 |
| NQ 4 asia 15m emax[9, 21] exit=bracket0.25xSR | negative pre-2023 | 1902 | -7.4 | -19.9 | -12.5 | 12.6 | -0.40 / -1.07 / -0.67 | 46.2 / 34.0 |
| NQ 5 asia 30m emax[9, 21] exit=bracket0.25xSR | negative pre-2023 | 804 | -20.5 | -33.1 | -25.8 | 12.6 | -0.75 / -1.19 / -0.94 | 59.9 / 47.7 |
| NQ 6 lon 30m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 682 | 8.0 | -5.0 | 2.9 | 13.0 | 0.11 / -0.07 / 0.04 | 229.4 / 216.7 |
| NQ 7 lon 30m rsi[14, 30] exit=bracket0.25xSR | positive pre-2023 | 744 | 12.7 | 0.7 | 7.9 | 11.9 | 0.32 / 0.02 / 0.20 | 118.1 / 106.3 |
| NQ 8 lon 15m rsi[14, 30] exit=trail0.5xSR | negative pre-2023 | 1452 | -11.0 | -25.3 | -16.8 | 14.4 | -0.26 / -0.61 / -0.40 | 111.0 / 96.7 |
| NQ 9 lon 5m rsi[14, 30] exit=trail0.5xSR | negative pre-2023 | 2904 | -2.0 | -16.4 | -7.9 | 14.4 | -0.06 / -0.52 / -0.25 | 77.8 / 63.5 |
| NQ 10 lon 15m vwz[2.0] exit=trail0.5xSR | negative pre-2023 | 1768 | -16.8 | -31.1 | -22.7 | 14.4 | -0.42 / -0.78 / -0.57 | 75.7 / 61.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- NQ overnight (Asia/London) books: 23 cells pass the clean rule against a replicate mean of 13.8 (p(count) = 0.00; top-mean p = 0.00) but nothing carries: no cell has +0.10 on all three spans (best H1 +0.17, best H2 +0.08), best all-in uplift +0.12. NO.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat. Overnight liquidity (Asia) is thin for ZN/RTY/CL; slippage of 1 tick may be optimistic there.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q1c.py (= ap_b10.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q1c/ (`Q1C_CO_all_selected_scored.csv`).

DONE Q1C
