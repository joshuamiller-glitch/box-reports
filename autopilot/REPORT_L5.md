# REPORT L5
**Verdict: NO** (1/7 measured gates pass). Selected cell rule=vixmed; additive @20% clean/H1/H2 +0.16/-0.03/-0.27; standalone all-in weekly Sharpe 0.41 (2013-26 0.60, dev 2013-22 0.61); pair-window trades 140. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

L5 conditional-beta sleeve: long the four indices while a VIX state is ON (5 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 5 cells, eligible (>= 20 clean trades): 5. Top cells by clean weekly Sharpe:

| rule         |   n |   sharpe |    net |   ypos | eligible   |
|:-------------|----:|---------:|-------:|-------:|:-----------|
| vixmed       |  68 |    1.729 | 63.851 |      2 | True       |
| both         |  68 |    1.729 | 63.851 |      2 | True       |
| falling      | 200 |    1.050 | 55.542 |      3 | True       |
| contango0.95 |  72 |    0.807 | 44.259 |      3 | True       |
| contango1.00 |  32 |    0.262 |  8.139 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.73; replicate best-eligible median 0.98, p95 1.25; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.13e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.088 | +0.013 | -0.122 | +0.032 | +9.4 | [-0.075, +0.135] | 0.45 | NO |
| 20% | add | +0.158 | -0.032 | -0.266 | +0.041 | +22.4 | [-0.169, +0.246] | 0.45 | NO |
| 30% | add | +0.211 | -0.123 | -0.426 | +0.030 | +38.7 | [-0.277, +0.331] | 0.45 | NO |
| 50% | add | +0.272 | -0.377 | -0.769 | -0.038 | +72.3 | [-0.519, +0.424] | 0.45 | NO |
| 10% | const | +0.096 | +0.011 | -0.137 | +0.034 | -0.6 | [-0.085, +0.149] | 0.45 | NO |
| 20% | const | +0.187 | -0.073 | -0.344 | +0.038 | +4.3 | [-0.221, +0.293] | 0.45 | NO |
| 30% | const | +0.256 | -0.280 | -0.645 | -0.008 | +12.2 | [-0.435, +0.397] | 0.45 | NO |
| 50% | const | +0.262 | -0.989 | -1.553 | -0.309 | +28.1 | [-1.078, +0.437] | 0.45 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 963,454, Sharpe 1.06, maxDD 522,037, worst wk -138,490; H1: net 103,699, Sharpe 0.33, maxDD 298,565, worst wk -270,389; H2: net -426,685, Sharpe -1.28, maxDD 630,915, worst wk -181,183; all: net 640,468, Sharpe 0.41, maxDD 684,832, worst wk -270,389
Correlation with pair (weekly): clean +0.07, H1 +0.01, H2 -0.08, all +0.01; worst-decile weeks (n=17) corr +0.26, sleeve mean in those weeks $10,757, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.62 | 3.13 | 4.83 | -89,733 | -83,205 | 315,106 | -100,649 | 44.8 |
| clean | add 30% | 1.67 | 3.22 | 4.42 | -95,970 | -86,642 | 366,004 | -114,498 | 44.8 |
| clean | const 20% | 1.65 | 3.18 | 4.61 | -74,281 | -67,939 | 272,444 | -86,059 | 43.8 |
| clean | const 30% | 1.72 | 3.27 | 4.04 | -73,188 | -64,810 | 302,012 | -92,613 | 40.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.80 | 5.60 | 3.48 | -89,663 | -75,681 | 176,595 | -101,038 | 32.1 |
| H1 | add 30% | 2.70 | 5.28 | 3.19 | -95,689 | -80,507 | 196,077 | -113,091 | 35.7 |
| H1 | const 20% | 2.76 | 5.44 | 3.33 | -74,141 | -62,475 | 149,069 | -85,652 | 32.1 |
| H1 | const 30% | 2.55 | 4.76 | 2.89 | -72,406 | -60,698 | 154,787 | -90,012 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.03 | 3.90 | 2.86 | -88,873 | -82,970 | 236,418 | -98,093 | 44.4 |
| H2 | add 30% | 1.87 | 3.52 | 2.56 | -92,766 | -84,862 | 247,489 | -105,878 | 44.4 |
| H2 | const 20% | 1.95 | 3.71 | 2.71 | -72,656 | -67,133 | 192,933 | -81,588 | 44.4 |
| H2 | const 30% | 1.65 | 3.04 | 2.14 | -72,016 | -63,845 | 188,797 | -81,120 | 50.0 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.90 | 3.66 | 8.93 | -90,798 | -83,910 | 315,106 | -101,038 | 42.3 |
| all | add 30% | 1.89 | 3.60 | 7.86 | -97,161 | -87,410 | 366,004 | -114,498 | 42.9 |
| all | const 20% | 1.89 | 3.64 | 8.35 | -75,184 | -68,479 | 272,444 | -86,059 | 41.7 |
| all | const 30% | 1.85 | 3.47 | 6.86 | -74,797 | -65,477 | 302,012 | -92,613 | 41.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.158 / -0.032 / -0.266
- [FAIL] 3 worst week within share: all-in worst week +22.4% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.41 vs p95 1.23 (rank 0.19)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.169, +0.246]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.156 / -0.035 / -0.268
- [PASS] 6 worst-decile corr <=+0.30: +0.26
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section L5); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (140 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 406 | +0.3299 | 0.64 |
| fixed | 406 | +0.3145 | 0.61 |
| scaled | 406 | +0.3235 | 0.63 |

Plateau neighbours (all-in 20% uplift; selected +0.041):

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.65, p95 1.23, real 0.41. Standalone Sharpe at 2x slippage 0.40.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 36 | 38 | 2.00 |
| 2014 | 43 | -5 | -0.27 |
| 2015 | 60 | -43 | -3.06 |
| 2016 | 30 | 16 | 0.93 |
| 2017 | 37 | 67 | 2.54 |
| 2018 | 40 | 5 | 0.39 |
| 2019 | 64 | 37 | 1.78 |
| 2020 | 16 | 25 | 1.68 |
| 2021 | 48 | 2 | 0.07 |
| 2022 | 32 | -15 | -0.96 |
| 2023 | 28 | 35 | 1.24 |
| 2024 | 32 | 28 | 1.42 |
| 2025 | 44 | 11 | 0.53 |
| 2026 | 48 | -21 | -1.19 |


## Beta / drift test (report): regression of the sleeve's daily P&L on the always-long basket of the same instruments (unit risk), 2023-08..2026-10: beta +0.361; sleeve weekly Sharpe 0.41; always-long basket 0.65; ALPHA weekly Sharpe 0.01, bootstrap 90% CI [-0.88, +0.93] (alpha CI includes zero).

DONE L5