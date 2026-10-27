# REPORT RU7_NQ
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=mkt, k=2.0, tf=15, S=1.0, R=0.0; additive @20% clean/H1/H2 +0.26/-0.22/-0.10; standalone all-in weekly Sharpe 0.89 (2013-26 -0.74, dev 2013-22 -1.41); pair-window trades 2082. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |    net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|-------:|-------:|:-----------|
| NQ    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.000 | 0.000 | 1361 |    1.551 | 83.912 |      2 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 0.000 | 1299 |    1.210 | 58.815 |      2 | True       |
| NQ    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 | 1179 |    1.102 | 49.409 |      2 | True       |
| NQ    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 0.000 | 1236 |    1.099 | 58.422 |      2 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 0.000 | 1617 |    0.761 | 35.354 |      1 | True       |
| NQ    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1455 |    0.722 | 32.898 |      2 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 0.000 | 1768 |    0.715 | 40.688 |      2 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  842 |    0.672 | 25.089 |      1 | True       |
| NQ    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 0.000 | 2663 |    0.587 | 41.862 |      2 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 0.000 |  804 |    0.385 | 14.062 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.55; replicate best-eligible median 0.64, p95 1.18; real beats 95% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.683e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.141 | -0.101 | -0.038 | +0.070 | +4.2 | [-0.021, +0.161] | 0.22 | NO |
| 20% | add | +0.264 | -0.218 | -0.097 | +0.120 | +8.5 | [-0.062, +0.300] | 0.22 | NO |
| 30% | add | +0.366 | -0.343 | -0.175 | +0.150 | +14.5 | [-0.117, +0.415] | 0.22 | NO |
| 50% | add | +0.511 | -0.597 | -0.366 | +0.160 | +28.7 | [-0.259, +0.586] | 0.22 | NO |
| 10% | const | +0.156 | -0.113 | -0.043 | +0.077 | -5.8 | [-0.025, +0.178] | 0.22 | NO |
| 20% | const | +0.317 | -0.280 | -0.134 | +0.137 | -11.2 | [-0.087, +0.361] | 0.22 | NO |
| 30% | const | +0.467 | -0.507 | -0.294 | +0.163 | -13.5 | [-0.207, +0.534] | 0.22 | NO |
| 50% | const | +0.631 | -1.133 | -0.877 | +0.032 | +0.8 | [-0.660, +0.735] | 0.22 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,412,628, Sharpe 1.55, maxDD 405,316, worst wk -138,456; H1: net 2,247, Sharpe 0.01, maxDD 470,347, worst wk -105,738; H2: net -101,313, Sharpe -0.30, maxDD 403,089, worst wk -163,953; all: net 1,313,561, Sharpe 0.89, maxDD 606,517, worst wk -163,953
Correlation with pair (weekly): clean +0.04, H1 +0.30, H2 -0.02, all +0.05; worst-decile weeks (n=17) corr +0.32, sleeve mean in those weeks $11,495, positive share 0.71.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.72 | 3.44 | 5.81 | -81,389 | -76,914 | 277,357 | -88,698 | 41.0 |
| clean | add 30% | 1.83 | 3.70 | 6.27 | -83,126 | -77,172 | 279,876 | -94,526 | 39.0 |
| clean | const 20% | 1.78 | 3.57 | 6.04 | -65,673 | -61,391 | 222,893 | -73,290 | 40.0 |
| clean | const 30% | 1.93 | 3.96 | 6.84 | -61,473 | -55,903 | 198,179 | -71,413 | 37.1 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.61 | 5.72 | 3.85 | -72,321 | -66,689 | 154,154 | -74,207 | 35.7 |
| H1 | add 30% | 2.48 | 5.45 | 3.83 | -69,676 | -67,019 | 155,375 | -72,167 | 42.9 |
| H1 | const 20% | 2.55 | 5.59 | 3.84 | -56,799 | -53,483 | 123,812 | -58,549 | 39.3 |
| H1 | const 30% | 2.32 | 5.07 | 3.74 | -48,762 | -48,566 | 111,279 | -48,843 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.20 | 4.47 | 3.56 | -82,584 | -76,435 | 213,015 | -89,498 | 43.2 |
| H2 | add 30% | 2.12 | 4.28 | 3.55 | -83,958 | -77,894 | 210,810 | -92,985 | 43.2 |
| H2 | const 20% | 2.16 | 4.38 | 3.55 | -66,617 | -61,732 | 169,530 | -72,993 | 43.2 |
| H2 | const 30% | 2.00 | 3.99 | 3.53 | -62,310 | -56,808 | 145,583 | -68,228 | 43.2 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.98 | 3.99 | 10.69 | -80,866 | -76,352 | 277,357 | -89,498 | 40.8 |
| all | add 30% | 2.01 | 4.09 | 11.06 | -82,166 | -76,460 | 279,876 | -94,526 | 40.8 |
| all | const 20% | 2.00 | 4.05 | 10.88 | -65,091 | -60,931 | 222,893 | -73,290 | 40.8 |
| all | const 30% | 2.02 | 4.14 | 11.53 | -60,650 | -55,362 | 198,179 | -71,413 | 39.6 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.264 / -0.218 / -0.097
- [PASS] 3 worst week within share: all-in worst week +8.5% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.89 vs p95 0.29 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.062, +0.300]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.211 / -0.257 / -0.117
- [FAIL] 6 worst-decile corr <=+0.30: +0.32
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_NQ); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2082 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6173 | -0.0112 | -0.29 |
| fixed | 6173 | -0.0563 | -1.41 |
| scaled | 6173 | -0.0563 | -1.41 |

Plateau neighbours (all-in 20% uplift; selected +0.120):
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '0.0'}: -0.282 (trades 5082)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '15', 'S': '0.75', 'R': '0.0'}: +0.035 (trades 2127)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '15', 'S': '1.0', 'R': '0.0'}: +0.090 (trades 1021)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '15', 'S': '1.25', 'R': '0.0'}: +0.091 (trades 2025)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.63, p95 0.29, real 0.89. Standalone Sharpe at 2x slippage 0.67.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 530 | -57 | -2.47 |
| 2014 | 593 | -52 | -1.85 |
| 2015 | 706 | -121 | -5.23 |
| 2016 | 644 | -82 | -3.21 |
| 2017 | 585 | -16 | -0.67 |
| 2018 | 612 | -26 | -1.13 |
| 2019 | 620 | -21 | -0.91 |
| 2020 | 554 | 21 | 0.99 |
| 2021 | 653 | -10 | -0.41 |
| 2022 | 676 | 16 | 0.62 |
| 2023 | 701 | 4 | 0.16 |
| 2024 | 692 | 62 | 2.09 |
| 2025 | 623 | 23 | 0.92 |
| 2026 | 461 | 0 | 0.01 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.55 | +0.26/-0.22/-0.10 |
| 2 tick entry / 2 tick exit | 1.05 | +0.16/-0.31/-0.13 |
| 3 tick entry / 3 tick exit | 0.56 | +0.07/-0.49/-0.17 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.16 | -0.07/-0.01/-0.17 |

DONE RU7_NQ