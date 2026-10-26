# REPORT J9
**Verdict: NO** (1/7 measured gates pass). Selected cell kind=inv, thr=1.0, sma=off, N=5; additive @20% clean/H1/H2 +0.03/+0.32/+0.11; standalone all-in weekly Sharpe 0.68 (2013-26 0.48, dev 2013-22 0.42); pair-window trades 68 (SMALL-SAMPLE). Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

J9 VIX-spike / term-inversion dip-buy sleeve on ES/NQ/RTY/YM (16 cells): long at the 16:16 ET px of the signal label, exit after 2 or 5 days; VIX is the 16:15 CBOE close so entry is priced at the 16:16-17 bar.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 40 clean trades): 6. Top cells by clean weekly Sharpe:

| kind   |   thr | sma   |   N |   n |   sharpe |    net |   ypos | eligible   |
|:-------|------:|:------|----:|----:|---------:|-------:|-------:|:-----------|
| spike  | 1.300 | on    |   5 |  12 |    2.983 | 16.604 |      1 | False      |
| inv    | 1.050 | on    |   5 |   7 |    2.632 | 12.395 |      1 | False      |
| inv    | 1.000 | on    |   5 |  18 |    1.915 | 29.668 |      1 | False      |
| inv    | 1.050 | on    |   2 |   7 |    1.512 |  3.180 |      1 | False      |
| inv    | 1.000 | on    |   2 |  27 |    1.381 | 17.132 |      1 | False      |
| spike  | 1.300 | on    |   2 |  15 |    1.284 |  4.586 |      1 | False      |
| inv    | 1.050 | off   |   5 |  24 |    1.249 | 18.467 |      2 | False      |
| spike  | 1.300 | off   |   5 |  16 |    0.980 | 12.399 |      1 | False      |
| inv    | 1.000 | off   |   5 |  40 |    0.807 | 20.602 |      1 | True       |
| spike  | 1.300 | off   |   2 |  24 |    0.458 |  6.192 |      2 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.81; replicate best-eligible median 1.10, p95 1.56; real beats 27% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.185e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.022 | +0.162 | +0.061 | +0.043 | +10.1 | [-0.030, +0.114] | 0.27 | NO |
| 20% | add | +0.029 | +0.317 | +0.110 | +0.070 | +21.0 | [-0.077, +0.210] | 0.27 | NO |
| 30% | add | +0.025 | +0.463 | +0.149 | +0.084 | +31.9 | [-0.140, +0.291] | 0.27 | NO |
| 50% | add | -0.012 | +0.721 | +0.190 | +0.074 | +55.6 | [-0.291, +0.413] | 0.27 | NO |
| 10% | const | +0.023 | +0.179 | +0.067 | +0.047 | +0.2 | [-0.034, +0.125] | 0.27 | NO |
| 20% | const | +0.028 | +0.391 | +0.131 | +0.079 | +1.2 | [-0.107, +0.252] | 0.27 | NO |
| 30% | const | +0.004 | +0.635 | +0.180 | +0.082 | +2.1 | [-0.233, +0.373] | 0.27 | NO |
| 50% | const | -0.165 | +1.129 | +0.121 | -0.069 | +95.8 | [-0.731, +0.559] | 0.27 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 450,091, Sharpe 0.49, maxDD 648,519, worst wk -389,609; H1: net 266,139, Sharpe 2.18, maxDD 90,695, worst wk 0; H2: net 158,948, Sharpe 0.70, maxDD 277,963, worst wk -135,917; all: net 875,178, Sharpe 0.68, maxDD 648,519, worst wk -389,609
Correlation with pair (weekly): clean +0.14, H1 -0.23, H2 -0.11, all +0.06; worst-decile weeks (n=17) corr +0.12, sleeve mean in those weeks $10,387, positive share 0.18.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.49 | 2.94 | 4.46 | -81,724 | -79,616 | 318,593 | -99,855 | 43.8 |
| clean | add 30% | 1.48 | 2.97 | 4.34 | -83,222 | -80,433 | 337,835 | -108,846 | 43.8 |
| clean | const 20% | 1.49 | 2.96 | 4.39 | -65,978 | -64,020 | 262,571 | -83,481 | 43.8 |
| clean | const 30% | 1.46 | 2.94 | 4.13 | -62,321 | -58,537 | 257,924 | -84,284 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.14 | 7.10 | 4.70 | -70,948 | -61,589 | 137,633 | -76,932 | 39.3 |
| H1 | add 30% | 3.29 | 7.64 | 4.89 | -67,617 | -59,368 | 137,633 | -76,932 | 39.3 |
| H1 | const 20% | 3.22 | 7.37 | 4.80 | -55,426 | -48,383 | 110,106 | -61,546 | 39.3 |
| H1 | const 30% | 3.46 | 8.33 | 5.14 | -44,335 | -39,559 | 96,343 | -53,853 | 39.3 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.41 | 5.16 | 3.65 | -79,970 | -74,323 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.44 | 5.36 | 3.72 | -79,970 | -74,323 | 217,425 | -82,524 | 44.4 |
| H2 | const 20% | 2.43 | 5.26 | 3.68 | -63,976 | -59,458 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 2.48 | 5.58 | 3.81 | -55,979 | -52,026 | 152,198 | -57,767 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.93 | 3.92 | 8.98 | -80,828 | -78,805 | 318,593 | -99,855 | 43.5 |
| all | add 30% | 1.94 | 4.00 | 8.72 | -81,827 | -79,334 | 337,835 | -108,846 | 43.5 |
| all | const 20% | 1.93 | 3.97 | 8.85 | -65,062 | -63,256 | 262,571 | -83,481 | 43.5 |
| all | const 30% | 1.94 | 4.04 | 8.31 | -59,996 | -57,146 | 257,924 | -84,284 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.029 / +0.317 / +0.110
- [FAIL] 3 worst week within share: all-in worst week +21.0% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.68 vs p95 1.12 (rank 0.74)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.077, +0.210]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.029 / +0.316 / +0.110
- [PASS] 6 worst-decile corr <=+0.30: +0.12
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section J9); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (68 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 246 | +0.3412 | 0.43 |
| fixed | 246 | +0.3305 | 0.42 |
| scaled | 246 | +0.3347 | 0.43 |

Plateau neighbours (all-in 20% uplift; selected +0.070):
- {'kind': 'inv', 'thr': '1.038', 'sma': 'off', 'N': '5'}: -0.008 (trades 32)
- {'kind': 'inv', 'thr': '1.062', 'sma': 'off', 'N': '5'}: +0.016 (trades 28)
- {'kind': 'inv', 'thr': '1.0', 'sma': 'off', 'N': '4'}: +0.021 (trades 76)
- {'kind': 'inv', 'thr': '1.0', 'sma': 'off', 'N': '6'}: +0.044 (trades 60)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.37, p95 1.12, real 0.68. Standalone Sharpe at 2x slippage 0.68.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 15 | 25 | 2.79 |
| 2014 | 21 | 12 | 0.80 |
| 2015 | 24 | 9 | 0.76 |
| 2016 | 15 | 7 | 0.41 |
| 2017 | 3 | 2 | nan |
| 2018 | 60 | -7 | -0.25 |
| 2019 | 24 | 17 | 1.21 |
| 2020 | 52 | -27 | -0.77 |
| 2021 | 8 | 21 | 1.45 |
| 2022 | 24 | 23 | 2.35 |
| 2024 | 16 | 36 | 3.01 |
| 2025 | 32 | -3 | -0.14 |
| 2026 | 20 | 7 | 1.51 |


DONE J9