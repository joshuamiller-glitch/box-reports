# REPORT RW12
**Verdict: LEAD** (6/7 measured gates pass). Selected cell model=d2, N=1, delta=0.08, mode=longonly; additive @20% clean/H1/H2 +0.26/+0.65/+0.40; standalone all-in weekly Sharpe 2.01 (2013-26 0.37, dev 2013-22 0.06); pair-window trades 225. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

R12 K4 with extended features (SKEW, VIX9D/VIX, VIX6M/VIX3M, VIX z-score).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 1 cells, eligible (>= 100 clean trades): 1. Top cells by clean weekly Sharpe:

| model   |   N |   delta | mode     |   n |   sharpe |    net |   ypos | eligible   |
|:--------|----:|--------:|:---------|----:|---------:|-------:|-------:|:-----------|
| d2      |   1 |   0.080 | longonly | 121 |    1.686 | 34.956 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.69; replicate best-eligible median 0.00, p95 1.15; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.261e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.142 | +0.338 | +0.209 | +0.180 | +1.9 | [+0.103, +0.264] | 0.38 | NO |
| 20% | add | +0.265 | +0.654 | +0.397 | +0.337 | +4.6 | [+0.191, +0.497] | 0.38 | NO |
| 30% | add | +0.366 | +0.941 | +0.558 | +0.470 | +10.2 | [+0.259, +0.699] | 0.38 | NO |
| 50% | add | +0.512 | +1.402 | +0.800 | +0.664 | +21.4 | [+0.341, +1.013] | 0.38 | NO |
| 10% | const | +0.157 | +0.374 | +0.231 | +0.198 | -8.0 | [+0.113, +0.292] | 0.38 | NO |
| 20% | const | +0.318 | +0.802 | +0.481 | +0.407 | -14.1 | [+0.225, +0.602] | 0.38 | NO |
| 30% | const | +0.468 | +1.255 | +0.726 | +0.605 | -17.8 | [+0.321, +0.916] | 0.38 | INSURANCE |
| 50% | const | +0.642 | +1.926 | +1.024 | +0.841 | -25.3 | [+0.310, +1.411] | 0.38 | INSURANCE |

Standalone at 100% pair-equivalent risk ($): clean: net 1,489,578, Sharpe 1.64, maxDD 252,078, worst wk -164,474; H1: net 634,702, Sharpe 3.34, maxDD 24,641, worst wk -21,441; H2: net 690,356, Sharpe 2.28, maxDD 176,432, worst wk -95,344; all: net 2,814,636, Sharpe 2.01, maxDD 252,078, worst wk -164,474
Correlation with pair (weekly): clean +0.08, H1 -0.17, H2 -0.05, all +0.03; worst-decile weeks (n=17) corr -0.07, sleeve mean in those weeks $20,974, positive share 0.29.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.72 | 3.45 | 6.54 | -80,973 | -79,044 | 248,770 | -86,309 | 41.9 |
| clean | add 30% | 1.83 | 3.76 | 7.51 | -82,113 | -79,580 | 236,580 | -90,934 | 41.9 |
| clean | const 20% | 1.78 | 3.61 | 7.07 | -65,235 | -63,450 | 192,748 | -70,897 | 41.9 |
| clean | const 30% | 1.93 | 4.15 | 8.29 | -58,505 | -56,188 | 166,303 | -67,816 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.48 | 9.60 | 4.94 | -53,225 | -49,077 | 145,826 | -63,581 | 39.3 |
| H1 | add 30% | 3.77 | 11.84 | 5.49 | -49,549 | -44,046 | 142,882 | -56,227 | 39.3 |
| H1 | const 20% | 3.63 | 10.68 | 5.21 | -41,110 | -36,609 | 115,483 | -47,923 | 39.3 |
| H1 | const 30% | 4.08 | 14.82 | 6.22 | -31,375 | -27,743 | 97,368 | -32,741 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.69 | 6.15 | 4.14 | -79,970 | -73,348 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.85 | 6.82 | 4.45 | -79,970 | -73,348 | 217,425 | -82,524 | 41.7 |
| H2 | const 20% | 2.78 | 6.50 | 4.30 | -63,976 | -58,678 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 3.02 | 7.55 | 4.86 | -55,979 | -51,344 | 152,198 | -57,767 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.19 | 4.64 | 13.06 | -80,338 | -77,106 | 248,770 | -86,309 | 42.3 |
| all | add 30% | 2.33 | 5.11 | 14.92 | -81,098 | -77,148 | 236,580 | -90,934 | 41.7 |
| all | const 20% | 2.26 | 4.88 | 14.06 | -64,574 | -61,701 | 192,748 | -70,897 | 42.3 |
| all | const 30% | 2.46 | 5.66 | 16.38 | -57,452 | -54,221 | 166,303 | -67,816 | 41.1 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.265 / +0.654 / +0.397
- [PASS] 3 worst week within share: all-in worst week +4.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 2.01 vs p95 1.01 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.191, +0.497]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.260 / +0.649 / +0.391
- [PASS] 6 worst-decile corr <=+0.30: -0.07
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section R12); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (225 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2084 | +0.0156 | 0.21 |
| fixed | 2084 | +0.0043 | 0.06 |
| scaled | 2084 | +0.0091 | 0.12 |

Plateau neighbours (all-in 20% uplift; selected +0.337):
- {'model': 'd2', 'N': '1', 'delta': '0.06', 'mode': 'longonly'}: +0.357 (trades 592)
- {'model': 'd2', 'N': '1', 'delta': '0.1', 'mode': 'longonly'}: +0.121 (trades 74)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.11, p95 1.01, real 2.01. Standalone Sharpe at 2x slippage 1.99.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 224 | -3 | -0.14 |
| 2017 | 354 | 29 | 1.59 |
| 2018 | 397 | -13 | -0.46 |
| 2019 | 249 | -4 | -0.23 |
| 2020 | 284 | -6 | -0.20 |
| 2021 | 329 | 16 | 0.85 |
| 2022 | 247 | -10 | -0.54 |
| 2023 | 20 | 0 | 0.28 |
| 2024 | 64 | 9 | 0.90 |
| 2025 | 75 | 36 | 3.03 |
| 2026 | 79 | 21 | 2.75 |


## Beta / drift test (report): beta +0.093; alpha weekly Sharpe 1.87, 90% CI [+1.10, +2.58] (alpha CI lower bound > 0).

## Paired comparison with K4 (own scaling to the pair clean sd, 20% additive uplift clean/H1/H2/all): K4 +0.183/+0.392/+0.193/+0.203; R12 +0.265/+0.654/+0.397/+0.337; difference (all-in) +0.134.

DONE RW12