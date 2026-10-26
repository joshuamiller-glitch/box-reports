# REPORT RX3
**Verdict: LEAD** (6/7 measured gates pass). Selected cell trig=r5b, N=3; additive @20% clean/H1/H2 +0.19/+1.02/+0.19; standalone all-in weekly Sharpe 1.77 (2013-26 0.68, dev 2013-22 0.19); pair-window trades 200. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RX3 I9 tail fix: stress-week stand-down walk-forward (ES 5-day drop or VIX 2-day jump triggers no new entries for N days; 8 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 100 clean trades): 8. Top cells by clean weekly Sharpe:

| trig   |   N |   n |   sharpe |    net |   ypos | eligible   |
|:-------|----:|----:|---------:|-------:|-------:|:-----------|
| r5b    |   5 | 120 |    1.293 | 28.061 |      3 | True       |
| r5b    |   3 | 120 |    1.293 | 28.061 |      3 | True       |
| r5a    |   5 | 118 |    1.268 | 27.470 |      3 | True       |
| r5a    |   3 | 118 |    1.268 | 27.470 |      3 | True       |
| vc1    |   3 | 115 |    1.201 | 25.468 |      3 | True       |
| vc1    |   5 | 115 |    1.201 | 25.468 |      3 | True       |
| vc2    |   3 | 117 |    1.150 | 24.735 |      3 | True       |
| vc2    |   5 | 117 |    1.150 | 24.735 |      3 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.29; replicate best-eligible median 0.70, p95 1.60; real beats 87% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.177e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.103 | +0.549 | +0.107 | +0.165 | +15.1 | [+0.062, +0.279] | 0.28 | NO |
| 20% | add | +0.188 | +1.020 | +0.194 | +0.305 | +41.9 | [+0.101, +0.527] | 0.28 | NO |
| 30% | add | +0.255 | +1.399 | +0.259 | +0.417 | +68.6 | [+0.125, +0.738] | 0.28 | NO |
| 50% | add | +0.341 | +1.890 | +0.328 | +0.565 | +122.0 | [+0.120, +1.048] | 0.28 | NO |
| 10% | const | +0.114 | +0.606 | +0.117 | +0.182 | +6.3 | [+0.067, +0.308] | 0.28 | NO |
| 20% | const | +0.224 | +1.222 | +0.229 | +0.364 | +24.2 | [+0.116, +0.637] | 0.28 | NO |
| 30% | const | +0.317 | +1.751 | +0.312 | +0.523 | +42.1 | [+0.127, +0.953] | 0.28 | NO |
| 50% | const | +0.380 | +2.196 | +0.246 | +0.649 | +77.8 | [-0.038, +1.364] | 0.28 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,172,132, Sharpe 1.29, maxDD 381,568, worst wk -220,555; H1: net 1,182,257, Sharpe 4.04, maxDD 87,017, worst wk -87,017; H2: net 328,235, Sharpe 1.09, maxDD 160,959, worst wk -82,261; all: net 2,682,624, Sharpe 1.77, maxDD 381,568, worst wk -220,555
Correlation with pair (weekly): clean +0.11, H1 -0.04, H2 -0.08, all +0.04; worst-decile weeks (n=17) corr +0.27, sleeve mean in those weeks $-6,059, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.65 | 3.11 | 5.43 | -91,419 | -84,420 | 288,007 | -117,062 | 40.0 |
| clean | add 30% | 1.71 | 3.21 | 5.29 | -100,299 | -89,409 | 317,916 | -139,118 | 42.9 |
| clean | const 20% | 1.68 | 3.17 | 5.37 | -76,288 | -69,431 | 241,888 | -102,472 | 41.0 |
| clean | const 30% | 1.78 | 3.28 | 5.12 | -79,099 | -67,301 | 250,540 | -117,232 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.85 | 9.13 | 6.01 | -77,610 | -65,594 | 138,068 | -78,287 | 35.7 |
| H1 | add 30% | 4.23 | 10.51 | 6.86 | -77,610 | -65,376 | 138,286 | -78,287 | 35.7 |
| H1 | const 20% | 4.05 | 9.83 | 6.44 | -62,088 | -52,388 | 110,541 | -62,630 | 35.7 |
| H1 | const 30% | 4.58 | 12.12 | 7.94 | -54,327 | -45,567 | 96,996 | -54,801 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.49 | 5.18 | 3.60 | -84,750 | -81,575 | 229,743 | -89,734 | 44.4 |
| H2 | add 30% | 2.55 | 5.30 | 3.64 | -87,773 | -82,770 | 235,902 | -95,893 | 38.9 |
| H2 | const 20% | 2.52 | 5.24 | 3.62 | -68,987 | -65,738 | 186,258 | -74,251 | 41.7 |
| H2 | const 30% | 2.61 | 5.40 | 3.64 | -64,213 | -59,014 | 173,522 | -72,668 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.16 | 4.26 | 11.19 | -88,738 | -82,949 | 288,007 | -117,062 | 39.9 |
| all | add 30% | 2.27 | 4.47 | 10.98 | -95,170 | -86,458 | 317,916 | -139,118 | 40.5 |
| all | const 20% | 2.22 | 4.37 | 11.10 | -73,286 | -67,698 | 241,888 | -102,472 | 39.9 |
| all | const 30% | 2.38 | 4.67 | 10.71 | -73,091 | -63,825 | 250,540 | -117,232 | 38.7 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.188 / +1.020 / +0.194
- [FAIL] 3 worst week within share: all-in worst week +41.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.77 vs p95 1.05 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.101, +0.527]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.182 / +1.015 / +0.190
- [PASS] 6 worst-decile corr <=+0.30: +0.27
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RX3); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (200 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 416 | +0.0653 | 0.24 |
| fixed | 416 | +0.0511 | 0.19 |
| scaled | 416 | +0.0587 | 0.22 |

Plateau neighbours (all-in 20% uplift; selected +0.305):
- {'trig': 'r5b', 'N': '2'}: +0.305 (trades 200)
- {'trig': 'r5b', 'N': '4'}: +0.305 (trades 200)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.32, p95 1.05, real 1.77. Standalone Sharpe at 2x slippage 1.74.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 6 | 2 | 1.38 |
| 2014 | 50 | 11 | 0.72 |
| 2015 | 55 | -8 | -0.62 |
| 2016 | 30 | -7 | -0.49 |
| 2017 | 42 | 16 | 1.58 |
| 2018 | 40 | -13 | -1.07 |
| 2019 | 47 | 8 | 1.05 |
| 2020 | 52 | 12 | 0.98 |
| 2021 | 80 | 5 | 0.34 |
| 2022 | 14 | -4 | -0.52 |
| 2023 | 71 | 22 | 1.71 |
| 2024 | 70 | 23 | 2.10 |
| 2025 | 52 | 25 | 2.41 |
| 2026 | 46 | 15 | 1.75 |


DONE RX3