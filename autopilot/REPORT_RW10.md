# REPORT RW10
**Verdict: LEAD** (6/7 measured gates pass). Selected cell theta=0.1, c=0.0; additive @20% clean/H1/H2 +0.13/+1.29/+0.18; standalone all-in weekly Sharpe 1.69 (2013-26 0.80, dev 2013-22 0.26); pair-window trades 180. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

R10 I9 x K4 consensus: IBS dip-buy only when K4 agrees (4 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 4 cells, eligible (>= 100 clean trades): 3. Top cells by clean weekly Sharpe:

|   theta |     c |   n |   sharpe |    net |   ypos | eligible   |
|--------:|------:|----:|---------:|-------:|-------:|:-----------|
|   0.100 | 0.040 |  63 |    1.112 | 13.738 |      2 | False      |
|   0.100 | 0.000 | 104 |    1.061 | 19.118 |      2 | True       |
|   0.200 | 0.040 | 132 |    0.480 |  8.488 |      2 | True       |
|   0.200 | 0.000 | 207 |   -0.139 | -3.459 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.06; replicate best-eligible median 0.66, p95 1.58; real beats 87% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=5.033e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.074 | +0.685 | +0.101 | +0.158 | +15.2 | [+0.053, +0.270] | 0.20 | NO |
| 20% | add | +0.132 | +1.289 | +0.180 | +0.289 | +32.0 | [+0.086, +0.505] | 0.20 | NO |
| 30% | add | +0.174 | +1.779 | +0.236 | +0.392 | +53.8 | [+0.100, +0.704] | 0.20 | NO |
| 50% | add | +0.217 | +2.401 | +0.283 | +0.521 | +97.4 | [+0.078, +0.988] | 0.20 | NO |
| 10% | const | +0.082 | +0.757 | +0.111 | +0.174 | +5.3 | [+0.058, +0.298] | 0.20 | NO |
| 20% | const | +0.155 | +1.549 | +0.211 | +0.344 | +14.3 | [+0.095, +0.610] | 0.20 | NO |
| 30% | const | +0.207 | +2.229 | +0.276 | +0.485 | +27.3 | [+0.093, +0.902] | 0.20 | NO |
| 50% | const | +0.196 | +2.725 | +0.160 | +0.571 | +55.2 | [-0.101, +1.274] | 0.20 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 962,249, Sharpe 1.06, maxDD 408,171, worst wk -221,679; H1: net 1,368,578, Sharpe 4.35, maxDD 97,731, worst wk -12,395; H2: net 331,941, Sharpe 1.05, maxDD 176,080, worst wk -99,123; all: net 2,662,768, Sharpe 1.69, maxDD 408,171, worst wk -221,679
Correlation with pair (weekly): clean +0.15, H1 -0.14, H2 -0.05, all +0.06; worst-decile weeks (n=17) corr +0.25, sleeve mean in those weeks $-8,516, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.59 | 3.00 | 5.26 | -91,607 | -84,936 | 289,237 | -108,918 | 41.0 |
| clean | add 30% | 1.63 | 3.06 | 5.03 | -102,076 | -90,605 | 321,563 | -126,902 | 42.9 |
| clean | const 20% | 1.61 | 3.04 | 5.14 | -77,473 | -70,217 | 244,320 | -94,328 | 43.8 |
| clean | const 30% | 1.67 | 3.07 | 4.80 | -80,876 | -68,526 | 254,188 | -105,016 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 4.12 | 9.64 | 6.28 | -77,610 | -65,504 | 138,157 | -78,287 | 32.1 |
| H1 | add 30% | 4.61 | 11.33 | 7.26 | -77,610 | -65,242 | 138,420 | -78,287 | 28.6 |
| H1 | const 20% | 4.38 | 10.49 | 6.77 | -62,088 | -52,298 | 110,631 | -62,630 | 32.1 |
| H1 | const 30% | 5.06 | 13.46 | 8.51 | -54,327 | -45,433 | 97,130 | -54,801 | 28.6 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.48 | 5.16 | 3.56 | -85,956 | -82,065 | 232,268 | -92,259 | 41.7 |
| H2 | add 30% | 2.53 | 5.29 | 3.57 | -89,667 | -83,505 | 241,268 | -99,680 | 41.7 |
| H2 | const 20% | 2.51 | 5.23 | 3.58 | -70,249 | -66,228 | 188,783 | -76,776 | 41.7 |
| H2 | const 30% | 2.57 | 5.39 | 3.52 | -66,106 | -59,749 | 179,591 | -76,455 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.14 | 4.23 | 11.12 | -89,056 | -83,399 | 289,237 | -108,918 | 39.9 |
| all | add 30% | 2.25 | 4.43 | 10.83 | -96,686 | -87,406 | 321,563 | -126,902 | 40.5 |
| all | const 20% | 2.20 | 4.34 | 10.97 | -74,297 | -68,322 | 244,320 | -94,328 | 41.7 |
| all | const 30% | 2.34 | 4.60 | 10.54 | -74,697 | -64,790 | 254,188 | -105,016 | 39.3 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.132 / +1.289 / +0.180
- [FAIL] 3 worst week within share: all-in worst week +32.0% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.69 vs p95 1.12 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.086, +0.505]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.126 / +1.282 / +0.176
- [PASS] 6 worst-decile corr <=+0.30: +0.25
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section R10); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (180 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 264 | +0.0825 | 0.30 |
| fixed | 264 | +0.0712 | 0.26 |
| scaled | 264 | +0.0759 | 0.27 |

Plateau neighbours (all-in 20% uplift; selected +0.289):
- {'theta': '0.075', 'c': '0.0'}: +0.232 (trades 142)
- {'theta': '0.125', 'c': '0.0'}: +0.291 (trades 220)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.33, p95 1.12, real 1.69. Standalone Sharpe at 2x slippage 1.67.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 17 | 1 | 0.09 |
| 2017 | 29 | 5 | 0.70 |
| 2018 | 36 | -5 | -0.53 |
| 2019 | 45 | 6 | 0.86 |
| 2020 | 50 | 11 | 0.88 |
| 2021 | 73 | 4 | 0.27 |
| 2022 | 14 | -4 | -0.52 |
| 2023 | 55 | 14 | 1.48 |
| 2024 | 64 | 18 | 1.88 |
| 2025 | 50 | 24 | 2.56 |
| 2026 | 43 | 13 | 1.79 |


## Beta / drift test (report): beta +0.092; alpha weekly Sharpe 1.52, 90% CI [+0.65, +2.32] (alpha CI lower bound > 0).

DONE RW10