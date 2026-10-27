# REPORT RU7_HO
**Verdict: NO** (3/7 measured gates pass). Selected cell nb=1, conf=0, sess=ALL, ent=stop, k=2.0, tf=15, S=1.5, R=0.0; additive @20% clean/H1/H2 +0.12/+0.04/+0.24; standalone all-in weekly Sharpe 1.08 (2013-26 0.23, dev 2013-22 -0.04); pair-window trades 2026. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU7 displacement continuation with a trailing exit (trail S ATR, no target). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 16. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|-----:|---------:|--------:|-------:|:-----------|
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 0.000 | 1348 |    0.944 |  53.749 |      2 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.000 | 0.000 | 1398 |    0.463 |  24.734 |      2 | True       |
| HO    |    1 |      0 | ALL    | mkt   | 2.000 |   15 | 1.500 | 0.000 | 1507 |    0.038 |   2.345 |      1 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.000 | 0.000 |  779 |   -0.070 |  -3.134 |      2 | True       |
| HO    |    1 |      0 | ALL    | mkt   | 2.000 |   30 | 1.000 | 0.000 |  862 |   -0.088 |  -4.105 |      2 | True       |
| HO    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 0.000 |  758 |   -0.150 |  -5.368 |      1 | True       |
| HO    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.000 | 0.000 | 1828 |   -0.150 |  -9.588 |      1 | True       |
| HO    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.000 | 0.000 | 3277 |   -0.173 | -15.064 |      1 | True       |
| HO    |    1 |      0 | ALL    | stop  | 1.500 |   30 | 1.500 | 0.000 | 1705 |   -0.252 | -14.368 |      1 | True       |
| HO    |    1 |      0 | ALL    | stop  | 1.500 |   15 | 1.500 | 0.000 | 3016 |   -0.318 | -26.018 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.94; replicate best-eligible median 0.56, p95 0.89; real beats 95% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.6e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.067 | +0.031 | +0.130 | +0.075 | +0.4 | [-0.011, +0.165] | 0.06 | NO |
| 20% | add | +0.118 | +0.040 | +0.243 | +0.132 | +7.5 | [-0.038, +0.310] | 0.06 | NO |
| 30% | add | +0.153 | +0.032 | +0.338 | +0.171 | +14.6 | [-0.080, +0.432] | 0.06 | NO |
| 50% | add | +0.185 | -0.027 | +0.469 | +0.205 | +33.6 | [-0.188, +0.609] | 0.06 | NO |
| 10% | const | +0.074 | +0.033 | +0.144 | +0.082 | -8.9 | [-0.013, +0.182] | 0.06 | NO |
| 20% | const | +0.137 | +0.038 | +0.293 | +0.154 | -11.2 | [-0.057, +0.373] | 0.06 | NO |
| 30% | const | +0.179 | -0.001 | +0.431 | +0.199 | -13.4 | [-0.147, +0.555] | 0.06 | NO |
| 50% | const | +0.139 | -0.288 | +0.540 | +0.136 | +7.6 | [-0.511, +0.801] | 0.06 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 859,917, Sharpe 0.94, maxDD 619,330, worst wk -136,082; H1: net 169,450, Sharpe 0.92, maxDD 241,307, worst wk -101,358; H2: net 447,404, Sharpe 1.60, maxDD 165,183, worst wk -71,840; all: net 1,476,771, Sharpe 1.08, maxDD 619,330, worst wk -136,082
Correlation with pair (weekly): clean +0.13, H1 +0.16, H2 -0.03, all +0.10; worst-decile weeks (n=17) corr -0.51, sleeve mean in those weeks $15,308, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.58 | 3.12 | 5.03 | -82,913 | -78,593 | 298,362 | -88,709 | 46.7 |
| clean | add 30% | 1.61 | 3.21 | 5.16 | -87,407 | -81,802 | 307,488 | -94,543 | 45.7 |
| clean | const 20% | 1.60 | 3.17 | 5.10 | -67,725 | -64,138 | 242,340 | -73,301 | 45.7 |
| clean | const 30% | 1.64 | 3.26 | 5.26 | -67,294 | -60,615 | 226,163 | -71,430 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.87 | 6.09 | 3.84 | -78,989 | -73,373 | 163,370 | -82,101 | 39.3 |
| H1 | add 30% | 2.86 | 5.96 | 3.81 | -79,678 | -77,211 | 169,198 | -84,008 | 35.7 |
| H1 | const 20% | 2.87 | 6.03 | 3.83 | -63,467 | -60,234 | 133,027 | -66,444 | 39.3 |
| H1 | const 30% | 2.83 | 5.72 | 3.77 | -60,119 | -57,502 | 123,685 | -60,522 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.54 | 5.37 | 4.03 | -73,979 | -70,300 | 215,280 | -74,207 | 40.5 |
| H2 | add 30% | 2.64 | 5.69 | 4.26 | -71,701 | -68,218 | 214,207 | -71,918 | 40.5 |
| H2 | const 20% | 2.59 | 5.54 | 4.15 | -58,272 | -55,161 | 171,794 | -58,276 | 40.5 |
| H2 | const 30% | 2.73 | 6.07 | 4.56 | -48,381 | -47,817 | 148,979 | -48,693 | 40.5 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.99 | 4.02 | 10.05 | -81,206 | -76,857 | 298,362 | -88,709 | 44.4 |
| all | add 30% | 2.03 | 4.13 | 10.23 | -85,291 | -78,881 | 307,488 | -94,543 | 43.2 |
| all | const 20% | 2.01 | 4.08 | 10.14 | -66,289 | -62,097 | 242,340 | -73,301 | 43.8 |
| all | const 30% | 2.06 | 4.18 | 10.32 | -64,516 | -57,860 | 226,163 | -71,430 | 42.6 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.118 / +0.040 / +0.243
- [PASS] 3 worst week within share: all-in worst week +7.5% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.08 vs p95 0.69 (rank 0.99)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.038, +0.310]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 67% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.058 / -0.018 / +0.225
- [PASS] 6 worst-decile corr <=+0.30: -0.51
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU7_HO); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2026 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6633 | +0.0352 | 0.81 |
| fixed | 6633 | -0.0016 | -0.04 |
| scaled | 6633 | -0.0016 | -0.04 |

Plateau neighbours (all-in 20% uplift; selected +0.132):
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '0.0'}: -0.039 (trades 4673)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '0.0'}: +0.124 (trades 2083)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.0', 'L': '15'}: +0.138 (trades 2021)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '0.0'}: -0.028 (trades 795)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '0.0'}: +0.114 (trades 1970)
- {'sym': 'HO', 'nb': '1', 'conf': '0', 'sess': 'ALL', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.0', 'L': '25'}: +0.131 (trades 2023)

Own random-entry null: 300 draws, standalone all-in Sharpe median 0.02, p95 0.69, real 1.08. Standalone Sharpe at 2x slippage 0.80.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 653 | -32 | -1.05 |
| 2014 | 596 | -22 | -0.76 |
| 2015 | 659 | 46 | 1.48 |
| 2016 | 710 | -12 | -0.38 |
| 2017 | 680 | -17 | -0.64 |
| 2018 | 680 | -15 | -0.56 |
| 2019 | 701 | -31 | -1.22 |
| 2020 | 624 | -10 | -0.37 |
| 2021 | 647 | 13 | 0.44 |
| 2022 | 683 | 70 | 2.23 |
| 2023 | 721 | -4 | -0.16 |
| 2024 | 680 | 15 | 0.56 |
| 2025 | 607 | 55 | 2.04 |
| 2026 | 449 | 36 | 1.86 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.94 | +0.12/+0.04/+0.24 |
| 2 tick entry / 2 tick exit | 0.34 | +0.00/-0.07/+0.21 |
| 3 tick entry / 3 tick exit | -0.26 | -0.11/-0.19/+0.17 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.89 | -0.17/-0.66/-0.08 |

DONE RU7_HO