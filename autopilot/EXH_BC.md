# EXH_BC - loss families B (book-state) and C (flow), EX-LBC; generated 2026-11-09 05:44Z
Entry match label: PRE-PROOF. The live-week column is the HELD-OUT week: the 186 actual live trades with the EX-FEAT live panel (feat_live), delta vs the actual live exit; it is computed for book-level rows only. Features: EX-FEAT panels, all 44 months 202304-202611 (full history). Rules: each alone as a market cut (decision k, execute k+1 at mid -+ 0.80), armed on adverse excursion ARM (latch = armed once; cur = current), persistence 1-20 s, threshold lattice per prereg (DECISIONS 2026-11-09T02:57Z).
Screened: 63 features x 432 rule-thresholds x 7 persistence x 16 arms x 2 arm modes = 96,768 cells, all 77 scopes each (bc/screen_*.parquet). Ledgered with score_cell (null_ver 2): 134 cells = the top per scope by the drawdown-first key. Family p covers ledgered cells only, so it is optimistic against 96,768 screened.
Causality: noise-after-k0 test on the lattice kernel (6 features, k0 = 300 and 900 s, mid and feature replaced after k0): 2,729,879 fires at <= k0 checked, 0 changed. Pass.
Label rules: EXH_API section 3 (ENTER / CANDIDATE-DD / LEAD / no). A cell is picked per book (sessions pooled) by (L6M maxDD, worst-20, Ulcer, -mean), valid = nfire>=20, L6M mean >= never-cut, PRE maxDD <= never*1.05.

## ALL loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -507835.58, "dd_never": 153255.2, "dd_wf": 153255.2, "share_pos": 0.37, "npick": 28, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 35468 / 31777 / 14768 / 20752 / 13342 / 12409 / 16843 / 950; maxDD L6M 121381 PRE 152455 w20 L6M 77580. Live S1b-COMB: mean 11588 / 31519 / 16583 / 23991 / 15430 / 18454 / 14960 / 902; maxDD L6M 82873 PRE 144002 w20 L6M 190560.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 5 latch arm pct 0.3 | 5232 | 29550 | 19284 | 21427 | 8082 | -4792 | 6905 | 1564 | 36812/121381 | 107422/152455 | 127045/77580 | 10337 | 0.02 | 1.00 | -95004 | -30237 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 8 latch arm pct 0.3 | 5823 | 30900 | 20879 | 22557 | 8667 | -3968 | 7496 | 1641 | 42380/121381 | 114256/152455 | 175762/77580 | 10006 | 0.02 | 1.00 | -91150 | -29645 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w10 | thr 9 pers 20 latch arm abs 25 | 21262 | 21763 | 15626 | 22878 | 12062 | 1359 | 9724 | 4040 | 43600/121381 | 109576/152455 | 208464/77580 | 7412 | 0.02 | 1.00 | -57539 | -14206 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| dlt_med_w30 | thr -28.69 pers 3 latch arm abs 20 | 23137 | 24408 | 15593 | 20854 | 9374 | -4616 | 2596 | 3509 | 46558/121381 | 144646/152455 | 131274/77580 | 12368 | 0.02 | 1.00 | -38873 | -12331 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep4_w10 | thr 4 pers 8 cur arm pct 0.15 | -506 | 17313 | 10193 | 21393 | 9029 | 4898 | 6358 | 3617 | 47240/121381 | 154974/152455 | 103287/77580 | 10687 | 0.20 | 1.00 | -117995 | -35974 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |

ALL loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 4 for 5 s, armed latch 0.3); L6M maxDD 36812 vs 121381 never-cut (live line 82873), L6M mean 21427 vs 20752 never-cut, PRE maxDD 107422 vs 152455; placebo p 0.02, family p 1.00, live week delta -95004; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 10 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 14 pers 20 latch arm abs 25 | 20638 | 30363 | 20134 | 27094 | 15456 | 4062 | 13547 | 900 | 69144/121381 | 148955/152455 | 233015/77580 | 3158 | 0.02 | 1.00 | -28027 | -14830 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w10 | thr 22 pers 12 latch arm abs 40 | 28383 | 34985 | 21128 | 27372 | 14976 | 5980 | 15292 | 1048 | 71641/121381 | 112350/152455 | 233478/77580 | 3024 | 0.02 | 1.00 | 3485 | -7085 | ok | CANDIDATE-DD |
| retr_w10 | thr 14 pers 20 latch arm abs 20 | 22035 | 29142 | 20887 | 28562 | 15594 | 2481 | 13128 | 288 | 74855/121381 | 134881/152455 | 259300/77580 | 3557 | 0.23 | 1.00 | -30189 | -13433 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## K7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -112667.0, "dd_never": 42831.12, "dd_wf": 40803.98, "share_pos": 0.26, "npick": 28, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 4952 / 8594 / 3828 / 3245 / 2177 / 829 / 2881 / 595; maxDD L6M 20902 PRE 26707 w20 L6M 1791. Live S1b-COMB: mean 7873 / 8450 / 3532 / 3232 / 1955 / 2979 / 2738 / 436; maxDD L6M 41849 PRE 23073 w20 L6M -20339.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 12 latch arm abs 10 | 1104 | 6026 | 5102 | 3657 | 1688 | -240 | 1481 | -19 | 5514/20902 | 27025/26707 | 25164/1791 | 3787 | 0.11 | 1.00 | -15890 | -3848 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep4_w10 | thr 4 pers 12 latch arm abs 10 | 684 | 5120 | 3083 | 3606 | 1790 | 1366 | 1446 | -32 | 9097/20902 | 23670/26707 | 13419/1791 | 3060 | 0.57 | 1.00 | -11824 | -4268 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep4_w10 | thr 4 pers 12 latch arm pct 0.15 | 1937 | 5428 | 3187 | 3551 | 1754 | 1247 | 1508 | -3 | 10702/20902 | 26726/26707 | 15505/1791 | 3113 | 0.68 | 1.00 | -11352 | -3014 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 20 cur arm abs 15 | 4922 | 7055 | 4542 | 5302 | 3156 | 1966 | 1978 | -243 | 10790/20902 | 18946/26707 | 28688/1791 | 2471 | 0.17 | 1.00 | -6625 | -29 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 20 cur arm pct 0.3 | 6037 | 8329 | 5256 | 5646 | 3360 | 2377 | 2201 | 167 | 11354/20902 | 17706/26707 | 33167/1791 | 2319 | 0.03 | 1.00 | -5284 | 1085 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |

K7 loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 4 for 12 s, armed latch 10); L6M maxDD 5514 vs 20902 never-cut (live line 41849), L6M mean 3657 vs 3245 never-cut, PRE maxDD 27025 vs 26707; placebo p 0.11, family p 1.00, live week delta -15890; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 5 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 20 cur arm pct 0.3 | 6037 | 8329 | 5256 | 5646 | 3360 | 2377 | 2201 | 167 | 11354/20902 | 17706/26707 | 33167/1791 | 2319 | 0.03 | 1.00 | -5284 | 1085 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| dlt_med_w30 | thr -52.16 pers 2 cur arm pct 0.15 | 7175 | 6645 | 3459 | 3602 | 2349 | 1189 | 2389 | 698 | 11759/20902 | 23921/26707 | 21340/1791 | 2553 | 0.86 | 1.00 | -6326 | -1202 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| dlt_med_w30 | thr -52.16 pers 2 cur arm abs 20 | 6120 | 5957 | 2860 | 3878 | 2688 | 1084 | 2853 | 288 | 13741/20902 | 18069/26707 | 24874/1791 | 2180 | 0.95 | 1.00 | -2900 | 495 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## P7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -159453.01, "dd_never": 144369.91, "dd_wf": 124747.88, "share_pos": 0.43, "npick": 31, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 33625 / 22555 / 13873 / 11894 / 8318 / 6680 / 8641 / -628; maxDD L6M 133887 PRE 109442 w20 L6M -29902. Live S1b-COMB: mean 5700 / 18966 / 12054 / 14708 / 10485 / 8283 / 6746 / -321; maxDD L6M 96490 PRE 106914 w20 L6M 53844.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 6 pers 1 latch arm abs 10 | 25653 | 31594 | 23256 | 22753 | 9606 | -3335 | 4064 | -607 | 36977/133887 | 78726/109442 | 264422/-29902 | 1891 | 0.02 | 1.00 | -71288 | -7972 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep4_w10 | thr 4 pers 8 cur arm abs 15 | 7362 | 15882 | 11850 | 18700 | 9890 | -6458 | 3858 | -725 | 37113/133887 | 89280/109442 | 161302/-29902 | 2301 | 0.02 | 1.00 | -83434 | -26264 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w10 | thr 22 pers 5 cur arm pct 0.3 | 2450 | 12900 | 9942 | 13651 | 7076 | 2474 | 1344 | 958 | 40579/133887 | 76049/109442 | 94591/-29902 | 2794 | 0.02 | 1.00 | -75937 | -31175 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep4_w10 | thr 4 pers 8 cur arm pct 0.15 | -969 | 12460 | 9579 | 17487 | 7189 | -5218 | 2684 | 15 | 41466/133887 | 100647/109442 | 113523/-29902 | 2534 | 0.02 | 1.00 | -105237 | -34594 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 6 pers 1 latch arm pct 0.15 | 24336 | 30945 | 23039 | 22801 | 9164 | -2462 | 4112 | -444 | 41615/133887 | 76035/109442 | 271730/-29902 | 1901 | 0.02 | 1.00 | -82335 | -9289 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |

P7 loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 6 for 1 s, armed latch 10); L6M maxDD 36977 vs 133887 never-cut (live line 96490), L6M mean 22753 vs 11894 never-cut, PRE maxDD 78726 vs 109442; placebo p 0.02, family p 1.00, live week delta -71288; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 14 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 14 pers 20 latch arm abs 10 | 16754 | 21012 | 18305 | 21837 | 11645 | 2372 | 6097 | -2038 | 56327/133887 | 99925/109442 | 203969/-29902 | 1022 | 0.02 | 1.00 | -24551 | -16871 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w10 | thr 9 pers 20 latch arm abs 35 | 29230 | 23604 | 18505 | 17132 | 7760 | 499 | 8189 | -18 | 65982/133887 | 82562/109442 | 122503/-29902 | 1349 | 0.02 | 1.00 | -16630 | -4395 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w10 | thr 14 pers 20 latch arm abs 15 | 21507 | 20394 | 15662 | 19910 | 11235 | 3171 | 6179 | -1983 | 66983/133887 | 109020/109442 | 172311/-29902 | 930 | 0.02 | 1.00 | -19851 | -12118 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## M7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -61223.0, "dd_never": 68802.24, "dd_wf": 77402.96, "share_pos": 0.4, "npick": 30, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 419 / 4773 / 1552 / 526 / 12 / 32 / -93 / -107; maxDD L6M 44425 PRE 50321 w20 L6M -68299. Live S1b-COMB: mean 40 / 3817 / 592 / -555 / -623 / 1825 / 373 / 28; maxDD L6M 46547 PRE 25812 w20 L6M -64633.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 3 latch arm abs 20 | -413 | 1451 | 926 | 58 | -79 | 734 | -144 | -61 | 22535/44425 | 41974/50321 | -32527/-68299 | 2175 | 0.17 | 1.00 | -3521 | -832 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 2 latch arm abs 20 | -349 | 1439 | 905 | -3 | -85 | 736 | -190 | -99 | 25180/44425 | 41486/50321 | -34792/-68299 | 2189 | 0.32 | 1.00 | -3451 | -767 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 1 latch arm abs 20 | -395 | 1583 | 1049 | 64 | -77 | 644 | -222 | -179 | 25636/44425 | 41853/50321 | -36446/-68299 | 2204 | 0.29 | 1.00 | -3289 | -813 | ok | CANDIDATE-DD |
| retr_w10 | thr 14 pers 8 cur arm pct 0.6 | 1284 | 2288 | 665 | -29 | -836 | -94 | -186 | -374 | 28479/44425 | 45015/50321 | -41041/-68299 | 2010 | 0.08 | 1.00 | 947 | 456 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 5 latch arm abs 20 | -524 | 1504 | 768 | -85 | -112 | 695 | -102 | -48 | 28851/44425 | 37508/50321 | -38211/-68299 | 2134 | 0.12 | 1.00 | -3200 | -943 | ok | CANDIDATE-DD |

M7 loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 4 for 3 s, armed latch 20); L6M maxDD 22535 vs 44425 never-cut (live line 46547), L6M mean 58 vs -540 never-cut, PRE maxDD 41974 vs 50321; placebo p 0.17, family p 1.00, live week delta -3521; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 23 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 3 latch arm abs 20 | -413 | 1451 | 926 | 58 | -79 | 734 | -144 | -61 | 22535/44425 | 41974/50321 | -32527/-68299 | 2175 | 0.17 | 1.00 | -3521 | -832 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 2 latch arm abs 20 | -349 | 1439 | 905 | -3 | -85 | 736 | -190 | -99 | 25180/44425 | 41486/50321 | -34792/-68299 | 2189 | 0.32 | 1.00 | -3451 | -767 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 1 latch arm abs 20 | -395 | 1583 | 1049 | 64 | -77 | 644 | -222 | -179 | 25636/44425 | 41853/50321 | -36446/-68299 | 2204 | 0.29 | 1.00 | -3289 | -813 | ok | CANDIDATE-DD |
## U7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -181421.67, "dd_never": 42226.48, "dd_wf": 48388.02, "share_pos": 0.34, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -4186 / 858 / 264 / 2822 / 1627 / 690 / 1386 / 909; maxDD L6M 21561 PRE 42226 w20 L6M 120. Live S1b-COMB: mean -3377 / 1351 / 1238 / 2949 / 1808 / 1620 / 1325 / 669; maxDD L6M 16419 PRE 39155 w20 L6M 8146.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 3 pers 20 latch arm abs 45 | -1932 | 3908 | 1628 | 3291 | 2250 | 2825 | 1651 | 1830 | 9886/21561 | 43161/42226 | 3532/120 | 571 | 0.03 | 1.00 | 0 | 469 | ok | CANDIDATE-DD |
| dlt_med_w30 | thr -16.96 pers 20 cur arm abs 30 | -2426 | 2488 | 1370 | 3492 | 2748 | 4361 | 800 | 1252 | 10440/21561 | 38079/42226 | 8302/120 | 673 | 0.02 | 1.00 | 0 | 388 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 8 latch arm pct 0.75 | -1801 | 3776 | 1474 | 3864 | 2154 | 1396 | 1615 | 1869 | 10819/21561 | 42523/42226 | 9790/120 | 320 | 0.20 | 1.00 | 0 | 306 | ok | CANDIDATE-DD |
| dlt_med_w30 | thr -52.16 pers 2 latch arm pct 0.3 | -2493 | 1534 | 2346 | 4235 | 2361 | 2380 | 1277 | 1231 | 12618/21561 | 41403/42226 | 24798/120 | 462 | 0.05 | 1.00 | 0 | -80 | ok | CANDIDATE-DD |
| dlt_med_w30 | thr -52.16 pers 2 latch arm abs 20 | -3752 | 140 | 1647 | 3854 | 2224 | 2457 | 1437 | 1221 | 15371/21561 | 37018/42226 | 15274/120 | 449 | 0.03 | 1.00 | 0 | 116 | ok | CANDIDATE-DD |

U7 loss: the rule that lowers L6M drawdown most is retr_w10 (f >= 3 for 20 s, armed latch 45); L6M maxDD 9886 vs 21561 never-cut (live line 16419), L6M mean 3291 vs 2822 never-cut, PRE maxDD 43161 vs 42226; placebo p 0.03, family p 1.00, live week delta 0; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 15 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 3 pers 20 latch arm abs 45 | -1932 | 3908 | 1628 | 3291 | 2250 | 2825 | 1651 | 1830 | 9886/21561 | 43161/42226 | 3532/120 | 571 | 0.03 | 1.00 | 0 | 469 | ok | CANDIDATE-DD |
| dlt_med_w30 | thr -16.96 pers 20 cur arm abs 30 | -2426 | 2488 | 1370 | 3492 | 2748 | 4361 | 800 | 1252 | 10440/21561 | 38079/42226 | 8302/120 | 673 | 0.02 | 1.00 | 0 | 388 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 8 latch arm pct 0.75 | -1801 | 3776 | 1474 | 3864 | 2154 | 1396 | 1615 | 1869 | 10819/21561 | 42523/42226 | 9790/120 | 320 | 0.20 | 1.00 | 0 | 306 | ok | CANDIDATE-DD |
## A7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -33653.0, "dd_never": 14180.76, "dd_wf": 10454.78, "share_pos": 0.37, "npick": 29, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 389 / -97 / -190 / 601 / 538 / 140 / 859 / 179; maxDD L6M 12461 PRE 6089 w20 L6M -17069. Live S1b-COMB: mean -1287 / 217 / 169 / 821 / 731 / 328 / 808 / 212; maxDD L6M 8518 PRE 7325 w20 L6M -11915.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 14 pers 8 cur arm pct 0.6 | 272 | 996 | 471 | 1218 | 856 | 404 | 774 | 345 | 5407/12461 | 5469/6089 | -2246/-17069 | 573 | 0.02 | 1.00 | -1854 | -118 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 3 pers 5 cur arm pct 0.6 | -856 | 621 | 127 | 1155 | 840 | 121 | 791 | 316 | 6795/12461 | 6324/6089 | -11220/-17069 | 401 | 0.03 | 1.00 | -1775 | -1245 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| dlt_med_w30 | thr -52.16 pers 3 cur arm abs 10 | -314 | 95 | -146 | 879 | 683 | 238 | 848 | 446 | 6971/12461 | 5643/6089 | -10472/-17069 | 349 | 0.03 | 1.00 | -1936 | -703 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w10 | thr 9 pers 20 cur arm pct 0.45 | 240 | 443 | -7 | 1011 | 706 | 807 | 967 | 363 | 7152/12461 | 5995/6089 | -10416/-17069 | 272 | 0.03 | 1.00 | 1098 | -149 | ok | CANDIDATE-DD |
| retr_w10 | thr 9 pers 5 cur arm abs 35 | -427 | 890 | 328 | 963 | 635 | 592 | 637 | 371 | 7520/12461 | 6335/6089 | -12345/-17069 | 660 | 0.03 | 1.00 | -1675 | -816 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |

A7 loss: the rule that lowers L6M drawdown most is retr_w10 (f >= 14 for 8 s, armed cur 0.6); L6M maxDD 5407 vs 12461 never-cut (live line 8518), L6M mean 1218 vs 601 never-cut, PRE maxDD 5469 vs 6089; placebo p 0.02, family p 1.00, live week delta -1854; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 8 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 14 pers 8 cur arm pct 0.6 | 272 | 996 | 471 | 1218 | 856 | 404 | 774 | 345 | 5407/12461 | 5469/6089 | -2246/-17069 | 573 | 0.02 | 1.00 | -1854 | -118 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 3 pers 5 cur arm pct 0.6 | -856 | 621 | 127 | 1155 | 840 | 121 | 791 | 316 | 6795/12461 | 6324/6089 | -11220/-17069 | 401 | 0.03 | 1.00 | -1775 | -1245 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| dlt_med_w30 | thr -52.16 pers 3 cur arm abs 10 | -314 | 95 | -146 | 879 | 683 | 238 | 848 | 446 | 6971/12461 | 5643/6089 | -10472/-17069 | 349 | 0.03 | 1.00 | -1936 | -703 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## H7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -31739.5, "dd_never": 57397.21, "dd_wf": 53389.82, "share_pos": 0.49, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -88 / 270 / -1307 / 1121 / -331 / -2452 / 1453 / 103; maxDD L6M 15477 PRE 20667 w20 L6M -32750. Live S1b-COMB: mean 3186 / 2043 / 996 / 2609 / 656 / -1655 / 1468 / 220; maxDD L6M 8818 PRE 19256 w20 L6M 11007.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 6 pers 5 latch arm pct 0.15 | 320 | 575 | 962 | 1487 | 44 | -266 | 1531 | 72 | 5190/15477 | 15940/20667 | -922/-32750 | 354 | 0.03 | 1.00 | 374 | 305 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 5 latch arm abs 10 | 516 | 673 | 1042 | 1454 | 23 | -266 | 1585 | 94 | 5375/15477 | 14744/20667 | -2569/-32750 | 347 | 0.02 | 1.00 | 374 | 403 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 1 latch arm pct 0.15 | 461 | 1679 | 969 | 1427 | 87 | -271 | 1497 | -76 | 5466/15477 | 18613/20667 | -928/-32750 | 395 | 0.06 | 1.00 | 394 | 354 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 1 latch arm abs 10 | 620 | 1758 | 1089 | 1378 | 58 | -275 | 1538 | -55 | 5486/15477 | 17364/20667 | -1823/-32750 | 387 | 0.02 | 1.00 | 394 | 434 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 20 cur arm pct 0.15 | 754 | 2946 | 1513 | 2061 | 407 | -326 | 1435 | 437 | 5505/15477 | 16303/20667 | 579/-32750 | 389 | 0.02 | 1.00 | 244 | 458 | ok | CANDIDATE-DD |

H7 loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 6 for 5 s, armed latch 0.15); L6M maxDD 5190 vs 15477 never-cut (live line 8818), L6M mean 1487 vs 833 never-cut, PRE maxDD 15940 vs 20667; placebo p 0.03, family p 1.00, live week delta 374; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 74 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 6 pers 5 latch arm pct 0.15 | 320 | 575 | 962 | 1487 | 44 | -266 | 1531 | 72 | 5190/15477 | 15940/20667 | -922/-32750 | 354 | 0.03 | 1.00 | 374 | 305 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 5 latch arm abs 10 | 516 | 673 | 1042 | 1454 | 23 | -266 | 1585 | 94 | 5375/15477 | 14744/20667 | -2569/-32750 | 347 | 0.02 | 1.00 | 374 | 403 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 1 latch arm pct 0.15 | 461 | 1679 | 969 | 1427 | 87 | -271 | 1497 | -76 | 5466/15477 | 18613/20667 | -928/-32750 | 395 | 0.06 | 1.00 | 394 | 354 | ok | CANDIDATE-DD |
## O7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -39742.5, "dd_never": 7468.56, "dd_wf": 10378.2, "share_pos": 0.43, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -685 / 149 / -65 / 176 / 653 / -181 / 644 / -136; maxDD L6M 7469 PRE 5102 w20 L6M -9532. Live S1b-COMB: mean -988 / 75 / 115 / 322 / 669 / -127 / 653 / -166; maxDD L6M 6656 PRE 4532 w20 L6M -8247.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 37 pers 5 latch arm pct 0.15 | 116 | 240 | 377 | 302 | 496 | 95 | 311 | -71 | 4635/7469 | 5183/5102 | -3886/-9532 | 340 | 0.09 | 1.00 | 986 | 128 | ok | CANDIDATE-DD |
| retr_w10 | thr 29 pers 8 cur arm pct 0.15 | -255 | 139 | 231 | 222 | 571 | 73 | 378 | -182 | 4985/7469 | 4917/5102 | -3971/-9532 | 295 | 0.17 | 1.00 | 656 | -115 | ok | CANDIDATE-DD |
| dlt_med_w30 | thr -52.16 pers 2 latch arm pct 0.45 | -809 | 47 | 426 | 289 | 501 | -636 | 308 | -34 | 5048/7469 | 4204/5102 | -7323/-9532 | 352 | 0.11 | 1.00 | 443 | -125 | ok | CANDIDATE-DD |
| dlt_med_w30 | thr -28.69 pers 8 latch arm pct 0.45 | -783 | 105 | 465 | 227 | 489 | -532 | 268 | -173 | 5099/7469 | 4983/5102 | -6024/-9532 | 369 | 0.15 | 1.00 | 516 | -98 | ok | CANDIDATE-DD |
| retr_w10 | thr 22 pers 12 latch arm abs 20 | -503 | 436 | 553 | 540 | 652 | -422 | 591 | 53 | 6710/7469 | 4986/5102 | -6283/-9532 | 205 | 0.32 | 1.00 | 0 | 181 | ok | CANDIDATE-DD |

O7 loss: the rule that lowers L6M drawdown most is retr_w10 (f >= 37 for 5 s, armed latch 0.15); L6M maxDD 4635 vs 7469 never-cut (live line 6656), L6M mean 302 vs 173 never-cut, PRE maxDD 5183 vs 5102; placebo p 0.09, family p 1.00, live week delta 986; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 7 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 22 pers 12 latch arm abs 20 | -503 | 436 | 553 | 540 | 652 | -422 | 591 | 53 | 6710/7469 | 4986/5102 | -6283/-9532 | 205 | 0.32 | 1.00 | 0 | 181 | ok | CANDIDATE-DD |
| retr_w10 | thr 14 pers 20 latch arm abs 25 | -595 | -174 | 83 | 325 | 702 | -112 | 663 | -48 | 6772/7469 | 4025/5102 | -10511/-9532 | 89 | 0.57 | 1.00 | 0 | 83 | ok | CANDIDATE-DD |
| retr_w10 | thr 9 pers 20 latch arm abs 25 | -594 | -80 | 158 | 301 | 735 | -51 | 631 | -70 | 6779/7469 | 4192/5102 | -9331/-9532 | 162 | 0.52 | 1.00 | 0 | 90 | ok | CANDIDATE-DD |
## X3 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {}
Reference rows: never-cut L1M..X' mean = -166 / 0 / 0 / 0 / 0 / 0 / 0 / 0; maxDD L6M 664 PRE 0 w20 L6M -664. Live S1b-COMB: mean -448 / 0 / 0 / 0 / 0 / 0 / 0 / 0; maxDD L6M 1794 PRE 0 w20 L6M -1794.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 0 cells

X3 loss: no ledgered cell passes the validity filter.

## X4 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {}
Reference rows: never-cut L1M..X' mean = 1195 / 598 / 398 / 191 / 94 / 0 / 0 / 0; maxDD L6M 0 PRE 0 w20 L6M 0. Live S1b-COMB: mean 795 / 398 / 265 / 127 / 62 / 0 / 0 / 0; maxDD L6M 0 PRE 0 w20 L6M 0.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 0 cells

X4 loss: no ledgered cell passes the validity filter.

## X5 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {}
Reference rows: never-cut L1M..X' mean = 13 / 0 / 0 / 0 / 0 / 0 / 0 / 0; maxDD L6M 0 PRE 0 w20 L6M 0. Live S1b-COMB: mean 95 / 0 / 0 / 0 / 0 / 0 / 0 / 0; maxDD L6M 0 PRE 0 w20 L6M 0.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 0 cells

X5 loss: no ledgered cell passes the validity filter.

# Session-level tables (book x entry session, best by the drawdown-first key, validity as above, top 2)
### K7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 3 pers 20 latch arm abs 15 | 1481 | 3772 | 3346 | 2739 | 1468 | 143 | 976 | 163 | 4306/22104 | 12257/13344 | 16637/-6120 | 1175 | 0.03 | 1.00 |  | -3108 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 8 latch arm abs 15 | 1705 | 4471 | 3950 | 2968 | 1539 | 51 | 959 | 268 | 4613/22104 | 13710/13344 | 12772/-6120 | 1043 | 0.02 | 1.00 |  | -2884 | ok | CANDIDATE-DD |
### K7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep4_w10 | thr 4 pers 8 cur arm pct 0.3 | 18 | 2311 | 1475 | 412 | 323 | -174 | 208 | 250 | 7920/14952 | 18504/18704 | -15558/-27616 | 754 | 0.31 | 1.00 |  | 576 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 8 cur arm pct 0.3 | -1483 | 1640 | 502 | 552 | 234 | -38 | 180 | 40 | 8889/14952 | 15021/18704 | -20750/-27616 | 693 | 0.11 | 1.00 |  | -506 | ok | CANDIDATE-DD |
### K7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dlt_med_w30 | thr -16.96 pers 20 cur arm pct 0.15 | 398 | -22 | 192 | 34 | -275 | -746 | 148 | 140 | 5268/23185 | 6222/6211 | -12971/-34239 | 1168 | 0.14 | 1.00 |  | -1339 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 5 cur arm abs 25 | 2046 | 558 | 330 | 177 | -272 | -86 | 531 | 369 | 8104/23185 | 5792/6211 | -18730/-34239 | 531 | 0.71 | 1.00 |  | 234 | ok | CANDIDATE-DD |
### K7 nypm (session 4)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 2 cur arm pct 0.3 | 1392 | 251 | 509 | 742 | 251 | -748 | 351 | 148 | 3428/6369 | 29321/33629 | -4989/-7470 | 576 | 0.22 | 1.00 |  | -64 | FAIL | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 8 cur arm pct 0.3 | 1397 | 451 | 55 | 737 | 251 | -775 | 343 | 156 | 3976/6369 | 27123/33629 | -3974/-7470 | 542 | 0.29 | 1.00 |  | 43 | ok | CANDIDATE-DD |
### P7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 37 pers 1 cur arm pct 0.15 | 7281 | 12612 | 9581 | 11804 | 7014 | 3531 | 4186 | -1311 | 35019/116210 | 43328/66531 | 32192/8506 | 1085 | 0.02 | 1.00 |  | -26035 | FAIL | CANDIDATE-DD |
| retr_w10 | thr 37 pers 2 cur arm pct 0.15 | 5293 | 13616 | 10040 | 13407 | 7792 | 1362 | 5418 | -841 | 35813/116210 | 35147/66531 | 45801/8506 | 966 | 0.02 | 1.00 |  | -28023 | FAIL | CANDIDATE-DD |
### P7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 14 pers 20 latch arm abs 20 | 3483 | 13280 | 8717 | 8970 | 3701 | -1391 | -1675 | -551 | 26766/51796 | 153007/150275 | 66288/-20541 | 287 | 0.02 | 1.00 |  | -4136 | FAIL | CANDIDATE-DD |
| retr_w10 | thr 14 pers 20 latch arm pct 0.3 | 3483 | 12222 | 8012 | 8623 | 3501 | -1539 | -1649 | -575 | 26766/51796 | 151095/150275 | 62996/-20541 | 297 | 0.02 | 1.00 |  | -5194 | FAIL | CANDIDATE-DD |
### P7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep4_w10 | thr 4 pers 12 latch arm pct 0.15 | 2898 | 4029 | 1857 | 1799 | 383 | 2856 | 782 | 674 | 13560/86629 | 40328/77956 | -27231/-147642 | 645 | 0.02 | 1.00 |  | -772 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 1 latch arm pct 0.15 | 1028 | 4914 | 3930 | 2394 | 786 | 2963 | 1043 | 426 | 15071/86629 | 43476/77956 | -21548/-147642 | 560 | 0.02 | 1.00 |  | 113 | ok | CANDIDATE-DD |
### M7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 3 latch arm abs 20 | -1774 | 12 | -274 | -443 | -58 | 650 | -547 | 54 | 14564/38178 | 49163/69890 | -33858/-64988 | 1212 | 0.02 | 1.00 |  | -1078 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 2 latch arm abs 20 | -1713 | 21 | -282 | -504 | -66 | 650 | -573 | -22 | 16781/38178 | 51257/69890 | -35518/-64988 | 1219 | 0.02 | 1.00 |  | -1018 | ok | CANDIDATE-DD |
### M7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 6 pers 5 cur arm abs 25 | 1986 | 1787 | 1425 | 749 | 117 | 162 | 591 | 38 | 4575/11667 | 7431/7583 | -3655/-17931 | 547 | 0.02 | 1.00 |  | 399 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 3 pers 5 cur arm pct 0.6 | 1743 | 1555 | 1544 | 793 | 31 | 532 | 646 | -360 | 6958/11667 | 6027/7583 | -5261/-17931 | 763 | 0.02 | 1.00 |  | 107 | ok | CANDIDATE-DD |
### U7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 22 pers 12 latch arm abs 20 | 1366 | 4841 | 3440 | 4429 | 2156 | 638 | 1130 | 1649 | 5578/9906 | 32027/31026 | 38162/9960 | 132 | 0.42 | 1.00 |  | 152 | ok | CANDIDATE-DD |
| retr_w10 | thr 22 pers 12 latch arm pct 0.15 | 71 | 930 | 2777 | 3844 | 1765 | 331 | 997 | 1594 | 6917/9906 | 32027/31026 | 29034/9960 | 159 | 0.98 | 1.00 |  | -1142 | FAIL | CANDIDATE-DD |
### U7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 9 pers 20 cur arm pct 0.45 | -4799 | -494 | -2104 | 408 | 480 | 1802 | 538 | -131 | 25579/32749 | 33395/33984 | -51698/-53967 | 169 | 0.95 | 1.00 |  | -17 | ok | CANDIDATE-DD |
| dlt_med_w30 | thr -52.16 pers 2 cur arm pct 0.15 | -4834 | -1759 | -1869 | 270 | 616 | 1130 | 573 | -453 | 25697/32749 | 33563/33984 | -51194/-53967 | 239 | 0.91 | 1.00 |  | 312 | ok | CANDIDATE-DD |
### A7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 14 pers 8 cur arm pct 0.6 | 272 | 996 | 471 | 1218 | 856 | 404 | 774 | 345 | 5407/12461 | 5469/6089 | -2246/-17069 | 573 | 0.02 | 1.00 |  | -118 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 3 pers 5 cur arm pct 0.6 | -856 | 621 | 127 | 1155 | 840 | 121 | 791 | 316 | 6795/12461 | 6324/6089 | -11220/-17069 | 401 | 0.03 | 1.00 |  | -1245 | ok | CANDIDATE-DD |
### H7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 6 pers 1 latch arm pct 0.15 | 81 | 1354 | 764 | 1320 | 74 | -296 | 1825 | -167 | 3959/14606 | 15571/17912 | -779/-39488 | 173 | 0.02 | 1.00 |  | 753 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 1 latch arm abs 10 | 258 | 1443 | 755 | 1237 | 33 | -296 | 1860 | -167 | 4144/14606 | 15571/17912 | -3276/-39488 | 169 | 0.02 | 1.00 |  | 761 | ok | CANDIDATE-DD |
### H7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 14 pers 12 cur arm abs 20 | 436 | -61 | -4 | 355 | 147 | 182 | -125 | 126 | 2803/3762 | 16886/23608 | -3526/-5403 | 233 | 0.25 | 1.00 |  | -715 | ok | CANDIDATE-DD |
| retr_w10 | thr 14 pers 8 cur arm pct 0.6 | 468 | 56 | -52 | 327 | 222 | -8 | -115 | 121 | 3328/3762 | 21351/23608 | -4921/-5403 | 228 | 0.71 | 1.00 |  | -682 | ok | CANDIDATE-DD |
### O7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 37 pers 5 latch arm pct 0.15 | 116 | 240 | 377 | 302 | 496 | 95 | 311 | -71 | 4635/7469 | 5183/5102 | -3886/-9532 | 340 | 0.09 | 1.00 |  | 128 | ok | CANDIDATE-DD |
| retr_w10 | thr 29 pers 8 cur arm pct 0.15 | -255 | 139 | 231 | 222 | 571 | 73 | 378 | -182 | 4985/7469 | 4917/5102 | -3971/-9532 | 295 | 0.17 | 1.00 |  | -115 | ok | CANDIDATE-DD |
# Lot-scaled ARM variants (V1 clip(ARM*sqrt(4/lots),15,50), V2 clip(ARM*sqrt(lots/4),15,50), USD clip($/(lots*20),10,55)): 14,742 further cells screened on the 29 features of the best rules; best valid cell per book vs the best lattice (fixed/pct) cell (L6M maxDD, mean); top 3 per book-level scope ledgered
lot-arm table failed: [Errno 2] No such file or directory: '/mnt/l2/l2vast/_th_exh/bc/valid_ranked_lot
# Finalists (12) and Stage 2
Groups: A_recent = best recents-consistent supported rule per book (live-week delta >= 0 preferred), B_ddbest = pure drawdown-best for contrast, C_uniform = one rule on all books. Stage 2 sets: /mnt/l2/l2vast/_th_exh/stage2/sets/bc_a_recent.json, bc_b_ddbest.json, bc_c_uniform.json (kernel bc_s2.kern_bc, panel functions bc_s2.pan_<feature> = feat_core.prim on a state slice; verified equal to the EX-FEAT panel to 0.0 on 8+5 features incl. multi-day concatenated Z). Stage 2 progress: see ledger stage2_* parts (agent S2) and /mnt/l2/l2vast/_th_exh/bc/s2_*.log.
| group | book | rule | thr | pers | mode | arm | L6M maxDD w/wo | L6M mean | held-out live-week delta | nfire |
|---|---|---|---|---|---|---|---|---|---|---|
| A_recent | K7 | sweep8_w30 | 4 | 20 | cur | pct 0.3 | 8634/26983 | 5259 | -5284 | 2306 |
| A_recent | P7 | spread_t | 6 | 20 | latch | abs 15 | 73778/126710 | 13535 | -54560 | 862 |
| A_recent | M7 | ice_ag_w10 | 2 | 1 | cur | pct 0.6 | 28482/43318 | -147 | 867 | 2188 |
| A_recent | U7 | ice_ag_w10 | 4 | 5 | cur | pct 0.15 | 7277/21436 | 3591 | 2829 | 779 |
| A_recent | A7 | dlt_v60_w120 | -0.5588 | 3 | cur | abs 35 | 5134/12456 | 1080 | 101 | 535 |
| A_recent | H7 | sweep8_w10 | 4 | 3 | latch | abs 10 | 5354/16682 | 2005 | 394 | 338 |
| A_recent | O7 | sweep8_w10 | 4 | 5 | cur | pct 0.15 | 3924/7489 | 269 | 826 | 220 |
| C_uniform | ALL | sweep8_w10 | 3 | 8 | cur | pct 0.3 | 88465/117593 | 26484 | -38535 | 5274 |
| B_ddbest | K7 | sweep8_w30 | 4 | 12 | latch | abs 10 | 6384/26983 | 3186 | -15890 | 3769 |
| B_ddbest | P7 | sweep8_w30 | 4 | 8 | latch | USD 1600 | 23789/126710 | 15872 | -75321 | 2168 |
| B_ddbest | M7 | micro_sg | -1.333 | 3 | latch | abs 15 | 19143/43318 | 922 | -253 | 761 |
| B_ddbest | U7 | ice_ag_w30 | 6 | 5 | cur | pct 0.15 | 6611/21436 | 3598 | 2829 | 794 |