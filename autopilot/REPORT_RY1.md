# REPORT RY1
**Verdict: NO** (1/7 measured gates pass). Selected cell rule=r3; additive @20% clean/H1/H2 +0.13/+0.16/+0.00; standalone all-in weekly Sharpe 0.65 (2013-26 0.43, dev 2013-22 0.41); pair-window trades 1680. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RY1 VIX-state timing without ML: long the four indices for one day when a simple VIX rule is ON (6 rules), tested with the RW1 criterion against exposure-matched buy-and-hold.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 6 cells, eligible (>= 100 clean trades): 6. Top cells by clean weekly Sharpe:

| rule   |    n |   sharpe |    net |   ypos | eligible   |
|:-------|-----:|---------:|-------:|-------:|:-----------|
| r3     | 1072 |    0.913 | 49.482 |      3 | True       |
| r6     | 1032 |    0.817 | 43.948 |      3 | True       |
| r5     | 1004 |    0.704 | 35.899 |      2 | True       |
| r1     | 1004 |    0.704 | 35.899 |      2 | True       |
| r2     | 1868 |    0.459 | 33.964 |      3 | True       |
| r4     | 1140 |   -0.016 | -0.982 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.91; replicate best-eligible median 0.63, p95 0.95; real beats 90% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.672e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.075 | +0.093 | +0.011 | +0.057 | +9.5 | [-0.035, +0.150] | 0.57 | NO |
| 20% | add | +0.133 | +0.160 | +0.004 | +0.095 | +25.6 | [-0.085, +0.277] | 0.57 | NO |
| 30% | add | +0.175 | +0.195 | -0.019 | +0.114 | +41.8 | [-0.153, +0.383] | 0.57 | NO |
| 50% | add | +0.215 | +0.165 | -0.104 | +0.107 | +74.0 | [-0.321, +0.534] | 0.57 | NO |
| 10% | const | +0.082 | +0.102 | +0.011 | +0.062 | +0.2 | [-0.040, +0.165] | 0.57 | NO |
| 20% | const | +0.156 | +0.182 | -0.005 | +0.107 | +7.0 | [-0.115, +0.334] | 0.57 | NO |
| 30% | const | +0.206 | +0.191 | -0.069 | +0.116 | +13.8 | [-0.255, +0.490] | 0.57 | NO |
| 50% | const | +0.167 | -0.308 | -0.417 | -0.061 | +27.3 | [-0.779, +0.620] | 0.57 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 810,675, Sharpe 0.89, maxDD 384,525, worst wk -133,115; H1: net 28,540, Sharpe 0.13, maxDD 176,045, worst wk -176,045; H2: net 84,752, Sharpe 0.29, maxDD 262,447, worst wk -153,795; all: net 923,967, Sharpe 0.65, maxDD 384,525, worst wk -176,045
Correlation with pair (weekly): clean +0.04, H1 -0.32, H2 +0.03, all -0.01; worst-decile weeks (n=17) corr -0.04, sleeve mean in those weeks $21,084, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.59 | 3.03 | 5.24 | -91,786 | -84,048 | 284,507 | -103,682 | 42.9 |
| clean | add 30% | 1.63 | 3.09 | 5.49 | -99,209 | -87,906 | 286,706 | -116,993 | 41.9 |
| clean | const 20% | 1.62 | 3.07 | 5.37 | -76,398 | -68,781 | 228,485 | -88,270 | 42.9 |
| clean | const 30% | 1.67 | 3.12 | 5.73 | -76,127 | -65,117 | 204,783 | -93,875 | 39.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.99 | 6.54 | 4.08 | -72,409 | -62,563 | 146,842 | -85,068 | 39.3 |
| H1 | add 30% | 3.02 | 6.66 | 3.98 | -69,809 | -60,830 | 151,447 | -89,136 | 32.1 |
| H1 | const 20% | 3.01 | 6.61 | 4.03 | -56,888 | -49,357 | 119,316 | -69,682 | 32.1 |
| H1 | const 30% | 3.02 | 6.73 | 3.71 | -48,033 | -41,021 | 114,371 | -66,056 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.30 | 4.96 | 3.24 | -79,483 | -72,364 | 240,176 | -84,839 | 44.4 |
| H2 | add 30% | 2.28 | 5.04 | 3.13 | -79,239 | -71,873 | 251,552 | -88,551 | 44.4 |
| H2 | const 20% | 2.29 | 5.00 | 3.18 | -63,489 | -57,695 | 196,691 | -69,356 | 44.4 |
| H2 | const 30% | 2.23 | 5.11 | 3.00 | -56,162 | -49,909 | 186,324 | -65,326 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.95 | 3.86 | 10.09 | -89,166 | -80,832 | 284,507 | -103,682 | 42.9 |
| all | add 30% | 1.97 | 3.90 | 10.33 | -94,979 | -82,926 | 286,706 | -116,993 | 41.1 |
| all | const 20% | 1.96 | 3.89 | 10.21 | -73,658 | -65,427 | 228,485 | -88,270 | 41.7 |
| all | const 30% | 1.97 | 3.90 | 10.53 | -71,717 | -60,523 | 204,783 | -93,875 | 39.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.133 / +0.160 / +0.004
- [FAIL] 3 worst week within share: all-in worst week +25.6% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.65 vs p95 0.87 (rank 0.79)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.085, +0.277]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.115 / +0.142 / -0.008
- [PASS] 6 worst-decile corr <=+0.30: -0.04
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RY1); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1680 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 4851 | +0.0332 | 0.69 |
| fixed | 4851 | +0.0198 | 0.41 |
| scaled | 4851 | +0.0267 | 0.55 |

Plateau neighbours (all-in 20% uplift; selected +0.095):

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.45, p95 0.87, real 0.65. Standalone Sharpe at 2x slippage 0.57.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 384 | 17 | 0.76 |
| 2014 | 377 | -4 | -0.19 |
| 2015 | 417 | -22 | -1.00 |
| 2016 | 414 | -8 | -0.32 |
| 2017 | 452 | 52 | 2.40 |
| 2018 | 524 | 0 | 0.02 |
| 2019 | 600 | 37 | 1.69 |
| 2020 | 543 | 51 | 2.22 |
| 2021 | 572 | -3 | -0.12 |
| 2022 | 568 | -25 | -0.98 |
| 2023 | 572 | 21 | 0.62 |
| 2024 | 500 | 2 | 0.10 |
| 2025 | 560 | 22 | 0.90 |
| 2026 | 388 | 3 | 0.16 |


## Beta / drift test (report): beta +0.372; alpha weekly Sharpe 0.41, 90% CI [-0.50, +1.31] (alpha CI includes zero).

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 0.65 vs scaled buy-and-hold 0.65; paired-bootstrap 90% CI of the difference [-0.73, +0.73]; exposure ES 52.4%, NQ 52.4%, RTY 52.4%, YM 52.4%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 0.89 | 0.46 | +0.133 | +0.033 |
| H1 | 0.13 | 1.59 | +0.160 | +0.358 |
| H2 | 0.29 | 0.61 | +0.004 | +0.099 |
| all | 0.65 | 0.65 | +0.095 | +0.081 |
DONE RY1