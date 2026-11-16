# DS3_FLOW - T-FLOW (order-by-order flow, other markets, score sizing, flow-as-entry), W-FL1

VERDICT (data ends 2026-10-31; FIRST PASS; base JN05W2 provisional, base lots, engine fee $1.18 with $4.84 column, live = x1.75): engine side running (43 FL cell-months done, 8 set x window rows scored); Part D flow-as-entry shadow books: 0 survivors in the first pass (see section 7); Part B other markets: no family beyond the nonsense pass rate at table level; see sections below. No PASS claim.

Basis: exact engine (identity TL3_FL_ID 202610 = 598 trades / 25,943.82), all layers ON as in JN05W2 (ATR-SKIP, P7 blackout and Jn04 stack cap may be missing from the JN05W2 set: all deltas base-relative, provisional). Hook th_flow/fl_hooks.py (keep, size m, target tg, WAIT hold w s). Skip rules read against SKIP_RND (engine random skip, same keep share and scope, PATH_EFFECT_RULE). Size and WAIT are read against their own controls (HALF==X2 after constant-risk normalisation; WAIT against unconditional HOLD of the same length).

## 1. Engine results: Part A lead (c_imb_n5_60_lo) and Part B items, per scope and window

### window L3M

| set | scope | n | d_wk | d_wk175 | d_wk484 | dd | base_dd | d_dd | cn | base_cn | cexp | base_cexp | d_cwk | cdd | base_cdd | wk_noW44 | base_wk_noW44 | dd_noW44 | base_dd_noW44 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TL3_FL_LEADU70_HALF | U70 | 1872 | 36.31 | 63.55 | 37.16 | 56403 | 52233 | 4170 | 72 | 72 | 517 | 602 | -471 | 14280 | 15497 | 24376 | 23989 | 43385 | 43405 |
| TL3_FL_LEADU70_SKIP | U70 | 1839 | -2666 | -4665 | -2630 | 55106 | 52233 | 2873 | 17 | 72 | 1954 | 602 | -778 | 4206 | 15497 | 21440 | 23989 | 48127 | 43405 |
| TL3_FL_LEADU70_SKIP_RND | U70 | 1849 | -6052 | -10590 | -6019 | 60662 | 52233 | 8429 | 17 | 72 | -140 | 602 | -3517 | 19164 | 15497 | 18217 | 23989 | 60662 | 43405 |
| TL3_FL_LEADU70_X15 | U70 | 1875 | 535 | 936 | 530 | 53105 | 52233 | 872 | 72 | 72 | 698 | 602 | 535 | 15479 | 15497 | 24641 | 23989 | 43387 | 43405 |
| TL3_FL_LEADU70_X2 | U70 | 1872 | 36.31 | 63.55 | 37.16 | 56403 | 52233 | 4170 | 72 | 72 | 517 | 602 | -471 | 14280 | 15497 | 24376 | 23989 | 43385 | 43405 |
| TL3_FL_LEADU7_HALF | U7 | 1875 | -657 | -1149 | -655 | 56341 | 52233 | 4107 | 120 | 121 | 500 | 518 | -212 | 14417 | 14457 | 23621 | 23989 | 43828 | 43405 |
| TL3_FL_LEADU7_SKIP | U7 | 1811 | -2964 | -5188 | -2901 | 56937 | 52233 | 4703 | 28 | 121 | 1265 | 518 | -2099 | 4181 | 14457 | 21000 | 23989 | 48183 | 43405 |
| TL3_FL_LEADU7_SKIP_RND | U7 | 1809 | -8859 | -15504 | -8797 | 64768 | 52233 | 12535 | 25 | 121 | -1272 | 518 | -7269 | 35831 | 14457 | 14799 | 23989 | 64768 | 43405 |


## 2. Part C score sizing (table-level screen on taken trades; engine sets queued)

| win | cell | mode | n_test | delta | delta175 | delta484 | mean_m | rand_ladder_pct | rand_ladder_mean | nonsense_mean | nonsense_p90 | beats_nonsense_p90 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | P7|1 | frozen | 382 | 28486 | 49851 | 27943 | 1.19 | 0.93 | -234 | -10367 | 9653 | True |
| L6M | P7|1 | refit2 | 382 | 18097 | 31670 | 17539 | 1.17 | 0.81 | 223 | -11512 | 2982 | True |
| L6M | P7|0 | frozen | 662 | 74356 | 130122 | 72416 | 1.17 | 0.64 | 54148 | 57975 | 137688 | False |
| L6M | P7|0 | refit2 | 662 | 33131 | 57980 | 30694 | 1.22 | 0.20 | 80558 | 49737 | 99024 | False |
| L6M | P7|3 | frozen | 124 | 18427 | 32248 | 18260 | 1.19 | 0.86 | 5280 | 945 | 19575 | False |
| L6M | P7|3 | refit2 | 124 | 7909 | 13841 | 7800 | 1.12 | 0.64 | 3573 | -2901 | 8258 | False |
| L6M | M7|1 | frozen | 579 | 32067 | 56117 | 31559 | 1.18 | 0.98 | -1115 | -5487 | 11079 | True |
| L6M | M7|1 | refit2 | 579 | 13891 | 24308 | 13248 | 1.22 | 0.84 | -1460 | -3150 | 20941 | False |
| L6M | M7|3 | frozen | 226 | 8155 | 14271 | 8038 | 1.14 | 0.73 | 3993 | 9747 | 15792 | False |
| L6M | M7|3 | refit2 | 226 | 6537 | 11441 | 6409 | 1.15 | 0.57 | 4933 | 8366 | 14347 | False |
| L6M | U7|0 | frozen | 175 | -33270 | -58222 | -32373 | 0.50 | 0.00 | -33270 | 11556 | 36260 | False |
| L6M | U7|0 | refit2 | 175 | -33270 | -58222 | -32373 | 0.50 | 0.00 | -33270 | 14609 | 41832 | False |
| L6M | K7|0 | frozen | 894 | 19549 | 34211 | 18674 | 1.21 | 0.43 | 22562 | 15751 | 34351 | False |
| L6M | K7|0 | refit2 | 894 | 32118 | 56206 | 31287 | 1.21 | 0.68 | 23118 | 5649 | 29060 | True |
| L6M | K7|1 | frozen | 471 | 6724 | 11767 | 6371 | 1.18 | 0.63 | 2398 | 4663 | 23822 | False |
| L6M | K7|1 | refit2 | 471 | -3218 | -5632 | -3590 | 1.19 | 0.39 | 981 | 5314 | 17348 | False |
| L6M | K7|3 | frozen | 197 | 154 | 270 | -12.47 | 1.23 | 0.40 | 1756 | 2119 | 9749 | False |
| L6M | K7|3 | refit2 | 197 | -4439 | -7769 | -4483 | 1.06 | 0.28 | -740 | -2625 | 6913 | False |
| L6M | A7|0 | frozen | 405 | 12596 | 22044 | 12269 | 1.22 | 0.79 | 3266 | -8301 | 1174 | True |
| L6M | A7|0 | refit2 | 405 | 2562 | 4483 | 2315 | 1.17 | 0.48 | 3114 | 10027 | 19780 | False |
| L6M | P7 | frozen | 1168 | 42754 | 74820 | 40098 | 1.17 | 0.40 | 57178 | 88602 | 145068 | False |
| L6M | P7 | refit2 | 1168 | 36645 | 64129 | 33550 | 1.21 | 0.25 | 78846 | 61472 | 102500 | False |
| L6M | M7 | frozen | 809 | 50865 | 89014 | 50336 | 1.14 | 1.00 | -243 | -7798 | 10664 | True |
| L6M | M7 | refit2 | 809 | 41002 | 71754 | 40354 | 1.18 | 0.99 | 1205 | -903 | 19517 | True |
| L6M | U7 | frozen | 298 | -54026 | -94546 | -52526 | 0.50 | 0.00 | -54026 | 37005 | 70423 | False |
| L6M | U7 | refit2 | 298 | -54026 | -94546 | -52526 | 0.50 | 0.00 | -54026 | 19125 | 68460 | False |
| L6M | ALL | frozen | 4638 | 161426 | 282495 | 155576 | 1.19 | 0.65 | 131616 | 124424 | 315244 | False |
| L6M | ALL | refit2 | 4638 | 228884 | 400547 | 223156 | 1.19 | 0.88 | 138845 | 184937 | 272331 | False |
| L3M | P7|1 | frozen | 196 | 10706 | 18736 | 10443 | 1.18 | 0.73 | 1664 | -17865 | -3691 | True |
| L3M | P7|1 | refit2 | 196 | 9345 | 16354 | 9084 | 1.17 | 0.68 | 2707 | -7554 | 6944 | True |
| L3M | P7|0 | frozen | 342 | 66592 | 116536 | 65311 | 1.22 | 0.77 | 35363 | 10961 | 58894 | True |
| L3M | P7|0 | refit2 | 342 | 22433 | 39258 | 21133 | 1.22 | 0.38 | 34096 | 11029 | 41327 | False |
| L3M | P7|3 | frozen | 66 | 1126 | 1971 | 1073 | 1.12 | 0.44 | 2604 | 2509 | 9574 | False |
| L3M | P7|3 | refit2 | 66 | -4927 | -8621 | -4993 | 1.17 | 0.21 | 2067 | 2369 | 10283 | False |
| L3M | M7|1 | frozen | 307 | -7146 | -12505 | -7516 | 1.23 | 0.29 | -988 | -4684 | 7754 | False |
| L3M | M7|1 | refit2 | 307 | -3556 | -6224 | -3958 | 1.26 | 0.37 | -151 | -2968 | 10807 | False |
| L3M | M7|3 | frozen | 105 | 7097 | 12420 | 7039 | 1.15 | 0.79 | 3009 | 6042 | 11370 | False |
| L3M | M7|3 | refit2 | 105 | 8808 | 15414 | 8737 | 1.19 | 0.81 | 4175 | 5882 | 13327 | False |
| L3M | U7|0 | frozen | 92 | -26816 | -46928 | -26334 | 0.50 | 0.00 | -26816 | 19520 | 40237 | False |
| L3M | U7|0 | refit2 | 92 | -26816 | -46928 | -26334 | 0.50 | 0.00 | -26816 | 22820 | 41144 | False |
| L3M | K7|0 | frozen | 474 | 26896 | 47068 | 26345 | 1.28 | 0.77 | 16152 | 4147 | 10481 | True |
| L3M | K7|0 | refit2 | 474 | 31367 | 54892 | 30885 | 1.25 | 0.89 | 14187 | 13793 | 30260 | True |
| L3M | K7|1 | frozen | 255 | -6138 | -10742 | -6413 | 1.25 | 0.28 | -462 | 1668 | 11910 | False |
| L3M | K7|1 | refit2 | 255 | -13749 | -24061 | -13976 | 1.21 | 0.11 | -1569 | 1753 | 9899 | False |
| L3M | K7|3 | frozen | 96 | -2730 | -4777 | -2752 | 1.06 | 0.32 | -213 | 420 | 4092 | False |
| L3M | K7|3 | refit2 | 96 | -3076 | -5382 | -3101 | 1.07 | 0.31 | -819 | -1038 | 5823 | False |
| L3M | A7|0 | frozen | 218 | -1848 | -3233 | -2043 | 1.25 | 0.36 | 949 | 4162 | 10966 | False |
| L3M | A7|0 | refit2 | 218 | -4279 | -7489 | -4457 | 1.22 | 0.28 | 291 | 4545 | 14815 | False |
| L3M | P7 | frozen | 604 | 60158 | 105276 | 58428 | 1.21 | 0.71 | 34857 | -16266 | 25761 | True |
| L3M | P7 | refit2 | 604 | -5692 | -9961 | -7469 | 1.23 | 0.17 | 33668 | 1965 | 52357 | False |
| L3M | M7 | frozen | 416 | 5110 | 8942 | 4675 | 1.23 | 0.58 | 2126 | -4162 | 6406 | False |
| L3M | M7 | refit2 | 416 | 7015 | 12276 | 6593 | 1.23 | 0.62 | 2957 | 2591 | 12775 | False |
| L3M | U7 | frozen | 155 | -37008 | -64764 | -36214 | 0.50 | 0.00 | -37008 | 31748 | 48847 | False |
| L3M | U7 | refit2 | 155 | -37008 | -64764 | -36214 | 0.50 | 0.00 | -37008 | 22247 | 37800 | False |
| L3M | ALL | frozen | 2414 | 161818 | 283182 | 158314 | 1.21 | 0.96 | 67164 | 72482 | 171656 | False |
| L3M | ALL | refit2 | 2414 | 149337 | 261339 | 145897 | 1.21 | 0.94 | 65309 | 83792 | 172071 | False |


## 7. Part D flow-as-entry shadow books (proxy simulator on 1-s trade prints)

Cells 1800 (event x level x session x bracket x time stop), flow-shift placebos 11/23/37 trading days; bar = 99th percentile |t(real - placebo)| of placebo-vs-placebo contrasts = 1.87; cells with mean>0: 187; clearing bar with mean>0: 4; a cost drag of about -$15 per trade dominates (mean of all cells -15.0).

| ev | fam | sess | cfg | n | mean | tdiff | mean_L6M | n_L6M | mean_L3M | mean_2023 | mean_2024 | mean_2025 | mean_2026 | plc_mean |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E4f | PD | 3 | 40_40_30 | 1132 | 48.82 | 2.12 | -51.22 | 120 | 119 | -1.82 | 92.62 | 29.33 | 64.54 | -24.20 |
| E4t | VW1 | 2 | 40_40_15 | 2705 | 5.42 | 2.00 | -80.41 | 202 | -77.58 | 18.06 | 24.51 | -13.10 | -26.24 | -26.89 |
| E4t | VW1 | 2 | 40_60_15 | 2705 | 8.31 | 1.98 | -62.64 | 202 | -53.16 | 24.88 | 16.15 | -13.00 | -2.08 | -26.44 |
| E4t | PD | 3 | 40_60_15 | 1369 | 17.74 | 1.96 | 120 | 157 | 95.25 | -5.93 | 44.38 | -16.87 | 61.13 | -39.56 |
