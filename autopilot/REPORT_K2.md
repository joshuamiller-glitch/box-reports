# REPORT K2
**Verdict: NO** (1/7 measured gates pass). Selected cell L=40, B=60, tmin=2.0, uni=idx; additive @20% clean/H1/H2 -0.10/-0.36/-0.06; standalone all-in weekly Sharpe -0.80 (2013-26 -1.73, dev 2013-22 -2.16); pair-window trades 1563. Runtime 0.1 min (+selection 0.0 min). 6-worker pool.

K2 walk-forward intraday seasonality sleeve: per-bucket drift estimated on the prior L days, traded when |t|>=tmin; indices or other assets (16 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 100 clean trades): 16. Top cells by clean weekly Sharpe:

|   L |   B |   tmin | uni   |     n |   sharpe |      net |   ypos | eligible   |
|----:|----:|-------:|:------|------:|---------:|---------:|-------:|:-----------|
|  40 |  60 |  2.000 | idx   |   974 |   -0.589 |   -6.654 |      1 | True       |
|  80 |  60 |  2.000 | idx   |   655 |   -1.058 |  -10.058 |      0 | True       |
|  40 |  30 |  2.000 | idx   |  2648 |   -1.578 |  -22.332 |      0 | True       |
|  80 |  30 |  2.000 | idx   |  1991 |   -2.280 |  -23.820 |      0 | True       |
|  40 |  60 |  1.000 | idx   |  7210 |   -2.335 |  -87.826 |      1 | True       |
|  80 |  60 |  1.000 | idx   |  6520 |   -2.520 |  -77.343 |      0 | True       |
|  40 |  30 |  1.000 | idx   | 16252 |   -3.535 | -139.990 |      0 | True       |
|  40 |  60 |  2.000 | oth   |  1396 |   -3.815 |  -34.825 |      0 | True       |
|  80 |  60 |  2.000 | oth   |  1175 |   -4.127 |  -31.666 |      0 | True       |
|  80 |  30 |  1.000 | idx   | 14559 |   -4.865 | -147.127 |      0 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.59; replicate best-eligible median -0.70, p95 0.38; real beats 67% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=8.06e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.045 | -0.173 | -0.017 | -0.058 | +11.1 | [-0.150, +0.036] | 0.97 | NO |
| 20% | add | -0.104 | -0.365 | -0.062 | -0.135 | +28.6 | [-0.318, +0.052] | 0.97 | NO |
| 30% | add | -0.177 | -0.570 | -0.133 | -0.228 | +46.2 | [-0.502, +0.055] | 0.97 | NO |
| 50% | add | -0.349 | -1.005 | -0.343 | -0.449 | +81.3 | [-0.893, +0.008] | 0.97 | NO |
| 10% | const | -0.051 | -0.194 | -0.021 | -0.066 | +1.7 | [-0.168, +0.038] | 0.97 | NO |
| 20% | const | -0.139 | -0.466 | -0.094 | -0.180 | +9.9 | [-0.409, +0.057] | 0.97 | NO |
| 30% | const | -0.284 | -0.848 | -0.260 | -0.367 | +18.1 | [-0.750, +0.029] | 0.97 | NO |
| 50% | const | -0.792 | -2.039 | -0.990 | -1.022 | +34.6 | [-1.798, -0.257] | 0.97 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -536,333, Sharpe -0.59, maxDD 1,059,503, worst wk -234,593; H1: net -391,887, Sharpe -2.31, maxDD 563,619, worst wk -108,622; H2: net -208,805, Sharpe -0.59, maxDD 492,111, worst wk -255,446; all: net -1,137,025, Sharpe -0.80, maxDD 1,858,984, worst wk -255,446
Correlation with pair (weekly): clean -0.15, H1 -0.10, H2 -0.24, all -0.16; worst-decile weeks (n=17) corr -0.08, sleeve mean in those weeks $8,510, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.36 | 2.46 | 4.42 | -87,743 | -81,567 | 276,897 | -106,159 | 44.8 |
| clean | add 30% | 1.28 | 2.27 | 4.25 | -95,119 | -86,622 | 275,290 | -120,653 | 42.9 |
| clean | const 20% | 1.32 | 2.37 | 4.33 | -72,640 | -67,276 | 220,875 | -90,725 | 43.8 |
| clean | const 30% | 1.18 | 2.01 | 3.94 | -75,165 | -65,780 | 195,309 | -97,502 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.46 | 4.77 | 3.21 | -84,952 | -72,959 | 160,370 | -88,260 | 39.3 |
| H1 | add 30% | 2.26 | 4.18 | 2.89 | -88,623 | -76,590 | 164,698 | -93,924 | 39.3 |
| H1 | const 20% | 2.36 | 4.47 | 3.05 | -69,430 | -59,820 | 130,027 | -72,874 | 42.9 |
| H1 | const 30% | 1.98 | 3.50 | 2.50 | -65,340 | -56,881 | 119,185 | -70,845 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.23 | 4.55 | 3.28 | -80,583 | -78,932 | 219,612 | -81,512 | 44.4 |
| H2 | add 30% | 2.16 | 4.40 | 3.17 | -80,330 | -78,805 | 220,706 | -81,006 | 41.7 |
| H2 | const 20% | 2.20 | 4.48 | 3.22 | -64,365 | -63,095 | 176,127 | -65,007 | 44.4 |
| H2 | const 30% | 2.04 | 4.09 | 2.99 | -56,003 | -55,140 | 157,078 | -56,248 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.72 | 3.22 | 8.88 | -86,591 | -81,345 | 276,897 | -106,159 | 44.0 |
| all | add 30% | 1.63 | 2.98 | 8.51 | -92,204 | -85,019 | 275,290 | -120,653 | 42.3 |
| all | const 20% | 1.68 | 3.10 | 8.70 | -71,079 | -66,545 | 220,875 | -90,725 | 44.0 |
| all | const 30% | 1.49 | 2.64 | 7.88 | -70,998 | -63,487 | 195,309 | -97,502 | 42.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.104 / -0.365 / -0.062
- [FAIL] 3 worst week within share: all-in worst week +28.6% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.80 vs p95 -0.36 (rank 0.80)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.318, +0.052]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.200 / -0.446 / -0.115
- [PASS] 6 worst-decile corr <=+0.30: -0.08
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K2); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1563 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 4330 | -0.0050 | -0.52 |
| fixed | 4330 | -0.0213 | -2.16 |
| scaled | 4330 | -0.0115 | -1.19 |

Plateau neighbours (all-in 20% uplift; selected -0.135):
- {'L': '30', 'B': '60', 'tmin': '2.0', 'uni': 'idx'}: -0.124 (trades 1745)
- {'L': '40', 'B': '60', 'tmin': '1.5', 'uni': 'idx'}: -0.398 (trades 4579)
- {'L': '40', 'B': '45', 'tmin': '2.0', 'uni': 'idx'}: -0.373 (trades 1966)
- {'L': '50', 'B': '60', 'tmin': '2.0', 'uni': 'idx'}: -0.118 (trades 1478)
- {'L': '40', 'B': '60', 'tmin': '2.5', 'uni': 'idx'}: -0.043 (trades 401)
- {'L': '40', 'B': '75', 'tmin': '2.0', 'uni': 'idx'}: -0.192 (trades 1139)

Own random-entry null: 500 draws, standalone all-in Sharpe median -1.17, p95 -0.36, real -0.80. Standalone Sharpe at 2x slippage -1.23.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 466 | -14 | -3.51 |
| 2014 | 405 | -14 | -3.93 |
| 2015 | 371 | -10 | -1.73 |
| 2016 | 453 | -9 | -2.23 |
| 2017 | 497 | -15 | -3.30 |
| 2018 | 627 | -8 | -2.07 |
| 2019 | 399 | -7 | -3.20 |
| 2020 | 382 | -0 | -0.02 |
| 2021 | 421 | -10 | -2.12 |
| 2022 | 309 | -5 | -0.97 |
| 2023 | 542 | -2 | -0.35 |
| 2024 | 458 | -4 | -0.63 |
| 2025 | 437 | -8 | -2.05 |
| 2026 | 339 | -3 | -0.68 |


DONE K2