# REPORT RU10_HOxCL
**Verdict: NO** (3/7 measured gates pass). Selected cell nb=1, conf=1, sess=ALL, ent=stop, k=2.0, tf=15, S=1.0, R=2.0, partner=CL; additive @20% clean/H1/H2 +0.09/-0.12/+0.19; standalone all-in weekly Sharpe 0.77 (2013-26 0.08, dev 2013-22 -0.14); pair-window trades 2060. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU10 displacement continuation confirmed by a same-direction displacement (range >= 1 ATR) in the partner market. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R | partner   |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|:----------|-----:|---------:|---------:|-------:|:-----------|
| HO    |    1 |      1 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | CL        | 1362 |    0.867 |   73.587 |      2 | True       |
| HO    |    1 |      1 | ALL    | stop  | 2.000 |   30 | 1.000 | 2.000 | CL        |  753 |    0.541 |   30.007 |      2 | True       |
| HO    |    1 |      1 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | CL        | 2936 |    0.095 |   10.393 |      1 | True       |
| HO    |    1 |      1 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 | CL        |  842 |    0.077 |    4.580 |      1 | True       |
| HO    |    1 |      1 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | CL        | 1683 |   -0.453 |  -36.870 |      0 | True       |
| HO    |    1 |      1 | ALL    | mkt   | 2.000 |   15 | 1.000 | 2.000 | CL        | 1522 |   -0.681 |  -63.139 |      1 | True       |
| HO    |    1 |      1 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | CL        | 1931 |   -1.058 |  -99.787 |      1 | True       |
| HO    |    1 |      1 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | CL        | 3457 |   -2.047 | -241.557 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.87; replicate best-eligible median 0.51, p95 1.02; real beats 75% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.074e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.052 | -0.051 | +0.102 | +0.044 | +3.9 | [-0.039, +0.130] | 0.08 | NO |
| 20% | add | +0.089 | -0.116 | +0.191 | +0.072 | +14.5 | [-0.091, +0.238] | 0.08 | NO |
| 30% | add | +0.111 | -0.192 | +0.266 | +0.085 | +25.1 | [-0.153, +0.329] | 0.08 | NO |
| 50% | add | +0.123 | -0.366 | +0.369 | +0.073 | +46.3 | [-0.297, +0.456] | 0.08 | NO |
| 10% | const | +0.057 | -0.058 | +0.112 | +0.048 | -5.4 | [-0.044, +0.143] | 0.08 | NO |
| 20% | const | +0.102 | -0.153 | +0.230 | +0.080 | -4.2 | [-0.121, +0.285] | 0.08 | NO |
| 30% | const | +0.123 | -0.301 | +0.339 | +0.082 | -2.9 | [-0.243, +0.419] | 0.08 | NO |
| 50% | const | +0.054 | -0.832 | +0.386 | -0.065 | +9.5 | [-0.675, +0.578] | 0.08 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 790,044, Sharpe 0.87, maxDD 552,960, worst wk -139,179; H1: net -34,193, Sharpe -0.21, maxDD 333,480, worst wk -95,247; H2: net 272,141, Sharpe 1.06, maxDD 248,580, worst wk -140,975; all: net 1,027,992, Sharpe 0.77, maxDD 552,960, worst wk -140,975
Correlation with pair (weekly): clean +0.18, H1 +0.13, H2 -0.16, all +0.11; worst-decile weeks (n=17) corr -0.43, sleeve mean in those weeks $930, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.55 | 2.98 | 4.62 | -85,757 | -81,103 | 322,114 | -94,493 | 44.8 |
| clean | add 30% | 1.57 | 3.03 | 4.57 | -90,857 | -84,769 | 343,117 | -103,236 | 45.7 |
| clean | const 20% | 1.56 | 3.01 | 4.59 | -70,299 | -66,087 | 266,093 | -79,092 | 44.8 |
| clean | const 30% | 1.58 | 3.05 | 4.51 | -70,736 | -63,228 | 259,084 | -80,133 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.71 | 5.60 | 3.38 | -78,763 | -72,815 | 173,434 | -86,241 | 35.7 |
| H1 | add 30% | 2.64 | 5.31 | 3.17 | -80,331 | -76,375 | 184,294 | -90,219 | 35.7 |
| H1 | const 20% | 2.67 | 5.46 | 3.27 | -63,241 | -59,676 | 143,091 | -70,584 | 35.7 |
| H1 | const 30% | 2.53 | 4.93 | 2.92 | -62,308 | -56,666 | 138,780 | -66,732 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.49 | 5.30 | 3.97 | -75,411 | -70,226 | 210,021 | -75,634 | 43.2 |
| H2 | add 30% | 2.56 | 5.56 | 4.17 | -72,572 | -65,747 | 206,319 | -73,624 | 43.2 |
| H2 | const 20% | 2.53 | 5.44 | 4.07 | -59,193 | -54,389 | 166,536 | -59,703 | 43.2 |
| H2 | const 30% | 2.64 | 5.83 | 4.44 | -48,947 | -46,145 | 141,092 | -49,728 | 43.2 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.93 | 3.82 | 9.03 | -84,007 | -79,031 | 322,114 | -94,493 | 43.2 |
| all | add 30% | 1.94 | 3.85 | 8.77 | -88,310 | -81,247 | 343,117 | -103,236 | 43.8 |
| all | const 20% | 1.94 | 3.84 | 8.90 | -68,514 | -64,065 | 266,093 | -79,092 | 43.2 |
| all | const 30% | 1.94 | 3.83 | 8.49 | -67,327 | -59,764 | 259,084 | -80,133 | 43.2 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.089 / -0.116 / +0.191
- [PASS] 3 worst week within share: all-in worst week +14.5% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.77 vs p95 0.47 (rank 0.99)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.091, +0.238]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.051 / -0.156 / +0.179
- [PASS] 6 worst-decile corr <=+0.30: -0.43
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU10_HOxCL); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2060 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6669 | +0.0327 | 0.56 |
| fixed | 6669 | -0.0079 | -0.14 |
| scaled | 6669 | -0.0079 | -0.14 |

Plateau neighbours (all-in 20% uplift; selected +0.072):
- {'sym': 'HO', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '2.0', 'partner': 'CL'}: -0.040 (trades 4517)
- {'sym': 'HO', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '0.75', 'R': '2.0', 'partner': 'CL'}: -0.027 (trades 2101)
- {'sym': 'HO', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '1.5', 'partner': 'CL'}: +0.038 (trades 2101)
- {'sym': 'HO', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.0', 'partner': 'CL', 'L': '15'}: +0.091 (trades 2055)
- {'sym': 'HO', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.0', 'R': '2.0', 'partner': 'CL'}: +0.042 (trades 789)
- {'sym': 'HO', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.25', 'R': '2.0', 'partner': 'CL'}: +0.074 (trades 1990)
- {'sym': 'HO', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.5', 'partner': 'CL'}: +0.094 (trades 2012)
- {'sym': 'HO', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.0', 'partner': 'CL', 'L': '25'}: +0.067 (trades 2056)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.31, p95 0.47, real 0.77. Standalone Sharpe at 2x slippage 0.58.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 635 | 4 | 0.08 |
| 2014 | 559 | 3 | 0.09 |
| 2015 | 660 | 42 | 1.05 |
| 2016 | 727 | -43 | -1.19 |
| 2017 | 695 | 23 | 0.62 |
| 2018 | 689 | -83 | -2.36 |
| 2019 | 711 | -62 | -1.66 |
| 2020 | 641 | -31 | -0.79 |
| 2021 | 676 | 50 | 1.41 |
| 2022 | 676 | 44 | 0.95 |
| 2023 | 718 | -4 | -0.09 |
| 2024 | 697 | 18 | 0.43 |
| 2025 | 629 | 49 | 1.42 |
| 2026 | 458 | 35 | 1.29 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.87 | +0.09/-0.12/+0.19 |
| 2 tick entry / 2 tick exit | 0.30 | -0.01/-0.18/+0.15 |
| 3 tick entry / 3 tick exit | -0.13 | -0.09/-0.33/+0.13 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.89 | -0.17/-0.66/-0.08 |

DONE RU10_HOxCL