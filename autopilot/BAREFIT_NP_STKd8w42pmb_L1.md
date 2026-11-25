# BAREFIT_NP_STKd8w42pmb - truly bare all-layers fit (W-LAYERS, 2026-11-25 21:16Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 1 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 2409 / -6224 / -1285 / -4324 / 2290 | 2085 / -6479 / -1405 / -6042 / 2462 |
| L3M | 2069 / -5597 / -1082 / -4324 / 2334 | 1816 / -4853 / -1218 / -3884 / 2356 |
| 2023 | 7084 / -14172 / -4797 / -5684 / 821 | 7505 / -15006 / -5982 / -5684 / 596 |
| 2024 | 7734 / -23907 / -10012 / -6564 / 650 | 7430 / -25684 / -8227 / -3604 / 661 |
| 2025 | 6149 / -15632 / -5902 / -7119 / 1197 | 7588 / -17898 / -7353 / -5248 / 572 |

Best joint combo TL3_SR_NP_STKd8w42pmb_BF1_JT19: {'LOSS.MF1': ['STC', 4], 'TAKE.MF1': ['TK', 12], 'ZONE.MF1': ['ZONE', 2], 'LOSS.MF2': ['CU', 4], 'TAKE.MF2': ['TK', 6], 'ZONE.MF2': ['ZONE', 2], 'DLB': ['DLB', 5], 'DLC': ['DLC', 8], 'BL': ['BL', 7], 'STK': ['STK', 1], 'SZW': ['SZW', 2], 'CG': ['CGB', 1]}
Rolling walk-forward vs BARE among the combos 0.537 over 80 periods; fixed-pick persistence 0.505; year bands vs bare (equal-risk $/wk) RED/GREEN/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: STC4 state-cut cell MF1 mult 15.0 (d ulcer -87, d $/wk +89)
- LOCK.MF1: LK5 lock at 65% -> stop to entry+10 pts (d ulcer -16, d $/wk -318, fails the guard: weak)
- TAKE.MF1: TK12 take at 95% of target after 30 s without a new extreme (d ulcer -12, d $/wk -9)
- ZONE.MF1: ZONE1 zone no-trade set MF1 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOSS.MF2: STC4 state-cut cell MF2 mult 15.0 (d ulcer -21, d $/wk +29)
- LOCK.MF2: LK7 lock at 80% -> stop to entry+0 pts (d ulcer -72, d $/wk +159)
- TAKE.MF2: TK6 take at 65% of target after 30 s without a new extreme (d ulcer -130, d $/wk -17)
- ZONE.MF2: ZONE1 zone no-trade set MF2 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLA: DLA10 per-book day loss halt at -3R (new entries only, open position runs, rest of session) (d ulcer -60, d $/wk +47)
- DLB: DLB5 stack day loss halt at -$6000 per lot per book (open P&L counts, all books halted, positions closed, rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLC: DLC4 per-book halt after 5 consecutive full-stop losses (rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +1065, d $/wk -296, fails the guard: weak)
- BL: BL7 BookLock arm 3.0R give-back 33% (d ulcer -9, d $/wk +66)
- CAP: CAP1 per-book day profit stop +5R ($7000) (d ulcer +0, d $/wk +0, fails the guard: weak)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($5600) (d ulcer +0, d $/wk +42, fails the guard: weak)
- SZW: SZW1 ER sizer (new-book hook) ER(20,5m) < 0.20 -> lots x 0.50, half-up, min 1 (d ulcer +0, d $/wk +0, fails the guard: weak)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer +0, d $/wk +0, fails the guard: weak)
- CG: CGB1 skip after 1 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer -57, d $/wk -16, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: 480 / 319 / 399
- LOCK.MF1: 326 / 377 / 489
- TAKE.MF1: 464 / 361 / 371
- ZONE.MF1: 436 / 366 / 394
- LOSS.MF2: 418 / 413 / 365
- LOCK.MF2: 424 / 287 / 483
- TAKE.MF2: 436 / 350 / 409
- ZONE.MF2: 351 / 401 / 440
- DLA: 375 / 377 / 442
- DLB: 430 / 443 / 322
- DLC: 421 / 376 / 399
- SC: -57 / 639 / 596
- BL: 376 / 370 / 448
- CAP: 429 / 365 / 401
- STK: 412 / 267 / 515
- SZW: 400 / 387 / 407
- NTS: 390 / 404 / 400
- CG: 446 / 266 / 484

