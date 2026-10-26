# REPORT RX8
**Verdict: LEAD** (5/7 measured gates pass). Selected cell r=10, ex=rsi65; additive @20% clean/H1/H2 +0.16/+1.35/+0.72; standalone all-in weekly Sharpe 1.89 (2013-26 0.85, dev 2013-22 0.35); pair-window trades 126. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RX8 ES-dip (RSI2) x K4 consensus on ES/NQ/RTY/YM at the 16:16 px (4 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 4 cells, eligible (>= 60 clean trades): 2. Top cells by clean weekly Sharpe:

|   r | ex    |   n |   sharpe |    net |   ypos | eligible   |
|----:|:------|----:|---------:|-------:|-------:|:-----------|
|  10 | rsi65 |  68 |    1.137 | 22.664 |      3 | True       |
|  10 | d5    |  75 |    0.946 | 30.101 |      2 | True       |
|   5 | d5    |  37 |    0.632 |  9.897 |      1 | False      |
|   5 | rsi65 |  33 |    0.517 |  6.220 |      2 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.14; replicate best-eligible median 0.85, p95 1.85; real beats 80% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.568e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.089 | +0.769 | +0.356 | +0.232 | +16.6 | [+0.117, +0.357] | 0.77 | NO |
| 20% | add | +0.161 | +1.353 | +0.716 | +0.430 | +34.1 | [+0.207, +0.668] | 0.77 | NO |
| 30% | add | +0.216 | +1.697 | +1.071 | +0.589 | +51.5 | [+0.269, +0.930] | 0.77 | NO |
| 50% | add | +0.281 | +1.853 | +1.719 | +0.791 | +86.4 | [+0.313, +1.302] | 0.77 | NO |
| 10% | const | +0.098 | +0.845 | +0.396 | +0.256 | +6.7 | [+0.128, +0.394] | 0.77 | NO |
| 20% | const | +0.191 | +1.554 | +0.895 | +0.515 | +14.2 | [+0.242, +0.808] | 0.77 | NO |
| 30% | const | +0.264 | +1.853 | +1.501 | +0.735 | +21.8 | [+0.306, +1.195] | 0.77 | NO |
| 50% | const | +0.285 | +1.442 | +2.644 | +0.869 | +36.8 | [+0.139, +1.619] | 0.77 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,035,405, Sharpe 1.14, maxDD 414,740, worst wk -186,246; H1: net 1,424,634, Sharpe 3.01, maxDD 320,820, worst wk -152,622; H2: net 877,737, Sharpe 3.05, maxDD 305,633, worst wk -162,694; all: net 3,337,776, Sharpe 1.89, maxDD 419,278, worst wk -186,246
Correlation with pair (weekly): clean +0.11, H1 -0.22, H2 -0.43, all -0.07; worst-decile weeks (n=17) corr +0.43, sleeve mean in those weeks $6,996, positive share 0.24.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.62 | 3.11 | 4.63 | -87,276 | -82,717 | 332,177 | -110,650 | 41.0 |
| clean | add 30% | 1.68 | 3.22 | 4.58 | -92,669 | -85,757 | 358,211 | -125,039 | 42.9 |
| clean | const 20% | 1.65 | 3.17 | 4.60 | -71,860 | -67,364 | 276,155 | -94,276 | 42.9 |
| clean | const 30% | 1.72 | 3.32 | 4.53 | -69,988 | -62,822 | 274,178 | -100,476 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 4.18 | 11.78 | 7.39 | -60,079 | -50,085 | 118,864 | -78,287 | 32.1 |
| H1 | add 30% | 4.52 | 14.19 | 8.59 | -60,079 | -48,510 | 118,864 | -78,287 | 28.6 |
| H1 | const 20% | 4.38 | 13.08 | 7.99 | -48,063 | -39,216 | 95,091 | -62,630 | 32.1 |
| H1 | const 30% | 4.68 | 16.26 | 10.13 | -42,055 | -37,256 | 83,205 | -54,801 | 25.0 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 3.01 | 6.99 | 5.05 | -81,089 | -66,623 | 185,608 | -82,524 | 41.7 |
| H2 | add 30% | 3.37 | 8.28 | 6.04 | -81,089 | -64,971 | 169,700 | -82,524 | 38.9 |
| H2 | const 20% | 3.19 | 7.63 | 5.52 | -64,871 | -52,422 | 142,123 | -66,020 | 41.7 |
| H2 | const 30% | 3.80 | 9.93 | 7.06 | -56,762 | -44,478 | 112,812 | -57,767 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.29 | 4.70 | 10.09 | -84,903 | -80,738 | 332,177 | -110,650 | 39.3 |
| all | add 30% | 2.45 | 5.13 | 10.29 | -88,498 | -82,493 | 358,211 | -125,039 | 39.3 |
| all | const 20% | 2.37 | 4.93 | 10.20 | -69,281 | -65,293 | 276,155 | -94,276 | 40.5 |
| all | const 30% | 2.59 | 5.57 | 10.51 | -65,362 | -59,539 | 274,178 | -100,476 | 38.7 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.161 / +1.353 / +0.716
- [FAIL] 3 worst week within share: all-in worst week +34.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.89 vs p95 1.73 (rank 0.98)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.207, +0.668]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.158 / +1.348 / +0.712
- [FAIL] 6 worst-decile corr <=+0.30: +0.43
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RX8); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (126 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 165 | +0.2208 | 0.37 |
| fixed | 165 | +0.2078 | 0.35 |
| scaled | 165 | +0.2141 | 0.36 |

Plateau neighbours (all-in 20% uplift; selected +0.430):
- {'r': '8', 'ex': 'rsi65'}: +0.363 (trades 99)
- {'r': '12', 'ex': 'rsi65'}: +0.351 (trades 143)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.88, p95 1.73, real 1.89. Standalone Sharpe at 2x slippage 1.87.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 16 | 2 | 0.16 |
| 2017 | 19 | 14 | 2.06 |
| 2018 | 30 | -12 | -0.66 |
| 2019 | 22 | 2 | 0.22 |
| 2020 | 28 | 0 | 0.02 |
| 2021 | 42 | 36 | 2.22 |
| 2022 | 8 | -7 | -0.89 |
| 2023 | 26 | 16 | 2.65 |
| 2024 | 47 | 20 | 1.65 |
| 2025 | 34 | 16 | 1.13 |
| 2026 | 35 | 34 | 3.84 |


## Beta / drift test (report): beta +0.179; alpha weekly Sharpe 1.61, 90% CI [+0.79, +2.40] (alpha CI lower bound > 0).

DONE RX8