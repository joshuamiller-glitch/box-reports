# REPORT RX7
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell ds=0.04; additive @20% clean/H1/H2 +0.15/+0.29/+0.17; standalone all-in weekly Sharpe 1.19 (2013-26 0.30, dev 2013-22 0.04); pair-window trades 325. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RX7 K4 with asymmetric long/short thresholds: long p>=0.58, short p<=0.5-ds (3 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 100 clean trades): 3. Top cells by clean weekly Sharpe:

|    ds |   n |   sharpe |    net |   ypos | eligible   |
|------:|----:|---------:|-------:|-------:|:-----------|
| 0.040 | 219 |    1.089 | 36.263 |      2 | True       |
| 0.030 | 250 |    0.994 | 34.515 |      2 | True       |
| 0.020 | 286 |    0.831 | 30.392 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.09; replicate best-eligible median 0.58, p95 1.26; real beats 83% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.656e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.085 | +0.151 | +0.085 | +0.089 | +4.5 | [+0.027, +0.155] | 0.30 | NO |
| 20% | add | +0.152 | +0.291 | +0.165 | +0.163 | +9.8 | [+0.041, +0.290] | 0.30 | NO |
| 30% | add | +0.202 | +0.419 | +0.241 | +0.221 | +15.2 | [+0.037, +0.403] | 0.30 | NO |
| 50% | add | +0.259 | +0.627 | +0.376 | +0.292 | +25.8 | [+0.001, +0.580] | 0.30 | NO |
| 10% | const | +0.093 | +0.167 | +0.094 | +0.098 | -5.4 | [+0.029, +0.171] | 0.30 | NO |
| 20% | const | +0.179 | +0.357 | +0.204 | +0.194 | -10.0 | [+0.041, +0.348] | 0.30 | NO |
| 30% | const | +0.245 | +0.560 | +0.330 | +0.273 | -14.6 | [+0.018, +0.524] | 0.30 | NO |
| 50% | const | +0.246 | +0.871 | +0.613 | +0.292 | +15.9 | [-0.229, +0.808] | 0.30 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 963,267, Sharpe 1.06, maxDD 444,107, worst wk -234,658; H1: net 260,715, Sharpe 1.88, maxDD 98,006, worst wk -60,431; H2: net 252,260, Sharpe 1.72, maxDD 140,832, worst wk -92,792; all: net 1,476,242, Sharpe 1.19, maxDD 444,107, worst wk -234,658
Correlation with pair (weekly): clean +0.09, H1 -0.17, H2 -0.10, all +0.04; worst-decile weeks (n=17) corr +0.23, sleeve mean in those weeks $12,057, positive share 0.29.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.61 | 3.24 | 5.93 | -80,477 | -78,865 | 256,929 | -90,653 | 43.8 |
| clean | add 30% | 1.66 | 3.45 | 6.60 | -81,368 | -79,317 | 245,338 | -95,043 | 42.9 |
| clean | const 20% | 1.64 | 3.35 | 6.25 | -64,738 | -63,273 | 200,907 | -74,278 | 41.9 |
| clean | const 30% | 1.70 | 3.67 | 7.10 | -57,760 | -55,929 | 171,707 | -70,480 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.12 | 7.41 | 4.69 | -67,659 | -59,396 | 137,703 | -69,154 | 39.3 |
| H1 | add 30% | 3.25 | 8.07 | 5.04 | -62,684 | -56,079 | 133,406 | -65,265 | 35.7 |
| H1 | const 20% | 3.18 | 7.74 | 4.90 | -52,137 | -46,190 | 107,594 | -53,768 | 35.7 |
| H1 | const 30% | 3.39 | 8.98 | 5.40 | -39,401 | -36,270 | 91,428 | -42,185 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.46 | 5.18 | 3.73 | -79,970 | -76,596 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.54 | 5.42 | 3.85 | -79,970 | -75,301 | 217,425 | -82,524 | 44.4 |
| H2 | const 20% | 2.50 | 5.30 | 3.79 | -63,976 | -60,759 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 2.63 | 5.72 | 4.00 | -55,979 | -51,545 | 152,198 | -57,767 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.02 | 4.16 | 11.60 | -80,007 | -77,413 | 256,929 | -90,653 | 43.5 |
| all | add 30% | 2.08 | 4.40 | 12.75 | -80,601 | -77,234 | 245,338 | -95,043 | 42.3 |
| all | const 20% | 2.05 | 4.28 | 12.16 | -64,243 | -61,856 | 200,907 | -74,278 | 41.7 |
| all | const 30% | 2.13 | 4.67 | 13.53 | -56,956 | -54,098 | 171,707 | -70,480 | 43.5 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.152 / +0.291 / +0.165
- [PASS] 3 worst week within share: all-in worst week +9.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.19 vs p95 1.10 (rank 0.96)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.041, +0.290]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.146 / +0.288 / +0.162
- [PASS] 6 worst-decile corr <=+0.30: +0.23
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RX7); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (325 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2477 | +0.0141 | 0.26 |
| fixed | 2477 | +0.0020 | 0.04 |
| scaled | 2477 | +0.0076 | 0.14 |

Plateau neighbours (all-in 20% uplift; selected +0.163):
- {'ds': '0.03'}: +0.152 (trades 358)
- {'ds': '0.05'}: +0.168 (trades 297)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.24, p95 1.10, real 1.19. Standalone Sharpe at 2x slippage 1.16.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 413 | 0 | 0.00 |
| 2017 | 430 | 11 | 0.51 |
| 2018 | 396 | -5 | -0.23 |
| 2019 | 261 | -24 | -1.40 |
| 2020 | 387 | 25 | 1.30 |
| 2021 | 316 | 16 | 0.96 |
| 2022 | 274 | -16 | -0.86 |
| 2023 | 77 | -11 | -1.12 |
| 2024 | 98 | 14 | 0.83 |
| 2025 | 105 | 37 | 2.52 |
| 2026 | 74 | 11 | 1.89 |


## Beta / drift test (report): beta +0.097; alpha weekly Sharpe 1.03, 90% CI [+0.13, +1.82] (alpha CI lower bound > 0).

DONE RX7