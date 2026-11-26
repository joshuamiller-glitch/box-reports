# TEST 7: is the level edge real, or a rising market? Checks on the Test 5 primary's held baskets, candidate set (3) (W-TEST7)

Written 2026-11-26 21:31Z. **QUICK SCREEN label on every number** (grid tape walk / gcore2x re-simulation, 1 NQ lot per book at $20/point, grid cost in, no stack rules, no account layers; 160 held weeks 2023-10 to 2026-10, weeks 26..185 of the grid). Order: autopilot/DIRECTIVE_TEST7_2115Z.md (relay design under Josh's 18:22Z standing order, not Josh's words). The primary rule is NOT changed: Test 5 primary (N>=100, t>=4, >=75% profitable half-years, family share >=70%, trailing 26 weeks profitable, re-qualify every 13 weeks, hold ALL qualifiers), candidate set (3) = no print-rule bar types and no stale level files, exactly as Test 6 (reproduced here: summed +139 $/lot/wk p 0.072, Asia +148 p 0.070, NY AM +166 p 0.106, NY PM +276 p 0.091, London -127). Held books are the Test 6 walk6 set-3 logs. Code code/th_test7/ ; data on server C /mnt/l2/l2vast/_test7. Plain block bootstrap p (blocks of 4 weeks, 2,000 draws, centred, one-sided, no best-of penalty) for single named rules; the D part and the sub-groups below test many items and carry a Bonferroni / BH note.

## ANSWER FIRST

1. **It is both: about half of the headline is what the same books earn at random entry times in the same weeks (drift plus bracket shape); the part beyond that sits in the level books that trade BOTH sides, not in the long-only books.** Date-shift / random-entry null (200 draws, same side, same bracket, same number of entries per session and week, entry bar redrawn inside the same session and week, same engine): the summed basket earns **+147 $/lot/wk real vs +85 at random entry** (excess **+62**, real beats 99% of the 200 draws, but the paired weekly bootstrap p of the excess is **0.27**). Per session (basket of validated cells): Asia +147 vs +114 (excess +33, beats 83%, p 0.34), London -148 vs +11 (excess -159), NY AM +170 vs +84 (+86, beats 99.5%, p 0.26), NY PM +300 vs +2 (+298, beats 99%, p 0.11; 99 cells, about 8-13 books held).
2. **VERDICT per session, EDGE BEYOND DRIFT (rule fixed before the run: YES = real minus null > 0 AND real beats >= 95% of the draws AND the paired weekly p <= 0.10): Asia NO; London NO; NY AM NO (PARTIAL: beats the draws, excess not significant by week); NY PM NO (PARTIAL, p 0.109, 99 cells); four sessions summed NO (PARTIAL).** No session passes on its own. The Asia list that the primary holds today is mostly a long-NQ-in-a-rising-market list: Asia basket correlation to the NQ Asia session return **+0.59**, **-530 $/lot/wk in the 62 weeks NQ's Asia session fell vs +577 in the 98 weeks it rose**; its long-only books earn +161 vs +142 at random entry (excess +19, beaten 77%).
3. **WHERE the edge beyond drift is: level books that trade both sides.** Summed: **level, both-sides books real +343 vs null +45 (excess +298, beats 100% of the draws, paired p 0.021; L6M +356 vs +21, L3M +482 vs +127; Asia excess +230 p 0.024, NY AM +429 p 0.008)**. Level long-only books: +137 vs +122 (excess +15, beats 68%, p 0.42) = drift. Non-level books: +114 vs +123 (excess -9), non-level both-sides books -63 (random entry earns more than they do). This is a sub-group look (about 8 groups x 5 scopes): Bonferroni for the 8 groups on the summed row gives p 0.17 for level-both, so read it as the best lead, not a proven result.
4. **A, long vs short:** the held books are 966 long-only (share of P&L 33%, +152 $/lot/wk, p 0.046), 36 short-only (-1%, -94, p 0.92, no short book carries anything) and 1,141 both-sides (68%, +191, p 0.073, but max DD $19.0k vs $9.8k for long-only). Level modules: 74% of P&L, +200 (p 0.020); non-level +97 (p 0.21). Asia is 485 long-only of 712 books, 68% of Asia P&L.
5. **C, down markets: yes, the basket loses when NQ falls, almost entirely through the long-only books.** Summed: **-84 $/lot/wk in the 66 weeks NQ's four sessions net negative vs +296 in the 94 positive weeks; -372 in the worst 20 NQ weeks** (only 45% of those weeks positive); correlation 0.22, beta +0.47 $/lot per NQ point. Long-only books: -376 / +523 and **-965 in the worst 20** (corr 0.47, beta ~1.0 = a long NQ position); short-only +213 / -309; both-sides books +244 / +155 and **+287 in the worst 20** (corr 0.00: market-neutral). Level modules +96 / +273 and -80 in the worst 20; non-level modules -252 / +342, -631 in the worst 20. By session: Asia -530 / +577 (corr 0.59), London -712 / +264 (0.41), NY AM -298 / +576 (0.28), NY PM +228 / +322 (0.13, +1,362 in the worst 20 on about 8-13 books).
6. **The benchmark, 1 lot long NQ open to close, each session each day, cost in: Asia +$858/wk (p 0.005), London +426, NY AM +291, NY PM +70; four sessions +$1,644/wk with max DD $68k.** NQ rose in all four sessions over the span, Asia most. These are 5 session-trades a week (about 19.8 for four sessions) against a basket whose books trade fewer, shorter positions, so the dollar sizes are not comparable; the exposure-matched benchmark is the random-entry null in point 1. In relative terms the primary sits far below buy-and-hold in the dollar sum and with about 5x lower max DD ($12.7k vs $68k).
7. **D, which levels (multiple-comparison corrected):** by module, VWAP is **34% of the summed P&L** (+47.8 $/lot/wk contribution, plain p 0.007) and the next four are trendline 10%, channel 8%, prior day 7%, profile nodes 6%; **no single level module survives correction: 40 modules tested, Bonferroni p 0.30 for VWAP, BH q >= 0.30 for all (none at q <= 0.10)**. By action: **break is 59% of P&L (+82.6, plain p 0.004, Bonferroni p 0.036 over 9 actions, q 0.036)**; false_break 9%, retest 6%, reject -0% (-0.2, 135 books earn nothing). By level type: VWAP (34%, Bonferroni p 0.065 over 10 types) and swing S/R + trendline + channel (18%, q 0.12) lead. The level edge is a BREAK edge on VWAP, trendline and channel levels, not a reject/fade edge. London is empty in every cut.
8. **E, stale level modules: no rows needed from me; nothing queued.** Owner W-SHORT (cron status) with W-GRIDOPS (0145Z audit); state in autopilot/SEARCH_STATUS.md 21:15Z: stale real level files Dallas 12 (merge host, fresh 24,825), Frankfurt 1,660 and Singapore 1,657 before their merge. All 52 level modules still have some stale files in the server C grid copy (extracted 16:03Z: 1,095 of 10,274 level files, 10.7%); set (3) already drops every stale file, so Test 5/6/7 numbers do not use them. The list of 13 flagged modules is not published anywhere I could find (only the count "13 of 17" in W-GRIDOPS 0145Z); per-module state is the table in part E. 29 level files are fresh by time but carry a code stamp that differs from today's module code (listed below).

CAVEATS (read before using any number): (a) the null re-simulation reproduces the stored grid weekly points exactly (max diff 0.0) for **1,778 of 2,128** re-simulated cells (83.6%); the other 350 (mostly bar types tsf 199, t3, typ, swing, vfp, lbrk: their bar rows have changed since the grid result was written) are in the ALL table below; 15 cells use own exits (not re-randomisable) and are left out of both. The VALID tables are the headline; the ALL tables give the same picture (summed real +136 vs null +74, excess +62, p 0.25; level both +295 vs +43, excess +252, p 0.028). (b) the null draws the entry BAR uniformly inside the same bar row, session and week (not uniform in clock time for activity bars); signals keep their side, one-position blocking and bracket. (c) the held books were picked on past weeks only; the held weeks are after qualification, so an excess is out of sample for the selection, but the null is not selected so a lucky selection of books that are net long in a rising tape cannot be separated from drift for long-only books. (d) one regime: NQ rose in all four sessions; L6M for the sums is less than 30 independent weeks.

## PART B: DRIFT BENCHMARK (QUICK SCREEN, 200 draws)

**Method and cost.** The cheapest honest way: the SAME gcore2x re-simulation as Q7 (server C, 32 niced processes, table lookups, no engine change), draw 0 = the real signals (validated), draws 1-200 = every signal keeps its side and the cell keeps its bracket, cost and one-position blocking, but the entry bar is redrawn at random among the bars of the same bar row in the SAME week and session. 2,143 held cells, 1,163 grid jobs, 251 bar rows, 201 runs each; 10 minutes wall, about 5 core-hours; nothing queued on the fleet, no exact-engine rows (an exact-engine null of 200 draws on every held cell was not needed for a screen; say the word if you want it queued). Real minus null per week is bootstrapped (paired weekly p).

### B1. Headline: per session and summed, validated cells (draw 0 equals the stored grid)

| scope | group | cells | real $/lot/wk | null mean | real minus null | share of 200 draws real beats | paired weekly bootstrap p | L6M real / null / diff | L6M share beaten | L3M real / null | 2026 real / null | max DD real / null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Four sessions summed | all | 1778 | 147 | 85 | 62 | 0.990 | 0.266 | 120 / 45 / 75 | 0.860 | 248 / 140 | 7 / 144 | 12660 / 5997 |
| Asia | all | 554 | 147 | 114 | 33 | 0.830 | 0.335 | 464 / 14 / 450 | 1.000 | 278 / 46 | 293 / 19 | 9646 / 7862 |
| London | all | 150 | -148 | 11 | -159 | 0.070 | 0.919 | -271 / -25 / -246 | 0.275 | -727 / 95 | -168 / 43 | 24581 / 20428 |
| NY AM | all | 975 | 170 | 84 | 86 | 0.995 | 0.262 | -31 / 134 / -164 | 0.075 | 237 / 305 | -100 / 215 | 20870 / 9877 |
| NY PM | all | 99 | 300 | 2 | 298 | 0.990 | 0.109 | 676 / 220 / 456 | 0.840 | -16 / 272 | -53 / 166 | 26527 / 28843 |

### B2. Summed, by long/both and level/non-level (validated cells; about 8 groups tested, Bonferroni x8)

| scope | group | cells | real $/lot/wk | null mean | real minus null | share of 200 draws real beats | paired weekly bootstrap p | L6M real / null / diff | L6M share beaten | L3M real / null | 2026 real / null | max DD real / null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Four sessions summed | all | 1778 | 147 | 85 | 62 | 0.990 | 0.266 | 120 / 45 / 75 | 0.860 | 248 / 140 | 7 / 144 | 12660 / 5997 |
| Four sessions summed | long only | 795 | 151 | 114 | 37 | 0.940 | 0.295 | 314 / 58 / 256 | 1.000 | 253 / 167 | 293 / 235 | 10620 / 11071 |
| Four sessions summed | both sides | 950 | 209 | 102 | 107 | 0.990 | 0.217 | 99 / 50 / 50 | 0.650 | 276 / 113 | -76 / 118 | 19290 / 4892 |
| Four sessions summed | level modules | 916 | 205 | 47 | 158 | 1.000 | 0.054 | 294 / 12 / 281 | 0.990 | 437 / 108 | 214 / 126 | 10881 / 9896 |
| Four sessions summed | non-level modules | 862 | 114 | 123 | -9 | 0.375 | 0.587 | -27 / 77 / -104 | 0.110 | 90 / 172 | -143 / 163 | 15709 / 5033 |
| Four sessions summed | level both | 470 | 343 | 45 | 298 | 1.000 | 0.021 | 356 / 21 / 335 | 0.970 | 482 / 127 | 213 / 55 | 17622 / 10914 |
| Four sessions summed | level long | 437 | 137 | 122 | 15 | 0.680 | 0.423 | 380 / 51 / 329 | 1.000 | 438 / 135 | 340 / 286 | 15377 / 15276 |
| Four sessions summed | non-level long | 358 | 195 | 113 | 82 | 1.000 | 0.117 | 240 / 70 / 170 | 0.960 | 117 / 224 | 245 / 174 | 9302 / 8454 |
| Four sessions summed | non-level both | 480 | 99 | 162 | -63 | 0.165 | 0.701 | -133 / 77 / -210 | 0.070 | 100 / 106 | -281 / 168 | 23935 / 5586 |

### B3. Per session, by group (validated cells)

| scope | group | cells | real $/lot/wk | null mean | real minus null | share of 200 draws real beats | paired weekly bootstrap p | L6M real / null / diff | L6M share beaten | L3M real / null | 2026 real / null | max DD real / null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | long only | 395 | 161 | 142 | 19 | 0.765 | 0.392 | 425 / 10 / 414 | 1.000 | 260 / 89 | 280 / 73 | 7356 / 8181 |
| Asia | both sides | 157 | 121 | 45 | 75 | 0.775 | 0.300 | 574 / 30 / 545 | 1.000 | 358 / -49 | 728 / 47 | 29475 / 17057 |
| Asia | level modules | 284 | 216 | 139 | 77 | 0.960 | 0.202 | 532 / 25 / 506 | 1.000 | 431 / 39 | 392 / 50 | 7749 / 8790 |
| Asia | non-level modules | 270 | 112 | 77 | 35 | 0.740 | 0.364 | 376 / 4 / 372 | 1.000 | 129 / 67 | 179 / -23 | 10238 / 10491 |
| Asia | level both | 85 | 297 | 68 | 230 | 1.000 | 0.024 | 716 / 23 / 692 | 1.000 | 431 / -76 | 842 / 39 | 13072 / 14065 |
| Asia | level long | 197 | 219 | 174 | 45 | 0.840 | 0.311 | 478 / 42 / 436 | 1.000 | 468 / 119 | 340 / 100 | 7156 / 9892 |
| Asia | non-level long | 198 | 159 | 117 | 42 | 0.860 | 0.334 | 345 / -20 / 364 | 1.000 | 70 / 86 | 205 / 21 | 8734 / 8330 |
| Asia | non-level both | 72 | -90 | 19 | -109 | 0.200 | 0.762 | 457 / 43 / 413 | 0.990 | 267 / -16 | 294 / 46 | 42607 / 21684 |
| London | long only | 51 | 54 | 22 | 32 | 0.620 | 0.375 | -99 / -61 / -37 | 0.475 | -199 / -24 | 42 / 55 | 12984 / 15422 |
| London | both sides | 98 | -151 | -45 | -106 | 0.275 | 0.739 | -282 / 23 / -305 | 0.130 | -747 / 91 | -494 / -117 | 41953 / 37969 |
| London | level modules | 66 | -144 | -3 | -140 | 0.180 | 0.879 | -324 / -10 / -314 | 0.255 | -647 / -20 | -200 / -6 | 29364 / 27031 |
| London | non-level modules | 84 | -123 | -3 | -120 | 0.135 | 0.824 | -236 / -27 / -209 | 0.305 | -657 / 91 | -147 / 42 | 29622 / 20000 |
| London | level both | 61 | -68 | 11 | -79 | 0.340 | 0.685 | -324 / -10 / -314 | 0.255 | -647 / -20 | -200 / -6 | 29364 / 31184 |
| London | level long | 4 | 100 | 24 | 75 | 0.845 | 0.158 | 0 / 0 / 0 | 0.000 | 0 / 0 | 0 / 0 | 19264 / 17378 |
| London | non-level long | 47 | 24 | 14 | 10 | 0.525 | 0.472 | -99 / -61 / -37 | 0.475 | -199 / -24 | 42 / 55 | 14068 / 15675 |
| London | non-level both | 37 | -236 | -50 | -186 | 0.060 | 0.937 | -241 / 20 / -261 | 0.165 | -666 / 85 | -469 / -119 | 38063 / 26277 |
| NY AM | long only | 334 | 133 | 148 | -15 | 0.345 | 0.559 | 61 / 369 / -308 | 0.020 | 230 / 663 | 234 / 589 | 13963 / 16202 |
| NY AM | both sides | 612 | 307 | 122 | 185 | 1.000 | 0.119 | 7 / 75 / -68 | 0.310 | 304 / 216 | -129 / 146 | 24250 / 6098 |
| NY AM | level modules | 500 | 281 | 20 | 260 | 1.000 | 0.048 | 438 / 81 / 357 | 0.920 | 639 / 312 | 309 / 174 | 20306 / 15070 |
| NY AM | non-level modules | 475 | 133 | 157 | -23 | 0.340 | 0.604 | -229 / 171 / -400 | 0.000 | 67 / 304 | -284 / 247 | 23931 / 8185 |
| NY AM | level both | 267 | 490 | 61 | 429 | 1.000 | 0.009 | 484 / 53 / 431 | 0.935 | 741 / 292 | 329 / 79 | 23156 / 12938 |
| NY AM | level long | 227 | 107 | 106 | 1 | 0.515 | 0.496 | 91 / 248 / -157 | 0.300 | 29 / 459 | 159 / 528 | 16367 / 20730 |
| NY AM | non-level long | 107 | 211 | 197 | 15 | 0.590 | 0.426 | 72 / 392 / -320 | 0.040 | 277 / 710 | 370 / 567 | 12120 / 11471 |
| NY AM | non-level both | 345 | 193 | 179 | 14 | 0.565 | 0.509 | -287 / 102 / -388 | 0.020 | 74 / 181 | -376 / 197 | 29043 / 9351 |
| NY PM | long only | 15 | -123 | -39 | -85 | 0.045 | 0.882 | 0 / 0 / 0 | 0.000 | 0 / 0 | -453 / -123 | 26336 / 13087 |
| NY PM | both sides | 83 | 317 | 3 | 314 | 0.990 | 0.098 | 676 / 220 / 456 | 0.840 | -16 / 272 | -36 / 175 | 26081 / 29841 |
| NY PM | level modules | 66 | 272 | 8 | 264 | 0.965 | 0.158 | 676 / 220 / 456 | 0.840 | -16 / 272 | -22 / 180 | 25690 / 30484 |
| NY PM | non-level modules | 33 | -125 | -26 | -99 | 0.205 | 0.800 | 0 / 0 / 0 | 0.000 | 0 / 0 | -426 / -86 | 37592 / 24354 |
| NY PM | level both | 57 | 290 | 0 | 290 | 0.965 | 0.141 | 676 / 220 / 456 | 0.840 | -16 / 272 | -22 / 180 | 25690 / 32487 |
| NY PM | level long | 9 | -37 | 13 | -50 | 0.145 | 0.792 | 0 / 0 / 0 | 0.000 | 0 / 0 | 0 / 0 | 11743 / 9950 |
| NY PM | non-level long | 6 | -67 | -62 | -4 | 0.460 | 0.552 | 0 / 0 / 0 | 0.000 | 0 / 0 | -453 / -123 | 19322 / 13958 |
| NY PM | non-level both | 26 | -120 | -15 | -105 | 0.200 | 0.796 | 0 / 0 / 0 | 0.000 | 0 / 0 | -398 / -49 | 37202 / 27185 |

### B4. Sensitivity: ALL re-simulated cells (real = re-simulated real)

| scope | group | cells | real $/lot/wk | null mean | real minus null | share of 200 draws real beats | paired weekly bootstrap p | L6M real / null / diff | L6M share beaten | L3M real / null | 2026 real / null | max DD real / null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Four sessions summed | all | 2128 | 136 | 74 | 62 | 1.000 | 0.245 | 121 / 22 / 98 | 0.975 | 209 / 94 | 21 / 116 | 11726 / 5610 |
| Asia | all | 706 | 137 | 102 | 35 | 0.860 | 0.323 | 435 / -6 / 441 | 1.000 | 244 / 16 | 270 / -5 | 9270 / 7605 |
| London | all | 196 | -109 | 9 | -118 | 0.060 | 0.893 | 32 / -120 / 152 | 0.755 | -217 / -90 | -58 / -47 | 21441 / 15588 |
| NY AM | all | 1110 | 155 | 75 | 81 | 1.000 | 0.266 | -41 / 121 / -162 | 0.075 | 151 / 279 | -92 / 198 | 19498 / 10520 |
| NY PM | all | 116 | 288 | -2 | 290 | 0.995 | 0.077 | 552 / 182 / 370 | 0.860 | 247 / 207 | -85 / 145 | 23915 / 24984 |

| scope | group | cells | real $/lot/wk | null mean | real minus null | share of 200 draws real beats | paired weekly bootstrap p | L6M real / null / diff | L6M share beaten | L3M real / null | 2026 real / null | max DD real / null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Four sessions summed | all | 2128 | 136 | 74 | 62 | 1.000 | 0.245 | 121 / 22 / 98 | 0.975 | 209 / 94 | 21 / 116 | 11726 / 5610 |
| Four sessions summed | long only | 962 | 153 | 99 | 54 | 0.990 | 0.209 | 298 / 22 / 276 | 1.000 | 207 / 119 | 287 / 188 | 9613 / 10777 |
| Four sessions summed | both sides | 1130 | 184 | 95 | 89 | 0.990 | 0.241 | 102 / 38 / 64 | 0.740 | 250 / 80 | -58 / 103 | 18337 / 4483 |
| Four sessions summed | level modules | 1089 | 176 | 41 | 136 | 1.000 | 0.070 | 224 / -4 / 228 | 0.990 | 361 / 65 | 151 / 99 | 10819 / 9052 |
| Four sessions summed | non-level modules | 1039 | 114 | 107 | 8 | 0.570 | 0.516 | 26 / 47 / -21 | 0.375 | 68 / 122 | -81 / 132 | 14356 / 4690 |
| Four sessions summed | level both | 577 | 295 | 43 | 252 | 1.000 | 0.028 | 251 / 14 / 237 | 0.965 | 427 / 84 | 137 / 48 | 17499 / 9197 |
| Four sessions summed | level long | 503 | 129 | 109 | 20 | 0.735 | 0.391 | 348 / 25 / 323 | 1.000 | 350 / 102 | 312 / 244 | 15516 / 14726 |
| Four sessions summed | non-level long | 459 | 202 | 96 | 106 | 1.000 | 0.052 | 250 / 23 / 227 | 1.000 | 103 / 154 | 264 / 123 | 8151 / 8409 |
| Four sessions summed | non-level both | 553 | 85 | 154 | -69 | 0.095 | 0.715 | -64 / 65 / -129 | 0.155 | 75 / 81 | -211 / 150 | 21023 / 5127 |

### B5. The simplest benchmark: 1 lot long NQ, open to close, every session every day (cost 0.24 pts per trade in)

| session | 1 lot long NQ open-to-close, $/wk (cost in) | plain p | L3M | L6M | 2023 Q4 / 2024 / 2025 / 2026 | max DD | session-trades per week | set-3 basket $/lot/wk (Test 6) |
|---|---|---|---|---|---|---|---|---|
| Asia | 858 | 0.005 | 1720 | 1308 | 151 / 1056 / 715 / 1011 | 25243 | 5.0 | 148 |
| London | 426 | 0.053 | -1018 | -251 | 971 / 463 / 154 / 557 | 29091 | 4.9 | -127 |
| NY AM | 291 | 0.284 | 628 | 160 | 1312 / -120 / -463 / 1434 | 56830 | 4.9 | 166 |
| NY PM | 70 | 0.428 | -1024 | -204 | 675 / -105 / 633 / -612 | 40640 | 4.9 | 276 |
| Four sessions summed | 1644 | 0.029 | 307 | 1013 | 3109 / 1293 / 1039 / 2390 | 68253 | 19.8 | 139 |


## PART A: LONG vs SHORT, LEVEL vs NON-LEVEL (QUICK SCREEN; stand-alone $/lot/wk of the sub-basket over all 160 held weeks, zero when none held; share of P&L = its contribution to the whole basket, sums to 100%)

Mode of a cell in the grid: long-only = the book takes long signals only, short-only = shorts only, both = the book takes both directions.

### A1. Summed over four sessions

| scope | split | books ever / mean held | share of P&L | L3M | L6M | $/lot/wk (held weeks all) | plain p | max DD | 2023 Q4 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Four sessions summed | all | 2143 / 228 | 100% | 248 | 124 | 139 | 0.072 | 12227 | -34 | 142 | 271 | 24 |
| Four sessions summed | long only | 966 / 95 | 33% | 249 | 305 | 152 | 0.045 | 9784 | 396 | 116 | 25 | 282 |
| Four sessions summed | short only | 36 / 5 | -1% | -335 | -180 | -94 | 0.918 | 18976 | -255 | -92 | -3 | -160 |
| Four sessions summed | both sides | 1141 / 128 | 68% | 287 | 103 | 191 | 0.073 | 19032 | -170 | 195 | 469 | -50 |
| Four sessions summed | level modules | 1103 / 120 | 74% | 390 | 287 | 200 | 0.019 | 11012 | -78 | 112 | 351 | 204 |
| Four sessions summed | non-level modules | 1040 / 108 | 26% | 114 | -32 | 97 | 0.214 | 15322 | 58 | 182 | 199 | -125 |
| Four sessions summed | level long | 507 / 52 | 17% | 415 | 390 | 148 | 0.096 | 14609 | 367 | 58 | 38 | 330 |
| Four sessions summed | level short | 9 / 1 | -1% | 0 | 0 | -102 | 0.967 | 18906 | -589 | -130 | -35 | 0 |
| Four sessions summed | level both | 587 / 68 | 57% | 430 | 317 | 323 | 0.009 | 16804 | -257 | 221 | 657 | 209 |
| Four sessions summed | non-level long | 459 / 44 | 16% | 127 | 224 | 176 | 0.019 | 8712 | 533 | 187 | 29 | 236 |
| Four sessions summed | non-level short | 27 / 4 | -0% | -335 | -180 | -37 | 0.704 | 12040 | 78 | -37 | 32 | -160 |
| Four sessions summed | non-level both | 554 / 60 | 11% | 141 | -136 | 73 | 0.344 | 23979 | -20 | 151 | 285 | -261 |

### A2. Per session (selected splits)

| scope | split | books ever / mean held | share of P&L | L3M | L6M | $/lot/wk (held weeks all) | plain p | max DD | 2023 Q4 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | all | 712 / 65 | 100% | 277 | 475 | 148 | 0.070 | 9493 | 102 | 106 | 80 | 301 |
| Asia | long only | 485 / 45 | 68% | 263 | 425 | 162 | 0.052 | 7969 | 0 | 126 | 140 | 286 |
| Asia | short only | 3 / 0 | -1% | 0 | -25 | -38 | 0.920 | 7238 | 0 | 0 | -35 | -100 |
| Asia | both sides | 224 / 20 | 33% | 352 | 592 | 146 | 0.166 | 22364 | 102 | 59 | -204 | 707 |
| Asia | level modules | 370 / 35 | 62% | 371 | 539 | 215 | 0.024 | 6396 | 173 | 82 | 229 | 374 |
| Asia | non-level modules | 342 / 30 | 38% | 172 | 385 | 108 | 0.147 | 10043 | -74 | 121 | 64 | 202 |
| Asia | level long | 239 / 23 | 33% | 438 | 477 | 197 | 0.045 | 7243 | 0 | 86 | 243 | 338 |
| Asia | level both | 129 / 12 | 30% | 357 | 689 | 365 | 0.003 | 8208 | 173 | 46 | 405 | 769 |
| London | all | 196 / 18 | -2025582566186046% | -467 | -175 | -127 | 0.856 | 22108 | -193 | -55 | -157 | -155 |
| London | long only | 80 / 8 | 236004073485161% | -337 | -147 | 19 | 0.441 | 15007 | 0 | 219 | -132 | -35 |
| London | short only | 1 / 0 | -23729345253536% | 0 | 0 | -10 | 0.769 | 3611 | 0 | -32 | 0 | 0 |
| London | both sides | 115 / 10 | -2237857294417672% | -747 | -282 | -216 | 0.972 | 34503 | -193 | -308 | 90 | -494 |
| London | level modules | 82 / 8 | -994011486509791% | -647 | -324 | -106 | 0.862 | 16941 | -198 | -185 | 70 | -200 |
| London | non-level modules | 114 / 10 | -1031571079676255% | -414 | -148 | -107 | 0.821 | 20006 | -180 | -6 | -161 | -139 |
| London | level long | 6 / 1 | 71666672875206% | 0 | 0 | 46 | 0.287 | 16390 | 0 | 119 | 21 | 0 |
| London | level both | 75 / 7 | -1041948814131462% | -647 | -324 | -108 | 0.835 | 19649 | -198 | -277 | 154 | -200 |
| NY AM | all | 1118 / 131 | 100% | 225 | -29 | 166 | 0.106 | 20533 | 62 | 209 | 346 | -82 |
| NY AM | long only | 386 / 41 | 16% | 230 | 37 | 132 | 0.119 | 11936 | 403 | 121 | 16 | 208 |
| NY AM | short only | 31 / 4 | -3% | -335 | -166 | -73 | 0.848 | 15399 | -332 | -60 | 32 | -141 |
| NY AM | both sides | 701 / 86 | 86% | 285 | 11 | 294 | 0.034 | 23949 | -182 | 515 | 510 | -105 |
| NY AM | level modules | 571 / 67 | 81% | 606 | 444 | 286 | 0.035 | 20735 | 23 | 205 | 405 | 316 |
| NY AM | non-level modules | 547 / 64 | 19% | 54 | -263 | 108 | 0.245 | 24012 | 166 | 220 | 293 | -283 |
| NY AM | level long | 253 / 27 | 9% | 29 | 91 | 114 | 0.195 | 15421 | 367 | 97 | 39 | 152 |
| NY AM | level both | 312 / 39 | 73% | 686 | 484 | 470 | 0.004 | 23187 | -307 | 533 | 701 | 339 |
| NY PM | all | 117 / 14 | 100% | 180 | 693 | 276 | 0.091 | 26279 | -103 | -69 | 935 | -12 |
| NY PM | long only | 15 / 1 | -4% | 0 | 0 | -123 | 0.915 | 26336 | 194 | -69 | 7 | -453 |
| NY PM | short only | 1 / 0 | 0% | 0 | 0 | 23 | 0.266 | 3839 | 283 | 0 | 0 | 0 |
| NY PM | both sides | 101 / 12 | 104% | 180 | 693 | 290 | 0.082 | 25843 | -141 | -29 | 935 | 5 |
| NY PM | level modules | 80 / 10 | 102% | 180 | 693 | 262 | 0.118 | 25459 | -602 | -71 | 993 | 19 |
| NY PM | non-level modules | 37 / 3 | -2% | 0 | 0 | -152 | 0.904 | 37592 | 122 | -157 | 4 | -426 |
| NY PM | level long | 9 / 1 | -3% | 0 | 0 | -37 | 0.756 | 11743 | 0 | -114 | 0 | 0 |
| NY PM | level both | 71 / 10 | 104% | 180 | 693 | 284 | 0.105 | 25459 | -602 | -4 | 993 | 19 |

## PART C: DOWN MARKETS (QUICK SCREEN; NQ session return = sum over the days of the week of last close minus first open of that session, from the stored time bars on server C)

### C1. Summed (NQ all-session weekly return: negative / positive weeks, worst 20 weeks)

| scope | split | condition | weeks | basket $/lot/wk | share of weeks positive | mean NQ session return (pts) | corr to NQ session return | beta ($/lot per NQ pt) |
|---|---|---|---|---|---|---|---|---|
| Four sessions summed | all | NQ all-session return < 0 | 66 | -84 | 55% | -432 | 0.22 | 0.47 |
| Four sessions summed | all | NQ all-session return >= 0 | 94 | 296 | 62% | 451 | 0.22 | 0.47 |
| Four sessions summed | all | worst 20 NQ weeks (all sessions) | 20 | -372 | 45% | -922 | 0.22 | 0.47 |
| Four sessions summed | all | all other weeks | 140 | 213 | 61% | 231 | 0.22 | 0.47 |
| Four sessions summed | long only | NQ all-session return < 0 | 66 | -376 | 35% | -432 | 0.47 | 0.99 |
| Four sessions summed | long only | NQ all-session return >= 0 | 94 | 523 | 73% | 451 | 0.47 | 0.99 |
| Four sessions summed | long only | worst 20 NQ weeks (all sessions) | 20 | -965 | 30% | -922 | 0.47 | 0.99 |
| Four sessions summed | long only | all other weeks | 140 | 312 | 61% | 231 | 0.47 | 0.99 |
| Four sessions summed | short only | NQ all-session return < 0 | 66 | 213 | 42% | -432 | -0.16 | -0.29 |
| Four sessions summed | short only | NQ all-session return >= 0 | 94 | -309 | 28% | 451 | -0.16 | -0.29 |
| Four sessions summed | short only | worst 20 NQ weeks (all sessions) | 20 | 407 | 40% | -922 | -0.16 | -0.29 |
| Four sessions summed | short only | all other weeks | 140 | -165 | 33% | 231 | -0.16 | -0.29 |
| Four sessions summed | both sides | NQ all-session return < 0 | 66 | 244 | 67% | -432 | 0.00 | 0.01 |
| Four sessions summed | both sides | NQ all-session return >= 0 | 94 | 154 | 50% | 451 | 0.00 | 0.01 |
| Four sessions summed | both sides | worst 20 NQ weeks (all sessions) | 20 | 287 | 70% | -922 | 0.00 | 0.01 |
| Four sessions summed | both sides | all other weeks | 140 | 178 | 55% | 231 | 0.00 | 0.01 |
| Four sessions summed | level modules | NQ all-session return < 0 | 66 | 96 | 52% | -432 | 0.14 | 0.31 |
| Four sessions summed | level modules | NQ all-session return >= 0 | 94 | 273 | 59% | 451 | 0.14 | 0.31 |
| Four sessions summed | level modules | worst 20 NQ weeks (all sessions) | 20 | -80 | 45% | -922 | 0.14 | 0.31 |
| Four sessions summed | level modules | all other weeks | 140 | 240 | 57% | 231 | 0.14 | 0.31 |
| Four sessions summed | non-level modules | NQ all-session return < 0 | 66 | -252 | 45% | -432 | 0.27 | 0.62 |
| Four sessions summed | non-level modules | NQ all-session return >= 0 | 94 | 342 | 63% | 451 | 0.27 | 0.62 |
| Four sessions summed | non-level modules | worst 20 NQ weeks (all sessions) | 20 | -631 | 45% | -922 | 0.27 | 0.62 |
| Four sessions summed | non-level modules | all other weeks | 140 | 201 | 57% | 231 | 0.27 | 0.62 |

### C2. Per session (the session's own NQ return sign; worst 20 = worst 20 weeks of all-session NQ return)

| scope | split | condition | weeks | basket $/lot/wk | share of weeks positive | mean NQ session return (pts) | corr to NQ session return | beta ($/lot per NQ pt) |
|---|---|---|---|---|---|---|---|---|
| Asia | all | NQ session return < 0 | 62 | -530 | 27% | -166 | 0.59 | 3.43 |
| Asia | all | NQ session return >= 0 | 98 | 577 | 69% | 177 | 0.59 | 3.43 |
| Asia | all | worst 20 NQ weeks (all sessions) | 20 | -349 | 35% | -922 | 0.59 | 3.43 |
| Asia | all | all other weeks | 140 | 219 | 56% | 231 | 0.59 | 3.43 |
| London | all | NQ session return < 0 | 64 | -712 | 30% | -162 | 0.41 | 2.89 |
| London | all | NQ session return >= 0 | 96 | 264 | 62% | 145 | 0.41 | 2.89 |
| London | all | worst 20 NQ weeks (all sessions) | 20 | -469 | 45% | -922 | 0.41 | 2.89 |
| London | all | all other weeks | 140 | -78 | 50% | 231 | 0.41 | 2.89 |
| NY AM | all | NQ session return < 0 | 75 | -298 | 45% | -265 | 0.28 | 1.35 |
| NY AM | all | NQ session return >= 0 | 85 | 576 | 69% | 264 | 0.28 | 1.35 |
| NY AM | all | worst 20 NQ weeks (all sessions) | 20 | -592 | 35% | -922 | 0.28 | 1.35 |
| NY AM | all | all other weeks | 140 | 274 | 61% | 231 | 0.28 | 1.35 |
| NY PM | all | NQ session return < 0 | 79 | 228 | 49% | -221 | 0.13 | 0.97 |
| NY PM | all | NQ session return >= 0 | 81 | 322 | 52% | 224 | 0.13 | 0.97 |
| NY PM | all | worst 20 NQ weeks (all sessions) | 20 | 1362 | 55% | -922 | 0.13 | 0.97 |
| NY PM | all | all other weeks | 140 | 121 | 50% | 231 | 0.13 | 0.97 |

### C3. Per session, long-only vs both-sides books (session's own NQ return sign)

| scope | split | condition | weeks | basket $/lot/wk | share of weeks positive | mean NQ session return (pts) | corr to NQ session return | beta ($/lot per NQ pt) |
|---|---|---|---|---|---|---|---|---|
| Asia | long only | NQ session return < 0 | 62 | -751 | 15% | -166 | 0.78 | 4.77 |
| Asia | long only | NQ session return >= 0 | 98 | 740 | 59% | 177 | 0.78 | 4.77 |
| Asia | both sides | NQ session return < 0 | 62 | 14 | 52% | -166 | 0.11 | 0.76 |
| Asia | both sides | NQ session return >= 0 | 98 | 229 | 54% | 177 | 0.11 | 0.76 |
| London | long only | NQ session return < 0 | 64 | -590 | 30% | -162 | 0.48 | 3.47 |
| London | long only | NQ session return >= 0 | 96 | 424 | 49% | 145 | 0.48 | 3.47 |
| London | both sides | NQ session return < 0 | 64 | -384 | 28% | -162 | -0.02 | -0.15 |
| London | both sides | NQ session return >= 0 | 96 | -104 | 38% | 145 | -0.02 | -0.15 |
| NY AM | long only | NQ session return < 0 | 75 | -868 | 19% | -265 | 0.67 | 3.06 |
| NY AM | long only | NQ session return >= 0 | 85 | 1014 | 84% | 264 | 0.67 | 3.06 |
| NY AM | both sides | NQ session return < 0 | 75 | 173 | 59% | -265 | 0.04 | 0.25 |
| NY AM | both sides | NQ session return >= 0 | 85 | 401 | 56% | 264 | 0.04 | 0.25 |
| NY PM | long only | NQ session return < 0 | 79 | -496 | 6% | -221 | 0.35 | 1.11 |
| NY PM | long only | NQ session return >= 0 | 81 | 240 | 30% | 224 | 0.35 | 1.11 |
| NY PM | both sides | NQ session return < 0 | 79 | 306 | 51% | -221 | 0.10 | 0.75 |
| NY PM | both sides | NQ session return >= 0 | 81 | 275 | 52% | 224 | 0.10 | 0.75 |

Worst 20 NQ weeks (week index, week start, all-session NQ points): first 5 are 168 2026-06-21 -1,677; 74 2024-09-01 -1,304; 171 2026-07-12 -1,303; 184 2026-10-11 -1,249; 100 2025-03-02 -974. Full list:

| week | start | NQ pts |
|---|---|---|
| 168 | 2026-06-21 | -1677 |
| 74 | 2024-09-01 | -1304 |
| 171 | 2026-07-12 | -1303 |
| 184 | 2026-10-11 | -1249 |
| 100 | 2025-03-02 | -974 |
| 54 | 2024-04-14 | -946 |
| 176 | 2026-08-16 | -945 |
| 67 | 2024-07-14 | -938 |
| 135 | 2025-11-02 | -886 |
| 137 | 2025-11-16 | -855 |
| 165 | 2026-05-31 | -835 |
| 104 | 2025-03-30 | -830 |
| 99 | 2025-02-23 | -775 |
| 106 | 2025-04-13 | -751 |
| 68 | 2024-07-21 | -731 |
| 121 | 2025-07-27 | -726 |
| 149 | 2026-02-08 | -713 |
| 155 | 2026-03-22 | -690 |
| 84 | 2024-11-10 | -683 |
| 131 | 2025-10-05 | -627 |

## PART D: WHICH LEVELS (QUICK SCREEN; summed over four sessions; contribution = $/lot/wk it adds to the whole basket; p on the contribution series; m = number of items tested in that table)

MULTIPLE COMPARISON: 40 level modules, 10 level types, 9 actions, 21 type x action cells are each tested; "plain p" is the single-item bootstrap, Bonferroni multiplies by m, BH q is the Benjamini-Hochberg false discovery rate. Treat everything with q > 0.10 as a lead only. Level types are my grouping of the trig_levels_* names (fib = fib* and fibr_*; VWAP = vwap, vwap_bands; swing S/R, trendline, channel = swsr*, swcluster, trendline, channel; profile/zones/stack; prior day/session/opens/range = prior_day, session_hl, opens, open_range, week_month, gaps, mmove; pivot = piv_*; FVG/order block, UW and other = other levels).

### D1. Level modules: top 5 and bottom 5

| level module (top 5 by contribution) | books ever / mean held | weeks held | P&L share | contribution $/lot/wk (to the basket) | plain p | Bonferroni p (m tests) | BH q | L6M | L3M | stand-alone $/lot/wk when held |
|---|---|---|---|---|---|---|---|---|---|---|
| trig_levels_vwap | 175 / 22.8 | 160 | 34% | 47.8 | 0.007 | 0.300 (40) | 0.300 | 24.5 | 72.5 | 528 |
| trig_levels_trendline | 62 / 8.4 | 160 | 10% | 13.8 | 0.079 | 1.000 (40) | 0.693 | 19.6 | -2.1 | 327 |
| trig_levels_channel | 50 / 5.8 | 134 | 8% | 11.3 | 0.029 | 1.000 (40) | 0.590 | 17.2 | 22.5 | 700 |
| trig_levels_prior_day | 75 / 7.5 | 147 | 7% | 9.4 | 0.104 | 1.000 (40) | 0.693 | 38.1 | 36.0 | 433 |
| trig_levels_profile_nodes | 192 / 20.0 | 160 | 6% | 8.3 | 0.284 | 1.000 (40) | 0.750 | -13.1 | 14.4 | 49 |

| level module (bottom 5 by contribution) | books ever / mean held | weeks held | P&L share | contribution $/lot/wk (to the basket) | plain p | Bonferroni p (m tests) | BH q | L6M | L3M | stand-alone $/lot/wk when held |
|---|---|---|---|---|---|---|---|---|---|---|
| trig_levels_open_range | 9 / 1.0 | 65 | -1% | -0.9 | 0.703 | 1.000 (40) | 0.878 | 0.0 | 0.0 | -494 |
| trig_levels_fvg15 | 6 / 0.4 | 43 | -1% | -1.2 | 0.915 | 1.000 (40) | 0.921 | -0.4 | -0.9 | -346 |
| trig_levels_fibr_dev | 28 / 2.8 | 121 | -1% | -1.4 | 0.654 | 1.000 (40) | 0.878 | 1.1 | 1.8 | 60 |
| trig_levels_fvg5 | 22 / 2.0 | 56 | -2% | -2.5 | 0.885 | 1.000 (40) | 0.921 | -3.3 | -0.8 | -506 |
| trig_levels_fib15 | 64 / 5.9 | 134 | -4% | -6.3 | 0.821 | 1.000 (40) | 0.921 | 0.9 | 0.0 | -44 |

### D2. Top 3 level modules per session

| session | top 3 level modules by contribution to the session basket |
|---|---|
| Asia | prior_day +27 $/lot/wk (p 0.205); fib15 +21 $/lot/wk (p 0.044); vwap +20 $/lot/wk (p 0.035) |
| London | swsr60 +1 $/lot/wk (p 0.216); gaps +0 $/lot/wk (p 0.284); piv_floor +0 $/lot/wk (p 0.474) |
| NY AM | vwap +80 $/lot/wk (p 0.008); prior_day +18 $/lot/wk (p 0.082); profile_nodes +13 $/lot/wk (p 0.315) |
| NY PM | trendline +305 $/lot/wk (p 0.070); ob5 +18 $/lot/wk (p 0.076); piv_floor +2 $/lot/wk (p 0.491) |

### D3. By action (level books only; break / false_break / retest / reject / ...)

| action (reject / break / retest ...) | books ever / mean held | weeks held | P&L share | contribution $/lot/wk (to the basket) | plain p | Bonferroni p (m tests) | BH q | L6M | L3M | stand-alone $/lot/wk when held |
|---|---|---|---|---|---|---|---|---|---|---|
| break | 610 / 68.3 | 160 | 59% | 82.6 | 0.004 | 0.036 (9) | 0.036 | 61.1 | 92.4 | 294 |
| false_break | 164 / 16.2 | 160 | 9% | 12.9 | 0.176 | 1.000 (9) | 0.480 | 66.0 | 60.5 | 210 |
| retest | 176 / 19.1 | 160 | 6% | 8.7 | 0.249 | 1.000 (9) | 0.480 | 16.8 | 31.4 | 131 |
| rej_flow | 1 / 0.1 | 13 | 0% | 0.6 | 0.048 | 0.427 (9) | 0.214 | 0.0 | 0.0 | 1098 |
| ema_hold | 2 / 0.2 | 30 | 0% | 0.1 | 0.267 | 1.000 (9) | 0.480 | 0.8 | 1.7 | 202 |
| fade | 1 / 0.1 | 13 | -0% | -0.1 | 0.698 | 1.000 (9) | 0.897 | 0.0 | 0.0 | -221 |
| reject | 135 / 14.7 | 160 | -0% | -0.2 | 0.522 | 1.000 (9) | 0.784 | -5.2 | -0.7 | -23 |
| lim_prox | 1 / 0.1 | 13 | -0% | -0.2 | 0.911 | 1.000 (9) | 0.911 | 0.0 | 0.0 | -370 |
| pullback | 13 / 1.2 | 95 | -1% | -1.8 | 0.831 | 1.000 (9) | 0.911 | -0.7 | 1.3 | 92 |

### D4. By action, native bar types only

| action, native bars only | books ever / mean held | weeks held | P&L share | contribution $/lot/wk (to the basket) | plain p | Bonferroni p (m tests) | BH q | L6M | L3M | stand-alone $/lot/wk when held |
|---|---|---|---|---|---|---|---|---|---|---|
| break_native | 289 / 32.6 | 160 | 28% | 39.7 | 0.005 | 0.027 (5) | 0.027 | 25.4 | 45.8 | 307 |
| false_break_native | 87 / 8.3 | 160 | 4% | 6.1 | 0.181 | 0.905 (5) | 0.453 | 28.2 | 31.0 | 166 |
| retest_native | 86 / 9.4 | 160 | 3% | 4.1 | 0.281 | 1.000 (5) | 0.468 | 11.8 | 15.7 | 121 |
| pullback_native | 8 / 0.8 | 95 | -1% | -0.8 | 0.777 | 1.000 (5) | 0.939 | -0.7 | 1.3 | 97 |
| reject_native | 57 / 5.7 | 160 | -4% | -6.1 | 0.939 | 1.000 (5) | 0.939 | -4.7 | -1.6 | -222 |

### D5. By level type

| level type | books ever / mean held | weeks held | P&L share | contribution $/lot/wk (to the basket) | plain p | Bonferroni p (m tests) | BH q | L6M | L3M | stand-alone $/lot/wk when held |
|---|---|---|---|---|---|---|---|---|---|---|
| VWAP | 191 / 24.3 | 160 | 34% | 47.8 | 0.006 | 0.065 (10) | 0.065 | 21.4 | 70.3 | 488 |
| swing S/R, trendline, channel | 114 / 14.5 | 160 | 18% | 25.0 | 0.024 | 0.240 (10) | 0.120 | 36.8 | 20.4 | 430 |
| profile / zones / stack | 244 / 25.7 | 160 | 8% | 11.1 | 0.247 | 1.000 (10) | 0.472 | -5.9 | 19.3 | 70 |
| prior day / session / opens / range | 124 / 11.9 | 160 | 7% | 10.4 | 0.111 | 1.000 (10) | 0.368 | 48.3 | 52.0 | 296 |
| pivot | 82 / 9.3 | 160 | 4% | 6.0 | 0.170 | 1.000 (10) | 0.425 | -0.2 | -20.5 | 249 |
| round numbers | 35 / 3.5 | 121 | 2% | 2.3 | 0.283 | 1.000 (10) | 0.472 | 9.0 | 11.4 | 99 |
| fib | 92 / 9.5 | 160 | 1% | 1.0 | 0.450 | 1.000 (10) | 0.563 | -12.6 | 9.5 | 124 |
| supply-demand (sd/sdx) | 4 / 0.3 | 17 | 0% | 0.0 | 0.451 | 1.000 (10) | 0.563 | 0.1 | 1.5 | 26 |
| book walls | 7 / 0.9 | 65 | -0% | -0.4 | 0.885 | 1.000 (10) | 0.885 | -0.6 | -0.7 | -176 |
| other levels | 210 / 20.0 | 160 | -0% | -0.6 | 0.528 | 1.000 (10) | 0.587 | 42.7 | 23.3 | 47 |

### D6. Level type x action (>= 15 books)

| level type x action (>=15 books) | books ever / mean held | weeks held | P&L share | contribution $/lot/wk (to the basket) | plain p | Bonferroni p (m tests) | BH q | L6M | L3M | stand-alone $/lot/wk when held |
|---|---|---|---|---|---|---|---|---|---|---|
| VWAP / break | 133 / 18.5 | 160 | 34% | 47.8 | 0.004 | 0.084 (21) | 0.084 | 6.3 | 46.2 | 603 |
| swing S/R, trendline, channel / break | 65 / 8.8 | 160 | 13% | 17.7 | 0.009 | 0.189 (21) | 0.094 | 35.7 | 20.1 | 513 |
| other levels / break | 114 / 11.0 | 147 | 6% | 8.4 | 0.121 | 1.000 (21) | 0.436 | 21.3 | 1.1 | 238 |
| prior day / session / opens / range / false_break | 24 / 2.3 | 69 | 5% | 7.2 | 0.138 | 1.000 (21) | 0.436 | 43.9 | 41.6 | 780 |
| profile / zones / stack / retest | 54 / 6.4 | 160 | 4% | 5.9 | 0.066 | 1.000 (21) | 0.436 | 0.6 | 2.5 | 163 |
| round numbers / break | 28 / 2.9 | 108 | 3% | 4.1 | 0.128 | 1.000 (21) | 0.436 | 8.5 | 8.9 | 296 |
| pivot / reject | 22 / 2.9 | 160 | 3% | 3.6 | 0.176 | 1.000 (21) | 0.436 | 0.5 | -0.1 | 398 |
| profile / zones / stack / false_break | 65 / 7.5 | 160 | 3% | 3.5 | 0.343 | 1.000 (21) | 0.554 | -10.1 | -5.6 | -78 |
| pivot / break | 51 / 5.5 | 147 | 2% | 3.4 | 0.187 | 1.000 (21) | 0.436 | 2.9 | -17.3 | 235 |
| prior day / session / opens / range / retest | 20 / 1.8 | 108 | 2% | 2.7 | 0.187 | 1.000 (21) | 0.436 | 2.4 | 6.3 | 222 |
| swing S/R, trendline, channel / reject | 29 / 3.6 | 147 | 2% | 2.7 | 0.291 | 1.000 (21) | 0.514 | 2.3 | 1.6 | 156 |
| other levels / false_break | 21 / 1.8 | 82 | 1% | 1.7 | 0.283 | 1.000 (21) | 0.514 | 21.0 | 11.0 | 140 |
| fib / false_break | 27 / 2.5 | 121 | 1% | 1.5 | 0.293 | 1.000 (21) | 0.514 | 5.8 | 12.9 | 138 |
| profile / zones / stack / break | 121 / 11.4 | 160 | 1% | 1.5 | 0.414 | 1.000 (21) | 0.567 | 3.6 | 22.4 | -55 |
| prior day / session / opens / range / break | 51 / 5.0 | 134 | 1% | 0.7 | 0.414 | 1.000 (21) | 0.567 | 2.0 | 4.2 | -5 |
| VWAP / retest | 29 / 3.1 | 147 | 0% | 0.6 | 0.432 | 1.000 (21) | 0.567 | 13.0 | 23.8 | -52 |
| prior day / session / opens / range / reject | 29 / 2.8 | 78 | -0% | -0.2 | 0.537 | 1.000 (21) | 0.664 | 0.0 | 0.0 | -4 |
| fib / break | 44 / 5.0 | 147 | -1% | -1.2 | 0.595 | 1.000 (21) | 0.694 | -19.8 | 4.5 | 112 |
| other levels / reject | 21 / 2.2 | 104 | -1% | -2.0 | 0.831 | 1.000 (21) | 0.872 | -3.8 | -1.3 | -166 |
| VWAP / reject | 15 / 1.5 | 91 | -2% | -2.7 | 0.744 | 1.000 (21) | 0.822 | -4.4 | -2.3 | -361 |
| other levels / retest | 37 / 3.5 | 108 | -5% | -7.3 | 0.899 | 1.000 (21) | 0.899 | 4.0 | 9.6 | -15 |

### D7. All level modules

| level module (all) | books ever / mean held | weeks held | P&L share | contribution $/lot/wk (to the basket) | plain p | Bonferroni p (m tests) | BH q | L6M | L3M | stand-alone $/lot/wk when held |
|---|---|---|---|---|---|---|---|---|---|---|
| trig_levels_vwap | 175 / 22.8 | 160 | 34% | 47.8 | 0.007 | 0.300 (40) | 0.300 | 24.5 | 72.5 | 528 |
| trig_levels_trendline | 62 / 8.4 | 160 | 10% | 13.8 | 0.079 | 1.000 (40) | 0.693 | 19.6 | -2.1 | 327 |
| trig_levels_channel | 50 / 5.8 | 134 | 8% | 11.3 | 0.029 | 1.000 (40) | 0.590 | 17.2 | 22.5 | 700 |
| trig_levels_prior_day | 75 / 7.5 | 147 | 7% | 9.4 | 0.104 | 1.000 (40) | 0.693 | 38.1 | 36.0 | 433 |
| trig_levels_profile_nodes | 192 / 20.0 | 160 | 6% | 8.3 | 0.284 | 1.000 (40) | 0.750 | -13.1 | 14.4 | 49 |
| trig_levels_piv_floor | 63 / 7.1 | 160 | 4% | 5.1 | 0.185 | 1.000 (40) | 0.693 | -2.0 | -12.2 | 368 |
| trig_levels_fib60 | 18 / 2.0 | 104 | 3% | 4.0 | 0.166 | 1.000 (40) | 0.693 | 20.4 | 0.0 | 927 |
| trig_levels_swsr5 | 38 / 3.2 | 95 | 2% | 2.9 | 0.184 | 1.000 (40) | 0.693 | 13.7 | 5.8 | 128 |
| trig_levels_session_hl | 7 / 0.6 | 39 | 2% | 2.7 | 0.144 | 1.000 (40) | 0.693 | 0.0 | 0.0 | 236 |
| trig_levels_profile_va | 40 / 4.6 | 147 | 2% | 2.6 | 0.191 | 1.000 (40) | 0.693 | 1.8 | -3.9 | 52 |
| trig_levels_round | 35 / 3.5 | 121 | 2% | 2.3 | 0.283 | 1.000 (40) | 0.750 | 9.0 | 11.4 | 99 |
| trig_levels_fibr_on | 26 / 3.2 | 134 | 2% | 2.2 | 0.331 | 1.000 (40) | 0.750 | -24.3 | -1.2 | 348 |
| trig_levels_ob5 | 13 / 1.8 | 69 | 1% | 1.7 | 0.105 | 1.000 (40) | 0.693 | 5.7 | 9.8 | 155 |
| trig_levels_piv_wf | 19 / 2.2 | 108 | 1% | 0.9 | 0.315 | 1.000 (40) | 0.750 | 1.7 | -8.3 | 11 |
| trig_levels_fibr_pd | 20 / 1.8 | 82 | 1% | 0.8 | 0.338 | 1.000 (40) | 0.750 | 11.0 | 8.5 | -49 |
| trig_levels_ob15 | 13 / 0.8 | 56 | 1% | 0.8 | 0.223 | 1.000 (40) | 0.742 | 8.3 | 4.5 | 180 |
| trig_levels_sdx15 | 4 / 0.5 | 26 | 0% | 0.6 | 0.291 | 1.000 (40) | 0.750 | 3.9 | 3.3 | 369 |
| trig_levels_zones | 7 / 0.6 | 69 | 0% | 0.3 | 0.362 | 1.000 (40) | 0.762 | 0.5 | 1.1 | 87 |
| trig_levels_sdx_vol1100 | 2 / 0.2 | 17 | 0% | 0.3 | 0.171 | 1.000 (40) | 0.693 | 1.6 | 3.2 | 464 |
| trig_levels_sdx3 | 5 / 0.4 | 56 | 0% | 0.2 | 0.429 | 1.000 (40) | 0.832 | -2.3 | 2.1 | 348 |
| trig_levels_vwap_bands | 16 / 1.5 | 91 | 0% | 0.0 | 0.489 | 1.000 (40) | 0.832 | -3.2 | -2.2 | -105 |
| trig_levels_book_walls | 1 / 0.2 | 26 | -0% | -0.0 | 0.662 | 1.000 (40) | 0.878 | -0.0 | 0.0 | -19 |
| trig_levels_fib5 | 17 / 1.8 | 121 | -0% | -0.0 | 0.519 | 1.000 (40) | 0.832 | -0.7 | 1.8 | 134 |
| trig_levels_stack | 5 / 0.5 | 69 | -0% | -0.0 | 0.505 | 1.000 (40) | 0.832 | 4.8 | 7.7 | 256 |
| trig_levels_mmove | 19 / 1.7 | 108 | -0% | -0.1 | 0.540 | 1.000 (40) | 0.832 | 5.9 | 7.4 | 90 |
| trig_levels_opens | 10 / 0.9 | 43 | -0% | -0.1 | 0.539 | 1.000 (40) | 0.832 | 4.3 | 8.6 | 263 |
| trig_levels_fibr_ib | 8 / 0.7 | 56 | -0% | -0.1 | 0.486 | 1.000 (40) | 0.832 | -0.5 | 0.5 | -113 |
| trig_levels_swcluster | 2 / 0.3 | 26 | -0% | -0.2 | 0.651 | 1.000 (40) | 0.878 | 0.0 | 0.0 | -125 |
| trig_levels_swsr60 | 6 / 0.8 | 117 | -0% | -0.2 | 0.618 | 1.000 (40) | 0.878 | -0.9 | 0.6 | -112 |
| trig_levels_sdx_rng28 | 2 / 0.1 | 17 | -0% | -0.2 | 0.921 | 1.000 (40) | 0.921 | -1.4 | -1.8 | -749 |
| trig_levels_sdx5 | 2 / 0.2 | 26 | -0% | -0.3 | 0.792 | 1.000 (40) | 0.921 | -0.8 | 0.0 | -389 |
| trig_levels_swsr15 | 2 / 0.2 | 13 | -0% | -0.3 | 0.839 | 1.000 (40) | 0.921 | -1.8 | -3.0 | -652 |
| trig_levels_book_walls_loose | 6 / 0.7 | 65 | -0% | -0.4 | 0.881 | 1.000 (40) | 0.921 | -0.6 | -0.7 | -218 |
| trig_levels_fibr_or | 10 / 1.0 | 78 | -0% | -0.4 | 0.695 | 1.000 (40) | 0.878 | 0.0 | 0.0 | -180 |
| trig_levels_gaps | 4 / 0.3 | 26 | -0% | -0.6 | 0.906 | 1.000 (40) | 0.921 | 0.0 | 0.0 | -208 |
| trig_levels_open_range | 9 / 1.0 | 65 | -1% | -0.9 | 0.703 | 1.000 (40) | 0.878 | 0.0 | 0.0 | -494 |
| trig_levels_fvg15 | 6 / 0.4 | 43 | -1% | -1.2 | 0.915 | 1.000 (40) | 0.921 | -0.4 | -0.9 | -346 |
| trig_levels_fibr_dev | 28 / 2.8 | 121 | -1% | -1.4 | 0.654 | 1.000 (40) | 0.878 | 1.1 | 1.8 | 60 |
| trig_levels_fvg5 | 22 / 2.0 | 56 | -2% | -2.5 | 0.885 | 1.000 (40) | 0.921 | -3.3 | -0.8 | -506 |
| trig_levels_fib15 | 64 / 5.9 | 134 | -4% | -6.3 | 0.821 | 1.000 (40) | 0.921 | 0.9 | 0.0 | -44 |

## PART E: THE STALE LEVEL MODULES (re-verification state)

Owner / state: re-run owned by W-SHORT (cron line in MORNING.md every 30 min) and W-GRIDOPS (0145Z audit: trig_levels_* grid results written before 2026-11-18 06:00Z predate the level-module fixes; "13 of 17 level modules differ on a fresh re-run"); status table in autopilot/SEARCH_STATUS.md (21:15Z): Dallas 12 stale real / 0 null draw 1 / 0 null draw 2, fresh level files 24,825 / 23,970 / 23,970; Frankfurt 1,660 / 1,396 / 1,759 stale before merge (fresh 8,608); Singapore 1,657 / 776 / 1,179 (fresh 8,727). So the REAL level re-run is essentially done on the merge host (12 left); it is a grid job, not engine rows: **no rows to queue, nothing appended to pending_nyam_gating.txt**. I read the server C copy (extracted 16:03Z, 10,274 level grid files) only; classification: fresh = written at or after 2026-11-18 06:00Z; stamp = gstamp.stamp of today's module code on the same bar row compared with the stamp stored in the file (stamped files only: 1,972 of 10,274; the rest are legacy files accepted by the time rule). C copy totals: fresh 9179, stale 1095, stamped 1972 of which equal to today's code 1943, fresh but stamp differs 29. No level module is fully verified in the C copy at 16:03Z (every module still has stale files there; Dallas had 12 left at 21:15Z, so a fresh extract will show most as verified); test 5-7 baskets use only fresh files, so the verified/not question only changes which candidate cells exist, not the held-book numbers above. A re-extract of the Dallas copy and a re-run of this table is the way to close it (not done: Dallas is the fleet merge host, I did not touch it).

| level module | grid files (C copy 16:03Z) | fresh (>= 11-18 06:00Z) | stale | stamped | stamp equals today code | fresh but stamp differs |
|---|---|---|---|---|---|---|
| trig_levels_book_walls | 193 | 151 | 42 | 0 | 0 | 0 |
| trig_levels_book_walls_loose | 207 | 168 | 39 | 22 | 22 | 0 |
| trig_levels_channel | 194 | 179 | 15 | 45 | 45 | 0 |
| trig_levels_fib15 | 258 | 252 | 6 | 121 | 120 | 1 |
| trig_levels_fib5 | 227 | 216 | 11 | 81 | 79 | 2 |
| trig_levels_fib60 | 221 | 209 | 12 | 70 | 70 | 0 |
| trig_levels_fibr_dev | 197 | 188 | 9 | 61 | 60 | 1 |
| trig_levels_fibr_ib | 182 | 167 | 15 | 21 | 20 | 1 |
| trig_levels_fibr_on | 173 | 161 | 12 | 20 | 19 | 1 |
| trig_levels_fibr_or | 180 | 162 | 18 | 18 | 18 | 0 |
| trig_levels_fibr_pd | 203 | 191 | 12 | 54 | 52 | 2 |
| trig_levels_fvg15 | 181 | 162 | 19 | 16 | 16 | 0 |
| trig_levels_fvg5 | 234 | 222 | 12 | 97 | 96 | 1 |
| trig_levels_gaps | 192 | 173 | 19 | 31 | 31 | 0 |
| trig_levels_mmove | 183 | 173 | 10 | 37 | 37 | 0 |
| trig_levels_ob15 | 172 | 151 | 21 | 0 | 0 | 0 |
| trig_levels_ob5 | 180 | 161 | 19 | 16 | 14 | 2 |
| trig_levels_open_range | 222 | 187 | 35 | 39 | 39 | 0 |
| trig_levels_opens | 252 | 227 | 25 | 91 | 90 | 1 |
| trig_levels_piv_cama | 181 | 166 | 15 | 23 | 23 | 0 |
| trig_levels_piv_floor | 192 | 182 | 10 | 47 | 47 | 0 |
| trig_levels_piv_wf | 180 | 166 | 14 | 20 | 20 | 0 |
| trig_levels_prior_day | 225 | 191 | 34 | 49 | 49 | 0 |
| trig_levels_profile_nodes | 261 | 234 | 27 | 107 | 106 | 1 |
| trig_levels_profile_va | 255 | 224 | 31 | 97 | 97 | 0 |
| trig_levels_round | 269 | 241 | 28 | 115 | 107 | 8 |
| trig_levels_sd15 | 172 | 151 | 21 | 0 | 0 | 0 |
| trig_levels_sd5 | 172 | 151 | 21 | 0 | 0 | 0 |
| trig_levels_sd60 | 172 | 151 | 21 | 0 | 0 | 0 |
| trig_levels_sdx15 | 173 | 152 | 21 | 2 | 2 | 0 |
| trig_levels_sdx3 | 174 | 163 | 11 | 21 | 21 | 0 |
| trig_levels_sdx30 | 172 | 151 | 21 | 0 | 0 | 0 |
| trig_levels_sdx5 | 173 | 157 | 16 | 9 | 9 | 0 |
| trig_levels_sdx60 | 172 | 151 | 21 | 0 | 0 | 0 |
| trig_levels_sdx_renko28 | 172 | 153 | 19 | 7 | 7 | 0 |
| trig_levels_sdx_rng28 | 172 | 155 | 17 | 8 | 8 | 0 |
| trig_levels_sdx_vol1100 | 172 | 153 | 19 | 10 | 10 | 0 |
| trig_levels_session_hl | 257 | 231 | 26 | 95 | 95 | 0 |
| trig_levels_stack | 202 | 185 | 17 | 42 | 42 | 0 |
| trig_levels_swcluster | 177 | 156 | 21 | 14 | 11 | 3 |
| trig_levels_swsr15 | 180 | 169 | 11 | 25 | 25 | 0 |
| trig_levels_swsr5 | 207 | 195 | 12 | 64 | 64 | 0 |
| trig_levels_swsr60 | 178 | 160 | 18 | 19 | 19 | 0 |
| trig_levels_trendline | 235 | 227 | 8 | 99 | 98 | 1 |
| trig_levels_uw_dp | 194 | 150 | 44 | 0 | 0 | 0 |
| trig_levels_uw_ndx | 194 | 151 | 43 | 0 | 0 | 0 |
| trig_levels_uw_qqq | 194 | 151 | 43 | 0 | 0 | 0 |
| trig_levels_vwap | 291 | 272 | 19 | 149 | 147 | 2 |
| trig_levels_vwap_bands | 247 | 216 | 31 | 80 | 79 | 1 |
| trig_levels_week_month | 195 | 151 | 44 | 1 | 1 | 0 |
| trig_levels_zones | 213 | 173 | 40 | 29 | 28 | 1 |


Code and data: code/th_test7/ (build_jobs7, null_run, b_analysis, partACD, common7, nq_sess, stampcheck, tables7, page7); server C /mnt/l2/l2vast/_test7 (jobs7.pkl, out/*.npz null outputs, res7_*.pkl). No engine or gate change; no server touched except C scratch; nothing deleted.
