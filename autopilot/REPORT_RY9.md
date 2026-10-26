# REPORT RY9
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell sc=0.15, cap=2.0; additive @20% clean/H1/H2 +0.13/+0.45/+0.13; standalone all-in weekly Sharpe 1.17 (2013-26 0.52, dev 2013-22 0.32); pair-window trades 2893. Runtime 0.1 min (+selection 0.0 min). 10-worker pool.

RY9 K4 continuous sizing: units = clip((p-0.5)/sc, 0, cap) with the 5-seed ensemble (4 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 4 cells, eligible (>= 100 clean trades): 4. Top cells by clean weekly Sharpe:

|    sc |   cap |    n |   sharpe |    net |   ypos | eligible   |
|------:|------:|-----:|---------:|-------:|-------:|:-----------|
| 0.150 | 2.000 | 1761 |    1.038 | 33.785 |      2 | True       |
| 0.100 | 2.000 | 1761 |    1.023 | 45.689 |      2 | True       |
| 0.150 | 1.000 | 1761 |    0.988 | 27.191 |      2 | True       |
| 0.100 | 1.000 | 1761 |    0.934 | 36.161 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.04; replicate best-eligible median 0.46, p95 0.67; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.797e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.074 | +0.230 | +0.072 | +0.088 | +4.7 | [+0.019, +0.160] | 0.27 | NO |
| 20% | add | +0.132 | +0.446 | +0.134 | +0.160 | +14.8 | [+0.025, +0.297] | 0.27 | NO |
| 30% | add | +0.173 | +0.644 | +0.185 | +0.214 | +25.5 | [+0.018, +0.412] | 0.27 | NO |
| 50% | add | +0.216 | +0.972 | +0.255 | +0.276 | +46.9 | [-0.036, +0.583] | 0.27 | NO |
| 10% | const | +0.082 | +0.254 | +0.079 | +0.097 | -5.2 | [+0.020, +0.176] | 0.27 | NO |
| 20% | const | +0.154 | +0.548 | +0.161 | +0.189 | -3.9 | [+0.024, +0.356] | 0.27 | NO |
| 30% | const | +0.206 | +0.867 | +0.235 | +0.260 | -2.5 | [-0.011, +0.532] | 0.27 | NO |
| 50% | const | +0.191 | +1.360 | +0.257 | +0.253 | +0.2 | [-0.279, +0.775] | 0.27 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 942,435, Sharpe 1.03, maxDD 384,888, worst wk -100,905; H1: net 391,866, Sharpe 2.42, maxDD 157,767, worst wk -63,276; H2: net 190,426, Sharpe 0.88, maxDD 280,438, worst wk -86,597; all: net 1,524,727, Sharpe 1.17, maxDD 384,888, worst wk -100,905
Correlation with pair (weekly): clean +0.14, H1 -0.22, H2 -0.13, all +0.05; worst-decile weeks (n=17) corr -0.09, sleeve mean in those weeks $13,414, positive share 0.59.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.59 | 3.12 | 5.18 | -87,261 | -81,854 | 292,909 | -94,730 | 41.9 |
| clean | add 30% | 1.63 | 3.25 | 5.39 | -92,012 | -84,185 | 299,309 | -103,566 | 42.9 |
| clean | const 20% | 1.61 | 3.19 | 5.29 | -71,709 | -66,336 | 236,887 | -79,318 | 42.9 |
| clean | const 30% | 1.67 | 3.39 | 5.64 | -68,824 | -61,246 | 215,276 | -80,448 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.27 | 7.66 | 4.79 | -70,219 | -62,098 | 140,338 | -74,993 | 39.3 |
| H1 | add 30% | 3.47 | 8.45 | 5.02 | -66,523 | -60,132 | 141,691 | -74,024 | 35.7 |
| H1 | const 20% | 3.38 | 8.05 | 4.91 | -54,697 | -48,892 | 112,812 | -59,607 | 35.7 |
| H1 | const 30% | 3.69 | 9.49 | 5.31 | -43,240 | -40,323 | 100,401 | -50,944 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.43 | 5.25 | 3.54 | -77,639 | -71,726 | 225,535 | -79,962 | 41.7 |
| H2 | add 30% | 2.48 | 5.52 | 3.56 | -77,818 | -70,277 | 229,589 | -81,370 | 41.7 |
| H2 | const 20% | 2.46 | 5.39 | 3.55 | -62,183 | -56,631 | 182,050 | -64,533 | 41.7 |
| H2 | const 30% | 2.53 | 5.85 | 3.59 | -54,634 | -48,273 | 164,362 | -58,226 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.02 | 4.10 | 10.21 | -84,473 | -79,050 | 292,909 | -94,730 | 41.7 |
| all | add 30% | 2.07 | 4.29 | 10.50 | -87,942 | -80,066 | 299,309 | -103,566 | 41.7 |
| all | const 20% | 2.04 | 4.19 | 10.35 | -68,966 | -63,646 | 236,887 | -79,318 | 41.7 |
| all | const 30% | 2.12 | 4.48 | 10.86 | -64,681 | -57,260 | 215,276 | -80,448 | 41.1 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.132 / +0.446 / +0.134
- [PASS] 3 worst week within share: all-in worst week +14.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.17 vs p95 0.71 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.025, +0.297]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.117 / +0.431 / +0.123
- [PASS] 6 worst-decile corr <=+0.30: -0.09
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RY9); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2893 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 5545 | +0.0137 | 0.51 |
| fixed | 5545 | +0.0087 | 0.32 |
| scaled | 5545 | +0.0106 | 0.39 |

Plateau neighbours (all-in 20% uplift; selected +0.160):
- {'sc': '0.1125', 'cap': '2.0'}: +0.196 (trades 2893)
- {'sc': '0.1875', 'cap': '2.0'}: +0.133 (trades 2893)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.53, p95 0.71, real 1.17. Standalone Sharpe at 2x slippage 1.09.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 399 | -4 | -0.22 |
| 2017 | 614 | 35 | 2.10 |
| 2018 | 860 | 5 | 0.18 |
| 2019 | 856 | 2 | 0.12 |
| 2020 | 943 | 14 | 0.46 |
| 2021 | 945 | 24 | 1.48 |
| 2022 | 928 | -28 | -1.47 |
| 2023 | 744 | 3 | 0.42 |
| 2024 | 950 | 10 | 0.70 |
| 2025 | 906 | 35 | 1.89 |
| 2026 | 732 | 10 | 1.16 |


## Beta / drift test (report): beta +0.307; alpha weekly Sharpe 0.92, 90% CI [+0.06, +1.60] (alpha CI lower bound > 0).

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.17 vs scaled buy-and-hold 0.66; paired-bootstrap 90% CI of the difference [-0.04, +1.03]; exposure ES 93.4%, NQ 94.2%, RTY 86.2%, YM 86.4%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.03 | 0.47 | +0.132 | +0.034 |
| H1 | 2.42 | 1.57 | +0.446 | +0.352 |
| H2 | 0.88 | 0.65 | +0.134 | +0.104 |
| all | 1.17 | 0.66 | +0.160 | +0.082 |
DONE RY9