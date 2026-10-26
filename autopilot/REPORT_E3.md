# REPORT E3
**Verdict: NO** (2/6 measured gates, replication 1/2 available; D1-harness class NO). Selected cell W120_a0.25_BLOCK_sg-1: all-in weekly Sharpe uplift clean/H1/H2/all +0.10/+0.04/+0.44/+0.17. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

E3 PERS30 continuous size tilt (32 cells): factor 1 +- a(2p-1) clipped to 0.5-1.5 from the walk-forward percentile of the signed-volume persistence over W minutes before the entry bar; normal contract counts.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | mean factor on clean |
|---|---|---|
| W120_a0.25_BLOCK_sg-1 | +0.102 | 1.009 |
| W30_a0.5_BLOCK_sg-1 | +0.059 | 1.021 |
| W120_a0.25_ALL_sg+1 | +0.029 | 0.997 |
| W30_a0.25_BLOCK_sg-1 | +0.009 | 1.011 |
| W120_a0.5_ALL_sg+1 | -0.001 | 0.994 |
| W30_a0.25_ALL_sg+1 | -0.003 | 0.996 |
| W60_a0.5_BLOCK_sg-1 | -0.024 | 1.016 |
| W15_a0.25_ALL_sg+1 | -0.070 | 0.994 |
| W60_a0.25_BLOCK_sg-1 | -0.072 | 1.008 |
| W60_a0.25_ALL_sg-1 | -0.082 | 1.002 |
| W60_a0.5_ALL_sg-1 | -0.091 | 1.004 |
| W60_a0.25_ALL_sg+1 | -0.139 | 0.998 |
| W60_a0.5_ALL_sg+1 | -0.174 | 0.996 |
| W30_a0.5_ALL_sg-1 | -0.216 | 1.008 |
| W120_a0.25_BLOCK_sg+1 | -0.241 | 0.991 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.56 |
| clean | Sortino | 2.78 | 2.90 |
| clean | MAR | 4.75 | 4.87 |
| clean | net $ | 1,329,958.72 | 1,410,295.93 |
| clean | maxDD $ | 280,109.76 | 289,475.36 |
| clean | worst wk $ | -81,873.92 | -79,803.50 |
| clean | CVaR5 $ | -78,735.52 | -79,110.66 |
| clean | CVaR10 $ | -78,008.81 | -78,375.85 |
| clean | % neg wk | 42.86 | 42.86 |
| H1 | weekly Sharpe | 2.83 | 2.87 |
| H1 | Sortino | 6.09 | 6.60 |
| H1 | MAR | 3.91 | 2.80 |
| H1 | net $ | 593,797.44 | 622,435.71 |
| H1 | maxDD $ | 151,712.64 | 222,338.91 |
| H1 | worst wk $ | -78,287.36 | -78,094.79 |
| H1 | CVaR5 $ | -77,609.92 | -77,698.40 |
| H1 | CVaR10 $ | -66,029.97 | -66,111.34 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 2.73 |
| H2 | Sortino | 4.69 | 6.00 |
| H2 | MAR | 3.50 | 3.87 |
| H2 | net $ | 761,254.40 | 847,855.45 |
| H2 | maxDD $ | 217,425.28 | 219,314.48 |
| H2 | worst wk $ | -82,524.48 | -78,271.17 |
| H2 | CVaR5 $ | -81,088.96 | -77,922.40 |
| H2 | CVaR10 $ | -79,185.12 | -74,404.29 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 2.02 |
| all | Sortino | 3.63 | 3.98 |
| all | MAR | 9.59 | 9.95 |
| all | net $ | 2,685,010.56 | 2,880,587.09 |
| all | maxDD $ | 280,109.76 | 289,475.36 |
| all | worst wk $ | -82,524.48 | -79,803.50 |
| all | CVaR5 $ | -79,220.34 | -78,787.63 |
| all | CVaR10 $ | -78,243.12 | -78,090.82 |
| all | % neg wk | 42.86 | 42.26 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.102 / +0.039 / +0.438
- [PASS] 3 worst week not worse (all-in): -79,804 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.168 vs p95 +0.147 (median -0.188, rank 0.96, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.241, +0.589]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.260 / -0.133 / +0.093
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.39/+0.24/+0.51/+0.38
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): W prev: -0.281; a x0.75: +0.089; a x1.25: -0.010

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.084)

- H0 2023-02-10..2023-07-31: uplift +0.498 -> PASS
- Alternating months: odd-selected W30_a0.25_BLOCK_sg+1 read on even -0.018; even-selected W120_a0.25_BLOCK_sg-1 read on odd -0.362 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Entry quantity multiplier per flip computed from the trailing-window signed-volume persistence (needs a per-minute signed-volume feed in NT8 from the tick stream; percentile vs expanding history by ET block); contract counts stay normal (mean factor ~1, range 0.5-1.5), margin unchanged at the peak (1.5x on 15 percent of entries).

DONE E3