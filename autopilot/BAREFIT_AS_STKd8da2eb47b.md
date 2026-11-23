# BAREFIT_AS_STKd8da2eb47b - truly bare all-layers fit (W-LAYERS, 2026-11-23 04:34Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 1 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 2581 / -8577 / -5079 / -6093 / 7468 | 1348 / -5979 / -2100 / -5087 / 6199 |
| L3M | 2875 / -8526 / 1248 / -5933 / 6327 | 1614 / -5979 / -2100 / -5087 / 4671 |
| 2023 | 2825 / -6313 / -3586 / -2849 / 931 | 4231 / -9777 / -3212 / -2211 / 514 |
| 2024 | 5723 / -15575 / -7296 / -5368 / 1234 | 6046 / -13166 / -9354 / -6112 / 799 |
| 2025 | 5950 / -14678 / -9221 / -7158 / 1441 | 4949 / -14618 / -11897 / -8197 / 460 |

Best joint combo TL3_SR_AS_STKd8da2eb47b_BF1_JT76: {'LOSS.MF1': ['STC', 2], 'LOCK.MF1': ['LK', 2], 'TAKE.MF1': ['FR_TAKE', 1], 'LOSS.MF2': ['STC', 4], 'TAKE.MF2': ['TK', 4], 'LOSS.MF3': ['CX', 1], 'LOCK.MF3': ['LK', 2], 'TAKE.MF3': ['TK', 2], 'ZONE.MF3': ['ZONE', 1], 'LOCK.MF4': ['LK', 4], 'ZONE.MF4': ['ZONE', 1], 'BL': ['BL', 1], 'CAP': ['CAP', 2], 'STK': ['STK', 3]}
Rolling walk-forward vs BARE among the combos 0.562 over 73 periods; fixed-pick persistence 0.505; year bands vs bare (equal-risk $/wk) RED/RED/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: STC2 state-cut cell MF1 arm 60.0 (d ulcer -78, d $/wk -171)
- LOCK.MF1: LK2 lock at 50% -> stop to entry+10 pts (d ulcer -303, d $/wk +345)
- TAKE.MF1: TK3 take at 50% of target after 30 s without a new extreme (d ulcer -66, d $/wk -577)
- ZONE.MF1: ZONE6 zone no-trade set MF1 Skip within 50 pts (d ulcer -196, d $/wk -786)
- LOSS.MF2: STC2 state-cut cell MF2 arm 60.0 (d ulcer -9, d $/wk -276)
- LOCK.MF2: LK5 lock at 65% -> stop to entry+10 pts (d ulcer +49, d $/wk +75, fails the guard: weak)
- TAKE.MF2: TK4 take at 65% of target after 5 s without a new extreme (d ulcer -60, d $/wk -46)
- ZONE.MF2: ZONE4 zone no-trade set MF2 Skip within 20 pts (d ulcer -18, d $/wk -202)
- LOSS.MF3: CX1 context cut (fresh) at -18 pts (d ulcer -184, d $/wk +432)
- LOCK.MF3: LK3 lock at 50% -> stop to entry+20 pts (d ulcer -396, d $/wk -166)
- TAKE.MF3: TK2 take at 50% of target after 15 s without a new extreme (d ulcer -410, d $/wk +53)
- ZONE.MF3: ZONE4 zone no-trade set MF3 Skip within 20 pts (d ulcer -9, d $/wk -169, fails the guard: weak)
- LOSS.MF4: CU3 loss cut when unrealised <= -24 pts (0.8 x stop) (d ulcer -35, d $/wk -184)
- LOCK.MF4: LK1 lock at 50% -> stop to entry+0 pts (d ulcer -20, d $/wk -277)
- TAKE.MF4: SHV3 target shave MF4 8 ticks (d ulcer -110, d $/wk +31)
- ZONE.MF4: ZONE1 zone no-trade set MF4 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +677, d $/wk -143, fails the guard: weak)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -709, d $/wk -857)
- CAP: CAP1 per-book day profit stop +5R ($4250) (d ulcer -164, d $/wk -326, fails the guard: weak)
- STK: STK3 WHOLE-STACK day profit stop +8R of one book ($6800) (d ulcer -3, d $/wk -304)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -70 / -358 / -264
- LOCK.MF1: -135 / -140 / -420
- TAKE.MF1: -437 / -105 / -164
- ZONE.MF1: -391 / 168 / -481
- LOSS.MF2: -255 / -3 / -441
- LOCK.MF2: -274 / -82 / -343
- TAKE.MF2: -383 / -254 / -67
- ZONE.MF2: -237 / -235 / -226
- LOSS.MF3: -253 / -440 / -6
- LOCK.MF3: -193 / -385 / -120
- TAKE.MF3: -169 / -383 / -144
- ZONE.MF3: -138 / -344 / -213
- LOSS.MF4: -155 / -179 / -362
- LOCK.MF4: -213 / -171 / -314
- TAKE.MF4: -208 / -207 / -282
- ZONE.MF4: -86 / -219 / -388
- SC: -607 / -60 / -45
- BL: -73 / -465 / -155
- CAP: -302 / -247 / -151
- STK: -9 / -370 / -311

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 2943 / -10556 / -5111 / -6858 / 7217 | 971 / -3705 / -1766 / -3161 / 4399 |
| L3M | 3470 / -10556 / 456 / -6858 / 6037 | 1019 / -3441 / -1402 / -2764 / 3498 |
| 2023 | 2891 / -6436 / -3636 / -2866 / 902 | 6070 / -9576 / -2740 / -2337 / 5 |
| 2024 | 5836 / -15782 / -7343 / -5391 / 1187 | 3943 / -10783 / -4168 / -2777 / 733 |
| 2025 | 6236 / -16098 / -10547 / -7190 / 1285 | 4728 / -12760 / -11319 / -3674 / 619 |

Best joint combo TL3_SR_AS_STKd8da2eb47b_BF2_JT32: {'LOSS.MF1': ['STC', 2], 'LOCK.MF1': ['LK', 2], 'ZONE.MF1': ['ZONE', 5], 'LOCK.MF2': ['LK', 7], 'TAKE.MF2': ['TK', 11], 'ZONE.MF2': ['ZONE', 2], 'LOCK.MF3': ['LK', 2], 'TAKE.MF3': ['TK', 3], 'ZONE.MF3': ['ZONE', 4], 'LOCK.MF4': ['LK', 6], 'ZONE.MF4': ['ZONE', 4], 'SC': ['SC', 1], 'BL': ['BL', 1], 'SZW': ['SZW', 2], 'NTS': ['NTS', 1]}
Rolling walk-forward vs BARE among the combos 0.887 over 80 periods; fixed-pick persistence 0.796; year bands vs bare (equal-risk $/wk) RED/GREEN/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU4 loss cut when unrealised <= -40 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF1: LK2 lock at 50% -> stop to entry+10 pts (d ulcer -754, d $/wk +480)
- TAKE.MF1: FR_TAKE4 W-FASTR pick: lock 80% -> +10 (d ulcer -217, d $/wk -143)
- ZONE.MF1: ZONE3 zone no-trade set MF1 Half within 50 pts (d ulcer -913, d $/wk -688)
- LOSS.MF2: CU4 loss cut when unrealised <= -60 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF2: LK9 lock at 80% -> stop to entry+20 pts (d ulcer +314, d $/wk +66, fails the guard: weak)
- TAKE.MF2: TK11 take at 95% of target after 15 s without a new extreme (d ulcer -5, d $/wk -99)
- ZONE.MF2: ZONE2 zone no-trade set MF2 Half within 30 pts (d ulcer -151, d $/wk -416)
- LOSS.MF3: CX1 context cut (fresh) at -18 pts (d ulcer -540, d $/wk +943)
- LOCK.MF3: LK3 lock at 50% -> stop to entry+20 pts (d ulcer -821, d $/wk -472)
- TAKE.MF3: TK2 take at 50% of target after 15 s without a new extreme (d ulcer -1023, d $/wk -3)
- ZONE.MF3: ZONE4 zone no-trade set MF3 Skip within 20 pts (d ulcer -112, d $/wk -395)
- LOSS.MF4: CU3 loss cut when unrealised <= -24 pts (0.8 x stop) (d ulcer -48, d $/wk -360)
- LOCK.MF4: LK6 lock at 65% -> stop to entry+20 pts (d ulcer -25, d $/wk -108)
- TAKE.MF4: SHV3 target shave MF4 8 ticks (d ulcer -222, d $/wk +64)
- ZONE.MF4: ZONE1 zone no-trade set MF4 Half within 10 pts (d ulcer +3, d $/wk -74, fails the guard: weak)
- SC: SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +1040, d $/wk -213, fails the guard: weak)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -1809, d $/wk -1992)
- CAP: CAP1 per-book day profit stop +5R ($8500) (d ulcer -437, d $/wk -650)
- STK: STK8 WHOLE-STACK day loss stop -8R of one book ($13600) (d ulcer -155, d $/wk -5)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -2526, d $/wk -5044)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer -141, d $/wk -818)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -2762 / -3017 / -3037
- LOCK.MF1: -2689 / -3220 / -2905
- TAKE.MF1: -2921 / -2810 / -3091
- ZONE.MF1: -2902 / -2954 / -2965
- LOSS.MF2: -2968 / -2902 / -2953
- LOCK.MF2: -2810 / -2928 / -3080
- TAKE.MF2: -3040 / -2890 / -2897
- ZONE.MF2: -2982 / -2967 / -2875
- LOSS.MF3: -2956 / -2990 / -2877
- LOCK.MF3: -2949 / -2954 / -2920
- TAKE.MF3: -2842 / -2945 / -3032
- ZONE.MF3: -3001 / -2873 / -2950
- LOSS.MF4: -2988 / -2910 / -2927
- LOCK.MF4: -3047 / -2920 / -2859
- TAKE.MF4: -2898 / -2991 / -2932
- ZONE.MF4: -2998 / -2988 / -2838
- SC: -2912 / -2822 / -3087
- BL: -2758 / -3084 / -2974
- CAP: -2961 / -2875 / -2988
- STK: -2981 / -2846 / -2997
- SZW: -2321 / -3287 / -3192
- NTS: -2899 / -2937 / -2985

## 4 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 3528 / -12811 / -5197 / -6869 / 6833 | 971 / -4295 / -3030 / -3030 / 3874 |
| L3M | 4276 / -12811 / -2061 / -6869 / 5619 | 912 / -3689 / 665 / -2658 / 3276 |
| 2023 | 3092 / -6915 / -3711 / -2874 / 835 | 2743 / -6545 / -2235 / -1536 / 147 |
| 2024 | 5984 / -15661 / -7363 / -5342 / 1188 | 4389 / -10183 / -4345 / -2743 / 532 |
| 2025 | 6848 / -19438 / -14661 / -7174 / 1077 | 4281 / -11911 / -9453 / -3881 / 329 |

Best joint combo TL3_SR_AS_STKd8da2eb47b_BF4_JT6: {'LOCK.MF1': ['LK', 1], 'TAKE.MF1': ['SHV', 3], 'ZONE.MF1': ['ZONE', 5], 'ZONE.MF2': ['ZONE', 2], 'LOSS.MF3': ['CX', 2], 'LOCK.MF3': ['LK', 5], 'TAKE.MF3': ['TK', 2], 'ZONE.MF3': ['ZONE', 4], 'LOSS.MF4': ['CU', 3], 'SC': ['SC', 2], 'BL': ['BL', 3], 'CAP': ['CAP', 2], 'STK': ['STK', 8], 'SZW': ['SZW', 3], 'NTS': ['NTS', 1]}
Rolling walk-forward vs BARE among the combos 0.863 over 80 periods; fixed-pick persistence 0.871; year bands vs bare (equal-risk $/wk) RED/RED/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: STC1 state-cut cell MF1 arm 30.0 (d ulcer -566, d $/wk -700)
- LOCK.MF1: LK2 lock at 50% -> stop to entry+10 pts (d ulcer -2637, d $/wk +1647)
- TAKE.MF1: SHV2 target shave MF1 4 ticks (d ulcer -1561, d $/wk +897)
- ZONE.MF1: ZONE6 zone no-trade set MF1 Skip within 50 pts (d ulcer -3239, d $/wk -2702)
- LOSS.MF2: STC1 state-cut cell MF2 arm 30.0 (d ulcer -490, d $/wk -965)
- LOCK.MF2: LK5 lock at 65% -> stop to entry+10 pts (d ulcer +1109, d $/wk -117, fails the guard: weak)
- TAKE.MF2: SHV1 target shave MF2 2 ticks (d ulcer +37, d $/wk -126, fails the guard: weak)
- ZONE.MF2: ZONE5 zone no-trade set MF2 Skip within 30 pts (d ulcer -801, d $/wk -2040)
- LOSS.MF3: CX1 context cut (fresh) at -18 pts (d ulcer -1181, d $/wk +1650)
- LOCK.MF3: LK3 lock at 50% -> stop to entry+20 pts (d ulcer -1730, d $/wk -829)
- TAKE.MF3: TK2 take at 50% of target after 15 s without a new extreme (d ulcer -2001, d $/wk -506)
- ZONE.MF3: ZONE4 zone no-trade set MF3 Skip within 20 pts (d ulcer -572, d $/wk -774, fails the guard: weak)
- LOSS.MF4: CU3 loss cut when unrealised <= -24 pts (0.8 x stop) (d ulcer -58, d $/wk -1042)
- LOCK.MF4: LK4 lock at 65% -> stop to entry+0 pts (d ulcer +76, d $/wk -927, fails the guard: weak)
- TAKE.MF4: SHV3 target shave MF4 8 ticks (d ulcer -439, d $/wk +215)
- ZONE.MF4: ZONE1 zone no-trade set MF4 Half within 10 pts (d ulcer -25, d $/wk -145)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots) (d ulcer +809, d $/wk -788, fails the guard: weak)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -5785, d $/wk -3175)
- CAP: CAP1 per-book day profit stop +5R ($17000) (d ulcer -1531, d $/wk -1307)
- STK: STK8 WHOLE-STACK day loss stop -8R of one book ($27200) (d ulcer -716, d $/wk -4)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -6129, d $/wk -9417)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer -844, d $/wk -1334, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -6387 / -7213 / -7627
- LOCK.MF1: -6048 / -7319 / -7847
- TAKE.MF1: -6763 / -6691 / -7787
- ZONE.MF1: -7419 / -6641 / -7204
- LOSS.MF2: -7324 / -6581 / -7357
- LOCK.MF2: -7523 / -6398 / -7348
- TAKE.MF2: -7355 / -6776 / -7132
- ZONE.MF2: -7329 / -6923 / -7009
- LOSS.MF3: -7273 / -7234 / -6753
- LOCK.MF3: -6899 / -7956 / -6390
- TAKE.MF3: -6517 / -7814 / -6901
- ZONE.MF3: -6932 / -7212 / -7103
- LOSS.MF4: -6707 / -7342 / -7190
- LOCK.MF4: -7449 / -6864 / -6954
- TAKE.MF4: -7167 / -6862 / -7227
- ZONE.MF4: -7520 / -6882 / -6867
- SC: -7260 / -7231 / -6769
- BL: -6970 / -7377 / -6902
- CAP: -7454 / -6905 / -6908
- STK: -6790 / -6973 / -7479
- SZW: -5132 / -8331 / -7717
- NTS: -6696 / -7269 / -7273

