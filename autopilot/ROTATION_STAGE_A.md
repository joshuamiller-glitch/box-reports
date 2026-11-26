# ROTATION TEST, STAGE A: QUICK SCREEN (W-ROTA)

**QUICK SCREEN label on every number below**: grid weekly arrays (th_grid/gcore2 tape walk, NOT the exact engine, not calibrated against it), 1 NQ lot per book at $20/point, grid cost 4.84 USD round trip in, no stack rules / account layers / depth fills. Stage B (exact engine on the picked books) is in ROTATION_STAGE_B.md.

Walk: weekly arrays from 2023-04-02 (week 0), out-of-sample weeks 26..185 = 2023-10-01 to 2026-10-25 (160 weeks; 2025-11 holes are zeros for every cell alike). Candidate set per session: every grid cell (file x param x bracket x mode both/long/short) with >= 5 trades in total, from bfl17 (17 brackets) + real + p1real (bfl17 supersedes where the same row/module exists): **Asia 14,501,940; London 16,818,394; NY AM 17,767,116; NY PM 17,777,269 cells (66.9 M)**; cells with < 5 trades over 3.6 years are the only cut (data-independent of the ranking window except that it looks at the whole span; nothing else filters). Ranking at date w uses only weeks < w. Lookbacks 2w,3w,1M(4w),3M(13w),4M(17w),5M(22w),6M(26w). Refit steps 1,2,3,4 weeks (all chains start at week 26 so every row covers the same 160 weeks). Top 3/5/8 per session, 1 lot each, equal weight (N lots summed; "per lot" divides by N).

Rank keys (the order says drawdown first, ulcer, $/wk tie-break; literal ulcer-ascending picks near-flat books, so three keys are run and shown): **U** = ulcer ascending among profitable books (tie: $/wk); **M** = $/wk per unit ulcer (ulcer floor 2.5 pts); **P** = $/wk only. Eligible: window P&L > 0 and >= 10 trades (for 2w/3w the "no minimum" row beside uses >= 1 trade; for 1M and longer 10 trades is never binding). Ulcer = RMS of the drawdown of the cumulative weekly P&L inside the window (weekly, coarser than daily).

Near-duplicates: same (bar type, module, variant) family counts once; and weekly-P&L correlation >= tau with a book already picked over the last 26 weeks skips the candidate; tau 0.7 / 0.8 (headline) / 0.9 all run. Identical-signal twins have correlation 1 and are skipped by that rule.

Prior-year filter (graded): pass if (worst fully-past calendar year weekly income) / (lookback weekly income) x 100 >= mark, marks -50..+50 (rows W-50 .. W+50); the same with the weekly average of ALL data older than the lookback window (A-50 .. A+50); "none" = no filter. 2023 counts as a fully-past year from 2024 (data starts April 2023, 39 weeks); with no past data the book passes. Dates in 2023 therefore run effectively unfiltered for W levels.

Rows tried: 20,412 configs per session (7+2 lookbacks x 3 ranks x 21 levels x 3 tau x 3 N x 4 steps). Reference = today's fixed mixes held throughout, built from the same grid arrays with the live bracket of each book (17 of 20 books found; **missing: Asia L385f4f2e_CX502, NY AM B7bfd33b7 and Bf428c4a1.BRS8U**, no grid cell) and picked with the last 6 months in view (hindsight-flattered).

## ANSWER FIRST (QUICK SCREEN)

1. **Unfiltered rotation on the whole candidate set loses money out of sample.** Median over all unfiltered rows (tau 0.8, all N/steps/ranks, lookbacks 13-26 weeks), four sessions per lot per week: **-63 $**; for the short lookbacks (2w-1M) **-301 $**. The fixed mixes (hindsight) earn 529 $ per lot per week on the same weeks. Selecting from 67 M cells by a trailing window picks cells that were lucky in the window.
2. **The prior-year filter is what makes rotation positive.** Median $/lot/wk (four sessions, lookbacks 3M-6M) by level: none -63; best three levels: W+10 61, A+10 30, W+20 11. The gain is large against none but small against the hindsight fixed mix (529).
3. **Best-of-rows luck penalty** (block bootstrap over weeks, 2,000 draws, block 4 weeks, White reality check on 20,412 rows, four sessions summed, per-lot $/wk): best row vs zero earns 387 $/lot/wk, luck haircut 359, left after haircut **28**, reality-check p = **0.11**. Against the fixed mixes: best row -89 $/lot/wk, p = **1.00** (no row beats the hindsight mix; 0 of 20,412 rows are above it). So rotation does **not** beat holding today's mixes on the quick screen, and the best rotation row is only marginally distinguishable from luck.
4. Per session see the tables; reading order: recent first (L6M, L3M of the out-of-sample curve), then years 2023-2026.

## Reference rows: today's mixes held (QUICK SCREEN, same weeks)

| scope | $/wk | max DD | ulcer | worst wk | L6M $/wk | L3M $/wk | 2023 (Oct-Dec) | 2024 | 2025 | 2026 | books |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,423 | 14,492 | 3,060 | -9,157 | 2,356 | 2,946 | 889 | 1,325 | 1,141 | 2,066 | 3 |
| London | 1,457 | 28,293 | 7,762 | -15,590 | 3,775 | 3,938 | 1,416 | 1,227 | 773 | 2,618 | 3 |
| NY AM | 4,456 | 48,273 | 11,697 | -25,303 | 10,769 | 9,242 | 3,255 | 3,132 | 4,076 | 6,947 | 7 |
| NY PM | 1,665 | 40,161 | 13,614 | -26,308 | 3,677 | 3,722 | 2,135 | 912 | 1,732 | 2,367 | 4 |
| Four sessions summed | 9,001 | 60,062 | 11,156 | -33,566 | 20,576 | 19,848 | 7,696 | 6,596 | 7,722 | 13,998 | 17 |

Books used in the quick-screen mix: Asia: Lb0e6dfa3_R0_F40_80, L9c2622b0_R0_P45, L4aaacdb2_R0_P30; NYAM: L43f0cbfb.BRS8U, Le4fede95.BRF90_30, Lf0346d55.BRP60, L8cfda948.BRF90_30, L4407508c.BRF120_60, L39287638.BRF80_40, L64390867.BRF80_40; NYPM: L52359bf4_R0_P30, L8e0bf58c_R0_S8U, L4bdd521a_R0_F80_40, L2c6916a5_R0_P60; London: L19201dfc.BRF90_30, L12842dde.BRP45, L74274eca.BRF120_60. Missing: Asia: L385f4f2e_CX502; NYAM: B7bfd33b7, Bf428c4a1.BRS8U.

## Asia

### Best rows (N=5, step 2 weeks, tau 0.8, ranked by drawdown-first return per ulcer), lookback x rank x level; recent first

| lookback | rank | level | L3M $/wk | L6M $/wk | $/wk | max DD | ulcer | worst wk | 2023/24/25/26 $/wk | turnover/refit | blocks beating fixed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 3w | M | A+30 | 0 | 0 | 869 | 6,458 | 2,320 | -6,458 | 1,937/1,397/610/212 | 1.00 | 36% |
| 2w | P | A+30 | 0 | 0 | 640 | 11,543 | 2,178 | -5,156 | 1,183/1,004/192/586 | 1.00 | 31% |
| 2w | M | A+30 | 0 | 0 | 608 | 11,209 | 2,088 | -5,156 | 1,140/1,003/192/478 | 1.00 | 31% |
| 5M | U | W+20 | 31 | -26 | 553 | 10,665 | 3,850 | -7,148 | -305/707/928/155 | 0.74 | 31% |
| 3w | P | A+30 | 0 | 0 | 808 | 9,371 | 5,708 | -9,371 | 1,413/1,323/794/0 | 1.00 | 36% |
| 3M | M | A+50 | 694 | 258 | 1,001 | 22,039 | 7,267 | -15,570 | 991/1,004/931/1,087 | 0.92 | 36% |
| 4M | P | W+50 | 0 | 0 | 919 | 15,658 | 6,910 | -10,249 | 948/2,611/-20/0 | 0.95 | 36% |
| 6M | M | A+20 | 1,072 | 3,033 | 1,019 | 31,394 | 7,945 | -25,907 | -601/1,181/347/2,168 | 0.77 | 35% |
| 6M | M | W+30 | -181 | 105 | 517 | 13,319 | 4,490 | -7,157 | -160/898/339/480 | 0.72 | 31% |
| 6M | M | W+20 | 1,857 | 1,779 | 842 | 29,021 | 7,654 | -7,665 | -160/1,690/328/752 | 0.71 | 31% |
| 5M | M | A+30 | 810 | 2,430 | 1,145 | 31,683 | 10,774 | -19,116 | -201/923/961/2,068 | 0.81 | 38% |
| 3w | M | A+10 | 1,004 | 3,313 | 2,021 | 54,675 | 19,928 | -27,543 | -480/2,626/1,597/2,580 | 0.99 | 42% |

### Median $/wk per lot by lookback x rank key (no filter) and with the best three levels (tau 0.8, all N, all steps)

| level | 2w | 3w | 1M | 3M | 4M | 5M | 6M |
|---|---|---|---|---|---|---|---|
| none | -479 | -246 | -217 | -206 | 33 | 0 | 103 |
| A+20 | 47 | 96 | 31 | 146 | 108 | 125 | 62 |
| A+30 | 116 | 148 | 56 | 98 | 91 | 130 | 91 |
| A+10 | 56 | 153 | -23 | 16 | 81 | 136 | 85 |

Per-level medians, lookbacks 1M-6M, $/lot/wk: A+20 101, A+30 87, A+10 82, W+10 66, W+30 58, A+50 55, W+20 53, W+50 51, W+0 41, A+0 15, A-10 -16, W-20 -17, A-20 -28, W-30 -28, W-40 -31, W-50 -35, none -36, W-10 -36, A-30 -37, A-40 -38, A-50 -39

### 2w/3w: minimum 10 trades vs no minimum (median $/wk per lot, N all, steps all)

- 2w: >=10 trades -264, no minimum -120
- 3w: >=10 trades -85, no minimum -43

Luck penalty (20,412 rows): best row vs zero 231 $/lot/wk, haircut 592, after -361, RC p=0.20; vs fixed mix best 46, RC p=1.00, rows above fixed: 2.

## London

### Best rows (N=5, step 2 weeks, tau 0.8, ranked by drawdown-first return per ulcer), lookback x rank x level; recent first

| lookback | rank | level | L3M $/wk | L6M $/wk | $/wk | max DD | ulcer | worst wk | 2023/24/25/26 $/wk | turnover/refit | blocks beating fixed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1M | P | A+30 | 0 | 0 | 337 | 19,253 | 4,539 | -14,572 | 1,251/482/237/0 | 0.99 | 38% |
| 3M | M | A-10 | -969 | 3,435 | 1,134 | 45,672 | 18,839 | -28,988 | -999/806/1,102/2,241 | 0.86 | 42% |
| 3M | P | W+10 | 6,624 | 4,952 | 1,401 | 68,306 | 28,599 | -34,024 | -256/-46/2,838/1,894 | 0.83 | 42% |
| 3M | M | A-30 | -969 | 3,435 | 925 | 59,961 | 20,434 | -33,356 | 890/426/361/2,262 | 0.86 | 40% |
| 3M | M | A-50 | -969 | 3,435 | 892 | 59,961 | 20,437 | -33,356 | 485/426/361/2,262 | 0.86 | 40% |
| 3M | M | A-40 | -969 | 3,435 | 891 | 59,961 | 20,437 | -33,356 | 480/426/361/2,262 | 0.86 | 40% |
| 3M | M | W-50 | -969 | 3,435 | 856 | 59,961 | 20,474 | -33,356 | 42/426/361/2,262 | 0.86 | 40% |
| 3M | M | none | -969 | 3,435 | 856 | 59,961 | 20,474 | -33,356 | 42/426/361/2,262 | 0.86 | 40% |
| 3M | M | W-40 | -969 | 3,435 | 837 | 59,961 | 20,621 | -33,356 | 42/426/305/2,262 | 0.86 | 40% |
| 3M | M | A-20 | -969 | 3,435 | 756 | 59,534 | 20,880 | -33,356 | -513/320/300/2,262 | 0.86 | 41% |
| 3M | M | W-20 | -969 | 1,756 | 768 | 48,664 | 21,640 | -31,462 | 42/283/1,145/1,116 | 0.86 | 40% |
| 3M | M | W-30 | -969 | 3,435 | 743 | 59,961 | 21,390 | -33,356 | 42/136/305/2,262 | 0.87 | 39% |

### Median $/wk per lot by lookback x rank key (no filter) and with the best three levels (tau 0.8, all N, all steps)

| level | 2w | 3w | 1M | 3M | 4M | 5M | 6M |
|---|---|---|---|---|---|---|---|
| none | -289 | -281 | -382 | -66 | -245 | -63 | -74 |
| A+50 | -4 | -22 | -25 | -54 | -1 | -26 | 38 |
| W+50 | -34 | -38 | -46 | -52 | -67 | -34 | -2 |
| A+30 | -71 | -55 | -37 | -120 | -10 | -47 | -30 |

Per-level medians, lookbacks 1M-6M, $/lot/wk: A+50 -20, W+50 -41, A+30 -43, W+10 -55, A+10 -60, W+30 -63, A+20 -67, W+20 -75, W+0 -95, A+0 -124, A-10 -137, W-40 -152, A-30 -153, W-20 -155, W-30 -156, A-40 -158, A-50 -159, none -159, A-20 -160, W-50 -164, W-10 -172

### 2w/3w: minimum 10 trades vs no minimum (median $/wk per lot, N all, steps all)

- 2w: >=10 trades -189, no minimum -223
- 3w: >=10 trades -212, no minimum -200

Luck penalty (20,412 rows): best row vs zero 515 $/lot/wk, haircut 586, after -71, RC p=0.46; vs fixed mix best 165, RC p=1.00, rows above fixed: 5.

## NY AM

### Best rows (N=5, step 2 weeks, tau 0.8, ranked by drawdown-first return per ulcer), lookback x rank x level; recent first

| lookback | rank | level | L3M $/wk | L6M $/wk | $/wk | max DD | ulcer | worst wk | 2023/24/25/26 $/wk | turnover/refit | blocks beating fixed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 5M | P | A+0 | 4,092 | 3,994 | 2,989 | 65,523 | 26,125 | -41,997 | 118/2,488/3,136/4,313 | 0.66 | 55% |
| 1M | M | W+20 | 513 | 256 | 1,823 | 52,957 | 16,846 | -30,192 | 887/1,991/3,042/367 | 0.98 | 40% |
| 4M | P | A+50 | 0 | -921 | 2,479 | 64,698 | 25,148 | -38,196 | 3,765/1,139/4,897/690 | 0.84 | 46% |
| 1M | U | A+20 | 4,950 | 4,569 | 3,054 | 102,084 | 31,095 | -42,684 | 1,109/2,431/3,138/4,323 | 0.99 | 54% |
| 2w | M | A+20 | 0 | -858 | 1,504 | 52,517 | 15,942 | -38,456 | -918/1,394/3,270/159 | 1.00 | 44% |
| 5M | P | A+10 | 1,158 | -1,319 | 2,946 | 98,037 | 33,301 | -36,492 | 730/2,550/5,001/1,529 | 0.66 | 49% |
| 3w | M | A+20 | -904 | -1,703 | 2,666 | 76,189 | 30,934 | -57,272 | 1,390/1,903/4,435/1,772 | 0.99 | 48% |
| 2w | P | A+20 | 0 | -858 | 1,430 | 56,491 | 16,699 | -38,456 | -918/1,218/3,222/159 | 1.00 | 44% |
| 3M | P | W+30 | 763 | 297 | 2,135 | 79,297 | 25,026 | -52,363 | -303/2,989/1,689/2,395 | 0.90 | 41% |
| 3M | U | A+30 | -239 | -1,124 | 1,888 | 59,923 | 24,587 | -25,421 | -508/818/4,404/781 | 0.88 | 42% |
| 3w | P | A+20 | 453 | -938 | 2,045 | 76,189 | 27,047 | -57,272 | 259/1,110/3,146/2,365 | 0.98 | 45% |
| 2w | M | W+50 | 0 | 0 | 276 | 18,602 | 3,692 | -11,436 | 1,853/385/0/0 | 1.00 | 35% |

### Median $/wk per lot by lookback x rank key (no filter) and with the best three levels (tau 0.8, all N, all steps)

| level | 2w | 3w | 1M | 3M | 4M | 5M | 6M |
|---|---|---|---|---|---|---|---|
| none | -46 | -240 | -295 | 214 | 259 | 159 | 63 |
| W+10 | 87 | 118 | 300 | 405 | 331 | 150 | 35 |
| A+10 | 183 | 146 | 183 | 331 | 340 | 198 | 53 |
| A+20 | 131 | 343 | 354 | 227 | 271 | -5 | 4 |

Per-level medians, lookbacks 1M-6M, $/lot/wk: W+10 315, A+10 255, A+20 246, W+0 218, A+0 191, A-10 168, W+20 148, A-20 136, W-20 135, A-30 135, A-50 128, A-40 127, none 126, W-50 126, W-40 123, W-30 121, A+30 121, W-10 121, W+30 104, A+50 20, W+50 19

### 2w/3w: minimum 10 trades vs no minimum (median $/wk per lot, N all, steps all)

- 2w: >=10 trades -3, no minimum -1
- 3w: >=10 trades -90, no minimum -48

Luck penalty (20,412 rows): best row vs zero 801 $/lot/wk, haircut 883, after -82, RC p=0.06; vs fixed mix best 573, RC p=0.99, rows above fixed: 265.

## NY PM

### Best rows (N=5, step 2 weeks, tau 0.8, ranked by drawdown-first return per ulcer), lookback x rank x level; recent first

| lookback | rank | level | L3M $/wk | L6M $/wk | $/wk | max DD | ulcer | worst wk | 2023/24/25/26 $/wk | turnover/refit | blocks beating fixed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 5M | P | A+50 | 752 | 1,422 | 1,352 | 55,171 | 16,558 | -22,303 | -1,877/3,359/-106/1,706 | 0.82 | 44% |
| 3M | P | W+10 | -869 | 313 | 1,529 | 73,535 | 24,085 | -28,373 | 909/1,505/1,860/1,333 | 0.82 | 50% |
| 3w | U | A+30 | -837 | 60 | 901 | 51,475 | 17,602 | -31,744 | -848/552/1,780/763 | 1.00 | 44% |
| 1M | M | A+30 | 0 | 0 | 663 | 35,666 | 14,852 | -20,594 | 2,248/1,090/287/118 | 0.99 | 36% |
| 3M | P | A+30 | -3,720 | 222 | 984 | 143,954 | 39,010 | -37,375 | 2,595/130/1,417/996 | 0.82 | 41% |
| 3M | P | A+10 | 928 | -337 | 983 | 94,727 | 39,684 | -35,776 | 1,877/1,616/1,374/-571 | 0.80 | 48% |
| 2w | P | A+10 | 3,235 | -641 | 811 | 69,426 | 36,330 | -45,900 | 266/-352/2,522/261 | 1.00 | 46% |
| 2w | M | A+10 | 3,235 | -641 | 872 | 88,801 | 39,186 | -45,900 | 266/103/2,370/123 | 1.00 | 46% |
| 3w | U | A-10 | -4,628 | -1,382 | 1,047 | 154,301 | 47,781 | -55,449 | -666/254/2,199/1,105 | 1.00 | 42% |
| 5M | P | W+20 | -7,136 | -1,588 | 1,117 | 112,958 | 50,962 | -36,126 | 782/-751/5,072/-1,459 | 0.72 | 50% |
| 2w | M | W+30 | 0 | 0 | 167 | 26,122 | 8,613 | -21,891 | -1,309/842/0/0 | 1.00 | 32% |
| 3w | P | A+30 | 0 | 0 | 146 | 37,648 | 9,376 | -15,571 | -1,522/684/182/-49 | 0.98 | 32% |

### Median $/wk per lot by lookback x rank key (no filter) and with the best three levels (tau 0.8, all N, all steps)

| level | 2w | 3w | 1M | 3M | 4M | 5M | 6M |
|---|---|---|---|---|---|---|---|
| none | -337 | -255 | -336 | -337 | -327 | -273 | -183 |
| W+50 | -35 | -40 | -13 | -15 | -13 | -48 | -46 |
| A+50 | -6 | -17 | -6 | 42 | -95 | -57 | -78 |
| W+30 | -10 | -43 | -24 | -17 | -106 | -94 | -81 |

Per-level medians, lookbacks 1M-6M, $/lot/wk: W+50 -29, A+50 -48, W+30 -66, W+20 -79, W+10 -80, A+30 -82, A+20 -119, A+10 -139, W+0 -222, A+0 -227, A-30 -273, W-20 -273, A-20 -277, A-40 -280, W-50 -285, none -285, W-10 -286, W-40 -287, W-30 -287, A-50 -289, A-10 -294

### 2w/3w: minimum 10 trades vs no minimum (median $/wk per lot, N all, steps all)

- 2w: >=10 trades -247, no minimum -175
- 3w: >=10 trades -187, no minimum -229

Luck penalty (20,412 rows): best row vs zero 571 $/lot/wk, haircut 774, after -202, RC p=0.73; vs fixed mix best 271, RC p=1.00, rows above fixed: 16.

## Four sessions summed

### Best rows (N=5, step 2 weeks, tau 0.8, ranked by drawdown-first return per ulcer), lookback x rank x level; recent first

| lookback | rank | level | L3M $/wk | L6M $/wk | $/wk | max DD | ulcer | worst wk | 2023/24/25/26 $/wk | turnover/refit | blocks beating fixed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 3M | P | W+30 | 340 | 85 | 3,108 | 86,481 | 25,773 | -53,525 | 1,558/3,506/3,628/2,439 | 0.91 | 31% |
| 1M | M | A+30 | 0 | 0 | 2,215 | 78,841 | 20,355 | -41,861 | 3,302/2,004/2,922/1,245 | 0.99 | 26% |
| 3M | P | W+10 | -1,126 | 3,445 | 5,217 | 171,804 | 51,242 | -74,109 | 1,558/1,988/8,550/6,141 | 0.83 | 36% |
| 4M | P | A+50 | 0 | -921 | 2,304 | 62,655 | 26,296 | -49,618 | 681/3,107/3,505/296 | 0.89 | 32% |
| 5M | P | W+10 | -618 | -1,504 | 3,604 | 152,785 | 51,866 | -92,513 | -4,110/4,755/5,430/2,263 | 0.70 | 38% |
| 3M | U | A+30 | -1,274 | -2,574 | 2,165 | 83,128 | 37,454 | -57,659 | -781/1,916/4,187/834 | 0.88 | 28% |
| 2w | M | A+10 | -1,390 | -1,036 | 3,802 | 158,766 | 71,722 | -91,272 | -5,784/977/10,424/1,912 | 1.00 | 36% |
| 3w | M | A+30 | 0 | 0 | 1,068 | 89,412 | 21,820 | -33,051 | -4,370/1,251/2,940/163 | 1.00 | 24% |
| 2w | P | W+20 | 0 | 0 | 1,517 | 126,281 | 31,898 | -35,413 | -1,864/2,918/1,145/1,299 | 1.00 | 30% |
| 3w | P | A+30 | 0 | 0 | 1,145 | 72,725 | 24,182 | -33,051 | -5,191/1,225/3,566/-49 | 0.99 | 22% |
| 2w | M | W+20 | 0 | 0 | 1,418 | 119,829 | 30,797 | -34,010 | -1,875/3,172/1,163/586 | 1.00 | 30% |
| 6M | U | A+30 | 1,821 | 951 | 479 | 34,014 | 11,333 | -13,740 | 392/945/-262/863 | 0.73 | 20% |

### Median $/wk per lot by lookback x rank key (no filter) and with the best three levels (tau 0.8, all N, all steps)

| level | 2w | 3w | 1M | 3M | 4M | 5M | 6M |
|---|---|---|---|---|---|---|---|
| none | -306 | -258 | -308 | -94 | -84 | -48 | -30 |
| W+10 | -39 | -19 | -59 | 92 | 95 | 7 | 10 |
| A+10 | 48 | -21 | -10 | 39 | 41 | 19 | 28 |
| A+30 | -1 | 46 | 37 | 40 | 6 | 7 | -2 |

Per-level medians, lookbacks 1M-6M, $/lot/wk: W+10 26, A+10 25, A+30 14, A+20 14, W+20 6, A+50 4, W+50 -2, W+30 -4, W+0 -22, A+0 -30, A-10 -59, W-20 -70, W-10 -76, A-30 -76, A-40 -79, A-50 -83, W-50 -84, W-30 -84, none -85, A-20 -85, W-40 -88

### 2w/3w: minimum 10 trades vs no minimum (median $/wk per lot, N all, steps all)

- 2w: >=10 trades -213, no minimum -186
- 3w: >=10 trades -158, no minimum -155

Luck penalty (20,412 rows): best row vs zero 387 $/lot/wk, haircut 359, after 28, RC p=0.11; vs fixed mix best -89, RC p=1.00, rows above fixed: 0.

## Sensitivity (four sessions summed, median $/lot/wk over the other dimensions, levels W+10..W+30 and A+10..A+30 only vs none)

- near-duplicate tau: 0.7: none -63 / graded 18; 0.8: none -63 / graded 16; 0.9: none -64 / graded 18
- refit step (weeks): 1: none -62 / graded 36; 2: none -63 / graded 23; 3: none -85 / graded 14; 4: none -46 / graded 3
- books per session N: 3: none -80 / graded 13; 5: none -64 / graded 19; 8: none -49 / graded 15
- rank key: M: none -45 / graded 5; P: none -87 / graded 70; U: none -63 / graded 7

## Turnover per refit (share of the N slots replaced; mean, tau 0.8, level none vs W+10; sessions in columns)

| lookback | step | Asia | London | NY AM | NY PM |
|---|---|---|---|---|---|
| 2w | 1 | 0.99 | 0.99 | 0.99 | 0.99 |
| 2w | 2 | 1.00 | 1.00 | 1.00 | 1.00 |
| 2w | 4 | 1.00 | 1.00 | 1.00 | 1.00 |
| 1M | 1 | 0.93 | 0.94 | 0.93 | 0.93 |
| 1M | 2 | 0.99 | 0.99 | 0.99 | 0.99 |
| 1M | 4 | 1.00 | 1.00 | 1.00 | 1.00 |
| 3M | 1 | 0.74 | 0.72 | 0.72 | 0.74 |
| 3M | 2 | 0.91 | 0.86 | 0.90 | 0.92 |
| 3M | 4 | 0.97 | 0.97 | 0.97 | 0.99 |
| 6M | 1 | 0.58 | 0.56 | 0.59 | 0.62 |
| 6M | 2 | 0.74 | 0.73 | 0.77 | 0.79 |
| 6M | 4 | 0.88 | 0.91 | 0.91 | 0.94 |

Turnover is lower at long lookbacks; the live file would need as many different books as the picks visit (see stage B list).

## Caveats
- Rows with L3M and L6M $/wk of 0 stopped trading: with a strict filter no book passes late in the walk (flat = no pick), which flatters return per ulcer; read those rows with the L6M/L3M columns.
- QUICK SCREEN only; stage B re-scores the picked books on the exact engine. Level modules written before 2026-11-18 06:00Z were stale (13 of 17); their cells are UNVERIFIED until the grid re-run stamps; picked cells carry this flag in the stage B pick list.
- Weekly bins, weekly ulcer. 202511 tape hole = zero weeks.
- The cell set is every cell with >= 5 trades (66.9 M), not the audit's 44.0 M (the audit counted cells by its own pass); sessions: the same cell can appear under several modes (both/long/short).
- Fixed-mix reference is hindsight-picked; three of its books are missing from the grid.
- Code: code/th_rota/{extract,rank,chain,metrics,refs}.py; data on server C /mnt/l2/l2vast/_rota/{ext,picks}. Metrics table: autopilot/ROTATION_STAGE_A_ROWS.parquet (102,060 rows).
