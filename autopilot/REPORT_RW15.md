# REPORT RW15
**Verdict: NO** (2/6 measured gates, replication 1/2 available; D1-harness class NO). Selected cell RS20_abs_a0.5_sg+1: all-in weekly Sharpe uplift clean/H1/H2/all +0.11/+0.87/-0.90/-0.03. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

R15 NQ-ES relative-strength tilt (daily, 16 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| RS20_abs_a0.5_sg+1 | +0.114 | 1.000 |
| RS5_abs_a0.25_sg+1 | +0.056 | 1.000 |
| RS20_dir_a0.5_sg-1 | +0.050 | 1.000 |
| RS5_dir_a0.25_sg-1 | -0.153 | 1.000 |
| RS5_abs_a0.5_sg+1 | -0.174 | 1.000 |
| RS20_dir_a0.25_sg-1 | -0.184 | 1.000 |
| RS20_abs_a0.25_sg-1 | -0.242 | 1.000 |
| RS5_dir_a0.25_sg+1 | -0.260 | 1.000 |
| RS5_dir_a0.5_sg-1 | -0.265 | 1.000 |
| RS20_abs_a0.5_sg-1 | -0.285 | 1.000 |
| RS20_dir_a0.25_sg+1 | -0.292 | 1.000 |
| RS20_abs_a0.25_sg+1 | -0.420 | 1.000 |
| RS5_abs_a0.25_sg-1 | -0.500 | 1.000 |
| RS20_dir_a0.5_sg+1 | -0.645 | 1.000 |
| RS5_dir_a0.5_sg+1 | -0.671 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.57 |
| clean | Sortino | 2.78 | 2.98 |
| clean | MAR | 4.75 | 4.10 |
| clean | net $ | 1,329,958.72 | 1,392,094.77 |
| clean | maxDD $ | 280,109.76 | 339,653.91 |
| clean | worst wk $ | -81,873.92 | -82,179.85 |
| clean | CVaR5 $ | -78,735.52 | -78,929.25 |
| clean | CVaR10 $ | -78,008.81 | -78,180.16 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 3.70 |
| H1 | Sortino | 6.09 | 8.33 |
| H1 | MAR | 3.91 | 6.09 |
| H1 | net $ | 593,797.44 | 806,546.53 |
| H1 | maxDD $ | 151,712.64 | 132,402.19 |
| H1 | worst wk $ | -78,287.36 | -78,587.19 |
| H1 | CVaR5 $ | -77,609.92 | -77,929.77 |
| H1 | CVaR10 $ | -66,029.97 | -69,351.87 |
| H1 | % neg wk | 39.29 | 28.57 |
| H2 | weekly Sharpe | 2.30 | 1.40 |
| H2 | Sortino | 4.69 | 2.82 |
| H2 | MAR | 3.50 | 2.22 |
| H2 | net $ | 761,254.40 | 568,793.06 |
| H2 | maxDD $ | 217,425.28 | 256,396.43 |
| H2 | worst wk $ | -82,524.48 | -81,724.34 |
| H2 | CVaR5 $ | -81,088.96 | -80,740.97 |
| H2 | CVaR10 $ | -79,185.12 | -79,939.18 |
| H2 | % neg wk | 44.44 | 50.00 |
| all | weekly Sharpe | 1.86 | 1.83 |
| all | Sortino | 3.63 | 3.59 |
| all | MAR | 9.59 | 8.15 |
| all | net $ | 2,685,010.56 | 2,767,434.36 |
| all | maxDD $ | 280,109.76 | 339,653.91 |
| all | worst wk $ | -82,524.48 | -82,179.85 |
| all | CVaR5 $ | -79,220.34 | -79,638.35 |
| all | CVaR10 $ | -78,243.12 | -78,729.82 |
| all | % neg wk | 42.86 | 41.67 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.114 / +0.874 / -0.896
- [PASS] 3 worst week not worse (all-in): -82,180 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real -0.030 vs p95 -0.049 (median -0.406, rank 0.95, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.546, +0.504]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.148 / +0.651 / -1.172
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all -0.02/+1.35/-0.27/+0.14
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.006; a x1.25: -0.155; W other: -0.423

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.015)

- H0 2023-02-10..2023-07-31: uplift +1.150 -> PASS
- Alternating months: odd-selected RS20_dir_a0.25_sg-1 read on even -0.246; even-selected RS20_abs_a0.5_sg+1 read on odd -0.602 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Daily file: NQ minus ES relative strength percentile from the previous close; multiplier.

DONE RW15