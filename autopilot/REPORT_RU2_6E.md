# REPORT RU2_6E
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=2.0; additive @20% clean/H1/H2 -0.18/+0.02/-0.16; standalone all-in weekly Sharpe -0.68 (2013-26 -3.30, dev 2013-22 -4.03); pair-window trades 1086. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 |  734 |   -0.757 | -40.634 |      1 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | 1420 |   -0.777 | -54.300 |      2 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 1400 |   -0.795 | -55.618 |      2 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 |  740 |   -0.804 | -44.394 |      1 | True       |
| 6E    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 2.000 | 1169 |   -0.829 | -46.777 |      0 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 2.000 |  496 |   -0.833 | -28.508 |      1 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | 1078 |   -0.837 | -44.893 |      0 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 2.000 |  500 |   -0.890 | -30.264 |      0 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 2.000 | 1050 |   -0.913 | -43.981 |      0 | True       |
| 6E    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 1.000 | 1374 |   -1.036 | -53.709 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.76; replicate best-eligible median -0.27, p95 0.27; real beats 0% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.697e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.083 | +0.026 | -0.077 | -0.071 | +7.2 | [-0.157, +0.013] | 0.52 | NO |
| 20% | add | -0.177 | +0.021 | -0.162 | -0.156 | +19.9 | [-0.326, +0.010] | 0.52 | NO |
| 30% | add | -0.279 | -0.016 | -0.252 | -0.252 | +32.5 | [-0.503, -0.004] | 0.52 | NO |
| 50% | add | -0.493 | -0.173 | -0.443 | -0.462 | +57.7 | [-0.859, -0.071] | 0.52 | NO |
| 10% | const | -0.093 | +0.027 | -0.086 | -0.080 | -2.2 | [-0.175, +0.014] | 0.52 | NO |
| 20% | const | -0.227 | +0.006 | -0.206 | -0.203 | +0.9 | [-0.414, +0.005] | 0.52 | NO |
| 30% | const | -0.417 | -0.106 | -0.373 | -0.386 | +4.1 | [-0.732, -0.041] | 0.52 | NO |
| 50% | const | -0.963 | -0.774 | -0.925 | -0.967 | +10.4 | [-1.614, -0.305] | 0.52 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -689,601, Sharpe -0.76, maxDD 1,150,067, worst wk -160,842; H1: net -35,810, Sharpe -0.16, maxDD 425,976, worst wk -89,710; H2: net -205,324, Sharpe -0.95, maxDD 351,619, worst wk -76,304; all: net -930,735, Sharpe -0.68, maxDD 1,150,067, worst wk -160,842
Correlation with pair (weekly): clean +0.00, H1 -0.20, H2 +0.08, all -0.00; worst-decile weeks (n=17) corr +0.17, sleeve mean in those weeks $7,165, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.28 | 2.38 | 4.31 | -83,756 | -80,154 | 276,847 | -98,922 | 45.7 |
| clean | add 30% | 1.18 | 2.15 | 3.71 | -86,932 | -81,514 | 302,809 | -109,342 | 45.7 |
| clean | const 20% | 1.23 | 2.27 | 4.02 | -68,272 | -64,636 | 230,367 | -83,306 | 45.7 |
| clean | const 30% | 1.04 | 1.85 | 3.03 | -63,953 | -59,719 | 238,696 | -85,917 | 49.5 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.85 | 6.67 | 3.58 | -66,312 | -57,278 | 164,035 | -71,962 | 42.9 |
| H1 | add 30% | 2.81 | 6.84 | 3.43 | -60,662 | -53,068 | 170,196 | -68,799 | 46.4 |
| H1 | const 20% | 2.83 | 6.77 | 3.50 | -50,790 | -44,138 | 133,692 | -56,304 | 42.9 |
| H1 | const 30% | 2.72 | 6.86 | 3.25 | -37,379 | -33,359 | 124,682 | -45,313 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.14 | 4.32 | 3.29 | -83,223 | -79,092 | 224,053 | -83,363 | 43.2 |
| H2 | add 30% | 2.05 | 4.12 | 3.15 | -84,850 | -79,045 | 227,367 | -85,917 | 43.2 |
| H2 | const 20% | 2.09 | 4.23 | 3.22 | -67,229 | -63,255 | 180,568 | -67,600 | 43.2 |
| H2 | const 30% | 1.92 | 3.84 | 2.98 | -60,859 | -55,319 | 162,140 | -62,692 | 43.2 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.70 | 3.30 | 9.09 | -83,252 | -78,907 | 276,847 | -98,922 | 45.0 |
| all | add 30% | 1.61 | 3.08 | 8.00 | -85,766 | -79,841 | 302,809 | -109,342 | 45.6 |
| all | const 20% | 1.66 | 3.19 | 8.58 | -67,605 | -63,391 | 230,367 | -83,306 | 45.0 |
| all | const 30% | 1.47 | 2.77 | 6.75 | -62,460 | -58,424 | 238,696 | -85,917 | 47.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.177 / +0.021 / -0.162
- [PASS] 3 worst week within share: all-in worst week +19.9% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.68 vs p95 -0.43 (rank 0.85)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.326, +0.010]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.247 / -0.043 / -0.215
- [PASS] 6 worst-decile corr <=+0.30: +0.17
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_6E); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1086 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 4955 | -0.3565 | -3.67 |
| fixed | 4955 | -0.3982 | -4.03 |
| scaled | 4955 | -0.3982 | -4.03 |

Plateau neighbours (all-in 20% uplift; selected -0.156):
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.292 (trades 2220)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '2.0'}: -0.169 (trades 1092)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.5'}: -0.221 (trades 1128)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '15'}: -0.149 (trades 1079)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.094 (trades 461)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '2.0'}: -0.127 (trades 1074)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '2.5'}: -0.142 (trades 1063)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '25'}: -0.156 (trades 1089)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.15, p95 -0.43, real -0.68. Standalone Sharpe at 2x slippage -1.03.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 793 | -634 | -14.29 |
| 2014 | 689 | -550 | -12.69 |
| 2015 | 799 | -593 | -10.68 |
| 2016 | 405 | -3 | -0.11 |
| 2017 | 389 | -51 | -1.58 |
| 2018 | 419 | -35 | -1.30 |
| 2019 | 286 | -28 | -1.37 |
| 2020 | 377 | -3 | -0.13 |
| 2021 | 372 | -33 | -1.53 |
| 2022 | 426 | -43 | -1.49 |
| 2023 | 428 | -36 | -1.30 |
| 2024 | 346 | -38 | -1.70 |
| 2025 | 333 | 12 | 0.43 |
| 2026 | 222 | -12 | -0.80 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.76 | -0.18/+0.02/-0.16 |
| 2 tick entry / 2 tick exit | -1.55 | -0.34/-0.07/-0.26 |
| 3 tick entry / 3 tick exit | -2.30 | -0.48/-0.19/-0.35 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.13 | -0.05/-0.27/-0.20 |

DONE RU2_6E