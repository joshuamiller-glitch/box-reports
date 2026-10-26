# REPORT FOURTH-BOOK (trackFOURTH, 2026-10-23/24) - steps 0-4; research only, nothing live, no purchases, UNTOUCHED unread
Prereg: l2vast/PREREG_FOURTH_BOOK.md (sha256 c1fb1f30c6c51906b860c02bd4fddb98736b78956651f097fd63a8b86c700463), ADDENDUM1 (81f26c7d3...), ADDENDUM2 (91f4c6c0...). All frozen before the cells they govern were scored (DECISIONS.md). F_P 3,561 -> 3,580 (families: 0.3, 0.4, C1-C7, R1-R6, switch a-d); best-of-F line 0.95^(1/3580) = 0.999986. Code and every table: outputs/l2vast/fourth/ (out/*.csv). Format: weekly figures at 14/14-equivalent, label weeks; IS 2023-02-10..2024-01-31 (52 wk), WF 2024-02..2026-10-16 (142 wk), L8W 2026-W35..W42, WF-pre 2024-02..2025-06, HOLDOUT 2025-07..2026-10 (finalists only); SD, maxDD on the daily path, worst week, weekly Sharpe (sqrt 52), trades/wk, avg/max lots. No cumulative totals.

## 0. Answer
1. **The switched system (range book + compression switch) does not beat the benchmark.** Only 1 of 56 Step 3 cells (2 of 112 counting both credit settings of the same base-A cell) beats its own benchmark (live spec BM1, user Set B BM2) on weekly mean AND maxDD in the walk-forward, and the same cell in the last 8 weeks: (d) breakout re-arm on the predicted-quiet session flag, base A: WF +3.4k/wk with maxDD -16.1k, L8W +0.5k/-7.2k (gates a and b pass). It fails gate c (family-wise shuffled-state rank .735 on the mean), gate d (bootstrap 90% CI of the weekly gain [-5.3k, +12.1k]) and the frozen holdout 2025-07..2026-10 (-0.4k/wk, maxDD +17.3k); its gain is a MAPPED break sleeve that shrinks further in the direct L2 replay (section 6). Random shuffled states pass gate (a) in 0.72 of 56 cells per world, so one passer is at chance level. It is not a LEAD. No FOURTH_BOOK_SPEC.md is written; no frozen-leads JSON / shadow script is issued.
2. **The range book does not pay.** None of the six books (R1 VWAP-band, R2 session-range boundary, R3 BB/KC 5-min, R4 HM-anchor, R5 opening range, R6 prior-session range) pays after cost in all sessions (108/108 cells negative; gross points before ANY cost are also negative in all 54 simulations), none pays in predicted-quiet sessions (0/108 positive in IS and in WF) and none in the real-time compression state in IS (8/108 in WF, all small). They DO pay in the pair's failing sessions (ex-post view: 87/108 cells positive in WF; R2 session-range boundary fade +762 $/trade at 8 lots, 6.6 trades/wk, +5.0k/wk), and that is not chance (500 shifted failing-session flags: rank 1.000) - but a failing session is only known afterwards. All six books are dropped by the pre-registered rule.
3. **Where the pair fails (Step 0):** in NORMAL-volatility, NON-DIRECTIONAL sessions (path efficiency |close-open|/path .032 vs .051 for the rest, AUC .38; RV AUC .50; range 136 vs 162 pts; VIX / events / day of week |AUC-0.5| < .07), not in compressed sessions. The failure is predictable only a little: AUC .59-.61 pre-open (top-decile precision .39-.44 vs 35% base), .66 after 60 minutes (NY .74). The vol forecaster predicts predicted-compression well (AUC .83-.86, calibrated) but the pair earns about the same in predicted-quiet and predicted-wide sessions.
4. **A real-time RELATIVE-compression state (VWAP-band width / same-clock 20-day median < 0.8, hysteresis 1.0) does mark hours where the pair earns ~0** (WF net per trade -53 ON vs +964 OFF, t 2.1; IS -1,252 vs +1,096, t 2.4) - but L8W reverses (+1,089 vs +776) and standing the pair down in that state (hard variant a) lowers the weekly mean by 5k-20k and raises WF maxDD by 25k-740k in every cell.
5. **Caveat that governs all maxDD comparisons:** the live benchmark's WF maxDD (401k) sits at the favourable tail of its own perturbation distribution: dropping a random 10% of entries raises it by +53k on average (random 30%: +193k +-200k). No overlay lowers WF maxDD except two (d) cells ((d) SA and (d) BOTH-120, base A: -16.1k and -6.5k), which is why the shuffled-state null is the real test.

## 1. Benchmarks (reproduced bit for bit before any cell; firmlib, $4.84 RT, corrected P9 points, S113 size cost)
* BM1 (corrected P9 14/14 live spec). As quoted by you (ds2lib, $4.36): IS 13.9k / WF 24.8k, SD 104.2k, maxDD 399k, worst -137k / L8W 34.5k, maxDD 267k. Restated at $4.84 (same engine as every cell, FIRM V4): IS 13.7k / SD 95.9k / maxDD 407.3k / worst -136.3k / Sh 1.03 / 27 tr/wk / lots 14.0/14; WF 25.0k / SD 104.5k / maxDD 401.3k / worst -137.1k / Sh 1.72 / 36 tr/wk / lots 14.0/14; L8W 34.2k / SD 109.4k / maxDD 267.1k / worst -98.9k / Sh 2.25 / 40 tr/wk / lots 14.0/14.
* BM2 (Set B: combined cap removed, week floor 12R, lots 14/10/10, give-back 2R keep 50%; reproduces FIRM V4 W4 and FWD_AB_SETS): IS 11.2k / SD 83.6k / maxDD 368.3k / worst -201.9k / Sh 0.97 / 33 tr/wk / lots 11.1/14; WF 34.2k / SD 106.9k / maxDD 317.1k / worst -188.8k / Sh 2.31 / 45 tr/wk / lots 11.6/14; L8W 58.2k / SD 125.1k / maxDD 206.1k / worst -94.8k / Sh 3.35 / 50 tr/wk / lots 11.8/14.
* Additional windows (both benchmarks): WFPRE BM1 17.5k/401.3k, BM2 28.7k/317.1k; HOLD BM1 32.8k/267.1k, BM2 39.8k/254.2k
* No-lookahead: every feature/state/level builder is a pure function of its arrays; truncation- and future-poison-invariance tests (bitwise): RT state features 104 checks, range-book levels 192, session features 684, ALL 0 mismatches (out/trunc_*.log). The test found one genuine look-ahead (global price centering in the VWAP-band feature), fixed before the final run; all of Steps 1-3 were re-run, the selected state did not change. Forecasts (forecast_table) and book state (STATE_NQ) are the existing walk-forward / as-of tables.
## 2. STEP 0 - where the trend pair fails (measured, no theory)
### 0.1 / 0.2 session labels and the failing sessions (2,859 sessions ASIA/LONDON/NY plus NY-AM/NY-PM sub-sessions, 2023-02..2026-10; pair = corrected P9 14/14, live spec, session P&L by ENTRY session; failing = bottom quartile of P&L within type AND P&L<0)
| session   |    n |   q25 $ |   failing n |   mean P&L failing |   rest |   top quartile |   P&L<0 |   no trades |
|:----------|-----:|--------:|------------:|-------------------:|-------:|---------------:|--------:|------------:|
| ASIA      |  954 |  -19842 |         239 |             -40251 |  17249 |          41672 |     425 |          59 |
| LONDON    |  954 |  -13786 |         240 |             -26683 |  10215 |          32939 |     372 |         311 |
| NY        |  951 |   -4373 |         238 |             -24102 |   8963 |          29842 |     274 |         461 |
| NYAM      |  951 |    -608 |         238 |             -21006 |   7452 |          25944 |     261 |         485 |
| NYPM      |  951 |       0 |         142 |             -14275 |   2926 |          17281 |     142 |         672 |
| ALL3      | 2859 |  -12675 |         717 |             -30349 |  12146 |          36166 |    1071 |         831 |

Single-feature AUC of "failing" (0.5 = no information; 90% week-block bootstrap intervals in out/step0_features.csv) and Cohen d, ex-post path features and known-before-open features:
| feature                               |   ASIA |   LONDON |    NY |    NYAM |    NYPM |   ALL3 | ALL3 failing / rest / top-quartile (median)   |   Cohen d (ALL3) |
|:--------------------------------------|-------:|---------:|------:|--------:|--------:|-------:|:----------------------------------------------|-----------------:|
| range (pts)                           |  0.494 |    0.448 | 0.354 |   0.366 |   0.429 |  0.447 | 136 / 162 / 158                               |           -0.216 |
| range / ATR20                         |  0.496 |    0.432 | 0.409 |   0.423 |   0.487 |  0.457 | 0.408 / 0.469 / 0.452                         |           -0.161 |
| realised vol (1-min)                  |  0.513 |    0.506 | 0.440 |   0.440 |   0.489 |  0.497 | 0.00432 / 0.00441 / 0.00378                   |           -0.052 |
| 20-pt swing count                     |  0.505 |    0.519 | 0.426 |   0.436 |   0.455 |  0.492 | 14 / 14 / 11                                  |           -0.094 |
| 40-pt swing count                     |  0.519 |    0.527 | 0.432 |   0.460 |   0.467 |  0.501 | 4 / 4 / 3                                     |           -0.085 |
| 60-pt swing count                     |  0.504 |    0.539 | 0.450 |   0.450 |   0.480 |  0.504 | 2 / 2 / 1                                     |           -0.061 |
| max trend run (rev 20)                |  0.510 |    0.480 | 0.421 |   0.412 |   0.453 |  0.478 | 95.2 / 100 / 96.5                             |           -0.091 |
| max trend run (rev 40)                |  0.488 |    0.464 | 0.388 |   0.382 |   0.444 |  0.458 | 113 / 125 / 122                               |           -0.155 |
| path efficiency |close-open|/path     |  0.400 |    0.385 | 0.360 |   0.374 |   0.396 |  0.381 | 0.032 / 0.0507 / 0.0665                       |           -0.408 |
| |net move| (pts)                      |  0.419 |    0.398 | 0.344 |   0.354 |   0.401 |  0.392 | 46.5 / 70.8 / 85.5                            |           -0.320 |
| time within +-30 pts of open          |  0.531 |    0.544 | 0.648 |   0.613 |   0.590 |  0.564 | 0.435 / 0.316 / 0.263                         |            0.186 |
| ST+HM flip events                     |  0.511 |    0.508 | 0.553 |   0.545 |   0.547 |  0.522 | 20 / 20 / 19                                  |            0.070 |
| ST flips                              |  0.510 |    0.515 | 0.567 |   0.562 |   0.553 |  0.527 | 13 / 13 / 11                                  |            0.089 |
| HM flips                              |  0.498 |    0.485 | 0.525 |   0.499 |   0.527 |  0.503 | 8 / 8 / 8                                     |            0.004 |
| trades (mechanical)                   |  0.574 |    0.670 | 0.770 |   0.804 |   0.906 |  0.662 | 2 / 2 / 3                                     |            0.434 |
| stop-outs (mechanical)                |  0.918 |    0.849 | 0.829 |   0.842 |   0.805 |  0.854 | 2 / 0 / 0                                     |            1.361 |
| day of week                           |  0.489 |    0.515 | 0.466 |   0.473 |   0.488 |  0.490 | 2 / 2 / 2                                     |           -0.035 |
| VIX (prior day)                       |  0.504 |    0.479 | 0.447 |   0.437 |   0.470 |  0.477 | 16.3 / 16.5 / 16.4                            |           -0.090 |
| VIX 5-day change                      |  0.518 |    0.452 | 0.435 |   0.442 |   0.442 |  0.469 | -0.25 / -0.06 / -0.06                         |           -0.074 |
| VIX3M - VIX                           |  0.494 |    0.506 | 0.541 |   0.545 |   0.515 |  0.514 | 2.19 / 2.16 / 2.16                            |            0.053 |
| pair P&L, trades closed in prior 24 h |  0.491 |    0.511 | 0.470 | nan     | nan     |  0.490 | 0 / 0 / 0                                     |           -0.007 |
| stops closed in prior 24 h            |  0.534 |    0.528 | 0.533 | nan     | nan     |  0.532 | 2 / 1 / 2                                     |            0.069 |
| consecutive stops at open             |  0.505 |    0.527 | 0.514 | nan     | nan     |  0.515 | 0 / 0 / 0                                     |           -0.025 |
| prior-session range/ATR               |  0.544 |    0.451 | 0.449 | nan     | nan     |  0.482 | 0.43 / 0.461 / 0.548                          |           -0.005 |
| prior-session RV                      |  0.510 |    0.467 | 0.388 | nan     | nan     |  0.463 | 0.00395 / 0.00454 / 0.00523                   |           -0.078 |
| FOMC/CPI/NFP/PCE day                  |  0.501 |    0.532 | 0.494 |   0.483 |   0.528 |  0.509 | 0 / 0 / 0                                     |            0.050 |
| ATR20 percentile                      |  0.499 |    0.546 | 0.452 | nan     | nan     |  0.499 | 0.688 / 0.695 / 0.687                         |           -0.007 |
| overnight gap / ATR                   |  0.488 |    0.486 | 0.509 | nan     | nan     |  0.504 | 0.00185 / 0.00176 / 0.00395                   |           -0.046 |

Failing share by calendar / VIX (fail share of all three session types = 25.1%; binomial p vs the other days, 9 event tests, no multiplicity correction):
| calendar         |   sessions |   fail_share |   fail_share_other |   mean_pnl_on |   mean_pnl_other |   binom_p |
|:-----------------|-----------:|-------------:|-------------------:|--------------:|-----------------:|----------:|
| FOMC day         |         87 |        0.310 |              0.249 |     -1854.834 |         1594.073 |     0.214 |
| CPI day          |        132 |        0.356 |              0.246 |     -3375.967 |         1724.616 |     0.004 |
| NFP day          |        127 |        0.165 |              0.255 |      5151.970 |         1318.850 |     0.019 |
| PCE day          |        128 |        0.258 |              0.250 |      2942.296 |         1421.013 |     0.839 |
| opex day         |        132 |        0.235 |              0.252 |      4197.867 |         1358.006 |     0.763 |
| month-end        |        128 |        0.281 |              0.249 |      -545.681 |         1584.492 |     0.414 |
| quarter-end      |         42 |        0.286 |              0.250 |      -190.814 |         1514.169 |     0.594 |
| half-day         |         23 |        0.087 |              0.252 |      9722.704 |         1422.347 |     0.090 |
| roll week        |        135 |        0.163 |              0.255 |      4201.500 |         1354.698 |     0.013 |
| Monday           |        570 |        0.249 |            nan     |      2420.462 |          nan     |   nan     |
| Tuesday          |        576 |        0.264 |            nan     |       814.551 |          nan     |   nan     |
| Wednesday        |        570 |        0.260 |            nan     |       569.042 |          nan     |   nan     |
| Thursday         |        572 |        0.247 |            nan     |      1502.809 |          nan     |   nan     |
| Friday           |        571 |        0.235 |            nan     |      2144.649 |          nan     |   nan     |
| VIX tercile low  |        954 |        0.263 |            nan     |      1316.749 |          nan     |   nan     |
| VIX tercile mid  |        955 |        0.265 |            nan     |      1760.953 |          nan     |   nan     |
| VIX tercile high |        948 |        0.225 |            nan     |      1371.764 |          nan     |   nan     |
CPI days are the one calendar effect that stands out (36% failing vs 25%, mean session P&L -3.4k vs +1.7k, binomial p 0.004, n 132 sessions; it is a pair-side effect, not a volatility one); FOMC days show the same sign (31%, n 87). Day of week, VIX terciles and prior closed P&L are flat.
What a failing session looks like, in numbers: it is a normal-volatility session (RV AUC .497; range 136 vs 162 pts; 20/60-pt swing counts equal) that goes nowhere - path efficiency .032 vs .051 (top quartile .066; AUC .381 [.36,.40], d -0.41, the strongest non-mechanical separator in all three sessions) and |net move| 46 vs 71 pts (AUC .392) - and spends more of the session near its open (inside +-30 pts: 44% of bars vs 32%; NY 24% vs 9%, AUC .65). Volatility, VIX level and change, term structure, events, day of week, overnight gap, prior-session result and range are all within 0.07 of 0.5. The failing quartile loses 3.5x (Asia) to 8.8x (NY) the session type's total net P&L; the other three quarters earn it back.

### 0.3 session-ahead and real-time prediction of FAILURE (walk-forward OOS 2024-02.., 2,101 sessions, 11 expanding folds, 3-day embargo; ridge-logistic and LightGBM; 32 cells; label-permutation p < 0.002 in every cell)
| target   | information   | model   |   AUC |   CI lo |   CI hi |   Asia |   London |    NY |   L8W |   base rate |   calib slope |   ECE |   top-decile precision |   lo90 |   hi90 |   lift |
|:---------|:--------------|:--------|------:|--------:|--------:|-------:|---------:|------:|------:|------------:|--------------:|------:|-----------------------:|-------:|-------:|-------:|
| neg      | pre-open      | lgb     | 0.612 |   0.584 |   0.640 |  0.521 |    0.629 | 0.621 | 0.595 |       0.353 |         0.770 | 0.033 |                  0.390 |  0.338 |  0.448 |  1.106 |
| neg      | pre-open      | ridge   | 0.593 |   0.566 |   0.622 |  0.513 |    0.572 | 0.637 | 0.628 |       0.353 |         0.379 | 0.082 |                  0.395 |  0.348 |  0.457 |  1.119 |
| neg      | +15 min       | lgb     | 0.621 |   0.595 |   0.646 |  0.529 |    0.608 | 0.672 | 0.697 |       0.338 |         0.857 | 0.042 |                  0.414 |  0.348 |  0.467 |  1.226 |
| neg      | +15 min       | ridge   | 0.617 |   0.591 |   0.641 |  0.532 |    0.593 | 0.675 | 0.690 |       0.338 |         0.414 | 0.092 |                  0.433 |  0.371 |  0.481 |  1.282 |
| neg      | +30 min       | lgb     | 0.646 |   0.623 |   0.669 |  0.534 |    0.624 | 0.721 | 0.732 |       0.326 |         0.987 | 0.039 |                  0.395 |  0.343 |  0.448 |  1.212 |
| neg      | +30 min       | ridge   | 0.637 |   0.610 |   0.662 |  0.534 |    0.615 | 0.708 | 0.737 |       0.326 |         0.456 | 0.092 |                  0.462 |  0.405 |  0.514 |  1.417 |
| neg      | +60 min       | lgb     | 0.664 |   0.640 |   0.688 |  0.554 |    0.630 | 0.743 | 0.740 |       0.306 |         1.119 | 0.029 |                  0.452 |  0.390 |  0.514 |  1.478 |
| neg      | +60 min       | ridge   | 0.637 |   0.613 |   0.664 |  0.544 |    0.598 | 0.699 | 0.690 |       0.306 |         0.437 | 0.091 |                  0.405 |  0.357 |  0.471 |  1.323 |
| q25      | pre-open      | lgb     | 0.562 |   0.531 |   0.592 |  0.485 |    0.599 | 0.585 | 0.662 |       0.227 |         0.454 | 0.037 |                  0.243 |  0.200 |  0.295 |  1.070 |
| q25      | pre-open      | ridge   | 0.553 |   0.525 |   0.580 |  0.511 |    0.565 | 0.587 | 0.586 |       0.227 |         0.210 | 0.087 |                  0.238 |  0.195 |  0.295 |  1.049 |
| q25      | +15 min       | lgb     | 0.595 |   0.565 |   0.624 |  0.523 |    0.602 | 0.647 | 0.652 |       0.229 |         0.689 | 0.023 |                  0.305 |  0.248 |  0.357 |  1.328 |
| q25      | +15 min       | ridge   | 0.575 |   0.545 |   0.606 |  0.527 |    0.568 | 0.632 | 0.680 |       0.229 |         0.249 | 0.082 |                  0.257 |  0.205 |  0.310 |  1.121 |
| q25      | +30 min       | lgb     | 0.633 |   0.606 |   0.657 |  0.550 |    0.610 | 0.718 | 0.763 |       0.227 |         0.999 | 0.029 |                  0.362 |  0.310 |  0.419 |  1.594 |
| q25      | +30 min       | ridge   | 0.612 |   0.583 |   0.640 |  0.541 |    0.581 | 0.703 | 0.693 |       0.227 |         0.386 | 0.070 |                  0.357 |  0.300 |  0.405 |  1.573 |
| q25      | +60 min       | lgb     | 0.643 |   0.613 |   0.671 |  0.573 |    0.604 | 0.745 | 0.724 |       0.212 |         1.053 | 0.037 |                  0.343 |  0.295 |  0.405 |  1.615 |
| q25      | +60 min       | ridge   | 0.633 |   0.605 |   0.662 |  0.567 |    0.603 | 0.725 | 0.659 |       0.212 |         0.449 | 0.058 |                  0.319 |  0.267 |  0.371 |  1.503 |
(target "neg" = P&L<0; "q25" = bottom quartile with the fit-window threshold; real-time targets are the P&L of trades entered after open+N. Per-session-type fits (not shown here, in out/clf03_results.csv) are not better than pooled. Calibration slope 1 = perfect: LightGBM is calibrated (0.77-1.12), ridge-logistic is overconfident (0.2-0.46). Top LightGBM gain pre-open: realised day RV 16%, last-5-closed-trades P&L 9%, stops in the last 24 h 9%; at +60 min: trades closed so far 15%, day RV 7%, first-hour range 6%, first-hour flips 6%.)

Reading: statistically real but small. The full pre-open feature set (Part-1 forecaster inputs and outputs, VIX family, prior-session P&L and path, calendar, L2 book state at 18:05 / 02:00 / 09:30) gives AUC .59-.61 for P&L<0 (Asia ~.51 = nothing; NY .62-.64), top-decile precision .39-.44 against 35% (lift 1.1-1.25). The first hour adds information mostly for NY (AUC .62 -> .74). The earlier result (rank corr .01-.03 for the P&L level) is consistent: the P&L level is unpredictable, the failure classifier has a little signal.

### 0.4 predicted-compression from the existing vol forecaster: P(session RV < 20-day same-type p40) = Phi((q40 - mu)/e), thresholds {.5, .6, .7}, ridge and LightGBM forecasts (6 cells)
| model   |   theta |   share flagged |   precision |   recall |   base rate |   pair $/session quiet |     wide |   $/trade quiet |    wide |   $/wk from quiet sessions |   from wide sessions |   AUC |    lo |    hi |
|:--------|--------:|----------------:|------------:|---------:|------------:|-----------------------:|---------:|----------------:|--------:|---------------------------:|---------------------:|------:|------:|------:|
| ridge   |   0.500 |           0.422 |       0.687 |    0.700 |       0.414 |               1979.840 | 1462.331 |         807.074 | 611.740 |                  12339.144 |            12501.902 | 0.825 | 0.803 | 0.847 |
| ridge   |   0.600 |           0.326 |       0.749 |    0.590 |       0.414 |               1510.953 | 1762.678 |         598.960 | 745.120 |                   7288.750 |            17552.296 | 0.825 | 0.803 | 0.847 |
| ridge   |   0.700 |           0.232 |       0.809 |    0.455 |       0.414 |                705.665 | 1975.831 |         277.938 | 830.220 |                   2425.103 |            22415.943 | 0.825 | 0.803 | 0.847 |
| lgb     |   0.500 |           0.401 |       0.747 |    0.723 |       0.414 |               1042.756 | 2106.892 |         441.348 | 858.869 |                   6175.761 |            18665.285 | 0.858 | 0.836 | 0.878 |
| lgb     |   0.600 |           0.313 |       0.788 |    0.596 |       0.414 |               1422.060 | 1798.291 |         584.299 | 746.441 |                   6579.532 |            18261.514 | 0.858 | 0.836 | 0.878 |
| lgb     |   0.700 |           0.219 |       0.839 |    0.443 |       0.414 |                915.873 | 1894.538 |         367.791 | 790.596 |                   2960.462 |            21880.584 | 0.858 | 0.836 | 0.878 |

Calibration (WF, bins of predicted probability: mean predicted -> realised frequency): ridge 0.04->0.01 (n 313); 0.15->0.12 (n 214); 0.25->0.27 (n 234); 0.35->0.32 (n 238); 0.45->0.43 (n 215); 0.55->0.47 (n 200); 0.65->0.60 (n 197); 0.75->0.73 (n 165); 0.85->0.81 (n 178); 0.95->0.90 (n 145). LightGBM 0.04->0.01; 0.15->0.11; 0.25->0.23; 0.35->0.31; 0.45->0.41; 0.55->0.60; 0.65->0.67; 0.75->0.78; 0.85->0.80; 0.95->0.94.
The pair's P&L in predicted-quiet vs predicted-wide sessions (per session, week-block bootstrap 90% CI of quiet minus wide):
| win   | model   | sess   |   n_quiet |   n_wide |   mean_quiet |   mean_wide |   diff |    lo |    hi |
|:------|:--------|:-------|----------:|---------:|-------------:|------------:|-------:|------:|------:|
| WF    | ridge   | ALL3   |       685 |     1414 |         1511 |        1763 |   -252 | -2285 |  1895 |
| WF    | ridge   | ASIA   |       297 |      403 |         4695 |        2918 |   1777 | -2677 |  6169 |
| WF    | ridge   | LONDON |       177 |      523 |        -2556 |        1541 |  -4097 | -7680 |  -612 |
| WF    | ridge   | NY     |       211 |      488 |          441 |        1046 |   -605 | -3615 |  2633 |
| WF    | lgb     | ALL3   |       657 |     1442 |         1422 |        1798 |   -376 | -2609 |  1774 |
| WF    | lgb     | ASIA   |       264 |      436 |         4226 |        3336 |    890 | -4007 |  5430 |
| WF    | lgb     | LONDON |       198 |      502 |         -317 |         829 |  -1145 | -4634 |  2086 |
| WF    | lgb     | NY     |       195 |      504 |         -609 |        1434 |  -2043 | -4987 |   978 |
| WF    | EXPOST  | ALL3   |       869 |     1230 |          601 |        2443 |  -1842 | -3765 |   132 |
| IS    | ridge   | ALL3   |       211 |      502 |         1328 |        1104 |    223 | -2472 |  3156 |
| IS    | ridge   | ASIA   |        60 |      178 |         2204 |        -195 |   2400 | -4286 |  8906 |
| IS    | ridge   | LONDON |        63 |      175 |          804 |        2615 |  -1811 | -6967 |  4241 |
| IS    | ridge   | NY     |        88 |      149 |         1105 |         882 |    222 | -6305 |  5805 |
| IS    | lgb     | ALL3   |       235 |      478 |         2783 |         377 |   2406 |  -863 |  5508 |
| IS    | lgb     | ASIA   |        76 |      162 |         3486 |       -1033 |   4519 | -2195 | 11490 |
| IS    | lgb     | LONDON |        80 |      158 |         1977 |        2216 |   -238 | -5259 |  5389 |
| IS    | lgb     | NY     |        79 |      158 |         2924 |         -15 |   2939 | -2067 |  8147 |
| IS    | EXPOST  | ALL3   |       304 |      409 |         1681 |         791 |    890 | -2246 |  4182 |
Conclusion of Step 0: the forecaster is good at the volatility target, but low volatility is not where the pair loses; London is the only session where predicted-quiet loses (-4.1k/session, CI [-7.7k,-0.6k], one look), Asia is the opposite (+1.8k, CI spans zero). The failure axis is directionality, which the pre-open information barely sees.
## 3. STEP 1 - real-time compression state (7 candidate families, 45 cells; 2-state with hysteresis; selection on IS only)
Rule (frozen): among cells with ON share of session hours in [10%, 60%] and >= 60 pair trades entered ON in IS, maximise the Welch t of (pair net per trade OFF) minus (ON) in IS. 25 of 45 cells were eligible. Best cell per candidate family (WF/L8W shown, never used for selection):
| cell              |   ON share IS |   ON episode min |   OFF episode min |   lag med min |   truth episodes missed |   bal. acc. vs truth |   n ON IS |   net/trade ON IS |   OFF IS |   Welch t IS |   n ON WF |   ON WF |   OFF WF |   Welch t WF |   ON L8W |   OFF L8W |
|:------------------|--------------:|-----------------:|------------------:|--------------:|------------------------:|---------------------:|----------:|------------------:|---------:|-------------:|----------:|--------:|---------:|-------------:|---------:|----------:|
| C3|vwb120|0.8|1.0 |          0.37 |           126.17 |            194.74 |          0.00 |                    0.07 |                 0.67 |       347 |          -1252.33 |  1096.13 |         2.44 |      1324 |  -53.38 |   963.81 |         2.07 |  1088.54 |    775.67 |
| C1|rng120|0.8|1.0 |          0.35 |           143.19 |            230.62 |          0.00 |                    0.07 |                 0.68 |       325 |           -737.50 |   890.89 |         1.65 |      1308 |  422.89 |   794.21 |         0.75 |  1588.40 |    639.14 |
| C6|zz240|0|1      |          0.57 |            34.37 |             55.85 |          0.00 |                    0.28 |                 0.57 |       452 |           -121.78 |   814.83 |         1.04 |       806 |  389.52 |   756.86 |         0.62 |  2827.77 |    619.29 |
| C2|atr120|0.7|0.9 |          0.15 |           467.64 |           1849.35 |          0.00 |                    0.32 |                 0.68 |       177 |           -354.07 |   636.68 |         0.81 |       893 | -192.96 |   888.82 |         1.93 |   479.40 |    913.98 |
| C5|flip60|4|2     |          0.35 |            72.06 |            136.80 |          1.00 |                    0.37 |                 0.49 |       532 |            346.54 |   612.25 |         0.31 |      1766 |  572.99 |   765.51 |         0.43 |  -188.89 |   1436.02 |
| C4|vr240|0.85|1.0 |          0.55 |           241.94 |            193.21 |          0.00 |                    0.21 |                 0.55 |       658 |           1154.59 |   -66.52 |        -1.47 |      2434 |  210.12 |  1148.34 |         2.17 |  -269.42 |   1702.29 |

**Selected: C3|vwb120|0.8|1.0** (volume-weighted std of close about the 120-bar VWAP / same-clock 20-day median; ON < 0.8, OFF > 1.0). ON share ASIA 38% / LONDON 40% / NY 40%; 4,070 ON episodes, median length 77 min (mean 126), OFF mean 195 min. Against the realised forward-60-min compression truth (22% of minutes; 1,204 episodes of >= 60 min): P(ON|truth) 66%, P(truth|ON) 36%, balanced accuracy 0.67, 7% of truth episodes never flagged, detection lag median 0 min / mean 12 min. Pair per state-hour: ON -206 (IS) / -11 (WF) / 224 (L8W) $/h vs OFF 314 / 380 / 346; stop rate ON 44% / 41% vs OFF 35% / 38% (IS / WF).
Family reading: the relative-range (C1), ATR (C2) and VWAP-band (C3) states agree - the pair earns ~0 per trade when current range / vol / band width is below the same-clock 20-day norm (WF ON vs OFF: C1 +423 vs +794, C2 -13 vs +982, C3 -53 vs +964) - and L8W goes the other way for C1 and C3. The variance-ratio state (C4) is ON 55-73% of the time (not a state), the flip-count states (C5) are ON 35-97%, the 60-pt-swing states (C6) and the consecutive-stop states (C7, ON 1-7% of time) show no IS or WF separation (Welch t 0.3-1.0; C7 negative in WF). Full table: out/step1_cells.csv.

## 4. STEP 2 - the range book (6 families x 18 cells = 108 cells)
Fill model (frozen, conservative; the sensitivity of the verdict to it is bounded below): entry = resting limit at the book's level re-evaluated each minute, filled only when a 1-s close trades THROUGH it by >= 1 tick (queue-risk proxy), at the limit price; target = resting limit, same through-1-tick rule; stop = market on the first 1-s close at/through the stop, filled at the NEXT printed second; time cap and session-end flat = market. Market exits pay the S113 surface (3.12 ticks per lot at 8 lots, 3.98 at 14) and fees $4.84/lot RT; limit fills pay no impact. One position per book, 30-min cooldown after a stop, session halted after 3 stops, day halted at -60 gross pts. Entries only >= warm-up after the session open and >= 30 min before the flat time, never in the pair-blocked windows. Sensitivity (touch fills: 0-tick-through entries and targets) changes net per trade by +18..+62 $ at 8 lots; gross points before ANY cost are negative in every one of the 54 simulations in all sessions (mean -1.2 pts IS, -1.9 WF) - the verdict cannot be a cost-model artefact.

Best range-book table. For each book the config with the highest min(IS net/trade in (b), IS net/trade in (c)) (the pre-registered carry rule; IS only), 8 lots, net per trade after cost, trades per week and net per week. Views: (a) all sessions, (b) the Step-0 failing sessions (ex-post oracle), (c) predicted-quiet (ridge, theta .6), (d) real-time compression state (C3).
| book | cfg (k,H,lots) | IS min((b),(c)) | view | IS n / tr per wk / net per trade | WF n / tr per wk / net per trade / net per wk | L8W net per trade (n) |
|---|---|---|---|---|---|---|
| R4 | 2.0,60,8 | -16 | (a) all | 1710 / 32.9 / -175 | 4373 / 30.8 / -371 / -11434 | -292 (219) |
| R4 | 2.0,60,8 | -16 | (b) failing | 494 / 9.5 / 168 | 1206 / 8.5 / 241 / 2049 | 800 (57) |
| R4 | 2.0,60,8 | -16 | (c) pred-quiet | 514 / 9.9 / -16 | 1452 / 10.2 / -184 / -1882 | -676 (73) |
| R4 | 2.0,60,8 | -16 | (d) RT state | 813 / 15.6 / -108 | 2293 / 16.1 / -409 / -6607 | -272 (102) |
| R5 | 1.5,30,8 | -62 | (a) all | 479 / 9.2 / -315 | 1244 / 8.8 / -405 / -3551 | -319 (68) |
| R5 | 1.5,30,8 | -62 | (b) failing | 180 / 3.5 / 167 | 300 / 2.1 / -34 / -71 | -2360 (14) |
| R5 | 1.5,30,8 | -62 | (c) pred-quiet | 153 / 2.9 / -62 | 380 / 2.7 / -463 / -1240 | -1236 (6) |
| R5 | 1.5,30,8 | -62 | (d) RT state | 227 / 4.4 / -70 | 628 / 4.4 / -51 / -227 | -322 (29) |
| R2 | 1.0,120,8 | -189 | (a) all | 1173 / 22.6 / -349 | 3555 / 25.0 / -567 / -14199 | -494 (217) |
| R2 | 1.0,120,8 | -189 | (b) failing | 317 / 6.1 / 315 | 940 / 6.6 / 762 / 5045 | 1591 (54) |
| R2 | 1.0,120,8 | -189 | (c) pred-quiet | 303 / 5.8 / -189 | 1205 / 8.5 / -534 / -4533 | -492 (98) |
| R2 | 1.0,120,8 | -189 | (d) RT state | 434 / 8.3 / -296 | 1697 / 12.0 / -417 / -4981 | 900 (98) |
| R3 | 2.0,120,8 | -191 | (a) all | 2304 / 44.3 / -235 | 5324 / 37.5 / -384 / -14380 | -334 (261) |
| R3 | 2.0,120,8 | -191 | (b) failing | 622 / 12.0 / -44 | 1435 / 10.1 / 389 / 3936 | 529 (70) |
| R3 | 2.0,120,8 | -191 | (c) pred-quiet | 626 / 12.0 / -191 | 1867 / 13.1 / -384 / -5055 | -131 (124) |
| R3 | 2.0,120,8 | -191 | (d) RT state | 1123 / 21.6 / -124 | 2885 / 20.3 / -289 / -5864 | 890 (130) |
| R6 | 1.5,60,8 | -196 | (a) all | 799 / 15.4 / -365 | 2076 / 14.6 / -478 / -6986 | -1909 (105) |
| R6 | 1.5,60,8 | -196 | (b) failing | 206 / 4.0 / -196 | 546 / 3.8 / 591 / 2274 | 1846 (28) |
| R6 | 1.5,60,8 | -196 | (c) pred-quiet | 214 / 4.1 / -143 | 696 / 4.9 / -257 / -1260 | -2005 (39) |
| R6 | 1.5,60,8 | -196 | (d) RT state | 332 / 6.4 / -235 | 901 / 6.3 / -485 / -3076 | -2895 (43) |
| R1 | 1.0,120,8 | -246 | (a) all | 2079 / 40.0 / -304 | 5321 / 37.5 / -484 / -18119 | -798 (291) |
| R1 | 1.0,120,8 | -246 | (b) failing | 555 / 10.7 / -146 | 1413 / 10.0 / -24 / -243 | -516 (83) |
| R1 | 1.0,120,8 | -246 | (c) pred-quiet | 544 / 10.5 / -246 | 1908 / 13.4 / -322 / -4321 | -816 (139) |
| R1 | 1.0,120,8 | -246 | (d) RT state | 893 / 17.2 / -218 | 2718 / 19.1 / -297 / -5684 | -797 (137) |

Positive-net cells (of 108, >= 30 trades): a_all IS: 0/108; a_all WF: 0/108; a_all L8W: 2/108; b_fail IS: 48/108; b_fail WF: 87/108; b_fail L8W: 56/78; c_quiet IS: 0/108; c_quiet WF: 0/108; c_quiet L8W: 2/90; d_rt IS: 0/108; d_rt WF: 8/108; d_rt L8W: 38/94.

Oracle view (b), best configs by WF net per trade at 14 lots (flagged: selected on WF, an ex-post view, NOT a tradable result): R5 k2.0 H120 +3,014 $/trade (2.0 trades/wk, +4.9k/wk), R6 k2.0 H120 +2,016 (3.0/wk, +6.0k/wk), R2 k2.0 H120 +1,859 (6.0/wk, +11.7k/wk), R3 k2.0 H120 +648 (10/wk, +6.5k/wk), R4 k2.0 H120 +470 (8/wk, +3.6k/wk), R1 k2.0 H120 +331 (10/wk, +3.2k/wk). The books are fades of non-directional price action and earn when the pair fails; capacity is small (2-10 trades a week in failing sessions at 8-14 lots).

Nulls (200 placebo range books; 500 shifted-flag worlds). PLACEBO = every real trade re-created at the same ET clock time on another label day (circular shift >= 20 days, wrapping), same side / stop / target / hold / costs, entry at market (more generous than the real fill). SHUFFLED FLAG = the (b) / (c) / (d) flag series shifted by whole label days, real trades re-labelled. Rank = share of null worlds with a LOWER net per trade than the real book (8 lots, IS-selected config per book):
| book   |    k |   H | view           |   n trades |   real net/trade |   placebo mean |   placebo sd |   placebo rank |   shuffled-flag mean |   shuffled-flag rank |
|:-------|-----:|----:|:---------------|-----------:|-----------------:|---------------:|-------------:|---------------:|---------------------:|---------------------:|
| R4     | 2.00 |  60 | (a) all        |       6083 |          -316.08 |        -188.96 |        54.62 |           0.01 |               nan    |               nan    |
| R4     | 2.00 |  60 | (b) failing    |       1700 |           220.11 |        -177.07 |       107.47 |           1.00 |              -314.53 |                 1.00 |
| R4     | 2.00 |  60 | (c) pred-quiet |       1966 |          -140.11 |        -177.23 |        97.94 |           0.63 |              -319.09 |                 0.93 |
| R4     | 2.00 |  60 | (d) RT state   |       3106 |          -330.41 |        -184.03 |        82.50 |           0.04 |              -317.78 |                 0.45 |
| R5     | 1.50 |  30 | (a) all        |       1723 |          -380.20 |        -194.60 |       181.73 |           0.15 |               nan    |               nan    |
| R5     | 1.50 |  30 | (b) failing    |        480 |            41.62 |        -192.23 |       324.41 |           0.77 |              -358.30 |                 0.87 |
| R5     | 1.50 |  30 | (c) pred-quiet |        533 |          -348.22 |        -166.23 |       287.44 |           0.25 |              -383.27 |                 0.53 |
| R5     | 1.50 |  30 | (d) RT state   |        855 |           -56.36 |        -154.41 |       252.21 |           0.64 |              -395.56 |                 0.90 |
| R2     | 1.00 | 120 | (a) all        |       4728 |          -513.04 |        -195.07 |        87.10 |           0.00 |               nan    |               nan    |
| R2     | 1.00 | 120 | (b) failing    |       1257 |           649.36 |        -178.55 |       172.32 |           1.00 |              -511.03 |                 1.00 |
| R2     | 1.00 | 120 | (c) pred-quiet |       1508 |          -464.87 |        -180.00 |       157.23 |           0.03 |              -537.69 |                 0.68 |
| R2     | 1.00 | 120 | (d) RT state   |       2131 |          -392.13 |        -197.61 |       134.60 |           0.09 |              -510.53 |                 0.85 |
| R3     | 2.00 | 120 | (a) all        |       7628 |          -338.63 |        -184.30 |        56.66 |           0.01 |               nan    |               nan    |
| R3     | 2.00 | 120 | (b) failing    |       2057 |           258.43 |        -189.14 |       107.86 |           1.00 |              -336.93 |                 1.00 |
| R3     | 2.00 | 120 | (c) pred-quiet |       2493 |          -335.92 |        -176.81 |        93.17 |           0.03 |              -348.89 |                 0.54 |
| R3     | 2.00 | 120 | (d) RT state   |       4008 |          -242.44 |        -178.42 |        77.07 |           0.21 |              -337.02 |                 0.85 |
| R6     | 1.50 |  60 | (a) all        |       2875 |          -446.52 |        -189.71 |        92.56 |           0.01 |               nan    |               nan    |
| R6     | 1.50 |  60 | (b) failing    |        752 |           375.81 |        -174.83 |       148.68 |           1.00 |              -441.79 |                 1.00 |
| R6     | 1.50 |  60 | (c) pred-quiet |        910 |          -230.25 |        -156.03 |       156.13 |           0.32 |              -420.30 |                 0.88 |
| R6     | 1.50 |  60 | (d) RT state   |       1233 |          -417.49 |        -187.43 |       131.48 |           0.04 |              -436.56 |                 0.53 |
| R1     | 1.00 | 120 | (a) all        |       7400 |          -433.02 |        -183.10 |        44.16 |           0.00 |               nan    |               nan    |
| R1     | 1.00 | 120 | (b) failing    |       1968 |           -58.81 |        -211.50 |        79.72 |           0.96 |              -431.86 |                 1.00 |
| R1     | 1.00 | 120 | (c) pred-quiet |       2452 |          -304.90 |        -186.12 |        76.30 |           0.06 |              -442.84 |                 0.97 |
| R1     | 1.00 | 120 | (d) RT state   |       3611 |          -277.32 |        -194.85 |        69.38 |           0.10 |              -435.69 |                 1.00 |

Reading: (a) the real book is WORSE than same-clock random-timing trades with the same geometry in every book (rank 0.000-0.15; R4 -316 vs -189 +-55): the fade levels carry no mean-reversion skill, and about half of the gap is the through-fill convention. (b) in the pair's failing sessions the real books beat placebo and beat 500 shifted failing-session flags (rank 1.000 for R2, R3, R4, R6) - the hedge relation is real but ex-post. (c) predicted-quiet sessions are relatively less bad for fades than random sessions (shuffled-flag rank .93 R4, .97 R1) but still negative (R4 -140 vs null mean -319). (d) the real-time state: shuffled-flag ranks .45-.996 but every real value is negative.
Correlation and tail behaviour (exploratory): weekly correlation of RB P&L with the pair -0.02..-0.34 (R6 -0.34, R3 -0.21), but at 8 lots the books lose 3k-17k a week; in the pair's worst-decile weeks only R5 (both configs) and one R6 config are positive. Exploratory (not a cell): gating the mid-config books (k1.5 H60) by the OOS failure classifier (top quartile of P(P&L<0), pre-open or +60 min) does not make any book profitable (R2 -477 pre-open, -243 at +60; out/expl_clfgate.csv).

DROP RULE result (IS, frozen): min over (b),(c) of IS net per trade, best config per book: R4 -16, R5 -62, R2 -189, R3 -191, R6 -196, R1 -246 - no book > 0 in both, so every book is dropped; the least-bad (R4 HM-anchor fade, k 2.0, H 60, 8 lots; 32 trades/wk in all sessions, 9.9/wk in predicted-quiet) was carried into Step 3 as DROPPED-BOOK (ADDENDUM1).
## 5. STEP 3 - the switch (DROPPED-BOOK R4 k2.0 H60 8 lots; 4 variants x 7 sources x 2 bases = 56 cells, each at both credit settings)
Variants: (a) hard - ON: pair takes no NEW entries (signals ignored, rows regenerated so later signals are taken: ADDENDUM2), RB may enter; OFF: pair normal, RB none. (b) size-shift - ON: pair 6 lots, RB 8; OFF: pair base lots. (c) both always on - ON: pair 6, RB 14; OFF: pair base, RB 4. (d) breakout re-arm - (a) plus: when an ON episode (>= 30 bars) closes beyond its [low, high] excluding the last 15 bars the state is forced OFF and a break trade (pair bracket 60/60, base lots, P9 haircut by exit type, MAPPED) is entered at the next open. Sources: SA = predicted-quiet session flag (ridge, theta .6); RT = C3 state with min-dwell 30/60/120 min; BOTH = SA and RT. Bases: A = live spec (BM1), B = Set B (BM2). (b), (c) PRIMARY at credit=False (no S113 refund below 14 lots) against the benchmark at credit=False; (a), (d) against the user's credit=True benchmarks.
Deltas are system minus its own benchmark: weekly mean ($/wk) and maxDD ($, negative = better), WF = 142 weeks, L8W = 8 weeks. Rank = share of 200 shuffled-state worlds (SA and RT circularly shifted by the same random whole number of label days >= 20, wrapping) with a worse delta (mean: lower; maxDD: larger).
### BASE A (benchmark BM1: live spec)
| cell      |   ON share |   WF mean |   WF d mean |   WF d maxDD |   WF SD |   WF worst wk |   L8W d mean |   L8W d maxDD |   IS d mean |   IS d maxDD |   WF-pre d mean |   WF-pre d maxDD |   HOLD d mean |   HOLD d maxDD |   rank mean |   rank maxDD |
|:----------|-----------:|----------:|------------:|-------------:|--------:|--------------:|-------------:|--------------:|------------:|-------------:|----------------:|-----------------:|--------------:|---------------:|------------:|-------------:|
| a SA      |       0.31 |     20219 |       -4757 |       109324 |   94302 |       -161097 |       -29583 |        183704 |       -5440 |      -102312 |            3654 |           -99675 |        -13963 |         243484 |        0.90 |         0.74 |
| a RT30    |       0.40 |      9813 |      -15163 |       347620 |   98095 |       -188147 |        -1496 |        -96971 |      -14046 |       231117 |          -17138 |           347620 |        -12761 |         216610 |        0.30 |         0.41 |
| a RT60    |       0.41 |      6801 |      -18175 |       738259 |   95547 |       -174211 |       -42020 |         60903 |      -16917 |       104571 |          -15039 |           738259 |        -21366 |         296034 |        0.18 |         0.07 |
| a RT120   |       0.42 |      8465 |      -16511 |       450648 |  104540 |       -195758 |       -20760 |         50756 |      -21430 |       298710 |          -11242 |           450648 |        -22079 |         343217 |        0.30 |         0.28 |
| a BOTH30  |       0.19 |     13262 |      -11714 |        24625 |  102839 |       -160975 |         3319 |        -44223 |       -1894 |        15257 |           -9561 |            24625 |        -13916 |         121575 |        0.09 |         0.86 |
| a BOTH60  |       0.19 |     12098 |      -12877 |       222301 |  101387 |       -166303 |        -1418 |         65164 |       -2775 |       111897 |           -9439 |            66637 |        -16480 |         356462 |        0.04 |         0.27 |
| a BOTH120 |       0.18 |     13032 |      -11943 |       341290 |  105893 |       -170079 |        -6742 |        143445 |       -8746 |        83941 |           -3184 |             9985 |        -21429 |         475451 |        0.14 |         0.12 |
| b SA      |       0.31 |     22754 |       -2221 |        14091 |   94487 |       -165935 |         -631 |         24571 |       -3443 |      -124647 |            -678 |            14091 |         -3890 |         119770 |        0.85 |         0.77 |
| b RT30    |       0.40 |     15937 |       -9039 |        96702 |  101427 |       -189038 |        -4252 |         79396 |        1184 |        55217 |           -9416 |            96702 |         -8490 |          79396 |        0.29 |         0.58 |
| b RT60    |       0.41 |     14253 |      -10723 |       170783 |  101686 |       -175298 |       -17229 |        137836 |         -91 |        45962 |          -12790 |            52178 |         -8285 |         138458 |        0.22 |         0.30 |
| b RT120   |       0.42 |     20812 |       -4164 |       153753 |  105370 |       -181515 |         -219 |         36225 |       -3687 |        92445 |           -7723 |            94588 |          -177 |          81597 |        0.73 |         0.42 |
| b BOTH30  |       0.19 |     19555 |       -5420 |        90243 |  103439 |       -159919 |        -4911 |         88598 |         -25 |       -21413 |           -3463 |            90243 |         -7499 |         123608 |        0.22 |         0.34 |
| b BOTH60  |       0.19 |     19357 |       -5619 |        81543 |  103530 |       -163354 |        -8525 |        133204 |         685 |       -12457 |           -5514 |            81543 |         -5652 |         186279 |        0.23 |         0.38 |
| b BOTH120 |       0.18 |     19788 |       -5187 |        76243 |  103249 |       -167144 |        -9000 |        121641 |       -3288 |        38489 |           -2220 |            32612 |         -8384 |         193788 |        0.29 |         0.41 |
| c SA      |       0.31 |     16618 |       -8358 |        98505 |   93470 |       -161009 |        -6452 |         54234 |       -6609 |       -56701 |           -5729 |            38561 |        -11134 |         127625 |        0.87 |         0.70 |
| c RT30    |       0.40 |      8031 |      -16944 |       191782 |  101950 |       -213778 |       -10069 |        145004 |       -1373 |        54333 |          -14886 |           191782 |        -18966 |         145004 |        0.18 |         0.54 |
| c RT60    |       0.41 |      6595 |      -18380 |       405869 |  102781 |       -211507 |       -22545 |        203255 |       -3046 |        48464 |          -17718 |           236548 |        -18841 |         227662 |        0.14 |         0.09 |
| c RT120   |       0.42 |     13506 |      -11469 |       243712 |  104190 |       -206875 |        -4416 |         67933 |       -5974 |        90328 |          -12049 |           243712 |        -10661 |          77497 |        0.63 |         0.41 |
| c BOTH30  |       0.19 |     13222 |      -11754 |       112809 |  103442 |       -179957 |       -10642 |        117854 |       -2386 |        10089 |           -8377 |           112809 |        -15305 |         117854 |        0.23 |         0.46 |
| c BOTH60  |       0.19 |     13123 |      -11853 |       107370 |  103363 |       -191959 |       -14177 |        161832 |       -1660 |        13360 |          -10306 |           107370 |        -13384 |         214485 |        0.20 |         0.44 |
| c BOTH120 |       0.18 |     13539 |      -11437 |       171314 |  102854 |       -189108 |       -13897 |        133466 |       -5363 |        73061 |           -7138 |            56039 |        -16009 |         185803 |        0.25 |         0.23 |
| d SA      |       0.03 |     28422 |        3447 |       -16104 |  104623 |       -190850 |          452 |         -7171 |       -2478 |       203820 |            6907 |           -16104 |          -421 |          17289 |        0.95 |         0.94 |
| d RT30    |       0.12 |     22528 |       -2447 |       326167 |  119944 |       -210115 |       -25156 |        145275 |      -10440 |       206029 |          -14972 |           326167 |         11404 |         145275 |        0.67 |         0.41 |
| d RT60    |       0.12 |     23845 |       -1131 |       231447 |  115685 |       -220316 |       -16400 |        205043 |      -14550 |       368624 |          -13221 |           231447 |         12220 |         205043 |        0.76 |         0.74 |
| d RT120   |       0.10 |     27376 |        2401 |       133223 |  120267 |       -231986 |        47082 |        -41196 |       -2763 |       175936 |           -4737 |           121406 |         10238 |         239975 |        0.86 |         0.88 |
| d BOTH30  |       0.05 |     21490 |       -3486 |       109856 |  108299 |       -197168 |       -24737 |        197805 |       -1808 |       212182 |            3820 |           -47765 |        -11492 |         244016 |        0.51 |         0.59 |
| d BOTH60  |       0.05 |     22842 |       -2133 |        71231 |  108601 |       -197290 |       -15918 |        205391 |        -367 |       266208 |            4044 |           -21234 |         -8915 |         205391 |        0.60 |         0.77 |
| d BOTH120 |       0.04 |     24057 |        -918 |        -6492 |  106857 |       -186984 |         2337 |         61487 |        5544 |       116114 |            7069 |           -10092 |         -9714 |         116269 |        0.55 |         0.97 |

### BASE B (benchmark BM2: Set B)
| cell      |   ON share |   WF mean |   WF d mean |   WF d maxDD |   WF SD |   WF worst wk |   L8W d mean |   L8W d maxDD |   IS d mean |   IS d maxDD |   WF-pre d mean |   WF-pre d maxDD |   HOLD d mean |   HOLD d maxDD |   rank mean |   rank maxDD |
|:----------|-----------:|----------:|------------:|-------------:|--------:|--------------:|-------------:|--------------:|------------:|-------------:|----------------:|-----------------:|--------------:|---------------:|------------:|-------------:|
| a SA      |       0.31 |     22893 |      -11289 |       197050 |   94075 |       -195776 |       -37408 |        247205 |       -7011 |         9667 |           -5837 |            79748 |        -17137 |         259901 |        0.79 |         0.38 |
| a RT30    |       0.40 |     16142 |      -18040 |       373653 |  102156 |       -256211 |       -24643 |         71633 |      -12915 |       205850 |          -19533 |           373653 |        -16128 |         161637 |        0.55 |         0.28 |
| a RT60    |       0.41 |     14149 |      -20033 |       619703 |  101158 |       -221835 |       -34803 |         78003 |      -18815 |       333961 |          -19242 |           619703 |        -20610 |         196067 |        0.42 |         0.06 |
| a RT120   |       0.42 |     18845 |      -15337 |       333848 |  104652 |       -205095 |       -26979 |         80339 |      -20145 |       457820 |          -13999 |           333848 |        -16586 |         249712 |        0.76 |         0.43 |
| a BOTH30  |       0.19 |     21864 |      -12318 |       261420 |  105868 |       -200151 |         2866 |         13605 |       -2426 |        43882 |           -9041 |           261420 |        -15750 |         142481 |        0.18 |         0.12 |
| a BOTH60  |       0.19 |     19579 |      -14603 |       343750 |  105933 |       -209622 |        -3360 |         48479 |       -2566 |        95111 |          -11185 |           343750 |        -18158 |         263902 |        0.07 |         0.04 |
| a BOTH120 |       0.18 |     20393 |      -13789 |       535424 |  107335 |       -199314 |        -9684 |         91750 |       -5884 |        94899 |           -6575 |           158101 |        -21543 |         598275 |        0.11 |         0.00 |
| b SA      |       0.31 |     24534 |       -8584 |       169738 |   99065 |       -195795 |       -27860 |        184460 |       -5176 |        20254 |           -6220 |           -30221 |        -11065 |         233491 |        0.64 |         0.14 |
| b RT30    |       0.40 |     23221 |       -9898 |       105705 |  105569 |       -207169 |        -5685 |        156381 |        1930 |       -39805 |          -14477 |           105705 |         -4702 |         109177 |        0.71 |         0.56 |
| b RT60    |       0.41 |     24384 |       -8735 |       141113 |  102910 |       -207169 |          -62 |         97779 |          89 |       -44332 |          -13593 |           141113 |         -3248 |          50574 |        0.79 |         0.36 |
| b RT120   |       0.42 |     23686 |       -9433 |       112354 |  104511 |       -203989 |       -33129 |        162485 |       -2043 |       -44717 |          -17119 |           112354 |          -817 |         172128 |        0.74 |         0.59 |
| b BOTH30  |       0.19 |     25820 |       -7299 |        76440 |  108291 |       -204157 |       -10158 |        132294 |       -1405 |        95670 |           -6570 |            -1847 |         -7996 |         140193 |        0.27 |         0.34 |
| b BOTH60  |       0.19 |     26279 |       -6840 |        56656 |  106824 |       -203192 |        -4905 |        111657 |        -822 |       109591 |           -7159 |            34801 |         -6388 |         120409 |        0.33 |         0.47 |
| b BOTH120 |       0.18 |     25605 |       -7513 |       190165 |  106652 |       -212958 |       -24047 |        212187 |       -4733 |       108951 |           -5580 |           -13894 |         -9535 |         253917 |        0.23 |         0.06 |
| c SA      |       0.31 |     18398 |      -14721 |       168917 |   97384 |       -207338 |       -33682 |        205445 |       -8341 |        37529 |          -11271 |            82874 |        -18309 |         232669 |        0.69 |         0.38 |
| c RT30    |       0.40 |     15315 |      -17803 |       276999 |  105439 |       -205186 |       -11502 |        221989 |        -627 |       -24866 |          -19947 |           276999 |        -15178 |         174785 |        0.54 |         0.21 |
| c RT60    |       0.41 |     16726 |      -16393 |       224102 |  103563 |       -205186 |        -5378 |        163198 |       -2866 |        -7339 |          -18521 |           224102 |        -13804 |         138264 |        0.67 |         0.39 |
| c RT120   |       0.42 |     16380 |      -16738 |       388604 |  102465 |       -201887 |       -37326 |        189135 |       -4330 |       -14675 |          -21445 |           388604 |        -11301 |         169475 |        0.66 |         0.07 |
| c BOTH30  |       0.19 |     19486 |      -13633 |       154712 |  107914 |       -200529 |       -15889 |        167003 |       -3766 |       103906 |          -11484 |           154712 |        -15802 |         136092 |        0.26 |         0.19 |
| c BOTH60  |       0.19 |     20045 |      -13074 |       175129 |  106125 |       -200529 |       -10557 |        140284 |       -3166 |       117325 |          -11951 |           175129 |        -14120 |         110226 |        0.32 |         0.14 |
| c BOTH120 |       0.18 |     19356 |      -13763 |       180773 |  105486 |       -209056 |       -28945 |        227598 |       -6808 |       120641 |          -10498 |            58312 |        -17161 |         244526 |        0.23 |         0.15 |
| d SA      |       0.03 |     34112 |         -70 |        25533 |  105342 |       -170749 |       -10365 |          6730 |       -2783 |       287081 |            1086 |            25533 |         -1344 |          20019 |        0.84 |         0.87 |
| d RT30    |       0.12 |     29989 |       -4193 |       303824 |  116305 |       -207287 |       -23866 |        159090 |       -8040 |       183549 |          -18412 |           303824 |         11550 |         110919 |        0.69 |         0.30 |
| d RT60    |       0.12 |     30741 |       -3441 |       293615 |  116751 |       -223462 |       -17265 |        228118 |      -13788 |       314079 |          -14438 |           293615 |          8739 |         179948 |        0.81 |         0.38 |
| d RT120   |       0.10 |     36122 |        1941 |       169288 |  118472 |       -209768 |        26046 |         88975 |        -857 |        83011 |           -7289 |           169288 |         12091 |         101657 |        0.93 |         0.65 |
| d BOTH30  |       0.05 |     30139 |       -4043 |        76581 |  108422 |       -203860 |       -19094 |        187602 |        -692 |       252604 |             198 |            40976 |         -8661 |         139432 |        0.45 |         0.68 |
| d BOTH60  |       0.05 |     31063 |       -3119 |        99621 |  110887 |       -203860 |       -12036 |        203232 |        1760 |       255694 |            -831 |            99621 |         -5596 |         155062 |        0.59 |         0.57 |
| d BOTH120 |       0.04 |     30051 |       -4130 |        63570 |  110378 |       -173109 |       -10245 |        171255 |        7542 |       133396 |              45 |             -775 |         -8675 |         126420 |        0.40 |         0.71 |

Gate (a) [WF delta mean > 0 AND delta maxDD < 0]: **1 of 56** (keep-mask first version: 0 of 56). Gate (b) [same on L8W] among those: 1. Cells with WF delta mean > 0: 3; with WF delta maxDD < 0: 2. Other windows (cells passing the same test): IS 3, WF-pre 6, HOLDOUT 0, L8W 3.
Null calibration: in the 200 shuffled-state worlds 0.72 of the 56 cells pass gate (a) per world on average (max 7); 31% of worlds contain at least one gate-(a) passer. A chance passer is therefore common; the real 56 give 1.

Family-wise gate (c) (family-world scan: statistic = best WF delta mean among cells with L8W delta mean > 0, and best WF -delta maxDD among cells with L8W delta maxDD < 0, rank among the 200 shuffled-state worlds; need >= 0.95 on both):
| family   |   cells |   real best mean |   rank (mean) |   null best mean p50 |   null best mean p95 |   real best -dmaxDD |   rank (maxDD) |   null best -dmaxDD p50 |   null best -dmaxDD p95 |
|:---------|--------:|-----------------:|--------------:|---------------------:|---------------------:|--------------------:|---------------:|------------------------:|------------------------:|
| a        |      14 |        -11713.53 |          0.27 |             -6270.27 |              2956.40 |           -24624.69 |           0.78 |              -102274.09 |                40184.05 |
| b        |      14 |           nan    |          0.00 |             -2330.72 |              3792.07 |              nan    |           0.00 |               -40274.87 |                59199.84 |
| c        |      14 |           nan    |          0.00 |             -8935.27 |             -2278.87 |              nan    |           0.00 |              -236158.69 |                  751.77 |
| d        |      14 |          3446.67 |          0.73 |               255.60 |              9065.85 |            16104.14 |           0.98 |              -141280.97 |                -1512.13 |
| ALL      |      56 |          3446.67 |          0.68 |              1492.18 |              9065.85 |            16104.14 |           0.70 |               -13823.83 |                62087.69 |

Variant medians over cells (WF, vs benchmark): (a) mean -14.2k/wk, maxDD +343k; (b) mean -7.4k/wk, maxDD +101k; (c) mean -13.7k/wk, maxDD +178k; (d) mean -2.3k/wk, maxDD +105k. Decomposition (WF, per week): the pair-only part of the gate changes the mean by (a) -9.7k; (b) -2.9k; (c) -2.9k; (d) -1.9k (median over cells), the range book adds (a) -3.0k; (b) -3.0k; (c) -9.3k; (d) -0.5k, the break sleeve (d) +1.3k.

### Finalists: gate (a) on IS + WF-pre (2024-02..2025-06) = 6 cells; each read ONCE on the frozen HOLDOUT 2025-07..2026-10
| v   | src   |   dwell | base   |   WF-pre d mean |   WF-pre d maxDD |   WF d mean |   WF d maxDD |   L8W d mean |   L8W d maxDD |   HOLD d mean |   HOLD d maxDD |   IS d mean |   IS d maxDD |   H1 d mean |   H2 d mean |
|:----|:------|--------:|:-------|----------------:|-----------------:|------------:|-------------:|-------------:|--------------:|--------------:|---------------:|------------:|-------------:|------------:|------------:|
| a   | SA    |       0 | A      |            3654 |           -99675 |       -4757 |       109324 |       -29583 |        183704 |        -13963 |         243484 |       -5440 |      -102312 |        4037 |      -12232 |
| d   | SA    |       0 | A      |            6907 |           -16104 |        3447 |       -16104 |          452 |         -7171 |          -421 |          17289 |       -2478 |       203820 |         524 |        5907 |
| d   | BOTH  |      30 | A      |            3820 |           -47765 |       -3486 |       109856 |       -24737 |        197805 |        -11492 |         244016 |       -1808 |       212182 |        2634 |       -8685 |
| d   | BOTH  |      60 | A      |            4044 |           -21234 |       -2133 |        71231 |       -15918 |        205391 |         -8915 |         205391 |        -367 |       266208 |        3378 |       -6830 |
| d   | BOTH  |     120 | A      |            7069 |           -10092 |        -918 |        -6492 |         2337 |         61487 |         -9714 |         116269 |        5544 |       116114 |        5285 |       -6223 |
| d   | BOTH  |     120 | B      |              45 |             -775 |       -4130 |        63570 |       -10245 |        171255 |         -8675 |         126420 |        7542 |       133396 |        -704 |       -7014 |
**All six fail the holdout (HOLD delta mean < 0 and delta maxDD > 0 for each; the closest is (d) SA base A: -0.4k/wk, +17.3k).**

State-ON-share-matched RANDOM-SESSION null for the finalists (200 worlds; same number of flagged sessions per session type, drawn uniformly; RT part real):
| cell         |   real_WF_d_mean |   rank_mean |   real_WF_d_dd |   rank_dd |   null_WF_mean |   null_WF_dd |   real_HOLD_d_mean |   rank_hold_mean |   real_HOLD_d_dd |   rank_hold_dd |
|:-------------|-----------------:|------------:|---------------:|----------:|---------------:|-------------:|-------------------:|-----------------:|-----------------:|---------------:|
| a|SA|0|A     |        -4756.706 |       0.825 |     109323.940 |     0.880 |     -10337.899 |   298407.738 |         -13962.782 |            0.450 |       243484.243 |          0.465 |
| d|SA|0|A     |         3446.675 |       0.980 |     -16104.139 |     0.965 |      -4068.690 |   170169.038 |           -420.873 |            0.775 |        17288.831 |          0.985 |
| d|BOTH|30|A  |        -3485.617 |       0.325 |     109855.646 |     0.655 |      -1914.552 |   155574.054 |         -11492.301 |            0.105 |       244015.950 |          0.055 |
| d|BOTH|60|A  |        -2133.384 |       0.580 |      71230.520 |     0.855 |      -2831.950 |   175106.682 |          -8915.044 |            0.305 |       205390.824 |          0.210 |
| d|BOTH|120|A |         -918.127 |       0.420 |      -6492.234 |     0.985 |         46.650 |   128737.558 |          -9713.686 |            0.120 |       116268.964 |          0.775 |
| d|BOTH|120|B |        -4130.475 |       0.160 |      63569.501 |     0.705 |      -1234.146 |   113419.683 |          -8674.922 |            0.100 |       126420.280 |          0.390 |

### The closest cell: (d) breakout re-arm, SA source, base A
| window   |   system |   benchmark |   d_mean |   sys_maxDD |   bm_maxDD |   d_maxDD |     SD |   bm_SD |   pair_part |   RB_part |   break_sleeve |
|:---------|---------:|------------:|---------:|------------:|-----------:|----------:|-------:|--------:|------------:|----------:|---------------:|
| IS       |    11193 |       13671 |    -2478 |      611073 |     407253 |    203820 | 102494 |   95946 |       13194 |      -598 |          -1402 |
| WFPRE    |    24456 |       17549 |     6907 |      385189 |     401293 |    -16104 | 101662 |   97533 |       21392 |      -534 |           3598 |
| WF       |    28422 |       24975 |     3447 |      385189 |     401293 |    -16104 | 104623 |  104523 |       23928 |      -394 |           4887 |
| L8W      |    34643 |       34191 |      452 |      259962 |     267133 |     -7171 |  87612 |  109399 |       10492 |       133 |          24019 |
| HOLD     |    32378 |       32799 |     -421 |      284422 |     267133 |     17289 | 106737 |  110543 |       26373 |      -233 |           6237 |
| H1       |    20093 |       19569 |      524 |      385189 |     401293 |    -16104 |  98939 |   98934 |       18894 |      -355 |           1554 |
| H2       |    35192 |       29285 |     5907 |      284422 |     267133 |     17289 | 107819 |  108808 |       27933 |      -421 |           7681 |
WF: weekly Sharpe 1.96 vs 1.72; worst week -191k vs -137k; trades/wk 36 pair-engine trades (RB 0.5/wk, break sleeve 2.6/wk over the full 191 weeks). 4-week-block bootstrap (2,000 draws) 90% CI of the WF weekly mean gain [-5.3k, 12.1k] (gate d fails), halves +5.9k / +1.0k; shuffled-state single-cell ranks 0.950 (mean) / 0.935 (maxDD); family-wise rank for family (d) 0.735 on the mean (gate c fails). The gain comes from the MAPPED break sleeve (+4.9k/wk WF, +24k/wk in L8W: natural fills minus the average P9 haircut, no L2 table) while the pair part is -1.0k/wk WF and -23.7k/wk in L8W; the sleeve is the thing the direct replay has to test. In IS the cell is -2.5k/wk with maxDD +204k, and on the holdout -0.4k / +17.3k.

Deflated Sharpe (Bailey & Lopez de Prado, trials = F_P = 3,580, weekly WF returns): BM1 SR(ann) 1.72, DSR 0.23; BM2 SR(ann) 2.31, DSR 0.62; cell d|SA|0|B|True SR(ann) 2.34, DSR 0.64; cell d|RT|120|B|True SR(ann) 2.20, DSR 0.57; cell d|BOTH|60|B|True SR(ann) 2.02, DSR 0.42; FINALIST a|SA|0|A|True SR(ann) 1.55, DSR 0.17; FINALIST d|SA|0|A|True SR(ann) 1.96, DSR 0.34; FINALIST d|BOTH|30|A|True SR(ann) 1.43, DSR 0.11; FINALIST d|BOTH|60|A|True SR(ann) 1.52, DSR 0.14; FINALIST d|BOTH|120|A|True SR(ann) 1.62, DSR 0.18; FINALIST d|BOTH|120|B|True SR(ann) 1.96, DSR 0.42. (With 3,580 trials even the live benchmark BM1 deflates to 0.23; no overlay clears it.)

Keep-mask first version (superseded by ADDENDUM2, kept for transparency): gate (a) passers 0/56; (a) SA base A WF -7.4k/+234k vs regenerated -4.8k/+109k. The regeneration (later signals taken after a skipped entry) changes the (a) cells by a few k/wk and exposes the (d) SA cell. Additivity check that exposed the defect: with all locks off the gating is exactly additive (-14.1k/wk), with the live locks the same gating is -12.7k/wk against an additive expectation of -2.8k/wk: the lock engine is strongly path dependent, which is also why net-per-trade by state (Step 1) does not translate into a gating gain.
## 6. Direct L2 replay of the finalist's mapped components (mapping-vs-replay bias)
Scope: the pair trades of every Step 3 cell use the exact corrected P9 table, so the only mapped (not replayed) components are (1) the break trades of variant (d) and (2) the NEW pair rows created when a skipped entry lets a later signal through. For the closest cell (d, SA, base A; 494 break rows + 587 new pair rows over 44 months) these rows were replayed on raw mbp-10 with exec_engine_l2 (prop queue model, 5 ms latency, S14x1 slice entries, XJ stop-join exits, bracket 240 ticks from each fill) on the months listed below (L8W months first, then FIRM validation months), and the haircut (natural net points minus replay P9-equivalent points) was measured by exit type.
Months replayed: 2023-06, 2023-11, 2024-06, 2024-10, 2025-03, 2025-08, 2026-02, 2026-08, 2026-09, 2026-10; 243 rows; XJ stop-join gain 0.92 pts per stop (validated table: ~1.0). Measured haircut (pts) vs assumed (target +2.62 / stop -1.95 / time-block +1.68): _Target +3.24, _Stop -1.49, _TimeBlock +1.52.
| src     | typ        |   n |   haircut_pts |    sd |   assumed |   bias_pts_per_trade |   bias_$_per_trade_14lots |
|:--------|:-----------|----:|--------------:|------:|----------:|---------------------:|--------------------------:|
| BREAK   | _Stop      |  47 |         -2.79 | 10.68 |     -1.95 |                -0.84 |                   -234.54 |
| BREAK   | _Target    |  62 |          4.25 | 11.70 |      2.62 |                 1.63 |                    455.54 |
| BREAK   | _TimeBlock |   5 |          1.49 |  1.20 |      1.68 |                -0.20 |                    -55.16 |
| NEWPAIR | _Stop      |  57 |         -0.42 |  2.23 |     -1.95 |                 1.53 |                    428.97 |
| NEWPAIR | _Target    |  62 |          2.23 | 13.87 |      2.62 |                -0.39 |                   -109.01 |
| NEWPAIR | _TimeBlock |  10 |          1.54 |  3.55 |      1.68 |                -0.14 |                    -39.66 |

**Re-score of the finalist (d, SA, base A) with the replay-measured haircuts** (BREAK haircut by exit type _Target +4.25, _Stop -2.79, _TimeBlock +1.68; NEWPAIR _Target +2.23, _Stop -0.42, _TimeBlock +1.54 pts; 243 replayed rows over 10 months):

| version                                          |   IS_d_mean |   IS_d_dd |   WFPRE_d_mean |   WFPRE_d_dd |   WF_d_mean |   WF_d_dd |   L8W_d_mean |   L8W_d_dd |   HOLD_d_mean |   HOLD_d_dd |   WF_break_mean |   L8W_break_mean |
|:-------------------------------------------------|------------:|----------:|---------------:|-------------:|------------:|----------:|-------------:|-----------:|--------------:|------------:|----------------:|-----------------:|
| assumed haircuts (average P9)                    |       -2478 |    203820 |           6907 |       -16104 |        3447 |    -16104 |          452 |      -7171 |          -421 |       17289 |            4887 |            24019 |
| replay-measured haircuts by source and exit type |       -2121 |    189739 |           6067 |       -21383 |        2185 |    -21383 |        -1959 |      -2413 |         -2130 |       20762 |            4388 |            22292 |

**Reading (all 10 months complete, 243 of 1,081 mapped rows replayed, i.e. 22%; per-row SD 10-14 pts so cell means have SE ~1.5-2 pts).** Pooled measured haircut: target +3.24 (assumed +2.62), stop -1.49 (-1.95), time-block +1.52 (+1.68). By source: BREAK target +4.25 (bias +1.63 pts = +$456 per trade at 14 lots), BREAK stop -2.79 (bias -0.84), NEWPAIR target +2.23, NEWPAIR stop -0.42 (bias +1.53). Replay exit type matches the natural exit type for 109/110 targets and 99/99 stops; 14 natural targets and 5 stops finished at the session end in the replay. Re-scored with the measured haircuts the cell keeps gate (a) on WF (mean +2.2k/wk, maxDD -21.4k; was +3.4k / -16.1k) but L8W mean turns negative (-2.0k/wk, was +0.5k), the frozen HOLDOUT is -2.1k/wk with maxDD +20.8k worse (was -0.4k / +17.3k) and IS -2.1k / +190k. Family-wise rank (.735 on the mean) and the bootstrap CI were not rescued by the replay (the mean fell), so the cell does NOT clear gates b-d. Verdict unchanged.

## 7. STEP 4 - exhibits
### 4(i) the week 2026-10-19..10-23, hour by hour
The NQ minute tape on disk ends 2026-10-16 (no price bars for 10-19..10-23 exist in data/live or elsewhere on the box, and nothing may be bought), so the state / book-on / would-have-done columns cannot be computed yet. The script is ready and a watcher (outputs/l2vast/fourth/watch_ext.sh, PID in logs/watch_ext.pid) builds out/step4_week_1019_1023.md automatically once the Saturday 10-24 weekly extension raises LAST in ins_env.py to >= 20261023; re-run `make_report*.py` and this section fills in. Dry-run of the same script on the last available week (label days 10-12..10-16) is in out/step4_week_dryrun_W42.md. What is available now - the actual live DualStrat2 trades of the week by ET entry hour (28 trades, net -175.3k, 9 winners / 19 losers; exits Target 8 +134k, StopJoin 8 -133k, StopJoinFallback 9 -160k, StopJoinRejected 1 -17k):
# Live DualStrat2 trades by ET entry hour, week 2026-10-19..10-23 (data/live/StratTrades_DualStrat2_<acct>.csv; times converted CT->ET). State columns PENDING: the NQ minute tape on disk ends 2026-10-16 (weekly extension Sat 10-24).

| hour (ET) | trades entered (book side exit net$) | hour net $ |
|---|---|---|
| Tue 10-20 14:00 | HM L StopJoin -16,205; ST L StopJoinFallback -18,640 | -34,845 |
| Tue 10-20 19:00 | ST L StopJoinFallback -16,730 | -16,730 |
| Tue 10-20 20:00 | ST L Target 16,825 | 16,825 |
| Tue 10-20 21:00 | ST L StopJoin -16,590; HM L StopJoinFallback -17,200 | -33,790 |
| Tue 10-20 22:00 | HM L StopJoinRejected -17,205; ST L StopJoinFallback -16,910 | -34,115 |
| Wed 10-21 02:00 | ST S Target 16,820 | 16,820 |
| Wed 10-21 03:00 | ST S StopJoin -16,805 | -16,805 |
| Wed 10-21 09:00 | ST L StopJoinFallback -17,520 | -17,520 |
| Wed 10-21 20:00 | HM S Target 16,770; HM S StopJoinFallback -18,260 | -1,490 |
| Wed 10-21 21:00 | ST S Target 16,820 | 16,820 |
| Wed 10-21 22:00 | ST S ComboLock -1,330; HM S ComboLock 1,925 | 595 |
| Thu 10-22 19:00 | HM L StopJoinFallback -17,190; ST S Target 16,785 | -405 |
| Thu 10-22 20:00 | HM S Target 16,790 | 16,790 |
| Thu 10-22 21:00 | ST S StopJoinFallback -19,340; ST S StopJoin -16,390; HM L Target 16,830 | -18,900 |
| Thu 10-22 22:00 | ST L Target 16,785; HM L StopJoinFallback -18,090; ST L StopJoin -16,960 | -18,265 |
| Fri 10-23 00:00 | HM L StopJoin -16,740; ST L StopJoin -17,025 | -33,765 |
| Fri 10-23 02:00 | HM S StopJoin -16,520 | -16,520 |

Total 28 trades, net -175,300; by day (label day by exit): see FWD_AB_SETS.md. State (C3 ON/OFF), book-on and the would-have-been trades are filled in automatically by step4_week.py when the tape reaches 2026-10-23 (watcher PID in logs/watch_ext.pid).

### 4(ii) the 10 worst pair weeks of the last 2 years (benchmark weekly P&L, label days >= 2024-10-17, 104 weeks) under the switched system
Change in weekly P&L (system minus benchmark, $) for base A (BM1); columns: variant-source(-dwell); last two = best cell by WF mean / by WF maxDD:
| weeks              |   BM_week |   a-SA |   a-RT60 |   a-BOTH60 |   b-SA |   b-RT60 |   b-BOTH60 |   c-SA |   c-RT60 |   c-BOTH60 |   d-SA |   d-RT60 |   d-BOTH60 |   best-mean d|SA|0|A|True |   best-maxDD d|SA|0|A|True |
|:-------------------|----------:|-------:|---------:|-----------:|-------:|---------:|-----------:|-------:|---------:|-----------:|-------:|---------:|-----------:|--------------------------:|---------------------------:|
| 20251208..20251212 |   -137081 | 226060 |    97948 |     129446 | 139874 |    88404 |     101914 | 123653 |    70584 |      84298 |  -2448 |   -32642 |     -60210 |                     -2448 |                      -2448 |
| 20250707..20250711 |   -137038 |  42844 |    39148 |       9181 |  -3431 |    -8670 |      -7719 |  -4822 |   -14382 |      -9832 |  -8463 |   -24065 |     -33498 |                     -8463 |                      -8463 |
| 20241118..20241122 |   -136494 |   1840 |    13771 |       5067 |     13 |    13005 |       3515 |  13032 |    25026 |      17356 | -14011 |    56124 |     -14011 |                    -14011 |                     -14011 |
| 20250106..20250110 |   -135550 |      0 |    19252 |          0 |      0 |    19090 |          0 | -16533 |   -13064 |     -16533 |      0 |    91631 |          0 |                         0 |                          0 |
| 20241111..20241115 |   -135390 |  85388 |    47014 |      39728 |  38742 |   -28135 |     -18109 |  16984 |   -49330 |     -36394 |   -305 |   -84926 |     -59055 |                      -305 |                       -305 |
| 20260518..20260522 |   -135349 |      0 |   -13499 |          0 |      0 |   -13499 |          0 | -11543 |   -11516 |     -11543 |  16588 |   -46558 |     -17437 |                     16588 |                      16588 |
| 20250811..20250815 |   -135258 |  97220 |     1324 |      -5135 |  65333 |     1057 |      -5135 |  66938 |    -4504 |      -7131 |  51755 |    23843 |     -17964 |                     51755 |                      51755 |
| 20260629..20260703 |   -135251 |  93722 |    18453 |      -3583 |  95084 |   161565 |     115367 | 105714 |   173585 |     122848 | -32428 |    43306 |     -16265 |                    -32428 |                     -32428 |
| 20260420..20260424 |   -134981 | 172620 |    67971 |      77846 | 181183 |   -37812 |      -8878 | 169654 |   -76526 |     -25976 | 175174 |   140491 |      41458 |                    175174 |                     175174 |
| 20250721..20250725 |   -134650 | 111275 |    18241 |       2340 |   4405 |     5267 |       5174 |   4463 |     2175 |       5479 |  51280 |   -12881 |     -18323 |                     51280 |                      51280 |

Change in weekly P&L (system minus benchmark, $) for base B (BM2); columns: variant-source(-dwell); last two = best cell by WF mean / by WF maxDD:
| weeks              |   BM_week |   a-SA |   a-RT60 |   a-BOTH60 |   b-SA |   b-RT60 |   b-BOTH60 |   c-SA |   c-RT60 |   c-BOTH60 |   d-SA |   d-RT60 |   d-BOTH60 |   best-mean d|RT|120|B|True |   best-maxDD d|SA|0|B|True |
|:-------------------|----------:|-------:|---------:|-----------:|-------:|---------:|-----------:|-------:|---------:|-----------:|-------:|---------:|-----------:|----------------------------:|---------------------------:|
| 20250707..20250711 |   -188777 | 116740 |    86833 |      54919 |   7821 |    44305 |      28618 |   6430 |    38594 |      26505 |  47728 |    25642 |      11998 |                       86737 |                      47728 |
| 20260518..20260522 |   -186423 |  41400 |   -14166 |       2288 |  -8813 |   -20187 |      -2004 | -20356 |   -18204 |     -13548 |  16588 |   -20921 |     -17437 |                       65384 |                      16588 |
| 20241118..20241122 |   -151159 |  25272 |   -39299 |     -48103 |  -4929 |    16913 |     -45948 |   8090 |    28934 |     -32107 | -14011 |    48723 |     -14011 |                        1700 |                     -14011 |
| 20260420..20260424 |   -141204 | 187119 |    72834 |      87594 | 143703 |    29165 |      34545 | 132173 |    -9549 |      17447 | 168077 |   211915 |      95070 |                      154991 |                     168077 |
| 20250303..20250307 |   -136919 |      0 |   -16774 |          0 |      0 |   -11660 |          0 | -25690 |   -31033 |     -25690 |      0 |    -5307 |          0 |                      -15608 |                          0 |
| 20260119..20260123 |   -136328 |      0 |    65535 |          0 |      0 |    -5134 |          0 | -20052 |   -25632 |     -20052 |      0 |   -12553 |          0 |                       12013 |                          0 |
| 20250609..20250613 |   -105515 |  77528 |   126260 |      43871 |  47856 |     6330 |       -870 |  39930 |     1941 |      -5395 | -65234 |   -21233 |     -48591 |                       -1907 |                     -65234 |
| 20250721..20250725 |   -105081 |  81085 |     4053 |     -32108 |  -5167 |    -9945 |     -27307 |  -5109 |   -13037 |     -27002 |  -7639 |   -28627 |     -53859 |                      -85691 |                      -7639 |
| 20250811..20250815 |    -96722 |  49952 |  -104717 |     -35167 |  33485 |    -9952 |      -8613 |  35090 |   -15513 |     -10610 |    837 |    16562 |     -26593 |                       38000 |                        837 |
| 20250106..20250110 |    -95336 |      0 |   108365 |          0 |      0 |    97283 |          0 | -16533 |    65129 |     -16533 |      0 |    45906 |          0 |                       68982 |                          0 |

Regression-to-the-mean reference: the same 10 weeks (selected as the benchmark's worst) under 100 SHUFFLED-STATE worlds. Sum over the 10 weeks of (system minus benchmark), real vs null mean +- sd, z:
| base   | cell     |   real sum $ |   null mean $ |   null sd |   null p5 |   null p95 |    z |
|:-------|:---------|-------------:|--------------:|----------:|----------:|-----------:|-----:|
| A      | a-BOTH60 |     254891.1 |      282119.9 |  210580.7 |   -1320.7 |   721435.2 | -0.1 |
| A      | a-RT60   |     309622.2 |      559657.3 |  244097.4 |  199321.9 |   939518.4 | -1.0 |
| A      | a-SA     |     830968.4 |      527322.0 |  232921.2 |  177483.7 |   959315.5 |  1.3 |
| A      | b-BOTH60 |     186128.7 |      138820.6 |  138696.7 |  -31979.3 |   398129.0 |  0.3 |
| A      | b-RT60   |     200271.1 |      287094.5 |  188813.0 |   30245.4 |   640887.6 | -0.5 |
| A      | b-SA     |     521204.3 |      247255.8 |  156357.5 |   16731.3 |   559520.1 |  1.8 |
| A      | d-BOTH60 |    -195305.0 |       81990.9 |  166429.0 | -161373.5 |   362075.6 | -1.7 |
| A      | d-RT60   |     154322.7 |      127152.6 |  268476.9 | -273160.0 |   547072.4 |  0.1 |
| A      | d-SA     |     237140.7 |       69236.7 |  115934.8 | -107722.6 |   248567.9 |  1.4 |
| B      | a-BOTH60 |      73293.1 |      148964.9 |  146009.2 | -110877.2 |   409110.5 | -0.5 |
| B      | a-RT60   |     288924.9 |      248813.6 |  207751.7 |  -69588.9 |   561004.1 |  0.2 |
| B      | a-SA     |     579096.1 |      436981.8 |  187061.6 |  178918.8 |   727676.3 |  0.8 |
| B      | b-BOTH60 |     -21578.8 |       35120.7 |   92267.3 | -127251.7 |   185957.2 | -0.6 |
| B      | b-RT60   |     137117.4 |       69069.2 |  109366.2 | -125378.9 |   234115.2 |  0.6 |
| B      | b-SA     |     213955.8 |      134247.9 |  125067.2 |  -54680.6 |   328552.5 |  0.6 |
| B      | d-BOTH60 |     -53422.6 |      -18521.7 |  123147.5 | -170676.6 |   190784.5 | -0.3 |
| B      | d-RT60   |     260106.9 |     -112579.2 |  220035.4 | -404019.1 |   240899.7 |  1.7 |
| B      | d-SA     |     146344.6 |       66340.0 |  120819.8 | -105937.8 |   249145.0 |  0.7 |
The switched system "protects" the benchmark's worst weeks (sums of +0.1M..+0.8M over 10 weeks) but random states do the same: |z| <= 1.8 in all 18 comparisons. The benchmark's worst weeks are selected as the worst, so any perturbation improves them on average; the apparent protection is not skill.

## 8. STEP 5 - deliverable and verdict
* The switched system does NOT beat the benchmark on weekly mean AND maxDD walk-forward with clean nulls (live spec or Set B). No FOURTH_BOOK_SPEC.md. No gate a-d passer (the closest, (d) SA base A, passes a and b, fails c family-wise on the mean (.735), fails d (CI [-5.3k,+12.1k]) and the frozen holdout), so no LEADS_FROZEN_FOURTH.json, no forward shadow script, nothing registered in PAPER-ALL.
* The step-0 failure profile and the best range-book table are in sections 2 and 4. The one structural result worth keeping: the range books are a real hedge to the pair's failures (they win in exactly the sessions where the pair loses, rank 1.000 against shifted flags) but the failing sessions are non-directional days of normal volatility, which neither the vol forecaster (compression), the L2 book state, nor the first hour identifies well enough (failure AUC .59-.66) to harvest them after cost.
* What would have to be true for a fourth book: a session-direction predictor that raises failure AUC from .6-.66 to roughly .8+ in the first 30-60 minutes (NY first hour .72-.77 is the only place it is close), or a range book with positive gross points in unconditioned sessions (all 54 simulations are negative gross). Neither exists in the current data. A different family - breakout of the session range after >= 30 minutes in predicted-quiet sessions (the (d) break sleeve, WF +4.9k/wk on MAPPED fills) - is the only positive component found; it is a candidate for its own pre-registered test with a direct-replay price model, not a result.
* Caveats: (1) maxDD comparisons against the live benchmark are dominated by path dependence of the lock engine (random 10% entry removal: +53k maxDD); (2) all range-book fills are simulated on 1-s closes with a conservative through-1-tick rule - the direct L2 replay of a range-book finalist was not run because no range book is a finalist (the verdict is gross-negative before any cost); (3) the 2023-02..2023-03 sessions have no 20-day warm-up (state undefined = OFF); (4) the first 3,561 families of F_P are the lead's count; this report adds 19.

## 9. Files
Prereg + addenda: l2vast/PREREG_FOURTH_BOOK.md (+ .sha256, .frozen.md), PREREG_FOURTH_BOOK_ADDENDUM1/2.md. Code and tables: l2vast/fourth/ (flib, sesstab, feats_sess, clf03, clf04, rtstate, step1_eval, rbbook, step2_run, step2_null, step3lib, gatedrows, step3_run, step3_null, step3_gates, step3_null_random, step4_worst, step4_rtm, step4_week, replay_eval, make_report*.py; out/ for CSV/MD/logs). Progress: autopilot/FOURTH_BOOK_PROGRESS.md; MORNING.md block FOURTH; DECISIONS.md lines.
