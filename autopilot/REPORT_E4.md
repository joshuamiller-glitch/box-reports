# REPORT E4
**Verdict: NO** (2/6 measured gates, replication 1/2 available; D1-harness class NO). Selected cell n2_W120_pair_rth: all-in weekly Sharpe uplift clean/H1/H2/all +0.28/-0.02/-0.45/+0.10. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

E4 whipsaw-halt neighbourhood (72 cells): after n consecutive stop-outs halt entries for W minutes or until the session ends, per book or combined, in Globex, RTH or both. Refines H11-B and G0a.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| n2_W120_pair_rth | +0.281 | 0.069 |
| n2_W60_pair_rth | +0.259 | 0.046 |
| n2_Wsess_pair_rth | +0.233 | 0.098 |
| n3_Wsess_pair_rth | +0.214 | 0.054 |
| n2_W30_pair_rth | +0.176 | 0.030 |
| n2_W30_book_rth | +0.162 | 0.014 |
| n2_Wsess_book_rth | +0.135 | 0.059 |
| n3_W60_pair_rth | +0.109 | 0.022 |
| n2_W120_book_rth | +0.105 | 0.038 |
| n3_W120_pair_rth | +0.097 | 0.031 |
| n2_W60_book_rth | +0.044 | 0.025 |
| n2_W30_book_both | +0.043 | 0.030 |
| n3_W30_pair_rth | +0.039 | 0.014 |
| n3_W30_book_both | +0.033 | 0.011 |
| n4_Wsess_pair_globex | +0.026 | 0.041 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.74 |
| clean | Sortino | 2.78 | 3.40 |
| clean | MAR | 4.75 | 5.37 |
| clean | net $ | 1,329,958.72 | 1,561,371.84 |
| clean | maxDD $ | 280,109.76 | 290,947.52 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -79,002.35 |
| clean | CVaR10 $ | -78,008.81 | -78,238.17 |
| clean | % neg wk | 42.86 | 40.95 |
| H1 | weekly Sharpe | 2.83 | 2.81 |
| H1 | Sortino | 6.09 | 6.92 |
| H1 | MAR | 3.91 | 4.44 |
| H1 | net $ | 593,797.44 | 664,817.28 |
| H1 | maxDD $ | 151,712.64 | 149,722.56 |
| H1 | worst wk $ | -78,287.36 | -77,975.68 |
| H1 | CVaR5 $ | -77,609.92 | -77,454.08 |
| H1 | CVaR10 $ | -66,029.97 | -66,564.37 |
| H1 | % neg wk | 39.29 | 42.86 |
| H2 | weekly Sharpe | 2.30 | 1.85 |
| H2 | Sortino | 4.69 | 3.65 |
| H2 | MAR | 3.50 | 2.83 |
| H2 | net $ | 761,254.40 | 614,919.36 |
| H2 | maxDD $ | 217,425.28 | 217,195.52 |
| H2 | worst wk $ | -82,524.48 | -79,653.44 |
| H2 | CVaR5 $ | -81,088.96 | -79,402.88 |
| H2 | CVaR10 $ | -79,185.12 | -78,417.52 |
| H2 | % neg wk | 44.44 | 47.22 |
| all | weekly Sharpe | 1.86 | 1.95 |
| all | Sortino | 3.63 | 3.92 |
| all | MAR | 9.59 | 9.77 |
| all | net $ | 2,685,010.56 | 2,841,108.48 |
| all | maxDD $ | 280,109.76 | 290,947.52 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -78,977.28 |
| all | CVaR10 $ | -78,243.12 | -78,200.73 |
| all | % neg wk | 42.86 | 42.86 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.281 / -0.022 / -0.446
- [PASS] 3 worst week not worse (all-in): -81,874 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real +0.095 vs p95 +0.491 (median +0.340, rank 0.01, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.138, +0.336]
- [PASS] 5 plateau >=75% of neighbours keep >=75%: 100% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.269 / -0.093 / -0.406
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.18/+0.59/-0.44/+0.12
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): n-1: +0.080; n+1: +0.114; W x0.75: +0.109; W x1.25: +0.072

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.048)

- H0 2023-02-10..2023-07-31: uplift +0.385 -> PASS
- Alternating months: odd-selected n3_W120_book_globex read on even +0.051; even-selected n3_W120_book_both read on odd -0.056 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. A DualStrat parameter set (consecutive-stop count n, halt window W or until session end, per book or combined, Globex/RTH scope); no extra contracts; reduces entries only.

DONE E4