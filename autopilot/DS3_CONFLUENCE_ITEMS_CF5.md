**NOTE (2026-11-15): this page is the PRE-EXTENSION version (universe to 2026-10-30, plain Welch tables). The current each-alone verdicts with the cluster-robust zw and the nonsense bar are in DS3_CONFLUENCE_ITEMS_CF5_ZW.md (data to 2026-11-13, November provisional).** PRE-EXTENSION

# DS3_CONFLUENCE_ITEMS_CF5 - Block 3 (desk / named-trader systems), STEP 3 each alone

**Verdict line (updated 2026-11-15 17:15Z): sub-blocks A, B, B2, C1, C2, D and Addendum-6 Blocks 7, 8, 9, 13 and 16 are built and scored each alone (4847 conditions); no item is claimed as a finding, the tables are the map (flow measures at our entries are mostly null, like the earlier MBO screen).**

Signal universe = W-CF1 entry table signals_all.parquet (sig_id = book7_sig_ts); causality checked by truncated-history recompute for A and B.

## Sub-block A: named-system indicators on HTF bars (DeMark, Raschke, Connors, Chande, Wilder, Kase, Ehlers, Brooks, statistical desk measures)

### A - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 3965 conditions; 98292 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 544 conditions with |t|>2 (chance alone: about 198). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | wl_volstop_flip_fast_1d_against10 | 0.32 | 3.0 | 155.1 | 0.42 | 0.45 | -152.1 [-217.0, -87.1] | -98.8 | -4.6 | 4 | -82.9 | -212.9 |
| ALL/ALL | cn_double7_fast_3m_against10 | 0.31 | 14.3 | 146.7 | 0.42 | 0.44 | -132.3 [-192.3, -72.3] | -90.6 | -4.3 | 4 | -134.6 | -285.3 |
| ALL/ALL | rk_soup_fast_3m_state | 0.29 | 1.9 | 148.5 | 0.41 | 0.45 | -146.6 [-213.3, -79.8] | -93.4 | -4.3 | 4 | -179.6 | -140.1 |
| ALL/ALL | wl_volstop_dist_std_5m_side | 0.80 | 135.0 | -10.9 | 0.44 | 0.41 | 145.9 [79.3, 212.5] | 93.1 | 4.3 | 4 | 79.1 | 163.5 |
| ALL/ALL | eh_ebsw_slow_5m_side | 0.75 | 138.7 | 7.8 | 0.44 | 0.42 | 130.9 [70.4, 191.3] | 89.2 | 4.2 | 4 | 194.3 | 378.9 |
| ALL/ALL | wl_volstop_std_5m_side | 0.80 | 134.6 | -8.6 | 0.44 | 0.41 | 143.2 [76.9, 209.6] | 91.7 | 4.2 | 4 | 71.9 | 139.1 |
| ALL/ALL | cn_double7_1m_against_state | 0.26 | 11.4 | 138.5 | 0.42 | 0.44 | -127.2 [-188.0, -66.3] | -86.3 | -4.1 | 4 | -131.1 | -293.7 |
| ALL/ALL | ch_fosc_fast_1d_fresh5 | 0.46 | 175.9 | 46.9 | 0.45 | 0.42 | 129.0 [66.9, 191.1] | 86.4 | 4.1 | 4 | 157.7 | 146.1 |
| ALL/ALL | rk_grail_slow_60m_against_state | 0.12 | -61.2 | 129.6 | 0.40 | 0.44 | -190.8 [-283.7, -97.9] | -90.8 | -4.0 | 4 | -4.3 | -241.1 |
| ALL/ALL | eh_ebsw_fast_15m_side | 0.71 | 141.1 | 20.0 | 0.44 | 0.42 | 121.2 [62.0, 180.3] | 83.8 | 4.0 | 4 | 169.4 | 284.9 |
| ALL/ALL | eh_ebsw_fast_15m_ewith | 0.55 | 161.9 | 38.1 | 0.45 | 0.43 | 123.8 [63.3, 184.3] | 84.4 | 4.0 | 4 | 89.9 | 96.0 |
| ALL/ALL | st_amihud_3m_hi | 0.46 | 175.8 | 46.5 | 0.45 | 0.43 | 129.3 [65.0, 193.6] | 84.6 | 3.9 | 4 | 45.7 | 16.9 |
| ALL/ALL | rk_8020_slow_60m_with10 | 0.11 | -64.3 | 127.9 | 0.40 | 0.44 | -192.3 [-288.7, -95.8] | -87.9 | -3.9 | 3 | -308.5 | -201.6 |
| ALL/ALL | eh_ebsw_std_15m_eagainst | 0.27 | 17.6 | 138.2 | 0.42 | 0.44 | -120.6 [-181.3, -59.9] | -82.0 | -3.9 | 3 | -178.7 | -268.1 |
| ALL/ALL | rk_310_std_15m_side | 0.71 | 139.5 | 21.6 | 0.44 | 0.42 | 117.8 [58.5, 177.2] | 81.2 | 3.9 | 4 | 179.8 | 325.9 |
| ALL/ALL | eh_ss20_15m_side | 0.81 | 132.4 | -6.2 | 0.44 | 0.41 | 138.6 [68.3, 208.8] | 85.0 | 3.9 | 4 | 100.0 | 298.0 |
| ALL/ALL | ks_devstop2_5m_side | 0.81 | 130.5 | 2.9 | 0.44 | 0.41 | 127.6 [62.5, 192.8] | 82.7 | 3.8 | 4 | 125.6 | 359.3 |
| ALL/ALL | ch_dmi_1m_eleave | 0.01 | 885.5 | 100.4 | 0.59 | 0.44 | 785.2 [384.2, 1186.2] | 36.4 | 3.8 | 4 | 453.8 | 74.1 |
| ALL/ALL | st_zma200_1m_fresh5 | 0.10 | -22.8 | 120.6 | 0.41 | 0.44 | -143.4 [-216.9, -69.8] | -84.8 | -3.8 | 4 | -132.0 | -154.3 |
| ALL/ALL | ks_peak25_5m_side | 0.82 | 130.0 | -1.0 | 0.44 | 0.42 | 131.1 [63.4, 198.7] | 82.7 | 3.8 | 4 | 140.7 | 256.7 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | cn_double7_fast_3m_against10 | 0.30 | 23.5 | 321.3 | 0.43 | 0.48 | -297.8 [-432.8, -162.9] | -188.1 | -2.7 | 4 | -185.1 | -443.8 |
| ALL/0 | eh_ebsw_slow_5m_side | 0.76 | 300.4 | 11.4 | 0.48 | 0.43 | 289.0 [151.0, 426.9] | 179.5 | 2.5 | 4 | 272.3 | 545.1 |
| ALL/0 | eh_ebsw_fast_15m_side | 0.72 | 306.0 | 39.3 | 0.48 | 0.44 | 266.7 [134.0, 399.4] | 170.5 | 2.5 | 4 | 205.9 | 387.3 |
| ALL/0 | rk_310_std_15m_side | 0.72 | 304.3 | 42.9 | 0.48 | 0.44 | 261.4 [128.1, 394.7] | 166.5 | 2.4 | 4 | 191.1 | 377.4 |
| ALL/0 | eh_ebsw_slow_5m_ewith | 0.71 | 304.3 | 54.4 | 0.48 | 0.44 | 249.9 [115.4, 384.4] | 158.2 | 2.3 | 4 | 235.7 | 396.5 |
| ALL/0 | wl_volstop_dist_std_5m_side | 0.80 | 294.2 | -11.5 | 0.48 | 0.42 | 305.7 [153.0, 458.3] | 175.0 | 2.2 | 4 | 55.4 | 139.4 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | eh_ss6_60m_nodiv | 0.79 | 82.6 | -162.1 | 0.43 | 0.37 | 244.8 [139.5, 350.0] | 128.8 | 2.4 | 4 | 297.3 | 334.8 |
| ALL/1 | wl_volstop_flip_fast_1d_against10 | 0.31 | -103.7 | 91.7 | 0.37 | 0.43 | -195.4 [-288.8, -102.0] | -114.3 | -2.4 | 4 | -208.1 | -268.2 |
| ALL/1 | st_nqlag_es60_1d_rise | 0.49 | -56.8 | 117.0 | 0.39 | 0.44 | -173.8 [-263.5, -84.2] | -105.1 | -2.3 | 4 | -238.5 | -202.4 |
| ALL/1 | cn_rsi2_fast_60m_nodiv | 0.84 | 75.0 | -198.1 | 0.42 | 0.37 | 273.1 [158.7, 387.6] | 132.3 | 2.3 | 4 | 286.7 | 565.1 |
| ALL/1 | cn_rsi2_std_60m_nodiv | 0.84 | 75.0 | -198.1 | 0.42 | 0.37 | 273.1 [158.7, 387.6] | 132.3 | 2.3 | 4 | 286.7 | 565.1 |
| ALL/1 | ch_fosc_std_60m_nodiv | 0.77 | 77.0 | -124.5 | 0.42 | 0.39 | 201.5 [99.2, 303.8] | 108.9 | 2.1 | 4 | 202.3 | 291.7 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | wl_volstop_dist_std_60m_ewith | 0.34 | -80.3 | 82.9 | 0.38 | 0.44 | -163.2 [-243.7, -82.8] | -92.7 | -2.3 | 4 | -104.6 | -140.9 |
| ALL/3 | rk_8020_std_60m_with10 | 0.36 | -63.7 | 79.0 | 0.39 | 0.44 | -142.7 [-221.4, -64.0] | -82.6 | -2.1 | 4 | -108.9 | -194.8 |
| ALL/3 | wl_volstop_flip_std_1d_state | 0.35 | 122.6 | -23.2 | 0.45 | 0.40 | 145.8 [65.8, 225.8] | 83.2 | 2.0 | 4 | 101.9 | -130.7 |
| ALL/3 | bk_h1h2_1m_with3 | 0.44 | 101.2 | -30.8 | 0.44 | 0.40 | 132.0 [55.4, 208.5] | 78.1 | 2.0 | 4 | 158.6 | 132.8 |
| ALL/3 | rk_8020_fast_60m_state | 0.49 | -37.6 | 90.2 | 0.40 | 0.44 | -127.8 [-203.6, -52.0] | -76.3 | -2.0 | 4 | -85.8 | -88.6 |
| ALL/3 | bk_failbo_slow_60m_state | 0.32 | -66.7 | 71.4 | 0.39 | 0.43 | -138.0 [-218.2, -57.9] | -78.7 | -1.9 | 4 | -49.2 | -148.9 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | st_corr_es_3m_hi_z1 | 0.37 | -101.7 | 157.5 | 0.39 | 0.50 | -259.2 [-402.1, -116.3] | -12.2 | -0.2 | 4 | -226.5 | -1293.3 |
| ALL/4 | cn_double7_slow_1d_against_state | 0.41 | -75.0 | 158.2 | 0.39 | 0.51 | -233.2 [-377.1, -89.3] | -10.8 | -0.1 | 4 | -418.2 | -714.6 |
| ALL/4 | st_corr_es_1m_hi_z1 | 0.44 | -62.5 | 159.0 | 0.41 | 0.50 | -221.5 [-363.3, -79.7] | -10.6 | -0.1 | 4 | -231.2 | -906.1 |
| ALL/4 | rk_anti_15m_with10 | 0.47 | 175.3 | -39.0 | 0.49 | 0.43 | 214.3 [72.1, 356.4] | 10.2 | 0.1 | 4 | 504.9 | 662.3 |
| ALL/4 | wl_volstop_flip_fast_60m_against_state | 0.45 | -47.3 | 151.2 | 0.41 | 0.49 | -198.5 [-339.0, -58.0] | -9.7 | -0.1 | 4 | -300.4 | -582.6 |
| ALL/4 | ch_fosc_slow_1d_sig | 0.51 | 157.8 | -37.0 | 0.50 | 0.42 | 194.7 [53.3, 336.2] | 9.3 | 0.1 | 4 | 244.8 | 254.7 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | ch_fosc_slow_3m_nodiv | 0.71 | 38.8 | 302.4 | 0.49 | 0.60 | -263.6 [-406.1, -121.1] | -0.0 | -3.6 | 4 | -297.5 | -275.8 |
| A7/0 | eh_mama_std_60m_nodiv | 0.85 | 69.1 | 374.1 | 0.50 | 0.64 | -305.0 [-483.4, -126.6] | -0.0 | -3.4 | 4 | -39.3 | 245.5 |
| A7/0 | ks_peak14_3m_fresh5 | 0.21 | -99.2 | 171.7 | 0.43 | 0.55 | -270.9 [-431.2, -110.5] | -0.0 | -3.3 | 4 | -21.5 | -51.5 |
| A7/0 | wl_volstop_dist_fast_5m_fresh5 | 0.16 | -121.9 | 160.4 | 0.41 | 0.54 | -282.4 [-459.3, -105.5] | -0.0 | -3.1 | 4 | -178.9 | -203.7 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | dm_flip_1d_against3 | 0.22 | 764.3 | 58.5 | 0.59 | 0.45 | 705.8 [267.0, 1144.6] | 0.0 | 3.2 | 4 | 296.1 | 318.2 |
| H7/0 | rk_310h_std_agree4of4 | 0.12 | -568.6 | 322.7 | 0.35 | 0.50 | -891.3 [-1446.6, -336.1] | -0.0 | -3.1 | 4 | -383.5 | -1.0 |
| H7/0 | rk_8020_fast_1d_against10 | 0.71 | 386.9 | -212.1 | 0.51 | 0.41 | 599.1 [187.9, 1010.2] | 0.0 | 2.9 | 4 | 127.6 | 298.0 |
| H7/0 | eh_ebsw_std_15m_nodiv | 0.85 | 324.8 | -423.3 | 0.49 | 0.39 | 748.0 [230.2, 1265.9] | 0.0 | 2.8 | 4 | 506.2 | 405.0 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | cn_rsi2_fast_3m_nodiv | 0.80 | -63.1 | 454.5 | 0.43 | 0.66 | -517.6 [-792.6, -242.6] | -79.0 | -3.7 | 4 | -417.9 | -1443.8 |
| H7/3 | cn_rsi2_std_3m_nodiv | 0.80 | -63.1 | 454.5 | 0.43 | 0.66 | -517.6 [-792.6, -242.6] | -79.0 | -3.7 | 4 | -417.9 | -1443.8 |
| H7/3 | wl_volstop_dist_std_3m_nodiv | 0.85 | -42.1 | 513.2 | 0.44 | 0.68 | -555.4 [-858.9, -251.9] | -71.5 | -3.6 | 4 | -240.4 | -673.9 |
| H7/3 | eh_cyber_fast_1m_side | 0.51 | 244.7 | -171.7 | 0.58 | 0.38 | 416.4 [187.1, 645.7] | 85.7 | 3.6 | 4 | 328.1 | 428.3 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | wl_volstop_dist_slow_15m_fresh5 | 0.09 | 473.0 | 50.5 | 0.57 | 0.43 | 422.5 [221.0, 624.0] | 86.1 | 4.1 | 4 | 249.3 | 276.4 |
| K7/0 | eh_cyber_fast_15m_ewith | 0.14 | 381.4 | 41.5 | 0.54 | 0.43 | 339.9 [168.8, 510.9] | 89.0 | 3.9 | 4 | 120.2 | 146.8 |
| K7/0 | rk_8020_slow_5m_state | 0.28 | -59.2 | 145.4 | 0.38 | 0.47 | -204.6 [-312.2, -96.9] | -96.6 | -3.7 | 4 | -257.1 | -255.0 |
| K7/0 | rk_grail_std_60m_against10 | 0.13 | -140.4 | 122.1 | 0.36 | 0.46 | -262.6 [-405.3, -119.8] | -88.6 | -3.6 | 4 | -203.3 | -357.5 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | rk_soup_std_3m_against_state | 0.45 | 159.3 | -63.8 | 0.48 | 0.39 | 223.1 [104.9, 341.3] | 0.0 | 3.7 | 4 | 217.9 | 329.4 |
| K7/1 | rk_soup_std_5m_state | 0.27 | -118.3 | 92.0 | 0.36 | 0.45 | -210.2 [-332.3, -88.1] | -0.0 | -3.4 | 4 | -78.8 | -81.3 |
| K7/1 | dm_line_break_3m_with1 | 0.15 | -195.3 | 75.0 | 0.33 | 0.44 | -270.3 [-435.1, -105.4] | -0.0 | -3.2 | 4 | -480.2 | -647.1 |
| K7/1 | ch_fosc_slow_agree4of4 | 0.18 | 237.7 | -8.9 | 0.50 | 0.41 | 246.6 [93.3, 400.0] | 0.0 | 3.2 | 3 | 345.5 | 867.3 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | wl_volstop_dist_std_5m_fresh5 | 0.12 | 228.2 | -20.4 | 0.52 | 0.41 | 248.6 [96.4, 400.8] | 0.0 | 3.2 | 4 | 185.7 | 369.7 |
| K7/3 | rk_anti_5m_with3 | 0.27 | 141.5 | -38.4 | 0.49 | 0.40 | 179.9 [66.9, 292.9] | 0.0 | 3.1 | 4 | 168.1 | 192.2 |
| K7/3 | st_es_leads_1m_hi_z1 | 0.13 | 216.3 | -21.0 | 0.52 | 0.41 | 237.3 [87.4, 387.2] | 0.0 | 3.1 | 4 | 421.4 | 510.6 |
| K7/3 | rk_310_slow_5m_fresh5 | 0.17 | 183.1 | -26.3 | 0.51 | 0.41 | 209.3 [76.4, 342.3] | 0.0 | 3.1 | 4 | 181.6 | -46.8 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | st_corr_es_3m_hi_z1 | 0.37 | -101.7 | 157.5 | 0.39 | 0.50 | -259.2 [-402.1, -116.3] | -12.2 | -3.6 | 4 | -226.5 | -1293.3 |
| K7/4 | dm_flip_1d_against10 | 0.80 | -1.9 | 310.5 | 0.44 | 0.53 | -312.4 [-496.9, -127.8] | -9.0 | -3.3 | 3 | -466.6 | -335.1 |
| K7/4 | cn_double7_slow_1d_against_state | 0.41 | -75.0 | 158.2 | 0.39 | 0.51 | -233.2 [-377.1, -89.3] | -10.8 | -3.2 | 4 | -418.2 | -714.6 |
| K7/4 | st_zma200_15m_ewith | 0.28 | 252.7 | -11.6 | 0.52 | 0.43 | 264.3 [97.5, 431.0] | 9.2 | 3.1 | 4 | 522.2 | 1202.2 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | wl_volstop_flip_fast_1d_against10 | 0.33 | -149.5 | 68.3 | 0.34 | 0.43 | -217.9 [-327.9, -107.8] | -31.6 | -3.9 | 4 | -251.7 | -300.3 |
| M7/1 | dm_cd_1m_with_ge12 | 0.05 | -282.1 | 12.6 | 0.27 | 0.41 | -294.8 [-469.7, -119.8] | -18.6 | -3.3 | 4 | -231.5 | -396.1 |
| M7/1 | bk_trendbars5_1m_eleave | 0.10 | 279.2 | -35.6 | 0.50 | 0.39 | 314.8 [122.6, 507.0] | 16.6 | 3.2 | 4 | 360.9 | 485.0 |
| M7/1 | dm_cd_1m_with_ge13 | 0.04 | -312.6 | 9.8 | 0.26 | 0.41 | -322.4 [-522.2, -122.6] | -15.8 | -3.2 | 4 | -159.8 | -426.2 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | bk_h1h2_1m_with3 | 0.40 | 143.7 | -28.7 | 0.48 | 0.41 | 172.4 [67.4, 277.5] | 0.0 | 3.2 | 4 | 243.8 | 224.3 |
| M7/3 | st_zma20_5m_nodiv | 0.78 | 83.1 | -109.4 | 0.46 | 0.37 | 192.5 [70.6, 314.3] | 0.0 | 3.1 | 4 | 198.8 | 355.0 |
| M7/3 | rk_grail_std_3m_with10 | 0.16 | -136.7 | 74.3 | 0.35 | 0.45 | -210.9 [-348.2, -73.6] | -0.0 | -3.0 | 4 | -324.6 | 26.8 |
| M7/3 | eh_mamapx_slow_5m_nodiv | 0.81 | 77.2 | -119.5 | 0.45 | 0.36 | 196.7 [67.6, 325.7] | 0.0 | 3.0 | 4 | 197.2 | 308.1 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | eh_ss6_3m_fresh5 | 0.72 | 273.4 | -70.2 | 0.41 | 0.28 | 343.6 [123.7, 563.5] | 0.0 | 3.1 | 4 | 679.3 | 948.7 |
| O7/3 | rk_anti_3m_against_state | 0.35 | -38.3 | 291.3 | 0.29 | 0.42 | -329.6 [-542.4, -116.7] | -0.0 | -3.0 | 3 | -717.1 | -1017.4 |
| O7/3 | rk_310h_slow_agree3of4 | 0.53 | 321.0 | 13.5 | 0.44 | 0.31 | 307.5 [97.8, 517.3] | 0.0 | 2.9 | 4 | 136.7 | 1026.4 |
| O7/3 | rk_anti_3m_state | 0.64 | 279.2 | -8.5 | 0.41 | 0.30 | 287.6 [74.0, 501.3] | 0.0 | 2.6 | 3 | 717.1 | 1017.4 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | rk_soup_fast_3m_with3 | 0.05 | -864.0 | 492.9 | 0.29 | 0.45 | -1356.9 [-2140.2, -573.7] | -112.1 | -3.4 | 4 | -1367.8 | -870.3 |
| P7/0 | eh_roof_slow_60m_fresh5 | 0.12 | 1348.4 | 291.8 | 0.52 | 0.43 | 1056.6 [441.4, 1671.7] | 134.6 | 3.4 | 4 | 1649.2 | 2791.2 |
| P7/0 | rk_310h_fast_5m_fresh5 | 0.40 | 25.0 | 689.5 | 0.41 | 0.46 | -664.5 [-1057.6, -271.5] | -175.0 | -3.3 | 4 | -701.5 | -961.6 |
| P7/0 | eh_mamapx_slow_3m_side | 0.79 | 581.5 | -179.0 | 0.45 | 0.40 | 760.5 [300.8, 1220.1] | 157.6 | 3.2 | 4 | 735.6 | 1624.8 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | rk_8020_fast_5m_against10 | 0.69 | 157.3 | -239.6 | 0.41 | 0.33 | 397.0 [156.2, 637.7] | 0.0 | 3.2 | 4 | 439.1 | 650.2 |
| P7/1 | dm_demand_line_15m_nodiv | 0.91 | -78.4 | 939.2 | 0.35 | 0.61 | -1017.6 [-1654.6, -380.5] | -0.0 | -3.1 | 3 | -274.9 | 373.9 |
| P7/1 | ks_peak14_5m_divwith | 0.08 | 670.9 | -18.0 | 0.50 | 0.37 | 688.9 [256.9, 1120.9] | 0.0 | 3.1 | 4 | 140.9 | 32.0 |
| P7/1 | cn_rsi2_std_60m_nodiv | 0.84 | 105.7 | -336.4 | 0.39 | 0.32 | 442.1 [153.6, 730.7] | 0.0 | 3.0 | 4 | 356.1 | 548.3 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | rk_8020_fast_5m_against10 | 0.69 | -199.2 | 329.4 | 0.36 | 0.46 | -528.5 [-814.6, -242.5] | -28.9 | -3.6 | 4 | -498.8 | -41.7 |
| P7/3 | bk_h1h2_60m_with10 | 0.45 | 223.7 | -247.7 | 0.44 | 0.35 | 471.4 [209.4, 733.5] | 30.3 | 3.5 | 4 | 569.6 | 669.4 |
| P7/3 | cn_rsi2_std_1d_ewith | 0.13 | 591.1 | -124.9 | 0.48 | 0.38 | 716.1 [288.6, 1143.5] | 18.1 | 3.3 | 4 | 784.6 | 1094.4 |
| P7/3 | st_nqlag_es120_60m_divwith | 0.26 | -370.1 | 85.2 | 0.31 | 0.41 | -455.3 [-731.2, -179.4] | -26.6 | -3.2 | 4 | -377.9 | -506.3 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | cn_double7_slow_1d_with3 | 0.11 | 1528.4 | 247.0 | 0.69 | 0.51 | 1281.4 [571.9, 1990.8] | 0.0 | 3.5 | 4 | 1631.6 | 1361.0 |
| U7/0 | cn_double7_1d_with3 | 0.18 | 1288.7 | 185.9 | 0.67 | 0.50 | 1102.8 [489.7, 1716.0] | 0.0 | 3.5 | 4 | 1088.7 | 633.3 |
| U7/0 | eh_roof_slow_15m_sig | 0.88 | 516.0 | -564.9 | 0.55 | 0.34 | 1080.9 [455.6, 1706.2] | 0.0 | 3.4 | 3 | 574.0 | 830.9 |
| U7/0 | eh_roof_slow_15m_rise | 0.88 | 516.0 | -564.9 | 0.55 | 0.34 | 1080.9 [455.6, 1706.2] | 0.0 | 3.4 | 3 | 574.0 | 830.9 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | ch_fosc_std_60m_nodiv | 0.80 | 322.8 | -636.1 | 0.53 | 0.40 | 958.9 [370.1, 1547.7] | 0.0 | 3.2 | 4 | 928.4 | 1828.8 |
| U7/1 | eh_ss6_60m_nodiv | 0.82 | 313.5 | -676.1 | 0.53 | 0.38 | 989.5 [376.6, 1602.4] | 0.0 | 3.2 | 4 | 970.0 | 497.1 |
| U7/1 | bk_failbo_std_3m_state | 0.25 | -444.5 | 331.2 | 0.42 | 0.53 | -775.7 [-1280.8, -270.5] | -0.0 | -3.0 | 3 | -1137.6 | -1638.2 |
| U7/1 | eh_roof_slow_5m_fresh5 | 0.26 | -421.3 | 326.4 | 0.43 | 0.53 | -747.6 [-1243.0, -252.3] | -0.0 | -3.0 | 4 | -999.5 | -1096.6 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_A_named_hs.parquet

### A - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 4011 conditions; 187249 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 2079 conditions with |t|>2 (chance alone: about 200). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | st_zma200_15m_ewith | 0.26 | 4.4 | 0.3 | 0.53 | 0.49 | 4.1 [3.6, 4.6] | 3.9 | 15.5 | 4 | 4.5 | 8.3 |
| ALL/ALL | ch_fosc_fast_1d_fresh5 | 0.45 | 3.1 | -0.1 | 0.52 | 0.49 | 3.2 [2.8, 3.7] | 3.2 | 13.9 | 4 | 2.0 | 4.7 |
| ALL/ALL | eh_ebsw_slow_agree4of4 | 0.33 | 3.6 | 0.2 | 0.52 | 0.49 | 3.4 [2.9, 3.8] | 3.3 | 13.7 | 4 | 2.6 | 5.0 |
| ALL/ALL | eh_mama_slow_agree4of4 | 0.36 | 3.4 | 0.2 | 0.52 | 0.49 | 3.3 [2.8, 3.7] | 3.2 | 13.6 | 4 | 4.2 | 5.5 |
| ALL/ALL | eh_ebsw_slow_60m_side | 0.52 | 2.8 | -0.3 | 0.52 | 0.48 | 3.1 [2.7, 3.6] | 3.0 | 13.5 | 4 | 2.2 | 3.4 |
| ALL/ALL | st_nqlag_es60_60m_divwith | 0.26 | -1.2 | 2.3 | 0.48 | 0.51 | -3.4 [-4.0, -2.9] | -3.3 | -13.2 | 4 | -7.4 | -7.2 |
| ALL/ALL | rk_anti_60m_against_state | 0.43 | -0.4 | 2.7 | 0.48 | 0.52 | -3.0 [-3.5, -2.6] | -3.0 | -13.1 | 3 | -2.6 | 1.7 |
| ALL/ALL | st_zma50_agree4of4 | 0.48 | 2.9 | -0.1 | 0.52 | 0.49 | 3.0 [2.6, 3.5] | 2.9 | 13.1 | 4 | 3.1 | 6.3 |
| ALL/ALL | ks_devstop3_60m_side | 0.55 | 2.7 | -0.3 | 0.52 | 0.48 | 3.0 [2.6, 3.5] | 2.9 | 13.1 | 4 | 2.4 | 2.2 |
| ALL/ALL | eh_ebsw_slow_60m_eagainst | 0.43 | -0.3 | 2.6 | 0.48 | 0.52 | -3.0 [-3.4, -2.5] | -2.9 | -12.8 | 4 | -2.6 | -3.7 |
| ALL/ALL | ks_devstop3_agree4of4 | 0.34 | 3.4 | 0.3 | 0.52 | 0.49 | 3.1 [2.6, 3.6] | 3.0 | 12.7 | 4 | 1.3 | 4.9 |
| ALL/ALL | dm_setup9_any_15m_against_state | 0.41 | 3.1 | 0.1 | 0.52 | 0.49 | 3.0 [2.5, 3.4] | 2.9 | 12.7 | 3 | 2.0 | 1.1 |
| ALL/ALL | eh_cyber_slow_60m_ewith | 0.21 | 4.2 | 0.6 | 0.53 | 0.50 | 3.6 [3.1, 4.2] | 3.5 | 12.7 | 4 | 5.7 | 9.3 |
| ALL/ALL | rk_8020_std_60m_against_state | 0.48 | 2.8 | -0.0 | 0.52 | 0.49 | 2.9 [2.4, 3.3] | 2.8 | 12.5 | 3 | 3.5 | 4.9 |
| ALL/ALL | ks_devstop1_60m_side | 0.58 | 2.6 | -0.3 | 0.51 | 0.49 | 2.9 [2.4, 3.3] | 2.8 | 12.4 | 4 | 3.9 | 8.6 |
| ALL/ALL | eh_ebsw_slow_60m_ewith | 0.48 | 2.8 | -0.0 | 0.52 | 0.49 | 2.8 [2.4, 3.3] | 2.8 | 12.3 | 4 | 1.3 | 2.4 |
| ALL/ALL | rk_anti_60m_state | 0.54 | 2.7 | -0.2 | 0.51 | 0.49 | 2.8 [2.4, 3.3] | 2.8 | 12.3 | 4 | 1.9 | -2.2 |
| ALL/ALL | bk_trendbars20_15m_side | 0.60 | 2.5 | -0.4 | 0.51 | 0.48 | 2.9 [2.4, 3.3] | 2.8 | 12.3 | 4 | 4.1 | 5.2 |
| ALL/ALL | rk_8020_std_60m_state | 0.44 | -0.2 | 2.6 | 0.48 | 0.52 | -2.8 [-3.3, -2.4] | -2.7 | -12.1 | 3 | -4.3 | -5.4 |
| ALL/ALL | rk_310h_fast_1d_rise | 0.50 | 2.7 | -0.0 | 0.51 | 0.49 | 2.8 [2.3, 3.2] | 2.7 | 12.1 | 4 | 3.6 | 7.0 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | dm_tdst_5m_side | 0.51 | 5.4 | -0.1 | 0.54 | 0.48 | 5.5 [4.8, 6.2] | 5.4 | 15.5 | 4 | 6.6 | 9.1 |
| ALL/0 | st_zma200_15m_ewith | 0.26 | 7.0 | 1.2 | 0.56 | 0.50 | 5.8 [5.0, 6.6] | 5.6 | 14.0 | 4 | 3.4 | 9.0 |
| ALL/0 | eh_dcp_long_60m_hi | 0.67 | 1.0 | 6.0 | 0.49 | 0.56 | -5.0 [-5.7, -4.2] | -4.8 | -12.9 | 4 | -2.6 | -4.9 |
| ALL/0 | ch_dmi_15m_side | 0.77 | 3.9 | -1.4 | 0.53 | 0.47 | 5.3 [4.5, 6.1] | 5.2 | 12.8 | 4 | 10.1 | 10.9 |
| ALL/0 | dm_setup9_any_5m_against_state | 0.48 | 5.0 | 0.5 | 0.54 | 0.49 | 4.5 [3.8, 5.2] | 4.4 | 12.6 | 4 | 1.9 | 1.6 |
| ALL/0 | dm_setup9_perf_5m_against_state | 0.37 | 5.6 | 0.9 | 0.55 | 0.50 | 4.7 [4.0, 5.4] | 4.6 | 12.6 | 4 | 2.0 | -1.2 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | wl_volstop_flip_fast_1d_against10 | 0.32 | -2.9 | 3.2 | 0.46 | 0.52 | -6.1 [-7.0, -5.2] | -5.9 | -12.7 | 4 | -13.4 | -14.7 |
| ALL/1 | dm_supply_line_1d_fresh5 | 0.23 | -6.3 | 4.3 | 0.43 | 0.53 | -10.6 [-12.1, -9.0] | -9.6 | -12.2 | 4 | -7.9 | -15.9 |
| ALL/1 | wl_volstop_flip_fast_1d_state | 0.44 | 4.2 | -1.1 | 0.53 | 0.48 | 5.3 [4.4, 6.1] | 5.1 | 11.7 | 4 | 4.6 | 1.0 |
| ALL/1 | wl_volstop_flip_slow_1d_against10 | 0.18 | -4.4 | 2.5 | 0.44 | 0.51 | -6.9 [-8.0, -5.8] | -6.6 | -11.5 | 4 | -7.6 | -5.3 |
| ALL/1 | rk_grail_std_1d_against10 | 0.04 | -11.6 | 1.8 | 0.38 | 0.51 | -13.4 [-15.4, -11.4] | -11.3 | -10.9 | 4 | -13.7 | nan |
| ALL/1 | bk_micro_60m_against_ge3 | 0.16 | -4.4 | 2.3 | 0.45 | 0.51 | -6.7 [-7.9, -5.6] | -6.4 | -10.8 | 4 | -11.3 | -11.3 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | ch_fosc_slow_1d_sig | 0.51 | 5.5 | -7.0 | 0.54 | 0.44 | 12.6 [10.2, 14.9] | 11.8 | 9.7 | 4 | 15.2 | 10.2 |
| ALL/2 | ch_fosc_slow_1d_rise | 0.51 | 5.0 | -6.6 | 0.54 | 0.44 | 11.6 [9.2, 14.0] | 10.9 | 9.0 | 4 | 13.4 | 16.1 |
| ALL/2 | cn_rsi2_std_1d_divwith | 0.19 | 11.2 | -3.4 | 0.60 | 0.47 | 14.6 [11.6, 17.7] | 13.3 | 8.6 | 4 | 10.5 | 20.7 |
| ALL/2 | cn_rsi2_fast_1d_divwith | 0.19 | 11.2 | -3.4 | 0.60 | 0.47 | 14.6 [11.6, 17.7] | 13.3 | 8.6 | 4 | 10.5 | 20.7 |
| ALL/2 | rk_8020_fast_60m_state | 0.50 | -5.4 | 4.1 | 0.45 | 0.53 | -9.5 [-11.9, -7.1] | -9.0 | -7.4 | 4 | -15.7 | -16.0 |
| ALL/2 | rk_310h_fast_1d_rise | 0.49 | 4.2 | -5.3 | 0.53 | 0.46 | 9.4 [7.0, 11.8] | 8.9 | 7.3 | 4 | 11.9 | 4.9 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | eh_cyber_fast_1d_nodiv | 0.85 | 0.1 | 9.7 | 0.48 | 0.57 | -9.6 [-11.5, -7.6] | -8.7 | -8.8 | 4 | -0.3 | 0.5 |
| ALL/3 | cn_double7_60m_against10 | 0.40 | -2.3 | 4.1 | 0.45 | 0.52 | -6.4 [-7.9, -5.0] | -6.1 | -8.3 | 4 | -4.0 | -5.0 |
| ALL/3 | rk_soup_slow_15m_state | 0.29 | -3.4 | 3.6 | 0.45 | 0.51 | -7.0 [-8.5, -5.4] | -6.6 | -8.3 | 4 | -4.4 | -3.3 |
| ALL/3 | bk_trendbars20_15m_side | 0.57 | 4.2 | -2.0 | 0.52 | 0.46 | 6.2 [4.8, 7.6] | 5.9 | 8.1 | 4 | 8.0 | 13.2 |
| ALL/3 | eh_roof_fast_1d_nodiv | 0.86 | 0.3 | 8.9 | 0.48 | 0.56 | -8.6 [-10.6, -6.6] | -7.8 | -7.6 | 4 | -1.8 | 0.5 |
| ALL/3 | rk_8020_slow_1d_state | 0.37 | -2.1 | 3.6 | 0.46 | 0.51 | -5.7 [-7.1, -4.3] | -5.4 | -7.3 | 4 | -12.1 | nan |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | dm_combo13_60m_against_state | 0.02 | 34.0 | -1.1 | 0.79 | 0.48 | 35.1 [31.6, 38.6] | 28.0 | 15.7 | 4 | 47.0 | 46.7 |
| ALL/4 | st_zma200_15m_ewith | 0.38 | 6.1 | -4.1 | 0.55 | 0.46 | 10.2 [8.9, 11.6] | 9.8 | 14.0 | 4 | 19.0 | 37.6 |
| ALL/4 | ch_fosc_slow_1d_sig | 0.51 | 4.4 | -5.2 | 0.54 | 0.44 | 9.5 [8.2, 10.9] | 9.2 | 13.4 | 4 | 8.1 | 29.7 |
| ALL/4 | rk_310_fast_1d_rise | 0.50 | 4.3 | -4.8 | 0.53 | 0.45 | 9.2 [7.8, 10.5] | 8.8 | 12.9 | 4 | 14.3 | 38.0 |
| ALL/4 | bk_failbo_std_60m_state | 0.39 | -5.7 | 3.2 | 0.44 | 0.52 | -9.0 [-10.3, -7.6] | -8.6 | -12.3 | 4 | -10.3 | -11.6 |
| ALL/4 | eh_ebsw_slow_60m_side | 0.57 | 3.5 | -5.3 | 0.53 | 0.45 | 8.8 [7.5, 10.2] | 8.5 | 12.3 | 4 | 15.7 | 24.4 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | dm_tdst_1d_side | 0.38 | 4.4 | -3.0 | 0.54 | 0.46 | 7.3 [5.7, 9.0] | 6.8 | 8.0 | 4 | 12.9 | 27.9 |
| ALL/5 | dm_line_break_1d_against10 | 0.60 | 2.6 | -4.4 | 0.52 | 0.45 | 7.0 [5.3, 8.7] | 6.5 | 7.7 | 4 | 2.0 | 12.8 |
| ALL/5 | rk_8020_std_1d_against10 | 0.44 | -3.7 | 2.6 | 0.46 | 0.52 | -6.3 [-7.9, -4.6] | -5.9 | -7.0 | 4 | -7.8 | -4.3 |
| ALL/5 | cn_rsi_pb_fast_1d_against_state | 0.16 | -7.6 | 1.2 | 0.43 | 0.50 | -8.8 [-11.0, -6.6] | -7.8 | -7.0 | 4 | -3.4 | nan |
| ALL/5 | eh_mama_fast_60m_fresh5 | 0.25 | -5.5 | 1.6 | 0.44 | 0.51 | -7.2 [-9.0, -5.3] | -6.6 | -6.8 | 4 | -16.4 | -7.4 |
| ALL/5 | eh_mamapx_std_15m_fresh5 | 0.48 | 3.0 | -3.1 | 0.52 | 0.46 | 6.1 [4.5, 7.7] | 5.7 | 6.8 | 4 | 6.9 | 8.1 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_A_named_hs.parquet

## Sub-block B: session / daily named systems (Dalton / Steidlmayer, Crabel, Fisher ACD, Williams)

### B - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 123 conditions; 2055 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 28 conditions with |t|>2 (chance alone: about 6). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | dl_pd_neutral | 0.11 | 267.3 | 85.2 | 0.48 | 0.43 | 182.1 [81.1, 283.0] | 83.4 | 3.5 | 4 | 239.6 | 345.8 |
| ALL/ALL | cb_stretch_std_hit | 0.75 | 66.9 | -53.4 | 0.44 | 0.40 | 120.3 [48.8, 191.8] | 75.5 | 3.3 | 3 | 289.9 | 340.0 |
| ALL/ALL | cb_stretch_std_beyond | 0.58 | 80.3 | -24.5 | 0.44 | 0.41 | 104.8 [38.2, 171.4] | 69.2 | 3.1 | 3 | 159.5 | 232.6 |
| ALL/ALL | wl_volbo_fast_beyond | 0.46 | 91.3 | -9.4 | 0.45 | 0.41 | 100.7 [32.0, 169.5] | 65.1 | 2.9 | 3 | 343.0 | 416.2 |
| ALL/ALL | dl_sp_ahead_120 | 0.06 | -75.6 | 118.0 | 0.40 | 0.44 | -193.6 [-326.5, -60.7] | -63.5 | -2.9 | 3 | -161.0 | -22.1 |
| ALL/ALL | cb_stretch_fast_beyond | 0.60 | 74.9 | -20.1 | 0.44 | 0.41 | 95.0 [28.2, 161.7] | 62.6 | 2.8 | 4 | 215.6 | 349.0 |
| ALL/ALL | cb_stretch_slow_hit | 0.74 | 62.2 | -38.1 | 0.43 | 0.41 | 100.4 [29.0, 171.8] | 63.1 | 2.8 | 3 | 283.1 | 396.7 |
| ALL/ALL | fa_inor_std | 0.41 | -41.4 | 58.7 | 0.41 | 0.44 | -100.1 [-173.0, -27.2] | -62.0 | -2.7 | 4 | -186.5 | -0.1 |
| ALL/ALL | dl_ib_ext_dn | 0.28 | -48.5 | 77.9 | 0.41 | 0.45 | -126.3 [-218.5, -34.2] | -63.7 | -2.7 | 3 | -77.4 | -912.1 |
| ALL/ALL | dl_pd_neutral_ext | 0.06 | 272.1 | 94.8 | 0.49 | 0.43 | 177.2 [47.1, 307.4] | 59.8 | 2.7 | 4 | 191.4 | 642.0 |
| ALL/ALL | wl_volbo_std_hit | 0.34 | 102.6 | 1.7 | 0.45 | 0.41 | 100.9 [26.4, 175.3] | 61.4 | 2.7 | 4 | 309.1 | 343.3 |
| ALL/ALL | dl_pd_trend_against | 0.04 | -93.5 | 113.2 | 0.39 | 0.44 | -206.7 [-362.1, -51.3] | -54.4 | -2.6 | 3 | -36.5 | -20.3 |
| ALL/ALL | cb_stretch_fast_hit | 0.75 | 60.1 | -34.9 | 0.43 | 0.41 | 95.0 [22.9, 167.1] | 59.3 | 2.6 | 3 | 222.0 | 351.3 |
| ALL/ALL | wl_volbo_fast_hit | 0.61 | 70.7 | -16.3 | 0.44 | 0.41 | 87.0 [20.1, 153.9] | 57.3 | 2.5 | 4 | 217.6 | 299.8 |
| ALL/ALL | dl_sp_ahead_any | 0.20 | 25.8 | 125.6 | 0.42 | 0.44 | -99.8 [-177.1, -22.5] | -59.0 | -2.5 | 3 | -126.3 | -205.0 |
| ALL/ALL | fa_a_std_hit_with | 0.46 | 66.6 | -23.9 | 0.44 | 0.42 | 90.5 [18.0, 163.0] | 56.2 | 2.4 | 3 | 164.5 | 99.6 |
| ALL/ALL | fa_nl60_fast_with | 0.05 | 277.7 | 96.9 | 0.49 | 0.44 | 180.8 [35.3, 326.3] | 52.3 | 2.4 | 3 | 120.1 | nan |
| ALL/ALL | fa_a_fast_hit_with | 0.68 | 52.8 | -33.3 | 0.44 | 0.42 | 86.1 [13.4, 158.8] | 53.4 | 2.3 | 3 | 208.8 | 98.9 |
| ALL/ALL | dl_excess_high | 0.77 | 125.5 | 39.9 | 0.44 | 0.43 | 85.6 [12.6, 158.5] | 52.9 | 2.3 | 4 | 19.9 | -0.0 |
| ALL/ALL | dl_sp_ahead_60 | 0.03 | -110.5 | 112.0 | 0.40 | 0.44 | -222.5 [-419.2, -25.8] | -40.6 | -2.2 | 3 | -466.8 | -530.0 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | fa_above_pr_with | 0.62 | 286.1 | 145.7 | 0.48 | 0.45 | 140.4 [1.3, 279.5] | 101.8 | 1.4 | 4 | 207.1 | 414.1 |
| ALL/0 | dl_sp_ahead_any | 0.20 | 96.5 | 266.3 | 0.44 | 0.47 | -169.8 [-340.3, 0.7] | -108.2 | -1.2 | 4 | -383.5 | -409.4 |
| ALL/0 | cb_nr7 | 0.14 | 76.3 | 256.7 | 0.45 | 0.47 | -180.4 [-383.0, 22.2] | -100.0 | -1.0 | 4 | -117.3 | -166.4 |
| ALL/0 | dl_pd_neutral | 0.11 | 418.9 | 209.7 | 0.49 | 0.46 | 209.2 [-25.0, 443.4] | 100.9 | 0.8 | 4 | 103.1 | 511.5 |
| ALL/0 | fa_nl30_std_with | 0.13 | 341.2 | 215.6 | 0.49 | 0.46 | 125.5 [-76.3, 327.4] | 69.9 | 0.7 | 4 | 24.8 | -459.4 |
| ALL/0 | fa_nl15_slow_with | 0.22 | 300.1 | 213.4 | 0.48 | 0.46 | 86.7 [-78.0, 251.5] | 56.7 | 0.7 | 4 | 35.4 | -106.9 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | dl_poc_side_with | 0.59 | -4.4 | 80.6 | 0.41 | 0.43 | -84.9 [-176.0, 6.1] | -0.0 | -0.0 | 4 | -196.8 | -242.6 |
| ALL/1 | dl_pd_normal | 0.13 | 179.8 | 8.5 | 0.45 | 0.41 | 171.3 [38.2, 304.5] | 0.0 | 0.0 | 4 | 152.1 | 286.9 |
| ALL/1 | dl_pd_neutral | 0.11 | 196.4 | 10.5 | 0.46 | 0.41 | 185.9 [41.2, 330.5] | 0.0 | 0.0 | 4 | 348.9 | 327.5 |
| ALL/1 | wl_tdom_first3 | 0.15 | -39.7 | 42.5 | 0.39 | 0.42 | -82.2 [-207.1, 42.8] | -0.0 | -0.0 | 4 | -34.3 | -69.8 |
| ALL/1 | dl_pd_neutral_ext | 0.06 | 308.3 | 13.3 | 0.48 | 0.41 | 295.0 [102.6, 487.4] | 0.0 | 0.0 | 4 | 569.1 | 517.5 |
| ALL/1 | dl_sp_ahead_120 | 0.06 | -95.7 | 38.6 | 0.38 | 0.42 | -134.3 [-331.2, 62.6] | -0.0 | -0.0 | 4 | -134.0 | 77.5 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | dl_pd_neutral | 0.12 | 205.8 | 2.3 | 0.49 | 0.41 | 203.5 [78.0, 329.0] | 128.1 | 2.0 | 4 | 345.0 | -22.7 |
| ALL/3 | dl_pd_normal | 0.11 | -115.1 | 44.2 | 0.38 | 0.42 | -159.3 [-276.8, -41.8] | -105.1 | -1.8 | 4 | -27.9 | 103.1 |
| ALL/3 | cb_prior_wide | 0.12 | -103.0 | 44.6 | 0.36 | 0.43 | -147.6 [-261.1, -34.0] | -99.6 | -1.7 | 4 | -51.1 | 128.4 |
| ALL/3 | fa_inor_std | 0.43 | -45.5 | 43.0 | 0.41 | 0.43 | -88.5 [-171.7, -5.3] | -70.3 | -1.7 | 4 | -226.9 | 10.3 |
| ALL/3 | wl_volbo_std_hit | 0.33 | 90.7 | -0.6 | 0.45 | 0.41 | 91.3 [5.2, 177.4] | 71.5 | 1.6 | 4 | 375.5 | 292.7 |
| ALL/3 | dl_va_wide | 0.14 | -71.2 | 44.0 | 0.38 | 0.43 | -115.2 [-221.8, -8.5] | -80.8 | -1.5 | 4 | -170.2 | -162.0 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | cb_stretch_slow_hit | 0.70 | 125.8 | -69.7 | 0.48 | 0.41 | 195.5 [48.8, 342.2] | 76.0 | 1.0 | 4 | 469.3 | 783.2 |
| ALL/4 | cb_stretch_std_hit | 0.70 | 120.4 | -59.9 | 0.48 | 0.42 | 180.3 [32.8, 327.9] | 69.6 | 0.9 | 4 | 443.2 | 560.5 |
| ALL/4 | cb_stretch_slow_beyond | 0.48 | 150.2 | -11.4 | 0.48 | 0.44 | 161.6 [18.9, 304.4] | 65.0 | 0.9 | 4 | 248.8 | 514.8 |
| ALL/4 | cb_stretch_std_beyond | 0.48 | 147.4 | -9.0 | 0.48 | 0.44 | 156.4 [13.7, 299.0] | 62.9 | 0.9 | 4 | 54.6 | 364.2 |
| ALL/4 | cb_orb15_beyond | 0.51 | 142.9 | -11.1 | 0.48 | 0.44 | 154.0 [12.3, 295.8] | 62.4 | 0.9 | 4 | 101.4 | 289.8 |
| ALL/4 | cb_stretch_fast_hit | 0.70 | 117.3 | -53.5 | 0.48 | 0.42 | 170.8 [22.0, 319.6] | 65.3 | 0.9 | 4 | 313.0 | 616.8 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | cb_nr4 | 0.23 | 235.0 | 78.4 | 0.58 | 0.50 | 156.6 [2.3, 310.9] | 0.0 | 2.0 | 3 | 226.5 | -168.8 |
| A7/0 | dl_pd_neutral | 0.10 | 283.6 | 96.5 | 0.60 | 0.51 | 187.0 [-31.1, 405.2] | 0.0 | 1.7 | 3 | 253.1 | 539.3 |
| A7/0 | dl_pd_normal | 0.13 | -25.7 | 136.0 | 0.46 | 0.53 | -161.7 [-357.6, 34.2] | -0.0 | -1.6 | 3 | -194.1 | -244.7 |
| A7/0 | dl_against_va | 0.08 | 267.2 | 101.5 | 0.60 | 0.52 | 165.7 [-74.9, 406.3] | 0.0 | 1.4 | 4 | 28.9 | -592.3 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | wl_tdom_last3 | 0.14 | 595.6 | 156.1 | 0.55 | 0.47 | 439.4 [-113.1, 992.0] | 0.0 | 1.6 | 4 | 307.9 | -595.6 |
| H7/0 | fa_nl15_fast_with | 0.21 | 3.9 | 271.1 | 0.46 | 0.49 | -267.2 [-711.8, 177.4] | -0.0 | -1.2 | 3 | -681.5 | 0.4 |
| H7/0 | dl_pd_normal | 0.14 | 55.0 | 242.6 | 0.40 | 0.49 | -187.6 [-675.6, 300.4] | -0.0 | -0.8 | 3 | -275.9 | -474.9 |
| H7/0 | wl_tdom_seasonal_with | 0.57 | 148.8 | 245.6 | 0.48 | 0.47 | -96.9 [-482.1, 288.4] | -0.0 | -0.5 | 3 | -561.9 | -71.5 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | wl_volbo_fast_beyond | 0.42 | 234.0 | -90.0 | 0.57 | 0.42 | 324.0 [86.9, 561.2] | 205.5 | 2.7 | 3 | 524.4 | 572.3 |
| H7/3 | dl_open_outside_va | 0.63 | 159.7 | -149.0 | 0.53 | 0.41 | 308.7 [67.6, 549.8] | 193.4 | 2.5 | 3 | 581.7 | -1251.3 |
| H7/3 | wl_volbo_fast_hit | 0.55 | 145.7 | -76.6 | 0.53 | 0.42 | 222.3 [-10.9, 455.5] | 142.7 | 1.9 | 4 | 405.5 | 434.7 |
| H7/3 | fa_a_fast_fresh30 | 0.47 | -58.5 | 136.0 | 0.44 | 0.52 | -194.5 [-429.1, 40.1] | -124.3 | -1.6 | 3 | -566.3 | -515.2 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | dl_poc_side_with | 0.61 | 132.0 | 21.2 | 0.46 | 0.42 | 110.9 [9.9, 211.8] | 0.0 | 2.2 | 4 | 150.4 | 209.1 |
| K7/0 | dl_pd_double | 0.11 | 212.0 | 73.9 | 0.50 | 0.44 | 138.1 [-24.7, 301.0] | 0.0 | 1.7 | 3 | 192.9 | 166.8 |
| K7/0 | fa_above_pr_with | 0.56 | 122.8 | 45.5 | 0.46 | 0.43 | 77.3 [-22.8, 177.4] | 0.0 | 1.5 | 4 | 109.1 | 339.6 |
| K7/0 | cb_nr7 | 0.12 | -10.5 | 102.9 | 0.40 | 0.45 | -113.3 [-261.9, 35.2] | -0.0 | -1.5 | 4 | -157.2 | -338.6 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | wl_tdom_seasonal_with | 0.50 | 108.9 | -27.4 | 0.45 | 0.41 | 136.3 [18.6, 254.1] | 14.4 | 2.3 | 4 | 93.4 | -10.9 |
| K7/1 | dl_pd_normvar_with | 0.35 | -15.8 | 62.7 | 0.40 | 0.44 | -78.5 [-201.8, 44.9] | -7.6 | -1.2 | 3 | -215.0 | -350.0 |
| K7/1 | dl_inside_va | 0.37 | -11.7 | 63.5 | 0.40 | 0.44 | -75.2 [-195.5, 45.1] | -7.6 | -1.2 | 3 | -19.2 | -8.3 |
| K7/1 | cb_nr7 | 0.14 | 120.2 | 22.1 | 0.45 | 0.42 | 98.1 [-77.4, 273.6] | 5.0 | 1.1 | 3 | 198.1 | 282.3 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | cb_prior_wide | 0.12 | -205.8 | 39.0 | 0.32 | 0.44 | -244.8 [-392.6, -97.0] | -43.0 | -3.2 | 4 | -782.3 | -817.5 |
| K7/3 | dl_excess_support_with | 0.68 | -30.6 | 96.2 | 0.41 | 0.47 | -126.7 [-234.4, -19.1] | -36.3 | -2.3 | 3 | -214.2 | -2.4 |
| K7/3 | dl_pd_neutral | 0.12 | 156.6 | -10.8 | 0.50 | 0.42 | 167.4 [12.0, 322.7] | 27.1 | 2.1 | 4 | 260.0 | -218.9 |
| K7/3 | cb_nr4 | 0.26 | 95.2 | -20.3 | 0.47 | 0.41 | 115.5 [0.8, 230.2] | 30.2 | 2.0 | 4 | 113.5 | 54.1 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | cb_stretch_slow_hit | 0.70 | 125.8 | -69.7 | 0.48 | 0.41 | 195.5 [48.8, 342.2] | 76.0 | 2.6 | 4 | 469.3 | 783.2 |
| K7/4 | cb_stretch_std_hit | 0.70 | 120.4 | -59.9 | 0.48 | 0.42 | 180.3 [32.8, 327.9] | 69.6 | 2.4 | 4 | 443.2 | 560.5 |
| K7/4 | dl_excess_low | 0.82 | 101.3 | -112.8 | 0.47 | 0.41 | 214.1 [38.5, 389.7] | 65.8 | 2.4 | 4 | 415.5 | 425.1 |
| K7/4 | cb_stretch_fast_hit | 0.70 | 117.3 | -53.5 | 0.48 | 0.42 | 170.8 [22.0, 319.6] | 65.3 | 2.2 | 4 | 313.0 | 616.8 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | dl_pd_neutral | 0.11 | 261.5 | -34.5 | 0.50 | 0.39 | 296.0 [119.5, 472.6] | 0.0 | 3.3 | 4 | 495.1 | 651.5 |
| M7/1 | fa_nl30_slow_with | 0.13 | 124.3 | -21.6 | 0.45 | 0.40 | 145.9 [-8.8, 300.7] | 0.0 | 1.8 | 3 | 19.2 | -216.1 |
| M7/1 | dl_pd_neutral_ext | 0.06 | 199.5 | -16.1 | 0.49 | 0.40 | 215.6 [-13.3, 444.5] | 0.0 | 1.8 | 4 | 681.5 | 1190.9 |
| M7/1 | fa_nl60_slow_with | 0.10 | 107.4 | -15.5 | 0.45 | 0.40 | 122.8 [-53.0, 298.6] | 0.0 | 1.4 | 3 | 205.1 | 880.7 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | dl_pd_normal | 0.11 | -179.5 | 67.6 | 0.34 | 0.45 | -247.1 [-406.6, -87.5] | -0.0 | -3.0 | 4 | -130.4 | -93.7 |
| M7/3 | dl_pd_neutral | 0.12 | 248.3 | 11.0 | 0.55 | 0.42 | 237.3 [76.7, 398.0] | 0.0 | 2.9 | 4 | 409.0 | 234.2 |
| M7/3 | cb_prior_wide | 0.12 | -107.6 | 60.7 | 0.36 | 0.45 | -168.3 [-320.9, -15.8] | -0.0 | -2.2 | 4 | -220.8 | -25.4 |
| M7/3 | fa_a_std_now_with | 0.37 | 105.3 | -8.2 | 0.47 | 0.41 | 113.6 [4.1, 223.1] | 0.0 | 2.0 | 4 | 157.3 | 100.0 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | cb_stretch_fast_beyond | 0.50 | 269.4 | 89.4 | 0.41 | 0.34 | 180.0 [-33.3, 393.3] | 54.8 | 1.7 | 4 | 141.1 | 1051.2 |
| O7/3 | wl_tdom_4_9 | 0.31 | 45.9 | 233.9 | 0.31 | 0.40 | -187.9 [-413.9, 38.0] | -52.7 | -1.6 | 3 | -132.7 | -153.4 |
| O7/3 | wl_smash_with | 0.30 | 47.5 | 230.3 | 0.33 | 0.39 | -182.8 [-411.0, 45.4] | -50.6 | -1.6 | 3 | -91.1 | 307.4 |
| O7/3 | dl_excess_high | 0.73 | 213.1 | 73.5 | 0.39 | 0.34 | 139.6 [-93.3, 372.5] | 37.5 | 1.2 | 3 | 1049.3 | 803.9 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | dl_sp_ahead_120 | 0.07 | -518.3 | 494.6 | 0.34 | 0.45 | -1012.9 [-1766.7, -259.2] | -115.9 | -2.6 | 3 | -1189.6 | -942.0 |
| P7/0 | dl_sp_ahead_any | 0.20 | -38.0 | 542.2 | 0.39 | 0.45 | -580.2 [-1061.7, -98.8] | -139.6 | -2.4 | 4 | -756.8 | -706.1 |
| P7/0 | dl_pd_trend_against | 0.03 | -494.3 | 451.8 | 0.34 | 0.44 | -946.1 [-1994.1, 101.9] | -59.3 | -1.8 | 4 | -698.4 | 1591.8 |
| P7/0 | fa_nl30_slow_with | 0.13 | 853.4 | 357.0 | 0.48 | 0.43 | 496.4 [-80.1, 1073.0] | 89.8 | 1.7 | 4 | 258.7 | 381.0 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | fa_inside_pr | 0.13 | 258.6 | 0.3 | 0.41 | 0.38 | 258.3 [-79.4, 596.0] | 0.0 | 1.5 | 4 | 474.3 | 313.8 |
| P7/1 | wl_tdom_seasonal_with | 0.50 | -29.4 | 130.6 | 0.37 | 0.40 | -160.1 [-390.4, 70.2] | -0.0 | -1.4 | 3 | -254.8 | -496.3 |
| P7/1 | dl_pd_neutral_ext | 0.06 | 364.1 | 13.9 | 0.42 | 0.38 | 350.2 [-174.1, 874.5] | 0.0 | 1.3 | 4 | 484.0 | 211.7 |
| P7/1 | fa_nl30_slow_with | 0.13 | -137.6 | 59.2 | 0.35 | 0.39 | -196.9 [-516.2, 122.4] | -0.0 | -1.2 | 3 | -162.7 | -93.8 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | cb_stretch_std_hit | 0.82 | 34.8 | -323.9 | 0.40 | 0.34 | 358.7 [63.6, 653.9] | 0.0 | 2.4 | 3 | 918.4 | 726.0 |
| P7/3 | cb_stretch_std_beyond | 0.64 | 80.4 | -226.7 | 0.40 | 0.37 | 307.1 [54.4, 559.8] | 0.0 | 2.4 | 3 | 690.0 | 443.8 |
| P7/3 | cb_stretch_slow_hit | 0.82 | 34.9 | -316.6 | 0.40 | 0.35 | 351.5 [57.5, 645.5] | 0.0 | 2.3 | 3 | 911.1 | 708.8 |
| P7/3 | dl_inside_va | 0.28 | -262.2 | 56.6 | 0.34 | 0.41 | -318.8 [-587.5, -50.1] | -0.0 | -2.3 | 3 | -709.1 | -654.5 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | dl_pd_normal | 0.15 | -360.7 | 512.5 | 0.42 | 0.55 | -873.3 [-1584.9, -161.6] | -0.0 | -2.4 | 3 | -525.6 | -1553.8 |
| U7/0 | dl_excess_low | 0.82 | 279.7 | 873.1 | 0.51 | 0.61 | -593.4 [-1260.3, 73.4] | -0.0 | -1.7 | 4 | -782.3 | -1887.0 |
| U7/0 | dl_pd_normvar_with | 0.24 | 777.6 | 259.0 | 0.60 | 0.50 | 518.6 [-69.0, 1106.2] | 0.0 | 1.7 | 3 | 220.6 | 1447.4 |
| U7/0 | cb_prior_wide | 0.13 | -40.9 | 448.8 | 0.48 | 0.53 | -489.7 [-1267.8, 288.4] | -0.0 | -1.2 | 3 | -1063.8 | 763.7 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | dl_above_va_with | 0.19 | -440.5 | 270.7 | 0.40 | 0.53 | -711.2 [-1337.8, -84.5] | -35.7 | -2.2 | 3 | -753.9 | -1677.0 |
| U7/1 | dl_pd_normal | 0.11 | 804.8 | 48.3 | 0.63 | 0.49 | 756.5 [6.1, 1507.0] | 26.9 | 2.0 | 3 | 168.6 | 803.3 |
| U7/1 | dl_poc_side_with | 0.37 | -171.7 | 311.5 | 0.46 | 0.53 | -483.3 [-982.2, 15.7] | -37.2 | -1.9 | 4 | -871.5 | -936.4 |
| U7/1 | dl_inside_va | 0.42 | 364.1 | -31.7 | 0.56 | 0.46 | 395.8 [-85.4, 877.0] | 32.6 | 1.6 | 3 | 241.5 | 1809.3 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B_sess_named.parquet

### B - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 124 conditions; 4296 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 70 conditions with |t|>2 (chance alone: about 6). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | dl_pd_neutral | 0.11 | 6.2 | 0.7 | 0.54 | 0.50 | 5.5 [4.8, 6.2] | 5.4 | 14.9 | 4 | 9.6 | 1.6 |
| ALL/ALL | dl_pd_neutral_ext | 0.06 | 7.3 | 1.0 | 0.55 | 0.50 | 6.3 [5.4, 7.3] | 6.2 | 13.1 | 4 | 9.2 | 13.4 |
| ALL/ALL | fa_above_pr_with | 0.61 | 2.5 | -0.4 | 0.51 | 0.49 | 2.9 [2.4, 3.3] | 2.8 | 12.2 | 4 | 4.6 | 6.7 |
| ALL/ALL | wl_oops_with | 0.11 | -6.4 | 1.3 | 0.43 | 0.50 | -7.7 [-9.1, -6.2] | -7.2 | -10.4 | 4 | -13.6 | -20.0 |
| ALL/ALL | wl_volbo_fast_beyond | 0.52 | 2.5 | -1.7 | 0.51 | 0.47 | 4.1 [3.2, 5.1] | 4.1 | 9.0 | 4 | 10.6 | 14.8 |
| ALL/ALL | wl_volbo_std_hit | 0.42 | 2.9 | -1.3 | 0.51 | 0.48 | 4.2 [3.2, 5.1] | 4.1 | 8.9 | 4 | 7.5 | 12.0 |
| ALL/ALL | dl_poor_high_ahead | 0.00 | 15.3 | 1.3 | 0.62 | 0.50 | 14.0 [10.8, 17.1] | 10.8 | 8.7 | 3 | 15.8 | 20.7 |
| ALL/ALL | wl_volbo_fast_hit | 0.64 | 2.0 | -2.1 | 0.51 | 0.47 | 4.1 [3.1, 5.0] | 4.0 | 8.5 | 4 | 8.5 | 10.1 |
| ALL/ALL | wl_gap_with | 0.21 | 3.9 | -0.4 | 0.52 | 0.48 | 4.4 [3.3, 5.5] | 4.2 | 7.8 | 4 | 5.2 | 7.7 |
| ALL/ALL | dl_poor_extreme_ahead | 0.00 | 13.1 | 1.3 | 0.59 | 0.50 | 11.8 [8.8, 14.8] | 9.3 | 7.7 | 3 | 8.9 | 20.7 |
| ALL/ALL | wl_volbo_std_beyond | 0.33 | 2.9 | -0.7 | 0.51 | 0.48 | 3.7 [2.7, 4.7] | 3.6 | 7.6 | 4 | 7.0 | 12.7 |
| ALL/ALL | dl_poc_side_with | 0.67 | 2.0 | 0.1 | 0.51 | 0.49 | 1.8 [1.4, 2.3] | 1.8 | 7.5 | 4 | 5.2 | 4.6 |
| ALL/ALL | dl_r80_active_with | 0.04 | -7.7 | 0.8 | 0.41 | 0.50 | -8.6 [-10.8, -6.3] | -7.5 | -7.5 | 4 | -9.0 | -6.6 |
| ALL/ALL | dl_sp_behind_120 | 0.04 | 4.6 | 1.2 | 0.53 | 0.50 | 3.4 [2.5, 4.4] | 3.3 | 7.1 | 4 | 16.5 | 24.7 |
| ALL/ALL | dl_pd_trend_against | 0.04 | -2.7 | 1.5 | 0.46 | 0.50 | -4.2 [-5.4, -3.1] | -4.1 | -7.1 | 4 | -2.4 | -12.1 |
| ALL/ALL | fa_c_std_with | 0.09 | -5.2 | 0.8 | 0.46 | 0.49 | -6.1 [-7.7, -4.4] | -5.6 | -7.1 | 4 | -7.8 | -18.6 |
| ALL/ALL | cb_stretch_std_hit | 0.77 | 1.3 | -2.3 | 0.50 | 0.47 | 3.7 [2.6, 4.7] | 3.6 | 6.7 | 4 | 7.2 | 10.3 |
| ALL/ALL | fa_nl60_fast_with | 0.05 | 4.7 | 1.2 | 0.54 | 0.50 | 3.5 [2.5, 4.6] | 3.4 | 6.6 | 3 | 3.4 | nan |
| ALL/ALL | cb_stretch_std_beyond | 0.63 | 1.6 | -1.5 | 0.50 | 0.48 | 3.1 [2.2, 4.1] | 3.0 | 6.6 | 4 | 5.8 | 12.4 |
| ALL/ALL | cb_stretch_fast_hit | 0.77 | 1.3 | -2.2 | 0.50 | 0.47 | 3.5 [2.4, 4.6] | 3.4 | 6.4 | 4 | 2.9 | 7.1 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | fa_above_pr_with | 0.60 | 4.2 | 0.3 | 0.53 | 0.49 | 3.9 [3.2, 4.6] | 3.9 | 10.9 | 4 | 3.1 | 8.2 |
| ALL/0 | dl_poc_side_with | 0.68 | 3.8 | 0.3 | 0.52 | 0.50 | 3.5 [2.8, 4.3] | 3.5 | 9.4 | 4 | 7.7 | 8.4 |
| ALL/0 | fa_nl30_std_with | 0.14 | 6.0 | 2.1 | 0.57 | 0.51 | 3.9 [2.9, 4.8] | 3.8 | 7.7 | 4 | 1.2 | -10.2 |
| ALL/0 | wl_tdom_4_9 | 0.28 | 0.7 | 3.4 | 0.49 | 0.52 | -2.7 [-3.4, -1.9] | -2.6 | -6.8 | 4 | -2.6 | -9.2 |
| ALL/0 | dl_pd_neutral | 0.11 | 5.9 | 2.3 | 0.54 | 0.51 | 3.6 [2.5, 4.7] | 3.4 | 6.0 | 4 | 8.4 | 6.8 |
| ALL/0 | dl_pd_neutral_ext | 0.06 | 7.0 | 2.4 | 0.56 | 0.51 | 4.6 [3.1, 6.1] | 4.3 | 5.6 | 4 | 9.9 | 23.2 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | dl_pd_neutral | 0.11 | 6.1 | 0.6 | 0.54 | 0.49 | 5.5 [4.1, 6.8] | 5.4 | 7.9 | 4 | 15.7 | 5.6 |
| ALL/1 | dl_sp_ahead_120 | 0.08 | -4.0 | 1.7 | 0.46 | 0.50 | -5.8 [-7.3, -4.2] | -5.6 | -7.3 | 4 | -4.2 | -5.4 |
| ALL/1 | dl_sp_behind_120 | 0.05 | 7.2 | 1.0 | 0.56 | 0.50 | 6.2 [4.4, 8.0] | 6.0 | 6.5 | 4 | 46.4 | 25.5 |
| ALL/1 | dl_pd_neutral_ext | 0.06 | 5.3 | 1.0 | 0.54 | 0.50 | 4.3 [2.6, 6.1] | 4.2 | 4.7 | 4 | 11.8 | 8.7 |
| ALL/1 | cb_outside | 0.08 | 4.1 | 1.0 | 0.52 | 0.50 | 3.2 [1.6, 4.7] | 3.1 | 3.9 | 4 | 26.4 | 32.2 |
| ALL/1 | wl_tdom_seasonal_with | 0.50 | 0.9 | 2.1 | 0.50 | 0.51 | -1.2 [-2.1, -0.3] | -1.2 | -2.6 | 4 | -5.2 | -6.4 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | wl_smash_against | 0.29 | -8.9 | 2.7 | 0.42 | 0.52 | -11.6 [-14.2, -8.9] | -11.4 | -8.5 | 4 | -18.9 | -30.5 |
| ALL/2 | fa_nl30_std_with | 0.13 | -8.4 | 0.5 | 0.42 | 0.50 | -8.8 [-12.4, -5.3] | -8.6 | -4.8 | 4 | -16.1 | -50.8 |
| ALL/2 | wl_tdom_10_16 | 0.34 | -4.7 | 1.4 | 0.46 | 0.51 | -6.2 [-8.7, -3.6] | -6.1 | -4.7 | 4 | -13.2 | -30.4 |
| ALL/2 | fa_nl15_std_with | 0.22 | -5.9 | 0.8 | 0.44 | 0.51 | -6.8 [-9.6, -3.9] | -6.7 | -4.5 | 4 | -8.7 | -17.7 |
| ALL/2 | fa_nl60_std_with | 0.07 | -7.8 | -0.1 | 0.43 | 0.50 | -7.6 [-12.4, -2.9] | -7.4 | -3.1 | 4 | -4.9 | nan |
| ALL/2 | dl_pd_normal | 0.12 | 3.6 | -1.2 | 0.52 | 0.49 | 4.9 [1.3, 8.4] | 4.8 | 2.6 | 4 | 11.3 | 14.9 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | dl_pd_neutral | 0.11 | 11.4 | 0.3 | 0.58 | 0.48 | 11.1 [8.9, 13.3] | 10.1 | 8.9 | 4 | 16.2 | -5.8 |
| ALL/3 | dl_pd_neutral_ext | 0.06 | 13.6 | 0.7 | 0.60 | 0.49 | 12.9 [9.9, 15.8] | 11.1 | 7.4 | 4 | 11.4 | 6.7 |
| ALL/3 | cb_prior_wide | 0.13 | -5.0 | 2.5 | 0.44 | 0.50 | -7.5 [-9.6, -5.4] | -6.9 | -6.4 | 4 | -5.7 | 6.8 |
| ALL/3 | dl_open_outside_va | 0.65 | 3.2 | -0.7 | 0.51 | 0.47 | 3.9 [2.4, 5.4] | 3.7 | 4.8 | 4 | 1.8 | -7.8 |
| ALL/3 | dl_inside_va | 0.28 | -1.3 | 2.6 | 0.47 | 0.50 | -3.9 [-5.5, -2.3] | -3.7 | -4.7 | 4 | -12.9 | -7.1 |
| ALL/3 | cb_orb15_failed | 0.09 | -2.1 | 2.0 | 0.46 | 0.50 | -4.1 [-6.9, -1.4] | -3.6 | -2.6 | 4 | -1.9 | -1.9 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | dl_pd_neutral_ext | 0.07 | 14.0 | -1.3 | 0.61 | 0.48 | 15.3 [12.6, 18.0] | 14.1 | 10.3 | 4 | 9.0 | 24.1 |
| ALL/4 | wl_oops_with | 0.11 | -10.7 | 1.2 | 0.39 | 0.51 | -11.9 [-14.1, -9.7] | -11.3 | -10.1 | 4 | -12.5 | -28.2 |
| ALL/4 | dl_pd_neutral | 0.12 | 9.6 | -1.6 | 0.57 | 0.48 | 11.2 [9.2, 13.3] | 10.7 | 10.1 | 4 | 10.2 | 8.3 |
| ALL/4 | wl_volbo_std_hit | 0.49 | 3.4 | -3.5 | 0.52 | 0.46 | 6.9 [5.5, 8.2] | 6.7 | 9.8 | 4 | 15.3 | 24.9 |
| ALL/4 | wl_volbo_fast_hit | 0.69 | 2.1 | -5.0 | 0.51 | 0.45 | 7.0 [5.6, 8.5] | 6.9 | 9.2 | 4 | 17.0 | 22.7 |
| ALL/4 | wl_volbo_std_beyond | 0.39 | 3.9 | -2.7 | 0.53 | 0.47 | 6.6 [5.3, 8.0] | 6.5 | 9.2 | 4 | 17.5 | 27.0 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | cb_orb5_narrow | 0.31 | 5.5 | -4.8 | 0.54 | 0.45 | 10.3 [8.1, 12.6] | 9.8 | 8.5 | 4 | 18.5 | 26.6 |
| ALL/5 | fa_c_fast_with | 0.28 | -9.0 | 1.5 | 0.41 | 0.51 | -10.5 [-12.9, -8.1] | -9.9 | -8.1 | 4 | -18.4 | -10.8 |
| ALL/5 | wl_smash_with | 0.34 | 3.6 | -2.1 | 0.54 | 0.47 | 5.7 [4.0, 7.5] | 5.6 | 6.3 | 4 | 1.3 | 3.2 |
| ALL/5 | cb_orb15_beyond | 0.62 | -3.5 | 1.8 | 0.46 | 0.52 | -5.3 [-7.6, -3.1] | -5.0 | -4.4 | 4 | -19.3 | -21.0 |
| ALL/5 | cb_orb30_narrow | 0.32 | 2.1 | -3.2 | 0.50 | 0.47 | 5.3 [3.0, 7.5] | 5.0 | 4.3 | 4 | 0.1 | 11.4 |
| ALL/5 | dl_pd_normvar_with | 0.35 | 2.3 | -1.5 | 0.51 | 0.48 | 3.7 [2.0, 5.4] | 3.6 | 4.1 | 4 | 5.4 | 9.2 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B_sess_named.parquet

## Sub-block B2: the same opening-range systems re-anchored on the D7 session (asia, london, pre, nyam, nypm, close)

### B2 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 48 conditions; 1218 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 2 conditions with |t|>2 (chance alone: about 2). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | ss_gap_with | 0.37 | 161.2 | 73.7 | 0.45 | 0.43 | 87.6 [20.4, 154.8] | 24.6 | 2.6 | 4 | 30.5 | 169.1 |
| ALL/ALL | ss_orb15_against_beyond | 0.09 | -11.5 | 117.1 | 0.42 | 0.44 | -128.7 [-242.8, -14.6] | -15.3 | -2.2 | 3 | -258.0 | -307.8 |
| ALL/ALL | ss_a_std_now_against | 0.06 | -7.7 | 112.8 | 0.41 | 0.44 | -120.5 [-244.3, 3.3] | -12.4 | -1.9 | 3 | -276.5 | -497.2 |
| ALL/ALL | ss_a_slow_fresh30 | 0.14 | 165.2 | 82.0 | 0.46 | 0.43 | 83.2 [-9.3, 175.7] | 14.2 | 1.8 | 3 | 181.1 | 29.6 |
| ALL/ALL | ss_volbo_fast_hit | 0.59 | 129.0 | 72.5 | 0.44 | 0.43 | 56.5 [-7.9, 121.0] | 16.8 | 1.7 | 4 | 200.0 | 136.3 |
| ALL/ALL | ss_orb30_against_beyond | 0.08 | -1.4 | 102.1 | 0.41 | 0.44 | -103.6 [-225.1, 18.0] | -11.0 | -1.7 | 3 | -222.4 | -371.7 |
| ALL/ALL | ss_orb5_against_beyond | 0.11 | 27.6 | 115.6 | 0.42 | 0.44 | -87.9 [-193.8, 17.9] | -11.9 | -1.6 | 4 | -199.2 | -209.1 |
| ALL/ALL | ss_range_used_gt100 | 0.25 | 60.8 | 121.6 | 0.43 | 0.44 | -60.8 [-134.4, 12.9] | -14.9 | -1.6 | 3 | -127.9 | -161.1 |
| ALL/ALL | ss_a_fast_now_against | 0.08 | 19.9 | 113.9 | 0.42 | 0.44 | -93.9 [-207.9, 20.0] | -11.2 | -1.6 | 3 | -269.1 | -348.8 |
| ALL/ALL | ss_inside | 0.06 | 16.3 | 111.5 | 0.41 | 0.44 | -95.2 [-220.0, 29.7] | -9.7 | -1.5 | 3 | -150.5 | -49.0 |
| ALL/ALL | ss_volbo_std_hit | 0.39 | 135.7 | 87.1 | 0.44 | 0.43 | 48.6 [-16.8, 113.9] | 14.2 | 1.5 | 3 | 216.4 | 161.1 |
| ALL/ALL | ss_gap_against | 0.34 | 74.5 | 122.6 | 0.43 | 0.44 | -48.2 [-114.6, 18.2] | -13.7 | -1.4 | 3 | -102.0 | -186.2 |
| ALL/ALL | ss_orb30_beyond | 0.60 | 113.7 | 63.6 | 0.44 | 0.43 | 50.1 [-19.8, 120.0] | 13.3 | 1.4 | 4 | 117.3 | 139.8 |
| ALL/ALL | ss_orb30_fresh15 | 0.11 | 41.2 | 100.0 | 0.45 | 0.43 | -58.8 [-145.0, 27.4] | -11.3 | -1.3 | 3 | -9.5 | -201.7 |
| ALL/ALL | ss_a_slow_hit_with | 0.50 | 115.7 | 71.8 | 0.44 | 0.43 | 43.9 [-23.9, 111.6] | 12.2 | 1.3 | 3 | 131.0 | 140.8 |
| ALL/ALL | ss_volbo_fast_beyond | 0.46 | 127.6 | 87.5 | 0.44 | 0.43 | 40.2 [-23.3, 103.6] | 12.2 | 1.2 | 3 | 221.2 | 181.1 |
| ALL/ALL | ss_inor_std | 0.25 | 138.6 | 94.0 | 0.45 | 0.44 | 44.6 [-38.0, 127.2] | 9.1 | 1.1 | 3 | 29.7 | 105.5 |
| ALL/ALL | ss_inor_fast | 0.18 | 137.3 | 99.1 | 0.44 | 0.44 | 38.2 [-51.2, 127.5] | 6.9 | 0.8 | 3 | 129.4 | 108.6 |
| ALL/ALL | ss_a_slow_now_against | 0.05 | 42.9 | 96.2 | 0.41 | 0.44 | -53.2 [-200.0, 93.5] | -4.0 | -0.7 | 3 | -291.4 | -685.9 |
| ALL/ALL | ss_inor_slow | 0.32 | 80.3 | 99.9 | 0.43 | 0.44 | -19.6 [-94.1, 55.0] | -4.7 | -0.5 | 3 | -40.3 | -17.5 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | ss_volbo_fast_hit | 0.56 | 295.1 | 156.6 | 0.47 | 0.46 | 138.5 [-1.3, 278.2] | 41.6 | 0.6 | 4 | 231.1 | 163.3 |
| ALL/0 | ss_gap_with | 0.42 | 282.8 | 199.6 | 0.48 | 0.46 | 83.2 [-59.0, 225.5] | 24.4 | 0.3 | 4 | 163.3 | 307.1 |
| ALL/0 | ss_orb5_beyond | 0.64 | 265.8 | 179.1 | 0.47 | 0.46 | 86.7 [-62.0, 235.5] | 23.8 | 0.3 | 4 | 57.4 | 82.8 |
| ALL/0 | ss_orb5_against_beyond | 0.12 | 66.9 | 257.4 | 0.43 | 0.47 | -190.5 [-407.2, 26.1] | -28.9 | -0.3 | 4 | -335.4 | -272.6 |
| ALL/0 | ss_a_slow_fresh30 | 0.11 | 370.1 | 207.9 | 0.51 | 0.46 | 162.2 [-54.2, 378.6] | 24.6 | 0.2 | 4 | 143.6 | 69.8 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | ss_range_used_gt100 | 0.24 | -115.8 | 77.2 | 0.37 | 0.43 | -193.0 [-301.6, -84.4] | -22.5 | -0.4 | 4 | -258.4 | -523.7 |
| ALL/1 | ss_volbo_slow_hit | 0.18 | -132.4 | 66.7 | 0.36 | 0.42 | -199.1 [-319.2, -79.0] | -19.4 | -0.3 | 4 | -204.1 | -66.4 |
| ALL/1 | ss_volbo_slow_beyond | 0.12 | -154.2 | 56.2 | 0.36 | 0.42 | -210.4 [-354.3, -66.5] | -14.7 | -0.2 | 4 | -241.2 | -5.9 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | ss_volbo_std_hit | 0.50 | 78.7 | -22.8 | 0.44 | 0.40 | 101.5 [25.5, 177.4] | 46.7 | 1.2 | 4 | 318.7 | 179.5 |
| ALL/3 | ss_orb30_beyond | 0.55 | 45.3 | -48.5 | 0.43 | 0.41 | 93.8 [11.6, 176.1] | 39.5 | 0.9 | 4 | 258.3 | 46.2 |
| ALL/3 | ss_inor_slow | 0.43 | -49.0 | 42.8 | 0.41 | 0.43 | -91.9 [-174.5, -9.2] | -38.5 | -0.9 | 4 | -242.9 | -5.9 |
| ALL/3 | ss_a_slow_fresh30 | 0.18 | 115.7 | -21.6 | 0.45 | 0.41 | 137.4 [28.8, 245.9] | 40.5 | 0.7 | 4 | 102.9 | -193.4 |
| ALL/3 | ss_oops_with | 0.13 | -43.3 | 37.7 | 0.39 | 0.42 | -81.0 [-194.9, 32.8] | -22.3 | -0.4 | 4 | -169.6 | -117.5 |
| ALL/3 | ss_orb5_against_beyond | 0.04 | -152.4 | 35.2 | 0.40 | 0.42 | -187.6 [-357.1, -18.1] | -27.5 | -0.3 | 4 | -262.5 | -191.9 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | ss_gap_with | 0.37 | 114.5 | -8.5 | 0.47 | 0.44 | 123.0 [-30.5, 276.5] | 11.6 | 0.1 | 4 | 163.6 | 538.8 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | ss_volbo_slow_beyond | 0.27 | 227.8 | 71.4 | 0.57 | 0.50 | 156.3 [8.1, 304.6] | 0.0 | 2.1 | 3 | 389.4 | 586.4 |
| A7/0 | ss_volbo_slow_hit | 0.29 | 214.3 | 72.2 | 0.57 | 0.50 | 142.2 [-2.7, 287.0] | 0.0 | 1.9 | 3 | 396.3 | 564.5 |
| A7/0 | ss_range_used_lt50 | 0.26 | 212.1 | 79.0 | 0.57 | 0.50 | 133.2 [-16.8, 283.1] | 0.0 | 1.7 | 4 | 30.0 | -38.1 |
| A7/0 | ss_inor_fast | 0.13 | 50.0 | 122.9 | 0.49 | 0.53 | -72.9 [-272.0, 126.1] | -0.0 | -0.7 | 3 | -85.0 | 131.6 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | ss_orb15_failed | 0.10 | -44.7 | 252.9 | 0.44 | 0.49 | -297.5 [-852.9, 257.8] | -0.0 | -1.1 | 3 | -82.7 | -1105.1 |
| H7/0 | ss_range_used_gt100 | 0.19 | -15.4 | 255.0 | 0.43 | 0.49 | -270.4 [-803.1, 262.3] | -0.0 | -1.0 | 3 | -672.2 | -42.5 |
| H7/0 | ss_a_slow_now_with | 0.37 | 367.5 | 176.7 | 0.52 | 0.47 | 190.8 [-240.4, 622.0] | 0.0 | 0.9 | 3 | 239.8 | 362.5 |
| H7/0 | ss_stretch_beyond | 0.53 | 265.6 | 135.7 | 0.49 | 0.47 | 130.0 [-239.4, 499.3] | 0.0 | 0.7 | 3 | 267.5 | 306.4 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | ss_c_fast_with | 0.43 | -99.1 | 149.7 | 0.41 | 0.53 | -248.8 [-482.4, -15.2] | -96.0 | -2.1 | 4 | -609.2 | -105.2 |
| H7/3 | ss_volbo_fast_beyond | 0.58 | 136.1 | -85.6 | 0.52 | 0.43 | 221.8 [-12.3, 455.9] | 85.3 | 1.9 | 4 | 190.0 | 141.7 |
| H7/3 | ss_volbo_fast_hit | 0.70 | 110.2 | -116.6 | 0.50 | 0.42 | 226.8 [-25.4, 478.9] | 79.4 | 1.8 | 4 | 518.4 | 791.0 |
| H7/3 | ss_volbo_std_hit | 0.44 | 149.6 | -40.7 | 0.53 | 0.44 | 190.3 [-45.3, 425.9] | 72.6 | 1.6 | 3 | 668.8 | 977.4 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | ss_orb5_against_beyond | 0.16 | -79.8 | 125.1 | 0.38 | 0.46 | -204.9 [-339.5, -70.4] | -54.9 | -3.0 | 3 | -232.2 | -374.4 |
| K7/0 | ss_orb30_against_beyond | 0.15 | -62.9 | 143.2 | 0.39 | 0.46 | -206.1 [-354.6, -57.6] | -47.6 | -2.7 | 3 | -284.1 | -477.2 |
| K7/0 | ss_orb15_against_beyond | 0.15 | -41.6 | 122.4 | 0.40 | 0.46 | -164.0 [-307.6, -20.4] | -39.9 | -2.2 | 3 | -261.6 | -431.6 |
| K7/0 | ss_a_slow_now_against | 0.10 | -63.1 | 130.4 | 0.39 | 0.46 | -193.5 [-373.0, -14.0] | -33.0 | -2.1 | 3 | -252.3 | -515.3 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | ss_a_slow_fresh30 | 0.11 | 146.6 | 11.2 | 0.48 | 0.42 | 135.4 [-74.4, 345.2] | 0.0 | 1.3 | 4 | 269.4 | 366.5 |
| K7/1 | ss_range_used_lt50 | 0.29 | 89.4 | 8.1 | 0.45 | 0.42 | 81.2 [-48.7, 211.2] | 0.0 | 1.2 | 3 | 33.2 | -73.5 |
| K7/1 | ss_nr4 | 0.24 | -23.2 | 49.2 | 0.40 | 0.43 | -72.4 [-211.4, 66.7] | -0.0 | -1.0 | 3 | -133.5 | -89.2 |
| K7/1 | ss_volbo_slow_hit | 0.19 | -32.2 | 46.5 | 0.40 | 0.43 | -78.7 [-230.7, 73.2] | -0.0 | -1.0 | 3 | -24.7 | 218.4 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | ss_volbo_fast_beyond | 0.51 | 60.3 | -41.7 | 0.45 | 0.40 | 102.0 [1.9, 202.0] | 0.0 | 2.0 | 4 | 257.4 | 360.4 |
| K7/3 | ss_a_std_fresh30 | 0.22 | 101.1 | -14.9 | 0.46 | 0.42 | 115.9 [-6.1, 238.0] | 0.0 | 1.9 | 4 | 59.9 | -121.3 |
| K7/3 | ss_c_std_with | 0.09 | 142.2 | -2.9 | 0.49 | 0.42 | 145.1 [-34.4, 324.5] | 0.0 | 1.6 | 3 | 161.1 | -108.0 |
| K7/3 | ss_volbo_fast_hit | 0.62 | 40.5 | -39.2 | 0.44 | 0.40 | 79.7 [-22.8, 182.3] | 0.0 | 1.5 | 3 | 196.1 | 249.9 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | ss_volbo_std_beyond | 0.30 | 182.5 | -26.2 | 0.49 | 0.43 | 208.8 [42.5, 375.0] | 17.0 | 2.5 | 3 | 139.4 | 252.0 |
| K7/4 | ss_volbo_std_hit | 0.39 | 154.5 | -36.8 | 0.50 | 0.42 | 191.3 [38.8, 343.7] | 18.2 | 2.5 | 3 | 51.2 | 119.6 |
| K7/4 | ss_volbo_fast_beyond | 0.49 | 108.2 | -32.2 | 0.47 | 0.43 | 140.4 [-5.5, 286.3] | 14.5 | 1.9 | 3 | 315.8 | 662.6 |
| K7/4 | ss_gap_with | 0.37 | 114.5 | -8.5 | 0.47 | 0.44 | 123.0 [-30.5, 276.5] | 11.6 | 1.6 | 4 | 163.6 | 538.8 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | ss_range_used_gt100 | 0.22 | -152.5 | 29.8 | 0.36 | 0.41 | -182.3 [-327.6, -37.1] | -0.0 | -2.5 | 4 | -160.7 | -170.1 |
| M7/1 | ss_volbo_std_hit | 0.34 | -109.1 | 40.6 | 0.38 | 0.41 | -149.7 [-275.2, -24.2] | -0.0 | -2.3 | 4 | -37.0 | -107.6 |
| M7/1 | ss_volbo_slow_beyond | 0.13 | -197.4 | 18.1 | 0.35 | 0.41 | -215.5 [-401.4, -29.7] | -0.0 | -2.3 | 4 | -216.7 | 15.8 |
| M7/1 | ss_stretch_beyond | 0.53 | -72.0 | 56.7 | 0.38 | 0.42 | -128.6 [-240.9, -16.4] | -0.0 | -2.2 | 4 | -121.0 | -220.8 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | ss_a_slow_now_with | 0.34 | 110.4 | -8.5 | 0.47 | 0.41 | 118.9 [8.5, 229.4] | 0.0 | 2.1 | 4 | 149.7 | 113.5 |
| M7/3 | ss_oops_with | 0.15 | -76.2 | 60.9 | 0.37 | 0.45 | -137.1 [-277.8, 3.5] | -0.0 | -1.9 | 3 | -226.2 | -75.9 |
| M7/3 | ss_a_slow_hit_with | 0.47 | 86.2 | -15.0 | 0.46 | 0.41 | 101.2 [-3.3, 205.7] | 0.0 | 1.9 | 4 | 179.1 | 49.6 |
| M7/3 | ss_volbo_fast_hit | 0.78 | 64.9 | -48.7 | 0.45 | 0.39 | 113.6 [-9.1, 236.3] | 0.0 | 1.8 | 3 | 317.7 | 510.7 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | ss_volbo_std_hit | 0.32 | 174.3 | 176.9 | 0.37 | 0.37 | -2.6 [-231.0, 225.7] | -0.0 | -0.0 | 3 | -431.3 | -209.0 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | ss_gap_against | 0.33 | 129.7 | 572.6 | 0.40 | 0.46 | -443.0 [-851.4, -34.5] | -0.0 | -2.1 | 3 | -709.1 | -1082.1 |
| P7/0 | ss_volbo_std_hit | 0.36 | 643.2 | 301.9 | 0.43 | 0.44 | 341.3 [-75.0, 757.6] | 0.0 | 1.6 | 4 | 439.5 | 307.8 |
| P7/0 | ss_volbo_fast_hit | 0.54 | 566.5 | 258.9 | 0.43 | 0.45 | 307.6 [-85.0, 700.3] | 0.0 | 1.5 | 4 | 206.8 | -144.3 |
| P7/0 | ss_range_used_gt150 | 0.12 | 19.6 | 478.1 | 0.39 | 0.45 | -458.5 [-1051.6, 134.6] | -0.0 | -1.5 | 3 | -993.5 | 53.7 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | ss_volbo_slow_hit | 0.22 | -248.6 | 118.4 | 0.32 | 0.40 | -367.1 [-655.9, -78.2] | -0.0 | -2.5 | 4 | -523.5 | -521.4 |
| P7/1 | ss_range_used_gt100 | 0.27 | -193.7 | 122.9 | 0.33 | 0.40 | -316.6 [-577.8, -55.3] | -0.0 | -2.4 | 3 | -694.9 | -991.1 |
| P7/1 | ss_volbo_slow_beyond | 0.14 | -243.4 | 83.7 | 0.32 | 0.39 | -327.1 [-682.3, 28.2] | -0.0 | -1.8 | 3 | -332.8 | -263.7 |
| P7/1 | ss_nr4 | 0.24 | -88.2 | 76.8 | 0.36 | 0.39 | -165.0 [-428.7, 98.7] | -0.0 | -1.2 | 4 | -28.6 | 414.1 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | ss_a_slow_fresh30 | 0.17 | 301.4 | -119.7 | 0.44 | 0.37 | 421.1 [53.5, 788.7] | 195.8 | 2.2 | 4 | 36.2 | -670.0 |
| P7/3 | ss_gap_with | 0.28 | 210.8 | -130.0 | 0.43 | 0.37 | 340.8 [33.9, 647.7] | 189.1 | 2.2 | 3 | 370.5 | 822.7 |
| P7/3 | ss_stretch_hit | 0.89 | 6.1 | -356.1 | 0.39 | 0.36 | 362.2 [-2.2, 726.6] | 170.0 | 1.9 | 3 | 797.6 | 500.8 |
| P7/3 | ss_a_fast_hit_with | 0.88 | 8.8 | -338.7 | 0.39 | 0.37 | 347.5 [-2.7, 697.7] | 170.0 | 1.9 | 4 | 752.3 | 545.9 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | ss_orb30_against_beyond | 0.10 | -283.6 | 447.9 | 0.48 | 0.53 | -731.5 [-1612.1, 149.1] | -0.0 | -1.6 | 3 | -905.1 | -80.7 |
| U7/0 | ss_nr4 | 0.24 | 684.2 | 289.8 | 0.57 | 0.51 | 394.4 [-200.0, 988.9] | 0.0 | 1.3 | 3 | 29.2 | 24.2 |
| U7/0 | ss_orb15_against_beyond | 0.12 | -111.7 | 425.7 | 0.50 | 0.53 | -537.3 [-1377.2, 302.5] | -0.0 | -1.3 | 3 | -949.5 | -155.5 |
| U7/0 | ss_orb5_against_beyond | 0.13 | -37.1 | 449.0 | 0.50 | 0.53 | -486.1 [-1254.9, 282.6] | -0.0 | -1.2 | 3 | -505.2 | 533.6 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | ss_a_fast_fresh30 | 0.35 | -279.2 | 382.2 | 0.46 | 0.53 | -661.4 [-1171.0, -151.9] | -0.0 | -2.5 | 4 | -340.4 | 505.5 |
| U7/1 | ss_orb15_fresh15 | 0.20 | -325.5 | 295.9 | 0.48 | 0.52 | -621.5 [-1221.0, -22.0] | -0.0 | -2.0 | 3 | -68.3 | 1251.8 |
| U7/1 | ss_nr4 | 0.25 | 351.8 | 81.7 | 0.57 | 0.49 | 270.1 [-280.2, 820.4] | 0.0 | 1.0 | 3 | 1245.3 | 911.7 |
| U7/1 | ss_c_std_with | 0.36 | 53.3 | 235.0 | 0.49 | 0.52 | -181.6 [-715.1, 351.8] | -0.0 | -0.7 | 3 | -449.5 | -856.9 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B2_sessanch_named.parquet

### B2 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 48 conditions; 2235 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 42 conditions with |t|>2 (chance alone: about 2). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | ss_volbo_std_hit | 0.40 | 2.9 | 0.4 | 0.52 | 0.49 | 2.5 [2.0, 2.9] | 2.4 | 10.2 | 4 | 4.0 | 3.0 |
| ALL/ALL | ss_gap_with | 0.41 | 2.7 | 0.5 | 0.52 | 0.49 | 2.3 [1.8, 2.7] | 2.2 | 9.5 | 4 | 1.5 | 2.0 |
| ALL/ALL | ss_volbo_fast_beyond | 0.48 | 2.5 | 0.4 | 0.52 | 0.49 | 2.2 [1.7, 2.6] | 2.1 | 9.1 | 4 | 4.5 | 2.4 |
| ALL/ALL | ss_volbo_fast_hit | 0.61 | 2.2 | 0.1 | 0.51 | 0.49 | 2.1 [1.6, 2.5] | 2.0 | 8.6 | 4 | 3.1 | -0.0 |
| ALL/ALL | ss_volbo_slow_hit | 0.21 | 3.4 | 0.9 | 0.52 | 0.50 | 2.5 [1.9, 3.1] | 2.4 | 8.5 | 4 | 6.2 | 6.6 |
| ALL/ALL | ss_a_slow_hit_with | 0.53 | 2.4 | 0.4 | 0.51 | 0.49 | 2.0 [1.5, 2.5] | 1.9 | 8.1 | 3 | 3.4 | 5.1 |
| ALL/ALL | ss_volbo_slow_beyond | 0.16 | 3.6 | 1.0 | 0.52 | 0.50 | 2.6 [1.9, 3.2] | 2.5 | 7.8 | 4 | 5.2 | 7.0 |
| ALL/ALL | ss_a_slow_now_with | 0.41 | 2.6 | 0.7 | 0.52 | 0.49 | 1.9 [1.4, 2.4] | 1.9 | 7.6 | 3 | 1.0 | 1.8 |
| ALL/ALL | ss_c_slow_with | 0.10 | 4.2 | 1.2 | 0.53 | 0.50 | 3.0 [2.2, 3.9] | 2.8 | 6.9 | 3 | 1.0 | 6.3 |
| ALL/ALL | ss_volbo_std_beyond | 0.31 | 2.6 | 0.9 | 0.52 | 0.50 | 1.7 [1.2, 2.2] | 1.7 | 6.6 | 4 | 4.3 | 4.3 |
| ALL/ALL | ss_a_std_now_with | 0.53 | 2.1 | 0.6 | 0.51 | 0.49 | 1.5 [1.0, 2.0] | 1.5 | 6.2 | 3 | 1.8 | 2.6 |
| ALL/ALL | ss_stretch_beyond | 0.58 | 2.0 | 0.5 | 0.51 | 0.49 | 1.5 [1.0, 1.9] | 1.4 | 6.2 | 4 | 1.4 | 0.4 |
| ALL/ALL | ss_gap_against | 0.34 | 0.4 | 1.9 | 0.49 | 0.51 | -1.4 [-1.9, -1.0] | -1.4 | -5.9 | 4 | -3.0 | -3.6 |
| ALL/ALL | ss_orb30_beyond | 0.64 | 2.0 | 0.5 | 0.51 | 0.49 | 1.5 [1.0, 2.0] | 1.5 | 5.8 | 3 | 2.4 | 4.3 |
| ALL/ALL | ss_orb15_against_beyond | 0.07 | -0.9 | 1.6 | 0.47 | 0.51 | -2.5 [-3.4, -1.6] | -2.3 | -5.4 | 3 | -5.4 | -4.8 |
| ALL/ALL | ss_nr7 | 0.14 | -0.1 | 1.6 | 0.49 | 0.50 | -1.7 [-2.4, -1.1] | -1.6 | -5.2 | 3 | -1.9 | -1.2 |
| ALL/ALL | ss_a_std_now_against | 0.05 | -1.3 | 1.5 | 0.47 | 0.50 | -2.9 [-4.0, -1.7] | -2.5 | -4.9 | 3 | -5.7 | -10.9 |
| ALL/ALL | ss_stretch_hit | 0.72 | 1.7 | 0.5 | 0.51 | 0.49 | 1.2 [0.7, 1.7] | 1.2 | 4.8 | 4 | 2.0 | -0.2 |
| ALL/ALL | ss_orb30_fresh15 | 0.09 | -0.4 | 1.6 | 0.48 | 0.50 | -2.1 [-2.9, -1.2] | -1.9 | -4.5 | 4 | -2.2 | -9.0 |
| ALL/ALL | ss_a_fast_now_with | 0.63 | 1.8 | 0.7 | 0.51 | 0.49 | 1.0 [0.6, 1.5] | 1.0 | 4.3 | 3 | 2.3 | 2.3 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | ss_volbo_std_hit | 0.40 | 5.0 | 1.3 | 0.54 | 0.50 | 3.7 [3.0, 4.4] | 3.7 | 10.1 | 4 | 4.8 | 1.9 |
| ALL/0 | ss_volbo_slow_hit | 0.22 | 6.2 | 1.8 | 0.55 | 0.51 | 4.4 [3.6, 5.3] | 4.3 | 9.8 | 4 | 13.3 | 16.3 |
| ALL/0 | ss_volbo_std_beyond | 0.30 | 5.0 | 1.8 | 0.54 | 0.50 | 3.2 [2.4, 3.9] | 3.1 | 7.9 | 4 | 7.5 | 5.4 |
| ALL/0 | ss_oops_against | 0.06 | -1.4 | 3.0 | 0.47 | 0.52 | -4.4 [-6.0, -2.9] | -4.0 | -5.1 | 4 | -8.5 | -9.5 |
| ALL/0 | ss_gap_with | 0.42 | 3.7 | 2.0 | 0.53 | 0.51 | 1.7 [1.0, 2.4] | 1.7 | 4.7 | 4 | 0.7 | 2.1 |
| ALL/0 | ss_orb30_failed | 0.10 | 0.7 | 3.0 | 0.49 | 0.52 | -2.3 [-3.5, -1.1] | -2.2 | -3.7 | 4 | -2.6 | -4.4 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | ss_range_used_gt100 | 0.18 | 4.2 | 0.6 | 0.52 | 0.50 | 3.6 [2.4, 4.8] | 3.4 | 5.5 | 4 | 1.9 | -2.7 |
| ALL/1 | ss_volbo_slow_hit | 0.16 | 3.8 | 0.8 | 0.52 | 0.50 | 3.1 [1.8, 4.3] | 2.9 | 4.6 | 4 | 1.1 | 3.1 |
| ALL/1 | ss_inside | 0.04 | -2.1 | 1.4 | 0.47 | 0.50 | -3.5 [-5.8, -1.3] | -2.8 | -2.5 | 4 | -8.2 | -6.1 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | ss_orb5_beyond | 0.69 | -3.0 | 3.4 | 0.47 | 0.53 | -6.4 [-9.3, -3.6] | -5.9 | -4.1 | 4 | -4.5 | -10.6 |
| ALL/2 | ss_a_fast_hit_with | 0.71 | -2.8 | 3.5 | 0.48 | 0.52 | -6.4 [-9.2, -3.5] | -5.8 | -3.9 | 4 | -8.5 | -12.3 |
| ALL/2 | ss_inor_fast | 0.30 | 3.1 | -2.8 | 0.52 | 0.48 | 5.8 [3.0, 8.7] | 5.3 | 3.6 | 4 | 0.4 | 6.1 |
| ALL/2 | ss_a_fast_now_with | 0.56 | -3.0 | 1.5 | 0.48 | 0.51 | -4.5 [-7.2, -1.9] | -4.2 | -3.1 | 4 | -4.6 | -7.7 |
| ALL/2 | ss_volbo_slow_hit | 0.29 | -4.3 | 0.4 | 0.47 | 0.50 | -4.7 [-7.6, -1.8] | -4.3 | -2.9 | 4 | -3.7 | -15.8 |
| ALL/2 | ss_inor_std | 0.46 | 0.5 | -2.6 | 0.50 | 0.48 | 3.1 [0.2, 6.0] | 2.8 | 1.9 | 4 | 2.9 | 7.0 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | ss_volbo_std_hit | 0.50 | 4.5 | -1.2 | 0.52 | 0.47 | 5.6 [4.2, 7.1] | 5.4 | 7.2 | 4 | 7.2 | 4.5 |
| ALL/3 | ss_orb15_failed | 0.09 | -2.2 | 1.8 | 0.46 | 0.50 | -3.9 [-6.6, -1.2] | -3.4 | -2.5 | 4 | -1.1 | -1.5 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | ss_gap_with | 0.47 | 4.0 | -4.1 | 0.53 | 0.46 | 8.2 [6.8, 9.6] | 7.6 | 10.9 | 4 | 15.2 | 21.6 |
| ALL/4 | ss_oops_with | 0.08 | -9.1 | 0.5 | 0.41 | 0.50 | -9.7 [-12.1, -7.2] | -7.8 | -6.3 | 4 | -14.3 | -20.2 |
| ALL/4 | ss_gap_against | 0.26 | -3.5 | 0.9 | 0.46 | 0.50 | -4.4 [-5.9, -2.8] | -4.0 | -5.0 | 4 | -8.3 | -16.0 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | ss_c_fast_with | 0.30 | 3.0 | -1.6 | 0.53 | 0.48 | 4.6 [2.8, 6.5] | 2.5 | 2.6 | 4 | 1.8 | -1.4 |
| ALL/5 | ss_inor_std | 0.30 | -2.8 | 1.0 | 0.47 | 0.50 | -3.8 [-5.8, -1.9] | -1.9 | -1.9 | 4 | -5.7 | -6.5 |
| ALL/5 | ss_range_used_gt150 | 0.09 | 3.7 | -0.6 | 0.50 | 0.49 | 4.3 [1.2, 7.5] | 1.2 | 0.7 | 4 | 2.9 | -14.0 |
| ALL/5 | ss_c_slow_with | 0.05 | 7.0 | 0.1 | 0.59 | 0.49 | 6.9 [2.0, 11.8] | 1.0 | 0.4 | 4 | 19.4 | 27.3 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B2_sessanch_named.parquet

## Sub-block C1: execution-desk levels, seasonality, volume-by-time curve

### C1 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 34 conditions; 835 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 1 conditions with |t|>2 (chance alone: about 1). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | ex_mv_with | 0.86 | 124.4 | -14.3 | 0.44 | 0.41 | 138.7 [60.6, 216.9] | 0.0 | 3.5 | 4 | 141.0 | 310.0 |
| ALL/ALL | ex_ss_arrival_against1 | 0.08 | 10.7 | 114.7 | 0.42 | 0.44 | -104.0 [-219.6, 11.6] | -0.0 | -1.8 | 3 | -267.5 | -332.2 |
| ALL/ALL | ex_gx_twap_side | 0.81 | 118.5 | 51.1 | 0.44 | 0.42 | 67.4 [-8.5, 143.3] | 0.0 | 1.7 | 4 | 5.8 | 213.8 |
| ALL/ALL | ex_seas120_strong_against | 0.14 | 172.5 | 95.3 | 0.46 | 0.43 | 77.2 [-11.6, 165.9] | 0.0 | 1.7 | 3 | 163.1 | 150.7 |
| ALL/ALL | ex_range30_lo | 0.20 | 142.5 | 82.7 | 0.44 | 0.43 | 59.8 [-23.4, 143.1] | 0.0 | 1.4 | 4 | 186.0 | 89.8 |
| ALL/ALL | ex_gx_arrival_against1 | 0.18 | 68.6 | 114.0 | 0.43 | 0.44 | -45.4 [-117.0, 26.3] | -0.0 | -1.2 | 3 | -116.2 | -167.3 |
| ALL/ALL | ex_gx_vwap_ext1_against | 0.05 | 54.1 | 108.7 | 0.42 | 0.44 | -54.6 [-152.9, 43.8] | -0.0 | -1.1 | 4 | -56.9 | -286.3 |
| ALL/ALL | ex_gx_vwap_side | 0.85 | 113.3 | 64.6 | 0.44 | 0.43 | 48.7 [-39.2, 136.6] | 0.0 | 1.1 | 4 | 4.1 | 237.6 |
| ALL/ALL | ex_ss_vwap_ext1_with | 0.49 | 123.2 | 91.0 | 0.44 | 0.43 | 32.2 [-31.8, 96.2] | 0.0 | 1.0 | 4 | 19.3 | 7.4 |
| ALL/ALL | ex_gx_twap_vwap_with | 0.44 | 116.1 | 97.6 | 0.44 | 0.43 | 18.5 [-44.1, 81.1] | 0.0 | 0.6 | 3 | 5.1 | 112.4 |
| ALL/ALL | ex_volcurve_behind | 0.23 | 117.6 | 102.2 | 0.44 | 0.44 | 15.4 [-62.0, 92.8] | 0.0 | 0.4 | 4 | 49.3 | 158.2 |
| ALL/ALL | ex_volcurve_ahead_move_with | 0.28 | 103.1 | 106.9 | 0.43 | 0.44 | -3.8 [-72.6, 65.0] | -0.0 | -0.1 | 3 | -67.7 | -9.6 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | ex_mv_with | 0.84 | 274.6 | 2.5 | 0.47 | 0.42 | 272.0 [106.9, 437.2] | 0.0 | 0.0 | 4 | 146.4 | 410.1 |
| ALL/0 | ex_gx_vwap_ext1_with | 0.39 | 326.6 | 182.3 | 0.49 | 0.45 | 144.3 [-0.9, 289.5] | 0.0 | 0.0 | 4 | 144.7 | 41.9 |
| ALL/0 | ex_ss_vwap_ext1_with | 0.39 | 326.6 | 182.3 | 0.49 | 0.45 | 144.3 [-0.9, 289.5] | 0.0 | 0.0 | 4 | 144.7 | 41.9 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | ex_mv_with | 0.89 | 42.8 | -87.0 | 0.42 | 0.37 | 129.8 [23.8, 235.8] | 95.5 | 1.8 | 4 | 201.4 | 295.0 |
| ALL/1 | ex_seas120_strong_against | 0.12 | 168.1 | 12.2 | 0.44 | 0.41 | 155.9 [14.4, 297.4] | 95.0 | 1.3 | 4 | 8.3 | 9.7 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | ex_ss_arrival_against1 | 0.04 | -170.8 | 35.7 | 0.39 | 0.42 | -206.4 [-370.8, -42.1] | -0.0 | -0.0 | 4 | -328.9 | -349.3 |
| ALL/3 | ex_seas30_strong_against | 0.15 | 46.9 | 23.9 | 0.42 | 0.42 | 23.0 [-82.4, 128.4] | 0.0 | 0.0 | 4 | 29.1 | -54.1 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | ex_gx_vwap_ext2_with | 0.35 | 167.3 | 4.9 | 0.49 | 0.44 | 162.4 [4.2, 320.6] | 9.4 | 0.1 | 4 | 446.1 | 655.8 |
| ALL/4 | ex_gx_vwap_ext1_with | 0.51 | 95.3 | 26.8 | 0.46 | 0.45 | 68.5 [-72.6, 209.6] | 4.9 | 0.1 | 4 | 31.9 | 439.8 |
| ALL/4 | ex_gx_arrival_with1 | 0.52 | 94.4 | 26.6 | 0.46 | 0.45 | 67.7 [-73.5, 209.0] | 4.8 | 0.1 | 4 | 145.0 | 249.3 |
| ALL/4 | ex_seas120_strong_with | 0.13 | -102.2 | 86.5 | 0.38 | 0.47 | -188.7 [-400.8, 23.3] | -6.2 | -0.1 | 4 | -400.8 | -907.2 |
| ALL/4 | ex_seas120_strong_against | 0.12 | 243.5 | 37.9 | 0.53 | 0.45 | 205.6 [-20.7, 432.0] | 6.0 | 0.1 | 4 | 623.1 | 428.2 |
| ALL/4 | ex_volcurve_sess_behind | 0.19 | -16.0 | 60.0 | 0.45 | 0.46 | -76.0 [-253.4, 101.4] | -3.5 | -0.0 | 4 | -77.0 | 308.3 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | ex_seas120_strong_against | 0.17 | 283.0 | 81.7 | 0.60 | 0.51 | 201.3 [26.2, 376.4] | 26.8 | 2.3 | 4 | 164.9 | -11.1 |
| A7/0 | ex_gx_vwap_ext2_with | 0.26 | 199.7 | 82.0 | 0.56 | 0.51 | 117.6 [-33.4, 268.7] | 20.1 | 1.5 | 3 | 172.0 | 275.1 |
| A7/0 | ex_ss_vwap_ext2_with | 0.26 | 199.7 | 82.0 | 0.56 | 0.51 | 117.6 [-33.4, 268.7] | 20.1 | 1.5 | 3 | 172.0 | 275.1 |
| A7/0 | ex_seas120_strong_with | 0.18 | 18.2 | 136.0 | 0.48 | 0.53 | -117.8 [-288.2, 52.6] | -16.4 | -1.4 | 3 | -370.8 | -175.8 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | ex_volcurve_ahead | 0.24 | -105.5 | 318.8 | 0.39 | 0.51 | -424.3 [-876.6, 28.0] | -0.0 | -1.8 | 4 | -643.7 | -344.6 |
| H7/0 | ex_volcurve_sess_ahead | 0.24 | -111.1 | 303.4 | 0.40 | 0.50 | -414.5 [-866.6, 37.6] | -0.0 | -1.8 | 4 | -745.3 | -344.6 |
| H7/0 | ex_volcurve_ahead_move_with | 0.24 | -89.8 | 311.5 | 0.40 | 0.51 | -401.3 [-856.5, 53.9] | -0.0 | -1.7 | 4 | -643.7 | -344.6 |
| H7/0 | ex_gx_vwap_ext1_with | 0.31 | 455.1 | 102.2 | 0.51 | 0.47 | 353.0 [-87.5, 793.5] | 0.0 | 1.6 | 3 | 362.8 | 564.3 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | ex_ss_twap_vwap_with | 0.68 | 88.3 | -52.8 | 0.49 | 0.45 | 141.1 [-107.4, 389.6] | 0.0 | 1.1 | 3 | 332.0 | 305.9 |
| H7/3 | ex_gx_vwap_ext1_with | 0.76 | 75.5 | -61.5 | 0.50 | 0.43 | 137.1 [-130.1, 404.2] | 0.0 | 1.0 | 3 | 260.1 | 72.7 |
| H7/3 | ex_gx_arrival_with1 | 0.72 | 78.0 | -49.6 | 0.49 | 0.44 | 127.6 [-131.2, 386.4] | 0.0 | 1.0 | 3 | 161.6 | 229.5 |
| H7/3 | ex_seas30_with | 0.47 | 58.0 | 28.6 | 0.49 | 0.47 | 29.5 [-204.7, 263.6] | 0.0 | 0.2 | 3 | 170.0 | 389.5 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | ex_mv_large2 | 0.43 | 197.1 | 8.7 | 0.48 | 0.42 | 188.4 [82.9, 293.9] | 99.9 | 3.5 | 4 | 81.7 | 105.1 |
| K7/0 | ex_mv_with_large | 0.38 | 208.5 | 18.2 | 0.48 | 0.42 | 190.3 [79.7, 300.8] | 96.5 | 3.4 | 4 | 39.5 | 134.3 |
| K7/0 | ex_mv_pullback_hold | 0.38 | 208.5 | 18.2 | 0.48 | 0.42 | 190.3 [79.7, 300.8] | 96.5 | 3.4 | 4 | 39.5 | 134.3 |
| K7/0 | ex_mv_with | 0.72 | 127.0 | -6.9 | 0.45 | 0.42 | 133.9 [27.0, 240.8] | 70.2 | 2.5 | 4 | 53.5 | 162.1 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | ex_mv_large2 | 0.69 | 70.0 | -48.6 | 0.44 | 0.39 | 118.6 [4.7, 232.5] | 0.0 | 2.0 | 4 | 100.6 | 80.3 |
| K7/1 | ex_mv_with | 0.76 | 61.9 | -58.1 | 0.44 | 0.39 | 120.0 [-4.2, 244.2] | 0.0 | 1.9 | 3 | 233.0 | 316.4 |
| K7/1 | ex_range30_lo | 0.17 | 134.9 | 15.9 | 0.49 | 0.41 | 119.0 [-45.1, 283.2] | 0.0 | 1.4 | 3 | 198.6 | 94.0 |
| K7/1 | ex_mv_with_large | 0.62 | 61.3 | -13.6 | 0.44 | 0.41 | 74.9 [-39.1, 188.9] | 0.0 | 1.3 | 4 | 166.3 | 272.3 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | ex_mv_large2 | 0.85 | 26.1 | -76.3 | 0.43 | 0.38 | 102.5 [-36.6, 241.6] | 0.0 | 1.4 | 3 | 547.1 | 598.5 |
| K7/3 | ex_volcurve_sess_ahead | 0.24 | -53.6 | 30.3 | 0.39 | 0.44 | -83.9 [-200.1, 32.3] | -0.0 | -1.4 | 3 | -265.0 | -471.6 |
| K7/3 | ex_gx_vwap_ext1_with | 0.62 | 34.7 | -29.7 | 0.44 | 0.41 | 64.4 [-38.4, 167.3] | 0.0 | 1.2 | 3 | 172.4 | 81.4 |
| K7/3 | ex_ss_arrival_with1 | 0.63 | 29.3 | -22.9 | 0.43 | 0.41 | 52.2 [-51.5, 155.8] | 0.0 | 1.0 | 3 | 207.4 | 118.1 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | ex_gx_vwap_ext2_with | 0.35 | 167.3 | 4.9 | 0.49 | 0.44 | 162.4 [4.2, 320.6] | 9.4 | 2.0 | 4 | 446.1 | 655.8 |
| K7/4 | ex_seas120_strong_against | 0.12 | 243.5 | 37.9 | 0.53 | 0.45 | 205.6 [-20.7, 432.0] | 6.0 | 1.8 | 4 | 623.1 | 428.2 |
| K7/4 | ex_seas120_strong_with | 0.13 | -102.2 | 86.5 | 0.38 | 0.47 | -188.7 [-400.8, 23.3] | -6.2 | -1.7 | 4 | -400.8 | -907.2 |
| K7/4 | ex_ss_twap_side | 0.96 | 39.0 | 227.6 | 0.45 | 0.58 | -188.6 [-486.2, 108.9] | -3.2 | -1.2 | 3 | -85.8 | 1567.5 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | ex_mv_with | 0.96 | 6.2 | -300.0 | 0.41 | 0.25 | 306.2 [110.5, 501.8] | 0.0 | 3.1 | 3 | 356.6 | 705.0 |
| M7/1 | ex_range30_lo | 0.22 | 116.4 | -36.3 | 0.46 | 0.39 | 152.7 [22.3, 283.1] | 0.0 | 2.3 | 4 | 176.4 | -3.3 |
| M7/1 | ex_ss_arrival_with1 | 0.60 | -68.5 | 49.3 | 0.38 | 0.42 | -117.9 [-232.6, -3.2] | -0.0 | -2.0 | 3 | -163.4 | -279.5 |
| M7/1 | ex_seas30_with | 0.49 | 41.8 | -46.6 | 0.42 | 0.39 | 88.3 [-17.0, 193.7] | 0.0 | 1.6 | 4 | 97.9 | 27.3 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | ex_seas30_strong_with | 0.14 | 175.1 | 17.7 | 0.51 | 0.42 | 157.4 [6.9, 307.9] | 0.0 | 2.1 | 4 | 263.1 | 233.9 |
| M7/3 | ex_seas120_strong_with | 0.14 | 159.3 | 21.2 | 0.50 | 0.43 | 138.1 [-16.8, 293.0] | 0.0 | 1.7 | 4 | 467.6 | 633.1 |
| M7/3 | ex_seas30_strong_against | 0.15 | -63.5 | 58.3 | 0.38 | 0.45 | -121.9 [-263.3, 19.6] | -0.0 | -1.7 | 3 | -11.0 | -95.9 |
| M7/3 | ex_gx_vwap_ext1_with | 0.85 | 22.6 | 141.9 | 0.43 | 0.48 | -119.2 [-265.5, 27.1] | -0.0 | -1.6 | 4 | -180.9 | 43.2 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | ex_seas30_with | 0.49 | 248.7 | 107.2 | 0.40 | 0.35 | 141.4 [-70.8, 353.6] | 0.0 | 1.3 | 3 | 334.5 | 253.2 |
| O7/3 | ex_gx_arrival_against1 | 0.29 | 101.4 | 206.9 | 0.33 | 0.39 | -105.5 [-337.0, 126.0] | -0.0 | -0.9 | 3 | -512.9 | -1051.2 |
| O7/3 | ex_gx_twap_vwap_with | 0.42 | 136.6 | 205.0 | 0.36 | 0.39 | -68.4 [-282.6, 145.8] | -0.0 | -0.6 | 3 | -519.0 | -568.9 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | ex_mv_with | 0.84 | 500.9 | -22.6 | 0.44 | 0.41 | 523.5 [29.7, 1017.3] | 0.0 | 2.1 | 4 | 211.6 | 876.3 |
| P7/0 | ex_mv_vwap_side | 0.81 | 491.6 | 90.0 | 0.44 | 0.43 | 401.6 [-75.2, 878.4] | 0.0 | 1.7 | 3 | 352.2 | 1362.0 |
| P7/0 | ex_range30_hi | 0.29 | 618.6 | 263.8 | 0.45 | 0.42 | 354.8 [-111.6, 821.2] | 0.0 | 1.5 | 3 | 439.1 | 807.3 |
| P7/0 | ex_seas30_strong_against | 0.16 | 173.5 | 470.1 | 0.43 | 0.44 | -296.5 [-822.3, 229.2] | -0.0 | -1.1 | 3 | -410.8 | -522.5 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | ex_range30_hi | 0.24 | -127.8 | 84.7 | 0.35 | 0.39 | -212.5 [-476.6, 51.7] | -0.0 | -1.6 | 3 | -183.2 | -606.8 |
| P7/1 | ex_mv_pullback_hold | 0.67 | 81.0 | -63.9 | 0.38 | 0.37 | 144.9 [-70.1, 359.9] | 0.0 | 1.3 | 4 | 191.4 | 520.2 |
| P7/1 | ex_mv_large2 | 0.69 | 74.6 | -60.6 | 0.38 | 0.38 | 135.1 [-79.2, 349.5] | 0.0 | 1.2 | 4 | 179.6 | 500.6 |
| P7/1 | ex_mv_with_large | 0.68 | 73.1 | -52.2 | 0.38 | 0.38 | 125.4 [-89.9, 340.6] | 0.0 | 1.1 | 4 | 211.3 | 500.6 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | ex_ss_arrival_with1 | 0.75 | 23.9 | -202.2 | 0.39 | 0.37 | 226.1 [-39.3, 491.5] | 42.8 | 1.7 | 4 | 746.4 | 343.2 |
| P7/3 | ex_gx_arrival_with1 | 0.61 | 41.9 | -151.9 | 0.39 | 0.39 | 193.8 [-61.2, 448.9] | 39.1 | 1.5 | 3 | 734.0 | 925.9 |
| P7/3 | ex_ss_vwap_side | 0.92 | -12.5 | -285.3 | 0.39 | 0.35 | 272.8 [-133.0, 678.7] | 24.7 | 1.3 | 3 | 136.4 | -423.3 |
| P7/3 | ex_volcurve_sess_ahead | 0.23 | -198.8 | 15.9 | 0.37 | 0.39 | -214.7 [-536.5, 107.2] | -29.4 | -1.3 | 3 | -108.4 | -1056.2 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | ex_gx_vwap_ext1_with | 0.62 | 553.9 | 53.1 | 0.55 | 0.48 | 500.8 [-37.3, 1038.9] | 67.2 | 1.8 | 4 | 616.3 | 527.3 |
| U7/0 | ex_ss_vwap_ext1_with | 0.62 | 553.9 | 53.1 | 0.55 | 0.48 | 500.8 [-37.3, 1038.9] | 67.2 | 1.8 | 4 | 616.3 | 527.3 |
| U7/0 | ex_ss_arrival_with1 | 0.56 | 203.9 | 564.2 | 0.50 | 0.55 | -360.3 [-893.8, 173.3] | -49.0 | -1.3 | 3 | -449.3 | -996.2 |
| U7/0 | ex_gx_arrival_with1 | 0.56 | 203.9 | 564.2 | 0.50 | 0.55 | -360.3 [-893.8, 173.3] | -49.0 | -1.3 | 3 | -449.3 | -996.2 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | ex_gx_twap_vwap_with | 0.63 | 284.3 | -121.5 | 0.52 | 0.48 | 405.8 [-87.1, 898.7] | 25.1 | 1.6 | 4 | 141.1 | 562.4 |
| U7/1 | ex_gx_arrival_with1 | 0.32 | -154.9 | 268.6 | 0.48 | 0.52 | -423.5 [-945.6, 98.7] | -23.5 | -1.6 | 4 | -396.1 | -779.1 |
| U7/1 | ex_mv_large2 | 0.89 | 96.9 | 401.9 | 0.49 | 0.57 | -305.0 [-838.4, 228.3] | -16.3 | -1.1 | 4 | -337.1 | 451.1 |
| U7/1 | ex_mv_with_large | 0.89 | 96.9 | 401.9 | 0.49 | 0.57 | -305.0 [-838.4, 228.3] | -16.3 | -1.1 | 4 | -337.1 | 451.1 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_C1_exec_named.parquet

### C1 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 34 conditions; 1534 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 26 conditions with |t|>2 (chance alone: about 1). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | ex_seas120_strong_against | 0.13 | 4.5 | 0.9 | 0.53 | 0.50 | 3.6 [2.9, 4.3] | 3.5 | 10.3 | 4 | 4.3 | 2.2 |
| ALL/ALL | ex_ss_vwap_ext1_with | 0.44 | 2.5 | 0.5 | 0.51 | 0.49 | 2.0 [1.5, 2.5] | 1.9 | 8.3 | 4 | 1.5 | 4.9 |
| ALL/ALL | ex_ss_vwap_ext2_with | 0.12 | 4.2 | 1.0 | 0.53 | 0.50 | 3.2 [2.4, 3.9] | 3.0 | 8.2 | 3 | 6.5 | 6.8 |
| ALL/ALL | ex_gx_arrival_with1 | 0.58 | 2.1 | 0.3 | 0.51 | 0.49 | 1.8 [1.3, 2.3] | 1.8 | 7.7 | 4 | 7.0 | 7.0 |
| ALL/ALL | ex_gx_twap_side | 0.84 | 1.7 | -0.5 | 0.51 | 0.48 | 2.2 [1.6, 2.8] | 2.1 | 6.8 | 4 | 3.3 | 3.9 |
| ALL/ALL | ex_ss_arrival_with1 | 0.57 | 2.0 | 0.5 | 0.51 | 0.49 | 1.5 [1.0, 2.0] | 1.5 | 6.3 | 3 | 3.5 | 3.8 |
| ALL/ALL | ex_seas120_strong_with | 0.14 | -0.4 | 1.6 | 0.49 | 0.50 | -2.0 [-2.6, -1.3] | -1.9 | -6.0 | 4 | -4.8 | -10.2 |
| ALL/ALL | ex_ss_twap_side | 0.93 | 1.6 | -1.2 | 0.50 | 0.47 | 2.8 [1.8, 3.7] | 2.6 | 5.9 | 4 | 5.8 | 5.4 |
| ALL/ALL | ex_ss_vwap_side | 0.93 | 1.6 | -1.1 | 0.50 | 0.47 | 2.7 [1.8, 3.6] | 2.5 | 5.9 | 4 | 4.1 | 4.6 |
| ALL/ALL | ex_seas30_strong_against | 0.15 | 2.9 | 1.1 | 0.51 | 0.50 | 1.8 [1.2, 2.4] | 1.7 | 5.6 | 4 | 4.2 | 5.0 |
| ALL/ALL | ex_gx_vwap_ext1_with | 0.59 | 1.9 | 0.6 | 0.51 | 0.49 | 1.2 [0.8, 1.7] | 1.2 | 5.4 | 3 | 3.8 | 5.4 |
| ALL/ALL | ex_seas30_with | 0.50 | 0.8 | 2.0 | 0.50 | 0.51 | -1.2 [-1.7, -0.8] | -1.2 | -5.2 | 4 | -3.9 | -4.3 |
| ALL/ALL | ex_mv_with | 0.89 | 1.6 | -0.3 | 0.50 | 0.48 | 1.9 [1.2, 2.6] | 1.8 | 5.1 | 4 | 2.7 | 3.8 |
| ALL/ALL | ex_gx_vwap_ext2_with | 0.33 | 2.2 | 1.0 | 0.51 | 0.50 | 1.3 [0.8, 1.8] | 1.2 | 5.0 | 3 | 2.3 | 4.5 |
| ALL/ALL | ex_gx_vwap_side | 0.87 | 1.6 | 0.0 | 0.50 | 0.49 | 1.6 [0.9, 2.2] | 1.5 | 4.5 | 3 | 3.0 | 3.5 |
| ALL/ALL | ex_ss_arrival_against1 | 0.06 | -0.6 | 1.5 | 0.48 | 0.50 | -2.1 [-3.1, -1.1] | -2.0 | -4.2 | 3 | -4.4 | -5.5 |
| ALL/ALL | ex_seas30_strong_with | 0.16 | 0.4 | 1.5 | 0.49 | 0.50 | -1.2 [-1.8, -0.5] | -1.1 | -3.7 | 4 | -2.8 | -3.8 |
| ALL/ALL | ex_gx_vwap_ext1_against | 0.04 | -0.5 | 1.5 | 0.49 | 0.50 | -2.0 [-3.2, -0.8] | -1.8 | -3.3 | 3 | -3.0 | -4.4 |
| ALL/ALL | ex_gx_twap_vwap_with | 0.44 | 1.0 | 1.7 | 0.50 | 0.50 | -0.7 [-1.2, -0.3] | -0.7 | -3.2 | 3 | -0.1 | 2.3 |
| ALL/ALL | ex_ss_vwap_ext1_against | 0.01 | -3.4 | 1.4 | 0.46 | 0.50 | -4.8 [-7.8, -1.8] | -2.7 | -3.2 | 4 | -5.4 | -15.8 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | ex_ss_twap_side | 0.90 | 3.2 | -1.3 | 0.52 | 0.47 | 4.5 [3.3, 5.7] | 4.4 | 7.2 | 4 | 6.4 | 6.7 |
| ALL/0 | ex_gx_twap_side | 0.90 | 3.2 | -1.3 | 0.52 | 0.47 | 4.5 [3.3, 5.7] | 4.4 | 7.2 | 4 | 6.4 | 6.7 |
| ALL/0 | ex_gx_vwap_side | 0.90 | 3.2 | -1.0 | 0.52 | 0.47 | 4.2 [3.0, 5.4] | 4.0 | 6.8 | 4 | 5.5 | 5.1 |
| ALL/0 | ex_ss_vwap_side | 0.90 | 3.2 | -1.0 | 0.52 | 0.47 | 4.2 [3.0, 5.4] | 4.0 | 6.8 | 4 | 5.5 | 5.1 |
| ALL/0 | ex_mv_with | 0.87 | 3.1 | -0.0 | 0.52 | 0.48 | 3.1 [2.1, 4.1] | 3.1 | 6.0 | 4 | 3.6 | 2.4 |
| ALL/0 | ex_seas30_strong_against | 0.15 | 4.0 | 2.4 | 0.52 | 0.51 | 1.6 [0.7, 2.5] | 1.6 | 3.3 | 4 | 8.1 | 7.1 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | ex_seas120_strong_against | 0.12 | 6.8 | 0.5 | 0.54 | 0.49 | 6.3 [4.9, 7.6] | 6.1 | 9.0 | 4 | 5.6 | -2.1 |
| ALL/1 | ex_ss_vwap_ext2_with | 0.15 | 6.0 | 0.4 | 0.55 | 0.49 | 5.6 [4.3, 6.9] | 5.5 | 8.5 | 4 | 6.0 | 1.4 |
| ALL/1 | ex_seas30_strong_against | 0.15 | 4.3 | 0.7 | 0.52 | 0.50 | 3.6 [2.4, 4.8] | 3.5 | 5.8 | 4 | 3.2 | 2.5 |
| ALL/1 | ex_seas30_with | 0.51 | 0.2 | 2.3 | 0.49 | 0.51 | -2.1 [-3.0, -1.3] | -2.1 | -4.8 | 4 | -4.0 | -5.2 |
| ALL/1 | ex_ss_twap_side | 0.94 | 1.5 | -2.5 | 0.50 | 0.47 | 4.0 [2.2, 5.9] | 3.8 | 4.0 | 4 | 7.8 | 12.5 |
| ALL/1 | ex_seas30_strong_with | 0.16 | -0.0 | 1.5 | 0.49 | 0.50 | -1.5 [-2.7, -0.3] | -1.5 | -2.5 | 4 | -3.4 | 1.8 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | ex_seas30_strong_with | 0.14 | -6.5 | 0.3 | 0.44 | 0.50 | -6.8 [-10.3, -3.4] | -5.9 | -3.4 | 4 | -8.9 | 0.8 |
| ALL/2 | ex_seas120_strong_with | 0.12 | -6.5 | 0.2 | 0.44 | 0.50 | -6.7 [-10.4, -3.0] | -5.7 | -3.0 | 4 | -2.4 | -8.8 |
| ALL/2 | ex_gx_vwap_ext1_against | 0.07 | -8.7 | -0.1 | 0.43 | 0.50 | -8.6 [-13.4, -3.8] | -6.6 | -2.7 | 4 | -6.0 | -4.0 |
| ALL/2 | ex_seas30_with | 0.50 | -2.0 | 0.7 | 0.48 | 0.51 | -2.6 [-5.0, -0.2] | -2.4 | -2.0 | 4 | -8.5 | -12.4 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | ex_seas120_strong_with | 0.14 | -0.9 | 1.9 | 0.48 | 0.50 | -2.9 [-4.9, -0.8] | -2.5 | -2.4 | 4 | -1.6 | -2.2 |
| ALL/3 | ex_gx_twap_vwap_with | 0.37 | 0.6 | 2.1 | 0.49 | 0.50 | -1.4 [-2.9, 0.0] | -1.4 | -1.8 | 4 | -3.0 | 2.2 |
| ALL/3 | ex_range30_lo | 0.29 | 0.5 | 1.9 | 0.49 | 0.50 | -1.4 [-3.0, 0.1] | -1.3 | -1.7 | 4 | -6.8 | -3.5 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | ex_gx_arrival_with1 | 0.64 | 1.8 | -4.0 | 0.51 | 0.45 | 5.8 [4.4, 7.2] | 5.4 | 7.6 | 4 | 14.7 | 21.7 |
| ALL/4 | ex_gx_vwap_ext2_with | 0.47 | 1.7 | -2.0 | 0.51 | 0.47 | 3.7 [2.4, 5.1] | 3.5 | 5.1 | 4 | 14.8 | 28.0 |
| ALL/4 | ex_seas120_strong_against | 0.12 | 4.8 | -1.0 | 0.53 | 0.49 | 5.8 [3.7, 7.8] | 4.9 | 4.6 | 4 | 2.1 | 0.2 |
| ALL/4 | ex_gx_arrival_against1 | 0.18 | -3.3 | 0.4 | 0.46 | 0.50 | -3.7 [-5.4, -1.9] | -3.2 | -3.6 | 4 | -14.7 | -13.8 |
| ALL/4 | ex_seas30_strong_against | 0.16 | 2.6 | -0.8 | 0.51 | 0.49 | 3.3 [1.5, 5.2] | 2.9 | 3.1 | 4 | 0.5 | 6.2 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | ex_gx_vwap_side | 0.79 | -1.1 | 3.3 | 0.48 | 0.54 | -4.4 [-6.4, -2.4] | -3.8 | -3.7 | 4 | -9.9 | -0.7 |
| ALL/5 | ex_ss_vwap_ext1_with | 0.17 | 3.6 | -1.0 | 0.54 | 0.48 | 4.6 [2.2, 6.9] | 3.8 | 3.2 | 4 | 2.3 | 2.8 |
| ALL/5 | ex_gx_twap_vwap_with | 0.43 | -1.1 | 0.5 | 0.49 | 0.49 | -1.6 [-3.3, 0.0] | -1.5 | -1.7 | 4 | -1.8 | -6.0 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_C1_exec_named.parquet

## Sub-block C2: statistical order-flow measures (tape and book: signed volume, book imbalance, Kyle lambda, trade size, quote-to-trade)

### C2 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 72 conditions; 1745 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 3 conditions with |t|>2 (chance alone: about 3). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | fl_bimb5300s_with | 0.51 | 62.3 | 128.6 | 0.43 | 0.44 | -66.3 [-128.2, -4.5] | -14.0 | -2.1 | 4 | -52.7 | -112.2 |
| ALL/ALL | fl_kyle_hi | 0.08 | 224.1 | 77.8 | 0.46 | 0.43 | 146.3 [9.0, 283.6] | 7.5 | 2.1 | 3 | 454.7 | 569.9 |
| ALL/ALL | fl_ofi5s_z1 | 0.12 | 172.8 | 83.9 | 0.46 | 0.43 | 88.9 [0.5, 177.2] | 10.3 | 2.0 | 4 | 39.7 | 25.1 |
| ALL/ALL | fl_ofi1s_strong | 0.37 | 114.8 | 47.7 | 0.44 | 0.42 | 67.1 [-3.9, 138.2] | 11.3 | 1.9 | 3 | 123.3 | 101.7 |
| ALL/ALL | fl_mic60s_with | 0.49 | 65.4 | 122.8 | 0.43 | 0.44 | -57.4 [-119.3, 4.5] | -12.1 | -1.8 | 3 | -64.0 | -152.6 |
| ALL/ALL | fl_bimb101s_strong | 0.07 | 198.4 | 86.2 | 0.44 | 0.43 | 112.2 [-12.1, 236.5] | 7.0 | 1.8 | 3 | 112.1 | 123.4 |
| ALL/ALL | fl_ofi1s_z2 | 0.03 | 244.7 | 89.7 | 0.47 | 0.43 | 155.0 [-18.0, 327.9] | 5.1 | 1.8 | 4 | 147.9 | 196.7 |
| ALL/ALL | fl_bimb10300s_strong | 0.04 | -66.0 | 101.0 | 0.42 | 0.44 | -167.0 [-364.4, 30.4] | -4.3 | -1.7 | 3 | -355.8 | -666.2 |
| ALL/ALL | fl_bimb1015s_strong | 0.03 | 284.7 | 89.4 | 0.48 | 0.43 | 195.3 [-37.5, 428.1] | 3.6 | 1.6 | 3 | 46.0 | -189.6 |
| ALL/ALL | fl_bimb10300s_with | 0.47 | 68.3 | 118.1 | 0.43 | 0.44 | -49.7 [-112.0, 12.5] | -10.4 | -1.6 | 3 | -75.4 | -177.0 |
| ALL/ALL | fl_ofi15s_z2 | 0.08 | 172.1 | 87.9 | 0.46 | 0.43 | 84.2 [-22.9, 191.4] | 6.9 | 1.5 | 3 | 194.1 | -16.3 |
| ALL/ALL | fl_ofi5s_strong | 0.30 | 132.9 | 77.2 | 0.45 | 0.43 | 55.7 [-15.3, 126.7] | 9.4 | 1.5 | 4 | 124.0 | -9.8 |
| ALL/ALL | fl_mic300s_with | 0.51 | 71.3 | 118.7 | 0.43 | 0.44 | -47.4 [-109.3, 14.5] | -10.0 | -1.5 | 4 | -45.1 | 18.6 |
| ALL/ALL | fl_bimb560s_with | 0.49 | 71.1 | 117.4 | 0.43 | 0.44 | -46.3 [-108.2, 15.6] | -9.7 | -1.5 | 3 | -95.0 | -120.0 |
| ALL/ALL | fl_bimb115s_with | 0.49 | 71.3 | 116.9 | 0.43 | 0.44 | -45.6 [-107.5, 16.3] | -9.6 | -1.4 | 3 | -154.5 | -157.0 |
| ALL/ALL | fl_mic15s_with | 0.50 | 72.3 | 116.3 | 0.43 | 0.44 | -44.0 [-105.9, 17.9] | -9.3 | -1.4 | 3 | -126.6 | -120.7 |
| ALL/ALL | fl_ofi15s_strong | 0.25 | 139.4 | 85.4 | 0.45 | 0.43 | 54.0 [-23.2, 131.2] | 7.9 | 1.4 | 3 | 12.5 | -5.6 |
| ALL/ALL | fl_bimb160s_with | 0.49 | 72.8 | 115.6 | 0.43 | 0.44 | -42.8 [-104.7, 19.1] | -9.0 | -1.4 | 3 | -73.8 | -114.9 |
| ALL/ALL | fl_bimb515s_with | 0.51 | 73.5 | 116.2 | 0.43 | 0.44 | -42.7 [-104.6, 19.3] | -9.0 | -1.3 | 3 | -81.9 | -163.9 |
| ALL/ALL | fl_bimb105s_with | 0.48 | 72.4 | 114.9 | 0.43 | 0.44 | -42.5 [-104.5, 19.5] | -8.9 | -1.3 | 3 | -86.3 | -154.6 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | fl_bimb5300s_with | 0.54 | 167.5 | 294.5 | 0.46 | 0.47 | -127.0 [-278.7, 24.8] | -77.0 | -1.0 | 4 | -210.4 | -370.2 |
| ALL/0 | fl_ofi5s_z1 | 0.10 | 437.8 | 203.0 | 0.52 | 0.46 | 234.8 [-4.2, 473.9] | 90.0 | 0.7 | 4 | 7.2 | 65.8 |
| ALL/0 | fl_bimb11s_strong | 0.27 | 300.3 | 198.4 | 0.48 | 0.46 | 101.9 [-70.6, 274.5] | 55.4 | 0.6 | 4 | 72.5 | 80.3 |
| ALL/0 | fl_bimb160s_strong | 0.09 | 52.2 | 242.6 | 0.45 | 0.47 | -190.4 [-465.1, 84.4] | -60.9 | -0.4 | 4 | -115.7 | -123.2 |
| ALL/0 | fl_ofi1s_z1 | 0.05 | 495.1 | 211.3 | 0.51 | 0.46 | 283.9 [-41.8, 609.5] | 71.2 | 0.4 | 4 | 40.3 | 75.0 |
| ALL/0 | fl_ofi1s_strong | 0.45 | 305.3 | 193.7 | 0.47 | 0.46 | 111.6 [-110.1, 333.3] | 46.8 | 0.4 | 4 | 33.5 | 197.5 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | fl_ofi300s_z1 | 0.47 | 65.3 | -0.9 | 0.43 | 0.40 | 66.2 [-22.3, 154.7] | 53.7 | 1.2 | 4 | 143.7 | 56.3 |
| ALL/1 | fl_ofi1s_z1 | 0.07 | -104.8 | 40.1 | 0.39 | 0.42 | -144.9 [-319.3, 29.5] | -76.1 | -0.9 | 4 | -144.1 | -232.9 |
| ALL/1 | fl_bignet60_with | 0.03 | 257.3 | 24.0 | 0.45 | 0.41 | 233.3 [-21.5, 488.1] | 79.6 | 0.6 | 4 | 537.1 | 540.4 |
| ALL/1 | fl_bimb15s_strong | 0.10 | 95.7 | 23.3 | 0.44 | 0.41 | 72.4 [-87.3, 232.0] | 41.2 | 0.5 | 4 | 53.1 | 130.5 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | fl_bimb51s_with | 0.48 | -42.2 | 91.8 | 0.39 | 0.44 | -134.0 [-209.9, -58.2] | -108.7 | -2.8 | 4 | -70.8 | -378.9 |
| ALL/3 | fl_mic300s_with | 0.49 | -37.3 | 89.8 | 0.40 | 0.44 | -127.2 [-202.9, -51.4] | -103.2 | -2.7 | 4 | -139.2 | -204.0 |
| ALL/3 | fl_bimb55s_with | 0.52 | -32.9 | 91.9 | 0.40 | 0.45 | -124.7 [-200.6, -48.9] | -101.1 | -2.6 | 4 | -59.0 | -74.9 |
| ALL/3 | fl_bimb515s_with | 0.53 | -23.8 | 84.1 | 0.40 | 0.44 | -107.9 [-184.0, -31.8] | -87.4 | -2.3 | 4 | -107.5 | -191.5 |
| ALL/3 | fl_bimb1060s_with | 0.44 | -32.2 | 73.6 | 0.39 | 0.44 | -105.8 [-181.3, -30.3] | -86.0 | -2.2 | 4 | -132.5 | -251.4 |
| ALL/3 | fl_bimb1300s_with | 0.49 | -25.6 | 77.8 | 0.41 | 0.43 | -103.4 [-179.1, -27.6] | -83.9 | -2.2 | 4 | -120.5 | -274.1 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | fl_bimb515s_with | 0.57 | 141.7 | -43.2 | 0.48 | 0.42 | 184.9 [41.8, 328.1] | 25.4 | 0.3 | 4 | 138.2 | -337.1 |
| ALL/4 | fl_mic60s_with | 0.55 | 124.3 | -14.1 | 0.48 | 0.43 | 138.4 [-3.5, 280.2] | 19.3 | 0.3 | 4 | 204.4 | 137.8 |
| ALL/4 | fl_bimb51s_strong | 0.09 | 454.8 | 24.0 | 0.62 | 0.44 | 430.8 [183.3, 678.3] | 21.8 | 0.2 | 4 | 702.5 | 332.0 |
| ALL/4 | fl_qtr300_lo | 0.18 | 118.2 | 49.6 | 0.47 | 0.45 | 68.6 [-116.3, 253.6] | 6.0 | 0.1 | 4 | 369.9 | 460.5 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | fl_ofi1s_strong | 0.49 | -6.1 | 226.3 | 0.46 | 0.57 | -232.4 [-438.8, -26.0] | -0.0 | -2.2 | 3 | -226.9 | -139.6 |
| A7/0 | fl_ofi1s_with | 0.25 | -17.7 | 162.9 | 0.46 | 0.54 | -180.7 [-344.0, -17.3] | -0.0 | -2.2 | 3 | -331.2 | -180.7 |
| A7/0 | fl_bigshare300_up | 0.33 | 21.3 | 181.0 | 0.48 | 0.55 | -159.7 [-319.1, -0.3] | -0.0 | -2.0 | 4 | -138.9 | -3.8 |
| A7/0 | fl_bimb10300s_with | 0.57 | 64.1 | 187.6 | 0.49 | 0.56 | -123.5 [-267.2, 20.2] | -0.0 | -1.7 | 4 | -108.3 | -154.6 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | fl_qtr60_hi | 0.35 | -122.0 | 454.9 | 0.45 | 0.51 | -576.9 [-988.1, -165.7] | -170.9 | -2.7 | 4 | -177.8 | 46.9 |
| H7/0 | fl_qtr300_hi | 0.14 | -288.2 | 333.1 | 0.40 | 0.50 | -621.3 [-1133.1, -109.5] | -132.8 | -2.4 | 4 | -1277.7 | -925.4 |
| H7/0 | fl_bimb515s_with | 0.57 | 400.9 | 42.5 | 0.51 | 0.45 | 358.4 [-40.1, 756.9] | 111.0 | 1.8 | 4 | 693.9 | 115.7 |
| H7/0 | fl_ofi300s_z1 | 0.33 | 503.7 | 116.4 | 0.51 | 0.47 | 387.3 [-43.5, 818.1] | 107.4 | 1.8 | 3 | 480.5 | 387.1 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | fl_bimb115s_with | 0.46 | 141.6 | -40.9 | 0.51 | 0.46 | 182.5 [-50.4, 415.4] | 0.0 | 1.5 | 3 | 194.1 | 205.5 |
| H7/3 | fl_ofi60s_with | 0.57 | 101.2 | -34.2 | 0.50 | 0.45 | 135.5 [-100.2, 371.1] | 0.0 | 1.1 | 3 | 404.5 | 999.7 |
| H7/3 | fl_bimb160s_with | 0.54 | 96.1 | -21.3 | 0.49 | 0.47 | 117.5 [-116.6, 351.6] | 0.0 | 1.0 | 3 | 327.2 | -34.0 |
| H7/3 | fl_bimb15s_with | 0.49 | 90.9 | -4.3 | 0.49 | 0.47 | 95.2 [-138.0, 328.3] | 0.0 | 0.8 | 3 | 428.9 | -144.1 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | fl_ofi5s_z1 | 0.12 | 302.5 | 77.2 | 0.53 | 0.44 | 225.3 [50.0, 400.6] | 100.0 | 2.5 | 4 | 135.2 | -21.7 |
| K7/0 | fl_ofi1s_strong | 0.44 | 225.0 | 28.7 | 0.49 | 0.42 | 196.3 [26.3, 366.4] | 90.0 | 2.3 | 4 | 171.8 | -23.0 |
| K7/0 | fl_ofi1s_with | 0.21 | 230.5 | 70.6 | 0.49 | 0.44 | 159.9 [19.3, 300.5] | 88.5 | 2.2 | 4 | 186.5 | -17.1 |
| K7/0 | fl_ofi1s_z1 | 0.06 | 359.2 | 89.1 | 0.53 | 0.44 | 270.1 [24.6, 515.5] | 78.1 | 2.2 | 3 | 315.3 | -243.6 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | fl_mic60s_with | 0.47 | -45.0 | 105.9 | 0.39 | 0.46 | -150.9 [-267.5, -34.4] | -0.0 | -2.5 | 4 | -68.3 | -29.5 |
| K7/1 | fl_bimb160s_with | 0.46 | -40.9 | 101.9 | 0.39 | 0.46 | -142.8 [-259.3, -26.3] | -0.0 | -2.4 | 4 | -99.5 | -84.5 |
| K7/1 | fl_bimb10300s_strong | 0.03 | -306.7 | 47.7 | 0.31 | 0.43 | -354.4 [-669.8, -39.0] | -0.0 | -2.2 | 3 | -353.2 | -330.4 |
| K7/1 | fl_ofi60s_with | 0.73 | 74.1 | -67.0 | 0.44 | 0.39 | 141.1 [12.8, 269.4] | 0.0 | 2.2 | 3 | 242.2 | 129.4 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | fl_mic300s_with | 0.50 | -83.4 | 103.0 | 0.38 | 0.47 | -186.4 [-286.1, -86.7] | -0.0 | -3.7 | 4 | -323.0 | -135.6 |
| K7/3 | fl_bimb560s_with | 0.57 | -55.0 | 94.9 | 0.39 | 0.47 | -149.9 [-251.1, -48.8] | -0.0 | -2.9 | 4 | -260.8 | -193.1 |
| K7/3 | fl_bimb1300s_with | 0.49 | -57.1 | 74.2 | 0.40 | 0.45 | -131.4 [-231.3, -31.4] | -0.0 | -2.6 | 4 | -225.4 | -74.6 |
| K7/3 | fl_bimb5300s_with | 0.52 | -49.2 | 75.5 | 0.39 | 0.46 | -124.7 [-224.9, -24.6] | -0.0 | -2.4 | 4 | -188.3 | -203.8 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | fl_bimb51s_strong | 0.09 | 454.8 | 24.0 | 0.62 | 0.44 | 430.8 [183.3, 678.3] | 21.8 | 3.4 | 4 | 702.5 | 332.0 |
| K7/4 | fl_bimb515s_with | 0.57 | 141.7 | -43.2 | 0.48 | 0.42 | 184.9 [41.8, 328.1] | 25.4 | 2.5 | 4 | 138.2 | -337.1 |
| K7/4 | fl_mic1s_with | 0.37 | 166.8 | -0.0 | 0.50 | 0.44 | 166.8 [20.8, 312.8] | 22.2 | 2.2 | 3 | 444.8 | 166.5 |
| K7/4 | fl_bimb11s_with | 0.37 | 166.8 | -0.0 | 0.50 | 0.44 | 166.8 [20.8, 312.8] | 22.2 | 2.2 | 3 | 444.8 | 166.5 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | fl_ofi5s_with | 0.47 | 62.0 | -59.5 | 0.43 | 0.39 | 121.5 [15.8, 227.2] | 0.0 | 2.3 | 3 | 202.1 | 59.8 |
| M7/1 | fl_bimb11s_strong | 0.25 | -94.5 | 26.9 | 0.38 | 0.41 | -121.4 [-242.6, -0.1] | -0.0 | -2.0 | 4 | -270.5 | 2.0 |
| M7/1 | fl_ofi1s_with | 0.23 | 90.6 | -30.5 | 0.43 | 0.40 | 121.0 [-5.4, 247.5] | 0.0 | 1.9 | 4 | 259.9 | 254.7 |
| M7/1 | fl_bimb5300s_with | 0.51 | -51.6 | 47.3 | 0.39 | 0.42 | -98.8 [-204.1, 6.4] | -0.0 | -1.8 | 4 | -131.9 | -120.7 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | fl_ofi15s_z1 | 0.22 | 115.7 | 19.2 | 0.48 | 0.43 | 96.4 [-30.2, 223.0] | 0.0 | 1.5 | 3 | 149.2 | 253.0 |
| M7/3 | fl_ofi60s_with | 0.84 | 25.1 | 119.2 | 0.43 | 0.48 | -94.1 [-235.3, 47.1] | -0.0 | -1.3 | 3 | -284.0 | 119.9 |
| M7/3 | fl_bimb5300s_with | 0.45 | 7.1 | 66.9 | 0.41 | 0.46 | -59.8 [-163.4, 43.8] | -0.0 | -1.1 | 3 | -67.0 | 0.8 |
| M7/3 | fl_bigshare60_up | 0.30 | 83.5 | 21.4 | 0.46 | 0.43 | 62.1 [-51.5, 175.7] | 0.0 | 1.1 | 3 | 299.9 | 176.9 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | fl_ofi5s_with | 0.45 | 253.8 | 111.6 | 0.41 | 0.34 | 142.2 [-70.9, 355.4] | 0.0 | 1.3 | 3 | 463.5 | 435.4 |
| O7/3 | fl_mic5s_with | 0.50 | 114.0 | 238.1 | 0.35 | 0.39 | -124.1 [-336.1, 87.9] | -0.0 | -1.1 | 3 | -626.1 | -869.2 |
| O7/3 | fl_bimb560s_with | 0.61 | 219.2 | 108.4 | 0.39 | 0.35 | 110.9 [-105.3, 327.0] | 0.0 | 1.0 | 3 | 246.0 | 54.9 |
| O7/3 | fl_bimb15s_with | 0.48 | 120.1 | 228.7 | 0.36 | 0.39 | -108.6 [-320.5, 103.2] | -0.0 | -1.0 | 4 | -482.8 | -869.2 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | fl_bimb5300s_with | 0.52 | 179.0 | 570.7 | 0.41 | 0.44 | -391.7 [-821.7, 38.2] | -161.7 | -1.8 | 3 | -666.9 | -1175.1 |
| P7/0 | fl_ofi1s_z1 | 0.04 | 1304.1 | 327.5 | 0.52 | 0.42 | 976.6 [-132.4, 2085.6] | 93.4 | 1.7 | 3 | 718.0 | 3194.2 |
| P7/0 | fl_bimb160s_strong | 0.08 | -319.2 | 424.8 | 0.35 | 0.43 | -744.0 [-1599.9, 111.8] | -112.2 | -1.7 | 4 | -140.0 | -1262.2 |
| P7/0 | fl_ofi60s_z2 | 0.12 | -109.8 | 433.0 | 0.39 | 0.43 | -542.8 [-1170.7, 85.1] | -134.6 | -1.7 | 3 | -60.5 | 1319.1 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | fl_bimb101s_strong | 0.07 | 636.4 | -10.2 | 0.51 | 0.37 | 646.6 [142.6, 1150.7] | 172.9 | 2.5 | 3 | 1380.7 | 2257.8 |
| P7/1 | fl_ofi300s_z2 | 0.06 | 619.3 | -5.0 | 0.51 | 0.37 | 624.3 [125.0, 1123.6] | 169.3 | 2.5 | 4 | 1020.5 | 1151.0 |
| P7/1 | fl_ofi5s_with | 0.43 | -109.9 | 144.1 | 0.35 | 0.40 | -254.0 [-481.8, -26.2] | -162.8 | -2.2 | 3 | -468.7 | -503.5 |
| P7/1 | fl_bimb560s_with | 0.42 | 181.4 | -71.1 | 0.41 | 0.36 | 252.5 [20.0, 484.9] | 159.5 | 2.1 | 3 | 394.6 | 674.1 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | fl_bimb101s_with | 0.49 | -275.3 | 195.7 | 0.33 | 0.44 | -471.0 [-729.2, -212.8] | -267.6 | -3.6 | 4 | -709.4 | -636.4 |
| P7/3 | fl_bimb1060s_with | 0.38 | -264.3 | 107.9 | 0.34 | 0.42 | -372.2 [-633.4, -111.1] | -209.4 | -2.8 | 4 | -20.6 | -536.5 |
| P7/3 | fl_mic300s_with | 0.49 | -211.6 | 134.5 | 0.36 | 0.42 | -346.1 [-605.1, -87.1] | -196.1 | -2.6 | 4 | -13.8 | -252.3 |
| P7/3 | fl_bimb51s_with | 0.49 | -203.5 | 131.9 | 0.34 | 0.44 | -335.4 [-594.7, -76.1] | -189.9 | -2.5 | 3 | -556.8 | -1123.8 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | fl_bimb160s_with | 0.54 | 124.2 | 657.8 | 0.50 | 0.56 | -533.6 [-1078.2, 10.9] | -0.0 | -1.9 | 3 | -944.2 | -1034.9 |
| U7/0 | fl_mic60s_with | 0.53 | 152.5 | 621.9 | 0.50 | 0.56 | -469.4 [-1014.1, 75.3] | -0.0 | -1.7 | 3 | -1016.8 | -1233.5 |
| U7/0 | fl_ofi15s_strong | 0.29 | 96.2 | 493.5 | 0.47 | 0.55 | -397.4 [-1011.7, 217.0] | -0.0 | -1.3 | 3 | -652.3 | -1837.0 |
| U7/0 | fl_bimb10300s_with | 0.51 | 212.7 | 536.5 | 0.51 | 0.54 | -323.8 [-867.9, 220.3] | -0.0 | -1.2 | 3 | -171.5 | -631.8 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | fl_qtr60_hi | 0.19 | -473.8 | 282.0 | 0.44 | 0.52 | -755.9 [-1346.5, -165.2] | -0.0 | -2.5 | 4 | -848.5 | -1706.1 |
| U7/1 | fl_bimb51s_with | 0.49 | -101.5 | 357.3 | 0.48 | 0.53 | -458.9 [-933.7, 16.0] | -0.0 | -1.9 | 3 | -312.3 | -691.6 |
| U7/1 | fl_kyle_lo | 0.34 | -166.7 | 286.4 | 0.47 | 0.52 | -453.1 [-964.3, 58.2] | -0.0 | -1.7 | 3 | -65.9 | -890.7 |
| U7/1 | fl_bimb5300s_with | 0.58 | 30.4 | 276.9 | 0.48 | 0.54 | -246.6 [-722.0, 228.8] | -0.0 | -1.0 | 3 | -383.9 | -422.6 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_C2_flow_named.parquet

### C2 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 72 conditions; 3341 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 14 conditions with |t|>2 (chance alone: about 3). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | fl_ofi300s_with | 0.74 | 1.1 | 2.0 | 0.50 | 0.51 | -0.9 [-1.4, -0.3] | -0.7 | -3.2 | 4 | -1.6 | -3.3 |
| ALL/ALL | fl_ofi15s_with | 0.58 | 1.0 | 1.8 | 0.50 | 0.51 | -0.7 [-1.2, -0.3] | -0.6 | -3.2 | 4 | -0.6 | -1.5 |
| ALL/ALL | fl_ofi300s_z1 | 0.41 | 0.9 | 1.6 | 0.50 | 0.50 | -0.7 [-1.2, -0.2] | -0.6 | -3.0 | 3 | -1.1 | -1.1 |
| ALL/ALL | fl_bimb5300s_with | 0.48 | 1.0 | 1.7 | 0.50 | 0.51 | -0.7 [-1.2, -0.2] | -0.6 | -3.0 | 3 | -3.3 | -3.3 |
| ALL/ALL | fl_size60_up | 0.03 | 3.2 | 1.3 | 0.52 | 0.50 | 1.9 [0.6, 3.2] | 0.7 | 2.9 | 4 | 5.9 | 1.3 |
| ALL/ALL | fl_ofi300s_z2 | 0.15 | 0.5 | 1.5 | 0.49 | 0.50 | -0.9 [-1.6, -0.3] | -0.7 | -2.9 | 4 | -1.7 | -1.0 |
| ALL/ALL | fl_size300_up | 0.01 | 5.3 | 1.3 | 0.55 | 0.50 | 4.0 [1.2, 6.7] | 0.4 | 2.8 | 4 | 12.5 | 21.4 |
| ALL/ALL | fl_bimb55s_with | 0.46 | 1.0 | 1.6 | 0.50 | 0.50 | -0.6 [-1.1, -0.2] | -0.5 | -2.8 | 4 | -1.1 | -1.1 |
| ALL/ALL | fl_bigshare60_up | 0.20 | 0.6 | 1.5 | 0.50 | 0.50 | -0.9 [-1.5, -0.2] | -0.6 | -2.7 | 4 | -0.4 | -1.0 |
| ALL/ALL | fl_bimb51s_with | 0.43 | 1.0 | 1.6 | 0.50 | 0.50 | -0.5 [-1.0, -0.1] | -0.4 | -2.3 | 3 | -0.3 | -1.2 |
| ALL/ALL | fl_bimb560s_with | 0.43 | 1.0 | 1.6 | 0.50 | 0.50 | -0.5 [-1.0, -0.1] | -0.4 | -2.2 | 4 | -1.9 | -2.2 |
| ALL/ALL | fl_kyle_hi | 0.09 | 2.0 | 1.2 | 0.51 | 0.50 | 0.8 [-0.0, 1.5] | 0.5 | 1.9 | 4 | 1.7 | 3.4 |
| ALL/ALL | fl_bimb515s_strong | 0.03 | 2.4 | 1.3 | 0.51 | 0.50 | 1.1 [-0.2, 2.4] | 0.4 | 1.7 | 3 | 4.4 | 7.1 |
| ALL/ALL | fl_ofi5s_strong | 0.33 | 1.5 | 1.0 | 0.50 | 0.50 | 0.5 [-0.1, 1.0] | 0.3 | 1.7 | 3 | 1.7 | 0.8 |
| ALL/ALL | fl_qtr60_lo | 0.24 | 1.0 | 1.4 | 0.50 | 0.50 | -0.5 [-1.0, 0.1] | -0.3 | -1.7 | 4 | -0.3 | 1.7 |
| ALL/ALL | fl_bimb515s_with | 0.46 | 1.1 | 1.5 | 0.50 | 0.50 | -0.4 [-0.8, 0.1] | -0.3 | -1.5 | 4 | -0.8 | -0.2 |
| ALL/ALL | fl_ofi60s_z2 | 0.15 | 0.9 | 1.4 | 0.50 | 0.50 | -0.5 [-1.1, 0.1] | -0.3 | -1.5 | 3 | -0.2 | 3.8 |
| ALL/ALL | fl_bignet60_with | 0.06 | 0.6 | 1.4 | 0.50 | 0.50 | -0.8 [-1.8, 0.2] | -0.4 | -1.5 | 3 | -1.5 | 1.0 |
| ALL/ALL | fl_mic1s_with | 0.33 | 1.1 | 1.4 | 0.50 | 0.50 | -0.4 [-0.8, 0.1] | -0.3 | -1.4 | 3 | -1.6 | -1.1 |
| ALL/ALL | fl_bimb11s_with | 0.33 | 1.1 | 1.4 | 0.50 | 0.50 | -0.4 [-0.8, 0.1] | -0.3 | -1.4 | 3 | -1.6 | -1.1 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | fl_ofi60s_z2 | 0.15 | 1.3 | 3.0 | 0.50 | 0.52 | -1.7 [-2.6, -0.7] | -1.5 | -3.0 | 4 | -3.3 | -0.2 |
| ALL/0 | fl_ofi60s_z1 | 0.34 | 2.2 | 3.0 | 0.51 | 0.52 | -0.8 [-1.6, -0.1] | -0.8 | -2.0 | 4 | -0.2 | -0.1 |
| ALL/0 | fl_ofi60s_with | 0.76 | 2.5 | 3.3 | 0.51 | 0.52 | -0.8 [-1.6, 0.0] | -0.7 | -1.7 | 4 | -1.0 | -0.5 |
| ALL/0 | fl_ofi5s_strong | 0.45 | 3.2 | 2.4 | 0.52 | 0.51 | 0.8 [-0.1, 1.7] | 0.7 | 1.6 | 4 | 2.2 | 0.7 |
| ALL/0 | fl_bignet300_strong | 0.01 | 9.5 | 2.6 | 0.58 | 0.51 | 6.9 [3.2, 10.6] | 2.6 | 1.3 | 4 | 4.5 | 14.9 |
| ALL/0 | fl_bignet60_with | 0.02 | 6.7 | 2.6 | 0.55 | 0.51 | 4.0 [1.0, 7.0] | 1.9 | 1.3 | 4 | 8.5 | 13.0 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | fl_bigshare300_up | 0.26 | 2.6 | 0.9 | 0.51 | 0.50 | 1.8 [0.7, 2.8] | 1.5 | 2.9 | 4 | 3.3 | 0.5 |
| ALL/1 | fl_size60_up | 0.03 | 6.3 | 1.1 | 0.55 | 0.50 | 5.2 [2.7, 7.6] | 2.5 | 2.0 | 4 | 11.1 | 4.7 |
| ALL/1 | fl_bignet300_with | 0.07 | 3.4 | 1.1 | 0.52 | 0.50 | 2.3 [0.6, 4.1] | 1.5 | 1.7 | 4 | 3.3 | 4.5 |
| ALL/1 | fl_ofi60s_z2 | 0.16 | 2.2 | 1.1 | 0.51 | 0.50 | 1.1 [-0.0, 2.3] | 0.9 | 1.5 | 4 | 2.6 | 9.5 |
| ALL/1 | fl_bignet300_strong | 0.02 | 6.1 | 1.1 | 0.55 | 0.50 | 5.0 [2.0, 7.9] | 2.0 | 1.3 | 4 | 4.1 | 4.0 |
| ALL/1 | fl_ofi5s_z2 | 0.05 | 3.0 | 1.1 | 0.51 | 0.50 | 1.9 [0.0, 3.7] | 1.1 | 1.2 | 4 | 4.2 | 10.6 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | fl_ofi15s_with | 0.60 | -1.7 | 1.0 | 0.48 | 0.51 | -2.8 [-5.2, -0.3] | -0.5 | -0.4 | 4 | -6.8 | -14.2 |
| ALL/2 | fl_bimb105s_strong | 0.04 | -9.3 | -0.3 | 0.43 | 0.50 | -9.0 [-14.9, -3.1] | -0.4 | -0.1 | 4 | -16.8 | 1.0 |
| ALL/2 | fl_bimb560s_strong | 0.07 | 2.9 | -0.9 | 0.53 | 0.49 | 3.8 [-0.9, 8.5] | 0.2 | 0.1 | 4 | 6.0 | 9.0 |
| ALL/2 | fl_bimb1060s_strong | 0.06 | 1.8 | -0.8 | 0.52 | 0.49 | 2.6 [-2.3, 7.5] | 0.2 | 0.1 | 4 | 7.2 | 10.0 |
| ALL/2 | fl_bignet60_strong | 0.03 | -6.6 | -0.5 | 0.45 | 0.49 | -6.1 [-13.2, 1.0] | -0.2 | -0.0 | 4 | -14.0 | -13.3 |
| ALL/2 | fl_bimb1015s_strong | 0.02 | -5.4 | -0.5 | 0.46 | 0.49 | -4.9 [-12.7, 2.9] | -0.1 | -0.0 | 4 | -13.5 | 0.1 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | fl_bimb1060s_with | 0.37 | -0.9 | 2.9 | 0.47 | 0.51 | -3.8 [-5.3, -2.4] | -3.1 | -4.1 | 4 | -1.5 | -0.0 |
| ALL/3 | fl_bimb560s_with | 0.42 | -0.4 | 3.0 | 0.47 | 0.51 | -3.4 [-4.8, -2.0] | -2.7 | -3.7 | 4 | -1.8 | 2.5 |
| ALL/3 | fl_bimb5300s_with | 0.44 | -0.2 | 2.8 | 0.47 | 0.51 | -3.0 [-4.4, -1.6] | -2.4 | -3.3 | 4 | -2.4 | 0.4 |
| ALL/3 | fl_ofi300s_z1 | 0.41 | -0.2 | 2.7 | 0.48 | 0.51 | -2.9 [-4.4, -1.5] | -2.4 | -3.2 | 4 | -6.0 | -8.5 |
| ALL/3 | fl_bimb101s_with | 0.44 | -0.1 | 2.8 | 0.48 | 0.51 | -2.9 [-4.3, -1.5] | -2.3 | -3.2 | 4 | -1.7 | -1.0 |
| ALL/3 | fl_bimb55s_with | 0.48 | 0.2 | 2.8 | 0.48 | 0.51 | -2.6 [-4.0, -1.2] | -2.1 | -2.9 | 4 | -1.0 | 1.8 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | fl_ofi300s_z1 | 0.39 | -1.1 | 0.3 | 0.48 | 0.50 | -1.4 [-2.8, -0.1] | -1.3 | -1.9 | 4 | -4.1 | -8.6 |
| ALL/4 | fl_ofi5s_with | 0.54 | 0.3 | -0.9 | 0.50 | 0.48 | 1.3 [-0.1, 2.6] | 1.2 | 1.7 | 4 | 5.2 | 0.2 |
| ALL/4 | fl_bimb15s_strong | 0.11 | -1.6 | -0.1 | 0.48 | 0.49 | -1.5 [-3.6, 0.6] | -1.2 | -1.1 | 4 | -9.4 | -5.9 |
| ALL/4 | fl_ofi300s_z2 | 0.13 | -1.3 | -0.1 | 0.48 | 0.49 | -1.2 [-3.2, 0.8] | -1.0 | -1.0 | 4 | -7.1 | -9.5 |
| ALL/4 | fl_bimb560s_with | 0.42 | -0.6 | -0.0 | 0.49 | 0.49 | -0.6 [-2.0, 0.7] | -0.6 | -0.8 | 4 | -4.4 | -6.2 |
| ALL/4 | fl_ofi1s_z2 | 0.03 | 2.2 | -0.3 | 0.52 | 0.49 | 2.5 [-1.3, 6.4] | 1.5 | 0.8 | 4 | 12.4 | 7.1 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | fl_mic15s_with | 0.49 | -1.3 | 1.0 | 0.48 | 0.50 | -2.3 [-3.9, -0.7] | -1.4 | -1.6 | 4 | -2.7 | -1.1 |
| ALL/5 | fl_qtr300_hi | 0.22 | 1.9 | -0.8 | 0.51 | 0.49 | 2.7 [0.8, 4.6] | 1.4 | 1.4 | 4 | 1.9 | 8.0 |
| ALL/5 | fl_qtr60_hi | 0.24 | 1.6 | -0.7 | 0.51 | 0.49 | 2.4 [0.5, 4.2] | 1.2 | 1.3 | 4 | 2.4 | 10.0 |
| ALL/5 | fl_ofi5s_z1 | 0.12 | -3.5 | 0.3 | 0.46 | 0.50 | -3.8 [-6.3, -1.3] | -1.4 | -1.1 | 4 | -2.2 | 1.7 |
| ALL/5 | fl_bimb115s_with | 0.49 | -0.9 | 0.5 | 0.48 | 0.50 | -1.4 [-3.0, 0.2] | -0.8 | -1.0 | 4 | -0.7 | 1.3 |
| ALL/5 | fl_ofi1s_z2 | 0.04 | -7.1 | 0.1 | 0.42 | 0.50 | -7.2 [-11.3, -3.0] | -1.3 | -0.6 | 4 | -7.8 | -8.3 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_C2_flow_named.parquet

## ADDENDUM 6 BLOCK 7: time-of-day liquidity events (minutes to / from 02:00 ... 18:00, macro windows, with / against the window move)

### B7 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 269 conditions; 2495 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 50 conditions with |t|>2 (chance alone: about 13). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n7_halfhour_pre15_big_with | 0.02 | -150.4 | 112.0 | 0.39 | 0.44 | -262.4 [-393.8, -131.0] | -146.2 | -3.9 | 4 | -395.7 | -349.4 |
| ALL/ALL | n7_grp_fix_post15 | 0.03 | -110.8 | 112.2 | 0.39 | 0.44 | -223.0 [-340.0, -106.0] | -136.7 | -3.7 | 4 | -164.8 | -257.0 |
| ALL/ALL | n7_grp_fix_post15_with | 0.02 | -115.3 | 111.2 | 0.39 | 0.44 | -226.5 [-352.2, -100.8] | -131.1 | -3.5 | 3 | -122.8 | -197.4 |
| ALL/ALL | n7_t0830_pre15_with | 0.01 | -259.3 | 109.8 | 0.33 | 0.44 | -369.0 [-611.9, -126.2] | -99.3 | -3.0 | 4 | -8.5 | -120.3 |
| ALL/ALL | n7_grp_rel_post5_with | 0.01 | -143.8 | 109.3 | 0.38 | 0.44 | -253.1 [-420.0, -86.2] | -110.9 | -3.0 | 4 | -687.3 | -438.8 |
| ALL/ALL | n7_w1000_1100_in | 0.14 | 32.0 | 118.0 | 0.43 | 0.44 | -86.0 [-148.3, -23.8] | -73.0 | -2.7 | 4 | -147.7 | -19.9 |
| ALL/ALL | n7_w1000_1100_in_against | 0.02 | -118.3 | 108.3 | 0.38 | 0.44 | -226.5 [-395.4, -57.6] | -97.9 | -2.6 | 3 | -118.4 | 513.9 |
| ALL/ALL | n7_w0950_post15 | 0.04 | -30.0 | 110.9 | 0.41 | 0.44 | -140.9 [-248.9, -32.9] | -91.7 | -2.6 | 4 | -115.5 | -199.3 |
| ALL/ALL | n7_t1800_post30 | 0.03 | 454.9 | 95.8 | 0.50 | 0.44 | 359.2 [82.9, 635.4] | 79.5 | 2.5 | 4 | 295.6 | 798.9 |
| ALL/ALL | n7_t1130_post15 | 0.01 | -101.2 | 108.6 | 0.40 | 0.44 | -209.8 [-381.0, -38.6] | -89.3 | -2.4 | 3 | -391.3 | -307.0 |
| ALL/ALL | n7_w0950_in | 0.04 | -17.1 | 110.8 | 0.42 | 0.44 | -127.8 [-233.5, -22.2] | -84.5 | -2.4 | 4 | -278.2 | 140.1 |
| ALL/ALL | n7_t0300_post30_with | 0.01 | -204.5 | 109.2 | 0.36 | 0.44 | -313.7 [-574.0, -53.4] | -76.1 | -2.4 | 4 | -364.9 | -238.1 |
| ALL/ALL | n7_t1130_post15_with | 0.01 | -107.0 | 108.3 | 0.39 | 0.44 | -215.3 [-399.1, -31.5] | -84.3 | -2.3 | 3 | -392.6 | -259.4 |
| ALL/ALL | n7_w1000_1100_in_with | 0.12 | 37.4 | 113.5 | 0.43 | 0.44 | -76.1 [-141.6, -10.6] | -63.6 | -2.3 | 4 | -139.5 | -108.2 |
| ALL/ALL | n7_t1000_post15 | 0.03 | -31.5 | 109.8 | 0.41 | 0.44 | -141.3 [-265.2, -17.5] | -82.8 | -2.2 | 3 | -107.2 | 201.8 |
| ALL/ALL | n7_grp_rel_post15 | 0.03 | -29.8 | 109.8 | 0.41 | 0.44 | -139.6 [-262.6, -16.7] | -82.3 | -2.2 | 3 | -107.2 | 201.8 |
| ALL/ALL | n7_t1800_post30_with | 0.02 | 406.8 | 98.5 | 0.49 | 0.44 | 308.4 [36.5, 580.2] | 70.0 | 2.2 | 3 | 231.0 | 532.1 |
| ALL/ALL | n7_tophour_post30_against | 0.10 | -5.5 | 118.1 | 0.42 | 0.44 | -123.6 [-232.8, -14.3] | -79.7 | -2.2 | 3 | -240.4 | -280.9 |
| ALL/ALL | n7_t1000_post5 | 0.02 | -38.0 | 109.1 | 0.42 | 0.44 | -147.2 [-282.7, -11.6] | -79.7 | -2.1 | 3 | -499.8 | -213.2 |
| ALL/ALL | n7_grp_rel_post5 | 0.02 | -31.8 | 109.0 | 0.42 | 0.44 | -140.8 [-275.1, -6.5] | -76.9 | -2.1 | 3 | -508.1 | -213.2 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n7_t1800_post15 | 0.06 | 83.8 | 241.7 | 0.44 | 0.47 | -157.9 [-343.3, 27.5] | -93.6 | -1.0 | 4 | -176.4 | -167.1 |
| ALL/0 | n7_t1800_post15_with | 0.05 | 110.7 | 239.0 | 0.45 | 0.47 | -128.3 [-320.6, 63.9] | -73.9 | -0.8 | 4 | -87.1 | 4.6 |
| ALL/0 | n7_t1800_post30 | 0.08 | 454.9 | 213.9 | 0.50 | 0.46 | 241.0 [-42.5, 524.5] | 92.6 | 0.6 | 4 | 199.6 | 743.3 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n7_tophour_post15 | 0.28 | 70.6 | 14.8 | 0.42 | 0.41 | 55.8 [-39.8, 151.4] | 0.0 | 0.0 | 4 | 85.4 | 100.8 |
| ALL/1 | n7_tophour_post15_with | 0.18 | 74.3 | 20.5 | 0.41 | 0.42 | 53.8 [-57.3, 164.8] | 0.0 | 0.0 | 4 | 98.2 | 121.9 |
| ALL/1 | n7_t0300_post30_with | 0.03 | -204.5 | 38.2 | 0.36 | 0.42 | -242.7 [-505.0, 19.6] | -0.0 | -0.0 | 4 | -248.5 | -175.2 |
| ALL/1 | n7_t0300_post30 | 0.03 | -155.2 | 36.9 | 0.38 | 0.42 | -192.1 [-451.1, 66.9] | -0.0 | -0.0 | 4 | -184.5 | -175.2 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n7_grp_nyo_post15_with | 0.15 | 171.3 | 1.6 | 0.42 | 0.42 | 169.7 [68.8, 270.6] | 135.9 | 2.6 | 4 | 199.0 | 271.3 |
| ALL/3 | n7_grp_nyo_post15 | 0.16 | 154.4 | 2.9 | 0.41 | 0.42 | 151.6 [52.2, 250.9] | 122.1 | 2.4 | 4 | 136.2 | 186.3 |
| ALL/3 | n7_w1000_1100_in_big_with | 0.25 | 99.8 | -7.0 | 0.45 | 0.40 | 106.8 [20.8, 192.9] | 90.4 | 2.1 | 4 | 93.3 | 311.2 |
| ALL/3 | n7_tophour_in_with | 0.08 | -186.8 | 31.7 | 0.36 | 0.42 | -218.5 [-364.3, -72.8] | -143.8 | -1.9 | 4 | -637.8 | -486.5 |
| ALL/3 | n7_halfhour_post15_with | 0.21 | 110.3 | 5.7 | 0.42 | 0.42 | 104.7 [13.2, 196.1] | 86.9 | 1.9 | 4 | 132.3 | 185.9 |
| ALL/3 | n7_grp_fix_pre15_big_with | 0.05 | -104.7 | 34.3 | 0.37 | 0.42 | -139.0 [-276.9, -1.2] | -94.9 | -1.3 | 4 | -14.9 | 326.5 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n7_halfhour_post30 | 0.30 | 153.0 | 22.2 | 0.50 | 0.44 | 130.7 [-24.3, 285.8] | 0.0 | 0.0 | 4 | 290.1 | 191.2 |
| ALL/4 | n7_tophour_post15 | 0.23 | -43.5 | 93.4 | 0.40 | 0.47 | -136.8 [-303.6, 29.9] | -0.0 | -0.0 | 4 | -534.9 | -485.7 |
| ALL/4 | n7_halfhour_post30_with | 0.18 | 193.7 | 32.2 | 0.51 | 0.45 | 161.4 [-26.9, 349.7] | 0.0 | 0.0 | 4 | 207.5 | 41.8 |
| ALL/4 | n7_w1400_1500_in_with | 0.28 | 4.6 | 77.8 | 0.44 | 0.46 | -73.1 [-218.6, 72.3] | -0.0 | -0.0 | 4 | -260.1 | -287.7 |
| ALL/4 | n7_halfhour_pre15 | 0.22 | -32.8 | 88.8 | 0.40 | 0.47 | -121.6 [-298.0, 54.7] | -0.0 | -0.0 | 4 | -97.5 | -518.0 |
| ALL/4 | n7_tophour_post15_with | 0.17 | -51.2 | 85.5 | 0.41 | 0.47 | -136.7 [-324.8, 51.4] | -0.0 | -0.0 | 4 | -180.8 | 173.2 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | n7_halfhour_in | 0.09 | -172.2 | 142.2 | 0.40 | 0.53 | -314.4 [-543.9, -84.9] | -95.9 | -2.7 | 3 | -100.3 | -285.8 |
| A7/0 | n7_macro_xx50_post30_with | 0.16 | -94.1 | 151.8 | 0.44 | 0.54 | -245.9 [-431.4, -60.4] | -98.8 | -2.6 | 3 | -121.8 | -502.0 |
| A7/0 | n7_macro_xx50_post15_with | 0.21 | 257.8 | 87.0 | 0.58 | 0.51 | 170.8 [4.4, 337.1] | 77.7 | 2.0 | 3 | 246.4 | 355.7 |
| A7/0 | n7_macro_xx50_post30 | 0.24 | -2.2 | 151.9 | 0.47 | 0.54 | -154.2 [-308.3, -0.0] | -76.0 | -2.0 | 3 | -54.9 | -208.8 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | n7_macro_xx50_in_with | 0.15 | 566.2 | 148.5 | 0.53 | 0.47 | 417.7 [-130.6, 966.1] | 0.0 | 1.5 | 4 | 578.1 | 484.2 |
| H7/0 | n7_macro_xx50_in | 0.30 | 386.7 | 144.0 | 0.50 | 0.47 | 242.7 [-178.7, 664.1] | 0.0 | 1.1 | 3 | 513.3 | 116.9 |
| H7/0 | n7_tophour_post15_with | 0.22 | 415.8 | 159.8 | 0.50 | 0.47 | 256.0 [-209.8, 721.8] | 0.0 | 1.1 | 4 | 563.7 | 23.7 |
| H7/0 | n7_halfhour_post30_with | 0.15 | 427.3 | 179.3 | 0.53 | 0.47 | 248.1 [-270.6, 766.8] | 0.0 | 0.9 | 3 | 505.8 | 134.1 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | n7_w1000_1100_in_with | 0.58 | -23.6 | 106.1 | 0.46 | 0.50 | -129.7 [-373.6, 114.1] | -0.0 | -1.0 | 3 | -574.5 | -662.2 |
| H7/3 | n7_w1000_1100_in | 0.64 | 8.1 | 102.3 | 0.47 | 0.50 | -94.2 [-335.4, 147.0] | -0.0 | -0.8 | 3 | -447.2 | -662.2 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | n7_tophour_pre15 | 0.19 | 197.7 | 62.9 | 0.48 | 0.44 | 134.8 [3.1, 266.5] | 0.0 | 2.0 | 3 | 213.1 | 421.9 |
| K7/0 | n7_halfhour_post30 | 0.21 | 186.2 | 63.7 | 0.48 | 0.43 | 122.5 [-3.3, 248.2] | 0.0 | 1.9 | 4 | 235.8 | 355.3 |
| K7/0 | n7_tophour_pre15_with | 0.18 | 194.5 | 66.0 | 0.47 | 0.44 | 128.5 [-6.5, 263.5] | 0.0 | 1.9 | 3 | 211.9 | 316.6 |
| K7/0 | n7_halfhour_post30_with | 0.11 | 225.4 | 71.8 | 0.49 | 0.44 | 153.6 [-9.2, 316.4] | 0.0 | 1.8 | 4 | 281.6 | 597.8 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | n7_macro_xx50_post15_against | 0.06 | -159.2 | 49.0 | 0.36 | 0.43 | -208.2 [-443.4, 27.1] | -13.6 | -1.7 | 4 | -207.5 | -719.4 |
| K7/1 | n7_grp_eur_post15_with | 0.05 | 280.2 | 22.7 | 0.48 | 0.42 | 257.5 [-33.6, 548.6] | 11.2 | 1.7 | 3 | 321.6 | 250.4 |
| K7/1 | n7_grp_eur_post15 | 0.05 | 268.7 | 22.6 | 0.48 | 0.42 | 246.1 [-39.0, 531.3] | 11.2 | 1.7 | 3 | 203.3 | 110.1 |
| K7/1 | n7_halfhour_post15_against | 0.07 | 191.8 | 22.9 | 0.49 | 0.42 | 168.8 [-60.6, 398.2] | 11.5 | 1.4 | 3 | 94.1 | 61.7 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | n7_halfhour_post30 | 0.28 | 85.5 | -19.9 | 0.46 | 0.41 | 105.3 [-6.6, 217.2] | 0.0 | 1.8 | 3 | 107.9 | 244.9 |
| K7/3 | n7_halfhour_post30_with | 0.15 | 121.5 | -10.0 | 0.48 | 0.42 | 131.5 [-10.0, 272.9] | 0.0 | 1.8 | 3 | 294.3 | 211.0 |
| K7/3 | n7_macro_xx50_post30 | 0.24 | -67.8 | 34.7 | 0.40 | 0.43 | -102.5 [-218.9, 14.0] | -0.0 | -1.7 | 3 | -403.8 | -151.8 |
| K7/3 | n7_w1050_post30 | 0.10 | -111.5 | 23.1 | 0.38 | 0.43 | -134.6 [-301.2, 32.0] | -0.0 | -1.6 | 3 | -419.6 | -131.6 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | n7_tophour_in_with | 0.10 | 260.5 | 40.8 | 0.49 | 0.46 | 219.7 [-33.9, 473.3] | 0.0 | 1.7 | 4 | 379.5 | 53.9 |
| K7/4 | n7_halfhour_post30_with | 0.18 | 193.7 | 32.2 | 0.51 | 0.45 | 161.4 [-26.9, 349.7] | 0.0 | 1.7 | 4 | 207.5 | 41.8 |
| K7/4 | n7_halfhour_post30 | 0.30 | 153.0 | 22.2 | 0.50 | 0.44 | 130.7 [-24.3, 285.8] | 0.0 | 1.7 | 4 | 290.1 | 191.2 |
| K7/4 | n7_tophour_post15 | 0.23 | -43.5 | 93.4 | 0.40 | 0.47 | -136.8 [-303.6, 29.9] | -0.0 | -1.6 | 4 | -534.9 | -485.7 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | n7_tophour_post15_with | 0.19 | -99.0 | 20.2 | 0.37 | 0.41 | -119.2 [-244.0, 5.6] | -0.0 | -1.9 | 4 | -23.1 | -33.0 |
| M7/1 | n7_tophour_pre15 | 0.15 | -113.3 | 16.2 | 0.39 | 0.41 | -129.5 [-285.0, 26.1] | -0.0 | -1.6 | 3 | -123.2 | -114.1 |
| M7/1 | n7_tophour_pre15_with | 0.12 | -106.5 | 11.2 | 0.39 | 0.41 | -117.7 [-281.7, 46.2] | -0.0 | -1.4 | 3 | -143.1 | -74.3 |
| M7/1 | n7_tophour_in_with | 0.15 | 83.4 | -14.9 | 0.44 | 0.40 | 98.3 [-47.2, 243.8] | 0.0 | 1.3 | 3 | 1.7 | -126.3 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | n7_w1000_1100_in_big_with | 0.27 | 167.2 | -16.6 | 0.49 | 0.41 | 183.7 [65.6, 301.8] | 0.6 | 3.0 | 4 | 374.1 | 488.1 |
| M7/3 | n7_tophour_post15_against | 0.12 | -104.7 | 59.8 | 0.38 | 0.44 | -164.5 [-322.2, -6.9] | -0.3 | -2.0 | 4 | -86.1 | -63.5 |
| M7/3 | n7_t1030_post30_with | 0.10 | 198.3 | 22.1 | 0.50 | 0.43 | 176.2 [6.6, 345.7] | 0.3 | 2.0 | 4 | 397.6 | 444.3 |
| M7/3 | n7_grp_nyo_post30_with | 0.10 | 198.3 | 22.1 | 0.50 | 0.43 | 176.2 [6.6, 345.7] | 0.3 | 2.0 | 4 | 397.6 | 444.3 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | n7_halfhour_post15_big_with | 0.46 | 314.9 | 58.8 | 0.43 | 0.32 | 256.1 [43.2, 469.1] | 0.0 | 2.4 | 3 | 321.0 | 830.8 |
| O7/3 | n7_w0950_pre15_big_with | 0.70 | 210.8 | 94.4 | 0.39 | 0.33 | 116.4 [-112.1, 344.8] | 0.0 | 1.0 | 3 | 46.5 | 323.3 |
| O7/3 | n7_macro_xx50_pre15_big_with | 0.70 | 210.8 | 94.4 | 0.39 | 0.33 | 116.4 [-112.1, 344.8] | 0.0 | 1.0 | 3 | 46.5 | 323.3 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | n7_t1800_post30 | 0.09 | 1133.3 | 349.9 | 0.56 | 0.43 | 783.5 [73.9, 1493.0] | 162.7 | 2.2 | 4 | 1144.3 | 2537.1 |
| P7/0 | n7_t1800_post30_with | 0.07 | 1188.6 | 368.0 | 0.56 | 0.43 | 820.6 [22.4, 1618.8] | 140.8 | 2.0 | 4 | 1040.0 | 2081.4 |
| P7/0 | n7_tophour_in | 0.09 | 1042.9 | 365.2 | 0.49 | 0.43 | 677.7 [-17.9, 1373.3] | 145.2 | 1.9 | 4 | 770.1 | -517.5 |
| P7/0 | n7_macro_xx50_post30_against | 0.07 | -174.0 | 470.8 | 0.37 | 0.44 | -644.7 [-1395.8, 106.3] | -122.3 | -1.7 | 3 | -200.4 | 55.5 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | n7_tophour_post30 | 0.27 | -132.4 | 95.5 | 0.34 | 0.39 | -227.9 [-485.5, 29.7] | -0.0 | -1.7 | 4 | -141.2 | 154.7 |
| P7/1 | n7_tophour_post15 | 0.23 | 207.3 | -17.1 | 0.43 | 0.37 | 224.4 [-43.8, 492.6] | 0.0 | 1.6 | 3 | 45.9 | 473.8 |
| P7/1 | n7_macro_xx50_post30_with | 0.17 | -161.5 | 74.1 | 0.34 | 0.39 | -235.6 [-529.9, 58.7] | -0.0 | -1.6 | 4 | -228.4 | 333.5 |
| P7/1 | n7_tophour_post30_against | 0.10 | -237.0 | 64.6 | 0.32 | 0.39 | -301.6 [-680.0, 76.8] | -0.0 | -1.6 | 4 | -154.2 | -814.7 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | n7_w1050_pre15 | 0.13 | 435.6 | -102.2 | 0.49 | 0.37 | 537.8 [133.6, 942.0] | 290.4 | 2.6 | 3 | 1152.5 | 2298.5 |
| P7/3 | n7_tophour_in | 0.15 | -383.7 | 30.3 | 0.30 | 0.40 | -414.0 [-762.3, -65.8] | -253.6 | -2.3 | 3 | -245.6 | -61.8 |
| P7/3 | n7_halfhour_post30_with | 0.18 | -214.7 | 6.2 | 0.34 | 0.40 | -220.9 [-540.6, 98.8] | -144.1 | -1.4 | 3 | -331.8 | -525.4 |
| P7/3 | n7_w0950_in | 0.18 | -214.2 | 4.8 | 0.36 | 0.39 | -219.0 [-574.6, 136.7] | -131.9 | -1.2 | 3 | -231.0 | 749.7 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | n7_tophour_post15_with | 0.22 | 844.3 | 256.8 | 0.59 | 0.51 | 587.5 [-38.5, 1213.6] | 0.0 | 1.8 | 3 | 697.7 | 1487.7 |
| U7/0 | n7_tophour_post15 | 0.26 | 736.4 | 265.0 | 0.57 | 0.51 | 471.4 [-124.6, 1067.4] | 0.0 | 1.6 | 3 | 857.7 | 1407.9 |
| U7/0 | n7_halfhour_post15 | 0.14 | -130.4 | 469.1 | 0.47 | 0.54 | -599.5 [-1397.4, 198.3] | -0.0 | -1.5 | 3 | -723.5 | -709.3 |
| U7/0 | n7_macro_xx50_pre15 | 0.14 | -130.4 | 469.1 | 0.47 | 0.54 | -599.5 [-1397.4, 198.3] | -0.0 | -1.5 | 3 | -723.5 | -709.3 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | n7_tophour_post15_with | 0.23 | 428.7 | 46.2 | 0.53 | 0.49 | 382.5 [-155.1, 920.1] | 0.0 | 1.4 | 3 | 598.1 | 586.8 |
| U7/1 | n7_halfhour_pre15 | 0.19 | -196.1 | 211.7 | 0.50 | 0.51 | -407.8 [-1019.2, 203.6] | -0.0 | -1.3 | 3 | -1056.6 | -2296.1 |
| U7/1 | n7_tophour_post30 | 0.33 | -71.6 | 236.7 | 0.49 | 0.51 | -308.4 [-817.9, 201.2] | -0.0 | -1.2 | 3 | -490.8 | -1462.5 |
| U7/1 | n7_halfhour_pre15_with | 0.18 | -120.7 | 191.6 | 0.51 | 0.50 | -312.2 [-933.8, 309.3] | -0.0 | -1.0 | 3 | -1056.6 | -2296.1 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B7_tod.parquet

### B7 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 443 conditions; 6198 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 78 conditions with |t|>2 (chance alone: about 22). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n7_w1400_1500_post30_with | 0.01 | -4.8 | 1.4 | 0.46 | 0.50 | -6.2 [-8.9, -3.6] | -5.5 | -4.5 | 4 | -8.8 | 4.9 |
| ALL/ALL | n7_w1450_post30_with | 0.01 | -4.7 | 1.4 | 0.46 | 0.50 | -6.1 [-8.8, -3.3] | -5.3 | -4.3 | 4 | -9.6 | -14.0 |
| ALL/ALL | n7_w1450_post30 | 0.01 | -3.2 | 1.4 | 0.47 | 0.50 | -4.6 [-6.9, -2.3] | -4.2 | -3.9 | 4 | -9.7 | -9.8 |
| ALL/ALL | n7_tophour_post30_big_with | 0.00 | 9.8 | 1.3 | 0.56 | 0.50 | 8.5 [4.2, 12.7] | 6.3 | 3.9 | 3 | 11.1 | 8.9 |
| ALL/ALL | n7_t1600_pre15 | 0.01 | -2.5 | 1.4 | 0.48 | 0.50 | -3.9 [-5.9, -1.9] | -3.6 | -3.8 | 3 | -6.4 | -11.3 |
| ALL/ALL | n7_t1600_pre15_with | 0.01 | -2.5 | 1.4 | 0.48 | 0.50 | -3.9 [-6.0, -1.8] | -3.6 | -3.6 | 3 | -6.3 | -11.2 |
| ALL/ALL | n7_t0830_post30_big_with | 0.00 | -7.9 | 1.4 | 0.43 | 0.50 | -9.3 [-14.3, -4.2] | -6.3 | -3.6 | 3 | -25.1 | -24.1 |
| ALL/ALL | n7_t1550_pre15_with | 0.01 | -3.0 | 1.4 | 0.47 | 0.50 | -4.4 [-6.7, -2.0] | -3.9 | -3.6 | 4 | -8.4 | -9.7 |
| ALL/ALL | n7_t1500_post30 | 0.01 | -2.8 | 1.4 | 0.48 | 0.50 | -4.2 [-6.5, -1.9] | -3.8 | -3.6 | 4 | -9.7 | -1.7 |
| ALL/ALL | n7_w1400_1500_post30 | 0.01 | -2.8 | 1.4 | 0.48 | 0.50 | -4.2 [-6.5, -1.9] | -3.8 | -3.6 | 4 | -9.7 | -1.7 |
| ALL/ALL | n7_w0950_post15_against | 0.00 | -7.5 | 1.4 | 0.39 | 0.50 | -8.9 [-13.9, -4.0] | -6.1 | -3.5 | 4 | -9.7 | -10.9 |
| ALL/ALL | n7_t1550_pre15 | 0.01 | -2.6 | 1.4 | 0.47 | 0.50 | -4.0 [-6.3, -1.7] | -3.7 | -3.5 | 3 | -8.9 | -10.6 |
| ALL/ALL | n7_w1400_1500_post30_big_with | 0.00 | -6.2 | 1.4 | 0.44 | 0.50 | -7.6 [-12.2, -3.0] | -5.5 | -3.3 | 3 | -9.3 | 21.8 |
| ALL/ALL | n7_t1500_post30_with | 0.01 | -2.5 | 1.4 | 0.48 | 0.50 | -3.9 [-6.3, -1.5] | -3.6 | -3.2 | 3 | -10.7 | -2.3 |
| ALL/ALL | n7_t0830_pre15_with | 0.01 | -2.5 | 1.4 | 0.47 | 0.50 | -3.9 [-6.4, -1.4] | -3.5 | -3.1 | 3 | -6.6 | -12.5 |
| ALL/ALL | n7_halfhour_post15 | 0.24 | 2.0 | 1.2 | 0.51 | 0.50 | 0.8 [0.3, 1.4] | 0.8 | 3.0 | 4 | 0.5 | 1.3 |
| ALL/ALL | n7_macro_xx50_pre15 | 0.24 | 2.0 | 1.2 | 0.51 | 0.50 | 0.8 [0.3, 1.4] | 0.8 | 3.0 | 4 | 0.5 | 1.3 |
| ALL/ALL | n7_t0300_post15_with | 0.01 | -2.2 | 1.4 | 0.46 | 0.50 | -3.6 [-6.0, -1.3] | -3.3 | -3.0 | 3 | -3.1 | 1.8 |
| ALL/ALL | n7_tophour_post15_against | 0.08 | 0.3 | 1.4 | 0.49 | 0.50 | -1.2 [-2.0, -0.4] | -1.2 | -2.8 | 3 | -1.0 | -1.9 |
| ALL/ALL | n7_grp_rel_pre15_with | 0.02 | -1.1 | 1.4 | 0.49 | 0.50 | -2.5 [-4.3, -0.8] | -2.4 | -2.8 | 4 | -7.2 | -12.3 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n7_halfhour_post15 | 0.24 | 3.4 | 2.4 | 0.52 | 0.51 | 1.0 [0.2, 1.8] | 0.8 | 2.0 | 4 | 0.6 | 2.5 |
| ALL/0 | n7_macro_xx50_pre15 | 0.24 | 3.4 | 2.4 | 0.52 | 0.51 | 1.0 [0.2, 1.8] | 0.8 | 2.0 | 4 | 0.6 | 2.5 |
| ALL/0 | n7_t1800_post5 | 0.02 | -1.3 | 2.7 | 0.49 | 0.52 | -4.0 [-6.7, -1.4] | -1.4 | -1.0 | 4 | -13.8 | -11.1 |
| ALL/0 | n7_tophour_pre15 | 0.24 | 3.0 | 2.6 | 0.52 | 0.51 | 0.5 [-0.3, 1.3] | 0.4 | 1.0 | 4 | 0.3 | -0.9 |
| ALL/0 | n7_t1800_post30_big_with | 0.00 | 16.6 | 2.6 | 0.65 | 0.51 | 14.0 [4.0, 24.0] | 0.5 | 0.1 | 4 | 26.3 | 42.2 |
| ALL/0 | n7_halfhour_pre15_big_with | 0.00 | -7.1 | 2.7 | 0.40 | 0.52 | -9.8 [-20.0, 0.4] | -0.3 | -0.1 | 4 | -30.0 | -21.6 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n7_t0830_pre15_with | 0.04 | -2.5 | 1.4 | 0.47 | 0.50 | -3.9 [-6.4, -1.4] | -3.4 | -2.6 | 4 | -4.8 | -13.8 |
| ALL/1 | n7_grp_rel_pre15_with | 0.04 | -2.5 | 1.4 | 0.47 | 0.50 | -3.9 [-6.4, -1.4] | -3.4 | -2.6 | 4 | -4.8 | -13.8 |
| ALL/1 | n7_halfhour_in | 0.08 | -0.5 | 1.4 | 0.49 | 0.50 | -1.9 [-3.5, -0.4] | -1.8 | -2.4 | 4 | -3.6 | -2.8 |
| ALL/1 | n7_halfhour_in_with | 0.05 | -0.7 | 1.4 | 0.49 | 0.50 | -2.1 [-4.0, -0.2] | -1.9 | -1.9 | 4 | -1.5 | 1.3 |
| ALL/1 | n7_t0200_post30 | 0.04 | 2.4 | 1.2 | 0.51 | 0.50 | 1.2 [-0.9, 3.2] | 1.1 | 1.0 | 4 | 6.0 | -0.3 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | n7_macro_xx50_post30_against | 0.11 | 3.3 | -1.1 | 0.53 | 0.49 | 4.4 [0.6, 8.3] | 2.6 | 1.3 | 4 | 11.1 | 24.3 |
| ALL/2 | n7_halfhour_post30_big_with | 0.03 | -11.9 | -0.3 | 0.40 | 0.50 | -11.6 [-18.8, -4.5] | -3.4 | -0.9 | 4 | -6.1 | -0.9 |
| ALL/2 | n7_grp_rel_post5_with | 0.09 | 2.5 | -1.0 | 0.51 | 0.49 | 3.4 [-0.7, 7.6] | 1.9 | 0.9 | 4 | 8.2 | 19.5 |
| ALL/2 | n7_macro_xx50_post30_big_with | 0.01 | 18.3 | -0.9 | 0.65 | 0.49 | 19.2 [8.6, 29.7] | 3.0 | 0.6 | 4 | 5.0 | -10.0 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n7_w1000_1100_post15_with | 0.08 | 4.8 | 1.2 | 0.53 | 0.49 | 3.5 [1.0, 6.1] | 3.2 | 2.5 | 4 | 15.3 | 8.4 |
| ALL/3 | n7_grp_nyo_post15_with | 0.14 | 3.6 | 1.2 | 0.50 | 0.49 | 2.5 [0.4, 4.5] | 2.3 | 2.2 | 4 | 2.9 | 3.2 |
| ALL/3 | n7_grp_nyo_post15 | 0.15 | 3.2 | 1.2 | 0.50 | 0.49 | 1.9 [-0.1, 3.9] | 1.8 | 1.8 | 4 | 2.3 | 1.9 |
| ALL/3 | n7_t1030_post15_with | 0.05 | 4.6 | 1.4 | 0.52 | 0.49 | 3.2 [0.1, 6.3] | 2.7 | 1.7 | 4 | 2.3 | 8.9 |
| ALL/3 | n7_t1130_post5_with | 0.02 | -3.8 | 1.6 | 0.44 | 0.50 | -5.5 [-10.4, -0.6] | -3.8 | -1.5 | 4 | -25.8 | -25.8 |
| ALL/3 | n7_w0950_in_against | 0.02 | -3.6 | 1.7 | 0.44 | 0.50 | -5.2 [-10.1, -0.4] | -3.7 | -1.5 | 4 | -6.4 | -0.4 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n7_tophour_pre15_big_with | 0.02 | 8.4 | -0.4 | 0.55 | 0.49 | 8.8 [3.3, 14.3] | 7.7 | 2.7 | 4 | 5.2 | 18.4 |
| ALL/4 | n7_macro_xx50_pre15_big_with | 0.01 | 7.2 | -0.4 | 0.55 | 0.49 | 7.6 [1.9, 13.2] | 6.6 | 2.3 | 4 | 11.2 | 13.4 |
| ALL/4 | n7_w1450_in_against | 0.01 | 6.0 | -0.3 | 0.54 | 0.49 | 6.3 [-0.6, 13.2] | 5.2 | 1.5 | 4 | 13.4 | 16.7 |
| ALL/4 | n7_tophour_pre15_against | 0.02 | 2.6 | -0.3 | 0.51 | 0.49 | 3.0 [-1.4, 7.3] | 2.7 | 1.2 | 4 | 8.1 | 9.8 |
| ALL/4 | n7_macro_xx50_pre15_against | 0.02 | -2.9 | -0.2 | 0.46 | 0.49 | -2.7 [-7.1, 1.8] | -2.4 | -1.1 | 4 | -7.6 | 13.2 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | n7_w1450_post30_with | 0.09 | -4.7 | 0.3 | 0.46 | 0.50 | -5.0 [-7.8, -2.1] | -4.2 | -2.8 | 4 | -4.7 | -10.0 |
| ALL/5 | n7_w1450_post30 | 0.14 | -3.2 | 0.3 | 0.47 | 0.50 | -3.5 [-5.9, -1.1] | -3.1 | -2.5 | 4 | -5.0 | -5.6 |
| ALL/5 | n7_t1600_pre15 | 0.17 | -2.5 | 0.3 | 0.48 | 0.50 | -2.8 [-5.0, -0.6] | -2.5 | -2.3 | 4 | -1.3 | -7.6 |
| ALL/5 | n7_t1615_pre15 | 0.12 | 2.5 | -0.5 | 0.52 | 0.49 | 3.0 [0.6, 5.4] | 2.7 | 2.2 | 4 | 4.6 | 18.1 |
| ALL/5 | n7_t1550_pre15_with | 0.13 | -3.0 | 0.2 | 0.47 | 0.50 | -3.2 [-5.7, -0.7] | -2.8 | -2.2 | 4 | -3.6 | -5.5 |
| ALL/5 | n7_t1600_pre15_with | 0.16 | -2.5 | 0.3 | 0.48 | 0.50 | -2.7 [-5.0, -0.5] | -2.5 | -2.1 | 4 | -1.2 | -7.5 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B7_tod.parquet

## ADDENDUM 6 BLOCK 8: opening prices (midnight, 08:30, 09:30, 18:00, week, month, quarter), gaps as levels, session handoff, overnight inventory, cash-open gap

### B8 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 126 conditions; 2685 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 28 conditions with |t|>2 (chance alone: about 6). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n8_cg_filled | 0.45 | -35.7 | 96.0 | 0.40 | 0.45 | -131.7 [-199.2, -64.3] | -112.8 | -3.8 | 4 | -155.1 | -117.6 |
| ALL/ALL | n8_gapD_mid_side_with | 0.53 | 196.3 | 18.6 | 0.46 | 0.42 | 177.7 [80.2, 275.2] | 131.6 | 3.6 | 3 | 299.2 | 220.9 |
| ALL/ALL | n8_on_inv_big_with | 0.06 | 300.5 | 83.3 | 0.48 | 0.43 | 217.3 [86.8, 347.7] | 133.5 | 3.3 | 4 | 148.1 | 86.3 |
| ALL/ALL | n8_cg_unfilled_with | 0.29 | 123.7 | 0.5 | 0.45 | 0.42 | 123.2 [45.9, 200.4] | 101.0 | 3.1 | 3 | 246.5 | 314.9 |
| ALL/ALL | n8_month_side | 0.54 | 150.0 | 54.2 | 0.45 | 0.42 | 95.8 [33.9, 157.7] | 84.0 | 3.0 | 3 | 120.0 | 45.7 |
| ALL/ALL | n8_gapW_unf_behind_3atr | 0.05 | 334.3 | 93.0 | 0.47 | 0.44 | 241.3 [83.0, 399.7] | 125.4 | 3.0 | 4 | 363.9 | 282.8 |
| ALL/ALL | n8_px_onvwap_ext_with1 | 0.31 | 35.9 | 124.6 | 0.42 | 0.44 | -88.7 [-149.4, -28.1] | -78.1 | -2.9 | 4 | -118.9 | 13.9 |
| ALL/ALL | n8_ig_against_half | 0.05 | -38.2 | 113.9 | 0.40 | 0.44 | -152.1 [-261.4, -42.9] | -105.6 | -2.7 | 4 | -273.3 | -461.4 |
| ALL/ALL | n8_gapW_unf_behind_1atr | 0.02 | 479.2 | 97.7 | 0.49 | 0.44 | 381.5 [104.3, 658.6] | 99.5 | 2.7 | 4 | 468.1 | 614.6 |
| ALL/ALL | n8_hoNL_rev_cur_with | 0.33 | 31.3 | 151.3 | 0.43 | 0.45 | -120.0 [-207.9, -32.1] | -93.4 | -2.7 | 4 | -217.6 | -230.4 |
| ALL/ALL | n8_hoNL_ext | 0.50 | 169.7 | 54.0 | 0.46 | 0.44 | 115.7 [30.2, 201.2] | 91.1 | 2.7 | 4 | 7.7 | 120.3 |
| ALL/ALL | n8_hoNL_rev | 0.50 | 54.0 | 169.7 | 0.44 | 0.46 | -115.7 [-201.2, -30.2] | -91.1 | -2.7 | 4 | -7.7 | -120.3 |
| ALL/ALL | n8_gapW_cur_up_with | 0.51 | 146.9 | 63.5 | 0.44 | 0.43 | 83.3 [21.6, 145.1] | 73.1 | 2.6 | 4 | 99.1 | -17.6 |
| ALL/ALL | n8_px_onvwap_ext_against1 | 0.03 | -29.6 | 101.6 | 0.41 | 0.44 | -131.2 [-235.5, -26.9] | -93.6 | -2.5 | 3 | -131.8 | -333.0 |
| ALL/ALL | n8_week_ext_against2 | 0.02 | -123.6 | 111.2 | 0.40 | 0.44 | -234.8 [-427.5, -42.1] | -99.1 | -2.4 | 3 | -302.7 | -174.7 |
| ALL/ALL | n8_ig_with1 | 0.05 | 258.0 | 98.3 | 0.48 | 0.44 | 159.7 [27.3, 292.0] | 97.0 | 2.4 | 3 | 206.1 | 253.6 |
| ALL/ALL | n8_hoAN_cur_with | 0.64 | 148.6 | 31.5 | 0.45 | 0.42 | 117.2 [17.7, 216.6] | 85.8 | 2.3 | 3 | 223.4 | 103.5 |
| ALL/ALL | n8_o1800_ext_against2 | 0.05 | -18.4 | 112.1 | 0.41 | 0.44 | -130.4 [-241.2, -19.7] | -89.8 | -2.3 | 3 | -199.5 | -399.1 |
| ALL/ALL | n8_month_ext_against1 | 0.29 | 50.3 | 129.0 | 0.42 | 0.44 | -78.8 [-146.5, -11.0] | -67.3 | -2.3 | 4 | -38.8 | -5.9 |
| ALL/ALL | n8_week_ext_against1 | 0.11 | 14.7 | 116.9 | 0.42 | 0.44 | -102.1 [-194.4, -9.9] | -77.7 | -2.2 | 4 | -157.5 | -173.8 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n8_gapW_cur_up_with | 0.52 | 312.5 | 145.6 | 0.48 | 0.45 | 167.0 [30.0, 303.9] | 142.1 | 2.0 | 4 | 165.3 | -15.2 |
| ALL/0 | n8_o0930_ext_against1 | 0.27 | 57.5 | 256.5 | 0.43 | 0.47 | -198.9 [-366.7, -31.2] | -157.6 | -1.8 | 4 | -263.1 | -398.6 |
| ALL/0 | n8_intraday_opens_all4 | 0.42 | 302.6 | 129.2 | 0.49 | 0.45 | 173.4 [17.8, 329.1] | 141.5 | 1.8 | 4 | 180.6 | 288.7 |
| ALL/0 | n8_gapW_unf_behind_3atr | 0.08 | 579.9 | 201.9 | 0.53 | 0.46 | 378.1 [116.8, 639.3] | 231.2 | 1.7 | 4 | 504.1 | 476.6 |
| ALL/0 | n8_hoAN_cur_with | 0.77 | 240.2 | -20.5 | 0.47 | 0.42 | 260.7 [50.1, 471.4] | 184.5 | 1.7 | 4 | 373.2 | 139.6 |
| ALL/0 | n8_o0930_ext_against2 | 0.16 | 2.9 | 239.7 | 0.43 | 0.47 | -236.8 [-439.0, -34.5] | -171.5 | -1.7 | 4 | -428.6 | -513.1 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n8_month_ext_against1 | 0.29 | -60.8 | 67.6 | 0.39 | 0.42 | -128.4 [-224.9, -31.9] | -8.4 | -0.2 | 4 | -85.0 | -95.4 |
| ALL/1 | n8_intraday_opens_ge3of4 | 0.52 | -14.0 | 82.8 | 0.41 | 0.42 | -96.8 [-195.8, 2.3] | -6.0 | -0.1 | 4 | -92.0 | 10.9 |
| ALL/1 | n8_px_onvwap_ext_with1 | 0.28 | -33.8 | 55.3 | 0.40 | 0.42 | -89.1 [-191.5, 13.2] | -5.2 | -0.1 | 4 | -169.9 | -82.1 |
| ALL/1 | n8_gapW_cur_up_with | 0.52 | 58.0 | 0.5 | 0.42 | 0.41 | 57.5 [-31.5, 146.4] | 4.4 | 0.1 | 4 | 39.2 | -65.7 |
| ALL/1 | n8_week_near | 0.27 | 89.8 | 8.2 | 0.43 | 0.41 | 81.6 [-19.3, 182.5] | 4.9 | 0.1 | 4 | 141.8 | 259.5 |
| ALL/1 | n8_o0930_ext_against1 | 0.33 | 87.2 | 5.3 | 0.43 | 0.41 | 81.9 [-24.2, 188.0] | 4.5 | 0.1 | 4 | 115.4 | -108.3 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n8_cg_filled | 0.43 | -57.9 | 94.7 | 0.39 | 0.44 | -152.6 [-229.3, -75.9] | -108.3 | -2.8 | 4 | -149.3 | -30.8 |
| ALL/3 | n8_hoNL_ext | 0.50 | 63.7 | -40.9 | 0.44 | 0.41 | 104.7 [24.0, 185.3] | 72.0 | 1.8 | 4 | 49.8 | -60.7 |
| ALL/3 | n8_hoNL_rev | 0.50 | -40.9 | 63.7 | 0.41 | 0.44 | -104.7 [-185.3, -24.0] | -72.0 | -1.8 | 4 | -49.8 | 60.7 |
| ALL/3 | n8_hoNL_ext_cur_with | 0.46 | 66.0 | -34.4 | 0.44 | 0.41 | 100.4 [19.0, 181.8] | 68.7 | 1.7 | 4 | 56.3 | -47.4 |
| ALL/3 | n8_month_near | 0.11 | -124.8 | 46.5 | 0.35 | 0.43 | -171.3 [-284.0, -58.6] | -90.9 | -1.6 | 4 | -70.2 | -107.6 |
| ALL/3 | n8_cg_filled_with_trade_dir | 0.28 | -34.8 | 53.8 | 0.39 | 0.43 | -88.7 [-174.2, -3.1] | -58.7 | -1.3 | 4 | -128.2 | 4.5 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n8_ig_inside_prior_range | 0.42 | -61.7 | 153.0 | 0.42 | 0.49 | -214.7 [-355.7, -73.7] | -102.8 | -1.4 | 4 | -324.6 | -684.6 |
| ALL/4 | n8_o1800_ext_with2 | 0.34 | 194.4 | -6.5 | 0.50 | 0.44 | 200.9 [44.0, 357.8] | 85.5 | 1.1 | 4 | 422.9 | 836.9 |
| ALL/4 | n8_intraday_opens_all4 | 0.48 | 143.0 | -13.9 | 0.48 | 0.44 | 156.9 [14.5, 299.2] | 74.3 | 1.0 | 4 | 341.1 | 789.8 |
| ALL/4 | n8_o0830_ext_with2 | 0.32 | 193.6 | -0.1 | 0.49 | 0.44 | 193.7 [35.7, 351.8] | 81.8 | 1.0 | 4 | 444.0 | 877.1 |
| ALL/4 | n8_week_ext_with1 | 0.19 | 281.2 | 9.6 | 0.54 | 0.44 | 271.6 [81.5, 461.8] | 91.1 | 0.9 | 4 | 383.7 | 513.6 |
| ALL/4 | n8_o0830_ext_with1 | 0.47 | 132.5 | -1.3 | 0.48 | 0.44 | 133.7 [-9.1, 276.5] | 63.2 | 0.9 | 4 | 76.3 | 501.7 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | n8_on_inv_big_with | 0.07 | 450.0 | 91.4 | 0.67 | 0.51 | 358.6 [94.5, 622.7] | 5.9 | 2.7 | 3 | 115.1 | 366.0 |
| A7/0 | n8_o1800_ext_with2 | 0.12 | 320.7 | 86.9 | 0.60 | 0.51 | 233.8 [38.5, 429.1] | 6.9 | 2.3 | 3 | 310.9 | 451.4 |
| A7/0 | n8_gapD_unf_behind_3atr | 0.09 | 345.4 | 93.2 | 0.62 | 0.51 | 252.2 [25.0, 479.4] | 5.5 | 2.2 | 3 | 7.7 | 253.7 |
| A7/0 | n8_hoAN_prev_big | 0.42 | 32.2 | 182.7 | 0.48 | 0.55 | -150.5 [-311.8, 10.8] | -6.4 | -1.8 | 3 | -3.0 | -56.7 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | n8_week_near | 0.33 | 478.7 | 83.8 | 0.52 | 0.46 | 394.9 [1.1, 788.7] | 0.0 | 2.0 | 4 | 373.2 | 267.9 |
| H7/0 | n8_gapD_mid_side_with | 0.61 | 525.8 | -52.0 | 0.52 | 0.46 | 577.8 [-25.7, 1181.3] | 0.0 | 1.9 | 3 | 87.0 | -401.1 |
| H7/0 | n8_gapD_cur_unfilled | 0.17 | 612.0 | 134.6 | 0.54 | 0.47 | 477.4 [-58.9, 1013.7] | 0.0 | 1.7 | 4 | 337.6 | 738.3 |
| H7/0 | n8_mid_cross_with30 | 0.12 | 567.0 | 158.6 | 0.56 | 0.47 | 408.4 [-230.4, 1047.3] | 0.0 | 1.3 | 3 | 61.0 | 735.1 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | n8_cg_filled | 0.44 | -173.3 | 215.3 | 0.39 | 0.55 | -388.6 [-621.3, -155.8] | -213.2 | -3.3 | 4 | -462.2 | 34.5 |
| H7/3 | n8_ig_inside_prior_range | 0.51 | -120.9 | 213.5 | 0.41 | 0.55 | -334.4 [-565.2, -103.6] | -184.8 | -2.8 | 4 | -731.1 | -606.8 |
| H7/3 | n8_cg_outside_range | 0.36 | 243.5 | -64.7 | 0.56 | 0.44 | 308.1 [68.0, 548.2] | 164.3 | 2.5 | 4 | 611.7 | 234.5 |
| H7/3 | n8_cg_inside_range | 0.64 | -64.7 | 243.5 | 0.44 | 0.56 | -308.1 [-548.2, -68.0] | -164.3 | -2.5 | 4 | -611.7 | -234.5 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | n8_hoAN_cur_with | 0.72 | 134.6 | -49.0 | 0.46 | 0.39 | 183.6 [47.6, 319.6] | 0.0 | 2.6 | 4 | 232.2 | 248.4 |
| K7/0 | n8_gapW_unf_behind_3atr | 0.07 | 311.1 | 71.5 | 0.52 | 0.44 | 239.6 [50.9, 428.2] | 0.0 | 2.5 | 4 | 247.1 | 424.2 |
| K7/0 | n8_gapW_unf_behind_1atr | 0.04 | 401.7 | 76.8 | 0.57 | 0.44 | 324.9 [54.5, 595.3] | 0.0 | 2.4 | 3 | 250.5 | 499.5 |
| K7/0 | n8_gapW_cur_up_with | 0.51 | 143.9 | 32.5 | 0.46 | 0.42 | 111.4 [11.0, 211.8] | 0.0 | 2.2 | 4 | 69.7 | -26.9 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | n8_mid_ext_with2 | 0.11 | -108.2 | 53.4 | 0.39 | 0.43 | -161.6 [-356.5, 33.3] | -0.0 | -1.6 | 4 | -56.1 | 48.5 |
| K7/1 | n8_o1800_cross_with30 | 0.09 | -103.0 | 48.9 | 0.37 | 0.43 | -152.0 [-342.5, 38.6] | -0.0 | -1.6 | 3 | -412.7 | -421.0 |
| K7/1 | n8_hoLA_ext | 0.51 | 65.5 | -23.0 | 0.44 | 0.40 | 88.5 [-31.0, 208.0] | 0.0 | 1.5 | 3 | 150.6 | 128.1 |
| K7/1 | n8_hoLA_rev | 0.49 | -23.0 | 65.5 | 0.40 | 0.44 | -88.5 [-208.0, 31.0] | -0.0 | -1.5 | 3 | -150.6 | -128.1 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | n8_cg_large | 0.26 | 98.5 | -19.7 | 0.46 | 0.41 | 118.2 [2.2, 234.1] | 0.0 | 2.0 | 4 | 158.0 | -72.6 |
| K7/3 | n8_ig_with1 | 0.08 | 172.6 | -4.4 | 0.50 | 0.42 | 177.0 [-6.2, 360.2] | 0.0 | 1.9 | 3 | 463.8 | 68.2 |
| K7/3 | n8_on_inv_big_with | 0.07 | 177.3 | -1.8 | 0.50 | 0.42 | 179.1 [-22.4, 380.6] | 0.0 | 1.7 | 4 | 49.6 | 56.1 |
| K7/3 | n8_o0830_ext_against1 | 0.10 | -111.5 | 23.6 | 0.37 | 0.43 | -135.0 [-297.6, 27.5] | -0.0 | -1.6 | 4 | -347.3 | -368.3 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | n8_ig_inside_prior_range | 0.42 | -61.7 | 153.0 | 0.42 | 0.49 | -214.7 [-355.7, -73.7] | -102.8 | -3.0 | 4 | -324.6 | -684.6 |
| K7/4 | n8_week_ext_with1 | 0.19 | 281.2 | 9.6 | 0.54 | 0.44 | 271.6 [81.5, 461.8] | 91.1 | 2.8 | 4 | 383.7 | 513.6 |
| K7/4 | n8_ig_with1 | 0.12 | 366.1 | 21.3 | 0.54 | 0.45 | 344.8 [100.0, 589.6] | 80.5 | 2.8 | 4 | 1560.7 | 1900.7 |
| K7/4 | n8_o1800_ext_with2 | 0.34 | 194.4 | -6.5 | 0.50 | 0.44 | 200.9 [44.0, 357.8] | 85.5 | 2.5 | 4 | 422.9 | 836.9 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | n8_week_near | 0.27 | 90.6 | -37.9 | 0.44 | 0.39 | 128.5 [8.9, 248.2] | 2.3 | 2.1 | 4 | 294.2 | 263.6 |
| M7/1 | n8_mid_ext_with2 | 0.09 | -196.4 | 16.3 | 0.35 | 0.41 | -212.7 [-422.3, -3.2] | -1.2 | -2.0 | 4 | -127.6 | 126.7 |
| M7/1 | n8_on_inv_big_against | 0.05 | -229.1 | 10.4 | 0.31 | 0.41 | -239.4 [-475.6, -3.3] | -1.1 | -2.0 | 3 | -310.7 | -322.1 |
| M7/1 | n8_quarter_near | 0.07 | -167.7 | 9.8 | 0.32 | 0.41 | -177.5 [-371.9, 16.9] | -1.2 | -1.8 | 4 | -260.4 | -237.7 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | n8_month_near | 0.12 | -161.6 | 67.4 | 0.33 | 0.45 | -229.0 [-381.4, -76.6] | -18.0 | -2.9 | 4 | -122.7 | -246.2 |
| M7/3 | n8_on_inv_big_with | 0.07 | 252.6 | 24.3 | 0.54 | 0.43 | 228.3 [22.1, 434.4] | 10.2 | 2.2 | 3 | 173.3 | 388.2 |
| M7/3 | n8_cg_filled | 0.45 | -18.7 | 90.4 | 0.40 | 0.46 | -109.1 [-213.3, -4.9] | -16.8 | -2.1 | 4 | -66.7 | -70.5 |
| M7/3 | n8_gapW_unf_ahead_3atr | 0.05 | -191.2 | 51.3 | 0.31 | 0.44 | -242.5 [-475.5, -9.5] | -8.5 | -2.0 | 3 | -371.9 | -122.6 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | n8_o1800_ext_with2 | 0.33 | 284.6 | 123.8 | 0.42 | 0.35 | 160.8 [-68.4, 390.0] | 0.0 | 1.4 | 3 | 624.1 | 1082.5 |
| O7/3 | n8_on_inv_with | 0.49 | 243.9 | 111.7 | 0.41 | 0.34 | 132.1 [-80.0, 344.3] | 0.0 | 1.2 | 4 | 353.6 | 481.6 |
| O7/3 | n8_o0830_ext_with1 | 0.48 | 229.9 | 126.0 | 0.39 | 0.35 | 103.9 [-108.6, 316.4] | 0.0 | 1.0 | 3 | 224.6 | 409.9 |
| O7/3 | n8_hoLA_rev | 0.47 | 219.7 | 136.8 | 0.39 | 0.36 | 82.8 [-130.1, 295.8] | 0.0 | 0.8 | 3 | 147.3 | -95.3 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | n8_week_ext_against1 | 0.09 | -364.1 | 502.0 | 0.34 | 0.45 | -866.1 [-1482.6, -249.6] | -210.9 | -2.8 | 3 | -1264.2 | -802.3 |
| P7/0 | n8_mid_ext_against2 | 0.15 | -318.5 | 488.1 | 0.35 | 0.45 | -806.6 [-1380.8, -232.3] | -218.2 | -2.8 | 4 | -1379.8 | -1195.1 |
| P7/0 | n8_mid_ext_against1 | 0.23 | -95.3 | 505.8 | 0.38 | 0.45 | -601.1 [-1100.9, -101.2] | -197.5 | -2.4 | 3 | -1079.8 | -1616.1 |
| P7/0 | n8_gapW_cur_up_with | 0.52 | 637.8 | 194.9 | 0.46 | 0.42 | 442.9 [52.1, 833.6] | 197.0 | 2.2 | 4 | 374.3 | -0.7 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | n8_hoAN_prev_big | 0.51 | 151.3 | -78.2 | 0.39 | 0.37 | 229.4 [-27.8, 486.6] | 0.0 | 1.7 | 4 | 192.3 | 150.0 |
| P7/1 | n8_hoLA_prev_big | 0.17 | -140.7 | 80.0 | 0.34 | 0.39 | -220.6 [-511.6, 70.4] | -0.0 | -1.5 | 4 | -293.8 | -365.8 |
| P7/1 | n8_o0830_ext_against1 | 0.32 | 126.3 | -16.7 | 0.39 | 0.37 | 143.0 [-125.0, 410.9] | 0.0 | 1.0 | 3 | 277.8 | 269.1 |
| P7/1 | n8_intraday_opens_ge3of4 | 0.54 | -29.1 | 95.1 | 0.38 | 0.38 | -124.2 [-379.7, 131.3] | -0.0 | -1.0 | 4 | -224.9 | 92.5 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | n8_o0930_side | 0.91 | 12.9 | -511.3 | 0.39 | 0.35 | 524.1 [146.9, 901.3] | 161.4 | 2.7 | 3 | 561.5 | 53.5 |
| P7/3 | n8_hoNL_cur_with | 0.91 | 11.6 | -511.3 | 0.39 | 0.35 | 522.9 [145.6, 900.1] | 161.0 | 2.7 | 3 | 561.5 | 53.5 |
| P7/3 | n8_ig_with_half | 0.32 | 209.2 | -146.3 | 0.43 | 0.37 | 355.5 [56.5, 654.5] | 147.4 | 2.3 | 3 | 752.8 | 273.8 |
| P7/3 | n8_o1800_ext_with1 | 0.55 | 100.6 | -198.5 | 0.40 | 0.37 | 299.2 [43.9, 554.4] | 147.4 | 2.3 | 3 | 939.5 | 925.9 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | n8_week_ext_with1 | 0.10 | -372.5 | 465.9 | 0.42 | 0.54 | -838.4 [-1709.7, 33.0] | -0.0 | -1.9 | 3 | -674.8 | -1773.7 |
| U7/0 | n8_hoNL_rev_cur_with | 0.17 | -206.7 | 476.2 | 0.47 | 0.54 | -682.9 [-1449.6, 83.9] | -0.0 | -1.7 | 3 | -775.5 | -148.1 |
| U7/0 | n8_o0930_ext_with1 | 0.22 | -36.0 | 474.8 | 0.50 | 0.54 | -510.7 [-1226.8, 205.4] | -0.0 | -1.4 | 3 | -313.6 | 605.6 |
| U7/0 | n8_o1800_cross_with30 | 0.30 | 653.9 | 271.5 | 0.58 | 0.51 | 382.4 [-160.6, 925.5] | 0.0 | 1.4 | 4 | 227.8 | -661.3 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | n8_month_ext_against1 | 0.32 | -213.2 | 294.6 | 0.46 | 0.53 | -507.8 [-1009.5, -6.1] | -8.2 | -2.0 | 4 | -441.0 | -902.4 |
| U7/1 | n8_hoLA_prev_with | 0.33 | -192.0 | 329.6 | 0.46 | 0.53 | -521.6 [-1076.5, 33.4] | -6.9 | -1.8 | 3 | -355.8 | -1154.5 |
| U7/1 | n8_mid_near | 0.27 | 478.1 | 6.8 | 0.54 | 0.49 | 471.3 [-56.1, 998.6] | 6.9 | 1.8 | 4 | 902.0 | 2154.4 |
| U7/1 | n8_o1800_side | 0.43 | -90.2 | 305.9 | 0.49 | 0.51 | -396.2 [-877.2, 84.9] | -6.9 | -1.6 | 4 | -685.8 | -577.2 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B8_open.parquet

### B8 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 128 conditions; 5190 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 97 conditions with |t|>2 (chance alone: about 6). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n8_gapD_mid_side_with | 0.54 | 4.2 | -0.4 | 0.53 | 0.49 | 4.6 [3.9, 5.3] | 4.5 | 13.4 | 3 | 12.2 | 16.0 |
| ALL/ALL | n8_on_inv_with | 0.56 | 2.7 | -0.4 | 0.52 | 0.48 | 3.1 [2.7, 3.6] | 3.1 | 13.1 | 4 | 6.1 | 2.8 |
| ALL/ALL | n8_cg_unfilled_with | 0.28 | 5.0 | -1.1 | 0.53 | 0.48 | 6.1 [5.1, 7.0] | 5.9 | 12.6 | 4 | 9.3 | 13.6 |
| ALL/ALL | n8_gapD_cur_up_with | 0.51 | 2.7 | -0.1 | 0.52 | 0.49 | 2.8 [2.4, 3.3] | 2.8 | 12.2 | 3 | 1.2 | -0.4 |
| ALL/ALL | n8_ig_with_half | 0.18 | 4.4 | 0.7 | 0.53 | 0.50 | 3.7 [3.1, 4.4] | 3.7 | 11.8 | 4 | 3.4 | 4.7 |
| ALL/ALL | n8_on_inv_big_with | 0.05 | 7.5 | 1.0 | 0.55 | 0.50 | 6.5 [5.4, 7.6] | 6.2 | 11.7 | 4 | 5.5 | 0.5 |
| ALL/ALL | n8_ig_inside_prior_range | 0.63 | 0.4 | 2.9 | 0.49 | 0.52 | -2.5 [-3.0, -2.0] | -2.5 | -10.4 | 4 | -1.5 | -0.5 |
| ALL/ALL | n8_gapD_unf_behind_3atr | 0.04 | 7.1 | 1.1 | 0.56 | 0.50 | 6.0 [4.8, 7.1] | 5.6 | 10.2 | 3 | 7.9 | 7.4 |
| ALL/ALL | n8_hoLA_ext_cur_with | 0.36 | 2.8 | -0.5 | 0.51 | 0.49 | 3.2 [2.6, 3.8] | 3.2 | 10.2 | 3 | 7.4 | 3.3 |
| ALL/ALL | n8_gapD_unf_behind_1atr | 0.01 | 11.2 | 1.2 | 0.62 | 0.50 | 9.9 [8.0, 11.8] | 8.6 | 10.2 | 3 | 6.6 | 14.1 |
| ALL/ALL | n8_ig_with1 | 0.05 | 6.6 | 1.1 | 0.54 | 0.50 | 5.5 [4.4, 6.6] | 5.2 | 10.0 | 4 | 7.7 | 10.9 |
| ALL/ALL | n8_month_side | 0.55 | 2.4 | 0.1 | 0.52 | 0.49 | 2.2 [1.8, 2.7] | 2.2 | 9.7 | 3 | 5.0 | -0.4 |
| ALL/ALL | n8_o1800_ext_with2 | 0.22 | 3.5 | 0.8 | 0.52 | 0.50 | 2.7 [2.2, 3.3] | 2.7 | 9.3 | 3 | 5.6 | 5.9 |
| ALL/ALL | n8_cg_filled | 0.49 | -1.4 | 2.6 | 0.48 | 0.51 | -4.0 [-4.8, -3.1] | -3.9 | -9.2 | 4 | -2.2 | -5.7 |
| ALL/ALL | n8_hoNL_ext_cur_with | 0.35 | 3.0 | 0.1 | 0.52 | 0.49 | 2.9 [2.3, 3.5] | 2.9 | 9.1 | 4 | 3.2 | 11.0 |
| ALL/ALL | n8_month_ext_against1 | 0.28 | -0.3 | 2.0 | 0.48 | 0.51 | -2.3 [-2.8, -1.8] | -2.2 | -8.9 | 4 | -3.7 | 2.0 |
| ALL/ALL | n8_cg_gap_with | 0.52 | 2.4 | -1.4 | 0.51 | 0.48 | 3.8 [2.9, 4.6] | 3.7 | 8.7 | 4 | 9.8 | 8.7 |
| ALL/ALL | n8_cg_gap_against | 0.48 | -1.4 | 2.4 | 0.48 | 0.51 | -3.8 [-4.6, -2.9] | -3.7 | -8.7 | 4 | -9.8 | -8.7 |
| ALL/ALL | n8_px_vs_onvwap_with | 0.85 | 1.8 | -1.1 | 0.51 | 0.48 | 2.9 [2.3, 3.6] | 2.9 | 8.7 | 4 | 5.5 | 6.9 |
| ALL/ALL | n8_hoAN_cur_with | 0.65 | 2.5 | -0.3 | 0.52 | 0.48 | 2.8 [2.1, 3.4] | 2.7 | 8.4 | 3 | 9.0 | 1.9 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n8_gapD_unf_behind_1atr | 0.03 | 16.4 | 2.3 | 0.68 | 0.51 | 14.1 [12.0, 16.3] | 13.1 | 11.8 | 4 | 6.2 | 14.2 |
| ALL/0 | n8_on_inv_big_with | 0.04 | 12.8 | 2.3 | 0.61 | 0.51 | 10.5 [8.5, 12.4] | 9.8 | 10.1 | 4 | 2.4 | -4.3 |
| ALL/0 | n8_hoAN_cur_with | 0.78 | 3.2 | -1.7 | 0.52 | 0.47 | 4.9 [4.0, 5.8] | 4.8 | 10.1 | 4 | 7.8 | 1.3 |
| ALL/0 | n8_intraday_opens_all4 | 0.41 | 4.4 | 0.6 | 0.53 | 0.49 | 3.8 [3.0, 4.6] | 3.7 | 9.3 | 4 | 4.7 | 10.6 |
| ALL/0 | n8_o0830_ext_against2 | 0.18 | -1.6 | 3.0 | 0.48 | 0.52 | -4.5 [-5.5, -3.6] | -4.5 | -9.1 | 4 | -4.3 | -5.0 |
| ALL/0 | n8_week_ext_against1 | 0.09 | -2.2 | 3.2 | 0.46 | 0.52 | -5.4 [-6.6, -4.1] | -5.2 | -8.4 | 4 | -10.0 | -6.3 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n8_month_ext_against1 | 0.29 | -3.0 | 3.0 | 0.45 | 0.52 | -5.9 [-6.9, -5.0] | -5.8 | -12.2 | 4 | -8.3 | -3.0 |
| ALL/1 | n8_on_inv_big_with | 0.05 | 6.5 | 1.0 | 0.54 | 0.50 | 5.5 [3.3, 7.6] | 4.9 | 4.5 | 4 | 7.4 | 3.7 |
| ALL/1 | n8_ig_inside_prior_range | 0.67 | 0.6 | 2.7 | 0.50 | 0.51 | -2.1 [-3.0, -1.2] | -2.1 | -4.4 | 4 | -2.7 | 2.6 |
| ALL/1 | n8_gapW_inside_unf | 0.02 | 7.4 | 1.1 | 0.57 | 0.50 | 6.3 [3.3, 9.4] | 5.2 | 3.4 | 4 | 10.8 | 11.4 |
| ALL/1 | n8_gapD_unf_behind_3atr | 0.04 | 5.5 | 1.1 | 0.54 | 0.50 | 4.4 [2.1, 6.7] | 3.9 | 3.3 | 4 | 13.7 | 18.6 |
| ALL/1 | n8_o0830_cross_with30 | 0.04 | -1.9 | 1.3 | 0.46 | 0.50 | -3.2 [-5.8, -0.7] | -2.8 | -2.2 | 4 | -6.8 | -9.6 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | n8_mid_near | 0.11 | 8.2 | -1.7 | 0.56 | 0.48 | 10.0 [6.2, 13.8] | 8.9 | 4.6 | 4 | 11.8 | -10.1 |
| ALL/2 | n8_gapW_cur_up_with | 0.53 | -3.4 | 2.4 | 0.47 | 0.52 | -5.8 [-8.2, -3.4] | -5.6 | -4.5 | 4 | -4.4 | -12.6 |
| ALL/2 | n8_gapD_mid_side_with | 0.52 | 3.7 | -5.4 | 0.53 | 0.45 | 9.1 [5.5, 12.7] | 8.2 | 4.5 | 4 | 33.1 | 87.6 |
| ALL/2 | n8_gapW_unf_behind_3atr | 0.03 | -21.2 | -0.1 | 0.31 | 0.50 | -21.1 [-28.3, -14.0] | -14.9 | -4.1 | 4 | -28.2 | -29.2 |
| ALL/2 | n8_gapD_unf_ahead_ge1 | 0.23 | -5.0 | 0.7 | 0.45 | 0.50 | -5.7 [-8.5, -2.8] | -5.3 | -3.7 | 4 | -12.9 | -57.0 |
| ALL/2 | n8_mid_cross_with30 | 0.13 | 1.8 | -1.0 | 0.51 | 0.49 | 2.8 [-0.8, 6.4] | 2.6 | 1.4 | 4 | 11.7 | -3.1 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n8_gapD_mid_side_with | 0.53 | 6.3 | -3.6 | 0.54 | 0.45 | 9.8 [7.7, 12.0] | 8.9 | 8.2 | 4 | 7.5 | -12.5 |
| ALL/3 | n8_ig_inside_prior_range | 0.51 | -1.1 | 4.2 | 0.47 | 0.52 | -5.3 [-6.8, -3.9] | -5.1 | -7.1 | 4 | -12.9 | -6.7 |
| ALL/3 | n8_gapD_unf_ahead_ge1 | 0.23 | -2.1 | 2.6 | 0.46 | 0.50 | -4.7 [-6.4, -3.0] | -4.4 | -5.2 | 4 | -2.9 | 0.6 |
| ALL/3 | n8_hoNL_ext | 0.51 | 3.4 | -0.4 | 0.51 | 0.48 | 3.7 [2.1, 5.3] | 3.5 | 4.3 | 4 | 3.8 | 3.8 |
| ALL/3 | n8_hoNL_rev | 0.49 | -0.4 | 3.4 | 0.48 | 0.51 | -3.7 [-5.3, -2.1] | -3.5 | -4.3 | 4 | -3.8 | -3.8 |
| ALL/3 | n8_hoNL_ext_cur_with | 0.48 | 3.4 | -0.2 | 0.51 | 0.48 | 3.6 [2.0, 5.2] | 3.4 | 4.2 | 4 | 3.9 | 5.2 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n8_cg_unfilled_with | 0.27 | 7.4 | -2.9 | 0.55 | 0.47 | 10.4 [8.8, 11.9] | 10.2 | 13.1 | 4 | 13.8 | 23.2 |
| ALL/4 | n8_ig_inside_prior_range | 0.42 | -5.2 | 3.3 | 0.45 | 0.52 | -8.6 [-9.9, -7.2] | -8.4 | -12.2 | 4 | -15.5 | -18.6 |
| ALL/4 | n8_o1800_ext_with2 | 0.43 | 4.5 | -3.9 | 0.53 | 0.46 | 8.5 [7.1, 9.8] | 8.3 | 12.1 | 4 | 19.2 | 26.9 |
| ALL/4 | n8_on_inv_with | 0.51 | 3.5 | -4.1 | 0.52 | 0.46 | 7.6 [6.2, 8.9] | 7.4 | 10.9 | 4 | 9.1 | 8.4 |
| ALL/4 | n8_ig_with_half | 0.39 | 3.9 | -3.0 | 0.52 | 0.47 | 6.9 [5.5, 8.3] | 6.8 | 9.6 | 4 | 16.0 | 24.2 |
| ALL/4 | n8_mid_ext_with2 | 0.43 | 3.3 | -3.0 | 0.52 | 0.47 | 6.3 [4.9, 7.6] | 6.2 | 9.0 | 4 | 14.9 | 27.2 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | n8_cg_gap_against | 0.47 | -1.9 | 1.4 | 0.48 | 0.50 | -3.4 [-5.0, -1.7] | -3.3 | -3.9 | 4 | -3.1 | -4.6 |
| ALL/5 | n8_cg_gap_with | 0.53 | 1.4 | -1.9 | 0.50 | 0.48 | 3.4 [1.7, 5.0] | 3.3 | 3.9 | 4 | 3.1 | 4.6 |
| ALL/5 | n8_o0930_near | 0.07 | -3.3 | 0.1 | 0.47 | 0.49 | -3.4 [-6.5, -0.2] | -3.0 | -1.8 | 4 | -6.5 | -10.6 |
| ALL/5 | n8_o0930_ext_against1 | 0.18 | 1.4 | -0.5 | 0.52 | 0.49 | 1.9 [-0.3, 4.0] | 1.8 | 1.6 | 4 | 8.2 | -9.4 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B8_open.parquet

## ADDENDUM 6 BLOCK 9: week and session structure (week extreme odds, Monday range, month position, session extensions, 90-minute quarters, AMD phase)

### B9 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 69 conditions; 1630 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 13 conditions with |t|>2 (chance alone: about 3). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n9_mo_pos_top20 | 0.30 | 187.5 | 72.7 | 0.45 | 0.43 | 114.8 [44.3, 185.3] | 75.1 | 3.2 | 4 | 36.7 | 142.2 |
| ALL/ALL | n9_mon_ext_against0 | 0.21 | -2.1 | 124.2 | 0.42 | 0.44 | -126.3 [-208.0, -44.6] | -73.9 | -3.0 | 4 | -203.5 | -304.9 |
| ALL/ALL | n9_q1_consol | 0.38 | 154.3 | 51.8 | 0.46 | 0.42 | 102.5 [30.4, 174.5] | 66.0 | 2.8 | 3 | 241.2 | 419.1 |
| ALL/ALL | n9_q3_complete_with | 0.63 | 215.2 | -5.0 | 0.47 | 0.42 | 220.2 [50.3, 390.1] | 54.1 | 2.5 | 3 | 439.6 | 663.9 |
| ALL/ALL | n9_wk_used_gt100 | 0.20 | 20.4 | 113.6 | 0.41 | 0.44 | -93.2 [-168.7, -17.6] | -58.0 | -2.4 | 4 | -167.6 | -377.1 |
| ALL/ALL | n9_amd_dist_against | 0.06 | -31.4 | 102.3 | 0.41 | 0.44 | -133.7 [-243.9, -23.5] | -58.3 | -2.4 | 3 | -134.1 | -573.4 |
| ALL/ALL | n9_q4_live_fade_with | 0.33 | 46.6 | 244.3 | 0.43 | 0.48 | -197.8 [-365.2, -30.3] | -49.6 | -2.3 | 3 | -484.5 | -502.9 |
| ALL/ALL | n9_wk_pos_mid | 0.17 | 17.0 | 110.5 | 0.42 | 0.44 | -93.6 [-174.8, -12.3] | -55.0 | -2.3 | 3 | -88.0 | 115.2 |
| ALL/ALL | n9_mon_ext_against2 | 0.02 | -151.3 | 103.0 | 0.40 | 0.44 | -254.3 [-487.3, -21.3] | -37.5 | -2.1 | 4 | -72.4 | 428.1 |
| ALL/ALL | n9_amd_dist_with | 0.60 | 124.7 | 48.6 | 0.44 | 0.42 | 76.0 [5.1, 147.0] | 49.5 | 2.1 | 4 | 84.9 | 97.3 |
| ALL/ALL | n9_q_in4 | 0.23 | 173.5 | 85.6 | 0.46 | 0.43 | 87.9 [2.0, 173.8] | 49.2 | 2.0 | 4 | 62.3 | 44.0 |
| ALL/ALL | n9_ysame_ext1_with | 0.24 | 167.9 | 79.3 | 0.46 | 0.43 | 88.6 [0.9, 176.4] | 48.7 | 2.0 | 3 | 178.7 | 381.4 |
| ALL/ALL | n9_ysame_break_with | 0.47 | 136.7 | 68.2 | 0.45 | 0.43 | 68.4 [-2.1, 139.0] | 44.8 | 1.9 | 3 | 67.6 | 202.9 |
| ALL/ALL | n9_mon_ext_against1 | 0.05 | -27.8 | 105.4 | 0.41 | 0.44 | -133.1 [-274.3, 8.0] | -42.7 | -1.8 | 3 | -7.8 | -20.0 |
| ALL/ALL | n9_ysame_ext05_with | 0.34 | 146.2 | 76.7 | 0.45 | 0.43 | 69.5 [-6.3, 145.3] | 43.1 | 1.8 | 3 | 39.8 | 147.2 |
| ALL/ALL | n9_mon_ext_with1 | 0.10 | 187.8 | 88.5 | 0.46 | 0.44 | 99.3 [-15.6, 214.1] | 41.3 | 1.7 | 3 | 141.4 | -134.1 |
| ALL/ALL | n9_asia_ext1_with | 0.16 | 80.7 | 23.5 | 0.45 | 0.42 | 57.2 [-18.7, 133.1] | 35.4 | 1.5 | 3 | 261.2 | 286.7 |
| ALL/ALL | n9_fhour_ext1_with | 0.18 | 164.4 | 87.4 | 0.45 | 0.43 | 77.1 [-31.8, 185.9] | 34.1 | 1.4 | 3 | 131.5 | 67.3 |
| ALL/ALL | n9_ysame_break_against | 0.27 | 61.8 | 114.2 | 0.43 | 0.44 | -52.4 [-132.3, 27.5] | -31.2 | -1.3 | 3 | -182.6 | -327.7 |
| ALL/ALL | n9_q_in2 | 0.30 | 77.9 | 118.1 | 0.43 | 0.44 | -40.1 [-101.3, 21.1] | -28.7 | -1.3 | 3 | -50.1 | -2.1 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n9_wk_pos_top20 | 0.37 | 369.9 | 119.8 | 0.50 | 0.44 | 250.1 [100.8, 399.4] | 177.9 | 2.3 | 4 | 87.5 | 395.7 |
| ALL/0 | n9_mo_pos_top20 | 0.30 | 425.6 | 168.9 | 0.50 | 0.45 | 256.7 [97.3, 416.1] | 175.5 | 2.2 | 4 | 33.6 | 192.4 |
| ALL/0 | n9_wk_used_gt100 | 0.21 | -6.4 | 271.2 | 0.41 | 0.48 | -277.6 [-447.8, -107.4] | -181.7 | -2.1 | 4 | -369.8 | -734.2 |
| ALL/0 | n9_mon_ext_against0 | 0.18 | -51.0 | 258.0 | 0.41 | 0.47 | -309.0 [-502.4, -115.7] | -183.8 | -1.9 | 4 | -457.2 | -546.2 |
| ALL/0 | n9_amd_dist_with | 0.53 | 309.3 | 126.9 | 0.50 | 0.44 | 182.4 [14.9, 349.8] | 120.7 | 1.4 | 4 | 135.6 | 69.6 |
| ALL/0 | n9_ysame_break_with | 0.48 | 271.4 | 133.5 | 0.48 | 0.44 | 138.0 [-17.2, 293.1] | 95.9 | 1.2 | 4 | 146.1 | 340.6 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n9_wk_opp_ext_in_odds50 | 0.32 | 135.3 | -20.3 | 0.45 | 0.40 | 155.5 [59.9, 251.1] | 101.8 | 2.1 | 4 | 17.1 | 62.3 |
| ALL/1 | n9_q1_consol | 0.32 | 165.6 | -57.4 | 0.45 | 0.39 | 223.0 [98.7, 347.2] | 117.8 | 1.9 | 4 | 408.4 | 483.5 |
| ALL/1 | n9_q1_range_gt_avg | 0.37 | -76.4 | 67.2 | 0.38 | 0.42 | -143.6 [-259.4, -27.7] | -80.8 | -1.4 | 4 | -234.9 | -210.8 |
| ALL/1 | n9_q_in3 | 0.19 | -33.0 | 44.6 | 0.39 | 0.42 | -77.7 [-189.2, 33.8] | -45.2 | -0.8 | 4 | -131.7 | 59.8 |
| ALL/1 | n9_mon_ext_against1 | 0.06 | 225.0 | 19.5 | 0.46 | 0.41 | 205.5 [-3.9, 415.0] | 58.1 | 0.5 | 4 | 365.2 | 111.1 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n9_psess_ext1_with | 0.36 | 70.6 | 3.7 | 0.43 | 0.41 | 66.9 [-16.6, 150.5] | 39.1 | 0.9 | 4 | 251.7 | 304.9 |
| ALL/3 | n9_mo_used_gt100 | 0.25 | 9.3 | 37.0 | 0.41 | 0.43 | -27.7 [-116.4, 61.0] | -15.4 | -0.3 | 4 | -70.2 | -458.9 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n9_wk_pos_top20 | 0.34 | 197.3 | -8.6 | 0.51 | 0.43 | 205.9 [49.9, 361.9] | 0.0 | 0.0 | 4 | 299.0 | 771.6 |
| ALL/4 | n9_wk_opp_ext_in | 0.51 | -1.1 | 127.5 | 0.43 | 0.48 | -128.6 [-270.5, 13.2] | -0.0 | -0.0 | 4 | -117.2 | -909.4 |
| ALL/4 | n9_asia_ext1_with | 0.30 | 188.2 | 7.3 | 0.50 | 0.44 | 180.9 [18.8, 343.0] | 0.0 | 0.0 | 4 | 425.7 | 791.5 |
| ALL/4 | n9_wk_pos_mid | 0.18 | -119.2 | 101.1 | 0.37 | 0.48 | -220.3 [-393.6, -47.0] | -0.0 | -0.0 | 4 | -231.7 | -223.5 |
| ALL/4 | n9_mon_inside | 0.36 | -49.5 | 112.3 | 0.41 | 0.48 | -161.9 [-320.6, -3.1] | -0.0 | -0.0 | 4 | -99.5 | -532.3 |
| ALL/4 | n9_asia_ext05_with | 0.41 | 124.4 | 19.1 | 0.47 | 0.45 | 105.3 [-41.9, 252.6] | 0.0 | 0.0 | 4 | 355.3 | 559.7 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | n9_amd_acc | 0.30 | -40.2 | 199.6 | 0.46 | 0.56 | -239.7 [-390.5, -89.0] | -30.5 | -3.1 | 4 | -278.4 | -294.8 |
| A7/0 | n9_mon_ext_against0 | 0.16 | -93.8 | 173.5 | 0.43 | 0.55 | -267.3 [-470.1, -64.5] | -19.9 | -2.6 | 4 | -485.4 | -410.0 |
| A7/0 | n9_amd_dist_with | 0.85 | 230.2 | -52.6 | 0.57 | 0.44 | 282.9 [55.8, 509.9] | 17.1 | 2.4 | 3 | 409.0 | 459.4 |
| A7/0 | n9_q_in1 | 0.24 | -25.9 | 159.2 | 0.46 | 0.54 | -185.1 [-339.9, -30.3] | -22.5 | -2.3 | 3 | -211.8 | -144.6 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | n9_amd_manip_dir_against | 0.20 | 500.8 | 126.4 | 0.54 | 0.47 | 374.4 [-131.4, 880.2] | 0.0 | 1.5 | 3 | 323.9 | 276.6 |
| H7/0 | n9_ysame_inside | 0.26 | -12.3 | 284.0 | 0.42 | 0.50 | -296.2 [-745.4, 153.0] | -0.0 | -1.3 | 3 | -1088.7 | -865.0 |
| H7/0 | n9_wk_opp_ext_in | 0.67 | 284.7 | 78.4 | 0.50 | 0.44 | 206.3 [-206.4, 619.0] | 0.0 | 1.0 | 3 | 409.8 | 266.6 |
| H7/0 | n9_fhour_ext1_with | 0.17 | 35.1 | 305.0 | 0.47 | 0.49 | -269.9 [-902.3, 362.5] | -0.0 | -0.8 | 3 | -70.0 | 231.6 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | n9_ysame_break_with | 0.53 | 179.2 | -51.6 | 0.55 | 0.44 | 230.8 [-38.2, 499.8] | 0.0 | 1.7 | 4 | 289.3 | 584.5 |
| H7/3 | n9_q1_consol | 0.48 | 116.9 | -27.0 | 0.51 | 0.46 | 143.9 [-89.1, 376.9] | 0.0 | 1.2 | 3 | 586.4 | 1209.2 |
| H7/3 | n9_q_in2 | 0.64 | 8.1 | 102.3 | 0.47 | 0.50 | -94.2 [-335.4, 147.0] | -0.0 | -0.8 | 3 | -447.2 | -662.2 |
| H7/3 | n9_wk_my_ext_in | 0.62 | 27.3 | 67.3 | 0.48 | 0.48 | -40.0 [-279.4, 199.4] | -0.0 | -0.3 | 3 | -419.0 | 34.6 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | n9_wk_pos_top20 | 0.33 | 193.6 | 26.1 | 0.48 | 0.42 | 167.5 [51.2, 283.9] | 20.9 | 2.8 | 3 | 123.5 | 474.2 |
| K7/0 | n9_amd_dist_with | 0.40 | 179.2 | 31.7 | 0.47 | 0.43 | 147.6 [13.1, 282.0] | 14.2 | 2.2 | 3 | 185.2 | 193.0 |
| K7/0 | n9_mon_ext_against1 | 0.05 | -174.0 | 87.7 | 0.31 | 0.45 | -261.7 [-500.7, -22.8] | -8.5 | -2.1 | 4 | -183.7 | -185.2 |
| K7/0 | n9_wk_pos_mid | 0.17 | -33.5 | 105.2 | 0.41 | 0.45 | -138.7 [-274.7, -2.8] | -13.1 | -2.0 | 3 | -270.9 | -187.8 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | n9_wk_opp_ext_in_odds50 | 0.32 | 133.2 | -10.4 | 0.47 | 0.41 | 143.6 [18.9, 268.3] | 0.0 | 2.3 | 4 | 82.3 | 99.3 |
| K7/1 | n9_q1_consol | 0.32 | 125.6 | -18.1 | 0.47 | 0.41 | 143.7 [0.1, 287.2] | 0.0 | 2.0 | 3 | 304.9 | 285.3 |
| K7/1 | n9_amd_sweep_then_dist_with | 0.10 | 203.4 | 6.3 | 0.49 | 0.42 | 197.1 [-79.8, 474.1] | 0.0 | 1.4 | 3 | 467.8 | 689.3 |
| K7/1 | n9_wk_my_ext_in | 0.62 | 66.2 | -15.2 | 0.44 | 0.41 | 81.4 [-39.3, 202.1] | 0.0 | 1.3 | 3 | 150.9 | 82.3 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | n9_wk_used_gt100 | 0.19 | -91.2 | 33.6 | 0.37 | 0.44 | -124.8 [-250.7, 1.1] | -0.0 | -1.9 | 3 | -294.3 | -310.7 |
| K7/3 | n9_ysame_inside | 0.37 | -51.8 | 48.5 | 0.40 | 0.45 | -100.2 [-214.5, 14.1] | -0.0 | -1.7 | 3 | -35.8 | 211.5 |
| K7/3 | n9_wk_used_lt50 | 0.36 | 67.8 | -22.1 | 0.45 | 0.41 | 89.9 [-14.5, 194.3] | 0.0 | 1.7 | 4 | 325.9 | 380.5 |
| K7/3 | n9_wk_opp_ext_in_odds50 | 0.35 | -37.9 | 36.4 | 0.40 | 0.44 | -74.3 [-178.9, 30.3] | -0.0 | -1.4 | 4 | -11.7 | 103.5 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | n9_wk_pos_top20 | 0.34 | 197.3 | -8.6 | 0.51 | 0.43 | 205.9 [49.9, 361.9] | 0.0 | 2.6 | 4 | 299.0 | 771.6 |
| K7/4 | n9_wk_pos_mid | 0.18 | -119.2 | 101.1 | 0.37 | 0.48 | -220.3 [-393.6, -47.0] | -0.0 | -2.5 | 4 | -231.7 | -223.5 |
| K7/4 | n9_asia_ext1_with | 0.30 | 188.2 | 7.3 | 0.50 | 0.44 | 180.9 [18.8, 343.0] | 0.0 | 2.2 | 4 | 425.7 | 791.5 |
| K7/4 | n9_mon_inside | 0.36 | -49.5 | 112.3 | 0.41 | 0.48 | -161.9 [-320.6, -3.1] | -0.0 | -2.0 | 4 | -99.5 | -532.3 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | n9_q1_consol | 0.30 | 90.1 | -105.9 | 0.44 | 0.37 | 196.0 [32.4, 359.6] | 0.0 | 2.3 | 4 | 326.6 | 375.7 |
| M7/1 | n9_q_in3 | 0.16 | -151.8 | 24.4 | 0.35 | 0.42 | -176.2 [-324.9, -27.5] | -0.0 | -2.3 | 4 | -238.3 | 14.0 |
| M7/1 | n9_q1_range_gt_avg | 0.37 | -162.4 | 22.2 | 0.35 | 0.41 | -184.6 [-343.3, -26.0] | -0.0 | -2.3 | 4 | -159.5 | -36.0 |
| M7/1 | n9_mon_inside | 0.48 | 30.1 | -72.0 | 0.41 | 0.39 | 102.1 [-15.0, 219.1] | 0.0 | 1.7 | 4 | 78.2 | 57.4 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | n9_ysame_break_against | 0.13 | 188.6 | 44.5 | 0.50 | 0.44 | 144.1 [-27.2, 315.4] | 0.0 | 1.6 | 3 | 203.5 | -83.3 |
| M7/3 | n9_mon_ext_with1 | 0.15 | 159.6 | 45.7 | 0.50 | 0.44 | 113.9 [-46.3, 274.2] | 0.0 | 1.4 | 3 | 52.9 | 19.7 |
| M7/3 | n9_q1_consol | 0.44 | 73.5 | 14.0 | 0.46 | 0.42 | 59.5 [-44.8, 163.9] | 0.0 | 1.1 | 3 | 48.1 | 262.5 |
| M7/3 | n9_ysame_inside | 0.35 | 20.6 | 85.4 | 0.43 | 0.46 | -64.8 [-185.6, 56.0] | -0.0 | -1.1 | 4 | -66.4 | 103.0 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | n9_psess_ext05_with | 0.41 | 260.8 | 117.9 | 0.41 | 0.35 | 142.8 [-74.6, 360.2] | 0.0 | 1.3 | 3 | 139.8 | 340.1 |
| O7/3 | n9_wk_my_ext_in | 0.56 | 226.6 | 112.4 | 0.39 | 0.35 | 114.2 [-98.4, 326.8] | 0.0 | 1.1 | 3 | 418.6 | 635.3 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | n9_mo_pos_top20 | 0.29 | 975.4 | 245.8 | 0.49 | 0.42 | 729.6 [270.1, 1189.0] | 323.3 | 3.1 | 4 | 119.0 | 787.4 |
| P7/0 | n9_mon_ext_against1 | 0.04 | -934.1 | 395.9 | 0.29 | 0.44 | -1330.0 [-2307.3, -352.7] | -199.0 | -2.7 | 4 | -572.5 | -107.8 |
| P7/0 | n9_wk_pos_top20 | 0.38 | 703.2 | 175.8 | 0.46 | 0.41 | 527.5 [95.2, 959.7] | 249.7 | 2.4 | 4 | 283.5 | 898.9 |
| P7/0 | n9_mon_ext_against0 | 0.18 | -160.1 | 453.6 | 0.37 | 0.44 | -613.8 [-1156.2, -71.4] | -223.1 | -2.2 | 3 | -734.9 | -822.8 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | n9_q4_live_fade_with | 0.30 | -481.0 | 274.4 | 0.27 | 0.44 | -755.4 [-1300.9, -209.8] | -0.0 | -2.7 | 3 | -977.6 | -2017.6 |
| P7/1 | n9_q3_complete_with | 0.69 | 250.1 | -371.0 | 0.43 | 0.30 | 621.2 [97.6, 1144.7] | 0.0 | 2.3 | 3 | 1025.0 | 2017.6 |
| P7/1 | n9_q1_consol | 0.32 | 225.8 | -103.6 | 0.42 | 0.35 | 329.4 [50.2, 608.5] | 0.0 | 2.3 | 4 | 492.0 | 592.0 |
| P7/1 | n9_wk_opp_ext_in_odds50 | 0.31 | 222.0 | -50.0 | 0.43 | 0.36 | 272.0 [22.7, 521.2] | 0.0 | 2.1 | 3 | 199.8 | 400.6 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | n9_q_cur_move_with | 0.86 | 37.5 | -331.8 | 0.40 | 0.35 | 369.3 [30.2, 708.4] | 125.5 | 2.1 | 4 | 140.5 | -1280.1 |
| P7/3 | n9_psess_ext1_with | 0.38 | 152.4 | -149.9 | 0.42 | 0.37 | 302.3 [17.5, 587.2] | 127.5 | 2.1 | 3 | 749.2 | 481.6 |
| P7/3 | n9_ysame_break_with | 0.47 | 156.4 | -144.4 | 0.42 | 0.37 | 300.8 [3.7, 597.9] | 120.7 | 2.0 | 3 | 595.6 | 557.0 |
| P7/3 | n9_ysame_inside | 0.36 | -192.6 | 104.0 | 0.36 | 0.41 | -296.6 [-591.1, -2.1] | -120.3 | -2.0 | 3 | -62.2 | 151.6 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | n9_psess_inside | 0.57 | 653.9 | -77.2 | 0.55 | 0.48 | 731.1 [127.0, 1335.2] | 0.0 | 2.4 | 4 | 1229.2 | 2313.7 |
| U7/0 | n9_psess_break_with | 0.35 | -129.9 | 595.9 | 0.46 | 0.55 | -725.9 [-1350.1, -101.6] | -0.0 | -2.3 | 4 | -905.1 | -1944.6 |
| U7/0 | n9_mon_inside | 0.57 | 613.2 | 29.9 | 0.56 | 0.48 | 583.3 [-10.7, 1177.3] | 0.0 | 1.9 | 3 | 1220.6 | 1425.5 |
| U7/0 | n9_mon_ext_against0 | 0.25 | -92.6 | 508.7 | 0.46 | 0.55 | -601.3 [-1284.1, 81.5] | -0.0 | -1.7 | 3 | -1602.1 | -1455.0 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | n9_wk_used_gt100 | 0.18 | 805.4 | -14.8 | 0.60 | 0.48 | 820.2 [220.2, 1420.3] | 281.4 | 2.7 | 3 | 492.6 | 760.7 |
| U7/1 | n9_mo_pos_bottom20 | 0.28 | -361.0 | 251.4 | 0.42 | 0.52 | -612.4 [-1149.5, -75.3] | -241.6 | -2.2 | 3 | -592.3 | -936.2 |
| U7/1 | n9_psess_inside | 0.82 | 250.4 | -319.8 | 0.52 | 0.45 | 570.1 [-91.7, 1232.0] | 171.3 | 1.7 | 4 | 528.3 | 2488.6 |
| U7/1 | n9_asia_inside | 0.82 | 250.4 | -319.8 | 0.52 | 0.45 | 570.1 [-91.7, 1232.0] | 171.3 | 1.7 | 4 | 528.3 | 2488.6 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B9_structure.parquet

### B9 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 69 conditions; 2893 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 53 conditions with |t|>2 (chance alone: about 3). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n9_wk_pos_top20 | 0.41 | 3.3 | -0.1 | 0.52 | 0.49 | 3.3 [2.9, 3.8] | 3.3 | 14.1 | 4 | 2.6 | 6.9 |
| ALL/ALL | n9_mon_ext_against0 | 0.20 | -1.4 | 1.9 | 0.47 | 0.51 | -3.2 [-3.8, -2.6] | -3.1 | -9.9 | 4 | -3.4 | -4.2 |
| ALL/ALL | n9_psess_ext1_with | 0.08 | 5.4 | 0.7 | 0.53 | 0.50 | 4.7 [3.8, 5.7] | 4.5 | 9.7 | 4 | 2.3 | 4.3 |
| ALL/ALL | n9_ysame_ext1_with | 0.28 | 3.3 | 0.4 | 0.52 | 0.49 | 2.8 [2.3, 3.4] | 2.8 | 9.6 | 3 | 6.0 | 7.1 |
| ALL/ALL | n9_mon_ext_against1 | 0.05 | -3.9 | 1.5 | 0.45 | 0.50 | -5.4 [-6.5, -4.3] | -5.1 | -9.6 | 4 | -6.6 | -6.4 |
| ALL/ALL | n9_amd_dist_with | 0.59 | 2.8 | 0.2 | 0.52 | 0.49 | 2.6 [2.1, 3.2] | 2.6 | 9.3 | 4 | 6.3 | 9.6 |
| ALL/ALL | n9_amd_acc | 0.38 | -0.1 | 2.1 | 0.49 | 0.51 | -2.2 [-2.7, -1.7] | -2.2 | -9.3 | 3 | -0.4 | -3.6 |
| ALL/ALL | n9_fhour_ext1_with | 0.17 | 4.4 | 1.1 | 0.53 | 0.50 | 3.3 [2.6, 4.0] | 3.2 | 9.0 | 4 | 6.8 | 5.9 |
| ALL/ALL | n9_mon_ext_with1 | 0.11 | 4.5 | 0.8 | 0.53 | 0.50 | 3.7 [2.9, 4.5] | 3.6 | 8.9 | 4 | 8.1 | 3.0 |
| ALL/ALL | n9_wk_pos_bottom20 | 0.11 | -1.6 | 1.7 | 0.47 | 0.51 | -3.2 [-4.0, -2.5] | -3.1 | -8.9 | 4 | -3.5 | -2.2 |
| ALL/ALL | n9_asia_ext1_with | 0.19 | 3.5 | 0.1 | 0.52 | 0.49 | 3.3 [2.6, 4.1] | 3.2 | 8.8 | 4 | 7.9 | 7.6 |
| ALL/ALL | n9_ysame_ext05_with | 0.38 | 2.7 | 0.3 | 0.52 | 0.49 | 2.4 [1.8, 2.9] | 2.3 | 8.6 | 3 | 3.1 | 4.1 |
| ALL/ALL | n9_mo_pos_top20 | 0.33 | 2.7 | 0.6 | 0.52 | 0.49 | 2.1 [1.6, 2.6] | 2.1 | 8.4 | 4 | 1.9 | 0.1 |
| ALL/ALL | n9_mon_ext_with0 | 0.36 | 2.6 | 0.4 | 0.52 | 0.49 | 2.2 [1.7, 2.8] | 2.2 | 8.3 | 4 | 2.1 | 1.7 |
| ALL/ALL | n9_amd_dist_against | 0.04 | -3.9 | 2.0 | 0.45 | 0.51 | -5.9 [-7.3, -4.4] | -5.2 | -7.9 | 4 | -9.3 | -15.4 |
| ALL/ALL | n9_ysame_break_with | 0.50 | 2.2 | 0.3 | 0.51 | 0.49 | 2.0 [1.4, 2.5] | 1.9 | 7.4 | 4 | 2.4 | 2.6 |
| ALL/ALL | n9_asia_ext05_with | 0.29 | 2.3 | 0.1 | 0.51 | 0.49 | 2.2 [1.6, 2.9] | 2.2 | 6.7 | 4 | 4.2 | 5.9 |
| ALL/ALL | n9_psess_ext05_with | 0.16 | 3.0 | 0.7 | 0.51 | 0.50 | 2.3 [1.6, 3.0] | 2.2 | 6.5 | 4 | 1.6 | 0.4 |
| ALL/ALL | n9_q_in4 | 0.25 | 2.6 | 0.9 | 0.51 | 0.50 | 1.7 [1.2, 2.2] | 1.7 | 6.3 | 4 | 2.4 | 4.3 |
| ALL/ALL | n9_ysame_break_against | 0.27 | -0.1 | 1.7 | 0.49 | 0.51 | -1.8 [-2.4, -1.2] | -1.8 | -6.1 | 3 | -2.8 | 0.3 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n9_wk_pos_top20 | 0.39 | 5.6 | 0.6 | 0.55 | 0.49 | 5.0 [4.3, 5.7] | 4.9 | 13.5 | 4 | 1.2 | 7.7 |
| ALL/0 | n9_mon_ext_against1 | 0.04 | -9.0 | 2.7 | 0.39 | 0.52 | -11.6 [-13.4, -9.9] | -10.7 | -11.9 | 4 | -19.9 | -12.1 |
| ALL/0 | n9_wk_pos_bottom20 | 0.12 | -2.9 | 3.3 | 0.46 | 0.52 | -6.2 [-7.2, -5.1] | -6.0 | -11.3 | 4 | -8.9 | -12.3 |
| ALL/0 | n9_amd_dist_with | 0.51 | 4.7 | 1.0 | 0.54 | 0.49 | 3.7 [2.9, 4.5] | 3.7 | 8.8 | 4 | 8.5 | 10.3 |
| ALL/0 | n9_mon_ext_against0 | 0.18 | -1.6 | 3.0 | 0.47 | 0.52 | -4.6 [-5.5, -3.6] | -4.4 | -8.8 | 4 | -9.5 | -10.0 |
| ALL/0 | n9_amd_acc | 0.37 | 0.7 | 3.6 | 0.49 | 0.53 | -2.9 [-3.6, -2.2] | -2.9 | -7.9 | 4 | -7.9 | -10.1 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n9_mo_pos_bottom20 | 0.21 | -2.8 | 2.1 | 0.45 | 0.51 | -4.9 [-6.0, -3.9] | -4.8 | -8.9 | 4 | -3.9 | -5.6 |
| ALL/1 | n9_fhour_ext1_with | 0.25 | 4.2 | 0.2 | 0.53 | 0.49 | 4.0 [2.9, 5.1] | 3.9 | 6.8 | 4 | 5.9 | 1.8 |
| ALL/1 | n9_psess_ext05_with | 0.11 | 5.5 | 0.7 | 0.54 | 0.50 | 4.9 [3.5, 6.3] | 4.6 | 6.5 | 4 | 6.5 | 5.2 |
| ALL/1 | n9_asia_ext05_with | 0.11 | 5.5 | 0.7 | 0.54 | 0.50 | 4.8 [3.4, 6.2] | 4.6 | 6.5 | 4 | 6.4 | 5.2 |
| ALL/1 | n9_q_in2 | 0.23 | -0.3 | 1.7 | 0.48 | 0.50 | -2.1 [-3.0, -1.1] | -2.0 | -4.2 | 4 | -1.2 | -2.3 |
| ALL/1 | n9_wk_pos_bottom20 | 0.13 | -0.5 | 1.5 | 0.48 | 0.50 | -2.0 [-3.3, -0.8] | -2.0 | -3.1 | 4 | -2.0 | 5.1 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | n9_psess_break_with | 0.35 | -6.6 | 1.7 | 0.44 | 0.51 | -8.3 [-11.0, -5.6] | -7.7 | -5.5 | 4 | -11.8 | -16.8 |
| ALL/2 | n9_psess_inside | 0.65 | 1.6 | -6.5 | 0.51 | 0.44 | 8.1 [5.3, 10.8] | 7.5 | 5.4 | 4 | 11.6 | 16.2 |
| ALL/2 | n9_mo_pos_top20 | 0.31 | -4.3 | 1.0 | 0.46 | 0.51 | -5.4 [-8.0, -2.7] | -5.0 | -3.7 | 4 | -2.0 | -15.7 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n9_psess_ext1_with | 0.38 | 4.8 | -0.2 | 0.52 | 0.48 | 5.0 [3.5, 6.5] | 4.8 | 6.2 | 4 | 5.7 | 13.1 |
| ALL/3 | n9_mo_pos_top20 | 0.37 | 4.0 | 0.4 | 0.52 | 0.48 | 3.6 [2.1, 5.1] | 3.4 | 4.5 | 4 | 10.2 | 14.1 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n9_asia_ext1_with | 0.36 | 4.9 | -3.2 | 0.54 | 0.47 | 8.0 [6.6, 9.4] | 7.8 | 11.0 | 4 | 16.6 | 17.4 |
| ALL/4 | n9_wk_pos_top20 | 0.49 | 3.3 | -3.6 | 0.52 | 0.46 | 6.9 [5.5, 8.2] | 6.7 | 9.8 | 4 | 15.8 | 30.8 |
| ALL/4 | n9_ysame_ext1_with | 0.33 | 4.4 | -2.4 | 0.53 | 0.47 | 6.9 [5.2, 8.5] | 6.6 | 7.9 | 4 | 18.8 | 15.4 |
| ALL/4 | n9_asia_ext05_with | 0.49 | 2.3 | -2.8 | 0.52 | 0.47 | 5.1 [3.8, 6.4] | 5.0 | 7.2 | 4 | 13.2 | 23.7 |
| ALL/4 | n9_ysame_inside | 0.24 | -5.5 | 1.5 | 0.44 | 0.51 | -7.0 [-8.8, -5.2] | -6.7 | -7.2 | 4 | -15.6 | -10.6 |
| ALL/4 | n9_ysame_ext05_with | 0.45 | 3.0 | -2.8 | 0.52 | 0.47 | 5.8 [4.3, 7.4] | 5.6 | 7.1 | 4 | 19.3 | 25.4 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | n9_ysame_inside | 0.18 | -6.0 | 0.4 | 0.44 | 0.50 | -6.3 [-8.9, -3.8] | -5.9 | -4.6 | 4 | -6.0 | -18.0 |
| ALL/5 | n9_wk_used_gt100 | 0.26 | -2.7 | 0.7 | 0.46 | 0.50 | -3.4 [-5.4, -1.4] | -3.3 | -3.2 | 4 | -11.2 | -18.8 |
| ALL/5 | n9_wk_new_ext_with | 0.05 | -5.2 | 0.1 | 0.44 | 0.50 | -5.3 [-8.9, -1.7] | -4.6 | -2.5 | 4 | -15.9 | -27.4 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B9_structure.parquet

## ADDENDUM 6 BLOCK 16: flow calendar (roll, opex, VIX expiry, month / quarter end, index events, holidays, FOMC, tax weeks)

### B16 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 47 conditions; 962 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 7 conditions with |t|>2 (chance alone: about 2). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n16_day_after_quad | 0.01 | 532.1 | 99.4 | 0.52 | 0.44 | 432.6 [169.2, 696.1] | 94.2 | 3.2 | 4 | 767.3 | 1638.2 |
| ALL/ALL | n16_quad_witch | 0.02 | 400.9 | 100.7 | 0.49 | 0.44 | 300.2 [44.5, 555.9] | 68.4 | 2.3 | 4 | 727.7 | 518.1 |
| ALL/ALL | n16_sp_rebal_day | 0.02 | 400.9 | 100.7 | 0.49 | 0.44 | 300.2 [44.5, 555.9] | 68.4 | 2.3 | 4 | 727.7 | 518.1 |
| ALL/ALL | n16_week_before_fomc | 0.16 | 37.9 | 118.6 | 0.42 | 0.44 | -80.7 [-162.4, 1.0] | -60.0 | -1.9 | 3 | -96.1 | -116.3 |
| ALL/ALL | n16_estimated_tax_week | 0.08 | 202.1 | 97.2 | 0.46 | 0.44 | 104.9 [-13.9, 223.8] | 60.6 | 1.7 | 3 | 161.4 | 287.7 |
| ALL/ALL | n16_flow_heavy_day | 0.12 | 178.2 | 96.2 | 0.45 | 0.44 | 82.0 [-14.5, 178.6] | 55.3 | 1.7 | 3 | 19.1 | -211.7 |
| ALL/ALL | n16_russell_recon_day | 0.01 | 389.3 | 104.0 | 0.50 | 0.44 | 285.3 [-71.0, 641.7] | 37.7 | 1.6 | 3 | 347.0 | nan |
| ALL/ALL | n16_opex_week | 0.23 | 146.2 | 93.2 | 0.44 | 0.44 | 53.1 [-20.1, 126.2] | 41.5 | 1.4 | 3 | 112.5 | 175.8 |
| ALL/ALL | n16_quad_week | 0.08 | 167.7 | 100.4 | 0.44 | 0.44 | 67.3 [-48.1, 182.7] | 39.8 | 1.1 | 3 | 161.4 | 287.7 |
| ALL/ALL | n16_expiry_week_quarterly | 0.08 | 167.7 | 100.4 | 0.44 | 0.44 | 67.3 [-48.1, 182.7] | 39.8 | 1.1 | 3 | 161.4 | 287.7 |
| ALL/ALL | n16_fomc_day | 0.03 | 21.7 | 108.3 | 0.41 | 0.44 | -86.6 [-262.0, 88.8] | -33.4 | -1.0 | 3 | -85.0 | -546.9 |
| ALL/ALL | n16_vix_expiry_week | 0.23 | 79.3 | 113.3 | 0.43 | 0.44 | -34.0 [-108.3, 40.4] | -26.4 | -0.9 | 3 | -35.8 | 153.4 |
| ALL/ALL | n16_half_day | 0.02 | 218.5 | 103.2 | 0.44 | 0.44 | 115.3 [-137.9, 368.6] | 26.7 | 0.9 | 3 | 225.5 | -448.2 |
| ALL/ALL | n16_vix_expiry_day | 0.04 | 60.2 | 107.7 | 0.42 | 0.44 | -47.5 [-195.4, 100.4] | -22.3 | -0.6 | 3 | -225.8 | -295.0 |
| ALL/ALL | n16_first_td_month | 0.05 | 142.4 | 103.7 | 0.45 | 0.44 | 38.7 [-104.1, 181.4] | 18.8 | 0.5 | 3 | 161.2 | 158.7 |
| ALL/ALL | n16_collar_reset_pm1 | 0.03 | 135.5 | 104.7 | 0.42 | 0.44 | 30.8 [-135.6, 197.2] | 12.7 | 0.4 | 3 | 33.2 | -9.6 |
| ALL/ALL | n16_quarter_end_week | 0.07 | 118.9 | 104.5 | 0.43 | 0.44 | 14.4 [-101.2, 129.9] | 8.5 | 0.2 | 3 | 81.7 | 124.7 |
| ALL/ALL | n16_roll_week | 0.08 | 96.4 | 106.4 | 0.44 | 0.44 | -10.0 [-118.7, 98.7] | -6.2 | -0.2 | 3 | -59.8 | -178.7 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n16_estimated_tax_week | 0.07 | 548.5 | 207.0 | 0.51 | 0.46 | 341.5 [61.4, 621.6] | 23.2 | 0.2 | 4 | 208.8 | 125.7 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n16_fomc_day | 0.03 | -324.2 | 40.2 | 0.30 | 0.42 | -364.4 [-626.9, -101.9] | -219.9 | -1.6 | 4 | -229.5 | -969.2 |
| ALL/1 | n16_week_before_fomc | 0.16 | -59.9 | 47.4 | 0.39 | 0.42 | -107.4 [-227.4, 12.7] | -94.4 | -1.5 | 4 | -210.9 | -313.2 |
| ALL/1 | n16_day_after_opex | 0.05 | -197.6 | 41.0 | 0.36 | 0.42 | -238.7 [-458.1, -19.2] | -163.6 | -1.5 | 4 | -445.8 | -510.3 |
| ALL/1 | n16_first_td_month | 0.05 | 206.2 | 21.0 | 0.42 | 0.41 | 185.1 [-20.8, 391.1] | 131.8 | 1.3 | 4 | 454.0 | 499.6 |
| ALL/1 | n16_vix_expiry_day | 0.04 | -52.3 | 33.6 | 0.41 | 0.42 | -85.9 [-305.8, 134.0] | -58.8 | -0.5 | 4 | -250.6 | -553.8 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n16_day_after_vix_expiry | 0.05 | -172.6 | 36.3 | 0.34 | 0.42 | -208.9 [-379.4, -38.4] | -106.5 | -1.2 | 4 | -416.6 | -426.9 |
| ALL/3 | n16_roll_week | 0.08 | 154.1 | 15.5 | 0.47 | 0.42 | 138.6 [-1.2, 278.5] | 84.2 | 1.2 | 4 | 145.6 | -538.8 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | n16_estimated_tax_week | 0.07 | 372.9 | 93.5 | 0.65 | 0.51 | 279.4 [32.9, 525.9] | 0.0 | 2.2 | 4 | 267.4 | 263.5 |
| A7/0 | n16_last5_td_month | 0.26 | 37.4 | 140.3 | 0.49 | 0.53 | -102.9 [-255.1, 49.3] | -0.0 | -1.3 | 3 | -35.1 | 77.3 |
| A7/0 | n16_flow_heavy_day | 0.13 | 205.8 | 100.9 | 0.57 | 0.51 | 105.0 [-92.5, 302.4] | 0.0 | 1.0 | 3 | 12.3 | -8.6 |
| A7/0 | n16_vix_expiry_day | 0.04 | -37.3 | 120.9 | 0.44 | 0.52 | -158.2 [-477.5, 161.1] | -0.0 | -1.0 | 3 | -101.4 | -630.6 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | n16_fomc_week | 0.19 | 855.9 | 69.8 | 0.55 | 0.46 | 786.1 [323.4, 1248.8] | 420.6 | 3.3 | 4 | 541.4 | 255.6 |
| H7/0 | n16_week_before_fomc | 0.17 | -203.6 | 299.9 | 0.39 | 0.50 | -503.6 [-981.5, -25.7] | -261.3 | -2.1 | 4 | -275.6 | 9.3 |
| H7/0 | n16_opex_week | 0.22 | 518.3 | 132.6 | 0.52 | 0.47 | 385.7 [-50.8, 822.2] | 217.5 | 1.7 | 4 | 103.7 | -331.5 |
| H7/0 | n16_flow_heavy_day | 0.09 | 665.4 | 170.5 | 0.59 | 0.47 | 494.8 [-152.7, 1142.3] | 183.2 | 1.5 | 3 | 440.1 | 117.3 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | n16_roll_day_pm1 | 0.05 | -168.4 | 102.1 | 0.35 | 0.45 | -270.5 [-484.8, -56.1] | -0.0 | -2.5 | 3 | -351.9 | 67.2 |
| K7/0 | n16_last3_td_month | 0.14 | 204.4 | 70.4 | 0.48 | 0.44 | 133.9 [-16.6, 284.5] | 0.0 | 1.7 | 3 | 55.3 | -1.1 |
| K7/0 | n16_quarter_end_week | 0.08 | 220.3 | 78.0 | 0.47 | 0.44 | 142.2 [-51.9, 336.4] | 0.0 | 1.4 | 4 | 129.7 | 186.7 |
| K7/0 | n16_week_before_fomc | 0.16 | 7.4 | 103.9 | 0.42 | 0.45 | -96.5 [-230.9, 37.9] | -0.0 | -1.4 | 3 | -76.1 | 157.8 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | n16_fomc_day | 0.03 | -251.7 | 43.3 | 0.30 | 0.43 | -295.0 [-659.9, 69.9] | -0.0 | -1.6 | 3 | -243.7 | -1016.7 |
| K7/1 | n16_estimated_tax_week | 0.07 | -87.3 | 44.7 | 0.40 | 0.43 | -131.9 [-372.2, 108.4] | -0.0 | -1.1 | 3 | -171.2 | -92.0 |
| K7/1 | n16_day_after_opex | 0.04 | -112.3 | 42.1 | 0.38 | 0.43 | -154.5 [-457.6, 148.7] | -0.0 | -1.0 | 3 | -268.8 | -479.3 |
| K7/1 | n16_day_after_vix_expiry | 0.05 | 140.0 | 30.1 | 0.47 | 0.42 | 109.9 [-146.2, 366.0] | 0.0 | 0.8 | 3 | 329.8 | 23.8 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | n16_last5_td_month | 0.23 | -57.6 | 29.6 | 0.39 | 0.44 | -87.2 [-205.1, 30.7] | -0.0 | -1.4 | 4 | -50.1 | -61.2 |
| K7/3 | n16_flow_heavy_day | 0.11 | -73.4 | 19.7 | 0.39 | 0.43 | -93.2 [-251.6, 65.3] | -0.0 | -1.2 | 3 | -176.5 | -425.0 |
| K7/3 | n16_fomc_week | 0.15 | -56.1 | 21.0 | 0.39 | 0.43 | -77.1 [-216.6, 62.4] | -0.0 | -1.1 | 3 | -308.7 | -460.0 |
| K7/3 | n16_vix_expiry_week | 0.22 | -39.8 | 23.2 | 0.40 | 0.43 | -63.0 [-183.8, 57.8] | -0.0 | -1.0 | 3 | -263.6 | -381.6 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | n16_week_after_fomc | 0.12 | 198.8 | 42.5 | 0.53 | 0.45 | 156.3 [-54.2, 366.8] | 59.9 | 1.5 | 3 | 71.7 | 287.0 |
| K7/4 | n16_last5_td_month | 0.24 | -24.1 | 88.4 | 0.41 | 0.47 | -112.5 [-276.0, 51.0] | -57.1 | -1.3 | 3 | -779.5 | -1102.1 |
| K7/4 | n16_last3_td_month | 0.15 | 41.9 | 65.4 | 0.44 | 0.46 | -23.5 [-219.2, 172.2] | -9.8 | -0.2 | 3 | -397.2 | -615.5 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | n16_expiry_week_quarterly | 0.08 | 120.0 | -13.9 | 0.45 | 0.40 | 133.9 [-60.1, 327.9] | 24.1 | 1.4 | 4 | 201.0 | 416.2 |
| M7/1 | n16_quad_week | 0.08 | 120.0 | -13.9 | 0.45 | 0.40 | 133.9 [-60.1, 327.9] | 24.1 | 1.4 | 4 | 201.0 | 416.2 |
| M7/1 | n16_last_td_month | 0.04 | -151.2 | 3.7 | 0.33 | 0.41 | -155.0 [-400.2, 90.3] | -18.7 | -1.2 | 3 | -28.6 | 44.7 |
| M7/1 | n16_fomc_week | 0.16 | 73.1 | -17.4 | 0.43 | 0.40 | 90.4 [-55.3, 236.2] | 25.3 | 1.2 | 4 | 130.6 | 303.1 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | n16_vix_expiry_week | 0.23 | -82.1 | 75.5 | 0.38 | 0.45 | -157.5 [-277.7, -37.4] | -0.0 | -2.6 | 4 | -231.1 | -96.4 |
| M7/3 | n16_fomc_week | 0.15 | 58.6 | 35.8 | 0.44 | 0.44 | 22.7 [-121.8, 167.2] | 0.0 | 0.3 | 3 | 61.3 | 555.3 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | n16_flow_heavy_day | 0.11 | 896.4 | 362.6 | 0.48 | 0.43 | 533.8 [-76.0, 1143.7] | 0.0 | 1.7 | 3 | 473.0 | -1069.0 |
| P7/0 | n16_estimated_tax_week | 0.07 | 1061.5 | 372.1 | 0.48 | 0.44 | 689.4 [-111.5, 1490.3] | 0.0 | 1.7 | 4 | 301.2 | 365.4 |
| P7/0 | n16_first3_td_month | 0.14 | 175.4 | 463.3 | 0.44 | 0.44 | -287.9 [-847.0, 271.3] | -0.0 | -1.0 | 3 | -888.7 | -1494.4 |
| P7/0 | n16_quarter_end_week | 0.08 | 603.5 | 409.2 | 0.45 | 0.44 | 194.3 [-521.5, 910.0] | 0.0 | 0.5 | 3 | 220.7 | 722.2 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | n16_day_after_vix_expiry | 0.04 | 489.3 | 14.3 | 0.51 | 0.38 | 475.0 [-130.7, 1080.7] | 0.0 | 1.5 | 3 | 769.4 | 447.2 |
| P7/1 | n16_week_before_fomc | 0.16 | -166.3 | 72.5 | 0.35 | 0.39 | -238.7 [-543.3, 65.9] | -0.0 | -1.5 | 3 | -211.4 | -393.9 |
| P7/1 | n16_quad_week | 0.07 | 268.2 | 15.5 | 0.40 | 0.38 | 252.8 [-202.0, 707.5] | 0.0 | 1.1 | 3 | 236.9 | 498.3 |
| P7/1 | n16_expiry_week_quarterly | 0.07 | 268.2 | 15.5 | 0.40 | 0.38 | 252.8 [-202.0, 707.5] | 0.0 | 1.1 | 3 | 236.9 | 498.3 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | n16_vix_expiry_week | 0.23 | -247.8 | 29.5 | 0.31 | 0.41 | -277.3 [-574.1, 19.4] | -161.1 | -1.8 | 3 | -279.7 | -16.7 |
| P7/3 | n16_week_after_fomc | 0.14 | 113.3 | -58.3 | 0.42 | 0.38 | 171.5 [-218.1, 561.2] | 76.4 | 0.9 | 3 | 810.9 | 1285.3 |
| P7/3 | n16_fomc_week | 0.15 | 70.8 | -53.6 | 0.39 | 0.39 | 124.4 [-234.1, 482.8] | 60.6 | 0.7 | 3 | 838.9 | 1580.2 |
| P7/3 | n16_last5_td_month | 0.24 | -72.3 | -23.0 | 0.40 | 0.38 | -49.3 [-332.0, 233.4] | -29.8 | -0.3 | 3 | -274.9 | -532.0 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | n16_last3_td_month | 0.14 | -204.3 | 188.8 | 0.44 | 0.51 | -393.1 [-1096.6, 310.3] | -227.9 | -1.1 | 3 | -793.1 | -784.9 |
| U7/1 | n16_opex_week | 0.25 | 364.4 | 55.4 | 0.52 | 0.50 | 308.9 [-244.9, 862.8] | 213.1 | 1.1 | 3 | 163.1 | -105.7 |
| U7/1 | n16_last5_td_month | 0.23 | -106.2 | 204.9 | 0.46 | 0.52 | -311.1 [-884.0, 261.9] | -210.0 | -1.1 | 3 | -826.8 | -777.1 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B16_calendar.parquet

### B16 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 48 conditions; 1999 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 27 conditions with |t|>2 (chance alone: about 2). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n16_fomc_day_before | 0.03 | 5.4 | 1.2 | 0.54 | 0.50 | 4.2 [3.0, 5.5] | 4.0 | 6.6 | 4 | 0.1 | 7.2 |
| ALL/ALL | n16_week_before_fomc | 0.16 | -0.2 | 1.6 | 0.49 | 0.50 | -1.8 [-2.4, -1.2] | -1.8 | -5.7 | 3 | -5.1 | -5.4 |
| ALL/ALL | n16_fomc_week | 0.16 | 2.8 | 1.1 | 0.52 | 0.50 | 1.8 [1.1, 2.4] | 1.7 | 5.6 | 4 | 0.9 | 2.2 |
| ALL/ALL | n16_collar_reset_day | 0.01 | -3.6 | 1.4 | 0.45 | 0.50 | -5.0 [-6.9, -3.2] | -4.5 | -5.3 | 3 | -11.9 | -17.2 |
| ALL/ALL | n16_quarter_end_day | 0.01 | -3.6 | 1.4 | 0.45 | 0.50 | -5.0 [-6.9, -3.2] | -4.5 | -5.3 | 3 | -11.9 | -17.2 |
| ALL/ALL | n16_day_after_quad | 0.02 | 5.7 | 1.3 | 0.53 | 0.50 | 4.4 [2.6, 6.2] | 4.0 | 4.8 | 3 | 13.7 | 35.7 |
| ALL/ALL | n16_first3_td_month | 0.14 | 2.4 | 1.2 | 0.51 | 0.50 | 1.3 [0.6, 1.9] | 1.2 | 3.7 | 3 | 3.6 | 0.3 |
| ALL/ALL | n16_roll_week | 0.08 | 0.1 | 1.4 | 0.49 | 0.50 | -1.4 [-2.2, -0.5] | -1.3 | -3.2 | 3 | -3.9 | -3.6 |
| ALL/ALL | n16_roll_day_pm1 | 0.05 | -0.3 | 1.4 | 0.48 | 0.50 | -1.7 [-2.8, -0.6] | -1.6 | -3.0 | 3 | -3.8 | -3.1 |
| ALL/ALL | n16_russell_recon_day | 0.00 | 6.2 | 1.3 | 0.53 | 0.50 | 4.9 [1.6, 8.1] | 3.6 | 3.0 | 3 | 1.8 | nan |
| ALL/ALL | n16_last_td_month | 0.05 | -0.0 | 1.4 | 0.49 | 0.50 | -1.4 [-2.5, -0.3] | -1.4 | -2.5 | 3 | -4.3 | -0.9 |
| ALL/ALL | n16_vix_expiry_day | 0.05 | 0.2 | 1.4 | 0.49 | 0.50 | -1.2 [-2.3, -0.1] | -1.2 | -2.2 | 3 | -3.7 | -9.5 |
| ALL/ALL | n16_quad_week | 0.08 | 2.2 | 1.3 | 0.51 | 0.50 | 0.9 [0.1, 1.8] | 0.9 | 2.2 | 3 | 3.7 | 6.2 |
| ALL/ALL | n16_expiry_week_quarterly | 0.08 | 2.2 | 1.3 | 0.51 | 0.50 | 0.9 [0.1, 1.8] | 0.9 | 2.2 | 3 | 3.7 | 6.2 |
| ALL/ALL | n16_quad_witch | 0.02 | 2.4 | 1.3 | 0.51 | 0.50 | 1.1 [-0.8, 3.0] | 0.9 | 1.1 | 3 | 3.8 | 14.5 |
| ALL/ALL | n16_sp_rebal_day | 0.02 | 2.4 | 1.3 | 0.51 | 0.50 | 1.1 [-0.8, 3.0] | 0.9 | 1.1 | 3 | 3.8 | 14.5 |
| ALL/ALL | n16_opex_week | 0.23 | 1.5 | 1.3 | 0.50 | 0.50 | 0.2 [-0.4, 0.7] | 0.2 | 0.6 | 3 | 2.2 | 1.9 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n16_roll_day_pm1 | 0.04 | -3.4 | 2.9 | 0.43 | 0.52 | -6.3 [-8.0, -4.6] | -6.0 | -7.1 | 4 | -17.3 | -24.8 |
| ALL/0 | n16_russell_recon_day | 0.01 | 17.2 | 2.6 | 0.68 | 0.51 | 14.6 [10.8, 18.5] | 11.9 | 6.0 | 4 | 20.9 | nan |
| ALL/0 | n16_first3_td_month | 0.14 | 5.0 | 2.2 | 0.54 | 0.51 | 2.8 [1.7, 3.8] | 2.7 | 5.3 | 4 | 0.5 | -6.4 |
| ALL/0 | n16_fomc_day_before | 0.03 | 6.9 | 2.5 | 0.56 | 0.51 | 4.4 [2.5, 6.3] | 4.2 | 4.3 | 4 | 4.2 | 21.9 |
| ALL/0 | n16_day_after_quad | 0.01 | 7.6 | 2.6 | 0.55 | 0.51 | 5.1 [2.1, 8.1] | 4.5 | 2.9 | 4 | 11.6 | 30.4 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n16_fomc_day | 0.03 | -8.3 | 1.5 | 0.41 | 0.50 | -9.8 [-12.2, -7.4] | -9.2 | -7.6 | 4 | -11.4 | -18.8 |
| ALL/1 | n16_week_before_fomc | 0.16 | -1.7 | 1.8 | 0.47 | 0.50 | -3.5 [-4.7, -2.4] | -3.5 | -5.9 | 4 | -7.2 | -4.3 |
| ALL/1 | n16_vix_expiry_day | 0.05 | -4.2 | 1.5 | 0.46 | 0.50 | -5.7 [-7.7, -3.7] | -5.5 | -5.3 | 4 | -10.0 | -22.6 |
| ALL/1 | n16_last_td_month | 0.05 | -3.4 | 1.5 | 0.45 | 0.50 | -4.9 [-6.9, -2.8] | -4.6 | -4.4 | 4 | -7.6 | -0.3 |
| ALL/1 | n16_russell_recon_week | 0.02 | -4.4 | 1.4 | 0.45 | 0.50 | -5.7 [-8.7, -2.8] | -5.2 | -3.4 | 4 | -15.1 | nan |
| ALL/1 | n16_first_td_quarter | 0.02 | -3.6 | 1.3 | 0.45 | 0.50 | -4.9 [-8.4, -1.5] | -4.3 | -2.4 | 4 | -3.5 | -1.6 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | n16_week_after_fomc | 0.16 | 8.0 | -2.3 | 0.57 | 0.48 | 10.3 [7.0, 13.5] | 9.9 | 6.0 | 4 | 35.8 | 38.1 |
| ALL/2 | n16_day_after_vix_expiry | 0.05 | -14.8 | 0.0 | 0.38 | 0.50 | -14.8 [-20.4, -9.2] | -13.2 | -4.6 | 4 | -9.2 | -36.9 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n16_day_after_vix_expiry | 0.04 | -10.6 | 2.1 | 0.40 | 0.50 | -12.7 [-16.1, -9.3] | -12.1 | -7.0 | 4 | -27.2 | -24.4 |
| ALL/3 | n16_vix_expiry_week | 0.23 | -2.2 | 2.6 | 0.47 | 0.50 | -4.7 [-6.4, -3.1] | -4.7 | -5.5 | 4 | -6.4 | 1.6 |
| ALL/3 | n16_week_after_fomc | 0.15 | 5.7 | 0.8 | 0.53 | 0.49 | 5.0 [3.0, 6.9] | 4.9 | 4.9 | 4 | 12.1 | 17.1 |
| ALL/3 | n16_week_before_fomc | 0.16 | -1.4 | 2.1 | 0.47 | 0.50 | -3.5 [-5.4, -1.6] | -3.5 | -3.5 | 4 | -5.9 | -8.1 |
| ALL/3 | n16_fomc_day | 0.03 | -5.9 | 1.8 | 0.43 | 0.50 | -7.7 [-11.8, -3.6] | -7.2 | -3.5 | 4 | -11.4 | -18.7 |
| ALL/3 | n16_fomc_day_before | 0.03 | 7.4 | 1.3 | 0.55 | 0.49 | 6.1 [2.0, 10.2] | 5.7 | 2.7 | 4 | 27.5 | 43.1 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n16_fomc_day_before | 0.03 | 14.8 | -0.8 | 0.60 | 0.49 | 15.7 [12.1, 19.2] | 14.8 | 8.2 | 4 | 2.8 | -6.4 |
| ALL/4 | n16_first_td_quarter | 0.02 | -19.2 | -0.0 | 0.34 | 0.49 | -19.2 [-24.6, -13.8] | -17.1 | -6.2 | 4 | -27.1 | -36.2 |
| ALL/4 | n16_vix_expiry_week | 0.22 | -3.7 | 0.7 | 0.46 | 0.50 | -4.3 [-6.0, -2.7] | -4.3 | -5.2 | 4 | -11.7 | -11.5 |
| ALL/4 | n16_fomc_day | 0.03 | -11.7 | 0.1 | 0.40 | 0.49 | -11.7 [-15.9, -7.5] | -10.9 | -5.1 | 4 | -11.9 | -16.0 |
| ALL/4 | n16_roll_day_pm1 | 0.05 | -6.7 | 0.0 | 0.44 | 0.49 | -6.7 [-9.7, -3.7] | -6.4 | -4.2 | 4 | -14.4 | -31.2 |
| ALL/4 | n16_roll_week | 0.08 | -4.9 | 0.1 | 0.45 | 0.49 | -5.0 [-7.5, -2.5] | -4.9 | -3.9 | 4 | -14.0 | -32.7 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | n16_quarter_end_day | 0.02 | -7.7 | -0.0 | 0.42 | 0.49 | -7.7 [-14.2, -1.2] | -6.0 | -1.8 | 4 | -40.5 | -43.9 |
| ALL/5 | n16_collar_reset_day | 0.02 | -7.7 | -0.0 | 0.42 | 0.49 | -7.7 [-14.2, -1.2] | -6.0 | -1.8 | 4 | -40.5 | -43.9 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B16_calendar.parquet

## ADDENDUM 6 BLOCK 13: microstructure state (arrival intensity, spread / depth vs clock, vol of vol, skew / kurtosis, jumps, VPIN, sweeps, large trades, print size)

### B13 - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 62 conditions; 1414 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 4 conditions with |t|>2 (chance alone: about 3). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n13_sweep_resilient | 0.39 | -8.2 | 129.8 | 0.41 | 0.45 | -138.1 [-256.2, -20.0] | -18.9 | -2.3 | 3 | -275.5 | -139.2 |
| ALL/ALL | n13_kurt15_hi | 0.04 | -59.7 | 112.3 | 0.42 | 0.44 | -172.1 [-320.1, -24.0] | -15.7 | -2.3 | 4 | -449.7 | -445.2 |
| ALL/ALL | n13_skew60_strong_with | 0.26 | 166.6 | 84.9 | 0.44 | 0.44 | 81.7 [7.6, 155.8] | 23.4 | 2.2 | 3 | 77.9 | 87.8 |
| ALL/ALL | n13_vov60_lo | 0.05 | 227.8 | 98.9 | 0.47 | 0.44 | 128.9 [7.9, 250.0] | 16.9 | 2.1 | 4 | 20.2 | -388.6 |
| ALL/ALL | n13_sweep_thin | 0.23 | 179.6 | 45.7 | 0.46 | 0.43 | 133.8 [-11.8, 279.5] | 12.6 | 1.8 | 3 | 358.9 | 404.5 |
| ALL/ALL | n13_jump15_against | 0.01 | 353.2 | 103.2 | 0.50 | 0.44 | 249.9 [-47.6, 547.4] | 6.1 | 1.6 | 3 | 431.1 | 386.5 |
| ALL/ALL | n13_jshare60_hi | 0.04 | 228.2 | 100.5 | 0.47 | 0.44 | 127.7 [-45.3, 300.7] | 8.8 | 1.4 | 3 | 235.6 | 41.3 |
| ALL/ALL | n13_arr10_hi | 0.15 | 140.9 | 86.6 | 0.45 | 0.43 | 54.4 [-31.1, 139.8] | 12.6 | 1.2 | 3 | 125.5 | -28.0 |
| ALL/ALL | n13_vpin_dir_against | 0.10 | 7.7 | 70.1 | 0.42 | 0.43 | -62.4 [-160.8, 36.0] | -11.6 | -1.2 | 3 | -119.4 | -145.3 |
| ALL/ALL | n13_arr10_lo | 0.23 | 130.4 | 84.0 | 0.45 | 0.43 | 46.3 [-37.8, 130.4] | 11.0 | 1.1 | 3 | 115.0 | 7.2 |
| ALL/ALL | n13_skew60_strong_against | 0.10 | 156.9 | 100.4 | 0.45 | 0.44 | 56.4 [-48.2, 161.1] | 9.5 | 1.1 | 3 | 96.8 | 18.7 |
| ALL/ALL | n13_spread_tight | 0.36 | 116.6 | 82.1 | 0.45 | 0.43 | 34.5 [-30.1, 99.0] | 11.9 | 1.0 | 3 | 42.3 | -57.5 |
| ALL/ALL | n13_sweep_thin_with | 0.17 | 142.9 | 62.0 | 0.44 | 0.43 | 81.0 [-78.1, 240.0] | 6.5 | 1.0 | 3 | 209.1 | 500.3 |
| ALL/ALL | n13_arr300_lo | 0.25 | 66.4 | 103.6 | 0.42 | 0.44 | -37.2 [-118.1, 43.6] | -9.4 | -0.9 | 3 | -2.2 | -19.6 |
| ALL/ALL | n13_sweep120_with | 0.11 | 74.5 | 96.9 | 0.43 | 0.44 | -22.5 [-97.0, 52.1] | -6.4 | -0.6 | 3 | -130.2 | -75.5 |
| ALL/ALL | n13_lt25_since_lt10 | 0.02 | 75.5 | 96.1 | 0.44 | 0.43 | -20.6 [-169.4, 128.2] | -1.9 | -0.3 | 3 | -56.7 | 585.5 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n13_jump15_with | 0.11 | 77.9 | 250.7 | 0.46 | 0.47 | -172.8 [-360.5, 14.9] | -0.0 | -0.0 | 4 | -197.6 | 282.2 |
| ALL/0 | n13_jump15_any | 0.12 | 113.3 | 248.1 | 0.46 | 0.47 | -134.8 [-318.5, 48.9] | -0.0 | -0.0 | 4 | -124.7 | 294.4 |
| ALL/0 | n13_kurt15_hi | 0.05 | -99.2 | 248.9 | 0.44 | 0.47 | -348.0 [-615.4, -80.7] | -0.0 | -0.0 | 4 | -897.9 | -779.9 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n13_skew15_strong_against | 0.15 | -73.8 | 48.5 | 0.38 | 0.42 | -122.3 [-243.9, -0.7] | -87.1 | -1.4 | 4 | -140.1 | -272.3 |
| ALL/1 | n13_arr60_vs_300_hi | 0.25 | 85.7 | 11.6 | 0.42 | 0.41 | 74.1 [-24.0, 172.2] | 58.7 | 1.2 | 4 | 2.9 | 150.8 |
| ALL/1 | n13_spread_wide | 0.18 | -43.5 | 46.7 | 0.38 | 0.42 | -90.2 [-203.0, 22.6] | -66.9 | -1.2 | 4 | -95.5 | 70.8 |
| ALL/1 | n13_lt25_since_lt60 | 0.04 | 281.6 | 19.0 | 0.45 | 0.41 | 262.6 [42.2, 482.9] | 112.8 | 1.0 | 4 | 311.5 | 236.8 |
| ALL/1 | n13_lt25_last_with60 | 0.03 | 276.3 | 22.9 | 0.45 | 0.41 | 253.4 [-7.7, 514.6] | 88.5 | 0.7 | 4 | 538.5 | 540.4 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n13_skew60_with | 0.58 | -6.2 | 74.5 | 0.40 | 0.45 | -80.7 [-157.6, -3.8] | -0.0 | -0.0 | 4 | -56.2 | 182.2 |
| ALL/3 | n13_arrival_vs_clock_lo | 0.13 | 166.3 | 7.6 | 0.47 | 0.41 | 158.7 [42.1, 275.3] | 0.0 | 0.0 | 4 | 150.0 | 56.5 |
| ALL/3 | n13_lt25_since_gt300 | 0.39 | -1.7 | 46.1 | 0.41 | 0.43 | -47.8 [-126.2, 30.6] | -0.0 | -0.0 | 4 | -155.7 | -61.3 |
| ALL/3 | n13_lt50_since_gt300 | 0.78 | 40.8 | -3.4 | 0.42 | 0.41 | 44.2 [-44.0, 132.4] | 0.0 | 0.0 | 4 | 78.9 | -25.7 |
| ALL/3 | n13_arr10_hi | 0.06 | 82.1 | 23.7 | 0.42 | 0.42 | 58.4 [-90.9, 207.6] | 0.0 | 0.0 | 4 | 121.6 | 448.1 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n13_jshare15_lo | 0.55 | -0.4 | 137.9 | 0.43 | 0.50 | -138.3 [-281.0, 4.3] | -0.0 | -0.0 | 4 | -164.0 | -355.3 |
| ALL/4 | n13_lt25_since_lt60 | 0.20 | -60.5 | 92.0 | 0.40 | 0.47 | -152.5 [-330.3, 25.3] | -0.0 | -0.0 | 4 | -220.7 | 11.8 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | n13_avgprint60_ge16 | 0.14 | 355.6 | 78.8 | 0.63 | 0.50 | 276.8 [77.4, 476.2] | 35.3 | 2.7 | 3 | 244.5 | -19.4 |
| A7/0 | n13_skew15_strong_with | 0.37 | 215.8 | 57.0 | 0.57 | 0.49 | 158.7 [22.5, 295.0] | 37.9 | 2.3 | 3 | 56.5 | -119.3 |
| A7/0 | n13_skew15_with | 0.66 | 162.2 | 23.2 | 0.55 | 0.48 | 139.0 [1.1, 276.9] | 32.5 | 2.0 | 3 | 133.8 | 128.4 |
| A7/0 | n13_jump15_with | 0.14 | 245.2 | 93.8 | 0.59 | 0.51 | 151.4 [-37.1, 339.8] | 21.3 | 1.6 | 4 | 50.9 | -96.4 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | n13_arr60_lo | 0.38 | -48.3 | 424.5 | 0.46 | 0.50 | -472.8 [-875.6, -70.0] | -68.7 | -2.3 | 4 | -444.5 | 188.4 |
| H7/0 | n13_arr300_lo | 0.24 | -142.3 | 367.0 | 0.44 | 0.50 | -509.3 [-945.0, -73.7] | -64.6 | -2.3 | 4 | -390.8 | 207.6 |
| H7/0 | n13_jshare60_lo | 0.49 | 409.8 | 30.4 | 0.53 | 0.43 | 379.4 [8.3, 750.4] | 63.3 | 2.0 | 4 | 640.7 | 971.3 |
| H7/0 | n13_avgprint60_le115 | 0.17 | -135.1 | 322.6 | 0.43 | 0.50 | -457.7 [-953.7, 38.4] | -46.1 | -1.8 | 4 | -103.3 | -487.0 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | n13_skew60_with | 0.47 | -37.1 | 112.6 | 0.45 | 0.51 | -149.7 [-383.2, 83.8] | -62.7 | -1.3 | 3 | -26.1 | 51.7 |
| H7/3 | n13_jshare15_lo | 0.63 | 77.1 | -17.1 | 0.50 | 0.45 | 94.2 [-148.3, 336.7] | 37.7 | 0.8 | 3 | 418.7 | 123.8 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | n13_vpin_dir_with | 0.33 | 320.5 | 30.6 | 0.51 | 0.42 | 289.9 [94.3, 485.5] | 69.1 | 2.9 | 3 | 348.3 | 297.8 |
| K7/0 | n13_arr10_lo | 0.25 | 253.2 | 55.1 | 0.51 | 0.43 | 198.0 [60.8, 335.2] | 76.9 | 2.8 | 3 | 271.5 | 413.6 |
| K7/0 | n13_kurt15_hi | 0.06 | -121.1 | 102.1 | 0.38 | 0.45 | -223.2 [-435.5, -10.9] | -46.8 | -2.1 | 3 | -332.2 | -416.9 |
| K7/0 | n13_jshare60_lo | 0.47 | 36.2 | 134.8 | 0.42 | 0.46 | -98.6 [-199.0, 1.9] | -53.5 | -1.9 | 3 | -123.8 | -210.6 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | n13_vpin_lo | 0.22 | 152.1 | 10.8 | 0.47 | 0.42 | 141.4 [5.5, 277.2] | 0.0 | 2.0 | 3 | 53.9 | 213.6 |
| K7/1 | n13_skew15_strong_with | 0.29 | -47.2 | 69.5 | 0.39 | 0.44 | -116.7 [-244.4, 11.0] | -0.0 | -1.8 | 3 | -356.3 | -426.7 |
| K7/1 | n13_skew60_with | 0.59 | 73.6 | -20.2 | 0.43 | 0.42 | 93.8 [-23.5, 211.1] | 0.0 | 1.6 | 3 | 0.8 | 71.9 |
| K7/1 | n13_jump15_any | 0.08 | 166.0 | 23.5 | 0.48 | 0.42 | 142.5 [-83.6, 368.7] | 0.0 | 1.2 | 3 | 247.5 | 57.7 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | n13_lt50_since_gt300 | 0.76 | 38.7 | -63.8 | 0.44 | 0.38 | 102.4 [-15.3, 220.1] | 0.0 | 1.7 | 3 | 170.5 | 34.9 |
| K7/3 | n13_vpin_dir_with | 0.59 | -20.5 | 53.0 | 0.41 | 0.45 | -73.4 [-175.8, 28.9] | -0.0 | -1.4 | 3 | -41.4 | 64.3 |
| K7/3 | n13_arr60_hi | 0.19 | 73.3 | -5.2 | 0.45 | 0.42 | 78.5 [-48.4, 205.3] | 0.0 | 1.2 | 3 | 317.8 | 395.9 |
| K7/3 | n13_skew60_strong_against | 0.13 | -55.7 | 19.6 | 0.39 | 0.43 | -75.3 [-223.5, 73.0] | -0.0 | -1.0 | 3 | -290.9 | -495.4 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | n13_jshare15_lo | 0.55 | -0.4 | 137.9 | 0.43 | 0.50 | -138.3 [-281.0, 4.3] | -0.0 | -1.9 | 4 | -164.0 | -355.3 |
| K7/4 | n13_lt25_since_lt60 | 0.20 | -60.5 | 92.0 | 0.40 | 0.47 | -152.5 [-330.3, 25.3] | -0.0 | -1.7 | 4 | -220.7 | 11.8 |
| K7/4 | n13_lt25_last_with60 | 0.13 | -84.4 | 84.2 | 0.39 | 0.47 | -168.5 [-380.8, 43.7] | -0.0 | -1.6 | 3 | -160.8 | -230.6 |
| K7/4 | n13_arrival_vs_clock_hi | 0.37 | 122.7 | 25.6 | 0.46 | 0.46 | 97.1 [-50.9, 245.2] | 0.0 | 1.3 | 3 | 31.6 | -96.6 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | n13_spread_tight | 0.36 | 87.7 | -53.3 | 0.44 | 0.39 | 141.0 [30.9, 251.0] | 0.0 | 2.5 | 4 | 68.7 | -202.7 |
| M7/1 | n13_depth_thick | 0.08 | 217.0 | -22.9 | 0.48 | 0.40 | 239.9 [39.3, 440.4] | 0.0 | 2.3 | 4 | 337.6 | 438.0 |
| M7/1 | n13_vpin_dir_against | 0.09 | -167.7 | 6.8 | 0.36 | 0.41 | -174.6 [-340.8, -8.3] | -0.0 | -2.1 | 4 | -48.5 | -156.1 |
| M7/1 | n13_avgprint60_le115 | 0.07 | 160.3 | -14.7 | 0.46 | 0.40 | 175.0 [-29.4, 379.3] | 0.0 | 1.7 | 3 | 249.0 | -121.2 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | n13_arr_accel | 0.13 | 215.8 | 13.8 | 0.52 | 0.42 | 202.0 [46.1, 357.9] | 96.0 | 2.5 | 4 | 352.2 | 437.3 |
| M7/3 | n13_skew60_strong_with | 0.17 | -87.4 | 66.1 | 0.37 | 0.45 | -153.4 [-289.2, -17.7] | -83.5 | -2.2 | 4 | -229.8 | 52.4 |
| M7/3 | n13_arr300_lo | 0.31 | -41.5 | 77.0 | 0.40 | 0.45 | -118.5 [-229.5, -7.4] | -75.9 | -2.1 | 4 | -130.2 | -173.0 |
| M7/3 | n13_arr10_lo | 0.15 | -87.2 | 61.7 | 0.38 | 0.45 | -148.9 [-292.3, -5.5] | -77.0 | -2.0 | 3 | -420.2 | -303.3 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | n13_spread_tight | 0.38 | 296.3 | 103.6 | 0.41 | 0.35 | 192.6 [-29.5, 414.8] | 44.8 | 1.7 | 3 | 91.4 | 386.2 |
| O7/3 | n13_skew15_with | 0.67 | 226.7 | 75.2 | 0.40 | 0.33 | 151.4 [-70.7, 373.6] | 35.3 | 1.3 | 3 | 404.8 | 1074.4 |
| O7/3 | n13_skew60_strong_with | 0.67 | 209.2 | 110.0 | 0.39 | 0.34 | 99.3 [-124.6, 323.2] | 22.8 | 0.9 | 3 | 206.9 | 413.4 |
| O7/3 | n13_jump15_with | 0.62 | 193.9 | 146.4 | 0.38 | 0.36 | 47.5 [-170.6, 265.7] | 11.4 | 0.4 | 3 | 253.8 | 640.9 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | n13_jump15_with | 0.04 | -456.8 | 458.6 | 0.34 | 0.44 | -915.4 [-1800.2, -30.5] | -0.0 | -2.0 | 3 | -1080.6 | 2227.5 |
| P7/0 | n13_jump15_any | 0.05 | -130.4 | 450.7 | 0.38 | 0.44 | -581.1 [-1406.5, 244.3] | -0.0 | -1.4 | 3 | -630.2 | 2095.6 |
| P7/0 | n13_arr10_hi | 0.13 | 651.3 | 325.2 | 0.45 | 0.42 | 326.1 [-311.4, 963.7] | 0.0 | 1.0 | 3 | 234.7 | -824.5 |
| P7/0 | n13_arr10_lo | 0.38 | 232.6 | 450.7 | 0.42 | 0.43 | -218.0 [-661.5, 225.5] | -0.0 | -1.0 | 3 | -390.6 | -1115.6 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | n13_vpin_dir_with | 0.43 | 201.3 | -60.7 | 0.41 | 0.37 | 262.0 [22.4, 501.6] | 192.6 | 2.1 | 4 | 14.0 | -10.0 |
| P7/1 | n13_jump60_any | 0.21 | 240.8 | -20.9 | 0.41 | 0.37 | 261.7 [-20.0, 543.5] | 174.7 | 1.8 | 3 | 503.6 | 625.8 |
| P7/1 | n13_jshare60_hi | 0.03 | 509.8 | 19.4 | 0.45 | 0.38 | 490.4 [-179.8, 1160.7] | 128.4 | 1.4 | 3 | 487.4 | 185.2 |
| P7/1 | n13_arrival_vs_clock_lo | 0.21 | 180.9 | -5.5 | 0.42 | 0.37 | 186.5 [-83.9, 456.9] | 127.8 | 1.4 | 3 | 213.7 | -119.9 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | n13_vpin_dir_with | 0.30 | -226.9 | 48.2 | 0.33 | 0.41 | -275.1 [-553.5, 3.4] | -42.6 | -1.9 | 4 | -880.0 | -516.0 |
| P7/3 | n13_skew60_with | 0.58 | -129.7 | 101.3 | 0.36 | 0.43 | -231.1 [-495.3, 33.1] | -39.1 | -1.7 | 3 | -243.2 | -2.5 |
| P7/3 | n13_lt50_since_gt300 | 0.85 | -0.6 | -216.0 | 0.39 | 0.38 | 215.4 [-156.9, 587.7] | 20.0 | 1.1 | 3 | 176.0 | 38.6 |
| P7/3 | n13_jump60_any | 0.36 | -119.9 | 14.6 | 0.38 | 0.39 | -134.5 [-411.1, 142.1] | -21.1 | -1.0 | 3 | -691.6 | 403.8 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | n13_arr300_lo | 0.13 | -141.6 | 448.8 | 0.48 | 0.53 | -590.4 [-1381.8, 201.1] | -0.0 | -1.5 | 3 | -205.5 | 623.6 |
| U7/0 | n13_skew60_with | 0.76 | 297.3 | 658.6 | 0.51 | 0.59 | -361.3 [-950.5, 227.8] | -0.0 | -1.2 | 3 | -250.0 | -533.4 |
| U7/0 | n13_arr300_hi | 0.49 | 537.0 | 215.3 | 0.54 | 0.52 | 321.7 [-222.7, 866.2] | 0.0 | 1.2 | 3 | 114.0 | 1173.0 |
| U7/0 | n13_skew60_strong_with | 0.42 | 541.4 | 270.8 | 0.53 | 0.52 | 270.6 [-249.9, 791.1] | 0.0 | 1.0 | 4 | 519.3 | 413.9 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | n13_arr60_lo | 0.18 | -297.1 | 225.5 | 0.44 | 0.52 | -522.6 [-1126.4, 81.3] | -0.0 | -1.7 | 3 | -267.2 | 40.6 |
| U7/1 | n13_arr60_vs_300_hi | 0.15 | 599.0 | 51.6 | 0.58 | 0.49 | 547.4 [-98.7, 1193.4] | 0.0 | 1.7 | 4 | 877.7 | 1073.0 |
| U7/1 | n13_spread_wide | 0.15 | -263.4 | 201.7 | 0.47 | 0.51 | -465.1 [-1113.4, 183.2] | -0.0 | -1.4 | 3 | -226.9 | -9.7 |
| U7/1 | n13_skew60_with | 0.71 | 34.7 | 382.6 | 0.50 | 0.52 | -347.8 [-879.0, 183.3] | -0.0 | -1.3 | 3 | -988.7 | -1069.5 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_B13_micro.parquet

### B13 - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 62 conditions; 2832 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 10 conditions with |t|>2 (chance alone: about 3). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | n13_vpin_hi_dir_against | 0.00 | -11.3 | 1.1 | 0.37 | 0.50 | -12.4 [-17.3, -7.5] | -3.5 | -4.9 | 3 | -3.4 | -0.1 |
| ALL/ALL | n13_spread_tight | 0.41 | 1.8 | 1.0 | 0.51 | 0.50 | 0.9 [0.4, 1.3] | 0.8 | 3.6 | 3 | 1.6 | 4.1 |
| ALL/ALL | n13_avgprint300_ge16 | 0.16 | 2.2 | 1.2 | 0.51 | 0.50 | 1.1 [0.5, 1.7] | 1.0 | 3.6 | 3 | 2.5 | 6.7 |
| ALL/ALL | n13_skew15_strong_against | 0.15 | 0.4 | 1.5 | 0.49 | 0.50 | -1.1 [-1.7, -0.5] | -1.1 | -3.5 | 4 | -1.4 | -1.0 |
| ALL/ALL | n13_arr10_lo | 0.27 | 1.9 | 1.1 | 0.51 | 0.50 | 0.8 [0.3, 1.3] | 0.8 | 3.1 | 4 | 0.9 | 2.2 |
| ALL/ALL | n13_depth_thin | 0.08 | 0.0 | 1.4 | 0.49 | 0.50 | -1.4 [-2.3, -0.5] | -1.3 | -3.0 | 3 | -0.8 | 0.1 |
| ALL/ALL | n13_sweep120_with | 0.07 | 0.5 | 1.4 | 0.49 | 0.50 | -0.9 [-1.9, -0.0] | -0.9 | -2.0 | 3 | -1.8 | -0.6 |
| ALL/ALL | n13_arr60_hi | 0.28 | 1.0 | 1.5 | 0.50 | 0.50 | -0.5 [-1.0, 0.0] | -0.5 | -2.0 | 4 | -0.5 | 1.2 |
| ALL/ALL | n13_jump60_any | 0.23 | 1.0 | 1.5 | 0.49 | 0.50 | -0.5 [-1.0, 0.0] | -0.5 | -1.8 | 3 | -1.4 | -1.0 |
| ALL/ALL | n13_arr300_lo | 0.26 | 1.7 | 1.2 | 0.51 | 0.50 | 0.5 [-0.0, 1.0] | 0.5 | 1.8 | 3 | 0.9 | 0.7 |
| ALL/ALL | n13_vov240_hi | 0.07 | 2.1 | 1.3 | 0.50 | 0.50 | 0.8 [-0.1, 1.7] | 0.7 | 1.8 | 3 | 0.7 | 5.5 |
| ALL/ALL | n13_lt25_since_lt60 | 0.09 | 0.7 | 1.5 | 0.50 | 0.50 | -0.8 [-1.6, 0.1] | -0.7 | -1.7 | 3 | -2.1 | -1.1 |
| ALL/ALL | n13_sweep120_any | 0.10 | 0.7 | 1.4 | 0.49 | 0.50 | -0.7 [-1.5, 0.1] | -0.7 | -1.6 | 3 | -1.9 | -0.9 |
| ALL/ALL | n13_lt25_last_with60 | 0.06 | 0.6 | 1.4 | 0.50 | 0.50 | -0.8 [-1.8, 0.2] | -0.7 | -1.5 | 3 | -0.4 | 1.2 |
| ALL/ALL | n13_sweep_resilient_against | 0.09 | 2.5 | 0.5 | 0.50 | 0.49 | 2.0 [-0.8, 4.8] | 1.1 | 1.4 | 3 | 0.8 | 1.5 |
| ALL/ALL | n13_jshare15_hi | 0.14 | 1.0 | 1.4 | 0.50 | 0.50 | -0.5 [-1.1, 0.2] | -0.4 | -1.4 | 4 | -0.4 | 0.2 |
| ALL/ALL | n13_arr60_lo | 0.20 | 1.6 | 1.3 | 0.51 | 0.50 | 0.4 [-0.2, 0.9] | 0.4 | 1.4 | 3 | 0.7 | 0.5 |
| ALL/ALL | n13_arr300_hi | 0.26 | 1.1 | 1.4 | 0.50 | 0.50 | -0.3 [-0.9, 0.2] | -0.3 | -1.2 | 3 | -1.2 | -2.0 |
| ALL/ALL | n13_lt25_since_gt300 | 0.76 | 1.5 | 1.1 | 0.50 | 0.50 | 0.4 [-0.2, 0.9] | 0.3 | 1.2 | 3 | 1.5 | 0.9 |
| ALL/ALL | n13_arrival_vs_clock_hi | 0.25 | 1.6 | 1.2 | 0.50 | 0.50 | 0.3 [-0.2, 0.9] | 0.3 | 1.2 | 4 | 0.1 | 2.0 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | n13_vpin_dir_against | 0.09 | -2.0 | 3.8 | 0.45 | 0.52 | -5.8 [-8.3, -3.3] | -4.4 | -3.5 | 4 | -9.1 | -9.7 |
| ALL/0 | n13_jump15_any | 0.07 | 0.6 | 2.8 | 0.49 | 0.52 | -2.2 [-3.6, -0.9] | -2.1 | -2.9 | 4 | -3.0 | -1.4 |
| ALL/0 | n13_jump15_with | 0.06 | 0.8 | 2.8 | 0.50 | 0.52 | -2.0 [-3.4, -0.5] | -1.8 | -2.4 | 4 | -1.5 | 3.6 |
| ALL/0 | n13_vpin_lo | 0.11 | 6.2 | 2.9 | 0.54 | 0.51 | 3.3 [1.1, 5.5] | 2.7 | 2.4 | 4 | 0.1 | -0.6 |
| ALL/0 | n13_kurt15_hi | 0.04 | 0.1 | 2.8 | 0.50 | 0.52 | -2.6 [-4.5, -0.7] | -2.2 | -2.3 | 4 | -13.8 | -10.9 |
| ALL/0 | n13_arr60_vs_300_hi | 0.27 | 2.1 | 2.9 | 0.51 | 0.52 | -0.9 [-1.7, -0.1] | -0.8 | -2.1 | 4 | -1.3 | -0.4 |

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | n13_avgprint300_ge16 | 0.07 | 6.0 | 0.9 | 0.55 | 0.50 | 5.1 [3.5, 6.7] | 5.0 | 6.2 | 4 | 2.4 | 0.1 |
| ALL/1 | n13_lt25_since_lt10 | 0.01 | 11.4 | 1.3 | 0.59 | 0.50 | 10.0 [4.9, 15.2] | 8.6 | 3.3 | 4 | 14.3 | 22.4 |
| ALL/1 | n13_lt50_since_lt60 | 0.01 | 8.1 | 1.7 | 0.56 | 0.50 | 6.4 [1.6, 11.1] | 5.6 | 2.3 | 4 | 10.2 | 10.5 |
| ALL/1 | n13_skew15_strong_against | 0.15 | 0.2 | 1.4 | 0.49 | 0.50 | -1.3 [-2.5, -0.1] | -1.3 | -2.1 | 4 | -4.6 | -3.7 |
| ALL/1 | n13_lt25_since_lt60 | 0.04 | 3.6 | 1.3 | 0.52 | 0.50 | 2.2 [-0.1, 4.6] | 2.2 | 1.8 | 4 | 4.8 | 4.9 |
| ALL/1 | n13_sweep_thin_with | 0.32 | 5.9 | 1.6 | 0.53 | 0.50 | 4.3 [-0.9, 9.5] | 3.6 | 1.4 | 4 | 14.4 | 6.0 |

**all books, session 2**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/2 | n13_jump60_any | 0.39 | -5.6 | 2.6 | 0.45 | 0.52 | -8.2 [-10.6, -5.7] | -6.8 | -5.4 | 4 | -19.4 | -17.3 |
| ALL/2 | n13_kurt60_hi | 0.25 | -5.6 | 1.0 | 0.45 | 0.51 | -6.6 [-9.4, -3.8] | -5.2 | -3.7 | 4 | -12.2 | -7.6 |
| ALL/2 | n13_avgprint60_ge16 | 0.18 | -6.8 | 0.7 | 0.44 | 0.50 | -7.5 [-10.5, -4.4] | -5.7 | -3.6 | 4 | -17.5 | -11.3 |
| ALL/2 | n13_skew15_strong_against | 0.14 | -6.1 | 0.2 | 0.44 | 0.50 | -6.3 [-9.7, -2.9] | -4.5 | -2.6 | 4 | -10.3 | -11.7 |
| ALL/2 | n13_sweep_thin | 0.27 | -8.6 | -1.8 | 0.42 | 0.49 | -6.9 [-14.7, 1.0] | -2.2 | -0.6 | 4 | -5.3 | 7.9 |
| ALL/2 | n13_lt50_since_lt60 | 0.04 | -5.8 | -0.9 | 0.46 | 0.49 | -4.9 [-11.9, 2.1] | -1.8 | -0.5 | 4 | -1.2 | 6.6 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | n13_vpin_lo | 0.06 | -4.9 | 1.9 | 0.44 | 0.50 | -6.8 [-9.8, -3.8] | -5.9 | -3.9 | 4 | -4.7 | -11.7 |
| ALL/3 | n13_skew60_with | 0.60 | 0.7 | 2.7 | 0.49 | 0.51 | -2.0 [-3.4, -0.5] | -1.9 | -2.6 | 4 | -0.7 | 5.1 |
| ALL/3 | n13_sweep_thin_with | 0.15 | -2.0 | 2.1 | 0.46 | 0.50 | -4.1 [-7.7, -0.5] | -3.4 | -1.9 | 4 | -13.6 | 3.6 |
| ALL/3 | n13_sweep_resilient | 0.40 | 2.3 | 0.9 | 0.50 | 0.49 | 1.5 [-1.2, 4.1] | 1.3 | 1.0 | 4 | 5.6 | -0.9 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | n13_vpin_dir_against | 0.07 | 4.8 | -0.7 | 0.53 | 0.49 | 5.4 [2.9, 8.0] | 4.1 | 3.1 | 4 | 8.6 | 23.3 |
| ALL/4 | n13_avgprint60_ge16 | 0.38 | 1.1 | -1.1 | 0.50 | 0.48 | 2.2 [0.9, 3.6] | 2.0 | 2.9 | 4 | 3.0 | -2.2 |
| ALL/4 | n13_jump15_against | 0.00 | 7.5 | -0.3 | 0.55 | 0.49 | 7.8 [-2.3, 17.9] | 1.3 | 0.2 | 4 | 12.1 | 32.2 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | n13_jump60_any | 0.23 | 6.3 | -2.0 | 0.56 | 0.47 | 8.3 [6.3, 10.3] | 7.8 | 7.7 | 4 | 8.6 | 11.6 |
| ALL/5 | n13_kurt60_hi | 0.19 | 5.6 | -1.5 | 0.56 | 0.48 | 7.0 [5.0, 9.1] | 6.5 | 6.1 | 4 | 5.7 | 7.2 |
| ALL/5 | n13_skew60_with | 0.60 | 1.6 | -2.7 | 0.51 | 0.46 | 4.3 [2.7, 6.0] | 4.1 | 4.9 | 4 | 2.7 | 13.1 |
| ALL/5 | n13_skew60_strong_with | 0.26 | 3.5 | -1.4 | 0.54 | 0.48 | 4.9 [3.0, 6.8] | 4.6 | 4.8 | 4 | 0.9 | 2.2 |
| ALL/5 | n13_skew15_strong_against | 0.16 | -4.8 | 0.7 | 0.45 | 0.50 | -5.5 [-7.8, -3.3] | -5.1 | -4.5 | 4 | -6.6 | -7.2 |
| ALL/5 | n13_jump15_any | 0.07 | 7.4 | -0.8 | 0.58 | 0.49 | 8.2 [5.0, 11.4] | 6.9 | 4.2 | 4 | 4.4 | 8.5 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_B13_micro.parquet

## Sub-block D: realized vs implied vol, VIX term structure, megacap dispersion / breadth

### D - taken trades

Unit: $ per taken trade (engine net, as-run base lots). 32 conditions; 763 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 7 conditions with |t|>2 (chance alone: about 1). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | sd_rviv30_lt50 | 0.50 | 165.6 | 47.2 | 0.45 | 0.42 | 118.5 [56.6, 180.4] | 94.3 | 3.8 | 4 | 205.0 | 121.5 |
| ALL/ALL | sd_rviv60_lt50 | 0.49 | 158.3 | 54.7 | 0.46 | 0.42 | 103.6 [41.6, 165.5] | 82.4 | 3.3 | 4 | 137.4 | 229.4 |
| ALL/ALL | sd_rviv30_gt1 | 0.16 | 27.5 | 120.3 | 0.42 | 0.44 | -92.8 [-159.6, -26.1] | -71.5 | -2.7 | 3 | -62.1 | -56.4 |
| ALL/ALL | sd_rviv30_gt15 | 0.04 | -48.0 | 112.3 | 0.40 | 0.44 | -160.3 [-279.2, -41.4] | -82.3 | -2.6 | 4 | -103.0 | -72.0 |
| ALL/ALL | sd_rviv60_gt1 | 0.15 | 30.3 | 119.6 | 0.42 | 0.44 | -89.3 [-158.2, -20.4] | -67.7 | -2.5 | 4 | -64.4 | -4.5 |
| ALL/ALL | sd_mean5_with | 0.78 | 31.4 | 167.5 | 0.42 | 0.44 | -136.1 [-264.5, -7.7] | -64.6 | -2.1 | 3 | -197.9 | -347.2 |
| ALL/ALL | sd_rviv240_gt15 | 0.01 | 442.8 | 101.3 | 0.54 | 0.44 | 341.5 [17.0, 666.0] | 42.4 | 2.1 | 3 | 478.9 | 595.0 |
| ALL/ALL | sd_disp5_hi | 0.32 | 111.9 | 37.8 | 0.44 | 0.42 | 74.2 [-15.6, 163.9] | 48.2 | 1.6 | 3 | 77.6 | 89.1 |
| ALL/ALL | sd_rviv60_gt15 | 0.04 | 26.6 | 108.8 | 0.41 | 0.44 | -82.2 [-221.1, 56.7] | -35.8 | -1.2 | 3 | -34.7 | 58.3 |
| ALL/ALL | sd_rviv240_gt1 | 0.09 | 154.0 | 100.8 | 0.46 | 0.44 | 53.2 [-46.8, 153.3] | 31.8 | 1.0 | 3 | 95.1 | 123.3 |
| ALL/ALL | sd_rviv240_lt50 | 0.47 | 122.3 | 91.2 | 0.44 | 0.43 | 31.1 [-31.2, 93.5] | 24.7 | 1.0 | 3 | 62.8 | 238.2 |
| ALL/ALL | sd_vvix_vix_hi | 0.17 | 133.8 | 100.1 | 0.46 | 0.43 | 33.7 [-50.2, 117.7] | 22.9 | 0.8 | 3 | 529.6 | 583.8 |
| ALL/ALL | sd_disp5_lo | 0.20 | 17.8 | 72.4 | 0.42 | 0.43 | -54.6 [-202.4, 93.2] | -22.2 | -0.7 | 3 | -54.5 | -100.0 |
| ALL/ALL | sd_mean15_with | 0.80 | 40.9 | 77.3 | 0.42 | 0.41 | -36.4 [-172.8, 99.9] | -16.2 | -0.5 | 3 | -19.0 | 12.4 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/1 | sd_rviv60_lt50 | 0.70 | 93.2 | -116.3 | 0.44 | 0.36 | 209.4 [115.7, 303.2] | 0.0 | 0.0 | 4 | 35.6 | 240.4 |
| ALL/1 | sd_rviv30_lt50 | 0.69 | 75.4 | -68.2 | 0.43 | 0.38 | 143.6 [49.8, 237.4] | 0.0 | 0.0 | 4 | 37.6 | 0.9 |

**all books, session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/3 | sd_rviv60_gt15 | 0.11 | -59.8 | 38.3 | 0.39 | 0.42 | -98.1 [-216.3, 20.1] | -0.0 | -0.0 | 4 | -138.2 | 44.1 |
| ALL/3 | sd_vvix_vix_hi | 0.23 | 62.0 | 17.0 | 0.45 | 0.41 | 44.9 [-47.6, 137.4] | 0.0 | 0.0 | 4 | 326.7 | 386.1 |

Per book x session cell (>=150 trades), top 4 by |t| with the same stability filter:

**A7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7/0 | sd_vix_fall5d_with | 0.51 | 88.8 | 142.6 | 0.51 | 0.53 | -53.9 [-185.1, 77.4] | -0.0 | -0.8 | 3 | -124.3 | -194.0 |
| A7/0 | sd_vix_low | 0.24 | 151.9 | 103.3 | 0.55 | 0.51 | 48.6 [-106.2, 203.3] | 0.0 | 0.6 | 3 | 112.0 | 209.5 |

**H7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/0 | sd_vix_fall1d_with | 0.61 | 213.7 | 219.1 | 0.49 | 0.47 | -5.3 [-391.6, 381.0] | -0.0 | -0.0 | 3 | -108.0 | -73.7 |

**H7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H7/3 | sd_breadth5_ge5 | 0.55 | 268.9 | -36.3 | 0.59 | 0.42 | 305.1 [-18.0, 628.3] | 81.3 | 1.9 | 3 | 513.4 | 471.2 |
| H7/3 | sd_vix9d_inverted | 0.78 | 75.2 | -76.8 | 0.49 | 0.43 | 152.0 [-134.2, 438.2] | 48.1 | 1.0 | 3 | 28.9 | 1376.9 |
| H7/3 | sd_rviv60_gt1 | 0.52 | 9.1 | 78.6 | 0.47 | 0.49 | -69.6 [-302.9, 163.8] | -28.5 | -0.6 | 3 | -588.7 | -509.8 |
| H7/3 | sd_vix_fall5d_with | 0.52 | 32.5 | 53.3 | 0.48 | 0.48 | -20.8 [-254.5, 212.8] | -8.5 | -0.2 | 3 | -164.4 | 85.2 |

**K7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/0 | sd_vix_fall5d_with | 0.50 | 140.7 | 37.2 | 0.46 | 0.42 | 103.5 [3.1, 203.8] | 0.0 | 2.0 | 4 | 37.0 | 103.9 |
| K7/0 | sd_breadth15_ge5 | 0.57 | -58.9 | 151.6 | 0.40 | 0.47 | -210.5 [-440.8, 19.7] | -0.0 | -1.8 | 3 | -210.1 | 95.1 |
| K7/0 | sd_rviv240_gt1 | 0.09 | 191.4 | 79.1 | 0.48 | 0.44 | 112.3 [-65.4, 290.0] | 0.0 | 1.2 | 4 | 78.5 | 280.5 |
| K7/0 | sd_vix_contango | 0.76 | 79.3 | 119.3 | 0.44 | 0.45 | -40.1 [-157.5, 77.3] | -0.0 | -0.7 | 4 | -204.9 | -817.6 |

**K7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/1 | sd_vix_fall1d_with | 0.50 | 18.9 | 52.0 | 0.42 | 0.43 | -33.0 [-149.8, 83.8] | -0.0 | -0.6 | 3 | -109.8 | -47.5 |

**K7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/3 | sd_mean15_with | 0.88 | 14.5 | -135.8 | 0.42 | 0.38 | 150.3 [-53.6, 354.3] | 0.0 | 1.4 | 3 | 183.5 | 365.7 |
| K7/3 | sd_breadth60_le2 | 0.10 | -133.3 | 10.2 | 0.34 | 0.42 | -143.5 [-354.0, 67.0] | -0.0 | -1.3 | 3 | -172.0 | -57.2 |
| K7/3 | sd_rviv60_gt15 | 0.12 | -72.2 | 21.2 | 0.37 | 0.43 | -93.4 [-242.9, 56.0] | -0.0 | -1.2 | 4 | -43.8 | -118.4 |
| K7/3 | sd_vix_fall5d_with | 0.50 | -18.8 | 38.7 | 0.42 | 0.43 | -57.5 [-157.7, 42.6] | -0.0 | -1.1 | 3 | -145.8 | -137.9 |

**K7 session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7/4 | sd_rviv30_gt15 | 0.05 | 336.4 | 47.7 | 0.55 | 0.45 | 288.7 [-64.3, 641.7] | 0.0 | 1.6 | 3 | 142.1 | -1105.0 |
| K7/4 | sd_breadth60_ge5 | 0.68 | 105.4 | -13.4 | 0.48 | 0.43 | 118.8 [-72.3, 309.9] | 0.0 | 1.2 | 3 | 281.7 | 345.7 |
| K7/4 | sd_disp15_hi | 0.17 | -50.3 | 92.9 | 0.40 | 0.48 | -143.1 [-384.5, 98.2] | -0.0 | -1.2 | 3 | -115.3 | 297.9 |
| K7/4 | sd_rviv60_gt1 | 0.17 | 137.4 | 46.9 | 0.46 | 0.46 | 90.6 [-102.6, 283.7] | 0.0 | 0.9 | 3 | 204.6 | -1327.7 |

**M7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/1 | sd_rviv60_lt50 | 0.73 | 68.2 | -196.3 | 0.43 | 0.33 | 264.5 [145.2, 383.9] | 65.6 | 4.3 | 4 | 280.5 | 455.0 |
| M7/1 | sd_rviv30_lt50 | 0.71 | 45.5 | -123.9 | 0.43 | 0.35 | 169.4 [51.7, 287.0] | 42.9 | 2.8 | 4 | 122.7 | 93.7 |
| M7/1 | sd_vvix_vix_hi | 0.15 | 177.5 | -35.8 | 0.48 | 0.39 | 213.4 [62.5, 364.3] | 36.5 | 2.8 | 4 | 412.3 | 438.2 |
| M7/1 | sd_rviv240_lt50 | 0.80 | 32.4 | -140.7 | 0.42 | 0.34 | 173.1 [45.6, 300.5] | 38.8 | 2.7 | 4 | 110.5 | 194.3 |

**M7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M7/3 | sd_rviv30_gt15 | 0.16 | -64.1 | 60.0 | 0.37 | 0.45 | -124.1 [-260.4, 12.2] | -0.0 | -1.8 | 3 | -309.0 | -361.7 |
| M7/3 | sd_rviv240_gt1 | 0.21 | 116.1 | 19.8 | 0.46 | 0.43 | 96.3 [-28.2, 220.9] | 0.0 | 1.5 | 3 | 30.4 | 71.4 |
| M7/3 | sd_breadth5_ge5 | 0.62 | 31.7 | 129.0 | 0.42 | 0.47 | -97.3 [-235.4, 40.9] | -0.0 | -1.4 | 3 | -67.0 | 49.1 |
| M7/3 | sd_rviv30_gt1 | 0.52 | 13.0 | 69.6 | 0.42 | 0.46 | -56.6 [-160.1, 47.0] | -0.0 | -1.1 | 3 | -90.7 | -47.6 |

**O7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O7/3 | sd_vix9d_inverted | 0.82 | 225.2 | -52.4 | 0.40 | 0.28 | 277.5 [17.1, 538.0] | 0.0 | 2.1 | 3 | 1049.3 | 803.9 |
| O7/3 | sd_rviv30_gt1 | 0.53 | 170.1 | 182.9 | 0.38 | 0.37 | -12.8 [-225.8, 200.3] | -0.0 | -0.1 | 3 | -166.0 | 796.9 |

**P7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/0 | sd_vvix_vix_hi | 0.14 | 873.1 | 348.9 | 0.49 | 0.43 | 524.2 [-87.4, 1135.8] | 161.5 | 1.7 | 3 | 3140.6 | 3423.4 |
| P7/0 | sd_vix_low | 0.21 | 658.7 | 360.5 | 0.47 | 0.43 | 298.2 [-198.5, 794.9] | 120.2 | 1.2 | 3 | 432.4 | 784.0 |
| P7/0 | sd_vix_fall1d_with | 0.52 | 534.9 | 301.2 | 0.46 | 0.42 | 233.7 [-157.2, 624.6] | 121.9 | 1.2 | 3 | 324.6 | 94.3 |

**P7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/1 | sd_rviv240_lt50 | 0.76 | 92.1 | -145.7 | 0.39 | 0.34 | 237.8 [-15.6, 491.1] | 0.0 | 1.8 | 3 | 232.2 | 688.1 |
| P7/1 | sd_vvix_vix_hi | 0.13 | -200.8 | 70.4 | 0.33 | 0.39 | -271.2 [-615.3, 72.8] | -0.0 | -1.5 | 3 | -506.9 | -645.5 |
| P7/1 | sd_rviv30_lt50 | 0.68 | 88.4 | -81.4 | 0.40 | 0.35 | 169.9 [-71.3, 411.1] | 0.0 | 1.4 | 3 | 15.7 | -27.0 |
| P7/1 | sd_vix9d_inverted | 0.75 | 77.0 | -96.8 | 0.39 | 0.35 | 173.8 [-89.5, 437.1] | 0.0 | 1.3 | 3 | 562.3 | 1177.8 |

**P7 session 3**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7/3 | sd_vix_fall1d_with | 0.51 | 69.1 | -139.8 | 0.41 | 0.37 | 208.9 [-50.4, 468.3] | 0.0 | 1.6 | 4 | 233.1 | 760.3 |
| P7/3 | sd_rviv60_gt1 | 0.49 | -93.8 | 24.9 | 0.39 | 0.39 | -118.7 [-378.8, 141.4] | -0.0 | -0.9 | 3 | -476.1 | -173.8 |
| P7/3 | sd_rviv30_gt1 | 0.45 | -89.6 | 13.1 | 0.39 | 0.39 | -102.6 [-364.3, 159.0] | -0.0 | -0.8 | 3 | -319.9 | -370.9 |
| P7/3 | sd_disp60_hi | 0.65 | 16.3 | -116.5 | 0.41 | 0.33 | 132.8 [-235.1, 500.6] | 0.0 | 0.7 | 3 | 111.8 | -97.0 |

**U7 session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/0 | sd_vix_fall1d_with | 0.39 | 485.6 | 320.1 | 0.55 | 0.51 | 165.5 [-358.0, 689.0] | 0.0 | 0.6 | 3 | 475.2 | 502.0 |
| U7/0 | sd_vix9d_inverted | 0.79 | 369.5 | 445.0 | 0.52 | 0.56 | -75.5 [-718.5, 567.4] | -0.0 | -0.2 | 3 | -219.2 | -2538.7 |

**U7 session 1**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U7/1 | sd_rviv30_lt50 | 0.72 | 258.1 | -179.4 | 0.53 | 0.44 | 437.5 [-73.9, 948.9] | 0.0 | 1.7 | 4 | 112.3 | 70.2 |
| U7/1 | sd_vix_fall5d_with | 0.49 | 203.1 | 68.4 | 0.52 | 0.49 | 134.6 [-341.3, 610.6] | 0.0 | 0.6 | 3 | 76.9 | -801.9 |
| U7/1 | sd_rviv240_lt50 | 0.85 | 152.9 | 29.4 | 0.51 | 0.45 | 123.5 [-522.5, 769.5] | 0.0 | 0.4 | 3 | 15.0 | 1460.3 |
| U7/1 | sd_vix_low | 0.24 | 176.3 | 120.3 | 0.52 | 0.50 | 56.0 [-497.2, 609.2] | 0.0 | 0.2 | 3 | 373.8 | -148.0 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/score_D_statext_named.parquet

### D - whole signal universe (taken + skipped)

Unit: points per signal (hypothetical 60-pt target/stop style outcome, ALL signals incl. skipped). 32 conditions; 1501 condition x cell tests with >=20 yes and >=20 no. Pooled cell: 22 conditions with |t|>2 (chance alone: about 1). A map, not findings: most best-looking items are noise unless they keep sign by year and in L6M.

Pooled, top 20 by |t| that also keep the sign in >=3 of 4 years and in L6M:

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/ALL | sd_rviv30_lt50 | 0.64 | 2.0 | 0.3 | 0.51 | 0.49 | 1.7 [1.2, 2.2] | 1.6 | 6.8 | 3 | 2.8 | 4.5 |
| ALL/ALL | sd_rviv60_lt50 | 0.63 | 2.0 | 0.3 | 0.51 | 0.49 | 1.7 [1.2, 2.2] | 1.6 | 6.7 | 3 | 2.9 | 5.4 |
| ALL/ALL | sd_breadth60_ge5 | 0.62 | 0.1 | 2.8 | 0.49 | 0.51 | -2.7 [-3.7, -1.7] | -2.4 | -5.5 | 3 | -3.5 | -4.3 |
| ALL/ALL | sd_rviv240_lt50 | 0.58 | 1.9 | 0.6 | 0.51 | 0.49 | 1.3 [0.8, 1.7] | 1.2 | 5.3 | 3 | 2.9 | 6.1 |
| ALL/ALL | sd_breadth5_ge5 | 0.50 | 0.1 | 2.0 | 0.49 | 0.51 | -1.9 [-2.8, -1.0] | -1.7 | -4.1 | 3 | -0.2 | -0.1 |
| ALL/ALL | sd_vix9d_inverted | 0.79 | 1.6 | 0.5 | 0.50 | 0.49 | 1.1 [0.5, 1.6] | 1.0 | 3.7 | 3 | 6.6 | 2.3 |
| ALL/ALL | sd_disp60_hi | 0.26 | 2.5 | 0.7 | 0.51 | 0.50 | 1.8 [0.7, 2.9] | 1.5 | 3.1 | 3 | 1.5 | -0.6 |
| ALL/ALL | sd_breadth60_le2 | 0.10 | 3.2 | 0.9 | 0.52 | 0.50 | 2.4 [0.8, 3.9] | 1.8 | 3.0 | 3 | 5.4 | 6.2 |
| ALL/ALL | sd_mean60_with | 0.82 | 0.8 | 2.6 | 0.50 | 0.51 | -1.8 [-3.1, -0.6] | -1.5 | -2.9 | 3 | -4.6 | -5.9 |
| ALL/ALL | sd_disp5_hi | 0.25 | 2.2 | 0.8 | 0.50 | 0.50 | 1.4 [0.3, 2.5] | 1.2 | 2.5 | 3 | 2.9 | 1.3 |
| ALL/ALL | sd_vvix_vix_hi | 0.23 | 1.8 | 1.2 | 0.51 | 0.50 | 0.6 [0.1, 1.1] | 0.6 | 2.5 | 3 | 7.2 | 8.1 |
| ALL/ALL | sd_disp15_hi | 0.25 | 2.1 | 0.9 | 0.50 | 0.50 | 1.2 [0.1, 2.3] | 1.0 | 2.2 | 3 | 1.6 | 1.2 |
| ALL/ALL | sd_rviv240_gt15 | 0.01 | 4.1 | 1.3 | 0.53 | 0.50 | 2.8 [0.1, 5.4] | 1.4 | 2.0 | 3 | 14.0 | 24.4 |

Per session (all books), conditions with the SAME SIGN in every year 2023-2026 and in L6M, n yes >= 50, ranked by shrunk effect / se (the t column in these per-session tables is shrunk lift / se; session codes 0 asia, 1 london, 2 pre, 3 NY AM, 4 NY PM, 5 close):

**all books, session 0**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/0 | sd_rviv240_gt1 | 0.04 | 10.4 | 2.4 | 0.58 | 0.51 | 8.0 [5.8, 10.2] | 7.2 | 6.4 | 4 | 13.1 | 19.2 |

**all books, session 4**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/4 | sd_vix_fall1d_with | 0.50 | 2.2 | -2.8 | 0.51 | 0.47 | 5.0 [3.6, 6.3] | 4.7 | 6.8 | 4 | 4.4 | 13.0 |
| ALL/4 | sd_vix_contango | 0.82 | 0.3 | -2.7 | 0.50 | 0.47 | 2.9 [1.1, 4.8] | 2.6 | 2.8 | 4 | 12.7 | 15.0 |

**all books, session 5**

| cell | condition | share yes | exp yes | exp no | WR yes | WR no | lift [95% CI] | shrunk lift | t | years same sign (of 4) | lift L6M | lift L3M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL/5 | sd_vix_low | 0.29 | 0.3 | -0.4 | 0.49 | 0.49 | 0.7 [-0.9, 2.3] | 0.5 | 0.6 | 4 | 15.7 | 21.7 |

Full per-cell table: /mnt/l2/l2vast/_confl/cols_cf5/scoreU_D_statext_named.parquet
