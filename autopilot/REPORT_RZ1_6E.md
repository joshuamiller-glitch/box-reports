# REPORT RZ1_6E
**Verdict: NO** (2/7 measured gates pass). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.12/-0.15/+0.07; standalone all-in weekly Sharpe 0.70 (2013-26 -0.20, dev 2013-22 -0.39); pair-window trades 2277. Runtime 0.3 min (+selection 0.0 min). 10-worker pool.

RZ1 6E: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |     net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|--------:|-------:|:-----------|
| 6E    | FVG     |   15 | 0.250 | 1431 |    0.772 |  46.614 |      3 | True       |
| 6E    | FVG     |   30 | 0.250 |  962 |    0.224 |  11.861 |      2 | True       |
| 6E    | DISP    |   15 | 1.500 | 1009 |   -0.008 |  -0.491 |      1 | True       |
| 6E    | FVG     |   15 | 0.500 |  974 |   -0.101 |  -5.600 |      2 | True       |
| 6E    | DISP    |   15 | 2.000 |  503 |   -0.133 |  -5.688 |      2 | True       |
| 6E    | FVG     |   30 | 0.500 |  580 |   -0.354 | -13.492 |      2 | True       |
| 6E    | DISP    |   30 | 1.500 |  658 |   -0.671 | -26.510 |      1 | True       |
| 6E    | DISP    |   30 | 2.000 |  293 |   -0.765 | -20.716 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.77; replicate best-eligible median -0.23, p95 0.93; real beats 90% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.509e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.067 | -0.061 | +0.041 | +0.046 | +8.6 | [-0.047, +0.136] | 0.22 | NO |
| 20% | add | +0.119 | -0.146 | +0.068 | +0.074 | +23.1 | [-0.111, +0.254] | 0.22 | NO |
| 30% | add | +0.154 | -0.248 | +0.083 | +0.086 | +37.6 | [-0.187, +0.355] | 0.22 | NO |
| 50% | add | +0.182 | -0.486 | +0.083 | +0.070 | +70.4 | [-0.358, +0.497] | 0.22 | NO |
| 10% | const | +0.074 | -0.069 | +0.045 | +0.049 | -0.8 | [-0.054, +0.150] | 0.22 | NO |
| 20% | const | +0.138 | -0.195 | +0.077 | +0.082 | +4.3 | [-0.149, +0.307] | 0.22 | NO |
| 30% | const | +0.178 | -0.398 | +0.087 | +0.081 | +9.5 | [-0.295, +0.455] | 0.22 | NO |
| 50% | const | +0.107 | -1.074 | -0.017 | -0.088 | +33.9 | [-0.781, +0.626] | 0.22 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 703,621, Sharpe 0.77, maxDD 452,400, worst wk -158,048; H1: net -47,637, Sharpe -0.22, maxDD 383,019, worst wk -151,300; H2: net 299,444, Sharpe 1.16, maxDD 236,481, worst wk -160,771; all: net 955,429, Sharpe 0.70, maxDD 490,214, worst wk -160,771
Correlation with pair (weekly): clean +0.01, H1 +0.09, H2 +0.23, all +0.07; worst-decile weeks (n=17) corr -0.10, sleeve mean in those weeks $18,696, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.58 | 3.06 | 5.33 | -88,989 | -81,403 | 275,877 | -101,604 | 41.0 |
| clean | add 30% | 1.61 | 3.12 | 5.63 | -94,552 | -83,805 | 273,761 | -113,547 | 40.0 |
| clean | const 20% | 1.60 | 3.10 | 5.48 | -73,416 | -65,880 | 219,855 | -86,061 | 41.0 |
| clean | const 30% | 1.64 | 3.13 | 6.02 | -72,261 | -62,202 | 189,728 | -90,231 | 39.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.68 | 6.18 | 3.85 | -71,940 | -63,257 | 151,764 | -73,213 | 46.4 |
| H1 | add 30% | 2.58 | 6.05 | 3.71 | -69,104 | -62,038 | 156,127 | -71,353 | 46.4 |
| H1 | const 20% | 2.63 | 6.13 | 3.79 | -56,418 | -50,118 | 122,742 | -57,827 | 46.4 |
| H1 | const 30% | 2.43 | 5.71 | 3.52 | -45,940 | -45,083 | 114,149 | -48,274 | 46.4 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.36 | 4.99 | 3.83 | -87,405 | -79,180 | 214,252 | -92,359 | 44.4 |
| H2 | add 30% | 2.38 | 5.02 | 3.98 | -96,770 | -83,546 | 213,666 | -108,436 | 44.4 |
| H2 | const 20% | 2.37 | 5.02 | 3.92 | -73,670 | -64,903 | 170,767 | -80,318 | 44.4 |
| H2 | const 30% | 2.38 | 4.98 | 3.86 | -76,168 | -62,832 | 161,211 | -90,374 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.93 | 3.88 | 10.43 | -87,052 | -79,766 | 275,877 | -101,604 | 42.9 |
| all | add 30% | 1.94 | 3.91 | 10.85 | -92,712 | -82,014 | 273,761 | -113,547 | 42.3 |
| all | const 20% | 1.94 | 3.90 | 10.64 | -71,906 | -64,537 | 219,855 | -86,061 | 42.9 |
| all | const 30% | 1.94 | 3.86 | 11.42 | -71,437 | -60,592 | 189,728 | -90,374 | 41.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.119 / -0.146 / +0.068
- [FAIL] 3 worst week within share: all-in worst week +23.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.70 vs p95 -1.24 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.111, +0.254]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 67% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.006 / -0.298 / -0.043
- [PASS] 6 worst-decile corr <=+0.30: -0.10
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ1_6E); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2277 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 7380 | +0.0298 | 0.70 |
| fixed | 7380 | -0.0170 | -0.39 |
| scaled | 7380 | -0.0170 | -0.39 |

Plateau neighbours (all-in 20% uplift; selected +0.074):
- {'sym': '6E', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.090 (trades 2464)
- {'sym': '6E', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.063 (trades 2433)
- {'sym': '6E', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: -0.009 (trades 2284)
- {'sym': '6E', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: -0.003 (trades 2105)
- {'sym': '6E', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.136 (trades 2215)
- {'sym': '6E', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.113 (trades 2270)

Own random-entry null: 300 draws, standalone all-in Sharpe median -2.16, p95 -1.24, real 0.70. Standalone Sharpe at 2x slippage 0.01.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 683 | -48 | -1.36 |
| 2014 | 566 | -106 | -3.65 |
| 2015 | 776 | 7 | 0.20 |
| 2016 | 819 | 21 | 0.87 |
| 2017 | 793 | -75 | -2.10 |
| 2018 | 835 | 74 | 2.37 |
| 2019 | 554 | -39 | -1.73 |
| 2020 | 810 | 16 | 0.51 |
| 2021 | 664 | -5 | -0.20 |
| 2022 | 880 | 30 | 0.75 |
| 2023 | 765 | -6 | -0.19 |
| 2024 | 627 | 24 | 0.77 |
| 2025 | 803 | 2 | 0.09 |
| 2026 | 524 | 20 | 1.04 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 2331 | -0.151 | 0.022 |
| 2013-22 | mid | 2453 | -0.018 | 0.024 |
| 2013-22 | high | 2566 | +0.105 | 0.025 |
| 2023-26 | low | 733 | -0.157 | 0.034 |
| 2023-26 | mid | 744 | +0.040 | 0.042 |
| 2023-26 | high | 800 | +0.185 | 0.043 |

DONE RZ1_6E