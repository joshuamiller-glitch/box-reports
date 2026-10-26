# REPORT RU2_SI
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=1.0; additive @20% clean/H1/H2 +0.17/-0.09/+0.23; standalone all-in weekly Sharpe 0.94 (2013-26 -0.18, dev 2013-22 -0.73); pair-window trades 1654. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 1.000 |  998 |    1.067 |  43.844 |      2 | True       |
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 1.000 |  999 |    0.782 |  32.101 |      2 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 1.000 | 1127 |    0.006 |   0.307 |      2 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.000 | 1.000 | 1132 |   -0.040 |  -1.982 |      1 | True       |
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 |  872 |   -0.289 | -14.727 |      1 | True       |
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 |  881 |   -0.346 | -17.330 |      2 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.000 | 2.000 | 1003 |   -0.349 | -20.315 |      2 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 1.000 |  677 |   -0.569 | -18.685 |      0 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 1.000 | 1445 |   -0.574 | -29.143 |      1 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 1.000 |  681 |   -0.656 | -21.183 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.07; replicate best-eligible median 0.09, p95 0.86; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.217e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.093 | -0.033 | +0.127 | +0.080 | +7.2 | [-0.014, +0.175] | 0.33 | NO |
| 20% | add | +0.169 | -0.095 | +0.226 | +0.139 | +20.9 | [-0.046, +0.327] | 0.33 | NO |
| 30% | add | +0.228 | -0.185 | +0.297 | +0.177 | +34.6 | [-0.097, +0.452] | 0.33 | NO |
| 50% | add | +0.297 | -0.437 | +0.370 | +0.201 | +62.0 | [-0.229, +0.634] | 0.33 | NO |
| 10% | const | +0.102 | -0.038 | +0.140 | +0.087 | -2.2 | [-0.017, +0.193] | 0.33 | NO |
| 20% | const | +0.201 | -0.136 | +0.264 | +0.160 | +2.2 | [-0.069, +0.392] | 0.33 | NO |
| 30% | const | +0.279 | -0.338 | +0.353 | +0.200 | +6.6 | [-0.176, +0.577] | 0.33 | NO |
| 50% | const | +0.294 | -1.202 | +0.331 | +0.091 | +15.3 | [-0.622, +0.785] | 0.33 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 971,840, Sharpe 1.07, maxDD 500,413, worst wk -165,006; H1: net -166,701, Sharpe -0.79, maxDD 373,260, worst wk -113,792; H2: net 577,748, Sharpe 1.67, maxDD 220,010, worst wk -113,135; all: net 1,382,886, Sharpe 0.94, maxDD 500,413, worst wk -165,006
Correlation with pair (weekly): clean +0.04, H1 -0.22, H2 +0.14, all +0.03; worst-decile weeks (n=17) corr -0.02, sleeve mean in those weeks $10,185, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.63 | 3.23 | 5.74 | -82,549 | -78,416 | 265,758 | -87,472 | 46.7 |
| clean | add 30% | 1.69 | 3.42 | 5.90 | -85,799 | -79,724 | 274,690 | -91,976 | 47.6 |
| clean | const 20% | 1.66 | 3.33 | 5.82 | -67,339 | -63,057 | 216,179 | -71,658 | 46.7 |
| clean | const 30% | 1.74 | 3.58 | 6.08 | -62,985 | -57,633 | 201,189 | -68,709 | 48.6 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.73 | 5.70 | 3.36 | -73,164 | -68,800 | 166,949 | -73,792 | 35.7 |
| H1 | add 30% | 2.64 | 5.37 | 3.08 | -70,942 | -70,352 | 176,292 | -71,544 | 35.7 |
| H1 | const 20% | 2.69 | 5.54 | 3.23 | -57,643 | -55,661 | 136,606 | -58,134 | 35.7 |
| H1 | const 30% | 2.49 | 4.89 | 2.72 | -52,334 | -50,643 | 134,314 | -56,611 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.52 | 5.28 | 4.08 | -91,367 | -81,099 | 214,733 | -99,774 | 36.1 |
| H2 | add 30% | 2.59 | 5.40 | 4.38 | -97,133 | -84,694 | 213,388 | -111,087 | 33.3 |
| H2 | const 20% | 2.56 | 5.35 | 4.23 | -75,400 | -66,317 | 171,248 | -84,345 | 36.1 |
| H2 | const 30% | 2.65 | 5.48 | 4.69 | -74,681 | -64,773 | 150,549 | -87,943 | 33.3 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.99 | 4.02 | 11.14 | -83,899 | -78,533 | 265,758 | -99,774 | 42.9 |
| all | add 30% | 2.03 | 4.14 | 11.29 | -87,486 | -80,044 | 274,690 | -111,087 | 42.9 |
| all | const 20% | 2.02 | 4.09 | 11.22 | -68,499 | -63,320 | 216,179 | -84,345 | 42.9 |
| all | const 30% | 2.06 | 4.21 | 11.40 | -65,077 | -58,690 | 201,189 | -87,943 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.169 / -0.095 / +0.226
- [FAIL] 3 worst week within share: all-in worst week +20.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.94 vs p95 0.34 (rank 0.99)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.046, +0.327]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 25% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.091 / -0.145 / +0.197
- [PASS] 6 worst-decile corr <=+0.30: -0.02
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_SI); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1654 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2338 | -0.0158 | -0.28 |
| fixed | 2338 | -0.0415 | -0.73 |
| scaled | 2338 | -0.0415 | -0.73 |

Plateau neighbours (all-in 20% uplift; selected +0.139):
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.0'}: -0.194 (trades 3385)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '1.0'}: +0.063 (trades 1663)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.75'}: +0.086 (trades 1696)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.0', 'L': '15'}: +0.136 (trades 1650)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '1.0'}: -0.019 (trades 725)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '1.0'}: +0.051 (trades 1612)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.25'}: +0.041 (trades 1591)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.0', 'L': '25'}: +0.141 (trades 1662)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.28, p95 0.34, real 0.94. Standalone Sharpe at 2x slippage 0.62.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 359 | -26 | -1.67 |
| 2014 | 188 | 14 | 1.49 |
| 2015 | 174 | -18 | -1.66 |
| 2016 | 214 | -2 | -0.17 |
| 2017 | 82 | -7 | -1.16 |
| 2018 | 39 | -4 | -1.03 |
| 2019 | 87 | -3 | -0.38 |
| 2020 | 334 | -26 | -1.59 |
| 2021 | 447 | -20 | -0.97 |
| 2022 | 414 | -4 | -0.25 |
| 2023 | 432 | -9 | -0.40 |
| 2024 | 508 | 9 | 0.39 |
| 2025 | 532 | 36 | 2.00 |
| 2026 | 441 | 21 | 1.18 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.07 | +0.17/-0.09/+0.23 |
| 2 tick entry / 2 tick exit | -0.05 | -0.04/-0.18/+0.14 |
| 3 tick entry / 3 tick exit | -1.10 | -0.24/-0.34/+0.05 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.20 | -0.07/+0.08/+0.01 |

DONE RU2_SI