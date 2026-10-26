# REPORT L7
**Verdict: NO** (1/7 measured gates pass). Selected cell sp=6A-6C, sig=mr1.5, N=5; additive @20% clean/H1/H2 +0.16/-0.36/+0.24; standalone all-in weekly Sharpe 0.70 (2013-26 0.12, dev 2013-22 0.00); pair-window trades 94 (SMALL-SAMPLE). Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

L7 FX cross-rate spread sleeve (6E-6B, 6A-6C, 6B-6A, 6E-6C, 6J-6E; 30 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 30 cells, eligible (>= 40 clean trades): 15. Top cells by clean weekly Sharpe:

| sp    | sig   |   N |   n |   sharpe |   net |   ypos | eligible   |
|:------|:------|----:|----:|---------:|------:|-------:|:-----------|
| 6A-6C | mr2.0 |   5 |  37 |    1.120 | 8.937 |      3 | False      |
| 6A-6C | mr1.5 |   5 |  58 |    0.905 | 8.493 |      2 | True       |
| 6E-6C | mr2.0 |  10 |  25 |    0.560 | 7.834 |      2 | False      |
| 6E-6B | mr2.0 |   5 |  35 |    0.491 | 4.479 |      2 | False      |
| 6A-6C | mr1.5 |  10 |  37 |    0.484 | 5.996 |      2 | False      |
| 6E-6C | mr1.5 |  10 |  33 |    0.473 | 7.298 |      2 | False      |
| 6E-6B | mr1.5 |  10 |  33 |    0.452 | 5.069 |      2 | False      |
| 6E-6C | mr2.0 |   5 |  33 |    0.405 | 4.468 |      2 | False      |
| 6E-6C | mr1.5 |   5 |  52 |    0.389 | 5.436 |      2 | True       |
| 6A-6C | mr2.0 |  10 |  27 |    0.378 | 4.257 |      2 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.91; replicate best-eligible median 0.36, p95 0.96; real beats 93% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=9.739e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.086 | -0.160 | +0.133 | +0.063 | +12.0 | [-0.035, +0.164] | 0.49 | NO |
| 20% | add | +0.156 | -0.356 | +0.240 | +0.106 | +24.1 | [-0.089, +0.305] | 0.49 | NO |
| 30% | add | +0.209 | -0.577 | +0.321 | +0.128 | +36.2 | [-0.159, +0.420] | 0.49 | NO |
| 50% | add | +0.265 | -1.042 | +0.417 | +0.119 | +62.6 | [-0.331, +0.573] | 0.49 | NO |
| 10% | const | +0.095 | -0.180 | +0.146 | +0.069 | +2.0 | [-0.040, +0.181] | 0.49 | NO |
| 20% | const | +0.185 | -0.464 | +0.283 | +0.119 | +4.1 | [-0.121, +0.366] | 0.49 | NO |
| 30% | const | +0.252 | -0.876 | +0.392 | +0.129 | +7.2 | [-0.268, +0.529] | 0.49 | NO |
| 50% | const | +0.223 | -2.003 | +0.430 | -0.057 | +31.3 | [-0.791, +0.689] | 0.49 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 780,479, Sharpe 0.86, maxDD 494,189, worst wk -283,064; H1: net -325,959, Sharpe -1.26, maxDD 338,873, worst wk -174,512; H2: net 591,777, Sharpe 1.82, maxDD 278,149, worst wk -109,100; all: net 1,046,297, Sharpe 0.70, maxDD 575,802, worst wk -283,064
Correlation with pair (weekly): clean -0.05, H1 -0.05, H2 +0.14, all -0.01; worst-decile weeks (n=17) corr +0.42, sleeve mean in those weeks $-6,029, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.62 | 3.08 | 5.93 | -82,724 | -80,582 | 250,548 | -88,807 | 40.0 |
| clean | add 30% | 1.67 | 3.18 | 5.82 | -85,662 | -82,084 | 268,968 | -94,581 | 41.0 |
| clean | const 20% | 1.64 | 3.13 | 5.87 | -67,320 | -65,066 | 207,806 | -73,355 | 41.0 |
| clean | const 30% | 1.71 | 3.24 | 5.69 | -62,703 | -59,072 | 204,855 | -71,404 | 40.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.47 | 5.12 | 3.80 | -70,153 | -64,273 | 138,962 | -71,474 | 39.3 |
| H1 | add 30% | 2.25 | 4.43 | 3.48 | -69,355 | -67,604 | 142,664 | -69,965 | 39.3 |
| H1 | const 20% | 2.36 | 4.78 | 3.67 | -54,631 | -52,751 | 111,584 | -56,087 | 39.3 |
| H1 | const 30% | 1.95 | 3.57 | 3.01 | -57,674 | -54,627 | 105,597 | -64,682 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.53 | 5.08 | 4.26 | -101,935 | -86,540 | 206,500 | -102,397 | 38.9 |
| H2 | add 30% | 2.62 | 5.17 | 4.67 | -112,358 | -91,505 | 201,037 | -112,383 | 38.9 |
| H2 | const 20% | 2.58 | 5.13 | 4.46 | -85,717 | -70,806 | 163,015 | -85,892 | 38.9 |
| H2 | const 30% | 2.69 | 5.21 | 5.00 | -88,032 | -69,449 | 142,194 | -88,487 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.96 | 3.81 | 11.55 | -86,606 | -81,523 | 250,548 | -102,397 | 39.9 |
| all | add 30% | 1.98 | 3.82 | 11.15 | -90,951 | -83,409 | 268,968 | -112,383 | 40.5 |
| all | const 20% | 1.97 | 3.82 | 11.34 | -71,023 | -65,944 | 207,806 | -85,892 | 40.5 |
| all | const 30% | 1.98 | 3.75 | 10.71 | -68,551 | -61,607 | 204,855 | -88,487 | 39.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.156 / -0.356 / +0.240
- [FAIL] 3 worst week within share: all-in worst week +24.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.70 vs p95 0.54 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.089, +0.305]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.082 / -0.433 / +0.163
- [FAIL] 6 worst-decile corr <=+0.30: +0.42
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section L7); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (94 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 276 | +0.0793 | 0.26 |
| fixed | 276 | +0.0003 | 0.00 |
| scaled | 276 | +0.0003 | 0.00 |

Plateau neighbours (all-in 20% uplift; selected +0.106):
- {'sp': '6A-6C', 'sig': 'mr1.12', 'N': '5'}: -0.080 (trades 112)
- {'sp': '6A-6C', 'sig': 'mr1.88', 'N': '5'}: +0.167 (trades 65)
- {'sp': '6A-6C', 'sig': 'mr1.5', 'N': '4'}: +0.079 (trades 106)
- {'sp': '6A-6C', 'sig': 'mr1.5', 'N': '6'}: +0.146 (trades 85)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.25, p95 0.54, real 0.70. Standalone Sharpe at 2x slippage 0.33.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 26 | -9 | -0.90 |
| 2014 | 28 | -0 | -0.03 |
| 2015 | 29 | 1 | 0.08 |
| 2016 | 24 | -6 | -0.67 |
| 2017 | 28 | -3 | -0.36 |
| 2018 | 30 | -6 | -0.76 |
| 2019 | 26 | 14 | 2.26 |
| 2020 | 28 | 5 | 0.82 |
| 2021 | 29 | 4 | 0.69 |
| 2022 | 28 | -1 | -0.11 |
| 2023 | 27 | 1 | 0.15 |
| 2024 | 29 | 4 | 1.13 |
| 2025 | 29 | 4 | 0.64 |
| 2026 | 26 | 4 | 0.94 |


DONE L7