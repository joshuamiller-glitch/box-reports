# EXH_G - family G (combinations + learned shapes), EX-LG - FIRST PAGE (learned tree, pooled scope)
Status 04:05Z. Entry match PRE-PROOF. null_ver 2. Learned tree (LightGBM single tree, <=8 leaves, 265 EX-FEAT features + book index, monotone + on pulled-own-side, 3 seeds, purged monthly walk-forward from 202310, thr lattice 0..3200 USD, objectives DD / DDT (tail-loss weighted, DDT = one vote per trade) and MEAN / MEANT). 240 cells (pooled scope) registered as G_TREE_WF/G/loss, agent EX-LG; per-book trees and the pair/vote crosses are running next (addenda in DECISIONS.md). Causality: a fire at second k uses only the feature row k (EX-FEAT noise-after-s0 test passed, their report); labels use the future but only in training rows of months before the test month with a 7-day purge; the kernel only reads F[0,0] and the path up to k+1 (market exit at k+1 is the contract). Live week: month 202611 is a walk-forward test month (trained on earlier months only), so every cell's live delta is out of sample. Honest-null note: the family null is the whole ledger; no G cell is ENTER.

## Headline (04:40Z refresh, universe U1)
- Learned trees (240 pooled cells): none beats never-cut on L6M mean; best drawdown cells cut L6M stack maxDD 117.6k to 67-71k but cost 9-22k/week and raise PRE maxDD: label no. One-vote-per-trade weighting (DDT, MEANT) is less bad. Tree shape unstable across seeds: no shape beyond regime/clock.
- Combinations (G2, 1,014 cells: sticky-AND, OR, 2-of-3 votes of single rules from A,B,C,D; components were picked from the ledger by IN-SAMPLE key, so every combination below is NOT yet walk-forward-proven): OR of two rules lowers stack L6M maxDD from 117.6k to 31-35k with L6M mean about equal to never-cut (some CANDIDATE-DD with positive dmean), per-book K7 maxDD 27.0k to 4.6-5.9k at +450..+2,000 per week. Caveats: PRE maxDD often above never (181-282k vs 178k stack), live-week delta mixed (+4.0k to -16.8k), component picks in-sample. These need the WF picker and the U2 re-score before any claim.
- Next: re-run on U2 (feature months rebuilt), pooled trees WF on U2, pair pool rebuilt from U2 cells, E conditioners on finalists, per-book trees.

Cells registered by EX-LG: 96558 rows (1254 cells).
### Stack (all books), top by L6M maxDD reduction, nfire>=20
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | 12be59c122a0 + 498ceb1dc703 | 13128 | 9218/19040/11766/19068 | 30635 / 117593 | 181783 / 177634 | 139494 / 89449 | -2146 | 0.02 | 4002 | no |
| G_OR | 503ce144003c + 6e114e4ea813 | 10603 | 3190/20309/13504/15545 | 31278 / 117593 | 249878 / 177634 | 110252 / 89449 | -5669 | 0.02 | -13295 | no |
| G_OR | 16fe5f472032 + 498ceb1dc703 | 13093 | 9846/21364/12338/18763 | 31340 / 117593 | 165921 / 177634 | 135746 / 89449 | -2451 | 0.05 | 3967 | no |
| G_VOTE2of3 | d912d0027c26 + 6e114e4ea813 + 5777d1d2c2e6 | 7624 | 6159/22040/12850/29743 | 32319 / 117593 | 101819 / 177634 | 311028 / 89449 | 8530 | 0.02 | -6414 | CANDIDATE-DD |
| G_OR | 503ce144003c + 4373f750fa8d | 12234 | -1285/21418/12236/14333 | 32526 / 117593 | 281664 / 177634 | 63431 / 89449 | -6880 | 0.02 | -13561 | no |
| G_OR | a0e786835d91 + 02b6f4d55147 | 10540 | 3827/29099/18880/21890 | 32689 / 117593 | 174715 / 177634 | 145488 / 89449 | 677 | 0.02 | -13072 | CANDIDATE-DD |
| G_OR | 64300cadcdc1 + 16fe5f472032 | 11649 | 7101/19279/11637/18420 | 32732 / 117593 | 221850 / 177634 | 176941 / 89449 | -2793 | 0.02 | -2162 | no |
| G_OR | a0e786835d91 + 16fe5f472032 | 11639 | -1890/20540/11793/24202 | 33012 / 117593 | 102045 / 177634 | 172308 / 89449 | 2988 | 0.02 | -16805 | CANDIDATE-DD |
| G_OR | a0e786835d91 + 64300cadcdc1 | 6302 | 12872/28390/20234/24028 | 33652 / 117593 | 125311 / 177634 | 244699 / 89449 | 2814 | 0.05 | -15136 | CANDIDATE-DD |
| G_OR | 2170e73cc6ab + b56e188b0e97 | 9925 | 8236/21102/13589/23140 | 34583 / 117593 | 137985 / 177634 | 205617 / 89449 | 1927 | 0.12 | 1302 | CANDIDATE-DD |
| G_VOTE2of3 | d912d0027c26 + 4373f750fa8d + 5777d1d2c2e6 | 9936 | 4734/24437/13435/27473 | 34690 / 117593 | 93551 / 177634 | 275488 / 89449 | 6259 | 0.02 | -6809 | CANDIDATE-DD |
| G_VOTE2of3 | d912d0027c26 + 02b6f4d55147 + 12be59c122a0 | 9850 | 6432/24511/14723/25647 | 34728 / 117593 | 108966 / 177634 | 188707 / 89449 | 4434 | 0.03 | 3735 | CANDIDATE-DD |

### Book K7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | cd3f0c8f96d5 + f870dc88b6ba | 3903 | 1827/5786/4740/3312 | 4642 / 26983 | 31463 / 30403 | 26969 / -15009 | 780 | 0.02 | 4101 | CANDIDATE-DD |
| G_OR | 55462e9fab3f + cd3f0c8f96d5 | 4209 | 1971/4950/4293/2981 | 5160 / 26983 | 21469 / 30403 | 18128 / -15009 | 449 | 0.05 | 3225 | CANDIDATE-DD |
| G_AND | 145ef7bf3f99 + cd3f0c8f96d5 | 3439 | 6948/8830/6505/4794 | 5501 / 26983 | 24135 / 30403 | 44481 / -15009 | 2076 | 0.02 | 2830 | CANDIDATE-DD |
| G_OR | a0e786835d91 + cd3f0c8f96d5 | 3853 | 1875/5169/4356/3110 | 5569 / 26983 | 32484 / 30403 | 22239 / -15009 | 578 | 0.05 | 4150 | LEAD |
| G_OR | cd3f0c8f96d5 + b56e188b0e97 | 4125 | 2969/5012/4477/2973 | 5870 / 26983 | 27090 / 30403 | 18162 / -15009 | 442 | 0.09 | 4101 | CANDIDATE-DD |
| G_OR | cd3f0c8f96d5 + ec3dfcf9714e | 4696 | 1810/5709/4109/3116 | 6079 / 26983 | 29796 / 30403 | 23574 / -15009 | 585 | 0.09 | 2973 | CANDIDATE-DD |

### Book P7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_VOTE2of3 | d912d0027c26 + 6e114e4ea813 + 5777d1d2c2e6 | 2356 | 1174/13043/9839/20245 | 18527 / 126710 | 131193 / 131881 | 185878 / -2075 | 7129 | 0.02 | -8533 | CANDIDATE-DD |
| G_OR | 503ce144003c + 64300cadcdc1 | 2885 | 3829/14736/13120/11676 | 20967 / 126710 | 248336 / 131881 | 84640 / -2075 | -1439 | 0.02 | -17807 | no |
| G_OR | d912d0027c26 + 6e114e4ea813 | 2682 | 1933/13014/10869/11921 | 21576 / 126710 | 138577 / 131881 | 90593 / -2075 | -1194 | 0.02 | -8932 | no |
| G_OR | a0e786835d91 + 64300cadcdc1 | 2295 | 9264/20539/17531/16844 | 21911 / 126710 | 148676 / 131881 | 172821 / -2075 | 3729 | 0.02 | -17922 | no |
| G_OR | 9239ba384da3 + 64300cadcdc1 | 2873 | 5650/13082/10439/12031 | 23582 / 126710 | 197444 / 131881 | 91466 / -2075 | -1084 | 0.02 | -17424 | no |
| G_VOTE2of3 | a0e786835d91 + 6e114e4ea813 + 5777d1d2c2e6 | 2079 | 12695/16276/12996/21558 | 24961 / 126710 | 125458 / 131881 | 228881 / -2075 | 8443 | 0.02 | -3833 | CANDIDATE-DD |

### Book M7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | 4fdbf5914108 + 6338e2bffd23 | 2604 | 1111/572/17/622 | 10224 / 43318 | 52893 / 48984 | -25367 / -68462 | 1125 | 0.03 | 0 | LEAD |
| G_OR | 4fdbf5914108 + 10c66fe5e3fc | 2772 | 142/240/592/387 | 11233 / 43318 | 74934 / 48984 | -24053 / -68462 | 889 | 0.02 | 0 | no |
| G_OR | 55462e9fab3f + 4fdbf5914108 | 2450 | 1704/2353/1203/1125 | 11294 / 43318 | 46919 / 48984 | -12322 / -68462 | 1627 | 0.02 | 0 | CANDIDATE-DD |
| G_AND | 55462e9fab3f + 2b9033788833 | 1174 | 2999/4964/3262/1430 | 12445 / 43318 | 32446 / 48984 | -13274 / -68462 | 1829 | 0.02 | 0 | CANDIDATE-DD |
| G_AND | 55462e9fab3f + 58d107d28ac7 | 1034 | 2735/4205/2579/1416 | 12525 / 43318 | 35787 / 48984 | -15455 / -68462 | 1815 | 0.02 | 0 | CANDIDATE-DD |
| G_AND | 145ef7bf3f99 + 4fdbf5914108 | 2065 | -698/2364/977/562 | 13115 / 43318 | 42344 / 48984 | -20380 / -68462 | 1064 | 0.06 | 0 | CANDIDATE-DD |

### Book U7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | 3d852783ada6 + 10c66fe5e3fc | 842 | -1177/1788/844/3383 | 6204 / 21436 | 41216 / 42883 | 10054 / 45 | 650 | 0.06 | 0 | CANDIDATE-DD |
| G_OR | 10c66fe5e3fc + ec3dfcf9714e | 888 | -1255/1879/1184/2822 | 6218 / 21436 | 40702 / 42883 | -4215 / 45 | -1106 | 0.03 | 0 | no |
| G_AND | b624d0feccc8 + 0793cbf88119 | 771 | -391/2480/1590/3420 | 6714 / 21436 | 25387 / 42883 | 17364 / 45 | 682 | 0.02 | 0 | CANDIDATE-DD |
| G_AND | 145ef7bf3f99 + 10c66fe5e3fc | 683 | -932/2397/1594/3938 | 6838 / 21436 | 36040 / 42883 | 26405 / 45 | 1206 | 0.03 | 0 | CANDIDATE-DD |
| G_AND | 503ce144003c + 5777d1d2c2e6 | 582 | -702/2087/1410/3962 | 6882 / 21436 | 51642 / 42883 | 18589 / 45 | 33 | 0.02 | 0 | no |
| G_AND | 10c66fe5e3fc + 5777d1d2c2e6 | 618 | 1502/1153/774/4120 | 7300 / 21436 | 54291 / 42883 | 23593 / 45 | 1387 | 0.02 | 0 | LEAD |

### Book A7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | 0a1fc0de5c4b + 5777d1d2c2e6 | 764 | -269/701/269/955 | 3605 / 12456 | 7097 / 6208 | -6762 / -17012 | 360 | 0.02 | 634 | LEAD |
| G_OR | 3d852783ada6 + 6338e2bffd23 | 889 | 319/-128/-140/263 | 3769 / 12456 | 5794 / 6208 | -8850 / -17012 | -225 | 0.03 | 667 | no |
| G_VOTE2of3 | 0a1fc0de5c4b + 12be59c122a0 + 5777d1d2c2e6 | 707 | 313/931/409/1131 | 3893 / 12456 | 6715 / 6208 | -6917 / -17012 | 535 | 0.02 | 392 | LEAD |
| G_OR | 0a1fc0de5c4b + 0518f606288d | 706 | 461/1093/752/1019 | 4010 / 12456 | 8431 / 6208 | -2875 / -17012 | 423 | 0.03 | 634 | LEAD |
| G_OR | 503ce144003c + 64300cadcdc1 | 574 | -543/707/387/830 | 4410 / 12456 | 5886 / 6208 | -10266 / -17012 | 234 | 0.05 | 529 | CANDIDATE-DD |
| G_OR | 503ce144003c + 6e114e4ea813 | 574 | -543/707/387/830 | 4410 / 12456 | 5886 / 6208 | -10266 / -17012 | 234 | 0.06 | 529 | CANDIDATE-DD |

### Book H7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | a0e786835d91 + 2170e73cc6ab | 362 | 808/3423/1538/1768 | 4733 / 16682 | 13517 / 20667 | -267 / -36140 | 1025 | 0.02 | 0 | CANDIDATE-DD |
| G_OR | 8ecdebd93f80 + 2170e73cc6ab | 379 | 1822/1345/1431/2054 | 4769 / 16682 | 13517 / 20667 | 11605 / -36140 | 1311 | 0.02 | 0 | CANDIDATE-DD |
| G_OR | 4373f750fa8d + 6360a3110ed7 | 654 | 1759/3320/1134/1455 | 5014 / 16682 | 17116 / 20667 | -574 / -36140 | 712 | 0.02 | 0 | CANDIDATE-DD |
| G_OR | 2170e73cc6ab + 6360a3110ed7 | 630 | 1414/1392/1042/1422 | 5096 / 16682 | 15625 / 20667 | -1874 / -36140 | 679 | 0.02 | 0 | CANDIDATE-DD |
| G_OR | a44a782bd01b + 10c66fe5e3fc | 667 | 1674/1204/288/1773 | 5779 / 16682 | 13943 / 20667 | 6218 / -36140 | 1029 | 0.02 | 0 | CANDIDATE-DD |
| G_OR | cd3f0c8f96d5 + 6360a3110ed7 | 676 | -79/1457/200/908 | 5784 / 16682 | 17150 / 20667 | -9256 / -36140 | 165 | 0.02 | 0 | CANDIDATE-DD |

### Book O7 (all sessions)
| tech | params |  nfire | L1M/L2M/L3M/L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | worst20 L6M w/wo | L6M dmean | placebo p | live dUSD | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | a44a782bd01b + 5b506a3e02bd | 453 | -46/193/208/299 | 2175 / 7489 | 9188 / 5097 | -3011 / -9447 | 122 | 0.03 | 0 | LEAD |
| G_OR | b624d0feccc8 + fbb626f02da6 | 457 | -361/-91/2/246 | 2700 / 7489 | 14462 / 5097 | -3240 / -9447 | 70 | 0.11 | 0 | LEAD |
| G_OR | 5b506a3e02bd + 58d107d28ac7 | 455 | 151/269/222/309 | 2878 / 7489 | 12021 / 5097 | -2609 / -9447 | 133 | 0.09 | 0 | LEAD |
| G_OR | 9239ba384da3 + 5b506a3e02bd | 454 | 95/263/208/247 | 2930 / 7489 | 12609 / 5097 | -3917 / -9447 | 70 | 0.12 | 0 | LEAD |
| G_OR | a44a782bd01b + fbb626f02da6 | 451 | -474/-105/34/227 | 3028 / 7489 | 6265 / 5097 | -4205 / -9447 | 51 | 0.09 | 0 | LEAD |
| G_OR | 4373f750fa8d + fbb626f02da6 | 454 | -583/-158/-47/197 | 3060 / 7489 | 8286 / 5097 | -5097 / -9447 | 20 | 0.08 | 0 | LEAD |

Rows are sorted by the drawdown key (L6M maxDD reduction vs never-cut); the label column is the ledger rule. Means are weekly USD at live lots, carrying week dropped.