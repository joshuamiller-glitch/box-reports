# DS3_NEAR_TARGET - W-NT near-target take that catches a touch-and-reverse (user relay 11-18 01:25Z) 

Generated 2026-11-19 09:21Z. Data end 2026-11-13 (JL3 months 202304..202611, 44 months, exact engine TL3_EV_JL3 trades + 1-s tape p_high/p_low/mid). Pick window (trailing 6M) 2026-05-14..2026-11-13, 3M beside 2026-08-14..2026-11-13; refit date 2026-11-22 (2-week roll); prior-year percentages to follow with the engine rows (this page version = COUNT TABLE only, no selection yet, no trials counted). Standing selection rule applies to every pick below. The earlier near-target page (user order 17:25Z, first-order screen on LPB_BASE) is kept at the bottom and in autopilot/DS3_NEAR_TARGET_1725Z_prev.md.

## Five lines
1. Tried: counted, per book x session, the JL3 trades whose 1-s print extreme reached 85/90/95/97.5/100% of the target without a Target fill, and how they ended (live take, live lock, other exit).
2. Holds: in the JL3 engine the live per-print take lines (K7 P7 M7 0.95/5, U7 A7 0.983/5, H7 0.9875/30, O7 0.975/5) and persist=1 locks end almost all trades that reach 97.5% (see live-line share column); the residue the lines do NOT catch is small in count but costly: see the unprotected columns.
3. Does not hold: the touch-and-reverse (price inside the band for less than the 5 s the line needs) is only caught by chance; K7 and M7 have no simple lock; K7/M7/U7 persist>=2 lines are dead (counter bug L1790).
4. DS7 needs: simple lock lines and target shave are POLICY FILE only; a latched near-target take (new latch grammar) is NEW CODE; the persist counter fix is a one-line code change (L1790).
5. Next: first-order screen of the latch / lock / shave families on these paths, then a small engine batch under TL3_NT_ (queue file /mnt/l2/l2vast/_nt/pending.txt).

## 1. COUNT TABLE (JL3 engine trades, base lots, $ = gross price dollars, fees extra: $4.84 RT/contract; x1.75 column = live-lot rounding)
Definitions. reached X = the favourable 1-s print extreme (p_high long, p_low short) between entry and exit was >= X x target distance (60 pts, O7 90). target later = the trade ended with a Target fill. not filled = ended any other way. exit = live take / live lock = JL3 exits named PolicyTake / PolicyTrail (the live persist=1 lines modelled in JL3). unprotected = not filled and not exited by a take/lock (state cut, early cut, stop, stack cut, time block, book lock...). $ left vs target = (target - realised pts) x 20 x lots over all not-filled trades. $ given back vs take at X = what a perfect take at X x target would have added over the unprotected exits.
Caveat: the engine take is modelled on the same prints/seconds as the live line; a fast touch that never satisfies pct>=P and secs_ext>=s together at one evaluation is missed in the engine as in live (these are the unprotected rows). The engine bracket target is 60 for every book (live K7 59 / P7 58 / M7 59.5 only change the pct denominator of the lines).

### Book x session, last 6 months, reached >= 95.0% of target
| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 381 | 158 | 137 | 21 | 16 | 0 | 5 | 5 | 5 | 10,836 | 10,051 | 20,103 | 76% |
| H7 | asia | 144 | 19 | 15 | 4 | 0 | 4 | 0 | 0 | 0 | 2,512 | 0 | 0 | 100% |
| H7 | nyam | 38 | 7 | 6 | 1 | 0 | 1 | 0 | 0 | 0 | 315 | 0 | 0 | 100% |
| K7 | asia | 858 | 309 | 134 | 175 | 171 | 0 | 4 | 4 | 4 | 22,455 | 7,380 | 14,761 | 98% |
| K7 | london | 470 | 151 | 60 | 91 | 83 | 0 | 8 | 7 | 7 | 26,040 | 18,580 | 37,161 | 91% |
| K7 | nyam | 194 | 62 | 34 | 28 | 28 | 0 | 0 | 0 | 0 | 2,215 | 0 | 0 | 100% |
| K7 | nypm | 166 | 59 | 37 | 22 | 21 | 0 | 1 | 1 | 1 | 3,843 | 2,063 | 4,127 | 95% |
| M7 | london | 528 | 162 | 82 | 80 | 73 | 0 | 7 | 7 | 7 | 24,972 | 19,037 | 38,075 | 91% |
| M7 | nyam | 231 | 86 | 49 | 37 | 33 | 0 | 4 | 4 | 4 | 9,884 | 7,484 | 14,968 | 89% |
| O7 | nyam | 46 | 13 | 13 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0% |
| P7 | asia | 610 | 144 | 47 | 97 | 92 | 5 | 0 | 0 | 0 | 27,734 | 0 | 0 | 100% |
| P7 | london | 402 | 93 | 28 | 65 | 57 | 8 | 0 | 0 | 0 | 12,170 | 0 | 0 | 100% |
| P7 | nyam | 43 | 14 | 2 | 12 | 10 | 2 | 0 | 0 | 0 | 2,320 | 0 | 0 | 100% |
| U7 | asia | 156 | 63 | 51 | 12 | 10 | 2 | 0 | 0 | 0 | 4,475 | 0 | 0 | 100% |
| U7 | london | 109 | 39 | 33 | 6 | 4 | 2 | 0 | 0 | 0 | 4,095 | 0 | 0 | 100% |

### Book x session, last 6 months, reached >= 97.5% of target
| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 381 | 116 | 99 | 17 | 16 | 0 | 1 | 1 | 1 | 2,311 | 1,796 | 3,592 | 94% |
| H7 | asia | 144 | 13 | 11 | 2 | 0 | 2 | 0 | 0 | 0 | 718 | 0 | 0 | 100% |
| H7 | nyam | 38 | 4 | 4 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0% |
| K7 | asia | 858 | 168 | 88 | 80 | 79 | 0 | 1 | 1 | 1 | 8,291 | 1,786 | 3,572 | 99% |
| K7 | london | 470 | 78 | 43 | 35 | 34 | 0 | 1 | 1 | 1 | 4,636 | 2,056 | 4,112 | 97% |
| K7 | nyam | 194 | 39 | 20 | 19 | 19 | 0 | 0 | 0 | 0 | 1,455 | 0 | 0 | 100% |
| K7 | nypm | 166 | 41 | 28 | 13 | 13 | 0 | 0 | 0 | 0 | 1,065 | 0 | 0 | 100% |
| M7 | london | 528 | 97 | 56 | 41 | 39 | 0 | 2 | 2 | 2 | 8,753 | 6,078 | 12,156 | 95% |
| M7 | nyam | 231 | 67 | 39 | 28 | 25 | 0 | 3 | 3 | 3 | 7,498 | 5,798 | 11,596 | 89% |
| O7 | nyam | 46 | 7 | 7 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0% |
| P7 | asia | 610 | 77 | 36 | 41 | 38 | 3 | 0 | 0 | 0 | 12,224 | 0 | 0 | 100% |
| P7 | london | 402 | 51 | 20 | 31 | 27 | 4 | 0 | 0 | 0 | 5,035 | 0 | 0 | 100% |
| P7 | nyam | 43 | 3 | 2 | 1 | 1 | 0 | 0 | 0 | 0 | 50 | 0 | 0 | 100% |
| U7 | asia | 156 | 56 | 44 | 12 | 10 | 2 | 0 | 0 | 0 | 4,475 | 0 | 0 | 100% |
| U7 | london | 109 | 31 | 27 | 4 | 4 | 0 | 0 | 0 | 0 | 500 | 0 | 0 | 100% |

### Book x session, all 44 months, reached >= 95.0% of target
| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 1198 | 528 | 425 | 103 | 91 | 0 | 12 | 12 | 12 | 27,826 | 24,681 | 49,363 | 88% |
| H7 | asia | 722 | 103 | 79 | 24 | 0 | 24 | 0 | 0 | 0 | 13,577 | 0 | 0 | 100% |
| H7 | nyam | 366 | 50 | 38 | 12 | 1 | 11 | 0 | 0 | 0 | 3,515 | 0 | 0 | 100% |
| K7 | asia | 2738 | 941 | 332 | 609 | 596 | 0 | 13 | 12 | 12 | 82,677 | 25,504 | 51,009 | 98% |
| K7 | london | 1885 | 624 | 249 | 375 | 360 | 0 | 15 | 14 | 14 | 64,270 | 34,352 | 68,705 | 96% |
| K7 | nyam | 1654 | 573 | 240 | 333 | 327 | 0 | 6 | 5 | 5 | 33,126 | 9,716 | 19,433 | 98% |
| K7 | nypm | 1293 | 421 | 187 | 234 | 221 | 0 | 13 | 9 | 9 | 40,764 | 21,549 | 43,098 | 94% |
| M7 | london | 2494 | 844 | 339 | 505 | 486 | 0 | 19 | 19 | 19 | 85,646 | 47,773 | 95,547 | 96% |
| M7 | nyam | 1566 | 585 | 284 | 301 | 288 | 0 | 13 | 13 | 12 | 42,801 | 23,451 | 46,903 | 96% |
| O7 | nyam | 464 | 151 | 106 | 45 | 32 | 0 | 13 | 0 | 0 | 13,990 | 11,350 | 22,700 | 71% |
| P7 | asia | 2162 | 426 | 124 | 302 | 286 | 16 | 0 | 0 | 0 | 90,315 | 0 | 0 | 100% |
| P7 | london | 1709 | 330 | 98 | 232 | 213 | 19 | 0 | 0 | 0 | 34,812 | 0 | 0 | 100% |
| P7 | nyam | 252 | 58 | 16 | 42 | 37 | 4 | 1 | 1 | 1 | 7,235 | 1,555 | 3,110 | 98% |
| U7 | asia | 702 | 279 | 210 | 69 | 59 | 10 | 0 | 0 | 0 | 40,415 | 0 | 0 | 100% |
| U7 | london | 676 | 260 | 207 | 53 | 43 | 10 | 0 | 0 | 0 | 23,417 | 0 | 0 | 100% |

### Book x session, all 44 months, reached >= 97.5% of target
| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 1198 | 428 | 330 | 98 | 91 | 0 | 7 | 7 | 7 | 16,911 | 14,276 | 28,552 | 93% |
| H7 | asia | 722 | 78 | 66 | 12 | 0 | 12 | 0 | 0 | 0 | 5,658 | 0 | 0 | 100% |
| H7 | nyam | 366 | 36 | 30 | 6 | 1 | 5 | 0 | 0 | 0 | 1,585 | 0 | 0 | 100% |
| K7 | asia | 2738 | 448 | 206 | 242 | 239 | 0 | 3 | 3 | 3 | 26,614 | 5,299 | 10,599 | 99% |
| K7 | london | 1885 | 333 | 172 | 161 | 160 | 0 | 1 | 1 | 1 | 13,643 | 2,056 | 4,112 | 99% |
| K7 | nyam | 1654 | 324 | 162 | 162 | 159 | 0 | 3 | 2 | 2 | 14,253 | 4,008 | 8,017 | 98% |
| K7 | nypm | 1293 | 226 | 122 | 104 | 103 | 0 | 1 | 1 | 1 | 9,075 | 1,295 | 2,590 | 99% |
| M7 | london | 2494 | 462 | 234 | 228 | 225 | 0 | 3 | 3 | 3 | 23,511 | 8,044 | 16,088 | 99% |
| M7 | nyam | 1566 | 351 | 196 | 155 | 147 | 0 | 8 | 8 | 7 | 22,765 | 13,735 | 27,470 | 95% |
| O7 | nyam | 464 | 112 | 77 | 35 | 32 | 0 | 3 | 0 | 0 | 4,225 | 2,620 | 5,240 | 91% |
| P7 | asia | 2162 | 195 | 82 | 113 | 107 | 6 | 0 | 0 | 0 | 28,549 | 0 | 0 | 100% |
| P7 | london | 1709 | 151 | 59 | 92 | 84 | 8 | 0 | 0 | 0 | 12,480 | 0 | 0 | 100% |
| P7 | nyam | 252 | 26 | 14 | 12 | 10 | 1 | 1 | 1 | 1 | 2,850 | 1,585 | 3,170 | 92% |
| U7 | asia | 702 | 229 | 164 | 65 | 59 | 6 | 0 | 0 | 0 | 27,245 | 0 | 0 | 100% |
| U7 | london | 676 | 208 | 161 | 47 | 43 | 4 | 0 | 0 | 0 | 12,502 | 0 | 0 | 100% |

### By book, reached >= 90.0%, L6M and all months
L6M

| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | ALL | 381 | 180 | 155 | 25 | 16 | 0 | 9 | 9 | 9 | 18,771 | 17,206 | 34,412 | 64% |
| ALL | ALL | 4376 | 1782 | 898 | 884 | 728 | 87 | 69 | 65 | 65 | 338,499 | 136,637 | 273,274 | 92% |
| H7 | ALL | 182 | 49 | 28 | 21 | 0 | 21 | 0 | 0 | 0 | 10,000 | 0 | 0 | 100% |
| K7 | ALL | 1688 | 706 | 330 | 376 | 339 | 0 | 37 | 35 | 35 | 109,104 | 74,279 | 148,559 | 90% |
| M7 | ALL | 759 | 299 | 169 | 130 | 109 | 0 | 21 | 21 | 21 | 54,246 | 43,521 | 87,043 | 84% |
| O7 | ALL | 46 | 16 | 14 | 2 | 0 | 0 | 2 | 0 | 0 | 1,990 | 1,630 | 3,260 | 0% |
| P7 | ALL | 1055 | 415 | 108 | 307 | 250 | 57 | 0 | 0 | 0 | 119,982 | 0 | 0 | 100% |
| U7 | ALL | 265 | 117 | 94 | 23 | 14 | 9 | 0 | 0 | 0 | 24,405 | 0 | 0 | 100% |

ALL

| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | ALL | 1198 | 601 | 480 | 121 | 91 | 0 | 30 | 29 | 29 | 65,589 | 59,564 | 119,128 | 75% |
| ALL | ALL | 19881 | 7941 | 3593 | 4348 | 3721 | 349 | 278 | 231 | 227 | 1,416,036 | 507,714 | 1,015,428 | 94% |
| H7 | ALL | 1088 | 231 | 144 | 87 | 1 | 86 | 0 | 0 | 0 | 42,020 | 0 | 0 | 100% |
| K7 | ALL | 7570 | 3152 | 1301 | 1851 | 1720 | 0 | 131 | 114 | 112 | 408,189 | 241,714 | 483,429 | 93% |
| M7 | ALL | 4060 | 1656 | 775 | 881 | 793 | 0 | 88 | 85 | 83 | 246,768 | 178,165 | 356,331 | 90% |
| O7 | ALL | 464 | 171 | 113 | 58 | 32 | 0 | 26 | 1 | 1 | 28,630 | 22,480 | 44,960 | 55% |
| P7 | ALL | 4123 | 1496 | 310 | 1186 | 982 | 202 | 2 | 1 | 1 | 434,838 | 1,585 | 3,170 | 100% |
| U7 | ALL | 1378 | 634 | 470 | 164 | 102 | 61 | 1 | 1 | 1 | 190,002 | 4,205 | 8,410 | 99% |

### By book, reached >= 95.0%, L6M and all months
L6M

| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | ALL | 381 | 158 | 137 | 21 | 16 | 0 | 5 | 5 | 5 | 10,836 | 10,051 | 20,103 | 76% |
| ALL | ALL | 4376 | 1379 | 728 | 651 | 598 | 24 | 29 | 28 | 28 | 153,869 | 64,597 | 129,195 | 96% |
| H7 | ALL | 182 | 26 | 21 | 5 | 0 | 5 | 0 | 0 | 0 | 2,828 | 0 | 0 | 100% |
| K7 | ALL | 1688 | 581 | 265 | 316 | 303 | 0 | 13 | 12 | 12 | 54,554 | 28,024 | 56,049 | 96% |
| M7 | ALL | 759 | 248 | 131 | 117 | 106 | 0 | 11 | 11 | 11 | 34,856 | 26,521 | 53,043 | 91% |
| O7 | ALL | 46 | 13 | 13 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0% |
| P7 | ALL | 1055 | 251 | 77 | 174 | 159 | 15 | 0 | 0 | 0 | 42,224 | 0 | 0 | 100% |
| U7 | ALL | 265 | 102 | 84 | 18 | 14 | 4 | 0 | 0 | 0 | 8,570 | 0 | 0 | 100% |

ALL

| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | ALL | 1198 | 528 | 425 | 103 | 91 | 0 | 12 | 12 | 12 | 27,826 | 24,681 | 49,363 | 88% |
| ALL | ALL | 19881 | 6173 | 2934 | 3239 | 3040 | 94 | 105 | 85 | 84 | 604,388 | 199,934 | 399,868 | 97% |
| H7 | ALL | 1088 | 153 | 117 | 36 | 1 | 35 | 0 | 0 | 0 | 17,092 | 0 | 0 | 100% |
| K7 | ALL | 7570 | 2559 | 1008 | 1551 | 1504 | 0 | 47 | 40 | 40 | 220,837 | 91,122 | 182,245 | 97% |
| M7 | ALL | 4060 | 1429 | 623 | 806 | 774 | 0 | 32 | 32 | 31 | 128,447 | 71,225 | 142,450 | 96% |
| O7 | ALL | 464 | 151 | 106 | 45 | 32 | 0 | 13 | 0 | 0 | 13,990 | 11,350 | 22,700 | 71% |
| P7 | ALL | 4123 | 814 | 238 | 576 | 536 | 39 | 1 | 1 | 1 | 132,363 | 1,555 | 3,110 | 100% |
| U7 | ALL | 1378 | 539 | 417 | 122 | 102 | 20 | 0 | 0 | 0 | 63,832 | 0 | 0 | 100% |

### By book, reached >= 97.5%, L6M and all months
L6M

| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | ALL | 381 | 116 | 99 | 17 | 16 | 0 | 1 | 1 | 1 | 2,311 | 1,796 | 3,592 | 94% |
| ALL | ALL | 4376 | 848 | 524 | 324 | 305 | 11 | 8 | 8 | 8 | 57,011 | 17,514 | 35,028 | 98% |
| H7 | ALL | 182 | 17 | 15 | 2 | 0 | 2 | 0 | 0 | 0 | 718 | 0 | 0 | 100% |
| K7 | ALL | 1688 | 326 | 179 | 147 | 145 | 0 | 2 | 2 | 2 | 15,447 | 3,842 | 7,684 | 99% |
| M7 | ALL | 759 | 164 | 95 | 69 | 64 | 0 | 5 | 5 | 5 | 16,251 | 11,876 | 23,752 | 93% |
| O7 | ALL | 46 | 7 | 7 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0% |
| P7 | ALL | 1055 | 131 | 58 | 73 | 66 | 7 | 0 | 0 | 0 | 17,309 | 0 | 0 | 100% |
| U7 | ALL | 265 | 87 | 71 | 16 | 14 | 2 | 0 | 0 | 0 | 4,975 | 0 | 0 | 100% |

ALL

| book | session | trades | reached | target later (filled) | not filled | exit = live take | exit = live lock | unprotected exits | unprot. ended <=+5 pts | unprot. ended < -5 | $ left vs target (base) | $ given back vs take at X (unprot, base) | same x1.75 live lots | live-line share of not-filled |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | ALL | 1198 | 428 | 330 | 98 | 91 | 0 | 7 | 7 | 7 | 16,911 | 14,276 | 28,552 | 93% |
| ALL | ALL | 19881 | 3607 | 2075 | 1532 | 1460 | 42 | 30 | 26 | 25 | 221,867 | 52,919 | 105,838 | 98% |
| H7 | ALL | 1088 | 114 | 96 | 18 | 1 | 17 | 0 | 0 | 0 | 7,242 | 0 | 0 | 100% |
| K7 | ALL | 7570 | 1331 | 662 | 669 | 661 | 0 | 8 | 7 | 7 | 63,586 | 12,659 | 25,318 | 99% |
| M7 | ALL | 4060 | 813 | 430 | 383 | 372 | 0 | 11 | 11 | 10 | 46,276 | 21,779 | 43,558 | 97% |
| O7 | ALL | 464 | 112 | 77 | 35 | 32 | 0 | 3 | 0 | 0 | 4,225 | 2,620 | 5,240 | 91% |
| P7 | ALL | 4123 | 372 | 155 | 217 | 201 | 15 | 1 | 1 | 1 | 43,879 | 1,585 | 3,170 | 100% |
| U7 | ALL | 1378 | 437 | 325 | 112 | 102 | 10 | 0 | 0 | 0 | 39,747 | 0 | 0 | 100% |

### By window and year (all books), reached >= 90.0%
| window | trades | reached | not filled | live take | live lock | unprotected | ended <=+5 | ended < -5 | $ left vs target (base) | $ given back (unprot, base) | x1.75 | per week given back (base) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M | 766 | 298 | 138 | 116 | 13 | 9 | 9 | 9 | 45,731 | 16,803 | 33,606 | 3,361 |
| L3M | 2021 | 811 | 421 | 346 | 40 | 35 | 32 | 32 | 169,275 | 66,690 | 133,380 | 4,764 |
| L6M | 4376 | 1782 | 884 | 728 | 87 | 69 | 65 | 65 | 338,499 | 136,637 | 273,274 | 5,061 |
| HOLD | 3287 | 1334 | 722 | 603 | 63 | 56 | 49 | 47 | 264,106 | 103,776 | 207,553 | 3,844 |
| GAP | 1833 | 758 | 423 | 365 | 35 | 23 | 16 | 16 | 114,350 | 33,805 | 67,610 | 1,690 |
| PRE | 7336 | 2828 | 1519 | 1316 | 115 | 88 | 75 | 74 | 484,090 | 167,340 | 334,681 | 2,231 |
| X' | 2971 | 1197 | 784 | 695 | 47 | 42 | 26 | 25 | 211,800 | 66,155 | 132,310 | 1,504 |
| ALL | 19881 | 7941 | 4348 | 3721 | 349 | 278 | 231 | 227 | 1,416,036 | 507,714 | 1,015,428 | 2,686 |
| Y2023 | 2642 | 1040 | 679 | 608 | 37 | 34 | 23 | 22 | 183,694 | 56,464 | 112,928 | 1,448 |
| Y2024 | 4607 | 1815 | 1055 | 909 | 74 | 72 | 55 | 54 | 330,692 | 126,412 | 252,825 | 2,385 |
| Y2025 | 5691 | 2239 | 1156 | 996 | 100 | 60 | 50 | 48 | 353,319 | 106,681 | 213,362 | 2,013 |
| Y2026 | 6941 | 2847 | 1458 | 1208 | 138 | 112 | 103 | 103 | 548,331 | 218,156 | 436,313 | 4,743 |

### By window and year (all books), reached >= 95.0%
| window | trades | reached | not filled | live take | live lock | unprotected | ended <=+5 | ended < -5 | $ left vs target (base) | $ given back (unprot, base) | x1.75 | per week given back (base) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M | 766 | 238 | 107 | 96 | 6 | 5 | 5 | 5 | 26,612 | 9,806 | 19,613 | 1,961 |
| L3M | 2021 | 623 | 314 | 288 | 14 | 12 | 11 | 11 | 72,560 | 25,619 | 51,239 | 1,830 |
| L6M | 4376 | 1379 | 651 | 598 | 24 | 29 | 28 | 28 | 153,869 | 64,597 | 129,195 | 2,392 |
| HOLD | 3287 | 1028 | 529 | 492 | 15 | 22 | 17 | 17 | 99,952 | 37,922 | 75,845 | 1,405 |
| GAP | 1833 | 583 | 308 | 290 | 8 | 10 | 7 | 7 | 48,637 | 15,059 | 30,118 | 753 |
| PRE | 7336 | 2218 | 1166 | 1101 | 33 | 32 | 28 | 27 | 206,889 | 65,989 | 131,979 | 880 |
| X' | 2971 | 928 | 572 | 546 | 14 | 12 | 5 | 5 | 92,976 | 16,365 | 32,731 | 372 |
| ALL | 19881 | 6173 | 3239 | 3040 | 94 | 105 | 85 | 84 | 604,388 | 199,934 | 399,868 | 1,058 |
| Y2023 | 2642 | 814 | 500 | 480 | 11 | 9 | 4 | 4 | 80,781 | 12,050 | 24,101 | 309 |
| Y2024 | 4607 | 1429 | 801 | 753 | 19 | 29 | 23 | 22 | 137,897 | 53,512 | 107,025 | 1,010 |
| Y2025 | 5691 | 1731 | 863 | 815 | 29 | 19 | 15 | 15 | 148,893 | 35,987 | 71,974 | 679 |
| Y2026 | 6941 | 2199 | 1075 | 992 | 35 | 48 | 43 | 43 | 236,818 | 98,384 | 196,768 | 2,139 |

### By window and year (all books), reached >= 97.5%
| window | trades | reached | not filled | live take | live lock | unprotected | ended <=+5 | ended < -5 | $ left vs target (base) | $ given back (unprot, base) | x1.75 | per week given back (base) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M | 766 | 161 | 60 | 55 | 4 | 1 | 1 | 1 | 11,047 | 1,911 | 3,822 | 382 |
| L3M | 2021 | 389 | 152 | 144 | 5 | 3 | 3 | 3 | 24,321 | 5,560 | 11,121 | 397 |
| L6M | 4376 | 848 | 324 | 305 | 11 | 8 | 8 | 8 | 57,011 | 17,514 | 35,028 | 649 |
| HOLD | 3287 | 590 | 254 | 242 | 5 | 7 | 6 | 6 | 34,810 | 11,610 | 23,220 | 430 |
| GAP | 1833 | 325 | 126 | 118 | 4 | 4 | 3 | 3 | 18,468 | 5,493 | 10,987 | 275 |
| PRE | 7336 | 1288 | 562 | 537 | 18 | 7 | 6 | 5 | 77,955 | 11,838 | 23,676 | 158 |
| X' | 2971 | 537 | 260 | 252 | 4 | 4 | 3 | 3 | 32,953 | 6,463 | 12,927 | 147 |
| ALL | 19881 | 3607 | 1532 | 1460 | 42 | 30 | 26 | 25 | 221,867 | 52,919 | 105,838 | 280 |
| Y2023 | 2642 | 476 | 227 | 220 | 3 | 4 | 3 | 3 | 30,968 | 6,463 | 12,927 | 166 |
| Y2024 | 4607 | 813 | 364 | 348 | 9 | 7 | 6 | 5 | 44,365 | 11,838 | 23,676 | 223 |
| Y2025 | 5691 | 1000 | 412 | 392 | 15 | 5 | 4 | 4 | 59,916 | 6,823 | 13,647 | 129 |
| Y2026 | 6941 | 1318 | 529 | 500 | 15 | 14 | 13 | 13 | 86,618 | 27,794 | 55,588 | 604 |

## 1b. UNPROTECTED RESIDUE - exact definitions, decomposition, exit distribution, placebo (answer to lead check 11-18)

**Definitions.** Reached 95% = the 1-s favourable print extreme between entry and exit was >= 0.95 x target (57 pts; O7 85.5) and the trade did not end with a Target fill. **Unprotected residue** = reached 95%, no Target fill, and the JL3 exit was NOT the live take (PolicyTake) or live lock (PolicyTrail): i.e. it ended by StateCut, EarlyCut, StackCut, Stop/StopJoin, TimeBlock, BookLock. (a) = realized price P&L of those trades = pts x $20 x lots, minus $4.84 x lots RT fee. (b) = what a take at 95% would have captured = (0.95 x target - 0.80 pt market slippage) x $20 x lots, minus the same $4.84 x lots fee. (c) = b - a = the real "left on the table" (the fee cancels). x1.75 columns use live lots = max(1, floor(1.75 x base + 0.5)) on the same pts. The earlier count-table column "$ given back vs a take at X" was (c) without the 0.8 pt slippage, summed over the unprotected trades; it is a DIFFERENCE, not the target value. Why ~$2k per trade: these trades touched +57 and then ended at -26..-71 pts (state cut / early cut / stop), a swing of ~90 pts = $1.8k per lot; a 59-pt target alone is $1.2k per lot but the swing is what is lost. Base lots are 1-2 per trade here (K7 15 lots on 13 trades). Count of residue trades L6M: 29 of 1,379 that reached 95% (2.1%), of 4,376 L6M trades.

### L6M (2026-05-14..2026-11-13) by book
| book | trades | base lots | live lots | (a) realized net $4.84, base | (b) take at 95% less 0.8 pt slip, net $4.84, base | (c) = b - a left on the table, base | (a) x1.75 | (b) x1.75 | (c) x1.75 | (c) per trade base |
|---|---|---|---|---|---|---|---|---|---|---|
| A7 | 5 | 5 | 10 | -4,376 | 5,596 | 9,971 | -8,751 | 11,192 | 19,943 | 1,994 |
| K7 | 13 | 15 | 30 | -10,997 | 16,787 | 27,784 | -21,994 | 33,575 | 55,569 | 2,137 |
| M7 | 11 | 14 | 28 | -10,629 | 15,668 | 26,297 | -21,259 | 31,336 | 52,595 | 2,391 |
| **all** | 29 | 34 | 68 | -26,002 | 38,051 | 64,053 | -52,004 | 76,103 | 128,107 | 2,209 |

### L6M by session
| sess | trades | base lots | live lots | (a) realized net $4.84, base | (b) take at 95% less 0.8 pt slip, net $4.84, base | (c) = b - a left on the table, base | (a) x1.75 | (b) x1.75 | (c) x1.75 | (c) per trade base |
|---|---|---|---|---|---|---|---|---|---|---|
| asia | 9 | 9 | 18 | -7,216 | 10,072 | 17,288 | -14,431 | 20,145 | 34,576 | 1,921 |
| london | 15 | 20 | 40 | -14,915 | 22,383 | 37,298 | -29,830 | 44,766 | 74,596 | 2,487 |
| nyam | 4 | 4 | 8 | -2,943 | 4,477 | 7,420 | -5,887 | 8,953 | 14,840 | 1,855 |
| nypm | 1 | 1 | 2 | -928 | 1,119 | 2,047 | -1,857 | 2,238 | 4,095 | 2,047 |
| **all** | 29 | 34 | 68 | -26,002 | 38,051 | 64,053 | -52,004 | 76,103 | 128,107 | 2,209 |

### All 44 months by calendar year
| yr | trades | base lots | live lots | (a) realized net $4.84, base | (b) take at 95% less 0.8 pt slip, net $4.84, base | (c) = b - a left on the table, base | (a) x1.75 | (b) x1.75 | (c) x1.75 | (c) per trade base |
|---|---|---|---|---|---|---|---|---|---|---|
| 2023 | 9 | 10 | 20 | 441 | 12,332 | 11,890 | 882 | 24,663 | 23,781 | 1,321 |
| 2024 | 29 | 32 | 64 | -14,907 | 38,093 | 53,000 | -29,815 | 76,186 | 106,001 | 1,828 |
| 2025 | 19 | 21 | 42 | -10,439 | 25,212 | 35,651 | -20,877 | 50,425 | 71,302 | 1,876 |
| 2026 | 48 | 54 | 108 | -34,805 | 62,715 | 97,520 | -69,611 | 125,429 | 195,040 | 2,032 |
| **all** | 105 | 117 | 234 | -59,710 | 138,352 | 198,062 | -119,421 | 276,703 | 396,124 | 1,886 |

### All 44 months by book
| book | trades | base lots | live lots | (a) realized net $4.84, base | (b) take at 95% less 0.8 pt slip, net $4.84, base | (c) = b - a left on the table, base | (a) x1.75 | (b) x1.75 | (c) x1.75 | (c) per trade base |
|---|---|---|---|---|---|---|---|---|---|---|
| A7 | 12 | 12 | 24 | -11,060 | 13,430 | 24,489 | -22,119 | 26,860 | 48,979 | 2,041 |
| K7 | 47 | 54 | 108 | -29,824 | 60,435 | 90,258 | -59,648 | 120,869 | 180,517 | 1,920 |
| M7 | 32 | 37 | 74 | -29,224 | 41,409 | 70,633 | -58,448 | 82,818 | 141,266 | 2,207 |
| O7 | 13 | 13 | 26 | 10,817 | 21,959 | 11,142 | 21,634 | 43,918 | 22,284 | 857 |
| P7 | 1 | 1 | 2 | -420 | 1,119 | 1,539 | -840 | 2,238 | 3,078 | 1,539 |
| **all** | 105 | 117 | 234 | -59,710 | 138,352 | 198,062 | -119,421 | 276,703 | 396,124 | 1,886 |

### Trades per book
| book | trades_44m | trades_L6M | reached95_44m | reached95_L6M | residue_44m | residue_L6M |
|---|---|---|---|---|---|---|
| A7 | 1198 | 381 | 528 | 158 | 12 | 5 |
| H7 | 1088 | 182 | 153 | 26 | 0 | 0 |
| K7 | 7570 | 1688 | 2559 | 581 | 47 | 13 |
| M7 | 4060 | 759 | 1429 | 248 | 32 | 11 |
| O7 | 464 | 46 | 151 | 13 | 13 | 0 |
| P7 | 4123 | 1055 | 814 | 251 | 1 | 0 |
| U7 | 1378 | 265 | 539 | 102 | 0 | 0 |

### Exit distribution of the 29 L6M residue trades (target-later is excluded by definition: those filled the Target and are not residue; of all 1,379 L6M trades that reached 95%, 728 filled the target later, 622 exited by the live take/lock, 29 residue)
| end | n | mean pts | mean MFE |
|---|---|---|---|
| loss (cut / other) | 26 | -37.8 | 58.1 |
| stop | 3 | -27.8 | 57.7 |
By JL3 exit name: StateCut 20, EarlyCut 5, Stop 3, StackCut 1

### Placebo (luck baseline): the same-clock 1-s path 11 / 23 / 37 days earlier, same side and duration for every JL3 trade, latched at 95% of target, with NO exit rule (hold to the same duration)
| shift days | trades | reach 95% | ended <= +5 pts at the same duration | share of reached |
|---|---|---|---|---|
| 11 | 19881 | 4772 | 654 | 13.7% |
| 23 | 19881 | 4581 | 592 | 12.9% |
| 37 | 19881 | 4540 | 676 | 14.9% |
Real JL3: 6,173 of 19,881 trades reach 95% (31%; placebo paths 23-24%, so real paths are not random: the strategy enters with the trend), and only 85 of those 6,173 (1.4%) end <= +5 pts under the live take/lock lines, against 13-15% for the unprotected random-path baseline. Reading: the live lines already remove about nine tenths of the touch-and-reverse outcomes; what remains is a 1.4% tail, concentrated in K7/M7/A7 state cuts and stops after a fast touch (price outside the 3-pt band before 5 s pass). A new rule has to beat the placebo-latch nulls in section 2 to count as edge.

## Steps 2-6
**Screen status**: FIRST-ORDER on JL3 trade paths (alternative exit only if it fires before the real JL3 exit; no freed-book effect; market exits at mid -0.80 pt; limit fills optimistic unless `cons`); in-sample 44 months, trailing-6M pick (2026-05-14..2026-11-13), L3M beside; older windows/years = ulcer and mean vs JL3 (AMBER 15-30%, RED >30% worse, mean drop floored at 10% of the stack mean). Trials counted: 12 LA + 12 LB (x3 latch levels) + 24 LC + 6 SH + 4 TS = 154 cells x 17 scopes; no multiple-testing correction applied; engine controls (30 persistent draws) not run -> nothing here is CONFIRMED or LEAD. Placebo column = ulcer change % (L6M, own book) of the same cell with decisions from the path 11/23/37 days earlier (real must be clearly lower than these).

### K7 (pooled sessions, own-book ulcer)
| cell | policy / what DS7 needs | ulcer chg L6M / L3M (%) | d mean $/wk L6M base ($4.84) / x1.75 | mean chg L6M / L3M (%) | fires L6M | worst older ulcer / mean drop (%) | older tier | placebo ulcer chg 11/23/37 | label |
|---|---|---|---|---|---|---|---|---|---|
| TS_X0.90_opt | NEW CODE (partial exit): half of the position at 0.90 of target (scale 0.5 style), rest to target | -6.8 / -12.9 | 418 / 835 | 13.8 / 15.6 | 676 | 2.3 / 19.2 | AMBER | n/a | WEAK-BUT-POSITIVE |
| TS_X0.95_opt | NEW CODE (partial exit): half of the position at 0.95 of target (scale 0.5 style), rest to target | -4.4 / -5.6 | 452 / 903 | 14.9 / 10.9 | 484 | 0.5 / 5.4 | ok | n/a | WEAK-BUT-POSITIVE |
| SH_k2_opt | bracket K7 * target=59.50  (engine/screen baseline target 60; live K7 is already 59 = 4 ticks, P7 58, M7 59.5) | -2.7 / -2.4 | 195 / 390 | 6.5 / 2.8 | 106 | -0.7 / -2.5 | ok | n/a | WEAK-BUT-POSITIVE |
| SH_k4_opt | bracket K7 * target=59.00  (engine/screen baseline target 60; live K7 is already 59 = 4 ticks, P7 58, M7 59.5) | -2.5 / -2.1 | 182 / 364 | 6.0 / 1.2 | 215 | -0.4 / -4.4 | ok | n/a | WEAK-BUT-POSITIVE |
| SH_k4_cons | bracket K7 * target=59.00  (engine/screen baseline target 60; live K7 is already 59 = 4 ticks, P7 58, M7 59.5) | -2.3 / -2.2 | 164 / 327 | 5.4 / 1.0 | 169 | -0.3 / -1.1 | ok | n/a | WEAK-BUT-POSITIVE |

### M7 (pooled sessions, own-book ulcer)
| cell | policy / what DS7 needs | ulcer chg L6M / L3M (%) | d mean $/wk L6M base ($4.84) / x1.75 | mean chg L6M / L3M (%) | fires L6M | worst older ulcer / mean drop (%) | older tier | placebo ulcer chg 11/23/37 | label |
|---|---|---|---|---|---|---|---|---|---|
| LB_X0.95_G8 | NEW CODE: latch at 0.95 of target, exit at market when price gives back 8 pts from the extreme | -23.6 / -15.9 | 472 / 943 | 25.3 / 36.9 | 69 | 11.6 / 22.9 | AMBER | 17.0 / 5.4 / 54.9 | WEAK-BUT-POSITIVE |
| LA_X0.95_S10 | NEW CODE: latch at 0.95 of target, exit at market when no new favourable extreme for 10 s | -23.2 / -15.1 | 412 / 824 | 22.1 / 34.3 | 83 | 7.5 / 29.2 | AMBER | 18.2 / 3.1 / 44.2 | WEAK-BUT-POSITIVE |
| TS_X0.95_opt | NEW CODE (partial exit): half of the position at 0.95 of target (scale 0.5 style), rest to target | -20.6 / -11.0 | 385 / 771 | 20.7 / 27.0 | 203 | 0.1 / -6.3 | ok | n/a | WEAK-BUT-POSITIVE |
| SH_k2_opt | bracket M7 * target=59.50  (engine/screen baseline target 60; live K7 is already 59 = 4 ticks, P7 58, M7 59.5) | -20.2 / -0.0 | 240 / 480 | 12.9 / 0.1 | 65 | -0.1 / -1.2 | ok | n/a | WEAK-BUT-POSITIVE |
| SH_k4_opt | bracket M7 * target=59.00  (engine/screen baseline target 60; live K7 is already 59 = 4 ticks, P7 58, M7 59.5) | -19.8 / -0.2 | 294 / 587 | 15.8 / 8.3 | 112 | 0.0 / -5.7 | ok | n/a | WEAK-BUT-POSITIVE |

### A7 (pooled sessions, own-book ulcer)
| cell | policy / what DS7 needs | ulcer chg L6M / L3M (%) | d mean $/wk L6M base ($4.84) / x1.75 | mean chg L6M / L3M (%) | fires L6M | worst older ulcer / mean drop (%) | older tier | placebo ulcer chg 11/23/37 | label |
|---|---|---|---|---|---|---|---|---|---|
| LB_X0.85_G12 | NEW CODE: latch at 0.85 of target, exit at market when price gives back 12 pts from the extreme | -12.7 / -15.8 | -81 / -161 | -4.3 / -16.0 | 107 | 18.8 / 26.2 | AMBER | 112.6 / 34.1 / -2.7 | BEST-AVAILABLE-NOT-PROVEN |
| TS_X0.90_opt | NEW CODE (partial exit): half of the position at 0.90 of target (scale 0.5 style), rest to target | -7.6 / 1.1 | -35 / -69 | -1.9 / -9.5 | 172 | 12.2 / 4.8 | ok | n/a | BEST-AVAILABLE-NOT-PROVEN |
| TS_X0.95_opt | NEW CODE (partial exit): half of the position at 0.95 of target (scale 0.5 style), rest to target | -5.6 / 0.8 | 44 / 88 | 2.4 / -0.0 | 141 | 3.8 / 5.4 | ok | n/a | BEST-AVAILABLE-NOT-PROVEN |
| SH_k1_opt | bracket A7 * target=59.75  (engine/screen baseline target 60; live K7 is already 59 = 4 ticks, P7 58, M7 59.5) | -4.5 / -4.0 | 68 / 135 | 3.6 / 9.8 | 38 | 0.3 / 0.2 | ok | n/a | WEAK-BUT-POSITIVE |
| SH_k2_cons | bracket A7 * target=59.50  (engine/screen baseline target 60; live K7 is already 59 = 4 ticks, P7 58, M7 59.5) | -4.2 / -3.8 | 61 / 121 | 3.3 / 9.2 | 37 | 0.6 / 0.8 | ok | n/a | WEAK-BUT-POSITIVE |

### P7 (pooled sessions, own-book ulcer)
| cell | policy / what DS7 needs | ulcer chg L6M / L3M (%) | d mean $/wk L6M base ($4.84) / x1.75 | mean chg L6M / L3M (%) | fires L6M | worst older ulcer / mean drop (%) | older tier | placebo ulcer chg 11/23/37 | label |
|---|---|---|---|---|---|---|---|---|---|
| LC_a0.80_L0.50 | profit P7 * pct>=0.80 lock 30.0 persist=1 | -3.4 / -3.9 | 83 / 110 | 0.8 / -1.3 | 88 | 3.2 / 14.4 | ok | -12.9 / -15.7 / -0.4 | WEAK-BUT-POSITIVE |
| TS_X0.90_opt | NEW CODE (partial exit): half of the position at 0.90 of target (scale 0.5 style), rest to target | -2.1 / -2.3 | 343 / 633 | 3.4 / 4.2 | 401 | -0.8 / -4.4 | ok | n/a | WEAK-BUT-POSITIVE |
| LC_a0.85_L0.50 | profit P7 * pct>=0.85 lock 30.0 persist=1 | -1.7 / -1.9 | 198 / 337 | 2.0 / 1.5 | 27 | -1.3 / 1.1 | ok | -11.8 / -12.2 / 1.6 | WEAK-BUT-POSITIVE |
| TS_X0.95_opt | NEW CODE (partial exit): half of the position at 0.95 of target (scale 0.5 style), rest to target | -1.4 / -1.6 | 269 / 507 | 2.7 / 4.1 | 219 | -0.9 / -1.4 | ok | n/a | WEAK-BUT-POSITIVE |
| LC_a0.90_L0.70 | profit P7 * pct>=0.90 lock 42.0 persist=1 | -1.3 / -1.2 | -77 / -129 | -0.8 / -4.8 | 60 | 1.1 / 0.9 | ok | -24.6 / -16.4 / -5.7 | BEST-AVAILABLE-NOT-PROVEN |

### U7 (pooled sessions, own-book ulcer)
| cell | policy / what DS7 needs | ulcer chg L6M / L3M (%) | d mean $/wk L6M base ($4.84) / x1.75 | mean chg L6M / L3M (%) | fires L6M | worst older ulcer / mean drop (%) | older tier | placebo ulcer chg 11/23/37 | label |
|---|---|---|---|---|---|---|---|---|---|
| LC_a0.70_L0.00 | profit U7 * pct>=0.70 lock 0.0 persist=1 | -24.8 / -24.6 | 745 / 1329 | 29.3 / 75.4 | 17 | 13.7 / 16.8 | AMBER | -16.4 / -1.5 / -29.6 | WEAK-BUT-POSITIVE |
| LC_a0.90_L0.80 | profit U7 * pct>=0.90 lock 48.0 persist=1 | -14.9 / -23.3 | -54 / -97 | -2.1 / 16.5 | 45 | 17.2 / 26.0 | AMBER | -34.6 / -31.1 / -35.9 | BEST-AVAILABLE-NOT-PROVEN |
| TS_X0.90_opt | NEW CODE (partial exit): half of the position at 0.90 of target (scale 0.5 style), rest to target | -8.6 / -14.3 | -76 / -132 | -3.0 / 5.6 | 112 | -1.9 / 7.2 | ok | n/a | BEST-AVAILABLE-NOT-PROVEN |
| TS_X0.90_cons | NEW CODE (partial exit): half of the position at 0.90 of target (scale 0.5 style), rest to target | -6.4 / -10.7 | -207 / -372 | -8.1 / -6.2 | 110 | 1.7 / 26.0 | AMBER | n/a | BEST-AVAILABLE-NOT-PROVEN |
| TS_X0.95_opt | NEW CODE (partial exit): half of the position at 0.95 of target (scale 0.5 style), rest to target | -0.0 / -1.1 | -26 / -37 | -1.0 / 3.0 | 95 | 3.0 / 12.5 | ok | n/a | BEST-AVAILABLE-NOT-PROVEN |

### H7 (pooled sessions, own-book ulcer)
| cell | policy / what DS7 needs | ulcer chg L6M / L3M (%) | d mean $/wk L6M base ($4.84) / x1.75 | mean chg L6M / L3M (%) | fires L6M | worst older ulcer / mean drop (%) | older tier | placebo ulcer chg 11/23/37 | label |
|---|---|---|---|---|---|---|---|---|---|
| LC_a0.60_L0.50 | profit H7 * pct>=0.60 lock 30.0 persist=1 | -8.7 / -5.4 | -220 / -468 | -11.6 / 3.1 | 62 | 18.0 / 20.0 | AMBER | -52.8 / -31.7 / -32.8 | BEST-AVAILABLE-NOT-PROVEN |
| LC_a0.85_L0.80 | profit H7 * pct>=0.85 lock 48.0 persist=1 | -8.2 / -11.5 | 74 / 147 | 3.9 / 11.3 | 28 | 5.9 / 7.5 | ok | -38.7 / -27.4 / -21.1 | WEAK-BUT-POSITIVE |
| LB_X0.85_G5 | NEW CODE: latch at 0.85 of target, exit at market when price gives back 5 pts from the extreme | -5.1 / -7.0 | 73 / 137 | 3.8 / 8.6 | 52 | 8.7 / 16.6 | AMBER | 30.1 / 9.7 / 22.5 | WEAK-BUT-POSITIVE |
| LA_X0.85_S5 | NEW CODE: latch at 0.85 of target, exit at market when no new favourable extreme for 5 s | -4.4 / -6.2 | 54 / 99 | 2.9 / 7.7 | 46 | 6.4 / 13.9 | ok | 26.5 / 12.7 / 21.4 | WEAK-BUT-POSITIVE |
| LC_a0.70_L0.50 | profit H7 * pct>=0.70 lock 30.0 persist=1 | -2.7 / 3.4 | -108 / -216 | -5.7 / 1.3 | 28 | 21.5 / 18.9 | AMBER | -29.7 / -20.5 / -22.6 | BEST-AVAILABLE-NOT-PROVEN |

### O7 (pooled sessions, own-book ulcer)
| cell | policy / what DS7 needs | ulcer chg L6M / L3M (%) | d mean $/wk L6M base ($4.84) / x1.75 | mean chg L6M / L3M (%) | fires L6M | worst older ulcer / mean drop (%) | older tier | placebo ulcer chg 11/23/37 | label |
|---|---|---|---|---|---|---|---|---|---|
| LC_a0.70_L0.50 | profit O7 * pct>=0.70 lock 30.0 persist=1 | -16.0 / -13.6 | -167 / -334 | -9.0 / -18.3 | 15 | 16.4 / 29.3 | AMBER | -11.4 / 1.3 / 2.4 | BEST-AVAILABLE-NOT-PROVEN |
| LC_a0.70_L0.25 | profit O7 * pct>=0.70 lock 15.0 persist=1 | -5.7 / 4.5 | -102 / -204 | -5.5 / -5.7 | 8 | 28.3 / 19.0 | AMBER | -8.4 / 2.4 / 0.0 | BEST-AVAILABLE-NOT-PROVEN |
| LC_a0.85_L0.00 | profit O7 * pct>=0.85 lock 0.0 persist=1 | -1.3 / 0.0 | 28 / 55 | 1.5 / 0.0 | 1 | 7.3 / 7.0 | ok | -5.0 / 3.8 / 0.0 | BEST-AVAILABLE-NOT-PROVEN |
| LC_a0.80_L0.25 | profit O7 * pct>=0.80 lock 15.0 persist=1 | -0.9 / 0.0 | -57 / -114 | -3.0 / 0.0 | 3 | 6.7 / 10.6 | ok | -8.4 / 2.4 / 0.0 | BEST-AVAILABLE-NOT-PROVEN |
| LC_a0.85_L0.25 | profit O7 * pct>=0.85 lock 15.0 persist=1 | -0.9 / 0.0 | -57 / -114 | -3.0 / 0.0 | 3 | 4.8 / 5.2 | ok | -8.4 / 2.4 / 0.0 | BEST-AVAILABLE-NOT-PROVEN |

Families not yet run: (5) persist-counter fix and (6) order-book latch need the book features and the ptr grammar hook on the JL3 hooklist (batch 2 after the identity cells land); two-step exit needs live-lot (x1.75) partials, the base-lot engine cannot split 1 lot. Live K7 target is already 59 (4 ticks nearer than the engine 60), P7 58, M7 59.5: the incident trade had a 59-pt target.

## 3. ENGINE ROWS (TL3_NT_* vs TL3_EV_JL3 on the same landed months; written 2026-11-19 09:21Z)

### Identity (inert == JL3 trade for trade)
| set | month | trades | JL3 trades | net | JL3 net | identical |
|---|---|---|---|---|---|---|
| TL3_NT_ID0 | 202504 | 637 | 637 | 41239.76 | 41239.76 | True |
| TL3_NT_ID0 | 202610 | 691 | 691 | 37159.82 | 37159.82 | True |
| TL3_NT_ID1 | 202504 | 637 | 637 | 41239.76 | 41239.76 | True |
| TL3_NT_ID1 | 202610 | 691 | 691 | 37159.82 | 37159.82 | True |

### Sets landed (stack-level, landed months only; months are L6M/HOLD recent-first, so read as a partial window)
| set | months landed | first..last | d mean $/wk ($4.84, base lots) | d mean $/wk x1.75 | stack ulcer change % | d trades | JL3 mean $/wk on these months |
|---|---|---|---|---|---|---|---|
| TL3_NT_LK_H7_a85_L80 | 13 | 202511..202611 | -3 | -9 | 0.4 | 1 | 14413 |
| TL3_NT_LK_K7_a60_L25 | 13 | 202511..202611 | -827 | -1625 | -6.4 | 415 | 14413 |
| TL3_NT_LK_K7_a70_L25 | 13 | 202511..202611 | -709 | -1422 | -13.6 | 303 | 14413 |
| TL3_NT_LK_K7_a70_L50 | 44 | 202304..202611 | -125 | -254 | -11.5 | 1110 | 7581 |
| TL3_NT_LK_K7_a80_L0 | 13 | 202511..202611 | -104 | -208 | 1.9 | 174 | 14413 |
| TL3_NT_LK_K7_a80_L25 | 13 | 202511..202611 | 425 | 841 | -13.6 | 213 | 14413 |
| TL3_NT_LK_K7_a80_L50 | 44 | 202304..202611 | -87 | -174 | 2.3 | 507 | 7581 |
| TL3_NT_LK_M7_a60_L25 | 13 | 202511..202611 | -64 | -134 | -4.1 | 214 | 14413 |
| TL3_NT_LK_M7_a70_L25 | 13 | 202511..202611 | -442 | -873 | -4.7 | 143 | 14413 |
| TL3_NT_LK_M7_a70_L50 | 13 | 202511..202611 | 139 | 278 | -7.4 | 166 | 14413 |
| TL3_NT_LK_M7_a80_L0 | 13 | 202511..202611 | -171 | -342 | -0.5 | 61 | 14413 |
| TL3_NT_LK_M7_a80_L25 | 13 | 202511..202611 | -451 | -890 | 2.5 | 112 | 14413 |
| TL3_NT_LK_M7_a80_L50 | 13 | 202511..202611 | 99 | 200 | 2.6 | 127 | 14413 |
| TL3_NT_LK_P7_a80_L50 | 13 | 202511..202611 | 105 | 212 | -5.3 | 47 | 14413 |
| TL3_NT_L_A7_A90S5 | 13 | 202511..202611 | -355 | -703 | 0.8 | 13 | 14413 |
| TL3_NT_L_A7_A95S10 | 13 | 202511..202611 | -15 | -24 | -0.1 | 31 | 14413 |
| TL3_NT_L_A7_A95S5 | 13 | 202511..202611 | 8 | 23 | 0.2 | 30 | 14413 |
| TL3_NT_L_A7_B95G8 | 13 | 202511..202611 | 4 | 13 | -1.1 | 31 | 14413 |
| TL3_NT_L_K7_A90S5 | 13 | 202511..202611 | 215 | 418 | -4.0 | 75 | 14413 |
| TL3_NT_L_K7_A95S10 | 13 | 202511..202611 | -66 | -131 | 2.8 | 26 | 14413 |
| TL3_NT_L_K7_A95S5 | 13 | 202511..202611 | -4 | -30 | -0.8 | 7 | 14413 |
| TL3_NT_L_K7_B95G8 | 13 | 202511..202611 | -121 | -241 | 3.1 | 18 | 14413 |
| TL3_NT_L_M7_A90S5 | 13 | 202511..202611 | 195 | 391 | 1.2 | 82 | 14413 |
| TL3_NT_L_M7_A95S10 | 44 | 202304..202611 | 49 | 99 | 2.0 | 37 | 7581 |
| TL3_NT_L_M7_A95S5 | 13 | 202511..202611 | 258 | 516 | 0.0 | 21 | 14413 |
| TL3_NT_L_M7_B95G8 | 13 | 202511..202611 | 222 | 443 | 0.8 | 22 | 14413 |
| TL3_NT_L_P7_A95S5 | 13 | 202511..202611 | 3 | 20 | 0.1 | -7 | 14413 |
| TL3_NT_L_P7_B95G8 | 13 | 202511..202611 | 15 | 39 | -0.3 | -10 | 14413 |
| TL3_NT_SH_A7_k1 | 13 | 202511..202611 | 31 | 63 | -0.4 | -1 | 14413 |
| TL3_NT_SH_A7_k2 | 13 | 202511..202611 | -6 | -5 | -0.2 | 2 | 14413 |
| TL3_NT_SH_A7_k4 | 13 | 202511..202611 | 56 | 112 | -2.1 | 15 | 14413 |
| TL3_NT_SH_K7_k1 | 13 | 202511..202611 | 132 | 265 | -0.8 | -6 | 14413 |
| TL3_NT_SH_K7_k2 | 44 | 202304..202611 | 50 | 100 | 0.3 | 2 | 7581 |
| TL3_NT_SH_K7_k4 | 13 | 202511..202611 | 48 | 97 | 0.1 | 0 | 14413 |
| TL3_NT_SH_M7_k1 | 13 | 202511..202611 | 52 | 103 | 0.0 | 1 | 14413 |
| TL3_NT_SH_M7_k2 | 13 | 202511..202611 | 98 | 195 | 0.2 | 4 | 14413 |
| TL3_NT_SH_M7_k4 | 13 | 202511..202611 | 111 | 222 | -0.2 | 4 | 14413 |
| TL3_NT_SH_P7_k1 | 13 | 202511..202611 | 10 | 14 | -0.0 | 0 | 14413 |
| TL3_NT_SH_P7_k2 | 13 | 202511..202611 | 43 | 79 | -0.2 | 2 | 14413 |
| TL3_NT_SH_P7_k4 | 13 | 202511..202611 | 45 | 86 | -0.1 | 2 | 14413 |

## 4. FULL TABLE WITH CONTROLS (W-NT2, order 2013Z item 4; PREREG_NT2.md sha256 9d09c259eb8a8694; written 2026-11-19 09:21Z)

All numbers: stack-level delta vs the live JL3 stack (TL3_EV_JL3) on the same months, exact engine, every layer ON, base lots at $4.84 RT with the x1.75 live-lot dollars in brackets. Cell format: d stack ulcer % (PRIMARY; negative = better) / d worst week $ (positive = better) / d max drawdown $ (negative = better) / d mean $/wk (x1.75). L6M = 2026-05-14..2026-11-13; L6X = 2026-05-14..2026-10-31 and HOLD = 2025-11-11..2026-05-11 are the windows the controls share (months 202511..202610). Selection caution: the variants were picked as the best of many on the same last 6 months they are judged on; controls B (random lock settings) are the selection null for the K7 lock family; controls A (random half activation) show whether the effect scales with how often the rule is applied, and cannot confer a label (PREREG_NT2.md).

| variant | what it does | L6M | L3M | HOLD | 2025 | 2024 | 2023 | controls B (beats n of N: d mean / d ulcer) | controls A | label | what DS7 needs |
|---|---|---|---|---|---|---|---|---|---|---|---|
| LK_K7_a80_L50 | K7 lock: after the 80% touch of the target, stop to +30 pts (lock line 0.80 / 30.0) | -3.2% / -477 / -2731 / +1011 (+2010) | -0.1% / -477 / -2731 / +2341 (+4729) | -11.8% / +1426 / -8372 / +675 (+1323) | +0.7% / -2274 / +4631 / -431 (-861) RED | +6.7% / -2025 / +733 / -470 (-918) RED | +1.5% / +671 / +3001 / -283 (-566) RED | 28 of 30 / 17 of 30 (controls median d mean +460, d ulcer -5.1%) | none | **WEAK-BUT-POSITIVE** | POLICY FILE only: add one K7 profit-lock line [0.80 of target, +30 pts] (same grammar as the live P7/H7 locks) |
| LKX_K7_a80_L50 | K7 latch-lock (same rule, modelled as a market exit at the first print <= entry+30 after the 80% latch) | pending | pending | -11.6% / +1401 / -9294 / +364 (+701) | +14.3% / -2274 / +15964 / -686 (-1371) RED | +6.0% / -2025 / +872 / -228 (-434) RED | +1.7% / +671 / +2966 / -407 (-813) RED | 25 of 30 / 24 of 30 (controls median d mean +460, d ulcer -5.1%) | n=30: median +665 best +1032, 80% > 0, dose 0.58 | **BEST-AVAILABLE-NOT-PROVEN** | POLICY FILE only (same K7 lock line; the engine models it as a latch exit) |
| LK_K7_a70_L50 | K7 lock 70% / +30 pts | -12.6% / +3303 / -2898 / +696 (+1387) | -13.4% / +3303 / -2898 / +1910 (+3821) | -16.7% / +3268 / -10920 / -985 (-2020) | -9.7% / +2592 / -8866 / -381 (-788) RED | -22.4% / +4156 / -13771 / +261 (+544) GREEN | +8.8% / -1993 / +8083 / +250 (+499) RED | 18 of 30 / 25 of 30 (controls median d mean +460, d ulcer -5.1%) | none | **WEAK-BUT-POSITIVE** | POLICY FILE only |
| SH_K7_k2 | K7 resting target 2 ticks nearer | +0.6% / -70 / +10 / +512 (+1023) | +0.2% / -70 / +10 / +1271 (+2542) | -0.9% / -60 / -5 / +55 (+110) | -0.1% / +165 / +65 / +31 (+62) GREEN | +1.1% / -90 / +170 / +8 (+17) GREEN | +0.3% / -10 / -45 / -12 (-25) AMBER | n/a (not a lock setting) | n=30: median +387 best +615, 83% > 0, dose 0.54 | **WEAK-BUT-POSITIVE** (no selection control B for this family (A cannot confer a label)) | POLICY FILE only (target ticks) |
| SH_K7_k1 | K7 resting target 1 tick nearer | +0.5% / -35 / +45 / +424 (+847) | +0.2% / -35 / +45 / +1045 (+2090) | -1.0% / -30 / +15 / +81 (+162) | pending ? | pending ? | pending ? | n/a (not a lock setting) | none | **WEAK-BUT-POSITIVE** (prior years not landed yet; no selection control B for this family (A cannot confer a label)) | POLICY FILE only |
| SH_K7_k4 | K7 resting target 4 ticks nearer | +1.7% / -85 / +10 / +243 (+485) | +1.9% / -85 / +10 / +846 (+1693) | -0.1% / -100 / +20 / -136 (-271) | pending ? | pending ? | pending ? | n/a (not a lock setting) | n=30: median +236 best +549, 83% > 0, dose 0.46 | **WEAK-BUT-POSITIVE** (prior years not landed yet; no selection control B for this family (A cannot confer a label)) | POLICY FILE only |
| L_M7_A95S5 | M7 latch at 95%, exit after 5 s without a new extreme | -1.2% / -275 / -523 / +207 (+415) | -1.2% / -275 / -523 / +396 (+791) | +0.2% / -110 / +565 / +343 (+685) | pending ? | pending ? | pending ? | n/a (not a lock setting) | none | **WEAK-BUT-POSITIVE** (prior years not landed yet; no selection control B for this family (A cannot confer a label)) | NEW CODE: latched near-target take |
| L_M7_A95S10 | M7 latch at 95%, 10 s stale | -1.2% / -370 / -558 / +177 (+354) | -1.3% / -370 / -558 / +400 (+801) | +0.1% / -100 / +495 / +358 (+715) | +3.0% / -130 / +2157 / -86 (-171) RED | +0.1% / -120 / +85 / +140 (+280) GREEN | +5.2% / -629 / +1355 / -103 (-207) RED | n/a (not a lock setting) | n=30: median +54 best +168, 70% > 0, dose 0.50 | **WEAK-BUT-POSITIVE** (no selection control B for this family (A cannot confer a label)) | NEW CODE: latched near-target take |
| L_M7_A90S5 | M7 latch at 90%, 5 s stale | -1.8% / +1669 / -1444 / +191 (+386) | -3.3% / +1669 / -1444 / +188 (+376) | +1.6% / -200 / +412 / +319 (+637) | pending ? | pending ? | pending ? | n/a (not a lock setting) | none | **WEAK-BUT-POSITIVE** (prior years not landed yet; no selection control B for this family (A cannot confer a label)) | NEW CODE: latched near-target take |
| SH_M7_k2 | M7 resting target 2 ticks nearer | -0.4% / -60 / +30 / +178 (+357) | -0.0% / -60 / +30 / -15 (-29) | +0.2% / +10 / +110 / +22 (+44) | pending ? | pending ? | pending ? | n/a (not a lock setting) | n=30: median +67 best +152, 100% > 0, dose 0.51 | **WEAK-BUT-POSITIVE** (prior years not landed yet; no selection control B for this family (A cannot confer a label)) | POLICY FILE only |
| L_K7_A90S5 | K7 latch at 90%, 5 s stale | +4.8% / +842 / +3062 / +868 (+1713) | +6.8% / +842 / +3062 / +2467 (+4934) | -5.0% / +5039 / -4318 / -241 (-483) | pending ? | pending ? | pending ? | n/a (not a lock setting) | none | **WEAK-BUT-POSITIVE** (prior years not landed yet; no selection control B for this family (A cannot confer a label)) | NEW CODE: latched near-target take |
| PF_K7 | persist-counter fix, K7 delta lock (persist 10) | pending | pending | -8.6% / +12671 / -7330 / -1235 (-2518) | pending ? | pending ? | pending ? | n/a (not a lock setting) | none | **BEST-AVAILABLE-NOT-PROVEN** (prior years not landed yet; no selection control B for this family (A cannot confer a label)) | ONE-LINE CODE FIX at DS7.cs L1790 + policy line |
| PF_M7 | persist-counter fix, M7 step (persist 2) | pending | pending | +1.5% / +560 / +1148 / +546 (+1068) | pending ? | pending ? | pending ? | n/a (not a lock setting) | none | **BEST-AVAILABLE-NOT-PROVEN** (prior years not landed yet; no selection control B for this family (A cannot confer a label)) | ONE-LINE CODE FIX at DS7.cs L1790 + policy line |

### Controls B detail (30 random K7 lock settings, L6X / HOLD; real LK_K7_a80_L50 = a 0.80, L 30 pts)
| set | a | L pts | L6X d mean / d ulcer | HOLD d mean / d ulcer |
|---|---|---|---|---|
| RS10_K7 | 0.872 | 30.4 | +1274 / -3.3% | -477 / -10.7% |
| RS11_K7 | 0.666 | 7.2 | -385 / -7.3% | -1386 / -3.0% |
| RS12_K7 | 0.797 | 14.5 | +470 / -3.2% | +596 / -13.6% |
| RS13_K7 | 0.622 | 30.7 | +657 / -15.3% | -2073 / +6.5% |
| RS14_K7 | 0.61 | 40.2 | -783 / -1.5% | -2249 / -8.0% |
| RS15_K7 | 0.833 | 35.5 | +583 / -1.1% | -281 / -3.1% |
| RS16_K7 | 0.669 | 36.4 | -822 / -5.2% | -1351 / -8.0% |
| RS17_K7 | 0.71 | 5.6 | +670 / -8.9% | -1062 / -1.9% |
| RS18_K7 | 0.636 | 17.5 | +184 / -12.4% | -1408 / +0.0% |
| RS19_K7 | 0.858 | 23.8 | -336 / -2.5% | -705 / -7.2% |
| RS1_K7 | 0.627 | 13.1 | +13 / -13.3% | -1135 / -1.6% |
| RS20_K7 | 0.61 | 35.5 | -530 / -10.3% | -1894 / -7.2% |
| RS21_K7 | 0.874 | 33.6 | +862 / +0.9% | -480 / -13.0% |
| RS22_K7 | 0.839 | 14.2 | -20 / -2.2% | +50 / -7.4% |
| RS23_K7 | 0.883 | 40.3 | +1221 / +0.6% | -141 / -8.1% |
| RS24_K7 | 0.641 | 16.5 | -395 / -9.0% | -921 / -2.9% |
| RS25_K7 | 0.816 | 25.3 | +451 / -8.0% | +572 / -12.9% |
| RS26_K7 | 0.883 | 10.6 | +106 / +1.7% | -504 / -0.6% |
| RS27_K7 | 0.851 | 41.6 | +517 / -4.0% | +559 / -17.8% |
| RS28_K7 | 0.685 | 14.6 | -551 / -8.1% | -403 / -6.9% |
| RS29_K7 | 0.791 | 24.4 | +1053 / -6.9% | -197 / -8.8% |
| RS2_K7 | 0.821 | 6.7 | +227 / -5.0% | -180 / -8.5% |
| RS30_K7 | 0.765 | 29.5 | +1147 / -11.8% | -251 / -13.8% |
| RS3_K7 | 0.791 | 43.5 | +805 / +5.6% | -51 / -17.2% |
| RS4_K7 | 0.601 | 27.7 | +989 / -18.6% | -1867 / -2.3% |
| RS5_K7 | 0.613 | 10.7 | +557 / -13.4% | -2195 / +2.3% |
| RS6_K7 | 0.888 | 43.3 | +711 / +4.5% | -16 / -7.1% |
| RS7_K7 | 0.707 | 1.7 | +361 / -4.9% | -1308 / -2.5% |
| RS8_K7 | 0.869 | 1.0 | -76 / +2.0% | -988 / -1.3% |
| RS9_K7 | 0.711 | 7.2 | +642 / -9.5% | -1116 / -2.8% |

Identity of the control mechanisms: TL3_NT_LKID2 (K7 lock never reachable) vs JL3: 202504 IDENTICAL; 202610 IDENTICAL. Latch/ctrl hook identity: TL3_NT_ID0 (inert latch) = JL3 (section 3).


---
# EARLIER SECTION (kept verbatim, generated 00:46Z, other program)
# DS3_NEAR_TARGET - near-target take, profit side, all books (user order 17:25Z)
Generated 2026-11-18 00:46Z. 184 cells scored (family PHI_NT, U2, live-week gated, null_ver 2). PRE-PROOF. First-order screen; exact (ExhCut) results in the Stage 2 section.

Cells: (1) NT_take: market take (decision at k, execute k+1 at mid -+0.80 pt) once the favourable extreme (print high/low, or mid) is within k ticks of the target (k 1-10) and the extreme is >= s seconds old (s 0-30); policy line `profit <book> * pct>=P secs_ext>=s take`, P = 1 - k*0.25/target (target 60 pt; O7 90). (2) NT_retarget: nominal limit at target -+ k ticks (k 1-8). (3) NT_queue_wall / NT_queue_book: within kt ticks of the target and the target-level wall (>= X x MedLevel) or the ahead_rel / tot_rel book ratio >= thr: market take. The stop-side mirror is not in the grid. Equal lots, no trade removed; reference row = never-cut hold-to-bracket (60/60), not a candidate.

Execution cost: every take that would have filled anyway at the target pays (target - exit price) + 0.80 pt slippage; the net-gain table below shows whether the rescued misses pay for that.

## Frozen live week: targets missed by <= k ticks
186 frozen live trades; the 60-pt (O7 90) target price was touched on the path before the live exit for 9; never touched for 177. Missed by 0 < m <= k ticks (live pnl = what the trade actually earned at its live exit): 
- k=1: 11 trades (P7 5, K7 5, M7 1), live pnl of those 43165 USD, a fill exactly at the target would add 2251 USD over what they earned
- k=2: 25 trades (K7 12, P7 7, M7 3, A7 2, U7 1), live pnl of those 68820 USD, a fill exactly at the target would add 2890 USD over what they earned
- k=3: 32 trades (K7 18, P7 7, M7 4, A7 2, U7 1), live pnl of those 78420 USD, a fill exactly at the target would add 2851 USD over what they earned
- k=5: 42 trades (K7 22, P7 11, M7 6, A7 2, U7 1), live pnl of those 110815 USD, a fill exactly at the target would add 3920 USD over what they earned
- k=8: 54 trades (K7 26, P7 15, M7 7, A7 3, X5 1, H7 1, U7 1), live pnl of those 135235 USD, a fill exactly at the target would add 6989 USD over what they earned
- k=10: 58 trades (K7 26, P7 15, M7 8, A7 6, X5 1, H7 1, U7 1), live pnl of those 136285 USD, a fill exactly at the target would add 10720 USD over what they earned
Note: most of the missed trades already earned at or above target pnl at their live exit, so the live miss gain is small; the live M7 example of today (long 27933.75, target 27993.75, high 27993.50, missed by 1 tick) is outside the frozen file and is quoted from the user only.

### K7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_retarget | k=4 | +870 / +872 / +496 / +415 / +212 / -8 / +147 / -28 | 15455 / 20902 | 23127 / 26707 | 1718 | 0.154 | -375 | CANDIDATE-DD |
| NT_take | k=7 s=30 trigger=mid | -455 / +155 / -29 / +92 / -24 / -323 / -86 / -142 | 15919 / 20902 | 23463 / 26707 | 437 | 0.231 | +1476 | CANDIDATE-DD |
| NT_retarget | k=5 | +632 / +1001 / +538 / +644 / +318 / -111 / +102 / +34 | 15935 / 20902 | 23727 / 26707 | 1957 | 0.108 | -495 | CANDIDATE-DD |
| NT_take | k=8 s=30 trigger=mid | -639 / +236 / +16 / +18 / -52 / -154 / -162 / -95 | 16020 / 20902 | 24054 / 26707 | 534 | 0.169 | +504 | CANDIDATE-DD |
| NT_take | k=7 s=20 trigger=mid | -527 / +116 / -69 / +68 / -49 / -344 / -93 / -147 | 16039 / 20902 | 23623 / 26707 | 514 | 0.385 | +1354 | CANDIDATE-DD |
Net gain per take (best cell, first order, all fired trades of the book): 1718 fired; 1688 would have filled at the target anyway (cost -38720 USD total, -22.9 per take); 30 rescued misses (gain vs their hold-to-bracket exit 71959 USD).

### P7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_retarget | k=8 | +2611 / -2261 / +535 / +1658 / +2001 / -1154 / -358 / -498 | 77449 / 133887 | 111128 / 109442 | 1857 | 0.031 | -3572 | CANDIDATE-DD |
| NT_retarget | k=7 | +3152 / -1728 / +1002 / +623 / +1576 / -1005 / -193 / -322 | 103032 / 133887 | 107618 / 109442 | 1751 | 0.077 | -2977 | CANDIDATE-DD |
| NT_retarget | k=5 | +4486 / -548 / +2034 / +1341 / +1066 / -1139 / -45 / -397 | 107577 / 133887 | 104313 / 109442 | 1483 | 0.077 | -1892 | CANDIDATE-DD |
| NT_retarget | k=6 | +3879 / -1103 / +1516 / +789 / +1144 / -1481 / -39 / -336 | 109867 / 133887 | 105618 / 109442 | 1627 | 0.200 | -2457 | CANDIDATE-DD |
| NT_queue_book | feat=tot_rel_slow kt=5 thr=3.0 | -149 / -75 / +686 / +90 / +35 / -584 / -148 / -162 | 111908 / 133887 | 109442 / 109442 | 46 | 0.031 | +0 | CANDIDATE-DD |
Net gain per take (best cell, first order, all fired trades of the book): 1857 fired; 1812 would have filled at the target anyway (cost -326120 USD total, -180.0 per take); 45 rescued misses (gain vs their hold-to-bracket exit 456629 USD).

### M7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_retarget | k=2 | -70 / -54 / -50 / +145 / +188 / -57 / -36 / -32 | 37775 / 44425 | 51471 / 50321 | 633 | 0.169 | +1930 | CANDIDATE-DD |
| NT_retarget | k=3 | +474 / +496 / +297 / +471 / +323 / -108 / +21 / -61 | 38495 / 44425 | 47811 / 50321 | 864 | 0.262 | +1920 | CANDIDATE-DD |
| NT_take | k=2 s=5 trigger=print | -284 / -135 / -97 / +32 / +16 / -323 / -122 / -89 | 39001 / 44425 | 54601 / 50321 | 243 | 0.046 | +1844 | no |
| NT_retarget | k=4 | +409 / +444 / +246 / +408 / +261 / -175 / +44 / -98 | 39265 / 44425 | 49026 / 50321 | 1039 | 0.262 | +1910 | CANDIDATE-DD |
| NT_queue_book | feat=tot_rel_fast kt=2 thr=1.5 | +0 / -22 / -26 / +41 / -40 / -249 / -51 / -101 | 39468 / 44425 | 51771 / 50321 | 147 | 0.062 | +334 | CANDIDATE-DD |
Net gain per take (best cell, first order, all fired trades of the book): 633 fired; 627 would have filled at the target anyway (cost -7340 USD total, -11.7 per take); 6 rescued misses (gain vs their hold-to-bracket exit 19260 USD).

### U7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_queue_book | feat=ahead_rel_slow kt=5 thr=3.0 | +0 / +0 / +0 / +13 / -30 / -14 / -17 / -3 | 21561 / 21561 | 42226 / 42226 | 26 | 1.000 | +0 | no |
| NT_queue_book | feat=ahead_rel_fast kt=5 thr=3.0 | +0 / +0 / +0 / +34 / -2 / +0 / -47 / -3 | 21561 / 21561 | 43913 / 42226 | 27 | 1.000 | +0 | no |
Net gain per take (best cell, first order, all fired trades of the book): 26 fired; 24 would have filled at the target anyway (cost -8375 USD total, -349.0 per take); 2 rescued misses (gain vs their hold-to-bracket exit 1393 USD).

### A7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_queue_wall | feat=wall_med kt=1 thr=10 | +0 / +0 / +0 / +0 / -3 / +0 / -6 / -3 | 12461 / 12461 | 6089 / 6089 | 22 | 0.862 | +0 | no |
Net gain per take (best cell, first order, all fired trades of the book): 22 fired; 22 would have filled at the target anyway (cost -1044 USD total, -47.5 per take); 0 rescued misses (gain vs their hold-to-bracket exit 0 USD).

### H7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_take | k=3 s=30 trigger=print | -56 / -28 / -44 / +16 / -25 / -28 / -48 / -31 | 13974 / 15477 | 20829 / 20667 | 69 | 0.108 | +0 | CANDIDATE-DD |
| NT_take | k=4 s=30 trigger=print | -56 / -28 / -56 / +1 / -61 / -74 / -74 / -63 | 13974 / 15477 | 20829 / 20667 | 100 | 0.092 | +0 | CANDIDATE-DD |
| NT_take | k=1 s=30 trigger=print | +0 / +0 / +0 / +0 / -11 / -8 / -10 / -3 | 15477 / 15477 | 20829 / 20667 | 27 | 1.000 | +0 | no |
Net gain per take (best cell, first order, all fired trades of the book): 69 fired; 64 would have filled at the target anyway (cost -14396 USD total, -224.9 per take); 5 rescued misses (gain vs their hold-to-bracket exit 12947 USD).

### O7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_take | k=9 s=5 trigger=mid | +0 / +0 / +0 / +0 / -10 / -6 / -17 / -28 | 7469 / 7469 | 5102 / 5102 | 42 | 1.000 | +0 | no |
| NT_take | k=10 s=10 trigger=mid | +0 / +0 / +0 / +0 / -7 / +0 / -19 / -22 | 7469 / 7469 | 5102 / 5102 | 37 | 1.000 | +0 | no |
| NT_take | k=5 s=5 trigger=print | +0 / +0 / +0 / +0 / -15 / -24 / -15 / -19 | 7469 / 7469 | 5102 / 5102 | 44 | 1.000 | +0 | no |
| NT_take | k=5 s=30 trigger=print | +0 / +0 / +0 / +0 / -12 / -34 / -8 / -12 | 7469 / 7469 | 5102 / 5102 | 20 | 1.000 | +0 | no |
| NT_take | k=8 s=10 trigger=mid | +0 / +0 / +0 / +0 / -4 / +0 / -14 / -22 | 7469 / 7469 | 5102 / 5102 | 30 | 1.000 | +0 | no |
Net gain per take (best cell, first order, all fired trades of the book): 42 fired; 42 would have filled at the target anyway (cost -3954 USD total, -94.2 per take); 0 rescued misses (gain vs their hold-to-bracket exit 0 USD).

### ALL - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_retarget | k=5 | +5069 / +1862 / +3341 / +2517 / +1807 / -640 / +215 / -426 | 109631 / 121381 | 133965 / 152455 | 5901 | 0.169 | -588 | CANDIDATE-DD |
| NT_retarget | k=6 | +4055 / +943 / +2480 / +1657 / +1711 / -881 / +130 / -227 | 111081 / 121381 | 135360 / 152455 | 6443 | 0.262 | +1643 | CANDIDATE-DD |
| NT_retarget | k=7 | +2885 / -36 / +1619 / +1275 / +1897 / -707 / +84 / -353 | 112731 / 121381 | 124625 / 152455 | 6903 | 0.292 | +843 | CANDIDATE-DD |
| NT_retarget | k=8 | +1980 / -928 / +800 / +2204 / +2165 / -972 / -182 / -610 | 114131 / 121381 | 126165 / 152455 | 7294 | 0.385 | -62 | CANDIDATE-DD |
| NT_queue_book | feat=tot_rel_fast kt=1 thr=3.0 | -28 / +0 / -9 / +58 / -6 / -35 / -31 / -156 | 121381 / 121381 | 153084 / 152455 | 34 | 1.000 | +0 | no |

## ROLL-EXCL check (the 33 roll-second-bracket trades removed from rule and never-cut reference; key (book, signal second) = /mnt/l2/l2vast/_th_exh/hi/roll_bracket_trades.csv; SZ_BASE_PROOF section 9)
Re-scored cells (family *_RX). Columns: maxDD with / without and mean delta vs never-cut, before -> after exclusion. L6M is unchanged within noise; X' and HOLD move because the roll trades sit in those windows. Stage 2 (engine) numbers still carry the artifact in the engine base (reference and rule alike); not re-run.

| book | technique | params | L6M maxDD before / after | HOLD maxDD before / after | PRE maxDD before / after | X' maxDD before / after | X' mean delta before / after | L6M mean delta before / after |
|---|---|---|---|---|---|---|---|---|
| A7 | NT_take | k=3 s=30 trigger=mid | 12702/12461 -> 12702/12461 | 14224/14181 -> 14224/14181 | 6089/6089 -> 6089/6089 | 14205/13855 -> 14205/13855 | -9 -> -9 | -17 -> -17 |
| H7 | NT_take | k=1 s=30 trigger=print | 15477/15477 -> 15477/15477 | 57978/57397 -> 57978/57397 | 20829/20667 -> 20829/20667 | 34879/34807 -> 34879/34807 | -3 -> -3 | +0 -> +0 |
| P7 | NT_retarget | k=6 | 109867/133887 -> 109867/133887 | 113600/144370 -> 109867/139466 | 105618/109442 -> 96959/109442 | 136792/135949 -> 140318/141816 | -336 -> -336 | +789 -> +789 |
| K7 | NT_take | k=7 s=20 trigger=mid | 16039/20902 -> 16039/20007 | 44384/42831 -> 43124/41571 | 23623/26707 -> 22449/25532 | 46453/44364 -> 46453/44364 | -147 -> -147 | +68 -> +68 |
| O7 | NT_take | k=5 s=30 trigger=print | 7469/7469 -> 7469/7469 | 7469/7469 -> 7469/7469 | 5102/5102 -> 5102/5102 | 14326/14262 -> 14326/14262 | -12 -> -12 | +0 -> +0 |
| U7 | NT_queue_book | feat=ahead_rel_fast kt=5 thr=3.0 | 21561/21561 -> 21561/21561 | 21561/21561 -> 21561/21561 | 43913/42226 -> 43913/42226 | 24317/24437 -> 26707/26827 | -3 -> -3 | +34 -> +34 |
| M7 | NT_take | k=2 s=5 trigger=print | 39001/44425 -> 39001/44425 | 39001/44425 -> 39001/44425 | 54601/50321 -> 54601/50321 | 24591/23241 -> 24591/23241 | -89 -> -89 | +32 -> +32 |
| H7 | NT_take | k=3 s=30 trigger=print | 13974/15477 -> 13974/15477 | 55136/57397 -> 55136/57397 | 20829/20667 -> 20829/20667 | 35864/34807 -> 35864/34807 | -31 -> -31 | +16 -> +16 |
| O7 | NT_take | k=5 s=5 trigger=print | 7469/7469 -> 7469/7469 | 7469/7469 -> 7469/7469 | 5102/5102 -> 5102/5102 | 14536/14262 -> 14536/14262 | -19 -> -19 | +0 -> +0 |
| H7 | NT_take | k=4 s=30 trigger=print | 13974/15477 -> 13974/15477 | 56711/57397 -> 56711/57397 | 20829/20667 -> 20829/20667 | 36525/34807 -> 36525/34807 | -63 -> -63 | +1 -> +1 |
| O7 | NT_take | k=8 s=10 trigger=mid | 7469/7469 -> 7469/7469 | 7469/7469 -> 7469/7469 | 5102/5102 -> 5102/5102 | 14720/14262 -> 14720/14262 | -22 -> -22 | +0 -> +0 |
| P7 | NT_retarget | k=8 | 77449/133887 -> 77449/133887 | 106265/144370 -> 101361/139466 | 111128/109442 -> 102469/109442 | 127957/135949 -> 131484/141816 | -498 -> -498 | +1658 -> +1658 |
| A7 | NT_retarget | k=8 | 12661/12461 -> 12661/12461 | 13232/14181 -> 13232/14181 | 6089/6089 -> 6089/6089 | 12000/13855 -> 12000/13855 | -53 -> -53 | -11 -> -11 |
| M7 | NT_retarget | k=3 | 38495/44425 -> 38495/44425 | 38495/44425 -> 38495/44425 | 47811/50321 -> 47811/50321 | 24081/23241 -> 24081/23241 | -61 -> -61 | +471 -> +471 |
| U7 | NT_take | k=2 s=10 trigger=mid | 21561/21561 -> 21561/21561 | 21561/21561 -> 21561/21561 | 42308/42226 -> 42308/42226 | 24828/24437 -> 27218/26827 | -7 -> -7 | -12 -> -12 |
| O7 | NT_take | k=10 s=10 trigger=mid | 7469/7469 -> 7469/7469 | 7469/7469 -> 7469/7469 | 5102/5102 -> 5102/5102 | 14707/14262 -> 14707/14262 | -22 -> -22 | +0 -> +0 |
| K7 | NT_take | k=7 s=30 trigger=mid | 15919/20902 -> 15919/20007 | 44146/42831 -> 42886/41571 | 23463/26707 -> 22288/25532 | 46532/44364 -> 46532/44364 | -142 -> -142 | +92 -> +92 |
| A7 | NT_take | k=2 s=0 trigger=mid | 12461/12461 -> 12461/12461 | 14295/14181 -> 14295/14181 | 6089/6089 -> 6089/6089 | 14011/13855 -> 14011/13855 | -7 -> -7 | -7 -> -7 |
| U7 | NT_retarget | k=1 | 21561/21561 -> 21561/21561 | 21561/21561 -> 21561/21561 | 42271/42226 -> 42271/42226 | 24517/24437 -> 26907/26827 | -7 -> -7 | -11 -> -11 |
| A7 | NT_retarget | k=1 | 12476/12461 -> 12476/12461 | 14221/14181 -> 14221/14181 | 6089/6089 -> 6089/6089 | 13885/13855 -> 13885/13855 | -2 -> -2 | -7 -> -7 |
| P7 | NT_retarget | k=7 | 103032/133887 -> 103032/133887 | 106405/144370 -> 103032/139466 | 107618/109442 -> 98959/109442 | 124227/135949 -> 127753/141816 | -322 -> -322 | +623 -> +623 |
| K7 | NT_retarget | k=5 | 15935/20902 -> 15935/20007 | 42411/42831 -> 41151/41571 | 23727/26707 -> 22552/25532 | 45389/44364 -> 45389/44364 | +34 -> +34 | +644 -> +644 |
| P7 | NT_retarget | k=5 | 107577/133887 -> 107577/133887 | 125987/144370 -> 121083/139466 | 104313/109442 -> 95654/109442 | 142382/135949 -> 145908/141816 | -397 -> -397 | +1341 -> +1341 |
| M7 | NT_queue_book | feat=tot_rel_fast kt=2 thr=1.5 | 39468/44425 -> 39468/44425 | 39468/44425 -> 39468/44425 | 51771/50321 -> 51771/50321 | 23708/23241 -> 23708/23241 | -101 -> -101 | +41 -> +41 |
| O7 | NT_take | k=9 s=5 trigger=mid | 7469/7469 -> 7469/7469 | 7469/7469 -> 7469/7469 | 5102/5102 -> 5102/5102 | 14894/14262 -> 14894/14262 | -28 -> -28 | +0 -> +0 |
| H7 | NT_take | k=3 s=10 trigger=mid | 15477/15477 -> 15477/15477 | 58193/57397 -> 58193/57397 | 20706/20667 -> 20706/20667 | 35138/34807 -> 35138/34807 | -9 -> -9 | -2 -> -2 |
| U7 | NT_queue_book | feat=ahead_rel_slow kt=5 thr=3.0 | 21561/21561 -> 21561/21561 | 21561/21561 -> 21561/21561 | 42226/42226 -> 42226/42226 | 24312/24437 -> 26702/26827 | -3 -> -3 | +13 -> +13 |
| U7 | NT_take | k=2 s=2 trigger=mid | 21561/21561 -> 21561/21561 | 21561/21561 -> 21561/21561 | 42293/42226 -> 42293/42226 | 24798/24437 -> 27188/26827 | -3 -> -3 | -10 -> -10 |
| A7 | NT_take | k=2 s=2 trigger=mid | 12461/12461 -> 12461/12461 | 14214/14181 -> 14214/14181 | 6089/6089 -> 6089/6089 | 14047/13855 -> 14047/13855 | -6 -> -6 | -4 -> -4 |
| H7 | NT_take | k=2 s=2 trigger=mid | 15477/15477 -> 15477/15477 | 57693/57397 -> 57693/57397 | 20667/20667 -> 20667/20667 | 35123/34807 -> 35123/34807 | -7 -> -7 | -3 -> -3 |
| K7 | NT_take | k=8 s=30 trigger=mid | 16020/20902 -> 16020/20007 | 40464/42831 -> 39204/41571 | 24054/26707 -> 22879/25532 | 45130/44364 -> 45130/44364 | -95 -> -95 | +18 -> +18 |
| P7 | NT_queue_book | feat=tot_rel_slow kt=5 thr=3.0 | 111908/133887 -> 111908/133887 | 152750/144370 -> 147846/139466 | 109442/109442 -> 109442/109442 | 142292/135949 -> 147445/141816 | -162 -> -162 | +90 -> +90 |
| K7 | NT_retarget | k=4 | 15455/20902 -> 15455/20007 | 41841/42831 -> 40581/41571 | 23127/26707 -> 21952/25532 | 45104/44364 -> 45104/44364 | -28 -> -28 | +415 -> +415 |
| M7 | NT_retarget | k=4 | 39265/44425 -> 39265/44425 | 39265/44425 -> 39265/44425 | 49026/50321 -> 49026/50321 | 24641/23241 -> 24641/23241 | -98 -> -98 | +408 -> +408 |
| M7 | NT_retarget | k=2 | 37775/44425 -> 37775/44425 | 37775/44425 -> 37775/44425 | 51471/50321 -> 51471/50321 | 23671/23241 -> 23671/23241 | -32 -> -32 | +145 -> +145 |

## Per-session best cell (drawdown-first, L6M mean >= never-cut, nfire >= 20)
- K7 session 1: NT_retarget k=7  L6M maxDD 11452 / 14952, L6M mean +181, PRE mean -5, nfire 538
- K7 session 3: NT_retarget k=5  L6M maxDD 19275 / 23185, L6M mean +43, PRE mean -27, nfire 453
- K7 session 4: NT_queue_wall feat=wall_med kt=5 thr=10  L6M maxDD 6369 / 6369, L6M mean +0, PRE mean -23, nfire 35
- P7 session 0: NT_retarget k=8  L6M maxDD 92850 / 116210, L6M mean +919, PRE mean -271, nfire 849
- P7 session 3: NT_take k=9 s=5 trigger=print  L6M maxDD 55529 / 86629, L6M mean +564, PRE mean -500, nfire 288
- M7 session 1: NT_retarget k=1  L6M maxDD 31193 / 38178, L6M mean +86, PRE mean -7, nfire 232
- M7 session 3: NT_queue_book feat=ahead_rel_fast kt=3 thr=3.0  L6M maxDD 11379 / 11667, L6M mean +11, PRE mean -1, nfire 20
- U7 session 0: NT_queue_wall feat=wall_med kt=2 thr=10  L6M maxDD 10073 / 9906, L6M mean +0, PRE mean -14, nfire 21
- U7 session 1: NT_take k=2 s=30 trigger=print  L6M maxDD 32749 / 32749, L6M mean +0, PRE mean -29, nfire 24
- A7 session 0: NT_queue_wall feat=wall_med kt=1 thr=10  L6M maxDD 12461 / 12461, L6M mean +0, PRE mean -6, nfire 22
- H7 session 0: NT_queue_wall feat=wall_med kt=3 thr=10  L6M maxDD 14606 / 14606, L6M mean +0, PRE mean -13, nfire 25
- H7 session 3: NT_take k=3 s=0 trigger=mid  L6M maxDD 3762 / 3762, L6M mean +0, PRE mean -5, nfire 26
- O7 session 3: NT_take k=9 s=5 trigger=mid  L6M maxDD 7469 / 7469, L6M mean +0, PRE mean -17, nfire 42

## Plain sentences per book (profit, near-target)
K7 profit (near-target): NT_retarget (k=4); L6M maxDD 20902 -> 15455, L6M mean +415 USD/wk, PRE maxDD 26707 -> 23127, PRE mean +147, placebo p 0.154, live week -375 USD (15 fired); CANDIDATE-DD.

P7 profit (near-target): NT_retarget (k=8); L6M maxDD 133887 -> 77449, L6M mean +1658 USD/wk, PRE maxDD 109442 -> 111128, PRE mean -358, placebo p 0.031, live week -3572 USD (19 fired); CANDIDATE-DD.

M7 profit (near-target): NT_retarget (k=2); L6M maxDD 44425 -> 37775, L6M mean +145 USD/wk, PRE maxDD 50321 -> 51471, PRE mean -36, placebo p 0.169, live week +1930 USD (2 fired); CANDIDATE-DD.

U7 profit (near-target): NT_queue_book (feat=ahead_rel_slow kt=5 thr=3.0); L6M maxDD 21561 -> 21561, L6M mean +13 USD/wk, PRE maxDD 42226 -> 42226, PRE mean -17, placebo p 1.000, live week +0 USD (0 fired); no.

A7 profit (near-target): NT_queue_wall (feat=wall_med kt=1 thr=10); L6M maxDD 12461 -> 12461, L6M mean +0 USD/wk, PRE maxDD 6089 -> 6089, PRE mean -6, placebo p 0.862, live week +0 USD (0 fired); no.

H7 profit (near-target): NT_take (k=3 s=30 trigger=print); L6M maxDD 15477 -> 13974, L6M mean +16 USD/wk, PRE maxDD 20667 -> 20829, PRE mean -48, placebo p 0.108, live week +0 USD (0 fired); CANDIDATE-DD.

O7 profit (near-target): NT_take (k=9 s=5 trigger=mid); L6M maxDD 7469 -> 7469, L6M mean +0 USD/wk, PRE maxDD 5102 -> 5102, PRE mean -17, placebo p 1.000, live week +0 USD (0 fired); no.

ALL profit (near-target): NT_retarget (k=5); L6M maxDD 121381 -> 109631, L6M mean +2517 USD/wk, PRE maxDD 152455 -> 133965, PRE mean +215, placebo p 0.169, live week -588 USD (37 fired); CANDIDATE-DD.

## Policy lines (D7 grammar, best cell per book; fields the grammar lacks marked)
- profit K7 * retarget -4 ticks
- profit P7 * retarget -8 ticks
- profit M7 * retarget -2 ticks
- profit U7 * within 5 ticks of target and ahead_rel_slow>=3.0 take at market   # needs: wall/ahead gate on take
- profit A7 * within 1 ticks of target and wall_med>=10 take at market   # needs: wall/ahead gate on take
- profit H7 * pct>=0.9875 secs_ext>=30 take   (k=3 ticks, print trigger)
- profit O7 * pct>=0.9750 secs_ext>=5 take   (k=9 ticks, mid trigger)