# BAREFIT_LO_L19201dfc_R0BRF90_30 - truly bare all-layers fit (W-LAYERS, 2026-11-23 13:48Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 1 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 1253 / -3809 / -2673 / -3310 / 1768 | 1069 / -3909 / -2065 / -2331 / 1614 |
| L3M | 1390 / -3402 / -2449 / -3310 / 1643 | 1262 / -3909 / -2065 / -2331 / 1343 |
| 2023 | 1935 / -5238 / -2549 / -1800 / 273 | 1684 / -5004 / -2549 / -1800 / 302 |
| 2024 | 4315 / -11780 / -5793 / -4164 / 261 | 5484 / -12661 / -5204 / -3575 / 102 |
| 2025 | 5068 / -12803 / -4448 / -3005 / 183 | 5563 / -13055 / -4973 / -3819 / 148 |

Best joint combo TL3_SR_LO_L19201dfc_R0BRF90_30_BF1_JT1: {'LOSS.MF1': ['STC', 4], 'TAKE.MF1': ['NRT', 1], 'ZONE.MF1': ['ZONE', 6], 'BL': ['BL', 1], 'CAP': ['CAP', 2], 'CG': ['CGB', 2], 'DLA': ['DLA', 4], 'DLC': ['DLC', 1]}
Rolling walk-forward vs BARE among the combos 0.610 over 77 periods; fixed-pick persistence 0.527; year bands vs bare (equal-risk $/wk) GREEN/RED/AMBER; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: STC4 state-cut cell MF1 mult 15.0 (d ulcer -31, d $/wk +82)
- LOCK.MF1: LK3 lock at 50% -> stop to entry+20 pts (d ulcer +297, d $/wk -893, fails the guard: weak)
- TAKE.MF1: NRT1 near-target latch MF1 X 0.90 stale 10 (d ulcer +0, d $/wk +0, fails the guard: weak)
- ZONE.MF1: ZONE5 zone no-trade set MF1 Skip within 30 pts (d ulcer -98, d $/wk -160)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, d $/wk +0, fails the guard: weak)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer +0, d $/wk -14, fails the guard: weak)
- CAP: CAP1 per-book day profit stop +5R ($9000) (d ulcer +0, d $/wk +0, fails the guard: weak)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($7200) (d ulcer +0, d $/wk +0, fails the guard: weak)
- CG: CGB2 skip after 2 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLA: DLA3 per-book day loss halt at -2R (open P&L counts, close the position, halt rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLB: DLB3 stack day loss halt at -$4000 per lot per book (open P&L counts, all books halted, positions closed, rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLC: DLC1 per-book halt after 2 consecutive full-stop losses (rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: 367 / -46 / 344
- LOCK.MF1: -106 / 516 / 203
- TAKE.MF1: 304 / 315 / 39
- ZONE.MF1: 138 / 237 / 265
- SC: 234 / 208 / 208
- BL: 234 / 208 / 208
- CAP: 234 / 208 / 208
- STK: 234 / 208 / 208
- CG: 234 / 208 / 208
- DLA: 234 / 208 / 208
- DLB: 234 / 208 / 208
- DLC: 234 / 208 / 208

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 1329 / -3918 / -2685 / -3315 / 1632 | 883 / -2548 / -1708 / -1437 / 563 |
| L3M | 1528 / -3918 / -2452 / -3315 / 1368 | 764 / -2212 / -1164 / -1337 / 702 |
| 2023 | 1943 / -5248 / -2559 / -1800 / 269 | 1339 / -2628 / -1849 / -1285 / 143 |
| 2024 | 4346 / -11822 / -5813 / -4176 / 257 | 2757 / -5279 / -3942 / -1904 / 42 |
| 2025 | 5379 / -12905 / -4508 / -3012 / 161 | 5422 / -8982 / -3597 / -2718 / 34 |

Best joint combo TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_JT14: {'LOSS.MF1': ['STC', 4], 'LOCK.MF1': ['LK', 3], 'ZONE.MF1': ['ZONE', 3], 'SC': ['SC', 1], 'CAP': ['CAP', 2], 'STK': ['STK', 2], 'SZW': ['SZW', 2], 'DLA': ['DLA', 4], 'DLB': ['DLB', 3]}
Rolling walk-forward vs BARE among the combos 0.775 over 80 periods; fixed-pick persistence 0.796; year bands vs bare (equal-risk $/wk) AMBER/RED/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU4 loss cut when unrealised <= -90 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF1: LK3 lock at 50% -> stop to entry+20 pts (d ulcer +598, d $/wk -1700, fails the guard: weak)
- TAKE.MF1: TK12 take at 95% of target after 30 s without a new extreme (d ulcer -69, d $/wk +39)
- ZONE.MF1: ZONE2 zone no-trade set MF1 Half within 30 pts (d ulcer -85, d $/wk -39)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, d $/wk +0, fails the guard: weak)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer +0, d $/wk -29, fails the guard: weak)
- CAP: CAP1 per-book day profit stop +5R ($18000) (d ulcer +0, d $/wk +0, fails the guard: weak)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($14400) (d ulcer +0, d $/wk +0, fails the guard: weak)
- SZW: SZW2 ER sizer (new-book hook) ER(20,5m) < 0.30 -> lots x 0.50, half-up, min 1 (d ulcer -266, d $/wk -1340)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer +0, d $/wk +0, fails the guard: weak)
- CG: CGB2 skip after 2 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLA: DLA3 per-book day loss halt at -2R (open P&L counts, close the position, halt rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLB: DLB3 stack day loss halt at -$4000 per lot per book (open P&L counts, all books halted, positions closed, rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLC: DLC1 per-book halt after 2 consecutive full-stop losses (rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: 171 / 130 / -7
- LOCK.MF1: -239 / 219 / 299
- TAKE.MF1: 28 / 132 / 129
- ZONE.MF1: 246 / 95 / -44
- SC: 42 / 90 / 158
- BL: -16 / 214 / 90
- CAP: 68 / 143 / 80
- STK: 145 / 74 / 75
- SZW: 333 / -340 / 307
- NTS: 78 / 60 / 153
- CG: 65 / 158 / 67
- DLA: 110 / 216 / -33
- DLB: 166 / 73 / 56
- DLC: 100 / 96 / 96

## 4 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 1364 / -3931 / -2475 / -3328 / 1619 | 1099 / -3328 / -2834 / -3328 / 1331 |
| L3M | 1549 / -3931 / -2475 / -3328 / 1352 | 1352 / -3328 / -2834 / -3328 / 1102 |
| 2023 | 1965 / -5281 / -2576 / -1802 / 261 | 1497 / -3799 / -2127 / -1351 / 226 |
| 2024 | 4195 / -11366 / -5295 / -4220 / 263 | 3853 / -9706 / -4260 / -3619 / 173 |
| 2025 | 5728 / -13036 / -4626 / -3025 / 136 | 4493 / -11527 / -5015 / -2721 / 154 |

Best joint combo TL3_SR_LO_L19201dfc_R0BRF90_30_BF4_JT1: {'LOSS.MF1': ['CU', 4], 'TAKE.MF1': ['TK', 12], 'ZONE.MF1': ['ZONE', 3], 'BL': ['BL', 1], 'CAP': ['CAP', 2], 'SZW': ['SZW', 4], 'NTS': ['NTS', 2], 'DLA': ['DLA', 3], 'DLB': ['DLB', 4]}
Rolling walk-forward vs BARE among the combos 0.825 over 80 periods; fixed-pick persistence 0.796; year bands vs bare (equal-risk $/wk) GREEN/AMBER/GREEN; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU4 loss cut when unrealised <= -90 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF1: LK3 lock at 50% -> stop to entry+20 pts (d ulcer +1228, d $/wk -3502, fails the guard: weak)
- TAKE.MF1: TK12 take at 95% of target after 30 s without a new extreme (d ulcer -238, d $/wk +419)
- ZONE.MF1: ZONE2 zone no-trade set MF1 Half within 30 pts (d ulcer -148, d $/wk -244)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots) (d ulcer +0, d $/wk +0, fails the guard: weak)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer +0, d $/wk -250, fails the guard: weak)
- CAP: CAP1 per-book day profit stop +5R ($36000) (d ulcer +0, d $/wk +0, fails the guard: weak)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($28800) (d ulcer +0, d $/wk +0, fails the guard: weak)
- SZW: SZW4 ER sizer (new-book hook) ER(20,5m) < 0.30 -> lots x 0.75, half-up, min 1 (d ulcer -602, d $/wk -1251)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer +0, d $/wk +0, fails the guard: weak)
- CG: CGB2 skip after 2 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLA: DLA3 per-book day loss halt at -2R (open P&L counts, close the position, halt rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLB: DLB3 stack day loss halt at -$4000 per lot per book (open P&L counts, all books halted, positions closed, rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLC: DLC1 per-book halt after 2 consecutive full-stop losses (rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: 215 / 53 / 400
- LOCK.MF1: -310 / 635 / 324
- TAKE.MF1: 54 / 269 / 340
- ZONE.MF1: 505 / 316 / -141
- SC: 382 / 163 / 130
- BL: -227 / 320 / 559
- CAP: 23 / 301 / 337
- STK: 337 / 273 / 62
- SZW: 940 / -288 / 43
- NTS: 159 / 256 / 251
- CG: 187 / 110 / 371
- DLA: 197 / 139 / 332
- DLB: 282 / 320 / 69
- DLC: 229 / 220 / 220

