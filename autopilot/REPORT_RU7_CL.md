# REPORT RU7_CL
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=mkt, k=1.5, tf=30, S=1.5, R=0.0; additive @20% clean/H1/H2 -0.25/-0.73/-0.24; standalone all-in weekly Sharpe -1.42 (2013-26 -1.38, dev 2013-22 -1.35); pair-window trades 2655. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|---------:|-------:|:-----------|
| CL    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 0.000 | 1773 |   -1.049 |  -61.946 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1582 |   -1.224 |  -68.925 |      0 | True       |
| CL    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  789 |   -1.672 |  -68.326 |      0 | True       |
| CL    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 0.000 | 1857 |   -1.700 | -111.388 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 0.000 |  720 |   -1.731 |  -67.638 |      0 | True       |
| CL    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 0.000 |  772 |   -1.801 |  -64.736 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 | 1147 |   -1.911 |  -88.778 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.000 | 0.000 | 1646 |   -1.923 | -116.969 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 0.000 |  708 |   -1.949 |  -67.913 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 0.000 | 1153 |   -2.057 | -101.757 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -1.05; replicate best-eligible median -0.21, p95 0.28; real beats 0% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.543e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.121 | -0.373 | -0.112 | -0.153 | +12.2 | [-0.248, -0.062] | 0.21 | NO |
| 20% | add | -0.250 | -0.735 | -0.238 | -0.315 | +29.5 | [-0.499, -0.137] | 0.21 | NO |
| 30% | add | -0.383 | -1.077 | -0.374 | -0.483 | +46.9 | [-0.750, -0.225] | 0.21 | NO |
| 50% | add | -0.645 | -1.683 | -0.671 | -0.815 | +81.5 | [-1.225, -0.411] | 0.21 | NO |
| 10% | const | -0.135 | -0.413 | -0.126 | -0.170 | +2.7 | [-0.276, -0.070] | 0.21 | NO |
| 20% | const | -0.316 | -0.909 | -0.304 | -0.399 | +10.6 | [-0.625, -0.180] | 0.21 | NO |
| 30% | const | -0.553 | -1.479 | -0.562 | -0.698 | +18.4 | [-1.062, -0.342] | 0.21 | NO |
| 50% | const | -1.179 | -2.752 | -1.433 | -1.503 | +34.1 | [-2.171, -0.842] | 0.21 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -955,902, Sharpe -1.05, maxDD 1,142,601, worst wk -158,463; H1: net -566,454, Sharpe -2.46, maxDD 614,702, worst wk -143,063; H2: net -444,995, Sharpe -1.82, maxDD 653,625, worst wk -100,973; all: net -1,967,351, Sharpe -1.42, maxDD 2,156,436, worst wk -158,463
Correlation with pair (weekly): clean +0.07, H1 +0.33, H2 -0.16, all +0.06; worst-decile weeks (n=17) corr -0.32, sleeve mean in those weeks $-9,484, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.21 | 2.25 | 3.35 | -88,483 | -83,883 | 339,541 | -93,836 | 47.6 |
| clean | add 30% | 1.08 | 1.96 | 2.66 | -95,170 | -87,952 | 392,184 | -102,249 | 50.5 |
| clean | const 20% | 1.14 | 2.11 | 2.98 | -73,458 | -68,734 | 292,690 | -78,434 | 50.5 |
| clean | const 30% | 0.91 | 1.59 | 2.00 | -73,546 | -66,405 | 321,908 | -82,508 | 50.5 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.09 | 3.91 | 2.76 | -95,244 | -85,789 | 174,106 | -106,900 | 35.7 |
| H1 | add 30% | 1.75 | 3.05 | 2.21 | -104,062 | -95,835 | 191,364 | -121,206 | 35.7 |
| H1 | const 20% | 1.92 | 3.46 | 2.48 | -79,722 | -72,649 | 145,927 | -91,242 | 35.7 |
| H1 | const 30% | 1.35 | 2.18 | 1.64 | -82,270 | -76,126 | 150,075 | -97,720 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.06 | 4.09 | 3.12 | -81,761 | -77,047 | 220,745 | -85,107 | 45.9 |
| H2 | add 30% | 1.92 | 3.78 | 2.90 | -82,097 | -76,067 | 222,406 | -86,398 | 45.9 |
| H2 | const 20% | 1.99 | 3.94 | 3.01 | -65,543 | -61,210 | 177,260 | -68,602 | 45.9 |
| H2 | const 30% | 1.74 | 3.35 | 2.57 | -57,770 | -53,953 | 160,210 | -61,640 | 43.2 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.54 | 2.90 | 6.80 | -89,610 | -83,611 | 339,541 | -106,900 | 45.6 |
| all | add 30% | 1.38 | 2.51 | 5.39 | -96,171 | -87,804 | 392,184 | -121,206 | 47.3 |
| all | const 20% | 1.46 | 2.71 | 6.04 | -74,311 | -68,356 | 292,690 | -91,242 | 47.3 |
| all | const 30% | 1.16 | 2.04 | 4.04 | -74,406 | -66,327 | 321,908 | -97,720 | 46.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.250 / -0.735 / -0.238
- [FAIL] 3 worst week within share: all-in worst week +29.5% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -1.42 vs p95 -0.71 (rank 0.56)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.499, -0.137]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.398 / -0.892 / -0.293
- [PASS] 6 worst-decile corr <=+0.30: -0.32
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_CL); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2655 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 7116 | -0.0070 | -0.21 |
| fixed | 7116 | -0.0441 | -1.35 |
| scaled | 7116 | -0.0441 | -1.35 |

Plateau neighbours (all-in 20% uplift; selected -0.315):
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.125', 'tf': '30', 'S': '1.5', 'R': '0.0'}: -0.620 (trades 4130)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.125', 'R': '0.0'}: -0.407 (trades 2762)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.5', 'R': '0.0'}: -0.225 (trades 1414)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.875', 'R': '0.0'}: -0.317 (trades 2437)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.50, p95 -0.71, real -1.42. Standalone Sharpe at 2x slippage -2.11.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 646 | -57 | -2.75 |
| 2014 | 658 | -61 | -2.62 |
| 2015 | 712 | -26 | -1.27 |
| 2016 | 770 | -34 | -1.40 |
| 2017 | 607 | -3 | -0.11 |
| 2018 | 726 | -40 | -1.92 |
| 2019 | 758 | -23 | -0.85 |
| 2020 | 668 | -23 | -0.84 |
| 2021 | 756 | -44 | -1.90 |
| 2022 | 815 | -3 | -0.15 |
| 2023 | 926 | -66 | -2.25 |
| 2024 | 903 | -20 | -0.66 |
| 2025 | 805 | -38 | -1.24 |
| 2026 | 550 | -34 | -1.86 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -1.05 | -0.25/-0.73/-0.24 |
| 2 tick entry / 2 tick exit | -2.56 | -0.54/-1.04/-0.34 |
| 3 tick entry / 3 tick exit | -4.03 | -0.83/-1.36/-0.45 |
| retrace-limit DISP (b=1.5, tf30, f=0.5, RZ geometry) | 0.32 | +0.05/-0.40/-0.07 |

DONE RU7_CL