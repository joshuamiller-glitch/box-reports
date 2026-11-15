# DS3_CONFLUENCE_ITEMS_CF5_ZW - Block 3 and Addendum-6 CF5 conditions each alone, cluster-robust (zw) with the nonsense bar

UNIVERSE: signals_all.parquet extended to 2026-11-13 (193,628 signals, in_pos == 0 and R known used). November 2026 rows (ld >= 20261101, about 2,100 signals) come from W-EV extended engine copy store and are PROVISIONAL until W-EV confirms parity; the table below uses everything, and a sensitivity column gives the pass rate with the universe cut at 2026-10-31. L3M / L6M windows are the step3 windows (asof 2026-11-09: L6M ld >= 20260512), so November enters only through the all-years tests. Price-frame fix of the 2026-10-18 reopen applied (W-CF1).

**Verdict line (2026-11-15 19:34Z): A named systems: 0.68% of tests (1.5x nonsense); B Dalton / Crabel / AC: 0.92% of tests (2.1x nonsense); B2 session-anchored op: 0.88% of tests (2.0x nonsense); C1 execution levels, s: 0.71% of tests (1.6x nonsense); C2 order-flow measures: 0.97% of tests (2.2x nonsense); D RV/IV, VIX term, dis: 1.12% of tests (2.6x nonsense); Block 7 time-of-day li: 0.08% of tests (0.2x nonsense); Block 8 opening prices: 0.50% of tests (1.1x nonsense); Block 9 week / session: 0.64% of tests (1.4x nonsense); Block 13 microstructur: 0.45% of tests (1.0x nonsense); Block 16 flow calendar: 0.46% of tests (1.0x nonsense). Passing alone is not an edge claim: the stack-level controls (W-CF3) still apply.**
RULE (W-CF1, CONFLUENCE_DEFS.md): pass alone only if |zw| (weekly cluster-robust t, >= 8 weeks) exceeds the 99th percentile of |zw| of the 200 nonsense controls c_Z_* IN THE SAME CELL, AND the lift keeps its sign in every calendar year with >= 30 cases per side (>= 2 such years) AND in L6M (>= 15 yes cases). Outcome = R of the universe signals with in_pos == 0 and R known (taken + skipped hypothetical), cells ALL, book, session, book x session. Data end: 2026-11-13.

## A named systems (DeMark, Raschke, Connors, Chande, Wilder, Kase, Ehlers, Brooks, stats)

4040 conditions, 202000 (condition x cell) tests; passing alone: 1369 tests, 990 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.68% of tests (1.5x the nonsense rate, 25% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.70% of tests (nonsense 0.46%).

Passing tests by cell type: ALL 93, book 316, book_sess 673, sess 287.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book | P7 |  | n_cn_rsi_pb_fast_60m_against10 | 2785 | 0.10 | -0.106 | 0.031 | -0.137 | -5.8 | 2.2 | 160 | 0/4 | -0.038 |
| sess |  | 4 | n_st_zma200_60m_eleave | 1555 | 0.08 | -0.238 | 0.020 | -0.258 | -5.2 | 2.4 | 108 | 0/4 | -0.333 |
| ALL |  |  | n_rk_soup_std_60m_with3 | 4652 | 0.06 | -0.070 | 0.024 | -0.094 | -5.2 | 2.3 | 173 | 0/4 | -0.128 |
| book | A7 |  | n_rk_grail_std_60m_against10 | 1825 | 0.10 | -0.084 | 0.034 | -0.118 | -5.1 | 2.4 | 138 | 0/4 | -0.141 |
| ALL |  |  | n_rk_grail_std_60m_with3 | 5026 | 0.06 | -0.057 | 0.023 | -0.080 | -5.0 | 2.3 | 143 | 0/4 | -0.196 |
| ALL |  |  | n_dm_combo_60m_with_ge13 | 684 | 0.01 | -0.159 | 0.020 | -0.179 | -4.8 | 2.3 | 19 | 0/4 | -0.466 |
| book_sess | M7 | 1 | n_ks_peak8_1m_eleave | 135 | 0.04 | 0.289 | -0.002 | 0.291 | 4.7 | 2.7 | 31 | 3/3 | 0.419 |
| book_sess | A7 | 4 | n_rk_310_std_60m_divwith | 715 | 0.18 | -0.217 | 0.043 | -0.260 | -4.7 | 2.5 | 91 | 0/4 | -0.253 |
| sess |  | 3 | n_wl_volstop_dist_fast_60m_fresh5 | 4625 | 0.27 | -0.043 | 0.047 | -0.090 | -4.6 | 2.0 | 182 | 0/4 | -0.028 |
| ALL |  |  | n_wl_volstop_flip_slow_60m_against10 | 13189 | 0.16 | -0.024 | 0.027 | -0.051 | -4.6 | 2.3 | 188 | 0/4 | -0.040 |
| book | K7 |  | n_bk_dojis5_1d_hi_z1 | 167 | 0.01 | 0.145 | 0.009 | 0.136 | 4.6 | 2.6 | 9 | 3/3 | 0.144 |
| sess |  | 3 | n_cn_rsi_pb_std_15m_against3 | 2520 | 0.15 | -0.052 | 0.035 | -0.087 | -4.6 | 2.0 | 172 | 0/4 | -0.115 |
| sess |  | 3 | n_eh_ebsw_std_1d_eleave | 1816 | 0.10 | -0.108 | 0.038 | -0.146 | -4.6 | 2.0 | 80 | 0/4 | -0.216 |
| book | M7 |  | n_rk_grail_std_60m_with3 | 1150 | 0.07 | -0.071 | 0.014 | -0.085 | -4.5 | 2.2 | 117 | 0/4 | -0.139 |
| book | K7 |  | n_dm_combo_60m_with_ge13 | 155 | 0.01 | -0.142 | 0.012 | -0.154 | -4.5 | 2.6 | 19 | 0/2 | -0.268 |
| sess |  | 3 | n_dm_line_break_1d_with1 | 1179 | 0.07 | -0.103 | 0.032 | -0.135 | -4.4 | 2.0 | 94 | 0/4 | -0.021 |
| sess |  | 3 | n_wl_volstop_flip_fast_60m_with3 | 4082 | 0.24 | -0.045 | 0.043 | -0.088 | -4.4 | 2.0 | 178 | 0/4 | -0.092 |
| book | M7 |  | n_wl_volstop_flip_slow_60m_against10 | 2451 | 0.15 | -0.059 | 0.020 | -0.078 | -4.4 | 2.2 | 171 | 0/4 | -0.077 |
| ALL |  |  | n_eh_roof_slow_60m_divwith | 14198 | 0.17 | -0.041 | 0.031 | -0.071 | -4.4 | 2.3 | 187 | 0/4 | -0.111 |
| book | M7 |  | n_st_nqlag_es30_5m_fresh5 | 6231 | 0.38 | -0.030 | 0.031 | -0.061 | -4.4 | 2.2 | 189 | 0/4 | -0.014 |
| book_sess | P7 | 0 | n_rk_grail_std_60m_against10 | 579 | 0.12 | -0.206 | 0.108 | -0.314 | -4.4 | 3.1 | 105 | 0/4 | -0.553 |
| ALL |  |  | n_dm_combo13_60m_with10 | 248 | 0.00 | -0.339 | 0.020 | -0.358 | -4.4 | 2.3 | 19 | 0/4 | -0.535 |
| book_sess | P7 | 1 | n_rk_grail_std_1d_against3 | 116 | 0.02 | -0.502 | 0.029 | -0.530 | -4.4 | 2.2 | 11 | 0/2 | -0.179 |
| sess |  | 3 | n_rk_310_slow_60m_divwith | 2486 | 0.14 | -0.069 | 0.038 | -0.108 | -4.3 | 2.0 | 157 | 0/4 | -0.138 |
| book | P7 |  | n_dm_combo_60m_with_ge13 | 214 | 0.01 | -0.291 | 0.020 | -0.311 | -4.3 | 2.2 | 18 | 0/3 | -0.450 |

## B Dalton / Crabel / ACD / Williams

124 conditions, 6200 (condition x cell) tests; passing alone: 57 tests, 32 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.92% of tests (2.1x the nonsense rate, 26% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.94% of tests (nonsense 0.46%).

Passing tests by cell type: ALL 6, book 16, book_sess 24, sess 11.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | n_wl_oops_with | 4573 | 0.11 | -0.099 | 0.019 | -0.118 | -6.7 | 2.3 | 141 | 0/4 | -0.222 |
| sess |  | 5 | n_fa_c_fast_with | 2207 | 0.30 | -0.146 | 0.029 | -0.176 | -4.2 | 2.5 | 154 | 0/4 | -0.267 |
| book_sess | U7 | 1 | n_dl_inside_va | 293 | 0.42 | 0.148 | -0.029 | 0.177 | 4.2 | 2.3 | 45 | 4/4 | 0.153 |
| book | M7 |  | n_wl_oops_with | 1155 | 0.11 | -0.090 | 0.016 | -0.107 | -4.1 | 2.2 | 119 | 0/4 | -0.217 |
| sess |  | 3 | n_cb_prior_wide | 2542 | 0.15 | -0.098 | 0.044 | -0.142 | -4.0 | 2.0 | 85 | 0/4 | -0.025 |
| book | A7 |  | n_wl_smash_against | 4684 | 0.27 | -0.039 | 0.043 | -0.082 | -3.8 | 2.4 | 184 | 0/4 | -0.098 |
| book_sess | K7 | 3 | n_dl_pd_neutral_ext | 216 | 0.06 | 0.241 | -0.009 | 0.250 | 3.7 | 2.3 | 46 | 4/4 | 0.289 |
| ALL |  |  | n_dl_pd_trend_with | 2947 | 0.04 | -0.046 | 0.021 | -0.067 | -3.6 | 2.3 | 71 | 0/4 | -0.202 |
| book | A7 |  | n_dl_pd_neutral | 2138 | 0.12 | 0.174 | 0.000 | 0.174 | 3.6 | 2.4 | 82 | 4/4 | 0.083 |
| book_sess | K7 | 3 | n_dl_pd_trend_with | 113 | 0.03 | -0.364 | 0.019 | -0.383 | -3.6 | 2.3 | 31 | 0/2 | -0.614 |
| ALL |  |  | n_fa_c_std_with | 4043 | 0.11 | -0.071 | 0.009 | -0.080 | -3.5 | 2.3 | 125 | 0/4 | -0.069 |
| book_sess | A7 | 4 | n_wl_oops_with | 435 | 0.11 | -0.304 | 0.035 | -0.339 | -3.5 | 2.5 | 63 | 0/4 | -0.494 |
| book | H7 |  | n_cb_prior_narrow | 408 | 0.13 | 0.164 | 0.029 | 0.136 | 3.5 | 2.4 | 67 | 4/4 | 0.136 |
| book_sess | A7 | 4 | n_wl_gap_against | 604 | 0.15 | -0.210 | 0.035 | -0.245 | -3.5 | 2.5 | 78 | 0/4 | -0.368 |
| book | K7 |  | n_wl_oops_with | 668 | 0.09 | -0.106 | 0.012 | -0.117 | -3.4 | 2.6 | 109 | 0/4 | -0.251 |
| sess |  | 4 | n_dl_r80_active_with | 963 | 0.05 | -0.202 | 0.011 | -0.213 | -3.4 | 2.4 | 87 | 0/4 | -0.082 |
| book_sess | A7 | 3 | n_cb_prior_wide | 456 | 0.12 | -0.229 | 0.071 | -0.300 | -3.4 | 2.6 | 64 | 0/4 | -0.099 |
| book_sess | K7 | 3 | n_dl_excess_support_with | 2403 | 0.70 | -0.030 | 0.092 | -0.122 | -3.4 | 2.3 | 165 | 0/4 | -0.187 |
| book_sess | K7 | 3 | n_dl_pd_neutral | 381 | 0.11 | 0.158 | -0.012 | 0.170 | 3.4 | 2.3 | 74 | 4/4 | 0.127 |
| sess |  | 3 | n_dl_pd_neutral_ext | 1058 | 0.06 | 0.224 | 0.010 | 0.214 | 3.4 | 2.0 | 49 | 4/4 | 0.149 |
| sess |  | 3 | n_dl_pd_neutral | 1887 | 0.11 | 0.155 | 0.007 | 0.148 | 3.3 | 2.0 | 81 | 4/4 | 0.048 |
| book_sess | A7 | 3 | n_fa_a_slow_now_with | 880 | 0.35 | 0.001 | 0.072 | -0.071 | -3.3 | 2.6 | 135 | 0/4 | -0.086 |
| book | A7 |  | n_cb_prior_wide | 2403 | 0.14 | -0.104 | 0.041 | -0.146 | -3.3 | 2.4 | 88 | 0/4 | -0.027 |
| sess |  | 4 | n_dl_va_narrow | 205 | 0.01 | 0.188 | -0.003 | 0.190 | 3.3 | 2.4 | 8 | 2/2 | 0.107 |
| book_sess | P7 | 3 | n_dl_pd_neutral_ext | 305 | 0.06 | 0.135 | -0.001 | 0.136 | 3.3 | 2.9 | 44 | 4/4 | 0.074 |

## B2 session-anchored opening-range systems

48 conditions, 2400 (condition x cell) tests; passing alone: 21 tests, 15 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.88% of tests (2.0x the nonsense rate, 31% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.88% of tests (nonsense 0.46%).

Passing tests by cell type: ALL 1, book 2, book_sess 15, sess 3.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | H7 | 1 | n_ss_a_slow_fresh30 | 138 | 0.16 | -0.170 | 0.095 | -0.265 | -4.1 | 2.9 | 24 | 0/3 | -0.427 |
| book_sess | M7 | 2 | n_ss_orb15_beyond | 448 | 0.46 | -0.033 | 0.026 | -0.059 | -3.7 | 2.4 | 68 | 0/4 | -0.046 |
| book_sess | M7 | 2 | n_ss_inor_std | 523 | 0.54 | 0.028 | -0.035 | 0.063 | 3.6 | 2.4 | 69 | 4/4 | 0.064 |
| book_sess | P7 | 2 | n_ss_orb5_fresh15 | 157 | 0.11 | -0.124 | 0.037 | -0.162 | -3.3 | 2.4 | 35 | 0/3 | -0.207 |
| ALL |  |  | n_ss_oops_with | 6920 | 0.09 | -0.033 | 0.024 | -0.057 | -3.2 | 2.3 | 183 | 0/4 | -0.148 |
| book_sess | K7 | 4 | n_ss_inor_std | 536 | 0.22 | 0.072 | -0.037 | 0.109 | 3.0 | 2.3 | 109 | 4/4 | 0.071 |
| book_sess | P7 | 2 | n_ss_a_fast_hit_with | 995 | 0.67 | -0.054 | 0.172 | -0.227 | -2.9 | 2.4 | 81 | 0/4 | -0.188 |
| book_sess | H7 | 1 | n_ss_a_std_fresh30 | 134 | 0.15 | -0.295 | 0.115 | -0.410 | -2.9 | 2.9 | 29 | 0/3 | -0.371 |
| sess |  | 2 | n_ss_range_used_gt150 | 886 | 0.19 | -0.182 | 0.031 | -0.214 | -2.8 | 2.8 | 94 | 0/4 | -0.365 |
| book_sess | K7 | 2 | n_ss_orb15_fresh15 | 239 | 0.38 | 0.107 | -0.054 | 0.161 | 2.8 | 2.3 | 48 | 3/3 | 0.114 |
| sess |  | 4 | n_ss_inor_slow | 4443 | 0.27 | 0.045 | -0.023 | 0.067 | 2.7 | 2.4 | 187 | 4/4 | 0.026 |
| book_sess | A7 | 5 | n_ss_orb15_beyond | 1155 | 0.86 | 0.036 | -0.189 | 0.225 | 2.7 | 2.4 | 48 | 3/3 | 0.350 |
| book_sess | M7 | 4 | n_ss_inor_slow | 990 | 0.22 | 0.114 | -0.026 | 0.140 | 2.7 | 2.6 | 151 | 4/4 | 0.230 |
| book_sess | M7 | 4 | n_ss_orb30_beyond | 3437 | 0.77 | -0.026 | 0.113 | -0.138 | -2.6 | 2.6 | 153 | 0/4 | -0.242 |
| book_sess | P7 | 2 | n_ss_orb5_beyond | 835 | 0.56 | -0.028 | 0.081 | -0.109 | -2.6 | 2.4 | 96 | 0/4 | -0.042 |
| sess |  | 4 | n_ss_orb30_beyond | 11597 | 0.71 | -0.024 | 0.044 | -0.068 | -2.6 | 2.4 | 189 | 0/4 | -0.045 |
| book_sess | K7 | 4 | n_ss_orb30_failed | 132 | 0.06 | 0.100 | -0.025 | 0.125 | 2.5 | 2.3 | 30 | 2/2 | 0.219 |
| book | P7 |  | n_ss_a_fast_hit_with | 20269 | 0.77 | -0.001 | 0.072 | -0.072 | -2.4 | 2.2 | 189 | 0/4 | -0.064 |
| book_sess | K7 | 4 | n_ss_a_std_hit_with | 1598 | 0.66 | -0.044 | 0.050 | -0.094 | -2.4 | 2.3 | 148 | 0/4 | -0.074 |
| book_sess | P7 | 1 | n_ss_c_std_with | 1513 | 0.31 | 0.075 | -0.022 | 0.096 | 2.3 | 2.2 | 142 | 4/4 | 0.050 |
| book | M7 |  | n_ss_oops_with | 1421 | 0.09 | -0.083 | 0.013 | -0.096 | -2.3 | 2.2 | 164 | 0/4 | -0.216 |

## C1 execution levels, seasonality, volume curve

34 conditions, 1700 (condition x cell) tests; passing alone: 12 tests, 10 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.71% of tests (1.6x the nonsense rate, 29% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.71% of tests (nonsense 0.46%).

Passing tests by cell type: book 2, book_sess 8, sess 2.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 5 | n_ex_volcurve_ahead_move_with | 2918 | 0.23 | -0.071 | 0.022 | -0.093 | -3.0 | 2.5 | 116 | 0/4 | -0.035 |
| book_sess | K7 | 0 | n_ex_mv_with_large | 1255 | 0.39 | 0.101 | 0.012 | 0.089 | 2.8 | 2.3 | 174 | 4/4 | 0.004 |
| book_sess | K7 | 0 | n_ex_mv_pullback_hold | 1255 | 0.39 | 0.101 | 0.012 | 0.089 | 2.8 | 2.3 | 174 | 4/4 | 0.004 |
| book_sess | M7 | 1 | n_ex_mv_with | 3085 | 0.96 | 0.020 | -0.269 | 0.289 | 2.7 | 2.7 | 30 | 2/2 | 0.195 |
| book_sess | M7 | 4 | n_ex_seas30_strong_against | 815 | 0.16 | 0.100 | -0.010 | 0.110 | 2.7 | 2.6 | 144 | 4/4 | 0.062 |
| book | A7 |  | n_ex_seas120_strong_with | 2462 | 0.15 | -0.030 | 0.029 | -0.059 | -2.7 | 2.4 | 181 | 0/4 | -0.022 |
| sess |  | 5 | n_ex_volcurve_ahead | 3189 | 0.25 | -0.071 | 0.024 | -0.095 | -2.6 | 2.5 | 113 | 0/4 | -0.019 |
| book_sess | K7 | 2 | n_ex_mv_pullback_hold | 646 | 0.71 | -0.077 | 0.168 | -0.245 | -2.6 | 2.3 | 60 | 0/3 | -0.437 |
| book_sess | K7 | 1 | n_ex_range30_lo | 362 | 0.13 | 0.092 | 0.001 | 0.091 | 2.5 | 2.4 | 66 | 3/3 | 0.069 |
| book_sess | K7 | 2 | n_ex_mv_with_large | 648 | 0.71 | -0.073 | 0.162 | -0.235 | -2.5 | 2.3 | 59 | 0/3 | -0.437 |
| book_sess | K7 | 0 | n_ex_mv_large2 | 1441 | 0.44 | 0.093 | 0.009 | 0.084 | 2.3 | 2.3 | 177 | 4/4 | 0.037 |
| book | M7 |  | n_ex_seas30_strong_with | 2611 | 0.16 | -0.034 | 0.016 | -0.050 | -2.2 | 2.2 | 189 | 0/4 | -0.060 |

## C2 order-flow measures

72 conditions, 3600 (condition x cell) tests; passing alone: 35 tests, 25 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.97% of tests (2.2x the nonsense rate, 35% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 1.08% of tests (nonsense 0.46%).

Passing tests by cell type: book 7, book_sess 19, sess 9.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | U7 | 0 | n_fl_bimb1060s_strong | 102 | 0.17 | 0.063 | 0.090 | -0.028 | 4.1 | 2.9 | 13 | 0/2 | -0.000 |
| book_sess | A7 | 3 | n_fl_mic5s_with | 1753 | 0.48 | 0.088 | -0.020 | 0.108 | 3.4 | 2.6 | 185 | 4/4 | 0.202 |
| book_sess | A7 | 1 | n_fl_mic300s_with | 2999 | 0.54 | 0.079 | -0.004 | 0.083 | 3.4 | 2.9 | 183 | 4/4 | 0.193 |
| book_sess | A7 | 5 | n_fl_ofi1s_z1 | 149 | 0.09 | -0.193 | -0.013 | -0.181 | -3.3 | 2.4 | 38 | 0/4 | -0.250 |
| book_sess | A7 | 1 | n_fl_bigshare300_up | 1700 | 0.32 | 0.091 | 0.026 | 0.065 | 3.2 | 2.9 | 180 | 4/4 | 0.112 |
| book_sess | K7 | 5 | n_fl_bimb515s_with | 1041 | 0.52 | -0.058 | 0.021 | -0.079 | -3.2 | 2.6 | 154 | 0/4 | -0.141 |
| book | U7 |  | n_fl_bimb5300s_with | 1420 | 0.57 | -0.001 | 0.108 | -0.109 | -3.1 | 2.5 | 184 | 0/4 | -0.048 |
| book_sess | P7 | 5 | n_fl_ofi15s_z2 | 278 | 0.06 | -0.095 | 0.008 | -0.103 | -3.1 | 2.6 | 81 | 0/4 | -0.164 |
| book_sess | K7 | 3 | n_fl_bimb5300s_with | 1765 | 0.52 | -0.043 | 0.058 | -0.101 | -3.1 | 2.3 | 182 | 0/4 | -0.043 |
| book | A7 |  | n_fl_ofi300s_with | 12559 | 0.73 | 0.008 | 0.058 | -0.050 | -3.0 | 2.4 | 189 | 0/4 | -0.136 |
| book_sess | K7 | 3 | n_fl_bimb1060s_with | 1594 | 0.47 | -0.049 | 0.053 | -0.101 | -2.9 | 2.3 | 180 | 0/4 | -0.094 |
| sess |  | 1 | n_fl_bigshare300_up | 4751 | 0.28 | 0.055 | 0.014 | 0.041 | 2.8 | 2.5 | 188 | 4/4 | 0.049 |
| book_sess | A7 | 3 | n_fl_ofi300s_z2 | 466 | 0.13 | -0.066 | 0.047 | -0.113 | -2.8 | 2.6 | 125 | 0/4 | -0.320 |
| book_sess | A7 | 3 | n_fl_qtr60_lo | 580 | 0.16 | -0.091 | 0.055 | -0.146 | -2.7 | 2.6 | 143 | 0/4 | -0.240 |
| book_sess | K7 | 4 | n_fl_bignet60_with | 299 | 0.11 | -0.115 | 0.009 | -0.125 | -2.6 | 2.3 | 78 | 0/4 | -0.071 |
| book_sess | K7 | 3 | n_fl_ofi15s_z2 | 319 | 0.09 | -0.102 | 0.016 | -0.118 | -2.6 | 2.3 | 92 | 0/4 | -0.145 |
| book_sess | K7 | 1 | n_fl_ofi15s_z2 | 221 | 0.08 | 0.177 | -0.000 | 0.178 | 2.6 | 2.4 | 51 | 3/3 | 0.141 |
| sess |  | 1 | n_fl_size60_up | 461 | 0.03 | 0.194 | 0.021 | 0.173 | 2.6 | 2.5 | 121 | 4/4 | 0.192 |
| sess |  | 5 | n_fl_mic15s_with | 6146 | 0.49 | -0.025 | 0.020 | -0.045 | -2.5 | 2.5 | 189 | 0/4 | -0.055 |
| book_sess | P7 | 4 | n_fl_bignet300_with | 1187 | 0.17 | -0.060 | 0.011 | -0.071 | -2.5 | 2.5 | 179 | 0/4 | -0.131 |
| book | U7 |  | n_fl_ofi5s_z2 | 142 | 0.06 | -0.132 | 0.057 | -0.189 | -2.5 | 2.5 | 30 | 0/4 | -0.273 |
| book | A7 |  | n_fl_bignet300_with | 4643 | 0.27 | -0.002 | 0.030 | -0.032 | -2.5 | 2.4 | 189 | 0/4 | -0.030 |
| sess |  | 3 | n_fl_ofi15s_strong | 1350 | 0.08 | -0.050 | 0.028 | -0.078 | -2.5 | 2.0 | 184 | 0/4 | -0.047 |
| sess |  | 3 | n_fl_bimb1060s_with | 6780 | 0.39 | -0.017 | 0.047 | -0.064 | -2.4 | 2.0 | 188 | 0/4 | -0.043 |
| book_sess | P7 | 2 | n_fl_bimb51s_strong | 195 | 0.12 | -0.056 | 0.038 | -0.094 | -2.4 | 2.4 | 52 | 0/3 | -0.062 |

## D RV/IV, VIX term, dispersion

32 conditions, 1600 (condition x cell) tests; passing alone: 18 tests, 10 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 1.12% of tests (2.6x the nonsense rate, 31% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 1.00% of tests (nonsense 0.46%).

Passing tests by cell type: book 6, book_sess 7, sess 5.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | M7 | 1 | n_sd_rviv60_lt50 | 2037 | 0.63 | 0.059 | -0.074 | 0.133 | 4.2 | 2.7 | 99 | 4/4 | 0.103 |
| book_sess | P7 | 0 | n_sd_rviv240_gt15 | 91 | 0.02 | 0.327 | 0.064 | 0.262 | 4.1 | 3.1 | 17 | 2/2 | 0.508 |
| book_sess | M7 | 5 | n_sd_breadth5_ge5 | 1093 | 0.51 | -0.016 | 0.129 | -0.145 | -3.9 | 2.8 | 109 | 0/3 | -0.172 |
| sess |  | 1 | n_sd_rviv60_lt50 | 12045 | 0.67 | 0.050 | -0.026 | 0.075 | 3.7 | 2.5 | 151 | 4/4 | 0.002 |
| book | M7 |  | n_sd_breadth5_ge5 | 5293 | 0.55 | -0.011 | 0.067 | -0.078 | -3.6 | 2.2 | 111 | 0/3 | -0.050 |
| book_sess | H7 | 4 | n_sd_vix_fall1d_with | 236 | 0.50 | 0.087 | -0.115 | 0.202 | 3.5 | 2.9 | 16 | 4/4 | 0.388 |
| sess |  | 1 | n_sd_rviv30_lt50 | 11844 | 0.65 | 0.053 | -0.029 | 0.081 | 3.1 | 2.5 | 166 | 4/4 | 0.032 |
| book_sess | K7 | 1 | n_sd_rviv60_lt50 | 1503 | 0.54 | 0.058 | -0.040 | 0.098 | 3.0 | 2.4 | 105 | 4/4 | 0.013 |
| book_sess | M7 | 1 | n_sd_rviv30_lt50 | 1996 | 0.62 | 0.053 | -0.060 | 0.113 | 2.8 | 2.7 | 111 | 4/4 | 0.090 |
| book_sess | P7 | 2 | n_sd_breadth15_ge5 | 482 | 0.42 | 0.128 | 0.040 | 0.088 | 2.7 | 2.4 | 90 | 2/2 | 0.250 |
| book | A7 |  | n_sd_vix_fall1d_with | 9128 | 0.52 | 0.067 | -0.029 | 0.096 | 2.7 | 2.4 | 189 | 4/4 | 0.033 |
| book | H7 |  | n_sd_rviv30_lt50 | 1604 | 0.50 | 0.084 | 0.008 | 0.075 | 2.7 | 2.4 | 184 | 4/4 | 0.039 |
| sess |  | 3 | n_sd_breadth5_ge5 | 6165 | 0.56 | -0.007 | 0.050 | -0.057 | -2.6 | 2.0 | 111 | 0/3 | -0.014 |
| sess |  | 5 | n_sd_breadth5_ge5 | 3826 | 0.50 | -0.012 | 0.046 | -0.058 | -2.6 | 2.5 | 111 | 0/3 | -0.065 |
| book | P7 |  | n_sd_vix_fall5d_with | 14317 | 0.51 | 0.044 | -0.010 | 0.054 | 2.5 | 2.2 | 189 | 4/4 | 0.037 |
| book | A7 |  | n_sd_rviv240_gt1 | 2331 | 0.13 | -0.047 | 0.032 | -0.079 | -2.4 | 2.4 | 144 | 0/4 | -0.006 |
| book | M7 |  | n_sd_vix_backward | 1446 | 0.09 | 0.082 | 0.001 | 0.080 | 2.4 | 2.2 | 16 | 3/3 | 0.276 |
| sess |  | 3 | n_sd_breadth15_le2 | 1086 | 0.10 | -0.048 | 0.025 | -0.072 | -2.0 | 2.0 | 108 | 0/3 | -0.083 |

## Block 7 time-of-day liquidity events

580 conditions, 29000 (condition x cell) tests; passing alone: 23 tests, 21 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.08% of tests (0.2x the nonsense rate, 4% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.07% of tests (nonsense 0.46%).

Passing tests by cell type: ALL 1, book 6, book_sess 11, sess 5.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | P7 | 5 | n7_t1600_post15_with | 118 | 0.02 | 0.235 | -0.002 | 0.237 | 3.3 | 2.6 | 29 | 2/2 | 0.335 |
| book | P7 |  | n7_w1400_1500_post30_with | 442 | 0.02 | -0.094 | 0.019 | -0.113 | -3.0 | 2.2 | 116 | 0/4 | -0.090 |
| sess |  | 0 | n7_t1800_post5 | 958 | 0.09 | -0.032 | 0.079 | -0.111 | -3.0 | 2.8 | 183 | 0/4 | -0.201 |
| book_sess | P7 | 5 | n7_t1600_post15 | 202 | 0.04 | 0.177 | -0.004 | 0.181 | 2.9 | 2.6 | 49 | 4/4 | 0.377 |
| book_sess | M7 | 5 | n7_t1600_post5_with | 147 | 0.04 | 0.101 | 0.013 | 0.089 | 2.9 | 2.8 | 39 | 2/2 | 0.310 |
| book_sess | K7 | 5 | n7_t1550_post15_with | 262 | 0.13 | 0.073 | -0.031 | 0.103 | 2.9 | 2.6 | 77 | 4/4 | 0.233 |
| book_sess | M7 | 1 | n7_tophour_pre15_against | 87 | 0.03 | -0.142 | 0.014 | -0.156 | -2.9 | 2.7 | 10 | 0/2 | -0.201 |
| book | M7 |  | n7_w1000_1100_in_big_with | 512 | 0.03 | 0.070 | 0.006 | 0.064 | 2.8 | 2.2 | 132 | 4/4 | 0.138 |
| book_sess | P7 | 2 | n7_macro_xx50_pre15_with | 210 | 0.13 | 0.142 | 0.010 | 0.132 | 2.7 | 2.4 | 56 | 3/3 | 0.167 |
| book_sess | K7 | 5 | n7_t1550_post15 | 271 | 0.13 | 0.058 | -0.029 | 0.086 | 2.7 | 2.6 | 78 | 4/4 | 0.231 |
| book_sess | M7 | 3 | n7_w1000_1100_in_big_with | 512 | 0.15 | 0.070 | -0.009 | 0.079 | 2.7 | 2.6 | 131 | 4/4 | 0.160 |
| book | K7 |  | n7_grp_eur_post5 | 87 | 0.01 | -0.116 | 0.011 | -0.127 | -2.7 | 2.6 | 19 | 0/2 | -0.236 |
| book_sess | K7 | 5 | n7_tophour_in_with | 146 | 0.08 | 0.144 | -0.031 | 0.174 | 2.7 | 2.6 | 40 | 3/3 | 0.385 |
| book | P7 |  | n7_w1450_post30_with | 399 | 0.01 | -0.134 | 0.020 | -0.153 | -2.6 | 2.2 | 108 | 0/4 | -0.352 |
| book | P7 |  | n7_t1600_post15_with | 118 | 0.00 | 0.235 | 0.017 | 0.218 | 2.6 | 2.2 | 29 | 2/2 | 0.282 |
| book_sess | K7 | 5 | n7_tophour_in | 281 | 0.14 | 0.066 | -0.031 | 0.097 | 2.6 | 2.6 | 80 | 4/4 | 0.195 |
| ALL |  |  | n7_t0930_post15_big_with | 933 | 0.01 | 0.137 | 0.017 | 0.120 | 2.6 | 2.3 | 172 | 4/4 | 0.078 |
| sess |  | 3 | n7_grp_nyo_post15_with | 2720 | 0.16 | 0.081 | 0.012 | 0.069 | 2.5 | 2.0 | 187 | 4/4 | 0.108 |
| book_sess | K7 | 2 | n7_macro_xx50_post30_with | 175 | 0.19 | -0.143 | 0.031 | -0.173 | -2.4 | 2.3 | 49 | 0/3 | -0.184 |
| sess |  | 3 | n7_grp_nyo_post15 | 2938 | 0.17 | 0.072 | 0.013 | 0.059 | 2.4 | 2.0 | 188 | 4/4 | 0.089 |
| book | M7 |  | n7_w1050_post15 | 232 | 0.01 | 0.064 | 0.007 | 0.056 | 2.3 | 2.2 | 65 | 3/3 | 0.056 |
| sess |  | 3 | n7_t0930_post15 | 1908 | 0.11 | 0.091 | 0.014 | 0.077 | 2.1 | 2.0 | 187 | 4/4 | 0.086 |
| sess |  | 3 | n7_t0930_post15_with | 1825 | 0.11 | 0.094 | 0.014 | 0.080 | 2.1 | 2.0 | 187 | 4/4 | 0.103 |

## Block 8 opening prices and gaps

131 conditions, 6550 (condition x cell) tests; passing alone: 33 tests, 23 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.50% of tests (1.1x the nonsense rate, 18% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.53% of tests (nonsense 0.46%).

Passing tests by cell type: ALL 4, book 11, book_sess 9, sess 9.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book | K7 |  | n8_gapD_unf_behind_3atr | 559 | 0.04 | 0.108 | 0.007 | 0.102 | 3.9 | 2.6 | 57 | 4/4 | 0.065 |
| book_sess | P7 | 2 | n8_mid_near | 167 | 0.10 | 0.485 | -0.025 | 0.510 | 3.9 | 2.4 | 36 | 2/2 | 0.242 |
| ALL |  |  | n8_week_ext_with1 | 19835 | 0.24 | 0.040 | 0.012 | 0.028 | -3.8 | 2.3 | 170 | 4/4 | 0.036 |
| book | U7 |  | n8_mid_cross_with30 | 643 | 0.26 | 0.115 | 0.024 | 0.091 | 3.5 | 2.5 | 165 | 4/4 | 0.163 |
| book_sess | P7 | 0 | n8_week_ext_against1 | 532 | 0.11 | -0.127 | 0.094 | -0.221 | -3.4 | 3.1 | 74 | 0/3 | -0.226 |
| sess |  | 3 | n8_gapD_mid_side_with | 3956 | 0.53 | 0.115 | -0.068 | 0.183 | 3.2 | 2.0 | 91 | 4/4 | 0.043 |
| sess |  | 2 | n8_mid_near | 518 | 0.09 | 0.277 | -0.034 | 0.311 | 3.2 | 2.8 | 76 | 4/4 | 0.348 |
| sess |  | 0 | n8_month_side | 5953 | 0.55 | 0.111 | 0.018 | 0.093 | 3.1 | 2.8 | 189 | 4/4 | 0.090 |
| sess |  | 3 | n8_cg_filled | 6436 | 0.38 | -0.029 | 0.060 | -0.089 | -3.1 | 2.0 | 181 | 0/4 | -0.053 |
| book | U7 |  | n8_o1800_ext_against2 | 217 | 0.08 | -0.073 | 0.058 | -0.131 | -3.1 | 2.5 | 61 | 0/4 | -0.060 |
| sess |  | 0 | n8_week_ext_against2 | 249 | 0.02 | -0.101 | 0.073 | -0.174 | -3.1 | 2.8 | 30 | 0/3 | -0.108 |
| sess |  | 1 | n8_month_ext_against1 | 4873 | 0.27 | -0.075 | 0.061 | -0.136 | -3.0 | 2.5 | 162 | 0/4 | -0.138 |
| book_sess | A7 | 5 | n8_gapW_cur_unfilled | 282 | 0.17 | -0.226 | 0.018 | -0.244 | -3.0 | 2.4 | 8 | 0/3 | -0.434 |
| book_sess | H7 | 3 | n8_cg_filled | 249 | 0.39 | -0.088 | 0.161 | -0.249 | -2.9 | 2.4 | 33 | 0/4 | -0.531 |
| sess |  | 4 | n8_cg_unfilled_against | 3101 | 0.16 | -0.063 | 0.013 | -0.075 | -2.9 | 2.4 | 156 | 0/4 | -0.148 |
| ALL |  |  | n8_ig_with1 | 7933 | 0.09 | 0.082 | 0.012 | 0.070 | -2.8 | 2.3 | 158 | 4/4 | 0.111 |
| book_sess | P7 | 4 | n8_hoLA_prev_big | 450 | 0.07 | -0.149 | 0.010 | -0.159 | -2.8 | 2.5 | 48 | 0/3 | -0.048 |
| book | M7 |  | n8_hoLA_rev_cur_with | 4819 | 0.30 | -0.020 | 0.019 | -0.038 | -2.8 | 2.2 | 183 | 0/4 | -0.091 |
| book | K7 |  | n8_hoAN_cur_with | 2857 | 0.59 | 0.059 | -0.026 | 0.084 | 2.7 | 2.6 | 176 | 4/4 | 0.105 |
| sess |  | 4 | n8_hoLA_prev_big | 1304 | 0.07 | -0.122 | 0.009 | -0.130 | -2.7 | 2.4 | 51 | 0/4 | -0.118 |
| book | H7 |  | n8_gapD_cur_up_with | 1664 | 0.52 | 0.099 | -0.010 | 0.109 | 2.6 | 2.4 | 185 | 4/4 | 0.073 |
| book | A7 |  | n8_ig_with1 | 2414 | 0.14 | 0.081 | 0.012 | 0.069 | -2.6 | 2.4 | 148 | 4/4 | 0.025 |
| book_sess | P7 | 1 | n8_gapD_cur_up_with | 2552 | 0.51 | 0.091 | -0.063 | 0.154 | 2.6 | 2.2 | 162 | 4/4 | 0.060 |
| book_sess | A7 | 5 | n8_mid_ext_against2 | 104 | 0.06 | 0.249 | -0.041 | 0.291 | 2.6 | 2.4 | 19 | 2/2 | 0.763 |
| book | A7 |  | n8_on_inv_with | 9438 | 0.57 | 0.059 | -0.031 | 0.089 | 2.5 | 2.4 | 189 | 4/4 | 0.121 |

## Block 9 week / session structure

69 conditions, 3450 (condition x cell) tests; passing alone: 22 tests, 15 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.64% of tests (1.4x the nonsense rate, 22% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.67% of tests (nonsense 0.46%).

Passing tests by cell type: ALL 3, book 5, book_sess 9, sess 5.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | n9_wk_used_lt50 | 27911 | 0.34 | 0.030 | 0.011 | 0.019 | 5.4 | 2.3 | 179 | 4/4 | 0.021 |
| book | M7 |  | n9_fhour_break_with | 5379 | 0.63 | -0.019 | 0.064 | -0.083 | -4.4 | 2.2 | 188 | 0/4 | -0.085 |
| book | M7 |  | n9_fhour_inside | 3044 | 0.36 | 0.065 | -0.019 | 0.084 | 4.3 | 2.2 | 188 | 4/4 | 0.104 |
| sess |  | 0 | n9_wk_used_gt100 | 2337 | 0.24 | 0.003 | 0.089 | -0.085 | -4.0 | 2.8 | 72 | 0/4 | -0.138 |
| sess |  | 0 | n9_mon_ext_against0 | 1561 | 0.18 | -0.072 | 0.092 | -0.164 | -3.7 | 2.8 | 145 | 0/4 | -0.208 |
| book_sess | P7 | 3 | n9_wk_used_gt150 | 194 | 0.04 | -0.154 | 0.014 | -0.168 | -3.6 | 2.9 | 17 | 0/3 | -0.312 |
| book_sess | M7 | 4 | n9_fhour_inside | 1183 | 0.32 | 0.097 | -0.046 | 0.143 | 3.6 | 2.6 | 168 | 4/4 | 0.279 |
| book_sess | M7 | 4 | n9_fhour_break_with | 2482 | 0.68 | -0.046 | 0.097 | -0.143 | -3.6 | 2.6 | 168 | 0/4 | -0.279 |
| sess |  | 0 | n9_mon_ext_against1 | 342 | 0.04 | -0.220 | 0.074 | -0.293 | -3.4 | 2.8 | 43 | 0/4 | -0.278 |
| book_sess | P7 | 0 | n9_mo_pos_bottom20 | 714 | 0.17 | -0.112 | 0.098 | -0.210 | -3.3 | 3.1 | 110 | 0/4 | -0.278 |
| ALL |  |  | n9_mon_ext_with1 | 8872 | 0.13 | 0.074 | 0.007 | 0.068 | -3.2 | 2.3 | 110 | 4/4 | 0.059 |
| book_sess | P7 | 0 | n9_mo_pos_top20 | 1239 | 0.29 | 0.161 | 0.023 | 0.138 | 3.1 | 3.1 | 130 | 4/4 | 0.068 |
| ALL |  |  | n9_amd_dist_against | 2313 | 0.04 | -0.085 | 0.030 | -0.115 | -3.0 | 2.3 | 185 | 0/4 | -0.153 |
| book_sess | A7 | 0 | n9_wk_used_gt100 | 267 | 0.21 | 0.067 | 0.134 | -0.067 | -3.0 | 2.4 | 31 | 0/3 | -0.153 |
| book | A7 |  | n9_amd_acc | 5051 | 0.29 | -0.039 | 0.046 | -0.085 | -2.9 | 2.4 | 189 | 0/4 | -0.050 |
| book_sess | M7 | 4 | n9_ysame_inside | 962 | 0.24 | -0.111 | 0.034 | -0.144 | -2.9 | 2.6 | 129 | 0/4 | -0.228 |
| sess |  | 5 | n9_fhour_inside | 2765 | 0.59 | 0.062 | 0.011 | 0.052 | 2.8 | 2.5 | 166 | 4/4 | 0.045 |
| book | A7 |  | n9_q_in1 | 4691 | 0.27 | -0.040 | 0.044 | -0.083 | -2.8 | 2.4 | 189 | 0/4 | -0.044 |
| book_sess | A7 | 2 | n9_mo_pos_top20 | 455 | 0.39 | -0.215 | 0.031 | -0.246 | -2.7 | 2.5 | 47 | 0/4 | -0.355 |
| book_sess | K7 | 0 | n9_mon_ext_against1 | 130 | 0.05 | -0.182 | 0.043 | -0.225 | -2.7 | 2.3 | 31 | 0/2 | -0.185 |
| sess |  | 3 | n9_mon_ext_against2 | 235 | 0.02 | -0.095 | 0.028 | -0.123 | -2.4 | 2.0 | 23 | 0/2 | -0.071 |
| book | P7 |  | n9_mon_ext_against2 | 423 | 0.02 | -0.086 | 0.016 | -0.103 | -2.3 | 2.2 | 28 | 0/4 | -0.229 |

## Block 13 microstructure

62 conditions, 3100 (condition x cell) tests; passing alone: 14 tests, 11 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.45% of tests (1.0x the nonsense rate, 18% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.48% of tests (nonsense 0.46%).

Passing tests by cell type: book 2, book_sess 6, sess 6.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 1 | n13_vpin_lo | 4444 | 0.26 | 0.066 | 0.010 | 0.055 | 3.4 | 2.5 | 166 | 4/4 | 0.024 |
| book_sess | K7 | 4 | n13_skew15_strong_against | 465 | 0.17 | -0.088 | 0.012 | -0.100 | -3.3 | 2.3 | 114 | 0/4 | -0.114 |
| sess |  | 5 | n13_skew15_strong_against | 1985 | 0.16 | -0.084 | 0.016 | -0.100 | -3.1 | 2.5 | 187 | 0/4 | -0.144 |
| book_sess | P7 | 0 | n13_jump15_with | 273 | 0.06 | -0.033 | 0.075 | -0.108 | -3.1 | 3.1 | 73 | 0/3 | -0.120 |
| book_sess | P7 | 5 | n13_arr300_hi | 892 | 0.18 | -0.064 | 0.020 | -0.084 | -2.8 | 2.6 | 170 | 0/4 | -0.183 |
| sess |  | 2 | n13_jump60_any | 2605 | 0.48 | -0.090 | 0.073 | -0.163 | -2.8 | 2.8 | 158 | 0/4 | -0.352 |
| book_sess | M7 | 2 | n13_arr300_lo | 307 | 0.24 | -0.140 | 0.037 | -0.177 | -2.7 | 2.4 | 79 | 0/4 | -0.265 |
| sess |  | 5 | n13_jump60_any | 2931 | 0.23 | 0.109 | -0.033 | 0.142 | 2.6 | 2.5 | 170 | 4/4 | 0.141 |
| book | A7 |  | n13_skew60_strong_against | 1583 | 0.09 | -0.007 | 0.024 | -0.032 | -2.6 | 2.4 | 174 | 0/4 | -0.069 |
| book_sess | K7 | 0 | n13_vpin_dir_with | 364 | 0.33 | 0.228 | 0.005 | 0.222 | 2.6 | 2.3 | 54 | 3/3 | 0.252 |
| sess |  | 5 | n13_sweep120_any | 1892 | 0.15 | -0.055 | 0.011 | -0.066 | -2.5 | 2.5 | 183 | 0/4 | -0.097 |
| sess |  | 4 | n13_vpin_dir_against | 1516 | 0.08 | 0.068 | -0.007 | 0.075 | 2.5 | 2.4 | 172 | 4/4 | 0.084 |
| book | P7 |  | n13_depth_thin | 3298 | 0.12 | -0.049 | 0.027 | -0.075 | -2.5 | 2.2 | 151 | 0/4 | -0.009 |
| book_sess | P7 | 1 | n13_depth_thin | 345 | 0.07 | -0.071 | 0.024 | -0.094 | -2.3 | 2.2 | 44 | 0/3 | -0.085 |

## Block 16 flow calendar

48 conditions, 2400 (condition x cell) tests; passing alone: 11 tests, 9 distinct conditions. The 200 nonsense controls pass the SAME full rule (bar + years + L6M) in 0.44% of their tests (19% of controls pass in at least one cell); this block passes in 0.46% of tests (1.0x the nonsense rate, 19% of its conditions pass in at least one cell). Sensitivity, universe cut at 2026-10-31: 0.38% of tests (nonsense 0.46%).

Passing tests by cell type: book 2, book_sess 4, sess 5.

| cell | book | sess | condition | n yes | share | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book | U7 |  | n16_first_td_month | 116 | 0.04 | 0.228 | 0.039 | 0.190 | 3.3 | 2.5 | 37 | 2/2 | 0.202 |
| sess |  | 1 | n16_fomc_day | 407 | 0.02 | -0.318 | 0.032 | -0.350 | -3.2 | 2.5 | 27 | 0/4 | -0.225 |
| book_sess | A7 | 2 | n16_first3_td_month | 164 | 0.14 | 0.165 | -0.088 | 0.253 | 3.2 | 2.5 | 19 | 4/4 | 0.334 |
| book_sess | A7 | 1 | n16_fomc_day | 108 | 0.02 | -0.493 | 0.050 | -0.543 | -3.2 | 2.9 | 16 | 0/2 | -0.463 |
| sess |  | 1 | n16_collar_reset_pm1 | 464 | 0.03 | -0.182 | 0.030 | -0.212 | -3.2 | 2.5 | 17 | 0/4 | -0.061 |
| sess |  | 4 | n16_first_td_quarter | 279 | 0.01 | -0.344 | 0.004 | -0.348 | -2.9 | 2.4 | 14 | 0/4 | -0.453 |
| book_sess | K7 | 0 | n16_last_td_month | 166 | 0.05 | 0.136 | 0.039 | 0.097 | 2.8 | 2.3 | 38 | 3/3 | 0.011 |
| sess |  | 2 | n16_day_after_vix_expiry | 294 | 0.05 | -0.282 | 0.011 | -0.292 | -2.8 | 2.8 | 36 | 0/4 | -0.108 |
| book | P7 |  | n16_day_after_quad | 351 | 0.01 | 0.209 | 0.015 | 0.194 | 2.7 | 2.2 | 14 | 4/4 | 0.211 |
| book_sess | P7 | 1 | n16_fomc_day | 125 | 0.03 | -0.374 | 0.026 | -0.400 | -2.7 | 2.2 | 16 | 0/2 | -0.333 |
| sess |  | 3 | n16_fomc_day_after | 544 | 0.03 | -0.127 | 0.028 | -0.155 | -2.1 | 2.0 | 29 | 0/4 | -0.246 |

