# REPORT D34
**Verdict: NO** (2/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell ON_w2_a0.25_sg+1: all-in weekly Sharpe uplift clean/H1/H2/all +0.02/+0.92/-0.12/+0.11. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

D34 overnight signed-volume carry as agreement tilt on first-RTH-hour entries.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| ON_w2_a0.25_sg+1 | +0.017 | 0.206 |
| ON_w2_a0.5_sg+1 | -0.028 | 0.206 |
| ON_w1_a0.25_sg-1 | -0.071 | 0.100 |
| ON_w2_a0.5_sg-1 | -0.108 | 0.206 |
| ON_w1_a0.5_sg-1 | -0.108 | 0.100 |
| ON_w2_a0.25_sg-1 | -0.119 | 0.206 |
| ON_w1_a0.5_sg+1 | -0.218 | 0.100 |
| ON_w1_a0.25_sg+1 | -0.223 | 0.100 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.48 |
| clean | Sortino | 2.78 | 2.84 |
| clean | MAR | 4.75 | 3.72 |
| clean | net $ | 1,329,958.72 | 1,397,737.12 |
| clean | maxDD $ | 280,109.76 | 375,623.68 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,363.12 |
| clean | CVaR10 $ | -78,008.81 | -77,809.70 |
| clean | % neg wk | 42.86 | 42.86 |
| H1 | weekly Sharpe | 2.83 | 3.74 |
| H1 | Sortino | 6.09 | 10.42 |
| H1 | MAR | 3.91 | 5.51 |
| H1 | net $ | 593,797.44 | 802,238.00 |
| H1 | maxDD $ | 151,712.64 | 145,592.40 |
| H1 | worst wk $ | -78,287.36 | -79,076.08 |
| H1 | CVaR5 $ | -77,609.92 | -61,431.96 |
| H1 | CVaR10 $ | -66,029.97 | -51,469.12 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 2.18 |
| H2 | Sortino | 4.69 | 4.28 |
| H2 | MAR | 3.50 | 3.45 |
| H2 | net $ | 761,254.40 | 754,680.16 |
| H2 | maxDD $ | 217,425.28 | 218,691.44 |
| H2 | worst wk $ | -82,524.48 | -79,674.88 |
| H2 | CVaR5 $ | -81,088.96 | -79,118.52 |
| H2 | CVaR10 $ | -79,185.12 | -78,404.56 |
| H2 | % neg wk | 44.44 | 38.89 |
| all | weekly Sharpe | 1.86 | 1.96 |
| all | Sortino | 3.63 | 3.92 |
| all | MAR | 9.59 | 7.87 |
| all | net $ | 2,685,010.56 | 2,954,655.28 |
| all | maxDD $ | 280,109.76 | 375,623.68 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -78,700.72 |
| all | CVaR10 $ | -78,243.12 | -77,985.17 |
| all | % neg wk | 42.86 | 41.07 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.017 / +0.916 / -0.119
- [PASS] 3 worst week not worse (all-in): -81,874 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.107 vs p95 +0.102 (median -0.115, rank 0.95, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.196, +0.395]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 67% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.162 / +0.243 / -0.199
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.06/+0.71/-0.11/+0.13
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.115; a x1.25: +0.140; win other: -0.041

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.054)

- H0 2023-02-10..2023-07-31: uplift -0.049 -> FAIL
- Alternating months: odd-selected ON_w2_a0.5_sg+1 read on even -0.175; even-selected ON_w2_a0.25_sg+1 read on odd +0.062 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Overnight signed volume (tick rule) accumulated from 18:00 ET; multiplier on first-RTH-hour entries.

DONE D34