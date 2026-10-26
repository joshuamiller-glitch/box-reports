# REPORT J4
**Verdict: LEAD** (5/7 measured gates pass). Selected cell ev=quad, win=0_1, side=long; additive @20% clean/H1/H2 +0.15/+0.53/+0.16; standalone all-in weekly Sharpe 1.30 (2013-26 0.29, dev 2013-22 -0.03); pair-window trades 39 (SMALL-SAMPLE). Runtime 0.1 min (+selection 0.0 min). 7-worker pool.

J4 index-event calendar sleeve (NQ, ES, RTY): quad witching/rebalance, monthly opex, Russell reconstitution, month-end windows, long or short (32 cells). Plateau n/a.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 20 clean trades): 24. Top cells by clean weekly Sharpe:

| ev      | win   | side   |   n |   sharpe |   net |   ypos | eligible   |
|:--------|:------|:-------|----:|---------:|------:|-------:|:-----------|
| russell | 0_3   | long   |   6 |    1.414 | 4.976 |      2 | False      |
| russell | -3_-1 | long   |   6 |    1.408 | 2.791 |      2 | False      |
| quad    | 0_1   | long   |  24 |    1.134 | 5.808 |      3 | True       |
| opex    | 0_1   | long   |  48 |    0.900 | 7.325 |      2 | True       |
| opex    | -1_0  | short  |  48 |    0.780 | 8.866 |      3 | True       |
| quad    | 0_3   | long   |  24 |    0.758 | 8.891 |      2 | True       |
| quad    | -1_0  | short  |  24 |    0.644 | 3.750 |      2 | True       |
| opex    | 0_3   | long   |  48 |    0.615 | 8.673 |      3 | True       |
| russell | 0_1   | long   |   6 |    0.482 | 0.406 |      1 | False      |
| opex    | -3_-1 | short  |  48 |    0.380 | 7.122 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.13; replicate best-eligible median 1.26, p95 1.95; real beats 33% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.673e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.083 | +0.277 | +0.111 | +0.113 | +0.0 | [+0.036, +0.202] | 0.01 | NO |
| 20% | add | +0.148 | +0.525 | +0.156 | +0.192 | +3.2 | [+0.050, +0.355] | 0.01 | NO |
| 30% | add | +0.197 | +0.734 | +0.159 | +0.241 | +10.6 | [+0.042, +0.471] | 0.01 | NO |
| 50% | add | +0.251 | +1.010 | +0.103 | +0.272 | +47.5 | [-0.027, +0.614] | 0.01 | NO |
| 10% | const | +0.091 | +0.306 | +0.119 | +0.123 | -10.0 | [+0.039, +0.220] | 0.01 | NO |
| 20% | const | +0.174 | +0.635 | +0.162 | +0.220 | -14.5 | [+0.049, +0.415] | 0.01 | NO |
| 30% | const | +0.238 | +0.933 | +0.128 | +0.269 | -10.1 | [+0.003, +0.576] | 0.01 | INSURANCE |
| 50% | const | +0.238 | +1.039 | -0.089 | +0.178 | +40.4 | [-0.298, +0.733] | 0.01 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 971,740, Sharpe 1.07, maxDD 220,007, worst wk -220,007; H1: net 444,635, Sharpe 1.96, maxDD 0, worst wk 0; H2: net 958,756, Sharpe 1.59, maxDD 7,869, worst wk -7,869; all: net 2,375,131, Sharpe 1.30, maxDD 220,007, worst wk -220,007
Correlation with pair (weekly): clean +0.11, H1 -0.25, H2 +0.33, all +0.15; worst-decile weeks (n=17) corr +nan, sleeve mean in those weeks $0, positive share 0.00.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.61 | 3.15 | 5.44 | -80,049 | -78,749 | 280,110 | -85,189 | 41.9 |
| clean | add 30% | 1.66 | 3.29 | 5.79 | -81,097 | -79,367 | 280,110 | -91,309 | 41.9 |
| clean | const 20% | 1.63 | 3.22 | 5.62 | -64,447 | -63,222 | 224,088 | -70,599 | 41.9 |
| clean | const 30% | 1.70 | 3.45 | 6.23 | -60,986 | -57,857 | 196,077 | -74,211 | 41.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.35 | 7.43 | 4.50 | -77,610 | -65,697 | 151,713 | -78,287 | 35.7 |
| H1 | add 30% | 3.56 | 7.91 | 4.79 | -77,610 | -65,697 | 151,713 | -78,287 | 32.1 |
| H1 | const 20% | 3.46 | 7.67 | 4.65 | -62,088 | -52,557 | 121,370 | -62,630 | 32.1 |
| H1 | const 30% | 3.76 | 8.53 | 5.17 | -54,327 | -45,988 | 106,199 | -54,801 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.45 | 5.87 | 4.38 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.45 | 6.46 | 4.82 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | const 20% | 2.46 | 6.16 | 4.60 | -64,871 | -63,348 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 2.42 | 7.22 | 5.39 | -56,762 | -55,430 | 152,198 | -57,767 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.05 | 4.26 | 11.28 | -80,084 | -78,724 | 280,110 | -85,189 | 41.7 |
| all | add 30% | 2.10 | 4.53 | 12.13 | -80,783 | -79,125 | 280,110 | -91,309 | 41.1 |
| all | const 20% | 2.08 | 4.40 | 11.71 | -64,339 | -63,123 | 224,088 | -70,599 | 41.1 |
| all | const 30% | 2.13 | 4.85 | 13.22 | -59,360 | -56,876 | 196,077 | -74,211 | 40.5 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.148 / +0.525 / +0.156
- [PASS] 3 worst week within share: all-in worst week +3.2% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.30 vs p95 1.08 (rank 0.99)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.050, +0.355]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.144 / +0.520 / +0.155
- [FAIL] 6 worst-decile corr <=+0.30: +nan
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section J4); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (39 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 102 | +0.0061 | 0.02 |
| fixed | 102 | -0.0087 | -0.03 |
| scaled | 102 | -0.0003 | -0.00 |

Plateau neighbours (all-in 20% uplift; selected +0.192):

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.07, p95 1.08, real 1.30. Standalone Sharpe at 2x slippage 1.29.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 8 | -1 | -0.54 |
| 2014 | 8 | -3 | -1.34 |
| 2015 | 8 | 3 | 1.49 |
| 2016 | 8 | 2 | 1.49 |
| 2017 | 10 | 5 | 1.87 |
| 2018 | 12 | -6 | -1.70 |
| 2019 | 12 | 1 | 1.03 |
| 2020 | 12 | -1 | -0.49 |
| 2021 | 12 | -2 | -0.33 |
| 2022 | 12 | 1 | 0.44 |
| 2023 | 12 | 0 | 0.24 |
| 2024 | 12 | 1 | 0.53 |
| 2025 | 12 | 7 | 2.27 |
| 2026 | 9 | 6 | 1.84 |


DONE J4