# DS3_CONFLUENCE_ITEMS_CF5 - Block 3 (desk / named-trader systems), STEP 3 each alone

**Verdict line (updated 2026-11-14 23:54Z): sub-blocks A and B built (A: DeMark, Raschke, Connors, Chande, Wilder, Kase, Ehlers, Brooks, statistical measures; B: Dalton, Crabel, ACD, Williams); no item is claimed as a finding, tables below are the map.**

## Sub-block A: named-system indicators on HTF bars

Conditions scored: 3652 columns; 89846 (condition x cell) tests with >=20 yes and >=20 no. Pnl = engine net $ per taken JN05W2 trade (as-run base lots), taken trades only (skipped signals come with W-CF1 entry table). Lift = mean(yes)-mean(no), Welch 95% CI.

Pooled cell: 511 of 3652 conditions have |t|>2 (chance alone would give about 182). Read as a map, not as findings: at this many tests the best-looking items are mostly noise unless they hold by year and in L6M.

### Pooled (all books, all sessions): top 25 by |t| that also keep the sign in >=3 of 4 years and in L6M

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | wl_volstop_flip_fast_1d_against10 | 0.32 | 4 | 156 | 0.42 | 0.45 | -152 [-218, -86] | -4.5 | 4 | -57 | -212 |
| ALL/ALL | wl_volstop_dist_std_5m_side | 0.80 | 139 | -13 | 0.45 | 0.41 | 152 [85, 219] | 4.4 | 4 | 108 | 238 |
| ALL/ALL | wl_volstop_std_5m_side | 0.80 | 138 | -11 | 0.45 | 0.41 | 149 [82, 216] | 4.4 | 4 | 100 | 209 |
| ALL/ALL | rk_soup_fast_3m_state | 0.29 | 6 | 150 | 0.42 | 0.45 | -144 [-211, -77] | -4.2 | 4 | -169 | -112 |
| ALL/ALL | cn_double7_fast_3m_against10 | 0.31 | 20 | 148 | 0.43 | 0.44 | -128 [-188, -67] | -4.1 | 4 | -117 | -256 |
| ALL/ALL | eh_ebsw_slow_5m_side | 0.75 | 140 | 13 | 0.44 | 0.42 | 127 [66, 188] | 4.1 | 4 | 187 | 376 |
| ALL/ALL | st_amihud_3m_hi | 0.45 | 182 | 47 | 0.45 | 0.43 | 135 [70, 200] | 4.1 | 4 | 61 | 48 |
| ALL/ALL | eh_ebsw_fast_15m_ewith | 0.55 | 165 | 40 | 0.45 | 0.43 | 124 [64, 185] | 4.0 | 4 | 89 | 100 |
| ALL/ALL | eh_ebsw_fast_15m_side | 0.71 | 144 | 22 | 0.44 | 0.42 | 121 [62, 181] | 4.0 | 4 | 173 | 317 |
| ALL/ALL | rk_8020_slow_60m_with10 | 0.12 | -65 | 131 | 0.40 | 0.44 | -196 [-293, -99] | -4.0 | 3 | -335 | -254 |
| ALL/ALL | eh_ss20_15m_side | 0.81 | 136 | -7 | 0.45 | 0.41 | 143 [72, 214] | 4.0 | 4 | 125 | 376 |
| ALL/ALL | cn_double7_1m_against_state | 0.26 | 17 | 140 | 0.42 | 0.44 | -124 [-185, -62] | -3.9 | 4 | -120 | -278 |
| ALL/ALL | ch_dmi_1m_eleave | 0.01 | 923 | 103 | 0.60 | 0.44 | 820 [413, 1228] | 3.9 | 4 | 578 | 240 |
| ALL/ALL | ks_devstop2_5m_side | 0.81 | 133 | 6 | 0.44 | 0.41 | 127 [61, 193] | 3.8 | 4 | 130 | 392 |
| ALL/ALL | eh_ebsw_std_15m_eagainst | 0.27 | 24 | 139 | 0.42 | 0.44 | -116 [-177, -55] | -3.7 | 3 | -161 | -237 |
| ALL/ALL | rk_310_std_15m_side | 0.71 | 141 | 28 | 0.44 | 0.43 | 113 [53, 172] | 3.7 | 4 | 157 | 298 |
| ALL/ALL | ks_peak25_5m_side | 0.82 | 132 | 5 | 0.44 | 0.42 | 127 [59, 195] | 3.6 | 4 | 122 | 229 |
| ALL/ALL | eh_ebsw_slow_1d_nodiv | 0.85 | 133 | -26 | 0.44 | 0.42 | 159 [74, 245] | 3.6 | 4 | 27 | -144 |
| ALL/ALL | rk_310_slow_5m_side | 0.76 | 137 | 15 | 0.44 | 0.42 | 122 [56, 188] | 3.6 | 4 | 134 | 254 |
| ALL/ALL | bk_micro_60m_with_rising | 0.49 | 167 | 53 | 0.45 | 0.43 | 115 [52, 177] | 3.6 | 4 | 143 | 207 |
| ALL/ALL | st_zma200_60m_rise | 0.67 | 146 | 32 | 0.44 | 0.43 | 113 [51, 175] | 3.6 | 4 | 212 | 271 |
| ALL/ALL | bk_micro_60m_against_ge3 | 0.18 | -10 | 134 | 0.41 | 0.45 | -144 [-223, -65] | -3.6 | 3 | -216 | -247 |
| ALL/ALL | bk_trendbars5_15m_side | 0.55 | 158 | 47 | 0.45 | 0.42 | 111 [49, 173] | 3.5 | 4 | 121 | 102 |
| ALL/ALL | cn_rsi_pb_std_1m_against_state | 0.25 | 26 | 136 | 0.43 | 0.44 | -110 [-171, -49] | -3.5 | 3 | -170 | -290 |
| ALL/ALL | cn_rsi3_slow_60m_side | 0.67 | 145 | 32 | 0.45 | 0.42 | 113 [50, 176] | 3.5 | 3 | 153 | 326 |

### Per book x session cells: top 6 by |t| (same stability filter, cells with >=150 trades)

**A7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | eh_mama_std_60m_nodiv | 0.85 | 71 | 407 | 0.50 | 0.66 | -336 [-518, -154] | -3.6 | 4 | -117 | 299 |
| A7/0 | ch_fosc_slow_3m_nodiv | 0.71 | 46 | 302 | 0.49 | 0.60 | -256 [-401, -111] | -3.5 | 4 | -290 | -219 |
| A7/0 | eh_mama_slow_60m_nodiv | 0.86 | 76 | 386 | 0.50 | 0.65 | -310 [-495, -126] | -3.3 | 3 | -85 | 342 |
| A7/0 | bk_trendbars20_15m_divwith | 0.10 | -214 | 156 | 0.38 | 0.54 | -370 [-594, -147] | -3.2 | 4 | -287 | -276 |
| A7/0 | st_zma50_15m_ewith | 0.16 | 354 | 77 | 0.63 | 0.51 | 277 [99, 456] | 3.0 | 4 | 289 | 668 |
| A7/0 | rk_soup_std_1d_with10 | 0.15 | 354 | 80 | 0.62 | 0.51 | 274 [92, 455] | 3.0 | 3 | 93 | 522 |

**H7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | rk_310h_std_agree4of4 | 0.12 | -604 | 320 | 0.34 | 0.50 | -924 [-1482, -366] | -3.2 | 4 | -536 | -147 |
| H7/0 | cn_ibs_15m_eleave | 0.35 | -178 | 414 | 0.41 | 0.51 | -593 [-989, -196] | -2.9 | 4 | -1 | -663 |
| H7/0 | dm_flip_1d_against3 | 0.22 | 725 | 64 | 0.58 | 0.45 | 661 [212, 1110] | 2.9 | 4 | 1 | -268 |
| H7/0 | rk_8020_fast_1d_against10 | 0.71 | 381 | -212 | 0.51 | 0.41 | 593 [179, 1006] | 2.8 | 4 | 117 | 146 |
| H7/0 | eh_ebsw_std_15m_nodiv | 0.85 | 316 | -418 | 0.49 | 0.40 | 734 [211, 1257] | 2.8 | 4 | 399 | 193 |
| H7/0 | eh_ss6_1m_divwith | 0.12 | 902 | 113 | 0.60 | 0.46 | 789 [226, 1352] | 2.7 | 4 | 603 | -578 |

**H7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | cn_rsi2_std_3m_nodiv | 0.80 | -59 | 444 | 0.43 | 0.66 | -503 [-780, -226] | -3.6 | 4 | -290 | -1364 |
| H7/3 | cn_rsi2_fast_3m_nodiv | 0.80 | -59 | 444 | 0.43 | 0.66 | -503 [-780, -226] | -3.6 | 4 | -290 | -1364 |
| H7/3 | eh_cyber_fast_1m_side | 0.51 | 239 | -166 | 0.57 | 0.38 | 405 [175, 635] | 3.4 | 3 | 200 | 129 |
| H7/3 | wl_volstop_dist_std_3m_nodiv | 0.85 | -38 | 500 | 0.45 | 0.67 | -538 [-846, -231] | -3.4 | 4 | -91 | -383 |
| H7/3 | eh_ss6_3m_nodiv | 0.74 | -69 | 360 | 0.43 | 0.61 | -429 [-688, -169] | -3.2 | 4 | -537 | -723 |
| H7/3 | ks_peak8_1m_rise | 0.46 | 243 | -129 | 0.57 | 0.40 | 372 [141, 603] | 3.2 | 4 | 376 | 277 |

**K7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | eh_cyber_fast_15m_ewith | 0.14 | 388 | 42 | 0.54 | 0.43 | 346 [171, 521] | 3.9 | 4 | 112 | 141 |
| K7/0 | rk_grail_std_60m_against10 | 0.12 | -151 | 124 | 0.36 | 0.46 | -275 [-420, -130] | -3.7 | 4 | -242 | -524 |
| K7/0 | eh_snr_3m_hi_z1 | 0.30 | 241 | 25 | 0.50 | 0.42 | 216 [101, 332] | 3.7 | 4 | 291 | 196 |
| K7/0 | eh_trendmode_5m_hi_z1 | 0.13 | 384 | 46 | 0.54 | 0.43 | 338 [149, 527] | 3.5 | 4 | 320 | 530 |
| K7/0 | rk_8020_slow_5m_state | 0.28 | -52 | 144 | 0.38 | 0.47 | -196 [-305, -86] | -3.5 | 4 | -232 | -180 |
| K7/0 | st_zma50_5m_ewith | 0.07 | 482 | 60 | 0.57 | 0.44 | 422 [180, 665] | 3.4 | 3 | 328 | 374 |

**K7 session 1**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | rk_soup_std_3m_against_state | 0.45 | 164 | -61 | 0.48 | 0.39 | 225 [106, 344] | 3.7 | 4 | 231 | 363 |
| K7/1 | rk_soup_std_5m_state | 0.26 | -113 | 95 | 0.36 | 0.45 | -208 [-332, -84] | -3.3 | 4 | -62 | -45 |
| K7/1 | dm_line_break_3m_with1 | 0.14 | -189 | 79 | 0.34 | 0.44 | -268 [-435, -101] | -3.1 | 4 | -486 | -689 |
| K7/1 | ch_fosc_slow_agree4of4 | 0.18 | 241 | -5 | 0.51 | 0.41 | 246 [93, 400] | 3.1 | 3 | 349 | 896 |
| K7/1 | ks_peak14_5m_divwith | 0.12 | 262 | 10 | 0.52 | 0.42 | 252 [83, 422] | 2.9 | 3 | 496 | 453 |
| K7/1 | st_nqlag_es60_3m_divwith | 0.19 | 211 | 0 | 0.50 | 0.41 | 211 [65, 357] | 2.8 | 4 | 155 | 8 |

**K7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | rk_anti_5m_with3 | 0.27 | 146 | -38 | 0.49 | 0.40 | 185 [71, 298] | 3.2 | 4 | 205 | 283 |
| K7/3 | st_es_leads_1m_hi_z1 | 0.13 | 216 | -19 | 0.52 | 0.41 | 236 [86, 386] | 3.1 | 4 | 408 | 485 |
| K7/3 | st_amihud_60m_hi | 0.56 | 79 | -75 | 0.46 | 0.39 | 154 [53, 254] | 3.0 | 4 | 270 | 379 |
| K7/3 | cn_cumrsi_raw_5m_side | 0.85 | 42 | -166 | 0.44 | 0.33 | 208 [72, 345] | 3.0 | 4 | 321 | 274 |
| K7/3 | ks_devstop1_agree3of4 | 0.68 | 61 | -95 | 0.45 | 0.38 | 156 [49, 263] | 2.9 | 4 | 72 | 34 |
| K7/3 | ch_fosc_std_agree4of4 | 0.14 | 193 | -18 | 0.51 | 0.41 | 211 [67, 356] | 2.9 | 4 | 264 | 325 |

**K7 session 4**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | st_corr_es_3m_hi_z1 | 0.37 | -102 | 158 | 0.39 | 0.50 | -259 [-402, -116] | -3.6 | 4 | -226 | -1293 |
| K7/4 | dm_flip_1d_against10 | 0.80 | -2 | 311 | 0.44 | 0.53 | -312 [-497, -128] | -3.3 | 3 | -467 | -335 |
| K7/4 | st_zma200_15m_ewith | 0.28 | 253 | -12 | 0.52 | 0.43 | 264 [97, 431] | 3.1 | 4 | 522 | 1202 |
| K7/4 | st_corr_es_1m_hi_z1 | 0.44 | -62 | 159 | 0.41 | 0.50 | -221 [-363, -80] | -3.1 | 4 | -231 | -906 |
| K7/4 | rk_anti_15m_with10 | 0.47 | 175 | -39 | 0.49 | 0.43 | 214 [72, 356] | 3.0 | 4 | 505 | 662 |
| K7/4 | rk_anti_d_agree4of4 | 0.19 | 289 | 7 | 0.54 | 0.44 | 281 [91, 472] | 2.9 | 3 | 837 | 495 |

**M7 session 1**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | wl_volstop_flip_fast_1d_against10 | 0.32 | -147 | 70 | 0.35 | 0.44 | -217 [-329, -104] | -3.8 | 4 | -253 | -315 |
| M7/1 | bk_trendbars5_1m_eleave | 0.10 | 299 | -34 | 0.51 | 0.39 | 333 [139, 527] | 3.4 | 4 | 460 | 697 |
| M7/1 | dm_cd_1m_with_ge12 | 0.05 | -273 | 16 | 0.27 | 0.41 | -289 [-468, -111] | -3.2 | 4 | -194 | -372 |
| M7/1 | ks_peak8_1m_eleave | 0.05 | 416 | -20 | 0.54 | 0.40 | 436 [160, 711] | 3.1 | 4 | 494 | -17 |
| M7/1 | dm_cd_1m_with_ge13 | 0.04 | -306 | 13 | 0.27 | 0.41 | -319 [-523, -115] | -3.1 | 4 | -123 | -416 |
| M7/1 | rk_soup_slow_5m_against_state | 0.40 | 105 | -68 | 0.45 | 0.38 | 172 [62, 283] | 3.0 | 3 | 141 | 78 |

**M7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | bk_h1h2_1m_with3 | 0.40 | 147 | -31 | 0.48 | 0.41 | 178 [73, 283] | 3.3 | 4 | 284 | 321 |
| M7/3 | st_zma20_5m_nodiv | 0.78 | 83 | -109 | 0.46 | 0.37 | 193 [71, 315] | 3.1 | 4 | 202 | 377 |
| M7/3 | rk_grail_std_3m_with10 | 0.16 | -137 | 74 | 0.35 | 0.45 | -211 [-349, -74] | -3.0 | 4 | -328 | 18 |
| M7/3 | eh_mamapx_slow_5m_nodiv | 0.81 | 77 | -119 | 0.45 | 0.36 | 197 [68, 326] | 3.0 | 4 | 200 | 324 |
| M7/3 | st_nqlag_es120_15m_side | 0.36 | 143 | -17 | 0.49 | 0.41 | 160 [52, 269] | 2.9 | 4 | 218 | 245 |
| M7/3 | rk_8020_std_60m_state | 0.47 | -41 | 111 | 0.40 | 0.47 | -152 [-256, -49] | -2.9 | 4 | -300 | -259 |

**O7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | rk_anti_3m_against_state | 0.35 | -34 | 291 | 0.29 | 0.42 | -325 [-538, -111] | -3.0 | 3 | -683 | -952 |
| O7/3 | rk_310h_slow_agree3of4 | 0.53 | 321 | 17 | 0.44 | 0.31 | 304 [94, 514] | 2.8 | 4 | 94 | 965 |
| O7/3 | rk_anti_3m_state | 0.64 | 279 | -4 | 0.41 | 0.30 | 283 [69, 497] | 2.6 | 3 | 683 | 952 |
| O7/3 | eh_ebsw_slow_60m_nodiv | 0.86 | 227 | -109 | 0.39 | 0.26 | 336 [66, 606] | 2.4 | 3 | 516 | 1157 |
| O7/3 | st_nqlag_es30_3m_eagainst | 0.70 | 256 | -7 | 0.40 | 0.31 | 263 [40, 485] | 2.3 | 4 | 54 | -192 |
| O7/3 | rk_8020_fast_15m_with10 | 0.60 | 275 | 31 | 0.42 | 0.31 | 243 [30, 456] | 2.2 | 3 | 350 | 760 |

**P7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | cn_rsi3_slow_agree3of4 | 0.68 | 651 | -31 | 0.45 | 0.42 | 682 [272, 1093] | 3.3 | 4 | 285 | 724 |
| P7/0 | rk_soup_fast_3m_with3 | 0.05 | -809 | 500 | 0.30 | 0.45 | -1309 [-2103, -515] | -3.2 | 4 | -1161 | -179 |
| P7/0 | dm_combo_5m_with_ge8 | 0.03 | -1054 | 482 | 0.29 | 0.45 | -1536 [-2473, -598] | -3.2 | 3 | -1416 | -1790 |
| P7/0 | eh_mamapx_slow_3m_side | 0.79 | 591 | -170 | 0.45 | 0.41 | 761 [297, 1226] | 3.2 | 4 | 721 | 1788 |
| P7/0 | eh_mama_slow_3m_rise | 0.79 | 591 | -170 | 0.45 | 0.41 | 761 [297, 1226] | 3.2 | 4 | 721 | 1788 |
| P7/0 | eh_ss10_15m_rise | 0.73 | 617 | -54 | 0.45 | 0.42 | 671 [252, 1091] | 3.1 | 4 | 77 | 625 |

**P7 session 1**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | dm_demand_line_15m_nodiv | 0.91 | -78 | 939 | 0.35 | 0.61 | -1018 [-1655, -381] | -3.1 | 3 | -275 | 374 |
| P7/1 | ks_peak14_5m_divwith | 0.08 | 682 | -12 | 0.50 | 0.37 | 694 [259, 1129] | 3.1 | 4 | 140 | 19 |
| P7/1 | rk_8020_fast_5m_against10 | 0.69 | 159 | -225 | 0.41 | 0.33 | 384 [143, 626] | 3.1 | 4 | 377 | 496 |
| P7/1 | cn_rsi2_fast_60m_nodiv | 0.84 | 111 | -329 | 0.39 | 0.33 | 440 [150, 731] | 3.0 | 4 | 346 | 540 |
| P7/1 | cn_rsi2_std_60m_nodiv | 0.84 | 111 | -329 | 0.39 | 0.33 | 440 [150, 731] | 3.0 | 4 | 346 | 540 |
| P7/1 | rk_grail_slow_15m_state | 0.09 | -486 | 90 | 0.29 | 0.39 | -577 [-960, -194] | -3.0 | 4 | -450 | 55 |

**P7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | rk_8020_fast_5m_against10 | 0.69 | -199 | 344 | 0.36 | 0.46 | -543 [-829, -256] | -3.7 | 4 | -650 | -240 |
| P7/3 | bk_h1h2_60m_with10 | 0.45 | 233 | -248 | 0.44 | 0.35 | 481 [219, 743] | 3.6 | 4 | 649 | 826 |
| P7/3 | st_nqlag_es120_60m_divwith | 0.26 | -370 | 91 | 0.31 | 0.42 | -461 [-737, -185] | -3.3 | 4 | -431 | -600 |
| P7/3 | cn_rsi2_std_1d_ewith | 0.13 | 591 | -121 | 0.48 | 0.38 | 712 [284, 1139] | 3.3 | 4 | 743 | 1019 |
| P7/3 | rk_8020_std_5m_against10 | 0.47 | -251 | 168 | 0.35 | 0.43 | -419 [-678, -160] | -3.2 | 4 | -139 | 2 |
| P7/3 | rk_anti_1d_with10 | 0.43 | 214 | -210 | 0.43 | 0.36 | 424 [161, 688] | 3.2 | 4 | 348 | 384 |

**U7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | cn_double7_slow_1d_with3 | 0.09 | 1658 | 268 | 0.71 | 0.51 | 1390 [602, 2179] | 3.5 | 3 | 1895 | 1811 |
| U7/0 | eh_roof_slow_15m_rise | 0.88 | 520 | -565 | 0.56 | 0.34 | 1085 [458, 1711] | 3.4 | 3 | 589 | 896 |
| U7/0 | eh_roof_slow_15m_sig | 0.88 | 520 | -565 | 0.56 | 0.34 | 1085 [458, 1711] | 3.4 | 3 | 589 | 896 |
| U7/0 | wl_volstop_fast_15m_side | 0.85 | 212 | 1359 | 0.50 | 0.67 | -1147 [-1832, -462] | -3.3 | 4 | -1706 | -3093 |
| U7/0 | wl_volstop_fast_agree3of4 | 0.88 | 237 | 1459 | 0.51 | 0.69 | -1222 [-1968, -476] | -3.2 | 4 | -1817 | -2022 |
| U7/0 | cn_double7_1d_with3 | 0.15 | 1294 | 222 | 0.67 | 0.50 | 1072 [417, 1727] | 3.2 | 3 | 1182 | 782 |

**U7 session 1**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | eh_ss6_60m_nodiv | 0.82 | 326 | -709 | 0.53 | 0.37 | 1035 [420, 1649] | 3.3 | 4 | 1246 | 1176 |
| U7/1 | ch_fosc_std_60m_nodiv | 0.81 | 326 | -632 | 0.53 | 0.40 | 957 [367, 1547] | 3.2 | 4 | 895 | 1971 |
| U7/1 | bk_failbo_std_3m_state | 0.26 | -444 | 342 | 0.42 | 0.53 | -786 [-1292, -280] | -3.0 | 3 | -1214 | -1874 |
| U7/1 | cn_rsi2_std_agree4of4 | 0.56 | 453 | -266 | 0.55 | 0.44 | 719 [245, 1194] | 3.0 | 4 | 438 | 1364 |
| U7/1 | cn_rsi2_fast_agree4of4 | 0.56 | 453 | -266 | 0.55 | 0.44 | 719 [245, 1194] | 3.0 | 4 | 438 | 1364 |
| U7/1 | cn_double7_fast_5m_against_state | 0.55 | -175 | 530 | 0.46 | 0.56 | -705 [-1185, -225] | -2.9 | 4 | -364 | -1333 |

Full per-cell table (all conditions, all cells): /mnt/l2/l2vast/_confl/cols_cf5/score_A_named_hs.parquet


## Sub-block B: session / daily named systems (Dalton, Crabel, ACD, Williams)

Conditions scored: 123 columns; 2055 (condition x cell) tests with >=20 yes and >=20 no. Pnl = engine net $ per taken JN05W2 trade (as-run base lots), taken trades only (skipped signals come with W-CF1 entry table). Lift = mean(yes)-mean(no), Welch 95% CI.

Pooled cell: 28 of 123 conditions have |t|>2 (chance alone would give about 6). Read as a map, not as findings: at this many tests the best-looking items are mostly noise unless they hold by year and in L6M.

### Pooled (all books, all sessions): top 25 by |t| that also keep the sign in >=3 of 4 years and in L6M

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | dl_pd_neutral | 0.11 | 267 | 88 | 0.48 | 0.43 | 179 [78, 281] | 3.5 | 4 | 223 | 311 |
| ALL/ALL | cb_stretch_std_hit | 0.75 | 68 | -52 | 0.44 | 0.40 | 119 [48, 191] | 3.3 | 3 | 288 | 338 |
| ALL/ALL | cb_stretch_std_beyond | 0.58 | 83 | -25 | 0.44 | 0.41 | 108 [41, 174] | 3.2 | 3 | 184 | 294 |
| ALL/ALL | dl_sp_ahead_120 | 0.06 | -88 | 122 | 0.39 | 0.44 | -210 [-344, -76] | -3.1 | 3 | -294 | -231 |
| ALL/ALL | dl_pd_trend_against | 0.04 | -124 | 117 | 0.38 | 0.44 | -241 [-397, -85] | -3.0 | 3 | -231 | -1301 |
| ALL/ALL | fa_nl60_fast_with | 0.05 | 317 | 97 | 0.49 | 0.44 | 220 [72, 367] | 2.9 | 3 | 102 | nan |
| ALL/ALL | wl_volbo_fast_beyond | 0.46 | 93 | -9 | 0.45 | 0.41 | 103 [34, 171] | 2.9 | 3 | 361 | 471 |
| ALL/ALL | cb_stretch_fast_beyond | 0.60 | 78 | -21 | 0.44 | 0.41 | 98 [32, 165] | 2.9 | 4 | 247 | 431 |
| ALL/ALL | cb_stretch_slow_hit | 0.74 | 64 | -37 | 0.43 | 0.41 | 100 [29, 172] | 2.8 | 3 | 288 | 413 |
| ALL/ALL | fa_inor_std | 0.41 | -41 | 61 | 0.41 | 0.44 | -102 [-175, -29] | -2.7 | 4 | -202 | -32 |
| ALL/ALL | wl_volbo_std_hit | 0.34 | 105 | 2 | 0.45 | 0.41 | 103 [28, 177] | 2.7 | 4 | 326 | 387 |
| ALL/ALL | cb_stretch_fast_hit | 0.75 | 62 | -35 | 0.43 | 0.41 | 97 [25, 170] | 2.6 | 3 | 244 | 415 |
| ALL/ALL | dl_pd_neutral_ext | 0.06 | 272 | 97 | 0.49 | 0.43 | 175 [44, 305] | 2.6 | 4 | 175 | 609 |
| ALL/ALL | dl_sp_ahead_any | 0.20 | 25 | 129 | 0.42 | 0.44 | -103 [-181, -25] | -2.6 | 3 | -145 | -271 |
| ALL/ALL | dl_excess_high | 0.77 | 131 | 35 | 0.44 | 0.43 | 96 [23, 169] | 2.6 | 4 | 77 | 135 |
| ALL/ALL | dl_ib_ext_dn | 0.28 | -42 | 78 | 0.41 | 0.45 | -120 [-212, -28] | -2.5 | 3 | -23 | -792 |
| ALL/ALL | wl_volbo_fast_hit | 0.61 | 72 | -15 | 0.44 | 0.41 | 87 [20, 154] | 2.5 | 4 | 216 | 308 |
| ALL/ALL | fa_a_std_hit_with | 0.46 | 69 | -24 | 0.44 | 0.42 | 93 [20, 166] | 2.5 | 3 | 186 | 151 |
| ALL/ALL | fa_a_fast_hit_with | 0.68 | 54 | -33 | 0.44 | 0.42 | 87 [15, 160] | 2.4 | 3 | 222 | 129 |
| ALL/ALL | dl_sp_ahead_60 | 0.03 | -117 | 115 | 0.40 | 0.44 | -232 [-431, -33] | -2.3 | 3 | -584 | -740 |
| ALL/ALL | dl_pd_nontrend | 0.02 | 370 | 104 | 0.52 | 0.44 | 267 [21, 512] | 2.1 | 3 | 551 | 564 |
| ALL/ALL | fa_a_std_now_with | 0.33 | 76 | -10 | 0.45 | 0.42 | 85 [6, 164] | 2.1 | 3 | 201 | 225 |
| ALL/ALL | dl_ib_ext_up | 0.25 | 123 | 18 | 0.48 | 0.42 | 104 [6, 202] | 2.1 | 3 | 178 | 428 |
| ALL/ALL | cb_orb30_beyond | 0.52 | 63 | -13 | 0.44 | 0.42 | 75 [4, 146] | 2.1 | 4 | 215 | 92 |
| ALL/ALL | cb_stretch_slow_beyond | 0.58 | 65 | 1 | 0.43 | 0.42 | 64 [-3, 130] | 1.9 | 3 | 245 | 322 |

### Per book x session cells: top 6 by |t| (same stability filter, cells with >=150 trades)

**A7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | cb_nr4 | 0.23 | 276 | 74 | 0.60 | 0.50 | 202 [45, 359] | 2.5 | 3 | 422 | 151 |
| A7/0 | wl_tdom_seasonal_with | 0.53 | 65 | 200 | 0.50 | 0.56 | -135 [-278, 9] | -1.8 | 3 | -141 | -127 |
| A7/0 | fa_nl30_std_with | 0.15 | 265 | 95 | 0.59 | 0.51 | 170 [-14, 355] | 1.8 | 3 | 44 | -648 |
| A7/0 | dl_pd_neutral | 0.10 | 284 | 102 | 0.60 | 0.52 | 182 [-37, 400] | 1.6 | 3 | 239 | 543 |
| A7/0 | dl_against_va | 0.08 | 299 | 104 | 0.61 | 0.52 | 195 [-47, 436] | 1.6 | 4 | 191 | -385 |
| A7/0 | fa_nl15_std_with | 0.22 | 221 | 92 | 0.57 | 0.51 | 129 [-32, 290] | 1.6 | 3 | 143 | 105 |

**H7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | wl_tdom_last3 | 0.14 | 557 | 143 | 0.54 | 0.47 | 414 [-148, 976] | 1.4 | 3 | 92 | -1355 |
| H7/0 | fa_nl15_fast_with | 0.21 | 4 | 263 | 0.46 | 0.49 | -259 [-705, 187] | -1.1 | 3 | -621 | 148 |
| H7/0 | dl_pd_normal | 0.14 | 76 | 230 | 0.41 | 0.49 | -154 [-650, 343] | -0.6 | 3 | -183 | -203 |
| H7/0 | dl_poc_side_with | 0.84 | 198 | 263 | 0.48 | 0.49 | -65 [-548, 417] | -0.3 | 3 | -494 | 17 |

**H7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | wl_volbo_fast_beyond | 0.42 | 234 | -91 | 0.57 | 0.42 | 325 [87, 562] | 2.7 | 3 | 538 | 622 |
| H7/3 | dl_open_outside_va | 0.63 | 161 | -149 | 0.53 | 0.41 | 310 [69, 552] | 2.5 | 3 | 606 | -1259 |
| H7/3 | wl_volbo_fast_hit | 0.55 | 146 | -78 | 0.53 | 0.42 | 223 [-10, 457] | 1.9 | 4 | 428 | 527 |
| H7/3 | fa_a_fast_fresh30 | 0.46 | -59 | 136 | 0.44 | 0.52 | -195 [-431, 40] | -1.6 | 3 | -585 | -544 |
| H7/3 | dl_excess_low | 0.81 | -1 | 225 | 0.46 | 0.57 | -226 [-525, 73] | -1.5 | 3 | -72 | -118 |
| H7/3 | cb_stretch_fast_beyond | 0.62 | 102 | -49 | 0.50 | 0.45 | 151 [-91, 393] | 1.2 | 3 | 131 | 137 |

**K7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | dl_poc_side_with | 0.61 | 128 | 29 | 0.46 | 0.43 | 98 [-4, 201] | 1.9 | 4 | 115 | 113 |
| K7/0 | wl_tdom_10_16 | 0.32 | 38 | 114 | 0.42 | 0.46 | -76 [-184, 32] | -1.4 | 3 | -99 | -135 |
| K7/0 | fa_above_pr_with | 0.56 | 120 | 51 | 0.46 | 0.43 | 69 [-33, 170] | 1.3 | 4 | 87 | 330 |
| K7/0 | cb_nr7 | 0.12 | 5 | 101 | 0.41 | 0.45 | -96 [-247, 55] | -1.2 | 4 | -90 | -245 |
| K7/0 | dl_excess_high | 0.80 | 74 | 150 | 0.44 | 0.47 | -75 [-203, 52] | -1.2 | 3 | -197 | -35 |
| K7/0 | cb_inside_nr4 | 0.05 | 223 | 83 | 0.48 | 0.44 | 140 [-108, 388] | 1.1 | 3 | 128 | 156 |

**K7 session 1**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | wl_tdom_seasonal_with | 0.51 | 101 | 4 | 0.44 | 0.42 | 97 [-28, 221] | 1.5 | 3 | 71 | 8 |
| K7/1 | dl_inside_va | 0.37 | -13 | 71 | 0.40 | 0.45 | -84 [-205, 37] | -1.4 | 3 | -52 | -79 |
| K7/1 | dl_pd_normvar_with | 0.34 | -10 | 66 | 0.40 | 0.44 | -76 [-200, 49] | -1.2 | 3 | -210 | -351 |
| K7/1 | cb_nr7 | 0.14 | 120 | 27 | 0.45 | 0.42 | 93 [-82, 269] | 1.0 | 3 | 179 | 240 |
| K7/1 | dl_against_va | 0.24 | 94 | 23 | 0.45 | 0.42 | 71 [-64, 206] | 1.0 | 4 | 73 | 240 |
| K7/1 | wl_tdom_first3 | 0.15 | -24 | 51 | 0.38 | 0.44 | -75 [-236, 87] | -0.9 | 4 | -2 | -9 |

**K7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | cb_prior_wide | 0.12 | -206 | 41 | 0.32 | 0.44 | -247 [-394, -99] | -3.3 | 4 | -798 | -851 |
| K7/3 | dl_excess_support_with | 0.68 | -30 | 100 | 0.41 | 0.47 | -130 [-238, -22] | -2.4 | 3 | -249 | -42 |
| K7/3 | dl_pd_neutral | 0.12 | 157 | -9 | 0.50 | 0.42 | 166 [10, 321] | 2.1 | 4 | 246 | -249 |
| K7/3 | cb_nr4 | 0.26 | 95 | -18 | 0.47 | 0.41 | 114 [-1, 228] | 1.9 | 4 | 97 | 18 |
| K7/3 | cb_inside | 0.12 | 136 | -5 | 0.48 | 0.42 | 142 [-14, 297] | 1.8 | 4 | 217 | -482 |
| K7/3 | wl_smash_with | 0.29 | -58 | 40 | 0.39 | 0.44 | -98 [-209, 12] | -1.7 | 3 | -150 | 113 |

**K7 session 4**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | cb_stretch_slow_hit | 0.70 | 126 | -70 | 0.48 | 0.41 | 195 [49, 342] | 2.6 | 4 | 469 | 783 |
| K7/4 | cb_stretch_std_hit | 0.70 | 120 | -60 | 0.48 | 0.42 | 180 [33, 328] | 2.4 | 4 | 443 | 561 |
| K7/4 | dl_excess_low | 0.82 | 101 | -113 | 0.47 | 0.41 | 214 [39, 390] | 2.4 | 4 | 415 | 425 |
| K7/4 | cb_stretch_fast_hit | 0.70 | 117 | -54 | 0.48 | 0.42 | 171 [22, 320] | 2.2 | 4 | 313 | 617 |
| K7/4 | cb_stretch_slow_beyond | 0.48 | 150 | -11 | 0.48 | 0.44 | 162 [19, 304] | 2.2 | 4 | 249 | 515 |
| K7/4 | dl_r80_done | 0.09 | -172 | 91 | 0.38 | 0.47 | -263 [-497, -29] | -2.2 | 3 | -501 | -375 |

**M7 session 1**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | dl_pd_neutral | 0.11 | 262 | -31 | 0.50 | 0.40 | 293 [116, 469] | 3.2 | 4 | 480 | 619 |
| M7/1 | fa_nl30_slow_with | 0.12 | 140 | -19 | 0.46 | 0.40 | 159 [-0, 319] | 2.0 | 3 | 28 | -235 |
| M7/1 | dl_pd_neutral_ext | 0.06 | 200 | -12 | 0.49 | 0.40 | 212 [-17, 441] | 1.8 | 4 | 666 | 1159 |
| M7/1 | fa_nl60_slow_with | 0.10 | 137 | -15 | 0.46 | 0.40 | 152 [-27, 331] | 1.7 | 3 | 187 | 846 |
| M7/1 | wl_tdom_10_16 | 0.34 | 56 | -28 | 0.44 | 0.39 | 84 [-30, 197] | 1.4 | 4 | 17 | 131 |
| M7/1 | dl_poc_side_with | 0.65 | -26 | 50 | 0.40 | 0.42 | -76 [-185, 34] | -1.4 | 4 | -78 | -60 |

**M7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | dl_pd_normal | 0.11 | -179 | 68 | 0.34 | 0.45 | -247 [-407, -88] | -3.0 | 4 | -133 | -110 |
| M7/3 | dl_pd_neutral | 0.12 | 248 | 11 | 0.55 | 0.42 | 237 [77, 398] | 2.9 | 4 | 410 | 227 |
| M7/3 | cb_prior_wide | 0.12 | -104 | 60 | 0.36 | 0.45 | -165 [-318, -11] | -2.1 | 4 | -199 | 46 |
| M7/3 | fa_a_std_now_with | 0.37 | 105 | -8 | 0.47 | 0.41 | 113 [4, 223] | 2.0 | 4 | 156 | 92 |
| M7/3 | cb_nr4 | 0.26 | 115 | 13 | 0.47 | 0.42 | 102 [-16, 219] | 1.7 | 4 | 85 | 21 |
| M7/3 | wl_oops_with | 0.13 | -71 | 58 | 0.37 | 0.45 | -129 [-282, 23] | -1.7 | 3 | -144 | 85 |

**O7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | cb_stretch_fast_beyond | 0.50 | 274 | 89 | 0.42 | 0.34 | 185 [-29, 398] | 1.7 | 4 | 187 | 1128 |
| O7/3 | wl_tdom_4_9 | 0.31 | 46 | 237 | 0.31 | 0.40 | -191 [-417, 35] | -1.7 | 3 | -167 | -239 |
| O7/3 | wl_smash_with | 0.29 | 54 | 230 | 0.33 | 0.39 | -177 [-406, 52] | -1.5 | 3 | -39 | 443 |
| O7/3 | dl_excess_high | 0.73 | 216 | 74 | 0.39 | 0.34 | 143 [-90, 376] | 1.2 | 3 | 1077 | 865 |
| O7/3 | dl_open_outside_va | 0.66 | 223 | 101 | 0.40 | 0.34 | 122 [-103, 346] | 1.1 | 3 | 673 | -264 |
| O7/3 | dl_above_va_with | 0.48 | 233 | 127 | 0.39 | 0.36 | 106 [-107, 319] | 1.0 | 3 | 586 | 912 |

**P7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | dl_sp_ahead_120 | 0.07 | -565 | 507 | 0.34 | 0.45 | -1072 [-1837, -306] | -2.7 | 3 | -1510 | -1451 |
| P7/0 | dl_sp_ahead_any | 0.20 | -56 | 556 | 0.39 | 0.45 | -612 [-1102, -122] | -2.4 | 4 | -899 | -1088 |
| P7/0 | fa_nl30_slow_with | 0.13 | 904 | 360 | 0.49 | 0.43 | 543 [-43, 1130] | 1.8 | 4 | 296 | 655 |
| P7/0 | dl_excess_high | 0.79 | 516 | 124 | 0.44 | 0.43 | 392 [-88, 872] | 1.6 | 3 | 844 | 652 |
| P7/0 | fa_above_pr_with | 0.62 | 540 | 257 | 0.45 | 0.43 | 283 [-117, 683] | 1.4 | 3 | 605 | 943 |
| P7/0 | dl_pd_neutral | 0.11 | 829 | 382 | 0.47 | 0.44 | 447 [-211, 1105] | 1.3 | 3 | 250 | 1435 |

**P7 session 1**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | fa_inside_pr | 0.13 | 259 | 7 | 0.41 | 0.38 | 251 [-86, 589] | 1.5 | 4 | 445 | 244 |
| P7/1 | dl_pd_neutral_ext | 0.06 | 364 | 20 | 0.42 | 0.38 | 344 [-181, 868] | 1.3 | 4 | 455 | 143 |
| P7/1 | fa_nl30_slow_with | 0.13 | -138 | 66 | 0.35 | 0.39 | -204 [-524, 115] | -1.3 | 3 | -201 | -174 |
| P7/1 | dl_pd_normvar_with | 0.34 | -61 | 92 | 0.37 | 0.39 | -153 [-395, 88] | -1.2 | 3 | -289 | -351 |
| P7/1 | fa_nl30_std_with | 0.12 | -127 | 63 | 0.34 | 0.39 | -190 [-534, 154] | -1.1 | 3 | -244 | -1672 |
| P7/1 | wl_tdom_first3 | 0.15 | -114 | 67 | 0.35 | 0.39 | -181 [-508, 147] | -1.1 | 3 | -377 | -403 |

**P7 session 3**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | cb_stretch_std_beyond | 0.64 | 87 | -227 | 0.40 | 0.37 | 313 [61, 566] | 2.4 | 3 | 761 | 575 |
| P7/3 | cb_stretch_std_hit | 0.82 | 40 | -324 | 0.40 | 0.34 | 364 [68, 659] | 2.4 | 3 | 971 | 826 |
| P7/3 | cb_stretch_slow_hit | 0.81 | 40 | -317 | 0.40 | 0.35 | 356 [62, 650] | 2.4 | 3 | 964 | 811 |
| P7/3 | dl_inside_va | 0.28 | -262 | 62 | 0.34 | 0.41 | -324 [-593, -55] | -2.4 | 3 | -762 | -753 |
| P7/3 | wl_gap_with | 0.20 | 299 | -107 | 0.45 | 0.38 | 406 [44, 769] | 2.2 | 3 | 416 | 1022 |
| P7/3 | cb_stretch_fast_hit | 0.83 | 32 | -305 | 0.40 | 0.35 | 337 [35, 638] | 2.2 | 3 | 804 | 1114 |

**U7 session 0**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | dl_pd_normal | 0.15 | -343 | 512 | 0.42 | 0.55 | -855 [-1573, -138] | -2.3 | 3 | -476 | -1625 |
| U7/0 | dl_pd_normvar_with | 0.24 | 807 | 253 | 0.61 | 0.50 | 554 [-36, 1144] | 1.8 | 3 | 371 | 2207 |
| U7/0 | dl_excess_low | 0.82 | 280 | 873 | 0.51 | 0.61 | -593 [-1261, 75] | -1.7 | 4 | -776 | -1877 |
| U7/0 | cb_prior_wide | 0.13 | -69 | 455 | 0.48 | 0.54 | -524 [-1308, 261] | -1.3 | 3 | -1227 | 528 |
| U7/0 | fa_nl30_std_with | 0.11 | 827 | 330 | 0.64 | 0.51 | 497 [-273, 1266] | 1.3 | 3 | 1198 | 2536 |
| U7/0 | dl_poc_side_with | 0.49 | 247 | 524 | 0.52 | 0.54 | -278 [-795, 239] | -1.1 | 4 | -535 | -1568 |

**U7 session 1**

| cell | condition | share yes | exp yes $ | exp no $ | WR yes | WR no | lift $ [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | dl_above_va_with | 0.19 | -405 | 270 | 0.41 | 0.53 | -674 [-1302, -47] | -2.1 | 3 | -625 | -1416 |
| U7/1 | dl_pd_normal | 0.11 | 805 | 54 | 0.63 | 0.49 | 751 [-0, 1502] | 2.0 | 3 | 110 | 668 |
| U7/1 | dl_poc_side_with | 0.37 | -163 | 316 | 0.46 | 0.53 | -479 [-979, 22] | -1.9 | 4 | -891 | -974 |
| U7/1 | fa_nl15_slow_with | 0.21 | -200 | 228 | 0.47 | 0.52 | -428 [-1020, 164] | -1.4 | 3 | -565 | -1153 |
| U7/1 | fa_pr_narrow | 0.29 | 330 | 60 | 0.53 | 0.49 | 270 [-261, 800] | 1.0 | 3 | 288 | 485 |
| U7/1 | dl_pd_normvar_against | 0.39 | 3 | 227 | 0.48 | 0.52 | -224 [-715, 267] | -0.9 | 4 | -1 | -7 |

Full per-cell table (all conditions, all cells): /mnt/l2/l2vast/_confl/cols_cf5/score_B_sess_named.parquet
