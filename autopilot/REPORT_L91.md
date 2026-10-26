# REPORT L91 - L91: ST/HM/WT signals with ATR-trail exits on NKD in Asia hours (19:00-02:00 ET)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+3 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe +0.20.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Restricted to entries 19:00-01:30 ET with flatten at 02:00 ET (NKD Asia window).
- Instruments: NKD. Grid: 180 cells = B1 grid on NKD, Asia window only.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| NKD   |     180 |        180 |         0 |               0.164 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| NKD   |     200 |                    0 |             0.84 |               4 |          1 |                         nan |            0.479 |           0.935 |      nan |         nan |                1.058 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NKD 1 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 172 | 1 | 0.16 | -0.99 | 0.07 | -0.15 / 1.13 | 0.01 / 0.03 / -0.01 | -0.01 | -0.03 | 0.85 | -0.02 | 0.17 | 280 | diag |
| NKD 2 (diag) | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 190 | 1 | 0.12 | -0.89 | -0.12 | -0.29 / 1.20 | -0.00 / 0.01 / -0.02 | -0.02 | -0.31 | 0.82 | -0.03 | 0.00 | 316 | diag |
| NKD 3 (diag) | 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | 361 | 1 | 0.04 | -0.76 | 0.20 | 0.33 / 1.21 | 0.01 / 0.06 / -0.00 | -0.02 | 0.02 | 0.96 | -0.03 | 0.67 | 585 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 3 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 2 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 1 |
| worst-decile corr <= +0.30 | 3 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NKD 30m ST[4, 2.0, 20] exit=ATRtrail3.0 (diag) | clean | 0.13 | 0.20 | -24638 | -20061 | 170711 | -41272 | 0.14 | 55.2 | 1.47 | -80574 | 282168 | -84016 |
| NKD 30m ST[4, 2.0, 20] exit=ATRtrail3.0 (diag) | H1 | 0.74 | 1.22 | -17524 | -17050 | 54814 | -17888 | 0.57 | 53.6 | 2.89 | -76418 | 145986 | -77154 |
| NKD 30m ST[4, 2.0, 20] exit=ATRtrail3.0 (diag) | H2 | 0.08 | 0.12 | -28581 | -23630 | 147513 | -31039 | 0.04 | 50.0 | 2.29 | -80208 | 218712 | -81561 |
| NKD 30m ST[4, 2.0, 20] exit=ATRtrail3.0 (diag) | all | 0.20 | 0.31 | -25222 | -20876 | 170711 | -41272 | 0.36 | 53.6 | 1.87 | -80199 | 282168 | -84016 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| NKD 30m ST[4, 2.0, 20] exit=ATRtrail3.0 (diag) | -29.3 | 26.7 | 27.9 | 28.9 | 26.1 / 26.3 | 32.2 / 32.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| NKD 1 (diag) 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 952 | 162.4 | -691.4 | -299.5 | 853.8 | 0.23 / -0.99 / -0.43 | 587.9 / 157.3 |
| NKD 2 (diag) 30m HM[9, 21, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 918 | 182.9 | -674.0 | -286.2 | 857.0 | 0.25 / -0.89 / -0.39 | 434.0 / -1.8 |
| NKD 3 (diag) 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1957 | 485.6 | -412.3 | 4.8 | 897.8 | 0.92 / -0.76 / 0.01 | 520.2 / 67.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Pair-style ST/HM/WT signals with ATR-trail exits on the Nikkei dollar future in Asia hours do not work: no cell of the 180-cell grid has positive weekly Sharpe in both clean halves with >= 100 trades (best clean Sharpe +0.16, one half positive); the replicate grid passes 0.84 cells on average (p(count) = 1). The three diagnostic cells have clean Sharpe 0.04-0.16 and uplifts within +-0.06 of zero at every span; their sleeves are tiny at equal R (NKD ADR stops are wide relative to the $9,600 R, so positions are small), so uplift cannot be large either way.
- ERA flag for the diagnostic cells: negative pre-2023 (2013-22 net weekly Sharpe -0.76 to -0.99). NKD is thin (many 1-minute rows missing outside the Tokyo session), which makes tf-bar signals noisy; the 1-tick cost is $25 per side per contract.
- Executability: NKD (CME) is available at NinjaTrader Brokerage via Rithmic in principle (not checked); nothing passed so no margin decision.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_l91.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/l91/ (`L91_CO_all_selected_scored.csv`).

DONE L91
