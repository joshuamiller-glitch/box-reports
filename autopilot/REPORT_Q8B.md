# REPORT Q8B - Q8B: B7 grid on ETH (ETH)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 10 selected cells (+0 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.14; best pair-window standalone Sharpe +0.79.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: ETH. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ETH   |     288 |        288 |        28 |               1.456 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ETH   |     100 |                   28 |            16.23 |              25 |          0 |                       1.217 |            0.825 |           1.088 |     0.01 |       1.456 |                 1.84 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH 1 | 15m emax[9, 21] dir=with hold=240m all | 859 | 2 | 1.46 | -1.71 | 0.79 | -0.15 / 0.80 | 0.26 / 0.13 / -0.14 | 0.05 | -0.08 | 0.99 | -0.06 | 0.33 | 1444 | NO |
| ETH 2 | 5m st[14, 2.0] dir=against hold=240m day | 602 | 2 | 1.43 | -1.20 | 0.42 | -0.93 / 1.17 | 0.27 / -0.66 / -0.02 | 0.02 | 0.30 | 0.91 | -0.13 | 0.33 | 927 | NO |
| ETH 3 | 5m st[14, 2.0] dir=against hold=180m day | 890 | 2 | 1.37 | -1.26 | 0.45 | -0.70 / 0.95 | 0.21 / -0.78 / 0.05 | -0.06 | 0.54 | 0.96 | -0.17 | 0.33 | 1375 | NO |
| ETH 4 | 10m rsi[14, 30] dir=against hold=240m all | 853 | 2 | 1.36 | -0.47 | 0.51 | -0.48 / 0.88 | 0.22 / -0.63 / 0.06 | -0.03 | -0.36 | 0.98 | -0.15 | 0.50 | 1352 | NO |
| ETH 5 | 15m emax[9, 21] dir=with hold=180m all | 970 | 2 | 1.31 | -2.30 | 0.51 | -0.65 / 0.82 | 0.23 / -0.51 / -0.08 | -0.07 | -0.03 | 0.98 | -0.14 | 0.33 | 1640 | NO |
| ETH 6 | 15m vwz[2.0, 'globex'] dir=with hold=120m day | 263 | 2 | 1.18 | -0.79 | -0.42 | -2.30 / 1.28 | 0.21 / -1.21 / -0.42 | -0.20 | -0.24 | 0.60 | -0.37 | 0.00 | 419 | NO |
| ETH 7 | 5m st[14, 2.0] dir=against hold=180m all | 2492 | 2 | 1.15 | -1.38 | 0.30 | -0.79 / 0.32 | 0.21 / -0.25 / -0.27 | -0.15 | 0.08 | 0.99 | -0.15 | 0.00 | 3947 | NO |
| ETH 8 | 10m st[14, 2.0] dir=against hold=240m day | 467 | 2 | 0.99 | -1.60 | 0.14 | -1.10 / 1.02 | 0.16 / 0.07 / -0.22 | -0.03 | 0.02 | 0.84 | -0.18 | 0.50 | 739 | NO |
| ETH 9 | 10m macd[12, 26] dir=with hold=240m all | 981 | 2 | 0.99 | -0.19 | 0.60 | -0.15 / 1.11 | 0.17 / -0.00 / -0.11 | -0.03 | 0.18 | 0.96 | -0.11 | 0.67 | 1621 | NO |
| ETH 10 | 5m rsi[14, 30] dir=against hold=240m all | 1214 | 2 | 0.94 | -0.62 | 0.50 | -0.12 / 1.05 | 0.14 / -0.26 / -0.05 | -0.08 | -0.09 | 0.98 | -0.15 | 0.67 | 1941 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 9 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 7 |
| worst-decile corr <= +0.30 | 9 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH 15m emax[9, 21] dir=with hold=240m all | clean | 1.52 | 2.59 | -114274 | -95491 | 315990 | -197058 | 4.37 | 48.6 | 1.72 | -82507 | 241033 | -94306 |
| ETH 15m emax[9, 21] dir=with hold=240m all | H1 | 0.09 | 0.13 | -210892 | -190955 | 601915 | -269721 | 0.07 | 46.4 | 2.96 | -78057 | 155584 | -78704 |
| ETH 15m emax[9, 21] dir=with hold=240m all | H2 | -0.72 | -0.94 | -80758 | -66855 | 453747 | -99760 | -0.31 | 52.8 | 2.15 | -87323 | 241562 | -88737 |
| ETH 15m emax[9, 21] dir=with hold=240m all | all | 0.79 | 1.23 | -146604 | -116570 | 601915 | -269721 | 2.13 | 48.8 | 2.00 | -83277 | 241562 | -94306 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ETH 15m emax[9, 21] dir=with hold=240m all | -15.7 | 3.3 | 19.4 | 29.7 | 2.5 / 19.1 | 27.8 / 29.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ETH 1 15m emax[9, 21] dir=with hold=240m all | negative pre-2023 | 636 | -110.1 | -164.5 | -148.0 | 54.4 | -1.15 / -1.71 / -1.54 | 224.9 / 170.6 |
| ETH 2 5m st[14, 2.0] dir=against hold=240m day | negative pre-2023 | 440 | -100.2 | -154.5 | -138.9 | 54.4 | -0.78 / -1.20 / -1.07 | 285.9 / 231.5 |
| ETH 3 5m st[14, 2.0] dir=against hold=180m day | negative pre-2023 | 657 | -86.6 | -141.0 | -125.3 | 54.4 | -0.78 / -1.26 / -1.12 | 190.8 / 136.5 |
| ETH 4 10m rsi[14, 30] dir=against hold=240m all | gross-positive, cost-negative pre-2023 | 596 | 12.5 | -41.9 | -26.7 | 54.4 | 0.15 / -0.47 / -0.29 | 194.0 / 139.6 |
| ETH 5 15m emax[9, 21] dir=with hold=180m all | negative pre-2023 | 725 | -104.8 | -159.1 | -143.0 | 54.4 | -1.53 / -2.30 / -2.06 | 172.5 / 118.2 |
| ETH 6 15m vwz[2.0, 'globex'] dir=with hold=120m day | negative pre-2023 | 174 | -72.3 | -126.6 | -111.8 | 54.4 | -0.45 / -0.79 / -0.70 | 227.9 / 173.6 |
| ETH 7 5m st[14, 2.0] dir=against hold=180m all | negative pre-2023 | 1805 | -4.5 | -58.9 | -43.0 | 54.4 | -0.12 / -1.38 / -1.02 | 104.2 / 49.8 |
| ETH 8 10m st[14, 2.0] dir=against hold=240m day | negative pre-2023 | 359 | -175.1 | -229.5 | -213.9 | 54.4 | -1.22 / -1.60 / -1.49 | 257.7 / 203.3 |
| ETH 9 10m macd[12, 26] dir=with hold=240m all | gross-positive, cost-negative pre-2023 | 709 | 38.6 | -15.7 | 0.3 | 54.4 | 0.46 / -0.19 / 0.01 | 162.7 / 108.3 |
| ETH 10 5m rsi[14, 30] dir=against hold=240m all | gross-positive, cost-negative pre-2023 | 812 | 13.3 | -41.0 | -25.3 | 54.4 | 0.20 / -0.62 / -0.38 | 133.2 / 78.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ETH: 28 cells pass the clean rule against a replicate mean of 16.2 (p(count) = 0.00, p(top) = 0.01).
- Of 10 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.14 (ETH 15m emax[9, 21] dir=with hold=240m all); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 7, 'gross-positive, cost-negative pre-2023': 3}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q8b.py (= ap_b7.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q8b/ (`Q8B_CO_all_selected_scored.csv`).

DONE Q8B
