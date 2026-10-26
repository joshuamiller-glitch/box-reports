# REPORT Q9B - Q9B: B7 grid on rates (ZB, ZF, ZT)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+9 diagnostic) scored on 3 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe -0.51.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: ZB, ZF, ZT. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ZB    |     288 |        288 |         0 |              -0.545 |                1 |          0 |            3 |
| ZF    |     288 |        288 |         0 |              -0.396 |                1 |          0 |            3 |
| ZT    |     288 |        288 |         0 |              -0.383 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ZB    |     100 |                    0 |             0.01 |               1 |          1 |                         nan |            0.086 |           0.086 |      nan |         nan |                0.086 |
| ZF    |     100 |                    0 |             0.01 |               1 |          1 |                         nan |            0.621 |           0.621 |      nan |         nan |                0.621 |
| ZT    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZB 1 (diag) | 10m st[14, 2.0] dir=with hold=240m day | 485 | 0 | -0.55 | -1.80 | -1.39 | -3.61 / -1.75 | -0.11 / -1.00 / -0.24 | -0.66 | -0.07 | 1.00 | -0.45 | 0.00 | 760 | diag |
| ZB 2 (diag) | 10m emax[9, 21] dir=with hold=240m day | 382 | 0 | -0.80 | -1.97 | -1.34 | -2.87 / -2.09 | -0.19 / -0.56 / -0.32 | -0.63 | 0.32 | 1.00 | -0.45 | 0.00 | 604 | diag |
| ZB 3 (diag) | 15m emax[9, 21] dir=with hold=240m day | 321 | 0 | -0.88 | -1.95 | -1.52 | -3.21 / -1.79 | -0.16 / -0.66 / -0.39 | -0.62 | -0.01 | 0.95 | -0.46 | 0.00 | 508 | diag |
| ZF 1 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=240m day | 283 | 1 | -0.40 | -1.18 | -0.51 | -0.78 / -1.01 | -0.11 / -0.09 / -0.04 | -0.33 | -0.54 | 0.99 | -0.29 | 0.00 | 451 | diag |
| ZF 2 (diag) | 15m emax[9, 21] dir=with hold=240m day | 333 | 0 | -0.42 | -2.01 | -0.96 | -2.56 / -1.48 | -0.08 / -0.51 / -0.29 | -0.43 | -0.06 | 1.00 | -0.35 | 0.00 | 517 | diag |
| ZF 3 (diag) | 10m emax[9, 21] dir=with hold=240m day | 371 | 1 | -0.54 | -2.34 | -1.66 | -4.47 / -1.67 | -0.15 / -0.90 / -0.58 | -0.64 | -0.12 | 0.92 | -0.52 | 0.00 | 598 | diag |
| ZT 1 (diag) | 10m vwz[2.0, 'globex'] dir=with hold=240m day | 347 | 0 | -0.38 | -2.20 | -1.02 | -2.87 / -1.54 | -0.06 / -0.32 / -0.34 | -0.41 | -0.05 | 1.00 | -0.34 | 0.00 | 546 | diag |
| ZT 2 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=240m day | 295 | 0 | -0.80 | -2.19 | -1.26 | -2.73 / -1.36 | -0.15 / -0.42 / -0.23 | -0.45 | -0.27 | 0.99 | -0.39 | 0.00 | 466 | diag |
| ZT 3 (diag) | 10m vwz[2.0, 'globex'] dir=with hold=180m day | 393 | 0 | -0.96 | -2.61 | -1.73 | -4.34 / -2.59 | -0.18 / -0.41 / -0.44 | -0.57 | 0.20 | 1.00 | -0.46 | 0.00 | 622 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 0 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 8 |
| worst-decile corr <= +0.30 | 8 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZB 10m st[14, 2.0] dir=with hold=240m day (diag) | clean | -0.60 | -0.83 | -123697 | -106157 | 972418 | -203318 | -0.56 | 52.4 | 1.35 | -85623 | 280366 | -98183 |
| ZB 10m st[14, 2.0] dir=with hold=240m day (diag) | H1 | -5.85 | -4.69 | -126833 | -117747 | 979855 | -133171 | -1.00 | 75.0 | 1.83 | -83603 | 162215 | -85822 |
| ZB 10m st[14, 2.0] dir=with hold=240m day (diag) | H2 | -1.85 | -2.27 | -67795 | -58646 | 467730 | -82241 | -0.69 | 63.9 | 2.05 | -89779 | 229797 | -93141 |
| ZB 10m st[14, 2.0] dir=with hold=240m day (diag) | all | -1.39 | -1.75 | -130792 | -108624 | 2136232 | -214875 | -0.86 | 58.3 | 1.59 | -87322 | 280366 | -98183 |
| ZF 15m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | clean | -0.39 | -0.56 | -121138 | -105488 | 922265 | -160882 | -0.38 | 51.4 | 1.35 | -90259 | 305007 | -94493 |
| ZF 15m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | H1 | -0.73 | -1.08 | -116621 | -99786 | 392240 | -127538 | -0.41 | 64.3 | 2.74 | -78977 | 168723 | -83087 |
| ZF 15m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | H2 | -0.84 | -1.13 | -79380 | -67728 | 294372 | -96153 | -0.57 | 52.8 | 2.25 | -82782 | 218756 | -82999 |
| ZF 15m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | all | -0.51 | -0.73 | -117358 | -100391 | 1157173 | -160882 | -0.59 | 54.2 | 1.75 | -87801 | 305007 | -94493 |
| ZT 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | clean | -0.40 | -0.58 | -130465 | -103928 | 682923 | -207762 | -0.53 | 58.1 | 1.40 | -86540 | 282397 | -93646 |
| ZT 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | H1 | -3.37 | -3.23 | -91350 | -78048 | 435332 | -121424 | -0.97 | 60.7 | 2.51 | -77315 | 162491 | -77324 |
| ZT 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | H2 | -2.55 | -3.04 | -78080 | -70513 | 556406 | -82996 | -0.92 | 72.2 | 1.96 | -83424 | 236595 | -84048 |
| ZT 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | all | -1.02 | -1.40 | -118933 | -94838 | 1636078 | -207762 | -0.79 | 61.9 | 1.70 | -85270 | 282397 | -93646 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ZB 10m st[14, 2.0] dir=with hold=240m day (diag) | -50.6 | -3.8 | 13.2 | 18.2 | -4.6 / 13.2 | 15.6 / 18.4 | NO |
| ZF 15m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | -37.6 | 3.6 | 9.9 | 2.6 | 2.8 / 3.7 | 20.8 / 27.4 | NO |
| ZT 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | -44.4 | 4.4 | 17.5 | 13.3 | 3.7 / 14.3 | 30.5 / 30.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ZB 1 (diag) 10m st[14, 2.0] dir=with hold=240m day | negative pre-2023 | 2466 | -0.6 | -67.5 | -86.3 | 66.9 | -0.01 / -1.80 / -2.29 | 48.6 / -18.2 |
| ZB 2 (diag) 10m emax[9, 21] dir=with hold=240m day | negative pre-2023 | 2021 | -9.4 | -76.2 | -94.9 | 66.9 | -0.24 / -1.97 / -2.45 | 40.2 / -26.6 |
| ZB 3 (diag) 15m emax[9, 21] dir=with hold=240m day | negative pre-2023 | 1653 | -16.0 | -82.9 | -101.5 | 66.9 | -0.38 / -1.95 / -2.39 | 36.2 / -30.6 |
| ZF 1 (diag) 15m vwz[2.0, 'globex'] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1259 | 5.5 | -14.5 | -16.6 | 20.0 | 0.45 / -1.18 / -1.35 | 14.4 / -5.6 |
| ZF 2 (diag) 15m emax[9, 21] dir=with hold=240m day | negative pre-2023 | 1639 | -4.4 | -24.4 | -26.5 | 20.0 | -0.37 / -2.01 / -2.19 | 15.1 / -4.9 |
| ZF 3 (diag) 10m emax[9, 21] dir=with hold=240m day | negative pre-2023 | 2051 | -4.6 | -24.6 | -26.7 | 20.0 | -0.44 / -2.34 / -2.54 | 14.0 / -5.9 |
| ZT 1 (diag) 10m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 1208 | -0.7 | -20.7 | -21.6 | 20.0 | -0.07 / -2.20 / -2.30 | 15.2 / -4.8 |
| ZT 2 (diag) 15m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 1038 | -1.3 | -21.3 | -22.3 | 20.0 | -0.14 / -2.19 / -2.29 | 10.4 / -9.6 |
| ZT 3 (diag) 10m vwz[2.0, 'globex'] dir=with hold=180m day | negative pre-2023 | 1425 | -1.6 | -21.6 | -22.6 | 20.0 | -0.20 / -2.61 / -2.73 | 10.0 / -10.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ZB: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZF: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZT: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q9b.py (= ap_b7.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q9b/ (`Q9B_CO_all_selected_scored.csv`).

DONE Q9B
