# NEW_BOOK_ENGINE - replacement of the NY AM / NY PM books on the exact engine (W-NYENG), refreshed 2026-11-19 02:07Z

**These rows are vs TODAY's stack (JL3) with today's DAY-DONE setting; they answer add / swap one book in today's stack, not the rebuilt stack.** WP10 and XA3 stay leads on that basis.

Stack = JL3 (all live layers ON). Dollars: engine BASE lots at $4.84 RT/contract proxy with an x1.75 live-lot column in brackets. Deltas = WITH minus the live JL3 stack on the same months; drawdown first: d ulcer / d worst week / d max DD / d mean $/wk (x1.75 in brackets). Negative ulcer / DD change = better. PROVISIONAL cells (selection-biased picks); no label without controls (none yet). Prereg PREREG_NYE.md + AMEND1 (DECISIONS.md). Identity (injection = JL3 with an inert event): 202610: PASS (691 trades, net 37159.82); 202504: PASS (637 trades, net 41239.76). Set-months done: 3807.

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
Cells seeded in rank order from /mnt/l2/l2vast/_nye/ladder_cells.json (NY AM by R3 p6 then p_all; NY PM family-bests of the bare rule, R3 not yet run for NY PM). Stage A = last 6 + 3 months as ADD and as replacement of the weakest live book of the session (K7), 12 set-months per cell; B = prior years for rows not negative; C = 30 date-shift controls for rows still alive; D = layer programme in clock order. Built so far: 5425 cells ({'A': 5425}); set-months still queued: 77027. Everything is vs TODAY's stack, provisional until Asia and London are decided.

## XA3 phase 3a (own layers; vs today's stack, provisional until Asia and London are decided)
Identity TL3_NYL_XA3_ID1-9 PASS. Fit stage F1 (72 settings x last 6 months) landed; scored on autopilot/NEW_BOOK_LAYER_FIT_XA3.md (ulcer first, vs the ADD row and vs JL3); stage F2 (top 2 settings per layer with ulcer better and >= 80% of trades, prior years 2023-2026-04) queued; joint stage after F2.

## ID glossary (reconciled 16:10Z; engine ids never change)
- WA<n> / WP<n> = W-SHORT rank n on the 14:23Z page (frozen): **WP1 = NY PM dlt_100 levels_vwap.reject {tol 0, conf close}, plain 60/60** (NOT tm1800); **WP10 = NY PM vol_350 tape_libvol.cmf {len 10}, asym20u/10u (median stop/target 120/60)**; WP11 = tm1800 xmarket_ym.follow plain 60/60 on that page.
- XA<n> / XP<n> = W-SHORT rank n on the 15:19Z equal-risk page (frozen): **XP2 = NY PM tm1800 xmarket_ym.follow {w 5, thr 1.0}**, XP1 = dib_400 tape_libvol.cmf {len 10}, XP3 = tm900 xmarket_es.follow. So XP2 (tm1800 YM follow) is a different cell from WP1 (dlt_100 VWAP reject); the headline rows NYE_WP1_* / NYW_WP1_* are dlt_100 VWAP reject.
- NA<n> / NP<n> = my first provisional six per session (level_nr_qual picks). Set names: TL3_NYE_<id>_ADD|RK7|RP7|RM7|ALL|BARE|ACCT|CT<k><p|m>, TL3_NYW_<id>_ADD (W / X cells), TL3_NYE_C2|C3|D1|D2|P2_<session>_<ids> (P2 = K7 kept + both new books).

## Date-shift controls (same events moved +-7..35 days, same weekday; ADD at 1 base lot; L6M)
| cell | real d mean $/wk | real d ulcer | controls n | controls d mean median / best | controls d ulcer median / best | real beats controls on mean (share) | real better ulcer than controls (share) |
|---|---|---|---|---|---|---|---|
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

### All sets (detail)
| cell | variant | window | d ulcer (x1 / x1.75) | d worst wk | d mean $/wk (x1 / x1.75) | d max DD | RISK-MATCHED c: d ulcer / d worst / d mean | new-book trades | R/trade | R/wk | corr daily w/ K7 / P7 / M7 | flag vs JL3 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | RK7 | L3M | -448 / -784 | +2462 | +2609 / +4565 | +2114 | c=1.00: -448 / +2462 / +2609 | 141 | +0.129 | +1.394 | +0.26 / +0.22 / +0.37 | ok |
|  | RK7 | L6M | -75 / -130 | +620 | +1755 / +3071 | +1857 | c=1.00: -75 / +620 / +1755 | 290 | +0.081 | +0.866 | +0.23 / +0.13 / +0.22 | ok |
|  | RK7 | L3M | +1188 / +2080 | -4065 | +1313 / +2298 | -2702 | c=1.00: +1188 / -4065 / +1313 | 59 | +0.069 | +0.313 | +0.11 / -0.02 / +0.26 | ok |
|  | RK7 | L6M | +732 / +1281 | -4065 | +1293 / +2262 | -2702 | c=1.00: +732 / -4065 / +1293 | 134 | +0.144 | +0.717 | +0.01 / -0.01 / +0.18 | ok |
|  | RK7 | L3M | +4567 / +7992 | -7038 | +1219 / +2134 | -13898 | c=1.00: +4567 / -7038 / +1219 | 90 | +0.034 | +0.238 | -0.16 / +0.43 / +0.18 | RED |
|  | RK7 | L6M | +3025 / +5294 | -7038 | +2044 / +3577 | -13898 | c=1.00: +3025 / -7038 / +2044 | 215 | +0.154 | +1.229 | -0.09 / +0.20 / +0.13 | RED |
|  | RK7 | L3M | +303 / +530 | +1651 | +2638 / +4617 | +664 | c=1.00: +303 / +1651 / +2638 | 163 | +0.125 | +1.569 | +0.17 / +0.12 / +0.38 | ok |
|  | RK7 | L6M | +255 / +446 | +1651 | +2505 / +4384 | +664 | c=1.00: +255 / +1651 / +2505 | 382 | +0.123 | +1.742 | +0.14 / +0.08 / +0.16 | ok |
|  | RK7 | L3M | +2706 / +4735 | -9015 | +1613 / +2823 | -12215 | c=1.00: +2706 / -9015 / +1613 | 127 | +0.111 | +1.086 | +0.13 / -0.00 / +0.20 | RED |
|  | RK7 | L6M | +1860 / +3255 | -9015 | +1741 / +3046 | -12215 | c=1.00: +1860 / -9015 / +1741 | 266 | +0.126 | +1.238 | +0.02 / +0.03 / +0.01 | RED |
|  | RK7 | L3M | +2679 / +4689 | -8240 | -452 / -791 | -7967 | c=1.00: +2679 / -8240 / -452 | 60 | -0.170 | -0.783 | +0.17 / -0.02 / +0.20 | AMBER |
|  | RK7 | L6M | +1710 / +2993 | -8240 | +1344 / +2351 | -7967 | c=1.00: +1710 / -8240 / +1344 | 137 | +0.162 | +0.822 | +0.15 / +0.03 / +0.19 | AMBER |
|  | RK7 | L3M | +1912 / +3345 | -1734 | +1964 / +3436 | -7092 | c=1.00: +1912 / -1734 / +1964 | 213 | +0.072 | +1.187 | -0.12 / -0.08 / +0.18 | AMBER |
|  | RK7 | L6M | +1360 / +2379 | -2148 | +931 / +1629 | -7092 | c=1.00: +1360 / -2148 / +931 | 503 | +0.029 | +0.535 | -0.05 / +0.02 / +0.15 | AMBER |
|  | RK7 | L3M | +892 / +1561 | +969 | +1557 / +2726 | -3857 | c=1.00: +892 / +969 / +1557 | 70 | +0.273 | +1.469 | +0.16 / +0.22 / +0.25 | ok |
|  | RK7 | L6M | +634 / +1109 | +969 | +1034 / +1809 | -3857 | c=1.00: +634 / +969 / +1034 | 176 | +0.137 | +0.893 | +0.12 / +0.15 / +0.25 | ok |
|  | RK7 | L3M | +469 / +822 | -3935 | +2811 / +4920 | -627 | c=1.00: +469 / -3935 / +2811 | 91 | +0.270 | +1.891 | +0.24 / +0.27 / +0.20 | ok |
|  | RK7 | L3M | +416 / +728 | -3580 | +791 / +1384 | -130 | c=1.00: +416 / -3580 / +791 | 69 | +0.030 | +0.158 | +0.10 / -0.04 / +0.04 | ok |
|  | RK7 | L6M | +358 / +627 | -3580 | +1374 / +2404 | -130 | c=1.00: +358 / -3580 / +1374 | 164 | +0.120 | +0.728 | +0.06 / +0.03 / +0.11 | ok |
|  | RK7 | L3M | +1083 / +1895 | -6570 | +2339 / +4093 | -4545 | c=1.00: +1083 / -6570 / +2339 | 126 | +0.161 | +1.563 | +0.36 / +0.15 / +0.28 | ok |
|  | RK7 | L6M | +758 / +1326 | -6570 | +1556 / +2723 | -4545 | c=1.00: +758 / -6570 / +1556 | 283 | +0.091 | +0.957 | +0.16 / +0.11 / +0.07 | ok |
|  | RK7 | L3M | +6885 / +12050 | -8104 | -649 / -1136 | -19527 | c=1.00: +6885 / -8104 / -649 | 92 | -0.099 | -0.699 | +0.10 / +0.24 / +0.28 | RED |
|  | RK7 | L6M | +4427 / +7747 | -8104 | +510 / +893 | -19527 | c=1.00: +4427 / -8104 / +510 | 224 | +0.035 | +0.292 | +0.02 / +0.17 / +0.24 | RED |
|  | RK7 | L3M | -664 / -1163 | +422 | +3941 / +6897 | +2235 | c=1.00: -664 / +422 / +3941 | 117 | +0.356 | +3.207 | +0.25 / +0.11 / +0.19 | ok |
|  | RK7 | L6M | +143 / +251 | +422 | +1571 / +2749 | -5362 | c=1.00: +143 / +422 / +1571 | 259 | +0.125 | +1.201 | +0.13 / +0.07 / +0.10 | AMBER |
|  | RK7 | L3M | +4595 / +8041 | -3125 | -371 / -649 | -14491 | c=1.00: +4595 / -3125 / -371 | 101 | -0.042 | -0.328 | +0.09 / +0.37 / +0.34 | RED |
|  | RK7 | L6M | +2951 / +5163 | -3851 | +743 / +1300 | -14491 | c=1.00: +2951 / -3851 / +743 | 222 | +0.067 | +0.549 | +0.02 / +0.25 / +0.25 | RED |
|  | RK7 | L3M | +541 / +946 | +2066 | +2017 / +3530 | -972 | c=1.00: +541 / +2066 / +2017 | 200 | +0.070 | +1.083 | +0.15 / +0.16 / +0.30 | ok |
|  | RK7 | L6M | +413 / +722 | +1007 | +2434 / +4260 | -972 | c=1.00: +413 / +1007 / +2434 | 436 | +0.100 | +1.615 | +0.17 / +0.07 / +0.12 | ok |
|  | RK7 | L3M | +3281 / +5742 | -6615 | +1025 / +1793 | -12433 | c=1.00: +3281 / -6615 / +1025 | 75 | +0.022 | +0.128 | -0.07 / +0.11 / +0.16 | RED |
|  | RK7 | L3M | +3860 / +6756 | -8080 | -199 / -349 | -11861 | c=1.00: +3860 / -8080 / -199 | 72 | -0.111 | -0.612 | +0.10 / +0.12 / +0.21 | RED |
|  | RK7 | L6M | +2369 / +4147 | -8080 | +408 / +714 | -11861 | c=1.00: +2369 / -8080 / +408 | 155 | +0.021 | +0.121 | +0.07 / +0.02 / +0.17 | RED |
|  | RK7 | L3M | +107 / +188 | +690 | +2626 / +4595 | +1537 | c=1.00: +107 / +690 / +2626 | 133 | +0.144 | +1.469 | +0.24 / +0.08 / +0.20 | ok |
|  | RK7 | L6M | +361 / +632 | -3010 | +1842 / +3223 | +1537 | c=1.00: +361 / -3010 / +1842 | 250 | +0.117 | +1.085 | +0.10 / +0.07 / +0.06 | ok |
|  | RK7 | L3M | -215 / -376 | -3000 | +1586 / +2775 | +2131 | c=1.00: -215 / -3000 / +1586 | 65 | +0.162 | +0.812 | +0.17 / -0.16 / +0.04 | ok |
|  | RK7 | L6M | +234 / +410 | -3850 | +1570 / +2747 | +1857 | c=1.00: +234 / -3850 / +1570 | 142 | +0.214 | +1.126 | +0.08 / -0.06 / +0.08 | ok |
|  | RK7 | L3M | +2569 / +4495 | -5990 | +609 / +1066 | -4682 | c=1.00: +2569 / -5990 / +609 | 61 | +0.133 | +0.624 | -0.08 / +0.19 / -0.01 | AMBER |
|  | RK7 | L6M | +1615 / +2826 | -5990 | +327 / +571 | -4682 | c=1.00: +1615 / -5990 / +327 | 149 | +0.045 | +0.251 | -0.09 / +0.18 / -0.02 | AMBER |
|  | RK7 | L3M | +5714 / +9999 | -8724 | +553 / +968 | -19101 | c=1.00: +5714 / -8724 / +553 | 116 | +0.036 | +0.324 | +0.05 / +0.25 / +0.31 | RED |
|  | RK7 | L6M | +3822 / +6688 | -8724 | +1631 / +2854 | -19101 | c=1.00: +3822 / -8724 / +1631 | 292 | +0.108 | +1.163 | +0.00 / +0.16 / +0.15 | RED |
|  | RK7 | L3M | -448 / -784 | -3080 | +2629 / +4601 | +2306 | c=1.00: -448 / -3080 / +2629 | 64 | +0.304 | +1.495 | +0.23 / -0.12 / +0.07 | ok |
|  | RK7 | L6M | +100 / +175 | -3825 | +1934 / +3385 | +1857 | c=1.00: +100 / -3825 / +1934 | 136 | +0.256 | +1.288 | +0.13 / -0.04 / +0.05 | ok |
|  | RK7 | L3M | +1317 / +2305 | +1142 | -1019 / -1783 | -4186 | c=1.00: +1317 / +1142 / -1019 | 89 | -0.183 | -1.255 | +0.07 / -0.02 / +0.03 | ok |
|  | RK7 | L6M | +980 / +1715 | +1142 | +1275 / +2231 | -4186 | c=1.00: +980 / +1142 / +1275 | 206 | +0.093 | +0.708 | -0.04 / -0.01 / -0.12 | ok |
|  | RK7 | L3M | +1505 / +2634 | -1108 | +250 / +437 | -4896 | c=1.00: +1505 / -1108 / +250 | 113 | +0.021 | +0.181 | +0.29 / +0.19 / +0.58 | AMBER |
|  | RK7 | L6M | +1185 / +2073 | -1108 | +166 / +291 | -4896 | c=1.00: +1185 / -1108 / +166 | 242 | +0.010 | +0.091 | +0.30 / +0.16 / +0.49 | AMBER |
|  | RK7 | L3M | +379 / +664 | +1227 | +553 / +969 | -2950 | c=1.00: +379 / +1227 / +553 | 162 | +0.021 | +0.262 | +0.28 / -0.09 / -0.04 | ok |
|  | RK7 | L6M | +306 / +536 | +1227 | +1023 / +1790 | -2950 | c=1.00: +306 / +1227 / +1023 | 337 | +0.035 | +0.436 | +0.30 / -0.05 / +0.01 | ok |
|  | RK7 | L3M | +2208 / +3863 | -5132 | +603 / +1055 | -4880 | c=1.00: +2208 / -5132 / +603 | 84 | +0.147 | +0.947 | +0.00 / +0.25 / +0.16 | AMBER |
|  | RK7 | L6M | +1336 / +2338 | -5132 | +822 / +1439 | -4880 | c=1.00: +1336 / -5132 / +822 | 194 | +0.110 | +0.793 | +0.07 / +0.15 / +0.20 | AMBER |
|  | RK7 | L3M | +1972 / +3452 | -3233 | +1918 / +3357 | -4963 | c=1.00: +1972 / -3233 / +1918 | 72 | +0.119 | +0.658 | +0.06 / +0.26 / +0.32 | AMBER |
|  | RK7 | L6M | +1297 / +2269 | -3233 | +591 / +1034 | -4963 | c=1.00: +1297 / -3233 / +591 | 169 | -0.008 | -0.049 | +0.16 / +0.20 / +0.26 | AMBER |
|  | RK7 | L3M | +2378 / +4161 | -2433 | -302 / -529 | -8118 | c=1.00: +2378 / -2433 / -302 | 106 | -0.032 | -0.259 | +0.11 / +0.32 / +0.22 | AMBER |
|  | RK7 | L6M | +1496 / +2617 | -2433 | +839 / +1468 | -8118 | c=1.00: +1496 / -2433 / +839 | 263 | +0.058 | +0.561 | +0.03 / +0.14 / +0.19 | AMBER |
|  | RK7 | L3M | +1868 / +3269 | -5505 | +441 / +771 | -6718 | c=1.00: +1868 / -5505 / +441 | 141 | -0.039 | -0.428 | +0.02 / +0.11 / +0.17 | AMBER |
|  | RK7 | L6M | +1272 / +2226 | -5505 | +706 / +1235 | -6718 | c=1.00: +1272 / -5505 / +706 | 290 | +0.013 | +0.144 | -0.05 / +0.02 / +0.06 | AMBER |
|  | RK7 | L3M | +2208 / +3863 | -1522 | +465 / +813 | -5294 | c=1.00: +2208 / -1522 / +465 | 112 | -0.003 | -0.029 | -0.06 / +0.30 / +0.35 | AMBER |
|  | RK7 | L6M | +1361 / +2382 | -1522 | +972 / +1701 | -5294 | c=1.00: +1361 / -1522 / +972 | 241 | +0.045 | +0.399 | +0.07 / +0.19 / +0.27 | AMBER |
|  | RK7 | L3M | +1507 / +2637 | -3756 | +1097 / +1919 | -4972 | c=1.00: +1507 / -3756 / +1097 | 168 | +0.077 | +0.989 | -0.35 / -0.23 / -0.15 | AMBER |
|  | RK7 | L3M | +2945 / +5153 | -6070 | +190 / +332 | -10271 | c=1.00: +2945 / -6070 / +190 | 77 | +0.041 | +0.242 | +0.17 / +0.03 / +0.20 | RED |
|  | RK7 | L6M | +1977 / +3459 | -6070 | +63 / +111 | -10271 | c=1.00: +1977 / -6070 / +63 | 178 | -0.012 | -0.081 | +0.06 / +0.04 / +0.12 | RED |
|  | RK7 | L3M | +1835 / +3211 | -3522 | +590 / +1033 | -6107 | c=1.00: +1835 / -3522 / +590 | 69 | -0.042 | -0.223 | +0.11 / +0.12 / -0.10 | AMBER |
|  | RK7 | L6M | +1230 / +2153 | -3522 | +1694 / +2965 | -6107 | c=1.00: +1230 / -3522 / +1694 | 153 | +0.179 | +1.014 | +0.03 / +0.09 / +0.02 | AMBER |
|  | RK7 | L3M | +3096 / +5418 | -8795 | +1163 / +2035 | -9101 | c=1.00: +3096 / -8795 / +1163 | 75 | +0.041 | +0.238 | +0.03 / +0.04 / +0.35 | AMBER |
|  | RK7 | L6M | +1970 / +3448 | -8795 | +1622 / +2838 | -9101 | c=1.00: +1970 / -8795 / +1622 | 158 | +0.156 | +0.912 | -0.03 / +0.01 / +0.14 | AMBER |
|  | RK7 | L3M | +249 / +435 | -1452 | +116 / +204 | +1612 | c=1.00: +249 / -1452 / +116 | 100 | +0.004 | +0.029 | +0.31 / +0.36 / +0.39 | ok |
|  | RK7 | L6M | +197 / +345 | -1452 | +906 / +1585 | +1612 | c=1.00: +197 / -1452 / +906 | 204 | +0.075 | +0.569 | +0.18 / +0.19 / +0.06 | ok |
|  | RK7 | L3M | +1301 / +2276 | -3535 | +203 / +354 | -4865 | c=1.00: +1301 / -3535 / +203 | 70 | +0.029 | +0.158 | +0.02 / -0.03 / -0.10 | AMBER |
|  | RK7 | L6M | +941 / +1646 | -3535 | +128 / +224 | -4865 | c=1.00: +941 / -3535 / +128 | 152 | +0.018 | +0.104 | +0.01 / +0.04 / +0.13 | AMBER |
|  | RK7 | L3M | +63 / +111 | +690 | +2912 / +5097 | +1537 | c=1.00: +63 / +690 / +2912 | 129 | +0.172 | +1.707 | +0.25 / +0.08 / +0.16 | ok |
|  | RK7 | L6M | +336 / +588 | -3010 | +1980 / +3464 | +1537 | c=1.00: +336 / -3010 / +1980 | 246 | +0.132 | +1.200 | +0.10 / +0.07 / +0.04 | ok |
|  | RK7 | L3M | +848 / +1484 | -5920 | +2149 / +3761 | -1844 | c=1.00: +848 / -5920 / +2149 | 60 | +0.308 | +1.420 | +0.20 / -0.02 / +0.06 | ok |
|  | RK7 | L6M | +808 / +1414 | -5920 | +2255 / +3946 | -1844 | c=1.00: +808 / -5920 / +2255 | 135 | +0.351 | +1.757 | +0.05 / +0.02 / +0.04 | ok |
|  | RK7 | L3M | +1877 / +3285 | -287 | +344 / +601 | -5881 | c=1.00: +1877 / -287 / +344 | 104 | +0.024 | +0.191 | +0.06 / +0.20 / +0.09 | AMBER |
|  | RK7 | L6M | +1467 / +2567 | -287 | +791 / +1384 | -5881 | c=1.00: +1467 / -287 / +791 | 263 | +0.060 | +0.586 | +0.14 / +0.15 / +0.02 | AMBER |
|  | RK7 | L3M | +1034 / +1810 | -3645 | +1658 / +2902 | -1417 | c=1.00: +1034 / -3645 / +1658 | 63 | +0.178 | +0.864 | -0.06 / -0.14 / +0.07 | ok |
|  | RK7 | L6M | +859 / +1503 | -3730 | +2515 / +4402 | -1417 | c=1.00: +859 / -3730 / +2515 | 146 | +0.341 | +1.843 | -0.06 / -0.08 / -0.00 | ok |
|  | RK7 | L3M | -141 / -247 | +1770 | +2175 / +3806 | +684 | c=1.00: -141 / +1770 / +2175 | 69 | +0.322 | +1.706 | +0.11 / +0.08 / +0.24 | ok |
|  | RK7 | L6M | +250 / +438 | -3605 | +1463 / +2560 | +684 | c=1.00: +250 / -3605 / +1463 | 173 | +0.174 | +1.118 | +0.10 / +0.06 / +0.31 | ok |
|  | RK7 | L3M | +2728 / +4774 | -5935 | +1639 / +2869 | -9857 | c=1.00: +2728 / -5935 / +1639 | 65 | +0.174 | +0.871 | +0.16 / +0.14 / +0.33 | RED |
|  | RK7 | L6M | +1955 / +3422 | -5935 | +1280 / +2240 | -9857 | c=1.00: +1955 / -5935 / +1280 | 146 | +0.155 | +0.839 | +0.04 / +0.08 / +0.21 | RED |
|  | RK7 | L3M | +1601 / +2803 | -3390 | +1088 / +1904 | -4065 | c=1.00: +1601 / -3390 / +1088 | 92 | +0.016 | +0.112 | -0.07 / -0.00 / -0.08 | ok |
|  | RK7 | L6M | +1022 / +1788 | -3390 | +1365 / +2389 | -4065 | c=1.00: +1022 / -3390 / +1365 | 193 | +0.079 | +0.566 | -0.04 / -0.05 / -0.08 | ok |
|  | RK7 | L3M | +624 / +1092 | -2955 | +1718 / +3006 | -493 | c=1.00: +624 / -2955 / +1718 | 120 | +0.107 | +0.988 | +0.13 / +0.10 / +0.04 | ok |
|  | RK7 | L6M | +476 / +833 | -2955 | +1545 / +2705 | -493 | c=1.00: +476 / -2955 / +1545 | 251 | +0.109 | +1.011 | +0.07 / +0.09 / -0.03 | ok |
|  | RK7 | L3M | -620 / -1085 | -1005 | +1301 / +2278 | +1164 | c=1.00: -620 / -1005 / +1301 | 76 | +0.095 | +0.558 | +0.16 / +0.03 / -0.08 | ok |
|  | RK7 | L6M | -178 / -311 | -1005 | +919 / +1609 | +1164 | c=1.00: -178 / -1005 / +919 | 169 | +0.045 | +0.283 | +0.20 / +0.00 / +0.02 | ok |
|  | RK7 | L3M | +148 / +260 | -3080 | +1607 / +2812 | +996 | c=1.00: +148 / -3080 / +1607 | 61 | +0.206 | +0.969 | +0.16 / -0.15 / +0.05 | ok |
|  | RK7 | L6M | +409 / +715 | -3815 | +2335 / +4087 | +996 | c=1.00: +409 / -3815 / +2335 | 132 | +0.373 | +1.825 | +0.01 / -0.07 / +0.03 | ok |
|  | RK7 | L3M | +4003 / +7005 | -8959 | -1005 / -1760 | -14304 | c=1.00: +4003 / -8959 / -1005 | 104 | -0.090 | -0.719 | +0.10 / +0.19 / +0.30 | RED |
|  | RK7 | L6M | +2498 / +4372 | -8959 | +1313 / +2298 | -14304 | c=1.00: +2498 / -8959 / +1313 | 252 | +0.109 | +1.018 | +0.02 / +0.13 / +0.16 | RED |
|  | RK7 | L3M | +5300 / +9275 | -9944 | +1018 / +1781 | -16481 | c=1.00: +5300 / -9944 / +1018 | 77 | +0.033 | +0.197 | -0.08 / +0.17 / +0.34 | RED |
|  | RK7 | L6M | +3247 / +5683 | -9944 | +1020 / +1785 | -16481 | c=1.00: +3247 / -9944 / +1020 | 166 | +0.082 | +0.504 | +0.03 / +0.15 / +0.23 | RED |
|  | RK7 | L3M | +4454 / +7795 | -8394 | +593 / +1038 | -15124 | c=1.00: +4454 / -8394 / +593 | 127 | +0.037 | +0.363 | +0.02 / +0.39 / +0.34 | RED |
|  | RK7 | L6M | +2688 / +4704 | -8394 | +1645 / +2878 | -15124 | c=1.00: +2688 / -8394 / +1645 | 299 | +0.107 | +1.181 | +0.08 / +0.21 / +0.22 | RED |
|  | RK7 | L3M | +3829 / +6701 | -7245 | +2261 / +3958 | -11200 | c=1.00: +3829 / -7245 / +2261 | 59 | +0.357 | +1.619 | -0.35 / +0.12 / -0.05 | RED |
|  | RK7 | L3M | +773 / +1352 | -5345 | +1432 / +2505 | -1140 | c=1.00: +773 / -5345 / +1432 | 116 | +0.032 | +0.286 | +0.24 / +0.10 / +0.21 | ok |
|  | RK7 | L6M | +655 / +1147 | -5345 | +855 / +1496 | -1140 | c=1.00: +655 / -5345 / +855 | 252 | +0.021 | +0.198 | +0.13 / +0.13 / +0.14 | ok |
|  | RK7 | L3M | +1508 / +2639 | -4055 | -214 / -375 | -5075 | c=1.00: +1508 / -4055 / -214 | 72 | -0.123 | -0.679 | +0.03 / +0.04 / -0.03 | AMBER |
|  | RK7 | L6M | +1032 / +1806 | -4055 | +1009 / +1766 | -5075 | c=1.00: +1032 / -4055 / +1009 | 164 | +0.078 | +0.475 | +0.04 / +0.05 / +0.07 | AMBER |
|  | RK7 | L3M | +1238 / +2166 | -5705 | +250 / +437 | -2768 | c=1.00: +1238 / -5705 / +250 | 151 | -0.006 | -0.065 | +0.04 / +0.06 / +0.11 | ok |
|  | RK7 | L6M | +930 / +1628 | -5705 | +488 / +854 | -2768 | c=1.00: +930 / -5705 / +488 | 375 | +0.012 | +0.173 | -0.06 / +0.07 / -0.02 | ok |
|  | RK7 | L3M | +1538 / +2692 | -100 | +2236 / +3913 | -5954 | c=1.00: +1538 / -100 / +2236 | 60 | +0.335 | +1.547 | +0.06 / -0.20 / +0.17 | AMBER |
|  | RK7 | L6M | +1043 / +1825 | -100 | +2899 / +5073 | -5954 | c=1.00: +1043 / -100 / +2899 | 135 | +0.437 | +2.185 | -0.08 / -0.05 / +0.09 | AMBER |
|  | RK7 | L3M | +1851 / +3240 | -3495 | +1140 / +1994 | -5845 | c=1.00: +1851 / -3495 / +1140 | 184 | +0.073 | +1.036 | +0.12 / +0.24 / +0.15 | AMBER |
|  | RK7 | L6M | +1312 / +2296 | -3495 | +1261 / +2206 | -5845 | c=1.00: +1312 / -3495 / +1261 | 450 | +0.060 | +1.007 | +0.14 / +0.14 / +0.15 | AMBER |
|  | RK7 | L3M | +2902 / +5079 | -4665 | -554 / -970 | -9869 | c=1.00: +2902 / -4665 / -554 | 136 | -0.101 | -1.054 | -0.04 / -0.05 / -0.09 | RED |
|  | RK7 | L6M | +1854 / +3245 | -4665 | +494 / +865 | -9869 | c=1.00: +1854 / -4665 / +494 | 303 | +0.002 | +0.020 | -0.00 / -0.02 / +0.04 | RED |
|  | RK7 | L3M | +2502 / +4378 | -5116 | +596 / +1043 | -8959 | c=1.00: +2502 / -5116 / +596 | 40 | +0.095 | +0.293 | +0.02 / +0.03 / +0.22 | AMBER |
|  | RK7 | L6M | +1611 / +2819 | -5116 | +928 / +1623 | -8959 | c=1.00: +1611 / -5116 / +928 | 81 | +0.183 | +0.550 | +0.08 / -0.04 / +0.08 | AMBER |
|  | RK7 | L3M | +1583 / +2769 | -3333 | +1307 / +2288 | -5791 | c=1.00: +1583 / -3333 / +1307 | 106 | +0.132 | +1.072 | +0.18 / +0.21 / +0.30 | AMBER |
|  | RK7 | L6M | +1113 / +1947 | -3333 | +1878 / +3286 | -5791 | c=1.00: +1113 / -3333 / +1878 | 212 | +0.177 | +1.391 | +0.13 / +0.09 / +0.20 | AMBER |
|  | RK7 | L3M | +3787 / +6626 | -6140 | +81 / +141 | -12301 | c=1.00: +3787 / -6140 / +81 | 71 | -0.120 | -0.655 | -0.04 / -0.01 / +0.30 | RED |
|  | RK7 | L6M | +2469 / +4320 | -6140 | +621 / +1087 | -12301 | c=1.00: +2469 / -6140 / +621 | 163 | -0.003 | -0.019 | +0.03 / +0.02 / +0.25 | RED |
|  | RK7 | L3M | +2116 / +3702 | -3106 | +655 / +1147 | -5497 | c=1.00: +2116 / -3106 / +655 | 204 | +0.031 | +0.494 | +0.22 / +0.19 / +0.30 | AMBER |
|  | RK7 | L6M | +1767 / +3093 | -3106 | +658 / +1152 | -5497 | c=1.00: +1767 / -3106 / +658 | 501 | +0.025 | +0.460 | +0.04 / +0.08 / +0.11 | AMBER |
|  | RK7 | L3M | +1153 / +2017 | -3400 | +2391 / +4184 | -3779 | c=1.00: +1153 / -3400 / +2391 | 56 | +0.417 | +1.795 | +0.05 / +0.11 / +0.26 | ok |
|  | RK7 | L6M | +1125 / +1969 | -4905 | +1417 / +2480 | -3779 | c=1.00: +1125 / -4905 / +1417 | 132 | +0.227 | +1.108 | +0.09 / +0.13 / +0.27 | ok |
|  | RK7 | L3M | +1920 / +3360 | -2722 | +3391 / +5934 | -6010 | c=1.00: +1920 / -2722 / +3391 | 90 | +0.300 | +2.075 | -0.20 / +0.26 / +0.12 | AMBER |
|  | RK7 | L6M | +1418 / +2482 | -2722 | +2392 / +4186 | -6010 | c=1.00: +1418 / -2722 / +2392 | 212 | +0.182 | +1.426 | -0.14 / +0.07 / -0.07 | AMBER |
|  | RK7 | L3M | +943 / +1651 | -5635 | +2913 / +5097 | -2385 | c=1.00: +943 / -5635 / +2913 | 155 | +0.197 | +2.354 | +0.26 / +0.13 / +0.16 | ok |
|  | RK7 | L6M | +605 / +1060 | -5635 | +1426 / +2496 | -2385 | c=1.00: +605 / -5635 / +1426 | 345 | +0.078 | +1.000 | +0.13 / +0.13 / +0.06 | ok |
|  | RK7 | L3M | +1929 / +3376 | -7400 | -437 / -765 | -3756 | c=1.00: +1929 / -7400 / -437 | 72 | -0.051 | -0.285 | -0.21 / +0.02 / -0.06 | AMBER |
|  | RK7 | L6M | +1383 / +2420 | -7400 | +56 / +99 | -3756 | c=1.00: +1383 / -7400 / +56 | 173 | -0.009 | -0.060 | -0.11 / -0.01 / +0.05 | ok |
|  | RK7 | L3M | +1212 / +2120 | -6540 | +2530 / +4428 | -4437 | c=1.00: +1212 / -6540 / +2530 | 57 | +0.328 | +1.437 | +0.21 / +0.03 / +0.08 | ok |
|  | RK7 | L6M | +1013 / +1772 | -6540 | +1797 / +3144 | -4437 | c=1.00: +1013 / -6540 / +1797 | 127 | +0.223 | +1.049 | +0.13 / +0.05 / +0.07 | ok |
|  | RK7 | L3M | +2577 / +4510 | -10490 | +1047 / +1833 | -8025 | c=1.00: +2577 / -10490 / +1047 | 266 | +0.065 | +1.320 | +0.13 / +0.10 / +0.13 | AMBER |
|  | RK7 | L3M | -508 / -889 | -3060 | +2315 / +4051 | +2291 | c=1.00: -508 / -3060 / +2315 | 64 | +0.250 | +1.233 | +0.19 / -0.22 / +0.05 | ok |
|  | RK7 | L6M | +35 / +61 | -3570 | +2301 / +4028 | +1857 | c=1.00: +35 / -3570 / +2301 | 138 | +0.321 | +1.640 | +0.07 / -0.10 / +0.07 | ok |
|  | RK7 | L3M | +3071 / +5375 | -6920 | +821 / +1436 | -11572 | c=1.00: +3071 / -6920 / +821 | 93 | +0.093 | +0.663 | +0.08 / +0.08 / +0.08 | RED |
|  | RK7 | L6M | +2351 / +4115 | -7325 | -236 / -414 | -11572 | c=1.00: +2351 / -7325 / -236 | 192 | -0.035 | -0.248 | +0.04 / +0.08 / +0.09 | RED |
|  | RK7 | L3M | +3071 / +5375 | -6920 | +821 / +1436 | -11572 | c=1.00: +3071 / -6920 / +821 | 93 | +0.093 | +0.663 | +0.08 / +0.08 / +0.08 | RED |
|  | RK7 | L6M | +2351 / +4115 | -7325 | -236 / -414 | -11572 | c=1.00: +2351 / -7325 / -236 | 192 | -0.035 | -0.248 | +0.04 / +0.08 / +0.09 | RED |
|  | RK7 | L3M | +3804 / +6657 | -7194 | +555 / +972 | -12323 | c=1.00: +3804 / -7194 / +555 | 69 | +0.067 | +0.358 | +0.12 / +0.33 / +0.38 | RED |
|  | RK7 | L6M | +2450 / +4287 | -7194 | +844 / +1477 | -12323 | c=1.00: +2450 / -7194 / +844 | 139 | +0.090 | +0.464 | +0.06 / +0.17 / +0.34 | RED |
|  | RK7 | L3M | +1675 / +2931 | -1770 | +2019 / +3534 | -7835 | c=1.00: +1675 / -1770 / +2019 | 90 | +0.217 | +1.501 | +0.04 / +0.20 / +0.30 | AMBER |
|  | RK7 | L6M | +1049 / +1835 | -1770 | +1871 / +3274 | -7835 | c=1.00: +1049 / -1770 / +1871 | 193 | +0.173 | +1.237 | +0.09 / +0.07 / +0.25 | AMBER |
|  | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=1.00: +1894 / -3780 / +589 | 74 | +0.067 | +0.382 | +0.03 / +0.06 / -0.01 | AMBER |
|  | RK7 | L6M | +1487 / +2602 | -3945 | +1090 / +1907 | -6714 | c=1.00: +1487 / -3945 / +1090 | 161 | +0.123 | +0.731 | -0.02 / +0.08 / +0.10 | AMBER |
|  | RK7 | L3M | -283 / -496 | +3268 | -335 / -586 | +2124 | c=1.00: -283 / +3268 / -335 | 132 | -0.018 | -0.180 | +0.45 / +0.20 / +0.39 | ok |
|  | RK7 | L6M | -93 / -163 | +3240 | +284 / +497 | +2124 | c=1.00: -93 / +3240 / +284 | 254 | +0.012 | +0.113 | +0.31 / +0.11 / +0.26 | ok |
|  | RK7 | L3M | +3450 / +6037 | -8248 | -386 / -675 | -10354 | c=1.00: +3450 / -8248 / -386 | 119 | -0.103 | -0.946 | +0.10 / +0.17 / +0.16 | RED |
|  | RK7 | L6M | +2149 / +3761 | -8248 | +753 / +1317 | -10354 | c=1.00: +2149 / -8248 / +753 | 231 | +0.016 | +0.134 | +0.18 / +0.10 / +0.13 | RED |
|  | RK7 | L3M | +5014 / +8774 | -8974 | +2186 / +3825 | -16907 | c=1.00: +5014 / -8974 / +2186 | 108 | +0.162 | +1.342 | -0.04 / +0.39 / +0.31 | RED |
|  | RK7 | L6M | +3102 / +5429 | -8974 | +974 / +1705 | -16907 | c=1.00: +3102 / -8974 / +974 | 275 | +0.047 | +0.483 | +0.01 / +0.20 / +0.14 | RED |
|  | RK7 | L3M | +5937 / +10389 | -9553 | -635 / -1111 | -19250 | c=1.00: +5937 / -9553 / -635 | 111 | -0.090 | -0.765 | -0.01 / +0.27 / +0.41 | RED |
|  | RK7 | L6M | +3710 / +6492 | -9553 | +883 / +1545 | -19250 | c=1.00: +3710 / -9553 / +883 | 281 | +0.059 | +0.613 | +0.01 / +0.19 / +0.14 | RED |
|  | RK7 | L3M | +2641 / +4621 | -4700 | +94 / +164 | -9614 | c=1.00: +2641 / -4700 / +94 | 132 | -0.057 | -0.577 | +0.01 / -0.01 / +0.19 | RED |
|  | RK7 | L6M | +1741 / +3047 | -4700 | +211 / +369 | -9614 | c=1.00: +1741 / -4700 / +211 | 278 | -0.020 | -0.201 | -0.02 / -0.05 / +0.10 | RED |
|  | RK7 | L3M | +717 / +1255 | -314 | +2772 / +4851 | -2862 | c=1.00: +717 / -314 / +2772 | 139 | +0.150 | +1.608 | +0.06 / +0.06 / +0.02 | ok |
|  | RK7 | L6M | +548 / +959 | -314 | +1604 / +2808 | -2862 | c=1.00: +548 / -314 / +1604 | 307 | +0.067 | +0.767 | +0.13 / +0.04 / +0.12 | ok |
|  | RK7 | L3M | +554 / +969 | -3130 | +2238 / +3916 | -2449 | c=1.00: +554 / -3130 / +2238 | 63 | +0.246 | +1.193 | +0.19 / -0.09 / +0.13 | ok |
|  | RK7 | L6M | +397 / +695 | -3130 | +2143 / +3751 | -2449 | c=1.00: +397 / -3130 / +2143 | 134 | +0.295 | +1.462 | +0.10 / -0.07 / +0.13 | ok |
|  | RK7 | L3M | +1083 / +1895 | -6570 | +2339 / +4093 | -4545 | c=1.00: +1083 / -6570 / +2339 | 126 | +0.161 | +1.563 | +0.36 / +0.15 / +0.28 | ok |
|  | RK7 | L6M | +758 / +1326 | -6570 | +1556 / +2723 | -4545 | c=1.00: +758 / -6570 / +1556 | 283 | +0.091 | +0.957 | +0.16 / +0.11 / +0.07 | ok |
|  | RK7 | L3M | +2674 / +4680 | -8184 | +1049 / +1836 | -8732 | c=1.00: +2674 / -8184 / +1049 | 67 | +0.138 | +0.712 | +0.22 / +0.31 / +0.41 | AMBER |
|  | RK7 | L6M | +1802 / +3154 | -8184 | +2161 / +3782 | -8732 | c=1.00: +1802 / -8184 / +2161 | 175 | +0.258 | +1.674 | +0.26 / +0.20 / +0.31 | AMBER |
|  | RK7 | L3M | +1253 / +2193 | +2078 | +762 / +1333 | -2002 | c=1.00: +1253 / +2078 / +762 | 73 | +0.095 | +0.534 | +0.11 / +0.31 / +0.28 | ok |
|  | RK7 | L6M | +967 / +1691 | -1090 | +1486 / +2601 | -2002 | c=1.00: +967 / -1090 / +1486 | 179 | +0.172 | +1.140 | +0.12 / +0.20 / +0.29 | ok |
|  | RK7 | L3M | +1341 / +2346 | -263 | +2262 / +3959 | -6343 | c=1.00: +1341 / -263 / +2262 | 116 | +0.181 | +1.618 | +0.28 / +0.29 / +0.46 | AMBER |
|  | RK7 | L6M | +739 / +1293 | -263 | +1815 / +3176 | -6343 | c=1.00: +739 / -263 / +1815 | 283 | +0.114 | +1.191 | +0.27 / +0.13 / +0.23 | AMBER |
|  | RK7 | L3M | +3202 / +5604 | -2697 | -623 / -1091 | -5915 | c=1.00: +3202 / -2697 / -623 | 89 | -0.063 | -0.432 | -0.11 / +0.15 / -0.29 | AMBER |
|  | RK7 | L6M | +1959 / +3429 | -2697 | +1942 / +3398 | -5915 | c=1.00: +1959 / -2697 / +1942 | 211 | +0.196 | +1.529 | +0.00 / +0.11 / -0.04 | AMBER |
|  | RK7 | L3M | +2839 / +4968 | -7507 | +2540 / +4445 | -8113 | c=1.00: +2839 / -7507 / +2540 | 106 | +0.215 | +1.755 | -0.06 / +0.09 / +0.31 | AMBER |
|  | RK7 | L6M | +2345 / +4104 | -7507 | +1343 / +2351 | -8113 | c=1.00: +2345 / -7507 / +1343 | 255 | +0.101 | +0.953 | +0.05 / +0.01 / +0.18 | AMBER |
|  | RK7 | L3M | +216 / +379 | -2625 | +3043 / +5325 | +1004 | c=1.00: +216 / -2625 / +3043 | 94 | +0.237 | +1.716 | +0.24 / +0.11 / +0.42 | ok |
|  | RK7 | L6M | +67 / +117 | -2625 | +1707 / +2987 | +1004 | c=1.00: +67 / -2625 / +1707 | 211 | +0.111 | +0.869 | +0.14 / +0.11 / +0.24 | ok |
|  | RK7 | L3M | +3305 / +5784 | -4928 | -334 / -584 | -11231 | c=1.00: +3305 / -4928 / -334 | 80 | -0.022 | -0.134 | +0.01 / +0.19 / +0.17 | RED |
|  | RK7 | L6M | +2040 / +3571 | -4928 | +694 / +1215 | -11231 | c=1.00: +2040 / -4928 / +694 | 177 | +0.082 | +0.537 | -0.05 / +0.15 / +0.10 | RED |
|  | RK7 | L3M | +1477 / +2585 | -3954 | +973 / +1704 | -4191 | c=1.00: +1477 / -3954 / +973 | 123 | +0.012 | +0.117 | +0.22 / +0.27 / +0.30 | ok |
|  | RK7 | L6M | +1008 / +1763 | -3954 | +674 / +1180 | -4191 | c=1.00: +1008 / -3954 / +674 | 259 | +0.010 | +0.096 | +0.18 / +0.25 / +0.21 | ok |
|  | RK7 | L3M | +1051 / +1839 | +745 | +1695 / +2966 | -6259 | c=1.00: +1051 / +745 / +1695 | 97 | +0.201 | +1.499 | +0.33 / +0.10 / +0.15 | AMBER |
|  | RK7 | L6M | +527 / +922 | +745 | +950 / +1662 | -6259 | c=1.00: +527 / +745 / +950 | 218 | +0.084 | +0.674 | +0.28 / +0.02 / +0.01 | AMBER |
|  | RK7 | L3M | +2729 / +4776 | -6937 | +727 / +1273 | -9245 | c=1.00: +2729 / -6937 / +727 | 88 | +0.032 | +0.219 | +0.15 / -0.05 / +0.15 | AMBER |
|  | RK7 | L6M | +1847 / +3232 | -6937 | +975 / +1706 | -9245 | c=1.00: +1847 / -6937 / +975 | 193 | +0.066 | +0.474 | +0.12 / +0.04 / +0.14 | AMBER |
|  | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=1.00: +1894 / -3780 / +589 | 74 | +0.067 | +0.382 | +0.03 / +0.06 / -0.01 | AMBER |
|  | RK7 | L3M | +3766 / +6591 | -6054 | +908 / +1590 | -13173 | c=1.00: +3766 / -6054 / +908 | 90 | +0.045 | +0.314 | -0.09 / +0.43 / +0.16 | RED |
|  | RK7 | L6M | +2534 / +4435 | -6054 | +1482 / +2593 | -13173 | c=1.00: +2534 / -6054 / +1482 | 210 | +0.117 | +0.910 | -0.05 / +0.23 / +0.05 | RED |
|  | RK7 | L3M | +1509 / +2640 | -1962 | -33 / -58 | -2958 | c=1.00: +1509 / -1962 / -33 | 116 | -0.026 | -0.232 | -0.10 / +0.06 / +0.01 | ok |
|  | RK7 | L6M | +1129 / +1976 | -1962 | +2243 / +3924 | -2958 | c=1.00: +1129 / -1962 / +2243 | 244 | +0.177 | +1.600 | -0.04 / +0.01 / +0.05 | ok |
|  | RK7 | L3M | +6285 / +10999 | -6194 | -401 / -702 | -20465 | c=1.00: +6285 / -6194 / -401 | 89 | -0.039 | -0.267 | +0.06 / +0.12 / +0.13 | RED |
|  | RK7 | L3M | +579 / +1013 | +1131 | +1965 / +3440 | -612 | c=1.00: +579 / +1131 / +1965 | 213 | +0.058 | +0.943 | +0.21 / +0.11 / +0.40 | ok |
|  | RK7 | L6M | +362 / +634 | +1131 | +2726 / +4770 | -612 | c=1.00: +362 / +1131 / +2726 | 485 | +0.101 | +1.812 | +0.19 / +0.04 / +0.19 | ok |
|  | RK7 | L3M | +2371 / +4149 | -10570 | +1932 / +3382 | -4795 | c=1.00: +2371 / -10570 / +1932 | 68 | +0.206 | +1.076 | +0.01 / +0.15 / +0.27 | AMBER |
|  | RK7 | L6M | +1668 / +2919 | -10570 | -704 / -1233 | -4795 | c=1.00: +1668 / -10570 / -704 | 159 | -0.171 | -1.010 | +0.01 / +0.05 / +0.08 | AMBER |
|  | RK7 | L3M | +6756 / +11822 | -7289 | -1593 / -2787 | -20323 | c=1.00: +6756 / -7289 / -1593 | 79 | -0.203 | -1.231 | +0.11 / +0.19 / +0.20 | RED |
|  | RK7 | L6M | +4461 / +7807 | -7289 | -24 / -43 | -20323 | c=1.00: +4461 / -7289 / -24 | 193 | -0.004 | -0.031 | -0.04 / +0.13 / +0.18 | RED |
|  | RK7 | L3M | +1287 / +2252 | -3120 | +1800 / +3150 | -5514 | c=1.00: +1287 / -3120 / +1800 | 63 | +0.203 | +0.981 | +0.14 / -0.21 / +0.20 | AMBER |
|  | RK7 | L6M | +1052 / +1841 | -3870 | +1790 / +3133 | -5514 | c=1.00: +1052 / -3870 / +1790 | 141 | +0.249 | +1.299 | +0.08 / -0.07 / +0.08 | AMBER |
|  | ADD | L3M | -870 / -1522 | +4026 | +1542 / +2698 | +3571 | c=1.00: -870 / +4026 / +1542 | 137 | +0.123 | +1.293 | +0.29 / +0.22 / +0.37 | ok |
|  | ADD | L6M | -453 / -793 | +1209 | +1117 / +1955 | +3571 | c=1.00: -453 / +1209 / +1117 | 284 | +0.078 | +0.818 | +0.24 / +0.13 / +0.22 | ok |
|  | ADD | L3M | +616 / +1079 | -4543 | -347 / -607 | -2235 | c=1.00: +616 / -4543 / -347 | 144 | -0.003 | -0.037 | +0.05 / +0.12 / +0.13 | ok |
|  | ADD | L6M | +480 / +839 | -4543 | +122 / +213 | -2235 | c=1.00: +480 / -4543 / +122 | 362 | +0.021 | +0.277 | -0.03 / +0.11 / +0.03 | ok |
|  | ADD | L3M | -916 / -1603 | -1005 | +376 / +657 | +4548 | c=1.00: -916 / -1005 / +376 | 60 | +0.067 | +0.311 | +0.11 / -0.02 / +0.26 | ok |
|  | ADD | L6M | -635 / -1112 | -1005 | +564 / +987 | +4548 | c=1.00: -635 / -1005 / +564 | 134 | +0.143 | +0.712 | +0.01 / -0.01 / +0.18 | ok |
|  | ADD | L3M | -564 / -986 | +2395 | +846 / +1481 | +3495 | c=1.00: -564 / +2395 / +846 | 38 | +0.261 | +0.762 | +0.37 / -0.05 / +0.13 | ok |
|  | ADD | L6M | -183 / -321 | -471 | +557 / +976 | +3495 | c=1.00: -183 / -471 / +557 | 89 | +0.131 | +0.431 | +0.14 / -0.04 / +0.26 | ok |
|  | ADD | L3M | +3101 / +5426 | -4559 | +1720 / +3010 | -9032 | c=1.00: +3101 / -4559 / +1720 | 88 | +0.073 | +0.492 | -0.16 / +0.42 / +0.19 | AMBER |
|  | ADD | L6M | +2012 / +3522 | -4559 | +2121 / +3711 | -9032 | c=1.00: +2012 / -4559 / +2121 | 212 | +0.180 | +1.410 | -0.08 / +0.19 / +0.13 | AMBER |
|  | ADD | L3M | -456 / -798 | +1134 | +1935 / +3386 | +2888 | c=1.00: -456 / +1134 / +1935 | 165 | +0.127 | +1.616 | +0.20 / +0.13 / +0.39 | ok |
|  | ADD | L6M | -262 / -458 | +1134 | +1965 / +3439 | +2888 | c=1.00: -262 / +1134 / +1965 | 383 | +0.125 | +1.767 | +0.15 / +0.08 / +0.16 | ok |
|  | ADD | L3M | -8 / -15 | -5150 | +1214 / +2124 | -3058 | c=1.00: -8 / -5150 / +1214 | 127 | +0.119 | +1.163 | +0.15 / -0.01 / +0.20 | ok |
|  | ADD | L6M | +129 / +225 | -5150 | +1452 / +2540 | -3058 | c=1.00: +129 / -5150 / +1452 | 264 | +0.137 | +1.337 | +0.02 / +0.03 / +0.01 | ok |
|  | ADD | L3M | +833 / +1458 | -4696 | -1022 / -1789 | -2260 | c=1.00: +833 / -4696 / -1022 | 61 | -0.170 | -0.798 | +0.16 / -0.02 / +0.20 | ok |
|  | ADD | L6M | +496 / +868 | -4696 | +866 / +1516 | -2260 | c=1.00: +496 / -4696 / +866 | 137 | +0.166 | +0.843 | +0.15 / +0.03 / +0.19 | ok |
|  | ADD | L3M | +3496 / +6118 | -6071 | +533 / +933 | -9516 | c=1.00: +3496 / -6071 / +533 | 214 | +0.021 | +0.338 | +0.12 / +0.10 / +0.23 | RED |
|  | ADD | L6M | +2315 / +4051 | -6071 | +306 / +535 | -9516 | c=1.00: +2315 / -6071 / +306 | 551 | +0.013 | +0.270 | +0.09 / +0.09 / +0.26 | RED |
|  | ADD | L3M | +1505 / +2634 | -1265 | +1153 / +2018 | -6828 | c=1.00: +1505 / -1265 / +1153 | 211 | +0.069 | +1.122 | -0.18 / -0.08 / +0.14 | AMBER |
|  | ADD | L6M | +1067 / +1868 | -1559 | +281 / +491 | -6828 | c=1.00: +1067 / -1559 / +281 | 501 | +0.027 | +0.504 | -0.08 / +0.02 / +0.13 | AMBER |
|  | ADD | L3M | -1351 / -2364 | +4160 | +1962 / +3433 | +4820 | c=1.00: -1351 / +4160 / +1962 | 69 | +0.306 | +1.622 | +0.19 / +0.23 / +0.27 | ok |
|  | ADD | L6M | -796 / -1393 | +4160 | +1023 / +1790 | +4820 | c=1.00: -796 / +4160 / +1023 | 174 | +0.153 | +0.986 | +0.13 / +0.15 / +0.26 | ok |
|  | ADD | L3M | -573 / -1003 | -1431 | +2829 / +4952 | +3696 | c=1.00: -573 / -1431 / +2829 | 90 | +0.263 | +1.819 | +0.23 / +0.27 / +0.19 | ok |
|  | ADD | L6M | -382 / -668 | -1431 | +2047 / +3582 | +3696 | c=1.00: -382 / -1431 / +2047 | 220 | +0.189 | +1.542 | +0.05 / +0.17 / +0.15 | ok |
|  | ADD | L3M | -293 / -513 | -2719 | +680 / +1190 | +2567 | c=1.00: -293 / -2719 / +680 | 68 | +0.004 | +0.022 | +0.07 / -0.04 / +0.03 | ok |
|  | ADD | L6M | -188 / -330 | -2719 | +1200 / +2100 | +2567 | c=1.00: -188 / -2719 / +1200 | 162 | +0.115 | +0.691 | +0.04 / +0.03 / +0.10 | ok |
|  | ADD | L3M | -462 / -808 | -2791 | +2434 / +4259 | +527 | c=1.00: -462 / -2791 / +2434 | 124 | +0.155 | +1.479 | +0.38 / +0.15 / +0.31 | ok |
|  | ADD | L6M | -250 / -437 | -2791 | +1385 / +2423 | +527 | c=1.00: -250 / -2791 / +1385 | 280 | +0.085 | +0.880 | +0.18 / +0.12 / +0.09 | ok |
|  | ADD | L3M | +6563 / +11485 | -8760 | -719 / -1259 | -17768 | c=1.00: +6563 / -8760 / -719 | 91 | -0.046 | -0.320 | +0.14 / +0.24 / +0.30 | RED |
|  | ADD | L6M | +4109 / +7191 | -8760 | +291 / +509 | -17768 | c=1.00: +4109 / -8760 / +291 | 222 | +0.057 | +0.466 | +0.04 / +0.17 / +0.25 | RED |
|  | ADD | L3M | +566 / +991 | -415 | +442 / +774 | -418 | c=1.00: +566 / -415 / +442 | 133 | +0.079 | +0.812 | -0.10 / -0.10 / +0.02 | ok |
|  | ADD | L6M | +246 / +431 | -415 | +1122 / +1963 | -418 | c=1.00: +246 / -415 / +1122 | 268 | +0.116 | +1.148 | -0.12 / -0.07 / +0.03 | ok |
|  | ADD | L3M | -1170 / -2047 | +3034 | +3747 / +6557 | +4739 | c=1.00: -1170 / +3034 / +3747 | 115 | +0.348 | +3.076 | +0.22 / +0.11 / +0.18 | ok |
|  | ADD | L6M | -51 / -89 | +3034 | +1132 / +1981 | -5362 | c=1.00: -51 / +3034 / +1132 | 256 | +0.122 | +1.156 | +0.11 / +0.07 / +0.09 | AMBER |
|  | ADD | L3M | +3534 / +6184 | -1571 | -20 / -34 | -12849 | c=1.00: +3534 / -1571 / -20 | 101 | -0.042 | -0.328 | +0.09 / +0.37 / +0.34 | RED |
|  | ADD | L6M | +2199 / +3848 | -3261 | +771 / +1350 | -12849 | c=1.00: +2199 / -3261 / +771 | 222 | +0.067 | +0.549 | +0.02 / +0.25 / +0.25 | RED |
|  | ADD | L3M | -157 / -274 | +3661 | +2274 / +3979 | +515 | c=1.00: -157 / +3661 / +2274 | 197 | +0.082 | +1.240 | +0.13 / +0.13 / +0.29 | ok |
|  | ADD | L6M | -54 / -94 | +1596 | +2298 / +4021 | +515 | c=1.00: -54 / +1596 / +2298 | 432 | +0.106 | +1.692 | +0.16 / +0.05 / +0.12 | ok |
|  | ADD | L3M | +1898 / +3321 | -3530 | +379 / +663 | -6853 | c=1.00: +1898 / -3530 / +379 | 77 | +0.060 | +0.354 | -0.04 / +0.10 / +0.15 | AMBER |
|  | ADD | L6M | +1035 / +1810 | -3530 | +786 / +1376 | -6853 | c=1.00: +1035 / -3530 / +786 | 195 | +0.093 | +0.674 | -0.07 / +0.12 / +0.08 | AMBER |
|  | ADD | L3M | -849 / -1486 | +1136 | +3640 / +6369 | +2215 | c=1.00: -849 / +1136 / +3640 | 207 | +0.163 | +2.589 | +0.20 / -0.05 / +0.15 | ok |
|  | ADD | L6M | -228 / -400 | -903 | +1639 / +2868 | +2215 | c=1.00: -228 / -903 / +1639 | 481 | +0.073 | +1.304 | +0.10 / -0.02 / +0.16 | ok |
|  | ADD | L3M | -344 / -601 | -2620 | +1128 / +1974 | +2386 | c=1.00: -344 / -2620 / +1128 | 61 | +0.215 | +1.009 | +0.11 / -0.20 / +0.10 | ok |
|  | ADD | L6M | +120 / +210 | -5721 | +1318 / +2307 | +2386 | c=1.00: +120 / -5721 / +1318 | 134 | +0.276 | +1.368 | -0.02 / -0.11 / +0.09 | ok |
|  | ADD | L3M | +1347 / +2358 | -4546 | -627 / -1097 | -3384 | c=1.00: +1347 / -4546 / -627 | 72 | -0.097 | -0.535 | +0.12 / +0.12 / +0.23 | ok |
|  | ADD | L6M | +695 / +1217 | -4546 | -22 / -38 | -3384 | c=1.00: +695 / -4546 / -22 | 154 | +0.026 | +0.151 | +0.08 / +0.02 / +0.18 | ok |
|  | ADD | L3M | -1109 / -1941 | +3906 | +1945 / +3404 | +5826 | c=1.00: -1109 / +3906 / +1945 | 133 | +0.152 | +1.554 | +0.26 / +0.08 / +0.20 | ok |
|  | ADD | L6M | -448 / -785 | -2420 | +1312 / +2295 | +5375 | c=1.00: -448 / -2420 / +1312 | 248 | +0.121 | +1.115 | +0.11 / +0.07 / +0.07 | ok |
|  | ADD | L3M | -1067 / -1868 | +195 | +621 / +1087 | +6421 | c=1.00: -1067 / +195 / +621 | 65 | +0.133 | +0.666 | +0.14 / -0.16 / +0.02 | ok |
|  | ADD | L6M | -353 / -618 | -3261 | +882 / +1543 | +5375 | c=1.00: -353 / -3261 / +882 | 141 | +0.197 | +1.031 | +0.07 / -0.06 / +0.07 | ok |
|  | ADD | L3M | +484 / +847 | -2904 | +754 / +1319 | +1428 | c=1.00: +484 / -2904 / +754 | 60 | +0.168 | +0.778 | -0.05 / +0.20 / +0.01 | ok |
|  | ADD | L6M | +225 / +394 | -2904 | +222 / +388 | +1428 | c=1.00: +225 / -2904 / +222 | 147 | +0.056 | +0.306 | -0.07 / +0.18 / -0.02 | ok |
|  | ADD | L3M | +2170 / +3798 | -3621 | -251 / -440 | -7464 | c=1.00: +2170 / -3621 / -251 | 78 | -0.026 | -0.155 | +0.29 / +0.29 / +0.44 | AMBER |
|  | ADD | L6M | +1359 / +2379 | -3621 | +284 / +498 | -7464 | c=1.00: +1359 / -3621 / +284 | 151 | +0.037 | +0.207 | +0.25 / +0.16 / +0.38 | AMBER |
|  | ADD | L3M | +6011 / +10519 | -8135 | +168 / +294 | -20481 | c=1.00: +6011 / -8135 / +168 | 117 | +0.031 | +0.280 | +0.05 / +0.26 / +0.31 | RED |
|  | ADD | L6M | +3942 / +6898 | -8135 | +1059 / +1853 | -20481 | c=1.00: +3942 / -8135 / +1059 | 292 | +0.104 | +1.127 | +0.00 / +0.16 / +0.15 | RED |
|  | ADD | L3M | -1497 / -2620 | +90 | +1844 / +3227 | +6596 | c=1.00: -1497 / +90 / +1844 | 64 | +0.274 | +1.347 | +0.21 / -0.12 / +0.05 | ok |
|  | ADD | L6M | -593 / -1037 | -3236 | +1339 / +2343 | +5375 | c=1.00: -593 / -3236 / +1339 | 135 | +0.239 | +1.196 | +0.12 / -0.04 / +0.05 | ok |
|  | ADD | L3M | +1220 / +2135 | +2706 | -840 / -1470 | -5191 | c=1.00: +1220 / +2706 / -840 | 89 | -0.189 | -1.297 | +0.02 / -0.05 / +0.02 | AMBER |
|  | ADD | L6M | +806 / +1411 | +2706 | +1137 / +1989 | -5191 | c=1.00: +806 / +2706 / +1137 | 206 | +0.090 | +0.689 | -0.06 / -0.03 / -0.12 | AMBER |
|  | ADD | L3M | +434 / +759 | +1556 | -391 / -684 | -1049 | c=1.00: +434 / +1556 / -391 | 112 | +0.012 | +0.104 | +0.28 / +0.19 / +0.56 | ok |
|  | ADD | L6M | +428 / +749 | +1556 | -289 / -507 | -1049 | c=1.00: +428 / +1556 / -289 | 241 | +0.006 | +0.054 | +0.29 / +0.16 / +0.48 | ok |
|  | ADD | L3M | +103 / +180 | +2791 | +296 / +518 | -1494 | c=1.00: +103 / +2791 / +296 | 158 | +0.015 | +0.183 | +0.26 / -0.09 / -0.04 | ok |
|  | ADD | L6M | +70 / +122 | +2791 | +734 / +1284 | -1494 | c=1.00: +70 / +2791 / +734 | 333 | +0.032 | +0.398 | +0.29 / -0.05 / +0.00 | ok |
|  | ADD | L3M | +272 / +476 | -1681 | +1032 / +1806 | +1383 | c=1.00: +272 / -1681 / +1032 | 83 | +0.157 | +1.002 | -0.01 / +0.25 / +0.15 | ok |
|  | ADD | L6M | +50 / +87 | -1681 | +899 / +1573 | +1383 | c=1.00: +50 / -1681 / +899 | 193 | +0.115 | +0.819 | +0.07 / +0.15 / +0.20 | ok |
|  | ADD | L3M | +1599 / +2799 | -1669 | +1780 / +3115 | -3835 | c=1.00: +1599 / -1669 / +1780 | 71 | +0.103 | +0.562 | +0.04 / +0.26 / +0.31 | ok |
|  | ADD | L6M | +965 / +1689 | -1669 | +407 / +713 | -3835 | c=1.00: +965 / -1669 / +407 | 168 | -0.015 | -0.095 | +0.15 / +0.21 / +0.26 | ok |
|  | ADD | L3M | +1411 / +2469 | -2459 | +82 / +144 | -4492 | c=1.00: +1411 / -2459 / +82 | 70 | +0.030 | +0.161 | +0.06 / +0.22 / -0.02 | ok |
|  | ADD | L6M | +841 / +1472 | -2459 | +11 / +19 | -4492 | c=1.00: +841 / -2459 / +11 | 146 | +0.037 | +0.201 | +0.05 / +0.18 / +0.18 | ok |
|  | ADD | L3M | +946 / +1656 | -869 | +302 / +528 | -3069 | c=1.00: +946 / -869 / +302 | 105 | -0.020 | -0.160 | +0.09 / +0.30 / +0.21 | ok |
|  | ADD | L6M | +518 / +907 | -869 | +918 / +1606 | -3069 | c=1.00: +518 / -869 / +918 | 262 | +0.063 | +0.608 | +0.02 / +0.13 / +0.18 | ok |
|  | ADD | L3M | +56 / +97 | -1109 | +1200 / +2099 | +2350 | c=1.00: +56 / -1109 / +1200 | 85 | +0.086 | +0.563 | +0.25 / +0.03 / +0.24 | ok |
|  | ADD | L6M | +114 / +200 | -1206 | +981 / +1716 | +2350 | c=1.00: +114 / -1206 / +981 | 178 | +0.092 | +0.607 | +0.10 / +0.05 / +0.18 | ok |
|  | ADD | L3M | +311 / +545 | -1686 | -290 / -508 | -1736 | c=1.00: +311 / -1686 / -290 | 141 | -0.032 | -0.349 | +0.04 / +0.11 / +0.18 | ok |
|  | ADD | L6M | +215 / +377 | -1686 | +227 / +397 | -1736 | c=1.00: +215 / -1686 / +227 | 288 | +0.019 | +0.204 | -0.04 / +0.02 / +0.06 | ok |
|  | ADD | L3M | +245 / +429 | +784 | -390 / -682 | +1136 | c=1.00: +245 / +784 / -390 | 71 | -0.046 | -0.252 | -0.09 / +0.07 / +0.07 | ok |
|  | ADD | L6M | +235 / +410 | +784 | +723 / +1265 | +1136 | c=1.00: +235 / +784 / +723 | 174 | +0.113 | +0.728 | -0.00 / +0.04 / -0.01 | ok |
|  | ADD | L3M | +471 / +825 | +1929 | -289 / -506 | +1386 | c=1.00: +471 / +1929 / -289 | 113 | -0.006 | -0.051 | -0.07 / +0.31 / +0.36 | ok |
|  | ADD | L6M | +200 / +351 | +1929 | +438 / +766 | +1386 | c=1.00: +200 / +1929 / +438 | 241 | +0.039 | +0.352 | +0.08 / +0.19 / +0.26 | ok |
|  | ADD | L3M | -912 / -1596 | -194 | +1551 / +2715 | +3421 | c=1.00: -912 / -194 / +1551 | 123 | +0.118 | +1.121 | +0.34 / +0.02 / +0.42 | ok |
|  | ADD | L6M | -561 / -982 | -194 | +1112 / +1946 | +3421 | c=1.00: -561 / -194 / +1112 | 276 | +0.079 | +0.808 | +0.31 / +0.04 / +0.30 | ok |
|  | ADD | L3M | +2741 / +4796 | -1616 | -555 / -972 | -6960 | c=1.00: +2741 / -1616 / -555 | 110 | -0.083 | -0.705 | -0.18 / -0.13 / -0.18 | AMBER |
|  | ADD | L6M | +1930 / +3378 | -1616 | -396 / -693 | -6960 | c=1.00: +1930 / -1616 / -396 | 240 | -0.031 | -0.275 | +0.02 / -0.04 / -0.13 | AMBER |
|  | ADD | L3M | +2394 / +4189 | -12852 | +1604 / +2808 | -11040 | c=1.00: +2394 / -12852 / +1604 | 115 | +0.071 | +0.630 | +0.18 / +0.25 / +0.28 | RED |
|  | ADD | L6M | +1380 / +2415 | -12852 | +2057 / +3600 | -11040 | c=1.00: +1380 / -12852 / +2057 | 264 | +0.145 | +1.416 | +0.13 / +0.15 / +0.28 | RED |
|  | ADD | L3M | +1283 / +2245 | -2885 | +614 / +1074 | -5688 | c=1.00: +1283 / -2885 / +614 | 170 | +0.076 | +0.989 | -0.35 / -0.23 / -0.15 | AMBER |
|  | ADD | L6M | +725 / +1268 | -2885 | +235 / +411 | -5688 | c=1.00: +725 / -2885 / +235 | 368 | +0.042 | +0.571 | -0.17 / -0.10 / -0.22 | AMBER |
|  | ADD | L3M | +1858 / +3252 | -4908 | +86 / +151 | -7367 | c=1.00: +1858 / -4908 / +86 | 76 | +0.057 | +0.333 | +0.19 / +0.03 / +0.20 | AMBER |
|  | ADD | L6M | +1154 / +2020 | -4908 | -43 / -75 | -7367 | c=1.00: +1154 / -4908 / -43 | 176 | +0.001 | +0.007 | +0.07 / +0.04 / +0.12 | AMBER |
|  | ADD | L3M | +913 / +1599 | -71 | -211 / -369 | -3719 | c=1.00: +913 / -71 / -211 | 71 | -0.025 | -0.135 | +0.12 / +0.12 / -0.11 | ok |
|  | ADD | L6M | +561 / +981 | -71 | +1110 / +1943 | -3719 | c=1.00: +561 / -71 / +1110 | 153 | +0.182 | +1.034 | +0.04 / +0.09 / +0.02 | ok |
|  | ADD | L3M | +1436 / +2513 | -6366 | +80 / +140 | -3700 | c=1.00: +1436 / -6366 / +80 | 74 | +0.014 | +0.079 | -0.02 / +0.04 / +0.33 | ok |
|  | ADD | L6M | +830 / +1452 | -6366 | +984 / +1722 | -3700 | c=1.00: +830 / -6366 / +984 | 156 | +0.153 | +0.885 | -0.06 / +0.01 / +0.13 | ok |
|  | ADD | L3M | -314 / -550 | +966 | +452 / +791 | +3585 | c=1.00: -314 / +966 / +452 | 100 | +0.004 | +0.029 | +0.31 / +0.36 / +0.39 | ok |
|  | ADD | L6M | -257 / -450 | +966 | +872 / +1527 | +3585 | c=1.00: -257 / +966 / +872 | 203 | +0.071 | +0.532 | +0.18 / +0.20 / +0.07 | ok |
|  | ADD | L3M | +154 / +269 | -2674 | -173 / -303 | -939 | c=1.00: +154 / -2674 / -173 | 69 | +0.001 | +0.005 | -0.02 / -0.03 / -0.12 | ok |
|  | ADD | L6M | +116 / +203 | -2674 | -255 / -447 | -939 | c=1.00: +116 / -2674 / -255 | 150 | +0.011 | +0.060 | -0.01 / +0.04 / +0.13 | ok |
|  | ADD | L3M | -1172 / -2051 | +3906 | +2247 / +3933 | +5826 | c=1.00: -1172 / +3906 / +2247 | 129 | +0.181 | +1.793 | +0.27 / +0.08 / +0.16 | ok |
|  | ADD | L6M | -483 / -845 | -2420 | +1457 / +2550 | +5375 | c=1.00: -483 / -2420 / +1457 | 244 | +0.136 | +1.230 | +0.11 / +0.07 / +0.04 | ok |
|  | ADD | L3M | +4408 / +7714 | -545 | -1911 / -3345 | -14967 | c=1.00: +4408 / -545 / -1911 | 55 | -0.214 | -0.906 | -0.06 / +0.05 / +0.04 | RED |
|  | ADD | L6M | +2721 / +4762 | -545 | -747 / -1307 | -14967 | c=1.00: +2721 / -545 / -747 | 132 | -0.045 | -0.222 | +0.03 / -0.03 / +0.02 | RED |
|  | ADD | L3M | -353 / -617 | -2705 | +1632 / +2856 | +2446 | c=1.00: -353 / -2705 / +1632 | 61 | +0.305 | +1.429 | +0.20 / -0.02 / +0.06 | ok |
|  | ADD | L6M | -13 / -24 | -3226 | +1775 / +3107 | +2446 | c=1.00: -13 / -3226 / +1775 | 135 | +0.350 | +1.749 | +0.05 / +0.02 / +0.04 | ok |
|  | ADD | L3M | +2110 / +3693 | -2255 | +51 / +89 | -8987 | c=1.00: +2110 / -2255 / +51 | 104 | +0.024 | +0.191 | +0.07 / +0.20 / +0.11 | AMBER |
|  | ADD | L6M | +1655 / +2896 | -2255 | +363 / +634 | -8987 | c=1.00: +1655 / -2255 / +363 | 263 | +0.060 | +0.586 | +0.14 / +0.15 / +0.03 | AMBER |
|  | ADD | L3M | -741 / -1297 | -1319 | +2558 / +4477 | +2141 | c=1.00: -741 / -1319 / +2558 | 98 | +0.190 | +1.433 | +0.30 / -0.08 / +0.12 | ok |
|  | ADD | L6M | -483 / -845 | -1319 | +1146 / +2006 | +2141 | c=1.00: -483 / -1319 / +1146 | 215 | +0.086 | +0.684 | +0.22 / -0.12 / -0.04 | ok |
|  | ADD | L3M | -1124 / -1967 | -585 | +403 / +705 | +5291 | c=1.00: -1124 / -585 / +403 | 63 | +0.152 | +0.736 | -0.07 / -0.13 / +0.05 | ok |
|  | ADD | L6M | -503 / -880 | -3141 | +1686 / +2951 | +5291 | c=1.00: -503 / -3141 / +1686 | 145 | +0.328 | +1.764 | -0.07 / -0.08 / -0.02 | ok |
|  | ADD | L3M | -427 / -747 | +2630 | +1632 / +2856 | +2141 | c=1.00: -427 / +2630 / +1632 | 68 | +0.297 | +1.553 | +0.08 / +0.08 / +0.22 | ok |
|  | ADD | L6M | -90 / -158 | -3015 | +1031 / +1804 | +2141 | c=1.00: -90 / -3015 / +1031 | 171 | +0.168 | +1.063 | +0.09 / +0.06 / +0.30 | ok |
|  | ADD | L3M | +965 / +1689 | -2980 | +1298 / +2272 | -3738 | c=1.00: +965 / -2980 / +1298 | 65 | +0.203 | +1.017 | +0.19 / +0.13 / +0.35 | ok |
|  | ADD | L6M | +811 / +1419 | -3111 | +885 / +1548 | -3738 | c=1.00: +811 / -3111 / +885 | 145 | +0.163 | +0.878 | +0.06 / +0.08 / +0.21 | ok |
|  | ADD | L3M | +950 / +1662 | -7204 | -103 / -180 | -4462 | c=1.00: +950 / -7204 / -103 | 67 | +0.026 | +0.136 | +0.09 / +0.02 / +0.03 | ok |
|  | ADD | L6M | +733 / +1283 | -7204 | +633 / +1108 | -4462 | c=1.00: +733 / -7204 / +633 | 158 | +0.127 | +0.746 | +0.06 / +0.08 / +0.15 | ok |
|  | ADD | L3M | +38 / +67 | +134 | +163 / +286 | +1505 | c=1.00: +38 / +134 / +163 | 92 | +0.023 | +0.166 | -0.08 / -0.03 / -0.08 | ok |
|  | ADD | L6M | -35 / -62 | +134 | +837 / +1465 | +1505 | c=1.00: -35 / +134 / +837 | 192 | +0.088 | +0.629 | -0.05 / -0.06 / -0.08 | ok |
|  | ADD | L3M | -763 / -1335 | +904 | +1249 / +2187 | +4490 | c=1.00: -763 / +904 / +1249 | 120 | +0.116 | +1.070 | +0.16 / +0.10 / +0.05 | ok |
|  | ADD | L6M | -460 / -804 | +904 | +1253 / +2193 | +4490 | c=1.00: -460 / +904 / +1253 | 249 | +0.121 | +1.113 | +0.08 / +0.09 / -0.02 | ok |
|  | ADD | L3M | -876 / -1533 | -144 | +936 / +1638 | +2621 | c=1.00: -876 / -144 / +936 | 75 | +0.070 | +0.404 | +0.12 / +0.03 / -0.10 | ok |
|  | ADD | L6M | -436 / -762 | -144 | +460 / +806 | +2621 | c=1.00: -436 / -144 / +460 | 167 | +0.034 | +0.209 | +0.18 / +0.01 / +0.02 | ok |
|  | ADD | L3M | -1010 / -1767 | +135 | +1090 / +1908 | +5286 | c=1.00: -1010 / +135 / +1090 | 62 | +0.205 | +0.977 | +0.16 / -0.15 / +0.04 | ok |
|  | ADD | L6M | -380 / -664 | -3226 | +1856 / +3248 | +5286 | c=1.00: -380 / -3226 / +1856 | 132 | +0.371 | +1.816 | +0.01 / -0.07 / +0.03 | ok |
|  | ADD | L3M | -1087 / -1902 | +3732 | +130 / +228 | +5291 | c=1.00: -1087 / +3732 / +130 | 237 | +0.004 | +0.072 | +0.25 / +0.07 / +0.11 | ok |
|  | ADD | L6M | -723 / -1266 | +3535 | +862 / +1508 | +5291 | c=1.00: -723 / +3535 / +862 | 555 | +0.034 | +0.700 | +0.20 / +0.06 / +0.05 | ok |
|  | ADD | L3M | +1321 / +2311 | -2871 | +803 / +1405 | -3667 | c=1.00: +1321 / -2871 / +803 | 178 | +0.053 | +0.719 | +0.04 / +0.13 / +0.26 | ok |
|  | ADD | L3M | -360 / -631 | +351 | +798 / +1397 | +1311 | c=1.00: -360 / +351 / +798 | 58 | +0.142 | +0.635 | +0.48 / +0.08 / +0.25 | ok |
|  | ADD | L6M | -80 / -140 | +351 | +539 / +943 | +1311 | c=1.00: -80 / +351 / +539 | 110 | +0.121 | +0.493 | +0.32 / +0.12 / +0.20 | ok |
|  | ADD | L3M | +4995 / +8742 | -8490 | -1251 / -2189 | -19122 | c=1.00: +4995 / -8490 / -1251 | 105 | -0.108 | -0.872 | +0.09 / +0.19 / +0.31 | RED |
|  | ADD | L6M | +3012 / +5271 | -8490 | +1043 / +1825 | -19122 | c=1.00: +3012 / -8490 / +1043 | 253 | +0.101 | +0.944 | +0.01 / +0.13 / +0.17 | RED |
|  | ADD | L3M | +764 / +1337 | +773 | +1727 / +3022 | -341 | c=1.00: +764 / +773 / +1727 | 85 | +0.092 | +0.602 | -0.14 / +0.20 / +0.05 | ok |
|  | ADD | L6M | +668 / +1169 | +354 | +1489 / +2605 | -341 | c=1.00: +668 / +354 / +1489 | 206 | +0.118 | +0.901 | -0.05 / +0.03 / +0.07 | ok |
|  | ADD | L3M | +5425 / +9493 | -10670 | +453 / +793 | -15899 | c=1.00: +5425 / -10670 / +453 | 77 | +0.033 | +0.197 | -0.08 / +0.17 / +0.34 | RED |
|  | ADD | L6M | +3256 / +5697 | -10670 | +609 / +1066 | -15899 | c=1.00: +3256 / -10670 / +609 | 165 | +0.083 | +0.505 | +0.03 / +0.15 / +0.23 | RED |
|  | ADD | L3M | -99 / -174 | +1195 | -1447 / -2532 | +90 | c=1.00: -99 / +1195 / -1447 | 80 | -0.081 | -0.496 | -0.07 / -0.19 / -0.20 | ok |
|  | ADD | L6M | +6 / +10 | +1195 | -330 / -577 | +90 | c=1.00: +6 / +1195 / -330 | 166 | +0.029 | +0.178 | -0.02 / -0.09 / -0.20 | ok |
|  | ADD | L3M | +3467 / +6068 | -7925 | +376 / +659 | -13157 | c=1.00: +3467 / -7925 / +376 | 128 | +0.048 | +0.473 | +0.00 / +0.37 / +0.33 | RED |
|  | ADD | L6M | +2031 / +3554 | -7925 | +1318 / +2307 | -13157 | c=1.00: +2031 / -7925 / +1318 | 299 | +0.111 | +1.234 | +0.07 / +0.20 / +0.21 | RED |
|  | ADD | L3M | +1681 / +2942 | -5285 | +1772 / +3101 | -5519 | c=1.00: +1681 / -5285 / +1772 | 59 | +0.357 | +1.619 | -0.35 / +0.12 / -0.05 | AMBER |
|  | ADD | L6M | +1219 / +2133 | -5285 | +611 / +1068 | -5519 | c=1.00: +1219 / -5285 / +611 | 149 | +0.135 | +0.747 | -0.20 / +0.12 / -0.11 | AMBER |
|  | ADD | L3M | -1452 / -2542 | +90 | +978 / +1712 | +6626 | c=1.00: -1452 / +90 / +978 | 64 | +0.143 | +0.703 | +0.20 / -0.15 / +0.07 | ok |
|  | ADD | L6M | -618 / -1082 | -3171 | +1301 / +2276 | +5375 | c=1.00: -618 / -3171 / +1301 | 139 | +0.246 | +1.266 | +0.05 / -0.08 / +0.04 | ok |
|  | ADD | L3M | -632 / -1106 | -1471 | +546 / +956 | +4027 | c=1.00: -632 / -1471 / +546 | 115 | +0.032 | +0.285 | +0.25 / +0.12 / +0.22 | ok |
|  | ADD | L6M | -283 / -496 | -1471 | +255 / +446 | +4027 | c=1.00: -283 / -1471 / +255 | 249 | +0.020 | +0.185 | +0.14 / +0.14 / +0.15 | ok |
|  | ADD | L3M | +1066 / +1865 | -4319 | -412 / -721 | -3503 | c=1.00: +1066 / -4319 / -412 | 71 | -0.149 | -0.816 | -0.00 / +0.04 / -0.05 | ok |
|  | ADD | L6M | +648 / +1134 | -4319 | +799 / +1397 | -3503 | c=1.00: +648 / -4319 / +799 | 162 | +0.073 | +0.438 | +0.02 / +0.05 / +0.07 | ok |
|  | ADD | L3M | +225 / +393 | -4543 | -449 / -787 | +270 | c=1.00: +225 / -4543 / -449 | 149 | +0.008 | +0.089 | +0.05 / +0.06 / +0.09 | ok |
|  | ADD | L6M | +201 / +352 | -4543 | +7 / +12 | +270 | c=1.00: +201 / -4543 / +7 | 372 | +0.021 | +0.283 | -0.06 / +0.07 / -0.03 | ok |
|  | ADD | L3M | +1678 / +2937 | -4571 | -1067 / -1868 | -7943 | c=1.00: +1678 / -4571 / -1067 | 136 | -0.031 | -0.326 | -0.08 / +0.01 / -0.10 | AMBER |
|  | ADD | L6M | +1082 / +1893 | -4571 | +30 / +52 | -7943 | c=1.00: +1082 / -4571 / +30 | 281 | +0.041 | +0.430 | -0.10 / +0.03 / -0.10 | AMBER |
|  | ADD | L3M | -420 / -735 | +2985 | +1802 / +3154 | +726 | c=1.00: -420 / +2985 / +1802 | 60 | +0.335 | +1.547 | +0.06 / -0.20 / +0.17 | ok |
|  | ADD | L6M | -255 / -447 | +1609 | +2513 / +4397 | +726 | c=1.00: -255 / +1609 / +2513 | 134 | +0.439 | +2.180 | -0.08 / -0.05 / +0.09 | ok |
|  | ADD | L3M | +2834 / +4959 | -5585 | +1087 / +1902 | -9744 | c=1.00: +2834 / -5585 / +1087 | 88 | +0.084 | +0.570 | -0.08 / +0.41 / +0.15 | RED |
|  | ADD | L6M | +1836 / +3213 | -5585 | +1370 / +2397 | -9744 | c=1.00: +1836 / -5585 / +1370 | 207 | +0.136 | +1.043 | -0.05 / +0.21 / +0.04 | RED |
|  | ADD | L3M | +476 / +832 | +616 | +1242 / +2173 | -843 | c=1.00: +476 / +616 / +1242 | 188 | +0.082 | +1.185 | +0.16 / +0.23 / +0.15 | ok |
|  | ADD | L6M | +381 / +666 | -2530 | +1210 / +2117 | -843 | c=1.00: +381 / -2530 / +1210 | 453 | +0.063 | +1.054 | +0.16 / +0.14 / +0.15 | ok |
|  | ADD | L3M | +1815 / +3176 | -1051 | -1639 / -2869 | -6824 | c=1.00: +1815 / -1051 / -1639 | 140 | -0.100 | -1.082 | -0.05 / -0.05 / -0.09 | AMBER |
|  | ADD | L6M | +1077 / +1885 | -1051 | -303 / -531 | -6824 | c=1.00: +1077 / -1051 / -303 | 305 | +0.002 | +0.025 | -0.01 / -0.02 / +0.05 | AMBER |
|  | ADD | L3M | +1424 / +2492 | -3732 | +23 / +40 | -5767 | c=1.00: +1424 / -3732 / +23 | 40 | +0.095 | +0.293 | +0.02 / +0.03 / +0.22 | AMBER |
|  | ADD | L6M | +840 / +1470 | -3732 | +465 / +813 | -5767 | c=1.00: +840 / -3732 / +465 | 80 | +0.187 | +0.554 | +0.08 / -0.04 / +0.08 | AMBER |
|  | ADD | L3M | +1597 / +2794 | -4060 | +863 / +1510 | -6723 | c=1.00: +1597 / -4060 / +863 | 106 | +0.132 | +1.072 | +0.18 / +0.21 / +0.30 | AMBER |
|  | ADD | L6M | +981 / +1716 | -4060 | +1454 / +2544 | -6723 | c=1.00: +981 / -4060 / +1454 | 211 | +0.173 | +1.354 | +0.12 / +0.09 / +0.20 | AMBER |
|  | ADD | L3M | +3631 / +6355 | -5279 | -461 / -807 | -11052 | c=1.00: +3631 / -5279 / -461 | 70 | -0.150 | -0.809 | -0.08 / -0.01 / +0.29 | RED |
|  | ADD | L6M | +2248 / +3933 | -5279 | +269 / +471 | -11052 | c=1.00: +2248 / -5279 / +269 | 161 | -0.011 | -0.063 | +0.00 / +0.02 / +0.24 | RED |
|  | ADD | L3M | +1536 / +2688 | -2958 | +320 / +560 | -4034 | c=1.00: +1536 / -2958 / +320 | 204 | +0.025 | +0.398 | +0.21 / +0.19 / +0.31 | ok |
|  | ADD | L6M | +1489 / +2605 | -2958 | +137 / +240 | -4687 | c=1.00: +1489 / -2958 / +137 | 501 | +0.022 | +0.414 | +0.03 / +0.08 / +0.11 | AMBER |
|  | ADD | L3M | -273 / -478 | -314 | +1876 / +3283 | +511 | c=1.00: -273 / -314 / +1876 | 56 | +0.417 | +1.795 | +0.05 / +0.11 / +0.26 | ok |
|  | ADD | L6M | +195 / +342 | -4316 | +1020 / +1784 | +511 | c=1.00: +195 / -4316 / +1020 | 132 | +0.227 | +1.108 | +0.09 / +0.13 / +0.27 | ok |
|  | ADD | L3M | +1111 / +1945 | +728 | +3379 / +5913 | -3137 | c=1.00: +1111 / +728 / +3379 | 89 | +0.326 | +2.228 | -0.17 / +0.26 / +0.13 | ok |
|  | ADD | L6M | +847 / +1483 | +728 | +1995 / +3491 | -3137 | c=1.00: +847 / +728 / +1995 | 211 | +0.192 | +1.499 | -0.13 / +0.07 / -0.06 | ok |
|  | ADD | L3M | +1090 / +1907 | -7456 | +2426 / +4246 | -2914 | c=1.00: +1090 / -7456 / +2426 | 152 | +0.207 | +2.422 | +0.23 / +0.13 / +0.13 | ok |
|  | ADD | L6M | +563 / +985 | -7456 | +1149 / +2010 | -2914 | c=1.00: +563 / -7456 / +1149 | 341 | +0.085 | +1.070 | +0.11 / +0.13 / +0.05 | ok |
|  | ADD | L3M | +878 / +1537 | -3885 | +163 / +285 | -1802 | c=1.00: +878 / -3885 / +163 | 68 | +0.011 | +0.057 | +0.15 / +0.26 / +0.28 | ok |
|  | ADD | L3M | +187 / +328 | -4314 | -528 / -925 | +2483 | c=1.00: +187 / -4314 / -528 | 71 | -0.080 | -0.439 | -0.24 / +0.02 / -0.08 | ok |
|  | ADD | L6M | +213 / +372 | -4314 | -260 / -455 | +2483 | c=1.00: +213 / -4314 / -260 | 171 | -0.025 | -0.156 | -0.13 / -0.01 / +0.04 | ok |
|  | ADD | L3M | -389 / -680 | -3780 | +1541 / +2696 | +1336 | c=1.00: -389 / -3780 / +1541 | 56 | +0.293 | +1.262 | +0.18 / +0.03 / +0.06 | ok |
|  | ADD | L6M | -35 / -62 | -3780 | +1155 / +2022 | +1336 | c=1.00: -35 / -3780 / +1155 | 125 | +0.206 | +0.952 | +0.11 / +0.05 / +0.06 | ok |
|  | ADD | L3M | +2397 / +4195 | -11411 | +1061 / +1856 | -7444 | c=1.00: +2397 / -11411 / +1061 | 265 | +0.064 | +1.306 | +0.13 / +0.10 / +0.13 | AMBER |
|  | ADD | L6M | +1402 / +2454 | -11411 | +1191 / +2084 | -7444 | c=1.00: +1402 / -11411 / +1191 | 564 | +0.045 | +0.944 | +0.21 / +0.07 / +0.16 | AMBER |
|  | ADD | L3M | -1582 / -2768 | +145 | +1532 / +2681 | +6581 | c=1.00: -1582 / +145 / +1532 | 64 | +0.221 | +1.087 | +0.17 / -0.22 / +0.04 | ok |
|  | ADD | L3M | +1097 / +1919 | -3256 | +603 / +1056 | -5742 | c=1.00: +1097 / -3256 / +603 | 92 | +0.100 | +0.706 | +0.08 / +0.07 / +0.06 | AMBER |
|  | ADD | L6M | +1034 / +1810 | -6735 | -506 / -886 | -5742 | c=1.00: +1034 / -6735 / -506 | 190 | -0.028 | -0.195 | +0.04 / +0.08 / +0.09 | AMBER |
|  | ADD | L3M | +705 / +1233 | -2900 | -428 / -749 | -3255 | c=1.00: +705 / -2900 / -428 | 64 | -0.010 | -0.051 | -0.19 / +0.04 / -0.03 | ok |
|  | ADD | L6M | +490 / +858 | -2900 | -16 / -28 | -3255 | c=1.00: +490 / -2900 / -16 | 149 | +0.033 | +0.183 | -0.04 / +0.02 / +0.12 | ok |
|  | ADD | L3M | +1097 / +1919 | -3256 | +603 / +1056 | -5742 | c=1.00: +1097 / -3256 / +603 | 92 | +0.100 | +0.706 | +0.08 / +0.07 / +0.06 | AMBER |
|  | ADD | L6M | +1034 / +1810 | -6735 | -506 / -886 | -5742 | c=1.00: +1034 / -6735 / -506 | 190 | -0.028 | -0.195 | +0.04 / +0.08 / +0.09 | AMBER |
|  | ADD | L3M | +3229 / +5652 | -7920 | +113 / +198 | -10820 | c=1.00: +3229 / -7920 / +113 | 69 | +0.067 | +0.358 | +0.12 / +0.33 / +0.38 | RED |
|  | ADD | L6M | +1977 / +3460 | -7920 | +507 / +888 | -10820 | c=1.00: +1977 / -7920 / +507 | 138 | +0.091 | +0.467 | +0.06 / +0.17 / +0.34 | RED |
|  | ADD | L3M | +711 / +1244 | -910 | +1225 / +2143 | -4573 | c=1.00: +711 / -910 / +1225 | 86 | +0.191 | +1.263 | +0.03 / +0.21 / +0.29 | ok |
|  | ADD | L6M | +348 / +610 | -910 | +1318 / +2307 | -4573 | c=1.00: +348 / -910 / +1318 | 190 | +0.153 | +1.075 | +0.08 / +0.08 / +0.25 | ok |
|  | ADD | L3M | +2166 / +3790 | -2680 | -870 / -1523 | -5136 | c=1.00: +2166 / -2680 / -870 | 221 | -0.040 | -0.675 | +0.22 / +0.20 / +0.50 | AMBER |
|  | ADD | L6M | +1260 / +2205 | -2680 | +413 / +723 | -5136 | c=1.00: +1260 / -2680 / +413 | 483 | +0.022 | +0.396 | +0.20 / +0.13 / +0.37 | AMBER |
|  | ADD | L3M | +594 / +1040 | -2919 | +226 / +396 | -2178 | c=1.00: +594 / -2919 / +226 | 73 | +0.041 | +0.228 | -0.01 / +0.07 / -0.03 | ok |
|  | ADD | L6M | +562 / +984 | -3356 | +800 / +1400 | -2178 | c=1.00: +562 / -3356 / +800 | 159 | +0.116 | +0.686 | -0.04 / +0.09 / +0.09 | ok |
|  | ADD | L3M | -67 / -116 | +2610 | +2117 / +3704 | +150 | c=1.00: -67 / +2610 / +2117 | 50 | +0.345 | +1.327 | +0.15 / +0.07 / +0.20 | ok |
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
|  | ADD | L3M | +1464 / +2563 | -881 | -924 / -1617 | -6439 | c=1.00: +1464 / -881 / -924 | 135 | -0.049 | -0.507 | +0.04 / -0.01 / +0.20 | AMBER |
|  | ADD | L6M | +916 / +1604 | -881 | -554 / -970 | -6439 | c=1.00: +916 / -881 / -554 | 278 | -0.013 | -0.132 | -0.01 / -0.05 / +0.10 | AMBER |
|  | ADD | L3M | +920 / +1609 | -2635 | -489 / -855 | +159 | c=1.00: +920 / -2635 / -489 | 126 | +0.020 | +0.191 | +0.18 / +0.13 / +0.22 | ok |
|  | ADD | L6M | +610 / +1067 | -2635 | -153 / -267 | +159 | c=1.00: +610 / -2635 / -153 | 298 | +0.016 | +0.178 | +0.12 / +0.08 / +0.19 | ok |
|  | ADD | L3M | +120 / +210 | +1281 | +2701 / +4727 | -1375 | c=1.00: +120 / +1281 / +2701 | 138 | +0.159 | +1.684 | +0.07 / +0.04 / +0.02 | ok |
|  | ADD | L6M | +101 / +177 | +1281 | +1508 / +2639 | -1375 | c=1.00: +101 / +1281 / +1508 | 306 | +0.071 | +0.804 | +0.13 / +0.03 / +0.11 | ok |
|  | ADD | L3M | +1436 / +2513 | -6366 | +270 / +472 | -3700 | c=1.00: +1436 / -6366 / +270 | 73 | +0.042 | +0.238 | -0.02 / +0.04 / +0.36 | ok |
|  | ADD | L6M | +836 / +1463 | -6366 | +1270 / +2223 | -3700 | c=1.00: +836 / -6366 / +1270 | 157 | +0.193 | +1.123 | -0.06 / +0.00 / +0.15 | ok |
|  | ADD | L3M | +4051 / +7090 | -8375 | -783 / -1371 | -13244 | c=1.00: +4051 / -8375 / -783 | 91 | -0.098 | -0.684 | -0.04 / +0.25 / +0.16 | RED |
|  | ADD | L6M | +2462 / +4309 | -8375 | +64 / +111 | -13244 | c=1.00: +2462 / -8375 / +64 | 213 | +0.016 | +0.125 | +0.07 / +0.19 / +0.17 | RED |
|  | ADD | L3M | -671 / -1175 | +40 | +1609 / +2815 | +1841 | c=1.00: -671 / +40 / +1609 | 63 | +0.263 | +1.276 | +0.21 / -0.09 / +0.14 | ok |
|  | ADD | L6M | -446 / -781 | +40 | +1630 / +2852 | +1841 | c=1.00: -446 / +40 / +1630 | 133 | +0.301 | +1.482 | +0.11 / -0.07 / +0.13 | ok |
|  | ADD | L3M | -462 / -808 | -2791 | +2434 / +4259 | +527 | c=1.00: -462 / -2791 / +2434 | 124 | +0.155 | +1.479 | +0.38 / +0.15 / +0.31 | ok |
|  | ADD | L6M | -250 / -437 | -2791 | +1385 / +2423 | +527 | c=1.00: -250 / -2791 / +1385 | 280 | +0.085 | +0.880 | +0.18 / +0.12 / +0.09 | ok |
|  | ADD | L3M | +1458 / +2551 | -7620 | +913 / +1597 | -5985 | c=1.00: +1458 / -7620 / +913 | 65 | +0.167 | +0.835 | +0.21 / +0.28 / +0.40 | AMBER |
|  | ADD | L6M | +969 / +1695 | -7620 | +2010 / +3518 | -5985 | c=1.00: +969 / -7620 / +2010 | 172 | +0.264 | +1.684 | +0.26 / +0.18 / +0.31 | AMBER |
|  | ADD | L3M | +527 / +923 | +3090 | +763 / +1334 | +508 | c=1.00: +527 / +3090 / +763 | 73 | +0.095 | +0.534 | +0.11 / +0.31 / +0.28 | ok |
|  | ADD | L6M | +375 / +656 | -501 | +1325 / +2319 | +508 | c=1.00: +375 / -501 / +1325 | 178 | +0.177 | +1.166 | +0.12 / +0.20 / +0.29 | ok |
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
|  | ADD | L3M | +2588 / +4529 | -4460 | -849 / -1486 | -10451 | c=1.00: +2588 / -4460 / -849 | 80 | -0.022 | -0.134 | +0.01 / +0.19 / +0.17 | RED |
|  | ADD | L6M | +1497 / +2619 | -4460 | +301 / +526 | -10451 | c=1.00: +1497 / -4460 / +301 | 177 | +0.082 | +0.537 | -0.05 / +0.15 / +0.10 | RED |
|  | ADD | L3M | -1053 / -1843 | +247 | +464 / +812 | +4764 | c=1.00: -1053 / +247 / +464 | 109 | +0.059 | +0.493 | +0.21 / +0.01 / +0.19 | ok |
|  | ADD | L6M | -625 / -1093 | +247 | +785 / +1374 | +4764 | c=1.00: -625 / +247 / +785 | 216 | +0.080 | +0.644 | +0.16 / +0.02 / +0.20 | ok |
|  | ADD | L3M | +1678 / +2936 | -4680 | -154 / -270 | -4798 | c=1.00: +1678 / -4680 / -154 | 122 | +0.004 | +0.040 | +0.25 / +0.28 / +0.30 | AMBER |
|  | ADD | L6M | +1011 / +1768 | -4680 | -181 / -318 | -4798 | c=1.00: +1011 / -4680 / -181 | 257 | +0.002 | +0.023 | +0.19 / +0.25 / +0.19 | AMBER |
|  | ADD | L3M | +387 / +677 | -3500 | +3660 / +6404 | -3595 | c=1.00: +387 / -3500 / +3660 | 171 | +0.212 | +2.794 | +0.08 / +0.06 / +0.08 | ok |
|  | ADD | L6M | +299 / +523 | -3500 | +1283 / +2245 | -3595 | c=1.00: +299 / -3500 / +1283 | 344 | +0.079 | +1.005 | +0.05 / +0.11 / -0.03 | ok |
|  | ADD | L3M | +1168 / +2044 | +1606 | +1259 / +2203 | -6114 | c=1.00: +1168 / +1606 / +1259 | 97 | +0.177 | +1.323 | +0.30 / +0.10 / +0.14 | AMBER |
|  | ADD | L6M | +593 / +1037 | +1606 | +483 / +845 | -6114 | c=1.00: +593 / +1606 / +483 | 217 | +0.074 | +0.595 | +0.26 / +0.02 / -0.00 | AMBER |
|  | ADD | L3M | +970 / +1698 | -3845 | +31 / +54 | -2760 | c=1.00: +970 / -3845 / +31 | 88 | +0.032 | +0.217 | +0.15 / -0.05 / +0.15 | ok |
|  | ADD | L6M | +717 / +1255 | -3845 | +198 / +346 | -2760 | c=1.00: +717 / -3845 / +198 | 188 | +0.062 | +0.429 | +0.11 / +0.04 / +0.12 | ok |
|  | ADD | L3M | +594 / +1040 | -2919 | +226 / +396 | -2178 | c=1.00: +594 / -2919 / +226 | 73 | +0.041 | +0.228 | -0.01 / +0.07 / -0.03 | ok |
|  | ADD | L6M | +562 / +984 | -3356 | +800 / +1400 | -2178 | c=1.00: +562 / -3356 / +800 | 159 | +0.116 | +0.686 | -0.04 / +0.09 / +0.09 | ok |
|  | ADD | L3M | +2268 / +3970 | -6790 | +739 / +1292 | -7234 | c=1.00: +2268 / -6790 / +739 | 60 | +0.182 | +0.840 | -0.38 / -0.01 / -0.09 | AMBER |
|  | ADD | L6M | +1509 / +2640 | -6790 | -145 / -254 | -7234 | c=1.00: +1509 / -6790 / -145 | 147 | +0.008 | +0.041 | -0.22 / -0.08 / -0.13 | AMBER |
|  | ADD | L3M | +2834 / +4959 | -5585 | +1087 / +1902 | -9744 | c=1.00: +2834 / -5585 / +1087 | 88 | +0.084 | +0.570 | -0.08 / +0.41 / +0.15 | RED |
|  | ADD | L6M | +1836 / +3213 | -5585 | +1370 / +2397 | -9744 | c=1.00: +1836 / -5585 / +1370 | 207 | +0.136 | +1.043 | -0.05 / +0.21 / +0.04 | RED |
|  | ADD | L3M | +49 / +85 | +529 | -79 / -138 | +2244 | c=1.00: +49 / +529 / -79 | 113 | -0.026 | -0.224 | -0.09 / +0.08 / +0.02 | ok |
|  | ADD | L6M | +139 / +243 | +279 | +2113 / +3697 | +2244 | c=1.00: +139 / +279 / +2113 | 241 | +0.180 | +1.603 | -0.03 / +0.01 / +0.05 | ok |
|  | ADD | L3M | +7102 / +12429 | -5745 | -515 / -902 | -22905 | c=1.00: +7102 / -5745 / -515 | 88 | -0.014 | -0.095 | +0.08 / +0.12 / +0.14 | RED |
|  | ADD | L6M | +4352 / +7615 | -5745 | +1193 / +2088 | -22905 | c=1.00: +4352 / -5745 / +1193 | 220 | +0.133 | +1.081 | +0.07 / +0.10 / +0.19 | RED |
|  | ADD | L3M | -39 / -68 | +2726 | +2148 / +3759 | +875 | c=1.00: -39 / +2726 / +2148 | 211 | +0.065 | +1.055 | +0.22 / +0.12 / +0.41 | ok |
|  | ADD | L6M | -53 / -93 | +2726 | +2554 / +4469 | +875 | c=1.00: -53 / +2726 / +2554 | 482 | +0.105 | +1.866 | +0.19 / +0.04 / +0.19 | ok |
|  | ADD | L3M | +1284 / +2248 | -8609 | +1939 / +3393 | -1542 | c=1.00: +1284 / -8609 / +1939 | 67 | +0.239 | +1.230 | +0.05 / +0.16 / +0.30 | ok |
|  | ADD | L6M | +889 / +1556 | -8609 | -848 / -1483 | -1542 | c=1.00: +889 / -8609 / -848 | 157 | -0.157 | -0.910 | +0.02 / +0.05 / +0.09 | ok |
|  | ADD | L3M | +5487 / +9602 | -6820 | -1511 / -2644 | -16398 | c=1.00: +5487 / -6820 / -1511 | 79 | -0.184 | -1.118 | +0.12 / +0.19 / +0.19 | RED |
|  | ADD | L6M | +3544 / +6203 | -6820 | -167 / -292 | -16398 | c=1.00: +3544 / -6820 / -167 | 192 | +0.002 | +0.017 | -0.03 / +0.13 / +0.18 | RED |
|  | ADD | L3M | +1438 / +2517 | -1445 | +44 / +77 | -4116 | c=1.00: +1438 / -1445 / +44 | 132 | -0.004 | -0.039 | +0.05 / +0.06 / +0.29 | ok |
|  | ADD | L6M | +798 / +1397 | -1445 | +772 / +1351 | -4116 | c=1.00: +798 / -1445 / +772 | 281 | +0.064 | +0.662 | -0.03 / +0.08 / +0.10 | ok |
|  | ADD | L3M | -467 / -818 | -60 | +1070 / +1872 | +1166 | c=1.00: -467 / -60 / +1070 | 64 | +0.199 | +0.980 | +0.14 / -0.21 / +0.20 | ok |
|  | ADD | L6M | -78 / -136 | -3281 | +1202 / +2104 | +1166 | c=1.00: -78 / -3281 / +1202 | 141 | +0.255 | +1.334 | +0.08 / -0.07 / +0.08 | ok |
| L02831614 | RK7 | L3M | +3594 / +6289 | -6905 | -1417 / -2480 | -9674 | c=0.50: +2417 / -4995 / -421 | 66 | -0.164 | -0.830 | -0.11 / +0.08 / +0.04 | RED |
| L02831614 | RK7 | L6M | +2399 / +4198 | -6905 | -1175 / -2057 | -9674 | c=0.50: +1620 / -4995 / -411 | 164 | -0.105 | -0.637 | -0.06 / +0.05 / -0.14 | RED |
| L02831614 | ADD | L3M | +2154 / +3770 | -3819 | -1223 / -2140 | -6573 | c=0.50: +1187 / -1910 / -319 | 65 | -0.151 | -0.753 | -0.07 / +0.08 / +0.06 | AMBER |
| L02831614 | ADD | L6M | +1399 / +2449 | -3819 | -1192 / -2087 | -6573 | c=0.50: +748 / -1910 / -459 | 162 | -0.102 | -0.611 | -0.04 / +0.05 / -0.13 | AMBER |
| L04f971dd | RK7 | L3M | +77 / +135 | -317 | +479 / +839 | +1478 | c=1.00: +77 / -317 / +479 | 134 | +0.040 | +0.413 | +0.22 / +0.20 / +0.52 | ok |
| L04f971dd | RK7 | L6M | +147 / +258 | -317 | +960 / +1679 | +1478 | c=1.00: +147 / -317 / +960 | 274 | +0.069 | +0.700 | +0.19 / +0.19 / +0.27 | ok |
| L04f971dd | ADD | L3M | -651 / -1140 | +2680 | +825 / +1443 | +2850 | c=1.00: -651 / +2680 / +825 | 132 | +0.039 | +0.391 | +0.22 / +0.20 / +0.52 | ok |
| L04f971dd | ADD | L6M | -391 / -684 | +1590 | +1064 / +1862 | +2850 | c=1.00: -391 / +1590 / +1064 | 272 | +0.068 | +0.689 | +0.19 / +0.19 / +0.27 | ok |
| L081c7427 | ADD | L3M | +43 / +76 | +351 | +528 / +925 | +115 | c=1.00: +43 / +351 / +528 | 71 | +0.068 | +0.369 | +0.34 / +0.20 / +0.29 | ok |
| L081c7427 | ADD | L6M | +170 / +297 | +351 | -181 / -317 | +115 | c=1.00: +170 / +351 / -181 | 160 | -0.026 | -0.155 | +0.22 / +0.17 / +0.13 | ok |
| L0f097450 | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=0.50: +290 / -3103 / +1882 | 62 | +0.178 | +0.849 | +0.25 / -0.07 / +0.11 | ok |
| L0f097450 | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=0.50: +318 / -3103 / +1302 | 136 | +0.164 | +0.825 | +0.06 / -0.03 / +0.02 | ok |
| L0f097450 | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=0.50: -916 / +48 / +1143 | 62 | +0.163 | +0.777 | +0.23 / -0.07 / +0.10 | ok |
| L0f097450 | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=0.50: -500 / +48 / +755 | 135 | +0.156 | +0.780 | +0.05 / -0.03 / +0.01 | ok |
| L252a89c9 | ADD | L3M | -495 / -866 | +295 | +1740 / +3044 | -436 | c=1.00: -495 / +295 / +1740 | 238 | +0.059 | +1.089 | +0.38 / +0.34 / +0.25 | ok |
| L252a89c9 | ADD | L6M | -360 / -629 | +295 | +2030 / +3553 | -436 | c=1.00: -360 / +295 / +2030 | 596 | +0.066 | +1.456 | +0.30 / +0.24 / +0.12 | ok |
| L3522e532 | RK7 | L3M | +2242 / +3923 | -6920 | +632 / +1105 | -7811 | c=0.97: +2201 / -6804 / +616 | 91 | +0.061 | +0.430 | +0.09 / +0.01 / +0.10 | AMBER |
| L3522e532 | RK7 | L6M | +1809 / +3166 | -7255 | +34 / +60 | -7811 | c=0.97: +1770 / -6922 / +36 | 197 | -0.007 | -0.051 | +0.04 / +0.04 / +0.06 | AMBER |
| L3522e532 | ADD | L3M | -65 / -114 | -3256 | +642 / +1123 | +186 | c=0.97: -81 / -3170 / +624 | 90 | +0.068 | +0.472 | +0.09 / +0.01 / +0.09 | ok |
| L3522e532 | ADD | L6M | +313 / +547 | -6665 | -137 / -240 | +186 | c=0.97: +287 / -6333 / -137 | 195 | +0.000 | +0.000 | +0.03 / +0.04 / +0.05 | ok |
| L3701b464 | RK7 | L3M | -504 / -881 | -3120 | +2902 / +5078 | +2281 | c=0.50: +290 / -3103 / +1882 | 62 | +0.178 | +0.849 | +0.25 / -0.07 / +0.11 | ok |
| L3701b464 | RK7 | L6M | -58 / -102 | -3120 | +2291 / +4010 | +1857 | c=0.50: +318 / -3103 / +1302 | 136 | +0.164 | +0.825 | +0.06 / -0.03 / +0.02 | ok |
| L3701b464 | ADD | L3M | -1573 / -2752 | +95 | +2075 / +3632 | +6571 | c=0.50: -916 / +48 / +1143 | 62 | +0.163 | +0.777 | +0.23 / -0.07 / +0.10 | ok |
| L3701b464 | ADD | L6M | -795 / -1391 | -796 | +1691 / +2959 | +5375 | c=0.50: -500 / +48 / +755 | 135 | +0.156 | +0.780 | +0.05 / -0.03 / +0.01 | ok |
| L3c6da67f | RK7 | L3M | +811 / +1418 | -2650 | +1481 / +2593 | -3220 | c=1.00: +811 / -2650 / +1481 | 78 | +0.160 | +0.962 | -0.03 / +0.04 / -0.17 | ok |
| L3c6da67f | RK7 | L6M | +494 / +865 | -2650 | +1431 / +2505 | -3220 | c=1.00: +494 / -2650 / +1431 | 173 | +0.146 | +0.935 | +0.12 / +0.06 / -0.09 | ok |
| L3c6da67f | ADD | L3M | -810 / -1417 | +481 | +1100 / +1925 | +1305 | c=1.00: -810 / +481 / +1100 | 77 | +0.154 | +0.913 | -0.00 / +0.04 / -0.18 | ok |
| L3c6da67f | ADD | L6M | -565 / -989 | +481 | +1119 / +1959 | +1305 | c=1.00: -565 / +481 / +1119 | 172 | +0.143 | +0.912 | +0.14 / +0.06 / -0.10 | ok |
| L582ae3cb | RK7 | L3M | +250 / +437 | -4905 | +2403 / +4204 | +952 | c=0.89: +331 / -4703 / +2253 | 67 | +0.193 | +0.994 | +0.04 / +0.02 / +0.00 | ok |
| L582ae3cb | RK7 | L6M | +240 / +419 | -4905 | +2329 / +4075 | +952 | c=0.89: +287 / -4703 / +2144 | 140 | +0.238 | +1.232 | +0.03 / -0.00 / +0.15 | ok |
| L582ae3cb | ADD | L3M | -1115 / -1951 | -1341 | +554 / +970 | +5563 | c=0.89: -1047 / -1115 / +430 | 66 | +0.163 | +0.828 | +0.02 / +0.03 / -0.02 | ok |
| L582ae3cb | ADD | L6M | -670 / -1173 | -1341 | +1242 / +2173 | +5375 | c=0.89: -637 / -1115 / +1072 | 137 | +0.222 | +1.128 | +0.02 / -0.00 / +0.14 | ok |
| L6036e259 | ADD | L3M | +9012 / +15770 | -8505 | -541 / -947 | -26522 | c=0.50: +4111 / -4873 / -209 | 111 | -0.032 | -0.276 | +0.02 / +0.24 / +0.38 | RED |
| L6036e259 | ADD | L6M | +5642 / +9874 | -8505 | -204 / -357 | -26522 | c=0.50: +2439 / -4873 / -59 | 279 | -0.012 | -0.121 | +0.03 / +0.14 / +0.08 | RED |
| L61c82960 | RK7 | L3M | +1430 / +2502 | -2808 | +1195 / +2091 | -1849 | c=0.50: +1194 / -2186 / +792 | 83 | +0.053 | +0.336 | +0.02 / +0.23 / +0.19 | ok |
| L61c82960 | RK7 | L6M | +859 / +1504 | -2808 | +2164 / +3786 | -1849 | c=0.50: +734 / -2186 / +1271 | 195 | +0.103 | +0.744 | +0.05 / +0.17 / +0.05 | ok |
| L61c82960 | ADD | L3M | +214 / +375 | -1244 | +2020 / +3535 | +736 | c=0.50: +108 / -622 / +1484 | 81 | +0.072 | +0.447 | -0.01 / +0.20 / +0.15 | ok |
| L61c82960 | ADD | L6M | +32 / +57 | -1244 | +2476 / +4332 | +736 | c=0.50: -34 / -622 / +1517 | 192 | +0.112 | +0.799 | +0.04 / +0.15 / +0.03 | ok |
| L684e3038 | ADD | L3M | +1426 / +2495 | -5941 | -1152 / -2017 | -3914 | c=1.00: +1426 / -5941 / -1152 | 135 | -0.029 | -0.300 | +0.18 / +0.08 / +0.17 | ok |
| L684e3038 | ADD | L6M | +859 / +1503 | -5941 | -261 / -457 | -3914 | c=1.00: +859 / -5941 / -261 | 302 | +0.015 | +0.164 | +0.11 / +0.12 / +0.15 | ok |
| L74ce8d84 | RK7 | L3M | +1894 / +3314 | -3780 | +589 / +1030 | -6714 | c=0.50: +1046 / -2320 / +360 | 74 | +0.034 | +0.191 | +0.03 / +0.06 / -0.01 | AMBER |
| L74ce8d84 | RK7 | L6M | +1487 / +2602 | -3945 | +1090 / +1907 | -6714 | c=0.50: +846 / -2320 / +651 | 161 | +0.061 | +0.366 | -0.02 / +0.08 / +0.10 | AMBER |
| L74ce8d84 | ADD | L3M | +594 / +1040 | -2919 | +226 / +396 | -2178 | c=0.50: +118 / -1460 / +90 | 73 | +0.020 | +0.114 | -0.01 / +0.07 / -0.03 | ok |
| L74ce8d84 | ADD | L6M | +562 / +984 | -3356 | +800 / +1400 | -2178 | c=0.50: +148 / -1460 / +389 | 159 | +0.058 | +0.343 | -0.04 / +0.09 / +0.09 | ok |
| L9bbb4c00 | RK7 | L3M | +892 / +1561 | +969 | +1557 / +2726 | -3857 | c=0.50: +1115 / -403 / +676 | 70 | +0.136 | +0.734 | +0.16 / +0.22 / +0.25 | ok |
| L9bbb4c00 | RK7 | L6M | +634 / +1109 | +969 | +856 / +1497 | -3857 | c=0.50: +744 / -403 / +409 | 176 | +0.057 | +0.373 | +0.12 / +0.15 / +0.24 | ok |
| L9bbb4c00 | ADD | L3M | -1351 / -2364 | +4160 | +1962 / +3433 | +4820 | c=0.50: -774 / +2787 / +989 | 69 | +0.153 | +0.811 | +0.19 / +0.23 / +0.27 | ok |
| L9bbb4c00 | ADD | L6M | -796 / -1393 | +4160 | +845 / +1478 | +4820 | c=0.50: -501 / +2787 / +342 | 174 | +0.065 | +0.419 | +0.14 / +0.15 / +0.25 | ok |
| La96d4160 | RK7 | L3M | +2761 / +4832 | -5423 | -889 / -1556 | -8102 | c=1.14: +2953 / -5657 / -1084 | 95 | -0.178 | -1.299 | -0.03 / -0.24 / -0.03 | AMBER |
| La96d4160 | RK7 | L6M | +1748 / +3059 | -5423 | -200 / -349 | -8102 | c=1.14: +1872 / -5657 / -287 | 209 | -0.075 | -0.583 | -0.01 / -0.17 / -0.07 | AMBER |
| La96d4160 | ADD | L3M | +1430 / +2503 | -941 | -891 / -1559 | -4444 | c=1.14: +1607 / -1174 / -1086 | 95 | -0.178 | -1.299 | -0.03 / -0.24 / -0.03 | ok |
| La96d4160 | ADD | L6M | +829 / +1452 | -941 | -436 / -763 | -4444 | c=1.14: +941 / -1174 / -529 | 208 | -0.081 | -0.623 | -0.00 / -0.17 / -0.07 | ok |
| Lbbdd1236 | RK7 | L3M | +2088 / +3655 | -5696 | +1786 / +3125 | -4913 | c=0.67: +1907 / -5132 / +1280 | 54 | +0.203 | +0.843 | +0.04 / +0.12 / +0.24 | AMBER |
| Lbbdd1236 | RK7 | L6M | +1220 / +2134 | -5696 | +2271 / +3974 | -4913 | c=0.67: +1147 / -5132 / +1597 | 106 | +0.286 | +1.122 | -0.02 / +0.04 / +0.13 | AMBER |
| Lbbdd1236 | ADD | L3M | -110 / -193 | -1865 | +1486 / +2600 | +2395 | c=0.67: -67 / -1243 / +984 | 55 | +0.198 | +0.836 | +0.04 / +0.12 / +0.24 | ok |
| Lbbdd1236 | ADD | L6M | -218 / -381 | -1865 | +2072 / +3626 | +2395 | c=0.67: -153 / -1243 / +1401 | 107 | +0.282 | +1.118 | -0.02 / +0.04 / +0.13 | ok |
| Lc9273dc9 | RK7 | L3M | +1782 / +3119 | -7971 | +2358 / +4127 | -5082 | c=0.76: +1641 / -7026 / +1905 | 74 | +0.212 | +1.209 | +0.34 / +0.39 / +0.44 | AMBER |
| Lc9273dc9 | RK7 | L6M | +1084 / +1898 | -7971 | +1578 / +2761 | -5082 | c=0.76: +1010 / -7026 / +1281 | 149 | +0.143 | +0.791 | +0.22 / +0.24 / +0.22 | AMBER |
| Lc9273dc9 | ADD | L3M | +918 / +1606 | -6587 | +2506 / +4386 | -2405 | c=0.76: +708 / -5642 / +2054 | 73 | +0.215 | +1.207 | +0.34 / +0.39 / +0.44 | ok |
| Lc9273dc9 | ADD | L6M | +471 / +824 | -6587 | +1569 / +2747 | -2405 | c=0.76: +349 / -5642 / +1273 | 148 | +0.144 | +0.790 | +0.22 / +0.24 / +0.22 | ok |
| Lcf12aa09 | RK7 | L3M | -283 / -496 | +3268 | -335 / -586 | +2124 | c=1.00: -283 / +3268 / -335 | 132 | -0.018 | -0.180 | +0.45 / +0.20 / +0.39 | ok |
| Lcf12aa09 | RK7 | L6M | -93 / -163 | +3240 | +284 / +497 | +2124 | c=1.00: -93 / +3240 / +284 | 254 | +0.012 | +0.113 | +0.31 / +0.11 / +0.26 | ok |
| Lcf12aa09 | ADD | L3M | -910 / -1593 | +5096 | -195 / -341 | +3581 | c=1.00: -910 / +5096 / -195 | 131 | -0.017 | -0.176 | +0.44 / +0.20 / +0.39 | ok |
| Lcf12aa09 | ADD | L6M | -587 / -1028 | +3829 | +235 / +412 | +3581 | c=1.00: -587 / +3829 / +235 | 253 | +0.012 | +0.115 | +0.31 / +0.10 / +0.26 | ok |
| Ld144438d | RK7 | L3M | +1835 / +3211 | -253 | +804 / +1407 | -6109 | c=1.00: +1835 / -253 / +804 | 143 | +0.046 | +0.504 | +0.26 / +0.14 / +0.17 | AMBER |
| Ld144438d | RK7 | L6M | +1188 / +2079 | -253 | +655 / +1147 | -6109 | c=1.00: +1188 / -253 / +655 | 300 | +0.034 | +0.379 | +0.23 / +0.14 / +0.14 | AMBER |
| Ld144438d | ADD | L3M | +41 / +71 | +1151 | +1341 / +2347 | +591 | c=1.00: +41 / +1151 / +1341 | 140 | +0.047 | +0.502 | +0.26 / +0.14 / +0.17 | ok |
| Ld144438d | ADD | L6M | -8 / -14 | +1151 | +798 / +1396 | +591 | c=1.00: -8 / +1151 / +798 | 297 | +0.034 | +0.378 | +0.23 / +0.15 / +0.14 | ok |
| Ld2802d77 | ADD | L3M | +3662 / +6408 | -1370 | +478 / +836 | -13146 | c=0.50: +1351 / -685 / +123 | 77 | +0.050 | +0.296 | -0.09 / +0.23 / +0.17 | RED |
| Ld2802d77 | ADD | L6M | +2313 / +4047 | -1370 | -829 / -1450 | -13146 | c=0.50: +813 / -685 / -441 | 212 | -0.041 | -0.323 | -0.05 / +0.16 / +0.21 | RED |
| Ld8def90a | ADD | L3M | +650 / +1138 | -3280 | +2343 / +4100 | -2454 | c=0.50: +238 / -2858 / +1093 | 84 | +0.161 | +1.042 | +0.03 / +0.26 / +0.20 | ok |
| Ld8def90a | ADD | L6M | +293 / +512 | -3280 | +965 / +1688 | -2454 | c=0.50: +88 / -2858 / +460 | 180 | +0.063 | +0.420 | -0.03 / +0.20 / +0.15 | ok |
| Le31f3d38 | RK7 | L3M | +5512 / +9646 | -8519 | +1006 / +1761 | -17768 | c=0.50: +2491 / -5711 / +870 | 95 | +0.016 | +0.114 | +0.01 / +0.22 / +0.34 | RED |
| Le31f3d38 | ADD | L3M | +5290 / +9258 | -8050 | +642 / +1123 | -16308 | c=0.50: +2242 / -5243 / +449 | 97 | +0.021 | +0.160 | +0.02 / +0.22 / +0.32 | RED |
| Le31f3d38 | ADD | L6M | +3166 / +5541 | -8050 | +782 / +1369 | -16308 | c=0.50: +1239 / -5243 / +467 | 212 | +0.033 | +0.263 | -0.01 / +0.17 / +0.15 | RED |
| Le7884733 | RK7 | L3M | +1505 / +2635 | -6225 | +1791 / +3134 | -4696 | c=0.50: +1191 / -4656 / +1349 | 42 | +0.114 | +0.369 | -0.03 / -0.06 / +0.11 | AMBER |
| Le7884733 | RK7 | L6M | +1198 / +2096 | -6225 | +1528 / +2674 | -4696 | c=0.50: +906 / -4656 / +1022 | 92 | +0.124 | +0.421 | -0.01 / +0.02 / +0.12 | AMBER |
| Le7884733 | ADD | L3M | -639 / -1119 | -3140 | +1012 / +1772 | +2561 | c=0.50: -422 / -1570 / +610 | 41 | +0.106 | +0.335 | -0.04 / -0.06 / +0.10 | ok |
| Le7884733 | ADD | L6M | -177 / -310 | -3711 | +1013 / +1772 | +2561 | c=0.50: -173 / -1570 / +556 | 90 | +0.114 | +0.380 | -0.01 / +0.02 / +0.12 | ok |
| Le7968c68 | RK7 | L3M | +1782 / +3118 | -3699 | -688 / -1203 | -5977 | c=1.00: +1782 / -3699 / -688 | 207 | -0.041 | -0.658 | +0.07 / -0.15 / +0.01 | AMBER |
| Le7968c68 | RK7 | L6M | +1264 / +2212 | -3699 | +711 / +1244 | -5977 | c=1.00: +1264 / -3699 / +711 | 446 | +0.020 | +0.332 | +0.21 / +0.02 / +0.07 | AMBER |
| Le7968c68 | ADD | L3M | +1185 / +2074 | -4395 | -502 / -878 | -4490 | c=1.00: +1185 / -4395 / -502 | 205 | -0.032 | -0.506 | +0.09 / -0.18 / +0.02 | ok |
| Le7968c68 | ADD | L6M | +827 / +1448 | -4395 | +526 / +920 | -4490 | c=1.00: +827 / -4395 / +526 | 444 | +0.025 | +0.405 | +0.22 / +0.01 / +0.08 | ok |
| Lf0880065 | ADD | L3M | +1989 / +3480 | -5646 | +1939 / +3393 | -6939 | c=0.50: +555 / -2476 / +1695 | 87 | +0.030 | +0.203 | -0.05 / +0.31 / +0.12 | AMBER |
| Lf0880065 | ADD | L6M | +1398 / +2446 | -5646 | +2059 / +3602 | -6939 | c=0.50: +429 / -2476 / +1348 | 209 | +0.077 | +0.592 | -0.02 / +0.13 / +0.06 | AMBER |
| Lf6d81bce | RK7 | L3M | +1296 / +2267 | -1865 | +617 / +1079 | -2328 | c=1.00: +1296 / -1865 / +617 | 80 | -0.033 | -0.206 | +0.18 / -0.06 / +0.35 | ok |
| Lf6d81bce | RK7 | L6M | +887 / +1553 | -1865 | +557 / +974 | -2328 | c=1.00: +887 / -1865 / +557 | 163 | -0.006 | -0.034 | +0.18 / -0.03 / +0.24 | ok |
| Lf6d81bce | ADD | L3M | -241 / -422 | +1639 | -134 / -235 | +2654 | c=1.00: -241 / +1639 / -134 | 81 | -0.036 | -0.223 | +0.17 / -0.05 / +0.35 | ok |
| Lf6d81bce | ADD | L6M | -129 / -226 | +1639 | +13 / +23 | +2654 | c=1.00: -129 / +1639 / +13 | 164 | -0.007 | -0.043 | +0.18 / -0.03 / +0.24 | ok |
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

