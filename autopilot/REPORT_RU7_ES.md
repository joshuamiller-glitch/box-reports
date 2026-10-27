# REPORT RU7_ES
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=mkt, k=2.0, tf=30, S=1.5, R=0.0; additive @20% clean/H1/H2 -0.29/-0.71/-0.37; standalone all-in weekly Sharpe -1.37 (2013-26 -0.80, dev 2013-22 -0.82); pair-window trades 1199. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|---------:|-------:|:-----------|
| ES    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 0.000 |  777 |   -1.078 |  -41.495 |      0 | True       |
| ES    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  798 |   -1.132 |  -41.506 |      0 | True       |
| ES    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1496 |   -1.301 |  -68.074 |      0 | True       |
| ES    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 0.000 |  690 |   -1.413 |  -52.243 |      0 | True       |
| ES    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 0.000 | 1696 |   -1.450 |  -82.321 |      0 | True       |
| ES    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 0.000 | 1801 |   -1.562 |  -88.415 |      0 | True       |
| ES    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 0.000 | 1227 |   -1.659 |  -69.614 |      0 | True       |
| ES    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 | 1103 |   -1.713 |  -76.893 |      0 | True       |
| ES    |    1 |      0 | ALL    | mkt   | 1.500 |   15 | 1.500 | 0.000 | 2763 |   -1.945 | -140.212 |      0 | True       |
| ES    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.000 | 0.000 | 1586 |   -2.012 | -103.679 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -1.08; replicate best-eligible median -1.12, p95 -0.26; real beats 60% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.367e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.141 | -0.346 | -0.185 | -0.183 | +8.9 | [-0.275, -0.095] | 0.01 | NO |
| 20% | add | -0.285 | -0.711 | -0.374 | -0.369 | +17.8 | [-0.551, -0.200] | 0.01 | NO |
| 30% | add | -0.428 | -1.079 | -0.560 | -0.554 | +26.6 | [-0.817, -0.307] | 0.01 | NO |
| 50% | add | -0.697 | -1.777 | -0.906 | -0.902 | +47.6 | [-1.308, -0.527] | 0.01 | NO |
| 10% | const | -0.157 | -0.386 | -0.206 | -0.203 | -1.1 | [-0.306, -0.106] | 0.01 | NO |
| 20% | const | -0.357 | -0.895 | -0.467 | -0.462 | -2.2 | [-0.685, -0.254] | 0.01 | NO |
| 30% | const | -0.604 | -1.537 | -0.787 | -0.782 | -2.1 | [-1.143, -0.453] | 0.01 | NO |
| 50% | const | -1.214 | -3.072 | -1.573 | -1.566 | +14.8 | [-2.223, -0.954] | 0.01 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -982,095, Sharpe -1.08, maxDD 1,038,632, worst wk -148,051; H1: net -672,580, Sharpe -2.83, maxDD 919,138, worst wk -159,685; H2: net -380,586, Sharpe -1.11, maxDD 748,538, worst wk -97,924; all: net -2,035,261, Sharpe -1.37, maxDD 2,197,980, worst wk -159,685
Correlation with pair (weekly): clean +0.21, H1 +0.04, H2 +0.30, all +0.20; worst-decile weeks (n=17) corr +0.22, sleeve mean in those weeks $-33,732, positive share 0.18.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.17 | 2.16 | 3.38 | -91,657 | -86,729 | 335,393 | -95,253 | 45.7 |
| clean | add 30% | 1.03 | 1.86 | 2.85 | -98,460 | -92,985 | 363,034 | -104,100 | 46.7 |
| clean | const 20% | 1.10 | 2.01 | 3.11 | -76,047 | -71,647 | 279,371 | -79,741 | 46.7 |
| clean | const 30% | 0.86 | 1.50 | 2.24 | -75,688 | -71,560 | 283,968 | -80,833 | 47.6 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.12 | 4.16 | 2.26 | -83,635 | -75,544 | 202,794 | -89,737 | 50.0 |
| H1 | add 30% | 1.75 | 3.26 | 1.72 | -86,648 | -80,467 | 228,335 | -95,461 | 46.4 |
| H1 | const 20% | 1.93 | 3.70 | 1.97 | -68,113 | -62,404 | 172,452 | -74,079 | 46.4 |
| H1 | const 30% | 1.29 | 2.26 | 1.09 | -63,760 | -60,758 | 195,444 | -71,975 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 1.92 | 3.71 | 3.06 | -95,567 | -90,201 | 229,215 | -97,179 | 40.5 |
| H2 | add 30% | 1.74 | 3.30 | 2.78 | -103,433 | -95,710 | 239,059 | -104,506 | 40.5 |
| H2 | const 20% | 1.83 | 3.50 | 2.92 | -79,600 | -74,364 | 187,310 | -80,674 | 40.5 |
| H2 | const 30% | 1.51 | 2.83 | 2.34 | -79,482 | -71,954 | 183,798 | -79,748 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.49 | 2.78 | 6.84 | -92,630 | -87,182 | 335,393 | -97,179 | 45.6 |
| all | add 30% | 1.30 | 2.38 | 5.76 | -99,600 | -92,881 | 363,034 | -104,506 | 45.6 |
| all | const 20% | 1.40 | 2.58 | 6.28 | -76,892 | -71,871 | 279,371 | -80,674 | 45.6 |
| all | const 30% | 1.08 | 1.91 | 4.51 | -76,191 | -70,819 | 283,968 | -80,833 | 46.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.285 / -0.711 / -0.374
- [PASS] 3 worst week within share: all-in worst week +17.8% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -1.37 vs p95 -0.30 (rank 0.30)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.551, -0.200]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.366 / -0.786 / -0.418
- [PASS] 6 worst-decile corr <=+0.30: +0.22
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_ES); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1199 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2839 | -0.0071 | -0.13 |
| fixed | 2839 | -0.0438 | -0.82 |
| scaled | 2839 | -0.0438 | -0.82 |

Plateau neighbours (all-in 20% uplift; selected -0.369):
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.5', 'R': '0.0'}: -0.635 (trades 2592)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.125', 'R': '0.0'}: -0.406 (trades 1228)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.5', 'R': '0.0'}: -0.091 (trades 593)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.875', 'R': '0.0'}: -0.222 (trades 1157)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.14, p95 -0.30, real -1.37. Standalone Sharpe at 2x slippage -1.74.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 197 | -20 | -1.76 |
| 2014 | 257 | -39 | -3.12 |
| 2015 | 292 | -16 | -1.04 |
| 2016 | 269 | -28 | -2.01 |
| 2017 | 190 | -14 | -1.52 |
| 2018 | 309 | -4 | -0.25 |
| 2019 | 302 | -13 | -0.86 |
| 2020 | 281 | 9 | 0.66 |
| 2021 | 342 | -7 | -0.38 |
| 2022 | 400 | 8 | 0.39 |
| 2023 | 365 | 15 | 0.74 |
| 2024 | 385 | -3 | -0.13 |
| 2025 | 373 | -51 | -2.94 |
| 2026 | 278 | -19 | -1.17 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -1.08 | -0.29/-0.71/-0.37 |
| 2 tick entry / 2 tick exit | -1.88 | -0.44/-0.85/-0.45 |
| 3 tick entry / 3 tick exit | -2.72 | -0.60/-0.99/-0.53 |
| retrace-limit DISP (b=2.0, tf30, f=0.5, RZ geometry) | 0.23 | -0.00/-0.27/+0.02 |

DONE RU7_ES