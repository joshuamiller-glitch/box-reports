# REPORT RW11
**Verdict: NO** (3/6 measured gates, replication 0/2 available; D1-harness class SURVIVES). Selected cell BT_W26_pertrade_s0.5: all-in weekly Sharpe uplift clean/H1/H2/all -0.02/+0.33/+0.53/+0.14. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

R11 walk-forward ST/HM book tilt by trailing book performance (12 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| BT_W26_pertrade_s0.5 | -0.020 | 1.000 |
| BT_W26_pertrade_s0.25 | -0.049 | 1.000 |
| BT_W13_pertrade_s0.25 | -0.055 | 1.000 |
| BT_W8_pertrade_s0.25 | -0.093 | 1.000 |
| BT_W13_pertrade_s0.5 | -0.124 | 1.000 |
| BT_W26_sum_s0.25 | -0.141 | 1.000 |
| BT_W26_sum_s0.5 | -0.148 | 1.000 |
| BT_W13_sum_s0.5 | -0.157 | 1.000 |
| BT_W8_pertrade_s0.5 | -0.165 | 1.000 |
| BT_W13_sum_s0.25 | -0.190 | 1.000 |
| BT_W8_sum_s0.25 | -0.283 | 1.000 |
| BT_W8_sum_s0.5 | -0.418 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.44 |
| clean | Sortino | 2.78 | 2.71 |
| clean | MAR | 4.75 | 3.85 |
| clean | net $ | 1,329,958.72 | 1,385,816.64 |
| clean | maxDD $ | 280,109.76 | 359,547.04 |
| clean | worst wk $ | -81,873.92 | -80,498.56 |
| clean | CVaR5 $ | -78,735.52 | -78,746.37 |
| clean | CVaR10 $ | -78,008.81 | -78,218.33 |
| clean | % neg wk | 42.86 | 46.67 |
| H1 | weekly Sharpe | 2.83 | 3.16 |
| H1 | Sortino | 6.09 | 6.01 |
| H1 | MAR | 3.91 | 4.55 |
| H1 | net $ | 593,797.44 | 654,711.04 |
| H1 | maxDD $ | 151,712.64 | 144,022.40 |
| H1 | worst wk $ | -78,287.36 | -78,077.60 |
| H1 | CVaR5 $ | -77,609.92 | -77,957.36 |
| H1 | CVaR10 $ | -66,029.97 | -77,713.17 |
| H1 | % neg wk | 39.29 | 28.57 |
| H2 | weekly Sharpe | 2.30 | 2.82 |
| H2 | Sortino | 4.69 | 6.29 |
| H2 | MAR | 3.50 | 6.94 |
| H2 | net $ | 761,254.40 | 1,039,459.04 |
| H2 | maxDD $ | 217,425.28 | 149,779.04 |
| H2 | worst wk $ | -82,524.48 | -79,059.84 |
| H2 | CVaR5 $ | -81,088.96 | -78,724.32 |
| H2 | CVaR10 $ | -79,185.12 | -78,173.60 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 2.00 |
| all | Sortino | 3.63 | 3.92 |
| all | MAR | 9.59 | 8.57 |
| all | net $ | 2,685,010.56 | 3,079,986.72 |
| all | maxDD $ | 280,109.76 | 359,547.04 |
| all | worst wk $ | -82,524.48 | -80,498.56 |
| all | CVaR5 $ | -79,220.34 | -78,680.46 |
| all | CVaR10 $ | -78,243.12 | -78,177.10 |
| all | % neg wk | 42.86 | 42.86 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.020 / +0.328 / +0.525
- [PASS] 3 worst week not worse (all-in): -80,499 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.144 vs p95 -0.086 (median -0.500, rank 0.99, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.334, +0.650]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 3
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.104 / +0.226 / +0.626
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.15/+0.44/+0.68/+0.32
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): s x0.75: -0.010; s x1.25: -0.019; W 13: -0.080

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.072)

- H0 2023-02-10..2023-07-31: uplift -0.192 -> FAIL
- Alternating months: odd-selected BT_W26_pertrade_s0.5 read on even -0.008; even-selected BT_W26_pertrade_s0.5 read on odd +0.404 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Weekly file of per-book multipliers from the trailing book performance (computed from the strategy trade log).

DONE RW11