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

## FINAL SECTION (EX-LG, written 09:30Z; U2; drawdown-first; walk-forward cells only; entry match PRE-PROOF)
Honest cells = the pairing procedures run INSIDE the purged walk-forward (G_PAIRWF: top-3 singles per family from A,B_book,C_flow,D, now 12,845 singles on U2 incl. 525 B and 403 C, all cross pairs AND/OR + singles; G_CONDWF: 5 best singles x 36 EX-LDEF contexts; each in per-book and one-rule-for-all mode, chosen on the trailing 26 weeks, 7-day embargo, applied the next month; first test month 202310). Learned trees (pooled and per book) all lose out of sample (see headline). Candidate counts per cell are in the cell params (candidates_examined). Columns: L6M maxDD with/without (weekly, live lots, stack of that book), L6M mean change per week, PRE maxDD with/without, share of the book's trades exited early, live-week delta vs the universe never-cut bracket of the live-week entries (the walk-forward month 202611, trained on earlier months only; this is not the actual live exit, so treat as indicative).

| scope | best WF cell by L6M maxDD | L6M maxDD w/wo | L6M dmean /wk | PRE maxDD w/wo | exited early | label |
|---|---|---|---|---|---|---|
| Stack | PAIRWF one-rule-for-all | 77.8k / 121.4k | -4.7k | 93.2k / 152.5k | 44% | no (costs mean; live week -146k) |
| K7 | none lowers L6M maxDD (best CONDWF_ALL 23.2k vs 20.9k) | - | +350 | - | 35% | no |
| P7 | PAIRWF one-rule-for-all | 92.6k / 133.9k | -4.3k | 145.6k / 109.4k | 44% | no (PRE worse, mean lost, live -120k) |
| M7 | PAIRWF one-rule-for-all | 25.1k / 44.4k | +252 | 52.3k / 50.3k | 45% | CANDIDATE-DD but FAILS-LIVE-WEEK (-11.7k) |
| U7 | CONDWF per-book | 18.6k / 21.6k | +323 | 34.3k / 42.2k | 48% | CANDIDATE-DD but FAILS-LIVE-WEEK (-7.2k) |
| A7 | CONDWF one-rule-for-all | 8.8k / 12.5k | +228 | 5.5k / 6.1k | 38% | CANDIDATE-DD but FAILS-LIVE-WEEK (-8.7k) |
| H7 | none (PAIRWF_ALL 18.2k vs 15.5k) | - | +361 | - | 45% | no |
| O7 | none (PAIRWF_ALL 7.1k vs 7.5k, PRE 5.5k vs 5.1k) | - | +21 | - | 33% | no |

Plain sentences (loss side).
- K7 loss: no walk-forward technique of family G lowers drawdown; the learned tree and the pair/conditioned rules all fail; keep the live line. It does not hold out of sample because the pair chosen on trailing weeks does not repeat next month.
- P7 loss: the technique that lowers drawdown most is the one-rule-for-all pair (L6M maxDD 133.9k to 92.6k); it costs 4.3k per week, raises PRE maxDD (109k to 146k), cuts 44% of trades and loses 120k in the live week: no.
- M7 loss: the one-rule-for-all pair lowers L6M maxDD 44.4k to 25.1k at +252 per week and PRE within 4%, but it exits 45% of trades (an exposure shrink) and fails the live week (-11.7k): CANDIDATE-DD, not ENTER.
- U7 loss: the per-book conditioned rule lowers L6M maxDD 21.6k to 18.6k and PRE 42.2k to 34.3k at +323 per week, but exits 48% of trades and fails the live week (-7.2k): CANDIDATE-DD, not ENTER.
- A7 loss: the conditioned one-rule-for-all rule lowers L6M maxDD 12.5k to 8.8k and PRE 6.1k to 5.5k at +228 per week, exits 38% of trades, fails the live week (-8.7k): CANDIDATE-DD, not ENTER.
- H7 and O7 loss: no walk-forward cell lowers L6M maxDD at non-negative mean; no.
- Stack: the one-rule-for-all pair lowers L6M maxDD 121.4k to 77.8k and PRE 152.5k to 93.2k but gives up 4.7k per week and the live-week delta is -146k (P7 dominates); drawdown is bought with exposure, not with timing information. Per-book beats one-rule-for-all on the stack only for the conditioned variant (72.0k vs 82.7k L6M).
- Survivor rule (CANDIDATE-DD and rec-ok and plc-ok and not FAILS-LIVE-WEEK): no G cell survives.
Grammar fields v1.6 would need to express any G cell: none recommended (no survivor). Conclusion for the order: the richer feature set and the 8-leaf learned shapes found nothing beyond regime/clock out of sample; pairs and conditioners reduce drawdown only by exiting 35-60% of trades early.
# EXH_G - family G (combinations + learned shapes), EX-LG
generated 11-09 09:21 UTC; entry match PRE-PROOF; null_ver 2; family p not yet attached (label computed with p_family=1, WF=False, so ENTER is impossible here; CANDIDATE-DD/LEAD are the live labels).

Cells registered by EX-LG: 107338 rows (1394 cells).
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
| G_PAIRWF_ALL | WF ALL cand=34613.0 | 1720 (45%) | -481/1742/-254/-240 | 25130 / 44425 | 52257 / 50321 | -44879 / -68299 | 252 | 0.58 | nan | CANDIDATE-DD |
| G_CONDWF_BOOK | WF BOOK cand=60800.0 | 1532 (40%) | 117/1213/1039/187 | 26034 / 44425 | 32668 / 50321 | -45974 / -68299 | 728 | 0.05 | nan | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr800 | 463 (12%) | -1878/136/-1259/-140 | 28901 / 44425 | 37524 / 50321 | -54341 / -68299 | 352 | 0.18 | 0 | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s0 thr800 | 469 (12%) | -666/-48/-1381/69 | 30499 / 44425 | 39905 / 50321 | -55553 / -68299 | 275 | 0.12 | 0 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=34410.0 | 1729 (46%) | -481/1742/-254/-468 | 30828 / 44425 | 46658 / 50321 | -47381 / -68299 | 24 | 0.60 | nan | CANDIDATE-DD |
| G_TREE_WF | DDT perbook s1 thr200 | 737 (19%) | -2956/-324/-1627/-192 | 31162 / 44425 | 27331 / 50321 | -61560 / -68299 | 300 | 0.65 | 0 | CANDIDATE-DD |

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
| G_CONDWF_ALL | WF ALL cand=60800.0 | 442 (38%) | -1236/382/190/829 | 8801 / 12461 | 5508 / 6089 | -12927 / -17069 | 228 | 0.95 | nan | CANDIDATE-DD |
| G_PAIRWF_BOOK | WF BOOK cand=12821.0 | 694 (59%) | -1638/151/234/952 | 10097 / 12461 | 6393 / 6089 | -14619 / -17069 | 352 | 0.69 | nan | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr0 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.94 | 616 | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr25 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.91 | 616 | CANDIDATE-DD |
| G_TREE_WF | MEANT pooled s0 thr10 | 351 (30%) | -1528/357/23/798 | 10331 / 12461 | 5043 / 6089 | -18788 / -17069 | 197 | 0.89 | 616 | CANDIDATE-DD |
| G_PAIRWF_ALL | WF ALL cand=30973.0 | 496 (42%) | -1494/132/-241/755 | 10740 / 12461 | 4291 / 6089 | -18468 / -17069 | 154 | 0.29 | nan | CANDIDATE-DD |

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