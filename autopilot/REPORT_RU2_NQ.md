# REPORT RU2_NQ
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=1.5, tf=15, S=1.5, R=2.0; additive @20% clean/H1/H2 +0.28/-0.25/-0.03; standalone all-in weekly Sharpe 1.03 (2013-26 0.47, dev 2013-22 0.25); pair-window trades 3641. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| NQ    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 2326 |    1.654 | 130.480 |      3 | True       |
| NQ    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 | 1161 |    1.557 |  87.027 |      3 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.000 | 2.000 | 1385 |    1.318 |  89.539 |      2 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 2.000 | 1276 |    1.299 |  81.382 |      3 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 2.000 | 1421 |    1.203 |  74.004 |      2 | True       |
| NQ    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 1.000 | 1262 |    1.187 |  53.487 |      3 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 1.000 |  862 |    1.175 |  45.548 |      2 | True       |
| NQ    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 2.000 | 1290 |    1.124 |  68.916 |      2 | True       |
| NQ    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 1.000 | 1865 |    1.035 |  58.913 |      2 | True       |
| NQ    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 1.000 | 2813 |    0.962 |  73.819 |      3 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.65; replicate best-eligible median 0.74, p95 1.62; real beats 95% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.155e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.151 | -0.120 | -0.003 | +0.084 | +8.7 | [-0.015, +0.184] | 0.25 | NO |
| 20% | add | +0.283 | -0.246 | -0.034 | +0.146 | +22.6 | [-0.047, +0.342] | 0.25 | NO |
| 30% | add | +0.394 | -0.372 | -0.089 | +0.187 | +36.4 | [-0.097, +0.474] | 0.25 | NO |
| 50% | add | +0.554 | -0.610 | -0.254 | +0.214 | +64.1 | [-0.224, +0.658] | 0.25 | NO |
| 10% | const | +0.167 | -0.133 | -0.006 | +0.092 | -0.8 | [-0.017, +0.203] | 0.25 | NO |
| 20% | const | +0.341 | -0.309 | -0.059 | +0.169 | +3.6 | [-0.069, +0.411] | 0.25 | NO |
| 30% | const | +0.506 | -0.528 | -0.189 | +0.211 | +8.0 | [-0.176, +0.603] | 0.25 | NO |
| 50% | const | +0.700 | -1.071 | -0.749 | +0.111 | +16.7 | [-0.602, +0.829] | 0.25 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,506,736, Sharpe 1.65, maxDD 329,977, worst wk -128,982; H1: net 81,420, Sharpe 0.34, maxDD 269,259, worst wk -114,321; H2: net -33,599, Sharpe -0.09, maxDD 496,740, worst wk -188,633; all: net 1,554,557, Sharpe 1.03, maxDD 496,740, worst wk -188,633
Correlation with pair (weekly): clean +0.04, H1 +0.48, H2 -0.08, all +0.06; worst-decile weeks (n=17) corr +0.16, sleeve mean in those weeks $17,622, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.74 | 3.48 | 6.24 | -80,073 | -75,674 | 261,267 | -87,980 | 41.9 |
| clean | add 30% | 1.85 | 3.78 | 6.65 | -81,046 | -76,419 | 267,831 | -93,190 | 40.0 |
| clean | const 20% | 1.80 | 3.64 | 6.48 | -64,448 | -60,483 | 210,568 | -72,468 | 41.0 |
| clean | const 30% | 1.97 | 4.08 | 7.06 | -59,302 | -55,254 | 195,799 | -69,923 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.58 | 5.12 | 4.02 | -94,848 | -79,027 | 151,689 | -101,152 | 39.3 |
| H1 | add 30% | 2.46 | 4.71 | 3.74 | -103,467 | -86,553 | 165,308 | -112,584 | 35.7 |
| H1 | const 20% | 2.52 | 4.91 | 3.96 | -79,326 | -65,887 | 124,086 | -85,494 | 39.3 |
| H1 | const 30% | 2.30 | 4.27 | 3.28 | -80,184 | -68,449 | 134,077 | -89,098 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.26 | 4.63 | 3.42 | -80,714 | -76,669 | 225,601 | -81,919 | 43.2 |
| H2 | add 30% | 2.21 | 4.51 | 3.29 | -81,580 | -78,050 | 233,640 | -83,052 | 37.8 |
| H2 | const 20% | 2.24 | 4.58 | 3.35 | -64,497 | -61,888 | 183,697 | -65,989 | 40.5 |
| H2 | const 30% | 2.11 | 4.29 | 3.13 | -61,186 | -56,520 | 170,782 | -63,216 | 40.5 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 2.00 | 4.01 | 11.53 | -83,992 | -78,164 | 261,267 | -101,152 | 42.0 |
| all | add 30% | 2.05 | 4.11 | 11.83 | -86,933 | -79,985 | 267,831 | -112,584 | 39.1 |
| all | const 20% | 2.03 | 4.07 | 11.74 | -68,236 | -63,030 | 210,568 | -85,494 | 40.8 |
| all | const 30% | 2.07 | 4.17 | 12.04 | -64,916 | -58,485 | 195,799 | -89,098 | 40.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.283 / -0.246 / -0.034
- [FAIL] 3 worst week within share: all-in worst week +22.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.03 vs p95 0.39 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.047, +0.342]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 38% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.253 / -0.269 / -0.047
- [PASS] 6 worst-decile corr <=+0.30: +0.16
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_NQ); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3641 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 9687 | +0.0424 | 1.01 |
| fixed | 9687 | +0.0105 | 0.25 |
| scaled | 9687 | +0.0105 | 0.25 |

Plateau neighbours (all-in 20% uplift; selected +0.146):
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.125', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.049 (trades 5344)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.125', 'R': '2.0'}: -0.028 (trades 4194)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.5'}: +0.103 (trades 3939)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '15'}: +0.146 (trades 3643)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.875', 'tf': '15', 'S': '1.5', 'R': '2.0'}: +0.067 (trades 2100)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.875', 'R': '2.0'}: +0.058 (trades 3181)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.5'}: +0.113 (trades 3410)
- {'sym': 'NQ', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '25'}: +0.136 (trades 3635)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.45, p95 0.39, real 1.03. Standalone Sharpe at 2x slippage 0.90.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 739 | -115 | -3.00 |
| 2014 | 834 | -22 | -0.55 |
| 2015 | 1020 | -82 | -2.07 |
| 2016 | 980 | -23 | -0.52 |
| 2017 | 896 | 27 | 0.66 |
| 2018 | 1061 | 23 | 0.63 |
| 2019 | 995 | 55 | 1.30 |
| 2020 | 978 | 122 | 2.78 |
| 2021 | 1053 | 53 | 1.43 |
| 2022 | 1131 | 64 | 1.49 |
| 2023 | 1172 | 66 | 1.62 |
| 2024 | 1193 | 82 | 2.05 |
| 2025 | 1084 | 25 | 0.68 |
| 2026 | 858 | -9 | -0.27 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.65 | +0.28/-0.25/-0.03 |
| 2 tick entry / 2 tick exit | 1.27 | +0.22/-0.29/-0.07 |
| 3 tick entry / 3 tick exit | 0.62 | +0.09/-0.32/-0.12 |
| retrace-limit DISP (b=1.5, tf15, f=0.5, RZ geometry) | 0.20 | -0.00/-0.05/+0.00 |

DONE RU2_NQ