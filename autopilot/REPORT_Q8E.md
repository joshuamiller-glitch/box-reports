# REPORT Q8E - Q8E: B1 grid on ETH (ETH)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 10 selected cells (+0 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.15; best pair-window standalone Sharpe +1.25.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Instruments: ETH. Grid: 180 cells per instrument = 4 bar sizes x 9 signal parameter sets x 5 trail exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ETH   |     180 |        180 |        89 |               2.225 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ETH   |     100 |                   89 |            24.45 |              32 |          0 |                       1.926 |            1.125 |           1.388 |        0 |       2.225 |                2.404 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH 1 | 15m WT[20, 3.0, 100] exit=ADRtrail0.15 | 663 | 2 | 2.22 | 0.60 | 1.25 | -0.17 / 1.01 | 0.16 / 0.08 / -0.15 | 0.00 | 0.16 | 1.00 | -0.00 | 0.50 | 1103 | NO |
| ETH 2 | 15m WT[20, 3.0, 100] exit=ATRtrail3.0 | 653 | 2 | 2.09 | 0.67 | 1.14 | -0.30 / 1.14 | 0.14 / 0.10 / -0.17 | 0.01 | 0.06 | 0.99 | -0.01 | 0.67 | 1090 | NO |
| ETH 3 | 10m HM[3, 6, 20] exit=ADRtrail0.2 | 2430 | 2 | 2.07 | -1.03 | 0.81 | -1.39 / 0.53 | 0.26 / 0.06 / -0.44 | -0.13 | -0.07 | 0.99 | -0.06 | 0.33 | 3877 | NO |
| ETH 4 | 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | 1698 | 2 | 1.97 | 0.01 | 1.10 | -0.16 / 0.46 | 0.23 / 0.46 / -0.25 | -0.05 | -0.18 | 1.00 | 0.02 | 0.00 | 2732 | NO |
| ETH 5 | 15m WT[20, 2.0, 100] exit=ADRtrail0.2 | 932 | 2 | 1.90 | -0.65 | 0.97 | -0.40 / 0.80 | 0.15 / 0.13 / -0.17 | -0.01 | -0.10 | 1.00 | -0.01 | 0.83 | 1528 | NO |
| ETH 6 | 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | 925 | 2 | 1.89 | -0.19 | 0.92 | -0.47 / 0.94 | 0.15 / 0.12 / -0.17 | -0.01 | -0.13 | 1.00 | -0.01 | 0.83 | 1512 | NO |
| ETH 7 | 15m WT[14, 2.0, 100] exit=ATRtrail3.0 | 915 | 2 | 1.83 | -0.08 | 1.05 | -0.08 / 1.02 | 0.14 / 0.15 / -0.13 | 0.00 | -0.15 | 0.96 | 0.00 | 0.50 | 1473 | NO |
| ETH 8 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 312 | 2 | 1.79 | 0.85 | 1.03 | -0.17 / 1.52 | 0.08 / -0.01 / -0.06 | 0.02 | -0.33 | 0.97 | -0.01 | 0.17 | 495 | NO |
| ETH 9 | 15m WT[20, 3.0, 100] exit=ATRtrail2.0 | 666 | 2 | 1.78 | -0.09 | 1.18 | 0.35 / 1.08 | 0.11 / 0.14 / -0.08 | -0.01 | -0.19 | 1.00 | -0.01 | 0.50 | 1106 | NO |
| ETH 10 | 15m WT[14, 2.0, 100] exit=ADRtrail0.15 | 992 | 2 | 1.71 | -0.40 | 1.18 | 0.48 / 0.74 | 0.15 / 0.20 / -0.07 | -0.01 | 0.22 | 1.00 | 0.02 | 0.33 | 1640 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 10 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 3 |
| standalone pair-window Sharpe above own random-entry null p95 | 10 |
| worst-decile corr <= +0.30 | 10 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | clean | 1.84 | 3.07 | -70789 | -63503 | 238531 | -78455 | 4.61 | 37.1 | 1.69 | -79516 | 309862 | -90843 |
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | H1 | 2.12 | 3.83 | -69686 | -56163 | 218214 | -70340 | 1.47 | 32.1 | 3.28 | -72652 | 144097 | -73339 |
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | H2 | -2.00 | -2.33 | -83842 | -74143 | 502788 | -88377 | -0.74 | 61.1 | 2.04 | -82375 | 219535 | -84088 |
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | all | 1.10 | 1.73 | -74044 | -66757 | 502788 | -88377 | 2.08 | 41.7 | 2.00 | -80007 | 309862 | -90843 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | -18.3 | 9.6 | 25.9 | 14.1 | 8.9 / 27.8 | 39.5 / 39.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ETH 1 15m WT[20, 3.0, 100] exit=ADRtrail0.15 | positive pre-2023 | 475 | 1121.9 | 400.5 | 647.7 | 721.4 | 1.67 / 0.60 / 0.96 | 1857.4 / 1289.2 |
| ETH 2 15m WT[20, 3.0, 100] exit=ATRtrail3.0 | positive pre-2023 | 472 | 909.0 | 381.7 | 566.0 | 527.2 | 1.60 / 0.67 / 0.99 | 1607.3 / 1195.1 |
| ETH 3 10m HM[3, 6, 20] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 1732 | 247.6 | -294.9 | -111.1 | 542.5 | 0.87 / -1.03 / -0.40 | 997.9 / 559.1 |
| ETH 4 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | positive pre-2023 | 1205 | 729.5 | 9.0 | 248.7 | 720.5 | 1.96 / 0.01 / 0.65 | 1218.2 / 648.0 |
| ETH 5 15m WT[20, 2.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 692 | 221.3 | -311.6 | -133.2 | 532.9 | 0.46 / -0.65 / -0.28 | 1254.8 / 831.6 |
| ETH 6 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 686 | 445.4 | -92.1 | 89.0 | 537.5 | 0.86 / -0.19 / 0.16 | 1259.9 / 835.9 |
| ETH 7 15m WT[14, 2.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 684 | 513.7 | -18.2 | 165.4 | 531.8 | 1.11 / -0.08 / 0.33 | 1145.8 / 739.9 |
| ETH 8 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | positive pre-2023 | 205 | 1198.5 | 853.0 | 970.1 | 345.5 | 1.19 / 0.85 / 0.96 | 1711.6 / 1450.4 |
| ETH 9 15m WT[20, 3.0, 100] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 476 | 733.1 | -53.8 | 220.7 | 786.9 | 1.11 / -0.09 / 0.33 | 1630.2 / 1010.1 |
| ETH 10 15m WT[14, 2.0, 100] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 739 | 527.0 | -188.3 | 52.8 | 715.3 | 1.05 / -0.40 / 0.08 | 1308.9 / 743.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ETH: 89 cells pass the clean rule against a replicate mean of 24.4 (p(count) = 0.00, p(top) = 0.00).
- Of 10 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.15 (ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15); bootstrap lower bound > 0 for 3 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 6, 'positive pre-2023': 4}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q8e.py (= ap_b1.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q8e/ (`Q8E_CO_all_selected_scored.csv`).

DONE Q8E
