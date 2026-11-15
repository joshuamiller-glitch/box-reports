# DS3_CONFLUENCE_ITEMS_CF4_ZW - CF4 conditions (Block 2, IRL/ERL, Blocks 10-12, Block 4 alternate bars) each alone, weekly cluster-robust (zw) with the nonsense bar

**Verdict (data ends 2026-11-11) line (2026-11-15 19:30Z, ): pass-alone rate per block vs nonsense (0.44%): osc 0.66% (1.5x); trend 0.62% (1.4x); smc 0.69% (1.6x); vol 0.58% (1.3x); ml 0.41% (0.9x); irl 0.54% (1.2x); candle 0.25% (0.6x); fp 0.58% (1.3x); geom 0.32% (0.7x). A block at or near 1x nonsense has no single-condition signal beyond the controls.**
RULE (W-CF1, CONFLUENCE_DEFS.md): pass alone only if |zw| (weekly cluster-robust t, >= 8 weeks) exceeds the 99th percentile of |zw| of the 200 nonsense controls c_Z_* IN THE SAME CELL, AND the lift keeps its sign in every calendar year with >= 30 cases per side (>= 2 such years) AND in L6M (>= 15 yes cases). Outcome = R of universe signals with in_pos == 0 (taken + skipped hypothetical), cells ALL, book, session, book x session. Nonsense controls pass the SAME full rule in 0.44% of their tests (CF5 table nonsense_pass_rate.csv). Code: code/th_confl_cf4/cf4_zw.py (machinery of code/th_confl_cf5/cf5_zw.py). November 2026 rows are provisional until W-EV parity.

| block | conditions | tests | passing tests | rate % | x nonsense | % conditions passing in >=1 cell |
|---|---|---|---|---|---|---|
| osc | 3144 | 157200 | 1035 | 0.66 | 1.5 | 24 |
| trend | 3330 | 166500 | 1039 | 0.62 | 1.4 | 24 |
| smc | 2030 | 101500 | 701 | 0.69 | 1.6 | 24 |
| vol | 598 | 29900 | 172 | 0.58 | 1.3 | 18 |
| ml | 222 | 11100 | 46 | 0.41 | 0.9 | 18 |
| irl | 334 | 16700 | 90 | 0.54 | 1.2 | 18 |
| candle | 3370 | 168500 | 429 | 0.25 | 0.6 | 10 |
| fp | 197 | 9850 | 57 | 0.58 | 1.3 | 20 |
| geom | 1188 | 59400 | 192 | 0.32 | 0.7 | 13 |

## osc

3144 conditions, 157200 tests, passing alone: 1035 tests (0.66%, 1.5x the nonsense rate), 759 distinct conditions (24% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 3 | c4_elderF_bull_15m_nodiv | 14655 | 0.044 | -0.099 | 0.144 | 5.4 | 2.0 | 165 | 4/4 | 0.112 |
| sess |  | 3 | c4_elder_bull_15m_nodiv | 14857 | 0.043 | -0.101 | 0.144 | 5.3 | 2.0 | 159 | 4/4 | 0.154 |
| book | M7 |  | c4_tsiF_60m_eleave | 1785 | -0.115 | 0.023 | -0.138 | -5.2 | 2.2 | 176 | 0/4 | -0.139 |
| book_sess | A7 | 3 | c4_elderF_bull_15m_nodiv | 3189 | 0.071 | -0.225 | 0.296 | 5.0 | 2.6 | 92 | 4/4 | 0.402 |
| ALL |  |  | c4_tsiF_60m_eleave | 8408 | -0.055 | 0.027 | -0.082 | -4.9 | 2.3 | 189 | 0/4 | -0.056 |
| sess |  | 5 | c4_kerF_dir_mtf_all | 2069 | -0.070 | 0.015 | -0.085 | -4.8 | 2.5 | 170 | 0/4 | -0.212 |
| book_sess | U7 | 3 | c4_smieF_3m_rise | 466 | 0.061 | 0.122 | -0.061 | -4.8 | 2.9 | 11 | 0/2 | -0.002 |
| ALL |  |  | c4_tsiS_60m_ewith | 9242 | 0.060 | 0.014 | 0.047 | -4.7 | 2.3 | 145 | 4/4 | 0.114 |
| book | A7 |  | c4_wtS_60m_eleave_z2 | 663 | -0.183 | 0.030 | -0.213 | -4.7 | 2.4 | 106 | 0/4 | -0.258 |
| sess |  | 3 | c4_copp_60m_divwith | 2703 | -0.051 | 0.036 | -0.088 | -4.6 | 2.0 | 161 | 0/4 | -0.079 |
| sess |  | 3 | c4_elderF_impulse_1d_hold3 | 2773 | -0.057 | 0.038 | -0.095 | -4.6 | 2.0 | 129 | 0/4 | -0.104 |
| sess |  | 3 | c4_elder_impulse_1d_hold3 | 2532 | -0.076 | 0.040 | -0.116 | -4.6 | 2.0 | 119 | 0/4 | -0.102 |
| sess |  | 3 | c4_elderS_bull_15m_nodiv | 15191 | 0.036 | -0.071 | 0.106 | 4.6 | 2.0 | 147 | 4/4 | 0.157 |
| ALL |  |  | c4_rsima21_60m_ewith | 6473 | 0.112 | 0.011 | 0.101 | -4.6 | 2.3 | 146 | 4/4 | 0.161 |
| sess |  | 5 | c4_ker_dir_15m_ewith | 3220 | -0.074 | 0.027 | -0.101 | -4.5 | 2.5 | 174 | 0/4 | -0.154 |

## trend

3330 conditions, 166500 tests, passing alone: 1039 tests (0.62%, 1.4x the nonsense rate), 803 distinct conditions (24% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 3 | c4_alma_x_1d_fresh1 | 580 | -0.240 | 0.032 | -0.272 | -5.6 | 2.0 | 49 | 0/4 | -0.168 |
| book | A7 |  | c4_ichiF_score_60m_eleave | 2339 | -0.119 | 0.044 | -0.163 | -5.1 | 2.4 | 179 | 0/4 | -0.105 |
| book_sess | H7 | 4 | c4_ichiS_tk_1m_rise | 168 | -0.088 | 0.028 | -0.116 | -4.9 | 2.9 | 20 | 0/4 | -0.210 |
| ALL |  |  | c4_ichiF_score_60m_eleave | 9975 | -0.069 | 0.031 | -0.100 | -4.9 | 2.3 | 188 | 0/4 | -0.104 |
| sess |  | 3 | c4_turt10_60m_fresh1 | 2052 | -0.075 | 0.036 | -0.111 | -4.8 | 2.0 | 166 | 0/4 | -0.050 |
| sess |  | 3 | c4_rfiltF_60m_fresh1 | 1870 | -0.111 | 0.039 | -0.150 | -4.8 | 2.0 | 160 | 0/4 | -0.199 |
| sess |  | 3 | c4_rfiltF_dir_60m_fresh1 | 1870 | -0.111 | 0.039 | -0.150 | -4.8 | 2.0 | 160 | 0/4 | -0.199 |
| book | M7 |  | c4_rfiltF_60m_fresh1 | 1331 | -0.145 | 0.022 | -0.167 | -4.8 | 2.2 | 176 | 0/4 | -0.059 |
| book | M7 |  | c4_rfiltF_dir_60m_fresh1 | 1331 | -0.145 | 0.022 | -0.167 | -4.8 | 2.2 | 176 | 0/4 | -0.059 |
| book_sess | H7 | 0 | c4_ichi_score_1d_rise | 141 | 0.236 | 0.046 | 0.190 | 4.8 | 2.2 | 20 | 3/3 | 0.322 |
| book_sess | M7 | 2 | c4_hullS_60m_rise | 872 | -0.081 | 0.159 | -0.240 | -4.8 | 2.4 | 68 | 0/4 | -0.318 |
| sess |  | 1 | c4_ichiF_score_60m_eleave | 2034 | -0.067 | 0.037 | -0.105 | -4.8 | 2.5 | 160 | 0/4 | -0.016 |
| sess |  | 3 | c4_turt20_60m_fresh1 | 1592 | -0.092 | 0.034 | -0.126 | -4.7 | 2.0 | 143 | 0/4 | -0.033 |
| ALL |  |  | c4_rfiltS_dir_60m_fresh5 | 8562 | -0.048 | 0.026 | -0.075 | -4.6 | 2.3 | 169 | 0/4 | -0.035 |
| ALL |  |  | c4_rfiltS_60m_fresh5 | 8562 | -0.048 | 0.026 | -0.075 | -4.6 | 2.3 | 169 | 0/4 | -0.035 |

## smc

2030 conditions, 101500 tests, passing alone: 701 tests (0.69%, 1.6x the nonsense rate), 490 distinct conditions (24% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | c4_po3_london_1m_hold3 | 19278 | -0.038 | 0.036 | -0.074 | -4.9 | 2.3 | 189 | 0/4 | -0.087 |
| sess |  | 3 | c4_obS_cnt_60m_rise | 2767 | -0.068 | 0.040 | -0.108 | -4.9 | 2.0 | 175 | 0/4 | -0.098 |
| ALL |  |  | c4_po3_london_1m_side | 20527 | -0.036 | 0.037 | -0.072 | -4.8 | 2.3 | 189 | 0/4 | -0.084 |
| ALL |  |  | c4_sfpS_60m_fresh5 | 9981 | -0.035 | 0.026 | -0.061 | -4.7 | 2.3 | 186 | 0/4 | -0.096 |
| sess |  | 4 | c4_ifvgF_in_1d_hold3 | 212 | -0.401 | 0.003 | -0.404 | -4.7 | 2.4 | 15 | 0/4 | -0.152 |
| sess |  | 4 | c4_ifvg_in_1d_hold3 | 212 | -0.401 | 0.003 | -0.404 | -4.7 | 2.4 | 15 | 0/4 | -0.152 |
| sess |  | 1 | c4_struct_15m_fresh5 | 3599 | -0.044 | 0.043 | -0.086 | -4.4 | 2.5 | 183 | 0/4 | -0.069 |
| ALL |  |  | c4_eqpool_upS_5m_rise | 6370 | 0.000 | 0.049 | -0.049 | -4.4 | 2.3 | 137 | 0/4 | -0.072 |
| book_sess | P7 | 0 | c4_fvgF_cnt_5m_fresh5 | 249 | -0.102 | 0.080 | -0.182 | -4.4 | 3.1 | 60 | 0/3 | -0.160 |
| book_sess | K7 | 4 | c4_sfp_3m_fresh5 | 121 | 0.133 | -0.011 | 0.144 | 4.4 | 2.3 | 27 | 3/3 | 0.150 |
| sess |  | 3 | c4_chochF_60m_fresh1 | 1630 | -0.070 | 0.032 | -0.102 | -4.3 | 2.0 | 149 | 0/4 | -0.118 |
| book | P7 |  | c4_po3_london_1m_hold3 | 6196 | -0.047 | 0.036 | -0.083 | -4.2 | 2.2 | 187 | 0/4 | -0.165 |
| book | P7 |  | c4_po3_london_1m_side | 6586 | -0.045 | 0.037 | -0.083 | -4.2 | 2.2 | 187 | 0/4 | -0.168 |
| sess |  | 4 | c4_fvgS_near_60m_against | 5966 | -0.098 | 0.042 | -0.140 | -4.2 | 2.4 | 179 | 0/4 | -0.038 |
| sess |  | 2 | c4_eqpool_dnS_60m_hi | 1016 | -0.047 | 0.289 | -0.336 | -4.1 | 2.8 | 10 | 0/2 | -0.462 |

## vol

598 conditions, 29900 tests, passing alone: 172 tests (0.58%, 1.3x the nonsense rate), 110 distinct conditions (18% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | A7 | 0 | c4_avwap_swing_hi_60m_side | 1210 | 0.092 | 0.275 | -0.183 | -4.2 | 2.4 | 28 | 0/3 | -0.373 |
| sess |  | 5 | c4_avwap_swing_hi_15m_far | 2457 | -0.062 | 0.016 | -0.078 | -3.8 | 2.5 | 167 | 0/4 | -0.030 |
| book_sess | O7 | 3 | c4_cvdF_3m_rise | 371 | 0.176 | 0.376 | -0.201 | -3.8 | 3.7 | 10 | 0/3 | -0.393 |
| book | O7 |  | c4_cvdF_3m_rise | 371 | 0.176 | 0.376 | -0.201 | -3.8 | 3.7 | 10 | 0/3 | -0.393 |
| book | H7 |  | c4_vp_fr240_in_va | 1389 | 0.109 | -0.002 | 0.112 | 3.7 | 2.4 | 189 | 4/4 | 0.053 |
| book_sess | A7 | 0 | c4_avwap_swing_hi_60m_rise | 1187 | 0.094 | 0.236 | -0.142 | -3.7 | 2.4 | 34 | 0/3 | -0.219 |
| sess |  | 5 | c4_avwap_nypm_open_far | 4628 | -0.024 | 0.016 | -0.040 | -3.7 | 2.5 | 187 | 0/4 | -0.096 |
| book_sess | M7 | 2 | c4_cvd_ema_15m_divwith | 154 | -0.252 | 0.029 | -0.281 | -3.7 | 2.4 | 36 | 0/3 | -0.403 |
| ALL |  |  | c4_cvdS_60m_rise | 51502 | 0.000 | 0.049 | -0.049 | -3.6 | 2.3 | 189 | 0/4 | -0.069 |
| book | H7 |  | c4_vp_fr240_va_above | 1823 | -0.002 | 0.108 | -0.109 | -3.6 | 2.4 | 189 | 0/4 | -0.045 |
| book | M7 |  | c4_cvd_60m_rise | 10425 | -0.018 | 0.054 | -0.072 | -3.5 | 2.2 | 189 | 0/4 | -0.058 |
| book_sess | A7 | 1 | c4_cvd_ema_3m_side | 5080 | 0.031 | 0.155 | -0.124 | -3.5 | 2.9 | 82 | 0/4 | -0.183 |
| sess |  | 3 | c4_vsa_climax_3m_side | 100 | 0.323 | 0.021 | 0.302 | 3.5 | 2.0 | 28 | 2/2 | 0.278 |
| sess |  | 3 | c4_vsa_climax_3m_fresh1 | 100 | 0.323 | 0.021 | 0.302 | 3.5 | 2.0 | 28 | 2/2 | 0.278 |
| book_sess | A7 | 3 | c4_delta_ratio_5m_fresh5 | 3238 | 0.061 | -0.178 | 0.239 | 3.5 | 2.6 | 105 | 4/4 | 0.431 |

## ml

222 conditions, 11100 tests, passing alone: 46 tests (0.41%, 0.9x the nonsense rate), 40 distinct conditions (18% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | H7 | 0 | c4_lorS_1m_flip3 | 202 | -0.031 | 0.128 | -0.159 | -3.7 | 2.2 | 45 | 0/4 | -0.241 |
| sess |  | 5 | c4_kr_dir_3m_fresh1 | 311 | 0.079 | -0.001 | 0.080 | 3.4 | 2.5 | 80 | 4/4 | 0.016 |
| book_sess | A7 | 2 | c4_lorF_1m_flip3 | 310 | 0.105 | -0.108 | 0.213 | 3.3 | 2.5 | 74 | 4/4 | 0.257 |
| book_sess | K7 | 5 | c4_lorF_60m_side | 720 | -0.113 | 0.038 | -0.151 | -3.2 | 2.6 | 132 | 0/4 | -0.140 |
| book_sess | K7 | 3 | c4_lor_5m_flip3 | 932 | -0.074 | 0.036 | -0.111 | -3.2 | 2.3 | 170 | 0/4 | -0.076 |
| book_sess | M7 | 2 | c4_kr_dir_mtf_ge4 | 1175 | -0.018 | 0.140 | -0.158 | -3.1 | 2.4 | 26 | 0/2 | -0.188 |
| book_sess | P7 | 0 | c4_krS_dir_5m_side | 4122 | 0.090 | -0.066 | 0.156 | 3.1 | 3.1 | 121 | 4/4 | 0.167 |
| book | A7 |  | c4_lorF_1m_rise | 6418 | 0.040 | 0.011 | 0.029 | 2.9 | 2.4 | 189 | 4/4 | 0.011 |
| book | K7 |  | c4_lorF_1m_flip3 | 3921 | -0.030 | 0.024 | -0.054 | -2.9 | 2.6 | 188 | 0/4 | -0.021 |
| book_sess | H7 | 1 | c4_krF_px_60m_side | 703 | 0.099 | -0.124 | 0.223 | 2.9 | 2.9 | 49 | 4/4 | 0.157 |
| book_sess | M7 | 2 | c4_kr_px_mtf_ge4 | 1184 | -0.015 | 0.122 | -0.137 | -2.9 | 2.4 | 22 | 0/2 | -0.265 |
| book | H7 |  | c4_krF_dir_60m_rise | 1526 | -0.002 | 0.089 | -0.091 | -2.9 | 2.4 | 188 | 0/4 | -0.147 |
| book | H7 |  | c4_lor_60m_flip3 | 948 | 0.113 | 0.018 | 0.096 | 2.8 | 2.4 | 184 | 4/4 | 0.074 |
| sess |  | 5 | c4_lorS_60m_rise | 4662 | -0.057 | 0.035 | -0.093 | -2.8 | 2.5 | 189 | 0/4 | -0.040 |
| book | H7 |  | c4_kr_px_1d_side | 1774 | 0.077 | 0.010 | 0.067 | 2.8 | 2.4 | 181 | 4/4 | 0.047 |

## irl

334 conditions, 16700 tests, passing alone: 90 tests (0.54%, 1.2x the nonsense rate), 61 distinct conditions (18% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book | M7 |  | c4_irl_e15_10_ext_fade_60 | 284 | -0.227 | 0.012 | -0.239 | -3.5 | 2.2 | 75 | 0/4 | -0.199 |
| ALL |  |  | c4_irl_e60_10_ext_fade_30 | 124 | -0.347 | 0.019 | -0.366 | -3.5 | 2.3 | 28 | 0/2 | -0.295 |
| sess |  | 4 | c4_irl_e15_20_int_against_60 | 6598 | -0.065 | 0.032 | -0.098 | -3.5 | 2.4 | 181 | 0/4 | -0.278 |
| book_sess | H7 | 5 | c4_irl_e15_10_int_fade_60 | 117 | 0.098 | -0.022 | 0.121 | 3.5 | 1.6 | 9 | 3/3 | 0.216 |
| sess |  | 4 | c4_irl_a_pd_int_against_60 | 6776 | -0.091 | 0.048 | -0.139 | -3.4 | 2.4 | 182 | 0/4 | -0.130 |
| book | A7 |  | c4_irl_c_on_int_against_60 | 3396 | -0.044 | 0.038 | -0.082 | -3.3 | 2.4 | 185 | 0/4 | -0.093 |
| ALL |  |  | c4_irl_f_or60_ext_fade_60 | 1431 | -0.084 | 0.021 | -0.105 | -3.3 | 2.3 | 148 | 0/4 | -0.024 |
| book_sess | A7 | 0 | c4_irl_e240_20_int_against_60 | 560 | 0.178 | 0.064 | 0.114 | 3.3 | 2.4 | 65 | 3/3 | 0.062 |
| book_sess | U7 | 0 | c4_irl_b_ps_int_fade_60 | 193 | 0.002 | 0.117 | -0.115 | -3.2 | 2.9 | 40 | 0/3 | -0.120 |
| book_sess | U7 | 0 | c4_irl_a_pd_int_fade_60 | 193 | 0.002 | 0.117 | -0.115 | -3.2 | 2.9 | 40 | 0/3 | -0.120 |
| book | M7 |  | c4_irl_any_ext_fade_15 | 209 | -0.246 | 0.012 | -0.258 | -3.2 | 2.2 | 57 | 0/4 | -0.216 |
| sess |  | 4 | c4_irl_e15_20_int_against_30 | 4500 | -0.063 | 0.018 | -0.081 | -3.2 | 2.4 | 180 | 0/4 | -0.232 |
| sess |  | 4 | c4_irl_a_pd_int_against_5 | 1217 | -0.131 | 0.008 | -0.138 | -3.1 | 2.4 | 157 | 0/4 | -0.179 |
| sess |  | 4 | c4_irl_e60_20_int_against_30 | 6080 | -0.077 | 0.034 | -0.111 | -3.1 | 2.4 | 181 | 0/4 | -0.030 |
| book_sess | M7 | 5 | c4_irl_b_ps_int_fade_15 | 183 | 0.205 | 0.006 | 0.199 | 3.1 | 2.8 | 45 | 4/4 | 0.292 |

## candle

3370 conditions, 168500 tests, passing alone: 429 tests (0.25%, 0.6x the nonsense rate), 330 distinct conditions (10% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 2 | c4_cdl_hammer_5m_against | 118 | 0.323 | -0.011 | 0.335 | 5.4 | 2.8 | 30 | 2/2 | 0.315 |
| book | A7 |  | c4_cdl_pin_bar_1d_side | 823 | -0.143 | 0.030 | -0.172 | -5.0 | 2.4 | 63 | 0/4 | -0.071 |
| book | A7 |  | c4_cdl_pin_bar_1d_fresh1 | 823 | -0.143 | 0.030 | -0.172 | -5.0 | 2.4 | 63 | 0/4 | -0.071 |
| book_sess | M7 | 3 | c4_cdl_tweezer_1m_against3 | 387 | 0.152 | -0.014 | 0.166 | 4.8 | 2.6 | 101 | 4/4 | 0.223 |
| sess |  | 1 | c4_cdl_harami_5m_fresh3_atlvl | 123 | 0.310 | 0.023 | 0.287 | 4.7 | 2.5 | 30 | 2/2 | 0.253 |
| sess |  | 1 | c4_cdl_hammer_mtf_n | 786 | -0.187 | 0.035 | -0.222 | -4.6 | 2.5 | 112 | 0/4 | -0.277 |
| book | A7 |  | c4_cdl_tweezer_1d_fresh1 | 582 | -0.169 | 0.028 | -0.197 | -4.5 | 2.4 | 58 | 0/4 | -0.162 |
| book | A7 |  | c4_cdl_tweezer_1d_side | 582 | -0.169 | 0.028 | -0.197 | -4.5 | 2.4 | 58 | 0/4 | -0.162 |
| book | K7 |  | c4_cdl_three_line_strike_5m_against | 133 | -0.165 | 0.012 | -0.177 | -4.5 | 2.6 | 31 | 0/3 | -0.219 |
| book | M7 |  | c4_cdl_wide_range_trend_1d_side | 665 | -0.146 | 0.015 | -0.160 | -4.4 | 2.2 | 56 | 0/4 | -0.010 |
| book | M7 |  | c4_cdl_wide_range_trend_1d_fresh1 | 665 | -0.146 | 0.015 | -0.160 | -4.4 | 2.2 | 56 | 0/4 | -0.010 |
| book | H7 |  | c4_cdl_shooting_star_5m_against5 | 464 | 0.174 | 0.024 | 0.150 | 4.3 | 2.4 | 122 | 4/4 | 0.092 |
| book | A7 |  | c4_cdl_opening_marubozu_1d_against | 562 | -0.199 | 0.029 | -0.228 | -4.3 | 2.4 | 53 | 0/4 | -0.301 |
| ALL |  |  | c4_cdl_tweezer_1d_fresh1 | 3309 | -0.069 | 0.022 | -0.091 | -4.3 | 2.3 | 68 | 0/4 | -0.091 |
| ALL |  |  | c4_cdl_tweezer_1d_side | 3309 | -0.069 | 0.022 | -0.091 | -4.3 | 2.3 | 68 | 0/4 | -0.091 |

## fp

197 conditions, 9850 tests, passing alone: 57 tests (0.58%, 1.3x the nonsense rate), 40 distinct conditions (20% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | P7 | 4 | c4_fp_1m_poc_against | 1191 | 0.076 | -0.019 | 0.094 | 4.2 | 2.5 | 184 | 4/4 | 0.118 |
| book_sess | P7 | 0 | c4_fp_5m_poc_mig3 | 2761 | 0.041 | 0.114 | -0.073 | -3.6 | 3.1 | 182 | 0/4 | -0.035 |
| book_sess | P7 | 4 | c4_fp_1m_poc_mig1 | 6032 | -0.012 | 0.073 | -0.086 | -3.5 | 2.5 | 170 | 0/4 | -0.037 |
| book_sess | A7 | 3 | c4_fp_5m_poc_mig1 | 2857 | 0.009 | 0.119 | -0.111 | -3.5 | 2.6 | 160 | 0/4 | -0.130 |
| book | A7 |  | c4_fp_15m_unf_ahead3 | 5167 | -0.028 | 0.043 | -0.071 | -3.4 | 2.4 | 189 | 0/4 | -0.162 |
| book | A7 |  | c4_fp_mtf_delta_with_ge3 | 14654 | 0.010 | 0.087 | -0.077 | -3.3 | 2.4 | 187 | 0/4 | -0.140 |
| book | M7 |  | c4_fp_mtf_delta_with_ge3 | 12842 | -0.008 | 0.067 | -0.075 | -3.2 | 2.2 | 189 | 0/4 | -0.066 |
| book_sess | U7 | 1 | c4_fp_15m_stack3_with3 | 154 | 0.169 | 0.009 | 0.159 | 3.2 | 2.3 | 33 | 3/3 | 0.222 |
| book_sess | A7 | 1 | c4_fp_3m_delta_with5 | 4715 | 0.024 | 0.135 | -0.110 | -3.2 | 2.9 | 138 | 0/4 | -0.202 |
| book | A7 |  | c4_fp_1m_delta_with5 | 12733 | 0.008 | 0.058 | -0.050 | -3.2 | 2.4 | 189 | 0/4 | -0.124 |
| book_sess | A7 | 3 | c4_fp_5m_poc_against | 556 | 0.145 | 0.013 | 0.132 | 3.2 | 2.6 | 135 | 4/4 | 0.099 |
| book_sess | A7 | 1 | c4_fp_15m_dbot_with | 2220 | -0.029 | 0.088 | -0.117 | -3.1 | 2.9 | 182 | 0/4 | -0.172 |
| ALL |  |  | c4_fp_mtf_delta_with_ge3 | 64394 | 0.010 | 0.049 | -0.039 | -3.1 | 2.3 | 189 | 0/4 | -0.064 |
| sess |  | 3 | c4_fp_mtf_delta_with_ge3 | 13580 | 0.006 | 0.085 | -0.080 | -3.0 | 2.0 | 188 | 0/4 | -0.140 |
| book_sess | M7 | 3 | c4_fp_mtf_delta_with_ge3 | 2769 | -0.029 | 0.127 | -0.156 | -3.0 | 2.6 | 146 | 0/4 | -0.220 |

## geom

1188 conditions, 59400 tests, passing alone: 192 tests (0.32%, 0.7x the nonsense rate), 150 distinct conditions (13% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 0 | c4_flag_5m_against | 870 | -0.093 | 0.084 | -0.177 | -5.4 | 2.8 | 171 | 0/4 | -0.097 |
| book | K7 |  | c4_fib_clusterS_60m_hi_z1 | 1286 | 0.072 | 0.004 | 0.068 | 4.7 | 2.6 | 144 | 4/4 | 0.016 |
| book_sess | K7 | 1 | c4_chan_pos_60m_eagainst | 298 | -0.200 | 0.039 | -0.239 | -4.5 | 2.4 | 53 | 0/3 | -0.214 |
| book_sess | H7 | 1 | c4_chan_posS_60m_fresh5 | 126 | 0.238 | 0.021 | 0.217 | 4.4 | 2.9 | 26 | 2/2 | 0.314 |
| sess |  | 0 | c4_flag_3m_against | 711 | -0.098 | 0.081 | -0.179 | -4.2 | 2.8 | 157 | 0/4 | -0.261 |
| sess |  | 3 | c4_threeline_60m_fresh1 | 1958 | -0.086 | 0.037 | -0.123 | -4.1 | 2.0 | 159 | 0/4 | -0.174 |
| book_sess | M7 | 5 | c4_chan_pos_3m_eagainst | 462 | -0.154 | 0.043 | -0.197 | -3.9 | 2.8 | 118 | 0/4 | -0.293 |
| sess |  | 0 | c4_fib_ext_upS_3m_rise | 5364 | 0.096 | 0.042 | 0.054 | 3.9 | 2.8 | 189 | 4/4 | 0.043 |
| book_sess | P7 | 0 | c4_pnf_3m_fresh1 | 170 | -0.082 | 0.076 | -0.158 | -3.9 | 3.1 | 39 | 0/2 | -0.335 |
| book | A7 |  | c4_kagi_60m_fresh1 | 833 | -0.125 | 0.029 | -0.154 | -3.8 | 2.4 | 138 | 0/4 | -0.076 |
| ALL |  |  | c4_flag_60m_against | 7751 | -0.018 | 0.022 | -0.040 | -3.8 | 2.3 | 188 | 0/4 | -0.058 |
| ALL |  |  | c4_chan_pos_60m_eleave | 8982 | -0.041 | 0.026 | -0.067 | -3.7 | 2.3 | 189 | 0/4 | -0.027 |
| book_sess | K7 | 4 | c4_tl_dist_upS_5m_hi_z1 | 425 | -0.074 | 0.081 | -0.155 | -3.7 | 2.3 | 47 | 0/3 | -0.137 |
| book_sess | P7 | 0 | c4_flag_3m_against | 385 | -0.134 | 0.089 | -0.223 | -3.7 | 3.1 | 105 | 0/4 | -0.322 |
| book | M7 |  | c4_tl_slope_up_15m_side | 3428 | -0.012 | 0.014 | -0.026 | -3.7 | 2.2 | 186 | 0/4 | -0.076 |

