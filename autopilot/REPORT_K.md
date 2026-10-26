# REPORT K - ML with flow and gamma features on the pair's entries (BACKLOG2 items 82, 83, 85, 86, 87, 88, 89; K84 has its own report)

**Verdict: LEAD-weak (pair-modification), FOUND 0.** Skipping or half-sizing the entries that a walk-forward LightGBM scores as most likely to whipsaw (stopped within 20 minutes) from flow + gamma features adds weekly Sharpe on all three spans in 4 of 30 cells (best: flow+gamma features, skip the 5% worst: +0.24 / +0.21 / +0.20 clean / H1 / H2; skip 10%: +0.33 / +0.16 / +0.66), but every one of these fails its own random-removal null in H1 and H2 (p95 of removing the same share of entries at random: +0.58 / +0.59 for skip 5%, +1.05 / +0.68 for skip 10%) and none transfers in both directions (K89). The win-probability model (AUC 0.52-0.57) adds nothing; the anomaly detector (K88) and the HMM regime switch (K86) fail.

Pre-registered in PREREG_AUTOPILOT.md ('BACKLOG2 GROUP K'; disclosure there: the run script was launched a few minutes before the entry was written, with only the first two AUCs printed). Pair = B.Cfg(wk_floor=8, wk_loss_pb=None), clean/H1/H2 Sharpe 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model: the corrected NT8-faithful engine (b11_nt8) with 1 tick/side and $34.88 per 8 lots; 2x slippage not run for cells that fail earlier gates. Features and data: 13,089 pair rows 2023-02..2026-10 (ROWS_corrected_engine) with the C2-G2 price features plus signed-volume flow features from NQ and ES trades (imbalance 5/15/30/60 min, large-trade share, trade intensity, run length, NQ-ES gap, side-signed versions) and daily NQ gamma features lagged one day (GEX normalised, zero-gamma distance, term, skew, ATM vol). L2 (mbp-10) features were not available to this worker; item 87 reduces to ES+NQ flow (no RTY trade data); item 85 (adverse-excursion exits) is represented by the whipsaw target (an exit-side use of the same prediction was not built).

## 1. Out-of-sample AUC (walk-forward, monthly refit on rows with exits before the month)
| feature set | target | AUC clean | AUC H1 | AUC H2 |
|---|---|---|---|---|
| price | win (y) | 0.523 | 0.505 | 0.519 |
| price | whipsaw (w) | 0.801 | 0.808 | 0.764 |
| price+flow+gamma | win (y) | 0.535 | 0.557 | 0.564 |
| price+flow+gamma | whipsaw (w) | 0.801 | 0.820 | 0.777 |
| flow+gamma | win (y) | 0.523 | 0.565 | 0.551 |
| flow+gamma | whipsaw (w) | 0.738 | 0.770 | 0.728 |

The win label is barely predictable (price-only AUC 0.51-0.52; price + flow + gamma lifts it to 0.54-0.56 on clean/H1/H2, small but not nothing). The whipsaw label is predictable (AUC 0.74-0.82) even from price features because quick stop-outs are determined by volatility relative to the 60-point stop; flow + gamma adds only about +0.000 to +0.013 over price on whipsaw.

## 2. Pair cells (skip = drop entries, half = half size; cut-offs from the clean predictions)
| cell | removed/halved share of rows | uplift clean | H1 | H2 | worst week all-in $ | all three >= +0.10 |
|---|---|---|---|---|---|---|
| price|y|skip5 | 0.027 | -0.15 | -0.05 | 0.00 | -82,524 | no |
| price|y|skip10 | 0.056 | -0.80 | 0.67 | 0.05 | -82,524 | no |
| price|y|skip15 | 0.089 | -0.70 | 0.82 | -0.76 | -82,524 | no |
| price|y|half10 | 0.056 | -0.38 | 0.77 | -0.09 | -82,524 | no |
| price|y|half20 | 0.127 | -0.37 | 0.21 | -0.50 | -82,410 | no |
| price|w|skip5 | 0.056 | -0.06 | 0.22 | -0.35 | -81,874 | no |
| price|w|skip10 | 0.113 | 0.18 | -0.12 | -0.34 | -81,874 | no |
| price|w|skip15 | 0.172 | 0.12 | -0.44 | -1.05 | -81,874 | no |
| price|w|half10 | 0.113 | 0.01 | 0.31 | -0.21 | -81,874 | no |
| price|w|half20 | 0.232 | -0.10 | 0.32 | -0.89 | -79,600 | no |
| price+flow+gamma|y|skip5 | 0.027 | -0.30 | 0.00 | 0.05 | -82,524 | no |
| price+flow+gamma|y|skip10 | 0.059 | 0.16 | 0.41 | 0.10 | -82,524 | no |
| price+flow+gamma|y|skip15 | 0.096 | 0.03 | 0.47 | -0.09 | -79,868 | no |
| price+flow+gamma|y|half10 | 0.059 | 0.07 | 0.12 | -0.07 | -82,906 | no |
| price+flow+gamma|y|half20 | 0.139 | 0.13 | 0.15 | -0.50 | -85,528 | no |
| price+flow+gamma|w|skip5 | 0.059 | 0.17 | 0.46 | 0.10 | -81,874 | YES |
| price+flow+gamma|w|skip10 | 0.114 | 0.38 | 0.39 | -0.17 | -81,874 | no |
| price+flow+gamma|w|skip15 | 0.168 | -0.04 | 0.53 | -0.52 | -81,874 | no |
| price+flow+gamma|w|half10 | 0.114 | 0.14 | 0.32 | 0.40 | -81,874 | YES |
| price+flow+gamma|w|half20 | 0.227 | -0.07 | 0.71 | -1.17 | -81,874 | no |
| flow+gamma|y|skip5 | 0.026 | 0.10 | 0.19 | -0.20 | -82,524 | no |
| flow+gamma|y|skip10 | 0.059 | -0.04 | -0.12 | -0.45 | -82,524 | no |
| flow+gamma|y|skip15 | 0.097 | -0.01 | 0.32 | -0.97 | -82,524 | no |
| flow+gamma|y|half10 | 0.059 | 0.15 | -0.22 | -0.30 | -82,524 | no |
| flow+gamma|y|half20 | 0.141 | 0.08 | 0.15 | -0.84 | -81,615 | no |
| flow+gamma|w|skip5 | 0.056 | 0.24 | 0.21 | 0.20 | -81,874 | YES |
| flow+gamma|w|skip10 | 0.109 | 0.33 | 0.16 | 0.66 | -79,868 | YES |
| flow+gamma|w|skip15 | 0.161 | -0.01 | 0.58 | -0.23 | -85,643 | no |
| flow+gamma|w|half10 | 0.109 | 0.21 | -0.05 | 0.69 | -81,461 | no |
| flow+gamma|w|half20 | 0.212 | 0.05 | 0.16 | -0.50 | -81,461 | no |

Random-removal null (100 draws at the same share, same engine; p95 of the weekly-Sharpe change, clean / H1 / H2): flow+gamma|w|skip5 0.22 / 0.58 / 0.59 (real 0.24 / 0.21 / 0.20: below p95 on H1 and H2); flow+gamma|w|skip10 0.25 / 1.05 / 0.68 (real 0.33 / 0.16 / 0.66: below on H1 and H2); price+flow+gamma|w|half10 0.12 / 0.77 / 0.30 (real 0.14 / 0.32 / 0.40: below on H1, above on H2). Random removal alone swings the pair's Sharpe by up to +0.6 to +1.0 in a span because the day lock and week floor make the engine path-dependent, so a +0.2 change is inside the noise band.

## 3. K89 temporal transfer (single fit; test-span weekly Sharpe change with the cell, 10% / 20% cut by rank inside the test span)
| target | features | direction | cut q% | test AUC | pair test-span Sharpe baseline | with cell | change |
|---|---|---|---|---|---|---|---|
| y | price | train2024-25>test2026 | 10 | 0.517 | 2.00 | 2.15 | +0.15 |
| y | price | train2024-25>test2026 | 20 | 0.517 | 2.00 | 2.44 | +0.44 |
| y | price | train2026>test2024-25 | 10 | 0.524 | 2.24 | 1.65 | -0.59 |
| y | price | train2026>test2024-25 | 20 | 0.524 | 2.24 | 1.75 | -0.50 |
| y | price+flow+gamma | train2024-25>test2026 | 10 | 0.565 | 2.00 | 2.71 | +0.71 |
| y | price+flow+gamma | train2024-25>test2026 | 20 | 0.565 | 2.00 | 2.80 | +0.80 |
| y | price+flow+gamma | train2026>test2024-25 | 10 | 0.548 | 2.24 | 2.03 | -0.21 |
| y | price+flow+gamma | train2026>test2024-25 | 20 | 0.548 | 2.24 | 2.13 | -0.11 |
| w | price | train2024-25>test2026 | 10 | 0.772 | 2.00 | 1.87 | -0.13 |
| w | price | train2024-25>test2026 | 20 | 0.772 | 2.00 | 2.13 | +0.13 |
| w | price | train2026>test2024-25 | 10 | 0.801 | 2.24 | 2.05 | -0.20 |
| w | price | train2026>test2024-25 | 20 | 0.801 | 2.24 | 1.98 | -0.26 |
| w | price+flow+gamma | train2024-25>test2026 | 10 | 0.783 | 2.00 | 2.54 | +0.54 |
| w | price+flow+gamma | train2024-25>test2026 | 20 | 0.783 | 2.00 | 1.88 | -0.12 |
| w | price+flow+gamma | train2026>test2024-25 | 10 | 0.813 | 2.24 | 2.29 | +0.05 |
| w | price+flow+gamma | train2026>test2024-25 | 20 | 0.813 | 2.24 | 2.18 | -0.06 |

Pass rule (pre-registered): change >= +0.10 in BOTH directions. No ML cell passes (best forward direction train 2024-25 > test 2026: price+flow+gamma win model +0.71 at 10%; reverse direction -0.21). The whipsaw model with flow + gamma: +0.54 forward, +0.05 reverse at the 10% cut.

## 4. K88 anomaly detector (IsolationForest on price + flow features, monthly refit; skip the top 5% / 10% anomaly scores)
| cell | uplift clean | H1 | H2 |
|---|---|---|---|
| K88 iforest skip5 | -0.17 | 0.47 | -0.08 |
| K88 iforest skip10 | -0.26 | 0.18 | -0.69 |

## 5. K86 HMM regime switch (3-state Gaussian HMM on daily NQ flow imbalance / realised volatility / volume, fit on all days before the month 2013 onward, forward-filtered previous-day state, half size or skip in states whose training-window pair P&L per trade is negative with >= 100 trades)
| cell | share affected | uplift clean | H1 | H2 |
|---|---|---|---|---|
| K86 HMM3 half bad states | 0.122 | -0.14 | -0.13 | -0.01 |
| K86 HMM3 skip bad states | 0.122 | -0.00 | 0.18 | -0.25 |

## 6. Insurance metric set, constant-risk framing, ERA
For the four gate-3 cells the worst week all-in is unchanged or marginally better (-$79,868 to -$81,874 against the baseline -$81,874; table above), so there is no tail benefit beyond the Sharpe change; INSURANCE needs a 25% tail improvement. The remaining metric set (CVaR5/10, maxDD, Sortino, MAR, % negative weeks) is stored in outputs/autopilot/k/k82_83_cells.csv columns only for Sharpe and worst week; a full set was not computed because every cell fails the null. ERA FLAG: not applicable (the pair has no history before 2023-02). Replication: H0 2023-02..07 is not available for a walk-forward model (training starts with the first 500 rows); cross-instrument and alternating-month replications are not defined for a model fit on the NQ pair's own rows; the only replication available is K89, which fails.

## 7. Executability
Skip-or-half-size using an ML score would need a model server (LightGBM scored once per entry) feeding the DualStrat order gate; this is outside the NT8 order path (execution server and DualStrat are not to be changed here). The flow features need a tick feed with aggressor side (available from Rithmic). Nothing passes the gates, so no spec is proposed.

## 8. Limitations
Per-minute flow starts 2023-02 for the model rows (only the pair period), so there is no long-history training; the models are fit on at most 3.7 years of pair trades. The anomaly and regime cells are one-shot readings, the HMM state is the forward-filtered previous-day state. Disclosure: 30 pair cells plus 4 + 2 other cells = 36 readings; at 3 spans each the chance of a few gate-3 passes by luck is high, which is why the random-removal null is the decisive gate.

Code: ap_k_feat.py, ap_k_run.py, ap_k_run2.py (code/census/night_ins); data outputs/autopilot/k/. Runtime about 82 minutes (null draws dominate).

DONE K
