# DS3_CONFLUENCE_ITEMS_CF5 - Block 3 (desk / named-trader systems), STEP 3 each alone

**Verdict line (updated 2026-11-15 00:09Z): sub-blocks A, B, B2, C1, C2, D are built and scored each alone (4274 conditions); no item is claimed as a finding, the tables are the map (flow measures at our entries are mostly null, like the earlier MBO screen).**

Signal universe = W-CF1 entry table signals_all.parquet (sig_id = book7_sig_ts); causality checked by truncated-history recompute for A and B.

## Sub-block A: named-system indicators on HTF bars (DeMark, Raschke, Connors, Chande, Wilder, Kase, Ehlers, Brooks, statistical desk measures)

### A - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 3965 conditions; 98292 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 544 conditions with |t|>2 (chance alone: about 198). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | wl_volstop_flip_fast_1d_against10 | 0.32 | 3.0 | 155.1 | 0.42 | 0.45 | -152.1 [-217.0, -87.1] | -4.6 | 4 | -82.9 | -212.9 |
| ALL/ALL | cn_double7_fast_3m_against10 | 0.31 | 14.3 | 146.7 | 0.42 | 0.44 | -132.3 [-192.3, -72.3] | -4.3 | 4 | -134.6 | -285.3 |
| ALL/ALL | rk_soup_fast_3m_state | 0.29 | 1.9 | 148.5 | 0.41 | 0.45 | -146.6 [-213.3, -79.8] | -4.3 | 4 | -179.6 | -140.1 |
| ALL/ALL | wl_volstop_dist_std_5m_side | 0.80 | 135.0 | -10.9 | 0.44 | 0.41 | 145.9 [79.3, 212.5] | 4.3 | 4 | 79.1 | 163.5 |
| ALL/ALL | eh_ebsw_slow_5m_side | 0.75 | 138.7 | 7.8 | 0.44 | 0.42 | 130.9 [70.4, 191.3] | 4.2 | 4 | 194.3 | 378.9 |
| ALL/ALL | wl_volstop_std_5m_side | 0.80 | 134.6 | -8.6 | 0.44 | 0.41 | 143.2 [76.9, 209.6] | 4.2 | 4 | 71.9 | 139.1 |
| ALL/ALL | cn_double7_1m_against_state | 0.26 | 11.4 | 138.5 | 0.42 | 0.44 | -127.2 [-188.0, -66.3] | -4.1 | 4 | -131.1 | -293.7 |
| ALL/ALL | ch_fosc_fast_1d_fresh5 | 0.46 | 175.9 | 46.9 | 0.45 | 0.42 | 129.0 [66.9, 191.1] | 4.1 | 4 | 157.7 | 146.1 |
| ALL/ALL | rk_grail_slow_60m_against_state | 0.12 | -61.2 | 129.6 | 0.40 | 0.44 | -190.8 [-283.7, -97.9] | -4.0 | 4 | -4.3 | -241.1 |
| ALL/ALL | eh_ebsw_fast_15m_side | 0.71 | 141.1 | 20.0 | 0.44 | 0.42 | 121.2 [62.0, 180.3] | 4.0 | 4 | 169.4 | 284.9 |
| ALL/ALL | eh_ebsw_fast_15m_ewith | 0.55 | 161.9 | 38.1 | 0.45 | 0.43 | 123.8 [63.3, 184.3] | 4.0 | 4 | 89.9 | 96.0 |
| ALL/ALL | st_amihud_3m_hi | 0.46 | 175.8 | 46.5 | 0.45 | 0.43 | 129.3 [65.0, 193.6] | 3.9 | 4 | 45.7 | 16.9 |
| ALL/ALL | rk_8020_slow_60m_with10 | 0.11 | -64.3 | 127.9 | 0.40 | 0.44 | -192.3 [-288.7, -95.8] | -3.9 | 3 | -308.5 | -201.6 |
| ALL/ALL | eh_ebsw_std_15m_eagainst | 0.27 | 17.6 | 138.2 | 0.42 | 0.44 | -120.6 [-181.3, -59.9] | -3.9 | 3 | -178.7 | -268.1 |
| ALL/ALL | rk_310_std_15m_side | 0.71 | 139.5 | 21.6 | 0.44 | 0.42 | 117.8 [58.5, 177.2] | 3.9 | 4 | 179.8 | 325.9 |
| ALL/ALL | eh_ss20_15m_side | 0.81 | 132.4 | -6.2 | 0.44 | 0.41 | 138.6 [68.3, 208.8] | 3.9 | 4 | 100.0 | 298.0 |
| ALL/ALL | ks_devstop2_5m_side | 0.81 | 130.5 | 2.9 | 0.44 | 0.41 | 127.6 [62.5, 192.8] | 3.8 | 4 | 125.6 | 359.3 |
| ALL/ALL | ch_dmi_1m_eleave | 0.01 | 885.5 | 100.4 | 0.59 | 0.44 | 785.2 [384.2, 1186.2] | 3.8 | 4 | 453.8 | 74.1 |
| ALL/ALL | st_zma200_1m_fresh5 | 0.10 | -22.8 | 120.6 | 0.41 | 0.44 | -143.4 [-216.9, -69.8] | -3.8 | 4 | -132.0 | -154.3 |
| ALL/ALL | ks_peak25_5m_side | 0.82 | 130.0 | -1.0 | 0.44 | 0.42 | 131.1 [63.4, 198.7] | 3.8 | 4 | 140.7 | 256.7 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | ch_fosc_slow_3m_nodiv | 0.71 | 38.8 | 302.4 | 0.49 | 0.60 | -263.6 [-406.1, -121.1] | -3.6 | 4 | -297.5 | -275.8 |
| A7/0 | eh_mama_std_60m_nodiv | 0.85 | 69.1 | 374.1 | 0.50 | 0.64 | -305.0 [-483.4, -126.6] | -3.4 | 4 | -39.3 | 245.5 |
| A7/0 | ks_peak14_3m_fresh5 | 0.21 | -99.2 | 171.7 | 0.43 | 0.55 | -270.9 [-431.2, -110.5] | -3.3 | 4 | -21.5 | -51.5 |
| A7/0 | wl_volstop_dist_fast_5m_fresh5 | 0.16 | -121.9 | 160.4 | 0.41 | 0.54 | -282.4 [-459.3, -105.5] | -3.1 | 4 | -178.9 | -203.7 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | dm_flip_1d_against3 | 0.22 | 764.3 | 58.5 | 0.59 | 0.45 | 705.8 [267.0, 1144.6] | 3.2 | 4 | 296.1 | 318.2 |
| H7/0 | rk_310h_std_agree4of4 | 0.12 | -568.6 | 322.7 | 0.35 | 0.50 | -891.3 [-1446.6, -336.1] | -3.1 | 4 | -383.5 | -1.0 |
| H7/0 | rk_8020_fast_1d_against10 | 0.71 | 386.9 | -212.1 | 0.51 | 0.41 | 599.1 [187.9, 1010.2] | 2.9 | 4 | 127.6 | 298.0 |
| H7/0 | eh_ebsw_std_15m_nodiv | 0.85 | 324.8 | -423.3 | 0.49 | 0.39 | 748.0 [230.2, 1265.9] | 2.8 | 4 | 506.2 | 405.0 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | cn_rsi2_fast_3m_nodiv | 0.80 | -63.1 | 454.5 | 0.43 | 0.66 | -517.6 [-792.6, -242.6] | -3.7 | 4 | -417.9 | -1443.8 |
| H7/3 | cn_rsi2_std_3m_nodiv | 0.80 | -63.1 | 454.5 | 0.43 | 0.66 | -517.6 [-792.6, -242.6] | -3.7 | 4 | -417.9 | -1443.8 |
| H7/3 | wl_volstop_dist_std_3m_nodiv | 0.85 | -42.1 | 513.2 | 0.44 | 0.68 | -555.4 [-858.9, -251.9] | -3.6 | 4 | -240.4 | -673.9 |
| H7/3 | eh_cyber_fast_1m_side | 0.51 | 244.7 | -171.7 | 0.58 | 0.38 | 416.4 [187.1, 645.7] | 3.6 | 4 | 328.1 | 428.3 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | wl_volstop_dist_slow_15m_fresh5 | 0.09 | 473.0 | 50.5 | 0.57 | 0.43 | 422.5 [221.0, 624.0] | 4.1 | 4 | 249.3 | 276.4 |
| K7/0 | eh_cyber_fast_15m_ewith | 0.14 | 381.4 | 41.5 | 0.54 | 0.43 | 339.9 [168.8, 510.9] | 3.9 | 4 | 120.2 | 146.8 |
| K7/0 | rk_8020_slow_5m_state | 0.28 | -59.2 | 145.4 | 0.38 | 0.47 | -204.6 [-312.2, -96.9] | -3.7 | 4 | -257.1 | -255.0 |
| K7/0 | rk_grail_std_60m_against10 | 0.13 | -140.4 | 122.1 | 0.36 | 0.46 | -262.6 [-405.3, -119.8] | -3.6 | 4 | -203.3 | -357.5 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | rk_soup_std_3m_against_state | 0.45 | 159.3 | -63.8 | 0.48 | 0.39 | 223.1 [104.9, 341.3] | 3.7 | 4 | 217.9 | 329.4 |
| K7/1 | rk_soup_std_5m_state | 0.27 | -118.3 | 92.0 | 0.36 | 0.45 | -210.2 [-332.3, -88.1] | -3.4 | 4 | -78.8 | -81.3 |
| K7/1 | dm_line_break_3m_with1 | 0.15 | -195.3 | 75.0 | 0.33 | 0.44 | -270.3 [-435.1, -105.4] | -3.2 | 4 | -480.2 | -647.1 |
| K7/1 | ch_fosc_slow_agree4of4 | 0.18 | 237.7 | -8.9 | 0.50 | 0.41 | 246.6 [93.3, 400.0] | 3.2 | 3 | 345.5 | 867.3 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | wl_volstop_dist_std_5m_fresh5 | 0.12 | 228.2 | -20.4 | 0.52 | 0.41 | 248.6 [96.4, 400.8] | 3.2 | 4 | 185.7 | 369.7 |
| K7/3 | rk_anti_5m_with3 | 0.27 | 141.5 | -38.4 | 0.49 | 0.40 | 179.9 [66.9, 292.9] | 3.1 | 4 | 168.1 | 192.2 |
| K7/3 | st_es_leads_1m_hi_z1 | 0.13 | 216.3 | -21.0 | 0.52 | 0.41 | 237.3 [87.4, 387.2] | 3.1 | 4 | 421.4 | 510.6 |
| K7/3 | rk_310_slow_5m_fresh5 | 0.17 | 183.1 | -26.3 | 0.51 | 0.41 | 209.3 [76.4, 342.3] | 3.1 | 4 | 181.6 | -46.8 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | st_corr_es_3m_hi_z1 | 0.37 | -101.7 | 157.5 | 0.39 | 0.50 | -259.2 [-402.1, -116.3] | -3.6 | 4 | -226.5 | -1293.3 |
| K7/4 | dm_flip_1d_against10 | 0.80 | -1.9 | 310.5 | 0.44 | 0.53 | -312.4 [-496.9, -127.8] | -3.3 | 3 | -466.6 | -335.1 |
| K7/4 | cn_double7_slow_1d_against_state | 0.41 | -75.0 | 158.2 | 0.39 | 0.51 | -233.2 [-377.1, -89.3] | -3.2 | 4 | -418.2 | -714.6 |
| K7/4 | st_zma200_15m_ewith | 0.28 | 252.7 | -11.6 | 0.52 | 0.43 | 264.3 [97.5, 431.0] | 3.1 | 4 | 522.2 | 1202.2 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | wl_volstop_flip_fast_1d_against10 | 0.33 | -149.5 | 68.3 | 0.34 | 0.43 | -217.9 [-327.9, -107.8] | -3.9 | 4 | -251.7 | -300.3 |
| M7/1 | dm_cd_1m_with_ge12 | 0.05 | -282.1 | 12.6 | 0.27 | 0.41 | -294.8 [-469.7, -119.8] | -3.3 | 4 | -231.5 | -396.1 |
| M7/1 | bk_trendbars5_1m_eleave | 0.10 | 279.2 | -35.6 | 0.50 | 0.39 | 314.8 [122.6, 507.0] | 3.2 | 4 | 360.9 | 485.0 |
| M7/1 | dm_cd_1m_with_ge13 | 0.04 | -312.6 | 9.8 | 0.26 | 0.41 | -322.4 [-522.2, -122.6] | -3.2 | 4 | -159.8 | -426.2 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | bk_h1h2_1m_with3 | 0.40 | 143.7 | -28.7 | 0.48 | 0.41 | 172.4 [67.4, 277.5] | 3.2 | 4 | 243.8 | 224.3 |
| M7/3 | st_zma20_5m_nodiv | 0.78 | 83.1 | -109.4 | 0.46 | 0.37 | 192.5 [70.6, 314.3] | 3.1 | 4 | 198.8 | 355.0 |
| M7/3 | rk_grail_std_3m_with10 | 0.16 | -136.7 | 74.3 | 0.35 | 0.45 | -210.9 [-348.2, -73.6] | -3.0 | 4 | -324.6 | 26.8 |
| M7/3 | eh_mamapx_slow_5m_nodiv | 0.81 | 77.2 | -119.5 | 0.45 | 0.36 | 196.7 [67.6, 325.7] | 3.0 | 4 | 197.2 | 308.1 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | eh_ss6_3m_fresh5 | 0.72 | 273.4 | -70.2 | 0.41 | 0.28 | 343.6 [123.7, 563.5] | 3.1 | 4 | 679.3 | 948.7 |
| O7/3 | rk_anti_3m_against_state | 0.35 | -38.3 | 291.3 | 0.29 | 0.42 | -329.6 [-542.4, -116.7] | -3.0 | 3 | -717.1 | -1017.4 |
| O7/3 | rk_310h_slow_agree3of4 | 0.53 | 321.0 | 13.5 | 0.44 | 0.31 | 307.5 [97.8, 517.3] | 2.9 | 4 | 136.7 | 1026.4 |
| O7/3 | rk_anti_3m_state | 0.64 | 279.2 | -8.5 | 0.41 | 0.30 | 287.6 [74.0, 501.3] | 2.6 | 3 | 717.1 | 1017.4 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | rk_soup_fast_3m_with3 | 0.05 | -864.0 | 492.9 | 0.29 | 0.45 | -1356.9 [-2140.2, -573.7] | -3.4 | 4 | -1367.8 | -870.3 |
| P7/0 | eh_roof_slow_60m_fresh5 | 0.12 | 1348.4 | 291.8 | 0.52 | 0.43 | 1056.6 [441.4, 1671.7] | 3.4 | 4 | 1649.2 | 2791.2 |
| P7/0 | rk_310h_fast_5m_fresh5 | 0.40 | 25.0 | 689.5 | 0.41 | 0.46 | -664.5 [-1057.6, -271.5] | -3.3 | 4 | -701.5 | -961.6 |
| P7/0 | eh_mamapx_slow_3m_side | 0.79 | 581.5 | -179.0 | 0.45 | 0.40 | 760.5 [300.8, 1220.1] | 3.2 | 4 | 735.6 | 1624.8 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | rk_8020_fast_5m_against10 | 0.69 | 157.3 | -239.6 | 0.41 | 0.33 | 397.0 [156.2, 637.7] | 3.2 | 4 | 439.1 | 650.2 |
| P7/1 | dm_demand_line_15m_nodiv | 0.91 | -78.4 | 939.2 | 0.35 | 0.61 | -1017.6 [-1654.6, -380.5] | -3.1 | 3 | -274.9 | 373.9 |
| P7/1 | ks_peak14_5m_divwith | 0.08 | 670.9 | -18.0 | 0.50 | 0.37 | 688.9 [256.9, 1120.9] | 3.1 | 4 | 140.9 | 32.0 |
| P7/1 | cn_rsi2_std_60m_nodiv | 0.84 | 105.7 | -336.4 | 0.39 | 0.32 | 442.1 [153.6, 730.7] | 3.0 | 4 | 356.1 | 548.3 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | rk_8020_fast_5m_against10 | 0.69 | -199.2 | 329.4 | 0.36 | 0.46 | -528.5 [-814.6, -242.5] | -3.6 | 4 | -498.8 | -41.7 |
| P7/3 | bk_h1h2_60m_with10 | 0.45 | 223.7 | -247.7 | 0.44 | 0.35 | 471.4 [209.4, 733.5] | 3.5 | 4 | 569.6 | 669.4 |
| P7/3 | cn_rsi2_std_1d_ewith | 0.13 | 591.1 | -124.9 | 0.48 | 0.38 | 716.1 [288.6, 1143.5] | 3.3 | 4 | 784.6 | 1094.4 |
| P7/3 | st_nqlag_es120_60m_divwith | 0.26 | -370.1 | 85.2 | 0.31 | 0.41 | -455.3 [-731.2, -179.4] | -3.2 | 4 | -377.9 | -506.3 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | cn_double7_slow_1d_with3 | 0.11 | 1528.4 | 247.0 | 0.69 | 0.51 | 1281.4 [571.9, 1990.8] | 3.5 | 4 | 1631.6 | 1361.0 |
| U7/0 | cn_double7_1d_with3 | 0.18 | 1288.7 | 185.9 | 0.67 | 0.50 | 1102.8 [489.7, 1716.0] | 3.5 | 4 | 1088.7 | 633.3 |
| U7/0 | eh_roof_slow_15m_sig | 0.88 | 516.0 | -564.9 | 0.55 | 0.34 | 1080.9 [455.6, 1706.2] | 3.4 | 3 | 574.0 | 830.9 |
| U7/0 | eh_roof_slow_15m_rise | 0.88 | 516.0 | -564.9 | 0.55 | 0.34 | 1080.9 [455.6, 1706.2] | 3.4 | 3 | 574.0 | 830.9 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | ch_fosc_std_60m_nodiv | 0.80 | 322.8 | -636.1 | 0.53 | 0.40 | 958.9 [370.1, 1547.7] | 3.2 | 4 | 928.4 | 1828.8 |
| U7/1 | eh_ss6_60m_nodiv | 0.82 | 313.5 | -676.1 | 0.53 | 0.38 | 989.5 [376.6, 1602.4] | 3.2 | 4 | 970.0 | 497.1 |
| U7/1 | bk_failbo_std_3m_state | 0.25 | -444.5 | 331.2 | 0.42 | 0.53 | -775.7 [-1280.8, -270.5] | -3.0 | 3 | -1137.6 | -1638.2 |
| U7/1 | eh_roof_slow_5m_fresh5 | 0.26 | -421.3 | 326.4 | 0.43 | 0.53 | -747.6 [-1243.0, -252.3] | -3.0 | 4 | -999.5 | -1096.6 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_A_named_hs.parquet

### A - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 3992 conditions; 160148 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 1726 conditions with |t|>2 (chance alone: about 199). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | dm_tdst_agree4of4 | 0.22 | 7.9 | 1.0 | 0.54 | 0.47 | 6.9 [5.7, 8.0] | 11.7 | 3 | 7.1 | 9.6 |
| ALL/ALL | cn_rsi_pb_slow_3m_against_state | 0.36 | -1.2 | 4.6 | 0.45 | 0.51 | -5.9 [-6.9, -4.9] | -11.6 | 4 | -5.8 | -6.4 |
| ALL/ALL | cn_double7_slow_3m_against_state | 0.36 | -1.3 | 4.6 | 0.45 | 0.51 | -5.9 [-6.9, -4.9] | -11.6 | 4 | -6.1 | -5.6 |
| ALL/ALL | cn_rsi_pb_std_3m_against_state | 0.36 | -1.2 | 4.6 | 0.45 | 0.51 | -5.8 [-6.8, -4.8] | -11.5 | 4 | -5.7 | -5.9 |
| ALL/ALL | ks_peak25_15m_side | 0.70 | 4.3 | -1.7 | 0.50 | 0.44 | 6.0 [5.0, 7.0] | 11.3 | 4 | 5.9 | 6.4 |
| ALL/ALL | cn_double7_3m_against_state | 0.36 | -1.2 | 4.6 | 0.45 | 0.51 | -5.7 [-6.7, -4.7] | -11.3 | 4 | -5.8 | -6.1 |
| ALL/ALL | cn_double7_3m_state | 0.60 | 4.7 | -0.9 | 0.51 | 0.45 | 5.6 [4.6, 6.6] | 11.2 | 4 | 5.0 | 6.1 |
| ALL/ALL | rk_grail_std_15m_against10 | 0.09 | -6.0 | 3.3 | 0.41 | 0.49 | -9.3 [-11.0, -7.7] | -11.1 | 3 | -17.0 | -22.1 |
| ALL/ALL | eh_mama_slow_15m_side | 0.61 | 4.6 | -0.8 | 0.51 | 0.45 | 5.4 [4.5, 6.4] | 10.9 | 4 | 5.5 | 5.3 |
| ALL/ALL | bk_micro_60m_against_ge3 | 0.16 | -3.5 | 3.6 | 0.43 | 0.50 | -7.2 [-8.5, -5.9] | -10.8 | 3 | -4.5 | -5.3 |
| ALL/ALL | cn_rsi_pb_std_3m_state | 0.46 | 5.3 | 0.1 | 0.51 | 0.46 | 5.2 [4.2, 6.1] | 10.6 | 4 | 4.8 | 7.3 |
| ALL/ALL | eh_mama_slow_agree4of4 | 0.36 | 5.8 | 0.6 | 0.52 | 0.47 | 5.2 [4.2, 6.2] | 10.3 | 4 | 4.2 | 6.7 |
| ALL/ALL | ch_fosc_fast_1d_side | 0.53 | 4.8 | -0.1 | 0.50 | 0.46 | 5.0 [4.0, 5.9] | 10.2 | 3 | 8.0 | 11.0 |
| ALL/ALL | eh_ebsw_slow_15m_ewith | 0.60 | 4.5 | -0.5 | 0.51 | 0.45 | 5.0 [4.1, 6.0] | 10.2 | 4 | 5.3 | 6.1 |
| ALL/ALL | eh_ebsw_fast_60m_eagainst | 0.30 | -1.3 | 4.1 | 0.45 | 0.50 | -5.4 [-6.5, -4.4] | -10.2 | 4 | -6.4 | -7.6 |
| ALL/ALL | rk_310_std_60m_side | 0.58 | 4.6 | -0.4 | 0.51 | 0.46 | 5.0 [4.0, 6.0] | 10.2 | 4 | 5.1 | 7.3 |
| ALL/ALL | eh_ebsw_fast_60m_side | 0.58 | 4.6 | -0.4 | 0.51 | 0.46 | 5.0 [4.0, 6.0] | 10.1 | 4 | 4.7 | 5.4 |
| ALL/ALL | bk_failbo_fast_1d_with1 | 0.04 | -9.6 | 3.0 | 0.38 | 0.49 | -12.6 [-15.1, -10.1] | -10.0 | 4 | -11.6 | -22.5 |
| ALL/ALL | cn_double7_fast_15m_against10 | 0.46 | -0.1 | 4.7 | 0.46 | 0.51 | -4.8 [-5.8, -3.9] | -9.9 | 4 | -4.4 | -5.3 |
| ALL/ALL | cn_double7_5m_against_state | 0.42 | -0.3 | 4.5 | 0.46 | 0.51 | -4.8 [-5.8, -3.9] | -9.8 | 4 | -4.1 | -3.7 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_A_named_hs.parquet

## Sub-block B: session / daily named systems (Dalton / Steidlmayer, Crabel, Fisher ACD, Williams)

### B - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 123 conditions; 2055 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 28 conditions with |t|>2 (chance alone: about 6). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | dl_pd_neutral | 0.11 | 267.3 | 85.2 | 0.48 | 0.43 | 182.1 [81.1, 283.0] | 3.5 | 4 | 239.6 | 345.8 |
| ALL/ALL | cb_stretch_std_hit | 0.75 | 66.9 | -53.4 | 0.44 | 0.40 | 120.3 [48.8, 191.8] | 3.3 | 3 | 289.9 | 340.0 |
| ALL/ALL | cb_stretch_std_beyond | 0.58 | 80.3 | -24.5 | 0.44 | 0.41 | 104.8 [38.2, 171.4] | 3.1 | 3 | 159.5 | 232.6 |
| ALL/ALL | wl_volbo_fast_beyond | 0.46 | 91.3 | -9.4 | 0.45 | 0.41 | 100.7 [32.0, 169.5] | 2.9 | 3 | 343.0 | 416.2 |
| ALL/ALL | dl_sp_ahead_120 | 0.06 | -75.6 | 118.0 | 0.40 | 0.44 | -193.6 [-326.5, -60.7] | -2.9 | 3 | -161.0 | -22.1 |
| ALL/ALL | cb_stretch_fast_beyond | 0.60 | 74.9 | -20.1 | 0.44 | 0.41 | 95.0 [28.2, 161.7] | 2.8 | 4 | 215.6 | 349.0 |
| ALL/ALL | cb_stretch_slow_hit | 0.74 | 62.2 | -38.1 | 0.43 | 0.41 | 100.4 [29.0, 171.8] | 2.8 | 3 | 283.1 | 396.7 |
| ALL/ALL | fa_inor_std | 0.41 | -41.4 | 58.7 | 0.41 | 0.44 | -100.1 [-173.0, -27.2] | -2.7 | 4 | -186.5 | -0.1 |
| ALL/ALL | dl_ib_ext_dn | 0.28 | -48.5 | 77.9 | 0.41 | 0.45 | -126.3 [-218.5, -34.2] | -2.7 | 3 | -77.4 | -912.1 |
| ALL/ALL | dl_pd_neutral_ext | 0.06 | 272.1 | 94.8 | 0.49 | 0.43 | 177.2 [47.1, 307.4] | 2.7 | 4 | 191.4 | 642.0 |
| ALL/ALL | wl_volbo_std_hit | 0.34 | 102.6 | 1.7 | 0.45 | 0.41 | 100.9 [26.4, 175.3] | 2.7 | 4 | 309.1 | 343.3 |
| ALL/ALL | dl_pd_trend_against | 0.04 | -93.5 | 113.2 | 0.39 | 0.44 | -206.7 [-362.1, -51.3] | -2.6 | 3 | -36.5 | -20.3 |
| ALL/ALL | cb_stretch_fast_hit | 0.75 | 60.1 | -34.9 | 0.43 | 0.41 | 95.0 [22.9, 167.1] | 2.6 | 3 | 222.0 | 351.3 |
| ALL/ALL | wl_volbo_fast_hit | 0.61 | 70.7 | -16.3 | 0.44 | 0.41 | 87.0 [20.1, 153.9] | 2.5 | 4 | 217.6 | 299.8 |
| ALL/ALL | dl_sp_ahead_any | 0.20 | 25.8 | 125.6 | 0.42 | 0.44 | -99.8 [-177.1, -22.5] | -2.5 | 3 | -126.3 | -205.0 |
| ALL/ALL | fa_a_std_hit_with | 0.46 | 66.6 | -23.9 | 0.44 | 0.42 | 90.5 [18.0, 163.0] | 2.4 | 3 | 164.5 | 99.6 |
| ALL/ALL | fa_nl60_fast_with | 0.05 | 277.7 | 96.9 | 0.49 | 0.44 | 180.8 [35.3, 326.3] | 2.4 | 3 | 120.1 | nan |
| ALL/ALL | fa_a_fast_hit_with | 0.68 | 52.8 | -33.3 | 0.44 | 0.42 | 86.1 [13.4, 158.8] | 2.3 | 3 | 208.8 | 98.9 |
| ALL/ALL | dl_excess_high | 0.77 | 125.5 | 39.9 | 0.44 | 0.43 | 85.6 [12.6, 158.5] | 2.3 | 4 | 19.9 | -0.0 |
| ALL/ALL | dl_sp_ahead_60 | 0.03 | -110.5 | 112.0 | 0.40 | 0.44 | -222.5 [-419.2, -25.8] | -2.2 | 3 | -466.8 | -530.0 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | cb_nr4 | 0.23 | 235.0 | 78.4 | 0.58 | 0.50 | 156.6 [2.3, 310.9] | 2.0 | 3 | 226.5 | -168.8 |
| A7/0 | dl_pd_neutral | 0.10 | 283.6 | 96.5 | 0.60 | 0.51 | 187.0 [-31.1, 405.2] | 1.7 | 3 | 253.1 | 539.3 |
| A7/0 | dl_pd_normal | 0.13 | -25.7 | 136.0 | 0.46 | 0.53 | -161.7 [-357.6, 34.2] | -1.6 | 3 | -194.1 | -244.7 |
| A7/0 | dl_against_va | 0.08 | 267.2 | 101.5 | 0.60 | 0.52 | 165.7 [-74.9, 406.3] | 1.4 | 4 | 28.9 | -592.3 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | wl_tdom_last3 | 0.14 | 595.6 | 156.1 | 0.55 | 0.47 | 439.4 [-113.1, 992.0] | 1.6 | 4 | 307.9 | -595.6 |
| H7/0 | fa_nl15_fast_with | 0.21 | 3.9 | 271.1 | 0.46 | 0.49 | -267.2 [-711.8, 177.4] | -1.2 | 3 | -681.5 | 0.4 |
| H7/0 | dl_pd_normal | 0.14 | 55.0 | 242.6 | 0.40 | 0.49 | -187.6 [-675.6, 300.4] | -0.8 | 3 | -275.9 | -474.9 |
| H7/0 | wl_tdom_seasonal_with | 0.57 | 148.8 | 245.6 | 0.48 | 0.47 | -96.9 [-482.1, 288.4] | -0.5 | 3 | -561.9 | -71.5 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | wl_volbo_fast_beyond | 0.42 | 234.0 | -90.0 | 0.57 | 0.42 | 324.0 [86.9, 561.2] | 2.7 | 3 | 524.4 | 572.3 |
| H7/3 | dl_open_outside_va | 0.63 | 159.7 | -149.0 | 0.53 | 0.41 | 308.7 [67.6, 549.8] | 2.5 | 3 | 581.7 | -1251.3 |
| H7/3 | wl_volbo_fast_hit | 0.55 | 145.7 | -76.6 | 0.53 | 0.42 | 222.3 [-10.9, 455.5] | 1.9 | 4 | 405.5 | 434.7 |
| H7/3 | fa_a_fast_fresh30 | 0.47 | -58.5 | 136.0 | 0.44 | 0.52 | -194.5 [-429.1, 40.1] | -1.6 | 3 | -566.3 | -515.2 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | dl_poc_side_with | 0.61 | 132.0 | 21.2 | 0.46 | 0.42 | 110.9 [9.9, 211.8] | 2.2 | 4 | 150.4 | 209.1 |
| K7/0 | dl_pd_double | 0.11 | 212.0 | 73.9 | 0.50 | 0.44 | 138.1 [-24.7, 301.0] | 1.7 | 3 | 192.9 | 166.8 |
| K7/0 | fa_above_pr_with | 0.56 | 122.8 | 45.5 | 0.46 | 0.43 | 77.3 [-22.8, 177.4] | 1.5 | 4 | 109.1 | 339.6 |
| K7/0 | cb_nr7 | 0.12 | -10.5 | 102.9 | 0.40 | 0.45 | -113.3 [-261.9, 35.2] | -1.5 | 4 | -157.2 | -338.6 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | wl_tdom_seasonal_with | 0.50 | 108.9 | -27.4 | 0.45 | 0.41 | 136.3 [18.6, 254.1] | 2.3 | 4 | 93.4 | -10.9 |
| K7/1 | dl_pd_normvar_with | 0.35 | -15.8 | 62.7 | 0.40 | 0.44 | -78.5 [-201.8, 44.9] | -1.2 | 3 | -215.0 | -350.0 |
| K7/1 | dl_inside_va | 0.37 | -11.7 | 63.5 | 0.40 | 0.44 | -75.2 [-195.5, 45.1] | -1.2 | 3 | -19.2 | -8.3 |
| K7/1 | cb_nr7 | 0.14 | 120.2 | 22.1 | 0.45 | 0.42 | 98.1 [-77.4, 273.6] | 1.1 | 3 | 198.1 | 282.3 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | cb_prior_wide | 0.12 | -205.8 | 39.0 | 0.32 | 0.44 | -244.8 [-392.6, -97.0] | -3.2 | 4 | -782.3 | -817.5 |
| K7/3 | dl_excess_support_with | 0.68 | -30.6 | 96.2 | 0.41 | 0.47 | -126.7 [-234.4, -19.1] | -2.3 | 3 | -214.2 | -2.4 |
| K7/3 | dl_pd_neutral | 0.12 | 156.6 | -10.8 | 0.50 | 0.42 | 167.4 [12.0, 322.7] | 2.1 | 4 | 260.0 | -218.9 |
| K7/3 | cb_nr4 | 0.26 | 95.2 | -20.3 | 0.47 | 0.41 | 115.5 [0.8, 230.2] | 2.0 | 4 | 113.5 | 54.1 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | cb_stretch_slow_hit | 0.70 | 125.8 | -69.7 | 0.48 | 0.41 | 195.5 [48.8, 342.2] | 2.6 | 4 | 469.3 | 783.2 |
| K7/4 | cb_stretch_std_hit | 0.70 | 120.4 | -59.9 | 0.48 | 0.42 | 180.3 [32.8, 327.9] | 2.4 | 4 | 443.2 | 560.5 |
| K7/4 | dl_excess_low | 0.82 | 101.3 | -112.8 | 0.47 | 0.41 | 214.1 [38.5, 389.7] | 2.4 | 4 | 415.5 | 425.1 |
| K7/4 | cb_stretch_fast_hit | 0.70 | 117.3 | -53.5 | 0.48 | 0.42 | 170.8 [22.0, 319.6] | 2.2 | 4 | 313.0 | 616.8 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | dl_pd_neutral | 0.11 | 261.5 | -34.5 | 0.50 | 0.39 | 296.0 [119.5, 472.6] | 3.3 | 4 | 495.1 | 651.5 |
| M7/1 | fa_nl30_slow_with | 0.13 | 124.3 | -21.6 | 0.45 | 0.40 | 145.9 [-8.8, 300.7] | 1.8 | 3 | 19.2 | -216.1 |
| M7/1 | dl_pd_neutral_ext | 0.06 | 199.5 | -16.1 | 0.49 | 0.40 | 215.6 [-13.3, 444.5] | 1.8 | 4 | 681.5 | 1190.9 |
| M7/1 | fa_nl60_slow_with | 0.10 | 107.4 | -15.5 | 0.45 | 0.40 | 122.8 [-53.0, 298.6] | 1.4 | 3 | 205.1 | 880.7 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | dl_pd_normal | 0.11 | -179.5 | 67.6 | 0.34 | 0.45 | -247.1 [-406.6, -87.5] | -3.0 | 4 | -130.4 | -93.7 |
| M7/3 | dl_pd_neutral | 0.12 | 248.3 | 11.0 | 0.55 | 0.42 | 237.3 [76.7, 398.0] | 2.9 | 4 | 409.0 | 234.2 |
| M7/3 | cb_prior_wide | 0.12 | -107.6 | 60.7 | 0.36 | 0.45 | -168.3 [-320.9, -15.8] | -2.2 | 4 | -220.8 | -25.4 |
| M7/3 | fa_a_std_now_with | 0.37 | 105.3 | -8.2 | 0.47 | 0.41 | 113.6 [4.1, 223.1] | 2.0 | 4 | 157.3 | 100.0 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | cb_stretch_fast_beyond | 0.50 | 269.4 | 89.4 | 0.41 | 0.34 | 180.0 [-33.3, 393.3] | 1.7 | 4 | 141.1 | 1051.2 |
| O7/3 | wl_tdom_4_9 | 0.31 | 45.9 | 233.9 | 0.31 | 0.40 | -187.9 [-413.9, 38.0] | -1.6 | 3 | -132.7 | -153.4 |
| O7/3 | wl_smash_with | 0.30 | 47.5 | 230.3 | 0.33 | 0.39 | -182.8 [-411.0, 45.4] | -1.6 | 3 | -91.1 | 307.4 |
| O7/3 | dl_excess_high | 0.73 | 213.1 | 73.5 | 0.39 | 0.34 | 139.6 [-93.3, 372.5] | 1.2 | 3 | 1049.3 | 803.9 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | dl_sp_ahead_120 | 0.07 | -518.3 | 494.6 | 0.34 | 0.45 | -1012.9 [-1766.7, -259.2] | -2.6 | 3 | -1189.6 | -942.0 |
| P7/0 | dl_sp_ahead_any | 0.20 | -38.0 | 542.2 | 0.39 | 0.45 | -580.2 [-1061.7, -98.8] | -2.4 | 4 | -756.8 | -706.1 |
| P7/0 | dl_pd_trend_against | 0.03 | -494.3 | 451.8 | 0.34 | 0.44 | -946.1 [-1994.1, 101.9] | -1.8 | 4 | -698.4 | 1591.8 |
| P7/0 | fa_nl30_slow_with | 0.13 | 853.4 | 357.0 | 0.48 | 0.43 | 496.4 [-80.1, 1073.0] | 1.7 | 4 | 258.7 | 381.0 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | fa_inside_pr | 0.13 | 258.6 | 0.3 | 0.41 | 0.38 | 258.3 [-79.4, 596.0] | 1.5 | 4 | 474.3 | 313.8 |
| P7/1 | wl_tdom_seasonal_with | 0.50 | -29.4 | 130.6 | 0.37 | 0.40 | -160.1 [-390.4, 70.2] | -1.4 | 3 | -254.8 | -496.3 |
| P7/1 | dl_pd_neutral_ext | 0.06 | 364.1 | 13.9 | 0.42 | 0.38 | 350.2 [-174.1, 874.5] | 1.3 | 4 | 484.0 | 211.7 |
| P7/1 | fa_nl30_slow_with | 0.13 | -137.6 | 59.2 | 0.35 | 0.39 | -196.9 [-516.2, 122.4] | -1.2 | 3 | -162.7 | -93.8 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | cb_stretch_std_hit | 0.82 | 34.8 | -323.9 | 0.40 | 0.34 | 358.7 [63.6, 653.9] | 2.4 | 3 | 918.4 | 726.0 |
| P7/3 | cb_stretch_std_beyond | 0.64 | 80.4 | -226.7 | 0.40 | 0.37 | 307.1 [54.4, 559.8] | 2.4 | 3 | 690.0 | 443.8 |
| P7/3 | cb_stretch_slow_hit | 0.82 | 34.9 | -316.6 | 0.40 | 0.35 | 351.5 [57.5, 645.5] | 2.3 | 3 | 911.1 | 708.8 |
| P7/3 | dl_inside_va | 0.28 | -262.2 | 56.6 | 0.34 | 0.41 | -318.8 [-587.5, -50.1] | -2.3 | 3 | -709.1 | -654.5 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | dl_pd_normal | 0.15 | -360.7 | 512.5 | 0.42 | 0.55 | -873.3 [-1584.9, -161.6] | -2.4 | 3 | -525.6 | -1553.8 |
| U7/0 | dl_excess_low | 0.82 | 279.7 | 873.1 | 0.51 | 0.61 | -593.4 [-1260.3, 73.4] | -1.7 | 4 | -782.3 | -1887.0 |
| U7/0 | dl_pd_normvar_with | 0.24 | 777.6 | 259.0 | 0.60 | 0.50 | 518.6 [-69.0, 1106.2] | 1.7 | 3 | 220.6 | 1447.4 |
| U7/0 | cb_prior_wide | 0.13 | -40.9 | 448.8 | 0.48 | 0.53 | -489.7 [-1267.8, 288.4] | -1.2 | 3 | -1063.8 | 763.7 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | dl_above_va_with | 0.19 | -440.5 | 270.7 | 0.40 | 0.53 | -711.2 [-1337.8, -84.5] | -2.2 | 3 | -753.9 | -1677.0 |
| U7/1 | dl_pd_normal | 0.11 | 804.8 | 48.3 | 0.63 | 0.49 | 756.5 [6.1, 1507.0] | 2.0 | 3 | 168.6 | 803.3 |
| U7/1 | dl_poc_side_with | 0.37 | -171.7 | 311.5 | 0.46 | 0.53 | -483.3 [-982.2, 15.7] | -1.9 | 4 | -871.5 | -936.4 |
| U7/1 | dl_inside_va | 0.42 | 364.1 | -31.7 | 0.56 | 0.46 | 395.8 [-85.4, 877.0] | 1.6 | 3 | 241.5 | 1809.3 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B_sess_named.parquet

### B - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 124 conditions; 3516 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 61 conditions with |t|>2 (chance alone: about 6). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | dl_pd_trend_with | 0.03 | -10.1 | 2.9 | 0.35 | 0.49 | -13.0 [-15.7, -10.3] | -9.4 | 3 | -13.7 | -15.2 |
| ALL/ALL | wl_volbo_fast_hit | 0.63 | 4.4 | -3.9 | 0.50 | 0.43 | 8.3 [6.5, 10.2] | 8.8 | 4 | 8.6 | 9.2 |
| ALL/ALL | wl_volbo_fast_beyond | 0.49 | 5.2 | -2.5 | 0.51 | 0.44 | 7.7 [5.9, 9.5] | 8.4 | 4 | 11.4 | 13.3 |
| ALL/ALL | cb_orb5_narrow | 0.30 | 6.3 | -0.9 | 0.51 | 0.45 | 7.2 [5.2, 9.1] | 7.2 | 4 | 2.8 | -0.2 |
| ALL/ALL | dl_r80_active_with | 0.03 | -15.1 | 1.9 | 0.35 | 0.48 | -16.9 [-21.9, -12.0] | -6.7 | 3 | -22.7 | -38.2 |
| ALL/ALL | dl_poc_side_with | 0.69 | 3.5 | 0.2 | 0.50 | 0.46 | 3.3 [2.3, 4.3] | 6.3 | 3 | 4.3 | 4.4 |
| ALL/ALL | cb_stretch_std_hit | 0.77 | 2.9 | -4.0 | 0.48 | 0.43 | 6.8 [4.7, 9.0] | 6.3 | 4 | 4.8 | 6.0 |
| ALL/ALL | cb_stretch_slow_hit | 0.78 | 2.7 | -3.6 | 0.48 | 0.43 | 6.4 [4.2, 8.5] | 5.8 | 3 | 5.6 | 8.9 |
| ALL/ALL | wl_volbo_std_hit | 0.39 | 4.6 | -0.8 | 0.50 | 0.45 | 5.3 [3.5, 7.2] | 5.7 | 4 | 8.9 | 13.1 |
| ALL/ALL | fa_above_pr_with | 0.63 | 3.5 | 0.7 | 0.50 | 0.46 | 2.8 [1.8, 3.8] | 5.6 | 4 | 2.8 | 6.6 |
| ALL/ALL | dl_pd_neutral_ext | 0.05 | 7.8 | 2.2 | 0.52 | 0.48 | 5.6 [3.4, 7.7] | 5.1 | 3 | 12.6 | 28.3 |
| ALL/ALL | dl_sp_behind_120 | 0.02 | 11.2 | 2.3 | 0.56 | 0.48 | 8.9 [5.4, 12.3] | 5.1 | 4 | 26.7 | 33.2 |
| ALL/ALL | cb_stretch_std_beyond | 0.62 | 3.0 | -1.4 | 0.49 | 0.45 | 4.4 [2.6, 6.3] | 4.7 | 4 | 4.2 | 8.4 |
| ALL/ALL | cb_stretch_fast_beyond | 0.63 | 2.9 | -1.3 | 0.48 | 0.45 | 4.1 [2.3, 6.0] | 4.4 | 3 | 3.5 | 9.5 |
| ALL/ALL | dl_above_va_with | 0.47 | 3.6 | 1.5 | 0.50 | 0.47 | 2.1 [1.1, 3.0] | 4.3 | 3 | 2.1 | 0.8 |
| ALL/ALL | dl_r80_active_against | 0.03 | -9.7 | 1.6 | 0.41 | 0.47 | -11.4 [-16.7, -6.1] | -4.2 | 3 | -2.4 | -14.4 |
| ALL/ALL | cb_nr4 | 0.24 | 4.2 | 2.0 | 0.50 | 0.48 | 2.2 [1.1, 3.3] | 3.9 | 3 | 2.7 | 0.5 |
| ALL/ALL | dl_dev_neutral | 0.04 | 11.5 | 1.0 | 0.59 | 0.48 | 10.5 [5.2, 15.7] | 3.9 | 4 | 0.8 | 7.8 |
| ALL/ALL | dl_dev_trend_with | 0.08 | -5.8 | 2.0 | 0.42 | 0.49 | -7.8 [-11.8, -3.9] | -3.9 | 3 | -3.0 | -9.8 |
| ALL/ALL | cb_stretch_slow_beyond | 0.62 | 2.7 | -0.9 | 0.48 | 0.45 | 3.6 [1.8, 5.5] | 3.9 | 3 | 4.1 | 6.8 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B_sess_named.parquet

## Sub-block B2: the same opening-range systems re-anchored on the D7 session (asia, london, pre, nyam, nypm, close)

### B2 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 48 conditions; 1218 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 2 conditions with |t|>2 (chance alone: about 2). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | ss_gap_with | 0.37 | 161.2 | 73.7 | 0.45 | 0.43 | 87.6 [20.4, 154.8] | 2.6 | 4 | 30.5 | 169.1 |
| ALL/ALL | ss_orb15_against_beyond | 0.09 | -11.5 | 117.1 | 0.42 | 0.44 | -128.7 [-242.8, -14.6] | -2.2 | 3 | -258.0 | -307.8 |
| ALL/ALL | ss_a_std_now_against | 0.06 | -7.7 | 112.8 | 0.41 | 0.44 | -120.5 [-244.3, 3.3] | -1.9 | 3 | -276.5 | -497.2 |
| ALL/ALL | ss_a_slow_fresh30 | 0.14 | 165.2 | 82.0 | 0.46 | 0.43 | 83.2 [-9.3, 175.7] | 1.8 | 3 | 181.1 | 29.6 |
| ALL/ALL | ss_volbo_fast_hit | 0.59 | 129.0 | 72.5 | 0.44 | 0.43 | 56.5 [-7.9, 121.0] | 1.7 | 4 | 200.0 | 136.3 |
| ALL/ALL | ss_orb30_against_beyond | 0.08 | -1.4 | 102.1 | 0.41 | 0.44 | -103.6 [-225.1, 18.0] | -1.7 | 3 | -222.4 | -371.7 |
| ALL/ALL | ss_orb5_against_beyond | 0.11 | 27.6 | 115.6 | 0.42 | 0.44 | -87.9 [-193.8, 17.9] | -1.6 | 4 | -199.2 | -209.1 |
| ALL/ALL | ss_range_used_gt100 | 0.25 | 60.8 | 121.6 | 0.43 | 0.44 | -60.8 [-134.4, 12.9] | -1.6 | 3 | -127.9 | -161.1 |
| ALL/ALL | ss_a_fast_now_against | 0.08 | 19.9 | 113.9 | 0.42 | 0.44 | -93.9 [-207.9, 20.0] | -1.6 | 3 | -269.1 | -348.8 |
| ALL/ALL | ss_inside | 0.06 | 16.3 | 111.5 | 0.41 | 0.44 | -95.2 [-220.0, 29.7] | -1.5 | 3 | -150.5 | -49.0 |
| ALL/ALL | ss_volbo_std_hit | 0.39 | 135.7 | 87.1 | 0.44 | 0.43 | 48.6 [-16.8, 113.9] | 1.5 | 3 | 216.4 | 161.1 |
| ALL/ALL | ss_gap_against | 0.34 | 74.5 | 122.6 | 0.43 | 0.44 | -48.2 [-114.6, 18.2] | -1.4 | 3 | -102.0 | -186.2 |
| ALL/ALL | ss_orb30_beyond | 0.60 | 113.7 | 63.6 | 0.44 | 0.43 | 50.1 [-19.8, 120.0] | 1.4 | 4 | 117.3 | 139.8 |
| ALL/ALL | ss_orb30_fresh15 | 0.11 | 41.2 | 100.0 | 0.45 | 0.43 | -58.8 [-145.0, 27.4] | -1.3 | 3 | -9.5 | -201.7 |
| ALL/ALL | ss_a_slow_hit_with | 0.50 | 115.7 | 71.8 | 0.44 | 0.43 | 43.9 [-23.9, 111.6] | 1.3 | 3 | 131.0 | 140.8 |
| ALL/ALL | ss_volbo_fast_beyond | 0.46 | 127.6 | 87.5 | 0.44 | 0.43 | 40.2 [-23.3, 103.6] | 1.2 | 3 | 221.2 | 181.1 |
| ALL/ALL | ss_inor_std | 0.25 | 138.6 | 94.0 | 0.45 | 0.44 | 44.6 [-38.0, 127.2] | 1.1 | 3 | 29.7 | 105.5 |
| ALL/ALL | ss_inor_fast | 0.18 | 137.3 | 99.1 | 0.44 | 0.44 | 38.2 [-51.2, 127.5] | 0.8 | 3 | 129.4 | 108.6 |
| ALL/ALL | ss_a_slow_now_against | 0.05 | 42.9 | 96.2 | 0.41 | 0.44 | -53.2 [-200.0, 93.5] | -0.7 | 3 | -291.4 | -685.9 |
| ALL/ALL | ss_inor_slow | 0.32 | 80.3 | 99.9 | 0.43 | 0.44 | -19.6 [-94.1, 55.0] | -0.5 | 3 | -40.3 | -17.5 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | ss_volbo_slow_beyond | 0.27 | 227.8 | 71.4 | 0.57 | 0.50 | 156.3 [8.1, 304.6] | 2.1 | 3 | 389.4 | 586.4 |
| A7/0 | ss_volbo_slow_hit | 0.29 | 214.3 | 72.2 | 0.57 | 0.50 | 142.2 [-2.7, 287.0] | 1.9 | 3 | 396.3 | 564.5 |
| A7/0 | ss_range_used_lt50 | 0.26 | 212.1 | 79.0 | 0.57 | 0.50 | 133.2 [-16.8, 283.1] | 1.7 | 4 | 30.0 | -38.1 |
| A7/0 | ss_inor_fast | 0.13 | 50.0 | 122.9 | 0.49 | 0.53 | -72.9 [-272.0, 126.1] | -0.7 | 3 | -85.0 | 131.6 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | ss_orb15_failed | 0.10 | -44.7 | 252.9 | 0.44 | 0.49 | -297.5 [-852.9, 257.8] | -1.1 | 3 | -82.7 | -1105.1 |
| H7/0 | ss_range_used_gt100 | 0.19 | -15.4 | 255.0 | 0.43 | 0.49 | -270.4 [-803.1, 262.3] | -1.0 | 3 | -672.2 | -42.5 |
| H7/0 | ss_a_slow_now_with | 0.37 | 367.5 | 176.7 | 0.52 | 0.47 | 190.8 [-240.4, 622.0] | 0.9 | 3 | 239.8 | 362.5 |
| H7/0 | ss_stretch_beyond | 0.53 | 265.6 | 135.7 | 0.49 | 0.47 | 130.0 [-239.4, 499.3] | 0.7 | 3 | 267.5 | 306.4 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | ss_c_fast_with | 0.43 | -99.1 | 149.7 | 0.41 | 0.53 | -248.8 [-482.4, -15.2] | -2.1 | 4 | -609.2 | -105.2 |
| H7/3 | ss_volbo_fast_beyond | 0.58 | 136.1 | -85.6 | 0.52 | 0.43 | 221.8 [-12.3, 455.9] | 1.9 | 4 | 190.0 | 141.7 |
| H7/3 | ss_volbo_fast_hit | 0.70 | 110.2 | -116.6 | 0.50 | 0.42 | 226.8 [-25.4, 478.9] | 1.8 | 4 | 518.4 | 791.0 |
| H7/3 | ss_volbo_std_hit | 0.44 | 149.6 | -40.7 | 0.53 | 0.44 | 190.3 [-45.3, 425.9] | 1.6 | 3 | 668.8 | 977.4 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | ss_orb5_against_beyond | 0.16 | -79.8 | 125.1 | 0.38 | 0.46 | -204.9 [-339.5, -70.4] | -3.0 | 3 | -232.2 | -374.4 |
| K7/0 | ss_orb30_against_beyond | 0.15 | -62.9 | 143.2 | 0.39 | 0.46 | -206.1 [-354.6, -57.6] | -2.7 | 3 | -284.1 | -477.2 |
| K7/0 | ss_orb15_against_beyond | 0.15 | -41.6 | 122.4 | 0.40 | 0.46 | -164.0 [-307.6, -20.4] | -2.2 | 3 | -261.6 | -431.6 |
| K7/0 | ss_a_slow_now_against | 0.10 | -63.1 | 130.4 | 0.39 | 0.46 | -193.5 [-373.0, -14.0] | -2.1 | 3 | -252.3 | -515.3 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | ss_a_slow_fresh30 | 0.11 | 146.6 | 11.2 | 0.48 | 0.42 | 135.4 [-74.4, 345.2] | 1.3 | 4 | 269.4 | 366.5 |
| K7/1 | ss_range_used_lt50 | 0.29 | 89.4 | 8.1 | 0.45 | 0.42 | 81.2 [-48.7, 211.2] | 1.2 | 3 | 33.2 | -73.5 |
| K7/1 | ss_nr4 | 0.24 | -23.2 | 49.2 | 0.40 | 0.43 | -72.4 [-211.4, 66.7] | -1.0 | 3 | -133.5 | -89.2 |
| K7/1 | ss_volbo_slow_hit | 0.19 | -32.2 | 46.5 | 0.40 | 0.43 | -78.7 [-230.7, 73.2] | -1.0 | 3 | -24.7 | 218.4 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | ss_volbo_fast_beyond | 0.51 | 60.3 | -41.7 | 0.45 | 0.40 | 102.0 [1.9, 202.0] | 2.0 | 4 | 257.4 | 360.4 |
| K7/3 | ss_a_std_fresh30 | 0.22 | 101.1 | -14.9 | 0.46 | 0.42 | 115.9 [-6.1, 238.0] | 1.9 | 4 | 59.9 | -121.3 |
| K7/3 | ss_c_std_with | 0.09 | 142.2 | -2.9 | 0.49 | 0.42 | 145.1 [-34.4, 324.5] | 1.6 | 3 | 161.1 | -108.0 |
| K7/3 | ss_volbo_fast_hit | 0.62 | 40.5 | -39.2 | 0.44 | 0.40 | 79.7 [-22.8, 182.3] | 1.5 | 3 | 196.1 | 249.9 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | ss_volbo_std_beyond | 0.30 | 182.5 | -26.2 | 0.49 | 0.43 | 208.8 [42.5, 375.0] | 2.5 | 3 | 139.4 | 252.0 |
| K7/4 | ss_volbo_std_hit | 0.39 | 154.5 | -36.8 | 0.50 | 0.42 | 191.3 [38.8, 343.7] | 2.5 | 3 | 51.2 | 119.6 |
| K7/4 | ss_volbo_fast_beyond | 0.49 | 108.2 | -32.2 | 0.47 | 0.43 | 140.4 [-5.5, 286.3] | 1.9 | 3 | 315.8 | 662.6 |
| K7/4 | ss_gap_with | 0.37 | 114.5 | -8.5 | 0.47 | 0.44 | 123.0 [-30.5, 276.5] | 1.6 | 4 | 163.6 | 538.8 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | ss_range_used_gt100 | 0.22 | -152.5 | 29.8 | 0.36 | 0.41 | -182.3 [-327.6, -37.1] | -2.5 | 4 | -160.7 | -170.1 |
| M7/1 | ss_volbo_std_hit | 0.34 | -109.1 | 40.6 | 0.38 | 0.41 | -149.7 [-275.2, -24.2] | -2.3 | 4 | -37.0 | -107.6 |
| M7/1 | ss_volbo_slow_beyond | 0.13 | -197.4 | 18.1 | 0.35 | 0.41 | -215.5 [-401.4, -29.7] | -2.3 | 4 | -216.7 | 15.8 |
| M7/1 | ss_stretch_beyond | 0.53 | -72.0 | 56.7 | 0.38 | 0.42 | -128.6 [-240.9, -16.4] | -2.2 | 4 | -121.0 | -220.8 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | ss_a_slow_now_with | 0.34 | 110.4 | -8.5 | 0.47 | 0.41 | 118.9 [8.5, 229.4] | 2.1 | 4 | 149.7 | 113.5 |
| M7/3 | ss_oops_with | 0.15 | -76.2 | 60.9 | 0.37 | 0.45 | -137.1 [-277.8, 3.5] | -1.9 | 3 | -226.2 | -75.9 |
| M7/3 | ss_a_slow_hit_with | 0.47 | 86.2 | -15.0 | 0.46 | 0.41 | 101.2 [-3.3, 205.7] | 1.9 | 4 | 179.1 | 49.6 |
| M7/3 | ss_volbo_fast_hit | 0.78 | 64.9 | -48.7 | 0.45 | 0.39 | 113.6 [-9.1, 236.3] | 1.8 | 3 | 317.7 | 510.7 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | ss_volbo_std_hit | 0.32 | 174.3 | 176.9 | 0.37 | 0.37 | -2.6 [-231.0, 225.7] | -0.0 | 3 | -431.3 | -209.0 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | ss_gap_against | 0.33 | 129.7 | 572.6 | 0.40 | 0.46 | -443.0 [-851.4, -34.5] | -2.1 | 3 | -709.1 | -1082.1 |
| P7/0 | ss_volbo_std_hit | 0.36 | 643.2 | 301.9 | 0.43 | 0.44 | 341.3 [-75.0, 757.6] | 1.6 | 4 | 439.5 | 307.8 |
| P7/0 | ss_volbo_fast_hit | 0.54 | 566.5 | 258.9 | 0.43 | 0.45 | 307.6 [-85.0, 700.3] | 1.5 | 4 | 206.8 | -144.3 |
| P7/0 | ss_range_used_gt150 | 0.12 | 19.6 | 478.1 | 0.39 | 0.45 | -458.5 [-1051.6, 134.6] | -1.5 | 3 | -993.5 | 53.7 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | ss_volbo_slow_hit | 0.22 | -248.6 | 118.4 | 0.32 | 0.40 | -367.1 [-655.9, -78.2] | -2.5 | 4 | -523.5 | -521.4 |
| P7/1 | ss_range_used_gt100 | 0.27 | -193.7 | 122.9 | 0.33 | 0.40 | -316.6 [-577.8, -55.3] | -2.4 | 3 | -694.9 | -991.1 |
| P7/1 | ss_volbo_slow_beyond | 0.14 | -243.4 | 83.7 | 0.32 | 0.39 | -327.1 [-682.3, 28.2] | -1.8 | 3 | -332.8 | -263.7 |
| P7/1 | ss_nr4 | 0.24 | -88.2 | 76.8 | 0.36 | 0.39 | -165.0 [-428.7, 98.7] | -1.2 | 4 | -28.6 | 414.1 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | ss_a_slow_fresh30 | 0.17 | 301.4 | -119.7 | 0.44 | 0.37 | 421.1 [53.5, 788.7] | 2.2 | 4 | 36.2 | -670.0 |
| P7/3 | ss_gap_with | 0.28 | 210.8 | -130.0 | 0.43 | 0.37 | 340.8 [33.9, 647.7] | 2.2 | 3 | 370.5 | 822.7 |
| P7/3 | ss_stretch_hit | 0.89 | 6.1 | -356.1 | 0.39 | 0.36 | 362.2 [-2.2, 726.6] | 1.9 | 3 | 797.6 | 500.8 |
| P7/3 | ss_a_fast_hit_with | 0.88 | 8.8 | -338.7 | 0.39 | 0.37 | 347.5 [-2.7, 697.7] | 1.9 | 4 | 752.3 | 545.9 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | ss_orb30_against_beyond | 0.10 | -283.6 | 447.9 | 0.48 | 0.53 | -731.5 [-1612.1, 149.1] | -1.6 | 3 | -905.1 | -80.7 |
| U7/0 | ss_nr4 | 0.24 | 684.2 | 289.8 | 0.57 | 0.51 | 394.4 [-200.0, 988.9] | 1.3 | 3 | 29.2 | 24.2 |
| U7/0 | ss_orb15_against_beyond | 0.12 | -111.7 | 425.7 | 0.50 | 0.53 | -537.3 [-1377.2, 302.5] | -1.3 | 3 | -949.5 | -155.5 |
| U7/0 | ss_orb5_against_beyond | 0.13 | -37.1 | 449.0 | 0.50 | 0.53 | -486.1 [-1254.9, 282.6] | -1.2 | 3 | -505.2 | 533.6 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | ss_a_fast_fresh30 | 0.35 | -279.2 | 382.2 | 0.46 | 0.53 | -661.4 [-1171.0, -151.9] | -2.5 | 4 | -340.4 | 505.5 |
| U7/1 | ss_orb15_fresh15 | 0.20 | -325.5 | 295.9 | 0.48 | 0.52 | -621.5 [-1221.0, -22.0] | -2.0 | 3 | -68.3 | 1251.8 |
| U7/1 | ss_nr4 | 0.25 | 351.8 | 81.7 | 0.57 | 0.49 | 270.1 [-280.2, 820.4] | 1.0 | 3 | 1245.3 | 911.7 |
| U7/1 | ss_c_std_with | 0.36 | 53.3 | 235.0 | 0.49 | 0.52 | -181.6 [-715.1, 351.8] | -0.7 | 3 | -449.5 | -856.9 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B2_sessanch_named.parquet

### B2 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 48 conditions; 1929 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 32 conditions with |t|>2 (chance alone: about 2). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | ss_volbo_fast_beyond | 0.48 | 4.2 | 1.0 | 0.50 | 0.47 | 3.2 [2.2, 4.1] | 6.4 | 3 | 5.1 | 4.8 |
| ALL/ALL | ss_volbo_std_hit | 0.40 | 4.4 | 1.3 | 0.50 | 0.48 | 3.0 [2.0, 4.0] | 6.0 | 4 | 4.2 | 5.1 |
| ALL/ALL | ss_volbo_fast_hit | 0.61 | 3.7 | 0.7 | 0.50 | 0.47 | 3.0 [2.0, 4.0] | 5.9 | 3 | 4.9 | 3.2 |
| ALL/ALL | ss_oops_with | 0.07 | -2.5 | 2.9 | 0.44 | 0.49 | -5.4 [-7.3, -3.6] | -5.7 | 3 | -11.1 | -8.4 |
| ALL/ALL | ss_volbo_std_beyond | 0.31 | 4.5 | 1.7 | 0.50 | 0.48 | 2.8 [1.8, 3.9] | 5.3 | 4 | 4.8 | 6.3 |
| ALL/ALL | ss_a_slow_now_against | 0.03 | -4.4 | 2.7 | 0.41 | 0.49 | -7.1 [-9.9, -4.4] | -5.0 | 3 | -10.9 | -23.5 |
| ALL/ALL | ss_gap_with | 0.40 | 4.0 | 1.5 | 0.51 | 0.47 | 2.5 [1.5, 3.5] | 5.0 | 3 | 3.1 | 3.7 |
| ALL/ALL | ss_a_slow_hit_with | 0.53 | 3.6 | 1.2 | 0.50 | 0.47 | 2.4 [1.4, 3.5] | 4.6 | 3 | 3.7 | 4.5 |
| ALL/ALL | ss_range_used_lt50 | 0.31 | 4.2 | 1.8 | 0.50 | 0.48 | 2.4 [1.4, 3.5] | 4.6 | 3 | 2.7 | 2.6 |
| ALL/ALL | ss_inside | 0.05 | -2.3 | 2.8 | 0.44 | 0.49 | -5.1 [-7.4, -2.9] | -4.6 | 3 | -9.1 | -7.0 |
| ALL/ALL | ss_orb15_against_beyond | 0.08 | -1.6 | 2.7 | 0.44 | 0.49 | -4.3 [-6.2, -2.4] | -4.5 | 3 | -4.0 | -3.7 |
| ALL/ALL | ss_orb30_against_beyond | 0.07 | -1.7 | 2.8 | 0.44 | 0.49 | -4.4 [-6.5, -2.4] | -4.2 | 3 | -2.7 | -5.5 |
| ALL/ALL | ss_a_fast_fresh30 | 0.18 | 0.2 | 3.0 | 0.46 | 0.49 | -2.8 [-4.1, -1.5] | -4.2 | 3 | -4.6 | -8.2 |
| ALL/ALL | ss_gap_against | 0.32 | 1.0 | 3.2 | 0.47 | 0.49 | -2.2 [-3.2, -1.2] | -4.1 | 3 | -3.2 | -5.1 |
| ALL/ALL | ss_orb30_beyond | 0.64 | 3.3 | 1.0 | 0.50 | 0.47 | 2.2 [1.2, 3.3] | 4.1 | 3 | 2.6 | 4.4 |
| ALL/ALL | ss_a_std_now_against | 0.05 | -2.1 | 2.7 | 0.43 | 0.49 | -4.8 [-7.1, -2.5] | -4.1 | 3 | -4.2 | -10.3 |
| ALL/ALL | ss_orb5_against_beyond | 0.09 | -0.4 | 2.8 | 0.45 | 0.49 | -3.2 [-4.9, -1.5] | -3.7 | 3 | -2.6 | -1.5 |
| ALL/ALL | ss_volbo_slow_beyond | 0.16 | 4.6 | 2.1 | 0.51 | 0.48 | 2.5 [1.2, 3.8] | 3.7 | 3 | 5.2 | 8.3 |
| ALL/ALL | ss_orb5_beyond | 0.74 | 3.0 | 1.1 | 0.49 | 0.47 | 1.9 [0.8, 3.1] | 3.4 | 3 | 3.5 | 4.7 |
| ALL/ALL | ss_stretch_beyond | 0.59 | 3.1 | 1.7 | 0.49 | 0.48 | 1.5 [0.5, 2.5] | 3.0 | 3 | 1.2 | 0.6 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B2_sessanch_named.parquet

## Sub-block C1: execution-desk levels, seasonality, volume-by-time curve

### C1 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 34 conditions; 835 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 1 conditions with |t|>2 (chance alone: about 1). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | ex_mv_with | 0.86 | 124.4 | -14.3 | 0.44 | 0.41 | 138.7 [60.6, 216.9] | 3.5 | 4 | 141.0 | 310.0 |
| ALL/ALL | ex_ss_arrival_against1 | 0.08 | 10.7 | 114.7 | 0.42 | 0.44 | -104.0 [-219.6, 11.6] | -1.8 | 3 | -267.5 | -332.2 |
| ALL/ALL | ex_gx_twap_side | 0.81 | 118.5 | 51.1 | 0.44 | 0.42 | 67.4 [-8.5, 143.3] | 1.7 | 4 | 5.8 | 213.8 |
| ALL/ALL | ex_seas120_strong_against | 0.14 | 172.5 | 95.3 | 0.46 | 0.43 | 77.2 [-11.6, 165.9] | 1.7 | 3 | 163.1 | 150.7 |
| ALL/ALL | ex_range30_lo | 0.20 | 142.5 | 82.7 | 0.44 | 0.43 | 59.8 [-23.4, 143.1] | 1.4 | 4 | 186.0 | 89.8 |
| ALL/ALL | ex_gx_arrival_against1 | 0.18 | 68.6 | 114.0 | 0.43 | 0.44 | -45.4 [-117.0, 26.3] | -1.2 | 3 | -116.2 | -167.3 |
| ALL/ALL | ex_gx_vwap_ext1_against | 0.05 | 54.1 | 108.7 | 0.42 | 0.44 | -54.6 [-152.9, 43.8] | -1.1 | 4 | -56.9 | -286.3 |
| ALL/ALL | ex_gx_vwap_side | 0.85 | 113.3 | 64.6 | 0.44 | 0.43 | 48.7 [-39.2, 136.6] | 1.1 | 4 | 4.1 | 237.6 |
| ALL/ALL | ex_ss_vwap_ext1_with | 0.49 | 123.2 | 91.0 | 0.44 | 0.43 | 32.2 [-31.8, 96.2] | 1.0 | 4 | 19.3 | 7.4 |
| ALL/ALL | ex_gx_twap_vwap_with | 0.44 | 116.1 | 97.6 | 0.44 | 0.43 | 18.5 [-44.1, 81.1] | 0.6 | 3 | 5.1 | 112.4 |
| ALL/ALL | ex_volcurve_behind | 0.23 | 117.6 | 102.2 | 0.44 | 0.44 | 15.4 [-62.0, 92.8] | 0.4 | 4 | 49.3 | 158.2 |
| ALL/ALL | ex_volcurve_ahead_move_with | 0.28 | 103.1 | 106.9 | 0.43 | 0.44 | -3.8 [-72.6, 65.0] | -0.1 | 3 | -67.7 | -9.6 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | ex_seas120_strong_against | 0.17 | 283.0 | 81.7 | 0.60 | 0.51 | 201.3 [26.2, 376.4] | 2.3 | 4 | 164.9 | -11.1 |
| A7/0 | ex_gx_vwap_ext2_with | 0.26 | 199.7 | 82.0 | 0.56 | 0.51 | 117.6 [-33.4, 268.7] | 1.5 | 3 | 172.0 | 275.1 |
| A7/0 | ex_ss_vwap_ext2_with | 0.26 | 199.7 | 82.0 | 0.56 | 0.51 | 117.6 [-33.4, 268.7] | 1.5 | 3 | 172.0 | 275.1 |
| A7/0 | ex_seas120_strong_with | 0.18 | 18.2 | 136.0 | 0.48 | 0.53 | -117.8 [-288.2, 52.6] | -1.4 | 3 | -370.8 | -175.8 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | ex_volcurve_ahead | 0.24 | -105.5 | 318.8 | 0.39 | 0.51 | -424.3 [-876.6, 28.0] | -1.8 | 4 | -643.7 | -344.6 |
| H7/0 | ex_volcurve_sess_ahead | 0.24 | -111.1 | 303.4 | 0.40 | 0.50 | -414.5 [-866.6, 37.6] | -1.8 | 4 | -745.3 | -344.6 |
| H7/0 | ex_volcurve_ahead_move_with | 0.24 | -89.8 | 311.5 | 0.40 | 0.51 | -401.3 [-856.5, 53.9] | -1.7 | 4 | -643.7 | -344.6 |
| H7/0 | ex_gx_vwap_ext1_with | 0.31 | 455.1 | 102.2 | 0.51 | 0.47 | 353.0 [-87.5, 793.5] | 1.6 | 3 | 362.8 | 564.3 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | ex_ss_twap_vwap_with | 0.68 | 88.3 | -52.8 | 0.49 | 0.45 | 141.1 [-107.4, 389.6] | 1.1 | 3 | 332.0 | 305.9 |
| H7/3 | ex_gx_vwap_ext1_with | 0.76 | 75.5 | -61.5 | 0.50 | 0.43 | 137.1 [-130.1, 404.2] | 1.0 | 3 | 260.1 | 72.7 |
| H7/3 | ex_gx_arrival_with1 | 0.72 | 78.0 | -49.6 | 0.49 | 0.44 | 127.6 [-131.2, 386.4] | 1.0 | 3 | 161.6 | 229.5 |
| H7/3 | ex_seas30_with | 0.47 | 58.0 | 28.6 | 0.49 | 0.47 | 29.5 [-204.7, 263.6] | 0.2 | 3 | 170.0 | 389.5 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | ex_mv_large2 | 0.43 | 197.1 | 8.7 | 0.48 | 0.42 | 188.4 [82.9, 293.9] | 3.5 | 4 | 81.7 | 105.1 |
| K7/0 | ex_mv_with_large | 0.38 | 208.5 | 18.2 | 0.48 | 0.42 | 190.3 [79.7, 300.8] | 3.4 | 4 | 39.5 | 134.3 |
| K7/0 | ex_mv_pullback_hold | 0.38 | 208.5 | 18.2 | 0.48 | 0.42 | 190.3 [79.7, 300.8] | 3.4 | 4 | 39.5 | 134.3 |
| K7/0 | ex_mv_with | 0.72 | 127.0 | -6.9 | 0.45 | 0.42 | 133.9 [27.0, 240.8] | 2.5 | 4 | 53.5 | 162.1 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | ex_mv_large2 | 0.69 | 70.0 | -48.6 | 0.44 | 0.39 | 118.6 [4.7, 232.5] | 2.0 | 4 | 100.6 | 80.3 |
| K7/1 | ex_mv_with | 0.76 | 61.9 | -58.1 | 0.44 | 0.39 | 120.0 [-4.2, 244.2] | 1.9 | 3 | 233.0 | 316.4 |
| K7/1 | ex_range30_lo | 0.17 | 134.9 | 15.9 | 0.49 | 0.41 | 119.0 [-45.1, 283.2] | 1.4 | 3 | 198.6 | 94.0 |
| K7/1 | ex_mv_with_large | 0.62 | 61.3 | -13.6 | 0.44 | 0.41 | 74.9 [-39.1, 188.9] | 1.3 | 4 | 166.3 | 272.3 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | ex_mv_large2 | 0.85 | 26.1 | -76.3 | 0.43 | 0.38 | 102.5 [-36.6, 241.6] | 1.4 | 3 | 547.1 | 598.5 |
| K7/3 | ex_volcurve_sess_ahead | 0.24 | -53.6 | 30.3 | 0.39 | 0.44 | -83.9 [-200.1, 32.3] | -1.4 | 3 | -265.0 | -471.6 |
| K7/3 | ex_gx_vwap_ext1_with | 0.62 | 34.7 | -29.7 | 0.44 | 0.41 | 64.4 [-38.4, 167.3] | 1.2 | 3 | 172.4 | 81.4 |
| K7/3 | ex_ss_arrival_with1 | 0.63 | 29.3 | -22.9 | 0.43 | 0.41 | 52.2 [-51.5, 155.8] | 1.0 | 3 | 207.4 | 118.1 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | ex_gx_vwap_ext2_with | 0.35 | 167.3 | 4.9 | 0.49 | 0.44 | 162.4 [4.2, 320.6] | 2.0 | 4 | 446.1 | 655.8 |
| K7/4 | ex_seas120_strong_against | 0.12 | 243.5 | 37.9 | 0.53 | 0.45 | 205.6 [-20.7, 432.0] | 1.8 | 4 | 623.1 | 428.2 |
| K7/4 | ex_seas120_strong_with | 0.13 | -102.2 | 86.5 | 0.38 | 0.47 | -188.7 [-400.8, 23.3] | -1.7 | 4 | -400.8 | -907.2 |
| K7/4 | ex_ss_twap_side | 0.96 | 39.0 | 227.6 | 0.45 | 0.58 | -188.6 [-486.2, 108.9] | -1.2 | 3 | -85.8 | 1567.5 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | ex_mv_with | 0.96 | 6.2 | -300.0 | 0.41 | 0.25 | 306.2 [110.5, 501.8] | 3.1 | 3 | 356.6 | 705.0 |
| M7/1 | ex_range30_lo | 0.22 | 116.4 | -36.3 | 0.46 | 0.39 | 152.7 [22.3, 283.1] | 2.3 | 4 | 176.4 | -3.3 |
| M7/1 | ex_ss_arrival_with1 | 0.60 | -68.5 | 49.3 | 0.38 | 0.42 | -117.9 [-232.6, -3.2] | -2.0 | 3 | -163.4 | -279.5 |
| M7/1 | ex_seas30_with | 0.49 | 41.8 | -46.6 | 0.42 | 0.39 | 88.3 [-17.0, 193.7] | 1.6 | 4 | 97.9 | 27.3 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | ex_seas30_strong_with | 0.14 | 175.1 | 17.7 | 0.51 | 0.42 | 157.4 [6.9, 307.9] | 2.1 | 4 | 263.1 | 233.9 |
| M7/3 | ex_seas120_strong_with | 0.14 | 159.3 | 21.2 | 0.50 | 0.43 | 138.1 [-16.8, 293.0] | 1.7 | 4 | 467.6 | 633.1 |
| M7/3 | ex_seas30_strong_against | 0.15 | -63.5 | 58.3 | 0.38 | 0.45 | -121.9 [-263.3, 19.6] | -1.7 | 3 | -11.0 | -95.9 |
| M7/3 | ex_gx_vwap_ext1_with | 0.85 | 22.6 | 141.9 | 0.43 | 0.48 | -119.2 [-265.5, 27.1] | -1.6 | 4 | -180.9 | 43.2 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | ex_seas30_with | 0.49 | 248.7 | 107.2 | 0.40 | 0.35 | 141.4 [-70.8, 353.6] | 1.3 | 3 | 334.5 | 253.2 |
| O7/3 | ex_gx_arrival_against1 | 0.29 | 101.4 | 206.9 | 0.33 | 0.39 | -105.5 [-337.0, 126.0] | -0.9 | 3 | -512.9 | -1051.2 |
| O7/3 | ex_gx_twap_vwap_with | 0.42 | 136.6 | 205.0 | 0.36 | 0.39 | -68.4 [-282.6, 145.8] | -0.6 | 3 | -519.0 | -568.9 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | ex_mv_with | 0.84 | 500.9 | -22.6 | 0.44 | 0.41 | 523.5 [29.7, 1017.3] | 2.1 | 4 | 211.6 | 876.3 |
| P7/0 | ex_mv_vwap_side | 0.81 | 491.6 | 90.0 | 0.44 | 0.43 | 401.6 [-75.2, 878.4] | 1.7 | 3 | 352.2 | 1362.0 |
| P7/0 | ex_range30_hi | 0.29 | 618.6 | 263.8 | 0.45 | 0.42 | 354.8 [-111.6, 821.2] | 1.5 | 3 | 439.1 | 807.3 |
| P7/0 | ex_seas30_strong_against | 0.16 | 173.5 | 470.1 | 0.43 | 0.44 | -296.5 [-822.3, 229.2] | -1.1 | 3 | -410.8 | -522.5 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | ex_range30_hi | 0.24 | -127.8 | 84.7 | 0.35 | 0.39 | -212.5 [-476.6, 51.7] | -1.6 | 3 | -183.2 | -606.8 |
| P7/1 | ex_mv_pullback_hold | 0.67 | 81.0 | -63.9 | 0.38 | 0.37 | 144.9 [-70.1, 359.9] | 1.3 | 4 | 191.4 | 520.2 |
| P7/1 | ex_mv_large2 | 0.69 | 74.6 | -60.6 | 0.38 | 0.38 | 135.1 [-79.2, 349.5] | 1.2 | 4 | 179.6 | 500.6 |
| P7/1 | ex_mv_with_large | 0.68 | 73.1 | -52.2 | 0.38 | 0.38 | 125.4 [-89.9, 340.6] | 1.1 | 4 | 211.3 | 500.6 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | ex_ss_arrival_with1 | 0.75 | 23.9 | -202.2 | 0.39 | 0.37 | 226.1 [-39.3, 491.5] | 1.7 | 4 | 746.4 | 343.2 |
| P7/3 | ex_gx_arrival_with1 | 0.61 | 41.9 | -151.9 | 0.39 | 0.39 | 193.8 [-61.2, 448.9] | 1.5 | 3 | 734.0 | 925.9 |
| P7/3 | ex_ss_vwap_side | 0.92 | -12.5 | -285.3 | 0.39 | 0.35 | 272.8 [-133.0, 678.7] | 1.3 | 3 | 136.4 | -423.3 |
| P7/3 | ex_volcurve_sess_ahead | 0.23 | -198.8 | 15.9 | 0.37 | 0.39 | -214.7 [-536.5, 107.2] | -1.3 | 3 | -108.4 | -1056.2 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | ex_gx_vwap_ext1_with | 0.62 | 553.9 | 53.1 | 0.55 | 0.48 | 500.8 [-37.3, 1038.9] | 1.8 | 4 | 616.3 | 527.3 |
| U7/0 | ex_ss_vwap_ext1_with | 0.62 | 553.9 | 53.1 | 0.55 | 0.48 | 500.8 [-37.3, 1038.9] | 1.8 | 4 | 616.3 | 527.3 |
| U7/0 | ex_ss_arrival_with1 | 0.56 | 203.9 | 564.2 | 0.50 | 0.55 | -360.3 [-893.8, 173.3] | -1.3 | 3 | -449.3 | -996.2 |
| U7/0 | ex_gx_arrival_with1 | 0.56 | 203.9 | 564.2 | 0.50 | 0.55 | -360.3 [-893.8, 173.3] | -1.3 | 3 | -449.3 | -996.2 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | ex_gx_twap_vwap_with | 0.63 | 284.3 | -121.5 | 0.52 | 0.48 | 405.8 [-87.1, 898.7] | 1.6 | 4 | 141.1 | 562.4 |
| U7/1 | ex_gx_arrival_with1 | 0.32 | -154.9 | 268.6 | 0.48 | 0.52 | -423.5 [-945.6, 98.7] | -1.6 | 4 | -396.1 | -779.1 |
| U7/1 | ex_mv_large2 | 0.89 | 96.9 | 401.9 | 0.49 | 0.57 | -305.0 [-838.4, 228.3] | -1.1 | 4 | -337.1 | 451.1 |
| U7/1 | ex_mv_with_large | 0.89 | 96.9 | 401.9 | 0.49 | 0.57 | -305.0 [-838.4, 228.3] | -1.1 | 4 | -337.1 | 451.1 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_C1_exec_named.parquet

### C1 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 34 conditions; 1329 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 23 conditions with |t|>2 (chance alone: about 1). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | ex_gx_vwap_side | 0.85 | 3.3 | -1.7 | 0.49 | 0.44 | 5.0 [3.6, 6.3] | 7.1 | 4 | 4.4 | 4.6 |
| ALL/ALL | ex_gx_twap_side | 0.83 | 3.3 | -1.2 | 0.49 | 0.45 | 4.6 [3.3, 5.8] | 7.0 | 3 | 2.9 | 2.7 |
| ALL/ALL | ex_ss_vwap_ext2_with | 0.13 | 6.9 | 1.9 | 0.53 | 0.48 | 5.0 [3.6, 6.5] | 6.8 | 3 | 7.7 | 9.7 |
| ALL/ALL | ex_volcurve_behind | 0.22 | 5.5 | 1.7 | 0.51 | 0.48 | 3.8 [2.7, 4.9] | 6.7 | 4 | 4.4 | 2.1 |
| ALL/ALL | ex_gx_vwap_ext1_with | 0.59 | 3.8 | 0.8 | 0.50 | 0.47 | 3.0 [2.0, 4.0] | 6.1 | 3 | 2.0 | 2.6 |
| ALL/ALL | ex_mv_with | 0.88 | 2.9 | -0.5 | 0.49 | 0.45 | 3.4 [2.0, 4.9] | 4.6 | 4 | 3.9 | 4.7 |
| ALL/ALL | ex_ss_arrival_against1 | 0.06 | -1.8 | 2.8 | 0.44 | 0.49 | -4.6 [-6.6, -2.6] | -4.4 | 3 | -3.9 | -4.0 |
| ALL/ALL | ex_ss_vwap_side | 0.93 | 2.8 | -1.3 | 0.49 | 0.44 | 4.2 [2.3, 6.1] | 4.3 | 4 | 3.7 | 3.5 |
| ALL/ALL | ex_volcurve_sess_behind | 0.27 | 4.2 | 1.9 | 0.51 | 0.48 | 2.3 [1.2, 3.4] | 4.1 | 4 | 1.0 | 4.1 |
| ALL/ALL | ex_seas120_strong_against | 0.13 | 5.1 | 2.2 | 0.50 | 0.48 | 3.0 [1.5, 4.4] | 4.1 | 3 | 4.6 | 0.4 |
| ALL/ALL | ex_gx_vwap_ext2_with | 0.34 | 3.9 | 1.9 | 0.50 | 0.48 | 2.0 [1.0, 3.0] | 3.8 | 4 | 1.0 | 3.8 |
| ALL/ALL | ex_ss_twap_side | 0.93 | 2.8 | -0.8 | 0.49 | 0.45 | 3.6 [1.7, 5.5] | 3.7 | 3 | 3.1 | 1.5 |
| ALL/ALL | ex_gx_vwap_ext1_against | 0.05 | -1.2 | 2.8 | 0.45 | 0.49 | -4.0 [-6.1, -1.8] | -3.7 | 4 | -2.4 | -2.9 |
| ALL/ALL | ex_range30_lo | 0.26 | 4.0 | 2.0 | 0.51 | 0.48 | 1.9 [0.8, 3.0] | 3.5 | 4 | 0.2 | 1.8 |
| ALL/ALL | ex_ss_vwap_ext1_against | 0.01 | -7.1 | 2.6 | 0.38 | 0.49 | -9.7 [-15.2, -4.2] | -3.5 | 3 | -5.5 | -17.2 |
| ALL/ALL | ex_ss_vwap_ext1_with | 0.46 | 3.4 | 1.8 | 0.50 | 0.48 | 1.7 [0.7, 2.7] | 3.3 | 4 | 1.2 | 4.2 |
| ALL/ALL | ex_seas30_strong_against | 0.15 | 3.9 | 2.2 | 0.50 | 0.48 | 1.7 [0.4, 3.0] | 2.5 | 3 | 4.0 | 3.7 |
| ALL/ALL | ex_ss_twap_vwap_with | 0.50 | 2.9 | 2.2 | 0.49 | 0.48 | 0.6 [-0.3, 1.6] | 1.3 | 3 | 1.9 | 3.8 |
| ALL/ALL | ex_mv_vwap_side | 0.95 | 2.5 | 1.6 | 0.49 | 0.47 | 0.9 [-1.3, 3.1] | 0.8 | 3 | 0.5 | 2.7 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_C1_exec_named.parquet

## Sub-block C2: statistical order-flow measures (tape and book: signed volume, book imbalance, Kyle lambda, trade size, quote-to-trade)

### C2 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 72 conditions; 1745 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 3 conditions with |t|>2 (chance alone: about 3). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | fl_bimb5300s_with | 0.51 | 62.3 | 128.6 | 0.43 | 0.44 | -66.3 [-128.2, -4.5] | -2.1 | 4 | -52.7 | -112.2 |
| ALL/ALL | fl_kyle_hi | 0.08 | 224.1 | 77.8 | 0.46 | 0.43 | 146.3 [9.0, 283.6] | 2.1 | 3 | 454.7 | 569.9 |
| ALL/ALL | fl_ofi5s_z1 | 0.12 | 172.8 | 83.9 | 0.46 | 0.43 | 88.9 [0.5, 177.2] | 2.0 | 4 | 39.7 | 25.1 |
| ALL/ALL | fl_ofi1s_strong | 0.37 | 114.8 | 47.7 | 0.44 | 0.42 | 67.1 [-3.9, 138.2] | 1.9 | 3 | 123.3 | 101.7 |
| ALL/ALL | fl_mic60s_with | 0.49 | 65.4 | 122.8 | 0.43 | 0.44 | -57.4 [-119.3, 4.5] | -1.8 | 3 | -64.0 | -152.6 |
| ALL/ALL | fl_bimb101s_strong | 0.07 | 198.4 | 86.2 | 0.44 | 0.43 | 112.2 [-12.1, 236.5] | 1.8 | 3 | 112.1 | 123.4 |
| ALL/ALL | fl_ofi1s_z2 | 0.03 | 244.7 | 89.7 | 0.47 | 0.43 | 155.0 [-18.0, 327.9] | 1.8 | 4 | 147.9 | 196.7 |
| ALL/ALL | fl_bimb10300s_strong | 0.04 | -66.0 | 101.0 | 0.42 | 0.44 | -167.0 [-364.4, 30.4] | -1.7 | 3 | -355.8 | -666.2 |
| ALL/ALL | fl_bimb1015s_strong | 0.03 | 284.7 | 89.4 | 0.48 | 0.43 | 195.3 [-37.5, 428.1] | 1.6 | 3 | 46.0 | -189.6 |
| ALL/ALL | fl_bimb10300s_with | 0.47 | 68.3 | 118.1 | 0.43 | 0.44 | -49.7 [-112.0, 12.5] | -1.6 | 3 | -75.4 | -177.0 |
| ALL/ALL | fl_ofi15s_z2 | 0.08 | 172.1 | 87.9 | 0.46 | 0.43 | 84.2 [-22.9, 191.4] | 1.5 | 3 | 194.1 | -16.3 |
| ALL/ALL | fl_ofi5s_strong | 0.30 | 132.9 | 77.2 | 0.45 | 0.43 | 55.7 [-15.3, 126.7] | 1.5 | 4 | 124.0 | -9.8 |
| ALL/ALL | fl_mic300s_with | 0.51 | 71.3 | 118.7 | 0.43 | 0.44 | -47.4 [-109.3, 14.5] | -1.5 | 4 | -45.1 | 18.6 |
| ALL/ALL | fl_bimb560s_with | 0.49 | 71.1 | 117.4 | 0.43 | 0.44 | -46.3 [-108.2, 15.6] | -1.5 | 3 | -95.0 | -120.0 |
| ALL/ALL | fl_bimb115s_with | 0.49 | 71.3 | 116.9 | 0.43 | 0.44 | -45.6 [-107.5, 16.3] | -1.4 | 3 | -154.5 | -157.0 |
| ALL/ALL | fl_mic15s_with | 0.50 | 72.3 | 116.3 | 0.43 | 0.44 | -44.0 [-105.9, 17.9] | -1.4 | 3 | -126.6 | -120.7 |
| ALL/ALL | fl_ofi15s_strong | 0.25 | 139.4 | 85.4 | 0.45 | 0.43 | 54.0 [-23.2, 131.2] | 1.4 | 3 | 12.5 | -5.6 |
| ALL/ALL | fl_bimb160s_with | 0.49 | 72.8 | 115.6 | 0.43 | 0.44 | -42.8 [-104.7, 19.1] | -1.4 | 3 | -73.8 | -114.9 |
| ALL/ALL | fl_bimb515s_with | 0.51 | 73.5 | 116.2 | 0.43 | 0.44 | -42.7 [-104.6, 19.3] | -1.3 | 3 | -81.9 | -163.9 |
| ALL/ALL | fl_bimb105s_with | 0.48 | 72.4 | 114.9 | 0.43 | 0.44 | -42.5 [-104.5, 19.5] | -1.3 | 3 | -86.3 | -154.6 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | fl_ofi1s_strong | 0.49 | -6.1 | 226.3 | 0.46 | 0.57 | -232.4 [-438.8, -26.0] | -2.2 | 3 | -226.9 | -139.6 |
| A7/0 | fl_ofi1s_with | 0.25 | -17.7 | 162.9 | 0.46 | 0.54 | -180.7 [-344.0, -17.3] | -2.2 | 3 | -331.2 | -180.7 |
| A7/0 | fl_bigshare300_up | 0.33 | 21.3 | 181.0 | 0.48 | 0.55 | -159.7 [-319.1, -0.3] | -2.0 | 4 | -138.9 | -3.8 |
| A7/0 | fl_bimb10300s_with | 0.57 | 64.1 | 187.6 | 0.49 | 0.56 | -123.5 [-267.2, 20.2] | -1.7 | 4 | -108.3 | -154.6 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | fl_qtr60_hi | 0.35 | -122.0 | 454.9 | 0.45 | 0.51 | -576.9 [-988.1, -165.7] | -2.7 | 4 | -177.8 | 46.9 |
| H7/0 | fl_qtr300_hi | 0.14 | -288.2 | 333.1 | 0.40 | 0.50 | -621.3 [-1133.1, -109.5] | -2.4 | 4 | -1277.7 | -925.4 |
| H7/0 | fl_bimb515s_with | 0.57 | 400.9 | 42.5 | 0.51 | 0.45 | 358.4 [-40.1, 756.9] | 1.8 | 4 | 693.9 | 115.7 |
| H7/0 | fl_ofi300s_z1 | 0.33 | 503.7 | 116.4 | 0.51 | 0.47 | 387.3 [-43.5, 818.1] | 1.8 | 3 | 480.5 | 387.1 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | fl_bimb115s_with | 0.46 | 141.6 | -40.9 | 0.51 | 0.46 | 182.5 [-50.4, 415.4] | 1.5 | 3 | 194.1 | 205.5 |
| H7/3 | fl_ofi60s_with | 0.57 | 101.2 | -34.2 | 0.50 | 0.45 | 135.5 [-100.2, 371.1] | 1.1 | 3 | 404.5 | 999.7 |
| H7/3 | fl_bimb160s_with | 0.54 | 96.1 | -21.3 | 0.49 | 0.47 | 117.5 [-116.6, 351.6] | 1.0 | 3 | 327.2 | -34.0 |
| H7/3 | fl_bimb15s_with | 0.49 | 90.9 | -4.3 | 0.49 | 0.47 | 95.2 [-138.0, 328.3] | 0.8 | 3 | 428.9 | -144.1 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | fl_ofi5s_z1 | 0.12 | 302.5 | 77.2 | 0.53 | 0.44 | 225.3 [50.0, 400.6] | 2.5 | 4 | 135.2 | -21.7 |
| K7/0 | fl_ofi1s_strong | 0.44 | 225.0 | 28.7 | 0.49 | 0.42 | 196.3 [26.3, 366.4] | 2.3 | 4 | 171.8 | -23.0 |
| K7/0 | fl_ofi1s_with | 0.21 | 230.5 | 70.6 | 0.49 | 0.44 | 159.9 [19.3, 300.5] | 2.2 | 4 | 186.5 | -17.1 |
| K7/0 | fl_ofi1s_z1 | 0.06 | 359.2 | 89.1 | 0.53 | 0.44 | 270.1 [24.6, 515.5] | 2.2 | 3 | 315.3 | -243.6 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | fl_mic60s_with | 0.47 | -45.0 | 105.9 | 0.39 | 0.46 | -150.9 [-267.5, -34.4] | -2.5 | 4 | -68.3 | -29.5 |
| K7/1 | fl_bimb160s_with | 0.46 | -40.9 | 101.9 | 0.39 | 0.46 | -142.8 [-259.3, -26.3] | -2.4 | 4 | -99.5 | -84.5 |
| K7/1 | fl_bimb10300s_strong | 0.03 | -306.7 | 47.7 | 0.31 | 0.43 | -354.4 [-669.8, -39.0] | -2.2 | 3 | -353.2 | -330.4 |
| K7/1 | fl_ofi60s_with | 0.73 | 74.1 | -67.0 | 0.44 | 0.39 | 141.1 [12.8, 269.4] | 2.2 | 3 | 242.2 | 129.4 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | fl_mic300s_with | 0.50 | -83.4 | 103.0 | 0.38 | 0.47 | -186.4 [-286.1, -86.7] | -3.7 | 4 | -323.0 | -135.6 |
| K7/3 | fl_bimb560s_with | 0.57 | -55.0 | 94.9 | 0.39 | 0.47 | -149.9 [-251.1, -48.8] | -2.9 | 4 | -260.8 | -193.1 |
| K7/3 | fl_bimb1300s_with | 0.49 | -57.1 | 74.2 | 0.40 | 0.45 | -131.4 [-231.3, -31.4] | -2.6 | 4 | -225.4 | -74.6 |
| K7/3 | fl_bimb5300s_with | 0.52 | -49.2 | 75.5 | 0.39 | 0.46 | -124.7 [-224.9, -24.6] | -2.4 | 4 | -188.3 | -203.8 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | fl_bimb51s_strong | 0.09 | 454.8 | 24.0 | 0.62 | 0.44 | 430.8 [183.3, 678.3] | 3.4 | 4 | 702.5 | 332.0 |
| K7/4 | fl_bimb515s_with | 0.57 | 141.7 | -43.2 | 0.48 | 0.42 | 184.9 [41.8, 328.1] | 2.5 | 4 | 138.2 | -337.1 |
| K7/4 | fl_mic1s_with | 0.37 | 166.8 | -0.0 | 0.50 | 0.44 | 166.8 [20.8, 312.8] | 2.2 | 3 | 444.8 | 166.5 |
| K7/4 | fl_bimb11s_with | 0.37 | 166.8 | -0.0 | 0.50 | 0.44 | 166.8 [20.8, 312.8] | 2.2 | 3 | 444.8 | 166.5 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | fl_ofi5s_with | 0.47 | 62.0 | -59.5 | 0.43 | 0.39 | 121.5 [15.8, 227.2] | 2.3 | 3 | 202.1 | 59.8 |
| M7/1 | fl_bimb11s_strong | 0.25 | -94.5 | 26.9 | 0.38 | 0.41 | -121.4 [-242.6, -0.1] | -2.0 | 4 | -270.5 | 2.0 |
| M7/1 | fl_ofi1s_with | 0.23 | 90.6 | -30.5 | 0.43 | 0.40 | 121.0 [-5.4, 247.5] | 1.9 | 4 | 259.9 | 254.7 |
| M7/1 | fl_bimb5300s_with | 0.51 | -51.6 | 47.3 | 0.39 | 0.42 | -98.8 [-204.1, 6.4] | -1.8 | 4 | -131.9 | -120.7 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | fl_ofi15s_z1 | 0.22 | 115.7 | 19.2 | 0.48 | 0.43 | 96.4 [-30.2, 223.0] | 1.5 | 3 | 149.2 | 253.0 |
| M7/3 | fl_ofi60s_with | 0.84 | 25.1 | 119.2 | 0.43 | 0.48 | -94.1 [-235.3, 47.1] | -1.3 | 3 | -284.0 | 119.9 |
| M7/3 | fl_bimb5300s_with | 0.45 | 7.1 | 66.9 | 0.41 | 0.46 | -59.8 [-163.4, 43.8] | -1.1 | 3 | -67.0 | 0.8 |
| M7/3 | fl_bigshare60_up | 0.30 | 83.5 | 21.4 | 0.46 | 0.43 | 62.1 [-51.5, 175.7] | 1.1 | 3 | 299.9 | 176.9 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | fl_ofi5s_with | 0.45 | 253.8 | 111.6 | 0.41 | 0.34 | 142.2 [-70.9, 355.4] | 1.3 | 3 | 463.5 | 435.4 |
| O7/3 | fl_mic5s_with | 0.50 | 114.0 | 238.1 | 0.35 | 0.39 | -124.1 [-336.1, 87.9] | -1.1 | 3 | -626.1 | -869.2 |
| O7/3 | fl_bimb560s_with | 0.61 | 219.2 | 108.4 | 0.39 | 0.35 | 110.9 [-105.3, 327.0] | 1.0 | 3 | 246.0 | 54.9 |
| O7/3 | fl_bimb15s_with | 0.48 | 120.1 | 228.7 | 0.36 | 0.39 | -108.6 [-320.5, 103.2] | -1.0 | 4 | -482.8 | -869.2 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | fl_bimb5300s_with | 0.52 | 179.0 | 570.7 | 0.41 | 0.44 | -391.7 [-821.7, 38.2] | -1.8 | 3 | -666.9 | -1175.1 |
| P7/0 | fl_ofi1s_z1 | 0.04 | 1304.1 | 327.5 | 0.52 | 0.42 | 976.6 [-132.4, 2085.6] | 1.7 | 3 | 718.0 | 3194.2 |
| P7/0 | fl_bimb160s_strong | 0.08 | -319.2 | 424.8 | 0.35 | 0.43 | -744.0 [-1599.9, 111.8] | -1.7 | 4 | -140.0 | -1262.2 |
| P7/0 | fl_ofi60s_z2 | 0.12 | -109.8 | 433.0 | 0.39 | 0.43 | -542.8 [-1170.7, 85.1] | -1.7 | 3 | -60.5 | 1319.1 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | fl_bimb101s_strong | 0.07 | 636.4 | -10.2 | 0.51 | 0.37 | 646.6 [142.6, 1150.7] | 2.5 | 3 | 1380.7 | 2257.8 |
| P7/1 | fl_ofi300s_z2 | 0.06 | 619.3 | -5.0 | 0.51 | 0.37 | 624.3 [125.0, 1123.6] | 2.5 | 4 | 1020.5 | 1151.0 |
| P7/1 | fl_ofi5s_with | 0.43 | -109.9 | 144.1 | 0.35 | 0.40 | -254.0 [-481.8, -26.2] | -2.2 | 3 | -468.7 | -503.5 |
| P7/1 | fl_bimb560s_with | 0.42 | 181.4 | -71.1 | 0.41 | 0.36 | 252.5 [20.0, 484.9] | 2.1 | 3 | 394.6 | 674.1 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | fl_bimb101s_with | 0.49 | -275.3 | 195.7 | 0.33 | 0.44 | -471.0 [-729.2, -212.8] | -3.6 | 4 | -709.4 | -636.4 |
| P7/3 | fl_bimb1060s_with | 0.38 | -264.3 | 107.9 | 0.34 | 0.42 | -372.2 [-633.4, -111.1] | -2.8 | 4 | -20.6 | -536.5 |
| P7/3 | fl_mic300s_with | 0.49 | -211.6 | 134.5 | 0.36 | 0.42 | -346.1 [-605.1, -87.1] | -2.6 | 4 | -13.8 | -252.3 |
| P7/3 | fl_bimb51s_with | 0.49 | -203.5 | 131.9 | 0.34 | 0.44 | -335.4 [-594.7, -76.1] | -2.5 | 3 | -556.8 | -1123.8 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | fl_bimb160s_with | 0.54 | 124.2 | 657.8 | 0.50 | 0.56 | -533.6 [-1078.2, 10.9] | -1.9 | 3 | -944.2 | -1034.9 |
| U7/0 | fl_mic60s_with | 0.53 | 152.5 | 621.9 | 0.50 | 0.56 | -469.4 [-1014.1, 75.3] | -1.7 | 3 | -1016.8 | -1233.5 |
| U7/0 | fl_ofi15s_strong | 0.29 | 96.2 | 493.5 | 0.47 | 0.55 | -397.4 [-1011.7, 217.0] | -1.3 | 3 | -652.3 | -1837.0 |
| U7/0 | fl_bimb10300s_with | 0.51 | 212.7 | 536.5 | 0.51 | 0.54 | -323.8 [-867.9, 220.3] | -1.2 | 3 | -171.5 | -631.8 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | fl_qtr60_hi | 0.19 | -473.8 | 282.0 | 0.44 | 0.52 | -755.9 [-1346.5, -165.2] | -2.5 | 4 | -848.5 | -1706.1 |
| U7/1 | fl_bimb51s_with | 0.49 | -101.5 | 357.3 | 0.48 | 0.53 | -458.9 [-933.7, 16.0] | -1.9 | 3 | -312.3 | -691.6 |
| U7/1 | fl_kyle_lo | 0.34 | -166.7 | 286.4 | 0.47 | 0.52 | -453.1 [-964.3, 58.2] | -1.7 | 3 | -65.9 | -890.7 |
| U7/1 | fl_bimb5300s_with | 0.58 | 30.4 | 276.9 | 0.48 | 0.54 | -246.6 [-722.0, 228.8] | -1.0 | 3 | -383.9 | -422.6 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_C2_flow_named.parquet

### C2 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 72 conditions; 2845 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 17 conditions with |t|>2 (chance alone: about 3). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | fl_bimb5300s_with | 0.51 | 1.6 | 3.5 | 0.48 | 0.50 | -2.0 [-2.9, -1.0] | -4.0 | 4 | -2.7 | -3.5 |
| ALL/ALL | fl_bimb105s_with | 0.47 | 1.6 | 3.4 | 0.48 | 0.50 | -1.8 [-2.8, -0.8] | -3.6 | 4 | -1.9 | -0.2 |
| ALL/ALL | fl_bimb1060s_with | 0.44 | 1.6 | 3.3 | 0.48 | 0.50 | -1.7 [-2.7, -0.8] | -3.5 | 4 | -2.5 | -1.6 |
| ALL/ALL | fl_size60_up | 0.02 | 7.6 | 2.4 | 0.54 | 0.49 | 5.2 [2.0, 8.4] | 3.2 | 4 | 4.5 | 1.1 |
| ALL/ALL | fl_bimb10300s_with | 0.48 | 1.8 | 3.2 | 0.48 | 0.49 | -1.5 [-2.4, -0.5] | -3.0 | 4 | -1.5 | -1.9 |
| ALL/ALL | fl_bimb560s_with | 0.47 | 1.7 | 3.2 | 0.48 | 0.49 | -1.5 [-2.4, -0.5] | -2.9 | 3 | -1.5 | -1.5 |
| ALL/ALL | fl_bimb1300s_strong | 0.01 | -3.7 | 2.6 | 0.44 | 0.49 | -6.3 [-10.7, -1.9] | -2.8 | 3 | -1.4 | 1.1 |
| ALL/ALL | fl_mic60s_with | 0.49 | 1.8 | 3.2 | 0.48 | 0.49 | -1.4 [-2.3, -0.4] | -2.7 | 4 | -1.0 | -2.3 |
| ALL/ALL | fl_ofi5s_strong | 0.32 | 3.3 | 1.8 | 0.49 | 0.48 | 1.5 [0.3, 2.6] | 2.6 | 4 | 1.7 | 2.0 |
| ALL/ALL | fl_bimb101s_with | 0.45 | 1.8 | 3.1 | 0.48 | 0.49 | -1.3 [-2.2, -0.3] | -2.5 | 4 | -1.0 | -1.2 |
| ALL/ALL | fl_bimb55s_with | 0.50 | 1.9 | 3.1 | 0.48 | 0.49 | -1.2 [-2.2, -0.3] | -2.5 | 3 | -1.3 | -1.4 |
| ALL/ALL | fl_bimb515s_with | 0.49 | 1.9 | 3.1 | 0.48 | 0.49 | -1.2 [-2.2, -0.2] | -2.4 | 3 | -0.9 | -0.2 |
| ALL/ALL | fl_size300_up | 0.00 | 10.7 | 2.5 | 0.58 | 0.49 | 8.2 [1.3, 15.1] | 2.3 | 4 | 12.5 | 28.0 |
| ALL/ALL | fl_bimb160s_with | 0.49 | 2.0 | 3.0 | 0.48 | 0.49 | -1.1 [-2.0, -0.1] | -2.1 | 4 | -0.5 | -1.3 |
| ALL/ALL | fl_bigshare300_up | 0.24 | 3.5 | 2.3 | 0.50 | 0.48 | 1.3 [0.1, 2.5] | 2.1 | 4 | 1.4 | 0.0 |
| ALL/ALL | fl_bimb51s_with | 0.46 | 2.0 | 3.0 | 0.48 | 0.49 | -1.0 [-2.0, -0.1] | -2.1 | 3 | -0.5 | -2.0 |
| ALL/ALL | fl_ofi1s_strong | 0.38 | 3.2 | 1.9 | 0.49 | 0.47 | 1.3 [0.0, 2.7] | 2.0 | 4 | 2.2 | 0.8 |
| ALL/ALL | fl_bimb11s_strong | 0.26 | 1.7 | 2.8 | 0.48 | 0.49 | -1.1 [-2.2, 0.0] | -1.9 | 3 | -2.3 | -2.1 |
| ALL/ALL | fl_bimb10300s_strong | 0.04 | 0.3 | 2.6 | 0.47 | 0.49 | -2.3 [-4.7, 0.1] | -1.9 | 4 | -1.8 | 1.9 |
| ALL/ALL | fl_bimb1015s_with | 0.47 | 2.1 | 2.9 | 0.48 | 0.49 | -0.9 [-1.8, 0.1] | -1.7 | 4 | -1.0 | -0.8 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_C2_flow_named.parquet

## Sub-block D: realized vs implied vol, VIX term structure, megacap dispersion / breadth

### D - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 32 conditions; 755 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 7 conditions with |t|>2 (chance alone: about 1). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | sd_rviv30_lt50 | 0.50 | 165.6 | 47.2 | 0.45 | 0.42 | 118.5 [56.6, 180.4] | 3.8 | 4 | 205.0 | 121.5 |
| ALL/ALL | sd_rviv60_lt50 | 0.49 | 158.3 | 54.7 | 0.46 | 0.42 | 103.6 [41.6, 165.5] | 3.3 | 4 | 137.4 | 229.4 |
| ALL/ALL | sd_rviv30_gt1 | 0.16 | 27.5 | 120.3 | 0.42 | 0.44 | -92.8 [-159.6, -26.1] | -2.7 | 3 | -62.1 | -56.4 |
| ALL/ALL | sd_rviv30_gt15 | 0.04 | -48.0 | 112.3 | 0.40 | 0.44 | -160.3 [-279.2, -41.4] | -2.6 | 4 | -103.0 | -72.0 |
| ALL/ALL | sd_rviv60_gt1 | 0.15 | 30.3 | 119.6 | 0.42 | 0.44 | -89.3 [-158.2, -20.4] | -2.5 | 4 | -64.4 | -4.5 |
| ALL/ALL | sd_mean5_with | 0.78 | 31.4 | 167.5 | 0.42 | 0.44 | -136.1 [-264.5, -7.7] | -2.1 | 3 | -197.9 | -347.2 |
| ALL/ALL | sd_rviv240_gt15 | 0.01 | 442.8 | 101.3 | 0.54 | 0.44 | 341.5 [17.0, 666.0] | 2.1 | 3 | 478.9 | 595.0 |
| ALL/ALL | sd_rviv60_gt15 | 0.04 | 26.6 | 108.8 | 0.41 | 0.44 | -82.2 [-221.1, 56.7] | -1.2 | 3 | -34.7 | 58.3 |
| ALL/ALL | sd_rviv240_gt1 | 0.09 | 154.0 | 100.8 | 0.46 | 0.44 | 53.2 [-46.8, 153.3] | 1.0 | 3 | 95.1 | 123.3 |
| ALL/ALL | sd_rviv240_lt50 | 0.47 | 122.3 | 91.2 | 0.44 | 0.43 | 31.1 [-31.2, 93.5] | 1.0 | 3 | 62.8 | 238.2 |
| ALL/ALL | sd_vvix_vix_hi | 0.17 | 133.8 | 100.1 | 0.46 | 0.43 | 33.7 [-50.2, 117.7] | 0.8 | 3 | 529.6 | 583.8 |
| ALL/ALL | sd_mean15_with | 0.80 | 40.9 | 77.3 | 0.42 | 0.41 | -36.4 [-172.8, 99.9] | -0.5 | 3 | -19.0 | 12.4 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | sd_vix_fall5d_with | 0.51 | 88.8 | 142.6 | 0.51 | 0.53 | -53.9 [-185.1, 77.4] | -0.8 | 3 | -124.3 | -194.0 |
| A7/0 | sd_vix_low | 0.24 | 151.9 | 103.3 | 0.55 | 0.51 | 48.6 [-106.2, 203.3] | 0.6 | 3 | 112.0 | 209.5 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | sd_vix_fall1d_with | 0.61 | 213.7 | 219.1 | 0.49 | 0.47 | -5.3 [-391.6, 381.0] | -0.0 | 3 | -108.0 | -73.7 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | sd_breadth5_ge5 | 0.55 | 268.9 | -36.3 | 0.59 | 0.42 | 305.1 [-18.0, 628.3] | 1.9 | 3 | 513.4 | 471.2 |
| H7/3 | sd_vix9d_inverted | 0.78 | 75.2 | -76.8 | 0.49 | 0.43 | 152.0 [-134.2, 438.2] | 1.0 | 3 | 28.9 | 1376.9 |
| H7/3 | sd_rviv60_gt1 | 0.52 | 9.1 | 78.6 | 0.47 | 0.49 | -69.6 [-302.9, 163.8] | -0.6 | 3 | -588.7 | -509.8 |
| H7/3 | sd_vix_fall5d_with | 0.52 | 32.5 | 53.3 | 0.48 | 0.48 | -20.8 [-254.5, 212.8] | -0.2 | 3 | -164.4 | 85.2 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | sd_vix_fall5d_with | 0.50 | 140.7 | 37.2 | 0.46 | 0.42 | 103.5 [3.1, 203.8] | 2.0 | 4 | 37.0 | 103.9 |
| K7/0 | sd_breadth15_ge5 | 0.57 | -58.9 | 151.6 | 0.40 | 0.47 | -210.5 [-440.8, 19.7] | -1.8 | 3 | -210.1 | 95.1 |
| K7/0 | sd_rviv240_gt1 | 0.09 | 191.4 | 79.1 | 0.48 | 0.44 | 112.3 [-65.4, 290.0] | 1.2 | 4 | 78.5 | 280.5 |
| K7/0 | sd_vix_contango | 0.76 | 79.3 | 119.3 | 0.44 | 0.45 | -40.1 [-157.5, 77.3] | -0.7 | 4 | -204.9 | -817.6 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | sd_vix_fall1d_with | 0.50 | 18.9 | 52.0 | 0.42 | 0.43 | -33.0 [-149.8, 83.8] | -0.6 | 3 | -109.8 | -47.5 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | sd_mean15_with | 0.88 | 14.5 | -135.8 | 0.42 | 0.38 | 150.3 [-53.6, 354.3] | 1.4 | 3 | 183.5 | 365.7 |
| K7/3 | sd_breadth60_le2 | 0.10 | -133.3 | 10.2 | 0.34 | 0.42 | -143.5 [-354.0, 67.0] | -1.3 | 3 | -172.0 | -57.2 |
| K7/3 | sd_rviv60_gt15 | 0.12 | -72.2 | 21.2 | 0.37 | 0.43 | -93.4 [-242.9, 56.0] | -1.2 | 4 | -43.8 | -118.4 |
| K7/3 | sd_vix_fall5d_with | 0.50 | -18.8 | 38.7 | 0.42 | 0.43 | -57.5 [-157.7, 42.6] | -1.1 | 3 | -145.8 | -137.9 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | sd_disp60_lo | 0.22 | 234.2 | 21.6 | 0.55 | 0.43 | 212.6 [-14.4, 439.6] | 1.8 | 3 | 242.9 | 128.7 |
| K7/4 | sd_rviv30_gt15 | 0.05 | 336.4 | 47.7 | 0.55 | 0.45 | 288.7 [-64.3, 641.7] | 1.6 | 3 | 142.1 | -1105.0 |
| K7/4 | sd_breadth60_ge5 | 0.68 | 105.4 | -13.4 | 0.48 | 0.43 | 118.8 [-72.3, 309.9] | 1.2 | 3 | 281.7 | 345.7 |
| K7/4 | sd_rviv60_gt1 | 0.17 | 137.4 | 46.9 | 0.46 | 0.46 | 90.6 [-102.6, 283.7] | 0.9 | 3 | 204.6 | -1327.7 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | sd_rviv60_lt50 | 0.73 | 68.2 | -196.3 | 0.43 | 0.33 | 264.5 [145.2, 383.9] | 4.3 | 4 | 280.5 | 455.0 |
| M7/1 | sd_rviv30_lt50 | 0.71 | 45.5 | -123.9 | 0.43 | 0.35 | 169.4 [51.7, 287.0] | 2.8 | 4 | 122.7 | 93.7 |
| M7/1 | sd_vvix_vix_hi | 0.15 | 177.5 | -35.8 | 0.48 | 0.39 | 213.4 [62.5, 364.3] | 2.8 | 4 | 412.3 | 438.2 |
| M7/1 | sd_rviv240_lt50 | 0.80 | 32.4 | -140.7 | 0.42 | 0.34 | 173.1 [45.6, 300.5] | 2.7 | 4 | 110.5 | 194.3 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | sd_rviv30_gt15 | 0.16 | -64.1 | 60.0 | 0.37 | 0.45 | -124.1 [-260.4, 12.2] | -1.8 | 3 | -309.0 | -361.7 |
| M7/3 | sd_rviv240_gt1 | 0.21 | 116.1 | 19.8 | 0.46 | 0.43 | 96.3 [-28.2, 220.9] | 1.5 | 3 | 30.4 | 71.4 |
| M7/3 | sd_breadth5_ge5 | 0.62 | 31.7 | 129.0 | 0.42 | 0.47 | -97.3 [-235.4, 40.9] | -1.4 | 3 | -67.0 | 49.1 |
| M7/3 | sd_rviv30_gt1 | 0.52 | 13.0 | 69.6 | 0.42 | 0.46 | -56.6 [-160.1, 47.0] | -1.1 | 3 | -90.7 | -47.6 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | sd_vix9d_inverted | 0.82 | 225.2 | -52.4 | 0.40 | 0.28 | 277.5 [17.1, 538.0] | 2.1 | 3 | 1049.3 | 803.9 |
| O7/3 | sd_rviv30_gt1 | 0.53 | 170.1 | 182.9 | 0.38 | 0.37 | -12.8 [-225.8, 200.3] | -0.1 | 3 | -166.0 | 796.9 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | sd_vvix_vix_hi | 0.14 | 873.1 | 348.9 | 0.49 | 0.43 | 524.2 [-87.4, 1135.8] | 1.7 | 3 | 3140.6 | 3423.4 |
| P7/0 | sd_vix_low | 0.21 | 658.7 | 360.5 | 0.47 | 0.43 | 298.2 [-198.5, 794.9] | 1.2 | 3 | 432.4 | 784.0 |
| P7/0 | sd_vix_fall1d_with | 0.52 | 534.9 | 301.2 | 0.46 | 0.42 | 233.7 [-157.2, 624.6] | 1.2 | 3 | 324.6 | 94.3 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | sd_rviv240_lt50 | 0.76 | 92.1 | -145.7 | 0.39 | 0.34 | 237.8 [-15.6, 491.1] | 1.8 | 3 | 232.2 | 688.1 |
| P7/1 | sd_vvix_vix_hi | 0.13 | -200.8 | 70.4 | 0.33 | 0.39 | -271.2 [-615.3, 72.8] | -1.5 | 3 | -506.9 | -645.5 |
| P7/1 | sd_rviv30_lt50 | 0.68 | 88.4 | -81.4 | 0.40 | 0.35 | 169.9 [-71.3, 411.1] | 1.4 | 3 | 15.7 | -27.0 |
| P7/1 | sd_vix9d_inverted | 0.75 | 77.0 | -96.8 | 0.39 | 0.35 | 173.8 [-89.5, 437.1] | 1.3 | 3 | 562.3 | 1177.8 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | sd_disp60_hi | 0.57 | 189.8 | -281.8 | 0.45 | 0.30 | 471.6 [106.7, 836.4] | 2.5 | 3 | 279.6 | 504.7 |
| P7/3 | sd_vix_fall1d_with | 0.51 | 69.1 | -139.8 | 0.41 | 0.37 | 208.9 [-50.4, 468.3] | 1.6 | 4 | 233.1 | 760.3 |
| P7/3 | sd_rviv60_gt1 | 0.49 | -93.8 | 24.9 | 0.39 | 0.39 | -118.7 [-378.8, 141.4] | -0.9 | 3 | -476.1 | -173.8 |
| P7/3 | sd_rviv30_gt1 | 0.45 | -89.6 | 13.1 | 0.39 | 0.39 | -102.6 [-364.3, 159.0] | -0.8 | 3 | -319.9 | -370.9 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | sd_vix_fall1d_with | 0.39 | 485.6 | 320.1 | 0.55 | 0.51 | 165.5 [-358.0, 689.0] | 0.6 | 3 | 475.2 | 502.0 |
| U7/0 | sd_vix9d_inverted | 0.79 | 369.5 | 445.0 | 0.52 | 0.56 | -75.5 [-718.5, 567.4] | -0.2 | 3 | -219.2 | -2538.7 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | sd_rviv30_lt50 | 0.72 | 258.1 | -179.4 | 0.53 | 0.44 | 437.5 [-73.9, 948.9] | 1.7 | 4 | 112.3 | 70.2 |
| U7/1 | sd_vix_fall5d_with | 0.49 | 203.1 | 68.4 | 0.52 | 0.49 | 134.6 [-341.3, 610.6] | 0.6 | 3 | 76.9 | -801.9 |
| U7/1 | sd_rviv240_lt50 | 0.85 | 152.9 | 29.4 | 0.51 | 0.45 | 123.5 [-522.5, 769.5] | 0.4 | 3 | 15.0 | 1460.3 |
| U7/1 | sd_vix_low | 0.24 | 176.3 | 120.3 | 0.52 | 0.50 | 56.0 [-497.2, 609.2] | 0.2 | 3 | 373.8 | -148.0 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_D_statext_named.parquet

### D - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 32 conditions; 1295 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 12 conditions with |t|>2 (chance alone: about 1). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | sd_vvix_vix_hi | 0.15 | 7.0 | 1.7 | 0.52 | 0.48 | 5.3 [4.1, 6.6] | 8.4 | 4 | 20.1 | 20.5 |
| ALL/ALL | sd_vix9d_inverted | 0.84 | 3.2 | -1.0 | 0.49 | 0.44 | 4.2 [2.9, 5.5] | 6.2 | 3 | 7.8 | 3.2 |
| ALL/ALL | sd_rviv240_gt15 | 0.02 | 12.4 | 2.3 | 0.59 | 0.48 | 10.1 [6.3, 13.8] | 5.3 | 4 | 13.9 | 24.9 |
| ALL/ALL | sd_rviv240_lt50 | 0.49 | 3.5 | 1.5 | 0.50 | 0.48 | 2.0 [1.1, 3.0] | 4.2 | 3 | 3.3 | 7.9 |
| ALL/ALL | sd_rviv60_lt50 | 0.54 | 3.3 | 1.6 | 0.50 | 0.47 | 1.7 [0.7, 2.7] | 3.4 | 4 | 1.6 | 4.9 |
| ALL/ALL | sd_disp60_hi | 0.25 | 3.3 | 0.2 | 0.49 | 0.48 | 3.1 [1.3, 4.9] | 3.4 | 3 | 4.0 | 1.4 |
| ALL/ALL | sd_rviv30_lt50 | 0.55 | 3.2 | 1.6 | 0.50 | 0.47 | 1.6 [0.6, 2.6] | 3.3 | 3 | 1.7 | 4.2 |
| ALL/ALL | sd_rviv60_gt15 | 0.03 | -1.4 | 2.6 | 0.44 | 0.49 | -4.0 [-6.9, -1.2] | -2.8 | 3 | -0.8 | 9.3 |
| ALL/ALL | sd_disp15_hi | 0.24 | 2.1 | 0.4 | 0.48 | 0.48 | 1.8 [-0.0, 3.5] | 1.9 | 3 | 1.7 | -0.7 |
| ALL/ALL | sd_disp5_lo | 0.24 | -0.4 | 1.2 | 0.47 | 0.48 | -1.6 [-3.3, 0.1] | -1.8 | 3 | -0.6 | -1.5 |
| ALL/ALL | sd_vix_contango | 0.87 | 2.7 | 1.4 | 0.49 | 0.45 | 1.2 [-0.2, 2.6] | 1.7 | 3 | 6.2 | 6.1 |
| ALL/ALL | sd_breadth60_ge5 | 0.57 | 0.5 | 1.6 | 0.48 | 0.49 | -1.2 [-2.7, 0.4] | -1.5 | 3 | -2.5 | -4.2 |
| ALL/ALL | sd_breadth5_ge5 | 0.49 | 0.3 | 1.3 | 0.47 | 0.49 | -1.1 [-2.6, 0.4] | -1.4 | 3 | -0.8 | -1.1 |
| ALL/ALL | sd_breadth60_le2 | 0.12 | 2.4 | 0.8 | 0.50 | 0.48 | 1.6 [-0.7, 4.0] | 1.3 | 3 | 3.9 | 4.4 |
| ALL/ALL | sd_vix_high | 0.14 | 2.9 | 2.4 | 0.46 | 0.49 | 0.4 [-0.9, 1.8] | 0.6 | 3 | 0.8 | -6.8 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_D_statext_named.parquet
