# DS3_ZONES_3_L2_TAPE_LARGEPRINT - the large-print rows: dollar effect of skipping them, definition sensitivity, walk-forward, live definition (ZL-2)

Rule `LP25_4h_D40`: skip the signal when a LARGE PRINT (any single print >= 25 contracts, either aggressor side) of the last 4 h, whose price level has not been traded through since the print (fresh), lies between the entry and the target within min(40 pts, target distance). 5,110 of 88,490 engine rows (5.8%); the same cell as `A40__TLP_p25_4h__skip` of the earlier pages. V13Y base; windows L3M L6M HOLD MID PRE X' and Feb-Oct (F9). Post-hoc, Shadow only, no PASS.

## 1. Weekly dollar effect of SKIPPING the rows in the engine (cell minus base, $ per week; MDE = 2.8 x SE of the paired weekly delta; month-block bootstrap 95% CI; row-level placebo = random rows with the same count per day)
Placebo columns: the mean weekly delta of the random skips, and the share of placebo draws that are >= / <= the real delta (rank_le = share of draws the real delta BEATS: 1.00 = better than every random skip; low = worse than random).
| frame | window | base mean | delta mean $/wk | MDE | month-block CI | placebo draws | placebo mean | real beats (share) |
|---|---|---|---|---|---|---|---|---|
| lock none (headline) | L3M | +19.7 | +2632 | +7106 | [+1178, +2882] | 100 | -579 | 0.85 |
| lock none (headline) | L6M | +28.8 | +3113 | +4111 | [+2124, +3338] | 100 | -1180 | 0.99 |
| lock none (headline) | HOLD | +24.6 | +1912 | +2898 | [+344, +2800] | 100 | -1134 | 0.98 |
| lock none (headline) | MID | +16.4 | +1876 | +7332 | [-121, +3646] | 100 | -808 | 0.82 |
| lock none (headline) | PRE | +12.1 | -683 | +2748 | [-2029, +825] | 100 | -1154 | 0.69 |
| lock none (headline) | X' | +1.6 | -1029 | +4314 | [-3720, +1554] | 100 | +219 | 0.14 |
| lock none (headline) | F9 | +25.6 | +2805 | +3676 | [+1592, +3190] | 100 | -1094 | 0.99 |
| 12R | L3M | +13.8 | +1437 | +3085 | [+664, +2212] | 100 | -517 | 0.76 |
| 12R | L6M | +21.2 | +2522 | +5447 | [+483, +5201] | 100 | -205 | 0.90 |
| 12R | HOLD | +16.4 | +2437 | +4555 | [+155, +4501] | 100 | +824 | 0.81 |
| 12R | MID | +6.7 | +5850 | +14946 | [+1475, +10204] | 100 | +1316 | 0.88 |
| 12R | PRE | +5.9 | +962 | +2604 | [-570, +2218] | 100 | -1033 | 0.92 |
| 12R | X' | -1.1 | -1102 | +4843 | [-4605, +1669] | 100 | -130 | 0.25 |
| 12R | F9 | +17.2 | +3640 | +6019 | [+1039, +5815] | 100 | +270 | 0.96 |

## 2. What the skipped rows themselves earned in V13X (realised net $ of the rows the engine TOOK that carry a large print ahead)
| frame | window | taken rows skipped (of taken) | sum $ | $ per row | $ per row of the other rows | worst 5% of them | the other 95% | best 5% |
|---|---|---|---|---|---|---|---|---|
| lock none | L6M | 202 (4486) | -95394 | -472 | +203 | -68604 | -26790 | +47517 |
| lock none | HOLD | 374 (7785) | -104703 | -280 | +187 | -129887 | +25185 | +106807 |
| lock none | PRE | 422 (6889) | -9216 | -22 | +142 | -163949 | +154734 | +162467 |
| lock none | X' | 290 (2666) | +51933 | +179 | +9 | -121724 | +173657 | +149077 |
| 12R | L6M | 132 (3049) | -57182 | -433 | +216 | -42901 | -14281 | +30454 |
| 12R | HOLD | 255 (5336) | -60853 | -239 | +180 | -90640 | +29787 | +74586 |
| 12R | PRE | 269 (4465) | -104456 | -388 | +130 | -120926 | +16470 | +92580 |
| 12R | X' | 180 (1801) | +55697 | +309 | -65 | -70403 | +126100 | +108564 |
Reading: in HOLD the skipped rows lost $103k (-$280 per row against +$183 for the others) and the loss sits in the TAIL: the worst 5% of them lose $130k, the other 95% together earn +$26k, the best 5% +$110k. The benefit is a fat-left-tail effect, not a body effect. In PRE the rows lose only -$40 per row and in X' they WIN (+$184 per row): the information is a 2025-26 phenomenon.
By book (HOLD, lock none, sum $ of skipped rows): HM -7138 (68 rows); KB -15104 (142 rows); MV -24407 (67 rows); PB -2706 (12 rows); PE -43828 (71 rows); SM -11520 (14 rows). By session: asia +41842 (141 rows); london -120377 (114 rows); nyam -13784 (95 rows); nypm -12384 (24 rows). **The whole loss is in London (-$118k); the Asia rows with a large print ahead are WINNERS (+$47k).**

## 3. Definition sensitivity (engine: V13X lock none and 12R; weekly mean delta $/wk and the maxDD change)
| variant (threshold, window, side, reach) | rows | none: Δmean L6M | HOLD | PRE | X' | none: maxDD change L6M / PRE | 12R: Δmean L6M | HOLD | PRE | X' | 12R maxDD L6M / PRE |
|---|---|---|---|---|---|---|---|---|---|---|---|
| T100 15m any D40 | 172 | -95 | -26 | -179 | +56 | -2% / +0% | -197 | -131 | -71 | +48 | -1% / +0% |
| T100 1h any D40 | 234 | -95 | -108 | -203 | -3 | -2% / +0% | -197 | -106 | -71 | +66 | -1% / +0% |
| T100 24h any D40 | 492 | +316 | +50 | -199 | -155 | -2% / +0% | +105 | +12 | -45 | -767 | -1% / +1% |
| T100 4h any D20 | 204 | -187 | -260 | -165 | +421 | -2% / +0% | -252 | -208 | -94 | +219 | -1% / +0% |
| T100 4h any D40 | 312 | -67 | -87 | -186 | +158 | -2% / +0% | -278 | -120 | -91 | -650 | -1% / +0% |
| T100 4h any D60 | 383 | -174 | -130 | -8 | +158 | -5% / +0% | -384 | -163 | +29 | -650 | -1% / +0% |
| T10 15m any D40 | 17211 | +3877 | +1316 | -3693 | +178 | -16% / -28% | +3130 | +3597 | -2239 | -536 | +32% / -24% |
| T10 1h any D40 | 22170 | +1286 | -1898 | -4043 | +1087 | -23% / -31% | -2605 | -1417 | -2349 | +1898 | +101% / -27% |
| T10 24h any D40 | 38602 | +1569 | -1079 | -3958 | -37 | -15% / +7% | +2909 | +3792 | -86 | +2775 | +15% / -65% |
| T10 4h any D20 | 21896 | -16 | -2315 | -2803 | +1958 | +18% / -7% | +2120 | -2 | -1716 | +3582 | +67% / -32% |
| T10 4h any D40 | 27451 | +795 | -1362 | -3802 | +2213 | -4% / +9% | +1928 | +1969 | -379 | +3647 | +82% / -37% |
| T10 4h any D60 | 29450 | +265 | -1596 | -3988 | +1837 | +2% / +14% | +2127 | +1685 | +225 | +3259 | +72% / -49% |
| T25 15m any D40 | 2763 | +2518 | +1534 | -145 | -1365 | -25% / -6% | +2677 | +2558 | +106 | -1575 | -8% / -17% |
| T25 1h against D40 | 1824 | +1808 | +854 | +153 | -1024 | -17% / +2% | +1411 | +2154 | +756 | -678 | +1% / -7% |
| T25 1h any D40 | 3741 | +2856 | +1830 | -610 | -1217 | -29% / +1% | +2600 | +2762 | +531 | -1303 | -8% / -10% |
| T25 1h with D40 | 2134 | +1361 | +1233 | -1155 | -349 | -18% / -4% | +2405 | +2878 | -1493 | -679 | -1% / -10% |
| T25 24h any D40 | 7797 | +6259 | +3601 | -243 | -2194 | -32% / +13% | +3315 | +2437 | +2380 | -21 | +3% / -43% |
| T25 4h against D20 | 1739 | +2010 | +720 | +501 | +922 | -20% / -2% | +1452 | +117 | +843 | +1068 | +4% / -6% |
| T25 4h against D40 | 2614 | +3079 | +1851 | +200 | +89 | -23% / -5% | +2275 | +3867 | +1204 | -430 | +3% / -12% |
| T25 4h against D60 | 3032 | +1751 | +887 | +107 | +6 | -24% / -2% | +996 | +1922 | +1321 | +547 | +5% / -8% |
| T25 4h any D20 | 3556 | +2376 | +1209 | -61 | -161 | -22% / -4% | +2222 | +790 | +1430 | -634 | -5% / -14% |
| T25 4h any D40 | 5110 | +3113 | +1912 | -683 | -1029 | -27% / -8% | +2522 | +2437 | +962 | -1102 | -1% / -17% |
| T25 4h any D40 notfresh | 41869 | -2276 | -2537 | -7376 | -927 | -60% / +18% | +4654 | +5410 | -2650 | +636 | +22% / -42% |
| T25 4h any D60 | 5803 | +1476 | +1134 | -855 | -1324 | -19% / -10% | +1177 | +3036 | +1067 | -346 | +9% / -22% |
| T25 4h any P25 | 2812 | +2230 | +1470 | +302 | -884 | -23% / -4% | +2312 | +2382 | +1243 | -538 | -5% / -3% |
| T25 4h any P50 | 4267 | +2292 | +1760 | +144 | -915 | -18% / -8% | +2027 | +2369 | +1523 | -1279 | +8% / -17% |
| T25 4h any P75 | 5185 | +2641 | +1671 | -564 | -1204 | -32% / -8% | +1840 | +3273 | +994 | -1294 | -0% / -20% |
| T25 4h with D20 | 2009 | +490 | +658 | -705 | -479 | -11% / +3% | +1916 | +1299 | -253 | -1807 | +3% / -13% |
| T25 4h with D40 | 2838 | +594 | +562 | -1711 | -774 | -15% / +10% | +1764 | +1209 | -690 | -1466 | -5% / -12% |
| T25 4h with D60 | 3215 | +44 | +852 | -1522 | -605 | -5% / +7% | +1405 | +2683 | -535 | -1466 | +2% / -21% |
| T50 15m any D40 | 689 | +585 | +267 | -323 | -573 | -4% / +1% | -328 | -279 | -104 | -497 | -1% / -11% |
| T50 1h any D40 | 920 | +543 | +156 | -365 | -651 | -3% / +3% | -357 | -257 | +205 | -512 | -1% / -10% |
| T50 24h any D40 | 1975 | +1981 | +1350 | +747 | -736 | -8% / +8% | -150 | +306 | +1285 | -844 | -1% / -18% |
| T50 4h any D20 | 830 | +516 | +261 | -63 | -494 | -7% / -1% | -314 | -111 | +764 | -1303 | -1% / -10% |
| T50 4h any D40 | 1267 | +610 | +246 | +6 | -592 | -7% / +8% | -469 | -53 | +1068 | -1254 | -1% / -12% |
| T50 4h any D60 | 1480 | +131 | -119 | -503 | -560 | -3% / +10% | -776 | -191 | +332 | -1225 | -1% / -7% |

Reading of the grid: the weekly-mean effect needs threshold >= 25 (10 lots fires on 17-38k rows = volume; 100 lots too few rows), grows with the window (15 m +2.2k, 1 h +2.5k, 4 h +2.9k, 24 h +7.1k $/wk in L6M, lock none) and **is carried by prints AGAINST the trade (aggressor opposite to the trade direction: a large SELL print above a long = supply / absorption ahead): against 4 h D40 +2.8k L6M / +1.8k HOLD, WITH the trade +0.3k / +0.4k.** The not-fresh variant (any print of the last 4 h, touched or not) is worse than the base (fresh matters). Pct-of-target reaches 25/50/75% behave like D20-D60.

## 3b. The AGAINST-the-trade variant (`T25|4h|against|D40`: 2,614 rows): row outcome, placebo, walk-forward
| frame | window | delta mean $/wk | MDE | placebo draws | placebo mean | real beats (share) |
|---|---|---|---|---|---|---|
| lock none | L3M | +2819 | +5130 | 100 | -284 | 0.98 |
| lock none | L6M | +3079 | +3595 | 100 | -956 | 1.00 |
| lock none | HOLD | +1851 | +2422 | 100 | -608 | 0.99 |
| lock none | MID | +346 | +5778 | 100 | -101 | 0.59 |
| lock none | PRE | +200 | +2102 | 100 | -405 | 0.78 |
| lock none | X' | +89 | +2540 | 100 | +229 | 0.49 |
| 12R | L3M | +1287 | +2078 | 100 | -740 | 0.89 |
| 12R | L6M | +2275 | +5377 | 100 | -498 | 0.97 |
| 12R | HOLD | +3867 | +5868 | 100 | +855 | 0.99 |
| 12R | MID | +7332 | +16957 | 100 | +1345 | 0.99 |
| 12R | PRE | +1204 | +1825 | 100 | -313 | 0.91 |
| 12R | X' | -430 | +3551 | 100 | -177 | 0.38 |

Row-level realised $ of the skipped rows (V13X taken rows, library of the earlier page): lock none, against: L6M -$559/row (n 128), HOLD -$368 (243), PRE -$346 (230), X' +$45 (148) vs the other rows +$185 / +$178 / +$125 / -$24; with the trade: -$135 / -$93 / **+$266** / +$125. With the combined 12R lock: against PRE -$609 per row. **Prints against the trade lose money in three of four windows (2024-26); prints with the trade do not.**
Walk-forward restricted to the against family (72 settings), 34 months: fixed default `T25 4h against D40` OOS excess $+236780 (t 3.51, 25/34 months positive; 2024 +83778, 2025 +40206, 2026 +112795); the trailing-12-month CHOICE gains less (+87902, t 0.48) because it drifts to the 10-lot volume-heavy settings. The definition is positive in every calendar year when fixed, but fixing it was done on this same data (post-hoc), and tuning it does not help.

## 4. Purged walk-forward on the definition (2024-01..2026-10; engine-free scoring)
Each month the setting (threshold {10,25,50,100} x window {15m,1h,4h,24h} x side {any, against, with} x reach {20,40,60}: 144 settings) is chosen on the trailing 12 months of label days (ending 2 days before the month) by the excess gain of skipping its flagged rows (gain = -sum of V13X realised $ of the flagged TAKEN rows, minus what skipping the same number of random rows costs = n x mean $), >= 80 flagged rows, and applied to the next month. Scoring: V13X realised $ per taken row, lock none (an approximation of the engine skip: no lock / ER re-sequencing).
| policy | months | sum of OOS excess $ | mean per month | t | positive months |
|---|---|---|---|---|---|
| walk-forward choice (trailing 12 m) | 34 | +420120 | +12356 | 2.22 | 20 |
| fixed default T25 4h any D40 | 34 | +219425 | +6454 | 2.51 | 24 |
| random setting each month | 34 | +33982 | +999 | 0.28 | 23 |
* 2024: walk-forward +32360, fixed default +33124, random setting +36916 ($ excess over random skipping).
* 2025: walk-forward +235299, fixed default +41579, random setting +5973 ($ excess over random skipping).
* 2026: walk-forward +152461, fixed default +144722, random setting -8907 ($ excess over random skipping).
Settings chosen most often: T10|4h|with|D40 (6), T10|24h|any|D40 (6), T10|24h|with|D40 (5), T10|24h|with|D60 (5), T10|24h|any|D60 (5), T10|4h|against|D60 (2). Reading: the walk-forward choice and the fixed default both gain in 2025-26 and not in 2024; a RANDOM setting also gains +$157k over the 34 months, i.e. any large-print flag carries part of the effect, and the extra from tuning the definition is small and unstable (2024: -$41k).

## 5. Verdict on the flag test
Flag condition: skipped-row dollar effect positive with the row-level placebo rank <= 0.05 in lock none AND positive in PRE and X' AND surviving the walk-forward. **Not met.** Lock none: real delta beats all 100 random-skip draws in L6M (+$2.9k/wk vs -$0.9k for random; HOLD +$1.9k/wk, CI [+0.3k, +2.8k]; F9 +$2.6k/wk), INSIDE the MDE ($4.3k), but PRE is -$0.4k/wk (beats 70% of random) and X' -$2.3k/wk (beats 10%): the effect is absent before 2025, and it is a London-only, tail-driven effect.

## 6. LIVE definition (what D7 sees from its own print tape) and latency
* D7 keeps a list of prints with size >= 25 contracts (any aggressor side) from its own trade feed: (price, second). A print is usable from the first decision AFTER its second ends.
* At a signal (entry E, side s, target distance td, evaluated at the signal second): the signal is flagged if there is a print of the last 4 h (240 minutes) whose price p satisfies 0 <= s*(p - E) <= min(40, td) AND the price has not traded through p since the print (every trade price after the print on the same side of p, i.e. the instrument has not touched p again; touch = a trade at p or beyond in the direction of the move). Action in Shadow: log the flag; in the research frame: skip.
* Latency: a SKIP is decided at the signal second from state that is already known (prints and touches strictly before the decision second); a 1-s or 3-s decision delay changes the state by at most the prints of those seconds, so the skip is not delay-sensitive (verified for the other cells: delay 1 s/3 s moved the cuts by 0-10 points in the earlier pages). No book data needed; no daily file.
* Forward Shadow log fields (appended to FORWARD_SHADOW_ZONES_SPEC.md): lp_flag, lp_n_prints, lp_nearest_px, lp_nearest_dist, lp_nearest_size, lp_nearest_side, lp_age_s, lp_fresh_since (touch time or none), rule id ZL2_LP25_4H_D40.
