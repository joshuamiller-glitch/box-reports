# REPORT RX2
**Verdict: LEAD** (6/7 measured gates pass). Selected cell x=2, N=2, m=0.5; additive @20% clean/H1/H2 +0.19/+1.02/+0.19; standalone all-in weekly Sharpe 1.75 (2013-26 0.67, dev 2013-22 0.16); pair-window trades 200. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RX2 I9 tail fix: size cut after a day where the sleeve lost >= x ADR units (8 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 100 clean trades): 8. Top cells by clean weekly Sharpe:

|   x |   N |     m |   n |   sharpe |    net |   ypos | eligible   |
|----:|----:|------:|----:|---------:|-------:|-------:|:-----------|
|   2 |   2 | 0.000 | 120 |    1.293 | 28.061 |      3 | True       |
|   2 |   2 | 0.500 | 120 |    1.293 | 28.061 |      3 | True       |
|   1 |   2 | 0.500 | 120 |    1.229 | 26.256 |      3 | True       |
|   2 |   5 | 0.500 | 120 |    1.197 | 25.325 |      3 | True       |
|   1 |   5 | 0.500 | 120 |    1.195 | 24.098 |      3 | True       |
|   1 |   2 | 0.000 | 115 |    1.149 | 24.450 |      3 | True       |
|   2 |   5 | 0.000 | 114 |    1.078 | 22.589 |      3 | True       |
|   1 |   5 | 0.000 | 106 |    0.964 | 19.009 |      3 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.29; replicate best-eligible median 1.04, p95 1.59; real beats 70% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.177e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.103 | +0.546 | +0.104 | +0.164 | +15.1 | [+0.060, +0.278] | 0.28 | NO |
| 20% | add | +0.188 | +1.020 | +0.189 | +0.302 | +41.9 | [+0.099, +0.525] | 0.28 | NO |
| 30% | add | +0.255 | +1.404 | +0.253 | +0.413 | +68.6 | [+0.121, +0.735] | 0.28 | NO |
| 50% | add | +0.341 | +1.905 | +0.317 | +0.560 | +122.0 | [+0.113, +1.041] | 0.28 | NO |
| 10% | const | +0.114 | +0.603 | +0.115 | +0.180 | +6.3 | [+0.065, +0.306] | 0.28 | NO |
| 20% | const | +0.224 | +1.223 | +0.224 | +0.361 | +24.2 | [+0.113, +0.634] | 0.28 | NO |
| 30% | const | +0.317 | +1.763 | +0.303 | +0.518 | +42.1 | [+0.123, +0.950] | 0.28 | NO |
| 50% | const | +0.380 | +2.219 | +0.229 | +0.642 | +77.8 | [-0.045, +1.360] | 0.28 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,172,132, Sharpe 1.29, maxDD 381,568, worst wk -220,555; H1: net 1,153,963, Sharpe 4.00, maxDD 87,017, worst wk -87,017; H2: net 321,819, Sharpe 1.07, maxDD 167,375, worst wk -82,261; all: net 2,647,914, Sharpe 1.75, maxDD 381,568, worst wk -220,555
Correlation with pair (weekly): clean +0.11, H1 -0.06, H2 -0.08, all +0.04; worst-decile weeks (n=17) corr +0.27, sleeve mean in those weeks $-6,059, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.65 | 3.11 | 5.43 | -91,419 | -84,420 | 288,007 | -117,062 | 40.0 |
| clean | add 30% | 1.71 | 3.21 | 5.29 | -100,299 | -89,409 | 317,916 | -139,118 | 42.9 |
| clean | const 20% | 1.68 | 3.17 | 5.37 | -76,288 | -69,431 | 241,888 | -102,472 | 41.0 |
| clean | const 30% | 1.78 | 3.28 | 5.12 | -79,099 | -67,301 | 250,540 | -117,232 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.85 | 9.06 | 5.97 | -77,610 | -65,594 | 138,068 | -78,287 | 35.7 |
| H1 | add 30% | 4.23 | 10.41 | 6.80 | -77,610 | -65,376 | 138,286 | -78,287 | 35.7 |
| H1 | const 20% | 4.05 | 9.75 | 6.39 | -62,088 | -52,388 | 110,541 | -62,630 | 35.7 |
| H1 | const 30% | 4.59 | 11.99 | 7.85 | -54,327 | -45,567 | 96,996 | -54,801 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.48 | 5.17 | 3.59 | -84,750 | -81,575 | 229,743 | -89,734 | 44.4 |
| H2 | add 30% | 2.55 | 5.28 | 3.64 | -87,773 | -82,770 | 235,902 | -95,893 | 38.9 |
| H2 | const 20% | 2.52 | 5.23 | 3.62 | -68,987 | -65,738 | 186,258 | -74,251 | 41.7 |
| H2 | const 30% | 2.60 | 5.38 | 3.63 | -64,213 | -59,014 | 173,522 | -72,668 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.16 | 4.25 | 11.16 | -88,738 | -82,949 | 288,007 | -117,062 | 39.9 |
| all | add 30% | 2.27 | 4.46 | 10.94 | -95,170 | -86,458 | 317,916 | -139,118 | 40.5 |
| all | const 20% | 2.22 | 4.36 | 11.07 | -73,286 | -67,698 | 241,888 | -102,472 | 39.9 |
| all | const 30% | 2.37 | 4.65 | 10.67 | -73,091 | -63,825 | 250,540 | -117,232 | 38.7 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.188 / +1.020 / +0.189
- [FAIL] 3 worst week within share: all-in worst week +41.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.75 vs p95 1.12 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.099, +0.525]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.182 / +1.014 / +0.185
- [PASS] 6 worst-decile corr <=+0.30: +0.27
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RX2); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (200 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 419 | +0.0559 | 0.22 |
| fixed | 419 | +0.0419 | 0.16 |
| scaled | 419 | +0.0494 | 0.19 |

Plateau neighbours (all-in 20% uplift; selected +0.302):
- {'x': '1.5', 'N': '2', 'm': '0.5'}: +0.302 (trades 200)
- {'x': '2.5', 'N': '2', 'm': '0.5'}: +0.305 (trades 200)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.39, p95 1.12, real 1.75. Standalone Sharpe at 2x slippage 1.73.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 6 | 2 | 1.38 |
| 2014 | 50 | 6 | 0.61 |
| 2015 | 55 | -8 | -0.61 |
| 2016 | 30 | -7 | -0.49 |
| 2017 | 42 | 16 | 1.55 |
| 2018 | 43 | -12 | -0.94 |
| 2019 | 47 | 8 | 1.05 |
| 2020 | 52 | 12 | 0.98 |
| 2021 | 80 | 4 | 0.29 |
| 2022 | 14 | -4 | -0.52 |
| 2023 | 71 | 22 | 1.71 |
| 2024 | 70 | 23 | 2.10 |
| 2025 | 52 | 24 | 2.38 |
| 2026 | 46 | 14 | 1.74 |


DONE RX2