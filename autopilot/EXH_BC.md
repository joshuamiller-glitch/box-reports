# EXH_BC - loss families B (book-state) and C (flow), EX-LBC; generated 2026-11-09 03:52Z
Entry match label: PRE-PROOF. The live-week column is the HELD-OUT week: the 186 actual live trades with the EX-FEAT live panel (feat_live), delta vs the actual live exit; it is computed for book-level rows only. Features: EX-FEAT panels, all 44 months 202304-202611 (full history). Rules: each alone as a market cut (decision k, execute k+1 at mid -+ 0.80), armed on adverse excursion ARM (latch = armed once; cur = current), persistence 1-20 s, threshold lattice per prereg (DECISIONS 2026-11-09T02:57Z).
Screened: 63 features x 432 rule-thresholds x 7 persistence x 16 arms x 2 arm modes = 96,768 cells, all 77 scopes each (bc/screen_*.parquet). Ledgered with score_cell (null_ver 2): 301 cells = the top per scope by the drawdown-first key. Family p covers ledgered cells only, so it is optimistic against 96,768 screened.
Causality: noise-after-k0 test on the lattice kernel (6 features, k0 = 300 and 900 s, mid and feature replaced after k0): 2,729,879 fires at <= k0 checked, 0 changed. Pass.
Label rules: EXH_API section 3 (ENTER / CANDIDATE-DD / LEAD / no). A cell is picked per book (sessions pooled) by (L6M maxDD, worst-20, Ulcer, -mean), valid = nfire>=20, L6M mean >= never-cut, PRE maxDD <= never*1.05.

## ALL loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -732726.92, "dd_never": 177634.05, "dd_wf": 177634.05, "share_pos": 0.23, "npick": 29, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 39825 / 33914 / 15825 / 21214 / 13522 / 3265 / 12902 / 2719; maxDD L6M 117593 PRE 177634 w20 L6M 89449. Live S1b-COMB: mean 11588 / 31519 / 16583 / 23991 / 15430 / 9520 / 12266 / 2101; maxDD L6M 82873 PRE 144002 w20 L6M 190560.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 5 latch arm pct 0.3 | 4327 | 29775 | 19678 | 21400 | 8211 | -6213 | 6275 | 1564 | 37689/117593 | 155330/177634 | 140368/89449 | 10291 | 0.03 | 1.00 | -95004 | -35497 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 8 latch arm USD 1200 | 3110 | 27880 | 18584 | 21937 | 9776 | -3635 | 8700 | 2112 | 39292/117593 | 57593/177634 | 189134/89449 | 5174 | 0.02 | 1.00 | -90368 | -36715 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w60 | thr 6 pers 1 latch arm V2 10 | -1760 | 30331 | 18638 | 21872 | 7754 | -9200 | 4843 | 1266 | 40787/117593 | 118133/177634 | 170794/89449 | 9976 | 0.02 | 1.00 | -96508 | -41585 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w60 | thr 6 pers 1 latch arm abs 15 | -1760 | 30331 | 18638 | 21872 | 7754 | -9200 | 4843 | 1266 | 40787/117593 | 118133/177634 | 170794/89449 | 9976 | 0.02 | 1.00 | -96508 | -41585 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 8 latch arm pct 0.3 | 4823 | 30294 | 20738 | 22247 | 8697 | -5454 | 6847 | 1641 | 42322/117593 | 164580/177634 | 182117/89449 | 9961 | 0.08 | 1.00 | -91150 | -35001 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |

ALL loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 4 for 5 s, armed latch 0.3); L6M maxDD 37689 vs 117593 never-cut (live line 82873), L6M mean 21400 vs 21214 never-cut, PRE maxDD 155330 vs 177634; placebo p 0.03, family p 1.00, live week delta -95004; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 2 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w10 | thr 3 pers 8 cur arm pct 0.3 | 36007 | 34697 | 18942 | 26484 | 14539 | 5361 | 14768 | 2198 | 88465/117593 | 133056/177634 | 195053/89449 | 5274 | 0.37 | 1.00 | -38535 | -3818 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 6 pers 5 cur arm abs 25 | 29229 | 36763 | 18798 | 23483 | 12022 | 4135 | 14165 | 1997 | 113810/117593 | 140685/177634 | 125106/89449 | 4420 | 0.82 | 1.00 | -18568 | -10595 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## K7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -107474.66, "dd_never": 51147.18, "dd_wf": 48633.68, "share_pos": 0.29, "npick": 26, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 4971 / 5505 / 1681 / 2880 / 1477 / -2321 / 2900 / 555; maxDD L6M 26983 PRE 30403 w20 L6M -15009. Live S1b-COMB: mean 7873 / 6509 / 2238 / 2955 / 1568 / 902 / 2968 / 392; maxDD L6M 41849 PRE 23073 w20 L6M -20339.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 12 latch arm abs 10 | 1613 | 5662 | 4760 | 3186 | 1351 | -970 | 1245 | -19 | 6384/26983 | 28853/30403 | 23584/-15009 | 3769 | 0.02 | 1.00 | -15890 | -3357 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 12 latch arm pct 0.15 | 2764 | 5721 | 4595 | 2909 | 1274 | -932 | 1191 | -35 | 7012/26983 | 29787/30403 | 17409/-15009 | 3832 | 0.12 | 1.00 | -15760 | -2207 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w60 | thr 6 pers 8 latch arm abs 10 | 1132 | 5774 | 4092 | 3196 | 1288 | -423 | 1310 | 472 | 7116/26983 | 30351/30403 | 13246/-15009 | 3580 | 0.06 | 1.00 | -14754 | -3838 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| spread_t | thr 8 pers 1 latch arm pct 0.15 | 2076 | 5239 | 3591 | 2693 | 976 | -1520 | 1527 | 27 | 7120/26983 | 28743/30403 | -7417/-15009 | 2114 | 0.18 | 1.00 | -11206 | -2895 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| spread_t | thr 8 pers 1 latch arm V1 10 | 5005 | 7840 | 4565 | 2762 | 906 | -1369 | 1519 | 201 | 7199/26983 | 29964/30403 | -4615/-15009 | 1733 | 0.02 | 1.00 | -4512 | -731 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |

K7 loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 4 for 12 s, armed latch 10); L6M maxDD 6384 vs 26983 never-cut (live line 41849), L6M mean 3186 vs 2532 never-cut, PRE maxDD 28853 vs 30403; placebo p 0.02, family p 1.00, live week delta -15890; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 6 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 20 cur arm pct 0.3 | 5674 | 7901 | 4887 | 5259 | 3060 | 1777 | 1829 | 167 | 8634/26983 | 22568/30403 | 31250/-15009 | 2306 | 0.02 | 1.00 | -5284 | 703 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| spread_t | thr 8 pers 1 cur arm abs 10 | 2563 | 6436 | 3485 | 3084 | 1541 | 81 | 2099 | 381 | 8874/26983 | 25960/30403 | 1621/-15009 | 1520 | 0.32 | 1.00 | -9712 | -2408 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| spread_t | thr 8 pers 1 cur arm pct 0.15 | 2441 | 6584 | 3411 | 3104 | 1460 | -384 | 2130 | 353 | 9360/26983 | 24516/30403 | 986/-15009 | 1554 | 0.42 | 1.00 | -11033 | -2530 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## P7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -854814.99, "dd_never": 142472.44, "dd_wf": 202450.97, "share_pos": 0.26, "npick": 31, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 37881 / 24670 / 15389 / 13115 / 8875 / 3189 / 8271 / 635; maxDD L6M 126710 PRE 131881 w20 L6M -2075. Live S1b-COMB: mean 5700 / 18966 / 12054 / 14708 / 10485 / 4891 / 6746 / 315; maxDD L6M 96490 PRE 106914 w20 L6M 53844.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w30 | thr 4 pers 8 latch arm USD 1600 | 9235 | 20248 | 17210 | 15872 | 6549 | -7214 | 1941 | -896 | 23789/126710 | 109421/131881 | 165391/-2075 | 2168 | 0.02 | 1.00 | -75321 | -28646 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 2 latch arm USD 1600 | 7907 | 17935 | 14490 | 13346 | 5255 | -6115 | 1506 | -771 | 24247/126710 | 131453/131881 | 116407/-2075 | 2320 | 0.02 | 1.00 | -69997 | -29975 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 8 latch arm USD 1200 | 2444 | 18279 | 14695 | 14745 | 5396 | -9311 | 1944 | -907 | 24308/126710 | 108074/131881 | 149443/-2075 | 2317 | 0.02 | 1.00 | -96671 | -35437 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 8 latch arm abs 10 | 1396 | 19665 | 15022 | 13182 | 4046 | -10229 | 1349 | -1095 | 28821/126710 | 136378/131881 | 91355/-2075 | 2699 | 0.02 | 1.00 | -97897 | -36486 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep4_w10 | thr 4 pers 8 cur arm abs 15 | 6903 | 15618 | 11669 | 18003 | 9224 | -6313 | 3584 | -725 | 39928/126710 | 81380/131881 | 135033/-2075 | 2280 | 0.02 | 1.00 | -83434 | -30978 | FAIL | CANDIDATE-DD FAILS-LIVE-WEEK |

P7 loss: the rule that lowers L6M drawdown most is sweep8_w30 (f >= 4 for 8 s, armed latch 1600); L6M maxDD 23789 vs 126710 never-cut (live line 96490), L6M mean 15872 vs 13115 never-cut, PRE maxDD 109421 vs 131881; placebo p 0.02, family p 1.00, live week delta -75321; label CANDIDATE-DD FAILS-LIVE-WEEK.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 3 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| spread_t | thr 6 pers 20 latch arm abs 15 | 12173 | 22310 | 15647 | 13535 | 7467 | -3230 | 7315 | 24 | 73778/126710 | 100806/131881 | 55575/-2075 | 862 | 0.05 | 1.00 | -54560 | -25709 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w30 | thr 4 pers 20 cur arm V2 25 | 30287 | 30629 | 17405 | 16176 | 8922 | 3020 | 7536 | -852 | 114033/126710 | 78175/131881 | 74152/-2075 | 1286 | 0.32 | 1.00 | -10172 | -7594 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| sweep8_w10 | thr 4 pers 5 latch arm pct 0.15 | 35767 | 28182 | 17312 | 16436 | 9203 | 2564 | 4699 | -1414 | 125354/126710 | 130082/131881 | 79117/-2075 | 1245 | 0.49 | 1.00 | -41922 | -2114 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## M7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -36619.52, "dd_never": 67465.22, "dd_wf": 40788.44, "share_pos": 0.37, "npick": 32, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 406 / 4753 / 34 / -503 / -167 / 782 / -12 / -302; maxDD L6M 43318 PRE 48984 w20 L6M -68462. Live S1b-COMB: mean 40 / 3817 / -776 / -1152 / -1092 / 1825 / 517 / -301; maxDD L6M 46547 PRE 25812 w20 L6M -64633.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dtot8_rel_w15 | thr -0.004938 pers 12 cur arm pct 0.15 | -132 | 2068 | 992 | 575 | -211 | 153 | -406 | -285 | 14759/43318 | 40943/48984 | -21222/-68462 | 2091 | 0.12 | 1.00 | 1968 | -2686 | FAIL | CANDIDATE-DD |
| dtot8_rel_w15 | thr -0.004938 pers 12 latch arm V2 25 | -1071 | -333 | -515 | 80 | -770 | -365 | -508 | -352 | 15489/43318 | 49651/48984 | -31183/-68462 | 2298 | 0.03 | 1.00 | -244 | -1477 | ok | CANDIDATE-DD |
| ownbest_rel60 | thr 0.6122 pers 8 latch arm V2 30 | -1948 | 129 | -258 | 32 | -428 | 769 | -320 | -336 | 15509/43318 | 42607/48984 | -36334/-68462 | 1946 | 0.02 | 1.00 | -883 | -2354 | FAIL | CANDIDATE-DD |
| dtot8_rel_w15 | thr -0.004938 pers 12 cur arm abs 10 | -593 | 1709 | 623 | 222 | -422 | 39 | -283 | -143 | 15903/43318 | 33359/48984 | -29724/-68462 | 2049 | 0.11 | 1.00 | 1968 | -3045 | FAIL | CANDIDATE-DD |
| dtot8_rel_w15 | thr -0.004938 pers 12 latch arm V2 30 | -1777 | -792 | -1060 | 187 | -767 | -174 | -579 | -142 | 16248/43318 | 49948/48984 | -31561/-68462 | 2258 | 0.05 | 1.00 | -3331 | -2183 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |

M7 loss: the rule that lowers L6M drawdown most is dtot8_rel_w15 (f ><= -0.004938 for 12 s, armed cur 0.15); L6M maxDD 14759 vs 43318 never-cut (live line 46547), L6M mean 575 vs -503 never-cut, PRE maxDD 40943 vs 48984; placebo p 0.12, family p 1.00, live week delta 1968; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 44 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dtot8_rel_w15 | thr -0.004938 pers 12 latch arm V2 25 | -1071 | -333 | -515 | 80 | -770 | -365 | -508 | -352 | 15489/43318 | 49651/48984 | -31183/-68462 | 2298 | 0.03 | 1.00 | -244 | -1477 | ok | CANDIDATE-DD |
| dtot8_rel_w15 | thr -0.004938 pers 12 latch arm V2 30 | -1777 | -792 | -1060 | 187 | -767 | -174 | -579 | -142 | 16248/43318 | 49948/48984 | -31561/-68462 | 2258 | 0.05 | 1.00 | -3331 | -2183 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| cdiv_w60 | thr -1 pers 2 cur arm pct 0.15 | -1506 | 505 | -292 | -72 | -514 | 867 | -437 | -449 | 16301/43318 | 46134/48984 | -30214/-68462 | 2815 | 0.11 | 1.00 | -4270 | -1912 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
## U7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -78411.33, "dd_never": 42882.62, "dd_wf": 35336.34, "share_pos": 0.49, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -4144 / -604 / -796 / 3025 / 1657 / 2223 / 1326 / 1021; maxDD L6M 21436 PRE 42883 w20 L6M 45. Live S1b-COMB: mean -3377 / 127 / 422 / 3493 / 1809 / 3362 / 1432 / 863; maxDD L6M 16419 PRE 39155 w20 L6M 8146.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ice_ag_w30 | thr 6 pers 5 cur arm pct 0.15 | -355 | 1340 | 1467 | 3598 | 2400 | 1200 | 1281 | -84 | 6611/21436 | 23521/42883 | 25888/45 | 794 | 0.02 | 1.00 | 2829 | -1498 | FAIL | CANDIDATE-DD |
| r_ab8 | thr 2.5 pers 1 latch arm abs 45 | -193 | 4731 | 2504 | 4318 | 2981 | 2706 | 1692 | 1897 | 7075/21436 | 40937/42883 | 21088/45 | 492 | 0.02 | 1.00 | 0 | 389 | ok | CANDIDATE-DD |
| dlt_med_w10 | thr -28.11 pers 3 latch arm pct 0.3 | -995 | 1619 | 1092 | 3841 | 2315 | 1836 | 902 | 1461 | 7091/21436 | 44486/42883 | 24060/45 | 694 | 0.02 | 1.00 | 0 | -1219 | FAIL | CANDIDATE-DD |
| ice_ag_w10 | thr 4 pers 5 cur arm pct 0.15 | 226 | 2984 | 2151 | 3591 | 2391 | 2540 | 806 | 598 | 7277/21436 | 35541/42883 | 23476/45 | 779 | 0.05 | 1.00 | 2829 | 853 | ok | CANDIDATE-DD |
| ice_ag_w10 | thr 4 pers 5 cur arm abs 10 | 198 | 3888 | 1872 | 3565 | 2305 | 2408 | 797 | 598 | 7277/21436 | 35050/42883 | 22839/45 | 769 | 0.11 | 1.00 | 2829 | 828 | ok | CANDIDATE-DD |

U7 loss: the rule that lowers L6M drawdown most is ice_ag_w30 (f >= 6 for 5 s, armed cur 0.15); L6M maxDD 6611 vs 21436 never-cut (live line 16419), L6M mean 3598 vs 2738 never-cut, PRE maxDD 23521 vs 42883; placebo p 0.02, family p 1.00, live week delta 2829; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 23 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| r_ab8 | thr 2.5 pers 1 latch arm abs 45 | -193 | 4731 | 2504 | 4318 | 2981 | 2706 | 1692 | 1897 | 7075/21436 | 40937/42883 | 21088/45 | 492 | 0.02 | 1.00 | 0 | 389 | ok | CANDIDATE-DD |
| ice_ag_w10 | thr 4 pers 5 cur arm pct 0.15 | 226 | 2984 | 2151 | 3591 | 2391 | 2540 | 806 | 598 | 7277/21436 | 35541/42883 | 23476/45 | 779 | 0.05 | 1.00 | 2829 | 853 | ok | CANDIDATE-DD |
| ice_ag_w10 | thr 4 pers 5 cur arm abs 10 | 198 | 3888 | 1872 | 3565 | 2305 | 2408 | 797 | 598 | 7277/21436 | 35050/42883 | 22839/45 | 769 | 0.11 | 1.00 | 2829 | 828 | ok | CANDIDATE-DD |
## A7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -51311.5, "dd_never": 14131.72, "dd_wf": 14398.72, "share_pos": 0.4, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = 394 / -104 / -96 / 488 / 509 / 136 / 912 / 290; maxDD L6M 12456 PRE 6208 w20 L6M -17012. Live S1b-COMB: mean -1287 / 217 / 169 / 521 / 584 / 328 / 857 / 318; maxDD L6M 8518 PRE 7325 w20 L6M -11915.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| lp_ag_w10 | thr 15 pers 2 latch arm V2 10 | 67 | 545 | 171 | 1018 | 422 | 129 | 318 | 386 | 4722/12456 | 6340/6208 | -6294/-17012 | 726 | 0.02 | 1.00 | -135 | -327 | ok | CANDIDATE-DD |
| lp_ag_w10 | thr 15 pers 2 latch arm V2 15 | 67 | 545 | 171 | 1018 | 422 | 129 | 318 | 386 | 4722/12456 | 6340/6208 | -6294/-17012 | 726 | 0.02 | 1.00 | -135 | -327 | ok | CANDIDATE-DD |
| lp_ag_w10 | thr 15 pers 2 latch arm V2 20 | 67 | 545 | 171 | 1018 | 422 | 129 | 318 | 386 | 4722/12456 | 6340/6208 | -6294/-17012 | 726 | 0.02 | 1.00 | -135 | -327 | ok | CANDIDATE-DD |
| lp_ag_w10 | thr 15 pers 2 latch arm abs 15 | 67 | 545 | 171 | 1018 | 422 | 129 | 318 | 386 | 4722/12456 | 6340/6208 | -6294/-17012 | 726 | 0.02 | 1.00 | -135 | -327 | ok | CANDIDATE-DD |
| lp_ag_w10 | thr 15 pers 1 latch arm abs 15 | 12 | 530 | 156 | 1008 | 416 | 129 | 324 | 385 | 4727/12456 | 6292/6208 | -6625/-17012 | 727 | 0.02 | 1.00 | -270 | -382 | ok | CANDIDATE-DD |

A7 loss: the rule that lowers L6M drawdown most is lp_ag_w10 (f >= 15 for 2 s, armed latch 10); L6M maxDD 4722 vs 12456 never-cut (live line 8518), L6M mean 1018 vs 596 never-cut, PRE maxDD 6340 vs 6208; placebo p 0.02, family p 1.00, live week delta -135; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 17 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dlt_v60_w120 | thr -0.5588 pers 3 cur arm abs 35 | 1173 | 1522 | 996 | 1080 | 728 | 612 | 765 | 349 | 5134/12456 | 5255/6208 | -5002/-17012 | 535 | 0.02 | 1.00 | 101 | 214 | ok | CANDIDATE-DD |
| dlt_v60_w120 | thr -0.5588 pers 5 cur arm abs 35 | 1523 | 1684 | 1097 | 1191 | 811 | 788 | 781 | 424 | 5151/12456 | 5625/6208 | -2103/-17012 | 523 | 0.02 | 1.00 | 101 | 315 | ok | CANDIDATE-DD |
| dlt_v60_w120 | thr -0.5588 pers 8 cur arm abs 35 | 1443 | 1508 | 971 | 1292 | 852 | 747 | 818 | 413 | 5428/12456 | 5509/6208 | 2217/-17012 | 514 | 0.02 | 1.00 | 101 | 367 | ok | CANDIDATE-DD |
## H7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -96981.17, "dd_never": 54450.23, "dd_wf": 37726.91, "share_pos": 0.37, "npick": 34, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -58 / 1334 / 84 / 744 / -414 / -2206 / 1514 / 409; maxDD L6M 16682 PRE 20667 w20 L6M -36140. Live S1b-COMB: mean 3186 / 1534 / 989 / 2103 / 409 / -1655 / 1316 / 377; maxDD L6M 8818 PRE 19256 w20 L6M 11007.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w10 | thr 4 pers 3 latch arm abs 10 | 1008 | 2103 | 1550 | 2005 | 454 | -163 | 1619 | -58 | 5354/16682 | 15643/20667 | 3826/-36140 | 338 | 0.02 | 1.00 | 394 | 321 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 20 latch arm pct 0.15 | -533 | 1647 | 666 | 1337 | 368 | 1 | 1629 | 381 | 5606/16682 | 12568/20667 | 18/-36140 | 477 | 0.02 | 1.00 | 244 | -475 | ok | CANDIDATE-DD |
| adv_best_move | thr 6 pers 3 latch arm abs 10 | 139 | 367 | 295 | 1110 | 351 | -309 | 1555 | 573 | 5637/16682 | 19423/20667 | -6645/-36140 | 496 | 0.02 | 1.00 | 109 | -110 | FAIL | CANDIDATE-DD |
| sweep8_w10 | thr 4 pers 2 latch arm abs 10 | 534 | 3026 | 1197 | 1752 | 334 | -163 | 1525 | 48 | 5817/16682 | 13477/20667 | 574/-36140 | 374 | 0.02 | 1.00 | 394 | 592 | ok | CANDIDATE-DD |
| sweep8_w10 | thr 4 pers 2 latch arm pct 0.15 | 531 | 3022 | 1130 | 1748 | 342 | -237 | 1527 | 25 | 5817/16682 | 13477/20667 | 255/-36140 | 379 | 0.02 | 1.00 | 419 | 589 | ok | CANDIDATE-DD |

H7 loss: the rule that lowers L6M drawdown most is sweep8_w10 (f >= 4 for 3 s, armed latch 10); L6M maxDD 5354 vs 16682 never-cut (live line 8818), L6M mean 2005 vs 744 never-cut, PRE maxDD 15643 vs 20667; placebo p 0.02, family p 1.00, live week delta 394; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 67 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w10 | thr 4 pers 3 latch arm abs 10 | 1008 | 2103 | 1550 | 2005 | 454 | -163 | 1619 | -58 | 5354/16682 | 15643/20667 | 3826/-36140 | 338 | 0.02 | 1.00 | 394 | 321 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 4 pers 20 latch arm pct 0.15 | -533 | 1647 | 666 | 1337 | 368 | 1 | 1629 | 381 | 5606/16682 | 12568/20667 | 18/-36140 | 477 | 0.02 | 1.00 | 244 | -475 | ok | CANDIDATE-DD |
| sweep8_w10 | thr 4 pers 2 latch arm abs 10 | 534 | 3026 | 1197 | 1752 | 334 | -163 | 1525 | 48 | 5817/16682 | 13477/20667 | 574/-36140 | 374 | 0.02 | 1.00 | 394 | 592 | ok | CANDIDATE-DD |
## O7 loss (sessions pooled)  walk-forward of the picking over the ledgered cells: {"total": -39605.5, "dd_never": 7488.56, "dd_wf": 7488.56, "share_pos": 0.34, "npick": 35, "months": 35, "wf_ok": false}
Reference rows: never-cut L1M..X' mean = -667 / -289 / -60 / 177 / 653 / -178 / 601 / -221; maxDD L6M 7489 PRE 5097 w20 L6M -9447. Live S1b-COMB: mean -988 / -396 / 115 / 225 / 621 / -127 / 655 / -220; maxDD L6M 6656 PRE 4532 w20 L6M -8247.
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dlt_med_w10 | thr -28.11 pers 1 latch arm pct 0.15 | -346 | 20 | 122 | 204 | 340 | -55 | 87 | -33 | 3453/7489 | 4701/5097 | -4822/-9447 | 449 | 0.17 | 1.00 | -243 | 27 | ok | CANDIDATE-DD |
| sweep4_w10 | thr 6 pers 2 cur arm pct 0.15 | -77 | 230 | 304 | 282 | 449 | -61 | 250 | -189 | 3728/7489 | 4097/5097 | -2526/-9447 | 338 | 0.03 | 1.00 | 501 | -65 | FAIL | CANDIDATE-DD |
| vol_ag_w30 | thr 588 pers 12 cur arm pct 0.15 | -254 | -66 | 272 | 322 | 335 | -381 | 58 | -202 | 3848/7489 | 4434/5097 | -2972/-9447 | 382 | 0.08 | 1.00 | -1193 | 145 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| tot_rel_slow | thr 0.6769 pers 1 latch arm pct 0.15 | -312 | 171 | 547 | 576 | 614 | 70 | 190 | -68 | 3881/7489 | 5151/5097 | 457/-9447 | 318 | 0.03 | 1.00 | -1264 | 355 | ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| dtot8_rel_w15 | thr -0.04444 pers 1 latch arm pct 0.15 | -93 | 433 | 585 | 451 | 653 | -161 | 216 | -148 | 3913/7489 | 5145/5097 | -1694/-9447 | 357 | 0.03 | 1.00 | 940 | 174 | ok | CANDIDATE-DD |

O7 loss: the rule that lowers L6M drawdown most is dlt_med_w10 (f ><= -28.11 for 1 s, armed latch 0.15); L6M maxDD 3453 vs 7489 never-cut (live line 6656), L6M mean 204 vs 177 never-cut, PRE maxDD 4701 vs 5097; placebo p 0.17, family p 1.00, live week delta -243; label CANDIDATE-DD.

Recents-consistent subset (L1M, L2M >= -0.5 MDE, L3M, L6M delta > 0, PRE maxDD <= never*1.05, PRE delta >= -0.5 MDE): 9 cells
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w10 | thr 4 pers 5 cur arm pct 0.15 | -206 | 280 | 340 | 269 | 461 | -100 | 518 | 28 | 3924/7489 | 4236/5097 | -4852/-9447 | 220 | 0.03 | 1.00 | 826 | 41 | ok | CANDIDATE-DD |
| sweep8_w10 | thr 4 pers 8 cur arm pct 0.15 | -488 | -86 | 89 | 296 | 516 | 24 | 585 | 24 | 4094/7489 | 3840/5097 | -4553/-9447 | 159 | 0.02 | 1.00 | 399 | 116 | ok | CANDIDATE-DD |
| sweep8_w10 | thr 3 pers 8 cur arm pct 0.3 | -561 | -70 | 235 | 250 | 478 | -404 | 570 | -113 | 4241/7489 | 4062/5097 | -4474/-9447 | 249 | 0.03 | 1.00 | 591 | 32 | ok | CANDIDATE-DD |
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
| sweep8_w10 | thr 3 pers 1 latch arm abs 10 | 665 | 2928 | 3041 | 2795 | 1524 | 513 | 939 | 45 | 4522/23228 | 13136/14762 | 12679/-10100 | 1220 | 0.02 | 1.00 |  | -3956 | ok | CANDIDATE-DD |
| sweep8_w30 | thr 3 pers 20 latch arm abs 10 | 538 | 2557 | 2892 | 2573 | 1311 | -158 | 813 | 117 | 4710/23228 | 12496/14762 | 14977/-10100 | 1270 | 0.02 | 1.00 |  | -4082 | ok | CANDIDATE-DD |
### K7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_base | thr 0.888 pers 8 latch arm abs 20 | 96 | 2507 | 1632 | 935 | 43 | -1319 | 156 | 23 | 4599/13569 | 13406/16206 | -5643/-31166 | 998 | 0.02 | 1.00 |  | 376 | ok | CANDIDATE-DD |
| tot_rel_slow | thr 0.8676 pers 8 latch arm abs 20 | -25 | 2081 | 1510 | 800 | 177 | -1028 | 261 | -8 | 5181/13569 | 8501/16206 | -4875/-31166 | 999 | 0.03 | 1.00 |  | -50 | ok | CANDIDATE-DD |
### K7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_h1 | thr 0.9942 pers 8 latch arm abs 15 | 1020 | 1239 | 1105 | 757 | 89 | -946 | 241 | 175 | 2232/20697 | 5900/6231 | 129/-31954 | 1064 | 0.02 | 1.00 |  | -724 | ok | CANDIDATE-DD |
| ahead_rel_fast | thr 1 pers 2 latch arm abs 20 | 1503 | 770 | 732 | 556 | -245 | -1164 | 228 | 287 | 2601/20697 | 6304/6231 | -6998/-31954 | 1052 | 0.02 | 1.00 |  | -241 | ok | CANDIDATE-DD |
### K7 nypm (session 4)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_base | thr 1.01 pers 12 latch arm abs 20 | 1285 | 650 | 247 | 730 | 374 | 1103 | 119 | 239 | 2243/6324 | 32319/39576 | -948/-7330 | 678 | 0.05 | 1.00 |  | 122 | ok | CANDIDATE-DD |
| ownbest_rel60 | thr 0.5 pers 5 latch arm abs 20 | 445 | 564 | 198 | 1058 | 819 | 537 | 147 | 346 | 2340/6324 | 24954/39576 | 5947/-7330 | 554 | 0.18 | 1.00 |  | -120 | ok | CANDIDATE-DD |
### P7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| adv_best_move | thr 8 pers 2 cur arm pct 0.15 | 8029 | 9060 | 6945 | 12562 | 6685 | 2911 | 5314 | -705 | 32818/106637 | 29287/78845 | 70768/49424 | 1015 | 0.02 | 1.00 |  | -29485 | FAIL | CANDIDATE-DD |
| retr_w10 | thr 37 pers 1 cur arm pct 0.15 | 6932 | 12499 | 9481 | 11973 | 6947 | 2701 | 3918 | -1311 | 35457/106637 | 43328/78845 | 36429/49424 | 1082 | 0.02 | 1.00 |  | -30581 | FAIL | CANDIDATE-DD |
### P7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dlt_v60_w10 | thr -0.06122 pers 20 cur arm abs 10 | -102 | 4457 | 3740 | 5635 | 1638 | -7210 | -97 | 356 | 23919/44287 | 129854/160840 | 26321/-16876 | 738 | 0.12 | 1.00 |  | -6136 | FAIL | CANDIDATE-DD |
| dlt_v60_w10 | thr -0.06122 pers 20 cur arm pct 0.15 | -302 | 3324 | 2985 | 5382 | 1683 | -6799 | -554 | 508 | 23919/44287 | 144080/160840 | 19794/-16876 | 753 | 0.17 | 1.00 |  | -7268 | FAIL | CANDIDATE-DD |
### P7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tot_rel_base | thr 1.01 pers 3 cur arm abs 10 | 1773 | 2916 | 2196 | 2352 | 384 | 1725 | 265 | 635 | 9007/103128 | 39108/75038 | -18071/-164165 | 815 | 0.02 | 1.00 |  | -1707 | ok | CANDIDATE-DD |
| tot_rel_base | thr 0.8129 pers 1 latch arm abs 10 | 1033 | 2018 | 1297 | 1306 | -450 | 1424 | 839 | -547 | 11201/103128 | 39716/75038 | -27912/-164165 | 839 | 0.02 | 1.00 |  | -2606 | ok | CANDIDATE-DD |
### M7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cps_rel_w30 | thr 2.044 pers 20 latch arm abs 15 | 122 | 1642 | 452 | 206 | -49 | 467 | -711 | -234 | 10896/34745 | 67785/70941 | -21506/-61665 | 1706 | 0.05 | 1.00 |  | -1872 | FAIL | CANDIDATE-DD |
| pps_rel_w30 | thr 2.626 pers 5 latch arm pct 0.3 | 299 | 1295 | 576 | 200 | 136 | 919 | -611 | -387 | 11065/34745 | 50980/70941 | -19918/-61665 | 1580 | 0.02 | 1.00 |  | -2220 | FAIL | CANDIDATE-DD |
### M7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pps_rel_w30 | thr 1.149 pers 2 cur arm abs 20 | 786 | 1099 | 1333 | 561 | -81 | -760 | 170 | 68 | 4655/12246 | 7537/7533 | -3600/-18056 | 1018 | 0.02 | 1.00 |  | -320 | ok | CANDIDATE-DD |
| pps_rel_w30 | thr 1.149 pers 5 cur arm abs 20 | 1268 | 1360 | 1215 | 612 | -65 | -817 | 166 | 45 | 4966/12246 | 7079/7533 | -2605/-18056 | 1010 | 0.02 | 1.00 |  | 162 | ok | CANDIDATE-DD |
### U7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ahead_rel_slow | thr 1.15 pers 12 cur arm pct 0.3 | 3406 | 3487 | 3616 | 3904 | 2662 | 2594 | 931 | 1268 | 1153/9836 | 28804/31041 | 45054/10132 | 351 | 0.02 | 1.00 |  | 104 | ok | CANDIDATE-DD |
| pps_rel_w30 | thr 2.626 pers 12 cur arm abs 15 | 2972 | 4035 | 3514 | 4498 | 3072 | 2617 | 803 | 1187 | 1718/9836 | 26115/31041 | 49555/10132 | 428 | 0.02 | 1.00 |  | 2 | ok | CANDIDATE-DD |
### U7 london (session 1)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ice_ag_w30 | thr 4 pers 1 latch arm pct 0.15 | -1214 | 241 | -115 | 242 | 187 | 589 | -357 | -291 | 8527/33738 | 35756/39568 | -21257/-56352 | 580 | 0.02 | 1.00 |  | 715 | ok | CANDIDATE-DD |
| ice_ag_w30 | thr 4 pers 1 latch arm abs 10 | -1302 | 493 | -65 | 398 | 445 | 682 | -326 | -175 | 8594/33738 | 28425/39568 | -22455/-56352 | 571 | 0.02 | 1.00 |  | 967 | ok | CANDIDATE-DD |
### A7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| lp_ag_w10 | thr 15 pers 2 latch arm V2 10 | 67 | 545 | 171 | 1018 | 422 | 129 | 318 | 386 | 4722/12456 | 6340/6208 | -6294/-17012 | 726 | 0.02 | 1.00 |  | -327 | ok | CANDIDATE-DD |
| lp_ag_w10 | thr 15 pers 2 latch arm V2 15 | 67 | 545 | 171 | 1018 | 422 | 129 | 318 | 386 | 4722/12456 | 6340/6208 | -6294/-17012 | 726 | 0.02 | 1.00 |  | -327 | ok | CANDIDATE-DD |
### H7 asia (session 0)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sweep8_w10 | thr 4 pers 2 latch arm pct 0.15 | 289 | 1487 | 435 | 1797 | 395 | -305 | 1824 | -4 | 4971/16891 | 12319/17912 | 1542/-42912 | 156 | 0.02 | 1.00 |  | 132 | ok | CANDIDATE-DD |
| sweep8_w10 | thr 4 pers 2 latch arm abs 10 | 289 | 1487 | 501 | 1778 | 403 | -224 | 1835 | -4 | 4971/16891 | 12319/17912 | 1087/-42912 | 155 | 0.02 | 1.00 |  | 132 | ok | CANDIDATE-DD |
### H7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cps_rel_w30 | thr 1.439 pers 3 cur arm abs 15 | 764 | 237 | 328 | 462 | 145 | 332 | -193 | 114 | 1496/3747 | 21323/23673 | -362/-5368 | 291 | 0.09 | 1.00 |  | -499 | FAIL | CANDIDATE-DD |
| cps_rel_w30 | thr 1.439 pers 12 cur arm abs 15 | 1123 | 405 | 343 | 630 | 223 | 359 | -215 | 119 | 1516/3747 | 21965/23673 | 2049/-5368 | 276 | 0.02 | 1.00 |  | -331 | ok | CANDIDATE-DD |
### O7 nyam (session 3)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | w20 L6M w/wo | nfire | plc p | fam p | HELD-OUT live-week delta (186 actual trades, vs actual) | worst recent window delta | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dlt_med_w10 | thr -28.11 pers 1 latch arm pct 0.15 | -346 | 20 | 122 | 204 | 340 | -55 | 87 | -33 | 3453/7489 | 4701/5097 | -4822/-9447 | 449 | 0.17 | 1.00 |  | 27 | ok | CANDIDATE-DD |
| sweep4_w10 | thr 6 pers 2 cur arm pct 0.15 | -77 | 230 | 304 | 282 | 449 | -61 | 250 | -189 | 3728/7489 | 4097/5097 | -2526/-9447 | 338 | 0.03 | 1.00 |  | -65 | FAIL | CANDIDATE-DD |
# Lot-scaled ARM variants (V1 clip(ARM*sqrt(4/lots),15,50), V2 clip(ARM*sqrt(lots/4),15,50), USD clip($/(lots*20),10,55)): 14,742 further cells screened on the 29 features of the best rules; best valid cell per book vs the best lattice (fixed/pct) cell (L6M maxDD, mean); top 3 per book-level scope ledgered
| book | best lot-scaled cell | L6M maxDD | L6M mean | best fixed/pct cell | L6M maxDD | L6M mean |
|---|---|---|---|---|---|---|
| ALL | sweep8_w30 thr 4 pers 8 latch USD 1200 | 39292 | 21937 | sweep8_w30 thr 4 pers 5 | 37689 | 21400 |
| K7 | spread_t thr 8 pers 1 latch V1 10 | 7199 | 2762 | sweep8_w30 thr 4 pers 12 | 6384 | 3186 |
| P7 | sweep8_w30 thr 4 pers 8 latch USD 1600 | 23789 | 15872 | sweep8_w30 thr 4 pers 8 | 28821 | 13182 |
| M7 | dtot8_rel_w15 thr -0.004938 pers 12 latch V2 25 | 15489 | 80 | dtot8_rel_w15 thr -0.004938 pers 12 | 14759 | 575 |
| U7 | ice_ag_w30 thr 6 pers 8 cur USD 800 | 7746 | 2888 | ice_ag_w30 thr 6 pers 5 | 6611 | 3598 |
| A7 | lp_ag_w10 thr 15 pers 2 latch V2 10 | 4722 | 1018 | lp_ag_w10 thr 15 pers 2 | 4722 | 1018 |
| H7 | sweep8_w60 thr 6 pers 20 latch V2 10 | 6967 | 1577 | sweep8_w10 thr 4 pers 3 | 5354 | 2005 |
| O7 | tot_rel_base thr 0.888 pers 1 cur V2 10 | 4170 | 203 | dlt_med_w10 thr -28.11 pers 1 | 3453 | 204 |
Reading: lot-scaled arms do not beat the fixed/pct arms on drawdown except P7 (USD 1600: L6M maxDD lower); none changes the picture.
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