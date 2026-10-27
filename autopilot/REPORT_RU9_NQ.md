# REPORT RU9_NQ
**Verdict: NO** (3/7 measured gates pass). Selected cell nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0; additive @20% clean/H1/H2 +0.16/+0.16/-0.25; standalone all-in weekly Sharpe 0.96 (2013-26 0.57, dev 2013-22 0.37); pair-window trades 670. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| NQ    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  448 |    1.392 |  60.751 |      2 | True       |
| NQ    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  788 |    1.325 |  79.806 |      3 | True       |
| NQ    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1465 |    0.930 |  70.205 |      2 | True       |
| NQ    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  541 |    0.853 |  34.365 |      2 | True       |
| NQ    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1623 |    0.300 |  20.848 |      2 | True       |
| NQ    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 | 1026 |    0.274 |  18.002 |      3 | True       |
| NQ    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 3138 |   -0.083 |  -9.177 |      1 | True       |
| NQ    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 2897 |   -0.746 | -72.122 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.39; replicate best-eligible median 0.88, p95 1.88; real beats 85% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.087e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.089 | +0.095 | -0.120 | +0.043 | +7.6 | [-0.038, +0.127] | 0.00 | NO |
| 20% | add | +0.160 | +0.156 | -0.249 | +0.069 | +16.0 | [-0.087, +0.231] | 0.00 | NO |
| 30% | add | +0.215 | +0.189 | -0.384 | +0.080 | +25.6 | [-0.145, +0.314] | 0.00 | NO |
| 50% | add | +0.285 | +0.198 | -0.664 | +0.070 | +46.2 | [-0.272, +0.427] | 0.00 | NO |
| 10% | const | +0.098 | +0.103 | -0.134 | +0.046 | -2.3 | [-0.043, +0.140] | 0.00 | NO |
| 20% | const | +0.190 | +0.176 | -0.316 | +0.076 | -3.7 | [-0.115, +0.275] | 0.00 | NO |
| 30% | const | +0.265 | +0.202 | -0.563 | +0.078 | -2.8 | [-0.226, +0.396] | 0.00 | NO |
| 50% | const | +0.324 | +0.075 | -1.338 | -0.046 | -1.1 | [-0.602, +0.521] | 0.00 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,267,941, Sharpe 1.39, maxDD 339,309, worst wk -124,396; H1: net 444,496, Sharpe 1.93, maxDD 220,853, worst wk -92,582; H2: net -384,559, Sharpe -1.69, maxDD 477,654, worst wk -84,073; all: net 1,327,878, Sharpe 0.96, maxDD 477,654, worst wk -124,396
Correlation with pair (weekly): clean +0.28, H1 +0.32, H2 +0.01, all +0.22; worst-decile weeks (n=17) corr -0.11, sleeve mean in those weeks $-22,626, positive share 0.24.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.62 | 3.16 | 5.56 | -90,424 | -85,096 | 284,888 | -95,762 | 41.9 |
| clean | add 30% | 1.68 | 3.30 | 5.95 | -96,557 | -88,657 | 287,278 | -103,625 | 42.9 |
| clean | const 20% | 1.65 | 3.23 | 5.76 | -74,792 | -69,501 | 228,866 | -79,495 | 42.9 |
| clean | const 30% | 1.72 | 3.43 | 6.45 | -73,110 | -65,434 | 203,245 | -80,200 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.98 | 6.60 | 4.45 | -81,654 | -71,698 | 153,437 | -87,804 | 35.7 |
| H1 | add 30% | 3.02 | 6.75 | 4.71 | -83,676 | -74,533 | 154,299 | -92,562 | 39.3 |
| H1 | const 20% | 3.00 | 6.68 | 4.58 | -66,132 | -58,493 | 123,094 | -72,146 | 35.7 |
| H1 | const 30% | 3.03 | 6.83 | 4.96 | -60,393 | -54,724 | 110,794 | -69,075 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.05 | 3.97 | 3.07 | -87,834 | -82,667 | 228,178 | -93,959 | 43.2 |
| H2 | add 30% | 1.91 | 3.62 | 2.84 | -93,110 | -86,521 | 233,555 | -102,365 | 45.9 |
| H2 | const 20% | 1.98 | 3.80 | 2.96 | -72,377 | -67,365 | 184,693 | -78,530 | 43.2 |
| H2 | const 30% | 1.73 | 3.18 | 2.53 | -70,402 | -64,732 | 169,545 | -79,221 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.93 | 3.79 | 10.42 | -89,557 | -84,120 | 284,888 | -95,762 | 41.4 |
| all | add 30% | 1.94 | 3.83 | 10.79 | -95,347 | -87,568 | 287,278 | -103,625 | 43.2 |
| all | const 20% | 1.93 | 3.81 | 10.61 | -73,962 | -68,602 | 228,866 | -79,495 | 42.0 |
| all | const 30% | 1.94 | 3.83 | 11.27 | -72,060 | -64,730 | 203,245 | -80,200 | 43.2 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.160 / +0.156 / -0.249
- [PASS] 3 worst week within share: all-in worst week +16.0% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.96 vs p95 0.74 (rank 0.98)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.087, +0.231]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.152 / +0.149 / -0.253
- [PASS] 6 worst-decile corr <=+0.30: -0.11
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_NQ); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (670 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2190 | +0.0672 | 0.73 |
| fixed | 2190 | +0.0342 | 0.37 |
| scaled | 2190 | +0.0342 | 0.37 |

Plateau neighbours (all-in 20% uplift; selected +0.069):
- {'sym': 'NQ', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.156 (trades 1532)
- {'sym': 'NQ', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '0.75', 'R': '2.0'}: +0.079 (trades 707)
- {'sym': 'NQ', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '1.5'}: +0.063 (trades 703)
- {'sym': 'NQ', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '3.125', 'tf': '30', 'S': '1.0', 'R': '2.0'}: +0.041 (trades 329)
- {'sym': 'NQ', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.25', 'R': '2.0'}: +0.048 (trades 654)
- {'sym': 'NQ', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '2.5'}: +0.099 (trades 658)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.06, p95 0.74, real 0.96. Standalone Sharpe at 2x slippage 0.92.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 223 | -22 | -0.94 |
| 2014 | 225 | -12 | -0.51 |
| 2015 | 248 | -8 | -0.36 |
| 2016 | 206 | -2 | -0.14 |
| 2017 | 220 | 4 | 0.19 |
| 2018 | 224 | 27 | 1.68 |
| 2019 | 214 | 7 | 0.37 |
| 2020 | 177 | 9 | 0.48 |
| 2021 | 212 | 33 | 1.79 |
| 2022 | 241 | 39 | 1.78 |
| 2023 | 217 | 43 | 2.31 |
| 2024 | 235 | 40 | 1.59 |
| 2025 | 195 | 19 | 0.99 |
| 2026 | 140 | -16 | -1.26 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.39 | +0.16/+0.16/-0.25 |
| 2 tick entry / 2 tick exit | 1.34 | +0.15/+0.15/-0.29 |
| 3 tick entry / 3 tick exit | 1.21 | +0.12/+0.12/-0.29 |

DONE RU9_NQ