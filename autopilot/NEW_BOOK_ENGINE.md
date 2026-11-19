# NEW_BOOK_ENGINE - replacement of the NY AM / NY PM books on the exact engine (W-NYENG), refreshed 2026-11-19 16:53Z

**These rows are vs TODAY's stack (JL3) with today's DAY-DONE setting; they answer add / swap one book in today's stack, not the rebuilt stack.** WP10 and XA3 stay leads on that basis.

Stack = JL3 (all live layers ON). Dollars: engine BASE lots at $4.84 RT/contract proxy with an x1.75 live-lot column in brackets. Deltas = WITH minus the live JL3 stack on the same months; drawdown first: d ulcer / d worst week / d max DD / d mean $/wk (x1.75 in brackets). Negative ulcer / DD change = better. PROVISIONAL cells (selection-biased picks); no label without controls (none yet). Prereg PREREG_NYE.md + AMEND1 (DECISIONS.md). Identity (injection = JL3 with an inert event): 202610: PASS (691 trades, net 37159.82); 202504: PASS (637 trades, net 41239.76). Set-months done: 10848.

## What acts on a new book in these runs (plain words; full list NEW_BOOK_LAYER_FACTS.md)
- ON the new book: the live DAY-DONE rule (engine: scr_hooks gate "conj" = the stack has >= 22 closes today AND the day is <= -2R = -2,400 base = -4,200 live; it applies to every book incl. the new one and skipped 334 of ~800 signals of NA1 in 202610), one position at a time, the book day caps (loss 4,800 $ / profit 12,000 $ default; a 120-pt stop = 2,400 $ at 1 base lot, 4,800 $ at 2 live lots = one stop trips it), the book give-back lock, measured slippage, the stack rule.
- NOT on the new book: no-trade zones, policy take / near-target latch / locks / shave (named live books only), trade-health and context cuts, ATR-skip, breakout rule, governor, session lot tables. So the engine row = the cell under those rules only; its own fitted layers are variant (iii), not built yet. BARE (screen gate and caps off) and ACCT (gate off, account day caps on) variants for NA1 NA2 NA5 NP1 NP5 are queued.

## LEAD STATUS (order 1932Z, ladder cheapest-first)
- **WP10 (NY PM money flow, vol_350 tape_libvol.cmf): lead for "add to TODAY's stack" at most; NOT a rebuilt-stack candidate.** Per PHASE2_TOOLING_TEST.md it is not distinguishable from random entries on its own wide bracket (beats 15 of 30 same-bracket random draws), its best date-shift control came within $135 of it ($41,613 vs real $41,748) and its own-stop result is weak. No more engine is spent on WP10 ahead of the R3 passers (what is running finishes).
- **XA3 (NY AM VWAP retest, tick_5000, levels_vwap.retest_native {M 6, tol 0.5}, plain 60/60): stays at the front.** Beats 25 of 30 same-bracket random draws at screen level (23 / 27 / 29 thresholds: 25 passes 24, fails 27 and 29) and 30 of 30 engine date-shift controls (real +$54,428 vs best control +$24,259, L6M, ADD).

### XA3 engine rows vs TODAY's stack (JL3): add vs replace K7 / P7 / M7 in NY AM (d ulcer / d worst wk / d max DD / d mean $/wk, base lots; x1.75 mean in brackets)
| variant | window | d ulcer | d worst wk | d max DD | d mean $/wk (x1.75) | new-book trades | corr daily w/ K7 / P7 / M7 |
|---|---|---|---|---|---|---|---|
| ADD | L6M | -262 | +1134 | +2888 | +1965 (+3439) | 383 | +0.15 / +0.08 / +0.16 |
| ADD | L3M | -456 | +1134 | +2888 | +1935 (+3386) | 165 | +0.20 / +0.13 / +0.39 |
| ADD | Y2025 | -4939 | +674 | +9036 | +1132 (+1981) | 656 | +0.17 / +0.05 / +0.06 |
| ADD | Y2024 | -5557 | +2660 | +12005 | +938 (+1642) | 541 | +0.15 / +0.09 / +0.21 |
| ADD | Y2023 | -468 | -3097 | -1427 | +1201 (+2102) | 358 | +0.18 / +0.16 / +0.25 |
| RK7 | L6M | +255 | +1651 | +664 | +2505 (+4384) | 382 | +0.14 / +0.08 / +0.16 |
| RK7 | L3M | +303 | +1651 | +664 | +2638 (+4617) | 163 | +0.17 / +0.12 / +0.38 |
| RK7 | Y2025 | -4169 | +7111 | +8946 | +537 (+940) | 664 | +0.17 / +0.05 / +0.07 |
| RK7 | Y2024 | -5800 | +1507 | +15168 | +860 (+1505) | 543 | +0.15 / +0.09 / +0.21 |
| RK7 | Y2023 | +758 | -9899 | -14123 | +404 (+707) | 358 | +0.18 / +0.16 / +0.25 |
| RP7 | L6M | -759 | +1763 | +6179 | +1519 (+2659) | 384 | +0.15 / +0.09 / +0.16 |
| RP7 | L3M | -1379 | +1763 | +6179 | +1230 (+2152) | 165 | +0.20 / +0.13 / +0.39 |
| RP7 | Y2025 | -5231 | +2936 | +10482 | +1235 (+2162) | 656 | +0.17 / +0.05 / +0.06 |
| RP7 | Y2024 | -5702 | +3433 | +12005 | +1236 (+2163) | 541 | +0.15 / +0.09 / +0.21 |
| RP7 | Y2023 | +620 | -4232 | -6433 | +786 (+1376) | 358 | +0.18 / +0.16 / +0.25 |
| RM7 | L6M | -586 | +2357 | +4663 | +1544 (+2702) | 383 | +0.15 / +0.09 / +0.16 |
| RM7 | L3M | -881 | +2357 | +4663 | +965 (+1689) | 164 | +0.20 / +0.12 / +0.39 |
| RM7 | Y2025 | -5100 | +7674 | +9739 | +755 (+1321) | 661 | +0.17 / +0.05 / +0.07 |
| RM7 | Y2024 | -3883 | +3882 | +17235 | +331 (+578) | 545 | +0.15 / +0.09 / +0.20 |
| RM7 | Y2023 | -2911 | -4913 | +4364 | +1346 (+2356) | 358 | +0.18 / +0.16 / +0.25 |

### XA3 OWN-STOP (the cell's own bad-day stop: no new entries for the rest of the label day once the book itself is down k stops; first-order on its engine trades, base lots, net of $4.84)
| window | no own-stop $ | k=1.5: kept $ (trades, dropped $) | k=2: kept $ | k=3: kept $ |
|---|---|---|---|---|
| L6M | +57241 | +45215 (311, +12027) | +59138 (360, -1896) | +54856 (379, +2386) |
| L3M | +25206 | +22327 (140, +2879) | +26255 (158, -1049) | +25206 (165, +0) |
| Y2025 | +80630 | +66984 (589, +13646) | +75866 (633, +4764) | +80619 (652, +11) |
| Y2024 | +55727 | +52735 (502, +2991) | +53890 (531, +1837) | +54531 (540, +1195) |
| Y2023 | +43592 | +44609 (339, -1017) | +44046 (352, -454) | +45942 (356, -2350) |

## R5 ladder (engine staged; SCREEN RANK, NOT YET CALIBRATED: the whole-search null is the judge)
Cells seeded in rank order from /mnt/l2/l2vast/_nye/ladder_cells.json (NY AM by R3 p6 then p_all; NY PM family-bests of the bare rule, R3 not yet run for NY PM). Stage A = last 6 + 3 months as ADD and as replacement of the weakest live book of the session (K7), 12 set-months per cell; B = prior years for rows not negative; C = 30 date-shift controls for rows still alive; D = layer programme in clock order. Built so far: 7285 cells ({'A': 7285}); set-months still queued: 40176. Everything is vs TODAY's stack, provisional until Asia and London are decided.

## XA3 phase 3a (own layers; vs today's stack, provisional until Asia and London are decided)
Identity TL3_NYL_XA3_ID1-9 PASS. Fit stage F1 (72 settings x last 6 months) landed; scored on autopilot/NEW_BOOK_LAYER_FIT_XA3.md (ulcer first, vs the ADD row and vs JL3); stage F2 (top 2 settings per layer with ulcer better and >= 80% of trades, prior years 2023-2026-04) queued; joint stage after F2.

## ID glossary (reconciled 16:10Z; engine ids never change)
- WA<n> / WP<n> = W-SHORT rank n on the 14:23Z page (frozen): **WP1 = NY PM dlt_100 levels_vwap.reject {tol 0, conf close}, plain 60/60** (NOT tm1800); **WP10 = NY PM vol_350 tape_libvol.cmf {len 10}, asym20u/10u (median stop/target 120/60)**; WP11 = tm1800 xmarket_ym.follow plain 60/60 on that page.
- XA<n> / XP<n> = W-SHORT rank n on the 15:19Z equal-risk page (frozen): **XP2 = NY PM tm1800 xmarket_ym.follow {w 5, thr 1.0}**, XP1 = dib_400 tape_libvol.cmf {len 10}, XP3 = tm900 xmarket_es.follow. So XP2 (tm1800 YM follow) is a different cell from WP1 (dlt_100 VWAP reject); the headline rows NYE_WP1_* / NYW_WP1_* are dlt_100 VWAP reject.
- NA<n> / NP<n> = my first provisional six per session (level_nr_qual picks). Set names: TL3_NYE_<id>_ADD|RK7|RP7|RM7|ALL|BARE|ACCT|CT<k><p|m>, TL3_NYW_<id>_ADD (W / X cells), TL3_NYE_C2|C3|D1|D2|P2_<session>_<ids> (P2 = K7 kept + both new books).

## Date-shift controls (same events moved +-7..35 days, same weekday; ADD at 1 base lot; L6M)
| cell | real d mean $/wk | real d ulcer | controls n | controls d mean median / best | controls d ulcer median / best | real beats controls on mean (share) | real better ulcer than controls (share) |
|---|---|---|---|---|---|---|---|
|  | +1117 | -453 | 154 | -126 / +2053 | +420 / -1067 | 0.92 | 0.92 |
| NA1 | -504 | +3903 | 1 | +633 / +633 | +1333 / +1333 | 0.00 | 0.00 |
| NA2 | -38 | +420 | 1 | +806 / +806 | +1832 / +1832 | 0.00 | 1.00 |
| NA4 | +1158 | -8 | 10 | +3 / +703 | +1487 / -504 | 1.00 | 0.90 |
| NA5 | +1351 | +860 | 1 | +2062 / +2062 | +131 / +131 | 0.00 | 0.00 |
| NP1 | -1011 | +400 | 1 | -375 / -375 | +166 / +166 | 0.00 | 0.00 |
| NP5 | +1382 | +242 | 11 | -434 / +940 | +238 / -211 | 1.00 | 0.45 |
| WA2 | +1619 | +904 | 10 | -347 / +1765 | +971 / -720 | 0.90 | 0.50 |
| WP1 | +655 | -132 | 11 | -124 / +639 | +34 / -140 | 1.00 | 0.82 |
| WP10 | +1516 | -206 | 31 | -245 / +2307 | +195 / -710 | 0.97 | 0.94 |
| XA3 | +1965 | -262 | 30 | -486 / +872 | +708 / -639 | 1.00 | 0.93 |

## NY AM - HEADLINE: replacement

### A. What the live NY AM books earn now (JL3 itself, this session only; reference, the bar to beat)
Engine base-lot $/week (x1.75 live), ulcer contribution = stack ulcer minus stack ulcer without the book's session trades (positive = the book adds drawdown), worst week of the book, trades. Base lots in this session: K7 1 / P7 7 / M7 1 / H7 1 base lots (x1.75 = 2 / 12 / 2 / 2 live; order says P7 7).
| window | book | trades | $/wk base (x1.75) | worst wk base (x1.75) | ulcer contribution base (x1.75) | max DD contribution base |
|---|---|---|---|---|---|---|
| L6M | K7 | 207 | -440 (-769) | -5409 (-9466) | -473 (-827) | +2234 |
| L6M | P7 | 45 | +223 (+390) | -3659 (-6404) | +295 (+515) | -1855 |
| L6M | M7 | 240 | +328 (+574) | -5751 (-10063) | +101 (+177) | -209 |
| L6M | H7 | 39 | +329 (+576) | -1773 (-3103) | -216 (-377) | +900 |
| L6M | TOTAL session | 531 | +440 (+770) | -8979 (-15714) | -448 (-784) | +1725 |
| L3M | K7 | 115 | -591 (-1034) | -5409 (-9466) | -749 (-1311) | +2234 |
| L3M | P7 | 31 | +429 (+751) | -3659 (-6404) | +526 (+921) | -1855 |
| L3M | M7 | 101 | +843 (+1476) | -3739 (-6544) | +18 (+31) | -209 |
| L3M | H7 | 20 | +546 (+956) | -1773 (-3103) | -274 (-480) | +900 |
| L3M | TOTAL session | 267 | +1228 (+2149) | -8979 (-15714) | -737 (-1290) | +1725 |
| Y2025 | K7 | 472 | -18 (-32) | -10378 (-18162) | +2063 (+3611) | -5372 |
| Y2025 | P7 | 83 | -117 (-206) | -3572 (-6250) | +1288 (+2254) | -2517 |
| Y2025 | M7 | 432 | +275 (+481) | -7508 (-13139) | -450 (-787) | +3561 |
| Y2025 | H7 | 99 | +131 (+230) | -3243 (-5675) | -1407 (-2463) | +5013 |
| Y2025 | TOTAL session | 1086 | +271 (+474) | -21302 (-37279) | +1068 (+1870) | +463 |
| Y2024 | K7 | 470 | +262 (+459) | -7029 (-12301) | +652 (+1141) | -7298 |
| Y2024 | P7 | 60 | -272 (-476) | -2845 (-4979) | +195 (+341) | +0 |
| Y2024 | M7 | 444 | +596 (+1043) | -5250 (-9187) | -3722 (-6513) | -7746 |
| Y2024 | H7 | 115 | -212 (-372) | -3736 (-6539) | +3128 (+5473) | +940 |
| Y2024 | TOTAL session | 1089 | +374 (+654) | -11257 (-19700) | +2034 (+3559) | -14104 |
| Y2023 | K7 | 331 | +27 (+48) | -6384 (-11172) | +1595 (+2791) | +799 |
| Y2023 | P7 | 46 | +419 (+734) | -2958 (-5177) | -1421 (-2486) | +3329 |
| Y2023 | M7 | 289 | -175 (-307) | -5466 (-9565) | +2502 (+4379) | -3174 |
| Y2023 | H7 | 86 | +110 (+193) | -2415 (-4226) | +1083 (+1895) | -3513 |
| Y2023 | TOTAL session | 752 | +382 (+668) | -9258 (-16201) | +2811 (+4919) | -297 |

Reference row (not a deliverable) "all live NY AM books OFF" (engine set TL3_NYE_OFF_NYAM): L6M d ulcer +1297 / d worst -2578 / d max DD -6011 / d mean -934 $/wk

### Headline table (L6M picks by lowest d ulcer among positive d mean; columns = d ulcer / d worst wk / d max DD / d mean $/wk (x1.75))
| row | set | size | L6M | L3M | 2025 | 2024 | 2023 | controls |
|---|---|---|---|---|---|---|---|---|
| live as-is | JL3 | - | 0 / 0 / 0 / 0 | 0 / 0 / 0 / 0 | 0 | 0 | 0 | - |
| best single swap | NYE_XA2_RP7 | risk-matched c=1.00 | -1067 / +4619 / +6251 / +501 (+876) | -1582 / +4619 / +6251 / -114 (-199) | n/a | n/a | n/a | 0 |
| best whole-session replacement | NYE_C3_NYAM_NA4_WA2_NA6 | risk-matched c=1.67 | +4503 / -14235 / -15729 / +1726 (+3020) | +6687 / -14235 / -15729 / -422 (-738) | -7880 / -765 / -1027 / +1433 (+2508) | +1960 / -12182 / -5935 / +199 (+348) | +5431 / -142 / -11986 / +1431 (+2505) | 0 |
| best mixed (keep best live book + new) | NYE_D2_NYAM_NA4_NA6 | risk-matched c=2.25 | +5773 / -18315 / -18927 / +1509 (+2641) | +8909 / -18315 / -18927 / +70 (+123) | n/a | n/a | +11114 / -10415 / -24567 / +1175 (+2056) | 0 |
(Prior-year windows are queued only for the headline sets after the L6M triage; "n/a" = not run yet. Controls = date-shift sets of the same cell run: 0 so far.)

### Bare-vs-engine BRIDGE (L6M and L3M; 1 base lot; ADD sets) - dollars
| cell | bar | trigger | window | bare screen P&L (same dates / bracket) | new book own P&L in the engine | change in OTHER books | entries blocked / exits forced per rule (engine month logs) |
|---|---|---|---|---|---|---|---|
| NA1 | vol_500 | levels_vwap.break_native | L6M | +17378 (342 tr) | -12525 (218 tr) | -1089 | blocked: inTrade 2791; blocked: SCR gate conj 1641; entries 218; blocked: dayHalt 205; exit: Target 86; exit: Stop 86; exit note: stack rule Asia-only, no cut 86 |
| NA1 | vol_500 | levels_vwap.break_native | L3M | -34344 (136 tr) | -31165 (95 tr) | +743 | blocked: inTrade 1471; blocked: SCR gate conj 692; entries 95; blocked: dayHalt 88; exit: Stop 38; exit note: stack rule Asia-only, no cut 38; exit: Target 29 |
| NA2 | rng_28 | levels_vwap.retest_native | L6M | +6598 (339 tr) | -2263 (200 tr) | +1234 | blocked: inTrade 2255; blocked: SCR gate conj 1486; entries 200; exit: Target 80; blocked: dayHalt 80; exit: Stop 76; exit note: stack rule Asia-only, no cut 76 |
| NA2 | rng_28 | levels_vwap.retest_native | L3M | -29300 (135 tr) | -1591 (88 tr) | +3581 | blocked: inTrade 1135; blocked: SCR gate conj 548; entries 88; exit: Target 31; exit: Stop 29; exit note: stack rule Asia-only, no cut 29; exit: UWTime 27 |
| NA3 | vol_500 | levels_profile_nodes.break | L6M | -5734 (267 tr) | +18671 (164 tr) | +565 | blocked: inTrade 2849; blocked: SCR gate conj 1381; blocked: dayHalt 189; entries 164; exit: Target 64; exit: Stop 55; exit note: stack rule Asia-only, no cut 55 |
| NA3 | vol_500 | levels_profile_nodes.break | L3M | -22393 (98 tr) | -18674 (70 tr) | +565 | blocked: inTrade 1512; blocked: SCR gate conj 512; entries 70; blocked: dayHalt 41; exit: Stop 26; exit note: stack rule Asia-only, no cut 26; exit: UWTime 24 |
| NA4 | vol_350 | levels_vwap_bands.break_native | L6M | +45104 (514 tr) | +37971 (316 tr) | -6710 | blocked: inTrade 5377; blocked: SCR gate conj 2790; entries 316; blocked: dayHalt 232; exit: Target 137; exit: Stop 101; exit note: stack rule Asia-only, no cut 101 |
| NA4 | vol_350 | levels_vwap_bands.break_native | L3M | +10192 (198 tr) | +8822 (137 tr) | -3940 | blocked: inTrade 2898; blocked: SCR gate conj 1225; entries 137; exit: Target 57; exit: UWTime 43; exit: Stop 36; exit note: stack rule Asia-only, no cut 36 |
| NA5 | rng_28 | levels_round.break_native | L6M | +4956 (466 tr) | +19783 (267 tr) | +16696 | blocked: inTrade 1279; blocked: SCR gate conj 1011; entries 267; blocked: dayHalt 167; exit: Target 104; exit: Stop 91; exit note: stack rule Asia-only, no cut 91 |
| NA5 | rng_28 | levels_round.break_native | L3M | -8475 (172 tr) | +8668 (111 tr) | +13035 | blocked: inTrade 562; blocked: SCR gate conj 357; entries 111; exit: Target 39; exit: UWTime 38; exit: Stop 34; exit note: stack rule Asia-only, no cut 34 |
| NA6 | vol_4000 | levels_opens.retest_native | L6M | +47291 (300 tr) | +33800 (188 tr) | -988 | blocked: inTrade 593; blocked: SCR gate conj 417; entries 188; exit: Target 77; exit: Stop 63; exit note: stack rule Asia-only, no cut 63; exit: UWTime 47 |
| NA6 | vol_4000 | levels_opens.retest_native | L3M | -4114 (118 tr) | -4222 (80 tr) | +592 | blocked: inTrade 364; blocked: SCR gate conj 190; entries 80; exit: Target 27; exit: UWTime 27; exit: Stop 26; exit note: stack rule Asia-only, no cut 26 |
| WA1 | vrb_700 | levels_profile_nodes.break | L6M | -7444 (265 tr) | +15428 (174 tr) | -7053 | blocked: inTrade 1020; blocked: SCR gate conj 520; blocked: dayHalt 54; entries 47; exit: Target 19; exit: UWTime 14; exit: Stop 12 |
| WA1 | vrb_700 | levels_profile_nodes.break | L3M | +2804 (94 tr) | +4172 (75 tr) | -3455 | blocked: inTrade 1020; blocked: SCR gate conj 520; blocked: dayHalt 54; entries 47; exit: Target 19; exit: UWTime 14; exit: Stop 12 |
| WA2 | tick_2000 | levels_vwap.break_native | L6M | +16960 (341 tr) | +35559 (211 tr) | +8162 | blocked: inTrade 262; blocked: SCR gate conj 190; entries 59; exit: UWTime 21; exit: Target 20; exit: Stop 17; exit note: stack rule Asia-only, no cut 17 |
| WA2 | tick_2000 | levels_vwap.break_native | L3M | +12892 (124 tr) | +9404 (90 tr) | +6590 | blocked: inTrade 262; blocked: SCR gate conj 190; entries 59; exit: UWTime 21; exit: Target 20; exit: Stop 17; exit note: stack rule Asia-only, no cut 17 |
| WA3 | vol_750 | structure_level.round_break | L6M | -53068 (472 tr) | -23754 (286 tr) | +2611 | blocked: inTrade 619; blocked: SCR gate conj 406; entries 68; exit: UWTime 26; exit: Stop 21; exit note: stack rule Asia-only, no cut 21; exit: Target 21 |
| WA3 | vol_750 | structure_level.round_break | L3M | -30210 (167 tr) | -11843 (104 tr) | -2295 | blocked: inTrade 619; blocked: SCR gate conj 406; entries 68; exit: UWTime 26; exit: Stop 21; exit note: stack rule Asia-only, no cut 21; exit: Target 21 |
| WA4 | vrb_700 | levels_vwap.break_native | L6M | +22606 (360 tr) | +15441 (227 tr) | -3442 | blocked: inTrade 864; blocked: SCR gate conj 613; entries 63; exit: Target 23; exit: Stop 23; exit note: stack rule Asia-only, no cut 23; blocked: dayHalt 19 |
| WA4 | vrb_700 | levels_vwap.break_native | L3M | -17782 (138 tr) | -22164 (98 tr) | -1661 | blocked: inTrade 864; blocked: SCR gate conj 613; entries 63; exit: Target 23; exit: Stop 23; exit note: stack rule Asia-only, no cut 23; blocked: dayHalt 19 |
| WA5 | dlt_400 | trend_adx_di.adx_cross | L6M | -222 (124 tr) | +8023 (83 tr) | +447 | entries 83; blocked: SCR gate conj 56; blocked: inTrade 49; exit: UWTime 32; exit: Target 27; exit: Stop 24; exit note: stack rule Asia-only, no cut 24 |
| WA5 | dlt_400 | trend_adx_di.adx_cross | L3M | +398 (56 tr) | -583 (42 tr) | -2778 | entries 42; blocked: inTrade 27; exit: UWTime 22; blocked: SCR gate conj 20; exit: Target 10; exit: Stop 10; exit note: stack rule Asia-only, no cut 10 |
| WA6 | vol_4000 | bands_regchan.break_stderr | L6M | -16670 (337 tr) | +13811 (227 tr) | +688 | blocked: inTrade 297; entries 227; blocked: SCR gate conj 212; exit: Target 82; exit: Stop 76; exit note: stack rule Asia-only, no cut 76; exit: UWTime 64 |
| WA6 | vol_4000 | bands_regchan.break_stderr | L3M | +7230 (139 tr) | +4096 (99 tr) | -804 | blocked: inTrade 171; blocked: SCR gate conj 100; entries 99; exit: UWTime 35; exit: Stop 31; exit note: stack rule Asia-only, no cut 31; exit: Target 31 |
| WA9 | tick_500 | structure_breakout.brk_native | L6M | +15513 (451 tr) | +34569 (277 tr) | -9863 | blocked: inTrade 1201; blocked: SCR gate conj 744; entries 277; exit: Target 112; blocked: dayHalt 94; exit: Stop 87; exit note: stack rule Asia-only, no cut 87 |
| WA9 | tick_500 | structure_breakout.brk_native | L3M | +40399 (173 tr) | +27199 (120 tr) | -6022 | blocked: inTrade 651; blocked: SCR gate conj 345; entries 120; exit: Target 47; exit: UWTime 40; exit: Stop 31; exit note: stack rule Asia-only, no cut 31 |
| WA10 | vol_500 | tape_delta.follow_sm | L6M | +13400 (493 tr) | +32230 (281 tr) | -1570 | blocked: inTrade 6201; blocked: SCR gate conj 3400; blocked: dayHalt 702; entries 281; exit: Target 113; exit: Stop 84; exit note: stack rule Asia-only, no cut 84 |
| WA10 | vol_500 | tape_delta.follow_sm | L3M | -17766 (183 tr) | -8721 (120 tr) | -3142 | blocked: inTrade 3426; blocked: SCR gate conj 1648; entries 120; blocked: dayHalt 63; exit: UWTime 41; exit: Target 40; exit: Stop 35 |
| WA11 | cusum_20 | levels_vwap.break | L6M | +15281 (337 tr) | -21079 (196 tr) | -235 | blocked: inTrade 850; blocked: SCR gate conj 627; entries 57; blocked: dayHalt 30; exit: Stop 21; exit note: stack rule Asia-only, no cut 21; exit: Target 19 |
| WA11 | cusum_20 | levels_vwap.break | L3M | -46500 (134 tr) | -31616 (89 tr) | -1679 | blocked: inTrade 850; blocked: SCR gate conj 627; entries 57; blocked: dayHalt 30; exit: Stop 21; exit note: stack rule Asia-only, no cut 21; exit: Target 19 |
| WA12 | vrb_700 | levels_profile_nodes.false_break | L6M | -5428 (265 tr) | +12283 (174 tr) | -7053 | blocked: inTrade 773; blocked: SCR gate conj 401; entries 47; blocked: dayHalt 42; exit: Target 19; exit: UWTime 14; exit: Stop 12 |
| WA12 | vrb_700 | levels_profile_nodes.false_break | L3M | +2654 (94 tr) | +4062 (75 tr) | -3455 | blocked: inTrade 773; blocked: SCR gate conj 401; entries 47; blocked: dayHalt 42; exit: Target 19; exit: UWTime 14; exit: Stop 12 |
| XA3 | tick_5000 | levels_vwap.retest_native | L6M | +4511 (651 tr) | +57241 (383 tr) | -4189 |  |
| XA3 | tick_5000 | levels_vwap.retest_native | L3M | +10871 (250 tr) | +25206 (165 tr) | -51 |  |
| XA1 | frenko_40 | book_ofi.follow_sm | L6M | +49990 (598 tr) | +12888 (333 tr) | +6927 |  |
| XA1 | frenko_40 | book_ofi.follow_sm | L3M | +5385 (275 tr) | +2855 (158 tr) | +990 |  |
| XA2 | renko_10 | momentum_mvote.v3of5_native | L6M | +44 (1386 tr) | +19579 (651 tr) | +2918 | blocked: inTrade 592; blocked: SCR gate conj 450; blocked: dayHalt 305; entries 96; exit: Target 48; exit: Stop 36; exit note: stack rule Asia-only, no cut 36 |
| XA2 | renko_10 | momentum_mvote.v3of5_native | L3M | -4706 (471 tr) | +2802 (261 tr) | +3030 |  |
| XA4 | pnf_7 | pullback_st.st | L3M | -5342 (313 tr) | -4100 (189 tr) | -6986 | blocked: SCR gate conj 234; entries 189; blocked: inTrade 181; exit: Target 85; exit: Stop 84; exit note: stack rule Asia-only, no cut 84; blocked: dayHalt 15 |
| XA4 | pnf_7 | pullback_st.st | L6M | +17751 (803 tr) | +7154 (431 tr) | -13742 | blocked: SCR gate conj 573; entries 431; blocked: inTrade 349; exit: Target 200; exit: Stop 187; exit note: stack rule Asia-only, no cut 187; blocked: dayHalt 82 |
| XA5 | kagi_28 | book_ofi.follow_sm | L6M | +19761 (1246 tr) | +47374 (648 tr) | -1969 | blocked: SCR gate conj 1302; blocked: inTrade 998; entries 648; exit: Target 313; blocked: dayHalt 294; exit: Stop 270; exit note: stack rule Asia-only, no cut 270 |
| XA5 | kagi_28 | book_ofi.follow_sm | L3M | -52558 (458 tr) | -31913 (261 tr) | -1797 | blocked: SCR gate conj 564; blocked: inTrade 521; entries 261; exit: Stop 125; exit note: stack rule Asia-only, no cut 125; exit: Target 100; blocked: dayHalt 61 |
| XA6 | renko_20 | trend_libstack.ema_hold | L6M | +5349 (1143 tr) | +48960 (533 tr) | -1076 | blocked: SCR gate conj 792; entries 533; blocked: inTrade 447; blocked: dayHalt 277; exit: Target 265; exit: Stop 208; exit note: stack rule Asia-only, no cut 208 |
| XA6 | renko_20 | trend_libstack.ema_hold | L3M | -25068 (397 tr) | +16650 (219 tr) | -7024 | blocked: SCR gate conj 292; blocked: inTrade 246; entries 219; exit: Target 108; blocked: dayHalt 86; exit: Stop 85; exit note: stack rule Asia-only, no cut 85 |
| La0dbbae6 | tick_5000 | levels_profile_nodes.break | L6M | -12634 (239 tr) | +9899 (147 tr) | -3914 |  |
| La0dbbae6 | tick_5000 | levels_profile_nodes.break | L3M | +5158 (88 tr) | +12130 (60 tr) | -2330 |  |
| L60cef2ae | drb_240 | levels_profile_nodes.false_break_native | L6M | -19359 (573 tr) | +8983 (362 tr) | -5699 |  |
| L60cef2ae | drb_240 | levels_profile_nodes.false_break_native | L3M | +690 (201 tr) | -582 (144 tr) | -3927 |  |
| L18117a71 | vrb_240 | levels_profile_va.break_native | L6M | -1766 (286 tr) | +13910 (188 tr) | -8566 |  |
| L18117a71 | vrb_240 | levels_profile_va.break_native | L3M | -5654 (123 tr) | +3389 (88 tr) | -2989 |  |
| Lb696c500 | drb_240 | levels_profile_nodes.false_break | L6M | -12376 (634 tr) | +9180 (372 tr) | -8999 |  |
| Lb696c500 | drb_240 | levels_profile_nodes.false_break | L3M | -11806 (217 tr) | +1384 (149 tr) | -7227 |  |
| L8ac754c9 | drb_2000 | levels_profile_nodes.false_break_native | L6M | -27807 (254 tr) | +22210 (159 tr) | -614 |  |
| L8ac754c9 | drb_2000 | levels_profile_nodes.false_break_native | L3M | -8209 (96 tr) | +3557 (73 tr) | -614 |  |
| L265998e4 | drb_2000 | levels_profile_nodes.false_break | L6M | -27807 (254 tr) | +22210 (159 tr) | -614 |  |
| L265998e4 | drb_2000 | levels_profile_nodes.false_break | L3M | -8209 (96 tr) | +3557 (73 tr) | -614 |  |
| L39470318 | vol_750 | levels_profile_va.retest | L6M | +44179 (397 tr) | +43327 (264 tr) | -4136 |  |
| L39470318 | vol_750 | levels_profile_va.retest | L3M | +16913 (166 tr) | +18140 (127 tr) | -2364 |  |
| L3fd2d876 | vol_6000 | levels_profile_va.false_break_native | L6M | +22010 (134 tr) | +24649 (90 tr) | +2693 |  |
| L3fd2d876 | vol_6000 | levels_profile_va.false_break_native | L3M | +8278 (55 tr) | +10467 (41 tr) | +2693 |  |
| Lf7bced9d | dol_350 | levels_profile_nodes.retest_native | L6M | +32887 (261 tr) | +14186 (162 tr) | +7375 |  |
| Lf7bced9d | dol_350 | levels_profile_nodes.retest_native | L3M | -2288 (94 tr) | -12729 (71 tr) | +7375 |  |
| L582e03e7 | drb_1200 | book_cancel.net_follow | L6M | -13226 (268 tr) | +17393 (177 tr) | -9276 |  |
| L582e03e7 | drb_1200 | book_cancel.net_follow | L3M | -13855 (110 tr) | -2092 (80 tr) | -8948 |  |
| L308e6047 | drb_2000 | book_ofi.follow | L6M | +14923 (318 tr) | +19285 (217 tr) | -6240 |  |
| L308e6047 | drb_2000 | book_ofi.follow | L3M | +23543 (135 tr) | +20636 (97 tr) | -4271 |  |
| L79892e2e | rng_20 | levels_profile_va.break_native | L6M | +29130 (209 tr) | +27327 (137 tr) | -3933 |  |
| L79892e2e | rng_20 | levels_profile_va.break_native | L3M | -4219 (81 tr) | -12455 (61 tr) | -834 |  |
| L3aca3c47 | rng_28 | levels_profile_va.false_break_native | L6M | +15678 (207 tr) | +33413 (141 tr) | -9606 |  |
| L3aca3c47 | rng_28 | levels_profile_va.false_break_native | L3M | +5011 (85 tr) | +10385 (65 tr) | -2308 |  |
| L471515d9 | rng_56 | levels_profile_va.retest_native | L6M | +7831 (384 tr) | +11404 (241 tr) | +412 |  |
| L471515d9 | rng_56 | levels_profile_va.retest_native | L3M | +642 (145 tr) | -802 (113 tr) | -2958 |  |
| L28f3d3c1 | rng_20 | levels_profile_va.break | L6M | +29130 (209 tr) | +27327 (137 tr) | -3933 |  |
| L28f3d3c1 | rng_20 | levels_profile_va.break | L3M | -4219 (81 tr) | -12455 (61 tr) | -834 |  |
| Lcfeda8c4 | rng_28 | levels_profile_va.false_break | L6M | +15678 (207 tr) | +33413 (141 tr) | -9606 |  |
| Lcfeda8c4 | rng_28 | levels_profile_va.false_break | L3M | +5011 (85 tr) | +10385 (65 tr) | -2308 |  |
| L21f079b6 | wrenko_20 | levels_profile_va.break_native | L6M | +16870 (205 tr) | +50552 (135 tr) | -4900 |  |
| L21f079b6 | wrenko_20 | levels_profile_va.break_native | L3M | +18180 (82 tr) | +24230 (62 tr) | +2748 |  |
| L875ee048 | mrenko_10 | levels_profile_va.break | L6M | -6116 (472 tr) | +6606 (288 tr) | -480 |  |
| L875ee048 | mrenko_10 | levels_profile_va.break | L3M | -14765 (190 tr) | -5437 (141 tr) | +1665 |  |
| Lcced15b8 | renko_14 | levels_profile_va.break | L6M | +43184 (242 tr) | +28670 (156 tr) | -2103 |  |
| Lcced15b8 | renko_14 | levels_profile_va.break | L3M | +2926 (103 tr) | +1237 (74 tr) | -199 |  |
| L718a3a1d | renko_14 | levels_profile_va.retest_native | L6M | +25315 (227 tr) | +33499 (153 tr) | -3523 |  |
| L718a3a1d | renko_14 | levels_profile_va.retest_native | L3M | +6854 (90 tr) | -2109 (71 tr) | -632 |  |
| Lf967df3b | wrenko_20 | levels_profile_va.break | L6M | +16870 (205 tr) | +50552 (135 tr) | -4900 |  |
| Lf967df3b | wrenko_20 | levels_profile_va.break | L3M | +18180 (82 tr) | +24230 (62 tr) | +2748 |  |
| L79cd626b | frenko_40 | levels_profile_va.false_break_native | L6M | +11767 (196 tr) | +30860 (125 tr) | +337 |  |
| L79cd626b | frenko_40 | levels_profile_va.false_break_native | L3M | +16297 (75 tr) | +19694 (56 tr) | +337 |  |
| Lc6e4ce81 | kagi_14 | levels_profile_nodes.false_break_native | L6M | +11193 (270 tr) | +34447 (171 tr) | -6609 |  |
| Lc6e4ce81 | kagi_14 | levels_profile_nodes.false_break_native | L3M | +14512 (91 tr) | +24226 (68 tr) | -3012 |  |
| L6be3bb7c | tm180 | levels_profile_va.reject | L6M | +9309 (320 tr) | +20381 (192 tr) | +2225 |  |
| L6be3bb7c | tm180 | levels_profile_va.reject | L3M | -8633 (134 tr) | +2585 (92 tr) | -461 |  |
| L11967aac | tm180 | levels_profile_va.reject_native | L6M | +9309 (320 tr) | +20381 (192 tr) | +2225 |  |
| L11967aac | tm180 | levels_profile_va.reject_native | L3M | -8633 (134 tr) | +2585 (92 tr) | -461 |  |
| Lcd368087 | tick_2000 | structure_breakout.brk_native | L6M | -602 (190 tr) | +15122 (138 tr) | -1427 |  |
| Lcd368087 | tick_2000 | structure_breakout.brk_native | L3M | -4915 (91 tr) | +5586 (69 tr) | -4113 |  |
| Ld47902ff | vol_1100 | levels_vwap.break | L6M | +34993 (333 tr) | +48549 (210 tr) | -9032 |  |
| Ld47902ff | vol_1100 | levels_vwap.break | L3M | -20356 (128 tr) | -6736 (89 tr) | -9785 |  |
| L33d1c278 | vol_750 | bands_envelope.break_ema | L6M | +614 (441 tr) | +19697 (262 tr) | +5083 |  |
| L33d1c278 | vol_750 | bands_envelope.break_ema | L3M | -4355 (165 tr) | -2503 (105 tr) | +6426 |  |
| L45796a06 | vsess_30 | bands_keltner.break | L6M | +16505 (230 tr) | +16366 (165 tr) | +81 |  |
| L45796a06 | vsess_30 | bands_keltner.break | L3M | +11700 (104 tr) | +3067 (77 tr) | +2820 |  |
| Led8baed4 | vol_4000 | levels_vwap.break | L6M | +34313 (309 tr) | +51786 (192 tr) | +15057 |  |
| Led8baed4 | vol_4000 | levels_vwap.break | L3M | +4602 (117 tr) | +13948 (81 tr) | +12315 |  |
| Lf0447f1d | vsess_30 | levels_vwap.retest_native | L6M | +28205 (262 tr) | -3083 (168 tr) | +14084 |  |
| Lf0447f1d | vsess_30 | levels_vwap.retest_native | L3M | +26992 (102 tr) | +8766 (71 tr) | +14373 |  |
| L5ee8ac30 | vol_1100 | levels_vwap.break_native | L6M | +34993 (333 tr) | +48549 (210 tr) | -9032 |  |
| L5ee8ac30 | vol_1100 | levels_vwap.break_native | L3M | -20356 (128 tr) | -6736 (89 tr) | -9785 |  |
| L3622205c | tick_500 | structure_breakout.brk | L6M | +54130 (486 tr) | +36517 (292 tr) | -7926 |  |
| L3622205c | tick_500 | structure_breakout.brk | L3M | +5051 (181 tr) | +4369 (117 tr) | -2184 |  |
| L60a286ff | swing_atr_0.25 | levels_profile_va.false_break_native | L6M | +21053 (220 tr) | +28448 (145 tr) | -4563 |  |
| L60a286ff | swing_atr_0.25 | levels_profile_va.false_break_native | L3M | +19721 (87 tr) | +15865 (65 tr) | +1015 |  |
| Le289ed93 | mom_28 | levels_profile_va.false_break_native | L6M | +26973 (197 tr) | +56657 (135 tr) | -8720 |  |
| Le289ed93 | mom_28 | levels_profile_va.false_break_native | L3M | +14875 (77 tr) | +22290 (61 tr) | -1072 |  |
| L593a5c56 | dchg_14 | levels_profile_nodes.false_break_native | L6M | +11239 (270 tr) | +34447 (171 tr) | -6609 |  |
| L593a5c56 | dchg_14 | levels_profile_nodes.false_break_native | L3M | +14529 (91 tr) | +24226 (68 tr) | -3012 |  |
| L8f126a83 | swing_pct_8 | levels_profile_nodes.false_break | L6M | +33179 (282 tr) | +31958 (174 tr) | -4337 |  |
| L8f126a83 | swing_pct_8 | levels_profile_nodes.false_break | L3M | +22200 (97 tr) | +25301 (69 tr) | +204 |  |
| Ld213a0b4 | mom_20 | levels_profile_va.false_break | L6M | +29421 (206 tr) | +38767 (135 tr) | -2624 |  |
| Ld213a0b4 | mom_20 | levels_profile_va.false_break | L3M | +17694 (83 tr) | +21015 (64 tr) | +2954 |  |
| L7b30753e | swing_pct_5 | levels_profile_nodes.false_break_native | L6M | -2750 (281 tr) | +37788 (178 tr) | -2016 |  |
| L7b30753e | swing_pct_5 | levels_profile_nodes.false_break_native | L3M | -2398 (95 tr) | +8332 (73 tr) | +1581 |  |
| Lbbb39855 | trend_20 | levels_profile_va.break_native | L6M | +16870 (205 tr) | +50552 (135 tr) | -4900 |  |
| Lbbb39855 | trend_20 | levels_profile_va.break_native | L3M | +18180 (82 tr) | +24230 (62 tr) | +2748 |  |
| L0bd23639 | trend_20 | levels_profile_va.break | L6M | +16870 (205 tr) | +50552 (135 tr) | -4900 |  |
| L0bd23639 | trend_20 | levels_profile_va.break | L3M | +18180 (82 tr) | +24230 (62 tr) | +2748 |  |
| L7ab10be1 | time_m_1 | bands_atrchan.break_ema_native | L6M | +26866 (275 tr) | +34830 (190 tr) | +766 |  |
| L7ab10be1 | time_m_1 | bands_atrchan.break_ema_native | L3M | +16554 (119 tr) | +19704 (86 tr) | -3783 |  |
| L7515c303 | swing_pct_5 | levels_vwap.break | L6M | +43626 (340 tr) | +45674 (212 tr) | +11585 |  |
| L7515c303 | swing_pct_5 | levels_vwap.break | L3M | +3410 (129 tr) | +7669 (88 tr) | +14688 |  |
| Lb3d7eb1b | urenko_28 | bands_bollinger.break_native | L6M | +14645 (450 tr) | +30585 (253 tr) | -2432 |  |
| Lb3d7eb1b | urenko_28 | bands_bollinger.break_native | L3M | -5744 (163 tr) | -13608 (105 tr) | -2657 |  |
| Ld2610290 | swing_atr_0.25 | levels_vwap.break_native | L6M | +44165 (347 tr) | +48584 (211 tr) | +5282 |  |
| Ld2610290 | swing_atr_0.25 | levels_vwap.break_native | L3M | +33712 (133 tr) | +34764 (89 tr) | +9162 |  |
| Le2a6e063 | time_m_20 | levels_fib60.break | L6M | +15679 (225 tr) | +6709 (151 tr) | +970 |  |
| Le2a6e063 | time_m_20 | levels_fib60.break | L3M | +8365 (106 tr) | -2423 (78 tr) | -846 |  |
| L925bb0f5 | renko_14 | structure_fvg.retest | L6M | +24740 (438 tr) | +30316 (254 tr) | -8722 |  |
| L925bb0f5 | renko_14 | structure_fvg.retest | L3M | +27029 (162 tr) | +26627 (106 tr) | +1660 |  |
| Lb292f65c | dib_40000 | trend_ichimoku.tk_cross_native | L6M | +21492 (297 tr) | +13945 (281 tr) | -13147 |  |
| Lb292f65c | dib_40000 | trend_ichimoku.tk_cross_native | L3M | +17655 (148 tr) | -5083 (136 tr) | -8793 |  |
| L27ec09c7 | dol_350 | structure_libpattern.threebar | L6M | -24993 (513 tr) | +37185 (284 tr) | +1722 |  |
| L27ec09c7 | dol_350 | structure_libpattern.threebar | L3M | +11806 (179 tr) | +23854 (117 tr) | -285 |  |
| L6e35bff0 | pnf_10 | bands_avwap0930.break_0930 | L6M | +25179 (463 tr) | +12842 (483 tr) | -1681 |  |
| L6e35bff0 | pnf_10 | bands_avwap0930.break_0930 | L3M | +13028 (198 tr) | -10535 (221 tr) | -779 |  |
| L1c19f73f | renko_28 | trend_heikin.run | L6M | +53253 (362 tr) | +49975 (220 tr) | +5294 |  |
| L1c19f73f | renko_28 | trend_heikin.run | L3M | +47345 (134 tr) | +28369 (90 tr) | +8414 |  |
| L932bb28e | tm240 | book_ofi.follow | L6M | +24929 (735 tr) | +13136 (444 tr) | +1060 |  |
| L932bb28e | tm240 | book_ofi.follow | L3M | -8825 (333 tr) | -7897 (205 tr) | +1376 |  |
| Lcdaa40bf | tm180 | book_cancel.net_follow_native | L6M | -279 (269 tr) | +27229 (180 tr) | -1185 |  |
| Lcdaa40bf | tm180 | book_cancel.net_follow_native | L3M | +17648 (116 tr) | +32503 (84 tr) | -2043 |  |
| L840241d1 | lbrk_3_10 | levels_fibr_on.break_native | L6M | -23935 (1047 tr) | +13425 (501 tr) | -9724 |  |
| L840241d1 | lbrk_3_10 | levels_fibr_on.break_native | L3M | +1643 (381 tr) | +6213 (204 tr) | -2050 |  |
| L68b147b4 | vsess_450 | momentum_mvote.v5of5_native | L6M | -6195 (324 tr) | +17786 (222 tr) | +3036 |  |
| L68b147b4 | vsess_450 | momentum_mvote.v5of5_native | L3M | -3053 (145 tr) | -5124 (101 tr) | +4868 |  |
| L4540ec78 | kagi_40 | levels_fibr_dev.retest_native | L6M | +11570 (457 tr) | +18982 (263 tr) | -9194 |  |
| L4540ec78 | kagi_40 | levels_fibr_dev.retest_native | L3M | -3632 (160 tr) | +2987 (104 tr) | -2328 |  |
| Lb44a3e99 | tm300 | tape_delta.cvd_follow | L6M | +29357 (329 tr) | +43884 (211 tr) | -4638 |  |
| Lb44a3e99 | tm300 | tape_delta.cvd_follow | L3M | +5150 (156 tr) | +16727 (106 tr) | -5509 |  |
| L8e5a7466 | vrb_40000 | levels_trendline.break | L6M | +14159 (128 tr) | +17943 (80 tr) | -5397 |  |
| L8e5a7466 | vrb_40000 | levels_trendline.break | L3M | +5584 (65 tr) | +4576 (40 tr) | -4282 |  |
| L33d4983b | renko_14 | levels_gaps.reject | L6M | +5062 (211 tr) | +35896 (132 tr) | -8366 |  |
| L33d4983b | renko_14 | levels_gaps.reject | L3M | +33181 (73 tr) | +28004 (56 tr) | -3618 |  |
| L0eb430f0 | dlt_100 | bands_bollinger.walk_native | L6M | +24824 (531 tr) | +34675 (341 tr) | -3660 |  |
| L0eb430f0 | dlt_100 | bands_bollinger.walk_native | L3M | +34523 (221 tr) | +37779 (152 tr) | -6238 |  |
| L1084d6ee | drb_10000 | bands_avwap0830.break_0830_native | L6M | +4317 (376 tr) | +3735 (253 tr) | +2621 |  |
| L1084d6ee | drb_10000 | bands_avwap0830.break_0830_native | L3M | -8486 (185 tr) | -2739 (131 tr) | +202 |  |
| L9d14d49d | bmsg_B030 | book_cancel.net_follow | L6M | +37545 (263 tr) | +54573 (172 tr) | -300 |  |
| L9d14d49d | bmsg_B030 | book_cancel.net_follow | L3M | +27719 (87 tr) | +13025 (65 tr) | -1158 |  |
| L9145e5cf | lbrk_3_10 | levels_vwap.break | L6M | +24172 (398 tr) | +51944 (241 tr) | +5103 |  |
| L9145e5cf | lbrk_3_10 | levels_vwap.break | L3M | +920 (158 tr) | -3502 (113 tr) | +2477 |  |
| Lee8faff6 | drb_10000 | bands_avwap0830.break_0830_native | L6M | +4317 (376 tr) | +3735 (253 tr) | +2621 |  |
| Lee8faff6 | drb_10000 | bands_avwap0830.break_0830_native | L3M | -8486 (185 tr) | -2739 (131 tr) | +202 |  |
| L58bcf9fc | dchg_10 | bands_keltner.break | L6M | +193 (504 tr) | +39983 (299 tr) | -4393 |  |
| L58bcf9fc | dchg_10 | bands_keltner.break | L3M | -3447 (186 tr) | +7385 (128 tr) | -2491 |  |
| L94ad0a1e | anch_L0200_B50 | levels_piv_floor.break_native | L6M | +7418 (482 tr) | +12258 (297 tr) | +9286 |  |
| L94ad0a1e | anch_L0200_B50 | levels_piv_floor.break_native | L3M | +11657 (218 tr) | +7832 (140 tr) | +9601 |  |
| L47543131 | kagi_20 | levels_vwap.break | L6M | +47636 (342 tr) | +33803 (207 tr) | +3186 |  |
| L47543131 | kagi_20 | levels_vwap.break | L3M | +8468 (134 tr) | +8899 (88 tr) | +5234 |  |
| Lcbda2ba7 | pasl_40 | xmarket_fast.follow_RTY | L6M | +27188 (479 tr) | +26044 (306 tr) | +14669 |  |
| Lcbda2ba7 | pasl_40 | xmarket_fast.follow_RTY | L3M | +26779 (193 tr) | +26272 (138 tr) | +8845 |  |
| L5332c1f1 | bmsg_B130 | trend_linreg.thresh_native | L6M | +18681 (307 tr) | +17227 (203 tr) | +6327 |  |
| L5332c1f1 | bmsg_B130 | trend_linreg.thresh_native | L3M | +12747 (148 tr) | +456 (100 tr) | +5421 |  |
| L97883de8 | drb_10000 | bands_envelope.break_ema | L6M | +20011 (333 tr) | +20850 (216 tr) | +345 |  |
| L97883de8 | drb_10000 | bands_envelope.break_ema | L3M | +12566 (157 tr) | +7687 (109 tr) | -1655 |  |
| Lb36e86fe | dol_500 | momentum_er.trend_z | L6M | +40111 (207 tr) | +33589 (148 tr) | +8786 |  |
| Lb36e86fe | dol_500 | momentum_er.trend_z | L3M | +31609 (98 tr) | +24712 (73 tr) | +7868 |  |
| L70d2a976 | mom_20 | bands_atrchan.break_ema | L6M | +12431 (317 tr) | +26546 (193 tr) | -2281 |  |
| L70d2a976 | mom_20 | bands_atrchan.break_ema | L3M | +12629 (127 tr) | +15633 (83 tr) | -2220 |  |
| L5879e162 | vol_1700 | book_ofi.follow_native | L6M | +33097 (1071 tr) | +47190 (596 tr) | +7631 |  |
| L5879e162 | vol_1700 | book_ofi.follow_native | L3M | +30702 (427 tr) | +16988 (238 tr) | +5628 |  |
| L72dec2a9 | dol_500 | levels_fibr_pd.reject_native | L6M | +7481 (1075 tr) | +16325 (501 tr) | -8747 |  |
| L72dec2a9 | dol_500 | levels_fibr_pd.reject_native | L3M | +8101 (375 tr) | +17509 (211 tr) | -2518 |  |
| Lf851abc1 | kagi_20 | levels_vwap.break_native | L6M | +47636 (342 tr) | +33803 (207 tr) | +3186 |  |
| Lf851abc1 | kagi_20 | levels_vwap.break_native | L3M | +8468 (134 tr) | +8899 (88 tr) | +5234 |  |
| L3ec75870 | dol_500 | bands_atrchan.break_ext_native | L6M | +29277 (466 tr) | +17650 (281 tr) | -8203 |  |
| L3ec75870 | dol_500 | bands_atrchan.break_ext_native | L3M | +16570 (173 tr) | -14142 (111 tr) | -741 |  |
| L13858cd5 | swing_pct_8 | pullback_ema.depth_native | L6M | +2624 (490 tr) | +13244 (276 tr) | +5815 |  |
| L13858cd5 | swing_pct_8 | pullback_ema.depth_native | L3M | +18509 (166 tr) | +18542 (109 tr) | +8404 |  |
| L9a245fb4 | dlt_100 | bands_vwap.break_native | L3M | -13251 (312 tr) | -14680 (190 tr) | +1989 |  |
| L0b6dde51 | swing_pct_12 | levels_session_hl.retest_native | L6M | +26916 (386 tr) | +35025 (220 tr) | -2804 |  |
| L0b6dde51 | swing_pct_12 | levels_session_hl.retest_native | L3M | +17650 (144 tr) | -1486 (88 tr) | -5215 |  |
| Lad0c27eb | dol_500 | momentum_er.trend | L6M | +40111 (207 tr) | +33589 (148 tr) | +8786 |  |
| Lad0c27eb | dol_500 | momentum_er.trend | L3M | +31609 (98 tr) | +24712 (73 tr) | +7868 |  |
| Lac8d37cb | time_m_10 | xmarket_ym.follow | L6M | +17842 (307 tr) | +22308 (206 tr) | +8381 |  |
| Lac8d37cb | time_m_10 | xmarket_ym.follow | L3M | -20395 (128 tr) | -20231 (89 tr) | +9310 |  |
| L42449cac | entropy_B200 | levels_fibr_pd.false_break_native | L6M | +16057 (774 tr) | +34152 (453 tr) | -1485 |  |
| L42449cac | entropy_B200 | levels_fibr_pd.false_break_native | L3M | +3018 (300 tr) | +18485 (188 tr) | -2343 |  |
| Lc517931d | frenko_40 | book_ofi.follow_sm | L6M | +49990 (598 tr) | +12888 (333 tr) | +6927 |  |
| Lc517931d | frenko_40 | book_ofi.follow_sm | L3M | +5385 (275 tr) | +2855 (158 tr) | +990 |  |
| Ld8d9f7cd | entropy_B200 | levels_fibr_pd.false_break | L6M | +16057 (774 tr) | +34152 (453 tr) | -1485 |  |
| Ld8d9f7cd | entropy_B200 | levels_fibr_pd.false_break | L3M | +3018 (300 tr) | +18485 (188 tr) | -2343 |  |
| Lfa46118f | pnf_5 | levels_sdx3.break | L6M | -1533 (354 tr) | +15086 (222 tr) | -7236 |  |
| Lfa46118f | pnf_5 | levels_sdx3.break | L3M | +5394 (139 tr) | -4985 (91 tr) | -4368 |  |

### All sets (detail)
| cell | variant | window | d ulcer (x1 / x1.75) | d worst wk | d mean $/wk (x1 / x1.75) | d max DD | RISK-MATCHED c: d ulcer / d worst / d mean | new-book trades | R/trade | R/wk | corr daily w/ K7 / P7 / M7 | flag vs JL3 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | RK7 | L3M | +2177 / +3810 | -7880 | +1928 / +3374 | -5741 | c=1.00: +2177 / -7880 / +1928 | 65 | +0.210 | +1.048 | +0.08 / +0.17 / +0.29 | AMBER |
|  | RK7 | L6M | +1602 / +2803 | -7880 | -480 / -840 | -5741 | c=1.00: +1602 / -7880 / -480 | 155 | -0.136 | -0.783 | +0.04 / +0.11 / +0.12 | AMBER |
|  | RH7 | L3M | -590 / -1033 | +3909 | +995 / +1742 | +2671 | c=1.00: -590 / +3909 / +995 | 137 | +0.123 | +1.293 | +0.29 / +0.22 / +0.37 | ok |
|  | RH7 | L6M | -222 / -389 | +319 | +753 / +1319 | +2671 | c=1.00: -222 / +319 / +753 | 285 | +0.081 | +0.855 | +0.24 / +0.13 / +0.22 | ok |
|  | RH7 | Y2023 | -3850 / -6737 | -952 | +1014 / +1775 | +2193 | c=1.00: -3850 / -952 / +1014 | 373 | +0.098 | +0.934 | +0.39 / +0.02 / +0.32 | ok |
|  | RH7 | Y2024 | -4689 / -8205 | -1570 | +775 / +1357 | -46 | c=1.00: -4689 / -1570 / +775 | 563 | +0.051 | +0.545 | +0.35 / +0.15 / +0.39 | ok |
|  | RH7 | Y2025 | -5507 / -9637 | +2507 | +1075 / +1881 | +11862 | c=1.00: -5507 / +2507 / +1075 | 580 | +0.103 | +1.127 | +0.09 / +0.05 / +0.16 | ok |
|  | CT105m | L3M | +342 / +599 | -117 | -662 / -1158 | -900 | c=1.00: +342 / -117 / -662 | 0 | +nan | +0.000 | n/a / n/a / n/a | ok |
|  | CT105m | L6M | +216 / +378 | -117 | -517 / -905 | -900 | c=1.00: +216 / -117 / -517 | 139 | -0.015 | -0.075 | -0.16 / +0.04 / -0.04 | ok |
|  | CT105p | L3M | +1153 / +2018 | -6627 | +932 / +1631 | -5505 | c=1.00: +1153 / -6627 / +932 | 119 | +0.161 | +1.475 | +0.09 / +0.02 / +0.21 | AMBER |
|  | CT105p | L6M | +756 / +1323 | -6627 | -446 / -781 | -5505 | c=1.00: +756 / -6627 / -446 | 233 | -0.002 | -0.020 | +0.00 / +0.03 / -0.04 | AMBER |
|  | CT14m | L3M | -543 / -951 | +2164 | +129 / +225 | +1196 | c=1.00: -543 / +2164 / +129 | 115 | +0.056 | +0.493 | +0.24 / +0.15 / +0.27 | ok |
|  | CT14m | L6M | -391 / -685 | +2164 | +1222 / +2139 | +1196 | c=1.00: -391 / +2164 / +1222 | 273 | +0.122 | +1.233 | +0.20 / +0.10 / +0.10 | ok |
|  | CT14p | L3M | +1791 / +3135 | -4628 | -447 / -783 | -6052 | c=1.00: +1791 / -4628 / -447 | 125 | +0.045 | +0.437 | -0.11 / -0.19 / +0.03 | AMBER |
|  | CT14p | L6M | +1105 / +1934 | -4628 | -311 / -544 | -6052 | c=1.00: +1105 / -4628 / -311 | 263 | +0.028 | +0.270 | -0.01 / -0.04 / +0.04 | AMBER |
|  | CT21m | L3M | -842 / -1473 | +3133 | +71 / +124 | +4315 | c=1.00: -842 / +3133 / +71 | 110 | +0.067 | +0.570 | +0.05 / -0.04 / -0.20 | ok |
|  | CT21m | L6M | -114 / -199 | -1676 | -214 / -374 | +4315 | c=1.00: -114 / -1676 / -214 | 254 | +0.014 | +0.136 | +0.09 / +0.04 / -0.01 | ok |
|  | CT21p | L3M | +861 / +1507 | -4014 | +120 / +211 | -3967 | c=1.00: +861 / -4014 / +120 | 126 | +0.099 | +0.964 | +0.08 / -0.05 / +0.03 | ok |
|  | CT21p | L6M | +544 / +953 | -4014 | +278 / +487 | -3967 | c=1.00: +544 / -4014 / +278 | 269 | +0.071 | +0.709 | +0.01 / -0.04 / +0.10 | ok |
|  | CT28m | L3M | +417 / +729 | +1223 | +418 / +732 | -2141 | c=1.00: +417 / +1223 / +418 | 97 | +0.100 | +0.743 | +0.13 / +0.09 / +0.18 | ok |
|  | CT28m | L6M | +417 / +729 | -1241 | +167 / +293 | -2141 | c=1.00: +417 / -1241 / +167 | 232 | +0.043 | +0.372 | +0.07 / +0.09 / -0.09 | ok |
|  | CT28p | L3M | -621 / -1087 | +2568 | +689 / +1205 | +3944 | c=1.00: -621 / +2568 / +689 | 131 | +0.103 | +1.034 | +0.28 / -0.06 / +0.11 | ok |
|  | CT28p | L6M | -313 / -547 | +2568 | +798 / +1397 | +3944 | c=1.00: -313 / +2568 / +798 | 255 | +0.110 | +1.034 | +0.19 / -0.03 / +0.14 | ok |
|  | CT35m | L3M | +1113 / +1948 | +1202 | -962 / -1684 | -3501 | c=1.00: +1113 / +1202 / -962 | 81 | -0.083 | -0.516 | +0.20 / +0.29 / +0.06 | ok |
|  | CT35m | L6M | +684 / +1197 | +1202 | -326 / -571 | -3501 | c=1.00: +684 / +1202 / -326 | 227 | -0.022 | -0.183 | +0.20 / +0.14 / -0.01 | ok |
|  | CT35p | L3M | +1807 / +3163 | -4973 | -497 / -870 | -4522 | c=1.00: +1807 / -4973 / -497 | 115 | +0.012 | +0.110 | +0.22 / +0.06 / +0.39 | AMBER |
|  | CT35p | L6M | +1081 / +1892 | -4973 | -147 / -257 | -4522 | c=1.00: +1081 / -4973 / -147 | 260 | +0.020 | +0.196 | +0.25 / +0.06 / +0.25 | ok |
|  | CT42m | L3M | +462 / +809 | -6938 | +11 / +20 | -615 | c=1.00: +462 / -6938 / +11 | 76 | +0.148 | +0.868 | +0.20 / +0.15 / -0.08 | ok |
|  | CT42m | L6M | +354 / +619 | -6938 | +178 / +312 | -615 | c=1.00: +354 / -6938 / +178 | 219 | +0.060 | +0.490 | +0.17 / +0.08 / -0.00 | ok |
|  | CT42p | L3M | -250 / -438 | -487 | -787 / -1378 | +2204 | c=1.00: -250 / -487 / -787 | 125 | -0.035 | -0.334 | +0.14 / -0.08 / +0.06 | ok |
|  | CT42p | L6M | +63 / +110 | -487 | -966 / -1691 | +2204 | c=1.00: +63 / -487 / -966 | 256 | -0.067 | -0.632 | +0.12 / -0.03 / +0.03 | ok |
|  | CT49m | L3M | +939 / +1643 | -6327 | -695 / -1217 | -2186 | c=1.00: +939 / -6327 / -695 | 72 | +0.037 | +0.205 | -0.09 / -0.33 / -0.09 | ok |
|  | CT49m | L6M | +573 / +1003 | -6327 | -955 / -1671 | -2186 | c=1.00: +573 / -6327 / -955 | 203 | -0.043 | -0.320 | +0.05 / -0.28 / -0.13 | ok |
|  | CT49p | L3M | +1235 / +2161 | -2852 | +1318 / +2306 | -5376 | c=1.00: +1235 / -2852 / +1318 | 126 | +0.144 | +1.400 | -0.22 / +0.07 / -0.29 | AMBER |
|  | CT49p | L6M | +764 / +1337 | -2852 | +1139 / +1994 | -5376 | c=1.00: +764 / -2852 / +1139 | 258 | +0.124 | +1.183 | -0.14 / +0.01 / -0.27 | AMBER |
|  | CT56m | L3M | +1020 / +1786 | -4668 | -1128 / -1974 | -3793 | c=1.00: +1020 / -4668 / -1128 | 64 | -0.046 | -0.229 | -0.06 / +0.03 / +0.15 | ok |
|  | CT56m | L6M | +929 / +1625 | -4668 | -1032 / -1807 | -3793 | c=1.00: +929 / -4668 / -1032 | 202 | -0.072 | -0.540 | -0.03 / -0.07 / +0.01 | ok |
|  | CT56p | L3M | -455 / -796 | +3699 | -690 / -1208 | +3016 | c=1.00: -455 / +3699 / -690 | 127 | -0.004 | -0.038 | -0.05 / -0.16 / -0.17 | ok |
|  | CT56p | L6M | -6 / -10 | +2249 | -597 / -1045 | +3016 | c=1.00: -6 / +2249 / -597 | 271 | -0.010 | -0.097 | -0.03 / -0.08 / -0.03 | ok |
|  | CT63m | L3M | -55 / -96 | +1078 | +698 / +1221 | +1271 | c=1.00: -55 / +1078 / +698 | 52 | +0.250 | +0.999 | +0.07 / +0.10 / +0.12 | ok |
|  | CT63m | L6M | +30 / +53 | +1078 | -153 / -268 | +1271 | c=1.00: +30 / +1078 / -153 | 195 | +0.011 | +0.077 | +0.03 / -0.05 / -0.08 | ok |
|  | CT63p | L3M | +1527 / +2672 | -666 | -655 / -1146 | -5915 | c=1.00: +1527 / -666 / -655 | 130 | +0.039 | +0.385 | +0.13 / -0.00 / +0.23 | AMBER |
|  | CT63p | L6M | +923 / +1616 | -666 | +95 / +166 | -5915 | c=1.00: +923 / -666 / +95 | 252 | +0.050 | +0.463 | +0.06 / +0.02 / +0.00 | AMBER |
|  | CT70m | L3M | +362 / +633 | +2714 | -1147 / -2008 | -830 | c=1.00: +362 / +2714 / -1147 | 42 | -0.143 | -0.462 | -0.02 / +0.16 / -0.12 | ok |
|  | CT70m | L6M | +235 / +411 | +2714 | -102 / -178 | -830 | c=1.00: +235 / +2714 / -102 | 181 | +0.041 | +0.273 | -0.08 / +0.10 / -0.07 | ok |
|  | CT70p | L3M | +989 / +1731 | -3816 | -2352 / -4116 | -3795 | c=1.00: +989 / -3816 / -2352 | 134 | -0.058 | -0.593 | +0.13 / -0.09 / +0.00 | ok |
|  | CT70p | L6M | +754 / +1319 | -3816 | -1018 / -1781 | -3795 | c=1.00: +754 / -3816 / -1018 | 270 | -0.019 | -0.188 | +0.01 / -0.04 / +0.03 | ok |
|  | CT77m | L3M | +334 / +584 | -117 | -556 / -973 | -900 | c=1.00: +334 / -117 / -556 | 40 | -0.016 | -0.048 | -0.20 / -0.08 / -0.19 | ok |
|  | CT77m | L6M | +201 / +352 | -117 | -862 / -1508 | -900 | c=1.00: +201 / -117 / -862 | 181 | -0.079 | -0.530 | -0.03 / -0.03 / +0.07 | ok |
|  | CT77p | L3M | +136 / +238 | -1412 | +246 / +430 | -2255 | c=1.00: +136 / -1412 / +246 | 135 | +0.050 | +0.520 | +0.08 / -0.08 / +0.07 | ok |
|  | CT77p | L6M | +70 / +123 | -1412 | +117 / +205 | -2255 | c=1.00: +70 / -1412 / +117 | 254 | +0.026 | +0.246 | -0.01 / -0.05 / -0.01 | ok |
|  | CT7m | L3M | +547 / +958 | -2367 | -1270 / -2222 | -2691 | c=1.00: +547 / -2367 / -1270 | 124 | +0.009 | +0.081 | -0.24 / -0.31 / -0.29 | ok |
|  | CT7m | L6M | +482 / +843 | -2367 | -791 / -1384 | -2691 | c=1.00: +482 / -2367 / -791 | 259 | -0.020 | -0.194 | -0.15 / -0.21 / -0.15 | ok |
|  | CT7p | L3M | +1157 / +2024 | -5003 | -309 / -541 | -3907 | c=1.00: +1157 / -5003 / -309 | 131 | +0.021 | +0.213 | -0.08 / +0.11 / -0.17 | ok |
|  | CT7p | L6M | +660 / +1155 | -5003 | -292 / -512 | -3907 | c=1.00: +660 / -5003 / -292 | 271 | +0.004 | +0.036 | -0.10 / +0.04 / -0.14 | ok |
|  | CT84m | L3M | +362 / +634 | -117 | -674 / -1179 | -900 | c=1.00: +362 / -117 / -674 | 22 | -0.018 | -0.031 | -0.06 / +0.10 / -0.01 | ok |
|  | CT84m | L6M | +308 / +539 | -117 | -994 / -1740 | -900 | c=1.00: +308 / -117 / -994 | 164 | -0.090 | -0.546 | -0.12 / +0.04 / -0.11 | ok |
|  | CT84p | L3M | +655 / +1146 | -1477 | -1084 / -1897 | -2386 | c=1.00: +655 / -1477 / -1084 | 126 | -0.120 | -1.160 | +0.03 / -0.03 / -0.16 | ok |
|  | CT84p | L6M | +531 / +929 | -1477 | -569 / -996 | -2386 | c=1.00: +531 / -1477 / -569 | 250 | -0.055 | -0.513 | +0.11 / -0.00 / +0.10 | ok |
|  | CT91m | L3M | +368 / +643 | -117 | -680 / -1190 | -900 | c=1.00: +368 / -117 / -680 | 13 | -0.015 | -0.015 | +0.16 / +0.37 / +0.19 | ok |
|  | CT91m | L6M | +374 / +655 | -117 | -172 / -301 | -900 | c=1.00: +374 / -117 / -172 | 142 | +0.014 | +0.076 | +0.02 / +0.10 / -0.08 | ok |
|  | CT91p | L3M | +3155 / +5521 | -4218 | -851 / -1489 | -13072 | c=1.00: +3155 / -4218 / -851 | 131 | +0.030 | +0.304 | -0.15 / -0.07 / +0.16 | RED |
|  | CT91p | L6M | +2055 / +3597 | -4218 | -1391 / -2434 | -13072 | c=1.00: +2055 / -4218 / -1391 | 241 | -0.073 | -0.654 | -0.06 / -0.02 / +0.17 | RED |
|  | CT98m | L3M | +499 / +874 | -117 | -925 / -1619 | -900 | c=1.00: +499 / -117 / -925 | 9 | -0.317 | -0.219 | +0.02 / +0.02 / +0.01 | ok |
|  | CT98m | L6M | +267 / +467 | -117 | +749 / +1311 | -900 | c=1.00: +267 / -117 / +749 | 140 | +0.208 | +1.080 | -0.04 / +0.04 / -0.01 | ok |
|  | CT98p | L3M | -960 / -1680 | +2127 | +1306 / +2286 | +3969 | c=1.00: -960 / +2127 / +1306 | 117 | +0.167 | +1.500 | -0.02 / -0.17 / +0.14 | ok |
|  | CT98p | L6M | -574 / -1004 | +2127 | +1010 / +1767 | +3969 | c=1.00: -574 / +2127 / +1010 | 225 | +0.128 | +1.066 | +0.11 / -0.10 / +0.12 | ok |
|  | RK7 | L3M | -448 / -784 | +2462 | +2609 / +4565 | +2114 | c=1.00: -448 / +2462 / +2609 | 141 | +0.129 | +1.394 | +0.26 / +0.22 / +0.37 | ok |
|  | RK7 | L6M | -75 / -130 | +620 | +1755 / +3071 | +1857 | c=1.00: -75 / +620 / +1755 | 290 | +0.081 | +0.866 | +0.23 / +0.13 / +0.22 | ok |
|  | RK7 | Y2023 | -3880 / -6789 | -4164 | +458 / +801 | -4549 | c=1.00: -3880 / -4164 / +458 | 373 | +0.098 | +0.934 | +0.39 / +0.02 / +0.32 | ok |
|  | RK7 | Y2024 | -4140 / -7245 | -2358 | +620 / +1085 | +2638 | c=1.00: -4140 / -2358 / +620 | 565 | +0.054 | +0.576 | +0.35 / +0.15 / +0.39 | ok |
|  | RK7 | Y2025 | -4190 / -7333 | +4205 | +515 / +901 | +8286 | c=1.00: -4190 / +4205 / +515 | 586 | +0.102 | +1.128 | +0.09 / +0.06 / +0.17 | ok |
|  | CT105m | L3M | +2292 / +4010 | -4002 | +73 / +128 | -7596 | c=1.00: +2292 / -4002 / +73 | 0 | +nan | +0.000 | n/a / n/a / n/a | AMBER |
|  | CT105m | L6M | +1464 / +2562 | -4002 | +20 / +35 | -7596 | c=1.00: +1464 / -4002 / +20 | 139 | -0.015 | -0.075 | -0.16 / +0.04 / -0.04 | AMBER |
|  | CT105p | L3M | +1585 / +2773 | -5783 | +1902 / +3329 | -7423 | c=1.00: +1585 / -5783 / +1902 | 119 | +0.161 | +1.475 | +0.09 / +0.02 / +0.21 | AMBER |
|  | CT105p | L6M | +1052 / +1841 | -5783 | +389 / +681 | -7423 | c=1.00: +1052 / -5783 / +389 | 239 | -0.000 | -0.003 | -0.01 / +0.03 / -0.02 | AMBER |
|  | CT14m | L3M | +1215 / +2126 | -805 | +937 / +1640 | -5372 | c=1.00: +1215 / -805 / +937 | 115 | +0.056 | +0.493 | +0.24 / +0.15 / +0.27 | AMBER |
|  | CT14m | L6M | +703 / +1230 | -805 | +1843 / +3226 | -5372 | c=1.00: +703 / -805 / +1843 | 273 | +0.122 | +1.233 | +0.20 / +0.10 / +0.10 | AMBER |
|  | CT14p | L3M | +2219 / +3883 | -3785 | +1405 / +2459 | -7298 | c=1.00: +2219 / -3785 / +1405 | 126 | +0.045 | +0.432 | -0.11 / -0.19 / +0.03 | AMBER |
|  | CT14p | L6M | +1388 / +2430 | -3785 | +938 / +1641 | -7298 | c=1.00: +1388 / -3785 / +938 | 265 | +0.023 | +0.230 | +0.00 / -0.04 / +0.04 | AMBER |
|  | CT21m | L3M | -384 / -673 | -317 | +1408 / +2464 | +2747 | c=1.00: -384 / -317 / +1408 | 111 | +0.058 | +0.496 | +0.07 / -0.04 / -0.17 | ok |
|  | CT21m | L6M | +186 / +325 | -1375 | +644 / +1127 | +2052 | c=1.00: +186 / -1375 / +644 | 256 | +0.007 | +0.063 | +0.09 / +0.04 / +0.00 | ok |
|  | CT21p | L3M | +1274 / +2229 | -4088 | +1604 / +2807 | -5442 | c=1.00: +1274 / -4088 / +1604 | 130 | +0.093 | +0.927 | +0.08 / -0.05 / +0.03 | AMBER |
|  | CT21p | L6M | +847 / +1483 | -4088 | +1366 / +2391 | -5442 | c=1.00: +847 / -4088 / +1366 | 278 | +0.068 | +0.701 | +0.00 / -0.04 / +0.11 | AMBER |
|  | CT28m | L3M | +1383 / +2421 | -317 | +1091 / +1910 | -5203 | c=1.00: +1383 / -317 / +1091 | 100 | +0.085 | +0.654 | +0.16 / +0.10 / +0.18 | AMBER |
|  | CT28m | L6M | +1016 / +1778 | -941 | +768 / +1344 | -5203 | c=1.00: +1016 / -941 / +768 | 235 | +0.038 | +0.329 | +0.09 / +0.09 / -0.10 | AMBER |
|  | CT28p | L3M | -311 / -545 | +583 | +1831 / +3204 | +2850 | c=1.00: -311 / +583 / +1831 | 135 | +0.093 | +0.963 | +0.30 / -0.05 / +0.10 | ok |
|  | CT28p | L6M | -39 / -69 | +583 | +1630 / +2853 | +2850 | c=1.00: -39 / +583 / +1630 | 259 | +0.104 | +1.000 | +0.20 / -0.03 / +0.13 | ok |
|  | CT35m | L3M | +2555 / +4472 | -3405 | -186 / -325 | -8803 | c=1.00: +2555 / -3405 / -186 | 83 | -0.114 | -0.730 | +0.21 / +0.32 / +0.09 | AMBER |
|  | CT35m | L6M | +1618 / +2832 | -3405 | +251 / +439 | -8803 | c=1.00: +1618 / -3405 / +251 | 231 | -0.039 | -0.334 | +0.21 / +0.16 / +0.01 | AMBER |
|  | CT35p | L3M | +2771 / +4850 | -4728 | +685 / +1200 | -8067 | c=1.00: +2771 / -4728 / +685 | 118 | +0.022 | +0.200 | +0.19 / +0.06 / +0.39 | AMBER |
|  | CT35p | L6M | +1699 / +2973 | -4728 | +745 / +1304 | -8067 | c=1.00: +1699 / -4728 / +745 | 263 | +0.025 | +0.239 | +0.23 / +0.06 / +0.25 | AMBER |
|  | CT42m | L3M | +968 / +1694 | -5913 | +1473 / +2578 | -1474 | c=1.00: +968 / -5913 / +1473 | 76 | +0.148 | +0.868 | +0.20 / +0.15 / -0.08 | ok |
|  | CT42m | L6M | +699 / +1223 | -5913 | +1097 / +1920 | -1474 | c=1.00: +699 / -5913 / +1097 | 220 | +0.065 | +0.527 | +0.17 / +0.08 / -0.01 | ok |
|  | CT42p | L3M | +80 / +140 | -2069 | +498 / +872 | +790 | c=1.00: +80 / -2069 / +498 | 129 | -0.031 | -0.311 | +0.13 / -0.07 / +0.06 | ok |
|  | CT42p | L6M | +283 / +495 | -2069 | -55 / -96 | +790 | c=1.00: +283 / -2069 / -55 | 260 | -0.064 | -0.621 | +0.11 / -0.02 / +0.03 | ok |
|  | CT49m | L3M | +1470 / +2572 | -5484 | +381 / +666 | -2742 | c=1.00: +1470 / -5484 / +381 | 73 | +0.024 | +0.134 | -0.07 / -0.33 / -0.06 | ok |
|  | CT49m | L6M | +935 / +1636 | -5484 | -217 / -380 | -2742 | c=1.00: +935 / -5484 / -217 | 204 | -0.047 | -0.354 | +0.06 / -0.28 / -0.12 | ok |
|  | CT49p | L3M | +1985 / +3474 | -4135 | +2424 / +4242 | -8058 | c=1.00: +1985 / -4135 / +2424 | 126 | +0.144 | +1.400 | -0.22 / +0.07 / -0.29 | AMBER |
|  | CT49p | L6M | +1254 / +2195 | -4135 | +2053 / +3592 | -8058 | c=1.00: +1254 / -4135 / +2053 | 259 | +0.127 | +1.220 | -0.13 / +0.01 / -0.27 | AMBER |
|  | CT56m | L3M | +2382 / +4169 | -3825 | -215 / -377 | -8112 | c=1.00: +2382 / -3825 / -215 | 64 | -0.046 | -0.229 | -0.06 / +0.03 / +0.15 | AMBER |
|  | CT56m | L6M | +1791 / +3134 | -3825 | -305 / -534 | -8112 | c=1.00: +1791 / -3825 / -305 | 202 | -0.072 | -0.540 | -0.03 / -0.07 / +0.01 | AMBER |
|  | CT56p | L3M | -278 / -487 | +248 | +627 / +1097 | +2460 | c=1.00: -278 / +248 / +627 | 129 | -0.019 | -0.191 | -0.07 / -0.15 / -0.19 | ok |
|  | CT56p | L6M | +152 / +265 | +248 | +391 / +684 | +1897 | c=1.00: +152 / +248 / +391 | 275 | -0.021 | -0.215 | -0.03 / -0.08 / -0.05 | ok |
|  | CT63m | L3M | +1442 / +2524 | -2806 | +1477 / +2585 | -3034 | c=1.00: +1442 / -2806 / +1477 | 52 | +0.250 | +0.999 | +0.07 / +0.10 / +0.12 | ok |
|  | CT63m | L6M | +961 / +1682 | -2806 | +450 / +787 | -3034 | c=1.00: +961 / -2806 / +450 | 196 | +0.006 | +0.041 | +0.03 / -0.05 / -0.08 | ok |
|  | CT63p | L3M | +1492 / +2611 | -3029 | +1063 / +1859 | -5535 | c=1.00: +1492 / -3029 / +1063 | 132 | +0.042 | +0.428 | +0.11 / +0.00 / +0.23 | AMBER |
|  | CT63p | L6M | +978 / +1712 | -3029 | +1051 / +1840 | -5535 | c=1.00: +978 / -3029 / +1051 | 257 | +0.044 | +0.416 | +0.05 / +0.02 / +0.01 | AMBER |
|  | CT70m | L3M | +1255 / +2196 | -317 | -165 / -289 | -3776 | c=1.00: +1255 / -317 / -165 | 42 | -0.143 | -0.462 | -0.02 / +0.16 / -0.12 | ok |
|  | CT70m | L6M | +801 / +1402 | -317 | +600 / +1050 | -3776 | c=1.00: +801 / -317 / +600 | 182 | +0.042 | +0.283 | -0.08 / +0.10 / -0.07 | ok |
|  | CT70p | L3M | +3033 / +5307 | -6815 | -910 / -1593 | -11036 | c=1.00: +3033 / -6815 / -910 | 135 | -0.049 | -0.510 | +0.14 / -0.09 / +0.02 | RED |
|  | CT70p | L6M | +2050 / +3588 | -6815 | -98 / -172 | -11036 | c=1.00: +2050 / -6815 / -98 | 273 | -0.018 | -0.182 | +0.01 / -0.04 / +0.04 | RED |
|  | CT77m | L3M | +2542 / +4449 | -4002 | +47 / +82 | -8359 | c=1.00: +2542 / -4002 / +47 | 40 | -0.016 | -0.048 | -0.20 / -0.08 / -0.19 | AMBER |
|  | CT77m | L6M | +1604 / +2806 | -4002 | -372 / -652 | -8359 | c=1.00: +1604 / -4002 / -372 | 183 | -0.084 | -0.570 | -0.04 / -0.02 / +0.06 | AMBER |
|  | CT77p | L3M | +1382 / +2418 | -3191 | +1387 / +2427 | -6903 | c=1.00: +1382 / -3191 / +1387 | 136 | +0.051 | +0.530 | +0.11 / -0.09 / +0.07 | AMBER |
|  | CT77p | L6M | +898 / +1571 | -3191 | +848 / +1484 | -6903 | c=1.00: +898 / -3191 / +848 | 258 | +0.027 | +0.262 | +0.01 / -0.06 / -0.01 | AMBER |
|  | CT7m | L3M | +1692 / +2961 | -2719 | -1180 / -2065 | -6833 | c=1.00: +1692 / -2719 / -1180 | 125 | +0.000 | +0.004 | -0.24 / -0.30 / -0.29 | AMBER |
|  | CT7m | L6M | +1289 / +2255 | -2719 | -624 / -1092 | -6833 | c=1.00: +1289 / -2719 / -624 | 262 | -0.024 | -0.231 | -0.16 / -0.20 / -0.16 | AMBER |
|  | CT7p | L3M | +2210 / +3867 | -4853 | +413 / +723 | -7547 | c=1.00: +2210 / -4853 / +413 | 134 | -0.001 | -0.014 | -0.05 / +0.14 / -0.14 | AMBER |
|  | CT7p | L6M | +1331 / +2330 | -4853 | +374 / +654 | -7547 | c=1.00: +1331 / -4853 / +374 | 274 | -0.007 | -0.073 | -0.09 / +0.06 / -0.13 | AMBER |
|  | CT84m | L3M | +2285 / +3998 | -4002 | +93 / +162 | -7596 | c=1.00: +2285 / -4002 / +93 | 22 | -0.018 | -0.031 | -0.06 / +0.10 / -0.01 | AMBER |
|  | CT84m | L6M | +1532 / +2681 | -4002 | -439 / -768 | -7596 | c=1.00: +1532 / -4002 / -439 | 165 | -0.083 | -0.509 | -0.13 / +0.04 / -0.11 | AMBER |
|  | CT84p | L3M | +1680 / +2941 | -1828 | -747 / -1308 | -6528 | c=1.00: +1680 / -1828 / -747 | 128 | -0.115 | -1.132 | +0.03 / -0.03 / -0.16 | AMBER |
|  | CT84p | L6M | +1225 / +2144 | -1828 | -109 / -190 | -6528 | c=1.00: +1225 / -1828 / -109 | 253 | -0.049 | -0.462 | +0.11 / -0.00 / +0.09 | AMBER |
|  | CT91m | L3M | +2309 / +4041 | -4002 | +55 / +96 | -7596 | c=1.00: +2309 / -4002 / +55 | 13 | -0.015 | -0.015 | +0.16 / +0.37 / +0.19 | AMBER |
|  | CT91m | L6M | +1588 / +2779 | -4002 | +338 / +591 | -7596 | c=1.00: +1588 / -4002 / +338 | 143 | +0.011 | +0.060 | +0.03 / +0.10 / -0.07 | AMBER |
|  | CT91p | L3M | +3591 / +6284 | -4150 | +472 / +826 | -13680 | c=1.00: +3591 / -4150 / +472 | 132 | +0.023 | +0.234 | -0.14 / -0.07 / +0.18 | RED |
|  | CT91p | L6M | +2418 / +4232 | -4150 | -463 / -810 | -13680 | c=1.00: +2418 / -4150 / -463 | 250 | -0.070 | -0.652 | -0.05 / -0.02 / +0.19 | RED |
|  | CT98m | L3M | +2374 / +4154 | -4002 | -138 / -241 | -7596 | c=1.00: +2374 / -4002 / -138 | 9 | -0.317 | -0.219 | +0.02 / +0.02 / +0.01 | AMBER |
|  | CT98m | L6M | +1443 / +2525 | -4002 | +1511 / +2645 | -7596 | c=1.00: +1443 / -4002 / +1511 | 140 | +0.208 | +1.080 | -0.04 / +0.04 / -0.01 | AMBER |
|  | CT98p | L3M | -282 / -494 | -13 | +1850 / +3238 | +1866 | c=1.00: -282 / -13 / +1850 | 118 | +0.168 | +1.528 | -0.02 / -0.17 / +0.14 | ok |
|  | CT98p | L6M | -143 / -250 | -13 | +1554 / +2719 | +1866 | c=1.00: -143 / -13 / +1554 | 230 | +0.127 | +1.079 | +0.10 / -0.11 / +0.13 | ok |
|  | RK7LO | L3M | +254 / +445 | -1959 | +1639 / +2869 | -1162 | c=1.00: +254 / -1959 / +1639 | 83 | +0.110 | +0.703 | +0.32 / +0.14 / +0.15 | ok |
|  | RK7LO | L6M | +387 / +677 | -1959 | +594 / +1040 | -1162 | c=1.00: +387 / -1959 / +594 | 158 | +0.007 | +0.041 | +0.22 / +0.10 / +0.16 | ok |
|  | RK7SO | L3M | +988 / +1729 | -725 | +1253 / +2192 | -1929 | c=1.00: +988 / -725 / +1253 | 73 | +0.119 | +0.666 | +0.14 / +0.15 / +0.33 | ok |
|  | RK7SO | L6M | +721 / +1261 | -725 | +1227 / +2148 | -1929 | c=1.00: +721 / -725 / +1227 | 156 | +0.127 | +0.737 | +0.12 / +0.07 / +0.13 | ok |
|  | RM7 | L3M | -736 / -1288 | +3831 | +505 / +884 | +3039 | c=1.00: -736 / +3831 / +505 | 138 | +0.127 | +1.353 | +0.30 / +0.20 / +0.36 | ok |
|  | RM7 | L6M | -457 / -799 | +2660 | +562 / +984 | +3039 | c=1.00: -457 / +2660 / +562 | 287 | +0.080 | +0.846 | +0.25 / +0.11 / +0.22 | ok |
|  | RM7 | Y2023 | -5346 / -9355 | +821 | +1327 / +2322 | +5811 | c=1.00: -5346 / +821 / +1327 | 373 | +0.098 | +0.934 | +0.39 / +0.02 / +0.32 | ok |
|  | RM7 | Y2024 | -2749 / -4811 | +1106 | +93 / +163 | +5511 | c=1.00: -2749 / +1106 / +93 | 566 | +0.052 | +0.557 | +0.35 / +0.15 / +0.39 | ok |
|  | RM7 | Y2025 | -5375 / -9407 | +2754 | +729 / +1276 | +7389 | c=1.00: -5375 / +2754 / +729 | 589 | +0.094 | +1.047 | +0.09 / +0.05 / +0.17 | ok |
|  | CT105m | L3M | -11 / -20 | +873 | -1043 / -1826 | +588 | c=1.00: -11 / +873 / -1043 | 0 | +nan | +0.000 | n/a / n/a / n/a | ok |
|  | CT105m | L6M | -109 / -190 | +873 | -613 / -1073 | +588 | c=1.00: -109 / +873 / -613 | 140 | -0.016 | -0.082 | -0.17 / +0.05 / -0.04 | ok |
|  | CT105p | L3M | +1623 / +2841 | -8087 | +270 / +472 | -7045 | c=1.00: +1623 / -8087 / +270 | 120 | +0.152 | +1.399 | +0.10 / +0.02 / +0.23 | AMBER |
|  | CT105p | L6M | +898 / +1572 | -8087 | -662 / -1158 | -7045 | c=1.00: +898 / -8087 / -662 | 235 | -0.006 | -0.053 | +0.01 / +0.03 / -0.03 | AMBER |
|  | CT14m | L3M | -675 / -1181 | +2085 | -339 / -594 | +1564 | c=1.00: -675 / +2085 / -339 | 114 | +0.065 | +0.569 | +0.24 / +0.12 / +0.26 | ok |
|  | CT14m | L6M | -603 / -1055 | +2085 | +1131 / +1979 | +1564 | c=1.00: -603 / +2085 / +1131 | 273 | +0.129 | +1.306 | +0.21 / +0.08 / +0.10 | ok |
|  | CT14p | L3M | +1527 / +2672 | -5657 | -968 / -1694 | -5704 | c=1.00: +1527 / -5657 / -968 | 125 | +0.045 | +0.437 | -0.11 / -0.19 / +0.03 | AMBER |
|  | CT14p | L6M | +808 / +1413 | -5657 | -422 / -739 | -5704 | c=1.00: +808 / -5657 / -422 | 263 | +0.028 | +0.273 | -0.02 / -0.03 / +0.04 | AMBER |
|  | CT21m | L3M | -500 / -876 | +873 | -475 / -832 | +3090 | c=1.00: -500 / +873 / -475 | 111 | +0.058 | +0.496 | +0.07 / -0.04 / -0.17 | ok |
|  | CT21m | L6M | -152 / -266 | +665 | -348 / -609 | +3090 | c=1.00: -152 / +665 / -348 | 257 | +0.006 | +0.061 | +0.09 / +0.04 / -0.00 | ok |
|  | CT21p | L3M | +901 / +1578 | -5267 | -386 / -675 | -4517 | c=1.00: +901 / -5267 / -386 | 127 | +0.097 | +0.950 | +0.08 / -0.05 / +0.03 | ok |
|  | CT21p | L6M | +423 / +740 | -5267 | +121 / +212 | -4517 | c=1.00: +423 / -5267 / +121 | 272 | +0.070 | +0.703 | +0.01 / -0.04 / +0.10 | ok |
|  | CT28m | L3M | +521 / +912 | +451 | -243 / -425 | -2466 | c=1.00: +521 / +451 / -243 | 96 | +0.090 | +0.667 | +0.16 / +0.09 / +0.18 | ok |
|  | CT28m | L6M | +292 / +511 | +451 | +41 / +71 | -2466 | c=1.00: +292 / +451 / +41 | 231 | +0.041 | +0.352 | +0.08 / +0.09 / -0.09 | ok |
|  | CT28p | L3M | -480 / -841 | +1951 | +38 / +66 | +3774 | c=1.00: -480 / +1951 / +38 | 133 | +0.095 | +0.968 | +0.29 / -0.05 / +0.13 | ok |
|  | CT28p | L6M | -437 / -765 | +1951 | +708 / +1239 | +3774 | c=1.00: -437 / +1951 / +708 | 258 | +0.107 | +1.022 | +0.20 / -0.03 / +0.15 | ok |
|  | CT35m | L3M | +1067 / +1868 | +681 | -1608 / -2814 | -3576 | c=1.00: +1067 / +681 / -1608 | 84 | -0.077 | -0.500 | +0.23 / +0.27 / +0.05 | ok |
|  | CT35m | L6M | +519 / +908 | +681 | -580 / -1016 | -3576 | c=1.00: +519 / +681 / -580 | 230 | -0.018 | -0.150 | +0.21 / +0.14 / -0.01 | ok |
|  | CT35p | L3M | +1727 / +3022 | -5906 | -1045 / -1830 | -4752 | c=1.00: +1727 / -5906 / -1045 | 116 | +0.013 | +0.116 | +0.22 / +0.06 / +0.39 | AMBER |
|  | CT35p | L6M | +926 / +1620 | -5906 | -251 / -439 | -4752 | c=1.00: +926 / -5906 / -251 | 260 | +0.024 | +0.233 | +0.24 / +0.06 / +0.26 | AMBER |
|  | CT42m | L3M | +350 / +612 | -7092 | -477 / -835 | +126 | c=1.00: +350 / -7092 / -477 | 76 | +0.148 | +0.868 | +0.20 / +0.15 / -0.08 | ok |
|  | CT42m | L6M | +132 / +231 | -7092 | +13 / +24 | +126 | c=1.00: +132 / -7092 / +13 | 220 | +0.065 | +0.527 | +0.17 / +0.08 / -0.01 | ok |
|  | CT42p | L3M | -100 / -175 | -2529 | -1501 / -2627 | +1734 | c=1.00: -100 / -2529 / -1501 | 126 | -0.036 | -0.345 | +0.15 / -0.10 / +0.08 | ok |
|  | CT42p | L6M | -33 / -58 | -2529 | -1211 / -2118 | +1734 | c=1.00: -33 / -2529 / -1211 | 257 | -0.067 | -0.637 | +0.13 / -0.04 / +0.04 | ok |
|  | CT49m | L3M | +864 / +1512 | -6662 | -1238 / -2166 | -1817 | c=1.00: +864 / -6662 / -1238 | 73 | +0.024 | +0.134 | -0.09 / -0.29 / -0.09 | ok |
|  | CT49m | L6M | +401 / +702 | -6662 | -1008 / -1764 | -1817 | c=1.00: +401 / -6662 / -1008 | 203 | -0.047 | -0.356 | +0.06 / -0.26 / -0.13 | ok |
|  | CT49p | L3M | +1612 / +2821 | -4781 | +530 / +928 | -6601 | c=1.00: +1612 / -4781 / +530 | 127 | +0.136 | +1.327 | -0.20 / +0.07 / -0.27 | AMBER |
|  | CT49p | L6M | +904 / +1582 | -4781 | +817 / +1429 | -6601 | c=1.00: +904 / -4781 / +817 | 260 | +0.115 | +1.111 | -0.13 / +0.01 / -0.25 | AMBER |
|  | CT56m | L3M | +985 / +1724 | -5697 | -1826 / -3195 | -3650 | c=1.00: +985 / -5697 / -1826 | 66 | -0.044 | -0.225 | -0.06 / +0.03 / +0.14 | ok |
|  | CT56m | L6M | +740 / +1295 | -5697 | -1280 / -2240 | -3650 | c=1.00: +740 / -5697 / -1280 | 203 | -0.067 | -0.503 | -0.04 / -0.07 / +0.01 | ok |
|  | CT56p | L3M | -568 / -994 | +1438 | -571 / -999 | +3384 | c=1.00: -568 / +1438 / -571 | 127 | -0.020 | -0.191 | -0.07 / -0.15 / -0.19 | ok |
|  | CT56p | L6M | -326 / -570 | +1438 | -342 / -598 | +3384 | c=1.00: -326 / +1438 / -342 | 272 | -0.016 | -0.158 | -0.04 / -0.09 / -0.05 | ok |
|  | CT63m | L3M | -80 / -141 | +873 | +135 / +236 | +1639 | c=1.00: -80 / +873 / +135 | 53 | +0.227 | +0.924 | +0.09 / +0.10 / +0.15 | ok |
|  | CT63m | L6M | -100 / -176 | +873 | -259 / -454 | +1639 | c=1.00: -100 / +873 / -259 | 194 | +0.006 | +0.041 | +0.04 / -0.05 / -0.07 | ok |
|  | CT63p | L3M | +895 / +1566 | +376 | -853 / -1492 | -4426 | c=1.00: +895 / +376 / -853 | 131 | +0.055 | +0.557 | +0.09 / -0.01 / +0.19 | ok |
|  | CT63p | L6M | +418 / +731 | +376 | -74 / -129 | -4426 | c=1.00: +418 / +376 / -74 | 251 | +0.051 | +0.472 | +0.05 / +0.02 / -0.03 | ok |
|  | CT70m | L3M | +249 / +436 | +873 | -1619 / -2834 | -462 | c=1.00: +249 / +873 / -1619 | 44 | -0.136 | -0.461 | -0.02 / +0.16 / -0.12 | ok |
|  | CT70m | L6M | +28 / +50 | +873 | -167 / -292 | -462 | c=1.00: +28 / +873 / -167 | 183 | +0.040 | +0.273 | -0.08 / +0.10 / -0.07 | ok |
|  | CT70p | L3M | +536 / +938 | -3894 | -1995 / -3491 | -2696 | c=1.00: +536 / -3894 / -1995 | 135 | -0.050 | -0.516 | +0.14 / -0.09 / +0.02 | ok |
|  | CT70p | L6M | +331 / +579 | -3894 | -758 / -1326 | -2696 | c=1.00: +331 / -3894 / -758 | 272 | -0.015 | -0.148 | +0.02 / -0.04 / +0.04 | ok |
|  | CT77m | L3M | +35 / +62 | +873 | -1034 / -1809 | +588 | c=1.00: +35 / +873 / -1034 | 37 | -0.044 | -0.127 | -0.21 / -0.03 / -0.19 | ok |
|  | CT77m | L6M | -85 / -148 | +873 | -1039 / -1819 | +588 | c=1.00: -85 / +873 / -1039 | 179 | -0.097 | -0.644 | -0.04 / -0.01 / +0.07 | ok |
|  | CT77p | L3M | +35 / +62 | -1490 | -298 / -521 | -1676 | c=1.00: +35 / -1490 / -298 | 136 | +0.051 | +0.531 | +0.08 / -0.08 / +0.07 | ok |
|  | CT77p | L6M | -118 / -207 | -1490 | -98 / -171 | -1676 | c=1.00: -118 / -1490 / -98 | 256 | +0.026 | +0.248 | -0.01 / -0.05 / -0.01 | ok |
|  | CT7m | L3M | +428 / +750 | -2702 | -1683 / -2944 | -2323 | c=1.00: +428 / -2702 / -1683 | 126 | +0.008 | +0.081 | -0.25 / -0.29 / -0.31 | ok |
|  | CT7m | L6M | +253 / +442 | -2702 | -935 / -1637 | -2323 | c=1.00: +253 / -2702 / -935 | 260 | -0.016 | -0.159 | -0.17 / -0.21 / -0.17 | ok |
|  | CT7p | L3M | +1240 / +2169 | -6031 | -1002 / -1754 | -4232 | c=1.00: +1240 / -6031 / -1002 | 132 | +0.014 | +0.139 | -0.07 / +0.11 / -0.14 | ok |
|  | CT7p | L6M | +610 / +1068 | -6031 | -547 / -957 | -4232 | c=1.00: +610 / -6031 / -547 | 272 | +0.000 | +0.001 | -0.10 / +0.04 / -0.13 | ok |
|  | CT84m | L3M | -0 / -0 | +873 | -1051 / -1839 | +588 | c=1.00: -0 / +873 / -1051 | 21 | +0.028 | +0.045 | -0.05 / -0.03 / -0.03 | ok |
|  | CT84m | L6M | -31 / -54 | +873 | -1102 / -1929 | +588 | c=1.00: -31 / +873 / -1102 | 164 | -0.090 | -0.547 | -0.14 / +0.02 / -0.11 | ok |
|  | CT84p | L3M | +487 / +852 | -1812 | -1769 / -3096 | -2018 | c=1.00: +487 / -1812 / -1769 | 128 | -0.102 | -1.008 | +0.02 / -0.06 / -0.17 | ok |
|  | CT84p | L6M | +236 / +414 | -1812 | -738 / -1291 | -2018 | c=1.00: +236 / -1812 / -738 | 252 | -0.047 | -0.440 | +0.11 / -0.02 / +0.10 | ok |
|  | CT91m | L3M | +9 / +17 | +873 | -1061 / -1858 | +588 | c=1.00: +9 / +873 / -1061 | 13 | -0.015 | -0.015 | +0.16 / +0.37 / +0.19 | ok |
|  | CT91m | L6M | -22 / -39 | +873 | -198 / -347 | +588 | c=1.00: -22 / +873 / -198 | 144 | +0.025 | +0.132 | +0.04 / +0.08 / -0.08 | ok |
|  | CT91p | L3M | +2621 / +4587 | -6146 | -1669 / -2921 | -12188 | c=1.00: +2621 / -6146 / -1669 | 133 | +0.030 | +0.304 | -0.12 / -0.07 / +0.19 | RED |
|  | CT91p | L6M | +1601 / +2802 | -6146 | -1761 / -3082 | -12188 | c=1.00: +1601 / -6146 / -1761 | 245 | -0.072 | -0.654 | -0.03 / -0.02 / +0.19 | RED |
|  | CT98m | L3M | +75 / +131 | +873 | -1237 / -2165 | +588 | c=1.00: +75 / +873 / -1237 | 9 | -0.317 | -0.219 | +0.02 / +0.02 / +0.01 | ok |
|  | CT98m | L6M | -151 / -264 | +873 | +787 / +1377 | +588 | c=1.00: -151 / +873 / +787 | 141 | +0.207 | +1.079 | -0.04 / +0.04 / -0.01 | ok |
|  | CT98p | L3M | -920 / -1610 | +1356 | +891 / +1559 | +3644 | c=1.00: -920 / +1356 / +891 | 117 | +0.167 | +1.500 | -0.02 / -0.17 / +0.14 | ok |
|  | CT98p | L6M | -662 / -1158 | +1356 | +851 / +1490 | +3644 | c=1.00: -662 / +1356 / +851 | 226 | +0.123 | +1.029 | +0.12 / -0.10 / +0.13 | ok |
|  | RP7 | L3M | -1365 / -2388 | +4654 | +832 / +1456 | +5426 | c=1.00: -1365 / +4654 / +832 | 140 | +0.123 | +1.328 | +0.30 / +0.20 / +0.37 | ok |
|  | RP7 | L6M | -713 / -1248 | +1209 | +714 / +1250 | +4245 | c=1.00: -713 / +1209 / +714 | 287 | +0.079 | +0.834 | +0.24 / +0.12 / +0.22 | ok |
|  | RP7 | Y2023 | -2092 / -3661 | -3092 | +751 / +1314 | -4118 | c=1.00: -2092 / -3092 / +751 | 373 | +0.098 | +0.934 | +0.39 / +0.02 / +0.32 | ok |
|  | RP7 | Y2024 | -4045 / -7079 | -432 | +854 / +1495 | +662 | c=1.00: -4045 / -432 / +854 | 563 | +0.051 | +0.545 | +0.35 / +0.15 / +0.39 | ok |
|  | RP7 | Y2025 | -6095 / -10665 | -487 | +1220 / +2135 | +13761 | c=1.00: -6095 / -487 / +1220 | 579 | +0.105 | +1.146 | +0.09 / +0.06 / +0.16 | ok |
|  | CT105m | L3M | -474 / -829 | +628 | -656 / -1147 | +1855 | c=1.00: -474 / +628 / -656 | 0 | +nan | +0.000 | n/a / n/a / n/a | ok |
|  | CT105m | L6M | -299 / -523 | +628 | -474 / -830 | +1855 | c=1.00: -299 / +628 / -474 | 140 | -0.016 | -0.082 | -0.17 / +0.05 / -0.04 | ok |
|  | CT105p | L3M | +1072 / +1876 | -7635 | +735 / +1286 | -4658 | c=1.00: +1072 / -7635 / +735 | 119 | +0.148 | +1.353 | +0.07 / +0.04 / +0.20 | ok |
|  | CT105p | L6M | +674 / +1179 | -7635 | -578 / -1012 | -4658 | c=1.00: +674 / -7635 / -578 | 233 | -0.009 | -0.078 | -0.01 / +0.04 / -0.04 | ok |
|  | CT14m | L3M | -1277 / -2234 | +2909 | -16 / -28 | +3951 | c=1.00: -1277 / +2909 / -16 | 115 | +0.056 | +0.493 | +0.24 / +0.15 / +0.27 | ok |
|  | CT14m | L6M | -843 / -1476 | +2909 | +1159 / +2029 | +3951 | c=1.00: -843 / +2909 / +1159 | 272 | +0.126 | +1.269 | +0.21 / +0.10 / +0.10 | ok |
|  | CT14p | L3M | +590 / +1033 | -4511 | -347 / -606 | -1975 | c=1.00: +590 / -4511 / -347 | 124 | +0.038 | +0.361 | -0.13 / -0.19 / +0.02 | ok |
|  | CT14p | L6M | +325 / +569 | -4511 | -171 / -299 | -1975 | c=1.00: +325 / -4511 / -171 | 262 | +0.024 | +0.236 | -0.02 / -0.03 / +0.03 | ok |
|  | CT21m | L3M | -1294 / -2264 | +3133 | -243 / -426 | +6170 | c=1.00: -1294 / +3133 / -243 | 111 | +0.062 | +0.531 | +0.05 / -0.02 / -0.20 | ok |
|  | CT21m | L6M | -475 / -832 | -785 | -269 / -471 | +4440 | c=1.00: -475 / -785 / -269 | 256 | +0.012 | +0.115 | +0.08 / +0.05 / -0.01 | ok |
|  | CT21p | L3M | +171 / +298 | -3897 | +103 / +181 | -1212 | c=1.00: +171 / -3897 / +103 | 125 | +0.092 | +0.888 | +0.06 / -0.05 / +0.02 | ok |
|  | CT21p | L6M | +104 / +183 | -3897 | +309 / +541 | -1212 | c=1.00: +104 / -3897 / +309 | 268 | +0.068 | +0.672 | -0.01 / -0.04 / +0.10 | ok |
|  | CT28m | L3M | -416 / -728 | +1968 | +401 / +702 | +614 | c=1.00: -416 / +1968 / +401 | 97 | +0.100 | +0.743 | +0.13 / +0.09 / +0.18 | ok |
|  | CT28m | L6M | -150 / -262 | -351 | +271 / +474 | +614 | c=1.00: -150 / -351 / +271 | 233 | +0.041 | +0.352 | +0.07 / +0.09 / -0.09 | ok |
|  | CT28p | L3M | -1235 / -2162 | +3313 | +799 / +1398 | +6699 | c=1.00: -1235 / +3313 / +799 | 131 | +0.103 | +1.034 | +0.28 / -0.06 / +0.11 | ok |
|  | CT28p | L6M | -782 / -1369 | +3313 | +1075 / +1881 | +5526 | c=1.00: -782 / +3313 / +1075 | 255 | +0.115 | +1.091 | +0.19 / -0.03 / +0.13 | ok |
|  | CT35m | L3M | +500 / +876 | +1948 | -1545 / -2705 | -746 | c=1.00: +500 / +1948 / -1545 | 82 | -0.118 | -0.746 | +0.21 / +0.30 / +0.07 | ok |
|  | CT35m | L6M | +262 / +459 | +1948 | -524 / -917 | -746 | c=1.00: +262 / +1948 / -524 | 228 | -0.035 | -0.293 | +0.21 / +0.15 / -0.01 | ok |
|  | CT35p | L3M | +1008 / +1763 | -4856 | -535 / -936 | -1767 | c=1.00: +1008 / -4856 / -535 | 115 | +0.012 | +0.110 | +0.22 / +0.06 / +0.39 | ok |
|  | CT35p | L6M | +558 / +976 | -4856 | -17 / -29 | -1767 | c=1.00: +558 / -4856 / -17 | 259 | +0.024 | +0.233 | +0.24 / +0.06 / +0.25 | ok |
|  | CT42m | L3M | -1135 / -1986 | -3576 | +416 / +728 | +5576 | c=1.00: -1135 / -3576 / +416 | 81 | +0.139 | +0.867 | +0.20 / +0.15 / -0.08 | ok |
|  | CT42m | L6M | -619 / -1084 | -3576 | +422 / +739 | +5456 | c=1.00: -619 / -3576 / +422 | 224 | +0.059 | +0.490 | +0.17 / +0.08 / -0.00 | ok |
|  | CT42p | L3M | -1001 / -1752 | -867 | -812 / -1420 | +4959 | c=1.00: -1001 / -867 / -812 | 126 | -0.027 | -0.258 | +0.14 / -0.10 / +0.05 | ok |
|  | CT42p | L6M | -411 / -720 | -867 | -914 / -1599 | +4235 | c=1.00: -411 / -867 / -914 | 256 | -0.061 | -0.574 | +0.12 / -0.04 / +0.03 | ok |
|  | CT49m | L3M | +106 / +186 | -6210 | -709 / -1241 | +569 | c=1.00: +106 / -6210 / -709 | 71 | +0.034 | +0.184 | -0.09 / -0.34 / -0.09 | ok |
|  | CT49m | L6M | +50 / +88 | -6210 | -950 / -1663 | +569 | c=1.00: +50 / -6210 / -950 | 202 | -0.044 | -0.330 | +0.05 / -0.28 / -0.13 | ok |
|  | CT49p | L3M | +723 / +1264 | -3635 | +1457 / +2549 | -3521 | c=1.00: +723 / -3635 / +1457 | 126 | +0.144 | +1.400 | -0.22 / +0.07 / -0.29 | ok |
|  | CT49p | L6M | +430 / +753 | -3635 | +1245 / +2178 | -3521 | c=1.00: +430 / -3635 / +1245 | 258 | +0.124 | +1.183 | -0.14 / +0.01 / -0.27 | ok |
|  | CT56m | L3M | +38 / +66 | -4551 | -996 / -1744 | -570 | c=1.00: +38 / -4551 / -996 | 64 | -0.046 | -0.229 | -0.06 / +0.03 / +0.15 | ok |
|  | CT56m | L6M | +320 / +561 | -4551 | -920 / -1610 | -570 | c=1.00: +320 / -4551 / -920 | 202 | -0.072 | -0.540 | -0.03 / -0.07 / +0.01 | ok |
|  | CT56p | L3M | -1147 / -2007 | +3699 | -822 / -1438 | +5771 | c=1.00: -1147 / +3699 / -822 | 127 | +0.001 | +0.011 | -0.03 / -0.15 / -0.16 | ok |
|  | CT56p | L6M | -565 / -988 | +3139 | -469 / -821 | +4285 | c=1.00: -565 / +3139 / -469 | 272 | -0.006 | -0.061 | -0.02 / -0.08 / -0.03 | ok |
|  | CT63m | L3M | -815 / -1425 | +1823 | +643 / +1125 | +4026 | c=1.00: -815 / +1823 / +643 | 53 | +0.226 | +0.923 | +0.06 / +0.13 / +0.12 | ok |
|  | CT63m | L6M | -451 / -788 | +1823 | -131 / -229 | +4026 | c=1.00: -451 / +1823 / -131 | 196 | +0.006 | +0.041 | +0.03 / -0.03 / -0.08 | ok |
|  | CT63p | L3M | +684 / +1197 | +79 | -453 / -792 | -3160 | c=1.00: +684 / +79 / -453 | 130 | +0.039 | +0.385 | +0.13 / -0.00 / +0.23 | ok |
|  | CT63p | L6M | +366 / +641 | +79 | +200 / +350 | -3160 | c=1.00: +366 / +79 / +200 | 252 | +0.050 | +0.463 | +0.06 / +0.02 / +0.00 | ok |
|  | CT70m | L3M | -384 / -672 | +3133 | -1252 / -2191 | +1925 | c=1.00: -384 / +3133 / -1252 | 43 | -0.161 | -0.532 | -0.03 / +0.21 / -0.10 | ok |
|  | CT70m | L6M | -254 / -445 | +3133 | -48 / -84 | +1925 | c=1.00: -254 / +3133 / -48 | 182 | +0.036 | +0.239 | -0.08 / +0.12 / -0.07 | ok |
|  | CT70p | L3M | +41 / +72 | -3071 | -2327 / -4072 | -309 | c=1.00: +41 / -3071 / -2327 | 134 | -0.058 | -0.593 | +0.13 / -0.09 / +0.00 | ok |
|  | CT70p | L6M | +172 / +301 | -3071 | -967 / -1693 | -309 | c=1.00: +172 / -3071 / -967 | 270 | -0.019 | -0.188 | +0.01 / -0.04 / +0.03 | ok |
|  | CT77m | L3M | -506 / -886 | +628 | -497 / -870 | +1855 | c=1.00: -506 / +628 / -497 | 40 | -0.016 | -0.048 | -0.20 / -0.08 / -0.19 | ok |
|  | CT77m | L6M | -328 / -574 | +628 | -829 / -1450 | +1855 | c=1.00: -328 / +628 / -829 | 180 | -0.085 | -0.567 | -0.03 / -0.03 / +0.08 | ok |
|  | CT77p | L3M | -617 / -1080 | -666 | +152 / +266 | +711 | c=1.00: -617 / -666 / +152 | 135 | +0.044 | +0.454 | +0.06 / -0.08 / +0.06 | ok |
|  | CT77p | L6M | -419 / -734 | -666 | +76 / +133 | +711 | c=1.00: -419 / -666 / +76 | 255 | +0.022 | +0.211 | -0.02 / -0.05 / -0.01 | ok |
|  | CT7m | L3M | -165 / -289 | -2250 | -1282 / -2243 | +64 | c=1.00: -165 / -2250 / -1282 | 124 | +0.009 | +0.081 | -0.24 / -0.31 / -0.29 | ok |
|  | CT7m | L6M | +43 / +76 | -2250 | -792 / -1386 | +64 | c=1.00: +43 / -2250 / -792 | 259 | -0.020 | -0.194 | -0.15 / -0.21 / -0.15 | ok |
|  | CT7p | L3M | +498 / +872 | -4886 | -677 / -1185 | -1152 | c=1.00: +498 / -4886 / -677 | 131 | +0.021 | +0.214 | -0.06 / +0.13 / -0.15 | ok |
|  | CT7p | L6M | +226 / +396 | -4886 | -356 / -623 | -1152 | c=1.00: +226 / -4886 / -356 | 270 | +0.007 | +0.073 | -0.10 / +0.06 / -0.14 | ok |
|  | CT84m | L3M | -424 / -742 | +628 | -717 / -1254 | +1855 | c=1.00: -424 / +628 / -717 | 23 | -0.061 | -0.108 | -0.06 / +0.18 / +0.01 | ok |
|  | CT84m | L6M | -200 / -349 | +628 | -1010 / -1768 | +1855 | c=1.00: -200 / +628 / -1010 | 164 | -0.102 | -0.620 | -0.13 / +0.07 / -0.10 | ok |
|  | CT84p | L3M | -136 / -238 | -1360 | -1160 / -2031 | +369 | c=1.00: -136 / -1360 / -1160 | 127 | -0.111 | -1.084 | +0.02 / -0.04 / -0.17 | ok |
|  | CT84p | L6M | +61 / +106 | -1360 | -687 / -1203 | +369 | c=1.00: +61 / -1360 / -687 | 250 | -0.055 | -0.513 | +0.10 / -0.01 / +0.10 | ok |
|  | CT91m | L3M | -451 / -790 | +628 | -674 / -1179 | +1855 | c=1.00: -451 / +628 / -674 | 13 | -0.015 | -0.015 | +0.16 / +0.37 / +0.19 | ok |
|  | CT91m | L6M | -240 / -420 | +628 | +59 / +103 | +1855 | c=1.00: -240 / +628 / +59 | 143 | +0.028 | +0.148 | +0.03 / +0.08 / -0.08 | ok |
|  | CT91p | L3M | +2407 / +4212 | -5001 | -918 / -1606 | -10805 | c=1.00: +2407 / -5001 / -918 | 130 | +0.036 | +0.363 | -0.16 / -0.07 / +0.15 | RED |
|  | CT91p | L6M | +1580 / +2765 | -5001 | -1415 / -2477 | -10805 | c=1.00: +1580 / -5001 / -1415 | 239 | -0.067 | -0.589 | -0.05 / -0.02 / +0.17 | RED |
|  | CT98m | L3M | -319 / -558 | +628 | -919 / -1608 | +1855 | c=1.00: -319 / +628 / -919 | 9 | -0.317 | -0.219 | +0.02 / +0.02 / +0.01 | ok |
|  | CT98m | L6M | -314 / -550 | +628 | +886 / +1551 | +1855 | c=1.00: -314 / +628 / +886 | 141 | +0.207 | +1.079 | -0.04 / +0.04 / -0.01 | ok |
|  | CT98p | L3M | -1679 / -2938 | +2873 | +1423 / +2491 | +6724 | c=1.00: -1679 / +2873 / +1423 | 117 | +0.167 | +1.500 | -0.02 / -0.17 / +0.14 | ok |
|  | CT98p | L6M | -1012 / -1770 | +2873 | +985 / +1723 | +6656 | c=1.00: -1012 / +2873 / +985 | 224 | +0.124 | +1.029 | +0.11 / -0.11 / +0.13 | ok |
|  | RK7 | L3M | +1666 / +2915 | -4780 | -851 / -1489 | -2096 | c=1.00: +1666 / -4780 / -851 | 85 | -0.071 | -0.465 | +0.10 / +0.08 / +0.11 | AMBER |
|  | RK7 | L6M | +1109 / +1940 | -4780 | -265 / -464 | -2096 | c=1.00: +1109 / -4780 / -265 | 176 | -0.047 | -0.306 | +0.15 / +0.08 / +0.15 | ok |
|  | RK7 | L3M | +3594 / +6289 | -6905 | -1417 / -2480 | -9674 | c=1.00: +3594 / -6905 / -1417 | 66 | -0.327 | -1.660 | -0.11 / +0.08 / +0.04 | RED |
|  | RK7 | L6M | +2399 / +4198 | -6905 | -1175 / -2057 | -9674 | c=1.00: +2399 / -6905 / -1175 | 164 | -0.210 | -1.275 | -0.06 / +0.05 / -0.14 | RED |
|  | RK7 | L3M | +1188 / +2080 | -4065 | +1313 / +2298 | -2702 | c=1.00: +1188 / -4065 / +1313 | 59 | +0.069 | +0.313 | +0.11 / -0.02 / +0.26 | ok |
|  | RK7 | L6M | +732 / +1281 | -4065 | +1293 / +2262 | -2702 | c=1.00: +732 / -4065 / +1293 | 134 | +0.144 | +0.717 | +0.01 / -0.01 / +0.18 | ok |
|  | RK7 | L3M | +77 / +135 | -317 | +479 / +839 | +1478 | c=1.00: +77 / -317 / +479 | 134 | +0.040 | +0.413 | +0.22 / +0.20 / +0.52 | ok |
|  | RK7 | L6M | +147 / +258 | -317 | +960 / +1679 | +1478 | c=1.00: +147 / -317 / +960 | 274 | +0.069 | +0.700 | +0.19 / +0.19 / +0.27 | ok |
|  | RK7 | L3M | +329 / +576 | -322 | +1285 / +2249 | +1123 | c=1.00: +329 / -322 / +1285 | 38 | +0.261 | +0.762 | +0.37 / -0.05 / +0.13 | ok |
|  | RK7 | L3M | +303 / +530 | +1651 | +2638 / +4617 | +664 | c=1.00: +303 / +1651 / +2638 | 163 | +0.125 | +1.569 | +0.17 / +0.12 / +0.38 | ok |
|  | RK7 | L6M | +255 / +446 | +1651 | +2505 / +4384 | +664 | c=1.00: +255 / +1651 / +2505 | 382 | +0.123 | +1.742 | +0.14 / +0.08 / +0.16 | ok |
|  | RK7 | L3M | +2706 / +4735 | -9015 | +1613 / +2823 | -12215 | c=1.00: +2706 / -9015 / +1613 | 127 | +0.111 | +1.086 | +0.13 / -0.00 / +0.20 | RED |
|  | RK7 | L6M | +1860 / +3255 | -9015 | +1741 / +3046 | -12215 | c=1.00: +1860 / -9015 / +1741 | 266 | +0.126 | +1.238 | +0.02 / +0.03 / +0.01 | RED |
|  | RK7 | L3M | +917 / +1606 | -1213 | +777 / +1361 | -1457 | c=1.00: +917 / -1213 / +777 | 74 | +0.083 | +0.473 | +0.28 / +0.20 / +0.29 | ok |
|  | RK7 | L6M | +798 / +1396 | -1213 | +228 / +400 | -1457 | c=1.00: +798 / -1213 / +228 | 166 | -0.001 | -0.005 | +0.16 / +0.17 / +0.14 | ok |
|  | RK7 | L3M | +2679 / +4689 | -8240 | -452 / -791 | -7967 | c=1.00: +2679 / -8240 / -452 | 60 | -0.170 | -0.783 | +0.17 / -0.02 / +0.20 | AMBER |
|  | RK7 | L6M | +1710 / +2993 | -8240 | +1344 / +2351 | -7967 | c=1.00: +1710 / -8240 / +1344 | 137 | +0.162 | +0.822 | +0.15 / +0.03 / +0.19 | AMBER |
|  | RK7 | L3M | +2438 / +4266 | -4180 | -804 / -1407 | -7064 | c=1.00: +2438 / -4180 / -804 | 72 | -0.094 | -0.519 | +0.15 / +0.09 / +0.16 | AMBER |
|  | RK7 | L6M | +1738 / +3042 | -4180 | -17 / -30 | -7064 | c=1.00: +1738 / -4180 / -17 | 163 | -0.009 | -0.057 | +0.01 / +0.07 / +0.17 | AMBER |
|  | RK7 | L3M | +1553 / +2717 | -2391 | +93 / +163 | -4840 | c=1.00: +1553 / -2391 / +93 | 136 | -0.057 | -0.593 | -0.10 / -0.11 / +0.06 | AMBER |
|  | RK7 | L6M | +1034 / +1809 | -2391 | +232 / +406 | -4840 | c=1.00: +1034 / -2391 / +232 | 272 | -0.024 | -0.244 | -0.00 / +0.01 / +0.01 | AMBER |
|  | RK7 | L3M | +1114 / +1949 | -2722 | -471 / -825 | -2695 | c=1.00: +1114 / -2722 / -471 | 71 | -0.008 | -0.043 | -0.02 / -0.18 / +0.07 | ok |
|  | RK7 | L6M | +1223 / +2140 | -7615 | -261 / -457 | -2695 | c=1.00: +1223 / -7615 / -261 | 167 | -0.016 | -0.100 | -0.03 / -0.04 / +0.11 | ok |
|  | RK7 | L3M | +2037 / +3565 | -5255 | +580 / +1015 | -7474 | c=1.00: +2037 / -5255 / +580 | 77 | +0.009 | +0.051 | +0.03 / -0.12 / +0.14 | AMBER |
|  | RK7 | L6M | +1519 / +2658 | -5255 | +1481 / +2592 | -7474 | c=1.00: +1519 / -5255 / +1481 | 157 | +0.174 | +1.010 | -0.04 / -0.05 / +0.09 | AMBER |
|  | RK7 | L3M | +2739 / +4793 | -2560 | +1101 / +1927 | -9826 | c=1.00: +2739 / -2560 / +1101 | 68 | +0.203 | +1.061 | +0.02 / -0.09 / +0.08 | RED |
|  | RK7 | L6M | +1741 / +3046 | -2560 | +1602 / +2804 | -9826 | c=1.00: +1741 / -2560 / +1602 | 146 | +0.237 | +1.279 | +0.02 / -0.01 / +0.15 | RED |
|  | RK7 | L3M | +943 / +1651 | -5635 | +2913 / +5097 | -2385 | c=1.00: +943 / -5635 / +2913 | 155 | +0.197 | +2.354 | +0.26 / +0.13 / +0.16 | ok |
|  | RK7 | L6M | +605 / +1060 | -5635 | +1426 / +2496 | -2385 | c=1.00: +605 / -5635 / +1426 | 345 | +0.078 | +1.000 | +0.13 / +0.13 / +0.06 | ok |
|  | RH7 | L3M | -1427 / -2497 | -21 | +1801 / +3151 | +5671 | c=1.00: -1427 / -21 / +1801 | 63 | +0.352 | +1.707 | +0.26 / -0.07 / +0.11 | ok |
|  | RH7 | L6M | -637 / -1114 | -1686 | +1537 / +2690 | +4180 | c=1.00: -637 / -1686 / +1537 | 136 | +0.324 | +1.634 | +0.07 / -0.03 / +0.02 | ok |
|  | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=1.00: -504 / -3120 / +2902 | 62 | +0.356 | +1.698 | +0.25 / -0.07 / +0.11 | ok |
|  | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=1.00: -58 / -3120 / +2291 | 136 | +0.327 | +1.650 | +0.06 / -0.03 / +0.02 | ok |
|  | RK7 | Y2023 | -1698 / -2972 | -7720 | -122 / -213 | -4200 | c=1.00: -1698 / -7720 / -122 | 182 | +0.096 | +0.448 | +0.07 / +0.04 / +0.23 | ok |
|  | RK7 | Y2024 | -1956 / -3423 | -882 | +670 / +1172 | +8949 | c=1.00: -1956 / -882 / +670 | 256 | +0.128 | +0.620 | -0.01 / +0.02 / +0.14 | ok |
|  | RK7 | Y2025 | -5837 / -10214 | +6385 | -137 / -239 | +13807 | c=1.00: -5837 / +6385 / -137 | 269 | +0.103 | +0.520 | +0.00 / -0.01 / +0.02 | ok |
|  | RK7LO | L3M | +1728 / +3023 | -5925 | +1303 / +2280 | -8593 | c=1.00: +1728 / -5925 / +1303 | 53 | +0.110 | +0.447 | +0.02 / +0.01 / -0.14 | AMBER |
|  | RK7LO | L6M | +1429 / +2501 | -5925 | +46 / +81 | -8593 | c=1.00: +1429 / -5925 / +46 | 123 | -0.098 | -0.448 | +0.05 / +0.01 / +0.05 | AMBER |
|  | RK7LO | Y2023 | -2645 / -4628 | -5030 | -27 / -47 | -1140 | c=1.00: -2645 / -5030 / -27 | 182 | +0.113 | +0.527 | +0.05 / +0.13 / +0.07 | ok |
|  | RK7LO | Y2024 | -2407 / -4213 | +1242 | +783 / +1370 | +1321 | c=1.00: -2407 / +1242 / +783 | 238 | +0.168 | +0.754 | -0.05 / -0.03 / -0.13 | ok |
|  | RK7LO | Y2025 | +3581 / +6267 | -6699 | -719 / -1258 | -10694 | c=1.00: +3581 / -6699 / -719 | 264 | +0.014 | +0.067 | -0.01 / +0.04 / -0.07 | ok |
|  | RK7SO | L3M | +2130 / +3727 | -5067 | +405 / +709 | -5499 | c=1.00: +2130 / -5067 / +405 | 57 | -0.051 | -0.223 | +0.08 / -0.01 / +0.31 | AMBER |
|  | RK7SO | L6M | +1364 / +2387 | -5067 | +1324 / +2318 | -5499 | c=1.00: +1364 / -5067 / +1324 | 128 | +0.168 | +0.796 | +0.01 / -0.00 / +0.07 | AMBER |
|  | RM7 | L3M | -1391 / -2434 | -100 | +1273 / +2228 | +6039 | c=1.00: -1391 / -100 / +1273 | 63 | +0.352 | +1.707 | +0.26 / -0.07 / +0.11 | ok |
|  | RM7 | L6M | -799 / -1397 | -100 | +1497 / +2620 | +6039 | c=1.00: -799 / -100 / +1497 | 136 | +0.324 | +1.634 | +0.07 / -0.03 / +0.02 | ok |
|  | RP7 | L3M | -2012 / -3522 | +724 | +1418 / +2481 | +8426 | c=1.00: -2012 / +724 / +1418 | 62 | +0.326 | +1.553 | +0.23 / -0.07 / +0.10 | ok |
|  | RP7 | L6M | -1014 / -1774 | -796 | +1313 / +2297 | +4245 | c=1.00: -1014 / -796 / +1313 | 135 | +0.312 | +1.560 | +0.05 / -0.03 / +0.01 | ok |
|  | RK7 | L3M | +2065 / +3614 | -5381 | +135 / +236 | -7825 | c=1.00: +2065 / -5381 / +135 | 136 | -0.042 | -0.437 | +0.17 / -0.01 / +0.12 | AMBER |
|  | RK7 | L6M | +1321 / +2312 | -5381 | -88 / -153 | -7825 | c=1.00: +1321 / -5381 / -88 | 312 | -0.035 | -0.410 | +0.13 / +0.02 / +0.09 | AMBER |
|  | RK7 | L3M | +1934 / +3385 | -3821 | +156 / +273 | -3653 | c=1.00: +1934 / -3821 / +156 | 132 | -0.055 | -0.557 | -0.13 / -0.06 / +0.06 | AMBER |
|  | RK7 | L6M | +1282 / +2243 | -3821 | +680 / +1190 | -3653 | c=1.00: +1282 / -3821 / +680 | 288 | +0.008 | +0.084 | +0.01 / +0.04 / +0.03 | ok |
|  | RK7 | L3M | +1912 / +3345 | -1734 | +1964 / +3436 | -7092 | c=1.00: +1912 / -1734 / +1964 | 213 | +0.072 | +1.187 | -0.12 / -0.08 / +0.18 | AMBER |
|  | RK7 | L6M | +1360 / +2379 | -2148 | +931 / +1629 | -7092 | c=1.00: +1360 / -2148 / +931 | 503 | +0.029 | +0.535 | -0.05 / +0.02 / +0.15 | AMBER |
|  | RK7 | L3M | +892 / +1561 | +969 | +1557 / +2726 | -3857 | c=1.00: +892 / +969 / +1557 | 70 | +0.273 | +1.469 | +0.16 / +0.22 / +0.25 | ok |
|  | RK7 | L6M | +634 / +1109 | +969 | +1034 / +1809 | -3857 | c=1.00: +634 / +969 / +1034 | 176 | +0.137 | +0.893 | +0.12 / +0.15 / +0.25 | ok |
|  | RK7 | L3M | +469 / +822 | -3935 | +2811 / +4920 | -627 | c=1.00: +469 / -3935 / +2811 | 91 | +0.270 | +1.891 | +0.24 / +0.27 / +0.20 | ok |
|  | RK7 | L6M | +307 / +538 | -3935 | +2330 / +4077 | -627 | c=1.00: +307 / -3935 / +2330 | 222 | +0.192 | +1.583 | +0.06 / +0.17 / +0.15 | ok |
|  | RK7 | L3M | +416 / +728 | -3580 | +791 / +1384 | -130 | c=1.00: +416 / -3580 / +791 | 69 | +0.030 | +0.158 | +0.10 / -0.04 / +0.04 | ok |
|  | RK7 | L6M | +358 / +627 | -3580 | +1374 / +2404 | -130 | c=1.00: +358 / -3580 / +1374 | 164 | +0.120 | +0.728 | +0.06 / +0.03 / +0.11 | ok |
|  | RK7 | L3M | -283 / -496 | +3268 | -335 / -586 | +2124 | c=1.00: -283 / +3268 / -335 | 132 | -0.018 | -0.180 | +0.45 / +0.20 / +0.39 | ok |
|  | RK7 | L6M | -93 / -163 | +3240 | +284 / +497 | +2124 | c=1.00: -93 / +3240 / +284 | 254 | +0.012 | +0.113 | +0.31 / +0.11 / +0.26 | ok |
|  | RK7 | L3M | +2453 / +4292 | -5545 | +641 / +1121 | -9365 | c=1.00: +2453 / -5545 / +641 | 103 | -0.003 | -0.026 | -0.33 / -0.19 / -0.32 | RED |
|  | RK7 | L3M | +1083 / +1895 | -6570 | +2339 / +4093 | -4545 | c=1.00: +1083 / -6570 / +2339 | 126 | +0.161 | +1.563 | +0.36 / +0.15 / +0.28 | ok |
|  | RK7 | L6M | +758 / +1326 | -6570 | +1556 / +2723 | -4545 | c=1.00: +758 / -6570 / +1556 | 283 | +0.091 | +0.957 | +0.16 / +0.11 / +0.07 | ok |
|  | RK7 | L3M | +1253 / +2192 | -6390 | +581 / +1017 | -3046 | c=1.00: +1253 / -6390 / +581 | 74 | +0.095 | +0.542 | +0.20 / +0.06 / +0.01 | ok |
|  | RK7 | L6M | +1096 / +1919 | -6390 | +430 / +752 | -3046 | c=1.00: +1096 / -6390 / +430 | 167 | +0.044 | +0.271 | +0.09 / +0.03 / +0.13 | ok |
|  | RK7 | L3M | -664 / -1163 | +422 | +3941 / +6897 | +2235 | c=1.00: -664 / +422 / +3941 | 117 | +0.356 | +3.207 | +0.25 / +0.11 / +0.19 | ok |
|  | RK7 | L6M | +143 / +251 | +422 | +1571 / +2749 | -5362 | c=1.00: +143 / +422 / +1571 | 259 | +0.125 | +1.201 | +0.13 / +0.07 / +0.10 | AMBER |
|  | RK7 | L3M | +419 / +733 | -3970 | +1788 / +3129 | -1170 | c=1.00: +419 / -3970 / +1788 | 65 | +0.296 | +1.480 | +0.29 / +0.09 / +0.21 | ok |
|  | RK7 | L6M | +572 / +1001 | -3970 | +174 / +305 | -1170 | c=1.00: +572 / -3970 / +174 | 149 | -0.006 | -0.035 | +0.12 / +0.10 / +0.16 | ok |
|  | RK7 | L3M | +1152 / +2017 | -5520 | +1785 / +3124 | -4853 | c=1.00: +1152 / -5520 / +1785 | 64 | +0.213 | +1.050 | +0.12 / +0.02 / +0.18 | AMBER |
|  | RK7 | L6M | +921 / +1611 | -5520 | -90 / -157 | -4853 | c=1.00: +921 / -5520 / -90 | 151 | -0.062 | -0.347 | +0.06 / +0.09 / +0.17 | AMBER |
|  | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=1.00: +1894 / -3780 / +589 | 74 | +0.067 | +0.382 | +0.03 / +0.06 / -0.01 | AMBER |
|  | RK7 | L6M | +1487 / +2602 | -3945 | +1090 / +1907 | -6714 | c=1.00: +1487 / -3945 / +1090 | 161 | +0.123 | +0.731 | -0.02 / +0.08 / +0.10 | AMBER |
|  | RK7 | L3M | +2729 / +4776 | -6937 | +727 / +1273 | -9245 | c=1.00: +2729 / -6937 / +727 | 88 | +0.032 | +0.219 | +0.15 / -0.05 / +0.15 | AMBER |
|  | RK7 | L6M | +1847 / +3232 | -6937 | +975 / +1706 | -9245 | c=1.00: +1847 / -6937 / +975 | 193 | +0.066 | +0.474 | +0.12 / +0.04 / +0.14 | AMBER |
|  | RK7 | L3M | +4595 / +8041 | -3125 | -371 / -649 | -14491 | c=1.00: +4595 / -3125 / -371 | 101 | -0.042 | -0.328 | +0.09 / +0.37 / +0.34 | RED |
|  | RK7 | L6M | +2951 / +5163 | -3851 | +743 / +1300 | -14491 | c=1.00: +2951 / -3851 / +743 | 222 | +0.067 | +0.549 | +0.02 / +0.25 / +0.25 | RED |
|  | RK7 | L3M | +541 / +946 | +2066 | +2017 / +3530 | -972 | c=1.00: +541 / +2066 / +2017 | 200 | +0.070 | +1.083 | +0.15 / +0.16 / +0.30 | ok |
|  | RK7 | L6M | +413 / +722 | +1007 | +2434 / +4260 | -972 | c=1.00: +413 / +1007 / +2434 | 436 | +0.100 | +1.615 | +0.17 / +0.07 / +0.12 | ok |
|  | RK7 | L3M | +1222 / +2139 | -4680 | +15 / +27 | -2931 | c=1.00: +1222 / -4680 / +15 | 55 | -0.024 | -0.099 | +0.09 / +0.01 / -0.13 | ok |
|  | RK7 | L6M | +902 / +1579 | -4680 | -187 / -328 | -2931 | c=1.00: +902 / -4680 / -187 | 119 | -0.089 | -0.392 | +0.08 / -0.02 / -0.04 | ok |
|  | RK7 | L3M | +3281 / +5742 | -6615 | +1025 / +1793 | -12433 | c=1.00: +3281 / -6615 / +1025 | 75 | +0.022 | +0.128 | -0.07 / +0.11 / +0.16 | RED |
|  | RK7 | L3M | +1314 / +2299 | -4440 | +1205 / +2109 | -5761 | c=1.00: +1314 / -4440 / +1205 | 70 | +0.182 | +0.978 | +0.11 / -0.09 / +0.17 | AMBER |
|  | RK7 | L6M | +1110 / +1942 | -4440 | +884 / +1547 | -5761 | c=1.00: +1110 / -4440 / +884 | 163 | +0.089 | +0.535 | +0.06 / +0.03 / +0.21 | AMBER |
|  | RK7 | L3M | +2681 / +4692 | -2702 | -362 / -634 | -7745 | c=1.00: +2681 / -2702 / -362 | 69 | -0.172 | -0.915 | -0.13 / +0.22 / +0.06 | AMBER |
|  | RK7 | L6M | +1921 / +3362 | -3760 | -1418 / -2482 | -7745 | c=1.00: +1921 / -3760 / -1418 | 159 | -0.279 | -1.643 | -0.06 / +0.04 / +0.03 | AMBER |
|  | RK7 | L3M | +3910 / +6842 | -7720 | +1005 / +1759 | -12802 | c=1.00: +3910 / -7720 / +1005 | 61 | +0.045 | +0.209 | -0.03 / +0.05 / +0.29 | RED |
|  | RK7 | L6M | +2381 / +4167 | -7720 | +2736 / +4788 | -12802 | c=1.00: +2381 / -7720 / +2736 | 149 | +0.348 | +1.919 | -0.06 / -0.03 / +0.13 | RED |
|  | RK7 | L3M | +527 / +922 | +15 | +2 / +4 | -1020 | c=1.00: +527 / +15 / +2 | 80 | +0.038 | +0.234 | +0.07 / -0.04 / +0.05 | ok |
|  | RK7 | L6M | +564 / +986 | +15 | +609 / +1066 | -1020 | c=1.00: +564 / +15 / +609 | 179 | +0.082 | +0.542 | +0.01 / -0.02 / +0.12 | ok |
|  | RK7 | L3M | +2051 / +3589 | -6385 | +20 / +35 | -8729 | c=1.00: +2051 / -6385 / +20 | 149 | -0.048 | -0.546 | +0.17 / +0.19 / +0.27 | AMBER |
|  | RK7 | L6M | +1342 / +2349 | -6385 | +1349 / +2361 | -8729 | c=1.00: +1342 / -6385 / +1349 | 325 | +0.064 | +0.775 | +0.08 / +0.04 / +0.17 | AMBER |
|  | RK7 | L3M | +3860 / +6756 | -8080 | -199 / -349 | -11861 | c=1.00: +3860 / -8080 / -199 | 72 | -0.111 | -0.612 | +0.10 / +0.12 / +0.21 | RED |
|  | RK7 | L6M | +2369 / +4147 | -8080 | +408 / +714 | -11861 | c=1.00: +2369 / -8080 / +408 | 155 | +0.021 | +0.121 | +0.07 / +0.02 / +0.17 | RED |
|  | RK7 | L3M | +180 / +316 | -1962 | +1276 / +2234 | -2585 | c=1.00: +180 / -1962 / +1276 | 238 | +0.053 | +0.964 | +0.34 / +0.34 / +0.23 | ok |
|  | RK7 | L6M | +137 / +240 | -1962 | +2049 / +3586 | -2585 | c=1.00: +137 / -1962 / +2049 | 596 | +0.063 | +1.396 | +0.28 / +0.24 / +0.12 | ok |
|  | RK7 | L3M | +107 / +188 | +690 | +2626 / +4595 | +1537 | c=1.00: +107 / +690 / +2626 | 133 | +0.144 | +1.469 | +0.24 / +0.08 / +0.20 | ok |
|  | RK7 | L6M | +361 / +632 | -3010 | +1842 / +3223 | +1537 | c=1.00: +361 / -3010 / +1842 | 250 | +0.117 | +1.085 | +0.10 / +0.07 / +0.06 | ok |
|  | RK7 | L3M | +2758 / +4826 | -5758 | -272 / -476 | -7049 | c=1.00: +2758 / -5758 / -272 | 90 | -0.114 | -0.788 | -0.04 / +0.03 / +0.19 | AMBER |
|  | RK7 | L6M | +1882 / +3294 | -5758 | +298 / +522 | -7049 | c=1.00: +1882 / -5758 / +298 | 194 | -0.036 | -0.258 | +0.03 / +0.07 / +0.19 | AMBER |
|  | RK7 | L3M | +696 / +1217 | -900 | +2024 / +3542 | -189 | c=1.00: +696 / -900 / +2024 | 70 | +0.198 | +1.068 | -0.03 / +0.21 / +0.15 | ok |
|  | RK7 | L6M | +665 / +1164 | -900 | +1204 / +2108 | -189 | c=1.00: +665 / -900 / +1204 | 158 | +0.091 | +0.531 | -0.09 / +0.13 / +0.14 | ok |
|  | RK7 | L3M | -215 / -376 | -3000 | +1586 / +2775 | +2131 | c=1.00: -215 / -3000 / +1586 | 65 | +0.162 | +0.812 | +0.17 / -0.16 / +0.04 | ok |
|  | RK7 | L6M | +234 / +410 | -3850 | +1570 / +2747 | +1857 | c=1.00: +234 / -3850 / +1570 | 142 | +0.214 | +1.126 | +0.08 / -0.06 / +0.08 | ok |
|  | RK7 | L3M | +2679 / +4689 | -8240 | -452 / -791 | -7967 | c=1.00: +2679 / -8240 / -452 | 60 | -0.170 | -0.783 | +0.17 / -0.02 / +0.20 | AMBER |
|  | RK7 | L6M | +1710 / +2993 | -8240 | +1344 / +2351 | -7967 | c=1.00: +1710 / -8240 / +1344 | 137 | +0.162 | +0.822 | +0.15 / +0.03 / +0.19 | AMBER |
|  | RK7 | L3M | +2569 / +4495 | -5990 | +609 / +1066 | -4682 | c=1.00: +2569 / -5990 / +609 | 61 | +0.133 | +0.624 | -0.08 / +0.19 / -0.01 | AMBER |
|  | RK7 | L6M | +1615 / +2826 | -5990 | +327 / +571 | -4682 | c=1.00: +1615 / -5990 / +327 | 149 | +0.045 | +0.251 | -0.09 / +0.18 / -0.02 | AMBER |
|  | RK7 | L3M | +1383 / +2421 | -2255 | +79 / +139 | -3808 | c=1.00: +1383 / -2255 / +79 | 101 | -0.090 | -0.697 | +0.36 / +0.11 / +0.39 | ok |
|  | RK7 | L6M | +1006 / +1761 | -2255 | +471 / +824 | -3808 | c=1.00: +1006 / -2255 / +471 | 214 | -0.022 | -0.178 | +0.15 / +0.11 / +0.29 | ok |
|  | RK7 | L3M | +2353 / +4118 | -6246 | +948 / +1659 | -10427 | c=1.00: +2353 / -6246 / +948 | 121 | +0.026 | +0.245 | +0.21 / -0.03 / +0.35 | RED |
|  | RK7 | L6M | +1602 / +2804 | -6246 | +480 / +839 | -10427 | c=1.00: +1602 / -6246 / +480 | 286 | +0.009 | +0.094 | +0.14 / +0.02 / +0.23 | RED |
|  | RK7 | L3M | +3582 / +6269 | -6275 | +525 / +919 | -12520 | c=1.00: +3582 / -6275 / +525 | 79 | -0.013 | -0.079 | +0.32 / +0.29 / +0.45 | RED |
|  | RK7 | L6M | +2380 / +4165 | -6275 | +729 / +1276 | -12520 | c=1.00: +2380 / -6275 / +729 | 155 | +0.036 | +0.207 | +0.27 / +0.16 / +0.39 | RED |
|  | RK7 | L3M | +5714 / +9999 | -8724 | +553 / +968 | -19101 | c=1.00: +5714 / -8724 / +553 | 116 | +0.036 | +0.324 | +0.05 / +0.25 / +0.31 | RED |
|  | RK7 | L6M | +3822 / +6688 | -8724 | +1631 / +2854 | -19101 | c=1.00: +3822 / -8724 / +1631 | 292 | +0.108 | +1.163 | +0.00 / +0.16 / +0.15 | RED |
|  | RK7 | L3M | -448 / -784 | -3080 | +2629 / +4601 | +2306 | c=1.00: -448 / -3080 / +2629 | 64 | +0.304 | +1.495 | +0.23 / -0.12 / +0.07 | ok |
|  | RK7 | L6M | +100 / +175 | -3825 | +1934 / +3385 | +1857 | c=1.00: +100 / -3825 / +1934 | 136 | +0.256 | +1.288 | +0.13 / -0.04 / +0.05 | ok |
|  | RK7 | L3M | +1345 / +2353 | -4875 | +1608 / +2814 | -3399 | c=1.00: +1345 / -4875 / +1608 | 71 | +0.147 | +0.805 | +0.06 / +0.07 / +0.10 | ok |
|  | RK7 | L6M | +1262 / +2208 | -6955 | +1016 / +1778 | -3399 | c=1.00: +1262 / -6955 / +1016 | 162 | +0.079 | +0.474 | +0.08 / +0.04 / +0.18 | ok |
|  | RK7 | L3M | +1317 / +2305 | +1142 | -1019 / -1783 | -4186 | c=1.00: +1317 / +1142 / -1019 | 89 | -0.183 | -1.255 | +0.07 / -0.02 / +0.03 | ok |
|  | RK7 | L6M | +980 / +1715 | +1142 | +1275 / +2231 | -4186 | c=1.00: +980 / +1142 / +1275 | 206 | +0.093 | +0.708 | -0.04 / -0.01 / -0.12 | ok |
|  | RK7 | L3M | -664 / -1163 | +422 | +3941 / +6897 | +2235 | c=1.00: -664 / +422 / +3941 | 117 | +0.356 | +3.207 | +0.25 / +0.11 / +0.19 | ok |
|  | RK7 | L6M | +143 / +251 | +422 | +1571 / +2749 | -5362 | c=1.00: +143 / +422 / +1571 | 259 | +0.125 | +1.201 | +0.13 / +0.07 / +0.10 | AMBER |
|  | RK7 | L3M | +588 / +1029 | -4275 | +692 / +1211 | +565 | c=1.00: +588 / -4275 / +692 | 59 | +0.027 | +0.122 | -0.01 / -0.24 / +0.02 | ok |
|  | RK7 | L6M | +464 / +812 | -4275 | +1427 / +2497 | +565 | c=1.00: +464 / -4275 / +1427 | 129 | +0.188 | +0.899 | +0.00 / -0.09 / +0.07 | ok |
|  | RK7 | L3M | +1505 / +2634 | -1108 | +250 / +437 | -4896 | c=1.00: +1505 / -1108 / +250 | 113 | +0.021 | +0.181 | +0.29 / +0.19 / +0.58 | AMBER |
|  | RK7 | L6M | +1185 / +2073 | -1108 | +166 / +291 | -4896 | c=1.00: +1185 / -1108 / +166 | 242 | +0.010 | +0.091 | +0.30 / +0.16 / +0.49 | AMBER |
|  | RK7 | L3M | +379 / +664 | +1227 | +553 / +969 | -2950 | c=1.00: +379 / +1227 / +553 | 162 | +0.021 | +0.262 | +0.28 / -0.09 / -0.04 | ok |
|  | RK7 | L6M | +306 / +536 | +1227 | +1023 / +1790 | -2950 | c=1.00: +306 / +1227 / +1023 | 337 | +0.035 | +0.436 | +0.30 / -0.05 / +0.01 | ok |
|  | RK7 | L3M | +2208 / +3863 | -5132 | +603 / +1055 | -4880 | c=1.00: +2208 / -5132 / +603 | 84 | +0.147 | +0.947 | +0.00 / +0.25 / +0.16 | AMBER |
|  | RK7 | L6M | +1336 / +2338 | -5132 | +822 / +1439 | -4880 | c=1.00: +1336 / -5132 / +822 | 194 | +0.110 | +0.793 | +0.07 / +0.15 / +0.20 | AMBER |
|  | RK7 | L3M | +1051 / +1839 | +745 | +1695 / +2966 | -6259 | c=1.00: +1051 / +745 / +1695 | 97 | +0.201 | +1.499 | +0.33 / +0.10 / +0.15 | AMBER |
|  | RK7 | L6M | +527 / +922 | +745 | +950 / +1662 | -6259 | c=1.00: +527 / +745 / +950 | 218 | +0.084 | +0.674 | +0.28 / +0.02 / +0.01 | AMBER |
|  | RK7 | L3M | +1972 / +3452 | -3233 | +1918 / +3357 | -4963 | c=1.00: +1972 / -3233 / +1918 | 72 | +0.119 | +0.658 | +0.06 / +0.26 / +0.32 | AMBER |
|  | RK7 | L6M | +1297 / +2269 | -3233 | +591 / +1034 | -4963 | c=1.00: +1297 / -3233 / +591 | 169 | -0.008 | -0.049 | +0.16 / +0.20 / +0.26 | AMBER |
|  | RK7 | L3M | +2378 / +4161 | -2433 | -302 / -529 | -8118 | c=1.00: +2378 / -2433 / -302 | 106 | -0.032 | -0.259 | +0.11 / +0.32 / +0.22 | AMBER |
|  | RK7 | L6M | +1496 / +2617 | -2433 | +839 / +1468 | -8118 | c=1.00: +1496 / -2433 / +839 | 263 | +0.058 | +0.561 | +0.03 / +0.14 / +0.19 | AMBER |
|  | RK7 | L3M | +588 / +1029 | -4275 | +692 / +1211 | +565 | c=1.00: +588 / -4275 / +692 | 59 | +0.027 | +0.122 | -0.01 / -0.24 / +0.02 | ok |
|  | RK7 | L6M | +464 / +812 | -4275 | +1427 / +2497 | +565 | c=1.00: +464 / -4275 / +1427 | 129 | +0.188 | +0.899 | +0.00 / -0.09 / +0.07 | ok |
|  | RK7 | L3M | +1153 / +2017 | -3400 | +2391 / +4184 | -3779 | c=1.00: +1153 / -3400 / +2391 | 56 | +0.417 | +1.795 | +0.05 / +0.11 / +0.26 | ok |
|  | RK7 | L6M | +1125 / +1969 | -4905 | +1417 / +2480 | -3779 | c=1.00: +1125 / -4905 / +1417 | 132 | +0.227 | +1.108 | +0.09 / +0.13 / +0.27 | ok |
|  | RK7 | L3M | +1239 / +2168 | -3985 | +326 / +570 | -4855 | c=1.00: +1239 / -3985 / +326 | 72 | +0.091 | +0.504 | +0.04 / -0.17 / +0.03 | AMBER |
|  | RK7 | L6M | +1170 / +2047 | -3985 | +227 / +396 | -4855 | c=1.00: +1170 / -3985 / +227 | 166 | +0.030 | +0.186 | -0.03 / -0.06 / +0.07 | AMBER |
|  | RK7 | L3M | -685 / -1198 | -3700 | +2740 / +4794 | +3072 | c=1.00: -685 / -3700 / +2740 | 258 | +0.148 | +2.935 | -0.04 / -0.36 / -0.34 | ok |
|  | RK7 | L3M | +2830 / +4952 | -3243 | -771 / -1349 | -10704 | c=1.00: +2830 / -3243 / -771 | 103 | -0.126 | -0.996 | +0.21 / +0.15 / +0.24 | RED |
|  | RK7 | L6M | +1735 / +3037 | -3243 | +316 / +554 | -10704 | c=1.00: +1735 / -3243 / +316 | 213 | +0.013 | +0.105 | +0.20 / +0.12 / +0.01 | RED |
|  | RK7 | L3M | +2242 / +3923 | -6920 | +632 / +1105 | -7811 | c=1.00: +2242 / -6920 / +632 | 91 | +0.063 | +0.444 | +0.09 / +0.01 / +0.10 | AMBER |
|  | RK7 | L6M | +1809 / +3166 | -7255 | +34 / +60 | -7811 | c=1.00: +1809 / -7255 / +34 | 197 | -0.007 | -0.053 | +0.04 / +0.04 / +0.06 | AMBER |
|  | RK7 | L3M | +2573 / +4503 | -4915 | +1892 / +3311 | -10073 | c=1.00: +2573 / -4915 / +1892 | 50 | +0.193 | +0.744 | -0.01 / +0.28 / +0.27 | RED |
|  | RK7 | L6M | +1637 / +2865 | -4915 | +1536 / +2688 | -10073 | c=1.00: +1637 / -4915 / +1536 | 113 | +0.199 | +0.831 | +0.03 / +0.22 / +0.26 | RED |
|  | RK7 | L3M | +5714 / +9999 | -8724 | +553 / +968 | -19101 | c=1.00: +5714 / -8724 / +553 | 116 | +0.036 | +0.324 | +0.05 / +0.25 / +0.31 | RED |
|  | RK7 | L6M | +3822 / +6688 | -8724 | +1631 / +2854 | -19101 | c=1.00: +3822 / -8724 / +1631 | 292 | +0.108 | +1.163 | +0.00 / +0.16 / +0.15 | RED |
|  | RK7 | L3M | +572 / +1001 | -6940 | +852 / +1491 | -1145 | c=1.00: +572 / -6940 / +852 | 60 | +0.187 | +0.865 | +0.22 / -0.10 / +0.14 | ok |
|  | RK7 | L6M | +645 / +1128 | -6940 | -294 / -515 | -1145 | c=1.00: +645 / -6940 / -294 | 144 | -0.056 | -0.300 | +0.12 / -0.05 / +0.17 | ok |
|  | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=1.00: -504 / -3120 / +2902 | 62 | +0.356 | +1.698 | +0.25 / -0.07 / +0.11 | ok |
|  | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=1.00: -58 / -3120 / +2291 | 136 | +0.327 | +1.650 | +0.06 / -0.03 / +0.02 | ok |
|  | RK7 | Y2023 | -1698 / -2972 | -7720 | -122 / -213 | -4200 | c=1.00: -1698 / -7720 / -122 | 182 | +0.096 | +0.448 | +0.07 / +0.04 / +0.23 | ok |
|  | RK7 | Y2024 | -1956 / -3423 | -882 | +670 / +1172 | +8949 | c=1.00: -1956 / -882 / +670 | 256 | +0.128 | +0.620 | -0.01 / +0.02 / +0.14 | ok |
|  | RK7 | Y2025 | -5837 / -10214 | +6385 | -137 / -239 | +13807 | c=1.00: -5837 / +6385 / -137 | 269 | +0.103 | +0.520 | +0.00 / -0.01 / +0.02 | ok |
|  | CT105p | L3M | +1432 / +2506 | -287 | +597 / +1045 | -4757 | c=1.00: +1432 / -287 / +597 | 59 | +0.015 | +0.069 | -0.12 / -0.27 / -0.10 | AMBER |
|  | CT105p | L6M | +886 / +1551 | -287 | +1178 / +2062 | -4757 | c=1.00: +886 / -287 / +1178 | 124 | +0.139 | +0.638 | -0.00 / -0.17 / -0.03 | AMBER |
|  | CT70p | L3M | +1761 / +3081 | -2035 | +781 / +1367 | -5894 | c=1.00: +1761 / -2035 / +781 | 57 | +0.071 | +0.313 | +0.04 / -0.12 / +0.23 | AMBER |
|  | CT7p | L3M | +845 / +1479 | -2567 | -103 / -181 | -2030 | c=1.00: +845 / -2567 / -103 | 62 | +0.035 | +0.165 | +0.03 / +0.02 / +0.01 | ok |
|  | RK7LO | L3M | +1728 / +3023 | -5925 | +1303 / +2280 | -8593 | c=1.00: +1728 / -5925 / +1303 | 53 | +0.110 | +0.447 | +0.02 / +0.01 / -0.14 | AMBER |
|  | RK7LO | L6M | +1429 / +2501 | -5925 | +46 / +81 | -8593 | c=1.00: +1429 / -5925 / +46 | 123 | -0.098 | -0.448 | +0.05 / +0.01 / +0.05 | AMBER |
|  | RK7LO | Y2023 | -2645 / -4628 | -5030 | -27 / -47 | -1140 | c=1.00: -2645 / -5030 / -27 | 182 | +0.113 | +0.527 | +0.05 / +0.13 / +0.07 | ok |
|  | RK7LO | Y2024 | -2407 / -4213 | +1242 | +783 / +1370 | +1321 | c=1.00: -2407 / +1242 / +783 | 238 | +0.168 | +0.754 | -0.05 / -0.03 / -0.13 | ok |
|  | RK7LO | Y2025 | +3581 / +6267 | -6699 | -719 / -1258 | -10694 | c=1.00: +3581 / -6699 / -719 | 264 | +0.014 | +0.067 | -0.01 / +0.04 / -0.07 | ok |
|  | RK7SO | L3M | +2130 / +3727 | -5067 | +405 / +709 | -5499 | c=1.00: +2130 / -5067 / +405 | 57 | -0.051 | -0.223 | +0.08 / -0.01 / +0.31 | AMBER |
|  | RK7SO | L6M | +1364 / +2387 | -5067 | +1324 / +2318 | -5499 | c=1.00: +1364 / -5067 / +1324 | 128 | +0.168 | +0.796 | +0.01 / -0.00 / +0.07 | AMBER |
|  | RK7 | L3M | +452 / +790 | -1208 | -317 / -555 | -785 | c=1.00: +452 / -1208 / -317 | 96 | -0.076 | -0.560 | +0.31 / +0.12 / +0.28 | ok |
|  | RK7 | L6M | +347 / +607 | -1208 | +776 / +1358 | -785 | c=1.00: +347 / -1208 / +776 | 185 | +0.045 | +0.309 | +0.16 / +0.03 / +0.11 | ok |
|  | RK7 | L3M | +148 / +260 | -3080 | +1607 / +2812 | +996 | c=1.00: +148 / -3080 / +1607 | 61 | +0.206 | +0.969 | +0.16 / -0.15 / +0.05 | ok |
|  | RK7 | L6M | +409 / +715 | -3815 | +2335 / +4087 | +996 | c=1.00: +409 / -3815 / +2335 | 132 | +0.373 | +1.825 | +0.01 / -0.07 / +0.03 | ok |
|  | RK7 | L3M | +1868 / +3269 | -5505 | +441 / +771 | -6718 | c=1.00: +1868 / -5505 / +441 | 141 | -0.039 | -0.428 | +0.02 / +0.11 / +0.17 | AMBER |
|  | RK7 | L6M | +1272 / +2226 | -5505 | +706 / +1235 | -6718 | c=1.00: +1272 / -5505 / +706 | 290 | +0.013 | +0.144 | -0.05 / +0.02 / +0.06 | AMBER |
|  | RK7 | L3M | +2706 / +4735 | -9015 | +1613 / +2823 | -12215 | c=1.00: +2706 / -9015 / +1613 | 127 | +0.111 | +1.086 | +0.13 / -0.00 / +0.20 | RED |
|  | RK7 | L6M | +1860 / +3255 | -9015 | +1741 / +3046 | -12215 | c=1.00: +1860 / -9015 / +1741 | 266 | +0.126 | +1.238 | +0.02 / +0.03 / +0.01 | RED |
|  | RK7 | L3M | +1188 / +2080 | -4065 | +1313 / +2298 | -2702 | c=1.00: +1188 / -4065 / +1313 | 59 | +0.069 | +0.313 | +0.11 / -0.02 / +0.26 | ok |
|  | RK7 | L6M | +732 / +1281 | -4065 | +1293 / +2262 | -2702 | c=1.00: +732 / -4065 / +1293 | 134 | +0.144 | +0.717 | +0.01 / -0.01 / +0.18 | ok |
|  | RK7 | L3M | +892 / +1561 | +969 | +1557 / +2726 | -3857 | c=1.00: +892 / +969 / +1557 | 70 | +0.273 | +1.469 | +0.16 / +0.22 / +0.25 | ok |
|  | RK7 | L6M | +634 / +1109 | +969 | +856 / +1497 | -3857 | c=1.00: +634 / +969 / +856 | 176 | +0.114 | +0.745 | +0.12 / +0.15 / +0.24 | ok |
|  | RK7 | L3M | +1461 / +2557 | -2202 | +713 / +1248 | -2182 | c=1.00: +1461 / -2202 / +713 | 198 | +0.005 | +0.076 | -0.02 / +0.03 / -0.04 | ok |
|  | RK7 | L3M | +1287 / +2252 | -3120 | +1800 / +3150 | -5514 | c=1.00: +1287 / -3120 / +1800 | 63 | +0.203 | +0.981 | +0.14 / -0.21 / +0.20 | AMBER |
|  | RK7 | L6M | +1052 / +1841 | -3870 | +1790 / +3133 | -5514 | c=1.00: +1052 / -3870 / +1790 | 141 | +0.249 | +1.299 | +0.08 / -0.07 / +0.08 | AMBER |
|  | RK7 | L3M | +1740 / +3045 | -4430 | +1010 / +1768 | -6959 | c=1.00: +1740 / -4430 / +1010 | 76 | +0.141 | +0.823 | -0.05 / -0.04 / -0.01 | AMBER |
|  | RK7 | L6M | +1277 / +2235 | -4430 | +1153 / +2017 | -6959 | c=1.00: +1277 / -4430 / +1153 | 172 | +0.130 | +0.827 | +0.03 / -0.03 / +0.16 | AMBER |
|  | RK7 | L3M | +811 / +1418 | -2650 | +1481 / +2593 | -3220 | c=1.00: +811 / -2650 / +1481 | 78 | +0.160 | +0.962 | -0.03 / +0.04 / -0.17 | ok |
|  | RK7 | L6M | +494 / +865 | -2650 | +1431 / +2505 | -3220 | c=1.00: +494 / -2650 / +1431 | 173 | +0.146 | +0.935 | +0.12 / +0.06 / -0.09 | ok |
|  | RK7 | L3M | +1220 / +2135 | -3440 | +347 / +607 | -2608 | c=1.00: +1220 / -3440 / +347 | 93 | -0.066 | -0.475 | +0.21 / +0.08 / +0.25 | ok |
|  | RK7 | L6M | +905 / +1584 | -3440 | +1083 / +1896 | -2608 | c=1.00: +905 / -3440 / +1083 | 200 | +0.051 | +0.380 | +0.07 / +0.09 / +0.20 | ok |
|  | RK7 | L3M | +2208 / +3863 | -1522 | +465 / +813 | -5294 | c=1.00: +2208 / -1522 / +465 | 112 | -0.003 | -0.029 | -0.06 / +0.30 / +0.35 | AMBER |
|  | RK7 | L6M | +1361 / +2382 | -1522 | +972 / +1701 | -5294 | c=1.00: +1361 / -1522 / +972 | 241 | +0.045 | +0.399 | +0.07 / +0.19 / +0.27 | AMBER |
|  | RK7 | L3M | +1568 / +2744 | -4530 | -809 / -1416 | -6564 | c=1.00: +1568 / -4530 / -809 | 59 | -0.230 | -1.044 | -0.03 / +0.00 / -0.16 | AMBER |
|  | RK7 | L6M | +1284 / +2247 | -4530 | -310 / -543 | -6564 | c=1.00: +1284 / -4530 / -310 | 139 | -0.119 | -0.612 | +0.05 / -0.02 / -0.04 | AMBER |
|  | RK7 | L3M | +3742 / +6549 | -6140 | -822 / -1438 | -12274 | c=1.00: +3742 / -6140 / -822 | 75 | -0.244 | -1.408 | -0.08 / -0.04 / +0.16 | RED |
|  | RK7 | L6M | +2440 / +4270 | -6140 | -150 / -263 | -12274 | c=1.00: +2440 / -6140 / -150 | 164 | -0.109 | -0.662 | -0.00 / -0.00 / +0.25 | RED |
|  | RK7 | L3M | +5937 / +10389 | -9553 | -635 / -1111 | -19250 | c=1.00: +5937 / -9553 / -635 | 111 | -0.090 | -0.765 | -0.01 / +0.27 / +0.41 | RED |
|  | RK7 | L6M | +3710 / +6492 | -9553 | +883 / +1545 | -19250 | c=1.00: +3710 / -9553 / +883 | 281 | +0.059 | +0.613 | +0.01 / +0.19 / +0.14 | RED |
|  | RK7 | L3M | +1084 / +1898 | -3190 | +352 / +616 | -4180 | c=1.00: +1084 / -3190 / +352 | 71 | +0.039 | +0.213 | -0.07 / -0.04 / +0.08 | ok |
|  | RK7 | L6M | +822 / +1438 | -3190 | +407 / +713 | -4180 | c=1.00: +822 / -3190 / +407 | 163 | +0.031 | +0.186 | -0.01 / -0.02 / +0.12 | ok |
|  | RK7 | L3M | +1877 / +3285 | -287 | +344 / +601 | -5881 | c=1.00: +1877 / -287 / +344 | 104 | +0.024 | +0.191 | +0.06 / +0.20 / +0.09 | AMBER |
|  | RK7 | L6M | +1467 / +2567 | -287 | +791 / +1384 | -5881 | c=1.00: +1467 / -287 / +791 | 263 | +0.060 | +0.586 | +0.14 / +0.15 / +0.02 | AMBER |
|  | RK7 | L3M | +5300 / +9275 | -9944 | +1018 / +1781 | -16481 | c=1.00: +5300 / -9944 / +1018 | 77 | +0.033 | +0.197 | -0.08 / +0.17 / +0.34 | RED |
|  | RK7 | L6M | +3247 / +5683 | -9944 | +1020 / +1785 | -16481 | c=1.00: +3247 / -9944 / +1020 | 166 | +0.082 | +0.504 | +0.03 / +0.15 / +0.23 | RED |
|  | RK7 | L3M | +554 / +969 | -3130 | +2238 / +3916 | -2449 | c=1.00: +554 / -3130 / +2238 | 63 | +0.246 | +1.193 | +0.19 / -0.09 / +0.13 | ok |
|  | RK7 | L6M | +397 / +695 | -3130 | +2143 / +3751 | -2449 | c=1.00: +397 / -3130 / +2143 | 134 | +0.295 | +1.462 | +0.10 / -0.07 / +0.13 | ok |
|  | RK7 | L3M | +2208 / +3863 | -1522 | +465 / +813 | -5294 | c=1.00: +2208 / -1522 / +465 | 112 | -0.003 | -0.029 | -0.06 / +0.30 / +0.35 | AMBER |
|  | RK7 | L6M | +1361 / +2382 | -1522 | +972 / +1701 | -5294 | c=1.00: +1361 / -1522 / +972 | 241 | +0.045 | +0.399 | +0.07 / +0.19 / +0.27 | AMBER |
|  | RK7 | L3M | +3766 / +6591 | -6054 | +908 / +1590 | -13173 | c=1.00: +3766 / -6054 / +908 | 90 | +0.045 | +0.314 | -0.09 / +0.43 / +0.16 | RED |
|  | RK7 | L6M | +2534 / +4435 | -6054 | +1482 / +2593 | -13173 | c=1.00: +2534 / -6054 / +1482 | 210 | +0.117 | +0.910 | -0.05 / +0.23 / +0.05 | RED |
|  | RK7 | L3M | +2945 / +5153 | -6070 | +190 / +332 | -10271 | c=1.00: +2945 / -6070 / +190 | 77 | +0.041 | +0.242 | +0.17 / +0.03 / +0.20 | RED |
|  | RK7 | L6M | +1977 / +3459 | -6070 | +63 / +111 | -10271 | c=1.00: +1977 / -6070 / +63 | 178 | -0.012 | -0.081 | +0.06 / +0.04 / +0.12 | RED |
|  | RK7 | L3M | +1835 / +3211 | -3522 | +590 / +1033 | -6107 | c=1.00: +1835 / -3522 / +590 | 69 | -0.042 | -0.223 | +0.11 / +0.12 / -0.10 | AMBER |
|  | RK7 | L6M | +1230 / +2153 | -3522 | +1694 / +2965 | -6107 | c=1.00: +1230 / -3522 / +1694 | 153 | +0.179 | +1.014 | +0.03 / +0.09 / +0.02 | AMBER |
|  | RK7 | L3M | +1654 / +2895 | -4220 | +760 / +1329 | -5427 | c=1.00: +1654 / -4220 / +760 | 74 | +0.083 | +0.470 | +0.25 / +0.15 / +0.18 | AMBER |
|  | RK7 | L6M | +1439 / +2518 | -6025 | +530 / +927 | -5427 | c=1.00: +1439 / -6025 / +530 | 175 | +0.048 | +0.313 | +0.12 / +0.09 / +0.18 | AMBER |
|  | RK7 | L3M | +3096 / +5418 | -8795 | +1163 / +2035 | -9101 | c=1.00: +3096 / -8795 / +1163 | 75 | +0.041 | +0.238 | +0.03 / +0.04 / +0.35 | AMBER |
|  | RK7 | L6M | +1970 / +3448 | -8795 | +1622 / +2838 | -9101 | c=1.00: +1970 / -8795 / +1622 | 158 | +0.156 | +0.912 | -0.03 / +0.01 / +0.14 | AMBER |
|  | RK7 | L3M | +2909 / +5092 | -6700 | +889 / +1556 | -11011 | c=1.00: +2909 / -6700 / +889 | 70 | +0.000 | +0.002 | -0.08 / +0.11 / +0.21 | RED |
|  | RK7 | L6M | +1869 / +3271 | -6700 | +1754 / +3069 | -11011 | c=1.00: +1869 / -6700 / +1754 | 166 | +0.149 | +0.916 | -0.03 / +0.08 / +0.09 | RED |
|  | RK7 | L3M | +1249 / +2186 | -5260 | +1475 / +2580 | -937 | c=1.00: +1249 / -5260 / +1475 | 54 | +0.193 | +0.801 | +0.31 / +0.27 / +0.43 | ok |
|  | RK7 | L6M | +1082 / +1893 | -5260 | +1825 / +3194 | -937 | c=1.00: +1082 / -5260 / +1825 | 115 | +0.290 | +1.237 | +0.17 / +0.17 / +0.35 | ok |
|  | RK7 | L3M | +1253 / +2193 | +2078 | +762 / +1333 | -2002 | c=1.00: +1253 / +2078 / +762 | 73 | +0.095 | +0.534 | +0.11 / +0.31 / +0.28 | ok |
|  | RK7 | L6M | +967 / +1691 | -1090 | +1486 / +2601 | -2002 | c=1.00: +967 / -1090 / +1486 | 179 | +0.172 | +1.140 | +0.12 / +0.20 / +0.29 | ok |
|  | RK7 | L3M | +249 / +435 | -1452 | +116 / +204 | +1612 | c=1.00: +249 / -1452 / +116 | 100 | +0.004 | +0.029 | +0.31 / +0.36 / +0.39 | ok |
|  | RK7 | L6M | +197 / +345 | -1452 | +906 / +1585 | +1612 | c=1.00: +197 / -1452 / +906 | 204 | +0.075 | +0.569 | +0.18 / +0.19 / +0.06 | ok |
|  | RK7 | L3M | +1760 / +3080 | -5570 | +142 / +249 | -7990 | c=1.00: +1760 / -5570 / +142 | 58 | -0.042 | -0.188 | +0.09 / +0.11 / -0.02 | AMBER |
|  | RK7 | L6M | +1347 / +2358 | -5570 | -332 / -580 | -7990 | c=1.00: +1347 / -5570 / -332 | 132 | -0.123 | -0.599 | +0.08 / +0.06 / -0.06 | AMBER |
|  | RK7 | L3M | +1301 / +2276 | -3535 | +203 / +354 | -4865 | c=1.00: +1301 / -3535 / +203 | 70 | +0.029 | +0.158 | +0.02 / -0.03 / -0.10 | AMBER |
|  | RK7 | L6M | +941 / +1646 | -3535 | +128 / +224 | -4865 | c=1.00: +941 / -3535 / +128 | 152 | +0.018 | +0.104 | +0.01 / +0.04 / +0.13 | AMBER |
|  | RK7 | L3M | +260 / +455 | -3190 | +722 / +1264 | +1326 | c=1.00: +260 / -3190 / +722 | 64 | +0.030 | +0.147 | +0.08 / -0.16 / +0.05 | ok |
|  | RK7 | L6M | +638 / +1117 | -6170 | +491 / +860 | +1326 | c=1.00: +638 / -6170 / +491 | 140 | +0.039 | +0.201 | +0.04 / -0.09 / +0.02 | ok |
|  | RK7 | L3M | +63 / +111 | +690 | +2912 / +5097 | +1537 | c=1.00: +63 / +690 / +2912 | 129 | +0.172 | +1.707 | +0.25 / +0.08 / +0.16 | ok |
|  | RK7 | L6M | +336 / +588 | -3010 | +1980 / +3464 | +1537 | c=1.00: +336 / -3010 / +1980 | 246 | +0.132 | +1.200 | +0.10 / +0.07 / +0.04 | ok |
|  | RK7 | L3M | +3886 / +6800 | -3535 | -50 / -87 | -12264 | c=1.00: +3886 / -3535 / -50 | 54 | -0.204 | -0.848 | -0.06 / +0.05 / +0.02 | RED |
|  | RK7 | L6M | +2484 / +4346 | -3535 | +259 / +453 | -12264 | c=1.00: +2484 / -3535 / +259 | 132 | -0.046 | -0.225 | +0.04 / -0.03 / +0.02 | RED |
|  | RK7 | L3M | +848 / +1484 | -5920 | +2149 / +3761 | -1844 | c=1.00: +848 / -5920 / +2149 | 60 | +0.308 | +1.420 | +0.20 / -0.02 / +0.06 | ok |
|  | RK7 | L6M | +808 / +1414 | -5920 | +2255 / +3946 | -1844 | c=1.00: +808 / -5920 / +2255 | 135 | +0.351 | +1.757 | +0.05 / +0.02 / +0.04 | ok |
|  | RK7 | L3M | +486 / +851 | -5108 | +2629 / +4602 | -2856 | c=1.00: +486 / -5108 / +2629 | 99 | +0.206 | +1.572 | +0.33 / -0.08 / +0.14 | ok |
|  | RK7 | L6M | +313 / +547 | -5108 | +1415 / +2475 | -2856 | c=1.00: +313 / -5108 / +1415 | 216 | +0.094 | +0.751 | +0.23 / -0.12 / -0.03 | ok |
|  | RK7 | L3M | +319 / +558 | -3045 | +1182 / +2069 | +1080 | c=1.00: +319 / -3045 / +1182 | 110 | +0.042 | +0.356 | +0.31 / +0.09 / +0.19 | ok |
|  | RK7 | L3M | +1089 / +1905 | -6775 | +2671 / +4674 | -2023 | c=1.00: +1089 / -6775 / +2671 | 65 | +0.358 | +1.789 | +0.15 / +0.30 / +0.25 | ok |
|  | RK7 | L6M | +1031 / +1805 | -6775 | +544 / +952 | -2023 | c=1.00: +1031 / -6775 / +544 | 146 | +0.042 | +0.227 | +0.03 / +0.15 / +0.15 | ok |
|  | RK7 | L3M | +250 / +437 | -4905 | +2403 / +4204 | +952 | c=1.00: +250 / -4905 / +2403 | 67 | +0.217 | +1.118 | +0.04 / +0.02 / +0.00 | ok |
|  | RK7 | L6M | +240 / +419 | -4905 | +2329 / +4075 | +952 | c=1.00: +240 / -4905 / +2329 | 140 | +0.267 | +1.386 | +0.03 / -0.00 / +0.15 | ok |
|  | RK7 | L3M | +3305 / +5784 | -4928 | -334 / -584 | -11231 | c=1.00: +3305 / -4928 / -334 | 80 | -0.022 | -0.134 | +0.01 / +0.19 / +0.17 | RED |
|  | RK7 | L6M | +2040 / +3571 | -4928 | +694 / +1215 | -11231 | c=1.00: +2040 / -4928 / +694 | 177 | +0.082 | +0.537 | -0.05 / +0.15 / +0.10 | RED |
|  | RK7 | L3M | -141 / -247 | +1770 | +2175 / +3806 | +684 | c=1.00: -141 / +1770 / +2175 | 69 | +0.322 | +1.706 | +0.11 / +0.08 / +0.24 | ok |
|  | RK7 | L6M | +250 / +438 | -3605 | +1463 / +2560 | +684 | c=1.00: +250 / -3605 / +1463 | 173 | +0.174 | +1.118 | +0.10 / +0.06 / +0.31 | ok |
|  | RK7 | L3M | +1760 / +3080 | -5895 | +1447 / +2532 | -8936 | c=1.00: +1760 / -5895 / +1447 | 53 | +0.139 | +0.567 | -0.08 / -0.07 / -0.16 | AMBER |
|  | RK7 | L6M | +1450 / +2537 | -5895 | +162 / +283 | -8936 | c=1.00: +1450 / -5895 / +162 | 124 | -0.077 | -0.351 | +0.02 / -0.05 / +0.06 | AMBER |
|  | RK7 | L3M | +3907 / +6837 | -8129 | +171 / +300 | -13843 | c=1.00: +3907 / -8129 / +171 | 99 | +0.025 | +0.193 | +0.23 / +0.39 / +0.40 | RED |
|  | RK7 | L3M | +3633 / +6358 | -3535 | +162 / +284 | -11404 | c=1.00: +3633 / -3535 / +162 | 55 | -0.148 | -0.626 | -0.13 / +0.10 / +0.03 | RED |
|  | RK7 | L6M | +2327 / +4073 | -3535 | +283 / +496 | -11404 | c=1.00: +2327 / -3535 / +283 | 130 | -0.032 | -0.155 | +0.01 / +0.00 / +0.06 | RED |
|  | RK7 | L3M | -141 / -247 | +1770 | +2175 / +3806 | +684 | c=1.00: -141 / +1770 / +2175 | 69 | +0.322 | +1.706 | +0.11 / +0.08 / +0.24 | ok |
|  | RK7 | L6M | +250 / +438 | -3605 | +1463 / +2560 | +684 | c=1.00: +250 / -3605 / +1463 | 173 | +0.174 | +1.118 | +0.10 / +0.06 / +0.31 | ok |
|  | RK7 | L3M | +2728 / +4774 | -5935 | +1639 / +2869 | -9857 | c=1.00: +2728 / -5935 / +1639 | 65 | +0.174 | +0.871 | +0.16 / +0.14 / +0.33 | RED |
|  | RK7 | L6M | +1955 / +3422 | -5935 | +1280 / +2240 | -9857 | c=1.00: +1955 / -5935 / +1280 | 146 | +0.155 | +0.839 | +0.04 / +0.08 / +0.21 | RED |
|  | RK7 | L3M | +2728 / +4774 | -5935 | +1639 / +2869 | -9857 | c=1.00: +2728 / -5935 / +1639 | 65 | +0.174 | +0.871 | +0.16 / +0.14 / +0.33 | RED |
|  | RK7 | L6M | +1955 / +3422 | -5935 | +1280 / +2240 | -9857 | c=1.00: +1955 / -5935 / +1280 | 146 | +0.155 | +0.839 | +0.04 / +0.08 / +0.21 | RED |
|  | RK7 | L3M | +2121 / +3712 | -5705 | +129 / +226 | -7663 | c=1.00: +2121 / -5705 / +129 | 146 | -0.017 | -0.191 | +0.04 / +0.12 / +0.15 | AMBER |
|  | RK7 | L6M | +1502 / +2629 | -5705 | +496 / +867 | -7663 | c=1.00: +1502 / -5705 / +496 | 365 | +0.012 | +0.166 | -0.03 / +0.11 / +0.03 | AMBER |
|  | RK7 | L3M | +1430 / +2502 | -2808 | +1195 / +2091 | -1849 | c=1.00: +1430 / -2808 / +1195 | 83 | +0.105 | +0.671 | +0.02 / +0.23 / +0.19 | ok |
|  | RK7 | L6M | +859 / +1504 | -2808 | +2164 / +3786 | -1849 | c=1.00: +859 / -2808 / +2164 | 195 | +0.206 | +1.489 | +0.05 / +0.17 / +0.05 | ok |
|  | RK7 | L3M | +1796 / +3143 | -8015 | -565 / -989 | -6500 | c=1.00: +1796 / -8015 / -565 | 81 | -0.011 | -0.067 | +0.11 / -0.10 / +0.00 | AMBER |
|  | RK7 | L6M | +1362 / +2384 | -8015 | +613 / +1072 | -6500 | c=1.00: +1362 / -8015 / +613 | 187 | +0.093 | +0.641 | +0.05 / -0.07 / +0.10 | AMBER |
|  | RK7 | L3M | +2277 / +3985 | -7880 | +1335 / +2336 | -5741 | c=1.00: +2277 / -7880 / +1335 | 65 | +0.111 | +0.554 | +0.05 / +0.08 / +0.21 | AMBER |
|  | RK7 | L6M | +1636 / +2863 | -7880 | -828 / -1449 | -5741 | c=1.00: +1636 / -7880 / -828 | 154 | -0.188 | -1.073 | -0.00 / +0.06 / +0.07 | AMBER |
|  | RK7 | L3M | +1606 / +2810 | -3535 | +80 / +140 | -4865 | c=1.00: +1606 / -3535 / +80 | 69 | +0.008 | +0.043 | +0.18 / -0.13 / +0.10 | AMBER |
|  | RK7 | L6M | +1095 / +1917 | -3535 | +392 / +685 | -4865 | c=1.00: +1095 / -3535 / +392 | 153 | +0.056 | +0.318 | +0.08 / +0.01 / +0.16 | AMBER |
|  | RK7 | L3M | +1218 / +2131 | -6270 | +1409 / +2465 | -4422 | c=1.00: +1218 / -6270 / +1409 | 57 | +0.104 | +0.454 | +0.13 / -0.06 / +0.08 | ok |
|  | RK7 | L6M | +844 / +1477 | -6270 | +1048 / +1833 | -4422 | c=1.00: +844 / -6270 / +1048 | 118 | +0.084 | +0.369 | +0.11 / -0.04 / +0.14 | ok |
|  | RK7 | L3M | +1461 / +2557 | -2202 | +713 / +1248 | -2182 | c=1.00: +1461 / -2202 / +713 | 198 | +0.005 | +0.076 | -0.02 / +0.03 / -0.04 | ok |
|  | RK7 | L3M | +1538 / +2692 | -100 | +2236 / +3913 | -5954 | c=1.00: +1538 / -100 / +2236 | 60 | +0.335 | +1.547 | +0.06 / -0.20 / +0.17 | AMBER |
|  | RK7 | L6M | +1043 / +1825 | -100 | +2899 / +5073 | -5954 | c=1.00: +1043 / -100 / +2899 | 135 | +0.437 | +2.185 | -0.08 / -0.05 / +0.09 | AMBER |
|  | RK7 | L3M | +624 / +1092 | -2955 | +1718 / +3006 | -493 | c=1.00: +624 / -2955 / +1718 | 120 | +0.107 | +0.988 | +0.13 / +0.10 / +0.04 | ok |
|  | RK7 | L6M | +476 / +833 | -2955 | +1545 / +2705 | -493 | c=1.00: +476 / -2955 / +1545 | 251 | +0.109 | +1.011 | +0.07 / +0.09 / -0.03 | ok |
|  | RH7 | L3M | -798 / -1396 | -261 | +681 / +1192 | +1720 | c=1.00: -798 / -261 / +681 | 76 | +0.095 | +0.558 | +0.16 / +0.03 / -0.08 | ok |
|  | RH7 | L6M | -360 / -630 | -261 | +313 / +548 | +1720 | c=1.00: -360 / -261 / +313 | 168 | +0.045 | +0.283 | +0.20 / +0.00 / +0.02 | ok |
|  | RK7 | L3M | -620 / -1085 | -1005 | +1301 / +2278 | +1164 | c=1.00: -620 / -1005 / +1301 | 76 | +0.095 | +0.558 | +0.16 / +0.03 / -0.08 | ok |
|  | RK7 | L6M | -178 / -311 | -1005 | +919 / +1609 | +1164 | c=1.00: -178 / -1005 / +919 | 169 | +0.045 | +0.283 | +0.20 / +0.00 / +0.02 | ok |
|  | RK7 | Y2023 | -821 / -1437 | -870 | +608 / +1064 | -6373 | c=1.00: -821 / -870 / +608 | 206 | +0.200 | +1.056 | +0.09 / +0.02 / +0.20 | AMBER |
|  | RK7 | Y2024 | +3001 / +5252 | +1242 | +751 / +1315 | +2326 | c=1.00: +3001 / +1242 / +751 | 343 | +0.125 | +0.809 | +0.07 / -0.00 / +0.10 | ok |
|  | RK7 | Y2025 | +1003 / +1756 | -185 | +510 / +892 | -2451 | c=1.00: +1003 / -185 / +510 | 366 | +0.157 | +1.087 | +0.01 / +0.08 / +0.06 | ok |
|  | CT105p | L3M | +1673 / +2928 | -2053 | +1796 / +3143 | -6960 | c=1.00: +1673 / -2053 / +1796 | 76 | +0.101 | +0.589 | -0.04 / +0.04 / +0.12 | AMBER |
|  | CT105p | L6M | +1060 / +1854 | -2053 | -8 / -14 | -6960 | c=1.00: +1060 / -2053 / -8 | 156 | -0.099 | -0.575 | -0.09 / +0.05 / +0.01 | AMBER |
|  | CT14m | L3M | +1694 / +2964 | -6180 | +980 / +1715 | -5207 | c=1.00: +1694 / -6180 / +980 | 74 | -0.009 | -0.051 | -0.17 / -0.01 / -0.25 | AMBER |
|  | CT14m | L6M | +1373 / +2403 | -6180 | +635 / +1112 | -5207 | c=1.00: +1373 / -6180 / +635 | 160 | -0.020 | -0.120 | -0.06 / +0.03 / -0.10 | AMBER |
|  | CT14p | L3M | +3536 / +6188 | -6915 | -702 / -1228 | -12607 | c=1.00: +3536 / -6915 / -702 | 72 | -0.134 | -0.740 | -0.07 / -0.07 / -0.15 | RED |
|  | CT14p | L6M | +2265 / +3964 | -6915 | +638 / +1116 | -12607 | c=1.00: +2265 / -6915 / +638 | 149 | +0.041 | +0.226 | +0.06 / +0.04 / -0.02 | RED |
|  | CT21m | L3M | +877 / +1534 | -3408 | +1652 / +2891 | -2531 | c=1.00: +877 / -3408 / +1652 | 67 | +0.140 | +0.720 | +0.24 / -0.06 / +0.26 | ok |
|  | CT21p | L3M | +4235 / +7411 | -6323 | -1523 / -2665 | -13698 | c=1.00: +4235 / -6323 / -1523 | 69 | -0.265 | -1.407 | -0.16 / +0.17 / -0.05 | RED |
|  | CT28m | L3M | +1639 / +2869 | -1858 | -1236 / -2164 | -2367 | c=1.00: +1639 / -1858 / -1236 | 62 | -0.334 | -1.595 | +0.13 / +0.13 / -0.06 | ok |
|  | CT28m | L6M | +1146 / +2006 | -1858 | -743 / -1301 | -2367 | c=1.00: +1146 / -1858 / -743 | 146 | -0.214 | -1.155 | -0.14 / +0.03 / -0.12 | ok |
|  | CT28p | L3M | +1495 / +2617 | -1888 | +583 / +1020 | -6937 | c=1.00: +1495 / -1888 / +583 | 70 | +0.082 | +0.444 | -0.02 / +0.05 / -0.07 | AMBER |
|  | CT28p | L6M | +1096 / +1918 | -1888 | -220 / -385 | -6937 | c=1.00: +1096 / -1888 / -220 | 159 | -0.069 | -0.408 | +0.01 / +0.06 / -0.15 | AMBER |
|  | CT35m | L3M | +894 / +1565 | -1508 | +386 / +676 | +198 | c=1.00: +894 / -1508 / +386 | 49 | +0.004 | +0.015 | -0.23 / -0.18 / -0.13 | ok |
|  | CT35m | L6M | +706 / +1236 | -1508 | +93 / +163 | +47 | c=1.00: +706 / -1508 / +93 | 127 | -0.058 | -0.273 | -0.08 / -0.13 / +0.04 | ok |
|  | CT35p | L3M | +3134 / +5484 | -6194 | +845 / +1478 | -12216 | c=1.00: +3134 / -6194 / +845 | 64 | +0.072 | +0.355 | -0.12 / -0.19 / -0.11 | RED |
|  | CT35p | L6M | +2210 / +3867 | -6194 | +541 / +946 | -12216 | c=1.00: +2210 / -6194 / +541 | 154 | +0.020 | +0.112 | -0.04 / -0.14 / -0.02 | RED |
|  | CT42m | L3M | +826 / +1445 | -778 | -335 / -587 | +103 | c=1.00: +826 / -778 / -335 | 49 | -0.183 | -0.690 | +0.16 / +0.15 / +0.11 | ok |
|  | CT42m | L6M | +642 / +1123 | -778 | +718 / +1257 | -478 | c=1.00: +642 / -778 / +718 | 130 | +0.045 | +0.219 | -0.04 / -0.00 / -0.11 | ok |
|  | CT42p | L3M | -877 / -1534 | -317 | +1687 / +2953 | +2747 | c=1.00: -877 / -317 / +1687 | 72 | +0.224 | +1.241 | +0.14 / -0.20 / -0.03 | ok |
|  | CT42p | L6M | -482 / -843 | -317 | +1284 / +2248 | +2747 | c=1.00: -482 / -317 / +1284 | 160 | +0.133 | +0.786 | +0.10 / -0.06 / -0.10 | ok |
|  | CT49m | L3M | +3123 / +5465 | -2008 | +928 / +1623 | -10263 | c=1.00: +3123 / -2008 / +928 | 47 | +0.114 | +0.411 | -0.35 / -0.24 / -0.14 | RED |
|  | CT49p | L3M | +754 / +1319 | -327 | +654 / +1145 | -482 | c=1.00: +754 / -327 / +654 | 70 | -0.034 | -0.184 | -0.15 / -0.00 / -0.03 | ok |
|  | CT49p | L6M | +595 / +1042 | -327 | -464 / -812 | -482 | c=1.00: +595 / -327 / -464 | 157 | -0.168 | -0.979 | -0.09 / +0.00 / -0.05 | ok |
|  | CT56m | L3M | +3901 / +6827 | -8409 | -620 / -1085 | -11556 | c=1.00: +3901 / -8409 / -620 | 38 | -0.217 | -0.633 | +0.06 / +0.02 / +0.33 | RED |
|  | CT56m | L6M | +2457 / +4299 | -8409 | -336 / -588 | -11556 | c=1.00: +2457 / -8409 / -336 | 118 | -0.130 | -0.568 | +0.06 / +0.01 / +0.24 | RED |
|  | CT56p | L3M | +2060 / +3605 | -2524 | -737 / -1290 | -6979 | c=1.00: +2060 / -2524 / -737 | 65 | -0.168 | -0.840 | +0.15 / +0.03 / +0.00 | AMBER |
|  | CT56p | L6M | +1248 / +2184 | -2524 | -920 / -1610 | -6979 | c=1.00: +1248 / -2524 / -920 | 162 | -0.168 | -1.008 | +0.21 / -0.00 / +0.13 | AMBER |
|  | CT63m | L3M | +1769 / +3096 | -5081 | +668 / +1169 | -5040 | c=1.00: +1769 / -5081 / +668 | 29 | +0.167 | +0.373 | +0.03 / -0.09 / +0.02 | AMBER |
|  | CT63p | L3M | +2312 / +4046 | -5236 | +1309 / +2292 | -8289 | c=1.00: +2312 / -5236 / +1309 | 67 | +0.100 | +0.515 | +0.31 / +0.07 / +0.23 | AMBER |
|  | CT63p | L6M | +1385 / +2424 | -5236 | +573 / +1002 | -8289 | c=1.00: +1385 / -5236 / +573 | 156 | +0.012 | +0.068 | +0.17 / +0.03 / +0.15 | AMBER |
|  | CT70m | L3M | +2434 / +4260 | -5046 | -117 / -204 | -8260 | c=1.00: +2434 / -5046 / -117 | 28 | +0.024 | +0.051 | -0.04 / -0.12 / -0.10 | AMBER |
|  | CT70m | L6M | +1521 / +2661 | -5046 | +934 / +1634 | -8260 | c=1.00: +1521 / -5046 / +934 | 107 | +0.161 | +0.636 | +0.07 / +0.06 / -0.10 | AMBER |
|  | CT70p | L3M | +649 / +1135 | +1073 | -486 / -851 | -2944 | c=1.00: +649 / +1073 / -486 | 70 | -0.055 | -0.294 | +0.42 / +0.14 / +0.22 | ok |
|  | CT70p | L6M | +404 / +706 | +1073 | -542 / -949 | -2944 | c=1.00: +404 / +1073 / -542 | 164 | -0.094 | -0.569 | +0.18 / +0.08 / +0.06 | ok |
|  | CT77m | L3M | +3129 / +5476 | -4002 | -683 / -1196 | -9554 | c=1.00: +3129 / -4002 / -683 | 18 | -0.495 | -0.685 | -0.14 / -0.17 / +0.02 | RED |
|  | CT77m | L6M | +2210 / +3867 | -4002 | -1775 / -3107 | -9554 | c=1.00: +2210 / -4002 / -1775 | 106 | -0.448 | -1.758 | -0.07 / -0.10 / -0.07 | RED |
|  | CT77p | L3M | -142 / -248 | -84 | +885 / +1548 | -422 | c=1.00: -142 / -84 / +885 | 70 | +0.009 | +0.046 | +0.14 / -0.22 / +0.10 | ok |
|  | CT77p | L6M | +334 / +584 | -84 | +79 / +137 | -1848 | c=1.00: +334 / -84 / +79 | 156 | -0.088 | -0.506 | +0.13 / -0.15 / +0.16 | ok |
|  | CT7m | L3M | +3945 / +6904 | -6339 | -1312 / -2296 | -14140 | c=1.00: +3945 / -6339 / -1312 | 73 | -0.208 | -1.170 | -0.07 / -0.08 / +0.03 | RED |
|  | CT7m | L6M | +2762 / +4834 | -6339 | -131 / -229 | -14140 | c=1.00: +2762 / -6339 / -131 | 152 | -0.069 | -0.386 | +0.07 / -0.02 / +0.15 | RED |
|  | CT7p | L3M | +1132 / +1981 | -2117 | +597 / +1045 | -2365 | c=1.00: +1132 / -2117 / +597 | 75 | +0.080 | +0.460 | -0.16 / -0.10 / -0.13 | ok |
|  | CT7p | L6M | +689 / +1206 | -2117 | +573 / +1002 | -2365 | c=1.00: +689 / -2117 / +573 | 165 | +0.045 | +0.272 | +0.00 / -0.00 / -0.13 | ok |
|  | CT84m | L3M | +2218 / +3881 | -4002 | +609 / +1065 | -7596 | c=1.00: +2218 / -4002 / +609 | 15 | +0.537 | +0.619 | -0.05 / -0.18 / -0.16 | AMBER |
|  | CT84m | L6M | +1505 / +2634 | -4002 | +1014 / +1775 | -7596 | c=1.00: +1505 / -4002 / +1014 | 105 | +0.185 | +0.718 | +0.16 / -0.02 / -0.13 | AMBER |
|  | CT84p | L3M | +1619 / +2833 | -3513 | -2444 / -4277 | -2077 | c=1.00: +1619 / -3513 / -2444 | 70 | -0.405 | -2.179 | -0.03 / -0.11 / -0.02 | AMBER |
|  | CT84p | L6M | +1352 / +2367 | -3513 | -2422 / -4238 | -2077 | c=1.00: +1352 / -3513 / -2422 | 158 | -0.374 | -2.191 | +0.01 / -0.09 / +0.02 | ok |
|  | CT91m | L3M | +2404 / +4207 | -4002 | -538 / -942 | -7596 | c=1.00: +2404 / -4002 / -538 | 10 | -0.662 | -0.509 | -0.20 / -0.23 / -0.15 | AMBER |
|  | CT91p | L3M | -96 / -168 | -802 | +1276 / +2234 | +2262 | c=1.00: -96 / -802 / +1276 | 69 | +0.034 | +0.182 | +0.34 / -0.01 / +0.21 | ok |
|  | CT91p | L6M | -4 / -7 | -802 | +61 / +106 | +2262 | c=1.00: -4 / -802 / +61 | 151 | -0.105 | -0.587 | +0.16 / +0.02 / +0.14 | ok |
|  | CT98m | L3M | +2399 / +4199 | -4002 | -142 / -248 | -7596 | c=1.00: +2399 / -4002 / -142 | 6 | -0.387 | -0.179 | +0.10 / -0.01 / +0.24 | AMBER |
|  | CT98m | L6M | +1610 / +2818 | -4002 | +405 / +709 | -7596 | c=1.00: +1610 / -4002 / +405 | 85 | +0.057 | +0.180 | +0.11 / -0.01 / -0.00 | AMBER |
|  | CT98p | L3M | +2469 / +4321 | -1933 | +141 / +248 | -8743 | c=1.00: +2469 / -1933 / +141 | 70 | -0.145 | -0.781 | -0.10 / +0.13 / +0.03 | AMBER |
|  | CT98p | L6M | +1594 / +2790 | -1933 | +212 / +371 | -8743 | c=1.00: +1594 / -1933 / +212 | 147 | -0.089 | -0.485 | -0.04 / +0.03 / +0.19 | AMBER |
|  | RK7LO | L3M | +329 / +576 | -880 | +74 / +129 | -1231 | c=1.00: +329 / -880 / +74 | 60 | -0.028 | -0.128 | +0.17 / -0.12 / -0.12 | ok |
|  | RK7LO | L6M | +302 / +528 | -880 | -309 / -541 | -1231 | c=1.00: +302 / -880 / -309 | 124 | -0.122 | -0.561 | +0.18 / -0.09 / -0.07 | ok |
|  | RK7SO | L3M | +874 / +1530 | -4126 | +363 / +635 | -2810 | c=1.00: +874 / -4126 / +363 | 44 | -0.033 | -0.113 | +0.01 / +0.05 / -0.03 | ok |
|  | RK7SO | L6M | +649 / +1135 | -4126 | +940 / +1645 | -2810 | c=1.00: +649 / -4126 / +940 | 97 | +0.131 | +0.470 | +0.09 / +0.02 / +0.04 | ok |
|  | RM7 | L3M | -967 / -1692 | -340 | +84 / +148 | +2089 | c=1.00: -967 / -340 / +84 | 76 | +0.095 | +0.558 | +0.16 / +0.03 / -0.08 | ok |
|  | RM7 | L6M | -610 / -1067 | -340 | +112 / +195 | +2089 | c=1.00: -610 / -340 / +112 | 168 | +0.045 | +0.283 | +0.20 / +0.00 / +0.02 | ok |
|  | RP7 | L3M | -1386 / -2425 | +484 | +424 / +742 | +4475 | c=1.00: -1386 / +484 / +424 | 75 | +0.070 | +0.404 | +0.12 / +0.03 / -0.10 | ok |
|  | RP7 | L6M | -684 / -1196 | +484 | +152 / +266 | +4245 | c=1.00: -684 / +484 / +152 | 167 | +0.034 | +0.209 | +0.18 / +0.01 / +0.02 | ok |
|  | RP7 | Y2023 | -2337 / -4089 | -522 | +900 / +1574 | -6090 | c=1.00: -2337 / -522 / +900 | 206 | +0.200 | +1.056 | +0.09 / +0.02 / +0.20 | ok |
|  | RP7 | Y2024 | +3403 / +5956 | +3168 | +1234 / +2160 | +90 | c=1.00: +3403 / +3168 / +1234 | 341 | +0.127 | +0.817 | +0.07 / -0.00 / +0.10 | ok |
|  | RP7 | Y2025 | -2902 / -5079 | -4677 | +1437 / +2514 | +979 | c=1.00: -2902 / -4677 / +1437 | 365 | +0.159 | +1.092 | +0.01 / +0.08 / +0.06 | ok |
|  | CT14p | L3M | +1416 / +2478 | -3201 | -2098 / -3671 | -6555 | c=1.00: +1416 / -3201 / -2098 | 70 | -0.119 | -0.642 | -0.04 / -0.07 / -0.14 | AMBER |
|  | CT14p | L6M | +866 / +1515 | -3201 | -122 / -214 | -6555 | c=1.00: +866 / -3201 / -122 | 146 | +0.058 | +0.311 | +0.07 / +0.04 / -0.02 | AMBER |
|  | CT21p | L3M | +2609 / +4565 | -5855 | -3205 / -5608 | -9325 | c=1.00: +2609 / -5855 / -3205 | 68 | -0.246 | -1.286 | -0.17 / +0.16 / -0.07 | AMBER |
|  | CT21p | L6M | +1724 / +3018 | -5855 | -1691 / -2960 | -9325 | c=1.00: +1724 / -5855 / -1691 | 158 | -0.140 | -0.819 | +0.02 / +0.15 / +0.14 | AMBER |
|  | CT28p | L3M | +884 / +1547 | +304 | -941 / -1647 | -5485 | c=1.00: +884 / +304 / -941 | 69 | +0.111 | +0.592 | +0.01 / +0.05 / -0.06 | AMBER |
|  | CT28p | L6M | +638 / +1117 | +304 | -1248 / -2184 | -5485 | c=1.00: +638 / +304 / -1248 | 158 | -0.058 | -0.337 | +0.03 / +0.06 / -0.14 | AMBER |
|  | CT35p | L3M | +2073 / +3627 | -5725 | -192 / -336 | -9581 | c=1.00: +2073 / -5725 / -192 | 64 | +0.072 | +0.355 | -0.12 / -0.19 / -0.11 | RED |
|  | CT35p | L6M | +1522 / +2663 | -5725 | -356 / -624 | -9581 | c=1.00: +1522 / -5725 / -356 | 154 | +0.020 | +0.112 | -0.04 / -0.14 / -0.02 | RED |
|  | CT42p | L3M | -1874 / -3280 | +3133 | +477 / +835 | +6197 | c=1.00: -1874 / +3133 / +477 | 69 | +0.261 | +1.386 | +0.16 / -0.21 / -0.01 | ok |
|  | CT42p | L6M | -1067 / -1868 | +3133 | +345 / +604 | +6197 | c=1.00: -1067 / +3133 / +345 | 157 | +0.147 | +0.856 | +0.10 / -0.06 / -0.10 | ok |
|  | CT49p | L3M | -1595 / -2791 | +3124 | -785 / -1374 | +6188 | c=1.00: -1595 / +3124 / -785 | 66 | -0.029 | -0.147 | -0.17 / -0.06 / -0.02 | ok |
|  | CT49p | L6M | -798 / -1396 | +1644 | -1478 / -2587 | +6188 | c=1.00: -798 / +1644 / -1478 | 153 | -0.170 | -0.962 | -0.10 / -0.03 / -0.04 | ok |
|  | CT56p | L3M | -23 / -39 | -2055 | -1842 / -3223 | +364 | c=1.00: -23 / -2055 / -1842 | 64 | -0.168 | -0.825 | +0.15 / +0.03 / +0.00 | ok |
|  | CT56p | L6M | -70 / -123 | -2055 | -1763 / -3086 | +364 | c=1.00: -70 / -2055 / -1763 | 160 | -0.172 | -1.021 | +0.21 / -0.00 / +0.13 | ok |
|  | CT63p | L3M | -351 / -613 | -606 | -156 / -273 | +1580 | c=1.00: -351 / -606 / -156 | 66 | +0.132 | +0.669 | +0.34 / +0.06 / +0.24 | ok |
|  | CT63p | L6M | -330 / -577 | -606 | -383 / -670 | +1580 | c=1.00: -330 / -606 / -383 | 154 | +0.024 | +0.138 | +0.19 / +0.03 / +0.16 | ok |
|  | CT7p | L3M | -221 / -387 | +599 | -14 / -24 | +1705 | c=1.00: -221 / +599 / -14 | 73 | +0.091 | +0.510 | -0.15 / -0.10 / -0.13 | ok |
|  | CT7p | L6M | -179 / -313 | +599 | -99 / -174 | +1705 | c=1.00: -179 / +599 / -99 | 163 | +0.049 | +0.296 | +0.01 / -0.00 / -0.13 | ok |
|  | RK7 | L3M | +148 / +260 | -3080 | +1607 / +2812 | +996 | c=1.00: +148 / -3080 / +1607 | 61 | +0.206 | +0.969 | +0.16 / -0.15 / +0.05 | ok |
|  | RK7 | L6M | +409 / +715 | -3815 | +2335 / +4087 | +996 | c=1.00: +409 / -3815 / +2335 | 132 | +0.373 | +1.825 | +0.01 / -0.07 / +0.03 | ok |
|  | RK7 | L3M | +3907 / +6837 | -8129 | +171 / +300 | -13843 | c=1.00: +3907 / -8129 / +171 | 99 | +0.025 | +0.193 | +0.23 / +0.39 / +0.40 | RED |
|  | RK7 | L3M | +2830 / +4952 | -3243 | -771 / -1349 | -10704 | c=1.00: +2830 / -3243 / -771 | 103 | -0.126 | -0.996 | +0.21 / +0.15 / +0.24 | RED |
|  | RK7 | L6M | +1735 / +3037 | -3243 | +316 / +554 | -10704 | c=1.00: +1735 / -3243 / +316 | 213 | +0.013 | +0.105 | +0.20 / +0.12 / +0.01 | RED |
|  | RK7 | L3M | +4003 / +7005 | -8959 | -1005 / -1760 | -14304 | c=1.00: +4003 / -8959 / -1005 | 104 | -0.090 | -0.719 | +0.10 / +0.19 / +0.30 | RED |
|  | RK7 | L6M | +2498 / +4372 | -8959 | +1313 / +2298 | -14304 | c=1.00: +2498 / -8959 / +1313 | 252 | +0.109 | +1.018 | +0.02 / +0.13 / +0.16 | RED |
|  | RK7 | L3M | +3886 / +6800 | -3535 | -50 / -87 | -12264 | c=1.00: +3886 / -3535 / -50 | 54 | -0.204 | -0.848 | -0.06 / +0.05 / +0.02 | RED |
|  | RK7 | L6M | +2484 / +4346 | -3535 | +259 / +453 | -12264 | c=1.00: +2484 / -3535 / +259 | 132 | -0.046 | -0.225 | +0.04 / -0.03 / +0.02 | RED |
|  | RK7 | L3M | +1518 / +2657 | -2515 | +1344 / +2352 | -3099 | c=1.00: +1518 / -2515 / +1344 | 69 | +0.166 | +0.883 | -0.09 / +0.07 / +0.08 | ok |
|  | RK7 | L6M | +1268 / +2219 | -4165 | +1164 / +2036 | -3099 | c=1.00: +1268 / -4165 / +1164 | 159 | +0.126 | +0.741 | -0.09 / +0.06 / +0.01 | ok |
|  | RK7 | L3M | +2184 / +3821 | -5580 | -501 / -876 | -4008 | c=1.00: +2184 / -5580 / -501 | 63 | -0.071 | -0.344 | -0.14 / +0.13 / -0.09 | AMBER |
|  | RK7 | L6M | +1382 / +2418 | -5580 | -41 / -73 | -4008 | c=1.00: +1382 / -5580 / -41 | 148 | -0.004 | -0.024 | -0.13 / +0.13 / -0.05 | ok |
|  | RK7 | L3M | +3405 / +5958 | -9590 | +321 / +562 | -11497 | c=1.00: +3405 / -9590 / +321 | 69 | -0.014 | -0.075 | -0.20 / -0.09 / -0.03 | RED |
|  | RK7 | L6M | +2086 / +3650 | -9590 | +1336 / +2338 | -11497 | c=1.00: +2086 / -9590 / +1336 | 161 | +0.138 | +0.824 | -0.09 / -0.09 / +0.04 | RED |
|  | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=1.00: +1894 / -3780 / +589 | 74 | +0.067 | +0.382 | +0.03 / +0.06 / -0.01 | AMBER |
|  | RK7 | L6M | +1487 / +2602 | -3945 | +1090 / +1907 | -6714 | c=1.00: +1487 / -3945 / +1090 | 161 | +0.123 | +0.731 | -0.02 / +0.08 / +0.10 | AMBER |
|  | RK7 | L3M | +3450 / +6037 | -8248 | -386 / -675 | -10354 | c=1.00: +3450 / -8248 / -386 | 119 | -0.103 | -0.946 | +0.10 / +0.17 / +0.16 | RED |
|  | RK7 | L6M | +2149 / +3761 | -8248 | +753 / +1317 | -10354 | c=1.00: +2149 / -8248 / +753 | 231 | +0.016 | +0.134 | +0.18 / +0.10 / +0.13 | RED |
|  | RK7 | L3M | +4454 / +7795 | -8394 | +593 / +1038 | -15124 | c=1.00: +4454 / -8394 / +593 | 127 | +0.037 | +0.363 | +0.02 / +0.39 / +0.34 | RED |
|  | RK7 | L6M | +2688 / +4704 | -8394 | +1645 / +2878 | -15124 | c=1.00: +2688 / -8394 / +1645 | 299 | +0.107 | +1.181 | +0.08 / +0.21 / +0.22 | RED |
|  | RK7 | L3M | +329 / +576 | -322 | +1285 / +2249 | +1123 | c=1.00: +329 / -322 / +1285 | 38 | +0.261 | +0.762 | +0.37 / -0.05 / +0.13 | ok |
|  | RK7 | L3M | +3829 / +6701 | -7245 | +2261 / +3958 | -11200 | c=1.00: +3829 / -7245 / +2261 | 59 | +0.357 | +1.619 | -0.35 / +0.12 / -0.05 | RED |
|  | RK7 | L3M | +2679 / +4689 | -8240 | -452 / -791 | -7967 | c=1.00: +2679 / -8240 / -452 | 60 | -0.170 | -0.783 | +0.17 / -0.02 / +0.20 | AMBER |
|  | RK7 | L6M | +1710 / +2993 | -8240 | +1344 / +2351 | -7967 | c=1.00: +1710 / -8240 / +1344 | 137 | +0.162 | +0.822 | +0.15 / +0.03 / +0.19 | AMBER |
|  | RK7 | L3M | +2371 / +4149 | -10570 | +1932 / +3382 | -4795 | c=1.00: +2371 / -10570 / +1932 | 68 | +0.206 | +1.076 | +0.01 / +0.15 / +0.27 | AMBER |
|  | RK7 | L6M | +1668 / +2919 | -10570 | -704 / -1233 | -4795 | c=1.00: +1668 / -10570 / -704 | 159 | -0.171 | -1.010 | +0.01 / +0.05 / +0.08 | AMBER |
|  | RK7 | L3M | +773 / +1352 | -5345 | +1432 / +2505 | -1140 | c=1.00: +773 / -5345 / +1432 | 116 | +0.032 | +0.286 | +0.24 / +0.10 / +0.21 | ok |
|  | RK7 | L6M | +655 / +1147 | -5345 | +855 / +1496 | -1140 | c=1.00: +655 / -5345 / +855 | 252 | +0.021 | +0.198 | +0.13 / +0.13 / +0.14 | ok |
|  | RK7 | L3M | +1145 / +2004 | -2722 | +2366 / +4140 | -109 | c=1.00: +1145 / -2722 / +2366 | 68 | +0.221 | +1.155 | -0.15 / +0.03 / +0.21 | ok |
|  | RK7 | L6M | +843 / +1476 | -2722 | +1239 / +2168 | -109 | c=1.00: +843 / -2722 / +1239 | 160 | +0.088 | +0.524 | -0.14 / -0.00 / +0.17 | ok |
|  | RK7 | L3M | +1508 / +2639 | -4055 | -214 / -375 | -5075 | c=1.00: +1508 / -4055 / -214 | 72 | -0.123 | -0.679 | +0.03 / +0.04 / -0.03 | AMBER |
|  | RK7 | L6M | +1032 / +1806 | -4055 | +1009 / +1766 | -5075 | c=1.00: +1032 / -4055 / +1009 | 164 | +0.078 | +0.475 | +0.04 / +0.05 / +0.07 | AMBER |
|  | RK7 | L3M | +2264 / +3963 | -6220 | +1754 / +3070 | -6301 | c=1.00: +2264 / -6220 / +1754 | 56 | +0.222 | +0.957 | +0.12 / -0.07 / +0.35 | AMBER |
|  | RK7 | L6M | +1433 / +2509 | -6220 | +1334 / +2335 | -6301 | c=1.00: +1433 / -6220 / +1334 | 134 | +0.195 | +0.966 | +0.08 / -0.06 / +0.21 | AMBER |
|  | RK7 | L3M | +2758 / +4826 | -5758 | -272 / -476 | -7049 | c=1.00: +2758 / -5758 / -272 | 90 | -0.114 | -0.788 | -0.04 / +0.03 / +0.19 | AMBER |
|  | RK7 | L6M | +1882 / +3294 | -5758 | +298 / +522 | -7049 | c=1.00: +1882 / -5758 / +298 | 194 | -0.036 | -0.258 | +0.03 / +0.07 / +0.19 | AMBER |
|  | RK7 | L3M | +1220 / +2135 | -3440 | +347 / +607 | -2608 | c=1.00: +1220 / -3440 / +347 | 93 | -0.066 | -0.475 | +0.21 / +0.08 / +0.25 | ok |
|  | RK7 | L6M | +905 / +1584 | -3440 | +1083 / +1896 | -2608 | c=1.00: +905 / -3440 / +1083 | 200 | +0.051 | +0.380 | +0.07 / +0.09 / +0.20 | ok |
|  | RK7 | L3M | +2007 / +3512 | -5275 | -1001 / -1752 | -7309 | c=1.00: +2007 / -5275 / -1001 | 62 | -0.253 | -1.204 | +0.01 / +0.10 / -0.14 | AMBER |
|  | RK7 | L6M | +1472 / +2575 | -5275 | -591 / -1034 | -7309 | c=1.00: +1472 / -5275 / -591 | 143 | -0.160 | -0.849 | +0.06 / +0.02 / -0.06 | AMBER |
|  | RK7 | L3M | +4251 / +7439 | -7665 | +1152 / +2017 | -14015 | c=1.00: +4251 / -7665 / +1152 | 58 | +0.144 | +0.644 | +0.07 / +0.07 / +0.42 | RED |
|  | RK7 | L6M | +2669 / +4671 | -7665 | +2152 / +3766 | -14015 | c=1.00: +2669 / -7665 / +2152 | 135 | +0.325 | +1.627 | -0.02 / +0.12 / +0.23 | RED |
|  | RK7 | L3M | +2051 / +3589 | -6385 | +20 / +35 | -8729 | c=1.00: +2051 / -6385 / +20 | 149 | -0.048 | -0.546 | +0.17 / +0.19 / +0.27 | AMBER |
|  | RK7 | L6M | +1342 / +2349 | -6385 | +1349 / +2361 | -8729 | c=1.00: +1342 / -6385 / +1349 | 325 | +0.064 | +0.775 | +0.08 / +0.04 / +0.17 | AMBER |
|  | RK7 | L3M | +1996 / +3493 | -4538 | -314 / -550 | -8221 | c=1.00: +1996 / -4538 / -314 | 137 | -0.030 | -0.317 | -0.08 / +0.01 / -0.10 | AMBER |
|  | RK7 | L6M | +1353 / +2368 | -4538 | +651 / +1139 | -8221 | c=1.00: +1353 / -4538 / +651 | 282 | +0.042 | +0.435 | -0.10 / +0.03 / -0.10 | AMBER |
|  | RK7 | L3M | +217 / +379 | -3000 | +2347 / +4107 | -796 | c=1.00: +217 / -3000 / +2347 | 64 | +0.276 | +1.361 | -0.01 / -0.09 / -0.01 | ok |
|  | RK7 | L6M | +315 / +551 | -3000 | +2014 / +3525 | -796 | c=1.00: +315 / -3000 / +2014 | 143 | +0.245 | +1.297 | +0.05 / -0.01 / +0.16 | ok |
|  | RK7 | L3M | +1538 / +2692 | -100 | +2236 / +3913 | -5954 | c=1.00: +1538 / -100 / +2236 | 60 | +0.335 | +1.547 | +0.06 / -0.20 / +0.17 | AMBER |
|  | RK7 | L6M | +1043 / +1825 | -100 | +2899 / +5073 | -5954 | c=1.00: +1043 / -100 / +2899 | 135 | +0.437 | +2.185 | -0.08 / -0.05 / +0.09 | AMBER |
|  | RK7 | L3M | +1834 / +3209 | -5785 | +336 / +587 | -8252 | c=1.00: +1834 / -5785 / +336 | 105 | -0.026 | -0.213 | -0.07 / -0.09 / -0.30 | AMBER |
|  | RK7 | L6M | +1355 / +2372 | -5785 | -348 / -610 | -8252 | c=1.00: +1355 / -5785 / -348 | 244 | -0.081 | -0.730 | -0.02 / -0.05 / -0.04 | AMBER |
|  | RK7 | L3M | +533 / +933 | -5805 | +1089 / +1906 | -929 | c=1.00: +533 / -5805 / +1089 | 62 | +0.084 | +0.398 | +0.23 / -0.05 / -0.02 | ok |
|  | RK7 | L6M | +653 / +1142 | -5805 | +971 / +1699 | -929 | c=1.00: +653 / -5805 / +971 | 137 | +0.124 | +0.627 | +0.10 / +0.01 / +0.02 | ok |
|  | RK7 | L3M | +1512 / +2645 | -4165 | +614 / +1075 | -5506 | c=1.00: +1512 / -4165 / +614 | 74 | +0.100 | +0.570 | +0.18 / +0.09 / +0.11 | AMBER |
|  | RK7 | L6M | +1235 / +2162 | -4165 | +454 / +794 | -5506 | c=1.00: +1235 / -4165 / +454 | 168 | +0.057 | +0.355 | +0.06 / +0.05 / +0.17 | AMBER |
|  | RK7 | L3M | +303 / +530 | +1651 | +2638 / +4617 | +664 | c=1.00: +303 / +1651 / +2638 | 163 | +0.125 | +1.569 | +0.17 / +0.12 / +0.38 | ok |
|  | RK7 | L6M | +255 / +446 | +1651 | +2505 / +4384 | +664 | c=1.00: +255 / +1651 / +2505 | 382 | +0.123 | +1.742 | +0.14 / +0.08 / +0.16 | ok |
|  | RK7 | L3M | +3766 / +6591 | -6054 | +908 / +1590 | -13173 | c=1.00: +3766 / -6054 / +908 | 90 | +0.045 | +0.314 | -0.09 / +0.43 / +0.16 | RED |
|  | RK7 | L6M | +2534 / +4435 | -6054 | +1482 / +2593 | -13173 | c=1.00: +2534 / -6054 / +1482 | 210 | +0.117 | +0.910 | -0.05 / +0.23 / +0.05 | RED |
|  | RK7 | L3M | +1851 / +3240 | -3495 | +1140 / +1994 | -5845 | c=1.00: +1851 / -3495 / +1140 | 184 | +0.073 | +1.036 | +0.12 / +0.24 / +0.15 | AMBER |
|  | RK7 | L6M | +1312 / +2296 | -3495 | +1261 / +2206 | -5845 | c=1.00: +1312 / -3495 / +1261 | 450 | +0.060 | +1.007 | +0.14 / +0.14 / +0.15 | AMBER |
|  | RK7 | L3M | +4208 / +7365 | -8375 | +292 / +511 | -13279 | c=1.00: +4208 / -8375 / +292 | 59 | -0.035 | -0.161 | +0.02 / +0.04 / +0.45 | RED |
|  | RK7 | L6M | +2977 / +5211 | -8375 | -574 / -1005 | -13279 | c=1.00: +2977 / -8375 / -574 | 141 | -0.148 | -0.771 | -0.01 / +0.08 / +0.34 | RED |
|  | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=1.00: +1894 / -3780 / +589 | 74 | +0.067 | +0.382 | +0.03 / +0.06 / -0.01 | AMBER |
|  | RK7 | L6M | +1487 / +2602 | -3945 | +1090 / +1907 | -6714 | c=1.00: +1487 / -3945 / +1090 | 161 | +0.123 | +0.731 | -0.02 / +0.08 / +0.10 | AMBER |
|  | RK7 | L3M | +2902 / +5079 | -4665 | -554 / -970 | -9869 | c=1.00: +2902 / -4665 / -554 | 136 | -0.101 | -1.054 | -0.04 / -0.05 / -0.09 | RED |
|  | RK7 | L6M | +1854 / +3245 | -4665 | +494 / +865 | -9869 | c=1.00: +1854 / -4665 / +494 | 303 | +0.002 | +0.020 | -0.00 / -0.02 / +0.04 | RED |
|  | RK7 | L3M | +2502 / +4378 | -5116 | +596 / +1043 | -8959 | c=1.00: +2502 / -5116 / +596 | 40 | +0.095 | +0.293 | +0.02 / +0.03 / +0.22 | AMBER |
|  | RK7 | L6M | +1611 / +2819 | -5116 | +928 / +1623 | -8959 | c=1.00: +1611 / -5116 / +928 | 81 | +0.183 | +0.550 | +0.08 / -0.04 / +0.08 | AMBER |
|  | RK7 | L3M | +1058 / +1852 | -2436 | +540 / +945 | -4895 | c=1.00: +1058 / -2436 / +540 | 138 | +0.005 | +0.053 | +0.25 / +0.18 / +0.18 | AMBER |
|  | RK7 | L6M | +686 / +1200 | -2436 | +836 / +1463 | -4895 | c=1.00: +686 / -2436 / +836 | 280 | +0.038 | +0.396 | +0.17 / +0.14 / +0.09 | AMBER |
|  | RK7 | L3M | +1505 / +2634 | -1108 | +250 / +437 | -4896 | c=1.00: +1505 / -1108 / +250 | 113 | +0.021 | +0.181 | +0.29 / +0.19 / +0.58 | AMBER |
|  | RK7 | L6M | +1185 / +2073 | -1108 | +166 / +291 | -4896 | c=1.00: +1185 / -1108 / +166 | 242 | +0.010 | +0.091 | +0.30 / +0.16 / +0.49 | AMBER |
|  | RK7 | L3M | +1509 / +2640 | -1962 | -33 / -58 | -2958 | c=1.00: +1509 / -1962 / -33 | 116 | -0.026 | -0.232 | -0.10 / +0.06 / +0.01 | ok |
|  | RK7 | L6M | +1129 / +1976 | -1962 | +2243 / +3924 | -2958 | c=1.00: +1129 / -1962 / +2243 | 244 | +0.177 | +1.600 | -0.04 / +0.01 / +0.05 | ok |
|  | RK7 | L3M | +572 / +1001 | -6940 | +852 / +1491 | -1145 | c=1.00: +572 / -6940 / +852 | 60 | +0.187 | +0.865 | +0.22 / -0.10 / +0.14 | ok |
|  | RK7 | L6M | +645 / +1128 | -6940 | -294 / -515 | -1145 | c=1.00: +645 / -6940 / -294 | 144 | -0.056 | -0.300 | +0.12 / -0.05 / +0.17 | ok |
|  | RK7 | L3M | +1583 / +2769 | -3333 | +1307 / +2288 | -5791 | c=1.00: +1583 / -3333 / +1307 | 106 | +0.132 | +1.072 | +0.18 / +0.21 / +0.30 | AMBER |
|  | RK7 | L6M | +1113 / +1947 | -3333 | +1878 / +3286 | -5791 | c=1.00: +1113 / -3333 / +1878 | 212 | +0.177 | +1.391 | +0.13 / +0.09 / +0.20 | AMBER |
|  | RK7 | L3M | +1782 / +3118 | -3699 | -688 / -1203 | -5977 | c=1.00: +1782 / -3699 / -688 | 207 | -0.041 | -0.658 | +0.07 / -0.15 / +0.01 | AMBER |
|  | RK7 | L6M | +1264 / +2212 | -3699 | +711 / +1244 | -5977 | c=1.00: +1264 / -3699 / +711 | 446 | +0.020 | +0.332 | +0.21 / +0.02 / +0.07 | AMBER |
|  | RK7 | L3M | +1835 / +3211 | -253 | +804 / +1407 | -6109 | c=1.00: +1835 / -253 / +804 | 143 | +0.046 | +0.504 | +0.26 / +0.14 / +0.17 | AMBER |
|  | RK7 | L6M | +1188 / +2079 | -253 | +655 / +1147 | -6109 | c=1.00: +1188 / -253 / +655 | 300 | +0.034 | +0.379 | +0.23 / +0.14 / +0.14 | AMBER |
|  | RK7 | L3M | +1747 / +3057 | -6225 | +1390 / +2433 | -8558 | c=1.00: +1747 / -6225 / +1390 | 55 | +0.123 | +0.520 | +0.10 / -0.03 / -0.09 | AMBER |
|  | RK7 | L6M | +1530 / +2677 | -6225 | +201 / +352 | -8558 | c=1.00: +1530 / -6225 / +201 | 122 | -0.070 | -0.319 | +0.08 / +0.02 / +0.09 | AMBER |
|  | RK7 | L3M | -460 / -805 | +1815 | +2376 / +4157 | +1427 | c=1.00: -460 / +1815 / +2376 | 100 | +0.153 | +1.173 | +0.26 / +0.19 / +0.15 | ok |
|  | RK7 | L6M | -26 / -46 | -1155 | +1294 / +2265 | +1427 | c=1.00: -26 / -1155 / +1294 | 201 | +0.072 | +0.538 | +0.10 / +0.13 / +0.04 | ok |
|  | RK7 | L3M | +419 / +733 | -3970 | +1788 / +3129 | -1170 | c=1.00: +419 / -3970 / +1788 | 65 | +0.296 | +1.480 | +0.29 / +0.09 / +0.21 | ok |
|  | RK7 | L6M | +572 / +1001 | -3970 | +174 / +305 | -1170 | c=1.00: +572 / -3970 / +174 | 149 | -0.006 | -0.035 | +0.12 / +0.10 / +0.16 | ok |
|  | RK7 | L3M | +1222 / +2139 | -4680 | +1 / +2 | -2931 | c=1.00: +1222 / -4680 / +1 | 55 | -0.026 | -0.111 | +0.09 / +0.01 / -0.13 | ok |
|  | RK7 | L6M | +841 / +1472 | -4680 | -115 / -202 | -2931 | c=1.00: +841 / -4680 / -115 | 118 | -0.076 | -0.332 | +0.08 / -0.02 / -0.05 | ok |
|  | RK7 | L3M | +2000 / +3500 | -2701 | -627 / -1097 | -7058 | c=1.00: +2000 / -2701 / -627 | 43 | -0.054 | -0.179 | +0.21 / +0.04 / +0.06 | AMBER |
|  | RK7 | L6M | +1244 / +2177 | -2701 | +64 / +112 | -7058 | c=1.00: +1244 / -2701 / +64 | 79 | +0.022 | +0.065 | +0.26 / +0.06 / +0.05 | AMBER |
|  | RK7 | L3M | +1787 / +3127 | -3345 | +417 / +730 | -5914 | c=1.00: +1787 / -3345 / +417 | 62 | -0.055 | -0.261 | -0.01 / +0.07 / -0.00 | AMBER |
|  | RK7 | L6M | +1218 / +2131 | -3345 | +722 / +1264 | -5914 | c=1.00: +1218 / -3345 / +722 | 140 | +0.036 | +0.184 | +0.02 / +0.03 / +0.20 | AMBER |
|  | RK7 | L3M | +892 / +1561 | +969 | +1557 / +2726 | -3857 | c=1.00: +892 / +969 / +1557 | 70 | +0.273 | +1.469 | +0.16 / +0.22 / +0.25 | ok |
|  | RK7 | L6M | +634 / +1109 | +969 | +856 / +1497 | -3857 | c=1.00: +634 / +969 / +856 | 176 | +0.114 | +0.745 | +0.12 / +0.15 / +0.24 | ok |
|  | RK7 | L3M | +3787 / +6626 | -6140 | +81 / +141 | -12301 | c=1.00: +3787 / -6140 / +81 | 71 | -0.120 | -0.655 | -0.04 / -0.01 / +0.30 | RED |
|  | RK7 | L6M | +2469 / +4320 | -6140 | +621 / +1087 | -12301 | c=1.00: +2469 / -6140 / +621 | 163 | -0.003 | -0.019 | +0.03 / +0.02 / +0.25 | RED |
|  | RK7 | L3M | +2116 / +3702 | -3106 | +655 / +1147 | -5497 | c=1.00: +2116 / -3106 / +655 | 204 | +0.031 | +0.494 | +0.22 / +0.19 / +0.30 | AMBER |
|  | RK7 | L6M | +1767 / +3093 | -3106 | +658 / +1152 | -5497 | c=1.00: +1767 / -3106 / +658 | 501 | +0.025 | +0.460 | +0.04 / +0.08 / +0.11 | AMBER |
|  | RK7 | L3M | +1314 / +2299 | -4440 | +1241 / +2172 | -5761 | c=1.00: +1314 / -4440 / +1241 | 70 | +0.187 | +1.008 | +0.10 / -0.10 / +0.16 | AMBER |
|  | RK7 | L6M | +1110 / +1942 | -4440 | +679 / +1188 | -5761 | c=1.00: +1110 / -4440 / +679 | 164 | +0.060 | +0.364 | +0.04 / -0.04 / +0.17 | AMBER |
|  | RK7 | L3M | +6187 / +10827 | -13323 | -364 / -637 | -20893 | c=1.00: +6187 / -13323 / -364 | 121 | +0.008 | +0.072 | +0.06 / +0.21 / +0.12 | RED |
|  | RK7 | L6M | +4218 / +7382 | -13323 | +448 / +784 | -20893 | c=1.00: +4218 / -13323 / +448 | 299 | +0.030 | +0.330 | +0.02 / +0.06 / +0.07 | RED |
|  | RK7 | L3M | +1920 / +3360 | -2722 | +3391 / +5934 | -6010 | c=1.00: +1920 / -2722 / +3391 | 90 | +0.300 | +2.075 | -0.20 / +0.26 / +0.12 | AMBER |
|  | RK7 | L6M | +1418 / +2482 | -2722 | +2392 / +4186 | -6010 | c=1.00: +1418 / -2722 / +2392 | 212 | +0.182 | +1.426 | -0.14 / +0.07 / -0.07 | AMBER |
|  | RK7 | L3M | +2030 / +3552 | -6220 | +1234 / +2159 | -6301 | c=1.00: +2030 / -6220 / +1234 | 51 | +0.133 | +0.523 | +0.23 / -0.08 / +0.17 | AMBER |
|  | RK7 | L6M | +1281 / +2242 | -6220 | +737 / +1289 | -6301 | c=1.00: +1281 / -6220 / +737 | 126 | +0.098 | +0.457 | +0.11 / -0.11 / +0.07 | AMBER |
|  | RK7 | L3M | +2156 / +3773 | -6465 | +792 / +1385 | -9386 | c=1.00: +2156 / -6465 / +792 | 54 | +0.005 | +0.021 | -0.11 / -0.00 / -0.06 | RED |
|  | RK7 | L6M | +1519 / +2659 | -6465 | +260 / +455 | -9386 | c=1.00: +1519 / -6465 / +260 | 117 | -0.051 | -0.219 | -0.02 / -0.03 / +0.02 | RED |
|  | RK7 | L3M | +943 / +1651 | -5635 | +2913 / +5097 | -2385 | c=1.00: +943 / -5635 / +2913 | 155 | +0.197 | +2.354 | +0.26 / +0.13 / +0.16 | ok |
|  | RK7 | L6M | +605 / +1060 | -5635 | +1426 / +2496 | -2385 | c=1.00: +605 / -5635 / +1426 | 345 | +0.078 | +1.000 | +0.13 / +0.13 / +0.06 | ok |
|  | RK7 | L3M | +715 / +1252 | -3935 | +1493 / +2614 | -2270 | c=1.00: +715 / -3935 / +1493 | 69 | +0.219 | +1.162 | +0.11 / +0.02 / +0.02 | ok |
|  | RK7 | L6M | +811 / +1420 | -3935 | +1630 / +2852 | -2270 | c=1.00: +811 / -3935 / +1630 | 168 | +0.193 | +1.204 | +0.07 / +0.01 / +0.19 | ok |
|  | RK7 | L3M | +2037 / +3565 | -5255 | +580 / +1015 | -7474 | c=1.00: +2037 / -5255 / +580 | 77 | +0.009 | +0.051 | +0.03 / -0.12 / +0.14 | AMBER |
|  | RK7 | L6M | +1519 / +2658 | -5255 | +1481 / +2592 | -7474 | c=1.00: +1519 / -5255 / +1481 | 157 | +0.174 | +1.010 | -0.04 / -0.05 / +0.09 | AMBER |
|  | RK7 | L3M | +2172 / +3802 | -4975 | -1277 / -2236 | -8039 | c=1.00: +2172 / -4975 / -1277 | 56 | -0.285 | -1.227 | +0.06 / +0.13 / -0.11 | AMBER |
|  | RK7 | L6M | +1637 / +2864 | -4975 | -1142 / -1998 | -8039 | c=1.00: +1637 / -4975 / -1142 | 146 | -0.223 | -1.208 | +0.06 / +0.04 / -0.13 | AMBER |
|  | RK7 | L3M | +1212 / +2120 | -6540 | +2530 / +4428 | -4437 | c=1.00: +1212 / -6540 / +2530 | 57 | +0.328 | +1.437 | +0.21 / +0.03 / +0.08 | ok |
|  | RK7 | L6M | +1013 / +1772 | -6540 | +1797 / +3144 | -4437 | c=1.00: +1013 / -6540 / +1797 | 127 | +0.223 | +1.049 | +0.13 / +0.05 / +0.07 | ok |
|  | RK7 | L3M | +892 / +1561 | +969 | +1557 / +2726 | -3857 | c=1.00: +892 / +969 / +1557 | 70 | +0.273 | +1.469 | +0.16 / +0.22 / +0.25 | ok |
|  | RK7 | L6M | +634 / +1109 | +969 | +856 / +1497 | -3857 | c=1.00: +634 / +969 / +856 | 176 | +0.114 | +0.745 | +0.12 / +0.15 / +0.24 | ok |
|  | RK7 | L3M | +2577 / +4510 | -10490 | +1047 / +1833 | -8025 | c=1.00: +2577 / -10490 / +1047 | 266 | +0.065 | +1.320 | +0.13 / +0.10 / +0.13 | AMBER |
|  | RK7 | L3M | -508 / -889 | -3060 | +2315 / +4051 | +2291 | c=1.00: -508 / -3060 / +2315 | 64 | +0.250 | +1.233 | +0.19 / -0.22 / +0.05 | ok |
|  | RK7 | L6M | +35 / +61 | -3570 | +2301 / +4028 | +1857 | c=1.00: +35 / -3570 / +2301 | 138 | +0.321 | +1.640 | +0.07 / -0.10 / +0.07 | ok |
|  | RK7 | L3M | +7758 / +13576 | -10893 | -1524 / -2666 | -22636 | c=1.00: +7758 / -10893 / -1524 | 122 | -0.185 | -1.732 | -0.16 / +0.07 / +0.09 | RED |
|  | RK7 | L6M | +5150 / +9013 | -10893 | -2064 / -3613 | -22636 | c=1.00: +5150 / -10893 / -2064 | 303 | -0.188 | -2.108 | -0.03 / +0.05 / -0.01 | RED |
|  | RK7 | L3M | +2178 / +3812 | -7880 | +688 / +1203 | -7371 | c=1.00: +2178 / -7880 / +688 | 125 | -0.012 | -0.116 | +0.31 / +0.04 / +0.34 | AMBER |
|  | RK7 | L6M | +1482 / +2594 | -7880 | +587 / +1027 | -7371 | c=1.00: +1482 / -7880 / +587 | 251 | +0.012 | +0.111 | +0.24 / +0.05 / +0.19 | AMBER |
|  | RK7 | L3M | +4472 / +7825 | -9135 | -813 / -1423 | -13807 | c=1.00: +4472 / -9135 / -813 | 64 | -0.275 | -1.354 | -0.21 / -0.16 / +0.02 | RED |
|  | RK7 | L6M | +2967 / +5192 | -9135 | +1215 / +2127 | -13807 | c=1.00: +2967 / -9135 / +1215 | 145 | +0.121 | +0.651 | -0.13 / -0.10 / +0.02 | RED |
|  | RK7 | L3M | +3071 / +5375 | -6920 | +821 / +1436 | -11572 | c=1.00: +3071 / -6920 / +821 | 93 | +0.093 | +0.663 | +0.08 / +0.08 / +0.08 | RED |
|  | RK7 | L6M | +2351 / +4115 | -7325 | -236 / -414 | -11572 | c=1.00: +2351 / -7325 / -236 | 192 | -0.035 | -0.248 | +0.04 / +0.08 / +0.09 | RED |
|  | RK7 | L3M | +3594 / +6289 | -6905 | -1417 / -2480 | -9674 | c=1.00: +3594 / -6905 / -1417 | 66 | -0.327 | -1.660 | -0.11 / +0.08 / +0.04 | RED |
|  | RK7 | L6M | +2399 / +4198 | -6905 | -1175 / -2057 | -9674 | c=1.00: +2399 / -6905 / -1175 | 164 | -0.210 | -1.275 | -0.06 / +0.05 / -0.14 | RED |
|  | RK7 | L3M | +3103 / +5431 | -5985 | +629 / +1101 | -11915 | c=1.00: +3103 / -5985 / +629 | 67 | +0.040 | +0.208 | -0.15 / +0.03 / +0.01 | RED |
|  | RK7 | L6M | +2036 / +3563 | -5985 | +682 / +1194 | -11915 | c=1.00: +2036 / -5985 / +682 | 153 | +0.053 | +0.302 | -0.01 / +0.02 / +0.14 | RED |
|  | RK7 | L3M | +3071 / +5375 | -6920 | +821 / +1436 | -11572 | c=1.00: +3071 / -6920 / +821 | 93 | +0.093 | +0.663 | +0.08 / +0.08 / +0.08 | RED |
|  | RK7 | L6M | +2351 / +4115 | -7325 | -236 / -414 | -11572 | c=1.00: +2351 / -7325 / -236 | 192 | -0.035 | -0.248 | +0.04 / +0.08 / +0.09 | RED |
|  | RK7 | L3M | +2761 / +4832 | -5423 | -889 / -1556 | -8102 | c=1.00: +2761 / -5423 / -889 | 95 | -0.155 | -1.136 | -0.03 / -0.24 / -0.03 | AMBER |
|  | RK7 | L6M | +1748 / +3059 | -5423 | -200 / -349 | -8102 | c=1.00: +1748 / -5423 / -200 | 209 | -0.066 | -0.510 | -0.01 / -0.17 / -0.07 | AMBER |
|  | RK7 | L3M | +1770 / +3098 | -2682 | +364 / +637 | -4939 | c=1.00: +1770 / -2682 / +364 | 73 | -0.056 | -0.313 | -0.17 / -0.11 / -0.01 | AMBER |
|  | RK7 | L6M | +1176 / +2058 | -2682 | +1144 / +2003 | -4939 | c=1.00: +1176 / -2682 / +1144 | 169 | +0.083 | +0.521 | -0.08 / -0.03 / +0.13 | AMBER |
|  | RK7 | L3M | +1370 / +2398 | -3610 | +70 / +122 | -4775 | c=1.00: +1370 / -3610 / +70 | 91 | +0.071 | +0.497 | +0.08 / +0.00 / +0.07 | AMBER |
|  | RK7 | L6M | +1133 / +1983 | -3610 | +1630 / +2852 | -4775 | c=1.00: +1133 / -3610 / +1630 | 209 | +0.178 | +1.381 | -0.02 / -0.00 / +0.13 | AMBER |
|  | RK7 | L3M | +1314 / +2299 | -4440 | +1241 / +2172 | -5761 | c=1.00: +1314 / -4440 / +1241 | 70 | +0.187 | +1.008 | +0.10 / -0.10 / +0.16 | AMBER |
|  | RK7 | L6M | +1110 / +1942 | -4440 | +679 / +1188 | -5761 | c=1.00: +1110 / -4440 / +679 | 164 | +0.060 | +0.364 | +0.04 / -0.04 / +0.17 | AMBER |
|  | RK7 | L3M | -32 / -56 | -3080 | +1504 / +2632 | +1286 | c=1.00: -32 / -3080 / +1504 | 64 | +0.108 | +0.534 | -0.01 / -0.27 / -0.04 | ok |
|  | RK7 | L6M | +448 / +783 | -6180 | +1968 / +3444 | +1286 | c=1.00: +448 / -6180 / +1968 | 137 | +0.257 | +1.304 | -0.03 / -0.14 / -0.01 | ok |
|  | RK7 | L3M | +1317 / +2305 | +1142 | -1019 / -1783 | -4186 | c=1.00: +1317 / +1142 / -1019 | 89 | -0.183 | -1.255 | +0.07 / -0.02 / +0.03 | ok |
|  | RK7 | L6M | +980 / +1715 | +1142 | +1275 / +2231 | -4186 | c=1.00: +980 / +1142 / +1275 | 206 | +0.093 | +0.708 | -0.04 / -0.01 / -0.12 | ok |
|  | RK7 | L3M | +3804 / +6657 | -7194 | +555 / +972 | -12323 | c=1.00: +3804 / -7194 / +555 | 69 | +0.067 | +0.358 | +0.12 / +0.33 / +0.38 | RED |
|  | RK7 | L6M | +2450 / +4287 | -7194 | +844 / +1477 | -12323 | c=1.00: +2450 / -7194 / +844 | 139 | +0.090 | +0.464 | +0.06 / +0.17 / +0.34 | RED |
|  | RK7 | L3M | +1412 / +2471 | -4050 | +125 / +219 | -5365 | c=1.00: +1412 / -4050 / +125 | 70 | +0.017 | +0.094 | +0.20 / +0.10 / +0.07 | AMBER |
|  | RK7 | L6M | +1164 / +2036 | -4050 | +477 / +835 | -5365 | c=1.00: +1164 / -4050 / +477 | 158 | +0.046 | +0.268 | +0.09 / +0.10 / +0.17 | AMBER |
|  | RK7 | L3M | +6347 / +11107 | -8590 | -596 / -1043 | -18429 | c=1.00: +6347 / -8590 / -596 | 62 | -0.275 | -1.311 | -0.24 / -0.02 / +0.14 | RED |
|  | RK7 | L6M | +3995 / +6991 | -8590 | +273 / +478 | -18429 | c=1.00: +3995 / -8590 / +273 | 144 | -0.046 | -0.247 | -0.12 / -0.05 / +0.07 | RED |
|  | RK7 | L3M | +1675 / +2931 | -1770 | +2019 / +3534 | -7835 | c=1.00: +1675 / -1770 / +2019 | 90 | +0.217 | +1.501 | +0.04 / +0.20 / +0.30 | AMBER |
|  | RK7 | L6M | +1049 / +1835 | -1770 | +1871 / +3274 | -7835 | c=1.00: +1049 / -1770 / +1871 | 193 | +0.173 | +1.237 | +0.09 / +0.07 / +0.25 | AMBER |
|  | RK7 | L3M | +811 / +1418 | -2650 | +1481 / +2593 | -3220 | c=1.00: +811 / -2650 / +1481 | 78 | +0.160 | +0.962 | -0.03 / +0.04 / -0.17 | ok |
|  | RK7 | L6M | +494 / +865 | -2650 | +1431 / +2505 | -3220 | c=1.00: +494 / -2650 / +1431 | 173 | +0.146 | +0.935 | +0.12 / +0.06 / -0.09 | ok |
|  | RK7 | L3M | +3155 / +5521 | -2885 | -962 / -1684 | -9046 | c=1.00: +3155 / -2885 / -962 | 221 | -0.040 | -0.675 | +0.22 / +0.20 / +0.50 | AMBER |
|  | RK7 | L6M | +1968 / +3444 | -2885 | +532 / +932 | -9046 | c=1.00: +1968 / -2885 / +532 | 484 | +0.020 | +0.361 | +0.20 / +0.13 / +0.38 | AMBER |
|  | RK7 | L3M | +1239 / +2168 | -3985 | +326 / +570 | -4855 | c=1.00: +1239 / -3985 / +326 | 72 | +0.091 | +0.504 | +0.04 / -0.17 / +0.03 | AMBER |
|  | RK7 | L6M | +1170 / +2047 | -3985 | +227 / +396 | -4855 | c=1.00: +1170 / -3985 / +227 | 166 | +0.030 | +0.186 | -0.03 / -0.06 / +0.07 | AMBER |
|  | RK7 | L3M | +4003 / +7005 | -8959 | -1005 / -1760 | -14304 | c=1.00: +4003 / -8959 / -1005 | 104 | -0.090 | -0.719 | +0.10 / +0.19 / +0.30 | RED |
|  | RK7 | L6M | +2498 / +4372 | -8959 | +1313 / +2298 | -14304 | c=1.00: +2498 / -8959 / +1313 | 252 | +0.109 | +1.018 | +0.02 / +0.13 / +0.16 | RED |
|  | RK7 | L3M | +2257 / +3949 | -4892 | +1118 / +1957 | -4508 | c=1.00: +2257 / -4892 / +1118 | 77 | +0.066 | +0.389 | -0.12 / +0.16 / +0.10 | AMBER |
|  | RK7 | L6M | +1419 / +2483 | -4892 | +861 / +1507 | -4508 | c=1.00: +1419 / -4892 / +861 | 163 | +0.049 | +0.294 | -0.04 / +0.12 / +0.14 | AMBER |
|  | RK7 | L3M | +2295 / +4016 | -6370 | -564 / -988 | -8674 | c=1.00: +2295 / -6370 / -564 | 69 | -0.112 | -0.594 | -0.01 / +0.03 / -0.11 | AMBER |
|  | RK7 | L6M | +1628 / +2849 | -6370 | -328 / -574 | -8674 | c=1.00: +1628 / -6370 / -328 | 170 | -0.080 | -0.504 | +0.02 / -0.03 / -0.07 | AMBER |
|  | RK7 | L3M | -208 / -364 | -3280 | +2021 / +3536 | +1726 | c=1.00: -208 / -3280 / +2021 | 60 | +0.209 | +0.964 | +0.21 / -0.09 / +0.07 | ok |
|  | RK7 | L6M | +333 / +583 | -6155 | +1809 / +3166 | +1726 | c=1.00: +333 / -6155 / +1809 | 136 | +0.242 | +1.218 | +0.07 / -0.02 / +0.10 | ok |
|  | RK7 | L3M | +1238 / +2166 | -5705 | +250 / +437 | -2768 | c=1.00: +1238 / -5705 / +250 | 151 | -0.006 | -0.065 | +0.04 / +0.06 / +0.11 | ok |
|  | RK7 | L6M | +930 / +1628 | -5705 | +488 / +854 | -2768 | c=1.00: +930 / -5705 / +488 | 375 | +0.012 | +0.173 | -0.06 / +0.07 / -0.02 | ok |
|  | RK7 | L3M | -283 / -496 | +3268 | -335 / -586 | +2124 | c=1.00: -283 / +3268 / -335 | 132 | -0.018 | -0.180 | +0.45 / +0.20 / +0.39 | ok |
|  | RK7 | L6M | -93 / -163 | +3240 | +284 / +497 | +2124 | c=1.00: -93 / +3240 / +284 | 254 | +0.012 | +0.113 | +0.31 / +0.11 / +0.26 | ok |
|  | RK7 | L3M | +3450 / +6037 | -8248 | -386 / -675 | -10354 | c=1.00: +3450 / -8248 / -386 | 119 | -0.103 | -0.946 | +0.10 / +0.17 / +0.16 | RED |
|  | RK7 | L6M | +2149 / +3761 | -8248 | +753 / +1317 | -10354 | c=1.00: +2149 / -8248 / +753 | 231 | +0.016 | +0.134 | +0.18 / +0.10 / +0.13 | RED |
|  | RK7 | L3M | +2350 / +4113 | -7760 | +782 / +1369 | -10094 | c=1.00: +2350 / -7760 / +782 | 55 | +0.051 | +0.215 | -0.07 / -0.03 / -0.13 | RED |
|  | RK7 | L6M | +1880 / +3290 | -7760 | -192 / -335 | -10094 | c=1.00: +1880 / -7760 / -192 | 122 | -0.121 | -0.548 | +0.03 / -0.01 / +0.09 | RED |
|  | RK7 | L3M | +5014 / +8774 | -8974 | +2186 / +3825 | -16907 | c=1.00: +5014 / -8974 / +2186 | 108 | +0.162 | +1.342 | -0.04 / +0.39 / +0.31 | RED |
|  | RK7 | L6M | +3102 / +5429 | -8974 | +974 / +1705 | -16907 | c=1.00: +3102 / -8974 / +974 | 275 | +0.047 | +0.483 | +0.01 / +0.20 / +0.14 | RED |
|  | RK7 | L3M | +5937 / +10389 | -9553 | -635 / -1111 | -19250 | c=1.00: +5937 / -9553 / -635 | 111 | -0.090 | -0.765 | -0.01 / +0.27 / +0.41 | RED |
|  | RK7 | L6M | +3710 / +6492 | -9553 | +883 / +1545 | -19250 | c=1.00: +3710 / -9553 / +883 | 281 | +0.059 | +0.613 | +0.01 / +0.19 / +0.14 | RED |
|  | RK7 | L3M | +1837 / +3214 | -6679 | +981 / +1717 | -6520 | c=1.00: +1837 / -6679 / +981 | 281 | +0.019 | +0.408 | +0.05 / -0.01 / -0.15 | AMBER |
|  | RK7 | L6M | +1199 / +2099 | -6679 | +808 / +1414 | -6520 | c=1.00: +1199 / -6679 / +808 | 627 | +0.004 | +0.085 | +0.00 / -0.04 / -0.07 | AMBER |
|  | RK7 | L3M | +2088 / +3655 | -5696 | +1786 / +3125 | -4913 | c=1.00: +2088 / -5696 / +1786 | 54 | +0.305 | +1.265 | +0.04 / +0.12 / +0.24 | AMBER |
|  | RK7 | L6M | +1220 / +2134 | -5696 | +2271 / +3974 | -4913 | c=1.00: +1220 / -5696 / +2271 | 106 | +0.429 | +1.683 | -0.02 / +0.04 / +0.13 | AMBER |
|  | RK7 | L3M | +1838 / +3217 | -5096 | +151 / +264 | -2342 | c=1.00: +1838 / -5096 / +151 | 110 | -0.060 | -0.510 | -0.24 / +0.09 / +0.05 | AMBER |
|  | RK7 | L6M | +1163 / +2035 | -5096 | +1054 / +1844 | -2342 | c=1.00: +1163 / -5096 / +1054 | 225 | +0.056 | +0.469 | -0.19 / +0.01 / -0.05 | ok |
|  | RK7 | L3M | +2641 / +4621 | -4700 | +94 / +164 | -9614 | c=1.00: +2641 / -4700 / +94 | 132 | -0.057 | -0.577 | +0.01 / -0.01 / +0.19 | RED |
|  | RK7 | L6M | +1741 / +3047 | -4700 | +211 / +369 | -9614 | c=1.00: +1741 / -4700 / +211 | 278 | -0.020 | -0.201 | -0.02 / -0.05 / +0.10 | RED |
|  | RK7 | L3M | +2641 / +4621 | -4700 | +94 / +164 | -9614 | c=1.00: +2641 / -4700 / +94 | 132 | -0.057 | -0.577 | +0.01 / -0.01 / +0.19 | RED |
|  | RK7 | L6M | +1741 / +3047 | -4700 | +211 / +369 | -9614 | c=1.00: +1741 / -4700 / +211 | 278 | -0.020 | -0.201 | -0.02 / -0.05 / +0.10 | RED |
|  | RK7 | L3M | +2681 / +4692 | -2702 | -362 / -634 | -7745 | c=1.00: +2681 / -2702 / -362 | 69 | -0.172 | -0.915 | -0.13 / +0.22 / +0.06 | AMBER |
|  | RK7 | L6M | +1921 / +3362 | -3760 | -1418 / -2482 | -7745 | c=1.00: +1921 / -3760 / -1418 | 159 | -0.279 | -1.643 | -0.06 / +0.04 / +0.03 | AMBER |
|  | RK7 | L3M | +1796 / +3143 | -8015 | -565 / -989 | -6500 | c=1.00: +1796 / -8015 / -565 | 81 | -0.011 | -0.067 | +0.11 / -0.10 / +0.00 | AMBER |
|  | RK7 | L6M | +1362 / +2384 | -8015 | +613 / +1072 | -6500 | c=1.00: +1362 / -8015 / +613 | 187 | +0.093 | +0.641 | +0.05 / -0.07 / +0.10 | AMBER |
|  | RK7 | L3M | +2438 / +4266 | -4180 | -804 / -1407 | -7064 | c=1.00: +2438 / -4180 / -804 | 72 | -0.094 | -0.519 | +0.15 / +0.09 / +0.16 | AMBER |
|  | RK7 | L6M | +1738 / +3042 | -4180 | -17 / -30 | -7064 | c=1.00: +1738 / -4180 / -17 | 163 | -0.009 | -0.057 | +0.01 / +0.07 / +0.17 | AMBER |
|  | RK7 | L3M | +2542 / +4449 | -4670 | -1427 / -2498 | -7625 | c=1.00: +2542 / -4670 / -1427 | 72 | -0.283 | -1.568 | -0.18 / -0.11 / -0.18 | AMBER |
|  | RK7 | L6M | +1596 / +2794 | -4670 | +861 / +1507 | -7625 | c=1.00: +1596 / -4670 / +861 | 167 | +0.066 | +0.411 | -0.08 / -0.07 / +0.03 | AMBER |
|  | RK7 | L3M | +1145 / +2003 | -2915 | +3152 / +5517 | -2071 | c=1.00: +1145 / -2915 / +3152 | 61 | +0.409 | +1.920 | -0.12 / -0.12 / +0.07 | ok |
|  | RK7 | L6M | +823 / +1441 | -2915 | +2487 / +4353 | -2071 | c=1.00: +823 / -2915 / +2487 | 140 | +0.319 | +1.654 | -0.12 / -0.07 / +0.01 | ok |
|  | RK7 | L3M | +379 / +664 | +1227 | +553 / +969 | -2950 | c=1.00: +379 / +1227 / +553 | 162 | +0.021 | +0.262 | +0.28 / -0.09 / -0.04 | ok |
|  | RK7 | L6M | +306 / +536 | +1227 | +1023 / +1790 | -2950 | c=1.00: +306 / +1227 / +1023 | 337 | +0.035 | +0.436 | +0.30 / -0.05 / +0.01 | ok |
|  | RK7 | L3M | +1382 / +2419 | -6180 | +1628 / +2848 | -4651 | c=1.00: +1382 / -6180 / +1628 | 106 | +0.108 | +0.882 | -0.02 / -0.09 / +0.05 | ok |
|  | RK7 | L6M | +1021 / +1786 | -6180 | +795 / +1391 | -4651 | c=1.00: +1021 / -6180 / +795 | 223 | +0.043 | +0.355 | -0.09 / -0.03 / -0.15 | ok |
|  | RK7 | L3M | +148 / +260 | -3080 | +1607 / +2812 | +996 | c=1.00: +148 / -3080 / +1607 | 61 | +0.206 | +0.969 | +0.16 / -0.15 / +0.05 | ok |
|  | RK7 | L6M | +409 / +715 | -3815 | +2335 / +4087 | +996 | c=1.00: +409 / -3815 / +2335 | 132 | +0.373 | +1.825 | +0.01 / -0.07 / +0.03 | ok |
|  | RK7 | L3M | +717 / +1255 | -314 | +2772 / +4851 | -2862 | c=1.00: +717 / -314 / +2772 | 139 | +0.150 | +1.608 | +0.06 / +0.06 / +0.02 | ok |
|  | RK7 | L6M | +548 / +959 | -314 | +1604 / +2808 | -2862 | c=1.00: +548 / -314 / +1604 | 307 | +0.067 | +0.767 | +0.13 / +0.04 / +0.12 | ok |
|  | RK7 | L3M | -141 / -247 | +1770 | +2175 / +3806 | +684 | c=1.00: -141 / +1770 / +2175 | 69 | +0.322 | +1.706 | +0.11 / +0.08 / +0.24 | ok |
|  | RK7 | L6M | +250 / +438 | -3605 | +1463 / +2560 | +684 | c=1.00: +250 / -3605 / +1463 | 173 | +0.174 | +1.118 | +0.10 / +0.06 / +0.31 | ok |
|  | RK7 | L3M | +303 / +530 | +1651 | +2638 / +4617 | +664 | c=1.00: +303 / +1651 / +2638 | 163 | +0.125 | +1.569 | +0.17 / +0.12 / +0.38 | ok |
|  | RK7 | L6M | +255 / +446 | +1651 | +2505 / +4384 | +664 | c=1.00: +255 / +1651 / +2505 | 382 | +0.123 | +1.742 | +0.14 / +0.08 / +0.16 | ok |
|  | RK7 | L3M | +4889 / +8555 | -12683 | +1515 / +2651 | -17594 | c=1.00: +4889 / -12683 / +1515 | 129 | +0.062 | +0.620 | -0.03 / -0.05 / +0.24 | RED |
|  | RK7 | L6M | +3236 / +5663 | -12683 | +1031 / +1804 | -17594 | c=1.00: +3236 / -12683 / +1031 | 286 | +0.048 | +0.504 | -0.01 / -0.03 / -0.04 | RED |
|  | RK7 | L3M | +4743 / +8299 | -9490 | -271 / -475 | -13837 | c=1.00: +4743 / -9490 / -271 | 66 | -0.159 | -0.806 | -0.12 / +0.02 / +0.16 | RED |
|  | RK7 | L6M | +3172 / +5551 | -9490 | +910 / +1592 | -13837 | c=1.00: +3172 / -9490 / +910 | 148 | +0.101 | +0.555 | -0.10 / +0.02 / +0.06 | RED |
|  | RK7 | L3M | +1782 / +3119 | -7971 | +2358 / +4127 | -5082 | c=1.00: +1782 / -7971 / +2358 | 74 | +0.279 | +1.587 | +0.34 / +0.39 / +0.44 | AMBER |
|  | RK7 | L6M | +1084 / +1898 | -7971 | +1578 / +2761 | -5082 | c=1.00: +1084 / -7971 / +1578 | 149 | +0.188 | +1.038 | +0.22 / +0.24 / +0.22 | AMBER |
|  | RK7 | L3M | +3594 / +6289 | -6905 | -1417 / -2480 | -9674 | c=1.00: +3594 / -6905 / -1417 | 66 | -0.327 | -1.660 | -0.11 / +0.08 / +0.04 | RED |
|  | RK7 | L6M | +2399 / +4198 | -6905 | -1175 / -2057 | -9674 | c=1.00: +2399 / -6905 / -1175 | 164 | -0.210 | -1.275 | -0.06 / +0.05 / -0.14 | RED |
|  | RK7 | L3M | +2478 / +4337 | -2540 | +1192 / +2086 | -7824 | c=1.00: +2478 / -2540 / +1192 | 75 | +0.081 | +0.465 | -0.23 / +0.29 / +0.16 | AMBER |
|  | RK7 | L6M | +1780 / +3116 | -2540 | +936 / +1638 | -7824 | c=1.00: +1780 / -2540 / +936 | 169 | +0.054 | +0.336 | -0.21 / +0.13 / +0.01 | AMBER |
|  | RK7 | L3M | +2101 / +3677 | -3749 | +2391 / +4184 | -6684 | c=1.00: +2101 / -3749 / +2391 | 85 | +0.295 | +1.929 | -0.00 / +0.25 / +0.17 | AMBER |
|  | RK7 | L6M | +1277 / +2235 | -3749 | +1036 / +1812 | -6684 | c=1.00: +1277 / -3749 / +1036 | 182 | +0.108 | +0.726 | -0.04 / +0.20 / +0.15 | AMBER |
|  | RK7 | L3M | +1518 / +2657 | -2515 | +1344 / +2352 | -3099 | c=1.00: +1518 / -2515 / +1344 | 69 | +0.166 | +0.883 | -0.09 / +0.07 / +0.08 | ok |
|  | RK7 | L6M | +1268 / +2219 | -4165 | +1164 / +2036 | -3099 | c=1.00: +1268 / -4165 / +1164 | 159 | +0.126 | +0.741 | -0.09 / +0.06 / +0.01 | ok |
|  | RK7 | L3M | -283 / -496 | +3268 | -335 / -586 | +2124 | c=1.00: -283 / +3268 / -335 | 132 | -0.018 | -0.180 | +0.45 / +0.20 / +0.39 | ok |
|  | RK7 | L6M | -93 / -163 | +3240 | +284 / +497 | +2124 | c=1.00: -93 / +3240 / +284 | 254 | +0.012 | +0.113 | +0.31 / +0.11 / +0.26 | ok |
|  | RK7 | L3M | +1835 / +3211 | -253 | +804 / +1407 | -6109 | c=1.00: +1835 / -253 / +804 | 143 | +0.046 | +0.504 | +0.26 / +0.14 / +0.17 | AMBER |
|  | RK7 | L6M | +1188 / +2079 | -253 | +655 / +1147 | -6109 | c=1.00: +1188 / -253 / +655 | 300 | +0.034 | +0.379 | +0.23 / +0.14 / +0.14 | AMBER |
|  | RK7 | L3M | +1083 / +1895 | -6570 | +2339 / +4093 | -4545 | c=1.00: +1083 / -6570 / +2339 | 126 | +0.161 | +1.563 | +0.36 / +0.15 / +0.28 | ok |
|  | RK7 | L6M | +758 / +1326 | -6570 | +1556 / +2723 | -4545 | c=1.00: +758 / -6570 / +1556 | 283 | +0.091 | +0.957 | +0.16 / +0.11 / +0.07 | ok |
|  | RK7 | L3M | +1089 / +1905 | -6775 | +2671 / +4674 | -2023 | c=1.00: +1089 / -6775 / +2671 | 65 | +0.358 | +1.789 | +0.15 / +0.30 / +0.25 | ok |
|  | RK7 | L6M | +1031 / +1805 | -6775 | +544 / +952 | -2023 | c=1.00: +1031 / -6775 / +544 | 146 | +0.042 | +0.227 | +0.03 / +0.15 / +0.15 | ok |
|  | RK7 | L3M | -448 / -784 | -3080 | +2629 / +4601 | +2306 | c=1.00: -448 / -3080 / +2629 | 64 | +0.304 | +1.495 | +0.23 / -0.12 / +0.07 | ok |
|  | RK7 | L6M | +100 / +175 | -3825 | +1934 / +3385 | +1857 | c=1.00: +100 / -3825 / +1934 | 136 | +0.256 | +1.288 | +0.13 / -0.04 / +0.05 | ok |
|  | RK7 | L3M | +2674 / +4680 | -8184 | +1049 / +1836 | -8732 | c=1.00: +2674 / -8184 / +1049 | 67 | +0.138 | +0.712 | +0.22 / +0.31 / +0.41 | AMBER |
|  | RK7 | L6M | +1802 / +3154 | -8184 | +2161 / +3782 | -8732 | c=1.00: +1802 / -8184 / +2161 | 175 | +0.258 | +1.674 | +0.26 / +0.20 / +0.31 | AMBER |
|  | RK7 | L3M | +1253 / +2193 | +2078 | +762 / +1333 | -2002 | c=1.00: +1253 / +2078 / +762 | 73 | +0.095 | +0.534 | +0.11 / +0.31 / +0.28 | ok |
|  | RK7 | L6M | +967 / +1691 | -1090 | +1486 / +2601 | -2002 | c=1.00: +967 / -1090 / +1486 | 179 | +0.172 | +1.140 | +0.12 / +0.20 / +0.29 | ok |
|  | RK7 | L3M | +3202 / +5604 | -2697 | -623 / -1091 | -5915 | c=1.00: +3202 / -2697 / -623 | 89 | -0.063 | -0.432 | -0.11 / +0.15 / -0.29 | AMBER |
|  | RK7 | L6M | +1959 / +3429 | -2697 | +1942 / +3398 | -5915 | c=1.00: +1959 / -2697 / +1942 | 211 | +0.196 | +1.529 | +0.00 / +0.11 / -0.04 | AMBER |
|  | RK7 | L3M | +1341 / +2346 | -263 | +2262 / +3959 | -6343 | c=1.00: +1341 / -263 / +2262 | 116 | +0.181 | +1.618 | +0.28 / +0.29 / +0.46 | AMBER |
|  | RK7 | L6M | +739 / +1293 | -263 | +1815 / +3176 | -6343 | c=1.00: +739 / -263 / +1815 | 283 | +0.114 | +1.191 | +0.27 / +0.13 / +0.23 | AMBER |
|  | RK7 | L3M | +3202 / +5604 | -2697 | -623 / -1091 | -5915 | c=1.00: +3202 / -2697 / -623 | 89 | -0.063 | -0.432 | -0.11 / +0.15 / -0.29 | AMBER |
|  | RK7 | L6M | +1959 / +3429 | -2697 | +1942 / +3398 | -5915 | c=1.00: +1959 / -2697 / +1942 | 211 | +0.196 | +1.529 | +0.00 / +0.11 / -0.04 | AMBER |
|  | RK7 | L3M | +2839 / +4968 | -7507 | +2540 / +4445 | -8113 | c=1.00: +2839 / -7507 / +2540 | 106 | +0.215 | +1.755 | -0.06 / +0.09 / +0.31 | AMBER |
|  | RK7 | L6M | +2345 / +4104 | -7507 | +1343 / +2351 | -8113 | c=1.00: +2345 / -7507 / +1343 | 255 | +0.101 | +0.953 | +0.05 / +0.01 / +0.18 | AMBER |
|  | RK7 | L3M | +1067 / +1867 | -5684 | +1426 / +2495 | -1359 | c=1.00: +1067 / -5684 / +1426 | 113 | +0.062 | +0.543 | +0.41 / +0.14 / +0.44 | ok |
|  | RK7 | L6M | +716 / +1253 | -5684 | +1544 / +2703 | -1359 | c=1.00: +716 / -5684 / +1544 | 227 | +0.104 | +0.873 | +0.32 / +0.15 / +0.29 | ok |
|  | RK7 | L3M | +554 / +969 | -3130 | +2059 / +3602 | -2449 | c=1.00: +554 / -3130 / +2059 | 61 | +0.222 | +1.044 | +0.19 / -0.08 / +0.13 | ok |
|  | RK7 | L6M | +454 / +794 | -3130 | +1725 / +3020 | -2449 | c=1.00: +454 / -3130 / +1725 | 138 | +0.218 | +1.114 | +0.12 / -0.06 / +0.15 | ok |
|  | RK7 | L3M | +216 / +379 | -2625 | +3043 / +5325 | +1004 | c=1.00: +216 / -2625 / +3043 | 94 | +0.237 | +1.716 | +0.24 / +0.11 / +0.42 | ok |
|  | RK7 | L6M | +67 / +117 | -2625 | +1707 / +2987 | +1004 | c=1.00: +67 / -2625 / +1707 | 211 | +0.111 | +0.869 | +0.14 / +0.11 / +0.24 | ok |
|  | RK7 | L3M | +2101 / +3677 | -3749 | +2391 / +4184 | -6684 | c=1.00: +2101 / -3749 / +2391 | 85 | +0.295 | +1.929 | -0.00 / +0.25 / +0.17 | AMBER |
|  | RK7 | L6M | +1277 / +2235 | -3749 | +1036 / +1812 | -6684 | c=1.00: +1277 / -3749 / +1036 | 182 | +0.108 | +0.726 | -0.04 / +0.20 / +0.15 | AMBER |
|  | RK7 | L3M | +608 / +1063 | -1545 | +1912 / +3346 | -1539 | c=1.00: +608 / -1545 / +1912 | 80 | +0.247 | +1.523 | -0.04 / -0.07 / +0.15 | ok |
|  | RK7 | L6M | +533 / +934 | -1545 | +3080 / +5390 | -1539 | c=1.00: +533 / -1545 / +3080 | 181 | +0.366 | +2.453 | -0.02 / -0.04 / +0.18 | ok |
|  | RK7 | L3M | +579 / +1013 | +1131 | +1965 / +3440 | -612 | c=1.00: +579 / +1131 / +1965 | 213 | +0.058 | +0.943 | +0.21 / +0.11 / +0.40 | ok |
|  | RK7 | L6M | +362 / +634 | +1131 | +2726 / +4770 | -612 | c=1.00: +362 / +1131 / +2726 | 485 | +0.101 | +1.812 | +0.19 / +0.04 / +0.19 | ok |
|  | RK7 | L3M | +3305 / +5784 | -4928 | -334 / -584 | -11231 | c=1.00: +3305 / -4928 / -334 | 80 | -0.022 | -0.134 | +0.01 / +0.19 / +0.17 | RED |
|  | RK7 | L6M | +2040 / +3571 | -4928 | +694 / +1215 | -11231 | c=1.00: +2040 / -4928 / +694 | 177 | +0.082 | +0.537 | -0.05 / +0.15 / +0.10 | RED |
|  | RK7 | L3M | +2166 / +3791 | -4760 | +1740 / +3045 | -9339 | c=1.00: +2166 / -4760 / +1740 | 49 | +0.253 | +0.954 | +0.17 / +0.17 / +0.38 | RED |
|  | RK7 | L6M | +1363 / +2385 | -4760 | +1861 / +3257 | -9339 | c=1.00: +1363 / -4760 / +1861 | 125 | +0.246 | +1.137 | +0.16 / +0.14 / +0.40 | RED |
|  | RK7 | L3M | +995 / +1742 | -1718 | +2282 / +3993 | -2545 | c=1.00: +995 / -1718 / +2282 | 136 | +0.110 | +1.154 | +0.02 / +0.32 / +0.17 | ok |
|  | RK7 | L6M | +768 / +1343 | -1718 | +2112 / +3695 | -2545 | c=1.00: +768 / -1718 / +2112 | 275 | +0.117 | +1.196 | +0.05 / +0.23 / +0.16 | ok |
|  | RK7 | L3M | +1982 / +3469 | -2980 | -787 / -1378 | -4332 | c=1.00: +1982 / -2980 / -787 | 65 | -0.288 | -1.438 | -0.15 / -0.00 / +0.00 | AMBER |
|  | RK7 | L6M | +1219 / +2133 | -2980 | +900 / +1575 | -4332 | c=1.00: +1219 / -2980 / +900 | 147 | +0.058 | +0.315 | -0.08 / -0.03 / +0.05 | ok |
|  | RK7 | L3M | +4047 / +7082 | -3535 | +350 / +613 | -12829 | c=1.00: +4047 / -3535 / +350 | 62 | -0.078 | -0.372 | -0.16 / +0.04 / +0.02 | RED |
|  | RK7 | L6M | +2645 / +4629 | -3535 | -13 / -22 | -12829 | c=1.00: +2645 / -3535 / -13 | 148 | -0.069 | -0.379 | -0.04 / +0.01 / -0.01 | RED |
|  | RK7 | L3M | +995 / +1742 | -1718 | +2282 / +3993 | -2545 | c=1.00: +995 / -1718 / +2282 | 136 | +0.110 | +1.154 | +0.02 / +0.32 / +0.17 | ok |
|  | RK7 | L6M | +768 / +1343 | -1718 | +2112 / +3695 | -2545 | c=1.00: +768 / -1718 / +2112 | 275 | +0.117 | +1.196 | +0.05 / +0.23 / +0.16 | ok |
|  | RK7 | L3M | +848 / +1484 | -5920 | +2149 / +3761 | -1844 | c=1.00: +848 / -5920 / +2149 | 60 | +0.308 | +1.420 | +0.20 / -0.02 / +0.06 | ok |
|  | RK7 | L6M | +808 / +1414 | -5920 | +2255 / +3946 | -1844 | c=1.00: +808 / -5920 / +2255 | 135 | +0.351 | +1.757 | +0.05 / +0.02 / +0.04 | ok |
|  | RK7 | L3M | +3582 / +6269 | -6275 | +525 / +919 | -12520 | c=1.00: +3582 / -6275 / +525 | 79 | -0.013 | -0.079 | +0.32 / +0.29 / +0.45 | RED |
|  | RK7 | L6M | +2380 / +4165 | -6275 | +729 / +1276 | -12520 | c=1.00: +2380 / -6275 / +729 | 155 | +0.036 | +0.207 | +0.27 / +0.16 / +0.39 | RED |
|  | RK7 | L3M | +5512 / +9646 | -8519 | +1006 / +1761 | -17768 | c=1.00: +5512 / -8519 / +1006 | 95 | +0.031 | +0.227 | +0.01 / +0.22 / +0.34 | RED |
|  | RK7 | L3M | +1477 / +2585 | -3954 | +973 / +1704 | -4191 | c=1.00: +1477 / -3954 / +973 | 123 | +0.012 | +0.117 | +0.22 / +0.27 / +0.30 | ok |
|  | RK7 | L6M | +1008 / +1763 | -3954 | +674 / +1180 | -4191 | c=1.00: +1008 / -3954 / +674 | 259 | +0.010 | +0.096 | +0.18 / +0.25 / +0.21 | ok |
|  | RK7 | L3M | +2184 / +3821 | -5580 | -501 / -876 | -4008 | c=1.00: +2184 / -5580 / -501 | 63 | -0.071 | -0.344 | -0.14 / +0.13 / -0.09 | AMBER |
|  | RK7 | L6M | +1382 / +2418 | -5580 | -41 / -73 | -4008 | c=1.00: +1382 / -5580 / -41 | 148 | -0.004 | -0.024 | -0.13 / +0.13 / -0.05 | ok |
|  | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=1.00: -504 / -3120 / +2902 | 62 | +0.356 | +1.698 | +0.25 / -0.07 / +0.11 | ok |
|  | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=1.00: -58 / -3120 / +2291 | 136 | +0.327 | +1.650 | +0.06 / -0.03 / +0.02 | ok |
|  | RK7 | L3M | +1505 / +2635 | -6225 | +1791 / +3134 | -4696 | c=1.00: +1505 / -6225 / +1791 | 42 | +0.228 | +0.737 | -0.03 / -0.06 / +0.11 | AMBER |
|  | RK7 | L6M | +1198 / +2096 | -6225 | +1528 / +2674 | -4696 | c=1.00: +1198 / -6225 / +1528 | 92 | +0.247 | +0.842 | -0.01 / +0.02 / +0.12 | AMBER |
|  | RK7 | L3M | +1782 / +3118 | -3699 | -688 / -1203 | -5977 | c=1.00: +1782 / -3699 / -688 | 207 | -0.041 | -0.658 | +0.07 / -0.15 / +0.01 | AMBER |
|  | RK7 | L6M | +1264 / +2212 | -3699 | +711 / +1244 | -5977 | c=1.00: +1264 / -3699 / +711 | 446 | +0.020 | +0.332 | +0.21 / +0.02 / +0.07 | AMBER |
|  | RK7 | L3M | +2134 / +3735 | -7630 | +2005 / +3508 | -5491 | c=1.00: +2134 / -7630 / +2005 | 64 | +0.210 | +1.036 | +0.03 / +0.23 / +0.24 | AMBER |
|  | RK7 | L6M | +1484 / +2597 | -7630 | -130 / -228 | -5491 | c=1.00: +1484 / -7630 / -130 | 155 | -0.083 | -0.476 | -0.04 / +0.14 / +0.11 | AMBER |
|  | RK7 | L3M | +1051 / +1839 | +745 | +1695 / +2966 | -6259 | c=1.00: +1051 / +745 / +1695 | 97 | +0.201 | +1.499 | +0.33 / +0.10 / +0.15 | AMBER |
|  | RK7 | L6M | +527 / +922 | +745 | +950 / +1662 | -6259 | c=1.00: +527 / +745 / +950 | 218 | +0.084 | +0.674 | +0.28 / +0.02 / +0.01 | AMBER |
|  | RK7 | L3M | +1882 / +3294 | +124 | -160 / -280 | -5503 | c=1.00: +1882 / +124 / -160 | 139 | -0.066 | -0.708 | +0.09 / +0.22 / +0.27 | AMBER |
|  | RK7 | L6M | +1257 / +2201 | +124 | +449 / +786 | -5503 | c=1.00: +1257 / +124 / +449 | 303 | +0.005 | +0.052 | +0.07 / +0.17 / +0.08 | AMBER |
|  | RK7 | L3M | +4324 / +7567 | -2990 | -599 / -1048 | -12429 | c=1.00: +4324 / -2990 / -599 | 64 | -0.173 | -0.851 | -0.11 / -0.01 / +0.02 | RED |
|  | RK7 | L6M | +2784 / +4872 | -2990 | +769 / +1346 | -12429 | c=1.00: +2784 / -2990 / +769 | 135 | +0.074 | +0.369 | -0.11 / +0.02 / +0.07 | RED |
|  | RK7 | L3M | +2729 / +4776 | -6937 | +727 / +1273 | -9245 | c=1.00: +2729 / -6937 / +727 | 88 | +0.032 | +0.219 | +0.15 / -0.05 / +0.15 | AMBER |
|  | RK7 | L6M | +1847 / +3232 | -6937 | +975 / +1706 | -9245 | c=1.00: +1847 / -6937 / +975 | 193 | +0.066 | +0.474 | +0.12 / +0.04 / +0.14 | AMBER |
|  | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=1.00: +1894 / -3780 / +589 | 74 | +0.067 | +0.382 | +0.03 / +0.06 / -0.01 | AMBER |
|  | RK7 | L3M | +1790 / +3133 | -5825 | +1045 / +1829 | -8965 | c=1.00: +1790 / -5825 / +1045 | 59 | +0.051 | +0.232 | -0.08 / -0.03 / -0.13 | AMBER |
|  | RK7 | L6M | +1557 / +2724 | -5825 | -188 / -329 | -8965 | c=1.00: +1557 / -5825 / -188 | 131 | -0.132 | -0.643 | +0.01 / -0.02 / +0.05 | AMBER |
|  | RK7 | L3M | +2577 / +4510 | -10490 | +1047 / +1833 | -8025 | c=1.00: +2577 / -10490 / +1047 | 266 | +0.065 | +1.320 | +0.13 / +0.10 / +0.13 | AMBER |
|  | RK7 | L3M | +1366 / +2391 | -4110 | +1411 / +2468 | -2433 | c=1.00: +1366 / -4110 / +1411 | 137 | +0.042 | +0.445 | +0.13 / -0.02 / +0.23 | ok |
|  | RK7 | L6M | +966 / +1691 | -4110 | +1280 / +2240 | -2433 | c=1.00: +966 / -4110 / +1280 | 268 | +0.064 | +0.636 | +0.07 / +0.01 / +0.21 | ok |
|  | RK7 | L3M | +2856 / +4997 | -3740 | +306 / +535 | -9009 | c=1.00: +2856 / -3740 / +306 | 72 | -0.001 | -0.007 | -0.17 / -0.02 / +0.03 | AMBER |
|  | RK7 | L6M | +2058 / +3602 | -3740 | +1572 / +2751 | -9009 | c=1.00: +2058 / -3740 / +1572 | 167 | +0.173 | +1.069 | -0.10 / -0.02 / +0.16 | AMBER |
|  | RK7 | L3M | +533 / +933 | -5805 | +1089 / +1906 | -929 | c=1.00: +533 / -5805 / +1089 | 62 | +0.084 | +0.398 | +0.23 / -0.05 / -0.02 | ok |
|  | RK7 | L6M | +653 / +1142 | -5805 | +971 / +1699 | -929 | c=1.00: +653 / -5805 / +971 | 137 | +0.124 | +0.627 | +0.10 / +0.01 / +0.02 | ok |
|  | RK7 | L3M | +1790 / +3133 | -5825 | +1045 / +1829 | -8965 | c=1.00: +1790 / -5825 / +1045 | 59 | +0.051 | +0.232 | -0.08 / -0.03 / -0.13 | AMBER |
|  | RK7 | L6M | +1555 / +2721 | -5825 | -198 / -346 | -8965 | c=1.00: +1555 / -5825 / -198 | 131 | -0.134 | -0.651 | +0.01 / -0.02 / +0.05 | AMBER |
|  | RK7 | L3M | +4455 / +7796 | -8750 | +1337 / +2340 | -12915 | c=1.00: +4455 / -8750 / +1337 | 60 | +0.182 | +0.840 | -0.38 / -0.01 / -0.09 | RED |
|  | RK7 | L6M | +2971 / +5199 | -8750 | +225 / +393 | -12915 | c=1.00: +2971 / -8750 / +225 | 147 | +0.008 | +0.041 | -0.22 / -0.08 / -0.13 | RED |
|  | RK7 | L3M | +2761 / +4832 | -5423 | -889 / -1556 | -8102 | c=1.00: +2761 / -5423 / -889 | 95 | -0.155 | -1.136 | -0.03 / -0.24 / -0.03 | AMBER |
|  | RK7 | L6M | +1748 / +3059 | -5423 | -200 / -349 | -8102 | c=1.00: +1748 / -5423 / -200 | 209 | -0.066 | -0.510 | -0.01 / -0.17 / -0.07 | AMBER |
|  | RK7 | L3M | +1445 / +2528 | -5745 | +820 / +1435 | -3785 | c=1.00: +1445 / -5745 / +820 | 129 | +0.045 | +0.450 | +0.16 / -0.02 / +0.19 | ok |
|  | RK7 | L6M | +1039 / +1817 | -5745 | +879 / +1538 | -3785 | c=1.00: +1039 / -5745 / +879 | 260 | +0.056 | +0.542 | +0.09 / -0.01 / +0.05 | ok |
|  | RK7 | L3M | +1509 / +2640 | -1962 | -33 / -58 | -2958 | c=1.00: +1509 / -1962 / -33 | 116 | -0.026 | -0.232 | -0.10 / +0.06 / +0.01 | ok |
|  | RK7 | L6M | +1129 / +1976 | -1962 | +2243 / +3924 | -2958 | c=1.00: +1129 / -1962 / +2243 | 244 | +0.177 | +1.600 | -0.04 / +0.01 / +0.05 | ok |
|  | RK7 | L3M | +2676 / +4682 | -3476 | +686 / +1201 | -7132 | c=1.00: +2676 / -3476 / +686 | 136 | +0.026 | +0.271 | -0.05 / +0.02 / +0.14 | AMBER |
|  | RK7 | L6M | +1617 / +2830 | -3476 | +451 / +790 | -7132 | c=1.00: +1617 / -3476 / +451 | 310 | +0.017 | +0.192 | +0.02 / +0.01 / -0.08 | AMBER |
|  | RK7 | L3M | +2016 / +3529 | -6530 | +1134 / +1984 | -8996 | c=1.00: +2016 / -6530 / +1134 | 54 | +0.074 | +0.306 | -0.14 / -0.01 / -0.13 | AMBER |
|  | RK7 | L6M | +1584 / +2771 | -6530 | +174 / +305 | -8996 | c=1.00: +1584 / -6530 / +174 | 127 | -0.073 | -0.341 | -0.04 / -0.05 / +0.05 | AMBER |
|  | RK7 | L3M | +892 / +1561 | +969 | +1557 / +2726 | -3857 | c=1.00: +892 / +969 / +1557 | 70 | +0.273 | +1.469 | +0.16 / +0.22 / +0.25 | ok |
|  | RK7 | L6M | +634 / +1109 | +969 | +856 / +1497 | -3857 | c=1.00: +634 / +969 / +856 | 176 | +0.114 | +0.745 | +0.12 / +0.15 / +0.24 | ok |
|  | RK7 | L3M | +1786 / +3125 | -4039 | -24 / -42 | -4160 | c=1.00: +1786 / -4039 / -24 | 60 | +0.035 | +0.161 | +0.18 / -0.10 / +0.16 | AMBER |
|  | RK7 | L6M | +1129 / +1976 | -4039 | +626 / +1095 | -4160 | c=1.00: +1129 / -4039 / +626 | 132 | +0.106 | +0.520 | +0.14 / -0.05 / +0.19 | ok |
|  | RK7 | L3M | +1296 / +2267 | -1865 | +617 / +1079 | -2328 | c=1.00: +1296 / -1865 / +617 | 80 | -0.033 | -0.206 | +0.18 / -0.06 / +0.35 | ok |
|  | RK7 | L6M | +887 / +1553 | -1865 | +557 / +974 | -2328 | c=1.00: +887 / -1865 / +557 | 163 | -0.006 | -0.034 | +0.18 / -0.03 / +0.24 | ok |
|  | RK7 | L3M | +1508 / +2639 | -4055 | -214 / -375 | -5075 | c=1.00: +1508 / -4055 / -214 | 72 | -0.123 | -0.679 | +0.03 / +0.04 / -0.03 | AMBER |
|  | RK7 | L6M | +1032 / +1806 | -4055 | +1009 / +1766 | -5075 | c=1.00: +1032 / -4055 / +1009 | 164 | +0.078 | +0.475 | +0.04 / +0.05 / +0.07 | AMBER |
|  | RK7 | L3M | +1398 / +2446 | -1700 | +750 / +1312 | -4989 | c=1.00: +1398 / -1700 / +750 | 70 | +0.086 | +0.463 | +0.01 / -0.00 / +0.08 | AMBER |
|  | RK7 | L6M | +1112 / +1946 | -3860 | +592 / +1036 | -4989 | c=1.00: +1112 / -3860 / +592 | 156 | +0.072 | +0.419 | -0.03 / +0.05 / +0.16 | AMBER |
|  | RK7 | L3M | +6285 / +10999 | -6194 | -401 / -702 | -20465 | c=1.00: +6285 / -6194 / -401 | 89 | -0.039 | -0.267 | +0.06 / +0.12 / +0.13 | RED |
|  | RK7 | L6M | +3911 / +6844 | -6194 | +1425 / +2494 | -20465 | c=1.00: +3911 / -6194 / +1425 | 221 | +0.122 | +0.998 | +0.05 / +0.10 / +0.18 | RED |
|  | RK7 | L3M | +3766 / +6591 | -6054 | +908 / +1590 | -13173 | c=1.00: +3766 / -6054 / +908 | 90 | +0.045 | +0.314 | -0.09 / +0.43 / +0.16 | RED |
|  | RK7 | L6M | +2534 / +4435 | -6054 | +1482 / +2593 | -13173 | c=1.00: +2534 / -6054 / +1482 | 210 | +0.117 | +0.910 | -0.05 / +0.23 / +0.05 | RED |
|  | RK7 | L3M | +2945 / +5153 | -6070 | +190 / +332 | -10271 | c=1.00: +2945 / -6070 / +190 | 77 | +0.041 | +0.242 | +0.17 / +0.03 / +0.20 | RED |
|  | RK7 | L6M | +1977 / +3459 | -6070 | +63 / +111 | -10271 | c=1.00: +1977 / -6070 / +63 | 178 | -0.012 | -0.081 | +0.06 / +0.04 / +0.12 | RED |
|  | RH7 | L3M | -1427 / -2497 | -21 | +1801 / +3151 | +5671 | c=1.00: -1427 / -21 / +1801 | 63 | +0.352 | +1.707 | +0.26 / -0.07 / +0.11 | ok |
|  | RH7 | L6M | -637 / -1114 | -1686 | +1537 / +2690 | +4180 | c=1.00: -637 / -1686 / +1537 | 136 | +0.324 | +1.634 | +0.07 / -0.03 / +0.02 | ok |
|  | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=1.00: -504 / -3120 / +2902 | 62 | +0.356 | +1.698 | +0.25 / -0.07 / +0.11 | ok |
|  | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=1.00: -58 / -3120 / +2291 | 136 | +0.327 | +1.650 | +0.06 / -0.03 / +0.02 | ok |
|  | RK7 | Y2023 | -1698 / -2972 | -7720 | -122 / -213 | -4200 | c=1.00: -1698 / -7720 / -122 | 182 | +0.096 | +0.448 | +0.07 / +0.04 / +0.23 | ok |
|  | RK7 | Y2024 | -1956 / -3423 | -882 | +670 / +1172 | +8949 | c=1.00: -1956 / -882 / +670 | 256 | +0.128 | +0.620 | -0.01 / +0.02 / +0.14 | ok |
|  | RK7 | Y2025 | -5837 / -10214 | +6385 | -137 / -239 | +13807 | c=1.00: -5837 / +6385 / -137 | 269 | +0.103 | +0.520 | +0.00 / -0.01 / +0.02 | ok |
|  | RM7 | L3M | -1391 / -2434 | -100 | +1273 / +2228 | +6039 | c=1.00: -1391 / -100 / +1273 | 63 | +0.352 | +1.707 | +0.26 / -0.07 / +0.11 | ok |
|  | RM7 | L6M | -799 / -1397 | -100 | +1497 / +2620 | +6039 | c=1.00: -799 / -100 / +1497 | 136 | +0.324 | +1.634 | +0.07 / -0.03 / +0.02 | ok |
|  | RK7 | L3M | +2371 / +4149 | -10570 | +1932 / +3382 | -4795 | c=1.00: +2371 / -10570 / +1932 | 68 | +0.206 | +1.076 | +0.01 / +0.15 / +0.27 | AMBER |
|  | RK7 | L6M | +1668 / +2919 | -10570 | -704 / -1233 | -4795 | c=1.00: +1668 / -10570 / -704 | 159 | -0.171 | -1.010 | +0.01 / +0.05 / +0.08 | AMBER |
|  | RK7 | L3M | +4794 / +8390 | -6578 | -1205 / -2110 | -15048 | c=1.00: +4794 / -6578 / -1205 | 122 | -0.134 | -1.262 | -0.02 / +0.04 / -0.02 | RED |
|  | RK7 | L6M | +2974 / +5205 | -6578 | +563 / +986 | -15048 | c=1.00: +2974 / -6578 / +563 | 294 | +0.011 | +0.122 | +0.04 / -0.01 / +0.02 | RED |
|  | RK7 | L3M | +1152 / +2017 | -5520 | +1785 / +3124 | -4853 | c=1.00: +1152 / -5520 / +1785 | 64 | +0.213 | +1.050 | +0.12 / +0.02 / +0.18 | AMBER |
|  | RK7 | L6M | +921 / +1611 | -5520 | -90 / -157 | -4853 | c=1.00: +921 / -5520 / -90 | 151 | -0.062 | -0.347 | +0.06 / +0.09 / +0.17 | AMBER |
|  | RK7 | L3M | +672 / +1176 | -1495 | +489 / +856 | -2865 | c=1.00: +672 / -1495 / +489 | 64 | +0.081 | +0.397 | +0.23 / +0.19 / -0.03 | ok |
|  | RK7 | L6M | +644 / +1128 | -2270 | +1360 / +2380 | -2865 | c=1.00: +644 / -2270 / +1360 | 143 | +0.212 | +1.124 | +0.09 / +0.15 / +0.13 | ok |
|  | RK7 | L3M | +6756 / +11822 | -7289 | -1593 / -2787 | -20323 | c=1.00: +6756 / -7289 / -1593 | 79 | -0.203 | -1.231 | +0.11 / +0.19 / +0.20 | RED |
|  | RK7 | L6M | +4461 / +7807 | -7289 | -24 / -43 | -20323 | c=1.00: +4461 / -7289 / -24 | 193 | -0.004 | -0.031 | -0.04 / +0.13 / +0.18 | RED |
|  | RK7 | L3M | +3071 / +5375 | -6920 | +821 / +1436 | -11572 | c=1.00: +3071 / -6920 / +821 | 93 | +0.093 | +0.663 | +0.08 / +0.08 / +0.08 | RED |
|  | RK7 | L6M | +2351 / +4115 | -7325 | -236 / -414 | -11572 | c=1.00: +2351 / -7325 / -236 | 192 | -0.035 | -0.248 | +0.04 / +0.08 / +0.09 | RED |
|  | RK7 | L3M | +320 / +561 | -2845 | +1622 / +2838 | -2109 | c=1.00: +320 / -2845 / +1622 | 81 | +0.100 | +0.622 | +0.43 / +0.07 / +0.30 | ok |
|  | RK7 | L6M | +409 / +716 | -2845 | +1093 / +1913 | -2109 | c=1.00: +409 / -2845 / +1093 | 166 | +0.060 | +0.371 | +0.33 / +0.09 / +0.32 | ok |
|  | RK7 | L3M | +1287 / +2252 | -3120 | +1800 / +3150 | -5514 | c=1.00: +1287 / -3120 / +1800 | 63 | +0.203 | +0.981 | +0.14 / -0.21 / +0.20 | AMBER |
|  | RK7 | L6M | +1052 / +1841 | -3870 | +1790 / +3133 | -5514 | c=1.00: +1052 / -3870 / +1790 | 141 | +0.249 | +1.299 | +0.08 / -0.07 / +0.08 | AMBER |
|  | ADD | L3M | -870 / -1522 | +4026 | +1542 / +2698 | +3571 | c=1.00: -870 / +4026 / +1542 | 137 | +0.123 | +1.293 | +0.29 / +0.22 / +0.37 | ok |
|  | ADD | L6M | -453 / -793 | +1209 | +1117 / +1955 | +3571 | c=1.00: -453 / +1209 / +1117 | 284 | +0.078 | +0.818 | +0.24 / +0.13 / +0.22 | ok |
|  | ADD | Y2023 | -2846 / -4981 | -1247 | +1148 / +2008 | +888 | c=1.00: -2846 / -1247 / +1148 | 373 | +0.098 | +0.934 | +0.39 / +0.02 / +0.32 | ok |
|  | ADD | Y2024 | -3407 / -5962 | -1205 | +524 / +917 | +662 | c=1.00: -3407 / -1205 / +524 | 563 | +0.051 | +0.545 | +0.35 / +0.15 / +0.39 | ok |
|  | ADD | Y2025 | -5757 / -10074 | +871 | +1138 / +1992 | +12500 | c=1.00: -5757 / +871 / +1138 | 580 | +0.103 | +1.127 | +0.09 / +0.05 / +0.16 | ok |
|  | ADDLO | L3M | -384 / -673 | +521 | +843 / +1475 | +1210 | c=1.00: -384 / +521 / +843 | 81 | +0.127 | +0.792 | +0.29 / +0.14 / +0.15 | ok |
|  | ADDLO | L6M | -112 / -196 | -11 | +115 / +202 | +1210 | c=1.00: -112 / -11 / +115 | 156 | +0.015 | +0.084 | +0.20 / +0.10 / +0.17 | ok |
|  | ADDSO | L3M | -452 / -792 | +2360 | +487 / +852 | +2360 | c=1.00: -452 / +2360 / +487 | 72 | +0.106 | +0.590 | +0.17 / +0.16 / +0.33 | ok |
|  | ADDSO | L6M | -252 / -440 | +2360 | +806 / +1410 | +2360 | c=1.00: -252 / +2360 / +806 | 155 | +0.122 | +0.700 | +0.14 / +0.07 / +0.13 | ok |
|  | ADD | L3M | +2154 / +3770 | -3819 | -1223 / -2140 | -6573 | c=1.00: +2154 / -3819 / -1223 | 65 | -0.301 | -1.506 | -0.07 / +0.08 / +0.06 | AMBER |
|  | ADD | L6M | +1399 / +2449 | -3819 | -1192 / -2087 | -6573 | c=1.00: +1399 / -3819 / -1192 | 162 | -0.204 | -1.222 | -0.04 / +0.05 / -0.13 | AMBER |
|  | ADD | L3M | -916 / -1603 | -1005 | +376 / +657 | +4548 | c=1.00: -916 / -1005 / +376 | 60 | +0.067 | +0.311 | +0.11 / -0.02 / +0.26 | ok |
|  | ADD | L6M | -635 / -1112 | -1005 | +564 / +987 | +4548 | c=1.00: -635 / -1005 / +564 | 134 | +0.143 | +0.712 | +0.01 / -0.01 / +0.18 | ok |
|  | ADD | Y2023 | +772 / +1351 | -2849 | +118 / +207 | +777 | c=1.00: +772 / -2849 / +118 | 203 | +0.019 | +0.098 | +0.06 / +0.18 / +0.10 | ok |
|  | ADD | Y2024 | -3059 / -5353 | -2390 | +572 / +1001 | +2784 | c=1.00: -3059 / -2390 / +572 | 266 | +0.111 | +0.558 | +0.00 / +0.00 / +0.07 | ok |
|  | ADD | Y2025 | -7007 / -12263 | +4809 | +1287 / +2252 | +7790 | c=1.00: -7007 / +4809 / +1287 | 276 | +0.190 | +0.989 | -0.02 / -0.01 / +0.03 | ok |
|  | ADD | L3M | -651 / -1140 | +2680 | +825 / +1443 | +2850 | c=1.00: -651 / +2680 / +825 | 132 | +0.039 | +0.391 | +0.22 / +0.20 / +0.52 | ok |
|  | ADD | L6M | -391 / -684 | +1590 | +1064 / +1862 | +2850 | c=1.00: -391 / +1590 / +1064 | 272 | +0.068 | +0.689 | +0.19 / +0.19 / +0.27 | ok |
|  | ADD | Y2023 | +2623 / +4590 | -2252 | +204 / +358 | -6113 | c=1.00: +2623 / -2252 / +204 | 315 | +0.021 | +0.169 | +0.24 / -0.02 / +0.27 | ok |
|  | ADD | Y2024 | -2344 / -4102 | -1070 | +327 / +572 | -371 | c=1.00: -2344 / -1070 / +327 | 463 | +0.052 | +0.453 | +0.27 / +0.05 / +0.28 | ok |
|  | ADD | Y2025 | -5002 / -8753 | +2245 | +446 / +780 | +11816 | c=1.00: -5002 / +2245 / +446 | 505 | +0.066 | +0.626 | +0.24 / +0.05 / +0.22 | ok |
|  | ADD | L3M | -564 / -986 | +2395 | +846 / +1481 | +3495 | c=1.00: -564 / +2395 / +846 | 38 | +0.261 | +0.762 | +0.37 / -0.05 / +0.13 | ok |
|  | ADD | L6M | -183 / -321 | -471 | +557 / +976 | +3495 | c=1.00: -183 / -471 / +557 | 89 | +0.131 | +0.431 | +0.14 / -0.04 / +0.26 | ok |
|  | ADD | L3M | -456 / -798 | +1134 | +1935 / +3386 | +2888 | c=1.00: -456 / +1134 / +1935 | 165 | +0.127 | +1.616 | +0.20 / +0.13 / +0.39 | ok |
|  | ADD | L6M | -262 / -458 | +1134 | +1965 / +3439 | +2888 | c=1.00: -262 / +1134 / +1965 | 383 | +0.125 | +1.767 | +0.15 / +0.08 / +0.16 | ok |
|  | ADD | Y2023 | -468 / -819 | -3097 | +1201 / +2102 | -1427 | c=1.00: -468 / -3097 / +1201 | 358 | +0.101 | +0.931 | +0.18 / +0.16 / +0.25 | ok |
|  | ADD | Y2024 | -5557 / -9725 | +2660 | +938 / +1642 | +12005 | c=1.00: -5557 / +2660 / +938 | 541 | +0.086 | +0.876 | +0.15 / +0.09 / +0.21 | ok |
|  | ADD | Y2025 | -4939 / -8644 | +674 | +1132 / +1981 | +9036 | c=1.00: -4939 / +674 / +1132 | 656 | +0.102 | +1.268 | +0.17 / +0.05 / +0.06 | ok |
|  | ADD | L3M | -8 / -15 | -5150 | +1214 / +2124 | -3058 | c=1.00: -8 / -5150 / +1214 | 127 | +0.119 | +1.163 | +0.15 / -0.01 / +0.20 | ok |
|  | ADD | L6M | +129 / +225 | -5150 | +1452 / +2540 | -3058 | c=1.00: +129 / -5150 / +1452 | 264 | +0.137 | +1.337 | +0.02 / +0.03 / +0.01 | ok |
|  | ADD | L3M | +43 / +76 | +351 | +528 / +925 | +115 | c=1.00: +43 / +351 / +528 | 71 | +0.068 | +0.369 | +0.34 / +0.20 / +0.29 | ok |
|  | ADD | L6M | +170 / +297 | +351 | -181 / -317 | +115 | c=1.00: +170 / +351 / -181 | 160 | -0.026 | -0.155 | +0.22 / +0.17 / +0.13 | ok |
|  | ADD | L3M | +833 / +1458 | -4696 | -1022 / -1789 | -2260 | c=1.00: +833 / -4696 / -1022 | 61 | -0.170 | -0.798 | +0.16 / -0.02 / +0.20 | ok |
|  | ADD | L6M | +496 / +868 | -4696 | +866 / +1516 | -2260 | c=1.00: +496 / -4696 / +866 | 137 | +0.166 | +0.843 | +0.15 / +0.03 / +0.19 | ok |
|  | ADD | L3M | +3496 / +6118 | -6071 | +533 / +933 | -9516 | c=1.00: +3496 / -6071 / +533 | 214 | +0.021 | +0.338 | +0.12 / +0.10 / +0.23 | RED |
|  | ADD | L6M | +2315 / +4051 | -6071 | +306 / +535 | -9516 | c=1.00: +2315 / -6071 / +306 | 551 | +0.013 | +0.270 | +0.09 / +0.09 / +0.26 | RED |
|  | ADD | L3M | +1090 / +1907 | -7456 | +2426 / +4246 | -2914 | c=1.00: +1090 / -7456 / +2426 | 152 | +0.207 | +2.422 | +0.23 / +0.13 / +0.13 | ok |
|  | ADD | L6M | +563 / +985 | -7456 | +1149 / +2010 | -2914 | c=1.00: +563 / -7456 / +1149 | 341 | +0.085 | +1.070 | +0.11 / +0.13 / +0.05 | ok |
|  | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=1.00: -1573 / +95 / +2075 | 62 | +0.326 | +1.553 | +0.23 / -0.07 / +0.10 | ok |
|  | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=1.00: -795 / -796 / +1691 | 135 | +0.312 | +1.560 | +0.05 / -0.03 / +0.01 | ok |
|  | ADD | Y2023 | -2295 / -4017 | -2303 | +538 / +941 | -4865 | c=1.00: -2295 / -2303 / +538 | 182 | +0.096 | +0.448 | +0.07 / +0.04 / +0.23 | ok |
|  | ADD | Y2024 | -833 / -1458 | +2233 | +748 / +1310 | +5769 | c=1.00: -833 / +2233 / +748 | 256 | +0.128 | +0.620 | -0.01 / +0.02 / +0.14 | ok |
|  | ADD | Y2025 | -7264 / -12712 | +4440 | +734 / +1284 | +15413 | c=1.00: -7264 / +4440 / +734 | 268 | +0.109 | +0.554 | +0.01 / -0.01 / +0.03 | ok |
|  | ADDLO | L3M | +607 / +1063 | -2710 | -100 / -175 | -5829 | c=1.00: +607 / -2710 / -100 | 55 | +0.162 | +0.687 | +0.07 / +0.00 / -0.14 | AMBER |
|  | ADDLO | L6M | +615 / +1077 | -2710 | -714 / -1250 | -5829 | c=1.00: +615 / -2710 / -714 | 123 | -0.061 | -0.278 | +0.07 / +0.01 / +0.05 | AMBER |
|  | ADDLO | Y2023 | -3611 / -6319 | -798 | +633 / +1107 | +5713 | c=1.00: -3611 / -798 / +633 | 182 | +0.113 | +0.527 | +0.05 / +0.13 / +0.07 | ok |
|  | ADDLO | Y2024 | -1802 / -3153 | +2395 | +774 / +1354 | -2441 | c=1.00: -1802 / +2395 / +774 | 235 | +0.163 | +0.722 | -0.06 / -0.03 / -0.14 | ok |
|  | ADDLO | Y2025 | +1692 / +2961 | -9745 | +86 / +150 | -11229 | c=1.00: +1692 / -9745 / +86 | 261 | +0.013 | +0.065 | -0.01 / +0.04 / -0.07 | ok |
|  | ADDSO | L3M | +470 / +823 | -1616 | -471 / -824 | +1181 | c=1.00: +470 / -1616 / -471 | 56 | -0.087 | -0.376 | +0.05 / -0.01 / +0.29 | ok |
|  | ADDSO | L6M | +277 / +485 | -1616 | +776 / +1358 | +1181 | c=1.00: +277 / -1616 / +776 | 126 | +0.160 | +0.748 | -0.01 / -0.00 / +0.06 | ok |
|  | ADD | L3M | +1505 / +2634 | -1265 | +1153 / +2018 | -6828 | c=1.00: +1505 / -1265 / +1153 | 211 | +0.069 | +1.122 | -0.18 / -0.08 / +0.14 | AMBER |
|  | ADD | L6M | +1067 / +1868 | -1559 | +281 / +491 | -6828 | c=1.00: +1067 / -1559 / +281 | 501 | +0.027 | +0.504 | -0.08 / +0.02 / +0.13 | AMBER |
|  | ADD | L3M | -1351 / -2364 | +4160 | +1962 / +3433 | +4820 | c=1.00: -1351 / +4160 / +1962 | 69 | +0.306 | +1.622 | +0.19 / +0.23 / +0.27 | ok |
|  | ADD | L6M | -796 / -1393 | +4160 | +1023 / +1790 | +4820 | c=1.00: -796 / +4160 / +1023 | 174 | +0.153 | +0.986 | +0.13 / +0.15 / +0.26 | ok |
|  | ADD | L3M | -573 / -1003 | -1431 | +2829 / +4952 | +3696 | c=1.00: -573 / -1431 / +2829 | 90 | +0.263 | +1.819 | +0.23 / +0.27 / +0.19 | ok |
|  | ADD | L6M | -382 / -668 | -1431 | +2047 / +3582 | +3696 | c=1.00: -382 / -1431 / +2047 | 220 | +0.189 | +1.542 | +0.05 / +0.17 / +0.15 | ok |
|  | ADD | L3M | -293 / -513 | -2719 | +680 / +1190 | +2567 | c=1.00: -293 / -2719 / +680 | 68 | +0.004 | +0.022 | +0.07 / -0.04 / +0.03 | ok |
|  | ADD | L6M | -188 / -330 | -2719 | +1200 / +2100 | +2567 | c=1.00: -188 / -2719 / +1200 | 162 | +0.115 | +0.691 | +0.04 / +0.03 / +0.10 | ok |
|  | ADD | Y2023 | +1984 / +3472 | -5098 | +85 / +148 | -9938 | c=1.00: +1984 / -5098 / +85 | 262 | +0.004 | +0.029 | +0.07 / -0.05 / +0.02 | AMBER |
|  | ADD | Y2024 | -5156 / -9022 | +1595 | +1315 / +2301 | +2571 | c=1.00: -5156 / +1595 / +1315 | 323 | +0.181 | +1.102 | +0.07 / +0.01 / +0.14 | ok |
|  | ADD | Y2025 | -3849 / -6735 | +1750 | +405 / +710 | -468 | c=1.00: -3849 / +1750 / +405 | 305 | +0.065 | +0.375 | +0.04 / +0.01 / +0.05 | ok |
|  | ADD | L3M | -910 / -1593 | +5096 | -195 / -341 | +3581 | c=1.00: -910 / +5096 / -195 | 131 | -0.017 | -0.176 | +0.44 / +0.20 / +0.39 | ok |
|  | ADD | L6M | -587 / -1028 | +3829 | +235 / +412 | +3581 | c=1.00: -587 / +3829 / +235 | 253 | +0.012 | +0.115 | +0.31 / +0.10 / +0.26 | ok |
|  | ADD | L3M | -462 / -808 | -2791 | +2434 / +4259 | +527 | c=1.00: -462 / -2791 / +2434 | 124 | +0.155 | +1.479 | +0.38 / +0.15 / +0.31 | ok |
|  | ADD | L6M | -250 / -437 | -2791 | +1385 / +2423 | +527 | c=1.00: -250 / -2791 / +1385 | 280 | +0.085 | +0.880 | +0.18 / +0.12 / +0.09 | ok |
|  | ADD | Y2023 | +4227 / +7397 | -3513 | +489 / +857 | -11582 | c=1.00: +4227 / -3513 / +489 | 305 | +0.056 | +0.440 | +0.02 / +0.08 / +0.03 | AMBER |
|  | ADD | Y2024 | -2860 / -5005 | +2285 | +147 / +257 | +343 | c=1.00: -2860 / +2285 / +147 | 441 | +0.026 | +0.216 | +0.10 / +0.17 / +0.04 | ok |
|  | ADD | Y2025 | -888 / -1554 | -1725 | +1115 / +1952 | -4348 | c=1.00: -888 / -1725 / +1115 | 482 | +0.113 | +1.028 | +0.14 / +0.04 / +0.16 | ok |
|  | ADD | L3M | -1170 / -2047 | +3034 | +3747 / +6557 | +4739 | c=1.00: -1170 / +3034 / +3747 | 115 | +0.348 | +3.076 | +0.22 / +0.11 / +0.18 | ok |
|  | ADD | L6M | -51 / -89 | +3034 | +1132 / +1981 | -5362 | c=1.00: -51 / +3034 / +1132 | 256 | +0.122 | +1.156 | +0.11 / +0.07 / +0.09 | AMBER |
|  | ADD | Y2023 | -1812 / -3171 | -1916 | +720 / +1261 | -3146 | c=1.00: -1812 / -1916 / +720 | 348 | +0.074 | +0.656 | +0.13 / +0.09 / +0.08 | ok |
|  | ADD | Y2024 | -1940 / -3394 | -228 | +600 / +1049 | -3154 | c=1.00: -1940 / -228 / +600 | 490 | +0.060 | +0.554 | +0.02 / +0.03 / -0.01 | ok |
|  | ADD | Y2025 | -5668 / -9919 | +790 | +1445 / +2529 | +10314 | c=1.00: -5668 / +790 / +1445 | 495 | +0.142 | +1.326 | +0.07 / -0.04 / +0.00 | ok |
|  | ADD | L3M | +970 / +1698 | -3845 | +31 / +54 | -2760 | c=1.00: +970 / -3845 / +31 | 88 | +0.032 | +0.217 | +0.15 / -0.05 / +0.15 | ok |
|  | ADD | L6M | +717 / +1255 | -3845 | +198 / +346 | -2760 | c=1.00: +717 / -3845 / +198 | 188 | +0.062 | +0.429 | +0.11 / +0.04 / +0.12 | ok |
|  | ADD | L3M | +3534 / +6184 | -1571 | -20 / -34 | -12849 | c=1.00: +3534 / -1571 / -20 | 101 | -0.042 | -0.328 | +0.09 / +0.37 / +0.34 | RED |
|  | ADD | L6M | +2199 / +3848 | -3261 | +771 / +1350 | -12849 | c=1.00: +2199 / -3261 / +771 | 222 | +0.067 | +0.549 | +0.02 / +0.25 / +0.25 | RED |
|  | ADD | L3M | -157 / -274 | +3661 | +2274 / +3979 | +515 | c=1.00: -157 / +3661 / +2274 | 197 | +0.082 | +1.240 | +0.13 / +0.13 / +0.29 | ok |
|  | ADD | L6M | -54 / -94 | +1596 | +2298 / +4021 | +515 | c=1.00: -54 / +1596 / +2298 | 432 | +0.106 | +1.692 | +0.16 / +0.05 / +0.12 | ok |
|  | ADD | Y2023 | -952 / -1666 | -3423 | +583 / +1020 | -547 | c=1.00: -952 / -3423 / +583 | 405 | +0.046 | +0.476 | +0.07 / +0.10 / +0.11 | ok |
|  | ADD | Y2024 | -594 / -1039 | -2230 | +520 / +911 | +3380 | c=1.00: -594 / -2230 / +520 | 636 | +0.045 | +0.536 | +0.13 / +0.10 / +0.16 | ok |
|  | ADD | Y2025 | +1529 / +2676 | +1316 | +662 / +1159 | -12139 | c=1.00: +1529 / +1316 / +662 | 751 | +0.047 | +0.659 | +0.21 / +0.05 / +0.20 | ok |
|  | ADD | L3M | +1898 / +3321 | -3530 | +379 / +663 | -6853 | c=1.00: +1898 / -3530 / +379 | 77 | +0.060 | +0.354 | -0.04 / +0.10 / +0.15 | AMBER |
|  | ADD | L6M | +1035 / +1810 | -3530 | +786 / +1376 | -6853 | c=1.00: +1035 / -3530 / +786 | 195 | +0.093 | +0.674 | -0.07 / +0.12 / +0.08 | AMBER |
|  | ADD | L3M | -849 / -1486 | +1136 | +3640 / +6369 | +2215 | c=1.00: -849 / +1136 / +3640 | 207 | +0.163 | +2.589 | +0.20 / -0.05 / +0.15 | ok |
|  | ADD | L6M | -228 / -400 | -903 | +1639 / +2868 | +2215 | c=1.00: -228 / -903 / +1639 | 481 | +0.073 | +1.304 | +0.10 / -0.02 / +0.16 | ok |
|  | ADD | L3M | -344 / -601 | -2620 | +1128 / +1974 | +2386 | c=1.00: -344 / -2620 / +1128 | 61 | +0.215 | +1.009 | +0.11 / -0.20 / +0.10 | ok |
|  | ADD | L6M | +120 / +210 | -5721 | +1318 / +2307 | +2386 | c=1.00: +120 / -5721 / +1318 | 134 | +0.276 | +1.368 | -0.02 / -0.11 / +0.09 | ok |
|  | ADD | L3M | +1347 / +2358 | -4546 | -627 / -1097 | -3384 | c=1.00: +1347 / -4546 / -627 | 72 | -0.097 | -0.535 | +0.12 / +0.12 / +0.23 | ok |
|  | ADD | L6M | +695 / +1217 | -4546 | -22 / -38 | -3384 | c=1.00: +695 / -4546 / -22 | 154 | +0.026 | +0.151 | +0.08 / +0.02 / +0.18 | ok |
|  | ADD | L3M | -495 / -866 | +295 | +1740 / +3044 | -436 | c=1.00: -495 / +295 / +1740 | 238 | +0.059 | +1.089 | +0.38 / +0.34 / +0.25 | ok |
|  | ADD | L6M | -360 / -629 | +295 | +2030 / +3553 | -436 | c=1.00: -360 / +295 / +2030 | 596 | +0.066 | +1.456 | +0.30 / +0.24 / +0.12 | ok |
|  | ADD | L3M | -1109 / -1941 | +3906 | +1945 / +3404 | +5826 | c=1.00: -1109 / +3906 / +1945 | 133 | +0.152 | +1.554 | +0.26 / +0.08 / +0.20 | ok |
|  | ADD | L6M | -448 / -785 | -2420 | +1312 / +2295 | +5375 | c=1.00: -448 / -2420 / +1312 | 248 | +0.121 | +1.115 | +0.11 / +0.07 / +0.07 | ok |
|  | ADD | Y2023 | +1675 / +2931 | -1708 | +111 / +195 | -8263 | c=1.00: +1675 / -1708 / +111 | 294 | +0.006 | +0.047 | +0.18 / +0.11 / +0.25 | AMBER |
|  | ADD | Y2024 | -724 / -1267 | -1090 | -202 / -354 | +1329 | c=1.00: -724 / -1090 / -202 | 415 | -0.006 | -0.043 | +0.13 / -0.04 / +0.16 | ok |
|  | ADD | Y2025 | +834 / +1459 | -4033 | -235 / -412 | -8032 | c=1.00: +834 / -4033 / -235 | 495 | +0.023 | +0.215 | +0.08 / +0.10 / +0.12 | ok |
|  | ADD | L3M | -1067 / -1868 | +195 | +621 / +1087 | +6421 | c=1.00: -1067 / +195 / +621 | 65 | +0.133 | +0.666 | +0.14 / -0.16 / +0.02 | ok |
|  | ADD | L6M | -353 / -618 | -3261 | +882 / +1543 | +5375 | c=1.00: -353 / -3261 / +882 | 141 | +0.197 | +1.031 | +0.07 / -0.06 / +0.07 | ok |
|  | ADD | Y2024 | -669 / -1171 | -2390 | +782 / +1368 | +8144 | c=1.00: -669 / -2390 / +782 | 252 | +0.140 | +0.666 | -0.01 / -0.02 / +0.15 | ok |
|  | ADD | Y2025 | -5025 / -8793 | -1695 | +1031 / +1804 | +4288 | c=1.00: -5025 / -1695 / +1031 | 268 | +0.160 | +0.810 | +0.04 / +0.00 / +0.11 | ok |
|  | ADD | L3M | +833 / +1458 | -4696 | -1022 / -1789 | -2260 | c=1.00: +833 / -4696 / -1022 | 61 | -0.170 | -0.798 | +0.16 / -0.02 / +0.20 | ok |
|  | ADD | L6M | +496 / +868 | -4696 | +866 / +1516 | -2260 | c=1.00: +496 / -4696 / +866 | 137 | +0.166 | +0.843 | +0.15 / +0.03 / +0.19 | ok |
|  | ADD | L3M | +484 / +847 | -2904 | +754 / +1319 | +1428 | c=1.00: +484 / -2904 / +754 | 60 | +0.168 | +0.778 | -0.05 / +0.20 / +0.01 | ok |
|  | ADD | L6M | +225 / +394 | -2904 | +222 / +388 | +1428 | c=1.00: +225 / -2904 / +222 | 147 | +0.056 | +0.306 | -0.07 / +0.18 / -0.02 | ok |
|  | ADD | L3M | +2170 / +3798 | -3621 | -251 / -440 | -7464 | c=1.00: +2170 / -3621 / -251 | 78 | -0.026 | -0.155 | +0.29 / +0.29 / +0.44 | AMBER |
|  | ADD | L6M | +1359 / +2379 | -3621 | +284 / +498 | -7464 | c=1.00: +1359 / -3621 / +284 | 151 | +0.037 | +0.207 | +0.25 / +0.16 / +0.38 | AMBER |
|  | ADD | L3M | +6011 / +10519 | -8135 | +168 / +294 | -20481 | c=1.00: +6011 / -8135 / +168 | 117 | +0.031 | +0.280 | +0.05 / +0.26 / +0.31 | RED |
|  | ADD | L6M | +3942 / +6898 | -8135 | +1059 / +1853 | -20481 | c=1.00: +3942 / -8135 / +1059 | 292 | +0.104 | +1.127 | +0.00 / +0.16 / +0.15 | RED |
|  | ADD | L3M | -1351 / -2364 | +80 | -199 / -348 | +6516 | c=1.00: -1351 / +80 / -199 | 62 | +0.176 | +0.840 | +0.08 / -0.18 / -0.12 | ok |
|  | ADD | L6M | -697 / -1219 | +80 | +320 / +560 | +5375 | c=1.00: -697 / +80 / +320 | 132 | +0.189 | +0.923 | +0.04 / -0.09 / -0.04 | ok |
|  | ADD | L3M | -1497 / -2620 | +90 | +1844 / +3227 | +6596 | c=1.00: -1497 / +90 / +1844 | 64 | +0.274 | +1.347 | +0.21 / -0.12 / +0.05 | ok |
|  | ADD | L6M | -593 / -1037 | -3236 | +1339 / +2343 | +5375 | c=1.00: -593 / -3236 / +1339 | 135 | +0.239 | +1.196 | +0.12 / -0.04 / +0.05 | ok |
|  | ADD | L3M | +1220 / +2135 | +2706 | -840 / -1470 | -5191 | c=1.00: +1220 / +2706 / -840 | 89 | -0.189 | -1.297 | +0.02 / -0.05 / +0.02 | AMBER |
|  | ADD | L6M | +806 / +1411 | +2706 | +1137 / +1989 | -5191 | c=1.00: +806 / +2706 / +1137 | 206 | +0.090 | +0.689 | -0.06 / -0.03 / -0.12 | AMBER |
|  | ADD | L3M | +640 / +1120 | -511 | +763 / +1334 | -3055 | c=1.00: +640 / -511 / +763 | 73 | -0.019 | -0.107 | +0.14 / +0.03 / +0.23 | ok |
|  | ADD | L6M | +283 / +495 | -511 | +1026 / +1795 | -3055 | c=1.00: +283 / -511 / +1026 | 184 | +0.064 | +0.437 | +0.19 / +0.04 / +0.12 | ok |
|  | ADD | L3M | +434 / +759 | +1556 | -391 / -684 | -1049 | c=1.00: +434 / +1556 / -391 | 112 | +0.012 | +0.104 | +0.28 / +0.19 / +0.56 | ok |
|  | ADD | L6M | +428 / +749 | +1556 | -289 / -507 | -1049 | c=1.00: +428 / +1556 / -289 | 241 | +0.006 | +0.054 | +0.29 / +0.16 / +0.48 | ok |
|  | ADD | L3M | +103 / +180 | +2791 | +296 / +518 | -1494 | c=1.00: +103 / +2791 / +296 | 158 | +0.015 | +0.183 | +0.26 / -0.09 / -0.04 | ok |
|  | ADD | L6M | +70 / +122 | +2791 | +734 / +1284 | -1494 | c=1.00: +70 / +2791 / +734 | 333 | +0.032 | +0.398 | +0.29 / -0.05 / +0.00 | ok |
|  | ADD | L3M | +272 / +476 | -1681 | +1032 / +1806 | +1383 | c=1.00: +272 / -1681 / +1032 | 83 | +0.157 | +1.002 | -0.01 / +0.25 / +0.15 | ok |
|  | ADD | L6M | +50 / +87 | -1681 | +899 / +1573 | +1383 | c=1.00: +50 / -1681 / +899 | 193 | +0.115 | +0.819 | +0.07 / +0.15 / +0.20 | ok |
|  | ADD | L3M | +1168 / +2044 | +1606 | +1259 / +2203 | -6114 | c=1.00: +1168 / +1606 / +1259 | 97 | +0.177 | +1.323 | +0.30 / +0.10 / +0.14 | AMBER |
|  | ADD | L6M | +593 / +1037 | +1606 | +483 / +845 | -6114 | c=1.00: +593 / +1606 / +483 | 217 | +0.074 | +0.595 | +0.26 / +0.02 / -0.00 | AMBER |
|  | ADD | L3M | +1599 / +2799 | -1669 | +1780 / +3115 | -3835 | c=1.00: +1599 / -1669 / +1780 | 71 | +0.103 | +0.562 | +0.04 / +0.26 / +0.31 | ok |
|  | ADD | L6M | +965 / +1689 | -1669 | +407 / +713 | -3835 | c=1.00: +965 / -1669 / +407 | 168 | -0.015 | -0.095 | +0.15 / +0.21 / +0.26 | ok |
|  | ADD | L3M | +946 / +1656 | -869 | +302 / +528 | -3069 | c=1.00: +946 / -869 / +302 | 105 | -0.020 | -0.160 | +0.09 / +0.30 / +0.21 | ok |
|  | ADD | L6M | +518 / +907 | -869 | +918 / +1606 | -3069 | c=1.00: +518 / -869 / +918 | 262 | +0.063 | +0.608 | +0.02 / +0.13 / +0.18 | ok |
|  | ADD | L3M | -273 / -478 | -314 | +1876 / +3283 | +511 | c=1.00: -273 / -314 / +1876 | 56 | +0.417 | +1.795 | +0.05 / +0.11 / +0.26 | ok |
|  | ADD | L6M | +195 / +342 | -4316 | +1020 / +1784 | +511 | c=1.00: +195 / -4316 / +1020 | 132 | +0.227 | +1.108 | +0.09 / +0.13 / +0.27 | ok |
|  | ADD | L3M | +56 / +97 | -1109 | +1200 / +2099 | +2350 | c=1.00: +56 / -1109 / +1200 | 85 | +0.086 | +0.563 | +0.25 / +0.03 / +0.24 | ok |
|  | ADD | L6M | +114 / +200 | -1206 | +981 / +1716 | +2350 | c=1.00: +114 / -1206 / +981 | 178 | +0.092 | +0.607 | +0.10 / +0.05 / +0.18 | ok |
|  | ADD | L3M | -65 / -114 | -3256 | +642 / +1123 | +186 | c=1.00: -65 / -3256 / +642 | 90 | +0.070 | +0.487 | +0.09 / +0.01 / +0.09 | ok |
|  | ADD | L6M | +313 / +547 | -6665 | -137 / -240 | +186 | c=1.00: +313 / -6665 / -137 | 195 | +0.000 | +0.000 | +0.03 / +0.04 / +0.05 | ok |
|  | ADD | L3M | +6011 / +10519 | -8135 | +168 / +294 | -20481 | c=1.00: +6011 / -8135 / +168 | 117 | +0.031 | +0.280 | +0.05 / +0.26 / +0.31 | RED |
|  | ADD | L6M | +3942 / +6898 | -8135 | +1059 / +1853 | -20481 | c=1.00: +3942 / -8135 / +1059 | 292 | +0.104 | +1.127 | +0.00 / +0.16 / +0.15 | RED |
|  | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=1.00: -1573 / +95 / +2075 | 62 | +0.326 | +1.553 | +0.23 / -0.07 / +0.10 | ok |
|  | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=1.00: -795 / -796 / +1691 | 135 | +0.312 | +1.560 | +0.05 / -0.03 / +0.01 | ok |
|  | ADDLO | L3M | +607 / +1063 | -2710 | -100 / -175 | -5829 | c=1.00: +607 / -2710 / -100 | 55 | +0.162 | +0.687 | +0.07 / +0.00 / -0.14 | AMBER |
|  | ADDLO | L6M | +615 / +1077 | -2710 | -714 / -1250 | -5829 | c=1.00: +615 / -2710 / -714 | 123 | -0.061 | -0.278 | +0.07 / +0.01 / +0.05 | AMBER |
|  | ADDLO | Y2023 | -3611 / -6319 | -798 | +633 / +1107 | +5713 | c=1.00: -3611 / -798 / +633 | 182 | +0.113 | +0.527 | +0.05 / +0.13 / +0.07 | ok |
|  | ADDLO | Y2024 | -1802 / -3153 | +2395 | +774 / +1354 | -2441 | c=1.00: -1802 / +2395 / +774 | 235 | +0.163 | +0.722 | -0.06 / -0.03 / -0.14 | ok |
|  | ADDLO | Y2025 | +1692 / +2961 | -9745 | +86 / +150 | -11229 | c=1.00: +1692 / -9745 / +86 | 261 | +0.013 | +0.065 | -0.01 / +0.04 / -0.07 | ok |
|  | ADDSO | L3M | +470 / +823 | -1616 | -471 / -824 | +1181 | c=1.00: +470 / -1616 / -471 | 56 | -0.087 | -0.376 | +0.05 / -0.01 / +0.29 | ok |
|  | ADDSO | L6M | +277 / +485 | -1616 | +776 / +1358 | +1181 | c=1.00: +277 / -1616 / +776 | 126 | +0.160 | +0.748 | -0.01 / -0.00 / +0.06 | ok |
|  | ADD | L3M | +311 / +545 | -1686 | -290 / -508 | -1736 | c=1.00: +311 / -1686 / -290 | 141 | -0.032 | -0.349 | +0.04 / +0.11 / +0.18 | ok |
|  | ADD | L6M | +215 / +377 | -1686 | +227 / +397 | -1736 | c=1.00: +215 / -1686 / +227 | 288 | +0.019 | +0.204 | -0.04 / +0.02 / +0.06 | ok |
|  | ADD | L3M | -8 / -15 | -5150 | +1214 / +2124 | -3058 | c=1.00: -8 / -5150 / +1214 | 127 | +0.119 | +1.163 | +0.15 / -0.01 / +0.20 | ok |
|  | ADD | L6M | +129 / +225 | -5150 | +1452 / +2540 | -3058 | c=1.00: +129 / -5150 / +1452 | 264 | +0.137 | +1.337 | +0.02 / +0.03 / +0.01 | ok |
|  | ADD | L3M | +245 / +429 | +784 | -390 / -682 | +1136 | c=1.00: +245 / +784 / -390 | 71 | -0.046 | -0.252 | -0.09 / +0.07 / +0.07 | ok |
|  | ADD | L6M | +235 / +410 | +784 | +723 / +1265 | +1136 | c=1.00: +235 / +784 / +723 | 174 | +0.113 | +0.728 | -0.00 / +0.04 / -0.01 | ok |
|  | ADD | L3M | +403 / +706 | +1249 | +514 / +900 | +1921 | c=1.00: +403 / +1249 / +514 | 201 | +0.015 | +0.236 | +0.02 / +0.02 / -0.05 | ok |
|  | ADD | L6M | +421 / +736 | +1249 | -651 / -1140 | +1921 | c=1.00: +421 / +1249 / -651 | 451 | -0.030 | -0.496 | +0.00 / +0.09 / +0.11 | ok |
|  | ADD | L3M | -810 / -1417 | +481 | +1100 / +1925 | +1305 | c=1.00: -810 / +481 / +1100 | 77 | +0.154 | +0.913 | -0.00 / +0.04 / -0.18 | ok |
|  | ADD | L6M | -565 / -989 | +481 | +1119 / +1959 | +1305 | c=1.00: -565 / +481 / +1119 | 172 | +0.143 | +0.912 | +0.14 / +0.06 / -0.10 | ok |
|  | ADD | Y2023 | +1115 / +1951 | -342 | +756 / +1322 | -4069 | c=1.00: +1115 / -342 / +756 | 305 | +0.078 | +0.608 | +0.38 / +0.05 / +0.36 | ok |
|  | ADD | Y2024 | -1991 / -3484 | +0 | +857 / +1499 | +2452 | c=1.00: -1991 / +0 / +857 | 450 | +0.108 | +0.919 | +0.30 / +0.01 / +0.24 | ok |
|  | ADD | Y2025 | -2084 / -3647 | +1554 | +998 / +1747 | +705 | c=1.00: -2084 / +1554 / +998 | 441 | +0.102 | +0.846 | +0.13 / +0.08 / +0.11 | ok |
|  | ADD | L3M | +471 / +825 | +1929 | -289 / -506 | +1386 | c=1.00: +471 / +1929 / -289 | 113 | -0.006 | -0.051 | -0.07 / +0.31 / +0.36 | ok |
|  | ADD | L6M | +200 / +351 | +1929 | +438 / +766 | +1386 | c=1.00: +200 / +1929 / +438 | 241 | +0.039 | +0.352 | +0.08 / +0.19 / +0.26 | ok |
|  | ADD | L3M | +7275 / +12730 | -10060 | -1145 / -2004 | -24131 | c=1.00: +7275 / -10060 / -1145 | 111 | -0.106 | -0.907 | -0.03 / +0.27 / +0.41 | RED |
|  | ADD | L6M | +4534 / +7934 | -10060 | +350 / +612 | -24131 | c=1.00: +4534 / -10060 / +350 | 281 | +0.052 | +0.545 | -0.00 / +0.19 / +0.14 | RED |
|  | ADD | L3M | -912 / -1596 | -194 | +1551 / +2715 | +3421 | c=1.00: -912 / -194 / +1551 | 123 | +0.118 | +1.121 | +0.34 / +0.02 / +0.42 | ok |
|  | ADD | L6M | -561 / -982 | -194 | +1112 / +1946 | +3421 | c=1.00: -561 / -194 / +1112 | 276 | +0.079 | +0.808 | +0.31 / +0.04 / +0.30 | ok |
|  | ADD | L3M | +1112 / +1947 | -1804 | +815 / +1426 | -6874 | c=1.00: +1112 / -1804 / +815 | 94 | +0.077 | +0.554 | +0.25 / +0.09 / +0.11 | AMBER |
|  | ADD | L6M | +508 / +890 | -1804 | +919 / +1608 | -6874 | c=1.00: +508 / -1804 / +919 | 201 | +0.103 | +0.766 | +0.19 / +0.07 / -0.02 | AMBER |
|  | ADD | L3M | +2110 / +3693 | -2255 | +51 / +89 | -8987 | c=1.00: +2110 / -2255 / +51 | 104 | +0.024 | +0.191 | +0.07 / +0.20 / +0.11 | AMBER |
|  | ADD | L6M | +1655 / +2896 | -2255 | +363 / +634 | -8987 | c=1.00: +1655 / -2255 / +363 | 263 | +0.060 | +0.586 | +0.14 / +0.15 / +0.03 | AMBER |
|  | ADD | L3M | +5425 / +9493 | -10670 | +453 / +793 | -15899 | c=1.00: +5425 / -10670 / +453 | 77 | +0.033 | +0.197 | -0.08 / +0.17 / +0.34 | RED |
|  | ADD | L6M | +3256 / +5697 | -10670 | +609 / +1066 | -15899 | c=1.00: +3256 / -10670 / +609 | 165 | +0.083 | +0.505 | +0.03 / +0.15 / +0.23 | RED |
|  | ADD | L3M | +471 / +825 | +1929 | -289 / -506 | +1386 | c=1.00: +471 / +1929 / -289 | 113 | -0.006 | -0.051 | -0.07 / +0.31 / +0.36 | ok |
|  | ADD | L6M | +200 / +351 | +1929 | +438 / +766 | +1386 | c=1.00: +200 / +1929 / +438 | 241 | +0.039 | +0.352 | +0.08 / +0.19 / +0.26 | ok |
|  | ADD | L3M | +2834 / +4959 | -5585 | +1087 / +1902 | -9744 | c=1.00: +2834 / -5585 / +1087 | 88 | +0.084 | +0.570 | -0.08 / +0.41 / +0.15 | RED |
|  | ADD | L6M | +1836 / +3213 | -5585 | +1370 / +2397 | -9744 | c=1.00: +1836 / -5585 / +1370 | 207 | +0.136 | +1.043 | -0.05 / +0.21 / +0.04 | RED |
|  | ADD | L3M | +1858 / +3252 | -4908 | +86 / +151 | -7367 | c=1.00: +1858 / -4908 / +86 | 76 | +0.057 | +0.333 | +0.19 / +0.03 / +0.20 | AMBER |
|  | ADD | L6M | +1154 / +2020 | -4908 | -43 / -75 | -7367 | c=1.00: +1154 / -4908 / -43 | 176 | +0.001 | +0.007 | +0.07 / +0.04 / +0.12 | AMBER |
|  | ADD | L3M | +913 / +1599 | -71 | -211 / -369 | -3719 | c=1.00: +913 / -71 / -211 | 71 | -0.025 | -0.135 | +0.12 / +0.12 / -0.11 | ok |
|  | ADD | L6M | +561 / +981 | -71 | +1110 / +1943 | -3719 | c=1.00: +561 / -71 / +1110 | 153 | +0.182 | +1.034 | +0.04 / +0.09 / +0.02 | ok |
|  | ADD | L3M | +1436 / +2513 | -6366 | +80 / +140 | -3700 | c=1.00: +1436 / -6366 / +80 | 74 | +0.014 | +0.079 | -0.02 / +0.04 / +0.33 | ok |
|  | ADD | L6M | +830 / +1452 | -6366 | +984 / +1722 | -3700 | c=1.00: +830 / -6366 / +984 | 156 | +0.153 | +0.885 | -0.06 / +0.01 / +0.13 | ok |
|  | ADD | L3M | -1526 / -2671 | +145 | +1113 / +1948 | +6581 | c=1.00: -1526 / +145 / +1113 | 61 | +0.174 | +0.815 | +0.25 / -0.18 / +0.09 | ok |
|  | ADD | L6M | -654 / -1144 | -2981 | +1483 / +2596 | +5375 | c=1.00: -654 / -2981 / +1483 | 134 | +0.286 | +1.418 | +0.10 / -0.08 / +0.09 | ok |
|  | ADD | L3M | +527 / +923 | +3090 | +763 / +1334 | +508 | c=1.00: +527 / +3090 / +763 | 73 | +0.095 | +0.534 | +0.11 / +0.31 / +0.28 | ok |
|  | ADD | L6M | +375 / +656 | -501 | +1325 / +2319 | +508 | c=1.00: +375 / -501 / +1325 | 178 | +0.177 | +1.166 | +0.12 / +0.20 / +0.29 | ok |
|  | ADD | L3M | -314 / -550 | +966 | +452 / +791 | +3585 | c=1.00: -314 / +966 / +452 | 100 | +0.004 | +0.029 | +0.31 / +0.36 / +0.39 | ok |
|  | ADD | L6M | -257 / -450 | +966 | +872 / +1527 | +3585 | c=1.00: -257 / +966 / +872 | 203 | +0.071 | +0.532 | +0.18 / +0.20 / +0.07 | ok |
|  | ADD | Y2023 | +4095 / +7166 | -857 | +310 / +542 | -11376 | c=1.00: +4095 / -857 / +310 | 300 | +0.029 | +0.220 | +0.26 / +0.13 / +0.29 | AMBER |
|  | ADD | Y2024 | -1069 / -1870 | -1140 | +176 / +308 | -3212 | c=1.00: -1069 / -1140 / +176 | 435 | +0.025 | +0.203 | +0.22 / +0.11 / +0.14 | ok |
|  | ADD | Y2025 | -1711 / -2993 | -1750 | +546 / +956 | +3003 | c=1.00: -1711 / -1750 / +546 | 432 | +0.074 | +0.603 | +0.12 / +0.11 / +0.08 | ok |
|  | ADD | L3M | +154 / +269 | -2674 | -173 / -303 | -939 | c=1.00: +154 / -2674 / -173 | 69 | +0.001 | +0.005 | -0.02 / -0.03 / -0.12 | ok |
|  | ADD | L6M | +116 / +203 | -2674 | -255 / -447 | -939 | c=1.00: +116 / -2674 / -255 | 150 | +0.011 | +0.060 | -0.01 / +0.04 / +0.13 | ok |
|  | ADD | L3M | -1172 / -2051 | +3906 | +2247 / +3933 | +5826 | c=1.00: -1172 / +3906 / +2247 | 129 | +0.181 | +1.793 | +0.27 / +0.08 / +0.16 | ok |
|  | ADD | L6M | -483 / -845 | -2420 | +1457 / +2550 | +5375 | c=1.00: -483 / -2420 / +1457 | 244 | +0.136 | +1.230 | +0.11 / +0.07 / +0.04 | ok |
|  | ADD | Y2023 | +1631 / +2854 | -1708 | +173 / +302 | -8263 | c=1.00: +1631 / -1708 / +173 | 294 | +0.013 | +0.098 | +0.17 / +0.10 / +0.25 | AMBER |
|  | ADD | Y2024 | -804 / -1407 | -1090 | -183 / -321 | +1329 | c=1.00: -804 / -1090 / -183 | 414 | -0.003 | -0.027 | +0.13 / -0.04 / +0.15 | ok |
|  | ADD | Y2025 | +766 / +1340 | -4033 | -163 / -285 | -8032 | c=1.00: +766 / -4033 / -163 | 494 | +0.026 | +0.243 | +0.08 / +0.08 / +0.11 | ok |
|  | ADD | L3M | +4408 / +7714 | -545 | -1911 / -3345 | -14967 | c=1.00: +4408 / -545 / -1911 | 55 | -0.214 | -0.906 | -0.06 / +0.05 / +0.04 | RED |
|  | ADD | L6M | +2721 / +4762 | -545 | -747 / -1307 | -14967 | c=1.00: +2721 / -545 / -747 | 132 | -0.045 | -0.222 | +0.03 / -0.03 / +0.02 | RED |
|  | ADD | L3M | -353 / -617 | -2705 | +1632 / +2856 | +2446 | c=1.00: -353 / -2705 / +1632 | 61 | +0.305 | +1.429 | +0.20 / -0.02 / +0.06 | ok |
|  | ADD | L6M | -13 / -24 | -3226 | +1775 / +3107 | +2446 | c=1.00: -13 / -3226 / +1775 | 135 | +0.350 | +1.749 | +0.05 / +0.02 / +0.04 | ok |
|  | ADD | Y2023 | -205 / -358 | -2364 | +474 / +830 | -7105 | c=1.00: -205 / -2364 / +474 | 179 | +0.086 | +0.395 | +0.06 / +0.07 / +0.21 | AMBER |
|  | ADD | Y2024 | -517 / -905 | -2395 | +676 / +1184 | +6894 | c=1.00: -517 / -2395 / +676 | 253 | +0.124 | +0.594 | -0.02 / +0.01 / +0.17 | ok |
|  | ADD | Y2025 | -7861 / -13757 | +3155 | +1040 / +1820 | +15161 | c=1.00: -7861 / +3155 / +1040 | 267 | +0.161 | +0.810 | +0.06 / -0.05 / +0.11 | ok |
|  | ADD | L3M | -741 / -1297 | -1319 | +2558 / +4477 | +2141 | c=1.00: -741 / -1319 / +2558 | 98 | +0.190 | +1.433 | +0.30 / -0.08 / +0.12 | ok |
|  | ADD | L6M | -483 / -845 | -1319 | +1146 / +2006 | +2141 | c=1.00: -483 / -1319 / +1146 | 215 | +0.086 | +0.684 | +0.22 / -0.12 / -0.04 | ok |
|  | ADD | Y2023 | +226 / +395 | -3842 | +1178 / +2061 | -11298 | c=1.00: +226 / -3842 / +1178 | 272 | +0.141 | +0.986 | +0.20 / -0.04 / +0.34 | AMBER |
|  | ADD | Y2024 | -1862 / -3259 | -900 | +1141 / +1996 | +477 | c=1.00: -1862 / -900 / +1141 | 431 | +0.112 | +0.912 | +0.20 / -0.02 / +0.27 | ok |
|  | ADD | Y2025 | -5209 / -9115 | +1157 | +1728 / +3025 | +6396 | c=1.00: -5209 / +1157 / +1728 | 458 | +0.163 | +1.412 | +0.05 / +0.09 / +0.06 | ok |
|  | ADD | L3M | +764 / +1337 | +773 | +1757 / +3074 | -341 | c=1.00: +764 / +773 / +1757 | 85 | +0.096 | +0.627 | -0.13 / +0.20 / +0.05 | ok |
|  | ADD | L6M | +668 / +1169 | +354 | +1424 / +2492 | -341 | c=1.00: +668 / +354 / +1424 | 205 | +0.112 | +0.847 | -0.05 / +0.04 / +0.07 | ok |
|  | ADD | L3M | -1115 / -1951 | -1341 | +554 / +970 | +5563 | c=1.00: -1115 / -1341 / +554 | 66 | +0.184 | +0.932 | +0.02 / +0.03 / -0.02 | ok |
|  | ADD | L6M | -670 / -1173 | -1341 | +1242 / +2173 | +5375 | c=1.00: -670 / -1341 / +1242 | 137 | +0.250 | +1.269 | +0.02 / -0.00 / +0.14 | ok |
|  | ADD | Y2023 | -112 / -195 | -1453 | +675 / +1181 | -3674 | c=1.00: -112 / -1453 / +675 | 294 | +0.082 | +0.618 | +0.07 / -0.01 / +0.10 | ok |
|  | ADD | Y2024 | +3672 / +6427 | -1355 | -406 / -710 | -307 | c=1.00: +3672 / -1355 / -406 | 383 | -0.037 | -0.268 | -0.08 / +0.03 / +0.02 | ok |
|  | ADD | Y2025 | +1151 / +2013 | +2439 | +691 / +1209 | -5872 | c=1.00: +1151 / +2439 / +691 | 328 | +0.102 | +0.630 | +0.05 / -0.02 / +0.05 | ok |
|  | ADD | L3M | +2588 / +4529 | -4460 | -849 / -1486 | -10451 | c=1.00: +2588 / -4460 / -849 | 80 | -0.022 | -0.134 | +0.01 / +0.19 / +0.17 | RED |
|  | ADD | L6M | +1497 / +2619 | -4460 | +301 / +526 | -10451 | c=1.00: +1497 / -4460 / +301 | 177 | +0.082 | +0.537 | -0.05 / +0.15 / +0.10 | RED |
|  | ADD | L3M | -427 / -747 | +2630 | +1632 / +2856 | +2141 | c=1.00: -427 / +2630 / +1632 | 68 | +0.297 | +1.553 | +0.08 / +0.08 / +0.22 | ok |
|  | ADD | L6M | -90 / -158 | -3015 | +1031 / +1804 | +2141 | c=1.00: -90 / -3015 / +1031 | 171 | +0.168 | +1.063 | +0.09 / +0.06 / +0.30 | ok |
|  | ADD | L3M | +2763 / +4835 | -1586 | -976 / -1708 | -7216 | c=1.00: +2763 / -1586 / -976 | 190 | -0.064 | -0.941 | +0.26 / +0.44 / +0.56 | AMBER |
|  | ADD | L3M | +4543 / +7950 | -7660 | +486 / +851 | -17817 | c=1.00: +4543 / -7660 / +486 | 99 | +0.020 | +0.155 | +0.20 / +0.36 / +0.40 | RED |
|  | ADD | L6M | +2740 / +4796 | -7660 | +2316 / +4053 | -17817 | c=1.00: +2740 / -7660 / +2316 | 235 | +0.231 | +2.009 | +0.13 / +0.26 / +0.09 | RED |
|  | ADD | L3M | -427 / -747 | +2630 | +1632 / +2856 | +2141 | c=1.00: -427 / +2630 / +1632 | 68 | +0.297 | +1.553 | +0.08 / +0.08 / +0.22 | ok |
|  | ADD | L6M | -90 / -158 | -3015 | +1031 / +1804 | +2141 | c=1.00: -90 / -3015 / +1031 | 171 | +0.168 | +1.063 | +0.09 / +0.06 / +0.30 | ok |
|  | ADD | L3M | +965 / +1689 | -2980 | +1298 / +2272 | -3738 | c=1.00: +965 / -2980 / +1298 | 65 | +0.203 | +1.017 | +0.19 / +0.13 / +0.35 | ok |
|  | ADD | L6M | +811 / +1419 | -3111 | +885 / +1548 | -3738 | c=1.00: +811 / -3111 / +885 | 145 | +0.163 | +0.878 | +0.06 / +0.08 / +0.21 | ok |
|  | ADD | L3M | +9012 / +15770 | -8505 | -541 / -947 | -26522 | c=1.00: +9012 / -8505 / -541 | 111 | -0.065 | -0.553 | +0.02 / +0.24 / +0.38 | RED |
|  | ADD | L6M | +5642 / +9874 | -8505 | -204 / -357 | -26522 | c=1.00: +5642 / -8505 / -204 | 279 | -0.023 | -0.242 | +0.03 / +0.14 / +0.08 | RED |
|  | ADD | L3M | +965 / +1689 | -2980 | +1298 / +2272 | -3738 | c=1.00: +965 / -2980 / +1298 | 65 | +0.203 | +1.017 | +0.19 / +0.13 / +0.35 | ok |
|  | ADD | L6M | +811 / +1419 | -3111 | +885 / +1548 | -3738 | c=1.00: +811 / -3111 / +885 | 145 | +0.163 | +0.878 | +0.06 / +0.08 / +0.21 | ok |
|  | ADD | L3M | +616 / +1079 | -4543 | -347 / -607 | -2235 | c=1.00: +616 / -4543 / -347 | 144 | -0.003 | -0.037 | +0.05 / +0.12 / +0.13 | ok |
|  | ADD | L6M | +480 / +839 | -4543 | +122 / +213 | -2235 | c=1.00: +480 / -4543 / +122 | 362 | +0.021 | +0.277 | -0.03 / +0.11 / +0.03 | ok |
|  | ADD | L3M | +214 / +375 | -1244 | +2020 / +3535 | +736 | c=1.00: +214 / -1244 / +2020 | 81 | +0.143 | +0.894 | -0.01 / +0.20 / +0.15 | ok |
|  | ADD | L6M | +32 / +57 | -1244 | +2476 / +4332 | +736 | c=1.00: +32 / -1244 / +2476 | 192 | +0.225 | +1.598 | +0.04 / +0.15 / +0.03 | ok |
|  | ADD | L3M | +950 / +1662 | -7204 | -103 / -180 | -4462 | c=1.00: +950 / -7204 / -103 | 67 | +0.026 | +0.136 | +0.09 / +0.02 / +0.03 | ok |
|  | ADD | L6M | +733 / +1283 | -7204 | +633 / +1108 | -4462 | c=1.00: +733 / -7204 / +633 | 158 | +0.127 | +0.746 | +0.06 / +0.08 / +0.15 | ok |
|  | ADD | L3M | +1426 / +2495 | -5941 | -1152 / -2017 | -3914 | c=1.00: +1426 / -5941 / -1152 | 135 | -0.029 | -0.300 | +0.18 / +0.08 / +0.17 | ok |
|  | ADD | L6M | +859 / +1503 | -5941 | -261 / -457 | -3914 | c=1.00: +859 / -5941 / -261 | 302 | +0.015 | +0.164 | +0.11 / +0.12 / +0.15 | ok |
|  | ADD | L3M | -763 / -1335 | +904 | +1249 / +2187 | +4490 | c=1.00: -763 / +904 / +1249 | 120 | +0.116 | +1.070 | +0.16 / +0.10 / +0.05 | ok |
|  | ADD | L6M | -460 / -804 | +904 | +1253 / +2193 | +4490 | c=1.00: -460 / +904 / +1253 | 249 | +0.121 | +1.113 | +0.08 / +0.09 / -0.02 | ok |
|  | ADD | Y2023 | +3710 / +6493 | -1753 | +141 / +247 | -8094 | c=1.00: +3710 / -1753 / +141 | 300 | +0.010 | +0.076 | +0.14 / +0.02 / +0.15 | AMBER |
|  | ADD | Y2024 | +5886 / +10300 | -1180 | -424 / -742 | -9387 | c=1.00: +5886 / -1180 / -424 | 410 | -0.037 | -0.284 | +0.11 / +0.06 / +0.06 | AMBER |
|  | ADD | Y2025 | -4082 / -7144 | +1222 | +376 / +658 | +1804 | c=1.00: -4082 / +1222 / +376 | 482 | +0.050 | +0.454 | -0.00 / -0.01 / +0.03 | ok |
|  | ADD | L3M | -876 / -1533 | -144 | +936 / +1638 | +2621 | c=1.00: -876 / -144 / +936 | 75 | +0.070 | +0.404 | +0.12 / +0.03 / -0.10 | ok |
|  | ADD | L6M | -436 / -762 | -144 | +460 / +806 | +2621 | c=1.00: -436 / -144 / +460 | 167 | +0.034 | +0.209 | +0.18 / +0.01 / +0.02 | ok |
|  | ADD | Y2023 | -3417 / -5981 | +1323 | +1291 / +2260 | -1084 | c=1.00: -3417 / +1323 / +1291 | 206 | +0.200 | +1.056 | +0.09 / +0.02 / +0.20 | ok |
|  | ADD | Y2024 | +3490 / +6108 | +2395 | +899 / +1573 | +90 | c=1.00: +3490 / +2395 / +899 | 341 | +0.127 | +0.817 | +0.07 / -0.00 / +0.10 | ok |
|  | ADD | Y2025 | -2134 / -3735 | -4710 | +1385 / +2424 | -282 | c=1.00: -2134 / -4710 / +1385 | 364 | +0.164 | +1.130 | +0.01 / +0.08 / +0.06 | ok |
|  | ADDLO | L3M | -343 / -600 | -19 | +15 / +26 | +225 | c=1.00: -343 / -19 / +15 | 60 | -0.028 | -0.128 | +0.17 / -0.12 / -0.12 | ok |
|  | ADDLO | L6M | -192 / -336 | -19 | -685 / -1199 | +225 | c=1.00: -192 / -19 / -685 | 121 | -0.135 | -0.604 | +0.19 / -0.09 / -0.07 | ok |
|  | ADDSO | L3M | -539 / -944 | -125 | +254 / +445 | +2395 | c=1.00: -539 / -125 / +254 | 43 | -0.081 | -0.267 | -0.04 / +0.05 / -0.05 | ok |
|  | ADDSO | L6M | -305 / -535 | -125 | +786 / +1375 | +2395 | c=1.00: -305 / -125 / +786 | 96 | +0.111 | +0.396 | +0.07 / +0.02 / +0.03 | ok |
|  | ADD | L3M | -1010 / -1767 | +135 | +1090 / +1908 | +5286 | c=1.00: -1010 / +135 / +1090 | 62 | +0.205 | +0.977 | +0.16 / -0.15 / +0.04 | ok |
|  | ADD | L6M | -380 / -664 | -3226 | +1856 / +3248 | +5286 | c=1.00: -380 / -3226 / +1856 | 132 | +0.371 | +1.816 | +0.01 / -0.07 / +0.03 | ok |
|  | ADD | Y2023 | -1337 / -2339 | -2223 | +352 / +616 | -5220 | c=1.00: -1337 / -2223 / +352 | 179 | +0.064 | +0.293 | +0.04 / +0.08 / +0.22 | ok |
|  | ADD | Y2024 | -2088 / -3655 | -2395 | +880 / +1540 | +10066 | c=1.00: -2088 / -2395 / +880 | 254 | +0.145 | +0.697 | +0.04 / +0.01 / +0.20 | ok |
|  | ADD | Y2025 | -7435 / -13011 | +1760 | +1117 / +1955 | +15161 | c=1.00: -7435 / +1760 / +1117 | 267 | +0.173 | +0.874 | +0.13 / -0.04 / +0.12 | ok |
|  | ADD | L3M | -1087 / -1902 | +3732 | +130 / +228 | +5291 | c=1.00: -1087 / +3732 / +130 | 237 | +0.004 | +0.072 | +0.25 / +0.07 / +0.11 | ok |
|  | ADD | L6M | -723 / -1266 | +3535 | +862 / +1508 | +5291 | c=1.00: -723 / +3535 / +862 | 555 | +0.034 | +0.700 | +0.20 / +0.06 / +0.05 | ok |
|  | ADD | L3M | -6 / -10 | -2529 | +2277 / +3984 | +183 | c=1.00: -6 / -2529 / +2277 | 69 | +0.277 | +1.472 | -0.10 / +0.14 / +0.12 | ok |
|  | ADD | L6M | +152 / +265 | -3220 | +669 / +1170 | +183 | c=1.00: +152 / -3220 / +669 | 163 | +0.068 | +0.410 | -0.10 / +0.06 / +0.12 | ok |
|  | ADD | L3M | +1321 / +2311 | -2871 | +803 / +1405 | -3667 | c=1.00: +1321 / -2871 / +803 | 178 | +0.053 | +0.719 | +0.04 / +0.13 / +0.26 | ok |
|  | ADD | L6M | +831 / +1454 | -2871 | +1003 / +1756 | -3667 | c=1.00: +831 / -2871 / +1003 | 377 | +0.054 | +0.758 | +0.09 / +0.12 / +0.31 | ok |
|  | ADD | L3M | +4995 / +8742 | -8490 | -1251 / -2189 | -19122 | c=1.00: +4995 / -8490 / -1251 | 105 | -0.108 | -0.872 | +0.09 / +0.19 / +0.31 | RED |
|  | ADD | L6M | +3012 / +5271 | -8490 | +1043 / +1825 | -19122 | c=1.00: +3012 / -8490 / +1043 | 253 | +0.101 | +0.944 | +0.01 / +0.13 / +0.17 | RED |
|  | ADD | L3M | +594 / +1040 | -2919 | +226 / +396 | -2178 | c=1.00: +594 / -2919 / +226 | 73 | +0.041 | +0.228 | -0.01 / +0.07 / -0.03 | ok |
|  | ADD | L6M | +562 / +984 | -3356 | +800 / +1400 | -2178 | c=1.00: +562 / -3356 / +800 | 159 | +0.116 | +0.686 | -0.04 / +0.09 / +0.09 | ok |
|  | ADD | L3M | -99 / -174 | +1195 | -1447 / -2532 | +90 | c=1.00: -99 / +1195 / -1447 | 80 | -0.081 | -0.496 | -0.07 / -0.19 / -0.20 | ok |
|  | ADD | L6M | +6 / +10 | +1195 | -330 / -577 | +90 | c=1.00: +6 / +1195 / -330 | 166 | +0.029 | +0.178 | -0.02 / -0.09 / -0.20 | ok |
|  | ADD | L3M | +3467 / +6068 | -7925 | +376 / +659 | -13157 | c=1.00: +3467 / -7925 / +376 | 128 | +0.048 | +0.473 | +0.00 / +0.37 / +0.33 | RED |
|  | ADD | L6M | +2031 / +3554 | -7925 | +1318 / +2307 | -13157 | c=1.00: +2031 / -7925 / +1318 | 299 | +0.111 | +1.234 | +0.07 / +0.20 / +0.21 | RED |
|  | ADD | L3M | +1681 / +2942 | -5285 | +1772 / +3101 | -5519 | c=1.00: +1681 / -5285 / +1772 | 59 | +0.357 | +1.619 | -0.35 / +0.12 / -0.05 | AMBER |
|  | ADD | L6M | +1219 / +2133 | -5285 | +611 / +1068 | -5519 | c=1.00: +1219 / -5285 / +611 | 149 | +0.135 | +0.747 | -0.20 / +0.12 / -0.11 | AMBER |
|  | ADD | L3M | +833 / +1458 | -4696 | -1022 / -1789 | -2260 | c=1.00: +833 / -4696 / -1022 | 61 | -0.170 | -0.798 | +0.16 / -0.02 / +0.20 | ok |
|  | ADD | L6M | +496 / +868 | -4696 | +866 / +1516 | -2260 | c=1.00: +496 / -4696 / +866 | 137 | +0.166 | +0.843 | +0.15 / +0.03 / +0.19 | ok |
|  | ADD | L3M | -632 / -1106 | -1471 | +546 / +956 | +4027 | c=1.00: -632 / -1471 / +546 | 115 | +0.032 | +0.285 | +0.25 / +0.12 / +0.22 | ok |
|  | ADD | L6M | -283 / -496 | -1471 | +255 / +446 | +4027 | c=1.00: -283 / -1471 / +255 | 249 | +0.020 | +0.185 | +0.14 / +0.14 / +0.15 | ok |
|  | ADD | Y2023 | -157 / -275 | -1568 | +302 / +529 | -1140 | c=1.00: -157 / -1568 / +302 | 295 | +0.027 | +0.206 | +0.11 / +0.13 / +0.18 | ok |
|  | ADD | Y2024 | +42 / +73 | -1055 | +316 / +553 | -4865 | c=1.00: +42 / -1055 / +316 | 417 | +0.039 | +0.309 | +0.10 / -0.01 / +0.10 | ok |
|  | ADD | Y2025 | -2483 / -4345 | +4081 | +362 / +633 | +1530 | c=1.00: -2483 / +4081 / +362 | 478 | +0.070 | +0.634 | +0.09 / +0.06 / +0.15 | ok |
|  | ADD | L3M | +1066 / +1865 | -4319 | -412 / -721 | -3503 | c=1.00: +1066 / -4319 / -412 | 71 | -0.149 | -0.816 | -0.00 / +0.04 / -0.05 | ok |
|  | ADD | L6M | +648 / +1134 | -4319 | +799 / +1397 | -3503 | c=1.00: +648 / -4319 / +799 | 162 | +0.073 | +0.438 | +0.02 / +0.05 / +0.07 | ok |
|  | ADD | L3M | +602 / +1053 | +1681 | +1216 / +2128 | -3018 | c=1.00: +602 / +1681 / +1216 | 84 | +0.085 | +0.547 | +0.18 / +0.19 / +0.27 | ok |
|  | ADD | L6M | +225 / +394 | +1681 | +1129 / +1976 | -3018 | c=1.00: +225 / +1681 / +1129 | 183 | +0.090 | +0.608 | +0.18 / +0.15 / +0.21 | ok |
|  | ADD | L3M | +1678 / +2937 | -4571 | -1067 / -1868 | -7943 | c=1.00: +1678 / -4571 / -1067 | 136 | -0.031 | -0.326 | -0.08 / +0.01 / -0.10 | AMBER |
|  | ADD | L6M | +1082 / +1893 | -4571 | +30 / +52 | -7943 | c=1.00: +1082 / -4571 / +30 | 281 | +0.041 | +0.430 | -0.10 / +0.03 / -0.10 | AMBER |
|  | ADD | L3M | -420 / -735 | +2985 | +1802 / +3154 | +726 | c=1.00: -420 / +2985 / +1802 | 60 | +0.335 | +1.547 | +0.06 / -0.20 / +0.17 | ok |
|  | ADD | L6M | -255 / -447 | +1609 | +2513 / +4397 | +726 | c=1.00: -255 / +1609 / +2513 | 134 | +0.439 | +2.180 | -0.08 / -0.05 / +0.09 | ok |
|  | ADD | Y2023 | +5572 / +9751 | -3523 | -444 / -777 | -12669 | c=1.00: +5572 / -3523 / -444 | 190 | -0.076 | -0.370 | -0.01 / +0.09 / +0.03 | RED |
|  | ADD | Y2024 | +2898 / +5071 | -2350 | -166 / -291 | -4039 | c=1.00: +2898 / -2350 / -166 | 247 | -0.016 | -0.076 | -0.00 / -0.00 / +0.04 | ok |
|  | ADD | Y2025 | -5684 / -9947 | +1990 | +602 / +1053 | +12553 | c=1.00: -5684 / +1990 / +602 | 262 | +0.096 | +0.473 | -0.09 / -0.09 / +0.08 | ok |
|  | ADD | L3M | +2834 / +4959 | -5585 | +1087 / +1902 | -9744 | c=1.00: +2834 / -5585 / +1087 | 88 | +0.084 | +0.570 | -0.08 / +0.41 / +0.15 | RED |
|  | ADD | L6M | +1836 / +3213 | -5585 | +1370 / +2397 | -9744 | c=1.00: +1836 / -5585 / +1370 | 207 | +0.136 | +1.043 | -0.05 / +0.21 / +0.04 | RED |
|  | ADD | L3M | +476 / +832 | +616 | +1242 / +2173 | -843 | c=1.00: +476 / +616 / +1242 | 188 | +0.082 | +1.185 | +0.16 / +0.23 / +0.15 | ok |
|  | ADD | L6M | +381 / +666 | -2530 | +1210 / +2117 | -843 | c=1.00: +381 / -2530 / +1210 | 453 | +0.063 | +1.054 | +0.16 / +0.14 / +0.15 | ok |
|  | ADD | L3M | +594 / +1040 | -2919 | +226 / +396 | -2178 | c=1.00: +594 / -2919 / +226 | 73 | +0.041 | +0.228 | -0.01 / +0.07 / -0.03 | ok |
|  | ADD | L6M | +562 / +984 | -3356 | +800 / +1400 | -2178 | c=1.00: +562 / -3356 / +800 | 159 | +0.116 | +0.686 | -0.04 / +0.09 / +0.09 | ok |
|  | ADD | L3M | +1815 / +3176 | -1051 | -1639 / -2869 | -6824 | c=1.00: +1815 / -1051 / -1639 | 140 | -0.100 | -1.082 | -0.05 / -0.05 / -0.09 | AMBER |
|  | ADD | L6M | +1077 / +1885 | -1051 | -303 / -531 | -6824 | c=1.00: +1077 / -1051 / -303 | 305 | +0.002 | +0.025 | -0.01 / -0.02 / +0.05 | AMBER |
|  | ADD | L3M | -607 / -1062 | -439 | +846 / +1480 | +2186 | c=1.00: -607 / -439 / +846 | 117 | +0.082 | +0.742 | +0.36 / +0.24 / +0.32 | ok |
|  | ADD | L6M | -313 / -547 | -439 | +564 / +988 | +2186 | c=1.00: -313 / -439 / +564 | 283 | +0.047 | +0.488 | +0.19 / +0.16 / +0.14 | ok |
|  | ADD | L3M | +1424 / +2492 | -3732 | +23 / +40 | -5767 | c=1.00: +1424 / -3732 / +23 | 40 | +0.095 | +0.293 | +0.02 / +0.03 / +0.22 | AMBER |
|  | ADD | L6M | +840 / +1470 | -3732 | +465 / +813 | -5767 | c=1.00: +840 / -3732 / +465 | 80 | +0.187 | +0.554 | +0.08 / -0.04 / +0.08 | AMBER |
|  | ADD | L3M | +49 / +85 | +529 | -79 / -138 | +2244 | c=1.00: +49 / +529 / -79 | 113 | -0.026 | -0.224 | -0.09 / +0.08 / +0.02 | ok |
|  | ADD | L6M | +139 / +243 | +279 | +2113 / +3697 | +2244 | c=1.00: +139 / +279 / +2113 | 241 | +0.180 | +1.603 | -0.03 / +0.01 / +0.05 | ok |
|  | ADD | L3M | -512 / -897 | +3559 | +875 / +1531 | +1894 | c=1.00: -512 / +3559 / +875 | 75 | +0.116 | +0.672 | -0.01 / -0.05 / +0.16 | ok |
|  | ADD | L6M | -328 / -574 | +3559 | +749 / +1312 | +1894 | c=1.00: -328 / +3559 / +749 | 144 | +0.129 | +0.686 | +0.03 / +0.00 / +0.12 | ok |
|  | ADD | L3M | +1597 / +2794 | -4060 | +863 / +1510 | -6723 | c=1.00: +1597 / -4060 / +863 | 106 | +0.132 | +1.072 | +0.18 / +0.21 / +0.30 | AMBER |
|  | ADD | L6M | +981 / +1716 | -4060 | +1454 / +2544 | -6723 | c=1.00: +981 / -4060 / +1454 | 211 | +0.173 | +1.354 | +0.12 / +0.09 / +0.20 | AMBER |
|  | ADD | L3M | +1185 / +2074 | -4395 | -502 / -878 | -4490 | c=1.00: +1185 / -4395 / -502 | 205 | -0.032 | -0.506 | +0.09 / -0.18 / +0.02 | ok |
|  | ADD | L6M | +827 / +1448 | -4395 | +526 / +920 | -4490 | c=1.00: +827 / -4395 / +526 | 444 | +0.025 | +0.405 | +0.22 / +0.01 / +0.08 | ok |
|  | ADD | L3M | +41 / +71 | +1151 | +1341 / +2347 | +591 | c=1.00: +41 / +1151 / +1341 | 140 | +0.047 | +0.502 | +0.26 / +0.14 / +0.17 | ok |
|  | ADD | L6M | -8 / -14 | +1151 | +798 / +1396 | +591 | c=1.00: -8 / +1151 / +798 | 297 | +0.034 | +0.378 | +0.23 / +0.15 / +0.14 | ok |
|  | ADD | L3M | +2763 / +4835 | -1586 | -976 / -1708 | -7216 | c=1.00: +2763 / -1586 / -976 | 190 | -0.064 | -0.941 | +0.26 / +0.44 / +0.56 | AMBER |
|  | ADD | L3M | -1301 / -2276 | +80 | -681 / -1192 | +6516 | c=1.00: -1301 / +80 / -681 | 62 | +0.108 | +0.515 | +0.14 / -0.14 / -0.08 | ok |
|  | ADD | L6M | -738 / -1291 | +80 | +96 / +168 | +5375 | c=1.00: -738 / +80 / +96 | 135 | +0.155 | +0.774 | +0.08 / -0.07 / -0.03 | ok |
|  | ADD | L3M | -1351 / -2364 | +4160 | +1962 / +3433 | +4820 | c=1.00: -1351 / +4160 / +1962 | 69 | +0.306 | +1.622 | +0.19 / +0.23 / +0.27 | ok |
|  | ADD | L6M | -796 / -1393 | +4160 | +845 / +1478 | +4820 | c=1.00: -796 / +4160 / +845 | 174 | +0.130 | +0.838 | +0.14 / +0.15 / +0.25 | ok |
|  | ADD | Y2023 | +1133 / +1982 | -3552 | +1027 / +1797 | -3664 | c=1.00: +1133 / -3552 / +1027 | 210 | +0.159 | +0.856 | +0.05 / +0.12 / +0.12 | ok |
|  | ADD | Y2024 | -998 / -1746 | -2875 | +711 / +1245 | +2175 | c=1.00: -998 / -2875 / +711 | 287 | +0.113 | +0.613 | +0.18 / +0.08 / +0.28 | ok |
|  | ADD | Y2025 | -3944 / -6902 | +949 | +1299 / +2273 | +603 | c=1.00: -3944 / +949 / +1299 | 295 | +0.188 | +1.045 | +0.12 / -0.01 / +0.12 | ok |
|  | ADD | L3M | +3631 / +6355 | -5279 | -461 / -807 | -11052 | c=1.00: +3631 / -5279 / -461 | 70 | -0.150 | -0.809 | -0.08 / -0.01 / +0.29 | RED |
|  | ADD | L6M | +2248 / +3933 | -5279 | +269 / +471 | -11052 | c=1.00: +2248 / -5279 / +269 | 161 | -0.011 | -0.063 | +0.00 / +0.02 / +0.24 | RED |
|  | ADD | L3M | +1536 / +2688 | -2958 | +320 / +560 | -4034 | c=1.00: +1536 / -2958 / +320 | 204 | +0.025 | +0.398 | +0.21 / +0.19 / +0.31 | ok |
|  | ADD | L6M | +1489 / +2605 | -2958 | +137 / +240 | -4687 | c=1.00: +1489 / -2958 / +137 | 501 | +0.022 | +0.414 | +0.03 / +0.08 / +0.11 | AMBER |
|  | ADD | L3M | +1111 / +1945 | +728 | +3379 / +5913 | -3137 | c=1.00: +1111 / +728 / +3379 | 89 | +0.326 | +2.228 | -0.17 / +0.26 / +0.13 | ok |
|  | ADD | L6M | +847 / +1483 | +728 | +1995 / +3491 | -3137 | c=1.00: +847 / +728 / +1995 | 211 | +0.192 | +1.499 | -0.13 / +0.07 / -0.06 | ok |
|  | ADD | L3M | +1090 / +1907 | -7456 | +2426 / +4246 | -2914 | c=1.00: +1090 / -7456 / +2426 | 152 | +0.207 | +2.422 | +0.23 / +0.13 / +0.13 | ok |
|  | ADD | L6M | +563 / +985 | -7456 | +1149 / +2010 | -2914 | c=1.00: +563 / -7456 / +1149 | 341 | +0.085 | +1.070 | +0.11 / +0.13 / +0.05 | ok |
|  | ADD | L3M | +878 / +1537 | -3885 | +163 / +285 | -1802 | c=1.00: +878 / -3885 / +163 | 68 | +0.011 | +0.057 | +0.15 / +0.26 / +0.28 | ok |
|  | ADD | L6M | +704 / +1232 | -3885 | +618 / +1082 | -1802 | c=1.00: +704 / -3885 / +618 | 154 | +0.114 | +0.650 | +0.04 / +0.18 / +0.20 | ok |
|  | ADD | L3M | -389 / -680 | -3780 | +1541 / +2696 | +1336 | c=1.00: -389 / -3780 / +1541 | 56 | +0.293 | +1.262 | +0.18 / +0.03 / +0.06 | ok |
|  | ADD | L6M | -35 / -62 | -3780 | +1155 / +2022 | +1336 | c=1.00: -35 / -3780 / +1155 | 125 | +0.206 | +0.952 | +0.11 / +0.05 / +0.06 | ok |
|  | ADD | L3M | +2397 / +4195 | -11411 | +1061 / +1856 | -7444 | c=1.00: +2397 / -11411 / +1061 | 265 | +0.064 | +1.306 | +0.13 / +0.10 / +0.13 | AMBER |
|  | ADD | L6M | +1402 / +2454 | -11411 | +1191 / +2084 | -7444 | c=1.00: +1402 / -11411 / +1191 | 564 | +0.045 | +0.944 | +0.21 / +0.07 / +0.16 | AMBER |
|  | ADD | L3M | -1582 / -2768 | +145 | +1532 / +2681 | +6581 | c=1.00: -1582 / +145 / +1532 | 64 | +0.221 | +1.087 | +0.17 / -0.22 / +0.04 | ok |
|  | ADD | L6M | -683 / -1196 | -2981 | +1685 / +2949 | +5375 | c=1.00: -683 / -2981 / +1685 | 137 | +0.305 | +1.549 | +0.06 / -0.10 / +0.07 | ok |
|  | ADD | Y2023 | -940 / -1645 | -2118 | +365 / +638 | -1735 | c=1.00: -940 / -2118 / +365 | 188 | +0.063 | +0.304 | +0.09 / +0.10 / +0.21 | ok |
|  | ADD | Y2024 | +917 / +1605 | +2395 | +621 / +1088 | +3689 | c=1.00: +917 / +2395 / +621 | 256 | +0.115 | +0.556 | -0.02 / +0.01 / +0.15 | ok |
|  | ADD | Y2025 | -5142 / -8999 | -1060 | +894 / +1564 | +5373 | c=1.00: -5142 / -1060 / +894 | 271 | +0.142 | +0.724 | +0.04 / -0.01 / +0.09 | ok |
|  | ADD | L3M | +1097 / +1919 | -3256 | +603 / +1056 | -5742 | c=1.00: +1097 / -3256 / +603 | 92 | +0.100 | +0.706 | +0.08 / +0.07 / +0.06 | AMBER |
|  | ADD | L6M | +1034 / +1810 | -6735 | -506 / -886 | -5742 | c=1.00: +1034 / -6735 / -506 | 190 | -0.028 | -0.195 | +0.04 / +0.08 / +0.09 | AMBER |
|  | ADD | L3M | +705 / +1233 | -2900 | -428 / -749 | -3255 | c=1.00: +705 / -2900 / -428 | 64 | -0.010 | -0.051 | -0.19 / +0.04 / -0.03 | ok |
|  | ADD | L6M | +490 / +858 | -2900 | -16 / -28 | -3255 | c=1.00: +490 / -2900 / -16 | 149 | +0.033 | +0.183 | -0.04 / +0.02 / +0.12 | ok |
|  | ADD | L3M | +1097 / +1919 | -3256 | +603 / +1056 | -5742 | c=1.00: +1097 / -3256 / +603 | 92 | +0.100 | +0.706 | +0.08 / +0.07 / +0.06 | AMBER |
|  | ADD | L6M | +1034 / +1810 | -6735 | -506 / -886 | -5742 | c=1.00: +1034 / -6735 / -506 | 190 | -0.028 | -0.195 | +0.04 / +0.08 / +0.09 | AMBER |
|  | ADD | L3M | +1430 / +2503 | -941 | -891 / -1559 | -4444 | c=1.00: +1430 / -941 / -891 | 95 | -0.155 | -1.136 | -0.03 / -0.24 / -0.03 | ok |
|  | ADD | L6M | +829 / +1452 | -941 | -436 / -763 | -4444 | c=1.00: +829 / -941 / -436 | 208 | -0.071 | -0.545 | -0.00 / -0.17 / -0.07 | ok |
|  | ADD | L3M | +1220 / +2135 | +2706 | -840 / -1470 | -5191 | c=1.00: +1220 / +2706 / -840 | 89 | -0.189 | -1.297 | +0.02 / -0.05 / +0.02 | AMBER |
|  | ADD | L6M | +806 / +1411 | +2706 | +1137 / +1989 | -5191 | c=1.00: +806 / +2706 / +1137 | 206 | +0.090 | +0.689 | -0.06 / -0.03 / -0.12 | AMBER |
|  | ADD | L3M | +3229 / +5652 | -7920 | +113 / +198 | -10820 | c=1.00: +3229 / -7920 / +113 | 69 | +0.067 | +0.358 | +0.12 / +0.33 / +0.38 | RED |
|  | ADD | L6M | +1977 / +3460 | -7920 | +507 / +888 | -10820 | c=1.00: +1977 / -7920 / +507 | 138 | +0.091 | +0.467 | +0.06 / +0.17 / +0.34 | RED |
|  | ADD | L3M | +711 / +1244 | -910 | +1225 / +2143 | -4573 | c=1.00: +711 / -910 / +1225 | 86 | +0.191 | +1.263 | +0.03 / +0.21 / +0.29 | ok |
|  | ADD | L6M | +348 / +610 | -910 | +1318 / +2307 | -4573 | c=1.00: +348 / -910 / +1318 | 190 | +0.153 | +1.075 | +0.08 / +0.08 / +0.25 | ok |
|  | ADD | L3M | +2166 / +3790 | -2680 | -870 / -1523 | -5136 | c=1.00: +2166 / -2680 / -870 | 221 | -0.040 | -0.675 | +0.22 / +0.20 / +0.50 | AMBER |
|  | ADD | L6M | +1260 / +2205 | -2680 | +413 / +723 | -5136 | c=1.00: +1260 / -2680 / +413 | 483 | +0.022 | +0.396 | +0.20 / +0.13 / +0.37 | AMBER |
|  | ADD | L3M | -67 / -116 | +2610 | +2117 / +3704 | +150 | c=1.00: -67 / +2610 / +2117 | 50 | +0.345 | +1.327 | +0.15 / +0.07 / +0.20 | ok |
|  | ADD | L6M | +117 / +205 | -427 | +460 / +805 | +150 | c=1.00: +117 / -427 / +460 | 98 | +0.048 | +0.173 | +0.15 / +0.05 / +0.18 | ok |
|  | ADD | L3M | +4995 / +8742 | -8490 | -1251 / -2189 | -19122 | c=1.00: +4995 / -8490 / -1251 | 105 | -0.108 | -0.872 | +0.09 / +0.19 / +0.31 | RED |
|  | ADD | L6M | +3012 / +5271 | -8490 | +1043 / +1825 | -19122 | c=1.00: +3012 / -8490 / +1043 | 253 | +0.101 | +0.944 | +0.01 / +0.13 / +0.17 | RED |
|  | ADD | L3M | +225 / +393 | -4543 | -449 / -787 | +270 | c=1.00: +225 / -4543 / -449 | 149 | +0.008 | +0.089 | +0.05 / +0.06 / +0.09 | ok |
|  | ADD | L6M | +201 / +352 | -4543 | +7 / +12 | +270 | c=1.00: +201 / -4543 / +7 | 372 | +0.021 | +0.283 | -0.06 / +0.07 / -0.03 | ok |
|  | ADD | L3M | -910 / -1593 | +5096 | -195 / -341 | +3581 | c=1.00: -910 / +5096 / -195 | 131 | -0.017 | -0.176 | +0.44 / +0.20 / +0.39 | ok |
|  | ADD | L6M | -587 / -1028 | +3829 | +235 / +412 | +3581 | c=1.00: -587 / +3829 / +235 | 253 | +0.012 | +0.115 | +0.31 / +0.10 / +0.26 | ok |
|  | ADD | L3M | +3080 / +5389 | -10100 | -1849 / -3236 | -9043 | c=1.00: +3080 / -10100 / -1849 | 118 | -0.101 | -0.921 | +0.10 / +0.16 / +0.16 | AMBER |
|  | ADD | L6M | +1807 / +3163 | -10100 | -25 / -44 | -9043 | c=1.00: +1807 / -10100 / -25 | 230 | +0.017 | +0.147 | +0.18 / +0.10 / +0.13 | AMBER |
|  | ADD | L3M | +2638 / +4617 | -8880 | +860 / +1506 | -8054 | c=1.00: +2638 / -8880 / +860 | 86 | +0.125 | +0.829 | +0.04 / +0.33 / +0.22 | AMBER |
|  | ADD | L6M | +1694 / +2964 | -8880 | +435 / +762 | -8054 | c=1.00: +1694 / -8880 / +435 | 204 | +0.067 | +0.504 | +0.05 / +0.23 / +0.22 | AMBER |
|  | ADD | L3M | +5465 / +9564 | -8505 | +2073 / +3627 | -20246 | c=1.00: +5465 / -8505 / +2073 | 109 | +0.142 | +1.189 | -0.06 / +0.39 / +0.32 | RED |
|  | ADD | L6M | +3368 / +5894 | -8505 | +706 / +1235 | -20246 | c=1.00: +3368 / -8505 / +706 | 276 | +0.040 | +0.409 | -0.00 / +0.20 / +0.15 | RED |
|  | ADD | L3M | +7275 / +12730 | -10060 | -1145 / -2004 | -24131 | c=1.00: +7275 / -10060 / -1145 | 111 | -0.106 | -0.907 | -0.03 / +0.27 / +0.41 | RED |
|  | ADD | L6M | +4534 / +7934 | -10060 | +350 / +612 | -24131 | c=1.00: +4534 / -10060 / +350 | 281 | +0.052 | +0.545 | -0.00 / +0.19 / +0.14 | RED |
|  | ADD | L3M | -110 / -193 | -1865 | +1486 / +2600 | +2395 | c=1.00: -110 / -1865 / +1486 | 55 | +0.296 | +1.254 | +0.04 / +0.12 / +0.24 | ok |
|  | ADD | L6M | -218 / -381 | -1865 | +2072 / +3626 | +2395 | c=1.00: -218 / -1865 / +2072 | 107 | +0.423 | +1.678 | -0.02 / +0.04 / +0.13 | ok |
|  | ADD | Y2023 | -353 / -618 | +121 | +939 / +1643 | +279 | c=1.00: -353 / +121 / +939 | 177 | +0.168 | +0.764 | +0.15 / +0.08 / +0.31 | ok |
|  | ADD | Y2024 | +304 / +531 | +0 | +470 / +822 | +410 | c=1.00: +304 / +0 / +470 | 234 | +0.100 | +0.441 | +0.15 / +0.14 / +0.30 | ok |
|  | ADD | Y2025 | -4916 / -8602 | +125 | +1612 / +2821 | +7911 | c=1.00: -4916 / +125 / +1612 | 257 | +0.287 | +1.390 | +0.04 / +0.07 / +0.17 | ok |
|  | ADD | L3M | +1464 / +2563 | -881 | -924 / -1617 | -6439 | c=1.00: +1464 / -881 / -924 | 135 | -0.049 | -0.507 | +0.04 / -0.01 / +0.20 | AMBER |
|  | ADD | L6M | +916 / +1604 | -881 | -554 / -970 | -6439 | c=1.00: +916 / -881 / -554 | 278 | -0.013 | -0.132 | -0.01 / -0.05 / +0.10 | AMBER |
|  | ADD | L3M | +103 / +180 | +2791 | +296 / +518 | -1494 | c=1.00: +103 / +2791 / +296 | 158 | +0.015 | +0.183 | +0.26 / -0.09 / -0.04 | ok |
|  | ADD | L6M | +70 / +122 | +2791 | +734 / +1284 | -1494 | c=1.00: +70 / +2791 / +734 | 333 | +0.032 | +0.398 | +0.29 / -0.05 / +0.00 | ok |
|  | ADD | L3M | +920 / +1609 | -2635 | -489 / -855 | +159 | c=1.00: +920 / -2635 / -489 | 126 | +0.020 | +0.191 | +0.18 / +0.13 / +0.22 | ok |
|  | ADD | L6M | +610 / +1067 | -2635 | -153 / -267 | +159 | c=1.00: +610 / -2635 / -153 | 298 | +0.016 | +0.178 | +0.12 / +0.08 / +0.19 | ok |
|  | ADD | L3M | +120 / +210 | +1281 | +2701 / +4727 | -1375 | c=1.00: +120 / +1281 / +2701 | 138 | +0.159 | +1.684 | +0.07 / +0.04 / +0.02 | ok |
|  | ADD | L6M | +101 / +177 | +1281 | +1508 / +2639 | -1375 | c=1.00: +101 / +1281 / +1508 | 306 | +0.071 | +0.804 | +0.13 / +0.03 / +0.11 | ok |
|  | ADD | L3M | -427 / -747 | +2630 | +1632 / +2856 | +2141 | c=1.00: -427 / +2630 / +1632 | 68 | +0.297 | +1.553 | +0.08 / +0.08 / +0.22 | ok |
|  | ADD | L6M | -90 / -158 | -3015 | +1031 / +1804 | +2141 | c=1.00: -90 / -3015 / +1031 | 171 | +0.168 | +1.063 | +0.09 / +0.06 / +0.30 | ok |
|  | ADD | L3M | -78 / -136 | +1990 | +55 / +96 | +1134 | c=1.00: -78 / +1990 / +55 | 169 | +0.000 | +0.004 | +0.15 / +0.20 / +0.24 | ok |
|  | ADD | L6M | +1 / +2 | +1990 | -225 / -393 | +1134 | c=1.00: +1 / +1990 / -225 | 357 | -0.015 | -0.194 | +0.15 / +0.11 / +0.10 | ok |
|  | ADD | L3M | +918 / +1606 | -6587 | +2506 / +4386 | -2405 | c=1.00: +918 / -6587 / +2506 | 73 | +0.282 | +1.584 | +0.34 / +0.39 / +0.44 | ok |
|  | ADD | L6M | +471 / +824 | -6587 | +1569 / +2747 | -2405 | c=1.00: +471 / -6587 / +1569 | 148 | +0.189 | +1.037 | +0.22 / +0.24 / +0.22 | ok |
|  | ADD | L3M | +1436 / +2513 | -6366 | +270 / +472 | -3700 | c=1.00: +1436 / -6366 / +270 | 73 | +0.042 | +0.238 | -0.02 / +0.04 / +0.36 | ok |
|  | ADD | L6M | +836 / +1463 | -6366 | +1270 / +2223 | -3700 | c=1.00: +836 / -6366 / +1270 | 157 | +0.193 | +1.123 | -0.06 / +0.00 / +0.15 | ok |
|  | ADD | L3M | +650 / +1138 | -3280 | +2343 / +4100 | -2454 | c=1.00: +650 / -3280 / +2343 | 84 | +0.322 | +2.084 | +0.03 / +0.26 / +0.20 | ok |
|  | ADD | L6M | +293 / +512 | -3280 | +965 / +1688 | -2454 | c=1.00: +293 / -3280 / +965 | 180 | +0.126 | +0.840 | -0.03 / +0.20 / +0.15 | ok |
|  | ADD | L3M | -67 / -116 | -1655 | +960 / +1679 | +2499 | c=1.00: -67 / -1655 / +960 | 68 | +0.139 | +0.729 | -0.12 / +0.07 / +0.07 | ok |
|  | ADD | L6M | +212 / +370 | -3576 | +801 / +1402 | +2499 | c=1.00: +212 / -3576 / +801 | 157 | +0.120 | +0.699 | -0.11 / +0.07 / +0.00 | ok |
|  | ADD | L3M | -910 / -1593 | +5096 | -195 / -341 | +3581 | c=1.00: -910 / +5096 / -195 | 131 | -0.017 | -0.176 | +0.44 / +0.20 / +0.39 | ok |
|  | ADD | L6M | -587 / -1028 | +3829 | +235 / +412 | +3581 | c=1.00: -587 / +3829 / +235 | 253 | +0.012 | +0.115 | +0.31 / +0.10 / +0.26 | ok |
|  | ADD | L3M | +41 / +71 | +1151 | +1341 / +2347 | +591 | c=1.00: +41 / +1151 / +1341 | 140 | +0.047 | +0.502 | +0.26 / +0.14 / +0.17 | ok |
|  | ADD | L6M | -8 / -14 | +1151 | +798 / +1396 | +591 | c=1.00: -8 / +1151 / +798 | 297 | +0.034 | +0.378 | +0.23 / +0.15 / +0.14 | ok |
|  | ADD | L3M | -462 / -808 | -2791 | +2434 / +4259 | +527 | c=1.00: -462 / -2791 / +2434 | 124 | +0.155 | +1.479 | +0.38 / +0.15 / +0.31 | ok |
|  | ADD | L6M | -250 / -437 | -2791 | +1385 / +2423 | +527 | c=1.00: -250 / -2791 / +1385 | 280 | +0.085 | +0.880 | +0.18 / +0.12 / +0.09 | ok |
|  | ADD | Y2023 | +4227 / +7397 | -3513 | +489 / +857 | -11582 | c=1.00: +4227 / -3513 / +489 | 305 | +0.056 | +0.440 | +0.02 / +0.08 / +0.03 | AMBER |
|  | ADD | Y2024 | -2860 / -5005 | +2285 | +147 / +257 | +343 | c=1.00: -2860 / +2285 / +147 | 441 | +0.026 | +0.216 | +0.10 / +0.17 / +0.04 | ok |
|  | ADD | Y2025 | -888 / -1554 | -1725 | +1115 / +1952 | -4348 | c=1.00: -888 / -1725 / +1115 | 482 | +0.113 | +1.028 | +0.14 / +0.04 / +0.16 | ok |
|  | ADD | L3M | -1497 / -2620 | +90 | +1844 / +3227 | +6596 | c=1.00: -1497 / +90 / +1844 | 64 | +0.274 | +1.347 | +0.21 / -0.12 / +0.05 | ok |
|  | ADD | L6M | -593 / -1037 | -3236 | +1339 / +2343 | +5375 | c=1.00: -593 / -3236 / +1339 | 135 | +0.239 | +1.196 | +0.12 / -0.04 / +0.05 | ok |
|  | ADD | L3M | +3662 / +6408 | -1370 | +478 / +836 | -13146 | c=1.00: +3662 / -1370 / +478 | 77 | +0.100 | +0.592 | -0.09 / +0.23 / +0.17 | RED |
|  | ADD | L6M | +2313 / +4047 | -1370 | -829 / -1450 | -13146 | c=1.00: +2313 / -1370 / -829 | 212 | -0.082 | -0.646 | -0.05 / +0.16 / +0.21 | RED |
|  | ADD | L3M | +1458 / +2551 | -7620 | +913 / +1597 | -5985 | c=1.00: +1458 / -7620 / +913 | 65 | +0.167 | +0.835 | +0.21 / +0.28 / +0.40 | AMBER |
|  | ADD | L6M | +969 / +1695 | -7620 | +2010 / +3518 | -5985 | c=1.00: +969 / -7620 / +2010 | 172 | +0.264 | +1.684 | +0.26 / +0.18 / +0.31 | AMBER |
|  | ADD | L3M | +527 / +923 | +3090 | +763 / +1334 | +508 | c=1.00: +527 / +3090 / +763 | 73 | +0.095 | +0.534 | +0.11 / +0.31 / +0.28 | ok |
|  | ADD | L6M | +375 / +656 | -501 | +1325 / +2319 | +508 | c=1.00: +375 / -501 / +1325 | 178 | +0.177 | +1.166 | +0.12 / +0.20 / +0.29 | ok |
|  | ADD | L3M | +3685 / +6449 | +66 | -1271 / -2224 | -6803 | c=1.00: +3685 / +66 / -1271 | 89 | -0.063 | -0.432 | -0.11 / +0.15 / -0.29 | RED |
|  | ADD | L6M | +2155 / +3771 | +66 | +1464 / +2561 | -6803 | c=1.00: +2155 / +66 / +1464 | 210 | +0.193 | +1.498 | +0.00 / +0.11 / -0.03 | AMBER |
|  | ADD | L3M | +223 / +391 | +276 | +634 / +1110 | -669 | c=1.00: +223 / +276 / +634 | 71 | +0.110 | +0.601 | -0.03 / -0.04 / +0.02 | ok |
|  | ADD | L6M | +316 / +553 | -830 | +223 / +391 | -669 | c=1.00: +316 / -830 / +223 | 162 | +0.051 | +0.307 | -0.10 / +0.00 / +0.05 | ok |
|  | ADD | L3M | +1522 / +2664 | -1555 | +1813 / +3173 | -8027 | c=1.00: +1522 / -1555 / +1813 | 117 | +0.170 | +1.529 | +0.27 / +0.29 / +0.46 | AMBER |
|  | ADD | L6M | +789 / +1380 | -1555 | +1441 / +2522 | -8027 | c=1.00: +789 / -1555 / +1441 | 284 | +0.109 | +1.148 | +0.26 / +0.13 / +0.23 | AMBER |
|  | ADD | L3M | +3685 / +6449 | +66 | -1271 / -2224 | -6803 | c=1.00: +3685 / +66 / -1271 | 89 | -0.063 | -0.432 | -0.11 / +0.15 / -0.29 | RED |
|  | ADD | L6M | +2155 / +3771 | +66 | +1464 / +2561 | -6803 | c=1.00: +2155 / +66 / +1464 | 210 | +0.193 | +1.498 | +0.00 / +0.11 / -0.03 | AMBER |
|  | ADD | L3M | +2883 / +5046 | -4056 | +2176 / +3808 | -10298 | c=1.00: +2883 / -4056 / +2176 | 106 | +0.209 | +1.707 | -0.06 / +0.09 / +0.32 | RED |
|  | ADD | L6M | +2420 / +4236 | -4056 | +800 / +1400 | -10298 | c=1.00: +2420 / -4056 / +800 | 254 | +0.099 | +0.936 | +0.05 / +0.01 / +0.18 | RED |
|  | ADD | L3M | -218 / -381 | -1764 | +2643 / +4626 | +2461 | c=1.00: -218 / -1764 / +2643 | 92 | +0.225 | +1.591 | +0.23 / +0.12 / +0.41 | ok |
|  | ADD | L6M | -286 / -500 | -1764 | +1426 / +2496 | +2461 | c=1.00: -286 / -1764 / +1426 | 209 | +0.105 | +0.809 | +0.13 / +0.12 / +0.23 | ok |
|  | ADD | Y2023 | -1302 / -2278 | -2367 | +1136 / +1988 | -2408 | c=1.00: -1302 / -2367 / +1136 | 279 | +0.136 | +0.970 | +0.24 / +0.14 / +0.23 | ok |
|  | ADD | Y2024 | +4641 / +8121 | +1155 | +631 / +1105 | -5481 | c=1.00: +4641 / +1155 / +631 | 395 | +0.078 | +0.581 | +0.15 / +0.04 / +0.27 | AMBER |
|  | ADD | Y2025 | -4630 / -8103 | +3567 | +1703 / +2980 | +6490 | c=1.00: -4630 / +3567 / +1703 | 422 | +0.200 | +1.594 | +0.08 / +0.03 / +0.14 | ok |
|  | ADD | L3M | +650 / +1138 | -3280 | +2343 / +4100 | -2454 | c=1.00: +650 / -3280 / +2343 | 84 | +0.322 | +2.084 | +0.03 / +0.26 / +0.20 | ok |
|  | ADD | L6M | +293 / +512 | -3280 | +965 / +1688 | -2454 | c=1.00: +293 / -3280 / +965 | 180 | +0.126 | +0.840 | -0.03 / +0.20 / +0.15 | ok |
|  | ADD | L3M | +2588 / +4529 | -4460 | -849 / -1486 | -10451 | c=1.00: +2588 / -4460 / -849 | 80 | -0.022 | -0.134 | +0.01 / +0.19 / +0.17 | RED |
|  | ADD | L6M | +1497 / +2619 | -4460 | +301 / +526 | -10451 | c=1.00: +1497 / -4460 / +301 | 177 | +0.082 | +0.537 | -0.05 / +0.15 / +0.10 | RED |
|  | ADD | L3M | -353 / -617 | -2705 | +1632 / +2856 | +2446 | c=1.00: -353 / -2705 / +1632 | 61 | +0.305 | +1.429 | +0.20 / -0.02 / +0.06 | ok |
|  | ADD | L6M | -13 / -24 | -3226 | +1775 / +3107 | +2446 | c=1.00: -13 / -3226 / +1775 | 135 | +0.350 | +1.749 | +0.05 / +0.02 / +0.04 | ok |
|  | ADD | L3M | +2170 / +3798 | -3621 | -251 / -440 | -7464 | c=1.00: +2170 / -3621 / -251 | 78 | -0.026 | -0.155 | +0.29 / +0.29 / +0.44 | AMBER |
|  | ADD | L6M | +1359 / +2379 | -3621 | +284 / +498 | -7464 | c=1.00: +1359 / -3621 / +284 | 151 | +0.037 | +0.207 | +0.25 / +0.16 / +0.38 | AMBER |
|  | ADD | L3M | +5290 / +9258 | -8050 | +642 / +1123 | -16308 | c=1.00: +5290 / -8050 / +642 | 97 | +0.043 | +0.320 | +0.02 / +0.22 / +0.32 | RED |
|  | ADD | L6M | +3166 / +5541 | -8050 | +782 / +1369 | -16308 | c=1.00: +3166 / -8050 / +782 | 212 | +0.067 | +0.526 | -0.01 / +0.17 / +0.15 | RED |
|  | ADD | L3M | +1678 / +2936 | -4680 | -154 / -270 | -4798 | c=1.00: +1678 / -4680 / -154 | 122 | +0.004 | +0.040 | +0.25 / +0.28 / +0.30 | AMBER |
|  | ADD | L6M | +1011 / +1768 | -4680 | -181 / -318 | -4798 | c=1.00: +1011 / -4680 / -181 | 257 | +0.002 | +0.023 | +0.19 / +0.25 / +0.19 | AMBER |
|  | ADD | L3M | +387 / +677 | -3500 | +3660 / +6404 | -3595 | c=1.00: +387 / -3500 / +3660 | 171 | +0.212 | +2.794 | +0.08 / +0.06 / +0.08 | ok |
|  | ADD | L6M | +299 / +523 | -3500 | +1283 / +2245 | -3595 | c=1.00: +299 / -3500 / +1283 | 344 | +0.079 | +1.005 | +0.05 / +0.11 / -0.03 | ok |
|  | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=1.00: -1573 / +95 / +2075 | 62 | +0.326 | +1.553 | +0.23 / -0.07 / +0.10 | ok |
|  | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=1.00: -795 / -796 / +1691 | 135 | +0.312 | +1.560 | +0.05 / -0.03 / +0.01 | ok |
|  | ADD | L3M | -639 / -1119 | -3140 | +1012 / +1772 | +2561 | c=1.00: -639 / -3140 / +1012 | 41 | +0.213 | +0.671 | -0.04 / -0.06 / +0.10 | ok |
|  | ADD | L6M | -177 / -310 | -3711 | +1013 / +1772 | +2561 | c=1.00: -177 / -3711 / +1013 | 90 | +0.228 | +0.761 | -0.01 / +0.02 / +0.12 | ok |
|  | ADD | L3M | +1185 / +2074 | -4395 | -502 / -878 | -4490 | c=1.00: +1185 / -4395 / -502 | 205 | -0.032 | -0.506 | +0.09 / -0.18 / +0.02 | ok |
|  | ADD | L6M | +827 / +1448 | -4395 | +526 / +920 | -4490 | c=1.00: +827 / -4395 / +526 | 444 | +0.025 | +0.405 | +0.22 / +0.01 / +0.08 | ok |
|  | ADD | L3M | +1168 / +2044 | +1606 | +1259 / +2203 | -6114 | c=1.00: +1168 / +1606 / +1259 | 97 | +0.177 | +1.323 | +0.30 / +0.10 / +0.14 | AMBER |
|  | ADD | L6M | +593 / +1037 | +1606 | +483 / +845 | -6114 | c=1.00: +593 / +1606 / +483 | 217 | +0.074 | +0.595 | +0.26 / +0.02 / -0.00 | AMBER |
|  | ADD | L3M | +455 / +797 | -4745 | +368 / +645 | -2343 | c=1.00: +455 / -4745 / +368 | 110 | +0.057 | +0.481 | +0.28 / +0.21 / +0.36 | ok |
|  | ADD | L6M | +298 / +522 | -4745 | +820 / +1434 | -2343 | c=1.00: +298 / -4745 / +820 | 253 | +0.081 | +0.761 | +0.24 / +0.12 / +0.26 | ok |
|  | ADD | L3M | +970 / +1698 | -3845 | +31 / +54 | -2760 | c=1.00: +970 / -3845 / +31 | 88 | +0.032 | +0.217 | +0.15 / -0.05 / +0.15 | ok |
|  | ADD | L6M | +717 / +1255 | -3845 | +198 / +346 | -2760 | c=1.00: +717 / -3845 / +198 | 188 | +0.062 | +0.429 | +0.11 / +0.04 / +0.12 | ok |
|  | ADD | L3M | +594 / +1040 | -2919 | +226 / +396 | -2178 | c=1.00: +594 / -2919 / +226 | 73 | +0.041 | +0.228 | -0.01 / +0.07 / -0.03 | ok |
|  | ADD | L6M | +562 / +984 | -3356 | +800 / +1400 | -2178 | c=1.00: +562 / -3356 / +800 | 159 | +0.116 | +0.686 | -0.04 / +0.09 / +0.09 | ok |
|  | ADD | L3M | +1989 / +3480 | -5646 | +1939 / +3393 | -6939 | c=1.00: +1989 / -5646 / +1939 | 87 | +0.061 | +0.406 | -0.05 / +0.31 / +0.12 | AMBER |
|  | ADD | L6M | +1398 / +2446 | -5646 | +2059 / +3602 | -6939 | c=1.00: +1398 / -5646 / +2059 | 209 | +0.153 | +1.184 | -0.02 / +0.13 / +0.06 | AMBER |
|  | ADD | L3M | +2268 / +3970 | -6790 | +739 / +1292 | -7234 | c=1.00: +2268 / -6790 / +739 | 60 | +0.182 | +0.840 | -0.38 / -0.01 / -0.09 | AMBER |
|  | ADD | L6M | +1509 / +2640 | -6790 | -145 / -254 | -7234 | c=1.00: +1509 / -6790 / -145 | 147 | +0.008 | +0.041 | -0.22 / -0.08 / -0.13 | AMBER |
|  | ADD | L3M | +49 / +85 | +529 | -79 / -138 | +2244 | c=1.00: +49 / +529 / -79 | 113 | -0.026 | -0.224 | -0.09 / +0.08 / +0.02 | ok |
|  | ADD | L6M | +139 / +243 | +279 | +2113 / +3697 | +2244 | c=1.00: +139 / +279 / +2113 | 241 | +0.180 | +1.603 | -0.03 / +0.01 / +0.05 | ok |
|  | ADD | L3M | -241 / -422 | +1639 | -134 / -235 | +2654 | c=1.00: -241 / +1639 / -134 | 81 | -0.036 | -0.223 | +0.17 / -0.05 / +0.35 | ok |
|  | ADD | L6M | -129 / -226 | +1639 | +13 / +23 | +2654 | c=1.00: -129 / +1639 / +13 | 164 | -0.007 | -0.043 | +0.18 / -0.03 / +0.24 | ok |
|  | ADD | L3M | +1066 / +1865 | -4319 | -412 / -721 | -3503 | c=1.00: +1066 / -4319 / -412 | 71 | -0.149 | -0.816 | -0.00 / +0.04 / -0.05 | ok |
|  | ADD | L6M | +648 / +1134 | -4319 | +799 / +1397 | -3503 | c=1.00: +648 / -4319 / +799 | 162 | +0.073 | +0.438 | +0.02 / +0.05 / +0.07 | ok |
|  | ADD | L3M | +7102 / +12429 | -5745 | -515 / -902 | -22905 | c=1.00: +7102 / -5745 / -515 | 88 | -0.014 | -0.095 | +0.08 / +0.12 / +0.14 | RED |
|  | ADD | L6M | +4352 / +7615 | -5745 | +1193 / +2088 | -22905 | c=1.00: +4352 / -5745 / +1193 | 220 | +0.133 | +1.081 | +0.07 / +0.10 / +0.19 | RED |
|  | ADD | L3M | +2834 / +4959 | -5585 | +1087 / +1902 | -9744 | c=1.00: +2834 / -5585 / +1087 | 88 | +0.084 | +0.570 | -0.08 / +0.41 / +0.15 | RED |
|  | ADD | L6M | +1836 / +3213 | -5585 | +1370 / +2397 | -9744 | c=1.00: +1836 / -5585 / +1370 | 207 | +0.136 | +1.043 | -0.05 / +0.21 / +0.04 | RED |
|  | ADD | L3M | +1943 / +3400 | -8722 | +92 / +161 | -5220 | c=1.00: +1943 / -8722 / +92 | 105 | +0.067 | +0.545 | +0.09 / +0.12 / +0.20 | AMBER |
|  | ADD | L6M | +1179 / +2063 | -8722 | +555 / +971 | -5220 | c=1.00: +1179 / -8722 / +555 | 248 | +0.074 | +0.681 | -0.04 / +0.08 / +0.14 | AMBER |
|  | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=1.00: -1573 / +95 / +2075 | 62 | +0.326 | +1.553 | +0.23 / -0.07 / +0.10 | ok |
|  | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=1.00: -795 / -796 / +1691 | 135 | +0.312 | +1.560 | +0.05 / -0.03 / +0.01 | ok |
|  | ADD | L3M | +1284 / +2248 | -8609 | +1939 / +3393 | -1542 | c=1.00: +1284 / -8609 / +1939 | 67 | +0.239 | +1.230 | +0.05 / +0.16 / +0.30 | ok |
|  | ADD | L6M | +889 / +1556 | -8609 | -848 / -1483 | -1542 | c=1.00: +889 / -8609 / -848 | 157 | -0.157 | -0.910 | +0.02 / +0.05 / +0.09 | ok |
|  | ADD | L3M | +5487 / +9602 | -6820 | -1511 / -2644 | -16398 | c=1.00: +5487 / -6820 / -1511 | 79 | -0.184 | -1.118 | +0.12 / +0.19 / +0.19 | RED |
|  | ADD | L6M | +3544 / +6203 | -6820 | -167 / -292 | -16398 | c=1.00: +3544 / -6820 / -167 | 192 | +0.002 | +0.017 | -0.03 / +0.13 / +0.18 | RED |
|  | ADD | L3M | +1438 / +2517 | -1445 | +44 / +77 | -4116 | c=1.00: +1438 / -1445 / +44 | 132 | -0.004 | -0.039 | +0.05 / +0.06 / +0.29 | ok |
|  | ADD | L6M | +798 / +1397 | -1445 | +772 / +1351 | -4116 | c=1.00: +798 / -1445 / +772 | 281 | +0.064 | +0.662 | -0.03 / +0.08 / +0.10 | ok |
|  | ADD | L3M | -467 / -818 | -60 | +1070 / +1872 | +1166 | c=1.00: -467 / -60 / +1070 | 64 | +0.199 | +0.980 | +0.14 / -0.21 / +0.20 | ok |
|  | ADD | L6M | -78 / -136 | -3281 | +1202 / +2104 | +1166 | c=1.00: -78 / -3281 / +1202 | 141 | +0.255 | +1.334 | +0.08 / -0.07 / +0.08 | ok |
|  | ADD | Y2023 | -546 / -955 | -2548 | +788 / +1380 | +640 | c=1.00: -546 / -2548 / +788 | 193 | +0.133 | +0.657 | +0.19 / +0.08 / +0.28 | ok |
|  | ADD | Y2024 | -1639 / -2868 | -2395 | +530 / +927 | +6799 | c=1.00: -1639 / -2395 / +530 | 257 | +0.099 | +0.479 | -0.03 / +0.01 / +0.07 | ok |
|  | ADD | Y2025 | -6988 / -12229 | +2040 | +943 / +1650 | +12431 | c=1.00: -6988 / +2040 / +943 | 275 | +0.160 | +0.832 | -0.02 / -0.07 / +0.09 | ok |
| L0127999d | RK7 | L3M | +1732 / +3031 | -4480 | +483 / +845 | -6145 | c=0.62: +1176 / -3088 / +311 | 75 | +0.040 | +0.230 | +0.12 / -0.05 / +0.02 | AMBER |
| L0127999d | RK7 | L6M | +1265 / +2213 | -4480 | +668 / +1169 | -6145 | c=0.62: +876 / -3088 / +434 | 172 | +0.049 | +0.312 | +0.03 / -0.01 / +0.06 | AMBER |
| L01ae185e | RK7 | L3M | +2761 / +4832 | -5423 | -889 / -1556 | -8102 | c=1.14: +2953 / -5657 / -1084 | 95 | -0.178 | -1.299 | -0.03 / -0.24 / -0.03 | AMBER |
| L01ae185e | RK7 | L6M | +1748 / +3059 | -5423 | -200 / -349 | -8102 | c=1.14: +1872 / -5657 / -287 | 209 | -0.075 | -0.583 | -0.01 / -0.17 / -0.07 | AMBER |
| L02dedbed | RK7 | L3M | +2121 / +3712 | -5705 | +129 / +226 | -7663 | c=1.00: +2121 / -5705 / +129 | 146 | -0.017 | -0.191 | +0.04 / +0.12 / +0.15 | AMBER |
| L02dedbed | RK7 | L6M | +1502 / +2629 | -5705 | +496 / +867 | -7663 | c=1.00: +1502 / -5705 / +496 | 365 | +0.012 | +0.166 | -0.03 / +0.11 / +0.03 | AMBER |
| L02dedbed | ADD | L3M | +616 / +1079 | -4543 | -347 / -607 | -2235 | c=1.00: +616 / -4543 / -347 | 144 | -0.003 | -0.037 | +0.05 / +0.12 / +0.13 | ok |
| L02dedbed | ADD | L6M | +480 / +839 | -4543 | +122 / +213 | -2235 | c=1.00: +480 / -4543 / +122 | 362 | +0.021 | +0.277 | -0.03 / +0.11 / +0.03 | ok |
| L03842e9c | RK7 | L3M | -508 / -889 | -3060 | +2315 / +4051 | +2291 | c=0.50: +301 / -3073 / +1575 | 64 | +0.125 | +0.617 | +0.19 / -0.22 / +0.05 | ok |
| L03842e9c | RK7 | L6M | +35 / +61 | -3570 | +2301 / +4028 | +1857 | c=0.50: +370 / -3073 / +1318 | 138 | +0.160 | +0.820 | +0.07 / -0.10 / +0.07 | ok |
| L03bf70b4 | RK7 | L3M | +77 / +135 | -317 | +479 / +839 | +1478 | c=1.00: +77 / -317 / +479 | 134 | +0.040 | +0.413 | +0.22 / +0.20 / +0.52 | ok |
| L03bf70b4 | RK7 | L6M | +147 / +258 | -317 | +960 / +1679 | +1478 | c=1.00: +147 / -317 / +960 | 274 | +0.069 | +0.700 | +0.19 / +0.19 / +0.27 | ok |
| L04aaa969 | RK7 | L3M | -508 / -889 | -3060 | +2315 / +4051 | +2291 | c=0.50: +301 / -3073 / +1575 | 64 | +0.125 | +0.617 | +0.19 / -0.22 / +0.05 | ok |
| L04aaa969 | RK7 | L6M | +35 / +61 | -3570 | +2301 / +4028 | +1857 | c=0.50: +370 / -3073 / +1318 | 138 | +0.160 | +0.820 | +0.07 / -0.10 / +0.07 | ok |
| L0529c773 | RK7 | L3M | +486 / +851 | -5108 | +2629 / +4602 | -2856 | c=0.50: +922 / -4449 / +1686 | 99 | +0.103 | +0.786 | +0.33 / -0.08 / +0.14 | ok |
| L0529c773 | RK7 | L6M | +313 / +547 | -5108 | +1415 / +2475 | -2856 | c=0.50: +580 / -4449 / +964 | 216 | +0.047 | +0.375 | +0.23 / -0.12 / -0.03 | ok |
| L06c0e4cb | RK7 | L3M | +4567 / +7992 | -7038 | +1219 / +2134 | -13898 | c=0.50: +2740 / -4864 / +1077 | 90 | +0.017 | +0.119 | -0.16 / +0.43 / +0.18 | RED |
| L06c0e4cb | RK7 | L6M | +3025 / +5294 | -7038 | +2044 / +3577 | -13898 | c=0.50: +1790 / -4864 / +1307 | 215 | +0.077 | +0.614 | -0.09 / +0.20 / +0.13 | RED |
| L06c0e4cb | ADD | L3M | +3101 / +5426 | -4559 | +1720 / +3010 | -9032 | c=0.50: +626 / -2384 / +1425 | 88 | +0.036 | +0.246 | -0.16 / +0.42 / +0.19 | AMBER |
| L06c0e4cb | ADD | L6M | +2012 / +3522 | -4559 | +2121 / +3711 | -9032 | c=0.50: +408 / -2384 / +1275 | 212 | +0.090 | +0.705 | -0.08 / +0.19 / +0.13 | AMBER |
| L06eab808 | RK7 | L3M | +2739 / +4793 | -2560 | +1101 / +1927 | -9826 | c=0.50: +1785 / -1710 / +465 | 68 | +0.101 | +0.530 | +0.02 / -0.09 / +0.08 | RED |
| L06eab808 | RK7 | L6M | +1756 / +3073 | -2560 | +1425 / +2494 | -9826 | c=0.50: +1177 / -1710 / +746 | 146 | +0.105 | +0.566 | +0.01 / -0.01 / +0.17 | RED |
| L076ea54b | RK7 | L3M | +260 / +455 | -3190 | +722 / +1264 | +1326 | c=0.50: +769 / -3138 / +634 | 64 | +0.015 | +0.074 | +0.08 / -0.16 / +0.05 | ok |
| L076ea54b | RK7 | L6M | +638 / +1117 | -6170 | +491 / +860 | +1326 | c=0.50: +706 / -3138 / +370 | 140 | +0.019 | +0.101 | +0.04 / -0.09 / +0.02 | ok |
| L082c912d | RK7 | L3M | +3910 / +6842 | -7720 | +1005 / +1759 | -12802 | c=0.50: +2759 / -5403 / +880 | 61 | +0.022 | +0.105 | -0.03 / +0.05 / +0.29 | RED |
| L082c912d | RK7 | L6M | +2381 / +4167 | -7720 | +2736 / +4788 | -12802 | c=0.50: +1683 / -5403 / +1585 | 149 | +0.174 | +0.960 | -0.06 / -0.03 / +0.13 | RED |
| L09ae66e3 | RK7 | L3M | -620 / -1085 | -1005 | +1301 / +2278 | +1164 | c=0.50: -19 / -933 / +967 | 76 | +0.048 | +0.279 | +0.16 / +0.03 / -0.08 | ok |
| L09ae66e3 | RK7 | L6M | -178 / -311 | -1005 | +919 / +1609 | +1164 | c=0.50: +115 / -933 / +750 | 169 | +0.023 | +0.141 | +0.20 / +0.00 / +0.02 | ok |
| L0a216639 | RK7 | L3M | +1084 / +1898 | -3190 | +352 / +616 | -4180 | c=0.50: +759 / -2025 / +224 | 71 | +0.019 | +0.106 | -0.07 / -0.04 / +0.08 | ok |
| L0a216639 | RK7 | L6M | +822 / +1438 | -3190 | +407 / +713 | -4180 | c=0.50: +586 / -2025 / +296 | 163 | +0.015 | +0.093 | -0.01 / -0.02 / +0.12 | ok |
| L0b0998a5 | RK7 | L3M | +2459 / +4304 | -8040 | +685 / +1198 | -10370 | c=1.00: +2459 / -8040 / +685 | 96 | +0.027 | +0.200 | -0.14 / -0.11 / -0.29 | RED |
| L0b0998a5 | RK7 | L6M | +1680 / +2940 | -8040 | +272 / +476 | -10370 | c=1.00: +1680 / -8040 / +272 | 219 | -0.013 | -0.103 | -0.08 / -0.05 / -0.00 | RED |
| L0b6dde51 | RK7 | L3M | +6285 / +10999 | -6194 | -401 / -702 | -20465 | c=0.50: +2859 / -4549 / -241 | 89 | -0.020 | -0.134 | +0.06 / +0.12 / +0.13 | RED |
| L0b6dde51 | RK7 | L6M | +3911 / +6844 | -6194 | +1425 / +2494 | -20465 | c=0.50: +1738 / -4549 / +826 | 221 | +0.061 | +0.499 | +0.05 / +0.10 / +0.18 | RED |
| L0b6dde51 | ADD | L3M | +7102 / +12429 | -5745 | -515 / -902 | -22905 | c=0.50: +3524 / -4090 / -458 | 88 | -0.007 | -0.048 | +0.08 / +0.12 / +0.14 | RED |
| L0b6dde51 | ADD | L6M | +4352 / +7615 | -5745 | +1193 / +2088 | -22905 | c=0.50: +2046 / -4090 / +545 | 220 | +0.066 | +0.541 | +0.07 / +0.10 / +0.19 | RED |
| L0bd23639 | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=0.50: +290 / -3103 / +1882 | 62 | +0.178 | +0.849 | +0.25 / -0.07 / +0.11 | ok |
| L0bd23639 | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=0.50: +318 / -3103 / +1302 | 136 | +0.164 | +0.825 | +0.06 / -0.03 / +0.02 | ok |
| L0bd23639 | RK7 | Y2023 | -1698 / -2972 | -7720 | -122 / -213 | -4200 | c=0.50: +353 / -6846 / -391 | 182 | +0.048 | +0.224 | +0.07 / +0.04 / +0.23 | ok |
| L0bd23639 | RK7 | Y2024 | -1956 / -3423 | -882 | +670 / +1172 | +8949 | c=0.50: -2028 / +45 / +298 | 256 | +0.064 | +0.310 | -0.01 / +0.02 / +0.14 | ok |
| L0bd23639 | RK7 | Y2025 | -5837 / -10214 | +6385 | -137 / -239 | +13807 | c=0.50: -2058 / +4287 / -449 | 269 | +0.051 | +0.260 | +0.00 / -0.01 / +0.02 | ok |
| L0bd23639 | RM7 | L3M | -1391 / -2434 | -100 | +1273 / +2228 | +6039 | c=0.50: -750 / -148 / +249 | 63 | +0.176 | +0.853 | +0.26 / -0.07 / +0.11 | ok |
| L0bd23639 | RM7 | L6M | -799 / -1397 | -100 | +1497 / +2620 | +6039 | c=0.50: -527 / -148 / +517 | 136 | +0.162 | +0.817 | +0.07 / -0.03 / +0.02 | ok |
| L0bd23639 | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=0.50: -916 / +48 / +1143 | 62 | +0.163 | +0.777 | +0.23 / -0.07 / +0.10 | ok |
| L0bd23639 | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=0.50: -500 / +48 / +755 | 135 | +0.156 | +0.780 | +0.05 / -0.03 / +0.01 | ok |
| L0dc67ba7 | RK7 | L3M | +1249 / +2186 | -5260 | +1475 / +2580 | -937 | c=0.50: +1248 / -4173 / +994 | 54 | +0.096 | +0.401 | +0.31 / +0.27 / +0.43 | ok |
| L0dc67ba7 | RK7 | L6M | +1082 / +1893 | -5260 | +1825 / +3194 | -937 | c=0.50: +951 / -4173 / +1083 | 115 | +0.145 | +0.618 | +0.17 / +0.17 / +0.35 | ok |
| L0f2d7c91 | ADD | L3M | +527 / +923 | +3090 | +1129 / +1975 | +508 | c=0.50: +28 / +1545 / +625 | 73 | +0.075 | +0.420 | +0.11 / +0.30 / +0.29 | ok |
| L0f2d7c91 | ADD | L6M | +375 / +657 | -501 | +1448 / +2534 | +508 | c=0.50: +27 / +1545 / +687 | 180 | +0.095 | +0.635 | +0.12 / +0.20 / +0.29 | ok |
| L11967aac | RK7 | L3M | +1601 / +2803 | -3390 | +1088 / +1904 | -4065 | c=1.00: +1601 / -3390 / +1088 | 92 | +0.016 | +0.112 | -0.07 / -0.00 / -0.08 | ok |
| L11967aac | RK7 | L6M | +1022 / +1788 | -3390 | +1365 / +2389 | -4065 | c=1.00: +1022 / -3390 / +1365 | 193 | +0.079 | +0.566 | -0.04 / -0.05 / -0.08 | ok |
| L11967aac | ADD | L3M | +38 / +67 | +134 | +163 / +286 | +1505 | c=1.00: +38 / +134 / +163 | 92 | +0.023 | +0.166 | -0.08 / -0.03 / -0.08 | ok |
| L11967aac | ADD | L6M | -35 / -62 | +134 | +837 / +1465 | +1505 | c=1.00: -35 / +134 / +837 | 192 | +0.088 | +0.629 | -0.05 / -0.06 / -0.08 | ok |
| L121542b3 | RK7 | L3M | +7758 / +13576 | -10893 | -1524 / -2666 | -22636 | c=0.50: +3045 / -6899 / -484 | 122 | -0.092 | -0.866 | -0.16 / +0.07 / +0.09 | RED |
| L124ae942 | RK7 | L3M | +1083 / +1895 | -6570 | +2339 / +4093 | -4545 | c=1.00: +1083 / -6570 / +2339 | 126 | +0.161 | +1.563 | +0.36 / +0.15 / +0.28 | ok |
| L124ae942 | RK7 | L6M | +758 / +1326 | -6570 | +1556 / +2723 | -4545 | c=1.00: +758 / -6570 / +1556 | 283 | +0.091 | +0.957 | +0.16 / +0.11 / +0.07 | ok |
| L12caec95 | RK7 | L3M | +6885 / +12050 | -8104 | -649 / -1136 | -19527 | c=0.53: +3434 / -5677 / -258 | 92 | -0.053 | -0.373 | +0.10 / +0.24 / +0.28 | RED |
| L12caec95 | RK7 | L6M | +4427 / +7747 | -8104 | +510 / +893 | -19527 | c=0.53: +2201 / -5677 / +346 | 224 | +0.019 | +0.156 | +0.02 / +0.17 / +0.24 | RED |
| L12caec95 | ADD | L3M | +6563 / +11485 | -8760 | -719 / -1259 | -17768 | c=0.53: +3308 / -6334 / -541 | 91 | -0.024 | -0.170 | +0.14 / +0.24 / +0.30 | RED |
| L12caec95 | ADD | L6M | +4109 / +7191 | -8760 | +291 / +509 | -17768 | c=0.53: +1991 / -6334 / +30 | 222 | +0.030 | +0.248 | +0.04 / +0.17 / +0.25 | RED |
| L12e67af0 | ADD | L3M | +566 / +991 | -415 | +442 / +774 | -418 | c=1.00: +566 / -415 / +442 | 133 | +0.079 | +0.812 | -0.10 / -0.10 / +0.02 | ok |
| L12e67af0 | ADD | L6M | +246 / +431 | -415 | +1122 / +1963 | -418 | c=1.00: +246 / -415 / +1122 | 268 | +0.116 | +1.148 | -0.12 / -0.07 / +0.03 | ok |
| L13858cd5 | RK7 | L3M | +5014 / +8774 | -8974 | +2186 / +3825 | -16907 | c=0.50: +2515 / -5939 / +1380 | 108 | +0.081 | +0.671 | -0.04 / +0.39 / +0.31 | RED |
| L13858cd5 | RK7 | L6M | +3102 / +5429 | -8974 | +974 / +1705 | -16907 | c=0.50: +1540 / -5939 / +685 | 275 | +0.024 | +0.241 | +0.01 / +0.20 / +0.14 | RED |
| L13858cd5 | ADD | L3M | +5465 / +9564 | -8505 | +2073 / +3627 | -20246 | c=0.50: +2560 / -5470 / +1360 | 109 | +0.071 | +0.594 | -0.06 / +0.39 / +0.32 | RED |
| L13858cd5 | ADD | L6M | +3368 / +5894 | -8505 | +706 / +1235 | -20246 | c=0.50: +1467 / -5470 / +461 | 276 | +0.020 | +0.204 | -0.00 / +0.20 / +0.15 | RED |
| L13a2513b | RK7 | L3M | +1837 / +3214 | -6679 | +981 / +1717 | -6520 | c=1.00: +1837 / -6679 / +981 | 281 | +0.019 | +0.408 | +0.05 / -0.01 / -0.15 | AMBER |
| L13a2513b | RK7 | L6M | +1199 / +2099 | -6679 | +808 / +1414 | -6520 | c=1.00: +1199 / -6679 / +808 | 627 | +0.004 | +0.085 | +0.00 / -0.04 / -0.07 | AMBER |
| L15a07e54 | RK7 | L3M | +672 / +1176 | -1495 | +489 / +856 | -2865 | c=0.50: +594 / -1178 / +251 | 64 | +0.040 | +0.199 | +0.23 / +0.19 / -0.03 | ok |
| L15a07e54 | RK7 | L6M | +644 / +1128 | -2270 | +1360 / +2380 | -2865 | c=0.50: +527 / -1178 / +686 | 143 | +0.106 | +0.562 | +0.09 / +0.15 / +0.13 | ok |
| L1801f948 | RK7 | L3M | +1880 / +3290 | -5690 | -978 / -1712 | -7744 | c=0.50: +1062 / -3275 / -272 | 53 | -0.144 | -0.589 | +0.12 / +0.12 / -0.07 | AMBER |
| L1801f948 | RK7 | L6M | +1523 / +2666 | -5690 | -869 / -1521 | -7744 | c=0.50: +867 / -3275 / -238 | 124 | -0.115 | -0.526 | +0.11 / +0.06 / -0.07 | AMBER |
| L18f42af2 | RK7 | L3M | +4047 / +7082 | -3535 | +350 / +613 | -12829 | c=0.50: +2380 / -3311 / +574 | 62 | -0.039 | -0.186 | -0.16 / +0.04 / +0.02 | RED |
| L18f42af2 | RK7 | L6M | +2645 / +4629 | -3535 | -13 / -22 | -12829 | c=0.50: +1547 / -3311 / +215 | 148 | -0.035 | -0.189 | -0.04 / +0.01 / -0.01 | RED |
| L18fce9f2 | RK7 | L3M | +1301 / +2276 | -3535 | +203 / +354 | -4865 | c=0.50: +892 / -2198 / +108 | 70 | +0.015 | +0.079 | +0.02 / -0.03 / -0.10 | AMBER |
| L18fce9f2 | RK7 | L6M | +941 / +1646 | -3535 | +128 / +224 | -4865 | c=0.50: +667 / -2198 / +65 | 152 | +0.009 | +0.052 | +0.01 / +0.04 / +0.13 | AMBER |
| L1af20032 | RK7 | L3M | +107 / +188 | +690 | +2626 / +4595 | +1537 | c=1.00: +107 / +690 / +2626 | 133 | +0.144 | +1.469 | +0.24 / +0.08 / +0.20 | ok |
| L1af20032 | RK7 | L6M | +361 / +632 | -3010 | +1842 / +3223 | +1537 | c=1.00: +361 / -3010 / +1842 | 250 | +0.117 | +1.085 | +0.10 / +0.07 / +0.06 | ok |
| L1b44d5f3 | RK7 | L3M | +1123 / +1966 | -2396 | +2192 / +3836 | -3404 | c=1.00: +1123 / -2396 / +2192 | 125 | +0.111 | +1.063 | +0.34 / +0.14 / +0.29 | ok |
| L1b44d5f3 | RK7 | L6M | +859 / +1503 | -2396 | +1797 / +3145 | -3404 | c=1.00: +859 / -2396 / +1797 | 262 | +0.108 | +1.051 | +0.22 / +0.11 / +0.22 | ok |
| L1c19f73f | RK7 | L3M | +469 / +822 | -3935 | +2811 / +4920 | -627 | c=0.50: +938 / -4328 / +1677 | 91 | +0.135 | +0.945 | +0.24 / +0.27 / +0.20 | ok |
| L1c19f73f | RK7 | L6M | +307 / +538 | -3935 | +2330 / +4077 | -627 | c=0.50: +612 / -4328 / +1380 | 222 | +0.096 | +0.791 | +0.06 / +0.17 / +0.15 | ok |
| L1c19f73f | ADD | L3M | -573 / -1003 | -1431 | +2829 / +4952 | +3696 | c=0.50: -413 / -1823 / +1738 | 90 | +0.131 | +0.909 | +0.23 / +0.27 / +0.19 | ok |
| L1c19f73f | ADD | L6M | -382 / -668 | -1431 | +2047 / +3582 | +3696 | c=0.50: -262 / -1823 / +1122 | 220 | +0.095 | +0.771 | +0.05 / +0.17 / +0.15 | ok |
| L1d7b6aaf | RK7 | L3M | +1136 / +1989 | -8490 | +1116 / +1952 | -2048 | c=0.50: +1269 / -5788 / +766 | 66 | +0.057 | +0.292 | +0.25 / +0.01 / +0.13 | ok |
| L1d7b6aaf | RK7 | L6M | +780 / +1365 | -8490 | +753 / +1318 | -2048 | c=0.50: +864 / -5788 / +554 | 143 | +0.031 | +0.166 | +0.07 / +0.02 / +0.12 | ok |
| L1e19f853 | RK7 | L3M | +452 / +790 | -1208 | -317 / -555 | -785 | c=1.00: +452 / -1208 / -317 | 96 | -0.076 | -0.560 | +0.31 / +0.12 / +0.28 | ok |
| L1e19f853 | RK7 | L6M | +347 / +607 | -1208 | +776 / +1358 | -785 | c=1.00: +347 / -1208 / +776 | 185 | +0.045 | +0.309 | +0.16 / +0.03 / +0.11 | ok |
| L1e395f95 | RK7 | L3M | +2241 / +3921 | -7425 | +281 / +492 | -5711 | c=0.50: +1571 / -5255 / +211 | 68 | +0.011 | +0.059 | +0.28 / +0.12 / +0.21 | AMBER |
| L1e395f95 | RK7 | L6M | +1522 / +2663 | -7425 | +249 / +436 | -5711 | c=0.50: +1049 / -5255 / +280 | 153 | -0.004 | -0.025 | +0.18 / +0.10 / +0.20 | AMBER |
| L1e50e8ae | RK7 | L3M | +1083 / +1895 | -6570 | +2339 / +4093 | -4545 | c=1.00: +1083 / -6570 / +2339 | 126 | +0.161 | +1.563 | +0.36 / +0.15 / +0.28 | ok |
| L1e50e8ae | RK7 | L6M | +758 / +1326 | -6570 | +1556 / +2723 | -4545 | c=1.00: +758 / -6570 / +1556 | 283 | +0.091 | +0.957 | +0.16 / +0.11 / +0.07 | ok |
| L206021b9 | RK7 | L3M | +1145 / +2004 | -2722 | +2366 / +4140 | -109 | c=0.50: +676 / -1520 / +1673 | 68 | +0.110 | +0.577 | -0.15 / +0.03 / +0.21 | ok |
| L206021b9 | RK7 | L6M | +843 / +1476 | -2722 | +1239 / +2168 | -109 | c=0.50: +536 / -1520 / +924 | 160 | +0.044 | +0.262 | -0.14 / -0.00 / +0.17 | ok |
| L213c2767 | ADD | L3M | +467 / +817 | -3885 | +1322 / +2314 | -1802 | c=0.50: +109 / -1942 / +720 | 67 | +0.097 | +0.502 | +0.12 / +0.17 / +0.26 | ok |
| L213c2767 | ADD | L6M | +511 / +894 | -3885 | +1005 / +1758 | -1802 | c=0.50: +157 / -1942 / +427 | 153 | +0.085 | +0.481 | +0.03 / +0.15 / +0.20 | ok |
| L2176f633 | RK7 | L3M | +1410 / +2468 | -4330 | +1786 / +3126 | -5390 | c=0.63: +1048 / -3037 / +1134 | 72 | +0.165 | +0.916 | +0.02 / -0.02 / +0.16 | AMBER |
| L2176f633 | RK7 | L6M | +970 / +1697 | -4330 | +2340 / +4095 | -5390 | c=0.63: +742 / -3037 / +1526 | 167 | +0.185 | +1.143 | -0.01 / +0.02 / +0.21 | AMBER |
| L21cd89ca | RK7 | L3M | +2051 / +3589 | -6385 | +20 / +35 | -8729 | c=1.00: +2051 / -6385 / +20 | 149 | -0.048 | -0.546 | +0.17 / +0.19 / +0.27 | AMBER |
| L21cd89ca | RK7 | L6M | +1342 / +2349 | -6385 | +1349 / +2361 | -8729 | c=1.00: +1342 / -6385 / +1349 | 325 | +0.064 | +0.775 | +0.08 / +0.04 / +0.17 | AMBER |
| L21f079b6 | RH7 | L3M | -1427 / -2497 | -21 | +1801 / +3151 | +5671 | c=0.50: -737 / -69 / +777 | 63 | +0.176 | +0.853 | +0.26 / -0.07 / +0.11 | ok |
| L21f079b6 | RH7 | L6M | -637 / -1114 | -1686 | +1537 / +2690 | +4180 | c=0.50: -332 / -69 / +557 | 136 | +0.162 | +0.817 | +0.07 / -0.03 / +0.02 | ok |
| L21f079b6 | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=0.50: +290 / -3103 / +1882 | 62 | +0.178 | +0.849 | +0.25 / -0.07 / +0.11 | ok |
| L21f079b6 | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=0.50: +318 / -3103 / +1302 | 136 | +0.164 | +0.825 | +0.06 / -0.03 / +0.02 | ok |
| L21f079b6 | RK7 | Y2023 | -1698 / -2972 | -7720 | -122 / -213 | -4200 | c=0.50: +353 / -6846 / -391 | 182 | +0.048 | +0.224 | +0.07 / +0.04 / +0.23 | ok |
| L21f079b6 | RK7 | Y2024 | -1956 / -3423 | -882 | +670 / +1172 | +8949 | c=0.50: -2028 / +45 / +298 | 256 | +0.064 | +0.310 | -0.01 / +0.02 / +0.14 | ok |
| L21f079b6 | RK7 | Y2025 | -5837 / -10214 | +6385 | -137 / -239 | +13807 | c=0.50: -2058 / +4287 / -449 | 269 | +0.051 | +0.260 | +0.00 / -0.01 / +0.02 | ok |
| L21f079b6 | RM7 | L3M | -1391 / -2434 | -100 | +1273 / +2228 | +6039 | c=0.50: -750 / -148 / +249 | 63 | +0.176 | +0.853 | +0.26 / -0.07 / +0.11 | ok |
| L21f079b6 | RM7 | L6M | -799 / -1397 | -100 | +1497 / +2620 | +6039 | c=0.50: -527 / -148 / +517 | 136 | +0.162 | +0.817 | +0.07 / -0.03 / +0.02 | ok |
| L21f079b6 | RP7 | L3M | -2012 / -3522 | +724 | +1418 / +2481 | +8426 | c=0.50: -1398 / +676 / +486 | 62 | +0.163 | +0.777 | +0.23 / -0.07 / +0.10 | ok |
| L21f079b6 | RP7 | L6M | -1014 / -1774 | -796 | +1313 / +2297 | +4245 | c=0.50: -753 / +676 / +376 | 135 | +0.156 | +0.780 | +0.05 / -0.03 / +0.01 | ok |
| L21f079b6 | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=0.50: -916 / +48 / +1143 | 62 | +0.163 | +0.777 | +0.23 / -0.07 / +0.10 | ok |
| L21f079b6 | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=0.50: -500 / +48 / +755 | 135 | +0.156 | +0.780 | +0.05 / -0.03 / +0.01 | ok |
| L26396d04 | RK7 | L3M | +581 / +1016 | -4000 | +2261 / +3956 | -326 | c=0.50: +768 / -3543 / +1626 | 61 | +0.113 | +0.529 | +0.00 / +0.12 / +0.07 | ok |
| L26396d04 | RK7 | L6M | +569 / +995 | -4000 | +1265 / +2213 | -326 | c=0.50: +603 / -3543 / +965 | 127 | +0.053 | +0.250 | +0.01 / +0.05 / +0.03 | ok |
| L265998e4 | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=0.50: +1046 / -2320 / +360 | 74 | +0.034 | +0.191 | +0.03 / +0.06 / -0.01 | AMBER |
| L265998e4 | RK7 | L6M | +1487 / +2602 | -3945 | +1090 / +1907 | -6714 | c=0.50: +846 / -2320 / +651 | 161 | +0.061 | +0.366 | -0.02 / +0.08 / +0.10 | AMBER |
| L265998e4 | ADD | L3M | +594 / +1040 | -2919 | +226 / +396 | -2178 | c=0.50: +118 / -1460 / +90 | 73 | +0.020 | +0.114 | -0.01 / +0.07 / -0.03 | ok |
| L265998e4 | ADD | L6M | +562 / +984 | -3356 | +800 / +1400 | -2178 | c=0.50: +148 / -1460 / +389 | 159 | +0.058 | +0.343 | -0.04 / +0.09 / +0.09 | ok |
| L27ec09c7 | RK7 | L3M | +1341 / +2346 | -263 | +2262 / +3959 | -6343 | c=0.57: +867 / -821 / +1430 | 116 | +0.104 | +0.925 | +0.28 / +0.29 / +0.46 | AMBER |
| L27ec09c7 | RK7 | L6M | +739 / +1293 | -263 | +1815 / +3176 | -6343 | c=0.57: +494 / -821 / +1202 | 283 | +0.065 | +0.680 | +0.27 / +0.13 / +0.23 | AMBER |
| L27ec09c7 | ADD | L3M | +1522 / +2664 | -1555 | +1813 / +3173 | -8027 | c=0.57: +957 / +743 / +1027 | 117 | +0.097 | +0.874 | +0.27 / +0.29 / +0.46 | AMBER |
| L27ec09c7 | ADD | L6M | +789 / +1380 | -1555 | +1441 / +2522 | -8027 | c=0.57: +426 / +743 / +851 | 284 | +0.062 | +0.656 | +0.26 / +0.13 / +0.23 | AMBER |
| L28e26f99 | RK7 | L3M | +2491 / +4359 | -8655 | +600 / +1050 | -5158 | c=0.59: +2013 / -6386 / +505 | 66 | +0.023 | +0.115 | -0.12 / -0.10 / +0.04 | AMBER |
| L28e26f99 | RK7 | L6M | +1724 / +3018 | -8655 | -479 / -837 | -5158 | c=0.59: +1351 / -6386 / -215 | 163 | -0.053 | -0.320 | -0.13 / -0.08 / -0.12 | AMBER |
| L28e7ee31 | RK7 | L3M | +3071 / +5375 | -6920 | +821 / +1436 | -11572 | c=1.14: +3384 / -7468 / +934 | 93 | +0.106 | +0.758 | +0.08 / +0.08 / +0.08 | RED |
| L28e7ee31 | RK7 | L6M | +2351 / +4115 | -7325 | -236 / -414 | -11572 | c=1.14: +2618 / -8904 / -279 | 192 | -0.040 | -0.284 | +0.04 / +0.08 / +0.09 | RED |
| L2b25565a | RK7 | L3M | +608 / +1063 | -1545 | +1912 / +3346 | -1539 | c=0.89: +564 / -1469 / +1709 | 80 | +0.220 | +1.353 | -0.04 / -0.07 / +0.15 | ok |
| L2b25565a | RK7 | L6M | +533 / +934 | -1545 | +3080 / +5390 | -1539 | c=0.89: +502 / -1469 / +2753 | 181 | +0.325 | +2.180 | -0.02 / -0.04 / +0.18 | ok |
| L2b78d9dc | RK7 | L3M | +4324 / +7567 | -2990 | -599 / -1048 | -12429 | c=0.50: +2446 / -3038 / -88 | 64 | -0.086 | -0.426 | -0.11 / -0.01 / +0.02 | RED |
| L2efa0aa9 | RK7 | L3M | +2709 / +4740 | -5895 | +799 / +1399 | -6291 | c=0.59: +1961 / -4751 / +820 | 64 | -0.005 | -0.024 | -0.33 / -0.05 / -0.06 | AMBER |
| L2efa0aa9 | RK7 | L6M | +1715 / +3001 | -5895 | +1082 / +1893 | -6291 | c=0.59: +1267 / -4751 / +835 | 145 | +0.056 | +0.300 | -0.23 / -0.04 / +0.03 | AMBER |
| L2f768765 | RK7 | L3M | +1497 / +2620 | -6755 | +1244 / +2177 | -4987 | c=0.50: +1368 / -4920 / +886 | 48 | +0.081 | +0.298 | +0.12 / -0.03 / -0.02 | AMBER |
| L2f768765 | RK7 | L6M | +1020 / +1786 | -6755 | +1175 / +2056 | -4987 | c=0.50: +930 / -4920 / +789 | 100 | +0.087 | +0.321 | +0.11 / +0.01 / +0.08 | AMBER |
| L2f89a77d | RK7 | L3M | +4625 / +8094 | -10080 | +481 / +842 | -14639 | c=0.50: +2991 / -6583 / +440 | 73 | +0.006 | +0.034 | +0.10 / +0.09 / +0.27 | RED |
| L2f89a77d | RK7 | L6M | +2875 / +5032 | -10080 | +1938 / +3392 | -14639 | c=0.50: +1876 / -6583 / +1112 | 156 | +0.119 | +0.688 | +0.04 / +0.06 / +0.11 | RED |
| L30ae34bf | RK7 | L3M | +2153 / +3768 | -5435 | -748 / -1310 | -8423 | c=0.50: +1696 / -4261 / -238 | 54 | -0.102 | -0.426 | +0.03 / +0.06 / -0.05 | AMBER |
| L30ae34bf | RK7 | L6M | +1640 / +2871 | -5435 | -450 / -788 | -8423 | c=0.50: +1208 / -4261 / -52 | 126 | -0.071 | -0.332 | +0.03 / -0.00 / -0.01 | AMBER |
| L31db2acf | ADD | L3M | +1411 / +2469 | -2459 | +82 / +144 | -4492 | c=0.50: +275 / -1230 / -14 | 70 | +0.015 | +0.080 | +0.06 / +0.22 / -0.02 | ok |
| L31db2acf | ADD | L6M | +841 / +1472 | -2459 | +11 / +19 | -4492 | c=0.50: +156 / -1230 / -110 | 146 | +0.019 | +0.101 | +0.05 / +0.18 / +0.18 | ok |
| L331856ca | RK7 | L3M | +1172 / +2052 | -4480 | +504 / +882 | -4285 | c=0.54: +806 / -2823 / +289 | 76 | +0.036 | +0.212 | +0.15 / -0.05 / +0.03 | ok |
| L331856ca | RK7 | L6M | +953 / +1668 | -4480 | +760 / +1330 | -4285 | c=0.54: +664 / -2823 / +448 | 173 | +0.048 | +0.309 | +0.09 / +0.02 / +0.10 | ok |
| L33d1c278 | RK7 | L3M | +2378 / +4161 | -2433 | -302 / -529 | -8118 | c=0.50: +1536 / -1998 / -147 | 106 | -0.016 | -0.129 | +0.11 / +0.32 / +0.22 | AMBER |
| L33d1c278 | RK7 | L6M | +1496 / +2617 | -2433 | +839 / +1468 | -8118 | c=0.50: +978 / -1998 / +502 | 263 | +0.029 | +0.280 | +0.03 / +0.14 / +0.19 | AMBER |
| L33d1c278 | ADD | L3M | +946 / +1656 | -869 | +302 / +528 | -3069 | c=0.50: +344 / -435 / +398 | 105 | -0.010 | -0.080 | +0.09 / +0.30 / +0.21 | ok |
| L33d1c278 | ADD | L6M | +518 / +907 | -869 | +918 / +1606 | -3069 | c=0.50: +138 / -435 / +553 | 262 | +0.031 | +0.304 | +0.02 / +0.13 / +0.18 | ok |
| L34dab7c0 | RK7 | L3M | +688 / +1204 | -4180 | +544 / +952 | -2640 | c=0.50: +641 / -2520 / +131 | 70 | +0.064 | +0.345 | +0.24 / -0.01 / +0.23 | ok |
| L3516aa98 | RK7 | L3M | +3594 / +6289 | -6905 | -1417 / -2480 | -9674 | c=0.50: +2417 / -4995 / -421 | 66 | -0.164 | -0.830 | -0.11 / +0.08 / +0.04 | RED |
| L3516aa98 | RK7 | L6M | +2399 / +4198 | -6905 | -1175 / -2057 | -9674 | c=0.50: +1620 / -4995 / -411 | 164 | -0.105 | -0.637 | -0.06 / +0.05 / -0.14 | RED |
| L3597d9f1 | RK7 | L3M | +588 / +1029 | -4275 | +692 / +1211 | +565 | c=0.50: +918 / -3681 / +619 | 59 | +0.013 | +0.061 | -0.01 / -0.24 / +0.02 | ok |
| L3597d9f1 | RK7 | L6M | +464 / +812 | -4275 | +1427 / +2497 | +565 | c=0.50: +651 / -3681 / +888 | 129 | +0.094 | +0.450 | +0.00 / -0.09 / +0.07 | ok |
| L37da9520 | RK7 | L3M | +1176 / +2058 | -4480 | +506 / +885 | -4285 | c=0.60: +849 / -3046 / +319 | 76 | +0.040 | +0.237 | +0.14 / -0.06 / +0.01 | ok |
| L37da9520 | RK7 | L6M | +952 / +1665 | -4480 | +639 / +1117 | -4285 | c=0.60: +694 / -3046 / +409 | 176 | +0.045 | +0.291 | +0.07 / -0.03 / +0.07 | ok |
| L394b3d55 | RK7 | L3M | -32 / -56 | -3080 | +1504 / +2632 | +1286 | c=0.50: +547 / -3083 / +1184 | 64 | +0.054 | +0.267 | -0.01 / -0.27 / -0.04 | ok |
| L394b3d55 | RK7 | L6M | +448 / +783 | -6180 | +1968 / +3444 | +1286 | c=0.50: +562 / -3083 / +1185 | 137 | +0.129 | +0.652 | -0.03 / -0.14 / -0.01 | ok |
| L39ad2f8d | RK7 | L3M | +1445 / +2528 | -5745 | +820 / +1435 | -3785 | c=1.00: +1445 / -5745 / +820 | 129 | +0.045 | +0.450 | +0.16 / -0.02 / +0.19 | ok |
| L39ad2f8d | RK7 | L6M | +1039 / +1817 | -5745 | +879 / +1538 | -3785 | c=1.00: +1039 / -5745 / +879 | 260 | +0.056 | +0.542 | +0.09 / -0.01 / +0.05 | ok |
| L3a102d84 | RK7 | L3M | +541 / +946 | +2066 | +2017 / +3530 | -972 | c=1.00: +541 / +2066 / +2017 | 200 | +0.070 | +1.083 | +0.15 / +0.16 / +0.30 | ok |
| L3a102d84 | RK7 | L6M | +413 / +722 | +1007 | +2434 / +4260 | -972 | c=1.00: +413 / +1007 / +2434 | 436 | +0.100 | +1.615 | +0.17 / +0.07 / +0.12 | ok |
| L3aca3c47 | RK7 | L3M | -215 / -376 | -3000 | +1586 / +2775 | +2131 | c=0.50: +484 / -3043 / +1099 | 65 | +0.081 | +0.406 | +0.17 / -0.16 / +0.04 | ok |
| L3aca3c47 | RK7 | L6M | +234 / +410 | -3850 | +1570 / +2747 | +1857 | c=0.50: +486 / -3043 / +894 | 142 | +0.107 | +0.563 | +0.08 / -0.06 / +0.08 | ok |
| L3aca3c47 | ADD | L3M | -1067 / -1868 | +195 | +621 / +1087 | +6421 | c=0.50: -529 / +98 / +222 | 65 | +0.067 | +0.333 | +0.14 / -0.16 / +0.02 | ok |
| L3aca3c47 | ADD | L6M | -353 / -618 | -3261 | +882 / +1543 | +5375 | c=0.50: -215 / +98 / +263 | 141 | +0.099 | +0.516 | +0.07 / -0.06 / +0.07 | ok |
| L3af9b5b8 | RK7 | L3M | +2902 / +5079 | -4665 | -554 / -970 | -9869 | c=1.00: +2902 / -4665 / -554 | 136 | -0.101 | -1.054 | -0.04 / -0.05 / -0.09 | RED |
| L3af9b5b8 | RK7 | L6M | +1854 / +3245 | -4665 | +494 / +865 | -9869 | c=1.00: +1854 / -4665 / +494 | 303 | +0.002 | +0.020 | -0.00 / -0.02 / +0.04 | RED |
| L3b88100b | RK7 | L3M | +516 / +902 | -3345 | +1248 / +2184 | -1385 | c=1.00: +516 / -3345 / +1248 | 124 | +0.066 | +0.627 | +0.30 / +0.06 / +0.28 | ok |
| L3b88100b | RK7 | L6M | +496 / +868 | -3345 | +943 / +1651 | -1385 | c=1.00: +496 / -3345 / +943 | 260 | +0.053 | +0.509 | +0.17 / +0.03 / +0.10 | ok |
| L3bf18ef0 | RK7 | L3M | +2852 / +4991 | -7605 | +932 / +1631 | -9722 | c=0.50: +2305 / -5345 / +610 | 52 | +0.067 | +0.268 | -0.20 / -0.09 / -0.25 | RED |
| L3bf18ef0 | RK7 | L6M | +1939 / +3394 | -7605 | +827 / +1447 | -9722 | c=0.50: +1531 / -5345 / +627 | 108 | +0.042 | +0.167 | -0.11 / -0.11 / -0.16 | RED |
| L3f82e8a4 | RK7 | L3M | +3058 / +5351 | -5023 | -1031 / -1805 | -7092 | c=0.50: +1772 / -3856 / -352 | 106 | -0.069 | -0.566 | -0.12 / +0.03 / -0.32 | AMBER |
| L3f82e8a4 | RK7 | L6M | +1921 / +3361 | -5023 | +17 / +30 | -7092 | c=0.50: +1131 / -3856 / +194 | 257 | -0.015 | -0.148 | -0.11 / +0.04 / -0.25 | AMBER |
| L3fd2d876 | RK7 | L3M | +1505 / +2635 | -6225 | +1791 / +3134 | -4696 | c=0.50: +1191 / -4656 / +1349 | 42 | +0.114 | +0.369 | -0.03 / -0.06 / +0.11 | AMBER |
| L3fd2d876 | RK7 | L6M | +1198 / +2096 | -6225 | +1528 / +2674 | -4696 | c=0.50: +906 / -4656 / +1022 | 92 | +0.124 | +0.421 | -0.01 / +0.02 / +0.12 | AMBER |
| L3fd2d876 | ADD | L3M | -639 / -1119 | -3140 | +1012 / +1772 | +2561 | c=0.50: -422 / -1570 / +610 | 41 | +0.106 | +0.335 | -0.04 / -0.06 / +0.10 | ok |
| L3fd2d876 | ADD | L6M | -177 / -310 | -3711 | +1013 / +1772 | +2561 | c=0.50: -173 / -1570 / +556 | 90 | +0.114 | +0.380 | -0.01 / +0.02 / +0.12 | ok |
| L3ff574f1 | RK7 | L3M | +1176 / +2058 | -4480 | +506 / +885 | -4285 | c=0.60: +849 / -3046 / +319 | 76 | +0.040 | +0.237 | +0.14 / -0.06 / +0.01 | ok |
| L3ff574f1 | RK7 | L6M | +952 / +1665 | -4480 | +639 / +1117 | -4285 | c=0.60: +694 / -3046 / +409 | 176 | +0.045 | +0.291 | +0.07 / -0.03 / +0.07 | ok |
| L3ffb22ea | RK7 | L3M | +4846 / +8480 | -6305 | -68 / -119 | -13923 | c=1.20: +5842 / -6949 / -230 | 82 | -0.129 | -0.811 | -0.11 / +0.11 / +0.23 | RED |
| L3ffb22ea | RK7 | L6M | +3067 / +5368 | -6305 | +1527 / +2672 | -13923 | c=1.20: +3720 / -6949 / +1739 | 169 | +0.169 | +1.060 | -0.12 / +0.05 / -0.01 | RED |
| L42449cac | RK7 | L3M | +1851 / +3240 | -3495 | +1140 / +1994 | -5845 | c=1.00: +1851 / -3495 / +1140 | 184 | +0.073 | +1.036 | +0.12 / +0.24 / +0.15 | AMBER |
| L42449cac | RK7 | L6M | +1312 / +2296 | -3495 | +1261 / +2206 | -5845 | c=1.00: +1312 / -3495 / +1261 | 450 | +0.060 | +1.007 | +0.14 / +0.14 / +0.15 | AMBER |
| L42449cac | ADD | L3M | +476 / +832 | +616 | +1242 / +2173 | -843 | c=1.00: +476 / +616 / +1242 | 188 | +0.082 | +1.185 | +0.16 / +0.23 / +0.15 | ok |
| L42449cac | ADD | L6M | +381 / +666 | -2530 | +1210 / +2117 | -843 | c=1.00: +381 / -2530 / +1210 | 453 | +0.063 | +1.054 | +0.16 / +0.14 / +0.15 | ok |
| L42ca039a | ADD | L3M | +2741 / +4796 | -1616 | -555 / -972 | -6960 | c=0.50: +1260 / -638 / -132 | 110 | -0.042 | -0.353 | -0.18 / -0.13 / -0.18 | AMBER |
| L42ca039a | ADD | L6M | +1930 / +3378 | -1616 | -396 / -693 | -6960 | c=0.50: +857 / -638 / -231 | 240 | -0.015 | -0.138 | +0.02 / -0.04 / -0.13 | AMBER |
| L43a256ef | RK7 | L3M | +1606 / +2810 | -3535 | +80 / +140 | -4865 | c=0.50: +1017 / -2198 / +54 | 69 | +0.004 | +0.022 | +0.18 / -0.13 / +0.10 | AMBER |
| L43a256ef | RK7 | L6M | +1095 / +1917 | -3535 | +392 / +685 | -4865 | c=0.50: +732 / -2198 / +201 | 153 | +0.028 | +0.159 | +0.08 / +0.01 / +0.16 | AMBER |
| L45eb9271 | RK7 | L3M | +2692 / +4711 | -5695 | +908 / +1590 | -9901 | c=0.50: +1530 / -3278 / +535 | 68 | +0.060 | +0.311 | -0.15 / +0.03 / -0.04 | RED |
| L4697e652 | RK7 | L3M | +2739 / +4793 | -2560 | +1101 / +1927 | -9826 | c=0.50: +1785 / -1710 / +465 | 68 | +0.101 | +0.530 | +0.02 / -0.09 / +0.08 | RED |
| L4697e652 | RK7 | L6M | +1756 / +3073 | -2560 | +1425 / +2494 | -9826 | c=0.50: +1177 / -1710 / +746 | 146 | +0.105 | +0.566 | +0.01 / -0.01 / +0.17 | RED |
| L4702b598 | ADD | L3M | +2394 / +4189 | -12852 | +1604 / +2808 | -11040 | c=0.50: +1137 / -7860 / +1226 | 115 | +0.036 | +0.315 | +0.18 / +0.25 / +0.28 | RED |
| L4702b598 | ADD | L6M | +1380 / +2415 | -12852 | +2057 / +3600 | -11040 | c=0.50: +635 / -7860 / +1207 | 264 | +0.072 | +0.708 | +0.13 / +0.15 / +0.28 | RED |
| L47e7770d | RK7 | L3M | +1636 / +2864 | -4090 | -1058 / -1851 | -6455 | c=0.50: +1045 / -2475 / -331 | 62 | -0.127 | -0.605 | -0.01 / +0.00 / -0.12 | AMBER |
| L47e7770d | RK7 | L6M | +1351 / +2364 | -4090 | -557 / -975 | -6455 | c=0.50: +819 / -2475 / -76 | 156 | -0.069 | -0.401 | +0.01 / -0.04 / -0.10 | AMBER |
| L48453475 | RK7 | L3M | +1507 / +2637 | -3756 | +1097 / +1919 | -4972 | c=1.00: +1507 / -3756 / +1097 | 168 | +0.077 | +0.989 | -0.35 / -0.23 / -0.15 | AMBER |
| L48453475 | ADD | L3M | +1283 / +2245 | -2885 | +614 / +1074 | -5688 | c=1.00: +1283 / -2885 / +614 | 170 | +0.076 | +0.989 | -0.35 / -0.23 / -0.15 | AMBER |
| L48453475 | ADD | L6M | +725 / +1268 | -2885 | +235 / +411 | -5688 | c=1.00: +725 / -2885 / +235 | 368 | +0.042 | +0.571 | -0.17 / -0.10 / -0.22 | AMBER |
| L486bae82 | RK7 | L3M | +986 / +1726 | -4125 | +1752 / +3067 | -5902 | c=1.00: +986 / -4125 / +1752 | 78 | +0.149 | +0.894 | +0.07 / -0.12 / -0.08 | AMBER |
| L486bae82 | RK7 | L6M | +762 / +1334 | -4125 | +1103 / +1929 | -5902 | c=1.00: +762 / -4125 / +1103 | 162 | +0.082 | +0.494 | +0.08 / -0.01 / +0.05 | AMBER |
| L4871f65f | ADD | L3M | +3589 / +6281 | -5460 | +267 / +467 | -14507 | c=0.50: +1694 / -3292 / +84 | 72 | +0.027 | +0.152 | -0.05 / +0.14 / +0.03 | RED |
| L4871f65f | ADD | L6M | +2153 / +3768 | -5460 | +485 / +848 | -14507 | c=0.50: +957 / -3292 / +128 | 177 | +0.045 | +0.297 | -0.17 / +0.13 / -0.00 | RED |
| L4b0ddacb | RK7 | L3M | +688 / +1204 | -4180 | +544 / +952 | -2640 | c=0.50: +641 / -2520 / +131 | 70 | +0.064 | +0.345 | +0.24 / -0.01 / +0.23 | ok |
| L4b0ddacb | ADD | L3M | +453 / +792 | -4444 | -146 / -256 | -1612 | c=0.50: +183 / -2785 / -468 | 69 | +0.050 | +0.268 | +0.20 / -0.01 / +0.20 | ok |
| L4b0ddacb | ADD | L6M | +392 / +687 | -4444 | +362 / +634 | -1612 | c=0.50: +133 / -2785 / +6 | 161 | +0.050 | +0.297 | +0.05 / +0.00 / +0.26 | ok |
| L4ce93efc | RK7 | L3M | +4455 / +7796 | -8750 | +1337 / +2340 | -12915 | c=0.55: +2818 / -6211 / +885 | 60 | +0.100 | +0.463 | -0.38 / -0.01 / -0.09 | RED |
| L4ce93efc | RK7 | L6M | +2971 / +5199 | -8750 | +225 / +393 | -12915 | c=0.55: +1885 / -6211 / +203 | 147 | +0.004 | +0.023 | -0.22 / -0.08 / -0.13 | RED |
| L4e038ffa | RK7 | L3M | +581 / +1016 | -4000 | +2261 / +3956 | -326 | c=0.50: +768 / -3543 / +1626 | 61 | +0.113 | +0.529 | +0.00 / +0.12 / +0.07 | ok |
| L4e038ffa | RK7 | L6M | +569 / +995 | -4000 | +1265 / +2213 | -326 | c=0.50: +603 / -3543 / +965 | 127 | +0.053 | +0.250 | +0.01 / +0.05 / +0.03 | ok |
| L4e53d2d0 | RK7 | L3M | +773 / +1352 | -5345 | +1432 / +2505 | -1140 | c=1.00: +773 / -5345 / +1432 | 116 | +0.032 | +0.286 | +0.24 / +0.10 / +0.21 | ok |
| L4e53d2d0 | RK7 | L6M | +655 / +1147 | -5345 | +855 / +1496 | -1140 | c=1.00: +655 / -5345 / +855 | 252 | +0.021 | +0.198 | +0.13 / +0.13 / +0.14 | ok |
| L4eba93d7 | RK7 | L3M | -510 / -893 | -2835 | +2536 / +4438 | +1432 | c=0.50: +366 / -2961 / +1612 | 63 | +0.159 | +0.771 | +0.28 / -0.09 / +0.12 | ok |
| L4eba93d7 | RK7 | L6M | +68 / +119 | -3830 | +2261 / +3957 | +1432 | c=0.50: +419 / -2961 / +1290 | 132 | +0.166 | +0.810 | +0.09 / -0.05 / +0.04 | ok |
| L4ff77392 | RK7 | L3M | +1877 / +3285 | -287 | +344 / +601 | -5881 | c=0.50: +1116 / -302 / +229 | 104 | +0.012 | +0.096 | +0.06 / +0.20 / +0.09 | AMBER |
| L4ff77392 | RK7 | L6M | +1467 / +2567 | -287 | +791 / +1384 | -5881 | c=0.50: +972 / -302 / +440 | 263 | +0.030 | +0.293 | +0.14 / +0.15 / +0.02 | AMBER |
| L4ff77392 | ADD | L3M | +2110 / +3693 | -2255 | +51 / +89 | -8987 | c=0.50: +1190 / +1555 / -64 | 104 | +0.012 | +0.096 | +0.07 / +0.20 / +0.11 | AMBER |
| L4ff77392 | ADD | L6M | +1655 / +2896 | -2255 | +363 / +634 | -8987 | c=0.50: +1052 / +1555 / +11 | 263 | +0.030 | +0.293 | +0.14 / +0.15 / +0.03 | AMBER |
| L51cd4408 | RK7 | L3M | +1477 / +2585 | -3954 | +973 / +1704 | -4191 | c=1.00: +1477 / -3954 / +973 | 123 | +0.012 | +0.117 | +0.22 / +0.27 / +0.30 | ok |
| L51cd4408 | RK7 | L6M | +1008 / +1763 | -3954 | +674 / +1180 | -4191 | c=1.00: +1008 / -3954 / +674 | 259 | +0.010 | +0.096 | +0.18 / +0.25 / +0.21 | ok |
| L5332c1f1 | RK7 | L3M | +249 / +435 | -1452 | +116 / +204 | +1612 | c=1.00: +249 / -1452 / +116 | 100 | +0.004 | +0.029 | +0.31 / +0.36 / +0.39 | ok |
| L5332c1f1 | RK7 | L6M | +197 / +345 | -1452 | +906 / +1585 | +1612 | c=1.00: +197 / -1452 / +906 | 204 | +0.075 | +0.569 | +0.18 / +0.19 / +0.06 | ok |
| L5332c1f1 | ADD | L3M | -314 / -550 | +966 | +452 / +791 | +3585 | c=1.00: -314 / +966 / +452 | 100 | +0.004 | +0.029 | +0.31 / +0.36 / +0.39 | ok |
| L5332c1f1 | ADD | L6M | -257 / -450 | +966 | +872 / +1527 | +3585 | c=1.00: -257 / +966 / +872 | 203 | +0.071 | +0.532 | +0.18 / +0.20 / +0.07 | ok |
| L537ea1d3 | RK7 | L3M | +1494 / +2614 | -3805 | -758 / -1327 | -6210 | c=0.52: +1004 / -2405 / -205 | 63 | -0.105 | -0.508 | -0.00 / +0.07 / -0.14 | AMBER |
| L537ea1d3 | RK7 | L6M | +1114 / +1949 | -3805 | -192 / -336 | -6210 | c=0.52: +756 / -2405 / +92 | 153 | -0.046 | -0.261 | +0.03 / -0.02 / -0.10 | AMBER |
| L54d8b908 | RK7 | L3M | +4208 / +7365 | -8375 | +292 / +511 | -13279 | c=0.50: +2458 / -5730 / +388 | 59 | -0.018 | -0.080 | +0.02 / +0.04 / +0.45 | RED |
| L54d8b908 | RK7 | L6M | +2977 / +5211 | -8375 | -574 / -1005 | -13279 | c=0.50: +1719 / -5730 / -111 | 141 | -0.074 | -0.386 | -0.01 / +0.08 / +0.34 | RED |
| L55ad4e88 | RK7 | L3M | +2918 / +5107 | -2045 | +613 / +1073 | -10519 | c=0.50: +1690 / -1453 / +651 | 77 | -0.005 | -0.032 | -0.01 / +0.22 / +0.23 | RED |
| L55ad4e88 | RK7 | L6M | +1931 / +3380 | -2045 | +320 / +560 | -10519 | c=0.50: +1140 / -1453 / +439 | 167 | -0.016 | -0.099 | +0.02 / +0.10 / +0.10 | RED |
| L564445b7 | RK7 | L3M | +996 / +1744 | -6260 | +1669 / +2920 | -4057 | c=0.54: +1039 / -4786 / +1226 | 53 | +0.105 | +0.426 | +0.10 / -0.10 / +0.05 | ok |
| L564445b7 | RK7 | L6M | +739 / +1293 | -6260 | +730 / +1277 | -4057 | c=0.54: +728 / -4786 / +652 | 104 | +0.019 | +0.075 | +0.09 / -0.04 / +0.07 | ok |
| L57aa898e | RK7 | L3M | +1787 / +3127 | -3345 | +417 / +730 | -5914 | c=0.50: +1700 / -3216 / +574 | 62 | -0.027 | -0.131 | -0.01 / +0.07 / -0.00 | AMBER |
| L57aa898e | RK7 | L6M | +1218 / +2131 | -3345 | +722 / +1264 | -5914 | c=0.50: +1143 / -3216 / +612 | 140 | +0.018 | +0.092 | +0.02 / +0.03 / +0.20 | AMBER |
| L5879e162 | RK7 | L3M | +180 / +316 | -1962 | +1276 / +2234 | -2585 | c=1.00: +180 / -1962 / +1276 | 238 | +0.053 | +0.964 | +0.34 / +0.34 / +0.23 | ok |
| L5879e162 | RK7 | L6M | +137 / +240 | -1962 | +2049 / +3586 | -2585 | c=1.00: +137 / -1962 / +2049 | 596 | +0.063 | +1.396 | +0.28 / +0.24 / +0.12 | ok |
| L5879e162 | ADD | L3M | -495 / -866 | +295 | +1740 / +3044 | -436 | c=1.00: -495 / +295 / +1740 | 238 | +0.059 | +1.089 | +0.38 / +0.34 / +0.25 | ok |
| L5879e162 | ADD | L6M | -360 / -629 | +295 | +2030 / +3553 | -436 | c=1.00: -360 / +295 / +2030 | 596 | +0.066 | +1.456 | +0.30 / +0.24 / +0.12 | ok |
| L58bcf9fc | RK7 | L3M | +4454 / +7795 | -8394 | +593 / +1038 | -15124 | c=0.59: +2832 / -6157 / +416 | 127 | +0.022 | +0.215 | +0.02 / +0.39 / +0.34 | RED |
| L58bcf9fc | RK7 | L6M | +2688 / +4704 | -8394 | +1645 / +2878 | -15124 | c=0.59: +1679 / -6157 / +1067 | 299 | +0.063 | +0.700 | +0.08 / +0.21 / +0.22 | RED |
| L58bcf9fc | ADD | L3M | +3467 / +6068 | -7925 | +376 / +659 | -13157 | c=0.59: +1890 / -5689 / +145 | 128 | +0.028 | +0.281 | +0.00 / +0.37 / +0.33 | RED |
| L58bcf9fc | ADD | L6M | +2031 / +3554 | -7925 | +1318 / +2307 | -13157 | c=0.59: +1008 / -5689 / +715 | 299 | +0.066 | +0.731 | +0.07 / +0.20 / +0.21 | RED |
| L59b66d32 | RK7 | L3M | +1034 / +1810 | -3645 | +1658 / +2902 | -1417 | c=0.61: +1100 / -3425 / +1249 | 63 | +0.108 | +0.524 | -0.06 / -0.14 / +0.07 | ok |
| L59b66d32 | RK7 | L6M | +859 / +1503 | -3730 | +2515 / +4402 | -1417 | c=0.61: +827 / -3425 / +1644 | 146 | +0.207 | +1.117 | -0.06 / -0.08 / -0.00 | ok |
| L59b66d32 | ADD | L3M | -1124 / -1967 | -585 | +403 / +705 | +5291 | c=0.61: -772 / -354 / +55 | 63 | +0.092 | +0.446 | -0.07 / -0.13 / +0.05 | ok |
| L59b66d32 | ADD | L6M | -503 / -880 | -3141 | +1686 / +2951 | +5291 | c=0.61: -382 / -354 / +853 | 145 | +0.199 | +1.069 | -0.07 / -0.08 / -0.02 | ok |
| L59b66d32 | ADD | Y2023 | +1526 / +2670 | -3883 | +95 / +167 | -3271 | c=0.61: +234 / -2026 / +77 | 230 | +0.004 | +0.023 | +0.06 / +0.09 / +0.03 | ok |
| L59b66d32 | ADD | Y2024 | -2770 / -4847 | -2130 | -41 / -71 | +8495 | c=0.61: -1787 / -1291 / -59 | 297 | +0.004 | +0.024 | -0.07 / -0.01 / +0.06 | ok |
| L59b66d32 | ADD | Y2025 | -6110 / -10692 | +1909 | +1116 / +1953 | +4892 | c=0.61: -4084 / +1527 / +672 | 279 | +0.108 | +0.570 | +0.08 / -0.04 / +0.03 | ok |
| L59d09db1 | RK7 | L3M | +1220 / +2135 | -3920 | +1108 / +1938 | -4825 | c=0.50: +804 / -2390 / +571 | 72 | +0.081 | +0.447 | +0.14 / -0.03 / +0.11 | AMBER |
| L59d09db1 | RK7 | L6M | +1109 / +1942 | -3920 | +874 / +1530 | -4825 | c=0.50: +703 / -2390 / +514 | 167 | +0.048 | +0.300 | +0.11 / -0.02 / +0.21 | AMBER |
| L5a49e86d | RK7 | L3M | -1885 / -3299 | +4777 | +3361 / +5881 | +6800 | c=0.67: -1055 / +2664 / +2360 | 107 | +0.203 | +1.668 | +0.11 / -0.10 / -0.13 | ok |
| L5a49e86d | RK7 | L6M | -418 / -731 | +2050 | +713 / +1248 | -5582 | c=0.67: -124 / +2609 / +593 | 254 | +0.021 | +0.199 | +0.10 / -0.04 / -0.14 | AMBER |
| L5ce83827 | RK7 | L3M | +1565 / +2740 | -3310 | -750 / -1312 | -5359 | c=0.50: +1020 / -2085 / -279 | 51 | -0.100 | -0.393 | +0.08 / +0.15 / -0.02 | AMBER |
| L5ce83827 | RK7 | L6M | +1312 / +2295 | -3310 | -514 / -899 | -5359 | c=0.50: +825 / -2085 / -118 | 116 | -0.077 | -0.329 | +0.10 / +0.07 / +0.00 | AMBER |
| L5d842982 | RK7 | L3M | +3932 / +6880 | -5390 | -523 / -916 | -10036 | c=0.54: +2730 / -4320 / +145 | 89 | -0.094 | -0.643 | +0.05 / +0.22 / +0.29 | RED |
| L5d842982 | RK7 | L6M | +2457 / +4300 | -5390 | +938 / +1641 | -10036 | c=0.54: +1715 / -4320 / +764 | 183 | +0.025 | +0.167 | +0.06 / +0.10 / +0.27 | RED |
| L5ee8ac30 | RK7 | L3M | +3202 / +5604 | -2697 | -623 / -1091 | -5915 | c=0.50: +1303 / -1507 / -364 | 89 | -0.032 | -0.216 | -0.11 / +0.15 / -0.29 | AMBER |
| L5ee8ac30 | RK7 | L6M | +1959 / +3429 | -2697 | +1942 / +3398 | -5915 | c=0.50: +832 / -1507 / +1025 | 211 | +0.098 | +0.764 | +0.00 / +0.11 / -0.04 | AMBER |
| L5ee8ac30 | ADD | L3M | +3685 / +6449 | +66 | -1271 / -2224 | -6803 | c=0.50: +1640 / -530 / -1012 | 89 | -0.032 | -0.216 | -0.11 / +0.15 / -0.29 | RED |
| L5ee8ac30 | ADD | L6M | +2155 / +3771 | +66 | +1464 / +2561 | -6803 | c=0.50: +915 / -530 / +565 | 210 | +0.096 | +0.749 | +0.00 / +0.11 / -0.03 | AMBER |
| L5fefb6e9 | RK7 | L3M | -664 / -1163 | +422 | +3941 / +6897 | +2235 | c=0.80: -421 / +25 / +3172 | 117 | +0.285 | +2.566 | +0.25 / +0.11 / +0.19 | ok |
| L5fefb6e9 | RK7 | L6M | +143 / +251 | +422 | +1571 / +2749 | -5362 | c=0.80: +211 / +25 / +1283 | 259 | +0.100 | +0.961 | +0.13 / +0.07 / +0.10 | AMBER |
| L5ffbcf8d | RK7 | L3M | +1220 / +2135 | -3920 | +1108 / +1938 | -4825 | c=0.50: +804 / -2390 / +571 | 72 | +0.081 | +0.447 | +0.14 / -0.03 / +0.11 | AMBER |
| L5ffbcf8d | RK7 | L6M | +1109 / +1942 | -3920 | +874 / +1530 | -4825 | c=0.50: +703 / -2390 / +514 | 167 | +0.048 | +0.300 | +0.11 / -0.02 / +0.21 | AMBER |
| L60253180 | RK7 | L3M | +2597 / +4545 | -8015 | -422 / -738 | -9005 | c=0.73: +2151 / -6671 / -427 | 80 | +0.002 | +0.012 | +0.10 / -0.10 / +0.12 | AMBER |
| L60253180 | RK7 | L6M | +1942 / +3398 | -8015 | +448 / +784 | -9005 | c=0.73: +1583 / -6671 / +277 | 186 | +0.055 | +0.380 | +0.04 / -0.03 / +0.17 | AMBER |
| L6038df27 | RK7 | L3M | +1123 / +1966 | -2396 | +2192 / +3836 | -3404 | c=1.00: +1123 / -2396 / +2192 | 125 | +0.111 | +1.063 | +0.34 / +0.14 / +0.29 | ok |
| L6038df27 | RK7 | L6M | +859 / +1503 | -2396 | +1797 / +3145 | -3404 | c=1.00: +859 / -2396 / +1797 | 262 | +0.108 | +1.051 | +0.22 / +0.11 / +0.22 | ok |
| L617f2c33 | RK7 | L3M | +2176 / +3807 | -4646 | -1434 / -2510 | -7639 | c=0.50: +2078 / -4324 / -1146 | 44 | -0.071 | -0.240 | +0.10 / +0.07 / -0.09 | AMBER |
| L617f2c33 | RK7 | L6M | +1464 / +2563 | -4646 | -623 / -1090 | -7639 | c=0.50: +1374 / -4324 / -456 | 94 | -0.040 | -0.139 | +0.11 / +0.06 / -0.05 | AMBER |
| L61c9f6b4 | RK7 | L3M | +917 / +1606 | -1213 | +777 / +1361 | -1457 | c=1.00: +917 / -1213 / +777 | 74 | +0.083 | +0.473 | +0.28 / +0.20 / +0.29 | ok |
| L61c9f6b4 | RK7 | L6M | +798 / +1396 | -1213 | +228 / +400 | -1457 | c=1.00: +798 / -1213 / +228 | 166 | -0.001 | -0.005 | +0.16 / +0.17 / +0.14 | ok |
| L63700f14 | RK7 | L3M | +1601 / +2803 | -3390 | +1088 / +1904 | -4065 | c=1.00: +1601 / -3390 / +1088 | 92 | +0.016 | +0.112 | -0.07 / -0.00 / -0.08 | ok |
| L63700f14 | RK7 | L6M | +1022 / +1788 | -3390 | +1365 / +2389 | -4065 | c=1.00: +1022 / -3390 / +1365 | 193 | +0.079 | +0.566 | -0.04 / -0.05 / -0.08 | ok |
| L63700f14 | ADD | L3M | +38 / +67 | +134 | +163 / +286 | +1505 | c=1.00: +38 / +134 / +163 | 92 | +0.023 | +0.166 | -0.08 / -0.03 / -0.08 | ok |
| L63700f14 | ADD | L6M | -35 / -62 | +134 | +837 / +1465 | +1505 | c=1.00: -35 / +134 / +837 | 192 | +0.088 | +0.629 | -0.05 / -0.06 / -0.08 | ok |
| L64faaf78 | RK7 | L3M | +6347 / +11107 | -8590 | -596 / -1043 | -18429 | c=0.75: +4624 / -7214 / -203 | 62 | -0.206 | -0.983 | -0.24 / -0.02 / +0.14 | RED |
| L64faaf78 | RK7 | L6M | +3995 / +6991 | -8590 | +273 / +478 | -18429 | c=0.75: +2889 / -7214 / +347 | 144 | -0.035 | -0.185 | -0.12 / -0.05 / +0.07 | RED |
| L666e883d | RK7 | L3M | +2623 / +4591 | -4580 | -521 / -912 | -5870 | c=0.50: +1530 / -2720 / -212 | 67 | -0.050 | -0.258 | -0.04 / +0.27 / +0.13 | AMBER |
| L666e883d | RK7 | L6M | +1685 / +2948 | -4580 | +650 / +1137 | -5870 | c=0.50: +1017 / -2720 / +461 | 145 | +0.029 | +0.157 | -0.06 / +0.18 / +0.08 | AMBER |
| L66b909fe | RK7 | L3M | +1636 / +2864 | -4090 | -1058 / -1851 | -6455 | c=0.50: +1045 / -2475 / -331 | 62 | -0.127 | -0.605 | -0.01 / +0.00 / -0.12 | AMBER |
| L66b909fe | RK7 | L6M | +1351 / +2364 | -4090 | -557 / -975 | -6455 | c=0.50: +819 / -2475 / -76 | 156 | -0.069 | -0.401 | +0.01 / -0.04 / -0.10 | AMBER |
| L67483d8d | RK7 | L3M | +2672 / +4675 | -5310 | +1856 / +3248 | -7105 | c=1.00: +2672 / -5310 / +1856 | 120 | +0.095 | +0.878 | -0.07 / -0.08 / +0.13 | AMBER |
| L67483d8d | RK7 | L6M | +1851 / +3239 | -5310 | +727 / +1272 | -7105 | c=1.00: +1851 / -5310 / +727 | 259 | +0.011 | +0.106 | -0.05 / -0.03 / +0.13 | AMBER |
| L68b147b4 | RK7 | L3M | +4595 / +8041 | -3125 | -371 / -649 | -14491 | c=0.51: +2147 / -2011 / -177 | 101 | -0.021 | -0.167 | +0.09 / +0.37 / +0.34 | RED |
| L68b147b4 | RK7 | L6M | +2951 / +5163 | -3851 | +743 / +1300 | -14491 | c=0.51: +1396 / -2011 / +418 | 222 | +0.034 | +0.279 | +0.02 / +0.25 / +0.25 | RED |
| L68b147b4 | ADD | L3M | +3534 / +6184 | -1571 | -20 / -34 | -12849 | c=0.51: +1117 / -457 / +174 | 101 | -0.021 | -0.167 | +0.09 / +0.37 / +0.34 | RED |
| L68b147b4 | ADD | L6M | +2199 / +3848 | -3261 | +771 / +1350 | -12849 | c=0.51: +670 / -457 / +447 | 222 | +0.034 | +0.279 | +0.02 / +0.25 / +0.25 | RED |
| L68bfa83f | RK7 | L3M | +4422 / +7739 | -10000 | +835 / +1461 | -15056 | c=0.61: +3195 / -7319 / +686 | 58 | +0.044 | +0.196 | +0.08 / -0.03 / +0.30 | RED |
| L68bfa83f | RK7 | L6M | +2709 / +4741 | -10000 | +1413 / +2473 | -15056 | c=0.61: +1956 / -7319 / +980 | 139 | +0.111 | +0.569 | +0.09 / -0.04 / +0.21 | RED |
| L6be3bb7c | RK7 | L3M | +1601 / +2803 | -3390 | +1088 / +1904 | -4065 | c=1.00: +1601 / -3390 / +1088 | 92 | +0.016 | +0.112 | -0.07 / -0.00 / -0.08 | ok |
| L6be3bb7c | RK7 | L6M | +1022 / +1788 | -3390 | +1365 / +2389 | -4065 | c=1.00: +1022 / -3390 / +1365 | 193 | +0.079 | +0.566 | -0.04 / -0.05 / -0.08 | ok |
| L6be3bb7c | ADD | L3M | +38 / +67 | +134 | +163 / +286 | +1505 | c=1.00: +38 / +134 / +163 | 92 | +0.023 | +0.166 | -0.08 / -0.03 / -0.08 | ok |
| L6be3bb7c | ADD | L6M | -35 / -62 | +134 | +837 / +1465 | +1505 | c=1.00: -35 / +134 / +837 | 192 | +0.088 | +0.629 | -0.05 / -0.06 / -0.08 | ok |
| L6c84f416 | RK7 | L3M | +2088 / +3655 | -5696 | +1786 / +3125 | -4913 | c=0.67: +1907 / -5132 / +1280 | 54 | +0.203 | +0.843 | +0.04 / +0.12 / +0.24 | AMBER |
| L6c84f416 | RK7 | L6M | +1220 / +2134 | -5696 | +2271 / +3974 | -4913 | c=0.67: +1147 / -5132 / +1597 | 106 | +0.286 | +1.122 | -0.02 / +0.04 / +0.13 | AMBER |
| L6e06d524 | RK7 | L3M | +1900 / +3325 | -3456 | -8 / -14 | -7342 | c=1.00: +1900 / -3456 / -8 | 146 | -0.035 | -0.394 | -0.04 / -0.04 / -0.04 | AMBER |
| L6e06d524 | RK7 | L6M | +1275 / +2232 | -3456 | +396 / +694 | -7342 | c=1.00: +1275 / -3456 / +396 | 308 | -0.003 | -0.034 | +0.07 / -0.02 / +0.17 | AMBER |
| L6e35bff0 | RK7 | L3M | +3155 / +5521 | -2885 | -962 / -1684 | -9046 | c=1.00: +3155 / -2885 / -962 | 221 | -0.040 | -0.675 | +0.22 / +0.20 / +0.50 | AMBER |
| L6e35bff0 | RK7 | L6M | +1968 / +3444 | -2885 | +532 / +932 | -9046 | c=1.00: +1968 / -2885 / +532 | 484 | +0.020 | +0.361 | +0.20 / +0.13 / +0.38 | AMBER |
| L6e35bff0 | ADD | L3M | +2166 / +3790 | -2680 | -870 / -1523 | -5136 | c=1.00: +2166 / -2680 / -870 | 221 | -0.040 | -0.675 | +0.22 / +0.20 / +0.50 | AMBER |
| L6e35bff0 | ADD | L6M | +1260 / +2205 | -2680 | +413 / +723 | -5136 | c=1.00: +1260 / -2680 / +413 | 483 | +0.022 | +0.396 | +0.20 / +0.13 / +0.37 | AMBER |
| L6eb4a3b7 | RK7 | L3M | +1969 / +3446 | -3935 | -302 / -528 | -5819 | c=0.76: +1540 / -3203 / -275 | 73 | -0.013 | -0.071 | -0.05 / -0.07 / -0.00 | AMBER |
| L6eb4a3b7 | RK7 | L6M | +1447 / +2533 | -3935 | +1070 / +1873 | -5819 | c=0.76: +1142 / -3203 / +847 | 175 | +0.092 | +0.594 | -0.06 / -0.07 / +0.10 | AMBER |
| L6f742d38 | RK7 | L3M | +1094 / +1915 | -2100 | +726 / +1270 | -1921 | c=0.50: +1110 / -2593 / +238 | 53 | +0.100 | +0.407 | +0.13 / +0.25 / +0.11 | ok |
| L6f742d38 | RK7 | L6M | +887 / +1552 | -2100 | +698 / +1222 | -1921 | c=0.50: +828 / -2593 / +364 | 132 | +0.057 | +0.279 | +0.02 / +0.22 / +0.16 | ok |
| L6fa8234b | RK7 | L3M | +1782 / +3119 | -7971 | +2358 / +4127 | -5082 | c=0.76: +1641 / -7026 / +1905 | 74 | +0.212 | +1.209 | +0.34 / +0.39 / +0.44 | AMBER |
| L6fa8234b | RK7 | L6M | +1084 / +1898 | -7971 | +1578 / +2761 | -5082 | c=0.76: +1010 / -7026 / +1281 | 149 | +0.143 | +0.791 | +0.22 / +0.24 / +0.22 | AMBER |
| L6fa8234b | ADD | L3M | +918 / +1606 | -6587 | +2506 / +4386 | -2405 | c=0.76: +708 / -5642 / +2054 | 73 | +0.215 | +1.207 | +0.34 / +0.39 / +0.44 | ok |
| L6fa8234b | ADD | L6M | +471 / +824 | -6587 | +1569 / +2747 | -2405 | c=0.76: +349 / -5642 / +1273 | 148 | +0.144 | +0.790 | +0.22 / +0.24 / +0.22 | ok |
| L70d2a976 | RK7 | L3M | +2208 / +3863 | -5132 | +603 / +1055 | -4880 | c=0.50: +1569 / -2725 / +35 | 84 | +0.073 | +0.474 | +0.00 / +0.25 / +0.16 | AMBER |
| L70d2a976 | RK7 | L6M | +1336 / +2338 | -5132 | +822 / +1439 | -4880 | c=0.50: +977 / -2725 / +347 | 194 | +0.055 | +0.396 | +0.07 / +0.15 / +0.20 | AMBER |
| L70d2a976 | ADD | L3M | +272 / +476 | -1681 | +1032 / +1806 | +1383 | c=0.50: +166 / +463 / +430 | 83 | +0.078 | +0.501 | -0.01 / +0.25 / +0.15 | ok |
| L70d2a976 | ADD | L6M | +50 / +87 | -1681 | +899 / +1573 | +1383 | c=0.50: +17 / +463 / +407 | 193 | +0.057 | +0.410 | +0.07 / +0.15 / +0.20 | ok |
| L718a3a1d | RK7 | L3M | +1835 / +3211 | -3522 | +590 / +1033 | -6107 | c=0.60: +1586 / -2977 / +698 | 69 | -0.025 | -0.134 | +0.11 / +0.12 / -0.10 | AMBER |
| L718a3a1d | RK7 | L6M | +1230 / +2153 | -3522 | +1694 / +2965 | -6107 | c=0.60: +1043 / -2977 / +1207 | 153 | +0.107 | +0.608 | +0.03 / +0.09 / +0.02 | AMBER |
| L718a3a1d | ADD | L3M | +913 / +1599 | -71 | -211 / -369 | -3719 | c=0.60: +719 / +108 / -146 | 71 | -0.015 | -0.081 | +0.12 / +0.12 / -0.11 | ok |
| L718a3a1d | ADD | L6M | +561 / +981 | -71 | +1110 / +1943 | -3719 | c=0.60: +395 / +108 / +614 | 153 | +0.109 | +0.620 | +0.04 / +0.09 / +0.02 | ok |
| L720e49e8 | RK7 | L3M | +2852 / +4991 | -7605 | +932 / +1631 | -9722 | c=0.50: +2305 / -5345 / +610 | 52 | +0.067 | +0.268 | -0.20 / -0.09 / -0.25 | RED |
| L720e49e8 | RK7 | L6M | +1939 / +3394 | -7605 | +827 / +1447 | -9722 | c=0.50: +1531 / -5345 / +627 | 108 | +0.042 | +0.167 | -0.11 / -0.11 / -0.16 | RED |
| L726fa6ff | ADD | L3M | -360 / -631 | +351 | +798 / +1397 | +1311 | c=1.00: -360 / +351 / +798 | 58 | +0.142 | +0.635 | +0.48 / +0.08 / +0.25 | ok |
| L726fa6ff | ADD | L6M | -80 / -140 | +351 | +539 / +943 | +1311 | c=1.00: -80 / +351 / +539 | 110 | +0.121 | +0.493 | +0.32 / +0.12 / +0.20 | ok |
| L72dec2a9 | RK7 | L3M | +1912 / +3345 | -1734 | +1964 / +3436 | -7092 | c=1.00: +1912 / -1734 / +1964 | 213 | +0.072 | +1.187 | -0.12 / -0.08 / +0.18 | AMBER |
| L72dec2a9 | RK7 | L6M | +1360 / +2379 | -2148 | +931 / +1629 | -7092 | c=1.00: +1360 / -2148 / +931 | 503 | +0.029 | +0.535 | -0.05 / +0.02 / +0.15 | AMBER |
| L72dec2a9 | ADD | L3M | +1505 / +2634 | -1265 | +1153 / +2018 | -6828 | c=1.00: +1505 / -1265 / +1153 | 211 | +0.069 | +1.122 | -0.18 / -0.08 / +0.14 | AMBER |
| L72dec2a9 | ADD | L6M | +1067 / +1868 | -1559 | +281 / +491 | -6828 | c=1.00: +1067 / -1559 / +281 | 501 | +0.027 | +0.504 | -0.08 / +0.02 / +0.13 | AMBER |
| L73076260 | RK7 | L3M | +554 / +969 | -3130 | +2059 / +3602 | -2449 | c=0.57: +803 / -3111 / +1522 | 61 | +0.127 | +0.596 | +0.19 / -0.08 / +0.13 | ok |
| L73076260 | RK7 | L6M | +454 / +794 | -3130 | +1725 / +3020 | -2449 | c=0.57: +596 / -3111 / +1153 | 138 | +0.125 | +0.636 | +0.12 / -0.06 / +0.15 | ok |
| L732f05d4 | ADD | L3M | +764 / +1337 | +773 | +1727 / +3022 | -341 | c=0.50: +208 / +1571 / +1366 | 85 | +0.046 | +0.301 | -0.14 / +0.20 / +0.05 | ok |
| L732f05d4 | ADD | L6M | +668 / +1169 | +354 | +1489 / +2605 | -341 | c=0.50: +211 / +1571 / +948 | 206 | +0.059 | +0.450 | -0.05 / +0.03 / +0.07 | ok |
| L73f2c64b | RK7 | L3M | +5300 / +9275 | -9944 | +1018 / +1781 | -16481 | c=0.50: +2892 / -6424 / +900 | 77 | +0.017 | +0.098 | -0.08 / +0.17 / +0.34 | RED |
| L73f2c64b | RK7 | L6M | +3247 / +5683 | -9944 | +1020 / +1785 | -16481 | c=0.50: +1761 / -6424 / +718 | 166 | +0.041 | +0.252 | +0.03 / +0.15 / +0.23 | RED |
| L73f2c64b | ADD | L3M | +5425 / +9493 | -10670 | +453 / +793 | -15899 | c=0.50: +2509 / -7151 / +335 | 77 | +0.017 | +0.098 | -0.08 / +0.17 / +0.34 | RED |
| L73f2c64b | ADD | L6M | +3256 / +5697 | -10670 | +609 / +1066 | -15899 | c=0.50: +1423 / -7151 / +306 | 165 | +0.041 | +0.253 | +0.03 / +0.15 / +0.23 | RED |
| L74bff562 | ADD | L3M | +42 / +73 | -650 | -763 / -1335 | +1568 | c=1.00: +42 / -650 / -763 | 114 | -0.033 | -0.286 | +0.13 / +0.04 / +0.14 | ok |
| L74bff562 | ADD | L6M | -82 / -143 | -650 | -117 / -204 | +1568 | c=1.00: -82 / -650 / -117 | 246 | +0.008 | +0.075 | +0.15 / +0.01 / +0.29 | ok |
| L7515c303 | RK7 | L3M | +4567 / +7992 | -7038 | +1219 / +2134 | -13898 | c=0.50: +2740 / -4864 / +1077 | 90 | +0.017 | +0.119 | -0.16 / +0.43 / +0.18 | RED |
| L7515c303 | RK7 | L6M | +3025 / +5294 | -7038 | +2044 / +3577 | -13898 | c=0.50: +1790 / -4864 / +1307 | 215 | +0.077 | +0.614 | -0.09 / +0.20 / +0.13 | RED |
| L7515c303 | ADD | L3M | +3101 / +5426 | -4559 | +1720 / +3010 | -9032 | c=0.50: +626 / -2384 / +1425 | 88 | +0.036 | +0.246 | -0.16 / +0.42 / +0.19 | AMBER |
| L7515c303 | ADD | L6M | +2012 / +3522 | -4559 | +2121 / +3711 | -9032 | c=0.50: +408 / -2384 / +1275 | 212 | +0.090 | +0.705 | -0.08 / +0.19 / +0.13 | AMBER |
| L754ec800 | RK7 | L3M | +1906 / +3336 | -5805 | +1232 / +2157 | -8962 | c=1.00: +1906 / -5805 / +1232 | 98 | +0.054 | +0.406 | -0.15 / -0.18 / -0.27 | AMBER |
| L754ec800 | RK7 | L6M | +1335 / +2336 | -5805 | +593 / +1038 | -8962 | c=1.00: +1335 / -5805 / +593 | 215 | -0.001 | -0.007 | -0.09 / -0.09 / -0.07 | AMBER |
| L77a763af | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=0.50: +290 / -3103 / +1882 | 62 | +0.178 | +0.849 | +0.25 / -0.07 / +0.11 | ok |
| L77a763af | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=0.50: +318 / -3103 / +1302 | 136 | +0.164 | +0.825 | +0.06 / -0.03 / +0.02 | ok |
| L77a763af | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=0.50: -916 / +48 / +1143 | 62 | +0.163 | +0.777 | +0.23 / -0.07 / +0.10 | ok |
| L77a763af | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=0.50: -500 / +48 / +755 | 135 | +0.156 | +0.780 | +0.05 / -0.03 / +0.01 | ok |
| L7868084e | RK7 | L3M | +964 / +1686 | -3205 | +1114 / +1950 | -2907 | c=1.00: +964 / -3205 / +1114 | 50 | +0.054 | +0.209 | -0.05 / -0.19 / -0.02 | ok |
| L7868084e | RK7 | L6M | +726 / +1270 | -3205 | +484 / +847 | -2907 | c=1.00: +726 / -3205 / +484 | 100 | -0.026 | -0.095 | +0.09 / +0.00 / +0.14 | ok |
| L79cd626b | RK7 | L3M | +1212 / +2120 | -6540 | +2530 / +4428 | -4437 | c=0.55: +1100 / -4992 / +1758 | 57 | +0.181 | +0.793 | +0.21 / +0.03 / +0.08 | ok |
| L79cd626b | RK7 | L6M | +1013 / +1772 | -6540 | +1797 / +3144 | -4437 | c=0.55: +846 / -4992 / +1232 | 127 | +0.123 | +0.579 | +0.13 / +0.05 / +0.07 | ok |
| L79cd626b | ADD | L3M | -389 / -680 | -3780 | +1541 / +2696 | +1336 | c=0.55: -304 / -2085 / +862 | 56 | +0.162 | +0.697 | +0.18 / +0.03 / +0.06 | ok |
| L79cd626b | ADD | L6M | -35 / -62 | -3780 | +1155 / +2022 | +1336 | c=0.55: -99 / -2085 / +643 | 125 | +0.114 | +0.526 | +0.11 / +0.05 / +0.06 | ok |
| L7a544778 | ADD | L3M | -1452 / -2542 | +90 | +978 / +1712 | +6626 | c=0.50: -837 / +45 / +557 | 64 | +0.071 | +0.351 | +0.20 / -0.15 / +0.07 | ok |
| L7a544778 | ADD | L6M | -618 / -1082 | -3171 | +1301 / +2276 | +5375 | c=0.50: -412 / +45 / +541 | 139 | +0.123 | +0.633 | +0.05 / -0.08 / +0.04 | ok |
| L7ab10be1 | RK7 | L3M | +1675 / +2931 | -1770 | +2019 / +3534 | -7835 | c=0.50: +1435 / -1315 / +1119 | 90 | +0.108 | +0.750 | +0.04 / +0.20 / +0.30 | AMBER |
| L7ab10be1 | RK7 | L6M | +1049 / +1835 | -1770 | +1871 / +3274 | -7835 | c=0.50: +915 / -1315 / +1128 | 193 | +0.087 | +0.619 | +0.09 / +0.07 / +0.25 | AMBER |
| L7ab10be1 | ADD | L3M | +711 / +1244 | -910 | +1225 / +2143 | -4573 | c=0.50: +258 / -455 / +467 | 86 | +0.095 | +0.632 | +0.03 / +0.21 / +0.29 | ok |
| L7ab10be1 | ADD | L6M | +348 / +610 | -910 | +1318 / +2307 | -4573 | c=0.50: +87 / -455 / +673 | 190 | +0.076 | +0.538 | +0.08 / +0.08 / +0.25 | ok |
| L7b30753e | RK7 | L3M | +1253 / +2193 | +2078 | +762 / +1333 | -2002 | c=0.50: +544 / +685 / +442 | 73 | +0.048 | +0.267 | +0.11 / +0.31 / +0.28 | ok |
| L7b30753e | RK7 | L6M | +967 / +1691 | -1090 | +1486 / +2601 | -2002 | c=0.50: +485 / +685 / +803 | 179 | +0.086 | +0.570 | +0.12 / +0.20 / +0.29 | ok |
| L7b30753e | ADD | L3M | +527 / +923 | +3090 | +763 / +1334 | +508 | c=0.50: +28 / +1545 / +442 | 73 | +0.048 | +0.267 | +0.11 / +0.31 / +0.28 | ok |
| L7b30753e | ADD | L6M | +375 / +656 | -501 | +1325 / +2319 | +508 | c=0.50: +27 / +1545 / +625 | 178 | +0.088 | +0.583 | +0.12 / +0.20 / +0.29 | ok |
| L7bfd33b7 | RK7 | L3M | +2741 / +4797 | -5835 | +748 / +1310 | -11055 | c=1.00: +2741 / -5835 / +748 | 99 | -0.002 | -0.015 | -0.18 / +0.01 / -0.13 | RED |
| L7bfd33b7 | RK7 | L6M | +1843 / +3225 | -5835 | +845 / +1478 | -11055 | c=1.00: +1843 / -5835 / +845 | 215 | +0.027 | +0.219 | -0.09 / +0.02 / +0.01 | RED |
| L7ca9fe54 | RK7 | L3M | +1136 / +1989 | -8490 | +1116 / +1952 | -2048 | c=0.50: +1269 / -5788 / +766 | 66 | +0.057 | +0.292 | +0.25 / +0.01 / +0.13 | ok |
| L7ca9fe54 | RK7 | L6M | +780 / +1365 | -8490 | +753 / +1318 | -2048 | c=0.50: +864 / -5788 / +554 | 143 | +0.031 | +0.166 | +0.07 / +0.02 / +0.12 | ok |
| L7e414dd6 | RK7 | L3M | +1238 / +2166 | -5705 | +250 / +437 | -2768 | c=1.00: +1238 / -5705 / +250 | 151 | -0.006 | -0.065 | +0.04 / +0.06 / +0.11 | ok |
| L7e414dd6 | RK7 | L6M | +930 / +1628 | -5705 | +488 / +854 | -2768 | c=1.00: +930 / -5705 / +488 | 375 | +0.012 | +0.173 | -0.06 / +0.07 / -0.02 | ok |
| L7e414dd6 | ADD | L3M | +225 / +393 | -4543 | -449 / -787 | +270 | c=1.00: +225 / -4543 / -449 | 149 | +0.008 | +0.089 | +0.05 / +0.06 / +0.09 | ok |
| L7e414dd6 | ADD | L6M | +201 / +352 | -4543 | +7 / +12 | +270 | c=1.00: +201 / -4543 / +7 | 372 | +0.021 | +0.283 | -0.06 / +0.07 / -0.03 | ok |
| L7f7eb5b6 | RK7 | L3M | +5222 / +9138 | -8385 | -114 / -200 | -17067 | c=0.80: +4180 / -7325 / -165 | 70 | +0.031 | +0.169 | +0.08 / +0.23 / +0.10 | RED |
| L7f7eb5b6 | RK7 | L6M | +3548 / +6209 | -8385 | +68 / +119 | -17067 | c=0.80: +2836 / -7325 / +43 | 174 | +0.013 | +0.083 | +0.02 / +0.06 / +0.15 | RED |
| L80501c0e | RK7 | L3M | +3872 / +6776 | -5501 | -28 / -49 | -12728 | c=0.80: +3040 / -4880 / +92 | 100 | -0.052 | -0.401 | -0.28 / -0.06 / -0.16 | RED |
| L80501c0e | RK7 | L6M | +2495 / +4366 | -5501 | +816 / +1427 | -12728 | c=0.80: +1971 / -4880 / +744 | 211 | +0.030 | +0.237 | -0.22 / -0.00 / -0.17 | RED |
| L83827e30 | RK7 | L3M | +1253 / +2192 | -6390 | +581 / +1017 | -3046 | c=0.50: +917 / -3625 / +256 | 74 | +0.048 | +0.271 | +0.20 / +0.06 / +0.01 | ok |
| L83827e30 | RK7 | L6M | +1096 / +1919 | -6390 | +430 / +752 | -3046 | c=0.50: +759 / -3625 / +267 | 167 | +0.022 | +0.136 | +0.09 / +0.03 / +0.13 | ok |
| L83ff65bd | RK7 | L3M | +2146 / +3756 | -6735 | +1172 / +2050 | -9163 | c=0.50: +1797 / -4911 / +848 | 49 | +0.072 | +0.270 | -0.06 / -0.02 / -0.07 | AMBER |
| L83ff65bd | RK7 | L6M | +1676 / +2933 | -6735 | +690 / +1207 | -9163 | c=0.50: +1285 / -4911 / +563 | 111 | +0.026 | +0.105 | +0.01 / -0.02 / +0.03 | AMBER |
| L840241d1 | RK7 | L3M | +2116 / +3702 | -3106 | +655 / +1147 | -5497 | c=1.00: +2116 / -3106 / +655 | 204 | +0.031 | +0.494 | +0.22 / +0.19 / +0.30 | AMBER |
| L840241d1 | RK7 | L6M | +1767 / +3093 | -3106 | +658 / +1152 | -5497 | c=1.00: +1767 / -3106 / +658 | 501 | +0.025 | +0.460 | +0.04 / +0.08 / +0.11 | AMBER |
| L840241d1 | ADD | L3M | +1536 / +2688 | -2958 | +320 / +560 | -4034 | c=1.00: +1536 / -2958 / +320 | 204 | +0.025 | +0.398 | +0.21 / +0.19 / +0.31 | ok |
| L840241d1 | ADD | L6M | +1489 / +2605 | -2958 | +137 / +240 | -4687 | c=1.00: +1489 / -2958 / +137 | 501 | +0.022 | +0.414 | +0.03 / +0.08 / +0.11 | AMBER |
| L85cb83dc | RK7 | L3M | +588 / +1029 | -4275 | +692 / +1211 | +565 | c=0.50: +918 / -3681 / +619 | 59 | +0.013 | +0.061 | -0.01 / -0.24 / +0.02 | ok |
| L85cb83dc | RK7 | L6M | +464 / +812 | -4275 | +1427 / +2497 | +565 | c=0.50: +651 / -3681 / +888 | 129 | +0.094 | +0.450 | +0.00 / -0.09 / +0.07 | ok |
| L86e12f6b | RK7 | L3M | +1398 / +2446 | -1700 | +750 / +1312 | -4989 | c=0.50: +844 / -1280 / +472 | 70 | +0.043 | +0.232 | +0.01 / -0.00 / +0.08 | AMBER |
| L86e12f6b | RK7 | L6M | +1112 / +1946 | -3860 | +592 / +1036 | -4989 | c=0.50: +685 / -1280 / +341 | 156 | +0.036 | +0.209 | -0.03 / +0.05 / +0.16 | AMBER |
| L875ee048 | RK7 | L3M | +1868 / +3269 | -5505 | +441 / +771 | -6718 | c=1.00: +1868 / -5505 / +441 | 141 | -0.039 | -0.428 | +0.02 / +0.11 / +0.17 | AMBER |
| L875ee048 | RK7 | L6M | +1272 / +2226 | -5505 | +706 / +1235 | -6718 | c=1.00: +1272 / -5505 / +706 | 290 | +0.013 | +0.144 | -0.05 / +0.02 / +0.06 | AMBER |
| L875ee048 | ADD | L3M | +311 / +545 | -1686 | -290 / -508 | -1736 | c=1.00: +311 / -1686 / -290 | 141 | -0.032 | -0.349 | +0.04 / +0.11 / +0.18 | ok |
| L875ee048 | ADD | L6M | +215 / +377 | -1686 | +227 / +397 | -1736 | c=1.00: +215 / -1686 / +227 | 288 | +0.019 | +0.204 | -0.04 / +0.02 / +0.06 | ok |
| L8a396ddf | RK7 | L3M | +3481 / +6091 | -7120 | +203 / +355 | -11482 | c=0.87: +3030 / -6607 / +146 | 75 | +0.056 | +0.322 | +0.14 / +0.11 / +0.09 | RED |
| L8a396ddf | RK7 | L6M | +2322 / +4064 | -7120 | +1017 / +1780 | -11482 | c=0.87: +2029 / -6607 / +888 | 172 | +0.116 | +0.737 | +0.07 / +0.08 / +0.12 | RED |
| L8a7167c1 | RK7 | L3M | +989 / +1730 | -2707 | +1368 / +2394 | -1726 | c=0.50: +988 / -1512 / +982 | 78 | +0.054 | +0.322 | -0.32 / -0.03 / -0.10 | ok |
| L8a7167c1 | RK7 | L6M | +929 / +1626 | -3805 | +1256 / +2199 | -1726 | c=0.50: +792 / -1512 / +863 | 175 | +0.051 | +0.328 | -0.17 / -0.04 / +0.06 | ok |
| L8ba3bc7f | RK7 | L3M | +1450 / +2538 | -3890 | +1055 / +1846 | -5261 | c=0.53: +1043 / -2476 / +459 | 71 | +0.104 | +0.567 | +0.08 / -0.07 / +0.21 | AMBER |
| L8cc60d8e | RK7 | L3M | +1220 / +2136 | -3920 | +1430 / +2502 | -4825 | c=0.50: +804 / -2390 / +732 | 72 | +0.105 | +0.581 | +0.20 / -0.03 / +0.22 | AMBER |
| L8cc60d8e | RK7 | L6M | +1066 / +1866 | -3920 | +1158 / +2026 | -4825 | c=0.50: +689 / -2390 / +656 | 166 | +0.068 | +0.418 | +0.13 / -0.00 / +0.26 | AMBER |
| L8e5a7466 | RK7 | L3M | +2502 / +4378 | -5116 | +596 / +1043 | -8959 | c=1.00: +2502 / -5116 / +596 | 40 | +0.095 | +0.293 | +0.02 / +0.03 / +0.22 | AMBER |
| L8e5a7466 | RK7 | L6M | +1611 / +2819 | -5116 | +928 / +1623 | -8959 | c=1.00: +1611 / -5116 / +928 | 81 | +0.183 | +0.550 | +0.08 / -0.04 / +0.08 | AMBER |
| L8e5a7466 | ADD | L3M | +1424 / +2492 | -3732 | +23 / +40 | -5767 | c=1.00: +1424 / -3732 / +23 | 40 | +0.095 | +0.293 | +0.02 / +0.03 / +0.22 | AMBER |
| L8e5a7466 | ADD | L6M | +840 / +1470 | -3732 | +465 / +813 | -5767 | c=1.00: +840 / -3732 / +465 | 80 | +0.187 | +0.554 | +0.08 / -0.04 / +0.08 | AMBER |
| L8e8dc6f4 | RK7 | L3M | +2761 / +4832 | -5423 | -889 / -1556 | -8102 | c=1.14: +2953 / -5657 / -1084 | 95 | -0.178 | -1.299 | -0.03 / -0.24 / -0.03 | AMBER |
| L8e8dc6f4 | RK7 | L6M | +1748 / +3059 | -5423 | -200 / -349 | -8102 | c=1.14: +1872 / -5657 / -287 | 209 | -0.075 | -0.583 | -0.01 / -0.17 / -0.07 | AMBER |
| L8f126a83 | RK7 | L3M | +892 / +1561 | +969 | +1557 / +2726 | -3857 | c=0.50: +1115 / -403 / +676 | 70 | +0.136 | +0.734 | +0.16 / +0.22 / +0.25 | ok |
| L8f126a83 | RK7 | L6M | +634 / +1109 | +969 | +1034 / +1809 | -3857 | c=0.50: +744 / -403 / +498 | 176 | +0.069 | +0.447 | +0.12 / +0.15 / +0.25 | ok |
| L8f126a83 | ADD | L3M | -1351 / -2364 | +4160 | +1962 / +3433 | +4820 | c=0.50: -774 / +2787 / +989 | 69 | +0.153 | +0.811 | +0.19 / +0.23 / +0.27 | ok |
| L8f126a83 | ADD | L6M | -796 / -1393 | +4160 | +1023 / +1790 | +4820 | c=0.50: -501 / +2787 / +431 | 174 | +0.077 | +0.493 | +0.13 / +0.15 / +0.26 | ok |
| L902b3613 | RK7 | L3M | +1838 / +3217 | -5096 | +151 / +264 | -2342 | c=1.00: +1838 / -5096 / +151 | 110 | -0.060 | -0.510 | -0.24 / +0.09 / +0.05 | AMBER |
| L902b3613 | RK7 | L6M | +1163 / +2035 | -5096 | +1054 / +1844 | -2342 | c=1.00: +1163 / -5096 / +1054 | 225 | +0.056 | +0.469 | -0.19 / +0.01 / -0.05 | ok |
| L908c5381 | RK7 | L3M | +250 / +437 | -4905 | +2403 / +4204 | +952 | c=0.89: +331 / -4703 / +2253 | 67 | +0.193 | +0.994 | +0.04 / +0.02 / +0.00 | ok |
| L908c5381 | RK7 | L6M | +240 / +419 | -4905 | +2329 / +4075 | +952 | c=0.89: +287 / -4703 / +2144 | 140 | +0.238 | +1.232 | +0.03 / -0.00 / +0.15 | ok |
| L9211eb1d | RK7 | L3M | +1646 / +2880 | -1510 | -987 / -1728 | -6147 | c=1.00: +1646 / -1510 / -987 | 88 | -0.084 | -0.570 | +0.07 / -0.05 / +0.07 | AMBER |
| L9211eb1d | RK7 | L6M | +1064 / +1861 | -1510 | +178 / +311 | -6147 | c=1.00: +1064 / -1510 / +178 | 159 | +0.032 | +0.190 | +0.19 / -0.04 / +0.07 | AMBER |
| L925bb0f5 | RK7 | L3M | +2839 / +4968 | -7507 | +2540 / +4445 | -8113 | c=0.50: +1296 / -3912 / +1487 | 106 | +0.108 | +0.877 | -0.06 / +0.09 / +0.31 | AMBER |
| L925bb0f5 | RK7 | L6M | +2345 / +4104 | -7507 | +1343 / +2351 | -8113 | c=0.50: +1185 / -3912 / +771 | 255 | +0.050 | +0.477 | +0.05 / +0.01 / +0.18 | AMBER |
| L925bb0f5 | ADD | L3M | +2883 / +5046 | -4056 | +2176 / +3808 | -10298 | c=0.50: +905 / -462 / +1152 | 106 | +0.105 | +0.853 | -0.06 / +0.09 / +0.32 | RED |
| L925bb0f5 | ADD | L6M | +2420 / +4236 | -4056 | +800 / +1400 | -10298 | c=0.50: +998 / -462 / +238 | 254 | +0.050 | +0.468 | +0.05 / +0.01 / +0.18 | RED |
| L94ef334b | RK7 | L3M | +1796 / +3143 | -8015 | -565 / -989 | -6500 | c=0.82: +1596 / -7130 / -551 | 81 | -0.009 | -0.055 | +0.11 / -0.10 / +0.00 | AMBER |
| L94ef334b | RK7 | L6M | +1362 / +2384 | -8015 | +613 / +1072 | -6500 | c=0.82: +1206 / -7130 / +475 | 187 | +0.076 | +0.526 | +0.05 / -0.07 / +0.10 | AMBER |
| L960fd79a | RK7 | L3M | +1461 / +2557 | -2202 | +713 / +1248 | -2182 | c=1.00: +1461 / -2202 / +713 | 198 | +0.005 | +0.076 | -0.02 / +0.03 / -0.04 | ok |
| L966b7824 | RK7 | L3M | +2551 / +4464 | -5675 | -1141 / -1996 | -7729 | c=0.50: +1446 / -3268 / -470 | 53 | -0.137 | -0.559 | +0.12 / +0.17 / +0.01 | AMBER |
| L966b7824 | RK7 | L6M | +1759 / +3079 | -5675 | -650 / -1138 | -7729 | c=0.50: +1014 / -3268 / -171 | 129 | -0.084 | -0.399 | +0.12 / +0.04 / -0.04 | AMBER |
| L97883de8 | RK7 | L3M | +432 / +755 | -2233 | +651 / +1139 | -589 | c=1.00: +432 / -2233 / +651 | 110 | +0.067 | +0.569 | +0.23 / +0.01 / +0.20 | ok |
| L97883de8 | RK7 | L6M | +398 / +697 | -2233 | +973 / +1703 | -589 | c=1.00: +398 / -2233 / +973 | 218 | +0.080 | +0.644 | +0.17 / +0.02 / +0.22 | ok |
| L97883de8 | ADD | L3M | -1053 / -1843 | +247 | +464 / +812 | +4764 | c=1.00: -1053 / +247 / +464 | 109 | +0.059 | +0.493 | +0.21 / +0.01 / +0.19 | ok |
| L97883de8 | ADD | L6M | -625 / -1093 | +247 | +785 / +1374 | +4764 | c=1.00: -625 / +247 / +785 | 216 | +0.080 | +0.644 | +0.16 / +0.02 / +0.20 | ok |
| L9ade175b | RK7 | L3M | +1120 / +1961 | -2490 | -579 / -1013 | -4285 | c=0.57: +752 / -1791 / -146 | 73 | -0.086 | -0.481 | -0.07 / +0.03 / -0.21 | ok |
| L9bd79a13 | RK7 | L3M | +3481 / +6091 | -7120 | +203 / +355 | -11482 | c=0.87: +3030 / -6607 / +146 | 75 | +0.056 | +0.322 | +0.14 / +0.11 / +0.09 | RED |
| L9bd79a13 | RK7 | L6M | +2322 / +4064 | -7120 | +1017 / +1780 | -11482 | c=0.87: +2029 / -6607 / +888 | 172 | +0.116 | +0.737 | +0.07 / +0.08 / +0.12 | RED |
| L9c7289bd | RK7 | L3M | +1153 / +2017 | -3400 | +2391 / +4184 | -3779 | c=1.26: +1058 / -3483 / +2958 | 56 | +0.526 | +2.268 | +0.05 / +0.11 / +0.26 | ok |
| L9c7289bd | RK7 | L6M | +1125 / +1969 | -4905 | +1417 / +2480 | -3779 | c=1.26: +1197 / -7178 / +1767 | 132 | +0.286 | +1.399 | +0.09 / +0.13 / +0.27 | ok |
| L9c7289bd | ADD | L3M | -273 / -478 | -314 | +1876 / +3283 | +511 | c=1.26: -351 / -397 / +2443 | 56 | +0.526 | +2.268 | +0.05 / +0.11 / +0.26 | ok |
| L9c7289bd | ADD | L6M | +195 / +342 | -4316 | +1020 / +1784 | +511 | c=1.26: +289 / -6588 / +1370 | 132 | +0.286 | +1.399 | +0.09 / +0.13 / +0.27 | ok |
| L9c81a783 | RK7 | L3M | +1929 / +3376 | -7400 | -437 / -765 | -3756 | c=1.07: +1977 / -7688 / -460 | 72 | -0.055 | -0.304 | -0.21 / +0.02 / -0.06 | AMBER |
| L9c81a783 | RK7 | L6M | +1383 / +2420 | -7400 | +56 / +99 | -3756 | c=1.07: +1422 / -7688 / +52 | 173 | -0.010 | -0.064 | -0.11 / -0.01 / +0.05 | ok |
| L9ca1cba1 | RK7 | L3M | +3423 / +5991 | -7480 | +2519 / +4409 | -12511 | c=0.50: +2093 / -5283 / +1674 | 60 | +0.153 | +0.704 | -0.02 / +0.07 / +0.39 | RED |
| L9ca1cba1 | RK7 | L6M | +2128 / +3723 | -7480 | +1947 / +3408 | -12511 | c=0.50: +1315 / -5283 / +1201 | 142 | +0.118 | +0.622 | -0.01 / +0.03 / +0.16 | RED |
| L9d14d49d | RK7 | L3M | +2674 / +4680 | -8184 | +1049 / +1836 | -8732 | c=0.50: +2090 / -5544 / +622 | 67 | +0.069 | +0.356 | +0.22 / +0.31 / +0.41 | AMBER |
| L9d14d49d | RK7 | L6M | +1802 / +3154 | -8184 | +2161 / +3782 | -8732 | c=0.50: +1393 / -5544 / +1157 | 175 | +0.129 | +0.837 | +0.26 / +0.20 / +0.31 | AMBER |
| L9d14d49d | ADD | L3M | +1458 / +2551 | -7620 | +913 / +1597 | -5985 | c=0.50: +924 / -5028 / +412 | 65 | +0.083 | +0.417 | +0.21 / +0.28 / +0.40 | AMBER |
| L9d14d49d | ADD | L6M | +969 / +1695 | -7620 | +2010 / +3518 | -5985 | c=0.50: +582 / -5028 / +999 | 172 | +0.132 | +0.842 | +0.26 / +0.18 / +0.31 | AMBER |
| L9d354ef5 | RK7 | L3M | +4472 / +7825 | -9135 | -813 / -1423 | -13807 | c=0.50: +2965 / -6110 / -1 | 64 | -0.137 | -0.677 | -0.21 / -0.16 / +0.02 | RED |
| L9d354ef5 | RK7 | L6M | +2967 / +5192 | -9135 | +1215 / +2127 | -13807 | c=0.50: +1945 / -6110 / +824 | 145 | +0.061 | +0.326 | -0.13 / -0.10 / +0.02 | RED |
| L9df1be5a | RK7 | L3M | +216 / +379 | -2625 | +3043 / +5325 | +1004 | c=0.50: +307 / -1743 / +2014 | 94 | +0.119 | +0.858 | +0.24 / +0.11 / +0.42 | ok |
| L9df1be5a | RK7 | L6M | +67 / +117 | -2625 | +1707 / +2987 | +1004 | c=0.50: +193 / -1743 / +1185 | 211 | +0.056 | +0.435 | +0.14 / +0.11 / +0.24 | ok |
| L9df764a3 | RK7 | L3M | +3145 / +5503 | -3957 | +463 / +811 | -9064 | c=1.23: +4070 / -4318 / +373 | 81 | -0.065 | -0.403 | -0.22 / -0.03 / +0.03 | AMBER |
| L9df764a3 | RK7 | L6M | +1983 / +3471 | -3957 | +602 / +1054 | -9064 | c=1.23: +2574 / -4318 / +577 | 182 | -0.016 | -0.111 | -0.10 / -0.01 / -0.06 | AMBER |
| L9e844f03 | RK7 | L3M | +2000 / +3500 | -2701 | -627 / -1097 | -7058 | c=1.00: +2000 / -2701 / -627 | 43 | -0.054 | -0.179 | +0.21 / +0.04 / +0.06 | AMBER |
| L9e844f03 | RK7 | L6M | +1244 / +2177 | -2701 | +64 / +112 | -7058 | c=1.00: +1244 / -2701 / +64 | 79 | +0.022 | +0.065 | +0.26 / +0.06 / +0.05 | AMBER |
| L9f026abc | RK7 | L3M | -460 / -805 | +1815 | +2376 / +4157 | +1427 | c=1.00: -460 / +1815 / +2376 | 100 | +0.153 | +1.173 | +0.26 / +0.19 / +0.15 | ok |
| L9f026abc | RK7 | L6M | -26 / -46 | -1155 | +1294 / +2265 | +1427 | c=1.00: -26 / -1155 / +1294 | 201 | +0.072 | +0.538 | +0.10 / +0.13 / +0.04 | ok |
| L9f888218 | RK7 | L3M | +2996 / +5242 | -7180 | -1259 / -2203 | -10118 | c=0.80: +2359 / -6361 / -996 | 69 | -0.165 | -0.876 | -0.07 / +0.07 / -0.15 | RED |
| L9f888218 | RK7 | L6M | +2156 / +3772 | -7180 | -881 / -1542 | -10118 | c=0.80: +1691 / -6361 / -660 | 170 | -0.117 | -0.736 | -0.01 / +0.01 / -0.12 | RED |
| La0dbbae6 | RK7 | L3M | +2569 / +4495 | -5990 | +609 / +1066 | -4682 | c=0.50: +1895 / -4538 / +235 | 61 | +0.066 | +0.312 | -0.08 / +0.19 / -0.01 | AMBER |
| La0dbbae6 | RK7 | L6M | +1615 / +2826 | -5990 | +327 / +571 | -4682 | c=0.50: +1218 / -4538 / +176 | 149 | +0.023 | +0.125 | -0.09 / +0.18 / -0.02 | AMBER |
| La0dbbae6 | ADD | L3M | +484 / +847 | -2904 | +754 / +1319 | +1428 | c=0.50: +258 / -1452 / +287 | 60 | +0.084 | +0.389 | -0.05 / +0.20 / +0.01 | ok |
| La0dbbae6 | ADD | L6M | +225 / +394 | -2904 | +222 / +388 | +1428 | c=0.50: +105 / -1452 / +38 | 147 | +0.028 | +0.153 | -0.07 / +0.18 / -0.02 | ok |
| La1d96e70 | RK7 | L3M | +1377 / +2410 | -2540 | +1706 / +2986 | -5386 | c=0.50: +991 / -1700 / +1295 | 64 | +0.070 | +0.343 | +0.18 / +0.22 / +0.31 | AMBER |
| La1d96e70 | RK7 | L6M | +1108 / +1940 | -2540 | +858 / +1501 | -5386 | c=0.50: +779 / -1700 / +716 | 155 | +0.021 | +0.118 | +0.04 / +0.14 / +0.17 | AMBER |
| La3d84d38 | RK7 | L3M | +1929 / +3376 | -7400 | -437 / -765 | -3756 | c=1.07: +1977 / -7688 / -460 | 72 | -0.055 | -0.304 | -0.21 / +0.02 / -0.06 | AMBER |
| La3d84d38 | RK7 | L6M | +1383 / +2420 | -7400 | +56 / +99 | -3756 | c=1.07: +1422 / -7688 / +52 | 173 | -0.010 | -0.064 | -0.11 / -0.01 / +0.05 | ok |
| La3d84d38 | ADD | L3M | +187 / +328 | -4314 | -528 / -925 | +2483 | c=1.07: +234 / -4602 / -563 | 71 | -0.086 | -0.468 | -0.24 / +0.02 / -0.08 | ok |
| La3d84d38 | ADD | L6M | +213 / +372 | -4314 | -260 / -455 | +2483 | c=1.07: +251 / -4602 / -273 | 171 | -0.026 | -0.167 | -0.13 / -0.01 / +0.04 | ok |
| La3dfec49 | RK7 | L3M | +5512 / +9646 | -8519 | +1006 / +1761 | -17768 | c=0.50: +2491 / -5711 / +870 | 95 | +0.016 | +0.114 | +0.01 / +0.22 / +0.34 | RED |
| La3dfec49 | RK7 | L6M | +3383 / +5920 | -8519 | +571 / +1000 | -17768 | c=0.50: +1514 / -5711 / +542 | 176 | +0.004 | +0.024 | +0.02 / +0.17 / +0.15 | RED |
| La409d9e0 | RK7 | L3M | +1382 / +2419 | -6180 | +1628 / +2848 | -4651 | c=1.23: +1458 / -6894 / +1872 | 106 | +0.133 | +1.085 | -0.02 / -0.09 / +0.05 | ok |
| La409d9e0 | RK7 | L6M | +1021 / +1786 | -6180 | +795 / +1391 | -4651 | c=1.23: +1093 / -6894 / +893 | 223 | +0.053 | +0.437 | -0.09 / -0.03 / -0.15 | ok |
| La56d6cd3 | RK7 | L3M | +3900 / +6825 | -3405 | -852 / -1491 | -10710 | c=0.56: +2541 / -3263 / -246 | 62 | -0.132 | -0.631 | -0.02 / +0.01 / +0.31 | RED |
| La56d6cd3 | RK7 | L6M | +2439 / +4267 | -3405 | +1383 / +2420 | -10710 | c=0.56: +1589 / -3263 / +921 | 150 | +0.087 | +0.481 | -0.02 / +0.02 / +0.09 | RED |
| La872937f | RK7 | L3M | +1651 / +2890 | -5910 | +463 / +811 | -8064 | c=1.00: +1651 / -5910 / +463 | 107 | -0.009 | -0.076 | -0.14 / -0.08 / -0.33 | AMBER |
| La872937f | RK7 | L6M | +1249 / +2185 | -5910 | -71 / -124 | -8064 | c=1.00: +1249 / -5910 / -71 | 243 | -0.054 | -0.484 | -0.04 / -0.04 / -0.04 | AMBER |
| Lad0c27eb | RK7 | L3M | +1782 / +3119 | -7971 | +2358 / +4127 | -5082 | c=0.76: +1641 / -7026 / +1905 | 74 | +0.212 | +1.209 | +0.34 / +0.39 / +0.44 | AMBER |
| Lad0c27eb | RK7 | L6M | +1084 / +1898 | -7971 | +1578 / +2761 | -5082 | c=0.76: +1010 / -7026 / +1281 | 149 | +0.143 | +0.791 | +0.22 / +0.24 / +0.22 | AMBER |
| Lad0c27eb | ADD | L3M | +918 / +1606 | -6587 | +2506 / +4386 | -2405 | c=0.76: +708 / -5642 / +2054 | 73 | +0.215 | +1.207 | +0.34 / +0.39 / +0.44 | ok |
| Lad0c27eb | ADD | L6M | +471 / +824 | -6587 | +1569 / +2747 | -2405 | c=0.76: +349 / -5642 / +1273 | 148 | +0.144 | +0.790 | +0.22 / +0.24 / +0.22 | ok |
| Lae0baee6 | RK7 | L3M | +2242 / +3923 | -6920 | +632 / +1105 | -7811 | c=0.97: +2201 / -6804 / +616 | 91 | +0.061 | +0.430 | +0.09 / +0.01 / +0.10 | AMBER |
| Lae0baee6 | RK7 | L6M | +1809 / +3166 | -7255 | +34 / +60 | -7811 | c=0.97: +1770 / -6922 / +36 | 197 | -0.007 | -0.051 | +0.04 / +0.04 / +0.06 | AMBER |
| Lb11eb5e8 | RK7 | L3M | +2126 / +3720 | -3027 | -697 / -1220 | -4336 | c=0.50: +1515 / -1672 / -332 | 67 | -0.059 | -0.305 | +0.13 / +0.04 / -0.10 | AMBER |
| Lb11eb5e8 | RK7 | L6M | +1432 / +2506 | -3027 | +312 / +546 | -4336 | c=0.50: +987 / -1672 / +279 | 168 | +0.004 | +0.028 | -0.00 / -0.01 / -0.22 | AMBER |
| Lb1b89688 | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=0.50: +1046 / -2320 / +360 | 74 | +0.034 | +0.191 | +0.03 / +0.06 / -0.01 | AMBER |
| Lb1b89688 | RK7 | L6M | +1487 / +2602 | -3945 | +1090 / +1907 | -6714 | c=0.50: +846 / -2320 / +651 | 161 | +0.061 | +0.366 | -0.02 / +0.08 / +0.10 | AMBER |
| Lb1b89688 | ADD | L3M | +594 / +1040 | -2919 | +226 / +396 | -2178 | c=0.50: +118 / -1460 / +90 | 73 | +0.020 | +0.114 | -0.01 / +0.07 / -0.03 | ok |
| Lb1b89688 | ADD | L6M | +562 / +984 | -3356 | +800 / +1400 | -2178 | c=0.50: +148 / -1460 / +389 | 159 | +0.058 | +0.343 | -0.04 / +0.09 / +0.09 | ok |
| Lb1fce0c5 | RK7 | L3M | +2074 / +3629 | -6401 | +1209 / +2115 | -6413 | c=0.50: +1727 / -5202 / +885 | 45 | +0.078 | +0.270 | +0.28 / +0.07 / +0.42 | AMBER |
| Lb1fce0c5 | RK7 | L6M | +1359 / +2379 | -6401 | +1304 / +2282 | -6413 | c=0.50: +1128 / -5202 / +862 | 98 | +0.102 | +0.369 | +0.22 / +0.13 / +0.35 | AMBER |
| Lb292f65c | RK7 | L3M | +1996 / +3493 | -4538 | -314 / -550 | -8221 | c=1.00: +1996 / -4538 / -314 | 137 | -0.030 | -0.317 | -0.08 / +0.01 / -0.10 | AMBER |
| Lb292f65c | RK7 | L6M | +1353 / +2368 | -4538 | +651 / +1139 | -8221 | c=1.00: +1353 / -4538 / +651 | 282 | +0.042 | +0.435 | -0.10 / +0.03 / -0.10 | AMBER |
| Lb292f65c | ADD | L3M | +1678 / +2937 | -4571 | -1067 / -1868 | -7943 | c=1.00: +1678 / -4571 / -1067 | 136 | -0.031 | -0.326 | -0.08 / +0.01 / -0.10 | AMBER |
| Lb292f65c | ADD | L6M | +1082 / +1893 | -4571 | +30 / +52 | -7943 | c=1.00: +1082 / -4571 / +30 | 281 | +0.041 | +0.430 | -0.10 / +0.03 / -0.10 | AMBER |
| Lb32dea9b | RK7 | L3M | +1220 / +2135 | -3920 | +1430 / +2502 | -4825 | c=0.50: +804 / -2390 / +733 | 72 | +0.105 | +0.581 | +0.20 / -0.03 / +0.22 | AMBER |
| Lb32dea9b | RK7 | L6M | +1064 / +1862 | -3920 | +1207 / +2112 | -4825 | c=0.50: +688 / -2390 / +681 | 167 | +0.071 | +0.438 | +0.13 / -0.01 / +0.25 | AMBER |
| Lb36e86fe | RK7 | L3M | +1782 / +3119 | -7971 | +2358 / +4127 | -5082 | c=0.76: +1641 / -7026 / +1905 | 74 | +0.212 | +1.209 | +0.34 / +0.39 / +0.44 | AMBER |
| Lb36e86fe | RK7 | L6M | +1084 / +1898 | -7971 | +1578 / +2761 | -5082 | c=0.76: +1010 / -7026 / +1281 | 149 | +0.143 | +0.791 | +0.22 / +0.24 / +0.22 | AMBER |
| Lb36e86fe | ADD | L3M | +918 / +1606 | -6587 | +2506 / +4386 | -2405 | c=0.76: +708 / -5642 / +2054 | 73 | +0.215 | +1.207 | +0.34 / +0.39 / +0.44 | ok |
| Lb36e86fe | ADD | L6M | +471 / +824 | -6587 | +1569 / +2747 | -2405 | c=0.76: +349 / -5642 / +1273 | 148 | +0.144 | +0.790 | +0.22 / +0.24 / +0.22 | ok |
| Lb38b06ff | RK7 | L3M | +2411 / +4219 | -925 | +23 / +40 | -8206 | c=0.50: +1756 / -893 / -196 | 60 | +0.039 | +0.182 | -0.02 / +0.17 / +0.03 | AMBER |
| Lb38b06ff | RK7 | L6M | +1666 / +2916 | -1685 | +478 / +837 | -8206 | c=0.50: +1203 / -893 / +155 | 142 | +0.051 | +0.270 | +0.01 / +0.15 / +0.10 | AMBER |
| Lb44a3e99 | RK7 | L3M | +1583 / +2769 | -3333 | +1307 / +2288 | -5791 | c=1.00: +1583 / -3333 / +1307 | 106 | +0.132 | +1.072 | +0.18 / +0.21 / +0.30 | AMBER |
| Lb44a3e99 | RK7 | L6M | +1113 / +1947 | -3333 | +1878 / +3286 | -5791 | c=1.00: +1113 / -3333 / +1878 | 212 | +0.177 | +1.391 | +0.13 / +0.09 / +0.20 | AMBER |
| Lb44a3e99 | ADD | L3M | +1597 / +2794 | -4060 | +863 / +1510 | -6723 | c=1.00: +1597 / -4060 / +863 | 106 | +0.132 | +1.072 | +0.18 / +0.21 / +0.30 | AMBER |
| Lb44a3e99 | ADD | L6M | +981 / +1716 | -4060 | +1454 / +2544 | -6723 | c=1.00: +981 / -4060 / +1454 | 211 | +0.173 | +1.354 | +0.12 / +0.09 / +0.20 | AMBER |
| Lb66c583e | RK7 | L3M | -446 / -781 | -3000 | +2312 / +4046 | +2276 | c=0.53: +313 / -3040 / +1540 | 63 | +0.152 | +0.735 | +0.18 / -0.23 / +0.00 | ok |
| Lb66c583e | RK7 | L6M | +126 / +221 | -3780 | +2222 / +3889 | +1857 | c=0.53: +407 / -3040 / +1327 | 135 | +0.170 | +0.852 | +0.08 / -0.13 / +0.04 | ok |
| Lb9026469 | RK7 | L3M | +1615 / +2826 | -4185 | -963 / -1686 | -6390 | c=0.62: +1164 / -2906 / -437 | 61 | -0.150 | -0.702 | +0.03 / +0.12 / -0.09 | AMBER |
| Lb9026469 | RK7 | L6M | +1351 / +2363 | -4185 | -760 / -1330 | -6390 | c=0.62: +931 / -2906 / -310 | 144 | -0.112 | -0.600 | +0.04 / +0.04 / -0.11 | AMBER |
| Lb9a5006e | RK7 | L3M | +3405 / +5958 | -9590 | +321 / +562 | -11497 | c=0.76: +2861 / -8041 / +343 | 69 | -0.011 | -0.057 | -0.20 / -0.09 / -0.03 | RED |
| Lba34ae9f | RK7 | L3M | +2516 / +4403 | -7675 | -108 / -189 | -8685 | c=0.86: +2301 / -7055 / -153 | 84 | +0.037 | +0.241 | +0.09 / -0.05 / +0.03 | AMBER |
| Lba34ae9f | RK7 | L6M | +1905 / +3333 | -7675 | +39 / +69 | -8685 | c=0.86: +1725 / -7055 / +33 | 185 | +0.005 | +0.031 | +0.06 / +0.04 / +0.19 | AMBER |
| Lba6f7f20 | RK7 | L3M | +3281 / +5742 | -6615 | +1025 / +1793 | -12433 | c=0.50: +1897 / -4851 / +948 | 75 | +0.011 | +0.064 | -0.07 / +0.11 / +0.16 | RED |
| Lbb064943 | RK7 | L3M | +3105 / +5433 | -5085 | +1077 / +1884 | -8412 | c=0.50: +1587 / -4085 / +997 | 71 | +0.012 | +0.067 | +0.21 / +0.27 / +0.41 | AMBER |
| Lbb064943 | RK7 | L6M | +2022 / +3538 | -5085 | +1432 / +2506 | -8412 | c=0.50: +1056 / -4085 / +977 | 150 | +0.068 | +0.379 | +0.17 / +0.23 / +0.31 | AMBER |
| Lbbb39855 | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=0.50: +290 / -3103 / +1882 | 62 | +0.178 | +0.849 | +0.25 / -0.07 / +0.11 | ok |
| Lbbb39855 | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=0.50: +318 / -3103 / +1302 | 136 | +0.164 | +0.825 | +0.06 / -0.03 / +0.02 | ok |
| Lbbb39855 | RK7 | Y2023 | -1698 / -2972 | -7720 | -122 / -213 | -4200 | c=0.50: +353 / -6846 / -391 | 182 | +0.048 | +0.224 | +0.07 / +0.04 / +0.23 | ok |
| Lbbb39855 | RK7 | Y2024 | -1956 / -3423 | -882 | +670 / +1172 | +8949 | c=0.50: -2028 / +45 / +298 | 256 | +0.064 | +0.310 | -0.01 / +0.02 / +0.14 | ok |
| Lbbb39855 | RK7 | Y2025 | -5837 / -10214 | +6385 | -137 / -239 | +13807 | c=0.50: -2058 / +4287 / -449 | 269 | +0.051 | +0.260 | +0.00 / -0.01 / +0.02 | ok |
| Lbbb39855 | RM7 | L3M | -1391 / -2434 | -100 | +1273 / +2228 | +6039 | c=0.50: -750 / -148 / +249 | 63 | +0.176 | +0.853 | +0.26 / -0.07 / +0.11 | ok |
| Lbbb39855 | RM7 | L6M | -799 / -1397 | -100 | +1497 / +2620 | +6039 | c=0.50: -527 / -148 / +517 | 136 | +0.162 | +0.817 | +0.07 / -0.03 / +0.02 | ok |
| Lbbb39855 | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=0.50: -916 / +48 / +1143 | 62 | +0.163 | +0.777 | +0.23 / -0.07 / +0.10 | ok |
| Lbbb39855 | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=0.50: -500 / +48 / +755 | 135 | +0.156 | +0.780 | +0.05 / -0.03 / +0.01 | ok |
| Lbf7b6788 | RK7 | L3M | +1444 / +2527 | -5290 | +1302 / +2278 | -5463 | c=1.00: +1444 / -5290 / +1302 | 111 | +0.044 | +0.378 | +0.12 / +0.02 / +0.25 | AMBER |
| Lbf7b6788 | RK7 | L6M | +1021 / +1787 | -5290 | +1104 / +1931 | -5463 | c=1.00: +1021 / -5290 / +1104 | 240 | +0.055 | +0.491 | +0.11 / +0.00 / +0.17 | AMBER |
| Lc018cf47 | RK7 | L3M | +1179 / +2063 | -3030 | +1916 / +3353 | -2654 | c=0.50: +681 / -1945 / +1360 | 75 | +0.080 | +0.463 | +0.13 / +0.11 / +0.37 | ok |
| Lc34e9ecb | RK7 | L3M | +1461 / +2557 | -2202 | +713 / +1248 | -2182 | c=1.00: +1461 / -2202 / +713 | 198 | +0.005 | +0.076 | -0.02 / +0.03 / -0.04 | ok |
| Lc573e500 | ADD | L3M | +502 / +878 | -5236 | +1876 / +3283 | +1947 | c=1.00: +502 / -5236 / +1876 | 168 | +0.090 | +1.163 | -0.03 / +0.11 / +0.10 | ok |
| Lc573e500 | ADD | L6M | +417 / +730 | -5236 | +359 / +628 | +1947 | c=1.00: +417 / -5236 / +359 | 359 | +0.002 | +0.028 | +0.01 / +0.06 / -0.03 | ok |
| Lc60d142a | RK7 | L3M | +416 / +728 | -3580 | +791 / +1384 | -130 | c=0.59: +447 / -2472 / +713 | 69 | +0.018 | +0.094 | +0.10 / -0.04 / +0.04 | ok |
| Lc60d142a | RK7 | L6M | +358 / +627 | -3580 | +1374 / +2404 | -130 | c=0.59: +379 / -2472 / +1018 | 164 | +0.071 | +0.432 | +0.06 / +0.03 / +0.11 | ok |
| Lc9217645 | RK7 | L3M | +1565 / +2739 | -6870 | +2049 / +3585 | -4582 | c=0.51: +1353 / -5010 / +1347 | 55 | +0.143 | +0.605 | +0.26 / -0.06 / +0.28 | ok |
| Lc9217645 | RK7 | L6M | +1229 / +2150 | -6870 | +1999 / +3498 | -4582 | c=0.51: +983 / -5010 / +1130 | 130 | +0.156 | +0.749 | +0.03 / -0.04 / +0.13 | ok |
| Lc92c02b0 | RK7 | L3M | +1511 / +2644 | -5675 | +1205 / +2109 | -7539 | c=1.00: +1511 / -5675 / +1205 | 91 | +0.091 | +0.638 | -0.05 / -0.15 / -0.37 | AMBER |
| Lc92c02b0 | RK7 | L6M | +1198 / +2096 | -5675 | +422 / +739 | -7539 | c=1.00: +1198 / -5675 / +422 | 204 | -0.000 | -0.002 | -0.01 / -0.04 / -0.02 | AMBER |
| Lcad54215 | RK7 | L3M | +148 / +260 | -3080 | +1607 / +2812 | +996 | c=0.50: +751 / -3083 / +1026 | 61 | +0.103 | +0.484 | +0.16 / -0.15 / +0.05 | ok |
| Lcad54215 | RK7 | L6M | +409 / +715 | -3815 | +2335 / +4087 | +996 | c=0.50: +627 / -3083 / +1241 | 132 | +0.187 | +0.912 | +0.01 / -0.07 / +0.03 | ok |
| Lcae9533f | RK7 | L3M | -32 / -56 | -3080 | +1504 / +2632 | +1286 | c=0.50: +547 / -3083 / +1184 | 64 | +0.054 | +0.267 | -0.01 / -0.27 / -0.04 | ok |
| Lcae9533f | RK7 | L6M | +448 / +783 | -6180 | +1968 / +3444 | +1286 | c=0.50: +562 / -3083 / +1185 | 137 | +0.129 | +0.652 | -0.03 / -0.14 / -0.01 | ok |
| Lcb3c99eb | ADD | L3M | +4051 / +7090 | -8375 | -783 / -1371 | -13244 | c=0.53: +1817 / -5603 / -400 | 91 | -0.052 | -0.365 | -0.04 / +0.25 / +0.16 | RED |
| Lcb3c99eb | ADD | L6M | +2462 / +4309 | -8375 | +64 / +111 | -13244 | c=0.53: +1054 / -5603 / -7 | 213 | +0.008 | +0.067 | +0.07 / +0.19 / +0.17 | RED |
| Lcb97bb95 | RK7 | L3M | +554 / +969 | -3130 | +2238 / +3916 | -2449 | c=0.59: +788 / -3112 / +1655 | 63 | +0.146 | +0.707 | +0.19 / -0.09 / +0.13 | ok |
| Lcb97bb95 | RK7 | L6M | +397 / +695 | -3130 | +2143 / +3751 | -2449 | c=0.59: +552 / -3112 / +1429 | 134 | +0.175 | +0.866 | +0.10 / -0.07 / +0.13 | ok |
| Lcb97bb95 | ADD | L3M | -671 / -1175 | +40 | +1609 / +2815 | +1841 | c=0.59: -491 / +24 / +985 | 63 | +0.156 | +0.756 | +0.21 / -0.09 / +0.14 | ok |
| Lcb97bb95 | ADD | L6M | -446 / -781 | +40 | +1630 / +2852 | +1841 | c=0.59: -328 / +24 / +905 | 133 | +0.178 | +0.878 | +0.11 / -0.07 / +0.13 | ok |
| Lcb97bb95 | ADD | Y2023 | +1217 / +2129 | -2818 | -110 / -193 | -2319 | c=0.59: +664 / -1332 / -77 | 238 | -0.007 | -0.040 | +0.09 / +0.03 / +0.22 | ok |
| Lcb97bb95 | ADD | Y2024 | +3325 / +5819 | -2390 | +2 / +4 | +686 | c=0.59: +1695 / -1416 / -7 | 299 | +0.002 | +0.012 | -0.05 / -0.01 / +0.14 | ok |
| Lcb97bb95 | ADD | Y2025 | -4962 / -8684 | +343 | +1180 / +2065 | +4259 | c=0.59: -2915 / +1699 / +658 | 283 | +0.119 | +0.633 | +0.03 / -0.00 / +0.03 | ok |
| Lcbda2ba7 | RK7 | L3M | +717 / +1255 | -314 | +2772 / +4851 | -2862 | c=1.00: +717 / -314 / +2772 | 139 | +0.150 | +1.608 | +0.06 / +0.06 / +0.02 | ok |
| Lcbda2ba7 | RK7 | L6M | +548 / +959 | -314 | +1604 / +2808 | -2862 | c=1.00: +548 / -314 / +1604 | 307 | +0.067 | +0.767 | +0.13 / +0.04 / +0.12 | ok |
| Lcbda2ba7 | ADD | L3M | +120 / +210 | +1281 | +2701 / +4727 | -1375 | c=1.00: +120 / +1281 / +2701 | 138 | +0.159 | +1.684 | +0.07 / +0.04 / +0.02 | ok |
| Lcbda2ba7 | ADD | L6M | +101 / +177 | +1281 | +1508 / +2639 | -1375 | c=1.00: +101 / +1281 / +1508 | 306 | +0.071 | +0.804 | +0.13 / +0.03 / +0.11 | ok |
| Lcced15b8 | RK7 | L3M | +3096 / +5418 | -8795 | +1163 / +2035 | -9101 | c=1.20: +3530 / -9937 / +1220 | 75 | +0.050 | +0.286 | +0.03 / +0.04 / +0.35 | AMBER |
| Lcced15b8 | RK7 | L6M | +1970 / +3448 | -8795 | +1622 / +2838 | -9101 | c=1.20: +2250 / -9937 / +1840 | 158 | +0.187 | +1.094 | -0.03 / +0.01 / +0.14 | AMBER |
| Lcced15b8 | ADD | L3M | +1436 / +2513 | -6366 | +80 / +140 | -3700 | c=1.20: +1889 / -7553 / +99 | 74 | +0.017 | +0.095 | -0.02 / +0.04 / +0.33 | ok |
| Lcced15b8 | ADD | L6M | +830 / +1452 | -6366 | +984 / +1722 | -3700 | c=1.20: +1115 / -7553 / +1196 | 156 | +0.184 | +1.062 | -0.06 / +0.01 / +0.13 | ok |
| Lcd368087 | RK7 | L3M | +3804 / +6657 | -7194 | +555 / +972 | -12323 | c=0.50: +2507 / -5049 / +341 | 69 | +0.034 | +0.179 | +0.12 / +0.33 / +0.38 | RED |
| Lcd368087 | RK7 | L6M | +2450 / +4287 | -7194 | +844 / +1477 | -12323 | c=0.50: +1617 / -5049 / +565 | 139 | +0.045 | +0.232 | +0.06 / +0.17 / +0.34 | RED |
| Lcd368087 | ADD | L3M | +3229 / +5652 | -7920 | +113 / +198 | -10820 | c=0.50: +1675 / -5776 / -102 | 69 | +0.034 | +0.179 | +0.12 / +0.33 / +0.38 | RED |
| Lcd368087 | ADD | L6M | +1977 / +3460 | -7920 | +507 / +888 | -10820 | c=0.50: +986 / -5776 / +227 | 138 | +0.046 | +0.233 | +0.06 / +0.17 / +0.34 | RED |
| Lce1c241f | RK7 | L3M | +1471 / +2574 | -5090 | +859 / +1504 | -7184 | c=1.23: +1537 / -5553 / +885 | 74 | +0.020 | +0.112 | -0.16 / +0.05 / -0.23 | AMBER |
| Lce1c241f | RK7 | L6M | +1238 / +2167 | -5090 | -149 / -262 | -7184 | c=1.23: +1396 / -5553 / -334 | 170 | -0.130 | -0.819 | -0.08 / +0.03 / -0.04 | AMBER |
| Lcfeda8c4 | RK7 | L3M | -215 / -376 | -3000 | +1586 / +2775 | +2131 | c=0.50: +484 / -3043 / +1099 | 65 | +0.081 | +0.406 | +0.17 / -0.16 / +0.04 | ok |
| Lcfeda8c4 | RK7 | L6M | +234 / +410 | -3850 | +1570 / +2747 | +1857 | c=0.50: +486 / -3043 / +894 | 142 | +0.107 | +0.563 | +0.08 / -0.06 / +0.08 | ok |
| Lcfeda8c4 | ADD | L3M | -1067 / -1868 | +195 | +621 / +1087 | +6421 | c=0.50: -529 / +98 / +222 | 65 | +0.067 | +0.333 | +0.14 / -0.16 / +0.02 | ok |
| Lcfeda8c4 | ADD | L6M | -353 / -618 | -3261 | +882 / +1543 | +5375 | c=0.50: -215 / +98 / +263 | 141 | +0.099 | +0.516 | +0.07 / -0.06 / +0.07 | ok |
| Ld0d0d2e9 | RK7 | L3M | +4560 / +7979 | -10080 | +660 / +1155 | -14384 | c=0.50: +2958 / -6583 / +530 | 74 | +0.019 | +0.108 | +0.09 / +0.08 / +0.25 | RED |
| Ld0d0d2e9 | RK7 | L6M | +2949 / +5161 | -10080 | +1489 / +2606 | -14384 | c=0.50: +1912 / -6583 / +888 | 158 | +0.086 | +0.501 | +0.03 / +0.04 / +0.12 | RED |
| Ld2610290 | RK7 | L3M | +1920 / +3360 | -2722 | +3391 / +5934 | -6010 | c=0.50: +1312 / -1520 / +2146 | 90 | +0.150 | +1.038 | -0.20 / +0.26 / +0.12 | AMBER |
| Ld2610290 | RK7 | L6M | +1418 / +2482 | -2722 | +2392 / +4186 | -6010 | c=0.50: +947 / -1520 / +1537 | 212 | +0.091 | +0.713 | -0.14 / +0.07 / -0.07 | AMBER |
| Ld2610290 | ADD | L3M | +1111 / +1945 | +728 | +3379 / +5913 | -3137 | c=0.50: -6 / +1653 / +2042 | 89 | +0.163 | +1.114 | -0.17 / +0.26 / +0.13 | ok |
| Ld2610290 | ADD | L6M | +847 / +1483 | +728 | +1995 / +3491 | -3137 | c=0.50: +62 / +1653 / +1095 | 211 | +0.096 | +0.750 | -0.13 / +0.07 / -0.06 | ok |
| Ld40c5e85 | RK7 | L3M | +2350 / +4113 | -7760 | +782 / +1369 | -10094 | c=0.50: +1847 / -5423 / +653 | 55 | +0.025 | +0.108 | -0.07 / -0.03 / -0.13 | RED |
| Ld40c5e85 | RK7 | L6M | +1880 / +3290 | -7760 | -192 / -335 | -10094 | c=0.50: +1347 / -5423 / +138 | 122 | -0.061 | -0.274 | +0.03 / -0.01 / +0.09 | RED |
| Ld45733db | RK7 | L3M | +184 / +322 | -3120 | +2867 / +5018 | -217 | c=0.50: +624 / -3103 / +1714 | 78 | +0.160 | +0.961 | +0.06 / +0.01 / +0.27 | ok |
| Ld45733db | RK7 | L6M | +194 / +339 | -3120 | +2845 / +4979 | -217 | c=0.50: +433 / -3103 / +1666 | 191 | +0.139 | +0.983 | +0.03 / +0.06 / +0.27 | ok |
| Ld58e1252 | RK7 | L3M | +2478 / +4337 | -2540 | +1192 / +2086 | -7824 | c=0.50: +1543 / -1700 / +913 | 75 | +0.040 | +0.232 | -0.23 / +0.29 / +0.16 | AMBER |
| Ld58e1252 | RK7 | L6M | +1780 / +3116 | -2540 | +936 / +1638 | -7824 | c=0.50: +1106 / -1700 / +734 | 169 | +0.027 | +0.168 | -0.21 / +0.13 / +0.01 | AMBER |
| Ld5ed5686 | RK7 | L3M | +2835 / +4962 | -5587 | +1641 / +2872 | -8303 | c=0.50: +2059 / -3352 / +895 | 84 | +0.096 | +0.622 | +0.03 / -0.04 / -0.01 | AMBER |
| Ld5ed5686 | RK7 | L6M | +2104 / +3682 | -5587 | +658 / +1151 | -8303 | c=0.50: +1469 / -3352 / +464 | 188 | +0.023 | +0.161 | +0.03 / +0.02 / +0.00 | AMBER |
| Ld6f467f5 | RK7 | L3M | +3670 / +6423 | -7875 | -1531 / -2679 | -13035 | c=0.84: +3242 / -7119 / -1266 | 76 | -0.202 | -1.178 | -0.05 / +0.05 / -0.16 | RED |
| Ld6f467f5 | RK7 | L6M | +2576 / +4507 | -7875 | -1030 / -1802 | -13035 | c=0.84: +2249 / -7119 / -825 | 174 | -0.141 | -0.911 | +0.01 / -0.03 / -0.15 | RED |
| Ld8794cda | RK7 | L3M | +2757 / +4825 | -4922 | +632 / +1106 | -7492 | c=1.14: +2980 / -5580 / +602 | 72 | -0.035 | -0.195 | -0.19 / -0.09 / +0.11 | AMBER |
| Ld8794cda | RK7 | L6M | +1868 / +3269 | -4922 | +1669 / +2921 | -7492 | c=1.14: +2028 / -5580 / +1807 | 153 | +0.163 | +0.921 | -0.12 / -0.07 / +0.12 | AMBER |
| Ld8d9f7cd | RK7 | L3M | +1851 / +3240 | -3495 | +1140 / +1994 | -5845 | c=1.00: +1851 / -3495 / +1140 | 184 | +0.073 | +1.036 | +0.12 / +0.24 / +0.15 | AMBER |
| Ld8d9f7cd | RK7 | L6M | +1312 / +2296 | -3495 | +1261 / +2206 | -5845 | c=1.00: +1312 / -3495 / +1261 | 450 | +0.060 | +1.007 | +0.14 / +0.14 / +0.15 | AMBER |
| Ld8d9f7cd | ADD | L3M | +476 / +832 | +616 | +1242 / +2173 | -843 | c=1.00: +476 / +616 / +1242 | 188 | +0.082 | +1.185 | +0.16 / +0.23 / +0.15 | ok |
| Ld8d9f7cd | ADD | L6M | +381 / +666 | -2530 | +1210 / +2117 | -843 | c=1.00: +381 / -2530 / +1210 | 453 | +0.063 | +1.054 | +0.16 / +0.14 / +0.15 | ok |
| Ldd0b0840 | RK7 | L3M | +1067 / +1867 | -5684 | +1426 / +2495 | -1359 | c=1.00: +1067 / -5684 / +1426 | 113 | +0.062 | +0.543 | +0.41 / +0.14 / +0.44 | ok |
| Ldd0b0840 | RK7 | L6M | +716 / +1253 | -5684 | +1544 / +2703 | -1359 | c=1.00: +716 / -5684 / +1544 | 227 | +0.104 | +0.873 | +0.32 / +0.15 / +0.29 | ok |
| Lde06bb47 | RK7 | L3M | +432 / +755 | -2233 | +651 / +1139 | -589 | c=1.00: +432 / -2233 / +651 | 110 | +0.067 | +0.569 | +0.23 / +0.01 / +0.20 | ok |
| Lde06bb47 | RK7 | L6M | +398 / +697 | -2233 | +973 / +1703 | -589 | c=1.00: +398 / -2233 / +973 | 218 | +0.080 | +0.644 | +0.17 / +0.02 / +0.22 | ok |
| Lde06bb47 | ADD | L3M | -1053 / -1843 | +247 | +464 / +812 | +4764 | c=1.00: -1053 / +247 / +464 | 109 | +0.059 | +0.493 | +0.21 / +0.01 / +0.19 | ok |
| Lde06bb47 | ADD | L6M | -625 / -1093 | +247 | +785 / +1374 | +4764 | c=1.00: -625 / +247 / +785 | 216 | +0.080 | +0.644 | +0.16 / +0.02 / +0.20 | ok |
| Lde06bb47 | ADD | Y2023 | +2905 / +5083 | -237 | +416 / +728 | -7244 | c=1.00: +2905 / -237 / +416 | 240 | +0.050 | +0.308 | +0.15 / -0.04 / +0.08 | AMBER |
| Lde06bb47 | ADD | Y2024 | -1454 / -2545 | +2285 | +330 / +578 | +1450 | c=1.00: -1454 / +2285 / +330 | 365 | +0.038 | +0.261 | +0.17 / +0.05 / +0.18 | ok |
| Lde06bb47 | ADD | Y2025 | -4721 / -8262 | +4055 | +654 / +1145 | +13780 | c=1.00: -4721 / +4055 / +654 | 402 | +0.080 | +0.608 | +0.13 / -0.04 / +0.03 | ok |
| Ldeb7c937 | RK7 | L3M | -207 / -363 | -3000 | +1055 / +1847 | +2131 | c=0.50: +484 / -3043 / +899 | 64 | +0.026 | +0.130 | +0.19 / -0.14 / +0.06 | ok |
| Ldeb7c937 | RK7 | L6M | +239 / +417 | -3850 | +1314 / +2300 | +1857 | c=0.50: +486 / -3043 / +798 | 141 | +0.082 | +0.430 | +0.10 / -0.05 / +0.09 | ok |
| Le0d40091 | RK7 | L3M | +1816 / +3178 | -3130 | +833 / +1458 | -7162 | c=0.50: +1431 / -3108 / +780 | 61 | +0.009 | +0.044 | -0.02 / -0.07 / +0.17 | AMBER |
| Le0d40091 | RK7 | L6M | +1210 / +2118 | -3130 | +2380 / +4165 | -7162 | c=0.50: +963 / -3108 / +1412 | 142 | +0.153 | +0.807 | +0.01 / -0.01 / +0.17 | AMBER |
| Le2688065 | ADD | L3M | +5100 / +8925 | -7995 | -34 / -59 | -15319 | c=0.50: +2086 / -5215 / +93 | 86 | -0.016 | -0.106 | +0.18 / +0.31 / +0.45 | RED |
| Le2688065 | ADD | L6M | +3055 / +5346 | -7995 | +486 / +851 | -15319 | c=0.50: +1173 / -5215 / +311 | 190 | +0.021 | +0.146 | +0.13 / +0.22 / +0.25 | RED |
| Le5ab3dac | RK7 | L3M | +2516 / +4403 | -7675 | -108 / -189 | -8685 | c=0.86: +2301 / -7055 / -153 | 84 | +0.037 | +0.241 | +0.09 / -0.05 / +0.03 | AMBER |
| Le5ab3dac | RK7 | L6M | +1905 / +3333 | -7675 | +39 / +69 | -8685 | c=0.86: +1725 / -7055 / +33 | 185 | +0.005 | +0.031 | +0.06 / +0.04 / +0.19 | AMBER |
| Le64f10da | RK7 | L3M | +1366 / +2391 | -4110 | +1411 / +2468 | -2433 | c=1.00: +1366 / -4110 / +1411 | 137 | +0.042 | +0.445 | +0.13 / -0.02 / +0.23 | ok |
| Le64f10da | RK7 | L6M | +966 / +1691 | -4110 | +1280 / +2240 | -2433 | c=1.00: +966 / -4110 / +1280 | 268 | +0.064 | +0.636 | +0.07 / +0.01 / +0.21 | ok |
| Le6ade82a | RK7 | L3M | +715 / +1252 | -3935 | +1493 / +2614 | -2270 | c=0.53: +568 / -2500 / +843 | 69 | +0.117 | +0.620 | +0.11 / +0.02 / +0.02 | ok |
| Le6ade82a | RK7 | L6M | +811 / +1420 | -3935 | +1630 / +2852 | -2270 | c=0.53: +573 / -2500 / +956 | 168 | +0.103 | +0.642 | +0.07 / +0.01 / +0.19 | ok |
| Le788e239 | RK7 | L3M | +3736 / +6538 | -7195 | -521 / -911 | -13220 | c=0.50: +2506 / -5140 / -407 | 69 | -0.018 | -0.095 | -0.01 / +0.08 / +0.21 | RED |
| Le788e239 | RK7 | L6M | +2448 / +4284 | -7195 | -451 / -789 | -13220 | c=0.50: +1647 / -5140 / -237 | 158 | -0.030 | -0.178 | +0.03 / +0.05 / +0.33 | RED |
| Le8a49956 | RK7 | L3M | +4487 / +7852 | -3585 | -1043 / -1826 | -13705 | c=0.50: +2086 / -3336 / -99 | 59 | -0.173 | -0.787 | -0.16 / +0.05 / +0.11 | RED |
| Le8a49956 | RK7 | L6M | +2812 / +4921 | -3585 | +201 / +352 | -13705 | c=0.50: +1326 / -3336 / +353 | 142 | -0.024 | -0.127 | -0.05 / +0.03 / +0.07 | RED |
| Le8cad847 | RK7 | L3M | +203 / +355 | -3665 | +1388 / +2430 | +889 | c=0.57: +337 / -2463 / +857 | 71 | +0.108 | +0.591 | +0.41 / +0.17 / +0.38 | ok |
| Le8cad847 | RK7 | L6M | +469 / +821 | -3665 | +1356 / +2372 | +889 | c=0.57: +422 / -2463 / +902 | 163 | +0.083 | +0.504 | +0.12 / +0.11 / +0.24 | ok |
| Lea3ea462 | RK7 | L3M | +1790 / +3133 | -5825 | +1045 / +1829 | -8965 | c=0.59: +1586 / -4709 / +932 | 59 | +0.030 | +0.138 | -0.08 / -0.03 / -0.13 | AMBER |
| Lea3ea462 | RK7 | L6M | +1557 / +2724 | -5825 | -188 / -329 | -8965 | c=0.59: +1228 / -4709 / +126 | 131 | -0.078 | -0.381 | +0.01 / -0.02 / +0.05 | AMBER |
| Led8baed4 | RK7 | L3M | +1430 / +2502 | -2808 | +1195 / +2091 | -1849 | c=0.50: +1194 / -2186 / +792 | 83 | +0.053 | +0.336 | +0.02 / +0.23 / +0.19 | ok |
| Led8baed4 | RK7 | L6M | +859 / +1504 | -2808 | +2164 / +3786 | -1849 | c=0.50: +734 / -2186 / +1271 | 195 | +0.103 | +0.744 | +0.05 / +0.17 / +0.05 | ok |
| Led8baed4 | ADD | L3M | +214 / +375 | -1244 | +2020 / +3535 | +736 | c=0.50: +108 / -622 / +1484 | 81 | +0.072 | +0.447 | -0.01 / +0.20 / +0.15 | ok |
| Led8baed4 | ADD | L6M | +32 / +57 | -1244 | +2476 / +4332 | +736 | c=0.50: -34 / -622 / +1517 | 192 | +0.112 | +0.799 | +0.04 / +0.15 / +0.03 | ok |
| Lee115285 | RK7 | L3M | -446 / -781 | -3000 | +2312 / +4046 | +2276 | c=0.53: +313 / -3040 / +1540 | 63 | +0.152 | +0.735 | +0.18 / -0.23 / +0.00 | ok |
| Lee115285 | RK7 | L6M | +126 / +221 | -3780 | +2222 / +3889 | +1857 | c=0.53: +407 / -3040 / +1327 | 135 | +0.170 | +0.852 | +0.08 / -0.13 / +0.04 | ok |
| Lee46749a | RK7 | L3M | +2832 / +4955 | -12503 | +2293 / +4012 | -7867 | c=0.50: +1851 / -7704 / +1646 | 121 | +0.058 | +0.539 | +0.26 / +0.19 / +0.13 | AMBER |
| Lee46749a | RK7 | L6M | +1659 / +2903 | -12503 | +1994 / +3489 | -7867 | c=0.50: +1106 / -7704 / +1318 | 292 | +0.052 | +0.563 | +0.11 / +0.10 / -0.04 | AMBER |
| Lee8faff6 | RK7 | L3M | -283 / -496 | +3268 | -335 / -586 | +2124 | c=1.00: -283 / +3268 / -335 | 132 | -0.018 | -0.180 | +0.45 / +0.20 / +0.39 | ok |
| Lee8faff6 | RK7 | L6M | -93 / -163 | +3240 | +284 / +497 | +2124 | c=1.00: -93 / +3240 / +284 | 254 | +0.012 | +0.113 | +0.31 / +0.11 / +0.26 | ok |
| Lee8faff6 | ADD | L3M | -910 / -1593 | +5096 | -195 / -341 | +3581 | c=1.00: -910 / +5096 / -195 | 131 | -0.017 | -0.176 | +0.44 / +0.20 / +0.39 | ok |
| Lee8faff6 | ADD | L6M | -587 / -1028 | +3829 | +235 / +412 | +3581 | c=1.00: -587 / +3829 / +235 | 253 | +0.012 | +0.115 | +0.31 / +0.10 / +0.26 | ok |
| Lf0447f1d | RK7 | L3M | +1972 / +3452 | -3233 | +1918 / +3357 | -4963 | c=0.50: +933 / -2398 / +1523 | 72 | +0.059 | +0.329 | +0.06 / +0.26 / +0.32 | AMBER |
| Lf0447f1d | RK7 | L6M | +1297 / +2269 | -3233 | +591 / +1034 | -4963 | c=0.50: +641 / -2398 / +620 | 169 | -0.004 | -0.025 | +0.16 / +0.20 / +0.26 | AMBER |
| Lf0447f1d | ADD | L3M | +1599 / +2799 | -1669 | +1780 / +3115 | -3835 | c=0.50: +113 / -835 / +1443 | 71 | +0.051 | +0.281 | +0.04 / +0.26 / +0.31 | ok |
| Lf0447f1d | ADD | L6M | +965 / +1689 | -1669 | +407 / +713 | -3835 | c=0.50: +35 / -835 / +465 | 168 | -0.008 | -0.048 | +0.15 / +0.21 / +0.26 | ok |
| Lf120aee0 | RK7 | L3M | +719 / +1258 | -1560 | +2011 / +3519 | -294 | c=0.62: +515 / -1291 / +1529 | 96 | +0.087 | +0.643 | +0.10 / +0.07 / +0.05 | ok |
| Lf120aee0 | RK7 | L6M | +577 / +1010 | -1560 | +648 / +1135 | -294 | c=0.62: +421 / -1291 / +650 | 194 | -0.000 | -0.002 | +0.16 / +0.04 / +0.08 | ok |
| Lf1339997 | ADD | L3M | -330 / -577 | -1560 | -565 / -988 | +2086 | c=0.50: -341 / -780 / -95 | 63 | -0.081 | -0.391 | +0.21 / +0.10 / +0.16 | ok |
| Lf1339997 | ADD | L6M | +11 / +20 | -1560 | -35 / -61 | +2086 | c=0.50: -193 / -780 / +11 | 156 | -0.007 | -0.038 | +0.27 / +0.07 / +0.02 | ok |
| Lf24a84da | RK7 | L3M | +2139 / +3744 | -4740 | -1343 / -2350 | -7186 | c=0.62: +1755 / -4117 / -781 | 60 | -0.168 | -0.775 | +0.01 / +0.02 / -0.17 | AMBER |
| Lf24a84da | RK7 | L6M | +1379 / +2412 | -4740 | -835 / -1462 | -7186 | c=0.62: +1150 / -4117 / -424 | 135 | -0.113 | -0.567 | +0.06 / -0.01 / -0.04 | AMBER |
| Lf2905267 | RK7 | L3M | +3766 / +6591 | -6054 | +908 / +1590 | -13173 | c=0.50: +2332 / -4479 / +720 | 90 | +0.023 | +0.157 | -0.09 / +0.43 / +0.16 | RED |
| Lf2905267 | RK7 | L6M | +2534 / +4435 | -6054 | +1482 / +2593 | -13173 | c=0.50: +1563 / -4479 / +935 | 210 | +0.059 | +0.455 | -0.05 / +0.23 / +0.05 | RED |
| Lf2905267 | ADD | L3M | +2834 / +4959 | -5585 | +1087 / +1902 | -9744 | c=0.50: +730 / -4010 / +745 | 88 | +0.042 | +0.285 | -0.08 / +0.41 / +0.15 | RED |
| Lf2905267 | ADD | L6M | +1836 / +3213 | -5585 | +1370 / +2397 | -9744 | c=0.50: +483 / -4010 / +744 | 207 | +0.068 | +0.522 | -0.05 / +0.21 / +0.04 | RED |
| Lf328379c | RK7 | L3M | +2371 / +4150 | -4646 | -1494 / -2614 | -7639 | c=0.50: +2148 / -4324 / -1138 | 45 | -0.086 | -0.297 | +0.11 / +0.08 / -0.03 | AMBER |
| Lf328379c | RK7 | L6M | +1681 / +2942 | -4646 | -822 / -1439 | -7639 | c=0.50: +1456 / -4324 / -490 | 93 | -0.080 | -0.277 | +0.13 / +0.04 / +0.00 | AMBER |
| Lf3ddecc0 | RK7 | L3M | +344 / +602 | -3835 | +1088 / +1903 | +1377 | c=0.62: +704 / -3553 / +593 | 78 | +0.114 | +0.682 | +0.10 / +0.02 / -0.02 | ok |
| Lf3ddecc0 | RK7 | L6M | +282 / +494 | -3835 | +975 / +1705 | +1377 | c=0.62: +509 / -3553 / +625 | 169 | +0.077 | +0.482 | -0.03 / +0.00 / -0.05 | ok |
| Lf5b9ca6c | RK7 | L3M | +2832 / +4955 | -12503 | +2293 / +4012 | -7867 | c=0.50: +1851 / -7704 / +1646 | 121 | +0.058 | +0.539 | +0.26 / +0.19 / +0.13 | AMBER |
| Lf5b9ca6c | RK7 | L6M | +1659 / +2903 | -12503 | +1994 / +3489 | -7867 | c=0.50: +1106 / -7704 / +1318 | 292 | +0.052 | +0.563 | +0.11 / +0.10 / -0.04 | AMBER |
| Lf6becac4 | RK7 | L3M | +1991 / +3484 | -6780 | +995 / +1741 | -9158 | c=0.61: +1754 / -5325 / +809 | 50 | +0.062 | +0.238 | -0.01 / +0.01 / -0.09 | AMBER |
| Lf6becac4 | RK7 | L6M | +1565 / +2738 | -6780 | +150 / +262 | -9158 | c=0.61: +1272 / -5325 / +287 | 119 | -0.040 | -0.177 | +0.06 / +0.02 / +0.09 | AMBER |
| Lf773ab0d | RK7 | L3M | +1991 / +3484 | -6780 | +995 / +1741 | -9158 | c=0.61: +1754 / -5325 / +809 | 50 | +0.062 | +0.238 | -0.01 / +0.01 / -0.09 | AMBER |
| Lf773ab0d | RK7 | L6M | +1565 / +2738 | -6780 | +150 / +262 | -9158 | c=0.61: +1272 / -5325 / +287 | 119 | -0.040 | -0.177 | +0.06 / +0.02 / +0.09 | AMBER |
| Lf82cdf44 | RK7 | L3M | +63 / +111 | +690 | +2912 / +5097 | +1537 | c=1.00: +63 / +690 / +2912 | 129 | +0.172 | +1.707 | +0.25 / +0.08 / +0.16 | ok |
| Lf82cdf44 | RK7 | L6M | +336 / +588 | -3010 | +1980 / +3464 | +1537 | c=1.00: +336 / -3010 / +1980 | 246 | +0.132 | +1.200 | +0.10 / +0.07 / +0.04 | ok |
| Lf9f3f4b5 | RK7 | L3M | +1370 / +2398 | -3610 | +70 / +122 | -4775 | c=0.57: +1178 / -2431 / -186 | 91 | +0.041 | +0.284 | +0.08 / +0.00 / +0.07 | AMBER |
| Lf9f3f4b5 | RK7 | L6M | +1133 / +1983 | -3610 | +1630 / +2852 | -4775 | c=0.57: +912 / -2431 / +920 | 209 | +0.102 | +0.789 | -0.02 / -0.00 / +0.13 | AMBER |
| Lfa1de080 | RK7 | L3M | +579 / +1013 | +1131 | +1965 / +3440 | -612 | c=1.00: +579 / +1131 / +1965 | 213 | +0.058 | +0.943 | +0.21 / +0.11 / +0.40 | ok |
| Lfa1de080 | RK7 | L6M | +362 / +634 | +1131 | +2726 / +4770 | -612 | c=1.00: +362 / +1131 / +2726 | 485 | +0.101 | +1.812 | +0.19 / +0.04 / +0.19 | ok |
| Lfa1de080 | ADD | L3M | -39 / -68 | +2726 | +2148 / +3759 | +875 | c=1.00: -39 / +2726 / +2148 | 211 | +0.065 | +1.055 | +0.22 / +0.12 / +0.41 | ok |
| Lfa1de080 | ADD | L6M | -53 / -93 | +2726 | +2554 / +4469 | +875 | c=1.00: -53 / +2726 / +2554 | 482 | +0.105 | +1.866 | +0.19 / +0.04 / +0.19 | ok |
| Lfa1de080 | ADD | Y2023 | -2350 / -4113 | -4017 | +868 / +1519 | +1565 | c=1.00: -2350 / -4017 / +868 | 441 | +0.063 | +0.714 | +0.13 / +0.15 / +0.19 | ok |
| Lfa1de080 | ADD | Y2024 | -281 / -492 | -2465 | +757 / +1325 | +4158 | c=1.00: -281 / -2465 / +757 | 691 | +0.053 | +0.690 | +0.19 / +0.16 / +0.19 | ok |
| Lfa1de080 | ADD | Y2025 | +803 / +1406 | -757 | +630 / +1103 | -8148 | c=1.00: +803 / -757 / +630 | 850 | +0.041 | +0.658 | +0.19 / +0.03 / +0.22 | ok |
| Lfa46118f | RK7 | L3M | +6885 / +12050 | -8104 | -649 / -1136 | -19527 | c=0.53: +3434 / -5677 / -258 | 92 | -0.053 | -0.373 | +0.10 / +0.24 / +0.28 | RED |
| Lfa46118f | RK7 | L6M | +4427 / +7747 | -8104 | +510 / +893 | -19527 | c=0.53: +2201 / -5677 / +346 | 224 | +0.019 | +0.156 | +0.02 / +0.17 / +0.24 | RED |
| Lfa46118f | ADD | L3M | +6563 / +11485 | -8760 | -719 / -1259 | -17768 | c=0.53: +3308 / -6334 / -541 | 91 | -0.024 | -0.170 | +0.14 / +0.24 / +0.30 | RED |
| Lfa46118f | ADD | L6M | +4109 / +7191 | -8760 | +291 / +509 | -17768 | c=0.53: +1991 / -6334 / +30 | 222 | +0.030 | +0.248 | +0.04 / +0.17 / +0.25 | RED |
| Lfa8c13c0 | RK7 | L3M | +272 / +477 | -4905 | +2381 / +4167 | +952 | c=0.94: +316 / -4798 / +2296 | 69 | +0.214 | +1.136 | -0.03 / -0.14 / -0.07 | ok |
| Lfa8c13c0 | RK7 | L6M | +266 / +465 | -4905 | +2264 / +3962 | +952 | c=0.94: +290 / -4798 / +2165 | 142 | +0.250 | +1.316 | -0.02 / -0.08 / +0.07 | ok |
| Lfe9994ff | RK7 | L3M | -87 / -152 | -3405 | +2466 / +4315 | +941 | c=0.56: +444 / -3263 / +1754 | 61 | +0.158 | +0.742 | +0.34 / +0.02 / +0.18 | ok |
| Lfe9994ff | RK7 | L6M | +269 / +471 | -3585 | +2186 / +3826 | +941 | c=0.56: +463 / -3263 / +1369 | 140 | +0.164 | +0.851 | +0.15 / +0.05 / +0.11 | ok |
| Lffb0f715 | RK7 | L3M | +2450 / +4288 | -5105 | -1028 / -1799 | -8790 | c=0.50: +1431 / -2983 / -292 | 55 | -0.145 | -0.614 | +0.11 / +0.10 / -0.03 | AMBER |
| Lffb0f715 | RK7 | L6M | +1713 / +2998 | -5105 | -656 / -1148 | -8790 | c=0.50: +1011 / -2983 / -114 | 130 | -0.094 | -0.452 | +0.12 / +0.05 / +0.01 | AMBER |
| NA1 | CT | L3M | +2562 / +4484 | -10610 | -3062 / -5358 | -9861 | c=0.50: +629 / -4141 / -1308 | 137 | -0.139 | -1.462 | -0.17 / +0.10 / -0.03 | RED |
| NA1 | CT | L6M | +1333 / +2334 | -10610 | +633 / +1108 | -9861 | c=0.50: +55 / -4141 / +538 | 330 | +0.006 | +0.079 | -0.07 / +0.06 / -0.02 | RED |
| NA1 | ADD | L3M | +5762 / +10083 | +360 | -2340 / -4095 | -15707 | c=0.50: +2009 / +378 / -1141 | 95 | -0.137 | -0.999 | -0.21 / +0.12 / -0.09 | RED |
| NA1 | ADD | L6M | +3903 / +6830 | -6471 | -504 / -882 | -15707 | c=0.50: +1368 / -1076 / -272 | 218 | -0.024 | -0.193 | -0.08 / +0.06 / -0.02 | RED |
| NA1 | BARE | L3M | +2519 / +4409 | -10610 | -2914 / -5100 | -9861 | c=0.50: +629 / -4141 / -1234 | 139 | -0.131 | -1.400 | -0.18 / +0.11 / -0.03 | RED |
| NA1 | BARE | L6M | +1331 / +2329 | -10610 | +712 / +1245 | -9861 | c=0.50: +65 / -4141 / +578 | 339 | +0.009 | +0.112 | -0.07 / +0.05 / -0.00 | RED |
| NA1 | RK7 | L3M | +6017 / +10529 | -2702 | -2012 / -3521 | -15862 | c=0.50: +2308 / -1510 / -813 | 95 | -0.137 | -0.999 | -0.21 / +0.12 / -0.09 | RED |
| NA1 | RK7 | L6M | +4178 / +7311 | -7060 | -173 / -303 | -15862 | c=0.50: +1661 / -1666 / +74 | 220 | -0.025 | -0.206 | -0.08 / +0.06 / -0.02 | RED |
| NA1 | RM7 | L3M | +4784 / +8372 | -1512 | -3106 / -5435 | -13679 | c=0.50: +1677 / -319 / -1955 | 95 | -0.131 | -0.959 | -0.20 / +0.08 / -0.08 | RED |
| NA1 | RM7 | L6M | +3187 / +5577 | -5020 | -779 / -1363 | -13679 | c=0.50: +1053 / -319 / -549 | 219 | -0.024 | -0.191 | -0.08 / +0.04 / -0.01 | RED |
| NA1 | RP7 | L3M | +4284 / +7498 | +748 | -2901 / -5076 | -11036 | c=0.50: +685 / +1006 / -1702 | 95 | -0.137 | -0.999 | -0.21 / +0.12 / -0.09 | RED |
| NA1 | RP7 | L6M | +3012 / +5271 | -6471 | -836 / -1463 | -11036 | c=0.50: +608 / -1076 / -604 | 218 | -0.024 | -0.193 | -0.08 / +0.06 / -0.02 | RED |
| NA2 | CT | L3M | +3507 / +6138 | -14180 | -1650 / -2887 | -8675 | c=0.71: +2456 / -9463 / -1085 | 129 | -0.119 | -1.176 | -0.20 / +0.14 / -0.16 | RED |
| NA2 | CT | L6M | +1832 / +3206 | -14180 | +806 / +1411 | -8675 | c=0.71: +1123 / -9463 / +673 | 320 | +0.023 | +0.278 | -0.03 / +0.14 / +0.02 | AMBER |
| NA2 | ADD | L3M | +104 / +182 | +758 | +153 / +268 | +3822 | c=0.71: -34 / +1437 / +188 | 88 | -0.011 | -0.073 | -0.22 / +0.15 / -0.19 | ok |
| NA2 | ADD | L6M | +420 / +736 | -1791 | -38 / -67 | +2965 | c=0.71: +209 / -45 / -14 | 200 | -0.007 | -0.050 | -0.04 / +0.18 / +0.04 | ok |
| NA2 | BARE | L3M | +3522 / +6163 | -14180 | -1657 / -2900 | -8675 | c=0.71: +2466 / -9463 / -1090 | 129 | -0.119 | -1.181 | -0.20 / +0.14 / -0.16 | RED |
| NA2 | BARE | L6M | +1847 / +3232 | -14180 | +637 / +1115 | -8675 | c=0.71: +1131 / -9463 / +552 | 323 | +0.015 | +0.177 | -0.02 / +0.14 / +0.04 | AMBER |
| NA2 | RK7 | L3M | +1279 / +2238 | -2692 | +376 / +659 | +372 | c=0.71: +958 / -2014 / +411 | 88 | -0.011 | -0.073 | -0.22 / +0.15 / -0.19 | ok |
| NA2 | RK7 | L6M | +1251 / +2190 | -2692 | +259 / +452 | -553 | c=0.71: +929 / -2014 / +273 | 201 | -0.004 | -0.031 | -0.04 / +0.18 / +0.04 | ok |
| NA2 | RM7 | L3M | +339 / +594 | -1502 | -1016 / -1779 | +1562 | c=0.71: +203 / -823 / -981 | 88 | -0.011 | -0.073 | -0.22 / +0.15 / -0.19 | ok |
| NA2 | RM7 | L6M | +376 / +658 | -1502 | -452 / -790 | +1562 | c=0.71: +191 / -823 / -437 | 201 | -0.004 | -0.031 | -0.04 / +0.18 / +0.04 | ok |
| NA2 | RP7 | L3M | -324 / -567 | +758 | -566 / -990 | +3822 | c=0.71: -475 / +1437 / -531 | 88 | -0.011 | -0.073 | -0.22 / +0.15 / -0.19 | ok |
| NA2 | RP7 | L6M | +219 / +383 | -1791 | -446 / -780 | +1835 | c=0.71: -5 / -45 / -422 | 200 | -0.007 | -0.050 | -0.04 / +0.18 / +0.04 | ok |
| NA3 | ADD | L3M | +1619 / +2833 | -3531 | -1393 / -2438 | -5081 | c=0.74: +1125 / -2426 / -1017 | 70 | -0.164 | -0.884 | -0.13 / -0.14 / -0.15 | AMBER |
| NA3 | ADD | L6M | +910 / +1592 | -3531 | +712 / +1247 | -5081 | c=0.74: +620 / -2426 / +532 | 164 | +0.070 | +0.426 | -0.06 / -0.08 / +0.04 | AMBER |
| NA3 | ALL | L3M | +2766 / +4841 | -6433 | -3518 / -6156 | -8287 | c=7.38: +31593 / -33690 / -14024 | 73 | -0.180 | -1.013 | -0.18 / -0.14 / -0.17 | AMBER |
| NA3 | ALL | L6M | +1738 / +3041 | -6433 | -193 / -338 | -8287 | c=7.38: +25408 / -49395 / +3747 | 168 | +0.061 | +0.380 | -0.08 / -0.08 / +0.03 | AMBER |
| NA3 | RK7 | L3M | +2494 / +4364 | -5085 | -903 / -1580 | -7749 | c=0.74: +1997 / -3980 / -481 | 72 | -0.179 | -0.994 | -0.16 / -0.13 / -0.17 | AMBER |
| NA3 | RK7 | L6M | +1564 / +2738 | -5085 | +1124 / +1967 | -7749 | c=0.74: +1271 / -3980 / +959 | 167 | +0.063 | +0.389 | -0.08 / -0.08 / +0.03 | AMBER |
| NA3 | RM7 | L3M | +1879 / +3289 | -4420 | -2562 / -4484 | -6306 | c=0.74: +1404 / -3315 / -2154 | 71 | -0.176 | -0.959 | -0.16 / -0.14 / -0.16 | AMBER |
| NA3 | RM7 | L6M | +1002 / +1754 | -4420 | +248 / +434 | -6306 | c=0.74: +712 / -3315 / +82 | 165 | +0.064 | +0.389 | -0.07 / -0.08 / +0.03 | AMBER |
| NA3 | RP7 | L3M | +1108 / +1939 | -2903 | -1980 / -3465 | -3226 | c=0.74: +607 / -1798 / -1604 | 70 | -0.164 | -0.884 | -0.13 / -0.14 / -0.15 | ok |
| NA3 | RP7 | L6M | +618 / +1081 | -2903 | +368 / +644 | -3226 | c=0.74: +327 / -1798 / +187 | 164 | +0.070 | +0.426 | -0.06 / -0.08 / +0.04 | ok |
| NA4 | D1 | L3M | +1846 / +3231 | -6561 | -874 / -1530 | -6086 | c=4.50: +18492 / -20384 / +1376 | 138 | +0.025 | +0.268 | -0.02 / +0.07 / +0.07 | AMBER |
| NA4 | D1 | L6M | +1041 / +1822 | -6561 | +838 / +1466 | -6086 | c=4.50: +13556 / -20384 / +5537 | 316 | +0.048 | +0.559 | +0.07 / +0.09 / +0.24 | AMBER |
| NA4 | ADD | L3M | +107 / +187 | -3530 | +375 / +657 | +307 | c=0.50: +239 / -2385 / +36 | 137 | +0.027 | +0.283 | -0.02 / +0.07 / +0.07 | ok |
| NA4 | ADD | L6M | -8 / -13 | -3530 | +1158 / +2026 | +307 | c=0.50: +72 / -2385 / +455 | 316 | +0.050 | +0.586 | +0.08 / +0.09 / +0.25 | ok |
| NA4 | ALL | L3M | +2985 / +5225 | -7579 | -1756 / -3073 | -9209 | c=5.00: +26592 / -28560 / +815 | 138 | +0.025 | +0.268 | -0.02 / +0.07 / +0.07 | AMBER |
| NA4 | ALL | L6M | +1812 / +3170 | -7579 | +301 / +526 | -9209 | c=5.00: +19374 / -28560 / +5671 | 316 | +0.048 | +0.559 | +0.07 / +0.09 / +0.24 | AMBER |
| NA4 | CT14m | L3M | +2515 / +4402 | -4085 | +1360 / +2380 | -9416 | c=0.50: +1506 / -3116 / +510 | 120 | +0.077 | +0.709 | -0.36 / -0.08 / -0.10 | RED |
| NA4 | CT14m | L6M | +2115 / +3702 | -4085 | -556 / -973 | -9416 | c=0.50: +1277 / -3116 / -450 | 272 | -0.009 | -0.088 | -0.19 / +0.01 / -0.01 | RED |
| NA4 | CT14p | L3M | +1434 / +2509 | -3991 | +2133 / +3733 | -5191 | c=0.50: +1138 / -1098 / +1114 | 131 | +0.084 | +0.849 | +0.01 / +0.33 / -0.02 | AMBER |
| NA4 | CT14p | L6M | +1013 / +1774 | -3991 | +159 / +279 | -5191 | c=0.50: +735 / -1098 / +206 | 328 | -0.003 | -0.039 | -0.05 / +0.24 / +0.08 | AMBER |
| NA4 | CT21m | L3M | +1413 / +2472 | -2460 | -1716 / -3003 | -6297 | c=0.50: +814 / +1765 / -1384 | 111 | -0.032 | -0.276 | -0.05 / -0.24 / +0.11 | AMBER |
| NA4 | CT21m | L6M | +1298 / +2272 | -2460 | -738 / -1292 | -6297 | c=0.50: +787 / +1765 / -621 | 280 | -0.009 | -0.097 | +0.01 / -0.17 / +0.09 | AMBER |
| NA4 | CT21p | L3M | +2860 / +5005 | -3200 | -1599 / -2798 | -7405 | c=0.50: +978 / -2220 / -753 | 139 | -0.066 | -0.705 | +0.07 / +0.10 / +0.15 | AMBER |
| NA4 | CT21p | L6M | +1676 / +2933 | -3200 | -1067 / -1867 | -7405 | c=0.50: +542 / -2220 / -549 | 329 | -0.035 | -0.431 | +0.00 / +0.07 / +0.13 | AMBER |
| NA4 | CT28m | L3M | +2388 / +4179 | -509 | -26 / -45 | -6767 | c=0.50: +774 / -255 / +36 | 107 | -0.006 | -0.051 | +0.15 / +0.29 / +0.21 | AMBER |
| NA4 | CT28m | L6M | +1705 / +2984 | -3561 | +703 / +1231 | -6767 | c=0.50: +577 / -255 / +344 | 270 | +0.030 | +0.299 | +0.10 / +0.18 / +0.16 | AMBER |
| NA4 | CT28p | L3M | +534 / +935 | +1171 | -2054 / -3594 | +576 | c=0.50: +295 / +585 / -1873 | 131 | -0.015 | -0.150 | -0.04 / -0.06 / -0.25 | ok |
| NA4 | CT28p | L6M | +993 / +1737 | +1171 | -2288 / -4005 | -5867 | c=0.50: +620 / +585 / -1655 | 294 | -0.048 | -0.528 | -0.13 / -0.05 / -0.08 | AMBER |
| NA4 | CT35m | L3M | -647 / -1133 | +3133 | -683 / -1196 | +4031 | c=0.50: -375 / +2363 / -340 | 89 | -0.042 | -0.286 | -0.04 / -0.07 / -0.17 | ok |
| NA4 | CT35m | L6M | -504 / -882 | +3133 | +198 / +347 | +4031 | c=0.50: -338 / +2363 / +189 | 249 | +0.001 | +0.008 | -0.05 / -0.00 / -0.22 | ok |
| NA4 | CT35p | L3M | +4230 / +7402 | -1840 | -1053 / -1843 | -13232 | c=0.50: +1212 / -2138 / -369 | 127 | -0.058 | -0.571 | -0.02 / +0.14 / -0.02 | RED |
| NA4 | CT35p | L6M | +2559 / +4477 | -1840 | -154 / -269 | -13232 | c=0.50: +685 / -2138 / +2 | 299 | -0.012 | -0.129 | -0.06 / +0.06 / -0.17 | RED |
| NA4 | CT7m | L3M | +3851 / +6739 | -2190 | -238 / -416 | -10827 | c=0.50: +1518 / -2313 / -331 | 134 | +0.008 | +0.077 | +0.05 / -0.04 / -0.08 | RED |
| NA4 | CT7m | L6M | +2359 / +4129 | -2190 | +389 / +681 | -10827 | c=0.50: +881 / -2313 / +27 | 307 | +0.027 | +0.302 | +0.07 / +0.02 / -0.06 | RED |
| NA4 | CT7p | L3M | -1320 / -2309 | +6824 | +2679 / +4687 | +1406 | c=0.50: -786 / +5296 / +1873 | 143 | +0.061 | +0.672 | -0.11 / -0.07 / -0.13 | ok |
| NA4 | CT7p | L6M | +138 / +241 | +344 | +258 / +451 | -3369 | c=0.50: +134 / +2331 / +253 | 327 | +0.000 | +0.004 | -0.15 / +0.03 / -0.14 | ok |
| NA4 | RK7 | L3M | +1291 / +2260 | -3998 | +952 / +1666 | -4094 | c=0.50: +1031 / -2854 / +613 | 137 | +0.027 | +0.283 | -0.02 / +0.07 / +0.07 | ok |
| NA4 | RK7 | L6M | +730 / +1278 | -3998 | +1770 / +3097 | -4094 | c=0.50: +601 / -2854 / +1066 | 316 | +0.050 | +0.586 | +0.08 / +0.09 / +0.25 | ok |
| NA4 | RM7 | L3M | +423 / +741 | -5177 | -492 / -861 | -1679 | c=0.50: +425 / -4032 / -831 | 137 | +0.027 | +0.283 | -0.02 / +0.07 / +0.07 | ok |
| NA4 | RM7 | L6M | +152 / +265 | -5177 | +751 / +1315 | -1679 | c=0.50: +137 / -4032 / +69 | 314 | +0.049 | +0.568 | +0.07 / +0.09 / +0.24 | ok |
| NA4 | RP7 | L3M | -401 / -701 | -3530 | +89 / +156 | +2162 | c=0.50: -282 / -2385 / -250 | 137 | +0.027 | +0.283 | -0.02 / +0.07 / +0.07 | ok |
| NA4 | RP7 | L6M | -294 / -514 | -3530 | +924 / +1617 | +2162 | c=0.50: -218 / -2385 / +221 | 316 | +0.050 | +0.586 | +0.08 / +0.09 / +0.25 | ok |
| NA4 | RP7 | Y2023 | +5588 / +9779 | -5257 | +611 / +1069 | -11037 | c=0.50: +3453 / -3388 / +95 | 493 | +0.034 | +0.430 | -0.07 / -0.02 / -0.06 | AMBER |
| NA4 | RP7 | Y2024 | +817 / +1430 | +2629 | +361 / +632 | -3068 | c=0.50: +45 / +2708 / +341 | 633 | +0.001 | +0.016 | -0.00 / +0.04 / +0.03 | ok |
| NA4 | RP7 | Y2025 | -5913 / -10347 | +1530 | +881 / +1541 | +65 | c=0.50: -3386 / +1014 / +536 | 652 | +0.023 | +0.288 | +0.04 / -0.05 / +0.03 | ok |
| NA4:NA6 | C2 | L3M | +5014 / +8774 | -9572 | -1559 / -2728 | -12302 | c=2.50: +10780 / -20063 / -288 | 0 | +nan | +0.353 | -0.30 / +0.07 / +0.02 | RED |
| NA4:NA6 | C2 | L6M | +3087 / +5402 | -9572 | -82 / -143 | -12302 | c=2.50: +7123 / -20063 / +1363 | 0 | +nan | +0.401 | -0.07 / +0.11 / +0.15 | RED |
| NA4:NA6 | D2 | L3M | +4271 / +7474 | -9572 | -989 / -1730 | -10080 | c=2.25: +8909 / -18315 / +70 | 0 | +nan | +0.353 | -0.30 / +0.07 / +0.02 | RED |
| NA4:NA6 | D2 | L6M | +2553 / +4468 | -9572 | +305 / +534 | -10080 | c=2.25: +5773 / -18315 / +1509 | 0 | +nan | +0.401 | -0.07 / +0.11 / +0.15 | RED |
| NA4:NA6 | D2 | Y2023 | +4548 / +7958 | -8955 | +40 / +71 | -9838 | c=2.25: +11114 / -10415 / +1175 | 0 | +nan | +0.378 | +0.03 / +0.02 / -0.01 | AMBER |
| NA4:NA6:WA10 | C3 | L3M | +4772 / +8350 | -5877 | -1769 / -3096 | -13919 | c=1.67: +7542 / -8076 / -1606 | 0 | +nan | +0.102 | -0.34 / +0.02 / +0.13 | RED |
| NA4:NA6:WA10 | C3 | L6M | +2845 / +4979 | -5877 | +1314 / +2299 | -13919 | c=1.67: +4664 / -8076 / +2696 | 0 | +nan | +0.864 | -0.15 / +0.01 / +0.25 | RED |
| NA4:WA2:NA6 | C3 | L3M | +4452 / +7791 | -9572 | -1060 / -1854 | -11527 | c=1.67: +6687 / -14235 / -422 | 0 | +nan | +0.399 | -0.21 / +0.09 / +0.01 | RED |
| NA4:WA2:NA6 | C3 | L6M | +2833 / +4958 | -9572 | +706 / +1236 | -11527 | c=1.67: +4503 / -14235 / +1726 | 0 | +nan | +0.637 | -0.03 / +0.13 / +0.06 | RED |
| NA4:WA2:NA6 | C3 | Y2023 | +2943 / +5150 | -1441 | +480 / +839 | -6682 | c=1.67: +5431 / -142 / +1431 | 0 | +nan | +0.595 | +0.08 / +0.03 / +0.09 | AMBER |
| NA4:WA2:NA6 | C3 | Y2024 | +125 / +218 | -6903 | +43 / +76 | +5648 | c=1.67: +1960 / -12182 / +199 | 0 | +nan | +0.097 | +0.05 / +0.05 / +0.08 | ok |
| NA4:WA2:NA6 | C3 | Y2025 | -5236 / -9163 | +3920 | +491 / +858 | +3963 | c=1.67: -7880 / -765 / +1433 | 0 | +nan | +0.589 | +0.03 / -0.09 / +0.09 | ok |
| NA5 | CT | L3M | +473 / +828 | -755 | +2030 / +3552 | -2298 | c=0.50: -909 / +174 / +1510 | 164 | +0.034 | +0.433 | -0.04 / +0.07 / +0.03 | ok |
| NA5 | CT | L6M | +131 / +229 | -755 | +2062 / +3609 | -2298 | c=0.50: -797 / +174 / +1369 | 416 | +0.037 | +0.578 | +0.01 / +0.05 / +0.02 | ok |
| NA5 | ADD | L3M | +1264 / +2212 | +236 | +1669 / +2922 | -4742 | c=0.50: +254 / +118 / +1336 | 111 | +0.033 | +0.278 | -0.05 / +0.11 / +0.05 | AMBER |
| NA5 | ADD | L6M | +860 / +1505 | +184 | +1351 / +2364 | -4742 | c=0.50: +175 / +118 / +985 | 267 | +0.031 | +0.305 | -0.01 / +0.07 / +0.04 | AMBER |
| NA5 | ALL | L3M | +2316 / +4053 | -2698 | -1225 / -2144 | -8299 | c=5.00: +24826 / -18585 / +1976 | 113 | +0.038 | +0.333 | -0.04 / +0.10 / +0.06 | AMBER |
| NA5 | ALL | L6M | +1618 / +2832 | -2698 | -7 / -12 | -8299 | c=5.00: +19623 / -18585 / +3181 | 269 | +0.033 | +0.332 | -0.00 / +0.07 / +0.04 | AMBER |
| NA5 | BARE | L3M | +435 / +760 | -755 | +2481 / +4342 | -2298 | c=0.50: -924 / +174 / +1780 | 167 | +0.045 | +0.584 | -0.03 / +0.07 / +0.05 | ok |
| NA5 | BARE | L6M | +99 / +174 | -755 | +2483 / +4345 | -2298 | c=0.50: -817 / +174 / +1601 | 438 | +0.045 | +0.735 | +0.02 / +0.05 / +0.03 | ok |
| NA5 | RK7 | L3M | +2168 / +3794 | -1198 | +1683 / +2946 | -8686 | c=0.50: +1412 / -1381 / +1283 | 113 | +0.038 | +0.333 | -0.04 / +0.10 / +0.06 | AMBER |
| NA5 | RK7 | L6M | +1551 / +2714 | -1198 | +1490 / +2608 | -8686 | c=0.50: +1001 / -1381 / +1092 | 269 | +0.033 | +0.332 | -0.00 / +0.07 / +0.04 | AMBER |
| NA5 | RM7 | L3M | +1264 / +2212 | +170 | +588 / +1029 | -5145 | c=0.50: +380 / -12 / +188 | 113 | +0.038 | +0.333 | -0.04 / +0.10 / +0.06 | AMBER |
| NA5 | RM7 | L6M | +756 / +1322 | +170 | +891 / +1560 | -5145 | c=0.50: +145 / -12 / +493 | 269 | +0.033 | +0.332 | -0.00 / +0.07 / +0.04 | AMBER |
| NA5 | RP7 | L3M | +273 / +478 | +864 | +998 / +1747 | -1334 | c=0.50: -248 / +746 / +665 | 111 | +0.033 | +0.278 | -0.05 / +0.11 / +0.05 | ok |
| NA5 | RP7 | L6M | +301 / +526 | +184 | +966 / +1691 | -1334 | c=0.50: -96 / +746 / +600 | 267 | +0.031 | +0.305 | -0.01 / +0.07 / +0.04 | ok |
| NA6 | ADD | L3M | +1674 / +2930 | -4066 | -279 / -489 | -5099 | c=0.50: +550 / -1686 / -117 | 80 | -0.022 | -0.135 | +0.18 / +0.34 / +0.34 | AMBER |
| NA6 | ADD | L6M | +894 / +1564 | -4066 | +1215 / +2127 | -5099 | c=0.50: +279 / -1686 / +589 | 188 | +0.075 | +0.522 | +0.10 / +0.25 / +0.02 | AMBER |
| NA6 | ALL | L3M | +4698 / +8221 | -6923 | -2580 / -4515 | -13943 | c=5.00: +20762 / -25959 / -3879 | 80 | -0.022 | -0.135 | +0.18 / +0.34 / +0.34 | RED |
| NA6 | ALL | L6M | +2864 / +5012 | -6923 | +176 / +308 | -13943 | c=5.00: +14325 / -25959 / +5183 | 188 | +0.075 | +0.522 | +0.10 / +0.25 / +0.02 | RED |
| NA6 | ALL | Y2023 | -2087 / -3653 | -10977 | +186 / +326 | +4174 | c=5.00: +5658 / -21946 / +4698 | 219 | +0.084 | +0.470 | +0.09 / +0.05 / +0.11 | ok |
| NA6 | ALL | Y2024 | -1030 / -1803 | -3909 | +795 / +1391 | +8207 | c=5.00: +5341 / -23606 / +4695 | 320 | +0.067 | +0.406 | +0.11 / +0.02 / +0.24 | ok |
| NA6 | ALL | Y2025 | -9362 / -16384 | +10180 | +92 / +162 | +19357 | c=5.00: +901 / -7943 / +4888 | 350 | +0.076 | +0.499 | -0.08 / +0.01 / -0.06 | ok |
| NA6 | RK7 | L3M | +3784 / +6621 | -6323 | -641 / -1121 | -11809 | c=0.50: +2361 / -3943 / -478 | 80 | -0.022 | -0.135 | +0.18 / +0.34 / +0.34 | RED |
| NA6 | RK7 | L6M | +2288 / +4004 | -6323 | +1216 / +2127 | -11809 | c=0.50: +1467 / -3943 / +590 | 188 | +0.075 | +0.522 | +0.10 / +0.25 / +0.02 | RED |
| NA6 | RM7 | L3M | +1818 / +3181 | -4955 | -1421 / -2487 | -5946 | c=0.50: +886 / -2575 / -1259 | 80 | -0.022 | -0.135 | +0.18 / +0.34 / +0.34 | AMBER |
| NA6 | RM7 | L6M | +896 / +1567 | -4955 | +728 / +1274 | -5946 | c=0.50: +380 / -2575 / +102 | 188 | +0.075 | +0.522 | +0.10 / +0.25 / +0.02 | AMBER |
| NA6 | RP7 | L3M | +982 / +1718 | -3438 | -619 / -1083 | -2866 | c=0.50: +7 / -1058 / -454 | 81 | -0.022 | -0.137 | +0.18 / +0.34 / +0.34 | ok |
| NA6 | RP7 | L6M | +486 / +851 | -3438 | +990 / +1733 | -2866 | c=0.50: -27 / -1058 / +365 | 189 | +0.074 | +0.521 | +0.10 / +0.25 / +0.02 | ok |
| WA1 | ALL | L3M | +2424 / +4241 | -6683 | -1752 / -3065 | -8024 | c=6.04: +13163 / -31114 / +605 | 77 | +0.040 | +0.235 | +0.14 / -0.06 / +0.01 | AMBER |
| WA1 | ALL | L6M | +1689 / +2955 | -6683 | -535 / -937 | -8024 | c=6.04: +17903 / -50451 / +1927 | 176 | +0.038 | +0.246 | +0.07 / -0.02 / +0.05 | AMBER |
| WA1 | RK7 | L3M | +1176 / +2058 | -4480 | +506 / +885 | -4285 | c=0.60: +849 / -3046 / +319 | 76 | +0.040 | +0.237 | +0.14 / -0.06 / +0.01 | ok |
| WA1 | RK7 | L6M | +952 / +1665 | -4480 | +639 / +1117 | -4285 | c=0.60: +694 / -3046 / +409 | 176 | +0.045 | +0.291 | +0.07 / -0.03 / +0.07 | ok |
| WA1 | RM7 | L3M | +305 / +534 | -4940 | -638 / -1117 | -1152 | c=0.60: +57 / -3506 / -825 | 76 | +0.040 | +0.237 | +0.14 / -0.06 / +0.01 | ok |
| WA1 | RM7 | L6M | +187 / +328 | -4940 | +54 / +95 | -1152 | c=0.60: -32 / -3506 / -165 | 174 | +0.043 | +0.279 | +0.07 / -0.02 / +0.05 | ok |
| WA1 | RP7 | L3M | -395 / -692 | -4116 | -548 / -959 | +1731 | c=0.60: -533 / -2682 / -675 | 75 | +0.028 | +0.161 | +0.12 / -0.06 / -0.00 | ok |
| WA1 | RP7 | L6M | -98 / -171 | -4116 | -42 / -73 | +1731 | c=0.60: -242 / -2682 / -268 | 174 | +0.045 | +0.287 | +0.06 / -0.03 / +0.06 | ok |
| WA1 | ADD | L3M | +285 / +499 | -4744 | +55 / +96 | -793 | c=0.60: +79 / -3310 / -72 | 75 | +0.028 | +0.161 | +0.12 / -0.06 / -0.00 | ok |
| WA1 | ADD | L6M | +260 / +455 | -4744 | +310 / +543 | -793 | c=0.60: +81 / -3310 / +84 | 174 | +0.045 | +0.287 | +0.06 / -0.03 / +0.06 | ok |
| WA10 | ALL | L3M | +6138 / +10742 | -5877 | -2554 / -4470 | -16809 | c=5.00: +32237 / -19074 / -4418 | 120 | -0.021 | -0.194 | -0.27 / -0.07 / +0.06 | RED |
| WA10 | ALL | L6M | +3922 / +6864 | -5877 | +494 / +865 | -16809 | c=5.00: +24312 / -19074 / +5791 | 280 | +0.053 | +0.552 | -0.19 / -0.03 / +0.12 | RED |
| WA10 | RK7 | L3M | +4095 / +7166 | -3616 | -43 / -76 | -11948 | c=0.50: +2224 / -2116 / +208 | 119 | -0.023 | -0.209 | -0.28 / -0.06 / +0.06 | RED |
| WA10 | RK7 | L6M | +2596 / +4543 | -3616 | +1792 / +3136 | -11948 | c=0.50: +1371 / -2116 / +1119 | 280 | +0.054 | +0.561 | -0.19 / -0.03 / +0.12 | RED |
| WA10 | RM7 | L3M | +4012 / +7021 | -3702 | -1764 / -3087 | -12907 | c=0.50: +1720 / -3295 / -1513 | 119 | -0.023 | -0.209 | -0.28 / -0.06 / +0.06 | RED |
| WA10 | RM7 | L6M | +2442 / +4274 | -3702 | +785 / +1374 | -12907 | c=0.50: +912 / -3295 / +148 | 280 | +0.051 | +0.531 | -0.20 / -0.03 / +0.12 | RED |
| WA10 | RP7 | L3M | +2599 / +4547 | -1361 | -1061 / -1856 | -8422 | c=0.50: +988 / -954 / -725 | 120 | -0.030 | -0.280 | -0.29 / -0.06 / +0.07 | AMBER |
| WA10 | RP7 | L6M | +1612 / +2821 | -1361 | +1002 / +1754 | -8422 | c=0.50: +544 / -954 / +406 | 281 | +0.048 | +0.497 | -0.20 / -0.03 / +0.12 | AMBER |
| WA10 | ADD | L3M | +4109 / +7191 | -1361 | -913 / -1597 | -13141 | c=0.50: +1602 / -954 / -577 | 120 | -0.030 | -0.280 | -0.29 / -0.06 / +0.07 | RED |
| WA10 | ADD | L6M | +2533 / +4433 | -1361 | +1136 / +1987 | -13141 | c=0.50: +898 / -954 / +539 | 281 | +0.048 | +0.497 | -0.20 / -0.03 / +0.12 | RED |
| WA11 | ADD | L3M | +1914 / +3350 | +748 | -2561 / -4482 | -4662 | c=0.52: +1037 / +1732 / -1384 | 89 | -0.153 | -1.046 | -0.18 / +0.14 / -0.16 | AMBER |
| WA11 | ADD | L6M | +1435 / +2511 | -441 | -789 / -1381 | -4662 | c=0.52: +745 / +1732 / -412 | 196 | -0.046 | -0.336 | -0.05 / +0.07 / +0.10 | AMBER |
| WA12 | ALL | L3M | +2424 / +4241 | -6683 | -1760 / -3080 | -8024 | c=5.52: +11161 / -26084 / +315 | 77 | +0.036 | +0.211 | +0.14 / -0.06 / +0.01 | AMBER |
| WA12 | ALL | L6M | +1689 / +2955 | -6683 | -652 / -1141 | -8024 | c=5.52: +15169 / -42856 / +1030 | 176 | +0.026 | +0.171 | +0.07 / -0.02 / +0.05 | AMBER |
| WA12 | RK7 | L3M | +1176 / +2058 | -4480 | +497 / +870 | -4285 | c=0.55: +815 / -2857 / +290 | 76 | +0.036 | +0.212 | +0.14 / -0.06 / +0.01 | ok |
| WA12 | RK7 | L6M | +952 / +1665 | -4480 | +522 / +914 | -4285 | c=0.55: +667 / -2857 / +315 | 176 | +0.033 | +0.213 | +0.07 / -0.02 / +0.07 | ok |
| WA12 | RM7 | L3M | +305 / +534 | -4940 | -647 / -1132 | -1152 | c=0.55: +36 / -3317 / -854 | 76 | +0.036 | +0.212 | +0.14 / -0.06 / +0.01 | ok |
| WA12 | RM7 | L6M | +187 / +328 | -4940 | -62 / -109 | -1152 | c=0.55: -50 / -3317 / -259 | 174 | +0.031 | +0.201 | +0.06 / -0.02 / +0.05 | ok |
| WA12 | RP7 | L3M | -395 / -692 | -4116 | -556 / -973 | +1731 | c=0.55: -521 / -2494 / -696 | 75 | +0.025 | +0.144 | +0.12 / -0.06 / -0.00 | ok |
| WA12 | RP7 | L6M | -98 / -171 | -4116 | -158 / -277 | +1731 | c=0.55: -242 / -2494 / -362 | 174 | +0.032 | +0.209 | +0.05 / -0.03 / +0.07 | ok |
| WA12 | ADD | L3M | +285 / +499 | -4744 | +47 / +82 | -793 | c=0.55: +60 / -3122 / -93 | 75 | +0.025 | +0.144 | +0.12 / -0.06 / -0.00 | ok |
| WA12 | ADD | L6M | +260 / +455 | -4744 | +194 / +339 | -793 | c=0.55: +64 / -3122 / -10 | 174 | +0.032 | +0.209 | +0.05 / -0.03 / +0.07 | ok |
| WA2 | ALL | L3M | +4124 / +7216 | -7402 | -1232 / -2156 | -12307 | c=5.00: +16587 / -28359 / +2399 | 91 | +0.054 | +0.378 | -0.01 / +0.09 / +0.16 | RED |
| WA2 | ALL | L6M | +2494 / +4365 | -7402 | +579 / +1013 | -12307 | c=5.00: +12846 / -28359 / +6375 | 213 | +0.077 | +0.604 | +0.06 / +0.10 / +0.02 | RED |
| WA2 | CT14m | L3M | +1171 / +2050 | +825 | -471 / -825 | -7398 | c=0.50: +680 / +413 / -295 | 84 | -0.023 | -0.147 | +0.29 / +0.09 / +0.01 | AMBER |
| WA2 | CT14m | L6M | +1182 / +2068 | +825 | -357 / -626 | -7398 | c=0.50: +754 / +413 / -369 | 209 | +0.001 | +0.009 | +0.19 / +0.03 / +0.04 | AMBER |
| WA2 | CT14p | L3M | +143 / +250 | -1306 | -188 / -329 | +3293 | c=0.50: -190 / -927 / +500 | 94 | -0.079 | -0.573 | +0.29 / -0.04 / +0.05 | ok |
| WA2 | CT14p | L6M | +199 / +349 | -1306 | -336 / -588 | +3293 | c=0.50: -53 / -927 / +140 | 215 | -0.050 | -0.397 | +0.05 / -0.00 / +0.01 | ok |
| WA2 | CT21m | L3M | +469 / +821 | +811 | +1318 / +2306 | -3594 | c=0.50: +176 / +405 / +668 | 81 | +0.087 | +0.541 | +0.24 / +0.03 / -0.15 | ok |
| WA2 | CT21m | L6M | +398 / +697 | -1501 | -122 / -213 | -3594 | c=0.50: +99 / +405 / -74 | 198 | -0.005 | -0.039 | +0.12 / -0.03 / -0.21 | ok |
| WA2 | CT21p | L3M | +1456 / +2548 | -4646 | +563 / +985 | -2227 | c=0.50: +777 / -3194 / +247 | 99 | +0.035 | +0.264 | -0.24 / +0.14 / -0.00 | ok |
| WA2 | CT21p | L6M | +1100 / +1924 | -4646 | +619 / +1084 | -2227 | c=0.50: +537 / -3194 / +263 | 224 | +0.036 | +0.297 | -0.17 / +0.11 / -0.03 | ok |
| WA2 | CT28m | L3M | +3245 / +5678 | -8700 | -691 / -1209 | -11971 | c=0.50: +1563 / -4970 / -538 | 69 | -0.024 | -0.128 | +0.01 / +0.11 / +0.16 | RED |
| WA2 | CT28m | L6M | +2243 / +3926 | -8700 | -732 / -1281 | -11971 | c=0.50: +1130 / -4970 / -617 | 187 | -0.014 | -0.096 | -0.07 / +0.04 / +0.03 | RED |
| WA2 | CT28p | L3M | +1083 / +1895 | -3740 | -3777 / -6609 | -2584 | c=0.50: +427 / -1870 / -2220 | 90 | -0.187 | -1.297 | -0.09 / -0.13 / -0.18 | AMBER |
| WA2 | CT28p | L6M | +891 / +1559 | -3740 | -2805 / -4909 | -2584 | c=0.50: +379 / -1870 / -1679 | 204 | -0.124 | -0.938 | -0.10 / -0.02 / -0.17 | ok |
| WA2 | CT35m | L3M | +1365 / +2389 | -3769 | -191 / -334 | -6162 | c=0.50: +754 / -2447 / -57 | 64 | -0.023 | -0.112 | +0.11 / +0.25 / +0.02 | AMBER |
| WA2 | CT35m | L6M | +1051 / +1839 | -3769 | +369 / +645 | -6162 | c=0.50: +540 / -2447 / +265 | 188 | +0.012 | +0.087 | +0.04 / +0.19 / +0.27 | AMBER |
| WA2 | CT35p | L3M | -1466 / -2566 | +1540 | +2845 / +4980 | +2879 | c=0.50: -932 / +857 / +1885 | 101 | +0.103 | +0.801 | +0.08 / +0.04 / +0.16 | ok |
| WA2 | CT35p | L6M | -720 / -1260 | +1540 | +1765 / +3089 | +2879 | c=0.50: -496 / +857 / +941 | 232 | +0.080 | +0.687 | +0.06 / -0.00 / -0.05 | ok |
| WA2 | CT7m | L3M | +652 / +1142 | -2885 | -319 / -557 | -3114 | c=0.50: +59 / -2063 / -85 | 94 | -0.027 | -0.195 | -0.13 / -0.20 / -0.13 | ok |
| WA2 | CT7m | L6M | +552 / +966 | -2885 | -1402 / -2453 | -3114 | c=0.50: +111 / -2063 / -683 | 206 | -0.079 | -0.599 | -0.11 / -0.08 / -0.03 | ok |
| WA2 | CT7p | L3M | +2089 / +3656 | -1571 | -3991 / -6985 | -1089 | c=0.50: +556 / -1000 / -2461 | 84 | -0.197 | -1.276 | -0.11 / +0.18 / -0.20 | AMBER |
| WA2 | CT7p | L6M | +1239 / +2169 | -1571 | -2893 / -5063 | -1089 | c=0.50: +325 / -1000 / -1665 | 204 | -0.135 | -1.023 | -0.01 / +0.10 / -0.07 | AMBER |
| WA2 | RK7 | L3M | +3342 / +5849 | -6803 | +1110 / +1942 | -10729 | c=0.50: +2106 / -4183 / +656 | 91 | +0.054 | +0.378 | -0.01 / +0.09 / +0.16 | RED |
| WA2 | RK7 | L6M | +2004 / +3507 | -6803 | +1808 / +3164 | -10729 | c=0.50: +1255 / -4183 / +1083 | 213 | +0.077 | +0.604 | +0.06 / +0.10 / +0.02 | RED |
| WA2 | RM7 | L3M | +1863 / +3260 | -5434 | +120 / +211 | -6421 | c=0.50: +912 / -2815 / -333 | 91 | +0.054 | +0.378 | -0.01 / +0.09 / +0.16 | AMBER |
| WA2 | RM7 | L6M | +963 / +1685 | -5434 | +1159 / +2028 | -6421 | c=0.50: +369 / -2815 / +456 | 212 | +0.075 | +0.586 | +0.06 / +0.10 / +0.02 | AMBER |
| WA2 | RP7 | L3M | +1171 / +2049 | -3917 | +502 / +879 | -3341 | c=0.50: +136 / -1298 / +140 | 90 | +0.044 | +0.301 | -0.05 / +0.09 / +0.14 | ok |
| WA2 | RP7 | L6M | +611 / +1069 | -3917 | +1207 / +2112 | -3341 | c=0.50: -16 / -1298 / +548 | 211 | +0.070 | +0.549 | +0.05 / +0.10 / +0.01 | ok |
| WA2 | ADD | L3M | +1666 / +2915 | -4546 | +1230 / +2153 | -5196 | c=0.50: +641 / -1926 / +869 | 90 | +0.044 | +0.301 | -0.05 / +0.09 / +0.14 | AMBER |
| WA2 | ADD | L6M | +904 / +1582 | -4546 | +1619 / +2834 | -5196 | c=0.50: +273 / -1926 / +961 | 211 | +0.070 | +0.549 | +0.05 / +0.10 / +0.01 | AMBER |
| WA3 | ADD | L3M | +1225 / +2144 | -7945 | -1088 / -1903 | -3123 | c=0.50: +56 / -4593 / -632 | 104 | -0.047 | -0.380 | +0.04 / -0.12 / +0.25 | ok |
| WA3 | ADD | L6M | +950 / +1663 | -7945 | -783 / -1370 | -3123 | c=0.50: +97 / -4593 / -343 | 286 | -0.035 | -0.367 | +0.06 / -0.08 / +0.34 | ok |
| WA4 | ALL | L3M | +5053 / +8843 | -4977 | -3731 / -6529 | -13876 | c=5.93: +46219 / -58609 / -10721 | 100 | -0.091 | -0.701 | -0.11 / +0.15 / +0.11 | RED |
| WA4 | ALL | L6M | +3143 / +5500 | -4977 | -394 / -689 | -13876 | c=5.93: +33501 / -58609 / +3101 | 229 | +0.041 | +0.350 | -0.00 / +0.07 / +0.06 | RED |
| WA4 | RK7 | L3M | +5945 / +10404 | -3733 | -1897 / -3319 | -16896 | c=0.59: +3426 / -2849 / -1202 | 98 | -0.112 | -0.842 | -0.11 / +0.15 / +0.11 | RED |
| WA4 | RK7 | L6M | +3707 / +6487 | -3733 | +475 / +831 | -16896 | c=0.59: +2123 / -2849 / +242 | 227 | +0.034 | +0.282 | -0.01 / +0.07 / +0.06 | RED |
| WA4 | RM7 | L3M | +4756 / +8324 | -2365 | -2727 / -4773 | -13021 | c=0.59: +2336 / -1481 / -2108 | 99 | -0.099 | -0.751 | -0.12 / +0.15 / +0.10 | RED |
| WA4 | RM7 | L6M | +2814 / +4925 | -2365 | +103 / +180 | -13021 | c=0.59: +1274 / -1481 / -166 | 228 | +0.039 | +0.326 | -0.01 / +0.07 / +0.06 | RED |
| WA4 | RP7 | L3M | +3242 / +5673 | -1541 | -2299 / -4023 | -7949 | c=0.59: +879 / -657 / -1605 | 98 | -0.112 | -0.842 | -0.11 / +0.15 / +0.11 | AMBER |
| WA4 | RP7 | L6M | +1903 / +3331 | -1541 | +158 / +277 | -7949 | c=0.59: +466 / -657 / -75 | 227 | +0.034 | +0.282 | -0.01 / +0.07 / +0.06 | AMBER |
| WA4 | ADD | L3M | +5022 / +8788 | -2169 | -1833 / -3207 | -13378 | c=0.59: +2528 / -1286 / -1138 | 98 | -0.112 | -0.842 | -0.11 / +0.15 / +0.11 | RED |
| WA4 | ADD | L6M | +3020 / +5286 | -2169 | +444 / +778 | -13378 | c=0.59: +1457 / -1286 / +211 | 227 | +0.034 | +0.282 | -0.01 / +0.07 / +0.06 | RED |
| WA5 | ALL | L3M | +3392 / +5936 | -4959 | -2136 / -3737 | -11470 | c=5.00: +11350 / -17317 / -2315 | 42 | -0.006 | -0.019 | +0.01 / -0.12 / +0.04 | RED |
| WA5 | ALL | L6M | +2202 / +3854 | -4959 | -636 / -1113 | -11470 | c=5.00: +7930 / -17317 / +553 | 83 | +0.040 | +0.124 | +0.04 / -0.14 / +0.06 | RED |
| WA5 | RK7 | L3M | +2522 / +4414 | -3950 | +200 / +351 | -9482 | c=0.50: +1871 / -2405 / +223 | 42 | -0.006 | -0.019 | +0.01 / -0.12 / +0.04 | RED |
| WA5 | RK7 | L6M | +1688 / +2953 | -3950 | +585 / +1024 | -9482 | c=0.50: +1256 / -2405 / +436 | 83 | +0.040 | +0.124 | +0.04 / -0.14 / +0.06 | RED |
| WA5 | RM7 | L3M | +511 / +894 | -3285 | -1221 / -2136 | -2937 | c=0.50: +375 / -1740 / -1198 | 42 | -0.006 | -0.019 | +0.01 / -0.12 / +0.04 | ok |
| WA5 | RM7 | L6M | +262 / +458 | -3285 | -215 / -376 | -2937 | c=0.50: +148 / -1740 / -364 | 83 | +0.040 | +0.124 | +0.04 / -0.14 / +0.06 | ok |
| WA5 | RP7 | L3M | -185 / -324 | -2461 | -770 / -1348 | -550 | c=0.50: -319 / -916 / -748 | 42 | -0.006 | -0.019 | +0.01 / -0.12 / +0.04 | ok |
| WA5 | RP7 | L6M | -47 / -83 | -2461 | +6 / +10 | -550 | c=0.50: -165 / -916 / -143 | 83 | +0.040 | +0.124 | +0.04 / -0.14 / +0.06 | ok |
| WA5 | ADD | L3M | +317 / +554 | -3090 | -259 / -452 | -2405 | c=0.50: +200 / -1545 / -236 | 42 | -0.006 | -0.019 | +0.01 / -0.12 / +0.04 | ok |
| WA5 | ADD | L6M | +217 / +379 | -3090 | +314 / +549 | -2405 | c=0.50: +114 / -1545 / +165 | 83 | +0.040 | +0.124 | +0.04 / -0.14 / +0.06 | ok |
| WA6 | ALL | L3M | +1460 / +2556 | -1857 | -1980 / -3465 | -1365 | c=5.00: +7140 / -2043 / -664 | 100 | +0.018 | +0.137 | +0.09 / +0.29 / +0.32 | ok |
| WA6 | ALL | L6M | +909 / +1591 | -1857 | -402 / -703 | -1365 | c=5.00: +10727 / -7157 / +1671 | 228 | +0.026 | +0.216 | +0.13 / +0.18 / +0.26 | ok |
| WA6 | RK7 | L3M | +905 / +1584 | +403 | +622 / +1089 | -1166 | c=0.50: +825 / +43 / +465 | 99 | +0.017 | +0.131 | +0.09 / +0.29 / +0.32 | ok |
| WA6 | RK7 | L6M | +616 / +1078 | +403 | +905 / +1583 | -1166 | c=0.50: +577 / +43 / +649 | 227 | +0.025 | +0.213 | +0.13 / +0.18 / +0.26 | ok |
| WA6 | RM7 | L3M | +335 / +587 | +1593 | -748 / -1309 | +2149 | c=0.50: +219 / +1233 / -913 | 100 | +0.018 | +0.137 | +0.09 / +0.29 / +0.32 | ok |
| WA6 | RM7 | L6M | +59 / +104 | +1593 | +81 / +142 | +2149 | c=0.50: -10 / +1233 / -178 | 228 | +0.026 | +0.216 | +0.13 / +0.18 / +0.26 | ok |
| WA6 | RP7 | L3M | -197 / -344 | +3854 | -472 / -826 | +4535 | c=0.50: -354 / +2631 / -629 | 99 | +0.017 | +0.131 | +0.09 / +0.29 / +0.32 | ok |
| WA6 | RP7 | L6M | -126 / -220 | +2029 | +126 / +221 | +4535 | c=0.50: -222 / +2631 / -130 | 227 | +0.025 | +0.213 | +0.13 / +0.18 / +0.26 | ok |
| WA6 | ADD | L3M | +322 / +563 | +3854 | +253 / +443 | +2681 | c=0.50: +142 / +2003 / +96 | 99 | +0.017 | +0.131 | +0.09 / +0.29 / +0.32 | ok |
| WA6 | ADD | L6M | +151 / +264 | +2029 | +537 / +940 | +2681 | c=0.50: +43 / +2003 / +281 | 227 | +0.025 | +0.213 | +0.13 / +0.18 / +0.26 | ok |
| WA9 | ALL | L3M | +6033 / +10557 | -11714 | -18 / -32 | -20340 | c=7.14: +41668 / -51178 / +13725 | 119 | +0.145 | +1.332 | +0.06 / +0.36 / +0.43 | RED |
| WA9 | ALL | L6M | +3843 / +6726 | -11714 | +372 / +651 | -20340 | c=7.14: +38881 / -51178 / +8417 | 276 | +0.076 | +0.780 | +0.00 / +0.22 / +0.22 | RED |
| WA9 | RK7 | L3M | +4359 / +7629 | -9329 | +2271 / +3975 | -15774 | c=0.71: +3219 / -7493 / +1657 | 118 | +0.141 | +1.280 | +0.05 / +0.35 / +0.42 | RED |
| WA9 | RK7 | L6M | +2746 / +4805 | -9329 | +1523 / +2666 | -15774 | c=0.71: +2019 / -7493 / +1141 | 276 | +0.078 | +0.798 | -0.01 / +0.22 / +0.23 | RED |
| WA9 | RM7 | L3M | +5121 / +8961 | -10507 | +769 / +1346 | -19466 | c=0.71: +3676 / -8671 / +171 | 120 | +0.135 | +1.245 | +0.05 / +0.36 / +0.42 | RED |
| WA9 | RM7 | L6M | +3075 / +5381 | -10507 | +652 / +1142 | -19466 | c=0.71: +2133 / -8671 / +307 | 276 | +0.070 | +0.719 | -0.01 / +0.23 / +0.22 | RED |
| WA9 | RP7 | L3M | +3715 / +6502 | -10055 | +958 / +1676 | -14116 | c=0.71: +2310 / -8220 / +345 | 120 | +0.138 | +1.275 | +0.05 / +0.35 / +0.42 | RED |
| WA9 | RP7 | L6M | +2243 / +3925 | -10055 | +530 / +928 | -14116 | c=0.71: +1355 / -8220 / +157 | 277 | +0.076 | +0.776 | -0.01 / +0.22 / +0.23 | RED |
| WA9 | ADD | L3M | +5523 / +9665 | -10055 | +1629 / +2851 | -19567 | c=0.71: +4001 / -8220 / +1031 | 120 | +0.135 | +1.245 | +0.05 / +0.36 / +0.42 | RED |
| WA9 | ADD | L6M | +3391 / +5935 | -10055 | +915 / +1601 | -19567 | c=0.71: +2402 / -8220 / +549 | 277 | +0.074 | +0.762 | -0.01 / +0.23 / +0.23 | RED |
| XA1 | ALL | L3M | +656 / +1147 | +963 | -1333 / -2333 | -3108 | c=10.00: +14593 / -31782 / +2583 | 168 | +0.028 | +0.363 | +0.27 / -0.10 / -0.07 | ok |
| XA1 | ALL | L6M | +478 / +836 | +963 | -124 / -217 | -3108 | c=10.00: +14056 / -31782 / +4710 | 344 | +0.035 | +0.448 | +0.29 / -0.05 / -0.00 | ok |
| XA1 | RK7 | L3M | +379 / +664 | +1227 | +553 / +969 | -2950 | c=1.00: +379 / +1227 / +553 | 162 | +0.021 | +0.262 | +0.28 / -0.09 / -0.04 | ok |
| XA1 | RK7 | L6M | +306 / +536 | +1227 | +1023 / +1790 | -2950 | c=1.00: +306 / +1227 / +1023 | 337 | +0.035 | +0.436 | +0.30 / -0.05 / +0.01 | ok |
| XA1 | RM7 | L3M | +201 / +352 | +2596 | -335 / -586 | -2026 | c=1.00: +201 / +2596 / -335 | 163 | +0.040 | +0.506 | +0.29 / -0.13 / -0.06 | ok |
| XA1 | RM7 | L6M | +60 / +105 | +2596 | +386 / +675 | -2026 | c=1.00: +60 / +2596 / +386 | 338 | +0.044 | +0.553 | +0.30 / -0.07 / -0.00 | ok |
| XA1 | RP7 | L3M | -338 / -592 | +3419 | -273 / -477 | +361 | c=1.00: -338 / +3419 / -273 | 159 | +0.016 | +0.195 | +0.26 / -0.09 / -0.04 | ok |
| XA1 | RP7 | L6M | -173 / -302 | +3419 | +398 / +697 | +361 | c=1.00: -173 / +3419 / +398 | 334 | +0.033 | +0.404 | +0.28 / -0.05 / +0.00 | ok |
| XA1 | ADD | L3M | +103 / +180 | +2791 | +296 / +518 | -1494 | c=1.00: +103 / +2791 / +296 | 158 | +0.015 | +0.183 | +0.26 / -0.09 / -0.04 | ok |
| XA1 | ADD | L6M | +70 / +122 | +2791 | +734 / +1284 | -1494 | c=1.00: +70 / +2791 / +734 | 333 | +0.032 | +0.398 | +0.29 / -0.05 / +0.00 | ok |
| XA2 | ALL | L3M | -345 / -603 | +1760 | -1685 / -2949 | +2378 | c=10.00: +73753 / -53444 / -1569 | 268 | +0.001 | +0.011 | +0.46 / +0.28 / +0.34 | ok |
| XA2 | ALL | L6M | -283 / -496 | +1174 | -1 / -2 | +2378 | c=10.00: +59661 / -104409 / +6046 | 659 | +0.023 | +0.560 | +0.26 / +0.17 / +0.15 | ok |
| XA2 | RK7 | L3M | -557 / -975 | +2137 | +267 / +468 | +2649 | c=1.00: -557 / +2137 / +267 | 263 | +0.006 | +0.130 | +0.48 / +0.28 / +0.36 | ok |
| XA2 | RK7 | L6M | -400 / -700 | +2137 | +922 / +1614 | +2649 | c=1.00: -400 / +2137 / +922 | 654 | +0.025 | +0.617 | +0.27 / +0.17 / +0.16 | ok |
| XA2 | RM7 | L3M | -676 / -1183 | +3102 | -520 / -909 | +3171 | c=1.00: -676 / +3102 / -520 | 263 | +0.011 | +0.224 | +0.48 / +0.28 / +0.35 | ok |
| XA2 | RM7 | L6M | -630 / -1103 | +1174 | +427 / +747 | +3171 | c=1.00: -630 / +1174 / +427 | 653 | +0.026 | +0.625 | +0.27 / +0.17 / +0.16 | ok |
| XA2 | RP7 | L3M | -1582 / -2768 | +4619 | -114 / -199 | +6251 | c=1.00: -1582 / +4619 / -114 | 261 | +0.009 | +0.180 | +0.48 / +0.28 / +0.35 | ok |
| XA2 | RP7 | L6M | -1067 / -1868 | +4619 | +501 / +876 | +6251 | c=1.00: -1067 / +4619 / +501 | 651 | +0.025 | +0.604 | +0.27 / +0.17 / +0.16 | ok |
| XA2 | ADD | L3M | -1000 / -1751 | +3991 | +449 / +785 | +4396 | c=1.00: -1000 / +3991 / +449 | 261 | +0.009 | +0.180 | +0.48 / +0.28 / +0.35 | ok |
| XA2 | ADD | L6M | -751 / -1315 | +3991 | +833 / +1458 | +4396 | c=1.00: -751 / +3991 / +833 | 651 | +0.025 | +0.604 | +0.27 / +0.17 / +0.16 | ok |
| XA3 | D1 | L3M | -935 / -1637 | -187 | +1323 / +2315 | +2877 | c=9.00: +8033 / -15367 / +16551 | 166 | +0.124 | +1.586 | +0.18 / +0.12 / +0.38 | ok |
| XA3 | D1 | L6M | -540 / -945 | -187 | +1916 / +3353 | +2877 | c=9.00: +8555 / -15367 / +18379 | 387 | +0.120 | +1.715 | +0.14 / +0.09 / +0.16 | ok |
| XA3 | ALL | L3M | -651 / -1140 | -187 | +797 / +1394 | +2877 | c=10.00: +9822 / -20839 / +17929 | 166 | +0.124 | +1.586 | +0.18 / +0.12 / +0.38 | ok |
| XA3 | ALL | L6M | -297 / -520 | -187 | +1564 / +2737 | +2877 | c=10.00: +10919 / -20839 / +20085 | 387 | +0.120 | +1.715 | +0.14 / +0.09 / +0.16 | ok |
| XA3 | CT105m | L3M | +0 / +0 | +0 | +0 / +0 | +0 | c=1.00: +0 / +0 / +0 | 0 | +nan | +0.000 | n/a / n/a / n/a | ok |
| XA3 | CT105m | L6M | +43 / +75 | +0 | -938 / -1641 | +0 | c=1.00: +43 / +0 / -938 | 185 | -0.114 | -0.783 | -0.06 / -0.07 / +0.14 | ok |
| XA3 | CT105p | L3M | -818 / -1431 | +5544 | +703 / +1230 | +1646 | c=1.00: -818 / +5544 / +703 | 158 | +0.050 | +0.612 | +0.15 / -0.14 / +0.06 | ok |
| XA3 | CT105p | L6M | -600 / -1050 | +5424 | -564 / -988 | +1646 | c=1.00: -600 / +5424 / -564 | 307 | -0.037 | -0.423 | +0.07 / -0.04 / -0.08 | ok |
| XA3 | CT14m | L3M | +645 / +1128 | +566 | -714 / -1250 | -914 | c=1.00: +645 / +566 / -714 | 165 | -0.007 | -0.093 | +0.02 / +0.32 / +0.09 | ok |
| XA3 | CT14m | L6M | +390 / +682 | +566 | +203 / +355 | -914 | c=1.00: +390 / +566 / +203 | 359 | +0.019 | +0.259 | +0.03 / +0.23 / -0.11 | ok |
| XA3 | CT14p | L3M | +1785 / +3123 | -2285 | -1447 / -2532 | -3828 | c=1.00: +1785 / -2285 / -1447 | 154 | -0.073 | -0.869 | -0.20 / -0.14 / -0.14 | AMBER |
| XA3 | CT14p | L6M | +1186 / +2076 | -2285 | -651 / -1140 | -3828 | c=1.00: +1186 / -2285 / -651 | 350 | -0.034 | -0.439 | -0.11 / -0.02 / -0.02 | ok |
| XA3 | CT21m | L3M | -1415 / -2477 | +3133 | -528 / -923 | +6197 | c=1.00: -1415 / +3133 / -528 | 136 | -0.017 | -0.178 | -0.02 / -0.19 / -0.15 | ok |
| XA3 | CT21m | L6M | -639 / -1119 | +3133 | -664 / -1161 | +6197 | c=1.00: -639 / +3133 / -664 | 323 | -0.014 | -0.166 | +0.06 / -0.02 / -0.20 | ok |
| XA3 | CT21p | L3M | +2209 / +3865 | -3066 | +308 / +540 | -9155 | c=1.00: +2209 / -3066 / +308 | 169 | +0.009 | +0.114 | -0.10 / -0.17 / -0.06 | AMBER |
| XA3 | CT21p | L6M | +1710 / +2992 | -3850 | -150 / -263 | -9155 | c=1.00: +1710 / -3850 / -150 | 377 | -0.007 | -0.103 | -0.18 / -0.06 / +0.17 | AMBER |
| XA3 | CT28m | L3M | +1337 / +2339 | -3740 | -2041 / -3572 | -3975 | c=1.00: +1337 / -3740 / -2041 | 138 | -0.129 | -1.364 | -0.07 / -0.17 / -0.01 | ok |
| XA3 | CT28m | L6M | +743 / +1301 | -3740 | -875 / -1531 | -3975 | c=1.00: +743 / -3740 / -875 | 326 | -0.040 | -0.488 | -0.02 / -0.06 / -0.04 | ok |
| XA3 | CT28p | L3M | -656 / -1148 | -76 | +1589 / +2781 | +2988 | c=1.00: -656 / -76 / +1589 | 179 | +0.110 | +1.512 | +0.31 / -0.01 / +0.20 | ok |
| XA3 | CT28p | L6M | -26 / -46 | -76 | +471 / +825 | +2988 | c=1.00: -26 / -76 / +471 | 360 | +0.044 | +0.591 | +0.20 / +0.02 / +0.26 | ok |
| XA3 | CT35m | L3M | +1118 / +1956 | -135 | -1048 / -1833 | -4594 | c=1.00: +1118 / -135 / -1048 | 105 | -0.088 | -0.713 | +0.07 / +0.09 / +0.11 | ok |
| XA3 | CT35m | L6M | +742 / +1299 | -135 | -1046 / -1830 | -4594 | c=1.00: +742 / -135 / -1046 | 314 | -0.074 | -0.864 | +0.07 / +0.03 / -0.06 | ok |
| XA3 | CT35p | L3M | +3202 / +5603 | -6386 | -1335 / -2335 | -8754 | c=1.00: +3202 / -6386 / -1335 | 158 | -0.070 | -0.850 | -0.14 / +0.03 / +0.15 | AMBER |
| XA3 | CT35p | L6M | +1971 / +3450 | -6386 | -532 / -931 | -8754 | c=1.00: +1971 / -6386 / -532 | 361 | -0.017 | -0.225 | +0.01 / +0.02 / +0.05 | AMBER |
| XA3 | CT42m | L3M | +2535 / +4436 | +685 | -907 / -1587 | -6475 | c=1.00: +2535 / +685 / -907 | 108 | -0.084 | -0.699 | +0.14 / +0.18 / -0.06 | AMBER |
| XA3 | CT42m | L6M | +1585 / +2774 | +685 | -315 / -551 | -6475 | c=1.00: +1585 / +685 / -315 | 309 | -0.033 | -0.379 | +0.10 / +0.09 / +0.16 | AMBER |
| XA3 | CT42p | L3M | +1585 / +2774 | -2487 | -2302 / -4029 | +1863 | c=1.00: +1585 / -2487 / -2302 | 177 | -0.131 | -1.788 | +0.12 / +0.16 / +0.07 | ok |
| XA3 | CT42p | L6M | +1147 / +2008 | -2487 | -1817 / -3180 | +1863 | c=1.00: +1147 / -2487 / -1817 | 341 | -0.114 | -1.435 | +0.04 / +0.13 / -0.10 | ok |
| XA3 | CT49m | L3M | +1156 / +2024 | -5476 | +140 / +245 | -3811 | c=1.00: +1156 / -5476 / +140 | 87 | +0.059 | +0.393 | -0.06 / -0.21 / +0.05 | ok |
| XA3 | CT49m | L6M | +1253 / +2192 | -5476 | +197 / +345 | -3811 | c=1.00: +1253 / -5476 / +197 | 260 | +0.050 | +0.477 | -0.11 / -0.18 / -0.01 | ok |
| XA3 | CT49p | L3M | +1423 / +2491 | -4891 | -961 / -1681 | -3557 | c=1.00: +1423 / -4891 / -961 | 163 | -0.039 | -0.487 | +0.08 / -0.23 / +0.00 | ok |
| XA3 | CT49p | L6M | +1336 / +2338 | -4891 | -731 / -1279 | -3704 | c=1.00: +1336 / -4891 / -731 | 346 | -0.037 | -0.471 | +0.01 / -0.12 / +0.07 | ok |
| XA3 | CT56m | L3M | +1445 / +2529 | -2606 | -1426 / -2495 | -4843 | c=1.00: +1445 / -2606 / -1426 | 77 | -0.182 | -1.078 | -0.17 / -0.01 / -0.10 | AMBER |
| XA3 | CT56m | L6M | +919 / +1608 | -2606 | -708 / -1239 | -4843 | c=1.00: +919 / -2606 / -708 | 260 | -0.074 | -0.715 | +0.00 / -0.00 / +0.18 | AMBER |
| XA3 | CT56p | L3M | +249 / +436 | -1971 | +803 / +1405 | -462 | c=1.00: +249 / -1971 / +803 | 166 | -0.004 | -0.051 | +0.17 / -0.04 / +0.04 | ok |
| XA3 | CT56p | L6M | +164 / +288 | -1971 | +751 / +1315 | -462 | c=1.00: +164 / -1971 / +751 | 353 | +0.024 | +0.313 | +0.11 / -0.03 / +0.03 | ok |
| XA3 | CT63m | L3M | -48 / -84 | -5 | +1088 / +1905 | +691 | c=1.00: -48 / -5 / +1088 | 66 | +0.149 | +0.759 | +0.09 / +0.01 / +0.20 | ok |
| XA3 | CT63m | L6M | +67 / +117 | -5 | -46 / -80 | +691 | c=1.00: +67 / -5 / -46 | 240 | -0.015 | -0.131 | +0.17 / -0.02 / +0.16 | ok |
| XA3 | CT63p | L3M | +1688 / +2954 | -4640 | -1009 / -1765 | -4896 | c=1.00: +1688 / -4640 / -1009 | 174 | -0.092 | -1.225 | +0.03 / +0.00 / +0.12 | AMBER |
| XA3 | CT63p | L6M | +1027 / +1797 | -4640 | -440 / -769 | -4896 | c=1.00: +1027 / -4640 / -440 | 357 | -0.028 | -0.367 | -0.03 / +0.01 / +0.17 | AMBER |
| XA3 | CT70m | L3M | +29 / +50 | +184 | -133 / -232 | +0 | c=1.00: +29 / +184 / -133 | 51 | -0.120 | -0.470 | +0.28 / +0.20 / +0.22 | ok |
| XA3 | CT70m | L6M | +76 / +134 | +184 | +872 / +1526 | +0 | c=1.00: +76 / +184 / +872 | 228 | +0.064 | +0.536 | +0.07 / +0.21 / +0.17 | ok |
| XA3 | CT70p | L3M | +1109 / +1941 | -4605 | -899 / -1574 | -6964 | c=1.00: +1109 / -4605 / -899 | 160 | +0.007 | +0.080 | +0.27 / +0.03 / -0.02 | AMBER |
| XA3 | CT70p | L6M | +626 / +1096 | -4605 | +223 / +390 | -6964 | c=1.00: +626 / -4605 / +223 | 337 | +0.038 | +0.475 | +0.23 / +0.06 / -0.05 | AMBER |
| XA3 | CT77m | L3M | +158 / +277 | +0 | -1015 / -1777 | -0 | c=1.00: +158 / +0 / -1015 | 52 | -0.223 | -0.893 | -0.12 / +0.02 / -0.04 | ok |
| XA3 | CT77m | L6M | +7 / +12 | +0 | +251 / +439 | +0 | c=1.00: +7 / +0 / +251 | 224 | +0.008 | +0.069 | -0.05 / -0.01 / -0.12 | ok |
| XA3 | CT77p | L3M | +1005 / +1758 | -1919 | +40 / +70 | -1719 | c=1.00: +1005 / -1919 / +40 | 172 | -0.018 | -0.233 | -0.21 / -0.00 / -0.18 | ok |
| XA3 | CT77p | L6M | +424 / +743 | -1919 | +65 / +114 | -1719 | c=1.00: +424 / -1919 / +65 | 362 | -0.008 | -0.101 | -0.10 / -0.05 / -0.08 | ok |
| XA3 | CT7m | L3M | +3169 / +5546 | -4725 | -3438 / -6017 | -11991 | c=1.00: +3169 / -4725 / -3438 | 163 | -0.177 | -2.216 | -0.22 / -0.14 / -0.21 | RED |
| XA3 | CT7m | L6M | +2124 / +3718 | -4725 | -2402 / -4203 | -11991 | c=1.00: +2124 / -4725 / -2402 | 350 | -0.112 | -1.449 | -0.22 / -0.11 / -0.18 | RED |
| XA3 | CT7p | L3M | +1264 / +2212 | -4801 | +782 / +1368 | -3901 | c=1.00: +1264 / -4801 / +782 | 162 | +0.060 | +0.748 | -0.08 / +0.23 / +0.06 | ok |
| XA3 | CT7p | L6M | +673 / +1178 | -4801 | -267 / -468 | -3901 | c=1.00: +673 / -4801 / -267 | 355 | -0.023 | -0.309 | -0.05 / +0.14 / -0.04 | ok |
| XA3 | CT84m | L3M | +57 / +99 | +0 | -129 / -226 | +0 | c=1.00: +57 / +0 / -129 | 23 | -0.048 | -0.084 | -0.05 / +0.15 / -0.07 | ok |
| XA3 | CT84m | L6M | +143 / +250 | +0 | -1554 / -2720 | +0 | c=1.00: +143 / +0 / -1554 | 206 | -0.185 | -1.414 | -0.02 / +0.01 / -0.02 | ok |
| XA3 | CT84p | L3M | +3336 / +5838 | -7311 | -3555 / -6222 | -10513 | c=1.00: +3336 / -7311 / -3555 | 166 | -0.179 | -2.289 | -0.01 / -0.02 / -0.19 | RED |
| XA3 | CT84p | L6M | +2061 / +3607 | -7311 | -2171 / -3798 | -10513 | c=1.00: +2061 / -7311 / -2171 | 329 | -0.137 | -1.673 | +0.00 / -0.01 / +0.01 | RED |
| XA3 | CT91m | L3M | -0 / -1 | +0 | +372 / +651 | +0 | c=1.00: -0 / +0 / +372 | 15 | +0.268 | +0.310 | +0.29 / +0.34 / +0.12 | ok |
| XA3 | CT91m | L6M | -104 / -182 | +0 | +466 / +815 | +0 | c=1.00: -104 / +0 / +466 | 187 | +0.049 | +0.341 | -0.05 / +0.02 / -0.07 | ok |
| XA3 | CT91p | L3M | +2803 / +4905 | -5270 | -2092 / -3661 | -10236 | c=1.00: +2803 / -5270 / -2092 | 161 | -0.116 | -1.441 | +0.02 / +0.10 / +0.01 | RED |
| XA3 | CT91p | L6M | +1722 / +3014 | -5270 | -699 / -1223 | -10236 | c=1.00: +1722 / -5270 / -699 | 320 | -0.040 | -0.477 | +0.08 / +0.03 / +0.06 | RED |
| XA3 | CT98m | L3M | +15 / +26 | +0 | -265 / -463 | -0 | c=1.00: +15 / +0 / -265 | 8 | -0.527 | -0.324 | -0.06 / -0.11 / -0.12 | ok |
| XA3 | CT98m | L6M | +133 / +233 | +0 | -895 / -1566 | +0 | c=1.00: +133 / +0 / -895 | 193 | -0.088 | -0.633 | +0.13 / +0.10 / +0.04 | ok |
| XA3 | CT98p | L3M | +1220 / +2135 | -6715 | +142 / +249 | -3260 | c=1.00: +1220 / -6715 / +142 | 165 | +0.061 | +0.779 | +0.27 / +0.23 / +0.23 | ok |
| XA3 | CT98p | L6M | +911 / +1594 | -6715 | -334 / -585 | -3260 | c=1.00: +911 / -6715 / -334 | 316 | -0.001 | -0.017 | +0.11 / +0.15 / +0.14 | ok |
| XA3 | RK7 | L3M | +303 / +530 | +1651 | +2638 / +4617 | +664 | c=1.00: +303 / +1651 / +2638 | 163 | +0.125 | +1.569 | +0.17 / +0.12 / +0.38 | ok |
| XA3 | RK7 | L6M | +255 / +446 | +1651 | +2505 / +4384 | +664 | c=1.00: +255 / +1651 / +2505 | 382 | +0.123 | +1.742 | +0.14 / +0.08 / +0.16 | ok |
| XA3 | RK7 | Y2023 | +758 / +1327 | -9899 | +404 / +707 | -14123 | c=1.00: +758 / -9899 / +404 | 358 | +0.101 | +0.931 | +0.18 / +0.16 / +0.25 | RED |
| XA3 | RK7 | Y2024 | -5800 / -10150 | +1507 | +860 / +1505 | +15168 | c=1.00: -5800 / +1507 / +860 | 543 | +0.085 | +0.875 | +0.15 / +0.09 / +0.21 | ok |
| XA3 | RK7 | Y2025 | -4169 / -7296 | +7111 | +537 / +940 | +8946 | c=1.00: -4169 / +7111 / +537 | 664 | +0.092 | +1.158 | +0.17 / +0.05 / +0.07 | ok |
| XA3 | RM7 | L3M | -881 / -1542 | +2357 | +965 / +1689 | +4663 | c=1.00: -881 / +2357 / +965 | 164 | +0.131 | +1.655 | +0.20 / +0.12 / +0.39 | ok |
| XA3 | RM7 | L6M | -586 / -1025 | +2357 | +1544 / +2702 | +4663 | c=1.00: -586 / +2357 / +1544 | 383 | +0.123 | +1.749 | +0.15 / +0.09 / +0.16 | ok |
| XA3 | RM7 | Y2023 | -2911 / -5095 | -4913 | +1346 / +2356 | +4364 | c=1.00: -2911 / -4913 / +1346 | 358 | +0.101 | +0.931 | +0.18 / +0.16 / +0.25 | ok |
| XA3 | RM7 | Y2024 | -3883 / -6795 | +3882 | +331 / +578 | +17235 | c=1.00: -3883 / +3882 / +331 | 545 | +0.089 | +0.912 | +0.15 / +0.09 / +0.20 | ok |
| XA3 | RM7 | Y2025 | -5100 / -8924 | +7674 | +755 / +1321 | +9739 | c=1.00: -5100 / +7674 / +755 | 661 | +0.094 | +1.177 | +0.17 / +0.05 / +0.07 | ok |
| XA3 | RP7 | L3M | -1379 / -2413 | +1763 | +1230 / +2152 | +6179 | c=1.00: -1379 / +1763 / +1230 | 165 | +0.127 | +1.616 | +0.20 / +0.13 / +0.39 | ok |
| XA3 | RP7 | L6M | -759 / -1329 | +1763 | +1519 / +2659 | +6179 | c=1.00: -759 / +1763 / +1519 | 384 | +0.122 | +1.730 | +0.15 / +0.09 / +0.16 | ok |
| XA3 | RP7 | Y2023 | +620 / +1084 | -4232 | +786 / +1376 | -6433 | c=1.00: +620 / -4232 / +786 | 358 | +0.101 | +0.931 | +0.18 / +0.16 / +0.25 | AMBER |
| XA3 | RP7 | Y2024 | -5702 / -9979 | +3433 | +1236 / +2163 | +12005 | c=1.00: -5702 / +3433 / +1236 | 541 | +0.086 | +0.876 | +0.15 / +0.09 / +0.21 | ok |
| XA3 | RP7 | Y2025 | -5231 / -9154 | +2936 | +1235 / +2162 | +10482 | c=1.00: -5231 / +2936 / +1235 | 656 | +0.102 | +1.268 | +0.17 / +0.05 / +0.06 | ok |
| XA3 | ADD | L3M | -456 / -798 | +1134 | +1935 / +3386 | +2888 | c=1.00: -456 / +1134 / +1935 | 165 | +0.127 | +1.616 | +0.20 / +0.13 / +0.39 | ok |
| XA3 | ADD | L6M | -262 / -458 | +1134 | +1965 / +3439 | +2888 | c=1.00: -262 / +1134 / +1965 | 383 | +0.125 | +1.767 | +0.15 / +0.08 / +0.16 | ok |
| XA3 | ADD | Y2023 | -468 / -819 | -3097 | +1201 / +2102 | -1427 | c=1.00: -468 / -3097 / +1201 | 358 | +0.101 | +0.931 | +0.18 / +0.16 / +0.25 | ok |
| XA3 | ADD | Y2024 | -5557 / -9725 | +2660 | +938 / +1642 | +12005 | c=1.00: -5557 / +2660 / +938 | 541 | +0.086 | +0.876 | +0.15 / +0.09 / +0.21 | ok |
| XA3 | ADD | Y2025 | -4939 / -8644 | +674 | +1132 / +1981 | +9036 | c=1.00: -4939 / +674 / +1132 | 656 | +0.102 | +1.268 | +0.17 / +0.05 / +0.06 | ok |
| XA4 | ADD | L3M | +97 / +169 | -2550 | -853 / -1492 | +1064 | c=1.00: +97 / -2550 / -853 | 189 | -0.018 | -0.263 | +0.15 / +0.06 / +0.15 | ok |
| XA4 | ADD | L6M | +115 / +200 | -2550 | -244 / -427 | +1064 | c=1.00: +115 / -2550 / -244 | 431 | +0.014 | +0.221 | +0.13 / +0.12 / +0.02 | ok |
| XA5 | ADD | L3M | +4386 / +7675 | -7571 | -2593 / -4538 | -12500 | c=1.00: +4386 / -7571 / -2593 | 261 | -0.102 | -2.046 | +0.06 / +0.07 / +0.19 | RED |
| XA5 | ADD | L6M | +2671 / +4674 | -7571 | +1682 / +2943 | -12500 | c=1.00: +2671 / -7571 / +1682 | 648 | +0.061 | +1.462 | +0.00 / +0.04 / +0.12 | RED |
| XA6 | ADD | L3M | -354 / -620 | +4374 | +740 / +1296 | +2889 | c=1.00: -354 / +4374 / +740 | 219 | +0.063 | +1.067 | +0.33 / +0.13 / +0.09 | ok |
| XA6 | ADD | L6M | -379 / -663 | +4374 | +1774 / +3104 | +2889 | c=1.00: -379 / +4374 / +1774 | 533 | +0.077 | +1.511 | +0.30 / +0.14 / +0.18 | ok |
| XP1 | ADD | L3M | +1067 / +1867 | -5823 | +868 / +1520 | -4561 | c=1.00: +1067 / -5823 / +868 | 178 | +0.059 | +0.813 | +0.24 / -0.01 / +0.16 | ok |
| XP2 | ADD | L3M | +11 / +19 | -1185 | -23 / -40 | +1051 | c=1.00: +11 / -1185 / -23 | 49 | +0.020 | +0.076 | -0.06 / -0.14 / -0.07 | ok |
| XP2 | ADD | L6M | -95 / -167 | -1185 | +290 / +508 | +1051 | c=1.00: -95 / -1185 / +290 | 110 | +0.071 | +0.288 | -0.08 / -0.11 / -0.18 | ok |
| XP3 | ADD | L3M | +1098 / +1921 | -3564 | -161 / -282 | -2573 | c=1.00: +1098 / -3564 / -161 | 79 | -0.007 | -0.040 | +0.06 / -0.02 / +0.43 | ok |
| XP3 | ADD | L6M | +610 / +1068 | -3564 | +475 / +831 | -2573 | c=1.00: +610 / -3564 / +475 | 188 | +0.063 | +0.441 | -0.07 / -0.03 / +0.09 | ok |
| XP5 | ADD | L3M | +111 / +194 | +2052 | +158 / +276 | -1514 | c=1.00: +111 / +2052 / +158 | 170 | +0.028 | +0.361 | +0.17 / -0.13 / +0.04 | ok |
| XP5 | ADD | L6M | +157 / +274 | +381 | +369 / +647 | -1514 | c=1.00: +157 / +381 / +369 | 404 | +0.025 | +0.374 | +0.12 / -0.08 / +0.04 | ok |

## NY PM - HEADLINE: replacement

### A. What the live NY PM books earn now (JL3 itself, this session only; reference, the bar to beat)
Engine base-lot $/week (x1.75 live), ulcer contribution = stack ulcer minus stack ulcer without the book's session trades (positive = the book adds drawdown), worst week of the book, trades. Base lots in this session: K7 2 base lots (4 live).
| window | book | trades | $/wk base (x1.75) | worst wk base (x1.75) | ulcer contribution base (x1.75) | max DD contribution base |
|---|---|---|---|---|---|---|
| L6M | K7 | 168 | +821 (+1436) | -4012 (-7020) | -186 (-325) | +1765 |
| L6M | TOTAL session | 168 | +821 (+1436) | -4012 (-7020) | -186 (-325) | +1765 |
| L3M | K7 | 76 | +247 (+432) | -4012 (-7020) | -219 (-383) | +1765 |
| L3M | TOTAL session | 76 | +247 (+432) | -4012 (-7020) | -219 (-383) | +1765 |
| Y2025 | K7 | 379 | +682 (+1193) | -4676 (-8183) | +2912 (+5097) | -7495 |
| Y2025 | TOTAL session | 379 | +682 (+1193) | -4676 (-8183) | +2912 (+5097) | -7495 |
| Y2024 | K7 | 367 | +381 (+667) | -5949 (-10411) | -2939 (-5142) | -6421 |
| Y2024 | TOTAL session | 367 | +381 (+667) | -5949 (-10411) | -2939 (-5142) | -6421 |
| Y2023 | K7 | 240 | +180 (+315) | -6543 (-11450) | -2823 (-4941) | +13460 |
| Y2023 | TOTAL session | 240 | +180 (+315) | -6543 (-11450) | -2823 (-4941) | +13460 |

Reference row (not a deliverable) "all live NY PM books OFF" (engine set TL3_NYE_OFF_NYPM): L6M d ulcer +186 / d worst -2435 / d max DD -1765 / d mean -812 $/wk

### Headline table (L6M picks by lowest d ulcer among positive d mean; columns = d ulcer / d worst wk / d max DD / d mean $/wk (x1.75))
| row | set | size | L6M | L3M | 2025 | 2024 | 2023 | controls |
|---|---|---|---|---|---|---|---|---|
| live as-is | JL3 | - | 0 / 0 / 0 / 0 | 0 / 0 / 0 / 0 | 0 | 0 | 0 | - |
| best single swap | NYE_WP1_RK7 | risk-matched c=1.00 | +20 / -719 / +621 / +53 (+93) | +16 / -719 / +621 / +9 (+16) | -5228 / -260 / +8837 / -82 (-144) | -1480 / +0 / +2969 / +85 (+148) | +498 / +1628 / -5144 / +315 (+551) | 0 |
| best whole-session replacement | NYE_C2_NYPM_WP1_WP10 | risk-matched c=0.67 | -177 / +2266 / -565 / +146 (+256) | -330 / +2266 / -565 / -356 (-622) | n/a | n/a | n/a | 0 |
| best mixed (keep best live book + new) | NYW_WP10_ADD | risk-matched c=0.50 | -154 / +201 / -35 / +736 (+1287) | -246 / +201 / -35 / +739 (+1292) | -2573 / -1334 / +3290 / +16 (+28) | -837 / -67 / +1856 / +196 (+344) | +1256 / +490 / -3429 / +39 (+68) | 0 |
(Prior-year windows are queued only for the headline sets after the L6M triage; "n/a" = not run yet. Controls = date-shift sets of the same cell run: 0 so far.)

### Bare-vs-engine BRIDGE (L6M and L3M; 1 base lot; ADD sets) - dollars
| cell | bar | trigger | window | bare screen P&L (same dates / bracket) | new book own P&L in the engine | change in OTHER books | entries blocked / exits forced per rule (engine month logs) |
|---|---|---|---|---|---|---|---|
| NP1 | vol_1100 | levels_round.break_native | L6M | +23850 (318 tr) | -30526 (184 tr) | +3238 | blocked: inTrade 634; blocked: SCR gate conj 559; entries 184; exit: UWTime 71; exit: Stop 60; exit note: stack rule Asia-only, no cut 60; exit: Target 52 |
| NP1 | vol_1100 | levels_round.break_native | L3M | +22623 (122 tr) | +4823 (79 tr) | -0 | blocked: inTrade 323; blocked: SCR gate conj 233; entries 79; exit: UWTime 37; exit: Target 25; exit: Stop 17; exit note: stack rule Asia-only, no cut 17 |
| NP2 | vol_1100 | levels_vwap_bands.reject_native | L6M | +35705 (305 tr) | +8702 (167 tr) | -0 | blocked: inTrade 2790; blocked: SCR gate conj 2253; blocked: dayHalt 188; entries 167; exit: UWTime 72; exit: Target 49; exit: Stop 42 |
| NP2 | vol_1100 | levels_vwap_bands.reject_native | L3M | -2613 (123 tr) | +347 (77 tr) | -0 | blocked: inTrade 1453; blocked: SCR gate conj 960; entries 77; blocked: dayHalt 50; exit: UWTime 39; exit: Stop 18; exit note: stack rule Asia-only, no cut 18 |
| NP3 | vol_2600 | levels_zones.reject_native | L6M | +14361 (155 tr) | -11495 (94 tr) | -1195 | blocked: inTrade 287; blocked: SCR gate conj 234; entries 94; exit: UWTime 47; exit: Stop 28; exit note: stack rule Asia-only, no cut 28; exit: Target 19 |
| NP3 | vol_2600 | levels_zones.reject_native | L3M | +7418 (65 tr) | +3846 (36 tr) | -1195 | blocked: inTrade 140; blocked: SCR gate conj 126; entries 36; exit: UWTime 24; exit: Stop 7; exit note: stack rule Asia-only, no cut 7; exit: Target 5 |
| NP4 | tick_800 | levels_round.reject | L6M | +3545 (324 tr) | +10770 (186 tr) | +2458 | blocked: inTrade 1247; blocked: SCR gate conj 1006; entries 186; blocked: dayHalt 136; exit: UWTime 72; exit: Target 59; exit: Stop 51 |
| NP4 | tick_800 | levels_round.reject | L3M | +14175 (119 tr) | +17457 (75 tr) | -0 | blocked: inTrade 636; blocked: SCR gate conj 433; entries 75; exit: UWTime 40; blocked: dayHalt 23; exit: Target 21; exit: Stop 13 |
| NP5 | tick_800 | levels_session_hl.break | L6M | +23147 (214 tr) | +37321 (132 tr) | -0 |  |
| NP5 | tick_800 | levels_session_hl.break | L3M | -439 (85 tr) | +9589 (54 tr) | -0 |  |
| NP6 | rng_10 | levels_profile_nodes.reject | L6M | +25889 (155 tr) | +6689 (85 tr) | -1195 |  |
| NP6 | rng_10 | levels_profile_nodes.reject | L3M | +1438 (66 tr) | -6118 (42 tr) | -1195 |  |
| WP1 | dlt_100 | levels_vwap.reject | L6M | -1076 (334 tr) | +17611 (196 tr) | +67 | blocked: SCR gate conj 147; blocked: inTrade 104; entries 24; exit: Stop 11; exit note: stack rule Asia-only, no cut 11; exit: Target 8; exit: UWTime 4 |
| WP1 | dlt_100 | levels_vwap.reject | L3M | -6829 (132 tr) | -258 (78 tr) | -2390 | blocked: SCR gate conj 147; blocked: inTrade 104; entries 24; exit: Stop 11; exit note: stack rule Asia-only, no cut 11; exit: Target 8; exit: UWTime 4 |
| WP2 | vol_350 | levels_stack.break_native | L6M | +24744 (259 tr) | +10639 (150 tr) | -1195 | blocked: SCR gate conj 576; blocked: inTrade 447; entries 20; exit: Target 7; exit: Stop 6; exit note: stack rule Asia-only, no cut 6; blocked: dayHalt 6 |
| WP2 | vol_350 | levels_stack.break_native | L3M | -8872 (107 tr) | +5345 (64 tr) | -1195 | blocked: SCR gate conj 576; blocked: inTrade 447; entries 20; exit: Target 7; exit: Stop 6; exit note: stack rule Asia-only, no cut 6; blocked: dayHalt 6 |
| WP3 | dol_350 | levels_trendline.break | L6M | +33638 (230 tr) | +20713 (141 tr) | +3238 | blocked: SCR gate conj 199; blocked: inTrade 132; entries 17; exit: UWTime 10; exit: Target 4; exit: Stop 3; exit note: stack rule Asia-only, no cut 3 |
| WP3 | dol_350 | levels_trendline.break | L3M | +340 (95 tr) | +11925 (61 tr) | -0 | blocked: SCR gate conj 199; blocked: inTrade 132; entries 17; exit: UWTime 10; exit: Target 4; exit: Stop 3; exit note: stack rule Asia-only, no cut 3 |
| WP4 | vsess_200 | levels_profile_nodes.reject | L6M | +8183 (134 tr) | -12427 (83 tr) | +0 | blocked: inTrade 192; blocked: SCR gate conj 121; entries 10; exit: UWTime 5; exit: Target 3; exit: Stop 2; exit note: stack rule Asia-only, no cut 2 |
| WP4 | vsess_200 | levels_profile_nodes.reject | L3M | -6021 (60 tr) | -12714 (38 tr) | +0 | blocked: inTrade 192; blocked: SCR gate conj 121; entries 10; exit: UWTime 5; exit: Target 3; exit: Stop 2; exit note: stack rule Asia-only, no cut 2 |
| WP5 | vsess_450 | manual_macd.sigcross_native | L6M | +11747 (327 tr) | -19162 (177 tr) | -1195 | blocked: SCR gate conj 559; blocked: inTrade 503; entries 21; blocked: dayHalt 11; exit: UWTime 10; exit: Stop 9; exit note: stack rule Asia-only, no cut 9 |
| WP5 | vsess_450 | manual_macd.sigcross_native | L3M | +6083 (129 tr) | -3213 (77 tr) | -1195 | blocked: SCR gate conj 559; blocked: inTrade 503; entries 21; blocked: dayHalt 11; exit: UWTime 10; exit: Stop 9; exit note: stack rule Asia-only, no cut 9 |
| WP6 | rng_56 | manual_squeeze.momturn | L6M | -26071 (263 tr) | -10132 (142 tr) | -946 | blocked: SCR gate conj 27; entries 22; exit: Stop 12; exit note: stack rule Asia-only, no cut 12; exit: Target 8; exit: UWTime 2; blocked: inTrade 1 |
| WP6 | rng_56 | manual_squeeze.momturn | L3M | -5260 (101 tr) | -4651 (57 tr) | -2390 | blocked: SCR gate conj 27; entries 22; exit: Stop 12; exit note: stack rule Asia-only, no cut 12; exit: Target 8; exit: UWTime 2; blocked: inTrade 1 |
| WP8 | vol_500 | manual_macd.sigcross | L6M | +16176 (342 tr) | +148 (175 tr) | -1195 | blocked: SCR gate conj 508; blocked: inTrade 469; blocked: dayHalt 28; entries 21; exit: UWTime 10; exit: Stop 8; exit note: stack rule Asia-only, no cut 8 |
| WP8 | vol_500 | manual_macd.sigcross | L3M | +17608 (127 tr) | +16577 (73 tr) | -1195 | blocked: SCR gate conj 508; blocked: inTrade 469; blocked: dayHalt 28; entries 21; exit: UWTime 10; exit: Stop 8; exit note: stack rule Asia-only, no cut 8 |
| WP10 | vol_350 | tape_libvol.cmf | L6M | +5101 (411 tr) | +42116 (227 tr) | -1195 | blocked: SCR gate conj 1009; blocked: inTrade 908; blocked: dayHalt 53; entries 34; exit: Target 17; exit: UWTime 10; exit: Stop 7 |
| WP10 | vol_350 | tape_libvol.cmf | L3M | +26289 (174 tr) | +21593 (110 tr) | -1195 | blocked: SCR gate conj 1009; blocked: inTrade 908; blocked: dayHalt 53; entries 34; exit: Target 17; exit: UWTime 10; exit: Stop 7 |
| WP11 | tm1800 | xmarket_ym.follow | L6M | +18071 (171 tr) | +9318 (110 tr) | -1477 | entries 15; blocked: SCR gate conj 14; exit: Stop 6; exit note: stack rule Asia-only, no cut 6; exit: Target 6; exit: UWTime 3 |
| WP11 | tm1800 | xmarket_ym.follow | L3M | +12873 (75 tr) | +1178 (49 tr) | -1477 | entries 15; blocked: SCR gate conj 14; exit: Stop 6; exit note: stack rule Asia-only, no cut 6; exit: Target 6; exit: UWTime 3 |
| XP2 | tm1800 | xmarket_ym.follow | L6M | +18071 (171 tr) | +9318 (110 tr) | -1477 | entries 110; blocked: SCR gate conj 65; exit: Target 48; exit: Stop 44; exit note: stack rule Asia-only, no cut 44; exit: UWTime 18; blocked: inTrade 10 |
| XP2 | tm1800 | xmarket_ym.follow | L3M | +12873 (75 tr) | +1178 (49 tr) | -1477 | entries 49; blocked: SCR gate conj 26; exit: Stop 20; exit note: stack rule Asia-only, no cut 20; exit: Target 19; exit: UWTime 10; blocked: inTrade 3 |
| XP3 | tm900 | xmarket_es.follow | L3M | +17676 (125 tr) | -617 (79 tr) | -1477 | entries 79; blocked: SCR gate conj 55; exit: Stop 34; exit note: stack rule Asia-only, no cut 34; exit: Target 34; blocked: inTrade 27; exit: UWTime 8 |
| XP3 | tm900 | xmarket_es.follow | L6M | +22290 (312 tr) | +14295 (188 tr) | -1477 | entries 188; blocked: SCR gate conj 138; exit: Target 90; exit: Stop 75; exit note: stack rule Asia-only, no cut 75; blocked: inTrade 65; exit: UWTime 17 |
| XP5 | time_s_20 | bands_atrchan.break_ext | L6M | +25695 (875 tr) | +12110 (404 tr) | -2134 | blocked: inTrade 6326; blocked: SCR gate conj 4805; blocked: dayHalt 970; entries 404; exit: Target 175; exit: Stop 159; exit note: stack rule Asia-only, no cut 159 |
| XP5 | time_s_20 | bands_atrchan.break_ext | L3M | +14223 (322 tr) | +5627 (170 tr) | -3579 | blocked: inTrade 3410; blocked: SCR gate conj 2388; blocked: dayHalt 291; entries 170; exit: Target 69; exit: Stop 63; exit note: stack rule Asia-only, no cut 63 |
| XP1 | dib_400 | tape_libvol.cmf | L3M | +16264 (357 tr) | +12683 (178 tr) | -1393 | blocked: inTrade 9271; blocked: SCR gate conj 7369; blocked: dayHalt 1579; entries 178; exit: Target 77; exit: Stop 64; exit note: stack rule Asia-only, no cut 64 |

### All sets (detail)
| cell | variant | window | d ulcer (x1 / x1.75) | d worst wk | d mean $/wk (x1 / x1.75) | d max DD | RISK-MATCHED c: d ulcer / d worst / d mean | new-book trades | R/trade | R/wk | corr daily w/ K7 / P7 / M7 | flag vs JL3 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NP1 | CT | L3M | +124 / +217 | +5161 | +1425 / +2494 | -3014 | c=0.56: -104 / +2894 / +770 | 123 | +0.074 | +0.696 | +0.06 / n/a / n/a | ok |
| NP1 | CT | L6M | +166 / +290 | +1625 | -375 / -657 | -3014 | c=0.56: -139 / +2808 / -148 | 294 | -0.022 | -0.241 | +0.10 / n/a / n/a | ok |
| NP1 | ADD | L3M | +297 / +520 | +2658 | +371 / +649 | -60 | c=0.56: +138 / +2867 / +208 | 79 | +0.029 | +0.173 | +0.09 / n/a / n/a | ok |
| NP1 | ADD | L6M | +400 / +701 | -996 | -1011 / -1769 | -60 | c=0.56: +180 / +1338 / -514 | 184 | -0.078 | -0.528 | +0.16 / n/a / n/a | ok |
| NP1 | BARE | L3M | +147 / +256 | +5161 | +1351 / +2364 | -3014 | c=0.56: -96 / +2894 / +729 | 124 | +0.069 | +0.662 | +0.06 / n/a / n/a | ok |
| NP1 | BARE | L6M | +22 / +39 | +1625 | +217 / +380 | -3014 | c=0.56: -243 / +2808 / +184 | 315 | +0.003 | +0.036 | +0.14 / n/a / n/a | ok |
| NP1 | RK7 | L3M | +147 / +257 | +4631 | +287 / +502 | -578 | c=0.56: +3 / +1528 / +52 | 78 | +0.042 | +0.249 | +0.10 / n/a / n/a | ok |
| NP1 | RK7 | L6M | +445 / +779 | -2513 | -1790 / -3132 | -578 | c=0.56: +212 / -178 / -1360 | 181 | -0.068 | -0.457 | +0.16 / n/a / n/a | ok |
| NP2 | ADD | L3M | +498 / +872 | +2318 | +27 / +47 | -1209 | c=0.55: +216 / +2684 / +15 | 77 | +0.002 | +0.012 | -0.14 / n/a / n/a | ok |
| NP2 | ADD | L6M | +329 / +577 | +239 | +322 / +564 | -1209 | c=0.55: +138 / +2068 / +178 | 167 | +0.024 | +0.148 | -0.22 / n/a / n/a | ok |
| NP2 | ALL | L3M | +342 / +599 | +2941 | -36 / -62 | -1728 | c=1.10: +412 / +3497 / -14 | 78 | +0.016 | +0.097 | -0.13 / n/a / n/a | ok |
| NP2 | ALL | L6M | +334 / +584 | -1278 | -401 / -702 | -1728 | c=1.10: +392 / -1700 / -359 | 168 | +0.030 | +0.189 | -0.22 / n/a / n/a | ok |
| NP2 | RK7 | L3M | +342 / +599 | +2941 | -36 / -62 | -1728 | c=0.55: +81 / +531 / -130 | 78 | +0.016 | +0.097 | -0.13 / n/a / n/a | ok |
| NP2 | RK7 | L6M | +334 / +584 | -1278 | -401 / -702 | -1728 | c=0.55: +122 / +531 / -586 | 168 | +0.030 | +0.189 | -0.22 / n/a / n/a | ok |
| NP3 | ADD | L3M | -78 / -137 | -10 | +204 / +357 | +475 | c=0.50: -53 / -5 / +56 | 36 | +0.045 | +0.123 | +0.04 / n/a / n/a | ok |
| NP3 | ADD | L6M | +129 / +226 | -10 | -470 / -823 | +475 | c=0.50: +47 / -5 / -257 | 94 | -0.051 | -0.177 | +0.01 / n/a / n/a | ok |
| NP3 | RK7 | L3M | -77 / -134 | -2444 | -135 / -236 | -361 | c=0.50: -85 / -2439 / -191 | 37 | +0.016 | +0.047 | +0.03 / n/a / n/a | ok |
| NP3 | RK7 | L6M | +203 / +355 | -2444 | -1327 / -2322 | -361 | c=0.50: +83 / -2439 / -1070 | 95 | -0.061 | -0.214 | +0.00 / n/a / n/a | ok |
| NP4 | ADD | L3M | +128 / +224 | +2076 | +1343 / +2350 | -299 | c=0.53: +38 / +1102 / +713 | 75 | +0.103 | +0.594 | +0.13 / n/a / n/a | ok |
| NP4 | ADD | L6M | +138 / +242 | +2076 | +490 / +857 | -299 | c=0.53: +16 / +1102 / +303 | 186 | +0.026 | +0.176 | +0.12 / n/a / n/a | ok |
| NP4 | ALL | L3M | +3 / +6 | -359 | +1096 / +1918 | -818 | c=1.06: +16 / -230 / +1179 | 75 | +0.103 | +0.594 | +0.13 / n/a / n/a | ok |
| NP4 | ALL | L6M | +134 / +235 | -359 | -346 / -605 | -818 | c=1.06: +154 / -230 / -317 | 184 | +0.030 | +0.207 | +0.12 / n/a / n/a | ok |
| NP4 | RK7 | L3M | +3 / +6 | -359 | +1096 / +1918 | -818 | c=0.53: -82 / -1332 / +466 | 75 | +0.103 | +0.594 | +0.13 / n/a / n/a | ok |
| NP4 | RK7 | L6M | +134 / +235 | -359 | -346 / -605 | -818 | c=0.53: +1 / -1332 / -564 | 184 | +0.030 | +0.207 | +0.12 / n/a / n/a | ok |
| NP5 | CT | L3M | +1243 / +2175 | -4089 | +26 / +46 | -3142 | c=0.50: +263 / -2044 / +13 | 85 | +0.002 | +0.011 | +0.09 / n/a / n/a | ok |
| NP5 | CT | L6M | +970 / +1697 | -4089 | +871 / +1525 | -3142 | c=0.50: +184 / -2044 / +375 | 213 | +0.052 | +0.413 | +0.16 / n/a / n/a | ok |
| NP5 | ADD | L3M | +330 / +577 | -2034 | +738 / +1291 | -359 | c=0.50: +57 / -1017 / +369 | 54 | +0.074 | +0.307 | +0.12 / n/a / n/a | ok |
| NP5 | ADD | L6M | +242 / +423 | -2034 | +1382 / +2419 | -359 | c=0.50: +56 / -1017 / +691 | 132 | +0.118 | +0.576 | +0.20 / n/a / n/a | ok |
| NP5 | ALL | L3M | +636 / +1113 | -4469 | +491 / +859 | -2451 | c=1.00: +636 / -4469 / +491 | 54 | +0.074 | +0.307 | +0.12 / n/a / n/a | ok |
| NP5 | ALL | L6M | +495 / +866 | -4469 | +570 / +997 | -2451 | c=1.00: +495 / -4469 / +570 | 132 | +0.118 | +0.576 | +0.20 / n/a / n/a | ok |
| NP5 | BARE | L3M | +1243 / +2175 | -4089 | +26 / +46 | -3142 | c=0.50: +263 / -2044 / +13 | 85 | +0.002 | +0.011 | +0.09 / n/a / n/a | ok |
| NP5 | BARE | L6M | +884 / +1547 | -4089 | +931 / +1629 | -3142 | c=0.50: +142 / -2044 / +405 | 214 | +0.055 | +0.438 | +0.16 / n/a / n/a | ok |
| NP5 | CT14m | L3M | +838 / +1466 | -2370 | -1723 / -3015 | -1889 | c=0.50: +144 / -1185 / -858 | 45 | -0.208 | -0.720 | +0.04 / n/a / n/a | ok |
| NP5 | CT14m | L6M | +572 / +1000 | -2370 | -1258 / -2201 | -1889 | c=0.50: +60 / -1185 / -627 | 106 | -0.134 | -0.525 | +0.04 / n/a / n/a | ok |
| NP5 | CT14p | L3M | +356 / +622 | -2815 | -268 / -469 | -519 | c=0.50: +99 / -1407 / -134 | 59 | -0.025 | -0.112 | +0.00 / n/a / n/a | ok |
| NP5 | CT14p | L6M | +402 / +703 | -2815 | -434 / -760 | -519 | c=0.50: +135 / -1407 / -157 | 132 | -0.047 | -0.231 | -0.06 / n/a / n/a | ok |
| NP5 | CT21m | L3M | +137 / +240 | +261 | -31 / -55 | -605 | c=0.50: -141 / +130 / -97 | 56 | +0.013 | +0.054 | -0.40 / n/a / n/a | ok |
| NP5 | CT21m | L6M | +238 / +417 | +261 | -997 / -1745 | -605 | c=0.50: -25 / +130 / -511 | 127 | -0.086 | -0.405 | -0.25 / n/a / n/a | ok |
| NP5 | CT21p | L3M | -46 / -80 | -1989 | -1326 / -2320 | -165 | c=0.50: -38 / -995 / -709 | 49 | -0.136 | -0.514 | -0.33 / n/a / n/a | ok |
| NP5 | CT21p | L6M | +40 / +70 | -1989 | -1101 / -1927 | -165 | c=0.50: -60 / -995 / -573 | 136 | -0.087 | -0.440 | -0.25 / n/a / n/a | ok |
| NP5 | CT28m | L3M | -145 / -253 | +3133 | -427 / -747 | +815 | c=0.50: -82 / +3133 / -111 | 37 | -0.093 | -0.263 | -0.27 / n/a / n/a | ok |
| NP5 | CT28m | L6M | -15 / -27 | +3039 | +684 / +1197 | +815 | c=0.50: -20 / +3133 / +418 | 100 | +0.060 | +0.222 | +0.18 / n/a / n/a | ok |
| NP5 | CT28p | L3M | +491 / +860 | +40 | -600 / -1050 | -285 | c=0.50: +89 / +20 / -346 | 54 | -0.051 | -0.212 | +0.09 / n/a / n/a | ok |
| NP5 | CT28p | L6M | +296 / +518 | +40 | -441 / -772 | -285 | c=0.50: +30 / +20 / -243 | 123 | -0.036 | -0.165 | +0.16 / n/a / n/a | ok |
| NP5 | CT35m | L3M | +1194 / +2090 | -580 | -491 / -860 | -4554 | c=0.50: +120 / -290 / -299 | 40 | -0.052 | -0.160 | -0.02 / n/a / n/a | ok |
| NP5 | CT35m | L6M | +713 / +1248 | -580 | -694 / -1215 | -4554 | c=0.50: +68 / -290 / -373 | 103 | -0.070 | -0.268 | -0.21 / n/a / n/a | ok |
| NP5 | CT35p | L3M | +368 / +644 | +1631 | +349 / +610 | -1795 | c=0.50: +171 / +815 / +174 | 49 | +0.039 | +0.145 | +0.09 / n/a / n/a | ok |
| NP5 | CT35p | L6M | +132 / +231 | +1631 | +530 / +927 | -1795 | c=0.50: +44 / +815 / +265 | 130 | +0.046 | +0.221 | +0.05 / n/a / n/a | ok |
| NP5 | CT7m | L3M | -206 / -360 | +1010 | -337 / -591 | +135 | c=0.50: -114 / +505 / -169 | 52 | -0.035 | -0.141 | +0.27 / n/a / n/a | ok |
| NP5 | CT7m | L6M | -211 / -369 | +1010 | +940 / +1645 | +135 | c=0.50: -127 / +505 / +470 | 120 | +0.088 | +0.392 | +0.26 / n/a / n/a | ok |
| NP5 | CT7p | L3M | -170 / -298 | +3663 | +1585 / +2774 | +350 | c=0.50: -95 / +3398 / +746 | 55 | +0.165 | +0.699 | +0.02 / n/a / n/a | ok |
| NP5 | CT7p | L6M | -80 / -141 | +3663 | -23 / -40 | +350 | c=0.50: -55 / +3398 / -33 | 127 | +0.002 | +0.009 | -0.01 / n/a / n/a | ok |
| NP5 | RK7 | L3M | +636 / +1113 | -4469 | +491 / +859 | -2451 | c=0.50: +289 / -3452 / +122 | 54 | +0.074 | +0.307 | +0.12 / n/a / n/a | ok |
| NP5 | RK7 | L6M | +495 / +866 | -4469 | +570 / +997 | -2451 | c=0.50: +258 / -3452 / -121 | 132 | +0.118 | +0.576 | +0.20 / n/a / n/a | ok |
| NP5:NP6 | C2 | L3M | +970 / +1697 | -3579 | +760 / +1329 | -4963 | c=0.70: +641 / -3230 / +453 | 0 | +nan | +0.583 | +0.21 / n/a / n/a | AMBER |
| NP5:NP6 | C2 | L6M | +614 / +1075 | -3579 | +547 / +957 | -4963 | c=0.70: +400 / -3230 / +133 | 0 | +nan | +0.788 | +0.05 / n/a / n/a | AMBER |
| NP6 | ADD | L3M | +1036 / +1813 | -574 | -563 / -985 | -4464 | c=1.14: +1200 / -656 / -630 | 42 | -0.139 | -0.448 | +0.29 / n/a / n/a | ok |
| NP6 | ADD | L6M | +729 / +1275 | -574 | +203 / +356 | -4464 | c=1.14: +851 / -1092 / +239 | 85 | +0.075 | +0.236 | +0.21 / n/a / n/a | ok |
| NP6 | ALL | L3M | +923 / +1615 | -3009 | -717 / -1255 | -4983 | c=2.29: +2573 / -3747 / -1322 | 42 | -0.139 | -0.448 | +0.29 / n/a / n/a | AMBER |
| NP6 | ALL | L6M | +733 / +1283 | -3009 | -565 / -988 | -4983 | c=2.29: +2143 / -8020 / -246 | 85 | +0.075 | +0.236 | +0.21 / n/a / n/a | AMBER |
| NP6 | RK7 | L3M | +923 / +1615 | -3009 | -717 / -1255 | -4983 | c=1.14: +1088 / -3091 / -784 | 42 | -0.139 | -0.448 | +0.29 / n/a / n/a | AMBER |
| NP6 | RK7 | L6M | +733 / +1283 | -3009 | -565 / -988 | -4983 | c=1.14: +861 / -3091 / -529 | 85 | +0.075 | +0.236 | +0.21 / n/a / n/a | AMBER |
| WP1 | CT | L3M | +247 / +433 | +2291 | -36 / -63 | +1397 | c=1.00: +247 / +2291 / -36 | 134 | +0.004 | +0.037 | -0.07 / n/a / n/a | ok |
| WP1 | CT | L6M | -139 / -244 | +2291 | +639 / +1118 | +1397 | c=1.00: -139 / +2291 / +639 | 319 | +0.037 | +0.441 | +0.08 / n/a / n/a | ok |
| WP1 | ALL | L3M | +16 / +29 | -719 | +9 / +16 | +621 | c=2.00: -70 / +997 / +265 | 83 | +0.033 | +0.213 | -0.09 / n/a / n/a | ok |
| WP1 | ALL | L6M | +20 / +34 | -719 | +53 / +93 | +621 | c=2.00: -10 / +997 / +919 | 198 | +0.098 | +0.721 | +0.08 / n/a / n/a | ok |
| WP1 | ALL | Y2023 | +498 / +872 | +1628 | +315 / +551 | -5144 | c=2.00: -973 / -1688 / +809 | 257 | +0.063 | +0.412 | +0.03 / n/a / n/a | ok |
| WP1 | ALL | Y2024 | -1480 / -2590 | +0 | +85 / +148 | +2969 | c=2.00: -2425 / +0 / +531 | 379 | +0.052 | +0.372 | +0.09 / n/a / n/a | ok |
| WP1 | ALL | Y2025 | -5228 / -9150 | -260 | -82 / -144 | +8837 | c=2.00: -7030 / -1933 / +517 | 393 | +0.067 | +0.500 | -0.04 / n/a / n/a | ok |
| WP1 | BARE | L3M | +247 / +433 | +2291 | -36 / -63 | +1397 | c=1.00: +247 / +2291 / -36 | 134 | +0.004 | +0.037 | -0.07 / n/a / n/a | ok |
| WP1 | BARE | L6M | -96 / -168 | +2291 | +462 / +809 | +1397 | c=1.00: -96 / +2291 / +462 | 323 | +0.025 | +0.294 | +0.09 / n/a / n/a | ok |
| WP1 | CT14m | L3M | +155 / +272 | -1470 | -599 / -1048 | -13 | c=1.00: +155 / -1470 / -599 | 69 | -0.059 | -0.313 | +0.03 / n/a / n/a | ok |
| WP1 | CT14m | L6M | +169 / +295 | -1470 | -252 / -440 | -13 | c=1.00: +169 / -1470 / -252 | 164 | -0.020 | -0.120 | +0.06 / n/a / n/a | ok |
| WP1 | CT14p | L3M | +502 / +878 | -5494 | -2312 / -4046 | -467 | c=1.00: +502 / -5494 / -2312 | 79 | -0.292 | -1.774 | -0.27 / n/a / n/a | ok |
| WP1 | CT14p | L6M | +262 / +459 | -5494 | -828 / -1449 | -467 | c=1.00: +262 / -5494 / -828 | 191 | -0.087 | -0.616 | -0.04 / n/a / n/a | ok |
| WP1 | CT21m | L3M | -227 / -398 | +3133 | -1032 / -1806 | +1245 | c=1.00: -227 / +3133 / -1032 | 66 | -0.122 | -0.620 | +0.02 / n/a / n/a | ok |
| WP1 | CT21m | L6M | -140 / -245 | +3133 | -1473 / -2578 | +1245 | c=1.00: -140 / +3133 / -1473 | 167 | -0.180 | -1.112 | -0.08 / n/a / n/a | ok |
| WP1 | CT21p | L3M | +537 / +940 | +1216 | -50 / -87 | -1600 | c=1.00: +537 / +1216 / -50 | 83 | +0.023 | +0.144 | -0.08 / n/a / n/a | ok |
| WP1 | CT21p | L6M | +271 / +475 | +1216 | +496 / +868 | -1600 | c=1.00: +271 / +1216 / +496 | 199 | +0.068 | +0.503 | -0.06 / n/a / n/a | ok |
| WP1 | CT28m | L3M | +779 / +1363 | +3133 | +331 / +579 | -3894 | c=1.00: +779 / +3133 / +331 | 73 | +0.039 | +0.219 | -0.15 / n/a / n/a | ok |
| WP1 | CT28m | L6M | +415 / +727 | +3133 | +323 / +566 | -3894 | c=1.00: +415 / +3133 / +323 | 172 | +0.038 | +0.242 | -0.01 / n/a / n/a | ok |
| WP1 | CT28p | L3M | +221 / +386 | +0 | -417 / -729 | -1270 | c=1.00: +221 / +0 / -417 | 72 | -0.032 | -0.175 | -0.04 / n/a / n/a | ok |
| WP1 | CT28p | L6M | +179 / +313 | +0 | -417 / -730 | -1270 | c=1.00: +179 / +0 / -417 | 173 | -0.041 | -0.264 | -0.04 / n/a / n/a | ok |
| WP1 | CT35m | L3M | -68 / -119 | +136 | -125 / -219 | +1136 | c=1.00: -68 / +136 / -125 | 51 | -0.003 | -0.012 | +0.17 / n/a / n/a | ok |
| WP1 | CT35m | L6M | -9 / -17 | +136 | -124 / -218 | +1136 | c=1.00: -9 / +136 / -124 | 176 | -0.009 | -0.059 | +0.15 / n/a / n/a | ok |
| WP1 | CT35p | L3M | -191 / -335 | -804 | -486 / -851 | -0 | c=1.00: -191 / -804 / -486 | 70 | -0.041 | -0.219 | -0.16 / n/a / n/a | ok |
| WP1 | CT35p | L6M | -128 / -224 | -804 | -102 / -178 | +0 | c=1.00: -128 / -804 / -102 | 178 | -0.006 | -0.040 | -0.08 / n/a / n/a | ok |
| WP1 | CT7m | L3M | -38 / -67 | +1335 | +1778 / +3112 | -220 | c=1.00: -38 / +1335 / +1778 | 78 | +0.245 | +1.469 | -0.03 / n/a / n/a | ok |
| WP1 | CT7m | L6M | +34 / +59 | +1335 | +598 / +1047 | -220 | c=1.00: +34 / +1335 / +598 | 166 | +0.080 | +0.492 | -0.05 / n/a / n/a | ok |
| WP1 | CT7p | L3M | -245 / -428 | +836 | -920 / -1610 | +1395 | c=1.00: -245 / +836 / -920 | 90 | -0.106 | -0.734 | -0.46 / n/a / n/a | ok |
| WP1 | CT7p | L6M | +32 / +55 | -375 | -773 / -1353 | +1395 | c=1.00: +32 / -375 / -773 | 170 | -0.100 | -0.628 | -0.38 / n/a / n/a | ok |
| WP1 | RK7 | L3M | +16 / +29 | -719 | +9 / +16 | +621 | c=1.00: +16 / -719 / +9 | 83 | +0.033 | +0.213 | -0.09 / n/a / n/a | ok |
| WP1 | RK7 | L6M | +20 / +34 | -719 | +53 / +93 | +621 | c=1.00: +20 / -719 / +53 | 198 | +0.098 | +0.721 | +0.08 / n/a / n/a | ok |
| WP1 | RK7 | Y2023 | +498 / +872 | +1628 | +315 / +551 | -5144 | c=1.00: +498 / +1628 / +315 | 257 | +0.063 | +0.412 | +0.03 / n/a / n/a | ok |
| WP1 | RK7 | Y2024 | -1480 / -2590 | +0 | +85 / +148 | +2969 | c=1.00: -1480 / +0 / +85 | 379 | +0.052 | +0.372 | +0.09 / n/a / n/a | ok |
| WP1 | RK7 | Y2025 | -5228 / -9150 | -260 | -82 / -144 | +8837 | c=1.00: -5228 / -260 / -82 | 393 | +0.067 | +0.500 | -0.04 / n/a / n/a | ok |
| WP1 | ADD | L3M | -176 / -309 | +1716 | -204 / -356 | +2390 | c=1.00: -176 / +1716 / -204 | 78 | -0.003 | -0.017 | -0.10 / n/a / n/a | ok |
| WP1 | ADD | L6M | -132 / -231 | +1716 | +655 / +1146 | +2390 | c=1.00: -132 / +1716 / +655 | 196 | +0.075 | +0.544 | +0.08 / n/a / n/a | ok |
| WP1 | ADD | Y2023 | -1192 / -2087 | -1209 | +519 / +909 | -1980 | c=1.00: -1192 / -1209 / +519 | 257 | +0.063 | +0.412 | +0.03 / n/a / n/a | ok |
| WP1 | ADD | Y2024 | -2028 / -3550 | +0 | +352 / +616 | -2143 | c=1.00: -2028 / +0 / +352 | 369 | +0.047 | +0.325 | +0.07 / n/a / n/a | ok |
| WP1 | ADD | Y2025 | -2839 / -4968 | +805 | +604 / +1056 | +1552 | c=1.00: -2839 / +805 / +604 | 392 | +0.065 | +0.482 | -0.03 / n/a / n/a | ok |
| WP10 | CT | L3M | -787 / -1377 | +2086 | +2266 / +3966 | +2851 | c=0.50: -455 / +593 / +1168 | 172 | +0.069 | +0.915 | -0.12 / n/a / n/a | ok |
| WP10 | CT | L6M | -710 / -1242 | +2086 | +2307 / +4037 | +2851 | c=0.50: -572 / +593 / +1307 | 367 | +0.061 | +0.833 | -0.13 / n/a / n/a | ok |
| WP10 | ALL | L3M | +181 / +316 | -2034 | +1234 / +2160 | -3029 | c=1.00: +181 / -2034 / +1234 | 111 | +0.072 | +0.617 | -0.12 / n/a / n/a | ok |
| WP10 | ALL | L6M | +188 / +329 | -2034 | +661 / +1156 | -3029 | c=1.00: +188 / -2034 / +661 | 228 | +0.073 | +0.614 | -0.15 / n/a / n/a | ok |
| WP10 | ALL | Y2023 | +7553 / +13218 | -11 | -96 / -168 | -20935 | c=1.00: +7553 / -11 / -96 | 444 | +0.003 | +0.035 | -0.23 / n/a / n/a | RED |
| WP10 | ALL | Y2024 | +6277 / +10984 | -135 | +74 / +130 | +1946 | c=1.00: +6277 / -135 / +74 | 589 | +0.016 | +0.182 | -0.41 / n/a / n/a | AMBER |
| WP10 | ALL | Y2025 | -5872 / -10276 | -2604 | -662 / -1158 | +818 | c=1.00: -5872 / -2604 / -662 | 531 | +0.001 | +0.008 | -0.28 / n/a / n/a | ok |
| WP10 | BARE | L3M | -771 / -1349 | +2086 | +2351 / +4114 | +2851 | c=0.50: -449 / +593 / +1210 | 177 | +0.070 | +0.950 | -0.12 / n/a / n/a | ok |
| WP10 | BARE | L6M | -429 / -751 | +2086 | +1965 / +3439 | +2851 | c=0.50: -551 / +593 / +1136 | 381 | +0.049 | +0.691 | -0.22 / n/a / n/a | ok |
| WP10 | CT105m | L3M | +0 / +0 | +0 | +0 / +0 | +0 | c=0.50: +0 / +0 / +0 | 0 | +nan | +0.000 | n/a / n/a / n/a | ok |
| WP10 | CT105m | L6M | +17 / +30 | +0 | +424 / +743 | +0 | c=0.50: -20 / +0 / +212 | 161 | +0.030 | +0.177 | -0.02 / n/a / n/a | ok |
| WP10 | CT105p | L3M | +1024 / +1793 | +2313 | -443 / -775 | -2595 | c=0.50: +508 / +2723 / -248 | 77 | -0.027 | -0.163 | +0.08 / n/a / n/a | ok |
| WP10 | CT105p | L6M | +1051 / +1840 | -5817 | -245 / -429 | -2595 | c=0.50: +627 / -3692 / -265 | 205 | +0.002 | +0.016 | +0.11 / n/a / n/a | ok |
| WP10 | CT14m | L3M | +209 / +366 | +2893 | -287 / -501 | +1091 | c=0.50: +1 / +1915 / -86 | 99 | -0.022 | -0.167 | +0.04 / n/a / n/a | ok |
| WP10 | CT14m | L6M | +129 / +226 | +2893 | +207 / +362 | +1091 | c=0.50: +0 / +1915 / +131 | 226 | +0.008 | +0.063 | -0.08 / n/a / n/a | ok |
| WP10 | CT14p | L3M | -131 / -228 | +3666 | +150 / +263 | +10 | c=0.50: -108 / +1833 / +121 | 99 | +0.003 | +0.024 | +0.06 / n/a / n/a | ok |
| WP10 | CT14p | L6M | +280 / +490 | -2135 | +89 / +155 | +10 | c=0.50: +52 / +1092 / +104 | 216 | -0.002 | -0.013 | +0.12 / n/a / n/a | ok |
| WP10 | CT21m | L3M | +227 / +397 | -2479 | -2391 / -4185 | -9 | c=0.50: +50 / -1239 / -1379 | 90 | -0.122 | -0.843 | +0.09 / n/a / n/a | ok |
| WP10 | CT21m | L6M | +239 / +419 | -2479 | -712 / -1245 | -9 | c=0.50: +71 / -1239 / -418 | 229 | -0.029 | -0.245 | -0.13 / n/a / n/a | ok |
| WP10 | CT21p | L3M | +84 / +147 | +4216 | -681 / -1191 | +906 | c=0.50: +23 / +2108 / -386 | 98 | -0.033 | -0.245 | +0.19 / n/a / n/a | ok |
| WP10 | CT21p | L6M | +188 / +329 | +4216 | -623 / -1089 | +906 | c=0.50: +28 / +2108 / -333 | 226 | -0.029 | -0.241 | -0.03 / n/a / n/a | ok |
| WP10 | CT28m | L3M | +227 / +396 | -4369 | -596 / -1043 | +363 | c=0.50: -165 / -2185 / -282 | 90 | -0.038 | -0.262 | -0.35 / n/a / n/a | ok |
| WP10 | CT28m | L6M | +98 / +171 | -4369 | -212 / -371 | +363 | c=0.50: -121 / -2185 / -98 | 218 | -0.012 | -0.095 | -0.21 / n/a / n/a | ok |
| WP10 | CT28p | L3M | -1208 / -2115 | +2117 | +123 / +214 | +5021 | c=0.50: -643 / +1058 / +61 | 113 | +0.006 | +0.051 | -0.06 / n/a / n/a | ok |
| WP10 | CT28p | L6M | -589 / -1030 | +2117 | -788 / -1378 | +5021 | c=0.50: -365 / +1058 / -367 | 268 | -0.035 | -0.350 | -0.10 / n/a / n/a | ok |
| WP10 | CT35m | L3M | -552 / -967 | +116 | -699 / -1224 | +2101 | c=0.50: -272 / +58 / -393 | 67 | -0.049 | -0.255 | +0.13 / n/a / n/a | ok |
| WP10 | CT35m | L6M | -123 / -215 | -805 | -757 / -1326 | +2101 | c=0.50: -75 / +58 / -400 | 206 | -0.039 | -0.298 | +0.06 / n/a / n/a | ok |
| WP10 | CT35p | L3M | +955 / +1672 | -5204 | +593 / +1037 | -4037 | c=0.50: +248 / -2602 / +193 | 93 | +0.047 | +0.333 | -0.19 / n/a / n/a | ok |
| WP10 | CT35p | L6M | +507 / +887 | -5204 | +868 / +1519 | -4037 | c=0.50: +88 / -2602 / +384 | 241 | +0.045 | +0.403 | +0.06 / n/a / n/a | ok |
| WP10 | CT42m | L3M | -77 / -135 | +2381 | +795 / +1391 | +446 | c=0.50: -43 / +1191 / +397 | 64 | +0.067 | +0.331 | +0.02 / n/a / n/a | ok |
| WP10 | CT42m | L6M | -31 / -55 | +2381 | +780 / +1365 | +446 | c=0.50: -44 / +1191 / +390 | 214 | +0.041 | +0.325 | +0.08 / n/a / n/a | ok |
| WP10 | CT42p | L3M | +1778 / +3111 | -3659 | +299 / +523 | -6210 | c=0.50: +687 / -1830 / +57 | 90 | +0.029 | +0.201 | -0.01 / n/a / n/a | AMBER |
| WP10 | CT42p | L6M | +1098 / +1921 | -3659 | -620 / -1085 | -6210 | c=0.50: +381 / -1830 / -316 | 211 | -0.032 | -0.253 | -0.14 / n/a / n/a | AMBER |
| WP10 | CT49m | L3M | -78 / -137 | +2766 | +862 / +1509 | +891 | c=0.50: -47 / +1383 / +439 | 55 | +0.083 | +0.353 | -0.19 / n/a / n/a | ok |
| WP10 | CT49m | L6M | +389 / +681 | -6980 | +875 / +1531 | +891 | c=0.50: +128 / -1331 / +441 | 192 | +0.051 | +0.361 | -0.01 / n/a / n/a | ok |
| WP10 | CT49p | L3M | +935 / +1636 | -4739 | +185 / +324 | -3657 | c=0.50: +235 / -2370 / +93 | 97 | +0.010 | +0.077 | -0.11 / n/a / n/a | ok |
| WP10 | CT49p | L6M | +455 / +797 | -4739 | +1012 / +1770 | -3657 | c=0.50: +61 / -2370 / +544 | 260 | +0.040 | +0.390 | +0.01 / n/a / n/a | ok |
| WP10 | CT56m | L3M | +418 / +732 | +3133 | -385 / -674 | -1125 | c=0.50: +226 / +3133 / -227 | 49 | -0.035 | -0.132 | -0.08 / n/a / n/a | ok |
| WP10 | CT56m | L6M | +344 / +602 | +2689 | -1241 / -2171 | -1125 | c=0.50: +151 / +3133 / -599 | 188 | -0.077 | -0.535 | -0.06 / n/a / n/a | ok |
| WP10 | CT56p | L3M | +304 / +531 | -614 | +1362 / +2384 | -2485 | c=0.50: +134 / -307 / +638 | 97 | +0.081 | +0.603 | -0.05 / n/a / n/a | ok |
| WP10 | CT56p | L6M | +71 / +125 | -614 | +1508 / +2639 | -2485 | c=0.50: +14 / -307 / +733 | 245 | +0.071 | +0.645 | +0.08 / n/a / n/a | ok |
| WP10 | CT63m | L3M | +495 / +867 | +0 | -803 / -1405 | -1605 | c=0.50: +228 / +0 / -401 | 26 | -0.167 | -0.334 | -0.21 / n/a / n/a | ok |
| WP10 | CT63m | L6M | +441 / +771 | +0 | -962 / -1684 | -1605 | c=0.50: +173 / +0 / -436 | 174 | -0.068 | -0.439 | -0.13 / n/a / n/a | ok |
| WP10 | CT63p | L3M | -125 / -218 | +721 | +120 / +210 | +2391 | c=0.50: -170 / +361 / +103 | 92 | +0.002 | +0.015 | +0.44 / n/a / n/a | ok |
| WP10 | CT63p | L6M | -44 / -76 | +434 | -219 / -383 | +2391 | c=0.50: -95 / +361 / -72 | 221 | -0.015 | -0.122 | +0.33 / n/a / n/a | ok |
| WP10 | CT70m | L3M | -207 / -362 | +2907 | -228 / -399 | +727 | c=0.50: -250 / +2097 / -99 | 34 | -0.041 | -0.108 | -0.10 / n/a / n/a | ok |
| WP10 | CT70m | L6M | -189 / -331 | +2907 | -395 / -691 | +727 | c=0.50: -197 / +2097 / -190 | 207 | -0.022 | -0.171 | -0.14 / n/a / n/a | ok |
| WP10 | CT70p | L3M | +628 / +1099 | +4284 | -2054 / -3595 | -1085 | c=0.50: +281 / +3708 / -1119 | 84 | -0.121 | -0.779 | -0.19 / n/a / n/a | ok |
| WP10 | CT70p | L6M | +493 / +863 | +2374 | -1722 / -3014 | -1085 | c=0.50: +202 / +3346 / -866 | 223 | -0.086 | -0.714 | -0.16 / n/a / n/a | ok |
| WP10 | CT77m | L3M | +86 / +150 | +0 | -1142 / -1999 | -0 | c=0.50: +34 / +0 / -571 | 20 | -0.309 | -0.476 | -0.32 / n/a / n/a | ok |
| WP10 | CT77m | L6M | +92 / +161 | +0 | -929 / -1625 | +0 | c=0.50: +9 / +0 / -426 | 151 | -0.075 | -0.418 | -0.01 / n/a / n/a | ok |
| WP10 | CT77p | L3M | -1023 / -1790 | +651 | -222 / -389 | +2650 | c=0.50: -536 / +325 / -103 | 84 | -0.015 | -0.099 | -0.28 / n/a / n/a | ok |
| WP10 | CT77p | L6M | -22 / -38 | -4852 | +212 / +371 | +2650 | c=0.50: +65 / -3210 / -20 | 224 | +0.023 | +0.193 | -0.23 / n/a / n/a | ok |
| WP10 | CT7m | L3M | +255 / +446 | -5259 | +749 / +1310 | +278 | c=0.50: -156 / -2629 / +282 | 96 | +0.053 | +0.389 | +0.05 / n/a / n/a | ok |
| WP10 | CT7m | L6M | +195 / +341 | -5259 | -306 / -536 | +278 | c=0.50: -107 / -2629 / -197 | 221 | -0.011 | -0.091 | -0.03 / n/a / n/a | ok |
| WP10 | CT7p | L3M | +1146 / +2005 | -5914 | -1325 / -2319 | -2442 | c=0.50: +241 / -2957 / -697 | 102 | -0.067 | -0.524 | +0.04 / n/a / n/a | ok |
| WP10 | CT7p | L6M | +661 / +1157 | -5914 | -1298 / -2272 | -2442 | c=0.50: +87 / -2957 / -628 | 223 | -0.068 | -0.559 | -0.17 / n/a / n/a | ok |
| WP10 | CT84m | L3M | +181 / +317 | +0 | +0 / +0 | +0 | c=0.50: +127 / +0 / -44 | 15 | +0.032 | +0.037 | -0.21 / n/a / n/a | ok |
| WP10 | CT84m | L6M | +46 / +80 | +0 | +817 / +1429 | +0 | c=0.50: +18 / +0 / +387 | 172 | +0.056 | +0.358 | -0.05 / n/a / n/a | ok |
| WP10 | CT84p | L3M | +222 / +389 | +1429 | -1330 / -2327 | +1135 | c=0.50: +28 / +800 / -757 | 80 | -0.078 | -0.477 | +0.33 / n/a / n/a | ok |
| WP10 | CT84p | L6M | +503 / +880 | +1429 | -1459 / -2553 | +1135 | c=0.50: +304 / +85 / -903 | 209 | -0.060 | -0.463 | -0.07 / n/a / n/a | ok |
| WP10 | CT91m | L3M | -34 / -60 | +0 | +212 / +370 | +0 | c=0.50: -19 / +0 / +114 | 7 | +0.152 | +0.082 | -0.10 / n/a / n/a | ok |
| WP10 | CT91m | L6M | +288 / +503 | -2315 | -527 / -922 | +0 | c=0.50: +100 / +0 / -260 | 161 | -0.037 | -0.223 | -0.22 / n/a / n/a | ok |
| WP10 | CT91p | L3M | +1595 / +2791 | -4909 | -1366 / -2390 | -3570 | c=0.50: +632 / -2455 / -717 | 76 | -0.092 | -0.540 | -0.31 / n/a / n/a | ok |
| WP10 | CT91p | L6M | +1289 / +2256 | -5291 | +21 / +37 | -3570 | c=0.50: +556 / -2455 / -69 | 212 | +0.010 | +0.075 | -0.17 / n/a / n/a | ok |
| WP10 | CT98m | L3M | -124 / -217 | +0 | +516 / +903 | +0 | c=0.50: -77 / +0 / +278 | 5 | +0.517 | +0.199 | +0.26 / n/a / n/a | ok |
| WP10 | CT98m | L6M | -63 / -110 | +0 | +280 / +490 | +0 | c=0.50: -72 / +0 / +149 | 137 | +0.021 | +0.109 | +0.13 / n/a / n/a | ok |
| WP10 | CT98p | L3M | +179 / +314 | -244 | -796 / -1393 | -1744 | c=0.50: +76 / -122 / -398 | 84 | -0.051 | -0.332 | -0.29 / n/a / n/a | ok |
| WP10 | CT98p | L6M | +410 / +717 | -6341 | -274 / -479 | -1744 | c=0.50: +130 / -2159 / -121 | 223 | -0.015 | -0.127 | +0.05 / n/a / n/a | ok |
| WP10 | RK7 | L3M | +181 / +316 | -2034 | +1234 / +2160 | -3029 | c=0.50: +162 / -2234 / +494 | 111 | +0.072 | +0.617 | -0.12 / n/a / n/a | ok |
| WP10 | RK7 | L6M | +188 / +329 | -2034 | +661 / +1156 | -3029 | c=0.50: +138 / -2234 / -76 | 228 | +0.073 | +0.614 | -0.15 / n/a / n/a | ok |
| WP10 | RK7 | Y2023 | +7553 / +13218 | -11 | -96 / -168 | -20935 | c=0.50: +5025 / -174 / -138 | 444 | +0.003 | +0.035 | -0.23 / n/a / n/a | RED |
| WP10 | RK7 | Y2024 | +6277 / +10984 | -135 | +74 / +130 | +1946 | c=0.50: +3729 / -67 / -144 | 589 | +0.016 | +0.182 | -0.41 / n/a / n/a | AMBER |
| WP10 | RK7 | Y2025 | -5872 / -10276 | -2604 | -662 / -1158 | +818 | c=0.50: -4705 / +303 / -672 | 531 | +0.001 | +0.008 | -0.28 / n/a / n/a | ok |
| WP10 | ADD | L3M | -372 / -652 | +401 | +1569 / +2746 | -285 | c=0.50: -246 / +201 / +739 | 110 | +0.082 | +0.692 | -0.12 / n/a / n/a | ok |
| WP10 | ADD | L6M | -206 / -360 | +401 | +1516 / +2652 | -285 | c=0.50: -154 / +201 / +736 | 227 | +0.077 | +0.650 | -0.15 / n/a / n/a | ok |
| WP10 | ADD | Y2023 | +3250 / +5688 | +653 | +77 / +135 | -7030 | c=0.50: +1256 / +490 / +39 | 443 | +0.003 | +0.032 | -0.23 / n/a / n/a | AMBER |
| WP10 | ADD | Y2024 | -22 / -38 | -135 | +427 / +746 | +372 | c=0.50: -837 / -67 / +196 | 581 | +0.017 | +0.192 | -0.40 / n/a / n/a | ok |
| WP10 | ADD | Y2025 | -4358 / -7626 | -4241 | +86 / +151 | -958 | c=0.50: -2573 / -1334 / +16 | 529 | +0.006 | +0.059 | -0.27 / n/a / n/a | ok |
| WP10:NP4 | C2 | L3M | -419 / -732 | +991 | +2710 / +4743 | -588 | c=0.52: -220 / -670 / +1276 | 0 | +nan | +1.269 | +0.20 / n/a / n/a | ok |
| WP10:NP4 | C2 | L6M | -120 / -211 | +991 | +1219 / +2134 | -588 | c=0.52: -110 / -670 / +234 | 0 | +nan | +0.872 | -0.02 / n/a / n/a | ok |
| WP10:NP5:NP4 | C3 | L3M | +1373 / +2402 | -5864 | +1754 / +3069 | -5721 | c=0.34: +416 / -3600 / +433 | 0 | +nan | +0.850 | +0.06 / n/a / n/a | AMBER |
| WP10:NP5:NP4 | C3 | L6M | +869 / +1520 | -5864 | +1488 / +2604 | -5721 | c=0.34: +228 / -3600 / -30 | 0 | +nan | +0.978 | +0.03 / n/a / n/a | AMBER |
| WP11 | ALL | L3M | +193 / +337 | -3619 | -156 / -273 | -704 | c=2.00: +231 / -4804 / -65 | 49 | +0.020 | +0.076 | +0.05 / n/a / n/a | ok |
| WP11 | ALL | L6M | +31 / +55 | -3619 | -467 / -818 | -704 | c=2.00: -5 / -4804 / -122 | 110 | +0.071 | +0.288 | +0.15 / n/a / n/a | ok |
| WP11 | RK7 | L3M | +193 / +337 | -3619 | -156 / -273 | -704 | c=1.00: +193 / -3619 / -156 | 49 | +0.020 | +0.076 | +0.05 / n/a / n/a | ok |
| WP11 | RK7 | L6M | +31 / +55 | -3619 | -467 / -818 | -704 | c=1.00: +31 / -3619 / -467 | 110 | +0.071 | +0.288 | +0.15 / n/a / n/a | ok |
| WP11 | ADD | L3M | +11 / +19 | -1185 | -23 / -40 | +1051 | c=1.00: +11 / -1185 / -23 | 49 | +0.020 | +0.076 | +0.05 / n/a / n/a | ok |
| WP11 | ADD | L6M | -95 / -167 | -1185 | +290 / +508 | +1051 | c=1.00: -95 / -1185 / +290 | 110 | +0.071 | +0.288 | +0.15 / n/a / n/a | ok |
| WP1:WP10 | C2 | L3M | -402 / -703 | +4616 | -410 / -718 | -588 | c=0.67: -330 / +2266 / -356 | 0 | +nan | -0.091 | +0.13 / n/a / n/a | ok |
| WP1:WP10 | C2 | L6M | -229 / -401 | +3558 | +625 / +1094 | -588 | c=0.67: -177 / +2266 / +146 | 0 | +nan | +0.799 | +0.20 / n/a / n/a | ok |
| WP1:WP10 | P2 | L3M | -339 / -593 | +6644 | -75 / -132 | -70 | c=1.00: -184 / +3526 / -84 | 0 | +nan | +0.014 | +0.14 / n/a / n/a | ok |
| WP1:WP10 | P2 | L6M | -232 / -405 | +5075 | +1480 / +2590 | -70 | c=1.00: -131 / +3526 / +718 | 0 | +nan | +1.270 | +0.21 / n/a / n/a | ok |
| WP1:WP10 | P2 | Y2025 | -3083 / -5395 | -350 | +781 / +1366 | -3520 | c=1.00: -1697 / +294 / +368 | 0 | +nan | +0.688 | -0.11 / n/a / n/a | ok |
| WP2 | ALL | L3M | -57 / -100 | +901 | +165 / +288 | -1153 | c=1.33: +3 / +2013 / +302 | 64 | +0.046 | +0.228 | +0.14 / n/a / n/a | ok |
| WP2 | ALL | L6M | +132 / +232 | +901 | -827 / -1447 | -1153 | c=1.33: +209 / +2013 / -832 | 145 | -0.002 | -0.008 | +0.23 / n/a / n/a | ok |
| WP2 | RK7 | L3M | -57 / -100 | +901 | +165 / +288 | -1153 | c=0.67: -103 / -211 / +28 | 64 | +0.046 | +0.228 | +0.14 / n/a / n/a | ok |
| WP2 | RK7 | L6M | +132 / +232 | +901 | -827 / -1447 | -1153 | c=0.67: +68 / -211 / -822 | 145 | -0.002 | -0.008 | +0.23 / n/a / n/a | ok |
| WP2 | ADD | L3M | +70 / +123 | +2743 | +319 / +559 | -634 | c=0.67: +24 / +2224 / +182 | 64 | +0.046 | +0.228 | +0.14 / n/a / n/a | ok |
| WP2 | ADD | L6M | +110 / +192 | +2743 | +350 / +612 | -634 | c=0.67: +54 / +2224 / +218 | 150 | +0.039 | +0.219 | +0.17 / n/a / n/a | ok |
| WP3 | ALL | L3M | +869 / +1520 | -6044 | +855 / +1495 | -3436 | c=1.31: +1184 / -7149 / +1192 | 60 | +0.130 | +0.599 | +0.28 / n/a / n/a | ok |
| WP3 | ALL | L6M | +500 / +875 | -6044 | +132 / +231 | -3436 | c=1.31: +681 / -7149 / +421 | 139 | +0.100 | +0.514 | +0.39 / n/a / n/a | ok |
| WP3 | RK7 | L3M | +869 / +1520 | -6044 | +855 / +1495 | -3436 | c=0.65: +532 / -4792 / +473 | 60 | +0.130 | +0.599 | +0.28 / n/a / n/a | ok |
| WP3 | RK7 | L6M | +500 / +875 | -6044 | +132 / +231 | -3436 | c=0.65: +315 / -4792 / -196 | 139 | +0.100 | +0.514 | +0.39 / n/a / n/a | ok |
| WP3 | ADD | L3M | +957 / +1674 | -5999 | +917 / +1605 | -2873 | c=0.65: +399 / -3918 / +599 | 61 | +0.106 | +0.499 | +0.22 / n/a / n/a | ok |
| WP3 | ADD | L6M | +530 / +928 | -5999 | +887 / +1552 | -2873 | c=0.65: +197 / -3918 / +621 | 141 | +0.080 | +0.417 | +0.37 / n/a / n/a | ok |
| WP4 | ADD | L3M | +1017 / +1779 | -4444 | -978 / -1711 | -3783 | c=0.50: +163 / -2222 / -489 | 38 | -0.139 | -0.407 | +0.32 / n/a / n/a | ok |
| WP4 | ADD | L6M | +878 / +1536 | -4444 | -460 / -805 | -3783 | c=0.50: +215 / -2222 / -230 | 83 | -0.062 | -0.192 | +0.13 / n/a / n/a | ok |
| WP5 | ADD | L3M | +376 / +659 | +2261 | -339 / -593 | -2675 | c=0.57: +205 / +1292 / -233 | 77 | -0.020 | -0.118 | -0.14 / n/a / n/a | ok |
| WP5 | ADD | L6M | +219 / +384 | +2261 | -754 / -1319 | -2675 | c=0.57: +115 / +1292 / -450 | 177 | -0.052 | -0.338 | -0.14 / n/a / n/a | ok |
| WP6 | ADD | L3M | +585 / +1024 | +135 | -542 / -948 | -1190 | c=1.00: +585 / +135 / -542 | 57 | -0.068 | -0.298 | -0.20 / n/a / n/a | ok |
| WP6 | ADD | L6M | +413 / +722 | +135 | -410 / -718 | -1190 | c=1.00: +413 / +135 / -410 | 142 | -0.059 | -0.313 | -0.04 / n/a / n/a | ok |
| WP8 | ALL | L3M | +1498 / +2621 | -3809 | +493 / +863 | -6659 | c=1.12: +1702 / -3978 / +584 | 71 | +0.063 | +0.346 | -0.35 / n/a / n/a | AMBER |
| WP8 | ALL | L6M | +1080 / +1891 | -3809 | -1065 / -1863 | -6659 | c=1.12: +1231 / -3978 / -1096 | 173 | -0.018 | -0.118 | -0.37 / n/a / n/a | AMBER |
| WP8 | RK7 | L3M | +1498 / +2621 | -3809 | +493 / +863 | -6659 | c=0.56: +869 / -3206 / +169 | 71 | +0.063 | +0.346 | -0.35 / n/a / n/a | AMBER |
| WP8 | RK7 | L6M | +1080 / +1891 | -3809 | -1065 / -1863 | -6659 | c=0.56: +621 / -3206 / -954 | 173 | -0.018 | -0.118 | -0.37 / n/a / n/a | AMBER |
| WP8 | ADD | L3M | +511 / +894 | +3241 | +1183 / +2071 | -2490 | c=0.56: +254 / +1820 / +624 | 73 | +0.106 | +0.597 | -0.30 / n/a / n/a | ok |
| WP8 | ADD | L6M | +399 / +698 | -1065 | -39 / -68 | -2490 | c=0.56: +194 / +1296 / -41 | 175 | +0.000 | +0.003 | -0.34 / n/a / n/a | ok |

Labels: none yet (controls pending; BUILD-READY / NEEDS MORE / DROPPED rule in PREREG_NYE.md).

