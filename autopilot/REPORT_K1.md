# REPORT K1
**Verdict: NO** (1/7 measured gates pass). Selected cell lead=ZN, w=30, thr=0.3, mode=follow; additive @20% clean/H1/H2 +0.22/-0.42/+0.08; standalone all-in weekly Sharpe 0.91 (2013-26 0.23, dev 2013-22 0.17); pair-window trades 2588. Runtime 0.4 min (+selection 0.1 min). 6-worker pool.

K1 cross-asset 60-minute lead sleeve: leader (ZN, 6J, GC, CL, 6E) move over w minutes in ADR units; trade NQ/ES/RTY/YM follow or inverse for 60 minutes (60 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 60 cells, eligible (>= 100 clean trades): 60. Top cells by clean weekly Sharpe:

| lead   |   w |   thr | mode    |    n |   sharpe |    net |   ypos | eligible   |
|:-------|----:|------:|:--------|-----:|---------:|-------:|-------:|:-----------|
| ZN     |  30 | 0.300 | follow  | 1552 |    1.457 | 51.343 |      3 | True       |
| 6E     |  30 | 0.300 | follow  | 1400 |    0.639 | 21.235 |      3 | True       |
| CL     |  30 | 0.300 | inverse | 2284 |    0.296 |  8.487 |      2 | True       |
| ZN     |  60 | 0.300 | follow  | 2704 |    0.074 |  2.811 |      2 | True       |
| 6J     |  30 | 0.300 | follow  | 1028 |   -0.026 | -0.749 |      1 | True       |
| 6J     |  30 | 0.150 | inverse | 4180 |   -0.033 | -1.641 |      1 | True       |
| 6J     | 120 | 0.150 | inverse | 7356 |   -0.036 | -2.165 |      2 | True       |
| GC     |  60 | 0.300 | inverse | 2760 |   -0.049 | -1.881 |      2 | True       |
| 6J     | 120 | 0.300 | inverse | 3144 |   -0.098 | -3.818 |      1 | True       |
| GC     |  30 | 0.150 | inverse | 5572 |   -0.117 | -5.282 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.46; replicate best-eligible median 0.54, p95 1.11; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.585e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.120 | -0.200 | +0.047 | +0.056 | +11.5 | [-0.016, +0.131] | 0.04 | NO |
| 20% | add | +0.220 | -0.419 | +0.084 | +0.096 | +23.8 | [-0.046, +0.240] | 0.04 | NO |
| 30% | add | +0.302 | -0.650 | +0.112 | +0.119 | +36.1 | [-0.089, +0.329] | 0.04 | NO |
| 50% | add | +0.412 | -1.121 | +0.142 | +0.126 | +60.7 | [-0.203, +0.454] | 0.04 | NO |
| 10% | const | +0.132 | -0.224 | +0.052 | +0.062 | +1.6 | [-0.018, +0.145] | 0.04 | NO |
| 20% | const | +0.263 | -0.534 | +0.099 | +0.109 | +4.0 | [-0.066, +0.286] | 0.04 | NO |
| 30% | const | +0.380 | -0.954 | +0.135 | +0.129 | +6.3 | [-0.158, +0.416] | 0.04 | NO |
| 50% | const | +0.492 | -2.138 | +0.124 | +0.019 | +11.1 | [-0.543, +0.564] | 0.04 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,327,290, Sharpe 1.46, maxDD 263,942, worst wk -155,199; H1: net -394,312, Sharpe -1.99, maxDD 640,985, worst wk -131,752; H2: net 298,578, Sharpe 1.40, maxDD 161,360, worst wk -98,433; all: net 1,231,556, Sharpe 0.91, maxDD 720,202, worst wk -155,199
Correlation with pair (weekly): clean +0.12, H1 +0.00, H2 +0.26, all +0.12; worst-decile weeks (n=17) corr +0.31, sleeve mean in those weeks $-8,646, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.68 | 3.26 | 6.41 | -86,504 | -82,510 | 248,707 | -102,161 | 39.0 |
| clean | add 30% | 1.76 | 3.47 | 6.94 | -91,908 | -85,563 | 249,113 | -112,304 | 38.1 |
| clean | const 20% | 1.72 | 3.37 | 6.68 | -71,365 | -67,229 | 199,128 | -85,786 | 37.1 |
| clean | const 30% | 1.84 | 3.71 | 7.61 | -69,200 | -62,641 | 174,745 | -87,742 | 37.1 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.41 | 4.91 | 3.34 | -86,816 | -73,598 | 154,227 | -87,373 | 42.9 |
| H1 | add 30% | 2.18 | 4.35 | 2.88 | -91,419 | -77,383 | 164,959 | -92,593 | 46.4 |
| H1 | const 20% | 2.29 | 4.62 | 3.14 | -71,294 | -60,392 | 126,280 | -71,986 | 42.9 |
| H1 | const 30% | 1.87 | 3.65 | 2.32 | -68,136 | -57,574 | 128,267 | -69,513 | 50.0 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.38 | 4.87 | 3.80 | -86,155 | -80,963 | 216,039 | -92,015 | 41.7 |
| H2 | add 30% | 2.41 | 4.92 | 3.95 | -89,315 | -81,852 | 215,346 | -99,449 | 41.7 |
| H2 | const 20% | 2.39 | 4.90 | 3.88 | -70,188 | -65,126 | 172,554 | -76,586 | 38.9 |
| H2 | const 30% | 2.43 | 4.97 | 4.15 | -65,364 | -59,009 | 150,118 | -76,305 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.95 | 3.84 | 11.79 | -87,235 | -82,653 | 248,707 | -102,161 | 40.5 |
| all | add 30% | 1.97 | 3.92 | 12.26 | -92,637 | -85,378 | 249,113 | -112,304 | 40.5 |
| all | const 20% | 1.96 | 3.88 | 12.02 | -71,929 | -67,213 | 199,128 | -85,786 | 38.7 |
| all | const 30% | 1.98 | 3.98 | 12.87 | -69,753 | -62,445 | 174,745 | -87,742 | 40.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.220 / -0.419 / +0.084
- [FAIL] 3 worst week within share: all-in worst week +23.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.91 vs p95 0.26 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.046, +0.240]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 25% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.180 / -0.467 / +0.054
- [FAIL] 6 worst-decile corr <=+0.30: +0.31
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K1); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2588 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 7247 | +0.0172 | 0.91 |
| fixed | 7247 | +0.0031 | 0.17 |
| scaled | 7247 | +0.0108 | 0.57 |

Plateau neighbours (all-in 20% uplift; selected +0.096):
- {'lead': 'ZN', 'w': '22', 'thr': '0.3', 'mode': 'follow'}: +0.018 (trades 1848)
- {'lead': 'ZN', 'w': '38', 'thr': '0.3', 'mode': 'follow'}: -0.044 (trades 3132)
- {'lead': 'ZN', 'w': '30', 'thr': '0.22', 'mode': 'follow'}: -0.026 (trades 5288)
- {'lead': 'ZN', 'w': '30', 'thr': '0.38', 'mode': 'follow'}: +0.081 (trades 1308)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.66, p95 0.26, real 0.91. Standalone Sharpe at 2x slippage 0.69.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 519 | 9 | 1.00 |
| 2014 | 612 | -27 | -2.16 |
| 2015 | 570 | 2 | 0.22 |
| 2016 | 582 | 5 | 0.51 |
| 2017 | 696 | -10 | -0.97 |
| 2018 | 964 | 28 | 1.69 |
| 2019 | 748 | -21 | -1.68 |
| 2020 | 864 | 12 | 0.65 |
| 2021 | 948 | -16 | -0.97 |
| 2022 | 744 | 41 | 2.67 |
| 2023 | 840 | -12 | -0.89 |
| 2024 | 740 | 8 | 0.54 |
| 2025 | 820 | 21 | 0.99 |
| 2026 | 700 | 5 | 0.49 |


DONE K1