# REPORT RX9
**Verdict: NO** (3/6 measured gates, replication 2/2 available; D1-harness class NO). Selected cell RW5xRW8: all-in weekly Sharpe uplift clean/H1/H2/all +0.23/+0.39/-0.15/+0.20. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

RX9 RW5 (K4 modulator) x RW8 (ER240 tilt) combined, both a=0.25 (single pre-declared cell).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| RW5xRW8 | +0.229 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.69 |
| clean | Sortino | 2.78 | 3.25 |
| clean | MAR | 4.75 | 4.01 |
| clean | net $ | 1,329,958.72 | 1,620,177.67 |
| clean | maxDD $ | 280,109.76 | 404,406.04 |
| clean | worst wk $ | -81,873.92 | -79,350.13 |
| clean | CVaR5 $ | -78,735.52 | -78,148.55 |
| clean | CVaR10 $ | -78,008.81 | -77,769.17 |
| clean | % neg wk | 42.86 | 42.86 |
| H1 | weekly Sharpe | 2.83 | 3.22 |
| H1 | Sortino | 6.09 | 8.11 |
| H1 | MAR | 3.91 | 6.00 |
| H1 | net $ | 593,797.44 | 856,363.50 |
| H1 | maxDD $ | 151,712.64 | 142,691.24 |
| H1 | worst wk $ | -78,287.36 | -77,825.64 |
| H1 | CVaR5 $ | -77,609.92 | -77,730.87 |
| H1 | CVaR10 $ | -66,029.97 | -77,619.43 |
| H1 | % neg wk | 39.29 | 32.14 |
| H2 | weekly Sharpe | 2.30 | 2.15 |
| H2 | Sortino | 4.69 | 4.38 |
| H2 | MAR | 3.50 | 3.49 |
| H2 | net $ | 761,254.40 | 762,446.30 |
| H2 | maxDD $ | 217,425.28 | 218,699.54 |
| H2 | worst wk $ | -82,524.48 | -78,166.53 |
| H2 | CVaR5 $ | -81,088.96 | -78,033.24 |
| H2 | CVaR10 $ | -79,185.12 | -77,562.37 |
| H2 | % neg wk | 44.44 | 38.89 |
| all | weekly Sharpe | 1.86 | 2.06 |
| all | Sortino | 3.63 | 4.16 |
| all | MAR | 9.59 | 8.01 |
| all | net $ | 2,685,010.56 | 3,238,987.46 |
| all | maxDD $ | 280,109.76 | 404,406.04 |
| all | worst wk $ | -82,524.48 | -79,350.13 |
| all | CVaR5 $ | -79,220.34 | -78,098.26 |
| all | CVaR10 $ | -78,243.12 | -77,740.37 |
| all | % neg wk | 42.86 | 40.48 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.229 / +0.390 / -0.145
- [PASS] 3 worst week not worse (all-in): -79,350 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.204 vs p95 +0.113 (median -0.180, rank 0.99, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.307, +0.726]
- [PASS] 5 plateau >=75% of neighbours keep >=75%: 75% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.246 / +0.472 / -0.608
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.71/+0.81/+0.09/+0.60
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): RW5 alone: +0.468; RW8 alone: +0.433; both a x0.75: +0.186; both a x1.25: +0.127

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.102)

- H0 2023-02-10..2023-07-31: uplift +0.285 -> PASS
- Alternating months: odd-selected RW5xRW8 read on even +0.273; even-selected RW5xRW8 read on odd +0.112 -> PASS
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Daily K4 probability file plus the in-strategy ER240 percentile; product multiplier clipped to 0.5-1.5.

DONE RX9