# REPORT RZ1_GC
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.46/+0.75/+0.36; standalone all-in weekly Sharpe 2.61 (2013-26 0.89, dev 2013-22 0.33); pair-window trades 3228. Runtime 0.2 min (+selection 0.0 min). 10-worker pool.

RZ1 GC: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |     net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|--------:|-------:|:-----------|
| GC    | FVG     |   15 | 0.250 | 1980 |    2.591 | 218.016 |      3 | True       |
| GC    | FVG     |   30 | 0.250 | 1062 |    2.127 | 107.208 |      3 | True       |
| GC    | FVG     |   15 | 0.500 | 1254 |    1.055 |  72.246 |      3 | True       |
| GC    | DISP    |   15 | 2.000 |  564 |    0.540 |  24.996 |      1 | True       |
| GC    | FVG     |   30 | 0.500 |  622 |    0.203 |   8.676 |      2 | True       |
| GC    | DISP    |   30 | 1.500 |  687 |   -0.443 | -20.514 |      1 | True       |
| GC    | DISP    |   15 | 1.500 | 1360 |   -0.487 | -30.260 |      1 | True       |
| GC    | DISP    |   30 | 2.000 |  301 |   -1.043 | -29.355 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 2.59; replicate best-eligible median 0.17, p95 0.61; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.083e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.240 | +0.378 | +0.189 | +0.238 | +4.3 | [+0.155, +0.334] | 0.47 | NO |
| 20% | add | +0.458 | +0.755 | +0.360 | +0.453 | +11.9 | [+0.288, +0.645] | 0.47 | NO |
| 30% | add | +0.648 | +1.111 | +0.511 | +0.642 | +19.5 | [+0.399, +0.925] | 0.47 | NO |
| 50% | add | +0.947 | +1.686 | +0.759 | +0.936 | +34.6 | [+0.552, +1.386] | 0.47 | NO |
| 10% | const | +0.266 | +0.421 | +0.209 | +0.263 | -5.3 | [+0.171, +0.370] | 0.47 | NO |
| 20% | const | +0.556 | +0.937 | +0.438 | +0.551 | -7.4 | [+0.346, +0.787] | 0.47 | NO |
| 30% | const | +0.852 | +1.507 | +0.679 | +0.844 | -9.6 | [+0.506, +1.235] | 0.47 | INSURANCE |
| 50% | const | +1.322 | +2.021 | +1.109 | +1.281 | -13.8 | [+0.644, +2.028] | 0.47 | INSURANCE |

Standalone at 100% pair-equivalent risk ($): clean: net 2,360,491, Sharpe 2.59, maxDD 192,024, worst wk -140,227; H1: net 487,662, Sharpe 2.18, maxDD 159,404, worst wk -70,792; H2: net 743,335, Sharpe 3.03, maxDD 201,468, worst wk -91,430; all: net 3,591,488, Sharpe 2.61, maxDD 201,468, worst wk -140,227
Correlation with pair (weekly): clean +0.06, H1 -0.47, H2 +0.16, all +0.00; worst-decile weeks (n=17) corr +0.27, sleeve mean in those weeks $22,236, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.92 | 3.97 | 7.30 | -86,081 | -77,911 | 246,989 | -92,357 | 41.9 |
| clean | add 30% | 2.11 | 4.53 | 8.27 | -89,821 | -78,457 | 246,537 | -98,602 | 41.9 |
| clean | const 20% | 2.02 | 4.26 | 7.78 | -70,361 | -62,547 | 197,410 | -76,383 | 42.9 |
| clean | const 30% | 2.31 | 5.15 | 9.42 | -66,241 | -55,411 | 173,971 | -74,641 | 39.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.58 | 8.67 | 4.44 | -64,006 | -56,619 | 155,577 | -70,642 | 35.7 |
| H1 | add 30% | 3.94 | 9.97 | 4.70 | -57,204 | -52,081 | 157,509 | -67,497 | 28.6 |
| H1 | const 20% | 3.76 | 9.32 | 4.57 | -48,484 | -43,480 | 125,234 | -55,256 | 28.6 |
| H1 | const 30% | 4.34 | 11.64 | 5.02 | -36,845 | -32,372 | 111,995 | -44,417 | 25.0 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.66 | 5.71 | 4.36 | -77,018 | -73,382 | 208,648 | -80,421 | 38.9 |
| H2 | add 30% | 2.81 | 6.18 | 4.82 | -75,908 | -72,695 | 204,259 | -79,370 | 41.7 |
| H2 | const 20% | 2.73 | 5.95 | 4.59 | -61,051 | -58,373 | 165,163 | -63,917 | 41.7 |
| H2 | const 30% | 2.97 | 6.73 | 5.44 | -54,499 | -51,118 | 139,032 | -54,613 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.31 | 4.88 | 13.78 | -83,176 | -75,856 | 246,989 | -92,357 | 40.5 |
| all | add 30% | 2.50 | 5.46 | 15.26 | -85,472 | -75,816 | 246,537 | -98,602 | 39.9 |
| all | const 20% | 2.41 | 5.18 | 14.52 | -67,433 | -60,575 | 197,410 | -76,383 | 40.5 |
| all | const 30% | 2.70 | 6.10 | 17.00 | -62,421 | -53,377 | 173,971 | -74,641 | 37.5 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.458 / +0.755 / +0.360
- [PASS] 3 worst week within share: all-in worst week +11.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 2.61 vs p95 -0.10 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.288, +0.645]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 83% of 6
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.376 / +0.700 / +0.328
- [PASS] 6 worst-decile corr <=+0.30: +0.27
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ1_GC); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3228 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 8288 | +0.0506 | 1.28 |
| fixed | 8288 | +0.0131 | 0.33 |
| scaled | 8288 | +0.0131 | 0.33 |

Plateau neighbours (all-in 20% uplift; selected +0.453):
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.564 (trades 3605)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.420 (trades 3416)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: +0.314 (trades 3204)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: +0.392 (trades 2894)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.628 (trades 3087)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.411 (trades 3199)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.08, p95 -0.10, real 2.61. Standalone Sharpe at 2x slippage 2.24.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 887 | 6 | 0.16 |
| 2014 | 746 | -27 | -0.80 |
| 2015 | 771 | 53 | 2.03 |
| 2016 | 846 | 13 | 0.42 |
| 2017 | 706 | 23 | 1.00 |
| 2018 | 724 | -18 | -0.65 |
| 2019 | 771 | -1 | -0.03 |
| 2020 | 964 | 56 | 1.34 |
| 2021 | 920 | 6 | 0.14 |
| 2022 | 953 | -1 | -0.03 |
| 2023 | 904 | 21 | 0.63 |
| 2024 | 1010 | 77 | 1.78 |
| 2025 | 1070 | 153 | 3.49 |
| 2026 | 798 | 73 | 2.62 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 2645 | -0.122 | 0.021 |
| 2013-22 | mid | 2798 | -0.031 | 0.022 |
| 2013-22 | high | 2813 | +0.179 | 0.024 |
| 2023-26 | low | 996 | -0.059 | 0.040 |
| 2023-26 | mid | 1148 | +0.126 | 0.039 |
| 2023-26 | high | 1084 | +0.227 | 0.042 |

DONE RZ1_GC