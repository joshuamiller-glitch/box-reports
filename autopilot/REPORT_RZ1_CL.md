# REPORT RZ1_CL
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.41/+0.36/+0.52; standalone all-in weekly Sharpe 2.34 (2013-26 1.40, dev 2013-22 1.04); pair-window trades 2992. Runtime 0.2 min (+selection 0.0 min). 10-worker pool.

RZ1 CL: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |     net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|--------:|-------:|:-----------|
| CL    | FVG     |   15 | 0.250 | 1831 |    2.272 | 159.620 |      3 | True       |
| CL    | FVG     |   30 | 0.250 | 1097 |    1.188 |  68.029 |      3 | True       |
| CL    | FVG     |   15 | 0.500 | 1262 |    0.571 |  36.645 |      2 | True       |
| CL    | DISP    |   30 | 1.500 |  829 |    0.322 |  15.405 |      1 | True       |
| CL    | FVG     |   30 | 0.500 |  662 |    0.062 |   2.713 |      2 | True       |
| CL    | DISP    |   30 | 2.000 |  383 |   -0.329 | -10.185 |      1 | True       |
| CL    | DISP    |   15 | 1.500 | 1378 |   -0.462 | -34.732 |      2 | True       |
| CL    | DISP    |   15 | 2.000 |  694 |   -0.515 | -26.254 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 2.27; replicate best-eligible median -0.02, p95 0.98; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.297e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.214 | +0.219 | +0.278 | +0.232 | +3.8 | [+0.135, +0.338] | 0.25 | NO |
| 20% | add | +0.407 | +0.363 | +0.522 | +0.433 | +10.6 | [+0.244, +0.642] | 0.25 | NO |
| 30% | add | +0.576 | +0.436 | +0.727 | +0.601 | +18.5 | [+0.323, +0.907] | 0.25 | NO |
| 50% | add | +0.836 | +0.433 | +1.029 | +0.841 | +34.7 | [+0.414, +1.321] | 0.25 | NO |
| 10% | const | +0.237 | +0.239 | +0.307 | +0.255 | -6.1 | [+0.149, +0.373] | 0.25 | NO |
| 20% | const | +0.495 | +0.407 | +0.629 | +0.521 | -8.4 | [+0.287, +0.778] | 0.25 | NO |
| 30% | const | +0.755 | +0.451 | +0.936 | +0.769 | -9.8 | [+0.391, +1.189] | 0.25 | NO |
| 50% | const | +1.143 | +0.134 | +1.340 | +1.058 | -1.8 | [+0.385, +1.814] | 0.25 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 2,069,980, Sharpe 2.27, maxDD 321,481, worst wk -136,324; H1: net 556,813, Sharpe 1.73, maxDD 347,765, worst wk -106,083; H2: net 1,042,010, Sharpe 3.05, maxDD 303,741, worst wk -92,320; all: net 3,668,803, Sharpe 2.34, maxDD 356,067, worst wk -136,324
Correlation with pair (weekly): clean +0.03, H1 +0.02, H2 +0.08, all +0.04; worst-decile weeks (n=17) corr +0.05, sleeve mean in those weeks $7,236, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.87 | 3.68 | 7.00 | -86,181 | -80,873 | 249,053 | -90,707 | 40.0 |
| clean | add 30% | 2.04 | 4.08 | 7.54 | -90,014 | -82,335 | 258,792 | -97,531 | 39.0 |
| clean | const 20% | 1.95 | 3.89 | 7.49 | -70,478 | -65,283 | 197,423 | -75,295 | 40.0 |
| clean | const 30% | 2.21 | 4.53 | 7.65 | -66,620 | -60,297 | 202,780 | -74,413 | 41.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.19 | 7.63 | 3.99 | -72,699 | -61,674 | 176,933 | -91,271 | 39.3 |
| H1 | add 30% | 3.26 | 7.79 | 4.01 | -79,010 | -68,182 | 189,543 | -97,762 | 39.3 |
| H1 | const 20% | 3.23 | 7.76 | 4.00 | -60,684 | -51,942 | 146,590 | -75,613 | 39.3 |
| H1 | const 30% | 3.28 | 7.62 | 4.05 | -60,986 | -53,585 | 144,029 | -74,276 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.82 | 6.46 | 4.70 | -80,498 | -74,491 | 206,387 | -86,227 | 38.9 |
| H2 | add 30% | 3.02 | 7.31 | 5.30 | -86,757 | -74,749 | 202,634 | -89,514 | 38.9 |
| H2 | const 20% | 2.92 | 6.89 | 5.01 | -66,902 | -59,696 | 163,026 | -70,296 | 36.1 |
| H2 | const 30% | 3.23 | 8.28 | 5.83 | -66,364 | -52,556 | 144,954 | -67,110 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.29 | 4.76 | 13.73 | -85,992 | -79,172 | 249,053 | -91,271 | 39.9 |
| all | add 30% | 2.46 | 5.23 | 14.63 | -90,151 | -81,049 | 258,792 | -97,762 | 39.3 |
| all | const 20% | 2.38 | 5.01 | 14.60 | -70,302 | -63,974 | 197,423 | -75,613 | 39.3 |
| all | const 30% | 2.62 | 5.72 | 14.70 | -67,414 | -59,382 | 202,780 | -74,413 | 39.3 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.407 / +0.363 / +0.522
- [PASS] 3 worst week within share: all-in worst week +10.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 2.34 vs p95 -0.86 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.244, +0.642]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 83% of 6
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.292 / +0.233 / +0.441
- [PASS] 6 worst-decile corr <=+0.30: +0.05
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ1_CL); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2992 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 7894 | +0.0823 | 1.87 |
| fixed | 7894 | +0.0460 | 1.04 |
| scaled | 7894 | +0.0460 | 1.04 |

Plateau neighbours (all-in 20% uplift; selected +0.433):
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.539 (trades 3231)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.336 (trades 3202)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: +0.348 (trades 3008)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: +0.270 (trades 2741)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.352 (trades 2856)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.491 (trades 2975)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.63, p95 -0.86, real 2.34. Standalone Sharpe at 2x slippage 1.80.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 731 | 113 | 3.24 |
| 2014 | 698 | 84 | 2.61 |
| 2015 | 768 | 90 | 2.91 |
| 2016 | 806 | -8 | -0.31 |
| 2017 | 547 | -24 | -1.00 |
| 2018 | 760 | -0 | -0.01 |
| 2019 | 738 | -16 | -0.59 |
| 2020 | 839 | 33 | 0.78 |
| 2021 | 908 | 37 | 1.01 |
| 2022 | 1099 | 56 | 1.11 |
| 2023 | 947 | 107 | 2.89 |
| 2024 | 899 | 96 | 2.57 |
| 2025 | 867 | 14 | 0.42 |
| 2026 | 827 | 115 | 3.44 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 2449 | -0.105 | 0.023 |
| 2013-22 | mid | 2661 | +0.008 | 0.024 |
| 2013-22 | high | 2763 | +0.215 | 0.025 |
| 2023-26 | low | 976 | -0.045 | 0.038 |
| 2023-26 | mid | 985 | +0.095 | 0.041 |
| 2023-26 | high | 1031 | +0.226 | 0.042 |

DONE RZ1_CL