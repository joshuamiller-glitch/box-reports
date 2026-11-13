# DS3_UWBOOKS_B1 - Unusual Whales standalone books, families 1, 2, 6, 7 (W-UB1). Updated 2026-11-13 19:47Z by code/th_uwbooks/uwb_page.py (chained every 3 h). Research, shadow, NO PASS claim.

## 0. Status
Jobs done 2592 of 1232 (job = family x instrument x ticker x series, all its event kinds, both directions, 5 sessions, 1,470 grid cells). Group rows stored: 104671. Null draws (shifted-time, whole event table moved by random weeks): 12.
Instruments run: CL, ES, GC, NQ, RTY, SI, YM. RTY/YM wait for IWM/DIA UW pulls (W-UB3). X' has NO UW data (history starts 2024-10-01): X' is not scored. PRE is clipped to the UW start (PREUW). Windows from 2026-11-12.

## 1. Where the signal sits (gated = mean L6M>0 and L3M>0 and HOLD>0 and n_L6M>=20)
| family | instrument | matched | groups scored | groups with any gated cell | best gated L6M Calmar (dd floor $1,200) | max recents $/wk over cells ((L6M+HOLD)/2) |
|--|--|--|--|--|--|--|
| F1 | ES | False | 2686 | 1145 | 47.0 | 2740 |
| F1 | ES | True | 1328 | 541 | 42.2 | 3253 |
| F1 | NQ | False | 2756 | 1269 | 71.2 | 3716 |
| F1 | NQ | True | 1258 | 564 | 62.2 | 3112 |
| F1 | RTY | False | 3270 | 1397 | 74.2 | 3939 |
| F1 | RTY | True | 744 | 274 | 66.6 | 2285 |
| F1 | YM | False | 3330 | 1439 | 51.4 | 3109 |
| F1 | YM | True | 684 | 343 | 42.9 | 2601 |
| F2 | ES | False | 296 | 35 | 27.9 | 2060 |
| F2 | ES | True | 280 | 119 | 26.1 | 2331 |
| F2 | NQ | False | 280 | 74 | 69.9 | 2093 |
| F2 | NQ | True | 268 | 115 | 37.7 | 3712 |
| F2 | RTY | False | 584 | 156 | 31.2 | 1874 |
| F2 | YM | False | 582 | 92 | 26.0 | 1625 |
| F6 | ES | False | 724 | 536 | 40.4 | 1585 |
| F6 | ES | True | 356 | 227 | 29.9 | 1559 |
| F6 | NQ | False | 734 | 577 | 39.9 | 1674 |
| F6 | NQ | True | 348 | 235 | 32.7 | 1597 |
| F6 | RTY | False | 904 | 677 | 56.3 | 1919 |
| F6 | RTY | True | 180 | 121 | 66.3 | 1676 |
| F6 | YM | False | 892 | 659 | 53.5 | 1353 |
| F6 | YM | True | 192 | 140 | 37.3 | 1802 |
| F6B | ES | False | 16 | 16 | 24.7 | 1445 |
| F6B | NQ | False | 16 | 16 | 22.9 | 1271 |
| F6B | RTY | False | 16 | 15 | 27.7 | 1622 |
| F6B | YM | False | 16 | 16 | 31.8 | 1173 |
| F7 | ES | False | 920 | 804 | 49.2 | 3268 |
| F7 | ES | True | 464 | 403 | 30.4 | 2901 |
| F7 | NQ | False | 940 | 866 | 47.5 | 6005 |
| F7 | NQ | True | 444 | 421 | 41.4 | 5764 |
| F7 | RTY | False | 1146 | 985 | 43.9 | 1439 |
| F7 | RTY | True | 238 | 201 | 29.3 | 1406 |
| F7 | YM | False | 1146 | 1020 | 42.8 | 2931 |
| F7 | YM | True | 238 | 208 | 38.7 | 2747 |
| F7B | ES | False | 6 | 6 | 9.6 | 2673 |
| F7B | NQ | False | 6 | 6 | 12.1 | 5275 |
| F7B | RTY | False | 6 | 6 | 14.2 | 908 |
| F7B | YM | False | 6 | 5 | 14.6 | 2141 |
| FEB | CL | False | 42 | 32 | 20.2 | 1376 |
| FEB | GC | False | 24 | 21 | 40.2 | 1576 |
| FEB | SI | False | 18 | 17 | 29.3 | 1993 |
| PAIR | ES | False | 460 | 116 | 60.6 | 1968 |
| PAIR | ES | True | 48 | 6 | 24.8 | 996 |
| PAIR | NQ | False | 554 | 99 | 48.4 | 1819 |
| PAIR | NQ | True | 126 | 23 | 36.7 | 1801 |
| PAIR | RTY | False | 456 | 161 | 90.1 | 3345 |
| PAIR | YM | False | 252 | 45 | 52.8 | 2682 |

Null = the same event tables moved by a random circular whole-week shift inside their own date span (weekday/time of day kept, same windows), same job subset (every 4th job), full 1,470-cell grid, all 5 sessions x 2 directions. Columns: groups scored / groups with any gated cell (share) / max recents $/wk over all cells / best gated L6M Calmar. Observed is restricted to the same job subset.
| family | observed (same jobs) | null draw 1 | null draw 2 | null draw 3 | null draw 4 | null draw 5 | null draw 6 | null draw 7 | null draw 8 | null draw 9 | null draw 10 | null draw 11 | null draw 12 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| F1 | 4242 / 1759 (41%) / 2836 / 56.5 | 1778 / 970 (55%) / 2797 / 80.3 | 1760 / 963 (55%) / 2951 / 67.5 | 1756 / 981 (56%) / 3093 / 69.0 | 1536 / 993 (65%) / 2621 / 53.7 | 1552 / 981 (63%) / 2624 / 46.1 | 1552 / 989 (64%) / 3011 / 53.3 | n/a | n/a | n/a | 1732 / 1111 (64%) / 3077 / 79.3 | 1714 / 1148 (67%) / 2976 / 44.8 | 1724 / 1132 (66%) / 3197 / 61.8 |
| F2 | 528 / 94 (18%) / 2060 / 32.6 | 322 / 170 (53%) / 2813 / 47.5 | 318 / 163 (51%) / 3308 / 50.7 | 328 / 159 (48%) / 2421 / 39.2 | 220 / 102 (46%) / 2428 / 36.6 | 220 / 105 (48%) / 2287 / 25.4 | 214 / 102 (48%) / 2359 / 37.6 | n/a | n/a | n/a | n/a | n/a | n/a |
| F6 | 1072 / 809 (75%) / 1676 / 50.7 | 432 / 181 (42%) / 1746 / 49.6 | 436 / 189 (43%) / 1643 / 58.6 | 422 / 190 (45%) / 1401 / 56.4 | 536 / 255 (48%) / 1854 / 41.6 | 524 / 253 (48%) / 1980 / 42.7 | 538 / 242 (45%) / 1706 / 46.3 | n/a | n/a | n/a | 552 / 218 (39%) / 2170 / 81.0 | 540 / 239 (44%) / 1861 / 54.6 | 544 / 237 (44%) / 1702 / 32.6 |
| F6B | 64 / 63 (98%) / 1622 / 31.8 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| F7 | 1362 / 1212 (89%) / 5713 / 38.9 | 464 / 320 (69%) / 5911 / 59.5 | 460 / 309 (67%) / 3463 / 59.1 | 460 / 308 (67%) / 5252 / 45.5 | 754 / 493 (65%) / 2743 / 45.5 | 756 / 491 (65%) / 2636 / 49.0 | 752 / 491 (65%) / 3231 / 48.7 | n/a | n/a | n/a | 672 / 418 (62%) / 4320 / 44.1 | 666 / 418 (63%) / 4231 / 44.9 | 678 / 407 (60%) / 4595 / 44.6 |
| F7B | 2 / 2 (100%) / 839 / 9.6 | n/a | n/a | n/a | 2 / 2 (100%) / 1335 / 10.5 | 2 / 2 (100%) / 883 / 7.9 | 2 / 2 (100%) / 611 / 6.3 | n/a | n/a | n/a | n/a | n/a | n/a |
| FEB | 84 / 70 (83%) / 1993 / 40.2 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| PAIR | 1894 / 450 (24%) / 3345 / 90.1 | n/a | n/a | n/a | n/a | n/a | n/a | 2042 / 709 (35%) / 3138 / 71.6 | 2008 / 711 (35%) / 2718 / 81.6 | 2024 / 713 (35%) / 2613 / 123.9 | n/a | n/a | n/a |

## 2. Best book per session (gated; ranked by L6M Calmar = mean*52/maxDD). Window values are $/wk at the cell lots (R=$1,200 per trade at the stop, cap 10 lots), fees and measured slippage in.
| session | dir | family | instrument (matched) | trigger | cell | n L6M | L1M | L3M | L6M | HOLD | PREUW | maxDD L6M | worst wk L6M | full stops/wk L6M | pos wk L6M | WF OOS $/wk | placebo shuffle p | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | long | F2 | NQ (cross) | SPX oi|flip touch_up | Eb3_Sa1_Tnone_X120 | 20 | 124 | 1571 | 1637 | 659 | -204 | 1218 | -1218 | 0.30 | 0.79 | 172 | 0.15 | thin n=20; placebo p>0.1; null: see section 1 |
| london | long | F1 | YM (cross) | SPY v_oi lo_d | Emkt_Sa1_Tnone_X120 | 27 | 3968 | 2116 | 1249 | 642 | -254 | 1362 | -1188 | 0.44 | 0.80 | 49 | 0.03 | thin n=27; null: see section 1 |
| pre | short | F1 | NQ (cross) | SPX v_oi lo_d | Emkt_S30_T90_X60 | 24 | 4364 | 1983 | 1073 | 352 | 53 | 1275 | -1275 | 0.22 | 0.64 | 250 | 0.01 | thin n=24; null: see section 1 |
| nyam | short | F1 | RTY (cross) | SPX v_oi d15_dn | Eb3_Sa1_T90_XSE | 44 | 2012 | 1377 | 1771 | 693 | 106 | 1241 | -1241 | 0.56 | 0.73 | 416 | 0.05 | no flag yet; null: see section 1 |
| nypm | short | F1 | NQ (cross) | DIA g_dir d5_up | Ep10_Sa2_Tnone_XSE | 38 | 1570 | 1163 | 2014 | 1113 | -226 | 1470 | -1470 | 0.19 | 0.73 | 353 | 0.10 | thin n=38; null: see section 1 |

Spec decoding: cell Ex_Sy_Tz_Xw = entry mode x, stop y, target z, time exit w (NQ-point lists scaled by the instrument ATR ratio, a1/a2 = 1x/2x ATR14 of 5-min bars; XSE = session end, flat). Trigger names: see UWBOOKS_B1_PREREG.md.

## 3. Finalist detail (top 3 per session, re-simulated; WF = bi-weekly re-pick over all 1,470 cells of the group, trail 26 wk; placebo = shuffled-day events, B=20: p = share of draws whose best-cell recents >= the group best-cell recents)
| session | dir | inst | trigger | cell | spec entry | stop | target | time exit | L6M | HOLD | stress L6M / HOLD (2x slip, label only) | WF mean $/wk | WF maxDD | WF worst | WF periods positive | placebo q95 | placebo p (B=100) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | 1 | NQ | F2 SPX oi|flip touch_up | Eb3_Sa1_Tnone_X120 | enter at +3 min if price moved in direction | 1 x ATR5 | none | 120 min | 1637 | 659 | 1617 / 637 | 172 | 11501 | -1814 | 0.44 | 1589 | 0.15 |
| asia | 1 | NQ | F2 SPX oi|flip touch_up | Eb3_Sa1_T90_X120 | enter at +3 min if price moved in direction | 1 x ATR5 | 90 NQ-pts x 1.00 = 90.0 NQ pts | 120 min | 1512 | 656 | 1497 / 637 | 172 | 11501 | -1814 | 0.44 | 1589 | 0.15 |
| asia | -1 | ES | F7 QQQ g_dir|asia1805 med_hi | Eb3_S45_Tnone_XSE | enter at +3 min if price moved in direction | 45 NQ-pts x 0.19 = 8.6 ES pts | none | session end | 1274 | 670 | 1220 / 580 | -232 | 20903 | -3467 | 0.32 | 2376 | 0.04 |
| london | 1 | YM | F1 SPY v_oi lo_d | Emkt_Sa1_Tnone_X120 | market at t0+1s | 1 x ATR5 | none | 120 min | 1249 | 642 | 1086 / 488 | 49 | 5343 | -2666 | 0.22 | 813 | 0.03 |
| london | 1 | YM | F1 SPY v_oi lo_d | Emkt_Sa1_Tnone_XSE | market at t0+1s | 1 x ATR5 | none | session end | 1249 | 642 | 1086 / 488 | 49 | 5343 | -2666 | 0.22 | 813 | 0.03 |
| london | 1 | ES | F1 QQQ g_oi d1_up | Ep10_Sa2_Tnone_XSE | limit pullback 10 NQ-pts | 2 x ATR5 | none | session end | 1130 | 472 | 1034 / 415 | 195 | 3541 | -1488 | 0.42 | 702 | 0.03 |
| nyam | -1 | RTY | F1 SPX v_oi d15_dn | Eb3_Sa1_T90_XSE | enter at +3 min if price moved in direction | 1 x ATR5 | 90 NQ-pts x 0.10 = 9.4 RTY pts | session end | 1767 | 690 | 1745 / 575 | 416 | 18668 | -6649 | 0.57 | 2477 | 0.05 |
| nyam | -1 | RTY | F1 SPX v_oi d15_dn | Eb3_Sa1_T90_X120 | enter at +3 min if price moved in direction | 1 x ATR5 | 90 NQ-pts x 0.10 = 9.4 RTY pts | 120 min | 1767 | 690 | 1745 / 575 | 416 | 18668 | -6649 | 0.57 | 2477 | 0.05 |
| nyam | -1 | RTY | F1 IWM v_oi hi_d | Eb5_S30_T60_XSE | enter at +5 min if price moved in direction | 30 NQ-pts x 0.10 = 3.1 RTY pts | 60 NQ-pts x 0.10 = 6.3 RTY pts | session end | 1703 | 1015 | 1672 / 970 | 183 | 16483 | -3872 | 0.58 | 2639 | 0.17 |
| nypm | -1 | NQ | F1 DIA g_dir d5_up | Ep10_Sa2_Tnone_XSE | limit pullback 10 NQ-pts | 2 x ATR5 | none | session end | 2014 | 1113 | 2000 / 1099 | 353 | 8533 | -3641 | 0.55 | 1724 | 0.10 |
| nypm | -1 | NQ | F1 NDX c_dir d1_dn | Ep10_S60_Tnone_XSE | limit pullback 10 NQ-pts | 60 NQ-pts x 1.00 = 60.0 NQ pts | none | session end | 1473 | 974 | 1460 / 962 | 524 | 2738 | -1976 | 0.63 | 2049 | 0.33 |
| nypm | -1 | NQ | F1 DIA g_dir d15_up | Ep5_Sa2_Tnone_XSE | limit pullback 5 NQ-pts | 2 x ATR5 | none | session end | 1334 | 415 | 1321 / 403 | -44 | 7376 | -2455 | 0.36 | 1662 | 0.98 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_X60 | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | 60 min | 1073 | 352 | 961 / 286 | 250 | 3773 | -1417 | 0.35 | 458 | 0.01 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_XSE | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | session end | 1073 | 352 | 961 / 286 | 250 | 3773 | -1417 | 0.35 | 458 | 0.01 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_X120 | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | 120 min | 1073 | 352 | 961 / 286 | 250 | 3773 | -1417 | 0.35 | 458 | 0.01 |

## 3b. First-order joint (finalist weekly $ added to the live stack S1B-COMB weekly, own lots; exact-engine joint via TP sets TL3_UW_* follows)
| finalist id | corr KB/PE/SM/HM/MV/PB/OD | corr stack | stack maxDD L6M -> with | stack worst wk L6M -> with | cand mean L6M | weeks trading |
|--|--|--|--|--|--|--|
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_T90_XSE | 0.08/0.07/0.04/-0.10/-0.16/0.06/0.01 | 0.04 | 79907 -> 79727 | -62941 -> -64220 | 1130 | 42 |
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_Tnone_X120 | 0.07/0.14/0.10/-0.09/-0.06/0.09/0.02 | 0.12 | 79907 -> 79727 | -62941 -> -64220 | 1173 | 42 |
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_Tnone_XSE | 0.07/0.14/0.10/-0.09/-0.06/0.09/0.02 | 0.12 | 79907 -> 79727 | -62941 -> -64220 | 1173 | 42 |
| F1_NQ_DIA_g_dir_d15_up_nypm_-1_Ep5_Sa2_Tnone_XSE | 0.01/0.12/-0.02/0.14/0.03/0.04/-0.08 | 0.11 | 79907 -> 79940 | -62941 -> -63988 | 1385 | 84 |
| F1_NQ_DIA_g_dir_d5_up_nypm_-1_Ep10_Sa2_Tnone_XSE | 0.07/0.21/0.15/0.10/0.04/0.11/-0.10 | 0.22 | 79907 -> 81378 | -62941 -> -61260 | 2091 | 86 |
| F1_NQ_NDX_c_dir_d1_dn_nypm_-1_Ep10_S45_Tnone_XSE | 0.03/0.11/0.14/0.05/-0.11/0.10/-0.15 | 0.10 | 79907 -> 79194 | -62941 -> -63855 | 1196 | 61 |
| F1_NQ_NDX_c_dir_d1_dn_nypm_-1_Ep10_S60_Tnone_XSE | 0.02/0.10/0.13/0.05/-0.14/0.09/-0.15 | 0.08 | 79907 -> 79194 | -62941 -> -59795 | 1426 | 61 |
| F1_NQ_QQQ_c_oi_hi_d_nyam_1_Ep10_S30_Tnone_X60 | 0.04/-0.03/-0.00/0.02/-0.02/-0.09/-0.08 | -0.02 | 79907 -> 74395 | -62941 -> -62941 | 1395 | 31 |
| F1_NQ_QQQ_v_dir_d15_up_nyam_-1_Eb3_S30_Tnone_X120 | 0.04/0.12/0.06/0.07/0.00/-0.09/-0.13 | 0.11 | 79907 -> 78451 | -62941 -> -64168 | 3140 | 47 |
| F1_NQ_QQQ_v_dir_d15_up_nyam_-1_Eb3_S30_Tnone_XSE | 0.04/0.12/0.06/0.07/0.00/-0.09/-0.13 | 0.11 | 79907 -> 78451 | -62941 -> -64168 | 3135 | 47 |
| F1_NQ_SPX_v_oi_lo_d_pre_-1_Emkt_S30_T90_X120 | 0.13/0.08/-0.02/-0.02/0.11/-0.10/-0.08 | 0.08 | 79907 -> 79907 | -62941 -> -59351 | 1117 | 73 |
| F1_NQ_SPX_v_oi_lo_d_pre_-1_Emkt_S30_T90_X60 | 0.13/0.08/-0.02/-0.02/0.11/-0.10/-0.08 | 0.08 | 79907 -> 79907 | -62941 -> -59351 | 1117 | 73 |
| F1_NQ_SPX_v_oi_lo_d_pre_-1_Emkt_S30_T90_XSE | 0.13/0.08/-0.02/-0.02/0.11/-0.10/-0.08 | 0.08 | 79907 -> 79907 | -62941 -> -59351 | 1117 | 73 |
| F1_NQ_SPY_v_vol_d15_up_nypm_-1_Ep10_Sa2_T60_XSE | 0.03/0.02/0.11/0.10/-0.02/0.01/-0.05 | 0.05 | 79907 -> 76926 | -62941 -> -60551 | 1229 | 97 |
| F1_RTY_IWM_v_oi_hi_d_nyam_-1_Eb5_S30_T60_XSE | 0.01/0.15/0.07/0.09/-0.13/0.14/0.03 | 0.13 | 79907 -> 78774 | -62941 -> -58014 | 1710 | 97 |
| F1_RTY_SPX_v_oi_d15_dn_nyam_-1_Eb3_Sa1_T90_X120 | 0.12/0.06/-0.03/0.04/0.06/0.02/0.11 | 0.08 | 79907 -> 78606 | -62941 -> -57369 | 1688 | 102 |
| F1_RTY_SPX_v_oi_d15_dn_nyam_-1_Eb3_Sa1_T90_XSE | 0.12/0.06/-0.03/0.04/0.07/0.02/0.11 | 0.08 | 79907 -> 78606 | -62941 -> -57369 | 1688 | 102 |
| F1_YM_SPY_v_oi_lo_d_london_1_Emkt_Sa1_Tnone_X120 | 0.05/-0.06/0.07/0.03/-0.11/-0.07/-0.17 | -0.04 | 79907 -> 79907 | -62941 -> -55540 | 1260 | 63 |
| F1_YM_SPY_v_oi_lo_d_london_1_Emkt_Sa1_Tnone_XSE | 0.05/-0.06/0.07/0.03/-0.11/-0.07/-0.17 | -0.04 | 79907 -> 79907 | -62941 -> -55540 | 1260 | 63 |
| F2_NQ_SPX_oi-flip_touch_up_asia_1_Eb3_Sa1_T90_X120 | -0.05/-0.01/0.01/0.11/0.06/0.06/-0.01 | 0.01 | 79907 -> 79907 | -62941 -> -58836 | 1444 | 52 |
| F2_NQ_SPX_oi-flip_touch_up_asia_1_Eb3_Sa1_Tnone_X120 | -0.04/0.05/0.04/0.11/0.08/0.05/0.01 | 0.07 | 79907 -> 79907 | -62941 -> -59148 | 1574 | 52 |
| F7_ES_QQQ_g_dir-asia1805_med_hi_asia_-1_Eb3_S45_Tnone_XSE | -0.01/0.17/0.11/0.11/0.10/0.09/0.01 | 0.18 | 79907 -> 79907 | -62941 -> -64286 | 1375 | 74 |
| FEB_CL_NONE_cl_pit_open_all_pit_1_Emkt_S90_Tnone_XSE | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |
| FEB_CL_NONE_ny_open_dn_pit_1_Emkt_S45_Tnone_XSE | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |
| FEB_CL_NONE_ny_open_dn_pit_1_Emkt_Sa2_Tnone_XSE | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |

## 6. No-UW baseline of the F6/F7 entry clocks (same harness/grid/gate; F7B = every business day at the clock, F6B = price move only) vs the UW-conditioned tables
| instrument | clock family | no-UW baseline: groups / gated (share) / max recents / best Calmar | UW-conditioned: groups / gated (share) / max recents / best Calmar |
|--|--|--|--|
| NQ | F6 | 16 / 16 (100%) / 1271 / 22.9 | 1082 / 812 (75%) / 1674 / 39.9 |
| NQ | F7 | 6 / 6 (100%) / 5275 / 12.1 | 1384 / 1287 (93%) / 6005 / 47.5 |
| ES | F6 | 16 / 16 (100%) / 1445 / 24.7 | 1080 / 763 (71%) / 1585 / 40.4 |
| ES | F7 | 6 / 6 (100%) / 2673 / 9.6 | 1384 / 1207 (87%) / 3268 / 49.2 |
| RTY | F6 | 16 / 15 (94%) / 1622 / 27.7 | 1084 / 798 (74%) / 1919 / 66.3 |
| RTY | F7 | 6 / 6 (100%) / 908 / 14.2 | 1384 / 1186 (86%) / 1439 / 43.9 |
| YM | F6 | 16 / 16 (100%) / 1173 / 31.8 | 1084 / 799 (74%) / 1802 / 53.5 |
| YM | F7 | 6 / 5 (83%) / 2141 / 14.6 | 1384 / 1228 (89%) / 2931 / 42.8 |

## 6b. Which instrument carries each trigger ticker best (all single-trigger families; gated share of groups / best gated L6M Calmar with $1,200 dd floor; * = matched instrument)
| trigger ticker | NQ | ES | RTY | YM | GC | SI | CL |
|--|--|--|--|--|--|--|--|
| DIA | 68% / 71.2 | 63% / 47.0 | 61% / 51.8 | *62% / 42.9 | - | - | - |
| IWM | 58% / 48.4 | 53% / 45.1 | *51% / 66.6 | 55% / 53.5 | - | - | - |
| NDX | *55% / 60.9 | 47% / 45.7 | 49% / 58.3 | 48% / 45.7 | - | - | - |
| QQQ | *60% / 62.2 | 55% / 49.2 | 57% / 56.3 | 58% / 41.9 | - | - | - |
| SPX | 56% / 69.9 | *54% / 35.7 | 53% / 74.2 | 54% / 42.8 | - | - | - |
| SPY | 56% / 56.5 | *52% / 42.2 | 52% / 43.9 | 56% / 51.4 | - | - | - |

## 7. Pairs of the top-20 singles per instrument (AND within 15 min, event = later one; no pair uses a table twice). Null = table B of each pair moved by a circular whole-week shift (A kept), same pairs.
| instrument | observed pairs: groups / gated (share) / max recents / best Calmar | null draw 1 | null draw 2 | null draw 3 |
|--|--|--|--|--|
| NQ | 680 / 122 (18%) / 1819 / 48.4 | 748 / 261 (35%) / 2312 / 71.6 | 730 / 259 (35%) / 2185 / 73.6 | 740 / 261 (35%) / 2238 / 123.9 |
| ES | 508 / 122 (24%) / 1968 / 60.6 | 504 / 173 (34%) / 2583 / 66.5 | 498 / 178 (36%) / 2338 / 81.6 | 498 / 171 (34%) / 2397 / 72.2 |
| RTY | 456 / 161 (35%) / 3345 / 90.1 | 506 / 229 (45%) / 3138 / 63.7 | 500 / 220 (44%) / 2718 / 61.3 | 502 / 227 (45%) / 2613 / 73.2 |
| YM | 252 / 45 (18%) / 2682 / 52.8 | 284 / 46 (16%) / 1493 / 32.8 | 280 / 54 (19%) / 2528 / 48.8 | 284 / 54 (19%) / 1730 / 43.7 |

Best pair rows per session (in-sample on the same 2 years; WF/placebo not run on pairs):
| session | dir | instrument | pair | cell | n L6M | L1M | L3M | L6M | HOLD | PREUW | maxDD L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|
| nyam | short | RTY | SPX:v_oi+QQQ:v_oi F1/d15_dn+F1/d5_up | Ep3_S45_Tnone_XSE | 60 | 2800 | 1141 | 3107 | 1487 | -79 | 1793 |
| nyam | short | RTY | SPX:v_oi+NDX:v_dir F1/d15_dn+F1/lo_d | Emkt_S30_Ta2_X60 | 45 | 1722 | 1603 | 2277 | 1603 | 171 | 1332 |
| nypm | short | NQ | SPY:v_vol+QQQ:v_vol F1/d15_up+F1/d5_up | Emkt_S90_T45_XSE | 57 | 2103 | 950 | 1117 | 862 | 357 | 528 |
| nypm | short | NQ | SPY:v_vol+QQQ:v_vol F1/d15_up+F1/d5_up | Ep10_S90_T90_XSE | 44 | 2663 | 1389 | 1173 | 533 | 370 | 1276 |
| asia | long | ES | QQQ:c_dir|asia1805+QQQ:c_oi|asia1805 F7/med_hi+F7/med_lo | Emkt_S30_Tnone_XSE | 26 | 1697 | 2227 | 1896 | 658 | -111 | 2440 |
| london | long | YM | SPY:c_dir|lon0200+SPX:c_oi|lon0200 F7/chg_dn+F7/med_hi | Emkt_S30_Tnone_XSE | 30 | 4532 | 3534 | 2188 | 1178 | 147 | 2864 |
| london | long | YM | SPY:c_dir|lon0200+SPX:c_oi|lon0200 F7/neg+F7/med_hi | Emkt_S30_Tnone_XSE | 30 | 4532 | 3534 | 2188 | 1178 | 147 | 2864 |
| asia | long | ES | QQQ:c_dir|asia1805+QQQ:c_oi|asia1805 F7/med_hi+F7/med_lo | Emkt_S45_Tnone_XSE | 26 | 1187 | 1729 | 1499 | 430 | -275 | 2693 |

## 4. Data honesty (lags; no-look-ahead proof, sample day per family)
LAG (spot_1m QQQ 2026-10-14): row time - start_time: min 0 s, median 58 s, max 59 s (snapshot taken inside the minute); avail used = start+60 s (>= snapshot time by construction) + EXTRA_LAG 60 s
F1 panel vs raw g_dir on 2026-10-14: 494 common minutes, max abs diff 0 (0 = identical)
F1 first d1_dn event 13:30:00 ET: decision ts 1791999000 = last used row avail 1791998940 (+60 s lag); value 5.541e+08 vs 15 min earlier 5.58e+08; entry fill path starts at ts+1 s (harness.simulate market = mid at t0+1)
  check: raw row avail <= decision ts: True ; no raw row with avail > decision ts - 60 is used
F2 gex_levels_oi SPX file 2026-10-14 computed at 2026-10-14T20:15:00.000000Z (end of day); used only for sessions starting 18:00 ET 2026-10-14 onward (label day next business day); same-day sessions of 2026-10-14 use the PRIOR file
F6 10:00 ET reading for 2026-10-14: row avail 10:00:00 ET (<= 10:00:00), value -3.161e+08; event ts = 10:00 + 60 s lag
F7 prior-close reading of 2026-10-14: row avail 16:00:00 ET (start 15:59); event 18:05 ET same date (Friday -> Sunday 18:05) + lag; London 02:00 ET next business day; pre-market 06:35 ET uses rows avail <= 06:35

## 5. Plain reading
PLAIN READING (updated 17:20Z; B2 NQ+ES, B3 RTY+YM, B4 pairs, B5 no-UW baselines). STRENGTH: WEAK everywhere; no book is distinguishable from chance after selection.
- Singles (families 1,2,6,7): per-session best books are listed in section 2 (thin n 20-47, placebo p 0.05-0.29). The shifted-time null reaches the same best recents and Calmar in F1 and F2 on NQ/ES, and the gated share is lower than null (F1 37% vs 55%, F2 21% vs 50%). RTY and YM crosses (SPX/SPY/QQQ/NDX triggers) look the same (gated share F1 41-44%, F2 16-27%, no null run there yet).
- F6/F7 clocks: the NO-UW baseline (same clock, no UW condition) passes the gate in 83-100% of its groups on every instrument, MORE than the UW-conditioned tables (66-94%). The apparent excess over the shifted null is the clock/market drift of the 2024-26 sample (overnight and morning legs of a rising market), not the UW reading. UW conditioning does not add a measurable lift here.
- Pairs (AND within 15 min of the top-20 singles per instrument, 741 pairs): observed gated share 18-35% vs null 16-45%, max recents and best Calmar inside the null range on all four instruments (RTY best Calmar 90 vs 61-73 null is the only excess, one group). No pair is a survivor.
- Not done yet: IWM/DIA matched runs (B6 running; IWM history starts 2024-12-23), IWM/DIA level files for F2, metals/oil (GC/SI/CL with GLD/GDX/SLV/USO/XLE/XOP, after the six tickers are pulled), exact-engine joint (needs an add-a-book hook; question in MORNING), WF/placebo B=100 for the final list by the 18:45Z cycle.
- Simulator audit: an independent naive second-by-second loop (entry modes market / +3 min confirm / 5-pt pullback, stops, targets, time exits, 08:30 slippage) reproduced the vectorised harness on 198 of 198 random event x cell checks (1-s resolution region, exit < 2 h).
- Update 17:55Z: IWM/DIA run (B6, 608 jobs on NQ/ES/RTY/YM) shows the same picture; matched instruments (section 6b) do not carry their trigger better than the crosses (gated share 51-62% matched vs 47-68% cross). Metals/oil: FEB clock baselines run; UW-conditioned FE/F1/F6/F7 wait for the GLD/GDX/SLV/USO/XLE/XOP spot_1m pulls (about 20 of ~500 days each at 17:48Z).
- Placebo (shuffled-day events, B=100, group best-cell recents vs the same statistic on shuffled days): finalists reach p 0.01-0.05 for pre short SPX v_oi lo_d (NQ, 0.01), london long SPY v_oi lo_d (YM, 0.03) and QQQ g_oi d1_up (ES, 0.03), asia short QQQ g_dir med_hi (ES, 0.04), nyam short SPX v_oi d15_dn (RTY, 0.05); others 0.10-0.98. With ~40k scored groups, ~2,000 groups would show p<=0.05 by chance, and the family-level shifted-time null is not beaten: these are named as best-per-session candidates, not survivors. 2x-slippage stress cuts L6M by only 1-12% (entries are market/limit at tick-scale slips on large-ATR stops), so costs are not what limits them.
