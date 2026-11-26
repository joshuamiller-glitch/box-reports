# TEST 5: t-stat ladder + recent gate, ONE pre-named primary (W-TEST5)

**QUICK SCREEN label on every number below** unless it says EXACT: grid weekly arrays (th_grid tape walk, not the exact engine), 1 NQ lot per book at $20/point, grid cost in, no stack rules, no account layers. Order: autopilot/DIRECTIVE_TEST5_1936Z.md (relay design under Josh's 18:22Z standing order), followed as written: t-stat of weekly P&L (3, 4, 5, 6) x recent gate (none / trailing 26 weeks profitable / trailing 13 weeks profitable) x re-qualify (13 weeks / 4 weeks) = 24 versions, none added; fixed trades to date >= 100, >= 75% of fully-past half-years profitable, family share >= 70%; one cell per book, one book per family, hold ALL qualifiers equal weight, no picking; same span as Test 4 (2023-10-01 to 2026-10-25, 160 weeks, only data before each date). Code code/th_test5, data server C /mnt/l2/l2vast/_test5/out (copy of tables on box 1 /mnt/l2/l2vast/_test5). $/lot/wk = equal-weight average over the books held that week (a week with no book held is cash, 0).

**Honesty about the primary.** The primary (t>=4, trailing 26 weeks profitable, re-qualify every 13 weeks) was named in the order BEFORE any Test 5 number existed, but AFTER the Test 4 results were seen (in Test 4 the N>=100, t>=4 row was already +134 $/lot/wk for the four sessions summed). So it is a one-version choice judged alone with no best-of penalty, but it is NOT out-of-sample independent of the idea. The 24-version grid below is the honest multiple-comparison view.

## ANSWER FIRST (QUICK SCREEN)

1. **PRIMARY, judged alone, plain block-bootstrap p vs zero (no best-of penalty; PASS = above zero with p <= 0.10): Asia PASS (+178 $/lot/wk, p 0.026), NY AM PASS (+172, p 0.096), four sessions summed PASS (+135, p 0.072); London FAIL (-80, p 0.83), NY PM FAIL (+190, p 0.14).** Recent first, four summed: L3M +221, L6M +76, 2026 (Jan to Oct) -5, 2025 +275, 2024 +154, 2023 Q4 -55; max drawdown 11,774 $/lot, worst week -5,649 $/lot. So the sum is positive and clears p 0.10 as a single version, but the recent half-year is thin (+76) and 2026 is flat; it is the 2024-2025 years that carry it. NY AM L6M is negative (-87) and its 2026 is -133; Asia is positive in every recent window (L3M 221, L6M 428, 2026 +283).
2. **The recent gate does almost nothing.** Along none -> 26 weeks -> 13 weeks the four-session mean over the other axes is 162 -> 162 -> 165 $/lot/wk (Asia 126 -> 127 -> 128, NY AM 217 -> 217 -> 220, NY PM 35 -> 32 -> 29, London -68 -> -67 -> -65). The t>=4 book already has profitable recent weeks nearly always, so the gate rarely removes a book (primary vs the same rule with no gate: 135 vs 134 summed). Re-qualifying every 13 weeks is better than every 4 weeks in the sum (179 vs 146 mean over the other axes): faster re-picking did not help.
3. **The t slope does NOT continue.** Four summed, mean over gate and step: t>=3 72 -> t>=4 121 -> t>=5 332 -> t>=6 127 $/lot/wk, but the t>=5 and t>=6 baskets are tiny (t>=5: about 18 books at the start, 11 at the last date, 198 books ever; t>=6: 8 books ever, none held at the end) and their recent windows are negative (t>=5 L6M -59 to -197, L3M -229 to -708; t>=6 4-weekly L3M -1,616). Their dollar figures are a handful of books in a handful of weeks. Asia goes steadily DOWN with t (189 -> 187 -> 107 -> 25); NY AM and NY PM are not monotonic; London has no slope.
4. **Best-of-24 grid (penalty as in Test 4, White reality check, block 4 wk, 2,000 draws):** four summed best = t>=5, trailing 13 wk, every 13 wk, +371 -> +235 after the penalty, p 0.07 (PASS by the rule, but it is an 18-book basket with L3M -229 and L6M -59: not a basket to trust or build). NY AM best +580 -> +424, p 0.01; Asia +196 -> +117, p 0.10 (FAIL, p just over); London FAIL (-57, p 0.89); NY PM +58, p 0.36 FAIL. The primary is the more honest pass than the grid best.
5. **BUILDABLE CHECK (reference, primary only):** a basket of 12 random qualified books per session per 13-week date (London 5), 200 chains: four summed +142 $/lot/wk (5-95%: 91 to 191), max DD 10,201 (6,997 to 13,743), all 200 chains above zero; Asia +179 (96 to 259), NY AM +156 (7 to 292, 96% of chains above zero), NY PM +185 (105 to 262), London -82 (-159 to 1, 6% above zero). A basket small enough to code (about 41 books across the four sessions) would have looked like the full basket of about 436.
6. **T2, the 20 live books under the primary:** 17 of 20 map to a stored cell; **none of the 17 ever qualifies** (t>=4 plus the recent gate is stricter than they ever were on their own history, as in Test 4). The quick-screen pass is on a set of books that is not the live set.
7. **EXACT** for the primary's held cells: see the EXACT section (PENDING until the rows land). Test 3 calibration: exact is 1.52x the quick screen on average, median 1.17, weekly correlation 0.92 (rank-grade, not level-grade); Test 4 calibration will be added when its rows land.

## PRIMARY, alone, per session and summed (QUICK SCREEN; L3M and L6M first)

| session | PRIMARY $/lot/wk | plain block-bootstrap p vs zero (no best-of penalty) | verdict | L3M | L6M | max DD $/lot | worst wk | 2023 Q4 | 2024 | 2025 | 2026 | books held first / mean / last | books ever | weeks with a book held (of 160) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 178 | 0.026 | **PASS** | 221 | 428 | 7083 | -3877 | 88 | 167 | 130 | 283 | 18 / 163 / 388 | 1641 | 160 |
| London | -80 | 0.833 | **FAIL** | -231 | -26 | 14344 | -6462 | -198 | -20 | -120 | -65 | 146 / 29 / 11 | 330 | 160 |
| NY AM | 172 | 0.096 | **PASS** | 251 | -87 | 22269 | -6438 | 21 | 243 | 382 | -133 | 231 / 222 / 125 | 1900 | 160 |
| NY PM | 190 | 0.138 | **FAIL** | 243 | 516 | 23441 | -4339 | -36 | 37 | 595 | -59 | 43 / 22 / 11 | 204 | 160 |
| Four sessions summed | 135 | 0.072 | **PASS** | 221 | 76 | 11774 | -5649 | -55 | 154 | 275 | -5 | 438 / 436 / 535 | 4075 | 160 |

p is a one-sided centred block bootstrap of the weekly per-lot series against zero (block 4 weeks, 2,000 draws), one version, no best-of penalty. Books held: first / mean / last re-qualify date (summed row adds the four sessions). Weeks with a book held: all 160 (the basket is never empty for the sums; per session see the table).

## 24-version grid, best-of-24 penalty (QUICK SCREEN)

| session | best of 24 by mean | $/lot/wk | best-of-24 haircut | after haircut | RC p vs zero | verdict | versions > 0 of 24 | median version $/lot/wk |
|---|---|---|---|---|---|---|---|---|
| Asia | t>=3, trailing 13 wk profitable, every 4 wk | 196 | 79 | 117 | 0.10 | **FAIL** | 21 | 153 |
| London | t>=6, no recent gate, every 13 wk | 18 | 75 | -57 | 0.89 | **FAIL** | 3 | -70 |
| NY AM | t>=5, trailing 13 wk profitable, every 4 wk | 580 | 156 | 424 | 0.01 | **PASS** | 24 | 143 |
| NY PM | t>=4, no recent gate, every 13 wk | 191 | 133 | 58 | 0.36 | **FAIL** | 9 | 0 |
| Four sessions summed | t>=5, trailing 13 wk profitable, every 13 wk | 371 | 136 | 235 | 0.07 | **PASS** | 24 | 121 |

PASS = after penalty > 0 and RC p <= 0.10. Versions above zero are counted out of 24 (versions with no book held earn 0 and are not above zero).

## BUILDABLE CHECK (reference, primary only; QUICK SCREEN)

Each 13-week date draw 12 of the books the primary would hold (London 5; fewer if fewer qualify) at random, hold to the next date, 200 chains; the four-session row sums the four session baskets (40.6 books per week on average).

| scope | chains: mean $/lot/wk (5-95%) | mean max DD (5-95%) | mean L6M (5-95%) | mean L3M (5-95%) | share of chains > 0 | books per week | the full primary for comparison: $/lot/wk / max DD |
|---|---|---|---|---|---|---|---|
| Asia | 179 (96 to 259) | 9419 (6514 to 13185) | 430 (143 to 724) | 242 (-88 to 586) | 100% | 12.0 | 178 / 7083 |
| London | -82 (-159 to 1) | 18283 (10355 to 28026) | -24 (-192 to 136) | -225 (-602 to 182) | 6% | 4.9 | -80 / 14344 |
| NY AM | 156 (7 to 292) | 25857 (14108 to 38810) | -131 (-700 to 429) | 278 (-277 to 928) | 96% | 12.0 | 172 / 22269 |
| NY PM | 185 (105 to 262) | 23788 (20119 to 27318) | 521 (350 to 648) | 243 (243 to 243) | 100% | 11.7 | 190 / 23441 |
| Four sessions summed | 142 (91 to 191) | 10201 (6997 to 13743) | 237 (35 to 422) | 198 (-20 to 413) | 100% | 40.6 | 135 / 11774 |

## T2: the 20 live books under the primary rule (first date qualified, result after; QUICK SCREEN)

| live book (session) | mapped | first date it qualifies under the PRIMARY | $/lot/wk after | max DD after | weeks after |
|---|---|---|---|---|---|
| Lb0e6dfa3_R0_F40_80 (Asia) | yes | never | | | |
| L385f4f2e_CX502 (Asia) | no stored cell | | | | |
| L9c2622b0_R0_P45 (Asia) | yes | never | | | |
| L4aaacdb2_R0_P30 (Asia) | yes | never | | | |
| L19201dfc.BRF90_30 (London) | yes | never | | | |
| L12842dde.BRP45 (London) | yes | never | | | |
| L74274eca.BRF120_60 (London) | yes | never | | | |
| L43f0cbfb.BRS8U (NY AM) | yes | never | | | |
| B7bfd33b7 (NY AM) | no stored cell | | | | |
| Bf428c4a1.BRS8U (NY AM) | no stored cell | | | | |
| Le4fede95.BRF90_30 (NY AM) | yes | never | | | |
| Lf0346d55.BRP60 (NY AM) | yes | never | | | |
| L8cfda948.BRF90_30 (NY AM) | yes | never | | | |
| L4407508c.BRF120_60 (NY AM) | yes | never | | | |
| L39287638.BRF80_40 (NY AM) | yes | never | | | |
| L64390867.BRF80_40 (NY AM) | yes | never | | | |
| L52359bf4_R0_P30 (NY PM) | yes | never | | | |
| L8e0bf58c_R0_S8U (NY PM) | yes | never | | | |
| L4bdd521a_R0_F80_40 (NY PM) | yes | never | | | |
| L2c6916a5_R0_P60 (NY PM) | yes | never | | | |
| **qualified / mapped** | 0 / 17 | | mean - | | |

## EXACT (primary's held cells per session, bare R0, held periods; added to the calibration)

PENDING: the build of the primary's exact sets (4,075 cells, 4,208 held periods) is running on box 1 (niced, 3 procs); rows are appended to pending_nyam_gating.txt only after the Test 3, Test 4 and Part C rows (waiter /mnt/l2/l2vast/_test5/queue_chain5.sh). Finishing commands are in MORNING.md.

## Per session: all 24 versions, grids and slopes (QUICK SCREEN; recent columns first)

Version names: t = minimum t-stat of weekly P&L over all history to date; recent gate = the cell's own trailing 26 (or 13) weeks must have a positive sum; every 13 / 4 wk = re-qualify cadence. Held books are dropped only when they fail the same rule at a re-qualify date.

### Asia: all 24 versions (QUICK SCREEN)

| version | L3M | L6M | $/lot/wk | max DD | worst wk | 2023 Q4 | 2024 | 2025 | 2026 | books held mean / last | books ever |
|---|---|---|---|---|---|---|---|---|---|---|---|
| t>=3, no recent gate, every 13 wk | 134 | 296 | 183 | 4509 | -2948 | 65 | 226 | 116 | 252 | 1277 / 2146 | 10757 |
| t>=4, no recent gate, every 13 wk | 221 | 428 | 179 | 7057 | -3876 | 88 | 167 | 130 | 286 | 163 / 388 | 1642 |
| t>=5, no recent gate, every 13 wk | -284 | -48 | 128 | 15026 | -3827 | 0 | 120 | 160 | 136 | 4 / 8 | 46 |
| t>=6, no recent gate, every 13 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |
| t>=3, trailing 26 wk profitable, every 13 wk | 133 | 297 | 183 | 4509 | -2972 | 65 | 226 | 116 | 253 | 1274 / 2145 | 10801 |
| **PRIMARY** t>=4, trailing 26 wk profitable, every 13 wk | 221 | 428 | 178 | 7083 | -3877 | 88 | 167 | 130 | 283 | 163 / 388 | 1641 |
| t>=5, trailing 26 wk profitable, every 13 wk | -284 | -48 | 128 | 15026 | -3827 | 0 | 120 | 160 | 136 | 4 / 8 | 46 |
| t>=6, trailing 26 wk profitable, every 13 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |
| t>=3, trailing 13 wk profitable, every 13 wk | 135 | 310 | 186 | 4506 | -2895 | 65 | 226 | 119 | 260 | 1256 / 2097 | 11001 |
| t>=4, trailing 13 wk profitable, every 13 wk | 214 | 421 | 184 | 7146 | -3916 | 88 | 167 | 151 | 278 | 161 / 385 | 1647 |
| t>=5, trailing 13 wk profitable, every 13 wk | -284 | -48 | 128 | 15026 | -3827 | 0 | 120 | 160 | 136 | 4 / 8 | 46 |
| t>=6, trailing 13 wk profitable, every 13 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |
| t>=3, no recent gate, every 4 wk | 141 | 299 | 191 | 5113 | -3502 | 100 | 203 | 157 | 248 | 1269 / 2146 | 17771 |
| t>=4, no recent gate, every 4 wk | 236 | 362 | 193 | 6420 | -3824 | 235 | 156 | 157 | 272 | 165 / 388 | 2977 |
| t>=5, no recent gate, every 4 wk | -452 | -181 | 86 | 13516 | -8471 | -45 | -147 | 442 | -34 | 3 / 8 | 81 |
| t>=6, no recent gate, every 4 wk | 0 | 0 | 50 | 2566 | -2440 | 0 | 155 | 0 | 0 | 0 / 0 | 1 |
| t>=3, trailing 26 wk profitable, every 4 wk | 144 | 303 | 192 | 5090 | -3485 | 100 | 203 | 156 | 252 | 1267 / 2145 | 17843 |
| t>=4, trailing 26 wk profitable, every 4 wk | 236 | 362 | 194 | 6420 | -3824 | 235 | 156 | 159 | 273 | 165 / 388 | 2978 |
| t>=5, trailing 26 wk profitable, every 4 wk | -452 | -181 | 86 | 13516 | -8471 | -45 | -147 | 442 | -34 | 3 / 8 | 81 |
| t>=6, trailing 26 wk profitable, every 4 wk | 0 | 0 | 50 | 2566 | -2440 | 0 | 155 | 0 | 0 | 0 / 0 | 1 |
| t>=3, trailing 13 wk profitable, every 4 wk | 140 | 313 | 196 | 5093 | -3524 | 102 | 206 | 160 | 256 | 1255 / 2097 | 18512 |
| t>=4, trailing 13 wk profitable, every 4 wk | 235 | 358 | 194 | 6489 | -3815 | 235 | 156 | 162 | 270 | 164 / 385 | 3002 |
| t>=5, trailing 13 wk profitable, every 4 wk | -452 | -181 | 86 | 13516 | -8471 | -45 | -147 | 442 | -34 | 3 / 8 | 81 |
| t>=6, trailing 13 wk profitable, every 4 wk | 0 | 0 | 50 | 2566 | -2440 | 0 | 155 | 0 | 0 | 0 / 0 | 1 |

Grid $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 187 | 188 | 191 | 189 |
| 4 | 186 | 186 | 189 | 187 |
| 5 | 107 | 107 | 107 | 107 |
| 6 | 25 | 25 | 25 | 25 |
| mean | 126 | 127 | 128 | |

Grid L6M $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 297 | 300 | 312 | 303 |
| 4 | 395 | 395 | 390 | 393 |
| 5 | -115 | -115 | -115 | -115 |
| 6 | 0 | 0 | 0 | 0 |
| mean | 144 | 145 | 147 | |

Grid max DD $/lot, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 4811 | 4800 | 4800 | 4803 |
| 4 | 6738 | 6752 | 6818 | 6769 |
| 5 | 14271 | 14271 | 14271 | 14271 |
| 6 | 1283 | 1283 | 1283 | 1283 |
| mean | 6776 | 6776 | 6793 | |

Slope ($/lot/wk): along t 3 -> 4 -> 5 -> 6: 189 -> 187 -> 107 -> 25 = **steady down**; along the recent gate none -> 26 wk -> 13 wk: 126 -> 127 -> 128 = **steady up**; re-qualify 13 wk vs 4 wk: 123 vs 131.

### London: all 24 versions (QUICK SCREEN)

| version | L3M | L6M | $/lot/wk | max DD | worst wk | 2023 Q4 | 2024 | 2025 | 2026 | books held mean / last | books ever |
|---|---|---|---|---|---|---|---|---|---|---|---|
| t>=3, no recent gate, every 13 wk | -229 | -98 | -70 | 13586 | -5823 | -187 | 42 | -140 | -85 | 329 / 162 | 3362 |
| t>=4, no recent gate, every 13 wk | -231 | -26 | -80 | 14344 | -6462 | -198 | -20 | -120 | -65 | 29 / 11 | 330 |
| t>=5, no recent gate, every 13 wk | 0 | 0 | -149 | 26174 | -8345 | -333 | -200 | -172 | 0 | 2 / 0 | 22 |
| t>=6, no recent gate, every 13 wk | 0 | 0 | 18 | 6774 | -3749 | 216 | 0 | 0 | 0 | 0 / 0 | 1 |
| t>=3, trailing 26 wk profitable, every 13 wk | -221 | -92 | -71 | 13775 | -5823 | -187 | 42 | -144 | -82 | 328 / 162 | 3361 |
| **PRIMARY** t>=4, trailing 26 wk profitable, every 13 wk | -231 | -26 | -80 | 14344 | -6462 | -198 | -20 | -120 | -65 | 29 / 11 | 330 |
| t>=5, trailing 26 wk profitable, every 13 wk | 0 | 0 | -149 | 26174 | -8345 | -333 | -200 | -172 | 0 | 2 / 0 | 22 |
| t>=6, trailing 26 wk profitable, every 13 wk | 0 | 0 | 18 | 6774 | -3749 | 216 | 0 | 0 | 0 | 0 / 0 | 1 |
| t>=3, trailing 13 wk profitable, every 13 wk | -212 | -104 | -66 | 12664 | -5819 | -187 | 46 | -116 | -105 | 321 / 153 | 3358 |
| t>=4, trailing 13 wk profitable, every 13 wk | -231 | -26 | -65 | 12302 | -6462 | -198 | -20 | -77 | -65 | 28 / 11 | 329 |
| t>=5, trailing 13 wk profitable, every 13 wk | 0 | 0 | -149 | 26174 | -8345 | -333 | -200 | -172 | 0 | 2 / 0 | 22 |
| t>=6, trailing 13 wk profitable, every 13 wk | 0 | 0 | 18 | 6774 | -3749 | 216 | 0 | 0 | 0 | 0 / 0 | 1 |
| t>=3, no recent gate, every 4 wk | -160 | -140 | -92 | 15173 | -6037 | -221 | 15 | -136 | -129 | 296 / 162 | 5540 |
| t>=4, no recent gate, every 4 wk | -385 | 136 | -43 | 12925 | -7604 | -246 | 63 | -123 | -11 | 24 / 11 | 557 |
| t>=5, no recent gate, every 4 wk | 0 | 0 | -101 | 18250 | -5874 | -309 | -195 | -39 | 0 | 1 / 0 | 29 |
| t>=6, no recent gate, every 4 wk | 0 | 0 | -29 | 6774 | -3749 | -353 | 0 | 0 | 0 | 0 / 0 | 1 |
| t>=3, trailing 26 wk profitable, every 4 wk | -157 | -128 | -87 | 14704 | -6037 | -221 | 15 | -133 | -113 | 295 / 162 | 5549 |
| t>=4, trailing 26 wk profitable, every 4 wk | -385 | 136 | -34 | 11538 | -7604 | -246 | 63 | -97 | -11 | 24 / 11 | 557 |
| t>=5, trailing 26 wk profitable, every 4 wk | 0 | 0 | -101 | 18250 | -5874 | -309 | -195 | -39 | 0 | 1 / 0 | 29 |
| t>=6, trailing 26 wk profitable, every 4 wk | 0 | 0 | -29 | 6774 | -3749 | -353 | 0 | 0 | 0 | 0 / 0 | 1 |
| t>=3, trailing 13 wk profitable, every 4 wk | -201 | -153 | -102 | 16912 | -6017 | -220 | 15 | -151 | -150 | 289 / 153 | 5599 |
| t>=4, trailing 13 wk profitable, every 4 wk | -385 | 136 | -28 | 10898 | -7580 | -246 | 63 | -77 | -11 | 23 / 11 | 556 |
| t>=5, trailing 13 wk profitable, every 4 wk | 0 | 0 | -101 | 18250 | -5874 | -309 | -195 | -39 | 0 | 1 / 0 | 29 |
| t>=6, trailing 13 wk profitable, every 4 wk | 0 | 0 | -29 | 6774 | -3749 | -353 | 0 | 0 | 0 | 0 / 0 | 1 |

Grid $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | -81 | -79 | -84 | -81 |
| 4 | -61 | -57 | -47 | -55 |
| 5 | -125 | -125 | -125 | -125 |
| 6 | -6 | -6 | -6 | -6 |
| mean | -68 | -67 | -65 | |

Grid L6M $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | -119 | -110 | -129 | -119 |
| 4 | 55 | 55 | 55 | 55 |
| 5 | 0 | 0 | 0 | 0 |
| 6 | 0 | 0 | 0 | 0 |
| mean | -16 | -14 | -18 | |

Grid max DD $/lot, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 14379 | 14239 | 14788 | 14469 |
| 4 | 13635 | 12941 | 11600 | 12725 |
| 5 | 22212 | 22212 | 22212 | 22212 |
| 6 | 6774 | 6774 | 6774 | 6774 |
| mean | 14250 | 14042 | 13844 | |

Slope ($/lot/wk): along t 3 -> 4 -> 5 -> 6: -81 -> -55 -> -125 -> -6 = **not monotonic**; along the recent gate none -> 26 wk -> 13 wk: -68 -> -67 -> -65 = **steady up**; re-qualify 13 wk vs 4 wk: -69 vs -65.

### NY AM: all 24 versions (QUICK SCREEN)

| version | L3M | L6M | $/lot/wk | max DD | worst wk | 2023 Q4 | 2024 | 2025 | 2026 | books held mean / last | books ever |
|---|---|---|---|---|---|---|---|---|---|---|---|
| t>=3, no recent gate, every 13 wk | 79 | -336 | 71 | 25437 | -6686 | 4 | 169 | 296 | -315 | 1874 / 1207 | 13794 |
| t>=4, no recent gate, every 13 wk | 219 | -89 | 171 | 22316 | -6434 | 21 | 243 | 383 | -140 | 223 / 129 | 1893 |
| t>=5, no recent gate, every 13 wk | 25 | 276 | 540 | 16345 | -6365 | 241 | 303 | 954 | 402 | 12 / 3 | 123 |
| t>=6, no recent gate, every 13 wk | 0 | 0 | 165 | 16448 | -8348 | 395 | 0 | 402 | 0 | 1 / 0 | 7 |
| t>=3, trailing 26 wk profitable, every 13 wk | 60 | -350 | 68 | 25646 | -6715 | 4 | 169 | 296 | -325 | 1860 / 1154 | 13997 |
| **PRIMARY** t>=4, trailing 26 wk profitable, every 13 wk | 251 | -87 | 172 | 22269 | -6438 | 21 | 243 | 382 | -133 | 222 / 125 | 1900 |
| t>=5, trailing 26 wk profitable, every 13 wk | 25 | 276 | 540 | 16345 | -6365 | 241 | 303 | 954 | 402 | 12 / 3 | 123 |
| t>=6, trailing 26 wk profitable, every 13 wk | 0 | 0 | 165 | 16448 | -8348 | 395 | 0 | 402 | 0 | 1 / 0 | 7 |
| t>=3, trailing 13 wk profitable, every 13 wk | 76 | -334 | 71 | 25292 | -6854 | 4 | 164 | 298 | -309 | 1816 / 1109 | 14480 |
| t>=4, trailing 13 wk profitable, every 13 wk | 179 | -138 | 162 | 22729 | -6565 | 21 | 236 | 385 | -168 | 218 / 120 | 1924 |
| t>=5, trailing 13 wk profitable, every 13 wk | 25 | 313 | 565 | 14745 | -6365 | 241 | 303 | 986 | 458 | 12 / 3 | 123 |
| t>=6, trailing 13 wk profitable, every 13 wk | 0 | 0 | 165 | 16448 | -8348 | 395 | 0 | 402 | 0 | 1 / 0 | 7 |
| t>=3, no recent gate, every 4 wk | 102 | -310 | 70 | 25054 | -6888 | 23 | 179 | 263 | -295 | 2017 / 1207 | 22836 |
| t>=4, no recent gate, every 4 wk | 292 | -117 | 123 | 25922 | -7004 | 17 | 205 | 294 | -160 | 249 / 129 | 3545 |
| t>=5, no recent gate, every 4 wk | -236 | 460 | 553 | 18069 | -5296 | 98 | 441 | 914 | 379 | 13 / 3 | 215 |
| t>=6, no recent gate, every 4 wk | -1616 | -807 | 46 | 36641 | -10789 | 375 | 100 | 68 | -152 | 1 / 0 | 16 |
| t>=3, trailing 26 wk profitable, every 4 wk | 95 | -311 | 68 | 25031 | -6987 | 23 | 178 | 263 | -302 | 2002 / 1154 | 23435 |
| t>=4, trailing 26 wk profitable, every 4 wk | 365 | -102 | 125 | 26400 | -7015 | 17 | 205 | 294 | -154 | 249 / 125 | 3561 |
| t>=5, trailing 26 wk profitable, every 4 wk | -236 | 466 | 556 | 17686 | -5296 | 98 | 441 | 914 | 388 | 13 / 3 | 216 |
| t>=6, trailing 26 wk profitable, every 4 wk | -1616 | -807 | 46 | 36641 | -10789 | 375 | 100 | 68 | -152 | 1 / 0 | 16 |
| t>=3, trailing 13 wk profitable, every 4 wk | 71 | -326 | 67 | 25531 | -7036 | 23 | 176 | 264 | -304 | 1948 / 1109 | 25218 |
| t>=4, trailing 13 wk profitable, every 4 wk | 226 | -246 | 103 | 28053 | -6942 | 17 | 208 | 286 | -233 | 244 / 120 | 3627 |
| t>=5, trailing 13 wk profitable, every 4 wk | -388 | 639 | 580 | 18622 | -4910 | 98 | 441 | 921 | 471 | 13 / 3 | 218 |
| t>=6, trailing 13 wk profitable, every 4 wk | -1616 | -807 | 46 | 36641 | -10789 | 375 | 100 | 68 | -152 | 1 / 0 | 16 |

Grid $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 70 | 68 | 69 | 69 |
| 4 | 147 | 149 | 132 | 143 |
| 5 | 547 | 548 | 572 | 556 |
| 6 | 106 | 106 | 106 | 106 |
| mean | 217 | 217 | 220 | |

Grid L6M $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | -323 | -331 | -330 | -328 |
| 4 | -103 | -94 | -192 | -130 |
| 5 | 368 | 371 | 476 | 405 |
| 6 | -404 | -404 | -404 | -404 |
| mean | -115 | -114 | -112 | |

Grid max DD $/lot, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 25246 | 25339 | 25412 | 25332 |
| 4 | 24119 | 24334 | 25391 | 24615 |
| 5 | 17207 | 17016 | 16684 | 16969 |
| 6 | 26545 | 26545 | 26545 | 26545 |
| mean | 23279 | 23308 | 23508 | |

Slope ($/lot/wk): along t 3 -> 4 -> 5 -> 6: 69 -> 143 -> 556 -> 106 = **not monotonic**; along the recent gate none -> 26 wk -> 13 wk: 217 -> 217 -> 220 = **steady up**; re-qualify 13 wk vs 4 wk: 238 vs 198.

### NY PM: all 24 versions (QUICK SCREEN)

| version | L3M | L6M | $/lot/wk | max DD | worst wk | 2023 Q4 | 2024 | 2025 | 2026 | books held mean / last | books ever |
|---|---|---|---|---|---|---|---|---|---|---|---|
| t>=3, no recent gate, every 13 wk | 214 | 304 | -3 | 9590 | -3303 | -90 | -99 | 113 | -2 | 284 / 164 | 2524 |
| t>=4, no recent gate, every 13 wk | 243 | 516 | 191 | 23391 | -4339 | -36 | 37 | 595 | -58 | 22 / 11 | 205 |
| t>=5, no recent gate, every 13 wk | 0 | 0 | 168 | 20434 | -10537 | -104 | 171 | 366 | 0 | 1 / 0 | 7 |
| t>=6, no recent gate, every 13 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |
| t>=3, trailing 26 wk profitable, every 13 wk | 185 | 257 | -4 | 9815 | -3218 | -90 | -99 | 131 | -31 | 282 / 159 | 2528 |
| **PRIMARY** t>=4, trailing 26 wk profitable, every 13 wk | 243 | 516 | 190 | 23441 | -4339 | -36 | 37 | 595 | -59 | 22 / 11 | 204 |
| t>=5, trailing 26 wk profitable, every 13 wk | 0 | 0 | 168 | 20434 | -10537 | -104 | 171 | 366 | 0 | 1 / 0 | 7 |
| t>=6, trailing 26 wk profitable, every 13 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |
| t>=3, trailing 13 wk profitable, every 13 wk | 207 | 230 | -19 | 10383 | -3727 | -90 | -94 | 111 | -68 | 276 / 151 | 2572 |
| t>=4, trailing 13 wk profitable, every 13 wk | 271 | 186 | 127 | 24559 | -5849 | -36 | 37 | 556 | -251 | 21 / 11 | 209 |
| t>=5, trailing 13 wk profitable, every 13 wk | 0 | 0 | 168 | 20434 | -10537 | -104 | 171 | 366 | 0 | 1 / 0 | 7 |
| t>=6, trailing 13 wk profitable, every 13 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |
| t>=3, no recent gate, every 4 wk | 244 | 197 | -45 | 13041 | -3115 | -128 | -128 | 72 | -65 | 282 / 164 | 4271 |
| t>=4, no recent gate, every 4 wk | -12 | -129 | 41 | 26219 | -5373 | -45 | -72 | 594 | -492 | 22 / 11 | 407 |
| t>=5, no recent gate, every 4 wk | 0 | 0 | -72 | 28185 | -10537 | -55 | -312 | 101 | 0 | 1 / 0 | 18 |
| t>=6, no recent gate, every 4 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |
| t>=3, trailing 26 wk profitable, every 4 wk | 254 | 177 | -40 | 12449 | -3287 | -128 | -127 | 89 | -70 | 280 / 159 | 4306 |
| t>=4, trailing 26 wk profitable, every 4 wk | 116 | -228 | 17 | 30302 | -4475 | -45 | -72 | 594 | -581 | 22 / 11 | 406 |
| t>=5, trailing 26 wk profitable, every 4 wk | 0 | 0 | -72 | 28185 | -10537 | -55 | -312 | 101 | 0 | 1 / 0 | 18 |
| t>=6, trailing 26 wk profitable, every 4 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |
| t>=3, trailing 13 wk profitable, every 4 wk | 248 | 171 | -53 | 14274 | -3720 | -128 | -121 | 81 | -115 | 274 / 151 | 4433 |
| t>=4, trailing 13 wk profitable, every 4 wk | 127 | 31 | 81 | 22179 | -5373 | -45 | -73 | 628 | -378 | 22 / 11 | 408 |
| t>=5, trailing 13 wk profitable, every 4 wk | 0 | 0 | -72 | 28185 | -10537 | -55 | -312 | 101 | 0 | 1 / 0 | 18 |
| t>=6, trailing 13 wk profitable, every 4 wk | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 |

Grid $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | -24 | -22 | -36 | -27 |
| 4 | 116 | 104 | 104 | 108 |
| 5 | 48 | 48 | 48 | 48 |
| 6 | 0 | 0 | 0 | 0 |
| mean | 35 | 32 | 29 | |

Grid L6M $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 250 | 217 | 200 | 222 |
| 4 | 193 | 144 | 109 | 149 |
| 5 | 0 | 0 | 0 | 0 |
| 6 | 0 | 0 | 0 | 0 |
| mean | 111 | 90 | 77 | |

Grid max DD $/lot, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 11315 | 11132 | 12329 | 11592 |
| 4 | 24805 | 26872 | 23369 | 25015 |
| 5 | 24309 | 24309 | 24309 | 24309 |
| 6 | 0 | 0 | 0 | 0 |
| mean | 15107 | 15578 | 15002 | |

Slope ($/lot/wk): along t 3 -> 4 -> 5 -> 6: -27 -> 108 -> 48 -> 0 = **not monotonic**; along the recent gate none -> 26 wk -> 13 wk: 35 -> 32 -> 29 = **steady down**; re-qualify 13 wk vs 4 wk: 82 vs -18.

### Four sessions summed: all 24 versions (QUICK SCREEN)

| version | L3M | L6M | $/lot/wk | max DD | worst wk | 2023 Q4 | 2024 | 2025 | 2026 | books held mean / last | books ever |
|---|---|---|---|---|---|---|---|---|---|---|---|
| t>=3, no recent gate, every 13 wk | 106 | -61 | 61 | 12492 | -5248 | -75 | 87 | 190 | -90 | 3764 / 3679 | 30437 |
| t>=4, no recent gate, every 13 wk | 213 | 71 | 134 | 11952 | -5648 | -55 | 154 | 275 | -11 | 437 / 539 | 4070 |
| t>=5, no recent gate, every 13 wk | -229 | -94 | 348 | 12314 | -5738 | 74 | 162 | 744 | 162 | 18 / 11 | 198 |
| t>=6, no recent gate, every 13 wk | 0 | 0 | 163 | 16448 | -8348 | 365 | 0 | 402 | 0 | 1 / 0 | 8 |
| t>=3, trailing 26 wk profitable, every 13 wk | 97 | -66 | 60 | 12595 | -5283 | -75 | 87 | 190 | -94 | 3744 / 3620 | 30687 |
| **PRIMARY** t>=4, trailing 26 wk profitable, every 13 wk | 221 | 76 | 135 | 11774 | -5649 | -55 | 154 | 275 | -5 | 436 / 535 | 4075 |
| t>=5, trailing 26 wk profitable, every 13 wk | -229 | -94 | 348 | 12314 | -5738 | 74 | 162 | 744 | 162 | 18 / 11 | 198 |
| t>=6, trailing 26 wk profitable, every 13 wk | 0 | 0 | 163 | 16448 | -8348 | 365 | 0 | 402 | 0 | 1 / 0 | 8 |
| t>=3, trailing 13 wk profitable, every 13 wk | 106 | -46 | 66 | 12091 | -5366 | -75 | 87 | 195 | -79 | 3669 / 3510 | 31411 |
| t>=4, trailing 13 wk profitable, every 13 wk | 199 | 52 | 135 | 12229 | -5760 | -55 | 152 | 286 | -18 | 429 / 527 | 4109 |
| t>=5, trailing 13 wk profitable, every 13 wk | -229 | -59 | 371 | 11914 | -5225 | 74 | 162 | 775 | 211 | 18 / 11 | 198 |
| t>=6, trailing 13 wk profitable, every 13 wk | 0 | 0 | 163 | 16448 | -8348 | 365 | 0 | 402 | 0 | 1 / 0 | 8 |
| t>=3, no recent gate, every 4 wk | 123 | -8 | 79 | 10826 | -5393 | -94 | 117 | 193 | -57 | 3864 / 3679 | 50418 |
| t>=4, no recent gate, every 4 wk | 226 | 119 | 107 | 12735 | -5876 | -73 | 129 | 216 | -1 | 460 / 539 | 7486 |
| t>=5, no recent gate, every 4 wk | -659 | -197 | 309 | 14912 | -4520 | -18 | 221 | 818 | -122 | 18 / 11 | 343 |
| t>=6, no recent gate, every 4 wk | -1616 | -807 | 91 | 36641 | -10789 | 312 | 255 | 68 | -152 | 1 / 0 | 18 |
| t>=3, trailing 26 wk profitable, every 4 wk | 124 | -3 | 79 | 10852 | -5453 | -94 | 117 | 193 | -57 | 3844 / 3620 | 51133 |
| t>=4, trailing 26 wk profitable, every 4 wk | 247 | 124 | 108 | 12778 | -5888 | -73 | 129 | 217 | 0 | 459 / 535 | 7502 |
| t>=5, trailing 26 wk profitable, every 4 wk | -659 | -191 | 311 | 14594 | -4520 | -18 | 221 | 818 | -114 | 18 / 11 | 344 |
| t>=6, trailing 26 wk profitable, every 4 wk | -1616 | -807 | 91 | 36641 | -10789 | 312 | 255 | 68 | -152 | 1 / 0 | 18 |
| t>=3, trailing 13 wk profitable, every 4 wk | 112 | 15 | 83 | 10669 | -5534 | -94 | 117 | 194 | -45 | 3766 / 3510 | 53762 |
| t>=4, trailing 13 wk profitable, every 4 wk | 208 | 97 | 104 | 12629 | -5861 | -73 | 130 | 214 | -11 | 453 / 527 | 7593 |
| t>=5, trailing 13 wk profitable, every 4 wk | -708 | -177 | 303 | 14889 | -4705 | -18 | 221 | 805 | -128 | 17 / 11 | 346 |
| t>=6, trailing 13 wk profitable, every 4 wk | -1616 | -807 | 91 | 36641 | -10789 | 312 | 255 | 68 | -152 | 1 / 0 | 18 |

Grid $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 70 | 70 | 75 | 72 |
| 4 | 121 | 122 | 120 | 121 |
| 5 | 328 | 329 | 337 | 332 |
| 6 | 127 | 127 | 127 | 127 |
| mean | 162 | 162 | 165 | |

Grid L6M $/lot/wk, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | -35 | -35 | -16 | -28 |
| 4 | 95 | 100 | 74 | 90 |
| 5 | -146 | -143 | -118 | -136 |
| 6 | -404 | -404 | -404 | -404 |
| mean | -122 | -120 | -116 | |

Grid max DD $/lot, mean over the two re-qualify steps: rows t, columns recent gate (none / 26 wk / 13 wk)

| t \ gate | none | 26 wk | 13 wk | mean |
|---|---|---|---|---|
| 3 | 11659 | 11724 | 11380 | 11587 |
| 4 | 12343 | 12276 | 12429 | 12349 |
| 5 | 13613 | 13454 | 13402 | 13490 |
| 6 | 26545 | 26545 | 26545 | 26545 |
| mean | 16040 | 16000 | 15939 | |

Slope ($/lot/wk): along t 3 -> 4 -> 5 -> 6: 72 -> 121 -> 332 -> 127 = **not monotonic**; along the recent gate none -> 26 wk -> 13 wk: 162 -> 162 -> 165 = **steady up**; re-qualify 13 wk vs 4 wk: 179 vs 146.

## Method notes

- Walk: W-ROTA grid extract (weekly points and trade counts of every stored grid cell, 14.5M cells in Asia), code code/th_test5/walk5.py derived from th_test4/walk4.py; the only changes are the version list (N fixed 100), the trailing-profit gate, and the re-qualify cadence (13 and 4 weeks; held-from-date to the next date).
- Metrics: code/th_test5/metrics5.py (primary plain p, best-of-24 reality check with the same 2,000 block draws as Test 4, slopes, buildable chains with rng seed 11, T2). Exact pick list for the primary: /mnt/l2/l2vast/_test5/picks_primary_test5.json (4,075 cells / 4,208 held periods: Asia 1,641, London 330, NY AM 1,900, NY PM 204 cells).
- No engine, gate or park change. The paused candidate backlog is NOT resumed (Josh's own order keeps it paused).
