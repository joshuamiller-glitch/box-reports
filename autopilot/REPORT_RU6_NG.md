# REPORT RU6_NG
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=RTH, ent=stop, k=2.0, tf=15, S=1.5, R=1.0; additive @20% clean/H1/H2 +0.15/-0.44/+0.11; standalone all-in weekly Sharpe 0.59 (2013-26 -0.03, dev 2013-22 -0.15); pair-window trades 354. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU6 session split of the RU2 selected cell (ALL / RTH / non-RTH by placement time). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 40 clean trades): 3. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |    net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|-------:|-------:|:-----------|
| NG    |    1 |      0 | RTH    | stop  | 2.000 |   15 | 1.500 | 1.000 |  230 |    1.155 | 21.513 |      3 | True       |
| NG    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 1.000 | 1070 |    0.861 | 37.958 |      2 | True       |
| NG    |    1 |      0 | NRTH   | stop  | 2.000 |   15 | 1.500 | 1.000 |  858 |    0.265 | 10.918 |      2 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.16; replicate best-eligible median 0.51, p95 1.05; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.868e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.083 | -0.198 | +0.070 | +0.036 | +2.9 | [-0.060, +0.131] | 0.16 | NO |
| 20% | add | +0.148 | -0.444 | +0.111 | +0.050 | +11.7 | [-0.138, +0.237] | 0.16 | NO |
| 30% | add | +0.197 | -0.726 | +0.126 | +0.046 | +20.7 | [-0.231, +0.322] | 0.16 | NO |
| 50% | add | +0.254 | -1.335 | +0.098 | -0.004 | +38.8 | [-0.428, +0.423] | 0.16 | NO |
| 10% | const | +0.091 | -0.223 | +0.076 | +0.038 | -6.7 | [-0.068, +0.145] | 0.16 | NO |
| 20% | const | +0.175 | -0.581 | +0.121 | +0.050 | -7.0 | [-0.183, +0.282] | 0.16 | NO |
| 30% | const | +0.239 | -1.117 | +0.115 | +0.019 | -7.4 | [-0.357, +0.393] | 0.16 | NO |
| 50% | const | +0.254 | -2.583 | -0.113 | -0.223 | -1.7 | [-0.907, +0.472] | 0.16 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,047,344, Sharpe 1.15, maxDD 455,696, worst wk -149,590; H1: net -519,790, Sharpe -1.95, maxDD 584,525, worst wk -203,538; H2: net 393,077, Sharpe 1.04, maxDD 300,635, worst wk -102,030; all: net 920,631, Sharpe 0.59, maxDD 831,698, worst wk -203,538
Correlation with pair (weekly): clean +0.16, H1 -0.21, H2 +0.12, all +0.08; worst-decile weeks (n=17) corr -0.14, sleeve mean in those weeks $-5,041, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.61 | 3.14 | 4.65 | -88,865 | -84,455 | 331,316 | -92,193 | 45.7 |
| clean | add 30% | 1.66 | 3.26 | 4.61 | -94,357 | -88,329 | 356,919 | -99,634 | 44.8 |
| clean | const 20% | 1.63 | 3.21 | 4.63 | -73,289 | -69,087 | 275,294 | -76,731 | 45.7 |
| clean | const 30% | 1.70 | 3.35 | 4.56 | -71,550 | -66,108 | 272,886 | -76,441 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.38 | 5.04 | 2.99 | -72,913 | -64,585 | 163,640 | -77,162 | 50.0 |
| H1 | add 30% | 2.10 | 4.36 | 2.58 | -70,564 | -66,705 | 169,604 | -77,277 | 50.0 |
| H1 | const 20% | 2.25 | 4.71 | 2.78 | -57,391 | -52,516 | 133,298 | -61,775 | 46.4 |
| H1 | const 30% | 1.71 | 3.46 | 2.09 | -52,719 | -48,601 | 124,090 | -54,197 | 50.0 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.41 | 4.92 | 3.69 | -85,230 | -81,890 | 231,948 | -89,856 | 37.8 |
| H2 | add 30% | 2.42 | 4.99 | 3.75 | -92,880 | -86,830 | 239,209 | -94,958 | 37.8 |
| H2 | const 20% | 2.42 | 4.96 | 3.72 | -71,244 | -67,014 | 188,462 | -73,926 | 37.8 |
| H2 | const 30% | 2.41 | 5.03 | 3.80 | -71,902 | -66,311 | 174,505 | -72,741 | 37.8 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.91 | 3.78 | 8.71 | -88,107 | -83,006 | 331,316 | -92,193 | 44.4 |
| all | add 30% | 1.90 | 3.79 | 8.34 | -93,912 | -87,050 | 356,919 | -99,634 | 43.8 |
| all | const 20% | 1.91 | 3.79 | 8.52 | -72,807 | -68,022 | 275,294 | -76,731 | 43.8 |
| all | const 30% | 1.88 | 3.75 | 7.94 | -71,367 | -64,846 | 272,886 | -76,441 | 43.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.148 / -0.444 / +0.111
- [PASS] 3 worst week within share: all-in worst week +11.7% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.59 vs p95 0.78 (rank 0.89)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.138, +0.237]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.111 / -0.488 / +0.081
- [PASS] 6 worst-decile corr <=+0.30: -0.14
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU6_NG); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (354 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1128 | +0.0222 | 0.30 |
| fixed | 1128 | -0.0111 | -0.15 |
| scaled | 1128 | -0.0111 | -0.15 |

Plateau neighbours (all-in 20% uplift; selected +0.050):
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.0'}: -0.161 (trades 1037)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '1.0'}: -0.042 (trades 355)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.75'}: +0.039 (trades 358)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.0', 'L': '15'}: +0.049 (trades 353)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '1.0'}: +0.031 (trades 134)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '1.0'}: +0.076 (trades 351)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.25'}: +0.027 (trades 346)
- {'sym': 'NG', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.0', 'L': '25'}: +0.049 (trades 355)

Own random-entry null: 300 draws, standalone all-in Sharpe median 0.02, p95 0.78, real 0.59. Standalone Sharpe at 2x slippage 0.41.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 135 | 6 | 0.70 |
| 2014 | 127 | -4 | -0.45 |
| 2015 | 122 | -6 | -0.79 |
| 2016 | 120 | -17 | -2.20 |
| 2017 | 96 | 9 | 1.04 |
| 2018 | 82 | 0 | 0.05 |
| 2019 | 108 | -10 | -1.27 |
| 2020 | 133 | -2 | -0.19 |
| 2021 | 109 | 0 | 0.05 |
| 2022 | 96 | 11 | 1.30 |
| 2023 | 115 | -1 | -0.07 |
| 2024 | 120 | 4 | 0.43 |
| 2025 | 105 | -1 | -0.12 |
| 2026 | 78 | 7 | 0.82 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.15 | +0.15/-0.44/+0.11 |
| 2 tick entry / 2 tick exit | 0.75 | +0.07/-0.51/+0.02 |
| 3 tick entry / 3 tick exit | 0.00 | -0.06/-0.55/-0.02 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | 0.04 | +0.04/-0.49/-0.02 |

DONE RU6_NG