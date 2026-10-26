# REPORT RW13
**Verdict: NO** (1/6 measured gates, replication 1/2 available; D1-harness class NO). Selected cell RU_hi_q0.8_x0.5: all-in weekly Sharpe uplift clean/H1/H2/all -0.09/+0.04/-0.00/-0.04. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

R13 range-used (day range so far / ADR20) regime tilt and switch (12 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| RU_hi_q0.8_x0.5 | -0.088 | 0.204 |
| RU_ALL_a0.5_sg-1 | -0.144 | 1.000 |
| RU_BLOCK_a0.25_sg+1 | -0.169 | 0.999 |
| RU_hi_q0.67_x0.5 | -0.176 | 0.322 |
| RU_BLOCK_a0.25_sg-1 | -0.294 | 0.999 |
| RU_ALL_a0.25_sg-1 | -0.355 | 1.000 |
| RU_hi_q0.8_x0.0 | -0.392 | 0.204 |
| RU_BLOCK_a0.5_sg+1 | -0.399 | 0.999 |
| RU_hi_q0.67_x0.0 | -0.433 | 0.322 |
| RU_ALL_a0.25_sg+1 | -0.512 | 1.000 |
| RU_BLOCK_a0.5_sg-1 | -0.586 | 0.999 |
| RU_ALL_a0.5_sg+1 | -1.146 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.37 |
| clean | Sortino | 2.78 | 2.53 |
| clean | MAR | 4.75 | 4.51 |
| clean | net $ | 1,329,958.72 | 1,198,897.76 |
| clean | maxDD $ | 280,109.76 | 266,030.24 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,735.52 |
| clean | CVaR10 $ | -78,008.81 | -77,994.07 |
| clean | % neg wk | 42.86 | 42.86 |
| H1 | weekly Sharpe | 2.83 | 2.86 |
| H1 | Sortino | 6.09 | 6.56 |
| H1 | MAR | 3.91 | 4.09 |
| H1 | net $ | 593,797.44 | 620,866.08 |
| H1 | maxDD $ | 151,712.64 | 151,712.64 |
| H1 | worst wk $ | -78,287.36 | -77,229.92 |
| H1 | CVaR5 $ | -77,609.92 | -77,192.24 |
| H1 | CVaR10 $ | -66,029.97 | -66,695.63 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 2.29 |
| H2 | Sortino | 4.69 | 4.70 |
| H2 | MAR | 3.50 | 3.45 |
| H2 | net $ | 761,254.40 | 750,019.84 |
| H2 | maxDD $ | 217,425.28 | 217,425.28 |
| H2 | worst wk $ | -82,524.48 | -79,653.44 |
| H2 | CVaR5 $ | -81,088.96 | -79,222.80 |
| H2 | CVaR10 $ | -79,185.12 | -78,252.04 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.82 |
| all | Sortino | 3.63 | 3.53 |
| all | MAR | 9.59 | 9.66 |
| all | net $ | 2,685,010.56 | 2,569,783.68 |
| all | maxDD $ | 280,109.76 | 266,030.24 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -78,697.16 |
| all | CVaR10 $ | -78,243.12 | -77,960.43 |
| all | % neg wk | 42.86 | 42.26 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.088 / +0.036 / -0.002
- [PASS] 3 worst week not worse (all-in): -81,874 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.036 vs p95 +0.132 (median -0.190, rank 0.76, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.185, +0.117]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.090 / +0.066 / -0.040
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.06/+0.42/+0.00/+0.11
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): q x0.75: -0.129; q x1.25: -0.033

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.018)

- H0 2023-02-10..2023-07-31: uplift +0.224 -> PASS
- Alternating months: odd-selected RU_hi_q0.67_x0.5 read on even -0.221; even-selected RU_ALL_a0.5_sg+1 read on odd -1.356 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Running day range / ADR20 computed in-strategy; multiplier or halve.

DONE RW13