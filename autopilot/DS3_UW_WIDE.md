# DS3_UW_WIDE - Unusual Whales WIDE program (W-UW2). Rebuilt 2026-11-13T14:15:10Z by code/th_uw/uw_page.py (every 3 h). Research only, shadow, NO PASS claim.
Rule: best candidate per use is always named with its honest strength; "null q95" = max over all cells of the group when the feature matrix is permuted within month (30-40 draws), so recents below it is chance-level. Windows: L1M L3M L6M HOLD PREUW (PRE clipped to the 2024-10-01 UW start); X' has NO UW data (history starts 2024-10); first-order $/wk, history unmodified, fees in net_fee. Screens are in-sample on thresholds (HOLD quantiles). Gain sign: E skip = -pnl of flagged entries, press = +0.5x pnl (size x1.5), K/Q hold = hold outcome minus actual at the cut/clip.

## 1. Status (what finished / running / died)
- screen (first read, features A regime, B levels, C Tide, D charm/vanna; RTH) and screen2 (WIDE: 1/5/15/60-min deltas, 10:00/10:30 regime, pre-market/prior-close LAST priors, Tide extremes/divergence; scopes rth/late/asia/london): FINISHED for JN05W2, JN05W2J, LPB_BASE (screen2 finished ~02:00Z 11-13; nobody read it until 14:15Z: lead watcher bug).
- pull IV (volatility stats SPX/NDX/QQQ/SPY): 2212 files under /mnt/l2/l2vast/uw (pull finished; features from them NOT yet screened)
- pull dark pool price levels (QQQ SPY + 8 NQ weights, 260 d): 2600 files under /mnt/l2/l2vast/uw (pull finished; features from them NOT yet screened)
- identity gate: TL3_UW_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL; TL3J_UW_ID 202610: 658 trades net 23596.16 vs JN05W2J 658 net 23596.16 -> IDENTICAL
- exact sets (TP engine, one set per job, tag UW): TL3J_UW_ID: 1 months; TL3J_UW_SPXVDIR_PR: 6 months; TL3_UW_ID: 1 months; TL3_UW_QQQGD15_PR: 6 months; TL3_UW_QQQGD15_SK: 6 months; TL3_UW_TDNV_PR: 6 months
- died/blocked: nothing died. Overnight the four first sets waited in TOOLS (box load ~40, cap 25); admitted 03:03Z-~11:00Z, L6M finished; HOLD months started 14:25Z after the UW priority tag. 0DTE walls: history is end-of-day only (not causal); expected-move inputs pulled but not yet screened.

## 2. Best candidate per use per base (screen2, ranked by recents = (L6M+HOLD)/2 $/wk; top 3 per use/action; LEAD = recents > null q95, L3M>0, both L6M halves > 0)

### LPB_BASE (42 groups x ~3,000 cells; LEAD cells: 6)

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

### JN05W2 (41 groups x ~3,000 cells; LEAD cells: 5)

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

### JN05W2J (41 groups x ~3,000 cells; LEAD cells: 4)

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

## 3. By feature family and horizon (best recents across all groups/bases; shows where the signal sits)
| family | horizon | base | use act book scope | feat | dir th | recents | null q95 | margin | PREUW |
|---|---|---|---|---|---|---|---|---|---|
| W | LAST | JN05W2 | E skip ALL asia | W_LAST_NDX_c_oi_s | ge 3.594e+12 | 2632 | 1753 | +879 | -397 |
| B | level | LPB_BASE | E press ALL rth | B_NDX_vol_behind | ge 349 | 1271 | 1234 | +37 | -289 |
| C | level | LPB_BASE | E press K7 rth | C_net_s | ge 2.307e+08 | 819 | 799 | +20 | -10 |
| D | level | LPB_BASE | K hold ALL rth | D_NDX_v_oi | le 1.388e+08 | 2949 | 2955 | -6 | 1019 |
| W | d15 | JN05W2 | E press ALL rth | W_QQQ_g_dir_d15 | le 2.541e+08 | 1716 | 1737 | -22 | 663 |
| A | d15 | JN05W2 | E press ALL rth | A_QQQ_g_dir_d15 | le 2.541e+08 | 1716 | 1737 | -22 | 663 |
| W | d5 | JN05W2J | E press M7 rth | W_NDX_g_dir_d5 | le 0 | 516 | 558 | -42 | 222 |
| W | d1 | LPB_BASE | E press ALL late | W_QQQ_c_vol_d1 | le -1.827e+11 | 293 | 343 | -50 | 108 |
| W | d60 | JN05W2 | E press ALL late | W_NDX_g_dir_d60 | ge 0 | 224 | 288 | -63 | -153 |
| A | level | JN05W2J | E press ALL late | A_NDX_g_vol | le 2.068e+10 | 290 | 362 | -73 | -153 |
| W | level | LPB_BASE | E press H7 rth | W_TD_z15 | ge 0.1376 | 290 | 371 | -81 | 311 |

Tickers: SPX/SPY/QQQ/NDX appear inside feature names (A_<TK>_*, D_<TK>_*, W_<TK>_*, W_LAST_<TK>_*); B levels are SPX and NDX only (daily, prior day); C Tide is market-wide. Full per-cell tables: /mnt/l2/l2vast/_uw_score/screen2_<SET>.csv (top-8 cells per group).

## 4. Reading of the evidence
- RTH signals (first read) are chance-level against the family null. The strongest, repeated structure is the PRIOR-CLOSE prior for off-hours books: skip Asia entries when side x NDX charm(oi) at the prior close >= 3.59e12 (same feature and threshold on JN05W2 and JN05W2J; also SPX gamma_dir for LPB_BASE Asia and NDX gamma_dir for London cuts). It is a 2025-07+ pattern (PREUW negative), so recent-only, rule-2a candidate; exact sets TL3_UW_NDXCA_* test it.
- Placebo (forward-only shifted features) rank is not selection-adjusted; only the family null counts.

## 5. Exact stage (TP engine; score_nf vs JN05W2 / JN05W2J; windows present only)

TL3J_UW_SPXVDIR_PR vs JN05W2J
                 cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3J_UW_SPXVDIR_PR    L1M  5.2       307.9     1657.4  16938.1  17861.9    4288.2     14.0      6.6         14.0          6.5         56             57       6   244437.1    252234.4                0         21
1  TL3J_UW_SPXVDIR_PR    L3M  1.2      -476.7      406.3  17642.5  17861.9   15348.0     14.0      6.0         14.0          6.0        169            172       6   244437.1    252234.4                0         21
2  TL3J_UW_SPXVDIR_PR    L6M -1.5        87.5      507.4  24331.9  23965.2   21372.2     14.0      6.0         14.0          6.0        359            363       6   244437.1    252234.4                0         21
trend {'best5_ref': 244437.14000000796, 'best5_cell': 252234.36000000814, 'win_turn_losing': 0, 'win_weeks': 21}


TL3_UW_QQQGD15_PR vs JN05W2
                cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_QQQGD15_PR    L1M  2.1       380.4     -218.6  35614.7  36370.5     387.7     13.0      6.0         13.0          6.0         49             50       6   316288.0    332843.1                0         20
1  TL3_UW_QQQGD15_PR    L3M  2.1      1006.0     1810.2  35614.7  36370.5   17825.4     13.0      6.0         13.0          6.0        160            161       6   316288.0    332843.1                0         20
2  TL3_UW_QQQGD15_PR    L6M  2.1      1258.4     1656.3  35614.7  36370.5   26793.2     13.0      6.0         13.0          6.0        345            350       6   316288.0    332843.1                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 332843.14000000956, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_QQQGD15_SK vs JN05W2
                cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_QQQGD15_SK    L1M  0.0       288.8     -147.1  36370.5  36370.5     459.2     13.0      6.0         13.0          6.0         48             50       6   316288.0    307013.2                0         20
1  TL3_UW_QQQGD15_SK    L3M  0.0       821.2      155.3  36370.5  36370.5   16170.5     13.0      6.0         13.0          6.0        151            161       6   316288.0    307013.2                0         20
2  TL3_UW_QQQGD15_SK    L6M  0.0       219.6     -144.8  36370.5  36370.5   24992.1     13.0      6.0         13.0          6.0        335            350       6   316288.0    307013.2                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 307013.2400000095, 'win_turn_losing': 0, 'win_weeks': 20}


TL3_UW_TDNV_PR vs JN05W2
             cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UW_TDNV_PR    L1M  2.1      -706.4    -1484.8  35614.7  36370.5    -878.5     13.0      6.0         13.0          6.0         49             50       6   316288.0    319960.2                0         20
1  TL3_UW_TDNV_PR    L3M  2.1       -74.3      531.1  35614.7  36370.5   16546.3     13.0      6.0         13.0          6.0        160            161       6   316288.0    319960.2                0         20
2  TL3_UW_TDNV_PR    L6M  2.1      -150.5      200.1  35614.7  36370.5   25337.0     13.0      6.0         13.0          6.0        347            350       6   316288.0    319960.2                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 319960.1600000097, 'win_turn_losing': 0, 'win_weeks': 20}

