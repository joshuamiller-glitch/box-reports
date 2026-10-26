# REPORT RZ1_ZN
**Verdict: NO** (4/7 measured gates pass). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.07/+0.00/+0.04; standalone all-in weekly Sharpe 0.62 (2013-26 0.51, dev 2013-22 0.57); pair-window trades 59 (SMALL-SAMPLE). Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RZ1 ZN: structural-level limit-order retrace (FVG or 50% displacement retrace), tf15/30, stop floor 30 ticks, 2R target, tick-level fills (limit fills on trade-through by one tick, same-minute stop = loss), 1 tick slippage on stop/market exits, $4.36/contract. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 5. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |   n |   sharpe |    net |   ypos | eligible   |
|:------|:--------|-----:|------:|----:|---------:|-------:|-------:|:-----------|
| ZN    | FVG     |   15 | 0.500 |  30 |    0.824 |  5.671 |      3 | False      |
| ZN    | FVG     |   15 | 0.250 |  57 |    0.733 |  5.086 |      2 | True       |
| ZN    | DISP    |   30 | 1.500 |  66 |    0.329 |  1.770 |      1 | True       |
| ZN    | FVG     |   30 | 0.250 | 105 |    0.129 |  1.040 |      2 | True       |
| ZN    | FVG     |   30 | 0.500 |  65 |   -0.079 | -0.588 |      2 | True       |
| ZN    | DISP    |   15 | 1.500 |  44 |   -0.150 | -0.909 |      1 | True       |
| ZN    | DISP    |   15 | 2.000 |  19 |   -0.337 | -1.293 |      1 | False      |
| ZN    | DISP    |   30 | 2.000 |  33 |   -0.643 | -3.240 |      1 | False      |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.73; replicate best-eligible median 0.13, p95 0.55; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.209e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.045 | +0.000 | +0.023 | +0.031 | +0.5 | [-0.033, +0.101] | 0.15 | NO |
| 20% | add | +0.075 | +0.000 | +0.043 | +0.049 | +7.8 | [-0.071, +0.182] | 0.15 | NO |
| 30% | add | +0.090 | +0.000 | +0.060 | +0.056 | +15.0 | [-0.116, +0.242] | 0.15 | NO |
| 50% | add | +0.087 | +0.000 | +0.085 | +0.039 | +29.4 | [-0.224, +0.320] | 0.15 | NO |
| 10% | const | +0.049 | +0.000 | +0.025 | +0.033 | -8.8 | [-0.037, +0.111] | 0.15 | NO |
| 20% | const | +0.084 | +0.000 | +0.052 | +0.054 | -10.9 | [-0.093, +0.213] | 0.15 | NO |
| 30% | const | +0.093 | +0.000 | +0.077 | +0.049 | -13.0 | [-0.184, +0.299] | 0.15 | NO |
| 50% | const | -0.021 | +0.000 | +0.104 | -0.099 | -17.2 | [-0.535, +0.369] | 0.15 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 615,080, Sharpe 0.68, maxDD 305,308, worst wk -123,174; H1: net 0, Sharpe nan, maxDD 0, worst wk 0; H2: net 116,659, Sharpe 1.00, maxDD 21,279, worst wk -21,279; all: net 731,739, Sharpe 0.62, maxDD 305,308, worst wk -123,174
Correlation with pair (weekly): clean +0.10, H1 +nan, H2 +0.13, all +0.09; worst-decile weeks (n=17) corr -0.38, sleeve mean in those weeks $18,558, positive share 0.18.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.53 | 3.05 | 5.49 | -81,426 | -79,064 | 264,530 | -88,923 | 42.9 |
| clean | add 30% | 1.55 | 3.13 | 5.90 | -83,176 | -80,019 | 256,740 | -94,880 | 43.8 |
| clean | const 20% | 1.54 | 3.10 | 5.69 | -65,841 | -63,633 | 208,508 | -73,521 | 42.9 |
| clean | const 30% | 1.55 | 3.20 | 6.41 | -59,799 | -56,872 | 174,088 | -71,777 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 30% | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | const 20% | 2.83 | 6.09 | 3.91 | -62,088 | -52,824 | 121,370 | -62,630 | 39.3 |
| H1 | const 30% | 2.83 | 6.09 | 3.91 | -54,327 | -46,221 | 106,199 | -54,801 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.34 | 4.83 | 3.61 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.35 | 4.90 | 3.66 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | const 20% | 2.35 | 4.87 | 3.64 | -64,871 | -63,348 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 2.37 | 5.00 | 3.73 | -56,762 | -55,430 | 152,198 | -57,767 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.90 | 3.84 | 10.70 | -81,014 | -78,921 | 264,530 | -88,923 | 42.9 |
| all | add 30% | 1.91 | 3.90 | 11.31 | -82,181 | -79,539 | 256,740 | -94,880 | 43.5 |
| all | const 20% | 1.91 | 3.87 | 11.00 | -65,278 | -63,384 | 208,508 | -73,521 | 42.9 |
| all | const 30% | 1.90 | 3.94 | 12.06 | -58,577 | -56,233 | 174,088 | -71,777 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.075 / +0.000 / +0.043
- [PASS] 3 worst week within share: all-in worst week +7.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.62 vs p95 -0.11 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.071, +0.182]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.029 / +0.000 / +0.039
- [PASS] 6 worst-decile corr <=+0.30: -0.38
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ1_ZN); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (59 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 313 | +0.1400 | 0.76 |
| fixed | 313 | +0.0996 | 0.57 |
| scaled | 313 | +0.0996 | 0.57 |

Plateau neighbours (all-in 20% uplift; selected +0.049):
- {'sym': 'ZN', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.089 (trades 69)
- {'sym': 'ZN', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.048 (trades 61)
- {'sym': 'ZN', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: +0.038 (trades 57)
- {'sym': 'ZN', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: +0.039 (trades 50)
- {'sym': 'ZN', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.052 (trades 59)
- {'sym': 'ZN', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.051 (trades 59)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.95, p95 -0.11, real 0.62. Standalone Sharpe at 2x slippage 0.44.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 25 | 2 | 1.07 |
| 2014 | 13 | -1 | -0.50 |
| 2015 | 32 | 3 | 0.82 |
| 2016 | 18 | 1 | 0.46 |
| 2018 | 5 | -2 | -1.23 |
| 2019 | 10 | 1 | 1.84 |
| 2020 | 57 | 23 | 1.73 |
| 2021 | 10 | 1 | 0.74 |
| 2022 | 143 | 2 | 0.30 |
| 2023 | 70 | -1 | -0.29 |
| 2024 | 20 | -1 | -0.47 |
| 2025 | 19 | 4 | 2.02 |
| 2026 | 2 | 1 | 2.87 |


## Range dependence (net R per trade by realised day-range/ADR tercile of the trade-entry label, cuts from the whole sample)

| era | tercile | trades | mean net R | se |
|---|---|---|---|---|
| 2013-22 | low | 37 | +0.098 | 0.086 |
| 2013-22 | mid | 49 | -0.075 | 0.075 |
| 2013-22 | high | 227 | +0.137 | 0.055 |
| 2023-26 | mid | 4 | -0.059 | 0.227 |
| 2023-26 | high | 55 | +0.114 | 0.093 |

DONE RZ1_ZN