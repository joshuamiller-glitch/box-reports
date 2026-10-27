# REPORT RU10_NGxCL
**Verdict: NO** (2/7 measured gates pass). Selected cell nb=1, conf=1, sess=ALL, ent=mkt, k=2.0, tf=30, S=1.0, R=2.0, partner=CL; additive @20% clean/H1/H2 +0.13/+0.01/-0.13; standalone all-in weekly Sharpe 0.27 (2013-26 -0.46, dev 2013-22 -0.62); pair-window trades 677. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RU10 displacement continuation confirmed by a same-direction displacement (range >= 1 ATR) in the partner market. 1-min sim, $4.36/contract, 1 tick slippage. Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| sym   |   nb |   conf | sess   | ent   |     k |   tf |     S |     R | partner   |    n |   sharpe |     net |   ypos | eligible   |
|:------|-----:|-------:|:-------|:------|------:|-----:|------:|------:|:----------|-----:|---------:|--------:|-------:|:-----------|
| NG    |    1 |      1 | ALL    | mkt   | 2.000 |   30 | 1.000 | 2.000 | CL        |  430 |    0.595 |  22.674 |      2 | True       |
| NG    |    1 |      1 | ALL    | stop  | 2.000 |   30 | 1.000 | 2.000 | CL        |  398 |    0.252 |   8.761 |      2 | True       |
| NG    |    1 |      1 | ALL    | stop  | 1.500 |   30 | 1.000 | 2.000 | CL        |  709 |   -0.340 | -14.690 |      1 | True       |
| NG    |    1 |      1 | ALL    | stop  | 2.000 |   15 | 1.000 | 2.000 | CL        |  514 |   -0.736 | -27.453 |      0 | True       |
| NG    |    1 |      1 | ALL    | mkt   | 2.000 |   15 | 1.000 | 2.000 | CL        |  565 |   -0.738 | -27.824 |      0 | True       |
| NG    |    1 |      1 | ALL    | mkt   | 1.500 |   30 | 1.000 | 2.000 | CL        |  782 |   -0.933 | -45.511 |      2 | True       |
| NG    |    1 |      1 | ALL    | stop  | 1.500 |   15 | 1.000 | 2.000 | CL        |  916 |   -1.216 | -62.821 |      1 | True       |
| NG    |    1 |      1 | ALL    | mkt   | 1.500 |   15 | 1.000 | 2.000 | CL        | 1011 |   -1.511 | -84.870 |      0 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.59; replicate best-eligible median 0.42, p95 1.18; real beats 75% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.39e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.074 | +0.024 | -0.058 | +0.036 | +8.9 | [-0.051, +0.129] | 0.94 | NO |
| 20% | add | +0.133 | +0.011 | -0.127 | +0.054 | +21.1 | [-0.121, +0.242] | 0.94 | NO |
| 30% | add | +0.176 | -0.041 | -0.202 | +0.054 | +33.2 | [-0.205, +0.333] | 0.94 | NO |
| 50% | add | +0.211 | -0.250 | -0.367 | +0.007 | +57.5 | [-0.411, +0.444] | 0.94 | NO |
| 10% | const | +0.081 | +0.024 | -0.065 | +0.039 | -0.8 | [-0.059, +0.143] | 0.94 | NO |
| 20% | const | +0.157 | -0.010 | -0.164 | +0.057 | +1.7 | [-0.161, +0.289] | 0.94 | NO |
| 30% | const | +0.206 | -0.162 | -0.307 | +0.030 | +4.2 | [-0.332, +0.419] | 0.94 | NO |
| 50% | const | +0.111 | -1.002 | -0.773 | -0.256 | +9.1 | [-0.965, +0.470] | 0.94 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 541,811, Sharpe 0.59, maxDD 738,029, worst wk -125,198; H1: net -100,156, Sharpe -0.42, maxDD 267,798, worst wk -124,620; H2: net -62,176, Sharpe -0.23, maxDD 425,490, worst wk -122,359; all: net 379,479, Sharpe 0.27, maxDD 738,029, worst wk -125,198
Correlation with pair (weekly): clean -0.14, H1 -0.28, H2 +0.19, all -0.10; worst-decile weeks (n=17) corr +0.21, sleeve mean in those weeks $13,708, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.59 | 3.17 | 6.51 | -83,466 | -77,347 | 220,781 | -99,899 | 43.8 |
| clean | add 30% | 1.64 | 3.30 | 6.26 | -86,596 | -77,579 | 238,415 | -109,915 | 44.8 |
| clean | const 20% | 1.62 | 3.24 | 6.38 | -68,025 | -61,828 | 183,678 | -83,926 | 44.8 |
| clean | const 30% | 1.67 | 3.39 | 5.98 | -63,858 | -55,000 | 182,762 | -85,955 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.84 | 5.72 | 3.64 | -69,527 | -66,121 | 157,659 | -72,260 | 28.6 |
| H1 | add 30% | 2.79 | 5.39 | 3.51 | -74,590 | -66,784 | 160,632 | -79,256 | 28.6 |
| H1 | const 20% | 2.82 | 5.56 | 3.57 | -57,647 | -52,982 | 127,317 | -58,420 | 28.6 |
| H1 | const 30% | 2.67 | 4.90 | 3.23 | -56,770 | -51,403 | 119,340 | -66,695 | 32.1 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.17 | 4.21 | 3.49 | -90,687 | -85,023 | 219,415 | -94,838 | 40.5 |
| H2 | add 30% | 2.10 | 3.98 | 3.45 | -98,348 | -90,861 | 220,409 | -103,684 | 40.5 |
| H2 | const 20% | 2.13 | 4.10 | 3.47 | -74,720 | -70,354 | 175,930 | -79,409 | 43.2 |
| H2 | const 30% | 1.99 | 3.69 | 3.25 | -78,330 | -68,857 | 161,892 | -80,539 | 37.8 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 1.91 | 3.77 | 12.58 | -85,297 | -78,757 | 220,781 | -99,899 | 40.8 |
| all | add 30% | 1.91 | 3.76 | 11.81 | -90,690 | -80,954 | 238,415 | -109,915 | 41.4 |
| all | const 20% | 1.92 | 3.77 | 12.18 | -70,149 | -63,778 | 183,678 | -83,926 | 42.0 |
| all | const 30% | 1.89 | 3.67 | 10.97 | -69,227 | -59,402 | 182,762 | -85,955 | 40.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.133 / +0.011 / -0.127
- [FAIL] 3 worst week within share: all-in worst week +21.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.27 vs p95 0.10 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.121, +0.242]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.078 / -0.034 / -0.180
- [PASS] 6 worst-decile corr <=+0.30: +0.21
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU10_NGxCL); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (677 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1650 | -0.0193 | -0.21 |
| fixed | 1650 | -0.0581 | -0.62 |
| scaled | 1650 | -0.0581 | -0.62 |

Plateau neighbours (all-in 20% uplift; selected +0.054):
- {'sym': 'NG', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '1.5', 'tf': '30', 'S': '1.0', 'R': '2.0', 'partner': 'CL'}: -0.264 (trades 1262)
- {'sym': 'NG', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '0.75', 'R': '2.0', 'partner': 'CL'}: -0.018 (trades 677)
- {'sym': 'NG', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.0', 'R': '1.5', 'partner': 'CL'}: +0.085 (trades 698)
- {'sym': 'NG', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.5', 'tf': '30', 'S': '1.0', 'R': '2.0', 'partner': 'CL'}: +0.068 (trades 315)
- {'sym': 'NG', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.25', 'R': '2.0', 'partner': 'CL'}: +0.024 (trades 673)
- {'sym': 'NG', 'nb': '1', 'conf': '1', 'sess': 'ALL', 'ent': 'mkt', 'k': '2.0', 'tf': '30', 'S': '1.0', 'R': '2.5', 'partner': 'CL'}: +0.043 (trades 664)

Own random-entry null: 300 draws, standalone all-in Sharpe median -0.74, p95 0.10, real 0.27. Standalone Sharpe at 2x slippage -0.01.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 194 | 8 | 0.41 |
| 2014 | 184 | -21 | -1.48 |
| 2015 | 168 | -2 | -0.11 |
| 2016 | 169 | -10 | -0.81 |
| 2017 | 138 | -22 | -1.99 |
| 2018 | 105 | -4 | -0.42 |
| 2019 | 128 | -20 | -1.77 |
| 2020 | 182 | -17 | -1.01 |
| 2021 | 178 | 25 | 1.39 |
| 2022 | 204 | -32 | -1.56 |
| 2023 | 225 | -4 | -0.18 |
| 2024 | 213 | -22 | -1.46 |
| 2025 | 207 | 21 | 0.97 |
| 2026 | 162 | -3 | -0.23 |


## Fill bounds (entry slippage and exit slippage in ticks) and retrace-limit comparison

| scenario | clean weekly Sharpe | additive-20% uplift clean/H1/H2 |
|---|---|---|
| 1 tick entry / 1 tick exit | 0.59 | +0.13/+0.01/-0.13 |
| 2 tick entry / 2 tick exit | 0.03 | +0.02/-0.18/-0.24 |
| 3 tick entry / 3 tick exit | -0.53 | -0.09/-0.28/-0.36 |
| retrace-limit DISP (b=2.0, tf30, f=0.5, RZ geometry) | 0.04 | +0.01/-0.20/+0.07 |

DONE RU10_NGxCL