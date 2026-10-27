# REPORT RU9_ES
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=2, conf=0, sess=ALL, ent=mkt, k=2.5, tf=30, S=1.0, R=2.0; additive @20% clean/H1/H2 -0.12/+0.15/-0.01; standalone all-in weekly Sharpe 0.13 (2013-26 0.09, dev 2013-22 0.18); pair-window trades 615. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU9 multi-bar continuation (nb consecutive same-direction bars, net >= k ATR), market entry. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |      net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|---------:|-------:|:-----------|
| ES    |    2 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  401 |   -0.050 |   -1.880 |      2 | True       |
| ES    |    2 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  704 |   -0.260 |  -11.655 |      2 | True       |
| ES    |    3 |      0 | ALL    | mkt   | 2.500 |   15 | 1.000 | 2.000 |  891 |   -0.377 |  -21.379 |      1 | True       |
| ES    |    2 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1571 |   -1.291 |  -82.148 |      1 | True       |
| ES    |    3 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 2331 |   -1.330 | -122.016 |      0 | True       |
| ES    |    3 |      0 | ALL    | mkt   | 2.500 |   30 | 1.000 | 2.000 |  546 |   -1.410 |  -63.898 |      0 | True       |
| ES    |    2 |      0 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | 2570 |   -1.870 | -171.551 |      0 | True       |
| ES    |    3 |      0 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | 1402 |   -2.116 | -137.129 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.05; replicate best-eligible median 0.07, p95 0.50; real beats 30% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.44e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.054 | +0.086 | +0.008 | -0.029 | +11.2 | [-0.120, +0.058] | 0.01 | NO |
| 20% | add | -0.115 | +0.150 | -0.011 | -0.073 | +23.2 | [-0.247, +0.095] | 0.01 | NO |
| 30% | add | -0.180 | +0.191 | -0.055 | -0.128 | +35.3 | [-0.380, +0.116] | 0.01 | NO |
| 50% | add | -0.310 | +0.212 | -0.195 | -0.254 | +59.3 | [-0.641, +0.118] | 0.01 | NO |
| 10% | const | -0.061 | +0.094 | +0.007 | -0.034 | +1.3 | [-0.134, +0.063] | 0.01 | NO |
| 20% | const | -0.147 | +0.173 | -0.030 | -0.099 | +3.4 | [-0.315, +0.106] | 0.01 | NO |
| 30% | const | -0.264 | +0.213 | -0.139 | -0.207 | +5.5 | [-0.551, +0.123] | 0.01 | NO |
| 50% | const | -0.588 | +0.026 | -0.624 | -0.570 | +9.7 | [-1.180, +0.021] | 0.01 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -45,877, Sharpe -0.05, maxDD 609,844, worst wk -102,006; H1: net 179,636, Sharpe 0.99, maxDD 251,249, worst wk -86,532; H2: net 62,658, Sharpe 0.17, maxDD 451,361, worst wk -149,776; all: net 196,416, Sharpe 0.13, maxDD 780,910, worst wk -149,776
Correlation with pair (weekly): clean +0.31, H1 -0.04, H2 -0.02, all +0.18; worst-decile weeks (n=17) corr -0.02, sleeve mean in those weeks $-32,560, positive share 0.24.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.34 | 2.47 | 3.93 | -95,576 | -90,873 | 336,503 | -101,709 | 41.9 |
| clean | add 30% | 1.28 | 2.31 | 3.61 | -104,236 | -97,311 | 364,699 | -111,626 | 42.9 |
| clean | const 20% | 1.31 | 2.39 | 3.76 | -79,925 | -75,274 | 280,481 | -85,334 | 41.9 |
| clean | const 30% | 1.20 | 2.12 | 3.27 | -80,759 | -74,363 | 280,666 | -87,064 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.98 | 6.56 | 4.53 | -74,627 | -69,810 | 138,934 | -82,133 | 39.3 |
| H1 | add 30% | 3.02 | 6.66 | 4.79 | -76,782 | -71,700 | 135,288 | -84,733 | 39.3 |
| H1 | const 20% | 3.00 | 6.62 | 4.71 | -59,175 | -56,604 | 108,592 | -66,747 | 39.3 |
| H1 | const 30% | 3.04 | 6.68 | 4.84 | -58,811 | -51,891 | 97,042 | -61,654 | 39.3 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.29 | 4.66 | 3.84 | -87,396 | -83,298 | 205,983 | -92,267 | 37.8 |
| H2 | add 30% | 2.24 | 4.59 | 3.64 | -91,176 | -85,354 | 218,831 | -99,827 | 40.5 |
| H2 | const 20% | 2.27 | 4.63 | 3.74 | -71,429 | -67,461 | 169,926 | -76,838 | 40.5 |
| H2 | const 30% | 2.16 | 4.44 | 3.42 | -67,877 | -61,599 | 164,745 | -76,683 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.79 | 3.40 | 8.15 | -93,997 | -87,249 | 336,503 | -101,709 | 40.8 |
| all | add 30% | 1.73 | 3.26 | 7.57 | -102,054 | -92,417 | 364,699 | -111,626 | 42.0 |
| all | const 20% | 1.76 | 3.33 | 7.85 | -78,420 | -71,836 | 280,481 | -85,334 | 41.4 |
| all | const 30% | 1.65 | 3.06 | 6.95 | -78,690 | -69,865 | 280,666 | -87,064 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.115 / +0.150 / -0.011
- [FAIL] 3 worst week within share: all-in worst week +23.2% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.13 vs p95 -0.16 (rank 0.98)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.247, +0.095]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.154 / +0.114 / -0.036
- [PASS] 6 worst-decile corr <=+0.30: -0.02
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU9_ES); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (615 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1487 | +0.0526 | 0.53 |
| fixed | 1487 | +0.0181 | 0.18 |
| scaled | 1487 | +0.0181 | 0.18 |

Plateau neighbours (all-in 20% uplift; selected -0.073):
- {'sym': 'ES', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0'}: -0.221 (trades 1496)
- {'sym': 'ES', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '0.75', 'R': '2.0'}: -0.135 (trades 632)
- {'sym': 'ES', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '1.5'}: -0.067 (trades 641)
- {'sym': 'ES', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '3.125', 'tf': '30', 'S': '1.0', 'R': '2.0'}: +0.016 (trades 274)
- {'sym': 'ES', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.25', 'R': '2.0'}: +0.006 (trades 600)
- {'sym': 'ES', 'nb': '2', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '2.5'}: +0.004 (trades 600)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.92, p95 -0.16, real 0.13. Standalone Sharpe at 2x slippage -0.05.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 108 | -19 | -1.76 |
| 2014 | 134 | -9 | -0.66 |
| 2015 | 161 | -4 | -0.27 |
| 2016 | 136 | -18 | -1.55 |
| 2017 | 103 | -15 | -1.81 |
| 2018 | 166 | 22 | 1.42 |
| 2019 | 148 | -2 | -0.12 |
| 2020 | 150 | 6 | 0.37 |
| 2021 | 164 | 9 | 0.49 |
| 2022 | 217 | 55 | 2.58 |
| 2023 | 195 | -1 | -0.07 |
| 2024 | 208 | 7 | 0.35 |
| 2025 | 186 | -15 | -1.08 |
| 2026 | 140 | 3 | 0.16 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.05 | -0.12/+0.15/-0.01 |
| 2 tick entry / 2 tick exit | -0.44 | -0.19/-0.16/-0.04 |
| 3 tick entry / 3 tick exit | -1.03 | -0.30/-0.28/-0.10 |

DONE RU9_ES