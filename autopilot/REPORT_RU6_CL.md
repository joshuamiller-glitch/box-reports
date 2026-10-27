# REPORT RU6_CL
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=1, conf=0, sess=RTH, ent=mkt, k=1.5, tf=30, S=1.0, R=2.0; additive @20% clean/H1/H2 -0.04/-0.65/+0.04; standalone all-in weekly Sharpe -0.45 (2013-26 -0.35, dev 2013-22 -0.18); pair-window trades 1136. Runtime 0.0 min (+selection 0.1 min). 10-worker pool.

RU6 session split of the RU2 selected cell (ALL / RTH / non-RTH by placement time). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 40 clean trades): 3. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| CL    |    1 |      0 | RTH    | mkt   | 1.500 |   30 | 1.000 | 2.000 |  795 |    0.023 |   1.061 |      1 | True       |
| CL    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1650 |   -0.102 |  -8.294 |      2 | True       |
| CL    |    1 |      0 | NRTH   | mkt   | 1.500 |   30 | 1.000 | 2.000 |  902 |   -0.334 | -20.989 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.02; replicate best-eligible median -0.42, p95 0.02; real beats 95% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.016e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.012 | -0.319 | +0.029 | -0.049 | +12.6 | [-0.140, +0.045] | 0.55 | NO |
| 20% | add | -0.038 | -0.647 | +0.045 | -0.113 | +31.2 | [-0.293, +0.072] | 0.55 | NO |
| 30% | add | -0.075 | -0.978 | +0.046 | -0.190 | +49.8 | [-0.452, +0.084] | 0.55 | NO |
| 50% | add | -0.171 | -1.614 | +0.007 | -0.365 | +87.0 | [-0.782, +0.070] | 0.55 | NO |
| 10% | const | -0.015 | -0.355 | +0.031 | -0.056 | +3.2 | [-0.156, +0.049] | 0.55 | NO |
| 20% | const | -0.055 | -0.813 | +0.047 | -0.150 | +12.4 | [-0.373, +0.080] | 0.55 | NO |
| 30% | const | -0.134 | -1.393 | +0.028 | -0.300 | +21.6 | [-0.664, +0.080] | 0.55 | NO |
| 50% | const | -0.438 | -2.899 | -0.277 | -0.810 | +40.0 | [-1.494, -0.089] | 0.55 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 21,392, Sharpe 0.02, maxDD 589,215, worst wk -162,344; H1: net -614,499, Sharpe -3.27, maxDD 652,912, worst wk -98,550; H2: net -20,167, Sharpe -0.08, maxDD 314,758, worst wk -132,845; all: net -613,274, Sharpe -0.45, maxDD 1,178,741, worst wk -162,344
Correlation with pair (weekly): clean +0.05, H1 +0.07, H2 -0.23, all -0.01; worst-decile weeks (n=17) corr -0.04, sleeve mean in those weeks $1,744, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.42 | 2.66 | 4.20 | -88,872 | -83,580 | 317,543 | -108,269 | 44.8 |
| clean | add 30% | 1.39 | 2.54 | 3.97 | -95,055 | -87,038 | 336,260 | -123,625 | 45.7 |
| clean | const 20% | 1.40 | 2.60 | 4.08 | -73,571 | -68,169 | 261,521 | -92,757 | 45.7 |
| clean | const 30% | 1.33 | 2.36 | 3.54 | -72,103 | -64,841 | 264,904 | -100,357 | 45.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.18 | 4.09 | 2.67 | -89,850 | -80,426 | 176,377 | -95,273 | 39.3 |
| H1 | add 30% | 1.85 | 3.25 | 2.17 | -95,970 | -87,791 | 188,710 | -103,766 | 42.9 |
| H1 | const 20% | 2.01 | 3.66 | 2.41 | -74,328 | -67,287 | 146,035 | -79,616 | 39.3 |
| H1 | const 30% | 1.43 | 2.34 | 1.40 | -72,687 | -68,082 | 164,990 | -80,280 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.34 | 4.83 | 3.68 | -77,808 | -73,493 | 210,206 | -81,845 | 40.5 |
| H2 | add 30% | 2.34 | 4.82 | 3.74 | -76,727 | -72,464 | 206,596 | -81,505 | 43.2 |
| H2 | const 20% | 2.34 | 4.83 | 3.71 | -61,814 | -57,655 | 166,720 | -65,340 | 43.2 |
| H2 | const 30% | 2.33 | 4.71 | 3.65 | -57,663 | -52,488 | 147,517 | -58,579 | 40.5 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.75 | 3.32 | 8.12 | -88,309 | -82,358 | 317,543 | -108,269 | 43.2 |
| all | add 30% | 1.67 | 3.10 | 7.49 | -93,753 | -85,058 | 336,260 | -123,625 | 45.0 |
| all | const 20% | 1.71 | 3.22 | 7.80 | -72,825 | -66,928 | 261,521 | -92,757 | 44.4 |
| all | const 30% | 1.56 | 2.80 | 6.45 | -70,763 | -63,843 | 264,904 | -100,357 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.038 / -0.647 / +0.045
- [FAIL] 3 worst week within share: all-in worst week +31.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.45 vs p95 0.02 (rank 0.79)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.293, +0.072]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.114 / -0.727 / +0.017
- [PASS] 6 worst-decile corr <=+0.30: -0.04
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU6_CL); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1136 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 3493 | +0.0235 | 0.37 |
| fixed | 3493 | -0.0117 | -0.18 |
| scaled | 3493 | -0.0117 | -0.18 |

Plateau neighbours (all-in 20% uplift; selected -0.113):
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'mkt', 'k': '1.125', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.190 (trades 1695)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '0.75', 'R': '2.0'}: -0.290 (trades 1177)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '1.5'}: -0.209 (trades 1201)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.086 (trades 662)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.25', 'R': '2.0'}: -0.096 (trades 1078)
- {'sym': 'CL', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '2.5'}: -0.099 (trades 1097)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.91, p95 0.02, real -0.45. Standalone Sharpe at 2x slippage -0.79.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 309 | -7 | -0.31 |
| 2014 | 337 | -34 | -1.55 |
| 2015 | 383 | 43 | 1.78 |
| 2016 | 375 | 9 | 0.40 |
| 2017 | 293 | 14 | 0.68 |
| 2018 | 385 | 4 | 0.20 |
| 2019 | 391 | -31 | -1.24 |
| 2020 | 296 | -36 | -1.69 |
| 2021 | 342 | -11 | -0.47 |
| 2022 | 382 | 8 | 0.34 |
| 2023 | 460 | -44 | -1.83 |
| 2024 | 401 | 25 | 0.95 |
| 2025 | 327 | -36 | -2.06 |
| 2026 | 211 | -12 | -0.86 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.02 | -0.04/-0.65/+0.04 |
| 2 tick entry / 2 tick exit | -0.93 | -0.22/-0.78/-0.05 |
| 3 tick entry / 3 tick exit | -2.05 | -0.44/-0.85/-0.17 |
| retrace-limit DISP (b=1.5, tf30, f=0.5, RZ geometry) | 0.32 | +0.05/-0.40/-0.07 |

DONE RU6_CL