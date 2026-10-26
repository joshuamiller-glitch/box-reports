# REPORT RZ8
**Verdict: NO** (1/7 measured gates pass). Selected cell st=0.75, q=0.5; additive @20% clean/H1/H2 -0.08/-0.51/+0.25; standalone all-in weekly Sharpe -0.10 (2013-26 0.61, dev 2013-22 0.81); pair-window trades 357. Runtime 1.8 min (+selection 0.0 min). 10-worker pool.

RZ8 NQ prior-day high/low break conditioned on the range forecast (6 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 6 cells, eligible (>= 40 clean trades): 6. Top cells by clean weekly Sharpe:

|    st |     q |   n |   sharpe |    net |   ypos | eligible   |
|------:|------:|----:|---------:|-------:|-------:|:-----------|
| 0.750 | 0.500 | 212 |   -0.195 | -2.944 |      1 | True       |
| 0.750 | 0.670 |  80 |   -0.227 | -1.802 |      1 | True       |
| 0.500 | 0.000 | 434 |   -0.243 | -5.337 |      1 | True       |
| 0.750 | 0.000 | 434 |   -0.332 | -5.765 |      1 | True       |
| 0.500 | 0.500 | 212 |   -0.344 | -6.277 |      1 | True       |
| 0.500 | 0.670 |  80 |   -0.539 | -5.903 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe -0.19; replicate best-eligible median 0.36, p95 0.98; real beats 3% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=6.026e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.032 | -0.240 | +0.132 | -0.026 | +6.7 | [-0.112, +0.061] | 0.27 | NO |
| 20% | add | -0.077 | -0.507 | +0.245 | -0.068 | +20.2 | [-0.238, +0.106] | 0.27 | NO |
| 30% | add | -0.132 | -0.796 | +0.340 | -0.122 | +33.7 | [-0.375, +0.135] | 0.27 | NO |
| 50% | add | -0.260 | -1.406 | +0.480 | -0.256 | +60.6 | [-0.662, +0.154] | 0.27 | NO |
| 10% | const | -0.036 | -0.269 | +0.146 | -0.030 | -2.6 | [-0.125, +0.067] | 0.27 | NO |
| 20% | const | -0.103 | -0.649 | +0.295 | -0.094 | +1.5 | [-0.306, +0.122] | 0.27 | NO |
| 30% | const | -0.212 | -1.185 | +0.437 | -0.206 | +5.7 | [-0.559, +0.154] | 0.27 | NO |
| 50% | const | -0.582 | -2.804 | +0.631 | -0.619 | +14.0 | [-1.281, +0.075] | 0.27 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -177,405, Sharpe -0.19, maxDD 842,464, worst wk -197,232; H1: net -587,782, Sharpe -3.13, maxDD 611,332, worst wk -111,209; H2: net 619,982, Sharpe 2.35, maxDD 260,575, worst wk -106,660; all: net -145,205, Sharpe -0.10, maxDD 948,208, worst wk -197,232
Correlation with pair (weekly): clean +0.04, H1 -0.21, H2 +0.25, all +0.04; worst-decile weeks (n=17) corr -0.21, sleeve mean in those weeks $9,644, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.38 | 2.66 | 4.80 | -85,864 | -81,025 | 269,819 | -94,802 | 45.7 |
| clean | add 30% | 1.33 | 2.54 | 4.25 | -90,272 | -82,778 | 300,183 | -105,727 | 43.8 |
| clean | const 20% | 1.36 | 2.61 | 4.56 | -70,454 | -65,521 | 225,577 | -80,211 | 47.6 |
| clean | const 30% | 1.25 | 2.34 | 3.61 | -68,288 | -60,833 | 242,911 | -83,842 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.32 | 4.38 | 2.52 | -83,566 | -70,981 | 189,226 | -99,174 | 42.9 |
| H1 | add 30% | 2.03 | 3.59 | 1.94 | -86,544 | -76,205 | 215,022 | -110,295 | 42.9 |
| H1 | const 20% | 2.18 | 3.98 | 2.21 | -68,044 | -58,874 | 161,699 | -83,788 | 42.9 |
| H1 | const 30% | 1.64 | 2.69 | 1.38 | -67,413 | -58,044 | 173,732 | -87,215 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.54 | 5.47 | 4.10 | -82,821 | -79,203 | 216,177 | -88,227 | 41.7 |
| H2 | add 30% | 2.64 | 5.84 | 4.39 | -85,592 | -79,212 | 215,553 | -93,768 | 41.7 |
| H2 | const 20% | 2.59 | 5.66 | 4.24 | -67,365 | -63,366 | 172,692 | -72,798 | 41.7 |
| H2 | const 30% | 2.73 | 6.28 | 4.78 | -62,407 | -55,986 | 150,325 | -70,623 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.79 | 3.51 | 9.84 | -86,667 | -80,895 | 269,819 | -99,174 | 44.0 |
| all | add 30% | 1.73 | 3.39 | 8.80 | -91,457 | -82,594 | 300,183 | -110,295 | 42.9 |
| all | const 20% | 1.76 | 3.46 | 9.39 | -71,249 | -65,311 | 225,577 | -83,788 | 45.2 |
| all | const 30% | 1.65 | 3.18 | 7.56 | -69,084 | -60,466 | 242,911 | -87,215 | 42.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.077 / -0.507 / +0.245
- [FAIL] 3 worst week within share: all-in worst week +20.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.10 vs p95 0.49 (rank 0.56)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.238, +0.106]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.077 / -0.509 / +0.248
- [PASS] 6 worst-decile corr <=+0.30: -0.21
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ8); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (357 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 976 | +0.0568 | 0.86 |
| fixed | 976 | +0.0530 | 0.81 |
| scaled | 976 | +0.0530 | 0.81 |

Plateau neighbours (all-in 20% uplift; selected -0.068):
- {'st': '0.6', 'q': '0.5'}: -0.123 (trades 357)
- {'st': '0.94', 'q': '0.5'}: -0.093 (trades 357)
- {'st': '0.75', 'q': '0.375'}: -0.120 (trades 519)
- {'st': '0.75', 'q': '0.625'}: -0.032 (trades 196)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.17, p95 0.49, real -0.10. Standalone Sharpe at 2x slippage -0.09.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2014 | 87 | -1 | -0.16 |
| 2015 | 129 | -5 | -0.56 |
| 2016 | 91 | 6 | 1.05 |
| 2017 | 56 | 19 | 3.95 |
| 2018 | 144 | 1 | 0.17 |
| 2019 | 96 | 13 | 2.77 |
| 2020 | 145 | 10 | 1.36 |
| 2021 | 81 | 8 | 1.13 |
| 2022 | 147 | -1 | -0.08 |
| 2023 | 55 | 4 | 0.70 |
| 2024 | 113 | -5 | -0.59 |
| 2025 | 109 | 0 | 0.06 |
| 2026 | 106 | 5 | 0.87 |

## Forecast skill of the pre-open score against the realised RTH range / ADR20 (Spearman rho, AUC for the top third)

| score | 2013-22 rho / AUC (n) | 2023-26 rho / AUC (n) |
|---|---|---|
| full (overnight, prior-day, VIX) | +0.40 / 0.71 (2304) | +0.37 / 0.66 (826) |
| early (prior-day, VIX) | +0.30 / 0.67 (2304) | +0.23 / 0.60 (826) |
| full + macro overnight leg (RZ10) | +0.43 / 0.73 (2304) | +0.40 / 0.68 (826) |
| early + macro (same as early) | +0.30 / 0.67 (2304) | +0.23 / 0.60 (826) |

## Control: same cell without the forecast filter (same scaling factor): 20% additive uplift clean/H1/H2/all -0.137/-0.607/+0.117/-0.146; selected cell -0.077/-0.507/+0.245/-0.068; trades 3040 vs 1359.

DONE RZ8