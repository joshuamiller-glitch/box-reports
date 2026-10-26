# REPORT Q9C - Q9C: B11 grid on rates (ZB, ZF, ZT)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+9 diagnostic) scored on 3 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe -1.07.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Levels: opening range of the first 15/30/60 min of the instrument RTH (ES/RTY 09:30, GC/ZN 08:20, CL 09:00 ET) or the prior trading day's high/low. First tf-bar close beyond a level per day, trade with (breakout) or against (fade); stop a x ADR20, bracket 1R/2R target, trail, or hold to flat.
- Instruments: ZB, ZF, ZT. Grid: 192 cells per instrument = 4 levels x 2 bar sizes x 2 modes x 12 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ZB    |     192 |        192 |         0 |              -1.106 |                0 |          0 |            3 |
| ZF    |     192 |        192 |         0 |              -0.726 |                0 |          0 |            3 |
| ZT    |     192 |        192 |         0 |              -0.923 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ZB    |     100 |                    0 |             0    |               0 |          1 |                         nan |          nan     |         nan     |      nan |         nan |              nan     |
| ZF    |     100 |                    0 |             0.03 |               1 |          1 |                         nan |            0.695 |           0.883 |      nan |         nan |                0.883 |
| ZT    |     100 |                    0 |             0.01 |               1 |          1 |                         nan |            0.156 |           0.156 |      nan |         nan |                0.156 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZB 1 (diag) | OR30 5m fade exit=hd0.3xADR | 500 | 0 | -1.11 | -2.32 | -1.80 | -3.89 / -1.90 | -0.22 / -0.32 / -0.59 | -0.69 | -0.41 | 0.96 | -0.49 | 0.00 | 799 | diag |
| ZB 2 (diag) | OR30 5m fade exit=b20.3xADR | 500 | 0 | -1.63 | -2.42 | -2.25 | -3.85 / -2.31 | -0.34 / -0.34 / -0.66 | -0.78 | -0.44 | 0.82 | -0.59 | 0.00 | 799 | diag |
| ZB 3 (diag) | OR30 5m fade exit=b10.3xADR | 500 | 0 | -1.72 | -2.64 | -2.50 | -4.39 / -1.90 | -0.36 / -0.44 / -0.76 | -0.86 | -0.49 | 0.61 | -0.66 | 0.00 | 799 | diag |
| ZF 1 (diag) | OR15 15m fade exit=hd0.2xADR | 492 | 0 | -0.73 | -2.84 | -1.11 | -2.24 / -1.62 | -0.14 / -0.33 / -0.32 | -0.51 | -0.66 | 1.00 | -0.37 | 0.00 | 788 | diag |
| ZF 2 (diag) | OR15 15m fade exit=hd0.3xADR | 492 | 0 | -0.73 | -2.49 | -1.07 | -2.03 / -1.47 | -0.12 / -0.32 / -0.25 | -0.47 | -0.70 | 0.99 | -0.34 | 0.00 | 788 | diag |
| ZF 3 (diag) | OR15 5m fade exit=hd0.2xADR | 498 | 0 | -0.81 | -2.49 | -1.41 | -3.76 / -1.84 | -0.17 / -0.43 / -0.39 | -0.55 | -0.52 | 0.99 | -0.41 | 0.00 | 796 | diag |
| ZT 1 (diag) | PD 5m with exit=hd0.2xADR | 378 | 0 | -0.92 | -2.61 | -1.59 | -3.18 / -1.71 | -0.23 / -0.48 / -0.41 | -0.69 | 0.21 | 0.92 | -0.49 | 0.00 | 595 | diag |
| ZT 2 (diag) | PD 5m with exit=hd0.3xADR | 378 | 0 | -1.15 | -2.46 | -1.48 | -2.30 / -1.16 | -0.27 / -0.16 / -0.42 | -0.62 | 0.35 | 0.95 | -0.47 | 0.00 | 595 | diag |
| ZT 3 (diag) | PD 5m with exit=hd0.1xADR | 378 | 0 | -1.38 | -2.36 | -1.91 | -3.22 / -2.18 | -0.32 / -0.41 / -0.43 | -0.79 | 0.22 | 1.00 | -0.54 | 0.00 | 592 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 0 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 6 |
| worst-decile corr <= +0.30 | 8 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZB OR30 5m fade exit=hd0.3xADR (diag) | clean | -1.08 | -1.45 | -115424 | -103601 | 1311884 | -146368 | -0.75 | 53.3 | 1.24 | -89874 | 269001 | -106282 |
| ZB OR30 5m fade exit=hd0.3xADR (diag) | H1 | -2.90 | -3.16 | -74107 | -71326 | 490658 | -77943 | -0.82 | 75.0 | 2.50 | -76787 | 154963 | -77433 |
| ZB OR30 5m fade exit=hd0.3xADR (diag) | H2 | -4.60 | -4.15 | -99635 | -88043 | 942799 | -107974 | -0.98 | 66.7 | 1.70 | -85743 | 214598 | -86504 |
| ZB OR30 5m fade exit=hd0.3xADR (diag) | all | -1.80 | -2.24 | -109688 | -97770 | 2449938 | -146368 | -0.94 | 59.5 | 1.53 | -87603 | 269001 | -106282 |
| ZF OR15 15m fade exit=hd0.3xADR (diag) | clean | -0.69 | -1.00 | -112170 | -101411 | 944155 | -128070 | -0.67 | 57.1 | 1.34 | -89484 | 241423 | -99846 |
| ZF OR15 15m fade exit=hd0.3xADR (diag) | H1 | -2.24 | -2.82 | -62305 | -56469 | 315213 | -70821 | -0.94 | 71.4 | 2.50 | -75138 | 159228 | -81487 |
| ZF OR15 15m fade exit=hd0.3xADR (diag) | H2 | -1.93 | -2.35 | -101735 | -85886 | 547437 | -106305 | -0.85 | 61.1 | 2.05 | -79431 | 206645 | -85685 |
| ZF OR15 15m fade exit=hd0.3xADR (diag) | all | -1.07 | -1.48 | -107770 | -94755 | 1635827 | -128070 | -0.85 | 60.1 | 1.68 | -87111 | 241423 | -99846 |
| ZT PD 5m with exit=hd0.3xADR (diag) | clean | -1.16 | -1.61 | -113269 | -97511 | 1264435 | -138823 | -0.83 | 60.0 | 1.19 | -92398 | 350285 | -102794 |
| ZT PD 5m with exit=hd0.3xADR (diag) | H1 | -1.29 | -1.73 | -69688 | -67161 | 402400 | -75211 | -0.49 | 60.7 | 2.67 | -78044 | 169273 | -79894 |
| ZT PD 5m with exit=hd0.3xADR (diag) | H2 | -3.02 | -3.16 | -94498 | -86025 | 661706 | -103864 | -0.99 | 63.9 | 1.87 | -87788 | 232480 | -93585 |
| ZT PD 5m with exit=hd0.3xADR (diag) | all | -1.48 | -1.94 | -106836 | -92134 | 2117556 | -138823 | -0.90 | 60.7 | 1.55 | -90655 | 350285 | -102794 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ZB OR30 5m fade exit=hd0.3xADR (diag) | -55.8 | -18.5 | 10.3 | 30.4 | -19.5 / 5.8 | 30.3 / 31.6 | NO |
| ZF OR15 15m fade exit=hd0.3xADR (diag) | -45.5 | -6.1 | 13.2 | 27.9 | -7.0 / 8.0 | 23.9 / 34.8 | NO |
| ZT PD 5m with exit=hd0.3xADR (diag) | -51.3 | -11.9 | 5.0 | -7.6 | -12.8 / 1.7 | 26.9 / 29.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ZB 1 (diag) OR30 5m fade exit=hd0.3xADR | negative pre-2023 | 2643 | -8.1 | -74.9 | -93.8 | 66.9 | -0.25 / -2.32 / -2.91 | 30.0 / -36.8 |
| ZB 2 (diag) OR30 5m fade exit=b20.3xADR | negative pre-2023 | 2643 | -10.4 | -73.1 | -90.9 | 62.8 | -0.35 / -2.42 / -2.99 | 13.2 / -49.0 |
| ZB 3 (diag) OR30 5m fade exit=b10.3xADR | negative pre-2023 | 2643 | -11.4 | -66.1 | -81.6 | 54.7 | -0.47 / -2.64 / -3.23 | 13.2 / -41.2 |
| ZF 1 (diag) OR15 15m fade exit=hd0.2xADR | negative pre-2023 | 2632 | -2.0 | -22.0 | -24.1 | 20.0 | -0.26 / -2.84 / -3.11 | 13.1 / -6.9 |
| ZF 2 (diag) OR15 15m fade exit=hd0.3xADR | negative pre-2023 | 2632 | -1.4 | -21.4 | -23.5 | 20.0 | -0.17 / -2.49 / -2.73 | 12.4 / -7.6 |
| ZF 3 (diag) OR15 5m fade exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 2658 | 0.7 | -19.3 | -21.4 | 20.0 | 0.09 / -2.49 / -2.76 | 11.7 / -8.3 |
| ZT 1 (diag) PD 5m with exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 1619 | 0.8 | -19.2 | -20.2 | 20.0 | 0.10 / -2.61 / -2.73 | 12.4 / -7.6 |
| ZT 2 (diag) PD 5m with exit=hd0.3xADR | gross-positive, cost-negative pre-2023 | 1749 | 1.6 | -18.4 | -19.4 | 20.0 | 0.22 / -2.46 / -2.60 | 8.9 / -11.1 |
| ZT 3 (diag) PD 5m with exit=hd0.1xADR | gross-positive, cost-negative pre-2023 | 1088 | 0.2 | -19.8 | -20.7 | 20.0 | 0.03 / -2.36 / -2.45 | 9.8 / -10.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ZB: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZF: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZT: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q9c.py (= ap_b11.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q9c/ (`Q9C_CO_all_selected_scored.csv`).

DONE Q9C
