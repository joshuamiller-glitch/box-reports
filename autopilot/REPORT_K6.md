# REPORT K6
**Verdict: NO** (2/7 measured gates pass). Selected cell u=CL, mode=follow, H=60; additive @20% clean/H1/H2 +0.13/-0.32/-0.03; standalone all-in weekly Sharpe 0.30 (2013-26 -0.40, dev 2013-22 -0.61); pair-window trades 109. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

K6 EIA weekly energy release sleeve (CL/HO/RB Wednesday, NG Thursday 10:30 ET; volume-confirmed events), post-move follow/fade (24 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 24 cells, eligible (>= 30 clean trades): 24. Top cells by clean weekly Sharpe:

| u   | mode   | H     |   n |   sharpe |   net |   ypos | eligible   |
|:----|:-------|:------|----:|---------:|------:|-------:|:-----------|
| CL  | follow | 60    |  84 |    0.738 | 2.399 |      1 | True       |
| HO  | follow | 60    |  81 |    0.502 | 1.728 |      2 | True       |
| RB  | follow | close |  85 |    0.470 | 3.213 |      3 | True       |
| NG  | follow | close |  95 |    0.453 | 2.475 |      2 | True       |
| HO  | follow | 30    |  81 |    0.417 | 1.142 |      2 | True       |
| CL  | follow | close |  84 |    0.403 | 2.638 |      3 | True       |
| RB  | follow | 60    |  85 |    0.185 | 0.691 |      2 | True       |
| HO  | follow | close |  81 |    0.165 | 1.011 |      2 | True       |
| CL  | follow | 30    |  84 |    0.103 | 0.279 |      2 | True       |
| RB  | fade   | 30    |  85 |    0.038 | 0.110 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.74; replicate best-eligible median 0.70, p95 1.08; real beats 63% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.804e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.072 | -0.155 | -0.016 | +0.022 | +3.8 | [-0.061, +0.107] | 0.58 | NO |
| 20% | add | +0.129 | -0.322 | -0.033 | +0.030 | +14.2 | [-0.135, +0.200] | 0.58 | NO |
| 30% | add | +0.168 | -0.497 | -0.051 | +0.025 | +24.6 | [-0.217, +0.276] | 0.58 | NO |
| 50% | add | +0.202 | -0.855 | -0.088 | -0.018 | +52.9 | [-0.404, +0.382] | 0.58 | NO |
| 10% | const | +0.079 | -0.173 | -0.018 | +0.023 | -5.6 | [-0.069, +0.119] | 0.58 | NO |
| 20% | const | +0.150 | -0.408 | -0.042 | +0.029 | -4.5 | [-0.175, +0.240] | 0.58 | NO |
| 30% | const | +0.197 | -0.727 | -0.075 | +0.002 | -3.3 | [-0.337, +0.349] | 0.58 | NO |
| 50% | const | +0.126 | -1.679 | -0.190 | -0.233 | +28.2 | [-0.879, +0.436] | 0.58 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 672,666, Sharpe 0.74, maxDD 409,416, worst wk -170,723; H1: net -277,948, Sharpe -1.70, maxDD 393,882, worst wk -109,409; H2: net -25,190, Sharpe -0.39, maxDD 50,775, worst wk -37,305; all: net 369,528, Sharpe 0.30, maxDD 572,524, worst wk -170,723
Correlation with pair (weekly): clean -0.04, H1 +0.07, H2 +0.19, all -0.02; worst-decile weeks (n=17) corr -0.09, sleeve mean in those weeks $-3,018, positive share 0.29.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.59 | 2.98 | 4.87 | -86,253 | -81,697 | 300,860 | -94,232 | 42.9 |
| clean | add 30% | 1.63 | 3.01 | 4.58 | -92,288 | -85,987 | 334,161 | -102,826 | 41.0 |
| clean | const 20% | 1.61 | 3.00 | 4.72 | -71,017 | -66,856 | 254,008 | -78,823 | 42.9 |
| clean | const 30% | 1.66 | 3.00 | 4.29 | -72,420 | -65,593 | 263,885 | -79,795 | 37.1 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.51 | 5.05 | 3.50 | -79,781 | -72,934 | 153,906 | -82,630 | 35.7 |
| H1 | add 30% | 2.33 | 4.55 | 2.94 | -80,867 | -76,387 | 173,859 | -84,802 | 39.3 |
| H1 | const 20% | 2.42 | 4.80 | 3.26 | -64,259 | -59,728 | 128,471 | -66,973 | 35.7 |
| H1 | const 30% | 2.10 | 3.96 | 2.28 | -57,940 | -56,578 | 145,587 | -61,316 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.26 | 4.69 | 3.48 | -81,089 | -77,766 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.24 | 4.68 | 3.47 | -81,089 | -77,057 | 217,425 | -82,524 | 44.4 |
| H2 | const 20% | 2.25 | 4.68 | 3.47 | -64,871 | -61,929 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 2.22 | 4.67 | 3.45 | -56,762 | -53,301 | 152,198 | -57,767 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.89 | 3.63 | 9.17 | -84,703 | -80,658 | 300,860 | -94,232 | 42.3 |
| all | add 30% | 1.88 | 3.58 | 8.37 | -89,174 | -83,680 | 334,161 | -102,826 | 41.7 |
| all | const 20% | 1.88 | 3.61 | 8.75 | -69,343 | -65,497 | 254,008 | -78,823 | 42.3 |
| all | const 30% | 1.86 | 3.46 | 7.54 | -68,504 | -62,296 | 263,885 | -79,795 | 39.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.129 / -0.322 / -0.033
- [PASS] 3 worst week within share: all-in worst week +14.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.30 vs p95 0.79 (rank 0.50)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.135, +0.200]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.079 / -0.390 / -0.039
- [PASS] 6 worst-decile corr <=+0.30: -0.09
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K6); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (109 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 429 | -0.0108 | -0.27 |
| fixed | 429 | -0.0247 | -0.61 |
| scaled | 429 | -0.0227 | -0.56 |

Plateau neighbours (all-in 20% uplift; selected +0.030):
- {'u': 'CL', 'mode': 'follow', 'H': '45'}: -0.030 (trades 109)
- {'u': 'CL', 'mode': 'follow', 'H': '75'}: -0.021 (trades 109)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.30, p95 0.79, real 0.30. Standalone Sharpe at 2x slippage 0.05.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 41 | -2 | -1.56 |
| 2014 | 44 | -4 | -2.13 |
| 2015 | 46 | 0 | 0.13 |
| 2016 | 47 | -2 | -0.76 |
| 2017 | 44 | -6 | -2.77 |
| 2018 | 42 | 1 | 0.45 |
| 2019 | 44 | 2 | 1.10 |
| 2020 | 43 | -2 | -1.17 |
| 2021 | 40 | -0 | -0.28 |
| 2022 | 38 | 2 | 1.71 |
| 2023 | 38 | -0 | -0.18 |
| 2024 | 41 | 3 | 2.04 |
| 2025 | 43 | -1 | -1.09 |
| 2026 | 8 | -0 | -0.65 |


DONE K6