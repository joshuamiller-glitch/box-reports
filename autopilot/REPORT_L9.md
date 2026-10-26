# REPORT L9
**Verdict: NO** (3/7 measured gates pass). Selected cell leg=rth, delta=0.08, mode=longonly; additive @20% clean/H1/H2 +0.20/+0.10/-0.20; standalone all-in weekly Sharpe 0.67 (2013-26 -0.01, dev 2013-22 -0.23); pair-window trades 267. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

L9 K4 signal decomposed into overnight (16:17 to 09:30) and RTH (09:31 to 16:16) legs (8 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 100 clean trades): 8. Top cells by clean weekly Sharpe:

| leg       |   delta | mode      |   n |   sharpe |    net |   ypos | eligible   |
|:----------|--------:|:----------|----:|---------:|-------:|-------:|:-----------|
| rth       |   0.080 | longonly  | 162 |    1.140 | 25.972 |      2 | True       |
| rth       |   0.080 | longshort | 169 |    0.896 | 21.264 |      1 | True       |
| rth       |   0.040 | longonly  | 899 |    0.752 | 32.674 |      1 | True       |
| rth       |   0.040 | longshort | 956 |    0.633 | 29.085 |      1 | True       |
| overnight |   0.080 | longonly  | 162 |    0.537 |  9.447 |      1 | True       |
| overnight |   0.080 | longshort | 169 |    0.475 |  8.481 |      1 | True       |
| overnight |   0.040 | longshort | 956 |    0.277 |  9.815 |      1 | True       |
| overnight |   0.040 | longonly  | 899 |    0.160 |  5.714 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.14; replicate best-eligible median 0.88, p95 1.50; real beats 77% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.882e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.107 | +0.056 | -0.098 | +0.052 | +1.0 | [-0.015, +0.128] | 0.52 | NO |
| 20% | add | +0.197 | +0.104 | -0.200 | +0.089 | +5.4 | [-0.044, +0.232] | 0.52 | NO |
| 30% | add | +0.268 | +0.142 | -0.302 | +0.111 | +19.1 | [-0.085, +0.319] | 0.52 | NO |
| 50% | add | +0.359 | +0.185 | -0.508 | +0.115 | +49.8 | [-0.200, +0.450] | 0.52 | NO |
| 10% | const | +0.118 | +0.062 | -0.110 | +0.057 | -8.7 | [-0.018, +0.141] | 0.52 | NO |
| 20% | const | +0.235 | +0.124 | -0.251 | +0.102 | -10.9 | [-0.063, +0.278] | 0.52 | NO |
| 30% | const | +0.334 | +0.174 | -0.435 | +0.119 | -2.8 | [-0.157, +0.411] | 0.52 | NO |
| 50% | const | +0.378 | +0.110 | -0.984 | -0.015 | +21.6 | [-0.572, +0.563] | 0.52 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,008,221, Sharpe 1.11, maxDD 298,663, worst wk -231,530; H1: net 43,781, Sharpe 0.35, maxDD 157,209, worst wk -118,891; H2: net -202,556, Sharpe -1.04, maxDD 350,521, worst wk -126,888; all: net 849,445, Sharpe 0.67, maxDD 350,521, worst wk -231,530
Correlation with pair (weekly): clean -0.02, H1 -0.24, H2 +0.26, all -0.00; worst-decile weeks (n=17) corr +0.12, sleeve mean in those weeks $14,885, positive share 0.29.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.66 | 3.33 | 6.41 | -78,803 | -77,684 | 238,863 | -82,323 | 42.9 |
| clean | add 30% | 1.73 | 3.57 | 7.03 | -79,240 | -77,682 | 232,104 | -84,956 | 42.9 |
| clean | const 20% | 1.69 | 3.45 | 6.86 | -63,217 | -62,133 | 184,399 | -66,912 | 42.9 |
| clean | const 30% | 1.79 | 3.82 | 6.70 | -55,863 | -54,404 | 183,984 | -61,838 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.93 | 6.74 | 3.74 | -68,914 | -60,233 | 161,046 | -70,419 | 39.3 |
| H1 | add 30% | 2.97 | 7.05 | 3.54 | -64,567 | -57,334 | 171,605 | -67,163 | 39.3 |
| H1 | const 20% | 2.95 | 6.90 | 3.64 | -53,392 | -47,027 | 133,060 | -55,033 | 39.3 |
| H1 | const 30% | 3.00 | 7.40 | 3.31 | -41,284 | -37,525 | 129,627 | -44,083 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.10 | 4.13 | 3.31 | -86,301 | -83,136 | 217,425 | -87,020 | 44.4 |
| H2 | add 30% | 1.99 | 3.85 | 3.22 | -94,487 | -87,229 | 217,425 | -98,271 | 44.4 |
| H2 | const 20% | 2.04 | 3.99 | 3.27 | -72,315 | -68,146 | 173,940 | -73,541 | 44.4 |
| H2 | const 30% | 1.86 | 3.50 | 2.93 | -73,508 | -64,744 | 160,903 | -80,210 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.94 | 3.93 | 11.95 | -80,899 | -78,674 | 238,863 | -87,020 | 42.9 |
| all | add 30% | 1.97 | 4.02 | 12.67 | -83,011 | -79,526 | 232,104 | -98,271 | 42.9 |
| all | const 20% | 1.96 | 3.98 | 12.57 | -65,564 | -63,273 | 184,399 | -73,541 | 42.9 |
| all | const 30% | 1.97 | 4.09 | 11.60 | -60,008 | -56,451 | 183,984 | -80,210 | 41.7 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.197 / +0.104 / -0.200
- [PASS] 3 worst week within share: all-in worst week +5.4% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.67 vs p95 0.72 (rank 0.94)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.044, +0.232]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.191 / +0.099 / -0.205
- [PASS] 6 worst-decile corr <=+0.30: +0.12
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section L9); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (267 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1934 | -0.0012 | -0.02 |
| fixed | 1934 | -0.0115 | -0.23 |
| scaled | 1934 | -0.0077 | -0.15 |

Plateau neighbours (all-in 20% uplift; selected +0.089):
- {'leg': 'rth', 'delta': '0.06', 'mode': 'longonly'}: +0.227 (trades 644)
- {'leg': 'rth', 'delta': '0.1', 'mode': 'longonly'}: +0.071 (trades 108)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.09, p95 0.72, real 0.67. Standalone Sharpe at 2x slippage 0.64.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 193 | -6 | -0.74 |
| 2017 | 288 | 7 | 0.49 |
| 2018 | 330 | -14 | -0.72 |
| 2019 | 199 | -3 | -0.28 |
| 2020 | 367 | 10 | 0.92 |
| 2021 | 299 | 4 | 0.31 |
| 2022 | 258 | -20 | -1.16 |
| 2023 | 21 | 2 | 1.17 |
| 2024 | 94 | -0 | -0.00 |
| 2025 | 90 | 24 | 1.89 |
| 2026 | 74 | -5 | -1.01 |


## Beta / drift test (report): regression of the sleeve's daily P&L on the always-long basket of the same instruments (unit risk), 2023-08..2026-10: beta +0.086; sleeve weekly Sharpe 0.67; always-long basket 0.65; ALPHA weekly Sharpe 0.47, bootstrap 90% CI [-0.50, +1.26] (alpha CI includes zero).

DONE L9