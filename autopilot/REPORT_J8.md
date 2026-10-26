# REPORT J8
**Verdict: NO** (1/6 measured gates pass; D1-harness class INSURANCE). Carried cell v=vchg, tail=high, q=0.9, m=0.0; all-in Sharpe uplift clean/H1/H2/all +0.20/-0.11/-0.13/+0.08. Runtime 37.8 min, 7-worker pool. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R, per-book week rule off).

J8 VIX / term-structure / VVIX / VIX9D state switch of the pair (40 cells), thresholds from trailing 756-day quantiles, state applies to the next label.


## Clean-only selection grid

| v    | tail   |     q |     m |   clean_sharpe |   clean_dsharpe |   changed |   clean_net | eligible   |
|:-----|:-------|------:|------:|---------------:|----------------:|----------:|------------:|:-----------|
| vchg | high   | 0.900 | 0.000 |          1.657 |           0.197 |     0.126 | 1428543.680 | True       |
| vchg | high   | 0.800 | 0.500 |          1.638 |           0.178 |     0.398 | 1386155.840 | True       |
| vvix | high   | 0.800 | 0.000 |          1.597 |           0.137 |     0.205 | 1226008.960 | True       |
| vchg | high   | 0.800 | 0.000 |          1.593 |           0.133 |     0.237 | 1292088.320 | True       |
| term | high   | 0.800 | 0.500 |          1.571 |           0.111 |     0.476 | 1306666.560 | True       |
| vchg | low    | 0.900 | 0.000 |          1.559 |           0.099 |     0.121 | 1308107.200 | True       |
| vchg | low    | 0.800 | 0.000 |          1.540 |           0.080 |     0.176 | 1273249.600 | True       |
| vvix | high   | 0.800 | 0.500 |          1.528 |           0.068 |     0.377 | 1273163.840 | True       |
| term | high   | 0.900 | 0.500 |          1.485 |           0.025 |     0.295 | 1222795.520 | True       |
| term | low    | 0.900 | 0.000 |          1.479 |           0.019 |     0.032 | 1323484.800 | False      |
| term | low    | 0.900 | 0.500 |          1.478 |           0.018 |     0.034 | 1334824.320 | False      |
| vvix | low    | 0.900 | 0.500 |          1.472 |           0.012 |     0.175 | 1291588.960 | True       |
| vix  | low    | 0.900 | 0.500 |          1.459 |          -0.001 |     0.310 | 1267871.200 | True       |
| vix  | high   | 0.800 | 0.500 |          1.440 |          -0.020 |     0.180 | 1261605.760 | True       |
| vvix | low    | 0.900 | 0.000 |          1.439 |          -0.021 |     0.138 | 1216893.120 | True       |
| v9   | low    | 0.800 | 0.000 |          1.396 |          -0.064 |     0.209 | 1213584.320 | True       |
| vix  | high   | 0.900 | 0.500 |          1.389 |          -0.071 |     0.104 | 1197292.480 | True       |
| v9   | low    | 0.800 | 0.500 |          1.374 |          -0.086 |     0.264 | 1202003.840 | True       |
| vix  | low    | 0.900 | 0.000 |          1.374 |          -0.086 |     0.248 | 1122011.200 | True       |
| term | high   | 0.800 | 0.000 |          1.372 |          -0.088 |     0.252 | 1036243.840 | True       |
| term | low    | 0.800 | 0.000 |          1.354 |          -0.106 |     0.129 | 1183967.040 | True       |
| v9   | low    | 0.900 | 0.000 |          1.348 |          -0.112 |     0.118 | 1178968.320 | True       |
| term | low    | 0.800 | 0.500 |          1.341 |          -0.119 |     0.149 | 1168577.760 | True       |
| term | high   | 0.900 | 0.000 |          1.337 |          -0.123 |     0.145 | 1027946.560 | True       |
| vchg | high   | 0.900 | 0.500 |          1.334 |          -0.126 |     0.236 | 1201210.240 | True       |
| v9   | low    | 0.900 | 0.500 |          1.332 |          -0.127 |     0.143 | 1174976.000 | True       |
| vix  | low    | 0.800 | 0.500 |          1.301 |          -0.159 |     0.442 | 1044115.040 | True       |
| vvix | low    | 0.800 | 0.500 |          1.284 |          -0.176 |     0.290 | 1107563.200 | True       |
| vix  | high   | 0.900 | 0.000 |          1.228 |          -0.232 |     0.048 | 1030772.480 | False      |
| vvix | high   | 0.900 | 0.500 |          1.227 |          -0.233 |     0.198 | 1057106.240 | True       |
| vchg | low    | 0.800 | 0.500 |          1.224 |          -0.235 |     0.257 | 1048991.840 | True       |
| vvix | high   | 0.900 | 0.000 |          1.202 |          -0.258 |     0.114 |  968179.200 | True       |
| vchg | low    | 0.900 | 0.500 |          1.180 |          -0.280 |     0.167 | 1043361.120 | True       |
| vix  | high   | 0.800 | 0.000 |          1.154 |          -0.305 |     0.085 |  965211.520 | True       |
| v9   | high   | 0.900 | 0.500 |          1.119 |          -0.341 |     0.186 |  959129.760 | True       |
| v9   | high   | 0.800 | 0.000 |          1.091 |          -0.368 |     0.205 |  852824.960 | True       |
| v9   | high   | 0.800 | 0.500 |          1.070 |          -0.390 |     0.351 |  913605.280 | True       |
| v9   | high   | 0.900 | 0.000 |          1.067 |          -0.393 |     0.098 |  863182.080 | True       |
| vix  | low    | 0.800 | 0.000 |          0.965 |          -0.494 |     0.338 |  705875.520 | True       |
| vvix | low    | 0.800 | 0.000 |          0.926 |          -0.534 |     0.226 |  780569.600 | True       |

## Carried cell vs baseline pair (clean / H1 / H2 / all-in)

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.66 |
| clean | Sortino | 2.78 | 3.20 |
| clean | MAR | 4.75 | 6.76 |
| clean | net $ | 1,329,958.72 | 1,428,543.68 |
| clean | maxDD $ | 280,109.76 | 211,222.40 |
| clean | worst wk $ | -81,873.92 | -79,867.84 |
| clean | CVaR5 $ | -78,735.52 | -77,966.29 |
| clean | CVaR10 $ | -78,008.81 | -77,566.49 |
| clean | % neg wk | 42.86 | 40.00 |
| H1 | weekly Sharpe | 2.83 | 2.72 |
| H1 | Sortino | 6.09 | 5.58 |
| H1 | MAR | 3.91 | 3.99 |
| H1 | net $ | 593,797.44 | 548,525.44 |
| H1 | maxDD $ | 151,712.64 | 137,607.04 |
| H1 | worst wk $ | -78,287.36 | -78,287.36 |
| H1 | CVaR5 $ | -77,609.92 | -77,597.12 |
| H1 | CVaR10 $ | -66,029.97 | -66,021.44 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 2.17 |
| H2 | Sortino | 4.69 | 4.46 |
| H2 | MAR | 3.50 | 3.28 |
| H2 | net $ | 761,254.40 | 712,822.08 |
| H2 | maxDD $ | 217,425.28 | 217,425.28 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -81,088.96 |
| H2 | CVaR10 $ | -79,185.12 | -79,185.12 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.94 |
| all | Sortino | 3.63 | 3.82 |
| all | MAR | 9.59 | 12.37 |
| all | net $ | 2,685,010.56 | 2,689,891.20 |
| all | maxDD $ | 280,109.76 | 217,425.28 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -78,713.35 |
| all | CVaR10 $ | -78,243.12 | -77,953.00 |
| all | % neg wk | 42.86 | 40.48 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.197 / -0.110 / -0.125
- [PASS] 3 worst week not worse (all-in): -82,524 vs baseline -82,524
- [FAIL] 4 matched family null p95: real +0.085 vs p95 +0.193 (median -0.138, rank 0.85, n=300)
- [FAIL] 4 bootstrap 90% CI >0: [-0.178, +0.371]
- [FAIL] 5 plateau: 0% of 3 neighbours keep >=75% of uplift
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.223 / -0.165 / -0.103
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md BATCH I); 2 selection on clean only, H1/H2 read once; 6 n/a (pair change, not a hedge claim); 7 see below

Plateau neighbours (all-in uplift):
- {'v': 'vchg', 'tail': 'high', 'q': 0.925, 'm': 0.0}: -0.055
- {'v': 'vchg', 'tail': 'high', 'q': 0.875, 'm': 0.0}: +0.027
- {'v': 'vchg', 'tail': 'high', 'q': 0.9, 'm': 0.25}: -0.038


DONE J8