# REPORT Q1B - Q1B: B7 grid on NQ index (NQ)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 10 selected cells (+0 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.27; best pair-window standalone Sharpe +0.92.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: NQ. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| NQ    |     288 |        288 |        65 |               2.009 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| NQ    |     100 |                   65 |            45.25 |              61 |          0 |                       1.501 |            1.301 |           1.516 |     0.06 |       2.009 |                2.285 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ 1 | 10m emax[9, 21] dir=with hold=180m day | 497 | 2 | 2.01 | -0.31 | 0.73 | -0.55 / 1.06 | 0.34 / -0.31 / -0.19 | 0.13 | -0.05 | 0.95 | -0.08 | 1.00 | 774 | NO |
| NQ 2 | 10m emax[9, 21] dir=with hold=120m day | 631 | 2 | 1.98 | -0.52 | 0.66 | -0.62 / 1.29 | 0.37 / -0.00 / -0.42 | 0.13 | 0.15 | 0.94 | -0.08 | 0.83 | 984 | NO |
| NQ 3 | 5m emax[9, 21] dir=with hold=240m day | 503 | 2 | 1.51 | 0.11 | 0.88 | 0.17 / 1.52 | 0.17 / -0.24 / 0.16 | 0.10 | -0.38 | 0.95 | -0.06 | 1.00 | 806 | NO |
| NQ 4 | 10m st[14, 2.0] dir=with hold=180m day | 634 | 2 | 1.50 | 0.13 | 0.71 | 0.09 / 1.54 | 0.25 / -0.17 / 0.11 | 0.16 | 0.08 | 0.91 | -0.06 | 0.67 | 990 | NO |
| NQ 5 | 10m st[14, 2.0] dir=with hold=240m day | 477 | 2 | 1.39 | -0.25 | 0.64 | -0.43 / 1.52 | 0.22 / -0.35 / 0.11 | 0.10 | -0.33 | 0.86 | -0.06 | 0.50 | 756 | NO |
| NQ 6 | 10m emax[9, 21] dir=with hold=120m all | 1780 | 2 | 1.39 | -1.02 | 0.85 | 0.52 / 1.28 | 0.32 / 0.11 / 0.05 | 0.19 | 0.06 | 0.99 | -0.00 | 0.17 | 2833 | NO |
| NQ 7 | 5m macd[12, 26] dir=with hold=240m day | 473 | 2 | 1.38 | 0.08 | 0.78 | 0.04 / 1.04 | 0.17 / -0.20 / 0.05 | 0.08 | -0.30 | 0.90 | -0.08 | 0.67 | 756 | NO |
| NQ 8 | 10m st[14, 2.0] dir=with hold=180m all | 1639 | 2 | 1.32 | -0.02 | 0.92 | 0.66 / 1.23 | 0.26 / 0.34 / 0.18 | 0.23 | -0.05 | 0.99 | 0.04 | 0.67 | 2665 | LEAD(gate3-7 fail: plateau ) |
| NQ 9 | 5m st[14, 2.0] dir=with hold=120m day | 1110 | 2 | 1.28 | 0.24 | 0.44 | -0.54 / 1.50 | 0.21 / -0.17 / -0.17 | 0.05 | 0.15 | 0.85 | -0.15 | 0.67 | 1745 | NO |
| NQ 10 | 5m vwz[2.0, 'globex'] dir=with hold=180m all | 1644 | 2 | 1.25 | 0.10 | 0.10 | -1.02 / 1.39 | 0.30 / -0.64 / -0.23 | 0.01 | 0.03 | 0.63 | -0.18 | 0.50 | 2535 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 1 / 1 / 0 |
| all-in uplift @20% > 0 (all scored) | 10 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 4 |
| worst-decile corr <= +0.30 | 10 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 3 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ 10m st[14, 2.0] dir=with hold=180m all | clean | 1.23 | 2.38 | -97413 | -83628 | 405940 | -122387 | 2.76 | 41.9 | 1.72 | -79154 | 231652 | -87215 |
| NQ 10m st[14, 2.0] dir=with hold=180m all | H1 | 1.39 | 3.21 | -112634 | -100478 | 354688 | -147097 | 1.63 | 57.1 | 3.17 | -56457 | 137949 | -57111 |
| NQ 10m st[14, 2.0] dir=with hold=180m all | H2 | 0.06 | 0.10 | -186600 | -162679 | 595532 | -187615 | 0.05 | 52.8 | 2.48 | -85361 | 215067 | -87516 |
| NQ 10m st[14, 2.0] dir=with hold=180m all | all | 0.92 | 1.69 | -138910 | -111403 | 611360 | -187615 | 2.84 | 47.0 | 2.12 | -80124 | 231652 | -87516 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| NQ 10m st[14, 2.0] dir=with hold=180m all | -10.6 | 16.0 | 24.5 | 46.1 | 15.5 / 26.4 | 20.0 / 37.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| NQ 1 10m emax[9, 21] dir=with hold=180m day | negative pre-2023 | 2624 | -15.3 | -29.6 | -21.1 | 14.4 | -0.16 / -0.31 / -0.22 | 277.0 / 262.7 |
| NQ 2 10m emax[9, 21] dir=with hold=120m day | negative pre-2023 | 3370 | -17.4 | -31.7 | -23.2 | 14.4 | -0.29 / -0.52 / -0.38 | 183.4 / 169.0 |
| NQ 3 5m emax[9, 21] dir=with hold=240m day | positive pre-2023 | 2627 | 25.7 | 11.3 | 19.8 | 14.4 | 0.24 / 0.11 / 0.19 | 288.4 / 274.1 |
| NQ 4 10m st[14, 2.0] dir=with hold=180m day | positive pre-2023 | 3280 | 24.3 | 9.9 | 18.5 | 14.4 | 0.31 / 0.13 / 0.24 | 190.5 / 176.2 |
| NQ 5 10m st[14, 2.0] dir=with hold=240m day | negative pre-2023 | 2503 | -9.6 | -24.0 | -15.4 | 14.4 | -0.10 / -0.25 / -0.16 | 321.3 / 306.9 |
| NQ 6 10m emax[9, 21] dir=with hold=120m all | negative pre-2023 | 9470 | -10.3 | -24.6 | -16.1 | 14.4 | -0.43 / -1.02 / -0.67 | 58.9 / 44.6 |
| NQ 7 5m macd[12, 26] dir=with hold=240m day | positive pre-2023 | 2440 | 22.3 | 7.9 | 16.5 | 14.4 | 0.22 / 0.08 / 0.16 | 273.4 / 259.0 |
| NQ 8 10m st[14, 2.0] dir=with hold=180m all | gross-positive, cost-negative pre-2023 | 8693 | 13.7 | -0.6 | 7.9 | 14.4 | 0.39 / -0.02 / 0.23 | 94.9 / 80.5 |
| NQ 9 5m st[14, 2.0] dir=with hold=120m day | positive pre-2023 | 5828 | 25.6 | 11.2 | 19.8 | 14.4 | 0.54 / 0.24 / 0.42 | 111.8 / 97.4 |
| NQ 10 5m vwz[2.0, 'globex'] dir=with hold=180m all | positive pre-2023 | 8110 | 17.7 | 3.3 | 11.9 | 14.4 | 0.55 / 0.10 / 0.37 | 71.5 / 57.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- **NQ with-trend ST flip held three hours (Q1B cell NQ 8): 10-minute Supertrend(14, 2.0) flip, traded WITH the flip, held 180 minutes, no stop, all-hours entries (18:00-15:00 ET, full hold before 16:55).** Clean weekly Sharpe 1.23, H1 1.39, H2 0.06 standalone; additive uplift at 20% share +0.26 / +0.34 / +0.18 (10%: +0.14/+0.23/+0.12; 30%: +0.37/+0.35/+0.18; 50% +0.52/+0.20/0.00), worst week +6.0% at 20%, bootstrap 90% lower bound +0.04, out-of-selection (H1+H2) standalone Sharpe 0.66 against its own null p95 1.23 (fails that sub-gate; the pair-window all-in null passes), 2x-slippage all-in uplift +0.23, worst-decile correlation -0.05. **Plateau 0.67 (needs 0.75): fails.** Replication: 1 of 4 holds (H0 2023-02..07 standalone Sharpe +1.75 on 398 trades); ES cross-instrument +0.11, RTY +0.02 (RTY below 50% of the uplift); alternating months odd +0.09, even +0.35 against +0.27 (odd half 33%: fails). ERA flag 'gross-positive, cost-negative pre-2023' (2013-22 weekly Sharpe gross +0.39 / net -0.02 / price-scaled +0.23). Contracts: about 8.5 NQ at 100% pair volatility, 1.7 NQ at 20% share; worst single trade -$11.2k per NQ contract (about -$19k at 1.7 contracts). It trades NQ, so it would net against the pair's lots and needs a separate account (library netting class NQ_INTRADAY). Mechanism in one sentence: a ten-minute trend flip on NQ continues for roughly three hours more often than not at the current price level (relative cost about eight times lower than in 2013-22); it plausibly depends on the current structure and is the same trade type as the live ST book, which explains the high sleeve alignment with the pair's trend regimes (worst-decile correlation nonetheless -0.05). LEAD: fails plateau and replication; the clean rule is strongly met by the family (65 cells pass, replicates 45) but p(count) = 0.00 and p(top) = 0.06.
- Other NQ cells in the grid: only this one has +0.10 on all three spans at 20% (1 of 10 selected); bootstrap lower bound > 0 for 1 cell.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q1b.py (= ap_b7.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q1b/ (`Q1B_CO_all_selected_scored.csv`).

DONE Q1B
