# REPORT Q17A - Q17A: B7 grid on livestock (HE, LE)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 2 selected cells (+0 diagnostic) scored on 2 instruments; best non-diagnostic all-in additive uplift at 20% share -0.04; best pair-window standalone Sharpe +0.16.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: HE, LE. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| HE    |     288 |        272 |         2 |               0.693 |                2 |          2 |            0 |
| LE    |     288 |        272 |        18 |               1.047 |                2 |          0 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| HE    |     200 |                    2 |           10.365 |              19 |       1    |                       0.562 |            0.658 |           0.923 |     0.74 |       0.562 |                1.739 |
| LE    |     200 |                   18 |           13.905 |              29 |       0.14 |                       0.796 |            0.755 |           0.983 |     0.46 |       1.047 |                1.879 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HE 1 | 15m macd[12, 26] dir=against hold=180m all | 123 | 2 | 0.56 | -0.96 | 0.16 | -0.56 / 0.64 | 0.07 / -0.30 / -0.18 | -0.12 | 0.22 | 0.90 | -0.21 | 0.00 | 221 | NO |
| HE 2 | 15m macd[12, 26] dir=against hold=180m day | 123 | 2 | 0.56 | -0.95 | 0.16 | -0.56 / 0.65 | 0.07 / -0.30 / -0.18 | -0.12 | 0.22 | 0.89 | -0.21 | 0.00 | 221 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 2 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 0 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 0 |
| worst-decile corr <= +0.30 | 2 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HE 15m macd[12, 26] dir=against hold=180m all | clean | 0.53 | 0.89 | -111527 | -92881 | 459911 | -131298 | 1.04 | 41.0 | 1.53 | -87029 | 309414 | -96983 |
| HE 15m macd[12, 26] dir=against hold=180m all | H1 | -0.31 | -0.40 | -151250 | -132032 | 229642 | -170608 | -0.33 | 35.7 | 2.52 | -77639 | 149118 | -78287 |
| HE 15m macd[12, 26] dir=against hold=180m all | H2 | -0.87 | -1.14 | -85513 | -79771 | 434010 | -87556 | -0.42 | 44.4 | 2.12 | -89241 | 216029 | -95957 |
| HE 15m macd[12, 26] dir=against hold=180m all | all | 0.16 | 0.25 | -118362 | -99616 | 494444 | -170608 | 0.45 | 40.5 | 1.82 | -86549 | 309414 | -96983 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| HE 15m macd[12, 26] dir=against hold=180m all | -27.5 | -1.4 | 11.4 | 14.3 | -2.2 / 12.8 | -3.7 / 12.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| HE 1 15m macd[12, 26] dir=against hold=180m all | negative pre-2023 | 1001 | -7.7 | -32.1 | -31.6 | 24.4 | -0.23 / -0.96 / -0.94 | 52.8 / 28.5 |
| HE 2 15m macd[12, 26] dir=against hold=180m day | negative pre-2023 | 926 | -10.0 | -34.4 | -33.6 | 24.4 | -0.28 / -0.95 / -0.92 | 52.8 / 28.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): HE: 2 cells pass the clean rule against a replicate mean of 10.4 (p(count) = 1.00, p(top) = 0.74); LE: 18 cells pass the clean rule against a replicate mean of 13.9 (p(count) = 0.14, p(top) = 0.46).
- Of 2 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift -0.04 (HE 15m macd[12, 26] dir=against hold=180m day); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 2}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q17a.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q17a/ (`Q17A_CO_all_selected_scored.csv`).

DONE Q17A
