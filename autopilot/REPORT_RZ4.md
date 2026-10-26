# REPORT RZ4
**Verdict: NO** (1/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell a0.5_sg+1_RTH: all-in weekly Sharpe uplift clean/H1/H2/all +0.15/+0.11/+0.02/+0.11. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

RZ4 pair flips tilted by a walk-forward pre-open range-expansion forecast (8 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| a0.5_sg+1_RTH | +0.150 | 0.473 |
| a0.5_sg+1_ALL | +0.078 | 1.000 |
| a0.25_sg+1_RTH | +0.027 | 0.473 |
| a0.5_sg-1_RTH | -0.053 | 0.473 |
| a0.25_sg+1_ALL | -0.103 | 1.000 |
| a0.25_sg-1_ALL | -0.153 | 1.000 |
| a0.25_sg-1_RTH | -0.194 | 0.473 |
| a0.5_sg-1_ALL | -0.304 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.61 |
| clean | Sortino | 2.78 | 3.08 |
| clean | MAR | 4.75 | 5.39 |
| clean | net $ | 1,329,958.72 | 1,509,652.18 |
| clean | maxDD $ | 280,109.76 | 279,855.40 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,939.15 |
| clean | CVaR10 $ | -78,008.81 | -78,259.09 |
| clean | % neg wk | 42.86 | 42.86 |
| H1 | weekly Sharpe | 2.83 | 2.94 |
| H1 | Sortino | 6.09 | 6.58 |
| H1 | MAR | 3.91 | 4.11 |
| H1 | net $ | 593,797.44 | 615,548.99 |
| H1 | maxDD $ | 151,712.64 | 149,642.33 |
| H1 | worst wk $ | -78,287.36 | -79,694.50 |
| H1 | CVaR5 $ | -77,609.92 | -78,340.03 |
| H1 | CVaR10 $ | -66,029.97 | -67,622.76 |
| H1 | % neg wk | 39.29 | 42.86 |
| H2 | weekly Sharpe | 2.30 | 2.31 |
| H2 | Sortino | 4.69 | 4.71 |
| H2 | MAR | 3.50 | 3.57 |
| H2 | net $ | 761,254.40 | 766,826.59 |
| H2 | maxDD $ | 217,425.28 | 214,601.48 |
| H2 | worst wk $ | -82,524.48 | -81,040.48 |
| H2 | CVaR5 $ | -81,088.96 | -79,631.38 |
| H2 | CVaR10 $ | -79,185.12 | -78,501.16 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.96 |
| all | Sortino | 3.63 | 3.86 |
| all | MAR | 9.59 | 10.33 |
| all | net $ | 2,685,010.56 | 2,892,027.77 |
| all | maxDD $ | 280,109.76 | 279,855.40 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -79,176.90 |
| all | CVaR10 $ | -78,243.12 | -78,339.43 |
| all | % neg wk | 42.86 | 42.86 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.150 / +0.111 / +0.019
- [PASS] 3 worst week not worse (all-in): -81,874 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real +0.109 vs p95 +0.132 (median -0.163, rank 0.92, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.128, +0.349]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 33% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.301 / +0.188 / +0.012
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.15/+0.19/+0.01/+0.13
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.060; a x1.25: +0.134; scope other: -0.010

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.054)

- H0 2023-02-10..2023-07-31: uplift -0.437 -> FAIL
- Alternating months: odd-selected a0.5_sg-1_RTH read on even -0.032; even-selected a0.5_sg+1_ALL read on odd -0.296 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Daily pre-open range-expansion score (overnight range, prior-day range, VIX percentile) computed in-strategy at 09:29 ET; multiplier on RTH flips.

DONE RZ4