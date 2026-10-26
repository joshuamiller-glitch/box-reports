# REPORT I9
**Verdict: NO** (3/7 measured gates pass). Selected cell sig=ibs0.10, exit=hi; additive @20% clean/H1/H2 +0.05/+0.78/+0.17; standalone all-in weekly Sharpe 1.07 (2013-26 0.79, dev 2013-22 0.67); pair-window trades 168. Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

IBS and consecutive-down-days reversal on daily bars (ES/NQ/YM/RTY, C11 16:00-ET bars), close above SMA200, entry at the signal close (MOC fiction), exits first close above prior high / 2 / 5 days, 3-ATR20 stop, mark-to-market daily. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on 2013-2022, one cell read on the pair window; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (2013-2022 development span; pair window untouched until one cell was chosen)
Grid 12 cells, eligible (>= 100 dev trades and net>0 in >=6 of 10 years): 6. Top cells by dev weekly Sharpe:

| sig     | exit   |   n |   sharpe |    net |   ypos | eligible   |
|:--------|:-------|----:|---------:|-------:|-------:|:-----------|
| ibs0.10 | hi     | 377 |    0.671 | 86.466 |      7 | True       |
| ibs0.10 | d5     | 344 |    0.602 | 84.908 |      7 | True       |
| ibs0.20 | d5     | 528 |    0.495 | 88.328 |      7 | True       |
| ibs0.20 | hi     | 594 |    0.368 | 63.765 |      6 | True       |
| down3   | hi     | 252 |    0.301 | 32.864 |      6 | True       |
| down3   | d5     | 253 |    0.241 | 30.052 |      4 | False      |
| ibs0.10 | d2     | 419 |    0.188 | 21.263 |      6 | True       |
| down3   | d2     | 275 |    0.127 | 11.411 |      5 | False      |
| down4   | hi     | 110 |    0.126 |  9.048 |      4 | False      |
| ibs0.20 | d2     | 714 |    0.090 | 12.323 |      4 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected dev Sharpe 0.67; replicate best-eligible median 0.74, p95 1.05; real beats 30% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.757e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.033 | +0.411 | +0.090 | +0.096 | +13.1 | [+0.003, +0.192] | 0.53 | NO |
| 20% | add | +0.052 | +0.777 | +0.174 | +0.173 | +37.5 | [-0.010, +0.365] | 0.53 | NO |
| 30% | add | +0.056 | +1.085 | +0.249 | +0.231 | +62.1 | [-0.037, +0.514] | 0.53 | NO |
| 50% | add | +0.031 | +1.501 | +0.376 | +0.292 | +111.2 | [-0.125, +0.743] | 0.53 | NO |
| 10% | const | +0.036 | +0.454 | +0.100 | +0.106 | +4.1 | [+0.002, +0.213] | 0.53 | NO |
| 20% | const | +0.055 | +0.939 | +0.212 | +0.204 | +19.8 | [-0.023, +0.443] | 0.53 | NO |
| 30% | const | +0.044 | +1.382 | +0.334 | +0.278 | +35.6 | [-0.091, +0.673] | 0.53 | NO |
| 50% | const | -0.124 | +1.713 | +0.549 | +0.241 | +67.0 | [-0.449, +0.980] | 0.53 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 427,274, Sharpe 0.47, maxDD 347,990, worst wk -202,662; H1: net 777,247, Sharpe 3.06, maxDD 124,987, worst wk -113,315; H2: net 282,208, Sharpe 1.56, maxDD 136,628, worst wk -78,878; all: net 1,486,729, Sharpe 1.07, maxDD 361,718, worst wk -202,662
Correlation with pair (weekly): clean +0.04, H1 -0.16, H2 -0.07, all -0.01; worst-decile weeks (n=17) corr +0.15, sleeve mean in those weeks $-6,401, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.51 | 2.79 | 4.59 | -96,702 | -87,188 | 308,193 | -113,483 | 41.9 |
| clean | add 30% | 1.52 | 2.74 | 4.52 | -106,205 | -92,046 | 322,500 | -133,750 | 42.9 |
| clean | const 20% | 1.52 | 2.77 | 4.56 | -81,163 | -71,694 | 252,171 | -98,893 | 42.9 |
| clean | const 30% | 1.50 | 2.64 | 4.27 | -82,896 | -68,804 | 248,131 | -111,864 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.60 | 8.57 | 4.97 | -71,722 | -61,802 | 150,614 | -76,932 | 35.7 |
| H1 | add 30% | 3.91 | 9.66 | 5.26 | -68,778 | -59,688 | 157,105 | -76,932 | 32.1 |
| H1 | const 20% | 3.77 | 9.13 | 5.12 | -56,200 | -48,596 | 123,088 | -61,546 | 35.7 |
| H1 | const 30% | 4.21 | 10.87 | 5.60 | -45,495 | -39,879 | 115,815 | -53,853 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.47 | 5.16 | 3.79 | -80,380 | -79,086 | 216,021 | -81,107 | 44.4 |
| H2 | add 30% | 2.54 | 5.39 | 3.93 | -80,026 | -79,036 | 215,319 | -80,398 | 41.7 |
| H2 | const 20% | 2.51 | 5.28 | 3.86 | -64,162 | -63,249 | 172,536 | -64,602 | 41.7 |
| H2 | const 30% | 2.63 | 5.69 | 4.11 | -55,740 | -55,281 | 150,092 | -55,757 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.03 | 3.94 | 9.68 | -91,045 | -83,661 | 308,193 | -113,483 | 41.1 |
| all | add 30% | 2.09 | 4.01 | 9.71 | -97,359 | -86,578 | 322,500 | -133,750 | 40.5 |
| all | const 20% | 2.06 | 3.98 | 9.70 | -75,362 | -68,095 | 252,171 | -98,893 | 41.1 |
| all | const 30% | 2.13 | 4.04 | 9.37 | -73,833 | -63,462 | 248,131 | -111,864 | 41.1 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.052 / +0.777 / +0.174
- [FAIL] 3 worst week within share: all-in worst week +37.5% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.07 vs p95 0.93 (rank 0.98)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.010, +0.365]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.048 / +0.773 / +0.172
- [PASS] 6 worst-decile corr <=+0.30: +0.15
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I9); 2 selection on 2013-2022 only, pair window read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (168 trades in pair window)

Plateau neighbours (all-in 20% uplift; selected +0.173):
- {'sig': 'ibs0.10', 'exit': 'hi', 'theta': '0.08'}: +0.169 (trades 147)
- {'sig': 'ibs0.10', 'exit': 'hi', 'theta': '0.12'}: +0.169 (trades 193)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.20, p95 0.93, real 1.07. Standalone Sharpe at 2x slippage 1.06.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 6 | 7 | 3.60 |
| 2014 | 43 | 1 | 0.09 |
| 2015 | 47 | -0 | -0.01 |
| 2016 | 27 | 6 | 0.43 |
| 2017 | 36 | 25 | 1.91 |
| 2018 | 38 | -6 | -0.43 |
| 2019 | 44 | 20 | 1.84 |
| 2020 | 49 | 24 | 1.74 |
| 2021 | 74 | 13 | 0.74 |
| 2022 | 13 | -3 | -0.34 |
| 2023 | 59 | 5 | 0.34 |
| 2024 | 59 | 18 | 0.93 |
| 2025 | 45 | 19 | 1.37 |
| 2026 | 38 | 18 | 2.10 |


DONE I9