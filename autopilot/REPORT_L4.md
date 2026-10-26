# REPORT L4
**Verdict: NO** (1/7 measured gates pass). Selected cell model=d4, N=10, delta=0.08, mode=longshort; additive @20% clean/H1/H2 +0.08/+0.11/+0.06; standalone all-in weekly Sharpe 0.66 (2013-26 0.25, dev 2013-22 0.12); pair-window trades 284. Runtime 0.2 min (+selection 0.0 min). 6-worker pool.

L4 weekly-horizon (5 and 10 day) walk-forward GBM on ES/NQ/RTY/YM (16 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 60 clean trades): 16. Top cells by clean weekly Sharpe:

| model   |   N |   delta | mode      |   n |   sharpe |    net |   ypos | eligible   |
|:--------|----:|--------:|:----------|----:|---------:|-------:|-------:|:-----------|
| d4      |  10 |   0.080 | longshort | 183 |    0.691 | 47.198 |      3 | True       |
| d2      |  10 |   0.040 | longshort | 198 |    0.657 | 51.568 |      3 | True       |
| d2      |  10 |   0.080 | longonly  | 171 |    0.614 | 44.954 |      2 | True       |
| d4      |   5 |   0.040 | longshort | 367 |    0.579 | 40.836 |      1 | True       |
| d4      |  10 |   0.040 | longshort | 197 |    0.571 | 39.069 |      3 | True       |
| d4      |  10 |   0.040 | longonly  | 176 |    0.570 | 42.822 |      3 | True       |
| d4      |   5 |   0.080 | longonly  | 266 |    0.498 | 30.721 |      2 | True       |
| d2      |  10 |   0.040 | longonly  | 192 |    0.469 | 38.047 |      3 | True       |
| d4      |   5 |   0.040 | longonly  | 337 |    0.428 | 32.600 |      2 | True       |
| d4      |  10 |   0.080 | longonly  | 163 |    0.410 | 29.720 |      3 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.69; replicate best-eligible median 1.14, p95 1.59; real beats 3% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.35e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.046 | +0.069 | +0.039 | +0.040 | +10.5 | [-0.042, +0.123] | 0.20 | NO |
| 20% | add | +0.077 | +0.107 | +0.064 | +0.064 | +21.8 | [-0.098, +0.227] | 0.20 | NO |
| 30% | add | +0.094 | +0.111 | +0.076 | +0.071 | +35.1 | [-0.166, +0.308] | 0.20 | NO |
| 50% | add | +0.095 | +0.018 | +0.067 | +0.047 | +62.8 | [-0.336, +0.420] | 0.20 | NO |
| 10% | const | +0.050 | +0.075 | +0.042 | +0.044 | +0.6 | [-0.048, +0.136] | 0.20 | NO |
| 20% | const | +0.087 | +0.114 | +0.072 | +0.069 | +2.6 | [-0.130, +0.269] | 0.20 | NO |
| 30% | const | +0.098 | +0.065 | +0.075 | +0.060 | +7.1 | [-0.272, +0.385] | 0.20 | NO |
| 50% | const | +0.002 | -0.529 | -0.071 | -0.123 | +16.0 | [-0.761, +0.492] | 0.20 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 685,147, Sharpe 0.75, maxDD 456,205, worst wk -166,114; H1: net 11,968, Sharpe 0.05, maxDD 239,036, worst wk -135,841; H2: net 217,236, Sharpe 0.85, maxDD 308,300, worst wk -81,738; all: net 914,351, Sharpe 0.66, maxDD 456,205, worst wk -166,114
Correlation with pair (weekly): clean +0.14, H1 -0.26, H2 +0.11, all +0.08; worst-decile weeks (n=17) corr +0.16, sleeve mean in those weeks $4,109, positive share 0.53.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.54 | 2.91 | 4.68 | -93,490 | -86,385 | 313,491 | -100,513 | 42.9 |
| clean | add 30% | 1.55 | 2.92 | 4.65 | -101,503 | -91,346 | 330,181 | -111,530 | 41.9 |
| clean | const 20% | 1.55 | 2.92 | 4.66 | -77,997 | -71,092 | 257,469 | -84,655 | 42.9 |
| clean | const 30% | 1.56 | 2.90 | 4.62 | -78,264 | -68,843 | 246,148 | -88,352 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.94 | 6.48 | 3.83 | -71,342 | -61,496 | 155,843 | -78,281 | 39.3 |
| H1 | add 30% | 2.94 | 6.56 | 3.62 | -68,208 | -59,229 | 164,949 | -78,956 | 35.7 |
| H1 | const 20% | 2.94 | 6.53 | 3.72 | -55,820 | -48,290 | 128,317 | -62,895 | 35.7 |
| H1 | const 30% | 2.89 | 6.60 | 3.39 | -44,926 | -39,892 | 123,659 | -55,876 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.36 | 5.03 | 3.63 | -80,545 | -77,327 | 221,886 | -83,279 | 41.7 |
| H2 | add 30% | 2.37 | 5.17 | 3.69 | -82,606 | -78,829 | 224,116 | -83,657 | 41.7 |
| H2 | const 20% | 2.37 | 5.10 | 3.66 | -64,586 | -62,463 | 178,401 | -66,775 | 41.7 |
| H2 | const 30% | 2.37 | 5.32 | 3.76 | -61,197 | -56,532 | 158,889 | -63,494 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.92 | 3.77 | 9.15 | -89,590 | -82,947 | 313,491 | -100,513 | 42.3 |
| all | add 30% | 1.93 | 3.78 | 8.96 | -95,441 | -86,401 | 330,181 | -111,530 | 41.1 |
| all | const 20% | 1.92 | 3.78 | 9.05 | -73,943 | -67,739 | 257,469 | -84,655 | 41.7 |
| all | const 30% | 1.92 | 3.75 | 8.75 | -72,990 | -64,042 | 246,148 | -88,352 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.077 / +0.107 / +0.064
- [FAIL] 3 worst week within share: all-in worst week +21.8% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.66 vs p95 0.88 (rank 0.82)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.098, +0.227]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.074 / +0.105 / +0.062
- [PASS] 6 worst-decile corr <=+0.30: +0.16
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section L4); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (284 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 641 | +0.0613 | 0.15 |
| fixed | 641 | +0.0497 | 0.12 |
| scaled | 641 | +0.0548 | 0.13 |

Plateau neighbours (all-in 20% uplift; selected +0.064):
- {'model': 'd4', 'N': '10', 'delta': '0.06', 'mode': 'longshort'}: +0.021 (trades 300)
- {'model': 'd4', 'N': '10', 'delta': '0.1', 'mode': 'longshort'}: +0.042 (trades 267)
- {'model': 'd4', 'N': '8', 'delta': '0.08', 'mode': 'longshort'}: -0.044 (trades 340)
- {'model': 'd4', 'N': '12', 'delta': '0.08', 'mode': 'longshort'}: +0.030 (trades 242)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.35, p95 0.88, real 0.66. Standalone Sharpe at 2x slippage 0.65.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 75 | -14 | -0.49 |
| 2017 | 81 | 39 | 1.60 |
| 2018 | 96 | -5 | -0.11 |
| 2019 | 100 | 48 | 1.54 |
| 2020 | 94 | -7 | -0.13 |
| 2021 | 99 | 22 | 0.62 |
| 2022 | 96 | -50 | -1.47 |
| 2023 | 85 | 7 | 0.23 |
| 2024 | 90 | 30 | 0.87 |
| 2025 | 93 | 3 | 0.09 |
| 2026 | 64 | 22 | 1.01 |


## Beta / drift test (report): regression of the sleeve's daily P&L on the always-long basket of the same instruments (unit risk), 2023-08..2026-10: beta +0.540; sleeve weekly Sharpe 0.66; always-long basket 0.65; ALPHA weekly Sharpe 0.34, bootstrap 90% CI [-0.62, +1.22] (alpha CI includes zero).

DONE L4