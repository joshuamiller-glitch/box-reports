# REPORT I8
**Verdict: NO** (1/7 measured gates pass). Selected cell case=B, ex=t, size=30; additive @20% clean/H1/H2 +0.15/-0.09/-0.47; standalone all-in weekly Sharpe 0.17 (2013-26 -0.07, dev 2013-22 -0.45); pair-window trades 2853. Runtime 0.1 min (+selection 0.0 min). 7-worker pool.

Post-exit re-entry book on NQ: reproduces the pair's ST/HM signals with a fixed 60/60 bracket on the 1-minute long series (independent books, no locks), and after a stop-out or target hit re-enters (reverse/same side) with a 30/60 bracket or 30/60-min time exit; 8 lots then scaled; costs 1 tick/side + $34.88 per 8 lots. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on the clean span only (Gate Amendment 2), H1/H2 read once for one cell; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 60 clean trades): 16. Top cells by clean weekly Sharpe:

| case   | ex   |   size |    n |   sharpe |         net |   ypos | eligible   |
|:-------|:-----|-------:|-----:|---------:|------------:|-------:|:-----------|
| B      | t    |     30 | 1511 |    1.118 |  668136.320 |      2 | True       |
| C      | t    |     60 | 1333 |    0.330 |  185304.960 |      1 | True       |
| C      | t    |     30 | 1513 |    0.126 |   52866.560 |      2 | True       |
| B      | t    |     60 | 1319 |   -0.111 |  -90566.720 |      1 | True       |
| B      | b    |     60 | 1389 |   -0.187 |  -97128.320 |      1 | True       |
| A      | t    |     60 | 1319 |   -0.259 | -212486.720 |      2 | True       |
| C      | b    |     60 | 1498 |   -0.387 | -170050.240 |      1 | True       |
| D      | b    |     60 | 1498 |   -0.489 | -212610.240 |      2 | True       |
| A      | b    |     60 | 1389 |   -0.530 | -279608.320 |      1 | True       |
| A      | b    |     30 | 1676 |   -0.540 | -153538.880 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.12; replicate best-eligible median 0.93, p95 1.41; real beats 70% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.524)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.083 | -0.029 | -0.219 | -0.003 | +12.7 | [-0.099, +0.090] | 0.24 | NO |
| 20% | add | +0.149 | -0.089 | -0.466 | -0.028 | +27.2 | [-0.212, +0.150] | 0.24 | NO |
| 30% | add | +0.199 | -0.178 | -0.723 | -0.069 | +44.3 | [-0.339, +0.188] | 0.24 | NO |
| 50% | add | +0.255 | -0.413 | -1.223 | -0.186 | +78.3 | [-0.611, +0.215] | 0.24 | NO |
| 10% | const | +0.091 | -0.034 | -0.246 | -0.005 | +2.7 | [-0.111, +0.098] | 0.24 | NO |
| 20% | const | +0.176 | -0.130 | -0.594 | -0.046 | +8.6 | [-0.275, +0.171] | 0.24 | NO |
| 30% | const | +0.240 | -0.322 | -1.051 | -0.141 | +16.3 | [-0.513, +0.209] | 0.24 | NO |
| 50% | const | +0.250 | -1.065 | -2.139 | -0.519 | +31.7 | [-1.215, +0.150] | 0.24 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,018,158, Sharpe 1.12, maxDD 268,424, worst wk -101,341; H1: net -69,732, Sharpe -0.31, maxDD 244,566, worst wk -140,383; H2: net -676,677, Sharpe -1.56, maxDD 1,151,614, worst wk -265,668; all: net 271,749, Sharpe 0.17, maxDD 1,151,614, worst wk -265,668
Correlation with pair (weekly): clean +0.14, H1 -0.07, H2 -0.01, all +0.05; worst-decile weeks (n=17) corr +0.11, sleeve mean in those weeks $-1,103, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.61 | 3.22 | 5.49 | -81,253 | -77,396 | 279,175 | -86,162 | 41.0 |
| clean | add 30% | 1.66 | 3.41 | 5.87 | -82,960 | -77,374 | 278,708 | -90,693 | 41.9 |
| clean | const 20% | 1.64 | 3.32 | 5.68 | -65,685 | -61,894 | 223,153 | -70,734 | 41.9 |
| clean | const 30% | 1.70 | 3.61 | 6.35 | -59,608 | -54,734 | 194,675 | -67,580 | 40.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.74 | 5.60 | 3.46 | -79,897 | -68,491 | 167,637 | -105,009 | 39.3 |
| H1 | add 30% | 2.65 | 5.17 | 3.14 | -87,329 | -72,565 | 182,639 | -119,047 | 42.9 |
| H1 | const 20% | 2.70 | 5.40 | 3.29 | -65,069 | -56,422 | 140,111 | -89,623 | 42.9 |
| H1 | const 30% | 2.51 | 4.59 | 2.79 | -71,917 | -55,865 | 141,350 | -95,968 | 46.4 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 1.83 | 3.33 | 2.54 | -98,804 | -93,316 | 246,461 | -103,405 | 44.4 |
| H2 | add 30% | 1.57 | 2.71 | 2.14 | -108,221 | -102,812 | 260,979 | -113,846 | 44.4 |
| H2 | const 20% | 1.70 | 3.01 | 2.33 | -82,810 | -78,451 | 202,976 | -86,900 | 44.4 |
| H2 | const 30% | 1.24 | 2.01 | 1.69 | -86,598 | -80,515 | 195,751 | -89,088 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.83 | 3.56 | 9.81 | -90,430 | -83,022 | 279,175 | -105,009 | 41.7 |
| all | add 30% | 1.79 | 3.46 | 9.93 | -97,418 | -86,280 | 278,708 | -119,047 | 42.3 |
| all | const 20% | 1.81 | 3.51 | 9.87 | -75,139 | -67,652 | 223,153 | -89,623 | 42.3 |
| all | const 30% | 1.71 | 3.28 | 10.02 | -74,481 | -64,231 | 195,751 | -95,968 | 41.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.149 / -0.089 / -0.466
- [FAIL] 3 worst week within share: all-in worst week +27.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.17 vs p95 0.68 (rank 0.69)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.212, +0.150]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.111 / -0.138 / -0.532
- [PASS] 6 worst-decile corr <=+0.30: +0.11
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I8); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2853 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2742 | -40.5543 | -0.12 |
| fixed | 2742 | -155.4343 | -0.45 |
| scaled | 2742 | -158.5324 | -0.46 |

Plateau neighbours (all-in 20% uplift; selected -0.028):
- {'case': 'B', 'ex': 't', 'size': '22'}: -0.042 (trades 3001)
- {'case': 'B', 'ex': 't', 'size': '38'}: -0.065 (trades 2733)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.04, p95 0.68, real 0.17. Standalone Sharpe at 2x slippage -0.05.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2014 | 30 | 6,434 | 0.73 |
| 2015 | 54 | -13,804 | -0.77 |
| 2016 | 53 | -4,649 | -0.21 |
| 2017 | 24 | -16,717 | -2.37 |
| 2018 | 238 | -63,541 | -0.99 |
| 2019 | 133 | 22,761 | 0.66 |
| 2020 | 664 | -7,520 | -0.05 |
| 2021 | 528 | -24,897 | -0.26 |
| 2022 | 1018 | -324,268 | -1.37 |
| 2023 | 508 | 135,681 | 0.97 |
| 2024 | 707 | -14,100 | -0.08 |
| 2025 | 928 | 639,991 | 1.57 |
| 2026 | 1018 | -499,548 | -1.54 |


DONE I8