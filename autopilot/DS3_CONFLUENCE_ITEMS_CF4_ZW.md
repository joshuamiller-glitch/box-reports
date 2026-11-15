# DS3_CONFLUENCE_ITEMS_CF4_ZW - CF4 conditions (Block 2, IRL/ERL, Blocks 10-12, Block 4 alternate bars) each alone, weekly cluster-robust (zw) with the nonsense bar

**Verdict (data ends 2026-11-11) line (2026-11-15 20:37Z, ): pass-alone rate per block vs nonsense (0.44%): osc 0.66% (1.5x); trend 0.62% (1.4x); smc 0.69% (1.6x); vol 0.58% (1.3x); ml 0.41% (0.9x); irl 0.54% (1.2x); candle 0.25% (0.6x); fp 0.58% (1.3x); geom 0.32% (0.7x); alt_ha1 0.52% (1.2x); alt_ha15 0.61% (1.4x); alt_ha3 0.58% (1.3x); alt_ha5 0.80% (1.8x); alt_ha60 0.89% (2.0x); alt_range16 0.64% (1.5x); alt_range8 0.91% (2.1x); alt_renko16 0.61% (1.4x); alt_renko8 0.58% (1.3x); alt_tick2000 0.78% (1.8x); alt_vol2000 0.57% (1.3x); alt_vol500 0.63% (1.4x); altagree 0.32% (0.7x); altagree_ctrl 0.56% (1.3x). A block at or near 1x nonsense has no single-condition signal beyond the controls.**
POWER (planted-edge check, autopilot/CF4_PLANT.md): the same pipeline finds a planted condition with a binary lift of ~0.03-0.05 R per signal in the pooled cell, ~0.1-0.17 R in book / session cells and ~0.17-0.28 R in book x session cells; real passers have median |lift| well below the book x session floor, so absence of a clear pass means no detectable single-condition edge of that size, not no edge. Where the top passers pass and how many are near-duplicates: autopilot/CF4_ZW_TOP.md.

MULTI-BAR-TYPE AGREEMENT (altagree): a condition true on >=3 (or >=6) of the 12 alternate-bar sets counts once; altagree_ctrl = the same construction with independently drawn random condition columns per set. The real agreement block passes at 0.32% of tests versus 0.56% for its control and 0.44% for the nonsense controls: bar-type agreement adds nothing.

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
| alt_ha1 | 2311 | 115550 | 597 | 0.52 | 1.2 | 20 |
| alt_ha15 | 2311 | 115550 | 700 | 0.61 | 1.4 | 23 |
| alt_ha3 | 2311 | 115550 | 675 | 0.58 | 1.3 | 23 |
| alt_ha5 | 2311 | 115550 | 923 | 0.80 | 1.8 | 29 |
| alt_ha60 | 2311 | 115550 | 1028 | 0.89 | 2.0 | 28 |
| alt_range16 | 2311 | 115550 | 738 | 0.64 | 1.5 | 25 |
| alt_range8 | 2311 | 115550 | 1055 | 0.91 | 2.1 | 32 |
| alt_renko16 | 2311 | 115550 | 702 | 0.61 | 1.4 | 22 |
| alt_renko8 | 2311 | 115550 | 674 | 0.58 | 1.3 | 23 |
| alt_tick2000 | 2311 | 115550 | 898 | 0.78 | 1.8 | 30 |
| alt_vol2000 | 2311 | 115550 | 657 | 0.57 | 1.3 | 24 |
| alt_vol500 | 2311 | 115550 | 732 | 0.63 | 1.4 | 24 |
| altagree | 4622 | 231100 | 751 | 0.32 | 0.7 | 13 |
| altagree_ctrl | 4622 | 231100 | 1283 | 0.56 | 1.3 | 22 |

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

## alt_ha1

2311 conditions, 115550 tests, passing alone: 597 tests (0.52%, 1.2x the nonsense rate), 468 distinct conditions (20% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | K7 | 3 | c4_eqpool_up_ha1_hi | 388 | -0.096 | 0.136 | -0.232 | -4.5 | 2.3 | 42 | 0/4 | -0.155 |
| book_sess | M7 | 3 | c4_w1_mom20_ha1_fresh5 | 970 | -0.095 | 0.042 | -0.137 | -4.4 | 2.6 | 173 | 0/4 | -0.223 |
| book_sess | M7 | 3 | c4_w1_roc20_ha1_fresh5 | 970 | -0.095 | 0.042 | -0.137 | -4.4 | 2.6 | 173 | 0/4 | -0.223 |
| book_sess | K7 | 3 | c4_sdF_dsup_ha1_hi | 182 | 0.274 | -0.005 | 0.279 | 4.4 | 2.3 | 52 | 3/3 | 0.196 |
| book_sess | M7 | 3 | c4_rviS_ha1_side | 2813 | 0.029 | -0.094 | 0.123 | 4.3 | 2.6 | 155 | 4/4 | 0.194 |
| book_sess | P7 | 3 | c4_w1_trendcolor_ha1_divwith | 711 | -0.111 | 0.027 | -0.138 | -4.2 | 2.9 | 154 | 0/4 | -0.077 |
| book_sess | K7 | 1 | c4_zlema_px_ha1_nodiv | 2141 | 0.034 | -0.056 | 0.089 | 4.2 | 2.4 | 111 | 4/4 | 0.067 |
| sess |  | 3 | c4_srsi_ha1_eleave | 2785 | -0.050 | 0.037 | -0.086 | -4.2 | 2.0 | 188 | 0/4 | -0.121 |
| sess |  | 3 | c4_w1_stochrsi14_ha1_eleave | 2785 | -0.050 | 0.037 | -0.086 | -4.2 | 2.0 | 188 | 0/4 | -0.121 |
| book_sess | U7 | 3 | c4_rsima7_ha1_ewith | 433 | 0.035 | 0.192 | -0.157 | -4.0 | 2.9 | 19 | 0/2 | -0.074 |
| book_sess | U7 | 3 | c4_w1_rsi7_ha1_ewith | 433 | 0.035 | 0.192 | -0.157 | -4.0 | 2.9 | 19 | 0/2 | -0.074 |
| book_sess | K7 | 1 | c4_w1_vwma200_px_ha1_divwith | 121 | -0.192 | 0.023 | -0.215 | -3.9 | 2.4 | 25 | 0/2 | -0.203 |
| book | M7 |  | c4_w1_eom14_ha1_nodiv | 12782 | 0.023 | -0.040 | 0.063 | 3.9 | 2.2 | 189 | 4/4 | 0.051 |
| book_sess | M7 | 5 | c4_w1_obv_ha1_rise | 2573 | -0.004 | 0.077 | -0.081 | -3.9 | 2.8 | 169 | 0/4 | -0.042 |
| sess |  | 3 | c4_rviS_ha1_side | 14580 | 0.040 | -0.071 | 0.111 | 3.8 | 2.0 | 188 | 4/4 | 0.145 |

## alt_ha15

2311 conditions, 115550 tests, passing alone: 700 tests (0.61%, 1.4x the nonsense rate), 535 distinct conditions (23% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 5 | c4_w1_mfi7_ha15_ewith | 3954 | -0.071 | 0.034 | -0.106 | -4.9 | 2.5 | 183 | 0/4 | -0.092 |
| book_sess | U7 | 1 | c4_w1_kama200_px_ha15_fresh5 | 103 | 0.178 | 0.001 | 0.177 | 4.7 | 2.3 | 13 | 3/3 | 0.076 |
| book_sess | P7 | 2 | c4_hullS_ha15_rise | 1375 | -0.016 | 0.231 | -0.247 | -4.6 | 2.4 | 64 | 0/3 | -0.576 |
| sess |  | 3 | c4_w1_cci20_ha15_nodiv | 14641 | 0.035 | -0.046 | 0.081 | 4.5 | 2.0 | 167 | 4/4 | 0.024 |
| book_sess | H7 | 0 | c4_w1_mfi7_ha15_nodiv | 596 | 0.099 | 0.006 | 0.093 | 4.5 | 2.2 | 21 | 2/2 | 0.309 |
| sess |  | 3 | c4_w1_cci14_ha15_nodiv | 14446 | 0.037 | -0.050 | 0.087 | 4.5 | 2.0 | 171 | 4/4 | 0.064 |
| sess |  | 5 | c4_sqzmF_on_ha15_hi | 8934 | 0.036 | -0.086 | 0.121 | 4.5 | 2.5 | 179 | 4/4 | 0.071 |
| sess |  | 1 | c4_fvg_in_ha15_fresh5 | 129 | -0.298 | 0.028 | -0.325 | -4.4 | 2.5 | 25 | 0/2 | -0.122 |
| sess |  | 4 | c4_wtS_ha15_nodiv | 17333 | 0.011 | -0.105 | 0.115 | 4.4 | 2.4 | 142 | 4/4 | 0.042 |
| book | H7 |  | c4_smieS_ha15_fresh5 | 624 | -0.084 | 0.077 | -0.161 | -4.4 | 2.4 | 150 | 0/4 | -0.159 |
| book_sess | A7 | 3 | c4_elderF_bull_ha15_nodiv | 3146 | 0.064 | -0.155 | 0.218 | 4.3 | 2.6 | 93 | 4/4 | 0.416 |
| book_sess | K7 | 1 | c4_elderS_impulse_ha15_side | 1215 | 0.059 | -0.022 | 0.082 | 4.3 | 2.4 | 138 | 4/4 | 0.021 |
| sess |  | 5 | c4_w1_mfi14_ha15_ewith | 1760 | -0.125 | 0.021 | -0.147 | -4.2 | 2.5 | 134 | 0/4 | -0.370 |
| sess |  | 3 | c4_almaS_px_ha15_nodiv | 14731 | 0.034 | -0.041 | 0.075 | 4.2 | 2.0 | 156 | 4/4 | 0.073 |
| sess |  | 3 | c4_ker_dir_ha15_nodiv | 14127 | 0.035 | -0.032 | 0.067 | 4.2 | 2.0 | 173 | 4/4 | 0.054 |

## alt_ha3

2311 conditions, 115550 tests, passing alone: 675 tests (0.58%, 1.3x the nonsense rate), 528 distinct conditions (23% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | H7 | 0 | c4_w1_aroon14_ha3_rise | 357 | 0.170 | -0.003 | 0.172 | 5.0 | 2.2 | 50 | 4/4 | 0.255 |
| book_sess | K7 | 1 | c4_wtF_ha3_divwith | 216 | -0.233 | 0.034 | -0.267 | -4.7 | 2.4 | 52 | 0/3 | -0.379 |
| book_sess | K7 | 1 | c4_w1_wave_mid_hist_ha3_divwith | 275 | -0.221 | 0.039 | -0.261 | -4.6 | 2.4 | 58 | 0/3 | -0.321 |
| book_sess | K7 | 1 | c4_w1_macd12_26_9_hist_ha3_divwith | 275 | -0.221 | 0.039 | -0.261 | -4.6 | 2.4 | 58 | 0/3 | -0.321 |
| book_sess | M7 | 1 | c4_sebS_ha3_eleave | 98 | -0.012 | 0.011 | -0.023 | -4.6 | 2.7 | 19 | 0/2 | -0.057 |
| book_sess | K7 | 1 | c4_smieF_ha3_divwith | 244 | -0.219 | 0.036 | -0.256 | -4.6 | 2.4 | 53 | 0/3 | -0.361 |
| book_sess | K7 | 1 | c4_qqeF_ha3_divwith | 225 | -0.231 | 0.035 | -0.266 | -4.4 | 2.4 | 51 | 0/3 | -0.319 |
| book_sess | K7 | 1 | c4_srsiS_ha3_divwith | 268 | -0.205 | 0.037 | -0.242 | -4.3 | 2.4 | 59 | 0/3 | -0.392 |
| book_sess | K7 | 1 | c4_w1_stochrsi21_ha3_divwith | 268 | -0.205 | 0.037 | -0.242 | -4.3 | 2.4 | 59 | 0/3 | -0.392 |
| book_sess | K7 | 1 | c4_almaS_px_ha3_divwith | 229 | -0.198 | 0.033 | -0.231 | -4.3 | 2.4 | 53 | 0/2 | -0.328 |
| book | U7 |  | c4_w1_cci14_ha3_ewith_z1 | 2321 | 0.060 | -0.060 | 0.121 | 4.3 | 2.5 | 82 | 4/4 | 0.073 |
| book_sess | U7 | 3 | c4_almaS_slope_ha3_fresh5 | 239 | 0.185 | -0.009 | 0.194 | 4.2 | 2.9 | 32 | 4/4 | 0.183 |
| book_sess | K7 | 1 | c4_w1_mfi14_ha3_divwith | 284 | -0.182 | 0.036 | -0.218 | -4.1 | 2.4 | 62 | 0/3 | -0.218 |
| book_sess | K7 | 4 | c4_eqpool_dnS_ha3_rise | 216 | -0.212 | -0.029 | -0.183 | -4.1 | 2.3 | 27 | 0/2 | -0.397 |
| book_sess | K7 | 1 | c4_sqzmS_bright_ha3_side | 1384 | 0.060 | -0.033 | 0.093 | 4.1 | 2.4 | 143 | 4/4 | 0.113 |

## alt_ha5

2311 conditions, 115550 tests, passing alone: 923 tests (0.80%, 1.8x the nonsense rate), 662 distinct conditions (29% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 5 | c4_kerS_dir_ha5_ewith | 1762 | -0.087 | 0.015 | -0.102 | -4.6 | 2.5 | 144 | 0/4 | -0.062 |
| book | U7 |  | c4_w1_hma100_px_ha5_rise | 2485 | 0.054 | -0.128 | 0.182 | 4.5 | 2.5 | 13 | 2/2 | 0.061 |
| book_sess | K7 | 2 | c4_w1_adx7_ha5_hi_z1 | 846 | -0.041 | 0.378 | -0.419 | -4.3 | 2.3 | 18 | 0/2 | -0.436 |
| book | P7 |  | c4_seb_ha5_eenter | 1252 | -0.111 | 0.024 | -0.135 | -4.3 | 2.2 | 178 | 0/4 | -0.175 |
| book | H7 |  | c4_w1_sqz_hist_ha5_divwith | 281 | 0.225 | 0.029 | 0.197 | 4.2 | 2.4 | 90 | 4/4 | 0.125 |
| book | H7 |  | c4_sqzm_mom_ha5_divwith | 281 | 0.225 | 0.029 | 0.197 | 4.2 | 2.4 | 90 | 4/4 | 0.125 |
| sess |  | 0 | c4_rfilt_dir_ha5_side | 8393 | 0.095 | -0.024 | 0.119 | 4.2 | 2.8 | 188 | 4/4 | 0.060 |
| sess |  | 0 | c4_rfilt_dir_ha5_against | 2336 | -0.024 | 0.095 | -0.119 | -4.2 | 2.8 | 188 | 0/4 | -0.060 |
| book_sess | M7 | 1 | c4_wtS_ha5_eenter_z1 | 105 | 0.137 | 0.006 | 0.130 | 4.2 | 2.7 | 20 | 2/2 | 0.244 |
| book_sess | K7 | 1 | c4_w1_stoch14_ha5_rise | 1825 | -0.027 | 0.093 | -0.120 | -4.1 | 2.4 | 141 | 0/4 | -0.003 |
| book | A7 |  | c4_w1_donchian10_pos_ha5_divwith | 1395 | -0.082 | 0.031 | -0.113 | -4.1 | 2.4 | 165 | 0/4 | -0.128 |
| book | A7 |  | c4_w1_kama34_px_ha5_divwith | 935 | -0.151 | 0.032 | -0.182 | -4.1 | 2.4 | 141 | 0/4 | -0.162 |
| book_sess | A7 | 5 | c4_elderF_bear_ha5_divwith | 131 | 0.314 | -0.052 | 0.366 | 4.1 | 2.4 | 24 | 2/2 | 0.488 |
| book_sess | M7 | 3 | c4_rfilt_ha5_side | 2902 | 0.023 | -0.082 | 0.105 | 4.0 | 2.6 | 155 | 4/4 | 0.109 |
| book | H7 |  | c4_w1_hma8_px_ha5_divwith | 958 | 0.122 | 0.014 | 0.108 | 4.0 | 2.4 | 180 | 4/4 | 0.060 |

## alt_ha60

2311 conditions, 115550 tests, passing alone: 1028 tests (0.89%, 2.0x the nonsense rate), 646 distinct conditions (28% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | c4_smie_ha60_eleave | 6542 | -0.094 | 0.028 | -0.123 | -5.9 | 2.3 | 189 | 0/4 | -0.101 |
| book | A7 |  | c4_w1_rsi21_ha60_eleave | 969 | -0.155 | 0.032 | -0.187 | -5.4 | 2.4 | 121 | 0/4 | -0.249 |
| book | A7 |  | c4_rsima21_ha60_eleave | 972 | -0.155 | 0.032 | -0.187 | -5.4 | 2.4 | 121 | 0/4 | -0.249 |
| book | A7 |  | c4_elderF_bear_ha60_divwith | 2476 | -0.072 | 0.037 | -0.108 | -5.3 | 2.4 | 173 | 0/4 | -0.035 |
| book | A7 |  | c4_ker_dir_ha60_divwith | 2715 | -0.081 | 0.040 | -0.121 | -5.3 | 2.4 | 168 | 0/4 | -0.115 |
| book | A7 |  | c4_w1_trix8_ha60_divwith | 2506 | -0.076 | 0.038 | -0.114 | -5.2 | 2.4 | 169 | 0/4 | -0.056 |
| ALL |  |  | c4_w1_cmo14_ha60_eleave | 8921 | -0.068 | 0.029 | -0.097 | -5.2 | 2.3 | 189 | 0/4 | -0.144 |
| book | A7 |  | c4_w1_aroon50_ha60_eagainst | 2187 | -0.108 | 0.040 | -0.148 | -5.1 | 2.4 | 174 | 0/4 | -0.101 |
| sess |  | 3 | c4_tsi_ha60_divwith | 1438 | -0.071 | 0.032 | -0.103 | -5.1 | 2.0 | 113 | 0/4 | -0.006 |
| book | M7 |  | c4_w1_cmo14_ha60_eleave | 1890 | -0.120 | 0.025 | -0.145 | -4.9 | 2.2 | 181 | 0/4 | -0.178 |
| book_sess | A7 | 4 | c4_ker_dir_ha60_divwith | 856 | -0.183 | 0.049 | -0.232 | -4.9 | 2.5 | 98 | 0/4 | -0.251 |
| sess |  | 3 | c4_w1_trix8_ha60_divwith | 2266 | -0.072 | 0.037 | -0.109 | -4.9 | 2.0 | 152 | 0/4 | -0.180 |
| book | M7 |  | c4_smie_ha60_eleave | 1413 | -0.121 | 0.020 | -0.141 | -4.9 | 2.2 | 163 | 0/4 | -0.152 |
| book | A7 |  | c4_tsiF_ha60_eleave | 1822 | -0.083 | 0.034 | -0.117 | -4.9 | 2.4 | 168 | 0/4 | -0.092 |
| book_sess | U7 | 1 | c4_t3_px_ha60_nodiv | 596 | 0.069 | -0.114 | 0.183 | 4.9 | 2.3 | 14 | 2/2 | 0.154 |

## alt_range16

2311 conditions, 115550 tests, passing alone: 738 tests (0.64%, 1.5x the nonsense rate), 574 distinct conditions (25% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | H7 | 1 | c4_kerF_dir_range16_eagainst | 119 | 0.215 | 0.027 | 0.189 | 4.7 | 2.9 | 23 | 2/2 | 0.030 |
| book_sess | K7 | 2 | c4_ichi_chikou_range16_side | 814 | 0.032 | -0.219 | 0.251 | 4.5 | 2.3 | 22 | 2/2 | 0.229 |
| book_sess | P7 | 2 | c4_w1_trix30_range16_divwith | 309 | -0.163 | 0.070 | -0.233 | -4.3 | 2.4 | 79 | 0/4 | -0.076 |
| book_sess | M7 | 5 | c4_ichi_tk_range16_fresh1 | 112 | -0.193 | 0.024 | -0.217 | -4.2 | 2.8 | 27 | 0/2 | -0.334 |
| book_sess | P7 | 2 | c4_kstS_range16_divwith | 280 | -0.184 | 0.069 | -0.252 | -4.2 | 2.4 | 73 | 0/3 | -0.067 |
| ALL |  |  | c4_wtS_range16_eenter_z2 | 4957 | -0.035 | 0.022 | -0.058 | -4.1 | 2.3 | 189 | 0/4 | -0.084 |
| ALL |  |  | c4_copp_range16_fresh5 | 12366 | -0.013 | 0.024 | -0.037 | -4.0 | 2.3 | 189 | 0/4 | -0.033 |
| book_sess | A7 | 3 | c4_chopF_range16_hi_z1 | 228 | -0.144 | 0.045 | -0.189 | -4.0 | 2.6 | 62 | 0/3 | -0.214 |
| sess |  | 5 | c4_w1_rsi2_range16_eleave | 1401 | 0.097 | -0.011 | 0.108 | 3.9 | 2.5 | 186 | 4/4 | 0.160 |
| book_sess | M7 | 5 | c4_w1_cmo21_range16_rise | 2101 | 0.047 | -0.029 | 0.075 | 3.9 | 2.8 | 184 | 4/4 | 0.109 |
| book_sess | H7 | 3 | c4_w1_hma200_px_range16_fresh5 | 107 | 0.001 | 0.071 | -0.070 | -3.9 | 2.4 | 17 | 0/2 | -0.299 |
| book_sess | K7 | 2 | c4_smieF_range16_nodiv | 788 | -0.032 | 0.164 | -0.196 | -3.9 | 2.3 | 33 | 0/3 | -0.369 |
| book_sess | M7 | 1 | c4_w1_kama200_px_range16_fresh5 | 385 | -0.123 | 0.029 | -0.152 | -3.8 | 2.7 | 97 | 0/4 | -0.173 |
| book_sess | M7 | 1 | c4_w1_willr7_range16_divwith | 257 | -0.090 | 0.019 | -0.109 | -3.8 | 2.7 | 71 | 0/3 | -0.028 |
| book_sess | P7 | 1 | c4_qqeF_range16_divwith | 308 | 0.162 | 0.008 | 0.155 | 3.8 | 2.2 | 77 | 3/3 | 0.195 |

## alt_range8

2311 conditions, 115550 tests, passing alone: 1055 tests (0.91%, 2.1x the nonsense rate), 737 distinct conditions (32% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sess |  | 3 | c4_w1_kama_stack_fast_range8_against | 1932 | 0.106 | 0.012 | 0.094 | 4.4 | 2.0 | 188 | 4/4 | 0.050 |
| book_sess | K7 | 0 | c4_w1_vwma200_px_range8_side | 3106 | 0.049 | -0.061 | 0.110 | 4.3 | 2.3 | 33 | 3/3 | 0.100 |
| book_sess | K7 | 0 | c4_vsa_upthrust_range8_against | 102 | 0.351 | 0.034 | 0.317 | 4.2 | 2.3 | 22 | 2/2 | 0.280 |
| book_sess | K7 | 5 | c4_w1_ema8_px_range8_fresh5 | 896 | 0.049 | -0.070 | 0.119 | 4.1 | 2.6 | 152 | 4/4 | 0.200 |
| ALL |  |  | c4_brkS_near_range8_against | 7943 | 0.054 | 0.015 | 0.039 | 4.1 | 2.3 | 189 | 4/4 | 0.029 |
| book_sess | O7 | 3 | c4_srsi_range8_side | 242 | 0.390 | 0.088 | 0.302 | 4.1 | 3.7 | 18 | 4/4 | 0.408 |
| book_sess | O7 | 3 | c4_w1_stochrsi14_range8_side | 242 | 0.390 | 0.088 | 0.302 | 4.1 | 3.7 | 18 | 4/4 | 0.408 |
| book | O7 |  | c4_srsi_range8_side | 242 | 0.390 | 0.088 | 0.302 | 4.1 | 3.7 | 18 | 4/4 | 0.408 |
| book | O7 |  | c4_w1_stochrsi14_range8_side | 242 | 0.390 | 0.088 | 0.302 | 4.1 | 3.7 | 18 | 4/4 | 0.408 |
| book_sess | A7 | 0 | c4_w1_kama21_px_range8_nodiv | 1133 | 0.143 | -0.056 | 0.199 | 4.0 | 2.4 | 57 | 3/3 | 0.153 |
| sess |  | 1 | c4_vsa_stopvol_range8_side | 151 | -0.241 | 0.028 | -0.269 | -4.0 | 2.5 | 32 | 0/2 | -0.443 |
| sess |  | 1 | c4_vsa_stopvol_range8_fresh1 | 151 | -0.241 | 0.028 | -0.269 | -4.0 | 2.5 | 32 | 0/2 | -0.443 |
| book_sess | H7 | 1 | c4_w1_hma21_px_range8_divwith | 162 | 0.309 | -0.005 | 0.314 | 4.0 | 2.9 | 37 | 3/3 | 0.527 |
| ALL |  |  | c4_w1_demarker14_range8_rise | 41793 | 0.032 | 0.006 | 0.026 | 3.9 | 2.3 | 189 | 4/4 | 0.023 |
| ALL |  |  | c4_w1_psar_0.01_range8_rise | 43286 | 0.032 | 0.004 | 0.028 | 3.9 | 2.3 | 189 | 4/4 | 0.037 |

## alt_renko16

2311 conditions, 115550 tests, passing alone: 702 tests (0.61%, 1.4x the nonsense rate), 502 distinct conditions (22% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | O7 | 3 | c4_w1_hma8_px_renko16_nodiv | 330 | 0.127 | 0.419 | -0.292 | -4.9 | 3.7 | 13 | 0/3 | -0.321 |
| book | O7 |  | c4_w1_hma8_px_renko16_nodiv | 330 | 0.127 | 0.419 | -0.292 | -4.9 | 3.7 | 13 | 0/3 | -0.321 |
| sess |  | 4 | c4_w1_donchian50_pos_renko16_eleave | 127 | 0.293 | -0.003 | 0.296 | 4.9 | 2.4 | 26 | 2/2 | 0.033 |
| book_sess | M7 | 3 | c4_mcmf_renko16_divwith | 158 | 0.343 | -0.011 | 0.354 | 4.7 | 2.6 | 41 | 3/3 | 0.301 |
| book_sess | K7 | 0 | c4_alligator_renko16_against | 440 | -0.069 | 0.061 | -0.130 | -4.4 | 2.3 | 128 | 0/4 | -0.021 |
| book_sess | K7 | 2 | c4_w1_mfi14_renko16_side | 759 | 0.051 | -0.221 | 0.272 | 4.3 | 2.3 | 47 | 3/3 | 0.387 |
| book_sess | H7 | 0 | c4_w1_mfi14_renko16_nodiv | 575 | 0.058 | 0.194 | -0.136 | -4.3 | 2.2 | 25 | 0/2 | -0.286 |
| book_sess | A7 | 3 | c4_ichiS_chikou_renko16_against | 167 | 0.222 | 0.024 | 0.198 | 4.2 | 2.6 | 42 | 3/3 | 0.415 |
| book | M7 |  | c4_w1_vortex7_renko16_divwith | 1003 | -0.119 | 0.017 | -0.135 | -4.1 | 2.2 | 166 | 0/4 | -0.052 |
| book_sess | M7 | 4 | c4_brk_in_renko16_against | 269 | 0.217 | -0.005 | 0.221 | 4.0 | 2.6 | 77 | 4/4 | 0.363 |
| book_sess | M7 | 4 | c4_brkF_in_renko16_against | 269 | 0.217 | -0.005 | 0.221 | 4.0 | 2.6 | 77 | 4/4 | 0.363 |
| book | M7 |  | c4_w1_ha_run_renko16_divwith | 1116 | -0.087 | 0.015 | -0.102 | -4.0 | 2.2 | 173 | 0/4 | -0.001 |
| book | M7 |  | c4_w1_rsi2_renko16_divwith | 1389 | -0.086 | 0.017 | -0.103 | -4.0 | 2.2 | 183 | 0/4 | -0.003 |
| book_sess | A7 | 4 | c4_sdflipF_near_renko16_against | 165 | 0.123 | -0.009 | 0.132 | 3.9 | 2.5 | 38 | 2/2 | 0.292 |
| book_sess | A7 | 4 | c4_sdflip_near_renko16_against | 165 | 0.123 | -0.009 | 0.132 | 3.9 | 2.5 | 38 | 2/2 | 0.292 |

## alt_renko8

2311 conditions, 115550 tests, passing alone: 674 tests (0.58%, 1.3x the nonsense rate), 524 distinct conditions (23% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | K7 | 2 | c4_w1_ichi_slow_tkkj_renko8_nodiv | 796 | -0.032 | 0.175 | -0.207 | -4.8 | 2.3 | 34 | 0/3 | -0.440 |
| book_sess | K7 | 2 | c4_ichiS_tk_renko8_nodiv | 796 | -0.032 | 0.175 | -0.207 | -4.8 | 2.3 | 34 | 0/3 | -0.440 |
| ALL |  |  | c4_coppS_renko8_fresh5 | 8897 | -0.020 | 0.023 | -0.044 | -4.6 | 2.3 | 189 | 0/4 | -0.025 |
| book_sess | M7 | 5 | c4_w1_kama50_px_renko8_fresh5 | 644 | 0.121 | -0.007 | 0.128 | 4.4 | 2.8 | 153 | 4/4 | 0.130 |
| sess |  | 2 | c4_choch_renko8_fresh1 | 119 | 0.218 | -0.009 | 0.227 | 4.4 | 2.8 | 27 | 2/2 | 0.486 |
| sess |  | 2 | c4_chochF_renko8_fresh1 | 119 | 0.218 | -0.009 | 0.227 | 4.4 | 2.8 | 27 | 2/2 | 0.486 |
| ALL |  |  | c4_turt20_renko8_fresh5 | 12253 | -0.013 | 0.024 | -0.037 | -4.4 | 2.3 | 189 | 0/4 | -0.019 |
| book_sess | A7 | 1 | c4_w1_macd19_39_9_hist_renko8_divwith | 128 | 0.088 | 0.039 | 0.049 | 4.3 | 2.9 | 32 | 2/2 | 0.217 |
| sess |  | 2 | c4_fractal_brk_renko8_fresh1 | 118 | 0.214 | -0.009 | 0.223 | 4.3 | 2.8 | 27 | 2/2 | 0.486 |
| book | P7 |  | c4_stPF_renko8_fresh1 | 1151 | 0.108 | 0.014 | 0.093 | 4.0 | 2.2 | 186 | 4/4 | 0.170 |
| book_sess | P7 | 0 | c4_w1_ema200_px_renko8_side | 4038 | 0.091 | -0.056 | 0.147 | 4.0 | 3.1 | 143 | 4/4 | 0.132 |
| ALL |  |  | c4_smiS_renko8_eenter | 8435 | -0.017 | 0.023 | -0.040 | -3.8 | 2.3 | 189 | 0/4 | -0.020 |
| book_sess | M7 | 5 | c4_obS_in_renko8_against | 297 | 0.209 | -0.001 | 0.210 | 3.8 | 2.8 | 78 | 4/4 | 0.228 |
| book_sess | H7 | 1 | c4_w1_vortex7_renko8_side | 580 | -0.039 | 0.222 | -0.261 | -3.8 | 2.9 | 78 | 0/4 | -0.373 |
| book_sess | H7 | 1 | c4_w1_demarker7_renko8_side | 580 | -0.039 | 0.222 | -0.261 | -3.8 | 2.9 | 78 | 0/4 | -0.373 |

## alt_tick2000

2311 conditions, 115550 tests, passing alone: 898 tests (0.78%, 1.8x the nonsense rate), 682 distinct conditions (30% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book | A7 |  | c4_w1_stoch21_tick2000_eagainst | 100 | 0.437 | 0.019 | 0.418 | 5.5 | 2.4 | 21 | 2/2 | 0.534 |
| book_sess | A7 | 1 | c4_w1_stoch21_tick2000_eagainst | 88 | 0.450 | 0.034 | 0.416 | 5.3 | 2.9 | 20 | 2/2 | 0.582 |
| book_sess | H7 | 0 | c4_obF_near_tick2000_side | 129 | -0.056 | 0.114 | -0.170 | -4.6 | 2.2 | 19 | 0/3 | -0.135 |
| sess |  | 0 | c4_sdF_near_tick2000_side | 1289 | -0.010 | 0.080 | -0.090 | -4.5 | 2.8 | 170 | 0/4 | -0.035 |
| sess |  | 0 | c4_don10_pos_tick2000_side | 8229 | 0.092 | -0.005 | 0.097 | 4.4 | 2.8 | 189 | 4/4 | 0.043 |
| sess |  | 0 | c4_w1_donchian10_pos_tick2000_side | 8229 | 0.092 | -0.005 | 0.097 | 4.4 | 2.8 | 189 | 4/4 | 0.043 |
| sess |  | 0 | c4_w1_sma8_px_tick2000_side | 8246 | 0.091 | -0.003 | 0.093 | 4.4 | 2.8 | 189 | 4/4 | 0.039 |
| sess |  | 0 | c4_w1_boll10_pctb_tick2000_side | 8286 | 0.089 | 0.001 | 0.089 | 4.3 | 2.8 | 189 | 4/4 | 0.004 |
| book_sess | A7 | 1 | c4_w1_stoch8_tick2000_eenter | 2150 | -0.047 | 0.097 | -0.144 | -4.3 | 2.9 | 179 | 0/4 | -0.314 |
| book | U7 |  | c4_w1_di21_tick2000_nodiv | 2402 | 0.064 | -0.161 | 0.225 | 4.3 | 2.5 | 46 | 3/3 | 0.246 |
| sess |  | 4 | c4_w1_roc20_tick2000_nodiv | 14899 | 0.023 | -0.082 | 0.105 | 4.3 | 2.4 | 186 | 4/4 | 0.061 |
| sess |  | 0 | c4_w1_vwma8_px_tick2000_side | 8255 | 0.091 | -0.003 | 0.093 | 4.3 | 2.8 | 188 | 4/4 | 0.047 |
| sess |  | 4 | c4_w1_mom20_tick2000_nodiv | 14909 | 0.022 | -0.080 | 0.102 | 4.3 | 2.4 | 186 | 4/4 | 0.057 |
| sess |  | 0 | c4_kerF_dir_tick2000_side | 7962 | 0.095 | -0.005 | 0.100 | 4.2 | 2.8 | 189 | 4/4 | 0.108 |
| sess |  | 0 | c4_w1_mom5_tick2000_side | 7962 | 0.095 | -0.005 | 0.100 | 4.2 | 2.8 | 189 | 4/4 | 0.108 |

## alt_vol2000

2311 conditions, 115550 tests, passing alone: 657 tests (0.57%, 1.3x the nonsense rate), 549 distinct conditions (24% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | P7 | 4 | c4_w1_willr14_vol2000_eagainst | 117 | 0.263 | -0.007 | 0.270 | 5.1 | 2.5 | 29 | 2/2 | 0.428 |
| book_sess | K7 | 5 | c4_w1_willr7_vol2000_eleave | 319 | -0.161 | 0.011 | -0.172 | -4.9 | 2.6 | 88 | 0/4 | -0.170 |
| book_sess | K7 | 2 | c4_w1_ha_run_vol2000_divwith | 127 | 0.100 | -0.016 | 0.117 | 4.8 | 2.3 | 27 | 2/2 | 0.489 |
| book_sess | U7 | 3 | c4_brk_near_vol2000_side | 110 | 0.009 | 0.088 | -0.079 | -4.7 | 2.9 | 13 | 0/2 | -0.049 |
| book_sess | K7 | 5 | c4_fvgS_dsup_vol2000_hi | 558 | -0.133 | 0.070 | -0.203 | -4.3 | 2.6 | 99 | 0/4 | -0.244 |
| book_sess | M7 | 4 | c4_alli_spread_vol2000_fresh5 | 681 | 0.125 | -0.011 | 0.137 | 4.3 | 2.6 | 146 | 4/4 | 0.173 |
| book_sess | H7 | 4 | c4_lrcS_vol2000_rise | 236 | -0.017 | -0.009 | -0.008 | -4.2 | 2.9 | 18 | 0/4 | -0.168 |
| book_sess | M7 | 2 | c4_w1_rsi2_vol2000_ewith | 258 | 0.169 | -0.048 | 0.217 | 4.2 | 2.4 | 60 | 4/4 | 0.304 |
| book_sess | H7 | 4 | c4_almaS_slope_vol2000_rise | 273 | -0.064 | 0.057 | -0.121 | -4.1 | 2.9 | 14 | 0/4 | -0.594 |
| book_sess | M7 | 2 | c4_w1_rsi2_vol2000_eenter | 236 | 0.168 | -0.044 | 0.212 | 4.0 | 2.4 | 57 | 4/4 | 0.283 |
| book_sess | U7 | 3 | c4_w1_di14_vol2000_rise | 315 | 0.008 | 0.152 | -0.143 | -4.0 | 2.9 | 27 | 0/4 | -0.126 |
| book_sess | H7 | 3 | c4_w1_demarker14_vol2000_rise | 320 | 0.183 | -0.063 | 0.246 | 4.0 | 2.4 | 51 | 4/4 | 0.232 |
| book_sess | M7 | 3 | c4_w1_stochrsi14_vol2000_eleave | 538 | -0.113 | 0.026 | -0.139 | -4.0 | 2.6 | 133 | 0/4 | -0.185 |
| book_sess | M7 | 3 | c4_srsi_vol2000_eleave | 538 | -0.113 | 0.026 | -0.139 | -4.0 | 2.6 | 133 | 0/4 | -0.185 |
| book_sess | A7 | 0 | c4_w1_di21_vol2000_divwith | 146 | 0.312 | 0.086 | 0.226 | 3.9 | 2.4 | 28 | 2/2 | 0.304 |

## alt_vol500

2311 conditions, 115550 tests, passing alone: 732 tests (0.63%, 1.4x the nonsense rate), 554 distinct conditions (24% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | A7 | 1 | c4_chand_vol500_fresh5 | 353 | 0.219 | 0.028 | 0.190 | 4.7 | 2.9 | 90 | 4/4 | 0.257 |
| book_sess | K7 | 2 | c4_smi_vol500_side | 817 | 0.018 | -0.126 | 0.144 | 4.6 | 2.3 | 23 | 3/3 | 0.144 |
| book_sess | H7 | 1 | c4_obF_dres_vol500_hi | 126 | -0.119 | 0.100 | -0.219 | -4.5 | 2.9 | 21 | 0/3 | -0.083 |
| sess |  | 0 | c4_don55_pos_vol500_side | 9015 | 0.087 | -0.024 | 0.111 | 4.5 | 2.8 | 187 | 4/4 | 0.040 |
| book_sess | K7 | 2 | c4_w1_linreg_slope10_vol500_side | 778 | 0.021 | -0.107 | 0.128 | 4.5 | 2.3 | 37 | 3/3 | 0.144 |
| sess |  | 0 | c4_w1_donchian50_pos_vol500_side | 9058 | 0.087 | -0.030 | 0.117 | 4.3 | 2.8 | 186 | 4/4 | 0.042 |
| book_sess | A7 | 1 | c4_w1_rsi21_vol500_eenter | 253 | -0.138 | 0.049 | -0.187 | -4.3 | 2.9 | 72 | 0/4 | -0.286 |
| book_sess | A7 | 1 | c4_rsima21_vol500_eenter | 253 | -0.138 | 0.049 | -0.187 | -4.3 | 2.9 | 72 | 0/4 | -0.286 |
| sess |  | 0 | c4_chandS_vol500_hold3 | 7890 | 0.091 | 0.009 | 0.082 | 4.2 | 2.8 | 189 | 4/4 | 0.013 |
| sess |  | 0 | c4_ichi_cloud_vol500_against | 1507 | -0.016 | 0.083 | -0.100 | -4.2 | 2.8 | 183 | 0/4 | -0.058 |
| book_sess | M7 | 5 | c4_w1_willr14_vol500_eleave | 495 | 0.149 | -0.005 | 0.154 | 4.1 | 2.8 | 133 | 4/4 | 0.395 |
| book_sess | K7 | 0 | c4_coppS_vol500_rise | 2525 | 0.009 | 0.163 | -0.153 | -4.1 | 2.3 | 153 | 0/4 | -0.137 |
| sess |  | 0 | c4_w1_range_expansion_vol500_hi | 1768 | -0.018 | 0.087 | -0.105 | -4.0 | 2.8 | 189 | 0/4 | -0.112 |
| book_sess | M7 | 5 | c4_tsi_vol500_sig | 2330 | -0.023 | 0.097 | -0.120 | -3.9 | 2.8 | 178 | 0/4 | -0.127 |
| sess |  | 0 | c4_wtS_vol500_side | 8329 | 0.087 | 0.008 | 0.079 | 3.9 | 2.8 | 187 | 4/4 | 0.015 |

## altagree

4622 conditions, 231100 tests, passing alone: 751 tests (0.32%, 0.7x the nonsense rate), 600 distinct conditions (13% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | U7 | 3 | c4_agr_kvo_fresh5_ge6 | 100 | -0.102 | 0.110 | -0.211 | -7.3 | 2.9 | 11 | 0/2 | -0.112 |
| book_sess | A7 | 1 | c4_agr_crsi_ewith_z1_ge6 | 106 | -0.329 | 0.048 | -0.377 | -6.7 | 2.9 | 27 | 0/2 | -0.364 |
| book_sess | H7 | 4 | c4_agr_w1_psar_0.01_fresh5_ge3 | 198 | -0.120 | 0.065 | -0.184 | -5.6 | 2.9 | 22 | 0/4 | -0.443 |
| sess |  | 0 | c4_agr_kstS_side_ge3 | 10562 | 0.073 | -0.195 | 0.268 | 5.4 | 2.8 | 37 | 4/4 | 0.230 |
| sess |  | 1 | c4_agr_crsi_ewith_z1_ge6 | 141 | -0.228 | 0.027 | -0.255 | -5.4 | 2.5 | 42 | 0/3 | -0.268 |
| sess |  | 0 | c4_agr_sd_near_hold3_ge3 | 743 | -0.047 | 0.078 | -0.125 | -5.1 | 2.8 | 146 | 0/4 | -0.020 |
| sess |  | 0 | c4_agr_rfiltF_dir_hold3_ge3 | 10555 | 0.074 | -0.197 | 0.271 | 4.6 | 2.8 | 40 | 4/4 | 0.041 |
| sess |  | 0 | c4_agr_w1_psar_0.03_divwith_ge6 | 103 | -0.156 | 0.071 | -0.228 | -4.4 | 2.8 | 23 | 0/2 | -0.365 |
| sess |  | 0 | c4_agr_w1_trix30_side_ge3 | 10515 | 0.074 | -0.178 | 0.253 | 4.4 | 2.8 | 52 | 4/4 | 0.316 |
| book_sess | M7 | 3 | c4_agr_w1_stochrsi8_eleave_ge3 | 1454 | -0.063 | 0.052 | -0.115 | -4.4 | 2.6 | 185 | 0/4 | -0.198 |
| book_sess | M7 | 3 | c4_agr_srsiF_eleave_ge3 | 1454 | -0.063 | 0.052 | -0.115 | -4.4 | 2.6 | 185 | 0/4 | -0.198 |
| sess |  | 0 | c4_agr_w1_supertrend_10_3_side_ge6 | 9974 | 0.078 | -0.046 | 0.124 | 4.4 | 2.8 | 152 | 4/4 | 0.144 |
| sess |  | 0 | c4_agr_w1_kama100_px_side_ge6 | 9846 | 0.081 | -0.064 | 0.145 | 4.3 | 2.8 | 163 | 4/4 | 0.118 |
| book_sess | U7 | 0 | c4_agr_wtS_fresh5_ge3 | 598 | 0.062 | 0.220 | -0.158 | -4.2 | 2.9 | 12 | 0/2 | -0.182 |
| book_sess | K7 | 0 | c4_agr_lrcS_side_ge6 | 2966 | 0.056 | -0.089 | 0.145 | 4.2 | 2.3 | 73 | 4/4 | 0.273 |

## altagree_ctrl

4622 conditions, 231100 tests, passing alone: 1283 tests (0.56%, 1.3x the nonsense rate), 1006 distinct conditions (22% of the block).

| cell | book | sess | condition | n yes | mean R yes | mean R no | lift R | zw | bar99 | weeks | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book_sess | H7 | 1 | c4_agrctl_2216_ge6 | 104 | -0.208 | 0.086 | -0.294 | -6.6 | 2.9 | 19 | 0/3 | -0.628 |
| book_sess | K7 | 5 | c4_agrctl_1287_ge3 | 1830 | -0.042 | 0.249 | -0.291 | -5.7 | 2.6 | 47 | 0/3 | -0.401 |
| sess |  | 0 | c4_agrctl_1518_ge6 | 5783 | 0.112 | 0.019 | 0.093 | 4.9 | 2.8 | 189 | 4/4 | 0.072 |
| book_sess | M7 | 5 | c4_agrctl_917_ge6 | 146 | 0.290 | 0.005 | 0.285 | 4.8 | 2.8 | 36 | 3/3 | 0.027 |
| book_sess | H7 | 1 | c4_agrctl_1621_ge6 | 211 | -0.156 | 0.116 | -0.272 | -4.6 | 2.9 | 49 | 0/4 | -0.255 |
| book_sess | P7 | 0 | c4_agrctl_2133_ge6 | 4021 | 0.090 | -0.043 | 0.132 | 4.5 | 3.1 | 129 | 4/4 | 0.121 |
| ALL |  |  | c4_agrctl_238_ge6 | 1867 | -0.067 | 0.021 | -0.087 | -4.5 | 2.3 | 158 | 0/4 | -0.110 |
| book_sess | A7 | 5 | c4_agrctl_272_ge3 | 1162 | -0.066 | 0.076 | -0.142 | -4.3 | 2.4 | 103 | 0/4 | -0.179 |
| book_sess | P7 | 4 | c4_agrctl_127_ge3 | 6340 | 0.007 | -0.131 | 0.139 | 4.3 | 2.5 | 123 | 4/4 | 0.303 |
| book_sess | H7 | 1 | c4_agrctl_969_ge6 | 235 | -0.121 | 0.114 | -0.235 | -4.3 | 2.9 | 54 | 0/4 | -0.269 |
| sess |  | 5 | c4_agrctl_917_ge6 | 407 | 0.241 | -0.007 | 0.248 | 4.3 | 2.5 | 87 | 4/4 | 0.179 |
| book_sess | P7 | 0 | c4_agrctl_1518_ge6 | 2561 | 0.114 | 0.018 | 0.096 | 4.3 | 3.1 | 181 | 4/4 | 0.089 |
| book_sess | H7 | 1 | c4_agrctl_217_ge3 | 654 | -0.017 | 0.242 | -0.259 | -4.2 | 2.9 | 55 | 0/4 | -0.339 |
| book_sess | A7 | 1 | c4_agrctl_1872_ge3 | 5411 | 0.037 | 0.229 | -0.193 | -4.1 | 2.9 | 24 | 0/2 | -0.317 |
| book_sess | M7 | 5 | c4_agrctl_444_ge3 | 3060 | 0.004 | 0.112 | -0.108 | -4.1 | 2.8 | 110 | 0/4 | -0.022 |

