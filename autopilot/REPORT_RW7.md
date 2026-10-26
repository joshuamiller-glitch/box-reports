# REPORT RW7
**Verdict: NO** (1/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell cut12_x0.5: all-in weekly Sharpe uplift clean/H1/H2/all -0.04/-0.10/-0.06/-0.05. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

R7 late-day entry cutoff (skip or halve RTH entries after 12/13/14 ET; 6 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| cut12_x0.5 | -0.042 | 0.225 |
| cut14_x0.5 | -0.045 | 0.078 |
| cut14_x0.0 | -0.045 | 0.078 |
| cut13_x0.5 | -0.048 | 0.146 |
| cut12_x0.0 | -0.087 | 0.225 |
| cut13_x0.0 | -0.276 | 0.146 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.42 |
| clean | Sortino | 2.78 | 2.63 |
| clean | MAR | 4.75 | 4.84 |
| clean | net $ | 1,329,958.72 | 1,240,054.24 |
| clean | maxDD $ | 280,109.76 | 256,218.40 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,605.09 |
| clean | CVaR10 $ | -78,008.81 | -77,957.43 |
| clean | % neg wk | 42.86 | 44.76 |
| H1 | weekly Sharpe | 2.83 | 2.73 |
| H1 | Sortino | 6.09 | 5.98 |
| H1 | MAR | 3.91 | 4.20 |
| H1 | net $ | 593,797.44 | 561,463.52 |
| H1 | maxDD $ | 151,712.64 | 133,702.88 |
| H1 | worst wk $ | -78,287.36 | -77,467.36 |
| H1 | CVaR5 $ | -77,609.92 | -77,466.08 |
| H1 | CVaR10 $ | -66,029.97 | -64,991.52 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 2.24 |
| H2 | Sortino | 4.69 | 4.62 |
| H2 | MAR | 3.50 | 3.48 |
| H2 | net $ | 761,254.40 | 740,032.80 |
| H2 | maxDD $ | 217,425.28 | 212,812.96 |
| H2 | worst wk $ | -82,524.48 | -79,653.44 |
| H2 | CVaR5 $ | -81,088.96 | -78,714.56 |
| H2 | CVaR10 $ | -79,185.12 | -78,007.68 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.81 |
| all | Sortino | 3.63 | 3.49 |
| all | MAR | 9.59 | 9.92 |
| all | net $ | 2,685,010.56 | 2,541,550.56 |
| all | maxDD $ | 280,109.76 | 256,218.40 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -78,503.00 |
| all | CVaR10 $ | -78,243.12 | -77,911.44 |
| all | % neg wk | 42.86 | 43.45 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.042 / -0.098 / -0.056
- [PASS] 3 worst week not worse (all-in): -81,874 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.047 vs p95 +0.122 (median -0.213, rank 0.80, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.184, +0.098]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 1
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.044 / -0.016 / -0.103
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.15/+0.06/-0.11/+0.09
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): h 13: -0.017

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.024)

- H0 2023-02-10..2023-07-31: uplift -0.334 -> FAIL
- Alternating months: odd-selected cut12_x0.0 read on even -0.360; even-selected cut14_x0.5 read on odd +0.026 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Entry cutoff time (skip or halve entries after the cutoff hour); a DualStrat session parameter.

DONE RW7