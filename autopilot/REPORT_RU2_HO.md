# REPORT RU2_HO
**Verdict: NO** (3/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.0, R=2.0; additive @20% clean/H1/H2 +0.15/-0.08/+0.15; standalone all-in weekly Sharpe 0.92 (2013-26 0.08, dev 2013-22 -0.19); pair-window trades 2162. Runtime 0.1 min (+selection 0.1 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | 1430 |    1.149 | 100.374 |      3 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 2.000 |  735 |    1.133 |  53.697 |      3 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 | 1314 |    0.789 |  61.931 |      2 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 1.000 | 1472 |    0.410 |  24.202 |      2 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 2.000 |  791 |    0.356 |  20.254 |      2 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 1.000 |  798 |    0.329 |  12.905 |      2 | True       |
| HO    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 2.000 | 1472 |    0.265 |  19.176 |      2 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 1.000 | 1435 |    0.086 |   5.126 |      1 | True       |
| HO    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 2614 |    0.015 |   1.507 |      2 | True       |
| HO    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | 3212 |    0.008 |   0.839 |      2 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.15; replicate best-eligible median 0.85, p95 1.08; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.043e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.081 | -0.031 | +0.083 | +0.061 | +6.2 | [-0.021, +0.150] | 0.10 | NO |
| 20% | add | +0.146 | -0.079 | +0.154 | +0.105 | +19.1 | [-0.055, +0.278] | 0.10 | NO |
| 30% | add | +0.193 | -0.143 | +0.209 | +0.133 | +32.0 | [-0.101, +0.384] | 0.10 | NO |
| 50% | add | +0.248 | -0.302 | +0.276 | +0.147 | +57.8 | [-0.224, +0.543] | 0.10 | NO |
| 10% | const | +0.089 | -0.036 | +0.092 | +0.067 | -3.1 | [-0.024, +0.166] | 0.10 | NO |
| 20% | const | +0.171 | -0.109 | +0.183 | +0.121 | +0.4 | [-0.078, +0.334] | 0.10 | NO |
| 30% | const | +0.234 | -0.241 | +0.259 | +0.147 | +4.0 | [-0.180, +0.498] | 0.10 | NO |
| 50% | const | +0.246 | -0.758 | +0.216 | +0.045 | +11.1 | [-0.575, +0.694] | 0.10 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,047,093, Sharpe 1.15, maxDD 429,659, worst wk -135,872; H1: net -4,551, Sharpe -0.03, maxDD 296,620, worst wk -103,688; H2: net 196,223, Sharpe 0.78, maxDD 248,558, worst wk -136,980; all: net 1,238,766, Sharpe 0.92, maxDD 429,659, worst wk -136,980
Correlation with pair (weekly): clean +0.17, H1 +0.08, H2 -0.17, all +0.09; worst-decile weeks (n=17) corr -0.38, sleeve mean in those weeks $6,238, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.61 | 3.11 | 4.86 | -84,961 | -80,106 | 316,799 | -98,278 | 44.8 |
| clean | add 30% | 1.65 | 3.23 | 4.91 | -89,513 | -83,093 | 335,144 | -108,913 | 44.8 |
| clean | const 20% | 1.63 | 3.17 | 4.88 | -69,475 | -64,971 | 260,777 | -82,877 | 45.7 |
| clean | const 30% | 1.69 | 3.32 | 4.96 | -69,346 | -61,549 | 251,111 | -85,811 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.75 | 5.70 | 3.39 | -77,745 | -72,699 | 175,046 | -86,016 | 35.7 |
| H1 | add 30% | 2.68 | 5.44 | 3.17 | -81,428 | -76,201 | 186,713 | -89,880 | 35.7 |
| H1 | const 20% | 2.72 | 5.57 | 3.28 | -62,296 | -59,560 | 144,704 | -70,359 | 35.7 |
| H1 | const 30% | 2.59 | 5.09 | 2.93 | -63,405 | -56,492 | 141,199 | -66,394 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.45 | 5.28 | 3.84 | -74,557 | -68,426 | 208,296 | -77,856 | 44.4 |
| H2 | add 30% | 2.50 | 5.51 | 4.03 | -71,292 | -63,501 | 203,731 | -76,957 | 44.4 |
| H2 | const 20% | 2.48 | 5.40 | 3.93 | -58,340 | -52,589 | 164,811 | -61,925 | 44.4 |
| H2 | const 30% | 2.55 | 5.69 | 4.27 | -50,095 | -45,095 | 138,504 | -53,061 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.96 | 3.91 | 9.26 | -83,177 | -78,017 | 316,799 | -98,278 | 43.5 |
| all | add 30% | 1.99 | 3.98 | 9.12 | -87,228 | -80,260 | 335,144 | -108,913 | 43.5 |
| all | const 20% | 1.98 | 3.95 | 9.19 | -67,755 | -63,119 | 260,777 | -82,877 | 44.0 |
| all | const 30% | 2.00 | 4.01 | 8.96 | -66,540 | -58,849 | 251,111 | -85,811 | 43.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.146 / -0.079 / +0.154
- [PASS] 3 worst week within share: all-in worst week +19.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.92 vs p95 0.31 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.055, +0.278]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.107 / -0.120 / +0.140
- [PASS] 6 worst-decile corr <=+0.30: -0.38
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_HO); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2162 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 7005 | +0.0297 | 0.52 |
| fixed | 7005 | -0.0108 | -0.19 |
| scaled | 7005 | -0.0108 | -0.19 |

Plateau neighbours (all-in 20% uplift; selected +0.105):
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.0', 'R': '2.0'}: -0.052 (trades 4977)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '0.75', 'R': '2.0'}: -0.008 (trades 2206)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '1.5'}: +0.071 (trades 2206)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.0', 'L': '15'}: +0.121 (trades 2157)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.0', 'R': '2.0'}: +0.064 (trades 818)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.25', 'R': '2.0'}: +0.140 (trades 2080)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.5'}: +0.155 (trades 2106)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.0', 'R': '2.0', 'L': '25'}: +0.100 (trades 2158)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.38, p95 0.31, real 0.92. Standalone Sharpe at 2x slippage 0.73.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 686 | 15 | 0.31 |
| 2014 | 619 | -26 | -0.67 |
| 2015 | 695 | 51 | 1.27 |
| 2016 | 739 | -47 | -1.32 |
| 2017 | 722 | 8 | 0.21 |
| 2018 | 711 | -77 | -2.10 |
| 2019 | 730 | -71 | -1.81 |
| 2020 | 664 | -37 | -0.93 |
| 2021 | 685 | 51 | 1.44 |
| 2022 | 754 | 57 | 1.16 |
| 2023 | 776 | 2 | 0.03 |
| 2024 | 718 | 34 | 0.77 |
| 2025 | 651 | 56 | 1.53 |
| 2026 | 481 | 28 | 1.01 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.15 | +0.15/-0.08/+0.15 |
| 2 tick entry / 2 tick exit | 0.59 | +0.05/-0.15/+0.11 |
| 3 tick entry / 3 tick exit | 0.17 | -0.03/-0.30/+0.09 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.89 | -0.17/-0.66/-0.07 |

DONE RU2_HO