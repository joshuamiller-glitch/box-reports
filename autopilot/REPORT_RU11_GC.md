# REPORT RU11_GC
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell setup=IMP, tf=5, thr=1.5; additive @20% clean/H1/H2 +0.80/+1.16/+1.12; standalone all-in weekly Sharpe 4.52 (2013-26 1.91, dev 2013-22 0.93); pair-window trades 6358. Runtime 0.2 min (+selection 0.1 min). 10-worker pool.

RU11: IMP3 impulse-retrace limit (3 consecutive same-direction tf bars, net >= m ATR, limit at 50% of the net move, stop beyond bar-1 extreme +0.05 ATR, floor 30 ticks, 2R, flat 16:55) on GC. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 4 cells, eligible (>= 40 clean trades): 4. Top cells by clean weekly Sharpe:

| sym   | setup   |   tf |   thr |    n |   sharpe |     net |   ypos | eligible   |
|:------|:--------|-----:|------:|-----:|---------:|--------:|-------:|:-----------|
| GC    | IMP     |    5 | 1.500 | 3538 |    4.360 | 442.124 |      2 | True       |
| GC    | IMP     |    3 | 1.500 | 4705 |    3.830 | 511.491 |      3 | True       |
| GC    | IMP     |    3 | 2.500 | 1651 |    0.842 |  68.403 |      2 | True       |
| GC    | IMP     |    5 | 2.500 | 1187 |    0.420 |  22.552 |      2 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 4.36; replicate best-eligible median -0.93, p95 -0.24; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=8983)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.414 | +0.627 | +0.595 | +0.483 | +4.9 | [+0.372, +0.608] | 0.15 | NO |
| 20% | add | +0.797 | +1.158 | +1.118 | +0.918 | +12.8 | [+0.700, +1.161] | 0.15 | NO |
| 30% | add | +1.143 | +1.570 | +1.565 | +1.297 | +22.1 | [+0.984, +1.649] | 0.15 | NO |
| 50% | add | +1.710 | +2.054 | +2.239 | +1.882 | +40.8 | [+1.408, +2.415] | 0.15 | NO |
| 10% | const | +0.458 | +0.692 | +0.656 | +0.534 | -5.0 | [+0.411, +0.673] | 0.15 | NO |
| 20% | const | +0.975 | +1.379 | +1.351 | +1.115 | -6.0 | [+0.849, +1.414] | 0.15 | NO |
| 30% | const | +1.527 | +1.926 | +2.029 | +1.699 | -6.1 | [+1.273, +2.175] | 0.15 | NO |
| 50% | const | +2.522 | +2.239 | +3.060 | +2.605 | -6.3 | [+1.890, +3.400] | 0.15 | INSURANCE |

Standalone at 100% pair-equivalent risk ($): clean: net 3,971,749, Sharpe 4.36, maxDD 258,372, worst wk -76,944; H1: net 1,310,350, Sharpe 3.97, maxDD 132,327, worst wk -93,438; H2: net 2,260,955, Sharpe 5.56, maxDD 174,684, worst wk -54,228; all: net 7,543,054, Sharpe 4.52, maxDD 258,372, worst wk -93,438
Correlation with pair (weekly): clean +0.07, H1 -0.08, H2 +0.15, all +0.08; worst-decile weeks (n=17) corr +0.17, sleeve mean in those weeks $37,456, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 2.26 | 4.73 | 8.14 | -86,221 | -78,847 | 261,069 | -93,108 | 37.1 |
| clean | add 30% | 2.60 | 5.64 | 9.19 | -90,303 | -80,223 | 274,475 | -100,802 | 34.3 |
| clean | const 20% | 2.43 | 5.19 | 8.67 | -70,610 | -63,628 | 214,218 | -77,564 | 36.2 |
| clean | const 30% | 2.99 | 6.70 | 10.39 | -66,886 | -58,124 | 204,199 | -77,487 | 33.3 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.99 | 11.15 | 5.39 | -54,978 | -48,795 | 158,830 | -62,854 | 35.7 |
| H1 | add 30% | 4.40 | 13.41 | 6.08 | -52,516 | -48,827 | 162,389 | -55,815 | 32.1 |
| H1 | const 20% | 4.21 | 12.36 | 5.74 | -42,998 | -39,049 | 128,487 | -47,467 | 32.1 |
| H1 | const 30% | 4.75 | 15.15 | 6.92 | -34,946 | -34,209 | 116,875 | -36,357 | 32.1 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 3.42 | 8.12 | 6.61 | -88,428 | -72,142 | 186,219 | -90,491 | 35.1 |
| H2 | add 30% | 3.86 | 9.85 | 7.70 | -92,098 | -71,260 | 189,185 | -95,909 | 32.4 |
| H2 | const 20% | 3.65 | 9.00 | 7.16 | -72,210 | -57,361 | 150,161 | -74,560 | 32.4 |
| H2 | const 30% | 4.33 | 11.87 | 8.64 | -67,771 | -50,318 | 141,559 | -72,013 | 29.7 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 2.78 | 6.18 | 16.13 | -85,353 | -75,890 | 261,069 | -93,108 | 36.7 |
| all | add 30% | 3.16 | 7.37 | 18.09 | -88,861 | -75,749 | 274,475 | -100,802 | 33.7 |
| all | const 20% | 2.97 | 6.78 | 17.13 | -69,662 | -60,542 | 214,218 | -77,564 | 34.9 |
| all | const 30% | 3.56 | 8.72 | 20.34 | -65,412 | -54,245 | 204,199 | -77,487 | 32.5 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.797 / +1.158 / +1.118
- [PASS] 3 worst week within share: all-in worst week +12.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 4.52 vs p95 -0.75 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.700, +1.161]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 83% of 6
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.666 / +1.032 / +1.038
- [PASS] 6 worst-decile corr <=+0.30: +0.17
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU11_GC); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (6358 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 9457 | +0.0804 | 1.75 |
| fixed | 9457 | +0.0430 | 0.93 |
| scaled | 9457 | +0.0430 | 0.93 |

Plateau neighbours (all-in 20% uplift; selected +0.918):
- {'sym': 'GC', 'setup': 'IMP', 'tf': '5', 'thr': '1.125'}: +1.360 (trades 7993)
- {'sym': 'GC', 'setup': 'IMP', 'tf': '5', 'thr': '1.5', 'R': '1.5'}: +0.847 (trades 6903)
- {'sym': 'GC', 'setup': 'IMP', 'tf': '5', 'thr': '1.5', 'L': '15'}: +0.841 (trades 6365)
- {'sym': 'GC', 'setup': 'IMP', 'tf': '5', 'thr': '1.875'}: +0.556 (trades 4507)
- {'sym': 'GC', 'setup': 'IMP', 'tf': '5', 'thr': '1.5', 'R': '2.5'}: +0.989 (trades 5857)
- {'sym': 'GC', 'setup': 'IMP', 'tf': '5', 'thr': '1.5', 'L': '25'}: +0.951 (trades 6319)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.72, p95 -0.75, real 4.52. Standalone Sharpe at 2x slippage 3.96.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 1140 | 47 | 0.94 |
| 2014 | 720 | -28 | -0.84 |
| 2015 | 669 | 59 | 1.74 |
| 2016 | 947 | 21 | 0.51 |
| 2017 | 458 | -22 | -0.79 |
| 2018 | 454 | -32 | -1.84 |
| 2019 | 672 | 37 | 1.12 |
| 2020 | 1680 | 87 | 1.51 |
| 2021 | 1270 | 106 | 2.19 |
| 2022 | 1447 | 131 | 1.95 |
| 2023 | 1285 | 40 | 0.94 |
| 2024 | 1769 | 264 | 5.02 |
| 2025 | 2239 | 298 | 5.03 |
| 2026 | 1858 | 278 | 5.60 |


## Depth null B (entry fraction U(0.25,0.75), 200 worlds)

Real clean weekly Sharpe 4.36; null median 2.88, p95 3.48, rank 1.00 -> DEPTH MATTERS.

DONE RU11_GC