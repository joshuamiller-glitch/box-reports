# REPORT RW4
**Verdict: NO** (1/7 measured gates pass). Selected cell kind=fixed, N=2, delta=0.06; additive @20% clean/H1/H2 +0.06/+0.25/+0.20; standalone all-in weekly Sharpe 0.84 (2013-26 0.44, dev 2013-22 0.23); pair-window trades 740. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

R4 K4 holding period: fixed 2-day with deltas, persistent hold while p stays high (5 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 5 cells, eligible (>= 100 clean trades): 3. Top cells by clean weekly Sharpe:

| kind    |       N |   delta |   n |   sharpe |    net |   ypos |       x | eligible   |
|:--------|--------:|--------:|----:|---------:|-------:|-------:|--------:|:-----------|
| fixed   |   2.000 |   0.060 | 538 |    0.698 | 39.341 |      3 | nan     | True       |
| persist | nan     | nan     |  75 |    0.636 | 25.477 |      3 |   0.530 | False      |
| persist | nan     | nan     |  50 |    0.521 | 23.683 |      3 |   0.500 | False      |
| fixed   |   2.000 |   0.040 | 754 |    0.500 | 33.594 |      3 | nan     | True       |
| fixed   |   2.000 |   0.080 | 308 |    0.094 |  3.778 |      1 | nan     | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.70; replicate best-eligible median 0.68, p95 1.13; real beats 53% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.608e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.037 | +0.130 | +0.104 | +0.058 | +12.2 | [-0.021, +0.135] | 0.25 | NO |
| 20% | add | +0.060 | +0.247 | +0.200 | +0.100 | +25.2 | [-0.057, +0.251] | 0.25 | NO |
| 30% | add | +0.069 | +0.350 | +0.287 | +0.127 | +38.1 | [-0.104, +0.350] | 0.25 | NO |
| 50% | add | +0.057 | +0.508 | +0.427 | +0.142 | +64.1 | [-0.227, +0.492] | 0.25 | NO |
| 10% | const | +0.041 | +0.143 | +0.115 | +0.063 | +2.3 | [-0.025, +0.149] | 0.25 | NO |
| 20% | const | +0.066 | +0.301 | +0.245 | +0.116 | +5.3 | [-0.078, +0.303] | 0.25 | NO |
| 30% | const | +0.065 | +0.459 | +0.382 | +0.142 | +8.4 | [-0.180, +0.446] | 0.25 | NO |
| 50% | const | -0.058 | +0.623 | +0.579 | +0.040 | +14.5 | [-0.584, +0.639] | 0.25 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 599,105, Sharpe 0.66, maxDD 614,519, worst wk -230,417; H1: net 205,868, Sharpe 1.42, maxDD 153,645, worst wk -57,048; H2: net 269,115, Sharpe 1.28, maxDD 183,534, worst wk -95,666; all: net 1,074,088, Sharpe 0.84, maxDD 614,519, worst wk -230,417
Correlation with pair (weekly): clean +0.14, H1 -0.19, H2 -0.18, all +0.05; worst-decile weeks (n=17) corr +0.21, sleeve mean in those weeks $7,378, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.52 | 2.92 | 4.69 | -90,397 | -82,430 | 309,433 | -103,286 | 43.8 |
| clean | add 30% | 1.53 | 2.95 | 4.66 | -96,364 | -84,868 | 324,095 | -113,991 | 45.7 |
| clean | const 20% | 1.53 | 2.94 | 4.67 | -74,704 | -66,919 | 253,411 | -86,911 | 43.8 |
| clean | const 30% | 1.52 | 2.94 | 4.63 | -72,824 | -62,054 | 240,062 | -89,429 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.07 | 6.86 | 4.53 | -72,954 | -63,789 | 140,253 | -82,731 | 42.9 |
| H1 | add 30% | 3.18 | 7.20 | 4.63 | -70,626 | -62,669 | 141,563 | -85,631 | 39.3 |
| H1 | const 20% | 3.13 | 7.03 | 4.58 | -57,432 | -50,583 | 112,726 | -67,345 | 42.9 |
| H1 | const 30% | 3.29 | 7.57 | 4.76 | -48,223 | -42,860 | 100,273 | -62,551 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.50 | 5.48 | 3.73 | -78,977 | -72,353 | 218,615 | -82,524 | 44.4 |
| H2 | add 30% | 2.58 | 5.86 | 3.84 | -78,481 | -69,487 | 219,210 | -82,524 | 44.4 |
| H2 | const 20% | 2.54 | 5.67 | 3.78 | -62,983 | -56,516 | 175,130 | -66,020 | 44.4 |
| H2 | const 30% | 2.68 | 6.30 | 3.98 | -54,490 | -47,599 | 153,982 | -57,767 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.96 | 3.91 | 9.37 | -87,008 | -79,497 | 309,433 | -103,286 | 44.0 |
| all | add 30% | 1.98 | 4.00 | 9.28 | -91,197 | -80,464 | 324,095 | -113,991 | 44.6 |
| all | const 20% | 1.97 | 3.96 | 9.32 | -71,282 | -63,944 | 253,411 | -86,911 | 44.0 |
| all | const 30% | 2.00 | 4.05 | 9.17 | -67,609 | -57,959 | 240,062 | -89,429 | 43.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.060 / +0.247 / +0.200
- [FAIL] 3 worst week within share: all-in worst week +25.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.84 vs p95 1.15 (rank 0.78)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.057, +0.251]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.052 / +0.242 / +0.197
- [PASS] 6 worst-decile corr <=+0.30: +0.21
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section R4); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (740 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2401 | +0.0328 | 0.34 |
| fixed | 2401 | +0.0223 | 0.23 |
| scaled | 2401 | +0.0262 | 0.27 |

Plateau neighbours (all-in 20% uplift; selected +0.100):
- {'kind': 'fixed', 'N': '2', 'delta': '0.045'}: +0.135 (trades 1044)
- {'kind': 'fixed', 'N': '2', 'delta': '0.075'}: +0.042 (trades 480)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.54, p95 1.15, real 0.84. Standalone Sharpe at 2x slippage 0.80.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 180 | 22 | 1.26 |
| 2017 | 266 | 47 | 2.47 |
| 2018 | 394 | -0 | -0.01 |
| 2019 | 314 | -15 | -0.54 |
| 2020 | 441 | 27 | 0.59 |
| 2021 | 408 | 46 | 1.40 |
| 2022 | 398 | -72 | -2.03 |
| 2023 | 200 | 24 | 1.05 |
| 2024 | 276 | 30 | 1.00 |
| 2025 | 258 | 20 | 0.73 |
| 2026 | 125 | 17 | 1.19 |


## Beta / drift test (report): beta +0.479; alpha weekly Sharpe 0.53, 90% CI [-0.40, +1.39] (alpha CI includes zero).

DONE RW4