# REPORT RU10_CLxHO
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=1, conf=1, sess=ALL, ent=mkt, k=1.5, tf=30, S=1.0, R=2.0, partner=HO; additive @20% clean/H1/H2 -0.05/-0.69/-0.21; standalone all-in weekly Sharpe -0.61 (2013-26 -0.85, dev 2013-22 -0.91); pair-window trades 2362. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU10 displacement continuation confirmed by a same-direction displacement (range >= 1 ATR) in the partner market. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R | partner   |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|:----------|-----:|---------:|---------:|-------:|:-----------|
| CL    |    1 |      1 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | HO        | 1550 |   -0.073 |   -5.544 |      2 | True       |
| CL    |    1 |      1 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 | HO        |  743 |   -0.805 |  -43.237 |      0 | True       |
| CL    |    1 |      1 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | HO        | 1436 |   -1.133 |  -76.726 |      1 | True       |
| CL    |    1 |      1 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | HO        | 1039 |   -1.145 |  -64.595 |      1 | True       |
| CL    |    1 |      1 | ALL    | stop  | 2.000 |   30 | 1.000 | 2.000 | HO        |  695 |   -1.265 |  -62.835 |      0 | True       |
| CL    |    1 |      1 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | HO        | 2066 |   -1.356 | -108.101 |      0 | True       |
| CL    |    1 |      1 | ALL    | mkt   | 2.000 |   15 | 1.000 | 2.000 | HO        | 1157 |   -1.358 |  -89.272 |      1 | True       |
| CL    |    1 |      1 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | HO        | 2313 |   -1.837 | -173.790 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.07; replicate best-eligible median 0.00, p95 0.76; real beats 45% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.198e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.020 | -0.355 | -0.097 | -0.080 | +16.3 | [-0.172, +0.008] | 0.22 | NO |
| 20% | add | -0.053 | -0.694 | -0.206 | -0.172 | +37.8 | [-0.354, +0.002] | 0.22 | NO |
| 30% | add | -0.096 | -1.010 | -0.326 | -0.274 | +59.3 | [-0.541, -0.018] | 0.22 | NO |
| 50% | add | -0.205 | -1.561 | -0.585 | -0.490 | +102.2 | [-0.899, -0.089] | 0.22 | NO |
| 10% | const | -0.023 | -0.394 | -0.108 | -0.089 | +6.9 | [-0.192, +0.008] | 0.22 | NO |
| 20% | const | -0.073 | -0.855 | -0.265 | -0.222 | +18.8 | [-0.447, -0.006] | 0.22 | NO |
| 30% | const | -0.164 | -1.377 | -0.490 | -0.413 | +30.8 | [-0.777, -0.063] | 0.22 | NO |
| 50% | const | -0.497 | -2.524 | -1.219 | -0.981 | +54.8 | [-1.649, -0.330] | 0.22 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -66,440, Sharpe -0.07, maxDD 653,827, worst wk -139,705; H1: net -480,675, Sharpe -2.08, maxDD 533,510, worst wk -177,215; H2: net -314,870, Sharpe -1.16, maxDD 674,092, worst wk -116,660; all: net -861,984, Sharpe -0.61, maxDD 1,513,257, worst wk -177,215
Correlation with pair (weekly): clean +0.04, H1 +0.42, H2 -0.02, all +0.07; worst-decile weeks (n=17) corr -0.06, sleeve mean in those weeks $-7,775, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.41 | 2.67 | 3.84 | -86,368 | -82,130 | 342,855 | -94,090 | 45.7 |
| clean | add 30% | 1.36 | 2.56 | 3.50 | -91,650 | -85,165 | 374,227 | -102,356 | 47.6 |
| clean | const 20% | 1.39 | 2.62 | 3.66 | -71,071 | -66,918 | 286,833 | -78,579 | 48.6 |
| clean | const 30% | 1.30 | 2.39 | 3.14 | -69,321 | -63,378 | 290,194 | -79,089 | 47.6 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.13 | 4.03 | 2.73 | -100,584 | -86,097 | 182,596 | -113,730 | 42.9 |
| H1 | add 30% | 1.82 | 3.22 | 2.27 | -112,071 | -96,297 | 198,038 | -131,452 | 50.0 |
| H1 | const 20% | 1.97 | 3.61 | 2.49 | -85,062 | -72,957 | 152,254 | -98,073 | 42.9 |
| H1 | const 30% | 1.45 | 2.40 | 1.76 | -88,788 | -76,588 | 154,310 | -107,966 | 46.4 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.09 | 4.24 | 3.27 | -83,981 | -77,979 | 218,852 | -89,871 | 43.2 |
| H2 | add 30% | 1.97 | 4.00 | 2.94 | -85,986 | -77,376 | 232,319 | -93,545 | 43.2 |
| H2 | const 20% | 2.03 | 4.13 | 3.14 | -67,987 | -62,142 | 178,276 | -73,367 | 43.2 |
| H2 | const 30% | 1.81 | 3.67 | 2.47 | -61,995 | -56,165 | 182,473 | -68,788 | 51.4 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.69 | 3.23 | 7.38 | -89,916 | -83,352 | 342,855 | -113,730 | 45.0 |
| all | add 30% | 1.58 | 2.98 | 6.53 | -96,399 | -86,546 | 374,227 | -131,452 | 46.7 |
| all | const 20% | 1.64 | 3.11 | 6.94 | -74,435 | -67,945 | 286,833 | -98,073 | 46.7 |
| all | const 30% | 1.45 | 2.65 | 5.63 | -73,588 | -64,978 | 290,194 | -107,966 | 47.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.053 / -0.694 / -0.206
- [FAIL] 3 worst week within share: all-in worst week +37.8% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.61 vs p95 -0.21 (rank 0.82)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.354, +0.002]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.141 / -0.787 / -0.249
- [PASS] 6 worst-decile corr <=+0.30: -0.06
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU10_CLxHO); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2362 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6337 | -0.0089 | -0.18 |
| fixed | 6337 | -0.0449 | -0.91 |
| scaled | 6337 | -0.0449 | -0.91 |

Plateau neighbours (all-in 20% uplift; selected -0.172):
- {'sym': 'CL', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.125', 'tf': '30', 'S': '1.0', 'R': '2.0', 'partner': 'HO'}: -0.270 (trades 3438)
- {'sym': 'CL', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '0.75', 'R': '2.0', 'partner': 'HO'}: -0.247 (trades 2418)
- {'sym': 'CL', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '1.5', 'partner': 'HO'}: -0.234 (trades 2518)
- {'sym': 'CL', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0', 'partner': 'HO'}: -0.137 (trades 1353)
- {'sym': 'CL', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.25', 'R': '2.0', 'partner': 'HO'}: -0.173 (trades 2271)
- {'sym': 'CL', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '2.5', 'partner': 'HO'}: -0.157 (trades 2246)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.09, p95 -0.21, real -0.61. Standalone Sharpe at 2x slippage -1.02.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 550 | -17 | -0.57 |
| 2014 | 539 | -38 | -1.39 |
| 2015 | 633 | 37 | 1.10 |
| 2016 | 676 | -2 | -0.05 |
| 2017 | 542 | -15 | -0.57 |
| 2018 | 646 | -21 | -0.76 |
| 2019 | 667 | -73 | -2.07 |
| 2020 | 599 | -71 | -2.26 |
| 2021 | 708 | -50 | -1.58 |
| 2022 | 777 | -34 | -0.95 |
| 2023 | 832 | -22 | -0.65 |
| 2024 | 798 | 23 | 0.57 |
| 2025 | 697 | -58 | -1.64 |
| 2026 | 530 | -39 | -1.56 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.07 | -0.05/-0.69/-0.21 |
| 2 tick entry / 2 tick exit | -1.36 | -0.30/-0.86/-0.29 |
| 3 tick entry / 3 tick exit | -2.58 | -0.54/-1.02/-0.42 |
| retrace-limit DISP (b=1.5, tf30, f=0.5, RZ geometry) | 0.32 | +0.05/-0.40/-0.07 |

DONE RU10_CLxHO