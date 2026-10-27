# REPORT RU7_SI
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=0.0; additive @20% clean/H1/H2 -0.08/+0.20/+0.07; standalone all-in weekly Sharpe 0.32 (2013-26 -0.75, dev 2013-22 -1.47); pair-window trades 1538. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 |  930 |   -0.152 |  -6.796 |      1 | True       |
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 0.000 |  932 |   -0.513 | -23.364 |      1 | True       |
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 0.000 |  562 |   -0.951 | -31.377 |      0 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 0.000 | 1054 |   -0.998 | -48.609 |      0 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 0.000 |  643 |   -1.174 | -40.627 |      0 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.000 | 0.000 | 1056 |   -1.240 | -63.898 |      0 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  649 |   -1.282 | -47.333 |      0 | True       |
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 0.000 |  567 |   -1.340 | -46.792 |      0 | True       |
| SI    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1239 |   -1.602 | -78.582 |      1 | True       |
| SI    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 0.000 | 1391 |   -1.673 | -83.518 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.15; replicate best-eligible median -0.51, p95 -0.05; real beats 90% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.033e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.035 | +0.120 | +0.044 | +0.005 | +13.5 | [-0.089, +0.099] | 0.09 | NO |
| 20% | add | -0.082 | +0.199 | +0.071 | -0.007 | +27.9 | [-0.189, +0.179] | 0.09 | NO |
| 30% | add | -0.138 | +0.242 | +0.083 | -0.033 | +42.2 | [-0.301, +0.237] | 0.09 | NO |
| 50% | add | -0.265 | +0.242 | +0.068 | -0.116 | +70.8 | [-0.529, +0.303] | 0.09 | NO |
| 10% | const | -0.040 | +0.131 | +0.048 | +0.004 | +3.6 | [-0.099, +0.109] | 0.09 | NO |
| 20% | const | -0.109 | +0.225 | +0.079 | -0.019 | +8.0 | [-0.246, +0.212] | 0.09 | NO |
| 30% | const | -0.218 | +0.253 | +0.078 | -0.083 | +12.4 | [-0.448, +0.287] | 0.09 | NO |
| 50% | const | -0.574 | +0.018 | -0.094 | -0.379 | +21.2 | [-1.049, +0.302] | 0.09 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -138,155, Sharpe -0.15, maxDD 770,894, worst wk -165,053; H1: net 352,873, Sharpe 1.47, maxDD 304,280, worst wk -113,934; H2: net 248,270, Sharpe 0.87, maxDD 191,892, worst wk -119,630; all: net 462,987, Sharpe 0.32, maxDD 770,894, worst wk -165,053
Correlation with pair (weekly): clean +0.09, H1 +0.09, H2 +0.11, all +0.10; worst-decile weeks (n=17) corr +0.10, sleeve mean in those weeks $-5,949, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.38 | 2.59 | 4.12 | -89,362 | -83,707 | 316,402 | -105,517 | 43.8 |
| clean | add 30% | 1.32 | 2.46 | 3.85 | -96,148 | -87,787 | 334,549 | -117,338 | 44.8 |
| clean | const 20% | 1.35 | 2.53 | 3.98 | -74,204 | -68,474 | 260,380 | -89,142 | 45.7 |
| clean | const 30% | 1.24 | 2.27 | 3.55 | -73,411 | -66,000 | 250,516 | -92,776 | 46.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.03 | 6.79 | 3.94 | -70,315 | -68,429 | 168,666 | -73,302 | 42.9 |
| H1 | add 30% | 3.07 | 6.94 | 3.95 | -73,768 | -69,795 | 177,143 | -76,050 | 39.3 |
| H1 | const 20% | 3.05 | 6.88 | 3.94 | -57,099 | -55,289 | 138,324 | -57,915 | 39.3 |
| H1 | const 30% | 3.08 | 6.98 | 3.96 | -55,948 | -50,086 | 131,630 | -63,489 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.37 | 4.66 | 3.75 | -93,685 | -85,391 | 220,956 | -101,073 | 37.8 |
| H2 | add 30% | 2.38 | 4.59 | 3.83 | -101,540 | -91,255 | 222,721 | -113,036 | 35.1 |
| H2 | const 20% | 2.38 | 4.63 | 3.79 | -77,718 | -70,616 | 177,470 | -85,644 | 37.8 |
| H2 | const 30% | 2.38 | 4.48 | 3.93 | -81,522 | -69,250 | 157,493 | -89,892 | 37.8 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.85 | 3.58 | 8.83 | -89,324 | -82,978 | 316,402 | -105,517 | 42.6 |
| all | add 30% | 1.83 | 3.50 | 8.49 | -96,461 | -87,058 | 334,549 | -117,338 | 42.0 |
| all | const 20% | 1.84 | 3.54 | 8.66 | -74,244 | -67,827 | 260,380 | -89,142 | 43.2 |
| all | const 30% | 1.78 | 3.35 | 8.10 | -74,111 | -65,639 | 250,516 | -92,776 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.082 / +0.199 / +0.071
- [FAIL] 3 worst week within share: all-in worst week +27.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.32 vs p95 0.03 (rank 0.98)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.189, +0.179]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.210 / +0.125 / +0.018
- [PASS] 6 worst-decile corr <=+0.30: +0.10
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_SI); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1538 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2269 | -0.0452 | -0.81 |
| fixed | 2269 | -0.0835 | -1.47 |
| scaled | 2269 | -0.0835 | -1.47 |

Plateau neighbours (all-in 20% uplift; selected -0.007):
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '0.0'}: -0.352 (trades 3278)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '0.0'}: -0.002 (trades 1554)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.0', 'L': '15'}: -0.001 (trades 1534)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '0.0'}: -0.066 (trades 692)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '0.0'}: +0.006 (trades 1515)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.0', 'L': '25'}: -0.012 (trades 1544)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.73, p95 0.03, real 0.32. Standalone Sharpe at 2x slippage -0.23.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 351 | -33 | -2.20 |
| 2014 | 175 | 8 | 0.64 |
| 2015 | 172 | -22 | -2.43 |
| 2016 | 212 | -13 | -1.17 |
| 2017 | 80 | -9 | -1.30 |
| 2018 | 39 | -8 | -2.25 |
| 2019 | 83 | -4 | -0.59 |
| 2020 | 318 | -27 | -1.46 |
| 2021 | 436 | -52 | -2.90 |
| 2022 | 403 | -29 | -1.74 |
| 2023 | 417 | -9 | -0.41 |
| 2024 | 478 | -13 | -0.61 |
| 2025 | 479 | 36 | 1.48 |
| 2026 | 412 | 10 | 0.67 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.15 | -0.08/+0.20/+0.07 |
| 2 tick entry / 2 tick exit | -1.50 | -0.34/+0.03/-0.03 |
| 3 tick entry / 3 tick exit | -2.94 | -0.62/-0.12/-0.13 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.20 | -0.07/+0.08/+0.02 |

DONE RU7_SI