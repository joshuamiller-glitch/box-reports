# BAREFIT_NY_STKd8b76ecd35 - truly bare all-layers fit (W-LAYERS, 2026-11-23 11:06Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 1 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 4372 / -15007 / -14493 / -7608 / 7495 | 2102 / -7234 / -3161 / -4849 / 6035 |
| L3M | 3540 / -9765 / -3445 / -7157 / 6747 | 2029 / -5471 / -3138 / -4849 / 4502 |
| 2023 | 11117 / -31342 / -13132 / -12462 / 2016 | 9580 / -23783 / -10375 / -9895 / 1441 |
| 2024 | 10668 / -31020 / -19393 / -10792 / 2349 | 9067 / -28109 / -11458 / -9446 / 1459 |
| 2025 | 15583 / -59504 / -30226 / -17236 / 3561 | 14575 / -48045 / -20849 / -14932 / 1885 |

Best joint combo TL3_SR_NY_STKd8b76ecd35_BF1_JT22: {'LOSS.MF1': ['CU', 3], 'LOCK.MF1': ['LK', 1], 'TAKE.MF1': ['TK', 2], 'LOSS.MF2': ['CX', 3], 'TAKE.MF2': ['TK', 6], 'LOSS.MF3': ['CU', 4], 'LOCK.MF3': ['LK', 5], 'TAKE.MF3': ['FR_TAKE', 6], 'ZONE.MF3': ['ZONE', 2], 'TAKE.MF4': ['SHV', 2], 'ZONE.MF4': ['ZONE', 5], 'LOSS.MF5': ['STC', 3], 'LOCK.MF5': ['LK', 8], 'ZONE.MF5': ['ZONE', 6], 'BL': ['BL', 1], 'CAP': ['CAP', 2], 'DLA': ['DLA', 5], 'DLC': ['DLC', 2]}
Rolling walk-forward vs BARE among the combos 0.628 over 78 periods; fixed-pick persistence 0.645; year bands vs bare (equal-risk $/wk) AMBER/AMBER/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU3 loss cut when unrealised <= -72 pts (0.8 x stop) (d ulcer -342, d $/wk +155)
- LOCK.MF1: LK1 lock at 50% -> stop to entry+0 pts (d ulcer -545, d $/wk -718)
- TAKE.MF1: TK1 take at 50% of target after 5 s without a new extreme (d ulcer -391, d $/wk -285)
- ZONE.MF1: ZONE5 zone no-trade set MF1 Skip within 30 pts (d ulcer -235, d $/wk +166)
- LOSS.MF2: CX1 context cut (fresh) at -24 pts (d ulcer -167, d $/wk -332)
- LOCK.MF2: LK3 lock at 50% -> stop to entry+20 pts (d ulcer -472, d $/wk -395)
- TAKE.MF2: TK6 take at 65% of target after 30 s without a new extreme (d ulcer -540, d $/wk -680)
- ZONE.MF2: ZONE5 zone no-trade set MF2 Skip within 30 pts (d ulcer -157, d $/wk -124)
- LOSS.MF3: CU4 loss cut when unrealised <= -120 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF3: LK6 lock at 65% -> stop to entry+20 pts (d ulcer -802, d $/wk -1159)
- TAKE.MF3: FR_TAKE6 W-FASTR pick: lock 80% -> +30 (d ulcer -535, d $/wk -925)
- ZONE.MF3: ZONE1 zone no-trade set MF3 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOSS.MF4: CX2 context cut (fresh) at -27 pts (d ulcer -19, d $/wk -282)
- LOCK.MF4: LK8 lock at 80% -> stop to entry+10 pts (d ulcer +139, d $/wk -241, fails the guard: weak)
- TAKE.MF4: SHV2 target shave MF4 4 ticks (d ulcer -64, d $/wk +72)
- ZONE.MF4: ZONE4 zone no-trade set MF4 Skip within 20 pts (d ulcer -60, d $/wk -48)
- LOSS.MF5: STC3 state-cut cell MF5 mult 5.0 (d ulcer -45, d $/wk -58)
- LOCK.MF5: LK9 lock at 80% -> stop to entry+20 pts (d ulcer -50, d $/wk +12)
- TAKE.MF5: FR_TAKE6 W-FASTR pick: lock 80% -> +30 (d ulcer -67, d $/wk +21)
- ZONE.MF5: ZONE4 zone no-trade set MF5 Skip within 20 pts (d ulcer -89, d $/wk +26)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +1393, d $/wk -2015, fails the guard: weak)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -619, d $/wk -364)
- CAP: CAP1 per-book day profit stop +5R ($6000) (d ulcer -475, d $/wk +692)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($4800) (d ulcer -688, d $/wk +622)
- DLA: DLA5 per-book day loss halt at -3R (open P&L counts, close the position, halt rest of session) (d ulcer -125, d $/wk -216)
- DLB: DLB11 stack day loss halt at -$8000 per lot per book (new entries only, open positions run, rest of session) (d ulcer +107, d $/wk -317, fails the guard: weak)
- DLC: DLC2 per-book halt after 3 consecutive full-stop losses (rest of session) (d ulcer -335, d $/wk +104)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -343 / -424 / -110
- LOCK.MF1: -356 / -342 / -179
- TAKE.MF1: -104 / -228 / -536
- ZONE.MF1: -6 / -387 / -471
- LOSS.MF2: -209 / -299 / -364
- LOCK.MF2: 45 / -601 / -306
- TAKE.MF2: -223 / -293 / -357
- ZONE.MF2: -172 / -451 / -248
- LOSS.MF3: -704 / -754 / 567
- LOCK.MF3: -284 / -254 / -336
- TAKE.MF3: -152 / -442 / -276
- ZONE.MF3: -367 / -182 / -329
- LOSS.MF4: -308 / -296 / -272
- LOCK.MF4: -360 / -234 / -284
- TAKE.MF4: -228 / -387 / -258
- ZONE.MF4: -260 / -379 / -235
- LOSS.MF5: -287 / -381 / -206
- LOCK.MF5: -233 / -354 / -286
- TAKE.MF5: -469 / -118 / -295
- ZONE.MF5: -158 / -371 / -342
- SC: -1131 / 188 / 37
- BL: -123 / -387 / -359
- CAP: -199 / -329 / -344
- STK: -287 / -266 / -323
- DLA: -368 / -254 / -256
- DLB: -415 / -215 / -249
- DLC: -231 / -239 / -403

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 4610 / -17430 / -16945 / -7910 / 7061 | 1760 / -5109 / -2275 / -2752 / 3038 |
| L3M | 3635 / -9728 / -3473 / -7119 / 6339 | 2091 / -5109 / -2275 / -2752 / 2014 |
| 2023 | 11154 / -31407 / -13155 / -12475 / 1954 | 7525 / -20192 / -8146 / -5447 / 869 |
| 2024 | 11309 / -32917 / -19403 / -10812 / 2270 | 4335 / -11167 / -7074 / -4246 / 1266 |
| 2025 | 15615 / -59614 / -30363 / -17271 / 3476 | 7395 / -26262 / -12856 / -9596 / 1686 |

Best joint combo TL3_SR_NY_STKd8b76ecd35_BF2_JT68: {'LOSS.MF1': ['CU', 2], 'LOCK.MF1': ['LK', 1], 'ZONE.MF1': ['ZONE', 6], 'LOSS.MF2': ['CX', 1], 'TAKE.MF2': ['TK', 1], 'ZONE.MF2': ['ZONE', 2], 'LOSS.MF3': ['CU', 4], 'ZONE.MF3': ['ZONE', 3], 'LOSS.MF4': ['CU', 4], 'LOCK.MF4': ['LK', 7], 'TAKE.MF4': ['SHV', 2], 'LOCK.MF5': ['LK', 8], 'TAKE.MF5': ['FR_TAKE', 4], 'ZONE.MF5': ['ZONE', 4], 'BL': ['BL', 1], 'STK': ['STK', 3], 'SZW': ['SZW', 3], 'NTS': ['NTS', 1], 'DLB': ['DLB', 6], 'DLC': ['DLC', 10]}
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
- DLA: DLA5 per-book day loss halt at -3R (open P&L counts, close the position, halt rest of session) (d ulcer -384, d $/wk -360)
- DLB: DLB14 stack day loss halt at -$8000 per lot per book (close positions, pause 60 min then re-arm) (d ulcer +315, d $/wk -2569, fails the guard: weak)
- DLC: DLC2 per-book halt after 3 consecutive full-stop losses (rest of session) (d ulcer -914, d $/wk +305)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -2753 / -2542 / -3008
- LOCK.MF1: -2211 / -3171 / -2900
- TAKE.MF1: -2563 / -2481 / -3251
- ZONE.MF1: -2705 / -2719 / -2877
- LOSS.MF2: -2771 / -2569 / -2962
- LOCK.MF2: -2609 / -3026 / -2662
- TAKE.MF2: -2541 / -2751 / -3003
- ZONE.MF2: -2888 / -2569 / -2851
- LOSS.MF3: -3149 / -3267 / -1901
- LOCK.MF3: -2864 / -2774 / -2669
- TAKE.MF3: -2739 / -2848 / -2716
- ZONE.MF3: -2372 / -2914 / -3002
- LOSS.MF4: -2801 / -2984 / -2519
- LOCK.MF4: -3350 / -2533 / -2442
- TAKE.MF4: -2758 / -2813 / -2732
- ZONE.MF4: -2639 / -2772 / -2888
- LOSS.MF5: -3017 / -2620 / -2676
- LOCK.MF5: -2660 / -2888 / -2751
- TAKE.MF5: -2524 / -2832 / -2937
- ZONE.MF5: -2838 / -2537 / -2931
- SC: -3006 / -2598 / -2707
- BL: -2423 / -2605 / -3262
- CAP: -2750 / -3282 / -2271
- STK: -2889 / -2968 / -2451
- SZW: -2942 / -3685 / -1683
- NTS: -2700 / -2839 / -2762
- DLA: -2922 / -2658 / -2729
- DLB: -2785 / -2879 / -2639
- DLC: -2721 / -2899 / -2681

## 4 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 4889 / -19461 / -17056 / -8001 / 6433 | 1733 / -6632 / -3040 / -3267 / 2532 |
| L3M | 3663 / -9796 / -3618 / -7169 / 6269 | 1752 / -4667 / -3040 / -3267 / 1925 |
| 2023 | 11176 / -31494 / -13161 / -12437 / 1911 | 11959 / -29961 / -8381 / -4380 / 572 |
| 2024 | 11708 / -33452 / -19500 / -10999 / 2082 | 3862 / -11795 / -6297 / -4249 / 1447 |
| 2025 | 15774 / -59782 / -30496 / -17249 / 3266 | 7685 / -23403 / -10215 / -7279 / 1457 |

Best joint combo TL3_SR_NY_STKd8b76ecd35_BF4_JT15: {'LOCK.MF1': ['LK', 2], 'TAKE.MF1': ['SHV', 1], 'ZONE.MF1': ['ZONE', 6], 'LOSS.MF2': ['CX', 1], 'LOCK.MF2': ['LK', 6], 'TAKE.MF2': ['TK', 6], 'TAKE.MF3': ['FR_TAKE', 6], 'ZONE.MF3': ['ZONE', 3], 'LOSS.MF4': ['STC', 2], 'LOSS.MF5': ['STC', 1], 'LOCK.MF5': ['LK', 8], 'TAKE.MF5': ['SHV', 2], 'ZONE.MF5': ['ZONE', 4], 'SC': ['SC', 2], 'BL': ['BL', 7], 'CAP': ['CAP', 1], 'STK': ['STK', 1], 'SZW': ['SZW', 3], 'DLC': ['DLC', 10]}
Rolling walk-forward vs BARE among the combos 0.838 over 80 periods; fixed-pick persistence 0.882; year bands vs bare (equal-risk $/wk) RED/GREEN/GREEN; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU3 loss cut when unrealised <= -72 pts (0.8 x stop) (d ulcer -1756, d $/wk +785)
- LOCK.MF1: LK1 lock at 50% -> stop to entry+0 pts (d ulcer -1839, d $/wk -3130)
- TAKE.MF1: TK1 take at 50% of target after 5 s without a new extreme (d ulcer -2527, d $/wk -235)
- ZONE.MF1: ZONE5 zone no-trade set MF1 Skip within 30 pts (d ulcer -1028, d $/wk +673)
- LOSS.MF2: CX1 context cut (fresh) at -24 pts (d ulcer -1458, d $/wk -1315)
- LOCK.MF2: LK6 lock at 65% -> stop to entry+20 pts (d ulcer -1523, d $/wk -1314)
- TAKE.MF2: TK6 take at 65% of target after 30 s without a new extreme (d ulcer -1776, d $/wk -2661)
- ZONE.MF2: ZONE5 zone no-trade set MF2 Skip within 30 pts (d ulcer -802, d $/wk -323)
- LOSS.MF3: CU4 loss cut when unrealised <= -120 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF3: LK6 lock at 65% -> stop to entry+20 pts (d ulcer -2861, d $/wk -3371)
- TAKE.MF3: FR_TAKE5 W-FASTR pick: lock 80% -> +20 (d ulcer -760, d $/wk -4468)
- ZONE.MF3: ZONE2 zone no-trade set MF3 Half within 30 pts (d ulcer -1365, d $/wk -288)
- LOSS.MF4: CU4 loss cut when unrealised <= -45 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF4: LK7 lock at 80% -> stop to entry+0 pts (d ulcer +506, d $/wk -827, fails the guard: weak)
- TAKE.MF4: SHV3 target shave MF4 8 ticks (d ulcer -227, d $/wk +383)
- ZONE.MF4: ZONE4 zone no-trade set MF4 Skip within 20 pts (d ulcer -218, d $/wk -189)
- LOSS.MF5: CU4 loss cut when unrealised <= -30 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF5: LK7 lock at 80% -> stop to entry+0 pts (d ulcer -30, d $/wk -16)
- TAKE.MF5: SHV1 target shave MF5 2 ticks (d ulcer +0, d $/wk +79, fails the guard: weak)
- ZONE.MF5: ZONE4 zone no-trade set MF5 Skip within 20 pts (d ulcer -338, d $/wk +101)
- SC: SC2 StackCut share 50% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots) (d ulcer +65, d $/wk -5814, fails the guard: weak)
- BL: BL7 BookLock arm 3.0R give-back 33% (d ulcer -3127, d $/wk +2771)
- CAP: CAP1 per-book day profit stop +5R ($24000) (d ulcer -3371, d $/wk +3315)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($19200) (d ulcer -3362, d $/wk +2221)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -6339, d $/wk -11166)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer -686, d $/wk -844)
- DLA: DLA5 per-book day loss halt at -3R (open P&L counts, close the position, halt rest of session) (d ulcer -1378, d $/wk -620)
- DLB: DLB17 stack day loss halt at -$8000 per lot per book (close positions, pause 120 min then re-arm) (d ulcer +2171, d $/wk -7260, fails the guard: weak)
- DLC: DLC2 per-book halt after 3 consecutive full-stop losses (rest of session) (d ulcer -2454, d $/wk +624)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -7977 / -7229 / -7105
- LOCK.MF1: -7028 / -7840 / -7408
- TAKE.MF1: -7002 / -7316 / -7957
- ZONE.MF1: -6261 / -8112 / -7875
- LOSS.MF2: -8005 / -6601 / -7706
- LOCK.MF2: -7457 / -7565 / -7269
- TAKE.MF2: -6997 / -8125 / -7153
- ZONE.MF2: -7025 / -7756 / -7495
- LOSS.MF3: -8672 / -8214 / -5451
- LOCK.MF3: -7567 / -7274 / -7454
- TAKE.MF3: -7800 / -7518 / -6987
- ZONE.MF3: -7084 / -7336 / -7858
- LOSS.MF4: -7165 / -7671 / -7445
- LOCK.MF4: -8518 / -7026 / -6787
- TAKE.MF4: -7267 / -7666 / -7352
- ZONE.MF4: -7308 / -7486 / -7493
- LOSS.MF5: -7621 / -7474 / -7203
- LOCK.MF5: -7519 / -7419 / -7357
- TAKE.MF5: -7219 / -7285 / -7779
- ZONE.MF5: -7233 / -7626 / -7425
- SC: -7204 / -7088 / -7991
- BL: -7207 / -7658 / -7418
- CAP: -7431 / -7396 / -7464
- STK: -7365 / -8201 / -6723
- SZW: -6017 / -9833 / -6388
- NTS: -7655 / -7372 / -7272
- DLA: -7517 / -7891 / -6886
- DLB: -7630 / -7082 / -7586
- DLC: -7097 / -7697 / -7485

