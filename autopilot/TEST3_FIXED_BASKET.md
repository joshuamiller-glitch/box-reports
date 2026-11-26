# TEST 3: a FIXED basket of qualified books, re-qualified slowly, picked for spread (W-TEST3)

**QUICK SCREEN label on every number below** unless it says EXACT: grid weekly arrays (th_grid tape walk, not the exact engine), 1 NQ lot per book at $20/point, grid cost in, no stack rules, no account layers. Order: Josh 18:13Z (autopilot/DIRECTIVE_TEST3_FIXED_BASKET_1818Z.md) plus parts B and C 18:21Z (DIRECTIVE_TEST3_PARTS_BC_1822Z.md), followed word for word: 8 qualification rules x 3 K x 2 schedules x method S = 48 versions per session, plus R and H reference rows, none added. Out of sample 2023-10-01 to 2026-10-25 (160 weeks). Written by W-TEST3. Code code/th_test3, data on server C /mnt/l2/l2vast/_test3.

## ANSWER FIRST (QUICK SCREEN)

1. **FAIL in all four sessions and in the four-session sum.** After the best-of-48 luck penalty the best method-S version is below zero everywhere (Asia -17, London -70, NY AM -88, NY PM -30, four summed -45 $/lot/wk) and the reality-check p-values are 0.71 to 0.97. Only 17 (Asia), 1 (London), 11 (NY AM), 8 (NY PM) of 48 versions earn more than zero at all.
2. **The spread rule (S) makes it worse, not better.** The reference of K random qualified families (R) beats S in Asia (R mean +111 vs S best +78 $/lot/wk; S is above its own random-draw mean in 0 of 48 versions) and NY AM (+77 vs +51); H (top history income per drawdown) and the equal-weight basket of all qualified families (Asia +114, NY AM +71) also match or beat S. In London and NY PM the qualified pool itself loses (equal-weight -44 and -80 $/lot/wk), and S is only less bad than random there. Picking for low correlation picks books that are low-correlated because they trade rarely or badly; it is the qualification (>=30 trades, profitable in past half-years, >=half of the family profitable) that carries whatever edge exists, and only in Asia and NY AM.
3. **PASS/FAIL per session** (PASS = S after best-of-48 haircut above zero with reality-check p <= 0.10): Asia FAIL, London FAIL, NY AM FAIL, NY PM FAIL, four summed FAIL. Nothing passes.
4. **Best versions are not stable.** The best version per session sits on different rules and schedules (table below); the L6M and L3M of the best versions disagree with the whole-period number in London (L3M +205, 2023 Q4 -245) and NY PM (L6M -14, 2025 +406). The equal-weight qualified basket, which has no selection, is the more honest read: Asia +114, NY AM +71 $/lot/wk but with max drawdowns of 3,380 and 5,000+ $/lot.
5. **Part B (brackets only, QUICK SCREEN)**: re-picking the bracket inside each held book (trailing 1, 3 or 6 months, refit 2, 4, 13 weeks, 9 versions) beats the unchanged held cell only in Asia (best 6M/13w: +54 $/lot/wk, after best-of-9 haircut +23, RC p 0.22 = FAIL) and NY AM (+15, after -28, p 0.73); London (-80) and NY PM (-90) are worse. No session passes. Family definition note: the test-2 family is (bar type, module, variant) with all bar sizes, params, brackets and sides, wider than one book; Part B therefore uses the narrower group "same bar type and size, module, variant, params, side, all 17 brackets".
6. **Part C (fittings only)**: not run; set-month count and fleet hours posted as a LEAD NOTE in MORNING.md (about 92,700 set-months, ~90 h at the measured fleet rate) for Josh to decide; nothing queued.
7. **Exact engine**: see the last section (LANDED, all sets 2026-11-26 23:48Z).

### Verdicts (QUICK SCREEN)

| session | best version (by $/wk per unit max DD) | $/lot/wk | best-of-48 haircut | after haircut vs zero | RC p vs zero | verdict | R mean (same config) | H (same config) | EW (same rule/sched) |
|---|---|---|---|---|---|---|---|---|---|
| Asia | T>=60, every half-year, fam>=70%, K=12, 13w | 78 | 95 | -17 | 0.71 | **FAIL** | 111 | 85 | 114 |
| London | T>=30, every half-year, fam>=50%, K=8, 26w | 118 | 188 | -70 | 0.90 | **FAIL** | -49 | -31 | -44 |
| NY AM | T>=30, every half-year, fam>=70%, K=20, 13w | 51 | 164 | -88 | 0.94 | **FAIL** | 77 | 52 | 71 |
| NY PM | T>=60, >=75% of half-years, fam>=50%, K=12, 13w | 114 | 145 | -30 | 0.76 | **FAIL** | -106 | -33 | -80 |
| Four sessions summed | T>=60, >=75% of half-years, fam>=70%, K=41, 26w | 26 | 74 | -45 | 0.97 | **FAIL** | 19 | -19 | -1 |

Rules as run (the order is silent on these, so the choice is marked): walk dates every 13 weeks (26, 39, ... 182 from week 26 = 2023-10-01) or every 26 weeks; qualification at a date uses weeks before it only. Rules: (a) trades to date >= 30 or 60; (b) every fully-past calendar half-year profitable, or >=75% of them (**choice**: 2023 H1 is not a full half-year in the data, so the first counted half-year is 2023 H2, past on 2024-01-01; before that the half-year test passes everything; a half-year with no trades is not profitable); (c) >=50% or >=70% of the stored cells of the family profitable over all history to date. One cell per family = lower-median eligible cell by the test-2 score (mean weekly points / max(max drawdown points, 2.5)). **Choice**: a held book is a cell; it is kept while it still qualifies as a cell under the same rule, dropped when it does not; empty slots are refilled by the same method (S: greedy lowest average weekly-P&L correlation, over all history before the date, with the families already held or chosen, start = most trades to date when nothing is held; R: random from the qualified families, 200 independent chains; H: top history score). Per lot = basket P&L / K (an empty slot is cash); four-session sum = summed P&L / total books. Best version = highest income per unit of max drawdown (drawdown first); the luck penalty uses the best-by-mean version (block bootstrap, block 4 weeks, 2,000 draws, White reality check) as in test 2.

## Answer tables per session (recent first: L3M, L6M, then all, then years)

## Asia (QUICK SCREEN)

| version (rule, K, re-qualify) | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books ever | replaced per date |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S BEST1: T>=60, every half-year, fam>=70%, K=12, 13w | 45 | 11 | 78 | 3646 | -1943 | -79 | 5 | 136 | 142 | 58 | 3.8 |
| S BEST2: T>=60, >=75% of half-years, fam>=70%, K=12, 13w | 99 | 32 | 72 | 3646 | -2008 | -79 | 5 | 141 | 114 | 51 | 3.2 |
| S BEST3: T>=30, every half-year, fam>=70%, K=12, 26w | 45 | 113 | 72 | 4073 | -1574 | -115 | 96 | 131 | 27 | 53 | 6.8 |
| S BEST4: T>=30, every half-year, fam>=70%, K=20, 13w | 55 | 95 | 41 | 3888 | -2701 | -149 | 22 | 78 | 78 | 119 | 8.2 |
| S BEST5: T>=60, every half-year, fam>=50%, K=8, 13w | -13 | -51 | 54 | 5224 | -1818 | -81 | 86 | 76 | 28 | 38 | 2.5 |
| R (random, same rule/K/sched), mean of 200 | 107 | 172 | 111 | 7080 | | | | | | | |
| R 5-95% range | -300 to 500 | -119 to 444 | 24 to 190 | 4635 to 10888 | | | | | | | |
| H (top history income per DD, same rule/K/sched) | 196 | 200 | 85 | 5870 | | | | | | | |
| EQUAL-WEIGHT all qualified families (same rule/sched) | | | 114 | 3380 | | | | | | | |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | |

Over the 48 S versions: positive 17 of 48 (median -14, best 78, worst -130 $/lot/wk); S above the mean of its 200 random draws in 0 of 48; S above H in 6 of 48; S above the equal-weight basket in 0 of 48.
Median $/lot/wk by dimension (48 S versions): min trades: 30 -32, 60 -10; half-year test: every -21, 75% -13; family share: 50% -45, 70% -5; K index: small 5, mid -24, large -38; re-qualify: 13w -4, 26w -38.
Best-of-48 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check): best version by mean 78 $/lot/wk, haircut 95, after **-17**, RC p **0.71**  -> **FAIL**. Versus equal-weight: after -112, p 1.00. Versus H: after -6, p 0.55.

## London (QUICK SCREEN)

| version (rule, K, re-qualify) | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books ever | replaced per date |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S BEST1: T>=30, every half-year, fam>=50%, K=8, 26w | 205 | 198 | 118 | 5987 | -1466 | -245 | 69 | 140 | 261 | 34 | 4.3 |
| S BEST2: T>=30, every half-year, fam>=70%, K=3, 13w | -7 | 188 | -1 | 23506 | -4539 | -217 | 100 | 177 | -283 | 19 | 1.3 |
| S BEST3: T>=60, >=75% of half-years, fam>=50%, K=8, 26w | 159 | 315 | -1 | 14309 | -3157 | -239 | -83 | -26 | 208 | 30 | 3.7 |
| S BEST4: T>=60, >=75% of half-years, fam>=70%, K=8, 26w | -274 | -94 | -9 | 12227 | -3056 | -256 | -29 | 8 | 71 | 30 | 3.7 |
| S BEST5: T>=30, >=75% of half-years, fam>=50%, K=8, 26w | -508 | -329 | -12 | 12495 | -2786 | -245 | 69 | 137 | -226 | 30 | 3.7 |
| R (random, same rule/K/sched), mean of 200 | -241 | -94 | -49 | 17293 | | | | | | | |
| R 5-95% range | -669 to 216 | -407 to 217 | -145 to 68 | 9077 to 27378 | | | | | | | |
| H (top history income per DD, same rule/K/sched) | 59 | -100 | -31 | 7816 | | | | | | | |
| EQUAL-WEIGHT all qualified families (same rule/sched) | | | -44 | 8921 | | | | | | | |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | |

Over the 48 S versions: positive 1 of 48 (median -84, best 118, worst -307 $/lot/wk); S above the mean of its 200 random draws in 16 of 48; S above H in 11 of 48; S above the equal-weight basket in 16 of 48.
Median $/lot/wk by dimension (48 S versions): min trades: 30 -90, 60 -81; half-year test: every -81, 75% -91; family share: 50% -102, 70% -63; K index: small -130, mid -121, large -53; re-qualify: 13w -92, 26w -70.
Best-of-48 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check): best version by mean 118 $/lot/wk, haircut 188, after **-70**, RC p **0.90**  -> **FAIL**. Versus equal-weight: after -29, p 0.66. Versus H: after -61, p 0.81.

## NY AM (QUICK SCREEN)

| version (rule, K, re-qualify) | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books ever | replaced per date |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S BEST1: T>=30, every half-year, fam>=70%, K=20, 13w | 511 | 196 | 51 | 6364 | -1884 | -67 | 13 | -53 | 266 | 130 | 9.2 |
| S BEST2: T>=30, every half-year, fam>=70%, K=8, 26w | -6 | -173 | 76 | 14897 | -3702 | -369 | -114 | 467 | -46 | 36 | 4.7 |
| S BEST3: T>=60, >=75% of half-years, fam>=70%, K=12, 26w | -96 | -158 | 36 | 9823 | -3354 | -40 | 39 | 55 | 30 | 43 | 5.2 |
| S BEST4: T>=30, every half-year, fam>=70%, K=12, 13w | 391 | 339 | 35 | 11148 | -2251 | -222 | -4 | -2 | 208 | 76 | 5.3 |
| S BEST5: T>=60, >=75% of half-years, fam>=50%, K=20, 26w | 476 | 184 | 24 | 11921 | -2227 | -7 | -171 | 186 | 71 | 66 | 7.7 |
| R (random, same rule/K/sched), mean of 200 | 187 | -168 | 77 | 17688 | | | | | | | |
| R 5-95% range | -140 to 533 | -501 to 100 | -34 to 183 | 10398 to 25713 | | | | | | | |
| H (top history income per DD, same rule/K/sched) | -118 | -25 | 52 | 4493 | | | | | | | |
| EQUAL-WEIGHT all qualified families (same rule/sched) | | | 71 | 16010 | | | | | | | |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | |

Over the 48 S versions: positive 11 of 48 (median -40, best 76, worst -204 $/lot/wk); S above the mean of its 200 random draws in 0 of 48; S above H in 16 of 48; S above the equal-weight basket in 1 of 48.
Median $/lot/wk by dimension (48 S versions): min trades: 30 -31, 60 -54; half-year test: every -24, 75% -62; family share: 50% -45, 70% -34; K index: small -19, mid -60, large -38; re-qualify: 13w -47, 26w -31.
Best-of-48 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check): best version by mean 76 $/lot/wk, haircut 164, after **-88**, RC p **0.94**  -> **FAIL**. Versus equal-weight: after -164, p 0.99. Versus H: after -84, p 0.88.

## NY PM (QUICK SCREEN)

| version (rule, K, re-qualify) | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books ever | replaced per date |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S BEST1: T>=60, >=75% of half-years, fam>=50%, K=12, 13w | 6 | -14 | 114 | 7895 | -2333 | 80 | -33 | 406 | -62 | 54 | 3.5 |
| S BEST2: T>=60, >=75% of half-years, fam>=70%, K=12, 26w | 442 | 397 | 114 | 8193 | -1990 | 279 | -58 | 50 | 357 | 51 | 6.5 |
| S BEST3: T>=60, every half-year, fam>=50%, K=12, 13w | -385 | -183 | 107 | 7895 | -1724 | 80 | -33 | 410 | -92 | 58 | 3.8 |
| S BEST4: T>=60, >=75% of half-years, fam>=50%, K=12, 26w | 89 | -1 | 56 | 7148 | -1848 | 80 | -77 | 96 | 163 | 43 | 5.2 |
| S BEST5: T>=60, every half-year, fam>=70%, K=8, 13w | -88 | 144 | 94 | 13835 | -4137 | 485 | -169 | 170 | 203 | 48 | 3.3 |
| R (random, same rule/K/sched), mean of 200 | -76 | -68 | -106 | 23502 | | | | | | | |
| R 5-95% range | -499 to 351 | -414 to 223 | -204 to -4 | 11226 to 36341 | | | | | | | |
| H (top history income per DD, same rule/K/sched) | 87 | 98 | -33 | 15809 | | | | | | | |
| EQUAL-WEIGHT all qualified families (same rule/sched) | | | -80 | 13964 | | | | | | | |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | |

Over the 48 S versions: positive 8 of 48 (median -99, best 114, worst -243 $/lot/wk); S above the mean of its 200 random draws in 20 of 48; S above H in 10 of 48; S above the equal-weight basket in 20 of 48.
Median $/lot/wk by dimension (48 S versions): min trades: 30 -121, 60 -42; half-year test: every -109, 75% -81; family share: 50% -110, 70% -80; K index: small -116, mid -42, large -142; re-qualify: 13w -77, 26w -115.
Best-of-48 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check): best version by mean 114 $/lot/wk, haircut 145, after **-30**, RC p **0.76**  -> **FAIL**. Versus equal-weight: after 52, p 0.15. Versus H: after 11, p 0.44.

## Four sessions summed (QUICK SCREEN)

| version (rule, K, re-qualify) | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books ever | replaced per date |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S BEST1: T>=60, >=75% of half-years, fam>=70%, K=41, 26w | 74 | 23 | 26 | 4602 | -1479 | 7 | -17 | 26 | 86 | 177 | 22.7 |
| S BEST2: T>=60, every half-year, fam>=70%, K=27, 13w | 45 | 41 | 30 | 7234 | -2404 | 76 | -89 | 139 | 25 | 168 | 11.8 |
| S BEST3: T>=30, every half-year, fam>=70%, K=41, 13w | 176 | 79 | 2 | 5307 | -902 | -91 | -49 | 16 | 78 | 241 | 16.7 |
| S BEST4: T>=60, every half-year, fam>=50%, K=41, 13w | -243 | -160 | -3 | 6040 | -1344 | 0 | -24 | 68 | -66 | 199 | 13.2 |
| S BEST5: T>=30, every half-year, fam>=70%, K=68, 13w | 179 | 25 | -5 | 5979 | -992 | -108 | -26 | -6 | 54 | 441 | 31.1 |
| R (random, same rule/K/sched), mean of 200 | 51 | -34 | 19 | 7015 | | | | | | | |
| R 5-95% range | -159 to 264 | -221 to 138 | -41 to 83 | 4026 to 10942 | | | | | | | |
| H (top history income per DD, same rule/K/sched) | -35 | 52 | -19 | 6011 | | | | | | | |
| EQUAL-WEIGHT all qualified families (same rule/sched) | | | -1 | 4244 | | | | | | | |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | |

Over the 48 S versions: positive 3 of 48 (median -60, best 30, worst -111 $/lot/wk); S above the mean of its 200 random draws in 1 of 48; S above H in 6 of 48; S above the equal-weight basket in 2 of 48.
Median $/lot/wk by dimension (48 S versions): min trades: 30 -69, 60 -45; half-year test: every -65, 75% -55; family share: 50% -71, 70% -45; K index: small -64, mid -40, large -65; re-qualify: 13w -45, 26w -70.
Best-of-48 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check): best version by mean 30 $/lot/wk, haircut 74, after **-45**, RC p **0.97**  -> **FAIL**. Versus equal-weight: after -47, p 0.95. Versus H: after -44, p 0.91.

## T1. THE BASKET TODAY (best rule per session; QUICK SCREEN; held as of the last data date 2026-10-25, last re-qualify date week 182 = 2026-09-27)

"Already coded in D8Asia.cs": **relay to confirm** for every row (not stated in the spec pages). "Near-twin of a live book": same family (bar type, module, variant) as a live book of the session, or weekly-P&L correlation >= 0.7 with one (all history). "Still qualifies" = the cell passes the best rule on data to 2026-10-25. Income is $ per lot per week of the grid cell (calendar year, 2023 = Apr-Dec, 2026 = Jan-Oct).


**Asia**: rule T>=60, every half-year, family>=70%, K=12, re-qualify 13 weeks.

| book id (set TL3_ALN_.._<id>_R0RT) | trigger (module, variant, params) | bar type | bracket (side) | family size | trades | 2023 | 2024 | 2025 | 2026 | still qualifies | D8Asia.cs | near-twin of a live book |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W8e76ce73 | trig_levels_profile_nodes retest_native {"M": 6, "tol": 0.5} | trend_40 | plain60/60 (long) | 432 | 682 | 73 | 353 | 114 | 405 | True | relay to confirm | none |
| W1e5d2da3 | trig_pullback_brick brick {"k": 4, "m": 1} | tsf_5_50 | plain60/60 (both) | 108 | 1253 | 206 | 348 | 801 | 292 | True | relay to confirm | none |
| W7dceb5a3 | trig_manual_volprofile va_fade {"va": 0.7, "buf": 0.0} | dol_6000 | sym15u (short) | 36 | 142 | 30 | 111 | 133 | 133 | True | relay to confirm | none |
| W0fca2b13 | trig_pullback_brick brick {"k": 5, "m": 3} | tsf_25_150 | sym15u (both) | 108 | 172 | 29 | 76 | 225 | -66 | True | relay to confirm | none |
| W35706780 | trig_levels_ob5 retest_native {"M": 10, "tol": 0.0} | dol_350 | fixed40/80 (short) | 342 | 292 | 156 | 56 | 169 | 352 | True | relay to confirm | none |
| Wdc05d8f3 | trig_levels_fib60 break {"n": 3, "k": 0.5} | dol_6000 | fixed120/60 (short) | 495 | 358 | -44 | 67 | 112 | 621 | True | relay to confirm | none |
| W7c110f00 | trig_confluence_user sq_macd {"k": 2, "w": 6} | wrenko_10 | sym15u (both) | 54 | 486 | -3 | 165 | 418 | 186 | True | relay to confirm | none |
| W040c0512 | trig_tape_absorb fade_native {"a": 0.15, "r": 0.6, "q": 1.0, "L": 1800} | dol_500 | plain60/60 (both) | 34 | 260 | 11 | 93 | 164 | 243 | False | relay to confirm | none |
| Wa4b9d9db | trig_levels_ob15 reject {"tol": 0.5, "conf": "body"} | wrenko_10 | sym15u (both) | 54 | 232 | 43 | 244 | 169 | -217 | True | relay to confirm | none |
| Wc53262f2 | trig_levels_round retest {"M": 10, "tol": 0.0} | drb_25000 | fixed80/40 (long) | 306 | 88 | 14 | 46 | 100 | 158 | True | relay to confirm | none |
| W5a406bf5 | trig_manual_sesslevel asia_reject {"buf": 0.5} | time_s_45 | sym8u (long) | 126 | 94 | 43 | 28 | 46 | -104 | False | relay to confirm | none |
| W8646c002 | trig_trend_ma_sma price {"len": 10, "width": 0.0} | cdr_160 | fixed120/60 (long) | 612 | 759 | 29 | 147 | 278 | -66 | True | relay to confirm | none |

**London**: rule T>=30, every half-year, family>=50%, K=8, re-qualify 26 weeks.

| book id (set TL3_ALN_.._<id>_R0RT) | trigger (module, variant, params) | bar type | bracket (side) | family size | trades | 2023 | 2024 | 2025 | 2026 | still qualifies | D8Asia.cs | near-twin of a live book |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Wfd54f9dd | trig_levels_open_range false_break {"M": 1, "k": 0.0} | sessrng_B050 | plain60/60 (long) | 126 | 300 | -28 | 184 | 571 | 10 | True | relay to confirm | none |
| W0996e651 | trig_levels_swsr5 false_break {"M": 1, "k": 0.0} | tib_3500 | sym8u (both) | 1008 | 1677 | 446 | 596 | 315 | 650 | True | relay to confirm | none |
| W25a17390 | trig_levels_sdx30 lim_mid {"d": "E", "F": 9, "tgt": "r2"} | tsf_10_120 | sym15u (both) | 108 | 998 | 412 | 431 | 460 | 430 | True | relay to confirm | none |
| Wc248b1e6 | trig_barnative_run cont {"n": 4} | tsf_25_150 | sym15u (long) | 108 | 79 | 77 | 52 | 50 | 300 | True | relay to confirm | none |
| Wad6d5036 | trig_book_wall appear_fade {"m": 3} | lbrk_3_20 | plain60/60 (both) | 54 | 1807 | -66 | 183 | 259 | 840 | True | relay to confirm | none |
| Wa8c4e8f4 | trig_live_seven H7 {"live": 1} | renko_10 | sym8u (short) | 102 | 277 | 68 | 56 | 121 | 16 | True | relay to confirm | none |
| Wdaa8a6f1 | trig_momentum_rsi revert {"len": 14, "lvl": 25} | renko_14 | fixed90/30 (both) | 1802 | 506 | 107 | 243 | 63 | 22 | True | relay to confirm | none |
| W9efa20cc | trig_xmarket_rates with_ZN {"w": 15, "thr": 2.0} | tsf_2_100 | fixed90/30 (both) | 612 | 1500 | 348 | 255 | 219 | 934 | True | relay to confirm | none |

**NY AM**: rule T>=30, every half-year, family>=70%, K=20, re-qualify 13 weeks.

| book id (set TL3_ALN_.._<id>_R0RT) | trigger (module, variant, params) | bar type | bracket (side) | family size | trades | 2023 | 2024 | 2025 | 2026 | still qualifies | D8Asia.cs | near-twin of a live book |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W5635c983 | trig_levels_vwap retest {"M": 3, "tol": 0.5} | anch_L0200_B50 | sym8u (both) | 306 | 1146 | 46 | 1145 | 454 | 1151 | True | relay to confirm | none |
| Wf64efa1c | trig_bands_bollinger walk {"n": 20, "k": 2.0, "N": 2} | pasl_10 | fixed60/120 (long) | 1088 | 165 | 402 | 25 | 399 | 227 | False | relay to confirm | none |
| Wff83903d | trig_book_cancel canc_follow {"L": 200, "z": 1.0} | lbrk_3_20 | asym15u/30u (long) | 495 | 1108 | 7 | 678 | 686 | 1252 | True | relay to confirm | none |
| W9dc7b76f | trig_levels_prior_day false_break {"M": 1, "k": 0.5} | renko_20 | fixed80/40 (short) | 1530 | 869 | 98 | 274 | 594 | 336 | True | relay to confirm | none |
| Wdcc61d45 | trig_book_queue follow_sm {"thr": 0.3, "min": 3, "sm": 3} | t3_micro_B200 | sym15u (both) | 36 | 813 | 590 | 600 | 741 | 909 | True | relay to confirm | none |
| We4580646 | trig_confluence_xfam squeezeflow {"k": 2, "w": 6} | dchg_20 | fixed120/60 (both) | 306 | 290 | 176 | 106 | 333 | 886 | True | relay to confirm | none |
| W181285c6 | trig_confluence_user sq_macd {"k": 2, "w": 6} | dchg_28 | fixed90/30 (long) | 153 | 753 | 266 | 148 | 251 | 279 | True | relay to confirm | none |
| Wb3fd8546 | trig_tape_stoprun fade {"N": 20, "k": 0.25} | typ_volor_B200 | plain60/60 (short) | 36 | 2573 | -38 | 209 | 454 | -740 | True | relay to confirm | none |
| Wec82a8fa | trig_confluence_user sq_lvl {"k": 2, "w": 3} | vfp_rng40 | sym15u (long) | 18 | 188 | 399 | 200 | 239 | 358 | True | relay to confirm | none |
| Wf5777ed1 | trig_levels_piv_floor reject {"tol": 1.0, "conf": "body"} | lbrk_3_10 | plain60/60 (short) | 54 | 1566 | 112 | 442 | 716 | 24 | True | relay to confirm | none |
| Wba4ec13f | trig_levels_book_walls_loose retest {"M": 10, "tol": 0.0} | time_s_10 | fixed80/40 (both) | 864 | 1150 | 240 | 567 | 376 | 517 | True | relay to confirm | none |
| W4d7aa6c7 | trig_manual_sesslevel asia_reject {"buf": 0.25} | tm300 | asym20u/10u (long) | 315 | 202 | -19 | 103 | 99 | 512 | True | relay to confirm | none |
| W11a0c742 | trig_levels_round reject {"tol": 0.5, "conf": "body"} | drb_25000 | asym20u/10u (short) | 612 | 401 | 90 | 216 | 176 | 271 | True | relay to confirm | none |
| W5020f494 | trig_levels_book_walls_loose false_break_native {"M": 2, "k": 0.5} | frenko_28 | plain60/60 (both) | 36 | 424 | -128 | 312 | 184 | 133 | True | relay to confirm | none |
| W257d2755 | trig_levels_profile_va reject_native {"tol": 0.0, "conf": "close"} | vib_3500 | plain60/60 (both) | 36 | 1994 | -75 | 277 | 623 | 697 | True | relay to confirm | none |
| W1f1d2282 | trig_barnative_absorb absorb {"len": 50, "dz": 1.5, "prog": 0.25} | tpo_30m | plain60/60 (long) | 18 | 155 | -94 | 168 | 107 | 286 | True | relay to confirm | none |
| Wf1ec8777 | trig_levels_swsr60 reject {"tol": 1.0, "conf": "close"} | anch_N0930_B10 | fixed45/45 (both) | 306 | 1085 | 107 | 157 | 66 | -134 | True | relay to confirm | none |
| Wbead28e8 | trig_levels_channel retest_native {"M": 10, "tol": 0.0} | time_s_15 | sym30u (both) | 306 | 1912 | 1110 | 1313 | 387 | 763 | True | relay to confirm | none |
| Wb0e36f88 | trig_levels_round retest_native {"M": 6, "tol": 0.0} | t3_qmid_B080 | fixed90/30 (long) | 324 | 2213 | 537 | 248 | 516 | 526 | False | relay to confirm | none |
| W32d986c1 | trig_levels_fvg15 retest {"M": 6, "tol": 0.5} | time_m_4 | fixed30/30 (both) | 306 | 949 | -139 | 181 | 99 | -87 | False | relay to confirm | none |

**NY PM**: rule T>=60, >=75% of half-years, family>=50%, K=12, re-qualify 13 weeks.

| book id (set TL3_ALN_.._<id>_R0RT) | trigger (module, variant, params) | bar type | bracket (side) | family size | trades | 2023 | 2024 | 2025 | 2026 | still qualifies | D8Asia.cs | near-twin of a live book |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W560b2806 | trig_levels_round false_break_native {"M": 1, "k": 0.0} | t3_micro_B080 | plain60/60 (short) | 36 | 1590 | 273 | 597 | 524 | 507 | True | relay to confirm | none |
| Wf9d1f600 | trig_barnative_avwap fade {"anchor": "day", "k": 2.0} | tm600 | sym15u (long) | 1674 | 206 | 179 | 200 | 631 | -268 | True | relay to confirm | none |
| We1cd7c87 | trig_levels_trendline reject_native {"tol": 1.0, "conf": "body"} | volor_B500 | fixed120/60 (both) | 414 | 1880 | 1249 | 133 | 1243 | 1554 | True | relay to confirm | none |
| W8a6ae11d | trig_xmarket_mega diverge {"w": 5} | vfp_t15m | sym15u (both) | 18 | 1189 | 626 | 404 | 790 | -429 | True | relay to confirm | none |
| W39dbe8fb | trig_book_dwm dev_follow_native {"L": 3600, "z": 2.0} | t3_bmsg_B080 | plain60/60 (both) | 36 | 892 | 5 | 376 | 32 | 402 | True | relay to confirm | none |
| Wdea9ad2a | trig_book_ofi norm_follow {"L": 100, "z": 1.5} | t3_micro_B200 | fixed60/120 (long) | 477 | 1303 | 282 | 467 | 937 | -445 | True | relay to confirm | none |
| We04f7d63 | trig_book_imb follow_sm {"lv": 5, "thr": 0.35, "sm": 4} | rngor_B320 | fixed90/30 (both) | 408 | 466 | 241 | 201 | 13 | 190 | True | relay to confirm | none |
| Wb8fcf173 | trig_levels_sdx_renko28 retest {"d": "E", "M": 6, "tol": 0.5} | vfp_vol2500 | sym15u (short) | 12 | 386 | -146 | 506 | 63 | 15 | True | relay to confirm | none |
| W2bafc3eb | trig_levels_trendline retest_native {"M": 3, "tol": 0.0} | vfp_vol2500 | sym15u (long) | 18 | 531 | 190 | 201 | -184 | -35 | True | relay to confirm | none |
| W5435994a | trig_book_cancel canc_follow {"L": 50, "z": 1.5} | kagi_20 | sym8u (both) | 2331 | 1986 | -467 | 420 | 110 | 1465 | True | relay to confirm | none |
| Wa9ae2b6e | trig_levels_sdx3 rej {"d": "E", "F": 9, "tol": 0.5} | urenko_80 | sym15u (long) | 90 | 172 | 73 | 261 | -32 | 84 | True | relay to confirm | none |
| W9806114b | trig_levels_swcluster reject {"tol": 0.0, "conf": "close"} | volor_B080 | fixed80/40 (both) | 1278 | 481 | 90 | 141 | 374 | 88 | True | relay to confirm | none |

Because the best-of-48 versions FAIL, T1 is the basket the best-looking version would hold; it is not a recommendation. Held books change at every re-qualify date (see replaced per date in the session tables).

## T2. THE 20 LIVE BOOKS under the same rules (QUICK SCREEN)

Mapping: the 20 live books are the D8 stack members used by W-ROTA (autopilot/ROTATION_STAGE_A.md, fixed_spec.json: Asia 4, London 3, NY AM 9, NY PM 4). **Mapped to a grid cell: 17. Could not be mapped (no grid cell, not guessed): Asia L385f4f2e_CX502, NY AM B7bfd33b7, NY AM Bf428c4a1.BRS8U.** "First date qualified" = the first re-qualify date (of the best rule and schedule of its session) at which the cell passes; "weekly" = first week on which it would have passed if checked every week. Result AFTER = $/lot/wk of the cell from that date to 2026-10-25 only; "while held" = only the periods starting at a re-qualify date where it passes. "oos all" = whole out-of-sample for context.

| session | live book | first date qualified (rule of the session) | first weekly | dates qualified of | result AFTER $/lot/wk (weeks) | L6M | L3M | max DD after | while held $/lot/wk (weeks) | oos all | state at last date (trades, bad half-years of, family share) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | Lb0e6dfa3_R0_F40_80 | never | never | 0 of 13 | - | - | - | - | - | 562 | 1137, 0 of 6, 0.53 |
| Asia | L385f4f2e_CX502 | not mapped to a grid cell | | | | | | | | | |
| Asia | L9c2622b0_R0_P45 | 2025-06-29 | 2025-06-15 | 1 of 13 | 535 (69) | 555 | 674 | 10773 | 802 (13) | 540 | 1267, 0 of 6, 0.66 |
| Asia | L4aaacdb2_R0_P30 | 2024-09-29 | 2024-01-28 | 6 of 13 | 410 (108) | 582 | 669 | 4930 | 371 (78) | 321 | 1126, 0 of 6, 0.71 |
| London | L19201dfc.BRF90_30 | 2024-03-31 | 2023-11-12 | 2 of 7 | 559 (134) | 1759 | 1041 | 9260 | 289 (52) | 539 | 1180, 1 of 6, 0.73 |
| London | L12842dde.BRP45 | never | 2024-02-04 | 0 of 7 | - | - | - | - | - | 88 | 1957, 3 of 6, 0.29 |
| London | L74274eca.BRF120_60 | 2023-10-01 | 2023-05-14 | 1 of 7 | 831 (160) | 1494 | 2269 | 14478 | 857 (26) | 831 | 1900, 2 of 6, 0.62 |
| NY AM | L43f0cbfb.BRS8U | 2023-10-01 | 2023-08-20 | 2 of 13 | 943 (160) | 2359 | 2627 | 26807 | 730 (26) | 943 | 841, 2 of 6, 0.85 |
| NY AM | B7bfd33b7 | not mapped to a grid cell | | | | | | | | | |
| NY AM | Bf428c4a1.BRS8U | not mapped to a grid cell | | | | | | | | | |
| NY AM | Le4fede95.BRF90_30 | 2023-10-01 | 2023-04-23 | 2 of 13 | 712 (160) | 2981 | 2353 | 38080 | 136 (26) | 712 | 3595, 2 of 6, 0.81 |
| NY AM | Lf0346d55.BRP60 | 2023-10-01 | 2023-05-07 | 12 of 13 | 709 (160) | 1073 | 1196 | 38442 | 655 (147) | 709 | 2874, 0 of 6, 0.82 |
| NY AM | L8cfda948.BRF90_30 | 2023-12-31 | 2023-05-28 | 7 of 13 | 649 (147) | 1660 | 825 | 48332 | 358 (91) | 689 | 2471, 1 of 6, 0.92 |
| NY AM | L4407508c.BRF120_60 | never | 2023-10-15 | 0 of 13 | - | - | - | - | - | 631 | 822, 1 of 6, 0.75 |
| NY AM | L39287638.BRF80_40 | 2025-03-30 | 2025-03-16 | 5 of 13 | 431 (82) | 1004 | 591 | 11011 | 402 (65) | 585 | 957, 0 of 6, 0.66 |
| NY AM | L64390867.BRF80_40 | 2024-09-29 | 2024-08-04 | 1 of 13 | 263 (108) | 287 | 191 | 11680 | -367 (13) | 188 | 644, 1 of 6, 0.70 |
| NY PM | L52359bf4_R0_P30 | never | 2023-05-07 | 0 of 13 | - | - | - | - | - | 308 | 3793, 3 of 6, 0.43 |
| NY PM | L8e0bf58c_R0_S8U | 2023-10-01 | 2023-09-03 | 6 of 13 | 344 (160) | 1274 | 1934 | 30824 | -97 (78) | 344 | 683, 3 of 6, 0.52 |
| NY PM | L4bdd521a_R0_F80_40 | 2023-10-01 | 2023-06-18 | 6 of 13 | 521 (160) | 720 | 694 | 16364 | 431 (78) | 521 | 1253, 2 of 6, 0.56 |
| NY PM | L2c6916a5_R0_P60 | 2024-09-29 | 2024-08-25 | 7 of 13 | 252 (108) | 791 | 792 | 16163 | 195 (82) | 491 | 2037, 1 of 6, 0.57 |

In D8Asia.cs? **relay to confirm** (not stated in the spec pages).

## T3. SESSION SIZE from the out-of-sample curve of the best basket (QUICK SCREEN; not the last 6 months)

Per book-lot = the basket P&L divided by K (1 lot per book). Whole basket = K books at 1 lot each. The best baskets FAIL the luck test, so these are the numbers a basket would have had, not a sizing recommendation. Lots by drawdown budget = floor(budget / basket max drawdown).

| session | K | income $/lot/wk | max DD $/lot | worst wk $/lot | ulcer $/lot | whole basket $/wk | whole basket max DD $ | whole basket worst wk $ | basket-lots at 10,000 $ DD | at 20,000 $ DD |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 12 | 78 | 3646 | -1943 | 1058 | 930 | 43748 | -23314 | 0.2 | 0.5 |
| London | 8 | 118 | 5987 | -1466 | 2380 | 941 | 47897 | -11726 | 0.2 | 0.4 |
| NY AM | 20 | 51 | 6364 | -1884 | 3115 | 1021 | 127276 | -37675 | 0.1 | 0.2 |
| NY PM | 12 | 114 | 7895 | -2333 | 3104 | 1370 | 94745 | -27998 | 0.1 | 0.2 |

## PART B (brackets only; QUICK SCREEN): re-pick the bracket inside each held book of the best S basket

Group = same bar type and size, module, variant, params, side, all 17 brackets (the test-2 family is wider; see answer 5). Score = trailing income per drawdown (floor 2.5 points) over 4, 13, 26 weeks; refit 2, 4, 13 weeks (9 versions); reference = the held cell unchanged. Difference = versions minus reference, $/lot/wk.

| session | lookback / refit | diff vs held cell $/lot/wk | $/lot/wk | max DD $/lot | worst wk | L6M | L3M | 2023 Q4 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 4w / 2w | -5 | 73 | 4414 | -1470 | -95 | -19 | -29 | 72 | 165 | -12 |
| Asia | 4w / 4w | -66 | 11 | 7561 | -1512 | -267 | -268 | -34 | 62 | 91 | -138 |
| Asia | 4w / 13w | 3 | 81 | 4423 | -1675 | -125 | -50 | -36 | 112 | 143 | 0 |
| Asia | 13w / 2w | 28 | 105 | 2898 | -1489 | 0 | 34 | -51 | 164 | 123 | 59 |
| Asia | 13w / 4w | 6 | 84 | 4204 | -1658 | -31 | 75 | -54 | 145 | 83 | 51 |
| Asia | 13w / 13w | 33 | 111 | 3481 | -1471 | -37 | -16 | -21 | 147 | 119 | 97 |
| Asia | 26w / 2w | 45 | 123 | 2394 | -1570 | 43 | 56 | -44 | 159 | 130 | 121 |
| Asia | 26w / 4w | 35 | 112 | 2469 | -1529 | 58 | 123 | -65 | 135 | 92 | 164 |
| Asia | 26w / 13w | 54 | 131 | 2581 | -1201 | 38 | 165 | -92 | 143 | 143 | 171 |
| Asia | REFERENCE held cell | 0 | 78 | 3646 | -1943 | 11 | 45 | -79 | 5 | 136 | 142 |
| London | 4w / 2w | -90 | 27 | 9899 | -1839 | 221 | 197 | 5 | -136 | 83 | 166 |
| London | 4w / 4w | -124 | -6 | 9305 | -2182 | 31 | 89 | -13 | -119 | 30 | 89 |
| London | 4w / 13w | -164 | -46 | 12430 | -1839 | 43 | 24 | -203 | -149 | 56 | 0 |
| London | 13w / 2w | -117 | 1 | 9586 | -2351 | -125 | 87 | 10 | 39 | 21 | -76 |
| London | 13w / 4w | -146 | -28 | 11721 | -2351 | -126 | 51 | 3 | 24 | -42 | -84 |
| London | 13w / 13w | -86 | 31 | 9834 | -2150 | 117 | 448 | 36 | -92 | 136 | 49 |
| London | 26w / 2w | -151 | -34 | 13854 | -2516 | -67 | 174 | 61 | -86 | -1 | -40 |
| London | 26w / 4w | -130 | -12 | 9684 | -1980 | 5 | 271 | 62 | -33 | -8 | -15 |
| London | 26w / 13w | -80 | 38 | 7976 | -1609 | -45 | 251 | 40 | 35 | 72 | -2 |
| London | REFERENCE held cell | 0 | 118 | 5987 | -1466 | 198 | 205 | -245 | 69 | 140 | 261 |
| NY AM | 4w / 2w | -71 | -20 | 9635 | -1933 | 123 | 181 | -101 | -4 | -121 | 114 |
| NY AM | 4w / 4w | -64 | -13 | 10422 | -1690 | 32 | 123 | -115 | -50 | -31 | 89 |
| NY AM | 4w / 13w | -99 | -48 | 11905 | -2198 | -84 | -87 | 78 | 31 | -133 | -78 |
| NY AM | 13w / 2w | 13 | 64 | 5207 | -2101 | 361 | 386 | -100 | 55 | -67 | 290 |
| NY AM | 13w / 4w | 15 | 66 | 3449 | -1972 | 290 | 426 | -61 | 84 | -50 | 232 |
| NY AM | 13w / 13w | -25 | 26 | 10168 | -2101 | 253 | 390 | -13 | 38 | -153 | 247 |
| NY AM | 26w / 2w | -1 | 50 | 7777 | -2052 | 439 | 427 | -155 | 8 | -88 | 341 |
| NY AM | 26w / 4w | 9 | 60 | 6715 | -1854 | 357 | 406 | -216 | -4 | -42 | 352 |
| NY AM | 26w / 13w | -59 | -8 | 12062 | -2052 | 199 | 377 | -124 | -9 | -151 | 208 |
| NY AM | REFERENCE held cell | 0 | 51 | 6364 | -1884 | 196 | 511 | -67 | 13 | -53 | 266 |
| NY PM | 4w / 2w | -95 | 19 | 16118 | -1848 | -447 | -525 | -52 | -39 | 378 | -339 |
| NY PM | 4w / 4w | -154 | -40 | 12652 | -2534 | -202 | -239 | -34 | -181 | 236 | -215 |
| NY PM | 4w / 13w | -153 | -39 | 14255 | -2600 | -182 | -208 | 50 | 37 | -47 | -152 |
| NY PM | 13w / 2w | -118 | -4 | 12353 | -2397 | 80 | 2 | -109 | -51 | 57 | 11 |
| NY PM | 13w / 4w | -180 | -66 | 17291 | -4282 | 182 | 111 | -139 | -107 | -73 | 16 |
| NY PM | 13w / 13w | -118 | -4 | 10028 | -3363 | 104 | -2 | -167 | -101 | 88 | 50 |
| NY PM | 26w / 2w | -90 | 25 | 7305 | -2437 | 77 | -108 | -56 | -22 | 102 | 9 |
| NY PM | 26w / 4w | -96 | 18 | 5989 | -1958 | 11 | -161 | -56 | -41 | 154 | -58 |
| NY PM | 26w / 13w | -109 | 5 | 10955 | -2893 | -271 | -134 | -26 | 64 | 78 | -150 |
| NY PM | REFERENCE held cell | 0 | 114 | 7895 | -2333 | -14 | 6 | 80 | -33 | 406 | -62 |

Best-of-9 luck penalty vs the held cell: Asia best 26/13w diff +54, haircut 30, after **+23**, RC p 0.22 -> **FAIL**; London best 26/13w diff -80, haircut 50, after **-130**, RC p 1.00 -> **FAIL**; NY AM best 13/4w diff +15, haircut 43, after **-28**, RC p 0.73 -> **FAIL**; NY PM best 26/2w diff -90, haircut 71, after **-161**, RC p 0.99 -> **FAIL**.

## PART C (fittings only): NOT RUN. Count posted in MORNING.md (LEAD NOTE): 276 books x 8 menu settings x 42 months = 92,736 set-months (~90 h at the measured fleet rate), awaiting a decision; nothing queued.

## EXACT ENGINE: calibration of the quick screen

**(iii) The live books, bare R0, all months, exact vs quick screen (same books, same weeks 2023-04 to 2026-10; existing full bare R0 sets TL3_ALN_<S>_<id>_R0BR<bracket>, 1 lot, own bracket, fees in; nothing new run)**

| session | live book | exact $/lot/wk | quick $/lot/wk | exact / quick | exact L6M | quick L6M | weekly correlation |
|---|---|---|---|---|---|---|---|
| Asia | Lb0e6dfa3_R0_F40_80 | 1010 | 501 | 2.02 | 3333 | 1218 | 0.66 |
| Asia | L9c2622b0_R0_P45 | 795 | 482 | 1.65 | 2018 | 555 | 0.64 |
| Asia | L4aaacdb2_R0_P30 | 265 | 313 | 0.84 | 672 | 582 | 0.92 |
| London | L19201dfc.BRF90_30 | 447 | 486 | 0.92 | 1782 | 1759 | 0.97 |
| London | L12842dde.BRP45 | 513 | 105 | 4.87 | 1402 | 522 | 0.70 |
| London | L74274eca.BRF120_60 | 589 | 717 | 0.82 | 1535 | 1494 | 0.79 |
| NYAM | L43f0cbfb.BRS8U | 1558 | 843 | 1.85 | 4086 | 2359 | 0.69 |
| NYAM | Le4fede95.BRF90_30 | 785 | 775 | 1.01 | 2888 | 2981 | 0.92 |
| NYAM | Lf0346d55.BRP60 | 728 | 590 | 1.23 | 1503 | 1073 | 0.95 |
| NYAM | L8cfda948.BRF90_30 | 745 | 656 | 1.14 | 2308 | 1660 | 0.80 |
| NYAM | L4407508c.BRF120_60 | 610 | 520 | 1.17 | 1566 | 1405 | 0.94 |
| NYAM | L39287638.BRF80_40 | 496 | 564 | 0.88 | 1080 | 1004 | 0.93 |
| NYAM | L64390867.BRF80_40 | 333 | 197 | 1.69 | 448 | 287 | 0.92 |
| NYPM | L52359bf4_R0_P30 | 652 | 278 | 2.35 | 1307 | 891 | 0.93 |
| NYPM | L8e0bf58c_R0_S8U | 486 | 393 | 1.24 | 1279 | 1274 | 0.88 |
| NYPM | L4bdd521a_R0_F80_40 | 602 | 526 | 1.14 | 784 | 720 | 0.97 |
| NYPM | L2c6916a5_R0_P60 | 429 | 443 | 0.97 | 1130 | 791 | 0.93 |

17 live books: exact is on average 1.52 x the quick screen (median ratio 1.17); weekly correlation median 0.92. The quick screen is therefore a ranking-grade, not a level-grade, measure of a book (levels differ by tens of percent either way; the quick screen misses the exact engine's fills and rollover handling). Mapped to a grid cell: 17 of 20 (missing L385f4f2e_CX502, B7bfd33b7, Bf428c4a1.BRS8U; the exact sets exist for the last of these but it has no grid cell to compare). The grid cell is W-ROTA's identification of the live definition and can differ from the live file.

**(i) Asia best: 58 of 58 picks landed (160 weeks)**: exact $/lot/wk 45 (max DD 4365, worst -1547, L6M 114, L3M 194) vs quick 78 (max DD 3646, worst -1943, L6M 11, L3M 45)

**(i) Asia ew: 195 of 195 picks landed (160 weeks)**: exact $/lot/wk 126 (max DD 9262, worst -3871, L6M 75, L3M 191) vs quick 138 (max DD 8072, worst -3591, L6M 182, L3M 220)

**(i) London best: 34 of 34 picks landed (160 weeks)**: exact $/lot/wk 13 (max DD 8558, worst -1670, L6M -98, L3M 29) vs quick 118 (max DD 5987, worst -1466, L6M 198, L3M 205)

**(i) London ew: 105 of 105 picks landed (160 weeks)**: exact $/lot/wk -81 (max DD 22880, worst -7240, L6M -111, L3M -421) vs quick 14 (max DD 9195, worst -4453, L6M 56, L3M -164)

**(i) NYAM best: 130 of 130 picks landed (160 weeks)**: exact $/lot/wk 66 (max DD 6985, worst -2215, L6M 383, L3M 478) vs quick 51 (max DD 6364, worst -1884, L6M 196, L3M 511)

**(i) NYAM ew: 195 of 195 picks landed (160 weeks)**: exact $/lot/wk 74 (max DD 9021, worst -4213, L6M 255, L3M 588) vs quick 60 (max DD 14462, worst -4233, L6M -105, L3M 258)

**(i) NYPM best: 54 of 54 picks landed (160 weeks)**: exact $/lot/wk 82 (max DD 5570, worst -1569, L6M -45, L3M -299) vs quick 114 (max DD 7895, worst -2333, L6M -14, L3M 6)

**(i) NYPM ew: 195 of 195 picks landed (160 weeks)**: exact $/lot/wk -25 (max DD 22148, worst -3817, L6M -159, L3M 240) vs quick -102 (max DD 26343, worst -3698, L6M -286, L3M -8)

**(ii) T1 Asia: 12 of 12 books landed**: exact mean $/lot/wk 94

**(ii) T1 London: 8 of 8 books landed**: exact mean $/lot/wk 111

**(ii) T1 NYAM: 20 of 20 books landed**: exact mean $/lot/wk 158

**(ii) T1 NYPM: 12 of 12 books landed**: exact mean $/lot/wk 149

**(i) Asia partB_best: 960 of 960 picks landed (160 weeks)**: exact $/lot/wk 1953 (max DD 27228, worst -24216, L6M 2374, L3M 3387) vs quick 1476 (max DD 28724, worst -18837, L6M 511, L3M 668)

**(i) London partB_best: 104 of 104 picks landed (160 weeks)**: exact $/lot/wk 317 (max DD 73354, worst -12807, L6M -485, L3M 2059) vs quick 304 (max DD 63806, worst -12871, L6M -358, L3M 2009)

**(i) NYAM partB_best: 800 of 800 picks landed (160 weeks)**: exact $/lot/wk 2287 (max DD 69793, worst -39798, L6M 7465, L3M 9543) vs quick 1328 (max DD 68979, worst -39430, L6M 5794, L3M 8514)

**(i) NYPM partB_best: 960 of 960 picks landed (160 weeks)**: exact $/lot/wk -215 (max DD 144743, worst -22279, L6M -1164, L3M 151) vs quick 295 (max DD 87658, worst -29246, L6M 918, L3M -1298)


## Hindsight and survivor effects
- Candidate set = the stored grid (cells with >= 5 trades over 3.6 years, a filter that looks at the whole span); modules, brackets and bar types were chosen by people who saw earlier data; 13 of 17 level modules had stale pre-06:00Z grid results (UNVERIFIED), as flagged in stage A.
- Quick screen is a tape walk, not the engine; weekly bins; the first three months of OOS have no half-year test.
- The best-of-48 row is selected on the same weeks it is reported on; the haircut is the correction. The equal-weight comparison has no selection.
- Part B uses the best S version per session as its basket (the basket whose number it improves); the best-of-9 penalty covers only the 9 Part B versions.
- Live-book mapping uses W-ROTA's grid cells, which approximate the live definitions; the exact calibration compares against the existing bare R0 sets instead.