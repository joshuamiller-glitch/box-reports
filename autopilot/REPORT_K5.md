# REPORT K5
**Verdict: NO** (3/7 measured gates pass). Selected cell sp=ZN-ZT, sig=mr1.5, N=5; additive @20% clean/H1/H2 +0.09/+0.08/-0.26; standalone all-in weekly Sharpe 0.24 (2013-26 -0.19, dev 2013-22 -0.33); pair-window trades 92 (SMALL-SAMPLE). Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

K5 Treasury curve spread sleeve (ZN-ZT, ZB-ZN, ZB-ZF), mean reversion or trend, equal-ADR legs (18 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 18 cells, eligible (>= 40 clean trades): 9. Top cells by clean weekly Sharpe:

| sp    | sig   |   N |   n |   sharpe |    net |   ypos | eligible   |
|:------|:------|----:|----:|---------:|-------:|-------:|:-----------|
| ZN-ZT | mr1.5 |  10 |  36 |    0.987 |  8.168 |      2 | False      |
| ZN-ZT | mr1.5 |   5 |  58 |    0.770 |  5.266 |      2 | True       |
| ZN-ZT | mr2.0 |   5 |  36 |    0.758 |  4.411 |      3 | False      |
| ZB-ZF | mr1.5 |  10 |  31 |    0.590 |  4.585 |      3 | False      |
| ZB-ZF | mr1.5 |   5 |  48 |    0.506 |  3.329 |      2 | True       |
| ZB-ZF | mr2.0 |   5 |  36 |    0.469 |  2.946 |      2 | False      |
| ZN-ZT | mr2.0 |  10 |  27 |    0.467 |  3.501 |      1 | False      |
| ZB-ZF | mr2.0 |  10 |  23 |    0.127 |  0.876 |      1 | False      |
| ZB-ZN | mr1.5 |  10 |  31 |   -0.173 | -0.922 |      1 | False      |
| ZB-ZN | mr2.0 |  10 |  23 |   -0.180 | -0.754 |      1 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.77; replicate best-eligible median -0.12, p95 0.48; real beats 97% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.333e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.053 | +0.048 | -0.124 | +0.005 | +3.0 | [-0.077, +0.088] | 0.21 | NO |
| 20% | add | +0.089 | +0.079 | -0.259 | -0.004 | +12.1 | [-0.170, +0.161] | 0.21 | NO |
| 30% | add | +0.111 | +0.093 | -0.404 | -0.027 | +21.1 | [-0.268, +0.217] | 0.21 | NO |
| 50% | add | +0.120 | +0.067 | -0.708 | -0.101 | +39.2 | [-0.479, +0.294] | 0.21 | NO |
| 10% | const | +0.057 | +0.052 | -0.138 | +0.005 | -6.4 | [-0.087, +0.097] | 0.21 | NO |
| 20% | const | +0.102 | +0.088 | -0.331 | -0.014 | -6.7 | [-0.219, +0.191] | 0.21 | NO |
| 30% | const | +0.122 | +0.084 | -0.598 | -0.071 | -7.1 | [-0.403, +0.274] | 0.21 | NO |
| 50% | const | +0.035 | -0.224 | -1.440 | -0.357 | +28.0 | [-0.991, +0.307] | 0.21 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 701,798, Sharpe 0.77, maxDD 460,626, worst wk -216,112; H1: net 30,708, Sharpe 0.19, maxDD 198,117, worst wk -75,733; H2: net -413,607, Sharpe -1.66, maxDD 497,182, worst wk -125,692; all: net 318,899, Sharpe 0.24, maxDD 580,859, worst wk -216,112
Correlation with pair (weekly): clean +0.11, H1 -0.19, H2 -0.04, all +0.06; worst-decile weeks (n=17) corr +0.01, sleeve mean in those weeks $4,031, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.55 | 3.10 | 5.29 | -83,021 | -78,282 | 277,942 | -92,476 | 44.8 |
| clean | add 30% | 1.57 | 3.18 | 5.56 | -85,612 | -79,130 | 276,858 | -99,934 | 43.8 |
| clean | const 20% | 1.56 | 3.14 | 5.43 | -67,453 | -62,777 | 221,920 | -76,964 | 44.8 |
| clean | const 30% | 1.58 | 3.21 | 5.92 | -63,709 | -58,584 | 192,825 | -76,667 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.91 | 6.14 | 3.99 | -77,866 | -66,201 | 150,543 | -78,800 | 42.9 |
| H1 | add 30% | 2.92 | 6.11 | 4.02 | -77,994 | -66,286 | 149,958 | -79,056 | 39.3 |
| H1 | const 20% | 2.92 | 6.13 | 4.00 | -62,344 | -52,995 | 120,200 | -63,143 | 39.3 |
| H1 | const 30% | 2.91 | 6.02 | 4.07 | -54,711 | -48,157 | 104,444 | -55,570 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.04 | 4.01 | 3.20 | -82,637 | -78,363 | 211,778 | -85,621 | 44.4 |
| H2 | add 30% | 1.89 | 3.65 | 3.02 | -83,412 | -78,667 | 210,652 | -87,170 | 44.4 |
| H2 | const 20% | 1.96 | 3.83 | 3.13 | -66,420 | -62,526 | 168,293 | -69,117 | 44.4 |
| H2 | const 30% | 1.70 | 3.18 | 2.59 | -59,085 | -56,611 | 158,008 | -62,413 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.85 | 3.70 | 9.89 | -82,467 | -78,252 | 277,942 | -92,476 | 44.6 |
| all | add 30% | 1.83 | 3.66 | 10.04 | -84,394 | -79,183 | 276,858 | -99,934 | 43.5 |
| all | const 20% | 1.84 | 3.69 | 9.97 | -66,744 | -62,838 | 221,920 | -76,964 | 44.0 |
| all | const 30% | 1.78 | 3.56 | 10.24 | -61,857 | -57,664 | 192,825 | -76,667 | 41.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.089 / +0.079 / -0.259
- [PASS] 3 worst week within share: all-in worst week +12.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.24 vs p95 0.03 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.170, +0.161]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.071 / -0.066 / -0.421
- [PASS] 6 worst-decile corr <=+0.30: +0.01
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K5); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (92 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 267 | +0.0642 | 0.39 |
| fixed | 267 | -0.0530 | -0.33 |
| scaled | 267 | -0.0530 | -0.33 |

Plateau neighbours (all-in 20% uplift; selected -0.004):
- {'sp': 'ZN-ZT', 'sig': 'mr1.12', 'N': '5'}: -0.114 (trades 111)
- {'sp': 'ZN-ZT', 'sig': 'mr1.88', 'N': '5'}: +0.016 (trades 62)
- {'sp': 'ZN-ZT', 'sig': 'mr1.5', 'N': '4'}: -0.024 (trades 106)
- {'sp': 'ZN-ZT', 'sig': 'mr1.5', 'N': '6'}: -0.016 (trades 83)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.72, p95 0.03, real 0.24. Standalone Sharpe at 2x slippage -0.66.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 26 | 1 | 0.24 |
| 2014 | 25 | -0 | -0.12 |
| 2015 | 24 | -3 | -0.63 |
| 2016 | 25 | -6 | -1.25 |
| 2017 | 28 | -1 | -0.40 |
| 2018 | 27 | -5 | -1.67 |
| 2019 | 29 | -3 | -0.83 |
| 2020 | 22 | 4 | 0.87 |
| 2021 | 32 | 2 | 0.43 |
| 2022 | 29 | -4 | -0.82 |
| 2023 | 28 | 4 | 0.75 |
| 2024 | 28 | -1 | -0.26 |
| 2025 | 30 | 3 | 1.00 |
| 2026 | 23 | -3 | -1.35 |


DONE K5