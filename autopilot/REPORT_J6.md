# REPORT J6
**Verdict: NO** (3/7 measured gates pass). Selected cell thr=0.25, mode=fade, H=384; additive @20% clean/H1/H2 +0.09/-0.34/-0.03; standalone all-in weekly Sharpe 0.33 (2013-26 -0.05, dev 2013-22 -0.08); pair-window trades 60 (SMALL-SAMPLE). Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

J6 mega-cap earnings-morning RTH gap sleeve on NQ (EDGAR 8-K 2.02 after-close releases): follow or fade the 09:30 gap, entry 09:31, time exit (18 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 18 cells, eligible (>= 20 clean trades): 18. Top cells by clean weekly Sharpe:

|   thr | mode   |   H |   n |   sharpe |    net |   ypos | eligible   |
|------:|:-------|----:|----:|---------:|-------:|-------:|:-----------|
| 0.250 | fade   | 384 |  40 |    0.589 |  3.906 |      2 | True       |
| 0.100 | follow | 150 |  55 |    0.531 |  2.957 |      1 | True       |
| 0.000 | fade   | 384 |  62 |    0.484 |  3.876 |      2 | True       |
| 0.000 | follow | 150 |  62 |    0.397 |  2.448 |      1 | True       |
| 0.250 | fade   |  60 |  40 |    0.323 |  1.138 |      2 | True       |
| 0.000 | follow |  60 |  62 |    0.314 |  1.422 |      1 | True       |
| 0.100 | fade   | 384 |  55 |    0.166 |  1.278 |      2 | True       |
| 0.100 | follow |  60 |  55 |    0.091 |  0.385 |      1 | True       |
| 0.250 | fade   | 150 |  40 |    0.086 |  0.387 |      2 | True       |
| 0.250 | follow | 150 |  40 |   -0.129 | -0.577 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.59; replicate best-eligible median 1.29, p95 1.61; real beats 0% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.375e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.054 | -0.162 | -0.015 | +0.016 | +0.0 | [-0.065, +0.096] | 0.28 | NO |
| 20% | add | +0.093 | -0.344 | -0.034 | +0.017 | +6.3 | [-0.144, +0.173] | 0.28 | NO |
| 30% | add | +0.116 | -0.530 | -0.055 | +0.004 | +12.7 | [-0.232, +0.230] | 0.28 | NO |
| 50% | add | +0.122 | -0.881 | -0.105 | -0.055 | +43.9 | [-0.434, +0.294] | 0.28 | NO |
| 10% | const | +0.059 | -0.182 | -0.017 | +0.017 | -9.5 | [-0.073, +0.105] | 0.28 | NO |
| 20% | const | +0.106 | -0.437 | -0.044 | +0.012 | -12.4 | [-0.187, +0.204] | 0.28 | NO |
| 30% | const | +0.125 | -0.761 | -0.086 | -0.030 | -13.4 | [-0.364, +0.278] | 0.28 | NO |
| 50% | const | +0.003 | -1.521 | -0.263 | -0.292 | +42.5 | [-0.937, +0.304] | 0.28 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 536,931, Sharpe 0.59, maxDD 576,540, worst wk -232,774; H1: net -62,503, Sharpe -0.21, maxDD 358,584, worst wk -163,492; H2: net -30,021, Sharpe -0.25, maxDD 119,970, worst wk -58,220; all: net 444,407, Sharpe 0.33, maxDD 576,540, worst wk -232,774
Correlation with pair (weekly): clean -0.02, H1 +0.30, H2 +0.06, all +0.04; worst-decile weeks (n=17) corr -0.16, sleeve mean in those weeks $-3,105, positive share 0.00.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.55 | 2.97 | 6.61 | -78,736 | -78,009 | 217,585 | -81,874 | 41.9 |
| clean | add 30% | 1.58 | 3.03 | 6.74 | -78,736 | -78,009 | 221,181 | -81,874 | 41.0 |
| clean | const 20% | 1.57 | 3.00 | 6.67 | -62,988 | -62,407 | 175,507 | -65,499 | 41.0 |
| clean | const 30% | 1.59 | 3.05 | 6.91 | -58,207 | -56,342 | 158,063 | -71,496 | 40.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.48 | 5.44 | 3.35 | -77,610 | -71,434 | 173,437 | -78,287 | 42.9 |
| H1 | add 30% | 2.30 | 5.03 | 2.90 | -77,610 | -76,884 | 198,377 | -78,287 | 46.4 |
| H1 | const 20% | 2.39 | 5.24 | 3.11 | -62,088 | -59,327 | 148,725 | -62,630 | 46.4 |
| H1 | const 30% | 2.07 | 4.48 | 2.46 | -61,159 | -58,723 | 161,310 | -67,517 | 46.4 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.26 | 4.53 | 3.38 | -85,115 | -81,825 | 223,371 | -87,705 | 44.4 |
| H2 | add 30% | 2.24 | 4.45 | 3.32 | -87,754 | -83,144 | 226,344 | -92,984 | 44.4 |
| H2 | const 20% | 2.25 | 4.49 | 3.35 | -69,148 | -65,988 | 179,886 | -72,275 | 44.4 |
| H2 | const 30% | 2.21 | 4.33 | 3.25 | -63,803 | -59,389 | 161,116 | -69,840 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.87 | 3.67 | 12.42 | -80,364 | -78,864 | 223,371 | -87,705 | 42.3 |
| all | add 30% | 1.86 | 3.64 | 11.71 | -80,950 | -79,175 | 240,710 | -92,984 | 42.3 |
| all | const 20% | 1.87 | 3.66 | 12.25 | -64,525 | -63,216 | 182,592 | -72,275 | 42.3 |
| all | const 30% | 1.83 | 3.56 | 10.54 | -60,651 | -57,625 | 190,943 | -71,496 | 41.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.093 / -0.344 / -0.034
- [PASS] 3 worst week within share: all-in worst week +6.3% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.33 vs p95 0.80 (rank 0.75)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.144, +0.173]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 75% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.091 / -0.345 / -0.035
- [PASS] 6 worst-decile corr <=+0.30: -0.16
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section J6); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (60 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 166 | -0.0030 | -0.02 |
| fixed | 166 | -0.0123 | -0.08 |
| scaled | 166 | -0.0055 | -0.04 |

Plateau neighbours (all-in 20% uplift; selected +0.017):
- {'thr': '0.19', 'mode': 'fade', 'H': '384'}: +0.010 (trades 65)
- {'thr': '0.31', 'mode': 'fade', 'H': '384'}: +0.057 (trades 53)
- {'thr': '0.25', 'mode': 'fade', 'H': '288'}: +0.039 (trades 60)
- {'thr': '0.25', 'mode': 'fade', 'H': '480'}: +0.017 (trades 60)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.01, p95 0.80, real 0.33. Standalone Sharpe at 2x slippage 0.33.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 17 | -0 | -0.30 |
| 2014 | 15 | -2 | -0.88 |
| 2015 | 12 | 0 | 0.17 |
| 2016 | 14 | 2 | 1.58 |
| 2017 | 14 | -0 | -0.01 |
| 2018 | 23 | 1 | 0.23 |
| 2019 | 25 | 1 | 0.50 |
| 2020 | 14 | -1 | -0.34 |
| 2021 | 17 | -1 | -0.50 |
| 2022 | 15 | -1 | -0.45 |
| 2023 | 23 | -0 | -0.01 |
| 2024 | 21 | -4 | -1.26 |
| 2025 | 18 | 6 | 1.87 |
| 2026 | 14 | -2 | -1.56 |


DONE J6