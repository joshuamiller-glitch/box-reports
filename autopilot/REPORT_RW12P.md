# REPORT RW12P - confirmation of R12 (K4 with extended features), K4v2 protocol (pre-registered, PREREG_AUTOPILOT.md BATCH R)
**Verdict: LEAD.** Pre-declared cell {'model': 'd2', 'N': 1, 'delta': 0.08, 'mode': 'longonly'}: additive 20% uplift clean/H1/H2/all +0.26/+0.65/+0.40/+0.34; standalone all-in weekly Sharpe 2.01; 225 pair-window trades; gates passed 8/9; replications passed 1/3 countable (R1 newest weeks unavailable). Runtime 0 min, 6-worker pool.

Fill model: entry and exit at the last 1-minute close at or before 16:16 ET of the label, 1 tick/side + $4.36 per contract RT (2x for the slippage test), 1 ADR-dollar of risk per trade, scaled to the pair clean weekly sd, additive and constant-risk framings.

## Clean-span selection over the full 32-cell grid (report)

| model   |   N |   delta | mode      |   n |   sharpe |    net |   ypos | eligible   |
|:--------|----:|--------:|:----------|----:|---------:|-------:|-------:|:-----------|
| d2      |   1 |   0.100 | longonly  |  35 |    1.960 | 17.985 |      2 | False      |
| d4      |   1 |   0.100 | longonly  | 268 |    1.813 | 50.372 |      3 | True       |
| d4      |   1 |   0.080 | longonly  | 460 |    1.805 | 59.625 |      3 | True       |
| d4      |   3 |   0.080 | longonly  | 355 |    1.721 | 80.693 |      3 | True       |
| d2      |   1 |   0.080 | longonly  | 121 |    1.686 | 34.956 |      2 | True       |
| d4      |   3 |   0.100 | longonly  | 291 |    1.607 | 67.315 |      3 | True       |
| d2      |   1 |   0.080 | longshort | 126 |    1.535 | 32.351 |      2 | True       |
| d2      |   1 |   0.060 | longonly  | 376 |    1.479 | 41.295 |      3 | True       |
| d4      |   1 |   0.060 | longonly  | 710 |    1.472 | 60.766 |      3 | True       |
| d4      |   3 |   0.060 | longonly  | 425 |    1.401 | 73.847 |      3 | True       |

Pre-declared cell clean Sharpe vs grid best 1.96; selection-aware null (100 random-entry replicates of the whole grid selection): real best 1.81, replicate median 1.32, p95 1.79, real beats 96% (caveat if < 95%).

## Pair-window results (pre-declared cell)

| share | framing | clean | H1 | H2 | all | worst wk chg % | boot 90% CI | verdict |
|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.142 | +0.338 | +0.209 | +0.180 | +1.9 | [+0.103, +0.264] | NO |
| 20% | add | +0.265 | +0.654 | +0.397 | +0.337 | +4.6 | [+0.191, +0.497] | NO |
| 30% | add | +0.366 | +0.941 | +0.558 | +0.470 | +10.2 | [+0.259, +0.699] | NO |
| 50% | add | +0.512 | +1.402 | +0.800 | +0.664 | +21.4 | [+0.341, +1.013] | NO |
| 10% | const | +0.157 | +0.374 | +0.231 | +0.198 | -8.0 | [+0.113, +0.292] | NO |
| 20% | const | +0.318 | +0.802 | +0.481 | +0.407 | -14.1 | [+0.225, +0.602] | NO |
| 30% | const | +0.468 | +1.255 | +0.726 | +0.605 | -17.8 | [+0.321, +0.916] | INSURANCE |
| 50% | const | +0.642 | +1.926 | +1.024 | +0.841 | -25.3 | [+0.310, +1.411] | INSURANCE |

Correlation with the pair (weekly): clean +0.08, H1 -0.17, H2 -0.05, all +0.03; worst-decile (n=17) -0.07.

## Insurance metric set

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.72 | 3.45 | 6.54 | -80,973 | -79,044 | 248,770 | -86,309 | 41.9 |
| clean | add 30% | 1.83 | 3.76 | 7.51 | -82,113 | -79,580 | 236,580 | -90,934 | 41.9 |
| clean | const 20% | 1.78 | 3.61 | 7.07 | -65,235 | -63,450 | 192,748 | -70,897 | 41.9 |
| clean | const 30% | 1.93 | 4.15 | 8.29 | -58,505 | -56,188 | 166,303 | -67,816 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.48 | 9.60 | 4.94 | -53,225 | -49,077 | 145,826 | -63,581 | 39.3 |
| H1 | add 30% | 3.77 | 11.84 | 5.49 | -49,549 | -44,046 | 142,882 | -56,227 | 39.3 |
| H1 | const 20% | 3.63 | 10.68 | 5.21 | -41,110 | -36,609 | 115,483 | -47,923 | 39.3 |
| H1 | const 30% | 4.08 | 14.82 | 6.22 | -31,375 | -27,743 | 97,368 | -32,741 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.69 | 6.15 | 4.14 | -79,970 | -73,348 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.85 | 6.82 | 4.45 | -79,970 | -73,348 | 217,425 | -82,524 | 41.7 |
| H2 | const 20% | 2.78 | 6.50 | 4.30 | -63,976 | -58,678 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 3.02 | 7.55 | 4.86 | -55,979 | -51,344 | 152,198 | -57,767 | 38.9 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.19 | 4.64 | 13.06 | -80,338 | -77,106 | 248,770 | -86,309 | 42.3 |
| all | add 30% | 2.33 | 5.11 | 14.92 | -81,098 | -77,148 | 236,580 | -90,934 | 41.7 |
| all | const 20% | 2.26 | 4.88 | 14.06 | -64,574 | -61,701 | 192,748 | -70,897 | 42.3 |
| all | const 30% | 2.46 | 5.66 | 16.38 | -57,452 | -54,221 | 166,303 | -67,816 | 41.1 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.265 / +0.654 / +0.397
- [PASS] 3 worst week within share: all-in worst week +4.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 2.01 vs p95 0.92 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.191, +0.497]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 22% of 9
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.260 / +0.649 / +0.391
- [PASS] 6 worst-decile corr <=+0.30: -0.07
- [PASS] 4 drift-matched (month-stratified) null p95: real 2.01 vs p95 0.95 (rank 1.00, median 0.28)
- [PASS] 4 beta test: alpha weekly Sharpe CI lower >0: beta +0.093; sleeve Sharpe 2.01, always-long basket 0.65, alpha Sharpe 1.87 CI [+1.10, +2.58]

Hyperparameter plateau (exact +-25%, pre-registered): selected all-in uplift +0.337; neighbours:
- {'model': 'd2', 'N': '1', 'delta': '0.06', 'mode': 'longonly'}: +0.357
- {'model': 'd2', 'N': '1', 'delta': '0.1', 'mode': 'longonly'}: +0.121
- {'model': 'd2_t112', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.214
- {'model': 'd2_t188', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.344
- {'model': 'd2_l0375', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.222
- {'model': 'd2_l0625', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.248
- {'model': 'd2_s1', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.158
- {'model': 'd2_s2', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.241
- {'model': 'd2_s3', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.135

## ERA (walk-forward out-of-sample 2016-2022): positive pre-2023

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 2084 | +0.0156 | 0.21 |
| fixed | 2084 | +0.0043 | 0.06 |
| scaled | 2084 | +0.0091 | 0.12 |

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 224 | -3 | -0.14 |
| 2017 | 354 | 29 | 1.59 |
| 2018 | 397 | -13 | -0.46 |
| 2019 | 249 | -4 | -0.23 |
| 2020 | 284 | -6 | -0.20 |
| 2021 | 329 | 16 | 0.85 |
| 2022 | 247 | -10 | -0.54 |
| 2023 | 20 | 0 | 0.28 |
| 2024 | 64 | 9 | 0.90 |
| 2025 | 75 | 36 | 3.03 |
| 2026 | 79 | 21 | 2.75 |

## Replication (same sign and >= 50 percent of the pre-declared all-in 20 percent uplift, i.e. >= +0.169)

- R1 newest live weeks: not available (data and pair rows end 2026-10-13, under one new week) - not counted.
- R2 H0: uplift +0.021 -> FAIL
- R3 cross-instrument (trained on NQ+ES without instrument id, traded on RTY+YM; standalone weekly Sharpe 1.21): uplift +0.126 -> FAIL
- R4 alternating months: odd-selected cell model=d2, N=1, delta=0.08, mode=longonly read on even months +0.372; even-selected cell model=d2, N=1, delta=0.08, mode=longonly read on odd months +0.262 -> PASS
- Replications passed: 1 of 3 countable (need 2).

## Executability and margin (NT8)

Signal: after 16:15 ET the model (retrained quarterly offline) is evaluated on the day's features (px at 16:16 ET, VIX/VIX3M/VVIX 16:15 closes, COT percentile from the last Friday release, calendar) and a daily signal file (instrument, side, quantity) is published; an NT8 strategy reads it and sends a market order at 16:16 ET and flattens at 16:16 ET the next trading day (a 1-minute-bar MARKET fill is assumed; 2x slippage tested). NinjaTrader Brokerage via Rithmic, all CME products.

Contracts per signal at 100% pair-equivalent risk (mean / p95 / max) and CME initial margin ASSUMPTIONS (not verified): ES: 10.9/17.8/19.8 (margin $13,000), NQ: 5.4/10.3/10.8 (margin $18,000), RTY: 17.1/25.3/29.7 (margin $8,000), YM: 15.2/22.4/26.7 (margin $10,000). At 20 percent share multiply contracts by 0.2 and at 30 percent by 0.3; worst case all four signals on the same day at 30 percent needs about $253,006 of initial margin.

Caveats: long-only in a rising sample; the drift-matched null and beta test above address it. Features need a COT file (weekly) and a VIX feed (CBOE) at the close; models are retrained offline each quarter (frozen code ap_k_fams.py).

DONE RW12P