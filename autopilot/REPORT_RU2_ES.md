# REPORT RU2_ES
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=1.5, tf=15, S=1.5, R=2.0; additive @20% clean/H1/H2 +0.01/-0.71/-0.27; standalone all-in weekly Sharpe -0.31 (2013-26 -0.53, dev 2013-22 -0.53); pair-window trades 3376. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| ES    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 2086 |    0.224 |  18.431 |      2 | True       |
| ES    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | 1494 |    0.100 |   7.267 |      1 | True       |
| ES    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 | 1067 |    0.064 |   3.963 |      2 | True       |
| ES    |    1 |      0 | ALL    | mkt   | 1.500 |   15 | 1.500 | 1.000 | 2861 |    0.009 |   0.637 |      2 | True       |
| ES    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 2.000 | 1320 |   -0.015 |  -0.914 |      2 | True       |
| ES    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | 2291 |   -0.191 | -18.659 |      1 | True       |
| ES    |    1 |      0 | ALL    | mkt   | 1.500 |   15 | 1.500 | 2.000 | 2273 |   -0.195 | -16.654 |      1 | True       |
| ES    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | 1102 |   -0.263 | -16.301 |      2 | True       |
| ES    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 2.000 |  665 |   -0.410 | -18.213 |      1 | True       |
| ES    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 1.000 | 1556 |   -0.432 | -24.552 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.22; replicate best-eligible median 0.23, p95 0.76; real beats 45% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.106e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.012 | -0.369 | -0.131 | -0.066 | +9.8 | [-0.169, +0.031] | 0.03 | NO |
| 20% | add | +0.010 | -0.714 | -0.272 | -0.146 | +24.7 | [-0.345, +0.043] | 0.03 | NO |
| 30% | add | -0.005 | -1.028 | -0.418 | -0.236 | +39.6 | [-0.522, +0.039] | 0.03 | NO |
| 50% | add | -0.064 | -1.557 | -0.702 | -0.427 | +69.4 | [-0.868, -0.008] | 0.03 | NO |
| 10% | const | +0.013 | -0.408 | -0.147 | -0.074 | +0.3 | [-0.187, +0.033] | 0.03 | NO |
| 20% | const | +0.004 | -0.875 | -0.345 | -0.190 | +5.7 | [-0.435, +0.042] | 0.03 | NO |
| 30% | const | -0.039 | -1.382 | -0.602 | -0.358 | +11.2 | [-0.744, +0.014] | 0.03 | NO |
| 50% | const | -0.280 | -2.423 | -1.288 | -0.857 | +23.9 | [-1.546, -0.190] | 0.03 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 203,774, Sharpe 0.22, maxDD 738,896, worst wk -123,486; H1: net -425,432, Sharpe -1.55, maxDD 695,070, worst wk -150,659; H2: net -244,015, Sharpe -0.73, maxDD 603,917, worst wk -167,137; all: net -465,673, Sharpe -0.31, maxDD 1,235,989, worst wk -167,137
Correlation with pair (weekly): clean +0.02, H1 +0.47, H2 +0.23, all +0.13; worst-decile weeks (n=17) corr +0.09, sleeve mean in those weeks $-13,841, positive share 0.29.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.47 | 2.81 | 4.89 | -88,939 | -82,724 | 280,583 | -97,698 | 43.8 |
| clean | add 30% | 1.46 | 2.77 | 4.80 | -94,689 | -85,133 | 289,966 | -107,768 | 42.9 |
| clean | const 20% | 1.46 | 2.79 | 4.92 | -73,451 | -67,122 | 224,561 | -82,186 | 41.9 |
| clean | const 30% | 1.42 | 2.67 | 4.26 | -71,457 | -63,099 | 232,694 | -84,501 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.11 | 3.99 | 2.70 | -100,030 | -87,647 | 188,436 | -102,908 | 39.3 |
| H1 | add 30% | 1.80 | 3.23 | 2.25 | -111,240 | -98,622 | 206,798 | -115,218 | 42.9 |
| H1 | const 20% | 1.95 | 3.59 | 2.47 | -84,508 | -74,507 | 158,094 | -87,250 | 39.3 |
| H1 | const 30% | 1.45 | 2.45 | 1.79 | -87,957 | -78,913 | 161,284 | -91,731 | 46.4 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.03 | 4.08 | 3.51 | -88,405 | -84,475 | 208,028 | -90,870 | 43.2 |
| H2 | add 30% | 1.88 | 3.74 | 3.40 | -97,901 | -89,759 | 207,280 | -100,758 | 45.9 |
| H2 | const 20% | 1.95 | 3.91 | 3.45 | -74,522 | -69,694 | 166,123 | -74,679 | 45.9 |
| H2 | const 30% | 1.70 | 3.30 | 3.21 | -77,076 | -71,030 | 146,829 | -83,866 | 54.1 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.71 | 3.29 | 9.30 | -92,130 | -85,172 | 280,583 | -102,908 | 43.2 |
| all | add 30% | 1.62 | 3.07 | 8.84 | -100,327 | -90,423 | 289,966 | -115,218 | 43.8 |
| all | const 20% | 1.67 | 3.19 | 9.21 | -76,983 | -69,880 | 224,561 | -87,250 | 42.6 |
| all | const 30% | 1.50 | 2.77 | 7.53 | -77,622 | -68,888 | 232,694 | -91,731 | 46.2 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.010 / -0.714 / -0.272
- [FAIL] 3 worst week within share: all-in worst week +24.7% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real -0.31 vs p95 -0.67 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.345, +0.043]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.085 / -0.812 / -0.340
- [PASS] 6 worst-decile corr <=+0.30: +0.09
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_ES); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3376 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6113 | +0.0099 | 0.22 |
| fixed | 6113 | -0.0236 | -0.53 |
| scaled | 6113 | -0.0236 | -0.53 |

Plateau neighbours (all-in 20% uplift; selected -0.146):
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.125', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.229 (trades 4741)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.125', 'R': '2.0'}: -0.423 (trades 3683)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.5'}: -0.372 (trades 3658)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '15'}: -0.142 (trades 3377)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.875', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.091 (trades 2009)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.875', 'R': '2.0'}: -0.159 (trades 3083)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.5'}: -0.193 (trades 3196)
- {'sym': 'ES', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '25'}: -0.151 (trades 3369)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.45, p95 -0.67, real -0.31. Standalone Sharpe at 2x slippage -0.75.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 231 | -42 | -3.18 |
| 2014 | 314 | -6 | -0.39 |
| 2015 | 533 | -67 | -2.63 |
| 2016 | 503 | -36 | -2.02 |
| 2017 | 211 | -29 | -3.25 |
| 2018 | 729 | -6 | -0.19 |
| 2019 | 656 | -11 | -0.38 |
| 2020 | 929 | 5 | 0.16 |
| 2021 | 907 | 38 | 1.04 |
| 2022 | 1100 | 9 | 0.22 |
| 2023 | 1002 | -10 | -0.26 |
| 2024 | 1045 | -24 | -0.56 |
| 2025 | 1057 | -15 | -0.37 |
| 2026 | 852 | -36 | -1.01 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.22 | +0.01/-0.71/-0.27 |
| 2 tick entry / 2 tick exit | -0.89 | -0.21/-0.88/-0.39 |
| 3 tick entry / 3 tick exit | -2.33 | -0.50/-1.14/-0.52 |
| retrace-limit DISP (b=1.5, tf15, f=0.5, RZ geometry) | -0.34 | -0.09/-0.06/-0.01 |

DONE RU2_ES