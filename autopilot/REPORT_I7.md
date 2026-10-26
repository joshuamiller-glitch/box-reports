# REPORT I7
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell key=bookside, W=26, m=0.5; all-in Sharpe uplift clean/H1/H2/all +0.33/-0.20/+0.12/+0.22. Runtime 13.1 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

I7 walk-forward side / book x side size tilt (8 cells): buckets with negative trailing mean per trade get multiplier m.


## Clean-only selection grid

| key      |   W |     m |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|:---------|----:|------:|---------------:|----------------:|----------:|------------:|:-----------|
| bookside |  26 | 0.500 |          1.786 |           0.326 |     0.380 | 1544958.560 | True       |
| bookside |  26 | 0.000 |          1.529 |           0.069 |     0.384 | 1213548.800 | True       |
| bookside |  13 | 0.000 |          1.208 |          -0.252 |     0.463 |  904303.040 | True       |
| side     |  26 | 0.000 |          1.203 |          -0.257 |     0.343 |  974500.160 | True       |
| side     |  26 | 0.500 |          1.169 |          -0.291 |     0.366 | 1023705.280 | True       |
| side     |  13 | 0.500 |          0.924 |          -0.536 |     0.326 |  786428.000 | True       |
| bookside |  13 | 0.500 |          0.832 |          -0.628 |     0.483 |  689074.560 | True       |
| side     |  13 | 0.000 |          0.737 |          -0.723 |     0.312 |  573562.240 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.79 |
| clean | Sortino | 2.78 | 3.38 |
| clean | MAR | 4.75 | 4.84 |
| clean | net $ | 1,329,958.72 | 1,544,958.56 |
| clean | maxDD $ | 280,109.76 | 319,303.36 |
| clean | worst wk $ | -81,873.92 | -82,355.04 |
| clean | CVaR5 $ | -78,735.52 | -79,266.99 |
| clean | CVaR10 $ | -78,008.81 | -78,321.08 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.63 |
| H1 | Sortino | 6.09 | 6.07 |
| H1 | MAR | 3.91 | 3.78 |
| H1 | net $ | 593,797.44 | 615,278.24 |
| H1 | maxDD $ | 151,712.64 | 162,596.00 |
| H1 | worst wk $ | -78,287.36 | -77,112.48 |
| H1 | CVaR5 $ | -77,609.92 | -77,022.48 |
| H1 | CVaR10 $ | -66,029.97 | -68,617.65 |
| H1 | % neg wk | 39.29 | 46.43 |
| H2 | weekly Sharpe | 2.30 | 2.42 |
| H2 | Sortino | 4.69 | 4.67 |
| H2 | MAR | 3.50 | 3.56 |
| H2 | net $ | 761,254.40 | 732,362.40 |
| H2 | maxDD $ | 217,425.28 | 205,775.04 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -80,980.24 |
| H2 | CVaR10 $ | -79,185.12 | -79,201.32 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 2.07 |
| all | Sortino | 3.63 | 4.05 |
| all | MAR | 9.59 | 9.06 |
| all | net $ | 2,685,010.56 | 2,892,599.20 |
| all | maxDD $ | 280,109.76 | 319,303.36 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -79,457.78 |
| all | CVaR10 $ | -78,243.12 | -78,375.42 |
| all | % neg wk | 42.86 | 42.86 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.326 / -0.198 / +0.120
- [PASS] 3 worst week not worse (all-in): -82,524 vs baseline -82,524
- [FAIL] 4 matched family null p95: real +0.216 vs p95 +0.360 (median +0.018, rank 0.83, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.197, +0.662]
- [FAIL] 5 plateau: 25% of 4 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.243 / -1.074 / +0.086
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'key': 'bookside', 'W': 20, 'm': 0.5}: -0.293
- {'key': 'bookside', 'W': 32, 'm': 0.5}: -0.016
- {'key': 'bookside', 'W': 26, 'm': 0.375}: +0.008
- {'key': 'bookside', 'W': 26, 'm': 0.625}: +0.297


DONE I7