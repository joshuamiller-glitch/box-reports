# REPORT RX11
**Verdict: NO** (4/7 measured gates pass). Selected cell ev=F, act=shorten; additive @20% clean/H1/H2 +0.19/+0.94/+0.18; standalone all-in weekly Sharpe 1.69 (2013-26 0.62, dev 2013-22 0.10); pair-window trades 195. Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RX11 event-aware I9: skip or shorten the 2-day dip-buy hold when FOMC (and CPI/NFP) falls inside it (6 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 6 cells, eligible (>= 100 clean trades): 5. Top cells by clean weekly Sharpe:

| ev   | act     |   n |   sharpe |    net |   ypos | eligible   |
|:-----|:--------|----:|---------:|-------:|-------:|:-----------|
| F    | shorten | 118 |    1.266 | 27.595 |      3 | True       |
| F    | skip    | 117 |    1.253 | 27.315 |      3 | True       |
| FC   | skip    | 111 |    1.209 | 26.377 |      3 | True       |
| FC   | shorten | 116 |    1.198 | 26.310 |      3 | True       |
| FNC  | shorten | 106 |    0.728 | 14.559 |      2 | True       |
| FNC  | skip    |  89 |    0.530 |  9.761 |      2 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.27; replicate best-eligible median 0.59, p95 1.37; real beats 90% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=4.159e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.102 | +0.509 | +0.100 | +0.158 | +15.0 | [+0.053, +0.272] | 0.31 | NO |
| 20% | add | +0.187 | +0.944 | +0.180 | +0.291 | +41.6 | [+0.090, +0.511] | 0.31 | NO |
| 30% | add | +0.253 | +1.290 | +0.239 | +0.397 | +68.2 | [+0.104, +0.714] | 0.31 | NO |
| 50% | add | +0.338 | +1.730 | +0.297 | +0.536 | +121.4 | [+0.096, +1.013] | 0.31 | NO |
| 10% | const | +0.113 | +0.562 | +0.110 | +0.174 | +6.2 | [+0.058, +0.300] | 0.31 | NO |
| 20% | const | +0.222 | +1.129 | +0.212 | +0.347 | +23.9 | [+0.097, +0.617] | 0.31 | NO |
| 30% | const | +0.314 | +1.608 | +0.285 | +0.496 | +41.7 | [+0.103, +0.921] | 0.31 | NO |
| 50% | const | +0.372 | +1.972 | +0.201 | +0.603 | +77.2 | [-0.072, +1.312] | 0.31 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,147,555, Sharpe 1.26, maxDD 379,887, worst wk -219,583; H1: net 1,095,639, Sharpe 3.76, maxDD 86,633, worst wk -86,633; H2: net 313,055, Sharpe 1.05, maxDD 160,250, worst wk -81,899; all: net 2,556,249, Sharpe 1.69, maxDD 379,887, worst wk -219,583
Correlation with pair (weekly): clean +0.10, H1 -0.04, H2 -0.07, all +0.04; worst-decile weeks (n=17) corr +0.32, sleeve mean in those weeks $-6,840, positive share 0.41.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.65 | 3.11 | 5.42 | -91,359 | -84,390 | 287,771 | -116,868 | 40.0 |
| clean | add 30% | 1.71 | 3.20 | 5.27 | -100,169 | -89,339 | 317,504 | -138,826 | 42.9 |
| clean | const 20% | 1.68 | 3.16 | 5.35 | -76,201 | -69,385 | 241,614 | -102,278 | 41.0 |
| clean | const 30% | 1.77 | 3.27 | 5.10 | -78,968 | -67,232 | 250,129 | -116,941 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.77 | 8.93 | 5.89 | -77,610 | -65,596 | 138,066 | -78,287 | 35.7 |
| H1 | add 30% | 4.12 | 10.22 | 6.67 | -77,610 | -65,379 | 138,283 | -78,287 | 35.7 |
| H1 | const 20% | 3.96 | 9.59 | 6.28 | -62,088 | -52,390 | 110,540 | -62,630 | 35.7 |
| H1 | const 30% | 4.44 | 11.71 | 7.67 | -54,327 | -45,570 | 96,993 | -54,801 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.48 | 5.13 | 3.59 | -86,102 | -82,251 | 229,689 | -89,680 | 44.4 |
| H2 | add 30% | 2.53 | 5.22 | 3.63 | -89,168 | -83,784 | 235,821 | -95,811 | 38.9 |
| H2 | const 20% | 2.51 | 5.18 | 3.61 | -70,108 | -66,414 | 186,204 | -74,196 | 41.7 |
| H2 | const 30% | 2.58 | 5.30 | 3.61 | -65,177 | -60,029 | 173,392 | -72,587 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.15 | 4.22 | 11.11 | -88,999 | -83,089 | 287,771 | -116,868 | 39.9 |
| all | add 30% | 2.25 | 4.42 | 10.87 | -95,533 | -86,652 | 317,504 | -138,826 | 40.5 |
| all | const 20% | 2.20 | 4.33 | 11.01 | -73,528 | -67,828 | 241,614 | -102,278 | 39.9 |
| all | const 30% | 2.35 | 4.59 | 10.58 | -73,394 | -64,019 | 250,129 | -116,941 | 38.7 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.187 / +0.944 / +0.180
- [FAIL] 3 worst week within share: all-in worst week +41.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.69 vs p95 1.09 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.090, +0.511]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.181 / +0.939 / +0.177
- [FAIL] 6 worst-decile corr <=+0.30: +0.32
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RX11); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (195 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 409 | +0.0400 | 0.16 |
| fixed | 409 | +0.0258 | 0.10 |
| scaled | 409 | +0.0334 | 0.13 |

Plateau neighbours (all-in 20% uplift; selected +0.291):

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.30, p95 1.09, real 1.69. Standalone Sharpe at 2x slippage 1.67.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 6 | 2 | 1.38 |
| 2014 | 47 | 5 | 0.70 |
| 2015 | 55 | -8 | -0.62 |
| 2016 | 29 | -8 | -0.59 |
| 2017 | 42 | 16 | 1.58 |
| 2018 | 43 | -12 | -0.89 |
| 2019 | 46 | 7 | 0.88 |
| 2020 | 47 | 9 | 0.74 |
| 2021 | 80 | 4 | 0.29 |
| 2022 | 14 | -4 | -0.52 |
| 2023 | 72 | 22 | 1.76 |
| 2024 | 68 | 23 | 2.04 |
| 2025 | 51 | 23 | 2.24 |
| 2026 | 44 | 14 | 1.71 |


DONE RX11