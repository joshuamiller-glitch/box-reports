# REPORT RU6_RB
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=0, sess=RTH, ent=stop, k=2.0, tf=30, S=1.5, R=1.0; additive @20% clean/H1/H2 +0.17/-0.22/+0.19; standalone all-in weekly Sharpe 0.78 (2013-26 0.30, dev 2013-22 0.14); pair-window trades 579. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RU6 session split of the RU2 selected cell (ALL / RTH / non-RTH by placement time). 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 3 cells, eligible (>= 40 clean trades): 3. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R |   n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|----:|---------:|--------:|-------:|:-----------|
| RB    |    1 |      0 | RTH    | stop  | 2.000 |   30 | 1.500 | 1.000 | 408 |    1.024 |  28.144 |      3 | True       |
| RB    |    1 |      0 | ALL    | stop  | 2.000 |   30 | 1.500 | 1.000 | 768 |    0.389 |  14.669 |      3 | True       |
| RB    |    1 |      0 | NRTH   | stop  | 2.000 |   30 | 1.500 | 1.000 | 363 |   -0.557 | -12.504 |      1 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.02; replicate best-eligible median 0.68, p95 1.47; real beats 85% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.313e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.093 | -0.089 | +0.100 | +0.067 | +4.0 | [-0.020, +0.163] | 0.50 | NO |
| 20% | add | +0.169 | -0.216 | +0.191 | +0.116 | +11.1 | [-0.057, +0.305] | 0.50 | NO |
| 30% | add | +0.228 | -0.371 | +0.272 | +0.147 | +19.4 | [-0.111, +0.421] | 0.50 | NO |
| 50% | add | +0.296 | -0.720 | +0.400 | +0.159 | +35.9 | [-0.250, +0.592] | 0.50 | NO |
| 10% | const | +0.102 | -0.102 | +0.111 | +0.074 | -6.0 | [-0.023, +0.180] | 0.50 | NO |
| 20% | const | +0.200 | -0.290 | +0.233 | +0.134 | -7.8 | [-0.082, +0.367] | 0.50 | NO |
| 30% | const | +0.278 | -0.592 | +0.359 | +0.161 | -9.0 | [-0.196, +0.539] | 0.50 | NO |
| 50% | const | +0.287 | -1.499 | +0.543 | +0.026 | -3.3 | [-0.654, +0.743] | 0.50 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 932,528, Sharpe 1.02, maxDD 445,142, worst wk -137,196; H1: net -153,514, Sharpe -0.59, maxDD 319,345, worst wk -135,881; H2: net 316,155, Sharpe 1.50, maxDD 226,647, worst wk -67,446; all: net 1,095,169, Sharpe 0.78, maxDD 445,142, worst wk -137,196
Correlation with pair (weekly): clean +0.01, H1 -0.01, H2 -0.08, all -0.01; worst-decile weeks (n=17) corr +0.18, sleeve mean in those weeks $7,161, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.63 | 3.17 | 5.39 | -85,340 | -80,957 | 281,151 | -91,707 | 40.0 |
| clean | add 30% | 1.69 | 3.29 | 5.07 | -89,010 | -83,939 | 317,447 | -98,519 | 42.9 |
| clean | const 20% | 1.66 | 3.24 | 5.22 | -69,734 | -65,831 | 239,439 | -76,090 | 40.0 |
| clean | const 30% | 1.74 | 3.37 | 4.75 | -67,087 | -62,390 | 254,879 | -75,094 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.61 | 5.46 | 2.99 | -76,138 | -69,188 | 188,624 | -81,903 | 35.7 |
| H1 | add 30% | 2.46 | 5.08 | 2.65 | -75,402 | -70,933 | 207,079 | -83,711 | 39.3 |
| H1 | const 20% | 2.54 | 5.28 | 2.81 | -60,616 | -56,049 | 158,281 | -66,246 | 39.3 |
| H1 | const 30% | 2.24 | 4.56 | 2.29 | -54,830 | -51,225 | 161,565 | -60,225 | 39.3 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.49 | 5.12 | 4.35 | -85,649 | -78,185 | 193,531 | -89,202 | 43.2 |
| H2 | add 30% | 2.57 | 5.29 | 4.52 | -87,930 | -80,314 | 193,077 | -92,540 | 40.5 |
| H2 | const 20% | 2.53 | 5.21 | 4.49 | -69,432 | -63,345 | 152,756 | -72,697 | 43.2 |
| H2 | const 30% | 2.66 | 5.43 | 4.60 | -63,603 | -58,258 | 138,991 | -67,783 | 35.1 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.97 | 3.92 | 10.39 | -85,027 | -79,820 | 281,151 | -91,707 | 40.2 |
| all | add 30% | 2.01 | 3.98 | 9.55 | -88,181 | -82,255 | 317,447 | -98,519 | 42.0 |
| all | const 20% | 1.99 | 3.96 | 9.94 | -69,279 | -64,805 | 239,439 | -76,090 | 40.8 |
| all | const 30% | 2.02 | 3.98 | 8.71 | -65,551 | -60,756 | 254,879 | -75,094 | 40.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.169 / -0.216 / +0.191
- [PASS] 3 worst week within share: all-in worst week +11.1% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.78 vs p95 0.89 (rank 0.93)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.057, +0.305]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 38% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.157 / -0.232 / +0.188
- [PASS] 6 worst-decile corr <=+0.30: +0.18
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU6_RB); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (579 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2012 | +0.0233 | 0.37 |
| fixed | 2012 | +0.0091 | 0.14 |
| scaled | 2012 | +0.0091 | 0.14 |

Plateau neighbours (all-in 20% uplift; selected +0.116):
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '1.5', 'tf': '30', 'S': '1.5', 'R': '1.0'}: +0.007 (trades 1195)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.125', 'R': '1.0'}: +0.100 (trades 589)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '0.75'}: +0.032 (trades 587)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '1.0', 'L': '15'}: +0.116 (trades 579)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.5', 'tf': '30', 'S': '1.5', 'R': '1.0'}: +0.045 (trades 223)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.875', 'R': '1.0'}: +0.024 (trades 556)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '1.25'}: +0.078 (trades 562)
- {'sym': 'RB', 'nb': '1', 'conf': '0', 'sess': 'RTH', 'ent': 'stop', 'k': '2.0', 'tf': '30', 'S': '1.5', 'R': '1.0', 'L': '25'}: +0.116 (trades 579)

Own random-entry null: 300 draws, standalone all-in Sharpe median 0.06, p95 0.89, real 0.78. Standalone Sharpe at 2x slippage 0.72.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 209 | 16 | 1.13 |
| 2014 | 223 | -1 | -0.10 |
| 2015 | 214 | -3 | -0.23 |
| 2016 | 211 | -9 | -0.69 |
| 2017 | 191 | 17 | 1.28 |
| 2018 | 208 | 16 | 1.53 |
| 2019 | 200 | -6 | -0.52 |
| 2020 | 173 | -13 | -1.08 |
| 2021 | 200 | -1 | -0.05 |
| 2022 | 183 | 2 | 0.15 |
| 2023 | 241 | 8 | 0.45 |
| 2024 | 212 | 7 | 0.64 |
| 2025 | 171 | 13 | 1.00 |
| 2026 | 92 | 7 | 0.88 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 1.02 | +0.17/-0.22/+0.19 |
| 2 tick entry / 2 tick exit | 0.92 | +0.15/-0.41/+0.19 |
| 3 tick entry / 3 tick exit | 0.69 | +0.11/-0.43/+0.18 |
| retrace-limit DISP (b=2.0, tf30, f=0.5, RZ geometry) | 0.23 | +0.01/-0.05/-0.34 |

DONE RU6_RB