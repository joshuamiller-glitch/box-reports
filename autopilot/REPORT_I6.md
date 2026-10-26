# REPORT I6
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell key=hourbook, q=0.33, m=0.5; all-in Sharpe uplift clean/H1/H2/all +0.29/-0.20/+0.02/+0.18. Runtime 21.1 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

I6 walk-forward hour/dow/hour x book size tilt of the pair (12 cells): each month the worst-trailing buckets get multiplier m.


## Clean-only selection grid

| key      |     q |     m |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|:---------|------:|------:|---------------:|----------------:|----------:|------------:|:-----------|
| hourbook | 0.330 | 0.500 |          1.749 |           0.289 |     0.383 | 1512151.360 | True       |
| hourbook | 0.330 | 0.000 |          1.616 |           0.156 |     0.431 | 1278106.880 | True       |
| hourbook | 0.200 | 0.500 |          1.489 |           0.029 |     0.214 | 1291667.040 | True       |
| hourbook | 0.200 | 0.000 |          1.366 |          -0.094 |     0.284 | 1123742.080 | True       |
| dow      | 0.200 | 0.500 |          1.212 |          -0.248 |     0.323 | 1063569.920 | True       |
| dow      | 0.200 | 0.000 |          1.147 |          -0.313 |     0.248 |  990123.840 | True       |
| dow      | 0.330 | 0.500 |          1.095 |          -0.365 |     0.623 |  865664.960 | True       |
| hour     | 0.330 | 0.500 |          0.995 |          -0.465 |     0.374 |  887341.760 | True       |
| hour     | 0.330 | 0.000 |          0.871 |          -0.588 |     0.428 |  722478.080 | True       |
| hour     | 0.200 | 0.500 |          0.801 |          -0.659 |     0.202 |  736515.040 | True       |
| dow      | 0.330 | 0.000 |          0.687 |          -0.773 |     0.452 |  502195.520 | True       |
| hour     | 0.200 | 0.000 |          0.525 |          -0.935 |     0.261 |  464913.280 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.75 |
| clean | Sortino | 2.78 | 3.31 |
| clean | MAR | 4.75 | 6.69 |
| clean | net $ | 1,329,958.72 | 1,512,151.36 |
| clean | maxDD $ | 280,109.76 | 225,958.08 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,460.32 |
| clean | CVaR10 $ | -78,008.81 | -77,853.02 |
| clean | % neg wk | 42.86 | 40.00 |
| H1 | weekly Sharpe | 2.83 | 2.63 |
| H1 | Sortino | 6.09 | 6.36 |
| H1 | MAR | 3.91 | 3.71 |
| H1 | net $ | 593,797.44 | 608,420.80 |
| H1 | maxDD $ | 151,712.64 | 164,064.00 |
| H1 | worst wk $ | -78,287.36 | -77,345.92 |
| H1 | CVaR5 $ | -77,609.92 | -77,109.20 |
| H1 | CVaR10 $ | -66,029.97 | -65,953.60 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 2.32 |
| H2 | Sortino | 4.69 | 4.50 |
| H2 | MAR | 3.50 | 3.64 |
| H2 | net $ | 761,254.40 | 727,712.48 |
| H2 | maxDD $ | 217,425.28 | 199,917.92 |
| H2 | worst wk $ | -82,524.48 | -78,199.36 |
| H2 | CVaR5 $ | -81,088.96 | -77,915.12 |
| H2 | CVaR10 $ | -79,185.12 | -77,613.72 |
| H2 | % neg wk | 44.44 | 33.33 |
| all | weekly Sharpe | 1.86 | 2.03 |
| all | Sortino | 3.63 | 3.99 |
| all | MAR | 9.59 | 12.61 |
| all | net $ | 2,685,010.56 | 2,848,284.64 |
| all | maxDD $ | 280,109.76 | 225,958.08 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -78,240.48 |
| all | CVaR10 $ | -78,243.12 | -77,716.84 |
| all | % neg wk | 42.86 | 38.10 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.289 / -0.198 / +0.020
- [PASS] 3 worst week not worse (all-in): -81,874 vs baseline -82,524
- [FAIL] 4 matched family null p95: real +0.178 vs p95 +0.193 (median -0.155, rank 0.94, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.279, +0.638]
- [FAIL] 5 plateau: 25% of 4 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.433 / -0.386 / -0.341
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'key': 'hourbook', 'q': 0.2475, 'm': 0.5}: -0.044
- {'key': 'hourbook', 'q': 0.4125, 'm': 0.5}: +0.260
- {'key': 'hourbook', 'q': 0.33, 'm': 0.375}: +0.066
- {'key': 'hourbook', 'q': 0.33, 'm': 0.625}: -0.013


DONE I6