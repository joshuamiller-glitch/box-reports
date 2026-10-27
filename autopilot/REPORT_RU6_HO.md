# REPORT RU6_HO
**Verdict: NO** (3/7 measured gates pass). Selected cell nb=1, conf=0, sess=NRTH, ent=stop, k=2.0, tf=15, S=1.0, R=2.0; additive @20% clean/H1/H2 +0.21/-0.01/+0.16; standalone all-in weekly Sharpe 1.26 (2013-26 0.01, dev 2013-22 -0.40); pair-window trades 1688. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU6 session split of the RU2 selected cell (ALL / RTH / non-RTH by placement time). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 40 clean trades): 3. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| HO    |    1 |      0 | NRTH   | stop  | 2.000 |   15 | 1.000 | 2.000 | 1087 |    1.513 | 119.787 |      3 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | 1430 |    1.149 | 100.374 |      3 | True       |
| HO    |    1 |      0 | RTH    | stop  | 2.000 |   15 | 1.000 | 2.000 |  354 |   -0.806 | -27.730 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.51; replicate best-eligible median 0.06, p95 0.67; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.151e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.114 | +0.007 | +0.086 | +0.088 | +4.6 | [+0.006, +0.175] | 0.09 | NO |
| 20% | add | +0.209 | -0.006 | +0.159 | +0.158 | +15.8 | [-0.004, +0.329] | 0.09 | NO |
| 30% | add | +0.285 | -0.037 | +0.218 | +0.210 | +27.1 | [-0.026, +0.460] | 0.09 | NO |
| 50% | add | +0.389 | -0.144 | +0.292 | +0.267 | +49.6 | [-0.106, +0.659] | 0.09 | NO |
| 10% | const | +0.126 | +0.006 | +0.095 | +0.097 | -4.8 | [+0.005, +0.193] | 0.09 | NO |
| 20% | const | +0.249 | -0.020 | +0.190 | +0.186 | -2.8 | [-0.015, +0.397] | 0.09 | NO |
| 30% | const | +0.358 | -0.100 | +0.272 | +0.253 | -0.9 | [-0.074, +0.597] | 0.09 | NO |
| 50% | const | +0.469 | -0.535 | +0.278 | +0.244 | +2.9 | [-0.376, +0.897] | 0.09 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,378,300, Sharpe 1.51, maxDD 402,313, worst wk -142,547; H1: net 38,398, Sharpe 0.22, maxDD 275,335, worst wk -102,577; H2: net 275,954, Sharpe 1.09, maxDD 241,169, worst wk -127,566; all: net 1,692,652, Sharpe 1.26, maxDD 402,313, worst wk -142,547
Correlation with pair (weekly): clean +0.19, H1 +0.01, H2 -0.06, all +0.11; worst-decile weeks (n=17) corr -0.29, sleeve mean in those weeks $10,249, positive share 0.71.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.67 | 3.22 | 5.09 | -86,004 | -80,311 | 315,691 | -95,587 | 41.9 |
| clean | add 30% | 1.75 | 3.38 | 5.23 | -90,758 | -82,926 | 333,481 | -104,876 | 42.9 |
| clean | const 20% | 1.71 | 3.30 | 5.16 | -70,534 | -65,002 | 259,669 | -80,185 | 42.9 |
| clean | const 30% | 1.82 | 3.52 | 5.39 | -69,344 | -62,447 | 249,448 | -81,773 | 41.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.82 | 5.90 | 3.43 | -76,226 | -71,612 | 175,356 | -79,712 | 35.7 |
| H1 | add 30% | 2.79 | 5.72 | 3.23 | -76,534 | -74,570 | 187,178 | -80,425 | 35.7 |
| H1 | const 20% | 2.81 | 5.82 | 3.33 | -60,704 | -58,473 | 145,013 | -64,055 | 35.7 |
| H1 | const 30% | 2.73 | 5.45 | 3.02 | -58,510 | -54,861 | 141,664 | -60,082 | 32.1 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.46 | 5.33 | 4.02 | -77,314 | -69,008 | 207,297 | -79,272 | 43.2 |
| H2 | add 30% | 2.52 | 5.63 | 4.26 | -75,427 | -64,048 | 202,234 | -77,645 | 43.2 |
| H2 | const 20% | 2.49 | 5.49 | 4.14 | -61,096 | -53,171 | 163,812 | -62,767 | 43.2 |
| H2 | const 30% | 2.57 | 5.96 | 4.58 | -51,100 | -44,156 | 137,006 | -52,888 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 2.02 | 4.01 | 9.63 | -83,439 | -78,281 | 315,691 | -95,587 | 41.4 |
| all | add 30% | 2.07 | 4.13 | 9.63 | -86,452 | -79,838 | 333,481 | -104,876 | 42.0 |
| all | const 20% | 2.04 | 4.08 | 9.63 | -67,837 | -63,011 | 259,669 | -80,185 | 42.0 |
| all | const 30% | 2.11 | 4.22 | 9.62 | -65,871 | -58,994 | 249,448 | -81,773 | 40.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.209 / -0.006 / +0.159
- [PASS] 3 worst week within share: all-in worst week +15.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.26 vs p95 0.51 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.004, +0.329]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.174 / -0.046 / +0.147
- [PASS] 6 worst-decile corr <=+0.30: -0.29
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU6_HO); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1688 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 5047 | +0.0177 | 0.26 |
| fixed | 5047 | -0.0272 | -0.40 |
| scaled | 5047 | -0.0272 | -0.40 |

Plateau neighbours (all-in 20% uplift; selected +0.158):
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'NRTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '2.0'}: -0.119 (trades 3696)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'NRTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '0.75', 'R': '2.0'}: +0.044 (trades 1720)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'NRTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '1.5'}: +0.103 (trades 1722)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'NRTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.0', 'L': '15'}: +0.177 (trades 1685)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'NRTH', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.0', 'R': '2.0'}: +0.038 (trades 633)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'NRTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.25', 'R': '2.0'}: +0.186 (trades 1623)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'NRTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.5'}: +0.193 (trades 1643)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'NRTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.0', 'L': '25'}: +0.155 (trades 1685)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.15, p95 0.51, real 1.26. Standalone Sharpe at 2x slippage 1.08.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 523 | -21 | -0.56 |
| 2014 | 432 | -33 | -1.00 |
| 2015 | 509 | 23 | 0.71 |
| 2016 | 510 | -23 | -0.80 |
| 2017 | 518 | -12 | -0.33 |
| 2018 | 478 | -66 | -2.40 |
| 2019 | 555 | -82 | -2.45 |
| 2020 | 477 | 2 | 0.05 |
| 2021 | 493 | 29 | 0.98 |
| 2022 | 552 | 47 | 1.09 |
| 2023 | 582 | -3 | -0.07 |
| 2024 | 533 | 65 | 1.67 |
| 2025 | 516 | 45 | 1.31 |
| 2026 | 391 | 35 | 1.42 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.51 | +0.21/-0.01/+0.16 |
| 2 tick entry / 2 tick exit | 1.00 | +0.12/-0.09/+0.12 |
| 3 tick entry / 3 tick exit | 0.58 | +0.04/-0.24/+0.11 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.89 | -0.17/-0.66/-0.08 |

DONE RU6_HO