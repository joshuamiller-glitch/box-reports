# DESK_JUDGE (generated 2026-11-28 15:23Z by code/th_algo/ar_judge.py; order 1418Z; research only)

LABELS: sections marked IN-SAMPLE choose with the whole window and then score on the same window (optimistic, fitting visible). Sections marked WALKED-FORWARD choose each book's design at every quarter start from the TRAILING 12 MONTHS ONLY and apply it to the next quarter; only that table can be used to decide what goes live. Rule (fixed before looking, same at floors 10 / 20 / 30%): among eligible designs whose income over the evaluation period is >= (1 - floor) x the bracket, take the shallowest max DD; the book's own bracket (fix_A) is always eligible, so with nothing clearing the floor the bracket is picked. Eligible designs = alone-bare _A rows of the registered designs (code/th_algo/desk_designs.json) that have every window month DONE for that book; designs with only in-mix _M rows (v0.7 sun_pl70k50, landscape codes) are NOT eligible here (no _A rows). Mix = live mix + sum over books of (chosen design - the book's own bracket), reference = live mix as run, same days. Windows: Asia / London 2023-09..2026-10, NY AM / NY PM 2024-10..2026-10, Nov 2025 out.

# Asia: window 202309-202610 (37 months); eligible designs: v0.10 DK10, v0.2.2 DK22MAIN, v0.3 DK3MAIN, v0.4 ratchet-only DK4MAIN, v0.4-ceiling DK4REF, v0.5 bank half, run half DK5, v0.6 ratchet + ABORT DK6, v0.7 bracket + near-target guard DK7, v0.8 DK8, v0.9 DK9; walkable quarters (trailing 12 months with >= 9 window months): 10 of 14 quarters (2024Q3, 2024Q4, 2025Q1, 2025Q2, 2025Q3, 2025Q4, 2026Q1, 2026Q2, 2026Q3, 2026Q4)

## Asia: per-book whole-window table, IN-SAMPLE (each eligible design alone vs the book's own bracket)

| book | design | income (vs bracket) | max DD managed / bracket | worst week managed / bracket | floors 10 / 20 / 30% |
|---|---|---|---|---|---|
| MF1 | v0.2.2 DK22MAIN | -198,618 (-123%) | -222,803 / -111,441 | -31,530 / -50,206 | no / no / no |
| MF1 | v0.3 DK3MAIN | 460,151 (-48%) | -101,818 / -111,441 | -51,433 / -50,206 | no / no / no |
| MF1 | v0.4 ratchet-only DK4MAIN | 89,234 (-90%) | -97,032 / -111,441 | -33,340 / -50,206 | no (smooth) / no (smooth) / no (smooth) |
| MF1 | v0.4-ceiling DK4REF | 83,415 (-91%) | -106,582 / -111,441 | -33,340 / -50,206 | no (smooth) / no (smooth) / no (smooth) |
| MF1 | v0.5 bank half, run half DK5 | 89,129 (-90%) | -101,012 / -111,441 | -33,340 / -50,206 | no (smooth) / no (smooth) / no (smooth) |
| MF1 | v0.6 ratchet + ABORT DK6 | 85,709 (-90%) | -94,717 / -111,441 | -33,340 / -50,206 | no (smooth) / no (smooth) / no (smooth) |
| MF1 | v0.7 bracket + near-target guard DK7 | 340,241 (-61%) | -90,967 / -111,441 | -41,917 / -50,206 | no / no / no |
| MF1 | v0.8 DK8 | 64,569 (-93%) | -104,602 / -111,441 | -33,130 / -50,206 | no (smooth) / no (smooth) / no (smooth) |
| MF1 | v0.9 DK9 | 81,809 (-91%) | -143,428 / -111,441 | -36,221 / -50,206 | no (smooth) / no (smooth) / no (smooth) |
| MF1 | v0.10 DK10 | 114,851 (-87%) | -84,769 / -111,441 | -28,319 / -50,206 | no (smooth) / no (smooth) / no (smooth) |
| MF2 | v0.2.2 DK22MAIN | 74,687 (-82%) | -93,385 / -92,225 | -26,783 / -30,707 | no / no / no |
| MF2 | v0.3 DK3MAIN | 210,720 (-49%) | -112,632 / -92,225 | -32,864 / -30,707 | no / no / no |
| MF2 | v0.4 ratchet-only DK4MAIN | 237,506 (-42%) | -95,808 / -92,225 | -26,596 / -30,707 | no / no / no |
| MF2 | v0.4-ceiling DK4REF | 281,152 (-31%) | -83,578 / -92,225 | -26,596 / -30,707 | no / no / no |
| MF2 | v0.5 bank half, run half DK5 | 263,941 (-36%) | -86,623 / -92,225 | -26,596 / -30,707 | no / no / no |
| MF2 | v0.6 ratchet + ABORT DK6 | 234,166 (-43%) | -95,808 / -92,225 | -26,596 / -30,707 | no / no / no |
| MF2 | v0.7 bracket + near-target guard DK7 | 236,523 (-42%) | -122,965 / -92,225 | -30,404 / -30,707 | no / no / no |
| MF3 | v0.2.2 DK22MAIN | -89,438 (-114%) | -239,545 / -103,232 | -41,929 / -39,659 | no / no / no |
| MF3 | v0.3 DK3MAIN | 332,919 (-48%) | -115,728 / -103,232 | -37,207 / -39,659 | no / no / no |
| MF3 | v0.4 ratchet-only DK4MAIN | 503,631 (-21%) | -113,282 / -103,232 | -55,780 / -39,659 | no / no / no |
| MF3 | v0.4-ceiling DK4REF | 400,477 (-37%) | -101,338 / -103,232 | -48,974 / -39,659 | no / no / no |
| MF3 | v0.5 bank half, run half DK5 | 469,827 (-26%) | -92,707 / -103,232 | -53,735 / -39,659 | no / no / no |
| MF3 | v0.6 ratchet + ABORT DK6 | 503,631 (-21%) | -113,282 / -103,232 | -55,780 / -39,659 | no / no / no |
| MF3 | v0.7 bracket + near-target guard DK7 | 476,015 (-25%) | -94,930 / -103,232 | -46,561 / -39,659 | no / no / no |

## Asia, floor 10%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 598,468 / 728,364 (-18%) | -121,855 / -67,941 | -67,037 / -37,409 | 23,177 / 21,253 | 21,619 / 15,529 | 3 / 2 / 2 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 728,364 / 728,364 (+0%) | -67,941 / -67,941 | -37,409 / -37,409 | 21,253 / 21,253 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: BRACKET x10; MF2: BRACKET x5, v0.4-ceiling DK4REF x2, v0.7 bracket + near-target guard DK7 x1, v0.5 bank half, run half DK5 x1, v0.2.2 DK22MAIN x1; MF3: BRACKET x4, v0.7 bracket + near-target guard DK7 x4, v0.5 bank half, run half DK5 x2
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF3: BRACKET

## Asia, floor 20%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 394,973 / 728,364 (-46%) | -152,983 / -67,941 | -67,037 / -37,409 | 26,704 / 21,253 | 24,714 / 15,529 | 2 / 3 / 3 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 728,364 / 728,364 (+0%) | -67,941 / -67,941 | -37,409 / -37,409 | 21,253 / 21,253 | not computed | not computed | YES / YES / YES |

Picks per book (walked, quarters picked): MF1: BRACKET x8, v0.3 DK3MAIN x2; MF2: BRACKET x5, v0.4-ceiling DK4REF x2, v0.7 bracket + near-target guard DK7 x1, v0.5 bank half, run half DK5 x1, v0.2.2 DK22MAIN x1; MF3: v0.7 bracket + near-target guard DK7 x4, BRACKET x2, v0.5 bank half, run half DK5 x2, v0.4 ratchet-only DK4MAIN x1, v0.4-ceiling DK4REF x1
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF3: BRACKET

## Asia, floor 30%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 233,438 / 728,364 (-68%) | -160,429 / -67,941 | -67,037 / -37,409 | 24,035 / 21,253 | 21,619 / 15,529 | 2 / 3 / 2 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 603,931 / 728,364 (-17%) | -135,949 / -67,941 | -64,191 / -37,409 | 25,456 / 21,253 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF1: BRACKET x7, v0.3 DK3MAIN x3; MF2: BRACKET x4, v0.2.2 DK22MAIN x2, v0.4-ceiling DK4REF x2, v0.7 bracket + near-target guard DK7 x1, v0.5 bank half, run half DK5 x1; MF3: v0.7 bracket + near-target guard DK7 x5, BRACKET x2, v0.5 bank half, run half DK5 x2, v0.4-ceiling DK4REF x1
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF3: v0.5 bank half, run half DK5

# NY AM: window 202410-202610 (24 months); eligible designs: v0.2.2 DK22MAIN, v0.3 DK3MAIN, v0.4 ratchet-only DK4MAIN, v0.4-ceiling DK4REF, v0.5 bank half, run half DK5, v0.6 ratchet + ABORT DK6, v0.7 bracket + near-target guard DK7; walkable quarters (trailing 12 months with >= 9 window months): 6 of 9 quarters (2025Q3, 2025Q4, 2026Q1, 2026Q2, 2026Q3, 2026Q4)

## NY AM: per-book whole-window table, IN-SAMPLE (each eligible design alone vs the book's own bracket)

| book | design | income (vs bracket) | max DD managed / bracket | worst week managed / bracket | floors 10 / 20 / 30% |
|---|---|---|---|---|---|
| MF1 | v0.2.2 DK22MAIN | 622,071 (-51%) | -113,982 / -158,282 | -46,763 / -81,412 | no (smooth) / no (smooth) / no (smooth) |
| MF1 | v0.3 DK3MAIN | 758,672 (-40%) | -136,263 / -158,282 | -64,062 / -81,412 | no / no / no |
| MF1 | v0.4 ratchet-only DK4MAIN | 864,251 (-32%) | -178,982 / -158,282 | -68,385 / -81,412 | no / no / no |
| MF1 | v0.4-ceiling DK4REF | 971,599 (-23%) | -164,535 / -158,282 | -68,385 / -81,412 | no / no / no |
| MF1 | v0.5 bank half, run half DK5 | 768,319 (-39%) | -169,627 / -158,282 | -68,385 / -81,412 | no / no / no |
| MF1 | v0.6 ratchet + ABORT DK6 | 850,757 (-33%) | -178,982 / -158,282 | -68,385 / -81,412 | no / no / no |
| MF1 | v0.7 bracket + near-target guard DK7 | 759,841 (-40%) | -204,279 / -158,282 | -63,486 / -81,412 | no / no / no |
| MF2 | v0.2.2 DK22MAIN | 6,145 (-96%) | -177,004 / -263,422 | -60,375 / -59,825 | no (smooth) / no (smooth) / no (smooth) |
| MF2 | v0.3 DK3MAIN | 6,153 (-96%) | -252,359 / -263,422 | -49,914 / -59,825 | no / no / no |
| MF2 | v0.4 ratchet-only DK4MAIN | -301,186 (-277%) | -353,806 / -263,422 | -70,723 / -59,825 | no / no / no |
| MF2 | v0.4-ceiling DK4REF | -118,782 (-170%) | -251,555 / -263,422 | -56,195 / -59,825 | no / no / no |
| MF2 | v0.5 bank half, run half DK5 | -321,214 (-289%) | -343,624 / -263,422 | -68,033 / -59,825 | no / no / no |
| MF2 | v0.6 ratchet + ABORT DK6 | -301,186 (-277%) | -353,806 / -263,422 | -70,723 / -59,825 | no / no / no |
| MF2 | v0.7 bracket + near-target guard DK7 | 85,197 (-50%) | -287,371 / -263,422 | -63,777 / -59,825 | no / no / no |
| MF4 | v0.2.2 DK22MAIN | 242,885 (-44%) | -145,799 / -199,315 | -89,332 / -73,124 | no / no / no |
| MF4 | v0.3 DK3MAIN | 204,524 (-53%) | -202,867 / -199,315 | -62,974 / -73,124 | no / no / no |
| MF4 | v0.4 ratchet-only DK4MAIN | 253,380 (-41%) | -171,492 / -199,315 | -61,995 / -73,124 | no / no / no |
| MF4 | v0.4-ceiling DK4REF | 295,470 (-32%) | -200,157 / -199,315 | -70,645 / -73,124 | no / no / no |
| MF4 | v0.5 bank half, run half DK5 | 291,816 (-33%) | -157,740 / -199,315 | -54,481 / -73,124 | no / no / no |
| MF4 | v0.6 ratchet + ABORT DK6 | 253,380 (-41%) | -171,492 / -199,315 | -61,995 / -73,124 | no / no / no |
| MF4 | v0.7 bracket + near-target guard DK7 | 408,239 (-6%) | -218,081 / -199,315 | -64,591 / -73,124 | no / no / no |
| MF5 | v0.2.2 DK22MAIN | 45,191 (-82%) | -84,752 / -103,673 | -21,271 / -50,861 | no / no / no |
| MF5 | v0.3 DK3MAIN | 166,326 (-35%) | -91,139 / -103,673 | -34,616 / -50,861 | no / no / no |
| MF5 | v0.4 ratchet-only DK4MAIN | 204,975 (-20%) | -140,141 / -103,673 | -43,523 / -50,861 | no / no / no |
| MF5 | v0.4-ceiling DK4REF | 218,871 (-15%) | -143,969 / -103,673 | -41,523 / -50,861 | no / no / no |
| MF5 | v0.5 bank half, run half DK5 | 199,841 (-22%) | -132,406 / -103,673 | -43,523 / -50,861 | no / no / no |
| MF5 | v0.6 ratchet + ABORT DK6 | 204,975 (-20%) | -140,141 / -103,673 | -43,523 / -50,861 | no / no / no |
| MF5 | v0.7 bracket + near-target guard DK7 | 297,756 (+16%) | -102,212 / -103,673 | -47,174 / -50,861 | no / no / no |

## NY AM, floor 10%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 933,486 / 1,959,030 (-52%) | -215,189 / -163,622 | -66,934 / -97,182 | 49,970 / 57,307 | 48,854 / 28,899 | 2 / 1 / 0 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 1,939,351 / 1,959,030 (-1%) | -165,876 / -163,622 | -93,446 / -97,182 | 57,059 / 57,307 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF1: v0.2.2 DK22MAIN x3, BRACKET x2, v0.5 bank half, run half DK5 x1; MF2: BRACKET x3, v0.2.2 DK22MAIN x3; MF4: v0.5 bank half, run half DK5 x3, BRACKET x2, v0.7 bracket + near-target guard DK7 x1; MF5: v0.7 bracket + near-target guard DK7 x3, v0.4-ceiling DK4REF x2, BRACKET x1
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF4: BRACKET, MF5: v0.7 bracket + near-target guard DK7

## NY AM, floor 20%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 933,486 / 1,959,030 (-52%) | -215,189 / -163,622 | -66,934 / -97,182 | 49,970 / 57,307 | 48,854 / 28,899 | 2 / 1 / 0 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 1,939,351 / 1,959,030 (-1%) | -165,876 / -163,622 | -93,446 / -97,182 | 57,059 / 57,307 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF1: v0.2.2 DK22MAIN x3, BRACKET x2, v0.5 bank half, run half DK5 x1; MF2: BRACKET x3, v0.2.2 DK22MAIN x3; MF4: v0.5 bank half, run half DK5 x3, BRACKET x2, v0.7 bracket + near-target guard DK7 x1; MF5: v0.7 bracket + near-target guard DK7 x3, v0.4-ceiling DK4REF x2, BRACKET x1
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF4: BRACKET, MF5: v0.7 bracket + near-target guard DK7

## NY AM, floor 30%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 659,424 / 1,959,030 (-66%) | -215,189 / -163,622 | -70,352 / -97,182 | 44,933 / 57,307 | 48,854 / 28,899 | 2 / 1 / 0 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 1,939,351 / 1,959,030 (-1%) | -165,876 / -163,622 | -93,446 / -97,182 | 57,059 / 57,307 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF1: v0.2.2 DK22MAIN x3, v0.5 bank half, run half DK5 x1, v0.4 ratchet-only DK4MAIN x1, v0.4-ceiling DK4REF x1; MF2: BRACKET x3, v0.2.2 DK22MAIN x3; MF4: v0.5 bank half, run half DK5 x3, BRACKET x2, v0.7 bracket + near-target guard DK7 x1; MF5: v0.4-ceiling DK4REF x2, v0.7 bracket + near-target guard DK7 x2, BRACKET x1, v0.3 DK3MAIN x1
IN-SAMPLE whole-window picks: MF1: BRACKET, MF2: BRACKET, MF4: BRACKET, MF5: v0.7 bracket + near-target guard DK7

# London: window 202309-202610 (37 months); eligible designs: v0.2.2 DK22MAIN, v0.3 DK3MAIN, v0.4 ratchet-only DK4MAIN, v0.4-ceiling DK4REF, v0.5 bank half, run half DK5, v0.6 ratchet + ABORT DK6, v0.7 bracket + near-target guard DK7; walkable quarters (trailing 12 months with >= 9 window months): 10 of 14 quarters (2024Q3, 2024Q4, 2025Q1, 2025Q2, 2025Q3, 2025Q4, 2026Q1, 2026Q2, 2026Q3, 2026Q4)

## London: per-book whole-window table, IN-SAMPLE (each eligible design alone vs the book's own bracket)

| book | design | income (vs bracket) | max DD managed / bracket | worst week managed / bracket | floors 10 / 20 / 30% |
|---|---|---|---|---|---|
| MF1 | v0.2.2 DK22MAIN | 198,554 (-61%) | -213,104 / -107,192 | -40,155 / -52,798 | no / no / no |
| MF1 | v0.3 DK3MAIN | 222,264 (-56%) | -156,679 / -107,192 | -36,382 / -52,798 | no / no / no |
| MF1 | v0.4 ratchet-only DK4MAIN | 336,401 (-34%) | -238,574 / -107,192 | -61,368 / -52,798 | no / no / no |
| MF1 | v0.4-ceiling DK4REF | 505,442 (-1%) | -103,322 / -107,192 | -46,887 / -52,798 | no / no / no |
| MF1 | v0.5 bank half, run half DK5 | 424,262 (-17%) | -150,243 / -107,192 | -55,033 / -52,798 | no / no / no |
| MF1 | v0.6 ratchet + ABORT DK6 | 319,553 (-37%) | -255,421 / -107,192 | -61,368 / -52,798 | no / no / no |
| MF1 | v0.7 bracket + near-target guard DK7 | 350,922 (-31%) | -176,966 / -107,192 | -51,855 / -52,798 | no / no / no |
| MF3 | v0.2.2 DK22MAIN | -98,813 (-153%) | -153,491 / -47,177 | -13,866 / -23,120 | no / no / no |
| MF3 | v0.3 DK3MAIN | 41,819 (-77%) | -47,513 / -47,177 | -16,070 / -23,120 | no / no / no |
| MF3 | v0.4 ratchet-only DK4MAIN | 117,749 (-36%) | -68,905 / -47,177 | -27,550 / -23,120 | no / no / no |
| MF3 | v0.4-ceiling DK4REF | 193,150 (+4%) | -54,519 / -47,177 | -23,030 / -23,120 | no / no / no |
| MF3 | v0.5 bank half, run half DK5 | 117,814 (-36%) | -64,812 / -47,177 | -27,395 / -23,120 | no / no / no |
| MF3 | v0.6 ratchet + ABORT DK6 | 120,702 (-35%) | -68,727 / -47,177 | -27,550 / -23,120 | no / no / no |
| MF3 | v0.7 bracket + near-target guard DK7 | 39,935 (-78%) | -90,945 / -47,177 | -27,950 / -23,120 | no / no / no |

## London, floor 10%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 378,557 / 586,760 (-35%) | -234,898 / -224,333 | -106,752 / -107,350 | 25,092 / 26,066 | 19,414 / 19,919 | 2 / 5 / 4 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 595,751 / 586,760 (+2%) | -226,508 / -224,333 | -102,647 / -107,350 | 25,904 / 26,066 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF1: v0.5 bank half, run half DK5 x3, v0.4-ceiling DK4REF x3, BRACKET x2, v0.2.2 DK22MAIN x2; MF3: BRACKET x7, v0.4-ceiling DK4REF x2, v0.3 DK3MAIN x1
IN-SAMPLE whole-window picks: MF1: v0.4-ceiling DK4REF, MF3: BRACKET

## London, floor 20%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 482,313 / 586,760 (-18%) | -234,898 / -224,333 | -106,752 / -107,350 | 25,443 / 26,066 | 19,639 / 19,919 | 2 / 5 / 5 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 595,751 / 586,760 (+2%) | -226,508 / -224,333 | -102,647 / -107,350 | 25,904 / 26,066 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF1: v0.5 bank half, run half DK5 x4, v0.4-ceiling DK4REF x3, BRACKET x2, v0.2.2 DK22MAIN x1; MF3: BRACKET x7, v0.4-ceiling DK4REF x2, v0.3 DK3MAIN x1
IN-SAMPLE whole-window picks: MF1: v0.4-ceiling DK4REF, MF3: BRACKET

## London, floor 30%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 10 walked quarters (202407-202610 (27 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 10) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 354,181 / 586,760 (-40%) | -255,780 / -224,333 | -106,752 / -107,350 | 25,106 / 26,066 | 19,414 / 19,919 | 3 / 5 / 2 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 595,751 / 586,760 (+2%) | -226,508 / -224,333 | -102,647 / -107,350 | 25,904 / 26,066 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF1: BRACKET x2, v0.5 bank half, run half DK5 x2, v0.4-ceiling DK4REF x2, v0.3 DK3MAIN x2, v0.7 bracket + near-target guard DK7 x1, v0.2.2 DK22MAIN x1; MF3: BRACKET x7, v0.4-ceiling DK4REF x2, v0.3 DK3MAIN x1
IN-SAMPLE whole-window picks: MF1: v0.4-ceiling DK4REF, MF3: BRACKET

# NY PM: window 202410-202610 (24 months); eligible designs: v0.2.2 DK22MAIN, v0.3 DK3MAIN, v0.4 ratchet-only DK4MAIN, v0.4-ceiling DK4REF, v0.5 bank half, run half DK5, v0.6 ratchet + ABORT DK6, v0.7 bracket + near-target guard DK7; walkable quarters (trailing 12 months with >= 9 window months): 6 of 9 quarters (2025Q3, 2025Q4, 2026Q1, 2026Q2, 2026Q3, 2026Q4)

## NY PM: per-book whole-window table, IN-SAMPLE (each eligible design alone vs the book's own bracket)

| book | design | income (vs bracket) | max DD managed / bracket | worst week managed / bracket | floors 10 / 20 / 30% |
|---|---|---|---|---|---|
| MF2 | v0.2.2 DK22MAIN | -36,355 (-115%) | -113,521 / -165,629 | -23,729 / -41,926 | no (smooth) / no (smooth) / no (smooth) |
| MF2 | v0.3 DK3MAIN | 70,585 (-70%) | -86,179 / -165,629 | -29,665 / -41,926 | no (smooth) / no (smooth) / no (smooth) |
| MF2 | v0.4 ratchet-only DK4MAIN | 392,175 (+67%) | -134,559 / -165,629 | -43,148 / -41,926 | no / no / no |
| MF2 | v0.4-ceiling DK4REF | 274,861 (+17%) | -156,572 / -165,629 | -43,148 / -41,926 | no / no / no |
| MF2 | v0.5 bank half, run half DK5 | 353,325 (+50%) | -140,869 / -165,629 | -43,148 / -41,926 | no / no / no |
| MF2 | v0.6 ratchet + ABORT DK6 | 386,555 (+64%) | -134,559 / -165,629 | -43,148 / -41,926 | no / no / no |
| MF2 | v0.7 bracket + near-target guard DK7 | 113,645 (-52%) | -167,293 / -165,629 | -41,926 / -41,926 | no / no / no |
| MF3 | v0.2.2 DK22MAIN | 52,793 (-87%) | -106,151 / -75,125 | -28,499 / -28,888 | no / no / no |
| MF3 | v0.3 DK3MAIN | 221,462 (-47%) | -70,389 / -75,125 | -29,739 / -28,888 | no / no / no |
| MF3 | v0.4 ratchet-only DK4MAIN | 512,234 (+23%) | -75,185 / -75,125 | -30,643 / -28,888 | no / no / no |
| MF3 | v0.4-ceiling DK4REF | 412,114 (-1%) | -67,280 / -75,125 | -30,263 / -28,888 | no / no / no |
| MF3 | v0.5 bank half, run half DK5 | 460,498 (+11%) | -67,275 / -75,125 | -31,734 / -28,888 | no / no / no |
| MF3 | v0.6 ratchet + ABORT DK6 | 512,234 (+23%) | -75,185 / -75,125 | -30,643 / -28,888 | no / no / no |
| MF3 | v0.7 bracket + near-target guard DK7 | 364,881 (-12%) | -67,969 / -75,125 | -30,263 / -28,888 | no / no / no |

## NY PM, floor 10%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 434,816 / 429,095 (+1%) | -60,099 / -88,173 | -50,645 / -44,139 | 22,329 / 18,237 | 27,954 / 27,954 | 0 / 3 / 3 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 623,708 / 429,095 (+45%) | -63,739 / -88,173 | -54,285 / -44,139 | 26,486 / 18,237 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF2: v0.3 DK3MAIN x3, v0.4-ceiling DK4REF x2, BRACKET x1; MF3: v0.5 bank half, run half DK5 x4, BRACKET x1, v0.4-ceiling DK4REF x1
IN-SAMPLE whole-window picks: MF2: v0.4 ratchet-only DK4MAIN, MF3: v0.5 bank half, run half DK5

## NY PM, floor 20%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 435,115 / 429,095 (+1%) | -72,406 / -88,173 | -50,645 / -44,139 | 22,379 / 18,237 | 27,954 / 27,954 | 0 / 3 / 3 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 623,708 / 429,095 (+45%) | -63,739 / -88,173 | -54,285 / -44,139 | 26,486 / 18,237 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF2: v0.3 DK3MAIN x3, v0.4-ceiling DK4REF x2, BRACKET x1; MF3: v0.5 bank half, run half DK5 x3, v0.7 bracket + near-target guard DK7 x1, BRACKET x1, v0.4-ceiling DK4REF x1
IN-SAMPLE whole-window picks: MF2: v0.4 ratchet-only DK4MAIN, MF3: v0.5 bank half, run half DK5

## NY PM, floor 30%: WALKED-FORWARD session mix (trailing-12-month picks) vs live mix as run, on the 6 walked quarters (202507-202610 (15 months))

| view | income managed / live (change) | max DD managed / live | worst week managed / live | weekly st.dev. managed / live | largest single give-back (picked designs / bracket books) | quarters better: smoother / shallower DD / more income (of 6) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|
| **WALKED-FORWARD** | 401,902 / 429,095 (-6%) | -66,212 / -88,173 | -60,135 / -44,139 | 22,577 / 18,237 | 27,954 / 27,954 | 0 / 2 / 3 | no / no / no |
| IN-SAMPLE best-per-book (same days) | 623,708 / 429,095 (+45%) | -63,739 / -88,173 | -54,285 / -44,139 | 26,486 / 18,237 | not computed | not computed | no / no / no |

Picks per book (walked, quarters picked): MF2: v0.3 DK3MAIN x3, v0.4-ceiling DK4REF x1, v0.5 bank half, run half DK5 x1, BRACKET x1; MF3: v0.7 bracket + near-target guard DK7 x2, v0.5 bank half, run half DK5 x2, BRACKET x1, v0.4-ceiling DK4REF x1
IN-SAMPLE whole-window picks: MF2: v0.4 ratchet-only DK4MAIN, MF3: v0.5 bank half, run half DK5

