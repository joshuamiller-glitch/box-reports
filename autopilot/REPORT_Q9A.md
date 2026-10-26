# REPORT Q9A - Q9A: B1 grid on rates (ZB, ZF, ZT)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+9 diagnostic) scored on 3 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe -1.20.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Instruments: ZB, ZF, ZT. Grid: 180 cells per instrument = 4 bar sizes x 9 signal parameter sets x 5 trail exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ZB    |     180 |        180 |         0 |              -1.586 |                0 |          0 |            3 |
| ZF    |     180 |        180 |         0 |              -0.533 |                1 |          0 |            3 |
| ZT    |     180 |        180 |         0 |              -1.33  |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ZB    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |
| ZF    |     100 |                    0 |             0.01 |               1 |          1 |                         nan |            0.451 |           0.451 |      nan |         nan |                0.451 |
| ZT    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZB 1 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 350 | 0 | -1.59 | -1.11 | -2.16 | -2.93 / -1.06 | -0.09 / -0.35 / -0.08 | -0.24 | -0.07 | 0.64 | -0.18 | 0.00 | 576 | diag |
| ZB 2 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 289 | 0 | -1.79 | -1.41 | -2.14 | -2.65 / -1.28 | -0.08 / -0.17 / -0.08 | -0.18 | -0.04 | 0.58 | -0.13 | 0.00 | 473 | diag |
| ZB 3 (diag) | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 306 | 0 | -1.99 | -2.64 | -2.78 | -4.02 / -1.72 | -0.10 / -0.29 / -0.16 | -0.28 | -0.06 | 0.67 | -0.18 | 0.00 | 497 | diag |
| ZF 1 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 320 | 0 | -0.53 | -1.59 | -1.20 | -2.01 / -0.30 | -0.03 / -0.29 / -0.04 | -0.15 | 0.40 | 0.87 | -0.11 | 0.00 | 503 | diag |
| ZF 2 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | 322 | 0 | -0.58 | -2.93 | -1.34 | -2.36 / -1.62 | -0.03 / -0.34 / -0.09 | -0.21 | 0.35 | 0.98 | -0.15 | 0.00 | 505 | diag |
| ZF 3 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | 367 | 1 | -0.85 | -3.21 | -1.53 | -2.33 / -1.88 | -0.05 / -0.42 / -0.08 | -0.25 | 0.48 | 0.99 | -0.17 | 0.00 | 586 | diag |
| ZT 1 (diag) | 30m ST[14, 2.0, 200] exit=ATRtrail3.0 | 488 | 0 | -1.33 | -4.35 | -1.93 | -2.78 / -1.57 | -0.09 / -0.42 / -0.18 | -0.32 | 0.12 | 0.96 | -0.22 | 0.00 | 777 | diag |
| ZT 2 (diag) | 30m WT[14, 2.0, 100] exit=ATRtrail3.0 | 503 | 0 | -1.47 | -4.29 | -2.25 | -3.57 / -1.77 | -0.10 / -0.38 / -0.18 | -0.33 | 0.17 | 0.92 | -0.22 | 0.00 | 812 | diag |
| ZT 3 (diag) | 30m WT[20, 2.0, 100] exit=ATRtrail3.0 | 484 | 0 | -1.48 | -4.45 | -2.17 | -3.16 / -1.64 | -0.09 / -0.39 / -0.12 | -0.31 | 0.14 | 0.91 | -0.20 | 0.00 | 795 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 0 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 3 |
| worst-decile corr <= +0.30 | 6 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZB 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | clean | -1.83 | -2.28 | -25028 | -22744 | 380509 | -32890 | -0.87 | 63.8 | 1.38 | -80361 | 290621 | -82386 |
| ZB 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H1 | -3.25 | -3.36 | -28257 | -25652 | 185436 | -29380 | -0.83 | 71.4 | 2.66 | -78658 | 157525 | -81641 |
| ZB 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H2 | -2.13 | -2.56 | -23007 | -20148 | 121890 | -26793 | -0.97 | 58.3 | 2.21 | -82928 | 224739 | -83301 |
| ZB 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | all | -2.14 | -2.54 | -25942 | -23095 | 618943 | -32890 | -0.97 | 64.3 | 1.76 | -81287 | 290621 | -83301 |
| ZF 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | clean | -0.62 | -0.89 | -25367 | -21913 | 150987 | -32600 | -0.84 | 56.2 | 1.43 | -80222 | 279094 | -83918 |
| ZF 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H1 | -5.06 | -4.35 | -41836 | -38626 | 322027 | -46529 | -0.97 | 78.6 | 2.54 | -79799 | 158912 | -82128 |
| ZF 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H2 | 0.45 | 0.80 | -22017 | -18553 | 55622 | -22603 | 0.55 | 58.3 | 2.25 | -83086 | 219846 | -84467 |
| ZF 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | all | -1.20 | -1.56 | -31722 | -26493 | 495461 | -46529 | -0.82 | 60.7 | 1.79 | -81569 | 279094 | -84467 |
| ZT 30m WT[20, 2.0, 100] exit=ATRtrail3.0 (diag) | clean | -1.50 | -2.04 | -31465 | -29149 | 409536 | -36408 | -0.98 | 64.8 | 1.37 | -79561 | 287170 | -81417 |
| ZT 30m WT[20, 2.0, 100] exit=ATRtrail3.0 (diag) | H1 | -6.15 | -5.01 | -45553 | -42519 | 433218 | -53618 | -0.97 | 85.7 | 2.44 | -82927 | 161003 | -85785 |
| ZT 30m WT[20, 2.0, 100] exit=ATRtrail3.0 (diag) | H2 | -1.47 | -1.81 | -42821 | -39137 | 230582 | -47439 | -0.70 | 61.1 | 2.17 | -85651 | 229550 | -86641 |
| ZT 30m WT[20, 2.0, 100] exit=ATRtrail3.0 (diag) | all | -2.17 | -2.62 | -39196 | -35161 | 1050884 | -53618 | -0.93 | 67.3 | 1.72 | -82007 | 287170 | -86641 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ZB 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | -36.7 | 25.6 | 25.9 | 24.4 | 25.0 / 26.7 | 23.6 / 28.0 | NO |
| ZF 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | -34.6 | 26.5 | 25.4 | 30.5 | 26.3 / 26.9 | 22.6 / 25.8 | NO |
| ZT 30m WT[20, 2.0, 100] exit=ATRtrail3.0 (diag) | -41.0 | 20.0 | 24.1 | 26.2 | 26.1 / 27.9 | 15.6 / 19.7 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ZB 1 (diag) 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1925 | 568.8 | -735.1 | -1092.6 | 1303.9 | 0.89 / -1.11 / -1.63 | 301.5 / -1056.2 |
| ZB 2 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1492 | 268.5 | -1001.3 | -1350.6 | 1269.8 | 0.39 / -1.41 / -1.88 | 223.3 / -1140.2 |
| ZB 3 (diag) 30m HM[20, 55, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1572 | 39.1 | -1871.4 | -2397.7 | 1910.5 | 0.06 / -2.64 / -3.30 | 691.3 / -1355.7 |
| ZF 1 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1695 | 562.7 | -1095.1 | -1280.7 | 1657.8 | 0.87 / -1.59 / -1.84 | 936.0 / -397.3 |
| ZF 2 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1701 | 233.3 | -2254.5 | -2533.1 | 2487.8 | 0.33 / -2.93 / -3.24 | 1455.8 / -541.6 |
| ZF 3 (diag) 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1938 | 221.3 | -2254.8 | -2529.9 | 2476.1 | 0.34 / -3.21 / -3.55 | 1274.5 / -699.2 |
| ZT 1 (diag) 30m ST[14, 2.0, 200] exit=ATRtrail3.0 | negative pre-2023 | 2271 | -41.1 | -2684.4 | -2834.3 | 2643.2 | -0.07 / -4.35 / -4.54 | 985.5 / -766.3 |
| ZT 2 (diag) 30m WT[14, 2.0, 100] exit=ATRtrail3.0 | negative pre-2023 | 2427 | -81.6 | -2753.9 | -2907.0 | 2672.3 | -0.14 / -4.29 / -4.47 | 919.4 / -822.7 |
| ZT 3 (diag) 30m WT[20, 2.0, 100] exit=ATRtrail3.0 | negative pre-2023 | 2423 | -74.1 | -2723.9 | -2875.7 | 2649.8 | -0.14 / -4.45 / -4.64 | 898.7 / -830.1 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ZB: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZF: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZT: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q9a.py (= ap_b1.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q9a/ (`Q9A_CO_all_selected_scored.csv`).

DONE Q9A
