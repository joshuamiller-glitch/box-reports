# REPORT Q22 - Q22: cross-market dislocation convergence (synthetic dollar-neutral spreads, Bollinger cross-out, time exit)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+3 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe -4.69.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: SPR_ZN_ZB, SPR_ZN_ES, SPR_ZB_ES, SPR_GC_SI, SPR_CL_HO, SPR_HO_RB, SPR_6E_6B, SPR_ZN_6E. Grid: 96 cells per pair
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym       |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:----------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| SPR_6E_6B |      96 |          0 |         0 |              -9     |                0 |          0 |            0 |
| SPR_CL_HO |      96 |          0 |         0 |              -9     |                0 |          0 |            0 |
| SPR_GC_SI |      96 |          0 |         0 |              -9     |                0 |          0 |            0 |
| SPR_HO_RB |      96 |          0 |         0 |              -9     |                0 |          0 |            0 |
| SPR_ZB_ES |      96 |          0 |         0 |              -9     |                0 |          0 |            0 |
| SPR_ZN_6E |      96 |          0 |         0 |              -9     |                0 |          0 |            0 |
| SPR_ZN_ES |      96 |          0 |         0 |              -9     |                0 |          0 |            0 |
| SPR_ZN_ZB |      96 |         94 |         0 |              -4.996 |                0 |          0 |            3 |

| sym       |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:----------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| SPR_ZN_ZB |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| SPR_ZN_ES |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| SPR_ZB_ES |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| SPR_GC_SI |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| SPR_CL_HO |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| SPR_HO_RB |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| SPR_6E_6B |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| SPR_ZN_6E |     200 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SPR_ZN_ZB 1 (diag) | 15m boll(480,2.5) dir=with hold 240m day | 90 | 0 | -5.00 | -3.57 | -4.69 | -4.21 / -6.75 | -1.00 / -1.30 / -0.68 | -1.26 | -0.11 | 1.00 | -1.23 | 0.00 | 154 | diag |
| SPR_ZN_ZB 2 (diag) | 15m boll(480,2.5) dir=against hold 240m day | 90 | 0 | -5.16 | -3.22 | -4.90 | -4.84 / -6.69 | -1.05 / -1.43 / -1.62 | -1.46 | 0.32 | 1.00 | -1.49 | 0.00 | 154 | diag |
| SPR_ZN_ZB 3 (diag) | 15m boll(480,2.5) dir=against hold 180m day | 109 | 0 | -5.18 | -3.59 | -5.13 | -5.10 / -8.20 | -1.05 / -1.40 / -1.15 | -1.40 | -0.13 | 1.00 | -1.38 | 0.00 | 185 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 3 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 0 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 3 |
| worst-decile corr <= +0.30 | 2 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SPR_ZN_ZB 15m boll(480,2.5) dir=with hold 240m day (diag) | clean | -4.96 | -4.12 | -188346 | -173355 | 4531401 | -198176 | -0.99 | 47.6 | 0.46 | -92460 | 351703 | -110620 |
| SPR_ZN_ZB 15m boll(480,2.5) dir=with hold 240m day (diag) | H1 | -6.05 | -4.73 | -206802 | -176243 | 1477345 | -217899 | -1.00 | 60.7 | 1.53 | -77610 | 180262 | -78287 |
| SPR_ZN_ZB 15m boll(480,2.5) dir=with hold 240m day (diag) | H2 | -3.05 | -3.29 | -192849 | -157287 | 1131161 | -211003 | -1.00 | 58.3 | 1.80 | -92818 | 201664 | -98565 |
| SPR_ZN_ZB 15m boll(480,2.5) dir=with hold 240m day (diag) | all | -4.69 | -4.07 | -194965 | -175163 | 7116440 | -217899 | -1.00 | 52.4 | 0.91 | -90965 | 351703 | -110620 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| SPR_ZN_ZB 15m boll(480,2.5) dir=with hold 240m day (diag) | -107.8 | -26.2 | -2.5 | -120.2 | -27.2 / -7.4 | 23.0 / 25.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| SPR_ZN_ZB 1 (diag) 15m boll(480,2.5) dir=with hold 240m day | negative pre-2023 | 430 | -6.8 | -75.0 | -75.0 | 68.1 | -0.39 / -3.57 / -3.57 | -3.4 / -71.5 |
| SPR_ZN_ZB 2 (diag) 15m boll(480,2.5) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 430 | 6.8 | -61.3 | -61.3 | 68.1 | 0.39 / -3.22 / -3.22 | 3.4 / -64.8 |
| SPR_ZN_ZB 3 (diag) 15m boll(480,2.5) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 541 | 9.4 | -58.7 | -58.7 | 68.1 | 0.67 / -3.59 / -3.59 | 6.1 / -62.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): SPR_6E_6B: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); SPR_CL_HO: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); SPR_GC_SI: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); SPR_HO_RB: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); SPR_ZB_ES: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); SPR_ZN_6E: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); SPR_ZN_ES: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); SPR_ZN_ZB: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

- Note: Synthetic spread instruments: costs are 1 tick per side per leg plus $4.36 per contract per leg; worst-trade and sizing figures are in spread dollars per 1 A-leg contract.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q22.py (ap_q_sig.py boll on synthetic spreads), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q22/ (`Q22_CO_all_selected_scored.csv`).

DONE Q22
