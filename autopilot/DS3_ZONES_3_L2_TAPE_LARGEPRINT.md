> **DEFECT BASE (V13X):** every cut, rank, lead and withdrawal on this page was computed on D7 V13X, which dropped the TH-L2 loss cut and take-line exits that came before the resting add filled (846 rows; BASE-4 fixed it in V13Y). Treat all numbers here as 'defect base (V13X)'; the V13Y re-run of the leads is in progress and will supersede them.

# DS3_ZONES_3_L2_TAPE_LARGEPRINT - the large-print rows: dollar effect of skipping them, definition sensitivity, walk-forward, live definition (ZL-2)

Rule `LP25_4h_D40`: skip the signal when a LARGE PRINT (any single print >= 25 contracts, either aggressor side) of the last 4 h, whose price level has not been traded through since the print (fresh), lies between the entry and the target within min(40 pts, target distance). 5,110 of 88,490 engine rows (5.8%); the same cell as `A40__TLP_p25_4h__skip` of the earlier pages. V13X base; windows L3M L6M HOLD MID PRE X' and Feb-Oct (F9). Post-hoc, Shadow only, no PASS.

## 1. Weekly dollar effect of SKIPPING the rows in the engine (cell minus base, $ per week; MDE = 2.8 x SE of the paired weekly delta; month-block bootstrap 95% CI; row-level placebo = random rows with the same count per day)
Placebo columns: the mean weekly delta of the random skips, and the share of placebo draws that are >= / <= the real delta (rank_le = share of draws the real delta BEATS: 1.00 = better than every random skip; low = worse than random).
| frame | window | base mean | delta mean $/wk | MDE | month-block CI | placebo draws | placebo mean | real beats (share) |
|---|---|---|---|---|---|---|---|---|
| lock none (headline) | L3M | +16.1 | +1972 | +7554 | [+23, +2882] | 200 | -82 | 0.80 |
| lock none (headline) | L6M | +26.9 | +2862 | +4288 | [+1439, +3444] | 200 | -941 | 0.97 |
| lock none (headline) | HOLD | +23.9 | +1886 | +2952 | [+284, +2833] | 200 | -1048 | 0.97 |
| lock none (headline) | MID | +10.9 | +1797 | +7254 | [-162, +3646] | 200 | -383 | 0.74 |
| lock none (headline) | PRE | +10.0 | -375 | +2686 | [-1830, +1153] | 200 | -935 | 0.71 |
| lock none (headline) | X' | -1.2 | -2279 | +5691 | [-6832, +1701] | 200 | -158 | 0.07 |
| lock none (headline) | F9 | +22.5 | +2601 | +3760 | [+1258, +3203] | 200 | -790 | 0.98 |
| 12R | L3M | +15.8 | +256 | +3753 | [-1480, +1723] | 200 | -220 | 0.60 |
| 12R | L6M | +22.4 | +2161 | +5934 | [-316, +5263] | 200 | -758 | 0.92 |
| 12R | HOLD | +19.9 | +1616 | +3540 | [-290, +3554] | 200 | -491 | 0.88 |
| 12R | MID | +5.3 | +3478 | +5741 | [+2663, +3874] | 200 | +1182 | 0.76 |
| 12R | PRE | +4.0 | +3438 | +5501 | [+134, +7861] | 200 | +212 | 0.99 |
| 12R | X' | -3.9 | +473 | +4504 | [-2203, +2361] | 200 | +666 | 0.44 |
| 12R | F9 | +17.6 | +2634 | +4551 | [+531, +4675] | 200 | -165 | 0.92 |

## 2. What the skipped rows themselves earned in V13X (realised net $ of the rows the engine TOOK that carry a large print ahead)
| frame | window | taken rows skipped (of taken) | sum $ | $ per row | $ per row of the other rows | worst 5% of them | the other 95% | best 5% |
|---|---|---|---|---|---|---|---|---|
| lock none | L6M | 197 (4424) | -90151 | -458 | +193 | -62520 | -27631 | +49495 |
| lock none | HOLD | 369 (7718) | -103393 | -280 | +183 | -129887 | +26494 | +110073 |
| lock none | PRE | 422 (6859) | -16772 | -40 | +119 | -164952 | +148180 | +162473 |
| lock none | X' | 290 (2661) | +53494 | +184 | -45 | -121724 | +175218 | +161819 |
| 12R | L6M | 114 (2756) | -37384 | -328 | +243 | -35474 | -1910 | +29837 |
| 12R | HOLD | 244 (5116) | -43537 | -178 | +221 | -88143 | +44606 | +77640 |
| 12R | PRE | 248 (4158) | -98270 | -396 | +101 | -98677 | +407 | +83968 |
| 12R | X' | 170 (1671) | +38953 | +229 | -142 | -64241 | +103194 | +102179 |
Reading: in HOLD the skipped rows lost $103k (-$280 per row against +$183 for the others) and the loss sits in the TAIL: the worst 5% of them lose $130k, the other 95% together earn +$26k, the best 5% +$110k. The benefit is a fat-left-tail effect, not a body effect. In PRE the rows lose only -$40 per row and in X' they WIN (+$184 per row): the information is a 2025-26 phenomenon.
By book (HOLD, lock none, sum $ of skipped rows): HM -9889 (65 rows); KB -15080 (139 rows); MV -23933 (67 rows); PB -2706 (12 rows); PE -45148 (72 rows); SM -6638 (14 rows). By session: asia +46724 (141 rows); london -118418 (114 rows); nyam -19733 (92 rows); nypm -11967 (22 rows). **The whole loss is in London (-$118k); the Asia rows with a large print ahead are WINNERS (+$47k).**

## 3. Definition sensitivity (engine: V13X lock none and 12R; weekly mean delta $/wk and the maxDD change)
| variant (threshold, window, side, reach) | rows | none: Δmean L6M | HOLD | PRE | X' | none: maxDD change L6M / PRE | 12R: Δmean L6M | HOLD | PRE | X' | 12R maxDD L6M / PRE |
|---|---|---|---|---|---|---|---|---|---|---|---|
| T100 15m any D40 | 172 | -180 | -61 | -179 | +56 | -3% / -0% | +53 | +36 | -41 | +2 | -9% / +0% |
| T100 1h any D40 | 234 | -180 | -113 | -203 | +137 | -3% / -0% | +53 | -1102 | -41 | +36 | -9% / +0% |
| T100 24h any D40 | 492 | +230 | -4 | +152 | +28 | -5% / -10% | +454 | -910 | +679 | -48 | -11% / -12% |
| T100 4h any D20 | 204 | -104 | -207 | +187 | +421 | -5% / -10% | -89 | -1221 | +630 | +30 | -4% / -12% |
| T100 4h any D40 | 312 | -153 | -92 | +165 | +383 | -5% / -10% | +71 | -1059 | +633 | +70 | -11% / -12% |
| T100 4h any D60 | 383 | -259 | -135 | +392 | +383 | -7% / -10% | -35 | -1089 | +802 | +70 | -15% / -13% |
| T10 15m any D40 | 17211 | +5104 | +2207 | -3467 | -383 | -3% / -23% | +1986 | +1144 | -1135 | +1006 | +32% / -9% |
| T10 1h any D40 | 22170 | +2551 | -967 | -2880 | +1039 | -7% / -32% | -2502 | -2858 | -325 | +3077 | +69% / -0% |
| T10 24h any D40 | 38602 | +4555 | +347 | -2705 | +1891 | -12% / -11% | +2017 | +1488 | +1530 | +4445 | +6% / -52% |
| T10 4h any D20 | 21896 | +750 | -1198 | -1254 | +2267 | +19% / -7% | +174 | -1669 | -1 | +4220 | +64% / -20% |
| T10 4h any D40 | 27451 | +2117 | +112 | -2368 | +2557 | +10% / -1% | +860 | +162 | +2088 | +5076 | +76% / -33% |
| T10 4h any D60 | 29450 | +1978 | -135 | -2486 | +2180 | +11% / -3% | +1386 | +1490 | +1687 | +4688 | +51% / -19% |
| T25 15m any D40 | 2763 | +2175 | +1452 | -140 | -1473 | -15% / -9% | +1778 | +3211 | +1214 | -543 | -12% / -11% |
| T25 1h against D40 | 1824 | +1679 | +901 | +235 | -1296 | -10% / -8% | +1293 | +2994 | +1980 | -270 | -3% / -10% |
| T25 1h any D40 | 3741 | +2510 | +1761 | -579 | -1488 | -16% / -1% | +1911 | +3275 | +1850 | -403 | -7% / -12% |
| T25 1h with D40 | 2134 | +1145 | +1094 | -1040 | -209 | -10% / +5% | +640 | +1053 | +329 | -210 | -8% / -21% |
| T25 24h any D40 | 7797 | +7108 | +3810 | +149 | -3464 | -29% / -4% | +2076 | +893 | +5124 | +1696 | -2% / -43% |
| T25 4h against D20 | 1739 | +1889 | +681 | +501 | +761 | -14% / -11% | +1280 | +199 | +1713 | +1820 | -1% / -10% |
| T25 4h against D40 | 2614 | +2788 | +1815 | +329 | -359 | -15% / -8% | +2217 | +1986 | +2304 | +1190 | -4% / -19% |
| T25 4h against D60 | 3032 | +1529 | +881 | +395 | -443 | -18% / +4% | +1150 | +1226 | +2853 | +1762 | -7% / -27% |
| T25 4h any D20 | 3556 | +2106 | +1091 | +119 | -769 | -15% / -3% | +1525 | -419 | +2522 | +974 | -4% / -22% |
| T25 4h any D40 | 5110 | +2862 | +1886 | -375 | -2279 | -19% / -8% | +2161 | +1616 | +3438 | +473 | -6% / -35% |
| T25 4h any D40 notfresh | 41869 | -2470 | -2013 | -5537 | -267 | -48% / -22% | -1678 | +741 | -1060 | +1757 | +7% / -26% |
| T25 4h any D60 | 5803 | +1320 | +1157 | -469 | -2573 | -13% / -10% | +1194 | +2349 | +3789 | +824 | -14% / -36% |
| T25 4h any P25 | 2812 | +2102 | +1442 | +598 | -1007 | -15% / -8% | +1547 | +1036 | +2228 | +1287 | -5% / -6% |
| T25 4h any P50 | 4267 | +2185 | +1745 | +362 | -2165 | -15% / -14% | +1395 | +67 | +3152 | +430 | +3% / -35% |
| T25 4h any P75 | 5185 | +2353 | +1625 | -192 | -2454 | -22% / -9% | +1501 | +2394 | +3581 | +280 | -6% / -37% |
| T25 4h with D20 | 2009 | +160 | +525 | -313 | -1154 | -5% / -1% | +94 | -694 | +1806 | -1082 | -5% / -21% |
| T25 4h with D40 | 2838 | +309 | +441 | -1203 | -2059 | -9% / +3% | +94 | -462 | +2349 | -98 | -5% / -28% |
| T25 4h with D60 | 3215 | -300 | +700 | -1028 | -1890 | +0% / +1% | +1603 | +2070 | +2584 | -98 | -13% / -30% |
| T50 15m any D40 | 689 | +475 | +283 | -329 | -573 | -4% / -4% | +71 | +29 | +9 | +252 | -9% / -16% |
| T50 1h any D40 | 920 | +433 | +202 | -355 | -511 | -4% / -3% | +71 | -1097 | +349 | +267 | -9% / -15% |
| T50 24h any D40 | 1975 | +1856 | +1303 | +1142 | -1329 | -9% / -3% | +419 | -677 | +2302 | +92 | -9% / -43% |
| T50 4h any D20 | 830 | +393 | +207 | +207 | -267 | -7% / -9% | +0 | -1076 | +1137 | +584 | -5% / -28% |
| T50 4h any D40 | 1267 | +329 | +203 | +395 | -976 | -7% / -2% | +99 | -782 | +1524 | +603 | -9% / -31% |
| T50 4h any D60 | 1480 | -141 | -158 | +45 | -944 | -5% / -1% | -257 | -933 | +1152 | +631 | -13% / -30% |

Reading of the grid: the weekly-mean effect needs threshold >= 25 (10 lots fires on 17-38k rows = volume; 100 lots too few rows), grows with the window (15 m +2.2k, 1 h +2.5k, 4 h +2.9k, 24 h +7.1k $/wk in L6M, lock none) and **is carried by prints AGAINST the trade (aggressor opposite to the trade direction: a large SELL print above a long = supply / absorption ahead): against 4 h D40 +2.8k L6M / +1.8k HOLD, WITH the trade +0.3k / +0.4k.** The not-fresh variant (any print of the last 4 h, touched or not) is worse than the base (fresh matters). Pct-of-target reaches 25/50/75% behave like D20-D60.

## 3b. The AGAINST-the-trade variant (`T25|4h|against|D40`: 2,614 rows): row outcome, placebo, walk-forward
| frame | window | delta mean $/wk | MDE | placebo draws | placebo mean | real beats (share) |
|---|---|---|---|---|---|---|
| lock none | L3M | +2202 | +5552 | 100 | -197 | 0.96 |
| lock none | L6M | +2788 | +3738 | 100 | -806 | 0.99 |
| lock none | HOLD | +1815 | +2479 | 100 | -682 | 0.99 |
| lock none | MID | +328 | +5780 | 100 | +71 | 0.56 |
| lock none | PRE | +329 | +2073 | 100 | -387 | 0.84 |
| lock none | X' | -359 | +3453 | 100 | -6 | 0.38 |
| 12R | L3M | +772 | +1890 | 100 | -21 | 0.73 |
| 12R | L6M | +2217 | +5740 | 100 | -576 | 0.98 |
| 12R | HOLD | +1986 | +3967 | 100 | -431 | 0.93 |
| 12R | MID | +3577 | +10839 | 100 | +97 | 0.92 |
| 12R | PRE | +2304 | +4403 | 100 | +525 | 0.97 |
| 12R | X' | +1190 | +3123 | 100 | +383 | 0.82 |

Row-level realised $ of the skipped rows (V13X taken rows, library of the earlier page): lock none, against: L6M -$559/row (n 128), HOLD -$368 (243), PRE -$346 (230), X' +$45 (148) vs the other rows +$185 / +$178 / +$125 / -$24; with the trade: -$135 / -$93 / **+$266** / +$125. With the combined 12R lock: against PRE -$609 per row. **Prints against the trade lose money in three of four windows (2024-26); prints with the trade do not.**
Walk-forward restricted to the against family (72 settings), 34 months: fixed default `T25 4h against D40` OOS excess $+244393 (t 3.44, 24/34 months positive; 2024 +83227, 2025 +55182, 2026 +105984); the trailing-12-month CHOICE gains less (+123099, t 0.76) because it drifts to the 10-lot volume-heavy settings. The definition is positive in every calendar year when fixed, but fixing it was done on this same data (post-hoc), and tuning it does not help.

## 4. Purged walk-forward on the definition (2024-01..2026-10; engine-free scoring)
Each month the setting (threshold {10,25,50,100} x window {15m,1h,4h,24h} x side {any, against, with} x reach {20,40,60}: 144 settings) is chosen on the trailing 12 months of label days (ending 2 days before the month) by the excess gain of skipping its flagged rows (gain = -sum of V13X realised $ of the flagged TAKEN rows, minus what skipping the same number of random rows costs = n x mean $), >= 80 flagged rows, and applied to the next month. Scoring: V13X realised $ per taken row, lock none (an approximation of the engine skip: no lock / ER re-sequencing).
| policy | months | sum of OOS excess $ | mean per month | t | positive months |
|---|---|---|---|---|---|
| walk-forward choice (trailing 12 m) | 34 | +402318 | +11833 | 2.21 | 20 |
| fixed default T25 4h any D40 | 34 | +227150 | +6681 | 2.47 | 23 |
| random setting each month | 34 | +156812 | +4612 | 1.17 | 21 |
* 2024: walk-forward -41052, fixed default +27294, random setting +50341 ($ excess over random skipping).
* 2025: walk-forward +285270, fixed default +64333, random setting +94325 ($ excess over random skipping).
* 2026: walk-forward +158099, fixed default +135524, random setting +12147 ($ excess over random skipping).
Settings chosen most often: T10|24h|any|D40 (7), T10|4h|with|D40 (5), T10|24h|with|D60 (5), T10|24h|any|D60 (5), T10|4h|against|D60 (4), T10|24h|with|D40 (4). Reading: the walk-forward choice and the fixed default both gain in 2025-26 and not in 2024; a RANDOM setting also gains +$157k over the 34 months, i.e. any large-print flag carries part of the effect, and the extra from tuning the definition is small and unstable (2024: -$41k).

## 5. Verdict on the flag test
Flag condition: skipped-row dollar effect positive with the row-level placebo rank <= 0.05 in lock none AND positive in PRE and X' AND surviving the walk-forward. **Not met.** Lock none: real delta beats all 200 random-skip draws in L6M (+$2.9k/wk vs -$0.9k for random; HOLD +$1.9k/wk, CI [+0.3k, +2.8k]; F9 +$2.6k/wk), INSIDE the MDE ($4.3k), but PRE is -$0.4k/wk (beats 70% of random) and X' -$2.3k/wk (beats 10%): the effect is absent before 2025, and it is a London-only, tail-driven effect.

## 6. LIVE definition (what D7 sees from its own print tape) and latency
* D7 keeps a list of prints with size >= 25 contracts (any aggressor side) from its own trade feed: (price, second). A print is usable from the first decision AFTER its second ends.
* At a signal (entry E, side s, target distance td, evaluated at the signal second): the signal is flagged if there is a print of the last 4 h (240 minutes) whose price p satisfies 0 <= s*(p - E) <= min(40, td) AND the price has not traded through p since the print (every trade price after the print on the same side of p, i.e. the instrument has not touched p again; touch = a trade at p or beyond in the direction of the move). Action in Shadow: log the flag; in the research frame: skip.
* Latency: a SKIP is decided at the signal second from state that is already known (prints and touches strictly before the decision second); a 1-s or 3-s decision delay changes the state by at most the prints of those seconds, so the skip is not delay-sensitive (verified for the other cells: delay 1 s/3 s moved the cuts by 0-10 points in the earlier pages). No book data needed; no daily file.
* Forward Shadow log fields (appended to FORWARD_SHADOW_ZONES_SPEC.md): lp_flag, lp_n_prints, lp_nearest_px, lp_nearest_dist, lp_nearest_size, lp_nearest_side, lp_age_s, lp_fresh_since (touch time or none), rule id ZL2_LP25_4H_D40.
