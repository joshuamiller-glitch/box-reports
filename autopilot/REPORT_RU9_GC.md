# REPORT RU9_GC
**Verdict: NO** (0/7 measured gates pass). Selected cell nb=3, conf=0, sess=ALL, ent=mkt, k=1.5, tf=15, S=1.0, R=2.0; additive @20% clean/H1/H2 -0.03/-0.64/-0.12; standalone all-in weekly Sharpe -0.49 (2013-26 -1.01, dev 2013-22 -1.07); pair-window trades 4303. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| GC    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 2579 |    0.136 |  13.076 |      2 | True       |
| GC    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  317 |   -0.211 |  -8.090 |      2 | True       |
| GC    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  559 |   -0.223 | -10.375 |      1 | True       |
| GC    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1384 |   -0.315 | -21.176 |      2 | True       |
| GC    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  835 |   -0.469 | -25.705 |      1 | True       |
| GC    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1483 |   -0.669 | -49.594 |      0 | True       |
| GC    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 2660 |   -0.873 | -75.924 |      1 | True       |
| GC    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  451 |   -1.279 | -48.367 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.14; replicate best-eligible median 0.11, p95 0.64; real beats 55% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=9478)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.010 | -0.288 | -0.047 | -0.065 | +9.1 | [-0.167, +0.036] | 0.48 | NO |
| 20% | add | -0.032 | -0.644 | -0.115 | -0.148 | +22.5 | [-0.351, +0.051] | 0.48 | NO |
| 30% | add | -0.064 | -1.043 | -0.203 | -0.245 | +37.2 | [-0.542, +0.051] | 0.48 | NO |
| 50% | add | -0.150 | -1.850 | -0.417 | -0.461 | +66.4 | [-0.935, +0.001] | 0.48 | NO |
| 10% | const | -0.011 | -0.325 | -0.053 | -0.073 | -0.8 | [-0.186, +0.038] | 0.48 | NO |
| 20% | const | -0.047 | -0.840 | -0.157 | -0.195 | +3.9 | [-0.446, +0.054] | 0.48 | NO |
| 30% | const | -0.117 | -1.570 | -0.336 | -0.382 | +9.2 | [-0.793, +0.027] | 0.48 | NO |
| 50% | const | -0.389 | -3.252 | -0.980 | -0.962 | +19.8 | [-1.717, -0.207] | 0.48 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 123,935, Sharpe 0.14, maxDD 804,539, worst wk -126,179; H1: net -735,954, Sharpe -2.33, maxDD 1,003,725, worst wk -197,951; H2: net -163,137, Sharpe -0.48, maxDD 430,849, worst wk -143,234; all: net -775,156, Sharpe -0.49, maxDD 1,551,574, worst wk -197,951
Correlation with pair (weekly): clean +0.11, H1 -0.24, H2 -0.06, all +0.00; worst-decile weeks (n=17) corr +0.35, sleeve mean in those weeks $13,833, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.43 | 2.78 | 4.25 | -90,078 | -81,177 | 318,838 | -101,104 | 48.6 |
| clean | add 30% | 1.40 | 2.73 | 4.04 | -97,118 | -86,152 | 338,203 | -113,184 | 49.5 |
| clean | const 20% | 1.41 | 2.76 | 4.14 | -74,878 | -66,818 | 262,817 | -85,715 | 49.5 |
| clean | const 30% | 1.34 | 2.61 | 3.81 | -75,673 | -65,784 | 254,170 | -90,102 | 51.4 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.18 | 4.09 | 2.72 | -73,454 | -66,996 | 164,011 | -82,253 | 35.7 |
| H1 | add 30% | 1.78 | 3.15 | 1.96 | -71,960 | -67,600 | 190,684 | -84,236 | 35.7 |
| H1 | const 20% | 1.99 | 3.61 | 2.39 | -57,932 | -53,790 | 137,074 | -66,595 | 35.7 |
| H1 | const 30% | 1.26 | 2.08 | 1.10 | -58,617 | -55,035 | 177,947 | -60,749 | 39.3 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.18 | 4.24 | 3.11 | -90,446 | -82,823 | 240,040 | -90,557 | 35.1 |
| H2 | add 30% | 2.09 | 3.99 | 2.86 | -96,401 | -86,760 | 255,298 | -96,794 | 37.8 |
| H2 | const 20% | 2.14 | 4.12 | 2.98 | -74,739 | -67,834 | 198,136 | -74,851 | 37.8 |
| H2 | const 30% | 1.96 | 3.66 | 2.58 | -72,841 | -64,276 | 192,441 | -73,569 | 37.8 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.71 | 3.30 | 7.99 | -89,290 | -80,734 | 318,838 | -101,104 | 43.8 |
| all | add 30% | 1.61 | 3.08 | 7.30 | -96,002 | -85,043 | 338,203 | -113,184 | 45.0 |
| all | const 20% | 1.66 | 3.20 | 7.64 | -73,978 | -66,168 | 262,817 | -85,715 | 45.0 |
| all | const 30% | 1.48 | 2.77 | 6.53 | -73,810 | -64,646 | 254,170 | -90,102 | 46.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.032 / -0.644 / -0.115
- [FAIL] 3 worst week within share: all-in worst week +22.5% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.49 vs p95 -0.30 (rank 0.91)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.351, +0.051]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.131 / -0.722 / -0.153
- [FAIL] 6 worst-decile corr <=+0.30: +0.35
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_GC); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (4303 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 9543 | -0.0037 | -0.10 |
| fixed | 9543 | -0.0421 | -1.07 |
| scaled | 9543 | -0.0421 | -1.07 |

Plateau neighbours (all-in 20% uplift; selected -0.148):
- {'sym': 'GC', 'nb': '3', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.125', 'tf': '15', 'S': '1.0', 'R': '2.0'}: -0.242 (trades 5794)
- {'sym': 'GC', 'nb': '3', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '0.75', 'R': '2.0'}: -0.247 (trades 4555)
- {'sym': 'GC', 'nb': '3', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '1.5'}: -0.232 (trades 4644)
- {'sym': 'GC', 'nb': '3', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '15', 'S': '1.0', 'R': '2.0'}: -0.140 (trades 2943)
- {'sym': 'GC', 'nb': '3', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '1.25', 'R': '2.0'}: -0.015 (trades 3956)
- {'sym': 'GC', 'nb': '3', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '2.5'}: -0.173 (trades 3996)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.16, p95 -0.30, real -0.49. Standalone Sharpe at 2x slippage -0.87.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 1008 | -16 | -0.39 |
| 2014 | 821 | -31 | -1.14 |
| 2015 | 818 | 3 | 0.07 |
| 2016 | 963 | -87 | -2.70 |
| 2017 | 757 | -62 | -2.05 |
| 2018 | 781 | 28 | 1.08 |
| 2019 | 852 | -47 | -1.25 |
| 2020 | 1218 | -94 | -2.12 |
| 2021 | 1112 | -64 | -1.41 |
| 2022 | 1213 | -30 | -0.64 |
| 2023 | 1145 | -85 | -1.77 |
| 2024 | 1283 | 3 | 0.07 |
| 2025 | 1462 | -84 | -1.46 |
| 2026 | 1096 | -11 | -0.26 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.14 | -0.03/-0.64/-0.12 |
| 2 tick entry / 2 tick exit | -1.18 | -0.28/-0.88/-0.23 |
| 3 tick entry / 3 tick exit | -2.31 | -0.50/-1.07/-0.32 |

DONE RU9_GC