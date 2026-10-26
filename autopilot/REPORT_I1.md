# REPORT I1
**Verdict: NO** (2/7 measured gates pass). Selected cell thr=0.2, mode=fade, H=60; additive @20% clean/H1/H2 +0.22/+0.71/-0.27; standalone all-in weekly Sharpe 0.81 (2013-26 -0.24, dev 2013-22 -0.72); pair-window trades 367. Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

Sunday weekend-gap basket (12 futures): fade/follow of the Sunday-open gap vs Friday close, time exit 60/240/720 min. NT8: calendar-triggered strategy, entry at the second minute of the Sunday session (18:01 ET). Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on the clean span only (Gate Amendment 2), H1/H2 read once for one cell; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 18 cells, eligible (>= 60 clean trades): 18. Top cells by clean weekly Sharpe:

|   thr | mode   |   H |   n |   sharpe |    net |   ypos | eligible   |
|------:|:-------|----:|----:|---------:|-------:|-------:|:-----------|
| 0.200 | fade   |  60 | 163 |    1.278 |  7.414 |      1 | True       |
| 0.400 | fade   |  60 |  68 |    0.963 |  4.313 |      1 | True       |
| 0.400 | fade   | 240 |  68 |    0.729 |  5.523 |      1 | True       |
| 0.100 | follow | 720 | 328 |    0.635 | 12.735 |      2 | True       |
| 0.200 | fade   | 240 | 163 |    0.475 |  4.630 |      1 | True       |
| 0.400 | fade   | 720 |  68 |    0.148 |  1.627 |      2 | True       |
| 0.200 | follow | 720 | 163 |    0.024 |  0.423 |      2 | True       |
| 0.100 | fade   |  60 | 328 |   -0.138 | -1.029 |      1 | True       |
| 0.100 | fade   | 240 | 328 |   -0.282 | -3.120 |      1 | True       |
| 0.200 | fade   | 720 | 163 |   -0.374 | -6.508 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.28; replicate best-eligible median 0.80, p95 1.71; real beats 83% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.524e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.118 | +0.385 | -0.107 | +0.098 | +3.2 | [-0.022, +0.221] | 0.69 | NO |
| 20% | add | +0.219 | +0.710 | -0.269 | +0.162 | +9.4 | [-0.075, +0.399] | 0.69 | NO |
| 30% | add | +0.302 | +0.946 | -0.457 | +0.192 | +70.4 | [-0.161, +0.534] | 0.69 | NO |
| 50% | add | +0.411 | +1.133 | -0.831 | +0.172 | +192.4 | [-0.386, +0.697] | 0.69 | NO |
| 10% | const | +0.130 | +0.425 | -0.123 | +0.107 | -6.8 | [-0.027, +0.243] | 0.69 | NO |
| 20% | const | +0.263 | +0.840 | -0.361 | +0.181 | +11.9 | [-0.114, +0.473] | 0.69 | NO |
| 30% | const | +0.380 | +1.106 | -0.703 | +0.189 | +74.2 | [-0.303, +0.653] | 0.69 | NO |
| 50% | const | +0.463 | +0.776 | -1.471 | -0.058 | +198.7 | [-0.908, +0.766] | 0.69 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,129,602, Sharpe 1.24, maxDD 322,873, worst wk -158,749; H1: net 583,927, Sharpe 1.83, maxDD 140,371, worst wk -55,964; H2: net -186,257, Sharpe -0.31, maxDD 653,667, worst wk -503,414; all: net 1,527,272, Sharpe 0.81, maxDD 653,667, worst wk -503,414
Correlation with pair (weekly): clean -0.01, H1 -0.29, H2 +0.04, all -0.04; worst-decile weeks (n=17) corr +0.80, sleeve mean in those weeks $-1,218, positive share 0.18.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.68 | 3.24 | 6.04 | -80,033 | -78,758 | 257,440 | -86,866 | 40.0 |
| clean | add 30% | 1.76 | 3.43 | 6.36 | -83,023 | -80,389 | 262,213 | -94,427 | 41.0 |
| clean | const 20% | 1.72 | 3.34 | 6.21 | -65,222 | -63,659 | 207,861 | -70,491 | 40.0 |
| clean | const 30% | 1.84 | 3.65 | 6.76 | -60,807 | -57,740 | 187,845 | -79,497 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.54 | 8.23 | 4.77 | -62,236 | -56,786 | 149,034 | -78,287 | 32.1 |
| H1 | add 30% | 3.77 | 9.08 | 5.21 | -63,091 | -56,351 | 147,694 | -78,287 | 32.1 |
| H1 | const 20% | 3.67 | 8.68 | 4.99 | -50,071 | -44,813 | 118,691 | -62,630 | 32.1 |
| H1 | const 30% | 3.93 | 9.86 | 5.78 | -45,067 | -40,048 | 102,181 | -54,801 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.03 | 4.01 | 3.39 | -89,067 | -83,733 | 213,681 | -90,306 | 47.2 |
| H2 | add 30% | 1.84 | 3.46 | 3.33 | -115,563 | -96,982 | 211,809 | -140,647 | 47.2 |
| H2 | const 20% | 1.93 | 3.74 | 3.36 | -81,852 | -72,286 | 170,196 | -92,381 | 47.2 |
| H2 | const 30% | 1.59 | 2.80 | 2.58 | -104,741 | -79,811 | 184,617 | -143,760 | 50.0 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.02 | 3.97 | 11.62 | -82,061 | -79,721 | 257,440 | -90,306 | 40.5 |
| all | add 30% | 2.05 | 4.01 | 11.99 | -89,943 | -83,847 | 262,213 | -140,647 | 41.1 |
| all | const 20% | 2.04 | 4.00 | 11.80 | -68,802 | -65,427 | 207,861 | -92,381 | 40.5 |
| all | const 30% | 2.04 | 3.95 | 11.64 | -70,053 | -62,407 | 200,761 | -143,760 | 42.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.219 / +0.710 / -0.269
- [PASS] 3 worst week within share: all-in worst week +9.4% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.81 vs p95 -0.34 (rank 1.00)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.075, +0.399]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.142 / +0.522 / -0.458
- [FAIL] 6 worst-decile corr <=+0.30: +0.80
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I1); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (367 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 782 | -0.0017 | -0.05 |
| fixed | 782 | -0.0248 | -0.72 |
| scaled | 782 | -0.0239 | -0.70 |

Plateau neighbours (all-in 20% uplift; selected +0.162):
- {'thr': '0.15', 'mode': 'fade', 'H': '60'}: +0.086 (trades 462)
- {'thr': '0.25', 'mode': 'fade', 'H': '60'}: +0.166 (trades 296)
- {'thr': '0.2', 'mode': 'fade', 'H': '45'}: +0.094 (trades 367)
- {'thr': '0.2', 'mode': 'fade', 'H': '75'}: +0.168 (trades 367)

Own random-entry null: 500 draws, standalone all-in Sharpe median -1.00, p95 -0.34, real 0.81. Standalone Sharpe at 2x slippage 0.33.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 81 | -5 | -1.97 |
| 2014 | 79 | -5 | -2.43 |
| 2015 | 89 | 1 | 0.43 |
| 2016 | 82 | -3 | -1.76 |
| 2017 | 66 | -3 | -1.54 |
| 2018 | 74 | -0 | -0.11 |
| 2019 | 102 | -1 | -0.23 |
| 2020 | 134 | -3 | -0.61 |
| 2021 | 24 | -2 | -0.98 |
| 2022 | 51 | 1 | 0.69 |
| 2023 | 44 | -1 | -0.52 |
| 2024 | 50 | -1 | -0.62 |
| 2025 | 126 | 9 | 2.43 |
| 2026 | 168 | 2 | 0.39 |


DONE I1