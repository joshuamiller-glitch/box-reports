# REPORT RU9_6E
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=15, S=1.0, R=2.0; additive @20% clean/H1/H2 -0.18/-0.04/-0.21; standalone all-in weekly Sharpe -0.84 (2013-26 -1.48, dev 2013-22 -1.82); pair-window trades 783. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|---------:|-------:|:-----------|
| 6E    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  524 |   -0.803 |  -40.317 |      0 | True       |
| 6E    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  418 |   -1.064 |  -40.427 |      1 | True       |
| 6E    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  684 |   -1.074 |  -50.283 |      1 | True       |
| 6E    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 1699 |   -1.577 | -110.681 |      0 | True       |
| 6E    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 1747 |   -1.744 | -124.647 |      0 | True       |
| 6E    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1260 |   -1.951 | -111.037 |      0 | True       |
| 6E    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  312 |   -2.190 |  -63.337 |      1 | True       |
| 6E    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1173 |   -2.338 | -140.465 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.80; replicate best-eligible median -0.62, p95 -0.01; real beats 30% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.814e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.085 | -0.007 | -0.102 | -0.082 | +5.6 | [-0.174, +0.006] | 0.60 | NO |
| 20% | add | -0.182 | -0.037 | -0.213 | -0.177 | +21.7 | [-0.357, -0.004] | 0.60 | NO |
| 30% | add | -0.287 | -0.088 | -0.332 | -0.282 | +38.4 | [-0.551, -0.026] | 0.60 | NO |
| 50% | add | -0.507 | -0.244 | -0.580 | -0.511 | +71.8 | [-0.933, -0.103] | 0.60 | NO |
| 10% | const | -0.095 | -0.010 | -0.114 | -0.091 | -3.8 | [-0.194, +0.006] | 0.60 | NO |
| 20% | const | -0.234 | -0.060 | -0.272 | -0.228 | +4.1 | [-0.453, -0.013] | 0.60 | NO |
| 30% | const | -0.429 | -0.181 | -0.490 | -0.428 | +11.9 | [-0.798, -0.070] | 0.60 | NO |
| 50% | const | -0.992 | -0.789 | -1.196 | -1.051 | +27.6 | [-1.751, -0.354] | 0.60 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -731,348, Sharpe -0.80, maxDD 1,106,269, worst wk -151,939; H1: net -64,748, Sharpe -0.35, maxDD 398,892, worst wk -72,306; H2: net -328,032, Sharpe -1.44, maxDD 429,728, worst wk -76,665; all: net -1,124,127, Sharpe -0.84, maxDD 1,205,378, worst wk -151,939
Correlation with pair (weekly): clean -0.02, H1 -0.14, H2 +0.00, all -0.02; worst-decile weeks (n=17) corr -0.04, sleeve mean in those weeks $20,558, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.28 | 2.42 | 4.35 | -89,254 | -80,813 | 272,058 | -100,473 | 45.7 |
| clean | add 30% | 1.17 | 2.20 | 3.82 | -95,288 | -83,073 | 290,960 | -114,234 | 46.7 |
| clean | const 20% | 1.23 | 2.31 | 4.07 | -73,817 | -65,492 | 225,207 | -85,883 | 44.8 |
| clean | const 30% | 1.03 | 1.90 | 3.22 | -72,132 | -62,086 | 220,683 | -92,349 | 50.5 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.79 | 6.39 | 3.22 | -65,346 | -60,077 | 180,177 | -80,754 | 42.9 |
| H1 | add 30% | 2.74 | 6.36 | 2.95 | -67,678 | -57,266 | 194,409 | -81,987 | 42.9 |
| H1 | const 20% | 2.77 | 6.39 | 3.08 | -53,129 | -46,937 | 149,834 | -65,096 | 42.9 |
| H1 | const 30% | 2.65 | 6.14 | 2.66 | -49,655 | -41,956 | 148,895 | -58,501 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.08 | 4.16 | 3.18 | -84,619 | -79,718 | 224,425 | -84,925 | 43.2 |
| H2 | add 30% | 1.97 | 3.88 | 2.98 | -86,943 | -82,416 | 227,925 | -88,679 | 43.2 |
| H2 | const 20% | 2.03 | 4.02 | 3.08 | -68,625 | -64,854 | 180,940 | -69,442 | 43.2 |
| H2 | const 30% | 1.81 | 3.50 | 2.65 | -65,299 | -60,119 | 168,177 | -65,455 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.68 | 3.29 | 9.11 | -87,280 | -79,644 | 272,058 | -100,473 | 45.0 |
| all | add 30% | 1.58 | 3.05 | 8.13 | -92,244 | -81,631 | 290,960 | -114,234 | 45.6 |
| all | const 20% | 1.63 | 3.17 | 8.60 | -71,694 | -64,476 | 225,207 | -85,883 | 44.4 |
| all | const 30% | 1.43 | 2.72 | 7.04 | -69,521 | -60,489 | 220,683 | -92,349 | 48.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.182 / -0.037 / -0.213
- [FAIL] 3 worst week within share: all-in worst week +21.7% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.84 vs p95 -0.04 (rank 0.54)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.357, -0.004]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.236 / -0.082 / -0.257
- [PASS] 6 worst-decile corr <=+0.30: -0.04
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_6E); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (783 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2403 | -0.1100 | -1.28 |
| fixed | 2403 | -0.1583 | -1.82 |
| scaled | 2403 | -0.1583 | -1.82 |

Plateau neighbours (all-in 20% uplift; selected -0.177):
- {'sym': '6E', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '15', 'S': '1.0', 'R': '2.0'}: -0.306 (trades 1833)
- {'sym': '6E', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '15', 'S': '0.75', 'R': '2.0'}: -0.183 (trades 783)
- {'sym': '6E', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '15', 'S': '1.0', 'R': '1.5'}: -0.237 (trades 805)
- {'sym': '6E', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '3.125', 'tf': '15', 'S': '1.0', 'R': '2.0'}: -0.050 (trades 317)
- {'sym': '6E', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '15', 'S': '1.25', 'R': '2.0'}: -0.185 (trades 779)
- {'sym': '6E', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '15', 'S': '1.0', 'R': '2.5'}: -0.166 (trades 759)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.87, p95 -0.04, real -0.84. Standalone Sharpe at 2x slippage -1.11.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 177 | -98 | -5.13 |
| 2014 | 194 | -117 | -6.53 |
| 2015 | 169 | -67 | -4.11 |
| 2016 | 275 | 5 | 0.25 |
| 2017 | 277 | -45 | -2.18 |
| 2018 | 279 | -0 | -0.00 |
| 2019 | 218 | -25 | -1.44 |
| 2020 | 266 | -6 | -0.29 |
| 2021 | 264 | -24 | -1.45 |
| 2022 | 284 | -4 | -0.14 |
| 2023 | 286 | -7 | -0.30 |
| 2024 | 239 | -23 | -1.11 |
| 2025 | 240 | -9 | -0.38 |
| 2026 | 169 | -13 | -0.84 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.80 | -0.18/-0.04/-0.21 |
| 2 tick entry / 2 tick exit | -1.37 | -0.29/-0.10/-0.33 |
| 3 tick entry / 3 tick exit | -2.10 | -0.43/-0.19/-0.43 |

DONE RU9_6E