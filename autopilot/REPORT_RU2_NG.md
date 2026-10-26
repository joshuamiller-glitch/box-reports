# REPORT RU2_NG
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=1.0; additive @20% clean/H1/H2 +0.16/-0.57/-0.23; standalone all-in weekly Sharpe -0.05 (2013-26 -0.61, dev 2013-22 -0.74); pair-window trades 1709. Runtime 0.1 min (+selection 0.1 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |    net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|-------:|-------:|:-----------|
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 1.000 | 1070 |    0.861 | 37.958 |      2 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 |  776 |    0.758 | 42.157 |      2 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 2.000 | 1030 |    0.717 | 38.163 |      2 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 1.000 |  858 |    0.663 | 27.004 |      2 | True       |
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 2.000 |  696 |    0.647 | 30.637 |      2 | True       |
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 |  926 |    0.628 | 32.687 |      3 | True       |
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 1.000 | 1072 |    0.563 | 24.718 |      2 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 1.000 |  861 |    0.552 | 22.752 |      2 | True       |
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 1.000 |  782 |    0.550 | 21.808 |      2 | True       |
| NG    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 2.000 | 1335 |    0.469 | 29.680 |      2 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.86; replicate best-eligible median 0.77, p95 1.32; real beats 60% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.066e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.086 | -0.259 | -0.113 | -0.007 | +10.3 | [-0.110, +0.089] | 0.70 | NO |
| 20% | add | +0.156 | -0.571 | -0.234 | -0.034 | +23.9 | [-0.237, +0.157] | 0.70 | NO |
| 30% | add | +0.208 | -0.917 | -0.360 | -0.078 | +37.4 | [-0.380, +0.208] | 0.70 | NO |
| 50% | add | +0.265 | -1.627 | -0.613 | -0.204 | +64.5 | [-0.681, +0.241] | 0.70 | NO |
| 10% | const | +0.095 | -0.291 | -0.126 | -0.009 | +0.6 | [-0.123, +0.098] | 0.70 | NO |
| 20% | const | +0.184 | -0.741 | -0.296 | -0.054 | +4.5 | [-0.308, +0.184] | 0.70 | NO |
| 30% | const | +0.252 | -1.378 | -0.523 | -0.155 | +8.4 | [-0.574, +0.237] | 0.70 | NO |
| 50% | const | +0.223 | -2.947 | -1.169 | -0.577 | +16.1 | [-1.354, +0.149] | 0.70 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 784,221, Sharpe 0.86, maxDD 374,099, worst wk -113,950; H1: net -632,405, Sharpe -2.20, maxDD 850,168, worst wk -162,480; H2: net -220,032, Sharpe -0.77, maxDD 521,151, worst wk -138,457; all: net -68,216, Sharpe -0.05, maxDD 1,315,149, worst wk -162,480
Correlation with pair (weekly): clean -0.05, H1 -0.19, H2 +0.20, all -0.04; worst-decile weeks (n=17) corr +0.07, sleeve mean in those weeks $-11,655, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.62 | 3.12 | 5.28 | -90,795 | -82,155 | 281,776 | -102,221 | 42.9 |
| clean | add 30% | 1.67 | 3.22 | 5.54 | -97,303 | -85,106 | 282,609 | -113,398 | 42.9 |
| clean | const 20% | 1.64 | 3.18 | 5.41 | -75,239 | -66,558 | 225,754 | -86,248 | 41.9 |
| clean | const 30% | 1.71 | 3.26 | 5.87 | -73,970 | -63,733 | 198,576 | -89,437 | 40.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.26 | 4.49 | 3.14 | -70,369 | -66,350 | 148,697 | -71,667 | 42.9 |
| H1 | add 30% | 1.91 | 3.55 | 2.63 | -78,365 | -75,029 | 153,350 | -82,172 | 39.3 |
| H1 | const 20% | 2.09 | 4.02 | 2.95 | -58,253 | -56,551 | 118,354 | -60,498 | 39.3 |
| H1 | const 30% | 1.45 | 2.47 | 1.88 | -68,063 | -60,332 | 119,921 | -69,311 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.06 | 4.11 | 3.02 | -89,790 | -83,757 | 237,867 | -94,824 | 44.4 |
| H2 | add 30% | 1.94 | 3.80 | 2.80 | -94,141 | -87,185 | 248,087 | -100,974 | 41.7 |
| H2 | const 20% | 2.00 | 3.96 | 2.91 | -73,573 | -67,987 | 194,382 | -78,319 | 44.4 |
| H2 | const 30% | 1.77 | 3.41 | 2.52 | -70,410 | -65,227 | 185,154 | -76,216 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.82 | 3.54 | 9.48 | -89,200 | -81,845 | 281,776 | -102,221 | 42.9 |
| all | add 30% | 1.78 | 3.41 | 9.43 | -94,919 | -86,268 | 282,609 | -113,398 | 41.7 |
| all | const 20% | 1.80 | 3.48 | 9.45 | -73,505 | -67,099 | 225,754 | -86,248 | 41.7 |
| all | const 30% | 1.70 | 3.18 | 9.36 | -73,219 | -65,217 | 198,576 | -89,437 | 39.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.156 / -0.571 / -0.234
- [FAIL] 3 worst week within share: all-in worst week +23.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real -0.05 vs p95 -0.21 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.237, +0.157]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.078 / -0.682 / -0.300
- [PASS] 6 worst-decile corr <=+0.30: +0.07
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_NG); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1709 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 3532 | -0.0057 | -0.12 |
| fixed | 3532 | -0.0364 | -0.74 |
| scaled | 3532 | -0.0364 | -0.74 |

Plateau neighbours (all-in 20% uplift; selected -0.034):
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.0'}: -0.126 (trades 3142)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '1.0'}: -0.092 (trades 1712)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.75'}: -0.144 (trades 1788)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.0', 'L': '15'}: -0.037 (trades 1711)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '1.0'}: -0.005 (trades 756)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '1.0'}: +0.026 (trades 1689)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.25'}: -0.103 (trades 1628)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.0', 'L': '25'}: -0.038 (trades 1714)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.94, p95 -0.21, real -0.05. Standalone Sharpe at 2x slippage -0.42.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 320 | -8 | -0.49 |
| 2014 | 443 | -19 | -0.86 |
| 2015 | 310 | -20 | -1.44 |
| 2016 | 326 | -54 | -3.45 |
| 2017 | 253 | -1 | -0.07 |
| 2018 | 243 | -0 | -0.00 |
| 2019 | 227 | -21 | -1.86 |
| 2020 | 384 | -0 | -0.01 |
| 2021 | 459 | -6 | -0.32 |
| 2022 | 567 | 2 | 0.08 |
| 2023 | 492 | 2 | 0.11 |
| 2024 | 482 | -2 | -0.09 |
| 2025 | 645 | -20 | -0.82 |
| 2026 | 360 | -10 | -0.58 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.86 | +0.16/-0.57/-0.23 |
| 2 tick entry / 2 tick exit | -0.34 | -0.08/-0.84/-0.41 |
| 3 tick entry / 3 tick exit | -1.61 | -0.33/-1.30/-0.74 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | 0.04 | +0.04/-0.49/+0.00 |

DONE RU2_NG