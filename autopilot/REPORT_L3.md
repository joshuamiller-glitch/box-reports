# REPORT L3
**Verdict: NO** (2/7 measured gates pass). Selected cell model=d4, N=3, gap=0.04; additive @20% clean/H1/H2 +0.21/-0.48/+0.20; standalone all-in weekly Sharpe 0.89 (2013-26 0.34, dev 2013-22 0.17); pair-window trades 706. Runtime 0.3 min (+selection 0.0 min). 6-worker pool.

L3 market-neutral cross-sectional sleeve from the K4 predictions: long highest-p index, short lowest-p index (8 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 100 clean trades): 7. Top cells by clean weekly Sharpe:

| model   |   N |   gap |   n |   sharpe |    net |   ypos | eligible   |
|:--------|----:|------:|----:|---------:|-------:|-------:|:-----------|
| d4      |   3 | 0.040 | 443 |    1.494 | 34.112 |      2 | True       |
| d4      |   3 | 0.080 | 330 |    1.358 | 25.947 |      2 | True       |
| d4      |   1 | 0.080 | 350 |    0.797 |  7.137 |      2 | True       |
| d4      |   1 | 0.040 | 780 |    0.792 | 10.318 |      2 | True       |
| d2      |   3 | 0.040 | 359 |    0.384 |  8.541 |      3 | True       |
| d2      |   1 | 0.080 |  20 |    0.143 |  0.307 |      1 | False      |
| d2      |   3 | 0.080 | 105 |   -0.404 | -4.582 |      1 | True       |
| d2      |   1 | 0.040 | 225 |   -0.818 | -5.732 |      0 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.49; replicate best-eligible median 1.27, p95 1.78; real beats 67% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.929e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.115 | -0.227 | +0.109 | +0.064 | +5.5 | [-0.025, +0.151] | 0.14 | NO |
| 20% | add | +0.211 | -0.476 | +0.197 | +0.108 | +14.5 | [-0.069, +0.284] | 0.14 | NO |
| 30% | add | +0.288 | -0.737 | +0.264 | +0.134 | +23.5 | [-0.128, +0.394] | 0.14 | NO |
| 50% | add | +0.392 | -1.259 | +0.342 | +0.140 | +41.5 | [-0.274, +0.548] | 0.14 | NO |
| 10% | const | +0.127 | -0.254 | +0.120 | +0.070 | -4.1 | [-0.030, +0.167] | 0.14 | NO |
| 20% | const | +0.252 | -0.606 | +0.233 | +0.123 | -4.8 | [-0.095, +0.341] | 0.14 | NO |
| 30% | const | +0.362 | -1.076 | +0.322 | +0.144 | -5.4 | [-0.219, +0.503] | 0.14 | NO |
| 50% | const | +0.459 | -2.323 | +0.322 | +0.014 | +15.4 | [-0.679, +0.689] | 0.14 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,277,080, Sharpe 1.40, maxDD 314,795, worst wk -157,931; H1: net -438,739, Sharpe -1.98, maxDD 493,070, worst wk -164,066; H2: net 442,136, Sharpe 1.49, maxDD 216,394, worst wk -96,271; all: net 1,280,476, Sharpe 0.89, maxDD 655,651, worst wk -164,066
Correlation with pair (weekly): clean +0.11, H1 +0.01, H2 +0.07, all +0.08; worst-decile weeks (n=17) corr +0.22, sleeve mean in those weeks $11,724, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.67 | 3.31 | 6.38 | -83,367 | -79,013 | 248,614 | -90,659 | 41.9 |
| clean | add 30% | 1.75 | 3.53 | 7.03 | -85,868 | -80,310 | 243,595 | -95,052 | 40.0 |
| clean | const 20% | 1.71 | 3.42 | 6.78 | -67,694 | -63,500 | 194,680 | -74,285 | 41.0 |
| clean | const 30% | 1.82 | 3.74 | 7.44 | -63,326 | -58,366 | 176,582 | -71,645 | 39.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.35 | 4.70 | 2.96 | -80,952 | -73,700 | 170,979 | -83,202 | 42.9 |
| H1 | add 30% | 2.09 | 3.97 | 2.56 | -82,623 | -80,283 | 180,613 | -85,659 | 42.9 |
| H1 | const 20% | 2.22 | 4.33 | 2.75 | -65,430 | -61,593 | 140,637 | -67,545 | 46.4 |
| H1 | const 30% | 1.75 | 3.10 | 1.77 | -64,931 | -62,123 | 160,488 | -67,689 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.49 | 5.41 | 4.46 | -86,907 | -77,216 | 190,669 | -94,508 | 44.4 |
| H2 | add 30% | 2.56 | 5.72 | 4.56 | -91,161 | -77,512 | 195,861 | -101,936 | 41.7 |
| H2 | const 20% | 2.53 | 5.57 | 4.51 | -71,227 | -61,659 | 154,612 | -78,578 | 41.7 |
| H2 | const 30% | 2.62 | 6.04 | 4.69 | -67,641 | -55,047 | 141,775 | -78,040 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.96 | 3.96 | 11.83 | -84,255 | -79,106 | 248,614 | -94,508 | 42.9 |
| all | add 30% | 1.99 | 4.05 | 12.60 | -87,222 | -80,739 | 243,595 | -101,936 | 41.1 |
| all | const 20% | 1.98 | 4.01 | 12.35 | -68,591 | -63,554 | 194,680 | -78,578 | 42.3 |
| all | const 30% | 2.00 | 4.10 | 11.66 | -65,400 | -59,375 | 194,065 | -78,040 | 40.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.211 / -0.476 / +0.197
- [PASS] 3 worst week within share: all-in worst week +14.5% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.89 vs p95 1.15 (rank 0.84)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.069, +0.284]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.193 / -0.492 / +0.186
- [PASS] 6 worst-decile corr <=+0.30: +0.22
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section L3); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (706 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1519 | +0.0216 | 0.35 |
| fixed | 1519 | +0.0101 | 0.17 |
| scaled | 1519 | +0.0153 | 0.25 |

Plateau neighbours (all-in 20% uplift; selected +0.108):
- {'model': 'd4', 'N': '3', 'gap': '0.03'}: +0.111 (trades 729)
- {'model': 'd4', 'N': '3', 'gap': '0.05'}: +0.110 (trades 670)
- {'model': 'd4', 'N': '2', 'gap': '0.04'}: -0.056 (trades 905)
- {'model': 'd4', 'N': '4', 'gap': '0.04'}: +0.074 (trades 571)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.37, p95 1.15, real 0.89. Standalone Sharpe at 2x slippage 0.80.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 186 | 9 | 0.60 |
| 2017 | 207 | 15 | 1.32 |
| 2018 | 228 | -16 | -1.11 |
| 2019 | 228 | -3 | -0.28 |
| 2020 | 224 | 9 | 0.53 |
| 2021 | 231 | 11 | 0.71 |
| 2022 | 215 | -10 | -1.59 |
| 2023 | 227 | -4 | -0.32 |
| 2024 | 221 | 34 | 2.94 |
| 2025 | 220 | 0 | 0.02 |
| 2026 | 170 | 2 | 0.17 |


DONE L3