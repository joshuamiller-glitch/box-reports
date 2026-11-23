# BAREFIT_AS_STKd8106b26ef - truly bare all-layers fit (W-LAYERS, 2026-11-23 18:34Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 3481 / -10508 / -9931 / -6608 / 10247 | 1323 / -6123 / -2808 / -3317 / 4850 |
| L3M | 3680 / -10508 / -3086 / -6608 / 10033 | 1343 / -6123 / 387 / -3317 / 3767 |
| 2023 | 5307 / -11253 / -7808 / -4738 / 1015 | 3836 / -9640 / -6136 / -3872 / 177 |
| 2024 | 5048 / -18731 / -10393 / -8930 / 1783 | 4383 / -12278 / -6023 / -2903 / 768 |
| 2025 | 6865 / -18734 / -11947 / -12080 / 1758 | 10806 / -18069 / -10905 / -4761 / -55 |

Best joint combo TL3_SR_AS_STKd8106b26ef_BF2_JT143: {'LOSS.MF1': ['CU', 4], 'LOCK.MF1': ['LK', 5], 'ZONE.MF1': ['ZONE', 5], 'LOSS.MF2': ['STC', 4], 'LOCK.MF2': ['LK', 9], 'LOSS.MF3': ['STC', 1], 'LOCK.MF3': ['LK', 3], 'TAKE.MF3': ['TK', 1], 'LOSS.MF4': ['CU', 2], 'LOCK.MF4': ['LK', 2], 'TAKE.MF4': ['NRT', 2], 'LOCK.MF5': ['LK', 6], 'TAKE.MF5': ['NRT', 2], 'ZONE.MF5': ['ZONE', 2], 'BL': ['BL', 1], 'CAP': ['CAP', 8], 'SZW': ['SZW', 3], 'NTS': ['NTS', 1], 'CG': ['CGB', 2], 'DLC': ['DLC', 12]}
Rolling walk-forward vs BARE among the combos 0.875 over 80 periods; fixed-pick persistence 0.817; year bands vs bare (equal-risk $/wk) RED/RED/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU4 loss cut when unrealised <= -40 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF1: LK4 lock at 65% -> stop to entry+0 pts (d ulcer -405, d $/wk +750)
- TAKE.MF1: TK10 take at 95% of target after 5 s without a new extreme (d ulcer -75, d $/wk +608)
- ZONE.MF1: ZONE5 zone no-trade set MF1 Skip within 30 pts (d ulcer -1042, d $/wk +25)
- LOSS.MF2: STC4 state-cut cell MF2 mult 15.0 (d ulcer -46, d $/wk +68)
- LOCK.MF2: LK6 lock at 65% -> stop to entry+20 pts (d ulcer -83, d $/wk -252)
- TAKE.MF2: NRT4 near-target latch MF2 X 0.95 givep 0.1 (d ulcer -327, d $/wk -4)
- ZONE.MF2: ZONE2 zone no-trade set MF2 Half within 30 pts (d ulcer -38, d $/wk -416)
- LOSS.MF3: STC1 state-cut cell MF3 arm 30.0 (d ulcer -480, d $/wk -607)
- LOCK.MF3: LK2 lock at 50% -> stop to entry+10 pts (d ulcer +95, d $/wk -1012, fails the guard: weak)
- TAKE.MF3: TK2 take at 50% of target after 15 s without a new extreme (d ulcer -48, d $/wk -981)
- ZONE.MF3: ZONE6 zone no-trade set MF3 Skip within 50 pts (d ulcer -113, d $/wk -672)
- LOSS.MF4: CU2 loss cut when unrealised <= -36 pts (0.6 x stop) (d ulcer -842, d $/wk +1095)
- LOCK.MF4: LK2 lock at 50% -> stop to entry+10 pts (d ulcer -231, d $/wk -1812)
- TAKE.MF4: NRT4 near-target latch MF4 X 0.95 givep 0.1 (d ulcer -138, d $/wk -380)
- ZONE.MF4: ZONE2 zone no-trade set MF4 Half within 30 pts (d ulcer -105, d $/wk -823)
- LOSS.MF5: STC2 state-cut cell MF5 arm 60.0 (d ulcer +0, d $/wk +0, fails the guard: weak)
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

- LOSS.MF1: -1802 / -1635 / -1769
- LOCK.MF1: -1441 / -1756 / -1995
- TAKE.MF1: -1660 / -2164 / -1377
- ZONE.MF1: -1450 / -1584 / -2159
- LOSS.MF2: -1688 / -1656 / -1858
- LOCK.MF2: -2007 / -1244 / -1962
- TAKE.MF2: -1756 / -1820 / -1628
- ZONE.MF2: -1604 / -1683 / -1911
- LOSS.MF3: -1483 / -1943 / -1769
- LOCK.MF3: -1775 / -1485 / -1944
- TAKE.MF3: -1703 / -1437 / -2063
- ZONE.MF3: -1692 / -1754 / -1755
- LOSS.MF4: -1514 / -2340 / -1341
- LOCK.MF4: -2338 / -1391 / -1496
- TAKE.MF4: -1845 / -1692 / -1670
- ZONE.MF4: -1915 / -1450 / -1845
- LOSS.MF5: -1733 / -1482 / -1988
- LOCK.MF5: -1510 / -1899 / -1786
- TAKE.MF5: -2058 / -1335 / -1822
- ZONE.MF5: -2067 / -1454 / -1695
- SC: -1533 / -1809 / -1854
- BL: -1672 / -1790 / -1738
- CAP: -1893 / -1959 / -1357
- STK: -1997 / -1655 / -1562
- SZW: -770 / -2514 / -1884
- NTS: -2020 / -1948 / -1246
- CG: -2428 / -1568 / -1233
- DLA: -1677 / -1923 / -1602
- DLB: -1822 / -1905 / -1479
- DLC: -2131 / -1407 / -1680

