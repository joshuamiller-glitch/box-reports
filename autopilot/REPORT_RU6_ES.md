# REPORT RU6_ES
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=RTH, ent=stop, k=1.5, tf=15, S=1.5, R=2.0; additive @20% clean/H1/H2 +0.21/-0.53/-0.25; standalone all-in weekly Sharpe 0.42 (2013-26 -0.20, dev 2013-22 -0.40); pair-window trades 1756. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU6 session split of the RU2 selected cell (ALL / RTH / non-RTH by placement time). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 40 clean trades): 3. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| ES    |    1 |      0 | RTH    | stop  | 1.500 |   15 | 1.500 | 2.000 | 1097 |    1.192 |  67.905 |      3 | True       |
| ES    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 2086 |    0.224 |  18.431 |      2 | True       |
| ES    |    1 |      0 | NRTH   | stop  | 1.500 |   15 | 1.500 | 2.000 | 1133 |   -0.763 | -47.962 |      2 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.19; replicate best-eligible median -0.52, p95 -0.00; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.6e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.114 | -0.262 | -0.121 | +0.015 | +10.1 | [-0.083, +0.116] | 0.12 | NO |
| 20% | add | +0.210 | -0.530 | -0.250 | +0.011 | +26.3 | [-0.180, +0.206] | 0.12 | NO |
| 30% | add | +0.288 | -0.789 | -0.384 | -0.010 | +42.4 | [-0.286, +0.274] | 0.12 | NO |
| 50% | add | +0.390 | -1.245 | -0.647 | -0.089 | +74.7 | [-0.514, +0.346] | 0.12 | NO |
| 10% | const | +0.125 | -0.292 | -0.135 | +0.016 | +0.7 | [-0.093, +0.127] | 0.12 | NO |
| 20% | const | +0.251 | -0.662 | -0.317 | +0.002 | +7.5 | [-0.232, +0.243] | 0.12 | NO |
| 30% | const | +0.361 | -1.093 | -0.555 | -0.057 | +14.2 | [-0.433, +0.326] | 0.12 | NO |
| 50% | const | +0.429 | -2.016 | -1.189 | -0.351 | +27.7 | [-1.023, +0.341] | 0.12 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,086,201, Sharpe 1.19, maxDD 425,350, worst wk -148,150; H1: net -254,437, Sharpe -0.85, maxDD 558,677, worst wk -154,755; H2: net -182,246, Sharpe -0.54, maxDD 491,879, worst wk -131,871; all: net 649,518, Sharpe 0.42, maxDD 700,075, worst wk -154,755
Correlation with pair (weekly): clean -0.01, H1 +0.32, H2 +0.26, all +0.09; worst-decile weeks (n=17) corr +0.20, sleeve mean in those weeks $-13,544, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.67 | 3.27 | 6.29 | -89,137 | -81,047 | 245,810 | -104,204 | 41.0 |
| clean | add 30% | 1.75 | 3.45 | 6.22 | -94,406 | -82,578 | 266,371 | -117,528 | 41.0 |
| clean | const 20% | 1.71 | 3.37 | 6.42 | -73,417 | -65,450 | 199,411 | -88,693 | 42.9 |
| clean | const 30% | 1.82 | 3.60 | 5.79 | -70,826 | -59,991 | 217,253 | -94,260 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.30 | 4.38 | 3.21 | -95,855 | -87,677 | 169,370 | -100,189 | 39.3 |
| H1 | add 30% | 2.04 | 3.69 | 2.90 | -104,978 | -98,667 | 178,199 | -111,140 | 39.3 |
| H1 | const 20% | 2.17 | 4.02 | 3.05 | -80,333 | -74,537 | 139,028 | -84,532 | 39.3 |
| H1 | const 30% | 1.73 | 2.97 | 2.10 | -81,695 | -78,958 | 161,680 | -87,654 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.05 | 4.08 | 3.16 | -88,153 | -82,592 | 235,012 | -92,327 | 43.2 |
| H2 | add 30% | 1.91 | 3.78 | 2.94 | -92,311 | -86,935 | 245,787 | -97,228 | 43.2 |
| H2 | const 20% | 1.98 | 3.93 | 3.06 | -72,186 | -67,811 | 191,795 | -75,822 | 43.2 |
| H2 | const 30% | 1.74 | 3.39 | 2.64 | -71,295 | -65,533 | 185,489 | -72,471 | 48.6 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.87 | 3.64 | 11.52 | -91,504 | -83,394 | 245,810 | -104,204 | 41.4 |
| all | add 30% | 1.85 | 3.57 | 10.88 | -98,273 | -87,652 | 266,371 | -117,528 | 41.4 |
| all | const 20% | 1.86 | 3.61 | 11.49 | -75,762 | -68,418 | 199,411 | -88,693 | 42.6 |
| all | const 30% | 1.80 | 3.43 | 9.60 | -76,538 | -66,445 | 217,253 | -94,260 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.210 / -0.530 / -0.250
- [FAIL] 3 worst week within share: all-in worst week +26.3% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.42 vs p95 0.01 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.180, +0.206]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 38% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.146 / -0.601 / -0.290
- [PASS] 6 worst-decile corr <=+0.30: +0.20
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU6_ES); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1756 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 3567 | +0.0082 | 0.14 |
| fixed | 3567 | -0.0246 | -0.40 |
| scaled | 3567 | -0.0246 | -0.40 |

Plateau neighbours (all-in 20% uplift; selected +0.011):
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.125', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.073 (trades 2347)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.125', 'R': '2.0'}: -0.241 (trades 1947)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.5'}: -0.127 (trades 1890)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '15'}: +0.013 (trades 1756)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.875', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.069 (trades 1120)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.875', 'R': '2.0'}: -0.032 (trades 1582)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.5'}: +0.049 (trades 1671)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '25'}: +0.009 (trades 1753)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.74, p95 0.01, real 0.42. Standalone Sharpe at 2x slippage 0.13.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 190 | -31 | -2.63 |
| 2014 | 254 | -4 | -0.24 |
| 2015 | 350 | -45 | -2.12 |
| 2016 | 314 | -9 | -0.53 |
| 2017 | 173 | -25 | -2.45 |
| 2018 | 462 | 5 | 0.20 |
| 2019 | 368 | -26 | -1.12 |
| 2020 | 455 | -6 | -0.23 |
| 2021 | 462 | 31 | 1.22 |
| 2022 | 539 | 23 | 0.80 |
| 2023 | 532 | 14 | 0.53 |
| 2024 | 571 | 21 | 0.66 |
| 2025 | 548 | 2 | 0.07 |
| 2026 | 410 | -17 | -0.65 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.19 | +0.21/-0.53/-0.25 |
| 2 tick entry / 2 tick exit | 0.24 | +0.02/-0.69/-0.33 |
| 3 tick entry / 3 tick exit | -0.93 | -0.22/-0.90/-0.41 |
| retrace-limit DISP (b=1.5, tf15, f=0.5, RZ geometry) | -0.34 | -0.09/-0.06/-0.01 |

DONE RU6_ES