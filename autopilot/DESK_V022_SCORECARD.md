# DESK_V022_SCORECARD (generated 2026-11-28 02:41Z by code/th_algo/ar_desk.py; order 0240Z; research only)

Smoothness-first scorecard (Josh's rules: smoother = worst week not worse AND weekly st.dev. not larger, judged per quarter; ACCEPTABLE = smoother in >= 2/3 of quarters overall AND in NQ-up weeks AND in NQ-down weeks, AND income not more than 10 / 20 / 30% below the bracket) on the months that EXIST for each managed set. Window = the months the managed set has (all DONE rows); the reference is cut to the SAME months and the same weeks (a week belongs to the window when its Monday is in a window month; Nov 2025 excluded as everywhere), so like is compared with like. Reference: alone-bare rows (_A) vs the fixed-bracket live-as-run book alone (TL3_DX_<S>_<MF>_fix_A); in-mix rows (_M) vs the live mix as run (TL3_SR_<S>_...). Income = engine p484 ($4.84/lot). The other families keep the 42-month gate in ALGO_REPORT.md (unchanged).

Window facts: Asia and London sets have 37 months (2023-09..2026-10 without 2025-11), NY AM and NY PM sets 24 months (2024-10..2026-10 without 2025-11); NO-GATE sets 8 months (Asia/London 2024-04..2026-10 subset) or 5 months (NY, from 2024-12): they are shown but are too short to judge. Quarter counts are small (Asia/London up to 13 quarters, NY up to 8): read n of n literally.

# Asia

## Asia, v0.2.2, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK22MAIN) | 202309-202610 (37 months) | -31,530 / -50,206 | 8,689 / 20,523 | 11/14, 8/11, 7/12 | -222,803 / -111,441 | -198,618 / 882,294 (-123%) | no / no / no |
| Asia MF2 (DK22MAIN) | 202309-202610 (37 months) | -26,783 / -30,707 | 5,950 / 10,772 | 9/14, 7/11, 6/12 | -93,385 / -92,225 | 74,687 / 409,579 (-82%) | no / no / no |
| Asia MF3 (DK22MAIN) | 202309-202610 (37 months) | -41,929 / -39,659 | 11,983 / 16,561 | 10/14, 7/11, 10/12 | -239,545 / -103,232 | -89,438 / 635,263 (-114%) | no / no / no |

### Asia, v0.2.2, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK22MAIN) | 202309-202610 (37 months) | -32,781 / -37,409 | 12,434 / 18,895 | 9/14, 7/11, 7/12 | -121,924 / -67,941 | 315,003 / 893,671 (-65%) | no / no / no |
| Asia MF2 in mix (DK22MAIN) | 202309-202610 (37 months) | -44,065 / -37,409 | 17,251 / 18,895 | 9/14, 7/11, 6/12 | -77,919 / -67,941 | 682,685 / 893,671 (-24%) | no / no / no |
| Asia MF3 in mix (DK22MAIN) | 202309-202610 (37 months) | -41,738 / -37,409 | 17,033 / 18,895 | 8/14, 6/11, 6/12 | -94,491 / -67,941 | 556,048 / 893,671 (-38%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -44,293 / -37,409 | 10,045 / 18,895 | 11/14, 8/11, 6/12 | -308,325 / -67,941 | -233,607 / 893,671 (-126%) | no / no / no |

## Asia, v0.2.2, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK22NOSEAT) | 202309-202610 (37 months) | -31,530 / -50,206 | 8,470 / 20,523 | 11/14, 9/11, 7/12 | -214,184 / -111,441 | -189,999 / 882,294 (-122%) | no / no / no |
| Asia MF2 (DK22NOSEAT) | 202309-202610 (37 months) | -26,783 / -30,707 | 5,994 / 10,772 | 9/14, 7/11, 6/12 | -93,385 / -92,225 | 79,813 / 409,579 (-81%) | no / no / no |
| Asia MF3 (DK22NOSEAT) | 202309-202610 (37 months) | -41,929 / -39,659 | 12,408 / 16,561 | 8/14, 6/11, 10/12 | -267,289 / -103,232 | -130,856 / 635,263 (-121%) | no / no / no |

### Asia, v0.2.2, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -32,510 / -37,409 | 12,380 / 18,895 | 9/14, 8/11, 7/12 | -121,408 / -67,941 | 321,311 / 893,671 (-64%) | no / no / no |
| Asia MF2 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -44,065 / -37,409 | 17,278 / 18,895 | 8/14, 6/11, 6/12 | -77,919 / -67,941 | 680,817 / 893,671 (-24%) | no / no / no |
| Asia MF3 in mix (DK22NOSEAT) | 202309-202311, 202401-202610 (36 months) | -41,738 / -37,409 | 17,262 / 19,119 | 6/14, 5/11, 5/12 | -95,510 / -67,941 | 534,304 / 861,661 (-38%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202311, 202401-202610 (36 months) | -44,293 / -37,409 | 10,183 / 19,119 | 10/14, 7/11, 6/12 | -306,290 / -67,941 | -240,644 / 861,661 (-128%) | no / no / no |

## Asia, v0.2.2, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -34,707 / -36,473 | 14,521 / 26,284 | 4/7, 2/5, 0/1 | -183,654 / -88,590 | -181,762 / 171,577 (-206%) | no / no / no |
| Asia MF2 (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -9,180 / -11,558 | 6,788 / 7,431 | 1/7, 1/5, 0/1 | -19,563 / -41,547 | 92,094 / 131,079 (-30%) | no / no / no |
| Asia MF3 (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -37,281 / -21,151 | 13,023 / 16,718 | 3/7, 2/5, 1/1 | -103,558 / -54,534 | -16,528 / 229,446 (-107%) | no / no / no |

### Asia, v0.2.2, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -25,941 / -24,216 | 14,066 / 24,342 | 3/7, 4/5, 0/1 | -68,021 / -40,703 | 84,171 / 378,701 (-78%) | no / no / no |
| Asia MF2 in mix (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -31,154 / -24,216 | 23,162 / 24,342 | 2/7, 1/5, 0/1 | -47,640 / -40,703 | 334,840 / 378,701 (-12%) | no / no / no |
| Asia MF3 in mix (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -41,738 / -24,216 | 20,603 / 24,342 | 4/7, 2/5, 1/1 | -54,938 / -40,703 | 272,292 / 378,701 (-28%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -50,400 / -24,216 | 12,879 / 24,342 | 2/7, 2/5, 1/1 | -126,460 / -40,703 | -66,100 / 378,701 (-117%) | no / no / no |

## Asia, v0.2.1, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK21MAIN) | 202309-202610 (37 months) | -29,242 / -50,206 | 7,517 / 20,523 | 11/14, 8/11, 7/12 | -148,632 / -111,441 | -116,004 / 882,294 (-113%) | no / no / no |
| Asia MF2 (DK21MAIN) | 202309-202610 (37 months) | -26,388 / -30,707 | 6,124 / 10,772 | 9/14, 7/11, 6/12 | -76,546 / -92,225 | 115,043 / 409,579 (-72%) | no / no / no |
| Asia MF3 (DK21MAIN) | 202309-202610 (37 months) | -39,175 / -39,659 | 11,778 / 16,561 | 11/14, 7/11, 10/12 | -224,159 / -103,232 | -57,982 / 635,263 (-109%) | no / no / no |

### Asia, v0.2.1, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK21MAIN) | 202309-202610 (37 months) | -33,011 / -37,409 | 12,325 / 18,895 | 10/14, 8/11, 7/12 | -101,109 / -67,941 | 366,862 / 893,671 (-59%) | no / no / no |
| Asia MF2 in mix (DK21MAIN) | 202309-202610 (37 months) | -43,960 / -37,409 | 17,290 / 18,895 | 9/14, 7/11, 6/12 | -73,925 / -67,941 | 714,633 / 893,671 (-20%) | no / no / no |
| Asia MF3 in mix (DK21MAIN) | 202309-202610 (37 months) | -39,678 / -37,409 | 16,683 / 18,895 | 9/14, 6/11, 7/12 | -100,193 / -67,941 | 608,882 / 893,671 (-32%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -41,293 / -37,409 | 9,465 / 18,895 | 10/14, 8/11, 6/12 | -174,730 / -67,941 | -96,964 / 893,671 (-111%) | no / no / no |

## Asia, v0.2.1, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK21NOSEAT) | 202309-202610 (37 months) | -22,625 / -50,206 | 7,501 / 20,523 | 12/14, 9/11, 7/12 | -155,107 / -111,441 | -122,478 / 882,294 (-114%) | no / no / no |
| Asia MF2 (DK21NOSEAT) | 202309-202610 (37 months) | -26,388 / -30,707 | 6,163 / 10,772 | 9/14, 7/11, 6/12 | -76,546 / -92,225 | 119,930 / 409,579 (-71%) | no / no / no |
| Asia MF3 (DK21NOSEAT) | 202309-202610 (37 months) | -39,175 / -39,659 | 12,185 / 16,561 | 9/14, 6/11, 8/12 | -248,140 / -103,232 | -88,237 / 635,263 (-114%) | no / no / no |

### Asia, v0.2.1, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK21NOSEAT) | 202309-202610 (37 months) | -32,705 / -37,409 | 12,257 / 18,895 | 10/14, 9/11, 7/12 | -100,804 / -67,941 | 366,072 / 893,671 (-59%) | no / no / no |
| Asia MF2 in mix (DK21NOSEAT) | 202309-202610 (37 months) | -43,960 / -37,409 | 17,318 / 18,895 | 8/14, 6/11, 6/12 | -73,925 / -67,941 | 712,680 / 893,671 (-20%) | no / no / no |
| Asia MF3 in mix (DK21NOSEAT) | 202309-202610 (37 months) | -39,678 / -37,409 | 16,814 / 18,895 | 8/14, 6/11, 7/12 | -95,686 / -67,941 | 616,238 / 893,671 (-31%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -41,293 / -37,409 | 9,597 / 18,895 | 10/14, 8/11, 6/12 | -174,049 / -67,941 | -92,351 / 893,671 (-110%) | no / no / no |

## Asia, v0.2.1, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -34,378 / -36,473 | 13,700 / 26,284 | 3/7, 2/5, 0/1 | -183,172 / -88,590 | -175,392 / 171,577 (-202%) | no / no / no |
| Asia MF2 (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -9,086 / -11,558 | 6,805 / 7,431 | 1/7, 1/5, 0/1 | -14,079 / -41,547 | 98,861 / 131,079 (-25%) | no / no / no |
| Asia MF3 (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -37,102 / -21,151 | 13,221 / 16,718 | 3/7, 2/5, 1/1 | -114,875 / -54,534 | -33,437 / 229,446 (-115%) | no / no / no |

### Asia, v0.2.1, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -26,586 / -24,216 | 13,401 / 24,342 | 3/7, 4/5, 0/1 | -41,439 / -40,703 | 138,639 / 378,701 (-63%) | no / no / no |
| Asia MF2 in mix (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -30,249 / -24,216 | 23,298 / 24,342 | 3/7, 3/5, 0/1 | -46,735 / -40,703 | 342,230 / 378,701 (-10%) | no / no / no |
| Asia MF3 in mix (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -39,678 / -24,216 | 19,898 / 24,342 | 5/7, 3/5, 0/1 | -59,528 / -40,703 | 255,120 / 378,701 (-33%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -48,080 / -24,216 | 11,795 / 24,342 | 3/7, 3/5, 1/1 | -91,721 / -40,703 | -21,415 / 378,701 (-106%) | no / no / no |

## Asia, v0.2, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DKMAIN) | 202309-202610 (37 months) | -29,242 / -50,206 | 6,455 / 20,523 | 12/14, 8/11, 9/12 | -163,705 / -111,441 | -157,387 / 882,294 (-118%) | no (smooth) / no (smooth) / no (smooth) |
| Asia MF2 (DKMAIN) | 202309-202610 (37 months) | -27,978 / -30,707 | 5,691 / 10,772 | 8/14, 8/11, 8/12 | -84,587 / -92,225 | 61,797 / 409,579 (-85%) | no / no / no |
| Asia MF3 (DKMAIN) | 202309-202610 (37 months) | -39,320 / -39,659 | 11,753 / 16,561 | 11/14, 8/11, 8/12 | -322,335 / -103,232 | -235,650 / 635,263 (-137%) | no (smooth) / no (smooth) / no (smooth) |

### Asia, v0.2, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DKMAIN) | 202309-202610 (37 months) | -33,011 / -37,409 | 12,359 / 18,895 | 9/14, 7/11, 6/12 | -106,233 / -67,941 | 356,232 / 893,671 (-60%) | no / no / no |
| Asia MF2 in mix (DKMAIN) | 202309-202610 (37 months) | -43,960 / -37,409 | 17,087 / 18,895 | 9/14, 7/11, 7/12 | -73,925 / -67,941 | 687,404 / 893,671 (-23%) | no / no / no |
| Asia MF3 in mix (DKMAIN) | 202309-202610 (37 months) | -38,502 / -37,409 | 16,231 / 18,895 | 9/14, 6/11, 6/12 | -99,207 / -67,941 | 515,826 / 893,671 (-42%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -40,118 / -37,409 | 8,849 / 18,895 | 10/14, 7/11, 6/12 | -270,388 / -67,941 | -227,879 / 893,671 (-125%) | no / no / no |

## Asia, v0.2, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DKNOSEAT) | 202309-202610 (36 months) | -22,557 / -50,206 | 6,782 / 20,749 | 13/14, 9/11, 9/12 | -189,965 / -111,441 | -183,722 / 871,641 (-121%) | no (smooth) / no (smooth) / no (smooth) |
| Asia MF2 (DKNOSEAT) | 202309-202610 (37 months) | -27,978 / -30,707 | 5,738 / 10,772 | 8/14, 8/11, 8/12 | -82,612 / -92,225 | 70,186 / 409,579 (-83%) | no / no / no |
| Asia MF3 (DKNOSEAT) | 202310-202610 (36 months) | -39,320 / -39,659 | 12,424 / 16,659 | 9/13, 8/11, 5/11 | -371,868 / -103,232 | -288,621 / 625,437 (-146%) | no / no / no |

### Asia, v0.2, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DKNOSEAT) | 202309-202610 (37 months) | -32,940 / -37,409 | 12,302 / 18,895 | 9/14, 7/11, 6/12 | -105,850 / -67,941 | 346,270 / 893,671 (-61%) | no / no / no |
| Asia MF2 in mix (DKNOSEAT) | 202309-202605, 202607, 202609-202610 (35 months) | -43,960 / -37,409 | 15,184 / 16,903 | 8/14, 6/11, 7/11 | -73,925 / -67,941 | 480,218 / 646,908 (-26%) | no / no / no |
| Asia MF3 in mix (DKNOSEAT) | 202309-202610 (37 months) | -38,502 / -37,409 | 16,393 / 18,895 | 7/14, 6/11, 5/12 | -94,700 / -67,941 | 509,280 / 893,671 (-43%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202605, 202607, 202609-202610 (35 months) | -40,118 / -37,409 | 9,023 / 16,903 | 9/14, 7/11, 5/11 | -225,095 / -67,941 | -182,284 / 646,908 (-128%) | no / no / no |

## Asia, v0.2, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -35,297 / -36,473 | 11,922 / 26,284 | 2/7, 3/5, 0/1 | -185,465 / -88,590 | -176,918 / 171,577 (-203%) | no / no / no |
| Asia MF2 (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -13,737 / -11,558 | 7,413 / 7,431 | 1/7, 1/5, 0/1 | -18,501 / -41,547 | 82,230 / 131,079 (-37%) | no / no / no |
| Asia MF3 (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -37,247 / -21,151 | 13,266 / 16,718 | 2/7, 1/5, 1/1 | -143,181 / -54,534 | -91,006 / 229,446 (-140%) | no / no / no |

### Asia, v0.2, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| Asia MF1 in mix (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202608, 202610 (7 months) | -24,697 / -24,216 | 10,672 / 15,888 | 1/6, 1/5, 1/1 | -55,259 / -40,703 | 17,740 / 178,390 (-90%) | no / no / no |
| Asia MF2 in mix (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -30,249 / -24,216 | 23,162 / 24,342 | 3/7, 3/5, 1/1 | -46,735 / -40,703 | 334,711 / 378,701 (-12%) | no / no / no |
| Asia MF3 in mix (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -38,502 / -24,216 | 20,148 / 24,342 | 4/7, 2/5, 1/1 | -58,353 / -40,703 | 235,009 / 378,701 (-38%) | no / no / no |
| **Asia MIX** (live mix + sum of the 3 managed books' deltas: MF1, MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202404, 202406, 202408, 202412, 202504, 202608, 202610 (7 months) | -45,015 / -24,216 | 12,025 / 15,888 | 2/6, 2/5, 1/1 | -143,653 / -40,703 | -90,734 / 178,390 (-151%) | no / no / no |

## Asia: same trade two ways (alone-bare managed vs the same signal on the book's own fixed bracket; a change counts when the managed R differs by >= 0.25 R of the book's own stop; $ = p484, managed minus own bracket)

| book / set | window | matched pairs | give-backs prevented n ($) | winners cut short n ($) | losers cut early n ($) | losers made worse n ($) | all matched pairs net $ (managed minus own bracket) | extra trades from freed slots n ($) | bracket-only trades (blocked) n ($) |
|---|---|---|---|---|---|---|---|---|---|
| Asia MF1 DK22MAIN | 202309-202610 (37 months) | 964 | 218 (+1203740) | 346 (-2349010) | 375 (+1889395) | 53 (-111455) | -572625 | 496 (-94864) | 1027 (+390081) |
| Asia MF2 DK22MAIN | 202309-202610 (37 months) | 470 | 54 (+387085) | 196 (-995225) | 119 (+763150) | 12 (-38310) | -265440 | 46 (+39514) | 144 (+129728) |
| Asia MF3 DK22MAIN | 202309-202610 (37 months) | 1914 | 240 (+1449285) | 853 (-3316720) | 532 (+2832875) | 121 (-289920) | -605835 | 1034 (-78382) | 418 (+17726) |
| **Asia all books DK22MAIN** | 202309-202610 (37 months) | 3348 | 512 (+3040110) | 1395 (-6660955) | 1026 (+5485420) | 186 (-439685) | -1443900 | 1576 (-133732) | 1589 (+537535) |
| Asia MF1 DK22NOSEAT | 202309-202610 (37 months) | 977 | 223 (+1234915) | 350 (-2382045) | 381 (+1926935) | 53 (-111455) | -571385 | 508 (-104217) | 1014 (+373348) |
| Asia MF2 DK22NOSEAT | 202309-202610 (37 months) | 472 | 54 (+387085) | 197 (-997445) | 119 (+763150) | 12 (-38310) | -267115 | 46 (+39514) | 142 (+122926) |
| Asia MF3 DK22NOSEAT | 202309-202610 (37 months) | 1952 | 243 (+1470265) | 869 (-3375060) | 541 (+2878180) | 124 (-297620) | -627580 | 1087 (-110681) | 380 (+5100) |
| **Asia all books DK22NOSEAT** | 202309-202610 (37 months) | 3401 | 520 (+3092265) | 1416 (-6754550) | 1041 (+5568265) | 189 (-447385) | -1466080 | 1641 (-175385) | 1536 (+501375) |
| Asia MF1 DK22NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 482 | 121 (+683955) | 155 (-1106135) | 192 (+1009555) | 38 (-80785) | -171640 | 493 (-120802) | 73 (+110405) |
| Asia MF2 DK22NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 153 | 20 (+159325) | 72 (-343815) | 38 (+277105) | 4 (-16055) | -75075 | 15 (+11269) | 1 (-7184) |
| Asia MF3 DK22NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 597 | 78 (+511715) | 274 (-1039335) | 171 (+958090) | 51 (-130495) | -141870 | 267 (-30144) | 66 (+82273) |
| **Asia all books DK22NOGATE** | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 1232 | 219 (+1354995) | 501 (-2489285) | 401 (+2244750) | 93 (-227335) | -388585 | 775 (-139676) | 140 (+185494) |
| Asia MF1 DK21MAIN | 202309-202610 (37 months) | 955 | 219 (+1206790) | 344 (-2343210) | 369 (+1890640) | 57 (-120780) | -565050 | 489 (-54246) | 1036 (+361240) |
| Asia MF2 DK21MAIN | 202309-202610 (37 months) | 470 | 54 (+398050) | 196 (-991740) | 119 (+788675) | 12 (-38855) | -231070 | 48 (+43841) | 144 (+129728) |
| Asia MF3 DK21MAIN | 202309-202610 (37 months) | 1906 | 239 (+1428540) | 855 (-3296055) | 520 (+2792690) | 132 (-314160) | -642320 | 1036 (-69960) | 426 (-34746) |
| **Asia all books DK21MAIN** | 202309-202610 (37 months) | 3331 | 512 (+3033380) | 1395 (-6631005) | 1008 (+5472005) | 201 (-473795) | -1438440 | 1573 (-80365) | 1606 (+456222) |
| Asia MF1 DK21NOSEAT | 202309-202610 (37 months) | 974 | 225 (+1242035) | 349 (-2386120) | 377 (+1936620) | 59 (-125440) | -570620 | 507 (-57293) | 1017 (+359096) |
| Asia MF2 DK21NOSEAT | 202309-202610 (37 months) | 472 | 54 (+398050) | 197 (-994200) | 119 (+788675) | 12 (-38855) | -232985 | 48 (+43841) | 142 (+122926) |
| Asia MF3 DK21NOSEAT | 202309-202610 (37 months) | 1947 | 244 (+1463445) | 874 (-3358895) | 531 (+2850210) | 133 (-317340) | -649530 | 1089 (-96935) | 385 (-38675) |
| **Asia all books DK21NOSEAT** | 202309-202610 (37 months) | 3393 | 523 (+3103530) | 1420 (-6739215) | 1027 (+5575505) | 204 (-481635) | -1453135 | 1644 (-110387) | 1544 (+443347) |
| Asia MF1 DK21NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 478 | 124 (+682480) | 153 (-1087520) | 191 (+999220) | 41 (-87565) | -167220 | 491 (-109034) | 77 (+119429) |
| Asia MF2 DK21NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 151 | 20 (+161090) | 71 (-334800) | 39 (+282250) | 4 (-16055) | -59160 | 14 (+10223) | 3 (+1433) |
| Asia MF3 DK21NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 595 | 77 (+500815) | 276 (-1037825) | 169 (+966480) | 58 (-141305) | -146790 | 255 (-54320) | 68 (+66400) |
| **Asia all books DK21NOGATE** | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 1224 | 221 (+1344385) | 500 (-2460145) | 399 (+2247950) | 103 (-244925) | -373170 | 760 (-153130) | 148 (+187262) |

NOTE on the counts: own-bracket peak (for give-backs prevented) is read from the 1-s NQ tape (the fix_A rows store no best price); R = points / the book's median stop distance on fix_A. The matched pairs sum is the same-signal difference only; extra trades from freed slots and blocked bracket-only trades are the entries only one side took.

# NY AM

## NY AM, v0.2.2, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK22MAIN) | 202410-202610 (24 months) | -46,763 / -81,412 | 26,565 / 38,170 | 7/9, 5/7, 5/7 | -113,982 / -158,282 | 622,071 / 1,261,834 (-51%) | no (smooth) / no (smooth) / no (smooth) |
| NY AM MF2 (DK22MAIN) | 202410-202610 (24 months) | -60,375 / -59,825 | 17,091 / 23,724 | 6/9, 5/7, 5/7 | -177,004 / -263,422 | 6,145 / 169,966 (-96%) | no (smooth) / no (smooth) / no (smooth) |
| NY AM MF4 (DK22MAIN) | 202410-202610 (24 months) | -89,332 / -73,124 | 24,565 / 28,083 | 5/9, 4/7, 4/7 | -145,799 / -199,315 | 242,885 / 432,840 (-44%) | no / no / no |
| NY AM MF5 (DK22MAIN) | 202410-202610 (24 months) | -21,271 / -50,861 | 8,705 / 13,987 | 6/9, 3/7, 4/7 | -84,752 / -103,673 | 45,191 / 256,213 (-82%) | no / no / no |

### NY AM, v0.2.2, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK22MAIN) | 202410-202610 (24 months) | -109,804 / -110,130 | 47,104 / 54,746 | 5/9, 2/7, 4/7 | -170,928 / -163,622 | 2,304,631 / 2,847,328 (-19%) | no / no / no |
| NY AM MF2 in mix (DK22MAIN) | 202410-202610 (24 months) | -95,946 / -110,130 | 51,059 / 54,746 | 6/9, 5/7, 3/7 | -199,594 / -163,622 | 2,617,074 / 2,847,328 (-8%) | no / no / no |
| NY AM MF4 in mix (DK22MAIN) | 202410-202610 (24 months) | -79,171 / -110,130 | 49,028 / 54,746 | 7/9, 4/7, 4/7 | -182,966 / -163,622 | 2,544,423 / 2,847,328 (-11%) | no / no / no |
| NY AM MF5 in mix (DK22MAIN) | 202410-202610 (24 months) | -97,560 / -110,130 | 52,813 / 54,746 | 4/9, 4/7, 4/7 | -166,985 / -163,622 | 2,759,157 / 2,847,328 (-3%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -64,328 / -110,130 | 37,994 / 54,746 | 4/9, 3/7, 4/7 | -130,615 / -163,622 | 1,683,301 / 2,847,328 (-41%) | no / no / no |

## NY AM, v0.2.2, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK22NOSEAT) | 202410-202610 (24 months) | -55,737 / -81,412 | 27,049 / 38,170 | 6/9, 4/7, 5/7 | -141,429 / -158,282 | 595,841 / 1,261,834 (-53%) | no / no / no |
| NY AM MF2 (DK22NOSEAT) | 202410-202610 (24 months) | -60,375 / -59,825 | 17,151 / 23,724 | 6/9, 5/7, 5/7 | -187,881 / -263,422 | 197 / 169,966 (-100%) | no (smooth) / no (smooth) / no (smooth) |
| NY AM MF4 (DK22NOSEAT) | 202410-202610 (24 months) | -89,332 / -73,124 | 24,624 / 28,083 | 5/9, 4/7, 4/7 | -152,121 / -199,315 | 194,107 / 432,840 (-55%) | no / no / no |
| NY AM MF5 (DK22NOSEAT) | 202410-202610 (24 months) | -23,433 / -50,861 | 8,995 / 13,987 | 6/9, 3/7, 4/7 | -91,465 / -103,673 | 28,710 / 256,213 (-89%) | no / no / no |

### NY AM, v0.2.2, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -109,804 / -110,130 | 46,934 / 54,746 | 5/9, 2/7, 4/7 | -170,928 / -163,622 | 2,304,996 / 2,847,328 (-19%) | no / no / no |
| NY AM MF2 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -95,946 / -110,130 | 51,125 / 54,746 | 6/9, 5/7, 3/7 | -199,594 / -163,622 | 2,616,508 / 2,847,328 (-8%) | no / no / no |
| NY AM MF4 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -79,171 / -110,130 | 48,790 / 54,746 | 7/9, 4/7, 4/7 | -182,966 / -163,622 | 2,528,588 / 2,847,328 (-11%) | no / no / no |
| NY AM MF5 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -97,560 / -110,130 | 52,633 / 54,746 | 4/9, 4/7, 4/7 | -166,985 / -163,622 | 2,746,132 / 2,847,328 (-4%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -64,328 / -110,130 | 37,931 / 54,746 | 4/9, 3/7, 4/7 | -129,429 / -163,622 | 1,654,241 / 2,847,328 (-42%) | no / no / no |

## NY AM, v0.2.2, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -51,913 / -81,412 | 36,854 / 42,317 | 2/5, 1/3, 0/0 | -105,367 / -150,362 | 186,266 / 286,943 (-35%) | no / no / no |
| NY AM MF2 (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -39,903 / -50,657 | 21,800 / 29,386 | 2/5, 2/3, 0/0 | -129,947 / -132,437 | -68,179 / 131,113 (-152%) | no / no / no |
| NY AM MF4 (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -89,332 / -57,552 | 32,290 / 29,026 | 0/5, 0/3, 0/0 | -152,189 / -110,169 | 4,619 / 166,449 (-97%) | no / no / no |
| NY AM MF5 (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -27,410 / -24,016 | 9,193 / 13,956 | 0/5, 0/3, 0/0 | -39,583 / -31,193 | 2,016 / 112,374 (-98%) | no / no / no |

### NY AM, v0.2.2, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -65,358 / -75,094 | 46,801 / 60,125 | 2/5, 1/3, 0/0 | -89,313 / -175,958 | 725,467 / 787,120 (-8%) | no / no / no |
| NY AM MF2 in mix (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -71,656 / -75,094 | 53,645 / 60,125 | 3/5, 2/3, 0/0 | -158,670 / -175,958 | 560,269 / 787,120 (-29%) | no / no / no |
| NY AM MF4 in mix (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -78,921 / -75,094 | 47,620 / 60,125 | 3/5, 2/3, 0/0 | -183,005 / -175,958 | 629,620 / 787,120 (-20%) | no / no / no |
| NY AM MF5 in mix (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -99,824 / -75,094 | 61,867 / 60,125 | 0/5, 0/3, 0/0 | -204,754 / -175,958 | 712,051 / 787,120 (-10%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202412, 202504, 202606, 202608, 202610 (5 months) | -57,315 / -75,094 | 42,746 / 60,125 | 1/5, 1/3, 0/0 | -142,113 / -175,958 | 266,048 / 787,120 (-66%) | no / no / no |

## NY AM, v0.2.1, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK21MAIN) | 202410-202610 (24 months) | -51,390 / -81,412 | 29,040 / 38,170 | 4/9, 5/7, 4/7 | -142,631 / -158,282 | 942,887 / 1,261,834 (-25%) | no / no / no |
| NY AM MF2 (DK21MAIN) | 202410-202610 (24 months) | -52,855 / -59,825 | 16,087 / 23,724 | 7/9, 5/7, 4/7 | -186,535 / -263,422 | -72,949 / 169,966 (-143%) | no / no / no |
| NY AM MF4 (DK21MAIN) | 202410-202610 (24 months) | -79,895 / -73,124 | 23,055 / 28,083 | 4/9, 2/7, 5/7 | -154,575 / -199,315 | 270,994 / 432,840 (-37%) | no / no / no |
| NY AM MF5 (DK21MAIN) | 202410-202610 (24 months) | -22,197 / -50,861 | 8,946 / 13,987 | 7/9, 3/7, 4/7 | -77,296 / -103,673 | 90,587 / 256,213 (-65%) | no / no / no |

### NY AM, v0.2.1, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK21MAIN) | 202410-202610 (24 months) | -106,040 / -110,130 | 47,953 / 54,746 | 5/9, 2/7, 3/7 | -139,522 / -163,622 | 2,512,309 / 2,847,328 (-12%) | no / no / no |
| NY AM MF2 in mix (DK21MAIN) | 202410-202610 (24 months) | -96,991 / -110,130 | 50,640 / 54,746 | 5/9, 3/7, 3/7 | -199,900 / -163,622 | 2,572,519 / 2,847,328 (-10%) | no / no / no |
| NY AM MF4 in mix (DK21MAIN) | 202410-202610 (24 months) | -77,355 / -110,130 | 48,884 / 54,746 | 6/9, 3/7, 3/7 | -169,659 / -163,622 | 2,656,826 / 2,847,328 (-7%) | no / no / no |
| NY AM MF5 in mix (DK21MAIN) | 202410-202610 (24 months) | -95,374 / -110,130 | 53,181 / 54,746 | 4/9, 3/7, 4/7 | -169,556 / -163,622 | 2,670,217 / 2,847,328 (-6%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -61,946 / -110,130 | 38,603 / 54,746 | 4/9, 3/7, 4/7 | -169,805 / -163,622 | 1,869,888 / 2,847,328 (-34%) | no / no / no |

## NY AM, v0.2.1, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK21NOSEAT) | 202410-202610 (24 months) | -51,390 / -81,412 | 29,272 / 38,170 | 4/9, 5/7, 4/7 | -142,631 / -158,282 | 923,819 / 1,261,834 (-27%) | no / no / no |
| NY AM MF2 (DK21NOSEAT) | 202410-202610 (24 months) | -52,855 / -59,825 | 16,132 / 23,724 | 7/9, 5/7, 4/7 | -191,772 / -263,422 | -73,860 / 169,966 (-143%) | no / no / no |
| NY AM MF4 (DK21NOSEAT) | 202410-202610 (24 months) | -79,895 / -73,124 | 23,522 / 28,083 | 5/9, 2/7, 4/7 | -174,461 / -199,315 | 199,844 / 432,840 (-54%) | no / no / no |
| NY AM MF5 (DK21NOSEAT) | 202410-202610 (24 months) | -22,197 / -50,861 | 9,020 / 13,987 | 7/9, 3/7, 4/7 | -77,296 / -103,673 | 95,326 / 256,213 (-63%) | no / no / no |

### NY AM, v0.2.1, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK21NOSEAT) | 202410-202610 (24 months) | -106,040 / -110,130 | 47,954 / 54,746 | 5/9, 2/7, 3/7 | -139,522 / -163,622 | 2,503,746 / 2,847,328 (-12%) | no / no / no |
| NY AM MF2 in mix (DK21NOSEAT) | 202410-202610 (24 months) | -96,991 / -110,130 | 50,692 / 54,746 | 5/9, 3/7, 3/7 | -199,900 / -163,622 | 2,574,645 / 2,847,328 (-10%) | no / no / no |
| NY AM MF4 in mix (DK21NOSEAT) | 202410-202610 (24 months) | -77,355 / -110,130 | 48,653 / 54,746 | 6/9, 4/7, 3/7 | -169,659 / -163,622 | 2,637,734 / 2,847,328 (-7%) | no / no / no |
| NY AM MF5 in mix (DK21NOSEAT) | 202410-202610 (24 months) | -95,374 / -110,130 | 53,153 / 54,746 | 4/9, 3/7, 4/7 | -169,556 / -163,622 | 2,674,013 / 2,847,328 (-6%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -61,946 / -110,130 | 38,627 / 54,746 | 4/9, 3/7, 4/7 | -169,805 / -163,622 | 1,848,155 / 2,847,328 (-35%) | no / no / no |

## NY AM, v0.2.1, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -87,727 / -81,412 | 34,018 / 42,317 | 3/5, 2/3, 0/0 | -127,745 / -150,362 | 171,218 / 286,943 (-40%) | no / no / no |
| NY AM MF2 (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -26,740 / -50,657 | 18,254 / 29,386 | 4/5, 3/3, 0/0 | -95,227 / -132,437 | -52,312 / 131,113 (-140%) | no / no / no |
| NY AM MF4 (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -79,895 / -57,552 | 26,587 / 29,026 | 3/5, 1/3, 0/0 | -121,116 / -110,169 | 86,351 / 166,449 (-48%) | no / no / no |
| NY AM MF5 (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -25,940 / -24,016 | 9,149 / 13,956 | 0/5, 0/3, 0/0 | -40,627 / -31,193 | -3,149 / 112,374 (-103%) | no / no / no |

### NY AM, v0.2.1, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -45,459 / -75,094 | 44,908 / 60,125 | 2/5, 1/3, 0/0 | -141,531 / -175,958 | 698,489 / 787,120 (-11%) | no / no / no |
| NY AM MF2 in mix (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -72,656 / -75,094 | 53,963 / 60,125 | 1/5, 1/3, 0/0 | -152,745 / -175,958 | 567,057 / 787,120 (-28%) | no / no / no |
| NY AM MF4 in mix (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -76,546 / -75,094 | 48,229 / 60,125 | 3/5, 3/3, 0/0 | -169,123 / -175,958 | 707,895 / 787,120 (-10%) | no / no / no |
| NY AM MF5 in mix (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -96,740 / -75,094 | 62,061 / 60,125 | 0/5, 0/3, 0/0 | -270,230 / -175,958 | 606,421 / 787,120 (-23%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202412, 202504, 202606, 202608, 202610 (5 months) | -59,639 / -75,094 | 34,267 / 60,125 | 3/5, 2/3, 0/0 | -172,183 / -175,958 | 218,504 / 787,120 (-72%) | no / no / no |

## NY AM, v0.2, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DKMAIN) | 202410-202610 (24 months) | -51,390 / -81,412 | 23,536 / 38,170 | 7/9, 6/7, 5/7 | -216,607 / -158,282 | 386,421 / 1,261,834 (-69%) | no (smooth) / no (smooth) / no (smooth) |
| NY AM MF2 (DKMAIN) | 202410-202610 (24 months) | -52,855 / -59,825 | 16,054 / 23,724 | 7/9, 5/7, 4/7 | -229,885 / -263,422 | -123,378 / 169,966 (-173%) | no / no / no |
| NY AM MF4 (DKMAIN) | 202410-202610 (24 months) | -79,895 / -73,124 | 23,035 / 28,083 | 5/9, 2/7, 5/7 | -154,575 / -199,315 | 273,039 / 432,840 (-37%) | no / no / no |
| NY AM MF5 (DKMAIN) | 202410-202610 (24 months) | -22,197 / -50,861 | 8,732 / 13,987 | 7/9, 3/7, 4/7 | -77,122 / -103,673 | 99,390 / 256,213 (-61%) | no / no / no |

### NY AM, v0.2, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DKMAIN) | 202410-202610 (24 months) | -110,960 / -110,130 | 45,214 / 54,746 | 5/9, 4/7, 4/7 | -228,933 / -163,622 | 2,128,809 / 2,847,328 (-25%) | no / no / no |
| NY AM MF2 in mix (DKMAIN) | 202410-202610 (24 months) | -96,991 / -110,130 | 50,620 / 54,746 | 4/9, 4/7, 3/7 | -199,900 / -163,622 | 2,523,958 / 2,847,328 (-11%) | no / no / no |
| NY AM MF4 in mix (DKMAIN) | 202410-202610 (24 months) | -77,355 / -110,130 | 48,873 / 54,746 | 6/9, 3/7, 3/7 | -169,659 / -163,622 | 2,658,716 / 2,847,328 (-7%) | no / no / no |
| NY AM MF5 in mix (DKMAIN) | 202410-202610 (24 months) | -95,374 / -110,130 | 53,412 / 54,746 | 4/9, 2/7, 4/7 | -169,346 / -163,622 | 2,647,320 / 2,847,328 (-7%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -86,526 / -110,130 | 36,581 / 54,746 | 5/9, 3/7, 3/7 | -172,286 / -163,622 | 1,416,819 / 2,847,328 (-50%) | no / no / no |

## NY AM, v0.2, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DKNOSEAT) | 202410-202610 (24 months) | -51,390 / -81,412 | 24,618 / 38,170 | 7/9, 6/7, 5/7 | -265,348 / -158,282 | 366,097 / 1,261,834 (-71%) | no (smooth) / no (smooth) / no (smooth) |
| NY AM MF2 (DKNOSEAT) | 202410-202610 (24 months) | -52,855 / -59,825 | 16,122 / 23,724 | 7/9, 5/7, 4/7 | -246,654 / -263,422 | -142,738 / 169,966 (-184%) | no / no / no |
| NY AM MF4 (DKNOSEAT) | 202410-202610 (24 months) | -79,895 / -73,124 | 23,498 / 28,083 | 5/9, 2/7, 4/7 | -170,470 / -199,315 | 203,615 / 432,840 (-53%) | no / no / no |
| NY AM MF5 (DKNOSEAT) | 202410-202610 (24 months) | -22,197 / -50,861 | 8,796 / 13,987 | 7/9, 3/7, 4/7 | -77,122 / -103,673 | 100,966 / 256,213 (-61%) | no / no / no |

### NY AM, v0.2, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DKNOSEAT) | 202410-202610 (24 months) | -110,960 / -110,130 | 45,371 / 54,746 | 5/9, 4/7, 4/7 | -228,600 / -163,622 | 2,112,406 / 2,847,328 (-26%) | no / no / no |
| NY AM MF2 in mix (DKNOSEAT) | 202410-202610 (24 months) | -96,991 / -110,130 | 50,755 / 54,746 | 4/9, 4/7, 3/7 | -199,900 / -163,622 | 2,519,363 / 2,847,328 (-12%) | no / no / no |
| NY AM MF4 in mix (DKNOSEAT) | 202410-202610 (24 months) | -77,355 / -110,130 | 48,646 / 54,746 | 6/9, 4/7, 3/7 | -169,659 / -163,622 | 2,640,509 / 2,847,328 (-7%) | no / no / no |
| NY AM MF5 in mix (DKNOSEAT) | 202410-202610 (24 months) | -95,374 / -110,130 | 53,380 / 54,746 | 4/9, 2/7, 4/7 | -169,346 / -163,622 | 2,648,288 / 2,847,328 (-7%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -86,526 / -110,130 | 37,096 / 54,746 | 6/9, 3/7, 3/7 | -172,286 / -163,622 | 1,378,583 / 2,847,328 (-52%) | no / no / no |

## NY AM, v0.2, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -87,727 / -81,412 | 32,392 / 42,317 | 3/5, 1/3, 0/0 | -130,742 / -150,362 | 64,359 / 286,943 (-78%) | no / no / no |
| NY AM MF2 (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -26,740 / -50,657 | 17,627 / 29,386 | 4/5, 3/3, 0/0 | -95,227 / -132,437 | -24,304 / 131,113 (-119%) | no / no / no |
| NY AM MF4 (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -79,895 / -57,552 | 26,587 / 29,026 | 3/5, 1/3, 0/0 | -121,116 / -110,169 | 86,351 / 166,449 (-48%) | no / no / no |
| NY AM MF5 (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -25,940 / -24,016 | 8,820 / 13,956 | 0/5, 0/3, 0/0 | -40,976 / -31,193 | -13,987 / 112,374 (-112%) | no / no / no |

### NY AM, v0.2, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY AM MF1 in mix (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -63,973 / -75,094 | 46,221 / 60,125 | 3/5, 2/3, 0/0 | -141,888 / -175,958 | 595,648 / 787,120 (-24%) | no / no / no |
| NY AM MF2 in mix (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -72,656 / -75,094 | 53,536 / 60,125 | 2/5, 2/3, 0/0 | -152,745 / -175,958 | 584,374 / 787,120 (-26%) | no / no / no |
| NY AM MF4 in mix (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -76,546 / -75,094 | 48,229 / 60,125 | 3/5, 3/3, 0/0 | -169,123 / -175,958 | 707,895 / 787,120 (-10%) | no / no / no |
| NY AM MF5 in mix (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -96,740 / -75,094 | 62,490 / 60,125 | 0/5, 0/3, 0/0 | -270,230 / -175,958 | 597,028 / 787,120 (-24%) | no / no / no |
| **NY AM MIX** (live mix + sum of the 4 managed books' deltas: MF1, MF2, MF4, MF5; other live books unmanaged; post-hoc additive, interaction neglected) | 202412, 202504, 202606, 202608, 202610 (5 months) | -57,755 / -75,094 | 34,944 / 60,125 | 2/5, 1/3, 0/0 | -179,203 / -175,958 | 123,586 / 787,120 (-84%) | no / no / no |

## NY AM: same trade two ways (alone-bare managed vs the same signal on the book's own fixed bracket; a change counts when the managed R differs by >= 0.25 R of the book's own stop; $ = p484, managed minus own bracket)

| book / set | window | matched pairs | give-backs prevented n ($) | winners cut short n ($) | losers cut early n ($) | losers made worse n ($) | all matched pairs net $ (managed minus own bracket) | extra trades from freed slots n ($) | bracket-only trades (blocked) n ($) |
|---|---|---|---|---|---|---|---|---|---|
| NY AM MF1 DK22MAIN | 202410-202610 (24 months) | 754 | 98 (+1367190) | 355 (-3651045) | 222 (+2820140) | 12 (-76665) | -816230 | 1027 (+116956) | 337 (-246) |
| NY AM MF2 DK22MAIN | 202410-202610 (24 months) | 1045 | 162 (+1410555) | 458 (-2254980) | 312 (+2475485) | 100 (-336155) | -67540 | 654 (-89737) | 369 (+23389) |
| NY AM MF4 DK22MAIN | 202410-202610 (24 months) | 1394 | 1 (+3390) | 135 (-759060) | 129 (+1133540) | 44 (-194700) | -65260 | 606 (-129043) | 982 (-31857) |
| NY AM MF5 DK22MAIN | 202410-202610 (24 months) | 1462 | 205 (+843080) | 676 (-1658890) | 445 (+1651305) | 116 (-191885) | -178125 | 676 (-36311) | 443 (+27888) |
| **NY AM all books DK22MAIN** | 202410-202610 (24 months) | 4655 | 466 (+3624215) | 1624 (-8323975) | 1108 (+8080470) | 272 (-799405) | -1127155 | 2963 (-138135) | 2131 (+19173) |
| NY AM MF1 DK22NOSEAT | 202410-202610 (24 months) | 756 | 98 (+1367190) | 356 (-3655090) | 222 (+2820140) | 12 (-76665) | -822655 | 1041 (+107219) | 335 (+9822) |
| NY AM MF2 DK22NOSEAT | 202410-202610 (24 months) | 1050 | 163 (+1419400) | 459 (-2257740) | 315 (+2496025) | 101 (-338875) | -52480 | 663 (-91154) | 364 (+46799) |
| NY AM MF4 DK22NOSEAT | 202410-202610 (24 months) | 1408 | 1 (+3390) | 136 (-762990) | 131 (+1151440) | 45 (-198975) | -52920 | 620 (-157800) | 968 (+504) |
| NY AM MF5 DK22NOSEAT | 202410-202610 (24 months) | 1477 | 211 (+860755) | 680 (-1669215) | 453 (+1674585) | 117 (-193825) | -166290 | 690 (-47264) | 428 (+45250) |
| **NY AM all books DK22NOSEAT** | 202410-202610 (24 months) | 4691 | 473 (+3650735) | 1631 (-8345035) | 1121 (+8142190) | 275 (-808340) | -1094345 | 3014 (-188998) | 2095 (+102376) |
| NY AM MF1 DK22NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 222 | 28 (+440140) | 102 (-1053235) | 64 (+912860) | 8 (-40710) | -170630 | 425 (+37893) | 53 (+28586) |
| NY AM MF2 DK22NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 261 | 38 (+355050) | 106 (-516710) | 72 (+629055) | 35 (-125365) | +5160 | 155 (-100771) | 90 (+105016) |
| NY AM MF4 DK22NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 334 | 0 (+0) | 27 (-240225) | 26 (+259920) | 15 (-72770) | -64385 | 137 (-99493) | 283 (+13327) |
| NY AM MF5 DK22NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 442 | 50 (+220270) | 198 (-469750) | 121 (+457975) | 53 (-87990) | -92770 | 121 (-7197) | 53 (+36855) |
| **NY AM all books DK22NOGATE** | 202412, 202504, 202606, 202608, 202610 (5 months) | 1259 | 116 (+1015460) | 433 (-2279920) | 283 (+2259810) | 111 (-326835) | -322625 | 838 (-169569) | 479 (+183784) |
| NY AM MF1 DK21MAIN | 202410-202610 (24 months) | 762 | 101 (+1461405) | 358 (-3698000) | 226 (+2961785) | 10 (-61685) | -697010 | 1032 (+306211) | 329 (-41129) |
| NY AM MF2 DK21MAIN | 202410-202610 (24 months) | 1034 | 154 (+1315925) | 458 (-2252220) | 301 (+2341265) | 103 (-348800) | -208790 | 633 (-98537) | 380 (-55825) |
| NY AM MF4 DK21MAIN | 202410-202610 (24 months) | 1370 | 1 (+3390) | 137 (-749835) | 131 (+1129270) | 46 (-208415) | +36655 | 637 (-104813) | 1006 (+86701) |
| NY AM MF5 DK21MAIN | 202410-202610 (24 months) | 1467 | 208 (+865160) | 671 (-1654160) | 454 (+1691795) | 117 (-193455) | -139255 | 684 (+6208) | 438 (+65280) |
| **NY AM all books DK21MAIN** | 202410-202610 (24 months) | 4633 | 464 (+3645880) | 1624 (-8354215) | 1112 (+8124115) | 276 (-812355) | -1008400 | 2986 (+109068) | 2153 (+55027) |
| NY AM MF1 DK21NOSEAT | 202410-202610 (24 months) | 763 | 101 (+1461405) | 359 (-3702045) | 226 (+2961785) | 10 (-61685) | -701055 | 1038 (+286876) | 328 (-45440) |
| NY AM MF2 DK21NOSEAT | 202410-202610 (24 months) | 1039 | 155 (+1325095) | 459 (-2254980) | 304 (+2363375) | 104 (-351520) | -192160 | 646 (-88695) | 375 (-32415) |
| NY AM MF4 DK21NOSEAT | 202410-202610 (24 months) | 1396 | 1 (+3390) | 139 (-756460) | 135 (+1153295) | 48 (-218335) | +22850 | 653 (-115728) | 980 (+133131) |
| NY AM MF5 DK21NOSEAT | 202410-202610 (24 months) | 1476 | 213 (+880135) | 673 (-1658770) | 459 (+1706485) | 117 (-193455) | -128215 | 694 (+6363) | 429 (+71736) |
| **NY AM all books DK21NOSEAT** | 202410-202610 (24 months) | 4674 | 470 (+3670025) | 1630 (-8372255) | 1124 (+8184940) | 279 (-824995) | -998580 | 3031 (+88817) | 2112 (+127012) |
| NY AM MF1 DK21NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 223 | 27 (+437430) | 100 (-1053040) | 63 (+911195) | 7 (-39525) | -168650 | 414 (+60707) | 52 (+15015) |
| NY AM MF2 DK21NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 261 | 35 (+326515) | 108 (-514190) | 73 (+612485) | 34 (-123590) | -18975 | 154 (-98582) | 90 (+76031) |
| NY AM MF4 DK21NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 342 | 0 (+0) | 30 (-224440) | 26 (+283195) | 17 (-85765) | +2525 | 151 (-126845) | 275 (-28261) |
| NY AM MF5 DK21NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 440 | 50 (+219310) | 199 (-476685) | 116 (+444580) | 52 (-85925) | -110795 | 113 (-1646) | 55 (+33001) |
| **NY AM all books DK21NOGATE** | 202412, 202504, 202606, 202608, 202610 (5 months) | 1266 | 112 (+983255) | 437 (-2268355) | 278 (+2251455) | 110 (-334805) | -295895 | 832 (-166366) | 472 (+95787) |

NOTE on the counts: own-bracket peak (for give-backs prevented) is read from the 1-s NQ tape (the fix_A rows store no best price); R = points / the book's median stop distance on fix_A. The matched pairs sum is the same-signal difference only; extra trades from freed slots and blocked bracket-only trades are the entries only one side took.

# London

## London, v0.2.2, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK22MAIN) | 202309-202610 (37 months) | -40,155 / -52,798 | 12,176 / 16,123 | 9/14, 7/11, 7/12 | -213,104 / -107,192 | 198,554 / 510,693 (-61%) | no / no / no |
| London MF3 (DK22MAIN) | 202309-202610 (37 months) | -13,866 / -23,120 | 4,755 / 6,993 | 8/14, 6/11, 7/12 | -153,491 / -47,177 | -98,813 / 185,303 (-153%) | no / no / no |

### London, v0.2.2, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK22MAIN) | 202309-202610 (37 months) | -103,259 / -107,350 | 21,137 / 23,472 | 7/14, 4/11, 6/12 | -296,935 / -224,333 | 568,916 / 881,056 (-35%) | no / no / no |
| London MF3 in mix (DK22MAIN) | 202309-202610 (37 months) | -86,881 / -107,350 | 22,251 / 23,472 | 5/14, 2/11, 4/12 | -247,830 / -224,333 | 596,940 / 881,056 (-32%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -82,790 / -107,350 | 19,661 / 23,472 | 6/14, 5/11, 4/12 | -336,126 / -224,333 | 284,800 / 881,056 (-68%) | no / no / no |

## London, v0.2.2, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK22NOSEAT) | 202309-202610 (37 months) | -45,113 / -52,798 | 12,786 / 16,123 | 7/14, 6/11, 7/12 | -220,553 / -107,192 | 198,246 / 510,693 (-61%) | no / no / no |
| London MF3 (DK22NOSEAT) | 202309-202610 (37 months) | -20,967 / -23,120 | 5,939 / 6,993 | 5/14, 3/11, 5/12 | -295,248 / -47,177 | -241,126 / 185,303 (-230%) | no / no / no |

### London, v0.2.2, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -101,617 / -107,350 | 21,095 / 23,472 | 5/14, 2/11, 6/12 | -301,562 / -224,333 | 568,608 / 881,056 (-35%) | no / no / no |
| London MF3 in mix (DK22NOSEAT) | 202309-202610 (37 months) | -94,716 / -107,350 | 23,169 / 23,472 | 2/14, 1/11, 3/12 | -306,790 / -224,333 | 454,626 / 881,056 (-48%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -88,983 / -107,350 | 20,640 / 23,472 | 6/14, 4/11, 5/12 | -427,600 / -224,333 | 142,179 / 881,056 (-84%) | no / no / no |

## London, v0.2.2, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -40,155 / -42,807 | 12,147 / 16,286 | 5/7, 4/5, 0/1 | -100,209 / -102,831 | 26,422 / 112,892 (-77%) | no / no / no |
| London MF3 (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -7,708 / -18,402 | 4,949 / 7,919 | 3/7, 3/5, 0/1 | -56,000 / -43,150 | -25,820 / 9,625 (-368%) | no / no / no |

### London, v0.2.2, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -48,036 / -50,689 | 19,698 / 20,669 | 5/7, 3/5, 0/1 | -134,555 / -97,998 | 28,578 / 115,047 (-75%) | no / no / no |
| London MF3 in mix (DK22NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -61,452 / -50,689 | 21,194 / 20,669 | 2/7, 2/5, 0/1 | -122,487 / -97,998 | 79,603 / 115,047 (-31%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -58,800 / -50,689 | 18,883 / 20,669 | 4/7, 2/5, 0/1 | -162,491 / -97,998 | -6,867 / 115,047 (-106%) | no / no / no |

## London, v0.2.1, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK21MAIN) | 202309-202610 (37 months) | -40,975 / -52,798 | 12,359 / 16,123 | 10/14, 9/11, 7/12 | -215,447 / -107,192 | 114,189 / 510,693 (-78%) | no / no / no |
| London MF3 (DK21MAIN) | 202309-202610 (37 months) | -27,862 / -23,120 | 5,485 / 6,993 | 8/14, 5/11, 6/12 | -184,578 / -47,177 | -115,591 / 185,303 (-162%) | no / no / no |

### London, v0.2.1, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK21MAIN) | 202309-202610 (37 months) | -92,790 / -107,350 | 21,209 / 23,472 | 7/14, 6/11, 5/12 | -279,351 / -224,333 | 484,551 / 881,056 (-45%) | no / no / no |
| London MF3 in mix (DK21MAIN) | 202309-202610 (37 months) | -88,737 / -107,350 | 22,228 / 23,472 | 3/14, 3/11, 3/12 | -267,040 / -224,333 | 580,161 / 881,056 (-34%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -74,177 / -107,350 | 19,870 / 23,472 | 4/14, 4/11, 3/12 | -367,322 / -224,333 | 183,657 / 881,056 (-79%) | no / no / no |

## London, v0.2.1, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK21NOSEAT) | 202309-202610 (37 months) | -42,753 / -52,798 | 12,777 / 16,123 | 10/14, 8/11, 6/12 | -238,111 / -107,192 | 126,347 / 510,693 (-75%) | no / no / no |
| London MF3 (DK21NOSEAT) | 202309-202610 (37 months) | -26,626 / -23,120 | 6,156 / 6,993 | 4/14, 3/11, 6/12 | -304,109 / -47,177 | -259,942 / 185,303 (-240%) | no / no / no |

### London, v0.2.1, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK21NOSEAT) | 202309-202610 (37 months) | -99,053 / -107,350 | 21,195 / 23,472 | 7/14, 5/11, 5/12 | -304,572 / -224,333 | 496,710 / 881,056 (-44%) | no / no / no |
| London MF3 in mix (DK21NOSEAT) | 202309-202509, 202602-202610 (34 months) | -107,167 / -107,350 | 23,479 / 23,490 | 3/13, 1/10, 0/12 | -333,964 / -226,115 | 392,713 / 779,980 (-50%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202509, 202602-202610 (34 months) | -98,871 / -107,350 | 21,432 / 23,490 | 5/13, 5/10, 4/12 | -491,787 / -226,115 | 41,810 / 779,980 (-95%) | no / no / no |

## London, v0.2.1, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -40,975 / -42,807 | 14,252 / 16,286 | 4/7, 4/5, 0/1 | -96,189 / -102,831 | 17,922 / 112,892 (-84%) | no / no / no |
| London MF3 (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -27,862 / -18,402 | 7,156 / 7,919 | 2/7, 2/5, 0/1 | -81,369 / -43,150 | -37,667 / 9,625 (-491%) | no / no / no |

### London, v0.2.1, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -48,856 / -50,689 | 20,545 / 20,669 | 4/7, 3/5, 0/1 | -116,815 / -97,998 | 20,078 / 115,047 (-83%) | no / no / no |
| London MF3 in mix (DK21NOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -54,525 / -50,689 | 20,933 / 20,669 | 2/7, 1/5, 0/1 | -137,622 / -97,998 | 67,756 / 115,047 (-41%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -52,693 / -50,689 | 19,791 / 20,669 | 3/7, 2/5, 0/1 | -170,960 / -97,998 | -27,214 / 115,047 (-124%) | no / no / no |

## London, v0.2, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DKMAIN) | 202309-202610 (37 months) | -40,975 / -52,798 | 11,898 / 16,123 | 11/14, 9/11, 8/12 | -227,167 / -107,192 | 105,542 / 510,693 (-79%) | no (smooth) / no (smooth) / no (smooth) |
| London MF3 (DKMAIN) | 202309-202610 (37 months) | -27,862 / -23,120 | 4,547 / 6,993 | 7/14, 6/11, 6/12 | -211,094 / -47,177 | -171,683 / 185,303 (-193%) | no / no / no |

### London, v0.2, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DKMAIN) | 202309-202610 (37 months) | -92,790 / -107,350 | 20,969 / 23,472 | 7/14, 5/11, 6/12 | -282,293 / -224,333 | 475,904 / 881,056 (-46%) | no / no / no |
| London MF3 in mix (DKMAIN) | 202309-202610 (37 months) | -88,179 / -107,350 | 22,016 / 23,472 | 4/14, 3/11, 3/12 | -291,799 / -224,333 | 524,070 / 881,056 (-41%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -73,619 / -107,350 | 19,160 / 23,472 | 4/14, 4/11, 4/12 | -400,688 / -224,333 | 118,919 / 881,056 (-87%) | no / no / no |

## London, v0.2, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DKNOSEAT) | 202309-202610 (37 months) | -42,753 / -52,798 | 12,282 / 16,123 | 10/14, 9/11, 6/12 | -247,777 / -107,192 | 90,687 / 510,693 (-82%) | no / no / no |
| London MF3 (DKNOSEAT) | 202309-202610 (37 months) | -26,626 / -23,120 | 5,141 / 6,993 | 5/14, 3/11, 5/12 | -461,147 / -47,177 | -436,849 / 185,303 (-336%) | no / no / no |

### London, v0.2, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DKNOSEAT) | 202309-202610 (37 months) | -99,053 / -107,350 | 20,952 / 23,472 | 6/14, 4/11, 5/12 | -298,194 / -224,333 | 461,049 / 881,056 (-48%) | no / no / no |
| London MF3 in mix (DKNOSEAT) | 202309-202610 (37 months) | -104,912 / -107,350 | 22,954 / 23,472 | 4/14, 2/11, 2/12 | -416,436 / -224,333 | 258,903 / 881,056 (-71%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202309-202610 (37 months) | -96,615 / -107,350 | 20,389 / 23,472 | 5/14, 4/11, 4/12 | -580,613 / -224,333 | -161,103 / 881,056 (-118%) | no / no / no |

## London, v0.2, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -40,975 / -42,807 | 13,499 / 16,286 | 4/7, 3/5, 0/1 | -66,726 / -102,831 | 42,381 / 112,892 (-62%) | no / no / no |
| London MF3 (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -27,862 / -18,402 | 6,294 / 7,919 | 3/7, 3/5, 0/1 | -54,888 / -43,150 | -21,034 / 9,625 (-319%) | no / no / no |

### London, v0.2, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| London MF1 in mix (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -48,856 / -50,689 | 19,845 / 20,669 | 4/7, 3/5, 0/1 | -92,262 / -97,998 | 44,536 / 115,047 (-61%) | no / no / no |
| London MF3 in mix (DKNOGATE) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -54,245 / -50,689 | 20,593 / 20,669 | 2/7, 2/5, 0/1 | -121,995 / -97,998 | 84,388 / 115,047 (-27%) | no / no / no |
| **London MIX** (live mix + sum of the 2 managed books' deltas: MF1, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | -52,413 / -50,689 | 18,216 / 20,669 | 3/7, 2/5, 0/1 | -125,501 / -97,998 | 13,877 / 115,047 (-88%) | no / no / no |

## London: same trade two ways (alone-bare managed vs the same signal on the book's own fixed bracket; a change counts when the managed R differs by >= 0.25 R of the book's own stop; $ = p484, managed minus own bracket)

| book / set | window | matched pairs | give-backs prevented n ($) | winners cut short n ($) | losers cut early n ($) | losers made worse n ($) | all matched pairs net $ (managed minus own bracket) | extra trades from freed slots n ($) | bracket-only trades (blocked) n ($) |
|---|---|---|---|---|---|---|---|---|---|
| London MF1 DK22MAIN | 202309-202610 (37 months) | 952 | 0 (+0) | 175 (-1022700) | 123 (+1108905) | 6 (-35545) | -230675 | 144 (-53031) | 79 (+76446) |
| London MF3 DK22MAIN | 202309-202610 (37 months) | 1174 | 2 (+6210) | 362 (-774360) | 213 (+669565) | 2 (-3730) | -246620 | 1902 (-83281) | 557 (-56982) |
| **London all books DK22MAIN** | 202309-202610 (37 months) | 2126 | 2 (+6210) | 537 (-1797060) | 336 (+1778470) | 8 (-39275) | -477295 | 2046 (-136312) | 636 (+19464) |
| London MF1 DK22NOSEAT | 202309-202610 (37 months) | 975 | 0 (+0) | 179 (-1041105) | 125 (+1120825) | 7 (-39245) | -234290 | 197 (-54198) | 56 (+53542) |
| London MF3 DK22NOSEAT | 202309-202610 (37 months) | 1322 | 2 (+6210) | 397 (-846095) | 239 (+735605) | 3 (-6075) | -264415 | 3394 (-174714) | 409 (-22439) |
| **London all books DK22NOSEAT** | 202309-202610 (37 months) | 2297 | 2 (+6210) | 576 (-1887200) | 364 (+1856430) | 10 (-45320) | -498705 | 3591 (-228912) | 465 (+31103) |
| London MF1 DK22NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 220 | 0 (+0) | 46 (-271430) | 31 (+280570) | 3 (-22960) | -77235 | 19 (-13521) | 18 (+34103) |
| London MF3 DK22NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 301 | 1 (+1290) | 89 (-191605) | 72 (+224785) | 1 (-2120) | -30745 | 450 (-9101) | 178 (-31733) |
| **London all books DK22NOGATE** | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 521 | 1 (+1290) | 135 (-463035) | 103 (+505355) | 4 (-25080) | -107980 | 469 (-22622) | 196 (+2370) |
| London MF1 DK21MAIN | 202309-202610 (37 months) | 953 | 0 (+0) | 179 (-1036830) | 122 (+1089460) | 8 (-48215) | -274155 | 149 (-85334) | 78 (+80390) |
| London MF3 DK21MAIN | 202309-202610 (37 months) | 1168 | 3 (+7410) | 377 (-799260) | 209 (+669585) | 2 (-3730) | -252365 | 1986 (-117084) | 563 (-77530) |
| **London all books DK21MAIN** | 202309-202610 (37 months) | 2121 | 3 (+7410) | 556 (-1836090) | 331 (+1759045) | 10 (-51945) | -526520 | 2135 (-202419) | 641 (+2860) |
| London MF1 DK21NOSEAT | 202309-202610 (37 months) | 972 | 0 (+0) | 183 (-1055745) | 123 (+1095885) | 9 (-51915) | -282890 | 197 (-70298) | 59 (+60706) |
| London MF3 DK21NOSEAT | 202309-202610 (37 months) | 1323 | 3 (+7410) | 416 (-879455) | 238 (+747555) | 2 (-3730) | -266980 | 3355 (-202031) | 408 (-31689) |
| **London all books DK21NOSEAT** | 202309-202610 (37 months) | 2295 | 3 (+7410) | 599 (-1935200) | 361 (+1843440) | 11 (-55645) | -549870 | 3552 (-272329) | 467 (+29016) |
| London MF1 DK21NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 223 | 0 (+0) | 46 (-267980) | 29 (+289815) | 4 (-28320) | -58845 | 21 (-27973) | 15 (+29979) |
| London MF3 DK21NOGATE | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 295 | 1 (+1290) | 87 (-190865) | 66 (+208425) | 1 (-2120) | -47580 | 451 (-30831) | 184 (-54081) |
| **London all books DK21NOGATE** | 202404, 202406, 202408, 202412, 202504, 202606, 202608, 202610 (8 months) | 518 | 1 (+1290) | 133 (-458845) | 95 (+498240) | 5 (-30440) | -106425 | 472 (-58804) | 199 (-24102) |

NOTE on the counts: own-bracket peak (for give-backs prevented) is read from the 1-s NQ tape (the fix_A rows store no best price); R = points / the book's median stop distance on fix_A. The matched pairs sum is the same-signal difference only; extra trades from freed slots and blocked bracket-only trades are the entries only one side took.

# NY PM

## NY PM, v0.2.2, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK22MAIN) | 202410-202610 (24 months) | -23,729 / -41,926 | 8,485 / 18,229 | 8/9, 7/7, 6/7 | -113,521 / -165,629 | -36,355 / 235,203 (-115%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DK22MAIN) | 202410-202610 (24 months) | -28,499 / -28,888 | 8,526 / 14,432 | 6/9, 4/7, 3/7 | -106,151 / -75,125 | 52,793 / 415,930 (-87%) | no / no / no |

### NY PM, v0.2.2, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK22MAIN) | 202410-202610 (24 months) | -34,555 / -44,139 | 17,173 / 20,021 | 5/9, 5/7, 3/7 | -132,429 / -134,363 | 320,101 / 658,056 (-51%) | no / no / no |
| NY PM MF3 in mix (DK22MAIN) | 202410-202610 (24 months) | -46,607 / -44,139 | 19,734 / 20,021 | 2/9, 2/7, 1/7 | -100,659 / -134,363 | 496,391 / 658,056 (-25%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -42,993 / -44,139 | 16,414 / 20,021 | 6/9, 6/7, 1/7 | -110,164 / -134,363 | 158,436 / 658,056 (-76%) | no / no / no |

## NY PM, v0.2.2, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK22NOSEAT) | 202410-202610 (24 months) | -19,741 / -41,926 | 8,578 / 18,229 | 8/9, 7/7, 6/7 | -119,609 / -165,629 | -35,686 / 235,203 (-115%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DK22NOSEAT) | 202410-202610 (24 months) | -28,499 / -28,888 | 8,452 / 14,432 | 6/9, 3/7, 3/7 | -102,650 / -75,125 | 48,330 / 415,930 (-88%) | no / no / no |

### NY PM, v0.2.2, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -34,555 / -44,139 | 17,234 / 20,021 | 5/9, 5/7, 3/7 | -129,200 / -134,363 | 313,845 / 658,056 (-52%) | no / no / no |
| NY PM MF3 in mix (DK22NOSEAT) | 202410-202610 (24 months) | -46,607 / -44,139 | 19,773 / 20,021 | 2/9, 2/7, 1/7 | -102,142 / -134,363 | 494,650 / 658,056 (-25%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -42,993 / -44,139 | 16,450 / 20,021 | 6/9, 6/7, 1/7 | -120,343 / -134,363 | 150,438 / 658,056 (-77%) | no / no / no |

## NY PM, v0.2.2, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -11,035 / -18,601 | 7,143 / 14,122 | 4/5, 3/3, 0/0 | -23,667 / -32,954 | 24,013 / 141,619 (-83%) | no / no / no |
| NY PM MF3 (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -14,153 / -25,498 | 7,463 / 12,342 | 4/5, 2/3, 0/0 | -24,696 / -33,778 | 47,897 / 28,058 (+71%) | no / no / no |

### NY PM, v0.2.2, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -21,318 / -23,047 | 14,632 / 19,904 | 3/5, 1/3, 0/0 | -52,717 / -45,012 | 103,635 / 234,341 (-56%) | no / no / no |
| NY PM MF3 in mix (DK22NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -24,913 / -23,047 | 19,398 / 19,904 | 2/5, 1/3, 0/0 | -28,156 / -45,012 | 216,973 / 234,341 (-7%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202412, 202504, 202606, 202608, 202610 (5 months) | -26,522 / -23,047 | 12,684 / 19,904 | 4/5, 2/3, 0/0 | -48,079 / -45,012 | 86,267 / 234,341 (-63%) | no / no / no |

## NY PM, v0.2.1, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK21MAIN) | 202410-202610 (24 months) | -30,474 / -41,926 | 8,175 / 18,229 | 7/9, 6/7, 5/7 | -106,599 / -165,629 | -28,267 / 235,203 (-112%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DK21MAIN) | 202410-202610 (24 months) | -26,384 / -28,888 | 8,848 / 14,432 | 7/9, 5/7, 2/7 | -89,190 / -75,125 | 46,793 / 415,930 (-89%) | no / no / no |

### NY PM, v0.2.1, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK21MAIN) | 202410-202610 (24 months) | -34,496 / -44,139 | 16,977 / 20,021 | 5/9, 5/7, 3/7 | -138,639 / -134,363 | 309,797 / 658,056 (-53%) | no / no / no |
| NY PM MF3 in mix (DK21MAIN) | 202410-202610 (24 months) | -46,572 / -44,139 | 19,946 / 20,021 | 2/9, 2/7, 1/7 | -102,095 / -134,363 | 509,541 / 658,056 (-23%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -40,284 / -44,139 | 16,324 / 20,021 | 5/9, 5/7, 1/7 | -103,432 / -134,363 | 161,282 / 658,056 (-75%) | no / no / no |

## NY PM, v0.2.1, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK21NOSEAT) | 202410-202610 (24 months) | -30,474 / -41,926 | 8,648 / 18,229 | 7/9, 6/7, 5/7 | -130,682 / -165,629 | -47,130 / 235,203 (-120%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DK21NOSEAT) | 202410-202610 (24 months) | -26,384 / -28,888 | 8,843 / 14,432 | 7/9, 4/7, 2/7 | -87,935 / -75,125 | 37,603 / 415,930 (-91%) | no / no / no |

### NY PM, v0.2.1, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK21NOSEAT) | 202410-202610 (24 months) | -34,496 / -44,139 | 17,024 / 20,021 | 5/9, 5/7, 3/7 | -134,736 / -134,363 | 303,722 / 658,056 (-54%) | no / no / no |
| NY PM MF3 in mix (DK21NOSEAT) | 202410-202610 (24 months) | -46,572 / -44,139 | 19,986 / 20,021 | 3/9, 2/7, 1/7 | -103,213 / -134,363 | 504,534 / 658,056 (-23%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -40,284 / -44,139 | 16,362 / 20,021 | 5/9, 5/7, 1/7 | -103,667 / -134,363 | 150,200 / 658,056 (-77%) | no / no / no |

## NY PM, v0.2.1, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -9,779 / -18,601 | 5,867 / 14,122 | 4/5, 3/3, 0/0 | -29,714 / -32,954 | -13,473 / 141,619 (-110%) | no / no / no |
| NY PM MF3 (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -21,533 / -25,498 | 9,243 / 12,342 | 4/5, 2/3, 0/0 | -40,081 / -33,778 | 8,893 / 28,058 (-68%) | no / no / no |

### NY PM, v0.2.1, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -21,148 / -23,047 | 14,459 / 19,904 | 3/5, 1/3, 0/0 | -66,171 / -45,012 | 71,090 / 234,341 (-70%) | no / no / no |
| NY PM MF3 in mix (DK21NOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -24,962 / -23,047 | 19,877 / 19,904 | 2/5, 1/3, 0/0 | -30,128 / -45,012 | 203,690 / 234,341 (-13%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202412, 202504, 202606, 202608, 202610 (5 months) | -26,537 / -23,047 | 13,378 / 19,904 | 2/5, 1/3, 0/0 | -74,184 / -45,012 | 40,439 / 234,341 (-83%) | no / no / no |

## NY PM, v0.2, main: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DKMAIN) | 202410-202610 (24 months) | -30,474 / -41,926 | 6,866 / 18,229 | 7/9, 6/7, 5/7 | -148,571 / -165,629 | -80,345 / 235,203 (-134%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DKMAIN) | 202410-202610 (24 months) | -22,129 / -28,888 | 8,671 / 14,432 | 8/9, 6/7, 2/7 | -89,325 / -75,125 | 35,189 / 415,930 (-92%) | no / no / no |

### NY PM, v0.2, main: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DKMAIN) | 202410-202610 (24 months) | -36,056 / -44,139 | 17,291 / 20,021 | 5/9, 5/7, 1/7 | -138,758 / -134,363 | 300,590 / 658,056 (-54%) | no / no / no |
| NY PM MF3 in mix (DKMAIN) | 202410-202610 (24 months) | -46,517 / -44,139 | 19,917 / 20,021 | 3/9, 3/7, 1/7 | -107,228 / -134,363 | 500,847 / 658,056 (-24%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -43,543 / -44,139 | 16,623 / 20,021 | 6/9, 6/7, 1/7 | -123,736 / -134,363 | 143,381 / 658,056 (-78%) | no / no / no |

## NY PM, v0.2, no-seat: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DKNOSEAT) | 202410-202610 (24 months) | -30,474 / -41,926 | 7,257 / 18,229 | 7/9, 6/7, 5/7 | -171,105 / -165,629 | -98,897 / 235,203 (-142%) | no (smooth) / no (smooth) / no (smooth) |
| NY PM MF3 (DKNOSEAT) | 202410-202610 (24 months) | -23,518 / -28,888 | 8,756 / 14,432 | 8/9, 5/7, 2/7 | -84,545 / -75,125 | 28,415 / 415,930 (-93%) | no / no / no |

### NY PM, v0.2, no-seat: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DKNOSEAT) | 202410-202610 (24 months) | -36,646 / -44,139 | 17,463 / 20,021 | 5/9, 5/7, 1/7 | -138,758 / -134,363 | 295,153 / 658,056 (-55%) | no / no / no |
| NY PM MF3 in mix (DKNOSEAT) | 202410-202610 (24 months) | -46,517 / -44,139 | 19,971 / 20,021 | 3/9, 3/7, 1/7 | -108,902 / -134,363 | 497,658 / 658,056 (-24%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202410-202610 (24 months) | -43,543 / -44,139 | 16,845 / 20,021 | 6/9, 6/7, 1/7 | -140,832 / -134,363 | 134,756 / 658,056 (-80%) | no / no / no |

## NY PM, v0.2, no-gate: per book, alone bare (_A) vs the book on its fixed bracket (fix_A)

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -14,356 / -18,601 | 6,481 / 14,122 | 3/5, 3/3, 0/0 | -42,055 / -32,954 | -19,507 / 141,619 (-114%) | no / no / no |
| NY PM MF3 (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -21,533 / -25,498 | 9,100 / 12,342 | 3/5, 2/3, 0/0 | -41,740 / -33,778 | 903 / 28,058 (-97%) | no / no / no |

### NY PM, v0.2, no-gate: per book in the live mix (_M, the live mix with only this book managed) vs the live mix as run

| managed set | window (months it has; reference cut to the same) | worst week managed / bracket | weekly st.dev. managed / bracket | smoother quarters all, NQ-up, NQ-down (n of n) | max DD managed / bracket | income managed / bracket (change) | acceptable at floor 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| NY PM MF2 in mix (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -21,148 / -23,047 | 15,058 / 19,904 | 3/5, 1/3, 0/0 | -71,099 / -45,012 | 72,070 / 234,341 (-69%) | no / no / no |
| NY PM MF3 in mix (DKNOGATE) | 202412, 202504, 202606, 202608, 202610 (5 months) | -26,208 / -23,047 | 20,105 / 19,904 | 2/5, 1/3, 0/0 | -33,908 / -45,012 | 199,635 / 234,341 (-15%) | no / no / no |
| **NY PM MIX** (live mix + sum of the 2 managed books' deltas: MF2, MF3; other live books unmanaged; post-hoc additive, interaction neglected) | 202412, 202504, 202606, 202608, 202610 (5 months) | -30,100 / -23,047 | 14,428 / 19,904 | 2/5, 1/3, 0/0 | -82,945 / -45,012 | 37,365 / 234,341 (-84%) | no / no / no |

## NY PM: same trade two ways (alone-bare managed vs the same signal on the book's own fixed bracket; a change counts when the managed R differs by >= 0.25 R of the book's own stop; $ = p484, managed minus own bracket)

| book / set | window | matched pairs | give-backs prevented n ($) | winners cut short n ($) | losers cut early n ($) | losers made worse n ($) | all matched pairs net $ (managed minus own bracket) | extra trades from freed slots n ($) | bracket-only trades (blocked) n ($) |
|---|---|---|---|---|---|---|---|---|---|
| NY PM MF2 DK22MAIN | 202410-202610 (24 months) | 357 | 36 (+469845) | 121 (-1249640) | 95 (+1080345) | 2 (-11795) | -109445 | 250 (-96145) | 75 (+91577) |
| NY PM MF3 DK22MAIN | 202410-202610 (24 months) | 680 | 7 (+47640) | 238 (-1024010) | 132 (+894065) | 6 (-23415) | -293990 | 72 (-12971) | 28 (+74112) |
| **NY PM all books DK22MAIN** | 202410-202610 (24 months) | 1037 | 43 (+517485) | 359 (-2273650) | 227 (+1974410) | 8 (-35210) | -403435 | 322 (-109116) | 103 (+165689) |
| NY PM MF2 DK22NOSEAT | 202410-202610 (24 months) | 363 | 36 (+469845) | 122 (-1263035) | 95 (+1080345) | 2 (-11795) | -123865 | 279 (-75067) | 69 (+97566) |
| NY PM MF3 DK22NOSEAT | 202410-202610 (24 months) | 685 | 7 (+47640) | 238 (-1024010) | 132 (+894065) | 6 (-23415) | -294630 | 84 (-27714) | 23 (+63192) |
| **NY PM all books DK22NOSEAT** | 202410-202610 (24 months) | 1048 | 43 (+517485) | 360 (-2287045) | 227 (+1974410) | 8 (-35210) | -418495 | 363 (-102782) | 92 (+160758) |
| NY PM MF2 DK22NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 101 | 10 (+144635) | 39 (-387965) | 24 (+309155) | 2 (-11795) | -58385 | 52 (-35885) | 6 (+23081) |
| NY PM MF3 DK22NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 135 | 0 (+0) | 42 (-173465) | 27 (+180610) | 1 (-4785) | -32005 | 12 (+10432) | 3 (-1407) |
| **NY PM all books DK22NOGATE** | 202412, 202504, 202606, 202608, 202610 (5 months) | 236 | 10 (+144635) | 81 (-561430) | 51 (+489765) | 3 (-16580) | -90390 | 64 (-25454) | 9 (+21674) |
| NY PM MF2 DK21MAIN | 202410-202610 (24 months) | 356 | 37 (+450605) | 124 (-1283460) | 89 (+1017170) | 2 (-11795) | -188420 | 253 (-79842) | 76 (+23078) |
| NY PM MF3 DK21MAIN | 202410-202610 (24 months) | 680 | 7 (+50070) | 240 (-991625) | 129 (+850350) | 6 (-24755) | -303140 | 71 (-16112) | 28 (+65052) |
| **NY PM all books DK21MAIN** | 202410-202610 (24 months) | 1036 | 44 (+500675) | 364 (-2275085) | 218 (+1867520) | 8 (-36550) | -491560 | 324 (-95954) | 104 (+88130) |
| NY PM MF2 DK21NOSEAT | 202410-202610 (24 months) | 362 | 38 (+469125) | 125 (-1297285) | 91 (+1041845) | 2 (-11795) | -177615 | 280 (-74876) | 70 (+57712) |
| NY PM MF3 DK21NOSEAT | 202410-202610 (24 months) | 685 | 7 (+50070) | 240 (-991625) | 129 (+850350) | 6 (-24755) | -303990 | 82 (-35371) | 23 (+54132) |
| **NY PM all books DK21NOSEAT** | 202410-202610 (24 months) | 1047 | 45 (+519195) | 365 (-2288910) | 220 (+1892195) | 8 (-36550) | -481605 | 362 (-110247) | 93 (+111844) |
| NY PM MF2 DK21NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 101 | 11 (+134495) | 41 (-411650) | 21 (+262795) | 2 (-11795) | -123195 | 50 (-36542) | 6 (-5554) |
| NY PM MF3 DK21NOGATE | 202412, 202504, 202606, 202608, 202610 (5 months) | 135 | 0 (+0) | 43 (-177005) | 23 (+146555) | 1 (-4785) | -68480 | 13 (+8522) | 3 (-1407) |
| **NY PM all books DK21NOGATE** | 202412, 202504, 202606, 202608, 202610 (5 months) | 236 | 11 (+134495) | 84 (-588655) | 44 (+409350) | 3 (-16580) | -191675 | 63 (-28020) | 9 (-6961) |

NOTE on the counts: own-bracket peak (for give-backs prevented) is read from the 1-s NQ tape (the fix_A rows store no best price); R = points / the book's median stop distance on fix_A. The matched pairs sum is the same-signal difference only; extra trades from freed slots and blocked bracket-only trades are the entries only one side took.

