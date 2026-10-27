# REPORT RU7_6E
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=30, S=1.5, R=0.0; additive @20% clean/H1/H2 -0.26/-0.81/-0.24; standalone all-in weekly Sharpe -1.70 (2013-26 -3.50, dev 2013-22 -4.14); pair-window trades 754. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 0.000 |  508 |   -1.244 | -37.092 |      1 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 0.000 |  510 |   -1.450 | -43.725 |      1 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 |  763 |   -1.518 | -60.737 |      1 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1166 |   -1.570 | -71.873 |      0 | True       |
| 6E    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 0.000 |  579 |   -1.758 | -56.753 |      1 | True       |
| 6E    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  581 |   -1.913 | -60.724 |      1 | True       |
| 6E    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 0.000 | 1332 |   -1.920 | -93.176 |      0 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.000 | 0.000 | 1183 |   -1.969 | -90.313 |      0 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 0.000 |  769 |   -2.063 | -80.771 |      1 | True       |
| 6E    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 0.000 |  846 |   -2.159 | -85.656 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -1.24; replicate best-eligible median -0.64, p95 -0.20; real beats 5% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.056e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.123 | -0.388 | -0.115 | -0.162 | +8.4 | [-0.257, -0.073] | 0.71 | NO |
| 20% | add | -0.259 | -0.815 | -0.240 | -0.338 | +23.5 | [-0.524, -0.161] | 0.71 | NO |
| 30% | add | -0.402 | -1.275 | -0.370 | -0.523 | +38.7 | [-0.796, -0.263] | 0.71 | NO |
| 50% | add | -0.692 | -2.258 | -0.633 | -0.896 | +69.0 | [-1.327, -0.485] | 0.71 | NO |
| 10% | const | -0.138 | -0.433 | -0.129 | -0.181 | -0.9 | [-0.286, -0.082] | 0.71 | NO |
| 20% | const | -0.330 | -1.041 | -0.304 | -0.430 | +4.9 | [-0.659, -0.210] | 0.71 | NO |
| 30% | const | -0.589 | -1.902 | -0.540 | -0.764 | +10.7 | [-1.140, -0.404] | 0.71 | NO |
| 50% | const | -1.303 | -4.527 | -1.220 | -1.687 | +22.4 | [-2.391, -1.004] | 0.71 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -1,133,518, Sharpe -1.24, maxDD 1,759,763, worst wk -179,548; H1: net -966,168, Sharpe -5.31, maxDD 1,057,655, worst wk -118,662; H2: net -266,288, Sharpe -0.94, maxDD 441,240, worst wk -93,418; all: net -2,365,974, Sharpe -1.70, maxDD 3,026,920, worst wk -179,548
Correlation with pair (weekly): clean -0.06, H1 -0.38, H2 +0.16, all -0.05; worst-decile weeks (n=17) corr +0.03, sleeve mean in those weeks $2,504, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.20 | 2.23 | 3.54 | -88,492 | -82,417 | 311,718 | -101,943 | 44.8 |
| clean | add 30% | 1.06 | 1.92 | 3.02 | -93,731 | -84,808 | 327,522 | -114,444 | 49.5 |
| clean | const 20% | 1.13 | 2.07 | 3.27 | -72,849 | -66,817 | 255,696 | -86,555 | 46.7 |
| clean | const 30% | 0.87 | 1.52 | 2.31 | -70,416 | -63,178 | 256,114 | -91,362 | 51.4 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.01 | 3.92 | 2.19 | -73,808 | -66,652 | 182,595 | -85,499 | 50.0 |
| H1 | add 30% | 1.55 | 2.80 | 1.53 | -73,340 | -67,130 | 198,037 | -89,104 | 46.4 |
| H1 | const 20% | 1.79 | 3.35 | 1.85 | -58,286 | -53,513 | 152,253 | -69,841 | 50.0 |
| H1 | const 30% | 0.93 | 1.50 | 0.82 | -55,317 | -49,254 | 152,523 | -65,618 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.06 | 4.07 | 3.02 | -89,064 | -84,690 | 239,886 | -89,124 | 43.2 |
| H2 | add 30% | 1.93 | 3.76 | 2.78 | -94,396 | -87,442 | 251,116 | -95,113 | 43.2 |
| H2 | const 20% | 1.99 | 3.92 | 2.90 | -73,384 | -68,853 | 196,401 | -73,695 | 43.2 |
| H2 | const 30% | 1.76 | 3.35 | 2.50 | -70,876 | -64,982 | 185,888 | -71,969 | 48.6 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.52 | 2.87 | 7.15 | -89,001 | -82,271 | 311,718 | -101,943 | 45.6 |
| all | add 30% | 1.34 | 2.46 | 6.08 | -94,521 | -84,656 | 327,522 | -114,444 | 47.9 |
| all | const 20% | 1.43 | 2.66 | 6.60 | -73,409 | -66,671 | 255,696 | -86,555 | 46.7 |
| all | const 30% | 1.09 | 1.93 | 4.61 | -71,133 | -62,779 | 256,114 | -91,362 | 49.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.259 / -0.815 / -0.240
- [FAIL] 3 worst week within share: all-in worst week +23.5% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -1.70 vs p95 -1.17 (rank 0.70)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.524, -0.161]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.362 / -0.916 / -0.312
- [PASS] 6 worst-decile corr <=+0.30: +0.03
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_6E); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (754 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2994 | -0.2982 | -3.67 |
| fixed | 2994 | -0.3391 | -4.14 |
| scaled | 2994 | -0.3391 | -4.14 |

Plateau neighbours (all-in 20% uplift; selected -0.338):
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '30', 'S': '1.5', 'R': '0.0'}: -0.674 (trades 1835)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.125', 'R': '0.0'}: -0.385 (trades 756)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '0.0', 'L': '15'}: -0.327 (trades 750)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '30', 'S': '1.5', 'R': '0.0'}: -0.210 (trades 292)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.875', 'R': '0.0'}: -0.309 (trades 748)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '0.0', 'L': '25'}: -0.347 (trades 753)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.90, p95 -1.17, real -1.70. Standalone Sharpe at 2x slippage -2.21.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 447 | -307 | -11.63 |
| 2014 | 391 | -262 | -11.63 |
| 2015 | 448 | -283 | -11.38 |
| 2016 | 231 | -24 | -1.64 |
| 2017 | 226 | 1 | 0.09 |
| 2018 | 242 | -30 | -1.96 |
| 2019 | 232 | -22 | -1.60 |
| 2020 | 259 | -15 | -1.00 |
| 2021 | 281 | -51 | -3.55 |
| 2022 | 237 | -23 | -1.46 |
| 2023 | 278 | 9 | 0.54 |
| 2024 | 260 | -28 | -2.18 |
| 2025 | 215 | -50 | -3.96 |
| 2026 | 156 | -12 | -1.13 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -1.24 | -0.26/-0.81/-0.24 |
| 2 tick entry / 2 tick exit | -2.23 | -0.46/-1.01/-0.38 |
| 3 tick entry / 3 tick exit | -3.31 | -0.67/-1.19/-0.56 |
| retrace-limit DISP (b=2.0, tf30, f=0.5, RZ geometry) | -0.77 | -0.16/-0.65/-0.35 |

DONE RU7_6E