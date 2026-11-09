# EXH_BC - loss families B (book-state) and C (flow), EX-LBC; generated 2026-11-09 09:46Z
Entry match label: PRE-PROOF. The live-week column is the HELD-OUT week: the 186 actual live trades with the EX-FEAT live panel (feat_live), delta vs the actual live exit; it is computed for book-level rows only. Features: EX-FEAT panels, all 44 months 202304-202611 (full history). Rules: each alone as a market cut (decision k, execute k+1 at mid -+ 0.80), armed on adverse excursion ARM (latch = armed once; cur = current), persistence 1-20 s, threshold lattice per prereg (DECISIONS 2026-11-09T02:57Z).
Screened: 63 features x 432 rule-thresholds x 7 persistence x 16 arms x 2 arm modes = 96,768 cells, all 77 scopes each (bc/screen_*.parquet). Ledgered with score_cell (null_ver 2): 928 cells = the top per scope by the drawdown-first key. Family p covers ledgered cells only, so it is optimistic against 96,768 screened.
Causality: noise-after-k0 test on the lattice kernel (6 features, k0 = 300 and 900 s, mid and feature replaced after k0): 2,729,879 fires at <= k0 checked, 0 changed. Pass.
Label rules: EXH_API section 3 (ENTER / CANDIDATE-DD / LEAD / no). A cell is picked per book (sessions pooled) by (L6M maxDD, worst-20, Ulcer, -mean), valid = nfire>=20, L6M mean >= never-cut, PRE maxDD <= never*1.05.

## ALL loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -598926.24, "dd_never": 153255.2, "dd_wf": 154340.56, "share_pos": 0.4, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 35468 / 31777 / 14768 / 20752 / 13342 / -3552 / 16838 / -6; maxDD L6M 121381 PRE 152455 w20 L6M 77580. Live S1b-COMB: mean 11588 / 31519 / 16583 / 23991 / 15430 / 4801 / 15015 / -529; maxDD L6M 82873 PRE 144002 w20 L6M 190560.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 5 latch arm pct 0.3 | 5232 | 29550 | 19284 | 21427 | 8082 | -4792 | 6905 | 1564 | 36812/121381 | 107422/152455 | 127045/77580 | 10337 | 0.02 | 1.00 | -95004 | -30237 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 8 latch arm pct 0.3 | 5823 | 30900 | 20879 | 22557 | 8667 | -3968 | 7496 | 1641 | 42380/121381 | 114256/152455 | 175762/77580 | 10006 | 0.02 | 1.00 | -91150 | -29645 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w10 | thr 9 pers 20 latch arm abs 25 | 21262 | 21763 | 15626 | 22878 | 12062 | 1359 | 9724 | 4040 | 43600/121381 | 109576/152455 | 208464/77580 | 7412 | 0.02 | 1.00 | -57539 | -14206 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| dlt_med_w30 | thr -28.69 pers 3 latch arm abs 20 | 23137 | 24408 | 15593 | 20854 | 9374 | -4616 | 2596 | 3509 | 46558/121381 | 144646/152455 | 131274/77580 | 12368 | 0.02 | 1.00 | -38873 | -12331 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep4_w10 | thr 4 pers 8 cur arm pct 0.15 | -506 | 17313 | 10193 | 21393 | 9029 | 4898 | 6358 | 3617 | 47240/121381 | 154974/152455 | 103287/77580 | 10687 | 0.20 | 1.00 | -117995 | -35974 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |

ALL loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 4 for 5 s, armed latch 0.3); L6M maxDD 36812 vs 121381 never-cut (live line 82873), L6M mean 21427 vs 20752 never-cut, PRE maxDD 107422 vs 152455; placebo p 0.02, family p 1.00, live week delta -95004; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 100 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_slow | thr 0.7891 pers 2 latch arm abs 40 | 40047 | 37921 | 20146 | 29479 | 16642 | 17009 | 14155 | 2210 | 66689/121381 | 86161/152455 | 203922/77580 | 8208 | 0.02 | 1.00 | -16577 | -1046 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| tot_rel_base | thr 0.8129 pers 3 latch arm abs 40 | 46047 | 42445 | 22584 | 29086 | 16487 | 18108 | 14186 | 1945 | 68757/121381 | 87532/152455 | 195030/77580 | 7949 | 0.11 | 1.00 | -12415 | 3023 | ok | CANDIDATE-DD |
| retr_w10 | thr 14 pers 20 latch arm abs 25 | 20638 | 30363 | 20134 | 27094 | 15456 | 4062 | 13547 | 900 | 69144/121381 | 148955/152455 | 233015/77580 | 3158 | 0.02 | 1.00 | -28027 | -14830 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## K7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -183352.5, "dd_never": 42831.12, "dd_wf": 41369.62, "share_pos": 0.26, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 4952 / 5000 / 1432 / 3382 / 2075 / -1276 / 2748 / 555; maxDD L6M 20902 PRE 26707 w20 L6M 1791. Live S1b-COMB: mean 7873 / 5607 / 1636 / 2666 / 1568 / 902 / 2580 / 392; maxDD L6M 41849 PRE 23073 w20 L6M -20339.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 12 latch arm abs 10 | 1104 | 6026 | 5102 | 3657 | 1688 | -240 | 1481 | -19 | 5514/20902 | 27025/26707 | 25164/1791 | 3787 | 0.11 | 1.00 | -15890 | -3848 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| adv_best_move | thr 3 pers 5 latch arm pct 0.15 | 5861 | 7785 | 5020 | 4368 | 2154 | -128 | 1611 | 456 | 8636/20902 | 23900/26707 | 28728/1791 | 3051 | 0.05 | 1.00 | 126 | 909 | ok | CANDIDATE-DD |
| sweep4_w10 | thr 4 pers 12 latch arm abs 10 | 684 | 5120 | 3083 | 3606 | 1790 | 1366 | 1446 | -32 | 9097/20902 | 23670/26707 | 13419/1791 | 3060 | 0.57 | 1.00 | -11824 | -4268 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| tot_rel_base | thr 1.01 pers 20 cur arm abs 40 | 5871 | 6853 | 3521 | 4939 | 2389 | 1329 | 2545 | -12 | 9396/20902 | 25381/26707 | 39604/1791 | 2191 | 0.03 | 1.00 | 879 | 839 | ok | CANDIDATE-DD |
| imb_ag10 | thr 0.4043 pers 2 cur arm pct 0.45 | 4650 | 6269 | 2954 | 4065 | 2363 | 1375 | 2695 | 399 | 9560/20902 | 21646/26707 | 18437/1791 | 1148 | 0.02 | 1.00 | 0 | -302 | ok | CANDIDATE-DD |

K7 loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 4 for 12 s, armed latch 10); L6M maxDD 5514 vs 20902 never-cut (live line 41849), L6M mean 3657 vs 3245 never-cut, PRE maxDD 27025 vs 26707; placebo p 0.11, family p 1.00, live week delta -15890; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 63 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_base | thr 1.01 pers 20 cur arm abs 40 | 5871 | 6853 | 3521 | 4939 | 2389 | 1329 | 2545 | -12 | 9396/20902 | 25381/26707 | 39604/1791 | 2191 | 0.03 | 1.00 | 879 | 839 | ok | CANDIDATE-DD |
| imb_ag10 | thr 0.4043 pers 2 cur arm pct 0.45 | 4650 | 6269 | 2954 | 4065 | 2363 | 1375 | 2695 | 399 | 9560/20902 | 21646/26707 | 18437/1791 | 1148 | 0.02 | 1.00 | 0 | -302 | ok | CANDIDATE-DD |
| r_ab8 | thr 2.133 pers 3 cur arm pct 0.6 | 6383 | 8630 | 4893 | 4740 | 3190 | 1588 | 2676 | 443 | 10152/20902 | 18772/26707 | 28557/1791 | 1231 | 0.29 | 1.00 | 497 | 784 | ok | CANDIDATE-DD |
## P7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -496817.83, "dd_never": 144369.91, "dd_wf": 112272.16, "share_pos": 0.37, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 33625 / 22555 / 13873 / 11894 / 8318 / 4310 / 6595 / -741; maxDD L6M 133887 PRE 109442 w20 L6M -29902. Live S1b-COMB: mean 5700 / 18966 / 12054 / 14708 / 10485 / 11110 / 4903 / -839; maxDD L6M 96490 PRE 106914 w20 L6M 53844.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 6 pers 1 latch arm abs 10 | 25653 | 31594 | 23256 | 22753 | 9606 | -3335 | 4064 | -607 | 36977/133887 | 78726/109442 | 264422/-29902 | 1891 | 0.02 | 1.00 | -71288 | -7972 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep4_w10 | thr 4 pers 8 cur arm abs 15 | 7362 | 15882 | 11850 | 18700 | 9890 | -6458 | 3858 | -725 | 37113/133887 | 89280/109442 | 161302/-29902 | 2301 | 0.02 | 1.00 | -83434 | -26264 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w10 | thr 2 pers 2 cur arm abs 20 | 2044 | 10520 | 7610 | 15327 | 7247 | 2077 | 1418 | 2120 | 40468/133887 | 64839/109442 | 119037/-29902 | 2769 | 0.02 | 1.00 | -65651 | -31581 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w10 | thr 22 pers 5 cur arm pct 0.3 | 2450 | 12900 | 9942 | 13651 | 7076 | 2474 | 1344 | 958 | 40579/133887 | 76049/109442 | 94591/-29902 | 2794 | 0.02 | 1.00 | -75937 | -31175 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| retr_w30 | thr 26 pers 12 cur arm pct 0.3 | -126 | 8083 | 5768 | 13725 | 7101 | 8339 | 1150 | 245 | 41105/133887 | 74208/109442 | 75880/-29902 | 2937 | 0.02 | 1.00 | -76572 | -33751 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |

P7 loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 6 for 1 s, armed latch 10); L6M maxDD 36977 vs 133887 never-cut (live line 96490), L6M mean 22753 vs 11894 never-cut, PRE maxDD 78726 vs 109442; placebo p 0.02, family p 1.00, live week delta -71288; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 91 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| retr_w10 | thr 14 pers 20 latch arm abs 10 | 16754 | 21012 | 18305 | 21837 | 11645 | 2372 | 6097 | -2038 | 56327/133887 | 99925/109442 | 203969/-29902 | 1022 | 0.02 | 1.00 | -24551 | -16871 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| dlt_med_w60 | thr -43.42 pers 20 cur arm abs 35 | 30342 | 27335 | 27945 | 21762 | 12635 | 6784 | 7572 | -1000 | 59918/133887 | 86090/109442 | 94113/-29902 | 1252 | 0.02 | 1.00 | 0 | -3283 | ok | CANDIDATE-DD |
| dlt_med_w10 | thr -4.47 pers 20 cur arm abs 30 | 39691 | 53126 | 34291 | 23091 | 11012 | -3927 | 7903 | -399 | 60170/133887 | 63167/109442 | 107131/-29902 | 1426 | 0.02 | 1.00 | -158 | 2068 | ok | CANDIDATE-DD |
## M7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -48035.0, "dd_never": 68802.24, "dd_wf": 55411.76, "share_pos": 0.4, "npick": 34, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 419 / 1473 / -648 / -540 / -338 / -23 / -78 / 140; maxDD L6M 44425 PRE 50321 w20 L6M -68299. Live S1b-COMB: mean 40 / 1747 / -788 / -1152 / -1092 / -932 / 439 / 177; maxDD L6M 46547 PRE 25812 w20 L6M -64633.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dtot8_rel_w15 | thr -0.004938 pers 12 latch arm abs 15 | -1623 | -354 | -464 | 308 | -627 | -958 | -476 | -288 | 13767/44425 | 48783/50321 | -28007/-68299 | 2323 | 0.03 | 1.00 | -1886 | -2042 | ok | CANDIDATE-DD |
| cps_rel_w10 | thr 3.139 pers 8 latch arm pct 0.3 | 69 | 1464 | 842 | 14 | -428 | -951 | -283 | -619 | 14306/44425 | 37643/50321 | -34516/-68299 | 2397 | 0.06 | 1.00 | -1135 | -3309 | FAIL | CANDIDATE-DD |
| dtot8_rel_w15 | thr -0.004938 pers 12 cur arm pct 0.15 | -702 | 2226 | 1005 | 416 | -332 | -466 | -282 | -285 | 14612/44425 | 35366/50321 | -24573/-68299 | 2092 | 0.15 | 1.00 | 1968 | -2548 | FAIL | CANDIDATE-DD |
| cps_rel_w10 | thr 3.139 pers 3 latch arm pct 0.3 | 369 | 1768 | 818 | 98 | -441 | 427 | -485 | -521 | 14882/44425 | 50928/50321 | -28055/-68299 | 2539 | 0.32 | 1.00 | -3316 | -3006 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| cps_rel_w10 | thr 2.203 pers 5 cur arm abs 10 | -695 | 1485 | 275 | 315 | -525 | -365 | -442 | -567 | 15453/44425 | 41772/50321 | -27764/-68299 | 2787 | 0.26 | 1.00 | -4293 | -3288 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |

M7 loss: the rule that lowers L6M drawdown most is dtot8_rel_w15 (f ><= -0.004938 for 12 s, armed latch 15); L6M maxDD 13767 vs 44425 never-cut (live line 46547), L6M mean 308 vs -540 never-cut, PRE maxDD 48783 vs 50321; placebo p 0.03, family p 1.00, live week delta -1886; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 287 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dtot8_rel_w15 | thr -0.004938 pers 12 latch arm abs 15 | -1623 | -354 | -464 | 308 | -627 | -958 | -476 | -288 | 13767/44425 | 48783/50321 | -28007/-68299 | 2323 | 0.03 | 1.00 | -1886 | -2042 | ok | CANDIDATE-DD |
| cdiv_w60 | thr -1 pers 2 cur arm abs 10 | -1535 | 348 | -116 | -258 | -677 | 79 | -426 | -454 | 15496/44425 | 45570/50321 | -33008/-68299 | 2764 | 0.11 | 1.00 | -3414 | -1954 | ok | CANDIDATE-DD |
| dlt_v60_w30 | thr -0.08929 pers 20 latch arm pct 0.3 | -769 | 460 | 496 | 280 | -751 | -702 | -466 | -130 | 15798/44425 | 52692/50321 | -27496/-68299 | 2666 | 0.20 | 1.00 | -5033 | -1188 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## U7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -40818.33, "dd_never": 42226.48, "dd_wf": 38622.02, "share_pos": 0.51, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -4186 / 2816 / 1570 / 2776 / 1600 / 2648 / 1356 / 1021; maxDD L6M 21561 PRE 42226 w20 L6M 120. Live S1b-COMB: mean -3377 / 3156 / 2441 / 3103 / 1856 / 3779 / 1387 / 863; maxDD L6M 16419 PRE 39155 w20 L6M 8146.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ice_ag_w10 | thr 4 pers 5 cur arm pct 0.15 | 180 | 2954 | 2146 | 3585 | 2343 | 2569 | 814 | 598 | 6061/21561 | 35033/42226 | 21429/120 | 777 | 0.02 | 1.00 | 2829 | 809 | ok | CANDIDATE-DD |
| ice_ag_w10 | thr 4 pers 5 cur arm abs 10 | 140 | 3855 | 1843 | 3550 | 2249 | 2416 | 880 | 598 | 6061/21561 | 30662/42226 | 20553/120 | 768 | 0.02 | 1.00 | 2829 | 774 | ok | CANDIDATE-DD |
| ice_ag_w30 | thr 6 pers 5 cur arm pct 0.15 | -366 | 1310 | 1460 | 3632 | 2385 | 1413 | 1366 | -84 | 6621/21561 | 20630/42226 | 28980/120 | 792 | 0.02 | 1.00 | 2829 | -1506 | FAIL | CANDIDATE-DD |
| r_ab8 | thr 2.5 pers 1 latch arm abs 45 | -234 | 4709 | 2560 | 4403 | 2938 | 2774 | 1828 | 1897 | 7200/21561 | 40937/42226 | 21278/120 | 490 | 0.02 | 1.00 | 0 | 382 | ok | CANDIDATE-DD |
| lp_ag_w10 | thr 3 pers 20 cur arm abs 35 | -1219 | 3734 | 1965 | 3788 | 3062 | 3134 | 457 | 1011 | 7341/21561 | 43069/42226 | 17164/120 | 686 | 0.02 | 1.00 | 0 | 395 | ok | CANDIDATE-DD |

U7 loss: the rule that lowers L6M drawdown most is ice_ag_w10 (f >= 4 for 5 s, armed cur 0.15); L6M maxDD 6061 vs 21561 never-cut (live line 16419), L6M mean 3585 vs 2776 never-cut, PRE maxDD 35033 vs 42226; placebo p 0.02, family p 1.00, live week delta 2829; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 112 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ice_ag_w10 | thr 4 pers 5 cur arm pct 0.15 | 180 | 2954 | 2146 | 3585 | 2343 | 2569 | 814 | 598 | 6061/21561 | 35033/42226 | 21429/120 | 777 | 0.02 | 1.00 | 2829 | 809 | ok | CANDIDATE-DD |
| ice_ag_w10 | thr 4 pers 5 cur arm abs 10 | 140 | 3855 | 1843 | 3550 | 2249 | 2416 | 880 | 598 | 6061/21561 | 30662/42226 | 20553/120 | 768 | 0.02 | 1.00 | 2829 | 774 | ok | CANDIDATE-DD |
| r_ab8 | thr 2.5 pers 1 latch arm abs 45 | -234 | 4709 | 2560 | 4403 | 2938 | 2774 | 1828 | 1897 | 7200/21561 | 40937/42226 | 21278/120 | 490 | 0.02 | 1.00 | 0 | 382 | ok | CANDIDATE-DD |
## A7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -52419.5, "dd_never": 14180.76, "dd_wf": 17645.52, "share_pos": 0.4, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 389 / 466 / 184 / 780 / 626 / 29 / 859 / 151; maxDD L6M 12461 PRE 6089 w20 L6M -17069. Live S1b-COMB: mean -1287 / -94 / 58 / 768 / 705 / 17 / 808 / 225; maxDD L6M 8518 PRE 7325 w20 L6M -11915.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| lp_ag_w30 | thr 18 pers 12 latch arm abs 15 | -721 | 385 | 49 | 939 | 411 | 146 | 391 | 398 | 5157/12461 | 5621/6089 | -8141/-17069 | 657 | 0.17 | 1.00 | -449 | -1110 | ok | CANDIDATE-DD |
| lp_ag_w30 | thr 18 pers 8 latch arm abs 15 | -778 | 342 | -12 | 915 | 396 | 125 | 387 | 406 | 5274/12461 | 5681/6089 | -8918/-17069 | 657 | 0.25 | 1.00 | -417 | -1168 | ok | CANDIDATE-DD |
| lp_ag_w30 | thr 18 pers 1 latch arm abs 15 | -754 | 342 | -5 | 874 | 390 | 181 | 396 | 410 | 5322/12461 | 5588/6089 | -9248/-17069 | 663 | 0.22 | 1.00 | -87 | -1144 | ok | CANDIDATE-DD |
| lp_ag_w30 | thr 18 pers 20 latch arm abs 15 | -572 | 409 | 67 | 954 | 418 | 121 | 388 | 392 | 5332/12461 | 5633/6089 | -7398/-17069 | 657 | 0.17 | 1.00 | -272 | -961 | ok | CANDIDATE-DD |
| lp_ag_w30 | thr 18 pers 2 latch arm abs 15 | -731 | 359 | 10 | 892 | 395 | 164 | 390 | 409 | 5344/12461 | 5586/6089 | -8894/-17069 | 661 | 0.25 | 1.00 | 33 | -1120 | ok | CANDIDATE-DD |

A7 loss: the rule that lowers L6M drawdown most is lp_ag_w30 (f >= 18 for 12 s, armed latch 15); L6M maxDD 5157 vs 12461 never-cut (live line 8518), L6M mean 939 vs 601 never-cut, PRE maxDD 5621 vs 6089; placebo p 0.17, family p 1.00, live week delta -449; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 148 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ice_ag_w60 | thr 6 pers 20 cur arm abs 25 | 1021 | 1145 | 493 | 1721 | 879 | 429 | 782 | 351 | 5392/12461 | 4857/6089 | 1164/-17069 | 584 | 0.03 | 1.00 | -952 | 109 | ok | CANDIDATE-DD |
| retr_w10 | thr 14 pers 8 cur arm pct 0.6 | 272 | 996 | 471 | 1218 | 856 | 404 | 774 | 345 | 5407/12461 | 5469/6089 | -2246/-17069 | 573 | 0.02 | 1.00 | -1854 | -118 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| micro_sg | thr -1.333 pers 1 cur arm abs 40 | -72 | 283 | 96 | 986 | 577 | 47 | 737 | 339 | 5895/12461 | 6053/6089 | -5412/-17069 | 370 | 0.02 | 1.00 | 0 | -462 | ok | CANDIDATE-DD |
## H7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -103389.0, "dd_never": 57397.21, "dd_wf": 48581.21, "share_pos": 0.4, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -88 / 270 / -1307 / 1121 / -331 / -2452 / 1453 / 88; maxDD L6M 15477 PRE 20667 w20 L6M -32750. Live S1b-COMB: mean 3186 / 2043 / 996 / 2609 / 656 / -1655 / 1468 / 57; maxDD L6M 8818 PRE 19256 w20 L6M 11007.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w10 | thr 4 pers 3 latch arm abs 10 | 1201 | 2100 | 920 | 2114 | 445 | -303 | 1569 | -58 | 4988/15477 | 15783/20667 | 6350/-32750 | 338 | 0.02 | 1.00 | 394 | 322 | ok | CANDIDATE-DD |
| adv_best_move | thr 6 pers 3 latch arm abs 10 | 255 | 427 | 437 | 1217 | 350 | -426 | 1551 | 573 | 5048/15477 | 19458/20667 | -3411/-32750 | 496 | 0.02 | 1.00 | 109 | -58 | FAIL | CANDIDATE-DD |
| adv_best_move | thr 6 pers 3 latch arm pct 0.15 | 135 | 367 | 397 | 1094 | 299 | -426 | 1489 | 554 | 5048/15477 | 20484/20667 | -4679/-32750 | 504 | 0.02 | 1.00 | 109 | -98 | FAIL | CANDIDATE-DD |
| sweep8_w60 | thr 6 pers 20 cur arm pct 0.15 | 1462 | 2383 | 1527 | 1823 | 142 | -434 | 1567 | 382 | 5146/15477 | 16156/20667 | 3037/-32750 | 394 | 0.02 | 1.00 | 244 | 604 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 5 latch arm pct 0.15 | 320 | 575 | 962 | 1487 | 44 | -266 | 1531 | 72 | 5190/15477 | 15940/20667 | -922/-32750 | 354 | 0.03 | 1.00 | 374 | 305 | ok | CANDIDATE-DD |

H7 loss: the rule that lowers L6M drawdown most is sweep8_w10 (f >= 4 for 3 s, armed latch 10); L6M maxDD 4988 vs 15477 never-cut (live line 8818), L6M mean 2114 vs 833 never-cut, PRE maxDD 15783 vs 20667; placebo p 0.02, family p 1.00, live week delta 394; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 186 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w10 | thr 4 pers 3 latch arm abs 10 | 1201 | 2100 | 920 | 2114 | 445 | -303 | 1569 | -58 | 4988/15477 | 15783/20667 | 6350/-32750 | 338 | 0.02 | 1.00 | 394 | 322 | ok | CANDIDATE-DD |
| sweep8_w60 | thr 6 pers 20 cur arm pct 0.15 | 1462 | 2383 | 1527 | 1823 | 142 | -434 | 1567 | 382 | 5146/15477 | 16156/20667 | 3037/-32750 | 394 | 0.02 | 1.00 | 244 | 604 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 5 latch arm pct 0.15 | 320 | 575 | 962 | 1487 | 44 | -266 | 1531 | 72 | 5190/15477 | 15940/20667 | -922/-32750 | 354 | 0.03 | 1.00 | 374 | 305 | ok | CANDIDATE-DD |
## O7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -34793.5, "dd_never": 7468.56, "dd_wf": 8033.08, "share_pos": 0.37, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -685 / -397 / -65 / 176 / 633 / -255 / 587 / -198; maxDD L6M 7469 PRE 5102 w20 L6M -9532. Live S1b-COMB: mean -988 / -176 / 115 / 322 / 597 / -327 / 569 / -198; maxDD L6M 6656 PRE 4532 w20 L6M -8247.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dtot8_rel_w15 | thr -0.04444 pers 1 latch arm pct 0.15 | -111 | 426 | 581 | 498 | 659 | -238 | 216 | -148 | 2725/7469 | 5195/5102 | -437/-9532 | 355 | 0.02 | 1.00 | 940 | 173 | ok | CANDIDATE-DD |
| dlt_med_w10 | thr -28.11 pers 1 latch arm pct 0.15 | -363 | 11 | 116 | 207 | 343 | -47 | 87 | -33 | 3243/7469 | 4699/5102 | -4802/-9532 | 448 | 0.05 | 1.00 | -243 | 34 | ok | CANDIDATE-DD |
| dlt_med_w10 | thr -28.11 pers 2 latch arm pct 0.15 | -61 | 181 | 226 | 240 | 435 | -44 | 92 | -68 | 3600/7469 | 5318/5102 | -4838/-9532 | 441 | 0.11 | 1.00 | 1302 | 66 | ok | CANDIDATE-DD |
| vol_ag_w30 | thr 588 pers 12 cur arm pct 0.15 | -272 | -76 | 115 | 244 | 297 | -384 | 83 | -202 | 3828/7469 | 4509/5102 | -4860/-9532 | 381 | 0.09 | 1.00 | -1193 | 71 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w10 | thr 4 pers 5 cur arm pct 0.15 | -223 | 275 | 336 | 286 | 467 | -103 | 552 | 28 | 3859/7469 | 4241/5102 | -4740/-9532 | 220 | 0.03 | 1.00 | 826 | 41 | ok | CANDIDATE-DD |

O7 loss: the rule that lowers L6M drawdown most is dtot8_rel_w15 (f ><= -0.04444 for 1 s, armed latch 0.15); L6M maxDD 2725 vs 7469 never-cut (live line 6656), L6M mean 498 vs 173 never-cut, PRE maxDD 5195 vs 5102; placebo p 0.02, family p 1.00, live week delta 940; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 109 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w10 | thr 4 pers 5 cur arm pct 0.15 | -223 | 275 | 336 | 286 | 467 | -103 | 552 | 28 | 3859/7469 | 4241/5102 | -4740/-9532 | 220 | 0.03 | 1.00 | 826 | 41 | ok | CANDIDATE-DD |
| sweep8_w10 | thr 4 pers 8 cur arm pct 0.15 | -505 | -96 | 84 | 305 | 520 | 21 | 619 | 24 | 4019/7469 | 3820/5102 | -4654/-9532 | 159 | 0.02 | 1.00 | 399 | 129 | ok | CANDIDATE-DD |
| sweep8_w10 | thr 3 pers 8 cur arm pct 0.3 | -555 | -50 | 251 | 257 | 482 | -401 | 584 | -113 | 4218/7469 | 4516/5102 | -4290/-9532 | 252 | 0.03 | 1.00 | 591 | 42 | ok | CANDIDATE-DD |
## X3 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {}
Reference rows: never-cut L1M..X' mean = -166 / 0 / 0 / 0 / 0 / 0 / 0 / 0; maxDD L6M 664 PRE 0 w20 L6M -664. Live S1b-COMB: mean -448 / 0 / 0 / 0 / 0 / 0 / 0 / 0; maxDD L6M 1794 PRE 0 w20 L6M -1794.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 0 cells

X3 loss: no ledgered cell passes the validity filter.

## X4 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {}
Reference rows: never-cut L1M..X' mean = 1195 / 0 / 0 / 0 / 0 / 0 / 0 / 0; maxDD L6M 0 PRE 0 w20 L6M 0. Live S1b-COMB: mean 795 / 0 / 0 / 0 / 0 / 0 / 0 / 0; maxDD L6M 0 PRE 0 w20 L6M 0.
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
| sweep8_w10 | thr 3 pers 1 latch arm abs 10 | 246 | 3383 | 3320 | 2979 | 1613 | 645 | 1136 | 45 | 4437/22104 | 13136/13344 | 13994/-6120 | 1220 | 0.02 | 1.00 |  | -4343 | ok | CANDIDATE-DD |
### K7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_base | thr 1.01 pers 8 cur arm abs 35 | -798 | 1481 | 759 | 937 | 378 | -1187 | 197 | -114 | 5596/14952 | 17577/18704 | -4354/-27616 | 783 | 0.06 | 1.00 |  | -106 | ok | CANDIDATE-DD |
| tot_rel_base | thr 1.01 pers 20 cur arm pct 0.45 | -720 | 2584 | 1502 | 843 | 254 | -1328 | 136 | -9 | 5702/14952 | 19265/18704 | -12124/-27616 | 746 | 0.34 | 1.00 |  | 291 | ok | CANDIDATE-DD |
### K7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_h1 | thr 0.9942 pers 8 latch arm abs 15 | 1012 | 1064 | 986 | 590 | -12 | -849 | 299 | 175 | 2262/23185 | 5980/6211 | -3776/-34239 | 1075 | 0.02 | 1.00 |  | -725 | ok | CANDIDATE-DD |
| tot_rel_h1 | thr 0.9942 pers 5 latch arm abs 10 | 861 | 609 | 683 | 414 | 11 | -567 | 98 | 41 | 2503/23185 | 5586/6211 | -2111/-34239 | 1223 | 0.03 | 1.00 |  | -876 | ok | CANDIDATE-DD |
### K7 nypm (session 4)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_base | thr 1.01 pers 12 latch arm abs 20 | 1279 | 637 | 232 | 702 | 384 | 968 | 220 | 239 | 1832/6369 | 25325/33629 | 180/-7470 | 680 | 0.03 | 1.00 |  | 8 | ok | CANDIDATE-DD |
| tot_rel_base | thr 0.5962 pers 1 cur arm abs 15 | 195 | 568 | 453 | 1197 | 800 | 1079 | 251 | 195 | 2018/6369 | 32362/33629 | 1172/-7470 | 444 | 0.03 | 1.00 |  | -574 | FAIL | CANDIDATE-DD |
### P7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| adv_best_move | thr 8 pers 2 cur arm pct 0.15 | 8797 | 9438 | 7455 | 12407 | 6763 | 3088 | 5426 | -705 | 34805/116210 | 29287/66531 | 72112/8506 | 1018 | 0.02 | 1.00 |  | -24519 | FAIL | CANDIDATE-DD |
| retr_w10 | thr 37 pers 1 cur arm pct 0.15 | 7281 | 12612 | 9581 | 11804 | 7014 | 3531 | 4186 | -1311 | 35019/116210 | 43328/66531 | 32192/8506 | 1085 | 0.02 | 1.00 |  | -26035 | FAIL | CANDIDATE-DD |
### P7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dlt_v60_w60 | thr -0.35 pers 20 latch arm pct 0.15 | 4120 | 3384 | 3945 | 4417 | 1170 | -4684 | -965 | 816 | 25430/51796 | 153520/150275 | -7972/-20541 | 904 | 0.25 | 1.00 |  | -5965 | FAIL | CANDIDATE-DD |
| tot_rel_h1 | thr 0.6156 pers 3 cur arm pct 0.15 | -1027 | 8937 | 4960 | 6218 | 2501 | -2691 | -526 | 701 | 26001/51796 | 116661/150275 | 39925/-20541 | 453 | 0.34 | 1.00 |  | -4066 | FAIL | CANDIDATE-DD |
### P7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_base | thr 0.8129 pers 1 latch arm abs 10 | 1383 | 1981 | 1353 | 1372 | -209 | 2086 | 837 | -547 | 10279/86629 | 39716/77956 | -24316/-147642 | 848 | 0.02 | 1.00 |  | -2821 | ok | CANDIDATE-DD |
| tot_rel_base | thr 1.01 pers 2 cur arm abs 15 | 40 | 2656 | 1037 | 1691 | 142 | 3080 | 213 | 1367 | 11662/86629 | 39965/77956 | -33270/-147642 | 785 | 0.02 | 1.00 |  | -2146 | FAIL | CANDIDATE-DD |
### M7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pps_rel_w30 | thr 2.626 pers 5 latch arm abs 15 | 582 | 1891 | 627 | 487 | 34 | -451 | -628 | -196 | 10106/38178 | 59809/69890 | -15408/-64988 | 1660 | 0.02 | 1.00 |  | -1641 | FAIL | CANDIDATE-DD |
| pps_rel_w30 | thr 2.626 pers 5 latch arm pct 0.3 | 345 | 1326 | 804 | 513 | 31 | -311 | -572 | -387 | 10207/38178 | 48110/69890 | -19934/-64988 | 1583 | 0.02 | 1.00 |  | -2206 | FAIL | CANDIDATE-DD |
### M7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 6 pers 5 cur arm abs 25 | 1986 | 1787 | 1425 | 749 | 117 | 162 | 591 | 38 | 4575/11667 | 7431/7583 | -3655/-17931 | 547 | 0.02 | 1.00 |  | 399 | ok | CANDIDATE-DD |
| pps_rel_w30 | thr 1.149 pers 3 cur arm abs 20 | 1203 | 1338 | 1535 | 619 | -104 | -589 | 225 | 63 | 4804/11667 | 6031/7583 | -5020/-17931 | 1013 | 0.02 | 1.00 |  | 89 | ok | CANDIDATE-DD |
### U7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ahead_rel_slow | thr 1.15 pers 12 cur arm pct 0.3 | 3386 | 3467 | 3587 | 4107 | 2690 | 2593 | 953 | 1268 | 1223/9906 | 27165/31026 | 45438/9960 | 350 | 0.02 | 1.00 |  | 89 | ok | CANDIDATE-DD |
| pps_rel_w30 | thr 2.626 pers 12 cur arm abs 15 | 2950 | 5065 | 3612 | 4688 | 3111 | 2655 | 821 | 1187 | 1788/9906 | 26115/31026 | 49523/9960 | 426 | 0.02 | 1.00 |  | 115 | ok | CANDIDATE-DD |
### U7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ice_ag_w30 | thr 3 pers 20 latch arm abs 10 | -1341 | 402 | -109 | 322 | 175 | -166 | -399 | -215 | 9434/32749 | 35452/33984 | -24790/-53967 | 572 | 0.02 | 1.00 |  | 850 | ok | CANDIDATE-DD |
| ice_ag_w60 | thr 4 pers 12 latch arm pct 0.15 | -1343 | 265 | -2 | 187 | 94 | 92 | -279 | -269 | 9542/32749 | 31075/33984 | -24103/-53967 | 584 | 0.03 | 1.00 |  | 715 | ok | CANDIDATE-DD |
### A7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| lp_ag_w30 | thr 18 pers 12 latch arm abs 15 | -721 | 385 | 49 | 939 | 411 | 146 | 391 | 398 | 5157/12461 | 5621/6089 | -8141/-17069 | 657 | 0.17 | 1.00 |  | -1110 | ok | CANDIDATE-DD |
| lp_ag_w30 | thr 18 pers 8 latch arm abs 15 | -778 | 342 | -12 | 915 | 396 | 125 | 387 | 406 | 5274/12461 | 5681/6089 | -8918/-17069 | 657 | 0.25 | 1.00 |  | -1168 | ok | CANDIDATE-DD |
### H7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 6 pers 1 latch arm pct 0.15 | 81 | 1354 | 764 | 1320 | 74 | -296 | 1825 | -167 | 3959/14606 | 15571/17912 | -779/-39488 | 173 | 0.02 | 1.00 |  | 753 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 6 pers 1 latch arm abs 10 | 258 | 1443 | 755 | 1237 | 33 | -296 | 1860 | -167 | 4144/14606 | 15571/17912 | -3276/-39488 | 169 | 0.02 | 1.00 |  | 761 | ok | CANDIDATE-DD |
### H7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cps_rel_w30 | thr 1.439 pers 3 cur arm abs 15 | 762 | 237 | 328 | 463 | 113 | 185 | -194 | 114 | 1491/3762 | 21333/23608 | -337/-5403 | 292 | 0.05 | 1.00 |  | -498 | FAIL | CANDIDATE-DD |
| cps_rel_w30 | thr 1.439 pers 12 cur arm abs 15 | 1121 | 405 | 343 | 569 | 162 | 213 | -216 | 119 | 1511/3762 | 21955/23608 | 1708/-5403 | 278 | 0.03 | 1.00 |  | -330 | ok | CANDIDATE-DD |
### O7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dtot8_rel_w15 | thr -0.04444 pers 1 latch arm pct 0.15 | -111 | 426 | 581 | 498 | 659 | -238 | 216 | -148 | 2725/7469 | 5195/5102 | -437/-9532 | 355 | 0.02 | 1.00 |  | 173 | ok | CANDIDATE-DD |
| dlt_med_w10 | thr -28.11 pers 1 latch arm pct 0.15 | -363 | 11 | 116 | 207 | 343 | -47 | 87 | -33 | 3243/7469 | 4699/5102 | -4802/-9532 | 448 | 0.05 | 1.00 |  | 34 | ok | CANDIDATE-DD |
# Lot-scaled ARM variants (V1 clip(ARM*sqrt(4/lots),15,50), V2 clip(ARM*sqrt(lots/4),15,50), USD clip($/(lots*20),10,55)): 14,742 further cells screened on the 29 features of the best rules; best valid cell per book vs the best lattice (fixed/pct) cell (L6M maxDD, mean); top 3 per book-level scope ledgered
| book | best lot-scaled cell | L6M maxDD | L6M mean | best fixed/pct cell | L6M maxDD | L6M mean |
|---|---|---|---|---|---|---|
| ALL | sweep8_w30 thr 4 pers 8 latch USD 800 | 32480 | 21247 | sweep8_w30 thr 4 pers 5 | 36812 | 21427 |
| K7 | sweep8_w30 thr 4 pers 20 cur V2 25 | 7753 | 5506 | sweep8_w30 thr 4 pers 12 | 5514 | 3657 |
| P7 | sweep8_w30 thr 4 pers 5 latch USD 1200 | 25981 | 14175 | sweep8_w30 thr 6 pers 1 | 36977 | 22753 |
| M7 | cps_rel_w10 thr 3.139 pers 3 latch V1 10 | 11646 | 417 | dtot8_rel_w15 thr -0.004938 pers 12 | 13767 | 308 |
| U7 | ice_ag_w30 thr 6 pers 8 cur USD 800 | 7756 | 3057 | ice_ag_w10 thr 4 pers 5 | 6061 | 3585 |
| A7 | lp_ag_w30 thr 18 pers 12 latch V2 10 | 5157 | 939 | lp_ag_w30 thr 18 pers 12 | 5157 | 939 |
| H7 | sweep8_w60 thr 6 pers 20 latch V2 10 | 6034 | 1631 | sweep8_w10 thr 4 pers 3 | 4988 | 2114 |
| O7 | tot_rel_base thr 1.01 pers 2 cur V2 10 | 4345 | 342 | dtot8_rel_w15 thr -0.04444 pers 1 | 2725 | 498 |
Reading: lot-scaled arms do not beat the fixed/pct arms on drawdown except P7 (USD 1600: L6M maxDD lower); none changes the picture.
# Finalists (12) and Stage 2
Groups: A_recent = best recents-consistent supported rule per book (live-week delta >= 0 preferred), B_ddbest = pure drawdown-best for contrast, C_uniform = one rule on all books. Stage 2 sets: /mnt/l2/l2vast/_th_exh/stage2/sets/bc_a_recent.json, bc_b_ddbest.json, bc_c_uniform.json (kernel bc_s2.kern_bc, panel functions bc_s2.pan_<feature> = feat_core.prim on a state slice; verified equal to the EX-FEAT panel to 0.0 on 8+5 features incl. multi-day concatenated Z). Stage 2 progress: see ledger stage2_* parts (agent S2) and /mnt/l2/l2vast/_th_exh/bc/s2_*.log.
| group | book | rule | thr | pers | mode | arm | L6M maxDD w/wo | L6M mean | held-out live-week delta | nfire |
|---|---|---|---|---|---|---|---|---|---|---|
| A_recent | K7 | imb_ag10 | 0.4043 | 2 | cur | pct 0.45 | 9560/20902 | 4065 | 0 | 1148 |
| A_recent | P7 | dlt_med_w60 | -43.42 | 20 | cur | abs 35 | 59918/133887 | 21762 | 0 | 1252 |
| A_recent | M7 | dlt_v60_w120 | -0.5588 | 2 | latch | abs 15 | 18648/44425 | 558 | 1799 | 1903 |
| A_recent | U7 | ice_ag_w10 | 4 | 5 | cur | pct 0.15 | 6061/21561 | 3585 | 2829 | 777 |
| A_recent | A7 | micro_sg | -1.333 | 1 | cur | abs 40 | 5895/12461 | 986 | 0 | 370 |
| A_recent | H7 | sweep8_w10 | 4 | 3 | latch | abs 10 | 4988/15477 | 2114 | 394 | 338 |
| A_recent | O7 | sweep8_w10 | 4 | 5 | cur | pct 0.15 | 3859/7469 | 286 | 826 | 220 |
| C_uniform | ALL | retr_w10 | 22 | 12 | latch | abs 40 | 71641/121381 | 27372 | 3485 | 3024 |
| B_ddbest | K7 | sweep8_w30 | 4 | 12 | latch | abs 10 | 5514/20902 | 3657 | -15890 | 3787 |
| B_ddbest | P7 | sweep8_w30 | 6 | 1 | latch | abs 10 | 36977/133887 | 22753 | -71288 | 1891 |
| B_ddbest | M7 | dlt_v60_w30 | -0.08929 | 20 | latch | pct 0.3 | 15798/44425 | 280 | -5033 | 2666 |
# FINAL section (EX-LBC2, written 2026-11-09 09:46Z): loss families B (book-state) and C (flow), per book, drawdown first
Basis: PRE-PROOF entry match; fills measured (market at mid -+ 0.80 pt at k+1); USD per ISO week at live lots, net of fees (FEES.md); L6M/PRE are the ledger windows. "S1" = first-order on U2 against the universe never-cut; "S2" = engine cascade against engine never-cut (set bc_a_recent / bc_b_ddbest / bc_c_uniform / bc_m7_cps; months run shown; months not run are filled from never-cut, so a partial S2 row is marked). Live week = the 186 actual live trades, held out, delta vs the actual exit (first-order). WF = purged monthly walk-forward of the picking procedure over this family ledger cells of that book (dd_wf = maxDD of the walk-forward-picked series, dd_never = maxDD of never-cut over the same months, share_pos = share of months where the pick beat never-cut; wf_ok as defined by X.walk_forward). Family p = placebo-max family null over the whole ledger. No PASS is claimed: no S2 row carries placebo draws, so nothing here is ENTER.

| group | book | rule | S1 L6M maxDD w/wo | S1 PRE maxDD w/wo | S1 L6M w20 w/wo | S1 L6M mean delta | S2 L6M maxDD w/wo | S2 PRE maxDD w/wo | S2 L6M mean delta | S2 stage | live-week delta | plc p | fam p | WF (dd_wf vs dd_never, share_pos) | ledger label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_recent | K7 | imb_ag10 >= 0.4043 pers 2 cur arm pct 0.45 | 9,560 / 20,902 | 21,646 / 26,707 | 18,437 / 1,791 | 683 | 22,732 / 35,969 | 26,891 / 22,188 | 1,491 | S2 | 0 | 0.02 | 1.00 | 39,824 vs 42,831, 0.29 | CANDIDATE-DD |
| A_recent | P7 | dlt_med_w60 <= -43.42 pers 20 cur arm abs 35 | 59,918 / 133,887 | 86,090 / 109,442 | 94,113 / -29,902 | 5,757 | 203,570 / 203,542 | 129,571 / 122,169 | 331 | S2 | 0 | 0.02 | 1.00 | 200,056 vs 144,370, 0.29 | CANDIDATE-DD |
| A_recent | M7 | dlt_v60_w120 <= -0.5588 pers 2 latch arm abs 15 | 18,648 / 44,425 | 30,421 / 50,321 | -33,620 / -68,299 | 148 | 39,410 / 48,019 | 28,806 / 44,205 | 108 | S2 | 1,799 | 0.08 | 1.00 | 41,711 vs 68,802, 0.51 | CANDIDATE-DD |
| A_recent | U7 | ice_ag_w10 >= 4 pers 5 cur arm pct 0.15 | 6,061 / 21,561 | 35,033 / 42,226 | 21,429 / 120 | 809 | 14,897 / 17,816 | 40,537 / 39,542 | -550 | S2 | 2,829 | 0.02 | 1.00 | 36,066 vs 42,226, 0.46 | CANDIDATE-DD |
| A_recent | A7 | micro_sg <= -1.333 pers 1 cur arm abs 40 | 5,895 / 12,461 | 6,053 / 6,089 | -5,412 / -17,069 | 385 | 9,821 / 9,361 | 5,949 / 8,625 | -50 | S2 | 0 | 0.02 | 1.00 | 15,491 vs 14,181, 0.43 | CANDIDATE-DD |
| A_recent | H7 | sweep8_w10 >= 4 pers 3 latch arm abs 10 | 4,988 / 15,477 | 15,783 / 20,667 | 6,350 / -32,750 | 1,281 | 19,900 / 16,242 | 14,020 / 18,436 | -1,007 | S2 | 394 | 0.02 | 1.00 | 31,200 vs 57,397, 0.43 | CANDIDATE-DD |
| A_recent | O7 | sweep8_w10 >= 4 pers 5 cur arm pct 0.15 | 3,859 / 7,469 | 4,241 / 5,102 | -4,740 / -9,532 | 110 | 3,284 / 6,958 | 5,225 / 4,797 | 111 | S2 | 826 | 0.03 | 1.00 | 9,479 vs 7,469, 0.26 | CANDIDATE-DD |
| C_uniform | K7 | retr_w10 >= 22 pers 12 latch arm abs 40 | 24,815 / 20,902 | 27,447 / 26,707 | 16,744 / 1,791 | 456 | 25,881 / 35,969 | 21,466 / 22,188 | 305 | S2[L1M,L2M,L3M,L6M,HOLD,MID,PRE-covered] | 1,817 | 1.00 | 1.00 | 39,824 vs 42,831, 0.29 | no |
| C_uniform | P7 | retr_w10 >= 22 pers 12 latch arm abs 40 | 92,482 / 133,887 | 122,101 / 109,442 | 86,404 / -29,902 | 4,659 | 183,796 / 203,542 | 123,623 / 122,169 | 1,886 | S2[L1M,L2M,L3M,L6M,HOLD,MID,PRE-covered] | 2,806 | 0.06 | 1.00 | 200,056 vs 144,370, 0.29 | LEAD |
| C_uniform | M7 | retr_w10 >= 22 pers 12 latch arm abs 40 | 42,814 / 44,425 | 46,728 / 50,321 | -60,975 / -68,299 | -602 | 41,495 / 48,019 | 49,926 / 44,205 | 39 | S2[L1M,L2M,L3M,L6M,HOLD,MID,PRE-covered] | 501 | 0.95 | 1.00 | 41,711 vs 68,802, 0.51 | no |
| C_uniform | U7 | retr_w10 >= 22 pers 12 latch arm abs 40 | 24,618 / 21,561 | 44,174 / 42,226 | 12,908 / 120 | 1,388 | 17,213 / 17,816 | 41,373 / 39,542 | 247 | S2[L1M,L2M,L3M,L6M,HOLD,MID,PRE-covered] | 0 | 1.00 | 1.00 | 36,066 vs 42,226, 0.46 | no |
| C_uniform | A7 | retr_w10 >= 22 pers 12 latch arm abs 40 | 11,144 / 12,461 | 10,163 / 6,089 | -12,839 / -17,069 | 314 | 8,444 / 9,361 | 8,592 / 8,625 | 108 | S2[L1M,L2M,L3M,L6M,HOLD,MID,PRE-covered] | -1,638 | 0.11 | 1.00 | 15,491 vs 14,181, 0.43 | LEAD FAILS-LIVE-WEEK |
| C_uniform | H7 | retr_w10 >= 22 pers 12 latch arm abs 40 | 15,870 / 15,477 | 20,820 / 20,667 | -25,004 / -32,750 | 290 | 14,995 / 16,242 | 19,425 / 18,436 | 237 | S2[L1M,L2M,L3M,L6M,HOLD,MID,PRE-covered] | 0 | 0.69 | 1.00 | 31,200 vs 57,397, 0.43 | no |
| C_uniform | O7 | retr_w10 >= 22 pers 12 latch arm abs 40 | 7,469 / 7,469 | 5,102 / 5,102 | -9,532 / -9,532 | 0 | 6,958 / 6,958 | 4,797 / 4,797 | 0 | S2[L1M,L2M,L3M,L6M,HOLD,MID,PRE-covered] | 0 | 1.00 | 1.00 | 9,479 vs 7,469, 0.26 | no |
| B_ddbest | K7 | sweep8_w30 >= 4 pers 12 latch arm abs 10 | 5,514 / 20,902 | 27,025 / 26,707 | 25,164 / 1,791 | 412 | n/a | n/a | n/a | not run | -15,890 | 0.11 | 1.00 | 39,824 vs 42,831, 0.29 | CANDIDATE-DD FAILS-LIVE-WEEK |
| B_ddbest | P7 | sweep8_w30 >= 6 pers 1 latch arm abs 10 | 36,977 / 133,887 | 78,726 / 109,442 | 264,422 / -29,902 | 10,859 | n/a | n/a | n/a | not run | -71,288 | 0.02 | 1.00 | 200,056 vs 144,370, 0.29 | CANDIDATE-DD FAILS-LIVE-WEEK |
| B_ddbest | M7 | dlt_v60_w30 <= -0.08929 pers 20 latch arm pct 0.3 | 15,798 / 44,425 | 52,692 / 50,321 | -27,496 / -68,299 | 820 | n/a | n/a | n/a | not run | -5,033 | 0.20 | 1.00 | 41,711 vs 68,802, 0.51 | CANDIDATE-DD FAILS-LIVE-WEEK |
| M7_cps | M7 | cps_rel_w10 thr 3.139 pers 8 latch arm pct 0.3 | 14,306 / 44,425 | 37,643 / 50,321 | -34,516 / -68,299 | 554 | n/a | n/a | n/a | not run | -1,135 | 0.06 | 1.00 | 41,711 vs 68,802, 0.51 | CANDIDATE-DD |

## Stack (all seven books together, sessions pooled), maxDD with / without the family rule
- Stage 1 (A_recent, the seven per-book rules stacked, first-order): L6M maxDD 69,860 vs never-cut 121,381 vs live S1b-COMB 82,873; PRE maxDD 120,198 vs 152,455; L6M worst-20 244,842 vs 77,580; L6M mean 37,001 vs 32,328.
- Stage 2 engine, A_recent per-book [S2, 43 of 43 months]: L6M maxDD 194,286 vs never-cut 191,045; PRE maxDD 139,790 vs 130,824; L6M worst-20 -57,815 vs -63,404; L6M mean delta 523/week (MDE 5,531).
- Stage 2 engine, C_uniform (one rule on all books) [S2[L1M,L2M,L3M,L6M,HOLD,MID,PRE-covered], 37 of 43 months]: L6M maxDD 147,999 vs never-cut 191,045; PRE maxDD 135,690 vs 130,824; L6M worst-20 24,508 vs -63,404; L6M mean delta 1,357/week (MDE 4,662).
- Stage 2 engine, B_ddbest: not run / not scored (as of this refresh).
- Reading of the stacks: A_recent stacks to L6M maxDD about 70k in Stage 1 (first-order, against the universe never-cut) but 194k vs 191k in the engine, i.e. the family drawdown gain does not survive the engine cascade as a stack; the per-book engine survivors are listed per book below (K7, M7, U7, O7 lower the L6M maxDD book-level; P7, A7, H7 do not). Worst-20 values are ledger-signed (S1 and S2 use different reference series, do not compare across stages).

## Plain sentences per book (loss side, families B and C)
- K7 loss [A_recent]: imb_ag10 >= 0.4043 pers 2 cur arm pct 0.45; S1 L6M maxDD 9,560 vs 20,902 never-cut, PRE maxDD 21,646 vs 26,707, worst-20 L6M 18,437 vs 1,791, L6M mean delta 683/week; engine S2 (all windows): lowers L6M maxDD in the engine (22,732 vs 35,969) and PRE maxDD 26,891 vs 22,188; L6M mean delta 1,491/week; held-out live week 0 USD (first-order); placebo p 0.02, family p 1.00, WF dd 39,824 vs never-cut 42,831 (share positive months 0.29, wf_ok False); ledger label CANDIDATE-DD.
- P7 loss [A_recent]: dlt_med_w60 <= -43.42 pers 20 cur arm abs 35; S1 L6M maxDD 59,918 vs 133,887 never-cut, PRE maxDD 86,090 vs 109,442, worst-20 L6M 94,113 vs -29,902, L6M mean delta 5,757/week; engine S2 (all windows): does NOT lower L6M maxDD in the engine (203,570 vs 203,542); L6M mean delta 331/week; held-out live week 0 USD (first-order); placebo p 0.02, family p 1.00, WF dd 200,056 vs never-cut 144,370 (share positive months 0.29, wf_ok False); ledger label CANDIDATE-DD.
- M7 loss [A_recent]: dlt_v60_w120 <= -0.5588 pers 2 latch arm abs 15; S1 L6M maxDD 18,648 vs 44,425 never-cut, PRE maxDD 30,421 vs 50,321, worst-20 L6M -33,620 vs -68,299, L6M mean delta 148/week; engine S2 (all windows): lowers L6M maxDD in the engine (39,410 vs 48,019) and PRE maxDD 28,806 vs 44,205; L6M mean delta 108/week; held-out live week 1,799 USD (first-order); placebo p 0.08, family p 1.00, WF dd 41,711 vs never-cut 68,802 (share positive months 0.51, wf_ok False); ledger label CANDIDATE-DD.
- U7 loss [A_recent]: ice_ag_w10 >= 4 pers 5 cur arm pct 0.15; S1 L6M maxDD 6,061 vs 21,561 never-cut, PRE maxDD 35,033 vs 42,226, worst-20 L6M 21,429 vs 120, L6M mean delta 809/week; engine S2 (all windows): lowers L6M maxDD in the engine (14,897 vs 17,816) and PRE maxDD 40,537 vs 39,542; L6M mean delta -550/week; held-out live week 2,829 USD (first-order); placebo p 0.02, family p 1.00, WF dd 36,066 vs never-cut 42,226 (share positive months 0.46, wf_ok False); ledger label CANDIDATE-DD.
- A7 loss [A_recent]: micro_sg <= -1.333 pers 1 cur arm abs 40; S1 L6M maxDD 5,895 vs 12,461 never-cut, PRE maxDD 6,053 vs 6,089, worst-20 L6M -5,412 vs -17,069, L6M mean delta 385/week; engine S2 (all windows): does NOT lower L6M maxDD in the engine (9,821 vs 9,361); L6M mean delta -50/week; held-out live week 0 USD (first-order); placebo p 0.02, family p 1.00, WF dd 15,491 vs never-cut 14,181 (share positive months 0.43, wf_ok False); ledger label CANDIDATE-DD.
- H7 loss [A_recent]: sweep8_w10 >= 4 pers 3 latch arm abs 10; S1 L6M maxDD 4,988 vs 15,477 never-cut, PRE maxDD 15,783 vs 20,667, worst-20 L6M 6,350 vs -32,750, L6M mean delta 1,281/week; engine S2 (all windows): does NOT lower L6M maxDD in the engine (19,900 vs 16,242); L6M mean delta -1,007/week; held-out live week 394 USD (first-order); placebo p 0.02, family p 1.00, WF dd 31,200 vs never-cut 57,397 (share positive months 0.43, wf_ok False); ledger label CANDIDATE-DD.
- O7 loss [A_recent]: sweep8_w10 >= 4 pers 5 cur arm pct 0.15; S1 L6M maxDD 3,859 vs 7,469 never-cut, PRE maxDD 4,241 vs 5,102, worst-20 L6M -4,740 vs -9,532, L6M mean delta 110/week; engine S2 (all windows): lowers L6M maxDD in the engine (3,284 vs 6,958) and PRE maxDD 5,225 vs 4,797; L6M mean delta 111/week; held-out live week 826 USD (first-order); placebo p 0.03, family p 1.00, WF dd 9,479 vs never-cut 7,469 (share positive months 0.26, wf_ok False); ledger label CANDIDATE-DD.
- M7 loss [M7_cps]: cps_rel_w10 thr 3.139 pers 8 latch arm pct 0.3; S1 L6M maxDD 14,306 vs 44,425 never-cut, PRE maxDD 37,643 vs 50,321, worst-20 L6M -34,516 vs -68,299, L6M mean delta 554/week; engine S2 not yet scored for this cell; held-out live week -1,135 USD (first-order); placebo p 0.06, family p 1.00, WF dd 41,711 vs never-cut 68,802 (share positive months 0.51, wf_ok False); ledger label CANDIDATE-DD.

Reading rule: a cell that lowers drawdown in Stage 1 but not in the engine (locks, stack gates, StopJoin already in the engine never-cut) is a first-order artefact; only the S2 column counts for a drawdown claim, and no S2 row can be ENTER. A walk-forward with wf_ok false means the picking procedure over this family did not hold its drawdown advantage out of sample. The family p is optimistic: it covers the ledgered cells only, against 96,768 screened.
