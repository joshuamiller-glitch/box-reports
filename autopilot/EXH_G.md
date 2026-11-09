# EXH_G - family G (combinations + learned shapes), EX-LG - refresh 05:10Z
Entry match PRE-PROOF. null_ver 2. Tables below are universe U2 (cells with universe_ver U2; the U1 screen cells stay in the ledger). Method files: code/th_exh_g (g_data, g_wf, g_score, g_combo, g_pairwf, g_page); pre-registrations and addenda 1-3 in DECISIONS.md.

## Headline
- Learned trees (LightGBM single tree, <=8 leaves, 265 features, 3 seeds, purged monthly WF from 202310, thr lattice 0..3200 USD; DDT/MEANT = one vote per trade; U2 rerun 60 cells, U1 had 240): none beats never-cut on L6M mean; the drawdown-lowering cells (stack L6M maxDD 121k to 68k) cost 11-18k/week and fire on 40-60% of trades (exposure shrink); the live week is mixed. Seeds disagree: no shape beyond regime/clock. Label no.
- In-sample pair/vote combinations (G_AND/G_OR/G_VOTE2of3, built on U1 from top single rules; components picked from thousands of cells, so selection multiplicity is huge): headline maxDD cuts (117.6k to 31-35k stack; K7 27.0k to 4.6k) are NOT evidence; many fire on 33-61% of trades (OR of two cutters is an exposure shrink where share>~35%) and live-week deltas are mixed (+4.0k to -16.8k). They are screen-only. Family-null accounting for them: 1,014 cells examined, drawn from a pool of 5,625 single rules.
- Pairing INSIDE the purged walk-forward (G_PAIRWF; per test month, components and pair chosen on the trailing 26 weeks ending 7 days before the month, top 3 per family, all cross pairs AND/OR plus singles, selected by train maxDD subject to train delta >= 0): honest estimate. U1 (families A,B,C,D): per-book picks L6M stack maxDD 121.4k to 79.3k, PRE 152.5k to 115.3k, L6M mean delta -3.4k/week, share of trades exited early 41%; one-rule-for-all picks L6M 94.9k, PRE 118.1k, L6M mean delta +2.2k/week, share 37%. U2 (only A and D, B/C not yet on U2): per-book L6M 112.0k vs 121.4k (delta -1.3k/week), ALL L6M 97.9k vs 121.4k (delta -3.4k/week), PRE 112.9k / 114.8k vs 152.5k, share 48% / 40%. So walk-forward shrinks the in-sample 70% maxDD cut to 10-35%, partly by cutting a large share of trades; the L6M mean is not kept on U2. Candidates only if the page rules (rec-ok, placebo, live week) pass: see ledger labels.
- E conditioners inside the walk-forward (G_CONDWF, U2; per scope the 5 best singles on trailing 26 weeks x 36 EX-LDEF context levels + unconditioned, best by train maxDD): per-book L6M maxDD 121.4k to 100.2k, PRE 152.5k to 133.3k, L6M mean delta -2.7k/week, 41% of trades exited early; one-rule-for-all L6M 127.7k (worse than never-cut), PRE 153.0k, delta -6.2k/week. Conditioners do not rescue the single rules out of sample.
- Per-book learned trees (U2, DDT and MEANT, 3 seeds x 10 thresholds = 60 cells): same pattern as pooled; 48 of 60 lose in L6M mean; the drawdown cuts (L6M 121k to 75-78k) cost 7-10k/week and raise PRE maxDD to 240-278k. One cell (nfire 1,210, L6M maxDD 78.5k vs 121.4k, PRE 116.9k vs 152.5k, L6M mean +216/week) is the single exception among 60 and is not distinguishable from the family max-stat; it is a LEAD at best.
- kernel_leak_test on the shared exit kernel (trees, pairs, votes, conditioned cells): 4789 legs checked, 0 changed: pass. Components' own causality is their owners' duty.
- Queue running (nohup, every 30 min poll / 2 h page refresh until 13:30Z): per-book trees DDT then MEANT (no new tree experiment after 10:00Z), pair walk-forward re-run whenever the U2 loss-cell set grows.

- Not done yet (handoff): pair pool and WF on U2 once B/C are re-scored on U2; E conditioners on finalists; per-book learned trees (ran one test month then stopped for the 2-process budget; code supports g_wf.py OBJ SEEDS B); Stage 2 for finalists (none qualifies); causality: fire at second k reads only the feature row k (EX-FEAT noise test), training labels use the future only inside earlier months with 7-day purge; kernel_leak_test not yet run on the G kernel (it only reads F[0,0] and calls market_exit; its br_k guard duplicates the contract).

Cells registered by EX-LG: 101486 rows (1318 cells).
# EXH_G - family G (combinations + learned shapes), EX-LG
generated 11-09 07:18 UTC; entry match PRE-PROOF; null_ver 2; family p not yet attached (label computed with p_family=1, WF=False, so ENTER is impossible here; CANDIDATE-DD/LEAD are the live labels).

Cells registered by EX-LG: 107030 rows (1390 cells).
### Stack (all books), top by L6M maxDD reduction, nfire>=20
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_PAIRWF_ALL | WF ALL cand=29747.0 | 7875 (41%) | -3269/18781/6699/21260 | 70942 / 121381 | 89728 / 152455 | 100359 / 77580 | 508 | 0.03 | nan | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr1600 | 1210 (6%) | 25648/24732/12371/20968 | 78529 / 121381 | 116921 / 152455 | 118289 / 77580 | 216 | 0.08 | -10384 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s2 thr1600 | 1227 (6%) | 25780/23709/12527/21587 | 82105 / 121381 | 123270 / 152455 | 136712 / 77580 | 834 | 0.48 | -9772 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr50 | 3299 (17%) | 32336/30258/14438/27930 | 85457 / 121381 | 120710 / 152455 | 109041 / 77580 | 1535 | 0.37 | 0 | CANDIDATE-DD |
| G_PAIRWF_BOOK | WF BOOK cand=29747.0 | 9490 (50%) | -5160/22944/12126/21590 | 86634 / 121381 | 104285 / 152455 | 98385 / 77580 | 837 | 0.03 | nan | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr0 | 6701 (35%) | 31178/29038/14681/27463 | 88648 / 121381 | 127908 / 152455 | 122892 / 77580 | 1067 | 0.85 | 2123 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr10 | 5937 (31%) | 31178/29038/14681/27467 | 88648 / 121381 | 127908 / 152455 | 120450 / 77580 | 1072 | 0.82 | 2123 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr25 | 5291 (28%) | 30961/29272/14837/27544 | 88648 / 121381 | 127908 / 152455 | 123178 / 77580 | 1148 | 0.82 | 483 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=29696.0 | 7057 (37%) | 18844/23679/9862/22914 | 94881 / 121381 | 118120 / 152455 | 165849 / 77580 | 2162 | 0.12 | nan | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr3200 | 320 (2%) | 30230/36582/18152/25557 | 112731 / 121381 | 142959 / 152455 | 133565 / 77580 | 4805 | 0.97 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s2 thr3200 | 236 (1%) | 49360/69337/39807/32771 | 116249 / 121381 | 152455 / 152455 | 113161 / 77580 | 444 | 1.00 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT pooled s1 thr200 | 12987 (68%) | -13742/2845/858/2418 | 67672 / 121381 | 306129 / 152455 | -128915 / 77580 | -18334 | 0.03 | -12625 | no |

### Book K7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | MEANT perbook s1 thr0 | 1557 (24%) | 7514/7578/3577/4412 | 19468 / 20902 | 23367 / 26707 | 25820 / 1791 | 1030 | 0.29 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s1 thr10 | 1018 (16%) | 7514/8493/3760/4500 | 20902 / 20902 | 23367 / 26707 | 20761 / 1791 | 1118 | 1.00 | 0 | LEAD |
| G_TREE_WF | MEANT perbook s2 thr10 | 880 (14%) | 7921/8697/3896/4503 | 20902 / 20902 | 39348 / 26707 | 19205 / 1791 | 1120 | 1.00 | 1737 | LEAD |
| G_TREE_WF | MEANT perbook s2 thr0 | 1387 (21%) | 7921/8697/3896/4503 | 20902 / 20902 | 39348 / 26707 | 19205 / 1791 | 1120 | 1.00 | 1737 | LEAD |
| G_TREE_WF | MEANT pooled s1 thr100 | 187 (3%) | 7702/9464/4408/4811 | 20902 / 20902 | 26707 / 26707 | 20426 / 1791 | 278 | 1.00 | 1363 | LEAD |
| G_TREE_WF | DDT pooled s0 thr100 | 1595 (25%) | 1971/5393/2893/2085 | 12573 / 20902 | 38861 / 26707 | -18552 / 1791 | -1297 | 0.08 | 0 | no |

### Book P7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | MEANT perbook s0 thr50 | 1756 (37%) | 29528/19713/12767/16636 | 69573 / 133887 | 95640 / 109442 | 17739 / -29902 | 631 | 0.05 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr0 | 1824 (38%) | 29528/19713/12767/16636 | 69573 / 133887 | 95640 / 109442 | 17739 / -29902 | 631 | 0.02 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr10 | 1824 (38%) | 29528/19713/12767/16636 | 69573 / 133887 | 95640 / 109442 | 17739 / -29902 | 631 | 0.05 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr100 | 1645 (35%) | 29528/19713/12767/16636 | 69573 / 133887 | 95640 / 109442 | 17739 / -29902 | 631 | 0.03 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr25 | 1824 (38%) | 29528/19713/12767/16636 | 69573 / 133887 | 95640 / 109442 | 17739 / -29902 | 631 | 0.02 | 0 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=29747.0 | 1913 (40%) | -3764/9042/5765/13069 | 71321 / 133887 | 91356 / 109442 | 39094 / -29902 | 1175 | 0.02 | nan | CANDIDATE-DD |

### Book M7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_CONDWF_BOOK | WF BOOK cand=60800.0 | 1532 (40%) | 117/1213/1039/187 | 26034 / 44425 | 32668 / 50321 | -45974 / -68299 | 728 | 0.05 | nan | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr800 | 463 (12%) | -1878/136/-1259/-140 | 28901 / 44425 | 37524 / 50321 | -54341 / -68299 | 352 | 0.18 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s0 thr800 | 469 (12%) | -666/-48/-1381/69 | 30499 / 44425 | 39905 / 50321 | -55553 / -68299 | 275 | 0.12 | 0 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=34410.0 | 1729 (46%) | -481/1742/-254/-468 | 30828 / 44425 | 46658 / 50321 | -47381 / -68299 | 24 | 0.60 | nan | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr200 | 737 (19%) | -2956/-324/-1627/-192 | 31162 / 44425 | 27331 / 50321 | -61560 / -68299 | 300 | 0.65 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr100 | 1710 (45%) | -2956/-324/-1627/-192 | 31162 / 44425 | 48304 / 50321 | -61560 / -68299 | 300 | 0.60 | 0 | CANDIDATE-DD |

### Book U7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | MEANT perbook s0 thr50 | 331 (24%) | -2617/2441/2372/4567 | 14872 / 21561 | 43646 / 42226 | 26129 / 120 | 828 | 0.09 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s0 thr25 | 333 (24%) | -2617/2441/2372/4567 | 14872 / 21561 | 43687 / 42226 | 26129 / 120 | 828 | 0.11 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s2 thr10 | 329 (24%) | -3204/1576/743/3395 | 16951 / 21561 | 33784 / 42226 | -10172 / 120 | 223 | 0.17 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s2 thr0 | 329 (24%) | -3204/1576/743/3395 | 16951 / 21561 | 33784 / 42226 | -10172 / 120 | 223 | 0.20 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s2 thr25 | 329 (24%) | -3204/1576/743/3395 | 16951 / 21561 | 33784 / 42226 | -10172 / 120 | 223 | 0.20 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s2 thr50 | 319 (23%) | -3204/1576/743/3395 | 16951 / 21561 | 33599 / 42226 | -10172 / 120 | 223 | 0.20 | 0 | CANDIDATE-DD |

### Book A7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_PAIRWF_BOOK | WF BOOK cand=12821.0 | 694 (59%) | -1638/151/234/952 | 10097 / 12461 | 6393 / 6089 | -14619 / -17069 | 352 | 0.69 | nan | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr0 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.94 | 616 | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr25 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.91 | 616 | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr10 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.89 | 616 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=30973.0 | 496 (42%) | -1494/132/-241/755 | 10740 / 12461 | 4291 / 6089 | -18468 / -17069 | 154 | 0.29 | nan | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=34410.0 | 530 (45%) | -1494/-144/-260/749 | 10740 / 12461 | 4521 / 6089 | -15736 / -17069 | 148 | 1.00 | nan | CANDIDATE-DD |

### Book H7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | DDT perbook s2 thr100 | 125 (11%) | 1632/1860/78/1589 | 12600 / 15477 | 10473 / 20667 | -16128 / -32750 | 468 | 0.08 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s2 thr200 | 109 (10%) | 831/1459/-190/1460 | 12600 / 15477 | 10473 / 20667 | -19334 / -32750 | 340 | 0.08 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s2 thr1600 | 71 (6%) | -88/694/-738/1586 | 13209 / 15477 | 15956 / 20667 | -24827 / -32750 | 465 | 0.06 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr200 | 108 (10%) | 831/1154/-436/1491 | 13209 / 15477 | 12326 / 20667 | -16102 / -32750 | 323 | 0.14 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr400 | 108 (10%) | 831/1154/-436/1491 | 13209 / 15477 | 12326 / 20667 | -16102 / -32750 | 323 | 0.08 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s2 thr400 | 91 (8%) | 831/1154/-436/1342 | 13209 / 15477 | 10543 / 20667 | -18988 / -32750 | 221 | 0.12 | 0 | CANDIDATE-DD |

### Book O7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_TREE_WF | DDT perbook s1 thr10 | 144 (28%) | -293/99/172/182 | 4518 / 7469 | 5102 / 5102 | -6765 / -9532 | 8 | 0.03 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr50 | 139 (27%) | -284/104/175/183 | 4518 / 7469 | 5102 / 5102 | -6728 / -9532 | 10 | 0.02 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr0 | 144 (28%) | -293/99/172/182 | 4518 / 7469 | 5102 / 5102 | -6765 / -9532 | 8 | 0.03 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr25 | 142 (28%) | -293/99/172/182 | 4518 / 7469 | 5102 / 5102 | -6765 / -9532 | 8 | 0.02 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s1 thr25 | 69 (14%) | -840/-314/-76/204 | 5714 / 7469 | 5102 / 5102 | -6554 / -9532 | 27 | 0.02 | 0 | CANDIDATE-DD |
| G_TREE_WF | MEANT perbook s1 thr50 | 69 (14%) | -840/-314/-76/204 | 5714 / 7469 | 5102 / 5102 | -6554 / -9532 | 27 | 0.02 | 0 | CANDIDATE-DD |

Rows are sorted by the drawdown key (L6M maxDD reduction vs never-cut); the label column is the ledger rule. Means are weekly USD at live lots, carrying week dropped.