# DS3_ABR_C1_PREHOLD - PRE-only (IN-SAMPLE-selected, walk-forward chain span 2024-02..2025-06) tables, ABRC1
Prereg l2vast/ds3/prereg/ABRC1_prereg.md sha256 2597226dc35a1213d8a9421e34afddb73e84826c8454dd1662acb3bc1101df47. Only the PRE chain span (label days 2024-02-01..2025-06-30) was read; X' and HOLD are untouched by this file. Chain deltas are WALK-FORWARD OOS within PRE (models fit on closed trades only); selection of headline cells on this span is the in-sample step of the group.
Units: delta vs 60/60 control, pts per lot (CL, constant lots) or $ per trade at constant-$-risk lots (RP); mean [week-cluster SE]; MDE80 = 2.8 SE.

Cells: 980 real, 676 placebo (PL1). White RC on PRE (best-of-N): CL N=490 max t 1.52 p=0.582 best=tab|P|ew10|1w|0|cl|m0 ; RP N=490 max t 2.14 p=0.320 best=tab|P|ew5|1w|0|rp|m1

## fix cl: 102 cells, PRE mean>0 in 47, t>2 in 0; mean over cells -0.225; best:
| key | PRE delta [SE] | MDE80 | share changed | PL1 same cfg PRE |
|--|--|--|--|--|
| fix|c40|ew10|1w|0|cl|m0 | +1.996 [1.892] | 5.30 | 0.99 | n/a |
| fix|c40|1w|1w|0|cl|m0 | +1.289 [1.527] | 4.28 | 0.93 | n/a |
| fix|c40|1m|1w|0|cl|m0 | +1.536 [1.871] | 5.24 | 0.96 | n/a |
| fix|a990|1w|1w|0|cl|m0 | +1.217 [1.529] | 4.28 | 0.97 | n/a |
| fix|c40|1m|1m|0|cl|m0 | +1.542 [1.955] | 5.47 | 1.00 | n/a |
| fix|a990|1m|1w|0|cl|m0 | +1.225 [1.716] | 4.81 | 1.00 | n/a |
| fix|a990|3m|1w|0|cl|m0 | +1.039 [1.770] | 4.96 | 1.00 | n/a |
| fix|c40|6m|1w|0|cl|m0 | +1.324 [2.279] | 6.38 | 1.00 | n/a |

## fix rp: 102 cells, PRE mean>0 in 29, t>2 in 0; mean over cells -97.017; best:
| key | PRE delta [SE] | MDE80 | share changed | PL1 same cfg PRE |
|--|--|--|--|--|
| fix|c40|ew20|1w|0|rp|m0 | +150.785 [194.489] | 544.57 | 1.00 | n/a |
| fix|a990|3m|1w|0|rp|m0 | +136.214 [193.404] | 541.53 | 1.00 | n/a |
| fix|c40|ew5|1w|0|rp|m0 | +105.345 [212.662] | 595.45 | 0.99 | n/a |
| fix|b40|3m|1w|0|rp|m0 | +67.103 [154.452] | 432.46 | 0.99 | n/a |
| fix|c40|3m|1w|0|rp|m0 | +88.503 [211.726] | 592.83 | 1.00 | n/a |
| fix|c40|ew10|1w|0|rp|m0 | +81.772 [198.036] | 554.50 | 1.00 | n/a |
| fix|b40|3m|1d|0|rp|m0 | +60.635 [162.179] | 454.10 | 0.99 | n/a |
| fix|c40|3m|1d|0|rp|m0 | +71.043 [199.387] | 558.28 | 1.00 | n/a |

## gbm cl: 68 cells, PRE mean>0 in 35, t>2 in 0; mean over cells 0.105; best:
| key | PRE delta [SE] | MDE80 | share changed | PL1 same cfg PRE |
|--|--|--|--|--|
| gbm|RA05|12m|1m|0|cl|m0 | +1.400 [1.024] | 2.87 | 0.99 | n/a |
| gbm|RA10|ew10|1m|0|cl|m0 | +1.581 [1.259] | 3.53 | 0.98 | n/a |
| gbm|EV|ew5|1m|0|cl|m1 | +1.756 [1.748] | 4.89 | 0.96 | n/a |
| gbm|EV|ew10|1m|0|cl|m1 | +1.648 [1.667] | 4.67 | 0.96 | 1.146 |
| gbm|EV|ew5|1m|0|cl|m0 | +1.722 [1.761] | 4.93 | 0.98 | n/a |
| gbm|EV|12m|1m|0|cl|m1 | +1.337 [1.374] | 3.85 | 0.91 | 0.454 |
| gbm|EV|12m|1m|0|cl|m0 | +1.299 [1.373] | 3.84 | 0.96 | 0.422 |
| gbm|EV|1m|1m|0|cl|m0 | +1.309 [1.470] | 4.11 | 0.98 | n/a |

## gbm rp: 68 cells, PRE mean>0 in 19, t>2 in 0; mean over cells -55.639; best:
| key | PRE delta [SE] | MDE80 | share changed | PL1 same cfg PRE |
|--|--|--|--|--|
| gbm|EV|12m|1m|0|rp|m1 | +174.017 [162.651] | 455.42 | 0.92 | -112.657 |
| gbm|EV|12m|1m|0|rp|m0 | +154.790 [163.905] | 458.93 | 0.97 | -142.511 |
| gbm|RA05|12m|1m|0|rp|m0 | +98.688 [144.129] | 403.56 | 0.98 | n/a |
| gbm|RA10|ew10|1m|0|rp|m0 | +93.730 [154.377] | 432.26 | 0.97 | n/a |
| gbm|RA10|12m|1m|0|rp|m0 | +65.620 [124.357] | 348.20 | 0.99 | n/a |
| gbm|EV|3m|1m|0|rp|m1 | +98.221 [198.504] | 555.81 | 0.97 | 53.837 |
| gbm|EV|3m|1m|0|rp|m0 | +97.305 [198.792] | 556.62 | 0.98 | 55.163 |
| gbm|EV|3m|1w|0|rp|m1 | +67.170 [190.096] | 532.27 | 0.96 | 36.192 |

## knn cl: 160 cells, PRE mean>0 in 75, t>2 in 0; mean over cells -0.115; best:
| key | PRE delta [SE] | MDE80 | share changed | PL1 same cfg PRE |
|--|--|--|--|--|
| knn|P|1m|1w|0|cl|m0 | +2.026 [1.613] | 4.52 | 0.98 | 0.314 |
| knn|P|1m|1w|0|cl|m1 | +1.975 [1.601] | 4.48 | 0.94 | 0.180 |
| knn|B|1m|1w|0|cl|m0 | +1.533 [1.488] | 4.17 | 0.98 | 0.116 |
| knn|B|1m|1w|0|cl|m1 | +1.475 [1.482] | 4.15 | 0.95 | 0.035 |
| knn|P|ew5|1w|0|cl|m1 | +1.263 [1.510] | 4.23 | 0.95 | 0.666 |
| knn|P|ew5|1w|0|cl|m0 | +1.259 [1.519] | 4.25 | 0.97 | 0.509 |
| knn|B|ew5|1w|0|cl|m1 | +1.054 [1.321] | 3.70 | 0.96 | 0.974 |
| knn|B|ew10|1w|0|cl|m1 | +0.980 [1.249] | 3.50 | 0.96 | 0.112 |

## knn rp: 160 cells, PRE mean>0 in 31, t>2 in 0; mean over cells -96.117; best:
| key | PRE delta [SE] | MDE80 | share changed | PL1 same cfg PRE |
|--|--|--|--|--|
| knn|B|2w|1w|0|rp|m0 | +100.834 [157.416] | 440.77 | 0.98 | 12.777 |
| knn|B|2w|1w|0|rp|m1 | +92.332 [156.843] | 439.16 | 0.95 | 18.412 |
| knn|B|1m|1m|0|rp|m0 | +80.408 [156.955] | 439.47 | 0.98 | -5.320 |
| knn|B|1m|1m|0|rp|m1 | +77.242 [153.807] | 430.66 | 0.95 | -5.892 |
| knn|P|1m|1w|0|rp|m1 | +74.703 [155.975] | 436.73 | 0.95 | -44.396 |
| knn|P|1m|1w|0|rp|m0 | +69.660 [156.264] | 437.54 | 0.98 | -58.901 |
| knn|B|YTD|1m|0|rp|m0 | +61.089 [142.385] | 398.68 | 0.92 | 19.011 |
| knn|B|ew5|1w|0|rp|m0 | +57.669 [138.554] | 387.95 | 0.98 | -36.150 |

## tab cl: 160 cells, PRE mean>0 in 71, t>2 in 0; mean over cells -0.120; best:
| key | PRE delta [SE] | MDE80 | share changed | PL1 same cfg PRE |
|--|--|--|--|--|
| tab|P|ew10|1w|0|cl|m0 | +2.479 [1.630] | 4.56 | 0.97 | -0.724 |
| tab|P|ew10|1w|0|cl|m1 | +2.223 [1.593] | 4.46 | 0.91 | -0.867 |
| tab|B|1w|1w|0|cl|m1 | +1.945 [1.504] | 4.21 | 0.93 | 0.819 |
| tab|B|1w|1w|0|cl|m0 | +1.923 [1.517] | 4.25 | 0.96 | 0.819 |
| tab|P|ew5|1w|0|cl|m1 | +1.978 [1.640] | 4.59 | 0.92 | 1.485 |
| tab|P|ew5|1w|0|cl|m0 | +1.948 [1.673] | 4.68 | 0.97 | 1.485 |
| tab|P|1w|1w|0|cl|m1 | +1.526 [1.533] | 4.29 | 0.93 | 0.399 |
| tab|P|2w|1w|0|cl|m0 | +1.728 [1.757] | 4.92 | 0.97 | 0.190 |

## tab rp: 160 cells, PRE mean>0 in 61, t>2 in 2; mean over cells -19.572; best:
| key | PRE delta [SE] | MDE80 | share changed | PL1 same cfg PRE |
|--|--|--|--|--|
| tab|P|ew5|1w|0|rp|m1 | +388.261 [181.825] | 509.11 | 0.94 | 92.636 |
| tab|P|ew10|1w|0|rp|m0 | +381.439 [189.742] | 531.28 | 0.99 | -125.523 |
| tab|P|ew5|1w|0|rp|m0 | +361.362 [183.396] | 513.51 | 0.98 | 97.127 |
| tab|P|ew10|1w|0|rp|m1 | +364.564 [189.346] | 530.17 | 0.93 | -139.618 |
| tab|P|2w|1w|0|rp|m0 | +176.299 [175.979] | 492.74 | 0.98 | -45.760 |
| tab|P|3m|1m|0|rp|m0 | +185.859 [209.556] | 586.76 | 0.98 | -203.676 |
| tab|P|3m|1m|0|rp|m1 | +183.032 [207.743] | 581.68 | 0.94 | -191.209 |
| tab|P|2w|1w|0|rp|m1 | +153.005 [174.786] | 489.40 | 0.95 | -22.017 |

Frozen abs120|OR|none (ABRA PRE-selected, so PRE is IN-SAMPLE for it): CL +2.329 [2.227] RP +212 [209] $/trade

## IN-SAMPLE (3-fold day-blocked CV inside each monthly training window, GBM EV, refits with first block date <= 2025-06-30; mean over refits)
* W12m cl: -1.22 pts per trade (refits 24). Negative: the CV-chosen brackets do worse than 60/60 inside the training window; the fixed wide-stop oracle direction is not recovered by the per-trade model at this size.
* W12m rp: -139.93 $ per trade (refits 24). Negative: the CV-chosen brackets do worse than 60/60 inside the training window; the fixed wide-stop oracle direction is not recovered by the per-trade model at this size.
* W3m cl: -1.00 pts per trade (refits 24). Negative: the CV-chosen brackets do worse than 60/60 inside the training window; the fixed wide-stop oracle direction is not recovered by the per-trade model at this size.
* W3m rp: -184.27 $ per trade (refits 24). Negative: the CV-chosen brackets do worse than 60/60 inside the training window; the fixed wide-stop oracle direction is not recovered by the per-trade model at this size.
