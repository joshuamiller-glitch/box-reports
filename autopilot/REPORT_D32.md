# REPORT D32
**Verdict: NO** (1/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell AVGSZ_ALL_a0.25_sg-1: all-in weekly Sharpe uplift clean/H1/H2/all -0.22/-0.40/-0.46/-0.30. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

D32 trailing 24h average trade size regime tilt.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| AVGSZ_ALL_a0.25_sg-1 | -0.220 | 1.000 |
| AVGSZ_ALL_a0.5_sg+1 | -0.230 | 1.000 |
| AVGSZ_ALL_a0.25_sg+1 | -0.298 | 1.000 |
| AVGSZ_ALL_a0.5_sg-1 | -0.309 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.24 |
| clean | Sortino | 2.78 | 2.27 |
| clean | MAR | 4.75 | 2.94 |
| clean | net $ | 1,329,958.72 | 1,223,837.04 |
| clean | maxDD $ | 280,109.76 | 416,891.30 |
| clean | worst wk $ | -81,873.92 | -81,405.34 |
| clean | CVaR5 $ | -78,735.52 | -78,985.77 |
| clean | CVaR10 $ | -78,008.81 | -78,351.42 |
| clean | % neg wk | 42.86 | 44.76 |
| H1 | weekly Sharpe | 2.83 | 2.43 |
| H1 | Sortino | 6.09 | 4.96 |
| H1 | MAR | 3.91 | 3.09 |
| H1 | net $ | 593,797.44 | 537,352.67 |
| H1 | maxDD $ | 151,712.64 | 173,825.65 |
| H1 | worst wk $ | -78,287.36 | -77,819.16 |
| H1 | CVaR5 $ | -77,609.92 | -77,626.33 |
| H1 | CVaR10 $ | -66,029.97 | -77,442.13 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 1.84 |
| H2 | Sortino | 4.69 | 3.94 |
| H2 | MAR | 3.50 | 2.76 |
| H2 | net $ | 761,254.40 | 687,162.45 |
| H2 | maxDD $ | 217,425.28 | 248,551.37 |
| H2 | worst wk $ | -82,524.48 | -79,834.02 |
| H2 | CVaR5 $ | -81,088.96 | -79,333.58 |
| H2 | CVaR10 $ | -79,185.12 | -78,750.71 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.55 |
| all | Sortino | 3.63 | 2.97 |
| all | MAR | 9.59 | 5.87 |
| all | net $ | 2,685,010.56 | 2,448,352.16 |
| all | maxDD $ | 280,109.76 | 416,891.30 |
| all | worst wk $ | -82,524.48 | -81,405.34 |
| all | CVaR5 $ | -79,220.34 | -79,017.34 |
| all | CVaR10 $ | -78,243.12 | -78,380.87 |
| all | % neg wk | 42.86 | 43.45 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.220 / -0.399 / -0.458
- [PASS] 3 worst week not worse (all-in): -81,405 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.303 vs p95 +0.024 (median -0.258, rank 0.40, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.767, +0.156]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.024 / -0.616 / -0.501
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all -0.07/-0.06/-0.22/-0.10
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: -0.168; a x1.25: -0.190

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.152)

- H0 2023-02-10..2023-07-31: uplift -0.557 -> FAIL
- Alternating months: odd-selected AVGSZ_ALL_a0.25_sg-1 read on even -0.363; even-selected AVGSZ_ALL_a0.25_sg+1 read on odd -0.510 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Trailing 24-hour average trade size from the NT8 tick stream; multiplier 0.5-1.5.

DONE D32