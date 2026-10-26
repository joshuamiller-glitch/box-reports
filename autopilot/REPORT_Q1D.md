# REPORT Q1D - Q1D: B11 grid on NQ index (NQ)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 10 selected cells (+0 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.19; best pair-window standalone Sharpe +1.47.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Levels: opening range of the first 15/30/60 min of the instrument RTH (ES/RTY 09:30, GC/ZN 08:20, CL 09:00 ET) or the prior trading day's high/low. First tf-bar close beyond a level per day, trade with (breakout) or against (fade); stop a x ADR20, bracket 1R/2R target, trail, or hold to flat.
- Instruments: NQ. Grid: 192 cells per instrument = 4 levels x 2 bar sizes x 2 modes x 12 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| NQ    |     192 |        192 |        59 |               1.938 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| NQ    |     100 |                   59 |            37.43 |              55 |          0 |                       1.445 |            1.225 |           1.418 |     0.03 |       1.938 |                2.309 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ 1 | OR15 5m with exit=b10.3xADR | 515 | 2 | 1.94 | -0.06 | 0.77 | -0.54 / 1.33 | 0.33 / -0.15 / -0.58 | 0.03 | -0.13 | 0.93 | -0.16 | 0.25 | 824 | NO |
| NQ 2 | OR15 5m with exit=b20.3xADR | 515 | 2 | 1.83 | 0.37 | 0.24 | -1.24 / 1.67 | 0.28 / -0.08 / -1.06 | -0.11 | -0.04 | 0.77 | -0.32 | 0.00 | 824 | NO |
| NQ 3 | OR15 5m with exit=hd0.3xADR | 515 | 2 | 1.68 | 0.47 | 0.14 | -1.39 / 0.97 | 0.27 / -0.38 / -1.01 | -0.14 | -0.04 | 0.72 | -0.34 | 0.00 | 824 | NO |
| NQ 4 | OR15 15m with exit=b10.3xADR | 512 | 2 | 1.42 | 0.29 | 1.12 | 0.80 / 1.14 | 0.18 / 0.51 / -0.19 | 0.13 | -0.12 | 0.98 | -0.05 | 0.00 | 817 | NO |
| NQ 5 | OR15 15m with exit=b20.3xADR | 512 | 2 | 1.37 | 0.57 | 0.67 | -0.05 / 1.02 | 0.17 / 0.20 / -0.40 | 0.03 | -0.14 | 0.92 | -0.17 | 0.25 | 817 | NO |
| NQ 6 | OR15 15m with exit=b20.1xADR | 512 | 2 | 1.37 | 0.19 | 0.85 | 0.17 / 1.01 | 0.22 / 0.17 / -0.21 | 0.09 | -0.44 | 0.99 | -0.07 | 0.25 | 817 | NO |
| NQ 7 | OR15 15m with exit=hd0.3xADR | 512 | 2 | 1.26 | 0.57 | 0.39 | -0.71 / 1.01 | 0.15 / -0.10 / -0.47 | -0.04 | -0.11 | 0.85 | -0.20 | 0.00 | 817 | NO |
| NQ 8 | OR15 5m with exit=b10.1xADR | 515 | 2 | 1.25 | -0.53 | 0.03 | -1.20 / 1.45 | 0.22 / -0.22 / -0.98 | -0.16 | 0.27 | 0.70 | -0.36 | 0.00 | 824 | NO |
| NQ 9 | OR30 15m with exit=hd0.3xADR | 498 | 2 | 1.19 | 0.47 | 0.40 | -0.52 / 1.20 | 0.12 / -0.21 / -0.43 | -0.06 | 0.00 | 0.84 | -0.23 | 0.00 | 790 | NO |
| NQ 10 | PD 5m with exit=b10.1xADR | 396 | 2 | 1.14 | -0.54 | 1.47 | 1.93 / 1.31 | 0.11 / 0.15 / 0.46 | 0.16 | 0.06 | 1.00 | 0.00 | 0.00 | 632 | LEAD |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 5 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 3 |
| worst-decile corr <= +0.30 | 10 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ PD 5m with exit=b10.1xADR | clean | 1.13 | 2.19 | -95240 | -84067 | 342087 | -106771 | 2.99 | 52.4 | 1.57 | -88187 | 317395 | -95375 |
| NQ PD 5m with exit=b10.1xADR | H1 | 0.89 | 1.15 | -139235 | -112892 | 266333 | -197019 | 0.74 | 32.1 | 2.97 | -72047 | 188725 | -72573 |
| NQ PD 5m with exit=b10.1xADR | H2 | 2.50 | 4.89 | -148400 | -117440 | 322997 | -195149 | 3.78 | 41.7 | 2.75 | -105357 | 228661 | -118683 |
| NQ PD 5m with exit=b10.1xADR | all | 1.47 | 2.70 | -119038 | -98752 | 342087 | -197019 | 7.13 | 46.4 | 2.04 | -91730 | 317395 | -118683 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| NQ PD 5m with exit=b10.1xADR | -2.7 | -38.5 | 4.8 | 10.0 | 0.5 / 11.7 | 30.2 / 34.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| NQ 1 OR15 5m with exit=b10.3xADR | gross-positive, cost-negative pre-2023 | 2676 | 8.6 | -3.7 | 3.7 | 12.3 | 0.17 / -0.06 / 0.07 | 224.9 / 212.8 |
| NQ 2 OR15 5m with exit=b20.3xADR | positive pre-2023 | 2676 | 37.7 | 24.3 | 32.3 | 13.5 | 0.57 / 0.37 / 0.49 | 258.9 / 245.5 |
| NQ 3 OR15 5m with exit=hd0.3xADR | positive pre-2023 | 2676 | 47.7 | 33.4 | 41.9 | 14.4 | 0.66 / 0.47 / 0.58 | 265.2 / 250.8 |
| NQ 4 OR15 15m with exit=b10.3xADR | positive pre-2023 | 2654 | 27.8 | 15.4 | 22.8 | 12.3 | 0.51 / 0.29 / 0.42 | 163.9 / 151.7 |
| NQ 5 OR15 15m with exit=b20.3xADR | positive pre-2023 | 2654 | 52.4 | 38.9 | 46.9 | 13.5 | 0.77 / 0.57 / 0.69 | 200.4 / 186.7 |
| NQ 6 OR15 15m with exit=b20.1xADR | positive pre-2023 | 2654 | 18.6 | 5.9 | 13.5 | 12.7 | 0.58 / 0.19 / 0.42 | 94.2 / 81.6 |
| NQ 7 OR15 15m with exit=hd0.3xADR | positive pre-2023 | 2654 | 56.7 | 42.4 | 50.9 | 14.4 | 0.76 / 0.57 / 0.69 | 226.4 / 212.0 |
| NQ 8 OR15 5m with exit=b10.1xADR | negative pre-2023 | 2676 | -1.0 | -12.9 | -5.8 | 11.9 | -0.04 / -0.53 / -0.23 | 61.4 / 49.7 |
| NQ 9 OR30 15m with exit=hd0.3xADR | positive pre-2023 | 2567 | 52.4 | 38.0 | 46.6 | 14.4 | 0.65 / 0.47 / 0.58 | 193.5 / 179.1 |
| NQ 10 PD 5m with exit=b10.1xADR | negative pre-2023 | 2031 | -2.8 | -14.7 | -7.6 | 11.8 | -0.10 / -0.54 / -0.28 | 70.1 / 58.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- NQ opening-range / prior-day-level books: 59 cells pass the clean rule (replicates 37; p(count) = 0.00, p(top) = 0.03). The only gate-3 cell is NQ 10 (prior-day high/low break, WITH, 5-minute, stop 0.1 x ADR20 and 1R target): +0.11 / +0.15 / +0.46 at 20% share, bootstrap lower bound +0.00, plateau 0.00, standalone Sharpe 1.13 / 0.89 / 2.50, ERA 'negative pre-2023', worst week +43.8% at 20% (fails the share allowance), replication 1 of 4 (H0 +0.81 on 94 trades; ES -0.23, RTY -0.06; alternating months odd +0.04, even +0.32). A weak LEAD at gate 3 only; it is the NQ prior-day-break family already on the CANDIDATES list (T4 D, D2), now re-seen under clean-only selection with a hard stop.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q1d.py (= ap_b11.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q1d/ (`Q1D_CO_all_selected_scored.csv`).

DONE Q1D
