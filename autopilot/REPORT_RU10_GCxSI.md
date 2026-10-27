# REPORT RU10_GCxSI
**Verdict: NO** (1/7 measured gates pass). Selected cell nb=1, conf=1, sess=ALL, ent=mkt, k=1.5, tf=30, S=1.0, R=2.0, partner=SI; additive @20% clean/H1/H2 +0.06/+0.17/-0.13; standalone all-in weekly Sharpe 0.52 (2013-26 -0.08, dev 2013-22 -0.33); pair-window trades 1916. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU10 displacement continuation confirmed by a same-direction displacement (range >= 1 ATR) in the partner market. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R | partner   |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|:----------|-----:|---------:|--------:|-------:|:-----------|
| GC    |    1 |      1 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | SI        | 1181 |    0.715 |  43.784 |      3 | True       |
| GC    |    1 |      1 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | SI        | 1945 |    0.688 |  55.930 |      2 | True       |
| GC    |    1 |      1 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 | SI        |  538 |    0.016 |   0.787 |      2 | True       |
| GC    |    1 |      1 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | SI        | 2161 |   -0.159 | -13.681 |      1 | True       |
| GC    |    1 |      1 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | SI        |  815 |   -0.355 | -19.400 |      1 | True       |
| GC    |    1 |      1 | ALL    | stop  | 2.000 |   30 | 1.000 | 2.000 | SI        |  480 |   -0.463 | -20.931 |      1 | True       |
| GC    |    1 |      1 | ALL    | mkt   | 2.000 |   15 | 1.000 | 2.000 | SI        |  892 |   -0.568 | -29.895 |      1 | True       |
| GC    |    1 |      1 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | SI        | 1063 |   -0.760 | -43.589 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.71; replicate best-eligible median -0.04, p95 1.27; real beats 85% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.487e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.037 | +0.106 | -0.054 | +0.021 | +11.3 | [-0.076, +0.123] | 0.04 | NO |
| 20% | add | +0.060 | +0.171 | -0.129 | +0.023 | +22.6 | [-0.166, +0.219] | 0.04 | NO |
| 30% | add | +0.069 | +0.196 | -0.220 | +0.009 | +33.8 | [-0.265, +0.293] | 0.04 | NO |
| 50% | add | +0.059 | +0.148 | -0.429 | -0.053 | +56.4 | [-0.475, +0.385] | 0.04 | NO |
| 10% | const | +0.040 | +0.115 | -0.062 | +0.022 | +1.3 | [-0.085, +0.134] | 0.04 | NO |
| 20% | const | +0.066 | +0.189 | -0.173 | +0.018 | +2.6 | [-0.214, +0.258] | 0.04 | NO |
| 30% | const | +0.066 | +0.178 | -0.352 | -0.027 | +3.8 | [-0.401, +0.360] | 0.04 | NO |
| 50% | const | -0.045 | -0.221 | -0.940 | -0.281 | +12.2 | [-0.945, +0.402] | 0.04 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 650,983, Sharpe 0.71, maxDD 432,120, worst wk -120,641; H1: net 228,255, Sharpe 0.93, maxDD 239,103, worst wk -91,821; H2: net -95,362, Sharpe -0.27, maxDD 504,728, worst wk -112,193; all: net 783,876, Sharpe 0.52, maxDD 540,839, worst wk -120,641
Correlation with pair (weekly): clean +0.18, H1 -0.05, H2 +0.06, all +0.12; worst-decile weeks (n=17) corr +0.33, sleeve mean in those weeks $4,764, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.52 | 2.95 | 5.09 | -87,290 | -83,156 | 286,601 | -95,420 | 44.8 |
| clean | add 30% | 1.53 | 2.97 | 4.99 | -93,257 | -87,335 | 305,954 | -104,474 | 44.8 |
| clean | const 20% | 1.53 | 2.96 | 5.04 | -72,115 | -68,004 | 237,022 | -79,958 | 44.8 |
| clean | const 30% | 1.53 | 2.95 | 4.86 | -71,187 | -65,574 | 231,586 | -81,418 | 46.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.00 | 6.37 | 3.87 | -74,438 | -66,853 | 165,408 | -89,421 | 32.1 |
| H1 | add 30% | 3.02 | 6.29 | 3.84 | -81,956 | -69,373 | 172,256 | -95,666 | 32.1 |
| H1 | const 20% | 3.02 | 6.34 | 3.86 | -62,557 | -53,714 | 135,065 | -74,035 | 32.1 |
| H1 | const 30% | 3.01 | 6.05 | 3.75 | -64,135 | -53,802 | 129,009 | -72,586 | 28.6 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.17 | 4.32 | 3.42 | -98,508 | -89,259 | 222,338 | -101,136 | 40.5 |
| H2 | add 30% | 2.08 | 4.11 | 3.09 | -107,217 | -94,296 | 242,343 | -110,441 | 43.2 |
| H2 | const 20% | 2.12 | 4.22 | 3.25 | -82,290 | -73,422 | 185,600 | -84,631 | 40.5 |
| H2 | const 30% | 1.95 | 3.82 | 2.74 | -82,891 | -70,540 | 188,257 | -85,684 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.88 | 3.70 | 9.98 | -90,020 | -84,297 | 286,601 | -101,136 | 42.0 |
| all | add 30% | 1.87 | 3.66 | 9.60 | -96,627 | -88,468 | 305,954 | -110,441 | 42.6 |
| all | const 20% | 1.88 | 3.68 | 9.78 | -74,630 | -68,999 | 237,022 | -84,631 | 42.0 |
| all | const 30% | 1.83 | 3.56 | 9.18 | -73,943 | -66,587 | 231,586 | -85,684 | 43.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.060 / +0.171 / -0.129
- [FAIL] 3 worst week within share: all-in worst week +22.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.52 vs p95 0.29 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.166, +0.219]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.001 / +0.143 / -0.149
- [FAIL] 6 worst-decile corr <=+0.30: +0.33
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU10_GCxSI); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (1916 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 5020 | +0.0174 | 0.31 |
| fixed | 5020 | -0.0188 | -0.33 |
| scaled | 5020 | -0.0188 | -0.33 |

Plateau neighbours (all-in 20% uplift; selected +0.023):
- {'sym': 'GC', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.125', 'tf': '30', 'S': '1.0', 'R': '2.0', 'partner': 'SI'}: -0.072 (trades 3121)
- {'sym': 'GC', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '0.75', 'R': '2.0', 'partner': 'SI'}: -0.012 (trades 2018)
- {'sym': 'GC', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '1.5', 'partner': 'SI'}: -0.026 (trades 2000)
- {'sym': 'GC', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.875', 'tf': '30', 'S': '1.0', 'R': '2.0', 'partner': 'SI'}: -0.076 (trades 1043)
- {'sym': 'GC', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.25', 'R': '2.0', 'partner': 'SI'}: +0.015 (trades 1800)
- {'sym': 'GC', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '2.5', 'partner': 'SI'}: -0.083 (trades 1851)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.52, p95 0.29, real 0.52. Standalone Sharpe at 2x slippage 0.29.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 467 | -36 | -1.33 |
| 2014 | 412 | 26 | 1.06 |
| 2015 | 477 | 1 | 0.05 |
| 2016 | 498 | -80 | -3.07 |
| 2017 | 440 | -5 | -0.17 |
| 2018 | 440 | 4 | 0.16 |
| 2019 | 499 | 21 | 0.84 |
| 2020 | 548 | 27 | 0.79 |
| 2021 | 626 | -30 | -0.92 |
| 2022 | 613 | -23 | -0.73 |
| 2023 | 635 | 14 | 0.39 |
| 2024 | 585 | 18 | 0.61 |
| 2025 | 585 | 27 | 0.85 |
| 2026 | 495 | 1 | 0.03 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.71 | +0.06/+0.17/-0.13 |
| 2 tick entry / 2 tick exit | -0.09 | -0.09/+0.13/-0.18 |
| 3 tick entry / 3 tick exit | -1.00 | -0.26/+0.03/-0.25 |
| retrace-limit DISP (b=1.5, tf30, f=0.5, RZ geometry) | -0.44 | -0.11/+0.38/+0.44 |

DONE RU10_GCxSI