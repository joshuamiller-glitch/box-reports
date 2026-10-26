# REPORT B15
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell m=0.25, books=HM, kinds=all; all-in Sharpe uplift clean/H1/H2/all -0.05/-0.18/-0.34/-0.12. Runtime 1.6 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

B15 post-lock reduced-size continuation of the pair (8 cells). After the combined day lock fires (positions flattened as live), later entries that day trade at fraction m of size.


## Clean-only selection grid

|     m | books   | kinds   |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|------:|:--------|:--------|---------------:|----------------:|----------:|------------:|:-----------|
| 0.250 | HM      | all     |          1.412 |          -0.048 |     0.150 | 1284039.520 | True       |
| 0.250 | both    | all     |          1.388 |          -0.072 |     0.324 | 1279413.120 | True       |
| 0.250 | HM      | gb      |          1.381 |          -0.079 |     0.141 | 1250303.440 | True       |
| 0.500 | HM      | all     |          1.372 |          -0.088 |     0.151 | 1248531.520 | True       |
| 0.500 | both    | all     |          1.365 |          -0.095 |     0.328 | 1281982.880 | True       |
| 0.250 | both    | gb      |          1.345 |          -0.115 |     0.309 | 1230410.160 | True       |
| 0.500 | HM      | gb      |          1.310 |          -0.150 |     0.141 | 1181059.360 | True       |
| 0.500 | both    | gb      |          1.279 |          -0.181 |     0.312 | 1183976.960 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.41 |
| clean | Sortino | 2.78 | 2.65 |
| clean | MAR | 4.75 | 4.42 |
| clean | net $ | 1,329,958.72 | 1,284,039.52 |
| clean | maxDD $ | 280,109.76 | 290,304.16 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,651.31 |
| clean | CVaR10 $ | -78,008.81 | -77,939.24 |
| clean | % neg wk | 42.86 | 44.76 |
| H1 | weekly Sharpe | 2.83 | 2.65 |
| H1 | Sortino | 6.09 | 5.39 |
| H1 | MAR | 3.91 | 3.03 |
| H1 | net $ | 593,797.44 | 581,252.64 |
| H1 | maxDD $ | 151,712.64 | 191,835.68 |
| H1 | worst wk $ | -78,287.36 | -78,287.36 |
| H1 | CVaR5 $ | -77,609.92 | -78,004.72 |
| H1 | CVaR10 $ | -66,029.97 | -77,810.99 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 1.95 |
| H2 | Sortino | 4.69 | 3.81 |
| H2 | MAR | 3.50 | 2.80 |
| H2 | net $ | 761,254.40 | 679,414.16 |
| H2 | maxDD $ | 217,425.28 | 242,630.72 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -81,088.96 |
| H2 | CVaR10 $ | -79,185.12 | -79,755.20 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.73 |
| all | Sortino | 3.63 | 3.30 |
| all | MAR | 9.59 | 8.77 |
| all | net $ | 2,685,010.56 | 2,544,706.32 |
| all | maxDD $ | 280,109.76 | 290,304.16 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -79,387.89 |
| all | CVaR10 $ | -78,243.12 | -78,424.80 |
| all | % neg wk | 42.86 | 43.45 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.048 / -0.180 / -0.340
- [PASS] 3 worst week not worse (all-in): -82,524 vs baseline -82,524
- [FAIL] 4 matched family null p95: real -0.125 vs p95 +0.083 (median -0.045, rank 0.10, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.245, -0.013]
- [FAIL] 5 plateau: 0% of 2 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.040 / -0.192 / -0.358
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'m': 0.1875, 'books': 'HM', 'kinds': 'all'}: -0.112
- {'m': 0.3125, 'books': 'HM', 'kinds': 'all'}: -0.180


DONE B15