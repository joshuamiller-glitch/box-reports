# REPORT I1
**Verdict: NO** (1/7 measured gates pass). Selected cell thr=0.2, mode=fade, H=720; additive @20% clean/H1/H2 -0.10/-0.31/-0.09; standalone all-in weekly Sharpe -0.48 (2013-26 -0.10, dev 2013-22 0.03); pair-window trades 367. Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

Sunday weekend-gap basket (12 futures): fade/follow of the Sunday-open gap vs Friday close, time exit 60/240/720 min. NT8: calendar-triggered strategy, entry at the second minute of the Sunday session (18:01 ET). Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on 2013-2022, one cell read on the pair window; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (2013-2022 development span; pair window untouched until one cell was chosen)
Grid 18 cells, eligible (>= 100 dev trades and net>0 in >=6 of 10 years): 1. Top cells by dev weekly Sharpe:

|   thr | mode   |   H |    n |   sharpe |     net |   ypos | eligible   |
|------:|:-------|----:|-----:|---------:|--------:|-------:|:-----------|
| 0.200 | fade   | 720 |  782 |    0.027 |   2.135 |      7 | True       |
| 0.400 | fade   | 720 |  322 |   -0.056 |  -3.376 |      3 | False      |
| 0.400 | fade   | 240 |  322 |   -0.074 |  -4.147 |      4 | False      |
| 0.400 | follow | 720 |  322 |   -0.203 | -12.265 |      5 | False      |
| 0.400 | follow | 240 |  322 |   -0.204 | -11.494 |      3 | False      |
| 0.200 | fade   | 240 |  782 |   -0.244 | -15.179 |      2 | False      |
| 0.400 | fade   |  60 |  322 |   -0.253 |  -5.120 |      4 | False      |
| 0.200 | follow | 240 |  782 |   -0.337 | -20.914 |      2 | False      |
| 0.100 | fade   | 720 | 1813 |   -0.384 | -37.786 |      3 | False      |
| 0.100 | follow | 240 | 1813 |   -0.465 | -33.983 |      2 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected dev Sharpe 0.03; replicate best-eligible median -9.00, p95 0.13; real beats 83% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=5.084e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.041 | -0.151 | -0.034 | -0.056 | +5.0 | [-0.143, +0.023] | 0.47 | NO |
| 20% | add | -0.096 | -0.310 | -0.085 | -0.126 | +17.7 | [-0.299, +0.032] | 0.47 | NO |
| 30% | add | -0.161 | -0.477 | -0.149 | -0.207 | +44.9 | [-0.472, +0.029] | 0.47 | NO |
| 50% | add | -0.310 | -0.827 | -0.303 | -0.391 | +99.3 | [-0.826, -0.007] | 0.47 | NO |
| 10% | const | -0.047 | -0.168 | -0.039 | -0.063 | -4.9 | [-0.159, +0.025] | 0.47 | NO |
| 20% | const | -0.127 | -0.393 | -0.116 | -0.165 | +5.0 | [-0.384, +0.031] | 0.47 | NO |
| 30% | const | -0.255 | -0.701 | -0.245 | -0.323 | +25.9 | [-0.697, +0.011] | 0.47 | NO |
| 50% | const | -0.679 | -1.711 | -0.704 | -0.843 | +70.5 | [-1.562, -0.167] | 0.47 | NO |

Standalone (1 unit = pair-risk scaled, $): clean: net -7, Sharpe -0.36, maxDD 16, worst wk -7; H1: net -7, Sharpe -2.83, maxDD 7, worst wk -2; H2: net 0, Sharpe 0.03, maxDD 5, worst wk -4; all: net -13, Sharpe -0.48, maxDD 16, worst wk -7
Correlation with pair (weekly): clean -0.01, H1 -0.09, H2 +0.13, all +0.02; worst-decile weeks (n=17) corr +0.61, sleeve mean in those weeks $-7,158, positive share 0.06.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.36 | 2.51 | 4.88 | -84,406 | -81,205 | 259,045 | -97,103 | 41.9 |
| clean | add 30% | 1.30 | 2.35 | 4.43 | -89,429 | -83,945 | 277,801 | -119,573 | 41.9 |
| clean | const 20% | 1.33 | 2.44 | 4.68 | -69,534 | -66,060 | 213,253 | -86,671 | 41.0 |
| clean | const 30% | 1.20 | 2.11 | 3.87 | -68,531 | -62,061 | 214,684 | -103,924 | 41.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.52 | 5.13 | 3.58 | -77,063 | -65,802 | 147,002 | -78,287 | 39.3 |
| H1 | add 30% | 2.35 | 4.64 | 3.25 | -76,790 | -67,492 | 151,686 | -78,287 | 39.3 |
| H1 | const 20% | 2.43 | 4.89 | 3.42 | -61,541 | -53,066 | 119,475 | -62,630 | 39.3 |
| H1 | const 30% | 2.13 | 4.03 | 2.86 | -53,507 | -49,332 | 110,396 | -54,801 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.21 | 4.49 | 3.46 | -84,882 | -81,641 | 220,612 | -87,531 | 41.7 |
| H2 | add 30% | 2.15 | 4.37 | 3.44 | -87,338 | -82,869 | 222,206 | -90,034 | 41.7 |
| H2 | const 20% | 2.18 | 4.43 | 3.45 | -68,888 | -65,804 | 177,127 | -71,026 | 41.7 |
| H2 | const 30% | 2.05 | 4.19 | 3.42 | -63,347 | -59,114 | 156,978 | -65,277 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.73 | 3.29 | 9.86 | -84,006 | -80,891 | 259,045 | -97,103 | 41.7 |
| all | add 30% | 1.65 | 3.09 | 8.96 | -87,901 | -82,953 | 277,801 | -119,573 | 41.7 |
| all | const 20% | 1.69 | 3.19 | 9.46 | -68,763 | -65,538 | 213,253 | -86,671 | 41.1 |
| all | const 30% | 1.53 | 2.80 | 7.84 | -65,960 | -60,463 | 214,684 | -103,924 | 41.1 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.096 / -0.310 / -0.085
- [PASS] 3 worst week within share: all-in worst week +17.7% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.48 vs p95 -0.14 (rank 0.81)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.299, +0.032]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.122 / -0.379 / -0.148
- [FAIL] 6 worst-decile corr <=+0.30: +0.61
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I1); 2 selection on 2013-2022 only, pair window read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (367 trades in pair window)

Plateau neighbours (all-in 20% uplift; selected -0.126):
- {'thr': '0.15', 'mode': 'fade', 'H': '720'}: -0.151 (trades 462)
- {'thr': '0.25', 'mode': 'fade', 'H': '720'}: -0.072 (trades 296)
- {'thr': '0.2', 'mode': 'fade', 'H': '540'}: -0.152 (trades 367)
- {'thr': '0.2', 'mode': 'fade', 'H': '900'}: -0.024 (trades 367)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.84, p95 -0.14, real -0.48. Standalone Sharpe at 2x slippage -0.70.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 81 | 4 | 0.77 |
| 2014 | 79 | 1 | 0.38 |
| 2015 | 89 | 19 | 2.00 |
| 2016 | 82 | 0 | 0.00 |
| 2017 | 66 | -4 | -0.99 |
| 2018 | 74 | 1 | 0.14 |
| 2019 | 102 | 2 | 0.26 |
| 2020 | 134 | -19 | -1.14 |
| 2021 | 24 | -2 | -0.62 |
| 2022 | 51 | 2 | 0.25 |
| 2023 | 44 | -2 | -0.51 |
| 2024 | 50 | -9 | -1.79 |
| 2025 | 126 | 0 | 0.01 |
| 2026 | 168 | -2 | -0.36 |


DONE I1