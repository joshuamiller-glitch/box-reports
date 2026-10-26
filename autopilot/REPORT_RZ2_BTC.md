# REPORT RZ2_BTC
**Verdict: LEAD** (5/7 measured gates pass). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.37/+0.30/+0.08; standalone all-in weekly Sharpe 1.73 (2013-26 1.57, dev 2013-22 1.67); pair-window trades 3816. Runtime 0.2 min (+selection 0.0 min). 10-worker pool.

RZ2 BTC: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |     net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|--------:|-------:|:-----------|
| BTC   | FVG     |   15 | 0.250 | 2306 |    2.243 | 217.670 |      3 | True       |
| BTC   | FVG     |   15 | 0.500 | 1657 |    0.851 |  74.836 |      3 | True       |
| BTC   | FVG     |   30 | 0.250 | 1188 |    0.312 |  18.762 |      2 | True       |
| BTC   | DISP    |   15 | 2.000 |  619 |    0.147 |   7.162 |      2 | True       |
| BTC   | DISP    |   30 | 2.000 |  341 |   -0.312 |  -9.420 |      1 | True       |
| BTC   | FVG     |   30 | 0.500 |  785 |   -0.386 | -19.094 |      2 | True       |
| BTC   | DISP    |   15 | 1.500 | 1372 |   -0.973 | -72.885 |      1 | True       |
| BTC   | DISP    |   30 | 1.500 |  696 |   -1.167 | -48.055 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 2.24; replicate best-eligible median -0.29, p95 0.46; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=9388)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.195 | +0.164 | +0.049 | +0.153 | +2.7 | [+0.062, +0.250] | 0.26 | NO |
| 20% | add | +0.367 | +0.297 | +0.075 | +0.282 | +12.1 | [+0.100, +0.473] | 0.26 | NO |
| 30% | add | +0.514 | +0.397 | +0.080 | +0.388 | +21.5 | [+0.117, +0.668] | 0.26 | NO |
| 50% | add | +0.739 | +0.494 | +0.035 | +0.530 | +40.3 | [+0.101, +0.985] | 0.26 | NO |
| 10% | const | +0.215 | +0.180 | +0.053 | +0.168 | -6.6 | [+0.068, +0.276] | 0.26 | NO |
| 20% | const | +0.444 | +0.352 | +0.080 | +0.338 | -6.5 | [+0.112, +0.575] | 0.26 | NO |
| 30% | const | +0.669 | +0.474 | +0.058 | +0.489 | -6.5 | [+0.114, +0.884] | 0.26 | NO |
| 50% | const | +1.005 | +0.333 | -0.238 | +0.619 | -5.7 | [-0.102, +1.369] | 0.26 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 2,043,548, Sharpe 2.24, maxDD 443,844, worst wk -171,947; H1: net 280,002, Sharpe 1.31, maxDD 178,375, worst wk -71,666; H2: net 178,092, Sharpe 0.55, maxDD 353,032, worst wk -200,418; all: net 2,501,641, Sharpe 1.73, maxDD 443,844, worst wk -200,418
Correlation with pair (weekly): clean +0.13, H1 -0.15, H2 -0.03, all +0.05; worst-decile weeks (n=17) corr -0.44, sleeve mean in those weeks $24,345, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.83 | 3.65 | 7.19 | -86,161 | -79,794 | 241,910 | -92,528 | 41.0 |
| clean | add 30% | 1.97 | 4.02 | 8.72 | -90,661 | -81,603 | 222,810 | -100,288 | 40.0 |
| clean | const 20% | 1.90 | 3.84 | 7.92 | -70,729 | -64,339 | 185,888 | -77,126 | 40.0 |
| clean | const 30% | 2.13 | 4.40 | 8.92 | -67,513 | -60,215 | 173,095 | -77,186 | 40.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.13 | 7.20 | 3.98 | -59,597 | -56,144 | 163,325 | -65,492 | 32.1 |
| H1 | add 30% | 3.22 | 7.49 | 4.01 | -59,694 | -55,658 | 169,131 | -59,772 | 32.1 |
| H1 | const 20% | 3.18 | 7.37 | 3.99 | -47,716 | -43,558 | 132,982 | -50,106 | 32.1 |
| H1 | const 30% | 3.30 | 7.55 | 4.04 | -43,362 | -41,139 | 123,617 | -47,056 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.37 | 5.19 | 3.48 | -79,116 | -72,191 | 228,976 | -84,314 | 44.4 |
| H2 | add 30% | 2.38 | 5.37 | 3.47 | -79,407 | -69,938 | 234,751 | -87,763 | 47.2 |
| H2 | const 20% | 2.38 | 5.29 | 3.48 | -63,409 | -56,619 | 185,491 | -68,831 | 44.4 |
| H2 | const 30% | 2.35 | 5.44 | 3.46 | -55,846 | -48,380 | 169,523 | -64,538 | 50.0 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.14 | 4.41 | 13.17 | -83,595 | -76,156 | 241,910 | -92,528 | 40.5 |
| all | add 30% | 2.24 | 4.72 | 14.63 | -86,788 | -76,504 | 234,751 | -100,288 | 40.5 |
| all | const 20% | 2.19 | 4.57 | 14.25 | -68,153 | -60,975 | 185,888 | -77,126 | 39.9 |
| all | const 30% | 2.34 | 4.99 | 15.19 | -64,089 | -56,276 | 173,095 | -77,186 | 41.1 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.367 / +0.297 / +0.075
- [PASS] 3 worst week within share: all-in worst week +12.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.73 vs p95 -1.63 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.100, +0.473]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 83% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.304 / +0.232 / -0.001
- [PASS] 6 worst-decile corr <=+0.30: -0.44
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ2_BTC); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3816 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 977 | +0.0801 | 2.40 |
| fixed | 977 | +0.0563 | 1.67 |
| scaled | 977 | +0.0563 | 1.67 |

Plateau neighbours (all-in 20% uplift; selected +0.282):
- {'sym': 'BTC', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.333 (trades 4056)
- {'sym': 'BTC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.106 (trades 4112)
- {'sym': 'BTC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: +0.269 (trades 3900)
- {'sym': 'BTC', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: +0.219 (trades 3551)
- {'sym': 'BTC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.370 (trades 3611)
- {'sym': 'BTC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.294 (trades 3723)

Own random-entry null: 300 draws, standalone all-in Sharpe median -2.46, p95 -1.63, real 1.73. Standalone Sharpe at 2x slippage 1.38.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2022 | 977 | 55 | 1.67 |
| 2023 | 830 | 33 | 0.78 |
| 2024 | 1212 | 72 | 1.37 |
| 2025 | 1240 | 154 | 3.61 |
| 2026 | 993 | 17 | 0.45 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 333 | -0.072 | 0.068 |
| 2013-22 | mid | 314 | +0.119 | 0.078 |
| 2013-22 | high | 289 | +0.128 | 0.081 |
| 2023-26 | low | 1230 | -0.061 | 0.038 |
| 2023-26 | mid | 1313 | +0.091 | 0.038 |
| 2023-26 | high | 1273 | +0.174 | 0.039 |

DONE RZ2_BTC