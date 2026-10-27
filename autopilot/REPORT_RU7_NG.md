# REPORT RU7_NG
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.0, R=0.0; additive @20% clean/H1/H2 +0.01/-0.09/-0.45; standalone all-in weekly Sharpe -0.36 (2013-26 -1.26, dev 2013-22 -1.63); pair-window trades 1629. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 0.000 | 1011 |    0.191 |   8.538 |      2 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  828 |    0.127 |   5.331 |      2 | True       |
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 | 1008 |   -0.078 |  -3.376 |      1 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 0.000 |  820 |   -0.168 |  -6.754 |      2 | True       |
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 0.000 |  751 |   -0.250 | -10.096 |      2 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 0.000 | 1593 |   -0.359 | -22.751 |      2 | True       |
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 0.000 |  743 |   -0.445 | -17.653 |      1 | True       |
| NG    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1404 |   -0.449 | -26.294 |      1 | True       |
| NG    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.000 | 0.000 | 1432 |   -0.467 | -28.317 |      2 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.000 | 0.000 | 1135 |   -0.567 | -27.957 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.19; replicate best-eligible median -0.00, p95 0.53; real beats 65% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.033e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.012 | -0.005 | -0.227 | -0.051 | +10.4 | [-0.162, +0.058] | 0.43 | NO |
| 20% | add | +0.009 | -0.094 | -0.449 | -0.121 | +20.9 | [-0.338, +0.092] | 0.43 | NO |
| 30% | add | -0.006 | -0.263 | -0.663 | -0.205 | +31.3 | [-0.519, +0.104] | 0.43 | NO |
| 50% | add | -0.068 | -0.735 | -1.056 | -0.399 | +54.5 | [-0.870, +0.070] | 0.43 | NO |
| 10% | const | +0.012 | -0.011 | -0.252 | -0.058 | +0.4 | [-0.181, +0.063] | 0.43 | NO |
| 20% | const | +0.003 | -0.170 | -0.558 | -0.161 | +0.9 | [-0.426, +0.100] | 0.43 | NO |
| 30% | const | -0.042 | -0.557 | -0.921 | -0.328 | +2.1 | [-0.750, +0.090] | 0.43 | NO |
| 50% | const | -0.292 | -1.760 | -1.811 | -0.864 | +7.4 | [-1.610, -0.133] | 0.43 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 173,550, Sharpe 0.19, maxDD 608,167, worst wk -116,109; H1: net -213,829, Sharpe -0.61, maxDD 527,441, worst wk -143,716; H2: net -523,333, Sharpe -1.78, maxDD 758,362, worst wk -86,765; all: net -563,613, Sharpe -0.36, maxDD 1,291,416, worst wk -143,716
Correlation with pair (weekly): clean -0.00, H1 -0.28, H2 +0.37, all +0.01; worst-decile weeks (n=17) corr -0.04, sleeve mean in those weeks $-16,806, positive share 0.29.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.47 | 2.83 | 5.55 | -90,246 | -83,778 | 245,732 | -97,629 | 46.7 |
| clean | add 30% | 1.45 | 2.76 | 6.05 | -96,408 | -87,058 | 228,543 | -107,585 | 46.7 |
| clean | const 20% | 1.46 | 2.80 | 5.79 | -74,662 | -68,269 | 189,710 | -82,086 | 46.7 |
| clean | const 30% | 1.42 | 2.64 | 5.53 | -73,030 | -64,719 | 177,660 | -84,269 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.73 | 5.79 | 3.78 | -69,516 | -64,530 | 145,667 | -69,722 | 39.3 |
| H1 | add 30% | 2.56 | 5.03 | 3.33 | -75,729 | -72,300 | 158,883 | -82,529 | 35.7 |
| H1 | const 20% | 2.66 | 5.43 | 3.68 | -57,400 | -54,732 | 117,605 | -60,736 | 32.1 |
| H1 | const 30% | 2.27 | 4.06 | 2.56 | -65,427 | -57,602 | 137,441 | -69,668 | 32.1 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 1.85 | 3.53 | 2.80 | -94,308 | -89,243 | 240,831 | -99,766 | 43.2 |
| H2 | add 30% | 1.63 | 3.06 | 2.46 | -101,544 | -94,272 | 252,534 | -108,387 | 45.9 |
| H2 | const 20% | 1.74 | 3.29 | 2.62 | -78,341 | -73,406 | 197,346 | -83,261 | 43.2 |
| H2 | const 30% | 1.38 | 2.52 | 2.07 | -77,594 | -70,516 | 187,307 | -83,630 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.74 | 3.35 | 10.54 | -90,634 | -83,586 | 245,732 | -99,766 | 45.0 |
| all | add 30% | 1.65 | 3.12 | 10.03 | -96,672 | -88,114 | 252,534 | -108,387 | 44.4 |
| all | const 20% | 1.70 | 3.24 | 10.38 | -74,922 | -68,598 | 197,346 | -83,261 | 43.8 |
| all | const 30% | 1.53 | 2.81 | 9.20 | -73,974 | -66,559 | 187,307 | -84,269 | 41.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.009 / -0.094 / -0.449
- [FAIL] 3 worst week within share: all-in worst week +20.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real -0.36 vs p95 -0.43 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.338, +0.092]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.137 / -0.299 / -0.563
- [PASS] 6 worst-decile corr <=+0.30: -0.04
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_NG); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1629 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 3416 | -0.0328 | -0.69 |
| fixed | 3416 | -0.0783 | -1.63 |
| scaled | 3416 | -0.0783 | -1.63 |

Plateau neighbours (all-in 20% uplift; selected -0.121):
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '0.0'}: -0.483 (trades 3056)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '0.75', 'R': '0.0'}: -0.107 (trades 1629)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '0.0', 'L': '15'}: -0.123 (trades 1628)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.0', 'R': '0.0'}: -0.035 (trades 733)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.25', 'R': '0.0'}: -0.150 (trades 1626)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '0.0', 'L': '25'}: -0.119 (trades 1633)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.16, p95 -0.43, real -0.36. Standalone Sharpe at 2x slippage -1.05.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 311 | -19 | -1.30 |
| 2014 | 424 | -34 | -1.69 |
| 2015 | 295 | -6 | -0.55 |
| 2016 | 323 | -58 | -3.75 |
| 2017 | 239 | 0 | 0.03 |
| 2018 | 237 | -17 | -1.42 |
| 2019 | 228 | -34 | -3.68 |
| 2020 | 367 | -27 | -1.55 |
| 2021 | 438 | -18 | -1.03 |
| 2022 | 554 | -54 | -2.14 |
| 2023 | 476 | -11 | -0.57 |
| 2024 | 456 | -14 | -0.74 |
| 2025 | 604 | -5 | -0.18 |
| 2026 | 361 | -25 | -1.23 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.19 | +0.01/-0.09/-0.45 |
| 2 tick entry / 2 tick exit | -1.35 | -0.29/-0.50/-0.67 |
| 3 tick entry / 3 tick exit | -2.88 | -0.58/-0.90/-0.86 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | 0.04 | +0.04/-0.49/-0.02 |

DONE RU7_NG