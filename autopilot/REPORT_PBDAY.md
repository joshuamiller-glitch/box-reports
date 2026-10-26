# REPORT_PBDAY - per-book day-loss limit l in {2R,3R,4R,off}, TH-off pair, exact 1-s engine (trackFIRM, 2026-10-23)
Prereg: l2vast/PREREG_PBDAY.md sha256 28745a4c040d2d541d0aee1e5e0499c9547e8ff036c53ef1a7dc75b1541d6392 (frozen before scoring; disclosure: the four LIVE-layer WF means 24,978/22,115/24,726/23,602 were printed once in an engine-equivalence check right before the freeze, nothing was selected on them). 19 cells, 9,000 null worlds, DSR trials n=3,601 (F_P 3,580 + 19 + 2).

## VERDICT (6 lines)
1. NOT SUPPORTED, live layer: relaxing -2R to -3R/-4R/off does not help the TH-off pair. WF weekly mean -2.9k / -0.3k / -1.4k vs -2R (24,978), bootstrap 90% CI of each delta spans 0 (e.g. -4R: [-6.0k,+6.0k]); maxDD gets worse 401k -> 431k/439k/506k and WORST DAY -101k -> -134k/-167k/-221k; IS collapses 13.7k -> 10.3k/3.0k/3.1k; only 4-6 of 11 folds are better on mean.
2. NOT SUPPORTED, Set B: the TH-audit lead reproduces in sign on this engine (Set B off +2.4k/wk = +0.34M over 142 wk; 3R +0.9k; 4R +0.3k vs Set B -2R) but is inside noise: CI vs Set B -2R [-2.6k,+7.5k] (off), [-3.6k,+5.8k] (3R); null rank on the hazard placebo 0.61 (3R) and on the shuffled-date placebo 0.20 (3R) / 0.00 (4R); only 6 of 11 folds better; maxDD +1% to +9% worse, WORST DAY -97k -> -132k/-146k/-186k, IS 10.3k -> 7.6k/7.3k/7.8k.
3. The -2R rule itself is mostly structure, not edge: vs random-trigger and shuffled-date rules of the same count/hours its WF mean rank at -2R is 0.36 / 0.60 (live hazard / shuffled) and 0.79 / 0.29 (Set B), i.e. not distinguishable from chance on the mean (the 3R/4R cells rank 0.09-0.84 live and 0.00-0.86 across Set B readings, never above the 0.90 bar); what it reliably does is cut risk (maxDD rank 0.78-0.99 live and 0.91-0.99 Set B across l; worst day halved vs off). So keep -2R as a risk limiter; do not read it as alpha, and do not relax it for money.
4. Reading of R: DualStrat.cs takes St/Wt/HmMaxDailyLoss as a FIXED dollar input (default 19,200 = 2 x 9,600 at 8/8) tested against the book's realized DayPnl, so the code-faithful Set B reading is fixed $ (14-lot R) in every session; the R-scaled reading (limit shrinks to 10/14 in London/NY entries) gives 31.9k/35.2k/33.3k at 2R/3R/4R: lowest maxDD of the whole study (R-scaled 3R: WF 35.2k, maxDD 318k) but it is one of 19 and fails the rules (hazard rank 0.86, shuffled 0.60, DSR 0.972 at n=3,601).
5. Walk-forward choice of l per fold does not beat fixed -2R: live rule M 22.6k (vs 25.0k fixed -2R), rule C 25.7k; Set B rule M 32.5k, rule C 33.3k (vs fixed -2R 33.1k) with maxDD 349k vs 320k. Frozen holdout (fit to 2025-06-30, scored 2025-07..2026-10): the 3 chosen cells are all l=-2R Set B variants (39.3k, 38.8k, 34.4k vs live -2R 32.8k); in hindsight Set B 3R/off scored 45k there, so the holdout does not contradict the lead, it just did not select it.
6. Joint cell (Set B x best l): the best-by-WF is Set B off (35.5k) = selection among 19; the only reading that survives is Set B itself (+8.1k vs live -2R, CI [+1.8k,+15.1k], DSR 0.975) - the day-loss limit adds nothing on top inside Set B beyond noise and costs worst day (-97k -> -186k at off). No gate changed; nothing live.

## T1 base grid (A), $k, report scale x1.75
| cell | IS mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk | WF mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk | L8W mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk |
|---|---|---|---|
| A|LIVE|2R | 13.7 / 95.9 / 407.5 / -136.3 / -79.1 / 1.03 / 26.8 | 25.0 / 104.5 / 401.6 / -137.1 / -100.8 / 1.72 / 35.9 | 34.2 / 109.4 / 267.1 / -98.9 / -100.3 / 2.25 / 40.8 |
| A|LIVE|3R | 10.3 / 100.1 / 490.0 / -138.1 / -112.3 / 0.74 / 30.0 | 22.1 / 115.0 / 431.1 / -145.8 / -133.8 / 1.39 / 39.4 | 38.2 / 127.3 / 267.4 / -140.9 / -114.4 / 2.17 / 47.6 |
| A|LIVE|4R | 3.0 / 103.9 / 671.0 / -136.8 / -139.2 / 0.21 / 30.5 | 24.7 / 115.4 / 439.5 / -139.7 / -167.2 / 1.55 / 41.6 | 38.7 / 132.3 / 277.2 / -133.8 / -131.9 / 2.11 / 48.8 |
| A|LIVE|off | 3.1 / 104.9 / 661.2 / -142.2 / -158.2 / 0.21 / 30.3 | 23.6 / 119.5 / 505.9 / -140.3 / -220.6 / 1.42 / 42.2 | 37.0 / 134.2 / 284.2 / -136.2 / -142.3 / 1.99 / 50.8 |
| A|SETB|2R | 10.3 / 83.6 / 376.1 / -201.4 / -86.0 / 0.88 / 32.7 | 33.1 / 106.7 / 320.1 / -189.5 / -96.5 / 2.24 / 45.2 | 57.0 / 124.8 / 209.1 / -95.4 / -81.0 / 3.29 / 49.6 |
| A|SETB|3R | 7.6 / 82.3 / 488.0 / -201.5 / -119.1 / 0.67 / 34.3 | 34.0 / 119.3 / 323.9 / -203.1 / -131.5 / 2.06 / 49.9 | 53.1 / 146.2 / 274.5 / -135.9 / -119.5 / 2.62 / 54.4 |
| A|SETB|4R | 7.3 / 83.6 / 524.2 / -202.0 / -121.2 / 0.63 / 34.9 | 33.4 / 122.3 / 332.1 / -203.1 / -146.1 / 1.97 / 52.3 | 53.0 / 155.0 / 303.1 / -149.2 / -115.3 / 2.47 / 56.1 |
| A|SETB|off | 7.8 / 83.2 / 512.7 / -202.1 / -120.6 / 0.68 / 35.2 | 35.5 / 122.1 / 349.2 / -203.4 / -185.8 / 2.10 / 53.7 | 53.9 / 154.2 / 308.3 / -154.3 / -119.7 / 2.52 / 58.1 |

## T1b profit rule off (B)
| cell | IS mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk | WF mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk | L8W mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk |
|---|---|---|---|
| B|LIVE|2R|nopft | 13.7 / 95.9 / 407.5 / -136.3 / -79.1 / 1.03 / 26.8 | 25.2 / 103.9 / 401.6 / -137.1 / -100.8 / 1.75 / 36.0 | 32.8 / 107.1 / 267.1 / -98.9 / -100.3 / 2.21 / 41.0 |
| B|LIVE|3R|nopft | 10.3 / 100.1 / 490.0 / -138.1 / -112.3 / 0.74 / 30.0 | 22.7 / 115.6 / 431.1 / -145.8 / -133.8 / 1.41 / 39.5 | 39.5 / 129.8 / 267.4 / -140.9 / -114.4 / 2.19 / 47.5 |
| B|LIVE|4R|nopft | 3.0 / 103.9 / 671.0 / -136.8 / -139.2 / 0.21 / 30.5 | 25.1 / 115.8 / 422.7 / -139.7 / -167.2 / 1.56 / 41.6 | 40.1 / 135.1 / 277.2 / -133.8 / -131.9 / 2.14 / 48.5 |
| B|LIVE|off|nopft | 3.1 / 104.9 / 661.2 / -142.2 / -158.2 / 0.21 / 30.3 | 24.0 / 119.9 / 505.9 / -140.3 / -220.6 / 1.44 / 42.2 | 38.4 / 136.9 / 284.2 / -136.2 / -142.3 / 2.02 / 50.5 |
| B|SETB|2R|nopft | 10.3 / 83.6 / 376.1 / -201.4 / -86.0 / 0.88 / 32.7 | 33.0 / 107.7 / 320.1 / -189.5 / -96.5 / 2.21 / 45.9 | 64.5 / 139.7 / 209.1 / -95.4 / -81.0 / 3.33 / 50.2 |
| B|SETB|3R|nopft | 7.6 / 82.3 / 488.0 / -201.5 / -119.1 / 0.67 / 34.3 | 34.1 / 120.6 / 323.9 / -203.1 / -131.5 / 2.04 / 50.6 | 60.5 / 162.0 / 274.5 / -135.9 / -119.5 / 2.69 / 55.0 |
| B|SETB|4R|nopft | 7.3 / 83.6 / 524.2 / -202.0 / -121.2 / 0.63 / 34.9 | 33.4 / 123.6 / 332.1 / -203.1 / -146.1 / 1.95 / 53.1 | 60.5 / 170.1 / 303.1 / -149.2 / -115.3 / 2.56 / 56.8 |
| B|SETB|off|nopft | 7.8 / 83.2 / 512.7 / -202.1 / -120.6 / 0.68 / 35.2 | 35.5 / 123.0 / 349.2 / -203.4 / -185.8 / 2.08 / 54.5 | 61.4 / 169.2 / 308.3 / -154.3 / -119.7 / 2.62 / 58.8 |

## T1c Set B R-scaled (C)
| cell | IS mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk | WF mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk | L8W mean/SD/maxDD/worstwk/worstday/Sharpe/tr-wk |
|---|---|---|---|
| C|SETB|2R|Rscaled | 9.8 / 82.3 / 382.2 / -202.9 / -68.8 / 0.86 / 29.6 | 31.9 / 107.6 / 384.3 / -203.3 / -96.5 / 2.14 / 40.9 | 38.1 / 143.7 / 328.1 / -121.0 / -82.4 / 1.91 / 45.2 |
| C|SETB|3R|Rscaled | 10.8 / 81.9 / 401.2 / -201.9 / -93.3 / 0.95 / 33.2 | 35.2 / 113.8 / 317.8 / -202.2 / -131.5 / 2.23 / 47.2 | 50.1 / 124.4 / 247.8 / -109.2 / -94.7 / 2.91 / 53.0 |
| C|SETB|4R|Rscaled | 7.5 / 82.5 / 495.3 / -201.5 / -119.1 / 0.65 / 34.3 | 33.3 / 119.0 / 336.6 / -202.5 / -146.1 / 2.02 / 50.1 | 52.5 / 147.0 / 278.6 / -140.0 / -112.2 / 2.58 / 54.4 |

## T2 per-day diagnostics (A and C)
| cell | window | attempts/day (active) | targets/day | stops/day | halted-day share (cal) | typical halt ET | $/active day | $/calendar day |
|---|---|---|---|---|---|---|---|---|
| A|LIVE|2R | WF | 7.64 | 3.96 | 3.49 | 31% | 09:49 | 5,310 | 5,060 |
| A|LIVE|2R | L8W | 8.15 | 4.28 | 3.75 | 38% | 09:59 | 6,842 | 6,842 |
| A|LIVE|3R | WF | 8.64 | 4.42 | 3.98 | 17% | 10:33 | 4,846 | 4,480 |
| A|LIVE|3R | L8W | 9.53 | 4.90 | 4.38 | 15% | 09:34 | 7,645 | 7,645 |
| A|LIVE|4R | WF | 9.11 | 4.67 | 4.18 | 7% | 10:29 | 5,418 | 5,009 |
| A|LIVE|4R | L8W | 9.75 | 5.05 | 4.47 | 8% | 09:25 | 7,746 | 7,746 |
| A|LIVE|off | WF | 9.41 | 4.82 | 4.32 | 0% | - | 5,261 | 4,781 |
| A|LIVE|off | L8W | 10.15 | 5.22 | 4.67 | 0% | - | 7,402 | 7,402 |
| A|SETB|2R | WF | 9.15 | 4.71 | 4.15 | 27% | 09:51 | 6,707 | 6,707 |
| A|SETB|2R | L8W | 9.93 | 5.22 | 4.45 | 25% | 09:59 | 11,403 | 11,403 |
| A|SETB|3R | WF | 10.16 | 5.22 | 4.63 | 13% | 10:12 | 6,936 | 6,896 |
| A|SETB|3R | L8W | 10.88 | 5.62 | 4.95 | 12% | 08:32 | 10,612 | 10,612 |
| A|SETB|4R | WF | 10.68 | 5.46 | 4.88 | 6% | 10:24 | 6,806 | 6,758 |
| A|SETB|4R | L8W | 11.22 | 5.80 | 5.08 | 8% | 12:20 | 10,604 | 10,604 |
| A|SETB|off | WF | 11.02 | 5.64 | 5.03 | 0% | - | 7,282 | 7,188 |
| A|SETB|off | L8W | 11.62 | 6.00 | 5.25 | 0% | - | 10,790 | 10,790 |
| C|SETB|2R|Rscaled | WF | 8.32 | 4.31 | 3.78 | 37% | 09:28 | 6,486 | 6,458 |
| C|SETB|2R|Rscaled | L8W | 9.05 | 4.65 | 4.22 | 38% | 09:54 | 7,616 | 7,616 |
| C|SETB|3R|Rscaled | WF | 9.58 | 4.94 | 4.35 | 23% | 09:54 | 7,136 | 7,126 |
| C|SETB|3R|Rscaled | L8W | 10.60 | 5.47 | 4.85 | 15% | 07:25 | 10,029 | 10,029 |
| C|SETB|4R|Rscaled | WF | 10.20 | 5.23 | 4.65 | 14% | 10:05 | 6,779 | 6,750 |
| C|SETB|4R|Rscaled | L8W | 10.88 | 5.62 | 4.95 | 12% | 08:32 | 10,509 | 10,509 |

## T3 nulls (500 worlds each; hazard = random-trigger by session hazard matched on count/hours-of-session; shuf = real halt minutes transplanted onto permuted dates). rank_mean = share of worlds the real cell beats; rank_dd = share of worlds with larger maxDD; rank_gain_vs_off = rank of the improvement over l=off
| cell | kind | n_halt_bookdays | real_WF_mean | null_mean | rank_mean | real_WF_dd | null_dd | rank_dd | rank_l8w | rank_gain_vs_off |
|---|---|---|---|---|---|---|---|---|---|---|
| A|LIVE|2R | haz | 396 | 24,978 | 26,718 | 0.364 | 401,641 | 531,357 | 0.858 | 0.302 | 0.364 |
| A|LIVE|2R | shuf | 396 | 24,978 | 24,249 | 0.596 | 401,641 | 516,468 | 0.924 | 0.250 | 0.596 |
| A|LIVE|3R | haz | 180 | 22,115 | 26,729 | 0.086 | 431,064 | 510,292 | 0.784 | 0.462 | 0.086 |
| A|LIVE|3R | shuf | 180 | 22,115 | 23,918 | 0.144 | 431,064 | 511,782 | 0.954 | 0.644 | 0.144 |
| A|LIVE|4R | haz | 71 | 24,726 | 25,567 | 0.368 | 439,475 | 504,259 | 0.830 | 0.532 | 0.368 |
| A|LIVE|4R | shuf | 71 | 24,726 | 23,742 | 0.844 | 439,475 | 509,901 | 0.990 | 0.786 | 0.844 |
| A|SETB|2R | haz | 295 | 33,109 | 30,512 | 0.790 | 320,103 | 413,545 | 0.952 | 0.788 | 0.790 |
| A|SETB|2R | shuf | 295 | 33,109 | 34,243 | 0.290 | 320,103 | 360,892 | 0.936 | 0.740 | 0.290 |
| A|SETB|3R | haz | 130 | 34,044 | 33,470 | 0.608 | 323,902 | 380,374 | 0.936 | 0.616 | 0.608 |
| A|SETB|3R | shuf | 130 | 34,044 | 35,051 | 0.204 | 323,902 | 354,619 | 0.980 | 0.342 | 0.204 |
| A|SETB|4R | haz | 50 | 33,361 | 34,690 | 0.204 | 332,078 | 363,064 | 0.910 | 0.528 | 0.204 |
| A|SETB|4R | shuf | 50 | 33,361 | 35,345 | 0.004 | 332,078 | 351,418 | 0.994 | 0.170 | 0.004 |
| C|SETB|2R|Rscaled | haz | 482 | 31,881 | 29,395 | 0.770 | 384,299 | 411,699 | 0.618 | 0.336 | 0.770 |
| C|SETB|2R|Rscaled | shuf | 482 | 31,881 | 33,648 | 0.222 | 384,299 | 362,152 | 0.232 | 0.056 | 0.222 |
| C|SETB|3R|Rscaled | haz | 247 | 35,179 | 32,437 | 0.856 | 317,792 | 386,337 | 0.914 | 0.556 | 0.856 |
| C|SETB|3R|Rscaled | shuf | 247 | 35,179 | 34,790 | 0.596 | 317,792 | 354,779 | 0.954 | 0.248 | 0.596 |
| C|SETB|4R|Rscaled | haz | 140 | 33,322 | 33,733 | 0.436 | 336,607 | 371,422 | 0.846 | 0.588 | 0.436 |
| C|SETB|4R|Rscaled | shuf | 140 | 33,322 | 35,117 | 0.052 | 336,607 | 353,494 | 0.918 | 0.302 | 0.052 |

## T4 fold stability (11 folds, test windows 3 months; rank 1 = best of 4 l)
| layer | l | mean_rank_avg | mean_rank_1st | dd_rank_avg | dd_rank_1st | folds_mean_better_than_2R | folds_dd_better_than_2R | first_half_delta_vs2R | second_half_delta_vs2R |
|---|---|---|---|---|---|---|---|---|---|
| LIVE | 2R | 2.364 | 4 | 1.818 | 7 |  |  |  |  |
| LIVE | 3R | 2.727 | 2 | 2.455 | 1 | 4.000 | 1.000 | -6,280 | -59.350 |
| LIVE | 4R | 2.455 | 2 | 2.636 | 1 | 5.000 | 4.000 | -3,531 | 2,438 |
| LIVE | off | 2.455 | 3 | 3.091 | 2 | 6.000 | 4.000 | -2,730 | -265 |
| SETB | 2R | 2.636 | 4 | 1.727 | 8 |  |  |  |  |
| SETB | 3R | 2.818 | 1 | 2.545 | 0 | 6.000 | 2.000 | -2,788 | 3,990 |
| SETB | 4R | 2.545 | 2 | 2.636 | 2 | 6.000 | 3.000 | -1,048 | 1,319 |
| SETB | off | 2.000 | 4 | 3.091 | 1 | 6.000 | 3.000 | 1,247 | 3,303 |
Per-fold values: out/pbday/fold_mean_*.csv, fold_dd_*.csv.


## T5 walk-forward l choice (concatenated 11-fold OOS; rule M = best fit-window mean, rule C = mean/maxDD) vs fixed l on the same OOS days
| layer | rule | chosen_l | OOS_mean | OOS_sd | OOS_maxdd | OOS_worst_day | OOS_worst_wk |
|---|---|---|---|---|---|---|---|
| LIVE | M | 2R 2R 2R off 2R 2R 2R 2R 3R 4R 4R | 22,648 | 112,691 | 401,641 | -163,453 | -139,699 |
| LIVE | C | 2R 2R 2R 2R 2R 2R 2R 2R 2R 2R 4R | 25,746 | 106,135 | 401,641 | -131,874 | -137,081 |
| LIVE | fixed 2R | nan | 24,978 | 104,547 | 401,641 | -100,752 | -137,081 |
| LIVE | fixed 3R | nan | 22,115 | 114,992 | 431,064 | -133,786 | -145,812 |
| LIVE | fixed 4R | nan | 24,726 | 115,402 | 439,475 | -167,152 | -139,699 |
| LIVE | fixed off | nan | 23,602 | 119,538 | 505,869 | -220,626 | -140,325 |
| SETB | M | 2R 2R off off off off 2R 2R 2R off 3R | 32,505 | 116,454 | 349,152 | -185,848 | -203,434 |
| SETB | C | 2R off off 4R off 2R 2R 2R 2R 2R 2R | 33,298 | 109,045 | 349,152 | -185,848 | -203,434 |
| SETB | fixed 2R | nan | 33,109 | 106,710 | 320,103 | -96,532 | -189,464 |
| SETB | fixed 3R | nan | 34,044 | 119,323 | 323,902 | -131,542 | -203,071 |
| SETB | fixed 4R | nan | 33,361 | 122,283 | 332,078 | -146,089 | -203,053 |
| SETB | fixed off | nan | 35,485 | 122,064 | 349,152 | -185,848 | -203,434 |

## T6 bootstrap 90% CI of WF weekly-mean difference (4-wk blocks, 2,000 draws); first block vs live -2R, second vs same-layer -2R (Set B)
| cell | delta_vs_live2R | ci_lo | ci_hi | delta_vs_setB2R | ci2_lo | ci2_hi |
|---|---|---|---|---|---|---|
| A|LIVE|2R | 0.000 | 0.000 | 0.000 |  |  |  |
| A|LIVE|3R | -2,863 | -7,845 | 2,955 |  |  |  |
| A|LIVE|4R | -252 | -5,996 | 5,954 |  |  |  |
| A|LIVE|off | -1,376 | -8,376 | 5,923 |  |  |  |
| A|SETB|2R | 8,131 | 1,808 | 15,092 | 0.000 | 0.000 | 0.000 |
| A|SETB|3R | 9,066 | 1,007 | 17,627 | 935 | -3,587 | 5,795 |
| A|SETB|4R | 8,383 | -237 | 17,109 | 252 | -4,611 | 5,074 |
| A|SETB|off | 10,507 | 1,536 | 19,474 | 2,376 | -2,594 | 7,495 |
| B|LIVE|2R|nopft | 261 | -451 | 1,132 |  |  |  |
| B|LIVE|3R|nopft | -2,297 | -7,400 | 3,552 |  |  |  |
| B|LIVE|4R|nopft | 96.147 | -5,636 | 6,428 |  |  |  |
| B|LIVE|off|nopft | -1,028 | -8,051 | 6,214 |  |  |  |
| B|SETB|2R|nopft | 8,016 | 1,406 | 15,210 | -115 | -1,439 | 1,159 |
| B|SETB|3R|nopft | 9,125 | 950 | 17,689 | 994 | -3,772 | 6,134 |
| B|SETB|4R|nopft | 8,442 | -348 | 17,263 | 312 | -4,715 | 5,390 |
| B|SETB|off|nopft | 10,566 | 1,551 | 19,603 | 2,436 | -2,684 | 7,456 |
| C|SETB|2R|Rscaled | 6,902 | 165 | 14,429 | -1,228 | -5,044 | 2,603 |
| C|SETB|3R|Rscaled | 10,200 | 3,004 | 17,646 | 2,070 | -1,300 | 6,116 |
| C|SETB|4R|Rscaled | 8,344 | 475 | 16,593 | 213 | -4,136 | 4,802 |

## T7 deflated Sharpe (n_trials=3,601: F_P 3,580 + 19 cells + 2 selection rules; trial-SR variance across 19 cells)
| cell | SR_week | SR0 | DSR |
|---|---|---|---|
| A|LIVE|2R | 0.239 | 0.150 | 0.856 |
| A|LIVE|3R | 0.192 | 0.150 | 0.695 |
| A|LIVE|4R | 0.214 | 0.150 | 0.780 |
| A|SETB|2R | 0.310 | 0.150 | 0.975 |
| A|SETB|3R | 0.285 | 0.150 | 0.949 |
| A|SETB|4R | 0.273 | 0.150 | 0.930 |
| B|LIVE|2R|nopft | 0.243 | 0.150 | 0.865 |
| B|LIVE|3R|nopft | 0.196 | 0.150 | 0.711 |
| B|LIVE|4R|nopft | 0.217 | 0.150 | 0.789 |
| B|SETB|2R|nopft | 0.306 | 0.150 | 0.974 |
| B|SETB|3R|nopft | 0.283 | 0.150 | 0.947 |
| B|SETB|4R|nopft | 0.270 | 0.150 | 0.927 |
| C|SETB|2R|Rscaled | 0.296 | 0.150 | 0.960 |
| C|SETB|3R|Rscaled | 0.309 | 0.150 | 0.972 |
| C|SETB|4R|Rscaled | 0.280 | 0.150 | 0.941 |

## T8 frozen holdout (rank fit 2023-02-10..2025-06-30; score 2025-07-01..2026-10-16; the 3 top fit cells flagged)
| cell | fit_mean | fit_rank | top3 | HO_mean | HO_sd | HO_maxdd | HO_worst_day | HO_worst_wk |
|---|---|---|---|---|---|---|---|---|
| A|LIVE|2R | 16,080 | 13 | False | 32,807 | 110,567 | 267,133 | -100,332 | -137,081 |
| A|LIVE|3R | 11,878 | 15 | False | 32,036 | 124,656 | 300,950 | -133,786 | -140,861 |
| A|LIVE|4R | 9,677 | 17 | False | 35,965 | 125,529 | 277,185 | -167,152 | -139,699 |
| A|LIVE|off | 9,024 | 19 | False | 34,903 | 129,198 | 333,198 | -183,074 | -137,063 |
| A|SETB|2R | 20,625 | 2 | True | 38,765 | 115,986 | 256,350 | -96,532 | -189,464 |
| A|SETB|3R | 16,808 | 10 | False | 45,774 | 133,396 | 312,704 | -131,542 | -203,071 |
| A|SETB|4R | 17,771 | 7 | False | 42,356 | 139,109 | 303,071 | -146,089 | -203,053 |
| A|SETB|off | 18,907 | 5 | False | 45,032 | 137,845 | 313,208 | -175,360 | -203,053 |
| B|LIVE|2R|nopft | 16,324 | 12 | False | 32,900 | 109,072 | 267,133 | -100,332 | -137,081 |
| B|LIVE|3R|nopft | 12,122 | 14 | False | 32,766 | 125,558 | 300,950 | -133,786 | -140,861 |
| B|LIVE|4R|nopft | 9,921 | 16 | False | 36,240 | 125,971 | 277,185 | -167,152 | -139,699 |
| B|LIVE|off|nopft | 9,268 | 18 | False | 35,178 | 129,641 | 333,198 | -183,074 | -137,063 |
| B|SETB|2R|nopft | 20,215 | 3 | True | 39,286 | 117,143 | 256,350 | -96,532 | -189,464 |
| B|SETB|3R|nopft | 16,398 | 11 | False | 46,657 | 134,830 | 312,704 | -131,542 | -203,071 |
| B|SETB|4R|nopft | 17,361 | 8 | False | 43,240 | 140,506 | 303,071 | -146,089 | -203,053 |
| B|SETB|off|nopft | 18,496 | 6 | False | 45,916 | 139,238 | 313,208 | -175,360 | -203,053 |
| C|SETB|2R|Rscaled | 21,388 | 1 | True | 34,418 | 118,583 | 328,109 | -96,532 | -198,747 |
| C|SETB|3R|Rscaled | 19,864 | 4 | False | 44,936 | 127,538 | 307,926 | -131,542 | -202,163 |
| C|SETB|4R|Rscaled | 16,916 | 9 | False | 43,958 | 132,463 | 336,607 | -146,089 | -202,538 |

## T9 interaction with the other locks (remove one lock at a time, profit +5R on; fires = lock fires over the full sample; pb_skips = entries skipped by the per-book rules)
| layer | l | removed | WF_mean | WF_dd | WF_worst_day | IS_mean | L8W_mean | fires_cap | fires_gb | fires_wk | pb_skips |
|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE | 2R | none | 24,978 | 401,641 | -100,752 | 13,654 | 34,209 | 30.000 | 435 | 26.000 | 2,022 |
| LIVE | 2R | cap | 30,077 | 370,037 | -100,752 | 13,887 | 41,639 | 0.000 | 437 | 26.000 | 2,147 |
| LIVE | 2R | wk | 29,183 | 324,952 | -100,752 | 18,746 | 34,209 | 31.000 | 459 | 0.000 | 2,268 |
| LIVE | 2R | gb | 39,471 | 646,510 | -100,752 | 1,317 | 68,738 | 68.000 | 0.000 | 41.000 | 2,672 |
| LIVE | 3R | none | 22,115 | 431,064 | -133,786 | 10,282 | 38,224 | 31.000 | 449 | 37.000 | 768 |
| LIVE | 3R | cap | 26,914 | 402,601 | -133,786 | 10,515 | 45,653 | 0.000 | 449 | 38.000 | 895 |
| LIVE | 3R | wk | 27,942 | 348,452 | -133,843 | 21,056 | 35,137 | 33.000 | 494 | 0.000 | 1,031 |
| LIVE | 3R | gb | 36,598 | 750,476 | -133,786 | 3,454 | 70,537 | 71.000 | 0.000 | 46.000 | 1,214 |
| LIVE | 4R | none | 24,726 | 439,475 | -167,152 | 2,957 | 38,732 | 31.000 | 461 | 36.000 | 334 |
| LIVE | 4R | cap | 29,724 | 439,475 | -167,152 | 3,190 | 46,162 | 0.000 | 461 | 37.000 | 462 |
| LIVE | 4R | wk | 26,177 | 463,235 | -167,152 | 14,843 | 32,369 | 33.000 | 505 | 0.000 | 500 |
| LIVE | 4R | gb | 35,222 | 831,137 | -167,152 | -2,228 | 114,128 | 69.000 | 0.000 | 50.000 | 601 |
| LIVE | off | none | 23,602 | 505,869 | -220,626 | 3,056 | 37,010 | 31.000 | 450 | 43.000 | 23.000 |
| LIVE | off | cap | 29,088 | 505,869 | -220,626 | 3,290 | 44,440 | 0.000 | 452 | 43.000 | 157 |
| LIVE | off | wk | 28,468 | 493,989 | -230,417 | 16,503 | 28,426 | 33.000 | 506 | 0.000 | 23.000 |
| LIVE | off | gb | 37,548 | 872,238 | -230,417 | -1,108 | 113,305 | 71.000 | 0.000 | 53.000 | 117 |
| SETB | 2R | none | 33,109 | 320,103 | -96,532 | 10,256 | 57,013 | 0.000 | 392 | 1.000 | 1,881 |
| SETB | 2R | cap | 33,109 | 320,103 | -96,532 | 10,256 | 57,013 | 0.000 | 392 | 1.000 | 1,881 |
| SETB | 2R | wk | 33,109 | 320,103 | -96,532 | 11,930 | 57,013 | 0.000 | 393 | 0.000 | 1,881 |
| SETB | 2R | gb | 35,502 | 614,933 | -95,071 | 6,292 | 35,795 | 0.000 | 0.000 | 7.000 | 2,311 |
| SETB | 3R | none | 34,044 | 323,902 | -131,542 | 7,619 | 53,058 | 0.000 | 407 | 7.000 | 814 |
| SETB | 3R | cap | 34,044 | 323,902 | -131,542 | 7,619 | 53,058 | 0.000 | 407 | 7.000 | 814 |
| SETB | 3R | wk | 35,157 | 323,902 | -131,542 | 8,318 | 53,058 | 0.000 | 411 | 0.000 | 831 |
| SETB | 3R | gb | 38,800 | 632,935 | -118,944 | 4,518 | 49,330 | 0.000 | 0.000 | 10.000 | 1,052 |
| SETB | 4R | none | 33,361 | 332,078 | -146,089 | 7,347 | 53,018 | 0.000 | 410 | 8.000 | 408 |
| SETB | 4R | cap | 33,361 | 332,078 | -146,089 | 7,347 | 53,018 | 0.000 | 410 | 8.000 | 408 |
| SETB | 4R | wk | 34,136 | 349,252 | -146,089 | 8,250 | 53,018 | 0.000 | 415 | 0.000 | 410 |
| SETB | 4R | gb | 38,517 | 704,646 | -152,352 | 4,278 | 52,897 | 0.000 | 0.000 | 11.000 | 566 |
| SETB | off | none | 35,485 | 349,152 | -185,848 | 7,798 | 53,949 | 0.000 | 409 | 9.000 | 110 |
| SETB | off | cap | 35,485 | 349,152 | -185,848 | 7,798 | 53,949 | 0.000 | 409 | 9.000 | 110 |
| SETB | off | wk | 36,269 | 360,888 | -175,360 | 9,356 | 53,949 | 0.000 | 416 | 0.000 | 110 |
| SETB | off | gb | 40,107 | 653,410 | -175,360 | 4,719 | 54,943 | 0.000 | 0.000 | 12.000 | 201 |
Reading: in the live layer the day-loss limit and the combined cap overlap (removing the cap changes WF by +4.5k..+5.5k at every l, the same sign regardless of l); the week floor is displaced by a looser day limit (week-floor fires 26 -> 43 as l goes 2R -> off) and the give-back is the binding protector at every l (removing it doubles maxDD to 650-870k). In Set B (no cap, floor 12R that fires 1-9 times) the day limit is the ONLY lock whose relaxation moves worst day (-97k -> -186k) and the extra mean (+2.4k/wk) is paid for with that tail.


## T10 engine cross-check, LIVE layer (hard engine firmlib.Ctx.run, ds2lib-identical) vs riskeng_pb (stateful)
| cell | hard_WF_mean | hard_WF_dd | hard_IS_mean | hard_L8W_mean | hard_WF_worst_day |
|---|---|---|---|---|---|
| A|LIVE|2R | 24,975 | 401,293 | 13,671 | 34,191 | -100,752 |
| B|LIVE|2R|nopft | 25,240 | 401,293 | 13,671 | 32,820 | -100,752 |
| A|LIVE|3R | 22,133 | 431,064 | 10,299 | 38,206 | -133,786 |
| B|LIVE|3R|nopft | 22,703 | 431,064 | 10,299 | 39,439 | -133,786 |
| A|LIVE|4R | 24,778 | 440,530 | 2,974 | 38,898 | -167,152 |
| B|LIVE|4R|nopft | 25,119 | 423,797 | 2,974 | 40,131 | -167,152 |
| A|LIVE|off | 23,626 | 505,733 | 3,082 | 37,176 | -220,626 |
| B|LIVE|off|nopft | 23,968 | 505,733 | 3,082 | 38,409 | -220,626 |
Agreement within 0.5% on WF mean and within 0.3% on maxDD (e.g. -2R 401,293 vs 401,641; -4R 440,530 vs 439,475); flag threshold not hit.

## Method notes
- Engine: firm/riskeng_pb.py (copy of riskeng.py + per-entry status/halt-second output, R-scaled flag, two placebo modes); with flags off it reproduces riskeng bit-for-bit (max |dx| = 0). Runner firm/pbd_run.py, statistics firm/pbd_stats.py, outputs firm/out/pbday/*.csv. Pair TH-off, 60 pt, corrected P9 points, $4.84 RT, windows 18:00-18:05 and 15:00-16:54 ET.
- Attempts/day = positions opened per active day (day with >= 1 entry); targets/stops by the trade's natural exit label (the remainder are time-block exits and lock-scaled exits); halted share = calendar days (WF, all trading days) with >= 1 entry skipped by the per-book LOSS rule; halt time = median ET time of the first skip per (book,day). Set B's higher attempts/day (9.2 vs 7.6 at 2R) is the cap removal letting both books keep trading; relaxing l adds about 1.0 attempt and 0.5 targets per active day per step.
- Income: $/calendar day WF at -2R live 5,060 -> 4,480/5,009/4,781 (3R/4R/off); Set B 6,707 -> 6,896/6,758/7,188.
- Placebo caveat: the hazard null skips entries at random with the real per-session skip rate, so it has no clustering after losses; the shuffled-date null keeps the clustering (once halted, stays halted that day) and is the fairer comparison. Both agree that the mean is not distinguishable from chance.
- The holdout window overlaps L8W (days >= 20260822). Folds use fit 12 / read 3 / step 3 months.
- Nothing live, UNTOUCHED unread, no data purchased, no gate changed.
