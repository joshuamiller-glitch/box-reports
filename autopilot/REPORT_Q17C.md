# REPORT Q17C - Q17C: B11 grid on livestock (HE, LE)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 10 selected cells (+6 diagnostic) scored on 2 instruments; best non-diagnostic all-in additive uplift at 20% share +0.06; best pair-window standalone Sharpe +0.53.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Levels: opening range of the first 15/30/60 min of the instrument RTH (ES/RTY 09:30, GC/ZN 08:20, CL 09:00 ET) or the prior trading day's high/low. First tf-bar close beyond a level per day, trade with (breakout) or against (fade); stop a x ADR20, bracket 1R/2R target, trail, or hold to flat.
- Instruments: HE, LE. Grid: 192 cells per instrument = 4 levels x 2 bar sizes x 2 modes x 12 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| HE    |     192 |        192 |         3 |               0.827 |                2 |          3 |            3 |
| LE    |     192 |        192 |         7 |               0.659 |                2 |          7 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| HE    |     200 |                    3 |            0.595 |               2 |      0     |                       0.67  |            0.435 |           0.839 |    0.08  |       0.827 |                0.966 |
| LE    |     200 |                    7 |            3.165 |               8 |      0.015 |                       0.396 |            0.517 |           0.835 |    0.725 |       0.659 |                1.277 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HE 1 | PD 5m fade exit=b20.2xADR | 399 | 2 | 0.83 | -1.02 | 0.53 | -0.09 / -0.68 | 0.11 / 0.12 / -0.05 | -0.15 | 0.53 | 1.00 | -0.12 | 0.00 | 633 | NO |
| HE 2 | PD 5m fade exit=tr0.3xADR | 399 | 2 | 0.71 | -1.10 | 0.49 | -0.07 / -0.16 | 0.11 / 0.12 / -0.12 | -0.18 | 0.35 | 1.00 | -0.13 | 0.00 | 633 | NO |
| HE 3 | PD 5m fade exit=b20.3xADR | 399 | 2 | 0.48 | -0.99 | 0.22 | -0.44 / -0.47 | 0.05 / -0.03 / -0.13 | -0.18 | 0.32 | 0.99 | -0.17 | 0.00 | 633 | NO |
| HE 4 (diag) | PD 5m fade exit=hd0.2xADR | 399 | 1 | 0.48 | -0.55 | 0.13 | -0.61 / -0.35 | 0.06 / -0.18 / -0.07 | -0.22 | 0.39 | 1.00 | -0.18 | 0.00 | 633 | diag |
| HE 5 (diag) | OR15 5m with exit=tr0.3xADR | 496 | 1 | 0.20 | -1.27 | -0.85 | -2.61 / -0.52 | 0.05 / -0.81 / -0.33 | -0.44 | 0.48 | 0.95 | -0.33 | 0.00 | 797 | diag |
| HE 6 (diag) | PD 5m fade exit=hd0.3xADR | 399 | 1 | 0.03 | -0.73 | -0.14 | -0.58 / 0.02 | -0.03 / -0.24 / -0.06 | -0.25 | 0.23 | 0.96 | -0.24 | 0.00 | 633 | diag |
| LE 1 | OR30 5m with exit=b20.3xADR | 486 | 2 | 0.66 | -0.79 | -0.48 | -2.08 / 0.59 | 0.14 / -1.21 / -0.47 | -0.36 | -0.33 | 0.76 | -0.41 | 0.00 | 778 | NO |
| LE 2 | OR30 15m with exit=b20.2xADR | 473 | 2 | 0.58 | -0.93 | -0.18 | -1.11 / 0.23 | 0.14 / -1.05 / -0.44 | -0.38 | -0.14 | 0.94 | -0.38 | 0.00 | 761 | NO |
| LE 3 | OR30 15m with exit=tr0.3xADR | 473 | 2 | 0.51 | -1.29 | -0.45 | -1.51 / 0.57 | 0.10 / -1.25 / -0.60 | -0.50 | -0.33 | 0.86 | -0.48 | 0.00 | 761 | NO |
| LE 4 | OR30 15m with exit=b10.3xADR | 473 | 2 | 0.44 | -1.11 | -0.88 | -2.52 / 0.33 | 0.11 / -1.28 / -0.80 | -0.48 | -0.17 | 0.68 | -0.54 | 0.00 | 761 | NO |
| LE 5 | OR60 15m with exit=b20.2xADR | 414 | 2 | 0.39 | -1.44 | -0.29 | -1.00 / 0.27 | 0.05 / -1.24 / -0.15 | -0.41 | -0.58 | 0.90 | -0.42 | 0.00 | 667 | NO |
| LE 6 | OR30 15m with exit=tr0.2xADR | 473 | 2 | 0.13 | -2.53 | -0.21 | -0.71 / 0.21 | 0.06 / -0.82 / -0.29 | -0.44 | -0.22 | 1.00 | -0.34 | 0.00 | 761 | NO |
| LE 7 | OR15 5m with exit=b20.3xADR | 499 | 2 | 0.06 | -0.95 | -0.82 | -2.23 / 0.50 | 0.01 / -1.07 / -0.49 | -0.40 | -0.39 | 0.52 | -0.45 | 0.00 | 797 | NO |
| LE 8 (diag) | OR30 5m with exit=tr0.3xADR | 486 | 1 | 0.41 | -1.42 | -0.33 | -1.29 / 0.67 | 0.08 / -0.94 / -0.36 | -0.38 | -0.16 | 0.78 | -0.37 | 0.00 | 778 | diag |
| LE 9 (diag) | OR30 5m with exit=b10.3xADR | 486 | 1 | 0.27 | -1.16 | -0.91 | -2.39 / 0.32 | 0.07 / -1.38 / -0.64 | -0.49 | -0.11 | 0.66 | -0.52 | 0.00 | 778 | diag |
| LE 10 (diag) | OR30 15m with exit=b20.3xADR | 473 | 1 | 0.25 | -0.77 | -0.69 | -1.86 / 0.42 | 0.06 / -1.41 / -0.54 | -0.48 | -0.40 | 0.67 | -0.53 | 0.00 | 761 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 6 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 2 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 6 |
| worst-decile corr <= +0.30 | 11 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HE PD 5m fade exit=b20.2xADR | clean | 0.84 | 1.38 | -106760 | -92818 | 473002 | -123255 | 1.60 | 46.7 | 1.57 | -90895 | 335700 | -103773 |
| HE PD 5m fade exit=b20.2xADR | H1 | 0.19 | 0.27 | -94819 | -88295 | 223571 | -95294 | 0.18 | 42.9 | 2.94 | -69362 | 133481 | -69804 |
| HE PD 5m fade exit=b20.2xADR | H2 | -0.35 | -0.47 | -87671 | -77964 | 309785 | -104197 | -0.27 | 50.0 | 2.43 | -90700 | 217884 | -92933 |
| HE PD 5m fade exit=b20.2xADR | all | 0.53 | 0.82 | -103822 | -90406 | 473002 | -123255 | 1.51 | 46.4 | 1.96 | -89732 | 335700 | -103773 |
| LE OR30 15m with exit=tr0.2xADR | clean | 0.27 | 0.43 | -96427 | -87227 | 551467 | -115767 | 0.44 | 50.5 | 1.52 | -88746 | 330881 | -94277 |
| LE OR30 15m with exit=tr0.2xADR | H1 | -1.05 | -1.42 | -199436 | -187030 | 767346 | -231629 | -0.55 | 60.7 | 2.01 | -93072 | 200274 | -97948 |
| LE OR30 15m with exit=tr0.2xADR | H2 | -0.42 | -0.69 | -144148 | -127358 | 603240 | -148456 | -0.33 | 69.4 | 2.20 | -90684 | 252882 | -96160 |
| LE OR30 15m with exit=tr0.2xADR | all | -0.21 | -0.31 | -147486 | -121010 | 905182 | -231629 | -0.41 | 56.5 | 1.77 | -90856 | 330881 | -97948 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| HE PD 5m fade exit=b20.2xADR | -22.2 | -9.3 | 9.3 | -2.0 | -10.1 / 6.5 | 46.3 / 45.9 | NO |
| LE OR30 15m with exit=tr0.2xADR | -34.1 | -19.7 | 1.8 | 0.6 | 3.5 / 8.2 | -26.2 / -18.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| HE 1 PD 5m fade exit=b20.2xADR | gross-positive, cost-negative pre-2023 | 2025 | 6.1 | -15.6 | -14.3 | 21.7 | 0.41 / -1.02 / -0.93 | 33.7 / 12.6 |
| HE 2 PD 5m fade exit=tr0.3xADR | gross-positive, cost-negative pre-2023 | 2025 | 5.1 | -19.3 | -17.8 | 24.4 | 0.30 / -1.10 / -1.02 | 37.7 / 13.3 |
| HE 3 PD 5m fade exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2025 | 3.8 | -18.9 | -17.5 | 22.7 | 0.21 / -0.99 / -0.92 | 32.8 / 10.6 |
| HE 4 (diag) PD 5m fade exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 2025 | 13.0 | -11.4 | -9.9 | 24.4 | 0.63 / -0.55 / -0.48 | 33.8 / 9.5 |
| HE 5 (diag) OR15 5m with exit=tr0.3xADR | gross-positive, cost-negative pre-2023 | 2580 | 5.4 | -19.0 | -17.4 | 24.4 | 0.34 / -1.27 / -1.17 | 24.8 / 0.4 |
| HE 6 (diag) PD 5m fade exit=hd0.3xADR | gross-positive, cost-negative pre-2023 | 2025 | 8.3 | -16.1 | -14.6 | 24.4 | 0.38 / -0.73 / -0.66 | 25.8 / 1.5 |
| LE 1 OR30 5m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2512 | 10.3 | -12.4 | -5.4 | 22.7 | 0.67 / -0.79 / -0.34 | 39.8 / 17.5 |
| LE 2 OR30 15m with exit=b20.2xADR | gross-positive, cost-negative pre-2023 | 2438 | 10.1 | -11.7 | -4.9 | 21.8 | 0.84 / -0.93 / -0.39 | 32.5 / 10.9 |
| LE 3 OR30 15m with exit=tr0.3xADR | gross-positive, cost-negative pre-2023 | 2438 | 7.5 | -16.9 | -9.3 | 24.4 | 0.59 / -1.29 / -0.71 | 34.5 / 10.1 |
| LE 4 OR30 15m with exit=b10.3xADR | gross-positive, cost-negative pre-2023 | 2438 | 6.0 | -14.5 | -8.1 | 20.5 | 0.48 / -1.11 / -0.62 | 29.0 / 8.8 |
| LE 5 OR60 15m with exit=b20.2xADR | gross-positive, cost-negative pre-2023 | 2130 | 3.9 | -18.4 | -11.5 | 22.3 | 0.32 / -1.44 / -0.90 | 28.9 / 6.9 |
| LE 6 OR30 15m with exit=tr0.2xADR | gross-positive, cost-negative pre-2023 | 2438 | 1.9 | -22.5 | -14.9 | 24.4 | 0.22 / -2.53 / -1.68 | 27.7 / 3.4 |
| LE 7 OR15 5m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2587 | 6.8 | -15.8 | -8.8 | 22.5 | 0.42 / -0.95 / -0.53 | 27.7 / 5.3 |
| LE 8 (diag) OR30 5m with exit=tr0.3xADR | gross-positive, cost-negative pre-2023 | 2512 | 6.1 | -18.3 | -10.7 | 24.4 | 0.48 / -1.42 / -0.83 | 33.5 / 9.1 |
| LE 9 (diag) OR30 5m with exit=b10.3xADR | gross-positive, cost-negative pre-2023 | 2512 | 5.7 | -14.6 | -8.3 | 20.3 | 0.47 / -1.16 / -0.66 | 25.8 / 5.8 |
| LE 10 (diag) OR30 15m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2438 | 10.9 | -11.9 | -4.8 | 22.8 | 0.72 / -0.77 / -0.31 | 31.2 / 8.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): HE: 3 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.00, p(top) = 0.08); LE: 7 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 0.01, p(top) = 0.72).
- Of 10 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.06 (HE PD 5m fade exit=b20.2xADR); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 10}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q17c.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q17c/ (`Q17C_CO_all_selected_scored.csv`).

DONE Q17C
