# REPORT K3
**Verdict: NO** (3/7 measured gates pass). Selected cell ev=FOMC, mode=follow, H=60; additive @20% clean/H1/H2 +0.11/-0.22/+0.10; standalone all-in weekly Sharpe 0.67 (2013-26 0.07, dev 2013-22 -0.05); pair-window trades 145. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

K3 post-release drift on GC, ZN, 6E, CL, RTY, YM after FOMC, NFP and CPI (12 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 12 cells, eligible (>= 20 clean trades): 12. Top cells by clean weekly Sharpe:

| ev   | mode   |   H |   n |   sharpe |     net |   ypos | eligible   |
|:-----|:-------|----:|----:|---------:|--------:|-------:|:-----------|
| FOMC | follow |  60 |  94 |    0.858 |  10.346 |      3 | True       |
| NFP  | fade   |  60 | 144 |    0.818 |   6.243 |      3 | True       |
| CPI  | follow |  30 | 143 |    0.442 |   2.433 |      2 | True       |
| NFP  | fade   |  30 | 144 |    0.245 |   1.527 |      2 | True       |
| CPI  | follow |  60 | 143 |    0.025 |   0.189 |      2 | True       |
| FOMC | follow |  30 |  94 |    0.005 |   0.030 |      1 | True       |
| FOMC | fade   |  30 |  94 |   -0.593 |  -3.564 |      0 | True       |
| CPI  | fade   |  60 | 143 |   -0.710 |  -5.525 |      1 | True       |
| NFP  | follow |  30 | 144 |   -1.064 |  -6.887 |      0 | True       |
| FOMC | fade   |  60 |  94 |   -1.117 | -13.879 |      0 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.86; replicate best-eligible median 0.38, p95 1.04; real beats 83% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=7.298e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.062 | -0.091 | +0.057 | +0.040 | -0.8 | [-0.033, +0.112] | 0.11 | NO |
| 20% | add | +0.108 | -0.222 | +0.099 | +0.062 | -0.8 | [-0.085, +0.198] | 0.11 | NO |
| 30% | add | +0.138 | -0.378 | +0.127 | +0.066 | -0.8 | [-0.154, +0.264] | 0.11 | NO |
| 50% | add | +0.160 | -0.714 | +0.147 | +0.034 | +39.7 | [-0.320, +0.345] | 0.11 | NO |
| 10% | const | +0.068 | -0.104 | +0.062 | +0.043 | -10.7 | [-0.038, +0.122] | 0.11 | NO |
| 20% | const | +0.125 | -0.297 | +0.115 | +0.066 | -20.6 | [-0.119, +0.234] | 0.11 | NO |
| 30% | const | +0.158 | -0.594 | +0.145 | +0.051 | -20.6 | [-0.259, +0.322] | 0.11 | NO |
| 50% | const | +0.091 | -1.416 | +0.062 | -0.149 | +61.5 | [-0.769, +0.391] | 0.11 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 755,041, Sharpe 0.83, maxDD 418,172, worst wk -161,918; H1: net -76,799, Sharpe -0.27, maxDD 302,494, worst wk -302,494; H2: net 289,371, Sharpe 1.12, maxDD 125,642, worst wk -125,642; all: net 967,612, Sharpe 0.67, maxDD 418,172, worst wk -302,494
Correlation with pair (weekly): clean +0.09, H1 +0.08, H2 +0.13, all +0.09; worst-decile weeks (n=17) corr -0.14, sleeve mean in those weeks $11,422, positive share 0.18.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.57 | 3.14 | 5.54 | -78,727 | -77,987 | 267,258 | -81,874 | 41.0 |
| clean | add 30% | 1.60 | 3.31 | 5.97 | -78,727 | -77,990 | 260,832 | -81,874 | 41.9 |
| clean | const 20% | 1.58 | 3.22 | 5.75 | -62,981 | -62,391 | 211,236 | -65,499 | 41.0 |
| clean | const 30% | 1.62 | 3.52 | 6.35 | -55,109 | -54,596 | 182,210 | -57,312 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.61 | 5.74 | 3.79 | -77,610 | -66,030 | 152,742 | -78,287 | 42.9 |
| H1 | add 30% | 2.45 | 5.28 | 3.56 | -77,610 | -69,991 | 160,297 | -78,287 | 42.9 |
| H1 | const 20% | 2.53 | 5.53 | 3.67 | -62,088 | -52,824 | 125,216 | -62,630 | 42.9 |
| H1 | const 30% | 2.23 | 4.55 | 3.08 | -60,177 | -58,069 | 127,412 | -65,552 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.39 | 5.19 | 3.77 | -78,535 | -75,719 | 217,425 | -79,653 | 44.4 |
| H2 | add 30% | 2.42 | 5.45 | 3.90 | -78,535 | -73,985 | 217,425 | -79,653 | 44.4 |
| H2 | const 20% | 2.41 | 5.32 | 3.83 | -62,828 | -59,882 | 173,940 | -63,723 | 44.4 |
| H2 | const 30% | 2.44 | 5.78 | 4.07 | -54,974 | -50,821 | 152,198 | -55,757 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.92 | 3.94 | 10.77 | -78,635 | -77,786 | 267,258 | -81,874 | 42.3 |
| all | add 30% | 1.92 | 4.06 | 11.41 | -78,635 | -77,733 | 260,832 | -81,874 | 42.9 |
| all | const 20% | 1.92 | 4.00 | 11.08 | -62,908 | -62,208 | 211,236 | -65,499 | 42.3 |
| all | const 30% | 1.91 | 4.17 | 11.91 | -56,319 | -55,210 | 182,210 | -65,552 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.108 / -0.222 / +0.099
- [PASS] 3 worst week within share: all-in worst week -0.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.67 vs p95 0.26 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.085, +0.198]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.087 / -0.243 / +0.079
- [PASS] 6 worst-decile corr <=+0.30: -0.14
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K3); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (145 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 426 | +0.0188 | 0.18 |
| fixed | 426 | -0.0050 | -0.05 |
| scaled | 426 | -0.0004 | -0.00 |

Plateau neighbours (all-in 20% uplift; selected +0.062):
- {'ev': 'FOMC', 'mode': 'follow', 'H': '45'}: -0.028 (trades 145)
- {'ev': 'FOMC', 'mode': 'follow', 'H': '75'}: +0.067 (trades 145)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.70, p95 0.26, real 0.67. Standalone Sharpe at 2x slippage 0.56.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 38 | 4 | 1.18 |
| 2014 | 40 | -3 | -0.94 |
| 2015 | 40 | 6 | 1.50 |
| 2016 | 40 | -1 | -0.29 |
| 2017 | 42 | 6 | 1.99 |
| 2018 | 44 | -0 | -0.05 |
| 2019 | 46 | 2 | 0.42 |
| 2020 | 41 | -6 | -1.94 |
| 2021 | 47 | -2 | -0.40 |
| 2022 | 48 | -8 | -1.33 |
| 2023 | 47 | -1 | -0.19 |
| 2024 | 48 | 5 | 0.75 |
| 2025 | 45 | 0 | 0.07 |
| 2026 | 34 | 3 | 0.82 |


DONE K3