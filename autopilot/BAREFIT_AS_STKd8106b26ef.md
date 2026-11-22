# BAREFIT_AS_STKd8106b26ef - truly bare all-layers fit (W-LAYERS, 2026-11-22 20:45Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 1 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 3046 / -9450 / -4971 / -6578 / 10834 | 1827 / -5422 / -1892 / -5259 / 7645 |
| L3M | 3375 / -9283 / -1858 / -6578 / 10600 | 1715 / -5422 / -463 / -4244 / 6646 |
| 2023 | 5200 / -11178 / -7756 / -4718 / 1042 | 8030 / -15556 / -7772 / -7029 / 381 |
| 2024 | 4545 / -16311 / -8171 / -8853 / 1917 | 4558 / -12014 / -5882 / -4649 / 1290 |
| 2025 | 6567 / -17403 / -9888 / -11445 / 1982 | 13198 / -26467 / -12614 / -6812 / 762 |

Best joint combo TL3_SR_AS_STKd8106b26ef_BF1_JT57: {'LOCK.MF1': ['LK', 2], 'TAKE.MF1': ['TK', 10], 'ZONE.MF1': ['ZONE', 6], 'ZONE.MF2': ['ZONE', 1], 'LOSS.MF3': ['CU', 2], 'LOCK.MF3': ['LK', 2], 'TAKE.MF3': ['TK', 1], 'ZONE.MF3': ['ZONE', 5], 'LOSS.MF4': ['STC', 1], 'LOCK.MF4': ['LK', 1], 'TAKE.MF4': ['TK', 12], 'ZONE.MF4': ['ZONE', 2], 'ZONE.MF5': ['ZONE', 1], 'SC': ['SC', 1], 'BL': ['BL', 1], 'CAP': ['CAP', 6], 'STK': ['STK', 4], 'CG': ['CG', 2]}
Rolling walk-forward vs BARE among the combos 0.600 over 80 periods; fixed-pick persistence 0.581; year bands vs bare (equal-risk $/wk) RED/RED/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: STC4 state-cut cell MF1 mult 15.0 (d ulcer -6, d $/wk -55)
- LOCK.MF1: LK2 lock at 50% -> stop to entry+10 pts (d ulcer -286, d $/wk +345)
- TAKE.MF1: TK10 take at 95% of target after 5 s without a new extreme (d ulcer -66, d $/wk +309)
- ZONE.MF1: ZONE6 zone no-trade set MF1 Skip within 50 pts (d ulcer -360, d $/wk -786)
- LOSS.MF2: CU4 loss cut when unrealised <= -60 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF2: LK6 lock at 65% -> stop to entry+20 pts (d ulcer -148, d $/wk -126)
- TAKE.MF2: TK4 take at 65% of target after 5 s without a new extreme (d ulcer -56, d $/wk -46)
- ZONE.MF2: ZONE1 zone no-trade set MF2 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOSS.MF3: CU2 loss cut when unrealised <= -36 pts (0.6 x stop) (d ulcer -106, d $/wk -497)
- LOCK.MF3: LK2 lock at 50% -> stop to entry+10 pts (d ulcer +47, d $/wk -543, fails the guard: weak)
- TAKE.MF3: TK2 take at 50% of target after 15 s without a new extreme (d ulcer -23, d $/wk -522)
- ZONE.MF3: ZONE6 zone no-trade set MF3 Skip within 50 pts (d ulcer -75, d $/wk -424)
- LOSS.MF4: CU2 loss cut when unrealised <= -36 pts (0.6 x stop) (d ulcer -316, d $/wk +494)
- LOCK.MF4: LK2 lock at 50% -> stop to entry+10 pts (d ulcer -36, d $/wk -790)
- TAKE.MF4: TK1 take at 50% of target after 5 s without a new extreme (d ulcer -1, d $/wk -1551, fails the guard: weak)
- ZONE.MF4: ZONE1 zone no-trade set MF4 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOSS.MF5: CU4 loss cut when unrealised <= -30 pts (1.0 x stop) (d ulcer -0, d $/wk +1)
- LOCK.MF5: LK6 lock at 65% -> stop to entry+20 pts (d ulcer +372, d $/wk +161, fails the guard: weak)
- TAKE.MF5: NRT2 near-target latch MF5 X 0.95 stale 20 (d ulcer -310, d $/wk -1499)
- ZONE.MF5: ZONE1 zone no-trade set MF5 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +1700, d $/wk -1686, fails the guard: weak)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -1180, d $/wk -1290)
- CAP: CAP8 per-book day loss stop -6R ($7200) (d ulcer +0, d $/wk +0, fails the guard: weak)
- STK: STK3 WHOLE-STACK day profit stop +8R of one book ($9600) (d ulcer -0, d $/wk -545)
- CG: CG1 skip after 1 same-side losses (c_gov) (d ulcer +0, d $/wk +0, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -78 / 652 / 341
- LOCK.MF1: 239 / 337 / 350
- TAKE.MF1: -135 / 334 / 713
- ZONE.MF1: 933 / -364 / 383
- LOSS.MF2: 140 / 307 / 476
- LOCK.MF2: 249 / 425 / 254
- TAKE.MF2: 179 / 578 / 168
- ZONE.MF2: 387 / 281 / 264
- LOSS.MF3: 479 / 346 / 111
- LOCK.MF3: 286 / 380 / 263
- TAKE.MF3: 241 / 260 / 426
- ZONE.MF3: 352 / 211 / 368
- LOSS.MF4: 554 / 83 / 302
- LOCK.MF4: -9 / 682 / 245
- TAKE.MF4: 356 / 659 / -83
- ZONE.MF4: 263 / 153 / 512
- LOSS.MF5: 696 / 132 / 115
- LOCK.MF5: 230 / 326 / 371
- TAKE.MF5: 11 / 678 / 230
- ZONE.MF5: 266 / 266 / 396
- SC: -31 / 648 / 300
- BL: 744 / 9 / 192
- CAP: 226 / 387 / 314
- STK: 338 / 324 / 268
- CG: 293 / 251 / 385

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 3481 / -10508 / -9931 / -6608 / 10247 | 1367 / -4347 / -1830 / -3817 / 4925 |
| L3M | 3680 / -10508 / -3086 / -6608 / 10033 | 1006 / -3214 / 423 / -2338 / 4431 |
| 2023 | 5307 / -11253 / -7808 / -4738 / 1015 | 4844 / -9951 / -5467 / -4594 / 158 |
| 2024 | 5048 / -18731 / -10393 / -8930 / 1783 | 4450 / -12346 / -5401 / -3836 / 851 |
| 2025 | 6865 / -18734 / -11947 / -12080 / 1758 | 10979 / -24388 / -10670 / -5674 / 266 |

Best joint combo TL3_SR_AS_STKd8106b26ef_BF2_JT19: {'LOSS.MF1': ['CU', 4], 'TAKE.MF1': ['TK', 10], 'ZONE.MF1': ['ZONE', 6], 'LOSS.MF2': ['CU', 4], 'TAKE.MF2': ['NRT', 4], 'ZONE.MF2': ['ZONE', 1], 'LOCK.MF3': ['LK', 2], 'TAKE.MF3': ['TK', 1], 'LOSS.MF4': ['CU', 2], 'TAKE.MF4': ['NRT', 4], 'ZONE.MF4': ['ZONE', 3], 'LOCK.MF5': ['LK', 6], 'TAKE.MF5': ['NRT', 2], 'SC': ['SC', 1], 'BL': ['BL', 2], 'CAP': ['CAP', 8], 'SZW': ['SZW', 3], 'NTS': ['NTS', 2]}
Rolling walk-forward vs BARE among the combos 0.850 over 80 periods; fixed-pick persistence 0.817; year bands vs bare (equal-risk $/wk) RED/RED/RED; null: pending (1-lot screen null).

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
- CG: CG1 skip after 1 same-side losses (c_gov) (d ulcer +0, d $/wk +0, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -2392 / -2056 / -2083
- LOCK.MF1: -2048 / -2094 / -2376
- TAKE.MF1: -2217 / -2447 / -1860
- ZONE.MF1: -1986 / -1954 / -2575
- LOSS.MF2: -2247 / -2081 / -2197
- LOCK.MF2: -2380 / -1880 / -2270
- TAKE.MF2: -2005 / -2335 / -2176
- ZONE.MF2: -2035 / -2261 / -2221
- LOSS.MF3: -1970 / -2401 / -2144
- LOCK.MF3: -2059 / -2014 / -2445
- TAKE.MF3: -2259 / -1938 / -2328
- ZONE.MF3: -2193 / -2165 / -2165
- LOSS.MF4: -2038 / -2681 / -1798
- LOCK.MF4: -2757 / -1808 / -1978
- TAKE.MF4: -2206 / -2159 / -2159
- ZONE.MF4: -2331 / -2028 / -2169
- LOSS.MF5: -2003 / -2181 / -2332
- LOCK.MF5: -1976 / -2275 / -2264
- TAKE.MF5: -2572 / -1873 / -2092
- ZONE.MF5: -2494 / -1978 / -2062
- SC: -1824 / -2346 / -2339
- BL: -2035 / -2269 / -2213
- CAP: -2432 / -2239 / -1861
- STK: -2423 / -2182 / -1926
- SZW: -1266 / -2878 / -2344
- NTS: -2223 / -2501 / -1800
- CG: -2358 / -1755 / -2416

## 4 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 3922 / -13091 / -10215 / -8185 / 9653 | 1578 / -4578 / -2508 / -4376 / 5348 |
| L3M | 4215 / -13091 / -5657 / -6646 / 9824 | 1330 / -4208 / -2508 / -2859 / 4962 |
| 2023 | 5154 / -11587 / -6684 / -4763 / 969 | 4994 / -9741 / -5511 / -4948 / 199 |
| 2024 | 5231 / -19296 / -10562 / -9080 / 1668 | 4479 / -12147 / -5483 / -3964 / 936 |
| 2025 | 8145 / -22961 / -16183 / -11899 / 1317 | 9328 / -19470 / -9278 / -6117 / 519 |

Best joint combo TL3_SR_AS_STKd8106b26ef_BF4_JT1: {'LOSS.MF1': ['CU', 4], 'TAKE.MF1': ['SHV', 2], 'ZONE.MF1': ['ZONE', 5], 'LOCK.MF2': ['LK', 9], 'TAKE.MF2': ['NRT', 1], 'LOSS.MF3': ['CU', 2], 'LOCK.MF3': ['LK', 7], 'ZONE.MF3': ['ZONE', 6], 'LOSS.MF4': ['CU', 3], 'TAKE.MF4': ['NRT', 4], 'ZONE.MF4': ['ZONE', 3], 'LOCK.MF5': ['LK', 5], 'TAKE.MF5': ['TK', 8], 'SC': ['SC', 2], 'BL': ['BL', 2], 'STK': ['STK', 4], 'SZW': ['SZW', 2], 'CG': ['CG', 1]}
Rolling walk-forward vs BARE among the combos 0.912 over 80 periods; fixed-pick persistence 0.914; year bands vs bare (equal-risk $/wk) RED/RED/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU4 loss cut when unrealised <= -40 pts (1.0 x stop) (d ulcer -10, d $/wk +3)
- LOCK.MF1: LK5 lock at 65% -> stop to entry+10 pts (d ulcer -1228, d $/wk +1657)
- TAKE.MF1: SHV2 target shave MF1 4 ticks (d ulcer -953, d $/wk +897)
- ZONE.MF1: ZONE6 zone no-trade set MF1 Skip within 50 pts (d ulcer -2177, d $/wk -2702)
- LOSS.MF2: STC3 state-cut cell MF2 mult 5.0 (d ulcer -217, d $/wk -1396)
- LOCK.MF2: LK9 lock at 80% -> stop to entry+20 pts (d ulcer +62, d $/wk -304, fails the guard: weak)
- TAKE.MF2: NRT4 near-target latch MF2 X 0.95 givep 0.1 (d ulcer -480, d $/wk -241)
- ZONE.MF2: ZONE2 zone no-trade set MF2 Half within 30 pts (d ulcer -132, d $/wk -824)
- LOSS.MF3: CU2 loss cut when unrealised <= -36 pts (0.6 x stop) (d ulcer -451, d $/wk -1297)
- LOCK.MF3: LK9 lock at 80% -> stop to entry+20 pts (d ulcer +461, d $/wk -812, fails the guard: weak)
- TAKE.MF3: SHV1 target shave MF3 2 ticks (d ulcer +31, d $/wk -124, fails the guard: weak)
- ZONE.MF3: ZONE6 zone no-trade set MF3 Skip within 50 pts (d ulcer -260, d $/wk -1320)
- LOSS.MF4: CU2 loss cut when unrealised <= -36 pts (0.6 x stop) (d ulcer -1479, d $/wk +2058)
- LOCK.MF4: LK2 lock at 50% -> stop to entry+10 pts (d ulcer -512, d $/wk -3632)
- TAKE.MF4: NRT4 near-target latch MF4 X 0.95 givep 0.1 (d ulcer -579, d $/wk -695)
- ZONE.MF4: ZONE2 zone no-trade set MF4 Half within 30 pts (d ulcer -525, d $/wk -1264)
- LOSS.MF5: STC1 state-cut cell MF5 arm 30.0 (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF5: LK5 lock at 65% -> stop to entry+10 pts (d ulcer +1397, d $/wk +426, fails the guard: weak)
- TAKE.MF5: TK7 take at 80% of target after 5 s without a new extreme (d ulcer -1552, d $/wk -3303)
- ZONE.MF5: ZONE3 zone no-trade set MF5 Half within 50 pts (d ulcer -249, d $/wk -1039)
- SC: SC2 StackCut share 50% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots) (d ulcer -1874, d $/wk -1602)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -6720, d $/wk -2991)
- CAP: CAP5 per-book day loss stop -2R ($9600) (d ulcer -6, d $/wk -1879)
- STK: STK4 WHOLE-STACK day profit stop +12R of one book ($57600) (d ulcer +0, d $/wk -911, fails the guard: weak)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -7391, d $/wk -12203)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer -1101, d $/wk -1370)
- CG: CG1 skip after 1 same-side losses (c_gov) (d ulcer +0, d $/wk +0, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -6317 / -5788 / -6123
- LOCK.MF1: -5776 / -6186 / -6246
- TAKE.MF1: -5718 / -6262 / -6226
- ZONE.MF1: -5985 / -6349 / -5882
- LOSS.MF2: -6327 / -6387 / -5515
- LOCK.MF2: -6000 / -6462 / -5754
- TAKE.MF2: -6151 / -6140 / -5930
- ZONE.MF2: -5794 / -6740 / -5674
- LOSS.MF3: -5691 / -6723 / -5790
- LOCK.MF3: -5800 / -5940 / -6469
- TAKE.MF3: -5801 / -6451 / -5956
- ZONE.MF3: -6283 / -5844 / -6100
- LOSS.MF4: -5768 / -6484 / -5955
- LOCK.MF4: -6822 / -5647 / -5778
- TAKE.MF4: -6863 / -5601 / -5784
- ZONE.MF4: -5914 / -6119 / -6180
- LOSS.MF5: -6269 / -5856 / -6101
- LOCK.MF5: -5924 / -5986 / -6303
- TAKE.MF5: -6419 / -5684 / -6128
- ZONE.MF5: -6160 / -6272 / -5790
- SC: -6147 / -6081 / -5993
- BL: -5697 / -6571 / -5937
- CAP: -6265 / -6171 / -5790
- STK: -6266 / -5817 / -6142
- SZW: -4810 / -6734 / -6628
- NTS: -6031 / -6162 / -6024
- CG: -5898 / -6017 / -6297

