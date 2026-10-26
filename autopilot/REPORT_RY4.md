# REPORT RY4
**Verdict: NO** (3/7 measured gates pass). Selected cell var=base, ss=A, N=1, delta=0.08, w=8, rule=neg; additive @20% clean/H1/H2 +0.10/+0.03/+0.00; standalone all-in weekly Sharpe 0.61 (2013-26 0.68, dev 2013-22 nan); pair-window trades 42 (SMALL-SAMPLE). Runtime 0.0 min (+selection 0.0 min). 10-worker pool.

RY4 regime-conditional RX5: take the K4 ensemble signal only when the pair's own trailing 8/13-week P&L is bad (hedge claim).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 4 cells, eligible (>= 40 clean trades): 2. Top cells by clean weekly Sharpe:

| var   | ss   |   N |   delta |   w | rule   |   n |   sharpe |    net |   ypos | eligible   |
|:------|:-----|----:|--------:|----:|:-------|----:|---------:|-------:|-------:|:-----------|
| base  | A    |   1 |   0.080 |  13 | neg    |   6 |    1.404 |  2.207 |      2 | False      |
| base  | A    |   1 |   0.080 |  13 | bot3   |  18 |    0.979 | 11.880 |      2 | False      |
| base  | A    |   1 |   0.080 |   8 | bot3   |  41 |    0.784 | 10.710 |      2 | True       |
| base  | A    |   1 |   0.080 |   8 | neg    |  41 |    0.784 | 10.710 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.78; replicate best-eligible median 0.52, p95 1.03; real beats 80% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=5.857e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.058 | +0.014 | +0.000 | +0.039 | +0.0 | [-0.015, +0.099] | 0.37 | NO |
| 20% | add | +0.100 | +0.026 | +0.000 | +0.066 | +0.0 | [-0.036, +0.171] | 0.37 | NO |
| 30% | add | +0.127 | +0.036 | +0.000 | +0.080 | +0.0 | [-0.063, +0.225] | 0.37 | NO |
| 50% | add | +0.140 | +0.048 | +0.000 | +0.077 | +30.7 | [-0.138, +0.300] | 0.37 | NO |
| 10% | const | +0.063 | +0.016 | +0.000 | +0.043 | -10.0 | [-0.017, +0.108] | 0.37 | NO |
| 20% | const | +0.115 | +0.031 | +0.000 | +0.074 | -20.0 | [-0.049, +0.200] | 0.37 | NO |
| 30% | const | +0.141 | +0.044 | +0.000 | +0.082 | -18.5 | [-0.108, +0.275] | 0.37 | NO |
| 50% | const | +0.043 | +0.046 | +0.000 | -0.049 | +14.9 | [-0.439, +0.400] | 0.37 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 627,271, Sharpe 0.69, maxDD 344,699, worst wk -163,740; H1: net 85,409, Sharpe 1.36, maxDD 0, worst wk 0; H2: net 0, Sharpe nan, maxDD 0, worst wk 0; all: net 712,680, Sharpe 0.61, maxDD 344,699, worst wk -163,740
Correlation with pair (weekly): clean +0.02, H1 +0.30, H2 +nan, all +0.03; worst-decile weeks (n=17) corr +0.05, sleeve mean in those weeks $14,127, positive share 0.18.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.56 | 3.10 | 5.69 | -77,943 | -77,249 | 255,842 | -79,868 | 42.9 |
| clean | add 30% | 1.59 | 3.23 | 6.23 | -77,943 | -77,357 | 243,708 | -79,868 | 42.9 |
| clean | const 20% | 1.58 | 3.17 | 5.95 | -62,354 | -61,731 | 199,820 | -63,894 | 42.9 |
| clean | const 30% | 1.60 | 3.37 | 6.68 | -56,772 | -55,490 | 167,621 | -67,291 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.85 | 6.26 | 4.03 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 30% | 2.86 | 6.35 | 4.08 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | const 20% | 2.86 | 6.31 | 4.05 | -62,088 | -52,824 | 121,370 | -62,630 | 39.3 |
| H1 | const 30% | 2.87 | 6.46 | 4.16 | -54,327 | -46,221 | 106,199 | -54,801 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | const 20% | 2.30 | 4.69 | 3.50 | -64,871 | -63,348 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 2.30 | 4.69 | 3.50 | -56,762 | -55,430 | 152,198 | -57,767 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.92 | 3.87 | 11.05 | -78,708 | -77,747 | 255,842 | -82,524 | 42.9 |
| all | add 30% | 1.94 | 3.97 | 11.89 | -78,708 | -77,817 | 243,708 | -82,524 | 42.9 |
| all | const 20% | 1.93 | 3.92 | 11.46 | -62,966 | -62,154 | 199,820 | -66,020 | 42.9 |
| all | const 30% | 1.94 | 4.07 | 12.49 | -56,563 | -55,339 | 167,621 | -67,291 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.100 / +0.026 / +0.000
- [PASS] 3 worst week within share: all-in worst week +0.0% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.61 vs p95 1.01 (rank 0.82)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.036, +0.171]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 75% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.098 / +0.026 / +0.000
- [PASS] 6 worst-decile corr <=+0.30: +0.05
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RY4); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (42 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 0 | +0.0000 | nan |
| fixed | 0 | +0.0000 | nan |
| scaled | 0 | +0.0000 | nan |

Plateau neighbours (all-in 20% uplift; selected +0.066):
- {'var': 'base', 'ss': 'A', 'N': '1', 'delta': '0.06', 'w': '8', 'rule': 'neg'}: +0.080 (trades 110)
- {'var': 'base', 'ss': 'A', 'N': '1', 'delta': '0.1', 'w': '8', 'rule': 'neg'}: +0.040 (trades 23)
- {'var': 'base', 'ss': 'A', 'N': '1', 'delta': '0.08', 'w': '6', 'rule': 'neg'}: +0.069 (trades 52)
- {'var': 'base', 'ss': 'A', 'N': '1', 'delta': '0.08', 'w': '10', 'rule': 'neg'}: +0.067 (trades 44)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.13, p95 1.01, real 0.61. Standalone Sharpe at 2x slippage 0.61.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2023 | 8 | 2 | 1.64 |
| 2024 | 7 | -1 | nan |
| 2025 | 29 | 11 | 1.56 |


## Beta / drift test (report): beta +0.039; alpha weekly Sharpe 0.45, 90% CI [-0.67, +1.06] (alpha CI includes zero).

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 0.61 vs scaled buy-and-hold 0.68; paired-bootstrap 90% CI of the difference [-1.33, +0.98]; exposure ES 1.5%, NQ 1.6%, RTY 1.2%, YM 0.9%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 0.69 | 0.49 | +0.100 | +0.037 |
| H1 | 1.36 | 1.47 | +0.026 | +0.327 |
| H2 | nan | 0.76 | +0.000 | +0.120 |
| all | 0.61 | 0.68 | +0.066 | +0.084 |
## Hedge-claim gates (RY4 registered as a hedge claim)
- [FAIL] worst-decile correlation with the pair < 0: +0.05
- [FAIL] circular-shift null rank >= 0.95: 0.37

DONE RY4