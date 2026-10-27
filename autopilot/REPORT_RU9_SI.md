# REPORT RU9_SI
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=2, conf=0, sess=ALL, ent=mkt, k=1.5, tf=15, S=1.0, R=2.0; additive @20% clean/H1/H2 -0.20/+0.26/-0.47; standalone all-in weekly Sharpe -0.59 (2013-26 -0.98, dev 2013-22 -1.20); pair-window trades 3740. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|---------:|-------:|:-----------|
| SI    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 1945 |   -0.787 |  -48.481 |      1 | True       |
| SI    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  368 |   -1.146 |  -38.532 |      0 | True       |
| SI    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  445 |   -1.216 |  -43.733 |      0 | True       |
| SI    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  595 |   -1.240 |  -50.763 |      0 | True       |
| SI    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1207 |   -1.725 |  -94.457 |      0 | True       |
| SI    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1306 |   -1.830 | -108.144 |      0 | True       |
| SI    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  779 |   -2.135 | -101.166 |      0 | True       |
| SI    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 1764 |   -2.305 | -145.161 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.79; replicate best-eligible median -0.11, p95 0.43; real beats 0% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.479e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.098 | +0.187 | -0.229 | -0.100 | +15.9 | [-0.211, +0.017] | 0.26 | NO |
| 20% | add | -0.205 | +0.263 | -0.471 | -0.221 | +38.0 | [-0.441, +0.005] | 0.26 | NO |
| 30% | add | -0.316 | +0.215 | -0.709 | -0.355 | +60.1 | [-0.675, -0.030] | 0.26 | NO |
| 50% | add | -0.539 | -0.126 | -1.135 | -0.631 | +112.4 | [-1.121, -0.134] | 0.26 | NO |
| 10% | const | -0.109 | +0.202 | -0.256 | -0.112 | +6.5 | [-0.236, +0.017] | 0.26 | NO |
| 20% | const | -0.260 | +0.254 | -0.591 | -0.287 | +19.2 | [-0.558, -0.012] | 0.26 | NO |
| 30% | const | -0.461 | +0.018 | -0.992 | -0.534 | +34.3 | [-0.968, -0.089] | 0.26 | NO |
| 50% | const | -1.004 | -1.020 | -1.849 | -1.185 | +78.3 | [-1.917, -0.416] | 0.26 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -717,046, Sharpe -0.79, maxDD 958,633, worst wk -205,818; H1: net 118,304, Sharpe 0.29, maxDD 576,442, worst wk -201,192; H2: net -482,973, Sharpe -0.97, maxDD 949,484, worst wk -238,003; all: net -1,081,716, Sharpe -0.59, maxDD 1,222,687, worst wk -238,003
Correlation with pair (weekly): clean +0.09, H1 -0.32, H2 +0.22, all +0.05; worst-decile weeks (n=17) corr -0.24, sleeve mean in those weeks $-12,762, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.26 | 2.31 | 3.32 | -88,089 | -82,474 | 357,818 | -99,751 | 46.7 |
| clean | add 30% | 1.14 | 2.07 | 2.64 | -94,432 | -86,352 | 422,812 | -111,050 | 46.7 |
| clean | const 20% | 1.20 | 2.19 | 2.95 | -72,978 | -67,283 | 312,252 | -84,321 | 47.6 |
| clean | const 30% | 1.00 | 1.77 | 2.02 | -72,853 | -65,674 | 354,462 | -87,905 | 47.6 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.09 | 6.52 | 4.29 | -68,527 | -66,555 | 143,997 | -69,944 | 35.7 |
| H1 | add 30% | 3.04 | 6.39 | 4.31 | -72,750 | -66,984 | 146,033 | -79,728 | 32.1 |
| H1 | const 20% | 3.08 | 6.48 | 4.30 | -56,511 | -53,415 | 116,012 | -58,735 | 32.1 |
| H1 | const 30% | 2.85 | 5.95 | 4.34 | -54,727 | -48,340 | 104,055 | -67,167 | 39.3 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 1.83 | 3.25 | 2.15 | -108,893 | -100,157 | 316,492 | -113,881 | 40.5 |
| H2 | add 30% | 1.59 | 2.68 | 1.66 | -129,910 | -115,679 | 380,767 | -132,113 | 40.5 |
| H2 | const 20% | 1.71 | 2.95 | 1.89 | -95,521 | -86,335 | 278,903 | -98,398 | 43.2 |
| H2 | const 30% | 1.31 | 2.09 | 1.23 | -109,852 | -95,573 | 324,384 | -110,814 | 37.8 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.64 | 3.02 | 6.95 | -94,613 | -85,391 | 357,818 | -113,881 | 43.8 |
| all | add 30% | 1.50 | 2.69 | 5.62 | -105,178 | -92,610 | 422,812 | -132,113 | 43.2 |
| all | const 20% | 1.57 | 2.85 | 6.23 | -79,882 | -70,812 | 312,252 | -98,398 | 44.4 |
| all | const 30% | 1.32 | 2.29 | 4.42 | -84,329 | -73,364 | 354,462 | -110,814 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.205 / +0.263 / -0.471
- [FAIL] 3 worst week within share: all-in worst week +38.0% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real -0.59 vs p95 -0.71 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.441, +0.005]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.362 / +0.094 / -0.576
- [PASS] 6 worst-decile corr <=+0.30: -0.24
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_SI); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3740 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 5016 | -0.0240 | -0.51 |
| fixed | 5016 | -0.0577 | -1.20 |
| scaled | 5016 | -0.0577 | -1.20 |

Plateau neighbours (all-in 20% uplift; selected -0.221):
- {'sym': 'SI', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.125', 'tf': '15', 'S': '1.0', 'R': '2.0'}: -0.562 (trades 5343)
- {'sym': 'SI', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '0.75', 'R': '2.0'}: -0.305 (trades 3856)
- {'sym': 'SI', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '1.5'}: -0.359 (trades 4050)
- {'sym': 'SI', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '15', 'S': '1.0', 'R': '2.0'}: -0.166 (trades 2359)
- {'sym': 'SI', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '1.25', 'R': '2.0'}: -0.248 (trades 3589)
- {'sym': 'SI', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '2.5'}: -0.311 (trades 3494)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.50, p95 -0.71, real -0.59. Standalone Sharpe at 2x slippage -1.17.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 827 | -59 | -1.51 |
| 2014 | 431 | -33 | -1.65 |
| 2015 | 369 | -62 | -3.07 |
| 2016 | 439 | -28 | -1.75 |
| 2017 | 172 | -11 | -0.91 |
| 2018 | 82 | -3 | -0.56 |
| 2019 | 179 | 15 | 1.51 |
| 2020 | 878 | -20 | -0.59 |
| 2021 | 795 | -66 | -2.11 |
| 2022 | 844 | -23 | -0.79 |
| 2023 | 736 | -58 | -2.13 |
| 2024 | 1004 | 7 | 0.21 |
| 2025 | 1234 | -21 | -0.49 |
| 2026 | 1211 | -22 | -0.59 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.79 | -0.20/+0.26/-0.47 |
| 2 tick entry / 2 tick exit | -2.89 | -0.61/-0.24/-0.73 |
| 3 tick entry / 3 tick exit | -5.09 | -1.03/-0.76/-1.01 |

DONE RU9_SI