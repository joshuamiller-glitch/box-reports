# REPORT RU5
**Verdict: NO** (3/7 measured gates pass). Selected cell basket GC:stop/k1.5/tf15/S1.5/R2.0+SI:stop/k2.0/tf15/S1.5/R1.0+HO:stop/k2.0/tf15/S1.0/R2.0+NG:stop/k2.0/tf15/S1.5/R1.0+NQ:stop/k1.5/tf15/S1.5/R2.0, scales k1.0 S1.0 R1.0; additive @20% clean/H1/H2 +0.42/-0.13/-0.02; standalone all-in weekly Sharpe 1.60 (2013-26 -0.07, dev 2013-22 -0.63); pair-window trades 12303. Runtime 0.1 min (+selection 0.1 min). 10-worker pool.

RU5: equal-risk basket of the RU2 selected continuation cells with clean weekly Sharpe >= 0.5 (selection inherited from RU2; disclosure). Pre-registered in PREREG_AUTOPILOT.md BATCH RU.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 1 cells, eligible (>= 40 clean trades): 1. Top cells by clean weekly Sharpe:

|    n |    km |    Sm |    Rm |   sharpe |    net |   ypos | eligible   |
|-----:|------:|------:|------:|---------:|-------:|-------:|:-----------|
| 7739 | 1.000 | 1.000 | 1.000 |    2.639 | 75.797 |      3 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 2.64; replicate best-eligible median -1.28, p95 -0.57; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.172e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.223 | -0.048 | +0.002 | +0.134 | +9.3 | [+0.035, +0.234] | 0.09 | NO |
| 20% | add | +0.421 | -0.130 | -0.019 | +0.242 | +24.6 | [+0.050, +0.438] | 0.09 | NO |
| 30% | add | +0.591 | -0.238 | -0.062 | +0.325 | +39.9 | [+0.046, +0.617] | 0.09 | NO |
| 50% | add | +0.854 | -0.496 | -0.193 | +0.427 | +70.5 | [-0.009, +0.874] | 0.09 | NO |
| 10% | const | +0.247 | -0.055 | +0.001 | +0.147 | -0.1 | [+0.038, +0.257] | 0.09 | NO |
| 20% | const | +0.509 | -0.181 | -0.038 | +0.286 | +5.8 | [+0.052, +0.531] | 0.09 | NO |
| 30% | const | +0.771 | -0.401 | -0.141 | +0.399 | +11.7 | [+0.016, +0.796] | 0.09 | NO |
| 50% | const | +1.194 | -1.109 | -0.606 | +0.455 | +23.5 | [-0.242, +1.174] | 0.09 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 2,403,920, Sharpe 2.64, maxDD 310,473, worst wk -126,349; H1: net -8,827, Sharpe -0.03, maxDD 312,305, worst wk -132,829; H2: net 44,025, Sharpe 0.13, maxDD 332,421, worst wk -103,260; all: net 2,439,119, Sharpe 1.60, maxDD 462,473, worst wk -132,829
Correlation with pair (weekly): clean +0.19, H1 +0.07, H2 -0.01, all +0.11; worst-decile weeks (n=17) corr +0.00, sleeve mean in those weeks $22,562, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.88 | 3.87 | 6.65 | -83,508 | -77,730 | 272,490 | -102,828 | 41.9 |
| clean | add 30% | 2.05 | 4.35 | 7.53 | -87,370 | -79,054 | 272,574 | -115,463 | 41.9 |
| clean | const 20% | 1.97 | 4.12 | 7.09 | -67,944 | -62,662 | 218,025 | -87,316 | 41.0 |
| clean | const 30% | 2.23 | 4.86 | 8.51 | -65,815 | -56,716 | 194,051 | -92,195 | 40.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.70 | 5.46 | 3.53 | -76,942 | -70,142 | 167,683 | -85,447 | 35.7 |
| H1 | add 30% | 2.59 | 5.04 | 3.31 | -85,373 | -78,041 | 178,591 | -89,028 | 35.7 |
| H1 | const 20% | 2.65 | 5.25 | 3.45 | -64,926 | -59,273 | 137,341 | -69,790 | 35.7 |
| H1 | const 30% | 2.43 | 4.51 | 2.89 | -67,350 | -61,738 | 142,932 | -69,158 | 35.7 |
| H2 | pair | 2.30 | 4.65 | 3.58 | -81,089 | -79,185 | 217,425 | -82,524 | 43.2 |
| H2 | add 20% | 2.28 | 4.82 | 3.50 | -79,969 | -77,840 | 225,151 | -82,981 | 43.2 |
| H2 | add 30% | 2.24 | 4.75 | 3.42 | -85,964 | -79,806 | 231,618 | -87,283 | 45.9 |
| H2 | const 20% | 2.26 | 4.80 | 3.46 | -66,373 | -63,059 | 182,349 | -67,051 | 45.9 |
| H2 | const 30% | 2.16 | 4.52 | 3.31 | -65,570 | -57,818 | 168,761 | -70,392 | 45.9 |
| all | pair | 1.86 | 3.63 | 9.65 | -79,220 | -78,243 | 280,110 | -82,524 | 42.6 |
| all | add 20% | 2.10 | 4.32 | 11.71 | -83,155 | -77,663 | 272,490 | -102,828 | 41.4 |
| all | add 30% | 2.18 | 4.56 | 12.60 | -88,050 | -79,975 | 272,574 | -115,463 | 42.0 |
| all | const 20% | 2.14 | 4.45 | 12.15 | -67,984 | -63,022 | 218,025 | -87,316 | 41.4 |
| all | const 30% | 2.26 | 4.74 | 13.52 | -67,805 | -58,920 | 194,051 | -92,195 | 40.8 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.421 / -0.130 / -0.019
- [FAIL] 3 worst week within share: all-in worst week +24.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.60 vs p95 -0.42 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.050, +0.438]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 17% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.297 / -0.234 / -0.075
- [PASS] 6 worst-decile corr <=+0.30: +0.00
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RU5); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (12303 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 30227 | +0.0037 | 0.77 |
| fixed | 30227 | -0.0031 | -0.63 |
| scaled | 30227 | -0.0031 | -0.63 |

Plateau neighbours (all-in 20% uplift; selected +0.242):
- {'n': '5', 'km': '0.75', 'Sm': '1.0', 'Rm': '1.0'}: -0.127 (trades 21807)
- {'n': '5', 'km': '1.0', 'Sm': '0.75', 'Rm': '1.0'}: -0.010 (trades 13320)
- {'n': '5', 'km': '1.0', 'Sm': '1.0', 'Rm': '0.75'}: +0.074 (trades 13052)
- {'n': '5', 'km': '1.25', 'Sm': '1.0', 'Rm': '1.0'}: +0.063 (trades 6079)
- {'n': '5', 'km': '1.0', 'Sm': '1.25', 'Rm': '1.0'}: +0.185 (trades 11378)
- {'n': '5', 'km': '1.0', 'Sm': '1.0', 'Rm': '1.25'}: +0.171 (trades 11730)

Own random-entry null: 300 draws, standalone all-in Sharpe median -1.17, p95 -0.42, real 1.60. Standalone Sharpe at 2x slippage 1.07.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 2840 | -21 | -1.31 |
| 2014 | 2754 | -18 | -1.36 |
| 2015 | 2905 | -20 | -1.60 |
| 2016 | 3017 | -44 | -3.00 |
| 2017 | 2567 | -0 | -0.02 |
| 2018 | 2721 | -16 | -1.32 |
| 2019 | 2734 | -16 | -1.10 |
| 2020 | 3257 | 13 | 0.75 |
| 2021 | 3627 | 13 | 0.84 |
| 2022 | 3805 | 15 | 0.87 |
| 2023 | 3811 | 12 | 0.72 |
| 2024 | 3880 | 35 | 2.16 |
| 2025 | 3916 | 32 | 2.39 |
| 2026 | 2920 | 1 | 0.10 |


DONE RU5