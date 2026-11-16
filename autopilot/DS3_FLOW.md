# DS3_FLOW - T-FLOW (order-by-order flow, other markets, score sizing, flow-as-entry), W-FL1

VERDICT (data ends 2026-10-31; FIRST PASS; base JN05W2 provisional, base lots, engine fee $1.18 with $4.84 column, live = x1.75): engine side running (78 FL cell-months done, 22 set x window rows scored); Part D flow-as-entry shadow books: 0 survivors in the first pass (see section 7); Part B other markets: no family beyond the nonsense pass rate at table level; see sections below. No PASS claim.

Basis: exact engine (identity TL3_FL_ID 202610 = 598 trades / 25,943.82), all layers ON as in JN05W2 (ATR-SKIP, P7 blackout and Jn04 stack cap may be missing from the JN05W2 set: all deltas base-relative, provisional). Hook th_flow/fl_hooks.py (keep, size m, target tg, WAIT hold w s). Skip rules read against SKIP_RND (engine random skip, same keep share and scope, PATH_EFFECT_RULE). Size and WAIT are read against their own controls (HALF==X2 after constant-risk normalisation; WAIT against unconditional HOLD of the same length).

## 0. Engine planted-edge and noise checks (L3M, five books U7 P7 O7 M7 A7)

A lead state planted from each signal's own R (P(lead|R>0)=0.65, P(lead|R<=0)=0.35) is recovered by the pipeline: PLANT SKIP +16.4k/wk vs base (DD 43.6k vs 52.2k), PLANT SKIP vs its random skip +21.7k/wk, PLANT X15 +4.1k/wk; a pure-noise state gives SKIP -15.7k/wk (random skip -10.9k, i.e. path-effect spread about +-5k/wk at this keep share) and X15 -0.8k/wk. So a real edge of that size is visible, and a skip result inside +-5k/wk of its random skip is noise. Rows of the sets are in section 1.

## 1. Engine results: Part A lead (c_imb_n5_60_lo) and Part B items, per scope and window

### window L3M

| set | scope | n | d_wk | d_wk175 | d_wk484 | dd | base_dd | d_dd | cn | base_cn | cexp | base_cexp | d_cwk | cdd | base_cdd | wk_noW44 | base_wk_noW44 | dd_noW44 | base_dd_noW44 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TL3_FL_LEADL5_SKIP | L5 | 1453 | -3736 | -6538 | -3440 | 47752 | 52233 | -4481 | 562 | 1104 | 255 | 173 | -3707 | 27355 | 42565 | 17399 | 23989 | 47752 | 43405 |
| TL3_FL_LEADP7_HALF | P7 | 1878 | -1916 | -3352 | -1927 | 55446 | 52233 | 3213 | 471 | 467 | 251 | 253 | 2.72 | 49368 | 39663 | 21803 | 23989 | 48910 | 43405 |
| TL3_FL_LEADP7_SKIP | P7 | 1724 | -3526 | -6171 | -3352 | 58417 | 52233 | 6184 | 264 | 467 | 316 | 253 | -2679 | 28679 | 39663 | 19030 | 23989 | 58417 | 43405 |
| TL3_FL_LEADP7_SKIP_RND | P7 | 1754 | -4398 | -7696 | -4245 | 42529 | 52233 | -9704 | 288 | 467 | 218 | 253 | -4262 | 35082 | 39663 | 16616 | 23989 | 42529 | 43405 |
| TL3_FL_LEADP7_X15 | P7 | 1876 | 681 | 1191 | 656 | 48820 | 52233 | -3413 | 471 | 467 | 274 | 253 | 830 | 42419 | 39663 | 24443 | 23989 | 44956 | 43405 |
| TL3_FL_LEADP7_X2 | P7 | 1878 | -1916 | -3352 | -1927 | 55446 | 52233 | 3213 | 471 | 467 | 251 | 253 | 2.72 | 49368 | 39663 | 21803 | 23989 | 48910 | 43405 |
| TL3_FL_LEADU70_HALF | U70 | 1872 | 36.31 | 63.55 | 37.16 | 56403 | 52233 | 4170 | 72 | 72 | 517 | 602 | -471 | 14280 | 15497 | 24376 | 23989 | 43385 | 43405 |
| TL3_FL_LEADU70_SKIP | U70 | 1839 | -2666 | -4665 | -2630 | 55106 | 52233 | 2873 | 17 | 72 | 1954 | 602 | -778 | 4206 | 15497 | 21440 | 23989 | 48127 | 43405 |
| TL3_FL_LEADU70_SKIP_RND | U70 | 1849 | -6052 | -10590 | -6019 | 60662 | 52233 | 8429 | 17 | 72 | -140 | 602 | -3517 | 19164 | 15497 | 18217 | 23989 | 60662 | 43405 |
| TL3_FL_LEADU70_X15 | U70 | 1875 | 535 | 936 | 530 | 53105 | 52233 | 872 | 72 | 72 | 698 | 602 | 535 | 15479 | 15497 | 24641 | 23989 | 43387 | 43405 |
| TL3_FL_LEADU70_X2 | U70 | 1872 | 36.31 | 63.55 | 37.16 | 56403 | 52233 | 4170 | 72 | 72 | 517 | 602 | -471 | 14280 | 15497 | 24376 | 23989 | 43385 | 43405 |
| TL3_FL_LEADU7_HALF | U7 | 1875 | -657 | -1149 | -655 | 56341 | 52233 | 4107 | 120 | 121 | 500 | 518 | -212 | 14417 | 14457 | 23621 | 23989 | 43828 | 43405 |
| TL3_FL_LEADU7_SKIP | U7 | 1811 | -2964 | -5188 | -2901 | 56937 | 52233 | 4703 | 28 | 121 | 1265 | 518 | -2099 | 4181 | 14457 | 21000 | 23989 | 48183 | 43405 |
| TL3_FL_LEADU7_SKIP_RND | U7 | 1809 | -8859 | -15504 | -8797 | 64768 | 52233 | 12535 | 25 | 121 | -1272 | 518 | -7269 | 35831 | 14457 | 14799 | 23989 | 64768 | 43405 |
| TL3_FL_LEADU7_X15 | U7 | 1877 | 862 | 1509 | 855 | 53105 | 52233 | 872 | 121 | 121 | 624 | 518 | 986 | 15613 | 14457 | 24996 | 23989 | 42280 | 43405 |
| TL3_FL_LEADU7_X2 | U7 | 1875 | -657 | -1149 | -655 | 56341 | 52233 | 4107 | 120 | 121 | 500 | 518 | -212 | 14417 | 14457 | 23621 | 23989 | 43828 | 43405 |
| TL3_FL_NOISEL5_SKIP | L5 | 1691 | -15719 | -27509 | -15584 | 94651 | 52233 | 42418 | 882 | 1104 | 29.24 | 173 | -12728 | 74333 | 42565 | 7155 | 23989 | 94651 | 43405 |
| TL3_FL_NOISEL5_SKIP_RND | L5 | 1682 | -10907 | -19086 | -10764 | 69068 | 52233 | 16835 | 875 | 1104 | 63.51 | 173 | -10436 | 56489 | 42565 | 9390 | 23989 | 69068 | 43405 |
| TL3_FL_NOISEL5_X15 | L5 | 1896 | -793 | -1387 | -797 | 62090 | 52233 | 9857 | 1117 | 1104 | 161 | 173 | -843 | 53134 | 42565 | 23630 | 23989 | 44267 | 43405 |
| TL3_FL_PLANTL5_SKIP | L5 | 1797 | 16370 | 28647 | 16460 | 43563 | 52233 | -8670 | 916 | 1104 | 428 | 173 | 15444 | 34566 | 42565 | 38717 | 23989 | 43563 | 43405 |
| TL3_FL_PLANTL5_SKIP_RND | L5 | 1710 | -5312 | -9296 | -5214 | 49052 | 52233 | -3181 | 914 | 1104 | 150 | 173 | -4198 | 36338 | 42565 | 17600 | 23989 | 49052 | 43405 |
| TL3_FL_PLANTL5_X15 | L5 | 1898 | 4083 | 7146 | 4072 | 53506 | 52233 | 1273 | 1119 | 1104 | 217 | 173 | 3975 | 44550 | 42565 | 28197 | 23989 | 34490 | 43405 |


### 1b. Each set read against its control (random skip / unconditional hold / random ladder / nonsense score / noise)

| set | win | control | d_wk_vs_base | d_wk_vs_control | dd | dd_control | base_dd | cell_exp | cell_exp_control | cell_dd | cell_dd_control |
|---|---|---|---|---|---|---|---|---|---|---|---|
| TL3_FL_LEADP7_SKIP | L3M | SKIP_RND | -3526 | 872 | 58417 | 42529 | 52233 | 316 | 218 | 28679 | 35082 |
| TL3_FL_LEADU70_SKIP | L3M | SKIP_RND | -2666 | 3386 | 55106 | 60662 | 52233 | 1954 | -140 | 4206 | 19164 |
| TL3_FL_LEADU7_SKIP | L3M | SKIP_RND | -2964 | 5895 | 56937 | 64768 | 52233 | 1265 | -1272 | 4181 | 35831 |
| TL3_FL_NOISEL5_SKIP | L3M | SKIP_RND | -15719 | -4813 | 94651 | 69068 | 52233 | 29.24 | 63.51 | 74333 | 56489 |
| TL3_FL_PLANTL5_SKIP | L3M | SKIP_RND | 16370 | 21682 | 43563 | 49052 | 52233 | 428 | 150 | 34566 | 36338 |
| TL3_FL_PLANTL5_SKIP | L3M | NOISE | 16370 | 32089 | 43563 | 94651 | 52233 | 428 | 29.24 | 34566 | 74333 |
| TL3_FL_PLANTL5_SKIP_RND | L3M | NOISE | -5312 | 5595 | 49052 | 69068 | 52233 | 150 | 63.51 | 36338 | 56489 |
| TL3_FL_PLANTL5_X15 | L3M | NOISE | 4083 | 4876 | 53506 | 62090 | 52233 | 217 | 161 | 44550 | 53134 |


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
| L6M | U7|0 | frozen | 175 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 | 11556 | 36260 | False |
| L6M | U7|0 | refit2 | 175 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 | 14609 | 41832 | False |
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
| L6M | U7 | frozen | 298 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 | 37005 | 70423 | False |
| L6M | U7 | refit2 | 298 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 | 19125 | 68460 | False |
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
| L3M | U7|0 | frozen | 92 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 | 19520 | 40237 | False |
| L3M | U7|0 | refit2 | 92 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 | 22820 | 41144 | False |
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
| L3M | U7 | frozen | 155 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 | 31748 | 48847 | False |
| L3M | U7 | refit2 | 155 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 | 22247 | 37800 | False |
| L3M | ALL | frozen | 2414 | 161818 | 283182 | 158314 | 1.21 | 0.96 | 67164 | 72482 | 171656 | False |
| L3M | ALL | refit2 | 2414 | 149337 | 261339 | 145897 | 1.21 | 0.94 | 65309 | 83792 | 172071 | False |


## 3. Part B other markets as a condition (table level, then engine)

screen_B: 4779 column x cell tests on taken trades; clearing the cell nonsense bar (99th pct |t| of 200 nonsense columns, day-clustered): 149 = 3.1 % (nonsense hold-out rate 4.2 % at |t|>2). Planted-edge check passed first (planted t 33.6 clears, noise -1.2 does not).
| cell | cond | n_yes | liftR | tR | lift_usd | lift_L6M | lift_y2023 | lift_y2024 | lift_y2025 | lift_y2026 |
|---|---|---|---|---|---|---|---|---|---|---|
| book:P7 | B_lead_6E_r1_bps_s__lo | 1030 | -0.10 | -3.78 | -493 | -577 | -27.89 | -803 | -405 | -528 |
| bs:M7_1 | B_lead_ZN_r60_bps_s__hi | 515 | 0.16 | 3.76 | 252 | 111 | 546 | 349 | 195 | 159 |
| bs:M7_1 | B_lead_ZN_z60_s__hi | 581 | 0.15 | 3.65 | 231 | 51.79 | 443 | 307 | 238 | 111 |
| bs:M7_1 | B_lead_ZN_r5_bps_s__hi | 600 | 0.13 | 3.55 | 203 | 160 | 509 | 4.74 | 265 | 180 |
| bs:P7_1 | B_nqes_nq_leads15 | 915 | -0.13 | -3.33 | -351 | -342 | -406 | -618 | -173 | -355 |
| book:M7 | B_lead_ZN_r60_bps_s__hi | 962 | 0.10 | 3.29 | 158 | 66.98 | 189 | 179 | 109 | 172 |
| bs:M7_1 | B_lead_ZB_z60_s__hi | 566 | 0.13 | 3.26 | 226 | 180 | 289 | 305 | 195 | 187 |
| bs:M7_1 | B_lead_ZB_r60_bps_s__hi | 501 | 0.13 | 3.13 | 217 | 244 | 383 | 291 | 144 | 190 |

screen_B2: 486 column x cell tests on taken trades; clearing the cell nonsense bar (99th pct |t| of 200 nonsense columns, day-clustered): 10 = 2.1 % (nonsense hold-out rate 4.2 % at |t|>2). Planted-edge check passed first (planted t 33.6 clears, noise -1.2 does not).
| cell | cond | n_yes | liftR | tR | lift_usd | lift_L6M | lift_y2023 | lift_y2024 | lift_y2025 | lift_y2026 |
|---|---|---|---|---|---|---|---|---|---|---|
| bs:K7_4 | B2_fcpa_60__lo | 226 | -0.18 | -3.05 | -244 | -352 | -452 | -322 | -183 | -102 |
| sess:4 | B2_fcpa_60__lo | 226 | -0.18 | -3.05 | -244 | -352 | -452 | -322 | -183 | -102 |
| sess:3 | B2_fct15_with | 2868 | 0.07 | 2.42 | 97.39 | 223 | 21.72 | 86.23 | 31.83 | 266 |
| bs:K7_4 | B2_fct15_against | 337 | -0.12 | -2.37 | -149 | -587 | -156 | -162 | -123 | -170 |
| sess:4 | B2_fct15_against | 337 | -0.12 | -2.37 | -149 | -587 | -156 | -162 | -123 | -170 |
| bs:K7_3 | B2_fca_5__lo | 390 | -0.11 | -2.23 | -127 | -28.70 | -318 | -121 | -74.81 | -6.55 |


## 4. Part A order-by-order library

W-CF2 builds the library (kernel over 1,126 MBO days running, planted-edge check and shift-placebo scoring next; columns with _d0/_d1/_d2/_d5 latency and _d30/_d60/_d120 wait variants). Until its first scored files exist, the engine side runs the existing lead c_imb_n5_60_lo (L3_LEAD_TABLE) in all actions; every further item goes through fl_lib.actions() (SKIP, SKIP_RND, HALF, X15, WAIT, latency) as soon as it lands.


## 7. Part D flow-as-entry shadow books (proxy simulator on 1-s trade prints)

Cells 2394 (event x level x session x bracket x time stop), flow-shift placebos 11/23/37 trading days; bar = 99th percentile |t(real - placebo)| of placebo-vs-placebo contrasts = 2.07; cells with mean>0: 341; clearing bar with mean>0: 7; a cost drag of about -$15 per trade dominates (mean of all cells -13.9).

| ev | fam | sess | cfg | n | mean | tdiff | mean_L6M | n_L6M | mean_L3M | mean_2023 | mean_2024 | mean_2025 | mean_2026 | plc_mean |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E3 | PD | 1 | 40_40_5 | 352 | 2.80 | 2.59 | -28.63 | 33 | 19.71 | nan | -24.87 | 52.96 | 11.30 | -55.87 |
| E3 | PD | 1 | 40_60_5 | 352 | 2.25 | 2.50 | -28.93 | 33 | 19.71 | nan | -24.87 | 51.11 | 11.12 | -55.96 |
| E3 | PD | 1 | 58_60_5 | 352 | 2.23 | 2.48 | -28.93 | 33 | 19.71 | nan | -24.87 | 51.06 | 11.12 | -54.44 |
| E3 | PD | 1 | 40_60_15 | 352 | 8.36 | 2.19 | 106 | 33 | 56.98 | nan | -50.64 | 22.71 | 180 | -79.57 |
| E3 | PD | 1 | 40_40_15 | 352 | 6.50 | 2.14 | 65.77 | 33 | 46.07 | nan | -52.13 | 38.76 | 145 | -77.49 |
| E4f | PD | 3 | 40_40_30 | 1132 | 48.82 | 2.12 | -51.22 | 120 | 119 | -1.82 | 92.62 | 29.33 | 64.54 | -24.20 |
| E3 | SESS | -1 | 40_60_30 | 4489 | 17.94 | 2.08 | 66.54 | 389 | 89.34 | 29.55 | 12.37 | 17.77 | 28.24 | -13.80 |


### 7b. Auto-expansion of the one family with a consistent sign (E3)

E3 (liquidity pull ahead of price, trade WITH the move) neighbourhood grid: 2160 cells, bar 2.56 (99th pct |t| of placebo-vs-placebo contrasts); clearing with mean>0: 3.

| fam | W | ccm | rt | mv | cfg | n | mean | tdiff | mean_L6M | n_L6M | mean_L3M | m2023 | m2024 | m2025 | m2026 | plc_mean |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SESS | 15 | 200 | 1.30 | 1.50 | with_40_60_120 | 4451 | 43.39 | 2.84 | 102 | 389 | 117 | 57.49 | 21.20 | 59.52 | 62.76 | -42.61 |
| SESS | 15 | 200 | 1.30 | 1.00 | with_40_60_120 | 4492 | 42.53 | 2.84 | 101 | 392 | 112 | 58.35 | 21.52 | 57.79 | 59.66 | -39.92 |
| SESS | 30 | 200 | 1.30 | 1.50 | with_40_60_15 | 877 | 22.17 | 2.71 | 102 | 12 | nan | nan | 31.32 | 10.13 | 42.66 | -39.32 |


Stack interplay (E3 SESS W15 ccm200 rt1.3, with, 40/60, 2 h time stop; 1/2/5 lots; D7 = engine JN05W2 base lots x1.75; overlap = entry inside an open D7 position):
```
E3 shadow e3x SESS W15 ccm200 rt1.3 mv1.0 with_40_60_120: n 4492; entry inside an open D7 position 0.90 (same side 0.75); events/day 6.15
FULL L=1: E3 total $191,064 ($1,034/wk), E3 alone DD $70,996; D7 x1.75 total $3,666,695 DD $161,424 worst week $-120,656; combined total $3,857,759 DD $167,007 worst week $-122,151; daily corr 0.195
FULL L=2: E3 total $382,127 ($2,068/wk), E3 alone DD $141,992; D7 x1.75 total $3,666,695 DD $161,424 worst week $-120,656; combined total $4,048,823 DD $172,590 worst week $-123,646; daily corr 0.195
FULL L=5: E3 total $955,319 ($5,169/wk), E3 alone DD $354,980; D7 x1.75 total $3,666,695 DD $161,424 worst week $-120,656; combined total $4,622,014 DD $275,620 worst week $-128,130; daily corr 0.195
L6M L=1: E3 total $39,448 ($1,494/wk), E3 alone DD $14,839; D7 x1.75 total $1,156,228 DD $91,408 worst week $-63,648; combined total $1,195,676 DD $89,867 worst week $-62,492; daily corr 0.199
L6M L=2: E3 total $78,895 ($2,988/wk), E3 alone DD $29,678; D7 x1.75 total $1,156,228 DD $91,408 worst week $-63,648; combined total $1,235,123 DD $88,325 worst week $-61,336; daily corr 0.199
L6M L=5: E3 total $197,239 ($7,471/wk), E3 alone DD $74,194; D7 x1.75 total $1,156,228 DD $91,408 worst week $-63,648; combined total $1,353,467 DD $101,849 worst week $-84,530; daily corr 0.199
L3M L=1: E3 total $20,710 ($1,569/wk), E3 alone DD $11,522; D7 x1.75 total $440,131 DD $91,408 worst week $-63,648; combined total $460,840 DD $89,867 worst week $-62,492; daily corr 0.230
L3M L=2: E3 total $41,419 ($3,138/wk), E3 alone DD $23,044; D7 x1.75 total $440,131 DD $91,408 worst week $-63,648; combined total $481,550 DD $88,325 worst week $-61,336; daily corr 0.230
L3M L=5: E3 total $103,548 ($7,845/wk), E3 alone DD $57,609; D7 x1.75 total $440,131 DD $91,408 worst week $-63,648; combined total $543,679 DD $101,849 worst week $-84,530; daily corr 0.230
```


## 8. Survivors and what D7 needs (shadow books only)

None registered yet. Computability per item: (a) L3 add-count imbalance (c_imb_n5_60_lo) and E3 cancel-volume-ahead need order-by-order data: NOT computable by D7 from NT8/CQG L2 today; needs the live L3 (CME MBO) feed plus a sidecar on the VPS (cost quote in DS3_CONFLUENCE_L3_QUOTES.md). (b) ES RTY YM ZN ZB 6E return leaders, NQ-minus-ES gap and the multi-market forecast tercile: 1-minute bars from feeds D7 already has (NT8/CQG; YM may need a subscription); GC, CL and agree_all7 need new COMEX/NYMEX data; the ridge forecast is a 90-coefficient formula D7 can compute, GBM/MLP versions need packaged models (DS3_FLOW_LEADERS.md). (c) WAIT needs only the entry-timing hook (hold w seconds, then the full native try_entry).


## 9. Notes
- Constant-risk normalisation makes HALF and X2 identical (same 2:1 ratio); X2 sets dropped. - A bare hold of P7 signals changes 202610 from 598 trades (P7 -16.8k) to 655 trades (P7 +0.9k): every WAIT is read against the unconditional hold (HOLD sets). - Part D proxy simulator uses 1-s trade prints (hi/lo/first/last), 1-tick slippage each side, stop-first, entry at the first print of second t+1 (1 s latency), $4.84 per lot; the engine injection step runs only for survivors. - cf_hooks sets cf_m/cf_found on every call (W-CF3 caveat); fl_hooks does not.
