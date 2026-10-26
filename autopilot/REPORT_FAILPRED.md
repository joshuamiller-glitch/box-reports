# FAILPRED - REPORT (Part 3): where DualStrat2 fails and how well it can be predicted
Research only. No spec, no book, no recommendation. Benchmark = live Set A on the corrected P9 replay (WF 2024-02..2026-10: $25.0k/wk, SD $104.5k, maxDD $401k; reproduced exactly). All $ are per week at 14/14 report scale, fees $4.84 RT. PREREG sha256 7fbd895c..., ADDENDUM1 (arm iii flatten) a7ecd886..., ADDENDUM2 (wider search) 120d5181... frozen before any scored cell. UNTOUCHED split never read.

## 0. Verdict (exact form, details below)
Full feature set vs step-0-type features: AUC gain >= 0.03 at 9 of 10 horizons (pooled F-A: pre-open +0.056, +30 +0.039, +60 +0.047, +120 +0.084); L2 data add nothing (cheap model equal or better at every horizon).
Pre-open: AUC 0.63 [0.60,0.66] (pooled, F-A; Asia 0.58, London 0.58, NY 0.63). By +60 min: AUC 0.74 [0.72,0.76] (Asia 0.55, London 0.65, NY 0.91), but most of that is the pair's own booked P&L (residual-failure AUC stays 0.60-0.66). As a halt switch the best cell (frozen pre-holdout rule: CHOSEN, flatten arm) is horizon pre-open / threshold 0.8: +4,793 $/wk, maxDD -38,826 $, CI [+2,081, +8,132], placebo rank 1.00, holdout sign: mean up, maxDD unchanged (+1,324 $/wk, 11 sessions halted: 10 in the WF-PRE selection window, 1 in the holdout). It captures 5.1% of the perfect-foresight ceiling. Verdict on the pass rule: FAIL (fails holdout).
AUC first reaches 0.70 at never for ASIA, +120 for LONDON, +15 for NY; 0.75 at never for ASIA, never for LONDON, +20 for NY (best pre-holdout-selected cell per type; whole-session label).
The only cell that clears all five conditions is (STACK-FB/soft/+5/theta 0.3: +8,613 $/wk, maxDD -19,824); it is isolated across horizons and its maxDD gain is placebo-indistinguishable, so it is reported, not endorsed.

## 1. Part 1 - failure profile (full detail: autopilot/REPORT_FAILPRED_PROFILE.md)
| definition | group | sessions | failing | mean P&L failing | mean P&L rest | share of weekly variance | losing weeks explained alone |
|---|---|---|---|---|---|---|---|
| F-A  P&L<0 | ASIA | 954 | 44.5% [41%,48%] | -25,972 | 25,995 | 22% | 39 of 80 |
| F-A  P&L<0 | LONDON | 954 | 39.0% [36%,42%] | -18,930 | 13,629 | 7% | 29 of 80 |
| F-A  P&L<0 | NY | 951 | 28.8% [26%,32%] | -21,136 | 9,521 | 6% | 26 of 80 |
| F-A  P&L<0 | POOLED | 2859 | 37.5% [36%,39%] | -22,289 | 15,732 | 35% | 80 of 80 |
| F-B  bottom quartile | ASIA | 954 | 25.1% [22%,28%] | -40,251 | 17,249 | 22% | 36 of 80 |
| F-B  bottom quartile | LONDON | 954 | 25.2% [23%,28%] | -26,683 | 10,215 | 7% | 29 of 80 |
| F-B  bottom quartile | NY | 951 | 25.0% [22%,28%] | -24,102 | 8,963 | 6% | 26 of 80 |
| F-B  bottom quartile | POOLED | 2859 | 25.1% [24%,27%] | -30,349 | 12,146 | 35% | 73 of 80 |
| F-C  loss>=1R ($16.8k) | ASIA | 954 | 30.1% [27%,33%] | -36,422 | 19,739 | 22% | 37 of 80 |
| F-C  loss>=1R ($16.8k) | LONDON | 954 | 18.4% [16%,21%] | -30,614 | 8,069 | 8% | 26 of 80 |
| F-C  loss>=1R ($16.8k) | NY | 951 | 15.6% [13%,18%] | -31,950 | 6,704 | 6% | 22 of 80 |
| F-C  loss>=1R ($16.8k) | POOLED | 2859 | 21.4% [20%,23%] | -33,666 | 11,044 | 36% | 71 of 80 |
A failing session is a stop-out session of normal volatility (2.1 stops vs 0.7 per session; stop rate 71% vs 22%); losses land late in Asia/London (59%/55% in the last hour) and early in NY (32% in the first hour). Persistence is weak (London after a failing Asia 46% vs 34%). Calendar and overnight context: 7 of 714 cells flag against about 18 expected by chance.

## 2. Part 2 - prediction
Search size: 870 candidate features per decision (incl. 20 noise), 10 horizons, 4 targets (F-A, F-B, F-C, RR), 12 binary models + 5 regression models, pooled and per-type fits, 33 monthly walk-forward refits with 1-week embargo, nested screening/hyperparameters/isotonic calibration/stack inside every training window; CPCV (6 groups, test 2, 7-day purge+embargo) as a second estimate; truncation-invariance: 360 decisions, 74,810 feature checks, 0 mismatches. Statistical cells scored: 1,450 (model x target x scope x horizon) series x 4 session subsets. Flags: U = UNSTABLE (|WF AUC - CPCV AUC| > 0.05), N = a noise feature sat in the model's top-20 importances in >10% of folds.

### 2.1 AUC [95% week-bootstrap CI] by horizon x session type - target F-A (P&L < 0); best model per cell chosen on WF-PRE (2024-02..2025-06) AUC only
| horizon | ASIA | LONDON | NY | POOLED | cheap model (no L2) POOLED | step-0-type features (logit) POOLED |
|---|---|---|---|---|---|---|
| pre-open | 0.579 [0.540,0.616] et | 0.584 [0.542,0.627] logit1 | 0.632 [0.588,0.673] et/U | 0.629 [0.603,0.655] rf | 0.653 [0.626,0.682] rf | 0.573 |
| +5 | 0.571 [0.530,0.611] logit1 | 0.593 [0.555,0.635] mlp | 0.664 [0.617,0.703] stack | 0.640 [0.613,0.666] rf | 0.648 [0.619,0.678] gbt3 | 0.599 |
| +10 | 0.581 [0.541,0.627] rf | 0.584 [0.543,0.623] logit1 | 0.694 [0.651,0.734] et | 0.643 [0.617,0.668] rf | 0.650 [0.624,0.675] stack | 0.612 |
| +15 | 0.563 [0.521,0.603] stack | 0.588 [0.548,0.628] logit2 | 0.725 [0.682,0.765] et | 0.643 [0.617,0.668] stack | 0.640 [0.611,0.667] stack | 0.614 |
| +20 | 0.576 [0.537,0.619] stack | 0.617 [0.577,0.659] rf/N | 0.759 [0.719,0.796] et | 0.654 [0.627,0.682] rf/N | 0.664 [0.639,0.690] rf/N | 0.620 |
| +30 | 0.578 [0.539,0.618] et | 0.643 [0.599,0.685] rf/N | 0.799 [0.761,0.830] rf/N | 0.685 [0.659,0.711] rf/N | 0.691 [0.665,0.717] rf/N | 0.646 |
| +45 | 0.572 [0.529,0.610] reg_etr | 0.538 [0.500,0.572] nb | 0.875 [0.845,0.900] et | 0.719 [0.698,0.741] et | 0.716 [0.695,0.737] et | 0.672 |
| +60 | 0.548 [0.506,0.590] logit2 | 0.653 [0.610,0.692] stack | 0.912 [0.885,0.935] et | 0.737 [0.717,0.756] et | 0.739 [0.718,0.758] et | 0.690 |
| +90 | 0.567 [0.526,0.603] mlp | 0.698 [0.657,0.736] et | 0.936 [0.914,0.956] et | 0.773 [0.751,0.793] et | 0.783 [0.764,0.801] rf | 0.707 |
| +120 | 0.646 [0.604,0.689] gbt3 | 0.719 [0.679,0.758] et | 0.947 [0.926,0.965] et | 0.802 [0.781,0.822] rf | 0.801 [0.781,0.822] et | 0.719 |

### 2.1 AUC [95% week-bootstrap CI] by horizon x session type - target F-B (bottom quartile); best model per cell chosen on WF-PRE (2024-02..2025-06) AUC only
| horizon | ASIA | LONDON | NY | POOLED | cheap model (no L2) POOLED | step-0-type features (logit) POOLED |
|---|---|---|---|---|---|---|
| pre-open | 0.539 [0.492,0.584] reg_rfr | 0.667 [0.621,0.709] rf/N | 0.680 [0.628,0.728] knn | 0.615 [0.583,0.648] knn | 0.632 [0.597,0.663] rf/N | 0.516 |
| +5 | 0.551 [0.503,0.598] knn/U | 0.632 [0.577,0.682] logit2/N | 0.684 [0.636,0.728] gbt2/UN | 0.630 [0.595,0.660] knn | 0.644 [0.614,0.673] stack | 0.565 |
| +10 | 0.556 [0.506,0.605] knn/U | 0.681 [0.633,0.729] et/N | 0.690 [0.638,0.735] gbt4/UN | 0.628 [0.598,0.660] gbt3/N | 0.649 [0.613,0.683] et/N | 0.573 |
| +15 | 0.519 [0.472,0.562] stack | 0.683 [0.637,0.728] rf/N | 0.688 [0.637,0.731] gbt4/UN | 0.630 [0.599,0.660] gbt4/N | 0.638 [0.606,0.667] gbt3/N | 0.571 |
| +20 | 0.523 [0.472,0.569] stack | 0.647 [0.599,0.691] knn/U | 0.723 [0.681,0.764] rf/N | 0.634 [0.604,0.663] rf/N | 0.649 [0.616,0.680] et/N | 0.581 |
| +30 | 0.546 [0.503,0.587] reg_ridge | 0.630 [0.577,0.677] gbt4/N | 0.763 [0.722,0.802] et | 0.635 [0.608,0.662] logit1 | 0.656 [0.624,0.686] et | 0.609 |
| +45 | 0.547 [0.492,0.597] reg_ridge | 0.645 [0.598,0.689] et | 0.863 [0.831,0.892] et | 0.702 [0.674,0.731] et | 0.699 [0.668,0.729] et | 0.646 |
| +60 | 0.563 [0.516,0.607] reg_etr | 0.624 [0.571,0.674] logit1 | 0.905 [0.879,0.929] et | 0.706 [0.680,0.731] et | 0.724 [0.699,0.750] et | 0.666 |
| +90 | 0.569 [0.522,0.615] reg_ridge | 0.678 [0.627,0.728] mlp | 0.929 [0.902,0.949] gbt2 | 0.745 [0.718,0.769] et | 0.756 [0.733,0.779] et | 0.689 |
| +120 | 0.625 [0.578,0.676] single | 0.706 [0.658,0.748] knn | 0.935 [0.912,0.957] rf | 0.777 [0.753,0.799] et | 0.778 [0.754,0.799] et | 0.707 |

### 2.1 AUC [95% week-bootstrap CI] by horizon x session type - target F-C (loss >= 1R); best model per cell chosen on WF-PRE (2024-02..2025-06) AUC only
| horizon | ASIA | LONDON | NY | POOLED | cheap model (no L2) POOLED | step-0-type features (logit) POOLED |
|---|---|---|---|---|---|---|
| pre-open | 0.538 [0.500,0.578] gbt2 | 0.679 [0.620,0.732] et | 0.551 [0.483,0.617] mlp | 0.645 [0.615,0.674] stack | 0.636 [0.612,0.661] et | 0.608 |
| +5 | 0.523 [0.479,0.570] logit2 | 0.614 [0.553,0.675] single | 0.538 [0.472,0.607] reg_ridge | 0.617 [0.587,0.647] single | 0.627 [0.601,0.654] stack | 0.623 |
| +10 | 0.566 [0.517,0.615] single | 0.651 [0.604,0.700] knn | 0.533 [0.469,0.593] reg_lgbr | 0.652 [0.623,0.680] single | 0.625 [0.596,0.651] stack | 0.633 |
| +15 | 0.542 [0.494,0.591] single | 0.614 [0.553,0.675] single | 0.641 [0.580,0.701] nb | 0.648 [0.617,0.677] single | 0.629 [0.602,0.655] stack | 0.631 |
| +20 | 0.526 [0.477,0.569] reg_etr | 0.614 [0.553,0.675] single | 0.718 [0.660,0.771] et | 0.662 [0.633,0.686] et | 0.642 [0.613,0.668] rf | 0.639 |
| +30 | 0.543 [0.493,0.589] nb | 0.614 [0.553,0.675] single | 0.745 [0.697,0.796] single | 0.663 [0.634,0.690] single | 0.670 [0.643,0.694] rf | 0.660 |
| +45 | 0.545 [0.495,0.592] reg_ridge | 0.614 [0.553,0.675] single | 0.801 [0.750,0.846] knn | 0.683 [0.656,0.705] knn | 0.677 [0.651,0.701] et | 0.688 |
| +60 | 0.570 [0.526,0.615] reg_etr | 0.614 [0.553,0.675] single | 0.890 [0.859,0.920] et | 0.720 [0.695,0.743] et | 0.716 [0.694,0.738] et | 0.711 |
| +90 | 0.573 [0.529,0.616] reg_ridge | 0.689 [0.637,0.735] rf | 0.917 [0.888,0.946] et | 0.745 [0.721,0.767] et | 0.763 [0.740,0.784] et | 0.727 |
| +120 | 0.605 [0.554,0.648] knn | 0.715 [0.670,0.761] et | 0.917 [0.889,0.946] logit1 | 0.780 [0.758,0.801] et | 0.781 [0.757,0.801] et | 0.738 |

Full feature set vs step-0-type features (F-A, pooled): gain in AUC by horizon = pre-open +0.056, +5 +0.041, +10 +0.031, +15 +0.029, +20 +0.034, +30 +0.039, +45 +0.047, +60 +0.047, +90 +0.066, +120 +0.084. Gain >= 0.03 at 9 of 10 horizons. Cheap model (no L2 data) vs full: pooled F-A AUC difference (cheap - full) = pre-open +0.024, +5 +0.008, +10 +0.011, +15 +0.002, +20 +0.010, +30 +0.006, +45 -0.003, +60 +0.002, +90 +0.011, +120 -0.001 (best-of-model in each set; L2 data do not add measurable information).

### 2.2 Most learnable target per session type (mean WF-PRE AUC of the best model over the 10 horizons; selection pre-holdout)
| session | F-A | F-B | F-C | most learnable | note |
|---|---|---|---|---|---|
| ASIA | 0.579 | 0.558 | 0.553 | FA | AUC is base-rate free but labels differ; the switch grid runs all three (STACK-FA/FB/FC) plus CHOSEN (per type and horizon, best pre-holdout cell of any target) |
| LONDON | 0.613 | 0.646 | 0.677 | FC | AUC is base-rate free but labels differ; the switch grid runs all three (STACK-FA/FB/FC) plus CHOSEN (per type and horizon, best pre-holdout cell of any target) |
| NY | 0.765 | 0.737 | 0.715 | FA | AUC is base-rate free but labels differ; the switch grid runs all three (STACK-FA/FB/FC) plus CHOSEN (per type and horizon, best pre-holdout cell of any target) |
| ALL | 0.669 | 0.640 | 0.679 | FC | AUC is base-rate free but labels differ; the switch grid runs all three (STACK-FA/FB/FC) plus CHOSEN (per type and horizon, best pre-holdout cell of any target) |

### 2.3 Horizon at which AUC first reaches 0.70 / 0.75 (best pre-holdout-selected cell over targets F-A/F-B/F-C, per session type; WF AUC and, in brackets, the same cell on the HOLDOUT 2025-07+)
| session | AUC at pre-open | first horizon >= 0.70 | first >= 0.75 | AUC series by horizon (WF) |
|---|---|---|---|---|
| ASIA | 0.579 | never () | never () | pre-open 0.58, +5 0.57, +10 0.58, +15 0.56, +20 0.58, +30 0.58, +45 0.57, +60 0.57, +90 0.57, +120 0.65 |
| LONDON | 0.679 | +120 (0.723 hold) | never () | pre-open 0.68, +5 0.61, +10 0.65, +15 0.68, +20 0.61, +30 0.61, +45 0.61, +60 0.61, +90 0.69, +120 0.71 |
| NY | 0.632 | +15 (0.766 hold) | +20 (0.803 hold) | pre-open 0.63, +5 0.68, +10 0.69, +15 0.73, +20 0.76, +30 0.80, +45 0.87, +60 0.91, +90 0.94, +120 0.95 |
| ALL | 0.645 | +45 (0.751 hold) | +90 (0.797 hold) | pre-open 0.65, +5 0.62, +10 0.65, +15 0.65, +20 0.66, +30 0.66, +45 0.72, +60 0.72, +90 0.77, +120 0.80 |
Important reading: the whole-session label contains the P&L already booked. From +45 onward the strongest predictors are the pair's own state (trades so far, P&L so far, first-trade outcome): the model largely recognises a session that has already failed. The residual label (P&L of entries after the decision time, F-R) is the part a halt can act on; its AUC stays 0.60-0.66 at every horizon (table 2.5).

### 2.4 Residual failure (F-R: P&L of trades entered after the decision time < 0), lite model set, pooled WF AUC
| horizon | logit-L2 | GBT3 | RF | stack |
|---|---|---|---|---|
| pre-open | 0.600 [0.578,0.621] | 0.623 [0.598,0.648] | 0.629 [0.603,0.655] | 0.626 [0.599,0.651] |
| +5 | 0.583 [0.559,0.606] | 0.610 [0.582,0.634] | 0.613 [0.587,0.637] | 0.606 [0.580,0.632] |
| +10 | 0.600 [0.577,0.621] | 0.645 [0.617,0.672] | 0.649 [0.622,0.676] | 0.650 [0.622,0.675] |
| +15 | 0.610 [0.586,0.635] | 0.659 [0.632,0.688] | 0.659 [0.631,0.688] | 0.665 [0.636,0.693] |
| +20 | 0.601 [0.577,0.625] | 0.628 [0.603,0.652] | 0.631 [0.609,0.655] | 0.628 [0.603,0.652] |
| +30 | 0.601 [0.575,0.627] | 0.651 [0.625,0.674] | 0.645 [0.621,0.670] | 0.644 [0.618,0.670] |
| +45 | 0.615 [0.589,0.640] | 0.633 [0.606,0.656] | 0.636 [0.614,0.659] | 0.624 [0.598,0.650] |
| +60 | 0.601 [0.574,0.626] | 0.651 [0.623,0.677] | 0.654 [0.629,0.679] | 0.652 [0.624,0.678] |
| +90 | 0.605 [0.577,0.629] | 0.664 [0.640,0.687] | 0.649 [0.624,0.672] | 0.652 [0.626,0.676] |
| +120 | 0.621 [0.594,0.649] | 0.651 [0.624,0.677] | 0.652 [0.626,0.676] | 0.638 [0.612,0.662] |

### 2.5 Stability, calibration, permutation (pooled STACK, target F-A)
| horizon | AUC 2024 / 2025 / 2026 | AUC VIX low / mid / high | Brier skill | ECE | permutation rank (500 week shuffles) | top-decile lift (precision) |
|---|---|---|---|---|---|---|
| pre-open | 0.590 / 0.588 / 0.685 | 0.594 / 0.620 / 0.640 | +0.046 | 0.027 | 1.000 | 1.23 (0.43) |
| +5 | 0.595 / 0.580 / 0.702 | 0.568 / 0.628 / 0.644 | +0.050 | 0.033 | 1.000 | 1.27 (0.45) |
| +10 | 0.607 / 0.593 / 0.693 | 0.593 / 0.632 / 0.647 | +0.055 | 0.031 | 1.000 | 1.32 (0.47) |
| +15 | 0.599 / 0.624 / 0.710 | 0.594 / 0.654 / 0.659 | +0.064 | 0.038 | 1.000 | 1.24 (0.44) |
| +20 | 0.616 / 0.635 / 0.738 | 0.608 / 0.671 / 0.678 | +0.081 | 0.035 | 1.000 | 1.40 (0.50) |
| +30 | 0.614 / 0.657 / 0.749 | 0.574 / 0.682 / 0.725 | +0.090 | 0.048 | 1.000 | 1.35 (0.48) |
| +45 | 0.639 / 0.715 / 0.768 | 0.627 / 0.707 / 0.766 | +0.137 | 0.034 | 1.000 | 1.78 (0.63) |
| +60 | 0.689 / 0.735 / 0.782 | 0.688 / 0.733 / 0.770 | +0.171 | 0.036 | 1.000 | 2.01 (0.71) |
| +90 | 0.708 / 0.773 / 0.821 | 0.700 / 0.765 / 0.822 | +0.208 | 0.043 | 1.000 | 2.14 (0.76) |
| +120 | 0.746 / 0.802 / 0.848 | 0.755 / 0.788 / 0.843 | +0.249 | 0.029 | 1.000 | 2.20 (0.78) |

### 2.6 Reliability (10 equal-count bins; calibrated P vs realised fail rate), pooled STACK F-A
| bin | pre-open P / realised | +30 P / realised | +60 P / realised |
|---|---|---|---|
| 1 | 0.16 / 0.13 | 0.08 / 0.03 | 0.02 / 0.02 |
| 2 | 0.26 / 0.20 | 0.18 / 0.11 | 0.10 / 0.10 |
| 3 | 0.31 / 0.31 | 0.26 / 0.31 | 0.19 / 0.18 |
| 4 | 0.35 / 0.32 | 0.31 / 0.37 | 0.27 / 0.34 |
| 5 | 0.38 / 0.38 | 0.35 / 0.40 | 0.32 / 0.40 |
| 6 | 0.40 / 0.43 | 0.38 / 0.43 | 0.36 / 0.45 |
| 7 | 0.43 / 0.42 | 0.41 / 0.44 | 0.40 / 0.35 |
| 8 | 0.45 / 0.44 | 0.44 / 0.48 | 0.44 / 0.48 |
| 9 | 0.48 / 0.46 | 0.49 / 0.49 | 0.49 / 0.51 |
| 10 | 0.52 / 0.43 | 0.57 / 0.48 | 0.72 / 0.71 |

### 2.7 What a threshold buys (pooled STACK F-A; calibrated P >= threshold; WF sessions). One-line answers.
| horizon | threshold | flagged share | catch (recall of failing) | wrongly flag (of good) | precision | one-line answer |
|---|---|---|---|---|---|---|
| pre-open | 0.5 | 7.1% | 8.6% | 6.3% | 42.7% | at pre-open, threshold 0.5: we catch 9% of failing sessions and wrongly flag 6% of good ones |
| pre-open | 0.6 | 0.0% | 0.0% | 0.1% | 0.0% | at pre-open, threshold 0.6: we catch 0% of failing sessions and wrongly flag 0% of good ones |
| pre-open | 0.7 | 0.0% | 0.0% | 0.0% | nan% | at pre-open, threshold 0.7: we catch 0% of failing sessions and wrongly flag 0% of good ones |
| pre-open | 0.8 | 0.0% | 0.0% | 0.0% | nan% | at pre-open, threshold 0.8: we catch 0% of failing sessions and wrongly flag 0% of good ones |
| +30 | 0.5 | 13.3% | 17.8% | 10.9% | 47.1% | at +30, threshold 0.5: we catch 18% of failing sessions and wrongly flag 11% of good ones |
| +30 | 0.6 | 2.1% | 2.8% | 1.8% | 46.7% | at +30, threshold 0.6: we catch 3% of failing sessions and wrongly flag 2% of good ones |
| +30 | 0.7 | 0.1% | 0.3% | 0.1% | 66.7% | at +30, threshold 0.7: we catch 0% of failing sessions and wrongly flag 0% of good ones |
| +30 | 0.8 | 0.0% | 0.0% | 0.1% | 0.0% | at +30, threshold 0.8: we catch 0% of failing sessions and wrongly flag 0% of good ones |
| +60 | 0.5 | 13.8% | 25.5% | 7.4% | 65.2% | at +60, threshold 0.5: we catch 25% of failing sessions and wrongly flag 7% of good ones |
| +60 | 0.6 | 6.5% | 14.6% | 2.1% | 78.8% | at +60, threshold 0.6: we catch 15% of failing sessions and wrongly flag 2% of good ones |
| +60 | 0.7 | 4.5% | 11.1% | 1.0% | 86.3% | at +60, threshold 0.7: we catch 11% of failing sessions and wrongly flag 1% of good ones |
| +60 | 0.8 | 3.1% | 8.4% | 0.2% | 95.4% | at +60, threshold 0.8: we catch 8% of failing sessions and wrongly flag 0% of good ones |

### 2.8 Decision curve (net benefit = TP/n - FP/n x t/(1-t); pooled STACK F-A, WF sessions)
| horizon | t | model | treat-all | treat-none |
|---|---|---|---|---|
| pre-open | 0.2 | +0.1986 | +0.1915 | 0 |
| pre-open | 0.3 | +0.1132 | +0.0760 | 0 |
| pre-open | 0.4 | +0.0311 | -0.0781 | 0 |
| pre-open | 0.5 | -0.0105 | -0.2937 | 0 |
| pre-open | 0.6 | -0.0007 | -0.6171 | 0 |
| pre-open | 0.7 | +0.0000 | -1.1561 | 0 |
| +30 | 0.2 | +0.2226 | +0.1915 | 0 |
| +30 | 0.3 | +0.1399 | +0.0760 | 0 |
| +30 | 0.4 | +0.0433 | -0.0781 | 0 |
| +30 | 0.5 | -0.0076 | -0.2937 | 0 |
| +30 | 0.6 | -0.0071 | -0.6171 | 0 |
| +30 | 0.7 | -0.0002 | -1.1561 | 0 |
| +60 | 0.2 | +0.2267 | +0.1915 | 0 |
| +60 | 0.3 | +0.1557 | +0.0760 | 0 |
| +60 | 0.4 | +0.0846 | -0.0781 | 0 |
| +60 | 0.5 | +0.0419 | -0.2937 | 0 |
| +60 | 0.6 | +0.0307 | -0.6171 | 0 |
| +60 | 0.7 | +0.0246 | -1.1561 | 0 |

### 2.9 Feature importance top 10 (pooled logit-L2 F-A, 33 refits): folds in top-20, sign stability (share of folds with positive coefficient); noise features flagged

pre-open: fc_p_rest_lgb (25.0/33 folds, sign + in 100%); pct60_depth_ratio (22.0/33 folds, sign + in 0%); pct60_btc_ovn (21.0/33 folds, sign + in 0%); pct60_spr15_rel (21.0/33 folds, sign + in 0%); pct60_refill_rate30 (20.0/33 folds, sign + in 0%); fc_p_sess_ridge (20.0/33 folds, sign + in 0%); day_peak (19.0/33 folds, sign + in 0%); pct60_gk60 (19.0/33 folds, sign + in 100%); pct60_park60 (17.0/33 folds, sign + in 100%); pct60_zn_ovn (16.0/33 folds, sign + in 0%)
  noise features in top-20: 0 of 33 folds

+30: ntr_sess (31.0/33 folds, sign + in 100%); vwapband60 (29.0/33 folds, sign + in 0%); fc_p_rest_lgb (27.0/33 folds, sign + in 100%); btc_rv60 (20.0/33 folds, sign + in 0%); depl_rate15 (19.0/33 folds, sign + in 100%); tin45 (19.0/33 folds, sign + in 100%); or_width_atr (19.0/33 folds, sign + in 100%); dist_wkfloor (19.0/33 folds, sign + in 0%); pnl_week (19.0/33 folds, sign + in 100%); agg_absmean (18.0/33 folds, sign + in 100%)
  noise features in top-20: 2 of 33 folds

+60: ntr_sess (33.0/33 folds, sign + in 100%); pnl_sess_closed (33.0/33 folds, sign + in 0%); ntr_sess*vpin60 (31.0/33 folds, sign + in 0%); vpin60 (31.0/33 folds, sign + in 100%); first_pnl (30.0/33 folds, sign + in 0%); ntr_ST (29.0/33 folds, sign + in 100%); fc_p_sess_ridge (25.0/33 folds, sign + in 0%); ntr_sess*fc_p_sess_ridge (22.0/33 folds, sign + in 100%); fc_p_rest_lgb (20.0/33 folds, sign + in 100%); tin60 (20.0/33 folds, sign + in 100%)
  noise features in top-20: 0 of 33 folds

Noise audit: of 120 (horizon x target x model) importance series, 25 have a noise feature in the top-20 in >10% of folds; mean share of folds with a noise feature in top-20 = 5.0%.

## 3. Economic score - the only test that matters
Switch = at decision time t, if calibrated P(fail) >= theta: no new entries for the session (hard), per-book (halt only the book whose own model says fail), soft (lots x0.5, no size-cost refund), flatten (close open trades at market with the S113 3.98-tick exit cost, then halt). Signal stream regenerated for every cell (identity check exact: no-halt reproduces the benchmark to the cent). 1080 cells scored (10 horizons x 6 thresholds x variants) plus 180 perfect-foresight ceilings; placebo (500 random switches, same halted count per session type, regenerated) run for every cell passing conditions 1-3 (9) and for the best cell. DSR trials N = 6,660 (F_P 3,620 + this track's 1260 economic + 1450 statistical + 330 CPCV series); benchmark DSR = 0.68.

### 3.1 Pass counts (pass = WF mean up AND maxDD down AND weekly-diff CI excludes 0 AND placebo rank >= 0.95 on delta mean AND holdout mean up and maxDD down)
| arm | variant | cells | mean up | maxDD down | mean up & maxDD down | + CI excludes 0 | PASS |
|---|---|---|---|---|---|---|---|
| flatten | CHOSEN | 60 | 21 | 11 | 8 | 4 | 0 |
| flatten | LITE-FR | 60 | 6 | 0 | 0 | 0 | 0 |
| flatten | STACK-FA | 60 | 16 | 3 | 2 | 0 | 0 |
| flatten | STACK-FB | 60 | 13 | 12 | 6 | 0 | 0 |
| flatten | STACK-FC | 60 | 10 | 6 | 3 | 0 | 0 |
| hard | CHOSEN | 60 | 20 | 14 | 9 | 2 | 0 |
| hard | LITE-FR | 60 | 7 | 2 | 1 | 0 | 0 |
| hard | STACK-FA | 60 | 17 | 9 | 6 | 0 | 0 |
| hard | STACK-FB | 60 | 14 | 12 | 5 | 0 | 0 |
| hard | STACK-FC | 60 | 13 | 12 | 5 | 0 | 0 |
| perbook | BOOK-FA | 60 | 13 | 3 | 2 | 0 | 0 |
| perbook | BOOK-FB | 60 | 14 | 11 | 5 | 0 | 0 |
| perbook | BOOK-FC | 60 | 8 | 1 | 0 | 0 | 0 |
| soft | CHOSEN | 60 | 21 | 19 | 13 | 2 | 0 |
| soft | LITE-FR | 60 | 13 | 4 | 2 | 0 | 0 |
| soft | STACK-FA | 60 | 17 | 16 | 6 | 0 | 0 |
| soft | STACK-FB | 60 | 24 | 13 | 5 | 1 | 1 |
| soft | STACK-FC | 60 | 15 | 14 | 6 | 0 | 0 |
Totals: 1080 cells; mean up 262; maxDD down 162; both 84; CI excludes 0 as well 9; PASS 1. Expected by chance if predictions were noise: about 1 in 40 cells show a 95% CI that excludes zero in the right direction on the mean alone.

### 3.2 Grid: variant STACK-FA, arm hard - cell = delta weekly mean / delta maxDD / sessions halted (P = passes all five). Full 1,080-cell table with CI, placebo rank, holdout, ceiling capture: out/econ_final.csv
| horizon | theta .3 | .4 | .5 | .6 | .7 | .8 |
|---|---|---|---|---|---|---|
| pre-open | -21.9k / +598k / n1635 | -10.5k / +210k / n977 | -3.0k / +213k / n150 | +0.0k / +0k / n1 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +5 | -23.4k / +782k / n1601 | -13.8k / +279k / n916 | -0.4k / +149k / n139 | -0.1k / +0k / n2 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +10 | -25.2k / +872k / n1583 | -14.7k / +286k / n975 | +0.2k / +125k / n182 | -0.3k / +118k / n7 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +15 | -26.6k / +904k / n1622 | -10.6k / +405k / n1055 | -0.5k / +138k / n224 | +1.1k / -61k / n10 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +20 | -15.0k / +403k / n1565 | -10.5k / +389k / n1009 | +3.5k / +73k / n223 | -2.3k / +0k / n10 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +30 | -21.9k / +758k / n1424 | -0.2k / +549k / n816 | +0.5k / +30k / n280 | +0.6k / -15k / n45 | +0.3k / +0k / n3 | -0.0k / +0k / n1 |
| +45 | -15.7k / +328k / n1375 | -11.1k / +146k / n795 | +0.3k / +102k / n304 | +2.2k / +81k / n137 | -0.1k / +0k / n60 | +0.1k / +0k / n21 |
| +60 | -16.7k / +282k / n1260 | +3.8k / +6k / n716 | +4.8k / +209k / n290 | +2.1k / +121k / n137 | -0.5k / +157k / n95 | +1.0k / -3k / n65 |
| +90 | -19.3k / +167k / n1206 | -10.6k / +189k / n781 | -1.8k / -22k / n390 | +1.3k / -22k / n213 | +2.6k / -1k / n132 | +0.0k / -17k / n92 |
| +120 | -16.5k / +206k / n1117 | -13.0k / +179k / n885 | -9.3k / +174k / n556 | -6.1k / +112k / n300 | -1.2k / -35k / n202 | -0.8k / -39k / n128 |

### 3.2 Grid: variant STACK-FB, arm soft - cell = delta weekly mean / delta maxDD / sessions halted (P = passes all five). Full 1,080-cell table with CI, placebo rank, holdout, ceiling capture: out/econ_final.csv
| horizon | theta .3 | .4 | .5 | .6 | .7 | .8 |
|---|---|---|---|---|---|---|
| pre-open | -0.8k / +23k / n326 | +0.7k / -3k / n46 | +0.2k / +0k / n9 | -0.0k / +0k / n1 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +5 | +8.6k / -20k / n286 P | -0.1k / +0k / n47 | -0.1k / +0k / n6 | -0.1k / +0k / n2 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +10 | -0.6k / -38k / n318 | +0.9k / +0k / n34 | +0.2k / +0k / n7 | +0.1k / +0k / n2 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +15 | +0.6k / +96k / n277 | +0.3k / +0k / n46 | +0.1k / +0k / n7 | +0.0k / +0k / n1 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +20 | -3.4k / +21k / n309 | -0.9k / +5k / n36 | +0.0k / +0k / n1 | +0.0k / +0k / n0 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +30 | +1.0k / +28k / n293 | +0.5k / +1k / n39 | +0.1k / +0k / n8 | +0.0k / +0k / n0 | +0.0k / +0k / n0 | +0.0k / +0k / n0 |
| +45 | +2.3k / -38k / n396 | +1.6k / +0k / n103 | +1.4k / +0k / n45 | +0.9k / +0k / n28 | +0.6k / +0k / n12 | +0.7k / +0k / n4 |
| +60 | -3.3k / -38k / n413 | -1.3k / -2k / n154 | +0.6k / +0k / n97 | +1.8k / +0k / n71 | +2.3k / +0k / n51 | +1.7k / +0k / n25 |
| +90 | -6.7k / +29k / n386 | -0.5k / -21k / n186 | -0.3k / -16k / n130 | +1.6k / -8k / n91 | +0.1k / -8k / n59 | -0.2k / -8k / n27 |
| +120 | -4.3k / +38k / n437 | -1.8k / +28k / n222 | -1.7k / +3k / n147 | -1.4k / +30k / n107 | -0.5k / -8k / n77 | -2.0k / -8k / n40 |

### 3.2 Grid: variant CHOSEN, arm flatten - cell = delta weekly mean / delta maxDD / sessions halted (P = passes all five). Full 1,080-cell table with CI, placebo rank, holdout, ceiling capture: out/econ_final.csv
| horizon | theta .3 | .4 | .5 | .6 | .7 | .8 |
|---|---|---|---|---|---|---|
| pre-open | -25.8k / +629k / n1136 | -6.9k / +252k / n597 | +5.7k / -51k / n68 | +5.0k / -51k / n21 | +4.6k / -39k / n12 | +4.8k / -39k / n11 |
| +5 | -19.8k / +444k / n798 | -7.7k / +581k / n485 | -0.6k / +237k / n30 | -1.3k / +172k / n5 | +0.0k / +0k / n1 | +0.0k / +0k / n0 |
| +10 | -22.0k / +786k / n784 | -12.0k / +259k / n488 | +0.5k / +21k / n77 | +0.9k / +0k / n3 | +0.2k / +0k / n1 | +0.2k / +0k / n1 |
| +15 | -25.1k / +748k / n1008 | -16.3k / +556k / n672 | -2.0k / +193k / n145 | +1.3k / -61k / n10 | +0.2k / +0k / n1 | +0.0k / +0k / n0 |
| +20 | -21.8k / +645k / n971 | -15.6k / +290k / n657 | +1.1k / +107k / n217 | -2.3k / +0k / n20 | +0.3k / +0k / n2 | +0.3k / +0k / n1 |
| +30 | -19.7k / +504k / n1067 | -18.7k / +420k / n837 | -3.1k / +218k / n130 | -0.4k / +0k / n9 | +0.1k / +0k / n2 | +0.0k / +0k / n0 |
| +45 | -21.8k / +702k / n1000 | -7.7k / +434k / n715 | -0.5k / +183k / n414 | -2.7k / +200k / n156 | -0.4k / -51k / n48 | -0.6k / -16k / n22 |
| +60 | +8.1k / -19k / n316 | +7.3k / -76k / n210 | +2.6k / -4k / n128 | +1.2k / +5k / n83 | +0.8k / +5k / n64 | +0.5k / +12k / n57 |
| +90 | -20.3k / +654k / n1000 | -21.2k / +735k / n796 | +1.7k / +100k / n290 | -0.9k / +131k / n121 | -1.1k / +65k / n97 | -0.2k / +38k / n69 |
| +120 | -22.2k / +549k / n938 | -18.5k / +339k / n754 | -21.6k / +429k / n438 | -7.5k / +26k / n214 | -3.0k / +32k / n138 | -2.4k / -35k / n100 |

### 3.3 Every cell that clears the first three conditions (mean up, maxDD down, CI excludes 0) - placebo and holdout outcomes
| variant | arm | horizon | theta | halted | d mean $/wk | d maxDD | CI 95% | placebo rank (mean / maxDD) | holdout d mean / d maxDD | ceiling capture | DSR | result |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CHOSEN | flatten | pre-open | 0.8 | 11 | +4,793 | -38,826 | [+2,081, +8,132] | 1.00 / 0.94 | +1,324 / +0 | 5.1% | 0.85 | fails holdout (BEST CELL by pre-holdout rule) |
| CHOSEN | flatten | pre-open | 0.7 | 12 | +4,609 | -38,826 | [+1,844, +7,947] | 1.00 / 0.94 | +1,324 / +0 | 4.9% | 0.85 | fails holdout |
| CHOSEN | flatten | pre-open | 0.6 | 21 | +4,997 | -51,057 | [+1,718, +8,592] | 1.00 / 0.99 | +1,210 / +0 | 5.3% | 0.85 | fails holdout |
| CHOSEN | flatten | pre-open | 0.5 | 68 | +5,658 | -51,057 | [+381, +11,054] | 0.98 / 0.97 | -315 / +0 | 6.0% | 0.86 | fails holdout |
| CHOSEN | hard | pre-open | 0.7 | 12 | +2,241 | -26,784 | [+568, +4,483] | 0.98 / 0.85 | -2 / +0 | 2.2% | 0.76 | fails holdout |
| CHOSEN | hard | pre-open | 0.8 | 11 | +2,240 | -26,784 | [+568, +4,482] | 0.98 / 0.85 | -2 / +0 | 2.2% | 0.76 | fails holdout |
| STACK-FB | soft | +5 | 0.3 | 286 | +8,613 | -19,824 | [+2,502, +15,778] | 1.00 / 0.61 | +6,946 / -12,717 | 15.8% | 0.94 | PASS |
| CHOSEN | soft | pre-open | 0.7 | 12 | +412 | -3,924 | [+75, +850] | 0.78 / 0.73 | -1 / +0 | 0.7% | 0.70 | fails placebo,holdout |
| CHOSEN | soft | pre-open | 0.8 | 11 | +411 | -3,924 | [+74, +850] | 0.77 / 0.79 | -1 / +0 | 0.7% | 0.70 | fails placebo,holdout |

Best cell by the frozen pre-holdout rule (highest WF-PRE paired t among cells with WF-PRE mean up and maxDD down; qualifying=True): CHOSEN / flatten / pre-open / theta 0.8: WF-PRE t = 2.85.
The one cell that passes all five conditions (1 of 1080): STACK-FB / soft / +5 / theta 0.3, 286 sessions at half size. Caveats read from the grid: it is isolated (same variant/arm/theta across horizons, d mean / d maxDD: pre-open: -775/+23,061 ; +5: +8,613/-19,824 ; +10: -610/-37,733 ; +15: +637/+95,921 ; +20: -3,421/+20,511 ; +30: +969/+27,837 ; +45: +2,278/-37,983 ; +60: -3,289/-38,456 ; +90: -6,664/+28,646 ; +120: -4,349/+37,548); its maxDD gain is not distinguishable from random half-size placebos (rank 0.61 on maxDD); it is not the cell the pre-holdout rule picks; DSR 0.94 with 6,660 trials; family-wise Sidak on the placebo p-value with K_eff = 9: 0.018.

### 3.4 Perfect-foresight ceilings (halting every truly failing session at the horizon; WF d weekly mean / d maxDD)
| horizon | hard F-A | hard F-B | hard F-C | hard F-R (resid.) | soft F-A | flatten F-A |
|---|---|---|---|---|---|---|
| pre-open | +113k / -302k | +108k / -247k | +101k / -236k | +113k / -302k | +59k / -176k | +92k / -261k |
| +5 | +108k / -230k | +106k / -215k | +98k / -204k | +109k / -230k | +58k / -179k | +95k / -264k |
| +10 | +99k / -230k | +99k / -215k | +93k / -204k | +101k / -230k | +55k / -179k | +95k / -253k |
| +15 | +96k / -211k | +96k / -195k | +90k / -184k | +99k / -211k | +52k / -178k | +97k / -297k |
| +20 | +94k / -194k | +94k / -195k | +88k / -184k | +97k / -218k | +51k / -170k | +95k / -260k |
| +30 | +89k / -191k | +89k / -195k | +81k / -184k | +92k / -218k | +48k / -170k | +95k / -267k |
| +45 | +78k / -171k | +80k / -161k | +75k / -148k | +87k / -190k | +43k / -157k | +91k / -266k |
| +60 | +71k / -170k | +75k / -159k | +69k / -149k | +84k / -206k | +39k / -161k | +88k / -238k |
| +90 | +62k / -139k | +66k / -172k | +61k / -161k | +79k / -206k | +32k / -136k | +80k / -223k |
| +120 | +53k / -108k | +58k / -143k | +53k / -131k | +70k / -205k | +30k / -103k | +78k / -236k |

### 3.5 CHOSEN variant: per (horizon, session type) best cell on WF-PRE AUC (target, scope, model, label, WF-PRE AUC)
| horizon | ASIA | LONDON | NY |
|---|---|---|---|
| pre-open | FA/pooled/et/FA 0.58 | FC/pertype/et/FC 0.69 | FA/pooled/et/FA 0.65 |
| +5 | FA/pooled/logit1/FA 0.58 | FC/pertype/single/FC 0.67 | FB/pooled/gbt2/FB 0.63 |
| +10 | FA/pooled/rf/FA 0.59 | FC/pertype/knn/FC 0.68 | FB/pooled/gbt4/FB 0.63 |
| +15 | FA/pooled/stack/FA 0.57 | FB/pooled/rf/FB 0.68 | FA/pertype/et/FA 0.68 |
| +20 | FA/pooled/stack/FA 0.57 | FC/pertype/single/FC 0.67 | FA/pertype/et/FA 0.71 |
| +30 | FA/pooled/et/FA 0.56 | FC/pertype/single/FC 0.67 | FA/pooled/rf/FA 0.75 |
| +45 | RR/pooled/reg_etr/FA 0.58 | FC/pertype/single/FC 0.67 | FA/pooled/et/FA 0.85 |
| +60 | RR/pooled/reg_etr/FC 0.57 | FC/pertype/single/FC 0.67 | FA/pooled/et/FA 0.90 |
| +90 | FA/pertype/mlp/FA 0.59 | FC/pertype/rf/FC 0.68 | FA/pooled/et/FA 0.92 |
| +120 | FA/pooled/gbt3/FA 0.62 | FB/pooled/knn/FB 0.69 | FA/pooled/et/FA 0.94 |