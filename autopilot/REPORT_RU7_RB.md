# REPORT RU7_RB
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=0.0; additive @20% clean/H1/H2 +0.00/-0.31/-0.00; standalone all-in weekly Sharpe -0.08 (2013-26 0.09, dev 2013-22 0.19); pair-window trades 1973. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| RB    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 | 1300 |    0.098 |   5.923 |      2 | True       |
| RB    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 0.000 |  724 |   -0.088 |  -3.442 |      2 | True       |
| RB    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 0.000 | 1359 |   -0.444 | -27.944 |      1 | True       |
| RB    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 0.000 | 2911 |   -0.549 | -43.969 |      1 | True       |
| RB    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 0.000 |  748 |   -0.561 | -25.224 |      0 | True       |
| RB    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1643 |   -0.567 | -33.808 |      0 | True       |
| RB    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 0.000 | 1474 |   -0.658 | -41.982 |      1 | True       |
| RB    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 0.000 |  798 |   -0.861 | -34.004 |      0 | True       |
| RB    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.000 | 0.000 | 1538 |   -0.875 | -61.961 |      0 | True       |
| RB    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  824 |   -1.064 | -49.659 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.10; replicate best-eligible median 0.33, p95 0.59; real beats 30% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.507e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.008 | -0.146 | +0.007 | -0.012 | +5.1 | [-0.104, +0.082] | 0.62 | NO |
| 20% | add | +0.001 | -0.310 | -0.003 | -0.041 | +16.6 | [-0.223, +0.142] | 0.62 | NO |
| 30% | add | -0.019 | -0.483 | -0.029 | -0.085 | +28.0 | [-0.353, +0.185] | 0.62 | NO |
| 50% | add | -0.091 | -0.829 | -0.125 | -0.207 | +51.0 | [-0.626, +0.214] | 0.62 | NO |
| 10% | const | +0.008 | -0.164 | +0.007 | -0.015 | -4.3 | [-0.117, +0.089] | 0.62 | NO |
| 20% | const | -0.008 | -0.396 | -0.014 | -0.062 | -2.2 | [-0.288, +0.166] | 0.62 | NO |
| 30% | const | -0.062 | -0.707 | -0.085 | -0.160 | -0.1 | [-0.530, +0.211] | 0.62 | NO |
| 50% | const | -0.339 | -1.546 | -0.506 | -0.568 | +4.1 | [-1.266, +0.126] | 0.62 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 89,260, Sharpe 0.10, maxDD 598,061, worst wk -117,624; H1: net -165,829, Sharpe -0.74, maxDD 518,702, worst wk -96,185; H2: net -40,311, Sharpe -0.14, maxDD 305,887, worst wk -109,323; all: net -116,881, Sharpe -0.08, maxDD 747,752, worst wk -117,624
Correlation with pair (weekly): clean -0.03, H1 +0.19, H2 -0.14, all -0.03; worst-decile weeks (n=17) corr -0.14, sleeve mean in those weeks $-11,338, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.46 | 2.74 | 4.88 | -86,898 | -81,072 | 276,376 | -96,186 | 43.8 |
| clean | add 30% | 1.44 | 2.68 | 4.86 | -91,687 | -83,416 | 279,198 | -105,650 | 44.8 |
| clean | const 20% | 1.45 | 2.72 | 4.91 | -71,434 | -65,795 | 220,354 | -80,735 | 43.8 |
| clean | const 30% | 1.40 | 2.57 | 4.68 | -68,490 | -60,987 | 204,830 | -82,473 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.52 | 4.98 | 3.19 | -81,799 | -75,235 | 175,853 | -83,758 | 35.7 |
| H1 | add 30% | 2.34 | 4.48 | 2.90 | -83,894 | -79,838 | 187,923 | -86,493 | 35.7 |
| H1 | const 20% | 2.43 | 4.73 | 3.04 | -66,277 | -62,029 | 145,510 | -68,101 | 35.7 |
| H1 | const 30% | 2.12 | 3.92 | 2.57 | -60,936 | -60,029 | 142,409 | -63,007 | 39.3 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.29 | 4.62 | 3.27 | -87,090 | -83,045 | 235,232 | -88,223 | 37.8 |
| H2 | add 30% | 2.27 | 4.53 | 3.14 | -91,368 | -84,974 | 244,135 | -93,627 | 37.8 |
| H2 | const 20% | 2.28 | 4.58 | 3.21 | -71,383 | -67,208 | 191,747 | -72,740 | 37.8 |
| H2 | const 30% | 2.21 | 4.36 | 2.98 | -67,808 | -61,219 | 178,908 | -70,402 | 37.8 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.82 | 3.48 | 9.69 | -87,327 | -81,622 | 276,376 | -96,186 | 41.4 |
| all | add 30% | 1.77 | 3.36 | 9.55 | -91,850 | -84,088 | 279,198 | -105,650 | 42.0 |
| all | const 20% | 1.80 | 3.42 | 9.70 | -71,671 | -66,184 | 220,354 | -80,735 | 41.4 |
| all | const 30% | 1.70 | 3.16 | 9.06 | -68,438 | -61,953 | 204,830 | -82,473 | 42.0 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.001 / -0.310 / -0.003
- [PASS] 3 worst week within share: all-in worst week +16.6% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.08 vs p95 0.45 (rank 0.59)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.223, +0.142]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.063 / -0.390 / -0.028
- [PASS] 6 worst-decile corr <=+0.30: -0.14
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_RB); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1973 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6669 | +0.0433 | 0.98 |
| fixed | 6669 | +0.0084 | 0.19 |
| scaled | 6669 | +0.0084 | 0.19 |

Plateau neighbours (all-in 20% uplift; selected -0.041):
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '0.0'}: +0.056 (trades 4521)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '0.0'}: -0.082 (trades 2041)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.0', 'L': '15'}: -0.057 (trades 1972)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '0.0'}: -0.089 (trades 774)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '0.0'}: -0.044 (trades 1918)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.0', 'L': '25'}: -0.021 (trades 1972)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.21, p95 0.45, real -0.08. Standalone Sharpe at 2x slippage -0.38.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 670 | 26 | 0.94 |
| 2014 | 636 | 2 | 0.08 |
| 2015 | 637 | 107 | 2.99 |
| 2016 | 711 | 52 | 1.67 |
| 2017 | 729 | -50 | -1.73 |
| 2018 | 689 | -75 | -2.94 |
| 2019 | 709 | -8 | -0.24 |
| 2020 | 647 | -40 | -1.72 |
| 2021 | 618 | 40 | 1.51 |
| 2022 | 623 | 2 | 0.06 |
| 2023 | 654 | 10 | 0.31 |
| 2024 | 684 | -18 | -0.63 |
| 2025 | 597 | -19 | -0.66 |
| 2026 | 421 | 9 | 0.41 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.10 | +0.00/-0.31/-0.00 |
| 2 tick entry / 2 tick exit | -0.64 | -0.14/-0.46/-0.05 |
| 3 tick entry / 3 tick exit | -1.39 | -0.29/-0.62/-0.10 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -1.06 | -0.21/+0.05/-0.35 |

DONE RU7_RB