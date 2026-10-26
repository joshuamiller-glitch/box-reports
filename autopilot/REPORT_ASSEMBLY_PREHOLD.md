# REPORT ASSEMBLY - PRE-HOLDOUT TEXT (WF-PRE 2024-02..2025-06 and IS 2023-02..2024-01 only; NO holdout, NO full-WF, NO L8W number computed or printed)

Prereg l2vast/struct48/prereg/ASSEMBLY.md sha256 24c918d0bb3e49d554af6308ee11217dc413688d736d074f7e6786b4a804ff99 (15 cells). Engine asm_lib (ds2lib lock engine, 3 books, per-group R). Benchmark: Set A on the same engine.

Reproduction (WF-PRE, same engine): Set A 17,558/wk (BK1 riskeng: 17,547), Set B 27,557/wk (BK1: 27,539).

## WF-PRE (75 weeks): mean / SD / maxDD(daily path) / worst week / trades per wk, and d vs Set A (mean, SD, maxDD) with 8-wk block CI (10k) and iid CI

| cell | mean | SD | maxDD | worst | tr/wk | d mean | d SD | d maxDD | block CI d mean | iid CI | MDE(block) | placebo rank maxDD / mean | 2x d mean | verdict (pre, provisional) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ASM_10_10_7_PB | 23,675 | 99,161 | 537,851 | -199,368 | 79.6 | 6,117 | 1,627 | 136,533 | [-2,909, 14,856] | [-8,464, 21,172] | 12,815 | 0.020 / 0.002 | -7,546 | DEAD |
| ASM_S141010_7_PB | 27,073 | 116,697 | 465,699 | -202,621 | 86.5 | 9,514 | 19,164 | 64,381 | [-3,543, 22,759] | [-6,872, 26,547] | 18,827 | 0.288 / 0.006 | -5,627 | DEAD |
| ASM_10_10_7_PB_wkcomb | 19,858 | 102,279 | 527,067 | -144,889 | 74.3 | 2,299 | 4,745 | 125,749 | [-6,946, 11,332] | [-11,401, 16,400] | 13,173 | - | -11,110 | DEAD |
| ASM_10_10_7_PB_WTnocorr | 25,834 | 98,582 | 522,433 | -190,774 | 75.9 | 8,276 | 1,049 | 121,115 | [-947, 17,294] | [-6,091, 22,762] | 13,140 | - | -5,388 | DEAD |
| ASM_10_10_7_COMBGB | 23,020 | 80,341 | 259,166 | -143,004 | 56.8 | 5,462 | -17,193 | -142,152 | [-6,626, 17,609] | [-7,974, 19,887] | 17,413 | - | -1,442 | DEAD |
| PAIR_10_10_PB | 21,665 | 88,316 | 362,271 | -167,778 | 44.7 | 4,107 | -9,218 | -39,047 | [-5,006, 12,162] | [-11,415, 19,502] | 12,200 | - | -4,589 | DEAD |
| PAIR_8_8_PB | 17,332 | 70,653 | 289,817 | -134,222 | 44.7 | -226 | -26,881 | -111,501 | [-8,805, 7,363] | [-15,281, 14,676] | 11,583 | - | -8,887 | DEAD |
| PAIR_12_12_PB | 25,998 | 105,979 | 434,725 | -201,333 | 44.7 | 8,440 | 8,446 | 33,407 | [-1,940, 17,955] | [-8,391, 25,204] | 14,202 | - | -221 | DEAD |
| PAIR_10_10_COMBGB | 22,423 | 70,926 | 232,109 | -150,963 | 35.8 | 4,864 | -26,607 | -169,210 | [-2,816, 13,547] | [-4,410, 15,472] | 11,758 | - | 1,113 | DEAD |
| ASM_8_8_7_PB | 19,342 | 82,270 | 468,422 | -165,813 | 79.6 | 1,784 | -15,264 | 67,103 | [-5,897, 9,282] | [-12,140, 15,830] | 10,898 | - | -12,471 | DEAD |
| ASM_12_12_7_PB | 28,008 | 116,282 | 607,281 | -232,924 | 79.6 | 10,450 | 18,748 | 205,962 | [-650, 21,290] | [-5,878, 27,358] | 15,744 | - | -3,805 | DEAD |
| ASM_S14_8_8_7_PB | 23,073 | 105,439 | 535,610 | -184,720 | 88.6 | 5,515 | 7,906 | 134,292 | [-7,129, 17,909] | [-9,131, 20,416] | 18,018 | - | -10,176 | DEAD |
| ASM_S14_12_12_7_PB | 28,374 | 127,415 | 528,350 | -222,098 | 84.3 | 10,816 | 29,882 | 127,031 | [-1,862, 23,481] | [-7,998, 30,333] | 18,244 | - | -4,191 | DEAD |
| PAIR_8_8_COMBGB | 17,938 | 56,741 | 185,687 | -120,771 | 35.8 | 380 | -40,793 | -215,631 | [-7,920, 9,555] | [-10,653, 12,454] | 12,615 | - | -6,861 | DEAD |
| PAIR_12_12_COMBGB | 26,907 | 85,111 | 278,531 | -181,156 | 35.8 | 9,349 | -12,422 | -122,788 | [1,596, 18,065] | [1,086, 19,113] | 11,781 | - | 2,108 | DEAD |
| SETB | 27,557 | 96,754 | 320,103 | -152,362 | 41.5 | 9,999 | -779 | -81,216 | [-3,600, 23,352] | [-873, 21,416] | 19,274 | - | 74 | DEAD |
| INFO_WT7_alone | 2,010 | 27,380 | 244,807 | -60,743 | 34.9 | -15,548 | -70,154 | -156,511 | [-28,355, -3,098] | [-35,088, 4,603] | 17,857 | - | -22,652 | DEAD |

## IS (52 weeks) mean / SD / maxDD (daily path), own series, by cell

| cell | IS mean | IS SD | IS maxDD | IS tr/wk |
|---|---|---|---|---|
| ASM_10_10_7_PB | 7,276 | 91,532 | 575,785 | 57.6 |
| ASM_S141010_7_PB | 8,834 | 101,597 | 580,187 | 62.8 |
| ASM_10_10_7_PB_wkcomb | 7,240 | 89,861 | 473,275 | 56.6 |
| ASM_10_10_7_PB_WTnocorr | 10,307 | 92,460 | 546,433 | 57.6 |
| ASM_10_10_7_COMBGB | 17,817 | 65,300 | 291,466 | 44.9 |
| PAIR_10_10_PB | 5,894 | 72,792 | 459,707 | 32.7 |
| PAIR_8_8_PB | 4,715 | 58,233 | 367,765 | 32.7 |
| PAIR_12_12_PB | 7,073 | 87,350 | 551,648 | 32.7 |
| PAIR_10_10_COMBGB | 13,569 | 64,315 | 209,594 | 28.3 |
| ASM_8_8_7_PB | 6,097 | 77,576 | 483,844 | 57.6 |
| ASM_12_12_7_PB | 8,455 | 105,650 | 667,727 | 57.6 |
| ASM_S14_8_8_7_PB | 6,656 | 95,615 | 546,785 | 63.6 |
| ASM_S14_12_12_7_PB | 8,125 | 109,894 | 712,110 | 61.6 |
| PAIR_8_8_COMBGB | 10,855 | 51,452 | 167,675 | 28.3 |
| PAIR_12_12_COMBGB | 16,283 | 77,178 | 251,513 | 28.3 |
| SETB | 10,287 | 83,559 | 375,875 | 32.6 |
| INFO_WT7_alone | 1,381 | 28,586 | 160,585 | 25.0 |

## Per-book split (WF-PRE, $/wk and trades/wk; book net attributed to the entry row)

| cell | ST | HM | WT |
|---|---|---|---|
| ASM_10_10_7_PB | 12,242 (23.2) | 9,422 (21.4) | 2,010 (34.9) |
| ASM_S141010_7_PB | 14,103 (27.4) | 10,960 (24.2) | 2,010 (34.9) |
| ASM_10_10_7_PB_wkcomb | 10,038 (21.5) | 8,907 (20.1) | 912 (32.7) |
| ASM_10_10_7_PB_WTnocorr | 12,242 (23.2) | 9,422 (21.4) | 4,169 (31.3) |
| ASM_10_10_7_COMBGB | 12,079 (16.3) | 7,056 (14.5) | 3,884 (26.0) |
| PAIR_10_10_PB | 12,242 (23.2) | 9,422 (21.4) | 0 (0.0) |
| PAIR_8_8_PB | 9,794 (23.2) | 7,538 (21.4) | 0 (0.0) |
| PAIR_12_12_PB | 14,691 (23.2) | 11,307 (21.4) | 0 (0.0) |
| PAIR_10_10_COMBGB | 13,562 (18.8) | 8,860 (17.0) | 0 (0.0) |
| ASM_8_8_7_PB | 9,794 (23.2) | 7,538 (21.4) | 2,010 (34.9) |
| ASM_12_12_7_PB | 14,691 (23.2) | 11,307 (21.4) | 2,010 (34.9) |
| ASM_S14_8_8_7_PB | 11,519 (28.6) | 9,544 (25.0) | 2,010 (34.9) |
| ASM_S14_12_12_7_PB | 16,185 (25.8) | 10,179 (23.5) | 2,010 (34.9) |
| PAIR_8_8_COMBGB | 10,850 (18.8) | 7,088 (17.0) | 0 (0.0) |
| PAIR_12_12_COMBGB | 16,275 (18.8) | 10,633 (17.0) | 0 (0.0) |
| SETB | 16,923 (22.4) | 10,634 (19.1) | 0 (0.0) |
| INFO_WT7_alone | 0 (0.0) | 0 (0.0) | 2,010 (34.9) |

## Job 2 (WF-PRE): PAIR_10_10_PB minus PAIR_10_10_COMBGB

d mean -758/wk (block CI [-11,868, 9,480], iid [-14,317, 12,848], MDE block 15,230), d SD 17,390 (CI [3,105, 32,385]), d maxDD daily path 130,162 (weekly-path CI [-35,854, 343,774]), d worst -16,814, placebo rank maxDD 0.184 / mean 0.008, neighbours deltas ['-606', '-909'], verdict (pre, provisional) DEAD.

Verdict objects: s48score.verdict(cell,"sizing-lock-session"), CI = 8-week circular block bootstrap, 10,000 draws; placebo of record = rank on the maxDD difference vs 500 random-timing lock placebos (fire rates measured on the candidate: give-back day groups per cell; week floor fired in 0 groups). Provisional pre-stage verdicts use WF-PRE only (holdout condition listed as not looked).

Fire counts (candidate, all days incl. holdout days; counts only, no P&L): ASM_10_10_7_PB {'day': (811, 2865), 'week': (0, 582)}; ASM_S141010_7_PB {'day': (630, 2865), 'week': (0, 582)}; PAIR_10_10_PB {'day': (504, 1908), 'week': (0, 388)}; PAIR_10_10_COMBGB {'day': (463, 958), 'week': (0, 388)}

Holdout 2025-07+ will be read ONCE through s48score.score_cell(stage='final') after this text is sha256-logged (log_holdout_look('ASSEMBLY')); it is a RE-READ (Set A / Set B / ST-HM pair holdouts were printed in earlier reports), the assembled series are new. Pre-text observation (WF-PRE only): per-book give-back lets all three books keep trading after one book locks (79.6 trades/wk vs 35.8 for Set A) and the WF-PRE maxDD of the per-book assembly is above Set A's; the combined give-back variants are lower-risk. This is a description, nothing is re-tuned: the cells and criteria above were frozen before scoring.
