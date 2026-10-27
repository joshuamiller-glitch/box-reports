# REPORT RU10_RBxCL
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=1, sess=ALL, ent=mkt, k=2.0, tf=30, S=1.0, R=2.0, partner=CL; additive @20% clean/H1/H2 -0.00/-0.18/-0.14; standalone all-in weekly Sharpe -0.25 (2013-26 -0.63, dev 2013-22 -0.84); pair-window trades 1239. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU10 displacement continuation confirmed by a same-direction displacement (range >= 1 ATR) in the partner market. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R | partner   |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|:----------|-----:|---------:|---------:|-------:|:-----------|
| RB    |    1 |      1 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 | CL        |  805 |   -0.030 |   -1.664 |      1 | True       |
| RB    |    1 |      1 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | CL        | 1844 |   -0.223 |  -18.934 |      1 | True       |
| RB    |    1 |      1 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | CL        | 2890 |   -0.224 |  -23.178 |      2 | True       |
| RB    |    1 |      1 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | CL        | 1334 |   -0.235 |  -18.371 |      2 | True       |
| RB    |    1 |      1 | ALL    | stop  | 2.000 |   30 | 1.000 | 2.000 | CL        |  730 |   -0.506 |  -25.999 |      1 | True       |
| RB    |    1 |      1 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | CL        | 1627 |   -0.675 |  -52.765 |      1 | True       |
| RB    |    1 |      1 | ALL    | mkt   | 2.000 |   15 | 1.000 | 2.000 | CL        | 1519 |   -0.862 |  -73.726 |      1 | True       |
| RB    |    1 |      1 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | CL        | 3420 |   -1.555 | -175.877 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.03; replicate best-eligible median 0.08, p95 0.77; real beats 30% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.619e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.006 | -0.072 | -0.063 | -0.018 | +8.3 | [-0.115, +0.082] | 0.87 | NO |
| 20% | add | -0.004 | -0.177 | -0.145 | -0.054 | +16.6 | [-0.246, +0.143] | 0.87 | NO |
| 30% | add | -0.027 | -0.304 | -0.243 | -0.107 | +24.8 | [-0.387, +0.185] | 0.87 | NO |
| 50% | add | -0.108 | -0.586 | -0.481 | -0.250 | +41.4 | [-0.688, +0.212] | 0.87 | NO |
| 10% | const | +0.005 | -0.082 | -0.071 | -0.021 | -1.7 | [-0.128, +0.090] | 0.87 | NO |
| 20% | const | -0.014 | -0.239 | -0.192 | -0.078 | -3.4 | [-0.316, +0.167] | 0.87 | NO |
| 30% | const | -0.074 | -0.484 | -0.391 | -0.194 | -5.2 | [-0.578, +0.210] | 0.87 | NO |
| 50% | const | -0.389 | -1.210 | -1.147 | -0.668 | -8.6 | [-1.392, +0.084] | 0.87 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -26,936, Sharpe -0.03, maxDD 570,972, worst wk -128,069; H1: net -21,339, Sharpe -0.08, maxDD 327,118, worst wk -120,460; H2: net -315,050, Sharpe -1.07, maxDD 585,248, worst wk -108,835; all: net -363,325, Sharpe -0.25, maxDD 993,031, worst wk -128,069
Correlation with pair (weekly): clean -0.11, H1 +0.12, H2 -0.20, all -0.09; worst-decile weeks (n=17) corr +0.18, sleeve mean in those weeks $4,767, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.46 | 2.75 | 4.51 | -84,759 | -79,454 | 293,845 | -88,295 | 41.0 |
| clean | add 30% | 1.43 | 2.67 | 3.93 | -88,116 | -80,906 | 336,488 | -93,400 | 42.9 |
| clean | const 20% | 1.45 | 2.72 | 4.20 | -69,150 | -64,144 | 252,133 | -72,678 | 41.9 |
| clean | const 30% | 1.39 | 2.54 | 3.37 | -64,703 | -59,133 | 273,920 | -70,015 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.65 | 5.56 | 3.35 | -75,190 | -67,642 | 175,852 | -92,128 | 35.7 |
| H1 | add 30% | 2.52 | 5.17 | 3.13 | -78,467 | -68,615 | 187,922 | -99,049 | 35.7 |
| H1 | const 20% | 2.59 | 5.37 | 3.24 | -60,322 | -54,503 | 145,509 | -76,471 | 35.7 |
| H1 | const 30% | 2.34 | 4.64 | 2.84 | -60,444 | -52,999 | 144,155 | -75,562 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.15 | 4.16 | 3.68 | -88,082 | -83,028 | 194,510 | -96,183 | 40.5 |
| H2 | add 30% | 2.05 | 3.85 | 3.65 | -91,578 | -84,950 | 187,566 | -103,012 | 40.5 |
| H2 | const 20% | 2.11 | 4.01 | 3.71 | -71,864 | -67,191 | 151,025 | -79,678 | 40.5 |
| H2 | const 30% | 1.91 | 3.45 | 3.37 | -67,252 | -61,195 | 133,480 | -78,254 | 40.5 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.80 | 3.46 | 8.95 | -86,316 | -80,179 | 293,845 | -96,183 | 40.2 |
| all | add 30% | 1.75 | 3.31 | 7.71 | -90,100 | -82,273 | 336,488 | -103,012 | 41.4 |
| all | const 20% | 1.78 | 3.39 | 8.29 | -70,567 | -64,981 | 252,133 | -79,678 | 40.8 |
| all | const 30% | 1.66 | 3.07 | 6.51 | -66,476 | -60,248 | 273,920 | -78,254 | 42.0 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.004 / -0.177 / -0.145
- [PASS] 3 worst week within share: all-in worst week +16.6% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.25 vs p95 0.73 (rank 0.41)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.246, +0.143]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.031 / -0.214 / -0.156
- [PASS] 6 worst-decile corr <=+0.30: +0.18
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU10_RBxCL); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1239 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 4198 | -0.0309 | -0.45 |
| fixed | 4198 | -0.0588 | -0.84 |
| scaled | 4198 | -0.0588 | -0.84 |

Plateau neighbours (all-in 20% uplift; selected -0.054):
- {'sym': 'RB', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '2.0', 'partner': 'CL'}: -0.232 (trades 2808)
- {'sym': 'RB', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '0.75', 'R': '2.0', 'partner': 'CL'}: -0.058 (trades 1260)
- {'sym': 'RB', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.0', 'R': '1.5', 'partner': 'CL'}: +0.027 (trades 1257)
- {'sym': 'RB', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '2.0', 'partner': 'CL'}: +0.010 (trades 454)
- {'sym': 'RB', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.25', 'R': '2.0', 'partner': 'CL'}: -0.173 (trades 1194)
- {'sym': 'RB', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.0', 'R': '2.5', 'partner': 'CL'}: -0.139 (trades 1209)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.14, p95 0.73, real -0.25. Standalone Sharpe at 2x slippage -0.37.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 396 | -23 | -0.81 |
| 2014 | 414 | -14 | -0.42 |
| 2015 | 444 | -16 | -0.55 |
| 2016 | 473 | -59 | -1.88 |
| 2017 | 435 | -36 | -1.27 |
| 2018 | 453 | -44 | -1.86 |
| 2019 | 450 | -16 | -0.51 |
| 2020 | 381 | -19 | -0.68 |
| 2021 | 383 | -16 | -0.49 |
| 2022 | 369 | -4 | -0.15 |
| 2023 | 462 | 16 | 0.55 |
| 2024 | 425 | 14 | 0.51 |
| 2025 | 370 | -14 | -0.50 |
| 2026 | 258 | -22 | -1.06 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.03 | -0.00/-0.18/-0.14 |
| 2 tick entry / 2 tick exit | -0.51 | -0.10/-0.24/-0.15 |
| 3 tick entry / 3 tick exit | -0.82 | -0.16/-0.29/-0.19 |
| retrace-limit DISP (b=2.0, tf30, f=0.5, RZ geometry) | 0.23 | +0.01/-0.05/-0.34 |

DONE RU10_RBxCL