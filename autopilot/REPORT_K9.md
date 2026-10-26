# REPORT K9
**Verdict: NO** (0/7 measured gates pass). Selected cell band=0.9, mode=longonly, N=5; additive @20% clean/H1/H2 +0.13/+0.09/-0.10; standalone all-in weekly Sharpe 0.48 (2013-26 0.48, dev 2013-22 0.44); pair-window trades 100. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

K9 variance-risk-premium spread sleeve: VIX minus 20-day realised ES vol, percentile over 252 days; long (or long/short) index basket (8 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

|   band | mode      |   N |   n |   sharpe |     net |   ypos | eligible   |
|-------:|:----------|----:|----:|---------:|--------:|-------:|:-----------|
|  0.900 | longonly  |   5 |  68 |    0.884 |  36.416 |      2 | True       |
|  0.800 | longshort |   5 | 280 |    0.246 |  17.472 |      1 | True       |
|  0.900 | longshort |   5 | 152 |    0.239 |  11.874 |      2 | True       |
|  0.900 | longonly  |   2 | 120 |    0.212 |   6.369 |      1 | True       |
|  0.800 | longshort |   2 | 560 |    0.010 |   0.571 |      1 | True       |
|  0.800 | longonly  |   5 | 116 |    0.010 |   0.490 |      2 | True       |
|  0.800 | longonly  |   2 | 228 |   -0.102 |  -4.241 |      1 | True       |
|  0.900 | longshort |   2 | 292 |   -0.691 | -24.946 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.88; replicate best-eligible median 0.42, p95 1.01; real beats 90% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.93e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.074 | +0.058 | -0.047 | +0.044 | +19.7 | [-0.031, +0.120] | 0.74 | NO |
| 20% | add | +0.132 | +0.085 | -0.098 | +0.072 | +40.2 | [-0.075, +0.220] | 0.74 | NO |
| 30% | add | +0.173 | +0.083 | -0.154 | +0.085 | +60.7 | [-0.132, +0.300] | 0.74 | NO |
| 50% | add | +0.210 | +0.001 | -0.275 | +0.069 | +101.8 | [-0.278, +0.403] | 0.74 | NO |
| 10% | const | +0.081 | +0.063 | -0.053 | +0.048 | +9.8 | [-0.035, +0.132] | 0.74 | NO |
| 20% | const | +0.154 | +0.088 | -0.126 | +0.080 | +20.4 | [-0.103, +0.262] | 0.74 | NO |
| 30% | const | +0.203 | +0.040 | -0.230 | +0.080 | +31.0 | [-0.223, +0.371] | 0.74 | NO |
| 50% | const | +0.141 | -0.409 | -0.621 | -0.113 | +52.2 | [-0.723, +0.477] | 0.74 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 703,008, Sharpe 0.77, maxDD 526,597, worst wk -188,700; H1: net 107,746, Sharpe 0.50, maxDD 259,907, worst wk -197,575; H2: net -185,980, Sharpe -1.36, maxDD 335,560, worst wk -78,814; all: net 624,774, Sharpe 0.48, maxDD 526,597, worst wk -197,575
Correlation with pair (weekly): clean -0.03, H1 -0.07, H2 -0.12, all -0.05; worst-decile weeks (n=17) corr +0.45, sleeve mean in those weeks $5,334, positive share 0.18.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.59 | 3.08 | 4.26 | -84,787 | -81,299 | 345,426 | -115,729 | 42.9 |
| clean | add 30% | 1.63 | 3.17 | 4.08 | -87,834 | -82,961 | 378,085 | -132,656 | 42.9 |
| clean | const 20% | 1.61 | 3.13 | 4.16 | -69,048 | -65,704 | 289,404 | -99,354 | 42.9 |
| clean | const 30% | 1.66 | 3.25 | 3.88 | -64,226 | -59,568 | 294,052 | -108,094 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.91 | 6.71 | 4.47 | -71,724 | -62,106 | 137,633 | -76,932 | 39.3 |
| H1 | add 30% | 2.91 | 7.02 | 4.31 | -68,780 | -60,144 | 145,159 | -76,932 | 39.3 |
| H1 | const 20% | 2.92 | 6.86 | 4.51 | -56,202 | -48,900 | 110,106 | -61,546 | 39.3 |
| H1 | const 30% | 2.87 | 7.39 | 3.79 | -45,497 | -40,335 | 118,177 | -53,853 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.20 | 4.46 | 3.33 | -81,089 | -79,185 | 217,425 | -82,524 | 47.2 |
| H2 | add 30% | 2.14 | 4.34 | 3.24 | -81,089 | -79,185 | 217,425 | -82,524 | 47.2 |
| H2 | const 20% | 2.17 | 4.40 | 3.29 | -64,871 | -63,348 | 173,940 | -66,020 | 47.2 |
| H2 | const 30% | 2.07 | 4.18 | 3.13 | -56,762 | -55,430 | 152,198 | -57,767 | 47.2 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.93 | 3.83 | 8.13 | -83,146 | -80,275 | 345,426 | -115,729 | 43.5 |
| all | add 30% | 1.94 | 3.88 | 7.60 | -85,177 | -81,333 | 378,085 | -132,656 | 43.5 |
| all | const 20% | 1.94 | 3.86 | 7.85 | -67,329 | -64,643 | 289,404 | -99,354 | 43.5 |
| all | const 30% | 1.94 | 3.90 | 7.03 | -61,452 | -57,885 | 294,052 | -108,094 | 44.0 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.132 / +0.085 / -0.098
- [FAIL] 3 worst week within share: all-in worst week +40.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.48 vs p95 0.71 (rank 0.88)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.075, +0.220]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.130 / +0.084 / -0.099
- [FAIL] 6 worst-decile corr <=+0.30: +0.45
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K9); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (100 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 247 | +0.3318 | 0.46 |
| fixed | 247 | +0.3193 | 0.44 |
| scaled | 247 | +0.3253 | 0.45 |

Plateau neighbours (all-in 20% uplift; selected +0.072):
- {'band': '0.925', 'mode': 'longonly', 'N': '5'}: +0.128 (trades 88)
- {'band': '0.875', 'mode': 'longonly', 'N': '5'}: +0.041 (trades 120)
- {'band': '0.9', 'mode': 'longonly', 'N': '4'}: +0.031 (trades 108)
- {'band': '0.9', 'mode': 'longonly', 'N': '6'}: +0.156 (trades 92)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.03, p95 0.71, real 0.48. Standalone Sharpe at 2x slippage 0.47.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2014 | 36 | -0 | -0.01 |
| 2015 | 3 | 9 | nan |
| 2016 | 6 | 5 | nan |
| 2017 | 14 | 10 | 1.21 |
| 2018 | 28 | 23 | 2.19 |
| 2019 | 24 | 18 | 3.70 |
| 2020 | 84 | -31 | -0.74 |
| 2021 | 24 | 36 | 1.58 |
| 2022 | 28 | 10 | 0.94 |
| 2023 | 24 | 21 | 1.62 |
| 2024 | 40 | 34 | 1.56 |
| 2025 | 32 | -3 | -0.14 |
| 2026 | 16 | -10 | -3.77 |


DONE K9