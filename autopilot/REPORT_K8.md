# REPORT K8
**Verdict: NO** (1/7 measured gates pass). Selected cell model=d4, N=3, delta=0.08, mode=longshort; additive @20% clean/H1/H2 +0.05/-0.01/-0.17; standalone all-in weekly Sharpe 0.29 (2013-26 -0.28, dev 2013-22 -0.53); pair-window trades 467. Runtime 0.3 min (+selection 0.0 min). 6-worker pool.

K8 daily walk-forward LightGBM on GC, CL, ZN, 6E, 6J with price, VIX-state, COT (spec/hedge) and calendar features (16 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 100 clean trades): 10. Top cells by clean weekly Sharpe:

| model   |   N |   delta | mode      |   n |   sharpe |     net |   ypos | eligible   |
|:--------|----:|--------:|:----------|----:|---------:|--------:|-------:|:-----------|
| d4      |   3 |   0.080 | longshort | 313 |    0.517 |  19.326 |      2 | True       |
| d2      |   3 |   0.080 | longshort |  86 |    0.347 |   6.814 |      2 | False      |
| d4      |   3 |   0.080 | longonly  |  77 |    0.225 |   4.642 |      1 | False      |
| d4      |   3 |   0.040 | longonly  | 201 |    0.133 |   4.130 |      2 | True       |
| d4      |   1 |   0.080 | longshort | 372 |    0.040 |   0.799 |      2 | True       |
| d2      |   1 |   0.080 | longshort | 122 |    0.033 |   0.415 |      2 | True       |
| d2      |   3 |   0.040 | longonly  |  73 |   -0.059 |  -1.104 |      2 | False      |
| d4      |   3 |   0.040 | longshort | 613 |   -0.238 | -12.539 |      1 | True       |
| d2      |   3 |   0.040 | longshort | 352 |   -0.327 | -13.471 |      2 | True       |
| d2      |   3 |   0.080 | longonly  |  12 |   -0.504 |  -3.579 |      1 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.52; replicate best-eligible median 0.68, p95 1.44; real beats 43% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.434e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.032 | +0.004 | -0.082 | -0.002 | +14.5 | [-0.086, +0.083] | 0.04 | NO |
| 20% | add | +0.049 | -0.010 | -0.174 | -0.018 | +35.6 | [-0.183, +0.149] | 0.04 | NO |
| 30% | add | +0.054 | -0.043 | -0.273 | -0.045 | +56.7 | [-0.287, +0.199] | 0.04 | NO |
| 50% | add | +0.035 | -0.155 | -0.485 | -0.127 | +98.9 | [-0.504, +0.257] | 0.04 | NO |
| 10% | const | +0.034 | +0.004 | -0.092 | -0.003 | +5.1 | [-0.096, +0.092] | 0.04 | NO |
| 20% | const | +0.053 | -0.025 | -0.223 | -0.030 | +16.9 | [-0.234, +0.177] | 0.04 | NO |
| 30% | const | +0.045 | -0.109 | -0.408 | -0.095 | +28.7 | [-0.424, +0.243] | 0.04 | NO |
| 50% | const | -0.087 | -0.566 | -1.005 | -0.382 | +52.2 | [-1.020, +0.256] | 0.04 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 579,181, Sharpe 0.64, maxDD 490,288, worst wk -228,259; H1: net 12,010, Sharpe 0.07, maxDD 276,227, worst wk -99,705; H2: net -204,738, Sharpe -0.82, maxDD 339,906, worst wk -106,762; all: net 386,452, Sharpe 0.29, maxDD 490,288, worst wk -228,259
Correlation with pair (weekly): clean +0.16, H1 -0.04, H2 +0.09, all +0.12; worst-decile weeks (n=17) corr -0.04, sleeve mean in those weeks $-21,126, positive share 0.29.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.51 | 2.87 | 5.02 | -93,877 | -86,350 | 288,241 | -111,878 | 42.9 |
| clean | add 30% | 1.51 | 2.88 | 5.12 | -101,648 | -91,150 | 293,946 | -129,288 | 43.8 |
| clean | const 20% | 1.51 | 2.88 | 5.08 | -78,210 | -70,954 | 232,219 | -96,466 | 42.9 |
| clean | const 30% | 1.50 | 2.85 | 4.83 | -78,148 | -68,229 | 228,722 | -106,170 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.82 | 6.23 | 3.52 | -72,164 | -63,329 | 169,489 | -89,286 | 42.9 |
| H1 | add 30% | 2.78 | 6.12 | 3.08 | -71,508 | -62,145 | 193,673 | -95,463 | 39.3 |
| H1 | const 20% | 2.80 | 6.19 | 3.29 | -56,642 | -50,190 | 145,265 | -73,900 | 42.9 |
| H1 | const 30% | 2.72 | 5.82 | 2.66 | -53,688 | -46,985 | 157,337 | -72,384 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.12 | 4.14 | 3.29 | -91,686 | -85,206 | 219,234 | -97,904 | 41.7 |
| H2 | add 30% | 2.02 | 3.86 | 3.18 | -97,611 | -88,216 | 220,139 | -108,283 | 36.1 |
| H2 | const 20% | 2.07 | 4.00 | 3.23 | -75,719 | -69,369 | 175,749 | -82,475 | 38.9 |
| H2 | const 30% | 1.89 | 3.50 | 3.04 | -73,660 | -65,739 | 154,911 | -85,139 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.84 | 3.56 | 9.58 | -92,908 | -85,367 | 288,241 | -111,878 | 42.9 |
| all | add 30% | 1.81 | 3.48 | 9.53 | -100,064 | -89,483 | 293,946 | -129,288 | 41.7 |
| all | const 20% | 1.83 | 3.52 | 9.58 | -77,177 | -69,940 | 232,219 | -96,466 | 42.3 |
| all | const 30% | 1.76 | 3.34 | 8.72 | -76,510 | -66,780 | 228,722 | -106,170 | 41.1 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.049 / -0.010 / -0.174
- [FAIL] 3 worst week within share: all-in worst week +35.6% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.29 vs p95 0.77 (rank 0.77)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.183, +0.149]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.020 / -0.051 / -0.200
- [PASS] 6 worst-decile corr <=+0.30: -0.04
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K8); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (467 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1714 | -0.0191 | -0.22 |
| fixed | 1714 | -0.0468 | -0.53 |
| scaled | 1714 | -0.0424 | -0.48 |

Plateau neighbours (all-in 20% uplift; selected -0.018):
- {'model': 'd4', 'N': '3', 'delta': '0.06', 'mode': 'longshort'}: -0.068 (trades 681)
- {'model': 'd4', 'N': '3', 'delta': '0.1', 'mode': 'longshort'}: -0.077 (trades 291)
- {'model': 'd4', 'N': '2', 'delta': '0.08', 'mode': 'longshort'}: -0.012 (trades 512)
- {'model': 'd4', 'N': '4', 'delta': '0.08', 'mode': 'longshort'}: -0.074 (trades 420)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.09, p95 0.77, real 0.29. Standalone Sharpe at 2x slippage 0.12.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 313 | -5 | -0.18 |
| 2017 | 297 | -7 | -0.32 |
| 2018 | 278 | -31 | -1.44 |
| 2019 | 195 | -16 | -1.07 |
| 2020 | 222 | -14 | -0.52 |
| 2021 | 206 | 14 | 0.91 |
| 2022 | 203 | -22 | -1.11 |
| 2023 | 155 | -4 | -0.28 |
| 2024 | 143 | 8 | 0.39 |
| 2025 | 144 | 30 | 1.95 |
| 2026 | 103 | -13 | -1.07 |


DONE K8