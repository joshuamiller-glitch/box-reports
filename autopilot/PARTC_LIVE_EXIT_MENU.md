# PART C (Test 4): the 20 live books x 8 exit settings vs bare, EXACT (HINDSIGHT-CHOSEN BOOKS)

**LABEL: the 20 live books were picked with hindsight on this same history, and the best setting per book below is also picked with hindsight. This table says what each exit setting would have done to these books over 2023-04..2026-10; it is NOT a forward test and not evidence that any setting is better.** EXACT engine, bare R0 own bracket, 1 lot, fees in, weeks of 7 days from 2023-04-02 (2025-11 not in the data: zero weeks in every column). Code code/th_test4/partc_score4.py (re-runnable). Coverage: 6774 of 8400 set-months DONE (161 of 200 book x setting sets complete).

## ANSWER FIRST

1. **Scored: 18 of 20 live books have a complete bare series; the other 2 (L385f4f2e_CX502, B7bfd33b7) lack their bare set or exit sets (sets not built: need the D8 _CANC builder, see MORNING 18:59Z W-TEST4) and are excluded, not guessed.**
1b. **CONFOUND (read before any number): the exit-setting sets (TL3_ALN_..._BR<bracket>CEX<setting>) are NOT the bare R0 set plus one exit. Their set json carries the live hook stack (wb_hooks day cap, ec_hooks, scr_hooks, c_gov, ev_panel, ev_profit/lock/take) and cap 12000/4800, which bare R0 (no hooks, cap 0) does not have. So "vs bare R0" mixes the exit setting with the live layers; e.g. Lb0e6dfa3 bare R0 +1010 $/wk vs its live-stack BASE set +175 $/wk. The like-for-like reference is the book's BASE set (same hooks, no exit setting), which exists complete for only 7 of the 20 books; "vs BASE" columns are filled for those. Exit-setting effect alone = vs BASE where present; elsewhere the table is exit + live-layer effect and cannot be split.**
2. **No setting is a free win.** Books (of 18) where a setting beats bare on income / has a lower max DD / both: bricks3_v25 3 / 1 / 0; flowp_v15_t2 0 / 5 / 0; flow_v25 0 / 2 / 0; oppx_v15_t2 1 / 4 / 0; oppx_v25 2 / 1 / 0; sar_v15 1 / 2 / 0; sar_v40 1 / 0 / 0; v25_t2 2 / 1 / 0 (n = books scored per setting: 17, 17, 17, 17, 17, 17, 17, 17).
2b. Vs BASE (like-for-like, 7 books): bricks3_v25 beats BASE on income 2 of 5, lower max DD 0 of 5; flowp_v15_t2 beats BASE on income 0 of 5, lower max DD 0 of 5; flow_v25 beats BASE on income 0 of 5, lower max DD 0 of 5; oppx_v15_t2 beats BASE on income 0 of 5, lower max DD 2 of 5; oppx_v25 beats BASE on income 0 of 5, lower max DD 1 of 5; sar_v15 beats BASE on income 0 of 5, lower max DD 0 of 5; sar_v40 beats BASE on income 0 of 5, lower max DD 0 of 5; v25_t2 beats BASE on income 1 of 5, lower max DD 0 of 5.
3. **Best setting per book (hindsight, by income $/wk): beats bare on income for 4 of 18 books, and on income AND lower max DD for 0 of 18.** Picking the best of 8 per book from the same history flatters it by construction.
4. **Per session (sum of the scored books of the session that have every setting and bare complete, 1 lot each; books listed under the table), exact $/wk and max DD, bare vs each setting: see the session table.** Session verdict rows: Asia: bare +2070 / maxDD 15518; best setting bricks3_v25 +827 / maxDD 49658; NY AM: bare +6058 / maxDD 51442; best setting v25_t2 +3084 / maxDD 103736; NY PM: bare +2169 / maxDD 27779; best setting oppx_v15_t2 +1520 / maxDD 34486; London: bare +1036 / maxDD 22434; best setting v25_t2 +536 / maxDD 43114.

## Session table (sum of the session's scored live books, 1 lot each; exact $/wk, max DD, worst week, L6M, L3M)

| session | books | setting | $/wk | vs bare | max DD | vs bare | worst wk | L6M | L3M |
|---|---|---|---|---|---|---|---|---|---|
| Asia | 3 | BARE | +2070 |  | 15518 |  | -14804 | +6023 | +4996 |
| Asia | 3 | bricks3_v25 | +827 | -1243 | 49658 | +34140 | -15042 | +1474 | +860 |
| Asia | 3 | flowp_v15_t2 | -434 | -2504 | 85901 | +70384 | -4299 | +131 | -94 |
| Asia | 3 | flow_v25 | -934 | -3004 | 173782 | +158264 | -5764 | -980 | -850 |
| Asia | 3 | oppx_v15_t2 | +330 | -1740 | 29224 | +13707 | -10457 | +612 | +350 |
| Asia | 3 | oppx_v25 | +695 | -1375 | 41852 | +26334 | -15171 | +2286 | +2002 |
| Asia | 3 | sar_v15 | +244 | -1826 | 48142 | +32624 | -13405 | +1488 | +108 |
| Asia | 3 | sar_v40 | +788 | -1282 | 60702 | +45185 | -18597 | +2118 | +1060 |
| Asia | 3 | v25_t2 | +533 | -1537 | 48560 | +33042 | -15206 | +116 | +522 |
| NY AM | 8 | BARE | +6058 |  | 51442 |  | -40732 | +15736 | +13761 |
| NY AM | 8 | bricks3_v25 | +2504 | -3554 | 83757 | +32315 | -51053 | +327 | +4202 |
| NY AM | 8 | flowp_v15_t2 | -917 | -6976 | 202648 | +151206 | -18554 | +56 | +688 |
| NY AM | 8 | flow_v25 | -3910 | -9968 | 727383 | +675941 | -13620 | -6052 | -4910 |
| NY AM | 8 | oppx_v15_t2 | +597 | -5462 | 80825 | +29383 | -31824 | +715 | -1599 |
| NY AM | 8 | oppx_v25 | +520 | -5539 | 131660 | +80219 | -52533 | -278 | +2424 |
| NY AM | 8 | sar_v15 | -595 | -6653 | 213731 | +162289 | -42799 | -1674 | -832 |
| NY AM | 8 | sar_v40 | -141 | -6200 | 198699 | +147257 | -74216 | -2540 | +4120 |
| NY AM | 8 | v25_t2 | +3084 | -2974 | 103736 | +52294 | -48776 | +1152 | +5968 |
| NY PM | 4 | BARE | +2169 |  | 27779 |  | -11262 | +4500 | +4426 |
| NY PM | 4 | bricks3_v25 | +907 | -1262 | 59298 | +31519 | -51746 | +1202 | +1125 |
| NY PM | 4 | flowp_v15_t2 | -289 | -2458 | 53832 | +26053 | -7117 | -511 | -329 |
| NY PM | 4 | flow_v25 | -979 | -3148 | 182175 | +154396 | -5464 | -1397 | -1534 |
| NY PM | 4 | oppx_v15_t2 | +1520 | -649 | 34486 | +6708 | -20347 | +3179 | +2812 |
| NY PM | 4 | oppx_v25 | +1441 | -728 | 42379 | +14600 | -22943 | +2517 | +3260 |
| NY PM | 4 | sar_v15 | +1210 | -959 | 61437 | +33658 | -39317 | +1634 | +4535 |
| NY PM | 4 | sar_v40 | +1239 | -929 | 68032 | +40253 | -41411 | +1755 | +3447 |
| NY PM | 4 | v25_t2 | +1287 | -882 | 54963 | +27185 | -43566 | +1626 | +85 |
| London | 2 | BARE | +1036 |  | 22434 |  | -12702 | +3317 | +3803 |
| London | 2 | bricks3_v25 | -139 | -1175 | 64896 | +42462 | -8574 | -608 | +560 |
| London | 2 | flowp_v15_t2 | -985 | -2021 | 183858 | +161424 | -5049 | -1176 | -915 |
| London | 2 | flow_v25 | -1883 | -2919 | 350268 | +327834 | -8863 | -2414 | -2602 |
| London | 2 | oppx_v15_t2 | -17 | -1053 | 39778 | +17344 | -6344 | -86 | +262 |
| London | 2 | oppx_v25 | +93 | -943 | 46910 | +24477 | -9755 | +250 | +1808 |
| London | 2 | sar_v15 | -321 | -1357 | 97143 | +74709 | -10304 | -291 | +1175 |
| London | 2 | sar_v40 | -239 | -1275 | 127565 | +105132 | -15643 | +1562 | +2606 |
| London | 2 | v25_t2 | +536 | -501 | 43114 | +20680 | -11807 | +1478 | +3693 |
Session Asia books in the sum: Lb0e6dfa3_R0_F40_80, L9c2622b0_R0_P45, L4aaacdb2_R0_P30
Session NY AM books in the sum: L43f0cbfb.BRS8U, Bf428c4a1.BRS8U, Le4fede95.BRF90_30, Lf0346d55.BRP60, L8cfda948.BRF90_30, L4407508c.BRF120_60, L39287638.BRF80_40, L64390867.BRF80_40
Session NY PM books in the sum: L52359bf4_R0_P30, L8e0bf58c_R0_S8U, L4bdd521a_R0_F80_40, L2c6916a5_R0_P60
Session London books in the sum: L19201dfc.BRF90_30, L74274eca.BRF120_60

## Per live book (recent first: L3M, L6M, then whole history; exact, 1 lot)

| session | book | setting | L3M $/wk | L6M $/wk | income $/wk | vs bare | max DD | vs bare | worst wk | income vs BASE | max DD vs BASE |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | Lb0e6dfa3_R0_F40_80 | BARE | +2383 | +3333 | +1010 |  | 14602 |  | -8094 |  |  |
| Asia | Lb0e6dfa3_R0_F40_80 | BASE | -470 | -288 | +175 | -835 | 33556 | +18955 | -19446 |  |  |
| Asia | Lb0e6dfa3_R0_F40_80 | bricks3_v25 (best) | -1578 | +362 | +280 | -730 | 34954 | +20352 | -10002 | +105 | +1397 |
| Asia | Lb0e6dfa3_R0_F40_80 | flowp_v15_t2 | -267 | -235 | -324 | -1334 | 60285 | +45684 | -3853 | -499 | +26729 |
| Asia | Lb0e6dfa3_R0_F40_80 | flow_v25 | -384 | -534 | -533 | -1543 | 99174 | +84572 | -1893 | -708 | +65617 |
| Asia | Lb0e6dfa3_R0_F40_80 | oppx_v15_t2 | -409 | +349 | +23 | -987 | 24843 | +10241 | -5724 | -151 | -8714 |
| Asia | Lb0e6dfa3_R0_F40_80 | oppx_v25 | -567 | +201 | +147 | -863 | 22868 | +8267 | -6101 | -28 | -10688 |
| Asia | Lb0e6dfa3_R0_F40_80 | sar_v15 | -1997 | -74 | -127 | -1136 | 46833 | +32231 | -9914 | -301 | +13277 |
| Asia | Lb0e6dfa3_R0_F40_80 | sar_v40 | -1791 | -43 | +45 | -965 | 60948 | +46346 | -13407 | -130 | +27391 |
| Asia | Lb0e6dfa3_R0_F40_80 | v25_t2 | -445 | -555 | +148 | -862 | 49760 | +35158 | -8192 | -27 | +16204 |
| Asia | L9c2622b0_R0_P45 | BARE | +1915 | +2018 | +795 |  | 12784 |  | -6377 |  |  |
| Asia | L9c2622b0_R0_P45 | BASE | +1133 | +1341 | +600 | -195 | 15172 | +2388 | -7865 |  |  |
| Asia | L9c2622b0_R0_P45 | bricks3_v25 | +1168 | +487 | +266 | -530 | 26308 | +13524 | -8397 | -334 | +11136 |
| Asia | L9c2622b0_R0_P45 | flowp_v15_t2 | +119 | +344 | -78 | -873 | 25000 | +12216 | -2544 | -678 | +9828 |
| Asia | L9c2622b0_R0_P45 | flow_v25 | -337 | -333 | -288 | -1083 | 55678 | +42893 | -4248 | -888 | +40505 |
| Asia | L9c2622b0_R0_P45 | oppx_v15_t2 | +635 | +229 | +117 | -678 | 9938 | -2847 | -4175 | -483 | -5235 |
| Asia | L9c2622b0_R0_P45 | oppx_v25 | +1424 | +1354 | +348 | -447 | 18967 | +6183 | -7887 | -252 | +3795 |
| Asia | L9c2622b0_R0_P45 | sar_v15 | +1502 | +1336 | +213 | -582 | 20360 | +7576 | -7235 | -387 | +5188 |
| Asia | L9c2622b0_R0_P45 | sar_v40 (best) | +1726 | +1873 | +517 | -278 | 17330 | +4545 | -9895 | -83 | +2157 |
| Asia | L9c2622b0_R0_P45 | v25_t2 | +331 | +581 | +175 | -621 | 20791 | +8006 | -8919 | -425 | +5619 |
| Asia | L4aaacdb2_R0_P30 | BARE | +698 | +672 | +265 |  | 4820 |  | -3422 |  |  |
| Asia | L4aaacdb2_R0_P30 | bricks3_v25 (best) | +1270 | +625 | +282 | +17 | 9611 | +4790 | -6193 |  |  |
| Asia | L4aaacdb2_R0_P30 | flowp_v15_t2 | +54 | +21 | -32 | -297 | 9941 | +5120 | -1534 |  |  |
| Asia | L4aaacdb2_R0_P30 | flow_v25 | -130 | -113 | -113 | -378 | 21109 | +16289 | -1705 |  |  |
| Asia | L4aaacdb2_R0_P30 | oppx_v15_t2 | +124 | +34 | +189 | -75 | 12570 | +7749 | -5715 |  |  |
| Asia | L4aaacdb2_R0_P30 | oppx_v25 | +1145 | +731 | +199 | -65 | 16505 | +11685 | -7035 |  |  |
| Asia | L4aaacdb2_R0_P30 | sar_v15 | +602 | +226 | +157 | -108 | 11016 | +6196 | -6405 |  |  |
| Asia | L4aaacdb2_R0_P30 | sar_v40 | +1125 | +287 | +227 | -38 | 18873 | +14053 | -7790 |  |  |
| Asia | L4aaacdb2_R0_P30 | v25_t2 | +635 | +91 | +211 | -54 | 13197 | +8376 | -5869 |  |  |
| NY AM | L43f0cbfb.BRS8U | BARE | +4562 | +4086 | +1558 |  | 23360 |  | -14925 |  |  |
| NY AM | L43f0cbfb.BRS8U | BASE | -255 | +813 | +602 | -957 | 26893 | +3533 | -12503 |  |  |
| NY AM | L43f0cbfb.BRS8U | bricks3_v25 (best) | +122 | +153 | +711 | -847 | 32236 | +8876 | -13881 | +109 | +5343 |
| NY AM | L43f0cbfb.BRS8U | flowp_v15_t2 | +528 | -209 | -164 | -1722 | 64819 | +41459 | -7079 | -766 | +37926 |
| NY AM | L43f0cbfb.BRS8U | flow_v25 | -1208 | -1241 | -841 | -2399 | 156447 | +133087 | -7555 | -1443 | +129554 |
| NY AM | L43f0cbfb.BRS8U | oppx_v15_t2 | -1000 | -752 | -235 | -1794 | 61752 | +38392 | -12994 | -837 | +34859 |
| NY AM | L43f0cbfb.BRS8U | oppx_v25 | -928 | -591 | -292 | -1850 | 69440 | +46080 | -10822 | -893 | +42546 |
| NY AM | L43f0cbfb.BRS8U | sar_v15 | -1186 | -801 | -387 | -1946 | 101946 | +78586 | -13660 | -989 | +75053 |
| NY AM | L43f0cbfb.BRS8U | sar_v40 | -882 | -1278 | -777 | -2336 | 151553 | +128193 | -21687 | -1379 | +124660 |
| NY AM | L43f0cbfb.BRS8U | v25_t2 | -315 | +114 | +634 | -924 | 30348 | +6988 | -12300 | +32 | +3455 |
| NY AM | Bf428c4a1.BRS8U | BARE | +493 | +1858 | +801 |  | 27410 |  | -10040 |  |  |
| NY AM | Bf428c4a1.BRS8U | BASE | -142 | +1216 | +661 | -140 | 23262 | -4148 | -8080 |  |  |
| NY AM | Bf428c4a1.BRS8U | bricks3_v25 | -192 | +261 | -43 | -844 | 39465 | +12055 | -9317 | -704 | +16203 |
| NY AM | Bf428c4a1.BRS8U | flowp_v15_t2 | -109 | -264 | -225 | -1026 | 43780 | +16370 | -8002 | -886 | +20518 |
| NY AM | Bf428c4a1.BRS8U | flow_v25 | -703 | -1059 | -545 | -1347 | 102202 | +74792 | -3558 | -1207 | +78940 |
| NY AM | Bf428c4a1.BRS8U | oppx_v15_t2 | -970 | -373 | -165 | -966 | 40290 | +12880 | -11354 | -826 | +17028 |
| NY AM | Bf428c4a1.BRS8U | oppx_v25 | +163 | -673 | -290 | -1092 | 72864 | +45454 | -12897 | -952 | +49602 |
| NY AM | Bf428c4a1.BRS8U | sar_v15 | -234 | -959 | -590 | -1391 | 132211 | +104801 | -17137 | -1251 | +108949 |
| NY AM | Bf428c4a1.BRS8U | sar_v40 | -175 | -2195 | -455 | -1256 | 128382 | +100972 | -21995 | -1116 | +105120 |
| NY AM | Bf428c4a1.BRS8U | v25_t2 (best) | +1410 | +529 | +489 | -313 | 29522 | +2112 | -7589 | -173 | +6260 |
| NY AM | Le4fede95.BRF90_30 | BARE | +2350 | +2888 | +785 |  | 26597 |  | -14920 |  |  |
| NY AM | Le4fede95.BRF90_30 | BASE | +3066 | +873 | +973 | +187 | 30195 | +3598 | -17460 |  |  |
| NY AM | Le4fede95.BRF90_30 | bricks3_v25 (best) | +1539 | -287 | +831 | +46 | 38704 | +12107 | -14836 | -142 | +8509 |
| NY AM | Le4fede95.BRF90_30 | flowp_v15_t2 | +513 | +292 | -337 | -1122 | 77660 | +51063 | -9890 | -1310 | +47465 |
| NY AM | Le4fede95.BRF90_30 | flow_v25 | -1474 | -2196 | -1393 | -2178 | 259106 | +232508 | -9938 | -2366 | +228910 |
| NY AM | Le4fede95.BRF90_30 | oppx_v15_t2 | -6 | +144 | +111 | -674 | 30271 | +3673 | -11028 | -861 | +75 |
| NY AM | Le4fede95.BRF90_30 | oppx_v25 | +915 | +1031 | -8 | -793 | 47746 | +21149 | -11031 | -981 | +17551 |
| NY AM | Le4fede95.BRF90_30 | sar_v15 | -210 | -173 | -325 | -1111 | 79112 | +52514 | -10900 | -1298 | +48916 |
| NY AM | Le4fede95.BRF90_30 | sar_v40 | +1888 | +679 | -401 | -1187 | 107726 | +81128 | -16012 | -1374 | +77530 |
| NY AM | Le4fede95.BRF90_30 | v25_t2 | +2382 | +71 | +703 | -83 | 40042 | +13445 | -16099 | -270 | +9847 |
| NY AM | Lf0346d55.BRP60 | BARE | +1788 | +1503 | +728 |  | 32173 |  | -16861 |  |  |
| NY AM | Lf0346d55.BRP60 | bricks3_v25 | -866 | -641 | -63 | -791 | 51489 | +19315 | -8448 |  |  |
| NY AM | Lf0346d55.BRP60 | flowp_v15_t2 | -379 | -108 | -162 | -890 | 34355 | +2181 | -3896 |  |  |
| NY AM | Lf0346d55.BRP60 | flow_v25 | -641 | -815 | -526 | -1255 | 98071 | +65898 | -6937 |  |  |
| NY AM | Lf0346d55.BRP60 | oppx_v15_t2 | -565 | +239 | +143 | -585 | 11195 | -20978 | -4845 |  |  |
| NY AM | Lf0346d55.BRP60 | oppx_v25 | -521 | -483 | -83 | -811 | 60290 | +28117 | -8427 |  |  |
| NY AM | Lf0346d55.BRP60 | sar_v15 | -640 | -96 | +27 | -701 | 29905 | -2269 | -7594 |  |  |
| NY AM | Lf0346d55.BRP60 | sar_v40 | -2225 | -927 | -58 | -786 | 70930 | +38756 | -14250 |  |  |
| NY AM | Lf0346d55.BRP60 | v25_t2 (best) | -706 | -306 | +214 | -514 | 21909 | -10265 | -8373 |  |  |
| NY AM | L8cfda948.BRF90_30 | BARE | +2115 | +2308 | +745 |  | 34723 |  | -8437 |  |  |
| NY AM | L8cfda948.BRF90_30 | bricks3_v25 | +171 | +494 | +547 | -199 | 28507 | -6216 | -10448 |  |  |
| NY AM | L8cfda948.BRF90_30 | flowp_v15_t2 | +545 | +250 | +36 | -709 | 16302 | -18421 | -4812 |  |  |
| NY AM | L8cfda948.BRF90_30 | flow_v25 | -661 | -519 | -335 | -1080 | 63258 | +28535 | -4220 |  |  |
| NY AM | L8cfda948.BRF90_30 | oppx_v15_t2 | +220 | +1789 | +450 | -296 | 31246 | -3477 | -9330 |  |  |
| NY AM | L8cfda948.BRF90_30 | oppx_v25 | +171 | +494 | +547 | -199 | 28507 | -6216 | -10448 |  |  |
| NY AM | L8cfda948.BRF90_30 | sar_v15 (best) | +731 | +982 | +552 | -194 | 22514 | -12208 | -9330 |  |  |
| NY AM | L8cfda948.BRF90_30 | sar_v40 | +412 | +655 | +517 | -229 | 38091 | +3368 | -10916 |  |  |
| NY AM | L8cfda948.BRF90_30 | v25_t2 | +265 | +145 | +395 | -351 | 37341 | +2618 | -10448 |  |  |
| NY AM | L4407508c.BRF120_60 | BARE | +1515 | +1566 | +610 |  | 14564 |  | -9167 |  |  |
| NY AM | L4407508c.BRF120_60 | bricks3_v25 | +2084 | +393 | +231 | -380 | 23784 | +9220 | -10293 |  |  |
| NY AM | L4407508c.BRF120_60 | flowp_v15_t2 | -213 | -75 | +0 | -611 | 8705 | -5860 | -3395 |  |  |
| NY AM | L4407508c.BRF120_60 | flow_v25 | -79 | -73 | -93 | -704 | 17898 | +3334 | -2239 |  |  |
| NY AM | L4407508c.BRF120_60 | oppx_v15_t2 | +691 | -112 | +126 | -484 | 16317 | +1753 | -9845 |  |  |
| NY AM | L4407508c.BRF120_60 | oppx_v25 | +1881 | +237 | +227 | -384 | 27397 | +12833 | -11973 |  |  |
| NY AM | L4407508c.BRF120_60 | sar_v15 | +1168 | +239 | +154 | -457 | 24192 | +9628 | -9845 |  |  |
| NY AM | L4407508c.BRF120_60 | sar_v40 (best) | +1966 | -91 | +393 | -218 | 33607 | +19043 | -15267 |  |  |
| NY AM | L4407508c.BRF120_60 | v25_t2 | +1294 | +61 | +127 | -483 | 23672 | +9108 | -11973 |  |  |
| NY AM | L39287638.BRF80_40 | BARE | +644 | +1080 | +496 |  | 13622 |  | -6878 |  |  |
| NY AM | L39287638.BRF80_40 | bricks3_v25 | -174 | +45 | -29 | -526 | 26642 | +13020 | -8622 |  |  |
| NY AM | L39287638.BRF80_40 | flowp_v15_t2 | -164 | +10 | -15 | -511 | 8242 | -5380 | -3785 |  |  |
| NY AM | L39287638.BRF80_40 | flow_v25 | -101 | -53 | -94 | -590 | 18502 | +4880 | -1710 |  |  |
| NY AM | L39287638.BRF80_40 | oppx_v15_t2 | -932 | -81 | -9 | -505 | 14843 | +1221 | -6140 |  |  |
| NY AM | L39287638.BRF80_40 | oppx_v25 | -817 | -307 | +61 | -435 | 20779 | +7157 | -9014 |  |  |
| NY AM | L39287638.BRF80_40 | sar_v15 | -1086 | -348 | -175 | -671 | 39259 | +25637 | -8436 |  |  |
| NY AM | L39287638.BRF80_40 | sar_v40 (best) | +1204 | +185 | +242 | -255 | 29115 | +15493 | -10721 |  |  |
| NY AM | L39287638.BRF80_40 | v25_t2 | +29 | +488 | +178 | -318 | 18254 | +4632 | -8939 |  |  |
| NY AM | L64390867.BRF80_40 | BARE | +294 | +448 | +333 |  | 21061 |  | -5282 |  |  |
| NY AM | L64390867.BRF80_40 | bricks3_v25 | +1518 | -91 | +320 | -13 | 30669 | +9608 | -12185 |  |  |
| NY AM | L64390867.BRF80_40 | flowp_v15_t2 | -32 | +160 | -51 | -384 | 16170 | -4891 | -5169 |  |  |
| NY AM | L64390867.BRF80_40 | flow_v25 | -42 | -95 | -82 | -415 | 15233 | -5829 | -1266 |  |  |
| NY AM | L64390867.BRF80_40 | oppx_v15_t2 | +963 | -139 | +176 | -158 | 34333 | +13271 | -7855 |  |  |
| NY AM | L64390867.BRF80_40 | oppx_v25 | +1561 | +14 | +358 | +25 | 27009 | +5948 | -12185 |  |  |
| NY AM | L64390867.BRF80_40 | sar_v15 | +624 | -517 | +151 | -182 | 43988 | +22927 | -7855 |  |  |
| NY AM | L64390867.BRF80_40 | sar_v40 (best) | +1932 | +430 | +400 | +66 | 27120 | +6059 | -8923 |  |  |
| NY AM | L64390867.BRF80_40 | v25_t2 | +1609 | +50 | +345 | +11 | 24979 | +3918 | -12185 |  |  |
| NY PM | L52359bf4_R0_P30 | BARE | +640 | +1307 | +652 |  | 16916 |  | -5701 |  |  |
| NY PM | L52359bf4_R0_P30 | bricks3_v25 | +1465 | +187 | +176 | -476 | 35806 | +18890 | -14642 |  |  |
| NY PM | L52359bf4_R0_P30 | flowp_v15_t2 | -143 | +4 | -118 | -770 | 27837 | +10921 | -3669 |  |  |
| NY PM | L52359bf4_R0_P30 | flow_v25 | -386 | -452 | -418 | -1070 | 77791 | +60875 | -3265 |  |  |
| NY PM | L52359bf4_R0_P30 | oppx_v15_t2 | +312 | +797 | +327 | -325 | 20882 | +3966 | -4964 |  |  |
| NY PM | L52359bf4_R0_P30 | oppx_v25 (best) | +1165 | +1522 | +548 | -103 | 27836 | +10920 | -6536 |  |  |
| NY PM | L52359bf4_R0_P30 | sar_v15 | +1095 | +487 | +305 | -347 | 33545 | +16629 | -16015 |  |  |
| NY PM | L52359bf4_R0_P30 | sar_v40 | +151 | +659 | +330 | -322 | 37604 | +20688 | -14780 |  |  |
| NY PM | L52359bf4_R0_P30 | v25_t2 | +539 | -247 | +265 | -387 | 29697 | +12781 | -8858 |  |  |
| NY PM | L8e0bf58c_R0_S8U | BARE | +1913 | +1279 | +486 |  | 18383 |  | -7080 |  |  |
| NY PM | L8e0bf58c_R0_S8U | bricks3_v25 | +497 | +858 | +301 | -185 | 41614 | +23231 | -24353 |  |  |
| NY PM | L8e0bf58c_R0_S8U | flowp_v15_t2 | +171 | -52 | +64 | -422 | 9550 | -8833 | -6012 |  |  |
| NY PM | L8e0bf58c_R0_S8U | flow_v25 | -257 | -113 | -105 | -591 | 19590 | +1207 | -1891 |  |  |
| NY PM | L8e0bf58c_R0_S8U | oppx_v15_t2 (best) | +2024 | +1318 | +435 | -51 | 23248 | +4864 | -12876 |  |  |
| NY PM | L8e0bf58c_R0_S8U | oppx_v25 | +1123 | +483 | +342 | -144 | 23809 | +5425 | -11272 |  |  |
| NY PM | L8e0bf58c_R0_S8U | sar_v15 | +1393 | -18 | +332 | -154 | 42773 | +24389 | -12360 |  |  |
| NY PM | L8e0bf58c_R0_S8U | sar_v40 | +849 | +61 | +412 | -75 | 36304 | +17921 | -11372 |  |  |
| NY PM | L8e0bf58c_R0_S8U | v25_t2 | +629 | +1620 | +224 | -262 | 69188 | +50804 | -27880 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | BARE | +736 | +784 | +602 |  | 14817 |  | -5965 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | bricks3_v25 | -474 | +828 | +729 | +127 | 20988 | +6172 | -10817 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | flowp_v15_t2 | +76 | -192 | -71 | -673 | 20632 | +5816 | -3434 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | flow_v25 | -241 | -228 | -51 | -653 | 9682 | -5135 | -1055 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | oppx_v15_t2 | +516 | +1116 | +760 | +158 | 30442 | +15625 | -7233 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | oppx_v25 | +1040 | +1207 | +683 | +81 | 21292 | +6476 | -7572 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | sar_v15 | +1536 | +1335 | +650 | +48 | 33353 | +18537 | -7233 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | sar_v40 | +2573 | +1670 | +549 | -52 | 31162 | +16346 | -9660 |  |  |
| NY PM | L4bdd521a_R0_F80_40 | v25_t2 (best) | -1031 | +598 | +817 | +215 | 22558 | +7741 | -13522 |  |  |
| NY PM | L2c6916a5_R0_P60 | BARE | +1137 | +1130 | +429 |  | 17868 |  | -6744 |  |  |
| NY PM | L2c6916a5_R0_P60 | bricks3_v25 | -363 | -672 | -299 | -728 | 58489 | +40622 | -8269 |  |  |
| NY PM | L2c6916a5_R0_P60 | flowp_v15_t2 | -434 | -271 | -165 | -594 | 31737 | +13869 | -2141 |  |  |
| NY PM | L2c6916a5_R0_P60 | flow_v25 | -650 | -603 | -405 | -834 | 75758 | +57890 | -3006 |  |  |
| NY PM | L2c6916a5_R0_P60 | oppx_v15_t2 (best) | -40 | -52 | -2 | -431 | 14614 | -3254 | -2537 |  |  |
| NY PM | L2c6916a5_R0_P60 | oppx_v25 | -69 | -695 | -133 | -561 | 43668 | +25801 | -8412 |  |  |
| NY PM | L2c6916a5_R0_P60 | sar_v15 | +511 | -171 | -77 | -506 | 34011 | +16143 | -12540 |  |  |
| NY PM | L2c6916a5_R0_P60 | sar_v40 | -125 | -635 | -52 | -481 | 49648 | +31781 | -22369 |  |  |
| NY PM | L2c6916a5_R0_P60 | v25_t2 | -53 | -344 | -19 | -448 | 27484 | +9617 | -6954 |  |  |
| London | L19201dfc.BRF90_30 | BARE | +1414 | +1782 | +447 |  | 10181 |  | -5841 |  |  |
| London | L19201dfc.BRF90_30 | bricks3_v25 | +1333 | +483 | +131 | -317 | 29932 | +19751 | -5405 |  |  |
| London | L19201dfc.BRF90_30 | flowp_v15_t2 | +236 | -38 | -50 | -497 | 14618 | +4436 | -2611 |  |  |
| London | L19201dfc.BRF90_30 | flow_v25 | -233 | -338 | -170 | -618 | 32142 | +21960 | -2341 |  |  |
| London | L19201dfc.BRF90_30 | oppx_v15_t2 | +670 | +385 | +207 | -240 | 21494 | +11312 | -5257 |  |  |
| London | L19201dfc.BRF90_30 | oppx_v25 | +1832 | +1144 | +288 | -159 | 40282 | +30101 | -8255 |  |  |
| London | L19201dfc.BRF90_30 | sar_v15 | +1522 | +537 | +156 | -291 | 36589 | +26408 | -4487 |  |  |
| London | L19201dfc.BRF90_30 | sar_v40 (best) | +3016 | +2067 | +382 | -66 | 54559 | +44378 | -9242 |  |  |
| London | L19201dfc.BRF90_30 | v25_t2 | +1710 | +881 | +300 | -148 | 33079 | +22898 | -6960 |  |  |
| London | L12842dde.BRP45 | BARE | +1759 | +1402 | +513 |  | 30275 |  | -13150 |  |  |
| London | L12842dde.BRP45 | bricks3_v25 | not landed (0 of 42 months) | | | | | | | | |
| London | L12842dde.BRP45 | flowp_v15_t2 | not landed (0 of 42 months) | | | | | | | | |
| London | L12842dde.BRP45 | flow_v25 | not landed (0 of 42 months) | | | | | | | | |
| London | L12842dde.BRP45 | oppx_v15_t2 | not landed (0 of 42 months) | | | | | | | | |
| London | L12842dde.BRP45 | oppx_v25 | not landed (0 of 42 months) | | | | | | | | |
| London | L12842dde.BRP45 | sar_v15 | not landed (0 of 42 months) | | | | | | | | |
| London | L12842dde.BRP45 | sar_v40 | not landed (0 of 42 months) | | | | | | | | |
| London | L12842dde.BRP45 | v25_t2 | not landed (0 of 42 months) | | | | | | | | |
| London | L74274eca.BRF120_60 | BARE | +2389 | +1535 | +589 |  | 20509 |  | -11448 |  |  |
| London | L74274eca.BRF120_60 | bricks3_v25 | -774 | -1091 | -270 | -859 | 56752 | +36244 | -5409 |  |  |
| London | L74274eca.BRF120_60 | flowp_v15_t2 | -1150 | -1138 | -935 | -1524 | 174615 | +154106 | -3774 |  |  |
| London | L74274eca.BRF120_60 | flow_v25 | -2369 | -2076 | -1713 | -2302 | 318631 | +298122 | -6522 |  |  |
| London | L74274eca.BRF120_60 | oppx_v15_t2 | -409 | -471 | -224 | -812 | 51683 | +31174 | -3678 |  |  |
| London | L74274eca.BRF120_60 | oppx_v25 | -24 | -894 | -195 | -783 | 48999 | +28490 | -5495 |  |  |
| London | L74274eca.BRF120_60 | sar_v15 | -347 | -828 | -478 | -1066 | 99236 | +78727 | -6445 |  |  |
| London | L74274eca.BRF120_60 | sar_v40 | -410 | -506 | -620 | -1209 | 126173 | +105664 | -12978 |  |  |
| London | L74274eca.BRF120_60 | v25_t2 (best) | +1983 | +597 | +236 | -353 | 35714 | +15205 | -7545 |  |  |
