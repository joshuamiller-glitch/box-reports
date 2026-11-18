# NEW_BOOK_ENGINE_LONDON - London replacement rows (W-LONENG), refreshed 2026-11-18 17:26Z

**These rows are vs TODAY's stack (JL3) with today's DAY-DONE setting; they answer 'add / swap one book in today's stack', not 'the rebuilt stack'. London is decided after Asia (clock order Asia -> London -> NY AM -> NY PM): London results stay PROVISIONAL.**

**Which rules act on a new book in these runs (plain words; from code/th_nyeng + autopilot/NEW_BOOK_LAYER_FACTS.md; London = same machinery as NY):** the new book (engine tag MF1) gets: its own bracket, the London session window, flat at session end, one position at a time, its own day cap (loss 4,800 / profit 12,000 $; a 120-pt stop = $2,400 at 1 base lot), a generic book give-back lock, measured slippage, the stack rule (an Asia-entered book that stops cuts others) and account-level rules. **The signal-state "conj" screen gate (written for ALL books) also blocks ~40% of its signals**, so the engine row is NOT the bare screen number; variants _BARE (screen gate off, book day caps off) and _ACCT (screen gate off, account day caps on) are built for the cells listed in the bridge section. The live-book layers (no-trade zones, policy take / near-target latch / profit locks / target shave, trade-health and context cuts) are named-book rules and do NOT act on the new book. Fitted-to-this-book layers (variant iii) are not built yet.

## A. What the live London books earn now (JL3 itself, London-session entries only; bar to beat). Engine base lots; x1.75 = live lots (London live lots K7 2, M7 2, P7 4, U7 per policy)
| window | book | trades | $/wk x1 / x1.75 | worst wk x1 | ulcer contribution x1 / x1.75 (+ = adds ulcer) | maxDD contribution x1 |
|---|---|---|---|---|---|---|
| L6M | K7 | 461 | -79 / -139 | -10319 | +1225 / +2144 | -7956 |
| L6M | M7 | 518 | -268 / -470 | -14758 | +1093 / +1913 | -6081 |
| L6M | U7 | 110 | +675 / +1181 | -5392 | -411 / -720 | +1028 |
| L6M | P7 | 400 | +1028 / +1800 | -7129 | -282 / -494 | +3452 |
| L6M | TOTAL London | 1489 | +1355 / +2372 | -27841 | +926 / +1620 | -4132 |
| L3M | K7 | 221 | +107 / +186 | -10319 | +1860 / +3254 | -9414 |
| L3M | M7 | 238 | +792 / +1386 | -14758 | +1658 / +2902 | -6160 |
| L3M | U7 | 45 | +396 / +693 | -5392 | -931 / -1629 | +1028 |
| L3M | P7 | 201 | +1092 / +1910 | -7129 | -666 / -1165 | +3452 |
| L3M | TOTAL London | 705 | +2386 / +4176 | -27841 | +1590 / +2783 | -4132 |
| Y2025 | K7 | 572 | +652 / +1142 | -7037 | +3670 / +6422 | -10549 |
| Y2025 | M7 | 762 | -199 / -348 | -9947 | +3064 / +5362 | -6316 |
| Y2025 | U7 | 197 | +134 / +235 | -8410 | -1741 / -3048 | -260 |
| Y2025 | P7 | 521 | -1093 / -1912 | -9361 | +9119 / +15958 | -11498 |
| Y2025 | TOTAL London | 2052 | -505 / -883 | -28188 | +15783 / +27620 | -38056 |
| Y2024 | K7 | 384 | +165 / +288 | -7993 | +2824 / +4942 | -10406 |
| Y2024 | M7 | 566 | -570 / -997 | -10668 | +6356 / +11123 | -7512 |
| Y2024 | U7 | 185 | -76 / -132 | -7738 | +5837 / +10215 | -10029 |
| Y2024 | P7 | 369 | -283 / -495 | -8243 | +3131 / +5480 | +380 |
| Y2024 | TOTAL London | 1504 | -763 / -1335 | -24224 | +12953 / +22668 | -25794 |
| Y2023 | K7 | 165 | +95 / +167 | -4677 | -761 / -1332 | +8636 |
| Y2023 | M7 | 297 | -62 / -108 | -8319 | -4747 / -8307 | +11690 |
| Y2023 | U7 | 102 | -273 / -478 | -7029 | +2983 / +5220 | -2909 |
| Y2023 | P7 | 178 | +115 / +202 | -7873 | -540 / -945 | +6368 |
| Y2023 | TOTAL London | 742 | -124 / -218 | -18072 | -1388 / -2429 | +11587 |

(reference only, not a deliverable) all live London books OFF: not landed yet

## HEADLINE (drawdown first; differences vs JL3 = the live stack as is; best set per row chosen by L6M stack-ulcer change, then shown on every window; 0 controls so far -> no label)
| row | set | window | d stack ulcer x1 / x1.75 | d worst wk x1 | d maxDD x1 | d mean $/wk x1 / x1.75 | controls |
|---|---|---|---|---|---|---|---|
| live as-is (zero line) | TL3_EV_JL3 | all | 0 | 0 | 0 | 0 | - |
| single swap (one live London book replaced) | not landed yet | | | | | | 0 |
| whole-session replacement (all 4 live London books OFF; ALL = one cell, C2/C3 = best 2/3 cells) | not landed yet | | | | | | 0 |
| mixed (keep best live London book, replace the rest with the best 1-2 new books) | not landed yet | | | | | | 0 |

Triage (ADD L6M standalone < 0 AND d mean < 0 = skipped, documented): LA1: queued: RK7,RM7,RU7,RP7,ALL (standalone $21914, d mean 1447); LA2: queued: RK7,RM7,RU7,RP7,ALL (standalone $18397, d mean 641); LA3: skipped: ADD L6M clearly negative (standalone $-22092, d mean $/wk -1294); LA4: queued: RK7,RM7,RU7,RP7,ALL (standalone $38249, d mean 1191); LA5: queued: RK7,RM7,RU7,RP7,ALL (standalone $59586, d mean 1902); LA6: queued: RK7,RM7,RU7,RP7,ALL (standalone $15618, d mean 720); WL1: skipped: ADD L6M clearly negative (standalone $-1581, d mean $/wk -221); WL2: queued: RK7,RM7,RU7,RP7,ALL (standalone $4966, d mean 627); WL4: skipped: ADD L6M clearly negative (standalone $-9074, d mean $/wk -453); WL6: queued: RK7,RM7,RU7,RP7,ALL (standalone $2593, d mean 1001)
Combos: {"key": "LA5,LA1|LA5,LA1,LA6|P7|LA5", "sets": ["TL3_LON_C2_LA5_LA1", "TL3_LON_C3_LA5_LA1_LA6", "TL3_LON_D1_P7_LA5", "TL3_LON_D2_P7_LA5_LA1"]}

## Per-cell ADD / ADDM rows
Stack = JL3 (TL3_EV_JL3, all live layers ON) + the candidate; engine BASE-lot dollars at $4.84 RT/contract proxy plus an x1.75 live-lot column; deltas = WITH candidate minus the reference on the same months; ulcer and worst week FIRST, then mean $/week. ADD = new book at 1 base lot (2 live lots); R* = the live London book (K7/M7/U7/P7) suppressed in London and replaced; ADDM = ADD plus the confirmed setting M7 London lots 4 live -> 0 (ev_panel, = TL3_CT_JL3_N_M7L) and is compared with TL3_CT_JL3_N_M7L (the base alternative: the stack without M7 London) and with JL3.
**EQUAL RISK (1447Z):** risk-matched c = 60/stop pts; shown as reference + c x the new book daily P&L (exact when the book does not change other books through caps/locks); wide (120-clip) rows are judged on the same-bracket null, not marked down. Day cap: MF1 loss cap $4,800/day: one 120-pt stop = $2,400 at 1 base lot (2 stops trip), $4,800 at 2 live lots (ONE stop trips).
**Identity of the M7-London mechanism (TL3_LON_ID = inert event + M7L0 vs TL3_CT_JL3_N_M7L):** 202610: PASS (645 trades, net 47685.32); 202504: PASS (575 trades, net 53447.62). JL3 identity of the injection (TL3_NYE_ID, W-NYENG): 202610 691 / 37,159.82, 202504 637 / 41,239.76.
**Set-months done:** 67 of 309 queued. Controls (date-shift) not run yet, so NO LABEL (BUILD-READY / NEEDS MORE / DROPPED need controls). Every row was picked as best-of-many on the same L6M it is judged on.

| cell | bar | trigger | stop/tgt pts ($ stop per base lot) | variant | reference | window | d ulcer x1 / x1.75 | d worst wk x1 | d mean $/wk x1 / x1.75 | d maxDD x1 | RISK-MATCHED c: d ulcer / d worst / d mean | trades | R/trade | R/wk | flag vs ref |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +1069 / +1871 | -9816 | +1447 / +2533 | -4360 | c=0.50: +360 / -4544 / +1042 | 152 | +0.060 | +0.338 | ok |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +1143 / +2000 | -6712 | +2118 / +3706 | -4360 | c=0.50: +437 / -4305 / +997 | 75 | +0.162 | +0.934 | ok |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +572 / +1000 | -8332 | +641 / +1123 | -8570 | c=0.50: +172 / -4808 / +301 | 202 | +0.038 | +0.284 | AMBER |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +1611 / +2819 | -8332 | -806 / -1411 | -8570 | c=0.50: +915 / -4808 / -722 | 101 | -0.009 | -0.070 | AMBER |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +3361 / +5882 | -14260 | -1294 / -2264 | -9611 | c=0.50: +1935 / -8938 / -884 | 237 | -0.039 | -0.341 | RED |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +5299 / +9273 | -14260 | -3039 / -5318 | -9611 | c=0.50: +3214 / -8938 / -1997 | 115 | -0.098 | -0.868 | RED |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +120 / +211 | -5410 | +1191 / +2083 | -211 | c=0.50: -159 / -2341 / +482 | 215 | +0.074 | +0.590 | ok |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -379 / -664 | +415 | +1704 / +2982 | -211 | c=0.50: -395 / +536 / +562 | 96 | +0.129 | +0.952 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L6M | -151 / -265 | +1434 | +1902 / +3328 | +3529 | c=0.50: -138 / +1081 / +798 | 194 | +0.128 | +0.920 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -295 / -517 | +2020 | +1674 / +2929 | +3529 | c=0.50: -283 / +1397 / +463 | 94 | +0.139 | +1.009 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +471 / +824 | -14141 | +720 / +1260 | +623 | c=0.50: -91 / -6707 / +431 | 175 | +0.037 | +0.241 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -805 / -1409 | -236 | +2495 / +4366 | +623 | c=0.50: -757 / +244 / +1468 | 88 | +0.126 | +0.856 | ok |
| WL1 | rng_28 | levels_vwap_bands.break_native {"n": 1, "k": 0.5} | 90/90 ($1800) | ADD | EV_JL3 | L6M | +2575 / +4506 | -6363 | -221 / -388 | -12694 | c=0.67: +2045 / -5728 / -202 | 244 | -0.004 | -0.033 | RED |
| WL1 | rng_28 | levels_vwap_bands.break_native {"n": 1, "k": 0.5} | 90/90 ($1800) | ADD | EV_JL3 | L3M | +4050 / +7088 | -6363 | -658 / -1151 | -12694 | c=0.67: +3372 / -5728 / -782 | 121 | +0.022 | +0.207 | RED |
| WL2 | rng_80 | levels_round.retest {"M": 6, "tol": 0.0} | 120/120 ($2400) | ADD | EV_JL3 | L6M | -225 / -394 | -4991 | +627 / +1097 | +4073 | c=0.50: -385 / -2132 / +535 | 191 | +0.011 | +0.077 | ok |
| WL2 | rng_80 | levels_round.retest {"M": 6, "tol": 0.0} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -906 / -1586 | +3414 | +624 / +1093 | +4073 | c=0.50: -712 / +1058 / +195 | 96 | +0.048 | +0.358 | ok |
| WL4 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +778 / +1362 | -3386 | -453 / -792 | +303 | c=0.50: +214 / -1329 / -285 | 196 | -0.019 | -0.140 | ok |
| WL4 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +493 / +862 | -481 | -192 / -336 | +303 | c=0.50: -77 / +790 / -269 | 96 | +0.009 | +0.064 | ok |
| WL6 | rng_14 | tape_delta.follow_sm {"L": 200, "z": 2.0, "sm": 3} | 94/94 ($1875) | ADD | EV_JL3 | L6M | -544 / -952 | -4221 | +1001 / +1752 | +455 | c=0.64: -850 / -2439 / +966 | 239 | +0.006 | +0.051 | ok |
| WL6 | rng_14 | tape_delta.follow_sm {"L": 200, "z": 2.0, "sm": 3} | 94/94 ($1875) | ADD | EV_JL3 | L3M | -830 / -1453 | -484 | -164 / -287 | +455 | c=0.64: -979 / +1274 / -73 | 117 | -0.015 | -0.135 | ok |
| WL7 | time_m_3 | tape_delta.cvd_fade {"N": 10, "L": 100, "z": 1.5} | 58/58 ($1160) | ADD | EV_JL3 | L3M | +883 / +1545 | -4659 | +1481 / +2591 | -6598 | c=1.03: +939 / -4776 / +1491 | 106 | +0.031 | +0.255 | AMBER |

Labels: none yet (controls pending).

