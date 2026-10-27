# REPORT RU11_ES
**Verdict: LEAD** (6/7 measured gates pass). Selected cell setup=IMP, tf=3, thr=1.5; additive @20% clean/H1/H2 +0.41/+0.59/+0.77; standalone all-in weekly Sharpe 3.11 (2013-26 2.26, dev 2013-22 1.93); pair-window trades 5580. Runtime 0.2 min (+selection 0.1 min). 10-worker pool.

RU11: IMP3 impulse-retrace limit (3 consecutive same-direction tf bars, net >= m ATR, limit at 50% of the net move, stop beyond bar-1 extreme +0.05 ATR, floor 30 ticks, 2R, flat 16:55) on ES. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 4 cells, eligible (>= 40 clean trades): 4. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |     net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|--------:|-------:|:-----------|
| ES    | IMP     |    3 | 1.500 | 3010 |    2.499 | 274.007 |      3 | True       |
| ES    | IMP     |    5 | 1.500 | 2433 |    1.243 | 112.661 |      2 | True       |
| ES    | IMP     |    3 | 2.500 | 1166 |    1.032 |  49.497 |      2 | True       |
| ES    | IMP     |    5 | 2.500 |  886 |    0.862 |  46.902 |      2 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 2.50; replicate best-eligible median -1.02, p95 -0.00; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=8308)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.216 | +0.343 | +0.406 | +0.286 | +4.1 | [+0.189, +0.394] | 0.03 | NO |
| 20% | add | +0.407 | +0.587 | +0.773 | +0.533 | +14.6 | [+0.343, +0.744] | 0.03 | NO |
| 30% | add | +0.572 | +0.754 | +1.096 | +0.740 | +25.3 | [+0.466, +1.046] | 0.03 | NO |
| 50% | add | +0.826 | +0.938 | +1.606 | +1.047 | +46.5 | [+0.636, +1.508] | 0.03 | NO |
| 10% | const | +0.238 | +0.375 | +0.449 | +0.316 | -5.3 | [+0.208, +0.435] | 0.03 | NO |
| 20% | const | +0.493 | +0.679 | +0.940 | +0.642 | -4.0 | [+0.408, +0.900] | 0.03 | NO |
| 30% | const | +0.746 | +0.890 | +1.444 | +0.953 | -2.8 | [+0.589, +1.361] | 0.03 | NO |
| 50% | const | +1.145 | +1.038 | +2.275 | +1.400 | -0.2 | [+0.770, +2.095] | 0.03 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 2,276,541, Sharpe 2.50, maxDD 258,657, worst wk -109,727; H1: net 1,203,499, Sharpe 3.51, maxDD 155,813, worst wk -73,644; H2: net 1,512,367, Sharpe 4.49, maxDD 221,527, worst wk -118,740; all: net 4,992,406, Sharpe 3.11, maxDD 258,657, worst wk -118,740
Correlation with pair (weekly): clean +0.15, H1 +0.38, H2 +0.10, all +0.19; worst-decile weeks (n=17) corr -0.02, sleeve mean in those weeks $-2,351, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.87 | 3.86 | 7.18 | -88,288 | -81,623 | 248,564 | -94,592 | 41.9 |
| clean | add 30% | 2.03 | 4.32 | 7.73 | -93,548 | -83,444 | 260,553 | -103,366 | 41.9 |
| clean | const 20% | 1.95 | 4.10 | 7.46 | -72,734 | -66,027 | 203,647 | -79,183 | 41.0 |
| clean | const 30% | 2.21 | 4.83 | 8.35 | -70,218 | -60,737 | 193,178 | -80,253 | 41.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.41 | 8.58 | 5.00 | -68,890 | -63,718 | 166,949 | -81,058 | 35.7 |
| H1 | add 30% | 3.58 | 9.54 | 5.47 | -70,535 | -66,240 | 174,567 | -82,443 | 42.9 |
| H1 | const 20% | 3.51 | 9.08 | 5.24 | -55,100 | -51,405 | 136,606 | -65,400 | 42.9 |
| H1 | const 30% | 3.72 | 10.54 | 6.02 | -52,361 | -49,937 | 129,053 | -58,957 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 3.07 | 6.75 | 4.90 | -81,174 | -77,004 | 220,800 | -84,117 | 32.4 |
| H2 | add 30% | 3.39 | 7.68 | 5.47 | -81,843 | -77,769 | 225,252 | -84,914 | 29.7 |
| H2 | const 20% | 3.24 | 7.22 | 5.19 | -65,207 | -61,700 | 178,104 | -67,612 | 32.4 |
| H2 | const 30% | 3.74 | 8.69 | 6.15 | -57,892 | -56,237 | 162,394 | -60,156 | 29.7 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 2.39 | 5.14 | 14.89 | -85,904 | -79,661 | 248,564 | -94,592 | 39.1 |
| all | add 30% | 2.60 | 5.78 | 16.12 | -89,713 | -80,923 | 260,553 | -103,366 | 39.6 |
| all | const 20% | 2.50 | 5.47 | 15.52 | -70,247 | -64,216 | 203,647 | -79,183 | 39.6 |
| all | const 30% | 2.81 | 6.49 | 17.54 | -66,228 | -59,117 | 193,178 | -80,253 | 39.1 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.407 / +0.587 / +0.773
- [PASS] 3 worst week within share: all-in worst week +14.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 3.11 vs p95 -1.23 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.343, +0.744]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 67% of 6
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.297 / +0.455 / +0.620
- [PASS] 6 worst-decile corr <=+0.30: -0.02
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU11_ES); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (5580 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 7287 | +0.1352 | 2.47 |
| fixed | 7287 | +0.1022 | 1.93 |
| scaled | 7287 | +0.1022 | 1.93 |

Plateau neighbours (all-in 20% uplift; selected +0.533):
- {'sym': 'ES', 'setup': 'IMP', 'tf': '3', 'thr': '1.125'}: +0.749 (trades 6629)
- {'sym': 'ES', 'setup': 'IMP', 'tf': '3', 'thr': '1.5', 'R': '1.5'}: +0.466 (trades 6280)
- {'sym': 'ES', 'setup': 'IMP', 'tf': '3', 'thr': '1.5', 'L': '15'}: +0.386 (trades 5563)
- {'sym': 'ES', 'setup': 'IMP', 'tf': '3', 'thr': '1.875'}: +0.100 (trades 4229)
- {'sym': 'ES', 'setup': 'IMP', 'tf': '3', 'thr': '1.5', 'R': '2.5'}: +0.411 (trades 5082)
- {'sym': 'ES', 'setup': 'IMP', 'tf': '3', 'thr': '1.5', 'L': '25'}: +0.608 (trades 5579)

Own random-entry null: 300 draws, standalone all-in Sharpe median -2.08, p95 -1.23, real 3.11. Standalone Sharpe at 2x slippage 2.51.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 53 | 3 | 0.43 |
| 2014 | 137 | 6 | 0.55 |
| 2015 | 330 | 60 | 2.37 |
| 2016 | 317 | 32 | 1.28 |
| 2017 | 46 | 6 | 0.83 |
| 2018 | 709 | 66 | 2.26 |
| 2019 | 450 | 56 | 1.76 |
| 2020 | 1762 | 183 | 2.83 |
| 2021 | 1137 | 122 | 3.03 |
| 2022 | 2346 | 210 | 2.90 |
| 2023 | 1166 | 85 | 1.84 |
| 2024 | 1301 | 96 | 1.78 |
| 2025 | 1987 | 247 | 3.63 |
| 2026 | 1841 | 227 | 4.81 |


## Depth null B (entry fraction U(0.25,0.75), 200 worlds)

Real clean weekly Sharpe 2.50; null median 1.75, p95 2.30, rank 0.99 -> DEPTH MATTERS.

DONE RU11_ES