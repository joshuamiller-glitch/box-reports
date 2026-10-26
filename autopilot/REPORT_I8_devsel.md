# REPORT I8
**Verdict: NO** (1/7 measured gates pass). Selected cell case=A, ex=b, size=60; additive @20% clean/H1/H2 -0.18/-0.06/-0.11; standalone all-in weekly Sharpe -0.40 (2013-26 -0.24, dev 2013-22 -0.08); pair-window trades 2716. Runtime 0.1 min (+selection 0.0 min). 7-worker pool.

Post-exit re-entry book on NQ: reproduces the pair's ST/HM signals with a fixed 60/60 bracket on the 1-minute long series (independent books, no locks), and after a stop-out or target hit re-enters (reverse/same side) with a 30/60 bracket or 30/60-min time exit; 8 lots then scaled; costs 1 tick/side + $34.88 per 8 lots. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on 2013-2022, one cell read on the pair window; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (2013-2022 development span; pair window untouched until one cell was chosen)
Grid 16 cells, eligible (>= 100 dev trades and net>0 in >=6 of 10 years): 3. Top cells by dev weekly Sharpe:

| case   | ex   |   size |    n |   sharpe |         net |   ypos | eligible   |
|:-------|:-----|-------:|-----:|---------:|------------:|-------:|:-----------|
| C      | t    |     60 | 2277 |   -0.039 |  -52021.760 |      3 | False      |
| C      | b    |     60 | 2383 |   -0.042 |  -48879.040 |      3 | False      |
| A      | b    |     60 | 2406 |   -0.083 | -102401.280 |      6 | True       |
| C      | b    |     30 | 2725 |   -0.111 |  -76968.000 |      6 | True       |
| B      | t    |     60 | 2435 |   -0.170 | -213732.800 |      4 | False      |
| A      | t    |     30 | 2742 |   -0.218 | -203800.960 |      4 | False      |
| C      | t    |     30 | 2528 |   -0.225 | -241536.640 |      2 | False      |
| A      | t    |     60 | 2435 |   -0.275 | -345732.800 |      4 | False      |
| D      | t    |     30 | 2528 |   -0.312 | -339296.640 |      6 | True       |
| D      | t    |     60 | 2277 |   -0.347 | -471141.760 |      3 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected dev Sharpe -0.08; replicate best-eligible median 0.12, p95 0.45; real beats 20% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.728)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.088 | -0.021 | -0.044 | -0.075 | +15.8 | [-0.175, +0.026] | 0.03 | NO |
| 20% | add | -0.183 | -0.063 | -0.113 | -0.163 | +37.6 | [-0.356, +0.034] | 0.03 | NO |
| 30% | add | -0.281 | -0.124 | -0.204 | -0.259 | +59.3 | [-0.536, +0.024] | 0.03 | NO |
| 50% | add | -0.472 | -0.287 | -0.421 | -0.460 | +102.9 | [-0.877, -0.029] | 0.03 | NO |
| 10% | const | -0.099 | -0.025 | -0.050 | -0.084 | +6.4 | [-0.195, +0.027] | 0.03 | NO |
| 20% | const | -0.232 | -0.092 | -0.156 | -0.210 | +18.8 | [-0.446, +0.030] | 0.03 | NO |
| 30% | const | -0.405 | -0.224 | -0.340 | -0.388 | +31.1 | [-0.757, -0.007] | 0.03 | NO |
| 50% | const | -0.863 | -0.781 | -0.956 | -0.905 | +55.9 | [-1.550, -0.242] | 0.03 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -483,093, Sharpe -0.53, maxDD 757,516, worst wk -179,794; H1: net -18,490, Sharpe -0.10, maxDD 297,466, worst wk -67,933; H2: net -86,636, Sharpe -0.23, maxDD 566,612, worst wk -139,313; all: net -588,219, Sharpe -0.40, maxDD 1,230,500, worst wk -179,794
Correlation with pair (weekly): clean +0.21, H1 +0.01, H2 +0.01, all +0.14; worst-decile weeks (n=17) corr -0.10, sleeve mean in those weeks $-22,660, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.28 | 2.29 | 3.22 | -98,096 | -91,427 | 382,851 | -113,517 | 43.8 |
| clean | add 30% | 1.18 | 2.05 | 2.73 | -108,469 | -99,146 | 434,222 | -131,496 | 43.8 |
| clean | const 20% | 1.23 | 2.17 | 2.96 | -82,626 | -76,002 | 326,829 | -98,005 | 43.8 |
| clean | const 30% | 1.06 | 1.76 | 2.24 | -86,053 | -76,860 | 350,189 | -108,229 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.76 | 5.91 | 3.91 | -73,088 | -66,278 | 150,819 | -91,710 | 39.3 |
| H1 | add 30% | 2.70 | 5.69 | 3.91 | -78,237 | -69,693 | 150,372 | -98,421 | 39.3 |
| H1 | const 20% | 2.74 | 5.81 | 3.91 | -60,169 | -53,708 | 120,476 | -76,052 | 39.3 |
| H1 | const 30% | 2.60 | 5.31 | 3.74 | -60,214 | -53,391 | 109,697 | -74,935 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.18 | 4.57 | 3.58 | -77,830 | -75,050 | 207,875 | -77,898 | 41.7 |
| H2 | add 30% | 2.09 | 4.38 | 3.45 | -81,914 | -79,093 | 212,964 | -85,555 | 44.4 |
| H2 | const 20% | 2.14 | 4.49 | 3.53 | -63,506 | -61,657 | 167,591 | -64,544 | 44.4 |
| H2 | const 30% | 1.96 | 4.02 | 3.24 | -63,982 | -59,105 | 156,581 | -68,664 | 47.2 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.69 | 3.19 | 6.71 | -94,437 | -87,131 | 382,851 | -113,517 | 42.9 |
| all | add 30% | 1.60 | 2.93 | 5.78 | -103,035 | -93,715 | 434,222 | -131,496 | 43.5 |
| all | const 20% | 1.65 | 3.06 | 6.21 | -78,939 | -72,283 | 326,829 | -98,005 | 43.5 |
| all | const 30% | 1.47 | 2.60 | 4.86 | -81,276 | -72,248 | 350,189 | -108,229 | 44.6 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.183 / -0.063 / -0.113
- [FAIL] 3 worst week within share: all-in worst week +37.6% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.40 vs p95 0.15 (rank 0.69)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.356, +0.034]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.223 / -0.116 / -0.190
- [PASS] 6 worst-decile corr <=+0.30: -0.10
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I8); 2 selection on 2013-2022 only, pair window read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2716 trades in pair window)

Plateau neighbours (all-in 20% uplift; selected -0.163):
- {'case': 'A', 'ex': 'b', 'size': '45'}: -0.158 (trades 3074)
- {'case': 'A', 'ex': 'b', 'size': '75'}: -0.105 (trades 2310)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.61, p95 0.15, real -0.40. Standalone Sharpe at 2x slippage -0.65.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2014 | 27 | 16,778 | 0.73 |
| 2015 | 49 | 35,971 | 1.11 |
| 2016 | 49 | 24,451 | 0.76 |
| 2017 | 22 | 33,993 | 1.83 |
| 2018 | 195 | 4,318 | 0.03 |
| 2019 | 116 | -35,446 | -0.52 |
| 2020 | 565 | 5,693 | 0.02 |
| 2021 | 459 | -41,170 | -0.21 |
| 2022 | 924 | -146,989 | -0.71 |
| 2023 | 449 | -125,701 | -0.61 |
| 2024 | 618 | 59,844 | 0.21 |
| 2025 | 904 | -372,412 | -1.51 |
| 2026 | 1015 | -2,883 | -0.01 |


DONE I8