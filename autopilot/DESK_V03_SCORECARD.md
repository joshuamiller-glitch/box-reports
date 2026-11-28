# DESK_V03_SCORECARD (generated 2026-11-28 04:02Z by code/th_algo/ar_desk.py; research only)

Smoothness-first scorecard (Josh's rules: smoother = worst week not worse AND weekly st.dev. not larger, judged per quarter; ACCEPTABLE = smoother in >= 2/3 of quarters overall AND in NQ-up weeks AND in NQ-down weeks, AND income not more than 10 / 20 / 30% below the bracket) on the months that EXIST for each managed set. Window = the months the managed set has (all DONE rows); the reference is cut to the SAME months and the same weeks (a week belongs to the window when its Monday is in a window month; Nov 2025 excluded as everywhere), so like is compared with like. Reference: alone-bare rows (_A) vs the fixed-bracket live-as-run book alone (TL3_DX_<S>_<MF>_fix_A); in-mix rows (_M) vs the live mix as run (TL3_SR_<S>_...). Income = engine p484 ($4.84/lot). The other families keep the 42-month gate in ALGO_REPORT.md (unchanged).

Window facts: Asia and London sets have 37 months (2023-09..2026-10 without 2025-11), NY AM and NY PM sets 24 months (2024-10..2026-10 without 2025-11); NO-GATE sets 8 months (Asia/London 2024-04..2026-10 subset) or 5 months (NY, from 2024-12): they are shown but are too short to judge. Quarter counts are small (Asia/London up to 13 quarters, NY up to 8): read n of n literally.

## READ FIRST (added by the scorecard agent): completeness, verdict, notes
Completeness checked before scoring: every DK3MAIN / DK3NOSEAT / DK3W _A and _M set has all its months DONE (Asia and London sets 37/37, NY AM and NY PM sets 24/24); nothing half-finished was scored. DK3IDMAIN / DK3MATCH sets are identity / match checks, not scored. Rows labelled "v0.2.2 (comparison)" repeat the earlier DK22 numbers; DK22 has no W variant (those blocks say no rows).
VERDICT per session at the 10 / 20 / 30% income floors (acceptable = smoother in >= 2/3 of quarters overall, in NQ-up and in NQ-down weeks, AND income not more than the floor below the bracket): ASIA FAIL / FAIL / FAIL; NY AM FAIL / FAIL / FAIL; LONDON FAIL / FAIL / FAIL; NY PM FAIL / FAIL / FAIL, for v0.3 main and v0.3 no-seat, per book and per session mix. No DK3MAIN or DK3NOSEAT row clears any floor. The only YES in the page is the REFERENCE row NY AM MF1 DK3W (1.5x stop) at the 30% floor.
Notes: (1) engine exit_name "Target" appears on desk-managed winners-cut-short trades that closed within a few points of entry (e.g. NY MF4: exit +6 pts vs own bracket +30 pts, label Target) after the desk moved the stop (never-bend / DEFEND-half); the label looks like the engine's name for the stop-at-entry fill, not the book target; unverified, W-DYNC to confirm. In the attribution page that bucket is "Target (book exit, not a desk rule)". (2) NY PM in-mix rows for MF2 are identical between DK3MAIN and DK3W: the 1.5x stop made no difference to the live-mix replacement there; unverified. (3) mix rows are post-hoc sums of per-book deltas on the live mix (interaction neglected).

# Asia

## Asia, v0.3, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK3MAIN) | 202309-202610 (37 months) | -51,433 / -50,206 | 16,042 / 20,523 | 10/14, 7/11, 6/12 | -101,818 / -111,441 | 460,151 / 882,294 (-48%) | no / no / no |
| Asia MF2 (DK3MAIN) | 202309-202610 (37 months) | -32,864 / -30,707 | 9,433 / 10,772 | 9/14, 6/11, 7/12 | -112,632 / -92,225 | 210,720 / 409,579 (-49%) | no / no / no |
| Asia MF3 (DK3MAIN) | 202309-202610 (37 months) | -37,207 / -39,659 | 15,138 / 16,561 | 9/14, 6/11, 8/12 | -115,728 / -103,232 | 332,919 / 635,263 (-48%) | no / no / no |

### Asia, v0.3, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK3MAIN) | 202309-202610 (37 months) | -34,672 / -37,409 | 15,409 / 18,895 | 8/14, 7/11, 5/12 | -96,386 / -67,941 | 687,146 / 893,671 (-23%) | no / no / no |
| Asia MF2 in mix (DK3MAIN) | 202309-202610 (37 months) | -40,666 / -37,409 | 17,701 / 18,895 | 6/14, 5/11, 3/12 | -69,002 / -67,941 | 755,466 / 893,671 (-15%) | no / no / no |
| Asia MF3 in mix (DK3MAIN) | 202309-202610 (37 months) | -34,607 / -37,409 | 17,521 / 18,895 | 9/14, 6/11, 7/12 | -79,022 / -67,941 | 744,592 / 893,671 (-17%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -35,127 / -37,409 | 13,100 / 18,895 | 11/14, 9/11, 6/12 | -120,551 / -67,941 | 399,861 / 893,671 (-55%) | no / no / no |

## Asia, v0.3, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK3NOSEAT) | 202309-202610 (37 months) | -56,258 / -50,206 | 16,124 / 20,523 | 10/14, 7/11, 6/12 | -111,541 / -111,441 | 441,571 / 882,294 (-50%) | no / no / no |
| Asia MF2 (DK3NOSEAT) | 202309-202610 (37 months) | -32,864 / -30,707 | 9,479 / 10,772 | 9/14, 7/11, 7/12 | -109,635 / -92,225 | 218,261 / 409,579 (-47%) | no / no / no |
| Asia MF3 (DK3NOSEAT) | 202309-202610 (37 months) | -42,446 / -39,659 | 15,511 / 16,561 | 8/14, 6/11, 7/12 | -117,976 / -103,232 | 308,880 / 635,263 (-51%) | no / no / no |

### Asia, v0.3, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK3NOSEAT) | 202309-202610 (37 months) | -34,672 / -37,409 | 15,464 / 18,895 | 8/14, 7/11, 5/12 | -96,386 / -67,941 | 661,922 / 893,671 (-26%) | no / no / no |
| Asia MF2 in mix (DK3NOSEAT) | 202309-202610 (37 months) | -42,571 / -37,409 | 17,753 / 18,895 | 6/14, 5/11, 3/12 | -69,002 / -67,941 | 757,447 / 893,671 (-15%) | no / no / no |
| Asia MF3 in mix (DK3NOSEAT) | 202309-202610 (37 months) | -41,314 / -37,409 | 17,782 / 18,895 | 9/14, 7/11, 7/12 | -77,429 / -67,941 | 745,282 / 893,671 (-17%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -43,739 / -37,409 | 13,617 / 18,895 | 9/14, 9/11, 5/12 | -129,494 / -67,941 | 377,309 / 893,671 (-58%) | no / no / no |

## Asia, v0.3, REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK3W) | 202309-202610 (37 months) | -61,882 / -50,206 | 16,637 / 20,523 | 11/14, 7/11, 7/12 | -223,172 / -111,441 | 359,941 / 882,294 (-59%) | no / no / no |
| Asia MF2 (DK3W) | 202309-202610 (37 months) | -38,524 / -30,707 | 9,911 / 10,772 | 8/14, 7/11, 5/12 | -121,652 / -92,225 | 248,900 / 409,579 (-39%) | no / no / no |
| Asia MF3 (DK3W) | 202309-202610 (37 months) | -34,342 / -39,659 | 14,458 / 16,561 | 8/14, 5/11, 8/12 | -113,321 / -103,232 | 299,899 / 635,263 (-53%) | no / no / no |

### Asia, v0.3, REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK3W) | 202309-202610 (37 months) | -34,672 / -37,409 | 15,488 / 18,895 | 8/14, 5/11, 5/12 | -109,303 / -67,941 | 618,697 / 893,671 (-31%) | no / no / no |
| Asia MF2 in mix (DK3W) | 202309-202610 (37 months) | -41,416 / -37,409 | 17,548 / 18,895 | 7/14, 5/11, 4/12 | -68,028 / -67,941 | 739,917 / 893,671 (-17%) | no / no / no |
| Asia MF3 in mix (DK3W) | 202309-202610 (37 months) | -38,053 / -37,409 | 18,120 / 18,895 | 7/14, 4/11, 5/12 | -103,998 / -67,941 | 660,050 / 893,671 (-26%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -65,670 / -37,409 | 15,386 / 18,895 | 11/14, 7/11, 6/12 | -151,707 / -67,941 | 231,322 / 893,671 (-74%) | no / no / no |

## Asia, v0.2.2 (comparison), main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK22MAIN) | 202309-202610 (37 months) | -31,530 / -50,206 | 8,689 / 20,523 | 11/14, 8/11, 7/12 | -222,803 / -111,441 | -198,618 / 882,294 (-123%) | no / no / no |
| Asia MF2 (DK22MAIN) | 202309-202610 (37 months) | -26,783 / -30,707 | 5,950 / 10,772 | 9/14, 7/11, 6/12 | -93,385 / -92,225 | 74,687 / 409,579 (-82%) | no / no / no |
| Asia MF3 (DK22MAIN) | 202309-202610 (37 months) | -41,929 / -39,659 | 11,983 / 16,561 | 10/14, 7/11, 10/12 | -239,545 / -103,232 | -89,438 / 635,263 (-114%) | no / no / no |

### Asia, v0.2.2 (comparison), main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK22MAIN) | 202309-202610 (37 months) | -32,781 / -37,409 | 12,434 / 18,895 | 9/14, 7/11, 7/12 | -121,924 / -67,941 | 315,003 / 893,671 (-65%) | no / no / no |
| Asia MF2 in mix (DK22MAIN) | 202309-202610 (37 months) | -44,065 / -37,409 | 17,251 / 18,895 | 9/14, 7/11, 6/12 | -77,919 / -67,941 | 682,685 / 893,671 (-24%) | no / no / no |
| Asia MF3 in mix (DK22MAIN) | 202309-202610 (37 months) | -41,738 / -37,409 | 17,033 / 18,895 | 8/14, 6/11, 6/12 | -94,491 / -67,941 | 556,048 / 893,671 (-38%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -44,293 / -37,409 | 10,045 / 18,895 | 11/14, 8/11, 6/12 | -308,325 / -67,941 | -233,607 / 893,671 (-126%) | no / no / no |

## Asia, v0.2.2 (comparison), no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK22NOSEAT) | 202309-202610 (37 months) | -31,530 / -50,206 | 8,470 / 20,523 | 11/14, 9/11, 7/12 | -214,184 / -111,441 | -189,999 / 882,294 (-122%) | no / no / no |
| Asia MF2 (DK22NOSEAT) | 202309-202610 (37 months) | -26,783 / -30,707 | 5,994 / 10,772 | 9/14, 7/11, 6/12 | -93,385 / -92,225 | 79,813 / 409,579 (-81%) | no / no / no |
| Asia MF3 (DK22NOSEAT) | 202309-202610 (37 months) | -41,929 / -39,659 | 12,408 / 16,561 | 8/14, 6/11, 10/12 | -267,289 / -103,232 | -130,856 / 635,263 (-121%) | no / no / no |

### Asia, v0.2.2 (comparison), no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -32,510 / -37,409 | 12,380 / 18,895 | 9/14, 8/11, 7/12 | -121,408 / -67,941 | 321,311 / 893,671 (-64%) | no / no / no |
| Asia MF2 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -44,065 / -37,409 | 17,278 / 18,895 | 8/14, 6/11, 6/12 | -77,919 / -67,941 | 680,817 / 893,671 (-24%) | no / no / no |
| Asia MF3 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -41,738 / -37,409 | 17,059 / 18,895 | 6/14, 5/11, 5/12 | -95,510 / -67,941 | 556,135 / 893,671 (-38%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -44,293 / -37,409 | 10,081 / 18,895 | 10/14, 7/11, 6/12 | -306,290 / -67,941 | -229,080 / 893,671 (-126%) | no / no / no |

## Asia, v0.2.2 (comparison), REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 | no rows |||||||
| Asia MF2 | no rows |||||||
| Asia MF3 | no rows |||||||

### Asia, v0.2.2 (comparison), REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|

## Asia: same trade two ways (alone-bare managed vs the same signal on the book's own fixed bracket; a change counts when the managed R differs by >= 0.25 R of the book's own stop; $ = p484, managed minus own bracket)

| book / set | window | matched pairs | give-backs prevented n ($) | winners cut short n ($) | losers cut early n ($) | losers made worse n ($) | all matched pairs net $ (managed minus own bracket) | extra trades from freed slots n ($) | bracket-only trades (blocked) n ($) |
|---|---|---|---|---|---|---|---|---|---|
| Asia MF1 DK3MAIN | 202309-202610 (37 months) | 1001 | 81 (+214470) | 98 (-483655) | 156 (+385000) | 1 (-1480) | -48135 | 26 (+44400) | 990 (+384190) |
| Asia MF2 DK3MAIN | 202309-202610 (37 months) | 473 | 22 (+89600) | 54 (-278130) | 58 (+212830) | 1 (-2550) | -66495 | 10 (-13425) | 141 (+130115) |
| Asia MF3 DK3MAIN | 202309-202610 (37 months) | 2125 | 93 (+288700) | 244 (-1060535) | 257 (+681315) | 4 (-8955) | -295490 | 160 (+2644) | 207 (+1604) |
| **Asia all books DK3MAIN** | 202309-202610 (37 months) | 3599 | 196 (+592770) | 396 (-1822320) | 471 (+1279145) | 6 (-12985) | -410120 | 196 (+33618) | 1338 (+515909) |
| Asia MF1 DK3NOSEAT | 202309-202610 (37 months) | 1012 | 82 (+216065) | 98 (-483655) | 157 (+386595) | 1 (-1480) | -44140 | 42 (+22000) | 979 (+384365) |
| Asia MF2 DK3NOSEAT | 202309-202610 (37 months) | 475 | 22 (+89600) | 54 (-278130) | 58 (+212830) | 1 (-2550) | -65950 | 14 (-13227) | 139 (+123318) |
| Asia MF3 DK3NOSEAT | 202309-202610 (37 months) | 2159 | 95 (+292730) | 249 (-1087005) | 260 (+688770) | 4 (-8955) | -311830 | 221 (-26913) | 173 (-20254) |
| **Asia all books DK3NOSEAT** | 202309-202610 (37 months) | 3646 | 199 (+598395) | 401 (-1848790) | 475 (+1288195) | 6 (-12985) | -421920 | 277 (-18139) | 1291 (+487429) |
| Asia MF1 DK3W | 202309-202610 (37 months) | 884 | 84 (+338520) | 90 (-426420) | 167 (+682325) | 133 (-289245) | -55725 | 42 (+60675) | 1107 (+500633) |
| Asia MF2 DK3W | 202309-202610 (37 months) | 463 | 29 (+161730) | 52 (-268095) | 74 (+382925) | 26 (-82905) | -7965 | 10 (-14895) | 151 (+150225) |
| Asia MF3 DK3W | 202309-202610 (37 months) | 1772 | 95 (+427650) | 213 (-941245) | 267 (+1147345) | 221 (-534360) | -372200 | 198 (-12810) | 560 (-39207) |
| **Asia all books DK3W** | 202309-202610 (37 months) | 3119 | 208 (+927900) | 355 (-1635760) | 508 (+2212595) | 380 (-906510) | -435890 | 250 (+32970) | 1818 (+611650) |

NOTE on the counts: own-bracket peak (for give-backs prevented) is read from the 1-s NQ tape (the fix_A rows store no best price); R = points / the book's median stop distance on fix_A. The matched pairs sum is the same-signal difference only; extra trades from freed slots and blocked bracket-only trades are the entries only one side took.

# NY AM

## NY AM, v0.3, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK3MAIN) | 202410-202610 (24 months) | -64,062 / -81,412 | 28,463 / 38,170 | 5/9, 5/7, 3/7 | -136,263 / -158,282 | 758,672 / 1,261,834 (-40%) | no / no / no |
| NY AM MF2 (DK3MAIN) | 202410-202610 (24 months) | -49,914 / -59,825 | 21,275 / 23,724 | 4/9, 3/7, 3/7 | -252,359 / -263,422 | 6,153 / 169,966 (-96%) | no / no / no |
| NY AM MF4 (DK3MAIN) | 202410-202610 (24 months) | -62,974 / -73,124 | 24,182 / 28,083 | 5/9, 2/7, 6/7 | -202,867 / -199,315 | 204,524 / 432,840 (-53%) | no / no / no |
| NY AM MF5 (DK3MAIN) | 202410-202610 (24 months) | -34,616 / -50,861 | 11,744 / 13,987 | 7/9, 3/7, 4/7 | -91,139 / -103,673 | 166,326 / 256,213 (-35%) | no / no / no |

### NY AM, v0.3, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK3MAIN) | 202410-202610 (24 months) | -96,373 / -110,130 | 49,300 / 54,746 | 5/9, 3/7, 3/7 | -174,226 / -163,622 | 2,505,510 / 2,847,328 (-12%) | no / no / no |
| NY AM MF2 in mix (DK3MAIN) | 202410-202610 (24 months) | -114,675 / -110,130 | 53,466 / 54,746 | 4/9, 3/7, 1/7 | -164,082 / -163,622 | 2,744,097 / 2,847,328 (-4%) | no / no / no |
| NY AM MF4 in mix (DK3MAIN) | 202410-202610 (24 months) | -99,212 / -110,130 | 52,315 / 54,746 | 5/9, 3/7, 5/7 | -177,299 / -163,622 | 2,675,949 / 2,847,328 (-6%) | no / no / no |
| NY AM MF5 in mix (DK3MAIN) | 202410-202610 (24 months) | -109,880 / -110,130 | 54,002 / 54,746 | 4/9, 3/7, 4/7 | -146,896 / -163,622 | 2,793,500 / 2,847,328 (-2%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -88,687 / -110,130 | 44,961 / 54,746 | 6/9, 2/7, 5/7 | -166,714 / -163,622 | 2,177,072 / 2,847,328 (-24%) | no / no / no |

## NY AM, v0.3, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK3NOSEAT) | 202410-202610 (24 months) | -64,062 / -81,412 | 28,326 / 38,170 | 5/9, 5/7, 3/7 | -136,263 / -158,282 | 731,142 / 1,261,834 (-42%) | no / no / no |
| NY AM MF2 (DK3NOSEAT) | 202410-202610 (24 months) | -49,914 / -59,825 | 21,318 / 23,724 | 4/9, 3/7, 3/7 | -256,172 / -263,422 | 2,340 / 169,966 (-99%) | no / no / no |
| NY AM MF4 (DK3NOSEAT) | 202410-202610 (24 months) | -62,974 / -73,124 | 24,139 / 28,083 | 5/9, 2/7, 6/7 | -221,161 / -199,315 | 155,526 / 432,840 (-64%) | no / no / no |
| NY AM MF5 (DK3NOSEAT) | 202410-202610 (24 months) | -34,616 / -50,861 | 11,951 / 13,987 | 6/9, 2/7, 4/7 | -98,786 / -103,673 | 165,016 / 256,213 (-36%) | no / no / no |

### NY AM, v0.3, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK3NOSEAT) | 202410-202610 (24 months) | -96,373 / -110,130 | 49,196 / 54,746 | 5/9, 3/7, 3/7 | -174,226 / -163,622 | 2,511,077 / 2,847,328 (-12%) | no / no / no |
| NY AM MF2 in mix (DK3NOSEAT) | 202410-202610 (24 months) | -114,675 / -110,130 | 53,480 / 54,746 | 4/9, 3/7, 1/7 | -164,082 / -163,622 | 2,742,718 / 2,847,328 (-4%) | no / no / no |
| NY AM MF4 in mix (DK3NOSEAT) | 202410-202610 (24 months) | -99,212 / -110,130 | 52,135 / 54,746 | 5/9, 3/7, 6/7 | -177,299 / -163,622 | 2,650,997 / 2,847,328 (-7%) | no / no / no |
| NY AM MF5 in mix (DK3NOSEAT) | 202410-202610 (24 months) | -109,880 / -110,130 | 54,155 / 54,746 | 4/9, 3/7, 4/7 | -146,936 / -163,622 | 2,794,538 / 2,847,328 (-2%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -88,687 / -110,130 | 44,838 / 54,746 | 6/9, 2/7, 5/7 | -166,714 / -163,622 | 2,157,347 / 2,847,328 (-24%) | no / no / no |

## NY AM, v0.3, REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK3W) | 202410-202610 (24 months) | -94,291 / -81,412 | 28,753 / 38,170 | 6/9, 5/7, 5/7 | -112,112 / -158,282 | 907,228 / 1,261,834 (-28%) | no (smooth) / no (smooth) / YES |
| NY AM MF2 (DK3W) | 202410-202610 (24 months) | -41,645 / -59,825 | 21,121 / 23,724 | 5/9, 5/7, 2/7 | -161,846 / -263,422 | 103,702 / 169,966 (-39%) | no / no / no |
| NY AM MF4 (DK3W) | 202410-202610 (24 months) | -77,916 / -73,124 | 25,747 / 28,083 | 5/9, 2/7, 6/7 | -114,578 / -199,315 | 392,275 / 432,840 (-9%) | no / no / no |
| NY AM MF5 (DK3W) | 202410-202610 (24 months) | -25,303 / -50,861 | 10,791 / 13,987 | 6/9, 4/7, 3/7 | -79,721 / -103,673 | 197,894 / 256,213 (-23%) | no / no / no |

### NY AM, v0.3, REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK3W) | 202410-202610 (24 months) | -111,720 / -110,130 | 47,716 / 54,746 | 5/9, 3/7, 4/7 | -153,376 / -163,622 | 2,611,295 / 2,847,328 (-8%) | no / no / no |
| NY AM MF2 in mix (DK3W) | 202410-202610 (24 months) | -115,456 / -110,130 | 55,000 / 54,746 | 2/9, 4/7, 1/7 | -182,052 / -163,622 | 2,764,957 / 2,847,328 (-3%) | no / no / no |
| NY AM MF4 in mix (DK3W) | 202410-202610 (24 months) | -113,482 / -110,130 | 51,702 / 54,746 | 6/9, 4/7, 5/7 | -168,960 / -163,622 | 2,571,472 / 2,847,328 (-10%) | no / no / no |
| NY AM MF5 in mix (DK3W) | 202410-202610 (24 months) | -104,890 / -110,130 | 53,932 / 54,746 | 4/9, 5/7, 4/7 | -138,354 / -163,622 | 2,841,656 / 2,847,328 (-0%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -88,421 / -110,130 | 44,095 / 54,746 | 4/9, 4/7, 5/7 | -143,019 / -163,622 | 2,247,397 / 2,847,328 (-21%) | no / no / no |

## NY AM, v0.2.2 (comparison), main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK22MAIN) | 202410-202610 (24 months) | -46,763 / -81,412 | 26,565 / 38,170 | 7/9, 5/7, 5/7 | -113,982 / -158,282 | 622,071 / 1,261,834 (-51%) | no (smooth) / no (smooth) / no (smooth) |
| NY AM MF2 (DK22MAIN) | 202410-202610 (24 months) | -60,375 / -59,825 | 17,091 / 23,724 | 6/9, 5/7, 5/7 | -177,004 / -263,422 | 6,145 / 169,966 (-96%) | no (smooth) / no (smooth) / no (smooth) |
| NY AM MF4 (DK22MAIN) | 202410-202610 (24 months) | -89,332 / -73,124 | 24,565 / 28,083 | 5/9, 4/7, 4/7 | -145,799 / -199,315 | 242,885 / 432,840 (-44%) | no / no / no |
| NY AM MF5 (DK22MAIN) | 202410-202610 (24 months) | -21,271 / -50,861 | 8,705 / 13,987 | 6/9, 3/7, 4/7 | -84,752 / -103,673 | 45,191 / 256,213 (-82%) | no / no / no |

### NY AM, v0.2.2 (comparison), main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK22MAIN) | 202410-202610 (24 months) | -109,804 / -110,130 | 47,104 / 54,746 | 5/9, 2/7, 4/7 | -170,928 / -163,622 | 2,304,631 / 2,847,328 (-19%) | no / no / no |
| NY AM MF2 in mix (DK22MAIN) | 202410-202610 (24 months) | -95,946 / -110,130 | 51,059 / 54,746 | 6/9, 5/7, 3/7 | -199,594 / -163,622 | 2,617,074 / 2,847,328 (-8%) | no / no / no |
| NY AM MF4 in mix (DK22MAIN) | 202410-202610 (24 months) | -79,171 / -110,130 | 49,028 / 54,746 | 7/9, 4/7, 4/7 | -182,966 / -163,622 | 2,544,423 / 2,847,328 (-11%) | no / no / no |
| NY AM MF5 in mix (DK22MAIN) | 202410-202610 (24 months) | -97,560 / -110,130 | 52,813 / 54,746 | 4/9, 4/7, 4/7 | -166,985 / -163,622 | 2,759,157 / 2,847,328 (-3%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -64,328 / -110,130 | 37,994 / 54,746 | 4/9, 3/7, 4/7 | -130,615 / -163,622 | 1,683,301 / 2,847,328 (-41%) | no / no / no |

## NY AM, v0.2.2 (comparison), no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK22NOSEAT) | 202410-202610 (24 months) | -55,737 / -81,412 | 27,049 / 38,170 | 6/9, 4/7, 5/7 | -141,429 / -158,282 | 595,841 / 1,261,834 (-53%) | no / no / no |
| NY AM MF2 (DK22NOSEAT) | 202410-202610 (24 months) | -60,375 / -59,825 | 17,151 / 23,724 | 6/9, 5/7, 5/7 | -187,881 / -263,422 | 197 / 169,966 (-100%) | no (smooth) / no (smooth) / no (smooth) |
| NY AM MF4 (DK22NOSEAT) | 202410-202610 (24 months) | -89,332 / -73,124 | 24,624 / 28,083 | 5/9, 4/7, 4/7 | -152,121 / -199,315 | 194,107 / 432,840 (-55%) | no / no / no |
| NY AM MF5 (DK22NOSEAT) | 202410-202610 (24 months) | -23,433 / -50,861 | 8,995 / 13,987 | 6/9, 3/7, 4/7 | -91,465 / -103,673 | 28,710 / 256,213 (-89%) | no / no / no |

### NY AM, v0.2.2 (comparison), no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -109,804 / -110,130 | 46,934 / 54,746 | 5/9, 2/7, 4/7 | -170,928 / -163,622 | 2,304,996 / 2,847,328 (-19%) | no / no / no |
| NY AM MF2 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -95,946 / -110,130 | 51,125 / 54,746 | 6/9, 5/7, 3/7 | -199,594 / -163,622 | 2,616,508 / 2,847,328 (-8%) | no / no / no |
| NY AM MF4 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -79,171 / -110,130 | 48,790 / 54,746 | 7/9, 4/7, 4/7 | -182,966 / -163,622 | 2,528,588 / 2,847,328 (-11%) | no / no / no |
| NY AM MF5 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -97,560 / -110,130 | 52,633 / 54,746 | 4/9, 4/7, 4/7 | -166,985 / -163,622 | 2,746,132 / 2,847,328 (-4%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -64,328 / -110,130 | 37,931 / 54,746 | 4/9, 3/7, 4/7 | -129,429 / -163,622 | 1,654,241 / 2,847,328 (-42%) | no / no / no |

## NY AM, v0.2.2 (comparison), REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 | no rows |||||||
| NY AM MF2 | no rows |||||||
| NY AM MF4 | no rows |||||||
| NY AM MF5 | no rows |||||||

### NY AM, v0.2.2 (comparison), REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|

## NY AM: same trade two ways (alone-bare managed vs the same signal on the book's own fixed bracket; a change counts when the managed R differs by >= 0.25 R of the book's own stop; $ = p484, managed minus own bracket)

| book / set | window | matched pairs | give-backs prevented n ($) | winners cut short n ($) | losers cut early n ($) | losers made worse n ($) | all matched pairs net $ (managed minus own bracket) | extra trades from freed slots n ($) | bracket-only trades (blocked) n ($) |
|---|---|---|---|---|---|---|---|---|---|
| NY AM MF1 DK3MAIN | 202410-202610 (24 months) | 861 | 68 (+506700) | 181 (-1653445) | 186 (+1261440) | 1 (-4280) | -308745 | 96 (-93853) | 230 (+91796) |
| NY AM MF2 DK3MAIN | 202410-202610 (24 months) | 1321 | 77 (+251775) | 178 (-868280) | 191 (+608615) | 0 (+0) | -142515 | 49 (-48423) | 93 (-34306) |
| NY AM MF4 DK3MAIN | 202410-202610 (24 months) | 2266 | 0 (+0) | 185 (-785495) | 146 (+680235) | 0 (+0) | -142065 | 161 (-51670) | 110 (+28146) |
| NY AM MF5 DK3MAIN | 202410-202610 (24 months) | 1700 | 106 (+207755) | 224 (-652505) | 271 (+494435) | 0 (+0) | -131905 | 39 (+29704) | 205 (-5037) |
| **NY AM all books DK3MAIN** | 202410-202610 (24 months) | 6148 | 251 (+966230) | 768 (-3959725) | 794 (+3044725) | 1 (-4280) | -725230 | 345 (-164243) | 638 (+80599) |
| NY AM MF1 DK3NOSEAT | 202410-202610 (24 months) | 862 | 68 (+506700) | 181 (-1653445) | 186 (+1261440) | 1 (-4280) | -306065 | 110 (-121309) | 229 (+94550) |
| NY AM MF2 DK3NOSEAT | 202410-202610 (24 months) | 1321 | 77 (+251775) | 178 (-868280) | 191 (+608615) | 0 (+0) | -142515 | 51 (-52236) | 93 (-34306) |
| NY AM MF4 DK3NOSEAT | 202410-202610 (24 months) | 2277 | 0 (+0) | 187 (-796100) | 149 (+691675) | 0 (+0) | -136430 | 173 (-76399) | 99 (+58050) |
| NY AM MF5 DK3NOSEAT | 202410-202610 (24 months) | 1714 | 109 (+215100) | 224 (-652505) | 274 (+503615) | 0 (+0) | -122130 | 45 (+28912) | 191 (+5257) |
| **NY AM all books DK3NOSEAT** | 202410-202610 (24 months) | 6174 | 254 (+973575) | 770 (-3970330) | 800 (+3065345) | 1 (-4280) | -707140 | 379 (-221033) | 612 (+123551) |
| NY AM MF1 DK3W | 202410-202610 (24 months) | 752 | 57 (+558990) | 162 (-1476885) | 151 (+1392875) | 19 (-105595) | -211780 | 127 (-67433) | 339 (+104125) |
| NY AM MF2 DK3W | 202410-202610 (24 months) | 976 | 60 (+399075) | 130 (-631620) | 162 (+1066485) | 140 (-456675) | -11730 | 115 (-86830) | 438 (-34365) |
| NY AM MF4 DK3W | 202410-202610 (24 months) | 1878 | 1 (+14055) | 159 (-680045) | 147 (+1181585) | 81 (-372165) | -123745 | 189 (+10176) | 498 (-74822) |
| NY AM MF5 DK3W | 202410-202610 (24 months) | 1410 | 97 (+292795) | 184 (-536815) | 275 (+830895) | 201 (-333100) | -44285 | 90 (+26433) | 495 (+58013) |
| **NY AM all books DK3W** | 202410-202610 (24 months) | 5016 | 215 (+1264915) | 635 (-3325365) | 735 (+4471840) | 441 (-1267535) | -391540 | 521 (-117653) | 1770 (+52952) |

NOTE on the counts: own-bracket peak (for give-backs prevented) is read from the 1-s NQ tape (the fix_A rows store no best price); R = points / the book's median stop distance on fix_A. The matched pairs sum is the same-signal difference only; extra trades from freed slots and blocked bracket-only trades are the entries only one side took.

# London

## London, v0.3, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK3MAIN) | 202309-202610 (37 months) | -36,382 / -52,798 | 11,948 / 16,123 | 9/14, 7/11, 7/12 | -156,679 / -107,192 | 222,264 / 510,693 (-56%) | no / no / no |
| London MF3 (DK3MAIN) | 202309-202610 (37 months) | -16,070 / -23,120 | 5,809 / 6,993 | 7/14, 4/11, 4/12 | -47,513 / -47,177 | 41,819 / 185,303 (-77%) | no / no / no |

### London, v0.3, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK3MAIN) | 202309-202610 (37 months) | -85,401 / -107,350 | 20,795 / 23,472 | 7/14, 4/11, 5/12 | -251,200 / -224,333 | 592,627 / 881,056 (-33%) | no / no / no |
| London MF3 in mix (DK3MAIN) | 202309-202610 (37 months) | -89,433 / -107,350 | 22,262 / 23,472 | 10/14, 4/11, 5/12 | -227,425 / -224,333 | 737,571 / 881,056 (-16%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -67,484 / -107,350 | 19,410 / 23,472 | 6/14, 2/11, 4/12 | -274,932 / -224,333 | 449,142 / 881,056 (-49%) | no / no / no |

## London, v0.3, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK3NOSEAT) | 202309-202610 (37 months) | -36,382 / -52,798 | 12,378 / 16,123 | 9/14, 7/11, 7/12 | -170,008 / -107,192 | 228,670 / 510,693 (-55%) | no / no / no |
| London MF3 (DK3NOSEAT) | 202309-202610 (37 months) | -17,211 / -23,120 | 6,507 / 6,993 | 7/14, 4/11, 3/12 | -118,154 / -47,177 | -31,590 / 185,303 (-117%) | no / no / no |

### London, v0.3, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK3NOSEAT) | 202309-202610 (37 months) | -91,665 / -107,350 | 20,833 / 23,472 | 8/14, 4/11, 5/12 | -263,742 / -224,333 | 599,033 / 881,056 (-32%) | no / no / no |
| London MF3 in mix (DK3NOSEAT) | 202309-202610 (37 months) | -104,369 / -107,350 | 23,255 / 23,472 | 5/14, 1/11, 2/12 | -299,843 / -224,333 | 664,163 / 881,056 (-25%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -88,683 / -107,350 | 20,432 / 23,472 | 7/14, 4/11, 4/12 | -359,892 / -224,333 | 382,140 / 881,056 (-57%) | no / no / no |

## London, v0.3, REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK3W) | 202309-202610 (37 months) | -34,824 / -52,798 | 12,830 / 16,123 | 8/14, 6/11, 7/12 | -191,839 / -107,192 | 264,687 / 510,693 (-48%) | no / no / no |
| London MF3 (DK3W) | 202309-202610 (37 months) | -15,837 / -23,120 | 5,910 / 6,993 | 7/14, 4/11, 5/12 | -94,214 / -47,177 | -8,451 / 185,303 (-105%) | no / no / no |

### London, v0.3, REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK3W) | 202309-202610 (37 months) | -97,304 / -107,350 | 21,599 / 23,472 | 6/14, 4/11, 5/12 | -276,643 / -224,333 | 635,050 / 881,056 (-28%) | no / no / no |
| London MF3 in mix (DK3W) | 202309-202610 (37 months) | -89,433 / -107,350 | 22,143 / 23,472 | 8/14, 3/11, 5/12 | -243,794 / -224,333 | 687,302 / 881,056 (-22%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -79,387 / -107,350 | 20,199 / 23,472 | 6/14, 4/11, 4/12 | -316,744 / -224,333 | 441,296 / 881,056 (-50%) | no / no / no |

## London, v0.2.2 (comparison), main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK22MAIN) | 202309-202610 (37 months) | -40,155 / -52,798 | 12,176 / 16,123 | 9/14, 7/11, 7/12 | -213,104 / -107,192 | 198,554 / 510,693 (-61%) | no / no / no |
| London MF3 (DK22MAIN) | 202309-202610 (37 months) | -13,866 / -23,120 | 4,755 / 6,993 | 8/14, 6/11, 7/12 | -153,491 / -47,177 | -98,813 / 185,303 (-153%) | no / no / no |

### London, v0.2.2 (comparison), main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK22MAIN) | 202309-202610 (37 months) | -103,259 / -107,350 | 21,137 / 23,472 | 7/14, 4/11, 6/12 | -296,935 / -224,333 | 568,916 / 881,056 (-35%) | no / no / no |
| London MF3 in mix (DK22MAIN) | 202309-202610 (37 months) | -86,881 / -107,350 | 22,251 / 23,472 | 5/14, 2/11, 4/12 | -247,830 / -224,333 | 596,940 / 881,056 (-32%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -82,790 / -107,350 | 19,661 / 23,472 | 6/14, 5/11, 4/12 | -336,126 / -224,333 | 284,800 / 881,056 (-68%) | no / no / no |

## London, v0.2.2 (comparison), no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK22NOSEAT) | 202309-202610 (37 months) | -45,113 / -52,798 | 12,786 / 16,123 | 7/14, 6/11, 7/12 | -220,553 / -107,192 | 198,246 / 510,693 (-61%) | no / no / no |
| London MF3 (DK22NOSEAT) | 202309-202610 (37 months) | -20,967 / -23,120 | 5,939 / 6,993 | 5/14, 3/11, 5/12 | -295,248 / -47,177 | -241,126 / 185,303 (-230%) | no / no / no |

### London, v0.2.2 (comparison), no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -101,617 / -107,350 | 21,095 / 23,472 | 5/14, 2/11, 6/12 | -301,562 / -224,333 | 568,608 / 881,056 (-35%) | no / no / no |
| London MF3 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -94,716 / -107,350 | 23,169 / 23,472 | 2/14, 1/11, 3/12 | -306,790 / -224,333 | 454,626 / 881,056 (-48%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -88,983 / -107,350 | 20,640 / 23,472 | 6/14, 4/11, 5/12 | -427,600 / -224,333 | 142,179 / 881,056 (-84%) | no / no / no |

## London, v0.2.2 (comparison), REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 | no rows |||||||
| London MF3 | no rows |||||||

### London, v0.2.2 (comparison), REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|

## London: same trade two ways (alone-bare managed vs the same signal on the book's own fixed bracket; a change counts when the managed R differs by >= 0.25 R of the book's own stop; $ = p484, managed minus own bracket)

| book / set | window | matched pairs | give-backs prevented n ($) | winners cut short n ($) | losers cut early n ($) | losers made worse n ($) | all matched pairs net $ (managed minus own bracket) | extra trades from freed slots n ($) | bracket-only trades (blocked) n ($) |
|---|---|---|---|---|---|---|---|---|---|
| London MF1 DK3MAIN | 202309-202610 (37 months) | 996 | 0 (+0) | 170 (-1005955) | 128 (+918185) | 1 (-3605) | -223155 | 112 (-71442) | 35 (+35795) |
| London MF3 DK3MAIN | 202309-202610 (37 months) | 1396 | 3 (+10125) | 311 (-726920) | 248 (+653470) | 1 (-1555) | -126655 | 1260 (-40402) | 335 (-26273) |
| **London all books DK3MAIN** | 202309-202610 (37 months) | 2392 | 3 (+10125) | 481 (-1732875) | 376 (+1571655) | 2 (-5160) | -349810 | 1372 (-111843) | 370 (+9522) |
| London MF1 DK3NOSEAT | 202309-202610 (37 months) | 1021 | 0 (+0) | 174 (-1027640) | 130 (+935825) | 2 (-7305) | -226795 | 162 (-70753) | 10 (+16778) |
| London MF3 DK3NOSEAT | 202309-202610 (37 months) | 1587 | 3 (+10125) | 343 (-804965) | 283 (+728285) | 1 (-1555) | -128075 | 2629 (-104839) | 144 (-14249) |
| **London all books DK3NOSEAT** | 202309-202610 (37 months) | 2608 | 3 (+10125) | 517 (-1832605) | 413 (+1664110) | 3 (-8860) | -354870 | 2791 (-175591) | 154 (+2529) |
| London MF1 DK3W | 202309-202610 (37 months) | 972 | 0 (+0) | 164 (-973835) | 121 (+978615) | 6 (-35545) | -172660 | 111 (-89493) | 59 (+25816) |
| London MF3 DK3W | 202309-202610 (37 months) | 1289 | 2 (+5475) | 293 (-688550) | 224 (+619200) | 4 (-6525) | -139905 | 1209 (-70628) | 442 (-17034) |
| **London all books DK3W** | 202309-202610 (37 months) | 2261 | 2 (+5475) | 457 (-1662385) | 345 (+1597815) | 10 (-42070) | -312565 | 1320 (-160121) | 501 (+8782) |

NOTE on the counts: own-bracket peak (for give-backs prevented) is read from the 1-s NQ tape (the fix_A rows store no best price); R = points / the book's median stop distance on fix_A. The matched pairs sum is the same-signal difference only; extra trades from freed slots and blocked bracket-only trades are the entries only one side took.

# NY PM

## NY PM, v0.3, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK3MAIN) | 202410-202610 (24 months) | -29,665 / -41,926 | 12,631 / 18,229 | 7/9, 6/7, 5/7 | -86,179 / -165,629 | 70,585 / 235,203 (-70%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DK3MAIN) | 202410-202610 (24 months) | -29,739 / -28,888 | 10,095 / 14,432 | 6/9, 4/7, 3/7 | -70,389 / -75,125 | 221,462 / 415,930 (-47%) | no / no / no |

### NY PM, v0.3, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK3MAIN) | 202410-202610 (24 months) | -41,804 / -44,139 | 18,747 / 20,021 | 7/9, 5/7, 4/7 | -146,669 / -134,363 | 511,147 / 658,056 (-22%) | no / no / no |
| NY PM MF3 in mix (DK3MAIN) | 202410-202610 (24 months) | -43,871 / -44,139 | 19,365 / 20,021 | 3/9, 4/7, 2/7 | -92,816 / -134,363 | 568,933 / 658,056 (-14%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -35,926 / -44,139 | 18,062 / 20,021 | 6/9, 5/7, 2/7 | -112,257 / -134,363 | 422,023 / 658,056 (-36%) | no / no / no |

## NY PM, v0.3, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK3NOSEAT) | 202410-202610 (24 months) | -29,665 / -41,926 | 12,781 / 18,229 | 7/9, 6/7, 4/7 | -110,091 / -165,629 | 61,295 / 235,203 (-74%) | no / no / no |
| NY PM MF3 (DK3NOSEAT) | 202410-202610 (24 months) | -29,739 / -28,888 | 10,177 / 14,432 | 6/9, 4/7, 3/7 | -58,861 / -75,125 | 206,099 / 415,930 (-50%) | no / no / no |

### NY PM, v0.3, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK3NOSEAT) | 202410-202610 (24 months) | -41,804 / -44,139 | 18,695 / 20,021 | 7/9, 5/7, 3/7 | -143,232 / -134,363 | 490,832 / 658,056 (-25%) | no / no / no |
| NY PM MF3 in mix (DK3NOSEAT) | 202410-202610 (24 months) | -43,871 / -44,139 | 19,389 / 20,021 | 3/9, 4/7, 2/7 | -95,003 / -134,363 | 567,985 / 658,056 (-14%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -35,926 / -44,139 | 17,989 / 20,021 | 6/9, 5/7, 2/7 | -111,008 / -134,363 | 400,761 / 658,056 (-39%) | no / no / no |

## NY PM, v0.3, REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK3W) | 202410-202610 (24 months) | -41,888 / -41,926 | 12,534 / 18,229 | 6/9, 5/7, 6/7 | -108,918 / -165,629 | 18,798 / 235,203 (-92%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DK3W) | 202410-202610 (24 months) | -20,250 / -28,888 | 10,000 / 14,432 | 7/9, 5/7, 3/7 | -52,300 / -75,125 | 202,062 / 415,930 (-51%) | no / no / no |

### NY PM, v0.3, REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK3W) | 202410-202610 (24 months) | -41,804 / -44,139 | 18,747 / 20,021 | 7/9, 5/7, 4/7 | -146,669 / -134,363 | 511,147 / 658,056 (-22%) | no / no / no |
| NY PM MF3 in mix (DK3W) | 202410-202610 (24 months) | -43,871 / -44,139 | 19,350 / 20,021 | 3/9, 4/7, 1/7 | -93,048 / -134,363 | 567,586 / 658,056 (-14%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -35,926 / -44,139 | 18,054 / 20,021 | 6/9, 5/7, 2/7 | -112,670 / -134,363 | 420,676 / 658,056 (-36%) | no / no / no |

## NY PM, v0.2.2 (comparison), main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK22MAIN) | 202410-202610 (24 months) | -23,729 / -41,926 | 8,485 / 18,229 | 8/9, 7/7, 6/7 | -113,521 / -165,629 | -36,355 / 235,203 (-115%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DK22MAIN) | 202410-202610 (24 months) | -28,499 / -28,888 | 8,526 / 14,432 | 6/9, 4/7, 3/7 | -106,151 / -75,125 | 52,793 / 415,930 (-87%) | no / no / no |

### NY PM, v0.2.2 (comparison), main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK22MAIN) | 202410-202610 (24 months) | -34,555 / -44,139 | 17,173 / 20,021 | 5/9, 5/7, 3/7 | -132,429 / -134,363 | 320,101 / 658,056 (-51%) | no / no / no |
| NY PM MF3 in mix (DK22MAIN) | 202410-202610 (24 months) | -46,607 / -44,139 | 19,734 / 20,021 | 2/9, 2/7, 1/7 | -100,659 / -134,363 | 496,391 / 658,056 (-25%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -42,993 / -44,139 | 16,414 / 20,021 | 6/9, 6/7, 1/7 | -110,164 / -134,363 | 158,436 / 658,056 (-76%) | no / no / no |

## NY PM, v0.2.2 (comparison), no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK22NOSEAT) | 202410-202610 (24 months) | -19,741 / -41,926 | 8,578 / 18,229 | 8/9, 7/7, 6/7 | -119,609 / -165,629 | -35,686 / 235,203 (-115%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DK22NOSEAT) | 202410-202610 (24 months) | -28,499 / -28,888 | 8,452 / 14,432 | 6/9, 3/7, 3/7 | -102,650 / -75,125 | 48,330 / 415,930 (-88%) | no / no / no |

### NY PM, v0.2.2 (comparison), no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -34,555 / -44,139 | 17,234 / 20,021 | 5/9, 5/7, 3/7 | -129,200 / -134,363 | 313,845 / 658,056 (-52%) | no / no / no |
| NY PM MF3 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -46,607 / -44,139 | 19,773 / 20,021 | 2/9, 2/7, 1/7 | -102,142 / -134,363 | 494,650 / 658,056 (-25%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -42,993 / -44,139 | 16,450 / 20,021 | 6/9, 6/7, 1/7 | -120,343 / -134,363 | 150,438 / 658,056 (-77%) | no / no / no |

## NY PM, v0.2.2 (comparison), REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 | no rows |||||||
| NY PM MF3 | no rows |||||||

### NY PM, v0.2.2 (comparison), REFERENCE: v0.3 with the 1.5x safety stop (DK3W): per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|

## NY PM: same trade two ways (alone-bare managed vs the same signal on the book's own fixed bracket; a change counts when the managed R differs by >= 0.25 R of the book's own stop; $ = p484, managed minus own bracket)

| book / set | window | matched pairs | give-backs prevented n ($) | winners cut short n ($) | losers cut early n ($) | losers made worse n ($) | all matched pairs net $ (managed minus own bracket) | extra trades from freed slots n ($) | bracket-only trades (blocked) n ($) |
|---|---|---|---|---|---|---|---|---|---|
| NY PM MF2 DK3MAIN | 202410-202610 (24 months) | 374 | 28 (+241170) | 87 (-835335) | 96 (+743650) | 0 (+0) | -92345 | 71 (-34007) | 58 (+75351) |
| NY PM MF3 DK3MAIN | 202410-202610 (24 months) | 693 | 7 (+31760) | 177 (-820715) | 137 (+651815) | 0 (+0) | -207585 | 31 (+15195) | 15 (+20304) |
| **NY PM all books DK3MAIN** | 202410-202610 (24 months) | 1067 | 35 (+272930) | 264 (-1656050) | 233 (+1395465) | 0 (+0) | -299930 | 102 (-18812) | 73 (+95655) |
| NY PM MF2 DK3NOSEAT | 202410-202610 (24 months) | 380 | 28 (+241170) | 89 (-848740) | 96 (+743650) | 0 (+0) | -105975 | 97 (-47652) | 52 (+57365) |
| NY PM MF3 DK3NOSEAT | 202410-202610 (24 months) | 699 | 7 (+31760) | 178 (-823435) | 138 (+654715) | 0 (+0) | -201805 | 43 (+401) | 9 (+26654) |
| **NY PM all books DK3NOSEAT** | 202410-202610 (24 months) | 1079 | 35 (+272930) | 267 (-1672175) | 234 (+1398365) | 0 (+0) | -307780 | 140 (-47251) | 61 (+84019) |
| NY PM MF2 DK3W | 202410-202610 (24 months) | 350 | 25 (+222475) | 82 (-790700) | 85 (+749290) | 6 (-38845) | -79320 | 67 (-53011) | 82 (+121159) |
| NY PM MF3 DK3W | 202410-202610 (24 months) | 678 | 7 (+31760) | 172 (-799515) | 111 (+639675) | 8 (-31060) | -209490 | 31 (+17590) | 30 (+35254) |
| **NY PM all books DK3W** | 202410-202610 (24 months) | 1028 | 32 (+254235) | 254 (-1590215) | 196 (+1388965) | 14 (-69905) | -288810 | 98 (-35421) | 112 (+156413) |

NOTE on the counts: own-bracket peak (for give-backs prevented) is read from the 1-s NQ tape (the fix_A rows store no best price); R = points / the book's median stop distance on fix_A. The matched pairs sum is the same-signal difference only; extra trades from freed slots and blocked bracket-only trades are the entries only one side took.

