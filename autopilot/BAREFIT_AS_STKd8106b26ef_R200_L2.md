# BAREFIT_AS_STKd8106b26ef - truly bare all-layers fit (W-LAYERS, 2026-11-24 01:59Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 3481 / -10508 / -9931 / -6608 / 10247 | 1303 / -5701 / -2582 / -3197 / 4749 |
| L3M | 3680 / -10508 / -3086 / -6608 / 10033 | 1308 / -5701 / -1054 / -2599 / 3590 |
| 2023 | 5307 / -11253 / -7808 / -4738 / 1015 | 4218 / -10489 / -6170 / -4051 / 159 |
| 2024 | 5048 / -18731 / -10393 / -8930 / 1783 | 4312 / -12462 / -6023 / -2893 / 781 |
| 2025 | 6865 / -18734 / -11947 / -12080 / 1758 | 11160 / -19208 / -11625 / -4374 / -53 |

Best joint combo TL3_SR_AS_STKd8106b26ef_BF2_JT243: {'LOSS.MF1': ['CU', 4], 'LOCK.MF1': ['LK', 5], 'ZONE.MF1': ['ZONE', 5], 'LOSS.MF2': ['CU', 4], 'LOCK.MF2': ['LK', 9], 'LOSS.MF3': ['CU', 2], 'LOCK.MF3': ['LK', 3], 'TAKE.MF3': ['TK', 1], 'LOSS.MF4': ['CU', 2], 'LOCK.MF4': ['LK', 2], 'TAKE.MF4': ['NRT', 2], 'LOCK.MF5': ['LK', 6], 'TAKE.MF5': ['NRT', 2], 'ZONE.MF5': ['ZONE', 2], 'BL': ['BL', 1], 'CAP': ['CAP', 8], 'SZW': ['SZW', 3], 'NTS': ['NTS', 1], 'CG': ['CGB', 2], 'DLC': ['DLC', 12]}
Rolling walk-forward vs BARE among the combos 0.838 over 80 periods; fixed-pick persistence 0.817; year bands vs bare (equal-risk $/wk) RED/RED/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU4 loss cut when unrealised <= -40 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF1: LK4 lock at 65% -> stop to entry+0 pts (d ulcer -405, d $/wk +750)
- TAKE.MF1: TK10 take at 95% of target after 5 s without a new extreme (d ulcer -75, d $/wk +608)
- ZONE.MF1: ZONE5 zone no-trade set MF1 Skip within 30 pts (d ulcer -1042, d $/wk +25)
- LOSS.MF2: CU4 loss cut when unrealised <= -60 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF2: LK6 lock at 65% -> stop to entry+20 pts (d ulcer -83, d $/wk -252)
- TAKE.MF2: NRT4 near-target latch MF2 X 0.95 givep 0.1 (d ulcer -327, d $/wk -4)
- ZONE.MF2: ZONE2 zone no-trade set MF2 Half within 30 pts (d ulcer -38, d $/wk -416)
- LOSS.MF3: CU2 loss cut when unrealised <= -36 pts (0.6 x stop) (d ulcer -351, d $/wk -827)
- LOCK.MF3: LK2 lock at 50% -> stop to entry+10 pts (d ulcer +95, d $/wk -1012, fails the guard: weak)
- TAKE.MF3: TK2 take at 50% of target after 15 s without a new extreme (d ulcer -48, d $/wk -981)
- ZONE.MF3: ZONE6 zone no-trade set MF3 Skip within 50 pts (d ulcer -113, d $/wk -672)
- LOSS.MF4: CU2 loss cut when unrealised <= -36 pts (0.6 x stop) (d ulcer -842, d $/wk +1095)
- LOCK.MF4: LK2 lock at 50% -> stop to entry+10 pts (d ulcer -231, d $/wk -1812)
- TAKE.MF4: NRT4 near-target latch MF4 X 0.95 givep 0.1 (d ulcer -138, d $/wk -380)
- ZONE.MF4: ZONE2 zone no-trade set MF4 Half within 30 pts (d ulcer -105, d $/wk -823)
- LOSS.MF5: FR_LOSS9 W-FASTR pick: scratch: after -45 exit at -5 (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF5: LK6 lock at 65% -> stop to entry+20 pts (d ulcer +435, d $/wk +678, fails the guard: weak)
- TAKE.MF5: TK7 take at 80% of target after 5 s without a new extreme (d ulcer -1004, d $/wk -1572)
- ZONE.MF5: ZONE3 zone no-trade set MF5 Half within 50 pts (d ulcer -421, d $/wk -344)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer -271, d $/wk -651)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -2722, d $/wk -1886)
- CAP: CAP6 per-book day loss stop -3R ($7200) (d ulcer -198, d $/wk -324, fails the guard: weak)
- STK: STK4 WHOLE-STACK day profit stop +12R of one book ($28800) (d ulcer +0, d $/wk -838, fails the guard: weak)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -2989, d $/wk -6857)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer -783, d $/wk -550)
- CG: CGB3 skip after 3 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer +197, d $/wk -849, fails the guard: weak)
- DLA: DLA8 per-book day loss halt at -6R (open P&L counts, close the position, halt rest of session) (d ulcer -295, d $/wk -25)
- DLB: DLB8 stack day loss halt at -$12000 per lot per book (open P&L counts, all books halted, positions closed, rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLC: DLC12 per-book pause 120 min after 5 consecutive full-stop losses, then re-arm (d ulcer -315, d $/wk -282)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -1456 / -1671 / -1459
- LOCK.MF1: -1097 / -1550 / -1925
- TAKE.MF1: -1556 / -2058 / -976
- ZONE.MF1: -953 / -1390 / -2224
- LOSS.MF2: -1497 / -1549 / -1542
- LOCK.MF2: -1846 / -1152 / -1602
- TAKE.MF2: -1662 / -1566 / -1366
- ZONE.MF2: -1161 / -1987 / -1427
- LOSS.MF3: -1148 / -1805 / -1621
- LOCK.MF3: -1799 / -1343 / -1457
- TAKE.MF3: -1249 / -1426 / -1904
- ZONE.MF3: -1365 / -1626 / -1592
- LOSS.MF4: -1173 / -2188 / -1214
- LOCK.MF4: -2108 / -1205 / -1297
- TAKE.MF4: -1855 / -1818 / -928
- ZONE.MF4: -1755 / -1359 / -1483
- LOSS.MF5: -1593 / -1200 / -1798
- LOCK.MF5: -1314 / -1944 / -1322
- TAKE.MF5: -1888 / -1302 / -1412
- ZONE.MF5: -1599 / -1484 / -1509
- SC: -1910 / -1383 / -1309
- BL: -1407 / -1836 / -1341
- CAP: -1823 / -1653 / -1124
- STK: -1906 / -1380 / -1317
- SZW: -308 / -2174 / -2062
- NTS: -1739 / -1680 / -1177
- CG: -2423 / -1461 / -738
- DLA: -1649 / -1590 / -1355
- DLB: -1869 / -1535 / -1198
- DLC: -1847 / -1335 / -1418

