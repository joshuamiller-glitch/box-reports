# DS3_TARGET_REPLAY_BOOK - family i (IN-TRADE EXIT from the book and tape) and the live profit-side state lines on the clean replica (W-LB2, 2026-11-16, first version ~17:00Z)
Order: DIRECTIVE_BRACKET_DD_20261116.md ORDER 3 addendum 2, items (i) and the profit-side question. Replay only (no engine). Rows for W-RP's table: /mnt/l2/l2vast/_replay/arr_i_book.npz (48 rule ids `i_T<t0>_<sig><par>`, schema README_schema.txt; rpts = favourable points at the alt exit incl. 0.8 pt slip, NaN = trade untouched); top-2 JSON: /mnt/l2/l2vast/_replay/step1_top2_book.json (per book and per book|session; `by_dd` and `keep60`). Code: code/th_lcb2/{book_replay.py, book_metrics.py, book_md.py, profit_lines.py}.
**VERDICT (plain): in-trade exits from the book/tape do NOT deliver a dynamic target that beats the real exits on drawdown without giving up most of the mean. Every cell fires on 70-90 % of trades (the +10/+15/+20 arm is hit and one of the four conditions is nearly always true), so each cell behaves like a fixed take at +T0 and the book/tape condition adds little over the plain fixed-take control (table below). Per book (best cell by DD vs real exits): A7 DD -32 % at 62 % of the real mean, H7 -54 % at 33 %, O7 -51 % at 19 %, U7 -35 % at 57 %, K7 -20 % at 0.2 % of the mean ($4 vs $2,201/wk); M7 and P7 get WORSE max DD than the real exits (M7 80.1k vs 64.5k, P7 63.9k vs 43.1k) because their winners are cut at +10..+20 while the stops stay. The cells differ from the fixed-take control by a few percent of DD only (section 2). Strength: WEAK for family i: the MedLevel and "level ahead" inputs are proxies (below), so the conditions are not the live definitions. Nothing here is a CONFIRMED rule.**
## 1. Method, coverage, caveats (stated, not hidden)
- Trades: JL2 trade list, 43 months (18,977 rows with fills; 32 trades without cf2 coverage skipped; trades that cross a file boundary use two day files). Real entry price and real exit price kept; each alternative: exit = the earlier of (alt fires) and (real exit); alt exit price = mid(next second) - 0.8 pt in the trade's direction (engine convention); net = real net + (alt gross - real gross) (fees unchanged). **The replay ignores freed-book re-entries** (a trade closed earlier does not free the book for another entry), exactly as W-RP's replay does.
- Per-second tape: /mnt/l2/l2vast/_confl/cf2_mbo (bought MBO history 2023-04-02..2026-11-13, 1,126 day files; NQ only; 11-01..11-05 2026 has no cf2 rows). The tables carry best bid/ask, aggressor volume buy/sell, cancel volume per side, top-2-level sizes and the largest single resting ORDER within 10 ticks per side; they do NOT carry a full top-5/top-10 level book. Therefore: **MedLevel = PROXY** (EWMA 0.001/s of the mean top-2-level size per side; live DS7 uses the top-5 mean), **[a] "level ahead >= k x MedLevel within 8 ticks" = largest resting ORDER within 10 ticks ahead >= k x MedLevel** (order, not aggregated level; 10 not 8 ticks), **[b]** aggressor delta against over 5/10/30 s >= k x MedLevel (live delta_mult definition, MedLevel proxy), **[c]** no new favourable mid extreme for 30/60/120 s (ties count, as live), **[d]** own-side cancel volume minus aggressor volume hitting that side (floored at 0), summed over 5 s, >= k x MedLevel (live pulled nets trades per price; here per second). Signals are evaluated at the end of each second while the trade is at +T0 or better (u >= T0 on the mid), exit on the next second.
- Cells (48): T0 in {+10, +15, +20} x {a 3x/5x; b windows 5/10/30 s x 5x/10x; c 30/60/120 s; d 5x/10x; any-2-of-4 loose (a3x, b 10 s 5x, c 60 s, d 5x) and strict (a5x, b 10 s 10x, c 120 s, d 10x)} plus a CONTROL cell per T0: fixed take at +T0 with no book condition (so the value of the book/tape condition is read against it).
- Metrics per cell: max DD of cumulative net over 43 months (equity ordered by alt exit time), worst week, HOLD-path DD (exits 2025-11-17..2025-12-10, equity from 0 inside the window), mean $/wk over the 187 calendar weeks of 2023-04-02..2026-10-31, L6M $/wk (2026-05-01..10-31), $/wk by year (2023 from April). Each book|group scored alone (not the whole stack: W-RP merges the whole-stack columns, $4.84 and x1.75 from the npz).
## 2. Summary: best book/tape cell vs the best fixed-take control (per BOOK)
| book | real maxDD / HOLD / mean wk | best control (fixed take) | best book/tape cell by DD | cell fired / n | beats control on DD at >= control mean? |
|---|---|---|---|---|---|
| A7 | 13724 / 2402 / 711 | T0=+20 z 0: DD 9489 HOLD 1311 $/wk 433 | T0=+20 any2_loose (('a', 3), ('b', (10, 5)), ('c', 60), ('d', 5)): DD 8951 HOLD 1216 $/wk 388 | 867/1156 | yes: T0=+20 d 10 DD 9384 $/wk 444 |
| H7 | 46603 / 8166 / 855 | T0=+10 z 0: DD 28960 HOLD 1181 $/wk 148 | T0=+15 b (30, 5): DD 21278 HOLD 1873 $/wk 286 | 763/1056 | yes: T0=+15 b (30, 5) DD 21278 $/wk 286 |
| K7 | 50155 / 37033 / 2201 | T0=+15 z 0: DD 38367 HOLD 18968 $/wk 23 | T0=+15 d 5: DD 40099 HOLD 18961 $/wk 4 | 5291/7302 | no |
| M7 | 64529 / 14056 / -20 | T0=+10 z 0: DD 82783 HOLD 6084 $/wk -394 | T0=+10 d 10: DD 80132 HOLD 6084 $/wk -378 | 3098/3970 | yes: T0=+10 d 10 DD 80132 $/wk -378 |
| O7 | 14950 / 731 / 473 | T0=+20 z 0: DD 8257 HOLD 0 $/wk 61 | T0=+20 b (10, 5): DD 7371 HOLD 0 $/wk 92 | 284/465 | yes: T0=+20 b (10, 5) DD 7371 $/wk 92 |
| P7 | 43061 / 15026 / 3174 | T0=+10 z 0: DD 84840 HOLD 12626 $/wk 187 | T0=+10 b (30, 10): DD 63941 HOLD 19071 $/wk 470 | 2558/3704 | yes: T0=+10 b (30, 10) DD 63941 $/wk 470 |
| U7 | 44879 / 23677 / 1413 | T0=+15 z 0: DD 61279 HOLD 11025 $/wk 68 | T0=+20 a 5: DD 29068 HOLD 18733 $/wk 801 | 853/1324 | yes: T0=+20 a 5 DD 29068 $/wk 801 |

## 3. Per book tables (REAL exits row first; DD-first = lowest max DD then HOLD DD; 'keeps >= 60% mean' = same ranking among cells with mean >= 60% of the real mean, or >= real if real <= 0; 'best alone' = best cell of each signal family)

#### A7 (n=1156 trades) - family i, per BOOK
| setting | max DD 43 mo | worst week | HOLD-path DD | mean $/wk | L6M $/wk | $/wk 2023 / 2024 / 2025 / 2026 | fired |
|---|---|---|---|---|---|---|---|
| REAL exits (no rule) | 13724 | -6207 | 2402 | 711 | 814 | 111 / 901 / 992 / 686 |  |
| DD-first: T0=+20 any-2-of-4 (loose) | 8951 | -3839 | 1216 | 388 | 363 | 136 / 483 / 428 / 454 | 867/1156 |
| DD-first: T0=+20 d pulled 5s>=10x | 9384 | -3944 | 1311 | 444 | 677 | 166 / 618 / 311 / 646 | 890/1156 |
| DD-first: T0=+20 d pulled 5s>=5x | 9456 | -3934 | 1311 | 438 | 677 | 189 / 599 / 307 / 626 | 892/1156 |
| keeps >=60% mean: T0=+20 d pulled 5s>=10x | 9384 | -3944 | 1311 | 444 | 677 | 166 / 618 / 311 / 646 | 890/1156 |
| keeps >=60% mean: T0=+20 d pulled 5s>=5x | 9456 | -3934 | 1311 | 438 | 677 | 189 / 599 / 307 / 626 | 892/1156 |
| keeps >=60% mean: T0=+20 CONTROL fixed take at +T0 (no book condition) | 9489 | -3934 | 1311 | 433 | 674 | 188 / 584 / 305 / 624 | 893/1156 |
| best alone (z): T0=+20 CONTROL fixed take at +T0 (no book condition) | 9489 | -3934 | 1311 | 433 | 674 | 188 / 584 / 305 / 624 | 893/1156 |
| best alone (a): T0=+10 a level>=5x Med ahead | 12667 | -5199 | 1930 | 233 | 347 | 299 / 176 / 198 / 287 | 884/1156 |
| best alone (b): T0=+20 b delta 10s>=5x | 10373 | -3834 | 2598 | 395 | 322 | 230 / 563 / 327 / 423 | 849/1156 |
| best alone (c): T0=+20 c no new extreme 60s | 10188 | -3679 | 1216 | 376 | 507 | 163 / 510 / 405 / 370 | 834/1156 |
| best alone (d): T0=+20 d pulled 5s>=10x | 9384 | -3944 | 1311 | 444 | 677 | 166 / 618 / 311 / 646 | 890/1156 |
| best alone (any2_loose): T0=+20 any-2-of-4 (loose) | 8951 | -3839 | 1216 | 388 | 363 | 136 / 483 / 428 / 454 | 867/1156 |
| best alone (any2_strict): T0=+20 any-2-of-4 (strict) | 9755 | -3739 | 1216 | 433 | 436 | 191 / 540 / 437 / 516 | 857/1156 |

#### H7 (n=1056 trades) - family i, per BOOK
| setting | max DD 43 mo | worst week | HOLD-path DD | mean $/wk | L6M $/wk | $/wk 2023 / 2024 / 2025 / 2026 | fired |
|---|---|---|---|---|---|---|---|
| REAL exits (no rule) | 46603 | -10787 | 8166 | 855 | 1795 | -13 / 1817 / 715 / 649 |  |
| DD-first: T0=+15 b delta 30s>=5x | 21278 | -7740 | 1873 | 286 | 688 | 321 / 569 / 88 / 154 | 763/1056 |
| DD-first: T0=+15 b delta 10s>=5x | 21600 | -7822 | 1878 | 314 | 994 | 313 / 554 / 39 / 355 | 771/1056 |
| DD-first: T0=+15 b delta 30s>=10x | 21679 | -7872 | 3242 | 332 | 560 | 431 / 654 / 128 / 99 | 739/1056 |
| keeps >=60% mean: T0=+20 a level>=5x Med ahead | 35319 | -8457 | 4418 | 567 | 1357 | 704 / 587 / 714 / 242 | 655/1056 |
| best alone (z): T0=+10 CONTROL fixed take at +T0 (no book condition) | 28960 | -7303 | 1181 | 148 | 585 | 410 / 330 / -177 / 81 | 870/1056 |
| best alone (a): T0=+10 a level>=3x Med ahead | 33186 | -7078 | 2513 | 384 | 1424 | 318 / 732 / 2 / 481 | 810/1056 |
| best alone (b): T0=+15 b delta 30s>=5x | 21278 | -7740 | 1873 | 286 | 688 | 321 / 569 / 88 / 154 | 763/1056 |
| best alone (c): T0=+10 c no new extreme 60s | 24199 | -7278 | 1181 | 294 | 1076 | 218 / 649 / -42 / 340 | 821/1056 |
| best alone (d): T0=+20 d pulled 5s>=10x | 29430 | -7892 | 1853 | 286 | 428 | 535 / 678 / 82 / -163 | 757/1056 |
| best alone (any2_loose): T0=+10 any-2-of-4 (loose) | 23281 | -7278 | 1181 | 203 | 869 | 224 / 437 / -65 / 223 | 846/1056 |
| best alone (any2_strict): T0=+15 any-2-of-4 (strict) | 24343 | -7163 | 1928 | 394 | 951 | 431 / 824 / 52 / 256 | 776/1056 |

#### K7 (n=7302 trades) - family i, per BOOK
| setting | max DD 43 mo | worst week | HOLD-path DD | mean $/wk | L6M $/wk | $/wk 2023 / 2024 / 2025 / 2026 | fired |
|---|---|---|---|---|---|---|---|
| REAL exits (no rule) | 50155 | -19363 | 37033 | 2201 | 4559 | 179 / 2092 / 1852 / 4574 |  |
| DD-first: T0=+15 CONTROL fixed take at +T0 (no book condition) | 38367 | -11938 | 18968 | 23 | 759 | -381 / 248 / -354 / 567 | 5298/7302 |
| DD-first: T0=+15 d pulled 5s>=5x | 40099 | -11931 | 18961 | 4 | 759 | -372 / 228 / -409 / 567 | 5291/7302 |
| DD-first: T0=+15 d pulled 5s>=10x | 40131 | -11921 | 18946 | 8 | 769 | -358 / 236 / -394 / 546 | 5288/7302 |
| (no cell keeps 60% of the real mean) | | | | | | | |
| best alone (z): T0=+15 CONTROL fixed take at +T0 (no book condition) | 38367 | -11938 | 18968 | 23 | 759 | -381 / 248 / -354 / 567 | 5298/7302 |
| best alone (a): T0=+15 a level>=3x Med ahead | 53629 | -13886 | 19394 | 509 | 2889 | 108 / 274 / -104 / 1892 | 4746/7302 |
| best alone (b): T0=+10 b delta 10s>=5x | 42941 | -10988 | 16528 | -1 | 733 | -162 / 231 / -357 / 292 | 5422/7302 |
| best alone (c): T0=+10 c no new extreme 30s | 41392 | -12808 | 20093 | 87 | 1199 | -90 / 116 / -333 / 716 | 5408/7302 |
| best alone (d): T0=+15 d pulled 5s>=5x | 40099 | -11931 | 18961 | 4 | 759 | -372 / 228 / -409 / 567 | 5291/7302 |
| best alone (any2_loose): T0=+10 any-2-of-4 (loose) | 47749 | -11598 | 14248 | -30 | 848 | -54 / -55 / -209 / 240 | 5591/7302 |
| best alone (any2_strict): T0=+15 any-2-of-4 (strict) | 43005 | -13363 | 21378 | 400 | 1882 | 153 / 457 / 29 / 999 | 5029/7302 |

#### M7 (n=3970 trades) - family i, per BOOK
| setting | max DD 43 mo | worst week | HOLD-path DD | mean $/wk | L6M $/wk | $/wk 2023 / 2024 / 2025 / 2026 | fired |
|---|---|---|---|---|---|---|---|
| REAL exits (no rule) | 64529 | -14224 | 14056 | -20 | -307 | 116 / 166 / -80 / -294 |  |
| DD-first: T0=+10 d pulled 5s>=10x | 80132 | -7170 | 6084 | -378 | -919 | -702 / -416 / -5 / -489 | 3098/3970 |
| DD-first: T0=+10 d pulled 5s>=5x | 82011 | -7170 | 6084 | -389 | -919 | -749 / -414 / -11 / -490 | 3099/3970 |
| DD-first: T0=+10 CONTROL fixed take at +T0 (no book condition) | 82783 | -7170 | 6084 | -394 | -919 | -757 / -416 / -18 / -490 | 3099/3970 |
| (no cell keeps 60% of the real mean) | | | | | | | |
| best alone (z): T0=+10 CONTROL fixed take at +T0 (no book condition) | 82783 | -7170 | 6084 | -394 | -919 | -757 / -416 / -18 / -490 | 3099/3970 |
| best alone (a): T0=+20 a level>=3x Med ahead | 107160 | -12731 | 10949 | -438 | -1001 | -566 / -711 / -114 / -384 | 2330/3970 |
| best alone (b): T0=+10 b delta 5s>=10x | 102914 | -11854 | 8575 | -466 | -1092 | -603 / -541 / 22 / -838 | 2698/3970 |
| best alone (c): T0=+10 c no new extreme 30s | 97969 | -9830 | 5012 | -432 | -817 | -716 / -342 / -129 / -647 | 2861/3970 |
| best alone (d): T0=+10 d pulled 5s>=10x | 80132 | -7170 | 6084 | -378 | -919 | -702 / -416 / -5 / -489 | 3098/3970 |
| best alone (any2_loose): T0=+10 any-2-of-4 (loose) | 107187 | -8477 | 6589 | -502 | -931 | -755 / -546 / -166 / -625 | 2978/3970 |
| best alone (any2_strict): T0=+10 any-2-of-4 (strict) | 111527 | -8214 | 5193 | -515 | -842 | -846 / -553 / -55 / -725 | 2903/3970 |

#### O7 (n=465 trades) - family i, per BOOK
| setting | max DD 43 mo | worst week | HOLD-path DD | mean $/wk | L6M $/wk | $/wk 2023 / 2024 / 2025 / 2026 | fired |
|---|---|---|---|---|---|---|---|
| REAL exits (no rule) | 14950 | -3906 | 731 | 473 | 394 | -126 / 751 / 593 / 532 |  |
| DD-first: T0=+20 b delta 10s>=5x | 7371 | -2737 | 0 | 92 | 137 | 44 / 83 / 153 / 74 | 284/465 |
| DD-first: T0=+20 b delta 10s>=10x | 7651 | -2767 | 0 | 98 | 118 | 67 / 93 / 137 / 86 | 281/465 |
| DD-first: T0=+20 a level>=5x Med ahead | 7774 | -2677 | 0 | 171 | 249 | 160 / 106 / 214 / 209 | 264/465 |
| (no cell keeps 60% of the real mean) | | | | | | | |
| best alone (z): T0=+20 CONTROL fixed take at +T0 (no book condition) | 8257 | -2762 | 0 | 61 | 12 | 6 / 75 / 148 / -10 | 300/465 |
| best alone (a): T0=+20 a level>=5x Med ahead | 7774 | -2677 | 0 | 171 | 249 | 160 / 106 / 214 / 209 | 264/465 |
| best alone (b): T0=+20 b delta 10s>=5x | 7371 | -2737 | 0 | 92 | 137 | 44 / 83 / 153 / 74 | 284/465 |
| best alone (c): T0=+20 c no new extreme 120s | 7885 | -2712 | 0 | 172 | 226 | 9 / 213 / 262 / 161 | 225/465 |
| best alone (d): T0=+20 d pulled 5s>=10x | 8245 | -2762 | 0 | 61 | 12 | 6 / 76 / 148 / -10 | 300/465 |
| best alone (any2_loose): T0=+20 any-2-of-4 (loose) | 9103 | -2752 | 0 | 70 | 159 | 36 / 63 / 87 / 86 | 288/465 |
| best alone (any2_strict): T0=+20 any-2-of-4 (strict) | 8629 | -2677 | 0 | 94 | 161 | 55 / 81 / 137 / 93 | 286/465 |

#### P7 (n=3704 trades) - family i, per BOOK
| setting | max DD 43 mo | worst week | HOLD-path DD | mean $/wk | L6M $/wk | $/wk 2023 / 2024 / 2025 / 2026 | fired |
|---|---|---|---|---|---|---|---|
| REAL exits (no rule) | 43061 | -25348 | 15026 | 3174 | 12015 | 1346 / 564 / 2421 / 8867 |  |
| DD-first: T0=+10 b delta 30s>=10x | 63941 | -11518 | 19071 | 470 | 3812 | 209 / -481 / 228 / 2140 | 2558/3704 |
| DD-first: T0=+20 b delta 10s>=10x | 72793 | -17907 | 18834 | 973 | 6226 | 271 / -741 / 1003 / 3636 | 2117/3704 |
| DD-first: T0=+10 b delta 10s>=10x | 76748 | -12244 | 17135 | 544 | 4501 | -107 / -587 / 392 / 2676 | 2503/3704 |
| (no cell keeps 60% of the real mean) | | | | | | | |
| best alone (z): T0=+10 CONTROL fixed take at +T0 (no book condition) | 84840 | -9539 | 12626 | 187 | 2559 | 5 / -864 / 292 / 1490 | 2857/3704 |
| best alone (a): T0=+20 a level>=5x Med ahead | 79456 | -18075 | 17135 | 889 | 5260 | 439 / -474 / 470 / 3440 | 1987/3704 |
| best alone (b): T0=+10 b delta 30s>=10x | 63941 | -11518 | 19071 | 470 | 3812 | 209 / -481 / 228 / 2140 | 2558/3704 |
| best alone (c): T0=+20 c no new extreme 30s | 85047 | -14902 | 17334 | 691 | 5015 | 528 / -802 / 500 / 2865 | 2269/3704 |
| best alone (d): T0=+10 d pulled 5s>=5x | 87715 | -9539 | 12626 | 135 | 2497 | -136 / -917 / 297 / 1453 | 2852/3704 |
| best alone (any2_loose): T0=+10 any-2-of-4 (loose) | 81468 | -11074 | 17774 | 242 | 2695 | -11 / -988 / 399 / 1764 | 2754/3704 |
| best alone (any2_strict): T0=+20 any-2-of-4 (strict) | 92163 | -14329 | 17340 | 777 | 5579 | 582 / -939 / 535 / 3307 | 2265/3704 |

#### U7 (n=1324 trades) - family i, per BOOK
| setting | max DD 43 mo | worst week | HOLD-path DD | mean $/wk | L6M $/wk | $/wk 2023 / 2024 / 2025 / 2026 | fired |
|---|---|---|---|---|---|---|---|
| REAL exits (no rule) | 44879 | -16772 | 23677 | 1413 | 2911 | 1227 / 972 / 1049 / 2549 |  |
| DD-first: T0=+20 a level>=5x Med ahead | 29068 | -12626 | 18733 | 801 | 1398 | 788 / 435 / 812 / 1239 | 853/1324 |
| DD-first: T0=+15 a level>=5x Med ahead | 30581 | -14724 | 16805 | 500 | 514 | 633 / 291 / 665 / 435 | 908/1324 |
| DD-first: T0=+20 b delta 10s>=10x | 30590 | -12716 | 13065 | 635 | 865 | 116 / 571 / 929 / 829 | 891/1324 |
| (no cell keeps 60% of the real mean) | | | | | | | |
| best alone (z): T0=+15 CONTROL fixed take at +T0 (no book condition) | 61279 | -11974 | 11025 | 68 | 372 | 286 / -239 / -76 / 412 | 1027/1324 |
| best alone (a): T0=+20 a level>=5x Med ahead | 29068 | -12626 | 18733 | 801 | 1398 | 788 / 435 / 812 / 1239 | 853/1324 |
| best alone (b): T0=+20 b delta 10s>=10x | 30590 | -12716 | 13065 | 635 | 865 | 116 / 571 / 929 / 829 | 891/1324 |
| best alone (c): T0=+20 c no new extreme 120s | 46993 | -10611 | 17756 | 587 | 1453 | 605 / -51 / 622 / 1297 | 867/1324 |
| best alone (d): T0=+20 d pulled 5s>=10x | 60883 | -12445 | 15153 | 431 | 531 | 767 / -51 / 473 / 657 | 979/1324 |
| best alone (any2_loose): T0=+20 any-2-of-4 (loose) | 50733 | -11895 | 13750 | 445 | 244 | 576 / 17 / 676 / 566 | 957/1324 |
| best alone (any2_strict): T0=+20 any-2-of-4 (strict) | 40089 | -11930 | 13418 | 478 | 265 | 506 / 192 / 824 / 382 | 941/1324 |

#### per BOOK x SESSION, top 2 by DD and top 1 keeping >=60% of the real mean (groups with >= 30 trades)
| group | n | real maxDD / HOLD / mean wk | DD-first #1 | DD-first #2 | keeps>=60% mean |
|---|---|---|---|---|---|
| A7|asia | 1156 | 13724 / 2402 / 711 | T0=+20 any-2-of-4 (loose): DD 8951 HOLD 1216 $/wk 388 | T0=+20 d pulled 5s>=10x: DD 9384 HOLD 1311 $/wk 444 | T0=+20 d pulled 5s>=10x: DD 9384 HOLD 1311 $/wk 444 |
| H7|asia | 698 | 41186 / 5869 / 770 | T0=+10 b delta 30s>=5x: DD 21669 HOLD 1089 $/wk 299 | T0=+15 b delta 10s>=10x: DD 22022 HOLD 3242 $/wk 494 | T0=+15 b delta 10s>=10x: DD 22022 HOLD 3242 $/wk 494 |
| H7|nyam | 358 | 23783 / 2377 / 86 | T0=+10 a level>=3x Med ahead: DD 10261 HOLD 1181 $/wk -13 | T0=+10 a level>=5x Med ahead: DD 10366 HOLD 1181 $/wk 35 | none |
| K7|asia | 2607 | 26763 / 14902 / 1254 | T0=+10 any-2-of-4 (loose): DD 18456 HOLD 3845 $/wk 69 | T0=+10 c no new extreme 30s: DD 18741 HOLD 5267 $/wk 51 | none |
| K7|london | 1820 | 27995 / 14320 / 443 | T0=+20 a level>=5x Med ahead: DD 21203 HOLD 12207 $/wk 115 | T0=+20 d pulled 5s>=10x: DD 21912 HOLD 12090 $/wk 82 | none |
| K7|nyam | 1634 | 41592 / 11196 / 48 | T0=+20 b delta 30s>=5x: DD 23802 HOLD 9208 $/wk 81 | T0=+20 b delta 30s>=10x: DD 23892 HOLD 9183 $/wk 98 | T0=+20 b delta 30s>=5x: DD 23802 HOLD 9208 $/wk 81 |
| K7|nypm | 1241 | 36048 / 7550 / 457 | T0=+10 b delta 10s>=10x: DD 17486 HOLD 4756 $/wk 170 | T0=+10 any-2-of-4 (strict): DD 18286 HOLD 4806 $/wk 152 | T0=+15 a level>=3x Med ahead: DD 18698 HOLD 4314 $/wk 291 |
| M7|london | 2420 | 111123 / 8800 / -357 | T0=+10 d pulled 5s>=10x: DD 61826 HOLD 5489 $/wk -282 | T0=+10 d pulled 5s>=5x: DD 63498 HOLD 5489 $/wk -293 | T0=+10 d pulled 5s>=10x: DD 61826 HOLD 5489 $/wk -282 |
| M7|nyam | 1550 | 21316 / 7815 / 337 | T0=+20 c no new extreme 30s: DD 20848 HOLD 3189 $/wk 102 | T0=+10 CONTROL fixed take at +T0 (no book condition): DD 22131 HOLD 1874 $/wk -96 | none |
| O7|nyam | 465 | 14950 / 731 / 473 | T0=+20 b delta 10s>=5x: DD 7371 HOLD 0 $/wk 92 | T0=+20 b delta 10s>=10x: DD 7651 HOLD 0 $/wk 98 | none |
| P7|asia | 1969 | 63819 / 12461 / 2964 | T0=+20 any-2-of-4 (strict): DD 34261 HOLD 17715 $/wk 1100 | T0=+10 b delta 10s>=10x: DD 35496 HOLD 17251 $/wk 856 | none |
| P7|london | 1494 | 86599 / 6834 / 117 | T0=+15 a level>=3x Med ahead: DD 51803 HOLD 4798 $/wk -111 | T0=+15 d pulled 5s>=10x: DD 55125 HOLD 4920 $/wk -181 | none |
| P7|nyam | 241 | 21407 / 2530 / 93 | T0=+10 d pulled 5s>=10x: DD 15314 HOLD 672 $/wk -59 | T0=+10 CONTROL fixed take at +T0 (no book condition): DD 15341 HOLD 672 $/wk -59 | none |
| U7|asia | 686 | 30643 / 9389 / 1146 | T0=+10 b delta 5s>=10x: DD 20150 HOLD 4890 $/wk 209 | T0=+10 b delta 10s>=5x: DD 20810 HOLD 5600 $/wk 167 | T0=+20 a level>=5x Med ahead: DD 26927 HOLD 11699 $/wk 737 |
| U7|london | 638 | 32127 / 16706 / 267 | T0=+15 a level>=5x Med ahead: DD 29297 HOLD 12348 $/wk 68 | T0=+10 a level>=3x Med ahead: DD 37764 HOLD 9329 $/wk -96 | none |
## 4. Live profit-side state lines on the clean replica (blind in live until 11-16)
Lines as in DS3_TRAIL_L2.md FINAL / DS7 v1.7 grammar (assumed to be the lines in the live v2.9 file; the log only prints U7 `lock 0 pct>=0.80`, K7/A7 `take` lines, so the three lines below are the T-TRAIL-L2 candidates named in the order): K7 `profit K7 * pct>=0.3 delta_mult>=5 lock 0 win=10 persist=10`; M7 `profit M7 * pct>=0.3 tot_rel>=2 step 10 win=0 persist=2 wall_ticks=8`; U7 `profit U7 * pct>=0.4 delta_mult>=20 tighten 30 win=15 persist=5`. pct = unreal / target distance (59-60 pts); persist = consecutive seconds; lock = protective level at entry; step = level one full 10-pt step behind the favourable extreme (k = floor(fav/10) - 1, ratchets up only); tighten = trail 30 pts behind the favourable mid extreme, latched and ratcheting; the protective level exits on the first second the mid touches it, at level - 0.8 pt. Window: trades from 2026-10-19 to 11-13: the live CSV rows 2026-11-06..11-13 (11-01..11-05 have no cf2 rows, 98 live trades skipped) and the JL2 engine trades 10-19..10-31 (the live CSV has no rows before 11-01). **Proxy warning: delta_mult uses the top-2 MedLevel proxy; M7's tot_rel (8-tick depth both sides / slot-normal) is replaced by top-2-level total / its ~1 h EWMA, a weak stand-in: treat the M7 row as indicative only.** Alt P&L = (alt exit pts - real exit pts) x qty x $20; "saved" = trades where the line exits better than the real exit.
| line | source window | trades covered | line fired | exits by the line | saved (n, $) | cost (n, $) | net $ vs real exits |
|---|---|---|---|---|---|---|---|
| K7 lock 0 (delta_mult>=5, w10, p10) | live 11-06..11-13 | 87 | 51 | 25 | 12, +$15,328 | 13, -$23,084 | **-$7,756** |
| K7 lock 0 | engine 10-19..10-31 | 115 | 71 | 36 | 28, +$24,411 | 8, -$12,160 | +$12,251 |
| K7 lock 0 | total | 202 | 122 | 61 | | | **+$4,494** |
| M7 step 10 (tot_rel PROXY >= 2, p2) | live 11-06..11-13 | 55 | 13 | 9 | 2, +$6,346 | 7, -$6,575 | -$229 |
| M7 step 10 | engine 10-19..10-31 | 40 | 11 | 10 | 6, +$7,004 | 4, -$2,664 | +$4,340 |
| M7 step 10 | total | 95 | 24 | 19 | | | **+$4,110** |
| U7 tighten 30 (delta_mult>=20, w15, p5) | live 11-06..11-13 | 12 | 5 | 4 | 3, +$10,108 | 1, -$3,794 | +$6,314 |
| U7 tighten 30 | engine 10-19..10-31 | 12 | 6 | 4 | 3, +$8,816 | 1, -$4,054 | +$4,762 |
| U7 tighten 30 | total | 24 | 11 | 8 | | | **+$11,076** |
Per-trade rows (fire second, level, exit, real vs alt points, $): /mnt/l2/l2vast/_replay/profit_lines_last4w.csv. Reading: K7's lock at entry is a coin flip that costs the Target winners (-$1,196 each for 1 lot) and saves the losers it catches: net -$7.8k on the live week and +$12.3k on the engine fortnight (the 4-week total is +$4.5k, tiny against the K7 four-week gross); U7's trail is the only line with a consistent sign (+$11.1k on 8 exits, 24 trades, so n is small); M7 is indicative only (proxy). None of the three is a stand-alone lead at this sample size.
## 5. Open items / what would change the verdict
- The family-i conditions need the live-definition inputs (top-5 MedLevel, aggregated level sizes within 8 ticks, trades netted per price) that the per-second cf2 tables do not hold; a rebuild from the MBO files (th_lcb2 MBO reconstructor, ~45 s per 8 h) for a month, with the exact port definitions, would test whether selective conditions exist; I did not do it inside the 1-hour window.
- Arm-time exits are +10..+20 takes in disguise: the useful comparison for Step 2 is each book's best cell against the fixed-target rows (a-g) of DS3_TARGET_REPLAY.md at the same mean, not against the real exits.
