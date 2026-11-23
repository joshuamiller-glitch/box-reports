# ASIA BOOK STYLES (W-STYLES, order 0105Z Nov 23; information only, results already on disk, no engine runs, no queue rows, no gate or rule change)

Josh (quoted, 22 Nov): "can you do an overview of all the asia books - like what kind of sets they are? trend following - pullback...reversal..etc" and "ok do an info request". Written 2026-11-23 UTC from: W-BRKT's step-2b state (`_brkt/step2b_state.json`, the 54 D_pass books + 8 twins), the first-look cell lists (`_brkt/firstlook_cells_asia*.json`), the truly bare R0BR sets on the exact engine (L6M = 2026-05..10, 131 trading days; 1 lot), and the truly bare 5-book stack set `TL3_SR_AS_STKd8106b26ef_BF1_BASE` (1 lot, R0).

## Plain answer (counts first)

- Of the 54 Asia books that pass (a)-(d) truly bare at their own bracket: **52 are continuation types** (30 breakout, 21 momentum / trend-follow, 1 flow-follow) and **2 are pullback-with-trend** (a level retest and a fib-pullback). **0 are reversal / fade / false-break / counter-trend.** The 8 twins (same trade list as a passer) are listed below with their own trigger labels.
- The five pinned books (Lb0e6dfa3 narrow-range breakout, L385f4f2e.J502 RSI momentum + confluence, L92a90948 efficiency-ratio trend, L6b373671 pivot-level break, L578701ed depth-pressure follow) are all continuation types, as the relay said.
- The search DID produce counter-trend candidates, and the gates removed them: see section 4. 269 counter-trend books reached step 2 (13% of the 2,076 that did), 173 of them were positive in both L6M and L3M at some shape, and none passed: 126 failed the prior-year check, 33 were stopped by the luck controls (lost more than 3 of 30), 14 are twins. Continuation books went through the same gates and 52 passed.
- The two pullback-with-trend passers are NOT diversifiers of the stack: they correlate 0.24-0.31 daily and lose money on the stack's 20 worst days (section 3).

## 1. STYLE TABLE of the complete Asia pass pool (54 books + 8 twins)

How labels were assigned: from the trigger DEFINITION in the engine's trigger library (`code/th_grid`), not from the result. Bands: `break*` = close crosses outside the band (breakout), `walk*` = N consecutive closes outside the band (momentum-trend), `fade*` = close re-enters after an outside close (reversal-fade). Levels (`lv_base.py`): `break` = n closes beyond the level (breakout), `retest` = break then a test of the level in the break's direction (pullback with trend), `reject` = touch-and-reject at a level (reversal-fade), `false_break` = fade of a failed break, fib `pullback` = retracement-level touch in the trend direction. Momentum modules: `mom` / `zone_break` / `break` / `mvote` / `trend` = the indicator crosses in the direction of the move (momentum-trend); `revert` / `cross_zone` = cross back from oversold/overbought (reversal-fade). `manual_cci go` = CCI breaks through +/-lvl (breakout; `rev` is the fade). `structure_libpattern nr` = narrow-range bar then close beyond the prior range (breakout). `structure_breakout brk` = N-bar close breakout. `trend_libstack ema_stack` = flip into an EMA-stack trend state (momentum-trend). `book_dwm dev_follow` = follow the depth-weighted mid deviation (flow-follow; name + Josh's description). All 54 passers' labels were checked against the code or its docstring; the flow-follow label rests on the variant name.

| book | bar | trigger.variant | STYLE | bracket | L6M / L3M $/wk | ulcer | max DD | worst wk | 2023 / 24 / 25 $/wk | persist. | controls beaten | trades / night |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L5483cb3c | urenko_56 | levels_profile_nodes.break | breakout | P45 | 2849 / 2536 | 2248 | -7644 | -4602 | 132 / 418 / 113 | 0.69 | 27 of 30 | 4.61 |
| Lb0e6dfa3 (pinned) | tm240 | structure_libpattern.nr | breakout | F40_80 | 2969 / 1930 | 2643 | -8614 | -4590 | 386 / 506 / 690 | 0.66 | 29 of 30 | 4.39 |
| L548972b6 | vsess_30 | momentum_roc.break_native | momentum-trend | F40_80 | 2337 / 1602 | 2081 | -5429 | -4326 | 219 / 575 / 603 | 0.66 | 29 of 30 | 3.96 |
| Ld60fb3e3 | time_m_4 | structure_libpattern.nr | breakout | F40_80 | 2736 / 1563 | 2599 | -8589 | -4695 | 373 / 523 / 848 | 0.65 | 28 of 30 | 4.40 |
| L7ea48296 | cdr_100 | momentum_mvote.v4of5 | momentum-trend | P45 | 2410 / 2368 | 2336 | -7540 | -4421 | 360 / 556 / 582 | 0.61 | 30 of 30 | 5.98 |
| L4cdac967 | vol_1700 | structure_breakout.brk | breakout | P45 | 2259 / 1089 | 2525 | -9053 | -3277 | 218 / 465 / 94 | 0.59 | 29 of 30 | 3.75 |
| L578701ed (pinned) | time_m_1 | book_dwm.dev_follow | flow-follow | F30_90 | 2910 / 2774 | 3358 | -9315 | -5428 | 527 / 705 / 83 | 0.61 | 27 of 30 | 6.60 |
| L6b373671 (pinned) | frenko_40 | levels_piv_floor.break_native | breakout | P60 | 2220 / 2255 | 2591 | -8707 | -4283 | 75 / 226 / 554 | 0.62 | 30 of 30 | 3.40 |
| Lac4916e6 | tm180 | bands_vwap.walk_native | momentum-trend | F40_80 | 1809 / 1327 | 2181 | -5657 | -3258 | 268 / 540 / 103 | 0.63 | 30 of 30 | 2.71 |
| L9c2622b0 | pnf_7 | levels_vwap.break | breakout | P45 | 1845 / 1523 | 2369 | -7156 | -3421 | 301 / 442 / 424 | 0.61 | 30 of 30 | 5.73 |
| L64313ba5 | tm420 | momentum_stoch.zone_break_native | momentum-trend | P30 | 1606 / 673 | 2403 | -7124 | -2977 | 155 / 388 / 21 | 0.58 | 30 of 30 | 5.34 |
| L5026acdc | time_m_4 | bands_bollinger.walk | momentum-trend | F30_90 | 1999 / 448 | 3068 | -8308 | -4842 | 29 / 271 / 215 | 0.59 | 27 of 30 | 3.34 |
| L9e3c5607 | vol_1100 | bands_bollinger.break | breakout | P45 | 1278 / 1476 | 2021 | -6158 | -4271 | 167 / 320 / 302 | 0.61 | 30 of 30 | 3.96 |
| L98c7ae1d | time_m_3 | bands_vwap.walk_native | momentum-trend | F40_80 | 1627 / 975 | 2665 | -7590 | -4083 | 263 / 495 / 246 | 0.63 | 27 of 30 | 2.76 |
| L2b152d25 | pasl_28 | levels_fib15.break | breakout | P30 | 1286 / 1609 | 2113 | -6948 | -4062 | 98 / 426 / 163 | 0.61 | 27 of 30 | 5.02 |
| Le207b901 | pnf_14 | levels_piv_floor.retest_native | pullback with trend | F30_90 | 1604 / 1339 | 2645 | -8307 | -3325 | 123 / 341 / 135 | 0.65 | 27 of 30 | 3.34 |
| M3e087b15 | tm900 | bands_donchian.break | breakout | F30_90 | 901 / 709 | 1551 | -4773 | -2949 | 2 / 179 / 94 | 0.59 | 27 of 30 | 1.40 |
| L1f5315f5 | time_m_3 | momentum_rsi.mom | momentum-trend | F40_80 | 2496 / 2854 | 4353 | -12492 | -6500 | 296 / 407 / 677 | 0.69 | 29 of 30 | 4.79 |
| L1343f8bd | frenko_28 | levels_trendline.break | breakout | P45 | 1682 / 1989 | 3064 | -9251 | -3213 | 115 / 619 / 582 | 0.62 | 30 of 30 | 4.88 |
| L81e3d0ff | tm2700 | levels_fib15.break_native | breakout | P45 | 1269 / 1609 | 2443 | -7733 | -3243 | 176 / 133 / 332 | 0.61 | 29 of 30 | 3.43 |
| La34ff0e1 | vsess_30 | bands_envelope.break_ema | breakout | F40_80 | 1550 / 1119 | 3072 | -8768 | -2771 | 112 / 278 / 811 | 0.62 | 28 of 30 | 3.19 |
| L552f6547 | pnf_5 | bands_atrchan.break_ext | breakout | F30_90 | 1603 / 929 | 3196 | -8539 | -4272 | 136 / 400 / 178 | 0.65 | 30 of 30 | 6.24 |
| L2fbba524 | vol_750 | momentum_stoch.zone_break | momentum-trend | P30 | 1788 / 1208 | 3660 | -9019 | -4759 | 140 / 363 / 37 | 0.59 | 27 of 30 | 8.06 |
| L1525fc29 | pnf_5 | bands_atrchan.break_ema | breakout | P45 | 1878 / 2636 | 4226 | -11925 | -9048 | 371 / 372 / 171 | 0.61 | 27 of 30 | 8.57 |
| Lb328c0d1 | time_m_2 | manual_cci.go | breakout | P45 | 1632 / 2303 | 3922 | -9331 | -5259 | 259 / 636 / 24 | 0.65 | 30 of 30 | 5.85 |
| Lb3f85ddc | time_m_2 | levels_fib15.break | breakout | F40_80 | 1467 / 2257 | 3568 | -10035 | -6555 | 176 / 262 / 190 | 0.59 | 27 of 30 | 5.33 |
| Lbfca747b | renko_40 | structure_libpattern.nr | breakout | P45 | 1606 / 689 | 3992 | -11287 | -5049 | 105 / 437 / 307 | 0.61 | 29 of 30 | 8.75 |
| L4aaacdb2 | vsess_30 | bands_vwap.break | breakout | P30 | 531 / 374 | 1348 | -3431 | -1839 | 205 / 70 / 147 | 0.62 | 27 of 30 | 1.56 |
| L459016c0 | time_m_7 | momentum_roc.break_native | momentum-trend | P30 | 951 / 609 | 2478 | -7009 | -3002 | 60 / 189 / 23 | 0.62 | 29 of 30 | 4.02 |
| L79fb26c4 | frenko_28 | levels_trendline.break_native | breakout | P45 | 1463 / 1199 | 3994 | -11961 | -4109 | 53 / 729 / 525 | 0.6 | 28 of 30 | 4.93 |
| L7669e599 | cdr_100 | trend_libstack.ema_stack | momentum-trend | P45 | 1104 / 1342 | 3075 | -8330 | -3898 | 319 / 79 / 372 | 0.66 | 27 of 30 | 3.07 |
| L82f920bb | time_m_3 | momentum_mvote.v4of5 | momentum-trend | P30 | 1161 / 855 | 3271 | -8534 | -4877 | 191 / 457 / 132 | 0.58 | 29 of 30 | 8.82 |
| L36f1a14e | dol_6000 | levels_fib5.pullback_native | pullback with trend | F30_90 | 927 / 98 | 2620 | -6636 | -3393 | 166 / 234 / 121 | 0.67 | 28 of 30 | 1.76 |
| Lcd4aa7cd | time_m_7 | momentum_er.trend_z_native | momentum-trend | P30 | 932 / 570 | 2867 | -7494 | -3002 | 60 / 200 / 29 | 0.62 | 29 of 30 | 4.01 |
| L294c4530 | vol_1100 | bands_bollinger.break_native | breakout | P45 | 994 / 1350 | 3094 | -7067 | -4776 | 307 / 179 / 290 | 0.58 | 29 of 30 | 3.66 |
| L9f09df59 | tm120 | bands_vwap.walk | momentum-trend | F60_120 | 1239 / 531 | 3931 | -10494 | -5688 | 321 / 504 / 475 | 0.62 | 28 of 30 | 2.65 |
| Lc11f2bcc | vsess_600 | levels_fib15.break | breakout | F30_90 | 1639 / 697 | 5285 | -12277 | -6600 | 247 / 266 / 244 | 0.59 | 27 of 30 | 6.92 |
| L2aa4f77d | time_m_4 | structure_breakout.brk_native | breakout | P45 | 1095 / 434 | 3710 | -10833 | -4676 | 236 / 449 / 89 | 0.66 | 29 of 30 | 6.27 |
| Ld3a03a68 | vol_500 | momentum_rsi.mom | momentum-trend | F30_90 | 1249 / 1248 | 4305 | -9799 | -5119 | 70 / 640 / 483 | 0.61 | 27 of 30 | 4.49 |
| La37b0d38 | cusum_80 | momentum_willr.break | momentum-trend | P45 | 776 / 365 | 2693 | -7535 | -3201 | 204 / 193 / 847 | 0.67 | 28 of 30 | 3.48 |
| M3c4f3969 | time_m_2 | bands_envelope.break_sma_native | breakout | P30 | 491 / 278 | 1845 | -3970 | -2033 | 114 / 251 / 242 | 0.58 | 29 of 30 | 2.02 |
| M345e7019 | tm120 | bands_envelope.break_sma_native | breakout | P30 | 495 / 369 | 2003 | -5090 | -2213 | 99 / 240 / 236 | 0.58 | 29 of 30 | 2.02 |
| Led34741b | time_m_3 | manual_cci.go | breakout | F80_40 | 1043 / 1163 | 4252 | -10973 | -6541 | 339 / 136 / 187 | 0.61 | 28 of 30 | 3.95 |
| Lb4e7a24a | dchg_10 | bands_vwap.walk_native | momentum-trend | A20U10U | 1677 / 234 | 7293 | -16703 | -6314 | 171 / 262 / 416 | 0.63 | 27 of 30 | 2.15 |
| Mac4916e6 | tm180 | bands_vwap.walk_native | momentum-trend | F40_80 | 579 / 378 | 2585 | -6730 | -3074 | 14 / 580 / 253 | 0.68 | 29 of 30 | 1.37 |
| L32bc5db3 | mom_28 | levels_fib15.break_native | breakout | P60 | 999 / 288 | 4795 | -12077 | -3892 | 257 / 320 / 1001 | 0.61 | 30 of 30 | 5.14 |
| L6f51709c | tm420 | momentum_er.trend | momentum-trend | P45 | 622 / 464 | 3005 | -7436 | -2618 | 184 / 246 / 193 | 0.65 | 28 of 30 | 2.23 |
| Ld8421129 | vol_500 | bands_bollinger.break_native | breakout | P30 | 647 / 793 | 3679 | -9510 | -3410 | 101 / 270 / 10 | 0.61 | 28 of 30 | 5.46 |
| La4dd3ce9 | drb_400 | bands_keltner.walk | momentum-trend | P45 | 737 / 738 | 4854 | -11722 | -4509 | 199 / 342 / 344 | 0.63 | 27 of 30 | 4.40 |
| M98c7ae1d | time_m_3 | bands_vwap.walk_native | momentum-trend | F40_80 | 450 / 147 | 3038 | -7365 | -3889 | 48 / 581 / 340 | 0.69 | 27 of 30 | 1.38 |
| L5c493ea5 | dib_400 | momentum_mvote.v3of5_native | momentum-trend | P60 | 866 / 1513 | 6043 | -15030 | -5289 | 380 / 383 / 382 | 0.61 | 28 of 30 | 5.46 |
| L12656380 | vol_750 | bands_bollinger.break_native | breakout | P45 | 433 / 156 | 4522 | -11908 | -4496 | 95 / 312 / 47 | 0.6 | 28 of 30 | 3.90 |
| L7c8c909c | vrb_700 | levels_fib15.break_native | breakout | P45 | 471 / 97 | 5271 | -14415 | -6521 | 139 / 487 / 475 | 0.66 | 27 of 30 | 6.68 |
| M254b4124 | time_m_2 | manual_cci.go | breakout | F80_40 | 272 / 260 | 7886 | -19171 | -7646 | 39 / 398 / 125 | 0.61 | 27 of 30 | 3.51 |

Note: the pinned L385f4f2e entry here is the plain L385f4f2e (the stack member is its J502 filtered version, TL3_ALN_AS_L385f4f2e_P2JCX502; see PINNED STACK). Trades / night = trades in the 131 L6M trading days of the 1-lot R0 set, divided by 131.

### Twins (same trade list as the passer they inherit from)

| twin | inherits from | its own trigger.variant | its STYLE |
|---|---|---|---|
| Lf0a487b9 | L5483cb3c | levels_profile_nodes.break_native | breakout |
| L8d866ea1 | L64313ba5 | momentum_stoch.zone_break | momentum-trend |
| L76cff489 | L1f5315f5 | momentum_rsi.mom_native | momentum-trend |
| Lf3d1eadb | Lb3f85ddc | levels_fib15.break_native | breakout |
| Laeacb62e | L459016c0 | momentum_roc.break | momentum-trend |
| L9e2ad3ae | L82f920bb | momentum_mvote.v4of5_native | momentum-trend |
| Le0c30cdb | Lcd4aa7cd | momentum_er.trend_z | momentum-trend |
| L81e25737 | L6f51709c | momentum_er.trend_native | momentum-trend |

(Item 2 of the order, the per-book statistics, is the same table: columns L6M / L3M $/wk, ulcer, max DD, worst week, prior years, persistence, controls, trades per night.)

## 3. Is anything NOT a continuation type, and does it help the pinned stack?

Stack reference: the truly bare R0 5-book stack TL3_ALN_AS_STKd8106b26ef at 1 lot, L6M $10834/wk. Its 20 worst days in L6M sum to $-84648; its 5 worst weeks sum to $-6504. Daily / weekly correlation = Pearson over the 131 L6M trading days / the L6M weeks, book alone at its own bracket (1 lot, R0) vs the stack. Baseline: the median daily correlation of the 54 pass books with the stack is 0.36 (range 0.02 to 0.61; five of the 54 are members of the stack itself).

### 3a. The two non-continuation PASSERS (both pullback-with-trend)

| book | trigger.variant (bar, bracket) | corr daily / weekly | book P&L on the stack's 20 worst days (negative on k of 20) | on the stack's 5 worst weeks (positive in k of 5) | L6M $/wk alone |
|---|---|---|---|---|---|
| Le207b901 | levels_piv_floor.retest_native (pnf_14, F30_90) | 0.31 / 0.38 | $-11394 (12 of 20 negative) | $1984 (2 of 5 positive) | $1604 |
| L36f1a14e | levels_fib5.pullback_native (dol_6000, F30_90) | 0.24 / 0.31 | $-3536 (11 of 20 negative) | $-294 (3 of 5 positive) | $927 |

Both lose on the stack's 20 worst days (Le207b901 $-11.4k, 12 of 20 days negative; L36f1a14e $-3.5k, 11 of 20) and are roughly flat to slightly positive on the 5 worst weeks (Le207b901 +$2.0k; L36f1a14e -$0.3k). They do not make money when the stack loses.

### 3b. Counter-trend candidates that FAILED the gates (information only: the 10 best by L6M $/wk per unit of ulcer among those positive in L6M and L3M)

Shown at their best tested step-2 shape; in-sample; all failed (b)/(c) or (d). Same correlation and worst-day / worst-week columns.

| book | trigger.variant (bar) | STYLE | L6M / L3M $/wk | ulcer | persist. | failed at | corr daily / weekly | P&L on stack 20 worst days (neg. days) | on 5 worst weeks (pos. weeks) |
|---|---|---|---|---|---|---|---|---|---|
| Le001fe42 | levels_trendline.reject_native (mrenko_20) | reversal-fade | 2487 / 2950 | 1979 | 0.66 | prior-year check (stage B) | 0.12 / 0.42 | $8250 (6 of 20) | $-1584 (3 of 5) |
| L1acc170a | levels_vwap.false_break (kagi_20) | false-break (fade of a break) | 2113 / 1439 | 2279 | 0.6 | prior-year check (stage B) | 0.26 / 0.35 | $-3135 (11 of 20) | $2938 (3 of 5) |
| L45c6baf5 | levels_vwap.false_break (dchg_20) | false-break (fade of a break) | 2113 / 1439 | 2279 | 0.6 | prior-year check (stage B) | 0.26 / 0.35 | $-3135 (11 of 20) | $2938 (3 of 5) |
| L302f2cbb | levels_fib60.reject_native (time_m_60) | reversal-fade | 1971 / 1515 | 2215 | 0.59 | prior-year check (stage B) | 0.25 / 0.12 | $-7913 (9 of 20) | $10220 (4 of 5) |
| L051dcad5 | levels_piv_wf.false_break_native (pnf_14) | false-break (fade of a break) | 1832 / 1502 | 2128 | 0.57 | prior-year check (stage B) | 0.16 / 0.20 | $7811 (8 of 20) | $8635 (2 of 5) |
| Le3823c3e | levels_gaps.false_break_native (vsess_450) | false-break (fade of a break) | 1570 / 856 | 2135 | 0.46 | prior-year check (stage B) | 0.20 / 0.33 | $2476 (10 of 20) | $6680 (3 of 5) |
| Le3a8a418 | levels_fib5.reject_native (time_m_60) | reversal-fade | 1674 / 1693 | 2416 | 0.57 | prior-year check (stage B) | 0.28 / 0.32 | $-8251 (10 of 20) | $-3609 (2 of 5) |
| L1716c153 | book_micro.fade (time_m_13) | flow-fade | 1875 / 1622 | 2952 | 0.56 | prior-year check (stage B) | 0.23 / 0.37 | $7836 (9 of 20) | $2644 (2 of 5) |
| L6ab791e1 | levels_profile_va.reject_native (mrenko_10) | reversal-fade | 1726 / 764 | 2771 | 0.54 | prior-year check (stage B) | 0.26 / 0.40 | $8227 (5 of 20) | $62 (1 of 5) |
| Lce256a20 | xmarket_es.revert (dchg_14) | cross-market fade | 2721 / 1527 | 4408 | 0.58 | luck controls (lost 8 of 30 at the stop) | 0.57 / 0.69 | $-22800 (13 of 20) | $-4572 (1 of 5) |

(L1acc170a and L45c6baf5 have identical numbers: same trade list, twins.) Reading: the correlations are low to moderate (0.12-0.57), but the sign on the stack's worst days is mixed: five of these ten make money on the stack's 20 worst days (Le001fe42 +$8.3k, L051dcad5 +$7.8k, Le3823c3e +$2.5k, L1716c153 +$7.8k, L6ab791e1 +$8.2k) and the other five lose (the twin pair -$3.1k, L302f2cbb -$7.9k, Le3a8a418 -$8.3k, Lce256a20 -$22.8k); on the 5 worst weeks the sign is mixed too. None passed the gates, so none is a verified diversifier.

## 4. Counts by style: the pass pool and the search funnel

Funnel definitions (W-BRKT step 2, exact engine, 1 lot, truly bare): a book reaches step 2 if it came out of the earlier ladder (first-look cells: 3,058 Asia cells, of which 2,076 distinct books were run at the 17-shape step 2); A_fail = L6M or L3M $/wk <= 0 at that shape; C_fail = failed the prior-year check (prior years not negative, persistence >= 0.58); D_stop = lost more than 3 of 30 luck controls; D_pass = passed. Twins inherit their representative's verdict. "Positive in both windows" = some tested shape of the book has L6M and L3M $/wk both > 0 (any shape; the pass uses the best one).

| style class | first-look cells | books at step 2 | positive in L6M and L3M at some shape | of those: failed prior years (C_fail) | failed luck controls (D_stop) | twins | PASSED (D_pass) |
|---|---|---|---|---|---|---|---|
| continuation (breakout, momentum/trend, flow-follow, cross-market follow) | 2303 | 1559 | 1058 | 616 | 291 | 99 | 52 |
| pullback with trend (retest, fib/EMA pullback) | 311 | 211 | 145 | 102 | 34 | 7 | 2 |
| counter-trend (reversal-fade, false-break, flow-fade, cross-market fade) | 389 | 269 | 173 | 126 | 33 | 14 | 0 |
| unclassified (oscillator families etc.) | 55 | 37 | 24 | 14 | 10 | 0 | 0 |

Note: the first-look cell total here (3,058) counts the two cell lists (asia + asia6) before de-duplication of overlapping ids; 2,497 distinct ids, 2,076 of them ran at step 2 (the rest were not run: skipped or paused).

Step-2 books by exact style label: breakout 844, momentum-trend 506, pullback with trend 211, flow-follow 162, reversal-fade 130, false-break (fade of a break) 78, flow-fade 50, unclassified 37, cross-market follow 34, live D7 book clone 13, cross-market fade 11.

The 54 passers by style label: breakout 30, momentum-trend 21, pullback with trend 2, flow-follow 1.

What it says (facts only): counter-trend books were 12.7% of the first-look cells and 13.0% of the books at step 2 (269 of 2,076), and their rate of being positive in both windows was 64% (173 of 269) against 68% for continuation books (1,058 of 1,559): the earlier stages did not remove them. At the luck-control stage counter-trend books were stopped 33 times and passed 0; continuation books were stopped 291 times and passed 52 (15% of those that got that far). If counter-trend books passed that stage at the continuation rate, about 5 of the 33 would have passed; the chance of 0 is about 0.5% (0.85^33), if the 33 were independent, which twins and shared triggers make only roughly true. Pullback-with-trend books: 211 at step 2, 145 positive in both windows, 2 passed (+7 twins); 34 were stopped by the luck controls.

## 5. Non-continuation books tried as an add to the pinned stack

- The stack-search pool (W-COMBO's loops, original and recent basis) is built from the books that pass (a)-(d), so it contains the 52 continuation passers and the 2 pullback passers and NO counter-trend book: none passed, so none could be tried as an add on any basis.
- The two pullback passers: L36f1a14e is in the loops' pool of 80 books (the page header lists it) and Le207b901 is in the layer-fit pool of 80 (layer-watch lines); the loops evaluated every pool book at every step, but neither appears in any page line as a chosen add, a blocked swap, or a top-5 second book. No page records a stack set with either of them landed against the pinned 5 or against J502 alone.
- The add rules that rejected the candidates that WERE listed (all continuation types): e.g. the recent-basis equal-weight loop stops at L385f4f2e.J502 alone because every second book fails one clause, return per unit of ulcer at least 1.01 times the stack before; its top five seconds (return per ulcer): L5483cb3c.BRP45 2.46 (levels_profile_nodes break, breakout), L6b373671.BRP60 2.14 (pivot break), L9e3c5607.BRP45 2.02, Lb0e6dfa3.BRF40_80 1.97 (narrow-range breakout), Ld60fb3e3.BRF40_80 1.94 (narrow-range breakout): all continuation types (details: ASIA_ONE_BOOK_EXPLAIN.md, MORNING 17:05Z). The 5-book pinned stack came from the 05:03Z weighted run on a 47-book pool, with the same add rule.
- So the stack searches never saw a counter-trend candidate: the gates removed them upstream of the pool (section 4). No recommendation; what, if anything, to test next is Josh's call.

## Caveats

- Style labels for the unclassified 55 first-look cells (oscillator families libosc: vortex, uo, cmo, stochrsi, fisher, trix, aroon; tape_libvol; confluence; structure_fvg cont; levels_sdx_renko28 lim_mid) are not assigned; none of them is among the 54 passers.
- Candlestick-pattern triggers (libpattern engulf / pin / threebar) are labelled reversal-fade from their names; libpattern nr and rangeexp are breakout. Flow / tape families are labelled by the variant name (follow vs fade), not by code reading.
- Positive-in-both-windows uses any tested shape of the book, so it flatters all classes equally; the stage fractions (C_fail / D_stop / D_pass) are the cleaner comparison.
- Everything is 1 lot, truly bare, L6M = 2026-05-01..10-31 (data end), in-sample for the pick; correlations use 131 daily and about 26 weekly points.
