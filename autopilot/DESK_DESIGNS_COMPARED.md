# DESK_DESIGNS_COMPARED (generated 2026-11-28 13:56Z by code/th_algo/ar_designs.py; order 1408Z; research only)

One table of manager designs, same windows, same like-with-like references. Window per session = the months the DK22 sets have (Asia / London 37 months 2023-09..2026-10, NY AM / NY PM 24 months 2024-10..2026-10, Nov 2025 out); every design is cut to those months and the reference (the live mix as run for the mix rows, the book on its fixed bracket for alone rows) is cut to the same months and weeks. SESSION MIX row = live mix + sum of the per-book deltas of the books that design has finished (post-hoc additive, interaction neglected); books a design has not finished for the whole window are listed as not complete and left out. Floors: ACCEPTABLE = smoother (worst week not worse AND weekly st.dev. not larger) in >= 2/3 of quarters overall AND in NQ-up AND in NQ-down weeks, and income not more than 10 / 20 / 30% below the bracket; shown as YES / no (smooth = smoothness passed, income failed) / no. Give-backs: peak open profit from best_px in the trade rows (tape where the column is absent, marked), $ minus realised p484; largest single trade and the count of trades that gave back more than half of a peak of at least $500; managed = the managed books' own trades, bracket = the same books on the fixed bracket (fix_A, tape). Designs are read from code/th_algo/desk_designs.json (first tag with rows wins) and rows appear as the sets finish; the best single landscape code per book is the _M set named in autopilot/SUNDAY_LANDSCAPE.md.

DK4..DK9 set families found in runs_rf: none yet

# Asia: window 202309-202610 (37 months)

## Asia: SESSION MIX

| design | books in the mix / not complete | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1, MF2, MF3 | -233,607 (-126%) | -308,325 / -67,941 | -44,293 / -37,409 | 10,045 / 18,895 | 35,774 / 15,529 | 1649 / 2345 | 11/14, 8/11, 6/12 | no / no / no |
| v0.3 (DK3 main) | MF1, MF2, MF3 | 399,861 (-55%) | -120,551 / -67,941 | -35,127 / -37,409 | 13,100 / 18,895 | 14,099 / 15,529 | 1976 / 2345 | 11/14, 9/11, 6/12 | no / no / no |
| v0.4 ratchet-only | none complete | not run yet |||||||| 
| v0.4-ceiling (own target as ceiling) | none complete | not run yet |||||||| 
| v0.5 bank half, run half | none complete | not run yet |||||||| 
| v0.6 ratchet + ABORT | none complete | not run yet |||||||| 
| v0.7 bracket + near-target guard (pl70k50) | MF1, MF2, MF3 | 818,847 (-8%) | -80,221 / -67,941 | -41,374 / -37,409 | 19,594 / 18,895 | 11,624 / 15,529 | 2125 / 2345 | 5/14, 5/11, 5/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF2 so0, MF3 x7) | MF1, MF2, MF3 | 912,321 (+2%) | -89,603 / -67,941 | -39,207 / -37,409 | 20,610 / 18,895 | 19,244 / 15,529 | 2116 / 2345 | 5/14, 4/11, 4/12 | no / no / no |

## Asia: PER BOOK

| design | book (row type) | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1 (alone) | -198,618 (-123%) | -222,803 / -111,441 | -31,530 / -50,206 | 8,689 / 20,523 | 16,079 / 14,634 | 473 / 1054 | 11/14, 8/11, 7/12 | no / no / no |
| v0.2.2 (DK22 main) | MF2 (alone) | 74,687 (-82%) | -93,385 / -92,225 | -26,783 / -30,707 | 5,950 / 10,772 | 18,079 / 15,529 | 165 / 280 | 9/14, 7/11, 6/12 | no / no / no |
| v0.2.2 (DK22 main) | MF3 (alone) | -89,438 (-114%) | -239,545 / -103,232 | -41,929 / -39,659 | 11,983 / 16,561 | 35,774 / 12,119 | 1011 / 1011 | 10/14, 7/11, 10/12 | no / no / no |
| v0.3 (DK3 main) | MF1 (alone) | 460,151 (-48%) | -101,818 / -111,441 | -51,433 / -50,206 | 16,042 / 20,523 | 13,839 / 14,634 | 588 / 1054 | 10/14, 7/11, 6/12 | no / no / no |
| v0.3 (DK3 main) | MF2 (alone) | 210,720 (-49%) | -112,632 / -92,225 | -32,864 / -30,707 | 9,433 / 10,772 | 14,099 / 15,529 | 254 / 280 | 9/14, 6/11, 7/12 | no / no / no |
| v0.3 (DK3 main) | MF3 (alone) | 332,919 (-48%) | -115,728 / -103,232 | -37,207 / -39,659 | 15,138 / 16,561 | 10,899 / 12,119 | 1134 / 1011 | 9/14, 6/11, 8/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1 (in mix) | 751,073 (-16%) | -85,430 / -67,941 | -39,424 / -37,409 | 18,489 / 18,895 | 11,519 / 14,634 | 886 / 1054 | 6/14, 8/11, 4/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF2 (in mix) | 893,889 (+0%) | -72,921 / -67,941 | -37,409 / -37,409 | 18,673 / 18,895 | 11,624 / 15,529 | 269 / 280 | 8/14, 5/11, 9/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF3 (in mix) | 961,227 (+8%) | -79,933 / -67,941 | -37,905 / -37,409 | 20,256 / 18,895 | 9,299 / 12,119 | 970 / 1011 | 3/14, 3/11, 5/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF2 so0, MF3 x7) | MF1 (in mix) | 848,019 (-5%) | -79,568 / -67,941 | -39,838 / -37,409 | 18,453 / 18,895 | 9,229 / 14,634 | 990 / 1054 | 6/14, 4/11, 4/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF2 so0, MF3 x7) | MF2 (in mix) | 858,715 (-4%) | -71,310 / -67,941 | -37,409 / -37,409 | 19,562 / 18,895 | 19,244 / 15,529 | 286 / 280 | 6/14, 4/11, 8/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF2 so0, MF3 x7) | MF3 (in mix) | 992,929 (+11%) | -65,426 / -67,941 | -36,778 / -37,409 | 20,533 / 18,895 | 11,440 / 12,119 | 840 / 1011 | 7/14, 4/11, 7/12 | no / no / no |

# NY AM: window 202410-202610 (24 months)

## NY AM: SESSION MIX

| design | books in the mix / not complete | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1, MF2, MF4, MF5 | 1,683,301 (-41%) | -130,615 / -163,622 | -64,328 / -110,130 | 37,994 / 54,746 | 29,234 / 29,179 | 3019 / 2433 | 4/9, 3/7, 4/7 | no / no / no |
| v0.3 (DK3 main) | MF1, MF2, MF4, MF5 | 2,177,072 (-24%) | -166,714 / -163,622 | -88,687 / -110,130 | 44,961 / 54,746 | 27,254 / 29,179 | 3039 / 2433 | 6/9, 2/7, 5/7 | no / no / no |
| v0.4 ratchet-only | none complete | not run yet |||||||| 
| v0.4-ceiling (own target as ceiling) | none complete | not run yet |||||||| 
| v0.5 bank half, run half | none complete | not run yet |||||||| 
| v0.6 ratchet + ABORT | none complete | not run yet |||||||| 
| v0.7 bracket + near-target guard (pl70k50) | MF1, MF2, MF4, MF5 | 2,003,756 (-30%) | -321,834 / -163,622 | -140,939 / -110,130 | 51,259 / 54,746 | 24,269 / 29,179 (tape) | 2552 / 2433 | 3/9, 4/7, 3/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF1, MF2, MF4, MF5 | 2,634,979 (-7%) | -160,142 / -163,622 | -107,874 / -110,130 | 46,092 / 54,746 | 18,624 / 29,179 | 2485 / 2433 | 5/9, 4/7, 4/7 | no / no / no |

## NY AM: PER BOOK

| design | book (row type) | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1 (alone) | 622,071 (-51%) | -113,982 / -158,282 | -46,763 / -81,412 | 26,565 / 38,170 | 26,764 / 29,179 | 779 / 543 | 7/9, 5/7, 5/7 | no (smooth) / no (smooth) / no (smooth) |
| v0.2.2 (DK22 main) | MF2 (alone) | 6,145 (-96%) | -177,004 / -263,422 | -60,375 / -59,825 | 17,091 / 23,724 | 25,944 / 15,369 | 713 / 629 | 6/9, 5/7, 5/7 | no (smooth) / no (smooth) / no (smooth) |
| v0.2.2 (DK22 main) | MF4 (alone) | 242,885 (-44%) | -145,799 / -199,315 | -89,332 / -73,124 | 24,565 / 28,083 | 29,234 / 16,454 | 843 / 549 | 5/9, 4/7, 4/7 | no / no / no |
| v0.2.2 (DK22 main) | MF5 (alone) | 45,191 (-82%) | -84,752 / -103,673 | -21,271 / -50,861 | 8,705 / 13,987 | 12,960 / 8,125 | 684 / 712 | 6/9, 3/7, 4/7 | no / no / no |
| v0.3 (DK3 main) | MF1 (alone) | 758,672 (-40%) | -136,263 / -158,282 | -64,062 / -81,412 | 28,463 / 38,170 | 27,254 / 29,179 | 640 / 543 | 5/9, 5/7, 3/7 | no / no / no |
| v0.3 (DK3 main) | MF2 (alone) | 6,153 (-96%) | -252,359 / -263,422 | -49,914 / -59,825 | 21,275 / 23,724 | 14,354 / 15,369 | 745 / 629 | 4/9, 3/7, 3/7 | no / no / no |
| v0.3 (DK3 main) | MF4 (alone) | 204,524 (-53%) | -202,867 / -199,315 | -62,974 / -73,124 | 24,182 / 28,083 | 14,544 / 16,454 | 814 / 549 | 5/9, 2/7, 6/7 | no / no / no |
| v0.3 (DK3 main) | MF5 (alone) | 166,326 (-35%) | -91,139 / -103,673 | -34,616 / -50,861 | 11,744 / 13,987 | 7,125 / 8,125 | 840 / 712 | 7/9, 3/7, 4/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1 (in mix) | 2,387,684 (-16%) | -228,327 / -163,622 | -110,130 / -110,130 | 51,815 / 54,746 | 24,269 / 29,179 (tape) | 629 / 543 | 4/9, 2/7, 4/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF2 (in mix) | 2,631,022 (-8%) | -159,918 / -163,622 | -123,574 / -110,130 | 54,520 / 54,746 | 12,259 / 15,369 | 573 / 629 | 4/9, 5/7, 3/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF4 (in mix) | 2,712,942 (-5%) | -163,325 / -163,622 | -112,046 / -110,130 | 54,053 / 54,746 | 13,189 / 16,454 | 748 / 549 | 3/9, 5/7, 3/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF5 (in mix) | 2,814,091 (-1%) | -178,168 / -163,622 | -101,238 / -110,130 | 54,724 / 54,746 | 6,100 / 8,125 | 602 / 712 | 4/9, 1/7, 6/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF1 (in mix) | 2,920,493 (+3%) | -148,601 / -163,622 | -103,227 / -110,130 | 51,954 / 54,746 | 18,624 / 29,179 | 504 / 543 | 6/9, 3/7, 4/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF2 (in mix) | 2,554,880 (-10%) | -167,136 / -163,622 | -104,639 / -110,130 | 50,928 / 54,746 | 10,724 / 15,369 | 1053 / 629 | 3/9, 1/7, 2/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF4 (in mix) | 2,850,996 (+0%) | -158,564 / -163,622 | -118,756 / -110,130 | 52,064 / 54,746 | 13,189 / 16,454 | 389 / 549 | 4/9, 3/7, 5/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF5 (in mix) | 2,850,593 (+0%) | -167,262 / -163,622 | -100,355 / -110,130 | 54,321 / 54,746 | 6,100 / 8,125 | 539 / 712 | 3/9, 2/7, 5/7 | no / no / no |

# London: window 202309-202610 (37 months)

## London: SESSION MIX

| design | books in the mix / not complete | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1, MF3 | 284,800 (-68%) | -336,126 / -224,333 | -82,790 / -107,350 | 19,661 / 23,472 | 22,529 / 19,919 | 1484 / 923 | 6/14, 5/11, 4/12 | no / no / no |
| v0.3 (DK3 main) | MF1, MF3 | 449,142 (-49%) | -274,932 / -224,333 | -67,484 / -107,350 | 19,410 / 23,472 | 17,239 / 19,919 | 1398 / 923 | 6/14, 2/11, 4/12 | no / no / no |
| v0.4 ratchet-only | none complete | not run yet |||||||| 
| v0.4-ceiling (own target as ceiling) | none complete | not run yet |||||||| 
| v0.5 bank half, run half | none complete | not run yet |||||||| 
| v0.6 ratchet + ABORT | none complete | not run yet |||||||| 
| v0.7 bracket + near-target guard (pl70k50) | MF1, MF3 | 464,563 (-47%) | -295,676 / -224,333 | -106,029 / -107,350 | 22,902 / 23,472 | 17,824 / 19,919 | 1426 / 923 | 7/14, 4/11, 4/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF3 so0) | MF1, MF3 | 778,909 (-12%) | -319,212 / -224,333 | -76,627 / -107,350 | 25,852 / 23,472 | 20,265 / 19,919 | 999 / 923 | 3/14, 2/11, 3/12 | no / no / no |

## London: PER BOOK

| design | book (row type) | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1 (alone) | 198,554 (-61%) | -213,104 / -107,192 | -40,155 / -52,798 | 12,176 / 16,123 | 22,529 / 19,919 | 548 / 321 | 9/14, 7/11, 7/12 | no / no / no |
| v0.2.2 (DK22 main) | MF3 (alone) | -98,813 (-153%) | -153,491 / -47,177 | -13,866 / -23,120 | 4,755 / 6,993 | 8,310 / 7,190 | 936 / 602 | 8/14, 6/11, 7/12 | no / no / no |
| v0.3 (DK3 main) | MF1 (alone) | 222,264 (-56%) | -156,679 / -107,192 | -36,382 / -52,798 | 11,948 / 16,123 | 17,239 / 19,919 | 531 / 321 | 9/14, 7/11, 7/12 | no / no / no |
| v0.3 (DK3 main) | MF3 (alone) | 41,819 (-77%) | -47,513 / -47,177 | -16,070 / -23,120 | 5,809 / 6,993 | 6,755 / 7,190 | 867 / 602 | 7/14, 4/11, 4/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1 (in mix) | 671,720 (-24%) | -252,604 / -224,333 | -110,021 / -107,350 | 22,497 / 23,472 | 17,824 / 19,919 | 592 / 321 | 7/14, 4/11, 5/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF3 (in mix) | 673,899 (-24%) | -267,386 / -224,333 | -103,358 / -107,350 | 23,904 / 23,472 | 6,415 / 7,190 | 834 / 602 | 5/14, 3/11, 4/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF3 so0) | MF1 (in mix) | 784,656 (-11%) | -371,371 / -224,333 | -71,741 / -107,350 | 26,303 / 23,472 | 16,919 / 19,919 | 504 / 321 | 5/14, 1/11, 4/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF3 so0) | MF3 (in mix) | 875,308 (-1%) | -193,751 / -224,333 | -111,154 / -107,350 | 23,561 / 23,472 | 20,265 / 7,190 | 495 / 602 | 3/14, 6/11, 2/12 | no / no / no |

# NY PM: window 202410-202610 (24 months)

## NY PM: SESSION MIX

| design | books in the mix / not complete | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF2, MF3 | 158,436 (-76%) | -110,164 / -134,363 | -42,993 / -44,139 | 16,414 / 20,021 | 24,499 / 28,539 | 744 / 454 | 6/9, 6/7, 1/7 | no / no / no |
| v0.3 (DK3 main) | MF2, MF3 | 422,023 (-36%) | -112,257 / -134,363 | -35,926 / -44,139 | 18,062 / 20,021 | 25,779 / 28,539 | 678 / 454 | 6/9, 5/7, 2/7 | no / no / no |
| v0.4 ratchet-only | none complete | not run yet |||||||| 
| v0.4-ceiling (own target as ceiling) | none complete | not run yet |||||||| 
| v0.5 bank half, run half | none complete | not run yet |||||||| 
| v0.6 ratchet + ABORT | none complete | not run yet |||||||| 
| v0.7 bracket + near-target guard (pl70k50) | MF2, MF3 | 581,840 (-12%) | -121,704 / -134,363 | -45,699 / -44,139 | 19,018 / 20,021 | 19,520 / 28,539 | 416 / 454 | 2/9, 0/7, 4/7 | no / no / no |
| best single landscape code per book (MF2 xi15all, MF3 x7) | MF2, MF3 | 543,807 (-17%) | -79,217 / -134,363 | -47,044 / -44,139 | 19,579 / 20,021 | 18,575 / 28,539 | 336 / 454 | 3/9, 0/7, 3/7 | no / no / no |

## NY PM: PER BOOK

| design | book (row type) | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF2 (alone) | -36,355 (-115%) | -113,521 / -165,629 | -23,729 / -41,926 | 8,485 / 18,229 | 24,499 / 28,539 | 357 / 239 | 8/9, 7/7, 6/7 | no (smooth) / no (smooth) / no (smooth) |
| v0.2.2 (DK22 main) | MF3 (alone) | 52,793 (-87%) | -106,151 / -75,125 | -28,499 / -28,888 | 8,526 / 14,432 | 18,829 / 14,494 | 387 / 215 | 6/9, 4/7, 3/7 | no / no / no |
| v0.3 (DK3 main) | MF2 (alone) | 70,585 (-70%) | -86,179 / -165,629 | -29,665 / -41,926 | 12,631 / 18,229 | 25,779 / 28,539 | 309 / 239 | 7/9, 6/7, 5/7 | no (smooth) / no (smooth) / no (smooth) |
| v0.3 (DK3 main) | MF3 (alone) | 221,462 (-47%) | -70,389 / -75,125 | -29,739 / -28,888 | 10,095 / 14,432 | 14,044 / 14,494 | 369 / 215 | 6/9, 4/7, 3/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF2 (in mix) | 676,560 (+3%) | -133,938 / -134,363 | -44,139 / -44,139 | 19,520 / 20,021 | 19,520 / 28,539 | 193 / 239 | 3/9, 1/7, 5/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF3 (in mix) | 563,335 (-14%) | -122,129 / -134,363 | -45,699 / -44,139 | 19,655 / 20,021 | 12,384 / 14,494 | 223 / 215 | 2/9, 0/7, 3/7 | no / no / no |
| best single landscape code per book (MF2 xi15all, MF3 x7) | MF2 (in mix) | 633,457 (-4%) | -94,366 / -134,363 | -44,139 / -44,139 | 19,669 / 20,021 | 18,575 / 28,539 | 191 / 239 | 1/9, 1/7, 3/7 | no / no / no |
| best single landscape code per book (MF2 xi15all, MF3 x7) | MF3 (in mix) | 568,406 (-14%) | -103,870 / -134,363 | -47,239 / -44,139 | 20,271 / 20,021 | 12,119 / 14,494 | 145 / 215 | 1/9, 0/7, 3/7 | no / no / no |

