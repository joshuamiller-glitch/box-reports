# REPORT RZ1_RTY
**Verdict: NO** (2/7 measured gates pass). Selected cell setup=FVG, tf=15, thr=0.5; additive @20% clean/H1/H2 +0.26/+0.05/-0.16; standalone all-in weekly Sharpe 1.14 (2013-26 0.67, dev 2013-22 0.45); pair-window trades 2038. Runtime 0.2 min (+selection 0.0 min). 10-worker pool.

RZ1 RTY: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |     net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|--------:|-------:|:-----------|
| RTY   | FVG     |   15 | 0.500 | 1281 |    1.708 | 125.523 |      3 | True       |
| RTY   | FVG     |   15 | 0.250 | 2013 |    1.359 | 113.340 |      2 | True       |
| RTY   | FVG     |   30 | 0.500 |  638 |    0.849 |  39.096 |      2 | True       |
| RTY   | FVG     |   30 | 0.250 | 1140 |    0.763 |  42.648 |      2 | True       |
| RTY   | DISP    |   15 | 1.500 | 1493 |   -0.690 | -49.220 |      1 | True       |
| RTY   | DISP    |   30 | 1.500 |  750 |   -0.887 | -39.328 |      0 | True       |
| RTY   | DISP    |   30 | 2.000 |  356 |   -0.906 | -29.954 |      0 | True       |
| RTY   | DISP    |   15 | 2.000 |  720 |   -0.923 | -42.197 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.71; replicate best-eligible median 0.23, p95 0.65; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.239e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.141 | +0.038 | -0.075 | +0.076 | +9.0 | [-0.007, +0.162] | 0.04 | NO |
| 20% | add | +0.261 | +0.047 | -0.157 | +0.134 | +21.1 | [-0.030, +0.301] | 0.04 | NO |
| 30% | add | +0.361 | +0.031 | -0.243 | +0.174 | +33.3 | [-0.062, +0.421] | 0.04 | NO |
| 50% | add | +0.503 | -0.063 | -0.421 | +0.211 | +57.6 | [-0.156, +0.593] | 0.04 | NO |
| 10% | const | +0.155 | +0.040 | -0.084 | +0.084 | -0.7 | [-0.009, +0.179] | 0.04 | NO |
| 20% | const | +0.313 | +0.042 | -0.200 | +0.156 | +1.8 | [-0.044, +0.364] | 0.04 | NO |
| 30% | const | +0.460 | -0.022 | -0.357 | +0.204 | +4.3 | [-0.119, +0.541] | 0.04 | NO |
| 50% | const | +0.639 | -0.458 | -0.838 | +0.154 | +9.2 | [-0.448, +0.783] | 0.04 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,555,646, Sharpe 1.71, maxDD 377,030, worst wk -113,068; H1: net 102,674, Sharpe 0.49, maxDD 175,609, worst wk -137,061; H2: net -95,596, Sharpe -0.40, maxDD 451,563, worst wk -99,916; all: net 1,562,724, Sharpe 1.14, maxDD 451,563, worst wk -137,061
Correlation with pair (weekly): clean +0.14, H1 -0.01, H2 +0.26, all +0.13; worst-decile weeks (n=17) corr +0.17, sleeve mean in those weeks $6,238, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.72 | 3.48 | 6.05 | -86,188 | -79,958 | 271,119 | -99,955 | 41.9 |
| clean | add 30% | 1.82 | 3.77 | 6.64 | -91,489 | -82,417 | 270,518 | -109,999 | 42.9 |
| clean | const 20% | 1.77 | 3.63 | 6.35 | -71,071 | -64,691 | 216,655 | -83,982 | 43.8 |
| clean | const 30% | 1.92 | 4.05 | 7.40 | -69,133 | -61,179 | 188,821 | -86,039 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.87 | 6.01 | 4.25 | -82,587 | -71,245 | 144,711 | -83,349 | 39.3 |
| H1 | add 30% | 2.86 | 5.90 | 4.42 | -85,076 | -74,019 | 141,210 | -86,557 | 35.7 |
| H1 | const 20% | 2.87 | 5.96 | 4.33 | -67,065 | -58,105 | 114,368 | -67,962 | 39.3 |
| H1 | const 30% | 2.81 | 5.74 | 4.38 | -61,793 | -54,310 | 101,916 | -63,477 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.14 | 4.28 | 3.50 | -88,306 | -84,361 | 211,883 | -90,526 | 41.7 |
| H2 | add 30% | 2.05 | 4.04 | 3.30 | -91,914 | -86,948 | 221,815 | -95,963 | 38.9 |
| H2 | const 20% | 2.10 | 4.16 | 3.44 | -72,088 | -68,524 | 171,274 | -74,596 | 38.9 |
| H2 | const 30% | 1.94 | 3.74 | 2.98 | -67,587 | -63,288 | 169,171 | -72,067 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.99 | 4.01 | 11.06 | -86,697 | -81,303 | 271,119 | -99,955 | 41.7 |
| all | add 30% | 2.03 | 4.13 | 11.66 | -91,282 | -84,403 | 270,518 | -109,999 | 41.1 |
| all | const 20% | 2.01 | 4.08 | 11.36 | -71,132 | -66,097 | 216,655 | -83,982 | 42.3 |
| all | const 30% | 2.06 | 4.21 | 12.44 | -68,161 | -62,599 | 188,821 | -86,039 | 41.1 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.261 / +0.047 / -0.157
- [FAIL] 3 worst week within share: all-in worst week +21.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.14 vs p95 -0.23 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.030, +0.301]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.206 / -0.012 / -0.204
- [PASS] 6 worst-decile corr <=+0.30: +0.17
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ1_RTY); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2038 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 3443 | +0.0618 | 1.24 |
| fixed | 3443 | +0.0228 | 0.45 |
| scaled | 3443 | +0.0228 | 0.45 |

Plateau neighbours (all-in 20% uplift; selected +0.134):
- {'sym': 'RTY', 'setup': 'FVG', 'tf': '15', 'thr': '0.375'}: +0.090 (trades 2664)
- {'sym': 'RTY', 'setup': 'FVG', 'tf': '15', 'thr': '0.5', 'R': '1.5'}: +0.121 (trades 2118)
- {'sym': 'RTY', 'setup': 'FVG', 'tf': '15', 'thr': '0.5', 'L': '15'}: +0.075 (trades 2002)
- {'sym': 'RTY', 'setup': 'FVG', 'tf': '15', 'thr': '0.625'}: +0.067 (trades 1600)
- {'sym': 'RTY', 'setup': 'FVG', 'tf': '15', 'thr': '0.5', 'R': '2.5'}: +0.111 (trades 1972)
- {'sym': 'RTY', 'setup': 'FVG', 'tf': '15', 'thr': '0.5', 'L': '25'}: +0.131 (trades 2061)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.11, p95 -0.23, real 1.14. Standalone Sharpe at 2x slippage 0.84.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2017 | 233 | -31 | -2.67 |
| 2018 | 648 | 28 | 0.91 |
| 2019 | 565 | -26 | -0.75 |
| 2020 | 650 | 56 | 1.67 |
| 2021 | 667 | 9 | 0.28 |
| 2022 | 680 | 43 | 1.47 |
| 2023 | 655 | 35 | 1.05 |
| 2024 | 633 | 47 | 1.50 |
| 2025 | 598 | 55 | 1.39 |
| 2026 | 518 | -14 | -0.66 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 1080 | -0.069 | 0.038 |
| 2013-22 | mid | 1141 | +0.023 | 0.039 |
| 2013-22 | high | 1200 | +0.112 | 0.039 |
| 2023-26 | low | 692 | -0.002 | 0.050 |
| 2023-26 | mid | 682 | +0.072 | 0.051 |
| 2023-26 | high | 664 | +0.117 | 0.053 |

DONE RZ1_RTY