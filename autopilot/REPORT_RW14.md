# REPORT RW14
**Verdict: NO** (2/7 measured gates pass). Selected cell cls=spec, mode=follow, band=0.9; additive @20% clean/H1/H2 +0.08/+0.07/-0.08; standalone all-in weekly Sharpe 0.48 (2013-26 0.06, dev 2013-22 -0.20); pair-window trades 212. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

R14 COT hedger/spec ensemble of lookbacks (52/104/156 weeks) on GC, CL, ZN, 6E, 6J (8 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 8. Top cells by clean weekly Sharpe:

| cls   | mode   |   band |   n |   sharpe |     net |   ypos | eligible   |
|:------|:-------|-------:|----:|---------:|--------:|-------:|:-----------|
| spec  | follow |  0.900 | 158 |    0.600 |  18.421 |      2 | True       |
| hedge | contra |  0.900 | 135 |    0.300 |   6.106 |      1 | True       |
| hedge | contra |  0.800 | 232 |    0.212 |   7.191 |      2 | True       |
| spec  | follow |  0.800 | 251 |    0.204 |   6.801 |      2 | True       |
| hedge | follow |  0.800 | 232 |   -0.503 | -17.087 |      0 | True       |
| spec  | contra |  0.800 | 251 |   -0.558 | -18.553 |      1 | True       |
| hedge | follow |  0.900 | 135 |   -0.560 | -11.441 |      2 | True       |
| spec  | contra |  0.900 | 158 |   -0.818 | -25.264 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.60; replicate best-eligible median 0.76, p95 1.28; real beats 30% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.96e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.049 | +0.042 | -0.040 | +0.031 | +3.6 | [-0.043, +0.101] | 0.42 | NO |
| 20% | add | +0.082 | +0.067 | -0.084 | +0.049 | +12.4 | [-0.097, +0.187] | 0.42 | NO |
| 30% | add | +0.100 | +0.076 | -0.132 | +0.054 | +21.1 | [-0.163, +0.257] | 0.42 | NO |
| 50% | add | +0.097 | +0.062 | -0.240 | +0.031 | +38.6 | [-0.320, +0.355] | 0.42 | NO |
| 10% | const | +0.053 | +0.046 | -0.044 | +0.034 | -5.9 | [-0.048, +0.112] | 0.42 | NO |
| 20% | const | +0.093 | +0.073 | -0.107 | +0.053 | -6.6 | [-0.128, +0.224] | 0.42 | NO |
| 30% | const | +0.103 | +0.071 | -0.199 | +0.044 | -7.4 | [-0.261, +0.326] | 0.42 | NO |
| 50% | const | -0.032 | -0.068 | -0.571 | -0.137 | +7.0 | [-0.737, +0.427] | 0.42 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 503,696, Sharpe 0.55, maxDD 500,196, worst wk -196,043; H1: net 284,018, Sharpe 1.61, maxDD 189,824, worst wk -72,176; H2: net -206,771, Sharpe -1.59, maxDD 255,695, worst wk -89,622; all: net 580,943, Sharpe 0.48, maxDD 500,196, worst wk -188,202
Correlation with pair (weekly): clean -0.01, H1 +0.35, H2 -0.27, all +0.01; worst-decile weeks (n=17) corr +0.05, sleeve mean in those weeks $7,326, positive share 0.35.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.54 | 3.04 | 4.67 | -79,927 | -78,094 | 306,398 | -83,693 | 45.7 |
| clean | add 30% | 1.56 | 3.12 | 4.26 | -81,104 | -78,190 | 347,908 | -87,069 | 44.8 |
| clean | const 20% | 1.55 | 3.08 | 4.45 | -64,380 | -62,513 | 261,723 | -68,305 | 44.8 |
| clean | const 30% | 1.56 | 3.17 | 3.85 | -58,607 | -55,765 | 280,894 | -63,986 | 45.7 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.89 | 6.12 | 4.04 | -84,733 | -72,828 | 161,158 | -92,723 | 42.9 |
| H1 | add 30% | 2.90 | 6.09 | 4.09 | -88,295 | -76,226 | 165,880 | -99,940 | 39.3 |
| H1 | const 20% | 2.90 | 6.11 | 4.07 | -69,211 | -59,622 | 130,815 | -77,065 | 39.3 |
| H1 | const 30% | 2.90 | 6.03 | 4.01 | -65,012 | -56,417 | 124,957 | -76,454 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.21 | 4.49 | 3.43 | -81,089 | -79,308 | 210,064 | -82,524 | 41.7 |
| H2 | add 30% | 2.16 | 4.38 | 3.39 | -81,089 | -79,369 | 206,383 | -82,524 | 41.7 |
| H2 | const 20% | 2.19 | 4.43 | 3.41 | -64,871 | -63,471 | 166,579 | -66,020 | 41.7 |
| H2 | const 30% | 2.10 | 4.23 | 3.34 | -56,762 | -55,614 | 141,156 | -57,767 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.90 | 3.80 | 9.14 | -81,628 | -79,160 | 306,398 | -92,723 | 44.6 |
| all | add 30% | 1.91 | 3.84 | 8.22 | -83,260 | -79,656 | 347,908 | -99,940 | 43.5 |
| all | const 20% | 1.91 | 3.82 | 8.65 | -65,940 | -63,527 | 261,723 | -77,065 | 43.5 |
| all | const 30% | 1.90 | 3.84 | 7.31 | -60,239 | -56,818 | 280,894 | -76,454 | 43.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.082 / +0.067 / -0.084
- [PASS] 3 worst week within share: all-in worst week +12.4% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.48 vs p95 0.81 (rank 0.85)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.097, +0.187]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.064 / +0.043 / -0.088
- [PASS] 6 worst-decile corr <=+0.30: +0.05
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section R14); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (212 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 372 | -0.0085 | -0.04 |
| fixed | 372 | -0.0454 | -0.20 |
| scaled | 372 | -0.0368 | -0.17 |

Plateau neighbours (all-in 20% uplift; selected +0.049):
- {'cls': 'spec', 'mode': 'follow', 'band': '0.925'}: +0.025 (trades 184)
- {'cls': 'spec', 'mode': 'follow', 'band': '0.875'}: +0.035 (trades 254)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.00, p95 0.81, real 0.48. Standalone Sharpe at 2x slippage 0.38.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 66 | 9 | 0.52 |
| 2017 | 49 | -9 | -0.86 |
| 2018 | 71 | -2 | -0.16 |
| 2019 | 44 | -13 | -1.44 |
| 2020 | 55 | 2 | 0.17 |
| 2021 | 46 | -2 | -0.28 |
| 2022 | 41 | -0 | -0.04 |
| 2023 | 74 | -11 | -1.00 |
| 2024 | 96 | 25 | 1.65 |
| 2025 | 76 | 20 | 1.36 |
| 2026 | 18 | -9 | -1.84 |


DONE RW14