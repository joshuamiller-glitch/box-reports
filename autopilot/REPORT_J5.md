# REPORT J5
**Verdict: NO** (1/6 measured gates pass; D1-harness class NO). Carried cell set=monthend, m=1.5; all-in Sharpe uplift clean/H1/H2/all +0.01/+0.09/-0.16/-0.02. Runtime 18.3 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

J5 index-event pair size tilt (12 cells): quad witching / opex / Russell / month-end labels.


## Clean-only selection grid

| set      |     m |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|:---------|------:|---------------:|----------------:|----------:|------------:|:-----------|
| monthend | 1.500 |          1.467 |           0.007 |     0.045 | 1366370.240 | True       |
| quad     | 1.500 |          1.458 |          -0.002 |     0.013 | 1328809.920 | True       |
| monthend | 0.000 |          1.443 |          -0.017 |     0.050 | 1270492.160 | True       |
| qor      | 0.500 |          1.431 |          -0.028 |     0.071 | 1253929.920 | True       |
| monthend | 0.500 |          1.426 |          -0.034 |     0.075 | 1259954.720 | True       |
| quad     | 0.000 |          1.424 |          -0.036 |     0.013 | 1261558.080 | True       |
| quad     | 0.500 |          1.399 |          -0.061 |     0.019 | 1250254.720 | True       |
| all      | 0.500 |          1.392 |          -0.067 |     0.143 | 1179955.680 | True       |
| all      | 1.500 |          1.324 |          -0.136 |     0.093 | 1212185.120 | True       |
| qor      | 1.500 |          1.317 |          -0.143 |     0.050 | 1178116.160 | True       |
| qor      | 0.000 |          1.274 |          -0.185 |     0.050 | 1116826.880 | True       |
| all      | 0.000 |          1.259 |          -0.201 |     0.099 | 1062300.800 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.47 |
| clean | Sortino | 2.78 | 2.77 |
| clean | MAR | 4.75 | 5.68 |
| clean | net $ | 1,329,958.72 | 1,366,370.24 |
| clean | maxDD $ | 280,109.76 | 240,713.92 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,884.64 |
| clean | CVaR10 $ | -78,008.81 | -78,114.50 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.91 |
| H1 | Sortino | 6.09 | 6.32 |
| H1 | MAR | 3.91 | 4.20 |
| H1 | net $ | 593,797.44 | 622,727.20 |
| H1 | maxDD $ | 151,712.64 | 148,387.04 |
| H1 | worst wk $ | -78,287.36 | -78,287.36 |
| H1 | CVaR5 $ | -77,609.92 | -77,609.92 |
| H1 | CVaR10 $ | -66,029.97 | -66,029.97 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 2.14 |
| H2 | Sortino | 4.69 | 4.18 |
| H2 | MAR | 3.50 | 3.34 |
| H2 | net $ | 761,254.40 | 725,842.24 |
| H2 | maxDD $ | 217,425.28 | 217,236.00 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -81,088.96 |
| H2 | CVaR10 $ | -79,185.12 | -79,306.28 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.84 |
| all | Sortino | 3.63 | 3.54 |
| all | MAR | 9.59 | 11.28 |
| all | net $ | 2,685,010.56 | 2,714,939.68 |
| all | maxDD $ | 280,109.76 | 240,713.92 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -79,337.32 |
| all | CVaR10 $ | -78,243.12 | -78,348.17 |
| all | % neg wk | 42.86 | 41.67 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.007 / +0.086 / -0.155
- [PASS] 3 worst week not worse (all-in): -82,524 vs baseline -82,524
- [FAIL] 4 matched family null p95: real -0.019 vs p95 +0.108 (median -0.079, rank 0.71, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.178, +0.130]
- [FAIL] 5 plateau: 0% of 2 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.036 / +0.113 / -0.148
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'set': 'monthend', 'm': 1.125}: -0.001
- {'set': 'monthend', 'm': 1.875}: -0.154


DONE J5