# DS3_UW_WIDE - Unusual Whales WIDE program (W-UW2). Rebuilt 2026-11-14T14:33:25Z by code/th_uw/uw_page.py (every 3 h). Research only, shadow, NO PASS claim.
Rule: best candidate per use is always named with its honest strength; "null q95" = max over all cells of the group when the feature matrix is permuted within month (30-40 draws), so recents below it is chance-level. Windows: L1M L3M L6M HOLD PREUW (PRE clipped to the 2024-10-01 UW start); X' has NO UW data (history starts 2024-10); first-order $/wk, history unmodified, fees in net_fee. Screens are in-sample on thresholds (HOLD quantiles). Gain sign: E skip = -pnl of flagged entries, press = +0.5x pnl (size x1.5), K/Q hold = hold outcome minus actual at the cut/clip.

## 1. Status (what finished / running / died)
- screen (first read, features A regime, B levels, C Tide, D charm/vanna; RTH) and screen2 (WIDE: 1/5/15/60-min deltas, 10:00/10:30 regime, pre-market/prior-close LAST priors, Tide extremes/divergence; scopes rth/late/asia/london): FINISHED for JN05W2, JN05W2J, LPB_BASE (screen2 finished ~02:00Z 11-13; nobody read it until 14:15Z: lead watcher bug).
- pull IV (volatility stats SPX/NDX/QQQ/SPY): 6636 files under /mnt/l2/l2vast/uw (pull finished; features from them NOT yet screened)
- pull dark pool price levels (QQQ SPY + 8 NQ weights, 260 d): 2600 files under /mnt/l2/l2vast/uw (pull finished; features from them NOT yet screened)
- identity gate: TL3_UW_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL; TL3J_UW_ID 202610: 658 trades net 23596.16 vs JN05W2J 658 net 23596.16 -> IDENTICAL
- exact sets (TP engine, one set per job, tag UW): TL3J_UW_ID: 1 months; TL3J_UW_KLDN_HOLD: 6 months; TL3J_UW_NDXCA_SK: 6 months; TL3J_UW_SPXVDIR_PR: 12 months; TL3_UW_FA1: 21 months; TL3_UW_FA1P11: 12 months; TL3_UW_FA1P23: 12 months; TL3_UW_FA1P37: 12 months; TL3_UW_FA2: 21 months; TL3_UW_FA2P11: 12 months; TL3_UW_FA2P23: 12 months; TL3_UW_FA2P37: 12 months; TL3_UW_FA3: 21 months; TL3_UW_FA3P11: 12 months; TL3_UW_FA3P23: 12 months; TL3_UW_FA3P37: 12 months; TL3_UW_FA4: 21 months; TL3_UW_FA4P11: 12 months; TL3_UW_FA4P23: 12 months; TL3_UW_FA4P37: 12 months; TL3_UW_FA5: 21 months; TL3_UW_FA6: 21 months; TL3_UW_FAID: 1 months; TL3_UW_FF1: 21 months; TL3_UW_FF1P11: 12 months; TL3_UW_FF1P23: 12 months; TL3_UW_FF1P37: 12 months; TL3_UW_FF2: 12 months; TL3_UW_FF2P11: 12 months; TL3_UW_FF2P23: 12 months; TL3_UW_FF2P37: 12 months; TL3_UW_FF3: 12 months; TL3_UW_FF3P11: 12 months; TL3_UW_FF3P23: 12 months; TL3_UW_FF3P37: 12 months; TL3_UW_FF4: 12 months; TL3_UW_FF4P11: 12 months; TL3_UW_FF4P23: 12 months; TL3_UW_FF4P37: 12 months; TL3_UW_FF5: 12 months; TL3_UW_FN11: 12 months; TL3_UW_FN23: 12 months; TL3_UW_FN37: 12 months; TL3_UW_ID: 1 months; TL3_UW_INJID: 1 months; TL3_UW_INJ_ASIA: 21 months; TL3_UW_INJ_MFB1: 21 months; TL3_UW_INJ_MFB1_P11: 12 months; TL3_UW_INJ_MFB1_P23: 12 months; TL3_UW_INJ_MFB1_P37: 12 months; TL3_UW_INJ_MFB2: 21 months; TL3_UW_INJ_MFB2_P11: 12 months; TL3_UW_INJ_MFB2_P23: 12 months; TL3_UW_INJ_MFB2_P37: 12 months; TL3_UW_INJ_MFB3: 21 months; TL3_UW_INJ_MFB4: 21 months; TL3_UW_INJ_MFB6: 21 months; TL3_UW_INJ_MFB7: 21 months; TL3_UW_INJ_MFB7_P11: 12 months; TL3_UW_INJ_MFB7_P23: 12 months; TL3_UW_INJ_MFB7_P37: 12 months; TL3_UW_INJ_MFC_ASIA: 21 months; TL3_UW_INJ_MFC_ASIA_P11: 12 months; TL3_UW_INJ_MFC_ASIA_P23: 12 months; TL3_UW_INJ_MFC_LDN: 21 months; TL3_UW_INJ_MFC_LDN_P11: 12 months; TL3_UW_INJ_MFC_LDN_P23: 12 months; TL3_UW_INJ_MFC_PRE: 21 months; TL3_UW_INJ_MFC_PRE_P11: 12 months; TL3_UW_INJ_MFC_PRE_P23: 12 months; TL3_UW_INJ_NDXB: 21 months; TL3_UW_INJ_NYAM: 21 months; TL3_UW_INJ_PRE: 21 months; TL3_UW_INJ_PRE2: 6 months; TL3_UW_KLDN_HOLD: 6 months; TL3_UW_MF_ASIA_SK: 18 months; TL3_UW_MF_LDN_M7: 21 months; TL3_UW_MF_NIGHT_HALF: 18 months; TL3_UW_MF_NIGHT_SK: 18 months; TL3_UW_MF_NIGHT_SK15: 18 months; TL3_UW_MF_NIGHT_SK_P11: 12 months; TL3_UW_MF_NIGHT_SK_P23: 12 months; TL3_UW_MF_NIGHT_SK_P37: 12 months; TL3_UW_MF_NYAM_K7: 18 months; TL3_UW_MF_U7_SK: 18 months; TL3_UW_NDXCA_SK: 6 months; TL3_UW_NDXCA_SKP7: 6 months; TL3_UW_QQQGD15_PR: 12 months; TL3_UW_QQQGD15_SK: 12 months; TL3_UW_TDNV_PR: 12 months
- died/blocked: nothing died. Overnight the four first sets waited in TOOLS (box load ~40, cap 25); admitted 03:03Z-~11:00Z, L6M finished; HOLD months started 14:25Z after the UW priority tag. 0DTE walls: history is end-of-day only (not causal); expected-move inputs pulled but not yet screened.

## 2. Best candidate per use per base (screen2, ranked by recents = (L6M+HOLD)/2 $/wk; top 3 per use/action; LEAD = recents > null q95, L3M>0, both L6M halves > 0)

### screen2 LPB_BASE (42 groups x ~3,000 cells; LEAD cells: 6)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | W_NQ_z15 | le | 0.2917 | 1731 | 1117 | 6155 | 7452 | 6750 | 4118 | 7101 | 7769 | 0.8 | 1.066e+05 | 0 | False |
| ALL | asia | W_NQ_z15 | le | 0.2057 | 1496 | 488.8 | 5920 | 6711 | 6515 | 3960 | 6613 | 7769 | 0.2 | 9.803e+04 | 0 | False |
| ALL | asia | W_LAST_TD_net_s | ge | -5.144e+08 | 1709 | 3390 | 7152 | 6637 | 6580 | 4708 | 6608 | 7769 | 0.4 | 7.157e+04 | 0 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | W_LAST_SPX_g_dir | le | 9.126e+10 | 289 | 8369 | 4684 | 3727 | 3038 | -4131 | 3383 | 2511 | 1 | 1.597e+04 | 0 | True |
| P7 | asia | W_LAST_NDX_c_oi | le | -1.396e+11 | 184 | 7539 | 4427 | 3284 | 1974 | -1007 | 2629 | 2713 | 1 | -2.538e+04 | 2 | False |
| P7 | asia | W_LAST_SPX_v_oi_s | ge | 1.392e+09 | 129 | 7012 | 2319 | 3018 | 2172 | 702.7 | 2595 | 2713 | 1 | -2.262e+04 | 0 | False |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | rth | D_NDX_v_oi | le | 1.388e+08 | 138 | 0 | -38.28 | 2807 | 3091 | 1019 | 2949 | 2955 | 1 | 2.41e+04 | 0 | False |
| ALL | rth | D_SPX_v_oi | le | 2.218e+09 | 253 | -124.3 | 443 | 3015 | 2714 | 1261 | 2865 | 2955 | 0.85 | 1.741e+04 | 0 | False |
| ALL | rth | W_NDX_c_vol_d1 | ge | -2.043e+10 | 275 | -455.7 | 586.9 | 3047 | 2615 | 1729 | 2831 | 2955 | 1 | 2.184e+04 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth +830; E press P7 rth -29; E skip P7 asia -436; E press P7 asia +1585; E skip P7 london -706; E press P7 london +590; E skip K7 rth +20; E press K7 rth +106; E skip K7 asia -393; E press K7 asia +730; E skip K7 london -534; E press K7 london +50; E skip M7 rth -149; E press M7 rth +26; E skip M7 london +648; E press M7 london -236; E skip U7 asia -293; E press U7 asia +248; E skip U7 london -525; E press U7 london +58; E skip H7 rth -171; E press H7 rth +49; E skip H7 asia +306; E press H7 asia +310; E skip ALL rth -197; E press ALL rth +54; E skip ALL late +89; E press ALL late -43; E skip ALL asia -1062; E press ALL asia +4525; E skip ALL london -1947; E press ALL london +291; K hold P7 rth +971; K hold P7 asia -1225; K hold P7 london +111; K hold K7 rth +67; K hold K7 asia -55; K hold K7 london -37; K hold ALL rth +1823; K hold ALL late +85; K hold ALL asia -628; K hold ALL london +644

### screen2 JN05W2 (41 groups x ~3,000 cells; LEAD cells: 5)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | W_NQ_z15 | le | 0.2906 | 1774 | 3051 | 7002 | 9917 | 7298 | 4114 | 8607 | 9027 | 0.9 | 1.28e+05 | 1 | False |
| ALL | asia | W_LAST_TD_net_s | ge | -5.144e+08 | 1753 | 4170 | 7343 | 9154 | 7332 | 4584 | 8243 | 9027 | 0.55 | 1.312e+05 | 0 | False |
| ALL | asia | W_NQ_z15 | le | 0.2051 | 1524 | 2300 | 6558 | 9102 | 6939 | 3945 | 8020 | 9027 | 0.2 | 1.225e+05 | 0 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | W_LAST_NDX_c_oi_s | ge | 3.594e+12 | 262 | 1.371e+04 | 5812 | 3500 | 1764 | -397.3 | 2632 | 1753 | 1 | 2.463e+04 | 0 | True |
| P7 | asia | W_LAST_NDX_c_oi_s | ge | 3.474e+12 | 76 | 1.095e+04 | 4599 | 2612 | 1317 | 21.16 | 1964 | 1786 | 1 | 1.137e+04 | 0 | True |
| P7 | asia | W_LAST_QQQ_c_oi_s | ge | 1.906e+13 | 54 | 9649 | 3960 | 2874 | 712.3 | -31.01 | 1793 | 1786 | 1 | 9154 | 0 | True |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P7 | asia | W_NQ_z15 | ge | -0.09292 | 140 | -484 | 3162 | 1582 | 2998 | 358.5 | 2290 | 3410 | 1 | 922 | 1 | False |
| P7 | asia | W_NQ_z15 | ge | -0.1309 | 193 | -5283 | 3665 | 1490 | 2273 | 1293 | 1881 | 3410 | 1 | -401.8 | 1 | False |
| ALL | rth | D_SPX_v_vol | le | 4.602e+08 | 84 | -491.5 | 157.5 | 1826 | 1720 | 2410 | 1773 | 1788 | 1 | 4866 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth -145; E press P7 rth +34; E skip P7 asia -1854; E press P7 asia +2758; E skip P7 london -246; E press P7 london +301; E skip K7 rth -461; E press K7 rth +143; E skip K7 asia -75; E press K7 asia +925; E skip K7 london -72; E press K7 london +272; E skip M7 rth -427; E press M7 rth +68; E skip M7 london +516; E press M7 london -113; E skip U7 asia -413; E press U7 asia +274; E skip U7 london -457; E press U7 london +151; E skip H7 rth +65; E press H7 rth -0; E skip H7 asia +285; E press H7 asia +304; E skip ALL rth -520; E press ALL rth +418; E skip ALL late -140; E press ALL late -9; E skip ALL asia -3296; E press ALL asia +5518; E skip ALL london -647; E press ALL london +156; K hold P7 rth +744; K hold P7 asia -1016; K hold P7 london -637; K hold K7 rth +72; K hold K7 asia +140; K hold K7 london -79; K hold ALL rth +1246; K hold ALL asia -1130; K hold ALL london +10

### screen2 JN05W2J (41 groups x ~3,000 cells; LEAD cells: 4)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | W_NQ_z15 | le | 0.2893 | 1808 | 1196 | 6889 | 8527 | 6026 | 3041 | 7277 | 7386 | 0.9 | 1.03e+05 | 0 | False |
| ALL | asia | W_NQ_z15 | le | 0.2028 | 1558 | 1462 | 6754 | 7776 | 5730 | 2878 | 6753 | 7386 | 0.05 | 9.214e+04 | 0 | False |
| ALL | asia | W_LAST_TD_net_s | le | 5.749e+08 | 1820 | 2947 | 6445 | 8030 | 5461 | 3568 | 6746 | 7386 | 0.3 | 9.91e+04 | 0 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | W_LAST_NDX_c_oi_s | ge | 3.594e+12 | 266 | 9043 | 3475 | 2485 | 1252 | -1170 | 1869 | 1022 | 1 | 1.627e+04 | 0 | True |
| M7 | london | W_LAST_QQQ_c_oi_s | le | 1.231e+12 | 290 | 2430 | 1386 | 1775 | 1229 | 190 | 1502 | 1500 | 1 | 1.526e+04 | 0 | True |
| M7 | london | W_LAST_QQQ_c_oi_s | le | 1.317e+13 | 377 | 3919 | 1333 | 1719 | 1075 | -148.6 | 1397 | 1500 | 1 | 1.093e+04 | 0 | False |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | rth | D_NDX_v_vol | le | 2.978e+07 | 125 | -482.5 | 334 | 1364 | 1502 | 1281 | 1433 | 1570 | 1 | 1636 | 0 | False |
| ALL | rth | B_SPX_oi_behind | ge | 140.9 | 145 | -439.1 | 371.7 | 1564 | 1302 | 955.3 | 1433 | 1570 | 1 | 6550 | 0 | False |
| ALL | rth | W_QQQ_g_vol_d60 | ge | -2.396e+09 | 197 | -665.1 | -349.2 | 1398 | 1464 | 1968 | 1431 | 1570 | 1 | 3557 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth +45; E press P7 rth +66; E skip P7 asia -953; E press P7 asia +1917; E skip P7 london -334; E press P7 london +65; E skip K7 rth -436; E press K7 rth +77; E skip K7 asia -193; E press K7 asia +895; E skip K7 london -269; E press K7 london +32; E skip M7 rth -178; E press M7 rth +189; E skip M7 london +381; E press M7 london -168; E skip U7 asia -290; E press U7 asia +160; E skip U7 london -83; E press U7 london +176; E skip H7 rth -6; E press H7 rth +3; E skip H7 asia +6; E press H7 asia +297; E skip ALL rth -731; E press ALL rth +309; E skip ALL late -364; E press ALL late +114; E skip ALL asia -734; E press ALL asia +4583; E skip ALL london +256; E press ALL london -58; K hold P7 rth +253; K hold P7 asia -259; K hold P7 london -216; K hold K7 rth +105; K hold K7 asia +161; K hold K7 london -93; K hold ALL rth +1060; K hold ALL asia -676; K hold ALL london +250

### screen3 LPB_BASE (42 groups x ~3,000 cells; LEAD cells: 10)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F3_EMroom_SPX | le | 331.9 | 1759 | 3249 | 6271 | 7972 | 6897 | 5452 | 7434 | 7738 | 0.85 | 1.161e+05 | 0 | False |
| ALL | asia | F3_IVrank_QQQ | le | 74.1 | 1671 | 3202 | 6283 | 7858 | 6984 | 5607 | 7421 | 7738 | 0.9 | 1.091e+05 | 0 | False |
| ALL | asia | F3_VRP_SPX | le | 0.05622 | 1937 | 3202 | 6283 | 7212 | 7539 | 4398 | 7376 | 7738 | 1 | 1.091e+05 | 0 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | W_R10_SPY_g_dir | le | 0 | 682 | 6901 | 1782 | 3694 | 1446 | -5565 | 2570 | 2442 | 1 | 1.029e+04 | 3 | True |
| ALL | asia | W_R10_SPY_g_dir | le | -1.709e+08 | 552 | 6901 | 2205 | 3207 | 1670 | -3356 | 2438 | 2442 | 1 | 1.23e+04 | 3 | False |
| ALL | rth | W_R10_SPY_g_dir | ge | 4.926e+08 | 314 | -182.2 | 2740 | 1997 | 2825 | 131.9 | 2411 | 2030 | 1 | 5817 | 0 | True |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | rth | F3_VRP_NDX | ge | -0.03143 | 225 | -661.4 | -557.4 | 2868 | 2644 | 1087 | 2756 | 2701 | 1 | 2.667e+04 | 0 | False |
| ALL | rth | F3_VRP_NDX | ge | -0.05159 | 300 | -661.4 | -447.9 | 2673 | 2560 | 1101 | 2617 | 2701 | 1 | 2.079e+04 | 0 | False |
| ALL | rth | F3_VRP_NDX | le | 0.0669 | 371 | -435 | -1024 | 2132 | 2557 | 1226 | 2345 | 2701 | 1 | 1.604e+04 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth +652; E press P7 rth -329; E skip P7 asia -1488; E press P7 asia +3549; E skip P7 london -517; E press P7 london +704; E skip K7 rth -192; E press K7 rth -21; E skip K7 asia -213; E press K7 asia +729; E skip K7 london -145; E press K7 london -108; E skip M7 rth -274; E press M7 rth +85; E skip M7 london -182; E press M7 london -266; E skip U7 asia -883; E press U7 asia +526; E skip U7 london -604; E press U7 london -67; E skip H7 rth -106; E press H7 rth +37; E skip H7 asia -134; E press H7 asia +472; E skip ALL rth -80; E press ALL rth -32; E skip ALL late +159; E press ALL late -5; E skip ALL asia -1405; E press ALL asia +4704; E skip ALL london -683; E press ALL london +786; K hold P7 rth +1111; K hold P7 asia -1244; K hold P7 london -518; K hold K7 rth +103; K hold K7 asia +192; K hold K7 london +50; K hold ALL rth +1508; K hold ALL late +71; K hold ALL asia -1148; K hold ALL london -222

### screen3 JN05W2 (41 groups x ~3,000 cells; LEAD cells: 13)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F3_EMroom_SPX | le | 341.2 | 1797 | 5593 | 7424 | 1.063e+04 | 7441 | 5664 | 9036 | 9362 | 0.95 | 1.281e+05 | 1 | False |
| ALL | asia | F3_EMroom_NDX | le | 465.7 | 1748 | 5196 | 7473 | 1.029e+04 | 7281 | 5124 | 8784 | 9362 | 0.95 | 1.196e+05 | 1 | False |
| ALL | asia | F3_IV_SPY | le | 0.19 | 2012 | 4565 | 6923 | 9828 | 7680 | 3163 | 8754 | 9362 | 1 | 1.256e+05 | 1 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | W_R1030_SPX_g_oi | le | -2.348e+10 | 166 | 4045 | 3025 | 1435 | 2790 | -1541 | 2113 | 1986 | 1 | 4848 | 0 | True |
| ALL | asia | W_R10_SPY_g_dir | le | -1.675e+08 | 570 | 9494 | 3218 | 2337 | 1190 | -1709 | 1764 | 1986 | 1 | -4.157e+04 | 0 | False |
| ALL | asia | W_R10_SPY_g_dir | le | 0 | 691 | 9494 | 2354 | 2685 | 738.1 | -3452 | 1711 | 1986 | 1 | -4.894e+04 | 0 | False |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F3_IV_NDX | le | 0.194 | 196 | -6598 | 4412 | 3309 | 3256 | -1.618 | 3283 | 3682 | 1 | 2.931e+04 | 0 | False |
| P7 | asia | F3_IV_NDX | le | 0.194 | 92 | -6460 | 4456 | 3207 | 2971 | 224.6 | 3089 | 3606 | 1 | 2.884e+04 | 0 | False |
| ALL | asia | F3_EMpts_NDX | le | 376.4 | 230 | -6752 | 2840 | 2418 | 3464 | 352.3 | 2941 | 3682 | 1 | 2.974e+04 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth +117; E press P7 rth +178; E skip P7 asia -232; E press P7 asia +2923; E skip P7 london -209; E press P7 london +396; E skip K7 rth +102; E press K7 rth +317; E skip K7 asia -256; E press K7 asia +939; E skip K7 london -211; E press K7 london +147; E skip M7 rth -508; E press M7 rth -57; E skip M7 london -35; E press M7 london -205; E skip U7 asia -882; E press U7 asia +492; E skip U7 london -572; E press U7 london -92; E skip H7 rth -52; E press H7 rth -27; E skip H7 asia -6; E press H7 asia +495; E skip ALL rth -791; E press ALL rth +281; E skip ALL late -19; E press ALL late +96; E skip ALL asia -206; E press ALL asia +5463; E skip ALL london -1824; E press ALL london -539; K hold P7 rth +45; K hold P7 asia -1738; K hold P7 london -1101; K hold K7 rth +137; K hold K7 asia -116; K hold K7 london -113; K hold ALL rth +677; K hold ALL asia -950; K hold ALL london -496

### screen3 JN05W2J (41 groups x ~3,000 cells; LEAD cells: 13)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F3_EMroom_SPX | le | 344.2 | 1835 | 3987 | 7304 | 9241 | 6412 | 4106 | 7826 | 7600 | 1 | 1.042e+05 | 0 | True |
| ALL | asia | F3_EMroom_NDX | le | 471.3 | 1786 | 3741 | 7318 | 8917 | 6172 | 3872 | 7544 | 7600 | 1 | 9.66e+04 | 0 | False |
| ALL | asia | F3_EMpos_NDX | ge | -0.2082 | 1835 | 2956 | 6706 | 8757 | 6098 | 3973 | 7427 | 7600 | 0.95 | 1.016e+05 | 0 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | london | F3_IV_SPY | ge | 0.145 | 464 | 4334 | 1460 | 2302 | 1021 | -788.3 | 1661 | 1612 | 1 | 1.035e+04 | 0 | True |
| ALL | london | F3_OI_SPX_cw | ge | -3300 | 298 | 1522 | -207.2 | 1270 | 1480 | 256.4 | 1375 | 1612 | 1 | -1867 | 0 | False |
| ALL | london | F3_OI_SPX_cw | ge | -2809 | 264 | 591.3 | -326.8 | 1210 | 1181 | 437.6 | 1195 | 1612 | 1 | 8275 | 0 | False |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F3_IVrank_SPY | le | 18.23 | 332 | -1776 | 725.9 | 2055 | 2011 | -680 | 2033 | 2678 | 0.85 | 5.07e+04 | 0 | False |
| ALL | asia | F3_IVrank_SPX | le | 21.49 | 325 | 200.5 | 1464 | 1478 | 1733 | -594.4 | 1605 | 2678 | 0.7 | 5.646e+04 | 0 | False |
| ALL | asia | F3_IV_NDX | le | 0.194 | 199 | -1712 | 1984 | 1716 | 1447 | -364.8 | 1582 | 2678 | 0.9 | 2.84e+04 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth -318; E press P7 rth -32; E skip P7 asia -275; E press P7 asia +2277; E skip P7 london -350; E press P7 london +40; E skip K7 rth -713; E press K7 rth +123; E skip K7 asia -230; E press K7 asia +905; E skip K7 london -85; E press K7 london +79; E skip M7 rth -551; E press M7 rth +76; E skip M7 london -88; E press M7 london -435; E skip U7 asia -512; E press U7 asia +122; E skip U7 london -516; E press U7 london +63; E skip H7 rth +3; E press H7 rth +13; E skip H7 asia -131; E press H7 asia +474; E skip ALL rth -1153; E press ALL rth -34; E skip ALL late -107; E press ALL late +161; E skip ALL asia -1517; E press ALL asia +5107; E skip ALL london -123; E press ALL london -288; K hold P7 rth +154; K hold P7 asia -535; K hold P7 london -407; K hold K7 rth +135; K hold K7 asia +103; K hold K7 london -175; K hold ALL rth +1331; K hold ALL asia -515; K hold ALL london +504

### screen4 LPB_BASE (42 groups x ~3,000 cells; LEAD cells: 10)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F4_OIchg_SPX_tot | ge | 0.007584 | 1383 | 6465 | 7498 | 8606 | 6931 | 1749 | 7769 | 8018 | 1 | 1.052e+05 | 0 | False |
| ALL | asia | F4_OIchg_NDX_cp_s | le | 0.004731 | 1576 | 6962 | 7870 | 8682 | 6795 | 2437 | 7738 | 8018 | 1 | 9.882e+04 | 0 | False |
| ALL | asia | F4_OIchg_SPX_tot | ge | 0.006469 | 1526 | 6465 | 6710 | 8309 | 7072 | 2732 | 7690 | 8018 | 1 | 1.032e+05 | 0 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | london | F4_OIchg_NDX_cp | ge | 0.003773 | 262 | 4267 | 2076 | 3030 | 1824 | 756 | 2427 | 2260 | 1 | 5186 | 0 | True |
| ALL | rth | F4_OIchg_SPX_cp | ge | -0.00256 | 841 | 3701 | 4980 | 2441 | 1953 | -1083 | 2197 | 2087 | 1 | 4771 | 0 | True |
| ALL | rth | F4_OIchg_SPX_cp | ge | -0.002128 | 746 | 3901 | 4158 | 2090 | 2292 | -695.4 | 2191 | 2087 | 1 | -464.6 | 0 | True |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | rth | F4_OIchg_SPX_tot | ge | 0.007379 | 339 | -4028 | -1107 | 2202 | 1901 | 522.7 | 2052 | 2505 | 0.9 | 1.586e+04 | 1 | False |
| ALL | rth | F4_OIchg_NDX_tot | ge | 0.006311 | 401 | -3173 | -1334 | 2023 | 2006 | 131.4 | 2014 | 2505 | 1 | 1.575e+04 | 0 | False |
| ALL | rth | F4_OIchg_NDX_tot | ge | 0.008396 | 337 | -1622 | -839.1 | 2123 | 1694 | 30.19 | 1909 | 2505 | 0.95 | 1.897e+04 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth +265; E press P7 rth -134; E skip P7 asia -2065; E press P7 asia +2763; E skip P7 london -1103; E press P7 london +376; E skip K7 rth -295; E press K7 rth +13; E skip K7 asia -248; E press K7 asia +952; E skip K7 london -446; E press K7 london -34; E skip M7 rth -329; E press M7 rth +35; E skip M7 london -107; E press M7 london -185; E skip U7 asia -657; E press U7 asia +576; E skip U7 london -288; E press U7 london +156; E skip H7 rth -8; E press H7 rth +96; E skip H7 asia -123; E press H7 asia +338; E skip ALL rth -1362; E press ALL rth -485; E skip ALL late +1; E press ALL late -59; E skip ALL asia -1861; E press ALL asia +5070; E skip ALL london -436; E press ALL london +709; K hold P7 rth +1165; K hold P7 asia -1539; K hold P7 london -540; K hold K7 rth +44; K hold K7 asia +96; K hold K7 london +159; K hold ALL rth +1751; K hold ALL late -5; K hold ALL asia -1185; K hold ALL london -493

### screen4 JN05W2 (41 groups x ~3,000 cells; LEAD cells: 0)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F4_OIchg_NDX_cp_s | le | 0.004731 | 1615 | 7552 | 7797 | 1.029e+04 | 7279 | 2520 | 8783 | 9071 | 0.95 | 1.048e+05 | 0 | False |
| ALL | asia | F4_OIchg_NDX_cp | le | 0.008744 | 1837 | 4877 | 6992 | 9765 | 7303 | 4492 | 8534 | 9071 | 0.8 | 1.077e+05 | 1 | False |
| ALL | asia | F4_OIchg_SPX_tot | ge | 0 | 1905 | 4877 | 6903 | 9820 | 7198 | 4637 | 8509 | 9071 | 0.6 | 1.18e+05 | 1 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | london | F4_DPshare_mega | ge | 0.5282 | 396 | -4460 | 730.1 | 1088 | 1476 | 0 | 1282 | 2026 | 0.85 | 1.332e+04 | 1 | False |
| ALL | london | F4_OIchg_NDX_cp_s | ge | 0.00968 | 153 | 2361 | 3356 | 1402 | 1074 | 57.26 | 1238 | 2026 | 1 | -392.5 | 0 | False |
| ALL | london | F4_OIchg_NDX_cp | ge | 0.003401 | 245 | 2549 | 953.5 | 1169 | 1224 | 129.2 | 1197 | 2026 | 0.85 | 2.236e+04 | 0 | False |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F4_OIchg_SPX_cp_s | le | 0.001327 | 432 | -9449 | 2223 | 2593 | 1761 | -993.4 | 2177 | 3733 | 1 | 1.235e+04 | 0 | False |
| P7 | asia | F4_OIchg_SPX_cp_s | le | 8e-05 | 143 | -2006 | 4199 | 2512 | 1323 | -2128 | 1917 | 3312 | 1 | -5131 | 0 | False |
| P7 | asia | F4_DPtop_SPY | le | 0.4348 | 194 | -6042 | 3290 | 2901 | 738.9 | 0 | 1820 | 3312 | 1 | -2338 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth +91; E press P7 rth +13; E skip P7 asia -1536; E press P7 asia +3281; E skip P7 london -559; E press P7 london +187; E skip K7 rth -71; E press K7 rth +164; E skip K7 asia -413; E press K7 asia +923; E skip K7 london -370; E press K7 london +185; E skip M7 rth -312; E press M7 rth +21; E skip M7 london -42; E press M7 london -142; E skip U7 asia -648; E press U7 asia +578; E skip U7 london -378; E press U7 london +2; E skip H7 rth +55; E press H7 rth +37; E skip H7 asia -354; E press H7 asia +299; E skip ALL rth -1091; E press ALL rth +51; E skip ALL late -165; E press ALL late +2; E skip ALL asia -2081; E press ALL asia +5617; E skip ALL london +540; E press ALL london +1220; K hold P7 rth +318; K hold P7 asia -765; K hold P7 london -1111; K hold K7 rth +147; K hold K7 asia +122; K hold K7 london -49; K hold ALL rth +876; K hold ALL asia -1352; K hold ALL london +439

### screen4 JN05W2J (41 groups x ~3,000 cells; LEAD cells: 1)

**E press**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F4_OIchg_SPX_cp | le | 0.000333 | 1912 | 2910 | 7241 | 8614 | 6239 | 3769 | 7427 | 7653 | 0.7 | 9.152e+04 | 0 | False |
| ALL | asia | F4_OIchg_SPX_tot | ge | 0.006469 | 1594 | 5015 | 6838 | 8459 | 6273 | 1847 | 7366 | 7653 | 0.95 | 8.396e+04 | 0 | False |
| ALL | asia | F4_OIchg_SPX_tot | ge | 0 | 1946 | 2910 | 6853 | 8561 | 6116 | 3558 | 7338 | 7653 | 0.7 | 9.522e+04 | 0 | False |

**E skip**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | london | F4_OIchg_SPX_ccw | le | 1244 | 214 | 4508 | 1545 | 1752 | 1374 | 319.1 | 1563 | 1787 | 1 | 2252 | 1 | False |
| ALL | london | F4_OIchg_SPX_ccw | le | 0 | 161 | 2626 | 298.5 | 1326 | 1291 | 157.2 | 1309 | 1787 | 1 | 1.225e+04 | 1 | False |
| ALL | london | F4_OIchg_SPX_ccw | le | 3217 | 299 | 2488 | -41.01 | 1410 | 983.9 | 413.4 | 1197 | 1787 | 1 | 2266 | 0 | False |

**K hold**

| book | scope | feat | dir | th | n_L6M | L1M | L3M | L6M | HOLD | PREUW | recents | null_q95 | plc_rank | tw_best5 | win_turned_losing | LEAD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | asia | F4_OIchg_SPX_cp_s | le | 0.001329 | 460 | -470.3 | 3290 | 3412 | 1948 | -573.3 | 2680 | 2553 | 1 | 4.591e+04 | 0 | True |
| ALL | asia | F4_OIchg_SPX_cp_s | le | 0.001684 | 512 | -1620 | 2890 | 2357 | 1441 | -575.5 | 1899 | 2553 | 1 | 4.967e+04 | 0 | False |
| ALL | asia | F4_DPshare_mega_z | ge | -0.4238 | 446 | -268.8 | 604.2 | 1865 | 1551 | 0 | 1708 | 2553 | 1 | 4.835e+04 | 0 | False |

Bi-weekly walk-forward over ALL cells (trailing 26 wk pick, OOS $/wk since 2025-04): E skip P7 rth -214; E press P7 rth -123; E skip P7 asia -1693; E press P7 asia +2299; E skip P7 london -561; E press P7 london -102; E skip K7 rth -357; E press K7 rth +79; E skip K7 asia -601; E press K7 asia +847; E skip K7 london -100; E press K7 london +190; E skip M7 rth -635; E press M7 rth +39; E skip M7 london +285; E press M7 london -270; E skip U7 asia -365; E press U7 asia +594; E skip U7 london -485; E press U7 london -60; E skip H7 rth +11; E press H7 rth +69; E skip H7 asia -478; E press H7 asia +158; E skip ALL rth -1361; E press ALL rth +126; E skip ALL late -266; E press ALL late +151; E skip ALL asia -2304; E press ALL asia +4665; E skip ALL london +52; E press ALL london +309; K hold P7 rth +148; K hold P7 asia -942; K hold P7 london -280; K hold K7 rth +267; K hold K7 asia +106; K hold K7 london +229; K hold ALL rth +833; K hold ALL asia -338; K hold ALL london +701

## 3. By feature family and horizon (best recents across all groups/bases; shows where the signal sits)
| family | horizon | base | use act book scope | feat | dir th | recents | null q95 | margin | PREUW |
|---|---|---|---|---|---|---|---|---|---|
| W | LAST | screen2 JN05W2 | E skip ALL asia | W_LAST_NDX_c_oi_s | ge 3.594e+12 | 2632 | 1753 | +879 | -397 |
| W | R10 | screen3 LPB_BASE | E skip ALL rth | W_R10_SPY_g_dir | ge 4.926e+08 | 2411 | 2030 | +381 | 132 |
| F3 | level | screen3 LPB_BASE | E skip K7 rth | F3_EMabs_SPX | le 1.132 | 1404 | 1085 | +319 | 171 |
| F4 | level | screen4 LPB_BASE | E skip ALL london | F4_OIchg_NDX_cp | ge 0.003773 | 2427 | 2260 | +167 | 756 |
| B | level | screen2 LPB_BASE | E press ALL rth | B_NDX_vol_behind | ge 349 | 1271 | 1234 | +37 | -289 |
| C | level | screen2 LPB_BASE | E press K7 rth | C_net_s | ge 2.307e+08 | 819 | 799 | +20 | -10 |
| D | level | screen2 LPB_BASE | K hold ALL rth | D_NDX_v_oi | le 1.388e+08 | 2949 | 2955 | -6 | 1019 |
| A | d15 | screen2 JN05W2 | E press ALL rth | A_QQQ_g_dir_d15 | le 2.541e+08 | 1716 | 1737 | -22 | 663 |
| W | d15 | screen2 JN05W2 | E press ALL rth | W_QQQ_g_dir_d15 | le 2.541e+08 | 1716 | 1737 | -22 | 663 |
| W | d5 | screen2 JN05W2J | E press M7 rth | W_NDX_g_dir_d5 | le 0 | 516 | 558 | -42 | 222 |
| W | d1 | screen2 LPB_BASE | E press ALL late | W_QQQ_c_vol_d1 | le -1.827e+11 | 293 | 343 | -50 | 108 |
| W | d60 | screen2 JN05W2 | E press ALL late | W_NDX_g_dir_d60 | ge 0 | 224 | 288 | -63 | -153 |
| A | level | screen2 JN05W2J | E press ALL late | A_NDX_g_vol | le 2.068e+10 | 290 | 362 | -73 | -153 |
| W | level | screen2 LPB_BASE | E press H7 rth | W_TD_z15 | ge 0.1376 | 290 | 371 | -81 | 311 |

Tickers: SPX/SPY/QQQ/NDX appear inside feature names (A_<TK>_*, D_<TK>_*, W_<TK>_*, W_LAST_<TK>_*); B levels are SPX and NDX only (daily, prior day); C Tide is market-wide. Full per-cell tables: /mnt/l2/l2vast/_uw_score/screen2_<SET>.csv (top-8 cells per group).

## 4. Reading of the evidence
- RTH signals (first read) are chance-level against the family null. The strongest, repeated structure is the PRIOR-CLOSE prior for off-hours books: skip Asia entries when side x NDX charm(oi) at the prior close >= 3.59e12 (same feature and threshold on JN05W2 and JN05W2J; also SPX gamma_dir for LPB_BASE Asia and NDX gamma_dir for London cuts). It is a 2025-07+ pattern (PREUW negative), so recent-only, rule-2a candidate; exact sets TL3_UW_NDXCA_* test it.
- Placebo (forward-only shifted features) rank is not selection-adjusted; only the family null counts.
- NDXCA interaction check (first-order, trade lists JN05W2/JN05W2J/LPB_BASE; JN05W2 already contains C22/E1/F3/BR3S so interactions with them are inside the base): the Asia skip gain by book (HOLD $/wk, JN05W2): P7 +1,234, K7 +448, A7 +305, U7 -230, H7 +7, M7/O7 no Asia trades; PREUW ~0 for P7/K7. By month (HOLD, $): Jun 0, Jul +15.6k, Aug -6.6k, Sep +22.3k, Oct +60.7k: about 60% of the total is October 2026, one regime month; StateCut exits carry the effect (+208k skipped losses) against -213k lost Target winners. So: Asia P7/K7 (not U7/H7), recent-only and concentrated: weak.
- learned timing model JN05W2J_ALL: JN05W2J ALL WF skip bottom-15% OOS $/wk -8616 (skipped 6465); placebo (shuffled pnl within month) mean -10557 max -6352
- learned timing model JN05W2J_P7: JN05W2J P7 WF skip bottom-15% OOS $/wk -2022 (skipped 996); placebo (shuffled pnl within month) mean -3223 max -1345
- learned timing model JN05W2_ALL: JN05W2 ALL WF skip bottom-15% OOS $/wk -12067 (skipped 7078); placebo (shuffled pnl within month) mean -12623 max -7786
- learned timing model JN05W2_P7: JN05W2 P7 WF skip bottom-15% OOS $/wk -3239 (skipped 683); placebo (shuffled pnl within month) mean -4282 max -2215
- learned timing model LPB_BASE_ALL: LPB_BASE ALL WF skip bottom-15% OOS $/wk -11900 (skipped 8512); placebo (shuffled pnl within month) mean -12492 max -9773
- learned timing model LPB_BASE_P7: LPB_BASE P7 WF skip bottom-15% OOS $/wk -3089 (skipped 1079); placebo (shuffled pnl within month) mean -2925 max 2043
- NDX SPOT CAVEAT (W-UR1, DS3_UWREGIME.md): UW NDX spot is frozen/stale on ~67 days (not ~15). Screens 1-3 (built before this note) used the NDX spot unfiltered for B_NDX_* / F3_OI_NDX level distances (SPX levels, Tide, gamma/charm/vanna exposure series, EM from NQ price are unaffected; the NQ/NDX ratio is a 5-day median and robust). uw_tf.py now drops NDX spot rows >0.4% off the NQ-implied price; B_NDX_* cells would need a re-screen (CANCELLED by the 3-part order) and any NDX-level cell in this page is provisional. Cells that rank on NDX levels: LPB_BASE E press ALL B_NDX_vol_behind.
- CLOSING NOTE (user order DIRECTIVE_UW_3PART_20261113): dealer-exposure direction screens (gamma/vanna/charm/regime as skip/press/entry direction) are CLOSED: no cell cleared the family null convincingly (best exact: TL3_UW_QQQGD15_PR, weak); no further dealer-direction screens or learned-model runs. Only the already-running screen3 and admitted exact sets finish; the page loop stays alive. Non-dealer UW features not yet covered: dark pool levels (pulled), per-strike OI changes, per-strike flow: to run behind the W-FA/W-MF/W-RU/W-CAL front.

## 5. Exact stage (TP engine; score_nf vs JN05W2 / JN05W2J; windows present only)

TL3J_UW_KLDN_HOLD vs JN05W2J
                cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3J_UW_KLDN_HOLD    L1M  0.0         0.0      -82.8  17861.9  17861.9    2548.0     14.0      6.5         14.0          6.5         57             57       6   244437.1    249036.0                0         21
1  TL3J_UW_KLDN_HOLD    L3M  0.0       173.9      799.8  17861.9  17861.9   15741.4     14.0      6.0         14.0          6.0        168            172       6   244437.1    249036.0                0         21
2  TL3J_UW_KLDN_HOLD    L6M -4.4       454.9      757.0  25013.7  23965.2   21621.9     14.0      6.0         14.0          6.0        349            363       6   244437.1    249036.0                0         21
trend {'best5_ref': 244437.14000000796, 'best5_cell': 249035.96000000698, 'win_turn_losing': 0, 'win_weeks': 21}


TL3J_UW_NDXCA_SK vs JN05W2J
               cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3J_UW_NDXCA_SK    L1M  46.4      2437.5     5107.1   9577.1  17861.9    7737.9      9.0      6.8         14.0          6.5         60             57       6   244437.1    257775.2                1         21
1  TL3J_UW_NDXCA_SK    L3M -10.0       554.2     1787.9  19648.8  17861.9   16729.5     10.0      6.0         14.0          6.0        165            172       6   244437.1    257775.2                1         21
2  TL3J_UW_NDXCA_SK    L6M   0.0       961.0     -245.5  23965.2  23965.2   20619.4     10.0      6.0         14.0          6.0        352            363       6   244437.1    257775.2                1         21
trend {'best5_ref': 244437.14000000796, 'best5_cell': 257775.22000000748, 'win_turn_losing': 1, 'win_weeks': 21}


TL3J_UW_SPXVDIR_PR vs JN05W2J
                 cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3J_UW_SPXVDIR_PR    L1M   5.2       307.9     1657.4  16938.1  17861.9    4288.2     14.0      6.6         14.0          6.5         56             57      12   244437.1    252234.4                0         21
1  TL3J_UW_SPXVDIR_PR    L3M   1.2      -476.7      406.3  17642.5  17861.9   15348.0     14.0      6.0         14.0          6.0        169            172      12   244437.1    252234.4                0         21
2  TL3J_UW_SPXVDIR_PR    L6M  -1.5        87.5      507.4  24331.9  23965.2   21372.2     14.0      6.0         14.0          6.0        359            363      12   244437.1    252234.4                0         21
3  TL3J_UW_SPXVDIR_PR   HOLD -16.2       592.9      362.3  50677.1  43622.0   14767.6     14.0      6.0         14.0          6.0        648            656      12   244437.1    252234.4                0         21
trend {'best5_ref': 244437.14000000796, 'best5_cell': 252234.36000000814, 'win_turn_losing': 0, 'win_weeks': 21}


TL3_UW_FA1 vs JN05W2
         cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA1    L1M  0.0         0.0      128.2  36370.5  36370.5     734.5     13.0      6.0         13.0          6.0         50             50      21   316288.0    314575.9                0         20
1  TL3_UW_FA1    L3M  0.0        49.7      140.7  36370.5  36370.5   16155.9     13.0      6.0         13.0          6.0        160            161      21   316288.0    314575.9                0         20
2  TL3_UW_FA1    L6M  0.0        22.3      377.3  36370.5  36370.5   25514.2     13.0      6.0         13.0          6.0        348            350      21   316288.0    314575.9                0         20
3  TL3_UW_FA1   HOLD  0.0        57.2      234.1  63185.1  63185.1   17723.4     13.0      6.0         13.0          6.0        628            631      21   316288.0    314575.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 314575.9000000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA1P11 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA1P11    L1M  0.0         0.0        0.0  36370.5  36370.5     606.3     13.0      6.0         13.0          6.0         50             50      12   316288.0    317261.2                0         20
1  TL3_UW_FA1P11    L3M  0.0        69.8      -27.3  36370.5  36370.5   15987.9     13.0      6.0         13.0          6.0        160            161      12   316288.0    317261.2                0         20
2  TL3_UW_FA1P11    L6M  0.0        48.7      209.3  36370.5  36370.5   25346.2     13.0      6.0         13.0          6.0        349            350      12   316288.0    317261.2                0         20
3  TL3_UW_FA1P11   HOLD  0.0        20.2      101.0  63185.1  63185.1   17590.4     13.0      6.0         13.0          6.0        629            631      12   316288.0    317261.2                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317261.1800000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA1P23 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA1P23    L1M  6.9         0.0      631.9  33842.9  36370.5    1238.2     13.0      6.0         13.0          6.0         50             50      12   316288.0    313933.3                0         20
1  TL3_UW_FA1P23    L3M  6.9       -87.1      114.1  33842.9  36370.5   16129.3     13.0      6.0         13.0          6.0        161            161      12   316288.0    313933.3                0         20
2  TL3_UW_FA1P23    L6M  6.9      -166.6      -62.9  33842.9  36370.5   25074.0     13.0      6.0         13.0          6.0        350            350      12   316288.0    313933.3                0         20
3  TL3_UW_FA1P23   HOLD  0.0       -96.2      -40.5  63185.1  63185.1   17448.9     13.0      6.0         13.0          6.0        632            631      12   316288.0    313933.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 313933.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA1P37 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA1P37    L1M  0.0         0.0        0.0  36370.5  36370.5     606.3     13.0      6.0         13.0          6.0         50             50      12   316288.0    315893.3                0         20
1  TL3_UW_FA1P37    L3M  0.0        -5.1     -187.4  36370.5  36370.5   15827.8     13.0      6.0         13.0          6.0        161            161      12   316288.0    315893.3                0         20
2  TL3_UW_FA1P37    L6M  0.0       -45.4     -135.0  36370.5  36370.5   25001.9     13.0      6.0         13.0          6.0        350            350      12   316288.0    315893.3                0         20
3  TL3_UW_FA1P37   HOLD  0.0        71.4      173.6  63185.1  63185.1   17662.9     13.0      6.0         13.0          6.0        631            631      12   316288.0    315893.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 315893.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA2 vs JN05W2
         cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA2    L1M  2.5       822.4     1343.7  35467.9  36370.5    1950.0     13.0      6.0         13.0          6.0         51             50      21   316288.0    313938.3                0         20
1  TL3_UW_FA2    L3M  2.5       171.2     -118.6  35467.9  36370.5   15896.6     13.0      6.0         13.0          6.0        163            161      21   316288.0    313938.3                0         20
2  TL3_UW_FA2    L6M  2.5       101.8      -40.4  35467.9  36370.5   25096.4     13.0      6.0         13.0          6.0        354            350      21   316288.0    313938.3                0         20
3  TL3_UW_FA2   HOLD -6.9       -39.7       62.3  67561.6  63185.1   17551.6     13.0      6.0         13.0          6.0        636            631      21   316288.0    313938.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 313938.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA2P11 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA2P11    L1M   2.5      1270.1     1736.0  35467.9  36370.5    2342.3     13.0      6.0         13.0          6.0         49             50      12   316288.0    310629.5                0         20
1  TL3_UW_FA2P11    L3M   2.5       678.1      224.6  35467.9  36370.5   16239.7     13.0      6.0         13.0          6.0        160            161      12   316288.0    310629.5                0         20
2  TL3_UW_FA2P11    L6M   2.5        76.3     -127.3  35467.9  36370.5   25009.6     13.0      6.0         13.0          6.0        349            350      12   316288.0    310629.5                0         20
3  TL3_UW_FA2P11   HOLD -11.0      -115.1     -223.6  70128.0  63185.1   17265.7     13.0      6.0         13.0          6.0        632            631      12   316288.0    310629.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 310629.4800000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA2P23 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA2P23    L1M  2.5      -130.1      128.1  35467.9  36370.5     734.4     13.0      6.0         13.0          6.0         50             50      12   316288.0    316384.4                0         20
1  TL3_UW_FA2P23    L3M  2.5        -4.9       66.1  35467.9  36370.5   16081.3     13.0      6.0         13.0          6.0        161            161      12   316288.0    316384.4                0         20
2  TL3_UW_FA2P23    L6M  2.5        20.7      -25.8  35467.9  36370.5   25111.1     13.0      6.0         13.0          6.0        351            350      12   316288.0    316384.4                0         20
3  TL3_UW_FA2P23   HOLD  0.0       197.6      -41.1  63185.1  63185.1   17448.3     13.0      6.0         13.0          6.0        631            631      12   316288.0    316384.4                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 316384.44000000966, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA2P37 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA2P37    L1M  0.0         0.0        0.0  36370.5  36370.5     606.3     13.0      6.0         13.0          6.0         50             50      12   316288.0    317563.3                0         20
1  TL3_UW_FA2P37    L3M  0.0       -15.9       35.9  36370.5  36370.5   16051.1     13.0      6.0         13.0          6.0        161            161      12   316288.0    317563.3                0         20
2  TL3_UW_FA2P37    L6M  0.0        26.2      -66.0  36370.5  36370.5   25070.9     13.0      6.0         13.0          6.0        351            350      12   316288.0    317563.3                0         20
3  TL3_UW_FA2P37   HOLD  1.0      -120.1       16.7  62562.5  63185.1   17506.0     13.0      6.0         13.0          6.0        632            631      12   316288.0    317563.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317563.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA3 vs JN05W2
         cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA3    L1M  7.0     -1326.1     -355.3  33813.4  36370.5     251.0     13.0      6.0         13.0          6.0         52             50      21   316288.0    317759.7                0         20
1  TL3_UW_FA3    L3M  7.0       547.5      702.0  33813.4  36370.5   16717.2     13.0      6.0         13.0          6.0        164            161      21   316288.0    317759.7                0         20
2  TL3_UW_FA3    L6M  7.0       567.7      408.8  33813.4  36370.5   25545.7     13.0      6.0         13.0          6.0        353            350      21   316288.0    317759.7                0         20
3  TL3_UW_FA3   HOLD  3.4       381.3      500.3  61019.9  63185.1   17989.7     13.0      6.0         13.0          6.0        635            631      21   316288.0    317759.7                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317759.7200000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA3P11 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA3P11    L1M  19.5      -951.4     1064.0  29260.5  36370.5    1670.3     13.0      6.0         13.0          6.0         52             50      12   316288.0    319636.8                0         20
1  TL3_UW_FA3P11    L3M  14.2      -366.5      208.6  31201.1  36370.5   16223.8     13.0      6.0         13.0          6.0        165            161      12   316288.0    319636.8                0         20
2  TL3_UW_FA3P11    L6M  14.2       135.5      403.7  31201.1  36370.5   25540.6     13.0      6.0         13.0          6.0        353            350      12   316288.0    319636.8                0         20
3  TL3_UW_FA3P11   HOLD   0.0       103.1      237.8  63185.1  63185.1   17727.2     13.0      6.0         13.0          6.0        635            631      12   316288.0    319636.8                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 319636.8200000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA3P23 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA3P23    L1M  2.5       270.5     -686.3  35471.7  36370.5     -80.0     13.0      6.0         13.0          6.0         51             50      12   316288.0    318627.1                0         20
1  TL3_UW_FA3P23    L3M  2.5       244.4      -48.0  35471.7  36370.5   15967.2     13.0      6.0         13.0          6.0        162            161      12   316288.0    318627.1                0         20
2  TL3_UW_FA3P23    L6M  2.5       413.2      260.5  35471.7  36370.5   25397.4     13.0      6.0         13.0          6.0        351            350      12   316288.0    318627.1                0         20
3  TL3_UW_FA3P23   HOLD -0.0       146.8       75.6  63185.1  63185.1   17564.9     13.0      6.0         13.0          6.0        632            631      12   316288.0    318627.1                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 318627.0800000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA3P37 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA3P37    L1M  0.0        57.9      268.2  36370.5  36370.5     874.5     13.0      6.0         13.0          6.0         50             50      12   316288.0    317560.0                0         20
1  TL3_UW_FA3P37    L3M  0.0        71.8      135.4  36370.5  36370.5   16150.6     13.0      6.0         13.0          6.0        161            161      12   316288.0    317560.0                0         20
2  TL3_UW_FA3P37    L6M  0.0        49.9      156.7  36370.5  36370.5   25293.6     13.0      6.0         13.0          6.0        348            350      12   316288.0    317560.0                0         20
3  TL3_UW_FA3P37   HOLD  0.0       157.2      208.5  63185.1  63185.1   17697.9     13.0      6.0         13.0          6.0        632            631      12   316288.0    317560.0                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317560.00000000966, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA4 vs JN05W2
         cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA4    L1M  2.8       336.3      506.9  35361.7  36370.5    1113.2     13.0      6.0         13.0          6.0         50             50      21   316288.0    317156.8                0         20
1  TL3_UW_FA4    L3M  2.8       278.2      371.6  35361.7  36370.5   16386.8     13.0      6.0         13.0          6.0        161            161      21   316288.0    317156.8                0         20
2  TL3_UW_FA4    L6M  2.8       238.9      348.9  35361.7  36370.5   25485.8     13.0      6.0         13.0          6.0        350            350      21   316288.0    317156.8                0         20
3  TL3_UW_FA4   HOLD  3.3       274.8      329.1  61123.6  63185.1   17818.4     13.0      6.0         13.0          6.0        631            631      21   316288.0    317156.8                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317156.8000000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA4P11 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA4P11    L1M  7.9         0.0      721.1  33486.0  36370.5    1327.4     13.0      6.0         13.0          6.0         50             50      12   316288.0    315693.3                0         20
1  TL3_UW_FA4P11    L3M  7.9        11.6      232.6  33486.0  36370.5   16247.8     13.0      6.0         13.0          6.0        161            161      12   316288.0    315693.3                0         20
2  TL3_UW_FA4P11    L6M  7.9       -83.0       31.2  33486.0  36370.5   25168.1     13.0      6.0         13.0          6.0        350            350      12   316288.0    315693.3                0         20
3  TL3_UW_FA4P11   HOLD -0.2       -75.8      -18.8  63291.3  63185.1   17470.5     13.0      6.0         13.0          6.0        631            631      12   316288.0    315693.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 315693.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA4P23 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA4P23    L1M  0.0         0.0        0.0  36370.5  36370.5     606.3     13.0      6.0         13.0          6.0         50             50      12   316288.0    313690.6                0         20
1  TL3_UW_FA4P23    L3M  0.0        -5.5      -74.8  36370.5  36370.5   15940.4     13.0      6.0         13.0          6.0        161            161      12   316288.0    313690.6                0         20
2  TL3_UW_FA4P23    L6M  0.0       -57.1     -109.6  36370.5  36370.5   25027.3     13.0      6.0         13.0          6.0        350            350      12   316288.0    313690.6                0         20
3  TL3_UW_FA4P23   HOLD -0.0       138.1      169.3  63185.1  63185.1   17658.6     13.0      6.0         13.0          6.0        631            631      12   316288.0    313690.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 313690.62000000966, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA4P37 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA4P37    L1M  2.8         0.0      252.2  35361.7  36370.5     858.5     13.0      6.0         13.0          6.0         50             50      12   316288.0    315763.3                0         20
1  TL3_UW_FA4P37    L3M  2.8         3.9       81.2  35361.7  36370.5   16096.4     13.0      6.0         13.0          6.0        161            161      12   316288.0    315763.3                0         20
2  TL3_UW_FA4P37    L6M  2.8       216.3      120.6  35361.7  36370.5   25257.5     13.0      6.0         13.0          6.0        349            350      12   316288.0    315763.3                0         20
3  TL3_UW_FA4P37   HOLD  1.9       210.1      162.3  61981.3  63185.1   17651.7     13.0      6.0         13.0          6.0        630            631      12   316288.0    315763.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 315763.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA5 vs JN05W2
         cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA5    L1M  5.7       269.9      772.9  34284.4  36370.5    1379.2     13.0      6.0         13.0          6.0         51             50      21   316288.0    310441.2                0         20
1  TL3_UW_FA5    L3M  5.6        24.5     -558.2  34339.6  36370.5   15457.0     13.0      6.0         13.0          6.0        164            161      21   316288.0    310441.2                0         20
2  TL3_UW_FA5    L6M  5.6       337.7       34.3  34339.6  36370.5   25171.2     13.0      6.0         13.0          6.0        353            350      21   316288.0    310441.2                0         20
3  TL3_UW_FA5   HOLD -5.5      -135.2     -294.7  66640.1  63185.1   17194.7     13.0      6.0         13.0          6.0        635            631      21   316288.0    310441.2                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 310441.18000000966, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FA6 vs JN05W2
         cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FA6    L1M  2.8        47.5      309.1  35336.7  36370.5     915.4     13.0      6.0         13.0          6.0         50             50      21   316288.0    320033.3                0         20
1  TL3_UW_FA6    L3M  2.8        41.4      122.4  35336.7  36370.5   16137.5     13.0      6.0         13.0          6.0        161            161      21   316288.0    320033.3                0         20
2  TL3_UW_FA6    L6M  2.8        53.3      196.9  35336.7  36370.5   25333.8     13.0      6.0         13.0          6.0        350            350      21   316288.0    320033.3                0         20
3  TL3_UW_FA6   HOLD  0.7       -23.3       50.0  62717.5  63185.1   17539.4     13.0      6.0         13.0          6.0        634            631      21   316288.0    320033.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 320033.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FF1 vs JN05W2
         cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF1    L1M  28.7      1734.0     3912.5  25922.6  36370.5    4518.8     13.0      6.0         13.0          6.0         50             50      21   316288.0    290963.9                0         20
1  TL3_UW_FF1    L3M  28.7      1244.5     3003.3  25922.6  36370.5   19018.5     13.0      6.0         13.0          6.0        160            161      21   316288.0    290963.9                0         20
2  TL3_UW_FF1    L6M  28.7      3452.4     2327.1  25922.6  36370.5   27464.0     13.0      6.0         13.0          6.0        344            350      21   316288.0    290963.9                0         20
3  TL3_UW_FF1   HOLD  -1.2      2260.4     1720.6  63913.9  63185.1   19209.9     13.0      6.0         13.0          6.0        618            631      21   316288.0    290963.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 290963.94000000955, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FF1P11 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF1P11    L1M  0.0       519.6    -7325.3  36370.5  36370.5   -6719.0     13.0      6.0         13.0          6.0         47             50      12   316288.0    316191.0                1         20
1  TL3_UW_FF1P11    L3M  0.0      -164.2    -2525.4  36370.5  36370.5   13489.8     13.0      6.0         13.0          6.0        157            161      12   316288.0    316191.0                1         20
2  TL3_UW_FF1P11    L6M  0.0      -549.9    -1715.7  36370.5  36370.5   23421.2     13.0      6.0         13.0          6.0        342            350      12   316288.0    316191.0                1         20
3  TL3_UW_FF1P11   HOLD  0.0       126.4     -688.6  63185.1  63185.1   16800.7     13.0      6.0         13.0          6.0        614            631      12   316288.0    316191.0                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 316191.0200000097, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_FF1P23 vs JN05W2
            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF1P23    L1M  0.0         0.0    -4161.1  36370.5  36370.5   -3554.8     13.0      6.0         13.0          6.0         47             50      12   316288.0    314338.6                0         20
1  TL3_UW_FF1P23    L3M  0.0      -369.7    -1621.6  36370.5  36370.5   14393.6     13.0      6.0         13.0          6.0        155            161      12   316288.0    314338.6                0         20
2  TL3_UW_FF1P23    L6M  0.0       240.6     -408.8  36370.5  36370.5   24728.1     13.0      6.0         13.0          6.0        342            350      12   316288.0    314338.6                0         20
3  TL3_UW_FF1P23   HOLD  0.0      -553.2      -67.8  63185.1  63185.1   17421.5     13.0      6.0         13.0          6.0        617            631      12   316288.0    314338.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 314338.6200000094, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FF1P37 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF1P37    L1M  54.1     -2966.9     2689.9  16710.3  36370.5    3296.2     13.0      6.0         13.0          6.0         49             50      12   316288.0    292821.7                0         20
1  TL3_UW_FF1P37    L3M -15.2      -841.2      735.9  41903.2  36370.5   16751.1     13.0      6.0         13.0          6.0        158            161      12   316288.0    292821.7                0         20
2  TL3_UW_FF1P37    L6M -15.2      -611.7    -2156.9  41903.2  36370.5   22980.0     13.0      6.0         13.0          6.0        342            350      12   316288.0    292821.7                0         20
3  TL3_UW_FF1P37   HOLD -16.6      -173.1     -954.1  73665.4  63185.1   16535.2     13.0      6.0         13.0          6.0        618            631      12   316288.0    292821.7                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 292821.7400000092, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FF2 vs JN05W2
         cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF2    L1M  61.8      1641.5     6853.5  13881.0  36370.5    7459.8     15.0      6.0         13.0          6.0         56             50      12   316288.0    301373.6                2         20
1  TL3_UW_FF2    L3M  16.0      1872.5    -1549.0  30557.6  36370.5   14466.2     15.0      6.0         13.0          6.0        164            161      12   316288.0    301373.6                2         20
2  TL3_UW_FF2    L6M   8.7       115.9    -1527.3  33202.2  36370.5   23609.6     15.0      6.0         13.0          6.0        343            350      12   316288.0    301373.6                2         20
3  TL3_UW_FF2   HOLD  24.6      -178.4    -1071.5  47639.8  63185.1   16417.8     15.0      6.0         13.0          6.0        612            631      12   316288.0    301373.6                2         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 301373.5800000085, 'win_turn_losing': 2, 'win_weeks': 20}


TL3_UW_FF2P11 vs JN05W2
            cell window    cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF2P11    L1M -147.1     -5168.2   -22736.7  89873.4  36370.5  -22130.4     13.0      7.0         13.0          6.0         55             50      12   316288.0    282348.4                3         20
1  TL3_UW_FF2P11    L3M -147.1     -8328.0   -13490.6  89873.4  36370.5    2524.6     13.0      6.0         13.0          6.0        160            161      12   316288.0    282348.4                3         20
2  TL3_UW_FF2P11    L6M -147.1     -8207.4   -10793.4  89873.4  36370.5   14343.5     13.0      6.0         13.0          6.0        333            350      12   316288.0    282348.4                3         20
3  TL3_UW_FF2P11   HOLD  -42.2     -6977.0    -8293.7  89873.4  63185.1    9195.6     13.0      6.0         13.0          6.0        613            631      12   316288.0    282348.4                3         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 282348.3600000081, 'win_turn_losing': 3, 'win_weeks': 20}


TL3_UW_FF2P23 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF2P23    L1M   1.5       817.1    -3278.3  35828.5  36370.5   -2672.0     15.0      6.0         13.0          6.0         49             50      12   316288.0    235241.2                2         20
1  TL3_UW_FF2P23    L3M -38.3     -4513.4    -6219.7  50286.4  36370.5    9795.5     15.0      6.0         13.0          6.0        158            161      12   316288.0    235241.2                2         20
2  TL3_UW_FF2P23    L6M -57.1     -8362.5    -9489.0  57120.4  36370.5   15647.9     15.0      6.0         13.0          6.0        326            350      12   316288.0    235241.2                2         20
3  TL3_UW_FF2P23   HOLD   9.6     -5671.1    -6327.9  57120.4  63185.1   11161.4     15.0      6.0         13.0          6.0        601            631      12   316288.0    235241.2                2         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 235241.2200000091, 'win_turn_losing': 2, 'win_weeks': 20}


TL3_UW_FF2P37 vs JN05W2
            cell window   cut  dmean_drop  dmean_all        dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF2P37    L1M   0.0         0.0      931.6   36370.5  36370.5    1537.9     13.0      6.0         13.0          6.0         49             50      12   316288.0    254230.4                5         20
1  TL3_UW_FF2P37    L3M -38.6     -4025.9    -6019.3   50409.0  36370.5    9995.9     13.0      6.0         13.0          6.0        149            161      12   316288.0    254230.4                5         20
2  TL3_UW_FF2P37    L6M -38.6     -8545.0   -10225.7   50409.0  36370.5   14911.2     13.0      6.0         13.0          6.0        314            350      12   316288.0    254230.4                5         20
3  TL3_UW_FF2P37   HOLD -91.1     -5693.0    -6588.2  120749.1  63185.1   10901.1     13.0      6.0         13.0          6.0        591            631      12   316288.0    254230.4                5         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 254230.38000000842, 'win_turn_losing': 5, 'win_weeks': 20}


TL3_UW_FF3 vs JN05W2
         cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF3    L1M  -2.6        -3.7     1887.0  37331.9  36370.5    2493.3     13.0      6.0         13.0          6.0         49             50      12   316288.0    327340.1                1         20
1  TL3_UW_FF3    L3M  -2.6      2209.2      406.1  37331.9  36370.5   16421.3     13.0      6.0         13.0          6.0        156            161      12   316288.0    327340.1                1         20
2  TL3_UW_FF3    L6M  -2.6       506.2     -386.7  37331.9  36370.5   24750.2     13.0      6.0         13.0          6.0        330            350      12   316288.0    327340.1                1         20
3  TL3_UW_FF3   HOLD -17.2      -423.6     -891.1  74026.7  63185.1   16598.3     13.0      6.0         13.0          6.0        603            631      12   316288.0    327340.1                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 327340.14000000875, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_FF3P11 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF3P11    L1M   7.9      2158.9     9194.8  33482.1  36370.5    9801.1     13.0      6.0         13.0          6.0         49             50      12   316288.0    308545.1                1         20
1  TL3_UW_FF3P11    L3M   7.9      -911.9     1489.3  33482.1  36370.5   17504.4     13.0      6.0         13.0          6.0        150            161      12   316288.0    308545.1                1         20
2  TL3_UW_FF3P11    L6M -26.1     -2485.4    -1224.3  45878.0  36370.5   23912.6     13.0      6.0         13.0          6.0        323            350      12   316288.0    308545.1                1         20
3  TL3_UW_FF3P11   HOLD -16.8     -1030.2     -427.6  73794.0  63185.1   17061.7     13.0      6.0         13.0          6.0        590            631      12   316288.0    308545.1                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 308545.0600000092, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_FF3P23 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF3P23    L1M -16.1     -1825.3    -4384.6  42216.6  36370.5   -3778.3     13.0      6.0         13.0          6.0         47             50      12   316288.0    330229.2                1         20
1  TL3_UW_FF3P23    L3M -16.1     -1027.9    -1876.7  42216.6  36370.5   14138.5     13.0      6.0         13.0          6.0        147            161      12   316288.0    330229.2                1         20
2  TL3_UW_FF3P23    L6M -16.1     -1365.2    -1847.5  42216.6  36370.5   23289.4     13.0      6.0         13.0          6.0        324            350      12   316288.0    330229.2                1         20
3  TL3_UW_FF3P23   HOLD  17.9     -1522.8    -1947.9  51905.0  63185.1   15541.5     13.0      6.0         13.0          6.0        595            631      12   316288.0    330229.2                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 330229.1800000088, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_FF3P37 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF3P37    L1M  -9.7     -1200.6      986.1  39886.5  36370.5    1592.4     13.0      6.0         13.0          6.0         51             50      12   316288.0    284510.9                0         20
1  TL3_UW_FF3P37    L3M  -9.7     -1149.1    -1865.6  39886.5  36370.5   14149.6     13.0      6.0         13.0          6.0        155            161      12   316288.0    284510.9                0         20
2  TL3_UW_FF3P37    L6M  -9.7      -768.8    -1416.6  39886.5  36370.5   23720.3     13.0      6.0         13.0          6.0        330            350      12   316288.0    284510.9                0         20
3  TL3_UW_FF3P37   HOLD -41.9      -383.9     -797.4  89636.5  63185.1   16691.9     13.0      6.0         13.0          6.0        598            631      12   316288.0    284510.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 284510.9000000092, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FF4 vs JN05W2
         cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF4    L1M  37.3      4523.0     -320.7  22801.4  36370.5     285.6     13.0      6.0         13.0          6.0         45             50      12   316288.0    318750.4                0         20
1  TL3_UW_FF4    L3M  25.0       553.3     -631.7  27294.8  36370.5   15383.5     13.0      6.0         13.0          6.0        151            161      12   316288.0    318750.4                0         20
2  TL3_UW_FF4    L6M  25.0      -596.9      191.1  27294.8  36370.5   25328.0     13.0      6.0         13.0          6.0        333            350      12   316288.0    318750.4                0         20
3  TL3_UW_FF4   HOLD   0.0      -463.9      124.0  63185.1  63185.1   17613.4     13.0      6.0         13.0          6.0        585            631      12   316288.0    318750.4                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 318750.3800000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FF4P11 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF4P11    L1M  26.6      3224.3    -1294.8  26697.7  36370.5    -688.5     13.0      6.0         13.0          6.0         49             50      12   316288.0    316288.0                0         20
1  TL3_UW_FF4P11    L3M  21.5     -1872.0    -3626.3  28539.8  36370.5   12388.9     13.0      6.0         13.0          6.0        157            161      12   316288.0    316288.0                0         20
2  TL3_UW_FF4P11    L6M  21.5     -1472.2    -2364.7  28539.8  36370.5   22772.2     13.0      6.0         13.0          6.0        338            350      12   316288.0    316288.0                0         20
3  TL3_UW_FF4P11   HOLD  12.3      -541.8    -1005.9  55436.0  63185.1   16483.4     13.0      6.0         13.0          6.0        599            631      12   316288.0    316288.0                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 316287.98000000964, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FF4P23 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF4P23    L1M -20.7      7055.7     -287.6  43887.3  36370.5     318.7     13.0      6.0         13.0          6.0         37             50      12   316288.0    297867.8                1         20
1  TL3_UW_FF4P23    L3M -20.7      1280.0     -535.2  43887.3  36370.5   15480.0     13.0      5.0         13.0          6.0        139            161      12   316288.0    297867.8                1         20
2  TL3_UW_FF4P23    L6M -20.7      -999.7    -1819.6  43887.3  36370.5   23317.3     13.0      6.0         13.0          6.0        313            350      12   316288.0    297867.8                1         20
3  TL3_UW_FF4P23   HOLD  12.7     -1021.3    -1616.7  55145.4  63185.1   15872.6     13.0      6.0         13.0          6.0        576            631      12   316288.0    297867.8                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 297867.78000000847, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_FF4P37 vs JN05W2
            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF4P37    L1M -24.7     -2996.6     1466.2  45360.4  36370.5    2072.5     13.0      6.0         13.0          6.0         42             50      12   316288.0    313107.6                0         20
1  TL3_UW_FF4P37    L3M -24.7     -3393.5    -1989.8  45360.4  36370.5   14025.4     13.0      6.0         13.0          6.0        146            161      12   316288.0    313107.6                0         20
2  TL3_UW_FF4P37    L6M -24.7     -2670.5    -3635.7  45360.4  36370.5   21501.2     13.0      6.0         13.0          6.0        323            350      12   316288.0    313107.6                0         20
3  TL3_UW_FF4P37   HOLD -15.3     -3047.0    -2098.6  72832.7  63185.1   15390.7     13.0      6.0         13.0          6.0        578            631      12   316288.0    313107.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 313107.60000000964, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FF5 vs JN05W2
         cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FF5    L1M  6.9      -352.6      358.4  33879.1  36370.5     964.7     13.0      6.0         13.0          6.0         52             50      12   316288.0    311204.7                0         20
1  TL3_UW_FF5    L3M  6.9       194.6      664.6  33879.1  36370.5   16679.8     13.0      6.0         13.0          6.0        163            161      12   316288.0    311204.7                0         20
2  TL3_UW_FF5    L6M  6.9       182.3      417.7  33879.1  36370.5   25554.6     13.0      6.0         13.0          6.0        352            350      12   316288.0    311204.7                0         20
3  TL3_UW_FF5   HOLD  0.0       298.0      495.5  63185.1  63185.1   17984.8     13.0      6.0         13.0          6.0        634            631      12   316288.0    311204.7                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 311204.7200000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FN11 vs JN05W2
          cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FN11    L1M   7.9     -1614.5     1952.5  33482.1  36370.5    2558.8     13.0      6.0         13.0          6.0         49             50      12   316288.0    269579.5                0         20
1  TL3_UW_FN11    L3M   7.9     -1527.1    -2490.6  33482.1  36370.5   13524.6     13.0      6.0         13.0          6.0        153            161      12   316288.0    269579.5                0         20
2  TL3_UW_FN11    L6M   7.9      -976.1    -2224.2  33482.1  36370.5   22912.7     13.0      6.0         13.0          6.0        317            350      12   316288.0    269579.5                0         20
3  TL3_UW_FN11   HOLD -27.7      -616.4    -1290.6  80691.3  63185.1   16198.7     13.0      6.0         13.0          6.0        576            631      12   316288.0    269579.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 269579.46000000834, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_FN23 vs JN05W2
          cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FN23    L1M  11.4      1211.8    -8660.9  32218.6  36370.5   -8054.6     13.0      7.0         13.0          6.0         50             50      12   316288.0    302776.6                1         20
1  TL3_UW_FN23    L3M -12.3     -2581.5    -5327.5  40855.0  36370.5   10687.7     13.0      6.0         13.0          6.0        148            161      12   316288.0    302776.6                1         20
2  TL3_UW_FN23    L6M -12.3      -137.0    -1604.0  40855.0  36370.5   23532.9     13.0      6.0         13.0          6.0        317            350      12   316288.0    302776.6                1         20
3  TL3_UW_FN23   HOLD  -0.9     -1338.1    -2048.5  63781.7  63185.1   15440.8     13.0      6.0         13.0          6.0        580            631      12   316288.0    302776.6                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 302776.62000000826, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_FN37 vs JN05W2
          cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_FN37    L1M  35.5     -2583.4     1289.5  23462.3  36370.5    1895.8     13.0      5.0         13.0          6.0         52             50      12   316288.0    324730.3                1         20
1  TL3_UW_FN37    L3M  35.5      -904.4      625.6  23462.3  36370.5   16640.8     13.0      6.0         13.0          6.0        158            161      12   316288.0    324730.3                1         20
2  TL3_UW_FN37    L6M  35.5       188.4    -1711.8  23462.3  36370.5   23425.1     13.0      6.0         13.0          6.0        343            350      12   316288.0    324730.3                1         20
3  TL3_UW_FN37   HOLD  12.7      2186.6     1198.1  55145.4  63185.1   18687.4     13.0      6.0         13.0          6.0        617            631      12   316288.0    324730.3                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 324730.2600000092, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_INJ_ASIA vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_ASIA    L1M  0.0         0.0        0.0  36370.5  36370.5     606.3     13.0      6.0         13.0          6.0         50             50      21   316288.0    317781.2                0         20
1  TL3_UW_INJ_ASIA    L3M  0.0        -7.8      -91.3  36370.5  36370.5   15923.9     13.0      6.0         13.0          6.0        162            161      21   316288.0    317781.2                0         20
2  TL3_UW_INJ_ASIA    L6M  0.0         2.3       84.8  36370.5  36370.5   25221.7     13.0      6.0         13.0          6.0        351            350      21   316288.0    317781.2                0         20
3  TL3_UW_INJ_ASIA   HOLD  0.8        97.7       52.5  62701.3  63185.1   17541.8     13.0      6.0         13.0          6.0        633            631      21   316288.0    317781.2                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317781.1800000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB1 vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB1    L1M  5.2         0.0      475.2  34469.8  36370.5    1081.5     13.0      6.0         13.0          6.0         51             50      21   316288.0    321272.4                0         20
1  TL3_UW_INJ_MFB1    L3M  5.2       285.5      431.5  34469.8  36370.5   16446.7     13.0      6.0         13.0          6.0        164            161      21   316288.0    321272.4                0         20
2  TL3_UW_INJ_MFB1    L6M  5.2       535.1      652.7  34469.8  36370.5   25789.6     13.0      6.0         13.0          6.0        352            350      21   316288.0    321272.4                0         20
3  TL3_UW_INJ_MFB1   HOLD -4.1       118.2      185.0  65752.5  63185.1   17674.4     13.0      6.0         13.0          6.0        633            631      21   316288.0    321272.4                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 321272.3600000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB1_P11 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB1_P11    L1M -5.7       100.1     -445.6  38453.2  36370.5     160.7     13.0      6.0         13.0          6.0         50             50      12   316288.0    304388.3                0         20
1  TL3_UW_INJ_MFB1_P11    L3M -5.7      -480.5     -924.3  38453.2  36370.5   15090.9     13.0      6.0         13.0          6.0        162            161      12   316288.0    304388.3                0         20
2  TL3_UW_INJ_MFB1_P11    L6M -5.7      -861.3    -1281.3  38453.2  36370.5   23855.6     13.0      6.0         13.0          6.0        352            350      12   316288.0    304388.3                0         20
3  TL3_UW_INJ_MFB1_P11   HOLD -1.6      -487.1     -704.4  64182.9  63185.1   16785.0     13.0      6.0         13.0          6.0        634            631      12   316288.0    304388.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 304388.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB1_P23 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB1_P23    L1M -0.3       -92.6     -178.8  36472.0  36370.5     427.5     13.0      6.0         13.0          6.0         50             50      12   316288.0    309128.1                0         20
1  TL3_UW_INJ_MFB1_P23    L3M -0.3      -235.8     -365.2  36472.0  36370.5   15650.0     13.0      5.6         13.0          6.0        161            161      12   316288.0    309128.1                0         20
2  TL3_UW_INJ_MFB1_P23    L6M -0.3      -423.0     -813.9  36472.0  36370.5   24323.0     13.0      6.0         13.0          6.0        351            350      12   316288.0    309128.1                0         20
3  TL3_UW_INJ_MFB1_P23   HOLD -2.2      -460.5     -655.3  64596.7  63185.1   16834.1     13.0      6.0         13.0          6.0        632            631      12   316288.0    309128.1                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 309128.0800000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB1_P37 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB1_P37    L1M -0.3       -92.6     -178.8  36472.0  36370.5     427.5     13.0      6.0         13.0          6.0         50             50      12   316288.0    305229.3                0         20
1  TL3_UW_INJ_MFB1_P37    L3M -0.3      -255.9     -421.1  36472.0  36370.5   15594.1     13.0      6.0         13.0          6.0        162            161      12   316288.0    305229.3                0         20
2  TL3_UW_INJ_MFB1_P37    L6M -0.3      -728.6    -1116.3  36472.0  36370.5   24020.6     13.0      6.0         13.0          6.0        351            350      12   316288.0    305229.3                0         20
3  TL3_UW_INJ_MFB1_P37   HOLD  4.2      -648.9     -844.2  60538.9  63185.1   16645.1     13.0      6.0         13.0          6.0        632            631      12   316288.0    305229.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 305229.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB2 vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB2    L1M  1.0      -205.2      253.0  36024.8  36370.5     859.3     13.0      6.0         13.0          6.0         50             50      21   316288.0    324665.9                0         20
1  TL3_UW_INJ_MFB2    L3M  1.0       301.8      717.4  36024.8  36370.5   16732.6     13.0      6.0         13.0          6.0        161            161      21   316288.0    324665.9                0         20
2  TL3_UW_INJ_MFB2    L6M  1.0       492.9      740.9  36024.8  36370.5   25877.8     13.0      6.0         13.0          6.0        348            350      21   316288.0    324665.9                0         20
3  TL3_UW_INJ_MFB2   HOLD -0.2       470.3      594.7  63306.3  63185.1   18084.1     13.0      6.0         13.0          6.0        634            631      21   316288.0    324665.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 324665.9000000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB2_P11 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB2_P11    L1M  3.0       357.9      628.2  35296.7  36370.5    1234.5     13.0      6.0         13.0          6.0         50             50      12   316288.0    314521.8                0         20
1  TL3_UW_INJ_MFB2_P11    L3M  3.0       300.8      392.1  35296.7  36370.5   16407.3     13.0      6.0         13.0          6.0        162            161      12   316288.0    314521.8                0         20
2  TL3_UW_INJ_MFB2_P11    L6M  3.0       257.5      337.2  35296.7  36370.5   25474.1     13.0      6.0         13.0          6.0        352            350      12   316288.0    314521.8                0         20
3  TL3_UW_INJ_MFB2_P11   HOLD -2.0       224.2      284.0  64471.3  63185.1   17773.3     13.0      6.0         13.0          6.0        635            631      12   316288.0    314521.8                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 314521.8000000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB2_P23 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB2_P23    L1M  0.0         0.0      292.2  36370.5  36370.5     898.5     13.0      6.0         13.0          6.0         51             50      12   316288.0    316018.3                0         20
1  TL3_UW_INJ_MFB2_P23    L3M  0.0        45.8      195.2  36370.5  36370.5   16210.4     13.0      6.0         13.0          6.0        163            161      12   316288.0    316018.3                0         20
2  TL3_UW_INJ_MFB2_P23    L6M  0.0       -45.9       98.7  36370.5  36370.5   25235.6     13.0      6.0         13.0          6.0        352            350      12   316288.0    316018.3                0         20
3  TL3_UW_INJ_MFB2_P23   HOLD  1.4      -217.1     -141.5  62291.3  63185.1   17347.8     13.0      6.0         13.0          6.0        637            631      12   316288.0    316018.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 316018.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB2_P37 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB2_P37    L1M  0.0         0.0      394.7  36370.5  36370.5    1001.0     13.0      6.0         13.0          6.0         50             50      12   316288.0    317078.9                0         20
1  TL3_UW_INJ_MFB2_P37    L3M  0.0       142.1      321.7  36370.5  36370.5   16336.9     13.0      6.0         13.0          6.0        161            161      12   316288.0    317078.9                0         20
2  TL3_UW_INJ_MFB2_P37    L6M  0.0       -91.0       12.9  36370.5  36370.5   25149.8     13.0      6.0         13.0          6.0        352            350      12   316288.0    317078.9                0         20
3  TL3_UW_INJ_MFB2_P37   HOLD  0.0       -82.2      -21.2  63185.1  63185.1   17468.1     13.0      6.0         13.0          6.0        635            631      12   316288.0    317078.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317078.9000000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB3 vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB3    L1M  0.0         0.0     -319.0  36370.5  36370.5     287.3     13.0      6.0         13.0          6.0         50             50      21   316288.0    321253.3                0         20
1  TL3_UW_INJ_MFB3    L3M  0.0       428.3      535.8  36370.5  36370.5   16551.0     13.0      6.0         13.0          6.0        163            161      21   316288.0    321253.3                0         20
2  TL3_UW_INJ_MFB3    L6M  0.0       795.3      903.1  36370.5  36370.5   26040.0     13.0      6.0         13.0          6.0        352            350      21   316288.0    321253.3                0         20
3  TL3_UW_INJ_MFB3   HOLD  1.4       603.8      668.9  62286.3  63185.1   18158.3     13.0      6.0         13.0          6.0        632            631      21   316288.0    321253.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 321253.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB4 vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB4    L1M  0.0       435.9      869.5  36370.5  36370.5    1475.8     13.0      6.0         13.0          6.0         50             50      21   316288.0    320644.9                0         20
1  TL3_UW_INJ_MFB4    L3M  0.0       406.5      542.1  36370.5  36370.5   16557.3     13.0      6.0         13.0          6.0        161            161      21   316288.0    320644.9                0         20
2  TL3_UW_INJ_MFB4    L6M  0.0       519.9      653.8  36370.5  36370.5   25790.7     13.0      6.0         13.0          6.0        350            350      21   316288.0    320644.9                0         20
3  TL3_UW_INJ_MFB4   HOLD  3.5       375.2      450.1  60949.8  63185.1   17939.4     13.0      6.0         13.0          6.0        631            631      21   316288.0    320644.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 320644.94000000966, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB6 vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB6    L1M  0.0         0.0      438.2  36370.5  36370.5    1044.5     13.0      6.0         13.0          6.0         50             50      21   316288.0    317343.5                0         20
1  TL3_UW_INJ_MFB6    L3M  0.0       -86.2       55.3  36370.5  36370.5   16070.5     13.0      6.0         13.0          6.0        161            161      21   316288.0    317343.5                0         20
2  TL3_UW_INJ_MFB6    L6M  0.0       130.2      320.8  36370.5  36370.5   25457.7     13.0      6.0         13.0          6.0        350            350      21   316288.0    317343.5                0         20
3  TL3_UW_INJ_MFB6   HOLD  0.0       400.1      490.2  63185.1  63185.1   17979.5     13.0      6.0         13.0          6.0        631            631      21   316288.0    317343.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317343.54000000964, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB7 vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB7    L1M  0.0         0.0      312.2  36370.5  36370.5     918.5     13.0      6.0         13.0          6.0         50             50      21   316288.0    316065.0                0         20
1  TL3_UW_INJ_MFB7    L3M  0.0        83.9     -103.0  36370.5  36370.5   15912.2     13.0      6.0         13.0          6.0        161            161      21   316288.0    316065.0                0         20
2  TL3_UW_INJ_MFB7    L6M  0.0       131.0      243.0  36370.5  36370.5   25379.9     13.0      6.0         13.0          6.0        350            350      21   316288.0    316065.0                0         20
3  TL3_UW_INJ_MFB7   HOLD  0.0        93.3      150.0  63185.1  63185.1   17639.3     13.0      6.0         13.0          6.0        633            631      21   316288.0    316065.0                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 316065.0000000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB7_P11 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB7_P11    L1M  4.0       330.5      609.8  34922.9  36370.5    1216.1     13.0      6.0         13.0          6.0         50             50      12   316288.0    314990.9                0         20
1  TL3_UW_INJ_MFB7_P11    L3M  4.0        16.5      275.8  34922.9  36370.5   16291.0     13.0      6.0         13.0          6.0        161            161      12   316288.0    314990.9                0         20
2  TL3_UW_INJ_MFB7_P11    L6M  4.0      -140.5       -4.8  34922.9  36370.5   25132.1     13.0      6.0         13.0          6.0        350            350      12   316288.0    314990.9                0         20
3  TL3_UW_INJ_MFB7_P11   HOLD  2.3       -27.1       38.5  61751.3  63185.1   17527.9     13.0      6.0         13.0          6.0        631            631      12   316288.0    314990.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 314990.9000000098, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB7_P23 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB7_P23    L1M  0.0         0.0        0.0  36370.5  36370.5     606.3     13.0      6.0         13.0          6.0         50             50      12   316288.0    316528.3                0         20
1  TL3_UW_INJ_MFB7_P23    L3M  0.0      -181.2      -67.2  36370.5  36370.5   15948.0     13.0      6.0         13.0          6.0        161            161      12   316288.0    316528.3                0         20
2  TL3_UW_INJ_MFB7_P23    L6M  0.0      -163.4     -214.5  36370.5  36370.5   24922.4     13.0      6.0         13.0          6.0        350            350      12   316288.0    316528.3                0         20
3  TL3_UW_INJ_MFB7_P23   HOLD -1.3      -140.9     -183.3  63976.3  63185.1   17306.0     13.0      6.0         13.0          6.0        633            631      12   316288.0    316528.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 316528.2600000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFB7_P37 vs JN05W2
                  cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFB7_P37    L1M  0.0         0.0      406.9  36370.5  36370.5    1013.2     13.0      6.0         13.0          6.0         50             50      12   316288.0    316128.5                0         20
1  TL3_UW_INJ_MFB7_P37    L3M  0.0       -56.3       73.3  36370.5  36370.5   16088.5     13.0      6.0         13.0          6.0        161            161      12   316288.0    316128.5                0         20
2  TL3_UW_INJ_MFB7_P37    L6M  0.0      -146.2      -78.0  36370.5  36370.5   25058.9     13.0      6.0         13.0          6.0        350            350      12   316288.0    316128.5                0         20
3  TL3_UW_INJ_MFB7_P37   HOLD -0.3      -158.3     -190.6  63379.8  63185.1   17298.8     13.0      6.0         13.0          6.0        634            631      12   316288.0    316128.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 316128.5400000098, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_ASIA vs JN05W2
                  cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_ASIA    L1M  21.9       -33.5     1966.9  28402.6  36370.5    2573.2     13.0      6.0         13.0          6.0         50             50      21   316288.0    322034.5                0         20
1  TL3_UW_INJ_MFC_ASIA    L3M  18.1      -198.0      430.2  29780.8  36370.5   16445.4     13.0      6.0         13.0          6.0        163            161      21   316288.0    322034.5                0         20
2  TL3_UW_INJ_MFC_ASIA    L6M  18.1       415.7      706.1  29780.8  36370.5   25843.0     13.0      6.0         13.0          6.0        353            350      21   316288.0    322034.5                0         20
3  TL3_UW_INJ_MFC_ASIA   HOLD   2.2       150.9      301.3  61774.6  63185.1   17790.6     13.0      6.0         13.0          6.0        637            631      21   316288.0    322034.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 322034.46000000974, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_ASIA_P11 vs JN05W2
                      cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_ASIA_P11    L1M  0.0       -58.7      -90.6  36370.5  36370.5     515.7     13.0      6.0         13.0          6.0         50             50      12   316288.0    309322.5                0         20
1  TL3_UW_INJ_MFC_ASIA_P11    L3M -4.4      -260.8     -789.5  37954.1  36370.5   15225.7     13.0      6.0         13.0          6.0        162            161      12   316288.0    309322.5                0         20
2  TL3_UW_INJ_MFC_ASIA_P11    L6M -4.4      -650.2    -1005.1  37954.1  36370.5   24131.8     13.0      6.0         13.0          6.0        351            350      12   316288.0    309322.5                0         20
3  TL3_UW_INJ_MFC_ASIA_P11   HOLD -6.1      -387.1     -569.6  67017.9  63185.1   16919.7     13.0      6.0         13.0          6.0        632            631      12   316288.0    309322.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 309322.5200000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_ASIA_P23 vs JN05W2
                      cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_ASIA_P23    L1M  21.6       678.8     2475.7  28504.1  36370.5    3082.0     13.0      6.0         13.0          6.0         51             50      12   316288.0    308306.3                0         20
1  TL3_UW_INJ_MFC_ASIA_P23    L3M  21.0         1.4      606.4  28734.6  36370.5   16621.6     13.0      5.9         13.0          6.0        163            161      12   316288.0    308306.3                0         20
2  TL3_UW_INJ_MFC_ASIA_P23    L6M  21.0       373.9       -0.5  28734.6  36370.5   25136.4     13.0      6.0         13.0          6.0        352            350      12   316288.0    308306.3                0         20
3  TL3_UW_INJ_MFC_ASIA_P23   HOLD   3.0        78.5     -103.1  61291.9  63185.1   17386.3     13.0      6.0         13.0          6.0        634            631      12   316288.0    308306.3                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 308306.34000000963, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_LDN vs JN05W2
                 cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_LDN    L1M -6.2      -754.1    -1278.4  38632.9  36370.5    -672.1     13.0      6.0         13.0          6.0         51             50      21   316288.0    318059.7                0         20
1  TL3_UW_INJ_MFC_LDN    L3M -6.2       698.0      425.0  38632.9  36370.5   16440.2     13.0      6.0         13.0          6.0        164            161      21   316288.0    318059.7                0         20
2  TL3_UW_INJ_MFC_LDN    L6M -6.2       274.1      401.9  38632.9  36370.5   25538.8     13.0      6.0         13.0          6.0        352            350      21   316288.0    318059.7                0         20
3  TL3_UW_INJ_MFC_LDN   HOLD  1.6       223.4      314.4  62165.1  63185.1   17803.7     13.0      6.0         13.0          6.0        634            631      21   316288.0    318059.7                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 318059.72000000963, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_LDN_P11 vs JN05W2
                     cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_LDN_P11    L1M  0.0       -58.7      -90.6  36370.5  36370.5     515.7     13.0      6.0         13.0          6.0         50             50      12   316288.0    306483.7                0         20
1  TL3_UW_INJ_MFC_LDN_P11    L3M  0.0      -145.2     -294.6  36370.5  36370.5   15720.6     13.0      6.0         13.0          6.0        162            161      12   316288.0    306483.7                0         20
2  TL3_UW_INJ_MFC_LDN_P11    L6M  0.0      -376.4     -723.0  36370.5  36370.5   24413.9     13.0      6.0         13.0          6.0        351            350      12   316288.0    306483.7                0         20
3  TL3_UW_INJ_MFC_LDN_P11   HOLD -1.4      -248.1     -423.8  64090.6  63185.1   17065.5     13.0      6.0         13.0          6.0        633            631      12   316288.0    306483.7                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 306483.7000000096, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_LDN_P23 vs JN05W2
                     cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_LDN_P23    L1M  12.0      -319.9      852.0  32002.6  36370.5    1458.3     13.0      6.0         13.0          6.0         50             50      12   316288.0    308764.1                0         20
1  TL3_UW_INJ_MFC_LDN_P23    L3M  12.0        49.1      381.3  32002.6  36370.5   16396.5     13.0      6.0         13.0          6.0        161            161      12   316288.0    308764.1                0         20
2  TL3_UW_INJ_MFC_LDN_P23    L6M  12.0        20.8     -322.6  32002.6  36370.5   24814.3     13.0      6.0         13.0          6.0        351            350      12   316288.0    308764.1                0         20
3  TL3_UW_INJ_MFC_LDN_P23   HOLD  -2.9       -33.8     -204.4  64996.3  63185.1   17284.9     13.0      6.0         13.0          6.0        633            631      12   316288.0    308764.1                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 308764.08000000974, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_PRE vs JN05W2
                 cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_PRE    L1M  1.7         0.0      154.4  35752.9  36370.5     760.7     13.0      6.0         13.0          6.0         50             50      21   316288.0    318159.1                0         20
1  TL3_UW_INJ_MFC_PRE    L3M  1.7       437.7      817.7  35752.9  36370.5   16832.9     13.0      6.0         13.0          6.0        161            161      21   316288.0    318159.1                0         20
2  TL3_UW_INJ_MFC_PRE    L6M  1.7       560.8      746.0  35752.9  36370.5   25882.9     13.0      6.0         13.0          6.0        350            350      21   316288.0    318159.1                0         20
3  TL3_UW_INJ_MFC_PRE   HOLD  0.0       115.8      217.0  63185.1  63185.1   17706.3     13.0      6.0         13.0          6.0        630            631      21   316288.0    318159.1                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 318159.10000000964, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_PRE_P11 vs JN05W2
                     cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_PRE_P11    L1M -1.5      -375.8     -492.4  36910.6  36370.5     113.9     13.0      6.0         13.0          6.0         50             50      12   316288.0    317138.5                0         20
1  TL3_UW_INJ_MFC_PRE_P11    L3M -1.5      -165.1     -291.6  36910.6  36370.5   15723.6     13.0      5.6         13.0          6.0        161            161      12   316288.0    317138.5                0         20
2  TL3_UW_INJ_MFC_PRE_P11    L6M -1.5      -451.1     -882.4  36910.6  36370.5   24254.5     13.0      6.0         13.0          6.0        350            350      12   316288.0    317138.5                0         20
3  TL3_UW_INJ_MFC_PRE_P11   HOLD  3.7      -416.9     -633.2  60830.1  63185.1   16856.1     13.0      6.0         13.0          6.0        630            631      12   316288.0    317138.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 317138.54000000964, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_MFC_PRE_P23 vs JN05W2
                     cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_MFC_PRE_P23    L1M -3.2      -385.9      500.6  37528.2  36370.5    1106.9     13.0      6.0         13.0          6.0         50             50      12   316288.0    316598.5                0         20
1  TL3_UW_INJ_MFC_PRE_P23    L3M -3.2      -471.8     -192.4  37528.2  36370.5   15822.8     13.0      5.6         13.0          6.0        161            161      12   316288.0    316598.5                0         20
2  TL3_UW_INJ_MFC_PRE_P23    L6M -3.2      -501.8     -360.9  37528.2  36370.5   24776.0     13.0      6.0         13.0          6.0        350            350      12   316288.0    316598.5                0         20
3  TL3_UW_INJ_MFC_PRE_P23   HOLD -0.0      -326.2     -385.1  63185.1  63185.1   17104.2     13.0      6.0         13.0          6.0        631            631      12   316288.0    316598.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 316598.5400000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_NDXB vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_NDXB    L1M  1.5       723.8      977.0  35816.7  36370.5    1583.3     13.0      6.0         13.0          6.0         50             50      21   316288.0    320345.6                0         20
1  TL3_UW_INJ_NDXB    L3M  1.5       404.9      550.4  35816.7  36370.5   16565.6     13.0      6.0         13.0          6.0        161            161      21   316288.0    320345.6                0         20
2  TL3_UW_INJ_NDXB    L6M  1.5       645.5      803.8  35816.7  36370.5   25940.7     13.0      6.0         13.0          6.0        351            350      21   316288.0    320345.6                0         20
3  TL3_UW_INJ_NDXB   HOLD  2.4       768.0      844.8  61697.5  63185.1   18334.1     13.0      6.0         13.0          6.0        633            631      21   316288.0    320345.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 320345.56000000966, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_NYAM vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_NYAM    L1M  0.0       199.2      537.6  36370.5  36370.5    1143.9     13.0      6.0         13.0          6.0         50             50      21   316288.0    321988.5                0         20
1  TL3_UW_INJ_NYAM    L3M  0.0        80.7      269.9  36370.5  36370.5   16285.1     13.0      6.0         13.0          6.0        161            161      21   316288.0    321988.5                0         20
2  TL3_UW_INJ_NYAM    L6M  0.0       378.3      550.8  36370.5  36370.5   25687.7     13.0      6.0         13.0          6.0        350            350      21   316288.0    321988.5                0         20
3  TL3_UW_INJ_NYAM   HOLD -1.9       150.7      241.3  64372.5  63185.1   17730.7     13.0      6.0         13.0          6.0        632            631      21   316288.0    321988.5                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 321988.5400000097, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_PRE vs JN05W2
             cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_PRE    L1M  1.4       416.0      562.0  35847.9  36370.5    1168.3     13.0      6.0         13.0          6.0         50             50      21   316288.0    315085.6                0         20
1  TL3_UW_INJ_PRE    L3M  1.4       183.0      354.0  35847.9  36370.5   16369.2     13.0      6.0         13.0          6.0        161            161      21   316288.0    315085.6                0         20
2  TL3_UW_INJ_PRE    L6M  1.4        29.3      120.7  35847.9  36370.5   25257.6     13.0      6.0         13.0          6.0        350            350      21   316288.0    315085.6                0         20
3  TL3_UW_INJ_PRE   HOLD  0.0       116.5      163.9  63185.1  63185.1   17653.2     13.0      6.0         13.0          6.0        630            631      21   316288.0    315085.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 315085.62000000966, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_INJ_PRE2 vs JN05W2
              cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_INJ_PRE2    L1M  1.4       416.0      562.0  35847.9  36370.5    1168.3     13.0      6.0         13.0          6.0         50             50       6   316288.0    315085.6                0         20
1  TL3_UW_INJ_PRE2    L3M  1.4       183.0      354.0  35847.9  36370.5   16369.2     13.0      6.0         13.0          6.0        161            161       6   316288.0    315085.6                0         20
2  TL3_UW_INJ_PRE2    L6M  1.4        29.3      120.7  35847.9  36370.5   25257.6     13.0      6.0         13.0          6.0        350            350       6   316288.0    315085.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 315085.62000000966, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_KLDN_HOLD vs JN05W2
               cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_KLDN_HOLD    L1M  0.0         0.0      334.5  36370.5  36370.5     940.8     13.0      6.0         13.0          6.0         49             50       6   316288.0    307222.0                0         20
1  TL3_UW_KLDN_HOLD    L3M  0.0       867.6     -187.4  36370.5  36370.5   15827.8     13.0      6.0         13.0          6.0        155            161       6   316288.0    307222.0                0         20
2  TL3_UW_KLDN_HOLD    L6M  0.0       248.9     -591.1  36370.5  36370.5   24545.8     13.0      6.0         13.0          6.0        335            350       6   316288.0    307222.0                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 307222.00000000803, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_MF_ASIA_SK vs JN05W2
Empty DataFrame
Columns: [cell, months]
Index: []
trend None


TL3_UW_MF_LDN_M7 vs JN05W2
               cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_MF_LDN_M7    L1M   1.8      -108.7       77.8  35733.3  36370.5     684.1     13.0      6.0         13.0          6.0         51             50      21   316288.0    326079.0                0         20
1  TL3_UW_MF_LDN_M7    L3M   1.8        96.6      211.1  35733.3  36370.5   16226.2     13.0      6.0         13.0          6.0        159            161      21   316288.0    326079.0                0         20
2  TL3_UW_MF_LDN_M7    L6M   1.8       181.0      581.8  35733.3  36370.5   25718.7     13.0      6.0         13.0          6.0        339            350      21   316288.0    326079.0                0         20
3  TL3_UW_MF_LDN_M7   HOLD  13.4       385.3      581.7  54740.9  63185.1   18071.0     13.0      6.0         13.0          6.0        610            631      21   316288.0    326079.0                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 326079.04000000923, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_MF_NIGHT_HALF vs JN05W2
Empty DataFrame
Columns: [cell, months]
Index: []
trend None


TL3_UW_MF_NIGHT_SK vs JN05W2
Empty DataFrame
Columns: [cell, months]
Index: []
trend None


TL3_UW_MF_NIGHT_SK15 vs JN05W2
Empty DataFrame
Columns: [cell, months]
Index: []
trend None


TL3_UW_MF_NIGHT_SK_P11 vs JN05W2
                     cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_MF_NIGHT_SK_P11    L1M  5.5         0.0      497.4  34380.8  36370.5    1103.7     13.0      6.0         13.0          6.0         47             50      12   316288.0    262755.1                1         20
1  TL3_UW_MF_NIGHT_SK_P11    L3M -5.0       621.6    -3173.7  38195.3  36370.5   12841.5     13.0      5.0         13.0          6.0        153            161      12   316288.0    262755.1                1         20
2  TL3_UW_MF_NIGHT_SK_P11    L6M -5.0     -2524.4    -4301.1  38195.3  36370.5   20835.8     13.0      6.0         13.0          6.0        324            350      12   316288.0    262755.1                1         20
3  TL3_UW_MF_NIGHT_SK_P11   HOLD  2.4      -881.3    -1801.2  61654.1  63185.1   15688.1     13.0      6.0         13.0          6.0        594            631      12   316288.0    262755.1                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 262755.0800000084, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_MF_NIGHT_SK_P23 vs JN05W2
                     cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_MF_NIGHT_SK_P23    L1M  29.3      3549.7    -1498.8  25721.3  36370.5    -892.5     13.0      6.0         13.0          6.0         47             50      12   316288.0    314098.6                0         20
1  TL3_UW_MF_NIGHT_SK_P23    L3M  16.0     -1142.3    -3638.7  30533.4  36370.5   12376.5     13.0      6.0         13.0          6.0        156            161      12   316288.0    314098.6                0         20
2  TL3_UW_MF_NIGHT_SK_P23    L6M  16.0       829.5     -494.6  30533.4  36370.5   24642.3     13.0      6.0         13.0          6.0        326            350      12   316288.0    314098.6                0         20
3  TL3_UW_MF_NIGHT_SK_P23   HOLD  -5.7      -660.8    -1792.2  66810.4  63185.1   15697.1     13.0      6.0         13.0          6.0        597            631      12   316288.0    314098.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 314098.6400000093, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_MF_NIGHT_SK_P37 vs JN05W2
                     cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_MF_NIGHT_SK_P37    L1M  29.3      3549.7     9328.8  25721.3  36370.5    9935.1     13.0      6.0         13.0          6.0         48             50      12   316288.0    290194.4                1         20
1  TL3_UW_MF_NIGHT_SK_P37    L3M -12.1     -1393.9      764.6  40771.1  36370.5   16779.8     13.0      6.0         13.0          6.0        156            161      12   316288.0    290194.4                1         20
2  TL3_UW_MF_NIGHT_SK_P37    L6M -12.1       685.5     -803.0  40771.1  36370.5   24333.9     13.0      6.0         13.0          6.0        334            350      12   316288.0    290194.4                1         20
3  TL3_UW_MF_NIGHT_SK_P37   HOLD   0.0      1633.2      870.8  63185.1  63185.1   18360.1     13.0      6.0         13.0          6.0        594            631      12   316288.0    290194.4                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 290194.3600000092, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_MF_NYAM_K7 vs JN05W2
Empty DataFrame
Columns: [cell, months]
Index: []
trend None


TL3_UW_MF_U7_SK vs JN05W2
Empty DataFrame
Columns: [cell, months]
Index: []
trend None


TL3_UW_NDXCA_SK vs JN05W2
              cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_NDXCA_SK    L1M  77.3      6081.7    11594.0   8239.7  36370.5   12200.3      9.0      6.0         13.0          6.0         56             50       6   316288.0    338212.9                1         20
1  TL3_UW_NDXCA_SK    L3M   0.2       940.8     3032.4  36288.2  36370.5   19047.6     10.0      6.0         13.0          6.0        162            161       6   316288.0    338212.9                1         20
2  TL3_UW_NDXCA_SK    L6M   0.2      2127.4      567.9  36288.2  36370.5   25704.8     10.0      6.0         13.0          6.0        347            350       6   316288.0    338212.9                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 338212.940000009, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_NDXCA_SKP7 vs JN05W2
                cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_NDXCA_SKP7    L1M  76.3      2490.0     8809.0   8604.3  36370.5    9415.3      9.0      6.0         13.0          6.0         53             50       6   316288.0    325056.1                1         20
1  TL3_UW_NDXCA_SKP7    L3M  24.5       821.6     2894.3  27447.9  36370.5   18909.5     10.0      6.0         13.0          6.0        162            161       6   316288.0    325056.1                1         20
2  TL3_UW_NDXCA_SKP7    L6M  24.5       -83.1      988.0  27447.9  36370.5   26124.9     10.0      6.0         13.0          6.0        346            350       6   316288.0    325056.1                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 325056.1000000095, 'win_turn_losing': 1, 'win_weeks': 20}


TL3_UW_QQQGD15_PR vs JN05W2
                cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_QQQGD15_PR    L1M  2.1       380.4     -218.6  35614.7  36370.5     387.7     13.0      6.0         13.0          6.0         49             50      12   316288.0    332843.1                0         20
1  TL3_UW_QQQGD15_PR    L3M  2.1      1006.0     1810.2  35614.7  36370.5   17825.4     13.0      6.0         13.0          6.0        160            161      12   316288.0    332843.1                0         20
2  TL3_UW_QQQGD15_PR    L6M  2.1      1258.4     1656.3  35614.7  36370.5   26793.2     13.0      6.0         13.0          6.0        345            350      12   316288.0    332843.1                0         20
3  TL3_UW_QQQGD15_PR   HOLD -3.7       686.4      936.8  65548.3  63185.1   18426.1     13.0      6.0         13.0          6.0        620            631      12   316288.0    332843.1                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 332843.14000000956, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_QQQGD15_SK vs JN05W2
                cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_QQQGD15_SK    L1M  0.0       288.8     -147.1  36370.5  36370.5     459.2     13.0      6.0         13.0          6.0         48             50      12   316288.0    307013.2                0         20
1  TL3_UW_QQQGD15_SK    L3M  0.0       821.2      155.3  36370.5  36370.5   16170.5     13.0      6.0         13.0          6.0        151            161      12   316288.0    307013.2                0         20
2  TL3_UW_QQQGD15_SK    L6M  0.0       219.6     -144.8  36370.5  36370.5   24992.1     13.0      6.0         13.0          6.0        335            350      12   316288.0    307013.2                0         20
3  TL3_UW_QQQGD15_SK   HOLD -0.8       745.9      491.1  63667.6  63185.1   17980.5     13.0      6.0         13.0          6.0        605            631      12   316288.0    307013.2                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 307013.2400000095, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_TDNV_PR vs JN05W2
             cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_TDNV_PR    L1M   2.1      -706.4    -1484.8  35614.7  36370.5    -878.5     13.0      6.0         13.0          6.0         49             50      12   316288.0    319960.2                0         20
1  TL3_UW_TDNV_PR    L3M   2.1       -74.3      531.1  35614.7  36370.5   16546.3     13.0      6.0         13.0          6.0        160            161      12   316288.0    319960.2                0         20
2  TL3_UW_TDNV_PR    L6M   2.1      -150.5      200.1  35614.7  36370.5   25337.0     13.0      6.0         13.0          6.0        347            350      12   316288.0    319960.2                0         20
3  TL3_UW_TDNV_PR   HOLD -10.9       427.9      756.0  70094.5  63185.1   18245.4     13.0      6.0         13.0          6.0        624            631      12   316288.0    319960.2                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 319960.1600000097, 'win_turn_losing': 0, 'win_weeks': 20}

