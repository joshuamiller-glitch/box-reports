# REPORT RZ1_YM
**Verdict: NO** (4/7 measured gates pass). Selected cell setup=FVG, tf=30, thr=0.25; additive @20% clean/H1/H2 +0.19/-0.31/+0.81; standalone all-in weekly Sharpe 1.19 (2013-26 0.87, dev 2013-22 0.88); pair-window trades 1806. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RZ1 YM: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |      net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|---------:|-------:|:-----------|
| YM    | FVG     |   30 | 0.250 | 1123 |    1.195 |   60.281 |      3 | True       |
| YM    | FVG     |   15 | 0.250 | 2090 |    0.781 |   66.436 |      2 | True       |
| YM    | FVG     |   15 | 0.500 | 1314 |    0.133 |    9.046 |      1 | True       |
| YM    | FVG     |   30 | 0.500 |  601 |   -0.146 |   -5.907 |      2 | True       |
| YM    | DISP    |   30 | 2.000 |  383 |   -0.853 |  -31.971 |      1 | True       |
| YM    | DISP    |   30 | 1.500 |  792 |   -0.944 |  -53.945 |      1 | True       |
| YM    | DISP    |   15 | 1.500 | 1545 |   -1.300 | -100.110 |      0 | True       |
| YM    | DISP    |   15 | 2.000 |  762 |   -2.007 | -119.117 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.19; replicate best-eligible median 0.25, p95 0.74; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.805e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.102 | -0.130 | +0.411 | +0.126 | +8.5 | [+0.030, +0.232] | 0.86 | NO |
| 20% | add | +0.187 | -0.307 | +0.813 | +0.231 | +22.9 | [+0.040, +0.443] | 0.86 | NO |
| 30% | add | +0.253 | -0.531 | +1.198 | +0.313 | +37.2 | [+0.026, +0.621] | 0.86 | NO |
| 50% | add | +0.337 | -1.092 | +1.877 | +0.407 | +65.9 | [-0.048, +0.891] | 0.86 | NO |
| 10% | const | +0.113 | -0.147 | +0.456 | +0.139 | -0.9 | [+0.032, +0.257] | 0.86 | NO |
| 20% | const | +0.222 | -0.413 | +1.009 | +0.275 | +4.0 | [+0.036, +0.537] | 0.86 | NO |
| 30% | const | +0.314 | -0.879 | +1.651 | +0.383 | +9.0 | [-0.018, +0.808] | 0.86 | NO |
| 50% | const | +0.363 | -2.517 | +2.875 | +0.378 | +18.9 | [-0.383, +1.151] | 0.86 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,088,315, Sharpe 1.19, maxDD 397,513, worst wk -134,193; H1: net -517,975, Sharpe -2.14, maxDD 629,336, worst wk -121,273; H2: net 1,192,556, Sharpe 4.16, maxDD 182,338, worst wk -116,019; all: net 1,762,896, Sharpe 1.19, maxDD 645,362, worst wk -134,193
Correlation with pair (weekly): clean +0.06, H1 -0.42, H2 -0.26, all -0.07; worst-decile weeks (n=17) corr -0.02, sleeve mean in those weeks $19,100, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.65 | 3.25 | 5.40 | -87,235 | -82,414 | 286,522 | -101,410 | 44.8 |
| clean | add 30% | 1.71 | 3.42 | 5.60 | -92,245 | -85,081 | 295,604 | -113,256 | 47.6 |
| clean | const 20% | 1.68 | 3.35 | 5.52 | -71,770 | -66,998 | 232,057 | -85,866 | 46.7 |
| clean | const 30% | 1.77 | 3.57 | 5.51 | -69,130 | -62,941 | 228,229 | -89,940 | 48.6 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.52 | 5.20 | 3.15 | -63,821 | -59,385 | 155,435 | -69,024 | 42.9 |
| H1 | add 30% | 2.30 | 4.46 | 2.79 | -59,614 | -56,229 | 157,296 | -64,392 | 39.3 |
| H1 | const 20% | 2.41 | 4.84 | 2.97 | -48,299 | -46,246 | 125,092 | -53,366 | 42.9 |
| H1 | const 30% | 1.95 | 3.48 | 2.20 | -43,377 | -42,553 | 118,462 | -44,479 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 3.11 | 7.29 | 5.41 | -83,231 | -70,471 | 184,682 | -87,348 | 36.1 |
| H2 | add 30% | 3.49 | 8.71 | 5.99 | -84,302 | -68,947 | 186,879 | -89,760 | 33.3 |
| H2 | const 20% | 3.30 | 8.00 | 5.70 | -67,014 | -55,767 | 148,624 | -70,843 | 36.1 |
| H2 | const 30% | 3.95 | 10.50 | 6.64 | -59,976 | -46,891 | 134,096 | -65,002 | 33.3 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.09 | 4.28 | 10.60 | -85,683 | -78,218 | 286,522 | -101,410 | 42.9 |
| all | add 30% | 2.17 | 4.50 | 10.87 | -89,690 | -78,959 | 295,604 | -113,256 | 43.5 |
| all | const 20% | 2.13 | 4.40 | 10.78 | -70,149 | -62,839 | 232,057 | -85,866 | 44.0 |
| all | const 30% | 2.24 | 4.67 | 10.55 | -66,389 | -57,696 | 228,229 | -89,940 | 44.0 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.187 / -0.307 / +0.813
- [FAIL] 3 worst week within share: all-in worst week +22.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.19 vs p95 -0.05 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.040, +0.443]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.128 / -0.378 / +0.776
- [PASS] 6 worst-decile corr <=+0.30: -0.02
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ1_YM); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1806 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 5476 | +0.0842 | 1.66 |
| fixed | 5476 | +0.0452 | 0.88 |
| scaled | 5476 | +0.0452 | 0.88 |

Plateau neighbours (all-in 20% uplift; selected +0.231):
- {'sym': 'YM', 'setup': 'FVG', 'tf': '30', 'thr': '0.188'}: +0.297 (trades 2040)
- {'sym': 'YM', 'setup': 'FVG', 'tf': '30', 'thr': '0.25', 'R': '1.5'}: +0.242 (trades 1866)
- {'sym': 'YM', 'setup': 'FVG', 'tf': '30', 'thr': '0.25', 'L': '15'}: +0.223 (trades 1805)
- {'sym': 'YM', 'setup': 'FVG', 'tf': '30', 'thr': '0.312'}: +0.199 (trades 1549)
- {'sym': 'YM', 'setup': 'FVG', 'tf': '30', 'thr': '0.25', 'R': '2.5'}: +0.243 (trades 1775)
- {'sym': 'YM', 'setup': 'FVG', 'tf': '30', 'thr': '0.25', 'L': '25'}: +0.257 (trades 1793)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.93, p95 -0.05, real 1.19. Standalone Sharpe at 2x slippage 0.91.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 508 | -6 | -0.26 |
| 2014 | 515 | -15 | -0.47 |
| 2015 | 563 | 46 | 1.58 |
| 2016 | 515 | 31 | 1.19 |
| 2017 | 470 | -28 | -1.33 |
| 2018 | 591 | 40 | 1.20 |
| 2019 | 544 | 28 | 0.96 |
| 2020 | 583 | 33 | 1.24 |
| 2021 | 593 | 70 | 2.05 |
| 2022 | 594 | 47 | 1.89 |
| 2023 | 576 | -9 | -0.41 |
| 2024 | 541 | 41 | 1.54 |
| 2025 | 562 | -14 | -0.53 |
| 2026 | 445 | 63 | 3.35 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 1711 | -0.063 | 0.027 |
| 2013-22 | mid | 1887 | +0.003 | 0.028 |
| 2013-22 | high | 1865 | +0.188 | 0.030 |
| 2023-26 | low | 504 | +0.001 | 0.055 |
| 2023-26 | mid | 653 | +0.018 | 0.049 |
| 2023-26 | high | 649 | +0.131 | 0.050 |

DONE RZ1_YM