# REPORT D35
**Verdict: NO** (0/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell ABS5_q0.1_x0.0_BLOCK: all-in weekly Sharpe uplift clean/H1/H2/all +0.13/-0.65/-0.50/-0.11. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

D35 quiet-flow filter: skip or halve entries when the last-5-minute |signed volume| is below its expanding quantile.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| ABS5_q0.1_x0.0_BLOCK | +0.126 | 0.106 |
| ABS5_q0.2_x0.5_BLOCK | -0.123 | 0.211 |
| ABS5_q0.1_x0.5_BLOCK | -0.133 | 0.106 |
| ABS5_q0.1_x0.5_ALL | -0.183 | 0.102 |
| ABS5_q0.2_x0.0_BLOCK | -0.238 | 0.211 |
| ABS5_q0.1_x0.0_ALL | -0.255 | 0.102 |
| ABS5_q0.33_x0.5_ALL | -0.316 | 0.359 |
| ABS5_q0.33_x0.5_BLOCK | -0.374 | 0.354 |
| ABS5_q0.2_x0.5_ALL | -0.396 | 0.210 |
| ABS5_q0.33_x0.0_BLOCK | -0.557 | 0.354 |
| ABS5_q0.33_x0.0_ALL | -0.731 | 0.359 |
| ABS5_q0.2_x0.0_ALL | -0.731 | 0.210 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.59 |
| clean | Sortino | 2.78 | 2.86 |
| clean | MAR | 4.75 | 4.92 |
| clean | net $ | 1,329,958.72 | 1,308,101.76 |
| clean | maxDD $ | 280,109.76 | 265,685.12 |
| clean | worst wk $ | -81,873.92 | -83,380.80 |
| clean | CVaR5 $ | -78,735.52 | -78,785.44 |
| clean | CVaR10 $ | -78,008.81 | -78,017.11 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.17 |
| H1 | Sortino | 6.09 | 4.68 |
| H1 | MAR | 3.91 | 3.40 |
| H1 | net $ | 593,797.44 | 573,807.36 |
| H1 | maxDD $ | 151,712.64 | 169,005.76 |
| H1 | worst wk $ | -78,287.36 | -78,770.56 |
| H1 | CVaR5 $ | -77,609.92 | -78,279.20 |
| H1 | CVaR10 $ | -66,029.97 | -77,830.29 |
| H1 | % neg wk | 39.29 | 46.43 |
| H2 | weekly Sharpe | 2.30 | 1.79 |
| H2 | Sortino | 4.69 | 3.83 |
| H2 | MAR | 3.50 | 3.25 |
| H2 | net $ | 761,254.40 | 636,596.48 |
| H2 | maxDD $ | 217,425.28 | 195,830.40 |
| H2 | worst wk $ | -82,524.48 | -78,780.80 |
| H2 | CVaR5 $ | -81,088.96 | -77,963.84 |
| H2 | CVaR10 $ | -79,185.12 | -77,478.24 |
| H2 | % neg wk | 44.44 | 47.22 |
| all | weekly Sharpe | 1.86 | 1.75 |
| all | Sortino | 3.63 | 3.39 |
| all | MAR | 9.59 | 9.48 |
| all | net $ | 2,685,010.56 | 2,518,505.60 |
| all | maxDD $ | 280,109.76 | 265,685.12 |
| all | worst wk $ | -82,524.48 | -83,380.80 |
| all | CVaR5 $ | -79,220.34 | -78,672.43 |
| all | CVaR10 $ | -78,243.12 | -77,921.15 |
| all | % neg wk | 42.86 | 44.05 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.126 / -0.653 / -0.503
- [FAIL] 3 worst week not worse (all-in): -83,381 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.108 vs p95 +0.163 (median -0.206, rank 0.67, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.592, +0.362]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.057 / -0.548 / -0.645
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.36/+0.19/-0.14/+0.22
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): q x0.75: +0.022; q x1.25: +0.001

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.054)

- H0 2023-02-10..2023-07-31: uplift -0.076 -> FAIL
- Alternating months: odd-selected ABS5_q0.1_x0.0_BLOCK read on even -0.035; even-selected ABS5_q0.1_x0.0_ALL read on odd -0.893 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Entry skip or halve when the 5-minute absolute signed volume (tick rule) is below its expanding quantile; reduces entries only.

DONE D35