# REPORT K4
**Verdict: LEAD** (6/7 measured gates pass). Selected cell model=d2, N=1, delta=0.08, mode=longonly; additive @20% clean/H1/H2 +0.18/+0.39/+0.19; standalone all-in weekly Sharpe 1.43 (2013-26 0.65, dev 2013-22 0.42); pair-window trades 267. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

K4 daily walk-forward LightGBM on ES/NQ/RTY/YM with price, VIX-state, COT and calendar features (16 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 100 clean trades): 16. Top cells by clean weekly Sharpe:

| model   |   N |   delta | mode      |   n |   sharpe |    net |   ypos | eligible   |
|:--------|----:|--------:|:----------|----:|---------:|-------:|-------:|:-----------|
| d2      |   1 |   0.080 | longonly  | 162 |    1.272 | 35.845 |      3 | True       |
| d4      |   1 |   0.080 | longonly  | 414 |    1.097 | 37.261 |      3 | True       |
| d2      |   1 |   0.080 | longshort | 169 |    1.005 | 29.949 |      2 | True       |
| d2      |   1 |   0.040 | longonly  | 899 |    0.847 | 42.783 |      2 | True       |
| d2      |   1 |   0.040 | longshort | 956 |    0.823 | 43.201 |      2 | True       |
| d4      |   1 |   0.040 | longonly  | 915 |    0.818 | 38.846 |      2 | True       |
| d4      |   1 |   0.080 | longshort | 511 |    0.775 | 33.254 |      2 | True       |
| d2      |   3 |   0.080 | longonly  | 319 |    0.581 | 27.989 |      2 | True       |
| d4      |   3 |   0.040 | longonly  | 490 |    0.574 | 37.231 |      2 | True       |
| d4      |   3 |   0.080 | longonly  | 350 |    0.535 | 28.228 |      3 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.27; replicate best-eligible median 1.14, p95 1.70; real beats 67% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.136e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.101 | +0.203 | +0.100 | +0.110 | +5.5 | [+0.051, +0.176] | 0.31 | NO |
| 20% | add | +0.183 | +0.392 | +0.193 | +0.203 | +11.8 | [+0.091, +0.326] | 0.31 | NO |
| 30% | add | +0.248 | +0.564 | +0.280 | +0.279 | +18.1 | [+0.118, +0.450] | 0.31 | NO |
| 50% | add | +0.329 | +0.848 | +0.430 | +0.382 | +30.6 | [+0.126, +0.649] | 0.31 | NO |
| 10% | const | +0.111 | +0.225 | +0.110 | +0.121 | -4.4 | [+0.056, +0.193] | 0.31 | NO |
| 20% | const | +0.218 | +0.480 | +0.237 | +0.243 | -8.1 | [+0.106, +0.390] | 0.31 | NO |
| 30% | const | +0.307 | +0.756 | +0.380 | +0.352 | -11.7 | [+0.130, +0.583] | 0.31 | NO |
| 50% | const | +0.358 | +1.205 | +0.663 | +0.434 | -19.0 | [-0.036, +0.917] | 0.31 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,124,230, Sharpe 1.23, maxDD 307,937, worst wk -136,683; H1: net 379,181, Sharpe 2.51, maxDD 72,717, worst wk -44,365; H2: net 297,847, Sharpe 1.72, maxDD 166,282, worst wk -109,560; all: net 1,801,259, Sharpe 1.43, maxDD 307,937, worst wk -136,683
Correlation with pair (weekly): clean +0.10, H1 -0.14, H2 -0.10, all +0.04; worst-decile weeks (n=17) corr +0.26, sleeve mean in those weeks $13,594, positive share 0.29.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.64 | 3.33 | 5.82 | -80,799 | -78,740 | 267,055 | -92,240 | 42.9 |
| clean | add 30% | 1.71 | 3.60 | 6.40 | -81,852 | -79,314 | 260,528 | -97,422 | 43.8 |
| clean | const 20% | 1.68 | 3.47 | 6.11 | -65,060 | -63,222 | 211,033 | -75,865 | 43.8 |
| clean | const 30% | 1.77 | 3.92 | 7.19 | -58,244 | -56,037 | 176,495 | -72,860 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.22 | 7.81 | 4.95 | -65,861 | -58,197 | 135,171 | -67,748 | 35.7 |
| H1 | add 30% | 3.39 | 8.71 | 5.35 | -59,987 | -54,281 | 132,228 | -63,156 | 35.7 |
| H1 | const 20% | 3.31 | 8.25 | 5.16 | -50,339 | -44,991 | 106,809 | -52,362 | 35.7 |
| H1 | const 30% | 3.58 | 9.94 | 5.87 | -36,704 | -34,472 | 90,250 | -40,077 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.49 | 5.27 | 3.78 | -79,970 | -76,128 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.57 | 5.55 | 3.91 | -79,970 | -74,599 | 217,425 | -82,524 | 44.4 |
| H2 | const 20% | 2.53 | 5.41 | 3.84 | -63,976 | -60,291 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 2.68 | 5.89 | 4.09 | -55,979 | -51,344 | 152,198 | -57,767 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.06 | 4.28 | 11.40 | -80,221 | -77,115 | 267,055 | -92,240 | 42.3 |
| all | add 30% | 2.13 | 4.60 | 12.38 | -80,923 | -76,893 | 260,528 | -97,422 | 42.9 |
| all | const 20% | 2.10 | 4.44 | 11.89 | -64,458 | -61,566 | 211,033 | -75,865 | 42.9 |
| all | const 30% | 2.21 | 4.98 | 13.71 | -57,278 | -53,790 | 176,495 | -72,860 | 42.9 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.183 / +0.392 / +0.193
- [PASS] 3 worst week within share: all-in worst week +11.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.43 vs p95 1.04 (rank 0.99)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.091, +0.326]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.179 / +0.388 / +0.189
- [PASS] 6 worst-decile corr <=+0.30: +0.26
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K4); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (267 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1934 | +0.0373 | 0.57 |
| fixed | 1934 | +0.0269 | 0.42 |
| scaled | 1934 | +0.0307 | 0.47 |

Plateau neighbours (all-in 20% uplift; selected +0.203):
- {'model': 'd2', 'N': '1', 'delta': '0.06', 'mode': 'longonly'}: +0.333 (trades 644)
- {'model': 'd2', 'N': '1', 'delta': '0.1', 'mode': 'longonly'}: +0.127 (trades 108)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.22, p95 1.04, real 1.43. Standalone Sharpe at 2x slippage 1.40.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 193 | 3 | 0.24 |
| 2017 | 289 | 36 | 2.13 |
| 2018 | 330 | -2 | -0.08 |
| 2019 | 198 | -11 | -0.70 |
| 2020 | 367 | 27 | 1.46 |
| 2021 | 299 | 17 | 1.06 |
| 2022 | 258 | -19 | -1.05 |
| 2023 | 21 | 5 | 2.06 |
| 2024 | 94 | 13 | 0.89 |
| 2025 | 90 | 31 | 2.52 |
| 2026 | 74 | 11 | 1.89 |


DONE K4