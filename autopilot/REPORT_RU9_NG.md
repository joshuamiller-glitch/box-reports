# REPORT RU9_NG
**Verdict: NO** (3/7 measured gates pass). Selected cell nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0; additive @20% clean/H1/H2 +0.29/-0.03/-0.22; standalone all-in weekly Sharpe 0.71 (2013-26 -0.05, dev 2013-22 -0.28); pair-window trades 683. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| NG    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  444 |    1.464 |  62.050 |      3 | True       |
| NG    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  576 |    0.526 |  22.323 |      3 | True       |
| NG    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  808 |   -0.201 | -12.068 |      1 | True       |
| NG    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1449 |   -0.217 | -15.968 |      1 | True       |
| NG    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 1701 |   -0.419 | -32.872 |      1 | True       |
| NG    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  620 |   -0.618 | -32.368 |      0 | True       |
| NG    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 1863 |   -0.989 | -83.061 |      0 | True       |
| NG    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1234 |   -1.016 | -61.120 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.46; replicate best-eligible median 0.00, p95 1.18; real beats 95% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.149e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.153 | -0.007 | -0.105 | +0.071 | +7.7 | [-0.015, +0.160] | 0.86 | NO |
| 20% | add | +0.290 | -0.033 | -0.217 | +0.125 | +18.6 | [-0.046, +0.300] | 0.86 | NO |
| 30% | add | +0.408 | -0.077 | -0.335 | +0.161 | +29.5 | [-0.091, +0.420] | 0.86 | NO |
| 50% | add | +0.578 | -0.220 | -0.577 | +0.185 | +51.4 | [-0.222, +0.597] | 0.86 | NO |
| 10% | const | +0.169 | -0.009 | -0.117 | +0.078 | -2.0 | [-0.017, +0.176] | 0.86 | NO |
| 20% | const | +0.352 | -0.052 | -0.275 | +0.145 | -0.7 | [-0.067, +0.362] | 0.86 | NO |
| 30% | const | +0.527 | -0.161 | -0.490 | +0.183 | +0.5 | [-0.172, +0.543] | 0.86 | NO |
| 50% | const | +0.711 | -0.778 | -1.141 | +0.059 | +3.0 | [-0.647, +0.746] | 0.86 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,333,465, Sharpe 1.46, maxDD 227,863, worst wk -135,113; H1: net -116,364, Sharpe -0.70, maxDD 227,690, worst wk -135,113; H2: net -262,185, Sharpe -1.05, maxDD 571,770, worst wk -112,594; all: net 954,915, Sharpe 0.71, maxDD 659,092, worst wk -135,113
Correlation with pair (weekly): clean -0.09, H1 -0.25, H2 +0.13, all -0.07; worst-decile weeks (n=17) corr +0.03, sleeve mean in those weeks $5,456, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.75 | 3.51 | 6.74 | -84,367 | -77,473 | 236,857 | -97,883 | 44.8 |
| clean | add 30% | 1.87 | 3.78 | 6.92 | -87,641 | -78,560 | 250,090 | -106,890 | 41.9 |
| clean | const 20% | 1.81 | 3.65 | 6.83 | -68,803 | -62,411 | 194,779 | -81,909 | 42.9 |
| clean | const 30% | 1.99 | 4.05 | 7.04 | -65,114 | -56,349 | 188,959 | -82,930 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.80 | 5.70 | 3.44 | -75,500 | -66,283 | 166,025 | -77,864 | 32.1 |
| H1 | add 30% | 2.75 | 5.48 | 3.23 | -74,445 | -66,409 | 173,181 | -78,330 | 28.6 |
| H1 | const 20% | 2.78 | 5.59 | 3.33 | -59,978 | -53,077 | 135,682 | -62,478 | 28.6 |
| H1 | const 30% | 2.67 | 5.18 | 2.98 | -51,162 | -46,600 | 127,667 | -55,250 | 32.1 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.08 | 4.02 | 3.01 | -85,910 | -83,713 | 241,296 | -86,423 | 40.5 |
| H2 | add 30% | 1.96 | 3.72 | 2.76 | -90,505 | -88,628 | 253,231 | -90,927 | 43.2 |
| H2 | const 20% | 2.02 | 3.87 | 2.88 | -69,916 | -68,865 | 197,811 | -70,940 | 43.2 |
| H2 | const 30% | 1.81 | 3.36 | 2.46 | -70,447 | -66,624 | 189,229 | -73,192 | 43.2 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.98 | 3.93 | 11.99 | -84,996 | -79,452 | 241,296 | -97,883 | 42.0 |
| all | add 30% | 2.02 | 3.99 | 11.80 | -89,463 | -81,408 | 253,231 | -106,890 | 40.2 |
| all | const 20% | 2.00 | 3.96 | 11.89 | -69,784 | -64,307 | 197,811 | -81,909 | 40.8 |
| all | const 30% | 2.04 | 4.01 | 11.51 | -66,856 | -59,265 | 189,229 | -82,930 | 40.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.290 / -0.033 / -0.217
- [PASS] 3 worst week within share: all-in worst week +18.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.71 vs p95 0.48 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.046, +0.300]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.241 / -0.082 / -0.261
- [PASS] 6 worst-decile corr <=+0.30: +0.03
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_NG); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (683 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1938 | +0.0161 | 0.20 |
| fixed | 1938 | -0.0229 | -0.28 |
| scaled | 1938 | -0.0229 | -0.28 |

Plateau neighbours (all-in 20% uplift; selected +0.125):
- {'sym': 'NG', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.204 (trades 1563)
- {'sym': 'NG', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '0.75', 'R': '2.0'}: +0.138 (trades 684)
- {'sym': 'NG', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '1.5'}: +0.037 (trades 711)
- {'sym': 'NG', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '3.125', 'tf': '30', 'S': '1.0', 'R': '2.0'}: +0.150 (trades 257)
- {'sym': 'NG', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.25', 'R': '2.0'}: +0.078 (trades 675)
- {'sym': 'NG', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '2.5'}: +0.103 (trades 661)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.38, p95 0.48, real 0.71. Standalone Sharpe at 2x slippage 0.45.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 232 | -17 | -0.99 |
| 2014 | 224 | -34 | -2.03 |
| 2015 | 190 | -0 | -0.01 |
| 2016 | 212 | -9 | -0.54 |
| 2017 | 185 | 22 | 1.74 |
| 2018 | 148 | -4 | -0.43 |
| 2019 | 154 | -22 | -1.97 |
| 2020 | 195 | 11 | 0.64 |
| 2021 | 199 | -4 | -0.23 |
| 2022 | 199 | 14 | 0.66 |
| 2023 | 201 | 14 | 0.91 |
| 2024 | 208 | 0 | 0.00 |
| 2025 | 231 | 34 | 1.37 |
| 2026 | 151 | -14 | -1.14 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.46 | +0.29/-0.03/-0.22 |
| 2 tick entry / 2 tick exit | 0.98 | +0.19/-0.21/-0.29 |
| 3 tick entry / 3 tick exit | 0.22 | +0.05/-0.29/-0.44 |

DONE RU9_NG