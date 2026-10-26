# REPORT RY7 - family-wise accounting for the K4 family: deflated Sharpe and probability of backtest overfitting (pre-registered, PREREG_AUTOPILOT.md BATCH RY)

Trials: 145 distinct ES/NQ/RTY/YM GBM-derived sleeve cells over the 167 pair-window weeks (2023-W31..2026-W41), weekly P&L (unit-risk, costs included) per cell: K4v2grid 32, RW12Pgrid 32, RW2 8, RW3 6, RW4 5, RX5 9, RX6 9, RX7Pgrid 12, L3 8, L4 16, L9 8. Mean pairwise correlation of the trials 0.44; effective number of independent trials (eigenvalue participation ratio) 3.9. Variance of the weekly Sharpe across trials 0.00448 (annualised sd 0.48).

## Deflated Sharpe ratio (Bailey-Lopez de Prado 2014): probability that the true Sharpe is above the best-of-N expectation under zero skill

| candidate | N used | annualised Sharpe | expected max Sharpe under the null (annualised) | DSR (probability) | z |
|---|---|---|---|---|---|
| K4v2 cell | N_total = 145 | 1.43 | 1.28 | 0.641 | 0.36 |
| K4v2 cell | N_eff = 4 | 1.43 | 0.51 | 0.990 | 2.32 |
| RX5 cell | N_total = 145 | 1.78 | 1.28 | 0.918 | 1.39 |
| RX5 cell | N_eff = 4 | 1.78 | 0.51 | 1.000 | 3.55 |
| RW12P cell | N_total = 145 | 2.01 | 1.28 | 0.965 | 1.81 |
| RW12P cell | N_eff = 4 | 2.01 | 0.51 | 1.000 | 3.73 |

## Probability of backtest overfitting (CSCV, 16 blocks, 12,870 splits; PBO = P(in-sample best ranks at or below the out-of-sample median))

| trial set | PBO | median logit |
|---|---|---|
| K4v2grid | 0.215 | +1.31 |
| RW12Pgrid | 0.344 | +0.56 |
| RX5 | 0.473 | +0.41 |
| RX7Pgrid | 0.310 | +0.81 |
| all trials | 0.336 | +0.65 |

Reading: DSR near or above 0.95 means the best cell survives deflation for the number of trials tried; PBO well below 0.5 means that selecting the in-sample best of this set does not systematically underperform out of sample. Caveat: all trials share the same 167 weeks (the block CSCV uses the pair window only; the 2016-22 walk-forward years are outside it), the trials are strongly correlated (their effective number is the honest N), and the family contains several choices made after seeing results (RW12 features, RX5 seed averaging) that no count captures.

Runtime 6.5 min. DONE RY7