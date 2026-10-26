# REPORT Q10A - Q10A: B7 grid on grains (ZC, ZS, ZW)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 5 selected cells (+9 diagnostic) scored on 3 instruments; best non-diagnostic all-in additive uplift at 20% share +0.01; best pair-window standalone Sharpe +0.42.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: ZC, ZS, ZW. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ZC    |     288 |        288 |         0 |               0.262 |                1 |          0 |            3 |
| ZS    |     288 |        288 |         2 |               0.668 |                2 |          2 |            3 |
| ZW    |     288 |        286 |         3 |               0.732 |                2 |          3 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ZC    |     100 |                    0 |             0.05 |               1 |       1    |                     nan     |            0.436 |           0.891 |   nan    |     nan     |                0.891 |
| ZS    |     100 |                    2 |             1.35 |               4 |       0.42 |                       0.529 |            0.549 |           0.986 |     0.36 |       0.668 |                1.223 |
| ZW    |     100 |                    3 |             0.89 |               3 |       0.05 |                       0.491 |            0.475 |           0.887 |     0.26 |       0.732 |                0.999 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZC 1 (diag) | 15m vwz[2.0, 'globex'] dir=against hold=240m day | 106 | 1 | 0.26 | -0.20 | -0.07 | -0.69 / 0.17 | 0.05 / -0.33 / -0.07 | -0.21 | 0.17 | 1.00 | -0.21 | 0.00 | 154 | diag |
| ZC 2 (diag) | 5m emax[9, 21] dir=with hold=240m day | 335 | 1 | 0.16 | -1.36 | -0.75 | -1.89 / -0.13 | 0.04 / -0.37 / -0.82 | -0.55 | 0.02 | 1.00 | -0.48 | 0.00 | 534 | diag |
| ZC 3 (diag) | 5m macd[12, 26] dir=with hold=240m day | 301 | 1 | -0.11 | -1.34 | -0.71 | -1.51 / -0.45 | -0.01 / -0.17 / -0.70 | -0.51 | 0.25 | 1.00 | -0.43 | 0.00 | 481 | diag |
| ZS 1 | 15m vwz[2.0, 'globex'] dir=with hold=240m day | 103 | 2 | 0.67 | -1.25 | 0.11 | -1.21 / 0.63 | 0.07 / 0.00 / -0.33 | -0.10 | -0.17 | 0.94 | -0.20 | 0.00 | 153 | NO |
| ZS 2 | 5m vwz[2.0, 'globex'] dir=with hold=240m day | 189 | 2 | 0.39 | -0.90 | 0.02 | -0.69 / 0.26 | -0.01 / 0.04 / -0.24 | -0.16 | -0.12 | 0.96 | -0.22 | 0.00 | 285 | NO |
| ZS 3 (diag) | 10m vwz[2.0, 'globex'] dir=with hold=240m day | 120 | 1 | 0.31 | -0.69 | -0.03 | -0.68 / 0.53 | -0.02 / -0.01 / -0.16 | -0.14 | -0.46 | 0.95 | -0.23 | 0.00 | 185 | diag |
| ZS 4 (diag) | 15m emax[9, 21] dir=against hold=180m day | 238 | 1 | 0.13 | -0.96 | -0.64 | -2.37 / 0.12 | -0.02 / -0.58 / -0.25 | -0.29 | -0.44 | 0.80 | -0.33 | 0.00 | 387 | diag |
| ZS 5 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=180m day | 151 | 1 | 0.03 | -1.15 | -0.47 | -1.75 / 0.42 | -0.06 / -0.11 / -0.44 | -0.27 | -0.00 | 0.88 | -0.33 | 0.00 | 237 | diag |
| ZW 1 | 10m macd[12, 26] dir=with hold=240m day | 197 | 2 | 0.73 | -0.59 | 0.19 | -0.76 / 0.40 | 0.10 / -0.10 / -0.21 | -0.13 | -0.32 | 0.97 | -0.18 | 0.00 | 300 | NO |
| ZW 2 | 15m st[14, 2.0] dir=with hold=240m day | 278 | 2 | 0.38 | -0.36 | -0.27 | -1.30 / 0.35 | 0.02 / -0.08 / -0.46 | -0.29 | 0.33 | 0.93 | -0.31 | 0.00 | 433 | NO |
| ZW 3 | 5m macd[12, 26] dir=with hold=240m day | 282 | 2 | 0.36 | -0.32 | 0.42 | 0.64 / 0.33 | -0.00 / 0.16 / 0.01 | -0.16 | 0.17 | 1.00 | -0.16 | 0.00 | 453 | NO |
| ZW 4 (diag) | 10m vwz[2.0, 'globex'] dir=against hold=240m day | 120 | 1 | 0.19 | 0.17 | 0.40 | 0.77 / 0.20 | 0.07 / 0.20 / 0.12 | -0.00 | 0.15 | 1.00 | -0.07 | 0.00 | 194 | diag |
| ZW 5 (diag) | 5m vwz[2.0, 'globex'] dir=against hold=240m day | 183 | 1 | 0.17 | 0.04 | 0.33 | 0.64 / 0.26 | 0.09 / 0.06 / 0.15 | -0.02 | -0.03 | 1.00 | -0.07 | 0.00 | 281 | diag |
| ZW 6 (diag) | 10m st[14, 2.0] dir=with hold=240m day | 359 | 1 | 0.14 | -0.94 | -0.02 | -0.30 / 0.04 | -0.03 / -0.10 / -0.15 | -0.24 | 0.36 | 0.98 | -0.25 | 0.00 | 561 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 5 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 3 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 10 |
| worst-decile corr <= +0.30 | 12 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZC 15m vwz[2.0, 'globex'] dir=against hold=240m day (diag) | clean | 0.26 | 0.37 | -147808 | -110350 | 592182 | -266909 | 0.40 | 30.5 | 1.51 | -85628 | 237994 | -91846 |
| ZC 15m vwz[2.0, 'globex'] dir=against hold=240m day (diag) | H1 | -2.10 | -2.22 | -105035 | -97273 | 358621 | -116728 | -0.91 | 39.3 | 2.50 | -80406 | 176238 | -88605 |
| ZC 15m vwz[2.0, 'globex'] dir=against hold=240m day (diag) | H2 | -0.01 | -0.01 | -115203 | -106459 | 312359 | -119575 | -0.01 | 30.6 | 2.22 | -80804 | 225905 | -81955 |
| ZC 15m vwz[2.0, 'globex'] dir=against hold=240m day (diag) | all | -0.07 | -0.09 | -137256 | -111202 | 1143881 | -266909 | -0.08 | 32.1 | 1.82 | -84887 | 237994 | -91846 |
| ZS 15m vwz[2.0, 'globex'] dir=with hold=240m day | clean | 0.67 | 1.15 | -117556 | -97805 | 763859 | -151880 | 0.79 | 30.5 | 1.53 | -84447 | 301013 | -107435 |
| ZS 15m vwz[2.0, 'globex'] dir=with hold=240m day | H1 | 0.44 | 0.76 | -74302 | -67938 | 136067 | -90686 | 0.56 | 28.6 | 2.83 | -77610 | 148675 | -78287 |
| ZS 15m vwz[2.0, 'globex'] dir=with hold=240m day | H2 | -2.66 | -2.63 | -132219 | -106128 | 607902 | -164988 | -0.88 | 33.3 | 1.96 | -88373 | 224550 | -89327 |
| ZS 15m vwz[2.0, 'globex'] dir=with hold=240m day | all | 0.11 | 0.17 | -117829 | -97224 | 808930 | -164988 | 0.18 | 31.0 | 1.82 | -85378 | 301013 | -107435 |
| ZW 5m macd[12, 26] dir=with hold=240m day | clean | 0.31 | 0.47 | -122309 | -103903 | 470826 | -157110 | 0.60 | 52.4 | 1.46 | -88083 | 324361 | -95943 |
| ZW 5m macd[12, 26] dir=with hold=240m day | H1 | 0.78 | 1.17 | -75982 | -64953 | 147712 | -101929 | 0.85 | 39.3 | 2.99 | -72384 | 156792 | -73035 |
| ZW 5m macd[12, 26] dir=with hold=240m day | H2 | 0.58 | 0.85 | -139762 | -110710 | 595269 | -151897 | 0.31 | 44.4 | 2.30 | -93598 | 224006 | -100042 |
| ZW 5m macd[12, 26] dir=with hold=240m day | all | 0.42 | 0.63 | -123923 | -103282 | 595269 | -157110 | 0.99 | 48.8 | 1.87 | -88473 | 324361 | -100042 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ZC 15m vwz[2.0, 'globex'] dir=against hold=240m day (diag) | -31.0 | 4.0 | 13.8 | 26.3 | 3.2 / 12.1 | 8.8 / 19.3 | NO |
| ZS 15m vwz[2.0, 'globex'] dir=with hold=240m day | -28.4 | -20.6 | 17.2 | 18.8 | -21.5 / 17.2 | 30.0 / 30.0 | NO |
| ZW 5m macd[12, 26] dir=with hold=240m day | -23.4 | -1.8 | 8.9 | 6.3 | -0.4 / 7.7 | 38.7 / 40.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ZC 1 (diag) 15m vwz[2.0, 'globex'] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 446 | 21.1 | -8.2 | -9.3 | 29.4 | 0.52 / -0.20 / -0.23 | 35.7 / 6.4 |
| ZC 2 (diag) 5m emax[9, 21] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1770 | 0.5 | -28.9 | -29.3 | 29.4 | 0.02 / -1.36 / -1.38 | 31.9 / 2.5 |
| ZC 3 (diag) 5m macd[12, 26] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1619 | 0.4 | -28.9 | -29.3 | 29.4 | 0.02 / -1.34 / -1.35 | 27.7 / -1.7 |
| ZS 1 15m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 407 | -65.3 | -94.7 | -95.5 | 29.4 | -0.87 / -1.25 / -1.26 | 74.0 / 44.7 |
| ZS 2 5m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 917 | -21.5 | -50.8 | -51.8 | 29.4 | -0.38 / -0.90 / -0.92 | 46.1 / 16.7 |
| ZS 3 (diag) 10m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 620 | -11.7 | -41.1 | -41.9 | 29.4 | -0.20 / -0.69 / -0.71 | 46.5 / 17.1 |
| ZS 4 (diag) 15m emax[9, 21] dir=against hold=180m day | negative pre-2023 | 1318 | -6.1 | -35.5 | -37.1 | 29.4 | -0.17 / -0.96 / -1.00 | 35.7 / 6.3 |
| ZS 5 (diag) 15m vwz[2.0, 'globex'] dir=with hold=180m day | negative pre-2023 | 642 | -30.6 | -60.0 | -61.3 | 29.4 | -0.59 / -1.15 / -1.18 | 34.4 / 5.1 |
| ZW 1 10m macd[12, 26] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1076 | 5.3 | -24.1 | -25.4 | 29.4 | 0.13 / -0.59 / -0.62 | 53.3 / 23.9 |
| ZW 2 15m st[14, 2.0] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1570 | 16.8 | -12.5 | -13.2 | 29.4 | 0.49 / -0.36 / -0.39 | 39.3 / 10.0 |
| ZW 3 5m macd[12, 26] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1626 | 19.9 | -9.4 | -10.4 | 29.4 | 0.67 / -0.32 / -0.35 | 38.1 / 8.7 |
| ZW 4 (diag) 10m vwz[2.0, 'globex'] dir=against hold=240m day | positive pre-2023 | 626 | 37.6 | 8.2 | 7.8 | 29.4 | 0.77 / 0.17 / 0.16 | 37.0 / 7.6 |
| ZW 5 (diag) 5m vwz[2.0, 'globex'] dir=against hold=240m day | positive pre-2023 | 934 | 31.2 | 1.8 | 1.4 | 29.4 | 0.77 / 0.04 / 0.03 | 34.9 / 5.5 |
| ZW 6 (diag) 10m st[14, 2.0] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1912 | 2.6 | -26.8 | -27.6 | 29.4 | 0.09 / -0.94 / -0.97 | 32.9 / 3.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ZC: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00); ZS: 2 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.42, p(top) = 0.36); ZW: 3 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.05, p(top) = 0.26).
- Of 5 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.01 (ZW 5m macd[12, 26] dir=with hold=240m day); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 3, 'negative pre-2023': 2}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q10a.py (= ap_b7.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q10a/ (`Q10A_CO_all_selected_scored.csv`).

DONE Q10A
