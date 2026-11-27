# TEST 8: level books that trade BOTH sides, judged against drift (W-TEST8)

Written 2026-11-27 01:15 UTC. **QUICK SCREEN label on every number** (grid tape walk / gcore2x re-simulation, 1 NQ lot per held unit at $20/point, grid cost in, no stack rules, no account layers; 160 held weeks 2023-10 to 2026-10 = weeks 26..185 of the grid). Order: autopilot/DIRECTIVE_TEST8_2149Z.md (relay design under Josh's standing 18:22Z order, not Josh's words). One named primary, no best-of penalty. Exact rows are queued, see section F.

> **EXACT SECTION CORRECTED 01:15Z UTC: the earlier version of section F read only the two END months of each 13-week hold (SS.mon), so middle-month weeks counted as zero exact trades and the 'exact far weaker than quick' reading was wrong. Section F below is the corrected one.**

## ANSWER FIRST

1. **PRIMARY VERDICT (quick screen): summed PASS; Asia PASS; NY AM PASS; London FAIL; NY PM FAIL (beats the draws, p 0.141).** Rule fixed before the run: PASS = excess over the drift null > 0 AND real beats >= 95% of the 200 draws AND weekly paired bootstrap p <= 0.10. Summed: real **+339 $/lot/wk vs random-entry null +41 (excess +298, beats 100% of draws, paired p 0.018)**. Asia +316 vs +55 (excess +260, p 0.017); NY AM +467 vs +60 (excess +406, p 0.009); London -68 vs +11 (excess -79, beats 34%); NY PM +290 vs +0 (excess +290, beats 96%, p 0.141).
2. **HOW MUCH THIS IS WORTH (read this before using the PASS):** the both-sides level group was FOUND by looking at Test 7 (exploratory, one of about 8 groups x 5 scopes; Test 7 level-both: +343 vs +45, excess +298, p 0.021). Test 8 re-runs it as one named version on the SAME 160 weeks of data, with the candidate-set restriction applied inside the walk (family slots go to both-sides level books) instead of as a subset of the held books. The summed excess comes out at the same +298: this is **the same data judged a second time, NOT an out-of-sample confirmation.** The clean test is the forward register (A4-A5, N4-N5, scored weekly from now on) and the exact rows.
3. **The excess is almost all in the second half of the span.** Summed: first 80 weeks real +121 vs null +52 (excess +70, beats 76%), second 80 weeks real +557 vs +31 (excess +526, beats 100%). Asia first half excess **-32** (beats 34%), second half +553. NY AM +215 then +598. A both-sides level group that only works in the last 18 months is a regime fact, not a stable edge.
4. **Recent first (stored-grid basket, $/lot/wk, raw):** summed L3M **439**, L6M **340**, 2026 231, 2025 643, 2024 206, 2023 Q4 -262; Asia L3M 387 / L6M 689; NY AM L3M 686 / L6M 512. Against the drift null: summed L6M real 387 vs null -1 (beats 99%), L3M real 493 vs null 77. **Raw $/lot/wk 319 (plain p 0.007), max DD $16280 (null $10500), worst week $-4546.**
5. **Down markets (NQ session return < 0 vs >= 0, per scope):** summed the basket earns **595 $/lot/wk in the 66 weeks NQ fell vs 126 in the 94 weeks it rose** (null 64 / 25); correlation to NQ -0.11. Asia 345 down / 407 up; NY AM 536 / 374. This group does not lose when NQ falls (it trades both sides), which is the opposite of the long-only baskets of Test 7. No down-market weakness is hidden here.
6. **Robustness rows (reference only, not candidates):** t>=3 instead of 4: summed excess +94 (beats 100%, p 0.140) = **FAIL**, Asia PASS, NY AM FAIL, NY PM PASS (the larger basket, 749 units held at the end, dilutes the effect: the summed row does not pass at the looser bar). Without the largest level type (VWAP, 237 of 909 held cell-dates): summed excess +237 (beats 100%, p 0.038) = PASS. So the result is **not VWAP alone**, and it **weakens when the qualification bar is relaxed**.
7. **The two-sided clause did nothing here:** no long+short pair unit (a long cell and a short cell of the same book) was held on any date in any session, because short-only level cells almost never pass t>=4. Every held unit is a both-sides cell at full weight, so "half weight each" never applied. Implementation: see section G.
8. **Where it is thin:** London (1 unit held at the end, negative, FAIL) and NY PM (9 units, beats 96.5% of draws but p 0.141) do not pass; the two sessions that pass, Asia and NY AM, are the ones with the forward stacks. **Forward register:** A4-A5 (Asia) and N4-N5 (NY AM) drawn with seed 20261128 and appended to autopilot/FORWARD_REGISTER_STACKS.md (A1-A3 / N1-N3 untouched). **Exact:** held cells 3,025 set-months (2,921 already queued by earlier tests, 66 done, 38 new), four stacks bare + live layers 336 new set-months, queued at the END of pending_nyam_gating.txt; the exact drift null is NOT queued (605,000 set-months, about 67 h of the fleet, over the 60 h limit).

## A. THE PRIMARY BASKETS (QUICK SCREEN, stored grid weekly points; $/lot/wk of the held units, zero when none held; recent first)

| scope | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | $/lot/wk all 160 weeks | plain bootstrap p | max DD | worst week | units held first / mean / last | units ever | pair units ever held |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 387 | 689 | 830 | 410 | 46 | 173 | 383 | 0.004 | 8208 | -5706 | 5 / 15 / 45 | 140 | 0 |
| London | -647 | -324 | -200 | 154 | -277 | -198 | -108 | 0.835 | 19649 | -7562 | 57 / 7 / 1 | 75 | 0 |
| NY AM | 686 | 512 | 360 | 684 | 476 | -318 | 450 | 0.006 | 22411 | -6688 | 48 / 39 / 20 | 319 | 0 |
| NY PM | 167 | 686 | 15 | 993 | -4 | -602 | 282 | 0.108 | 25459 | -5373 | 9 / 10 / 9 | 72 | 0 |
| Four sessions summed | 439 | 340 | 231 | 643 | 206 | -262 | 319 | 0.007 | 16280 | -4546 | 119 / 70 / 75 | 606 | 0 |

Units held per re-qualify date (every 13 weeks from week 26; "last" = week 182):

| scope | wk 26 | wk 39 | wk 52 | wk 65 | wk 78 | wk 91 | wk 104 | wk 117 | wk 130 | wk 143 | wk 156 | wk 169 | wk 182 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 5 | 13 | 6 | 7 | 16 | 1 | 1 | 11 | 1 | 4 | 22 | 58 | 45 |
| London | 57 | 15 | 2 | 0 | 0 | 3 | 2 | 2 | 3 | 0 | 0 | 0 | 1 |
| NY AM | 48 | 19 | 19 | 13 | 37 | 34 | 43 | 37 | 48 | 85 | 74 | 33 | 20 |
| NY PM | 9 | 7 | 10 | 6 | 13 | 9 | 7 | 11 | 11 | 13 | 12 | 7 | 9 |
| Four sessions summed | 119 | 54 | 37 | 26 | 66 | 47 | 53 | 61 | 63 | 102 | 108 | 98 | 75 |

## B. DRIFT NULL (QUICK SCREEN, Test 7 part B method, 200 draws; VALID cells = draw-0 re-simulation equals the stored grid every week)

Same engine (gcore2x), same signals, side, bracket, cost and one-position blocking; only the entry bar is redrawn uniformly among the bars of the same bar row in the SAME week and session (same number of signals). Real and null always use the same valid cells and held weeks. PASS = excess > 0, real beats >= 95% of draws, paired weekly bootstrap p <= 0.10, **per session and summed, one version, no best-of penalty**.

| scope | cells held ever / valid | real $/lot/wk (valid cells) | null mean | excess | share of 200 draws real beats | paired weekly p | PASS | L6M real / null / excess | L6M share beaten | L3M real / null | max DD real / null |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 140 / 95 | 316 | 55 | 260 | 1.000 | 0.017 | **PASS** | 708 / -10 / 718 | 1.000 | 457 / -124 | 13072 / 14902 |
| London | 75 / 61 | -68 | 11 | -79 | 0.340 | 0.685 | **FAIL** | -324 / -10 / -314 | 0.255 | -647 / -20 | 29364 / 31184 |
| NY AM | 319 / 274 | 467 | 60 | 406 | 1.000 | 0.009 | **PASS** | 522 / 56 / 466 | 0.940 | 741 / 292 | 22126 / 12652 |
| NY PM | 72 / 57 | 290 | 0 | 290 | 0.965 | 0.141 | **FAIL** | 676 / 220 / 456 | 0.840 | -16 / 272 | 25690 / 32487 |
| Four sessions summed | 606 / 487 | 339 | 41 | 298 | 1.000 | 0.018 | **PASS** | 387 / -1 / 389 | 0.990 | 493 / 77 | 16716 / 10500 |

## C. NQ DOWN WEEKS vs UP WEEKS (QUICK SCREEN; per scope the NQ session return of that session, summed = all four sessions summed)

| scope | down weeks | real (valid) / null / raw | up weeks | real (valid) / null / raw | corr of the raw basket to NQ session return |
|---|---|---|---|---|---|
| Asia | 62 | 297 / 77 / 345 | 98 | 328 / 42 / 407 | 0.02 |
| London | 64 | -555 / -24 / -482 | 96 | 258 / 35 / 142 | 0.12 |
| NY AM | 75 | 535 / 46 / 536 | 85 | 406 / 73 / 374 | -0.05 |
| NY PM | 79 | 344 / -34 / 316 | 81 | 237 / 34 / 250 | 0.11 |
| Four sessions summed | 66 | 612 / 64 / 595 | 94 | 147 / 25 / 126 | -0.11 |

## D. ROBUSTNESS (REFERENCE ROWS ONLY, not candidates; the t>=3 and without-VWAP rows are full re-walks with their own held lists)

| row | scope | units held first / mean / last | raw $/lot/wk | real (valid) / null | excess | beats | paired p | PASS under the same rule | L6M excess | first 80 wk excess / beats | second 80 wk excess / beats |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRIMARY t>=4 | Asia | 5 / 15 / 45 | 383 | 316 / 55 | 260 | 1.000 | 0.017 | PASS | 718 | -32 / 0.34 | 553 / 1.00 |
| PRIMARY t>=4 | London | 57 / 7 / 1 | -108 | -68 / 11 | -79 | 0.340 | 0.685 | FAIL | -314 | -109 / 0.25 | -49 / 0.45 |
| PRIMARY t>=4 | NY AM | 48 / 39 / 20 | 450 | 467 / 60 | 406 | 1.000 | 0.009 | PASS | 466 | 215 / 0.95 | 598 / 1.00 |
| PRIMARY t>=4 | NY PM | 9 / 10 / 9 | 282 | 290 / 0 | 290 | 0.965 | 0.141 | FAIL | 456 | 201 / 0.84 | 379 / 0.96 |
| PRIMARY t>=4 | Four sessions summed | 119 / 70 / 75 | 319 | 339 / 41 | 298 | 1.000 | 0.018 | PASS | 389 | 70 / 0.77 | 526 / 1.00 |
| t>=3 | Asia | 32 / 202 / 414 | 172 | 156 / 10 | 146 | 1.000 | 0.060 | PASS | 538 | 46 / 0.93 | 245 / 1.00 |
| t>=3 | London | 332 / 58 / 15 | -133 | -80 / -65 | -15 | 0.435 | 0.564 | FAIL | 234 | -125 / 0.02 | 95 / 0.70 |
| t>=3 | NY AM | 354 / 373 / 234 | 145 | 120 / -19 | 139 | 1.000 | 0.147 | FAIL | -86 | 186 / 1.00 | 91 / 1.00 |
| t>=3 | NY PM | 93 / 94 / 86 | 138 | 144 / -59 | 203 | 1.000 | 0.061 | PASS | 412 | 195 / 1.00 | 211 / 1.00 |
| t>=3 | Four sessions summed | 811 / 727 / 749 | 91 | 69 / -25 | 94 | 1.000 | 0.140 | FAIL | 131 | 63 / 1.00 | 126 / 1.00 |
| t>=4 without VWAP | Asia | 4 / 13 / 35 | 374 | 301 / 65 | 236 | 1.000 | 0.030 | PASS | 570 | -33 / 0.34 | 505 / 1.00 |
| t>=4 without VWAP | London | 45 / 5 / 1 | -102 | -64 / 13 | -77 | 0.320 | 0.681 | FAIL | -314 | -105 / 0.26 | -49 / 0.45 |
| t>=4 without VWAP | NY AM | 40 / 24 / 13 | 323 | 337 / -4 | 341 | 1.000 | 0.035 | PASS | 516 | 194 / 0.89 | 488 / 0.99 |
| t>=4 without VWAP | NY PM | 9 / 10 / 9 | 282 | 290 / 0 | 290 | 0.965 | 0.141 | FAIL | 456 | 201 / 0.84 | 379 / 0.96 |
| t>=4 without VWAP | Four sessions summed | 98 / 52 / 58 | 238 | 244 / 7 | 237 | 1.000 | 0.038 | PASS | 411 | 37 / 0.67 | 436 / 1.00 |

## E. THE LIST TODAY: both-sides level books held at the last re-qualify date (week 182, data to 2026-10-25), Asia and NY AM (QUICK SCREEN)

Every book is a both-sides cell (module trig_levels_*); per-side numbers are the grid cells of the SAME book and bracket restricted to long entries only / short entries only (1 lot, $20/pt). Mark: LIVE-CELL / twin of a live book / D8Asia.cs module+variant (relay confirms) / new. "still" = still qualifies at the end of the span (week 186).


### Asia: 45 books (40 still qualify at the end)

| book id | level type | action | module | bar type and size | bracket | side | trades long / short | $/lot/wk long: 2023 / 24 / 25 / 26 | $/lot/wk short: 2023 / 24 / 25 / 26 | $/lot/wk book (both) | L6M | L3M | t, trades | still | mark | stack |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Wc162cc44 | VWAP | retest | vwap | swing atr_0.1 | sym30u | both | 587 / 556 | 175 / 394 / 720 / 1432 | 267 / -626 / 715 / 1426 | 1082 | 3129 | 2836 | 4.3, 1143 | yes | new |  |
| Wd3a72355 | prior day / session / opens / range | retest | mmove | tsf 5_400 | plain60/60 | both | 490 / 497 | 27 / 378 / 256 / 706 | 111 / -43 / 184 / 1208 | 680 | 2360 | 2732 | 4.7, 987 | yes | new |  |
| W16b75d89 | prior day / session / opens / range | retest | mmove | tsf 5_400 | plain60/60 | both | 490 / 497 | 27 / 378 / 256 / 706 | 111 / -43 / 184 / 1208 | 680 | 2360 | 2732 | 4.7, 987 | yes | new |  |
| W601363ff | profile / zones / stack | break | stack | tsf 5_50 | plain60/60 | both | 909 / 862 | -35 / 542 / 841 / 1124 | -49 / -95 / 442 / 1310 | 1023 | 3072 | 2659 | 4.3, 1771 | yes | new |  |
| We0dbec32 | fib | break | fibr_pd | lbrk 5_10 | fixed60/120 | both | 711 / 710 | -135 / 828 / 817 / 1505 | -40 / -11 / 607 / 1123 | 1191 | 3118 | 2160 | 4.1, 1421 | yes | new |  |
| Wf06d4bb3 | VWAP | retest | vwap | swing atr_0.1 | sym30u | both | 587 / 553 | 201 / 405 / 637 / 1422 | 273 / -638 / 596 / 1587 | 1065 | 2729 | 2105 | 4.2, 1140 | yes | new |  |
| W2ff619a2 | VWAP | retest | vwap | dchg 10 | sym30u | both | 586 / 561 | 121 / 520 / 946 / 1505 | 160 / -581 / 725 / 1231 | 1136 | 2359 | 2059 | 4.3, 1147 | yes | new |  |
| W734be63f | swing S/R, trendline, channel | break | channel | tsf 10_60 | plain60/60 | both | 690 / 626 | -15 / 627 / 599 / 902 | 94 / -17 / 236 / 822 | 814 | 1823 | 2045 | 4.7, 1316 | yes | new |  |
| W86dbdd4b | VWAP | retest | vwap | kagi 10 | asym15u/30u | both | 595 / 572 | 81 / 489 / 893 / 1492 | 126 / -589 / 670 / 1236 | 1077 | 2342 | 2032 | 4.1, 1167 | yes | new |  |
| W73585da1 | VWAP | retest | vwap | pnf 7 | fixed120/120 | both | 539 / 539 | 194 / 487 / 450 / 1397 | 145 / -548 / 596 / 1420 | 988 | 2618 | 2026 | 4.6, 1078 | yes | new | A4 |
| W0d8714f7 | pivot | break | piv_floor | tsf 10_250 | plain60/60 | both | 415 / 426 | 112 / 430 / 344 / 903 | 112 / 119 / 207 / 328 | 635 | 1239 | 1891 | 4.3, 841 | yes | new | A5 |
| W595a69f1 | pivot | break | piv_floor | tsf 10_250 | plain60/60 | both | 415 / 426 | 112 / 430 / 344 / 903 | 112 / 119 / 207 / 328 | 635 | 1239 | 1891 | 4.3, 841 | yes | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W1539c680 | other levels | break | swsr5 | tsf 10_30 | plain60/60 | both | 1001 / 953 | 151 / 768 / 498 / 317 | 234 / -133 / 516 / 1365 | 927 | 1936 | 1437 | 4.1, 1954 | yes | new | A5 |
| Wc91c258f | supply-demand (sd/sdx) | break | sdx_vol1100 | tsf 10_250 | plain60/60 | both | 510 / 434 | -64 / 511 / 310 / 752 | 57 / -4 / 360 / 631 | 644 | 997 | 1424 | 4.1, 944 | yes | new |  |
| W7af015ca | fib | false_break | fibr_on | urenko 14 | sym30u | both | 96 / 74 | 61 / 313 / 271 / 876 | -77 / -14 / 136 / 241 | 449 | 1272 | 1410 | 4.1, 170 | yes | new |  |
| Wa7df403e | other levels | false_break | ob15 | tsf 10_60 | plain60/60 | both | 129 / 81 | 169 / 74 / 162 / 490 | -12 / -8 / 186 / 220 | 311 | 1090 | 1322 | 4.7, 210 | yes | new |  |
| Wb7866527 | prior day / session / opens / range | break | mmove | tsf 5_200 | plain60/60 | both | 743 / 694 | 122 / 508 / 194 / 849 | 183 / -111 / 460 / 340 | 630 | 1779 | 1265 | 4.0, 1437 | yes | new |  |
| Wf5779582 | other levels | false_break | ob15 | tsf 10_60 | plain60/60 | both | 130 / 81 | 169 / 68 / 162 / 459 | -12 / -8 / 186 / 229 | 304 | 945 | 1249 | 4.4, 211 | yes | new | A4 |
| W4a911926 | other levels | break | ob15 | tsf 10_60 | plain60/60 | both | 135 / 83 | 158 / 74 / 107 / 562 | -12 / -8 / 186 / 241 | 314 | 993 | 1127 | 4.5, 218 | yes | new | A5 |
| W4ebf9569 | other levels | break | ob15 | tsf 10_60 | plain60/60 | both | 135 / 83 | 158 / 74 / 107 / 562 | -12 / -8 / 186 / 241 | 314 | 993 | 1127 | 4.5, 218 | yes | new |  |
| W3a3821c8 | profile / zones / stack | break | profile_nodes | time m_90 | fixed80/40 | both | 465 / 415 | 1 / 233 / 317 / 189 | 35 / 88 / 263 / 660 | 455 | 1275 | 1100 | 4.1, 880 | yes | new |  |
| W87b89d8f | VWAP | retest | vwap | dchg 10 | sym30u | both | 596 / 548 | 182 / 545 / 890 / 1327 | 217 / -546 / 693 / 1055 | 1072 | 1774 | 983 | 4.3, 1144 | yes | new | A5 |
| W122d180c | VWAP | retest | vwap | kagi 10 | sym30u | both | 596 / 548 | 179 / 542 / 887 / 1325 | 215 / -548 / 691 / 1053 | 1067 | 1768 | 978 | 4.3, 1144 | yes | new |  |
| W09ce65c4 | fib | false_break | fibr_ib | urenko 56 | fixed90/90 | both | 137 / 135 | 45 / 185 / 379 / 622 | 84 / -56 / 360 / 154 | 449 | 989 | 912 | 4.4, 272 | yes | new |  |
| W3e82c655 | other levels | break | swsr5 | tsf 5_400 | plain60/60 | both | 749 / 709 | 77 / 433 / 339 / 503 | 93 / -222 / 610 / 677 | 632 | 920 | 895 | 4.2, 1458 | yes | new |  |
| W65dc0e76 | other levels | break | fib15 | tsf 5_400 | plain60/60 | both | 728 / 700 | 5 / 408 / 669 / 243 | 20 / -230 / 494 / 981 | 663 | 1292 | 861 | 3.8, 1428 | NO | new | A4 |
| Wa1810e2f | pivot | break | piv_floor | tsf 25_150 | plain60/60 | both | 248 / 236 | 47 / 294 / 477 / 370 | 81 / 83 / 167 / 520 | 517 | 870 | 796 | 4.6, 484 | yes | new |  |
| Waf483534 | pivot | break | piv_floor | tsf 25_150 | plain60/60 | both | 248 / 236 | 47 / 294 / 477 / 370 | 81 / 83 / 167 / 520 | 517 | 870 | 796 | 4.6, 484 | yes | module+variant also in D8Asia.cs (relay confirms the book) |  |
| W475d3483 | prior day / session / opens / range | break | prior_day | frenko 28 | fixed80/40 | both | 719 / 635 | 184 / 506 / 715 / 435 | 225 / -72 / 130 / 532 | 666 | 928 | 795 | 3.6, 1354 | NO | new |  |
| W0e7037ba | profile / zones / stack | retest | profile_nodes | lbrk 3_40 | fixed120/60 | both | 222 / 232 | 66 / 321 / 376 / 333 | 114 / 208 / 329 / 593 | 596 | 649 | 785 | 5.1, 454 | yes | new | A4 |
| Wd438d2d7 | profile / zones / stack | break | profile_nodes | time m_90 | fixed80/40 | both | 474 / 415 | 38 / 251 / 380 / 386 | 94 / 182 / 307 / 411 | 524 | 1051 | 781 | 4.5, 889 | yes | new |  |
| W8da69b05 | other levels | false_break | ob5 | tsf 2_700 | sym15u | both | 303 / 203 | -88 / 223 / 516 / 717 | 85 / -46 / 219 / 537 | 541 | 964 | 772 | 3.9, 506 | NO | new |  |
| Wff6cb74e | other levels | false_break | ob5 | tsf 2_700 | sym15u | both | 303 / 203 | -88 / 223 / 516 / 717 | 85 / -46 / 219 / 537 | 541 | 964 | 772 | 3.9, 506 | NO | new | A5 |
| We7eba185 | fib | break | fibr_pd | tsf 25_40 | plain60/60 | both | 490 / 454 | 26 / 366 / 382 / 614 | 85 / 141 / 494 / 538 | 675 | 1186 | 612 | 4.2, 944 | yes | new | A4 |
| W4ad3a33c | fib | break | fibr_pd | tsf 25_40 | plain60/60 | both | 490 / 454 | 26 / 366 / 382 / 614 | 85 / 141 / 494 / 538 | 675 | 1186 | 612 | 4.2, 944 | yes | new |  |
| W0fe67991 | VWAP | break | vwap | lbrk 3_10 | plain60/60 | both | 942 / 894 | 202 / 716 / 406 / 646 | 308 / 78 / 308 / 1245 | 960 | 1593 | 579 | 4.2, 1836 | yes | new |  |
| Wfac9ed8a | fib | false_break | fibr_on | frenko 40 | fixed30/90 | both | 169 / 153 | 69 / 320 / 178 / 358 | 39 / 205 / 69 / 356 | 401 | 821 | 564 | 4.4, 322 | yes | new |  |
| W0778abb1 | fib | false_break | fibr_on | frenko 40 | fixed30/90 | both | 169 / 153 | 69 / 320 / 178 / 358 | 39 / 205 / 69 / 356 | 401 | 821 | 564 | 4.4, 322 | yes | new | A5 |
| W0177408f | profile / zones / stack | false_break | profile_nodes | renko 40 | fixed40/80 | both | 635 / 722 | -140 / 444 / 414 / 852 | -64 / 94 / 234 / 1202 | 756 | 1690 | 564 | 4.2, 1357 | yes | new |  |
| W68089a3e | pivot | break | piv_floor | tsf 5_400 | plain60/60 | both | 489 / 453 | -30 / 212 / 357 / 383 | 129 / -126 / 714 / 604 | 573 | 664 | 473 | 4.1, 942 | yes | module+variant also in D8Asia.cs (relay confirms the book) | A4 |
| Wdd474052 | other levels | break | swsr5 | tsf 25_150 | plain60/60 | both | 346 / 284 | -9 / 343 / 347 / 427 | 56 / 73 / 190 / 537 | 497 | 501 | 270 | 4.3, 630 | yes | new |  |
| W3aaf3468 | other levels | break | swsr5 | tsf 25_150 | plain60/60 | both | 346 / 284 | -9 / 343 / 347 / 427 | 56 / 73 / 190 / 537 | 497 | 501 | 270 | 4.3, 630 | yes | new |  |
| Wc171ec63 | profile / zones / stack | retest | profile_nodes | lbrk 3_40 | fixed120/60 | both | 144 / 132 | 33 / 160 / 313 / 370 | 54 / 33 / 157 / 209 | 338 | 295 | 82 | 3.8, 276 | NO | new |  |
| W995e01d9 | VWAP | false_break | vwap | frenko 40 | sym15u | both | 534 / 563 | 15 / 679 / 475 / 1510 | 334 / -384 / 346 / 1208 | 1004 | 2434 | -596 | 4.0, 1097 | yes | new |  |
| Wa07a8fb3 | VWAP | false_break | vwap | frenko 40 | sym15u | both | 534 / 563 | 15 / 679 / 475 / 1510 | 334 / -384 / 346 / 1208 | 1004 | 2434 | -596 | 4.0, 1097 | yes | new |  |

### NY AM: 20 books (19 still qualify at the end)

| book id | level type | action | module | bar type and size | bracket | side | trades long / short | $/lot/wk long: 2023 / 24 / 25 / 26 | $/lot/wk short: 2023 / 24 / 25 / 26 | $/lot/wk book (both) | L6M | L3M | t, trades | still | mark | stack |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Wbb4ef729 | VWAP | break | vwap | swing pct_5 | sym15u | both | 804 / 814 | 874 / 575 / 712 / 1740 | 784 / -128 / 1714 / 1348 | 1861 | 2715 | 3708 | 4.9, 1618 | yes | new | N4 |
| Wbcfa80fb | prior day / session / opens / range | false_break | prior_day | swing atr_0.25 | fixed120/120 | both | 512 / 533 | 477 / 137 / 1001 / 1382 | 283 / 101 / 1561 / 1148 | 1527 | 3554 | 3470 | 4.9, 1045 | yes | new | N4 |
| Wa4b747b2 | prior day / session / opens / range | false_break | prior_day | swing atr_0.25 | fixed120/120 | both | 512 / 533 | 477 / 137 / 1001 / 1382 | 283 / 101 / 1561 / 1148 | 1527 | 3554 | 3470 | 4.9, 1045 | yes | new |  |
| Wb1ab799c | VWAP | break | vwap | dchg 28 | asym15u/30u | both | 814 / 810 | 866 / 719 / 488 / 1960 | 752 / 207 / 1352 / 489 | 1675 | 1243 | 3072 | 4.5, 1624 | yes | new | N5 |
| W050c781f | VWAP | break | vwap | kagi 28 | asym15u/30u | both | 814 / 810 | 866 / 718 / 487 / 1959 | 751 / 206 / 1352 / 488 | 1674 | 1241 | 3070 | 4.5, 1624 | yes | new |  |
| W10e7f4cd | prior day / session / opens / range | false_break | prior_day | dchg 14 | sym8u | both | 717 / 695 | 604 / -35 / 552 / 1110 | 297 / 180 / 1181 / 1321 | 1272 | 3815 | 2985 | 4.1, 1412 | yes | new | N5 |
| Wca8c5296 | prior day / session / opens / range | false_break | prior_day | kagi 14 | sym8u | both | 717 / 695 | 603 / -35 / 551 / 1110 | 296 / 179 / 1180 / 1320 | 1271 | 3814 | 2984 | 4.1, 1412 | yes | new |  |
| Wf74d00e3 | prior day / session / opens / range | false_break | prior_day | dchg 20 | fixed120/120 | both | 516 / 527 | 446 / 173 / 872 / 1238 | 246 / 97 / 1569 / 838 | 1385 | 2809 | 2640 | 4.5, 1043 | yes | new | N5 |
| W170cb5a0 | prior day / session / opens / range | false_break | prior_day | renko 20 | fixed120/60 | both | 671 / 691 | 321 / 154 / 1008 / 760 | 34 / 242 / 1351 / 561 | 1155 | 2152 | 2453 | 3.9, 1362 | NO | new |  |
| W3b484778 | prior day / session / opens / range | false_break | prior_day | urenko 20 | fixed120/60 | both | 679 / 691 | 313 / 223 / 895 / 874 | 65 / 339 / 1304 / 704 | 1219 | 2151 | 2359 | 4.1, 1370 | yes | new | N5 |
| Wc1c42940 | prior day / session / opens / range | false_break | prior_day | urenko 20 | fixed120/60 | both | 678 / 689 | 313 / 223 / 895 / 760 | 65 / 339 / 1351 / 618 | 1187 | 2059 | 2267 | 4.1, 1367 | yes | new |  |
| W3e503490 | prior day / session / opens / range | false_break | prior_day | pnf 5 | sym8u | both | 838 / 839 | 565 / -3 / 758 / 655 | 420 / 577 / 1037 / 868 | 1222 | 2750 | 2229 | 4.1, 1677 | yes | new | N5 |
| We3999e99 | fib | reject | fibr_dev | pnf 7 | asym15u/30u | both | 330 / 287 | 613 / 510 / 237 / 591 | 335 / 609 / 332 / 616 | 946 | 1542 | 1632 | 4.1, 617 | yes | new | N4 |
| Wd5038cce | prior day / session / opens / range | false_break | prior_day | kagi 28 | sym15u | both | 514 / 536 | 513 / 100 / 803 / 1262 | 318 / 266 / 1255 / 731 | 1313 | 2327 | 1321 | 4.5, 1050 | yes | new | N5 |
| W96a06db2 | VWAP | break | vwap | tsf 5_100 | sym15u | both | 820 / 784 | 667 / 1113 / 816 / 1188 | 457 / 589 / 1549 / 1683 | 2033 | 2995 | 470 | 4.8, 1604 | yes | new |  |
| W24cfa010 | VWAP | break | vwap | pnf 7 | sym30u | both | 788 / 799 | 1039 / 768 / 632 / 593 | 739 / 138 / 1589 / 182 | 1434 | 613 | 323 | 4.1, 1587 | yes | new |  |
| Wc7c3f9c5 | VWAP | break | vwap | pnf 7 | sym30u | both | 788 / 799 | 1039 / 768 / 632 / 593 | 739 / 138 / 1589 / 182 | 1434 | 613 | 323 | 4.1, 1587 | yes | new | N4 |
| W5ba295af | pivot | retest | piv_wf | urenko 40 | sym30u | both | 595 / 642 | 704 / 474 / 334 / 1323 | -18 / 472 / 1238 / 504 | 1269 | 2483 | 10 | 4.1, 1237 | yes | new | N4 |
| W9fd5ca5d | pivot | reject | piv_floor | pnf 10 | fixed60/120 | both | 330 / 328 | 987 / 553 / 302 / -8 | 378 / 416 / 368 / 166 | 784 | 106 | -97 | 4.0, 658 | yes | new | N4 |
| W5b6fa37d | VWAP | break | vwap | tsf 5_100 | sym15u | both | 819 / 743 | 508 / 762 / 1269 / 765 | 432 / 378 / 2121 / 703 | 1813 | 1401 | -937 | 4.9, 1562 | yes | new |  |

London had 1 book and NY PM 9 books held at the last date (not listed; no forward stacks for them).

## F. FORWARD REGISTER AND EXACT ROWS

Forward register (seed 20261128, drawn once, never re-drawn): in autopilot/FORWARD_REGISTER_STACKS.md section "ADDED BY W-TEST8", scored weekly with A1-N3.

| stack | session | list size | level modules | module repeat needed | book ids |
|---|---|---|---|---|---|
| A4 | Asia | 45 | vwap, fibr_pd, piv_floor, profile_nodes, ob15, fib15 | no | W73585da1, We7eba185, W68089a3e, W0e7037ba, Wf5779582, W65dc0e76 |
| A5 | Asia | 45 | ob5, swsr5, vwap, ob15, fibr_on, piv_floor | no | Wff6cb74e, W1539c680, W87b89d8f, W4a911926, W0778abb1, W0d8714f7 |
| N4 | NY AM | 20 | prior_day, vwap, fibr_dev, piv_floor, piv_wf, vwap | yes | Wbcfa80fb, Wc7c3f9c5, We3999e99, W9fd5ca5d, W5ba295af, Wbb4ef729 |
| N5 | NY AM | 20 | prior_day, vwap, prior_day, prior_day, prior_day, prior_day | yes | W3b484778, Wb1ab799c, Wf74d00e3, W3e503490, W10e7f4cd, Wd5038cce |

Overlap with the Test 6 stacks: Wbcfa80fb (N4) is also in N1 and Wf74d00e3 (N5) is also in N3; A4/A5 share nothing with A1-A3. The draw avoided reuse only inside its own draw.

Exact rows queued 22:01Z at the END of /mnt/l2/l2vast/_split/pending_nyam_gating.txt via _test5/queue_rows.py under its lock: held cells bare R0 (TL3_ALN_<AS|LO|NY|NP>_<id>_R0RT, 606 cells, 3,025 set-months of the held periods; 2,921 already in the queue from Tests 4-7/Q1, 66 done, 38 new; 8 cells needed stage-B event files, built), stacks TL3_SR_<AS|NY>_T8<A4|A5|N4|N5>_BARE and _LY (bare and with the session live account layers: Asia JT275 = STK8, SZW3, CGB1, DLA4, DLB14, DLC4; NY AM JT162 = BL6, CAP6, STK7, SZW2, NTS2, CGB2; 42 months, 1 lot per book, per-book Trade Health not applied) = 336 new set-months. Rows ahead of the new rows when queued: about 241,700. Served at about 8,500-9,000 rows/h: new rows come up about 27-28 h later (Fri 28 Nov early); the held-cell rows already in the queue sit at positions 7.6k to 200k (median 14.8k).

Exact held-period status (refreshed 01:15 UTC; re-run code/th_test8/exact8.py then page8.py). **Corrected: every hold is expanded to ALL its calendar months (4-5 per 13-week hold); a period counts only when all its months are DONE. Month 2025-11 is not in the fleet: its weeks (starting 2025-11-02..30) are dropped on both the exact and the quick side.** Exact = bare R0, own bracket, 1 lot per held cell, fees in, equal weight over the units held that week; quick = grid points for the same periods and weeks.

| session | held periods landed | of | exact $/lot/wk | quick $/lot/wk (same periods) | exact / quick |
|---|---|---|---|---|---|
| Asia | 137 | 144 | 365 | 340 | 1.07 |
| London | 75 | 75 | -198 | -159 | 1.25 |
| NYAM | 329 | 336 | 581 | 445 | 1.31 |
| NYPM | 74 | 75 | 329 | 227 | 1.45 |
| four sessions pooled (sum of $ / sum of units held that week) | 615 | 630 | 409 | 295 | 1.39 |

Stacks A4-A5 / N4-N5 (42 months each, all must be DONE): TL3_SR_AS_T8A4_BARE 0 of 42; TL3_SR_AS_T8A4_LY 0 of 42; TL3_SR_AS_T8A5_BARE 0 of 42; TL3_SR_AS_T8A5_LY 0 of 42; TL3_SR_NY_T8N4_BARE 0 of 42; TL3_SR_NY_T8N4_LY 0 of 42; TL3_SR_NY_T8N5_BARE 0 of 42; TL3_SR_NY_T8N5_LY 0 of 42.


Exact drift null: **not queued.** Count: 3,025 held-cell set-months x 200 draws = 605,000 set-months = about 67 h of the whole fleet at 9,000/h (over the 60 h limit). Option for LEAD: 20 draws = 60,500 set-months, about 6.7 h of fleet. The quick-screen null is the same engine on the same signals (draw 0 reproduces the stored grid weekly points exactly for 487 of 606 cells, 80%).

## G. METHOD AND CAVEATS

- **Walk:** th_test6/walk6.py candidate set (3) (print-rule bar types and stale level cells removed) with the Test 5 primary rule unchanged (N>=100 trades, t>=4, >=75% profitable half-years, family share >=70%, trailing 26 weeks profitable, re-qualify every 13 weeks, lower-median bracket per book, one book per test-2 family = most trades, hold ALL, equal weight, 13 weeks), code th_test8/walk8.py. **Both-sides implementation:** the candidate set is first restricted to level-module cells (module name trig_levels_*) that are either both-sides cells (mode "both"), or long-only / short-only cells whose (bar row, module params) has both a long and a short cell in the grid; family-share statistics are computed on that restricted set (as Test 6 did for its sets). At each date each (row, params, side) book gets its lower-median qualified bracket; a unit is then (a) a both-sides cell, or (b) a long cell and a short cell of the same (row, params) that BOTH qualify at that date, held as one unit with each cell at half weight (unit $ = mean of the two cells; counts as one book; family and trade count from the pair). A held pair is dropped when either cell fails the cell rule. Case (b) never occurred.
- **Null:** th_test7 method (code th_test8/null_run.py = th_test7/null_run.py, same gcore2x tables), 200 draws, 5,968 re-simulated cells across the primary and the two reference runs, VALID cells only in the headline rows. Paired weekly bootstrap: block 4 weeks, 2,000 draws, centred, difference real minus mean-null per week.
- **Why it is not independent:** same 160 weeks and the same cells as Test 7. Selection of the group by looking (Test 7), then judged alone here. Also: VWAP is the largest level type by held cell-dates, and the NY AM list is dominated by prior-day books, so N4/N5 share modules. The exact rows and the forward weeks are the checks that can still fail.
- Files: code/th_test8/ (walk8.py, build_jobs8.py, analysis8.py, partc8.py, draw8.py, register8.py, stageb_build8.py, stacks8_build.py, exact8.py, page8.py); server C /mnt/l2/l2vast/_test8 (res8.pkl, partc8.json, out/); box1 /mnt/l2/l2vast/_test8 (draws8.json, rows_T8.txt, rows_STK.txt, cells_T8.json).
