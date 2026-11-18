# NEW_BOOK_ENGINE - replacement of the NY AM / NY PM books on the exact engine (W-NYENG), refreshed 2026-11-18 16:14Z

Stack = JL3 (all live layers ON). Dollars: engine BASE lots at $4.84 RT/contract proxy with an x1.75 live-lot column in brackets. Deltas = WITH minus the live JL3 stack on the same months; drawdown first: d ulcer / d worst week / d max DD / d mean $/wk (x1.75 in brackets). Negative ulcer / DD change = better. PROVISIONAL cells (selection-biased picks); no label without controls (none yet). Prereg PREREG_NYE.md + AMEND1 (DECISIONS.md). Identity (injection = JL3 with an inert event): 202610: PASS (691 trades, net 37159.82); 202504: PASS (637 trades, net 41239.76). Set-months done: 914.

## What acts on a new book in these runs (plain words; full list NEW_BOOK_LAYER_FACTS.md)
- ON the new book: the signal-state screen gate "conj" (written for all books; it skipped 334 of ~800 signals of NA1 in 202610), one position at a time, the book day caps (loss 4,800 $ / profit 12,000 $ default; a 120-pt stop = 2,400 $ at 1 base lot, 4,800 $ at 2 live lots = one stop trips it), the book give-back lock, measured slippage, the stack rule.
- NOT on the new book: no-trade zones, policy take / near-target latch / locks / shave (named live books only), trade-health and context cuts, ATR-skip, breakout rule, governor, session lot tables. So the engine row = the cell under those rules only; its own fitted layers are variant (iii), not built yet. BARE (screen gate and caps off) and ACCT (gate off, account day caps on) variants for NA1 NA2 NA5 NP1 NP5 are queued.

## ID glossary (reconciled 16:10Z; engine ids never change)
- WA<n> / WP<n> = W-SHORT rank n on the 14:23Z page (frozen): **WP1 = NY PM dlt_100 levels_vwap.reject {tol 0, conf close}, plain 60/60** (NOT tm1800); **WP10 = NY PM vol_350 tape_libvol.cmf {len 10}, asym20u/10u (median stop/target 120/60)**; WP11 = tm1800 xmarket_ym.follow plain 60/60 on that page.
- XA<n> / XP<n> = W-SHORT rank n on the 15:19Z equal-risk page (frozen): **XP2 = NY PM tm1800 xmarket_ym.follow {w 5, thr 1.0}**, XP1 = dib_400 tape_libvol.cmf {len 10}, XP3 = tm900 xmarket_es.follow. So XP2 (tm1800 YM follow) is a different cell from WP1 (dlt_100 VWAP reject); the headline rows NYE_WP1_* / NYW_WP1_* are dlt_100 VWAP reject.
- NA<n> / NP<n> = my first provisional six per session (level_nr_qual picks). Set names: TL3_NYE_<id>_ADD|RK7|RP7|RM7|ALL|BARE|ACCT|CT<k><p|m>, TL3_NYW_<id>_ADD (W / X cells), TL3_NYE_C2|C3|D1|D2|P2_<session>_<ids> (P2 = K7 kept + both new books).

## Date-shift controls (same events moved +-7..35 days, same weekday; ADD at 1 base lot; L6M)
| cell | real d mean $/wk | real d ulcer | controls n | controls d mean median / best | controls d ulcer median / best | real beats controls on mean (share) | real better ulcer than controls (share) |
|---|---|---|---|---|---|---|---|
| NA4 | +1158 | -8 | 10 | +3 / +703 | +1487 / -504 | 1.00 | 0.90 |
| WA2 | +1619 | +904 | 10 | -347 / +1765 | +971 / -720 | 0.90 | 0.50 |

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
| best single swap | NYE_NA4_RP7 | risk-matched c=0.50 | -218 / -2385 / +1927 / +221 (+386) | -282 / -2385 / +1927 / -250 (-437) | n/a | n/a | n/a | 0 |
| best whole-session replacement | NYE_C3_NYAM_NA4_WA2_NA6 | risk-matched c=1.67 | +4503 / -14235 / -15729 / +1726 (+3020) | +6687 / -14235 / -15729 / -422 (-738) | n/a | n/a | n/a | 0 |
| best mixed (keep best live book + new) | NYE_D2_NYAM_NA4_NA6 | risk-matched c=2.25 | +5773 / -18315 / -18927 / +1509 (+2641) | +8909 / -18315 / -18927 / +70 (+123) | n/a | n/a | n/a | 0 |
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

### All sets (detail)
| cell | variant | window | d ulcer (x1 / x1.75) | d worst wk | d mean $/wk (x1 / x1.75) | d max DD | RISK-MATCHED c: d ulcer / d worst / d mean | new-book trades | R/trade | R/wk | corr daily w/ K7 / P7 / M7 | flag vs JL3 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NA1 | ACCT | L3M | +2562 / +4484 | -10610 | -3062 / -5358 | -9861 | c=0.50: +629 / -4141 / -1308 | 137 | -0.139 | -1.462 | -0.17 / +0.10 / -0.03 | RED |
| NA1 | ACCT | L6M | +1333 / +2334 | -10610 | +633 / +1108 | -9861 | c=0.50: +55 / -4141 / +538 | 330 | +0.006 | +0.079 | -0.07 / +0.06 / -0.02 | RED |
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
| NA2 | ACCT | L3M | +3507 / +6138 | -14180 | -1650 / -2887 | -8675 | c=0.71: +2456 / -9463 / -1085 | 129 | -0.119 | -1.176 | -0.20 / +0.14 / -0.16 | RED |
| NA2 | ACCT | L6M | +1832 / +3206 | -14180 | +806 / +1411 | -8675 | c=0.71: +1123 / -9463 / +673 | 320 | +0.023 | +0.278 | -0.03 / +0.14 / +0.02 | AMBER |
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
| NA4:NA6 | C2 | L3M | +5014 / +8774 | -9572 | -1559 / -2728 | -12302 | c=2.50: +10780 / -20063 / -288 | 0 | +nan | +0.353 | -0.30 / +0.07 / +0.02 | RED |
| NA4:NA6 | C2 | L6M | +3087 / +5402 | -9572 | -82 / -143 | -12302 | c=2.50: +7123 / -20063 / +1363 | 0 | +nan | +0.401 | -0.07 / +0.11 / +0.15 | RED |
| NA4:NA6 | D2 | L3M | +4271 / +7474 | -9572 | -989 / -1730 | -10080 | c=2.25: +8909 / -18315 / +70 | 0 | +nan | +0.353 | -0.30 / +0.07 / +0.02 | RED |
| NA4:NA6 | D2 | L6M | +2553 / +4468 | -9572 | +305 / +534 | -10080 | c=2.25: +5773 / -18315 / +1509 | 0 | +nan | +0.401 | -0.07 / +0.11 / +0.15 | RED |
| NA4:WA2:NA6 | C3 | L3M | +4452 / +7791 | -9572 | -1060 / -1854 | -11527 | c=1.67: +6687 / -14235 / -422 | 0 | +nan | +0.399 | -0.21 / +0.09 / +0.01 | RED |
| NA4:WA2:NA6 | C3 | L6M | +2833 / +4958 | -9572 | +706 / +1236 | -11527 | c=1.67: +4503 / -14235 / +1726 | 0 | +nan | +0.637 | -0.03 / +0.13 / +0.06 | RED |
| NA5 | ACCT | L3M | +473 / +828 | -755 | +2030 / +3552 | -2298 | c=0.50: -909 / +174 / +1510 | 164 | +0.034 | +0.433 | -0.04 / +0.07 / +0.03 | ok |
| NA5 | ACCT | L6M | +131 / +229 | -755 | +2062 / +3609 | -2298 | c=0.50: -797 / +174 / +1369 | 416 | +0.037 | +0.578 | +0.01 / +0.05 / +0.02 | ok |
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
| WA5 | ADD | L3M | +317 / +554 | -3090 | -259 / -452 | -2405 | c=0.50: +200 / -1545 / -236 | 42 | -0.006 | -0.019 | +0.01 / -0.12 / +0.04 | ok |
| WA5 | ADD | L6M | +217 / +379 | -3090 | +314 / +549 | -2405 | c=0.50: +114 / -1545 / +165 | 83 | +0.040 | +0.124 | +0.04 / -0.14 / +0.06 | ok |
| WA6 | ADD | L3M | +322 / +563 | +3854 | +253 / +443 | +2681 | c=0.50: +142 / +2003 / +96 | 99 | +0.017 | +0.131 | +0.09 / +0.29 / +0.32 | ok |
| WA6 | ADD | L6M | +151 / +264 | +2029 | +537 / +940 | +2681 | c=0.50: +43 / +2003 / +281 | 227 | +0.025 | +0.213 | +0.13 / +0.18 / +0.26 | ok |
| WA9 | ADD | L3M | +5523 / +9665 | -10055 | +1629 / +2851 | -19567 | c=0.71: +4001 / -8220 / +1031 | 120 | +0.135 | +1.245 | +0.05 / +0.36 / +0.42 | RED |
| WA9 | ADD | L6M | +3391 / +5935 | -10055 | +915 / +1601 | -19567 | c=0.71: +2402 / -8220 / +549 | 277 | +0.074 | +0.762 | -0.01 / +0.23 / +0.23 | RED |
| XA1 | ADD | L3M | +103 / +180 | +2791 | +296 / +518 | -1494 | c=1.00: +103 / +2791 / +296 | 158 | +0.015 | +0.183 | +0.26 / -0.09 / -0.04 | ok |
| XA1 | ADD | L6M | +70 / +122 | +2791 | +734 / +1284 | -1494 | c=1.00: +70 / +2791 / +734 | 333 | +0.032 | +0.398 | +0.29 / -0.05 / +0.00 | ok |
| XA2 | ADD | L3M | -1000 / -1751 | +3991 | +449 / +785 | +4396 | c=1.00: -1000 / +3991 / +449 | 261 | +0.009 | +0.180 | +0.48 / +0.28 / +0.35 | ok |
| XA2 | ADD | L6M | -751 / -1315 | +3991 | +833 / +1458 | +4396 | c=1.00: -751 / +3991 / +833 | 651 | +0.025 | +0.604 | +0.27 / +0.17 / +0.16 | ok |
| XA3 | ADD | L3M | -456 / -798 | +1134 | +1935 / +3386 | +2888 | c=1.00: -456 / +1134 / +1935 | 165 | +0.127 | +1.616 | +0.20 / +0.13 / +0.39 | ok |
| XA3 | ADD | L6M | -262 / -458 | +1134 | +1965 / +3439 | +2888 | c=1.00: -262 / +1134 / +1965 | 383 | +0.125 | +1.767 | +0.15 / +0.08 / +0.16 | ok |
| XA4 | ADD | L3M | +97 / +169 | -2550 | -853 / -1492 | +1064 | c=1.00: +97 / -2550 / -853 | 189 | -0.018 | -0.263 | +0.15 / +0.06 / +0.15 | ok |
| XA4 | ADD | L6M | +115 / +200 | -2550 | -244 / -427 | +1064 | c=1.00: +115 / -2550 / -244 | 431 | +0.014 | +0.221 | +0.13 / +0.12 / +0.02 | ok |

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
| best whole-session replacement | NYE_C2_NYPM_WP10_NP4 | risk-matched c=0.52 | -110 / -670 / -858 / +234 (+409) | -220 / -670 / -858 / +1276 (+2234) | n/a | n/a | n/a | 0 |
| best mixed (keep best live book + new) | NYW_WP10_ADD | risk-matched c=0.50 | -154 / +201 / -35 / +736 (+1287) | -246 / +201 / -35 / +739 (+1292) | n/a | n/a | +1256 / +490 / -3429 / +39 (+68) | 0 |
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

### All sets (detail)
| cell | variant | window | d ulcer (x1 / x1.75) | d worst wk | d mean $/wk (x1 / x1.75) | d max DD | RISK-MATCHED c: d ulcer / d worst / d mean | new-book trades | R/trade | R/wk | corr daily w/ K7 / P7 / M7 | flag vs JL3 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NP1 | ACCT | L3M | +124 / +217 | +5161 | +1425 / +2494 | -3014 | c=0.56: -104 / +2894 / +770 | 123 | +0.074 | +0.696 | +0.06 / n/a / n/a | ok |
| NP1 | ACCT | L6M | +166 / +290 | +1625 | -375 / -657 | -3014 | c=0.56: -139 / +2808 / -148 | 294 | -0.022 | -0.241 | +0.10 / n/a / n/a | ok |
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
| NP5 | ACCT | L3M | +1243 / +2175 | -4089 | +26 / +46 | -3142 | c=0.50: +263 / -2044 / +13 | 85 | +0.002 | +0.011 | +0.09 / n/a / n/a | ok |
| NP5 | ACCT | L6M | +970 / +1697 | -4089 | +871 / +1525 | -3142 | c=0.50: +184 / -2044 / +375 | 213 | +0.052 | +0.413 | +0.16 / n/a / n/a | ok |
| NP5 | ADD | L3M | +330 / +577 | -2034 | +738 / +1291 | -359 | c=0.50: +57 / -1017 / +369 | 54 | +0.074 | +0.307 | +0.12 / n/a / n/a | ok |
| NP5 | ADD | L6M | +242 / +423 | -2034 | +1382 / +2419 | -359 | c=0.50: +56 / -1017 / +691 | 132 | +0.118 | +0.576 | +0.20 / n/a / n/a | ok |
| NP5 | ALL | L3M | +636 / +1113 | -4469 | +491 / +859 | -2451 | c=1.00: +636 / -4469 / +491 | 54 | +0.074 | +0.307 | +0.12 / n/a / n/a | ok |
| NP5 | ALL | L6M | +495 / +866 | -4469 | +570 / +997 | -2451 | c=1.00: +495 / -4469 / +570 | 132 | +0.118 | +0.576 | +0.20 / n/a / n/a | ok |
| NP5 | BARE | L3M | +1243 / +2175 | -4089 | +26 / +46 | -3142 | c=0.50: +263 / -2044 / +13 | 85 | +0.002 | +0.011 | +0.09 / n/a / n/a | ok |
| NP5 | BARE | L6M | +884 / +1547 | -4089 | +931 / +1629 | -3142 | c=0.50: +142 / -2044 / +405 | 214 | +0.055 | +0.438 | +0.16 / n/a / n/a | ok |
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
| WP1 | ALL | L3M | +16 / +29 | -719 | +9 / +16 | +621 | c=2.00: -70 / +997 / +265 | 83 | +0.033 | +0.213 | -0.09 / n/a / n/a | ok |
| WP1 | ALL | L6M | +20 / +34 | -719 | +53 / +93 | +621 | c=2.00: -10 / +997 / +919 | 198 | +0.098 | +0.721 | +0.08 / n/a / n/a | ok |
| WP1 | RK7 | L3M | +16 / +29 | -719 | +9 / +16 | +621 | c=1.00: +16 / -719 / +9 | 83 | +0.033 | +0.213 | -0.09 / n/a / n/a | ok |
| WP1 | RK7 | L6M | +20 / +34 | -719 | +53 / +93 | +621 | c=1.00: +20 / -719 / +53 | 198 | +0.098 | +0.721 | +0.08 / n/a / n/a | ok |
| WP1 | RK7 | Y2023 | +498 / +872 | +1628 | +315 / +551 | -5144 | c=1.00: +498 / +1628 / +315 | 257 | +0.063 | +0.412 | +0.03 / n/a / n/a | ok |
| WP1 | RK7 | Y2024 | -1480 / -2590 | +0 | +85 / +148 | +2969 | c=1.00: -1480 / +0 / +85 | 379 | +0.052 | +0.372 | +0.09 / n/a / n/a | ok |
| WP1 | RK7 | Y2025 | -5228 / -9150 | -260 | -82 / -144 | +8837 | c=1.00: -5228 / -260 / -82 | 393 | +0.067 | +0.500 | -0.04 / n/a / n/a | ok |
| WP1 | ADD | L3M | -176 / -309 | +1716 | -204 / -356 | +2390 | c=1.00: -176 / +1716 / -204 | 78 | -0.003 | -0.017 | -0.10 / n/a / n/a | ok |
| WP1 | ADD | L6M | -132 / -231 | +1716 | +655 / +1146 | +2390 | c=1.00: -132 / +1716 / +655 | 196 | +0.075 | +0.544 | +0.08 / n/a / n/a | ok |
| WP10 | ALL | L3M | +181 / +316 | -2034 | +1234 / +2160 | -3029 | c=1.00: +181 / -2034 / +1234 | 111 | +0.072 | +0.617 | -0.12 / n/a / n/a | ok |
| WP10 | ALL | L6M | +188 / +329 | -2034 | +661 / +1156 | -3029 | c=1.00: +188 / -2034 / +661 | 228 | +0.073 | +0.614 | -0.15 / n/a / n/a | ok |
| WP10 | RK7 | L3M | +181 / +316 | -2034 | +1234 / +2160 | -3029 | c=0.50: +162 / -2234 / +494 | 111 | +0.072 | +0.617 | -0.12 / n/a / n/a | ok |
| WP10 | RK7 | L6M | +188 / +329 | -2034 | +661 / +1156 | -3029 | c=0.50: +138 / -2234 / -76 | 228 | +0.073 | +0.614 | -0.15 / n/a / n/a | ok |
| WP10 | ADD | L3M | -372 / -652 | +401 | +1569 / +2746 | -285 | c=0.50: -246 / +201 / +739 | 110 | +0.082 | +0.692 | -0.12 / n/a / n/a | ok |
| WP10 | ADD | L6M | -206 / -360 | +401 | +1516 / +2652 | -285 | c=0.50: -154 / +201 / +736 | 227 | +0.077 | +0.650 | -0.15 / n/a / n/a | ok |
| WP10 | ADD | Y2023 | +3250 / +5688 | +653 | +77 / +135 | -7030 | c=0.50: +1256 / +490 / +39 | 443 | +0.003 | +0.032 | -0.23 / n/a / n/a | AMBER |
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

