# BARE D7 YARDSTICK (W-BARE; order 1803Z; Josh: "if you judge anything it should be D7 bare books current to D8 bare books")

Written 2026-11-20 19:44Z UTC. Data end: month 202610 (all-new base, 42 months 2023-04..2026-10 minus 202511). Dollars are BASE lots (1 lot per trade, as every all-new book), net of $4.84 per lot round trip. Live lots = max(1, floor(1.75 x base + 0.5)). Windows: L6M = 202605-202610, L3M = 202608-202610, each prior year (2023 is Apr-Dec). Cells read: ulcer / max DD / worst week / mean $ per week.

## How the bare D7 books were built (plain words)
- **Trigger stream:** a passive hook (code/th_bare/bare_cap.py) sits on top of the JL3 engine (the live D7 as run) and writes down EVERY raw trigger call of every live book, before any layer sees it. The JL3 run with this hook is trade for trade the JL3 run (202610: 691 trades, 37,159.82 net, identical). Putting the captured triggers back into the live books with ALL layers ON reproduces 689 of 691 JL3 trades of 202610 and every book total to the cent except K7 and M7 (2 trades each differ by injection timing): so the captured events are the live books' own raw triggers.
- **Bare set:** exactly as the new D8 books: events file (signal time + 2 s, side, stop, target, 1 lot, flat at the session end), the live books switched off everywhere, account layers ON at the same stand-in settings as every all-new base (DAY-DONE, caps, ER sizer, stack rules, same-side-loser skip), one mf_multi stream per book with the same own day cap 12,000 / 4,800 base dollars the new books carry. A book alone = its stream only; the session stack = all the session's live books together (one 1-lot stream each).
- **Bracket:** the book's own plain bracket from the DS7 defaults: stop 60 pts / target 60 pts (R = 1.0) for K7, M7, U7, P7, H7, A7; O7 stop 40 / target 90 (its X40_90). Session-end flat (Asia 02:00, London 08:30, NY AM 12:00 ET) as every new book; O7 also shown with its own 16:00 time exit. No per-session bracket exists in the live panel (K7/H7 bracket-by-session fields are blank).
- **Stripped:** L2-gated entry, P7 three-bar confirm hold, signal-state rules (K7/P7/H7), slot halving, B02 gate, NTZ half size, ATR-skip, post-exit blackout, own caps of the live books, trade-health cuts, locks, takes, the 09:00-10:00 NY and 18:00-18:05 time blocks, governor/WL_E1, stack cut. **Stays in (it is the trigger):** H7 = HMA 20/55 cross on close-VWAP with EMA200 filter and slow-slope confirm; O7 = opening drive, only 09:40-09:44, once a day; P7 and A7 = pullback engines that carry their own regime state (Supertrend 5-min regime / depth-ATR); K7 = Keltner break EMA14 / ATR10 x 1.0 on 3-min; U7 = Supertrend ATR7 x 3.0 on 10-min; M7 = momentum vote 4 of 5.
- **Not like live:** lots are 1 per book (live lots differ per book/session; the equal-risk line removes that), and the book can re-enter whenever flat; live NY open block 09:30-10:00 is NOT applied (it is a no-trade-window layer).


## Asia: bare D7 vs bare D8, last 6 months (1 lot, base dollars)

| row | bar | trigger | bracket | L6M $/wk | L6M ulcer | L6M max DD | L6M worst wk | L3M $/wk | L6M $/wk at the bare D7 stack ulcer (13133) |
|---|---|---|---|---|---|---|---|---|---|
| BARE D7 STACK (A7 + H7 + K7 + P7 + U7) `TL3_ALN_AS_STKLIVE_BARE` | - | all of the above together | 60/60 (O7 40/90) | 5654 | 13133 | -32277 | -21126 | 3191 | 5654 |
| bare D7 A7 `TL3_ALN_AS_LIVEA7_BARE` | 1-min time bar | PB7 pullback, depth ATR 0.5, window 15 (Asia pullback) | 60/60 | 39 | 7244 | -17518 | -5318 | -761 | 71 |
| bare D7 H7 `TL3_ALN_AS_LIVEH7_BARE` | 1-min bars, 5-min HMA 20/55 on close-VWAP | HMA cross + EMA200 filter + slow-slope confirm | 60/60 | 594 | 3123 | -8333 | -5984 | 272 | 2497 |
| bare D7 K7 `TL3_ALN_AS_LIVEK7_BARE` | 3-min time bar | Keltner break EMA14, ATR10 x 1.0 | 60/60 | 1390 | 13683 | -33669 | -11741 | 297 | 1334 |
| bare D7 P7 `TL3_ALN_AS_LIVEP7_BARE` | 1-min bars / Supertrend 5-min regime | PB3B pullback inside the Supertrend regime | 60/60 | 1538 | 5238 | -12844 | -11775 | 2203 | 3857 |
| bare D7 U7 `TL3_ALN_AS_LIVEU7_BARE` | 10-min time bar | Supertrend ATR7 x 3.0 flip | 60/60 | 620 | 2325 | -6392 | -2599 | 468 | 3501 |
| D8 L15f14deb `TL3_ALN_AS_L15f14deb_BASE` | tm120 | trig_momentum_mvote v4of5 {"scale": 0.25, "thr": 0.25} | plain60/60 | 1482 | 3329 | -9477 | -6922 | 1208 | 5848 |
| D8 L1756b913 `TL3_ALN_AS_L1756b913_BASE` | tm240 | trig_structure_libpattern threebar {"filt": 20} | plain60/60 | 2107 | 4678 | -12916 | -5830 | 3272 | 5915 |
| D8 L1edb9fab `TL3_ALN_AS_L1edb9fab_BASE` | tm300 | trig_pullback_ema depth {"len": 10, "w": 0.5} | plain60/60 | 2167 | 4509 | -11823 | -7409 | 2289 | 6311 |
| D8 L3faac8df `TL3_ALN_AS_L3faac8df_BASE` | mrenko_20 | trig_levels_trendline break_native {"n": 2, "k": 0.0} | plain60/60 | 1314 | 4512 | -10962 | -6156 | 1186 | 3823 |
| D8 L578701ed `TL3_ALN_AS_L578701ed_BASE` | time_m_1 | trig_book_dwm dev_follow {"L": 200, "z": 2.0} | plain60/60 | 2207 | 5315 | -13108 | -6603 | 614 | 5454 |
| D8 L5dee2059 `TL3_ALN_AS_L5dee2059_BASE` | time_m_2 | trig_momentum_rsi mom {"len": 21, "lvl": 60} | asym10u/20u | 1142 | 7196 | -18906 | -7002 | 1986 | 2084 |
| D8 L7c368a4f `TL3_ALN_AS_L7c368a4f_BASE` | time_m_5 | trig_pullback_ema depth {"len": 10, "w": 0.5} | plain60/60 | 2456 | 4075 | -11123 | -7409 | 2434 | 7916 |
| D8 L7f41b347 `TL3_ALN_AS_L7f41b347_BASE` | tm60 | trig_levels_fib15 break {"n": 2, "k": 0.25} | plain60/60 | 2095 | 4173 | -12464 | -8251 | 1738 | 6592 |
| D8 L973b5c8a `TL3_ALN_AS_L973b5c8a_BASE` | tm420 | trig_momentum_stoch zone_break_native {"len": 21, "lvl": 80} | plain60/60 | 1211 | 3886 | -12660 | -5576 | 1310 | 4091 |
| D8 L9aa7805c `TL3_ALN_AS_L9aa7805c_BASE` | time_m_5 | trig_live_seven K7 {"live": 1} | plain60/60 | 1691 | 3604 | -8595 | -6065 | 1635 | 6162 |
| D8 Lb68a132d `TL3_ALN_AS_Lb68a132d_BASE` | tm600 | trig_bands_vwap walk_native {"clk": 6, "k": 1.0, "N": 2} | plain60/60 | 1090 | 3158 | -8621 | -3718 | 1273 | 4531 |
| D8 Lcbc8a7ec `TL3_ALN_AS_Lcbc8a7ec_BASE` | tm60 | trig_levels_fib15 break_native {"n": 2, "k": 0.25} | plain60/60 | 1880 | 4828 | -11760 | -6066 | 2105 | 5113 |
| D8 Lec335094 `TL3_ALN_AS_Lec335094_BASE` | tm780 | trig_levels_vwap break_native {"n": 1, "k": 0.25} | plain60/60 | 934 | 3740 | -9426 | -3137 | 1005 | 3279 |
| D8 Lff52ec0c `TL3_ALN_AS_Lff52ec0c_BASE` | time_m_1 | trig_levels_fib15 break {"n": 2, "k": 0.25} | plain60/60 | 1882 | 3866 | -12103 | -7121 | 1357 | 6392 |
| D8 M7423c0d9 `TL3_ALN_AS_M7423c0d9_BASE` | time_m_3 | trig_structure_inside inside {"k": 1, "filt": 20} | sym8u | 1055 | 3251 | -9723 | -3649 | 860 | 4260 |
| D8 stack: dead three-book Asia stack (Ldcdb0b6e + L578701ed + Lfb608c7b), for the record `TL3_ALN_AS_STKe7f8ab00` | - | - | - | 7256 | 4497 | -14918 | -8652 | 6397 | 21194 |
| D8 stack: current Asia pool pick L7c368a4f alone (own-checks step 1) `TL3_ALN_AS_L7c368a4f_BASE` | - | - | - | 2456 | 4075 | -11123 | -7409 | 2434 | 7916 |
| D8 stack: Asia pool book Ldcdb0b6e alone (staying-power / earlier pick) `TL3_ALN_AS_Ldcdb0b6e_BASE` | - | - | - | 2256 | 3706 | -11884 | -6537 | 1470 | 7993 |

## Asia: bare D7 books and bare D7 stack, all windows

| bare D7 set | L6M | L3M | 2023 | 2024 | 2025 | persistence (pos. 14-day blocks) | luck controls beaten L6M (L3M) of 30, ulcer-only |
|---|---|---|---|---|---|---|---|
| STACK (A7 + H7 + K7 + P7 + U7) `TL3_ALN_AS_STKLIVE_BARE` | 13133 / -32277 / -21126 / 5654 | 12212 / -27920 / -17823 / 3191 | 20445 / -33434 / -8171 / -160 | 9302 / -25668 / -8091 / 1386 | 19498 / -38603 / -14679 / 1273 | 0.63 | 22 (10), ulcer-only 29 |
| A7 `TL3_ALN_AS_LIVEA7_BARE` | 7244 / -17518 / -5318 / 39 | 4155 / -11860 / -5318 / -761 | 2915 / -6413 / -3059 / 65 | 2359 / -7218 / -4729 / 558 | 4966 / -12254 / -4174 / 421 | 0.62 | 17 (9), ulcer-only 21 |
| H7 `TL3_ALN_AS_LIVEH7_BARE` | 3123 / -8333 / -5984 / 594 | 2774 / -6317 / -2524 / 272 | 2008 / -4436 / -1549 / 127 | 1789 / -5778 / -1954 / 330 | 5628 / -13047 / -2824 / -100 | 0.54 | 3 (10), ulcer-only 27 |
| K7 `TL3_ALN_AS_LIVEK7_BARE` | 13683 / -33669 / -11741 / 1390 | 14575 / -27693 / -11741 / 297 | 2921 / -6163 / -2569 / 170 | 6334 / -16534 / -4674 / -37 | 10071 / -23472 / -8967 / 14 | 0.54 | 8 (1), ulcer-only 21 |
| P7 `TL3_ALN_AS_LIVEP7_BARE` | 5238 / -12844 / -11775 / 1538 | 3296 / -11750 / -7906 / 2203 | 9659 / -15320 / -4424 / -302 | 4886 / -12557 / -4003 / 446 | 3492 / -8260 / -5318 / 939 | 0.58 | 11 (5), ulcer-only 27 |
| U7 `TL3_ALN_AS_LIVEU7_BARE` | 2325 / -6392 / -2599 / 620 | 2088 / -6392 / -2599 / 468 | 4290 / -7462 / -1615 / -22 | 1619 / -4307 / -1904 / 135 | 3842 / -8347 / -4689 / 250 | 0.58 | 27 (13), ulcer-only 30 |

Equal-risk comparison (bare D7 session STACK scaled by one factor k so its L6M ulcer equals the D8 row; the same k in every window; "worse %" = how much WORSE the D8 row is than the scaled bare D7 stack on ulcer / max DD / worst week and how much LOWER on mean; GREEN <= 15%, AMBER 15-30%, RED > 30%; negative = D8 better):

| D8 comparator | k | window | D8: ulcer / maxDD / worst wk / mean | bare D7 stack scaled: ulcer / maxDD / worst wk / mean | D8 worse % (ulcer, maxDD, worst wk, mean) | colour |
|---|---|---|---|---|---|---|
| dead three-book Asia stack (Ldcdb0b6e + L578701ed + Lfb608c7b), for the record `TL3_ALN_AS_STKe7f8ab00` | 0.34 | L6M | 4497 / -14918 / -8652 / 7256 | 4497 / -11051 / -7233 / 1936 | 0% / 35% / 20% / -275% | RED |
|  `` | 0.34 | L3M | 5966 / -14918 / -8652 / 6397 | 4181 / -9559 / -6102 / 1092 | 43% / 56% / 42% / -486% | RED |
|  `` | 0.34 | Y2023 | 2776 / -6042 / -2733 / 1277 | 7000 / -11447 / -2797 / -55 | -60% / -47% / -2% / -2436% | GREEN |
|  `` | 0.34 | Y2024 | 9040 / -27272 / -10101 / 944 | 3185 / -8788 / -2770 / 475 | 184% / 210% / 265% / -99% | RED |
|  `` | 0.34 | Y2025 | 11554 / -25320 / -17451 / 1072 | 6676 / -13217 / -5026 / 436 | 73% / 92% / 247% / -146% | RED |
| | | persistence of D8 vs scaled bare D7 stack (share of 14-day blocks where D8 >= it) | 0.66 | | | |
| current Asia pool pick L7c368a4f alone (own-checks step 1) `TL3_ALN_AS_L7c368a4f_BASE` | 0.31 | L6M | 4075 / -11123 / -7409 / 2456 | 4075 / -10016 / -6556 / 1754 | 0% / 11% / 13% / -40% | GREEN |
|  `` | 0.31 | L3M | 2028 / -5118 / -3617 / 2434 | 3790 / -8664 / -5531 / 990 | -46% / -41% / -35% / -146% | GREEN |
|  `` | 0.31 | Y2023 | 4013 / -9990 / -2484 / 203 | 6344 / -10375 / -2535 / -50 | -37% / -4% / -2% / -510% | GREEN |
|  `` | 0.31 | Y2024 | 4626 / -11465 / -2843 / 654 | 2886 / -7965 / -2511 / 430 | 60% / 44% / 13% / -52% | RED |
|  `` | 0.31 | Y2025 | 5940 / -14312 / -10102 / 528 | 6050 / -11979 / -4555 / 395 | -2% / 19% / 122% / -34% | RED |
| | | persistence of D8 vs scaled bare D7 stack (share of 14-day blocks where D8 >= it) | 0.53 | | | |
| Asia pool book Ldcdb0b6e alone (staying-power / earlier pick) `TL3_ALN_AS_Ldcdb0b6e_BASE` | 0.28 | L6M | 3706 / -11884 / -6537 / 2256 | 3706 / -9109 / -5962 / 1596 | 0% / 30% / 10% / -41% | RED |
|  `` | 0.28 | L3M | 4466 / -11441 / -6537 / 1470 | 3446 / -7879 / -5030 / 900 | 30% / 45% / 30% / -63% | RED |
|  `` | 0.28 | Y2023 | 2764 / -6300 / -3724 / 380 | 5770 / -9435 / -2306 / -45 | -52% / -33% / 61% / -944% | RED |
|  `` | 0.28 | Y2024 | 4487 / -12697 / -3638 / 628 | 2625 / -7244 / -2283 / 391 | 71% / 75% / 59% / -61% | RED |
|  `` | 0.28 | Y2025 | 10407 / -21690 / -7067 / 391 | 5502 / -10894 / -4143 / 359 | 89% / 99% / 71% / -9% | RED |
| | | persistence of D8 vs scaled bare D7 stack (share of 14-day blocks where D8 >= it) | 0.52 | | | |

## NY AM: bare D7 vs bare D8, last 6 months (1 lot, base dollars)

| row | bar | trigger | bracket | L6M $/wk | L6M ulcer | L6M max DD | L6M worst wk | L3M $/wk | L6M $/wk at the bare D7 stack ulcer (33655) |
|---|---|---|---|---|---|---|---|---|---|
| BARE D7 STACK (H7 + K7 + M7 + O7 + P7) `TL3_ALN_NY_STKLIVE_BARE` | - | all of the above together | 60/60 (O7 40/90) | -599 | 33655 | -60055 | -25697 | -1039 | -599 |
| bare D7 H7 `TL3_ALN_NY_LIVEH7_BARE` | 1-min bars, 5-min HMA 20/55 on close-VWAP | HMA cross + EMA200 filter + slow-slope confirm | 60/60 | 861 | 1933 | -4589 | -2375 | 947 | 14986 |
| bare D7 K7 `TL3_ALN_NY_LIVEK7_BARE` | 3-min time bar | Keltner break EMA14, ATR10 x 1.0 | 60/60 | -1226 | 22882 | -37464 | -12981 | -1093 | -1804 |
| bare D7 M7 `TL3_ALN_NY_LIVEM7_BARE` | 1-min time bar | momentum vote 4 of 5, threshold 0.5 | 60/60 | -12 | 9547 | -23316 | -8197 | -298 | -43 |
| bare D7 O7 `TL3_ALN_NY_LIVEO7_BARE` | 1-min time bar | opening drive 10-min, pullback 1, 09:40-09:44, once a day | 40/90 | 343 | 4077 | -9098 | -3044 | 241 | 2828 |
| bare D7 P7 `TL3_ALN_NY_LIVEP7_BARE` | 1-min bars / Supertrend 5-min regime | PB3B pullback inside the Supertrend regime | 60/60 | -564 | 16967 | -32680 | -14571 | -836 | -1118 |
| bare D7 O7, own 16:00 exit `TL3_ALN_NY_LIVEO7_BARE16` | 1-min time bar | opening drive 10-min, pullback 1, 09:40-09:44, once a day | 40/90 | 330 | 4077 | -9098 | -3044 | 241 | 2721 |
| D8 B6f77f23d `TL3_ALN_NY_B6f77f23d_BASE` | tm45 | trig_levels_opens false_break_native {"M": 3, "k": 0.5} | asym15u/30u | 1393 | 5356 | -12737 | -6864 | 1214 | 8754 |
| D8 L05350e98 `TL3_ALN_NY_L05350e98_BASE` | tm420 | trig_levels_session_hl retest_native {"M": 3, "tol": 0.0} | sym15u | 952 | 3540 | -9608 | -6124 | 1043 | 9053 |
| D8 L488784d8 `TL3_ALN_NY_L488784d8_BASE` | swing_atr_0.25 | trig_momentum_roc break_native {"len": 20, "wd": 1.0} | plain60/60 | 961 | 2839 | -7243 | -3569 | 538 | 11392 |
| D8 L6547965c `TL3_ALN_NY_L6547965c_BASE` | swing_pct_8 | trig_tape_unfinished unf_fade {"m": 6, "cp": 0.0} | plain60/60 | 1275 | 3045 | -8124 | -4533 | 588 | 14094 |
| D8 L7cc56d99 `TL3_ALN_NY_L7cc56d99_BASE` | lbrk_3_40 | trig_levels_vwap break {"n": 2, "k": 0.25} | sym15u | 2405 | 4790 | -13326 | -7749 | 2166 | 16900 |
| D8 stack: NY AM Stack A (L7cc56d99 + L488784d8) on BASE `TL3_ALN_NY_STK30810e22` | - | - | - | 3366 | 4313 | -12245 | -7742 | 2704 | 26267 |
| D8 stack: NY AM Stack A on the D8 _CANC streams `TL3_ALN_NY_STKCANC_A` | - | - | - | 3326 | 4323 | -12245 | -7742 | 3004 | 25892 |

## NY AM: bare D7 books and bare D7 stack, all windows

| bare D7 set | L6M | L3M | 2023 | 2024 | 2025 | persistence (pos. 14-day blocks) | luck controls beaten L6M (L3M) of 30, ulcer-only |
|---|---|---|---|---|---|---|---|
| STACK (H7 + K7 + M7 + O7 + P7) `TL3_ALN_NY_STKLIVE_BARE` | 33655 / -60055 / -25697 / -599 | 24692 / -44363 / -17385 / -1039 | 18603 / -43707 / -16286 / 2077 | 16905 / -36886 / -17347 / 2238 | 24263 / -71352 / -22902 / 995 | 0.58 | 7 (5), ulcer-only 12 |
| H7 `TL3_ALN_NY_LIVEH7_BARE` | 1933 / -4589 / -2375 / 861 | 1158 / -2400 / -2375 / 947 | 3872 / -11171 / -3164 / 114 | 15564 / -24817 / -4729 / -437 | 6055 / -16355 / -5524 / 309 | 0.58 | 26 (16), ulcer-only 29 |
| K7 `TL3_ALN_NY_LIVEK7_BARE` | 22882 / -37464 / -12981 / -1226 | 9655 / -18748 / -10487 / -1093 | 7328 / -16513 / -7084 / 325 | 4101 / -10525 / -5842 / 1164 | 10208 / -24209 / -7003 / 122 | 0.57 | 0 (2), ulcer-only 4 |
| M7 `TL3_ALN_NY_LIVEM7_BARE` | 9547 / -23316 / -8197 / -12 | 11924 / -23316 / -7957 / -298 | 8320 / -19023 / -6943 / 153 | 9662 / -18077 / -11361 / 370 | 12837 / -29322 / -7204 / 324 | 0.51 | 14 (3), ulcer-only 17 |
| O7 `TL3_ALN_NY_LIVEO7_BARE` | 4077 / -9098 / -3044 / 343 | 2519 / -6889 / -2350 / 241 | 8906 / -15144 / -3974 / -190 | 1591 / -4749 / -2444 / 826 | 3352 / -7793 / -3134 / 498 | 0.70 | 5 (7), ulcer-only 15 |
| P7 `TL3_ALN_NY_LIVEP7_BARE` | 16967 / -32680 / -14571 / -564 | 16127 / -28350 / -5871 / -836 | 2462 / -8212 / -4874 / 1675 | 8725 / -15893 / -7672 / 314 | 20202 / -40919 / -14466 / -259 | 0.57 | 0 (1), ulcer-only 11 |
| O7 with its own 16:00 time exit (variant) `TL3_ALN_NY_LIVEO7_BARE16` | 4077 / -9098 / -3044 / 330 | 2519 / -6889 / -2350 / 241 | 8860 / -16004 / -3974 / -143 | 1695 / -5494 / -3189 / 827 | 3442 / -7793 / -3134 / 486 | 0.70 | controls not queued |

Equal-risk comparison (bare D7 session STACK scaled by one factor k so its L6M ulcer equals the D8 row; the same k in every window; "worse %" = how much WORSE the D8 row is than the scaled bare D7 stack on ulcer / max DD / worst week and how much LOWER on mean; GREEN <= 15%, AMBER 15-30%, RED > 30%; negative = D8 better):

| D8 comparator | k | window | D8: ulcer / maxDD / worst wk / mean | bare D7 stack scaled: ulcer / maxDD / worst wk / mean | D8 worse % (ulcer, maxDD, worst wk, mean) | colour |
|---|---|---|---|---|---|---|
| NY AM Stack A (L7cc56d99 + L488784d8) on BASE `TL3_ALN_NY_STK30810e22` | 0.13 | L6M | 4313 / -12245 / -7742 / 3366 | 4313 / -7696 / -3293 / -77 | -0% / 59% / 135% / -4487% | RED |
|  `` | 0.13 | L3M | 3616 / -10088 / -7377 / 2704 | 3164 / -5685 / -2228 / -133 | 14% / 77% / 231% / -2132% | RED |
|  `` | 0.13 | Y2023 | 5576 / -14827 / -6948 / 1463 | 2384 / -5601 / -2087 / 266 | 134% / 165% / 233% / -449% | RED |
|  `` | 0.13 | Y2024 | 9984 / -20581 / -8704 / 672 | 2166 / -4727 / -2223 / 287 | 361% / 335% / 292% / -134% | RED |
|  `` | 0.13 | Y2025 | 9176 / -26571 / -14752 / 1580 | 3109 / -9144 / -2935 / 127 | 195% / 191% / 403% / -1139% | RED |
| | | persistence of D8 vs scaled bare D7 stack (share of 14-day blocks where D8 >= it) | 0.65 | | | |
| NY AM Stack A on the D8 _CANC streams `TL3_ALN_NY_STKCANC_A` | 0.13 | L6M | 4323 / -12245 / -7742 / 3326 | 4323 / -7715 / -3301 / -77 | 0% / 59% / 135% / -4424% | RED |
|  `` | 0.13 | L3M | 3611 / -10068 / -7357 / 3004 | 3172 / -5699 / -2233 / -133 | 14% / 77% / 229% / -2351% | RED |
|  `` | 0.13 | Y2023 | 5425 / -15589 / -6278 / 1527 | 2390 / -5615 / -2092 / 267 | 127% / 178% / 200% / -472% | RED |
|  `` | 0.13 | Y2024 | 8706 / -18758 / -8704 / 645 | 2172 / -4739 / -2228 / 287 | 301% / 296% / 291% / -124% | RED |
|  `` | 0.13 | Y2025 | 9531 / -26301 / -14742 / 1496 | 3117 / -9166 / -2942 / 128 | 206% / 187% / 401% / -1071% | RED |
| | | persistence of D8 vs scaled bare D7 stack (share of 14-day blocks where D8 >= it) | 0.68 | | | |

## London: bare D7 vs bare D8, last 6 months (1 lot, base dollars)

| row | bar | trigger | bracket | L6M $/wk | L6M ulcer | L6M max DD | L6M worst wk | L3M $/wk | L6M $/wk at the bare D7 stack ulcer (26504) |
|---|---|---|---|---|---|---|---|---|---|
| BARE D7 STACK (K7 + M7 + P7 + U7) `TL3_ALN_LO_STKLIVE_BARE` | - | all of the above together | 60/60 (O7 40/90) | 198 | 26504 | -54522 | -24897 | 1307 | 198 |
| bare D7 K7 `TL3_ALN_LO_LIVEK7_BARE` | 3-min time bar | Keltner break EMA14, ATR10 x 1.0 | 60/60 | -755 | 20713 | -35038 | -8066 | 295 | -966 |
| bare D7 M7 `TL3_ALN_LO_LIVEM7_BARE` | 1-min time bar | momentum vote 4 of 5, threshold 0.5 | 60/60 | -22 | 11092 | -21670 | -14487 | 196 | -52 |
| bare D7 P7 `TL3_ALN_LO_LIVEP7_BARE` | 1-min bars / Supertrend 5-min regime | PB3B pullback inside the Supertrend regime | 60/60 | 1236 | 5562 | -12725 | -5633 | 1216 | 5887 |
| bare D7 U7 `TL3_ALN_LO_LIVEU7_BARE` | 10-min time bar | Supertrend ATR7 x 3.0 flip | 60/60 | -258 | 4471 | -14821 | -6254 | -400 | -1532 |

## London: bare D7 books and bare D7 stack, all windows

| bare D7 set | L6M | L3M | 2023 | 2024 | 2025 | persistence (pos. 14-day blocks) | luck controls beaten L6M (L3M) of 30, ulcer-only |
|---|---|---|---|---|---|---|---|
| STACK (K7 + M7 + P7 + U7) `TL3_ALN_LO_STKLIVE_BARE` | 26504 / -54522 / -24897 / 198 | 18796 / -38763 / -24897 / 1307 | 17142 / -40399 / -10934 / 363 | 75837 / -134401 / -30762 / -1972 | 28391 / -59694 / -18100 / -369 | 0.46 | 9 (4), ulcer-only 18 |
| K7 `TL3_ALN_LO_LIVEK7_BARE` | 20713 / -35038 / -8066 / -755 | 6727 / -14050 / -5057 / 295 | 4717 / -11389 / -3069 / 169 | 15743 / -31072 / -7393 / -159 | 8133 / -16461 / -5979 / 109 | 0.46 | 10 (12), ulcer-only 10 |
| M7 `TL3_ALN_LO_LIVEM7_BARE` | 11092 / -21670 / -14487 / -22 | 9166 / -19088 / -14487 / 196 | 5629 / -13346 / -4328 / 388 | 35430 / -57948 / -9893 / -956 | 12346 / -29878 / -6541 / -173 | 0.44 | 0 (0), ulcer-only 18 |
| P7 `TL3_ALN_LO_LIVEP7_BARE` | 5562 / -12725 / -5633 / 1236 | 3661 / -9609 / -5633 / 1216 | 5833 / -12805 / -4723 / 231 | 28569 / -48872 / -11458 / -743 | 16570 / -26209 / -8412 / -216 | 0.44 | 21 (18), ulcer-only 23 |
| U7 `TL3_ALN_LO_LIVEU7_BARE` | 4471 / -14821 / -6254 / -258 | 5324 / -14821 / -4754 / -400 | 11999 / -17584 / -4654 / -424 | 9441 / -18880 / -3919 / -113 | 7346 / -14047 / -5389 / -135 | 0.44 | 6 (2), ulcer-only 17 |

Equal-risk comparison (bare D7 session STACK scaled by one factor k so its L6M ulcer equals the D8 row; the same k in every window; "worse %" = how much WORSE the D8 row is than the scaled bare D7 stack on ulcer / max DD / worst week and how much LOWER on mean; GREEN <= 15%, AMBER 15-30%, RED > 30%; negative = D8 better):


