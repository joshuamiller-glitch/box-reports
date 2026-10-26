# REPORT Q17B - Q17B: B1 grid on livestock (HE, LE)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 10 selected cells (+3 diagnostic) scored on 2 instruments; best non-diagnostic all-in additive uplift at 20% share +0.02; best pair-window standalone Sharpe +0.74.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Instruments: HE, LE. Grid: 180 cells per instrument = 4 bar sizes x 9 signal parameter sets x 5 trail exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| HE    |     180 |        170 |         0 |               0.232 |                1 |          0 |            3 |
| LE    |     180 |        170 |        28 |               1.555 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| HE    |     200 |                    0 |            1.125 |               5 |          1 |                     nan     |            0.471 |            0.91 |   nan    |     nan     |                0.963 |
| LE    |     200 |                   28 |            3.42  |               9 |          0 |                       1.012 |            0.54  |            0.9  |     0.02 |       1.146 |                1.358 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HE 1 (diag) | 15m HM[20, 55, 200] exit=ATRtrail3.0 | 173 | 1 | 0.23 | -0.72 | -0.16 | -0.85 / 0.06 | -0.00 / -0.01 / -0.00 | -0.02 | 0.01 | 0.98 | -0.03 | 0.00 | 276 | diag |
| HE 2 (diag) | 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | 208 | 1 | 0.09 | -2.37 | -0.19 | -0.57 / -0.92 | 0.00 / 0.02 / -0.05 | -0.06 | -0.02 | 1.00 | -0.05 | 0.00 | 296 | diag |
| HE 3 (diag) | 30m ST[14, 2.0, 200] exit=ATRtrail2.0 | 135 | 1 | 0.06 | -0.71 | -0.30 | -1.01 / 0.41 | -0.00 / -0.04 / -0.01 | -0.02 | -0.10 | 0.85 | -0.03 | 0.00 | 219 | diag |
| LE 1 | 15m WT[20, 3.0, 100] exit=ATRtrail3.0 | 127 | 2 | 1.15 | -1.11 | 0.71 | -0.18 / 0.92 | 0.02 / 0.02 / -0.02 | 0.00 | 0.17 | 1.00 | -0.01 | 0.50 | 192 | NO |
| LE 2 | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 126 | 2 | 1.07 | -0.40 | 0.04 | -1.98 / 0.89 | 0.02 / -0.01 / -0.05 | -0.01 | 0.22 | 0.87 | -0.02 | 0.83 | 207 | NO |
| LE 3 | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 124 | 2 | 1.07 | -0.44 | 0.07 | -1.64 / 0.92 | 0.02 / -0.01 / -0.02 | -0.00 | 0.22 | 0.84 | -0.01 | 0.83 | 205 | NO |
| LE 4 | 15m ST[14, 3.0, 200] exit=ATRtrail3.0 | 107 | 2 | 1.06 | -0.91 | 0.74 | 0.06 / 1.28 | 0.02 / -0.01 / 0.00 | 0.01 | 0.45 | 1.00 | -0.01 | 0.33 | 163 | NO |
| LE 5 | 10m HM[9, 21, 200] exit=ATRtrail3.0 | 260 | 2 | 1.05 | -1.84 | 0.46 | -0.54 / 0.76 | 0.03 / -0.01 / 0.01 | -0.00 | -0.19 | 1.00 | -0.01 | 0.50 | 421 | NO |
| LE 6 | 30m ST[4, 2.0, 20] exit=ATRtrail2.0 | 236 | 2 | 0.99 | -1.23 | 0.54 | -0.20 / 0.72 | 0.02 / 0.06 / -0.04 | -0.00 | -0.56 | 0.99 | -0.01 | 0.67 | 377 | NO |
| LE 7 | 30m HM[3, 6, 20] exit=ATRtrail2.0 | 378 | 2 | 0.97 | -1.54 | 0.49 | -0.39 / 0.71 | 0.03 / -0.00 / -0.02 | -0.01 | 0.00 | 0.99 | -0.02 | 0.17 | 591 | NO |
| LE 8 | 30m WT[14, 2.0, 100] exit=ATRtrail3.0 | 134 | 2 | 0.96 | -0.95 | 0.38 | -0.64 / 1.01 | 0.02 / -0.03 / 0.01 | 0.00 | -0.13 | 0.96 | -0.01 | 0.67 | 210 | NO |
| LE 9 | 30m HM[3, 6, 20] exit=ATRtrail3.0 | 357 | 2 | 0.96 | -1.22 | 0.53 | -0.35 / 0.61 | 0.02 / -0.01 / -0.00 | -0.00 | 0.08 | 1.00 | -0.01 | 0.17 | 561 | NO |
| LE 10 | 15m WT[20, 3.0, 100] exit=ATRtrail2.0 | 127 | 2 | 0.84 | -1.38 | 0.41 | -0.44 / 0.34 | 0.02 / 0.03 / -0.05 | -0.01 | 0.13 | 0.97 | -0.02 | 0.33 | 192 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 3 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 10 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 10 |
| worst-decile corr <= +0.30 | 12 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HE 15m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | clean | 0.16 | 0.25 | -14359 | -12087 | 60139 | -18392 | 0.29 | 44.8 | 1.46 | -80741 | 288143 | -83799 |
| HE 15m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H1 | -1.43 | -1.67 | -10606 | -9973 | 32945 | -11098 | -0.76 | 53.6 | 2.82 | -76739 | 153455 | -77516 |
| HE 15m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H2 | -0.53 | -0.72 | -10304 | -10103 | 34180 | -10360 | -0.48 | 41.7 | 2.48 | -80806 | 219284 | -82181 |
| HE 15m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | all | -0.16 | -0.23 | -13112 | -11460 | 79776 | -18392 | -0.30 | 45.8 | 1.89 | -80509 | 288143 | -83799 |
| LE 10m HM[9, 21, 200] exit=ATRtrail3.0 | clean | 1.09 | 1.75 | -18276 | -14618 | 95207 | -27336 | 1.56 | 43.8 | 1.49 | -79343 | 275772 | -80761 |
| LE 10m HM[9, 21, 200] exit=ATRtrail3.0 | H1 | -0.72 | -1.01 | -17188 | -15321 | 85651 | -17291 | -0.28 | 57.1 | 2.81 | -76387 | 155309 | -77309 |
| LE 10m HM[9, 21, 200] exit=ATRtrail3.0 | H2 | -0.42 | -0.63 | -18340 | -16937 | 61293 | -19698 | -0.36 | 50.0 | 2.49 | -79024 | 218354 | -80467 |
| LE 10m HM[9, 21, 200] exit=ATRtrail3.0 | all | 0.46 | 0.71 | -19081 | -15779 | 135804 | -27336 | 0.76 | 47.6 | 1.92 | -79061 | 275772 | -80761 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| HE 15m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | -30.3 | 27.1 | 27.1 | 25.7 | 26.5 / 26.1 | 31.5 / 31.7 | NO |
| LE 10m HM[9, 21, 200] exit=ATRtrail3.0 | -28.9 | 29.5 | 29.8 | 32.3 | 28.9 / 28.6 | 30.5 / 32.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| HE 1 (diag) 15m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 992 | 257.8 | -447.1 | -439.2 | 704.8 | 0.41 / -0.72 / -0.71 | 591.3 / 99.6 |
| HE 2 (diag) 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | negative pre-2023 | 1424 | -178.9 | -1894.3 | -1857.2 | 1715.4 | -0.26 / -2.37 / -2.32 | 1529.0 / -15.8 |
| HE 3 (diag) 30m ST[14, 2.0, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 933 | 334.9 | -578.6 | -621.5 | 913.5 | 0.43 / -0.71 / -0.76 | 587.4 / 63.7 |
| LE 1 15m WT[20, 3.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1104 | 185.7 | -862.5 | -563.1 | 1048.2 | 0.26 / -1.11 / -0.75 | 1306.7 / 881.0 |
| LE 2 30m HM[20, 55, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 714 | 521.3 | -299.5 | -51.3 | 820.8 | 0.70 / -0.40 / -0.07 | 1345.5 / 889.5 |
| LE 3 30m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 708 | 292.0 | -256.0 | -90.4 | 548.0 | 0.51 / -0.44 / -0.16 | 920.5 / 617.1 |
| LE 4 15m ST[14, 3.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 964 | 359.7 | -736.2 | -424.4 | 1096.0 | 0.49 / -0.91 / -0.55 | 1399.3 / 982.5 |
| LE 5 10m HM[9, 21, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1861 | 12.7 | -1152.3 | -816.0 | 1165.0 | 0.02 / -1.84 / -1.37 | 1114.7 / 571.7 |
| LE 6 30m ST[4, 2.0, 20] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1563 | 281.2 | -834.7 | -515.9 | 1115.9 | 0.46 / -1.23 / -0.79 | 1011.4 / 548.6 |
| LE 7 30m HM[3, 6, 20] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 2437 | 225.0 | -811.0 | -509.4 | 1035.9 | 0.48 / -1.54 / -1.02 | 912.6 / 448.6 |
| LE 8 30m WT[14, 2.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 986 | 121.7 | -628.8 | -411.4 | 750.6 | 0.20 / -0.95 / -0.64 | 882.2 / 578.3 |
| LE 9 30m HM[3, 6, 20] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2210 | 148.5 | -522.2 | -326.2 | 670.7 | 0.37 / -1.22 / -0.78 | 655.4 / 345.6 |
| LE 10 15m WT[20, 3.0, 100] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1109 | 261.3 | -1320.6 | -869.0 | 1581.8 | 0.31 / -1.38 / -0.96 | 1508.9 / 870.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): HE: 0 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 1.00); LE: 28 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 0.00, p(top) = 0.02).
- Of 10 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.02 (LE 10m HM[9, 21, 200] exit=ATRtrail3.0); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 10}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q17b.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q17b/ (`Q17B_CO_all_selected_scored.csv`).

DONE Q17B
