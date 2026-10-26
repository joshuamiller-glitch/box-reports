# REPORT I4
**Verdict: NO** (2/7 measured gates pass). Selected cell R=5, K=2, mode=follow, H=12; additive @20% clean/H1/H2 +0.03/-0.16/-0.35; standalone all-in weekly Sharpe 0.09 (2013-26 -0.47, dev 2013-22 -0.59); pair-window trades 1300. Runtime 0.2 min (+selection 0.0 min). 7-worker pool.

Volume-surge continuation/reversal on 5-minute bars (ES/NQ/YM/RTY): rvol vs same-slot 20-day median and a large bar, time exit 3/6/12 bars. NT8: 5-minute bar strategy. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on the clean span only (Gate Amendment 2), H1/H2 read once for one cell; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 36 cells, eligible (>= 60 clean trades): 36. Top cells by clean weekly Sharpe:

|   R |   K | mode   |   H |    n |   sharpe |     net |   ypos | eligible   |
|----:|----:|:-------|----:|-----:|---------:|--------:|-------:|:-----------|
|   5 |   2 | follow |  12 |  743 |    0.569 |   9.047 |      3 | True       |
|   5 |   1 | fade   |   3 | 1336 |    0.056 |   0.687 |      1 | True       |
|   3 |   2 | follow |  12 | 1746 |    0.017 |   0.368 |      1 | True       |
|   5 |   2 | follow |   6 |  793 |   -0.001 |  -0.008 |      1 | True       |
|   5 |   1 | follow |   6 | 1172 |   -0.041 |  -0.692 |      1 | True       |
|   5 |   1 | follow |  12 | 1050 |   -0.077 |  -1.157 |      2 | True       |
|   2 |   2 | follow |  12 | 3087 |   -0.265 |  -7.209 |      1 | True       |
|   5 |   2 | fade   |   3 |  869 |   -0.347 |  -3.631 |      1 | True       |
|   3 |   1 | follow |  12 | 3152 |   -0.502 | -13.206 |      1 | True       |
|   3 |   1 | fade   |   3 | 4306 |   -0.589 | -10.274 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.57; replicate best-eligible median 0.15, p95 1.23; real beats 83% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=5.734e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.020 | -0.055 | -0.173 | -0.034 | +5.7 | [-0.123, +0.050] | 0.01 | NO |
| 20% | add | +0.027 | -0.160 | -0.353 | -0.085 | +17.9 | [-0.255, +0.082] | 0.01 | NO |
| 30% | add | +0.023 | -0.297 | -0.535 | -0.147 | +32.5 | [-0.394, +0.093] | 0.01 | NO |
| 50% | add | -0.011 | -0.606 | -0.888 | -0.288 | +72.3 | [-0.671, +0.079] | 0.01 | NO |
| 10% | const | +0.022 | -0.064 | -0.192 | -0.039 | -3.6 | [-0.137, +0.055] | 0.01 | NO |
| 20% | const | +0.026 | -0.225 | -0.444 | -0.114 | -0.9 | [-0.324, +0.089] | 0.01 | NO |
| 30% | const | +0.004 | -0.495 | -0.765 | -0.236 | +10.7 | [-0.572, +0.091] | 0.01 | NO |
| 50% | const | -0.150 | -1.243 | -1.608 | -0.628 | +35.8 | [-1.251, -0.048] | 0.01 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 518,791, Sharpe 0.57, maxDD 538,948, worst wk -105,070; H1: net 35,772, Sharpe 0.11, maxDD 303,342, worst wk -150,672; H2: net -422,365, Sharpe -1.37, maxDD 532,902, worst wk -163,936; all: net 132,199, Sharpe 0.09, maxDD 652,755, worst wk -163,936
Correlation with pair (weekly): clean +0.20, H1 +0.10, H2 +0.18, all +0.17; worst-decile weeks (n=17) corr +0.17, sleeve mean in those weeks $-11,687, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.49 | 2.92 | 4.96 | -87,221 | -82,837 | 288,828 | -97,263 | 44.8 |
| clean | add 30% | 1.48 | 2.95 | 5.07 | -91,731 | -85,318 | 293,187 | -107,265 | 44.8 |
| clean | const 20% | 1.49 | 2.94 | 5.02 | -71,542 | -67,255 | 232,806 | -81,811 | 45.7 |
| clean | const 30% | 1.46 | 2.95 | 5.03 | -68,359 | -62,622 | 216,151 | -84,087 | 46.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.67 | 6.14 | 3.11 | -65,331 | -60,117 | 193,141 | -77,712 | 42.9 |
| H1 | add 30% | 2.53 | 5.92 | 2.83 | -69,459 | -65,802 | 213,855 | -77,425 | 50.0 |
| H1 | const 20% | 2.60 | 6.05 | 2.96 | -53,315 | -50,356 | 162,798 | -62,055 | 46.4 |
| H1 | const 30% | 2.33 | 5.39 | 2.53 | -53,844 | -51,205 | 168,341 | -53,939 | 50.0 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 1.94 | 3.82 | 3.20 | -91,176 | -84,835 | 211,550 | -92,992 | 44.4 |
| H2 | add 30% | 1.76 | 3.39 | 2.74 | -101,081 | -89,811 | 231,580 | -109,385 | 44.4 |
| H2 | const 20% | 1.85 | 3.61 | 2.96 | -76,903 | -69,858 | 177,252 | -80,951 | 44.4 |
| H2 | const 30% | 1.53 | 2.87 | 2.25 | -79,672 | -67,346 | 180,133 | -91,324 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.77 | 3.53 | 9.39 | -87,286 | -82,413 | 288,828 | -97,263 | 44.6 |
| all | add 30% | 1.71 | 3.43 | 9.29 | -92,544 | -85,166 | 293,187 | -109,385 | 45.8 |
| all | const 20% | 1.74 | 3.48 | 9.34 | -71,919 | -67,027 | 232,806 | -81,811 | 45.8 |
| all | const 30% | 1.62 | 3.25 | 8.88 | -69,612 | -62,701 | 216,151 | -91,324 | 47.0 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.027 / -0.160 / -0.353
- [PASS] 3 worst week within share: all-in worst week +17.9% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.09 vs p95 0.28 (rank 0.91)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.255, +0.082]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.018 / -0.210 / -0.395
- [PASS] 6 worst-decile corr <=+0.30: +0.17
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I4); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1300 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 3995 | +0.0055 | 0.29 |
| fixed | 3995 | -0.0110 | -0.59 |
| scaled | 3995 | -0.0010 | -0.06 |

Plateau neighbours (all-in 20% uplift; selected -0.085):
- {'R': '3.75', 'K': '2', 'mode': 'follow', 'H': '12'}: -0.020 (trades 1991)
- {'R': '6.25', 'K': '2', 'mode': 'follow', 'H': '12'}: -0.021 (trades 907)
- {'R': '5', 'K': '1.5', 'mode': 'follow', 'H': '12'}: -0.082 (trades 1616)
- {'R': '5', 'K': '2.5', 'mode': 'follow', 'H': '12'}: -0.038 (trades 1029)
- {'R': '5', 'K': '2', 'mode': 'follow', 'H': '9'}: -0.067 (trades 1325)
- {'R': '5', 'K': '2', 'mode': 'follow', 'H': '15'}: -0.048 (trades 1276)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.69, p95 0.28, real 0.09. Standalone Sharpe at 2x slippage -0.14.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 372 | -8 | -1.42 |
| 2014 | 501 | -24 | -2.58 |
| 2015 | 396 | -9 | -1.08 |
| 2016 | 263 | -8 | -1.20 |
| 2017 | 567 | -8 | -1.24 |
| 2018 | 429 | -3 | -0.40 |
| 2019 | 543 | 17 | 1.91 |
| 2020 | 271 | 5 | 0.79 |
| 2021 | 373 | 0 | 0.10 |
| 2022 | 280 | -7 | -0.81 |
| 2023 | 296 | -5 | -0.72 |
| 2024 | 363 | 2 | 0.25 |
| 2025 | 436 | 2 | 0.26 |
| 2026 | 398 | -5 | -0.85 |


DONE I4