# DS3_THP_C2_STRUCT - structural models (optimal stopping DP, competing-risks hazard, quantile regression) under the adaptive walk-forward protocol, profit and loss sides (THPC2, 2026-10-29)
Research only. UNTOUCHED never read (tables end 2026-02-06). Fees per FEES.md cancel in paired deltas. No live change. Prereg l2vast/ds3/prereg/THPC2_prereg.md (sha in DECISIONS.md); PRE-only text autopilot/DS3_THP_C2_PREHOLD.md (sha in DECISIONS.md); tracks THPC2_DP/DPO/HAZ/QR_P/L, one HOLD look each. **HOLD-era (2025-07-01..2026-02-06) was opened once, after the PREHOLD file.** Code l2vast/ds3/code/thp_c2/; decisions parquets l2vast/ds3/out/thp/wf/c2/decisions_<model>_<side>.parquet (SCHEMA.md columns plus delta_N, delta_C, year, lots, entry_ts; they also contain the one finished supplementary chain dp|1w|vol); candidate policy wf/c2/policy_candidate.txt.

## Verdict
**PROFIT: 0 PASS / 0 CANDIDATE / 248 DEAD of 248 registered core cells. LOSS: 0 / 0 / 248 DEAD.**
Profit sentence: re-fitting on the last 6 months (quantile regression with regime dummies, re-fitted at every 18:00 open, 09:30 and 12:00 ET), the profit policy adds +0.50 pts/trade out of sample in the PRE-era (MDE 0.40) and +0.43 in the HOLD-era (MDE 0.84, CI [-0.09,+1.01] includes 0) on the MEASURED basis; without the P9 target correction (basis N) the same chain is -0.01 (PRE) and -0.54 (HOLD), so the gain is the target-correction artefact seen in THPB, not skill. Its failed gates: neighbours_agree, NOTC<=0, year_share>60%. Every DP/DPO cell (exit rate ~55%) shows about +0.4 on the M basis and -0.8 to -0.9 on the N basis, and its shuffled-label placebo gives the same +0.4-0.5, so it is not model skill. Books: positive PRE-era on ST, WT, MV, PB, HM, DN but negative on SM, and the HOLD-era signs flip on several (tables below).
Loss sentence: nothing beats the stop. Best PRE-era loss cell haz|6m|S1d|reg +0.21 pts/trade (MDE 0.46, CI [-0.12,+0.50] includes 0), HOLD -0.05; 18 of 248 cells have a positive PRE-era mean, none has CI above 0 (chance expectation 6.2), reality check p = 0.971. Re-fitting on any window from 1 week to 12 months, daily, weekly, monthly or intraday, the loss policy does not save points out of sample on any book.
Gates are those of the prereg; none was softened. Gate failure counts per side are listed in each section. SPAN2 (X' short-history span) is evaluated on the truncated-history chain and labelled.

## Scope, disclosures and deviations (read before using any number)
* Cell set. Registered 752 cells; **scored = 496 core cells (DP batch and DPO with variants none and tod; hazard and QR with none and regime-dummy variants; 248 per side)**. The supplementary regime-group DP variants (vol, sess, book) and DPO (vol, sess) were NOT run to completion: the per-refit group solves needed more than a day on 12 cores (dp|1w|vol finished and is in the parquet only). The pool was stopped with main's approval; price-path trade health was closed by the user at 21:30Z, so they are out of scope. They are not in the verdict set, reality check or multiplicity count. Regime conditioning is represented by the time-of-day state variant (DP tod) and the regime dummies (hazard, QR: vol_tag lo/hi, asia, london, pre+nyam).
* Fit-only warm-up: trades with label day 2023-04-03..2023-06-30 (never scored). Scored OOS from the 2023-07-02 18:00 ET open: X' = 2023-07-03..2024-01-31 (short history, windows truncated; used only for the SPAN2 gate), PRE-era 2024-02-01..2025-06-30 (all selection), HOLD-era 2025-07-01..2026-02-06 (one look). Every decision uses the policy fitted at the last refit time <= entry_ts on trades closed <= that time (asserted in the parquets).
* Decisions every 10 s on the 10-s grid; exit at market, 0.995 pt cost. TIGHTEN is not evaluated (chains are hold/take/cut). CR excluded (no static target/bracket). Books and lots as THPB.
* Placebo deviations (disclosed before the PREHOLD seal): shuffled labels within day: 6 draws (prereg 8), top 3 chains per model family per side (prereg 5), intraday/online chains tested at the 1d refit set of the same window/variant; the prereg's uniform-random-row random exit looks ahead (gave +5.9 pts/trade) and was replaced by a causal constant-per-row exit probability matched to the chain's exit rate (gives -0.3 to -0.8). Cells outside the placebo set are recorded 'placebo_not_run' and cannot exceed DEAD.
* Fits use at most 2,000 trades and 60,000 1-min rows per refit (hazard/QR); a fit is reused when no trade entered or left the window; EWMA DP tables are re-solved only when new trades closed.
* Multiplicity: 496 scored cells; PRE-era CI>0 cells: 14 profit (chance 6.2), 0 loss; White reality check (best of 248 per side, PRE-era days): profit p = 0.018, loss p = 0.971.
* The M-basis target correction (-1.4/-1.5/-4.2/-4.3 pts by year) is estimated on live rows and flatters every early exit; N basis, C stress basis and the placebos are therefore decisive, as in THPB.

# IN-SAMPLE (labelled; not walk-forward)
One pooled fit per model family inside PRE (2024-02..2025-06); raw = fit applied to its own trades; CV = 5-fold week-block cross-validation (each fold fitted on the other four folds). M basis, pts/trade, 10 books pooled.

| kind   | args            | side   |   raw |     cv |     n |
|:-------|:----------------|:-------|------:|-------:|------:|
| dp     | ('all', 'none') | profit | 0.386 |  0.271 | 24588 |
| dp     | ('all', 'none') | loss   | 0.000 | -0.013 | 24588 |
| dp     | ('all', 'sess') | profit | 0.501 |  0.382 | 24588 |
| dp     | ('all', 'sess') | loss   | 0.249 | -0.194 | 24588 |
| haz    | ('haz', False)  | profit | 0.364 |  0.307 | 24588 |
| haz    | ('haz', False)  | loss   | 0.000 |  0.000 | 24588 |
| haz    | ('haz', True)   | profit | 0.358 |  0.295 | 24588 |
| haz    | ('haz', True)   | loss   | 0.000 |  0.000 | 24588 |
| qr     | ('qr', False)   | profit | 0.337 |  0.241 | 24588 |
| qr     | ('qr', False)   | loss   | 0.000 |  0.000 | 24588 |
| qr     | ('qr', True)    | profit | 0.412 |  0.461 | 24588 |
| qr     | ('qr', True)    | loss   | 0.000 |  0.000 | 24588 |

Profit in-sample CV +0.24 to +0.46 on the M basis (DP-sess and QR-regime highest); loss 0.0 for hazard and QR (no threshold with positive training gain, so hold-all), DP loss CV -0.01 (none) and -0.19 (sess).


# PROFIT SIDE (hold / take vs hold-to-bracket)

**Verdicts, 248 registered core cells: {'DEAD': 248}.** PRE-era delta>0 154; PRE CI>0 14 (chance ~6.2); HOLD delta>0 159; both >0 120; HOLD CI lower>0 87; reality check on PRE-era (best of 248) p = 0.018. HOLD-era was opened once per track (THPC2_DP/DPO/HAZ/QR_P) after the PREHOLD file.

Gate failures (cells failing each gate): NOTC<=0 248, year_share>60% 238, paired_CI_excludes0 234, placebo_not_run 226, SPAN2<=0 207, neighbours_agree 146, 2x_cost<=0 117, mean_up 94, holdout_sign_agrees 89, maxDD_not_worse 37, placebo<0.90 7.

## Headline chains (best PRE-era cell of each model family; selection on PRE-era only) - recent-first, MDE80 in pts/trade

### dp|ew20|S1m|tod  (verdict DEAD; failed: paired_CI_excludes0;placebo<0.90;NOTC<=0;year_share>60%;SPAN2<=0; placebo rank 0.3333333333333333)

| span                                 |         n |   mean |     lo |    hi |   MDE |   exit_rate |   saved |   forfeited |   N_basis |   C_basis |    usd_wk |
|:-------------------------------------|----------:|-------:|-------:|------:|------:|------------:|--------:|------------:|----------:|----------:|----------:|
| 2026 (Jan-6 Feb)                     |  2229.000 |  1.273 | -0.700 | 3.280 | 2.828 |       0.592 |   6.851 |      -5.577 |    -0.941 |     0.975 | 79524.833 |
| last 6 mo (2025-08-07..2026-02-06)   |  9443.000 |  0.888 |  0.137 | 1.808 | 1.168 |       0.574 |   6.411 |      -5.523 |    -1.212 |     0.598 | 51616.695 |
| HOLD-era (2025-07..2026-02-06)       | 10805.000 |  0.923 |  0.176 | 1.725 | 1.073 |       0.572 |   6.469 |      -5.546 |    -1.151 |     0.634 | 49131.953 |
| PRE-era (2024-02..2025-06)           | 24654.000 |  0.474 | -0.008 | 1.017 | 0.738 |       0.554 |   6.324 |      -5.851 |    -0.823 |     0.194 | 25404.333 |
| X' (2023-07..2024-01, short history) |  6487.000 | -0.090 | -1.039 | 0.904 | 1.339 |       0.567 |   6.530 |      -6.620 |    -0.762 |    -0.376 | -5675.440 |

### dpo|ew20|Sonline|tod  (verdict DEAD; failed: paired_CI_excludes0;placebo<0.90;NOTC<=0;year_share>60%;SPAN2<=0; placebo rank 0.0)

| span                                 |         n |   mean |     lo |    hi |   MDE |   exit_rate |   saved |   forfeited |   N_basis |   C_basis |    usd_wk |
|:-------------------------------------|----------:|-------:|-------:|------:|------:|------------:|--------:|------------:|----------:|----------:|----------:|
| 2026 (Jan-6 Feb)                     |  2229.000 |  1.255 | -0.653 | 3.201 | 2.745 |       0.586 |   6.572 |      -5.317 |    -0.954 |     0.959 | 75812.049 |
| last 6 mo (2025-08-07..2026-02-06)   |  9443.000 |  0.836 |  0.137 | 1.746 | 1.132 |       0.570 |   6.152 |      -5.316 |    -1.264 |     0.548 | 48156.548 |
| HOLD-era (2025-07..2026-02-06)       | 10805.000 |  0.841 |  0.116 | 1.602 | 1.039 |       0.568 |   6.219 |      -5.377 |    -1.232 |     0.554 | 44589.681 |
| PRE-era (2024-02..2025-06)           | 24654.000 |  0.396 | -0.071 | 0.912 | 0.732 |       0.555 |   6.316 |      -5.919 |    -0.903 |     0.116 | 20514.935 |
| X' (2023-07..2024-01, short history) |  6487.000 | -0.072 | -1.074 | 0.865 | 1.348 |       0.565 |   6.555 |      -6.627 |    -0.744 |    -0.358 | -5459.149 |

### haz|ew10|S1w|reg  (verdict DEAD; failed: paired_CI_excludes0;holdout_sign_agrees;neighbours_agree;NOTC<=0;year_share>60%;SPAN2<=0; placebo rank 1.0)

| span                                 |         n |   mean |     lo |    hi |   MDE |   exit_rate |   saved |   forfeited |   N_basis |   C_basis |     usd_wk |
|:-------------------------------------|----------:|-------:|-------:|------:|------:|------------:|--------:|------------:|----------:|----------:|-----------:|
| 2026 (Jan-6 Feb)                     |  2229.000 |  0.640 | -1.491 | 2.934 | 3.140 |       0.337 |   6.865 |      -6.225 |    -0.294 |     0.470 |  37124.218 |
| last 6 mo (2025-08-07..2026-02-06)   |  9443.000 | -0.194 | -1.102 | 0.803 | 1.407 |       0.246 |   5.165 |      -5.359 |    -0.855 |    -0.318 | -13289.785 |
| HOLD-era (2025-07..2026-02-06)       | 10805.000 | -0.313 | -1.228 | 0.577 | 1.343 |       0.256 |   5.314 |      -5.627 |    -0.986 |    -0.442 | -18762.371 |
| PRE-era (2024-02..2025-06)           | 24654.000 |  0.381 | -0.043 | 0.900 | 0.664 |       0.190 |   4.385 |      -4.004 |    -0.051 |     0.286 |  20400.998 |
| X' (2023-07..2024-01, short history) |  6487.000 |  0.000 |  0.000 | 0.000 | 0.000 |       0.000 |   0.000 |       0.000 |     0.000 |     0.000 |      0.000 |

### qr|6m|Sintra|reg  (verdict DEAD; failed: neighbours_agree;NOTC<=0;year_share>60%; placebo rank 1.0)

| span                                 |         n |   mean |     lo |    hi |   MDE |   exit_rate |   saved |   forfeited |   N_basis |   C_basis |    usd_wk |
|:-------------------------------------|----------:|-------:|-------:|------:|------:|------------:|--------:|------------:|----------:|----------:|----------:|
| 2026 (Jan-6 Feb)                     |  2229.000 | -0.041 | -0.960 | 0.832 | 1.339 |       0.227 |   1.761 |      -1.801 |    -0.901 |    -0.155 | -7606.748 |
| last 6 mo (2025-08-07..2026-02-06)   |  9443.000 |  0.206 | -0.386 | 0.858 | 0.910 |       0.289 |   3.598 |      -3.391 |    -0.750 |     0.061 |  8033.508 |
| HOLD-era (2025-07..2026-02-06)       | 10805.000 |  0.431 | -0.197 | 1.004 | 0.849 |       0.301 |   4.067 |      -3.636 |    -0.537 |     0.279 | 19836.636 |
| PRE-era (2024-02..2025-06)           | 24654.000 |  0.500 |  0.270 | 0.764 | 0.377 |       0.232 |   2.280 |      -1.780 |    -0.015 |     0.383 | 28726.384 |
| X' (2023-07..2024-01, short history) |  6487.000 |  0.113 | -1.022 | 1.251 | 1.698 |       0.496 |   7.504 |      -7.390 |    -0.374 |    -0.137 |  8836.946 |

## By book / entry session / calendar year for the best PRE-era chain qr|6m|Sintra|reg

**by book**

|                |        n |   mean |     lo |     hi |   mde |   exit |   saved |   forfeited |   meanN |    usd_wk |
|:---------------|---------:|-------:|-------:|-------:|------:|-------:|--------:|------------:|--------:|----------:|
| ('PRE', 'DN')  | 1762.000 |  0.483 | -0.053 |  1.062 | 0.867 |  0.192 |   2.043 |      -1.560 |   0.092 |  2269.173 |
| ('PRE', 'HM')  | 2285.000 |  0.505 |  0.031 |  0.964 | 0.734 |  0.183 |   2.089 |      -1.584 |   0.131 |  3076.907 |
| ('PRE', 'KB')  | 3093.000 |  0.135 | -0.287 |  0.628 | 0.677 |  0.195 |   1.954 |      -1.819 |  -0.287 |   580.438 |
| ('PRE', 'MA')  | 1093.000 |  0.078 | -0.676 |  0.828 | 1.116 |  0.170 |   1.717 |      -1.640 |  -0.259 |   226.560 |
| ('PRE', 'MV')  | 2922.000 |  0.652 |  0.124 |  1.219 | 0.764 |  0.184 |   2.251 |      -1.599 |   0.259 |  5076.547 |
| ('PRE', 'PB')  | 2261.000 |  0.570 |  0.027 |  1.056 | 0.781 |  0.172 |   2.072 |      -1.502 |   0.225 |  3435.627 |
| ('PRE', 'PE')  | 3049.000 |  0.438 | -0.033 |  0.911 | 0.652 |  0.180 |   1.975 |      -1.536 |   0.061 |  1996.251 |
| ('PRE', 'SM')  |  904.000 | -0.737 | -1.722 | -0.017 | 1.239 |  0.159 |   1.094 |      -1.831 |  -1.047 | -1314.812 |
| ('PRE', 'ST')  | 3020.000 |  0.939 |  0.448 |  1.497 | 0.760 |  0.176 |   2.284 |      -1.345 |   0.588 |  7565.000 |
| ('PRE', 'WT')  | 4265.000 |  0.730 |  0.294 |  1.176 | 0.632 |  0.476 |   3.459 |      -2.729 |  -0.454 |  5814.694 |
| ('HOLD', 'DN') |  782.000 | -0.570 | -1.887 |  0.895 | 2.117 |  0.243 |   3.291 |      -3.861 |  -1.357 | -2784.719 |
| ('HOLD', 'HM') | 1008.000 | -0.298 | -1.600 |  0.932 | 1.944 |  0.244 |   3.670 |      -3.968 |  -1.051 | -1878.344 |
| ('HOLD', 'KB') | 1374.000 |  0.723 | -0.245 |  1.910 | 1.556 |  0.260 |   4.205 |      -3.483 |  -0.054 |  3227.608 |
| ('HOLD', 'MA') |  474.000 |  0.233 | -1.510 |  2.331 | 2.832 |  0.238 |   3.284 |      -3.051 |  -0.532 |   690.000 |
| ('HOLD', 'MV') | 1253.000 |  0.455 | -0.766 |  1.422 | 1.477 |  0.236 |   3.907 |      -3.453 |  -0.252 |  3560.438 |
| ('HOLD', 'PB') |  965.000 | -0.416 | -1.643 |  0.865 | 1.836 |  0.256 |   3.968 |      -4.384 |  -1.206 | -2510.906 |
| ('HOLD', 'PE') | 1311.000 | -0.113 | -1.162 |  0.987 | 1.455 |  0.227 |   3.389 |      -3.502 |  -0.801 |  -518.927 |
| ('HOLD', 'SM') |  363.000 |  1.788 |  0.055 |  3.700 | 2.742 |  0.215 |   4.480 |      -2.692 |   1.172 |  3001.371 |
| ('HOLD', 'ST') | 1382.000 |  0.448 | -0.615 |  1.598 | 1.720 |  0.230 |   4.116 |      -3.668 |  -0.235 |  3872.375 |
| ('HOLD', 'WT') | 1893.000 |  1.591 |  0.659 |  2.478 | 1.284 |  0.586 |   5.206 |      -3.615 |  -0.489 | 13177.740 |

**by entry session**

|                    |        n |   mean |     lo |     hi |    mde |   exit |   saved |   forfeited |   meanN |     usd_wk |
|:-------------------|---------:|-------:|-------:|-------:|-------:|-------:|--------:|------------:|--------:|-----------:|
| ('PRE', 'asia')    | 6319.000 |  0.336 |  0.021 |  0.925 |  0.633 |  0.190 |   1.473 |      -1.137 |  -0.078 |   5181.266 |
| ('PRE', 'close')   |   72.000 | -4.015 | -7.035 | -1.512 |  4.210 |  0.250 |   0.000 |      -4.015 |  -4.856 |   -702.433 |
| ('PRE', 'london')  | 5303.000 | -0.091 | -0.677 |  0.370 |  0.730 |  0.174 |   1.137 |      -1.228 |  -0.498 |   -615.067 |
| ('PRE', 'nyam')    | 6580.000 |  0.546 |  0.151 |  1.083 |  0.674 |  0.209 |   2.108 |      -1.562 |   0.129 |   8007.740 |
| ('PRE', 'nypm')    | 4901.000 |  1.240 |  0.390 |  2.101 |  1.233 |  0.416 |   5.068 |      -3.828 |   0.269 |  13776.531 |
| ('PRE', 'pre')     | 1479.000 |  0.876 | -0.184 |  2.041 |  1.570 |  0.118 |   1.466 |      -0.590 |   0.644 |   3078.346 |
| ('HOLD', 'asia')   | 3004.000 |  1.016 |  0.128 |  2.068 |  1.583 |  0.252 |   3.244 |      -2.228 |   0.167 |  15536.368 |
| ('HOLD', 'close')  |   25.000 |  5.908 | -3.255 | 17.093 | 15.072 |  0.280 |   8.383 |      -2.475 |   5.232 |    501.813 |
| ('HOLD', 'london') | 2243.000 |  0.536 | -0.514 |  1.786 |  1.799 |  0.200 |   2.532 |      -1.996 |  -0.132 |   5638.058 |
| ('HOLD', 'nyam')   | 3095.000 | -0.837 | -2.150 |  0.260 |  1.742 |  0.280 |   3.262 |      -4.098 |  -1.769 | -14464.942 |
| ('HOLD', 'nypm')   | 1898.000 |  0.844 | -1.094 |  2.667 |  2.837 |  0.567 |   8.702 |      -7.858 |  -0.850 |   6667.901 |
| ('HOLD', 'pre')    |  540.000 |  2.300 |  0.305 |  4.311 |  3.074 |  0.181 |   3.145 |      -0.845 |   1.754 |   5957.437 |

**by year**

|                |         n |   mean |     lo |    hi |   mde |   exit |   saved |   forfeited |   meanN |    usd_wk |
|:---------------|----------:|-------:|-------:|------:|------:|-------:|--------:|------------:|--------:|----------:|
| ('PRE', 2024)  | 13543.000 |  0.289 | -0.093 | 0.722 | 0.626 |  0.245 |   2.142 |      -1.854 |  -0.022 | 10754.695 |
| ('PRE', 2025)  | 11111.000 |  0.757 |  0.426 | 1.160 | 0.523 |  0.217 |   2.448 |      -1.691 |  -0.006 | 17971.689 |
| ('HOLD', 2025) |  8576.000 |  0.554 | -0.192 | 1.286 | 1.068 |  0.320 |   4.667 |      -4.113 |  -0.442 | 21025.190 |
| ('HOLD', 2026) |  2229.000 | -0.041 | -0.954 | 0.793 | 1.297 |  0.227 |   1.761 |      -1.801 |  -0.901 | -1188.554 |

## Regime read for qr|6m|Sintra|reg (weeks/days where the policy paid; ex-post day type is an analysis label only)

|                                                              |         n |   mean |   meanN |
|:-------------------------------------------------------------|----------:|-------:|--------:|
| ('daytype_EXPOST (analysis label only)', 'na', 'PRE')        |   410.000 | -0.462 |  -0.854 |
| ('daytype_EXPOST (analysis label only)', 'na', 'HOLD')       |   230.000 | -0.454 |  -1.317 |
| ('daytype_EXPOST (analysis label only)', 'range', 'PRE')     | 11181.000 |  1.182 |   0.698 |
| ('daytype_EXPOST (analysis label only)', 'range', 'HOLD')    |  4699.000 |  1.434 |   0.523 |
| ('daytype_EXPOST (analysis label only)', 'reversal', 'PRE')  |  2023.000 | -0.694 |  -1.417 |
| ('daytype_EXPOST (analysis label only)', 'reversal', 'HOLD') |   860.000 | -0.016 |  -0.944 |
| ('daytype_EXPOST (analysis label only)', 'trend', 'PRE')     | 11040.000 |  0.064 |  -0.449 |
| ('daytype_EXPOST (analysis label only)', 'trend', 'HOLD')    |  5016.000 | -0.391 |  -1.424 |
| ('VIX tercile (expanding)', 'VIX_low', 'PRE')                |  3377.000 |  0.098 |  -0.236 |
| ('VIX tercile (expanding)', 'VIX_low', 'HOLD')               |   565.000 |  3.513 |   2.590 |
| ('VIX tercile (expanding)', 'VIX_mid', 'PRE')                |  7305.000 |  0.441 |   0.009 |
| ('VIX tercile (expanding)', 'VIX_mid', 'HOLD')               |  6933.000 | -0.180 |  -1.220 |
| ('VIX tercile (expanding)', 'VIX_high', 'PRE')               | 13972.000 |  0.627 |   0.026 |
| ('VIX tercile (expanding)', 'VIX_high', 'HOLD')              |  3307.000 |  1.186 |   0.359 |

## Recency and re-fit frequency (mean over the cells; PRE-era | HOLD-era pts/trade)

|                 |   mean |   hold_mean |   meanN |
|:----------------|-------:|------------:|--------:|
| ('dp', '12m')   |  0.348 |       0.920 |  -0.952 |
| ('dp', '1m')    |  0.307 |       0.854 |  -0.983 |
| ('dp', '1w')    |  0.185 |       0.626 |  -1.086 |
| ('dp', '2w')    |  0.268 |       0.816 |  -1.008 |
| ('dp', '3m')    |  0.354 |       0.916 |  -0.948 |
| ('dp', '6m')    |  0.362 |       0.968 |  -0.940 |
| ('dp', 'YTD')   |  0.274 |       0.857 |  -0.993 |
| ('dp', 'ew10')  |  0.314 |       0.847 |  -0.981 |
| ('dp', 'ew20')  |  0.355 |       0.865 |  -0.946 |
| ('dp', 'ew5')   |  0.265 |       0.793 |  -1.021 |
| ('dpo', 'all')  |  0.344 |       0.898 |  -0.954 |
| ('dpo', 'ew10') |  0.308 |       0.794 |  -0.990 |
| ('dpo', 'ew20') |  0.319 |       0.841 |  -0.984 |
| ('dpo', 'ew5')  |  0.339 |       0.752 |  -0.956 |
| ('haz', '12m')  | -0.016 |       0.063 |  -0.064 |
| ('haz', '1m')   |  0.116 |      -0.238 |  -0.310 |
| ('haz', '1w')   | -0.069 |      -0.059 |  -0.197 |
| ('haz', '2w')   | -0.073 |      -0.086 |  -0.314 |
| ('haz', '3m')   | -0.309 |      -0.234 |  -0.600 |
| ('haz', '6m')   | -0.001 |       0.080 |  -0.096 |
| ('haz', 'YTD')  |  0.010 |      -0.305 |  -0.452 |
| ('haz', 'ew10') |  0.009 |      -0.180 |  -0.338 |
| ('haz', 'ew20') | -0.067 |      -0.387 |  -0.313 |
| ('haz', 'ew5')  | -0.062 |      -0.117 |  -0.446 |
| ('qr', '12m')   |  0.233 |       0.435 |  -0.259 |
| ('qr', '1m')    | -0.361 |       0.090 |  -0.990 |
| ('qr', '1w')    | -0.664 |       0.062 |  -1.464 |
| ('qr', '2w')    | -0.429 |      -0.133 |  -1.120 |
| ('qr', '3m')    |  0.143 |       0.146 |  -0.283 |
| ('qr', '6m')    |  0.222 |       0.854 |  -0.203 |
| ('qr', 'YTD')   | -0.028 |       0.612 |  -0.702 |
| ('qr', 'ew10')  | -0.280 |       0.220 |  -0.819 |
| ('qr', 'ew20')  | -0.004 |       0.339 |  -0.467 |
| ('qr', 'ew5')   | -0.114 |       0.100 |  -0.614 |

|                   |   mean |   hold_mean |   meanN |
|:------------------|-------:|------------:|--------:|
| ('dp', '1d')      |  0.298 |       0.843 |  -0.998 |
| ('dp', '1m')      |  0.327 |       0.868 |  -0.945 |
| ('dp', '1w')      |  0.286 |       0.822 |  -1.005 |
| ('dp', 'intra')   |  0.301 |       0.853 |  -0.995 |
| ('dpo', 'online') |  0.328 |       0.821 |  -0.971 |
| ('haz', '1d')     | -0.061 |      -0.105 |  -0.350 |
| ('haz', '1m')     | -0.074 |      -0.112 |  -0.288 |
| ('haz', '1w')     | -0.022 |      -0.182 |  -0.302 |
| ('haz', 'intra')  | -0.028 |      -0.185 |  -0.312 |
| ('qr', '1d')      | -0.145 |       0.419 |  -0.724 |
| ('qr', '1m')      | -0.098 |       0.162 |  -0.627 |
| ('qr', '1w')      | -0.161 |       0.092 |  -0.726 |
| ('qr', 'intra')   | -0.109 |       0.416 |  -0.691 |

|                 |   mean |   hold_mean |   meanN |
|:----------------|-------:|------------:|--------:|
| ('dp', 'none')  |  0.268 |       0.795 |  -1.019 |
| ('dp', 'tod')   |  0.339 |       0.898 |  -0.953 |
| ('dpo', 'none') |  0.286 |       0.795 |  -1.012 |
| ('dpo', 'tod')  |  0.369 |       0.848 |  -0.930 |
| ('haz', 'none') | -0.098 |      -0.132 |  -0.363 |
| ('haz', 'reg')  |  0.006 |      -0.160 |  -0.263 |
| ('qr', 'none')  | -0.211 |       0.396 |  -0.745 |
| ('qr', 'reg')   | -0.045 |       0.150 |  -0.639 |

## Top 10 by PRE-era delta (in-selection), regardless of verdict

|                      | model   | win   | step   | var   |   mean |     lo |    hi |   mde |   hold_mean |   hold_lo |   hold_hi |   hold_mde |   exit_rate |   hold_exit |   saved |   forfeited |   pre_meanN |   hold_meanN |    usd_wk |   hold_usd_wk | verdict   |
|:---------------------|:--------|:------|:-------|:------|-------:|-------:|------:|------:|------------:|----------:|----------:|-----------:|------------:|------------:|--------:|------------:|------------:|-------------:|----------:|--------------:|:----------|
| qr|6m|Sintra|reg     | qr      | 6m    | intra  | reg   |  0.500 |  0.268 | 0.790 | 0.397 |       0.431 |    -0.092 |     1.010 |      0.842 |       0.232 |       0.301 |   2.280 |      -1.780 |      -0.015 |       -0.537 | 28726.384 |     19836.636 | DEAD      |
| dp|ew20|S1m|tod      | dp      | ew20  | 1m     | tod   |  0.474 | -0.010 | 1.008 | 0.730 |       0.923 |     0.201 |     1.710 |      1.064 |       0.554 |       0.572 |   6.324 |      -5.851 |      -0.823 |       -1.151 | 25404.333 |     49131.953 | DEAD      |
| dp|ew20|S1w|tod      | dp      | ew20  | 1w     | tod   |  0.422 | -0.066 | 0.949 | 0.730 |       0.859 |     0.116 |     1.623 |      1.057 |       0.555 |       0.569 |   6.340 |      -5.918 |      -0.878 |       -1.215 | 22181.656 |     45805.313 | DEAD      |
| dp|2w|S1d|tod        | dp      | 2w    | 1d     | tod   |  0.410 | -0.109 | 0.909 | 0.753 |       0.931 |     0.235 |     1.712 |      1.087 |       0.562 |       0.565 |   7.015 |      -6.605 |      -0.884 |       -1.111 | 20679.633 |     45987.760 | DEAD      |
| dp|3m|S1w|tod        | dp      | 3m    | 1w     | tod   |  0.403 | -0.076 | 0.937 | 0.723 |       0.892 |     0.188 |     1.663 |      1.054 |       0.553 |       0.565 |   6.212 |      -5.809 |      -0.896 |       -1.172 | 21121.798 |     46583.280 | DEAD      |
| dp|6m|S1w|none       | dp      | 6m    | 1w     | none  |  0.396 | -0.101 | 0.927 | 0.743 |       0.897 |     0.195 |     1.750 |      1.073 |       0.556 |       0.574 |   6.612 |      -6.216 |      -0.907 |       -1.192 | 20954.200 |     45678.359 | DEAD      |
| dpo|ew20|Sonline|tod | dpo     | ew20  | online | tod   |  0.396 | -0.076 | 0.912 | 0.726 |       0.841 |     0.131 |     1.585 |      1.035 |       0.555 |       0.568 |   6.316 |      -5.920 |      -0.903 |       -1.232 | 20514.935 |     44589.681 | DEAD      |
| dp|2w|Sintra|tod     | dp      | 2w    | intra  | tod   |  0.394 | -0.105 | 0.890 | 0.754 |       0.950 |     0.253 |     1.694 |      1.088 |       0.562 |       0.565 |   7.001 |      -6.608 |      -0.900 |       -1.093 | 19783.473 |     47446.874 | DEAD      |
| dpo|ew5|Sonline|tod  | dpo     | ew5   | online | tod   |  0.393 | -0.105 | 0.920 | 0.735 |       0.785 |     0.034 |     1.646 |      1.090 |       0.560 |       0.566 |   6.799 |      -6.406 |      -0.909 |       -1.273 | 20712.740 |     39312.173 | DEAD      |
| dp|ew20|Sintra|tod   | dp      | ew20  | intra  | tod   |  0.392 | -0.078 | 0.914 | 0.726 |       0.806 |     0.098 |     1.529 |      1.033 |       0.555 |       0.567 |   6.311 |      -5.919 |      -0.907 |       -1.266 | 20412.977 |     42377.580 | DEAD      |

## Top 10 by HOLD-era delta (selection look), regardless of verdict

|                   | model   | win   | step   | var   |   mean |     lo |    hi |   mde |   hold_mean |   hold_lo |   hold_hi |   hold_mde |   exit_rate |   hold_exit |   saved |   forfeited |   pre_meanN |   hold_meanN |     usd_wk |   hold_usd_wk | verdict   |
|:------------------|:--------|:------|:-------|:------|-------:|-------:|------:|------:|------------:|----------:|----------:|-----------:|------------:|------------:|--------:|------------:|------------:|-------------:|-----------:|--------------:|:----------|
| qr|6m|S1w|none    | qr      | 6m    | 1w     | none  | -0.004 | -0.287 | 0.253 | 0.363 |       1.434 |     0.728 |     2.116 |      1.012 |       0.171 |       0.345 |   1.123 |      -1.127 |      -0.337 |        0.289 |   -946.555 |     79264.746 | DEAD      |
| qr|6m|S1w|reg     | qr      | 6m    | 1w     | reg   |  0.107 | -0.195 | 0.395 | 0.424 |       1.204 |     0.479 |     2.007 |      1.069 |       0.226 |       0.309 |   1.916 |      -1.809 |      -0.400 |        0.270 |   5559.339 |     65831.674 | DEAD      |
| qr|6m|S1m|none    | qr      | 6m    | 1m     | none  |  0.155 |  0.069 | 0.257 | 0.134 |       1.169 |     0.546 |     1.917 |      0.940 |       0.135 |       0.353 |   0.568 |      -0.414 |      -0.163 |       -0.031 |   7801.069 |     67138.577 | DEAD      |
| dp|6m|S1w|tod     | dp      | 6m    | 1w     | tod   |  0.347 | -0.095 | 0.884 | 0.708 |       1.022 |     0.302 |     1.828 |      1.047 |       0.552 |       0.570 |   6.085 |      -5.738 |      -0.954 |       -1.059 |  17802.585 |     53510.064 | DEAD      |
| dp|6m|Sintra|tod  | dp      | 6m    | intra  | tod   |  0.345 | -0.097 | 0.870 | 0.708 |       1.009 |     0.290 |     1.796 |      1.050 |       0.552 |       0.570 |   6.092 |      -5.747 |      -0.957 |       -1.072 |  17468.242 |     52651.508 | DEAD      |
| dp|6m|S1d|tod     | dp      | 6m    | 1d     | tod   |  0.340 | -0.101 | 0.855 | 0.707 |       1.006 |     0.289 |     1.794 |      1.049 |       0.552 |       0.570 |   6.087 |      -5.747 |      -0.961 |       -1.074 |  17155.238 |     52528.383 | DEAD      |
| dp|6m|S1m|tod     | dp      | 6m    | 1m     | tod   |  0.352 | -0.091 | 0.892 | 0.709 |       1.003 |     0.299 |     1.850 |      1.050 |       0.551 |       0.573 |   6.066 |      -5.714 |      -0.948 |       -1.083 |  18016.109 |     52184.214 | DEAD      |
| dp|3m|S1m|tod     | dp      | 3m    | 1m     | tod   |  0.377 | -0.090 | 0.892 | 0.720 |       0.985 |     0.259 |     1.777 |      1.067 |       0.552 |       0.570 |   6.179 |      -5.803 |      -0.919 |       -1.084 |  19488.522 |     52389.407 | DEAD      |
| qr|1w|Sintra|none | qr      | 1w    | intra  | none  | -0.548 | -1.271 | 0.250 | 1.104 |       0.972 |    -0.135 |     1.973 |      1.483 |       0.455 |       0.459 |   9.951 |     -10.499 |      -1.366 |       -0.336 | -31919.216 |     55306.263 | DEAD      |
| dp|6m|S1m|none    | dp      | 6m    | 1m     | none  |  0.373 | -0.108 | 0.901 | 0.731 |       0.968 |     0.265 |     1.854 |      1.087 |       0.553 |       0.577 |   6.483 |      -6.110 |      -0.924 |       -1.123 |  19364.607 |     50412.544 | DEAD      |

## Placebos of the finalists (PRE-era; rank = share of placebo draws below the chain)

See DS3_THP_C2_PREHOLD.md finalists tables (shuffled labels within day, 6 draws; causal random exits at the same exit rate, 200 draws).



# LOSS SIDE (hold / cut vs hold-to-stop)

**Verdicts, 248 registered core cells: {'DEAD': 248}.** PRE-era delta>0 18; PRE CI>0 0 (chance ~6.2); HOLD delta>0 33; both >0 1; HOLD CI lower>0 0; reality check on PRE-era (best of 248) p = 0.971. HOLD-era was opened once per track (THPC2_DP/DPO/HAZ/QR_L) after the PREHOLD file.

Gate failures (cells failing each gate): paired_CI_excludes0 248, neighbours_agree 248, NOTC<=0 248, year_share>60% 248, RC_p>0.05 248, 2x_cost<=0 243, SPAN2<=0 233, mean_up 230, placebo_not_run 226, holdout_sign_agrees 215, maxDD_not_worse 155, placebo<0.90 7.

## Headline chains (best PRE-era cell of each model family; selection on PRE-era only) - recent-first, MDE80 in pts/trade

### dp|12m|S1m|tod  (verdict DEAD; failed: paired_CI_excludes0;holdout_sign_agrees;neighbours_agree;2x_cost<=0;NOTC<=0;year_share>60%;SPAN2<=0;RC_p>0.05; placebo rank 0.995)

| span                                 |         n |   mean |     lo |    hi |   MDE |   exit_rate |   saved |   forfeited |   N_basis |   C_basis |     usd_wk |
|:-------------------------------------|----------:|-------:|-------:|------:|------:|------------:|--------:|------------:|----------:|----------:|-----------:|
| 2026 (Jan-6 Feb)                     |  2229.000 | -0.525 | -1.990 | 0.780 | 1.957 |       0.108 |   2.394 |      -2.920 |    -0.745 |    -0.580 | -36400.645 |
| last 6 mo (2025-08-07..2026-02-06)   |  9443.000 | -0.292 | -0.929 | 0.283 | 0.841 |       0.113 |   2.376 |      -2.668 |    -0.482 |    -0.349 | -17708.164 |
| HOLD-era (2025-07..2026-02-06)       | 10805.000 | -0.311 | -0.892 | 0.171 | 0.762 |       0.111 |   2.239 |      -2.550 |    -0.490 |    -0.367 | -17936.269 |
| PRE-era (2024-02..2025-06)           | 24654.000 |  0.078 | -0.102 | 0.251 | 0.254 |       0.031 |   0.716 |      -0.637 |     0.056 |     0.063 |   4863.871 |
| X' (2023-07..2024-01, short history) |  6487.000 | -0.337 | -1.588 | 0.878 | 1.826 |       0.324 |   7.499 |      -7.836 |    -0.518 |    -0.501 | -11309.039 |

### dpo|all|Sonline|none  (verdict DEAD; failed: mean_up;paired_CI_excludes0;holdout_sign_agrees;placebo<0.90;neighbours_agree;2x_cost<=0;NOTC<=0;year_share>60%;SPAN2<=0;RC_p>0.05; placebo rank 0.0)

| span                                 |         n |   mean |     lo |    hi |   MDE |   exit_rate |   saved |   forfeited |   N_basis |   C_basis |     usd_wk |
|:-------------------------------------|----------:|-------:|-------:|------:|------:|------------:|--------:|------------:|----------:|----------:|-----------:|
| 2026 (Jan-6 Feb)                     |  2229.000 |  0.000 |  0.000 | 0.000 | 0.000 |       0.000 |   0.000 |       0.000 |     0.000 |     0.000 |      0.000 |
| last 6 mo (2025-08-07..2026-02-06)   |  9443.000 |  0.000 |  0.000 | 0.000 | 0.000 |       0.000 |   0.000 |       0.000 |     0.000 |     0.000 |      0.000 |
| HOLD-era (2025-07..2026-02-06)       | 10805.000 |  0.000 |  0.000 | 0.000 | 0.000 |       0.000 |   0.000 |       0.000 |     0.000 |     0.000 |      0.000 |
| PRE-era (2024-02..2025-06)           | 24654.000 |  0.000 |  0.000 | 0.000 | 0.000 |       0.000 |   0.000 |       0.000 |     0.000 |     0.000 |      0.000 |
| X' (2023-07..2024-01, short history) |  6487.000 | -0.712 | -1.482 | 0.033 | 1.055 |       0.132 |   3.207 |      -3.919 |    -0.804 |    -0.778 | -24820.797 |

### haz|6m|S1d|reg  (verdict DEAD; failed: paired_CI_excludes0;holdout_sign_agrees;neighbours_agree;NOTC<=0;year_share>60%;RC_p>0.05; placebo rank 1.0)

| span                                 |         n |   mean |     lo |    hi |   MDE |   exit_rate |   saved |   forfeited |   N_basis |   C_basis |     usd_wk |
|:-------------------------------------|----------:|-------:|-------:|------:|------:|------------:|--------:|------------:|----------:|----------:|-----------:|
| 2026 (Jan-6 Feb)                     |  2229.000 |  0.000 |  0.000 | 0.000 | 0.000 |       0.000 |   0.000 |       0.000 |     0.000 |     0.000 |      0.000 |
| last 6 mo (2025-08-07..2026-02-06)   |  9443.000 | -0.228 | -0.679 | 0.199 | 0.634 |       0.074 |   1.742 |      -1.970 |    -0.363 |    -0.265 | -11000.786 |
| HOLD-era (2025-07..2026-02-06)       | 10805.000 | -0.055 | -0.635 | 0.560 | 0.878 |       0.106 |   2.591 |      -2.646 |    -0.239 |    -0.108 |   -671.188 |
| PRE-era (2024-02..2025-06)           | 24654.000 |  0.206 | -0.116 | 0.525 | 0.471 |       0.065 |   1.812 |      -1.606 |     0.137 |     0.172 |  11244.869 |
| X' (2023-07..2024-01, short history) |  6487.000 |  0.091 |  0.009 | 0.190 | 0.137 |       0.006 |   0.205 |      -0.114 |     0.089 |     0.088 |   3396.155 |

### qr|6m|S1d|none  (verdict DEAD; failed: paired_CI_excludes0;neighbours_agree;NOTC<=0;year_share>60%;SPAN2<=0;RC_p>0.05; placebo rank 1.0)

| span                                 |         n |   mean |     lo |    hi |   MDE |   exit_rate |   saved |   forfeited |   N_basis |   C_basis |    usd_wk |
|:-------------------------------------|----------:|-------:|-------:|------:|------:|------------:|--------:|------------:|----------:|----------:|----------:|
| 2026 (Jan-6 Feb)                     |  2229.000 |  0.000 |  0.000 | 0.000 | 0.000 |       0.000 |   0.000 |       0.000 |     0.000 |     0.000 |     0.000 |
| last 6 mo (2025-08-07..2026-02-06)   |  9443.000 | -0.112 | -0.706 | 0.411 | 0.793 |       0.070 |   1.746 |      -1.858 |    -0.250 |    -0.147 | -4528.082 |
| HOLD-era (2025-07..2026-02-06)       | 10805.000 |  0.023 | -0.527 | 0.592 | 0.819 |       0.107 |   2.754 |      -2.731 |    -0.183 |    -0.031 |  3454.093 |
| PRE-era (2024-02..2025-06)           | 24654.000 |  0.087 | -0.141 | 0.286 | 0.319 |       0.043 |   1.205 |      -1.118 |     0.028 |     0.066 |  4786.634 |
| X' (2023-07..2024-01, short history) |  6487.000 | -0.157 | -1.672 | 1.317 | 2.068 |       0.367 |   9.471 |      -9.628 |    -0.395 |    -0.342 | -2796.335 |

## By book / entry session / calendar year for the best PRE-era chain haz|6m|S1d|reg

**by book**

|                |        n |   mean |     lo |    hi |   mde |   exit |   saved |   forfeited |   meanN |    usd_wk |
|:---------------|---------:|-------:|-------:|------:|------:|-------:|--------:|------------:|--------:|----------:|
| ('PRE', 'DN')  | 1762.000 |  0.074 | -0.812 | 0.731 | 1.059 |  0.064 |   1.798 |      -1.724 |   0.011 |   347.533 |
| ('PRE', 'HM')  | 2285.000 |  0.262 | -0.231 | 0.822 | 0.787 |  0.063 |   1.828 |      -1.565 |   0.199 |  1599.493 |
| ('PRE', 'KB')  | 3093.000 |  0.004 | -0.499 | 0.526 | 0.750 |  0.064 |   1.784 |      -1.780 |  -0.065 |    15.822 |
| ('PRE', 'MA')  | 1093.000 | -0.461 | -1.308 | 0.281 | 1.188 |  0.062 |   1.480 |      -1.942 |  -0.541 | -1344.853 |
| ('PRE', 'MV')  | 2922.000 |  0.368 | -0.166 | 0.934 | 0.797 |  0.064 |   1.985 |      -1.618 |   0.308 |  2864.573 |
| ('PRE', 'PB')  | 2261.000 |  0.175 | -0.337 | 0.731 | 0.776 |  0.074 |   2.147 |      -1.972 |   0.091 |  1056.813 |
| ('PRE', 'PE')  | 3049.000 |  0.513 | -0.059 | 1.128 | 0.854 |  0.065 |   2.026 |      -1.513 |   0.457 |  2337.268 |
| ('PRE', 'SM')  |  904.000 |  0.244 | -0.568 | 1.094 | 1.261 |  0.070 |   2.054 |      -1.810 |   0.182 |   435.248 |
| ('PRE', 'ST')  | 3020.000 |  0.413 | -0.013 | 0.955 | 0.710 |  0.063 |   1.957 |      -1.544 |   0.352 |  3322.160 |
| ('PRE', 'WT')  | 4265.000 |  0.077 | -0.189 | 0.387 | 0.429 |  0.067 |   1.309 |      -1.232 |  -0.009 |   610.811 |
| ('HOLD', 'DN') |  782.000 | -0.083 | -1.132 | 1.092 | 1.668 |  0.098 |   2.607 |      -2.690 |  -0.255 |  -405.437 |
| ('HOLD', 'HM') | 1008.000 |  0.242 | -0.823 | 1.346 | 1.510 |  0.105 |   2.806 |      -2.564 |   0.084 |  1524.156 |
| ('HOLD', 'KB') | 1374.000 | -0.806 | -1.769 | 0.043 | 1.393 |  0.101 |   2.293 |      -3.100 |  -0.996 | -3600.594 |
| ('HOLD', 'MA') |  474.000 | -0.588 | -2.369 | 1.302 | 2.492 |  0.135 |   3.355 |      -3.943 |  -0.836 | -1742.750 |
| ('HOLD', 'MV') | 1253.000 |  0.699 | -0.278 | 1.666 | 1.404 |  0.101 |   2.961 |      -2.263 |   0.554 |  5471.125 |
| ('HOLD', 'PB') |  965.000 | -0.231 | -1.100 | 0.841 | 1.333 |  0.108 |   2.720 |      -2.951 |  -0.427 | -1394.000 |
| ('HOLD', 'PE') | 1311.000 | -0.030 | -0.789 | 0.850 | 1.236 |  0.096 |   2.469 |      -2.499 |  -0.184 |  -138.022 |
| ('HOLD', 'SM') |  363.000 | -0.681 | -2.672 | 1.273 | 2.992 |  0.135 |   3.398 |      -4.079 |  -0.947 | -1143.115 |
| ('HOLD', 'ST') | 1382.000 | -0.129 | -0.872 | 0.657 | 1.143 |  0.109 |   2.774 |      -2.904 |  -0.308 | -1115.906 |
| ('HOLD', 'WT') | 1893.000 |  0.226 | -0.327 | 0.753 | 0.813 |  0.104 |   1.982 |      -1.756 |   0.015 |  1873.353 |

**by entry session**

|                    |        n |   mean |     lo |    hi |   mde |   exit |   saved |   forfeited |   meanN |    usd_wk |
|:-------------------|---------:|-------:|-------:|------:|------:|-------:|--------:|------------:|--------:|----------:|
| ('PRE', 'asia')    | 6319.000 | -0.169 | -0.717 | 0.352 | 0.774 |  0.070 |   1.823 |      -1.992 |  -0.256 | -2496.334 |
| ('PRE', 'close')   |   72.000 |  2.959 |  0.680 | 5.822 | 3.869 |  0.056 |   2.959 |       0.000 |   2.959 |   530.536 |
| ('PRE', 'london')  | 5303.000 |  0.634 |  0.031 | 1.255 | 0.894 |  0.064 |   1.990 |      -1.356 |   0.571 |  8171.782 |
| ('PRE', 'nyam')    | 6580.000 |  0.255 | -0.582 | 1.029 | 1.199 |  0.065 |   1.803 |      -1.548 |   0.193 |  3222.189 |
| ('PRE', 'nypm')    | 4901.000 |  0.303 | -0.356 | 0.897 | 0.825 |  0.064 |   1.694 |      -1.391 |   0.246 |  3347.558 |
| ('PRE', 'pre')     | 1479.000 | -0.411 | -1.479 | 0.571 | 1.598 |  0.061 |   1.493 |      -1.903 |  -0.494 | -1530.863 |
| ('HOLD', 'asia')   | 3004.000 |  0.140 | -0.962 | 1.303 | 1.636 |  0.114 |   3.133 |      -2.993 |  -0.088 |  4407.154 |
| ('HOLD', 'close')  |   25.000 | -2.392 | -9.205 | 0.000 | 7.122 |  0.040 |   0.000 |      -2.392 |  -2.560 |  -373.719 |
| ('HOLD', 'london') | 2243.000 | -0.688 | -2.004 | 0.753 | 2.126 |  0.099 |   2.089 |      -2.777 |  -0.879 | -8498.713 |
| ('HOLD', 'nyam')   | 3095.000 | -0.274 | -1.175 | 0.563 | 1.180 |  0.098 |   2.340 |      -2.614 |  -0.448 | -3434.734 |
| ('HOLD', 'nypm')   | 1898.000 |  0.257 | -1.006 | 1.597 | 1.905 |  0.115 |   2.531 |      -2.274 |   0.114 |  1954.280 |
| ('HOLD', 'pre')    |  540.000 |  1.759 | -0.067 | 4.096 | 3.043 |  0.102 |   3.436 |      -1.678 |   1.650 |  5274.543 |

**by year**

|                |         n |   mean |     lo |    hi |   mde |   exit |   saved |   forfeited |   meanN |    usd_wk |
|:---------------|----------:|-------:|-------:|------:|------:|-------:|--------:|------------:|--------:|----------:|
| ('PRE', 2024)  | 13543.000 | -0.045 | -0.501 | 0.427 | 0.630 |  0.068 |   1.747 |      -1.792 |  -0.089 |  -988.444 |
| ('PRE', 2025)  | 11111.000 |  0.511 |  0.042 | 1.041 | 0.730 |  0.063 |   1.891 |      -1.379 |   0.412 | 12233.312 |
| ('HOLD', 2025) |  8576.000 | -0.069 | -0.738 | 0.748 | 1.124 |  0.133 |   3.265 |      -3.334 |  -0.301 |  -671.188 |
| ('HOLD', 2026) |  2229.000 |  0.000 |  0.000 | 0.000 | 0.000 |  0.000 |   0.000 |       0.000 |   0.000 |     0.000 |

## Regime read for haz|6m|S1d|reg (weeks/days where the policy paid; ex-post day type is an analysis label only)

|                                                              |         n |   mean |   meanN |
|:-------------------------------------------------------------|----------:|-------:|--------:|
| ('daytype_EXPOST (analysis label only)', 'na', 'PRE')        |   410.000 |  2.719 |   2.637 |
| ('daytype_EXPOST (analysis label only)', 'na', 'HOLD')       |   230.000 | -4.385 |  -4.987 |
| ('daytype_EXPOST (analysis label only)', 'range', 'PRE')     | 11181.000 |  0.671 |   0.589 |
| ('daytype_EXPOST (analysis label only)', 'range', 'HOLD')    |  4699.000 |  0.660 |   0.554 |
| ('daytype_EXPOST (analysis label only)', 'reversal', 'PRE')  |  2023.000 | -0.618 |  -0.792 |
| ('daytype_EXPOST (analysis label only)', 'reversal', 'HOLD') |   860.000 |  0.239 |  -0.093 |
| ('daytype_EXPOST (analysis label only)', 'trend', 'PRE')     | 11040.000 | -0.209 |  -0.244 |
| ('daytype_EXPOST (analysis label only)', 'trend', 'HOLD')    |  5016.000 | -0.576 |  -0.789 |
| ('VIX tercile (expanding)', 'VIX_low', 'PRE')                |  3377.000 | -0.005 |  -0.007 |
| ('VIX tercile (expanding)', 'VIX_low', 'HOLD')               |   565.000 |  1.748 |   1.651 |
| ('VIX tercile (expanding)', 'VIX_mid', 'PRE')                |  7305.000 |  0.319 |   0.228 |
| ('VIX tercile (expanding)', 'VIX_mid', 'HOLD')               |  6933.000 |  0.010 |  -0.245 |
| ('VIX tercile (expanding)', 'VIX_high', 'PRE')               | 13972.000 |  0.197 |   0.123 |
| ('VIX tercile (expanding)', 'VIX_high', 'HOLD')              |  3307.000 | -0.499 |  -0.547 |

## Recency and re-fit frequency (mean over the cells; PRE-era | HOLD-era pts/trade)

|                 |   mean |   hold_mean |   meanN |
|:----------------|-------:|------------:|--------:|
| ('dp', '12m')   |  0.030 |      -0.153 |   0.020 |
| ('dp', '1m')    | -0.686 |      -0.379 |  -1.005 |
| ('dp', '1w')    | -0.841 |      -0.806 |  -1.299 |
| ('dp', '2w')    | -0.625 |      -0.588 |  -1.022 |
| ('dp', '3m')    | -0.118 |      -0.859 |  -0.215 |
| ('dp', '6m')    | -0.010 |      -0.112 |  -0.076 |
| ('dp', 'YTD')   | -0.243 |      -0.345 |  -0.478 |
| ('dp', 'ew10')  | -0.484 |      -0.515 |  -0.753 |
| ('dp', 'ew20')  | -0.341 |      -0.497 |  -0.490 |
| ('dp', 'ew5')   | -0.642 |      -0.412 |  -0.991 |
| ('dpo', 'all')  | -0.021 |      -0.021 |  -0.036 |
| ('dpo', 'ew10') | -0.657 |      -0.413 |  -0.960 |
| ('dpo', 'ew20') | -0.530 |      -0.423 |  -0.712 |
| ('dpo', 'ew5')  | -0.610 |      -0.410 |  -0.994 |
| ('haz', '12m')  | -0.177 |      -0.223 |  -0.258 |
| ('haz', '1m')   | -0.494 |      -0.054 |  -0.753 |
| ('haz', '1w')   | -0.307 |      -0.015 |  -0.449 |
| ('haz', '2w')   | -0.357 |      -0.035 |  -0.545 |
| ('haz', '3m')   | -0.255 |      -0.205 |  -0.334 |
| ('haz', '6m')   | -0.020 |      -0.324 |  -0.070 |
| ('haz', 'YTD')  | -0.437 |      -0.211 |  -0.756 |
| ('haz', 'ew10') | -0.432 |      -0.110 |  -0.535 |
| ('haz', 'ew20') | -0.144 |      -0.219 |  -0.279 |
| ('haz', 'ew5')  | -0.293 |      -0.514 |  -0.462 |
| ('qr', '12m')   | -0.148 |      -0.114 |  -0.240 |
| ('qr', '1m')    | -0.820 |      -0.341 |  -1.185 |
| ('qr', '1w')    | -1.209 |      -0.686 |  -1.830 |
| ('qr', '2w')    | -0.951 |      -0.156 |  -1.449 |
| ('qr', '3m')    | -0.082 |      -0.916 |  -0.149 |
| ('qr', '6m')    | -0.020 |      -0.383 |  -0.064 |
| ('qr', 'YTD')   | -0.394 |      -0.025 |  -0.946 |
| ('qr', 'ew10')  | -0.557 |      -0.402 |  -0.749 |
| ('qr', 'ew20')  | -0.269 |      -0.032 |  -0.418 |
| ('qr', 'ew5')   | -0.593 |      -0.559 |  -0.825 |

|                   |   mean |   hold_mean |   meanN |
|:------------------|-------:|------------:|--------:|
| ('dp', '1d')      | -0.428 |      -0.450 |  -0.676 |
| ('dp', '1m')      | -0.310 |      -0.438 |  -0.508 |
| ('dp', '1w')      | -0.432 |      -0.537 |  -0.679 |
| ('dp', 'intra')   | -0.414 |      -0.441 |  -0.661 |
| ('dpo', 'online') | -0.455 |      -0.317 |  -0.675 |
| ('haz', '1d')     | -0.346 |      -0.169 |  -0.524 |
| ('haz', '1m')     | -0.154 |      -0.224 |  -0.237 |
| ('haz', '1w')     | -0.336 |      -0.193 |  -0.507 |
| ('haz', 'intra')  | -0.330 |      -0.178 |  -0.508 |
| ('qr', '1d')      | -0.602 |      -0.265 |  -0.895 |
| ('qr', '1m')      | -0.381 |      -0.428 |  -0.625 |
| ('qr', '1w')      | -0.492 |      -0.516 |  -0.787 |
| ('qr', 'intra')   | -0.543 |      -0.236 |  -0.835 |

|                 |   mean |   hold_mean |   meanN |
|:----------------|-------:|------------:|--------:|
| ('dp', 'none')  | -0.442 |      -0.420 |  -0.644 |
| ('dp', 'tod')   | -0.350 |      -0.514 |  -0.618 |
| ('dpo', 'none') | -0.470 |      -0.239 |  -0.655 |
| ('dpo', 'tod')  | -0.439 |      -0.394 |  -0.696 |
| ('haz', 'none') | -0.279 |      -0.202 |  -0.425 |
| ('haz', 'reg')  | -0.304 |      -0.180 |  -0.463 |
| ('qr', 'none')  | -0.478 |      -0.400 |  -0.748 |
| ('qr', 'reg')   | -0.531 |      -0.323 |  -0.823 |

## Top 10 by PRE-era delta (in-selection), regardless of verdict

|                   | model   | win   | step   | var   |   mean |     lo |    hi |   mde |   hold_mean |   hold_lo |   hold_hi |   hold_mde |   exit_rate |   hold_exit |   saved |   forfeited |   pre_meanN |   hold_meanN |    usd_wk |   hold_usd_wk | verdict   |
|:------------------|:--------|:------|:-------|:------|-------:|-------:|------:|------:|------------:|----------:|----------:|-----------:|------------:|------------:|--------:|------------:|------------:|-------------:|----------:|--------------:|:----------|
| haz|6m|S1d|reg    | haz     | 6m    | 1d     | reg   |  0.206 | -0.124 | 0.503 | 0.464 |      -0.055 |    -0.625 |     0.561 |      0.848 |       0.065 |       0.106 |   1.812 |      -1.606 |       0.137 |       -0.239 | 11244.869 |      -671.188 | DEAD      |
| haz|6m|S1d|none   | haz     | 6m    | 1d     | none  |  0.143 | -0.124 | 0.445 | 0.418 |      -0.465 |    -1.010 |     0.062 |      0.807 |       0.058 |       0.078 |   1.587 |      -1.444 |       0.083 |       -0.617 |  7773.311 |    -24352.071 | DEAD      |
| qr|6m|S1d|none    | qr      | 6m    | 1d     | none  |  0.087 | -0.153 | 0.301 | 0.334 |       0.023 |    -0.543 |     0.592 |      0.822 |       0.043 |       0.107 |   1.205 |      -1.118 |       0.028 |       -0.183 |  4786.634 |      3454.093 | DEAD      |
| qr|6m|S1d|reg     | qr      | 6m    | 1d     | reg   |  0.087 | -0.153 | 0.301 | 0.334 |      -0.001 |    -0.559 |     0.572 |      0.837 |       0.043 |       0.109 |   1.205 |      -1.118 |       0.028 |       -0.213 |  4786.634 |      2192.675 | DEAD      |
| haz|6m|Sintra|reg | haz     | 6m    | intra  | reg   |  0.081 | -0.205 | 0.334 | 0.401 |      -0.433 |    -1.065 |     0.163 |      0.849 |       0.060 |       0.093 |   1.637 |      -1.556 |       0.010 |       -0.610 |  5942.406 |    -21423.805 | DEAD      |
| dp|12m|S1m|tod    | dp      | 12m   | 1m     | tod   |  0.078 | -0.103 | 0.264 | 0.269 |      -0.311 |    -0.866 |     0.173 |      0.743 |       0.031 |       0.111 |   0.716 |      -0.637 |       0.056 |       -0.490 |  4863.871 |    -17936.269 | DEAD      |
| dp|12m|S1w|tod    | dp      | 12m   | 1w     | tod   |  0.074 | -0.079 | 0.241 | 0.241 |      -0.286 |    -0.835 |     0.202 |      0.738 |       0.027 |       0.107 |   0.604 |      -0.530 |       0.054 |       -0.454 |  4784.038 |    -16753.315 | DEAD      |
| qr|3m|S1w|reg     | qr      | 3m    | 1w     | reg   |  0.071 | -0.116 | 0.278 | 0.273 |      -1.168 |    -1.843 |    -0.504 |      1.020 |       0.037 |       0.150 |   1.009 |      -0.938 |       0.006 |       -1.506 |  4675.394 |    -66807.060 | DEAD      |
| haz|ew20|S1d|none | haz     | ew20  | 1d     | none  |  0.071 | -0.254 | 0.438 | 0.481 |      -0.061 |    -0.624 |     0.492 |      0.787 |       0.089 |       0.072 |   2.338 |      -2.267 |      -0.040 |       -0.194 |  2681.893 |     -1727.448 | DEAD      |
| qr|3m|S1w|none    | qr      | 3m    | 1w     | none  |  0.069 | -0.103 | 0.262 | 0.265 |      -1.279 |    -2.014 |    -0.626 |      1.020 |       0.036 |       0.139 |   0.959 |      -0.890 |       0.010 |       -1.605 |  4422.579 |    -72332.807 | DEAD      |

## Top 10 by HOLD-era delta (selection look), regardless of verdict

|                  | model   | win   | step   | var   |   mean |     lo |     hi |   mde |   hold_mean |   hold_lo |   hold_hi |   hold_mde |   exit_rate |   hold_exit |   saved |   forfeited |   pre_meanN |   hold_meanN |     usd_wk |   hold_usd_wk | verdict   |
|:-----------------|:--------|:------|:-------|:------|-------:|-------:|-------:|------:|------------:|----------:|----------:|-----------:|------------:|------------:|--------:|------------:|------------:|-------------:|-----------:|--------------:|:----------|
| haz|1m|S1w|reg   | haz     | 1m    | 1w     | reg   | -0.562 | -1.103 |  0.019 | 0.799 |       0.383 |    -0.393 |     1.180 |      1.140 |       0.175 |       0.128 |   4.363 |      -4.926 |      -0.861 |        0.146 | -32283.125 |     18112.401 | DEAD      |
| haz|1m|S1w|none  | haz     | 1m    | 1w     | none  | -0.563 | -1.110 |  0.005 | 0.798 |       0.347 |    -0.429 |     1.123 |      1.131 |       0.173 |       0.128 |   4.308 |      -4.871 |      -0.857 |        0.111 | -32311.659 |     16175.895 | DEAD      |
| qr|YTD|S1w|none  | qr      | YTD   | 1w     | none  | -0.458 | -1.074 |  0.200 | 0.967 |       0.250 |    -0.326 |     0.758 |      0.778 |       0.303 |       0.090 |   7.942 |      -8.401 |      -1.074 |        0.083 | -27978.293 |     15714.899 | DEAD      |
| qr|YTD|S1w|reg   | qr      | YTD   | 1w     | reg   | -0.444 | -1.037 |  0.189 | 0.932 |       0.250 |    -0.325 |     0.758 |      0.778 |       0.292 |       0.089 |   7.620 |      -8.064 |      -1.032 |        0.083 | -27542.607 |     15721.784 | DEAD      |
| haz|12m|S1d|reg  | haz     | 12m   | 1d     | reg   | -0.253 | -0.580 |  0.054 | 0.433 |       0.207 |    -0.421 |     0.944 |      1.008 |       0.069 |       0.115 |   1.669 |      -1.922 |      -0.373 |        0.004 | -14751.086 |     12100.474 | DEAD      |
| qr|2w|S1d|none   | qr      | 2w    | 1d     | none  | -0.892 | -1.637 | -0.048 | 1.119 |       0.191 |    -1.007 |     1.159 |      1.518 |       0.357 |       0.285 |   8.970 |      -9.863 |      -1.387 |       -0.352 | -51319.485 |      7114.492 | DEAD      |
| haz|YTD|S1w|none | haz     | YTD   | 1w     | none  | -0.584 | -1.136 |  0.004 | 0.816 |       0.176 |    -0.343 |     0.685 |      0.712 |       0.210 |       0.080 |   5.322 |      -5.906 |      -0.988 |        0.043 | -33848.382 |     12133.356 | DEAD      |
| haz|2w|S1m|reg   | haz     | 2w    | 1m     | reg   |  0.000 |  0.000 |  0.000 | 0.000 |       0.170 |    -0.628 |     0.844 |      0.991 |       0.000 |       0.125 |   0.000 |       0.000 |       0.000 |       -0.062 |      0.000 |      7660.602 | DEAD      |
| haz|YTD|S1w|reg  | haz     | YTD   | 1w     | reg   | -0.454 | -0.923 |  0.128 | 0.712 |       0.164 |    -0.345 |     0.681 |      0.727 |       0.164 |       0.082 |   4.184 |      -4.638 |      -0.777 |        0.019 | -24861.352 |     11227.954 | DEAD      |
| haz|ew20|S1w|reg | haz     | ew20  | 1w     | reg   | -0.280 | -0.654 |  0.082 | 0.542 |       0.125 |    -0.424 |     0.689 |      0.738 |       0.100 |       0.070 |   2.502 |      -2.781 |      -0.442 |        0.008 | -17373.248 |      7487.031 | DEAD      |

## Placebos of the finalists (PRE-era; rank = share of placebo draws below the chain)

See DS3_THP_C2_PREHOLD.md finalists tables (shuffled labels within day, 6 draws; causal random exits at the same exit rate, 200 draws).


# DRIFT of the fitted objects over time
### QR 6m regime (profit) refit drift by quarter: share of refits with an active rule, rule family (0 q50, 1 literal q10, 2 q90, -1 none), mean threshold, training gain/exit rate, q50 coefficients

| q      |   share_active |   fam_mode |   thr_mean |   train_gain |   train_exit |   q50 coef pct |   q50 coef dd/R |   q50 coef recov/R |   q50 coef delta60/100 |
|:-------|---------------:|-----------:|-----------:|-------------:|-------------:|---------------:|----------------:|-------------------:|-----------------------:|
| 2023Q3 |          0.995 |      0.000 |     -0.195 |        1.294 |        0.487 |        -16.542 |         -23.926 |              6.696 |                 -0.272 |
| 2023Q4 |          0.964 |      0.000 |     -2.495 |        0.620 |        0.371 |        -38.436 |          -8.393 |              0.541 |                  0.017 |
| 2024Q1 |          0.842 |      0.000 |     -4.063 |        0.310 |        0.211 |        -47.231 |          -0.214 |             -0.599 |                  0.053 |
| 2024Q2 |          0.851 |      0.000 |     -3.226 |        0.249 |        0.215 |        -39.461 |           1.929 |             -2.263 |                  0.114 |
| 2024Q3 |          0.833 |      0.000 |     -1.750 |        0.216 |        0.192 |        -37.687 |           0.046 |             -3.645 |                  0.106 |
| 2024Q4 |          0.753 |      0.000 |     -1.879 |        0.192 |        0.143 |        -43.012 |          -3.628 |             -4.202 |                 -0.029 |
| 2025Q1 |          0.974 |      0.000 |     -1.639 |        0.479 |        0.185 |        -46.870 |          -3.645 |             -3.338 |                 -0.011 |
| 2025Q2 |          0.964 |      0.000 |     -1.086 |        0.356 |        0.155 |        -47.074 |          -2.318 |             -1.521 |                  0.001 |
| 2025Q3 |          1.000 |      0.000 |     -2.136 |        0.693 |        0.246 |        -48.594 |           0.108 |             -0.024 |                  0.022 |
| 2025Q4 |          1.000 |      0.000 |     -1.840 |        0.736 |        0.259 |        -47.475 |          -0.855 |             -0.700 |                  0.008 |
| 2026Q1 |          1.000 |      0.000 |     -1.468 |        0.541 |        0.206 |        -46.642 |          -0.643 |             -0.706 |                 -0.001 |

### QR 6m regime (loss) refit drift by quarter: share of refits with an active rule, rule family (0 q50, 1 literal q10, 2 q90, -1 none), mean threshold, training gain/exit rate, q50 coefficients

| q      |   share_active |   fam_mode |   thr_mean |   train_gain |   train_exit |   q50 coef pct |   q50 coef dd/R |   q50 coef recov/R |   q50 coef delta60/100 |
|:-------|---------------:|-----------:|-----------:|-------------:|-------------:|---------------:|----------------:|-------------------:|-----------------------:|
| 2023Q3 |          0.533 |      0.000 |     -1.272 |        0.392 |        0.523 |          7.823 |          -6.458 |             16.773 |                 -0.175 |
| 2023Q4 |          0.193 |     -1.000 |     -0.557 |        0.140 |        0.190 |         10.647 |           0.154 |              6.963 |                  0.022 |
| 2024Q1 |          0.021 |     -1.000 |     -0.058 |        0.007 |        0.025 |          5.941 |           2.385 |              3.360 |                  0.094 |
| 2024Q2 |          0.026 |     -1.000 |     -0.082 |        0.007 |        0.024 |          4.113 |           3.844 |              5.227 |                  0.079 |
| 2024Q3 |          0.020 |     -1.000 |     -0.045 |        0.013 |        0.018 |          4.777 |           2.995 |              5.281 |                 -0.031 |
| 2024Q4 |          0.057 |     -1.000 |     -0.227 |        0.040 |        0.056 |          5.856 |          -0.356 |              0.441 |                  0.041 |
| 2025Q1 |          0.074 |     -1.000 |      0.000 |        0.039 |        0.080 |          8.512 |           1.241 |              4.551 |                  0.063 |
| 2025Q2 |          0.083 |     -1.000 |      0.073 |        0.033 |        0.081 |         20.307 |           4.723 |             15.607 |                 -0.204 |
| 2025Q3 |          0.253 |     -1.000 |     -0.303 |        0.145 |        0.220 |          5.754 |           1.997 |              1.346 |                  0.075 |
| 2025Q4 |          0.021 |     -1.000 |      0.000 |        0.015 |        0.023 |          8.558 |          -2.270 |             -5.873 |                  0.099 |
| 2026Q1 |          0.013 |     -1.000 |     -0.103 |        0.011 |        0.011 |         18.683 |          -8.113 |            -16.202 |                  0.120 |

### DP ew20/tod table drift by quarter: visit-weighted share of states where stopping beats continuing (profit / loss tables), trades in window

| q      |   take_profit |   take_loss |      ntr |
|:-------|--------------:|------------:|---------:|
| 2023Q3 |         0.057 |       0.007 | 1181.917 |
| 2023Q4 |         0.058 |       0.009 | 1258.977 |
| 2024Q1 |         0.054 |       0.001 | 1167.948 |
| 2024Q2 |         0.062 |       0.007 | 1288.717 |
| 2024Q3 |         0.068 |       0.009 | 1852.804 |
| 2024Q4 |         0.070 |       0.004 | 1784.948 |
| 2025Q1 |         0.085 |       0.012 | 2024.040 |
| 2025Q2 |         0.095 |       0.013 | 2691.170 |
| 2025Q3 |         0.079 |       0.023 | 1744.966 |
| 2025Q4 |         0.076 |       0.004 | 2052.231 |
| 2026Q1 |         0.079 |       0.006 | 2048.838 |

DP profit table: share of the 1440 states flipping hold/take between successive checkpoints (about monthly): mean 0.021, max 0.031.

### Hazard 6m regime (profit) drift by quarter: active share, mean threshold, target-hazard / stop-hazard coefficients

| q      |             thr |   bt_pct |   bs_pct |   bt_logdt |   bs_logds |   active |
|:-------|----------------:|---------:|---------:|-----------:|-----------:|---------:|
| 2023Q3 |  -969230769.292 |    0.100 |    0.001 |     -0.018 |      0.001 |    0.031 |
| 2023Q4 | -1000000000.000 |    0.000 |    0.000 |      0.000 |      0.000 |    0.000 |
| 2024Q1 | -1000000000.000 |    0.000 |    0.000 |      0.000 |      0.000 |    0.000 |
| 2024Q2 |  -948717948.844 |    0.247 |   -0.009 |     -0.191 |     -0.008 |    0.051 |
| 2024Q3 |  -838383838.745 |    0.846 |   -0.033 |     -0.532 |     -0.033 |    0.162 |
| 2024Q4 |  -927835051.724 |    0.572 |   -0.022 |     -0.364 |     -0.018 |    0.072 |
| 2025Q1 |  -973684210.616 |    1.268 |   -0.037 |     -0.725 |     -0.033 |    0.026 |
| 2025Q2 |  -718750000.109 |    2.287 |   -0.201 |     -1.104 |     -0.153 |    0.281 |
| 2025Q3 |  -429292929.210 |    2.284 |   -0.248 |     -1.159 |     -0.211 |    0.571 |
| 2025Q4 |  -768041237.088 |    1.293 |   -0.108 |     -0.760 |     -0.107 |    0.232 |
| 2026Q1 |  -846153846.147 |    1.496 |   -0.103 |     -0.902 |     -0.087 |    0.154 |

### Hazard 6m regime (loss) drift by quarter: active share, mean threshold, target-hazard / stop-hazard coefficients

| q      |             thr |   bt_pct |   bs_pct |   bt_logdt |   bs_logds |   active |
|:-------|----------------:|---------:|---------:|-----------:|-----------:|---------:|
| 2023Q3 |  -994871794.862 |    0.002 |   -0.018 |      0.000 |     -0.004 |    0.005 |
| 2023Q4 |  -994791666.698 |    0.001 |   -0.001 |      0.000 |     -0.019 |    0.005 |
| 2024Q1 | -1000000000.000 |    0.003 |   -0.043 |     -0.001 |     -0.066 |    0.000 |
| 2024Q2 |  -984615384.667 |    0.096 |   -0.389 |     -0.063 |     -0.638 |    0.015 |
| 2024Q3 |  -939393939.535 |    0.200 |   -0.691 |     -0.119 |     -1.101 |    0.061 |
| 2024Q4 |  -860824742.714 |    0.259 |   -0.730 |     -0.153 |     -1.037 |    0.139 |
| 2025Q1 |  -900000000.347 |    0.208 |   -0.695 |     -0.121 |     -0.795 |    0.100 |
| 2025Q2 |  -911458333.513 |    0.286 |   -1.130 |     -0.152 |     -1.117 |    0.089 |
| 2025Q3 |  -717171717.783 |    0.270 |   -1.190 |     -0.137 |     -1.156 |    0.283 |
| 2025Q4 |  -958762886.634 |    0.157 |   -0.954 |     -0.090 |     -0.849 |    0.041 |
| 2026Q1 |  -987179487.218 |    0.155 |   -1.068 |     -0.073 |     -0.972 |    0.013 |


# DISTILLED CANDIDATE POLICY (wf/c2/policy_candidate.txt)
Profit: CART, at most 12 leaves, features pct, mins, secs_ext, dd, recov, vel30, eff120, delta60 only, fitted monthly on the 6m-regime-QR policy's own take/hold decisions over the trailing 6 months of 1-min rows and applied to the next month; 3 profit take rules result. Loss: 0 rules (the best loss model is not distillable and its gain is inside the MDE). Retained gain of the distilled monthly chain vs the model's monthly chain (mean delta pts/trade, MDE beside it):

| span      |         n |   model_mean |   distilled_mean |   distilled_lo |   distilled_hi |   MDE |   retained |   exit_rate |   distilled_N_basis |
|:----------|----------:|-------------:|-----------------:|---------------:|---------------:|------:|-----------:|------------:|--------------------:|
| 2026      |  2229.000 |        0.210 |            0.154 |         -0.918 |          1.321 | 1.651 |      0.736 |       0.208 |              -0.606 |
| last 6 mo |  9443.000 |        0.518 |           -0.147 |         -0.940 |          0.621 | 1.108 |     -0.283 |       0.277 |              -1.047 |
| HOLD-era  | 10805.000 |        0.958 |           -0.269 |         -0.959 |          0.453 | 1.054 |     -0.281 |       0.277 |              -1.153 |
| PRE-era   | 24654.000 |        0.232 |            0.163 |         -0.189 |          0.579 | 0.547 |      0.702 |       0.183 |              -0.324 |
| X'        |  6487.000 |        0.023 |            0.223 |         -0.456 |          0.926 | 0.978 |      9.895 |       0.432 |              -0.298 |

The 80% retained-gain target is NOT met (PRE-era 0.70, HOLD-era negative). The file is labelled candidate-only/DEAD; do not run it.
