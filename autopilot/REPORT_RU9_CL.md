# REPORT RU9_CL
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0; additive @20% clean/H1/H2 -0.09/-0.34/-0.09; standalone all-in weekly Sharpe -0.54 (2013-26 0.07, dev 2013-22 0.35); pair-window trades 571. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|---------:|-------:|:-----------|
| CL    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  378 |   -0.289 |  -11.805 |      1 | True       |
| CL    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  662 |   -0.835 |  -43.502 |      1 | True       |
| CL    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1585 |   -0.870 |  -66.765 |      1 | True       |
| CL    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  928 |   -1.139 |  -66.340 |      0 | True       |
| CL    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  579 |   -1.303 |  -54.280 |      0 | True       |
| CL    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1456 |   -1.571 | -107.800 |      1 | True       |
| CL    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 2511 |   -2.298 | -198.400 |      0 | True       |
| CL    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 2307 |   -2.480 | -211.419 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.29; replicate best-eligible median 0.10, p95 0.64; real beats 20% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.229e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.039 | -0.165 | -0.041 | -0.060 | +10.1 | [-0.142, +0.026] | 0.40 | NO |
| 20% | add | -0.092 | -0.345 | -0.095 | -0.134 | +20.9 | [-0.295, +0.035] | 0.40 | NO |
| 30% | add | -0.153 | -0.535 | -0.159 | -0.218 | +31.7 | [-0.456, +0.030] | 0.40 | NO |
| 50% | add | -0.295 | -0.937 | -0.311 | -0.405 | +59.0 | [-0.781, -0.022] | 0.40 | NO |
| 10% | const | -0.045 | -0.185 | -0.046 | -0.068 | +0.1 | [-0.159, +0.028] | 0.40 | NO |
| 20% | const | -0.121 | -0.439 | -0.126 | -0.175 | +1.0 | [-0.376, +0.034] | 0.40 | NO |
| 30% | const | -0.243 | -0.792 | -0.254 | -0.337 | +4.2 | [-0.666, +0.002] | 0.40 | NO |
| 50% | const | -0.642 | -1.915 | -0.733 | -0.865 | +14.8 | [-1.487, -0.250] | 0.40 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -263,184, Sharpe -0.29, maxDD 552,642, worst wk -119,728; H1: net -368,555, Sharpe -2.46, maxDD 467,217, worst wk -70,083; H2: net -93,173, Sharpe -0.35, maxDD 481,309, worst wk -91,215; all: net -724,911, Sharpe -0.54, maxDD 1,099,525, worst wk -119,728
Correlation with pair (weekly): clean +0.02, H1 -0.09, H2 +0.04, all +0.02; worst-decile weeks (n=17) corr +0.27, sleeve mean in those weeks $2,485, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.37 | 2.56 | 4.02 | -87,172 | -81,148 | 317,420 | -99,763 | 41.9 |
| clean | add 30% | 1.31 | 2.41 | 3.44 | -92,156 | -83,723 | 363,837 | -108,708 | 43.8 |
| clean | const 20% | 1.34 | 2.49 | 3.71 | -71,731 | -65,886 | 272,503 | -83,388 | 43.8 |
| clean | const 30% | 1.22 | 2.20 | 2.86 | -69,432 | -62,492 | 297,623 | -86,011 | 46.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.48 | 4.78 | 2.99 | -87,184 | -75,629 | 174,038 | -90,949 | 39.3 |
| H1 | add 30% | 2.29 | 4.19 | 2.61 | -91,971 | -80,596 | 185,200 | -97,957 | 42.9 |
| H1 | const 20% | 2.39 | 4.48 | 2.79 | -71,662 | -62,490 | 143,695 | -75,563 | 42.9 |
| H1 | const 30% | 2.04 | 3.50 | 2.18 | -68,688 | -60,887 | 139,686 | -74,878 | 39.3 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.20 | 4.33 | 3.28 | -87,850 | -83,959 | 231,539 | -88,769 | 37.8 |
| H2 | add 30% | 2.14 | 4.18 | 3.12 | -92,508 | -86,346 | 240,508 | -93,327 | 37.8 |
| H2 | const 20% | 2.17 | 4.26 | 3.21 | -72,143 | -68,122 | 188,054 | -72,839 | 37.8 |
| H2 | const 30% | 2.04 | 3.98 | 2.89 | -68,948 | -62,591 | 178,831 | -69,431 | 40.5 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.72 | 3.27 | 8.06 | -88,617 | -82,520 | 317,420 | -99,763 | 40.8 |
| all | add 30% | 1.64 | 3.06 | 6.83 | -94,134 | -85,310 | 363,837 | -108,708 | 42.6 |
| all | const 20% | 1.68 | 3.16 | 7.40 | -73,100 | -67,092 | 272,503 | -83,388 | 42.6 |
| all | const 30% | 1.52 | 2.77 | 5.62 | -70,859 | -63,244 | 297,623 | -86,011 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.092 / -0.345 / -0.095
- [FAIL] 3 worst week within share: all-in worst week +20.9% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.54 vs p95 0.14 (rank 0.55)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.295, +0.035]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.130 / -0.393 / -0.111
- [PASS] 6 worst-decile corr <=+0.30: +0.27
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_CL); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (571 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1727 | +0.0694 | 0.70 |
| fixed | 1727 | +0.0344 | 0.35 |
| scaled | 1727 | +0.0344 | 0.35 |

Plateau neighbours (all-in 20% uplift; selected -0.134):
- {'sym': 'CL', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.324 (trades 1485)
- {'sym': 'CL', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '0.75', 'R': '2.0'}: -0.192 (trades 582)
- {'sym': 'CL', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '1.5'}: -0.155 (trades 595)
- {'sym': 'CL', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '3.125', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.026 (trades 200)
- {'sym': 'CL', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.25', 'R': '2.0'}: -0.078 (trades 559)
- {'sym': 'CL', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '2.5'}: -0.070 (trades 562)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.62, p95 0.14, real -0.54. Standalone Sharpe at 2x slippage -0.73.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 157 | 19 | 1.00 |
| 2014 | 175 | -19 | -1.01 |
| 2015 | 185 | -4 | -0.22 |
| 2016 | 171 | 16 | 0.94 |
| 2017 | 193 | 14 | 0.98 |
| 2018 | 203 | -3 | -0.18 |
| 2019 | 183 | 12 | 0.59 |
| 2020 | 142 | 0 | 0.00 |
| 2021 | 154 | 5 | 0.29 |
| 2022 | 164 | 19 | 1.17 |
| 2023 | 192 | -18 | -0.81 |
| 2024 | 188 | 11 | 0.55 |
| 2025 | 180 | -26 | -1.66 |
| 2026 | 124 | -9 | -0.65 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.29 | -0.09/-0.34/-0.09 |
| 2 tick entry / 2 tick exit | -0.84 | -0.20/-0.40/-0.11 |
| 3 tick entry / 3 tick exit | -1.31 | -0.29/-0.44/-0.19 |

DONE RU9_CL