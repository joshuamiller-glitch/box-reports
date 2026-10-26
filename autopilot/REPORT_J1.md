# REPORT J1
**Verdict: NO** (2/7 measured gates pass). Selected cell sig=ext, cls=lev, mode=follow, L=52, band=0.8; additive @20% clean/H1/H2 +0.20/-0.55/-0.10; standalone all-in weekly Sharpe 0.45 (2013-26 -0.24, dev 2013-22 -0.44); pair-window trades 271. Runtime 0.1 min (+selection 0.0 min). 7-worker pool.

J1 COT TFF positioning sleeve on NQ/ES/RTY/YM (30 cells): weekly 5-day hold, class lev/am/dealer net/OI percentile extremes or 4-week change, contrarian or follow. Entry/exit at the last 1-minute close at or before 16:16 ET of the label; COT effective as-of Tuesday + 7 days.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 30 cells, eligible (>= 40 clean trades): 30. Top cells by clean weekly Sharpe:

| sig   | cls    | mode   |       L |    band |   n |   sharpe |    net |   ypos | eligible   |
|:------|:-------|:-------|--------:|--------:|----:|---------:|-------:|-------:|:-----------|
| ext   | lev    | follow |  52.000 |   0.800 | 160 |    1.037 | 23.880 |      3 | True       |
| ext   | lev    | follow |  52.000 |   0.900 | 106 |    0.915 | 17.220 |      2 | True       |
| ext   | lev    | contra | 156.000 |   0.900 |  78 |    0.572 |  7.210 |      2 | True       |
| ext   | am     | follow | 156.000 |   0.900 | 110 |    0.407 | 12.705 |      3 | True       |
| ext   | dealer | contra | 156.000 |   0.900 | 144 |    0.385 | 15.031 |      3 | True       |
| ext   | dealer | contra |  52.000 |   0.900 | 143 |    0.253 |  9.686 |      2 | True       |
| ext   | am     | contra |  52.000 |   0.900 | 136 |    0.250 |  8.650 |      2 | True       |
| ext   | dealer | contra | 156.000 |   0.800 | 211 |    0.213 | 10.561 |      2 | True       |
| chg   | lev    | follow | nan     | nan     | 348 |    0.152 |  6.064 |      2 | True       |
| ext   | dealer | contra |  52.000 |   0.800 | 204 |    0.140 |  6.153 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.04; replicate best-eligible median 1.06, p95 1.77; real beats 47% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.958e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.108 | -0.266 | -0.043 | +0.028 | +6.0 | [-0.069, +0.129] | 0.32 | NO |
| 20% | add | +0.199 | -0.549 | -0.097 | +0.035 | +15.2 | [-0.156, +0.234] | 0.32 | NO |
| 30% | add | +0.273 | -0.828 | -0.158 | +0.024 | +28.2 | [-0.254, +0.313] | 0.32 | NO |
| 50% | add | +0.366 | -1.328 | -0.294 | -0.039 | +54.7 | [-0.472, +0.409] | 0.32 | NO |
| 10% | const | +0.119 | -0.297 | -0.048 | +0.030 | -4.0 | [-0.078, +0.142] | 0.32 | NO |
| 20% | const | +0.239 | -0.690 | -0.127 | +0.032 | -2.8 | [-0.204, +0.276] | 0.32 | NO |
| 30% | const | +0.341 | -1.161 | -0.245 | -0.011 | +1.6 | [-0.389, +0.383] | 0.32 | NO |
| 50% | const | +0.374 | -2.172 | -0.623 | -0.289 | +10.5 | [-0.968, +0.423] | 0.32 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 928,470, Sharpe 1.02, maxDD 442,707, worst wk -166,187; H1: net -322,861, Sharpe -1.04, maxDD 720,076, worst wk -185,902; H2: net 87,345, Sharpe 0.29, maxDD 354,351, worst wk -118,425; all: net 692,954, Sharpe 0.45, maxDD 871,222, worst wk -185,902
Correlation with pair (weekly): clean -0.09, H1 +0.23, H2 +0.30, all +0.05; worst-decile weeks (n=17) corr +0.05, sleeve mean in those weeks $9,494, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.66 | 3.20 | 5.24 | -85,203 | -80,487 | 288,990 | -94,826 | 42.9 |
| clean | add 30% | 1.73 | 3.33 | 4.96 | -89,338 | -82,682 | 324,607 | -105,764 | 42.9 |
| clean | const 20% | 1.70 | 3.27 | 5.09 | -69,813 | -65,055 | 245,439 | -80,236 | 42.9 |
| clean | const 30% | 1.80 | 3.44 | 4.66 | -68,342 | -60,706 | 259,280 | -83,879 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.28 | 4.87 | 3.08 | -80,141 | -68,518 | 171,763 | -95,061 | 39.3 |
| H1 | add 30% | 2.00 | 4.21 | 2.73 | -81,407 | -70,703 | 181,788 | -103,448 | 46.4 |
| H1 | const 20% | 2.14 | 4.54 | 2.90 | -64,619 | -55,378 | 141,420 | -79,404 | 42.9 |
| H1 | const 30% | 1.67 | 3.37 | 2.34 | -63,430 | -54,572 | 136,274 | -79,962 | 50.0 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.20 | 4.44 | 3.52 | -88,307 | -83,613 | 221,124 | -92,450 | 44.4 |
| H2 | add 30% | 2.14 | 4.26 | 3.53 | -92,825 | -87,978 | 222,973 | -97,413 | 44.4 |
| H2 | const 20% | 2.17 | 4.35 | 3.53 | -72,340 | -68,636 | 177,639 | -75,946 | 44.4 |
| H2 | const 30% | 2.05 | 4.02 | 3.42 | -71,416 | -65,514 | 163,530 | -72,656 | 47.2 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.89 | 3.73 | 9.77 | -87,217 | -81,605 | 288,990 | -95,061 | 42.9 |
| all | add 30% | 1.88 | 3.69 | 8.91 | -92,868 | -84,451 | 324,607 | -105,764 | 44.0 |
| all | const 20% | 1.89 | 3.71 | 9.32 | -72,022 | -66,264 | 245,439 | -80,236 | 43.5 |
| all | const 30% | 1.84 | 3.57 | 8.05 | -71,274 | -62,195 | 259,280 | -83,879 | 44.6 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.199 / -0.549 / -0.097
- [PASS] 3 worst week within share: all-in worst week +15.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.45 vs p95 0.73 (rank 0.83)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.156, +0.234]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 25% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.193 / -0.559 / -0.101
- [PASS] 6 worst-decile corr <=+0.30: +0.05
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section J1); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (271 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 700 | -0.0785 | -0.37 |
| fixed | 700 | -0.0916 | -0.44 |
| scaled | 700 | -0.0851 | -0.40 |

Plateau neighbours (all-in 20% uplift; selected +0.035):
- {'sig': 'ext', 'cls': 'lev', 'mode': 'follow', 'L': '39', 'band': '0.8'}: +0.011 (trades 269)
- {'sig': 'ext', 'cls': 'lev', 'mode': 'follow', 'L': '65', 'band': '0.8'}: -0.022 (trades 271)
- {'sig': 'ext', 'cls': 'lev', 'mode': 'follow', 'L': '52', 'band': '0.85'}: +0.075 (trades 221)
- {'sig': 'ext', 'cls': 'lev', 'mode': 'follow', 'L': '52', 'band': '0.75'}: -0.014 (trades 331)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.02, p95 0.73, real 0.45. Standalone Sharpe at 2x slippage 0.42.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2014 | 68 | -14 | -0.82 |
| 2015 | 68 | -7 | -0.47 |
| 2016 | 75 | -3 | -0.24 |
| 2017 | 65 | 9 | 0.91 |
| 2018 | 86 | -8 | -0.44 |
| 2019 | 79 | -16 | -1.40 |
| 2020 | 93 | -27 | -1.33 |
| 2021 | 87 | -7 | -0.33 |
| 2022 | 79 | 9 | 0.50 |
| 2023 | 97 | 4 | 0.31 |
| 2024 | 67 | 16 | 1.65 |
| 2025 | 101 | -12 | -0.89 |
| 2026 | 57 | 8 | 0.99 |


DONE J1