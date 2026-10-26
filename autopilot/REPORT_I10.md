# REPORT I10
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell a=0.0, b=0.5; all-in Sharpe uplift clean/H1/H2/all +0.25/-0.21/-0.98/-0.11. Runtime 17.9 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

I10 prior-week-conditioned pair size (5 cells): size 1+a after a losing week, 1-b after a winning week (previous week's net from the baseline live run, causal).


## Clean-only selection grid

|     a |     b |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|------:|------:|---------------:|----------------:|----------:|------------:|:-----------|
| 0.000 | 0.500 |          1.714 |           0.255 |     0.905 | 1332472.320 | True       |
| 0.000 | 0.250 |          1.474 |           0.014 |     0.705 | 1296388.880 | True       |
| 0.250 | 0.250 |          1.186 |          -0.273 |     1.141 | 1134578.960 | True       |
| 0.250 | 0.000 |          1.185 |          -0.275 |     0.437 | 1168148.800 | True       |
| 0.500 | 0.000 |          0.825 |          -0.634 |     0.437 |  794046.560 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.71 |
| clean | Sortino | 2.78 | 3.56 |
| clean | MAR | 4.75 | 7.16 |
| clean | net $ | 1,329,958.72 | 1,332,472.32 |
| clean | maxDD $ | 280,109.76 | 186,044.16 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -77,966.00 |
| clean | CVaR10 $ | -78,008.81 | -66,228.26 |
| clean | % neg wk | 42.86 | 44.76 |
| H1 | weekly Sharpe | 2.83 | 2.61 |
| H1 | Sortino | 6.09 | 5.03 |
| H1 | MAR | 3.91 | 2.91 |
| H1 | net $ | 593,797.44 | 493,735.52 |
| H1 | maxDD $ | 151,712.64 | 169,756.80 |
| H1 | worst wk $ | -78,287.36 | -78,287.36 |
| H1 | CVaR5 $ | -77,609.92 | -78,183.04 |
| H1 | CVaR10 $ | -66,029.97 | -71,217.17 |
| H1 | % neg wk | 39.29 | 25.00 |
| H2 | weekly Sharpe | 2.30 | 1.31 |
| H2 | Sortino | 4.69 | 2.43 |
| H2 | MAR | 3.50 | 1.93 |
| H2 | net $ | 761,254.40 | 427,736.80 |
| H2 | maxDD $ | 217,425.28 | 221,440.16 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -80,117.68 |
| H2 | CVaR10 $ | -79,185.12 | -78,699.48 |
| H2 | % neg wk | 44.44 | 50.00 |
| all | weekly Sharpe | 1.86 | 1.75 |
| all | Sortino | 3.63 | 3.45 |
| all | MAR | 9.59 | 10.18 |
| all | net $ | 2,685,010.56 | 2,253,944.64 |
| all | maxDD $ | 280,109.76 | 221,440.16 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -78,638.92 |
| all | CVaR10 $ | -78,243.12 | -73,871.41 |
| all | % neg wk | 42.86 | 42.86 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.255 / -0.214 / -0.980
- [PASS] 3 worst week not worse (all-in): -82,524 vs baseline -82,524
- [FAIL] 4 matched family null p95: real -0.105 vs p95 +0.193 (median -0.143, rank 0.54, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.531, +0.326]
- [FAIL] 5 plateau: 0% of 2 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.388 / -0.246 / -0.980
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'a': 0.0, 'b': 0.375}: -0.182
- {'a': 0.0, 'b': 0.625}: -0.150


DONE I10