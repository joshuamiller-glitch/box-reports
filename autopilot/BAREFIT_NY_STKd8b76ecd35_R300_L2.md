# BAREFIT_NY_STKd8b76ecd35 - truly bare all-layers fit (W-LAYERS, 2026-11-24 21:19Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 4610 / -17430 / -16945 / -7910 / 7061 | 1760 / -5109 / -2275 / -2752 / 3038 |
| L3M | 3635 / -9728 / -3473 / -7119 / 6339 | 2091 / -5109 / -2275 / -2752 / 2014 |
| 2023 | 11154 / -31407 / -13155 / -12475 / 1954 | 7525 / -20192 / -8146 / -5447 / 869 |
| 2024 | 11309 / -32917 / -19403 / -10812 / 2270 | 4335 / -11167 / -7074 / -4246 / 1266 |
| 2025 | 15615 / -59614 / -30363 / -17271 / 3476 | 7395 / -26262 / -12856 / -9596 / 1686 |

Best joint combo TL3_SR_NY_STKd8b76ecd35_BF2_JT368: {'LOSS.MF1': ['CU', 2], 'LOCK.MF1': ['LK', 1], 'ZONE.MF1': ['ZONE', 6], 'LOSS.MF2': ['CX', 1], 'TAKE.MF2': ['TK', 1], 'ZONE.MF2': ['ZONE', 2], 'LOSS.MF3': ['CU', 4], 'ZONE.MF3': ['ZONE', 3], 'LOSS.MF4': ['CU', 4], 'LOCK.MF4': ['LK', 7], 'TAKE.MF4': ['SHV', 2], 'LOCK.MF5': ['LK', 8], 'TAKE.MF5': ['FR_TAKE', 4], 'ZONE.MF5': ['ZONE', 4], 'BL': ['BL', 1], 'STK': ['STK', 3], 'SZW': ['SZW', 3], 'NTS': ['NTS', 1], 'DLA': ['DLA', 16], 'DLB': ['DLB', 6], 'DLC': ['DLC', 2]}
Rolling walk-forward vs BARE among the combos 0.838 over 80 periods; fixed-pick persistence 0.914; year bands vs bare (equal-risk $/wk) RED/GREEN/GREEN; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU3 loss cut when unrealised <= -72 pts (0.8 x stop) (d ulcer -716, d $/wk +335)
- LOCK.MF1: LK1 lock at 50% -> stop to entry+0 pts (d ulcer -961, d $/wk -1526)
- TAKE.MF1: TK1 take at 50% of target after 5 s without a new extreme (d ulcer -947, d $/wk -255)
- ZONE.MF1: ZONE5 zone no-trade set MF1 Skip within 30 pts (d ulcer -436, d $/wk +332)
- LOSS.MF2: CX1 context cut (fresh) at -24 pts (d ulcer -287, d $/wk -663)
- LOCK.MF2: LK3 lock at 50% -> stop to entry+20 pts (d ulcer -738, d $/wk -877)
- TAKE.MF2: TK6 take at 65% of target after 30 s without a new extreme (d ulcer -943, d $/wk -1115)
- ZONE.MF2: ZONE5 zone no-trade set MF2 Skip within 30 pts (d ulcer -374, d $/wk -160)
- LOSS.MF3: CU4 loss cut when unrealised <= -120 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF3: LK6 lock at 65% -> stop to entry+20 pts (d ulcer -1606, d $/wk -2052)
- TAKE.MF3: FR_TAKE6 W-FASTR pick: lock 80% -> +30 (d ulcer -1027, d $/wk -1857)
- ZONE.MF3: ZONE2 zone no-trade set MF3 Half within 30 pts (d ulcer -634, d $/wk -147)
- LOSS.MF4: CU4 loss cut when unrealised <= -45 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF4: LK8 lock at 80% -> stop to entry+10 pts (d ulcer +262, d $/wk -486, fails the guard: weak)
- TAKE.MF4: SHV2 target shave MF4 4 ticks (d ulcer -180, d $/wk +145)
- ZONE.MF4: ZONE4 zone no-trade set MF4 Skip within 20 pts (d ulcer -115, d $/wk -96)
- LOSS.MF5: CX1 context cut (fresh) at -12 pts (d ulcer -24, d $/wk -621)
- LOCK.MF5: LK7 lock at 80% -> stop to entry+0 pts (d ulcer -68, d $/wk +27)
- TAKE.MF5: FR_TAKE4 W-FASTR pick: lock 80% -> +10 (d ulcer -66, d $/wk -129)
- ZONE.MF5: ZONE4 zone no-trade set MF5 Skip within 20 pts (d ulcer -167, d $/wk +53)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +719, d $/wk -3267, fails the guard: weak)
- BL: BL7 BookLock arm 3.0R give-back 33% (d ulcer -1291, d $/wk +1374)
- CAP: CAP1 per-book day profit stop +5R ($12000) (d ulcer -1290, d $/wk +1475)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($9600) (d ulcer -1660, d $/wk +1778)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -3227, d $/wk -6560)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer -353, d $/wk -425)
- CG: CGB3 skip after 3 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer -980, d $/wk +858)
- DLA: DLA5 per-book day loss halt at -3R (open P&L counts, close the position, halt rest of session) (d ulcer -384, d $/wk -360)
- DLB: DLB14 stack day loss halt at -$8000 per lot per book (close positions, pause 60 min then re-arm) (d ulcer +315, d $/wk -2569, fails the guard: weak)
- DLC: DLC2 per-book halt after 3 consecutive full-stop losses (rest of session) (d ulcer -914, d $/wk +305)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -2757 / -2248 / -2867
- LOCK.MF1: -2166 / -3008 / -2676
- TAKE.MF1: -2151 / -2412 / -3285
- ZONE.MF1: -2450 / -2497 / -2913
- LOSS.MF2: -2530 / -2706 / -2627
- LOCK.MF2: -2430 / -2846 / -2584
- TAKE.MF2: -2494 / -2544 / -2823
- ZONE.MF2: -2740 / -2561 / -2570
- LOSS.MF3: -3057 / -3301 / -1524
- LOCK.MF3: -2684 / -2641 / -2544
- TAKE.MF3: -2516 / -2758 / -2588
- ZONE.MF3: -2459 / -2590 / -2811
- LOSS.MF4: -2708 / -3010 / -2151
- LOCK.MF4: -3143 / -2473 / -2269
- TAKE.MF4: -2504 / -2709 / -2648
- ZONE.MF4: -2567 / -2621 / -2676
- LOSS.MF5: -2738 / -2442 / -2691
- LOCK.MF5: -2334 / -2982 / -2539
- TAKE.MF5: -2285 / -2624 / -2945
- ZONE.MF5: -2640 / -2429 / -2797
- SC: -2738 / -2594 / -2538
- BL: -2119 / -2592 / -3136
- CAP: -2794 / -3084 / -1994
- STK: -2786 / -2846 / -2240
- SZW: -2695 / -3561 / -1613
- NTS: -2468 / -2775 / -2618
- CG: -2802 / -2560 / -2511
- DLA: -2685 / -2739 / -2444
- DLB: -2806 / -2873 / -2194
- DLC: -2659 / -2567 / -2642

