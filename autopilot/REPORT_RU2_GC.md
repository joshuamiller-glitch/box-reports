# REPORT RU2_GC
**Verdict: NO** (3/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=1.5, tf=15, S=1.5, R=2.0; additive @20% clean/H1/H2 +0.11/+0.37/-0.19; standalone all-in weekly Sharpe 0.66 (2013-26 -0.35, dev 2013-22 -0.79); pair-window trades 3101. Runtime 0.1 min (+selection 0.1 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |    net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|-------:|-------:|:-----------|
| GC    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 1915 |    0.939 | 66.329 |      2 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1347 |    0.791 | 48.510 |      3 | True       |
| GC    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | 2193 |    0.576 | 47.846 |      2 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 2.000 | 1178 |    0.430 | 23.334 |      2 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 2.000 |  904 |    0.371 | 20.663 |      3 | True       |
| GC    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 |  827 |    0.335 | 15.785 |      2 | True       |
| GC    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 |  868 |    0.148 |  8.307 |      2 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 1.500 |   15 | 1.500 | 2.000 | 2103 |    0.089 |  7.016 |      1 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 |  573 |    0.021 |  1.065 |      2 | True       |
| GC    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 2.000 | 1069 |    0.001 |  0.042 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.94; replicate best-eligible median 0.66, p95 1.32; real beats 75% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.29e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.064 | +0.219 | -0.083 | +0.047 | +2.4 | [-0.062, +0.151] | 0.16 | NO |
| 20% | add | +0.112 | +0.365 | -0.190 | +0.070 | +11.4 | [-0.144, +0.277] | 0.16 | NO |
| 30% | add | +0.144 | +0.435 | -0.314 | +0.072 | +20.4 | [-0.240, +0.374] | 0.16 | NO |
| 50% | add | +0.172 | +0.390 | -0.583 | +0.029 | +38.4 | [-0.450, +0.505] | 0.16 | NO |
| 10% | const | +0.070 | +0.239 | -0.093 | +0.051 | -7.0 | [-0.070, +0.165] | 0.16 | NO |
| 20% | const | +0.130 | +0.409 | -0.250 | +0.074 | -7.3 | [-0.190, +0.330] | 0.16 | NO |
| 30% | const | +0.167 | +0.428 | -0.486 | +0.050 | -7.6 | [-0.380, +0.468] | 0.16 | NO |
| 50% | const | +0.124 | -0.079 | -1.178 | -0.186 | +4.7 | [-0.935, +0.553] | 0.16 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 855,356, Sharpe 0.94, maxDD 465,407, worst wk -147,034; H1: net 388,477, Sharpe 1.21, maxDD 286,524, worst wk -195,832; H2: net -177,928, Sharpe -0.46, maxDD 363,725, worst wk -143,214; all: net 1,065,906, Sharpe 0.66, maxDD 465,407, worst wk -195,832
Correlation with pair (weekly): clean +0.15, H1 -0.15, H2 +0.06, all +0.07; worst-decile weeks (n=17) corr +0.18, sleeve mean in those weeks $19,828, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.57 | 3.08 | 5.75 | -87,543 | -81,218 | 260,848 | -91,901 | 42.9 |
| clean | add 30% | 1.60 | 3.14 | 6.01 | -92,098 | -84,619 | 263,963 | -99,330 | 42.9 |
| clean | const 20% | 1.59 | 3.12 | 6.03 | -71,857 | -66,223 | 204,826 | -76,493 | 42.9 |
| clean | const 30% | 1.63 | 3.15 | 5.56 | -68,996 | -63,856 | 213,403 | -76,217 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.19 | 7.19 | 4.53 | -65,112 | -60,844 | 148,382 | -65,720 | 35.7 |
| H1 | add 30% | 3.26 | 7.33 | 4.83 | -67,379 | -64,095 | 147,183 | -77,144 | 32.1 |
| H1 | const 20% | 3.24 | 7.30 | 4.68 | -52,996 | -49,976 | 118,040 | -57,145 | 35.7 |
| H1 | const 30% | 3.26 | 7.19 | 4.77 | -54,625 | -50,346 | 111,523 | -64,283 | 28.6 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.11 | 4.34 | 3.14 | -84,084 | -78,661 | 230,860 | -88,143 | 44.4 |
| H2 | add 30% | 1.98 | 4.06 | 2.98 | -86,926 | -80,438 | 237,578 | -92,388 | 44.4 |
| H2 | const 20% | 2.05 | 4.20 | 3.06 | -68,404 | -63,479 | 187,375 | -72,213 | 44.4 |
| H2 | const 30% | 1.81 | 3.66 | 2.78 | -63,406 | -58,409 | 172,350 | -68,492 | 47.2 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.93 | 3.86 | 11.11 | -85,756 | -78,919 | 260,848 | -91,901 | 42.3 |
| all | add 30% | 1.93 | 3.86 | 11.38 | -89,396 | -82,250 | 263,963 | -99,330 | 41.7 |
| all | const 20% | 1.93 | 3.87 | 11.53 | -70,034 | -64,266 | 204,826 | -76,493 | 42.3 |
| all | const 30% | 1.91 | 3.77 | 10.31 | -67,661 | -61,876 | 213,403 | -76,217 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.112 / +0.365 / -0.190
- [PASS] 3 worst week within share: all-in worst week +11.4% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.66 vs p95 0.11 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.144, +0.277]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 12% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.029 / +0.320 / -0.215
- [PASS] 6 worst-decile corr <=+0.30: +0.18
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_GC); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3101 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 7665 | +0.0005 | 0.01 |
| fixed | 7665 | -0.0353 | -0.79 |
| scaled | 7665 | -0.0353 | -0.79 |

Plateau neighbours (all-in 20% uplift; selected +0.070):
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.125', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.083 (trades 4891)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.125', 'R': '2.0'}: -0.038 (trades 3507)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.5'}: -0.066 (trades 3386)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '15'}: +0.045 (trades 3098)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.875', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.031 (trades 1663)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.875', 'R': '2.0'}: +0.036 (trades 2780)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.5'}: -0.009 (trades 2959)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '25'}: +0.095 (trades 3092)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.71, p95 0.11, real 0.66. Standalone Sharpe at 2x slippage 0.36.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 736 | 30 | 0.82 |
| 2014 | 670 | -39 | -1.34 |
| 2015 | 706 | -32 | -1.10 |
| 2016 | 758 | -94 | -3.09 |
| 2017 | 614 | -28 | -1.18 |
| 2018 | 667 | -23 | -0.92 |
| 2019 | 695 | -38 | -1.36 |
| 2020 | 897 | 7 | 0.16 |
| 2021 | 983 | -12 | -0.29 |
| 2022 | 939 | -42 | -0.91 |
| 2023 | 939 | -0 | -0.01 |
| 2024 | 979 | 50 | 1.38 |
| 2025 | 1004 | 62 | 1.57 |
| 2026 | 744 | -12 | -0.33 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.94 | +0.11/+0.37/-0.19 |
| 2 tick entry / 2 tick exit | -0.07 | -0.08/+0.30/-0.21 |
| 3 tick entry / 3 tick exit | -1.66 | -0.39/+0.20/-0.29 |
| retrace-limit DISP (b=1.5, tf15, f=0.5, RZ geometry) | -0.49 | -0.13/+0.47/-0.01 |

DONE RU2_GC