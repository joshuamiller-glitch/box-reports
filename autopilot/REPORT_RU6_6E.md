# REPORT RU6_6E
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=1, conf=0, sess=RTH, ent=stop, k=2.0, tf=15, S=1.5, R=2.0; additive @20% clean/H1/H2 -0.14/-0.13/-0.18; standalone all-in weekly Sharpe -0.49 (2013-26 -2.75, dev 2013-22 -3.37); pair-window trades 265. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU6 session split of the RU2 selected cell (ALL / RTH / non-RTH by placement time). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 40 clean trades): 3. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |   n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|----:|---------:|--------:|-------:|:-----------|
| 6E    |    1 |      0 | RTH    | stop  | 2.000 |   15 | 1.500 | 2.000 | 173 |   -0.468 | -10.369 |      1 | True       |
| 6E    |    1 |      0 | NRTH   | stop  | 2.000 |   15 | 1.500 | 2.000 | 572 |   -0.580 | -26.752 |      1 | True       |
| 6E    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 2.000 | 734 |   -0.757 | -40.634 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.47; replicate best-eligible median -0.21, p95 0.12; real beats 35% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.11e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.064 | -0.053 | -0.085 | -0.068 | +14.3 | [-0.162, +0.025] | 0.18 | NO |
| 20% | add | -0.138 | -0.135 | -0.184 | -0.151 | +35.3 | [-0.334, +0.030] | 0.18 | NO |
| 30% | add | -0.220 | -0.241 | -0.292 | -0.243 | +56.3 | [-0.510, +0.019] | 0.18 | NO |
| 50% | add | -0.393 | -0.497 | -0.523 | -0.442 | +98.3 | [-0.858, -0.031] | 0.18 | NO |
| 10% | const | -0.071 | -0.060 | -0.095 | -0.077 | +5.0 | [-0.180, +0.027] | 0.18 | NO |
| 20% | const | -0.178 | -0.185 | -0.237 | -0.196 | +16.6 | [-0.423, +0.026] | 0.18 | NO |
| 30% | const | -0.331 | -0.402 | -0.439 | -0.370 | +28.3 | [-0.737, -0.008] | 0.18 | NO |
| 50% | const | -0.782 | -1.142 | -1.070 | -0.905 | +51.6 | [-1.576, -0.233] | 0.18 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -426,183, Sharpe -0.47, maxDD 713,328, worst wk -173,716; H1: net -68,479, Sharpe -0.30, maxDD 365,564, worst wk -157,275; H2: net -199,039, Sharpe -0.67, maxDD 491,224, worst wk -162,341; all: net -693,701, Sharpe -0.49, maxDD 985,886, worst wk -173,716
Correlation with pair (weekly): clean +0.07, H1 +0.01, H2 +0.09, all +0.07; worst-decile weeks (n=17) corr -0.35, sleeve mean in those weeks $-11,862, positive share 0.24.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.32 | 2.43 | 4.13 | -90,248 | -85,079 | 301,084 | -111,653 | 42.9 |
| clean | add 30% | 1.24 | 2.23 | 3.50 | -98,907 | -90,599 | 343,064 | -128,976 | 43.8 |
| clean | const 20% | 1.28 | 2.33 | 3.81 | -75,368 | -70,271 | 257,204 | -96,252 | 43.8 |
| clean | const 30% | 1.13 | 1.98 | 2.88 | -77,689 | -68,387 | 278,951 | -105,874 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.69 | 5.72 | 3.36 | -69,485 | -66,070 | 172,520 | -78,287 | 39.3 |
| H1 | add 30% | 2.59 | 5.36 | 3.13 | -73,107 | -67,371 | 182,923 | -78,287 | 39.3 |
| H1 | const 20% | 2.64 | 5.55 | 3.24 | -56,749 | -52,931 | 142,177 | -62,630 | 39.3 |
| H1 | const 30% | 2.43 | 4.82 | 2.88 | -55,084 | -51,855 | 137,409 | -55,366 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.11 | 4.23 | 3.38 | -88,172 | -83,172 | 218,547 | -90,242 | 40.5 |
| H2 | add 30% | 2.01 | 3.96 | 3.28 | -93,617 | -85,166 | 219,108 | -96,790 | 40.5 |
| H2 | const 20% | 2.06 | 4.10 | 3.33 | -72,716 | -67,335 | 175,062 | -74,813 | 40.5 |
| H2 | const 30% | 1.86 | 3.58 | 3.15 | -70,433 | -64,389 | 153,880 | -73,646 | 43.2 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.71 | 3.25 | 8.51 | -88,781 | -83,766 | 301,084 | -111,653 | 42.0 |
| all | add 30% | 1.62 | 3.01 | 7.27 | -96,154 | -87,806 | 343,064 | -128,976 | 42.6 |
| all | const 20% | 1.66 | 3.13 | 7.87 | -73,828 | -68,629 | 257,204 | -96,252 | 42.6 |
| all | const 30% | 1.49 | 2.70 | 6.03 | -74,271 | -65,881 | 278,951 | -105,874 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.138 / -0.135 / -0.184
- [FAIL] 3 worst week within share: all-in worst week +35.3% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.49 vs p95 0.32 (rank 0.47)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.334, +0.030]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.178 / -0.167 / -0.223
- [PASS] 6 worst-decile corr <=+0.30: -0.35
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU6_6E); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (265 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1401 | -0.5073 | -3.20 |
| fixed | 1401 | -0.5422 | -3.37 |
| scaled | 1401 | -0.5422 | -3.37 |

Plateau neighbours (all-in 20% uplift; selected -0.151):
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.224 (trades 719)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '2.0'}: -0.183 (trades 268)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.5'}: -0.225 (trades 273)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '15'}: -0.151 (trades 265)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '2.0'}: -0.039 (trades 104)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '2.0'}: -0.130 (trades 262)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '2.5'}: -0.151 (trades 263)
- {'sym': '6E', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '2.0', 'L': '25'}: -0.154 (trades 266)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.46, p95 0.32, real -0.49. Standalone Sharpe at 2x slippage -0.68.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 305 | -269 | -9.77 |
| 2014 | 226 | -219 | -9.64 |
| 2015 | 286 | -259 | -10.14 |
| 2016 | 92 | -16 | -1.74 |
| 2017 | 91 | 10 | 0.85 |
| 2018 | 75 | -7 | -0.71 |
| 2019 | 89 | -6 | -0.79 |
| 2020 | 78 | -1 | -0.13 |
| 2021 | 77 | 7 | 0.74 |
| 2022 | 82 | 2 | 0.20 |
| 2023 | 79 | -10 | -1.06 |
| 2024 | 82 | -3 | -0.30 |
| 2025 | 79 | 1 | 0.06 |
| 2026 | 65 | -3 | -0.38 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.47 | -0.14/-0.13/-0.18 |
| 2 tick entry / 2 tick exit | -0.93 | -0.23/-0.18/-0.27 |
| 3 tick entry / 3 tick exit | -1.36 | -0.31/-0.22/-0.34 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.13 | -0.05/-0.27/-0.20 |

DONE RU6_6E