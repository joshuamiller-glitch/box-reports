# NEW_BOOK_ENGINE_LONDON - London replacement rows (W-LONENG), refreshed 2026-11-19 03:30Z

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

(reference only, not a deliverable) all live London books OFF: L6M: ulcer +200 / +350, worst wk -3403, maxDD -686, mean $/wk -1250 / -2188; L3M: ulcer +335 / +587, worst wk -3403, maxDD -686, mean $/wk -2346 / -4105

## HEADLINE (drawdown first; differences vs JL3 = the live stack as is; best set per row chosen by L6M stack-ulcer change, then shown on every window; 0 controls so far -> no label)
| row | set | window | d stack ulcer x1 / x1.75 | d worst wk x1 | d maxDD x1 | d mean $/wk x1 / x1.75 | controls |
|---|---|---|---|---|---|---|---|
| live as-is (zero line) | TL3_EV_JL3 | all | 0 | 0 | 0 | 0 | - |
| single swap | LA5_RK7 | L6M | -1244 / -2177 | +2026 | +7579 | +1864 / +3263 | 0 |
| single swap | LA5_RK7 | L3M | -1876 / -3283 | +2026 | +7579 | +1473 / +2577 | 0 |
| single swap | LA5_RK7 | Y2025 | +2077 / +3635 | +2657 | -7890 | -365 / -638 | 0 |
| single swap | LA5_RK7 | Y2024 | +1516 / +2653 | +183 | +4271 | -140 / -246 | 0 |
| single swap | LA5_RK7 | Y2023 | -300 / -526 | -1665 | -6454 | +330 / +578 | 0 |
| whole-session replacement | C2_LA5_LA1 | L6M | -21 / -36 | -1118 | +730 | +429 / +750 | 0 |
| whole-session replacement | C2_LA5_LA1 | L3M | -434 / -760 | -1118 | +730 | -728 / -1274 | 0 |
| mixed | D1_P7_LA5 | L6M | -786 / -1376 | -3022 | +1912 | +1935 / +3387 | 0 |
| mixed | D1_P7_LA5 | L3M | -815 / -1426 | -3022 | +1912 | +897 / +1570 | 0 |

Triage (ADD L6M standalone < 0 AND d mean < 0 = skipped, documented): LA1: queued: RK7,RM7,RU7,RP7,ALL (standalone $21914, d mean 1447); LA2: queued: RK7,RM7,RU7,RP7,ALL (standalone $18397, d mean 641); LA3: skipped: ADD L6M clearly negative (standalone $-22092, d mean $/wk -1294); LA4: queued: RK7,RM7,RU7,RP7,ALL (standalone $38249, d mean 1191); LA5: queued: RK7,RM7,RU7,RP7,ALL (standalone $59586, d mean 1902); LA6: queued: RK7,RM7,RU7,RP7,ALL (standalone $15618, d mean 720); WL1: skipped: ADD L6M clearly negative (standalone $-1581, d mean $/wk -221); WL2: queued: RK7,RM7,RU7,RP7,ALL (standalone $4966, d mean 627); WL4: skipped: ADD L6M clearly negative (standalone $-9074, d mean $/wk -453); WL6: queued: RK7,RM7,RU7,RP7,ALL (standalone $2593, d mean 1001)
Combos: {"key": "LA5,LA1|LA5,LA1,LA6|P7|LA5", "sets": ["TL3_LON_C2_LA5_LA1", "TL3_LON_C3_LA5_LA1_LA6", "TL3_LON_D1_P7_LA5", "TL3_LON_D2_P7_LA5_LA1"]}

## Per-cell ADD / ADDM rows
Stack = JL3 (TL3_EV_JL3, all live layers ON) + the candidate; engine BASE-lot dollars at $4.84 RT/contract proxy plus an x1.75 live-lot column; deltas = WITH candidate minus the reference on the same months; ulcer and worst week FIRST, then mean $/week. ADD = new book at 1 base lot (2 live lots); R* = the live London book (K7/M7/U7/P7) suppressed in London and replaced; ADDM = ADD plus the confirmed setting M7 London lots 4 live -> 0 (ev_panel, = TL3_CT_JL3_N_M7L) and is compared with TL3_CT_JL3_N_M7L (the base alternative: the stack without M7 London) and with JL3.
**EQUAL RISK (1447Z):** risk-matched c = 60/stop pts; shown as reference + c x the new book daily P&L (exact when the book does not change other books through caps/locks); wide (120-clip) rows are judged on the same-bracket null, not marked down. Day cap: MF1 loss cap $4,800/day: one 120-pt stop = $2,400 at 1 base lot (2 stops trip), $4,800 at 2 live lots (ONE stop trips).
**Identity of the M7-London mechanism (TL3_LON_ID = inert event + M7L0 vs TL3_CT_JL3_N_M7L):** 202610: PASS (645 trades, net 47685.32); 202504: PASS (575 trades, net 53447.62). JL3 identity of the injection (TL3_NYE_ID, W-NYENG): 202610 691 / 37,159.82, 202504 637 / 41,239.76.
**Set-months done:** 657 of 3844 queued. Controls (date-shift) not run yet, so NO LABEL (BUILD-READY / NEEDS MORE / DROPPED need controls). Every row was picked as best-of-many on the same L6M it is judged on.

| cell | bar | trigger | stop/tgt pts ($ stop per base lot) | variant | reference | window | d ulcer x1 / x1.75 | d worst wk x1 | d mean $/wk x1 / x1.75 | d maxDD x1 | RISK-MATCHED c: d ulcer / d worst / d mean | trades | R/trade | R/wk | flag vs ref |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +1069 / +1871 | -9816 | +1447 / +2533 | -4360 | c=0.50: +360 / -4544 / +1042 | 152 | +0.060 | +0.338 | ok |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +1143 / +2000 | -6712 | +2118 / +3706 | -4360 | c=0.50: +437 / -4305 / +997 | 75 | +0.162 | +0.934 | ok |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADDM | EV_JL3 | L6M | +3 / +6 | -4864 | +1610 / +2817 | +1683 | c=0.50: -682 / -2457 / +1245 | 160 | +0.051 | +0.304 | ok |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADDM | EV_JL3 | L3M | -132 / -230 | -4864 | +1337 / +2340 | +1683 | c=0.50: -743 / -2457 / +195 | 78 | +0.159 | +0.952 | ok |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +1248 / +2183 | -5806 | +545 / +954 | -4667 | c=0.50: +562 / -3399 / +181 | 160 | +0.051 | +0.304 | AMBER |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L3M | +1468 / +2569 | -5806 | +893 / +1562 | -4667 | c=0.50: +857 / -3399 / -249 | 78 | +0.159 | +0.952 | AMBER |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | RK7 | EV_JL3 | L6M | +429 / +751 | -7967 | +978 / +1711 | +90 | c=0.50: -22 / -5560 / +573 | 154 | +0.059 | +0.337 | ok |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | RK7 | EV_JL3 | L3M | +454 / +794 | -7967 | +1193 / +2088 | +90 | c=0.50: +100 / -5560 / +119 | 76 | +0.153 | +0.895 | ok |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | RM7 | EV_JL3 | L6M | +3 / +6 | -4864 | +1610 / +2817 | +1683 | c=0.50: -682 / -2457 / +1245 | 160 | +0.051 | +0.304 | ok |
| LA1 | rng_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | RM7 | EV_JL3 | L3M | -132 / -230 | -4864 | +1337 / +2340 | +1683 | c=0.50: -743 / -2457 / +195 | 78 | +0.159 | +0.952 | ok |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +572 / +1000 | -8332 | +641 / +1123 | -8570 | c=0.50: +172 / -4808 / +301 | 202 | +0.038 | +0.284 | AMBER |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +1611 / +2819 | -8332 | -806 / -1411 | -8570 | c=0.50: +915 / -4808 / -722 | 101 | -0.009 | -0.070 | AMBER |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADDM | EV_JL3 | L6M | +92 / +162 | -6367 | +903 / +1581 | -4416 | c=0.50: -659 / -1660 / +704 | 208 | +0.022 | +0.166 | ok |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADDM | EV_JL3 | L3M | +750 / +1313 | -6367 | -1560 / -2731 | -4416 | c=0.50: -343 / -1660 / -1339 | 102 | -0.023 | -0.184 | ok |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +1337 / +2340 | -7309 | -161 / -282 | -10766 | c=0.50: +585 / -2602 / -360 | 208 | +0.022 | +0.166 | RED |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L3M | +2350 / +4113 | -7309 | -2005 / -3508 | -10766 | c=0.50: +1257 / -2602 / -1784 | 102 | -0.023 | -0.184 | RED |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | RK7 | EV_JL3 | L6M | +907 / +1586 | -12776 | +344 / +603 | -6713 | c=0.50: +244 / -8069 / +61 | 205 | +0.031 | +0.236 | AMBER |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | RK7 | EV_JL3 | L3M | +2198 / +3847 | -12776 | -1557 / -2725 | -6713 | c=0.50: +1117 / -8069 / -1386 | 103 | -0.018 | -0.142 | AMBER |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | RM7 | EV_JL3 | L6M | +92 / +162 | -6367 | +903 / +1581 | -4416 | c=0.50: -659 / -1660 / +704 | 208 | +0.022 | +0.166 | ok |
| LA2 | vol_4000 | levels_vwap_bands.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | RM7 | EV_JL3 | L3M | +750 / +1313 | -6367 | -1560 / -2731 | -4416 | c=0.50: -343 / -1660 / -1339 | 102 | -0.023 | -0.184 | ok |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +3361 / +5882 | -14260 | -1294 / -2264 | -9611 | c=0.50: +1935 / -8938 / -884 | 237 | -0.039 | -0.341 | RED |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +5299 / +9273 | -14260 | -3039 / -5318 | -9611 | c=0.50: +3214 / -8938 / -1997 | 115 | -0.098 | -0.868 | RED |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | ADDM | EV_JL3 | L6M | +1801 / +3152 | -9295 | -562 / -984 | -5001 | c=0.50: +262 / -5923 / -65 | 243 | -0.046 | -0.415 | AMBER |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | ADDM | EV_JL3 | L3M | +3016 / +5279 | -9295 | -4009 / -7015 | -5001 | c=0.50: +847 / -5923 / -2776 | 116 | -0.115 | -1.027 | AMBER |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +3046 / +5330 | -10237 | -1627 / -2847 | -11352 | c=0.50: +1507 / -6865 / -1129 | 243 | -0.046 | -0.415 | RED |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L3M | +4616 / +8079 | -10237 | -4453 / -7793 | -11352 | c=0.50: +2447 / -6865 / -3220 | 116 | -0.115 | -1.027 | RED |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | RK7 | EV_JL3 | L6M | +3266 / +5715 | -13574 | -996 / -1742 | -8075 | c=0.50: +1559 / -8115 / -538 | 238 | -0.043 | -0.381 | RED |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | RK7 | EV_JL3 | L3M | +5255 / +9196 | -13574 | -3659 / -6403 | -8075 | c=0.50: +2854 / -8115 / -2517 | 116 | -0.107 | -0.952 | RED |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | RM7 | EV_JL3 | L6M | +1801 / +3152 | -9295 | -562 / -984 | -5001 | c=0.50: +262 / -5923 / -65 | 243 | -0.046 | -0.415 | AMBER |
| LA3 | tm120 | levels_vwap_bands.retest_native {"M": 10, "tol": 0.5} | 120/120 ($2400) | RM7 | EV_JL3 | L3M | +3016 / +5279 | -9295 | -4009 / -7015 | -5001 | c=0.50: +847 / -5923 / -2776 | 116 | -0.115 | -1.027 | AMBER |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +120 / +211 | -5410 | +1191 / +2083 | -211 | c=0.50: -159 / -2341 / +482 | 215 | +0.074 | +0.590 | ok |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -379 / -664 | +415 | +1704 / +2982 | -211 | c=0.50: -395 / +536 / +562 | 96 | +0.129 | +0.952 | ok |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADDM | EV_JL3 | L6M | +367 / +642 | -8848 | +1260 / +2204 | +289 | c=0.50: -278 / -3372 / +684 | 221 | +0.059 | +0.480 | ok |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADDM | EV_JL3 | L3M | -88 / -153 | -1120 | +330 / +578 | +289 | c=0.50: -484 / -940 / -630 | 99 | +0.105 | +0.800 | ok |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +1611 / +2820 | -9791 | +195 / +342 | -6062 | c=0.50: +966 / -4314 / -381 | 221 | +0.059 | +0.480 | AMBER |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L3M | +1512 / +2647 | -2062 | -114 / -200 | -6062 | c=0.50: +1116 / -1882 / -1074 | 99 | +0.105 | +0.800 | AMBER |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | RK7 | EV_JL3 | L6M | -464 / -812 | -4118 | +1363 / +2385 | +3602 | c=0.50: -670 / -3246 / +699 | 218 | +0.069 | +0.554 | ok |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | RK7 | EV_JL3 | L3M | -1342 / -2349 | -2802 | +1435 / +2511 | +3602 | c=0.50: -957 / -3246 / +290 | 98 | +0.126 | +0.954 | ok |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | RM7 | EV_JL3 | L6M | +367 / +642 | -8848 | +1260 / +2204 | +289 | c=0.50: -278 / -3372 / +684 | 221 | +0.059 | +0.480 | ok |
| LA4 | time_m_5 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | 120/120 ($2400) | RM7 | EV_JL3 | L3M | -88 / -153 | -1120 | +330 / +578 | +289 | c=0.50: -484 / -940 / -630 | 99 | +0.105 | +0.800 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L6M | -151 / -265 | +1434 | +1902 / +3328 | +3529 | c=0.50: -138 / +1081 / +798 | 194 | +0.128 | +0.920 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -295 / -517 | +2020 | +1674 / +2929 | +3529 | c=0.50: -283 / +1397 / +463 | 94 | +0.139 | +1.009 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | Y2025 | +3196 / +5593 | +302 | -421 / -736 | -2741 | c=0.50: +1225 / +456 / -383 | 331 | -0.005 | -0.032 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | Y2024 | +2577 / +4509 | -31 | +51 / +89 | +2996 | c=0.50: +643 / +2158 / +86 | 302 | -0.005 | -0.029 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | Y2023 | -702 / -1228 | +1826 | +51 / +90 | -4046 | c=0.50: -425 / +813 / -104 | 209 | +0.024 | +0.130 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADDM | EV_JL3 | L6M | -1041 / -1823 | +485 | +2258 / +3952 | +5327 | c=0.50: -1063 / -137 / +1221 | 199 | +0.117 | +0.865 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADDM | EV_JL3 | L3M | -1325 / -2318 | +485 | +670 / +1173 | +5327 | c=0.50: -1245 / -137 / -461 | 96 | +0.128 | +0.942 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +203 / +355 | -457 | +1194 / +2089 | -1023 | c=0.50: +181 / -1080 / +156 | 199 | +0.117 | +0.865 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L3M | +275 / +482 | -457 | +226 / +395 | -1023 | c=0.50: +355 / -1080 / -905 | 96 | +0.128 | +0.942 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RK7 | EV_JL3 | L6M | -1244 / -2177 | +2026 | +1864 / +3263 | +7579 | c=0.50: -1039 / +641 / +803 | 195 | +0.122 | +0.884 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RK7 | EV_JL3 | L3M | -1876 / -3283 | +2026 | +1473 / +2577 | +7579 | c=0.50: -1454 / +641 / +262 | 94 | +0.139 | +1.009 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RK7 | EV_JL3 | Y2025 | +2077 / +3635 | +2657 | -365 / -638 | -7890 | c=0.50: -86 / +3329 / -328 | 332 | -0.005 | -0.031 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RK7 | EV_JL3 | Y2024 | +1516 / +2653 | +183 | -140 / -246 | +4271 | c=0.50: -506 / +2373 / -105 | 302 | -0.005 | -0.029 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RK7 | EV_JL3 | Y2023 | -300 / -526 | -1665 | +330 / +578 | -6454 | c=0.50: -317 / -2677 / +175 | 209 | +0.024 | +0.130 | AMBER |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RM7 | EV_JL3 | L6M | -1041 / -1823 | +485 | +2258 / +3952 | +5327 | c=0.50: -1063 / -137 / +1221 | 199 | +0.117 | +0.865 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RM7 | EV_JL3 | L3M | -1325 / -2318 | +485 | +670 / +1173 | +5327 | c=0.50: -1245 / -137 / -461 | 96 | +0.128 | +0.942 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RM7 | EV_JL3 | Y2025 | +763 / +1334 | +627 | +555 / +970 | +780 | c=0.50: -1272 / +1694 / +580 | 333 | -0.003 | -0.021 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RM7 | EV_JL3 | Y2024 | -1746 / -3056 | +3313 | +148 / +259 | +3798 | c=0.50: -2777 / +5503 / +183 | 302 | -0.005 | -0.029 | ok |
| LA5 | vol_500 | levels_vwap.break {"n": 3, "k": 0.25} | 120/120 ($2400) | RM7 | EV_JL3 | Y2023 | +1331 / +2330 | +3452 | +289 / +506 | -2749 | c=0.50: +1444 / +2439 / +134 | 209 | +0.024 | +0.130 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +471 / +824 | -14141 | +720 / +1260 | +623 | c=0.50: -91 / -6707 / +431 | 175 | +0.037 | +0.241 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -805 / -1409 | -236 | +2495 / +4366 | +623 | c=0.50: -757 / +244 / +1468 | 88 | +0.126 | +0.856 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADDM | EV_JL3 | L6M | -53 / -94 | -5373 | +1130 / +1977 | +75 | c=0.50: -624 / -942 / +811 | 181 | +0.040 | +0.266 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADDM | EV_JL3 | L3M | -1461 / -2558 | -1421 | +1208 / +2114 | +3423 | c=0.50: -1387 / -942 / +181 | 88 | +0.126 | +0.856 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +1191 / +2084 | -6315 | +65 / +114 | -6275 | c=0.50: +620 / -1884 / -253 | 181 | +0.040 | +0.266 | AMBER |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L3M | +138 / +242 | -2364 | +764 / +1336 | -2928 | c=0.50: +213 / -1884 / -263 | 88 | +0.126 | +0.856 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | RK7 | EV_JL3 | L6M | +381 / +667 | -7833 | +580 / +1015 | +3822 | c=0.50: +75 / -5971 / +188 | 178 | +0.050 | +0.327 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | RK7 | EV_JL3 | L3M | -18 / -31 | -6451 | +1327 / +2323 | +3822 | c=0.50: +101 / -5971 / +301 | 88 | +0.126 | +0.856 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | RM7 | EV_JL3 | L6M | -53 / -94 | -5373 | +1130 / +1977 | +75 | c=0.50: -624 / -942 / +811 | 181 | +0.040 | +0.266 | ok |
| LA6 | tick_1300 | levels_opens.reject_native {"tol": 1.0, "conf": "close"} | 120/120 ($2400) | RM7 | EV_JL3 | L3M | -1461 / -2558 | -1421 | +1208 / +2114 | +3423 | c=0.50: -1387 / -942 / +181 | 88 | +0.126 | +0.856 | ok |
| WL1 | rng_28 | levels_vwap_bands.break_native {"n": 1, "k": 0.5} | 90/90 ($1800) | ADD | EV_JL3 | L6M | +2575 / +4506 | -6363 | -221 / -388 | -12694 | c=0.67: +2045 / -5728 / -202 | 244 | -0.004 | -0.033 | RED |
| WL1 | rng_28 | levels_vwap_bands.break_native {"n": 1, "k": 0.5} | 90/90 ($1800) | ADD | EV_JL3 | L3M | +4050 / +7088 | -6363 | -658 / -1151 | -12694 | c=0.67: +3372 / -5728 / -782 | 121 | +0.022 | +0.207 | RED |
| WL1 | rng_28 | levels_vwap_bands.break_native {"n": 1, "k": 0.5} | 90/90 ($1800) | ADDM | EV_JL3 | L6M | +886 / +1550 | -3175 | +337 / +589 | -3350 | c=0.67: +155 / -2967 / +436 | 247 | -0.018 | -0.165 | ok |
| WL1 | rng_28 | levels_vwap_bands.break_native {"n": 1, "k": 0.5} | 90/90 ($1800) | ADDM | EV_JL3 | L3M | +1179 / +2063 | -3175 | -1020 / -1785 | -3350 | c=0.67: +335 / -2967 / -1046 | 119 | +0.005 | +0.042 | ok |
| WL1 | rng_28 | levels_vwap_bands.break_native {"n": 1, "k": 0.5} | 90/90 ($1800) | ADDM | CT_JL3_N_M7L | L6M | +2130 / +3728 | -4117 | -728 / -1273 | -9701 | c=0.67: +1400 / -3909 / -629 | 247 | -0.018 | -0.165 | RED |
| WL1 | rng_28 | levels_vwap_bands.break_native {"n": 1, "k": 0.5} | 90/90 ($1800) | ADDM | CT_JL3_N_M7L | L3M | +2779 / +4863 | -4117 | -1465 / -2563 | -9701 | c=0.67: +1935 / -3909 / -1490 | 119 | +0.005 | +0.042 | RED |
| WL2 | rng_80 | levels_round.retest {"M": 6, "tol": 0.0} | 120/120 ($2400) | ADD | EV_JL3 | L6M | -225 / -394 | -4991 | +627 / +1097 | +4073 | c=0.50: -385 / -2132 / +535 | 191 | +0.011 | +0.077 | ok |
| WL2 | rng_80 | levels_round.retest {"M": 6, "tol": 0.0} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -906 / -1586 | +3414 | +624 / +1093 | +4073 | c=0.50: -712 / +1058 / +195 | 96 | +0.048 | +0.358 | ok |
| WL2 | rng_80 | levels_round.retest {"M": 6, "tol": 0.0} | 120/120 ($2400) | ADDM | EV_JL3 | L6M | -852 / -1490 | -828 | +1265 / +2213 | +6519 | c=0.50: -1145 / -105 / +1244 | 200 | +0.002 | +0.017 | ok |
| WL2 | rng_80 | levels_round.retest {"M": 6, "tol": 0.0} | 120/120 ($2400) | ADDM | EV_JL3 | L3M | -2193 / -3838 | +2250 | +972 / +1702 | +6519 | c=0.50: -2001 / -105 / +612 | 97 | +0.040 | +0.301 | ok |
| WL2 | rng_80 | levels_round.retest {"M": 6, "tol": 0.0} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +393 / +688 | -1770 | +200 / +351 | +168 | c=0.50: +100 / -1048 / +180 | 200 | +0.002 | +0.017 | ok |
| WL2 | rng_80 | levels_round.retest {"M": 6, "tol": 0.0} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L3M | -593 / -1038 | +1308 | +528 / +924 | +168 | c=0.50: -401 / -1048 / +167 | 97 | +0.040 | +0.301 | ok |
| WL4 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +778 / +1362 | -3386 | -453 / -792 | +303 | c=0.50: +214 / -1329 / -285 | 196 | -0.019 | -0.140 | ok |
| WL4 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +493 / +862 | -481 | -192 / -336 | +303 | c=0.50: -77 / +790 / -269 | 96 | +0.009 | +0.064 | ok |
| WL4 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | 120/120 ($2400) | ADDM | EV_JL3 | L6M | -172 / -302 | -1291 | +556 / +974 | +3103 | c=0.50: -841 / +517 / +791 | 203 | -0.026 | -0.196 | ok |
| WL4 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | 120/120 ($2400) | ADDM | EV_JL3 | L3M | -691 / -1209 | -1291 | -627 / -1097 | +3103 | c=0.50: -1275 / +517 / -592 | 99 | -0.004 | -0.029 | ok |
| WL4 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +1072 / +1876 | -2233 | -508 / -889 | -3248 | c=0.50: +403 / -426 / -273 | 203 | -0.026 | -0.196 | ok |
| WL4 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | 120/120 ($2400) | ADDM | CT_JL3_N_M7L | L3M | +909 / +1591 | -2233 | -1071 / -1875 | -3248 | c=0.50: +325 / -426 / -1036 | 99 | -0.004 | -0.029 | ok |
| WL6 | rng_14 | tape_delta.follow_sm {"L": 200, "z": 2.0, "sm": 3} | 94/94 ($1875) | ADD | EV_JL3 | L6M | -544 / -952 | -4221 | +1001 / +1752 | +455 | c=0.64: -850 / -2439 / +966 | 239 | +0.006 | +0.051 | ok |
| WL6 | rng_14 | tape_delta.follow_sm {"L": 200, "z": 2.0, "sm": 3} | 94/94 ($1875) | ADD | EV_JL3 | L3M | -830 / -1453 | -484 | -164 / -287 | +455 | c=0.64: -979 / +1274 / -73 | 117 | -0.015 | -0.135 | ok |
| WL6 | rng_14 | tape_delta.follow_sm {"L": 200, "z": 2.0, "sm": 3} | 94/94 ($1875) | ADDM | EV_JL3 | L6M | -797 / -1395 | -3140 | +714 / +1250 | +1409 | c=0.64: -1243 / -1381 / +748 | 247 | -0.006 | -0.050 | ok |
| WL6 | rng_14 | tape_delta.follow_sm {"L": 200, "z": 2.0, "sm": 3} | 94/94 ($1875) | ADDM | EV_JL3 | L3M | -1976 / -3457 | -3140 | -920 / -1609 | +1409 | c=0.64: -2179 / -1381 / -797 | 117 | -0.020 | -0.181 | ok |
| WL6 | rng_14 | tape_delta.follow_sm {"L": 200, "z": 2.0, "sm": 3} | 94/94 ($1875) | ADDM | CT_JL3_N_M7L | L6M | +447 / +783 | -4082 | -350 / -613 | -4942 | c=0.64: +1 / -2324 / -316 | 247 | -0.006 | -0.050 | AMBER |
| WL6 | rng_14 | tape_delta.follow_sm {"L": 200, "z": 2.0, "sm": 3} | 94/94 ($1875) | ADDM | CT_JL3_N_M7L | L3M | -376 / -657 | -4082 | -1364 / -2387 | -4942 | c=0.64: -579 / -2324 / -1242 | 117 | -0.020 | -0.181 | AMBER |
| WL7 | time_m_3 | tape_delta.cvd_fade {"N": 10, "L": 100, "z": 1.5} | 58/58 ($1160) | ADD | EV_JL3 | L6M | +888 / +1554 | -10201 | +1124 / +1967 | -6598 | c=1.03: +951 / -10578 / +1123 | 217 | -0.001 | -0.011 | AMBER |
| WL7 | time_m_3 | tape_delta.cvd_fade {"N": 10, "L": 100, "z": 1.5} | 58/58 ($1160) | ADD | EV_JL3 | L3M | +883 / +1545 | -4659 | +1481 / +2591 | -6598 | c=1.03: +939 / -4776 / +1491 | 106 | +0.031 | +0.255 | AMBER |
| WL7 | time_m_3 | tape_delta.cvd_fade {"N": 10, "L": 100, "z": 1.5} | 58/58 ($1160) | ADDM | EV_JL3 | L6M | -477 / -834 | -218 | +1220 / +2135 | -1207 | c=1.03: -415 / -501 / +1213 | 228 | -0.020 | -0.172 | ok |
| WL7 | time_m_3 | tape_delta.cvd_fade {"N": 10, "L": 100, "z": 1.5} | 58/58 ($1160) | ADDM | EV_JL3 | L3M | -698 / -1222 | -35 | +117 / +205 | -1207 | c=1.03: -627 / -230 / +111 | 111 | -0.018 | -0.152 | ok |
| WL7 | time_m_3 | tape_delta.cvd_fade {"N": 10, "L": 100, "z": 1.5} | 58/58 ($1160) | ADDM | CT_JL3_N_M7L | L6M | +768 / +1344 | -1161 | +156 / +272 | -7558 | c=1.03: +830 / -1444 / +149 | 228 | -0.020 | -0.172 | RED |
| WL7 | time_m_3 | tape_delta.cvd_fade {"N": 10, "L": 100, "z": 1.5} | 58/58 ($1160) | ADDM | CT_JL3_N_M7L | L3M | +902 / +1578 | -977 | -327 / -572 | -7558 | c=1.03: +973 / -1173 / -333 | 111 | -0.018 | -0.152 | RED |
| WL9 | time_m_4 | momentum_roc.break {"len": 10, "wd": 1.0} | 120/88 ($2400) | ADD | EV_JL3 | L6M | +322 / +563 | +834 | +222 / +388 | -2307 | c=0.50: -138 / +1431 / +359 | 208 | -0.015 | -0.115 | ok |
| WL9 | time_m_4 | momentum_roc.break {"len": 10, "wd": 1.0} | 120/88 ($2400) | ADD | EV_JL3 | L3M | +1029 / +1801 | +834 | -511 / -894 | -2307 | c=0.50: +122 / +1431 / -367 | 96 | -0.016 | -0.120 | ok |
| WL9 | time_m_4 | momentum_roc.break {"len": 10, "wd": 1.0} | 120/88 ($2400) | ADDM | EV_JL3 | L6M | +293 / +513 | -1656 | +596 / +1043 | -4232 | c=0.50: -439 / -1059 / +831 | 210 | -0.025 | -0.196 | ok |
| WL9 | time_m_4 | momentum_roc.break {"len": 10, "wd": 1.0} | 120/88 ($2400) | ADDM | EV_JL3 | L3M | +1315 / +2301 | -1656 | -747 / -1307 | -4232 | c=0.50: +170 / -1059 / -493 | 97 | -0.028 | -0.212 | ok |
| WL9 | time_m_4 | momentum_roc.break {"len": 10, "wd": 1.0} | 120/88 ($2400) | ADDM | CT_JL3_N_M7L | L6M | +1538 / +2691 | -2599 | -468 / -819 | -10583 | c=0.50: +805 / -2002 / -233 | 210 | -0.025 | -0.196 | RED |
| WL9 | time_m_4 | momentum_roc.break {"len": 10, "wd": 1.0} | 120/88 ($2400) | ADDM | CT_JL3_N_M7L | L3M | +2915 / +5101 | -2599 | -1191 / -2085 | -10583 | c=0.50: +1770 / -2002 / -937 | 97 | -0.028 | -0.212 | RED |
| LB1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +299 / +524 | -2345 | +42 / +74 | +2270 | c=0.50: -395 / -809 / +187 | 259 | -0.013 | -0.120 | ok |
| LB1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +491 / +859 | +1144 | +1575 / +2757 | +2270 | c=0.50: -456 / +1050 / +1080 | 122 | +0.044 | +0.413 | ok |
| LB2 | cusum_28 | trend_macd.hist_turn_native {"len": 26, "width": 0.03} | 60/60 ($1200) | ADD | EV_JL3 | L6M | +706 / +1236 | -4719 | -384 / -673 | -4190 | c=1.00: +706 / -4719 / -384 | 430 | +0.003 | +0.053 | ok |
| LB2 | cusum_28 | trend_macd.hist_turn_native {"len": 26, "width": 0.03} | 60/60 ($1200) | ADD | EV_JL3 | L3M | +1391 / +2434 | -4719 | +850 / +1488 | -4190 | c=1.00: +1391 / -4719 / +850 | 219 | +0.112 | +1.880 | ok |
| LB3 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | 120/120 ($2400) | ADD | EV_JL3 | L6M | -762 / -1334 | -306 | -654 / -1145 | +3927 | c=0.50: -331 / -1562 / -616 | 224 | -0.004 | -0.031 | ok |
| LB3 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -685 / -1199 | -67 | -3069 / -5371 | +3927 | c=0.50: +42 / -1562 / -2550 | 107 | -0.052 | -0.432 | AMBER |
| LB4 | bmsg_B320 | bands_regchan.fade_linreg_native {"clk": 5, "k": 1.5} | 120/120 ($2400) | ADD | EV_JL3 | L6M | -1434 / -2510 | +2016 | +917 / +1606 | +4089 | c=0.50: -1217 / +255 / +651 | 186 | +0.032 | +0.222 | ok |
| LB4 | bmsg_B320 | bands_regchan.fade_linreg_native {"clk": 5, "k": 1.5} | 120/120 ($2400) | ADD | EV_JL3 | L3M | -1675 / -2930 | +2016 | +539 / +943 | +4089 | c=0.50: -1247 / +255 / +160 | 89 | +0.046 | +0.316 | ok |
| LB5 | bmsg_B320 | manual_macd.sigcross_native {"f": 20, "s": 45, "g": 15} | 120/120 ($2400) | ADD | EV_JL3 | L6M | -121 / -211 | -456 | +2071 / +3625 | +829 | c=0.50: -371 / +1339 / +1482 | 228 | +0.058 | +0.491 | ok |
| LB5 | bmsg_B320 | manual_macd.sigcross_native {"f": 20, "s": 45, "g": 15} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +602 / +1053 | -456 | +1500 / +2625 | +829 | c=0.50: +77 / +1339 / +1170 | 111 | +0.032 | +0.275 | ok |
| LB6 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | 60/60 ($1200) | ADD | EV_JL3 | L6M | +1828 / +3199 | -10766 | +772 / +1351 | -8646 | c=1.00: +1828 / -10766 / +772 | 485 | +0.058 | +1.045 | AMBER |
| LB6 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | 60/60 ($1200) | ADD | EV_JL3 | L3M | +3355 / +5871 | -10766 | -1135 / -1986 | -8646 | c=1.00: +3355 / -10766 / -1135 | 226 | +0.016 | +0.272 | RED |
| LB7 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | 60/60 ($1200) | ADD | EV_JL3 | L6M | -280 / -490 | -1761 | +409 / +715 | +1702 | c=1.00: -280 / -1761 / +409 | 193 | +0.070 | +0.503 | ok |
| LB7 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | 60/60 ($1200) | ADD | EV_JL3 | L3M | -353 / -618 | -1761 | +369 / +645 | +1702 | c=1.00: -353 / -1761 / +369 | 97 | -0.005 | -0.037 | ok |
| LB8 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | 120/120 ($2400) | ADD | EV_JL3 | L6M | +2873 / +5028 | -9822 | +546 / +955 | -14151 | c=0.50: +1318 / -6931 / +334 | 229 | +0.021 | +0.177 | RED |
| LB8 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | 120/120 ($2400) | ADD | EV_JL3 | L3M | +4632 / +8107 | -9822 | -2641 / -4622 | -14151 | c=0.50: +2501 / -6931 / -1945 | 98 | -0.077 | -0.580 | RED |

Labels: none yet (controls pending).

