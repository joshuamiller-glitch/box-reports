# REPORT RU9_HO
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0; additive @20% clean/H1/H2 +0.09/+0.19/+0.10; standalone all-in weekly Sharpe 0.80 (2013-26 0.18, dev 2013-22 0.13); pair-window trades 748. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|---------:|-------:|:-----------|
| HO    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  489 |    0.506 |   22.371 |      3 | True       |
| HO    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 | 1256 |    0.244 |   16.490 |      2 | True       |
| HO    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  634 |   -0.130 |   -6.436 |      1 | True       |
| HO    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  974 |   -0.257 |  -16.870 |      1 | True       |
| HO    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1933 |   -0.829 |  -70.904 |      0 | True       |
| HO    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1663 |   -1.222 |  -87.819 |      0 | True       |
| HO    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 3164 |   -1.709 | -194.622 |      1 | True       |
| HO    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 3850 |   -2.028 | -256.100 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.51; replicate best-eligible median 0.66, p95 1.30; real beats 45% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.062e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.052 | +0.114 | +0.057 | +0.066 | +9.8 | [-0.024, +0.159] | 0.41 | NO |
| 20% | add | +0.088 | +0.188 | +0.098 | +0.113 | +25.4 | [-0.065, +0.297] | 0.41 | NO |
| 30% | add | +0.109 | +0.227 | +0.126 | +0.142 | +41.0 | [-0.119, +0.414] | 0.41 | NO |
| 50% | add | +0.109 | +0.223 | +0.145 | +0.153 | +72.3 | [-0.256, +0.573] | 0.41 | NO |
| 10% | const | +0.057 | +0.124 | +0.062 | +0.072 | +0.4 | [-0.028, +0.175] | 0.41 | NO |
| 20% | const | +0.101 | +0.212 | +0.114 | +0.130 | +6.6 | [-0.090, +0.358] | 0.41 | NO |
| 30% | const | +0.115 | +0.235 | +0.143 | +0.155 | +12.8 | [-0.202, +0.526] | 0.41 | NO |
| 50% | const | -0.028 | +0.007 | +0.058 | +0.021 | +25.2 | [-0.670, +0.710] | 0.41 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 461,210, Sharpe 0.51, maxDD 387,426, worst wk -134,182; H1: net 363,524, Sharpe 1.51, maxDD 208,071, worst wk -76,472; H2: net 301,049, Sharpe 1.13, maxDD 237,321, worst wk -84,481; all: net 1,125,782, Sharpe 0.80, maxDD 387,426, worst wk -134,182
Correlation with pair (weekly): clean -0.06, H1 +0.12, H2 +0.14, all +0.01; worst-decile weeks (n=17) corr +0.10, sleeve mean in those weeks $-12,205, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.55 | 2.96 | 4.72 | -91,899 | -82,646 | 301,530 | -103,505 | 41.0 |
| clean | add 30% | 1.57 | 2.98 | 4.68 | -98,625 | -86,018 | 313,826 | -116,398 | 41.0 |
| clean | const 20% | 1.56 | 2.97 | 4.71 | -76,209 | -67,285 | 245,526 | -87,961 | 41.0 |
| clean | const 30% | 1.57 | 2.96 | 4.61 | -75,090 | -65,008 | 232,129 | -93,082 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.02 | 6.68 | 4.46 | -76,605 | -69,712 | 149,361 | -82,760 | 39.3 |
| H1 | add 30% | 3.05 | 6.80 | 4.74 | -76,102 | -71,553 | 148,186 | -84,996 | 39.3 |
| H1 | const 20% | 3.04 | 6.75 | 4.60 | -61,083 | -56,506 | 119,019 | -67,102 | 39.3 |
| H1 | const 30% | 3.06 | 6.84 | 5.11 | -55,551 | -51,744 | 102,672 | -61,510 | 32.1 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.40 | 4.94 | 3.63 | -84,773 | -82,163 | 230,917 | -85,591 | 37.8 |
| H2 | add 30% | 2.42 | 5.06 | 3.66 | -87,959 | -83,652 | 237,662 | -89,813 | 40.5 |
| H2 | const 20% | 2.41 | 5.00 | 3.64 | -69,093 | -66,326 | 187,432 | -70,162 | 37.8 |
| H2 | const 30% | 2.44 | 5.17 | 3.68 | -64,439 | -59,897 | 172,435 | -66,669 | 37.8 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.97 | 3.90 | 9.71 | -89,300 | -81,821 | 301,530 | -103,505 | 40.2 |
| all | add 30% | 2.00 | 3.96 | 9.69 | -94,740 | -84,319 | 313,826 | -116,398 | 40.8 |
| all | const 20% | 1.99 | 3.93 | 9.72 | -73,616 | -66,330 | 245,526 | -87,961 | 40.2 |
| all | const 30% | 2.01 | 3.98 | 9.60 | -71,214 | -62,693 | 232,129 | -93,082 | 39.6 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.088 / +0.188 / +0.098
- [FAIL] 3 worst week within share: all-in worst week +25.4% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.80 vs p95 0.56 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.065, +0.297]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 17% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.071 / +0.170 / +0.094
- [PASS] 6 worst-decile corr <=+0.30: +0.10
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_HO); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (748 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2438 | +0.0396 | 0.44 |
| fixed | 2438 | +0.0119 | 0.13 |
| scaled | 2438 | +0.0119 | 0.13 |

Plateau neighbours (all-in 20% uplift; selected +0.113):
- {'sym': 'HO', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.031 (trades 1846)
- {'sym': 'HO', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '0.75', 'R': '2.0'}: +0.069 (trades 775)
- {'sym': 'HO', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '1.5'}: +0.080 (trades 766)
- {'sym': 'HO', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '3.125', 'tf': '30', 'S': '1.0', 'R': '2.0'}: +0.002 (trades 268)
- {'sym': 'HO', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.25', 'R': '2.0'}: +0.100 (trades 720)
- {'sym': 'HO', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '2.5'}: +0.084 (trades 723)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.22, p95 0.56, real 0.80. Standalone Sharpe at 2x slippage 0.72.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 230 | 38 | 1.63 |
| 2014 | 248 | -20 | -1.00 |
| 2015 | 289 | 35 | 1.25 |
| 2016 | 256 | 15 | 0.52 |
| 2017 | 264 | 19 | 0.93 |
| 2018 | 248 | -36 | -1.68 |
| 2019 | 243 | -12 | -0.60 |
| 2020 | 201 | 3 | 0.19 |
| 2021 | 215 | 10 | 0.52 |
| 2022 | 244 | -23 | -1.07 |
| 2023 | 269 | -20 | -0.92 |
| 2024 | 248 | 13 | 0.54 |
| 2025 | 220 | 10 | 0.49 |
| 2026 | 170 | 24 | 1.59 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.51 | +0.09/+0.19/+0.10 |
| 2 tick entry / 2 tick exit | 0.09 | -0.01/+0.17/+0.09 |
| 3 tick entry / 3 tick exit | -0.10 | -0.05/+0.11/+0.09 |

DONE RU9_HO