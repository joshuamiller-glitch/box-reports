# NEW_BOOK_BEATS_LIVE_ASIA - does a new book beat the live Asia book(s) in the exact engine? (W-ASIA, order 0400Z), refreshed 2026-11-19 10:00Z

**vs TODAY's stack (JL3, today's DAY-DONE); Asia is decided FIRST; label BETTER = calibration pending, NOT calibrated.** Asia rule (higher bar, order 1731Z / 0210Z item 4): a REPLACE row (new book ON, the named live Asia book's Asia entries OFF) beats that live book only if on BOTH L6M and L3M the stack ulcer is LOWER (drawdown first) AND mean $/wk is not lower AND worst week and max drawdown are not worse; then prior years (no RED = >30% worse; AMBER shown), persistence > 0.60, 30 date-shift controls, calibration. du = d stack ulcer (negative = better), dm = d mean $/wk (base lots, $4.84 RT).

**Counts:** Asia cells with any engine row 375; cells with a finished REPLACE verdict (L6M+L3M landed) 317; cells that beat at least one live Asia book on L6M+L3M under the Asia rule (BETTER, calibration pending) 14 (under the looser NY rule 27); ADD rows finished 361.

| live Asia book replaced | cells finished | beat it | pending |
|---|---|---|---|
| K7 | 57 | 0 | 4 |
| P7 | 51 | 0 | 3 |
| A7 | 317 | 14 | 10 |
| H7 | 55 | 0 | 3 |
| U7 | 55 | 0 | 2 |

## Engine throughput and queue (Asia sets TL3_ASI_*)
Asia set-months landed: last 1 h 2345, last 3 h 6624; Asia queue lines pending (not DONE): 35122.

## Proof that Asia sets are launched ahead of NY AM
- QUEUES.txt order on server 2 dispatcher: _asi position 4, _nye/pending_l 11, _nye/pending_w , _lon 12 (lower = earlier).
- PRIORITY.txt admission order (TP admit, all hosts): NT > ASI > NYL > NYR > NYF > FR > NYE > NYW > LON > ME
- box1 running engine sets by tag: 28 TL3_NYW_      12 TL3_ASI_       8 TL3_LON_
- server2 running engine sets by tag: 56 TL3_ASI_
- A running engine sets by tag: 199 TL3_ASI_
- B running engine sets by tag: 200 TL3_ASI_

## Best five rows (drawdown first: most negative L6M du among cells with a finished REPLACE row)
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | controls |
|---|---|---|---|---|---|---|---|
| AB6 trb_240 / levels_fib15.break_native {"n": 3, "k": 0.5} / plain60/60 / both | no (L6M du +335 dm +1217 | L3M du +511 dm -702) | no (L6M du +2242 dm -2808 | L3M du +3964 dm -6870) | not run | no (L6M du +49 dm +370 | L3M du +377 dm -199) | no (L6M du -296 dm -526 | L3M du -327 dm -1249) | no (L6M du -1396 dm -146 | L3M du -2236 dm -914) | 0 of 30 |
| Lda55d973 vol_750 / momentum_stoch.zone_break_native {"len": 9, "lvl": 80} / plain60/60 / long | yes (L6M du -1672 dm +2260 | L3M du -2265 dm +1965 RED Y2025) | no (L6M du +360 dm -2813 | L3M du +724 dm -4895) | no (L6M du +1702 dm -8194 | L3M du +2043 dm -6482) | yes (L6M du -1222 dm +911 | L3M du -1416 dm +2143 RED Y2025) | no (L6M du -99 dm -268 | L3M du -1462 dm +1191) | no (L6M du -1348 dm -66 | L3M du -1355 dm -1789) | 0 of 30 |
| La5b5d03a time_m_2 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / long | no (L6M du +222 dm +485 | L3M du +463 dm -51 RED Y2023) | no (L6M du +926 dm -2686 | L3M du +2289 dm -5618) | no (L6M du +3399 dm -9027 | L3M du +3705 dm -6504) | yes (L6M du -1197 dm +1547 | L3M du -892 dm +1038 RED Y2023) | no (L6M du +1058 dm -152 | L3M du -311 dm -616) | no (L6M du +99 dm -575 | L3M du -1062 dm -419) | 0 of 30 |
| Lcb276f27 tm120 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / long | no (L6M du +269 dm +872 | L3M du +546 dm +19 RED Y2023) | no (L6M du +985 dm -2570 | L3M du +2381 dm -5549) | no (L6M du +3438 dm -8996 | L3M du +3770 dm -6434) | yes (L6M du -1146 dm +1567 | L3M du -811 dm +1085 RED Y2023) | no (L6M du +1110 dm -122 | L3M du -214 dm -547) | no (L6M du +134 dm -550 | L3M du -996 dm -348) | 0 of 30 |
| Leee81e35 vol_750 / bands_atrchan.break_ext {"n": 20, "atr": 14, "k": 2.0} / asym15u/30u / long | no (L6M du +1888 dm -1084 | L3M du -1129 dm -101) | no (L6M du -359 dm -2865 | L3M du -377 dm -4775) | no (L6M du +4995 dm -10479 | L3M du +4462 dm -8644) | no (L6M du -992 dm +1085 | L3M du -895 dm +1573 RED Y2025) | no (L6M du +884 dm -1170 | L3M du -581 dm -376) | no (L6M du +1300 dm -2028 | L3M du -626 dm -1577) | 0 of 30 |

## Cells that beat a live Asia book (Asia rule, yes), drawdown first
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | prior years run | controls |
|---|---|---|---|---|---|---|---|---|
| Lda55d973 vol_750 / momentum_stoch.zone_break_native {"len": 9, "lvl": 80} / plain60/60 / long | yes (L6M du -1672 dm +2260 | L3M du -2265 dm +1965 RED Y2025) | no (L6M du +360 dm -2813 | L3M du +724 dm -4895) | no (L6M du +1702 dm -8194 | L3M du +2043 dm -6482) | yes (L6M du -1222 dm +911 | L3M du -1416 dm +2143 RED Y2025) | no (L6M du -99 dm -268 | L3M du -1462 dm +1191) | no (L6M du -1348 dm -66 | L3M du -1355 dm -1789) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| La5b5d03a time_m_2 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / long | no (L6M du +222 dm +485 | L3M du +463 dm -51 RED Y2023) | no (L6M du +926 dm -2686 | L3M du +2289 dm -5618) | no (L6M du +3399 dm -9027 | L3M du +3705 dm -6504) | yes (L6M du -1197 dm +1547 | L3M du -892 dm +1038 RED Y2023) | no (L6M du +1058 dm -152 | L3M du -311 dm -616) | no (L6M du +99 dm -575 | L3M du -1062 dm -419) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| Lcb276f27 tm120 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / long | no (L6M du +269 dm +872 | L3M du +546 dm +19 RED Y2023) | no (L6M du +985 dm -2570 | L3M du +2381 dm -5549) | no (L6M du +3438 dm -8996 | L3M du +3770 dm -6434) | yes (L6M du -1146 dm +1567 | L3M du -811 dm +1085 RED Y2023) | no (L6M du +1110 dm -122 | L3M du -214 dm -547) | no (L6M du +134 dm -550 | L3M du -996 dm -348) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L0a809c2e kagi_40 / trend_ma_t3.price_native {"len": 13, "width": 0.25} / plain60/60 / long | no (L6M du -47 dm +1439 | L3M du -1599 dm +1297) | not run | not run | yes (L6M du -789 dm +402 | L3M du -1498 dm +1029) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L7c368a4f time_m_5 / pullback_ema.depth {"len": 10, "w": 0.5} / plain60/60 / long | no (L6M du +682 dm +2019 | L3M du -454 dm +1240 RED Y2025) | no (L6M du -649 dm -1287 | L3M du -1529 dm -2786) | no (L6M du +2892 dm -7177 | L3M du +3173 dm -4564) | yes (L6M du -199 dm +1810 | L3M du -1260 dm +3199) | no (L6M du +334 dm +628 | L3M du -711 dm +811) | no (L6M du +52 dm +184 | L3M du -2119 dm +569) | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L5c9e11b3 vol_750 / momentum_mvote.v3of5 {"scale": 0.25, "thr": 0.25} / plain60/60 / long | no (L6M du -815 dm +2152 | L3M du -1706 dm +3570 RED Y2025) | no (L6M du +1530 dm -2252 | L3M du +2684 dm -3703) | no (L6M du +2680 dm -9625 | L3M du +2168 dm -6262) | yes (L6M du -603 dm +1062 | L3M du -1151 dm +3460 RED Y2025) | no (L6M du -451 dm +87 | L3M du -636 dm +2865 RED Y2025,Y2023) | no (L6M du -169 dm -472 | L3M du -651 dm +1123) | K7:0,P7:0,A7:3,H7:3,U7:0 | 0 of 30 |
| L1edb9fab tm300 / pullback_ema.depth {"len": 10, "w": 0.5} / plain60/60 / long | no (L6M du +747 dm +1854 | L3M du -411 dm +1205 RED Y2025) | no (L6M du -584 dm -1527 | L3M du -1448 dm -2924) | no (L6M du +3214 dm -7331 | L3M du +3583 dm -4483) | yes (L6M du -142 dm +1606 | L3M du -1252 dm +3083) | no (L6M du +391 dm +413 | L3M du -685 dm +692) | no (L6M du +246 dm +17 | L3M du -1893 dm +426) | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| Ledfbf4d2 vol_350 / bands_bollinger.break_native {"clk": 20, "k": 1.5} / plain60/60 / long | no (L6M du -813 dm +880 | L3M du -949 dm +64 RED Y2025) | no (L6M du -567 dm -1956 | L3M du -296 dm -3836) | no (L6M du +3368 dm -10349 | L3M du +3215 dm -7631) | yes (L6M du -459 dm +384 | L3M du -548 dm +1331 RED Y2025) | no (L6M du -541 dm -839 | L3M du -443 dm -582) | no (L6M du -421 dm -1230 | L3M du -860 dm -2636) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L17ce266f tm240 / momentum_rsi.mom {"len": 10, "lvl": 60} / plain60/60 / long | no (L6M du +485 dm +1043 | L3M du -887 dm +1432) | not run | not run | yes (L6M du -406 dm +659 | L3M du -119 dm +1682) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L5d9e7166 tm240 / momentum_rsi.mom_native {"len": 10, "lvl": 60} / plain60/60 / long | no (L6M du +485 dm +1043 | L3M du -887 dm +1432) | not run | not run | yes (L6M du -406 dm +659 | L3M du -119 dm +1682) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| Lf77e374b tm240 / bands_donchian.break {"n": 10, "buf": 0.0} / plain60/60 / long | no (L6M du +1118 dm +533 | L3M du +373 dm -278 RED Y2025) | no (L6M du +716 dm -1957 | L3M du +1701 dm -4841) | no (L6M du +3792 dm -9480 | L3M du +4392 dm -8197) | yes (L6M du -403 dm +1440 | L3M du -202 dm +2270 RED Y2025) | no (L6M du +2636 dm -1345 | L3M du +1734 dm -1341) | no (L6M du +1820 dm -1319 | L3M du +1943 dm -3101) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L05222ff9 time_m_4 / momentum_rsi.mom_native {"len": 10, "lvl": 60} / plain60/60 / long | no (L6M du +497 dm +464 | L3M du -884 dm +1412) | not run | not run | yes (L6M du -395 dm +85 | L3M du -122 dm +1676) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L63ff9ae8 time_m_4 / momentum_rsi.mom {"len": 10, "lvl": 60} / plain60/60 / long | no (L6M du +497 dm +464 | L3M du -884 dm +1412) | not run | not run | yes (L6M du -395 dm +85 | L3M du -122 dm +1676) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L0b1d7882 tm30 / bands_vwap.break {"minbars": 10, "k": 1.0} / plain60/60 / long | no (L6M du +782 dm +300 | L3M du +39 dm +724 RED Y2025) | no (L6M du +235 dm -3361 | L3M du +231 dm -4322) | no (L6M du +4343 dm -9748 | L3M du +3897 dm -6152) | yes (L6M du -65 dm +395 | L3M du -152 dm +1541 RED Y2025) | no (L6M du +1224 dm -1762 | L3M du +1599 dm -1201) | no (L6M du -117 dm -1186 | L3M du -2415 dm -21) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |

## D8 gate (orders 0213Z, 0228Z)
Nothing enters D8 without the EXIT RUN (68 recipes) on its own entries. Candidates are appended to autopilot/D8_CANDIDATES.txt (append-only, session Asia). Engine cost after the exit screen for the 14 Asia cell(s) that beat a live book today: about 24122 set-months (prior years + 30 controls + layers/exit rows ~1,723 per candidate).

All other cells: see /mnt/l2/l2vast/_asi_lad/beats_rows.csv (verdict per live book: no / pending). Asia ladder state: `python3 code/th_asia/asia_ladder.py status`.

