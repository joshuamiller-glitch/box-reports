# DESK_JUDGE (generated 2026-11-28 14:15Z by code/th_algo/ar_judge.py; order 1418Z; research only)

LABELS: sections marked IN-SAMPLE choose with the whole window and then score on the same window (optimistic, fitting visible). Sections marked WALKED-FORWARD choose each book's design at every quarter start from the TRAILING 12 MONTHS ONLY and apply it to the next quarter; only that table can be used to decide what goes live. Rule (fixed before looking, same at floors 10 / 20 / 30%): among eligible designs whose income over the evaluation period is >= (1 - floor) x the bracket, take the shallowest max DD; the book's own bracket (fix_A) is always eligible, so with nothing clearing the floor the bracket is picked. Eligible designs = alone-bare _A rows of the registered designs (code/th_algo/desk_designs.json) that have every window month DONE for that book; designs with only in-mix _M rows (v0.7 sun_pl70k50, landscape codes) are NOT eligible here (no _A rows). Mix = live mix + sum over books of (chosen design - the book's own bracket), reference = live mix as run, same days. Windows: Asia / London 2023-09..2026-10, NY AM / NY PM 2024-10..2026-10, Nov 2025 out.

# Asia: window 202309-202610 (37 months); eligible designs: v0.2.2 DK22MAIN, v0.3 DK3MAIN; walkable quarters (trailing 12 months with >= 9 window months): 10 of 14 quarters (2024Q3, 2024Q4, 2025Q1, 2025Q2, 2025Q3, 2025Q4, 2026Q1, 2026Q2, 2026Q3, 2026Q4)

## Asia: per-book whole-window table, IN-SAMPLE (each eligible design alone vs the book's own bracket)

| book | design | income (vs bracket) | max DD managed / bracket | worst week managed / bracket | floors 10 / 20 / 30% |
|---|---|---|---|---|---|
| MF1 | v0.2.2 DK22MAIN | -198,618 (-123%) | -222,803 / -111,441 | -31,530 / -50,206 | no / no / no |
| MF1 | v0.3 DK3MAIN | 460,151 (-48%) | -101,818 / -111,441 | -51,433 / -50,206 | no / no / no |
| MF2 | v0.2.2 DK22MAIN | 74,687 (-82%) | -93,385 / -92,225 | -26,783 / -30,707 | no / no / no |
| MF2 | v0.3 DK3MAIN | 210,720 (-49%) | -112,632 / -92,225 | -32,864 / -30,707 | no / no / no |
| MF3 | v0.2.2 DK22MAIN | -89,438 (-114%) | -239,545 / -103,232 | -41,929 / -39,659 | no / no / no |
| MF3 | v0.3 DK3MAIN | 332,919 (-48%) | -115,728 / -103,232 | -37,207 / -39,659 | no / no / no |

## Asia, floor 10%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 637,970 / 728,364 (-12%) | -77,963 / -67,941 | -39,080 / -37,409 | 21,010 / 21,253 | 15,529 / 15,529 | 7 / 1 / 2 | no (smooth) / YES / YES |
| IN-SAMPLE best-per-book (same days) | 728,364 / 728,364 (+0%) | -67,941 / -67,941 | -37,409 / -37,409 | 21,253 / 21,253 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: BRACKET x10; MF2: BRACKET x7, v0.3 DK3MAIN x2, v0.2.2 DK22MAIN x1; MF3: BRACKET x10
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF3: BRACKET

## Asia, floor 20%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 499,079 / 728,364 (-31%) | -92,806 / -67,941 | -43,549 / -37,409 | 22,206 / 21,253 | 15,529 / 15,529 | 5 / 1 / 2 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 728,364 / 728,364 (+0%) | -67,941 / -67,941 | -37,409 / -37,409 | 21,253 / 21,253 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: BRACKET x8, v0.3 DK3MAIN x2; MF2: BRACKET x7, v0.3 DK3MAIN x2, v0.2.2 DK22MAIN x1; MF3: BRACKET x10
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF3: BRACKET

## Asia, floor 30%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 353,356 / 728,364 (-51%) | -92,806 / -67,941 | -41,849 / -37,409 | 20,897 / 21,253 | 15,529 / 15,529 | 5 / 3 / 1 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 728,364 / 728,364 (+0%) | -67,941 / -67,941 | -37,409 / -37,409 | 21,253 / 21,253 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: BRACKET x7, v0.3 DK3MAIN x3; MF2: BRACKET x5, v0.3 DK3MAIN x3, v0.2.2 DK22MAIN x2; MF3: BRACKET x9, v0.3 DK3MAIN x1
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF3: BRACKET

# NY AM: window 202410-202610 (24 months); eligible designs: v0.2.2 DK22MAIN, v0.3 DK3MAIN; walkable quarters (trailing 12 months with >= 9 window months): 6 of 9 quarters (2025Q3, 2025Q4, 2026Q1, 2026Q2, 2026Q3, 2026Q4)

## NY AM: per-book whole-window table, IN-SAMPLE (each eligible design alone vs the book's own bracket)

| book | design | income (vs bracket) | max DD managed / bracket | worst week managed / bracket | floors 10 / 20 / 30% |
|---|---|---|---|---|---|
| MF1 | v0.2.2 DK22MAIN | 622,071 (-51%) | -113,982 / -158,282 | -46,763 / -81,412 | no (smooth) / no (smooth) / no (smooth) |
| MF1 | v0.3 DK3MAIN | 758,672 (-40%) | -136,263 / -158,282 | -64,062 / -81,412 | no / no / no |
| MF2 | v0.2.2 DK22MAIN | 6,145 (-96%) | -177,004 / -263,422 | -60,375 / -59,825 | no (smooth) / no (smooth) / no (smooth) |
| MF2 | v0.3 DK3MAIN | 6,153 (-96%) | -252,359 / -263,422 | -49,914 / -59,825 | no / no / no |
| MF4 | v0.2.2 DK22MAIN | 242,885 (-44%) | -145,799 / -199,315 | -89,332 / -73,124 | no / no / no |
| MF4 | v0.3 DK3MAIN | 204,524 (-53%) | -202,867 / -199,315 | -62,974 / -73,124 | no / no / no |
| MF5 | v0.2.2 DK22MAIN | 45,191 (-82%) | -84,752 / -103,673 | -21,271 / -50,861 | no / no / no |
| MF5 | v0.3 DK3MAIN | 166,326 (-35%) | -91,139 / -103,673 | -34,616 / -50,861 | no / no / no |

## NY AM, floor 10%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 1,301,088 / 1,959,030 (-34%) | -193,078 / -163,622 | -77,620 / -97,182 | 51,776 / 57,307 | 28,899 / 28,899 | 4 / 2 / 0 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 1,959,030 / 1,959,030 (+0%) | -163,622 / -163,622 | -97,182 / -97,182 | 57,307 / 57,307 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: v0.2.2 DK22MAIN x3, BRACKET x3; MF2: BRACKET x3, v0.2.2 DK22MAIN x3; MF4: BRACKET x4, v0.2.2 DK22MAIN x2; MF5: BRACKET x6
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF4: BRACKET, MF5: BRACKET

## NY AM, floor 20%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 1,276,391 / 1,959,030 (-35%) | -193,078 / -163,622 | -77,620 / -97,182 | 51,752 / 57,307 | 28,899 / 28,899 | 3 / 1 / 0 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 1,959,030 / 1,959,030 (+0%) | -163,622 / -163,622 | -97,182 / -97,182 | 57,307 / 57,307 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: v0.2.2 DK22MAIN x3, BRACKET x3; MF2: BRACKET x3, v0.2.2 DK22MAIN x3; MF4: BRACKET x3, v0.2.2 DK22MAIN x3; MF5: BRACKET x6
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF4: BRACKET, MF5: BRACKET

## NY AM, floor 30%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 1,259,680 / 1,959,030 (-36%) | -193,078 / -163,622 | -77,620 / -97,182 | 52,138 / 57,307 | 28,899 / 28,899 | 3 / 1 / 0 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 1,959,030 / 1,959,030 (+0%) | -163,622 / -163,622 | -97,182 / -97,182 | 57,307 / 57,307 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: v0.2.2 DK22MAIN x3, BRACKET x3; MF2: BRACKET x3, v0.2.2 DK22MAIN x3; MF4: BRACKET x3, v0.2.2 DK22MAIN x3; MF5: BRACKET x5, v0.3 DK3MAIN x1
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF4: BRACKET, MF5: BRACKET

# London: window 202309-202610 (37 months); eligible designs: v0.2.2 DK22MAIN, v0.3 DK3MAIN; walkable quarters (trailing 12 months with >= 9 window months): 10 of 14 quarters (2024Q3, 2024Q4, 2025Q1, 2025Q2, 2025Q3, 2025Q4, 2026Q1, 2026Q2, 2026Q3, 2026Q4)

## London: per-book whole-window table, IN-SAMPLE (each eligible design alone vs the book's own bracket)

| book | design | income (vs bracket) | max DD managed / bracket | worst week managed / bracket | floors 10 / 20 / 30% |
|---|---|---|---|---|---|
| MF1 | v0.2.2 DK22MAIN | 198,554 (-61%) | -213,104 / -107,192 | -40,155 / -52,798 | no / no / no |
| MF1 | v0.3 DK3MAIN | 222,264 (-56%) | -156,679 / -107,192 | -36,382 / -52,798 | no / no / no |
| MF3 | v0.2.2 DK22MAIN | -98,813 (-153%) | -153,491 / -47,177 | -13,866 / -23,120 | no / no / no |
| MF3 | v0.3 DK3MAIN | 41,819 (-77%) | -47,513 / -47,177 | -16,070 / -23,120 | no / no / no |

## London, floor 10%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 462,739 / 586,760 (-21%) | -224,333 / -224,333 | -107,350 / -107,350 | 25,173 / 26,066 | 19,669 / 19,919 | 7 / 4 / 6 | no (smooth) / no (smooth) / YES |
| IN-SAMPLE best-per-book (same days) | 586,760 / 586,760 (+0%) | -224,333 / -224,333 | -107,350 / -107,350 | 26,066 / 26,066 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: BRACKET x8, v0.2.2 DK22MAIN x2; MF3: BRACKET x8, v0.3 DK3MAIN x2
IN-SAMPLE whole-window picks: MF1: BRACKET, MF3: BRACKET

## London, floor 20%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 462,739 / 586,760 (-21%) | -224,333 / -224,333 | -107,350 / -107,350 | 25,173 / 26,066 | 19,669 / 19,919 | 7 / 4 / 6 | no (smooth) / no (smooth) / YES |
| IN-SAMPLE best-per-book (same days) | 586,760 / 586,760 (+0%) | -224,333 / -224,333 | -107,350 / -107,350 | 26,066 / 26,066 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: BRACKET x8, v0.2.2 DK22MAIN x2; MF3: BRACKET x8, v0.3 DK3MAIN x2
IN-SAMPLE whole-window picks: MF1: BRACKET, MF3: BRACKET

## London, floor 30%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 421,171 / 586,760 (-28%) | -252,511 / -224,333 | -107,350 / -107,350 | 25,046 / 26,066 | 19,669 / 19,919 | 6 / 4 / 5 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 586,760 / 586,760 (+0%) | -224,333 / -224,333 | -107,350 / -107,350 | 26,066 / 26,066 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: BRACKET x7, v0.3 DK3MAIN x2, v0.2.2 DK22MAIN x1; MF3: BRACKET x7, v0.3 DK3MAIN x3
IN-SAMPLE whole-window picks: MF1: BRACKET, MF3: BRACKET

# NY PM: window 202410-202610 (24 months); eligible designs: v0.2.2 DK22MAIN, v0.3 DK3MAIN; walkable quarters (trailing 12 months with >= 9 window months): 6 of 9 quarters (2025Q3, 2025Q4, 2026Q1, 2026Q2, 2026Q3, 2026Q4)

## NY PM: per-book whole-window table, IN-SAMPLE (each eligible design alone vs the book's own bracket)

| book | design | income (vs bracket) | max DD managed / bracket | worst week managed / bracket | floors 10 / 20 / 30% |
|---|---|---|---|---|---|
| MF2 | v0.2.2 DK22MAIN | -36,355 (-115%) | -113,521 / -165,629 | -23,729 / -41,926 | no (smooth) / no (smooth) / no (smooth) |
| MF2 | v0.3 DK3MAIN | 70,585 (-70%) | -86,179 / -165,629 | -29,665 / -41,926 | no (smooth) / no (smooth) / no (smooth) |
| MF3 | v0.2.2 DK22MAIN | 52,793 (-87%) | -106,151 / -75,125 | -28,499 / -28,888 | no / no / no |
| MF3 | v0.3 DK3MAIN | 221,462 (-47%) | -70,389 / -75,125 | -29,739 / -28,888 | no / no / no |

## NY PM, floor 10%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 349,154 / 429,095 (-19%) | -104,640 / -88,173 | -44,139 / -44,139 | 19,660 / 18,237 | 27,954 / 27,954 | 2 / 1 / 1 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 429,095 / 429,095 (+0%) | -88,173 / -88,173 | -44,139 / -44,139 | 18,237 / 18,237 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF2: BRACKET x3, v0.3 DK3MAIN x3; MF3: BRACKET x6
IN-SAMPLE whole-window picks: MF2: BRACKET, MF3: BRACKET

## NY PM, floor 20%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 349,154 / 429,095 (-19%) | -104,640 / -88,173 | -44,139 / -44,139 | 19,660 / 18,237 | 27,954 / 27,954 | 2 / 1 / 1 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 429,095 / 429,095 (+0%) | -88,173 / -88,173 | -44,139 / -44,139 | 18,237 / 18,237 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF2: BRACKET x3, v0.3 DK3MAIN x3; MF3: BRACKET x6
IN-SAMPLE whole-window picks: MF2: BRACKET, MF3: BRACKET

## NY PM, floor 30%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 349,154 / 429,095 (-19%) | -104,640 / -88,173 | -44,139 / -44,139 | 19,660 / 18,237 | 27,954 / 27,954 | 2 / 1 / 1 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 429,095 / 429,095 (+0%) | -88,173 / -88,173 | -44,139 / -44,139 | 18,237 / 18,237 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF2: BRACKET x3, v0.3 DK3MAIN x3; MF3: BRACKET x6
IN-SAMPLE whole-window picks: MF2: BRACKET, MF3: BRACKET

