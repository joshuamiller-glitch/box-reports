# REPORT I2
**Verdict: NO** (2/7 measured gates pass). Selected cell thr=0.1, mode=fade, H=120; additive @20% clean/H1/H2 +0.18/-0.30/+0.02; standalone all-in weekly Sharpe 0.65 (2013-26 -0.26, dev 2013-22 -0.53); pair-window trades 2519. Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

RTH opening gap (ES/NQ/YM/RTY): fade/follow of the 09:30 ET gap vs prior 15:59 close, entry 09:31, time exit 30/120/360 min (no later than 15:55). NT8: simple session-open strategy. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on the clean span only (Gate Amendment 2), H1/H2 read once for one cell; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 18 cells, eligible (>= 60 clean trades): 18. Top cells by clean weekly Sharpe:

|   thr | mode   |   H |    n |   sharpe |     net |   ypos | eligible   |
|------:|:-------|----:|-----:|---------:|--------:|-------:|:-----------|
| 0.100 | fade   | 120 | 1543 |    1.068 |  30.954 |      3 | True       |
| 0.100 | fade   | 360 | 1543 |    0.770 |  41.602 |      2 | True       |
| 0.250 | fade   | 120 |  951 |    0.529 |  12.651 |      1 | True       |
| 0.500 | fade   | 120 |  383 |    0.424 |   6.774 |      2 | True       |
| 0.500 | fade   | 360 |  383 |    0.369 |  10.537 |      2 | True       |
| 0.250 | fade   | 360 |  951 |    0.217 |   9.464 |      1 | True       |
| 0.500 | follow |  30 |  383 |    0.169 |   1.673 |      1 | True       |
| 0.250 | follow |  30 |  951 |    0.078 |   1.213 |      2 | True       |
| 0.100 | fade   |  30 | 1543 |    0.011 |   0.190 |      1 | True       |
| 0.250 | follow | 360 |  951 |   -0.506 | -22.081 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.07; replicate best-eligible median 0.96, p95 1.23; real beats 67% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.144e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.100 | -0.138 | +0.026 | +0.057 | +10.9 | [-0.040, +0.156] | 0.41 | NO |
| 20% | add | +0.182 | -0.301 | +0.022 | +0.091 | +28.0 | [-0.097, +0.285] | 0.41 | NO |
| 30% | add | +0.247 | -0.475 | -0.011 | +0.104 | +45.1 | [-0.170, +0.387] | 0.41 | NO |
| 50% | add | +0.327 | -0.810 | -0.140 | +0.076 | +79.2 | [-0.342, +0.521] | 0.41 | NO |
| 10% | const | +0.110 | -0.155 | +0.027 | +0.062 | +1.5 | [-0.045, +0.172] | 0.41 | NO |
| 20% | const | +0.217 | -0.388 | +0.009 | +0.100 | +9.2 | [-0.131, +0.341] | 0.41 | NO |
| 30% | const | +0.305 | -0.694 | -0.086 | +0.093 | +16.9 | [-0.276, +0.481] | 0.41 | NO |
| 50% | const | +0.331 | -1.431 | -0.577 | -0.129 | +32.3 | [-0.799, +0.591] | 0.41 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 973,142, Sharpe 1.07, maxDD 475,362, worst wk -150,489; H1: net -22,360, Sharpe -0.07, maxDD 429,555, worst wk -206,408; H2: net 75,043, Sharpe 0.20, maxDD 351,484, worst wk -140,958; all: net 1,025,825, Sharpe 0.65, maxDD 475,362, worst wk -206,408
Correlation with pair (weekly): clean -0.00, H1 +0.27, H2 -0.07, all +0.01; worst-decile weeks (n=17) corr -0.24, sleeve mean in those weeks $-19,236, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.64 | 3.18 | 5.85 | -87,537 | -82,423 | 260,811 | -93,139 | 44.8 |
| clean | add 30% | 1.71 | 3.31 | 6.12 | -92,672 | -85,048 | 265,054 | -102,960 | 41.9 |
| clean | const 20% | 1.68 | 3.25 | 6.03 | -72,084 | -66,913 | 208,717 | -78,367 | 43.8 |
| clean | const 30% | 1.77 | 3.41 | 6.34 | -69,492 | -62,199 | 193,022 | -81,074 | 41.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.53 | 5.45 | 3.73 | -90,374 | -74,082 | 158,200 | -98,734 | 46.4 |
| H1 | add 30% | 2.35 | 5.03 | 3.64 | -96,756 | -82,318 | 161,444 | -108,957 | 50.0 |
| H1 | const 20% | 2.44 | 5.25 | 3.68 | -74,852 | -62,560 | 127,858 | -83,077 | 46.4 |
| H1 | const 30% | 2.13 | 4.42 | 3.49 | -73,474 | -65,034 | 117,157 | -85,471 | 50.0 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.32 | 4.39 | 3.04 | -99,773 | -88,677 | 255,132 | -105,607 | 44.4 |
| H2 | add 30% | 2.28 | 4.19 | 2.86 | -111,019 | -93,423 | 273,985 | -119,703 | 41.7 |
| H2 | const 20% | 2.30 | 4.29 | 2.95 | -84,317 | -72,840 | 211,647 | -90,124 | 41.7 |
| H2 | const 30% | 2.21 | 3.92 | 2.66 | -87,835 | -70,176 | 208,757 | -96,478 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.95 | 3.79 | 11.08 | -91,501 | -84,830 | 260,811 | -105,607 | 44.6 |
| all | add 30% | 1.96 | 3.77 | 10.92 | -98,559 | -88,396 | 273,985 | -119,703 | 42.9 |
| all | const 20% | 1.96 | 3.79 | 11.12 | -76,024 | -69,241 | 211,647 | -90,124 | 43.5 |
| all | const 30% | 1.95 | 3.70 | 10.48 | -75,344 | -65,601 | 208,757 | -96,478 | 41.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.182 / -0.301 / +0.022
- [FAIL] 3 worst week within share: all-in worst week +28.0% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.65 vs p95 0.75 (rank 0.87)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.097, +0.285]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 75% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.131 / -0.348 / -0.015
- [PASS] 6 worst-decile corr <=+0.30: -0.24
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I2); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2519 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6905 | +0.0015 | 0.06 |
| fixed | 6905 | -0.0126 | -0.53 |
| scaled | 6905 | -0.0050 | -0.21 |

Plateau neighbours (all-in 20% uplift; selected +0.091):
- {'thr': '0.08', 'mode': 'fade', 'H': '120'}: +0.072 (trades 2660)
- {'thr': '0.12', 'mode': 'fade', 'H': '120'}: +0.091 (trades 2356)
- {'thr': '0.1', 'mode': 'fade', 'H': '90'}: +0.048 (trades 2519)
- {'thr': '0.1', 'mode': 'fade', 'H': '150'}: +0.169 (trades 2519)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.42, p95 0.75, real 0.65. Standalone Sharpe at 2x slippage 0.43.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 537 | -2 | -0.14 |
| 2014 | 558 | 4 | 0.23 |
| 2015 | 575 | -17 | -0.99 |
| 2016 | 582 | -7 | -0.56 |
| 2017 | 696 | 2 | 0.12 |
| 2018 | 796 | -6 | -0.33 |
| 2019 | 789 | -23 | -1.36 |
| 2020 | 821 | 16 | 0.84 |
| 2021 | 783 | -31 | -1.79 |
| 2022 | 768 | -23 | -1.39 |
| 2023 | 766 | 1 | 0.05 |
| 2024 | 785 | 11 | 0.70 |
| 2025 | 753 | 12 | 0.75 |
| 2026 | 657 | 5 | 0.40 |


DONE I2