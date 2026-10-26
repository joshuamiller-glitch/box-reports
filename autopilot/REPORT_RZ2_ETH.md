# REPORT RZ2_ETH
**Verdict: NO** (4/7 measured gates pass). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.36/+0.45/+0.07; standalone all-in weekly Sharpe 1.72 (2013-26 1.41, dev 2013-22 1.37); pair-window trades 3878. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RZ2 ETH: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |      net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|---------:|-------:|:-----------|
| ETH   | FVG     |   15 | 0.250 | 2460 |    2.036 |  168.501 |      3 | True       |
| ETH   | FVG     |   30 | 0.250 | 1250 |    0.757 |   48.664 |      3 | True       |
| ETH   | FVG     |   15 | 0.500 | 1895 |    0.343 |   32.385 |      3 | True       |
| ETH   | DISP    |   30 | 2.000 |  358 |    0.083 |    3.022 |      2 | True       |
| ETH   | DISP    |   30 | 1.500 |  740 |   -0.262 |  -13.704 |      1 | True       |
| ETH   | FVG     |   30 | 0.500 |  896 |   -0.429 |  -20.800 |      0 | True       |
| ETH   | DISP    |   15 | 2.000 |  662 |   -0.779 |  -33.498 |      1 | True       |
| ETH   | DISP    |   15 | 1.500 | 1432 |   -1.683 | -116.671 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 2.04; replicate best-eligible median -0.98, p95 0.24; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.101e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.191 | +0.259 | +0.054 | +0.174 | -0.8 | [+0.073, +0.275] | 0.40 | NO |
| 20% | add | +0.363 | +0.449 | +0.075 | +0.319 | +4.7 | [+0.119, +0.520] | 0.40 | NO |
| 30% | add | +0.511 | +0.577 | +0.063 | +0.435 | +10.3 | [+0.142, +0.730] | 0.40 | NO |
| 50% | add | +0.736 | +0.696 | -0.035 | +0.582 | +23.4 | [+0.128, +1.037] | 0.40 | NO |
| 10% | const | +0.212 | +0.283 | +0.058 | +0.191 | -10.2 | [+0.079, +0.303] | 0.40 | NO |
| 20% | const | +0.440 | +0.520 | +0.073 | +0.381 | -14.0 | [+0.134, +0.629] | 0.40 | NO |
| 30% | const | +0.666 | +0.670 | +0.009 | +0.541 | -17.8 | [+0.143, +0.944] | 0.40 | INSURANCE |
| 50% | const | +0.983 | +0.636 | -0.439 | +0.641 | -13.1 | [-0.090, +1.363] | 0.40 | INSURANCE |

Standalone at 100% pair-equivalent risk ($): clean: net 1,854,504, Sharpe 2.04, maxDD 363,077, worst wk -126,984; H1: net 742,405, Sharpe 2.53, maxDD 238,974, worst wk -134,729; H2: net 151,541, Sharpe 0.39, maxDD 438,512, worst wk -172,755; all: net 2,748,450, Sharpe 1.72, maxDD 438,512, worst wk -172,755
Correlation with pair (weekly): clean +0.02, H1 +0.15, H2 -0.09, all +0.02; worst-decile weeks (n=17) corr -0.19, sleeve mean in those weeks $42,161, positive share 0.71.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.82 | 3.71 | 6.89 | -83,478 | -78,117 | 246,698 | -86,421 | 41.9 |
| clean | add 30% | 1.97 | 4.10 | 7.13 | -86,967 | -78,618 | 264,566 | -91,002 | 39.0 |
| clean | const 20% | 1.90 | 3.91 | 7.19 | -68,178 | -62,694 | 199,552 | -70,969 | 39.0 |
| clean | const 30% | 2.13 | 4.50 | 7.00 | -64,018 | -55,484 | 212,423 | -67,825 | 38.1 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.28 | 8.22 | 5.33 | -67,429 | -60,574 | 139,149 | -77,871 | 39.3 |
| H1 | add 30% | 3.41 | 8.83 | 5.83 | -71,192 | -58,399 | 140,021 | -78,341 | 35.7 |
| H1 | const 20% | 3.35 | 8.58 | 5.59 | -55,448 | -47,368 | 111,622 | -62,485 | 39.3 |
| H1 | const 30% | 3.50 | 9.09 | 5.74 | -53,222 | -45,869 | 111,187 | -55,261 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.37 | 4.90 | 3.83 | -76,985 | -76,541 | 206,564 | -77,118 | 41.7 |
| H2 | add 30% | 2.36 | 4.94 | 3.93 | -80,547 | -77,649 | 205,083 | -85,178 | 41.7 |
| H2 | const 20% | 2.37 | 4.93 | 3.88 | -62,873 | -61,676 | 164,659 | -64,812 | 41.7 |
| H2 | const 30% | 2.30 | 4.93 | 4.06 | -59,904 | -55,352 | 142,415 | -67,116 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.17 | 4.54 | 13.11 | -81,600 | -77,111 | 246,698 | -86,421 | 41.7 |
| all | add 30% | 2.29 | 4.89 | 13.27 | -84,963 | -77,516 | 264,566 | -91,002 | 39.3 |
| all | const 20% | 2.24 | 4.73 | 13.52 | -66,613 | -61,792 | 199,552 | -70,969 | 39.9 |
| all | const 30% | 2.40 | 5.22 | 12.73 | -62,527 | -55,515 | 212,423 | -67,825 | 38.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.363 / +0.449 / +0.075
- [PASS] 3 worst week within share: all-in worst week +4.7% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.72 vs p95 -2.24 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.119, +0.520]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 67% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.282 / +0.386 / -0.024
- [PASS] 6 worst-decile corr <=+0.30: -0.19
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ2_ETH); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3878 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1200 | +0.0818 | 1.91 |
| fixed | 1200 | +0.0596 | 1.37 |
| scaled | 1200 | +0.0596 | 1.37 |

Plateau neighbours (all-in 20% uplift; selected +0.319):
- {'sym': 'ETH', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.376 (trades 4079)
- {'sym': 'ETH', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.163 (trades 4180)
- {'sym': 'ETH', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: +0.277 (trades 4001)
- {'sym': 'ETH', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: +0.216 (trades 3684)
- {'sym': 'ETH', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.454 (trades 3647)
- {'sym': 'ETH', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.305 (trades 3787)

Own random-entry null: 300 draws, standalone all-in Sharpe median -3.15, p95 -2.24, real 1.72. Standalone Sharpe at 2x slippage 1.32.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2022 | 1200 | 72 | 1.37 |
| 2023 | 1019 | 9 | 0.22 |
| 2024 | 1309 | 87 | 1.86 |
| 2025 | 1215 | 121 | 2.73 |
| 2026 | 930 | 29 | 0.73 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 456 | -0.042 | 0.063 |
| 2013-22 | mid | 355 | +0.011 | 0.074 |
| 2013-22 | high | 342 | +0.205 | 0.077 |
| 2023-26 | low | 1254 | -0.061 | 0.038 |
| 2023-26 | mid | 1296 | +0.105 | 0.039 |
| 2023-26 | high | 1328 | +0.143 | 0.038 |

DONE RZ2_ETH