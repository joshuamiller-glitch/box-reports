# REPORT RW3
**Verdict: NO** (2/7 measured gates pass). Selected cell cls=ridge, q=0.08, N=1; additive @20% clean/H1/H2 +0.01/+0.43/+0.10; standalone all-in weekly Sharpe 0.59 (2013-26 0.25, dev 2013-22 0.03); pair-window trades 298. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

R3 K4 with non-tree models (logistic, ridge), same features, top-q score rule (6 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 6 cells, eligible (>= 100 clean trades): 6. Top cells by clean weekly Sharpe:

| cls   |     q |   N |   n |   sharpe |   net |   ypos | eligible   |
|:------|------:|----:|----:|---------:|------:|-------:|:-----------|
| ridge | 0.080 |   1 | 229 |    0.325 | 9.562 |      1 | True       |
| logit | 0.080 |   1 | 225 |    0.234 | 6.815 |      1 | True       |
| logit | 0.160 |   1 | 384 |    0.205 | 8.187 |      1 | True       |
| ridge | 0.250 |   1 | 530 |    0.119 | 5.960 |      1 | True       |
| ridge | 0.160 |   1 | 385 |    0.109 | 4.316 |      1 | True       |
| logit | 0.250 |   1 | 532 |    0.108 | 5.389 |      1 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.32; replicate best-eligible median 0.85, p95 1.30; real beats 0% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.866e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.012 | +0.215 | +0.057 | +0.043 | +0.0 | [-0.023, +0.116] | 0.41 | NO |
| 20% | add | +0.009 | +0.431 | +0.101 | +0.071 | +2.5 | [-0.060, +0.210] | 0.41 | NO |
| 30% | add | -0.005 | +0.647 | +0.134 | +0.084 | +6.8 | [-0.111, +0.287] | 0.41 | NO |
| 50% | add | -0.062 | +1.069 | +0.163 | +0.072 | +16.6 | [-0.246, +0.393] | 0.41 | NO |
| 10% | const | +0.012 | +0.239 | +0.062 | +0.047 | -10.0 | [-0.026, +0.127] | 0.41 | NO |
| 20% | const | +0.003 | +0.539 | +0.119 | +0.079 | -16.3 | [-0.083, +0.250] | 0.41 | NO |
| 30% | const | -0.038 | +0.921 | +0.158 | +0.082 | -21.4 | [-0.194, +0.359] | 0.41 | NO |
| 50% | const | -0.260 | +1.975 | +0.067 | -0.084 | +38.8 | [-0.658, +0.484] | 0.41 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 274,012, Sharpe 0.30, maxDD 394,244, worst wk -295,488; H1: net 328,890, Sharpe 3.20, maxDD 27,677, worst wk -4,748; H2: net 154,971, Sharpe 0.66, maxDD 132,540, worst wk -96,643; all: net 757,873, Sharpe 0.59, maxDD 394,244, worst wk -295,488
Correlation with pair (weekly): clean +0.08, H1 -0.41, H2 -0.09, all +0.01; worst-decile weeks (n=17) corr -0.12, sleeve mean in those weeks $-3,024, positive share 0.12.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.47 | 2.85 | 4.74 | -82,051 | -79,999 | 292,321 | -84,596 | 42.9 |
| clean | add 30% | 1.45 | 2.87 | 4.73 | -83,762 | -81,142 | 298,427 | -88,115 | 44.8 |
| clean | const 20% | 1.46 | 2.86 | 4.73 | -66,323 | -64,398 | 236,299 | -69,085 | 43.8 |
| clean | const 30% | 1.42 | 2.84 | 4.73 | -61,344 | -58,419 | 214,394 | -64,848 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.26 | 7.55 | 4.35 | -69,649 | -60,723 | 151,713 | -78,287 | 39.3 |
| H1 | add 30% | 3.47 | 8.26 | 4.56 | -65,668 | -58,069 | 151,713 | -78,287 | 32.1 |
| H1 | const 20% | 3.37 | 7.91 | 4.46 | -54,127 | -47,517 | 121,370 | -62,630 | 35.7 |
| H1 | const 30% | 3.75 | 9.17 | 4.84 | -42,405 | -38,260 | 106,199 | -54,801 | 32.1 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.40 | 5.03 | 3.43 | -79,970 | -78,386 | 231,280 | -82,524 | 44.4 |
| H2 | add 30% | 2.43 | 5.13 | 3.39 | -79,970 | -77,987 | 238,207 | -82,524 | 44.4 |
| H2 | const 20% | 2.41 | 5.09 | 3.41 | -63,976 | -62,549 | 187,795 | -66,020 | 44.4 |
| H2 | const 30% | 2.45 | 5.20 | 3.35 | -55,979 | -54,231 | 172,980 | -57,767 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.93 | 3.86 | 9.70 | -81,365 | -79,339 | 292,321 | -84,596 | 42.9 |
| all | add 30% | 1.94 | 3.94 | 9.76 | -82,620 | -80,111 | 298,427 | -88,115 | 42.9 |
| all | const 20% | 1.93 | 3.91 | 9.73 | -65,579 | -63,692 | 236,299 | -69,085 | 42.9 |
| all | const 30% | 1.94 | 3.98 | 9.83 | -59,813 | -57,125 | 214,394 | -64,848 | 42.3 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.009 / +0.431 / +0.101
- [PASS] 3 worst week within share: all-in worst week +2.5% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.59 vs p95 1.04 (rank 0.76)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.060, +0.210]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.002 / +0.428 / +0.098
- [PASS] 6 worst-decile corr <=+0.30: -0.12
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section R3); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (298 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 446 | +0.0146 | 0.09 |
| fixed | 446 | +0.0054 | 0.03 |
| scaled | 446 | +0.0080 | 0.05 |

Plateau neighbours (all-in 20% uplift; selected +0.071):
- {'cls': 'ridge', 'q': '0.06', 'N': '1'}: +0.072 (trades 238)
- {'cls': 'ridge', 'q': '0.1', 'N': '1'}: +0.034 (trades 368)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.20, p95 1.04, real 0.59. Standalone Sharpe at 2x slippage 0.56.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 3 | 0 | 1.42 |
| 2017 | 49 | 5 | 1.16 |
| 2018 | 145 | -1 | -0.04 |
| 2019 | 24 | 1 | 0.30 |
| 2020 | 85 | -3 | -0.30 |
| 2021 | 95 | 6 | 0.44 |
| 2022 | 45 | -5 | -0.82 |
| 2023 | 100 | -1 | -0.09 |
| 2024 | 151 | 20 | 1.10 |
| 2025 | 32 | -5 | -0.47 |
| 2026 | 61 | 12 | 1.42 |


## Beta / drift test (report): beta +0.157; alpha weekly Sharpe 0.34, 90% CI [-0.63, +1.15] (alpha CI includes zero).

DONE RW3