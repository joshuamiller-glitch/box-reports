# REPORT L8
**Verdict: NO** (2/7 measured gates pass). Selected cell model=d4, delta=0.04, mode=longonly; additive @20% clean/H1/H2 +0.12/-0.18/+0.11; standalone all-in weekly Sharpe 0.56 (2013-26 -0.26, dev 2013-22 -0.69); pair-window trades 3014. Runtime 0.0 min (+selection 0.0 min). 6-worker pool.

L8 intraday walk-forward GBM on NQ/ES with cross-asset 60-min leaders and VIX state, 60-minute horizon (8 cells).


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 100 clean trades): 8. Top cells by clean weekly Sharpe:

| model   |   delta | mode      |    n |   sharpe |     net |   ypos | eligible   |
|:--------|--------:|:----------|-----:|---------:|--------:|-------:|:-----------|
| d4      |   0.040 | longonly  | 1907 |    0.794 |  12.170 |      3 | True       |
| d4      |   0.040 | longshort | 2168 |    0.313 |   5.670 |      2 | True       |
| d2      |   0.040 | longshort | 1365 |    0.192 |   2.594 |      2 | True       |
| d2      |   0.040 | longonly  | 1292 |   -0.072 |  -0.927 |      1 | True       |
| d4      |   0.020 | longshort | 3434 |   -0.210 |  -4.769 |      2 | True       |
| d4      |   0.020 | longonly  | 2997 |   -0.322 |  -6.438 |      1 | True       |
| d2      |   0.020 | longonly  | 3051 |   -0.397 |  -8.843 |      0 | True       |
| d2      |   0.020 | longshort | 3248 |   -0.409 | -10.513 |      0 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 0.79; replicate best-eligible median 0.33, p95 0.98; real beats 90% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=5.94e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.067 | -0.066 | +0.062 | +0.042 | +6.8 | [-0.047, +0.130] | 0.42 | NO |
| 20% | add | +0.118 | -0.177 | +0.107 | +0.065 | +20.2 | [-0.112, +0.238] | 0.42 | NO |
| 30% | add | +0.153 | -0.333 | +0.138 | +0.070 | +33.6 | [-0.191, +0.325] | 0.42 | NO |
| 50% | add | +0.181 | -0.751 | +0.163 | +0.037 | +60.4 | [-0.378, +0.438] | 0.42 | NO |
| 10% | const | +0.074 | -0.076 | +0.068 | +0.045 | -2.6 | [-0.054, +0.143] | 0.42 | NO |
| 20% | const | +0.138 | -0.250 | +0.124 | +0.069 | +1.5 | [-0.150, +0.284] | 0.42 | NO |
| 30% | const | +0.177 | -0.590 | +0.159 | +0.054 | +5.6 | [-0.310, +0.409] | 0.42 | NO |
| 50% | const | +0.110 | -1.868 | +0.109 | -0.166 | +13.7 | [-0.857, +0.502] | 0.42 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 722,903, Sharpe 0.79, maxDD 566,971, worst wk -148,091; H1: net -337,884, Sharpe -1.35, maxDD 585,300, worst wk -163,661; H2: net 414,401, Sharpe 1.49, maxDD 323,372, worst wk -134,369; all: net 799,420, Sharpe 0.56, maxDD 626,630, worst wk -163,661
Correlation with pair (weekly): clean +0.03, H1 -0.34, H2 +0.28, all +0.02; worst-decile weeks (n=17) corr -0.28, sleeve mean in those weeks $2,601, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.58 | 2.99 | 5.85 | -85,426 | -81,883 | 252,182 | -99,189 | 42.9 |
| clean | add 30% | 1.61 | 3.04 | 6.49 | -89,795 | -84,171 | 238,218 | -110,254 | 41.9 |
| clean | const 20% | 1.60 | 3.02 | 6.16 | -70,088 | -66,422 | 196,160 | -83,777 | 41.9 |
| clean | const 30% | 1.64 | 3.06 | 6.57 | -66,788 | -61,074 | 174,752 | -87,137 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.65 | 5.32 | 3.88 | -73,200 | -69,615 | 135,732 | -77,612 | 39.3 |
| H1 | add 30% | 2.49 | 4.88 | 3.25 | -75,092 | -71,408 | 151,647 | -77,952 | 39.3 |
| H1 | const 20% | 2.58 | 5.10 | 3.58 | -58,048 | -56,409 | 113,663 | -62,225 | 39.3 |
| H1 | const 30% | 2.24 | 4.28 | 2.55 | -57,122 | -51,599 | 123,376 | -59,371 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.40 | 5.03 | 3.56 | -86,931 | -80,333 | 236,890 | -89,146 | 36.1 |
| H2 | add 30% | 2.43 | 5.14 | 3.34 | -90,479 | -84,551 | 265,192 | -95,146 | 36.1 |
| H2 | const 20% | 2.42 | 5.09 | 3.45 | -70,964 | -65,574 | 200,833 | -73,717 | 36.1 |
| H2 | const 30% | 2.45 | 5.24 | 3.11 | -66,841 | -63,838 | 211,106 | -72,002 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.92 | 3.74 | 11.28 | -85,082 | -80,821 | 252,182 | -99,189 | 41.1 |
| all | add 30% | 1.93 | 3.73 | 11.03 | -88,911 | -83,213 | 265,192 | -110,254 | 40.5 |
| all | const 20% | 1.93 | 3.74 | 11.49 | -69,597 | -65,524 | 200,833 | -83,777 | 40.5 |
| all | const 30% | 1.91 | 3.69 | 10.04 | -66,628 | -61,260 | 211,106 | -87,137 | 42.9 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.118 / -0.177 / +0.107
- [FAIL] 3 worst week within share: all-in worst week +20.2% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 0.56 vs p95 0.26 (rank 0.99)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.112, +0.238]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.001 / -0.303 / +0.038
- [PASS] 6 worst-decile corr <=+0.30: -0.28
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section L8); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3014 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): gross-positive, cost-negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 6741 | +0.0065 | 0.72 |
| fixed | 6741 | -0.0062 | -0.69 |
| scaled | 6741 | +0.0004 | 0.05 |

Plateau neighbours (all-in 20% uplift; selected +0.065):
- {'model': 'd4', 'delta': '0.03', 'mode': 'longonly'}: +0.017 (trades 4018)
- {'model': 'd4', 'delta': '0.05', 'mode': 'longonly'}: -0.069 (trades 2067)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.51, p95 0.26, real 0.56. Standalone Sharpe at 2x slippage 0.00.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 1022 | -18 | -1.86 |
| 2017 | 968 | -15 | -1.70 |
| 2018 | 1047 | -15 | -1.43 |
| 2019 | 860 | 5 | 0.66 |
| 2020 | 947 | 3 | 0.52 |
| 2021 | 1010 | 11 | 1.30 |
| 2022 | 887 | -13 | -1.59 |
| 2023 | 983 | 8 | 1.16 |
| 2024 | 928 | 1 | 0.08 |
| 2025 | 976 | 5 | 0.68 |
| 2026 | 728 | 5 | 0.90 |


DONE L8