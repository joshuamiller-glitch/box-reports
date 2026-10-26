# REPORT RZ3
**Verdict: NO** (2/7 measured gates pass). Selected cell orm=15, q=0.0; additive @20% clean/H1/H2 -0.05/+0.06/-0.07; standalone all-in weekly Sharpe 0.13 (2013-26 0.44, dev 2013-22 0.43); pair-window trades 797. Runtime 1.4 min (+selection 0.3 min). 10-worker pool.

RZ3 pre-open range-expansion forecast (simple percentile rules) and NQ opening-range breakout conditioned on it (6 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 6 cells, eligible (>= 40 clean trades): 6. Top cells by clean weekly Sharpe:

|   orm |     q |   n |   sharpe |     net |   ypos | eligible   |
|------:|------:|----:|---------:|--------:|-------:|:-----------|
|    15 | 0.000 | 497 |    0.046 |   1.767 |      2 | True       |
|    15 | 0.500 | 254 |    0.021 |   0.639 |      1 | True       |
|    30 | 0.000 | 497 |   -0.485 | -17.462 |      0 | True       |
|    15 | 0.670 | 102 |   -0.556 |  -9.281 |      1 | True       |
|    30 | 0.500 | 254 |   -0.563 | -16.283 |      0 | True       |
|    30 | 0.670 | 102 |   -1.185 | -16.556 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.05; replicate best-eligible median 0.56, p95 1.51; real beats 0% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.352e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.017 | +0.039 | -0.031 | -0.014 | +4.9 | [-0.101, +0.068] | 0.09 | NO |
| 20% | add | -0.047 | +0.056 | -0.070 | -0.042 | +10.7 | [-0.215, +0.122] | 0.09 | NO |
| 30% | add | -0.087 | +0.050 | -0.116 | -0.082 | +18.2 | [-0.339, +0.161] | 0.09 | NO |
| 50% | add | -0.185 | -0.018 | -0.221 | -0.185 | +34.8 | [-0.591, +0.195] | 0.09 | NO |
| 10% | const | -0.020 | +0.042 | -0.034 | -0.017 | -5.0 | [-0.114, +0.075] | 0.09 | NO |
| 20% | const | -0.066 | +0.056 | -0.092 | -0.061 | -8.7 | [-0.276, +0.143] | 0.09 | NO |
| 30% | const | -0.148 | +0.014 | -0.182 | -0.146 | -9.8 | [-0.501, +0.191] | 0.09 | NO |
| 50% | const | -0.446 | -0.366 | -0.507 | -0.478 | +0.5 | [-1.142, +0.160] | 0.09 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 41,571, Sharpe 0.05, maxDD 702,068, worst wk -158,001; H1: net 83,445, Sharpe 0.45, maxDD 228,056, worst wk -83,640; H2: net 49,112, Sharpe 0.21, maxDD 400,011, worst wk -78,004; all: net 174,129, Sharpe 0.13, maxDD 702,068, worst wk -158,001
Correlation with pair (weekly): clean +0.10, H1 -0.04, H2 +0.25, all +0.11; worst-decile weeks (n=17) corr +0.28, sleeve mean in those weeks $3,561, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.41 | 2.69 | 4.30 | -87,503 | -83,904 | 311,283 | -91,319 | 41.0 |
| clean | add 30% | 1.37 | 2.59 | 4.07 | -92,609 | -87,091 | 329,714 | -97,548 | 46.7 |
| clean | const 20% | 1.39 | 2.64 | 4.19 | -72,045 | -68,395 | 256,119 | -75,307 | 44.8 |
| clean | const 30% | 1.31 | 2.43 | 3.68 | -69,422 | -64,171 | 256,628 | -74,430 | 45.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.88 | 6.47 | 4.16 | -66,471 | -62,738 | 146,786 | -71,338 | 39.3 |
| H1 | add 30% | 2.88 | 6.50 | 4.09 | -64,668 | -61,092 | 151,363 | -67,864 | 39.3 |
| H1 | const 20% | 2.88 | 6.50 | 4.12 | -51,189 | -49,532 | 119,260 | -55,681 | 39.3 |
| H1 | const 30% | 2.84 | 6.38 | 3.88 | -46,495 | -45,517 | 113,475 | -48,612 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.23 | 4.72 | 3.41 | -82,002 | -78,109 | 226,274 | -87,509 | 47.2 |
| H2 | add 30% | 2.18 | 4.71 | 3.36 | -82,459 | -77,571 | 230,699 | -90,002 | 44.4 |
| H2 | const 20% | 2.20 | 4.72 | 3.39 | -65,784 | -62,272 | 182,789 | -71,005 | 44.4 |
| H2 | const 30% | 2.11 | 4.66 | 3.31 | -59,502 | -55,259 | 165,471 | -65,245 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.81 | 3.59 | 8.74 | -86,423 | -80,999 | 311,283 | -91,319 | 42.3 |
| all | add 30% | 1.77 | 3.50 | 8.30 | -90,526 | -83,057 | 329,714 | -97,548 | 45.2 |
| all | const 20% | 1.79 | 3.55 | 8.52 | -70,774 | -65,557 | 256,119 | -75,307 | 44.0 |
| all | const 30% | 1.71 | 3.34 | 7.53 | -67,090 | -60,572 | 256,628 | -74,430 | 43.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.047 / +0.056 / -0.070
- [PASS] 3 worst week within share: all-in worst week +10.7% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.13 vs p95 0.13 (rank 0.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.215, +0.122]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.048 / +0.080 / -0.070
- [PASS] 6 worst-decile corr <=+0.30: +0.28
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ3); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (797 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2479 | +0.0358 | 0.49 |
| fixed | 2479 | +0.0316 | 0.43 |
| scaled | 2479 | +0.0316 | 0.43 |

Plateau neighbours (all-in 20% uplift; selected -0.042):
- {'orm': '11', 'q': '0.0'}: -0.128 (trades 797)
- {'orm': '19', 'q': '0.0'}: -0.092 (trades 797)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.13, p95 0.13, real 0.13. Standalone Sharpe at 2x slippage 0.14.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 239 | -1 | -0.05 |
| 2014 | 243 | -2 | -0.09 |
| 2015 | 250 | 4 | 0.19 |
| 2016 | 250 | -2 | -0.13 |
| 2017 | 249 | 42 | 2.11 |
| 2018 | 248 | -2 | -0.09 |
| 2019 | 249 | 32 | 1.88 |
| 2020 | 251 | 14 | 0.80 |
| 2021 | 250 | 8 | 0.43 |
| 2022 | 250 | -16 | -0.98 |
| 2023 | 248 | 28 | 1.94 |
| 2024 | 249 | 11 | 0.50 |
| 2025 | 247 | -7 | -0.37 |
| 2026 | 196 | -1 | -0.10 |

## Forecast skill of the pre-open score against the realised RTH range / ADR20 (Spearman rho, AUC for the top third)

| score | 2013-22 rho / AUC (n) | 2023-26 rho / AUC (n) |
|---|---|---|
| full (overnight, prior-day, VIX) | +0.40 / 0.71 (2304) | +0.37 / 0.66 (826) |
| early (prior-day, VIX) | +0.30 / 0.67 (2304) | +0.23 / 0.60 (826) |
| full + macro overnight leg (RZ10) | +0.43 / 0.73 (2304) | +0.40 / 0.68 (826) |
| early + macro (same as early) | +0.30 / 0.67 (2304) | +0.23 / 0.60 (826) |

## Control: same cell without the forecast filter (same scaling factor): 20% additive uplift clean/H1/H2/all -0.047/+0.056/-0.070/-0.042; selected cell -0.047/+0.056/-0.070/-0.042; trades 3419 vs 3419.

DONE RZ3