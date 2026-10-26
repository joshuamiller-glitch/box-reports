# REPORT L6
**Verdict: NO** (1/7 measured gates pass). Selected cell sp=HO-CL, sig=mr1.5, N=5; additive @20% clean/H1/H2 +0.16/-0.25/-0.49; standalone all-in weekly Sharpe 0.01 (2013-26 -0.19, dev 2013-22 -0.27); pair-window trades 88 (SMALL-SAMPLE). Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

L6 commodity spread sleeve (GC-SI, HO-CL, RB-CL, ZS-ZC, ZW-ZC, LE-HE; MR or trend; 36 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 36 cells, eligible (>= 40 clean trades): 18. Top cells by clean weekly Sharpe:

| sp    | sig   |   N |   n |   sharpe |    net |   ypos | eligible   |
|:------|:------|----:|----:|---------:|-------:|-------:|:-----------|
| HO-CL | mr1.5 |   5 |  53 |    0.945 | 11.950 |      3 | True       |
| HO-CL | mr2.0 |   5 |  39 |    0.751 |  7.428 |      3 | False      |
| GC-SI | mr1.5 |   5 |  60 |    0.715 | 11.113 |      3 | True       |
| RB-CL | mr2.0 |  10 |  28 |    0.606 |  4.899 |      1 | False      |
| HO-CL | mr2.0 |  10 |  27 |    0.591 |  6.967 |      3 | False      |
| RB-CL | mr2.0 |   5 |  36 |    0.588 |  4.057 |      1 | False      |
| LE-HE | mr2.0 |  10 |  24 |    0.531 | 10.929 |      2 | False      |
| ZW-ZC | trend |  10 |  51 |    0.520 |  9.962 |      2 | True       |
| GC-SI | trend |  10 |  52 |    0.405 |  7.135 |      1 | True       |
| ZS-ZC | mr2.0 |  10 |  24 |    0.393 |  5.067 |      2 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.95; replicate best-eligible median 0.66, p95 1.22; real beats 83% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=7.178e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.089 | -0.117 | -0.198 | +0.000 | +7.6 | [-0.139, +0.129] | 0.83 | NO |
| 20% | add | +0.162 | -0.249 | -0.493 | -0.040 | +20.7 | [-0.328, +0.217] | 0.83 | NO |
| 30% | add | +0.218 | -0.391 | -0.811 | -0.113 | +49.7 | [-0.549, +0.269] | 0.83 | NO |
| 50% | add | +0.279 | -0.687 | -1.348 | -0.313 | +200.4 | [-0.980, +0.297] | 0.83 | NO |
| 10% | const | +0.098 | -0.131 | -0.227 | -0.002 | -1.8 | [-0.158, +0.141] | 0.83 | NO |
| 20% | const | +0.192 | -0.319 | -0.653 | -0.073 | +1.7 | [-0.439, +0.247] | 0.83 | NO |
| 30% | const | +0.265 | -0.581 | -1.177 | -0.237 | +72.6 | [-0.831, +0.301] | 0.83 | NO |
| 50% | const | +0.227 | -1.357 | -2.048 | -0.786 | +238.5 | [-1.769, +0.152] | 0.83 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 708,960, Sharpe 0.78, maxDD 294,355, worst wk -177,744; H1: net -148,918, Sharpe -0.79, maxDD 460,228, worst wk -128,647; H2: net -544,037, Sharpe -0.65, maxDD 1,267,907, worst wk -621,720; all: net 16,005, Sharpe 0.01, maxDD 1,608,086, worst wk -621,720
Correlation with pair (weekly): clean -0.12, H1 +0.15, H2 -0.06, all -0.07; worst-decile weeks (n=17) corr -0.01, sleeve mean in those weeks $9,793, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.62 | 3.10 | 5.05 | -84,946 | -81,022 | 291,227 | -99,584 | 41.9 |
| clean | add 30% | 1.68 | 3.20 | 5.20 | -88,395 | -82,762 | 296,786 | -110,334 | 42.9 |
| clean | const 20% | 1.65 | 3.16 | 5.13 | -69,336 | -65,514 | 235,205 | -83,967 | 42.9 |
| clean | const 30% | 1.72 | 3.29 | 5.38 | -64,981 | -59,499 | 212,753 | -86,909 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.58 | 5.30 | 3.91 | -90,853 | -74,505 | 144,389 | -95,335 | 42.9 |
| H1 | add 30% | 2.44 | 4.88 | 3.55 | -97,474 | -78,743 | 154,833 | -103,859 | 46.4 |
| H1 | const 20% | 2.51 | 5.09 | 3.72 | -75,331 | -61,299 | 119,689 | -79,677 | 42.9 |
| H1 | const 30% | 2.25 | 4.36 | 3.15 | -74,191 | -58,934 | 117,783 | -80,373 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 1.80 | 4.15 | 2.94 | -75,319 | -70,305 | 221,836 | -79,653 | 50.0 |
| H2 | add 30% | 1.48 | 3.21 | 2.19 | -101,609 | -85,334 | 272,970 | -123,564 | 58.3 |
| H2 | const 20% | 1.64 | 3.70 | 2.69 | -68,852 | -61,486 | 185,779 | -73,982 | 58.3 |
| H2 | const 30% | 1.12 | 2.11 | 1.36 | -109,501 | -79,226 | 271,665 | -142,450 | 52.8 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.82 | 3.64 | 9.23 | -85,670 | -80,329 | 291,227 | -99,584 | 43.5 |
| all | add 30% | 1.74 | 3.45 | 8.12 | -94,320 | -85,401 | 331,100 | -123,564 | 46.4 |
| all | const 20% | 1.78 | 3.56 | 9.15 | -71,185 | -65,928 | 235,205 | -83,967 | 45.8 |
| all | const 30% | 1.62 | 3.06 | 5.61 | -77,798 | -66,158 | 335,662 | -142,450 | 44.6 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.162 / -0.249 / -0.493
- [FAIL] 3 worst week within share: all-in worst week +20.7% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.01 vs p95 0.62 (rank 0.66)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.328, +0.217]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.151 / -0.263 / -0.502
- [PASS] 6 worst-decile corr <=+0.30: -0.01
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section L6); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (88 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 268 | -0.0388 | -0.19 |
| fixed | 268 | -0.0553 | -0.27 |
| scaled | 268 | -0.0553 | -0.27 |

Plateau neighbours (all-in 20% uplift; selected -0.040):
- {'sp': 'HO-CL', 'sig': 'mr1.12', 'N': '5'}: -0.148 (trades 121)
- {'sp': 'HO-CL', 'sig': 'mr1.88', 'N': '5'}: -0.132 (trades 66)
- {'sp': 'HO-CL', 'sig': 'mr1.5', 'N': '4'}: -0.020 (trades 104)
- {'sp': 'HO-CL', 'sig': 'mr1.5', 'N': '6'}: -0.104 (trades 76)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.16, p95 0.62, real 0.01. Standalone Sharpe at 2x slippage -0.03.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 26 | -2 | -0.46 |
| 2014 | 28 | -3 | -0.74 |
| 2015 | 26 | -2 | -0.50 |
| 2016 | 23 | 1 | 0.72 |
| 2017 | 30 | 0 | 0.00 |
| 2018 | 27 | -6 | -1.84 |
| 2019 | 32 | -4 | -1.48 |
| 2020 | 22 | -5 | -1.83 |
| 2021 | 27 | -1 | -0.20 |
| 2022 | 27 | 7 | 0.50 |
| 2023 | 28 | 6 | 0.68 |
| 2024 | 24 | 0 | 0.03 |
| 2025 | 30 | -0 | -0.08 |
| 2026 | 23 | -8 | -0.64 |


DONE L6