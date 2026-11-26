# TEST 9: are the 20 LIVE books beyond drift? (W-TEST9, parts A, C, D)

Written 2026-11-26 23:40 UTC. **QUICK SCREEN label on every number** (grid tape walk / gcore2x re-simulation, 1 NQ lot per book at $20/point, grid cost in, no stack rules, no account layers; weeks 26..185 of the grid = 2023-10-01 to 2026-10-24, 160 weeks, the same span and null method as Tests 7 and 8). Order: autopilot/DIRECTIVE_TEST9_2313Z.md (relay design under Josh's 18:22Z standing order, not Josh's words). Part B (spec pages) is W-SPEC9's. Code code/th_test9/ ; data on server C /mnt/l2/l2vast/_test9. No engine or gate change, nothing bought or downloaded, nothing deleted.

## ANSWER FIRST

1. **Quick screen: 13 of the 17 mappable live books are BEYOND DRIFT, 4 are DRIFT, 0 TOO FEW TRADES; 3 of the 20 are UNMAPPED and not tested.** Rule fixed before the run (the Test 7 rule): BEYOND DRIFT = excess over the random-entry null > 0 AND real beats >= 95% of the 200 draws AND paired weekly bootstrap p <= 0.10; TOO FEW TRADES = fewer than 100 trades over the 160 weeks (no book falls under it: the smallest has 583 trades). All 17 grid cells reproduce the stored grid weekly points exactly in draw 0 (validated). Summed live mix: real **+$9001 per week for 1 lot of each of the 17 books vs null +$345** (excess +8657, beats 100% of draws, p 0.000). Sessions (1 lot of each mapped book, $/wk): Asia 3 books +1423 vs null +397; London 3 books +1457 vs -139; NY AM 7 books +4456 vs +643; NY PM 4 books +1665 vs -556 (all four sessions BEYOND DRIFT on the summed books).
2. **HOW MUCH THIS IS WORTH: very little as proof, because the live books were chosen on this same data.** The 20 live books were picked from the grid by looking at these weeks (hindsight), so beating a random-entry null here is the expected outcome, not an out-of-sample confirmation (Test 3 T2: of the 17 mapped, 4 never pass the Test 5 rule at any date and most of the others pass only after their good weeks). The null is also unusually weak for these brackets: the mean random-entry null is **negative for 8 of 17 books and for the NY PM and London mixes** (random entries with these brackets and costs lose money), so "beats drift" here mostly says the entry timing beats a coin, with a bracket that only pays with timing. Read it as: the live books' entries are not random in these 160 weeks; not as: they will beat drift going forward.
3. **By type (quick screen).** Level-module books: 3, BEYOND DRIFT 3 (mean excess 762); non-level: 14, BEYOND DRIFT 10 (mean excess 455). Both-sides books: 10, BEYOND DRIFT 8 (mean excess 592); long-only books: 7, BEYOND DRIFT 5 (mean excess 390). Only 3 of the 17 are level modules (VWAP, fib retracement on, profile nodes: Asia L9c2622b0, NY AM L43f0cbfb and Le4fede95) and only 1 of those trades both sides (Le4fede95), so the Test 7/8 finding (level, both sides) is a small slice of the live set: **the live books are mostly non-level books, so the Test 8 level-both result neither supports nor refutes them.**
4. **Down markets (NQ session return of the book's own session < 0 vs >= 0 in the week), summed live mix:** four sessions down weeks (66) real 4578 vs null -6298; up weeks (94) real 12107 vs null 5008. By session: Asia -556/-1655 down vs 2675/1695 up (real/null); London 359/-1706 down vs 2189/905 up (real/null); NY AM -327/-5860 down vs 8677/6381 up (real/null); NY PM 1450/-839 down vs 1874/-280 up (real/null). The Asia and NY AM mixes lose money in the weeks their own session falls (long tilt of their long-only books), London and NY PM stay positive; the per-book columns show which books.
5. **First vs second half (80 weeks each), summed live mix:** first half real 7159 vs null 7 (excess 7152, beats 100%); second half real 10844 vs null 682 (excess 10162, beats 100%). Recent first: L6M real 20576 vs null -727, L3M real 19848 vs null 1316.
6. **C, months the walk never used: 3 weeks, and they are not enough.** No stored month before 2023-04 exists for these cells, and Apr-Sep 2023 (weeks 0-25) were the qualification history of every date, so they are not clean. After the last stored grid week there are only **3 grid weeks (186-188, 2026-10-25 to 2026-11-14; week 187 has only 2 of 5 trading days of bars, Nov 2-4 missing)**. The Test 8 held list (week 182, 75 cells, 52 valid) scores on them **real -453 vs null -187 per held cell, 1 lot, basket average (excess -267, beats 32% of draws), 1 of 3 weeks positive**; on the 4 weeks held after its list date (182-185) +966 vs +193 (beats 99%). Three weeks of $1,000-scale noise decide nothing: **verdict INCONCLUSIVE (too few weeks)**; Asia and NY PM and London are negative in those 3 weeks, NY AM positive. Full table in section C.
7. **D, why the second half:** NQ's median daily range rose from **274 points (first 80 weeks) to 386 (second 80)**, +41%, and the second half is where the Test 8 excess sits (summed first half +70, second +526, from Test 8). The week-by-week link is weak: correlation of weekly excess with that week's NQ median daily range is 0.09 (Asia), -0.00 (NY AM), 0.35 (London), 0.38 (NY PM) on the weeks held. Two halves cannot separate "range" from "time" (April 7-10 2025 alone had four days of 1,400-2,650 points, all in the second half); see section D.
8. **Exact version (queued, lands late):** the engine CAN redraw entries. 17 books x 20 draws x 42-43 months = **14,380 set-months appended at the END of pending_nyam_gating.txt at 23:39Z** (200 draws would be 143,800: not queued). About 218,000 rows are ahead of them at about 14,000 rows per hour, so expect them roughly 15-17 h after the queue clears the older rows (about midday 11-27 to afternoon). Section E. **Also: queue_rows.py silently loses appends to this file (different lock from s2_pull.drop_line); my first 3 attempts vanished; check any rows queued with it.**

## A. THE 20 LIVE BOOKS vs THE DRIFT NULL (QUICK SCREEN, 200 draws; recent first)

Mapping: Test 3 T2 reproduced (W-ROTA fixed_spec; row/module/variant/params/bracket/side -> grid cell). Grid cells approximate the live definitions (exact vs quick-screen ratio in Test 3 exact section). **UNMAPPED, not guessed, not tested:** Asia L385f4f2e_CX502, NY AM B7bfd33b7, NY AM Bf428c4a1.BRS8U (no grid cell; the exact bare R0 sets exist for Bf428c4a1 only, see section E). Null = same engine, same signals, side, bracket, cost, one-position blocking; only the entry bar redrawn among the eligible bars of the same bar row in the same week and session. All numbers in $ per lot per week of the single book (draws are per book; the mix rows sum the books). Long share of trades: 100% for long-only books; for both-sides books = the share of trades the same cell makes long-only (standalone side runs, approximate: one-position blocking differs).

Books (each row: real / null; excess = real - null; beats = share of the 200 null draws real beats; p = paired weekly bootstrap of the excess, blocks of 4 weeks, one-sided):

| session | book | module | level book | both sides | trades | long share | L3M real / null | L6M real / null | all 160 wk real / null | excess | beats | paired p | NQ down wks real / null | NQ up wks real / null | first 80 real / null | second 80 real / null | Nov 2026 3 wk real / null | VERDICT |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | L385f4f2e_CX502 | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | **UNMAPPED (not tested)** |
| Asia | L4aaacdb2_R0_P30 | bands_vwap break | no | yes | 1007 | 52% | 669 / -43 | 582 / 0 | 321 / 134 | 187 | 0.965 | 0.041 | 446 / 111 (62) | 243 / 149 (98) | 130 / 167 | 513 / 101 | -1494 / -13 | **BEYOND DRIFT** |
| Asia | L9c2622b0_R0_P45 | levels_vwap break | yes | no | 1189 | 100% | 674 / 95 | 555 / -306 | 540 / 80 | 460 | 1.000 | 0.002 | -505 / -880 (62) | 1201 / 687 (98) | 494 / 180 | 585 / -20 | -236 / -328 | **BEYOND DRIFT** |
| Asia | Lb0e6dfa3_R0_F40_80 | structure_libpattern nr | no | no | 1049 | 100% | 1603 / -78 | 1218 / -147 | 562 / 183 | 379 | 1.000 | 0.003 | -496 / -886 (62) | 1232 / 859 (98) | 477 / 234 | 648 / 132 | -144 / 227 | **BEYOND DRIFT** |
| London | L12842dde.BRP45 | book_imb follow_native | no | no | 1832 | 100% | 628 / -516 | 522 / -215 | 88 / -15 | 103 | 0.725 | 0.239 | -1154 / -1426 (64) | 915 / 925 (96) | -32 / -37 | 207 / 7 | -441 / 599 | **DRIFT** |
| London | L19201dfc.BRF90_30 | xmarket_commod against_CL | no | yes | 1058 | 54% | 1041 / 61 | 1759 / -132 | 539 / -55 | 594 | 1.000 | 0.000 | 466 / -87 (64) | 587 / -34 (96) | 327 / -44 | 751 / -67 | 82 / 278 | **BEYOND DRIFT** |
| London | L74274eca.BRF120_60 | xmarket_rates with_ZB | no | yes | 1737 | 51% | 2269 / -464 | 1494 / -137 | 831 / -69 | 900 | 0.995 | 0.001 | 1047 / -194 (64) | 687 / 14 (96) | 740 / 8 | 921 / -146 | 73 / 751 | **BEYOND DRIFT** |
| NY AM | B7bfd33b7 | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | **UNMAPPED (not tested)** |
| NY AM | Bf428c4a1.BRS8U | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | **UNMAPPED (not tested)** |
| NY AM | L39287638.BRF80_40 | trend_ma_ema cross | no | yes | 848 | 50% | 591 / 41 | 1004 / -35 | 585 / -4 | 589 | 1.000 | 0.001 | 672 / -15 (75) | 508 / 5 (85) | 707 / -26 | 463 / 17 | -60 / -141 | **BEYOND DRIFT** |
| NY AM | L43f0cbfb.BRS8U | levels_fibr_on false_break | yes | no | 750 | 100% | 2627 / 694 | 2359 / 356 | 943 / 129 | 815 | 0.995 | 0.001 | -1146 / -2219 (75) | 2786 / 2201 (85) | 247 / -97 | 1639 / 354 | 4382 / 2051 | **BEYOND DRIFT** |
| NY AM | L4407508c.BRF120_60 | bands_bollinger walk | no | no | 732 | 100% | 1458 / 591 | 1405 / 276 | 631 / 296 | 334 | 0.980 | 0.034 | -438 / -721 (75) | 1574 / 1195 (85) | 279 / 219 | 983 / 374 | 2515 / 777 | **BEYOND DRIFT** |
| NY AM | L64390867.BRF80_40 | bands_avwap0830 break_0830_native | no | no | 583 | 100% | 191 / -48 | 287 / 31 | 188 / 106 | 82 | 0.770 | 0.240 | -300 / -352 (75) | 618 / 510 (85) | 55 / 90 | 321 / 122 | 1359 / 681 | **DRIFT** |
| NY AM | L8cfda948.BRF90_30 | tape_block b10_follow_sm | no | no | 2234 | 100% | 825 / 804 | 1660 / 225 | 689 / 128 | 560 | 0.990 | 0.016 | -608 / -1228 (75) | 1833 / 1325 (85) | 848 / 8 | 529 / 249 | 1064 / 733 | **BEYOND DRIFT** |
| NY AM | Le4fede95.BRF90_30 | levels_profile_nodes false_break_native | yes | yes | 3298 | 49% | 2353 / 387 | 2981 / -46 | 712 / -299 | 1010 | 0.995 | 0.006 | 1486 / -560 (75) | 28 / -68 (85) | 376 / -479 | 1047 / -119 | 2052 / -1041 | **BEYOND DRIFT** |
| NY AM | Lf0346d55.BRP60 | book_ofi follow_sm | no | yes | 2615 | 64% | 1196 / 103 | 1073 / 257 | 709 / 286 | 423 | 0.915 | 0.099 | 7 / -765 (75) | 1329 / 1214 (85) | 725 / 256 | 693 / 317 | -1361 / 57 | **DRIFT** |
| NY PM | L2c6916a5_R0_P60 | tape_div div_fade | no | yes | 1825 | 56% | 792 / 236 | 791 / -19 | 491 / -60 | 551 | 0.970 | 0.005 | 2 / -402 (79) | 968 / 274 (81) | 696 / 48 | 286 / -168 | 2115 / -533 | **BEYOND DRIFT** |
| NY PM | L4bdd521a_R0_F80_40 | xmarket_ym follow | no | yes | 1086 | 51% | 694 / -62 | 720 / -262 | 521 / -154 | 675 | 1.000 | 0.001 | 523 / -119 (79) | 519 / -188 (81) | 461 / -217 | 580 / -91 | 1847 / 857 | **BEYOND DRIFT** |
| NY PM | L52359bf4_R0_P30 | bands_atrchan fade_ext | no | yes | 3375 | 48% | 302 / -566 | 891 / -593 | 308 / -367 | 676 | 1.000 | 0.001 | 497 / -373 (79) | 124 / -362 (81) | 166 / -328 | 451 / -407 | -363 / -188 | **BEYOND DRIFT** |
| NY PM | L8e0bf58c_R0_S8U | xmarket_rates with_ZN | no | yes | 612 | 50% | 1934 / 82 | 1274 / 20 | 344 / 26 | 319 | 0.905 | 0.097 | 429 / 55 (79) | 262 / -3 (81) | 463 / 23 | 226 / 28 | -1149 / -413 | **DRIFT** |

A note on the column "NQ down wks": NQ session return of the book's own session (sum over the week) below zero. Nov 2026 3 wk = grid weeks 186-188, never in the stored grid and not used for anything (week 187 has 2 of 5 days of bars).

Session mixes and the four sessions summed (the mapped books at 1 lot each, $ summed per week; the unmapped books are not in the mix, so Asia is 3 of 4 books, NY AM 7 of 9):

| scope | books | L3M real / null | L6M real / null | all 160 wk real / null | excess | beats | paired p | max DD real / null | corr to NQ session | NQ down wks real / null | NQ up wks real / null | first 80 real / null (beats) | second 80 real / null (beats) | VERDICT |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Four sessions summed | 17 | 19848 / 1316 | 20576 / -727 | 9001 / 345 | 8657 | 1.000 | 0.000 | 60062 / 207172 | 0.32 | 4578 / -6298 (66) | 12107 / 5008 (94) | 7159 / 7 (100%) | 10844 / 682 (100%) | **BEYOND DRIFT** |
| Asia | 3 | 2946 / -26 | 2356 / -453 | 1423 / 397 | 1026 | 1.000 | 0.000 | 14492 / 39732 | 0.44 | -556 / -1655 (62) | 2675 / 1695 (98) | 1101 / 582 (96%) | 1746 / 212 (100%) | **BEYOND DRIFT** |
| London | 3 | 3938 / -918 | 3775 / -483 | 1457 / -139 | 1597 | 1.000 | 0.000 | 28293 / 88945 | 0.37 | 359 / -1706 (64) | 2189 / 905 (96) | 1035 / -73 (99%) | 1879 / -206 (100%) | **BEYOND DRIFT** |
| NY AM | 7 | 9242 / 2571 | 10769 / 1064 | 4456 / 643 | 3814 | 1.000 | 0.000 | 48273 / 141247 | 0.42 | -327 / -5860 (75) | 8677 / 6381 (85) | 3237 / -27 (100%) | 5676 / 1313 (100%) | **BEYOND DRIFT** |
| NY PM | 4 | 3722 / -310 | 3677 / -855 | 1665 / -556 | 2221 | 1.000 | 0.000 | 40161 / 141393 | 0.07 | 1450 / -839 (79) | 1874 / -280 (81) | 1786 / -474 (100%) | 1544 / -637 (100%) | **BEYOND DRIFT** |

Counts by type (BEYOND DRIFT / books): level books 3/3, non-level 10/14, both sides 8/10, long only 5/7. Level AND both sides: Le4fede95.BRF90_30 BEYOND DRIFT.

## C. INDEPENDENT CHECK WITHOUT NEW DATA (QUICK SCREEN)

**(1) Stored months.** Grid arrays and bar rows start 2023-04-02: **weeks 0-25 (2023-04 to 2023-09) exist** but are the qualification history of every re-qualify date (the first date is week 26), and of the week-182 list, so they are NOT held-out; they are shown only as a reference row. **Nothing exists before 2023-04** (no bars, no exact months; pre-2023 L2 not owned, memory/policy). After the grid end (week 185, ends 2026-10-24) the stored bar rows run to 2026-11-13 = **grid weeks 186, 187, 188 (2026-10-25..11-14); week 187 has bars for only 2 of 5 trading days (Nov 5-6; Nov 2-4 absent), weeks 186 and 188 have 5**. The stored grid weekly arrays (NW=186) do not contain them: they come from a gcore2x re-simulation of the same held cells (draw 0 equals the stored grid on weeks <186 for the cells used, cells that do not validate are dropped as in Test 8). Exact-engine months: the Test 8 primary cells' bare R0 sets exist for 2023-04..2026-10 (42 months, 2025-11 absent everywhere); **no exact month exists for 2026-11** for them (7 sets of other families have 202611). So the exact engine has no unused month for this list.

**(2) Scoring.** The list = units the Test 8 primary holds at week 182 (Asia 45 cells, London 1, NY AM 20, NY PM 9 = 75; 74 re-simulated, 52 valid; 1 Asia cell (trig_levels_sdx_vol1100) not re-simulable (own-bar signal), skipped). $/lot/week = sum of the cells' $ / number of cells (equal weight). Windows, recent first:

| scope | window | weeks | cells | real | null | excess | beats | weeks positive | NQ session return sum (points) |
|---|---|---|---|---|---|---|---|---|---|
| Four sessions summed | weeks 186-188 (2026-10-25..11-14), never used | 3 | 52 | -453 | -187 | -267 | 0.32 | 1 of 3 | 1512 |
| Four sessions summed | weeks 182-185 (2026-09-20..10-24), held after the list date, never used to qualify | 4 | 52 | 966 | 193 | 773 | 0.99 | 3 of 4 | -1914 |
| Four sessions summed | weeks 26-181, judging span before the list date (in-sample for the list) | 156 | 52 | 1048 | 28 | 1020 | 1.00 | 129 of 156 | 15835 |
| Four sessions summed | weeks 0-25 (2023-04..09), qualification history only (USED) | 26 | 52 | 580 | -15 | 595 | 1.00 | 18 of 26 | 943 |
| Asia | weeks 186-188 (2026-10-25..11-14), never used | 3 | 27 | -830 | -213 | -617 | 0.17 | 0 of 3 | 182 |
| Asia | weeks 182-185 (2026-09-20..10-24), held after the list date, never used to qualify | 4 | 27 | 1163 | -110 | 1273 | 0.99 | 3 of 4 | -307 |
| Asia | weeks 26-181, judging span before the list date (in-sample for the list) | 156 | 27 | 799 | -5 | 804 | 1.00 | 111 of 156 | 7362 |
| Asia | weeks 0-25 (2023-04..09), qualification history only (USED) | 26 | 27 | 105 | 6 | 99 | 0.97 | 13 of 26 | 432 |
| London | weeks 186-188 (2026-10-25..11-14), never used | 3 | 1 | -3982 | 297 | -4279 | 0.10 | 0 of 3 | 659 |
| London | weeks 182-185 (2026-09-20..10-24), held after the list date, never used to qualify | 4 | 1 | -2104 | -65 | -2039 | 0.26 | 1 of 4 | -503 |
| London | weeks 26-181, judging span before the list date (in-sample for the list) | 156 | 1 | 1336 | 17 | 1319 | 1.00 | 104 of 156 | 4104 |
| London | weeks 0-25 (2023-04..09), qualification history only (USED) | 26 | 1 | 344 | 70 | 273 | 0.74 | 14 of 26 | -136 |
| NY AM | weeks 186-188 (2026-10-25..11-14), never used | 3 | 17 | 874 | -151 | 1025 | 0.83 | 1 of 3 | 1096 |
| NY AM | weeks 182-185 (2026-09-20..10-24), held after the list date, never used to qualify | 4 | 17 | 1318 | 481 | 837 | 0.86 | 4 of 4 | -84 |
| NY AM | weeks 26-181, judging span before the list date (in-sample for the list) | 156 | 17 | 1368 | 55 | 1312 | 1.00 | 116 of 156 | 2601 |
| NY AM | weeks 0-25 (2023-04..09), qualification history only (USED) | 26 | 17 | 1204 | -69 | 1272 | 1.00 | 21 of 26 | 555 |
| NY PM | weeks 186-188 (2026-10-25..11-14), never used | 3 | 7 | -1718 | -240 | -1478 | 0.14 | 1 of 3 | -426 |
| NY PM | weeks 182-185 (2026-09-20..10-24), held after the list date, never used to qualify | 4 | 7 | -205 | 704 | -910 | 0.14 | 1 of 4 | -1020 |
| NY PM | weeks 26-181, judging span before the list date (in-sample for the list) | 156 | 7 | 1191 | 87 | 1104 | 1.00 | 103 of 156 | 1768 |
| NY PM | weeks 0-25 (2023-04..09), qualification history only (USED) | 26 | 7 | 929 | 19 | 910 | 1.00 | 18 of 26 | 91 |

Honest reading: the list was formed on weeks < 182, so its score on weeks 26-181 is in-sample. The clean weeks are 182-185 (4, held and never used to qualify it: the list holds up, +966 vs +193, beats 99%, 3 of 4 weeks positive) and 186-188 (3, with week 187 half empty: real -453 vs null -187, beats 32%, 1 of 3 weeks positive). **Seven weeks at most; three that are beyond the stored grid. That is not a test; it cannot confirm or reject a level of +300 $/lot/wk against a weekly noise of several thousand.** Per session in the 3 weeks: Asia -830 (27 cells), London -3,982 (1 cell), NY AM +874 (17), NY PM -1,718 (7).

**(3) Other index futures tape, owned, nothing bought or downloaded (box1 /mnt/l2 and server C):**

| symbol | what is owned | months / span | where |
|---|---|---|---|
| ES | mbp-10 L2 raw, 1 file per month | 2023-08 .. 2026-10 (39 months, incl. 2025-11) | box1 /mnt/l2/l2vast/raw/ES/ |
| ES | trades (parent symbology), monthly | 2023-02 .. 2026-10-30 (48 files) | box1 /mnt/l2/rootmoves/data_databento/ES/trades/ |
| ES | 1-min OHLCV continuous (volume roll, raw and back-adjusted) | 2013-01-02 .. 2026-10-16 (4.82 M bars) | box1 /mnt/l2/rootmoves/data_databento/ES, l2vast/ds3/cache_te2/ES.npz (also on C) |
| RTY | mbp-10 L2 raw | 2023-08 .. 2026-10 (39 months) | box1 /mnt/l2/l2vast/raw/RTY/ |
| RTY | trades (parent) | 2023-02 .. 2026-10-30 (48 files) | box1 /mnt/l2/rootmoves/data_databento/RTY/trades/ |
| RTY | 1-min OHLCV | 2017-07-09 .. 2026-10-16 (3.07 M bars) | cache_te2/RTY.npz |
| YM | 1-min OHLCV only (no trades, no L2) | 2013-01-02 .. 2026-10-16 (4.71 M bars) | cache_te2/YM.npz |
| MES | nothing found | - | - |

MES: not on disk on box1 or C (a micro would carry the ES price series anyway). Fee line: ES 4.84 RT; RTY and YM have no standard-size line (4.84 ES proxy; WEAK).

**Cost of running the same level modules on ES / RTY (posted as a LEAD NOTE; NOTHING STARTED, waiting for LEAD):** the level modules read bar rows with delta and book fields that exist for NQ only. (a) Prerequisite, not in set-months: build the time/range/tick bar rows for ES and RTY from the owned trades (and mbp-10 for the book/OFI/imbalance modules) for 2023-04..2026-10, about the 251 rows the grid uses; the NQ bar builder is not ported (time not measured; hours of cores). (b) Quick screen (gcore2x grid, as Tests 7 and 8): about 1,163 grid jobs per instrument, about 10 min wall on 32 niced processes once the bar rows exist. (c) Exact engine: not available for ES/RTY (the live replica, tick value $12.50 / $5.00, rollover handling, fee lines and depth fields are NQ-specific; _hist_replica_ES is empty, _hist_replica_RTY holds NQ day files). If it were ported, the Test 8 set of 606 ever-held cells x 42 months = **25,452 set-months per instrument** (50,904 for ES + RTY), about 2.8 h and 5.6 h at 9,000 set-months/h. YM could only be quick-screened on 1-min time bars (no delta/book).

## D. WHY THE SECOND HALF? Test 8 primary, first 80 vs second 80 weeks, per session and level type (QUICK SCREEN)

**NQ realised range** (stored bars; daily range = high minus low of each trading date over all sessions, median over the days of the week, then over the weeks of the half; points): first 80 weeks (2023-10-01 .. 2025-04-12) **median 274 / mean 308**; second 80 weeks (2025-04-13 .. 2026-10-24) **median 386 / mean 418** (+41% median). Mean session range (points): Asia 102 -> 189; London 117 -> 173; NY AM 195 -> 267; NY PM 173 -> 197. The second half contains the April 2025 tariff week (four days of 1,400-2,650 points) and the June 2026 spike (1,280-1,620).

Real = $/lot/wk of the held both-sides level cells of that type (sum of $ / units held, zero in weeks none held); null = random-entry null on the same valid cells (200 draws); excess = real - null; units = mean units held in the half (0.0 = nothing held, the 0/0/0 cells are not zero edge); r = Pearson (Spearman) correlation over the weeks held of the weekly excess with the weekly NQ median daily range. Types with fewer than 5 cells ever held are shown but not interpretable.

| session | level type | cells | units H1 / H2 | first 80: real / null / excess | second 80: real / null / excess | r (Spearman), excess vs weekly NQ daily range | r (Spearman), vs the session's own range |
|---|---|---|---|---|---|---|---|
| Asia | **all level types** | 95 | 6.7 / 10.9 | 32 / 64 / -32 | 599 / 47 / 553 | 0.09 (0.09) | 0.20 (0.17) |
| Asia | VWAP | 14 | 0.2 / 1.8 | 0 / -44 / 45 | 174 / -49 / 223 | 0.17 (0.21) | 0.31 (0.37) |
| Asia | fib | 15 | 0.0 / 2.6 | 0 / 0 / 0 | 233 / -10 / 244 | 0.28 (0.23) | 0.32 (0.30) |
| Asia | other levels | 16 | 1.5 / 1.5 | 183 / 42 / 141 | 269 / 91 / 178 | 0.32 (0.27) | 0.36 (0.24) |
| Asia | pivot | 4 | 0.0 / 1.2 | 0 / 0 / 0 | 294 / 9 / 285 | 0.24 (0.21) | 0.32 (0.31) |
| Asia | prior day / session / opens / range | 27 | 3.9 / 1.2 | 51 / 134 / -83 | 297 / -27 / 323 | 0.07 (0.05) | 0.01 (0.08) |
| Asia | profile / zones / stack | 14 | 0.7 / 2.3 | -30 / -80 / 50 | 558 / 35 / 523 | -0.02 (0.06) | 0.12 (0.15) |
| Asia | round numbers | 3 | 0.3 / 0.2 | 13 / -26 / 39 | 47 / -20 / 66 | 0.29 (0.09) | 0.22 (0.03) |
| Asia | swing S/R, trendline, channel | 2 | 0.2 / 0.2 | -71 / -9 / -62 | -109 / -82 / -27 | -0.16 (-0.08) | -0.07 (-0.01) |
| London | **all level types** | 61 | 10.4 / 0.5 | -78 / 30 / -109 | -57 / -7 / -49 | 0.35 (0.08) | 0.39 (0.13) |
| London | VWAP | 8 | 1.5 / 0.0 | -129 / 4 / -133 | 0 / 0 / 0 | 0.01 (0.01) | -0.25 (-0.17) |
| London | fib | 4 | 0.6 / 0.0 | -322 / 45 / -367 | 0 / 0 / 0 | -0.05 (-0.06) | -0.03 (-0.06) |
| London | other levels | 34 | 6.0 / 0.5 | 43 / 47 / -4 | 49 / -4 / 52 | 0.37 (0.08) | 0.39 (0.08) |
| London | pivot | 3 | 0.5 / 0.0 | -51 / -66 / 15 | 0 / 0 / 0 | 0.29 (0.23) | 0.33 (0.29) |
| London | prior day / session / opens / range | 8 | 1.3 / 0.0 | -67 / 9 / -76 | 0 / 0 / 0 | -0.41 (-0.37) | -0.53 (-0.33) |
| London | round numbers | 2 | 0.3 / 0.0 | -220 / -58 / -163 | 0 / 0 / 0 | -0.56 (-0.43) | -0.61 (-0.27) |
| London | swing S/R, trendline, channel | 2 | 0.2 / 0.1 | -148 / 25 / -173 | -105 / -3 / -102 | -0.04 (-0.13) | -0.01 (-0.16) |
| NY AM | **all level types** | 274 | 25.6 / 42.0 | 274 / 59 / 215 | 659 / 61 / 598 | -0.00 (0.05) | 0.11 (0.11) |
| NY AM | VWAP | 97 | 10.1 / 18.9 | 501 / 165 / 337 | 845 / 118 / 727 | -0.00 (0.00) | 0.06 (0.04) |
| NY AM | book walls | 2 | 0.0 / 0.6 | 0 / 0 / 0 | -4 / -55 / 51 | 0.04 (0.09) | 0.07 (0.18) |
| NY AM | fib | 24 | 1.3 / 4.5 | 227 / -87 / 314 | -217 / 71 / -288 | -0.28 (-0.15) | -0.23 (-0.07) |
| NY AM | other levels | 28 | 3.0 / 2.7 | -149 / -132 / -17 | 1048 / 133 / 915 | 0.19 (0.11) | 0.31 (0.18) |
| NY AM | pivot | 31 | 4.0 / 2.6 | 628 / 300 / 327 | 73 / -27 / 100 | 0.07 (0.08) | 0.12 (0.06) |
| NY AM | prior day / session / opens / range | 35 | 2.7 / 4.4 | -194 / -9 / -185 | 1255 / -99 / 1354 | 0.18 (0.18) | 0.29 (0.22) |
| NY AM | profile / zones / stack | 22 | 1.4 / 3.0 | -336 / -110 / -226 | -2 / 118 / -120 | -0.10 (0.06) | -0.08 (0.08) |
| NY AM | round numbers | 8 | 0.0 / 1.5 | 0 / 0 / 0 | 305 / 189 / 116 | 0.29 (0.21) | 0.38 (0.29) |
| NY AM | swing S/R, trendline, channel | 27 | 3.1 / 3.8 | 373 / -6 / 379 | 339 / -95 / 434 | -0.03 (0.04) | -0.05 (0.09) |
| NY PM | **all level types** | 57 | 6.8 / 8.5 | 153 / -47 / 201 | 427 / 48 / 379 | 0.38 (-0.00) | 0.51 (0.07) |
| NY PM | fib | 2 | 0.0 / 0.5 | 0 / 0 / 0 | -38 / 4 / -41 | 0.04 (0.21) | -0.10 (0.01) |
| NY PM | other levels | 3 | 0.0 / 0.4 | 0 / 0 / 0 | -150 / -1 / -149 | -0.43 (-0.45) | -0.44 (-0.50) |
| NY PM | pivot | 2 | 0.6 / 0.0 | 218 / 91 / 126 | 0 / 0 / 0 | 0.06 (-0.08) | 0.24 (0.13) |
| NY PM | prior day / session / opens / range | 1 | 0.2 / 0.0 | -134 / -41 / -93 | 0 / 0 / 0 | 0.12 (0.32) | 0.16 (0.19) |
| NY PM | profile / zones / stack | 3 | 0.5 / 0.0 | -308 / 22 / -330 | 0 / 0 / 0 | -0.24 (-0.21) | -0.29 (-0.15) |
| NY PM | round numbers | 2 | 0.3 / 0.0 | -267 / -53 / -214 | 0 / 0 / 0 | -0.54 (-0.48) | -0.37 (-0.37) |
| NY PM | swing S/R, trendline, channel | 44 | 5.2 / 7.6 | 280 / -51 / 331 | 445 / 73 / 372 | 0.36 (0.01) | 0.47 (0.07) |

Reading (honest): in Asia, NY AM and NY PM the second-half excess is far larger than the first half's (Asia -32 -> 553, NY AM 215 -> 598, NY PM 201 -> 379), with more units held in the second half (Asia 6.7 -> 10.9, NY AM 25.6 -> 42.0), and NQ's median daily range is 41% higher in the second half. But week by week the excess is **not** tied to range: Pearson (Spearman) correlation of the weekly excess with the weekly NQ median daily range is 0.09 (0.09) for Asia, -0.00 (0.05) for NY AM, 0.38 (-0.00) for NY PM, 0.35 (0.08) for London (one held cell, negative in both halves). So the data say "the second half is bigger and wilder", not "the edge is a volatility edge": the high-range weeks are not systematically the books' best weeks. With two halves, time and range cannot be separated; the second half also holds more units (the walk found more qualifying cells in 2026) and contains the April 2025 week. By type, the second-half excess is carried by prior-day/session/open levels, "other" levels and VWAP in NY AM, and by profile/zones, prior-day and pivot/fib levels in Asia; fib and profile/zones levels in NY AM go the other way (positive then negative).

## E. EXACT VERSION AND QUEUE STATUS

**What was built (box1, niced; code/th_test9/build_exact9.py):** the exact engine CAN redraw entries because an exact set reads its entries from an events parquet (ts, side, stop_pts, tgt_pts, lots, exit_ts). For each of the 17 mappable live books the existing bare R0 set (TL3_ALN_<S>_<id>_R0BR<bracket>, live definition, own bracket, fees in) is the REAL leg; 20 null sets TL3_ALN_<S>_<id>_T9X01..T9X20 are copies of the same set JSON (identical hooks, sizer, state, bracket) whose events file has every event's entry bar redrawn uniformly among the eligible bars of the same grid bar row in the same (week, session) (same rule as the quick screen), ts = bar close + 2 s, exit_ts = session end, then the standard cap_events. Events files /mnt/l2/l2vast/_rota/ev/T9X_<id>_<dd>.parquet (340 files, small), sets in exact/sets/ (340 files). No existing file changed.

**Count and queue:** 17 books x 20 draws = 340 sets; months = the months each real set has DONE (42, or 43 for 4 books): **14,380 set-months** (under the ~20k cap; 200 draws would be 143,800, not queued). Appended at the END of pending_nyam_gating.txt on 2026-11-26 23:39Z, all 14,380 present afterwards. Rows ahead of them: about 205,000; the file drains at about 4 rows/s (about 14,000 per hour), so **the 20-draw exact null lands roughly 15-17 h after the queue clears the older rows (about 15:00-17:00Z on 11-27), not in 1.6 h**; it is the last item by design. Scoring script ready: code/th_test9/exact9_score.py (real = existing R0 set, 20 draws, same verdict rule; with 20 draws "beats >= 95%" means real above at least 19 of 20 draws).

**Caveats of the exact null:** (1) two books use unit-scaled brackets (L43f0cbfb S8U, L8e0bf58c S8U): the redrawn events keep each original event's stop/target distance (set at the original bar), the quick screen recomputes it at the new bar; (2) the unmapped books have no grid bar row, so no redraw: Bf428c4a1 (events and R0 set exist, no grid cell) and L385f4f2e / B7bfd33b7 (no set) are NOT in the exact version; (3) the live events file is the REAL leg while the quick screen real leg is the grid cell; the two differ by the grid-vs-live definition gap (Test 3 exact section: exact/quick ratio and correlation per book).

**Queue finding for LEAD (infrastructure, not changed):** /mnt/l2/l2vast/_test5/queue_rows.py takes its flock on pending_nyam_gating.txt itself, but s2_pull.drop_line (th_s2/s2_pull.py) rewrites the whole file (tmp + os.replace) under a DIFFERENT lock, _split/.pend_lock, several times per minute; an append made with queue_rows.py in the window is written to the replaced inode and lost, while the script still prints "appended N". It lost my 14,380 rows three times in a row (0 present after a few seconds). I appended with an own script that takes .pend_lock first (code/th_test9/qrows9.py): the rows persisted. **Any earlier agent that queued rows with queue_rows.py may have lost rows silently; check that each queued set-month is in the file, in a lease or DONE.**


## Method and files
Code code/th_test9/ (build_jobs9, null_live, analysis9a, build_jobs9c, analysis9c, nqweek9, analysis9d, page9); server C /mnt/l2/l2vast/_test9 (jobs, out/*.npz null draws, res9a/c/d.pkl). Quick-screen caveats as Tests 7 and 8: weekly bins, approximate fills, grid cost, no stack rules; grid cells approximate the live definitions; null draws redraw the entry bar only (same signal count per week and session).

