# REPORT K10
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell s=100, d=5, m=0.5; all-in Sharpe uplift clean/H1/H2/all +0.18/+0.03/-0.12/+0.09. Runtime 26.6 min, 6-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

K10 round-number level-ahead conditioning of pair entries: entries with a multiple of s points within d points ahead in the trade direction get multiplier m (18 cells).


## Clean-only selection grid

|   s |   d |     m |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|----:|----:|------:|---------------:|----------------:|----------:|------------:|:-----------|
| 100 |   5 | 0.500 |          1.637 |           0.177 |     0.082 | 1500043.680 | True       |
| 100 |   5 | 0.000 |          1.594 |           0.134 |     0.114 | 1476432.320 | True       |
| 250 |   5 | 0.500 |          1.562 |           0.102 |     0.030 | 1445870.560 | False      |
| 100 |  10 | 0.500 |          1.534 |           0.074 |     0.152 | 1394706.720 | True       |
| 500 |   5 | 0.500 |          1.526 |           0.066 |     0.011 | 1385410.080 | False      |
| 250 |   5 | 0.000 |          1.491 |           0.031 |     0.040 | 1371691.200 | False      |
| 500 |   5 | 0.000 |          1.487 |           0.027 |     0.017 | 1354622.400 | False      |
| 500 |  10 | 0.500 |          1.484 |           0.024 |     0.028 | 1351973.280 | False      |
| 250 |  10 | 0.500 |          1.483 |           0.023 |     0.063 | 1389189.280 | True       |
| 100 |  10 | 0.000 |          1.473 |           0.013 |     0.224 | 1352009.280 | True       |
| 500 |  10 | 0.000 |          1.373 |          -0.087 |     0.043 | 1266573.440 | False      |
| 250 |  10 | 0.000 |          1.304 |          -0.156 |     0.099 | 1262368.960 | True       |
| 100 |  20 | 0.500 |          1.285 |          -0.175 |     0.302 | 1112785.440 | True       |
| 500 |  20 | 0.500 |          1.271 |          -0.189 |     0.064 | 1189585.280 | True       |
| 250 |  20 | 0.500 |          1.231 |          -0.228 |     0.121 | 1113451.360 | True       |
| 100 |  20 | 0.000 |          1.113 |          -0.347 |     0.374 |  933876.800 | True       |
| 250 |  20 | 0.000 |          1.098 |          -0.362 |     0.168 | 1022889.600 | True       |
| 500 |  20 | 0.000 |          1.064 |          -0.396 |     0.084 | 1009327.680 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.64 |
| clean | Sortino | 2.78 | 3.14 |
| clean | MAR | 4.75 | 5.46 |
| clean | net $ | 1,329,958.72 | 1,500,043.68 |
| clean | maxDD $ | 280,109.76 | 274,567.68 |
| clean | worst wk $ | -81,873.92 | -78,083.20 |
| clean | CVaR5 $ | -78,735.52 | -77,708.51 |
| clean | CVaR10 $ | -78,008.81 | -77,430.63 |
| clean | % neg wk | 42.86 | 40.00 |
| H1 | weekly Sharpe | 2.83 | 2.86 |
| H1 | Sortino | 6.09 | 5.79 |
| H1 | MAR | 3.91 | 3.73 |
| H1 | net $ | 593,797.44 | 614,912.96 |
| H1 | maxDD $ | 151,712.64 | 164,709.60 |
| H1 | worst wk $ | -78,287.36 | -81,113.12 |
| H1 | CVaR5 $ | -77,609.92 | -79,512.80 |
| H1 | CVaR10 $ | -66,029.97 | -78,614.40 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 2.18 |
| H2 | Sortino | 4.69 | 4.58 |
| H2 | MAR | 3.50 | 3.15 |
| H2 | net $ | 761,254.40 | 681,327.84 |
| H2 | maxDD $ | 217,425.28 | 216,301.12 |
| H2 | worst wk $ | -82,524.48 | -78,026.40 |
| H2 | CVaR5 $ | -81,088.96 | -77,736.40 |
| H2 | CVaR10 $ | -79,185.12 | -73,076.20 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.95 |
| all | Sortino | 3.63 | 3.82 |
| all | MAR | 9.59 | 10.18 |
| all | net $ | 2,685,010.56 | 2,796,284.48 |
| all | maxDD $ | 280,109.76 | 274,567.68 |
| all | worst wk $ | -82,524.48 | -81,113.12 |
| all | CVaR5 $ | -79,220.34 | -78,159.84 |
| all | CVaR10 $ | -78,243.12 | -77,673.27 |
| all | % neg wk | 42.86 | 39.88 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.177 / +0.033 / -0.116
- [PASS] 3 worst week not worse (all-in): -81,113 vs baseline -82,524
- [FAIL] 4 matched family null p95: real +0.092 vs p95 +0.118 (median -0.074, rank 0.90, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.138, +0.334]
- [FAIL] 5 plateau: 25% of 4 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.296 / +0.004 / -0.530
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'s': 100, 'd': 3.75, 'm': 0.5}: +0.065
- {'s': 100, 'd': 6.25, 'm': 0.5}: +0.166
- {'s': 100, 'd': 5, 'm': 0.375}: -0.016
- {'s': 100, 'd': 5, 'm': 0.625}: +0.018


DONE K10