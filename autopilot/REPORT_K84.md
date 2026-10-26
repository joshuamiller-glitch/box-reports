# REPORT K84 - K84 walk-forward GBM direction sleeve (price vs price+flow features) on NQ and ES, 15/30/60-minute time exits

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 1 selected cells (+6 diagnostic) scored on 2 instruments; best non-diagnostic all-in additive uplift at 20% share -0.09; best pair-window standalone Sharpe +0.17.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Model: LightGBM walk-forward (quarterly refit, expanding window from 2013, OOS predictions from 2018-01) classifying the sign of the next 15/30/60-minute return from 15-minute bar features, with or without NQ/ES signed-volume flow features. Entry when p > 0.5+delta (long) or p < 0.5-delta (short), time exit, no stop.
- Instruments: NQ, ES. Grid: 18 cells per instrument = 2 feature sets x 3 horizons x 3 thresholds (0.02, 0.04, 0.06).
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      18 |         18 |         0 |              -0.776 |                0 |          0 |            3 |
| NQ    |      18 |         18 |         1 |               0.725 |                2 |          1 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| NQ    |     200 |                    1 |            0.945 |               4 |       0.65 |                       0.725 |            0.649 |           1.312 |    0.235 |       0.725 |                1.531 |
| ES    |     200 |                    0 |            0.005 |               1 |       1    |                     nan     |            0.105 |           0.105 |  nan     |     nan     |                0.105 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ 1 | NQ GBM price+flow h=60m delta=0.04 | 1720 | 2 | 0.73 | -0.04 | -0.04 | -0.87 / 0.93 | 0.06 / -0.63 / -0.14 | -0.16 | 0.04 | 0.86 | -0.31 | 0.00 | 2764 | NO |
| NQ 2 (diag) | NQ GBM price h=30m delta=0.04 | 2394 | 1 | 0.09 | -0.77 | -0.64 | -1.85 / 0.84 | -0.05 / -0.12 / -0.64 | -0.28 | -0.19 | 0.57 | -0.37 | 0.00 | 3805 | diag |
| NQ 3 (diag) | NQ GBM price+flow h=15m delta=0.06 | 559 | 1 | -0.05 | -1.16 | 0.17 | 0.37 / 1.20 | -0.08 / 0.06 / 0.21 | -0.16 | 0.34 | 0.86 | -0.22 | 0.00 | 760 | diag |
| NQ 4 (diag) | NQ GBM price h=60m delta=0.06 | 223 | 1 | -0.19 | 0.13 | -0.90 | -1.93 / 1.43 | -0.11 / -0.68 / -0.38 | -0.28 | -0.07 | 0.05 | -0.46 | 0.00 | 327 | diag |
| ES 1 (diag) | ES GBM price h=60m delta=0.06 | 574 | 0 | -0.78 | -1.09 | -1.14 | -1.99 / -0.11 | -0.15 / -0.15 / -0.36 | -0.36 | 0.01 | 0.80 | -0.37 | 0.00 | 769 | diag |
| ES 2 (diag) | ES GBM price+flow h=60m delta=0.06 | 391 | 0 | -0.97 | -1.42 | -1.26 | -1.82 / 0.03 | -0.18 / -0.71 / -0.01 | -0.40 | 0.11 | 0.47 | -0.40 | 0.00 | 502 | diag |
| ES 3 (diag) | ES GBM price h=60m delta=0.04 | 2290 | 0 | -1.91 | -1.82 | -1.91 | -2.01 / -0.85 | -0.39 / -0.40 / -0.22 | -0.61 | -0.09 | 0.75 | -0.51 | 0.00 | 3280 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 1 |
| diagnostic cells read | 6 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 0 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 0 |
| worst-decile corr <= +0.30 | 6 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES ES GBM price h=60m delta=0.06 (diag) | clean | -0.82 | -1.22 | -129990 | -102223 | 971363 | -220874 | -0.76 | 63.8 | 1.31 | -86234 | 256255 | -96339 |
| ES ES GBM price h=60m delta=0.06 (diag) | H1 | -2.18 | -2.59 | -38642 | -34336 | 196519 | -47827 | -0.77 | 64.3 | 2.68 | -79557 | 147801 | -82181 |
| ES ES GBM price h=60m delta=0.06 (diag) | H2 | -2.21 | -2.29 | -181656 | -132562 | 603029 | -221112 | -0.97 | 55.6 | 1.94 | -101510 | 208628 | -123876 |
| ES ES GBM price h=60m delta=0.06 (diag) | all | -1.14 | -1.54 | -139388 | -103853 | 1502314 | -221112 | -0.98 | 62.5 | 1.66 | -89179 | 256255 | -123876 |
| NQ NQ GBM price+flow h=60m delta=0.04 | clean | 0.71 | 1.08 | -134089 | -108257 | 336171 | -171284 | 1.93 | 42.9 | 1.52 | -83885 | 284814 | -90098 |
| NQ NQ GBM price+flow h=60m delta=0.04 | H1 | -2.06 | -2.26 | -219988 | -206002 | 876951 | -259969 | -0.77 | 57.1 | 2.19 | -79506 | 164315 | -82411 |
| NQ NQ GBM price+flow h=60m delta=0.04 | H2 | -0.08 | -0.12 | -201516 | -165876 | 485754 | -217655 | -0.08 | 50.0 | 2.15 | -98860 | 236831 | -103133 |
| NQ NQ GBM price+flow h=60m delta=0.04 | all | -0.04 | -0.05 | -179484 | -147072 | 1159724 | -259969 | -0.06 | 46.4 | 1.77 | -87049 | 284814 | -103133 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| NQ NQ GBM price+flow h=60m delta=0.04 | -30.8 | -12.7 | 7.7 | 18.3 | -7.4 / 13.0 | 7.9 / 14.3 | NO |
| ES ES GBM price h=60m delta=0.06 (diag) | -46.5 | -47.9 | 6.5 | 22.5 | -25.5 / 9.9 | 22.5 / 26.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| NQ 1 NQ GBM price+flow h=60m delta=0.04 | gross-positive, cost-negative pre-2023 | 7062 | 13.3 | -1.1 | 5.4 | 14.4 | 0.53 / -0.04 / 0.22 | 33.8 / 19.4 |
| NQ 2 (diag) NQ GBM price h=30m delta=0.04 | gross-positive, cost-negative pre-2023 | 10049 | 4.0 | -10.4 | -3.7 | 14.4 | 0.29 / -0.77 / -0.28 | 15.4 / 1.1 |
| NQ 3 (diag) NQ GBM price+flow h=15m delta=0.06 | gross-positive, cost-negative pre-2023 | 2366 | 2.4 | -12.0 | -4.6 | 14.4 | 0.26 / -1.16 / -0.44 | 14.5 / 0.1 |
| NQ 4 (diag) NQ GBM price h=60m delta=0.06 | positive pre-2023 | 1406 | 23.1 | 8.8 | 15.6 | 14.4 | 0.34 / 0.13 / 0.23 | -1.8 / -16.2 |
| ES 1 (diag) ES GBM price h=60m delta=0.06 | gross-positive, cost-negative pre-2023 | 3524 | 7.8 | -21.6 | -9.9 | 29.4 | 0.41 / -1.09 / -0.51 | 8.9 / -20.5 |
| ES 2 (diag) ES GBM price+flow h=60m delta=0.06 | gross-positive, cost-negative pre-2023 | 2108 | 4.2 | -25.2 | -13.0 | 29.4 | 0.25 / -1.42 / -0.76 | 8.0 / -21.4 |
| ES 3 (diag) ES GBM price h=60m delta=0.04 | gross-positive, cost-negative pre-2023 | 9350 | 3.7 | -25.6 | -14.8 | 29.4 | 0.28 / -1.82 / -1.08 | -2.9 / -32.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- The direction model has essentially no out-of-sample skill: AUC for the sign of the next 15/30/60-minute return is 0.517-0.527 over 2018-2022 and 0.512-0.518 on clean for NQ and ES, with or without flow features (flow adds about +0.002 to +0.005 AUC). Price+flow is not better than price only in a way that trading can use.
- Under the clean-only rule only one NQ cell qualifies (price+flow, 60 minutes, delta 0.04: clean Sharpe 0.73, replicates pass 0.95 cells on average, p(count) = 0.65) and ES has none (best clean Sharpe -0.78). The NQ cell loses in H1 and H2 (uplift +0.06 / -0.63 / -0.14, OOS standalone Sharpe -0.87, 2x-slip all-in -0.16). Diagnostic cells (best failing) are also negative.
- ERA flag for the NQ cell: negative pre-2023 type (2018-2022 OOS weekly Sharpe -0.04 on a span that includes zero-P&L weeks before predictions start in 2018; treat as indicative). K89 (frozen-model transfer variant) was not run: with an OOS AUC of 0.52 there is no skill to transfer, and the walk-forward predictions are themselves out-of-sample in time (clean -> H1/H2). L2 (mbp-10) features and options features were not included in this model; the pair-trade models (K82/K83) include gamma features.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_k84.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/k84/ (`K84_CO_all_selected_scored.csv`).

DONE K84
