# REPORT L2
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell delta=0.03, a=0.25, b=0.25; all-in Sharpe uplift clean/H1/H2/all +0.17/-0.12/-0.65/-0.05. Runtime 19.7 min, 6-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

L2 K4-direction agreement tilt of the pair (8 cells): pair rows agreeing with the daily GBM index direction get 1+a, disagreeing 1-b.


## Clean-only selection grid

|   delta |     a |     b |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|--------:|------:|------:|---------------:|----------------:|----------:|------------:|:-----------|
|   0.030 | 0.250 | 0.250 |          1.634 |           0.174 |     0.700 | 1522381.520 | True       |
|   0.060 | 0.250 | 0.250 |          1.478 |           0.018 |     0.245 | 1355910.560 | True       |
|   0.060 | 0.500 | 0.000 |          1.472 |           0.012 |     0.139 | 1382184.960 | True       |
|   0.030 | 0.500 | 0.000 |          1.439 |          -0.020 |     0.420 | 1444374.720 | True       |
|   0.030 | 0.000 | 1.000 |          1.140 |          -0.320 |     0.460 |  974599.040 | True       |
|   0.060 | 0.000 | 0.500 |          1.118 |          -0.342 |     0.170 | 1018048.160 | True       |
|   0.030 | 0.000 | 0.500 |          1.011 |          -0.448 |     0.474 |  920788.960 | True       |
|   0.060 | 0.000 | 1.000 |          0.864 |          -0.596 |     0.172 |  789563.200 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.63 |
| clean | Sortino | 2.78 | 3.17 |
| clean | MAR | 4.75 | 5.70 |
| clean | net $ | 1,329,958.72 | 1,522,381.52 |
| clean | maxDD $ | 280,109.76 | 266,923.68 |
| clean | worst wk $ | -81,873.92 | -80,177.28 |
| clean | CVaR5 $ | -78,735.52 | -79,044.16 |
| clean | CVaR10 $ | -78,008.81 | -78,336.64 |
| clean | % neg wk | 42.86 | 39.05 |
| H1 | weekly Sharpe | 2.83 | 2.71 |
| H1 | Sortino | 6.09 | 5.47 |
| H1 | MAR | 3.91 | 4.96 |
| H1 | net $ | 593,797.44 | 618,640.24 |
| H1 | maxDD $ | 151,712.64 | 124,812.64 |
| H1 | worst wk $ | -78,287.36 | -77,681.20 |
| H1 | CVaR5 $ | -77,609.92 | -77,536.12 |
| H1 | CVaR10 $ | -66,029.97 | -77,303.87 |
| H1 | % neg wk | 39.29 | 28.57 |
| H2 | weekly Sharpe | 2.30 | 1.64 |
| H2 | Sortino | 4.69 | 3.23 |
| H2 | MAR | 3.50 | 2.67 |
| H2 | net $ | 761,254.40 | 569,994.64 |
| H2 | maxDD $ | 217,425.28 | 213,150.08 |
| H2 | worst wk $ | -82,524.48 | -79,801.12 |
| H2 | CVaR5 $ | -81,088.96 | -79,727.28 |
| H2 | CVaR10 $ | -79,185.12 | -79,244.22 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.81 |
| all | Sortino | 3.63 | 3.52 |
| all | MAR | 9.59 | 10.16 |
| all | net $ | 2,685,010.56 | 2,711,016.40 |
| all | maxDD $ | 280,109.76 | 266,923.68 |
| all | worst wk $ | -82,524.48 | -80,177.28 |
| all | CVaR5 $ | -79,220.34 | -79,255.87 |
| all | CVaR10 $ | -78,243.12 | -78,456.01 |
| all | % neg wk | 42.86 | 38.10 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.174 / -0.120 / -0.654
- [PASS] 3 worst week not worse (all-in): -80,177 vs baseline -82,524
- [FAIL] 4 matched family null p95: real -0.046 vs p95 +0.208 (median -0.071, rank 0.55, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.580, +0.467]
- [FAIL] 5 plateau: 0% of 6 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.296 / -0.180 / -0.863
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'delta': 0.0225, 'a': 0.25, 'b': 0.25}: +0.041
- {'delta': 0.0375, 'a': 0.25, 'b': 0.25}: -0.052
- {'delta': 0.03, 'a': 0.1875, 'b': 0.25}: -0.065
- {'delta': 0.03, 'a': 0.3125, 'b': 0.25}: -0.040
- {'delta': 0.03, 'a': 0.25, 'b': 0.1875}: +0.215
- {'delta': 0.03, 'a': 0.25, 'b': 0.3125}: -0.400


DONE L2