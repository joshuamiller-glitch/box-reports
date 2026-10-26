# REPORT RU2_RB
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=30, S=1.5, R=1.0; additive @20% clean/H1/H2 +0.09/-0.01/+0.09; standalone all-in weekly Sharpe 0.34 (2013-26 0.04, dev 2013-22 -0.09); pair-window trades 1154. Runtime 0.1 min (+selection 0.1 min). 10-worker pool.

RU2 displacement continuation: trade WITH a tf bar of range >= k ATR closing within 20% of its extreme; market (next open +1 tick) or stop entry; stop S ATR (floor 30 ticks), target R x stop, 360 min cap, flat 16:55. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 32 cells, eligible (>= 40 clean trades): 32. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| RB    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 1.000 |  768 |    0.389 |  14.669 |      3 | True       |
| RB    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 1.000 | 1734 |   -0.041 |  -2.277 |      2 | True       |
| RB    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 2.000 |  701 |   -0.110 |  -5.226 |      2 | True       |
| RB    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 |  839 |   -0.158 |  -9.214 |      1 | True       |
| RB    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | 3087 |   -0.208 | -22.319 |      2 | True       |
| RB    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 2.000 | 2505 |   -0.247 | -24.446 |      2 | True       |
| RB    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 2.000 | 1439 |   -0.309 | -23.253 |      2 | True       |
| RB    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1990 |   -0.359 | -30.961 |      1 | True       |
| RB    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | 1394 |   -0.386 | -29.578 |      2 | True       |
| RB    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 1.000 |  855 |   -0.592 | -25.440 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.39; replicate best-eligible median 0.62, p95 1.08; real beats 25% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.416e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.053 | +0.019 | +0.056 | +0.050 | +8.9 | [-0.043, +0.151] | 0.97 | NO |
| 20% | add | +0.091 | -0.006 | +0.091 | +0.081 | +17.9 | [-0.108, +0.284] | 0.97 | NO |
| 30% | add | +0.113 | -0.071 | +0.103 | +0.091 | +26.8 | [-0.194, +0.391] | 0.97 | NO |
| 50% | add | +0.112 | -0.279 | +0.064 | +0.056 | +47.8 | [-0.392, +0.526] | 0.97 | NO |
| 10% | const | +0.058 | +0.018 | +0.061 | +0.055 | -1.1 | [-0.049, +0.167] | 0.97 | NO |
| 20% | const | +0.104 | -0.034 | +0.100 | +0.089 | -2.1 | [-0.147, +0.342] | 0.97 | NO |
| 30% | const | +0.119 | -0.196 | +0.087 | +0.076 | -1.8 | [-0.319, +0.490] | 0.97 | NO |
| 50% | const | -0.048 | -0.882 | -0.250 | -0.205 | +0.4 | [-0.947, +0.577] | 0.97 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 354,339, Sharpe 0.39, maxDD 562,410, worst wk -148,467; H1: net 44,435, Sharpe 0.17, maxDD 297,052, worst wk -107,980; H2: net 98,375, Sharpe 0.31, maxDD 424,282, worst wk -125,980; all: net 497,149, Sharpe 0.34, maxDD 584,801, worst wk -148,467
Correlation with pair (weekly): clean -0.14, H1 -0.06, H2 -0.16, all -0.13; worst-decile weeks (n=17) corr +0.16, sleeve mean in those weeks $14,701, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.55 | 3.00 | 4.92 | -81,674 | -77,336 | 284,944 | -93,114 | 39.0 |
| clean | add 30% | 1.57 | 3.04 | 4.44 | -84,763 | -78,196 | 323,137 | -100,629 | 40.0 |
| clean | const 20% | 1.56 | 3.02 | 4.67 | -66,538 | -62,026 | 243,233 | -77,497 | 38.1 |
| clean | const 30% | 1.58 | 3.02 | 3.98 | -62,387 | -57,926 | 260,569 | -77,204 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.82 | 5.98 | 3.40 | -72,035 | -63,922 | 177,056 | -95,764 | 35.7 |
| H1 | add 30% | 2.76 | 5.69 | 3.20 | -77,557 | -65,467 | 189,728 | -104,502 | 39.3 |
| H1 | const 20% | 2.79 | 5.86 | 3.30 | -59,715 | -50,829 | 146,714 | -80,106 | 39.3 |
| H1 | const 30% | 2.63 | 5.18 | 2.97 | -59,533 | -52,329 | 144,214 | -81,016 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.39 | 4.82 | 4.08 | -87,266 | -80,569 | 191,630 | -97,266 | 44.4 |
| H2 | add 30% | 2.40 | 4.78 | 4.01 | -91,952 | -84,094 | 197,302 | -104,636 | 41.7 |
| H2 | const 20% | 2.40 | 4.80 | 4.04 | -71,299 | -65,865 | 155,573 | -80,761 | 44.4 |
| H2 | const 30% | 2.38 | 4.66 | 3.86 | -71,361 | -62,039 | 145,669 | -79,879 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.94 | 3.82 | 9.77 | -84,632 | -78,674 | 284,944 | -97,266 | 39.9 |
| all | add 30% | 1.95 | 3.81 | 8.77 | -88,554 | -80,319 | 323,137 | -104,636 | 40.5 |
| all | const 20% | 1.94 | 3.82 | 9.24 | -69,104 | -63,476 | 243,233 | -80,761 | 39.9 |
| all | const 30% | 1.93 | 3.72 | 7.79 | -66,451 | -59,556 | 260,569 | -81,016 | 40.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.091 / -0.006 / +0.091
- [PASS] 3 worst week within share: all-in worst week +17.9% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.34 vs p95 0.85 (rank 0.70)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.108, +0.284]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 25% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.072 / -0.033 / +0.084
- [PASS] 6 worst-decile corr <=+0.30: +0.16
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU2_RB); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1154 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 3999 | +0.0127 | 0.27 |
| fixed | 3999 | -0.0044 | -0.09 |
| scaled | 3999 | -0.0044 | -0.09 |

Plateau neighbours (all-in 20% uplift; selected +0.081):
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '30', 'S': '1.5', 'R': '1.0'}: -0.129 (trades 2654)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.125', 'R': '1.0'}: -0.002 (trades 1176)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '0.75'}: -0.019 (trades 1172)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '1.0', 'L': '15'}: +0.065 (trades 1152)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '30', 'S': '1.5', 'R': '1.0'}: +0.016 (trades 428)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.875', 'R': '1.0'}: -0.014 (trades 1100)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '1.25'}: -0.024 (trades 1120)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '1.0', 'L': '25'}: +0.081 (trades 1153)

Own random-entry null: 300 draws, standalone all-in Sharpe median 0.04, p95 0.85, real 0.34. Standalone Sharpe at 2x slippage 0.25.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 405 | -8 | -0.40 |
| 2014 | 392 | -3 | -0.16 |
| 2015 | 413 | 9 | 0.50 |
| 2016 | 470 | -11 | -0.61 |
| 2017 | 443 | -16 | -0.85 |
| 2018 | 409 | -5 | -0.28 |
| 2019 | 410 | 1 | 0.04 |
| 2020 | 358 | -10 | -0.51 |
| 2021 | 347 | 23 | 1.11 |
| 2022 | 352 | 3 | 0.15 |
| 2023 | 438 | 8 | 0.34 |
| 2024 | 405 | 9 | 0.55 |
| 2025 | 342 | 3 | 0.16 |
| 2026 | 222 | 8 | 0.50 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.39 | +0.09/-0.01/+0.09 |
| 2 tick entry / 2 tick exit | 0.12 | +0.03/-0.21/+0.07 |
| 3 tick entry / 3 tick exit | -0.15 | -0.01/-0.22/+0.03 |
| retrace-limit DISP (b=2.0, tf30, f=0.5, RZ geometry) | 0.23 | +0.01/-0.05/-0.32 |

DONE RU2_RB