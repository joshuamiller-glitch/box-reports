# REPORT D37
**Verdict: NO** (1/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell N5_BLOCK_a0.5_sg+1: all-in weekly Sharpe uplift clean/H1/H2/all +0.27/-0.73/-0.66/-0.09. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

D37 trade-arrival intensity (trades over the last 5/15 minutes) tilt.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| N5_BLOCK_a0.5_sg+1 | +0.274 | 0.999 |
| N5_ALL_a0.25_sg-1 | +0.009 | 1.000 |
| N15_ALL_a0.25_sg-1 | -0.016 | 1.000 |
| N15_BLOCK_a0.25_sg-1 | -0.024 | 0.999 |
| N5_BLOCK_a0.25_sg-1 | -0.065 | 0.999 |
| N15_BLOCK_a0.5_sg+1 | -0.071 | 0.999 |
| N15_ALL_a0.5_sg-1 | -0.086 | 1.000 |
| N15_BLOCK_a0.25_sg+1 | -0.214 | 0.999 |
| N5_BLOCK_a0.25_sg+1 | -0.354 | 0.999 |
| N5_ALL_a0.5_sg+1 | -0.437 | 1.000 |
| N5_ALL_a0.5_sg-1 | -0.455 | 1.000 |
| N5_ALL_a0.25_sg+1 | -0.471 | 1.000 |
| N15_BLOCK_a0.5_sg-1 | -0.557 | 0.999 |
| N15_ALL_a0.25_sg+1 | -0.592 | 1.000 |
| N15_ALL_a0.5_sg+1 | -0.742 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.73 |
| clean | Sortino | 2.78 | 3.26 |
| clean | MAR | 4.75 | 5.27 |
| clean | net $ | 1,329,958.72 | 1,525,663.11 |
| clean | maxDD $ | 280,109.76 | 289,349.13 |
| clean | worst wk $ | -81,873.92 | -81,612.26 |
| clean | CVaR5 $ | -78,735.52 | -79,110.54 |
| clean | CVaR10 $ | -78,008.81 | -78,381.25 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.10 |
| H1 | Sortino | 6.09 | 4.14 |
| H1 | MAR | 3.91 | 2.21 |
| H1 | net $ | 593,797.44 | 480,012.55 |
| H1 | maxDD $ | 151,712.64 | 217,491.57 |
| H1 | worst wk $ | -78,287.36 | -80,333.55 |
| H1 | CVaR5 $ | -77,609.92 | -78,649.03 |
| H1 | CVaR10 $ | -66,029.97 | -78,066.92 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 1.63 |
| H2 | Sortino | 4.69 | 3.49 |
| H2 | MAR | 3.50 | 2.02 |
| H2 | net $ | 761,254.40 | 652,364.92 |
| H2 | maxDD $ | 217,425.28 | 322,271.38 |
| H2 | worst wk $ | -82,524.48 | -79,485.96 |
| H2 | CVaR5 $ | -81,088.96 | -78,801.44 |
| H2 | CVaR10 $ | -79,185.12 | -78,115.51 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.76 |
| all | Sortino | 3.63 | 3.45 |
| all | MAR | 9.59 | 8.25 |
| all | net $ | 2,685,010.56 | 2,658,040.58 |
| all | maxDD $ | 280,109.76 | 322,271.38 |
| all | worst wk $ | -82,524.48 | -81,612.26 |
| all | CVaR5 $ | -79,220.34 | -79,177.74 |
| all | CVaR10 $ | -78,243.12 | -78,371.12 |
| all | % neg wk | 42.86 | 41.67 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.274 / -0.732 / -0.665
- [PASS] 3 worst week not worse (all-in): -81,612 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.093 vs p95 +0.024 (median -0.383, rank 0.89, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.610, +0.440]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.383 / -0.852 / -1.184
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.23/-0.55/+0.00/+0.06
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: -0.207; a x1.25: -0.080; feat N15: -0.479

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.046)

- H0 2023-02-10..2023-07-31: uplift -0.621 -> FAIL
- Alternating months: odd-selected N15_ALL_a0.25_sg-1 read on even -0.114; even-selected N5_ALL_a0.5_sg+1 read on odd -0.941 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Trade-count over the last N minutes from the tick stream; multiplier 0.5-1.5.

DONE D37