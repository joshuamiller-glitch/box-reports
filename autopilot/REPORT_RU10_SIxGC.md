# REPORT RU10_SIxGC
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=1, sess=ALL, ent=stop, k=2.0, tf=15, S=1.0, R=2.0, partner=GC; additive @20% clean/H1/H2 -0.16/+0.06/+0.09; standalone all-in weekly Sharpe 0.02 (2013-26 -0.45, dev 2013-22 -0.82); pair-window trades 1426. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU10 displacement continuation confirmed by a same-direction displacement (range >= 1 ATR) in the partner market. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R | partner   |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|:----------|-----:|---------:|---------:|-------:|:-----------|
| SI    |    1 |      1 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | GC        |  809 |   -0.548 |  -27.485 |      1 | True       |
| SI    |    1 |      1 | ALL    | mkt   | 2.000 |   15 | 1.000 | 2.000 | GC        |  922 |   -0.762 |  -44.317 |      1 | True       |
| SI    |    1 |      1 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | GC        | 1503 |   -1.083 |  -72.169 |      0 | True       |
| SI    |    1 |      1 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | GC        | 1142 |   -1.354 |  -76.373 |      0 | True       |
| SI    |    1 |      1 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | GC        | 1677 |   -1.808 | -124.046 |      0 | True       |
| SI    |    1 |      1 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 | GC        |  579 |   -1.973 |  -68.532 |      0 | True       |
| SI    |    1 |      1 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | GC        | 1017 |   -2.097 | -115.312 |      0 | True       |
| SI    |    1 |      1 | ALL    | stop  | 2.000 |   30 | 1.000 | 2.000 | GC        |  505 |   -2.711 |  -91.296 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.55; replicate best-eligible median -0.37, p95 0.27; real beats 35% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.816e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.077 | +0.059 | +0.063 | -0.028 | +13.6 | [-0.131, +0.077] | 0.11 | NO |
| 20% | add | -0.163 | +0.058 | +0.088 | -0.077 | +33.6 | [-0.276, +0.126] | 0.11 | NO |
| 30% | add | -0.255 | +0.002 | +0.081 | -0.142 | +53.7 | [-0.433, +0.150] | 0.11 | NO |
| 50% | add | -0.443 | -0.217 | +0.007 | -0.296 | +93.9 | [-0.743, +0.155] | 0.11 | NO |
| 10% | const | -0.086 | +0.062 | +0.068 | -0.033 | +4.2 | [-0.147, +0.083] | 0.11 | NO |
| 20% | const | -0.208 | +0.036 | +0.088 | -0.108 | +15.0 | [-0.354, +0.141] | 0.11 | NO |
| 30% | const | -0.376 | -0.128 | +0.040 | -0.239 | +25.7 | [-0.634, +0.162] | 0.11 | NO |
| 50% | const | -0.848 | -0.854 | -0.273 | -0.675 | +47.2 | [-1.379, +0.040] | 0.11 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -499,054, Sharpe -0.55, maxDD 1,098,255, worst wk -121,919; H1: net 99,858, Sharpe 0.33, maxDD 340,449, worst wk -149,346; H2: net 429,674, Sharpe 0.96, maxDD 336,838, worst wk -165,734; all: net 30,478, Sharpe 0.02, maxDD 1,098,255, worst wk -165,734
Correlation with pair (weekly): clean +0.11, H1 -0.10, H2 +0.14, all +0.09; worst-decile weeks (n=17) corr -0.12, sleeve mean in those weeks $1,832, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.30 | 2.43 | 3.65 | -89,242 | -83,796 | 336,792 | -103,127 | 46.7 |
| clean | add 30% | 1.20 | 2.22 | 3.04 | -96,014 | -88,743 | 388,061 | -113,753 | 42.9 |
| clean | const 20% | 1.25 | 2.33 | 3.33 | -73,797 | -69,015 | 289,941 | -86,752 | 44.8 |
| clean | const 30% | 1.08 | 1.96 | 2.45 | -74,091 | -66,572 | 318,490 | -89,191 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.89 | 6.11 | 3.88 | -72,820 | -70,575 | 158,017 | -73,901 | 42.9 |
| H1 | add 30% | 2.83 | 5.92 | 3.87 | -79,191 | -73,014 | 161,169 | -86,674 | 39.3 |
| H1 | const 20% | 2.86 | 6.03 | 3.88 | -60,804 | -57,436 | 127,674 | -63,365 | 39.3 |
| H1 | const 30% | 2.70 | 5.57 | 3.46 | -61,167 | -53,305 | 128,909 | -74,113 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.39 | 4.91 | 4.05 | -95,659 | -82,573 | 213,569 | -110,294 | 35.1 |
| H2 | add 30% | 2.38 | 4.89 | 4.29 | -110,125 | -88,194 | 211,641 | -126,867 | 37.8 |
| H2 | const 20% | 2.39 | 4.91 | 4.17 | -82,314 | -67,791 | 170,084 | -94,864 | 37.8 |
| H2 | const 30% | 2.34 | 4.74 | 4.48 | -90,108 | -70,205 | 150,507 | -103,723 | 37.8 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.78 | 3.45 | 8.04 | -89,505 | -82,217 | 336,792 | -110,294 | 43.8 |
| all | add 30% | 1.72 | 3.29 | 6.99 | -98,112 | -87,490 | 388,061 | -126,867 | 41.4 |
| all | const 20% | 1.75 | 3.38 | 7.48 | -74,836 | -67,761 | 289,941 | -94,864 | 42.6 |
| all | const 30% | 1.62 | 3.06 | 5.97 | -77,653 | -67,160 | 318,490 | -103,723 | 40.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.163 / +0.058 / +0.088
- [FAIL] 3 worst week within share: all-in worst week +33.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.02 vs p95 -0.15 (rank 0.98)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.276, +0.126]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.242 / -0.000 / +0.042
- [PASS] 6 worst-decile corr <=+0.30: -0.12
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU10_SIxGC); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1426 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2066 | -0.0272 | -0.37 |
| fixed | 2066 | -0.0609 | -0.82 |
| scaled | 2066 | -0.0609 | -0.82 |

Plateau neighbours (all-in 20% uplift; selected -0.077):
- {'sym': 'SI', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '2.0', 'partner': 'GC'}: -0.223 (trades 2830)
- {'sym': 'SI', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '0.75', 'R': '2.0', 'partner': 'GC'}: -0.167 (trades 1442)
- {'sym': 'SI', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '1.5', 'partner': 'GC'}: -0.104 (trades 1493)
- {'sym': 'SI', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.0', 'partner': 'GC', 'L': '15'}: -0.106 (trades 1420)
- {'sym': 'SI', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.0', 'R': '2.0', 'partner': 'GC'}: -0.082 (trades 669)
- {'sym': 'SI', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.25', 'R': '2.0', 'partner': 'GC'}: -0.083 (trades 1403)
- {'sym': 'SI', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.5', 'partner': 'GC'}: -0.134 (trades 1385)
- {'sym': 'SI', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.0', 'partner': 'GC', 'L': '25'}: -0.071 (trades 1432)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.94, p95 -0.15, real 0.02. Standalone Sharpe at 2x slippage -0.29.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 312 | -19 | -1.06 |
| 2014 | 164 | 7 | 0.54 |
| 2015 | 158 | -37 | -3.05 |
| 2016 | 187 | -5 | -0.35 |
| 2017 | 77 | -9 | -1.43 |
| 2018 | 36 | -4 | -0.91 |
| 2019 | 84 | -6 | -0.93 |
| 2020 | 294 | -18 | -0.83 |
| 2021 | 400 | -21 | -0.88 |
| 2022 | 354 | -14 | -0.67 |
| 2023 | 363 | -30 | -1.16 |
| 2024 | 427 | -2 | -0.10 |
| 2025 | 427 | 18 | 0.62 |
| 2026 | 430 | 16 | 0.60 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.55 | -0.16/+0.06/+0.09 |
| 2 tick entry / 2 tick exit | -1.82 | -0.41/-0.05/-0.04 |
| 3 tick entry / 3 tick exit | -2.85 | -0.61/-0.18/-0.11 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.20 | -0.07/+0.08/+0.02 |

DONE RU10_SIxGC