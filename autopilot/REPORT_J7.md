# REPORT J7
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell set=all10, m=1.5; all-in Sharpe uplift clean/H1/H2/all +0.22/-0.84/-0.55/-0.10. Runtime 10.8 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

J7 mega-cap earnings-reaction label pair size tilt (6 cells).


## Clean-only selection grid

| set   |     m |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|:------|------:|---------------:|----------------:|----------:|------------:|:-----------|
| all10 | 1.500 |          1.682 |           0.222 |     0.152 | 1627008.000 | True       |
| top5  | 1.500 |          1.548 |           0.088 |     0.069 | 1473512.320 | True       |
| top5  | 0.500 |          1.208 |          -0.252 |     0.105 | 1085935.040 | True       |
| all10 | 0.500 |          1.048 |          -0.411 |     0.225 |  905947.520 | True       |
| top5  | 0.000 |          0.922 |          -0.538 |     0.067 |  822559.680 | True       |
| all10 | 0.000 |          0.542 |          -0.918 |     0.150 |  452373.440 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.68 |
| clean | Sortino | 2.78 | 3.30 |
| clean | MAR | 4.75 | 5.15 |
| clean | net $ | 1,329,958.72 | 1,627,008.00 |
| clean | maxDD $ | 280,109.76 | 315,680.48 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -79,358.16 |
| clean | CVaR10 $ | -78,008.81 | -78,372.32 |
| clean | % neg wk | 42.86 | 42.86 |
| H1 | weekly Sharpe | 2.83 | 1.98 |
| H1 | Sortino | 6.09 | 4.00 |
| H1 | MAR | 3.91 | 2.74 |
| H1 | net $ | 593,797.44 | 481,326.72 |
| H1 | maxDD $ | 151,712.64 | 175,611.68 |
| H1 | worst wk $ | -78,287.36 | -79,776.64 |
| H1 | CVaR5 $ | -77,609.92 | -79,079.68 |
| H1 | CVaR10 $ | -66,029.97 | -78,635.25 |
| H1 | % neg wk | 39.29 | 42.86 |
| H2 | weekly Sharpe | 2.30 | 1.74 |
| H2 | Sortino | 4.69 | 3.25 |
| H2 | MAR | 3.50 | 2.49 |
| H2 | net $ | 761,254.40 | 593,583.52 |
| H2 | maxDD $ | 217,425.28 | 238,582.24 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -82,264.96 |
| H2 | CVaR10 $ | -79,185.12 | -80,759.36 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.76 |
| all | Sortino | 3.63 | 3.40 |
| all | MAR | 9.59 | 8.56 |
| all | net $ | 2,685,010.56 | 2,701,918.24 |
| all | maxDD $ | 280,109.76 | 315,680.48 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -80,442.83 |
| all | CVaR10 $ | -78,243.12 | -79,057.66 |
| all | % neg wk | 42.86 | 43.45 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.222 / -0.845 / -0.553
- [PASS] 3 worst week not worse (all-in): -82,524 vs baseline -82,524
- [FAIL] 4 matched family null p95: real -0.100 vs p95 +0.132 (median -0.185, rank 0.69, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.393, +0.166]
- [FAIL] 5 plateau: 0% of 2 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.258 / -0.633 / -0.736
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'set': 'all10', 'm': 1.125}: +0.014
- {'set': 'all10', 'm': 1.875}: -0.250


DONE J7