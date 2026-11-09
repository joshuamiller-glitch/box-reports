# EXH_G - family G (combinations + learned shapes), EX-LG - refresh 05:10Z
Entry match PRE-PROOF. null_ver 2. Tables below are universe U2 (cells with universe_ver U2; the U1 screen cells stay in the ledger). Method files: code/th_exh_g (g_data, g_wf, g_score, g_combo, g_pairwf, g_page); pre-registrations and addenda 1-3 in DECISIONS.md.

## Headline
- Learned trees (LightGBM single tree, <=8 leaves, 265 features, 3 seeds, purged monthly WF from 202310, thr lattice 0..3200 USD; DDT/MEANT = one vote per trade; U2 rerun 60 cells, U1 had 240): none beats never-cut on L6M mean; the drawdown-lowering cells (stack L6M maxDD 121k to 68k) cost 11-18k/week and fire on 40-60% of trades (exposure shrink); the live week is mixed. Seeds disagree: no shape beyond regime/clock. Label no.
- In-sample pair/vote combinations (G_AND/G_OR/G_VOTE2of3, built on U1 from top single rules; components picked from thousands of cells, so selection multiplicity is huge): headline maxDD cuts (117.6k to 31-35k stack; K7 27.0k to 4.6k) are NOT evidence; many fire on 33-61% of trades (OR of two cutters is an exposure shrink where share>~35%) and live-week deltas are mixed (+4.0k to -16.8k). They are screen-only. Family-null accounting for them: 1,014 cells examined, drawn from a pool of 5,625 single rules.
- Pairing INSIDE the purged walk-forward (G_PAIRWF; per test month, components and pair chosen on the trailing 26 weeks ending 7 days before the month, top 3 per family, all cross pairs AND/OR plus singles, selected by train maxDD subject to train delta >= 0): honest estimate. U1 (families A,B,C,D): per-book picks L6M stack maxDD 121.4k to 79.3k, PRE 152.5k to 115.3k, L6M mean delta -3.4k/week, share of trades exited early 41%; one-rule-for-all picks L6M 94.9k, PRE 118.1k, L6M mean delta +2.2k/week, share 37%. U2 (only A and D, B/C not yet on U2): per-book L6M 112.0k vs 121.4k (delta -1.3k/week), ALL L6M 97.9k vs 121.4k (delta -3.4k/week), PRE 112.9k / 114.8k vs 152.5k, share 48% / 40%. So walk-forward shrinks the in-sample 70% maxDD cut to 10-35%, partly by cutting a large share of trades; the L6M mean is not kept on U2. Candidates only if the page rules (rec-ok, placebo, live week) pass: see ledger labels.
- Not done yet (handoff): pair pool and WF on U2 once B/C are re-scored on U2; E conditioners on finalists; per-book learned trees (ran one test month then stopped for the 2-process budget; code supports g_wf.py OBJ SEEDS B); Stage 2 for finalists (none qualifies); causality: fire at second k reads only the feature row k (EX-FEAT noise test), training labels use the future only inside earlier months with 7-day purge; kernel_leak_test not yet run on the G kernel (it only reads F[0,0] and calls market_exit; its br_k guard duplicates the contract).

Cells registered by EX-LG: 101486 rows (1318 cells).
# EXH_G - family G (combinations + learned shapes), EX-LG
generated 11-09 05:08 UTC; entry match PRE-PROOF; null_ver 2; family p not yet attached (label computed with p_family=1, WF=False, so ENTER is impossible here; CANDIDATE-DD/LEAD are the live labels).

Cells registered by EX-LG: 101640 rows (1320 cells).
### Stack (all books), top by L6M maxDD reduction, nfire>=20
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_PAIRWF_ALL | WF ALL cand=29696.0 | 7057 (37%) | 18844/23679/9862/22914 | 94881 / 121381 | 118120 / 152455 | 165849 / 77580 | 2162 | 0.12 | nan | CANDIDATE-DD |
| G_TREE_WF | DDT pooled s1 thr200 | 12987 (68%) | -13742/2845/858/2418 | 67672 / 121381 | 306129 / 152455 | -128915 / 77580 | -18334 | 0.03 | -12625 | no |
| G_TREE_WF | DDT pooled s1 thr100 | 13502 (70%) | -7877/5972/2943/3546 | 67672 / 121381 | 377614 / 152455 | -96073 / 77580 | -17206 | 0.28 | -12425 | no |
| G_TREE_WF | DDT pooled s0 thr0 | 11519 (60%) | 16169/10847/8105/9267 | 68158 / 121381 | 224653 / 152455 | -17266 / 77580 | -11485 | 0.06 | 369 | no |
| G_TREE_WF | DDT pooled s0 thr10 | 10210 (53%) | 16169/10847/8105/9267 | 68158 / 121381 | 196224 / 152455 | -17266 / 77580 | -11485 | 0.15 | 369 | no |
| G_TREE_WF | DDT pooled s0 thr25 | 9584 (50%) | 16169/10847/8105/9267 | 68158 / 121381 | 196224 / 152455 | -17266 / 77580 | -11485 | 0.11 | 369 | no |
| G_TREE_WF | DDT pooled s2 thr100 | 12200 (64%) | -7412/12310/5998/8276 | 69301 / 121381 | 150847 / 152455 | -51447 / 77580 | -12476 | 0.06 | -96 | no |
| G_TREE_WF | MEANT pooled s1 thr0 | 8436 (44%) | 3430/13328/5353/15234 | 71214 / 121381 | 152455 / 152455 | 60034 / 77580 | -5518 | 0.03 | 3197 | no |
| G_TREE_WF | MEANT pooled s1 thr10 | 8436 (44%) | 3430/13328/5353/15234 | 71214 / 121381 | 152455 / 152455 | 60034 / 77580 | -5518 | 0.02 | 3197 | no |
| G_TREE_WF | MEANT pooled s1 thr25 | 8224 (43%) | 3430/13328/5353/15234 | 71214 / 121381 | 152455 / 152455 | 60034 / 77580 | -5518 | 0.03 | 3197 | no |
| G_TREE_WF | DDT pooled s2 thr0 | 12896 (67%) | -7412/12310/5975/7784 | 71543 / 121381 | 236668 / 152455 | -53117 / 77580 | -12969 | 0.17 | -96 | no |
| G_TREE_WF | DDT pooled s2 thr10 | 12831 (67%) | -7412/12310/5975/7784 | 71543 / 121381 | 236668 / 152455 | -53117 / 77580 | -12969 | 0.29 | -96 | no |

### Book K7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | MEANT pooled s1 thr100 | 187 (3%) | 7702/9464/4408/4811 | 20902 / 20902 | 26707 / 26707 | 20426 / 1791 | 278 | 1.00 | 1363 | LEAD |
| G_TREE_WF | DDT pooled s0 thr100 | 1595 (25%) | 1971/5393/2893/2085 | 12573 / 20902 | 38861 / 26707 | -18552 / 1791 | -1297 | 0.08 | 0 | no |
| G_TREE_WF | DDT pooled s1 thr10 | 4631 (72%) | 3656/3923/2237/1045 | 16781 / 20902 | 55365 / 26707 | -9856 / 1791 | -2201 | 0.55 | 2583 | no |
| G_TREE_WF | DDT pooled s1 thr25 | 4631 (72%) | 3656/3923/2237/1045 | 16781 / 20902 | 55365 / 26707 | -9856 / 1791 | -2201 | 0.58 | 2583 | no |
| G_TREE_WF | DDT pooled s1 thr0 | 4631 (72%) | 3656/3923/2237/1045 | 16781 / 20902 | 55365 / 26707 | -9856 / 1791 | -2201 | 0.62 | 2583 | no |
| G_TREE_WF | DDT pooled s1 thr200 | 4457 (69%) | 3825/4332/2446/1163 | 17363 / 20902 | 55005 / 26707 | -11091 / 1791 | -2083 | 0.38 | 2583 | no |

### Book P7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_PAIRWF_ALL | WF ALL cand=29696.0 | 1631 (34%) | 15750/15718/10636/14989 | 77104 / 133887 | 107580 / 109442 | 65988 / -29902 | 3095 | 0.11 | nan | CANDIDATE-DD |
| G_PAIRWF_BOOK | WF BOOK cand=11079.0 | 2007 (42%) | 15454/26031/16447/14769 | 120991 / 133887 | 148383 / 109442 | 33949 / -29902 | 2876 | 0.29 | nan | LEAD |
| G_TREE_WF | DDT pooled s1 thr200 | 3152 (66%) | -10850/179/1102/1199 | 51398 / 133887 | 234698 / 109442 | -128998 / -29902 | -10695 | 0.02 | -16131 | no |
| G_TREE_WF | DDT pooled s0 thr0 | 2881 (61%) | 18695/9041/9256/8372 | 56641 / 133887 | 242187 / 109442 | -2577 / -29902 | -3522 | 0.05 | 0 | no |
| G_TREE_WF | DDT pooled s0 thr10 | 2570 (54%) | 18695/9041/9256/8372 | 56641 / 133887 | 181958 / 109442 | -2577 / -29902 | -3522 | 0.03 | 0 | no |
| G_TREE_WF | DDT pooled s0 thr25 | 2434 (51%) | 18695/9041/9256/8372 | 56641 / 133887 | 181958 / 109442 | -2577 / -29902 | -3522 | 0.02 | 0 | no |

### Book M7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | DDT pooled s0 thr800 | 220 (6%) | 591/-341/-1283/160 | 34333 / 44425 | 34086 / 50321 | -60739 / -68299 | 366 | 0.75 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT pooled s0 thr200 | 552 (15%) | -1275/-1274/-1873/-190 | 35617 / 44425 | 38765 / 50321 | -60359 / -68299 | 16 | 0.77 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT pooled s0 thr400 | 513 (14%) | -1275/-1274/-1873/-190 | 35617 / 44425 | 38765 / 50321 | -60359 / -68299 | 16 | 0.80 | 0 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=11079.0 | 1568 (41%) | 1635/920/-810/-676 | 39922 / 44425 | 45859 / 50321 | -57210 / -68299 | 32 | 0.82 | nan | CANDIDATE-DD |
| G_PAIRWF_BOOK | WF BOOK cand=12821.0 | 1839 (49%) | 2779/4215/1105/-201 | 41844 / 44425 | 33988 / 50321 | -46941 / -68299 | 340 | 0.94 | nan | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr0 | 1032 (27%) | 808/1927/195/-37 | 43848 / 44425 | 42977 / 50321 | -56135 / -68299 | 503 | 0.88 | 0 | CANDIDATE-DD |

### Book U7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_PAIRWF_BOOK | WF BOOK cand=11079.0 | 774 (56%) | -3313/1494/687/1968 | 13700 / 21561 | 36432 / 42226 | -21053 / 120 | -853 | 0.17 | nan | no |
| G_PAIRWF_ALL | WF ALL cand=12821.0 | 540 (39%) | -3062/2854/1294/3932 | 15636 / 21561 | 37586 / 42226 | 13902 / 120 | -89 | 0.18 | nan | no |
| G_PAIRWF_ALL | WF ALL cand=11079.0 | 539 (39%) | -3755/2508/1063/3821 | 15636 / 21561 | 37586 / 42226 | 11132 / 120 | -200 | 0.22 | nan | no |
| G_PAIRWF_BOOK | WF BOOK cand=12821.0 | 781 (57%) | -3975/969/1083/1891 | 15990 / 21561 | 40341 / 42226 | -24586 / 120 | -931 | 0.32 | nan | no |
| G_PAIRWF_BOOK | WF BOOK cand=29696.0 | 617 (45%) | -3830/3283/1063/2354 | 17935 / 21561 | 45294 / 42226 | -16513 / 120 | -422 | 0.32 | nan | no |
| G_TREE_WF | MEANT pooled s2 thr10 | 574 (42%) | -4198/2919/1598/2607 | 19015 / 21561 | 35499 / 42226 | -10794 / 120 | -214 | 0.34 | 0 | no |

### Book A7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_PAIRWF_BOOK | WF BOOK cand=12821.0 | 694 (59%) | -1638/151/234/952 | 10097 / 12461 | 6393 / 6089 | -14619 / -17069 | 352 | 0.69 | nan | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr0 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.94 | 616 | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr25 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.91 | 616 | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr10 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.89 | 616 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=29696.0 | 432 (37%) | -828/849/538/817 | 6842 / 12461 | 8629 / 6089 | -14056 / -17069 | 216 | 0.03 | nan | LEAD |
| G_PAIRWF_BOOK | WF BOOK cand=29696.0 | 580 (49%) | -1111/427/486/623 | 7883 / 12461 | 8360 / 6089 | -12188 / -17069 | 23 | 0.94 | nan | LEAD |

### Book H7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | DDT pooled s0 thr100 | 231 (21%) | -491/898/-817/1606 | 14621 / 15477 | 12481 / 20667 | -10435 / -32750 | 485 | 0.29 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT pooled s0 thr200 | 146 (13%) | -88/1007/-744/1771 | 14621 / 15477 | 12620 / 20667 | -8753 / -32750 | 650 | 0.26 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT pooled s0 thr400 | 129 (12%) | -88/1007/-744/1771 | 14621 / 15477 | 12620 / 20667 | -8753 / -32750 | 650 | 0.23 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s1 thr100 | 25 (2%) | 2414/2596/244/1865 | 15477 / 15477 | 20667 / 20667 | -23435 / -32750 | 216 | 1.00 | 0 | LEAD |
| G_TREE_WF | DDT pooled s1 thr200 | 719 (66%) | 897/532/-280/937 | 13272 / 15477 | 15065 / 20667 | -16606 / -32750 | -184 | 0.25 | 0 | no |
| G_TREE_WF | DDT pooled s1 thr400 | 605 (55%) | 897/532/-280/562 | 13272 / 15477 | 15065 / 20667 | -23620 / -32750 | -558 | 0.22 | 0 | no |

### Book O7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | MEANT pooled s2 thr10 | 223 (44%) | -597/157/278/266 | 5953 / 7469 | 4559 / 5102 | -8996 / -9532 | 52 | 0.18 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s2 thr25 | 212 (42%) | -597/157/278/266 | 5953 / 7469 | 4559 / 5102 | -8996 / -9532 | 52 | 0.14 | 0 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=29696.0 | 164 (32%) | -405/-199/504/308 | 7008 / 7469 | 4921 / 5102 | -6706 / -9532 | 165 | 0.32 | nan | CANDIDATE-DD |
| G_TREE_WF | DDT pooled s1 thr10 | 329 (65%) | -252/-166/-2/209 | 3860 / 7469 | 10237 / 5102 | -4159 / -9532 | 35 | 0.06 | 0 | LEAD |
| G_TREE_WF | DDT pooled s1 thr25 | 329 (65%) | -252/-166/-2/209 | 3860 / 7469 | 10237 / 5102 | -4159 / -9532 | 35 | 0.05 | 0 | LEAD |
| G_TREE_WF | DDT pooled s1 thr0 | 329 (65%) | -252/-166/-2/209 | 3860 / 7469 | 10237 / 5102 | -4159 / -9532 | 35 | 0.02 | 0 | LEAD |

Rows are sorted by the drawdown key (L6M maxDD reduction vs never-cut); the label column is the ledger rule. Means are weekly USD at live lots, carrying week dropped.