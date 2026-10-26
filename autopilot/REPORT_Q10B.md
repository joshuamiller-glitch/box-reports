# REPORT Q10B - Q10B: B1 grid on grains (ZC, ZS, ZW)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+9 diagnostic) scored on 3 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe -0.79.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Instruments: ZC, ZS, ZW. Grid: 180 cells per instrument = 4 bar sizes x 9 signal parameter sets x 5 trail exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ZC    |     180 |        180 |         0 |              -1.423 |                0 |          0 |            3 |
| ZS    |     180 |        180 |         0 |              -0.784 |                1 |          0 |            3 |
| ZW    |     180 |        180 |         0 |              -0.326 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ZC    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |
| ZS    |     100 |                    0 |             0.18 |               2 |          1 |                         nan |            0.435 |           0.814 |      nan |         nan |                0.814 |
| ZW    |     100 |                    0 |             0.02 |               1 |          1 |                         nan |            0.784 |           0.969 |      nan |         nan |                0.969 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZC 1 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 279 | 0 | -1.42 | -2.04 | -1.24 | -0.83 / -1.24 | -0.07 / -0.06 / -0.01 | -0.14 | -0.34 | 1.00 | -0.10 | 0.00 | 440 | diag |
| ZC 2 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 258 | 0 | -1.85 | -2.12 | -1.64 | -1.22 / -0.51 | -0.06 / -0.07 / -0.04 | -0.13 | 0.16 | 0.91 | -0.09 | 0.00 | 408 | diag |
| ZC 3 (diag) | 30m WT[20, 2.0, 100] exit=ATRtrail3.0 | 428 | 0 | -2.24 | -3.02 | -2.71 | -3.55 / -1.43 | -0.12 / -0.33 / -0.11 | -0.28 | -0.25 | 0.70 | -0.20 | 0.00 | 686 | diag |
| ZS 1 (diag) | 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | 649 | 0 | -0.78 | -2.11 | -1.50 | -2.65 / 0.09 | -0.05 / -0.24 / -0.14 | -0.19 | -0.13 | 0.37 | -0.15 | 0.00 | 1058 | diag |
| ZS 2 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 309 | 1 | -0.81 | -1.15 | -0.79 | -0.72 / 0.40 | -0.04 / -0.11 / 0.01 | -0.08 | -0.10 | 0.62 | -0.08 | 0.00 | 484 | diag |
| ZS 3 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 253 | 1 | -0.81 | -0.37 | -1.18 | -1.59 / 0.38 | -0.04 / -0.05 / -0.09 | -0.09 | 0.37 | 0.41 | -0.09 | 0.00 | 418 | diag |
| ZW 1 (diag) | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 435 | 1 | -0.33 | -1.23 | -1.03 | -2.46 / -0.80 | -0.03 / -0.19 / -0.05 | -0.14 | -0.15 | 0.86 | -0.12 | 0.00 | 700 | diag |
| ZW 2 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 255 | 1 | -0.41 | -1.32 | -1.09 | -2.01 / -0.24 | -0.02 / -0.17 / -0.00 | -0.08 | 0.02 | 0.72 | -0.08 | 0.00 | 406 | diag |
| ZW 3 (diag) | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 266 | 0 | -0.88 | -1.92 | -1.37 | -1.93 / -0.57 | -0.05 / -0.23 / 0.02 | -0.12 | -0.03 | 0.91 | -0.11 | 0.00 | 427 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 0 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 1 |
| worst-decile corr <= +0.30 | 8 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZC 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | clean | -1.44 | -1.80 | -30358 | -25957 | 319462 | -51202 | -0.91 | 57.1 | 1.39 | -83175 | 285158 | -87393 |
| ZC 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H1 | -2.50 | -2.59 | -27851 | -25443 | 102996 | -28771 | -0.96 | 50.0 | 2.77 | -77457 | 153201 | -78543 |
| ZC 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H2 | 0.28 | 0.45 | -19337 | -17377 | 71627 | -20926 | 0.23 | 47.2 | 2.29 | -81038 | 219350 | -82734 |
| ZC 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | all | -1.24 | -1.56 | -28895 | -24596 | 450881 | -51202 | -0.83 | 54.2 | 1.80 | -82645 | 285158 | -87393 |
| ZS 30m WT[20, 3.0, 100] exit=ATRtrail3.0 (diag) | clean | -0.82 | -1.10 | -31919 | -26333 | 213518 | -40227 | -0.77 | 59.0 | 1.42 | -81920 | 292488 | -84564 |
| ZS 30m WT[20, 3.0, 100] exit=ATRtrail3.0 (diag) | H1 | -2.11 | -2.45 | -28630 | -27151 | 136026 | -31286 | -0.91 | 64.3 | 2.72 | -78094 | 155659 | -79089 |
| ZS 30m WT[20, 3.0, 100] exit=ATRtrail3.0 (diag) | H2 | 0.74 | 1.28 | -17862 | -15209 | 58629 | -20157 | 0.68 | 44.4 | 2.31 | -82475 | 219429 | -85104 |
| ZS 30m WT[20, 3.0, 100] exit=ATRtrail3.0 (diag) | all | -0.79 | -1.06 | -30330 | -25633 | 368392 | -40227 | -0.67 | 57.1 | 1.81 | -81729 | 292488 | -85104 |
| ZW 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | clean | -0.57 | -0.79 | -25885 | -22531 | 141414 | -35707 | -0.77 | 50.5 | 1.44 | -78997 | 274403 | -82397 |
| ZW 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H1 | -4.12 | -3.88 | -31523 | -26963 | 186974 | -34570 | -1.00 | 71.4 | 2.66 | -79009 | 156715 | -80804 |
| ZW 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H2 | -0.50 | -0.64 | -32436 | -25066 | 100101 | -41208 | -0.30 | 55.6 | 2.29 | -80462 | 217959 | -82975 |
| ZW 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | all | -1.09 | -1.39 | -29288 | -24454 | 382743 | -41208 | -0.85 | 55.4 | 1.81 | -79523 | 274403 | -82975 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ZC 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | -34.2 | 15.9 | 23.0 | 27.3 | 15.3 / 20.6 | 28.1 / 30.3 | NO |
| ZS 30m WT[20, 3.0, 100] exit=ATRtrail3.0 (diag) | -32.8 | 21.2 | 25.0 | 23.4 | 20.6 / 23.6 | 28.5 / 29.1 | NO |
| ZW 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | -33.6 | 29.0 | 28.9 | 33.1 | 29.0 / 29.0 | 25.2 / 27.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ZC 1 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1419 | 181.3 | -1450.1 | -1337.1 | 1631.4 | 0.27 / -2.04 / -1.91 | 486.4 / -1042.8 |
| ZC 2 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1389 | 124.0 | -1502.7 | -1408.8 | 1626.7 | 0.18 / -2.12 / -2.03 | 383.0 / -1171.7 |
| ZC 3 (diag) 30m WT[20, 2.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2235 | 31.4 | -1658.2 | -1546.2 | 1689.6 | 0.06 / -3.02 / -2.86 | 287.7 / -1291.1 |
| ZS 1 (diag) 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | negative pre-2023 | 3337 | -182.5 | -984.2 | -972.1 | 801.7 | -0.41 / -2.11 / -2.10 | 384.7 / -347.6 |
| ZS 2 (diag) 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1550 | 27.2 | -716.0 | -707.2 | 743.2 | 0.05 / -1.15 / -1.14 | 162.6 / -530.9 |
| ZS 3 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1471 | 485.8 | -252.0 | -244.5 | 737.8 | 0.68 / -0.37 / -0.36 | -18.9 / -692.7 |
| ZW 1 (diag) 30m HM[9, 21, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2190 | 374.1 | -653.7 | -609.5 | 1027.7 | 0.69 / -1.23 / -1.14 | 684.7 / -202.5 |
| ZW 2 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1453 | 51.2 | -948.7 | -899.9 | 999.9 | 0.06 / -1.32 / -1.26 | 411.2 / -425.1 |
| ZW 3 (diag) 30m HM[20, 55, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1528 | 52.7 | -1451.7 | -1376.7 | 1504.4 | 0.05 / -1.92 / -1.84 | 365.8 / -896.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ZC: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZS: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); ZW: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q10b.py (= ap_b1.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q10b/ (`Q10B_CO_all_selected_scored.csv`).

DONE Q10B
