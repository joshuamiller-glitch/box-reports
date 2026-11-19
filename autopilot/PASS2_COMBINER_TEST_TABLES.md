### TL3_ASI_L86781ac0_RA7 (Asia) vrb_700 | trig_bands_bollinger | break | {"n": 20, "k": 1.5} | plain60/60 | long | events 6999 | CPU 107.2 s (wall includes search-aware null 32.1 s)
Reference (all events, screen walker): L6M 1770 $/wk, ulcer 5246, maxDD 17045, worst wk -6505, 24.6 trades/wk (645); L3M 181 $/wk, ulcer 6661. Floor: 60% of trades and 5/wk. Scored settings 1329, library 341 conditions (81 not applicable).
- C1: K contest 428 (of 1079 scored), best 4.112 vs max-T q90 1.427 -> beats max-T: True ; search-aware null (10 permuted searches) p=0.55, null bests [4.4694, 4.3556, 3.426, 5.0349, 5.0314, 3.9487, 3.4686, 3.0802, 5.0593, 2.6964]
- C2: K contest 91 (of 122 scored), best 0.756 vs max-T q90 1.112 -> beats max-T: False
- C3: K contest 71 (of 128 scored), best 0.545 vs max-T q90 1.062 -> beats max-T: False

| setting | what | L6M $/wk | ulcer | maxDD | worst wk | tpw | L3M $/wk | ulcer | p6 (10k) | hold-out Y23 / Y24 / Y25 $/wk (ulcer) vs ref |
|---|---|---|---|---|---|---|---|---|---|---|
| C1_E3_1_12_111_217 | 1-of-3{LV_PWK_near_back_2u, LV_SESSRUN_room_6u, b_imb5_agree_gt0.4} | 3486 | 1747 | 5720 | -4173 | 15.9 | 2342 | 1890 | 0.0001 | 5 (5784) vs 324 (3968) / 717 (2228) vs 743 (3856) / -222 (14356) vs 593 (8834) |
| C1_E3_1_111_217_227 | 1-of-3{LV_SESSRUN_room_6u, b_imb5_agree_gt0.4, WALL_support_r3_d4} | 3347 | 2055 | 6000 | -3446 | 16.3 | 1740 | 2201 | 0.0004 | 74 (4296) vs 324 (3968) / 820 (2151) vs 743 (3856) / -75 (14530) vs 593 (8834) |
| C1_E3_2_111_110_173 | 2-of-3{LV_SESSRUN_room_6u, LV_SESSRUN_room_3u, GRID_momentum_squeeze:fire_native} | 2896 | 1723 | 4185 | -4185 | 16.0 | 2093 | 1569 | 0.0001 | -12 (5028) vs 324 (3968) / 701 (2247) vs 743 (3856) / -178 (12059) vs 593 (8834) |
| C1_X10_5_5a303c | 5-of-10{LV_SWING_react_2u, LV_SESSRUN_near_back_2u, LV_SESSRUN_room_3u, LV_SESSRUN_room_6u | 4548 | 1106 | 4118 | -3432 | 16.7 | 3253 | 1064 | 0.0001 | 105 (3511) vs 324 (3968) / 700 (2771) vs 743 (3856) / -365 (13209) vs 593 (8834) |
| C1_X10_5_381f5b | 5-of-10{LV_PWK_near_back_2u, LV_SWING_react_2u, LV_SESSRUN_near_back_2u, LV_SESSRUN_room_3 | 4167 | 1053 | 3471 | -3427 | 16.1 | 2534 | 1041 | 0.0001 | 65 (3252) vs 324 (3968) / 788 (2345) vs 743 (3856) / -335 (14903) vs 593 (8834) |
| C2_ER50_p33_trend_only | trend_only ER50 at trailing-60-session p33 | 2553 | 3399 | 10179 | -4323 | 19.6 | 1432 | 2920 | 0.0362 | 205 (4679) vs 324 (3968) / 486 (5651) vs 743 (3856) / 157 (7338) vs 593 (8834) |
| C2_ER50_p50_trend_only | trend_only ER50 at trailing-60-session p50 | 2030 | 2686 | 7007 | -3673 | 15.9 | 1334 | 2522 | 0.0472 | -81 (9026) vs 324 (3968) / 393 (3480) vs 743 (3856) / 137 (6334) vs 593 (8834) |
| C2_ADX14_p50_trend_only | trend_only ADX14 at trailing-60-session p50 | 2273 | 3606 | 8657 | -5291 | 16.2 | 1052 | 3099 | 0.0725 | 41 (6811) vs 324 (3968) / 612 (1983) vs 743 (3856) / 336 (10614) vs 593 (8834) |
| C3_dropblk5 | drop 30-min block 5 | 2372 | 4348 | 13722 | -6483 | 23.5 | 584 | 4863 | 0.0354 | 353 (4215) vs 324 (3968) / 650 (4292) vs 743 (3856) / 529 (8179) vs 593 (8834) |

### TL3_ASI_Lc4e74264_RA7 (Asia) time_m_3 | trig_pullback_ema | depth | {"len": 10, "w": 0.5} | plain60/60 | long | events 36736 | CPU 323.3 s (wall includes search-aware null 150.7 s)
Reference (all events, screen walker): L6M 1341 $/wk, ulcer 4863, maxDD 11678, worst wk -8824, 33.2 trades/wk (870); L3M 257 $/wk, ulcer 5138. Floor: 60% of trades and 5/wk. Scored settings 1323, library 339 conditions (86 not applicable).
- C1: K contest 462 (of 1073 scored), best 2.935 vs max-T q90 1.264 -> beats max-T: True ; search-aware null (10 permuted searches) p=0.82, null bests [4.1829, 4.5961, 2.9057, 4.6099, 2.3971, 3.4424, 3.7017, 4.3294, 3.7815, 4.0971]
- C2: K contest 94 (of 122 scored), best 0.722 vs max-T q90 0.905 -> beats max-T: False
- C3: K contest 74 (of 128 scored), best 0.436 vs max-T q90 0.871 -> beats max-T: False

| setting | what | L6M $/wk | ulcer | maxDD | worst wk | tpw | L3M $/wk | ulcer | p6 (10k) | hold-out Y23 / Y24 / Y25 $/wk (ulcer) vs ref |
|---|---|---|---|---|---|---|---|---|---|---|
| C1_E3_2_71_205_292 | 2-of-3{LV_ZONES_room_6u, FC_t_run_vol_sign, XM_NKD_newext15_with} | 2955 | 2830 | 8201 | -5904 | 25.8 | 2581 | 3211 | 0.0022 | 51 (4612) vs 148 (5786) / 293 (5250) vs -96 (13496) / 601 (5032) vs 783 (6088) |
| C1_E3_2_71_291_260 | 2-of-3{LV_ZONES_room_6u, XM_NKD_newext5_with, XM_RTY_rel60_leadsNQ_lt-1} | 2649 | 2161 | 8254 | -5573 | 20.7 | 1890 | 2735 | 0.0012 | 68 (3258) vs 148 (5786) / 378 (3742) vs -96 (13496) / 367 (4568) vs 783 (6088) |
| C1_E3_2_71_292_250 | 2-of-3{LV_ZONES_room_6u, XM_NKD_newext15_with, XM_RTY_own5_agree_gt1} | 2467 | 2255 | 8347 | -8347 | 20.4 | 1491 | 2625 | 0.0031 | -41 (4894) vs 148 (5786) / 495 (3652) vs -96 (13496) / 999 (2587) vs 783 (6088) |
| C1_X9_8_c323c6 | 8-of-9{LV_ZONES_room_3u, LV_ZONES_room_6u, LV_ROUND50_react_2u, MACD12_26_9_hist_sign, CCI | 4521 | 1541 | 5235 | -1679 | 20.2 | 3041 | 1779 | 0.0001 | 169 (1919) vs 148 (5786) / 554 (5542) vs -96 (13496) / 16 (5839) vs 783 (6088) |
| C1_X9_8_1b4214 | 8-of-9{LV_ZONES_room_3u, LV_ZONES_room_6u, LV_ROUND50_react_2u, MACD12_26_9_hist_sign, CCI | 3923 | 1430 | 4501 | -1996 | 20.6 | 2335 | 1758 | 0.0001 | 27 (4111) vs 148 (5786) / 366 (5720) vs -96 (13496) / 69 (5412) vs 783 (6088) |
| C2_SQZ_width_p25_flip_in_range | flip_in_range SQZ_width at trailing-60-session p25 | 2585 | 4211 | 13231 | -8819 | 33.2 | 1285 | 3907 | 0.0087 | -407 (10967) vs 148 (5786) / -30 (9634) vs -96 (13496) / 296 (8129) vs 783 (6088) |
| C2_SQZ_width_p33_trend_only | trend_only SQZ_width at trailing-60-session p33 | 2614 | 3621 | 10457 | -9532 | 30.2 | 1371 | 3934 | 0.0088 | 196 (5788) vs 148 (5786) / 216 (10697) vs -96 (13496) / 375 (6966) vs 783 (6088) |
| C2_SQZ_skip_in_squeeze | skip_in_squeeze | 2255 | 4302 | 11944 | -8802 | 31.4 | 304 | 5085 | 0.0334 | 151 (6123) vs 148 (5786) / 139 (11140) vs -96 (13496) / 587 (7514) vs 783 (6088) |
| C3_dropblk4 | drop 30-min block 4 | 1921 | 4409 | 11656 | -9839 | 31.7 | 1016 | 4173 | 0.0260 | 233 (3480) vs 148 (5786) / -51 (13160) vs -96 (13496) / 480 (7278) vs 783 (6088) |

### TL3_ASI_Ldcdb0b6e_RA7 (Asia) cdr_100 | trig_momentum_mvote | v3of5 | {"scale": 0.25, "thr": 0.25} | plain60/60 | long | events 7132 | CPU 93.8 s (wall includes search-aware null 31.0 s)
Reference (all events, screen walker): L6M 1971 $/wk, ulcer 3695, maxDD 11749, worst wk -7436, 23.4 trades/wk (612); L3M 1848 $/wk, ulcer 4576. Floor: 60% of trades and 5/wk. Scored settings 1324, library 340 conditions (85 not applicable).
- C1: K contest 407 (of 1074 scored), best 6.002 vs max-T q90 1.418 -> beats max-T: True ; search-aware null (10 permuted searches) p=0.09, null bests [4.9651, 4.3207, 5.7495, 4.9237, 4.6938, 4.0744, 3.6572, 5.483, 5.8699, 4.2498]
- C2: K contest 90 (of 122 scored), best 0.837 vs max-T q90 1.309 -> beats max-T: False
- C3: K contest 74 (of 128 scored), best 0.742 vs max-T q90 1.176 -> beats max-T: False

| setting | what | L6M $/wk | ulcer | maxDD | worst wk | tpw | L3M $/wk | ulcer | p6 (10k) | hold-out Y23 / Y24 / Y25 $/wk (ulcer) vs ref |
|---|---|---|---|---|---|---|---|---|---|---|
| C1_E3_1_34_330_47 | 1-of-3{LV_OPENS_near_back_1u, XM_6E_own15_agree_gt0.5, LV_VWAP_room_6u} | 3177 | 2193 | 6721 | -3546 | 15.4 | 2855 | 2622 | 0.0004 | 315 (2368) vs 373 (2614) / 966 (1741) vs 598 (5922) / -466 (16716) vs 306 (10551) |
| C1_E3_1_34_76_47 | 1-of-3{LV_OPENS_near_back_1u, LV_SWING_near_back_2u, LV_VWAP_room_6u} | 3203 | 2213 | 6913 | -4785 | 18.9 | 3442 | 2293 | 0.0002 | 291 (3051) vs 373 (2614) / 759 (3242) vs 598 (5922) / 6 (11526) vs 306 (10551) |
| C1_E3_1_330_35_226 | 1-of-3{XM_6E_own15_agree_gt0.5, LV_OPENS_react_1u, WALL_support_r3_d4} | 3058 | 2050 | 5468 | -2040 | 16.3 | 2147 | 2276 | 0.0002 | 461 (1891) vs 373 (2614) / 673 (2783) vs 598 (5922) / 79 (8802) vs 306 (10551) |
| C1_X8_4_26207c | 4-of-8{LV_OPENS_near_back_2u, LV_ROUND50_room_6u, LV_SESSRUN_room_6u, MACD12_26_9_line_sig | 4429 | 782 | 2720 | -2078 | 17.0 | 4488 | 705 | 0.0001 | 120 (4654) vs 373 (2614) / 317 (5436) vs 598 (5922) / -130 (11160) vs 306 (10551) |
| C1_X10_5_906aff | 5-of-10{LV_PDHL_near_back_0.5u, LV_OPENS_near_back_1u, LV_OPENS_near_back_2u, LV_SESSRUN_r | 4635 | 772 | 2580 | -419 | 16.8 | 4768 | 749 | 0.0001 | 148 (4405) vs 373 (2614) / 396 (4943) vs 598 (5922) / -90 (8525) vs 306 (10551) |
| C2_ER50_p67_range_only | range_only ER50 at trailing-60-session p67 | 1648 | 3206 | 9264 | -6519 | 16.6 | 1107 | 4173 | 0.0774 | 318 (2009) vs 373 (2614) / 303 (6672) vs 598 (5922) / 334 (7210) vs 306 (10551) |
| C2_ER50_p75_range_only | range_only ER50 at trailing-60-session p75 | 2014 | 3604 | 10481 | -6224 | 18.4 | 1940 | 4418 | 0.0664 | 262 (3088) vs 373 (2614) / 390 (5756) vs 598 (5922) / 168 (8238) vs 306 (10551) |
| C2_RANGE_sofar_vs_med_p67_range_only | range_only RANGE_sofar_vs_med at trailing-60-session p67 | 1910 | 3641 | 11749 | -7436 | 15.8 | 1143 | 4745 | 0.0294 | 452 (2813) vs 373 (2614) / 526 (5137) vs 598 (5922) / 170 (9753) vs 306 (10551) |
| C3_dropblk6 | drop 30-min block 6 | 2413 | 3252 | 10537 | -6224 | 22.4 | 2478 | 3634 | 0.0421 | 374 (2644) vs 373 (2614) / 596 (5356) vs 598 (5922) / 276 (10583) vs 306 (10551) |

### TL3_NYE_L678ebadd_RK7 (NYAM) tib_6000 | trig_levels_profile_va | retest_native | {"M": 10, "tol": 0.5} | sym15u | long | events 15406 | CPU 168.4 s (wall includes search-aware null 66.6 s)
Reference (all events, screen walker): L6M 2252 $/wk, ulcer 5885, maxDD 13104, worst wk -7873, 7.7 trades/wk (202); L3M 1599 $/wk, ulcer 5825. Floor: 60% of trades and 2/wk. Scored settings 1276, library 341 conditions (35 not applicable).
- C1: K contest 750 (of 1125 scored), best 8.537 vs max-T q90 1.393 -> beats max-T: True ; search-aware null (10 permuted searches) p=0.09, null bests [6.6081, 7.1614, 4.7937, 6.6731, 8.4444, 4.1989, 4.4359, 5.0994, 4.1191, 7.608]
- C2: K contest 102 (of 122 scored), best 0.892 vs max-T q90 1.165 -> beats max-T: False
- C3: K contest 20 (of 29 scored), best 0.590 vs max-T q90 0.895 -> beats max-T: False

| setting | what | L6M $/wk | ulcer | maxDD | worst wk | tpw | L3M $/wk | ulcer | p6 (10k) | hold-out Y23 / Y24 / Y25 $/wk (ulcer) vs ref |
|---|---|---|---|---|---|---|---|---|---|---|
| C1_E3_2_41_111_60 | 2-of-3{LV_VWAP_react_0.5u, LV_SESSRUN_room_6u, LV_PIVOT_near_back_2u} | 3629 | 1910 | 8712 | -4822 | 5.2 | 3462 | 1265 | 0.0001 | -466 (10868) vs -151 (19205) / 222 (17717) vs 98 (19420) / 471 (5584) vs 442 (9465) |
| C1_E3_2_41_60_252 | 2-of-3{LV_VWAP_react_0.5u, LV_PIVOT_near_back_2u, XM_RTY_own5_agree_gt1} | 3592 | 2087 | 7236 | -7236 | 5.2 | 2618 | 1608 | 0.0002 | 195 (5318) vs -151 (19205) / -214 (23553) vs 98 (19420) / 1054 (4031) vs 442 (9465) |
| C1_E3_2_81_229_252 | 2-of-3{LV_FIB_react_0.5u, WALL_opp_absent_r3_d10, XM_RTY_own5_agree_gt1} | 3782 | 2242 | 7152 | -5453 | 6.2 | 2801 | 1693 | 0.0002 | 693 (3303) vs -151 (19205) / -190 (23410) vs 98 (19420) / 627 (5930) vs 442 (9465) |
| C1_X10_5_7b88ee | 5-of-10{LV_PDHL_near_back_0.5u, LV_SESS_near_back_1u, LV_VWAP_react_0.5u, LV_FIB_react_0.5 | 6112 | 716 | 2536 | -1182 | 6.1 | 4540 | 866 | 0.0001 | -334 (13563) vs -151 (19205) / 493 (13203) vs 98 (19420) / -451 (22335) vs 442 (9465) |
| C1_X10_5_d88d1b | 5-of-10{LV_PDHL_near_back_0.5u, LV_PROFILE_near_back_2u, LV_PIVOT_near_back_1u, CCI14_risi | 5744 | 712 | 3811 | -2242 | 6.9 | 4665 | 822 | 0.0001 | -122 (8953) vs -151 (19205) / -597 (33480) vs 98 (19420) / 552 (4393) vs 442 (9465) |
| C2_SQZ_width_p25_trend_only | trend_only SQZ_width at trailing-60-session p25 | 2901 | 3253 | 10095 | -4897 | 7.3 | 1831 | 3674 | 0.0045 | -235 (13076) vs -151 (19205) / 241 (16916) vs 98 (19420) / 604 (10352) vs 442 (9465) |
| C2_PREV_RANGE_vs_med_p67_range_only | range_only PREV_RANGE_vs_med at trailing-60-session p67 | 1936 | 3017 | 8997 | -4382 | 5.3 | 1293 | 3068 | 0.0039 | -153 (14379) vs -151 (19205) / 57 (15401) vs 98 (19420) / 818 (7525) vs 442 (9465) |
| C2_PREV_RANGE_vs_med_p75_range_only | range_only PREV_RANGE_vs_med at trailing-60-session p75 | 2469 | 4096 | 10026 | -4382 | 6.0 | 1817 | 4095 | 0.0439 | -234 (17600) vs -151 (19205) / 290 (15157) vs 98 (19420) / 685 (7727) vs 442 (9465) |
| C3_dropdow34 | drop weekdays 3,4 | 2321 | 3935 | 10825 | -9153 | 4.9 | 2025 | 2206 | 0.0251 | -526 (21453) vs -151 (19205) / -44 (17415) vs 98 (19420) / 158 (4092) vs 442 (9465) |

### TL3_NYE_Lb44a3e99_RK7 (NYAM) tm300 | trig_tape_delta | cvd_follow | {"N": 10, "L": 100, "z": 1.5} | plain60/60 | long | events 2862 | CPU 44.5 s (wall includes search-aware null 17.2 s)
Reference (all events, screen walker): L6M 1117 $/wk, ulcer 5073, maxDD 13862, worst wk -5262, 12.6 trades/wk (329); L3M 395 $/wk, ulcer 6760. Floor: 60% of trades and 2/wk. Scored settings 1264, library 327 conditions (34 not applicable).
- C1: K contest 415 (of 1113 scored), best 2.606 vs max-T q90 1.044 -> beats max-T: True ; search-aware null (10 permuted searches) p=0.27, null bests [2.0611, 2.5101, 2.4745, 1.8715, 2.0388, 2.3472, 3.0206, 2.3176, 2.482, 3.8861]
- C2: K contest 85 (of 122 scored), best 0.654 vs max-T q90 0.867 -> beats max-T: False
- C3: K contest 22 (of 29 scored), best 0.392 vs max-T q90 0.662 -> beats max-T: False

| setting | what | L6M $/wk | ulcer | maxDD | worst wk | tpw | L3M $/wk | ulcer | p6 (10k) | hold-out Y23 / Y24 / Y25 $/wk (ulcer) vs ref |
|---|---|---|---|---|---|---|---|---|---|---|
| C1_E3_1_31_75_34 | 1-of-3{LV_ORIB_room_6u, LV_SWING_react_1u, LV_OPENS_near_back_1u} | 2380 | 1937 | 6422 | -3529 | 9.6 | 1697 | 2364 | 0.0002 | -3 (5820) vs 372 (5637) / 775 (4717) vs 901 (4853) / 412 (12888) vs 878 (6626) |
| C1_E3_2_191_34_38 | 2-of-3{FC_t_blk10_dlt_sign, LV_OPENS_near_back_1u, LV_OPENS_room_3u} | 1860 | 1656 | 5735 | -2482 | 7.6 | 1598 | 1969 | 0.0010 | 252 (6750) vs 372 (5637) / 253 (9675) vs 901 (4853) / 634 (3768) vs 878 (6626) |
| C1_Gmaj_4 | 2-of-4{FC_t_blk10_dlt_sign, LV_ORIB_room_3u, LV_SWING_react_1u, LV_OPENS_near_back_0.5u} | 2406 | 2007 | 7134 | -4744 | 8.1 | 2012 | 2379 | 0.0002 | 245 (6117) vs 372 (5637) / 707 (4088) vs 901 (4853) / 354 (13742) vs 878 (6626) |
| C1_X8_4_da669e | 4-of-8{LV_ORIB_room_3u, LV_OPENS_near_back_0.5u, LV_ZONES_room_6u, CVD3_sign, FC_t_blk10_d | 2834 | 1087 | 4931 | -1910 | 8.8 | 2429 | 1388 | 0.0001 | 297 (3431) vs 372 (5637) / 415 (4843) vs 901 (4853) / 731 (5640) vs 878 (6626) |
| C1_X10_5_61fb50 | 5-of-10{LV_ORIB_near_back_0.5u, LV_SWING_react_1u, LV_SESSRUN_near_back_0.5u, EMA20_slope, | 2489 | 969 | 3663 | -1756 | 8.0 | 2448 | 1069 | 0.0001 | -12 (8824) vs 372 (5637) / 489 (4668) vs 901 (4853) / 459 (7370) vs 878 (6626) |
| C2_ADX14_p67_range_only | range_only ADX14 at trailing-60-session p67 | 1002 | 2404 | 9389 | -5020 | 8.5 | 554 | 1851 | 0.0616 | 232 (6054) vs 372 (5637) / 121 (6579) vs 901 (4853) / 414 (8948) vs 878 (6626) |
| C2_ADX14_p75_range_only | range_only ADX14 at trailing-60-session p75 | 1357 | 2139 | 6999 | -5020 | 9.8 | 1098 | 1595 | 0.0079 | 111 (9132) vs 372 (5637) / 320 (4189) vs 901 (4853) / 575 (7563) vs 878 (6626) |
| C2_ADX14_p75_flip_in_trend | flip_in_trend ADX14 at trailing-60-session p75 | 1808 | 2763 | 7007 | -5020 | 12.6 | 2300 | 1897 | 0.0175 | -81 (12932) vs 372 (5637) / -331 (16568) vs 901 (4853) / 241 (13907) vs 878 (6626) |
| C3_dropdow3 | drop weekday 3 (0=Mon) | 1101 | 2812 | 7325 | -5758 | 10.0 | 989 | 3250 | 0.1112 | 24 (7130) vs 372 (5637) / 590 (3704) vs 901 (4853) / 694 (5674) vs 878 (6626) |

### TL3_NYE_Ld9ea2776_RK7 (NYAM) rng_10 | trig_levels_profile_nodes | false_break_native | {"M": 3, "k": 0.5} | asym15u/30u | long | events 46881 | CPU 516.4 s (wall includes search-aware null 198.9 s)
Reference (all events, screen walker): L6M 900 $/wk, ulcer 9234, maxDD 23672, worst wk -8326, 11.4 trades/wk (299); L3M 1131 $/wk, ulcer 7210. Floor: 60% of trades and 2/wk. Scored settings 1247, library 310 conditions (35 not applicable).
- C1: K contest 648 (of 1096 scored), best 4.430 vs max-T q90 1.060 -> beats max-T: True ; search-aware null (10 permuted searches) p=0.36, null bests [4.8495, 3.7224, 4.3229, 3.6191, 3.5745, 4.6082, 4.7236, 3.4058, 3.4236, 4.3495]
- C2: K contest 109 (of 122 scored), best 0.535 vs max-T q90 0.901 -> beats max-T: False
- C3: K contest 21 (of 29 scored), best 0.685 vs max-T q90 0.548 -> beats max-T: True

| setting | what | L6M $/wk | ulcer | maxDD | worst wk | tpw | L3M $/wk | ulcer | p6 (10k) | hold-out Y23 / Y24 / Y25 $/wk (ulcer) vs ref |
|---|---|---|---|---|---|---|---|---|---|---|
| C1_E3_2_172_213_301 | 2-of-3{GRID_momentum_rsi:revert_native, XM_ES_rel15_withNQ_gt1, XM_6E_own15_inverse_gt0.5} | 3966 | 4259 | 15426 | -11491 | 9.8 | 1963 | 4220 | 0.0003 | -431 (23594) vs 426 (5590) / -828 (30909) vs 1103 (4320) / 60 (21666) vs 606 (12779) |
| C1_Gmaj_4 | 2-of-4{XM_6J_own15_inverse_gt0.5, LV_ORIB_near_back_0.5u, XM_ZN_own15_inverse_gt0.5, GRID_ | 3386 | 3405 | 11001 | -6781 | 9.6 | 1266 | 3773 | 0.0003 | 237 (4532) vs 426 (5590) / -33 (14404) vs 1103 (4320) / -397 (33416) vs 606 (12779) |
| C1_Gmaj_5 | 3-of-5{XM_6J_own15_inverse_gt0.5, LV_ORIB_near_back_0.5u, XM_ZN_own15_inverse_gt0.5, GRID_ | 3410 | 3352 | 10469 | -4737 | 7.5 | 1538 | 3976 | 0.0006 | 116 (5674) vs 426 (5590) / -176 (14871) vs 1103 (4320) / -449 (39783) vs 606 (12779) |
| C1_X8_4_0ce4c4 | 4-of-8{LV_SESS_near_back_1u, LV_PIVOT_near_back_1u, GRID_momentum_rsi:revert_native, VOLRE | 4511 | 1172 | 5473 | -1703 | 8.3 | 3805 | 1109 | 0.0001 | 15 (10112) vs 426 (5590) / 518 (6408) vs 1103 (4320) / -101 (22446) vs 606 (12779) |
| C1_X9_5_dfb9cd | 5-of-9{LV_FIB_near_back_2u, LV_SESSRUN_room_6u, MACD12_26_9_hist_sign, RSI14_agree60, GRID | 6616 | 1493 | 5674 | -22 | 10.1 | 4166 | 1437 | 0.0001 | -391 (12652) vs 426 (5590) / 245 (8245) vs 1103 (4320) / 113 (21484) vs 606 (12779) |
| C2_ER20_p67_trend_only | trend_only ER20 at trailing-60-session p67 | 1818 | 4397 | 10425 | -5004 | 10.5 | 35 | 5337 | 0.0167 | -236 (11328) vs 426 (5590) / 364 (9358) vs 1103 (4320) / 301 (13612) vs 606 (12779) |
| C2_ER20_p75_trend_only | trend_only ER20 at trailing-60-session p75 | 2064 | 3856 | 11728 | -11695 | 10.3 | 1700 | 3969 | 0.0062 | -609 (18113) vs 426 (5590) / 183 (5996) vs 1103 (4320) / -52 (24419) vs 606 (12779) |
| C2_ER50_p33_trend_only | trend_only ER50 at trailing-60-session p33 | 2240 | 5292 | 14888 | -8326 | 11.1 | 1725 | 4288 | 0.0218 | 85 (9780) vs 426 (5590) / 347 (9091) vs 1103 (4320) / 115 (18519) vs 606 (12779) |
| C3_dropblk0 | drop 30-min block 0 | 2383 | 3482 | 8883 | -8883 | 7.6 | 972 | 2937 | 0.0025 | -771 (19329) vs 426 (5590) / -204 (13544) vs 1103 (4320) / 40 (10399) vs 606 (12779) |

