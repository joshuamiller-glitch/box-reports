# REPORT RX1
**Verdict: LEAD** (5/7 measured gates pass). Selected cell state=k4lo, act=half; additive @20% clean/H1/H2 +0.20/+1.10/+0.21; standalone all-in weekly Sharpe 1.84 (2013-26 0.72, dev 2013-22 0.24); pair-window trades 200. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RX1 I9 tail fix: gross-exposure cap (half size or at most one open position) when a market state is on (VIX/VIX3M inversion, VIX 252d percentile >= 0.8, K4 mean probability < 0.5), states taken from the previous label (6 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 6 cells, eligible (>= 100 clean trades): 6. Top cells by clean weekly Sharpe:

| state   | act   |   n |   sharpe |    net |   ypos | eligible   |
|:--------|:------|----:|---------:|-------:|-------:|:-----------|
| k4lo    | half  | 120 |    1.414 | 28.100 |      2 | True       |
| k4lo    | max1  | 112 |    1.389 | 27.266 |      2 | True       |
| inv     | max1  | 120 |    1.293 | 28.061 |      3 | True       |
| vixhi   | half  | 120 |    1.291 | 26.839 |      3 | True       |
| vixhi   | max1  | 113 |    1.286 | 26.865 |      3 | True       |
| inv     | half  | 120 |    1.265 | 27.398 |      3 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.41; replicate best-eligible median 1.06, p95 1.51; real beats 87% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.563e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.110 | +0.593 | +0.116 | +0.176 | +16.1 | [+0.070, +0.294] | 0.23 | NO |
| 20% | add | +0.201 | +1.098 | +0.207 | +0.324 | +43.7 | [+0.117, +0.551] | 0.23 | NO |
| 30% | add | +0.273 | +1.493 | +0.274 | +0.443 | +71.4 | [+0.141, +0.761] | 0.23 | NO |
| 50% | add | +0.369 | +1.978 | +0.333 | +0.598 | +126.7 | [+0.144, +1.068] | 0.23 | NO |
| 10% | const | +0.121 | +0.654 | +0.127 | +0.194 | +7.2 | [+0.076, +0.324] | 0.23 | NO |
| 20% | const | +0.239 | +1.310 | +0.244 | +0.387 | +26.0 | [+0.133, +0.660] | 0.23 | NO |
| 30% | const | +0.342 | +1.847 | +0.322 | +0.554 | +44.9 | [+0.150, +0.975] | 0.23 | NO |
| 50% | const | +0.432 | +2.212 | +0.210 | +0.687 | +82.5 | [-0.001, +1.397] | 0.23 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,282,215, Sharpe 1.41, maxDD 404,153, worst wk -228,260; H1: net 1,260,603, Sharpe 4.00, maxDD 95,058, worst wk -95,058; H2: net 358,568, Sharpe 1.09, maxDD 175,834, worst wk -89,863; all: net 2,901,386, Sharpe 1.84, maxDD 404,153, worst wk -228,260
Correlation with pair (weekly): clean +0.15, H1 -0.06, H2 -0.08, all +0.06; worst-decile weeks (n=17) corr +0.27, sleeve mean in those weeks $-6,619, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.66 | 3.13 | 5.46 | -92,255 | -84,907 | 290,439 | -118,603 | 40.0 |
| clean | add 30% | 1.73 | 3.24 | 5.31 | -102,404 | -90,515 | 322,737 | -141,429 | 40.0 |
| clean | const 20% | 1.70 | 3.19 | 5.39 | -77,691 | -70,169 | 245,103 | -104,013 | 40.0 |
| clean | const 30% | 1.80 | 3.32 | 5.15 | -81,203 | -68,408 | 255,362 | -119,544 | 41.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.93 | 9.32 | 6.13 | -77,610 | -65,553 | 138,108 | -78,287 | 35.7 |
| H1 | add 30% | 4.32 | 10.77 | 7.03 | -77,610 | -65,315 | 138,346 | -78,287 | 32.1 |
| H1 | const 20% | 4.14 | 10.06 | 6.58 | -62,088 | -52,347 | 110,582 | -62,630 | 35.7 |
| H1 | const 30% | 4.67 | 12.43 | 8.18 | -54,327 | -45,506 | 97,056 | -54,801 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.50 | 5.20 | 3.61 | -85,263 | -81,796 | 230,882 | -90,872 | 44.4 |
| H2 | add 30% | 2.57 | 5.32 | 3.65 | -88,627 | -83,101 | 237,935 | -97,600 | 38.9 |
| H2 | const 20% | 2.54 | 5.27 | 3.63 | -69,556 | -65,959 | 187,397 | -75,389 | 38.9 |
| H2 | const 30% | 2.62 | 5.42 | 3.63 | -65,067 | -59,346 | 176,258 | -74,376 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.18 | 4.29 | 11.24 | -89,394 | -83,317 | 290,439 | -118,603 | 39.9 |
| all | add 30% | 2.30 | 4.52 | 11.02 | -96,722 | -87,252 | 322,737 | -141,429 | 38.1 |
| all | const 20% | 2.24 | 4.41 | 11.13 | -74,321 | -68,228 | 245,103 | -104,013 | 38.7 |
| all | const 30% | 2.41 | 4.73 | 10.77 | -74,684 | -64,619 | 255,362 | -119,544 | 38.1 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.201 / +1.098 / +0.207
- [FAIL] 3 worst week within share: all-in worst week +43.7% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.84 vs p95 1.11 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.117, +0.551]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.195 / +1.092 / +0.203
- [PASS] 6 worst-decile corr <=+0.30: +0.27
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RX1); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (200 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 419 | +0.0745 | 0.29 |
| fixed | 419 | +0.0612 | 0.24 |
| scaled | 419 | +0.0682 | 0.26 |

Plateau neighbours (all-in 20% uplift; selected +0.324):

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.34, p95 1.11, real 1.84. Standalone Sharpe at 2x slippage 1.82.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 6 | 2 | 1.38 |
| 2014 | 50 | 11 | 0.72 |
| 2015 | 55 | -8 | -0.62 |
| 2016 | 30 | -6 | -0.43 |
| 2017 | 42 | 19 | 2.35 |
| 2018 | 43 | -11 | -0.87 |
| 2019 | 47 | 7 | 0.98 |
| 2020 | 52 | 11 | 1.01 |
| 2021 | 80 | 4 | 0.31 |
| 2022 | 14 | -4 | -0.62 |
| 2023 | 71 | 18 | 1.51 |
| 2024 | 70 | 25 | 2.50 |
| 2025 | 52 | 24 | 2.38 |
| 2026 | 46 | 15 | 1.75 |


DONE RX1