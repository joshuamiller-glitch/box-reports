# REPORT K4V2 - confirmation test of the daily walk-forward GBM (pre-registered, PREREG_AUTOPILOT.md BATCH L)
**Verdict: FOUND-PENDING (gates pass, replication short).** Pre-declared cell {'model': 'd2', 'N': 1, 'delta': 0.08, 'mode': 'longonly'}: additive 20% uplift clean/H1/H2/all +0.18/+0.39/+0.19/+0.20; standalone all-in weekly Sharpe 1.43; 267 pair-window trades; gates passed 9/9; replications passed 1/3 countable (R1 newest weeks unavailable). Runtime 0 min, 6-worker pool.

Fill model: entry and exit at the last 1-minute close at or before 16:16 ET of the label, 1 tick/side + $4.36 per contract RT (2x for the slippage test), 1 ADR-dollar of risk per trade, scaled to the pair clean weekly sd, additive and constant-risk framings.

## Clean-span selection over the full 32-cell grid (report)

| model   |   N |   delta | mode      |   n |   sharpe |    net |   ypos | eligible   |
|:--------|----:|--------:|:----------|----:|---------:|-------:|-------:|:-----------|
| d2      |   1 |   0.100 | longshort |  63 |    1.994 | 26.270 |      2 | False      |
| d2      |   1 |   0.100 | longonly  |  63 |    1.994 | 26.270 |      2 | False      |
| d2      |   1 |   0.060 | longonly  | 403 |    1.304 | 51.365 |      3 | True       |
| d2      |   1 |   0.080 | longonly  | 162 |    1.272 | 35.845 |      3 | True       |
| d4      |   1 |   0.100 | longonly  | 263 |    1.193 | 35.274 |      3 | True       |
| d4      |   1 |   0.060 | longonly  | 651 |    1.149 | 45.677 |      3 | True       |
| d4      |   1 |   0.080 | longonly  | 414 |    1.097 | 37.261 |      3 | True       |
| d2      |   1 |   0.060 | longshort | 421 |    1.087 | 44.609 |      2 | True       |
| d4      |   1 |   0.100 | longshort | 315 |    1.050 | 37.557 |      2 | True       |
| d2      |   1 |   0.080 | longshort | 169 |    1.005 | 29.949 |      2 | True       |

Pre-declared cell clean Sharpe vs grid best 1.99; selection-aware null (100 random-entry replicates of the whole grid selection): real best 1.30, replicate median 1.22, p95 1.73, real beats 55% (caveat if < 95%).

## Pair-window results (pre-declared cell)

| share | framing | clean | H1 | H2 | all | worst wk chg % | boot 90% CI | verdict |
|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.101 | +0.203 | +0.100 | +0.110 | +5.5 | [+0.051, +0.176] | NO |
| 20% | add | +0.183 | +0.392 | +0.193 | +0.203 | +11.8 | [+0.091, +0.326] | NO |
| 30% | add | +0.248 | +0.564 | +0.280 | +0.279 | +18.1 | [+0.118, +0.450] | NO |
| 50% | add | +0.329 | +0.848 | +0.430 | +0.382 | +30.6 | [+0.126, +0.649] | NO |
| 10% | const | +0.111 | +0.225 | +0.110 | +0.121 | -4.4 | [+0.056, +0.193] | NO |
| 20% | const | +0.218 | +0.480 | +0.237 | +0.243 | -8.1 | [+0.106, +0.390] | NO |
| 30% | const | +0.307 | +0.756 | +0.380 | +0.352 | -11.7 | [+0.130, +0.583] | NO |
| 50% | const | +0.358 | +1.205 | +0.663 | +0.434 | -19.0 | [-0.036, +0.917] | NO |

Correlation with the pair (weekly): clean +0.10, H1 -0.14, H2 -0.10, all +0.04; worst-decile (n=17) +0.26.

## Insurance metric set

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.64 | 3.33 | 5.82 | -80,799 | -78,740 | 267,055 | -92,240 | 42.9 |
| clean | add 30% | 1.71 | 3.60 | 6.40 | -81,852 | -79,314 | 260,528 | -97,422 | 43.8 |
| clean | const 20% | 1.68 | 3.47 | 6.11 | -65,060 | -63,222 | 211,033 | -75,865 | 43.8 |
| clean | const 30% | 1.77 | 3.92 | 7.19 | -58,244 | -56,037 | 176,495 | -72,860 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.22 | 7.81 | 4.95 | -65,861 | -58,197 | 135,171 | -67,748 | 35.7 |
| H1 | add 30% | 3.39 | 8.71 | 5.35 | -59,987 | -54,281 | 132,228 | -63,156 | 35.7 |
| H1 | const 20% | 3.31 | 8.25 | 5.16 | -50,339 | -44,991 | 106,809 | -52,362 | 35.7 |
| H1 | const 30% | 3.58 | 9.94 | 5.87 | -36,704 | -34,472 | 90,250 | -40,077 | 35.7 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.49 | 5.27 | 3.78 | -79,970 | -76,128 | 217,425 | -82,524 | 44.4 |
| H2 | add 30% | 2.57 | 5.55 | 3.91 | -79,970 | -74,599 | 217,425 | -82,524 | 44.4 |
| H2 | const 20% | 2.53 | 5.41 | 3.84 | -63,976 | -60,291 | 173,940 | -66,020 | 44.4 |
| H2 | const 30% | 2.68 | 5.89 | 4.09 | -55,979 | -51,344 | 152,198 | -57,767 | 41.7 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.06 | 4.28 | 11.40 | -80,221 | -77,115 | 267,055 | -92,240 | 42.3 |
| all | add 30% | 2.13 | 4.60 | 12.38 | -80,923 | -76,893 | 260,528 | -97,422 | 42.9 |
| all | const 20% | 2.10 | 4.44 | 11.89 | -64,458 | -61,566 | 211,033 | -75,865 | 42.9 |
| all | const 30% | 2.21 | 4.98 | 13.71 | -57,278 | -53,790 | 176,495 | -72,860 | 42.9 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.183 / +0.392 / +0.193
- [PASS] 3 worst week within share: all-in worst week +11.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.43 vs p95 1.10 (rank 0.99)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.091, +0.326]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 78% of 9
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.179 / +0.388 / +0.189
- [PASS] 6 worst-decile corr <=+0.30: +0.26
- [PASS] 4 drift-matched (month-stratified) null p95: real 1.43 vs p95 0.62 (rank 1.00, median -0.10)
- [PASS] 4 beta test: alpha weekly Sharpe CI lower >0: beta +0.137; sleeve Sharpe 1.43, always-long basket 0.65, alpha Sharpe 1.22 CI [+0.41, +1.91]

Hyperparameter plateau (exact +-25%, pre-registered): selected all-in uplift +0.203; neighbours:
- {'model': 'd2', 'N': '1', 'delta': '0.06', 'mode': 'longonly'}: +0.333
- {'model': 'd2', 'N': '1', 'delta': '0.1', 'mode': 'longonly'}: +0.127
- {'model': 'd2_t112', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.147
- {'model': 'd2_t188', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.205
- {'model': 'd2_l0375', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.191
- {'model': 'd2_l0625', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.272
- {'model': 'd2_s1', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.221
- {'model': 'd2_s2', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.205
- {'model': 'd2_s3', 'N': '1', 'delta': '0.08', 'mode': 'longonly'}: +0.238

## ERA (walk-forward out-of-sample 2016-2022): positive pre-2023

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 1934 | +0.0373 | 0.57 |
| fixed | 1934 | +0.0269 | 0.42 |
| scaled | 1934 | +0.0307 | 0.47 |

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2016 | 193 | 3 | 0.24 |
| 2017 | 289 | 36 | 2.13 |
| 2018 | 330 | -2 | -0.08 |
| 2019 | 198 | -11 | -0.70 |
| 2020 | 367 | 27 | 1.46 |
| 2021 | 299 | 17 | 1.06 |
| 2022 | 258 | -19 | -1.05 |
| 2023 | 21 | 5 | 2.06 |
| 2024 | 94 | 13 | 0.89 |
| 2025 | 90 | 31 | 2.52 |
| 2026 | 74 | 11 | 1.89 |

## Replication (same sign and >= 50 percent of the pre-declared all-in 20 percent uplift, i.e. >= +0.102)

- R1 newest live weeks: not available (data and pair rows end 2026-10-13, under one new week) - not counted.
- R2 H0: uplift +0.086 -> FAIL
- R3 cross-instrument (trained on NQ+ES without instrument id, traded on RTY+YM; standalone weekly Sharpe 0.81): uplift +0.078 -> FAIL
- R4 alternating months: odd-selected cell model=d2, N=1, delta=0.08, mode=longshort read on even months +0.145; even-selected cell model=d2, N=1, delta=0.06, mode=longonly read on odd months +0.116 -> PASS
- Replications passed: 1 of 3 countable (need 2).

## Executability and margin (NT8)

Signal: after 16:15 ET the model (retrained quarterly offline) is evaluated on the day's features (px at 16:16 ET, VIX/VIX3M/VVIX 16:15 closes, COT percentile from the last Friday release, calendar) and a daily signal file (instrument, side, quantity) is published; an NT8 strategy reads it and sends a market order at 16:16 ET and flattens at 16:16 ET the next trading day (a 1-minute-bar MARKET fill is assumed; 2x slippage tested). NinjaTrader Brokerage via Rithmic, all CME products.

Contracts per signal at 100% pair-equivalent risk (mean / p95 / max) and CME initial margin ASSUMPTIONS (not verified): ES: 7.8/12.0/15.2 (margin $13,000), NQ: 4.2/6.9/7.6 (margin $18,000), RTY: 13.2/17.7/18.9 (margin $8,000), YM: 11.4/15.2/17.2 (margin $10,000). At 20 percent share multiply contracts by 0.2 and at 30 percent by 0.3; worst case all four signals on the same day at 30 percent needs about $171,975 of initial margin.

Caveats: long-only in a rising sample; the drift-matched null and beta test above address it. Features need a COT file (weekly) and a VIX feed (CBOE) at the close; models are retrained offline each quarter (frozen code ap_k_fams.py).

DONE K4V2