# BAREFIT_LO_L19201dfc_R0BRF90_30 - truly bare all-layers fit (W-LAYERS, 2026-11-25 19:55Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 1329 / -3918 / -2685 / -3315 / 1632 | 1046 / -2942 / -2111 / -1465 / 530 |
| L3M | 1528 / -3918 / -2452 / -3315 / 1368 | 872 / -2212 / -1164 / -1465 / 529 |
| 2023 | 1943 / -5248 / -2559 / -1800 / 269 | 1339 / -2628 / -1849 / -1285 / 143 |
| 2024 | 4346 / -11822 / -5813 / -4176 / 257 | 2790 / -5350 / -3942 / -1904 / 34 |
| 2025 | 5379 / -12905 / -4508 / -3012 / 161 | 5764 / -9201 / -3927 / -2718 / 7 |

Best joint combo TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_JT203: {'LOCK.MF1': ['LK', 3], 'TAKE.MF1': ['TK', 12], 'ZONE.MF1': ['ZONE', 2], 'STK': ['STK', 1], 'SZW': ['SZW', 2], 'NTS': ['NTS', 1], 'CG': ['CGB', 3], 'DLA': ['DLA', 4], 'DLB': ['DLB', 4]}
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

- LOSS.MF1: 171 / 130 / 647
- LOCK.MF1: -46 / 519 / 467
- TAKE.MF1: 340 / 300 / 315
- ZONE.MF1: 421 / 281 / 256
- SC: 334 / 281 / 340
- BL: 182 / 395 / 371
- CAP: 257 / 424 / 271
- STK: 406 / 311 / 240
- SZW: 579 / -174 / 558
- NTS: 250 / 311 / 391
- CG: 281 / 424 / 247
- DLA: 385 / 395 / 176
- DLB: 353 / 281 / 321
- DLC: 326 / 314 / 314

