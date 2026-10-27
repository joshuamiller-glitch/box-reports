# REPORT RU9_RB
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0; additive @20% clean/H1/H2 +0.06/-0.39/+0.04; standalone all-in weekly Sharpe 0.12 (2013-26 -0.41, dev 2013-22 -0.50); pair-window trades 676. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|---------:|-------:|:-----------|
| RB    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  426 |    0.391 |   16.140 |      1 | True       |
| RB    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  934 |   -0.305 |  -17.038 |      1 | True       |
| RB    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  651 |   -0.423 |  -22.800 |      2 | True       |
| RB    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1892 |   -0.957 |  -74.051 |      0 | True       |
| RB    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 | 1248 |   -1.210 |  -80.282 |      0 | True       |
| RB    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1632 |   -1.228 |  -92.921 |      0 | True       |
| RB    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 3753 |   -1.556 | -183.578 |      0 | True       |
| RB    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 3067 |   -2.277 | -244.355 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.39; replicate best-eligible median 0.37, p95 1.56; real beats 55% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.206e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.039 | -0.184 | +0.028 | +0.008 | +10.2 | [-0.083, +0.107] | 0.62 | NO |
| 20% | add | +0.063 | -0.389 | +0.042 | -0.002 | +26.9 | [-0.180, +0.195] | 0.62 | NO |
| 30% | add | +0.073 | -0.603 | +0.041 | -0.028 | +43.5 | [-0.289, +0.261] | 0.62 | NO |
| 50% | add | +0.052 | -1.020 | +0.000 | -0.119 | +76.9 | [-0.525, +0.336] | 0.62 | NO |
| 10% | const | +0.043 | -0.206 | +0.030 | +0.008 | +0.8 | [-0.093, +0.118] | 0.62 | NO |
| 20% | const | +0.070 | -0.496 | +0.043 | -0.013 | +8.2 | [-0.234, +0.231] | 0.62 | NO |
| 30% | const | +0.065 | -0.875 | +0.021 | -0.082 | +15.5 | [-0.439, +0.318] | 0.62 | NO |
| 50% | const | -0.116 | -1.820 | -0.259 | -0.432 | +30.1 | [-1.098, +0.297] | 0.62 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 356,117, Sharpe 0.39, maxDD 518,719, worst wk -137,578; H1: net -232,042, Sharpe -0.90, maxDD 421,038, worst wk -117,578; H2: net 42,195, Sharpe 0.16, maxDD 215,829, worst wk -111,525; all: net 166,270, Sharpe 0.12, maxDD 777,056, worst wk -137,578
Correlation with pair (weekly): clean -0.05, H1 +0.17, H2 -0.12, all -0.03; worst-decile weeks (n=17) corr +0.06, sleeve mean in those weeks $-1,654, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.52 | 2.81 | 4.75 | -92,027 | -84,672 | 294,835 | -104,686 | 41.9 |
| clean | add 30% | 1.53 | 2.77 | 4.20 | -99,203 | -88,725 | 342,025 | -118,444 | 41.9 |
| clean | const 20% | 1.53 | 2.80 | 4.46 | -76,452 | -69,278 | 254,744 | -89,252 | 42.9 |
| clean | const 30% | 1.52 | 2.68 | 3.68 | -75,989 | -66,697 | 281,888 | -95,293 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.44 | 4.70 | 2.80 | -89,366 | -81,140 | 195,223 | -91,018 | 42.9 |
| H1 | add 30% | 2.22 | 4.12 | 2.40 | -95,244 | -88,862 | 218,800 | -98,061 | 42.9 |
| H1 | const 20% | 2.33 | 4.40 | 2.60 | -73,844 | -68,001 | 164,881 | -75,631 | 42.9 |
| H1 | const 30% | 1.95 | 3.47 | 1.96 | -71,961 | -69,153 | 176,822 | -74,981 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.34 | 4.84 | 3.77 | -82,499 | -77,257 | 208,890 | -83,272 | 40.5 |
| H2 | add 30% | 2.34 | 4.88 | 3.87 | -83,831 | -76,740 | 204,622 | -84,017 | 45.9 |
| H2 | const 20% | 2.34 | 4.87 | 3.82 | -66,532 | -61,420 | 165,405 | -66,767 | 43.2 |
| H2 | const 30% | 2.32 | 4.84 | 4.00 | -59,881 | -54,852 | 139,395 | -60,873 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.86 | 3.53 | 9.28 | -90,843 | -83,661 | 294,835 | -104,686 | 42.0 |
| all | add 30% | 1.83 | 3.41 | 8.05 | -97,030 | -87,520 | 342,025 | -118,444 | 43.2 |
| all | const 20% | 1.85 | 3.47 | 8.62 | -75,149 | -68,305 | 254,744 | -89,252 | 43.2 |
| all | const 30% | 1.78 | 3.23 | 6.89 | -74,006 | -65,605 | 281,888 | -95,293 | 43.2 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.063 / -0.389 / +0.042
- [FAIL] 3 worst week within share: all-in worst week +26.9% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.12 vs p95 0.43 (rank 0.81)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.180, +0.195]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.045 / -0.416 / +0.033
- [PASS] 6 worst-decile corr <=+0.30: +0.06
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_RB); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (676 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2519 | -0.0169 | -0.19 |
| fixed | 2519 | -0.0437 | -0.50 |
| scaled | 2519 | -0.0437 | -0.50 |

Plateau neighbours (all-in 20% uplift; selected -0.002):
- {'sym': 'RB', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.309 (trades 1826)
- {'sym': 'RB', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '0.75', 'R': '2.0'}: -0.163 (trades 713)
- {'sym': 'RB', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '1.5'}: +0.009 (trades 707)
- {'sym': 'RB', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '3.125', 'tf': '30', 'S': '1.0', 'R': '2.0'}: +0.029 (trades 256)
- {'sym': 'RB', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.25', 'R': '2.0'}: -0.050 (trades 658)
- {'sym': 'RB', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '2.5'}: -0.074 (trades 663)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.34, p95 0.43, real 0.12. Standalone Sharpe at 2x slippage 0.02.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 266 | -22 | -1.08 |
| 2014 | 274 | -30 | -1.18 |
| 2015 | 276 | 4 | 0.18 |
| 2016 | 287 | -14 | -0.59 |
| 2017 | 270 | -9 | -0.44 |
| 2018 | 252 | -23 | -1.11 |
| 2019 | 247 | 7 | 0.33 |
| 2020 | 224 | -13 | -0.55 |
| 2021 | 204 | -6 | -0.27 |
| 2022 | 219 | -3 | -0.15 |
| 2023 | 244 | -26 | -1.14 |
| 2024 | 208 | 31 | 1.42 |
| 2025 | 222 | -18 | -1.01 |
| 2026 | 151 | 1 | 0.08 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.39 | +0.06/-0.39/+0.04 |
| 2 tick entry / 2 tick exit | 0.23 | +0.03/-0.43/+0.04 |
| 3 tick entry / 3 tick exit | 0.08 | -0.00/-0.44/-0.03 |

DONE RU9_RB