# REPORT RU6_GC
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=RTH, ent=stop, k=1.5, tf=15, S=1.5, R=2.0; additive @20% clean/H1/H2 +0.16/-0.09/-0.34; standalone all-in weekly Sharpe 0.32 (2013-26 -0.04, dev 2013-22 -0.24); pair-window trades 903. Runtime 0.0 min (+selection 0.1 min). 10-worker pool.

RU6 session split of the RU2 selected cell (ALL / RTH / non-RTH by placement time). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 40 clean trades): 3. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |    net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|-------:|-------:|:-----------|
| GC    |    1 |      0 | RTH    | stop  | 1.500 |   15 | 1.500 | 2.000 |  555 |    1.093 | 46.155 |      3 | True       |
| GC    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 1915 |    0.939 | 66.329 |      2 | True       |
| GC    |    1 |      0 | NRTH   | stop  | 1.500 |   15 | 1.500 | 2.000 | 1449 |    0.367 | 24.314 |      2 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.09; replicate best-eligible median 0.10, p95 0.82; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.157e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.090 | -0.018 | -0.165 | +0.015 | +4.6 | [-0.083, +0.112] | 0.30 | NO |
| 20% | add | +0.163 | -0.094 | -0.344 | +0.009 | +15.7 | [-0.184, +0.199] | 0.30 | NO |
| 30% | add | +0.219 | -0.216 | -0.529 | -0.016 | +26.8 | [-0.298, +0.262] | 0.30 | NO |
| 50% | add | +0.285 | -0.537 | -0.895 | -0.103 | +48.9 | [-0.542, +0.325] | 0.30 | NO |
| 10% | const | +0.099 | -0.024 | -0.184 | +0.015 | -4.8 | [-0.094, +0.123] | 0.30 | NO |
| 20% | const | +0.193 | -0.150 | -0.436 | -0.001 | -3.0 | [-0.239, +0.231] | 0.30 | NO |
| 30% | const | +0.268 | -0.416 | -0.766 | -0.067 | -1.3 | [-0.455, +0.314] | 0.30 | NO |
| 50% | const | +0.283 | -1.290 | -1.648 | -0.391 | +8.9 | [-1.098, +0.289] | 0.30 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 995,637, Sharpe 1.09, maxDD 465,016, worst wk -155,427; H1: net -47,696, Sharpe -0.16, maxDD 371,804, worst wk -163,615; H2: net -451,232, Sharpe -1.32, maxDD 558,510, worst wk -156,028; all: net 496,708, Sharpe 0.32, maxDD 674,427, worst wk -163,615
Correlation with pair (weekly): clean +0.07, H1 -0.08, H2 +0.10, all +0.04; worst-decile weeks (n=17) corr +0.18, sleeve mean in those weeks $-4,295, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.62 | 3.14 | 6.33 | -86,176 | -81,031 | 241,638 | -95,465 | 43.8 |
| clean | add 30% | 1.68 | 3.26 | 6.33 | -90,530 | -83,136 | 257,260 | -104,613 | 41.0 |
| clean | const 20% | 1.65 | 3.20 | 6.33 | -70,614 | -65,667 | 199,559 | -80,031 | 41.9 |
| clean | const 30% | 1.73 | 3.35 | 6.30 | -69,221 | -61,417 | 195,117 | -81,461 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.73 | 5.68 | 3.41 | -73,399 | -67,276 | 171,387 | -78,396 | 35.7 |
| H1 | add 30% | 2.61 | 5.36 | 3.20 | -71,294 | -68,065 | 181,224 | -78,450 | 35.7 |
| H1 | const 20% | 2.68 | 5.53 | 3.30 | -57,877 | -54,137 | 141,045 | -62,738 | 35.7 |
| H1 | const 30% | 2.41 | 4.90 | 2.93 | -52,006 | -49,191 | 137,190 | -54,963 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 1.95 | 3.78 | 2.96 | -89,161 | -84,293 | 232,830 | -89,300 | 45.9 |
| H2 | add 30% | 1.77 | 3.35 | 2.63 | -93,197 | -87,635 | 244,482 | -94,123 | 45.9 |
| H2 | const 20% | 1.86 | 3.56 | 2.79 | -72,943 | -68,456 | 190,925 | -73,369 | 45.9 |
| H2 | const 30% | 1.53 | 2.83 | 2.25 | -68,870 | -65,559 | 181,625 | -70,227 | 48.6 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.87 | 3.62 | 11.59 | -86,270 | -81,169 | 241,638 | -95,465 | 43.2 |
| all | add 30% | 1.84 | 3.56 | 11.08 | -90,569 | -83,672 | 257,260 | -104,613 | 41.4 |
| all | const 20% | 1.86 | 3.60 | 11.33 | -70,566 | -65,936 | 199,559 | -80,031 | 42.0 |
| all | const 30% | 1.79 | 3.43 | 10.46 | -68,747 | -61,967 | 195,117 | -81,461 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.163 / -0.094 / -0.344
- [PASS] 3 worst week within share: all-in worst week +15.7% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.32 vs p95 0.63 (rank 0.85)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.184, +0.199]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 38% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.129 / -0.113 / -0.354
- [PASS] 6 worst-decile corr <=+0.30: +0.18
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU6_GC); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (903 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2132 | +0.0145 | 0.18 |
| fixed | 2132 | -0.0188 | -0.24 |
| scaled | 2132 | -0.0188 | -0.24 |

Plateau neighbours (all-in 20% uplift; selected +0.009):
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.125', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.101 (trades 1429)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.125', 'R': '2.0'}: +0.015 (trades 998)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.5'}: +0.022 (trades 964)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '15'}: +0.003 (trades 900)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.875', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.077 (trades 510)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.875', 'R': '2.0'}: -0.060 (trades 841)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.5'}: -0.025 (trades 878)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '25'}: +0.009 (trades 903)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.08, p95 0.63, real 0.32. Standalone Sharpe at 2x slippage 0.19.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 191 | 12 | 0.72 |
| 2014 | 181 | -19 | -1.49 |
| 2015 | 168 | -5 | -0.26 |
| 2016 | 235 | -29 | -1.73 |
| 2017 | 220 | -22 | -1.51 |
| 2018 | 210 | -9 | -0.62 |
| 2019 | 221 | -7 | -0.35 |
| 2020 | 244 | 15 | 0.72 |
| 2021 | 231 | -17 | -1.01 |
| 2022 | 231 | 41 | 2.33 |
| 2023 | 287 | 25 | 1.14 |
| 2024 | 278 | 23 | 1.11 |
| 2025 | 284 | -1 | -0.05 |
| 2026 | 213 | -16 | -0.84 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.09 | +0.16/-0.09/-0.34 |
| 2 tick entry / 2 tick exit | 0.63 | +0.08/-0.12/-0.43 |
| 3 tick entry / 3 tick exit | 0.00 | -0.04/-0.08/-0.51 |
| retrace-limit DISP (b=1.5, tf15, f=0.5, RZ geometry) | -0.49 | -0.13/+0.47/-0.02 |

DONE RU6_GC