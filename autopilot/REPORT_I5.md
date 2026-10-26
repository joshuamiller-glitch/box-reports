# REPORT I5
**Verdict: NO** (2/7 measured gates pass). Selected cell m=5, thr=4, h=5, T=NQ; additive @20% clean/H1/H2 -0.04/-0.23/-0.03; standalone all-in weekly Sharpe -0.20 (2013-26 -2.23, dev 2013-22 -3.09); pair-window trades 2085. Runtime 0.1 min (+selection 0.0 min). 7-worker pool.

ES-NQ 1-minute lead-lag catch-up: z-scored relative return over m minutes, trade the laggard, time exit 2/5/10 min. NT8: needs both instruments in one strategy (multi-instrument). Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on the clean span only (Gate Amendment 2), H1/H2 read once for one cell; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 54 cells, eligible (>= 60 clean trades): 54. Top cells by clean weekly Sharpe:

|   m |   thr |   h | T   |    n |   sharpe |    net |   ypos | eligible   |
|----:|------:|----:|:----|-----:|---------:|-------:|-------:|:-----------|
|   5 |     4 |   5 | NQ  | 1353 |    0.076 |  0.418 |      2 | True       |
|   5 |     4 |  10 | NQ  | 1091 |   -0.045 | -0.274 |      2 | True       |
|   5 |     3 |   5 | NQ  | 2488 |   -0.261 | -1.748 |      1 | True       |
|   1 |     4 |   5 | NQ  | 1501 |   -0.295 | -1.719 |      0 | True       |
|   3 |     3 |  10 | NQ  | 2079 |   -0.425 | -3.687 |      1 | True       |
|   1 |     4 |  10 | NQ  | 1189 |   -0.487 | -3.055 |      1 | True       |
|   3 |     2 |  10 | NQ  | 4277 |   -0.577 | -6.296 |      1 | True       |
|   1 |     3 |   5 | NQ  | 2903 |   -0.690 | -5.117 |      1 | True       |
|   5 |     3 |  10 | NQ  | 1908 |   -0.703 | -5.073 |      1 | True       |
|   1 |     2 |  10 | NQ  | 4829 |   -0.741 | -8.571 |      0 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.08; replicate best-eligible median 0.24, p95 0.62; real beats 33% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.666e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.013 | -0.095 | -0.010 | -0.029 | +4.4 | [-0.105, +0.050] | 0.39 | NO |
| 20% | add | -0.040 | -0.226 | -0.029 | -0.074 | +15.2 | [-0.224, +0.081] | 0.39 | NO |
| 30% | add | -0.076 | -0.387 | -0.058 | -0.131 | +26.1 | [-0.353, +0.092] | 0.39 | NO |
| 50% | add | -0.169 | -0.758 | -0.143 | -0.271 | +47.8 | [-0.626, +0.078] | 0.39 | NO |
| 10% | const | -0.016 | -0.108 | -0.011 | -0.034 | -5.0 | [-0.118, +0.054] | 0.39 | NO |
| 20% | const | -0.057 | -0.303 | -0.042 | -0.101 | -3.5 | [-0.287, +0.088] | 0.39 | NO |
| 30% | const | -0.134 | -0.621 | -0.109 | -0.218 | -2.0 | [-0.526, +0.087] | 0.39 | NO |
| 50% | const | -0.423 | -1.640 | -0.470 | -0.651 | +1.1 | [-1.274, -0.054] | 0.39 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 69,615, Sharpe 0.08, maxDD 583,099, worst wk -114,942; H1: net -238,016, Sharpe -1.00, maxDD 376,417, worst wk -151,112; H2: net -103,072, Sharpe -0.49, maxDD 266,280, worst wk -101,123; all: net -271,473, Sharpe -0.20, maxDD 583,099, worst wk -151,112
Correlation with pair (weekly): clean +0.10, H1 -0.11, H2 -0.18, all +0.01; worst-decile weeks (n=17) corr -0.43, sleeve mean in those weeks $12,725, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.42 | 2.74 | 4.93 | -87,250 | -81,648 | 272,343 | -95,080 | 44.8 |
| clean | add 30% | 1.38 | 2.70 | 5.03 | -92,166 | -84,738 | 268,460 | -104,043 | 46.7 |
| clean | const 20% | 1.40 | 2.72 | 4.98 | -71,766 | -66,309 | 216,321 | -79,649 | 45.7 |
| clean | const 30% | 1.33 | 2.62 | 4.97 | -69,922 | -62,652 | 191,705 | -80,897 | 47.6 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.60 | 5.36 | 4.03 | -76,204 | -68,266 | 135,441 | -77,054 | 39.3 |
| H1 | add 30% | 2.44 | 4.87 | 3.50 | -75,501 | -72,132 | 149,043 | -76,438 | 39.3 |
| H1 | const 20% | 2.52 | 5.12 | 3.96 | -60,682 | -56,159 | 108,007 | -61,397 | 39.3 |
| H1 | const 30% | 2.21 | 4.20 | 2.66 | -55,215 | -53,972 | 129,591 | -57,478 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.27 | 4.70 | 3.78 | -76,423 | -73,564 | 195,781 | -80,429 | 44.4 |
| H2 | add 30% | 2.24 | 4.65 | 3.76 | -79,670 | -72,905 | 194,424 | -90,541 | 44.4 |
| H2 | const 20% | 2.25 | 4.68 | 3.85 | -62,437 | -58,588 | 153,014 | -68,388 | 44.4 |
| H2 | const 30% | 2.19 | 4.53 | 3.54 | -58,691 | -50,781 | 141,780 | -72,480 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.78 | 3.51 | 9.66 | -84,267 | -79,105 | 272,343 | -95,080 | 44.0 |
| all | add 30% | 1.72 | 3.40 | 9.70 | -88,677 | -80,867 | 268,460 | -104,043 | 45.2 |
| all | const 20% | 1.75 | 3.46 | 9.68 | -69,178 | -63,837 | 216,321 | -79,649 | 44.6 |
| all | const 30% | 1.64 | 3.23 | 9.38 | -67,407 | -59,695 | 191,705 | -80,897 | 45.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.040 / -0.226 / -0.029
- [PASS] 3 worst week within share: all-in worst week +15.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.20 vs p95 -0.11 (rank 0.93)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.224, +0.081]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.121 / -0.303 / -0.068
- [PASS] 6 worst-decile corr <=+0.30: -0.43
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I5); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2085 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 5246 | -0.0046 | -1.10 |
| fixed | 5246 | -0.0133 | -3.09 |
| scaled | 5246 | -0.0071 | -1.70 |

Plateau neighbours (all-in 20% uplift; selected -0.074):
- {'m': '4', 'thr': '4', 'h': '5', 'T': 'NQ'}: -0.173 (trades 2062)
- {'m': '6', 'thr': '4', 'h': '5', 'T': 'NQ'}: -0.136 (trades 2072)
- {'m': '5', 'thr': '3.0', 'h': '5', 'T': 'NQ'}: -0.222 (trades 3868)
- {'m': '5', 'thr': '5.0', 'h': '5', 'T': 'NQ'}: -0.130 (trades 1198)
- {'m': '5', 'thr': '4', 'h': '4', 'T': 'NQ'}: -0.160 (trades 2195)
- {'m': '5', 'thr': '4', 'h': '6', 'T': 'NQ'}: -0.097 (trades 1994)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.86, p95 -0.11, real -0.20. Standalone Sharpe at 2x slippage -0.58.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 334 | -7 | -3.56 |
| 2014 | 437 | -7 | -2.81 |
| 2015 | 358 | -5 | -1.67 |
| 2016 | 528 | -9 | -4.79 |
| 2017 | 597 | -11 | -4.64 |
| 2018 | 621 | -8 | -3.44 |
| 2019 | 602 | -9 | -3.53 |
| 2020 | 477 | -5 | -2.62 |
| 2021 | 612 | -9 | -4.14 |
| 2022 | 680 | -1 | -0.33 |
| 2023 | 605 | -1 | -0.52 |
| 2024 | 709 | -1 | -0.47 |
| 2025 | 641 | 1 | 0.44 |
| 2026 | 463 | -2 | -1.16 |


DONE I5