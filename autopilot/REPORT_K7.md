# REPORT K7
**Verdict: NO** (1/7 measured gates pass). Selected cell ev=ism_svc, mode=fade, H=close; additive @20% clean/H1/H2 +0.19/-0.32/-0.06; standalone all-in weekly Sharpe 0.60 (2013-26 -0.08, dev 2013-22 -0.27); pair-window trades 153. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

K7 ISM release drift (NQ, ES, ZN, 6E): ISM manufacturing = first trading label of the month, services = third, 10:00 ET (calendar approximated by rule; 12 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 12 cells, eligible (>= 20 clean trades): 12. Top cells by clean weekly Sharpe:

| ev      | mode   | H     |   n |   sharpe |    net |   ypos | eligible   |
|:--------|:-------|:------|----:|---------:|-------:|-------:|:-----------|
| ism_svc | fade   | close |  95 |    1.317 |  9.099 |      3 | True       |
| ism_mfg | follow | close |  93 |    0.395 |  3.332 |      2 | True       |
| ism_mfg | fade   | 60    |  93 |    0.218 |  1.406 |      2 | True       |
| ism_mfg | fade   | 30    |  93 |    0.167 |  0.795 |      2 | True       |
| ism_svc | fade   | 60    |  95 |   -0.053 | -0.202 |      1 | True       |
| ism_svc | fade   | 30    |  95 |   -0.082 | -0.233 |      1 | True       |
| ism_mfg | fade   | close |  93 |   -0.845 | -7.415 |      1 | True       |
| ism_mfg | follow | 60    |  93 |   -0.858 | -5.489 |      1 | True       |
| ism_svc | follow | 60    |  95 |   -1.000 | -4.020 |      0 | True       |
| ism_mfg | follow | 30    |  93 |   -1.023 | -4.878 |      0 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.32; replicate best-eligible median 0.50, p95 1.13; real beats 97% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.292e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.104 | -0.147 | -0.026 | +0.039 | +20.2 | [-0.041, +0.125] | 0.23 | NO |
| 20% | add | +0.190 | -0.321 | -0.064 | +0.061 | +41.3 | [-0.093, +0.221] | 0.23 | NO |
| 30% | add | +0.257 | -0.509 | -0.114 | +0.065 | +62.3 | [-0.159, +0.295] | 0.23 | NO |
| 50% | add | +0.344 | -0.887 | -0.246 | +0.033 | +104.4 | [-0.322, +0.385] | 0.23 | NO |
| 10% | const | +0.114 | -0.165 | -0.030 | +0.043 | +10.3 | [-0.046, +0.138] | 0.23 | NO |
| 20% | const | +0.226 | -0.414 | -0.088 | +0.065 | +21.4 | [-0.125, +0.261] | 0.23 | NO |
| 30% | const | +0.320 | -0.754 | -0.194 | +0.049 | +32.6 | [-0.261, +0.360] | 0.23 | NO |
| 50% | const | +0.384 | -1.631 | -0.685 | -0.159 | +54.8 | [-0.754, +0.412] | 0.23 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,175,798, Sharpe 1.29, maxDD 298,444, worst wk -173,595; H1: net -158,840, Sharpe -0.59, maxDD 214,894, worst wk -214,894; H2: net -166,455, Sharpe -0.71, maxDD 250,661, worst wk -189,252; all: net 850,503, Sharpe 0.60, maxDD 707,944, worst wk -214,894
Correlation with pair (weekly): clean +0.11, H1 +0.15, H2 -0.18, all +0.05; worst-decile weeks (n=17) corr +0.44, sleeve mean in those weeks $1,408, positive share 0.18.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.65 | 3.19 | 5.54 | -84,522 | -81,165 | 282,613 | -116,593 | 41.9 |
| clean | add 30% | 1.72 | 3.37 | 5.61 | -87,415 | -82,743 | 299,973 | -133,952 | 41.9 |
| clean | const 20% | 1.69 | 3.28 | 5.57 | -68,775 | -65,563 | 233,035 | -100,218 | 41.9 |
| clean | const 30% | 1.78 | 3.56 | 5.69 | -63,795 | -59,341 | 225,605 | -109,390 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.51 | 5.49 | 3.53 | -77,610 | -68,238 | 159,338 | -78,287 | 39.3 |
| H1 | add 30% | 2.32 | 5.18 | 3.35 | -77,610 | -69,509 | 163,151 | -78,287 | 42.9 |
| H1 | const 20% | 2.41 | 5.34 | 3.44 | -62,088 | -55,099 | 128,995 | -62,630 | 42.9 |
| H1 | const 30% | 2.07 | 4.78 | 3.13 | -54,327 | -49,800 | 117,637 | -54,801 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.23 | 4.67 | 3.93 | -79,836 | -75,865 | 185,188 | -82,524 | 44.4 |
| H2 | add 30% | 2.18 | 4.57 | 3.95 | -80,184 | -77,037 | 180,286 | -82,524 | 47.2 |
| H2 | const 20% | 2.21 | 4.63 | 3.99 | -63,869 | -61,161 | 144,229 | -66,020 | 47.2 |
| H2 | const 30% | 2.10 | 4.33 | 3.83 | -59,593 | -54,982 | 126,200 | -61,419 | 47.2 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.92 | 3.81 | 10.10 | -82,800 | -80,024 | 282,613 | -116,593 | 42.3 |
| all | add 30% | 1.92 | 3.86 | 9.80 | -84,794 | -81,168 | 299,973 | -133,952 | 43.5 |
| all | const 20% | 1.92 | 3.84 | 9.95 | -67,012 | -64,413 | 233,035 | -100,218 | 43.5 |
| all | const 30% | 1.91 | 3.89 | 9.46 | -61,862 | -58,144 | 225,605 | -109,390 | 44.0 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.190 / -0.321 / -0.064
- [FAIL] 3 worst week within share: all-in worst week +41.3% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.60 vs p95 0.37 (rank 0.98)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.093, +0.221]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.144 / -0.390 / -0.115
- [FAIL] 6 worst-decile corr <=+0.30: +0.44
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section K7); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (153 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 456 | +0.0012 | 0.01 |
| fixed | 456 | -0.0278 | -0.27 |
| scaled | 456 | -0.0209 | -0.21 |

Plateau neighbours (all-in 20% uplift; selected +0.061):

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.43, p95 0.37, real 0.60. Standalone Sharpe at 2x slippage 0.33.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 43 | -2 | -0.54 |
| 2014 | 45 | -7 | -2.13 |
| 2015 | 45 | -4 | -1.10 |
| 2016 | 48 | -1 | -0.39 |
| 2017 | 46 | 1 | 0.31 |
| 2018 | 44 | 7 | 0.72 |
| 2019 | 46 | -2 | -0.38 |
| 2020 | 45 | -9 | -2.48 |
| 2021 | 47 | 3 | 0.93 |
| 2022 | 47 | 1 | 0.20 |
| 2023 | 48 | 4 | 0.96 |
| 2024 | 47 | 6 | 1.76 |
| 2025 | 47 | -0 | -0.08 |
| 2026 | 39 | -2 | -1.10 |


DONE K7