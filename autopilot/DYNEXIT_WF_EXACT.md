# DYNEXIT_WF EXACT section (W-DYNH; generated 2026-11-27 03:47Z UTC by code/th_dynexit/dx_score.py)

Exact engine rows only. 102 of 1752 DYNEXIT sets have all 42 months finished (Nov 2025 excluded). A set is used only when complete. Daily P&L = gross - 4.84 x lots per trade; the PESSIMISTIC label (stress) = also every Stop exit filled slip(lots) points worse (DS3_DN_STOPFILL: 1 lot 0.85, 5 lots 1.18, 8 lots 1.34 pt ...), x $20 x lots.

HOW TO READ: variant A = the book ALONE, bare (no layers, no TH); M = the live mix with this one stream changed, live TH kept; N = same, the book's live TH removed. Reference = fixed bracket (A: fix_A; M: the live mix; N: fix_N = live mix without that book's TH). Forward periods = Test 12 dates (weeks 26,39,...,169; 13 weeks each; tail wk 182 4 weeks), L3M = week 169-181, L6M = weeks 156-181. Drawdown first.

## 1. FIXED RECIPE vs its reference (no pick; every complete recipe, 12 forward periods of 13 weeks)

PASS = (forward max DD shallower or worst week better) in >= 2/3 of periods with income not lower by > 10%; or income higher in >= 2/3 with chained max DD not deeper. Counts: shallower DD / better worst week / higher income of n periods. Chained = the 12 forward periods joined into one curve (max DD of that curve) treated vs reference.

### AS: 65 complete (book x recipe x A/M) rows, 9 PASS
| book | recipe (family) | var | verdict | shallower DD / better worst wk / higher inc (n) | chained max DD recipe vs ref | income recipe vs ref (sum) | L3M DD recipe vs ref | L6M DD recipe vs ref |
|---|---|---|---|---|---|---|---|---|
| MF1 | mm127 (X3) | A | PASS | 6/5/5 of 12 | -85,922 vs -111,441 | 834,333 vs 831,743 | -66,387 vs -72,079 | -66,387 vs -72,079 |
| MF2 | rng07 (X1) | A | PASS | 6/8/8 of 12 | -67,942 vs -92,225 | 337,509 vs 326,955 | -47,703 vs -11,707 | -67,942 vs -20,443 |
| MF2 | atr10 (X1) | M | FAIL | 5/4/5 of 12 | -60,637 vs -67,941 | 814,482 vs 850,175 | -24,940 vs -21,250 | -34,549 vs -37,750 |
| MF2 | rng10 (X1) | M | PASS | 5/8/3 of 12 | -62,596 vs -67,941 | 790,743 vs 850,175 | -21,670 vs -21,250 | -36,332 vs -37,750 |
| MF2 | rng07 (X1) | M | PASS | 6/7/3 of 12 | -64,370 vs -67,941 | 787,965 vs 850,175 | -31,801 vs -21,250 | -46,251 vs -37,750 |
| MF2 | sw1 (X2) | M | PASS | 9/7/4 of 12 | -64,643 vs -67,941 | 771,589 vs 850,175 | -24,890 vs -21,250 | -33,265 vs -37,750 |
| MF2 | opp (X7) | A | FAIL | 3/1/3 of 12 | -89,775 vs -92,225 | 326,965 vs 326,955 | -11,707 vs -11,707 | -20,443 vs -20,443 |
| MF2 | sw4 (X2) | M | PASS | 8/7/4 of 12 | -67,048 vs -67,941 | 773,341 vs 850,175 | -24,945 vs -21,250 | -32,925 vs -37,750 |
| MF1 | mm162 (X3) | A | FAIL | 4/2/6 of 12 | -111,153 vs -111,441 | 635,209 vs 831,743 | -77,069 vs -72,079 | -111,153 vs -72,079 |
| MF2 | mm127 (X3) | M | FAIL | 4/2/5 of 12 | -67,771 vs -67,941 | 775,457 vs 850,175 | -27,745 vs -21,250 | -38,259 vs -37,750 |
| MF2 | opp (X7) | M | FAIL | 1/1/3 of 12 | -67,941 vs -67,941 | 850,665 vs 850,175 | -21,250 vs -21,250 | -37,750 vs -37,750 |
| MF2 | atr07 (X1) | M | PASS | 7/7/6 of 12 | -68,730 vs -67,941 | 833,367 vs 850,175 | -24,594 vs -21,250 | -33,987 vs -37,750 |
| MF2 | mm162 (X3) | M | FAIL | 7/3/6 of 12 | -69,100 vs -67,941 | 763,229 vs 850,175 | -34,665 vs -21,250 | -34,665 vs -37,750 |
| MF2 | rng10 (X1) | A | FAIL | 4/4/5 of 12 | -93,428 vs -92,225 | 382,535 vs 326,955 | -64,930 vs -11,707 | -64,930 vs -20,443 |
| MF1 | mm127 (X3) | M | FAIL | 3/4/6 of 12 | -70,601 vs -67,941 | 805,186 vs 850,175 | -21,250 vs -21,250 | -45,899 vs -37,750 |
| MF2 | rng14 (X1) | M | PASS | 7/6/5 of 12 | -71,646 vs -67,941 | 796,440 vs 850,175 | -40,782 vs -21,250 | -40,782 vs -37,750 |
| MF1 | mm162 (X3) | M | FAIL | 4/3/4 of 12 | -74,151 vs -67,941 | 772,703 vs 850,175 | -36,802 vs -21,250 | -39,915 vs -37,750 |
| MF3 | rng07 (X1) | A | FAIL | 4/7/1 of 12 | -109,981 vs -103,232 | 43,841 vs 522,546 | -91,471 vs -45,501 | -94,154 vs -45,501 |
| MF2 | tm60 (X6) | M | PASS | 5/7/2 of 12 | -75,638 vs -67,941 | 769,279 vs 850,175 | -23,045 vs -21,250 | -38,120 vs -37,750 |
| MF3 | atr07 (X1) | A | FAIL | 4/7/1 of 12 | -111,402 vs -103,232 | 47,760 vs 522,546 | -76,451 vs -45,501 | -111,402 vs -45,501 |
| MF2 | tm15 (X6) | M | FAIL | 6/7/2 of 12 | -77,154 vs -67,941 | 600,891 vs 850,175 | -21,025 vs -21,250 | -44,800 vs -37,750 |
| MF3 | rng07 (X1) | M | FAIL | 7/8/4 of 12 | -77,440 vs -67,941 | 636,301 vs 850,175 | -41,741 vs -21,250 | -41,741 vs -37,750 |
| MF2 | atr14 (X1) | M | FAIL | 4/5/5 of 12 | -77,445 vs -67,941 | 767,945 vs 850,175 | -32,005 vs -21,250 | -40,995 vs -37,750 |
| MF2 | sw1 (X2) | A | FAIL | 5/5/5 of 12 | -102,574 vs -92,225 | 352,161 vs 326,955 | -22,646 vs -11,707 | -28,920 vs -20,443 |
| MF2 | tm30 (X6) | M | FAIL | 6/8/1 of 12 | -79,581 vs -67,941 | 645,184 vs 850,175 | -30,596 vs -21,250 | -48,690 vs -37,750 |

### NY: 0 complete (book x recipe x A/M) rows, 0 PASS
| book | recipe (family) | var | verdict | shallower DD / better worst wk / higher inc (n) | chained max DD recipe vs ref | income recipe vs ref (sum) | L3M DD recipe vs ref | L6M DD recipe vs ref |
|---|---|---|---|---|---|---|---|---|

### NP: 0 complete (book x recipe x A/M) rows, 0 PASS
| book | recipe (family) | var | verdict | shallower DD / better worst wk / higher inc (n) | chained max DD recipe vs ref | income recipe vs ref (sum) | L3M DD recipe vs ref | L6M DD recipe vs ref |
|---|---|---|---|---|---|---|---|---|

### LO: 0 complete (book x recipe x A/M) rows, 0 PASS
| book | recipe (family) | var | verdict | shallower DD / better worst wk / higher inc (n) | chained max DD recipe vs ref | income recipe vs ref (sum) | L3M DD recipe vs ref | L6M DD recipe vs ref |
|---|---|---|---|---|---|---|---|---|

### Family by family (all complete rows, A and M, N): rows / PASS / chained max DD shallower than reference
| family | rows | PASS | shallower chained DD |
|---|---|---|---|
| X1 | 51 | 9 | 10 |
| X2 | 13 | 4 | 4 |
| X3 | 12 | 1 | 4 |
| X6 | 15 | 1 | 0 |
| X7 | 6 | 0 | 1 |

## 2. WALK-FORWARD PICK on exact rows (per book on the A rows, forward judged on the M row of the pick; mix = live + sum of per-book M deltas = post-hoc additive across books)

Pick rule (named in the order): eligible = last 26 and last 13 weeks positive, >= 20 trades in 26 weeks, no earlier full calendar year with ulcer > 1.3 x the fixed bracket's; best = lowest ulcer over the last 26 weeks then highest income; the pick replaces the fixed bracket only if its recent ulcer is lower. Re-pick every 13 / 4 / 2 weeks (2 weeks = Josh's rhythm, shown first). Menu size for the luck accounting: 38 recipes (seed + hook + X9) per book.

### step 2 weeks
| session | mix verdict | n | shallower / worst-wk better / income higher | chained max DD pick vs live | income pick vs live | books: picks (switches) |
|---|---|---|---|---|---|---|
| AS | PENDING (fixed reference rows not complete) | | | | | |
| NY | PENDING (fixed reference rows not complete) | | | | | |
| NP | PENDING (fixed reference rows not complete) | | | | | |
| LO | PENDING (fixed reference rows not complete) | | | | | |

### step 4 weeks
| session | mix verdict | n | shallower / worst-wk better / income higher | chained max DD pick vs live | income pick vs live | books: picks (switches) |
|---|---|---|---|---|---|---|
| AS | PENDING (fixed reference rows not complete) | | | | | |
| NY | PENDING (fixed reference rows not complete) | | | | | |
| NP | PENDING (fixed reference rows not complete) | | | | | |
| LO | PENDING (fixed reference rows not complete) | | | | | |

### step 13 weeks
| session | mix verdict | n | shallower / worst-wk better / income higher | chained max DD pick vs live | income pick vs live | books: picks (switches) |
|---|---|---|---|---|---|---|
| AS | PENDING (fixed reference rows not complete) | | | | | |
| NY | PENDING (fixed reference rows not complete) | | | | | |
| NP | PENDING (fixed reference rows not complete) | | | | | |
| LO | PENDING (fixed reference rows not complete) | | | | | |

## 3. TRADE HEALTH INTERACTION: recipe + live TH (M) vs recipe alone in the mix (N), books that have live TH (AS MF1-4, NP MF1-4)

Full period 2023-04..2026-10 (Nov 2025 excl.). A recipe where N is shallower than M on max DD AND income not lower = the live TH FIGHTS the new exit; M better than N = they cooperate. Reference rows: live mix and fix_N (mix without that book's TH).

| session | book | recipe | DD live mix / fix_N / M / N | income live / fix_N / M / N | reading |
|---|---|---|---|---|---|
| AS | MF1 | atr07 | -67,941 / -64,706 / -186,637 / -188,975 | 914,998 / 936,314 / 373,190 / 307,333 | cooperate |
| AS | MF1 | atr10 | -67,941 / -64,706 / -188,839 / -196,100 | 914,998 / 936,314 / 478,711 / 474,753 | cooperate |
| AS | MF1 | atr14 | -67,941 / -64,706 / -236,631 / -246,837 | 914,998 / 936,314 / 493,948 / 456,697 | cooperate |
| AS | MF1 | mm127 | -67,941 / -64,706 / -70,601 / -77,237 | 914,998 / 936,314 / 843,089 / 818,208 | cooperate |
| AS | MF1 | mm162 | -67,941 / -64,706 / -74,151 / -81,597 | 914,998 / 936,314 / 823,050 / 790,548 | cooperate |
| AS | MF1 | opp | -67,941 / -64,706 / -151,236 / -154,826 | 914,998 / 936,314 / 544,303 / 532,119 | cooperate |
| AS | MF1 | rng07 | -67,941 / -64,706 / -143,775 / -148,107 | 914,998 / 936,314 / 466,330 / 426,949 | cooperate |
| AS | MF1 | rng10 | -67,941 / -64,706 / -112,982 / -91,830 | 914,998 / 936,314 / 598,420 / 635,529 | fight (TH hurts) |
| AS | MF1 | rng14 | -67,941 / -64,706 / -128,970 / -131,775 | 914,998 / 936,314 / 597,329 / 587,316 | cooperate |
| AS | MF1 | sw1 | -67,941 / -64,706 / -103,906 / -103,302 | 914,998 / 936,314 / 570,791 / 614,838 | mixed |
| AS | MF1 | sw4 | -67,941 / -64,706 / -94,857 / -103,828 | 914,998 / 936,314 / 629,628 / 668,235 | mixed |
| AS | MF1 | tm30 | -67,941 / -64,706 / -195,503 / -196,143 | 914,998 / 936,314 / 233,852 / 225,695 | cooperate |
| AS | MF1 | tm60 | -67,941 / -64,706 / -153,827 / -155,847 | 914,998 / 936,314 / 548,857 / 517,335 | cooperate |
| AS | MF2 | atr07 | -67,941 / -74,536 / -68,730 / -82,082 | 914,998 / 908,591 / 895,575 / 931,998 | mixed |
| AS | MF2 | atr10 | -67,941 / -74,536 / -60,637 / -62,117 | 914,998 / 908,591 / 873,621 / 973,616 | mixed |
| AS | MF2 | atr14 | -67,941 / -74,536 / -77,445 / -71,931 | 914,998 / 908,591 / 828,176 / 932,725 | fight (TH hurts) |
| AS | MF2 | mm127 | -67,941 / -74,536 / -67,771 / -75,351 | 914,998 / 908,591 / 838,115 / 836,485 | cooperate |
| AS | MF2 | mm162 | -67,941 / -74,536 / -69,100 / -73,806 | 914,998 / 908,591 / 825,661 / 825,985 | mixed |
| AS | MF2 | opp | -67,941 / -74,536 / -67,941 / -74,536 | 914,998 / 908,591 / 914,496 / 905,927 | cooperate |
| AS | MF2 | rng07 | -67,941 / -74,536 / -64,370 / -69,686 | 914,998 / 908,591 / 835,644 / 884,867 | mixed |
| AS | MF2 | rng10 | -67,941 / -74,536 / -62,596 / -59,298 | 914,998 / 908,591 / 864,626 / 1,011,119 | fight (TH hurts) |
| AS | MF2 | rng14 | -67,941 / -74,536 / -71,646 / -61,392 | 914,998 / 908,591 / 864,493 / 886,028 | fight (TH hurts) |
| AS | MF2 | sw1 | -67,941 / -74,536 / -64,643 / -60,998 | 914,998 / 908,591 / 843,590 / 902,288 | fight (TH hurts) |
| AS | MF2 | sw4 | -67,941 / -74,536 / -67,048 / -62,611 | 914,998 / 908,591 / 839,361 / 904,132 | fight (TH hurts) |
| AS | MF2 | tm15 | -67,941 / -74,536 / -77,154 / -79,516 | 914,998 / 908,591 / 642,145 / 625,732 | cooperate |
| AS | MF2 | tm30 | -67,941 / -74,536 / -79,581 / -82,204 | 914,998 / 908,591 / 695,647 / 651,061 | cooperate |
| AS | MF2 | tm60 | -67,941 / -74,536 / -75,638 / -78,736 | 914,998 / 908,591 / 832,341 / 795,621 | cooperate |
| AS | MF3 | atr07 | -67,941 / -88,096 / -93,033 / -83,585 | 914,998 / 1,034,357 / 634,890 / 777,721 | fight (TH hurts) |
| AS | MF3 | atr10 | -67,941 / -88,096 / -116,021 / -111,025 | 914,998 / 1,034,357 / 720,090 / 712,301 | mixed |
| AS | MF3 | atr14 | -67,941 / -88,096 / -136,013 / -160,486 | 914,998 / 1,034,357 / 600,489 / 506,575 | cooperate |
| AS | MF3 | rng07 | -67,941 / -88,096 / -77,440 / -94,497 | 914,998 / 1,034,357 / 690,477 / 690,177 | cooperate |

## 5. FIXED-RULE ROWS (order 0343Z): every recipe as ONE fixed setting, straight through all 42 months, vs the live mix (M) / live mix without the book's TH (N)

Defaults committed before scoring: /mnt/l2/l2vast/_dynexit/fixed_rules_dynh.json (03:50Z). Every seed recipe is itself a fixed-setting row (no search); DEFAULT = the committed one per family. Win in a window = shallower max DD with income not lower by > 10%, or higher income with DD not deeper. CANDIDATE = DEFAULT rule that wins in >= 3 of the 4 calendar years AND L6M AND L3M in the M variant (and N where it exists); the random-exit null and non-hindsight entries are NOT done here (flag: pending null). Free settings = number of tunable parameters in the rule.

| session | book | recipe (family, free settings) | var | years 2023/24/25/26 | L6M | L3M | max DD rule vs ref | income rule vs ref | flag |
|---|---|---|---|---|---|---|---|---|---|
| AS | MF1 | atr10 (X1, 1) | M | -/-/-/- | - | - | -188,839 vs -67,941 | 478,711 vs 914,998 | default |
| AS | MF1 | atr10 (X1, 1) | N | -/-/-/- | - | - | -196,100 vs -64,706 | 474,753 vs 936,314 | default |
| AS | MF1 | mm127 (X3, 1) | M | -/-/-/W | - | - | -70,601 vs -67,941 | 843,089 vs 914,998 | default |
| AS | MF1 | mm127 (X3, 1) | N | W/-/-/- | - | - | -77,237 vs -64,706 | 818,208 vs 936,314 | default |
| AS | MF1 | opp (X7, 0) | M | -/-/-/- | - | - | -151,236 vs -67,941 | 544,303 vs 914,998 | default |
| AS | MF1 | opp (X7, 0) | N | -/-/-/- | - | - | -154,826 vs -64,706 | 532,119 vs 936,314 | default |
| AS | MF1 | rng10 (X1, 1) | M | -/-/-/- | - | - | -112,982 vs -67,941 | 598,420 vs 914,998 | default |
| AS | MF1 | rng10 (X1, 1) | N | -/-/-/- | - | - | -91,830 vs -64,706 | 635,529 vs 936,314 | default |
| AS | MF1 | sw4 (X2, 1) | M | -/-/W/- | - | - | -94,857 vs -67,941 | 629,628 vs 914,998 | default |
| AS | MF1 | sw4 (X2, 1) | N | -/-/W/- | - | - | -103,828 vs -64,706 | 668,235 vs 936,314 | default |
| AS | MF1 | tm30 (X6, 1) | M | -/-/-/- | - | - | -195,503 vs -67,941 | 233,852 vs 914,998 | default |
| AS | MF1 | tm30 (X6, 1) | N | -/-/-/- | - | - | -196,143 vs -64,706 | 225,695 vs 936,314 | default |
| AS | MF2 | atr10 (X1, 1) | M | -/-/-/- | W | - | -60,637 vs -67,941 | 873,621 vs 914,998 | default |
| AS | MF2 | atr10 (X1, 1) | N | -/W/-/- | W | - | -62,117 vs -74,536 | 973,616 vs 908,591 | default |
| AS | MF2 | mm127 (X3, 1) | M | -/-/-/W | - | - | -67,771 vs -67,941 | 838,115 vs 914,998 | default |
| AS | MF2 | mm127 (X3, 1) | N | -/W/-/- | W | - | -75,351 vs -74,536 | 836,485 vs 908,591 | default |
| AS | MF2 | opp (X7, 0) | M | -/W/-/W | - | - | -67,941 vs -67,941 | 914,496 vs 914,998 | default |
| AS | MF2 | opp (X7, 0) | N | -/W/-/W | - | - | -74,536 vs -74,536 | 905,927 vs 908,591 | default |
| AS | MF2 | rng10 (X1, 1) | M | -/-/-/- | W | - | -62,596 vs -67,941 | 864,626 vs 914,998 | default |
| AS | MF2 | rng10 (X1, 1) | N | -/W/W/- | W | - | -59,298 vs -74,536 | 1,011,119 vs 908,591 | default |
| AS | MF2 | sw4 (X2, 1) | M | W/W/-/- | W | - | -67,048 vs -67,941 | 839,361 vs 914,998 | default |
| AS | MF2 | sw4 (X2, 1) | N | -/W/-/- | W | - | -62,611 vs -74,536 | 904,132 vs 908,591 | default |
| AS | MF2 | tm30 (X6, 1) | M | -/-/-/- | - | - | -79,581 vs -67,941 | 695,647 vs 914,998 | default |
| AS | MF2 | tm30 (X6, 1) | N | -/-/-/- | - | - | -82,204 vs -74,536 | 651,061 vs 908,591 | default |
| AS | MF3 | atr10 (X1, 1) | M | -/W/-/- | - | - | -116,021 vs -67,941 | 720,090 vs 914,998 | default |
| AS | MF3 | atr10 (X1, 1) | N | -/W/-/- | - | - | -111,025 vs -88,096 | 712,301 vs 1,034,357 | default |
| AS | MF3 | rng10 (X1, 1) | N | -/-/-/- | - | - | -157,120 vs -88,096 | 498,298 vs 1,034,357 | default |

Fixed-rule rows complete: 63 (M and N). CANDIDATES: 0 []

Walk-forward pick row beside it: section 2 (mix level). Which is better per family and whether re-fitting adds anything is read from sections 2 and 5 once the rows are complete.

## 4. PESSIMISTIC STOP-FILL LABEL on the fixed-recipe PASS rows (M variant): chained forward max DD and income, measured vs stress

| session | book | recipe | chained DD (measured) | chained DD (stress) | live-mix DD (stress) | income recipe (stress) vs live (stress) |
|---|---|---|---|---|---|---|
| AS | MF2 | atr07 | -68,730 | -75,973 | -75,148 | 722,627 vs 743,428 |
| AS | MF2 | rng07 | -64,370 | -71,000 | -75,148 | 677,415 vs 743,428 |
| AS | MF2 | rng10 | -62,596 | -71,066 | -75,148 | 683,233 vs 743,428 |
| AS | MF2 | rng14 | -71,646 | -79,774 | -75,148 | 691,356 vs 743,428 |
| AS | MF2 | sw1 | -64,643 | -74,179 | -75,148 | 662,735 vs 743,428 |
| AS | MF2 | sw4 | -67,048 | -74,130 | -75,148 | 664,463 vs 743,428 |
| AS | MF2 | tm60 | -75,638 | -82,661 | -75,148 | 665,242 vs 743,428 |
