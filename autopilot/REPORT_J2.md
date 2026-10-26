# REPORT J2
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell cls=am, tail=either, band=0.8, m=0.5; all-in Sharpe uplift clean/H1/H2/all +0.19/+1.15/-0.70/+0.10. Runtime 26.1 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

J2 COT equity-index crowding size tilt of the pair (24 cells): NQ/ES basket percentile of class net/OI over 156 weeks, effective Tuesday after the as-of date.


## Clean-only selection grid

| cls   | tail   |   band |     m |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|:------|:-------|-------:|------:|---------------:|----------------:|----------:|------------:|:-----------|
| am    | either |  0.800 | 0.500 |          1.651 |           0.191 |     0.842 | 1233794.720 | True       |
| am    | high   |  0.800 | 0.500 |          1.651 |           0.191 |     0.842 | 1233794.720 | True       |
| lev   | low    |  0.900 | 0.500 |          1.617 |           0.157 |     0.022 | 1464152.960 | False      |
| lev   | low    |  0.900 | 0.000 |          1.584 |           0.124 |     0.019 | 1445147.520 | False      |
| lev   | either |  0.900 | 0.000 |          1.522 |           0.062 |     0.066 | 1302621.760 | True       |
| lev   | low    |  0.800 | 0.500 |          1.502 |           0.042 |     0.143 | 1310344.320 | True       |
| lev   | low    |  0.800 | 0.000 |          1.467 |           0.008 |     0.094 | 1235352.960 | True       |
| lev   | either |  0.900 | 0.500 |          1.467 |           0.007 |     0.087 | 1283473.440 | True       |
| am    | low    |  0.800 | 0.000 |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
| am    | low    |  0.900 | 0.500 |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
| am    | low    |  0.800 | 0.500 |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
| am    | low    |  0.900 | 0.000 |          1.460 |           0.000 |     0.000 | 1329958.720 | False      |
| lev   | high   |  0.900 | 0.000 |          1.391 |          -0.069 |     0.047 | 1187432.960 | False      |
| lev   | either |  0.800 | 0.500 |          1.385 |          -0.075 |     0.266 | 1132544.000 | True       |
| am    | high   |  0.900 | 0.500 |          1.343 |          -0.117 |     0.481 | 1101488.480 | True       |
| am    | either |  0.900 | 0.500 |          1.343 |          -0.117 |     0.481 | 1101488.480 | True       |
| lev   | high   |  0.800 | 0.500 |          1.341 |          -0.118 |     0.123 | 1152158.400 | True       |
| lev   | high   |  0.900 | 0.500 |          1.306 |          -0.154 |     0.066 | 1149279.200 | True       |
| lev   | either |  0.800 | 0.000 |          1.287 |          -0.173 |     0.162 |  953798.080 | True       |
| lev   | high   |  0.800 | 0.000 |          1.279 |          -0.181 |     0.068 | 1048403.840 | True       |
| am    | either |  0.800 | 0.000 |          0.972 |          -0.488 |     0.589 |  634316.480 | True       |
| am    | high   |  0.800 | 0.000 |          0.972 |          -0.488 |     0.589 |  634316.480 | True       |
| am    | high   |  0.900 | 0.000 |          0.813 |          -0.647 |     0.327 |  620805.440 | True       |
| am    | either |  0.900 | 0.000 |          0.813 |          -0.647 |     0.327 |  620805.440 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.65 |
| clean | Sortino | 2.78 | 3.12 |
| clean | MAR | 4.75 | 4.40 |
| clean | net $ | 1,329,958.72 | 1,233,794.72 |
| clean | maxDD $ | 280,109.76 | 280,109.76 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,399.81 |
| clean | CVaR10 $ | -78,008.81 | -72,730.89 |
| clean | % neg wk | 42.86 | 38.10 |
| H1 | weekly Sharpe | 2.83 | 3.97 |
| H1 | Sortino | 6.09 | 9.83 |
| H1 | MAR | 3.91 | 4.44 |
| H1 | net $ | 593,797.44 | 673,798.40 |
| H1 | maxDD $ | 151,712.64 | 151,712.64 |
| H1 | worst wk $ | -78,287.36 | -57,285.44 |
| H1 | CVaR5 $ | -77,609.92 | -50,077.76 |
| H1 | CVaR10 $ | -66,029.97 | -47,341.87 |
| H1 | % neg wk | 39.29 | 25.00 |
| H2 | weekly Sharpe | 2.30 | 1.60 |
| H2 | Sortino | 4.69 | 3.02 |
| H2 | MAR | 3.50 | 2.25 |
| H2 | net $ | 761,254.40 | 502,404.16 |
| H2 | maxDD $ | 217,425.28 | 223,339.84 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -81,088.96 |
| H2 | CVaR10 $ | -79,185.12 | -79,176.16 |
| H2 | % neg wk | 44.44 | 50.00 |
| all | weekly Sharpe | 1.86 | 1.95 |
| all | Sortino | 3.63 | 3.77 |
| all | MAR | 9.59 | 8.60 |
| all | net $ | 2,685,010.56 | 2,409,997.28 |
| all | maxDD $ | 280,109.76 | 280,109.76 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -78,894.33 |
| all | CVaR10 $ | -78,243.12 | -72,667.68 |
| all | % neg wk | 42.86 | 38.69 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.191 / +1.146 / -0.696
- [PASS] 3 worst week not worse (all-in): -82,524 vs baseline -82,524
- [FAIL] 4 matched family null p95: real +0.098 vs p95 +0.230 (median -0.085, rank 0.84, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.276, +0.503]
- [FAIL] 5 plateau: 50% of 4 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.195 / +0.982 / -0.657
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'cls': 'am', 'tail': 'either', 'band': 0.85, 'm': 0.5}: +0.023
- {'cls': 'am', 'tail': 'either', 'band': 0.75, 'm': 0.5}: +0.080
- {'cls': 'am', 'tail': 'either', 'band': 0.8, 'm': 0.375}: -0.012
- {'cls': 'am', 'tail': 'either', 'band': 0.8, 'm': 0.625}: +0.182


DONE J2