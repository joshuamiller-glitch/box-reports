# REPORT J10
**Verdict: NO** (2/7 measured gates pass). Selected cell sig=resid, thr=0.0, mode=follow, ex=90; additive @20% clean/H1/H2 +0.05/+0.08/-0.23; standalone all-in weekly Sharpe 0.19 (2013-26 -1.05, dev 2013-22 -1.50); pair-window trades 827. Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

J10 NKD overnight lead for NQ Globex (36 cells): Tokyo-session NKD return (raw or minus NQ) at 06:15 UTC, trade NQ from 06:20 UTC, follow or fade, exits +90/+240 min or 09:25 ET.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 36 cells, eligible (>= 60 clean trades): 36. Top cells by clean weekly Sharpe:

| sig   |   thr | mode   |   ex |   n |   sharpe |   net |   ypos | eligible   |
|:------|------:|:-------|-----:|----:|---------:|------:|-------:|:-----------|
| resid | 0.000 | follow |   90 | 517 |    0.494 | 2.005 |      3 | True       |
| raw   | 1.000 | follow |  925 | 141 |    0.414 | 2.368 |      2 | True       |
| resid | 0.000 | fade   |  925 | 517 |    0.306 | 3.051 |      2 | True       |
| raw   | 0.500 | follow |   90 | 300 |    0.290 | 0.875 |      2 | True       |
| raw   | 1.000 | follow |   90 | 141 |    0.232 | 0.510 |      2 | True       |
| raw   | 1.000 | follow |  240 | 141 |    0.209 | 0.723 |      2 | True       |
| resid | 0.500 | follow |   90 | 293 |    0.206 | 0.650 |      2 | True       |
| raw   | 0.500 | follow |  925 | 300 |    0.137 | 0.929 |      1 | True       |
| resid | 1.000 | fade   |   90 | 140 |    0.126 | 0.293 |      1 | True       |
| resid | 1.000 | follow |  925 | 140 |    0.090 | 0.516 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.49; replicate best-eligible median 0.99, p95 1.34; real beats 0% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.245e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.033 | +0.062 | -0.102 | +0.012 | +1.8 | [-0.090, +0.110] | 0.54 | NO |
| 20% | add | +0.052 | +0.085 | -0.232 | +0.004 | +19.3 | [-0.198, +0.200] | 0.54 | NO |
| 30% | add | +0.056 | +0.077 | -0.388 | -0.021 | +47.4 | [-0.320, +0.269] | 0.54 | NO |
| 50% | add | +0.032 | +0.002 | -0.755 | -0.113 | +103.5 | [-0.583, +0.355] | 0.54 | NO |
| 10% | const | +0.036 | +0.066 | -0.115 | +0.012 | -7.6 | [-0.101, +0.121] | 0.54 | NO |
| 20% | const | +0.056 | +0.084 | -0.307 | -0.006 | +6.7 | [-0.257, +0.237] | 0.54 | NO |
| 30% | const | +0.045 | +0.035 | -0.618 | -0.075 | +28.4 | [-0.487, +0.331] | 0.54 | NO |
| 50% | const | -0.117 | -0.282 | -1.673 | -0.424 | +71.9 | [-1.183, +0.357] | 0.54 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 450,210, Sharpe 0.49, maxDD 493,299, worst wk -231,620; H1: net 340,544, Sharpe 1.32, maxDD 219,935, worst wk -129,674; H2: net -506,642, Sharpe -1.46, maxDD 653,121, worst wk -214,572; all: net 284,112, Sharpe 0.19, maxDD 852,525, worst wk -231,620
Correlation with pair (weekly): clean +0.06, H1 +0.23, H2 -0.27, all -0.01; worst-decile weeks (n=17) corr -0.20, sleeve mean in those weeks $14,625, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.51 | 2.95 | 4.49 | -87,314 | -81,309 | 316,298 | -98,489 | 44.8 |
| clean | add 30% | 1.52 | 2.97 | 4.38 | -93,997 | -84,261 | 334,392 | -121,651 | 43.8 |
| clean | const 20% | 1.52 | 2.96 | 4.43 | -72,524 | -66,228 | 260,276 | -88,056 | 44.8 |
| clean | const 30% | 1.50 | 2.93 | 4.26 | -71,813 | -61,856 | 250,359 | -106,001 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.91 | 6.68 | 4.28 | -72,291 | -65,304 | 154,596 | -81,954 | 42.9 |
| H1 | add 30% | 2.90 | 6.71 | 4.46 | -69,674 | -64,942 | 156,037 | -83,787 | 39.3 |
| H1 | const 20% | 2.91 | 6.71 | 4.37 | -56,769 | -52,098 | 124,253 | -66,296 | 39.3 |
| H1 | const 30% | 2.86 | 6.61 | 4.69 | -51,501 | -45,861 | 110,523 | -60,301 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.06 | 4.15 | 2.87 | -83,908 | -74,863 | 230,291 | -89,064 | 47.2 |
| H2 | add 30% | 1.91 | 3.74 | 2.57 | -85,877 | -78,395 | 236,723 | -94,888 | 47.2 |
| H2 | const 20% | 1.99 | 3.96 | 2.72 | -67,914 | -59,992 | 186,806 | -73,581 | 47.2 |
| H2 | const 30% | 1.68 | 3.14 | 2.22 | -71,067 | -61,004 | 171,496 | -71,664 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.86 | 3.71 | 8.67 | -85,961 | -79,202 | 316,298 | -98,489 | 44.6 |
| all | add 30% | 1.83 | 3.65 | 8.28 | -91,058 | -81,677 | 334,392 | -121,651 | 43.5 |
| all | const 20% | 1.85 | 3.69 | 8.47 | -70,808 | -63,999 | 260,276 | -88,056 | 44.0 |
| all | const 30% | 1.78 | 3.51 | 7.85 | -70,368 | -60,579 | 250,359 | -106,001 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.052 / +0.085 / -0.232
- [PASS] 3 worst week within share: all-in worst week +19.3% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.19 vs p95 0.19 (rank 0.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.198, +0.200]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.010 / +0.047 / -0.256
- [PASS] 6 worst-decile corr <=+0.30: -0.20
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section J10); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (827 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2511 | -0.0036 | -0.42 |
| fixed | 2511 | -0.0130 | -1.50 |
| scaled | 2511 | -0.0062 | -0.71 |

Plateau neighbours (all-in 20% uplift; selected +0.004):
- {'sig': 'resid', 'thr': '0.0', 'mode': 'follow', 'ex': '68'}: -0.070 (trades 827)
- {'sig': 'resid', 'thr': '0.0', 'mode': 'follow', 'ex': '112'}: +0.055 (trades 827)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.19, p95 0.19, real 0.19. Standalone Sharpe at 2x slippage 0.00.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 212 | -1 | -0.67 |
| 2014 | 245 | -4 | -2.88 |
| 2015 | 253 | -3 | -0.96 |
| 2016 | 257 | -4 | -1.69 |
| 2017 | 255 | -7 | -3.86 |
| 2018 | 258 | -3 | -1.60 |
| 2019 | 258 | -4 | -1.76 |
| 2020 | 256 | -3 | -1.12 |
| 2021 | 259 | -1 | -0.68 |
| 2022 | 258 | -2 | -0.98 |
| 2023 | 258 | 1 | 0.79 |
| 2024 | 259 | 1 | 0.29 |
| 2025 | 257 | 2 | 1.10 |
| 2026 | 203 | -3 | -1.55 |


DONE J10