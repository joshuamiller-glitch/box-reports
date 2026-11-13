# DS3_UW_WIDE - Unusual Whales WIDE program (W-UW2). Rebuilt 2026-11-13T20:15:48Z by code/th_uw/uw_page.py (every 3 h). Research only, shadow, NO PASS claim.
Rule: best candidate per use is always named with its honest strength; "null q95" = max over all cells of the group when the feature matrix is permuted within month (30-40 draws), so recents below it is chance-level. Windows: L1M L3M L6M HOLD PREUW (PRE clipped to the 2024-10-01 UW start); X' has NO UW data (history starts 2024-10); first-order $/wk, history unmodified, fees in net_fee. Screens are in-sample on thresholds (HOLD quantiles). Gain sign: E skip = -pnl of flagged entries, press = +0.5x pnl (size x1.5), K/Q hold = hold outcome minus actual at the cut/clip.

## 1. Status (what finished / running / died)
- screen (first read, features A regime, B levels, C Tide, D charm/vanna; RTH) and screen2 (WIDE: 1/5/15/60-min deltas, 10:00/10:30 regime, pre-market/prior-close LAST priors, Tide extremes/divergence; scopes rth/late/asia/london): FINISHED for JN05W2, JN05W2J, LPB_BASE (screen2 finished ~02:00Z 11-13; nobody read it until 14:15Z: lead watcher bug).
- pull IV (volatility stats SPX/NDX/QQQ/SPY): 4692 files under /mnt/l2/l2vast/uw (pull finished; features from them NOT yet screened)
- pull dark pool price levels (QQQ SPY + 8 NQ weights, 260 d): 2600 files under /mnt/l2/l2vast/uw (pull finished; features from them NOT yet screened)
- identity gate: TL3_UW_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL; TL3J_UW_ID 202610: 658 trades net 23596.16 vs JN05W2J 658 net 23596.16 -> IDENTICAL
- exact sets (TP engine, one set per job, tag UW): TL3J_UW_ID: 1 months; TL3J_UW_KLDN_HOLD: 6 months; TL3J_UW_NDXCA_SK: 6 months; TL3J_UW_SPXVDIR_PR: 12 months; TL3_UW_ID: 1 months; TL3_UW_KLDN_HOLD: 6 months; TL3_UW_NDXCA_SK: 6 months; TL3_UW_NDXCA_SKP7: 6 months; TL3_UW_QQQGD15_PR: 12 months; TL3_UW_QQQGD15_SK: 12 months; TL3_UW_TDNV_PR: 12 months
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

## 3. By feature family and horizon (best recents across all groups/bases; shows where the signal sits)
| family | horizon | base | use act book scope | feat | dir th | recents | null q95 | margin | PREUW |
|---|---|---|---|---|---|---|---|---|---|
| W | LAST | screen2 JN05W2 | E skip ALL asia | W_LAST_NDX_c_oi_s | ge 3.594e+12 | 2632 | 1753 | +879 | -397 |
| W | R10 | screen3 LPB_BASE | E skip ALL rth | W_R10_SPY_g_dir | ge 4.926e+08 | 2411 | 2030 | +381 | 132 |
| F3 | level | screen3 LPB_BASE | E skip K7 rth | F3_EMabs_SPX | le 1.132 | 1404 | 1085 | +319 | 171 |
| B | level | screen2 LPB_BASE | E press ALL rth | B_NDX_vol_behind | ge 349 | 1271 | 1234 | +37 | -289 |
| C | level | screen2 LPB_BASE | E press K7 rth | C_net_s | ge 2.307e+08 | 819 | 799 | +20 | -10 |
| D | level | screen2 LPB_BASE | K hold ALL rth | D_NDX_v_oi | le 1.388e+08 | 2949 | 2955 | -6 | 1019 |
| W | d15 | screen2 JN05W2 | E press ALL rth | W_QQQ_g_dir_d15 | le 2.541e+08 | 1716 | 1737 | -22 | 663 |
| A | d15 | screen2 JN05W2 | E press ALL rth | A_QQQ_g_dir_d15 | le 2.541e+08 | 1716 | 1737 | -22 | 663 |
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
- NDX SPOT CAVEAT (W-UR1, DS3_UWREGIME.md): UW NDX spot is frozen/stale on ~67 days (not ~15). Screens 1-3 (built before this note) used the NDX spot unfiltered for B_NDX_* / F3_OI_NDX level distances (SPX levels, Tide, gamma/charm/vanna exposure series, EM from NQ price are unaffected; the NQ/NDX ratio is a 5-day median and robust). uw_tf.py now drops NDX spot rows >0.4% off the NQ-implied price; B_NDX_* cells must be re-screened (queued) and any NDX-level cell in this page is provisional. Cells that rank on NDX levels: LPB_BASE E press ALL B_NDX_vol_behind.

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


TL3_UW_KLDN_HOLD vs JN05W2
               cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_KLDN_HOLD    L1M  0.0         0.0      334.5  36370.5  36370.5     940.8     13.0      6.0         13.0          6.0         49             50       6   316288.0    307222.0                0         20
1  TL3_UW_KLDN_HOLD    L3M  0.0       867.6     -187.4  36370.5  36370.5   15827.8     13.0      6.0         13.0          6.0        155            161       6   316288.0    307222.0                0         20
2  TL3_UW_KLDN_HOLD    L6M  0.0       248.9     -591.1  36370.5  36370.5   24545.8     13.0      6.0         13.0          6.0        335            350       6   316288.0    307222.0                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 307222.00000000803, 'win_turn_losing': 0, 'win_weeks': 20}


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

