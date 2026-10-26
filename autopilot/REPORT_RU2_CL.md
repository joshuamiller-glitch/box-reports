# REPORT RU2_CL
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=mkt, k=1.5, tf=30, S=1.0, R=2.0; additive @20% clean/H1/H2 -0.05/-0.75/-0.23; standalone all-in weekly Sharpe -0.76 (2013-26 -0.83, dev 2013-22 -0.81); pair-window trades 2521. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| CL    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1650 |   -0.102 |  -8.294 |      2 | True       |
| CL    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 2.000 | 1485 |   -0.182 | -13.244 |      1 | True       |
| CL    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 2.000 | 1350 |   -0.281 | -16.960 |      2 | True       |
| CL    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 2059 |   -0.409 | -32.633 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 2.000 |  691 |   -0.812 | -35.655 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 | 1050 |   -0.869 | -48.243 |      1 | True       |
| CL    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 |  772 |   -0.869 | -45.747 |      1 | True       |
| CL    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 1.000 | 1641 |   -0.875 | -44.867 |      0 | True       |
| CL    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 2.000 |  739 |   -0.882 | -42.750 |      0 | True       |
| CL    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | 1509 |   -0.943 | -65.050 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.10; replicate best-eligible median 0.20, p95 0.82; real beats 15% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.122e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.021 | -0.385 | -0.110 | -0.088 | +15.0 | [-0.180, +0.003] | 0.28 | NO |
| 20% | add | -0.055 | -0.750 | -0.231 | -0.189 | +35.1 | [-0.367, -0.009] | 0.28 | NO |
| 30% | add | -0.100 | -1.091 | -0.362 | -0.298 | +55.2 | [-0.557, -0.036] | 0.28 | NO |
| 50% | add | -0.212 | -1.688 | -0.642 | -0.529 | +95.4 | [-0.930, -0.120] | 0.28 | NO |
| 10% | const | -0.024 | -0.427 | -0.123 | -0.099 | +5.5 | [-0.200, +0.002] | 0.28 | NO |
| 20% | const | -0.076 | -0.924 | -0.295 | -0.243 | +16.1 | [-0.463, -0.020] | 0.28 | NO |
| 30% | const | -0.169 | -1.487 | -0.540 | -0.446 | +26.7 | [-0.797, -0.087] | 0.28 | NO |
| 50% | const | -0.511 | -2.746 | -1.342 | -1.051 | +48.0 | [-1.702, -0.375] | 0.28 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -93,085, Sharpe -0.10, maxDD 706,754, worst wk -130,848; H1: net -564,704, Sharpe -2.65, maxDD 614,190, worst wk -165,981; H2: net -384,760, Sharpe -1.60, maxDD 667,433, worst wk -108,067; all: net -1,042,548, Sharpe -0.76, maxDD 1,740,221, worst wk -165,981
Correlation with pair (weekly): clean +0.02, H1 +0.43, H2 -0.08, all +0.05; worst-decile weeks (n=17) corr +0.00, sleeve mean in those weeks $-8,883, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.41 | 2.65 | 3.83 | -88,211 | -82,890 | 342,012 | -97,746 | 45.7 |
| clean | add 30% | 1.36 | 2.54 | 3.49 | -94,768 | -86,253 | 372,962 | -107,841 | 47.6 |
| clean | const 20% | 1.38 | 2.60 | 3.66 | -73,192 | -67,657 | 285,990 | -82,235 | 47.6 |
| clean | const 30% | 1.29 | 2.36 | 3.13 | -72,239 | -64,374 | 288,930 | -84,573 | 47.6 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.08 | 3.89 | 2.63 | -101,479 | -86,372 | 182,990 | -111,483 | 46.4 |
| H1 | add 30% | 1.74 | 3.05 | 2.14 | -113,414 | -96,709 | 198,629 | -128,082 | 46.4 |
| H1 | const 20% | 1.90 | 3.45 | 2.37 | -85,957 | -73,232 | 152,648 | -95,826 | 46.4 |
| H1 | const 30% | 1.34 | 2.19 | 1.59 | -90,131 | -77,000 | 154,518 | -104,595 | 46.4 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.06 | 4.12 | 3.06 | -86,111 | -79,814 | 223,566 | -91,703 | 44.4 |
| H2 | add 30% | 1.93 | 3.81 | 2.82 | -89,182 | -80,128 | 229,236 | -96,293 | 47.2 |
| H2 | const 20% | 2.00 | 3.97 | 2.95 | -70,117 | -63,977 | 180,081 | -75,198 | 47.2 |
| H2 | const 30% | 1.76 | 3.41 | 2.36 | -65,191 | -56,901 | 177,247 | -71,535 | 50.0 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.67 | 3.17 | 7.24 | -91,548 | -84,353 | 342,012 | -111,483 | 45.8 |
| all | add 30% | 1.56 | 2.90 | 6.36 | -99,081 | -88,007 | 372,962 | -128,082 | 47.6 |
| all | const 20% | 1.61 | 3.03 | 6.78 | -76,251 | -68,944 | 285,990 | -95,826 | 47.6 |
| all | const 30% | 1.41 | 2.54 | 5.42 | -76,137 | -65,886 | 288,930 | -104,595 | 47.6 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.055 / -0.750 / -0.231
- [FAIL] 3 worst week within share: all-in worst week +35.1% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.76 vs p95 -0.31 (rank 0.77)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.367, -0.009]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.144 / -0.844 / -0.276
- [PASS] 6 worst-decile corr <=+0.30: +0.00
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_CL); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2521 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6723 | -0.0032 | -0.07 |
| fixed | 6723 | -0.0391 | -0.81 |
| scaled | 6723 | -0.0391 | -0.81 |

Plateau neighbours (all-in 20% uplift; selected -0.189):
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.125', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.296 (trades 3884)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '0.75', 'R': '2.0'}: -0.277 (trades 2586)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '1.5'}: -0.256 (trades 2704)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.137 (trades 1408)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.25', 'R': '2.0'}: -0.186 (trades 2410)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '2.5'}: -0.179 (trades 2388)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.13, p95 -0.31, real -0.76. Standalone Sharpe at 2x slippage -1.18.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 609 | -8 | -0.25 |
| 2014 | 613 | -45 | -1.53 |
| 2015 | 670 | 24 | 0.68 |
| 2016 | 697 | -11 | -0.33 |
| 2017 | 555 | -2 | -0.06 |
| 2018 | 670 | -14 | -0.47 |
| 2019 | 692 | -75 | -2.08 |
| 2020 | 636 | -58 | -1.69 |
| 2021 | 723 | -57 | -1.77 |
| 2022 | 858 | -18 | -0.49 |
| 2023 | 904 | -25 | -0.67 |
| 2024 | 839 | 25 | 0.59 |
| 2025 | 733 | -73 | -2.05 |
| 2026 | 570 | -50 | -2.06 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.10 | -0.05/-0.75/-0.23 |
| 2 tick entry / 2 tick exit | -1.37 | -0.30/-0.92/-0.30 |
| 3 tick entry / 3 tick exit | -2.49 | -0.52/-1.07/-0.44 |
| retrace-limit DISP (b=1.5, tf30, f=0.5, RZ geometry) | 0.32 | +0.05/-0.40/-0.11 |

DONE RU2_CL