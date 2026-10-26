# REPORT L10
**Verdict: NO** (2/7 measured gates pass). Selected cell model=d2, N=3, delta=0.08, mode=longshort; additive @20% clean/H1/H2 -0.04/+0.14/-0.05; standalone all-in weekly Sharpe 0.27 (2013-26 -0.22, dev 2013-22 -0.34); pair-window trades 396. Runtime 0.1 min (+selection 0.0 min). 6-worker pool.

L10 daily walk-forward GBM on ZT/ZF/ZN/ZB (16 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 100 clean trades): 14. Top cells by clean weekly Sharpe:

| model   |   N |   delta | mode      |    n |   sharpe |     net |   ypos | eligible   |
|:--------|----:|--------:|:----------|-----:|---------:|--------:|-------:|:-----------|
| d2      |   3 |   0.080 | longshort |  282 |    0.098 |   4.659 |      2 | True       |
| d2      |   1 |   0.080 | longshort |  331 |   -0.011 |  -0.300 |      2 | True       |
| d4      |   1 |   0.040 | longonly  |  337 |   -0.012 |  -0.385 |      1 | True       |
| d4      |   1 |   0.080 | longshort |  666 |   -0.013 |  -0.505 |      2 | True       |
| d2      |   1 |   0.040 | longshort |  887 |   -0.232 | -10.995 |      1 | True       |
| d4      |   1 |   0.040 | longshort | 1214 |   -0.235 | -12.472 |      2 | True       |
| d2      |   3 |   0.040 | longshort |  530 |   -0.288 | -19.577 |      0 | True       |
| d4      |   1 |   0.080 | longonly  |  142 |   -0.393 |  -8.274 |      1 | True       |
| d4      |   3 |   0.040 | longshort |  591 |   -0.397 | -27.581 |      0 | True       |
| d4      |   3 |   0.080 | longshort |  442 |   -0.419 | -23.568 |      0 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.10; replicate best-eligible median 0.36, p95 0.80; real beats 20% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.907e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.011 | +0.075 | -0.020 | -0.004 | +6.5 | [-0.082, +0.070] | 0.05 | NO |
| 20% | add | -0.035 | +0.144 | -0.050 | -0.022 | +16.2 | [-0.176, +0.123] | 0.05 | NO |
| 30% | add | -0.070 | +0.208 | -0.088 | -0.051 | +25.8 | [-0.279, +0.162] | 0.05 | NO |
| 50% | add | -0.159 | +0.315 | -0.180 | -0.135 | +45.2 | [-0.503, +0.203] | 0.05 | NO |
| 10% | const | -0.013 | +0.083 | -0.022 | -0.006 | -3.2 | [-0.092, +0.077] | 0.05 | NO |
| 20% | const | -0.051 | +0.177 | -0.068 | -0.035 | -3.2 | [-0.228, +0.144] | 0.05 | NO |
| 30% | const | -0.125 | +0.280 | -0.145 | -0.102 | -3.2 | [-0.422, +0.193] | 0.05 | NO |
| 50% | const | -0.408 | +0.450 | -0.428 | -0.391 | -3.2 | [-1.015, +0.196] | 0.05 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 87,297, Sharpe 0.10, maxDD 663,837, worst wk -222,330; H1: net 101,756, Sharpe 1.02, maxDD 135,356, worst wk -49,402; H2: net 160,794, Sharpe 0.59, maxDD 209,288, worst wk -105,602; all: net 349,848, Sharpe 0.27, maxDD 663,837, worst wk -222,330
Correlation with pair (weekly): clean +0.09, H1 -0.21, H2 +0.33, all +0.12; worst-decile weeks (n=17) corr +0.14, sleeve mean in those weeks $-1,100, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.42 | 2.71 | 4.70 | -84,883 | -80,594 | 286,884 | -95,858 | 45.7 |
| clean | add 30% | 1.39 | 2.65 | 4.67 | -88,218 | -83,023 | 290,270 | -103,852 | 45.7 |
| clean | const 20% | 1.41 | 2.68 | 4.68 | -69,194 | -65,395 | 230,862 | -79,884 | 45.7 |
| clean | const 30% | 1.33 | 2.53 | 4.48 | -66,290 | -61,575 | 213,792 | -79,892 | 45.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.97 | 6.21 | 4.28 | -81,805 | -68,621 | 143,350 | -88,168 | 39.3 |
| H1 | add 30% | 3.04 | 6.23 | 4.47 | -83,902 | -69,916 | 139,677 | -93,108 | 35.7 |
| H1 | const 20% | 3.00 | 6.23 | 4.38 | -66,283 | -55,415 | 113,008 | -72,510 | 35.7 |
| H1 | const 30% | 3.11 | 6.21 | 4.53 | -60,619 | -50,107 | 98,387 | -69,622 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.25 | 4.83 | 3.82 | -79,908 | -77,669 | 207,833 | -80,247 | 44.4 |
| H2 | add 30% | 2.21 | 4.87 | 3.99 | -79,317 | -76,912 | 203,037 | -79,526 | 41.7 |
| H2 | const 20% | 2.23 | 4.86 | 3.90 | -63,690 | -61,832 | 164,348 | -63,742 | 44.4 |
| H2 | const 30% | 2.15 | 4.89 | 4.02 | -54,991 | -53,156 | 144,708 | -55,630 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.83 | 3.62 | 9.60 | -84,142 | -80,048 | 286,884 | -95,858 | 44.6 |
| all | add 30% | 1.80 | 3.57 | 9.61 | -87,090 | -81,688 | 290,270 | -103,852 | 43.5 |
| all | const 20% | 1.82 | 3.60 | 9.61 | -68,339 | -64,661 | 230,862 | -79,884 | 44.0 |
| all | const 30% | 1.75 | 3.48 | 9.28 | -64,526 | -59,521 | 213,792 | -79,892 | 43.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.035 / +0.144 / -0.050
- [PASS] 3 worst week within share: all-in worst week +16.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.27 vs p95 0.52 (rank 0.86)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.176, +0.123]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.088 / +0.088 / -0.094
- [PASS] 6 worst-decile corr <=+0.30: +0.14
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section L10); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (396 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1271 | +0.0306 | 0.19 |
| fixed | 1271 | -0.0539 | -0.34 |
| scaled | 1271 | -0.0247 | -0.16 |

Plateau neighbours (all-in 20% uplift; selected -0.022):
- {'model': 'd2', 'N': '3', 'delta': '0.06', 'mode': 'longshort'}: -0.039 (trades 583)
- {'model': 'd2', 'N': '3', 'delta': '0.1', 'mode': 'longshort'}: +0.013 (trades 260)
- {'model': 'd2', 'N': '2', 'delta': '0.08', 'mode': 'longshort'}: +0.040 (trades 499)
- {'model': 'd2', 'N': '4', 'delta': '0.08', 'mode': 'longshort'}: -0.026 (trades 311)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.22, p95 0.52, real 0.27. Standalone Sharpe at 2x slippage -0.03.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 256 | -23 | -0.65 |
| 2017 | 204 | 14 | 0.44 |
| 2018 | 171 | -42 | -1.41 |
| 2019 | 191 | 32 | 1.11 |
| 2020 | 175 | -46 | -1.38 |
| 2021 | 178 | -24 | -1.03 |
| 2022 | 96 | 19 | 1.39 |
| 2023 | 145 | -7 | -0.33 |
| 2024 | 121 | 4 | 0.16 |
| 2025 | 116 | 2 | 0.10 |
| 2026 | 79 | 7 | 0.45 |


## Beta / drift test (report): regression of the sleeve's daily P&L on the always-long basket of the same instruments (unit risk), 2023-08..2026-10: beta -0.333; sleeve weekly Sharpe 0.27; always-long basket -0.58; ALPHA weekly Sharpe -0.14, bootstrap 90% CI [-1.04, +0.79] (alpha CI includes zero).

DONE L10