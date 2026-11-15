# DS3_CONFLUENCE_ITEMS_CF5_ZW - Block 3 and Addendum-6 CF5 conditions each alone, cluster-robust (zw) with the nonsense bar

RULE (W-CF1, CONFLUENCE_DEFS.md): pass alone only if |zw| (weekly cluster-robust t, >= 8 weeks) exceeds the 99th percentile of |zw| of the 200 nonsense controls c_Z_* IN THE SAME CELL, AND the lift keeps its sign in every calendar year with >= 30 cases per side (>= 2 such years) AND in L6M (>= 15 yes cases). Outcome = R of the universe signals with in_pos == 0 (99,166 signals, taken + skipped hypothetical), cells ALL, book, session, book x session. Universe ends 2026-10-30 (November rows come when W-CF1 finishes the extension).

**Verdict line (2026-11-15 17:53Z): A named systems: 0.84% of tests (1.8x nonsense); B Dalton / Crabel / AC: 1.03% of tests (2.2x nonsense); B2 session-anchored op: 0.90% of tests (1.9x nonsense); C1 execution levels, s: 0.92% of tests (2.0x nonsense); C2 order-flow measures: 1.09% of tests (2.3x nonsense); D RV/IV, VIX term, dis: 0.98% of tests (2.1x nonsense); Block 7 time-of-day li: 0.07% of tests (0.2x nonsense); Block 8 opening prices: 0.82% of tests (1.7x nonsense); Block 9 week / session: 0.88% of tests (1.9x nonsense); Block 13 microstructur: 0.60% of tests (1.3x nonsense); Block 16 flow calendar: 0.37% of tests (0.8x nonsense). Passing alone is not an edge claim: the stack-level controls (W-CF3) still apply.**
## A named systems (DeMark, Raschke, Connors, Chande, Wilder, Kase, Ehlers, Brooks, stats)

4040 conditions, 206040 (condition x cell) tests; passing alone: 1739 tests, 1161 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.84% of tests (1.8x the nonsense rate, 29% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 161, book 417, book_sess 765, sess 396.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book | P7 |  | n_cn_rsi_pb_fast_60m_against10 | 2709 | 0.10 | -0.110 | 0.029 | -0.139 | -5.8 | 2.2 | 157 | 0/4 | -0.030 |
| sess |  | 0 | n_rk_grail_std_60m_against10 | 3012 | 0.11 | -0.088 | 0.072 | -0.160 | -5.8 | 2.3 | 142 | 0/4 | -0.290 |
| ALL |  |  | n_dm_combo13_60m_with10 | 298 | 0.00 | -0.327 | 0.023 | -0.350 | -5.4 | 2.2 | 19 | 0/4 | -0.470 |
| ALL |  |  | n_dm_combo_60m_with_ge13 | 820 | 0.01 | -0.145 | 0.023 | -0.168 | -5.2 | 2.2 | 19 | 0/4 | -0.373 |
| book_sess | H7 | 1 | n_wl_volstop_dist_fast_15m_eagainst | 106 | 0.12 | 0.203 | 0.028 | 0.174 | 5.1 | 2.7 | 21 | 2/2 | 0.192 |
| sess |  | 4 | n_st_zma200_60m_eleave | 1552 | 0.08 | -0.237 | 0.019 | -0.256 | -5.1 | 2.4 | 107 | 0/4 | -0.320 |
| book | A7 |  | n_rk_grail_std_60m_against10 | 1835 | 0.11 | -0.089 | 0.032 | -0.122 | -5.0 | 2.4 | 137 | 0/4 | -0.164 |
| sess |  | 0 | n_rk_grail_std_60m_against_state | 5585 | 0.20 | -0.021 | 0.074 | -0.095 | -5.0 | 2.3 | 161 | 0/4 | -0.052 |
| ALL |  |  | n_rk_grail_std_60m_with3 | 5384 | 0.05 | -0.053 | 0.026 | -0.079 | -4.9 | 2.2 | 143 | 0/4 | -0.176 |
| book | M7 |  | n_st_nqlag_es30_5m_fresh5 | 12143 | 0.36 | -0.004 | 0.044 | -0.048 | -4.8 | 2.1 | 187 | 0/4 | -0.060 |
| ALL |  |  | n_eh_roof_slow_60m_divwith | 16399 | 0.17 | -0.038 | 0.034 | -0.072 | -4.8 | 2.2 | 185 | 0/4 | -0.129 |
| ALL |  |  | n_wl_volstop_flip_slow_60m_against10 | 15965 | 0.16 | -0.017 | 0.029 | -0.046 | -4.7 | 2.2 | 186 | 0/4 | -0.054 |
| sess |  | 0 | n_rk_grail_slow_60m_against_state | 3637 | 0.13 | -0.009 | 0.064 | -0.073 | -4.7 | 2.3 | 136 | 0/4 | -0.066 |
| book_sess | A7 | 4 | n_rk_310_std_60m_divwith | 702 | 0.18 | -0.234 | 0.044 | -0.278 | -4.7 | 2.4 | 90 | 0/4 | -0.376 |
| book_sess | M7 | 1 | n_ks_peak8_1m_eleave | 133 | 0.04 | 0.290 | -0.003 | 0.292 | 4.7 | 2.8 | 31 | 3/3 | 0.437 |
| sess |  | 3 | n_wl_volstop_dist_fast_60m_fresh5 | 4529 | 0.26 | -0.052 | 0.045 | -0.097 | -4.7 | 2.1 | 180 | 0/4 | -0.077 |
| book | K7 |  | n_bk_dojis5_1d_hi_z1 | 167 | 0.01 | 0.145 | 0.007 | 0.138 | 4.6 | 2.7 | 9 | 3/3 | 0.155 |
| ALL |  |  | n_rk_soup_std_60m_with3 | 4934 | 0.05 | -0.066 | 0.026 | -0.092 | -4.6 | 2.2 | 173 | 0/4 | -0.177 |
| ALL |  |  | n_rk_grail_slow_60m_against_state | 12746 | 0.13 | -0.011 | 0.027 | -0.038 | -4.6 | 2.2 | 151 | 0/4 | -0.033 |
| book_sess | P7 | 0 | n_rk_grail_std_60m_against10 | 575 | 0.13 | -0.208 | 0.110 | -0.318 | -4.6 | 3.0 | 104 | 0/4 | -0.580 |
| ALL |  |  | n_rk_grail_std_60m_against10 | 11588 | 0.12 | -0.044 | 0.030 | -0.075 | -4.5 | 2.2 | 166 | 0/4 | -0.082 |
| sess |  | 0 | n_dm_cd13u_15m_state | 1980 | 0.07 | -0.047 | 0.062 | -0.109 | -4.5 | 2.3 | 136 | 0/4 | -0.141 |
| book | M7 |  | n_st_nqlag_es30_5m_side | 13860 | 0.42 | 0.001 | 0.045 | -0.043 | -4.5 | 2.1 | 187 | 0/4 | -0.061 |
| book | K7 |  | n_dm_combo_60m_with_ge13 | 155 | 0.01 | -0.142 | 0.010 | -0.152 | -4.5 | 2.7 | 19 | 0/2 | -0.257 |
| book | M7 |  | n_wl_volstop_flip_slow_60m_against10 | 5498 | 0.16 | -0.012 | 0.035 | -0.047 | -4.5 | 2.1 | 185 | 0/4 | -0.102 |

## B Dalton / Crabel / ACD / Williams

124 conditions, 6324 (condition x cell) tests; passing alone: 65 tests, 33 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 1.03% of tests (2.2x the nonsense rate, 27% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 9, book 17, book_sess 27, sess 12.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | n_wl_oops_with | 4551 | 0.11 | -0.100 | 0.017 | -0.116 | -6.7 | 2.2 | 140 | 0/4 | -0.215 |
| book_sess | U7 | 1 | n_dl_inside_va | 290 | 0.42 | 0.160 | -0.042 | 0.202 | 4.4 | 2.3 | 46 | 4/4 | 0.286 |
| sess |  | 5 | n_fa_c_fast_with | 2189 | 0.30 | -0.147 | 0.027 | -0.173 | -4.2 | 2.7 | 153 | 0/4 | -0.257 |
| book | M7 |  | n_wl_oops_with | 1150 | 0.11 | -0.090 | 0.014 | -0.104 | -4.0 | 2.1 | 118 | 0/4 | -0.206 |
| sess |  | 3 | n_cb_prior_wide | 2476 | 0.14 | -0.102 | 0.040 | -0.142 | -3.9 | 2.1 | 84 | 0/4 | -0.017 |
| book | A7 |  | n_wl_smash_against | 4636 | 0.27 | -0.044 | 0.043 | -0.086 | -3.8 | 2.4 | 182 | 0/4 | -0.119 |
| book_sess | K7 | 3 | n_dl_pd_neutral_ext | 216 | 0.06 | 0.241 | -0.014 | 0.255 | 3.7 | 2.4 | 46 | 4/4 | 0.321 |
| book | A7 |  | n_dl_pd_neutral | 2138 | 0.12 | 0.174 | -0.003 | 0.176 | 3.6 | 2.4 | 82 | 4/4 | 0.101 |
| ALL |  |  | n_fa_c_std_with | 3970 | 0.10 | -0.079 | 0.007 | -0.087 | -3.6 | 2.2 | 123 | 0/4 | -0.119 |
| book_sess | K7 | 3 | n_dl_pd_trend_with | 112 | 0.03 | -0.358 | 0.015 | -0.373 | -3.6 | 2.4 | 31 | 0/2 | -0.561 |
| book_sess | A7 | 4 | n_wl_gap_against | 611 | 0.15 | -0.209 | 0.034 | -0.243 | -3.6 | 2.4 | 79 | 0/4 | -0.359 |
| book_sess | A7 | 4 | n_wl_oops_with | 435 | 0.11 | -0.304 | 0.033 | -0.338 | -3.5 | 2.4 | 63 | 0/4 | -0.486 |
| sess |  | 4 | n_dl_va_wide | 2525 | 0.13 | -0.075 | 0.009 | -0.084 | -3.5 | 2.4 | 95 | 0/4 | -0.181 |
| book_sess | K7 | 3 | n_dl_excess_support_with | 2370 | 0.70 | -0.035 | 0.089 | -0.123 | -3.4 | 2.4 | 163 | 0/4 | -0.195 |
| book | K7 |  | n_wl_oops_with | 663 | 0.09 | -0.108 | 0.010 | -0.118 | -3.4 | 2.7 | 108 | 0/4 | -0.264 |
| book | H7 |  | n_cb_prior_narrow | 406 | 0.13 | 0.165 | 0.028 | 0.137 | 3.4 | 2.2 | 66 | 4/4 | 0.147 |
| book_sess | K7 | 3 | n_dl_pd_neutral | 381 | 0.11 | 0.158 | -0.018 | 0.176 | 3.4 | 2.4 | 74 | 4/4 | 0.160 |
| sess |  | 3 | n_dl_pd_neutral_ext | 1058 | 0.06 | 0.224 | 0.006 | 0.218 | 3.4 | 2.1 | 49 | 4/4 | 0.175 |
| sess |  | 4 | n_dl_r80_active_with | 938 | 0.05 | -0.206 | 0.010 | -0.216 | -3.3 | 2.4 | 85 | 0/4 | -0.078 |
| book_sess | A7 | 3 | n_cb_prior_wide | 450 | 0.12 | -0.232 | 0.067 | -0.299 | -3.3 | 2.6 | 63 | 0/4 | -0.073 |
| sess |  | 3 | n_dl_pd_neutral | 1887 | 0.11 | 0.155 | 0.003 | 0.152 | 3.3 | 2.1 | 81 | 4/4 | 0.075 |
| sess |  | 4 | n_dl_pd_trend_with | 574 | 0.03 | -0.100 | 0.001 | -0.101 | -3.3 | 2.4 | 46 | 0/4 | -0.302 |
| book | A7 |  | n_cb_prior_wide | 2343 | 0.14 | -0.112 | 0.040 | -0.153 | -3.3 | 2.4 | 87 | 0/4 | -0.054 |
| sess |  | 4 | n_dl_va_narrow | 205 | 0.01 | 0.188 | -0.004 | 0.191 | 3.3 | 2.4 | 8 | 2/2 | 0.112 |
| book_sess | P7 | 3 | n_dl_pd_neutral_ext | 305 | 0.06 | 0.135 | -0.005 | 0.140 | 3.3 | 2.9 | 44 | 4/4 | 0.100 |

## B2 session-anchored opening-range systems

48 conditions, 2448 (condition x cell) tests; passing alone: 22 tests, 15 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.90% of tests (1.9x the nonsense rate, 31% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 1, book 3, book_sess 14, sess 4.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | M7 | 2 | n_ss_inor_std | 511 | 0.53 | 0.033 | -0.035 | 0.068 | 3.7 | 2.4 | 67 | 4/4 | 0.094 |
| book_sess | M7 | 2 | n_ss_orb15_beyond | 445 | 0.47 | -0.035 | 0.033 | -0.068 | -3.7 | 2.4 | 67 | 0/4 | -0.094 |
| book_sess | P7 | 2 | n_ss_orb5_fresh15 | 157 | 0.11 | -0.124 | 0.039 | -0.164 | -3.3 | 2.4 | 35 | 0/3 | -0.216 |
| book_sess | K7 | 4 | n_ss_inor_std | 522 | 0.22 | 0.074 | -0.038 | 0.112 | 3.0 | 2.5 | 107 | 4/4 | 0.078 |
| book_sess | P7 | 2 | n_ss_a_fast_hit_with | 988 | 0.68 | -0.058 | 0.189 | -0.247 | -2.9 | 2.4 | 80 | 0/4 | -0.273 |
| sess |  | 0 | n_ss_gap_against | 9525 | 0.37 | 0.028 | 0.076 | -0.048 | -2.9 | 2.3 | 187 | 0/4 | -0.092 |
| book_sess | H7 | 1 | n_ss_a_std_fresh30 | 132 | 0.15 | -0.299 | 0.111 | -0.410 | -2.9 | 2.7 | 29 | 0/3 | -0.370 |
| book_sess | K7 | 2 | n_ss_orb15_fresh15 | 237 | 0.38 | 0.100 | -0.052 | 0.152 | 2.8 | 2.3 | 48 | 3/3 | 0.068 |
| book_sess | U7 | 3 | n_ss_a_fast_now_with | 384 | 0.70 | 0.004 | 0.235 | -0.231 | -2.8 | 2.7 | 21 | 0/4 | -0.505 |
| sess |  | 2 | n_ss_range_used_gt150 | 876 | 0.19 | -0.180 | 0.032 | -0.212 | -2.7 | 2.7 | 92 | 0/4 | -0.358 |
| sess |  | 4 | n_ss_inor_slow | 4392 | 0.27 | 0.043 | -0.024 | 0.067 | 2.7 | 2.4 | 185 | 4/4 | 0.020 |
| book_sess | A7 | 5 | n_ss_orb15_beyond | 1140 | 0.86 | 0.034 | -0.189 | 0.223 | 2.7 | 2.5 | 48 | 3/3 | 0.323 |
| book_sess | M7 | 4 | n_ss_inor_slow | 976 | 0.22 | 0.112 | -0.027 | 0.139 | 2.6 | 2.6 | 149 | 4/4 | 0.234 |
| book_sess | M7 | 4 | n_ss_orb30_beyond | 3402 | 0.77 | -0.028 | 0.110 | -0.138 | -2.6 | 2.6 | 151 | 0/4 | -0.247 |
| book_sess | P7 | 2 | n_ss_orb5_beyond | 834 | 0.57 | -0.029 | 0.089 | -0.118 | -2.6 | 2.4 | 96 | 0/4 | -0.075 |
| book_sess | K7 | 4 | n_ss_orb30_failed | 130 | 0.06 | 0.117 | -0.026 | 0.144 | 2.5 | 2.5 | 30 | 2/2 | 0.306 |
| book_sess | P7 | 5 | n_ss_inor_std | 1794 | 0.43 | -0.058 | 0.040 | -0.097 | -2.5 | 2.5 | 183 | 0/4 | -0.206 |
| sess |  | 4 | n_ss_orb30_beyond | 11466 | 0.71 | -0.025 | 0.042 | -0.068 | -2.5 | 2.4 | 187 | 0/4 | -0.041 |
| book | P7 |  | n_ss_a_fast_hit_with | 19883 | 0.77 | -0.003 | 0.072 | -0.075 | -2.5 | 2.2 | 187 | 0/4 | -0.077 |
| book | H7 |  | n_ss_a_std_fresh30 | 854 | 0.31 | -0.026 | 0.074 | -0.100 | -2.3 | 2.2 | 177 | 0/4 | -0.076 |
| ALL |  |  | n_ss_nr7 | 12128 | 0.13 | -0.014 | 0.028 | -0.041 | -2.3 | 2.2 | 169 | 0/4 | -0.062 |
| book | P7 |  | n_ss_orb15_failed | 2918 | 0.12 | -0.049 | 0.021 | -0.070 | -2.2 | 2.2 | 187 | 0/4 | -0.024 |

## C1 execution levels, seasonality, volume curve

34 conditions, 1734 (condition x cell) tests; passing alone: 16 tests, 10 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.92% of tests (2.0x the nonsense rate, 29% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 1, book 4, book_sess 10, sess 1.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | K7 | 2 | n_ex_mv_pullback_hold | 641 | 0.71 | -0.079 | 0.187 | -0.265 | -2.8 | 2.3 | 59 | 0/3 | -0.528 |
| book_sess | K7 | 0 | n_ex_mv_with_large | 1212 | 0.38 | 0.103 | 0.008 | 0.096 | 2.8 | 2.3 | 172 | 4/4 | 0.019 |
| book_sess | K7 | 0 | n_ex_mv_pullback_hold | 1212 | 0.38 | 0.103 | 0.008 | 0.096 | 2.8 | 2.3 | 172 | 4/4 | 0.019 |
| book_sess | M7 | 4 | n_ex_seas30_strong_against | 807 | 0.16 | 0.105 | -0.013 | 0.118 | 2.8 | 2.6 | 143 | 4/4 | 0.102 |
| book_sess | K7 | 2 | n_ex_mv_with_large | 643 | 0.72 | -0.075 | 0.180 | -0.256 | -2.7 | 2.3 | 58 | 0/3 | -0.528 |
| book | A7 |  | n_ex_seas120_strong_with | 2430 | 0.15 | -0.036 | 0.027 | -0.063 | -2.7 | 2.4 | 179 | 0/4 | -0.042 |
| book | M7 |  | n_ex_seas30_strong_with | 5433 | 0.16 | -0.004 | 0.033 | -0.037 | -2.6 | 2.1 | 187 | 0/4 | -0.132 |
| book_sess | A7 | 2 | n_ex_seas120_strong_with | 154 | 0.13 | -0.325 | -0.018 | -0.306 | -2.5 | 2.5 | 25 | 0/3 | -0.441 |
| book | M7 |  | n_ex_volcurve_ahead_move_with | 8552 | 0.26 | 0.007 | 0.034 | -0.026 | -2.5 | 2.1 | 173 | 0/4 | -0.031 |
| book_sess | K7 | 2 | n_ex_mv_with | 737 | 0.82 | -0.035 | 0.145 | -0.181 | -2.4 | 2.3 | 46 | 0/3 | -0.268 |
| book_sess | P7 | 2 | n_ex_ss_vwap_side | 1265 | 0.91 | 0.030 | -0.064 | 0.094 | 2.4 | 2.4 | 36 | 2/2 | 0.004 |
| book_sess | K7 | 0 | n_ex_mv_with | 2282 | 0.72 | 0.066 | -0.011 | 0.077 | 2.4 | 2.3 | 159 | 4/4 | 0.042 |
| book_sess | K7 | 0 | n_ex_mv_large2 | 1392 | 0.44 | 0.093 | 0.006 | 0.088 | 2.4 | 2.3 | 175 | 4/4 | 0.045 |
| sess |  | 3 | n_ex_seas120_strong_with | 2244 | 0.13 | -0.029 | 0.027 | -0.056 | -2.3 | 2.1 | 161 | 0/4 | -0.046 |
| book | M7 |  | n_ex_volcurve_ahead | 8944 | 0.27 | 0.010 | 0.033 | -0.024 | -2.3 | 2.1 | 173 | 0/4 | -0.027 |
| ALL |  |  | n_ex_seas30_strong_with | 15777 | 0.16 | 0.001 | 0.026 | -0.025 | -2.2 | 2.2 | 187 | 0/4 | -0.051 |

## C2 order-flow measures

72 conditions, 3672 (condition x cell) tests; passing alone: 40 tests, 28 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 1.09% of tests (2.3x the nonsense rate, 39% of its conditions pass in at least one cell).

Passing tests by cell type: book 10, book_sess 22, sess 8.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | A7 | 3 | n_fl_mic5s_with | 1742 | 0.48 | 0.088 | -0.024 | 0.112 | 3.5 | 2.6 | 183 | 4/4 | 0.243 |
| book | A7 |  | n_fl_bimb160s_strong | 832 | 0.05 | 0.122 | 0.014 | 0.108 | 3.4 | 2.4 | 170 | 4/4 | 0.041 |
| book_sess | A7 | 1 | n_fl_mic300s_with | 2957 | 0.54 | 0.079 | -0.005 | 0.084 | 3.4 | 2.9 | 181 | 4/4 | 0.207 |
| book_sess | A7 | 1 | n_fl_bigshare300_up | 1673 | 0.32 | 0.094 | 0.025 | 0.068 | 3.3 | 2.9 | 178 | 4/4 | 0.130 |
| book_sess | A7 | 5 | n_fl_ofi1s_z1 | 147 | 0.09 | -0.196 | -0.011 | -0.185 | -3.3 | 2.5 | 38 | 0/4 | -0.300 |
| book_sess | K7 | 5 | n_fl_bimb515s_with | 1023 | 0.52 | -0.059 | 0.021 | -0.080 | -3.2 | 2.6 | 152 | 0/4 | -0.155 |
| book_sess | P7 | 5 | n_fl_ofi15s_z2 | 277 | 0.06 | -0.091 | 0.005 | -0.097 | -3.1 | 2.5 | 81 | 0/4 | -0.123 |
| book_sess | K7 | 3 | n_fl_bimb5300s_with | 1747 | 0.52 | -0.047 | 0.055 | -0.103 | -3.0 | 2.4 | 180 | 0/4 | -0.044 |
| book_sess | K7 | 1 | n_fl_mic60s_with | 1283 | 0.48 | -0.036 | 0.055 | -0.092 | -3.0 | 2.5 | 133 | 0/4 | -0.000 |
| sess |  | 3 | n_fl_bimb51s_with | 7826 | 0.46 | -0.007 | 0.041 | -0.048 | -3.0 | 2.1 | 186 | 0/4 | -0.005 |
| book_sess | K7 | 3 | n_fl_bimb1060s_with | 1572 | 0.47 | -0.054 | 0.051 | -0.106 | -3.0 | 2.4 | 178 | 0/4 | -0.116 |
| book | U7 |  | n_fl_bimb5300s_with | 1403 | 0.56 | -0.001 | 0.105 | -0.106 | -3.0 | 2.5 | 182 | 0/4 | -0.022 |
| book | A7 |  | n_fl_ofi300s_with | 12428 | 0.73 | 0.006 | 0.054 | -0.048 | -2.9 | 2.4 | 187 | 0/4 | -0.131 |
| book_sess | A7 | 1 | n_fl_bimb515s_strong | 163 | 0.03 | 0.254 | 0.034 | 0.219 | 2.9 | 2.9 | 41 | 3/3 | 0.276 |
| sess |  | 1 | n_fl_bigshare300_up | 4630 | 0.28 | 0.054 | 0.012 | 0.042 | 2.9 | 2.5 | 186 | 4/4 | 0.049 |
| book_sess | U7 | 3 | n_fl_qtr60_hi | 127 | 0.23 | 0.012 | 0.084 | -0.072 | -2.8 | 2.7 | 13 | 0/2 | -0.385 |
| book | K7 |  | n_fl_mic15s_with | 6813 | 0.50 | -0.009 | 0.028 | -0.038 | -2.8 | 2.7 | 187 | 0/4 | -0.011 |
| book_sess | A7 | 3 | n_fl_ofi300s_z2 | 464 | 0.13 | -0.066 | 0.044 | -0.111 | -2.7 | 2.6 | 124 | 0/4 | -0.308 |
| sess |  | 5 | n_fl_mic15s_with | 6091 | 0.49 | -0.027 | 0.020 | -0.047 | -2.7 | 2.7 | 187 | 0/4 | -0.074 |
| book_sess | A7 | 3 | n_fl_qtr60_lo | 580 | 0.16 | -0.091 | 0.053 | -0.144 | -2.7 | 2.6 | 143 | 0/4 | -0.215 |
| book_sess | K7 | 1 | n_fl_ofi15s_z2 | 215 | 0.08 | 0.180 | -0.003 | 0.183 | 2.6 | 2.5 | 49 | 3/3 | 0.156 |
| book_sess | K7 | 3 | n_fl_ofi15s_z2 | 318 | 0.09 | -0.105 | 0.013 | -0.118 | -2.6 | 2.4 | 92 | 0/4 | -0.143 |
| sess |  | 1 | n_fl_size60_up | 454 | 0.03 | 0.194 | 0.019 | 0.174 | 2.6 | 2.5 | 119 | 4/4 | 0.198 |
| book_sess | K7 | 4 | n_fl_bignet60_with | 295 | 0.11 | -0.110 | 0.009 | -0.119 | -2.6 | 2.5 | 77 | 0/4 | -0.021 |
| book | A7 |  | n_fl_bignet300_with | 4597 | 0.27 | -0.005 | 0.028 | -0.033 | -2.5 | 2.4 | 187 | 0/4 | -0.040 |

## D RV/IV, VIX term, dispersion

32 conditions, 1632 (condition x cell) tests; passing alone: 16 tests, 8 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.98% of tests (2.1x the nonsense rate, 25% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 3, book 4, book_sess 6, sess 3.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | M7 | 1 | n_sd_rviv60_lt50 | 2055 | 0.66 | 0.057 | -0.080 | 0.137 | 4.3 | 2.8 | 97 | 4/4 | 0.117 |
| book_sess | P7 | 0 | n_sd_rviv240_gt15 | 86 | 0.02 | 0.324 | 0.065 | 0.259 | 4.1 | 3.0 | 17 | 2/2 | 0.541 |
| sess |  | 1 | n_sd_rviv60_lt50 | 12097 | 0.68 | 0.049 | -0.032 | 0.082 | 3.9 | 2.5 | 149 | 4/4 | 0.019 |
| book_sess | M7 | 5 | n_sd_breadth5_ge5 | 1060 | 0.50 | -0.021 | 0.124 | -0.145 | -3.9 | 2.6 | 107 | 0/3 | -0.189 |
| book | M7 |  | n_sd_breadth5_ge5 | 5689 | 0.53 | -0.006 | 0.066 | -0.072 | -3.6 | 2.1 | 109 | 0/3 | -0.050 |
| book_sess | H7 | 4 | n_sd_vix_fall1d_with | 235 | 0.50 | 0.083 | -0.112 | 0.195 | 3.5 | 2.9 | 16 | 4/4 | 0.338 |
| ALL |  |  | n_sd_breadth5_ge5 | 22043 | 0.52 | -0.008 | 0.031 | -0.039 | -3.5 | 2.2 | 109 | 0/3 | -0.010 |
| book_sess | K7 | 1 | n_sd_rviv60_lt50 | 1524 | 0.57 | 0.061 | -0.054 | 0.114 | 3.1 | 2.5 | 103 | 4/4 | 0.062 |
| sess |  | 1 | n_sd_rviv30_lt50 | 11858 | 0.67 | 0.050 | -0.031 | 0.081 | 3.1 | 2.5 | 164 | 4/4 | 0.027 |
| book | A7 |  | n_sd_vix_fall1d_with | 8981 | 0.52 | 0.067 | -0.033 | 0.100 | 2.8 | 2.4 | 187 | 4/4 | 0.049 |
| sess |  | 3 | n_sd_breadth5_ge5 | 6042 | 0.56 | -0.014 | 0.046 | -0.060 | -2.7 | 2.1 | 109 | 0/3 | -0.033 |
| book_sess | P7 | 2 | n_sd_breadth15_ge5 | 471 | 0.42 | 0.129 | 0.047 | 0.081 | 2.7 | 2.4 | 88 | 2/2 | 0.243 |
| ALL |  |  | n_sd_rviv60_lt50 | 45595 | 0.46 | 0.047 | 0.001 | 0.046 | 2.7 | 2.2 | 187 | 4/4 | 0.023 |
| book | P7 |  | n_sd_vix_fall5d_with | 14067 | 0.51 | 0.045 | -0.015 | 0.060 | 2.6 | 2.2 | 187 | 4/4 | 0.061 |
| book | M7 |  | n_sd_breadth60_ge5 | 7181 | 0.68 | 0.003 | 0.073 | -0.070 | -2.5 | 2.1 | 109 | 0/3 | -0.094 |
| ALL |  |  | n_sd_breadth60_ge5 | 25768 | 0.64 | -0.007 | 0.038 | -0.045 | -2.3 | 2.2 | 109 | 0/3 | -0.048 |

## Block 7 time-of-day liquidity events

580 conditions, 29580 (condition x cell) tests; passing alone: 21 tests, 18 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.07% of tests (0.2x the nonsense rate, 3% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 1, book 7, book_sess 10, sess 3.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | P7 | 5 | n7_t1600_post15_with | 116 | 0.02 | 0.222 | -0.005 | 0.227 | 3.3 | 2.5 | 29 | 2/2 | 0.290 |
| book_sess | K7 | 5 | n7_tophour_in | 273 | 0.14 | 0.075 | -0.036 | 0.111 | 3.0 | 2.6 | 78 | 4/4 | 0.285 |
| book | P7 |  | n7_w1400_1500_post30_with | 440 | 0.02 | -0.094 | 0.017 | -0.111 | -3.0 | 2.2 | 116 | 0/4 | -0.084 |
| book_sess | M7 | 5 | n7_t1600_post5_with | 147 | 0.04 | 0.101 | 0.009 | 0.092 | 2.9 | 2.6 | 39 | 2/2 | 0.334 |
| book_sess | K7 | 5 | n7_t1550_post15_with | 257 | 0.13 | 0.070 | -0.034 | 0.105 | 2.9 | 2.6 | 75 | 4/4 | 0.252 |
| book_sess | M7 | 3 | n7_w1000_1100_in_big_with | 506 | 0.15 | 0.075 | -0.013 | 0.088 | 2.8 | 2.7 | 130 | 4/4 | 0.211 |
| book_sess | P7 | 2 | n7_macro_xx50_pre15_with | 206 | 0.13 | 0.145 | 0.012 | 0.133 | 2.7 | 2.4 | 54 | 3/3 | 0.170 |
| book_sess | P7 | 5 | n7_t1600_post15 | 198 | 0.04 | 0.160 | -0.007 | 0.167 | 2.7 | 2.5 | 48 | 4/4 | 0.326 |
| book_sess | K7 | 5 | n7_tophour_in_with | 143 | 0.08 | 0.140 | -0.036 | 0.176 | 2.7 | 2.6 | 39 | 3/3 | 0.414 |
| book_sess | K7 | 5 | n7_t1550_post15 | 265 | 0.13 | 0.055 | -0.032 | 0.087 | 2.7 | 2.6 | 76 | 4/4 | 0.252 |
| book | P7 |  | n7_t1600_post15_with | 116 | 0.00 | 0.222 | 0.015 | 0.207 | 2.6 | 2.2 | 29 | 2/2 | 0.222 |
| book | P7 |  | n7_w1450_post30_with | 392 | 0.01 | -0.133 | 0.018 | -0.151 | -2.6 | 2.2 | 106 | 0/4 | -0.364 |
| book_sess | M7 | 0 | n7_tophour_pre15 | 4013 | 0.24 | 0.063 | 0.041 | 0.022 | 2.6 | 2.3 | 187 | 4/4 | 0.068 |
| sess |  | 3 | n7_grp_nyo_post15_with | 2678 | 0.16 | 0.075 | 0.009 | 0.066 | 2.4 | 2.1 | 185 | 4/4 | 0.089 |
| sess |  | 3 | n7_grp_nyo_post15 | 2888 | 0.17 | 0.066 | 0.010 | 0.056 | 2.3 | 2.1 | 186 | 4/4 | 0.071 |
| book | H7 |  | n7_halfhour_post15_with | 634 | 0.20 | 0.113 | 0.029 | 0.084 | 2.3 | 2.2 | 154 | 4/4 | 0.019 |
| ALL |  |  | n7_t1030_post30_against | 107 | 0.00 | -0.212 | 0.022 | -0.234 | -2.2 | 2.2 | 26 | 0/2 | -0.408 |
| book | M7 |  | n7_t1600_post5_with | 147 | 0.00 | 0.101 | 0.027 | 0.075 | 2.2 | 2.1 | 39 | 2/2 | 0.275 |
| book | M7 |  | n7_w1000_1100_in_big_with | 506 | 0.02 | 0.075 | 0.026 | 0.049 | 2.1 | 2.1 | 131 | 4/4 | 0.123 |
| book | M7 |  | n7_tophour_pre15_against | 859 | 0.03 | 0.066 | 0.026 | 0.041 | 2.1 | 2.1 | 166 | 4/4 | 0.078 |
| sess |  | 3 | n7_t0930_post15 | 1875 | 0.11 | 0.087 | 0.011 | 0.076 | 2.1 | 2.1 | 185 | 4/4 | 0.076 |

## Block 8 opening prices and gaps

131 conditions, 6681 (condition x cell) tests; passing alone: 55 tests, 37 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.82% of tests (1.7x the nonsense rate, 28% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 8, book 19, book_sess 11, sess 17.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 0 | n8_week_ext_against2 | 477 | 0.02 | -0.165 | 0.058 | -0.224 | -4.8 | 2.3 | 35 | 0/4 | -0.333 |
| ALL |  |  | n8_week_ext_with1 | 22078 | 0.22 | 0.041 | 0.016 | 0.025 | -4.2 | 2.2 | 169 | 4/4 | 0.026 |
| book | M7 |  | n8_gapD_unf_behind_1atr | 551 | 0.02 | 0.298 | 0.022 | 0.276 | 3.9 | 2.1 | 54 | 4/4 | 0.250 |
| sess |  | 0 | n8_mid_ext_against1 | 4663 | 0.20 | 0.000 | 0.063 | -0.063 | -3.9 | 2.3 | 183 | 0/4 | -0.126 |
| book_sess | P7 | 2 | n8_mid_near | 167 | 0.10 | 0.485 | -0.023 | 0.508 | 3.9 | 2.4 | 36 | 2/2 | 0.235 |
| book | K7 |  | n8_gapD_unf_behind_3atr | 546 | 0.04 | 0.105 | 0.005 | 0.100 | 3.8 | 2.7 | 55 | 4/4 | 0.034 |
| book | U7 |  | n8_mid_cross_with30 | 634 | 0.26 | 0.118 | 0.021 | 0.096 | 3.6 | 2.5 | 163 | 4/4 | 0.198 |
| sess |  | 0 | n8_o0830_ext_against2 | 3655 | 0.17 | -0.027 | 0.061 | -0.088 | -3.5 | 2.3 | 177 | 0/4 | -0.128 |
| book_sess | P7 | 0 | n8_week_ext_against1 | 473 | 0.10 | -0.137 | 0.093 | -0.231 | -3.4 | 3.0 | 70 | 0/3 | -0.248 |
| book | M7 |  | n8_gapD_unf_behind_3atr | 1455 | 0.04 | 0.168 | 0.020 | 0.148 | 3.4 | 2.1 | 65 | 4/4 | 0.184 |
| book_sess | M7 | 0 | n8_o0830_ext_against2 | 2340 | 0.17 | -0.030 | 0.051 | -0.081 | -3.3 | 2.3 | 160 | 0/4 | -0.133 |
| sess |  | 3 | n8_gapD_mid_side_with | 3859 | 0.53 | 0.112 | -0.082 | 0.194 | 3.2 | 2.1 | 89 | 4/4 | 0.131 |
| sess |  | 0 | n8_o0930_ext_against2 | 3616 | 0.17 | -0.018 | 0.060 | -0.078 | -3.2 | 2.3 | 173 | 0/4 | -0.077 |
| sess |  | 3 | n8_cg_filled | 6415 | 0.38 | -0.031 | 0.055 | -0.086 | -3.1 | 2.1 | 180 | 0/4 | -0.031 |
| book | U7 |  | n8_o1800_ext_against2 | 214 | 0.08 | -0.079 | 0.058 | -0.137 | -3.1 | 2.5 | 60 | 0/4 | -0.085 |
| sess |  | 2 | n8_mid_near | 508 | 0.09 | 0.275 | -0.033 | 0.308 | 3.1 | 2.7 | 75 | 4/4 | 0.335 |
| ALL |  |  | n8_hoNL_rev_cur_with | 21964 | 0.34 | -0.013 | 0.031 | -0.043 | -3.0 | 2.2 | 187 | 0/4 | -0.072 |
| sess |  | 0 | n8_mid_ext_against2 | 2959 | 0.13 | -0.017 | 0.060 | -0.078 | -3.0 | 2.3 | 168 | 0/4 | -0.140 |
| book_sess | A7 | 5 | n8_gapW_cur_unfilled | 286 | 0.17 | -0.237 | 0.017 | -0.254 | -3.0 | 2.5 | 8 | 0/3 | -0.470 |
| sess |  | 2 | n8_o0830_near | 1229 | 0.23 | 0.080 | -0.028 | 0.108 | 3.0 | 2.7 | 152 | 4/4 | 0.012 |
| sess |  | 4 | n8_cg_unfilled_against | 3032 | 0.16 | -0.069 | 0.012 | -0.081 | -2.9 | 2.4 | 154 | 0/4 | -0.189 |
| book_sess | H7 | 3 | n8_cg_filled | 249 | 0.39 | -0.088 | 0.163 | -0.251 | -2.9 | 2.4 | 33 | 0/4 | -0.557 |
| ALL |  |  | n8_on_inv_with | 50477 | 0.56 | 0.047 | -0.008 | 0.055 | 2.9 | 2.2 | 187 | 4/4 | 0.098 |
| book_sess | M7 | 0 | n8_o0930_ext_against2 | 2284 | 0.17 | -0.028 | 0.051 | -0.079 | -2.9 | 2.3 | 159 | 0/4 | -0.052 |
| sess |  | 1 | n8_month_ext_against1 | 4894 | 0.28 | -0.069 | 0.059 | -0.128 | -2.9 | 2.5 | 160 | 0/4 | -0.105 |

## Block 9 week / session structure

69 conditions, 3519 (condition x cell) tests; passing alone: 31 tests, 22 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.88% of tests (1.9x the nonsense rate, 32% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 5, book 4, book_sess 12, sess 10.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | n9_wk_used_lt50 | 35244 | 0.36 | 0.033 | 0.014 | 0.019 | 5.4 | 2.2 | 177 | 4/4 | 0.003 |
| book_sess | M7 | 0 | n9_mon_ext_against1 | 547 | 0.04 | -0.164 | 0.046 | -0.210 | -4.8 | 2.3 | 47 | 0/4 | -0.136 |
| sess |  | 0 | n9_mon_ext_against1 | 860 | 0.04 | -0.187 | 0.056 | -0.243 | -4.6 | 2.3 | 53 | 0/4 | -0.221 |
| sess |  | 0 | n9_mon_ext_against0 | 3780 | 0.17 | -0.042 | 0.065 | -0.107 | -3.9 | 2.3 | 162 | 0/4 | -0.175 |
| sess |  | 0 | n9_ysame_break_against | 6120 | 0.30 | -0.003 | 0.070 | -0.073 | -3.7 | 2.3 | 186 | 0/4 | -0.073 |
| book_sess | M7 | 0 | n9_ysame_break_against | 3902 | 0.29 | -0.008 | 0.054 | -0.061 | -3.5 | 2.3 | 184 | 0/4 | -0.064 |
| book_sess | M7 | 4 | n9_fhour_inside | 1166 | 0.32 | 0.087 | -0.046 | 0.133 | 3.4 | 2.6 | 166 | 4/4 | 0.218 |
| book_sess | M7 | 4 | n9_fhour_break_with | 2462 | 0.68 | -0.046 | 0.087 | -0.133 | -3.4 | 2.6 | 166 | 0/4 | -0.218 |
| ALL |  |  | n9_mon_ext_with1 | 10037 | 0.13 | 0.074 | 0.011 | 0.064 | -3.4 | 2.2 | 111 | 4/4 | 0.064 |
| book_sess | M7 | 0 | n9_wk_pos_bottom20 | 1700 | 0.10 | -0.057 | 0.058 | -0.114 | -3.3 | 2.3 | 141 | 0/4 | -0.243 |
| sess |  | 0 | n9_wk_pos_bottom20 | 2808 | 0.11 | -0.056 | 0.067 | -0.123 | -3.2 | 2.3 | 163 | 0/4 | -0.188 |
| ALL |  |  | n9_amd_dist_against | 2375 | 0.03 | -0.082 | 0.033 | -0.115 | -3.2 | 2.2 | 183 | 0/4 | -0.185 |
| book_sess | A7 | 0 | n9_wk_used_gt100 | 228 | 0.19 | 0.025 | 0.134 | -0.109 | -3.1 | 2.4 | 30 | 0/3 | -0.331 |
| sess |  | 0 | n9_mon_ext_with2 | 716 | 0.03 | 0.001 | 0.048 | -0.047 | -3.0 | 2.3 | 29 | 0/4 | -0.450 |
| book | A7 |  | n9_amd_acc | 4992 | 0.29 | -0.042 | 0.045 | -0.087 | -3.0 | 2.4 | 187 | 0/4 | -0.058 |
| book_sess | M7 | 4 | n9_ysame_inside | 950 | 0.24 | -0.110 | 0.033 | -0.143 | -2.9 | 2.6 | 128 | 0/4 | -0.227 |
| book | A7 |  | n9_q_in1 | 4635 | 0.27 | -0.043 | 0.042 | -0.086 | -2.9 | 2.4 | 187 | 0/4 | -0.051 |
| sess |  | 5 | n9_fhour_inside | 2732 | 0.59 | 0.056 | 0.006 | 0.050 | 2.8 | 2.7 | 164 | 4/4 | 0.032 |
| book_sess | M7 | 0 | n9_mon_ext_against0 | 2293 | 0.17 | -0.020 | 0.049 | -0.069 | -2.8 | 2.3 | 154 | 0/4 | -0.114 |
| book | M7 |  | n9_psess_break_against | 557 | 0.02 | -0.092 | 0.020 | -0.113 | -2.7 | 2.1 | 98 | 0/4 | -0.065 |
| book_sess | A7 | 2 | n9_mo_pos_top20 | 451 | 0.39 | -0.217 | 0.023 | -0.240 | -2.7 | 2.5 | 47 | 0/4 | -0.311 |
| sess |  | 0 | n9_fhour_break_against | 1354 | 0.06 | -0.007 | 0.063 | -0.070 | -2.7 | 2.3 | 153 | 0/4 | -0.149 |
| book_sess | K7 | 0 | n9_mon_ext_against1 | 123 | 0.05 | -0.183 | 0.042 | -0.225 | -2.7 | 2.3 | 30 | 0/2 | -0.172 |
| sess |  | 0 | n9_wk_pos_top20 | 10262 | 0.40 | 0.111 | 0.016 | 0.094 | 2.7 | 2.3 | 187 | 4/4 | 0.051 |
| book_sess | P7 | 2 | n9_ysame_inside | 145 | 0.12 | 0.386 | -0.025 | 0.410 | 2.6 | 2.4 | 29 | 2/2 | 0.634 |

## Block 13 microstructure

62 conditions, 3162 (condition x cell) tests; passing alone: 19 tests, 14 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.60% of tests (1.3x the nonsense rate, 23% of its conditions pass in at least one cell).

Passing tests by cell type: ALL 1, book 4, book_sess 9, sess 5.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 1 | n13_vpin_lo | 4428 | 0.26 | 0.064 | 0.008 | 0.056 | 3.3 | 2.5 | 165 | 4/4 | 0.029 |
| book_sess | K7 | 4 | n13_skew15_strong_against | 458 | 0.17 | -0.082 | 0.012 | -0.095 | -3.1 | 2.5 | 112 | 0/4 | -0.090 |
| sess |  | 5 | n13_skew15_strong_against | 1964 | 0.16 | -0.085 | 0.012 | -0.097 | -3.1 | 2.7 | 186 | 0/4 | -0.125 |
| sess |  | 2 | n13_jump60_any | 2571 | 0.48 | -0.089 | 0.074 | -0.163 | -2.8 | 2.7 | 156 | 0/4 | -0.368 |
| sess |  | 4 | n13_vpin_dir_against | 1478 | 0.08 | 0.082 | -0.009 | 0.091 | 2.7 | 2.4 | 170 | 4/4 | 0.157 |
| sess |  | 5 | n13_jump60_any | 2907 | 0.23 | 0.110 | -0.038 | 0.147 | 2.7 | 2.7 | 168 | 4/4 | 0.186 |
| book_sess | P7 | 5 | n13_arr300_hi | 880 | 0.18 | -0.060 | 0.013 | -0.074 | -2.7 | 2.5 | 168 | 0/4 | -0.121 |
| book_sess | P7 | 4 | n13_vpin_dir_against | 768 | 0.11 | 0.123 | -0.019 | 0.142 | 2.7 | 2.5 | 148 | 4/4 | 0.284 |
| book_sess | K7 | 0 | n13_vpin_dir_with | 344 | 0.33 | 0.248 | -0.002 | 0.250 | 2.6 | 2.3 | 52 | 3/3 | 0.322 |
| book | A7 |  | n13_skew60_strong_against | 1554 | 0.09 | -0.010 | 0.022 | -0.032 | -2.6 | 2.4 | 172 | 0/4 | -0.080 |
| book_sess | M7 | 2 | n13_arr300_lo | 304 | 0.24 | -0.131 | 0.035 | -0.167 | -2.6 | 2.4 | 78 | 0/4 | -0.210 |
| book_sess | P7 | 1 | n13_depth_thin | 343 | 0.07 | -0.077 | 0.019 | -0.096 | -2.6 | 2.2 | 43 | 0/3 | -0.145 |
| book_sess | P7 | 5 | n13_skew15_strong_against | 832 | 0.17 | -0.092 | 0.019 | -0.111 | -2.5 | 2.5 | 169 | 0/4 | -0.174 |
| book | P7 |  | n13_depth_thin | 3201 | 0.12 | -0.053 | 0.024 | -0.077 | -2.5 | 2.2 | 149 | 0/4 | -0.010 |
| ALL |  |  | n13_arr10_lo | 23008 | 0.24 | 0.035 | 0.018 | 0.017 | 2.5 | 2.2 | 187 | 4/4 | 0.032 |
| book_sess | M7 | 0 | n13_arr10_hi | 2867 | 0.18 | 0.020 | 0.054 | -0.034 | -2.4 | 2.3 | 187 | 0/4 | -0.046 |
| book_sess | M7 | 0 | n13_jump15_against | 149 | 0.01 | -0.094 | 0.047 | -0.141 | -2.4 | 2.3 | 41 | 0/2 | -0.316 |
| book | H7 |  | n13_sweep120_any | 432 | 0.14 | -0.040 | 0.061 | -0.101 | -2.3 | 2.2 | 123 | 0/4 | -0.007 |
| book | M7 |  | n13_arr_decel | 10483 | 0.33 | 0.041 | 0.020 | 0.021 | 2.1 | 2.1 | 187 | 4/4 | 0.057 |

## Block 16 flow calendar

48 conditions, 2448 (condition x cell) tests; passing alone: 9 tests, 7 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.47% of their tests (19% of controls pass in at least one cell); this block passes in 0.37% of tests (0.8x the nonsense rate, 15% of its conditions pass in at least one cell).

Passing tests by cell type: book 1, book_sess 3, sess 5.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 1 | n16_fomc_day | 407 | 0.02 | -0.318 | 0.032 | -0.349 | -3.2 | 2.5 | 27 | 0/4 | -0.217 |
| book_sess | A7 | 2 | n16_first3_td_month | 163 | 0.14 | 0.172 | -0.094 | 0.266 | 3.2 | 2.5 | 19 | 4/4 | 0.454 |
| book_sess | A7 | 1 | n16_fomc_day | 108 | 0.02 | -0.493 | 0.052 | -0.545 | -3.2 | 2.9 | 16 | 0/2 | -0.466 |
| sess |  | 1 | n16_collar_reset_pm1 | 464 | 0.03 | -0.182 | 0.029 | -0.211 | -3.2 | 2.5 | 17 | 0/4 | -0.052 |
| sess |  | 4 | n16_first_td_quarter | 279 | 0.01 | -0.344 | 0.003 | -0.347 | -2.9 | 2.4 | 14 | 0/4 | -0.449 |
| sess |  | 2 | n16_day_after_vix_expiry | 294 | 0.05 | -0.282 | 0.012 | -0.293 | -2.8 | 2.7 | 36 | 0/4 | -0.114 |
| book | P7 |  | n16_day_after_quad | 351 | 0.01 | 0.209 | 0.013 | 0.196 | 2.7 | 2.2 | 14 | 4/4 | 0.221 |
| book_sess | P7 | 1 | n16_fomc_day | 125 | 0.03 | -0.374 | 0.023 | -0.396 | -2.7 | 2.2 | 16 | 0/2 | -0.321 |
| sess |  | 3 | n16_fomc_day_after | 544 | 0.03 | -0.127 | 0.024 | -0.152 | -2.1 | 2.1 | 29 | 0/4 | -0.222 |

