# REPORT RW6
**Verdict: NO** (1/6 measured gates, replication 2/2 available; D1-harness class NO). Selected cell ALIGNES5_both_a0.25: all-in weekly Sharpe uplift clean/H1/H2/all +0.37/+0.37/-1.30/-0.02. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

R6 ES-flow alignment tilt restricted by book and shorter windows (D33 cure; 18 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| ALIGNES5_both_a0.25 | +0.374 | 0.999 |
| ALIGNES15_both_a0.25 | +0.286 | 0.999 |
| ALIGNES15_ST_a0.25 | +0.256 | 0.584 |
| ALIGNES10_both_a0.25 | +0.229 | 0.999 |
| ALIGNES5_both_a0.5 | +0.202 | 0.999 |
| ALIGNES10_ST_a0.5 | +0.157 | 0.584 |
| ALIGNES15_ST_a0.5 | +0.097 | 0.584 |
| ALIGNES5_ST_a0.5 | +0.049 | 0.585 |
| ALIGNES10_ST_a0.25 | -0.009 | 0.584 |
| ALIGNES5_ST_a0.25 | -0.022 | 0.585 |
| ALIGNES10_both_a0.5 | -0.070 | 0.999 |
| ALIGNES10_HM_a0.25 | -0.108 | 0.414 |
| ALIGNES15_HM_a0.25 | -0.148 | 0.414 |
| ALIGNES5_HM_a0.25 | -0.148 | 0.414 |
| ALIGNES15_both_a0.5 | -0.189 | 0.999 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.83 |
| clean | Sortino | 2.78 | 3.64 |
| clean | MAR | 4.75 | 5.98 |
| clean | net $ | 1,329,958.72 | 1,668,560.34 |
| clean | maxDD $ | 280,109.76 | 278,982.23 |
| clean | worst wk $ | -81,873.92 | -80,095.21 |
| clean | CVaR5 $ | -78,735.52 | -78,572.53 |
| clean | CVaR10 $ | -78,008.81 | -77,910.50 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 3.20 |
| H1 | Sortino | 6.09 | 7.30 |
| H1 | MAR | 3.91 | 4.95 |
| H1 | net $ | 593,797.44 | 710,061.75 |
| H1 | maxDD $ | 151,712.64 | 143,388.33 |
| H1 | worst wk $ | -78,287.36 | -78,485.97 |
| H1 | CVaR5 $ | -77,609.92 | -78,418.30 |
| H1 | CVaR10 $ | -66,029.97 | -72,233.23 |
| H1 | % neg wk | 39.29 | 32.14 |
| H2 | weekly Sharpe | 2.30 | 1.00 |
| H2 | Sortino | 4.69 | 1.79 |
| H2 | MAR | 3.50 | 1.05 |
| H2 | net $ | 761,254.40 | 358,447.38 |
| H2 | maxDD $ | 217,425.28 | 341,790.51 |
| H2 | worst wk $ | -82,524.48 | -78,296.13 |
| H2 | CVaR5 $ | -81,088.96 | -77,878.25 |
| H2 | CVaR10 $ | -79,185.12 | -77,594.21 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.84 |
| all | Sortino | 3.63 | 3.60 |
| all | MAR | 9.59 | 8.01 |
| all | net $ | 2,685,010.56 | 2,737,069.46 |
| all | maxDD $ | 280,109.76 | 341,790.51 |
| all | worst wk $ | -82,524.48 | -80,095.21 |
| all | CVaR5 $ | -79,220.34 | -78,520.16 |
| all | CVaR10 $ | -78,243.12 | -77,917.49 |
| all | % neg wk | 42.86 | 40.48 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.374 / +0.372 / -1.300
- [PASS] 3 worst week not worse (all-in): -80,095 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.015 vs p95 +0.153 (median -0.205, rank 0.78, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.547, +0.513]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.459 / +0.327 / -1.053
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.15/+1.01/-0.34/+0.18
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.109; a x1.25: -0.044; W 10: +0.221

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.008)

- H0 2023-02-10..2023-07-31: uplift +0.364 -> PASS
- Alternating months: odd-selected ALIGNES5_ST_a0.5 read on even +0.066; even-selected ALIGNES15_ST_a0.25 read on odd +0.047 -> PASS
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. ES tick stream in NT8; per-book multiplier from the ES imbalance over the last W minutes.

DONE RW6