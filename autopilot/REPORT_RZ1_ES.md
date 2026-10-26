# REPORT RZ1_ES
**Verdict: NO** (1/7 measured gates pass). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.11/-0.14/+0.46; standalone all-in weekly Sharpe 1.14 (2013-26 1.18, dev 2013-22 1.28); pair-window trades 2913. Runtime 0.2 min (+selection 0.1 min). 10-worker pool.

RZ1 ES: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |     net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|--------:|-------:|:-----------|
| ES    | FVG     |   15 | 0.250 | 1748 |    0.931 |  65.929 |      3 | True       |
| ES    | DISP    |   30 | 2.000 |  338 |    0.232 |   8.493 |      2 | True       |
| ES    | DISP    |   30 | 1.500 |  725 |    0.073 |   3.587 |      1 | True       |
| ES    | FVG     |   30 | 0.250 | 1061 |   -0.033 |  -1.838 |      1 | True       |
| ES    | DISP    |   15 | 2.000 |  642 |   -0.072 |  -4.082 |      1 | True       |
| ES    | FVG     |   30 | 0.500 |  631 |   -0.291 | -13.872 |      1 | True       |
| ES    | DISP    |   15 | 1.500 | 1290 |   -0.338 | -22.782 |      1 | True       |
| ES    | FVG     |   15 | 0.500 | 1137 |   -0.901 | -50.975 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.93; replicate best-eligible median -0.14, p95 0.31; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.287e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.064 | -0.050 | +0.246 | +0.088 | +10.3 | [-0.013, +0.187] | 0.06 | NO |
| 20% | add | +0.111 | -0.138 | +0.456 | +0.151 | +24.3 | [-0.048, +0.346] | 0.06 | NO |
| 30% | add | +0.143 | -0.254 | +0.625 | +0.193 | +39.4 | [-0.097, +0.474] | 0.06 | NO |
| 50% | add | +0.170 | -0.520 | +0.851 | +0.220 | +69.7 | [-0.225, +0.660] | 0.06 | NO |
| 10% | const | +0.070 | -0.058 | +0.271 | +0.096 | +0.7 | [-0.015, +0.206] | 0.06 | NO |
| 20% | const | +0.129 | -0.193 | +0.546 | +0.175 | +5.5 | [-0.073, +0.414] | 0.06 | NO |
| 30% | const | +0.166 | -0.423 | +0.787 | +0.217 | +11.2 | [-0.173, +0.605] | 0.06 | NO |
| 50% | const | +0.120 | -1.112 | +0.991 | +0.129 | +35.8 | [-0.585, +0.834] | 0.06 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 848,200, Sharpe 0.93, maxDD 370,955, worst wk -174,293; H1: net 38,524, Sharpe 0.14, maxDD 230,042, worst wk -115,866; H2: net 887,949, Sharpe 2.40, maxDD 251,579, worst wk -134,142; all: net 1,774,674, Sharpe 1.14, maxDD 386,345, worst wk -174,293
Correlation with pair (weekly): clean +0.14, H1 +0.12, H2 +0.02, all +0.11; worst-decile weeks (n=17) corr +0.36, sleeve mean in those weeks $-974, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.57 | 3.06 | 5.22 | -88,975 | -83,092 | 287,328 | -102,548 | 46.7 |
| clean | add 30% | 1.60 | 3.13 | 5.45 | -96,689 | -86,891 | 290,937 | -115,043 | 43.8 |
| clean | const 20% | 1.59 | 3.10 | 5.33 | -74,265 | -67,993 | 231,306 | -87,036 | 43.8 |
| clean | const 30% | 1.63 | 3.16 | 5.73 | -74,625 | -64,388 | 206,905 | -91,775 | 46.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.69 | 5.50 | 3.79 | -85,449 | -73,800 | 158,908 | -100,106 | 42.9 |
| H1 | add 30% | 2.57 | 5.16 | 3.72 | -89,369 | -77,852 | 162,789 | -111,692 | 42.9 |
| H1 | const 20% | 2.63 | 5.33 | 3.75 | -69,927 | -60,661 | 128,565 | -84,719 | 39.3 |
| H1 | const 30% | 2.41 | 4.74 | 3.38 | -66,086 | -58,143 | 126,452 | -88,612 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.75 | 5.97 | 4.25 | -92,219 | -81,216 | 220,732 | -102,471 | 41.7 |
| H2 | add 30% | 2.92 | 6.41 | 4.62 | -97,784 | -82,699 | 222,386 | -113,880 | 36.1 |
| H2 | const 20% | 2.84 | 6.21 | 4.44 | -76,001 | -65,379 | 177,247 | -86,541 | 38.9 |
| H2 | const 30% | 3.08 | 6.78 | 5.09 | -73,457 | -60,526 | 157,158 | -89,984 | 30.6 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.01 | 4.02 | 10.58 | -90,932 | -82,928 | 287,328 | -102,548 | 45.2 |
| all | add 30% | 2.05 | 4.11 | 11.06 | -98,599 | -86,196 | 290,937 | -115,043 | 42.3 |
| all | const 20% | 2.03 | 4.07 | 10.82 | -75,813 | -67,606 | 231,306 | -87,036 | 42.3 |
| all | const 30% | 2.07 | 4.15 | 11.66 | -75,919 | -63,991 | 206,905 | -91,775 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.111 / -0.138 / +0.456
- [FAIL] 3 worst week within share: all-in worst week +24.3% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.14 vs p95 -0.46 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.048, +0.346]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 67% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.008 / -0.258 / +0.364
- [FAIL] 6 worst-decile corr <=+0.30: +0.36
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ1_ES); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2913 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 5768 | +0.0966 | 2.00 |
| fixed | 5768 | +0.0617 | 1.28 |
| scaled | 5768 | +0.0617 | 1.28 |

Plateau neighbours (all-in 20% uplift; selected +0.151):
- {'sym': 'ES', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.259 (trades 3191)
- {'sym': 'ES', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.188 (trades 3090)
- {'sym': 'ES', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: +0.088 (trades 2909)
- {'sym': 'ES', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: +0.109 (trades 2632)
- {'sym': 'ES', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.126 (trades 2814)
- {'sym': 'ES', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.191 (trades 2899)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.31, p95 -0.46, real 1.14. Standalone Sharpe at 2x slippage 0.64.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 225 | -1 | -0.08 |
| 2014 | 292 | 36 | 1.97 |
| 2015 | 497 | 22 | 1.06 |
| 2016 | 477 | -20 | -1.05 |
| 2017 | 213 | -0 | -0.00 |
| 2018 | 669 | 39 | 1.70 |
| 2019 | 608 | 35 | 1.26 |
| 2020 | 915 | 57 | 1.32 |
| 2021 | 848 | 93 | 2.42 |
| 2022 | 1024 | 94 | 2.40 |
| 2023 | 870 | 19 | 0.57 |
| 2024 | 839 | 39 | 1.08 |
| 2025 | 937 | 8 | 0.20 |
| 2026 | 774 | 74 | 2.20 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 1656 | -0.063 | 0.026 |
| 2013-22 | mid | 1882 | +0.038 | 0.026 |
| 2013-22 | high | 2229 | +0.174 | 0.027 |
| 2023-26 | low | 841 | -0.078 | 0.041 |
| 2023-26 | mid | 1036 | +0.078 | 0.040 |
| 2023-26 | high | 1036 | +0.118 | 0.042 |

DONE RZ1_ES