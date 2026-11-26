# TEST 4: how strict must qualification be? Strict ladder, no picking, hold all (W-TEST4)

**QUICK SCREEN label on every number below** unless it says EXACT: grid weekly arrays (th_grid tape walk, not the exact engine), 1 NQ lot per book at $20/point, grid cost in, no stack rules, no account layers. Order: autopilot/DIRECTIVE_TEST4_1849Z.md (relay design under Josh's 18:22Z standing order), followed as written: N (100, 300, 1000) x t-stat (2, 3, 4) = 9 versions per session, plus the one REFERENCE row, none added. Out of sample 2023-10-01 to 2026-10-25 (160 weeks), only data before each date. Written by W-TEST4. Code code/th_test4, data on server C /mnt/l2/l2vast/_test4/out. $/lot/wk = equal-weight average over the books held that week (a week with no book held is cash, 0).

## ANSWER FIRST (QUICK SCREEN)

1. **FAIL in all four sessions and in the four-session sum.** After the best-of-9 luck penalty the best version is above zero in three sessions (Asia +105, NY AM +96, NY PM +135 $/lot/wk; four summed +67) and below zero in London (-95), but no reality-check p reaches 0.10 (Asia 0.19, London 0.84, NY AM 0.27, NY PM 0.20, sum 0.28). PASS needs both. Test 3's fixed basket was -45 after its penalty in the sum with p 0.97, so strict qualification is clearly better than picked baskets, but with 160 weeks it is not distinguishable from luck.
2. **Stricter t-stat helps steadily; stricter trade count does not.** Raising T from 2 to 3 to 4 (mean over N, $/lot/wk): NY AM -66 -> 66 -> 136, NY PM -185 -> -13 -> 199, four summed -75 -> 19 -> 116: a steady slope. Asia is flat then up (113, 106, 193), London has no slope (-141, -103, -139). Raising N from 100 to 300 to 1000 goes steadily DOWN in Asia (175, 169, 68), NY AM (77, 76, -18) and the sum (62, 48, -50), because fewer books are held (often none in the first year at N=1000) and each book matters more: max drawdown per lot in Asia rises from 6,076 (N=100) to 10,482 to 23,167 (N=1000). The best cell in every session is a t>=4 cell (N=1000 in Asia and London, N=300 in NY AM and NY PM), a corner of the grid held by few books (Asia 157 ever, London 7, NY AM 1,397 at N=300 t4, NY PM 120).
3. **Recent weeks (L3M, L6M first in every table).** L3M is positive in all 9 Asia versions (112 to 490) and in the six t>=3 versions of the sum (95 to 319); L6M is positive in all 9 Asia versions (296 to 905) and NY PM at t>=3/4 (304 to 604) but negative in all 9 NY AM versions (-85 to -679) and in 7 of 9 sum versions. 2026 (Jan to Oct) is negative for the four-session sum in all 9 versions (-11 to -356) while 2025 is positive in all 9 (91 to 485): the strict rule did not hold up through 2026 as a whole basket.
4. **Size of the baskets and turnover.** The loose end holds thousands of books (N=100, t>=2: Asia 2,459 on average, 3,364 at the last date; sum 9,455) and changes nearly all of them each 13 weeks (Asia 2,640 adds+drops per date); the strictest end holds a handful (N=1000, t>=4: Asia 15 on average, London 0.7). A basket of 1 to 10 books has per-lot drawdowns of 25,000 to 30,000 $ (London N1000 t4 30,061; NY PM N300 t4 25,561).
5. **REFERENCE row (same rule with t on the trailing 52 weeks only; N=300, t>=3):** Asia 170 (vs 156 for all-history t), London -89 (-78), NY AM 129 (69), NY PM -119 (-3), sum 85 (40). Mixed: better in Asia, NY AM and the sum, worse in London and NY PM; it is one row, not a result.
6. **T2, the 20 live books (table below):** 17 of 20 map to a stored grid cell. Under the loosest rule (N>=100, t>=2) 8 of 17 ever qualify (all at 2024-09 or later, on average +620 $/wk after the first qualified date); at t>=3 only 3 of 17 (+400/wk); at t>=4 none. The strict rules do not reach most of the live books: they have the trades but not the t-stat, the family share or the profitable half-years. Same hindsight caveat as Test 3 (the 20 books were chosen with hindsight).
7. **How far to trust the dollar figures:** Test 3 calibrated the quick screen against the exact engine on 17 live books (exact 1.52x the quick screen on average, median 1.17, weekly correlation 0.92: rank-grade, not level-grade). The Test 4 exact rows (best version per session) are queued and the calibration for them is in the EXACT section when they land (PENDING).

## Verdicts (QUICK SCREEN, best-of-9, White reality check vs zero, block bootstrap block 4 wk, 2,000 draws; REFERENCE not counted in the 9)

| session | best version by mean | $/lot/wk | best-of-9 haircut | after haircut | RC p vs zero | verdict | best by income per max DD | its $/lot/wk | its max DD | versions > 0 of 9 | REFERENCE (52-wk t) $/lot/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | N>=1000, t>=4 | 200 | 96 | 105 | 0.19 | **FAIL** | N>=100, t>=3 | 183 | 4509 | 8 | 170 |
| London | N>=1000, t>=4 | 33 | 128 | -95 | 0.84 | **FAIL** | N>=1000, t>=4 | 33 | 30061 | 1 | -89 |
| NY AM | N>=300, t>=4 | 182 | 85 | 96 | 0.27 | **FAIL** | N>=300, t>=4 | 182 | 23692 | 6 | 129 |
| NY PM | N>=300, t>=4 | 247 | 112 | 135 | 0.20 | **FAIL** | N>=300, t>=4 | 247 | 25561 | 3 | -119 |
| Four sessions summed | N>=300, t>=4 | 139 | 72 | 67 | 0.28 | **FAIL** | N>=100, t>=4 | 134 | 11952 | 5 | 85 |

## Per session tables (QUICK SCREEN; L3M and L6M first, then all, then by year)

## Asia (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books held first / mean / last date | books ever | books changed per date (adds + drops) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | 112 | 389 | 162 | 6664 | -3123 | -131 | 152 | 98 | 346 | 459 / 2459 / 3364 | 16995 | 2640 |
| N>=100, t>=3 | 134 | 296 | 183 | 4509 | -2948 | 65 | 226 | 116 | 252 | 106 / 1277 / 2146 | 10757 | 1681 |
| N>=100, t>=4 | 221 | 428 | 179 | 7057 | -3876 | 88 | 167 | 130 | 286 | 18 / 163 / 388 | 1642 | 249 |
| N>=300, t>=2 | 135 | 456 | 149 | 10498 | -3759 | -200 | 77 | 100 | 411 | 4 / 1787 / 3012 | 12722 | 1967 |
| N>=300, t>=3 | 137 | 337 | 156 | 10677 | -3692 | 43 | 133 | 103 | 288 | 2 / 882 / 1909 | 7695 | 1168 |
| N>=300, t>=4 | 212 | 443 | 200 | 10273 | -4412 | 43 | 130 | 217 | 313 | 2 / 110 / 327 | 1085 | 159 |
| N>=1000, t>=2 | 153 | 660 | 27 | 20423 | -7728 | 0 | -129 | -228 | 549 | 0 / 602 / 2040 | 4793 | 649 |
| N>=1000, t>=3 | 178 | 586 | -22 | 26823 | -8604 | 0 | -330 | -146 | 507 | 0 / 222 / 982 | 2129 | 278 |
| N>=1000, t>=4 | 490 | 905 | 200 | 22257 | -9665 | 0 | 0 | -326 | 1175 | 0 / 15 / 94 | 157 | 18 |
| REFERENCE: N>=300, t>=3, t on trailing 52 wk | 192 | 387 | 170 | 10776 | -3063 | 43 | 118 | 134 | 320 | 2 / 667 / 1231 | 7362 | 1134 |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | | |

3 x 3 grid, $/lot/wk (whole out-of-sample): rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | 162 | 183 | 179 | 175 |
| 300 | 149 | 156 | 200 | 169 |
| 1000 | 27 | -22 | 200 | 68 |
| mean over N | 113 | 106 | 193 | |

3 x 3 grid, L6M $/lot/wk: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | 389 | 296 | 428 | 371 |
| 300 | 456 | 337 | 443 | 412 |
| 1000 | 660 | 586 | 905 | 717 |
| mean over N | 501 | 406 | 592 | |

3 x 3 grid, max DD $/lot: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | 6664 | 4509 | 7057 | 6076 |
| 300 | 10498 | 10677 | 10273 | 10482 |
| 1000 | 20423 | 26823 | 22257 | 23167 |
| mean over N | 12528 | 14003 | 13195 | |

Slope ($/lot/wk): as T rises (mean over N) 113 -> 106 -> 193 = **not monotonic**; as N rises (mean over T) 175 -> 169 -> 68 = **steady down**.

Books held at each re-qualify date (first 6 dates then last, week index of the date = 26, 39, ...):

| version | 2023-10-01 | 2023-12-31 | 2024-03-31 | 2024-06-30 | 2024-09-29 | 2024-12-29 | 2025-03-30 | 2025-06-29 | 2025-09-28 | 2025-12-28 | 2026-03-29 | 2026-06-28 | 2026-09-27 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | 459 | 940 | 1773 | 2556 | 3407 | 1731 | 1850 | 3501 | 2112 | 2408 | 3355 | 4508 | 3364 |
| N>=100, t>=3 | 106 | 229 | 450 | 1107 | 1956 | 856 | 867 | 2001 | 986 | 1315 | 1721 | 2856 | 2146 |
| N>=100, t>=4 | 18 | 27 | 25 | 148 | 255 | 56 | 64 | 262 | 88 | 152 | 171 | 466 | 388 |
| N>=300, t>=2 | 4 | 85 | 612 | 1394 | 2335 | 1132 | 1370 | 2825 | 1650 | 1916 | 2830 | 4066 | 3012 |
| N>=300, t>=3 | 2 | 6 | 111 | 428 | 964 | 407 | 513 | 1473 | 711 | 990 | 1407 | 2541 | 1909 |
| N>=300, t>=4 | 2 | 0 | 6 | 42 | 73 | 15 | 31 | 183 | 63 | 118 | 149 | 427 | 327 |
| N>=1000, t>=2 | 0 | 0 | 0 | 0 | 35 | 45 | 113 | 735 | 347 | 557 | 1260 | 2691 | 2040 |
| N>=1000, t>=3 | 0 | 0 | 0 | 0 | 1 | 2 | 4 | 151 | 51 | 96 | 320 | 1278 | 982 |
| N>=1000, t>=4 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 2 | 2 | 1 | 9 | 83 | 94 |
| REF N>=300, t>=3, t on trailing 52 wk | 2 | 6 | 111 | 830 | 1545 | 469 | 403 | 999 | 270 | 513 | 864 | 1422 | 1231 |

Best-of-9 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check vs zero, 9 main versions; REFERENCE not counted): best version by mean = **N>=1000, t>=4**, 200 $/lot/wk, haircut 96, after penalty **105**, RC p **0.19**; 8 of 9 versions above zero, median 162. **FAIL** (PASS = after penalty > 0 and p <= 0.10).

## London (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books held first / mean / last date | books ever | books changed per date (adds + drops) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | -285 | -230 | -110 | 17567 | -3431 | -133 | -63 | -80 | -199 | 3769 / 1324 / 633 | 12047 | 1708 |
| N>=100, t>=3 | -229 | -98 | -70 | 13586 | -5823 | -187 | 42 | -140 | -85 | 995 / 329 / 162 | 3362 | 477 |
| N>=100, t>=4 | -231 | -26 | -80 | 14344 | -6462 | -198 | -20 | -120 | -65 | 146 / 29 / 11 | 330 | 42 |
| N>=300, t>=2 | -322 | -271 | -160 | 26883 | -3672 | -267 | -120 | -121 | -227 | 355 / 690 / 504 | 6117 | 987 |
| N>=300, t>=3 | -227 | -71 | -78 | 15580 | -6141 | -34 | -14 | -167 | -60 | 16 / 146 / 135 | 1416 | 230 |
| N>=300, t>=4 | -222 | 126 | -369 | 62734 | -9685 | -1092 | -322 | -268 | -333 | 1 / 7 / 11 | 89 | 14 |
| N>=1000, t>=2 | -385 | -342 | -152 | 31778 | -3079 | 0 | 77 | -289 | -310 | 0 / 134 / 237 | 1127 | 175 |
| N>=1000, t>=3 | -162 | 16 | -159 | 39125 | -6073 | 0 | 133 | -477 | -171 | 0 / 20 / 65 | 205 | 30 |
| N>=1000, t>=4 | -1457 | -289 | 33 | 30061 | -11318 | 0 | 0 | 242 | -179 | 0 / 1 / 4 | 7 | 1 |
| REFERENCE: N>=300, t>=3, t on trailing 52 wk | -182 | -107 | -89 | 15665 | -5231 | -34 | -34 | -148 | -100 | 16 / 124 / 89 | 1434 | 231 |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | | |

3 x 3 grid, $/lot/wk (whole out-of-sample): rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | -110 | -70 | -80 | -87 |
| 300 | -160 | -78 | -369 | -203 |
| 1000 | -152 | -159 | 33 | -93 |
| mean over N | -141 | -103 | -139 | |

3 x 3 grid, L6M $/lot/wk: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | -230 | -98 | -26 | -118 |
| 300 | -271 | -71 | 126 | -72 |
| 1000 | -342 | 16 | -289 | -205 |
| mean over N | -281 | -51 | -63 | |

3 x 3 grid, max DD $/lot: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | 17567 | 13586 | 14344 | 15165 |
| 300 | 26883 | 15580 | 62734 | 35066 |
| 1000 | 31778 | 39125 | 30061 | 33655 |
| mean over N | 25409 | 22764 | 35713 | |

Slope ($/lot/wk): as T rises (mean over N) -141 -> -103 -> -139 = **not monotonic**; as N rises (mean over T) -87 -> -203 -> -93 = **not monotonic**.

Books held at each re-qualify date (first 6 dates then last, week index of the date = 26, 39, ...):

| version | 2023-10-01 | 2023-12-31 | 2024-03-31 | 2024-06-30 | 2024-09-29 | 2024-12-29 | 2025-03-30 | 2025-06-29 | 2025-09-28 | 2025-12-28 | 2026-03-29 | 2026-06-28 | 2026-09-27 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | 3769 | 2563 | 2228 | 1088 | 1198 | 828 | 840 | 924 | 854 | 916 | 803 | 564 | 633 |
| N>=100, t>=3 | 995 | 598 | 463 | 198 | 423 | 357 | 203 | 209 | 174 | 202 | 152 | 141 | 162 |
| N>=100, t>=4 | 146 | 41 | 29 | 7 | 37 | 60 | 10 | 6 | 7 | 5 | 4 | 8 | 11 |
| N>=300, t>=2 | 355 | 709 | 1208 | 622 | 935 | 647 | 663 | 736 | 704 | 770 | 669 | 447 | 504 |
| N>=300, t>=3 | 16 | 128 | 198 | 85 | 263 | 273 | 137 | 172 | 129 | 144 | 116 | 101 | 135 |
| N>=300, t>=4 | 1 | 11 | 13 | 3 | 7 | 33 | 5 | 3 | 2 | 1 | 1 | 6 | 11 |
| N>=1000, t>=2 | 0 | 0 | 3 | 3 | 28 | 54 | 127 | 279 | 275 | 270 | 288 | 183 | 237 |
| N>=1000, t>=3 | 0 | 0 | 0 | 0 | 4 | 9 | 6 | 35 | 40 | 37 | 37 | 32 | 65 |
| N>=1000, t>=4 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | 4 |
| REF N>=300, t>=3, t on trailing 52 wk | 16 | 128 | 198 | 109 | 385 | 151 | 97 | 138 | 73 | 95 | 67 | 60 | 89 |

Best-of-9 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check vs zero, 9 main versions; REFERENCE not counted): best version by mean = **N>=1000, t>=4**, 33 $/lot/wk, haircut 128, after penalty **-95**, RC p **0.84**; 1 of 9 versions above zero, median -110. **FAIL** (PASS = after penalty > 0 and p <= 0.10).

## NY AM (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books held first / mean / last date | books ever | books changed per date (adds + drops) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | -104 | -506 | -11 | 28338 | -5793 | -48 | 137 | 215 | -468 | 3999 / 4604 / 3215 | 28665 | 4468 |
| N>=100, t>=3 | 79 | -336 | 71 | 25437 | -6686 | 4 | 169 | 296 | -315 | 1309 / 1874 / 1207 | 13794 | 2201 |
| N>=100, t>=4 | 219 | -89 | 171 | 22316 | -6434 | 21 | 243 | 383 | -140 | 231 / 223 / 129 | 1893 | 297 |
| N>=300, t>=2 | -117 | -530 | -21 | 29488 | -6019 | -154 | 141 | 227 | -492 | 2129 / 4074 / 3053 | 24821 | 3928 |
| N>=300, t>=3 | 88 | -353 | 69 | 26670 | -6971 | -109 | 187 | 317 | -337 | 474 / 1592 / 1126 | 11312 | 1842 |
| N>=300, t>=4 | 254 | -85 | 182 | 23692 | -6732 | -163 | 280 | 428 | -145 | 35 / 169 / 116 | 1397 | 228 |
| N>=1000, t>=2 | -277 | -679 | -167 | 34647 | -6474 | -323 | -100 | 179 | -639 | 50 / 2603 / 2415 | 16005 | 2561 |
| N>=1000, t>=3 | -9 | -502 | 59 | 33400 | -8128 | -433 | 366 | 325 | -504 | 4 / 930 / 790 | 6778 | 1103 |
| N>=1000, t>=4 | 157 | -213 | 55 | 29822 | -8213 | 0 | -95 | 490 | -290 | 0 / 89 / 76 | 722 | 116 |
| REFERENCE: N>=300, t>=3, t on trailing 52 wk | 79 | -274 | 129 | 23204 | -6853 | -109 | 225 | 403 | -262 | 474 / 1238 / 244 | 12449 | 2036 |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | | |

3 x 3 grid, $/lot/wk (whole out-of-sample): rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | -11 | 71 | 171 | 77 |
| 300 | -21 | 69 | 182 | 76 |
| 1000 | -167 | 59 | 55 | -18 |
| mean over N | -66 | 66 | 136 | |

3 x 3 grid, L6M $/lot/wk: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | -506 | -336 | -89 | -310 |
| 300 | -530 | -353 | -85 | -323 |
| 1000 | -679 | -502 | -213 | -465 |
| mean over N | -572 | -397 | -129 | |

3 x 3 grid, max DD $/lot: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | 28338 | 25437 | 22316 | 25363 |
| 300 | 29488 | 26670 | 23692 | 26617 |
| 1000 | 34647 | 33400 | 29822 | 32623 |
| mean over N | 30824 | 28502 | 25277 | |

Slope ($/lot/wk): as T rises (mean over N) -66 -> 66 -> 136 = **steady up**; as N rises (mean over T) 77 -> 76 -> -18 = **steady down**.

Books held at each re-qualify date (first 6 dates then last, week index of the date = 26, 39, ...):

| version | 2023-10-01 | 2023-12-31 | 2024-03-31 | 2024-06-30 | 2024-09-29 | 2024-12-29 | 2025-03-30 | 2025-06-29 | 2025-09-28 | 2025-12-28 | 2026-03-29 | 2026-06-28 | 2026-09-27 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | 3999 | 3685 | 1671 | 1656 | 4302 | 5600 | 5379 | 5445 | 6440 | 7806 | 6270 | 4385 | 3215 |
| N>=100, t>=3 | 1309 | 1442 | 689 | 591 | 1303 | 2325 | 1934 | 2182 | 2851 | 3945 | 2795 | 1795 | 1207 |
| N>=100, t>=4 | 231 | 144 | 154 | 88 | 145 | 250 | 165 | 229 | 322 | 536 | 325 | 182 | 129 |
| N>=300, t>=2 | 2129 | 2341 | 1215 | 1240 | 3849 | 5101 | 4958 | 5149 | 6165 | 7529 | 6039 | 4196 | 3053 |
| N>=300, t>=3 | 474 | 595 | 429 | 392 | 1058 | 2074 | 1751 | 2009 | 2712 | 3772 | 2630 | 1672 | 1126 |
| N>=300, t>=4 | 35 | 33 | 66 | 54 | 107 | 197 | 129 | 199 | 292 | 508 | 302 | 164 | 116 |
| N>=1000, t>=2 | 50 | 136 | 120 | 139 | 1457 | 2873 | 3264 | 3778 | 4881 | 6286 | 5059 | 3383 | 2415 |
| N>=1000, t>=3 | 4 | 9 | 7 | 11 | 222 | 776 | 918 | 1256 | 1896 | 2942 | 2021 | 1236 | 790 |
| N>=1000, t>=4 | 0 | 0 | 0 | 0 | 6 | 34 | 35 | 119 | 188 | 376 | 207 | 112 | 76 |
| REF N>=300, t>=3, t on trailing 52 wk | 474 | 595 | 429 | 258 | 871 | 1358 | 1744 | 2277 | 2837 | 2834 | 1544 | 632 | 244 |

Best-of-9 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check vs zero, 9 main versions; REFERENCE not counted): best version by mean = **N>=300, t>=4**, 182 $/lot/wk, haircut 85, after penalty **96**, RC p **0.27**; 6 of 9 versions above zero, median 59. **FAIL** (PASS = after penalty > 0 and p <= 0.10).

## NY PM (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books held first / mean / last date | books ever | books changed per date (adds + drops) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | 32 | -106 | -132 | 23078 | -1855 | 4 | -196 | -64 | -181 | 1232 / 1068 / 650 | 8707 | 1361 |
| N>=100, t>=3 | 214 | 304 | -3 | 9590 | -3303 | -90 | -99 | 113 | -2 | 381 / 284 / 164 | 2524 | 392 |
| N>=100, t>=4 | 243 | 516 | 191 | 23391 | -4339 | -36 | 37 | 595 | -58 | 43 / 22 / 11 | 205 | 30 |
| N>=300, t>=2 | 36 | -123 | -162 | 27413 | -2108 | -146 | -227 | -67 | -208 | 404 / 789 / 578 | 6331 | 1016 |
| N>=300, t>=3 | 240 | 337 | -3 | 10499 | -3594 | -137 | -130 | 144 | 10 | 79 / 205 / 149 | 1734 | 283 |
| N>=300, t>=4 | 277 | 604 | 247 | 25561 | -5007 | -434 | 151 | 734 | -36 | 3 / 14 / 10 | 120 | 20 |
| N>=1000, t>=2 | -16 | -237 | -259 | 43873 | -2756 | 0 | -431 | -131 | -289 | 0 / 274 / 330 | 2160 | 345 |
| N>=1000, t>=3 | 267 | 313 | -34 | 23745 | -16675 | 0 | -232 | 136 | -13 | 0 / 69 / 98 | 544 | 86 |
| N>=1000, t>=4 | 201 | 556 | 160 | 23552 | -5389 | 0 | -105 | 578 | 11 | 0 / 5 / 8 | 32 | 5 |
| REFERENCE: N>=300, t>=3, t on trailing 52 wk | -15 | -243 | -119 | 21085 | -3398 | -137 | -128 | 74 | -344 | 79 / 172 / 47 | 1942 | 314 |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | | |

3 x 3 grid, $/lot/wk (whole out-of-sample): rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | -132 | -3 | 191 | 19 |
| 300 | -162 | -3 | 247 | 27 |
| 1000 | -259 | -34 | 160 | -44 |
| mean over N | -185 | -13 | 199 | |

3 x 3 grid, L6M $/lot/wk: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | -106 | 304 | 516 | 238 |
| 300 | -123 | 337 | 604 | 272 |
| 1000 | -237 | 313 | 556 | 211 |
| mean over N | -156 | 318 | 559 | |

3 x 3 grid, max DD $/lot: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | 23078 | 9590 | 23391 | 18686 |
| 300 | 27413 | 10499 | 25561 | 21158 |
| 1000 | 43873 | 23745 | 23552 | 30390 |
| mean over N | 31455 | 14611 | 24168 | |

Slope ($/lot/wk): as T rises (mean over N) -185 -> -13 -> 199 = **steady up**; as N rises (mean over T) 19 -> 27 -> -44 = **not monotonic**.

Books held at each re-qualify date (first 6 dates then last, week index of the date = 26, 39, ...):

| version | 2023-10-01 | 2023-12-31 | 2024-03-31 | 2024-06-30 | 2024-09-29 | 2024-12-29 | 2025-03-30 | 2025-06-29 | 2025-09-28 | 2025-12-28 | 2026-03-29 | 2026-06-28 | 2026-09-27 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | 1232 | 1390 | 1366 | 2208 | 1460 | 936 | 852 | 888 | 809 | 798 | 636 | 662 | 650 |
| N>=100, t>=3 | 381 | 340 | 395 | 651 | 359 | 223 | 240 | 228 | 201 | 238 | 141 | 129 | 164 |
| N>=100, t>=4 | 43 | 32 | 35 | 27 | 26 | 15 | 16 | 21 | 16 | 18 | 15 | 9 | 11 |
| N>=300, t>=2 | 404 | 708 | 912 | 1761 | 1182 | 730 | 657 | 748 | 712 | 731 | 553 | 586 | 578 |
| N>=300, t>=3 | 79 | 117 | 261 | 526 | 288 | 186 | 195 | 212 | 187 | 223 | 126 | 116 | 149 |
| N>=300, t>=4 | 3 | 12 | 21 | 19 | 24 | 12 | 12 | 21 | 16 | 17 | 13 | 7 | 10 |
| N>=1000, t>=2 | 0 | 13 | 22 | 289 | 368 | 239 | 274 | 401 | 393 | 463 | 382 | 386 | 330 |
| N>=1000, t>=3 | 0 | 0 | 1 | 57 | 68 | 41 | 62 | 118 | 115 | 151 | 97 | 89 | 98 |
| N>=1000, t>=4 | 0 | 0 | 0 | 0 | 2 | 0 | 1 | 7 | 14 | 12 | 13 | 5 | 8 |
| REF N>=300, t>=3, t on trailing 52 wk | 79 | 117 | 261 | 567 | 347 | 168 | 119 | 158 | 110 | 114 | 115 | 40 | 47 |

Best-of-9 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check vs zero, 9 main versions; REFERENCE not counted): best version by mean = **N>=300, t>=4**, 247 $/lot/wk, haircut 112, after penalty **135**, RC p **0.20**; 3 of 9 versions above zero, median -3. **FAIL** (PASS = after penalty > 0 and p <= 0.10).

## Four sessions summed (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023 Q4 | 2024 | 2025 | 2026 | books held first / mean / last date | books ever | books changed per date (adds + drops) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | -13 | -158 | -9 | 14252 | -4322 | -79 | 18 | 118 | -182 | 9459 / 9455 / 7862 | 66414 | 10178 |
| N>=100, t>=3 | 106 | -61 | 61 | 12492 | -5248 | -75 | 87 | 190 | -90 | 2791 / 3764 / 3679 | 30437 | 4751 |
| N>=100, t>=4 | 213 | 71 | 134 | 11952 | -5648 | -55 | 154 | 275 | -11 | 438 / 437 / 539 | 4070 | 619 |
| N>=300, t>=2 | -11 | -172 | -35 | 15608 | -4723 | -167 | -32 | 126 | -200 | 2892 / 7340 / 7147 | 49991 | 7897 |
| N>=300, t>=3 | 112 | -74 | 40 | 13976 | -5780 | -110 | 29 | 206 | -108 | 571 / 2824 / 3319 | 22157 | 3522 |
| N>=300, t>=4 | 218 | 61 | 139 | 13032 | -6023 | -195 | 154 | 334 | -20 | 41 / 302 / 464 | 2691 | 421 |
| N>=1000, t>=2 | -90 | -304 | -182 | 33830 | -5755 | -323 | -283 | 91 | -356 | 50 / 3613 / 5022 | 24085 | 3730 |
| N>=1000, t>=3 | 95 | -245 | -44 | 25877 | -7495 | -433 | -37 | 263 | -319 | 4 / 1241 / 1935 | 9656 | 1496 |
| N>=1000, t>=4 | 319 | -84 | 74 | 25739 | -8028 | 0 | -98 | 485 | -209 | 0 / 109 / 182 | 918 | 140 |
| REFERENCE: N>=300, t>=3, t on trailing 52 wk | 145 | -2 | 85 | 13332 | -5844 | -110 | 10 | 315 | -54 | 571 / 2201 / 1611 | 23187 | 3716 |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | | |

3 x 3 grid, $/lot/wk (whole out-of-sample): rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | -9 | 61 | 134 | 62 |
| 300 | -35 | 40 | 139 | 48 |
| 1000 | -182 | -44 | 74 | -50 |
| mean over N | -75 | 19 | 116 | |

3 x 3 grid, L6M $/lot/wk: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | -158 | -61 | 71 | -49 |
| 300 | -172 | -74 | 61 | -62 |
| 1000 | -304 | -245 | -84 | -211 |
| mean over N | -212 | -127 | 16 | |

3 x 3 grid, max DD $/lot: rows = min trades N, columns = t-stat T

| N \ T | 2 | 3 | 4 | mean over T |
|---|---|---|---|---|
| 100 | 14252 | 12492 | 11952 | 12899 |
| 300 | 15608 | 13976 | 13032 | 14205 |
| 1000 | 33830 | 25877 | 25739 | 28482 |
| mean over N | 21230 | 17449 | 16908 | |

Slope ($/lot/wk): as T rises (mean over N) -75 -> 19 -> 116 = **steady up**; as N rises (mean over T) 62 -> 48 -> -50 = **steady down**.

Books held at each re-qualify date (first 6 dates then last, week index of the date = 26, 39, ...):

| version | 2023-10-01 | 2023-12-31 | 2024-03-31 | 2024-06-30 | 2024-09-29 | 2024-12-29 | 2025-03-30 | 2025-06-29 | 2025-09-28 | 2025-12-28 | 2026-03-29 | 2026-06-28 | 2026-09-27 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N>=100, t>=2 | 9459 | 8578 | 7038 | 7508 | 10367 | 9095 | 8921 | 10758 | 10215 | 11928 | 11064 | 10119 | 7862 |
| N>=100, t>=3 | 2791 | 2609 | 1997 | 2547 | 4041 | 3761 | 3244 | 4620 | 4212 | 5700 | 4809 | 4921 | 3679 |
| N>=100, t>=4 | 438 | 244 | 243 | 270 | 463 | 381 | 255 | 518 | 433 | 711 | 515 | 665 | 539 |
| N>=300, t>=2 | 2892 | 3843 | 3947 | 5017 | 8301 | 7610 | 7648 | 9458 | 9231 | 10946 | 10091 | 9295 | 7147 |
| N>=300, t>=3 | 571 | 846 | 999 | 1431 | 2573 | 2940 | 2596 | 3866 | 3739 | 5129 | 4279 | 4430 | 3319 |
| N>=300, t>=4 | 41 | 56 | 106 | 118 | 211 | 257 | 177 | 406 | 373 | 644 | 465 | 604 | 464 |
| N>=1000, t>=2 | 50 | 149 | 145 | 431 | 1888 | 3211 | 3778 | 5193 | 5896 | 7576 | 6989 | 6643 | 5022 |
| N>=1000, t>=3 | 4 | 9 | 8 | 68 | 295 | 828 | 990 | 1560 | 2102 | 3226 | 2475 | 2635 | 1935 |
| N>=1000, t>=4 | 0 | 0 | 0 | 0 | 8 | 35 | 37 | 129 | 205 | 389 | 229 | 201 | 182 |
| REF N>=300, t>=3, t on trailing 52 wk | 571 | 846 | 999 | 1764 | 3148 | 2146 | 2363 | 3572 | 3290 | 3556 | 2590 | 2154 | 1611 |

Best-of-9 luck penalty (block bootstrap, block 4 wk, 2,000 draws, White reality check vs zero, 9 main versions; REFERENCE not counted): best version by mean = **N>=300, t>=4**, 139 $/lot/wk, haircut 72, after penalty **67**, RC p **0.28**; 5 of 9 versions above zero, median 40. **FAIL** (PASS = after penalty > 0 and p <= 0.10).

## T2: the 20 live books under each of the 9 rules (QUICK SCREEN)

First re-qualify date (13-week dates) at which the live book's own grid cell passes all four conditions, then the cell's $/wk (1 lot) and max drawdown from that date to 2026-10-25. "never" = no date passed. Books chosen with hindsight.

| live book (session) | N>=100 t>=2 | N>=100 t>=3 | N>=100 t>=4 | N>=300 t>=2 | N>=300 t>=3 | N>=300 t>=4 | N>=1000 t>=2 | N>=1000 t>=3 | N>=1000 t>=4 |
|---|---|---|---|---|---|---|---|---|---|
| Lb0e6dfa3_R0_F40_80 (Asia) | never | never | never | never | never | never | never | never | never |
| L385f4f2e_CX502 (Asia) | not mapped to a stored cell | | | | | | | | |
| L9c2622b0_R0_P45 (Asia) | 2025-06-29: 535/wk (DD 10773) | never | never | 2025-06-29: 535/wk (DD 10773) | never | never | never | never | never |
| L4aaacdb2_R0_P30 (Asia) | 2025-06-29: 533/wk (DD 4693) | never | never | 2025-06-29: 533/wk (DD 4693) | never | never | 2026-06-28: 782/wk (DD 1283) | never | never |
| L19201dfc.BRF90_30 (London) | 2026-09-27: 445/wk (DD 2423) | 2026-09-27: 445/wk (DD 2423) | never | 2026-09-27: 445/wk (DD 2423) | 2026-09-27: 445/wk (DD 2423) | never | 2026-09-27: 445/wk (DD 2423) | 2026-09-27: 445/wk (DD 2423) | never |
| L12842dde.BRP45 (London) | never | never | never | never | never | never | never | never | never |
| L74274eca.BRF120_60 (London) | never | never | never | never | never | never | never | never | never |
| L43f0cbfb.BRS8U (NYAM) | never | never | never | never | never | never | never | never | never |
| B7bfd33b7 (NYAM) | not mapped to a stored cell | | | | | | | | |
| Bf428c4a1.BRS8U (NYAM) | not mapped to a stored cell | | | | | | | | |
| Le4fede95.BRF90_30 (NYAM) | 2025-06-29: 816/wk (DD 38080) | never | never | 2025-06-29: 816/wk (DD 38080) | never | never | 2025-06-29: 816/wk (DD 38080) | never | never |
| Lf0346d55.BRP60 (NYAM) | 2025-12-28: 311/wk (DD 38442) | never | never | 2025-12-28: 311/wk (DD 38442) | never | never | 2025-12-28: 311/wk (DD 38442) | never | never |
| L8cfda948.BRF90_30 (NYAM) | 2024-09-29: 705/wk (DD 48332) | 2025-06-29: 324/wk (DD 48332) | never | 2024-09-29: 705/wk (DD 48332) | 2025-06-29: 324/wk (DD 48332) | never | 2025-03-30: 621/wk (DD 48332) | 2025-06-29: 324/wk (DD 48332) | never |
| L4407508c.BRF120_60 (NYAM) | 2026-06-28: 1188/wk (DD 3192) | never | never | 2026-06-28: 1188/wk (DD 3192) | never | never | never | never | never |
| L39287638.BRF80_40 (NYAM) | 2025-03-30: 431/wk (DD 11011) | 2025-03-30: 431/wk (DD 11011) | never | 2025-03-30: 431/wk (DD 11011) | 2025-03-30: 431/wk (DD 11011) | never | never | never | never |
| L64390867.BRF80_40 (NYAM) | never | never | never | never | never | never | never | never | never |
| L52359bf4_R0_P30 (NYPM) | never | never | never | never | never | never | never | never | never |
| L8e0bf58c_R0_S8U (NYPM) | never | never | never | never | never | never | never | never | never |
| L4bdd521a_R0_F80_40 (NYPM) | never | never | never | never | never | never | never | never | never |
| L2c6916a5_R0_P60 (NYPM) | never | never | never | never | never | never | never | never | never |
| **qualified / mapped; mean $/wk after, of the books that qualified** | 8 / 17; 620 | 3 / 17; 400 | 0 / 17; - | 8 / 17; 620 | 3 / 17; 400 | 0 / 17; - | 5 / 17; 595 | 2 / 17; 384 | 0 / 17; - |

## What was run (choices where the order is silent, marked)

- Cell qualifies at a date if ALL: trades to date >= N; t-stat of weekly P&L to date >= T (mean / (sd / sqrt(n)) over all n weeks to date, zero weeks included; **choice**); profitable in >= 75% of fully-past calendar half-years (2023 H2 is the first counted; before 2024-01-01 the test passes everything; **same as Test 3**); family share >= 70% of the stored cells of its test-2 family (bar type, module, variant) profitable over all history to date (Test 3 definition).
- One cell per BOOK = group (bar type and size file, module, variant, params, side; the Part B group) = lower-median qualified bracket by history score (mean weekly points per max(max drawdown points, 2.5), as Test 3); then at most one book per family = the one with the most trades to date. HOLD ALL, equal weight, no K, no ranking, no spread rule. Re-qualify every 13 weeks (26, 39, ..., 182 from 2023-04-02). **Choice:** a held book stays while its held CELL still passes all four conditions (a held book leaves only when it fails); freed families are refilled by the same rule; books are not swapped for a better bracket while they qualify.
- **REFERENCE (one row per session, choice of cell):** N=300, t>=3 with requirement (2) measured on the trailing 52 weeks (all weeks when fewer exist); the order says "the same rule", so the middle cell of the grid was used; no other REFERENCE variant was run.
- Per lot = basket P&L / number of books held (cash weeks 0). Four-session sum = summed P&L / summed number of books held that week. Best-of-9 luck penalty = median of the bootstrap maximum over the 9 versions (White reality check vs zero, same code as Tests 2 and 3). PASS = after penalty > 0 and p <= 0.10.
- Best version for the exact part: by mean = the version the reality check evaluates (Asia N1000 t4, London N1000 t4, NY AM N300 t4, NY PM N300 t4). **Note for LEAD:** by income per unit max drawdown (the Test 3 convention) Asia would be N>=100, t>=3 with 10,757 cells ever held, ~tens of thousands of set-months; the by-mean version holds 157 cells. See the EXACT section for which was queued and why.
