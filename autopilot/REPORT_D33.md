# REPORT D33
**Verdict: NO** (2/6 measured gates, replication 1/2 available; D1-harness class NO). Selected cell ALIGNES15_BLOCK_a0.25_sg+1: all-in weekly Sharpe uplift clean/H1/H2/all +0.29/+1.27/-0.26/+0.31. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

D33 ES signed volume (ALIGNES15/30/60) as a tilt of NQ flips.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| ALIGNES15_BLOCK_a0.25_sg+1 | +0.286 | 0.999 |
| ALIGNES15_ALL_a0.25_sg+1 | +0.121 | 1.000 |
| ALIGNES30_BLOCK_a0.5_sg-1 | +0.099 | 0.999 |
| ALIGNES60_ALL_a0.5_sg-1 | +0.094 | 1.000 |
| ALIGNES60_BLOCK_a0.25_sg-1 | +0.069 | 0.999 |
| ALIGNES60_BLOCK_a0.5_sg-1 | +0.056 | 0.999 |
| ALIGNES30_ALL_a0.5_sg-1 | -0.004 | 1.000 |
| ALIGNES60_ALL_a0.25_sg-1 | -0.012 | 1.000 |
| ALIGNES30_ALL_a0.25_sg+1 | -0.135 | 1.000 |
| ALIGNES60_ALL_a0.25_sg+1 | -0.147 | 1.000 |
| ALIGNES30_BLOCK_a0.25_sg+1 | -0.165 | 0.999 |
| ALIGNES30_ALL_a0.25_sg-1 | -0.168 | 1.000 |
| ALIGNES30_BLOCK_a0.25_sg-1 | -0.169 | 0.999 |
| ALIGNES15_BLOCK_a0.5_sg+1 | -0.189 | 0.999 |
| ALIGNES15_BLOCK_a0.25_sg-1 | -0.193 | 0.999 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.75 |
| clean | Sortino | 2.78 | 3.40 |
| clean | MAR | 4.75 | 5.85 |
| clean | net $ | 1,329,958.72 | 1,602,898.20 |
| clean | maxDD $ | 280,109.76 | 273,873.19 |
| clean | worst wk $ | -81,873.92 | -80,656.27 |
| clean | CVaR5 $ | -78,735.52 | -79,430.70 |
| clean | CVaR10 $ | -78,008.81 | -78,652.68 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 4.10 |
| H1 | Sortino | 6.09 | 12.00 |
| H1 | MAR | 3.91 | 6.12 |
| H1 | net $ | 593,797.44 | 895,542.27 |
| H1 | maxDD $ | 151,712.64 | 146,309.90 |
| H1 | worst wk $ | -78,287.36 | -78,231.56 |
| H1 | CVaR5 $ | -77,609.92 | -55,199.07 |
| H1 | CVaR10 $ | -66,029.97 | -46,026.25 |
| H1 | % neg wk | 39.29 | 32.14 |
| H2 | weekly Sharpe | 2.30 | 2.04 |
| H2 | Sortino | 4.69 | 4.09 |
| H2 | MAR | 3.50 | 2.53 |
| H2 | net $ | 761,254.40 | 709,360.49 |
| H2 | maxDD $ | 217,425.28 | 279,955.95 |
| H2 | worst wk $ | -82,524.48 | -82,006.00 |
| H2 | CVaR5 $ | -81,088.96 | -81,112.14 |
| H2 | CVaR10 $ | -79,185.12 | -79,811.71 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 2.16 |
| all | Sortino | 3.63 | 4.41 |
| all | MAR | 9.59 | 11.46 |
| all | net $ | 2,685,010.56 | 3,207,800.96 |
| all | maxDD $ | 280,109.76 | 279,955.95 |
| all | worst wk $ | -82,524.48 | -82,006.00 |
| all | CVaR5 $ | -79,220.34 | -79,751.98 |
| all | CVaR10 $ | -78,243.12 | -78,861.32 |
| all | % neg wk | 42.86 | 41.07 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.286 / +1.269 / -0.258
- [PASS] 3 worst week not worse (all-in): -82,006 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.309 vs p95 +0.207 (median -0.197, rank 0.97, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.140, +0.775]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.454 / +0.726 / -0.850
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all -0.02/+1.55/+0.41/+0.30
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.108; a x1.25: +0.220; feat ALIGNES30: -0.067

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.154)

- H0 2023-02-10..2023-07-31: uplift +0.175 -> PASS
- Alternating months: odd-selected ALIGNES60_ALL_a0.25_sg+1 read on even -0.361; even-selected ALIGNES15_BLOCK_a0.25_sg+1 read on odd -0.078 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Needs an ES tick stream in the NT8 strategy (second data series with tick-rule signed volume); multiplier 0.5-1.5.

DONE D33