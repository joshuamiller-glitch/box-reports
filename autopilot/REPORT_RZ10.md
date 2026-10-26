# REPORT RZ10
**Verdict: NO** (1/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell a0.5_sg+1_RTH: all-in weekly Sharpe uplift clean/H1/H2/all +0.11/-0.02/+0.00/+0.06. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

RZ10 RZ4 with a cross-asset overnight-range leg added to the forecast (8 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| a0.5_sg+1_RTH | +0.109 | 0.473 |
| a0.25_sg+1_RTH | +0.045 | 0.473 |
| a0.5_sg+1_ALL | +0.034 | 1.000 |
| a0.25_sg+1_ALL | -0.105 | 1.000 |
| a0.25_sg-1_ALL | -0.141 | 1.000 |
| a0.5_sg-1_RTH | -0.197 | 0.473 |
| a0.25_sg-1_RTH | -0.198 | 0.473 |
| a0.5_sg-1_ALL | -0.348 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.57 |
| clean | Sortino | 2.78 | 2.98 |
| clean | MAR | 4.75 | 5.28 |
| clean | net $ | 1,329,958.72 | 1,460,824.38 |
| clean | maxDD $ | 280,109.76 | 276,884.97 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -79,152.51 |
| clean | CVaR10 $ | -78,008.81 | -78,471.88 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.81 |
| H1 | Sortino | 6.09 | 6.04 |
| H1 | MAR | 3.91 | 3.80 |
| H1 | net $ | 593,797.44 | 583,048.98 |
| H1 | maxDD $ | 151,712.64 | 153,292.95 |
| H1 | worst wk $ | -78,287.36 | -79,269.28 |
| H1 | CVaR5 $ | -77,609.92 | -78,408.77 |
| H1 | CVaR10 $ | -66,029.97 | -66,914.77 |
| H1 | % neg wk | 39.29 | 42.86 |
| H2 | weekly Sharpe | 2.30 | 2.30 |
| H2 | Sortino | 4.69 | 4.69 |
| H2 | MAR | 3.50 | 3.53 |
| H2 | net $ | 761,254.40 | 759,840.53 |
| H2 | maxDD $ | 217,425.28 | 215,512.64 |
| H2 | worst wk $ | -82,524.48 | -79,596.89 |
| H2 | CVaR5 $ | -81,088.96 | -79,040.59 |
| H2 | CVaR10 $ | -79,185.12 | -78,317.32 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.92 |
| all | Sortino | 3.63 | 3.74 |
| all | MAR | 9.59 | 10.13 |
| all | net $ | 2,685,010.56 | 2,803,713.88 |
| all | maxDD $ | 280,109.76 | 276,884.97 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -79,140.61 |
| all | CVaR10 $ | -78,243.12 | -78,440.83 |
| all | % neg wk | 42.86 | 42.26 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.109 / -0.018 / +0.000
- [PASS] 3 worst week not worse (all-in): -81,874 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real +0.060 vs p95 +0.153 (median -0.161, rank 0.85, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.177, +0.297]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 67% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.296 / +0.130 / -0.053
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.14/-0.02/+0.03/+0.09
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.050; a x1.25: +0.125; scope other: -0.044

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.030)

- H0 2023-02-10..2023-07-31: uplift -0.424 -> FAIL
- Alternating months: odd-selected a0.5_sg+1_RTH read on even +0.089; even-selected a0.25_sg+1_ALL read on odd -0.440 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. As RZ4 plus an overnight-range leg from ZN/6J/CL/GC data series.

DONE RZ10