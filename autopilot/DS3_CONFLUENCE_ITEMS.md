# DS3_CONFLUENCE_ITEMS.md - STEP 3: each condition alone (W-CF1)
Verdict: map only (6021 conditions x book x session cells, taken JN05W2 trades, $ per trade at base lots net of $4.84 fees); nothing is dropped for being weak alone and nothing here is a result; every number is in-sample on the full history until step 5 controls are run by W-CF3.

Columns: lift = mean $/trade(yes) - mean $/trade(no); z = Welch; years_pos/years_n = calendar years with the same sign (>=30 per side); L3M / L6M lift = same lift in the recent windows (L3M ld>=20260813, L6M ld>=20260512).

## Counts by source
src
M                           5686
T                             14
V                              5
all                          316
univ_cols_M                 5686
univ_entry_table_ABCDEKL     273
univ_entry_table_S            35
univ_entry_table_T            14
univ_entry_table_U             8
univ_entry_table_V             5

## Most stable positive lifts per book cell (z>=3, same sign every year, positive in L6M); top 40 by z

| cond | book | sess | n_yes | share | mean_yes | mean_no | lift | z | yrs | L3M lift | L6M lift |
|---|---|---|---|---|---|---|---|---|---|---|---|
| c_B_cl_ahead_cnt3_15 | P7 |  | 2317 | 0.49 | 457 | -76 | 533 | 5.2 | 4/4 | -115 | 338 |
| c_B_cl_ahead_cnt3_5 | P7 |  | 3199 | 0.67 | 360 | -178 | 538 | 5.1 | 4/4 | 170 | 323 |
| c_B_cl_ahead_cnt2_10 | K7 |  | 1873 | 0.26 | 175 | 4 | 171 | 5.1 | 4/4 | -9 | 6 |
| m_ichi_fast_tkkj_15m_nodiv | H7 |  | 811 | 0.77 | 312 | -398 | 711 | 4.9 | 4/4 | 670 | 738 |
| c_B_cl_ahead_kinds2_10 | A7 |  | 501 | 0.43 | 295 | -29 | 325 | 4.9 | 4/4 | 405 | 239 |
| c_B_cl_ahead_kinds2_5 | A7 |  | 625 | 0.54 | 260 | -64 | 324 | 4.9 | 4/4 | 329 | 391 |
| c_B_cl_ahead_kinds2_5 | K7 |  | 2758 | 0.39 | 138 | -7 | 145 | 4.8 | 4/4 | -10 | 63 |
| c_B_cl_ahead_cnt3_10 | P7 |  | 2498 | 0.53 | 411 | -67 | 477 | 4.7 | 4/4 | -243 | 298 |
| m_uo_15m_side | K7 |  | 4615 | 0.65 | 95 | -36 | 132 | 4.5 | 4/4 | 181 | 160 |
| c_B_cl_ahead_cnt2_5 | K7 |  | 2551 | 0.36 | 138 | -0 | 138 | 4.5 | 4/4 | -23 | 36 |
| c_B_cl_ahead_cnt2_10 | A7 |  | 489 | 0.42 | 282 | -14 | 297 | 4.4 | 4/4 | 405 | 213 |
| c_B_cl_ahead_cnt3_5 | A7 |  | 963 | 0.83 | 177 | -215 | 391 | 4.4 | 4/4 | -98 | 236 |
| m_mfi14_15m_side | K7 |  | 4134 | 0.58 | 101 | -22 | 123 | 4.3 | 4/4 | 239 | 135 |
| c_B_cl_ahead_kinds2_15 | P7 |  | 1148 | 0.24 | 589 | 55 | 534 | 4.3 | 4/4 | 127 | 290 |
| c_B_cl_ahead_cnt2_15 | P7 |  | 1139 | 0.24 | 587 | 57 | 530 | 4.2 | 4/4 | 127 | 232 |
| c_B_cl_ahead_kinds2_15 | A7 |  | 480 | 0.42 | 275 | -5 | 280 | 4.2 | 4/4 | 374 | 326 |
| m_boll20_walk_15m_fresh5 | K7 |  | 1231 | 0.17 | 194 | 19 | 175 | 4.2 | 4/4 | 175 | 174 |
| c_B_cl_ahead_kinds2_10 | P7 |  | 1042 | 0.22 | 613 | 64 | 549 | 4.2 | 4/4 | -300 | 105 |
| c_B_cl_ahead_kinds2_5 | P7 |  | 1600 | 0.34 | 486 | 31 | 455 | 4.1 | 4/4 | -109 | 233 |
| c_B_cl_ahead_kinds2_a2 | K7 |  | 3162 | 0.45 | 115 | -3 | 118 | 4.0 | 4/4 | -55 | 16 |
| c_B_cl_ahead_cnt2_10 | P7 |  | 1018 | 0.21 | 594 | 73 | 522 | 3.9 | 4/4 | -300 | 13 |
| c_B_cl_ahead_cnt2_15 | A7 |  | 471 | 0.41 | 268 | 4 | 264 | 3.9 | 4/4 | 374 | 300 |
| c_B_cl_ahead_cnt2_5 | A7 |  | 589 | 0.51 | 237 | -19 | 257 | 3.9 | 4/4 | 197 | 309 |
| m_di7_3m_side | P7 |  | 3664 | 0.77 | 289 | -170 | 459 | 3.8 | 4/4 | 422 | 490 |
| m_rsi7_15m_ewith | K7 |  | 1827 | 0.26 | 154 | 13 | 141 | 3.8 | 4/4 | 177 | 181 |
| c_B_cl_ahead_kinds2_a2 | P7 |  | 2014 | 0.42 | 418 | 13 | 405 | 3.8 | 4/4 | 92 | 462 |
| c_B_cl_ahead_cnt2_a2 | P7 |  | 1832 | 0.39 | 431 | 29 | 402 | 3.7 | 4/4 | -29 | 273 |
| c_U_ge4 | K7 |  | 3390 | 0.48 | 105 | -2 | 107 | 3.7 | 4/4 | 199 | 152 |
| m_demarker7_15m_ewith | K7 |  | 2781 | 0.39 | 119 | 5 | 114 | 3.6 | 4/4 | 230 | 147 |
| m_adx7_1m_hi_z1 | M7 |  | 3076 | 0.77 | 48 | -123 | 171 | 3.6 | 4/4 | 222 | 247 |
| m_stoch14_15m_nodiv | H7 |  | 836 | 0.80 | 258 | -268 | 526 | 3.6 | 4/4 | -35 | 578 |
| c_B_cl_ahead_cnt3_15 | K7 |  | 3637 | 0.51 | 100 | -3 | 103 | 3.6 | 4/4 | -45 | 4 |
| c_B_cl_ahead_cnt2_a2 | K7 |  | 2878 | 0.41 | 113 | 6 | 106 | 3.6 | 4/4 | -43 | 12 |
| m_vwmacd_15m_sig | K7 |  | 4122 | 0.58 | 92 | -10 | 102 | 3.6 | 4/4 | 187 | 148 |
| m_boll20_walk_15m_side | K7 |  | 1517 | 0.21 | 155 | 21 | 134 | 3.5 | 4/4 | 148 | 139 |
| m_di21_60m_rise | U7 |  | 868 | 0.65 | 471 | -153 | 623 | 3.5 | 4/4 | 324 | 401 |
| c_B_cl_ahead_kinds2_a2 | A7 |  | 789 | 0.68 | 190 | -58 | 248 | 3.5 | 3/3 | 12 | 245 |
| m_di7_60m_rise | K7 |  | 3866 | 0.55 | 95 | -5 | 100 | 3.5 | 4/4 | 126 | 75 |
| m_ichi_slow_lag_5m_side | P7 |  | 3654 | 0.77 | 273 | -111 | 384 | 3.5 | 4/4 | 992 | 627 |
| c_E_rangeused_le0.5 | P7 |  | 2788 | 0.59 | 323 | -13 | 336 | 3.4 | 4/4 | 505 | 361 |

## Most stable positive lifts per book_sess cell (z>=3, same sign every year, positive in L6M); top 40 by z

| cond | book | sess | n_yes | share | mean_yes | mean_no | lift | z | yrs | L3M lift | L6M lift |
|---|---|---|---|---|---|---|---|---|---|---|---|
| m_multicross_60m_ewith | A7 | 4 | 2244 | 0.56 | 0 | -0 | 0 | 10.1 | 4/4 | 1 | 0 |
| m_ema_8_21_34_stack_60m_side | A7 | 4 | 2464 | 0.62 | 0 | -0 | 0 | 9.6 | 4/4 | 1 | 0 |
| m_ema_stack_fast_60m_side | A7 | 4 | 2464 | 0.62 | 0 | -0 | 0 | 9.6 | 4/4 | 1 | 0 |
| m_ema_stack_slow_agree3of4 | A7 | 4 | 2305 | 0.58 | 0 | -0 | 0 | 9.5 | 4/4 | 1 | 0 |
| c_B_cl_ahead_kinds2_5 | M7 | 0 | 6152 | 0.36 | 0 | 0 | 0 | 9.5 | 4/4 | 0 | 0 |
| m_ema_ribbon_15m_ewith | A7 | 4 | 2687 | 0.67 | 0 | -0 | 0 | 9.4 | 4/4 | 1 | 0 |
| c_B_cl_ahead_cnt2_5 | M7 | 0 | 5671 | 0.33 | 0 | 0 | 0 | 9.2 | 4/4 | 0 | 0 |
| m_rsi14_15m_ewith | M7 | 0 | 1478 | 0.09 | 0 | 0 | 0 | 9.0 | 4/4 | 0 | 0 |
| m_multicross_60m_side | A7 | 4 | 2648 | 0.66 | 0 | -0 | 0 | 9.0 | 4/4 | 1 | 0 |
| m_cci50_60m_ewith_z1 | A7 | 4 | 2148 | 0.54 | 0 | -0 | 0 | 8.9 | 4/4 | 1 | 0 |
| m_ema_stack_slow_15m_side | A7 | 4 | 2367 | 0.59 | 0 | -0 | 0 | 8.9 | 4/4 | 1 | 0 |
| m_boll10_walk_1d_rise | P7 | 4 | 1352 | 0.20 | 0 | -0 | 0 | 8.8 | 4/4 | 1 | 0 |
| m_ao_60m_side | A7 | 4 | 2763 | 0.69 | 0 | -0 | 0 | 8.8 | 4/4 | 1 | 1 |
| m_macd12_26_9_line_60m_side | A7 | 4 | 2881 | 0.72 | 0 | -0 | 0 | 8.8 | 4/4 | 1 | 0 |
| m_trix30_15m_side | A7 | 4 | 2746 | 0.69 | 0 | -0 | 0 | 8.7 | 4/4 | 1 | 0 |
| m_macd19_39_9_line_60m_side | A7 | 4 | 2615 | 0.66 | 0 | -0 | 0 | 8.5 | 4/4 | 1 | 0 |
| c_S_pivot_R1S1_beyond | A7 | 4 | 2431 | 0.61 | 0 | -0 | 0 | 8.5 | 4/4 | 1 | 0 |
| m_vwma_stack_fast_60m_side | A7 | 4 | 2272 | 0.57 | 0 | -0 | 0 | 8.4 | 4/4 | 1 | 0 |
| m_sma_stack_fast_60m_side | A7 | 4 | 1779 | 0.45 | 0 | -0 | 0 | 8.2 | 4/4 | 1 | 0 |
| m_boll10_walk_1d_rise | A7 | 4 | 946 | 0.24 | 0 | -0 | 0 | 8.2 | 4/4 | 1 | 1 |
| m_ema_ribbon_60m_side | A7 | 4 | 2683 | 0.67 | 0 | -0 | 0 | 8.2 | 4/4 | 1 | 0 |
| m_trend_osc_60m_side | A7 | 4 | 2899 | 0.73 | 0 | -0 | 0 | 8.1 | 4/4 | 1 | 1 |
| c_B_cl_ahead_cnt2_10 | M7 | 0 | 4788 | 0.28 | 0 | 0 | 0 | 8.1 | 4/4 | 0 | 0 |
| c_A_kc_out_60m | A7 | 4 | 2760 | 0.69 | 0 | -0 | 0 | 8.1 | 4/4 | 1 | 0 |
| c_B_cl_ahead_kinds2_10 | M7 | 0 | 5015 | 0.29 | 0 | 0 | 0 | 8.0 | 4/4 | 0 | 0 |
| m_keltner20_pos_15m_ewith | M7 | 0 | 2667 | 0.16 | 0 | 0 | 0 | 8.0 | 4/4 | 0 | 0 |
| c_U_3 | A7 | 4 | 2774 | 0.70 | 0 | -0 | 0 | 7.9 | 4/4 | 1 | 0 |
| m_keltner10_pos_60m_ewith | M7 | 0 | 3027 | 0.18 | 0 | 0 | 0 | 7.7 | 4/4 | 0 | 0 |
| c_C_open_drive_with | A7 | 4 | 899 | 0.23 | 0 | -0 | 0 | 7.7 | 4/4 | 1 | 0 |
| m_cmo21_60m_ewith | A7 | 4 | 827 | 0.21 | 0 | -0 | 0 | 7.7 | 4/4 | 1 | 0 |
| m_fisher20_60m_side | A7 | 4 | 2691 | 0.67 | 0 | -0 | 0 | 7.6 | 4/4 | 1 | 0 |
| m_trix8_60m_side | A7 | 4 | 2816 | 0.71 | 0 | -0 | 0 | 7.6 | 4/4 | 1 | 0 |
| m_vwmacd_60m_side | A7 | 4 | 2914 | 0.73 | 0 | -0 | 0 | 7.5 | 4/4 | 1 | 1 |
| c_S_cama_H3L3_beyond | A7 | 4 | 2895 | 0.73 | 0 | -0 | 0 | 7.5 | 4/4 | 1 | 0 |
| c_C_open_drive_with | P7 | 4 | 1325 | 0.20 | 0 | -0 | 0 | 7.5 | 4/4 | 0 | 0 |
| m_aroon25_60m_side | A7 | 4 | 2666 | 0.67 | 0 | -0 | 0 | 7.5 | 4/4 | 0 | 0 |
| m_adline_15m_side | M7 | 0 | 11616 | 0.68 | 0 | -0 | 0 | 7.4 | 4/4 | 0 | 0 |
| c_B_gap_dir_with | A7 | 4 | 2252 | 0.56 | 0 | -0 | 0 | 7.4 | 4/4 | 0 | 0 |
| m_multicross_1d_rise | A7 | 1 | 427 | 0.08 | 0 | 0 | 0 | 7.4 | 4/4 | -0 | 0 |
| m_ema_ribbon_1d_fresh5 | A7 | 1 | 399 | 0.08 | 0 | 0 | 0 | 7.3 | 4/4 | 0 | 0 |

## Worst (candidate vetoes): most negative stable lifts per book cell

| cond | book | n_yes | lift | z | yrs | L6M lift |
|---|---|---|---|---|---|---|
| m_hma200_px_3m_nodiv | A7 | 920 | -341 | -4.2 | 0/3 | -382 |
| m_supertrend_14_4_60m_rise | P7 | 123 | -1175 | -4.0 | 0/3 | -805 |
| c_E_rv_ge0.8 | M7 | 3161 | -177 | -3.8 | 0/4 | -252 |
| m_vortex14_3m_fresh5 | A7 | 229 | -307 | -3.7 | 0/4 | -104 |
| m_kama21_px_3m_nodiv | A7 | 919 | -283 | -3.5 | 0/3 | -456 |
| m_cmf10_60m_nodiv | A7 | 890 | -270 | -3.5 | 0/3 | -172 |
| m_sqz_ntf_ge4 | K7 | 194 | -251 | -3.5 | 0/3 | -154 |
| m_keltner40_pos_3m_fresh5 | K7 | 2795 | -97 | -3.4 | 0/4 | -141 |
| m_sqz_strength_5m_hi | K7 | 1732 | -103 | -3.4 | 0/4 | -136 |
| m_sqz_on_5m_hi | K7 | 1732 | -103 | -3.4 | 0/4 | -136 |
| m_vwma21_px_3m_nodiv | A7 | 904 | -265 | -3.3 | 0/3 | -310 |
| m_rsi21_3m_fresh5 | K7 | 2750 | -94 | -3.3 | 0/4 | -138 |
| m_eom14_3m_fresh5 | K7 | 3057 | -96 | -3.3 | 0/4 | -180 |
| m_linreg_chan50_5m_fresh5 | A7 | 336 | -244 | -3.3 | 0/4 | -109 |
| m_demarker7_5m_fresh5 | A7 | 398 | -231 | -3.3 | 0/4 | -125 |
| m_force13_60m_divwith | H7 | 151 | -555 | -3.3 | 0/4 | -574 |
| m_obv_3m_nodiv | A7 | 854 | -244 | -3.3 | 0/4 | -193 |
| m_aroon14_3m_fresh5 | A7 | 229 | -271 | -3.3 | 0/3 | -63 |
| m_force13_3m_fresh5 | K7 | 3399 | -94 | -3.2 | 0/4 | -9 |
| m_stochrsi8_15m_eleave | U7 | 298 | -614 | -3.2 | 0/4 | -156 |
| m_kama50_px_3m_fresh5 | K7 | 2422 | -93 | -3.2 | 0/4 | -66 |
| m_stochrsi21_5m_divwith | K7 | 968 | -127 | -3.2 | 0/4 | -130 |
| m_hma50_px_5m_fresh5 | A7 | 371 | -231 | -3.2 | 0/3 | -64 |
| m_obv_60m_fresh5 | P7 | 1190 | -366 | -3.2 | 0/4 | -289 |
| m_stochrsi8_3m_ewith | P7 | 650 | -440 | -3.2 | 0/4 | -624 |
| m_rh_propulsion_3m_side | K7 | 2948 | -91 | -3.2 | 0/4 | -81 |
| m_willr21_1m_side | P7 | 4083 | -521 | -3.2 | 0/4 | -566 |
| m_ema34_px_3m_nodiv | A7 | 917 | -257 | -3.2 | 0/3 | -339 |
| m_updown_vol20_1m_nodiv | U7 | 992 | -639 | -3.2 | 0/4 | -768 |
| m_vwma50_px_3m_fresh5 | U7 | 212 | -694 | -3.1 | 0/4 | -292 |

## SCREEN on the full universe (taken + skipped signals, in_pos=0 rows, 99,166 signals): outcome in R, taken rows real engine R, skipped rows HYPOTHETICAL R (book/session median bracket on 1m bars). A SCREEN only: skipped rows carry the engine skip selection and the hypothetical-outcome convention.

Counts by block: 0; A     80; B     58; C     31; D     16; E     18; K     51; L     19; S     35; T     14; U      8; V      5; a    257; b    258; c    440; d    419; e    308; f    178; h    293; i    279; k    347; l    246; m    507; n      6; o     31; p    150; r    323; s    709; t    260; u     80; v    348; w    247

Top per-book cells, z>=4, same sign in every year (lift in R per signal):

| cond | book | n_yes | share | lift R | z | yrs | L6M lift |
|---|---|---|---|---|---|---|---|

## Other blocks (own pages): DS3_CONFLUENCE_ITEMS_CF2.md (F-J, Block 5), CF4 / CF5 / CF6 pages as listed in CONFLUENCE_DEFS.md.

<!-- NONSENSE-BEGIN -->
## Block 18: NONSENSE CONTROLS - each-alone pass rates, real vs nonsense (200 meaningless conditions, c_Z_*, definitions in CONFLUENCE_DEFS.md)

Rows are condition x cell results with >=100 yes cases and 3-97% yes share. |z|>2 and |z|>3 are Welch z of the yes-vs-no lift; stable = |z|>2 AND same sign in every calendar year (>=3 years with >=30 per side) AND same sign in L6M. Nonsense should pass |z|>2 about 5%% by chance (cells overlap, so it can run higher); a real-condition pass rate close to the nonsense rate means that stage carries no information.

| outcome basis | group | cell type | rows | conditions | share abs z>2 | share abs z>3 | share stable |
|---|---|---|---|---|---|---|---|
| taken trades, net $ (base lots, $4.84 fees) | REAL | ALL | 5519 | 5508 | 0.082 | 0.011 | 0.0496 |
| taken trades, net $ (base lots, $4.84 fees) | REAL | book | 31146 | 5620 | 0.060 | 0.007 | 0.0301 |
| taken trades, net $ (base lots, $4.84 fees) | REAL | sess | 21141 | 5610 | 0.065 | 0.006 | 0.0257 |
| taken trades, net $ (base lots, $4.84 fees) | REAL | book_sess | 62210 | 5562 | 0.060 | 0.007 | 0.0212 |
| taken trades, net $ (base lots, $4.84 fees) | NONSENSE | ALL | 200 | 200 | 0.055 | 0.000 | 0.0250 |
| taken trades, net $ (base lots, $4.84 fees) | NONSENSE | book | 1398 | 200 | 0.051 | 0.003 | 0.0229 |
| taken trades, net $ (base lots, $4.84 fees) | NONSENSE | sess | 800 | 200 | 0.052 | 0.003 | 0.0238 |
| taken trades, net $ (base lots, $4.84 fees) | NONSENSE | book_sess | 2908 | 200 | 0.055 | 0.004 | 0.0206 |
| universe, R (skipped rows HYPOTHETICAL: screen only) | REAL | ALL | 5464 | 5464 | 0.121 | 0.027 | 0.0480 |
| universe, R (skipped rows HYPOTHETICAL: screen only) | REAL | book | 33726 | 5638 | 0.070 | 0.011 | 0.0248 |
| universe, R (skipped rows HYPOTHETICAL: screen only) | REAL | sess | 32472 | 5616 | 0.113 | 0.015 | 0.0328 |
| universe, R (skipped rows HYPOTHETICAL: screen only) | REAL | book_sess | 147909 | 5718 | 0.059 | 0.005 | 0.0185 |
| universe, R (skipped rows HYPOTHETICAL: screen only) | NONSENSE | ALL | 200 | 200 | 0.035 | 0.000 | 0.0200 |
| universe, R (skipped rows HYPOTHETICAL: screen only) | NONSENSE | book | 1400 | 200 | 0.041 | 0.006 | 0.0150 |
| universe, R (skipped rows HYPOTHETICAL: screen only) | NONSENSE | sess | 1200 | 200 | 0.040 | 0.003 | 0.0192 |
| universe, R (skipped rows HYPOTHETICAL: screen only) | NONSENSE | book_sess | 6418 | 200 | 0.044 | 0.005 | 0.0154 |

Reading (plain): on taken trades the real conditions pass |z|>2 only slightly more often than meaningless ones (book x session cells 5.6% vs 4.3%, stable-sign 2.9% vs 2.5%), so the each-alone |z|>2 screen has almost no power on its own and a lift of that size is not evidence. On the full universe with the hypothetical outcome, NONSENSE passes |z|>2 in 33-36% of pooled/session cells (real 34-43%): the signals are heavily clustered (consecutive signals share one outcome path), so the Welch z is inflated and the bar must be raised (cluster-robust z / one vote per day-session) before this screen is used for selection. Both tables are SCREEN output, not results.
<!-- NONSENSE-END -->
