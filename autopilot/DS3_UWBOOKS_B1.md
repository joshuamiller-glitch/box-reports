# DS3_UWBOOKS_B1 - Unusual Whales standalone books, families 1, 2, 6, 7 (W-UB1). Updated 2026-11-13 23:06Z by code/th_uwbooks/uwb_page.py (chained every 3 h). Research, shadow, NO PASS claim.

## 0. Status
Jobs done 4279 of 1232 (job = family x instrument x ticker x series, all its event kinds, both directions, 5 sessions, 1,470 grid cells). Group rows stored: 195897. Null draws (shifted-time, whole event table moved by random weeks): 18.
Instruments run: CL, ES, GC, NQ, RTY, SI, YM. RTY/YM wait for IWM/DIA UW pulls (W-UB3). X' has NO UW data (history starts 2024-10-01): X' is not scored. PRE is clipped to the UW start (PREUW). Windows from 2026-11-12.

## 1. Where the signal sits (gated = mean L6M>0 and L3M>0 and HOLD>0 and n_L6M>=20)
| family | instrument | matched | groups scored | groups with any gated cell | best gated L6M Calmar (dd floor $1,200) | max recents $/wk over cells ((L6M+HOLD)/2) |
|--|--|--|--|--|--|--|
| F1 | CL | True | 2766 | 1330 | 51.2 | 2771 |
| F1 | ES | False | 6760 | 2929 | 61.5 | 3097 |
| F1 | ES | True | 1328 | 541 | 42.2 | 3253 |
| F1 | GC | True | 1490 | 663 | 62.4 | 2494 |
| F1 | NQ | False | 6830 | 3176 | 71.2 | 3716 |
| F1 | NQ | True | 1258 | 564 | 62.2 | 3112 |
| F1 | RTY | False | 3270 | 1397 | 74.2 | 3939 |
| F1 | RTY | True | 744 | 274 | 66.6 | 2285 |
| F1 | SI | True | 642 | 277 | 48.6 | 2421 |
| F1 | YM | False | 3330 | 1439 | 51.4 | 3109 |
| F1 | YM | True | 684 | 343 | 42.9 | 2601 |
| F2 | CL | True | 1044 | 214 | 70.6 | 1725 |
| F2 | ES | False | 850 | 108 | 27.9 | 2060 |
| F2 | ES | True | 280 | 119 | 26.1 | 2331 |
| F2 | GC | True | 534 | 113 | 43.3 | 2510 |
| F2 | NQ | False | 856 | 165 | 69.9 | 2093 |
| F2 | NQ | True | 268 | 115 | 37.7 | 3712 |
| F2 | RTY | False | 874 | 209 | 31.2 | 1874 |
| F2 | RTY | True | 278 | 80 | 38.6 | 1431 |
| F2 | SI | True | 274 | 80 | 26.7 | 2333 |
| F2 | YM | False | 854 | 123 | 31.6 | 1649 |
| F2 | YM | True | 286 | 87 | 43.6 | 1514 |
| F6 | CL | True | 1084 | 671 | 46.7 | 2014 |
| F6 | ES | False | 1832 | 1387 | 52.1 | 1747 |
| F6 | ES | True | 356 | 227 | 29.9 | 1559 |
| F6 | GC | True | 374 | 279 | 29.1 | 915 |
| F6 | NQ | False | 1842 | 1505 | 82.9 | 1852 |
| F6 | NQ | True | 348 | 235 | 32.7 | 1597 |
| F6 | RTY | False | 904 | 677 | 56.3 | 1919 |
| F6 | RTY | True | 180 | 121 | 66.3 | 1676 |
| F6 | SI | True | 172 | 128 | 38.6 | 1155 |
| F6 | YM | False | 892 | 659 | 53.5 | 1353 |
| F6 | YM | True | 192 | 140 | 37.3 | 1802 |
| F6B | ES | False | 16 | 16 | 24.7 | 1445 |
| F6B | NQ | False | 16 | 16 | 22.9 | 1271 |
| F6B | RTY | False | 16 | 15 | 27.7 | 1622 |
| F6B | YM | False | 16 | 16 | 31.8 | 1173 |
| F7 | CL | True | 686 | 654 | 47.1 | 1940 |
| F7 | ES | False | 2298 | 2052 | 58.2 | 3268 |
| F7 | ES | True | 464 | 403 | 30.4 | 2901 |
| F7 | GC | True | 464 | 442 | 53.9 | 2665 |
| F7 | NQ | False | 2318 | 2194 | 51.1 | 6195 |
| F7 | NQ | True | 444 | 421 | 41.4 | 5764 |
| F7 | RTY | False | 1146 | 985 | 43.9 | 1439 |
| F7 | RTY | True | 238 | 201 | 29.3 | 1406 |
| F7 | SI | True | 236 | 214 | 34.1 | 2756 |
| F7 | YM | False | 1146 | 1020 | 42.8 | 2931 |
| F7 | YM | True | 238 | 208 | 38.7 | 2747 |
| F7B | ES | False | 6 | 6 | 9.6 | 2673 |
| F7B | NQ | False | 6 | 6 | 12.1 | 5275 |
| F7B | RTY | False | 6 | 6 | 14.2 | 908 |
| F7B | YM | False | 6 | 5 | 14.6 | 2141 |
| FE | CL | True | 252 | 147 | 22.1 | 1344 |
| FE | GC | True | 168 | 132 | 39.2 | 1213 |
| FE | SI | True | 36 | 35 | 52.4 | 1514 |
| FEB | CL | False | 42 | 32 | 20.2 | 1376 |
| FEB | GC | False | 24 | 21 | 40.2 | 1576 |
| FEB | SI | False | 18 | 17 | 29.3 | 1993 |
| PAIR | ES | False | 460 | 116 | 60.6 | 1968 |
| PAIR | ES | True | 48 | 6 | 24.8 | 996 |
| PAIR | NQ | False | 554 | 99 | 48.4 | 1819 |
| PAIR | NQ | True | 126 | 23 | 36.7 | 1801 |
| PAIR | RTY | False | 456 | 161 | 90.1 | 3345 |
| PAIR | YM | False | 252 | 45 | 52.8 | 2682 |

Null draws pool the same event tables for all instruments (NQ/ES, RTY/YM, IWM/DIA, metals/oil, cross tickers) = the same event tables moved by a random circular whole-week shift inside their own date span (weekday/time of day kept, same windows), same job subset (every 4th job), full 1,470-cell grid, all 5 sessions x 2 directions. Columns: groups scored / groups with any gated cell (share) / max recents $/wk over all cells / best gated L6M Calmar. Observed is restricted to the same job subset.
| family | observed (same jobs) | null draw 1 | null draw 2 | null draw 3 |
|--|--|--|--|--|
| F1 | 7142 / 3062 (43%) / 2836 / 62.5 | 8362 / 5195 (62%) / 3077 / 80.3 | 8348 / 5206 (62%) / 3223 / 67.5 | 8352 / 5223 (63%) / 3197 / 69.0 |
| F2 | 1396 / 293 (21%) / 2060 / 33.8 | 1410 / 725 (51%) / 3633 / 61.7 | 1410 / 702 (50%) / 3964 / 56.1 | 1410 / 716 (51%) / 3380 / 63.5 |
| F6 | 1994 / 1518 (76%) / 1826 / 50.7 | 2862 / 1268 (44%) / 2547 / 81.0 | 2828 / 1298 (46%) / 2810 / 58.6 | 2844 / 1259 (44%) / 1914 / 56.4 |
| F6B | 64 / 63 (98%) / 1622 / 31.8 | n/a | n/a | n/a |
| F7 | 2280 / 2075 (91%) / 6195 / 58.2 | 3174 / 2061 (65%) / 5911 / 63.2 | 3194 / 2056 (64%) / 5314 / 59.1 | 3192 / 2039 (64%) / 5252 / 48.7 |
| F7B | 2 / 2 (100%) / 839 / 9.6 | 2 / 2 (100%) / 1335 / 10.5 | 2 / 2 (100%) / 883 / 7.9 | 2 / 2 (100%) / 611 / 6.3 |
| FE | 142 / 112 (79%) / 1378 / 52.4 | 276 / 92 (33%) / 1359 / 26.5 | 272 / 88 (32%) / 1940 / 32.4 | 270 / 85 (31%) / 1581 / 38.4 |
| FEB | 54 / 41 (76%) / 1445 / 35.5 | 106 / 43 (41%) / 2181 / 45.5 | 104 / 47 (45%) / 1222 / 36.1 | 104 / 49 (47%) / 1472 / 33.8 |
| PAIR | 1894 / 450 (24%) / 3345 / 90.1 | 2042 / 709 (35%) / 3138 / 71.6 | 2008 / 711 (35%) / 2718 / 81.6 | 2024 / 713 (35%) / 2613 / 123.9 |

## 2. Best book per session (gated; ranked by L6M Calmar = mean*52/maxDD). Window values are $/wk at the cell lots (R=$1,200 per trade at the stop, cap 10 lots), fees and measured slippage in.
| session | dir | family | instrument (matched) | trigger | cell | n L6M | L1M | L3M | L6M | HOLD | PREUW | maxDD L6M | worst wk L6M | full stops/wk L6M | pos wk L6M | WF OOS $/wk | placebo shuffle p | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | long | F2 | NQ (cross) | SPX oi|flip touch_up | Eb3_Sa1_Tnone_X120 | 20 | 124 | 1571 | 1637 | 659 | -204 | 1218 | -1218 | 0.30 | 0.79 | 172 | 0.15 | thin n=20; placebo p>0.1; null: see section 1 |
| london | long | FE | SI (matched) | SLV g_oi|lbma_silver hi_dn | Ep5_Sa2_T30_XSE | 39 | 1180 | 1431 | 1209 | 566 | n/a | 1137 | -1137 | 0.19 | 0.87 | 280 | 0.01 | thin n=39; null: see section 1 |
| pre | short | F1 | NQ (cross) | SPX v_oi lo_d | Emkt_S30_T90_XSE | 24 | 4364 | 1983 | 1073 | 352 | 53 | 1275 | -1275 | 0.22 | 0.64 | 250 | 0.01 | thin n=24; null: see section 1 |
| nyam | short | F6 | NQ (cross) | GLD g_oi|0930|0830|med lo_up | Ep5_S30_Tnone_X15 | 29 | 1110 | 698 | 1957 | 931 | n/a | 1227 | -1227 | 0.56 | 0.73 | 156 | 0.12 | thin n=29; placebo p>0.1; null: see section 1 |
| nypm | short | F1 | NQ (cross) | DIA g_dir d5_up | Ep10_Sa2_Tnone_XSE | 38 | 1570 | 1163 | 2014 | 1113 | -226 | 1470 | -1470 | 0.19 | 0.73 | 353 | 0.10 | thin n=38; null: see section 1 |
| pit | long | F2 | CL (matched) | XOP oi|magnet touch_dn | Emkt_S45_Tnone_X120 | 23 | 856 | 2410 | 1757 | 802 | n/a | 1295 | -1295 | 0.30 | 0.93 | n/a | 0.01 | thin n=23; null: see section 1 |

Spec decoding: cell Ex_Sy_Tz_Xw = entry mode x, stop y, target z, time exit w (NQ-point lists scaled by the instrument ATR ratio, a1/a2 = 1x/2x ATR14 of 5-min bars; XSE = session end, flat). Trigger names: see UWBOOKS_B1_PREREG.md.

## 3. Finalist detail (top 3 per session, re-simulated; WF = bi-weekly re-pick over all 1,470 cells of the group, trail 26 wk; placebo = shuffled-day events, B=20: p = share of draws whose best-cell recents >= the group best-cell recents)
| session | dir | inst | trigger | cell | spec entry | stop | target | time exit | L6M | HOLD | stress L6M / HOLD (2x slip, label only) | WF mean $/wk | WF maxDD | WF worst | WF periods positive | placebo q95 | placebo p (B=100) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | 1 | NQ | F2 SPX oi|flip touch_up | Eb3_Sa1_Tnone_X120 | enter at +3 min if price moved in direction | 1 x ATR5 | none | 120 min | 1637 | 659 | 1617 / 637 | 172 | 11501 | -1814 | 0.44 | 1589 | 0.15 |
| asia | 1 | NQ | F2 SPX oi|flip touch_up | Eb3_Sa1_T90_X120 | enter at +3 min if price moved in direction | 1 x ATR5 | 90 NQ-pts x 1.00 = 90.0 NQ pts | 120 min | 1512 | 656 | 1497 / 637 | 172 | 11501 | -1814 | 0.44 | 1589 | 0.15 |
| asia | 1 | ES | F7 XOP c_oi|asia1805 med_hi | Eb5_S30_Tnone_XSE | enter at +5 min if price moved in direction | 30 NQ-pts x 0.19 = 5.7 ES pts | none | session end | 1365 | 639 | 1303 / 485 | 221 | 7453 | -2413 | 0.46 | 1305 | 0.09 |
| asia | -1 | GC | F7 GLD v_oi|asia1805 med_lo | Ep5_S30_Tnone_XSE | limit pullback 5 NQ-pts | 30 NQ-pts x 0.19 = 5.7 GC pts | none | session end | 2432 | 345 | 2394 / 306 | 75 | 7790 | -3752 | 0.35 | 2585 | 0.42 |
| asia | -1 | CL | F7 USO c_oi|asia1805 chg_dn | Eb1_Sa2_T90_XSE | enter at +1 min if price moved in direction | 2 x ATR5 | 90 NQ-pts x 0.01 = 0.6 CL pts | session end | 1264 | 311 | 1242 / 205 | 31 | 4643 | -2585 | 0.52 | 1705 | 0.29 |
| asia | -1 | RTY | F7 SPY c_oi|asia1805 med_hi | Emkt_S30_Ta2_XSE | market at t0+1s | 30 NQ-pts x 0.10 = 3.1 RTY pts | 2 x ATR5 | session end | 1125 | 423 | 774 / 91 | -212 | 23301 | -3867 | 0.40 | 826 | 0.13 |
| asia | 1 | YM | F7 NDX g_vol|asia1805 med_hi | Eb5_S45_Tnone_XSE | enter at +5 min if price moved in direction | 45 NQ-pts x 1.27 = 57.2 YM pts | none | session end | 960 | 546 | 799 / 445 | -69 | 8142 | -2145 | 0.43 | 1009 | 0.04 |
| asia | 1 | SI | F7 SLV v_oi|asia1805 med_hi | Ep5_S90_T60_XSE | limit pullback 5 NQ-pts | 90 NQ-pts x 0.01 = 0.5 SI pts | 60 NQ-pts x 0.01 = 0.3 SI pts | session end | 761 | 299 | 603 / 172 | 292 | 7181 | -3085 | 0.25 | 2107 | 0.25 |
| london | 1 | SI | FE SLV g_oi|lbma_silver hi_dn | Ep5_Sa2_T30_X120 | limit pullback 5 NQ-pts | 2 x ATR5 | 30 NQ-pts x 0.01 = 0.2 SI pts | 120 min | 1209 | 556 | 1079 / 484 | 280 | 12896 | -4068 | 0.45 | 1023 | 0.01 |
| london | 1 | SI | FE SLV g_oi|lbma_silver hi_dn | Ep5_Sa2_T30_XSE | limit pullback 5 NQ-pts | 2 x ATR5 | 30 NQ-pts x 0.01 = 0.2 SI pts | session end | 1209 | 556 | 1079 / 484 | 280 | 12896 | -4068 | 0.45 | 1023 | 0.01 |
| london | 1 | YM | F1 SPY v_oi lo_d | Emkt_Sa1_Tnone_XSE | market at t0+1s | 1 x ATR5 | none | session end | 1249 | 642 | 1086 / 488 | 49 | 5343 | -2666 | 0.22 | 813 | 0.03 |
| london | 1 | ES | F1 QQQ g_oi d1_up | Ep10_Sa2_Tnone_X120 | limit pullback 10 NQ-pts | 2 x ATR5 | none | 120 min | 1130 | 472 | 1034 / 415 | 195 | 3541 | -1488 | 0.42 | 702 | 0.03 |
| london | 1 | NQ | F7 SLV v_oi|lon0200 med_hi | Ep5_S30_T90_XSE | limit pullback 5 NQ-pts | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | session end | 1138 | 382 | 771 / 184 | 259 | 3867 | -2528 | 0.39 | 1115 | 0.14 |
| london | -1 | CL | F7 XOP c_dir|lon0200 chg_up | Eb5_S60_T90_XSE | enter at +5 min if price moved in direction | 60 NQ-pts x 0.01 = 0.4 CL pts | 90 NQ-pts x 0.01 = 0.6 CL pts | session end | 1075 | 548 | 952 / 478 | 132 | 8320 | -2621 | 0.48 | 1338 | 0.05 |
| london | 1 | GC | F2 GLD vol|flip touch_dn | Ep10_S30_Ta2_X30 | limit pullback 10 NQ-pts | 30 NQ-pts x 0.19 = 5.7 GC pts | 2 x ATR5 | 30 min | 999 | 323 | 976 / 303 | 88 | 8181 | -3456 | 0.48 | 1388 | 0.10 |
| london | 1 | RTY | F1 DIA v_oi d5_up | Ep10_S30_Tnone_X120 | limit pullback 10 NQ-pts | 30 NQ-pts x 0.10 = 3.1 RTY pts | none | 120 min | 1102 | 643 | 1030 / 598 | 76 | 7273 | -2351 | 0.24 | 985 | 0.13 |
| nyam | -1 | NQ | F6 GLD g_oi|0930|0830|med lo_up | Ep5_S30_Tnone_X15 | limit pullback 5 NQ-pts | 30 NQ-pts x 1.00 = 30.0 NQ pts | none | 15 min | 1957 | 931 | 1937 / 915 | 156 | 7145 | -5349 | 0.42 | 1667 | 0.12 |
| nyam | -1 | NQ | F6 GLD g_oi|0930|0830|med lo_up | Ep3_S30_Tnone_X15 | limit pullback 3 NQ-pts | 30 NQ-pts x 1.00 = 30.0 NQ pts | none | 15 min | 1774 | 827 | 1755 / 811 | 156 | 7145 | -5349 | 0.42 | 1667 | 0.12 |
| nyam | -1 | RTY | F1 SPX v_oi d15_dn | Eb3_Sa1_T90_XSE | enter at +3 min if price moved in direction | 1 x ATR5 | 90 NQ-pts x 0.10 = 9.4 RTY pts | session end | 1767 | 690 | 1745 / 575 | 416 | 18668 | -6649 | 0.57 | 2477 | 0.05 |
| nyam | -1 | GC | F1 GDX c_dir zx_up | Eb3_S30_T60_X60 | enter at +3 min if price moved in direction | 30 NQ-pts x 0.19 = 5.7 GC pts | 60 NQ-pts x 0.19 = 11.4 GC pts | 60 min | 1492 | 702 | 1478 / 680 | 277 | 18374 | -5184 | 0.50 | 1629 | 0.30 |
| nyam | -1 | YM | F6 IWM g_oi|1000|0930|med lo_dn | Emkt_S30_Ta2_XSE | market at t0+1s | 30 NQ-pts x 1.27 = 38.2 YM pts | 2 x ATR5 | session end | 1239 | 718 | 1219 / 695 | -30 | 10630 | -3726 | 0.33 | 1053 | 0.11 |
| nyam | 1 | ES | F6 XLE g_oi|0930|0830|med lo_up | Emkt_S60_Tnone_XSE | market at t0+1s | 60 NQ-pts x 0.19 = 11.5 ES pts | none | session end | 1256 | 656 | 1226 / 575 | -51 | 12505 | -2679 | 0.30 | 1332 | 0.05 |
| nyam | 1 | CL | F1 USO g_oi lo_d | Eb5_S45_Tnone_X60 | enter at +5 min if price moved in direction | 45 NQ-pts x 0.01 = 0.3 CL pts | none | 60 min | 1381 | 1073 | 1319 / 1018 | 587 | 3976 | -3976 | 0.48 | 1317 | 0.01 |
| nyam | -1 | SI | F6 SLV g_dir|1000|0930|med lo_up | Ep10_Sa2_Tnone_XSE | limit pullback 10 NQ-pts | 2 x ATR5 | none | session end | 1450 | 750 | 1413 / 713 | -31 | 16289 | -4780 | 0.27 | 1059 | 0.06 |
| nypm | -1 | NQ | F1 DIA g_dir d5_up | Ep10_Sa2_Tnone_XSE | limit pullback 10 NQ-pts | 2 x ATR5 | none | session end | 2014 | 1113 | 2000 / 1099 | 353 | 8533 | -3641 | 0.55 | 1724 | 0.10 |
| nypm | -1 | NQ | F1 XLE c_dir d1_dn | Ep5_S30_Tnone_XSE | limit pullback 5 NQ-pts | 30 NQ-pts x 1.00 = 30.0 NQ pts | none | session end | 2679 | 1507 | 2659 / 1490 | 336 | 1527 | -1527 | 0.65 | 1457 | 0.01 |
| nypm | -1 | NQ | F1 XLE c_dir d1_dn | Ep3_S30_Tnone_X120 | limit pullback 3 NQ-pts | 30 NQ-pts x 1.00 = 30.0 NQ pts | none | 120 min | 2399 | 1497 | 2378 / 1479 | 336 | 1527 | -1527 | 0.65 | 1457 | 0.01 |
| nypm | -1 | ES | F1 XLE c_oi hi_d | Emkt_Sa1_Tnone_X120 | market at t0+1s | 1 x ATR5 | none | 120 min | 1632 | 1015 | 1562 / 962 | 368 | 2690 | -2690 | 0.41 | 1277 | 0.05 |
| nypm | -1 | GC | F1 GLD v_vol hi_d | Eb1_Sa1_Ta1_XSE | enter at +1 min if price moved in direction | 1 x ATR5 | 1 x ATR5 | session end | 1556 | 958 | 1306 / 821 | 501 | 13233 | -3337 | 0.67 | 1854 | 0.66 |
| nypm | 1 | CL | F1 XLE v_oi d60_dn | Eb5_Sa1_T90_XSE | enter at +5 min if price moved in direction | 1 x ATR5 | 90 NQ-pts x 0.01 = 0.6 CL pts | session end | 1258 | 724 | 990 / 558 | 268 | 4489 | -3510 | 0.50 | 1023 | 0.11 |
| nypm | -1 | SI | F1 SLV v_oi d60_up | Emkt_Sa1_T30_X60 | market at t0+1s | 1 x ATR5 | 30 NQ-pts x 0.01 = 0.2 SI pts | 60 min | 1122 | 570 | 936 / 457 | 147 | 15149 | -8735 | 0.56 | 1121 | 0.10 |
| nypm | -1 | YM | F1 NDX c_dir d5_dn | Emkt_S30_Tnone_XSE | market at t0+1s | 30 NQ-pts x 1.27 = 38.2 YM pts | none | session end | 1262 | 1061 | 1191 / 1009 | 53 | 2725 | -1374 | 0.27 | 1154 | 0.06 |
| nypm | -1 | RTY | F1 IWM v_dir d60_up | Emkt_S45_Tnone_XSE | market at t0+1s | 45 NQ-pts x 0.10 = 4.7 RTY pts | none | session end | 1081 | 448 | 866 / 324 | 32 | 8819 | -3990 | 0.27 | 1422 | 0.97 |
| pit | 1 | CL | F2 XOP oi|magnet touch_dn | Emkt_S45_Tnone_X120 | market at t0+1s | 45 NQ-pts x 0.01 = 0.3 CL pts | none | 120 min | n/a | n/a | n/a / n/a | n/a | n/a | n/a | n/a | n/a | 0.01 |
| pit | 1 | CL | F2 XOP oi|magnet touch_dn | Emkt_S60_Tnone_XSE | market at t0+1s | 60 NQ-pts x 0.01 = 0.4 CL pts | none | session end | n/a | n/a | n/a / n/a | n/a | n/a | n/a | n/a | n/a | 0.01 |
| pit | 1 | CL | F1 XOP v_vol d5_up | Eb1_S45_T60_XSE | enter at +1 min if price moved in direction | 45 NQ-pts x 0.01 = 0.3 CL pts | 60 NQ-pts x 0.01 = 0.4 CL pts | session end | n/a | n/a | n/a / n/a | n/a | n/a | n/a | n/a | n/a | 0.01 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_X60 | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | 60 min | 1073 | 352 | 961 / 286 | 250 | 3773 | -1417 | 0.35 | 458 | 0.01 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_X120 | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | 120 min | 1073 | 352 | 961 / 286 | 250 | 3773 | -1417 | 0.35 | 458 | 0.01 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_XSE | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | session end | 1073 | 352 | 961 / 286 | 250 | 3773 | -1417 | 0.35 | 458 | 0.01 |
| pre | -1 | YM | F6 SPY g_oi|0830|0200|med lo_up | Eb1_Sa1_T45_X30 | enter at +1 min if price moved in direction | 1 x ATR5 | 45 NQ-pts x 1.27 = 57.2 YM pts | 30 min | 867 | 377 | 853 / 360 | 48 | 9801 | -1753 | 0.34 | 580 | 0.04 |
| pre | 1 | ES | F1 GDX g_oi lo_d | Eb1_Sa1_Tnone_X15 | enter at +1 min if price moved in direction | 1 x ATR5 | none | 15 min | 704 | 326 | 618 / 273 | 10 | 4333 | -2438 | 0.47 | 386 | 0.02 |
| pre | -1 | SI | F6 SLV g_oi|0830|0200|sign hi_up | Eb1_S90_Tnone_X30 | enter at +1 min if price moved in direction | 90 NQ-pts x 0.01 = 0.5 SI pts | none | 30 min | 670 | 97 | 632 / 59 | -73 | 16272 | -6888 | 0.34 | 834 | 0.26 |
| pre | 1 | GC | F2 GLD vol|magnet touch_dn | Emkt_S30_Tnone_X30 | market at t0+1s | 30 NQ-pts x 0.19 = 5.7 GC pts | none | 30 min | 940 | 372 | 537 / 157 | 161 | 5426 | -3681 | 0.35 | 436 | 0.02 |
| pre | -1 | RTY | F1 SPY g_oi hi_d | Emkt_Sa1_Tnone_X120 | market at t0+1s | 1 x ATR5 | none | 120 min | 1245 | 294 | 942 / 113 | 48 | 6259 | -2545 | 0.35 | 638 | 0.04 |
| pre | -1 | CL | FE USO c_oi|data0830 lo_up | Eb1_S45_Tnone_X15 | enter at +1 min if price moved in direction | 45 NQ-pts x 0.01 = 0.3 CL pts | none | 15 min | 529 | 194 | 471 / 146 | 63 | 5215 | -2651 | 0.42 | 997 | 0.06 |

## 3b. First-order joint (finalist weekly $ added to the live stack S1B-COMB weekly, own lots; exact-engine joint via TP sets TL3_UW_* follows)
| finalist id | corr KB/PE/SM/HM/MV/PB/OD | corr stack | stack maxDD L6M -> with | stack worst wk L6M -> with | cand mean L6M | weeks trading |
|--|--|--|--|--|--|--|
| F1_CL_USO_g_oi_lo_d_nyam_1_Eb5_S45_Tnone_X60 | -0.14/-0.10/0.06/-0.08/-0.10/-0.13/0.05 | -0.12 | 79907 -> 79907 | -62941 -> -55865 | 1339 | 46 |
| F1_CL_XLE_v_oi_d60_dn_nypm_1_Eb5_Sa1_T90_XSE | -0.14/0.06/0.11/0.03/-0.02/0.03/0.06 | 0.04 | 79907 -> 77634 | -62941 -> -62827 | 1252 | 39 |
| F1_CL_XOP_v_vol_d5_up_pit_1_Eb1_S45_T60_XSE | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |
| F1_ES_GDX_g_oi_lo_d_pre_1_Eb1_Sa1_Tnone_X15 | 0.03/0.01/-0.03/0.08/-0.01/-0.13/-0.18 | -0.00 | 79907 -> 78961 | -62941 -> -62941 | 681 | 21 |
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_T90_XSE | 0.08/0.07/0.04/-0.10/-0.16/0.06/0.01 | 0.04 | 79907 -> 79727 | -62941 -> -64220 | 1130 | 42 |
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_Tnone_X120 | 0.07/0.14/0.10/-0.09/-0.06/0.09/0.02 | 0.12 | 79907 -> 79727 | -62941 -> -64220 | 1173 | 42 |
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_Tnone_XSE | 0.07/0.14/0.10/-0.09/-0.06/0.09/0.02 | 0.12 | 79907 -> 79727 | -62941 -> -64220 | 1173 | 42 |
| F1_ES_XLE_c_oi_hi_d_nypm_-1_Emkt_Sa1_Tnone_X120 | -0.08/0.00/-0.10/0.04/-0.08/0.03/-0.11 | -0.05 | 79907 -> 79907 | -62941 -> -64054 | 1747 | 32 |
| F1_GC_GDX_c_dir_zx_up_nyam_-1_Eb3_S30_T60_X60 | 0.02/0.05/0.03/0.08/0.03/-0.07/-0.06 | 0.06 | 79907 -> 78807 | -62941 -> -60668 | 1374 | 73 |
| F1_GC_GLD_v_vol_hi_d_nypm_-1_Eb1_Sa1_Ta1_XSE | 0.11/0.11/-0.01/-0.01/-0.03/0.07/-0.06 | 0.10 | 79907 -> 76177 | -62941 -> -64381 | 1622 | 75 |
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
| F1_NQ_XLE_c_dir_d1_dn_nypm_-1_Ep3_S30_Tnone_X120 | -0.03/-0.01/0.02/-0.02/-0.02/-0.00/-0.15 | -0.02 | 79907 -> 80196 | -62941 -> -62941 | 2491 | 58 |
| F1_NQ_XLE_c_dir_d1_dn_nypm_-1_Ep5_S30_Tnone_XSE | 0.06/0.02/0.11/0.04/0.07/0.07/-0.13 | 0.07 | 79907 -> 80036 | -62941 -> -62941 | 2783 | 55 |
| F1_RTY_DIA_v_oi_d5_up_london_1_Ep10_S30_Tnone_X120 | 0.06/0.04/0.06/0.09/0.01/-0.04/-0.03 | 0.07 | 79907 -> 79923 | -62941 -> -62941 | 1196 | 35 |
| F1_RTY_IWM_v_dir_d60_up_nypm_-1_Emkt_S45_Tnone_XSE | 0.01/0.03/0.05/0.02/-0.06/0.19/-0.09 | 0.04 | 79907 -> 79294 | -62941 -> -62941 | 1122 | 56 |
| F1_RTY_IWM_v_oi_hi_d_nyam_-1_Eb5_S30_T60_XSE | 0.01/0.15/0.07/0.09/-0.13/0.14/0.03 | 0.13 | 79907 -> 78774 | -62941 -> -58014 | 1710 | 97 |
| F1_RTY_SPX_v_oi_d15_dn_nyam_-1_Eb3_Sa1_T90_X120 | 0.12/0.06/-0.03/0.04/0.06/0.02/0.11 | 0.08 | 79907 -> 78606 | -62941 -> -57369 | 1688 | 102 |
| F1_RTY_SPX_v_oi_d15_dn_nyam_-1_Eb3_Sa1_T90_XSE | 0.12/0.06/-0.03/0.04/0.07/0.02/0.11 | 0.08 | 79907 -> 78606 | -62941 -> -57369 | 1688 | 102 |
| F1_RTY_SPY_g_oi_hi_d_pre_-1_Emkt_Sa1_Tnone_X120 | 0.15/0.06/-0.00/0.08/0.04/-0.04/0.04 | 0.09 | 79907 -> 79514 | -62941 -> -64123 | 1195 | 76 |
| F1_SI_SLV_v_oi_d60_up_nypm_-1_Emkt_Sa1_T30_X60 | 0.01/0.15/-0.03/0.02/0.02/0.03/-0.10 | 0.11 | 79907 -> 77179 | -62941 -> -62941 | 1153 | 58 |
| F1_YM_NDX_c_dir_d5_dn_nypm_-1_Emkt_S30_Tnone_XSE | 0.05/0.09/-0.01/-0.06/-0.04/0.09/-0.05 | 0.07 | 79907 -> 79996 | -62941 -> -64145 | 1247 | 31 |
| F1_YM_SPY_v_oi_lo_d_london_1_Emkt_Sa1_Tnone_X120 | 0.05/-0.06/0.07/0.03/-0.11/-0.07/-0.17 | -0.04 | 79907 -> 79907 | -62941 -> -55540 | 1260 | 63 |
| F1_YM_SPY_v_oi_lo_d_london_1_Emkt_Sa1_Tnone_XSE | 0.05/-0.06/0.07/0.03/-0.11/-0.07/-0.17 | -0.04 | 79907 -> 79907 | -62941 -> -55540 | 1260 | 63 |
| F2_CL_XOP_oi-magnet_touch_dn_pit_1_Emkt_S45_Tnone_X120 | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |
| F2_CL_XOP_oi-magnet_touch_dn_pit_1_Emkt_S60_Tnone_XSE | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |
| F2_GC_GLD_vol-flip_touch_dn_london_1_Ep10_S30_Ta2_X30 | 0.04/-0.01/-0.05/0.03/-0.05/0.02/0.07 | -0.01 | 79907 -> 77560 | -62941 -> -63943 | 1054 | 53 |
| F2_GC_GLD_vol-magnet_touch_dn_pre_1_Emkt_S30_Tnone_X30 | 0.02/-0.01/0.06/0.00/-0.09/0.01/-0.09 | -0.01 | 79907 -> 79776 | -62941 -> -62941 | 931 | 42 |
| F2_NQ_SPX_oi-flip_touch_up_asia_1_Eb3_Sa1_T90_X120 | -0.05/-0.01/0.01/0.11/0.06/0.06/-0.01 | 0.01 | 79907 -> 79907 | -62941 -> -58836 | 1444 | 52 |
| F2_NQ_SPX_oi-flip_touch_up_asia_1_Eb3_Sa1_Tnone_X120 | -0.04/0.05/0.04/0.11/0.08/0.05/0.01 | 0.07 | 79907 -> 79907 | -62941 -> -59148 | 1574 | 52 |
| F6_ES_XLE_g_oi-0930-0830-med_lo_up_nyam_1_Emkt_S60_Tnone_XSE | 0.12/0.02/0.01/0.05/0.06/-0.06/0.13 | 0.06 | 79907 -> 79907 | -62941 -> -64125 | 925 | 37 |
| F6_NQ_GLD_g_oi-0930-0830-med_lo_up_nyam_-1_Ep3_S30_Tnone_X15 | -0.07/0.18/0.01/0.14/-0.15/0.14/-0.00 | 0.12 | 79907 -> 81135 | -62941 -> -57811 | 1795 | 37 |
| F6_NQ_GLD_g_oi-0930-0830-med_lo_up_nyam_-1_Ep5_S30_Tnone_X15 | -0.08/0.19/0.01/0.15/-0.14/0.14/-0.00 | 0.13 | 79907 -> 81135 | -62941 -> -57731 | 1985 | 37 |
| F6_SI_SLV_g_dir-1000-0930-med_lo_up_nyam_-1_Ep10_Sa2_Tnone_XSE | 0.08/-0.02/0.04/0.03/-0.13/0.00/0.09 | 0.00 | 79907 -> 81773 | -62941 -> -63845 | 1506 | 52 |
| F6_SI_SLV_g_oi-0830-0200-sign_hi_up_pre_-1_Eb1_S90_Tnone_X30 | 0.09/0.05/-0.07/0.06/-0.02/-0.09/-0.16 | 0.03 | 79907 -> 79821 | -62941 -> -61721 | 692 | 52 |
| F6_YM_IWM_g_oi-1000-0930-med_lo_dn_nyam_-1_Emkt_S30_Ta2_XSE | -0.01/-0.08/0.04/0.03/-0.03/-0.06/0.01 | -0.05 | 79907 -> 79821 | -62941 -> -59722 | 1194 | 62 |
| F6_YM_SPY_g_oi-0830-0200-med_lo_up_pre_-1_Eb1_Sa1_T45_X30 | -0.11/-0.10/-0.04/0.13/-0.18/-0.00/0.01 | -0.12 | 79907 -> 75319 | -62941 -> -62941 | 901 | 41 |
| F7_CL_USO_c_oi-asia1805_chg_dn_asia_-1_Eb1_Sa2_T90_XSE | -0.06/0.02/0.09/0.01/-0.06/0.11/-0.02 | 0.02 | 79907 -> 81217 | -62941 -> -62941 | 1228 | 60 |
| F7_CL_XOP_c_dir-lon0200_chg_up_london_-1_Eb5_S60_T90_XSE | -0.05/-0.07/-0.03/0.05/-0.04/-0.04/-0.03 | -0.07 | 79907 -> 78072 | -62941 -> -61106 | 1187 | 55 |
| F7_ES_QQQ_g_dir-asia1805_med_hi_asia_-1_Eb3_S45_Tnone_XSE | -0.01/0.17/0.11/0.11/0.10/0.09/0.01 | 0.18 | 79907 -> 79907 | -62941 -> -64286 | 1375 | 74 |
| F7_ES_XOP_c_oi-asia1805_med_hi_asia_1_Eb5_S30_Tnone_XSE | 0.11/0.11/-0.01/0.06/0.06/0.17/0.05 | 0.13 | 79907 -> 79907 | -62941 -> -64160 | 1198 | 40 |
| F7_GC_GLD_v_oi-asia1805_med_lo_asia_-1_Ep5_S30_Tnone_XSE | 0.03/0.02/-0.01/0.18/-0.08/0.14/-0.07 | 0.03 | 79907 -> 79907 | -62941 -> -60746 | 2390 | 52 |
| F7_NQ_SLV_v_oi-lon0200_med_hi_london_1_Ep5_S30_T90_XSE | -0.19/-0.12/-0.00/-0.07/-0.16/0.02/0.06 | -0.16 | 79907 -> 79821 | -62941 -> -54570 | 1087 | 41 |
| F7_RTY_SPY_c_oi-asia1805_med_hi_asia_-1_Emkt_S30_Ta2_XSE | 0.03/-0.03/0.05/-0.03/0.11/-0.10/-0.08 | -0.01 | 79907 -> 78124 | -62941 -> -57799 | 1252 | 102 |
| F7_SI_SLV_v_oi-asia1805_med_hi_asia_1_Ep5_S90_T60_XSE | -0.09/0.10/-0.11/0.05/0.01/0.06/-0.05 | 0.04 | 79907 -> 79821 | -62941 -> -57982 | 1045 | 32 |
| F7_YM_NDX_g_vol-asia1805_med_hi_asia_1_Eb5_S45_Tnone_XSE | 0.01/0.12/0.00/0.13/0.16/0.20/0.03 | 0.15 | 79907 -> 77765 | -62941 -> -64125 | 802 | 80 |
| FEB_CL_NONE_cl_pit_open_all_pit_1_Emkt_S90_Tnone_XSE | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |
| FEB_CL_NONE_ny_open_dn_pit_1_Emkt_S45_Tnone_XSE | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |
| FEB_CL_NONE_ny_open_dn_pit_1_Emkt_Sa2_Tnone_XSE | n/a/n/a/n/a/n/a/n/a/n/a/n/a | n/a | 79907 -> 79907 | -62941 -> -62941 | 0 | 0 |
| FE_CL_USO_c_oi-data0830_lo_up_pre_-1_Eb1_S45_Tnone_X15 | -0.04/0.00/0.03/0.03/0.04/0.01/-0.02 | 0.01 | 79907 -> 79821 | -62941 -> -62617 | 493 | 42 |
| FE_SI_SLV_g_oi-lbma_silver_hi_dn_london_1_Ep5_Sa2_T30_X120 | -0.04/0.08/0.04/0.07/0.09/-0.02/-0.12 | 0.07 | 79907 -> 78129 | -62941 -> -62117 | 1292 | 58 |
| FE_SI_SLV_g_oi-lbma_silver_hi_dn_london_1_Ep5_Sa2_T30_XSE | -0.04/0.08/0.04/0.07/0.09/-0.02/-0.12 | 0.07 | 79907 -> 78129 | -62941 -> -62117 | 1292 | 58 |

## 6. No-UW baseline of the F6/F7 entry clocks (same harness/grid/gate; F7B = every business day at the clock, F6B = price move only) vs the UW-conditioned tables
| instrument | clock family | no-UW baseline: groups / gated (share) / max recents / best Calmar | UW-conditioned: groups / gated (share) / max recents / best Calmar |
|--|--|--|--|
| NQ | F6 | 16 / 16 (100%) / 1271 / 22.9 | 2190 / 1740 (79%) / 1852 / 82.9 |
| NQ | F7 | 6 / 6 (100%) / 5275 / 12.1 | 2762 / 2615 (95%) / 6195 / 51.1 |
| ES | F6 | 16 / 16 (100%) / 1445 / 24.7 | 2188 / 1614 (74%) / 1747 / 52.1 |
| ES | F7 | 6 / 6 (100%) / 2673 / 9.6 | 2762 / 2455 (89%) / 3268 / 58.2 |
| RTY | F6 | 16 / 15 (94%) / 1622 / 27.7 | 1084 / 798 (74%) / 1919 / 66.3 |
| RTY | F7 | 6 / 6 (100%) / 908 / 14.2 | 1384 / 1186 (86%) / 1439 / 43.9 |
| YM | F6 | 16 / 16 (100%) / 1173 / 31.8 | 1084 / 799 (74%) / 1802 / 53.5 |
| YM | F7 | 6 / 5 (83%) / 2141 / 14.6 | 1384 / 1228 (89%) / 2931 / 42.8 |

## 6a. Best gated book per instrument x session (in-sample, same 2 years, before WF/placebo; instrument = the product traded, trigger ticker beside it)
| instrument | session | dir | family | trigger | cell | n L6M | L1M | L3M | L6M | HOLD | PREUW | maxDD L6M | Calmar |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| CL | asia | short | F7 | USO c_oi|asia1805 chg_dn | Eb1_Sa2_T90_XSE | 26 | 216 | 1820 | 1264 | 351 | n/a | 1396 | 47.1 |
| CL | london | short | F7 | XOP c_dir|lon0200 chg_up | Eb5_S60_T90_XSE | 26 | 1212 | 1202 | 1075 | 548 | n/a | 1280 | 43.7 |
| CL | nyam | long | F1 | USO g_oi lo_d | Eb5_S45_Tnone_X60 | 25 | 1369 | 1422 | 1381 | 1079 | n/a | 1403 | 51.2 |
| CL | nypm | long | F1 | XLE v_oi d60_dn | Eb5_Sa1_T90_XSE | 27 | 353 | 1761 | 1258 | 675 | n/a | 1296 | 50.5 |
| CL | pit | long | F2 | XOP oi|magnet touch_dn | Emkt_S45_Tnone_X120 | 23 | 856 | 2410 | 1757 | 802 | n/a | 1295 | 70.6 |
| CL | pre | short | FE | USO c_oi|data0830 lo_up | Eb1_S45_Tnone_X15 | 22 | 1880 | 879 | 529 | 183 | n/a | 1318 | 20.9 |
| ES | asia | long | F7 | XOP c_oi|asia1805 med_hi | Eb5_S30_Tnone_XSE | 24 | 2761 | 1707 | 1365 | 584 | n/a | 1219 | 58.2 |
| ES | london | long | F1 | QQQ g_oi d1_up | Ep10_Sa2_Tnone_X120 | 28 | 141 | 1663 | 1130 | 472 | -155 | 1279 | 45.9 |
| ES | nyam | long | F6 | XLE g_oi|0930|0830|med lo_up | Emkt_S60_Tnone_XSE | 21 | 3079 | 1581 | 1256 | 678 | n/a | 1253 | 52.1 |
| ES | nypm | short | F1 | XLE c_oi hi_d | Emkt_Sa1_Tnone_X120 | 24 | 4204 | 2246 | 1632 | 916 | n/a | 1380 | 61.5 |
| ES | pre | long | F1 | GDX g_oi lo_d | Eb1_Sa1_T90_X15 | 20 | 1289 | 1038 | 704 | 326 | n/a | 819 | 30.5 |
| GC | asia | short | F7 | GLD v_oi|asia1805 med_lo | Ep5_S30_Tnone_XSE | 36 | 3008 | 1425 | 2432 | 547 | n/a | 2345 | 53.9 |
| GC | london | long | F2 | GLD vol|flip touch_dn | Ep10_S30_Ta2_X30 | 30 | 1068 | 1318 | 999 | 323 | n/a | 1172 | 43.3 |
| GC | nyam | short | F1 | GDX c_dir zx_up | Eb3_S30_T60_X120 | 43 | 1570 | 2251 | 1492 | 650 | n/a | 1243 | 62.4 |
| GC | nypm | short | F1 | GLD v_vol hi_d | Eb1_Sa1_Ta1_XSE | 69 | 1898 | 1587 | 1556 | 958 | n/a | 1543 | 52.5 |
| GC | pre | long | F2 | GLD vol|magnet touch_dn | Emkt_S30_Tnone_X30 | 20 | -225 | 1215 | 940 | 372 | n/a | 1726 | 28.3 |
| NQ | asia | long | F2 | SPX oi|flip touch_up | Eb3_Sa1_Tnone_X120 | 20 | 124 | 1571 | 1637 | 659 | -204 | 1218 | 69.9 |
| NQ | london | long | F7 | SLV v_oi|lon0200 med_hi | Ep5_S30_T90_XSE | 26 | n/a | 996 | 1138 | 362 | n/a | 1319 | 44.9 |
| NQ | nyam | short | F6 | GLD g_oi|0930|0830|med lo_up | Ep5_S30_Tnone_X15 | 29 | 1110 | 698 | 1957 | 931 | n/a | 1227 | 82.9 |
| NQ | nypm | short | F1 | DIA g_dir d5_up | Ep10_Sa2_Tnone_XSE | 38 | 1570 | 1163 | 2014 | 1113 | -226 | 1470 | 71.2 |
| NQ | pre | short | F1 | SPX v_oi lo_d | Emkt_S30_T90_XSE | 24 | 4364 | 1983 | 1073 | 352 | 53 | 1275 | 43.8 |
| RTY | asia | short | F7 | SPY c_oi|asia1805 med_hi | Emkt_S30_Ta2_XSE | 69 | 1279 | 1023 | 1124 | 421 | -241 | 1332 | 43.9 |
| RTY | london | long | F1 | DIA v_oi d5_up | Ep10_S30_Tnone_XSE | 30 | 2686 | 1540 | 1102 | 643 | -156 | 1330 | 43.1 |
| RTY | nyam | short | F1 | SPX v_oi d15_dn | Eb3_Sa1_T90_XSE | 44 | 2012 | 1377 | 1771 | 693 | 106 | 1241 | 74.2 |
| RTY | nypm | short | F1 | IWM v_dir d60_up | Emkt_S45_Tnone_XSE | 22 | 773 | 459 | 1081 | 448 | -0 | 1287 | 43.7 |
| RTY | pre | short | F1 | SPY g_oi hi_d | Emkt_Sa1_Tnone_XSE | 38 | 3406 | 1938 | 1245 | 294 | 241 | 2797 | 23.1 |
| SI | asia | long | F7 | SLV v_oi|asia1805 med_hi | Ep5_S90_T60_XSE | 20 | n/a | 1011 | 761 | 299 | n/a | 865 | 33.0 |
| SI | london | long | FE | SLV g_oi|lbma_silver hi_dn | Ep5_Sa2_T30_XSE | 39 | 1180 | 1431 | 1209 | 566 | n/a | 1137 | 52.4 |
| SI | nyam | short | F6 | SLV g_dir|1000|0930|med lo_up | Ep10_Sa2_Tnone_XSE | 22 | -390 | 1872 | 1450 | 791 | n/a | 1952 | 38.6 |
| SI | nypm | short | F1 | SLV v_oi d60_up | Emkt_Sa1_T30_X60 | 50 | 2398 | 1691 | 1122 | 570 | n/a | 579 | 48.6 |
| SI | pre | short | F6 | SLV g_oi|0830|0200|sign hi_up | Eb1_S90_Tnone_X30 | 21 | 842 | 639 | 670 | 132 | n/a | 730 | 29.0 |
| YM | asia | long | F7 | NDX g_vol|asia1805 med_hi | Eb5_S45_Tnone_XSE | 28 | 1182 | 1375 | 960 | 545 | 535 | 1185 | 41.6 |
| YM | london | long | F1 | SPY v_oi lo_d | Emkt_Sa1_Tnone_X120 | 27 | 3968 | 2116 | 1249 | 642 | -254 | 1362 | 47.7 |
| YM | nyam | short | F6 | IWM g_oi|1000|0930|med lo_dn | Emkt_S30_Ta2_XSE | 34 | 423 | 1293 | 1239 | 718 | -195 | 1204 | 53.5 |
| YM | nypm | short | F1 | NDX c_dir d5_dn | Emkt_S30_Tnone_XSE | 24 | 1829 | 712 | 1262 | 1060 | -88 | 1477 | 44.4 |
| YM | pre | short | F6 | SPY g_oi|0830|0200|med lo_up | Eb1_Sa1_T45_X30 | 20 | 648 | 977 | 868 | 378 | 158 | 1266 | 35.6 |

## 6b. Which instrument carries each trigger ticker best (all single-trigger families; gated share of groups / best gated L6M Calmar with $1,200 dd floor; * = matched instrument)
| trigger ticker | NQ | ES | RTY | YM | GC | SI | CL |
|--|--|--|--|--|--|--|--|
| DIA | 57% / 71.2 | 53% / 47.0 | 52% / 51.8 | *56% / 43.6 | - | - | - |
| GDX | 65% / 56.5 | 60% / 53.1 | - | - | *51% / 62.4 | - | - |
| GLD | 62% / 82.9 | 57% / 42.4 | - | - | *56% / 53.9 | - | - |
| IWM | 49% / 48.4 | 46% / 45.1 | *47% / 66.6 | 47% / 53.5 | - | - | - |
| NDX | *55% / 60.9 | 47% / 45.7 | 49% / 58.3 | 48% / 45.7 | - | - | - |
| QQQ | *60% / 62.2 | 55% / 49.2 | 57% / 56.3 | 58% / 41.9 | - | - | - |
| SLV | 65% / 58.9 | 59% / 39.0 | - | - | - | *54% / 52.4 | - |
| SPX | 56% / 69.9 | *54% / 35.7 | 53% / 74.2 | 54% / 42.8 | - | - | - |
| SPY | 56% / 56.5 | *52% / 42.2 | 52% / 43.9 | 56% / 51.4 | - | - | - |
| USO | 65% / 70.9 | 63% / 49.6 | - | - | - | - | *57% / 51.2 |
| XLE | 65% / 65.9 | 62% / 61.5 | - | - | - | - | *52% / 50.5 |
| XOP | 59% / 50.2 | 55% / 58.2 | - | - | - | - | *46% / 70.6 |

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

Pair finalists (WF bi-weekly over the 1,470 cells, shuffled-day placebo B=100 on the pair events, 2x-slippage stress):
| session | dir | inst | pair | cell | n events | L6M | HOLD | PREUW | stress L6M / HOLD | WF mean | WF periods positive | placebo q95 | placebo p |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| nyam | short | RTY | SPX:v_oi+QQQ:v_oi F1/d15_dn+F1/d5_up | Ep3_S45_Tnone_XSE | 1983 | 3109 | 1489 | -77 | 2956 / 1346 | -75 | 0.43 | 2362 | 0.01 |
| nyam | short | RTY | SPX:v_oi+NDX:v_dir F1/d15_dn+F1/lo_d | Emkt_S30_Ta2_X60 | 1329 | 2279 | 1605 | 173 | 2233 / 1551 | 375 | 0.63 | 1596 | 0.02 |
| nypm | short | NQ | SPY:v_vol+QQQ:v_vol F1/d15_up+F1/d5_up | Emkt_S90_T45_XSE | 4586 | 1117 | 862 | 357 | 1092 / 844 | 356 | 0.67 | 1960 | 0.74 |
| nypm | short | NQ | SPX:c_dir+SPY:v_dir F1/zx_dn+F1/d5_dn | Emkt_Sa2_Tnone_XSE | 1096 | 1176 | 730 | 241 | 1138 / 702 | 80 | 0.39 | 1267 | 0.13 |
| asia | long | ES | QQQ:c_dir|asia1805+QQQ:c_oi|asia1805 F7/med_hi+F7/med_lo | Emkt_S30_Tnone_XSE | 119 | 1631 | 524 | -111 | 1494 / 421 | 93 | 0.26 | 1459 | 0.03 |
| london | long | YM | SPY:c_dir|lon0200+SPX:c_oi|lon0200 F7/chg_dn+F7/med_hi | Emkt_S30_Tnone_XSE | 114 | 2189 | 1179 | 147 | 1892 / 1007 | -55 | 0.38 | 2089 | 0.04 |
| london | long | YM | SPY:c_dir|lon0200+SPX:c_oi|lon0200 F7/neg+F7/med_hi | Emkt_S30_Tnone_XSE | 114 | 2189 | 1179 | 147 | 1892 / 1007 | -55 | 0.38 | 2089 | 0.04 |
| asia | long | ES | QQQ:g_dir|asia1805+QQQ:c_dir|asia1805 F7/med_hi+F7/med_hi | Emkt_Sa1_Tnone_XSE | 145 | 2285 | 1213 | 595 | 1773 / 789 | 175 | 0.27 | 1530 | 0.02 |

## 8. EXACT-ENGINE JOINT (TP engine, JN05W2 base all layers ON, UW book injected via code/th_uwbooks/uw_inject.py; engine fills, $4.84 RT; reference = JN05W2 on the same months)
| set | window | months | weeks | stack mean $/wk ref -> inj (d) | stack maxDD ref -> inj (d) | worst week ref -> inj (d) | UW1 alone $/wk (n trades) | other books d mean | UW1 idle share | corr UW1 vs KB/PE/SM/HM/MV/PB/OD or live tags |
|--|--|--|--|--|--|--|--|--|--|--|
| TL3_UW_INJ_ASIA | L3M | 202410-202610 | 11 | 16819 -> 16711 (-108) | 36371 -> 36371 (0) | -36371 -> -36371 (0) | -108 (5) | 0 | 0.60 | A7 -0.10 H7 0.24 K7 0.35 M7 0.13 O7 -0.04 P7 -0.06 U7 0.13 |
| TL3_UW_INJ_ASIA | L6M | 202410-202610 | 25 | 23241 -> 23310 (69) | 36371 -> 36371 (0) | -36371 -> -36371 (0) | 3 (16) | 66 | 0.44 | A7 0.44 H7 0.19 K7 0.09 M7 -0.14 O7 -0.03 P7 -0.02 U7 0.06 |
| TL3_UW_INJ_ASIA | HOLD | 202410-202610 | 51 | 17640 -> 17693 (54) | 63185 -> 62701 (-484) | -55145 -> -55145 (0) | -61 (33) | 115 | 0.52 | A7 0.15 H7 0.11 K7 0.21 M7 -0.09 O7 -0.22 P7 -0.00 U7 -0.15 |
| TL3_UW_INJ_ASIA | PREUW | 202410-202610 | 40 | 11570 -> 11501 (-69) | 76186 -> 77650 (1464) | -52547 -> -52547 (0) | -3 (28) | -66 | 0.61 | A7 0.07 H7 0.03 K7 -0.09 M7 -0.21 O7 0.20 P7 -0.23 U7 0.08 |
| TL3_UW_INJ_NDXB | L3M | 202410-202610 | 11 | 16819 -> 17518 (699) | 36371 -> 35817 (-554) | -36371 -> -35817 (554) | 699 (29) | 0 | 0.38 | A7 -0.54 H7 0.40 K7 -0.47 M7 -0.49 O7 -0.16 P7 0.19 U7 -0.13 |
| TL3_UW_INJ_NDXB | L6M | 202410-202610 | 25 | 23241 -> 24097 (856) | 36371 -> 35817 (-554) | -36371 -> -35817 (554) | 856 (64) | 0 | 0.45 | A7 -0.05 H7 -0.01 K7 0.06 M7 -0.33 O7 -0.37 P7 0.48 U7 0.02 |
| TL3_UW_INJ_NDXB | HOLD | 202410-202610 | 51 | 17640 -> 18491 (851) | 63185 -> 61697 (-1488) | -55145 -> -55145 (0) | 851 (129) | 0 | 0.43 | A7 -0.08 H7 0.04 K7 0.09 M7 -0.08 O7 -0.37 P7 0.23 U7 0.03 |
| TL3_UW_INJ_NDXB | PREUW | 202410-202610 | 40 | 11570 -> 11359 (-211) | 76186 -> 80008 (3822) | -52547 -> -53443 (-896) | -207 (124) | -4 | 0.33 | A7 0.03 H7 -0.01 K7 0.17 M7 0.16 O7 -0.19 P7 -0.07 U7 0.33 |
| TL3_UW_INJ_NYAM | L3M | 202410-202610 | 11 | 16819 -> 16907 (88) | 36371 -> 36371 (-0) | -36371 -> -36371 (0) | 88 (5) | 0 | 0.60 | A7 -0.71 H7 0.17 K7 0.35 M7 -0.63 O7 -0.56 P7 -0.18 U7 0.18 |
| TL3_UW_INJ_NYAM | L6M | 202410-202610 | 25 | 23241 -> 23814 (573) | 36371 -> 36371 (0) | -36371 -> -36371 (0) | 537 (17) | 36 | 0.59 | A7 -0.09 H7 0.07 K7 0.17 M7 -0.16 O7 -0.23 P7 0.35 U7 0.29 |
| TL3_UW_INJ_NYAM | HOLD | 202410-202610 | 51 | 17640 -> 17890 (250) | 63185 -> 64372 (1187) | -55145 -> -55648 (-503) | 204 (33) | 46 | 0.55 | A7 0.01 H7 0.17 K7 0.16 M7 -0.05 O7 -0.32 P7 0.25 U7 0.19 |
| TL3_UW_INJ_NYAM | PREUW | 202410-202610 | 40 | 11570 -> 11562 (-7) | 76186 -> 76186 (0) | -52547 -> -52547 (0) | -53 (8) | 46 | 0.50 | A7 0.02 H7 0.11 K7 -0.17 M7 -0.11 O7 -0.14 P7 0.21 U7 0.08 |
| TL3_UW_INJ_PRE | L3M | 202410-202610 | 11 | 16819 -> 17238 (418) | 36371 -> 35848 (-523) | -36371 -> -35848 (523) | 385 (8) | 34 | 0.50 | A7 -0.35 H7 0.02 K7 -0.17 M7 -0.38 O7 -0.28 P7 -0.11 U7 -0.13 |
| TL3_UW_INJ_PRE | L6M | 202410-202610 | 25 | 23241 -> 23414 (174) | 36371 -> 35848 (-523) | -36371 -> -35848 (523) | 159 (11) | 15 | 0.45 | A7 -0.34 H7 -0.26 K7 -0.29 M7 -0.32 O7 -0.06 P7 -0.09 U7 -0.30 |
| TL3_UW_INJ_PRE | HOLD | 202410-202610 | 51 | 17640 -> 17807 (167) | 63185 -> 63185 (0) | -55145 -> -52563 (2582) | -42 (30) | 209 | 0.40 | A7 -0.31 H7 0.07 K7 0.03 M7 0.01 O7 -0.14 P7 -0.08 U7 -0.21 |
| TL3_UW_INJ_PRE | PREUW | 202410-202610 | 40 | 11570 -> 11901 (331) | 76186 -> 76580 (394) | -52547 -> -50920 (1628) | 388 (47) | -57 | 0.19 | A7 -0.20 H7 -0.18 K7 0.11 M7 0.24 O7 0.07 P7 -0.07 U7 0.01 |

## 4. Data honesty (lags; no-look-ahead proof, sample day per family)
LAG (spot_1m QQQ 2026-10-14): row time - start_time: min 0 s, median 58 s, max 59 s (snapshot taken inside the minute); avail used = start+60 s (>= snapshot time by construction) + EXTRA_LAG 60 s
F1 panel vs raw g_dir on 2026-10-14: 494 common minutes, max abs diff 0 (0 = identical)
F1 first d1_dn event 13:30:00 ET: decision ts 1791999000 = last used row avail 1791998940 (+60 s lag); value 5.541e+08 vs 15 min earlier 5.58e+08; entry fill path starts at ts+1 s (harness.simulate market = mid at t0+1)
  check: raw row avail <= decision ts: True ; no raw row with avail > decision ts - 60 is used
F2 gex_levels_oi SPX file 2026-10-14 computed at 2026-10-14T20:15:00.000000Z (end of day); used only for sessions starting 18:00 ET 2026-10-14 onward (label day next business day); same-day sessions of 2026-10-14 use the PRIOR file
F6 10:00 ET reading for 2026-10-14: row avail 10:00:00 ET (<= 10:00:00), value -3.161e+08; event ts = 10:00 + 60 s lag
F7 prior-close reading of 2026-10-14: row avail 16:00:00 ET (start 15:59); event 18:05 ET same date (Friday -> Sunday 18:05) + lag; London 02:00 ET next business day; pre-market 06:35 ET uses rows avail <= 06:35

## 5. Plain reading
PLAIN READING (21:30Z). Scope: NQ ES RTY YM (triggers SPX SPY QQQ NDX IWM DIA, matched and cross), GC SI CL (triggers GLD GDX SLV USO XLE XOP, own scheduled-event clocks, CL pit session), cross use of the metals/oil tickers on NQ/ES, families 1 2 6 7 + event clocks (FE) + no-UW baselines + 741 pairs. About 50k scored groups x 1,470 grid cells. STRENGTH: WEAK; nothing separates from chance after selection.
- Family 1 (exposure flips/extremes/deltas) and family 2 (levels as trade locations): the share of groups passing the tolerant gate is BELOW the shifted-time null (F1 43% vs 62-63%, F2 21% vs 50-51%) and the best recents $/wk and best Calmar sit inside the null range (F1 max recents 2,836 vs 3,077-3,223; F2 2,060 vs 3,380-3,964). No evidence of an exposure or level effect on any instrument, matched or cross (section 6b: the matched instrument does not carry its trigger better).
- Families 6, 7 and FE (morning set, prior-close / pre-market, scheduled-event clocks) pass the gate far more often than the null (F6 76% vs 44-46%, F7 91% vs 64-65%, FE 79% vs 31-33%), but so do the NO-UW baselines of the same clocks (F6B 98%, F7B 100%, FEB 76% vs 41-47% null) and the baseline best Calmar/recents are of the same size: the excess is the drift of the clock/time-of-day legs in this 2-year sample (rising market), not the UW reading. UW conditioning adds no measurable lift over its clock.
- Pairs (741, AND within 15 min): gated share 24% vs 35% null; max recents 3,345 vs 2,613-3,138; RTY best Calmar 90 vs 62-124 null. No survivor.
- Per-session best books (section 2, with spec) are thin (n 20-47 trades in L6M), have WF OOS $/wk small relative to in-sample, and placebo p 0.01-0.17 at group level; with ~50k groups ~2,500 would show p<=0.05 by chance. 2x-slippage stress changes L6M by 1-12%.
- Metals/oil: same picture (F1/F6/F7/F2/FE on GC SI CL, FE vs FEB lift none). UW pulls for the six ETFs are still arriving (about 250 of 510 days) so HOLD is partly covered; PREUW is empty for them.
- Simulator audit: independent second-by-second loop reproduces the harness on 198 of 198 checks. Seam checks, roll/glitch guard (event dropped if the 1-s path jumps > 80 NQ pts x scale, or 3 ATR5 for GC/SI/CL) and the VOID first screen are documented in MORNING.
- Not done: exact-engine joint (needs an add-a-book hook; awaiting the lead), WF/placebo for pairs, longer UW history for ETFs, forward register of 0DTE walls.
- EXACT-ENGINE JOINT (TP engine, JN05W2 base, all layers ON, hook uw_inject.py; identity: book registered with no events in the month reproduces JN05W2 202610 = 598 trades, net 25,943.82; one set per finalist, months 202410-202610 = L6M/HOLD/PREUW; stack mean ~$23k/wk, maxDD ~$36k in L6M so effects are 1-4% of the stack). Engine fills, $4.84 RT, live locks/give-back/caps and the live SCR entry gate apply to the injected book.
  * INJ_PRE (pre short SPX v_oi lo_d): stack mean +418 / +174 / +167 / +331 $/wk in L3M / L6M / HOLD / PREUW; stack maxDD -523 / -523 / 0 / +394; worst week 36.4k -> 35.8k in L6M; the book alone earns +159 $/wk in L6M (11 trades) against +1,073 in the standalone harness: 9 of 27 events were skipped by the live SCR gate and 5 of 13 entered trades were cut by BookLock (give-back lock) at +10-30 pts, i.e. the live stack rules remove most of the standalone profit. Mean positive in all four windows, DD cut in the recent two, slightly worse in PREUW: a small weak lead, not a survivor.
  * INJ_ASIA: +69 L6M, -108 L3M, PREUW -69 with maxDD +1,464 worse: no. INJ_NYAM: +573 L6M but maxDD +1,187 worse in HOLD, PREUW 0: no.
  * INJ_NDXB (W-UB2 NDX burst fade, labelled FAILED-NULL reference): +856 L6M with DD -554, +851 HOLD with DD -1,488, but PREUW -211 with DD +3,822 worse: strongest recent numbers, fails its family null and the PREUW window.
  * About half of each UW book's trades open while no other live book is open (idle share 0.2-0.6).
