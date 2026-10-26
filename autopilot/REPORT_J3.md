# REPORT J3
**Verdict: NO** (4/7 measured gates pass). Selected cell sig=ext, cls=hedge, mode=contra, L=52, band=0.9; additive @20% clean/H1/H2 +0.12/+0.10/+0.32; standalone all-in weekly Sharpe 0.89 (2013-26 -0.02, dev 2013-22 -0.29); pair-window trades 289. Runtime 0.1 min (+selection 0.0 min). 7-worker pool.

J3 COT sleeve on GC, CL (managed money / producer-merchant), ZN, 6E, 6J (leveraged / dealer): same construction as J1 (20 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 20 cells, eligible (>= 40 clean trades): 20. Top cells by clean weekly Sharpe:

| sig   | cls   | mode   |       L |    band |   n |   sharpe |    net |   ypos | eligible   |
|:------|:------|:-------|--------:|--------:|----:|---------:|-------:|-------:|:-----------|
| ext   | hedge | contra |  52.000 |   0.900 | 173 |    0.769 | 19.526 |      2 | True       |
| ext   | spec  | follow | 156.000 |   0.900 | 192 |    0.625 | 18.364 |      2 | True       |
| ext   | hedge | contra |  52.000 |   0.800 | 256 |    0.611 | 20.179 |      2 | True       |
| ext   | spec  | follow |  52.000 |   0.900 | 170 |    0.117 |  3.538 |      2 | True       |
| ext   | spec  | follow | 156.000 |   0.800 | 286 |    0.042 |  1.624 |      2 | True       |
| chg   | hedge | contra | nan     | nan     | 487 |    0.007 |  0.311 |      1 | True       |
| ext   | hedge | contra | 156.000 |   0.800 | 247 |   -0.007 | -0.214 |      2 | True       |
| chg   | spec  | follow | nan     | nan     | 487 |   -0.019 | -0.894 |      1 | True       |
| ext   | hedge | follow | 156.000 |   0.900 | 150 |   -0.088 | -2.414 |      1 | True       |
| ext   | hedge | contra | 156.000 |   0.900 | 150 |   -0.117 | -3.191 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.77; replicate best-eligible median 0.95, p95 1.43; real beats 33% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.59e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.069 | +0.066 | +0.190 | +0.091 | +6.0 | [-0.014, +0.197] | 0.60 | NO |
| 20% | add | +0.121 | +0.103 | +0.318 | +0.157 | +15.9 | [-0.052, +0.366] | 0.60 | NO |
| 30% | add | +0.158 | +0.110 | +0.387 | +0.196 | +27.1 | [-0.107, +0.503] | 0.60 | NO |
| 50% | add | +0.187 | +0.037 | +0.397 | +0.209 | +49.4 | [-0.271, +0.675] | 0.60 | NO |
| 10% | const | +0.075 | +0.071 | +0.207 | +0.100 | -3.7 | [-0.017, +0.218] | 0.60 | NO |
| 20% | const | +0.141 | +0.110 | +0.359 | +0.180 | -2.8 | [-0.077, +0.438] | 0.60 | NO |
| 30% | const | +0.182 | +0.075 | +0.409 | +0.213 | -1.0 | [-0.210, +0.628] | 0.60 | NO |
| 50% | const | +0.113 | -0.437 | +0.159 | +0.050 | +44.1 | [-0.729, +0.788] | 0.60 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 700,880, Sharpe 0.77, maxDD 331,439, worst wk -147,909; H1: net 34,111, Sharpe 0.16, maxDD 378,573, worst wk -107,342; H2: net 723,925, Sharpe 1.43, maxDD 472,961, worst wk -289,959; all: net 1,458,916, Sharpe 0.89, maxDD 472,961, worst wk -289,959
Correlation with pair (weekly): clean +0.00, H1 -0.22, H2 -0.00, all -0.01; worst-decile weeks (n=17) corr -0.38, sleeve mean in those weeks $33,498, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.58 | 3.16 | 5.58 | -81,919 | -77,264 | 263,638 | -86,853 | 42.9 |
| clean | add 30% | 1.62 | 3.26 | 5.50 | -86,138 | -79,726 | 280,152 | -91,624 | 43.8 |
| clean | const 20% | 1.60 | 3.22 | 5.54 | -67,172 | -62,698 | 217,409 | -71,391 | 42.9 |
| clean | const 30% | 1.64 | 3.31 | 5.38 | -65,200 | -59,143 | 212,279 | -74,562 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.93 | 6.15 | 3.75 | -73,285 | -65,630 | 160,296 | -78,749 | 39.3 |
| H1 | add 30% | 2.94 | 6.14 | 3.67 | -71,122 | -65,431 | 164,587 | -78,980 | 39.3 |
| H1 | const 20% | 2.94 | 6.15 | 3.71 | -57,763 | -52,424 | 129,953 | -63,092 | 39.3 |
| H1 | const 30% | 2.90 | 6.10 | 3.58 | -48,340 | -45,622 | 119,073 | -55,494 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.61 | 5.76 | 4.22 | -95,450 | -80,451 | 214,509 | -95,617 | 44.4 |
| H2 | add 30% | 2.68 | 6.01 | 4.59 | -103,975 | -83,874 | 213,050 | -104,852 | 41.7 |
| H2 | const 20% | 2.65 | 5.92 | 4.41 | -79,770 | -65,730 | 171,023 | -80,187 | 41.7 |
| H2 | const 30% | 2.70 | 5.98 | 5.07 | -80,455 | -66,346 | 147,823 | -81,708 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.01 | 4.13 | 11.29 | -84,606 | -78,310 | 263,638 | -95,617 | 42.9 |
| all | add 30% | 2.05 | 4.25 | 11.15 | -89,306 | -80,378 | 280,152 | -104,852 | 42.9 |
| all | const 20% | 2.04 | 4.20 | 11.22 | -69,518 | -63,421 | 217,409 | -80,187 | 42.3 |
| all | const 30% | 2.07 | 4.29 | 10.92 | -67,558 | -59,567 | 212,279 | -81,708 | 41.7 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.121 / +0.103 / +0.318
- [PASS] 3 worst week within share: all-in worst week +15.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.89 vs p95 0.76 (rank 0.97)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.052, +0.366]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.098 / +0.066 / +0.277
- [PASS] 6 worst-decile corr <=+0.30: -0.38
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section J3); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (289 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 784 | -0.0246 | -0.15 |
| fixed | 784 | -0.0489 | -0.29 |
| scaled | 784 | -0.0462 | -0.27 |

Plateau neighbours (all-in 20% uplift; selected +0.157):
- {'sig': 'ext', 'cls': 'hedge', 'mode': 'contra', 'L': '39', 'band': '0.9'}: +0.149 (trades 275)
- {'sig': 'ext', 'cls': 'hedge', 'mode': 'contra', 'L': '65', 'band': '0.9'}: +0.105 (trades 285)
- {'sig': 'ext', 'cls': 'hedge', 'mode': 'contra', 'L': '52', 'band': '0.925'}: +0.169 (trades 225)
- {'sig': 'ext', 'cls': 'hedge', 'mode': 'contra', 'L': '52', 'band': '0.875'}: +0.110 (trades 323)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.03, p95 0.76, real 0.89. Standalone Sharpe at 2x slippage 0.76.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2014 | 74 | 17 | 1.66 |
| 2015 | 86 | -26 | -1.63 |
| 2016 | 69 | 9 | 0.56 |
| 2017 | 99 | -15 | -1.27 |
| 2018 | 96 | 4 | 0.31 |
| 2019 | 69 | 11 | 0.99 |
| 2020 | 85 | -5 | -0.36 |
| 2021 | 103 | -21 | -1.01 |
| 2022 | 103 | -11 | -0.71 |
| 2023 | 52 | -9 | -0.89 |
| 2024 | 114 | 10 | 0.71 |
| 2025 | 68 | 13 | 1.13 |
| 2026 | 94 | 22 | 1.37 |


DONE J3