# DYNEXIT_WF EXACT section (W-DYNH; generated 2026-11-27 03:35Z UTC by code/th_dynexit/dx_score.py)

Exact engine rows only. 54 of 1752 DYNEXIT sets have all 42 months finished (Nov 2025 excluded). A set is used only when complete. Daily P&L = gross - 4.84 x lots per trade; the PESSIMISTIC label (stress) = also every Stop exit filled slip(lots) points worse (DS3_DN_STOPFILL: 1 lot 0.85, 5 lots 1.18, 8 lots 1.34 pt ...), x $20 x lots.

HOW TO READ: variant A = the book ALONE, bare (no layers, no TH); M = the live mix with this one stream changed, live TH kept; N = same, the book's live TH removed. Reference = fixed bracket (A: fix_A; M: the live mix; N: fix_N = live mix without that book's TH). Forward periods = Test 12 dates (weeks 26,39,...,169; 13 weeks each; tail wk 182 4 weeks), L3M = week 169-181, L6M = weeks 156-181. Drawdown first.

## 1. FIXED RECIPE vs its reference (no pick; every complete recipe, 12 forward periods of 13 weeks)

PASS = (forward max DD shallower or worst week better) in >= 2/3 of periods with income not lower by > 10%; or income higher in >= 2/3 with chained max DD not deeper. Counts: shallower DD / better worst week / higher income of n periods. Chained = the 12 forward periods joined into one curve (max DD of that curve) treated vs reference.

### AS: 34 complete (book x recipe x A/M) rows, 3 PASS
| book | recipe (family) | var | verdict | shallower DD / better worst wk / higher inc (n) | chained max DD recipe vs ref | income recipe vs ref (sum) | L3M DD recipe vs ref | L6M DD recipe vs ref |
|---|---|---|---|---|---|---|---|---|
| MF1 | mm127 (X3) | A | PASS | 6/5/5 of 12 | -85,922 vs -111,441 | 834,333 vs 831,743 | -66,387 vs -72,079 | -66,387 vs -72,079 |
| MF2 | rng07 (X1) | A | PASS | 6/8/8 of 12 | -67,942 vs -92,225 | 337,509 vs 326,955 | -47,703 vs -11,707 | -67,942 vs -20,443 |
| MF2 | atr10 (X1) | M | FAIL | 5/4/5 of 12 | -60,637 vs -67,941 | 814,482 vs 850,175 | -24,940 vs -21,250 | -34,549 vs -37,750 |
| MF1 | mm162 (X3) | A | FAIL | 4/2/6 of 12 | -111,153 vs -111,441 | 635,209 vs 831,743 | -77,069 vs -72,079 | -111,153 vs -72,079 |
| MF2 | atr07 (X1) | M | PASS | 7/7/6 of 12 | -68,730 vs -67,941 | 833,367 vs 850,175 | -24,594 vs -21,250 | -33,987 vs -37,750 |
| MF2 | rng10 (X1) | A | FAIL | 4/4/5 of 12 | -93,428 vs -92,225 | 382,535 vs 326,955 | -64,930 vs -11,707 | -64,930 vs -20,443 |
| MF1 | mm127 (X3) | M | FAIL | 3/4/6 of 12 | -70,601 vs -67,941 | 805,186 vs 850,175 | -21,250 vs -21,250 | -45,899 vs -37,750 |
| MF1 | mm162 (X3) | M | FAIL | 4/3/4 of 12 | -74,151 vs -67,941 | 772,703 vs 850,175 | -36,802 vs -21,250 | -39,915 vs -37,750 |
| MF2 | atr14 (X1) | M | FAIL | 4/5/5 of 12 | -77,445 vs -67,941 | 767,945 vs 850,175 | -32,005 vs -21,250 | -40,995 vs -37,750 |
| MF1 | sw4 (X2) | M | FAIL | 3/6/4 of 12 | -94,857 vs -67,941 | 592,955 vs 850,175 | -54,924 vs -21,250 | -54,924 vs -37,750 |
| MF1 | sw1 (X2) | M | FAIL | 3/4/5 of 12 | -103,906 vs -67,941 | 523,288 vs 850,175 | -76,565 vs -21,250 | -76,565 vs -37,750 |
| MF1 | rng10 (X1) | M | FAIL | 3/6/2 of 12 | -112,982 vs -67,941 | 493,541 vs 850,175 | -39,494 vs -21,250 | -67,856 vs -37,750 |
| MF2 | atr14 (X1) | A | FAIL | 3/5/7 of 12 | -151,732 vs -92,225 | 334,353 vs 326,955 | -60,010 vs -11,707 | -60,010 vs -20,443 |
| MF1 | rng14 (X1) | M | FAIL | 3/6/5 of 12 | -128,970 vs -67,941 | 452,555 vs 850,175 | -53,049 vs -21,250 | -73,647 vs -37,750 |
| MF2 | atr07 (X1) | A | FAIL | 6/6/6 of 12 | -159,008 vs -92,225 | 341,144 vs 326,955 | -28,222 vs -11,707 | -28,222 vs -20,443 |
| MF1 | rng07 (X1) | M | FAIL | 3/4/2 of 12 | -143,775 vs -67,941 | 398,754 vs 850,175 | -57,856 vs -21,250 | -64,898 vs -37,750 |
| MF1 | sw1 (X2) | A | FAIL | 7/8/4 of 12 | -192,094 vs -111,441 | 345,902 vs 831,743 | -136,880 vs -72,079 | -192,094 vs -72,079 |
| MF1 | sw4 (X2) | A | FAIL | 8/7/6 of 12 | -194,630 vs -111,441 | 483,563 vs 831,743 | -138,094 vs -72,079 | -194,630 vs -72,079 |
| MF1 | opp (X7) | M | FAIL | 4/5/0 of 12 | -151,236 vs -67,941 | 509,421 vs 850,175 | -32,458 vs -21,250 | -35,991 vs -37,750 |
| MF1 | tm60 (X6) | M | FAIL | 5/4/1 of 12 | -153,827 vs -67,941 | 529,401 vs 850,175 | -21,356 vs -21,250 | -36,358 vs -37,750 |
| MF2 | atr10 (X1) | A | FAIL | 3/4/4 of 12 | -189,238 vs -92,225 | 315,538 vs 326,955 | -36,831 vs -11,707 | -36,831 vs -20,443 |
| MF1 | opp (X7) | A | FAIL | 7/8/2 of 12 | -220,221 vs -111,441 | 138,650 vs 831,743 | -109,977 vs -72,079 | -109,977 vs -72,079 |
| MF1 | rng07 (X1) | A | FAIL | 5/6/3 of 12 | -227,512 vs -111,441 | 157,171 vs 831,743 | -167,650 vs -72,079 | -227,512 vs -72,079 |
| MF1 | atr07 (X1) | M | FAIL | 3/7/1 of 12 | -186,637 vs -67,941 | 265,353 vs 850,175 | -75,935 vs -21,250 | -114,042 vs -37,750 |
| MF1 | atr10 (X1) | M | FAIL | 3/7/5 of 12 | -188,839 vs -67,941 | 372,749 vs 850,175 | -41,033 vs -21,250 | -95,767 vs -37,750 |

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
| X1 | 29 | 3 | 4 |
| X2 | 6 | 0 | 0 |
| X3 | 6 | 1 | 2 |
| X6 | 6 | 0 | 0 |
| X7 | 3 | 0 | 0 |

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

## 4. PESSIMISTIC STOP-FILL LABEL on the fixed-recipe PASS rows (M variant): chained forward max DD and income, measured vs stress

| session | book | recipe | chained DD (measured) | chained DD (stress) | live-mix DD (stress) | income recipe (stress) vs live (stress) |
|---|---|---|---|---|---|---|
| AS | MF2 | atr07 | -68,730 | -75,973 | -75,148 | 722,627 vs 743,428 |
