# REPORT RU7_GC
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=mkt, k=2.0, tf=30, S=1.0, R=0.0; additive @20% clean/H1/H2 -0.05/-0.19/-0.05; standalone all-in weekly Sharpe -0.07 (2013-26 -0.54, dev 2013-22 -0.77); pair-window trades 865. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| GC    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  569 |   -0.052 |  -1.874 |      1 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.500 | 0.000 |  554 |   -0.056 |  -1.846 |      2 | True       |
| GC    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 0.000 |  497 |   -0.335 |  -9.750 |      1 | True       |
| GC    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 0.000 |  508 |   -0.590 | -19.410 |      0 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 1.500 |   30 | 1.500 | 0.000 | 1319 |   -0.774 | -34.292 |      1 | True       |
| GC    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1187 |   -1.054 | -43.652 |      1 | True       |
| GC    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 |  838 |   -1.090 | -45.156 |      0 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.000 | 0.000 |  951 |   -1.117 | -56.317 |      1 | True       |
| GC    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 0.000 |  926 |   -1.144 | -52.131 |      0 | True       |
| GC    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 0.000 |  861 |   -1.287 | -59.472 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.05; replicate best-eligible median -0.14, p95 0.64; real beats 55% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.532e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.018 | -0.088 | -0.017 | -0.026 | +5.5 | [-0.122, +0.069] | 0.21 | NO |
| 20% | add | -0.050 | -0.191 | -0.053 | -0.068 | +11.0 | [-0.255, +0.118] | 0.21 | NO |
| 30% | add | -0.092 | -0.305 | -0.107 | -0.123 | +16.6 | [-0.396, +0.150] | 0.21 | NO |
| 50% | add | -0.198 | -0.546 | -0.249 | -0.257 | +27.6 | [-0.683, +0.167] | 0.21 | NO |
| 10% | const | -0.021 | -0.098 | -0.020 | -0.030 | -4.5 | [-0.137, +0.075] | 0.21 | NO |
| 20% | const | -0.070 | -0.247 | -0.078 | -0.094 | -9.0 | [-0.325, +0.135] | 0.21 | NO |
| 30% | const | -0.158 | -0.459 | -0.194 | -0.206 | -13.4 | [-0.580, +0.166] | 0.21 | NO |
| 50% | const | -0.485 | -1.108 | -0.660 | -0.615 | -13.0 | [-1.297, +0.062] | 0.21 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -47,441, Sharpe -0.05, maxDD 876,909, worst wk -160,948; H1: net -57,406, Sharpe -0.30, maxDD 283,206, worst wk -85,019; H2: net 7,196, Sharpe 0.02, maxDD 224,963, worst wk -110,921; all: net -97,650, Sharpe -0.07, maxDD 876,909, worst wk -160,948
Correlation with pair (weekly): clean +0.04, H1 +0.20, H2 +0.04, all +0.06; worst-decile weeks (n=17) corr +0.10, sleeve mean in those weeks $18,981, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.41 | 2.78 | 4.51 | -81,476 | -77,779 | 292,861 | -85,097 | 48.6 |
| clean | add 30% | 1.37 | 2.70 | 3.83 | -84,620 | -79,478 | 343,838 | -88,990 | 48.6 |
| clean | const 20% | 1.39 | 2.75 | 4.14 | -66,335 | -62,774 | 254,680 | -69,635 | 48.6 |
| clean | const 30% | 1.30 | 2.54 | 3.20 | -62,731 | -58,162 | 286,566 | -65,796 | 47.6 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.64 | 5.54 | 3.65 | -80,370 | -70,820 | 159,655 | -87,301 | 39.3 |
| H1 | add 30% | 2.52 | 5.24 | 3.52 | -81,750 | -73,382 | 163,626 | -92,485 | 39.3 |
| H1 | const 20% | 2.58 | 5.39 | 3.58 | -64,848 | -57,681 | 129,313 | -71,914 | 39.3 |
| H1 | const 30% | 2.37 | 4.85 | 3.37 | -58,467 | -53,673 | 118,113 | -69,405 | 39.3 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.24 | 4.54 | 3.45 | -85,953 | -81,855 | 226,289 | -91,638 | 45.9 |
| H2 | add 30% | 2.19 | 4.41 | 3.38 | -89,012 | -83,190 | 230,721 | -96,195 | 45.9 |
| H2 | const 20% | 2.22 | 4.48 | 3.41 | -69,986 | -66,018 | 182,804 | -75,133 | 45.9 |
| H2 | const 30% | 2.10 | 4.20 | 3.31 | -65,061 | -59,435 | 165,494 | -71,438 | 40.5 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.79 | 3.57 | 9.16 | -83,118 | -79,043 | 292,861 | -91,638 | 46.7 |
| all | add 30% | 1.74 | 3.46 | 7.77 | -86,470 | -80,619 | 343,838 | -96,195 | 46.7 |
| all | const 20% | 1.76 | 3.52 | 8.41 | -67,766 | -63,782 | 254,680 | -75,133 | 46.7 |
| all | const 30% | 1.65 | 3.25 | 6.50 | -63,990 | -58,559 | 286,566 | -71,438 | 45.0 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.050 / -0.191 / -0.053
- [PASS] 3 worst week within share: all-in worst week +11.0% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.07 vs p95 0.16 (rank 0.86)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.255, +0.118]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.120 / -0.218 / -0.071
- [PASS] 6 worst-decile corr <=+0.30: +0.10
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_GC); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (865 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2499 | -0.0025 | -0.04 |
| fixed | 2499 | -0.0458 | -0.77 |
| scaled | 2499 | -0.0458 | -0.77 |

Plateau neighbours (all-in 20% uplift; selected -0.068):
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '0.0'}: -0.264 (trades 2214)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '0.75', 'R': '0.0'}: -0.098 (trades 875)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '0.0'}: -0.039 (trades 342)
- {'sym': 'GC', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.25', 'R': '0.0'}: -0.121 (trades 849)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.53, p95 0.16, real -0.07. Standalone Sharpe at 2x slippage -0.34.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 244 | -24 | -1.97 |
| 2014 | 211 | -26 | -1.97 |
| 2015 | 261 | 12 | 0.75 |
| 2016 | 250 | -23 | -1.72 |
| 2017 | 212 | 6 | 0.42 |
| 2018 | 213 | 1 | 0.07 |
| 2019 | 265 | 7 | 0.53 |
| 2020 | 242 | -17 | -1.06 |
| 2021 | 333 | -34 | -2.20 |
| 2022 | 268 | -18 | -0.93 |
| 2023 | 309 | -6 | -0.36 |
| 2024 | 275 | -1 | -0.05 |
| 2025 | 260 | 2 | 0.10 |
| 2026 | 201 | 2 | 0.15 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | -0.05 | -0.05/-0.19/-0.05 |
| 2 tick entry / 2 tick exit | -0.71 | -0.18/-0.24/-0.09 |
| 3 tick entry / 3 tick exit | -1.35 | -0.31/-0.29/-0.16 |
| retrace-limit DISP (b=2.0, tf30, f=0.5, RZ geometry) | -1.04 | -0.20/+0.27/+0.69 |

DONE RU7_GC