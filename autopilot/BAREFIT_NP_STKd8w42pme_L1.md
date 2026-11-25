# BAREFIT_NP_STKd8w42pme - truly bare all-layers fit (W-LAYERS, 2026-11-25 21:17Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 1 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 2227 / -6395 / -5112 / -4439 / 2433 | 1749 / -5596 / -3704 / -4666 / 2077 |
| L3M | 2053 / -5889 / -2342 / -4439 / 2204 | 1905 / -5596 / -3704 / -4666 / 1540 |
| 2023 | 8468 / -17458 / -4783 / -4594 / 503 | 4006 / -10360 / -5800 / -3479 / 454 |
| 2024 | 10425 / -25100 / -8162 / -5135 / 944 | 8161 / -19088 / -4680 / -4579 / 533 |
| 2025 | 4340 / -16310 / -6186 / -6308 / 1419 | 5138 / -16160 / -7833 / -4522 / 1053 |

Best joint combo TL3_SR_NP_STKd8w42pme_BF1_JT9: {'LOSS.MF2': ['FR_LOSS', 8], 'LOCK.MF2': ['LK', 9], 'TAKE.MF2': ['TK', 3], 'ZONE.MF2': ['ZONE', 4], 'DLA': ['DLA', 9], 'DLB': ['DLB', 5], 'DLC': ['DLC', 2], 'SC': ['SC', 1], 'BL': ['BL', 1]}
Rolling walk-forward vs BARE among the combos 0.442 over 77 periods; fixed-pick persistence 0.505; year bands vs bare (equal-risk $/wk) GREEN/AMBER/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: STC4 state-cut cell MF1 mult 15.0 (d ulcer -110, d $/wk +71)
- LOCK.MF1: LK7 lock at 80% -> stop to entry+0 pts (d ulcer +466, d $/wk -254, fails the guard: weak)
- TAKE.MF1: NRT1 near-target latch MF1 X 0.90 stale 10 (d ulcer +0, d $/wk +0, fails the guard: weak)
- ZONE.MF1: ZONE1 zone no-trade set MF1 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOSS.MF2: FR_LOSS8 W-FASTR pick: no-follow-through: < +5 pts after 20 min (d ulcer -384, d $/wk -238)
- LOCK.MF2: LK9 lock at 80% -> stop to entry+20 pts (d ulcer -53, d $/wk -33)
- TAKE.MF2: TK3 take at 50% of target after 30 s without a new extreme (d ulcer -391, d $/wk -215)
- ZONE.MF2: ZONE4 zone no-trade set MF2 Skip within 20 pts (d ulcer -59, d $/wk -41)
- DLA: DLA9 per-book day loss halt at -2R (new entries only, open position runs, rest of session) (d ulcer -4, d $/wk +14)
- DLB: DLB5 stack day loss halt at -$6000 per lot per book (open P&L counts, all books halted, positions closed, rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLC: DLC2 per-book halt after 3 consecutive full-stop losses (rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer -82, d $/wk +174)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -114, d $/wk -126)
- CAP: CAP1 per-book day profit stop +5R ($9000) (d ulcer +0, d $/wk +0, fails the guard: weak)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($7200) (d ulcer +0, d $/wk +0, fails the guard: weak)
- SZW: SZW1 ER sizer (new-book hook) ER(20,5m) < 0.20 -> lots x 0.50, half-up, min 1 (d ulcer +0, d $/wk +0, fails the guard: weak)
- NTS: NTS1 no-trade-set halving 0.5 (today's rule) (d ulcer +0, d $/wk +0, fails the guard: weak)
- CG: CGB3 skip after 3 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer +0, d $/wk +0, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: 33 / 475 / 1377
- LOCK.MF1: -181 / 1062 / 996
- TAKE.MF1: 902 / 735 / 280
- ZONE.MF1: 968 / 292 / 659
- LOSS.MF2: 559 / 582 / 763
- LOCK.MF2: 177 / 900 / 813
- TAKE.MF2: 1403 / 293 / 240
- ZONE.MF2: 672 / 568 / 668
- DLA: 872 / 570 / 474
- DLB: 359 / 780 / 758
- DLC: 948 / 501 / 470
- SC: 805 / 521 / 587
- BL: 309 / 685 / 901
- CAP: 651 / 628 / 628
- STK: 651 / 627 / 629
- SZW: 652 / 627 / 628
- NTS: 650 / 629 / 629
- CG: 653 / 628 / 627

