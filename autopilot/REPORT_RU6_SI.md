# REPORT RU6_SI
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=RTH, ent=stop, k=2.0, tf=15, S=1.5, R=1.0; additive @20% clean/H1/H2 +0.31/-0.41/+0.03; standalone all-in weekly Sharpe 1.09 (2013-26 0.43, dev 2013-22 0.12); pair-window trades 477. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU6 session split of the RU2 selected cell (ALL / RTH / non-RTH by placement time). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 40 clean trades): 3. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |   n |   sharpe |    net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|----:|---------:|-------:|-------:|:-----------|
| SI    |    1 |      0 | RTH    | stop  | 2.000 |   15 | 1.500 | 1.000 | 305 |    1.927 | 40.380 |      3 | True       |
| SI    |    1 |      0 | ALL    | stop  | 2.000 |   15 | 1.500 | 1.000 | 998 |    1.067 | 43.844 |      2 | True       |
| SI    |    1 |      0 | NRTH   | stop  | 2.000 |   15 | 1.500 | 1.000 | 718 |    0.184 |  6.358 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.93; replicate best-eligible median 0.61, p95 1.12; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.348e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.168 | -0.187 | +0.026 | +0.083 | +8.3 | [-0.008, +0.176] | 0.11 | NO |
| 20% | add | +0.314 | -0.409 | +0.034 | +0.145 | +23.1 | [-0.035, +0.329] | 0.11 | NO |
| 30% | add | +0.439 | -0.658 | +0.025 | +0.185 | +37.9 | [-0.081, +0.458] | 0.11 | NO |
| 50% | add | +0.623 | -1.188 | -0.024 | +0.216 | +67.5 | [-0.200, +0.643] | 0.11 | NO |
| 10% | const | +0.185 | -0.210 | +0.028 | +0.091 | -1.1 | [-0.010, +0.195] | 0.11 | NO |
| 20% | const | +0.379 | -0.531 | +0.031 | +0.167 | +4.4 | [-0.055, +0.396] | 0.11 | NO |
| 30% | const | +0.566 | -0.998 | -0.002 | +0.212 | +9.8 | [-0.151, +0.587] | 0.11 | NO |
| 50% | const | +0.820 | -2.320 | -0.225 | +0.130 | +20.7 | [-0.568, +0.824] | 0.11 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,755,550, Sharpe 1.93, maxDD 274,437, worst wk -137,398; H1: net -443,972, Sharpe -1.86, maxDD 453,864, worst wk -90,949; H2: net 300,587, Sharpe 0.93, maxDD 327,626, worst wk -132,112; all: net 1,612,165, Sharpe 1.09, maxDD 586,987, worst wk -137,398
Correlation with pair (weekly): clean +0.10, H1 -0.14, H2 +0.24, all +0.09; worst-decile weeks (n=17) corr -0.14, sleeve mean in those weeks $18,561, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.77 | 3.65 | 6.40 | -82,331 | -76,484 | 262,477 | -91,209 | 44.8 |
| clean | add 30% | 1.90 | 4.03 | 7.21 | -85,006 | -75,984 | 257,555 | -98,309 | 43.8 |
| clean | const 20% | 1.84 | 3.85 | 6.80 | -66,935 | -60,985 | 208,013 | -75,807 | 44.8 |
| clean | const 30% | 2.03 | 4.43 | 7.71 | -61,911 | -53,244 | 189,044 | -75,206 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.42 | 4.87 | 3.45 | -77,644 | -66,556 | 146,505 | -78,287 | 46.4 |
| H1 | add 30% | 2.17 | 4.23 | 3.05 | -77,661 | -69,288 | 150,941 | -78,287 | 42.9 |
| H1 | const 20% | 2.30 | 4.55 | 3.25 | -62,122 | -54,263 | 118,978 | -62,630 | 46.4 |
| H1 | const 30% | 1.83 | 3.45 | 2.52 | -54,378 | -51,127 | 112,024 | -54,801 | 42.9 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.33 | 5.01 | 3.70 | -92,186 | -79,546 | 226,338 | -101,575 | 43.2 |
| H2 | add 30% | 2.32 | 5.08 | 3.76 | -98,361 | -82,645 | 230,795 | -113,789 | 45.9 |
| H2 | const 20% | 2.33 | 5.05 | 3.73 | -76,219 | -64,877 | 182,853 | -86,146 | 43.2 |
| H2 | const 30% | 2.30 | 5.07 | 3.84 | -74,410 | -60,641 | 165,567 | -90,645 | 48.6 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 2.00 | 4.14 | 11.52 | -84,095 | -77,834 | 262,477 | -101,575 | 45.0 |
| all | add 30% | 2.04 | 4.31 | 12.37 | -87,236 | -78,084 | 257,555 | -113,789 | 44.4 |
| all | const 20% | 2.03 | 4.23 | 11.94 | -68,533 | -62,325 | 208,013 | -86,146 | 45.0 |
| all | const 30% | 2.07 | 4.44 | 12.56 | -63,899 | -55,416 | 189,044 | -90,645 | 44.4 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.314 / -0.409 / +0.034
- [FAIL] 3 worst week within share: all-in worst week +23.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.09 vs p95 0.64 (rank 0.98)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.035, +0.329]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.269 / -0.439 / +0.021
- [PASS] 6 worst-decile corr <=+0.30: -0.14
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU6_SI); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (477 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 721 | +0.0382 | 0.42 |
| fixed | 721 | +0.0115 | 0.12 |
| scaled | 721 | +0.0115 | 0.12 |

Plateau neighbours (all-in 20% uplift; selected +0.145):
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '15', 'S': '1.5', 'R': '1.0'}: -0.103 (trades 1036)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.125', 'R': '1.0'}: +0.096 (trades 478)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '0.75'}: +0.140 (trades 486)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.0', 'L': '15'}: +0.148 (trades 475)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.5', 'tf': '15', 'S': '1.5', 'R': '1.0'}: +0.024 (trades 184)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.875', 'R': '1.0'}: +0.126 (trades 462)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.25'}: +0.054 (trades 463)
- {'sym': 'SI', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '15', 'S': '1.5', 'R': '1.0', 'L': '25'}: +0.139 (trades 481)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.03, p95 0.64, real 1.09. Standalone Sharpe at 2x slippage 0.90.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 75 | 4 | 0.59 |
| 2014 | 56 | 7 | 1.30 |
| 2015 | 85 | -18 | -2.85 |
| 2016 | 85 | 5 | 0.77 |
| 2017 | 60 | -5 | -0.86 |
| 2018 | 30 | -0 | -0.08 |
| 2019 | 40 | -0 | -0.04 |
| 2020 | 90 | 2 | 0.30 |
| 2021 | 109 | 7 | 0.72 |
| 2022 | 91 | 7 | 0.89 |
| 2023 | 150 | 6 | 0.48 |
| 2024 | 162 | 26 | 2.48 |
| 2025 | 138 | 3 | 0.27 |
| 2026 | 110 | 4 | 0.47 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.93 | +0.31/-0.41/+0.03 |
| 2 tick entry / 2 tick exit | 1.35 | +0.21/-0.47/+0.00 |
| 3 tick entry / 3 tick exit | 0.74 | +0.09/-0.50/-0.08 |
| retrace-limit DISP (b=2.0, tf15, f=0.5, RZ geometry) | -0.20 | -0.07/+0.08/+0.02 |

DONE RU6_SI