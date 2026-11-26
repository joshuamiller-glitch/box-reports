# Q7 TIME OF SESSION (W-QASIA, QUICK SCREEN re-simulation, 2026-11-26)

**ANSWER FIRST** (rule N>=100, t>=3 baskets, per book per week, held weeks 2023-10 to 2026-10, out of sample; t>=4 table below agrees in sign unless noted):
- **London: no part of the session is positive.** Whole session -$77 per book per week (t -1.2; L6M -$107, L3M -$267). By hour: 02 -2, 03 -34 (t -1.7), 04 -7, 05 -11, 06 +1, 07 -8, 08 -15 (t -2.3). Nothing is positive over all weeks AND L6M AND L3M. Hour 02 is +$46 in L6M but -$28 in L3M and -$2 overall; hours 03 and 08 are marginally positive in L6M only (+$10, +$6). By weekday every day is negative overall except Monday (+$8, L3M -$208); Friday is positive in L6M and L3M (+$51, +$18) but -$16 overall. The t>=4 London basket (30 books) is also negative (-$81). No time filter turns London positive.
- **Asia: the income is made in the first two hours and on Monday; Tuesday loses.** Whole session +$167 per book per week (t 2.2; L6M +$236, L3M +$99). Hour 18 (the 18:00 ET open) +$80 (t 1.6, L6M +$149), hour 19 +$47 (t 2.1), 20:00 ET +$16 but L6M -$140 / L3M -$180, 22:00 -$14, midnight hour +$14 (L6M +$84). By weekday Monday +$89 (t 2.1, L6M +$208), Tuesday -$60 (t -2.1, negative in 2024, 2025 and 2026), Wed +$65, Thu +$59, Fri +$14. The 20:00 ET hour has turned negative recently in both rules.
- **NY AM: all of it is the first 30 minutes after 09:30.** Hour 09 (09:30-10:00) +$143 per book (t 1.7) overall but -$159 in L6M; hour 10 -$70, hour 11 -$23. The whole t>=3 basket is flat (+$49, t 0.4; L6M -$340 per book). Mon positive, Thu/Fri negative in L6M. t>=4 basket: hour 09 +$206, hours 10-11 negative.
- **NY PM: hour 12 (12:00-13:00) is the positive part** (+$57, t 1.3, L6M +$192); 13-15 are weak (-$27, -$17, -$21 overall; 15:00 hour positive in L6M +$74). Whole session -$9 (t>=3), +$205 (t>=4, 22 books). Thursday -$38 overall but +$176 in L6M: do not trust.
- Weekday patterns do not repeat across sessions or windows (Asia Tue negative, NY AM Mon positive, NY PM Thu flip), so no weekday filter is supported. Hour-of-session patterns are better: the first hour or two of Asia and NY AM carry the edge, London has none.

**HINDSIGHT / READ THIS**: each slice has about 30 weeks of L6M and 160 weeks overall, 4 sessions x 2 rules x (3 to 8 hours + 5 weekdays) are about 100 slices; with t near 2 a few will look good by chance. Baskets are the Test 4 baskets (very large for t>=3: Asia 1,227 books held on average; quick-screen levels, ranks and signs are the information). This page makes no trade rule; it only says where the Test 4 baskets earned.

**METHOD**: the stored grid has weekly bins only, so the cells of every Test 4 basket ever held (33,445 cells, 8,686 grid jobs) were re-simulated on server C with the SAME engine (gcore2x, same fills, costs, one position at a time) with only the week bin replaced by (week, ET clock hour of the signal bar) and (week, trading weekday). Validated: the hour-summed weekly series equals the stored grid weekly series (max difference below 1e-3 points on 4 cells; exact count match). Code code/th_q7 (hour_run.py, q7_report.py); outputs on server C /mnt/l2/l2vast/_q7/out. 4 of 8,686 jobs failed (module errors on bar sizes with 1-bar windows or a changed param list): cells with no re-sim are listed per table (at most 15 of 24,368). Held weeks, one cell per book and family, equal weight, 1 lot, are exactly the Test 4 log (weeks 26..185). Session windows: Asia 18:00-02:00 ET, London 02:00-08:30, NY AM 09:30-12:00, NY PM 12:00-16:00; hour 08 of London is 08:00-08:30 and hour 09 of NY AM is 09:30-10:00 only.


Basket = the Test 4 qualified basket (equal weight, 1 lot per book, one cell per book and family, re-qualified every 13 weeks, only data before each date; the weeks shown are the held weeks 26..185 = 2023-10 to 2026-10, so every number is out of sample for the qualification). Rows: hour = ET clock hour of the signal bar (Asia 18-01, London 02-08, NY AM 09-11 with 09:30 start, NY PM 12-15; 08:xx and 09:00-09:29 are outside the session codes). $ per week for the WHOLE basket (sum over the books held) and per book (basket / mean books held). t = mean weekly / (sd / sqrt(weeks)) over the 160 held weeks. Cost 4.84 USD/RT included, same engine and same fills as the grid (gcore2x), validated to the stored weekly cells to <1e-3 points. Only the week bin was changed to (week, hour) and (week, weekday); no engine change.

HINDSIGHT/CAVEAT: this is a descriptive screen of the baskets. Slicing a session by hour (about 3-8 slices x 2 rules x 4 sessions, plus 5 weekdays) is a multiple-comparison family: a single hour with |t| near 2 means little; consistent sign across rules and windows means more. Quick-screen dollars run below exact on live books (about 0.7-0.9 of quick for rotation picks, 1.5x lower on live books: levels uncertain, signs and ranks are the information).


## Rule N>=100, t>=3


### Asia, N>=100, t>=3 (books held mean 1227; cells with no re-sim 11 of 16596)

Whole session, per book: $167/wk, t 2.2, L6M $236, L3M $99 (basket total $155994/wk).

| hour ET | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | $/trade | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 18 | 1.89 | 80 | 1.6 | 149 | 125 | 76 | 15 | 157 | 31.8 | 72022 |
| 19 | 0.74 | 47 | 2.1 | 57 | 17 | 69 | 40 | 49 | 63.5 | 59662 |
| 20 | 0.88 | 16 | 0.6 | -140 | -180 | 70 | 41 | -74 | -22.2 | -28883 |
| 21 | 0.57 | 16 | 1.0 | 47 | -13 | 24 | 22 | 8 | 28.2 | 24343 |
| 22 | 0.38 | -14 | -1.3 | -29 | -36 | -13 | -4 | -29 | -47.3 | -27725 |
| 23 | 0.30 | 4 | 0.5 | 61 | 42 | -4 | 7 | 16 | 22.6 | 10536 |
| 00 | 0.29 | 14 | 1.4 | 84 | 95 | 9 | -19 | 68 | 88.7 | 39392 |
| 01 | 0.40 | 4 | 0.6 | 7 | 49 | 9 | 2 | 3 | 10.8 | 6655 |

(other hours with trades, outside the nominal window: [2], $0/wk per book)


| weekday | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|
| Mon | 1.25 | 89 | 2.1 | 208 | 217 | 40 | 91 | 158 | 119519 |
| Tue | 1.02 | -60 | -2.1 | -85 | -153 | -25 | -114 | -66 | -96131 |
| Wed | 1.03 | 65 | 1.6 | -10 | -4 | 124 | 23 | 57 | 91043 |
| Thu | 1.11 | 59 | 1.6 | 71 | 0 | 102 | 86 | 5 | 37471 |
| Fri | 1.03 | 14 | 0.4 | 52 | 39 | -2 | 18 | 44 | 4093 |

Weekday = trading day (ET clock + 6 h, so the Sunday 18:00 Asia open counts as Monday). Per book = the week basket divided by the books held that week.

### London, N>=100, t>=3 (books held mean 338; cells with no re-sim 0 of 4277)

Whole session, per book: $-77/wk, t -1.2, L6M $-107, L3M $-267 (basket total $-33411/wk).

| hour ET | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | $/trade | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 02 | 1.84 | -2 | -0.1 | 46 | -28 | 24 | 47 | -18 | -19.6 | -13498 |
| 03 | 1.04 | -34 | -1.7 | 10 | -38 | -52 | -40 | -5 | -40.1 | -14851 |
| 04 | 0.79 | -7 | -0.4 | -82 | -111 | 38 | -10 | -54 | -2.3 | -567 |
| 05 | 0.55 | -11 | -0.8 | -61 | -45 | 23 | -44 | -21 | -13.5 | -2277 |
| 06 | 0.54 | 1 | 0.0 | -22 | -25 | 24 | -24 | 3 | 7.1 | 1134 |
| 07 | 0.74 | -8 | -0.4 | -5 | -29 | 1 | -29 | -2 | 3.4 | 734 |
| 08 | 0.43 | -15 | -2.3 | 6 | 9 | -7 | -38 | 4 | -31.9 | -4088 |

| weekday | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|
| Mon | 1.22 | 8 | 0.3 | -30 | -208 | -40 | 38 | 42 | -4246 |
| Tue | 1.18 | -9 | -0.4 | -4 | 71 | 30 | -42 | -8 | -3829 |
| Wed | 1.13 | -21 | -1.0 | -31 | -18 | -8 | 13 | -42 | -12722 |
| Thu | 1.19 | -39 | -1.4 | -93 | -131 | 71 | -82 | -114 | -7258 |
| Fri | 1.19 | -16 | -0.6 | 51 | 18 | -3 | -64 | 30 | -5356 |

Weekday = trading day (ET clock + 6 h, so the Sunday 18:00 Asia open counts as Monday). Per book = the week basket divided by the books held that week.

### NYAM, N>=100, t>=3 (books held mean 1911; cells with no re-sim 15 of 24368)

Whole session, per book: $49/wk, t 0.4, L6M $-340, L3M $14 (basket total $3867/wk).

| hour ET | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | $/trade | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 09 | 4.85 | 143 | 1.7 | -159 | 25 | 184 | 321 | -84 | 25.7 | 258052 |
| 10 | 3.89 | -70 | -1.2 | -61 | 38 | -44 | -44 | -154 | -26.1 | -208058 |
| 11 | 2.25 | -23 | -0.6 | -120 | -49 | 4 | -11 | -84 | -9.9 | -45916 |

(other hours with trades, outside the nominal window: [12, 18], $0/wk per book)


| weekday | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|
| Mon | 2.04 | 74 | 1.4 | 104 | 355 | -68 | 177 | 126 | 181541 |
| Tue | 2.14 | 17 | 0.3 | 190 | 194 | 36 | -36 | 19 | -37397 |
| Wed | 2.09 | 4 | 0.1 | -251 | -95 | 92 | 51 | -132 | -17376 |
| Thu | 2.32 | -27 | -0.5 | -235 | -216 | 16 | 76 | -142 | -37107 |
| Fri | 2.39 | -20 | -0.4 | -147 | -224 | 67 | -2 | -192 | -85794 |

Weekday = trading day (ET clock + 6 h, so the Sunday 18:00 Asia open counts as Monday). Per book = the week basket divided by the books held that week.

### NYPM, N>=100, t>=3 (books held mean 291; cells with no re-sim 0 of 3690)

Whole session, per book: $-9/wk, t -0.1, L6M $270, L3M $200 (basket total $-13069/wk).

| hour ET | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | $/trade | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 12 | 3.36 | 57 | 1.3 | 192 | 91 | 55 | 79 | 78 | 15.3 | 15269 |
| 13 | 1.74 | -27 | -1.1 | 50 | 22 | -16 | -52 | -35 | -10.0 | -5150 |
| 14 | 1.60 | -17 | -0.7 | -46 | -58 | -39 | 57 | -80 | -16.5 | -7976 |
| 15 | 1.86 | -21 | -1.0 | 74 | 144 | -88 | 10 | 17 | -27.1 | -15185 |

(other hours with trades, outside the nominal window: [16, 18], $0/wk per book)


| weekday | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|
| Mon | 1.43 | 24 | 1.1 | 5 | 80 | -16 | 89 | 8 | 4817 |
| Tue | 1.66 | -10 | -0.3 | 25 | -153 | 37 | -28 | -48 | 1042 |
| Wed | 1.97 | 5 | 0.2 | 87 | 64 | -9 | -2 | 22 | -1717 |
| Thu | 1.86 | -38 | -1.3 | 176 | 172 | -46 | -57 | 17 | -15736 |
| Fri | 1.63 | 10 | 0.4 | -23 | 37 | -53 | 90 | -20 | -1475 |

Weekday = trading day (ET clock + 6 h, so the Sunday 18:00 Asia open counts as Monday). Per book = the week basket divided by the books held that week.

## Rule N>=100, t>=4


### Asia, N>=100, t>=4 (books held mean 150; cells with no re-sim 1 of 2120)

Whole session, per book: $162/wk, t 1.7, L6M $367, L3M $180 (basket total $18435/wk).

| hour ET | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | $/trade | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 18 | 1.80 | 111 | 1.8 | 224 | 184 | 96 | 20 | 224 | 54.4 | 13333 |
| 19 | 0.66 | 20 | 0.7 | 86 | 46 | 17 | 4 | 60 | 64.7 | 6464 |
| 20 | 0.75 | 23 | 0.8 | -106 | -159 | 66 | 52 | -58 | -43.7 | -5968 |
| 21 | 0.47 | 8 | 0.5 | 20 | -24 | 24 | 36 | -38 | -6.6 | -584 |
| 22 | 0.31 | -15 | -1.5 | -22 | -36 | -12 | -2 | -36 | -57.5 | -3476 |
| 23 | 0.23 | 6 | 0.6 | 87 | 32 | -2 | 4 | 24 | 51.7 | 2447 |
| 00 | 0.24 | 7 | 0.8 | 82 | 91 | 6 | -23 | 55 | 121.6 | 5399 |
| 01 | 0.32 | 3 | 0.4 | -3 | 45 | 3 | 5 | 0 | 12.7 | 818 |

| weekday | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|
| Mon | 1.09 | 101 | 2.0 | 320 | 308 | 52 | 73 | 213 | 18975 |
| Tue | 0.90 | -83 | -2.2 | -128 | -196 | -60 | -107 | -134 | -13886 |
| Wed | 0.92 | 69 | 1.4 | 12 | -57 | 83 | 30 | 107 | 11461 |
| Thu | 0.97 | 45 | 1.1 | 99 | -50 | 84 | 83 | -20 | -782 |
| Fri | 0.90 | 31 | 0.8 | 64 | 176 | 37 | 16 | 65 | 2668 |

Weekday = trading day (ET clock + 6 h, so the Sunday 18:00 Asia open counts as Monday). Per book = the week basket divided by the books held that week.

### London, N>=100, t>=4 (books held mean 30; cells with no re-sim 0 of 371)

Whole session, per book: $-81/wk, t -0.9, L6M $51, L3M $-135 (basket total $-3655/wk).

| hour ET | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | $/trade | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 02 | 1.48 | -37 | -0.8 | 144 | 74 | -45 | -33 | 43 | -42.7 | -2551 |
| 03 | 0.89 | -32 | -1.0 | -36 | 32 | -24 | -74 | -1 | -22.9 | -718 |
| 04 | 0.63 | 15 | 0.5 | -144 | -190 | 89 | 59 | -113 | 37.5 | 695 |
| 05 | 0.45 | -6 | -0.3 | 65 | 77 | 6 | -23 | 0 | -71.3 | -894 |
| 06 | 0.39 | -19 | -0.8 | -69 | -182 | -5 | -24 | -41 | -8.9 | -102 |
| 07 | 0.58 | -2 | -0.1 | 99 | 101 | -30 | -28 | 55 | 7.5 | 125 |
| 08 | 0.35 | 0 | 0.0 | -7 | -48 | -11 | -6 | 25 | -22.0 | -210 |

| weekday | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|
| Mon | 0.94 | -8 | -0.2 | -17 | -198 | -54 | 49 | -7 | -1984 |
| Tue | 0.97 | 29 | 0.8 | 160 | 205 | 8 | 1 | 88 | 635 |
| Wed | 0.89 | -40 | -1.3 | -57 | -64 | 2 | -25 | -62 | -1994 |
| Thu | 1.01 | -64 | -1.4 | -124 | -276 | 15 | -107 | -109 | -991 |
| Fri | 0.95 | 2 | 0.1 | 89 | 198 | 10 | -47 | 57 | 679 |

Weekday = trading day (ET clock + 6 h, so the Sunday 18:00 Asia open counts as Monday). Per book = the week basket divided by the books held that week.

### NYAM, N>=100, t>=4 (books held mean 228; cells with no re-sim 0 of 2900)

Whole session, per book: $148/wk, t 1.2, L6M $-128, L3M $97 (basket total $19838/wk).

| hour ET | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | $/trade | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 09 | 4.18 | 227 | 2.5 | 42 | 120 | 227 | 413 | 62 | 45.0 | 46992 |
| 10 | 3.11 | -70 | -1.2 | -51 | 102 | -47 | -66 | -124 | -33.2 | -25682 |
| 11 | 1.82 | -9 | -0.2 | -120 | -125 | 17 | 25 | -91 | -3.2 | -1473 |

| weekday | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|
| Mon | 1.72 | 119 | 2.2 | 211 | 434 | -46 | 190 | 231 | 30778 |
| Tue | 1.77 | 45 | 0.8 | 240 | 251 | 71 | -26 | 65 | 61 |
| Wed | 1.73 | 48 | 0.8 | -191 | -48 | 126 | 134 | -116 | 8019 |
| Thu | 1.92 | -25 | -0.5 | -182 | -155 | -11 | 94 | -104 | -4118 |
| Fri | 1.97 | -40 | -0.7 | -205 | -386 | 57 | -20 | -228 | -14902 |

Weekday = trading day (ET clock + 6 h, so the Sunday 18:00 Asia open counts as Monday). Per book = the week basket divided by the books held that week.

### NYPM, N>=100, t>=4 (books held mean 22; cells with no re-sim 0 of 284)

Whole session, per book: $205/wk, t 1.4, L6M $535, L3M $305 (basket total $3676/wk).

| hour ET | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | $/trade | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 12 | 3.43 | 180 | 1.8 | 255 | 38 | 157 | 237 | 165 | 47.7 | 3684 |
| 13 | 1.46 | 43 | 0.7 | 325 | 345 | 15 | 33 | 79 | 22.2 | 729 |
| 14 | 1.31 | 14 | 0.2 | -99 | -199 | -58 | 252 | -171 | -4.1 | -122 |
| 15 | 1.52 | -30 | -0.6 | 53 | 121 | -37 | -5 | -62 | -17.5 | -584 |

(other hours with trades, outside the nominal window: [16], $-2/wk per book)


| weekday | trades/wk per book | $/wk per book | t | L6M | L3M | 2024 | 2025 | 2026 | basket $/wk |
|---|---|---|---|---|---|---|---|---|---|
| Mon | 1.35 | 106 | 1.8 | -10 | 137 | 80 | 251 | 17 | 1765 |
| Tue | 1.51 | 0 | -0.0 | 224 | -158 | 29 | 6 | -52 | 205 |
| Wed | 1.71 | 16 | 0.2 | 90 | -20 | 69 | 23 | -57 | 517 |
| Thu | 1.66 | 28 | 0.5 | 318 | 106 | 9 | -49 | 110 | 663 |
| Fri | 1.50 | 55 | 0.9 | -88 | 240 | -112 | 284 | -15 | 525 |

Weekday = trading day (ET clock + 6 h, so the Sunday 18:00 Asia open counts as Monday). Per book = the week basket divided by the books held that week.