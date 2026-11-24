# BAREFIT_AS_L385f4f2e_P2JCX502 - truly bare all-layers fit (W-LAYERS, 2026-11-24 15:57Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 530 / -1922 / -1617 / -1922 / 2071 | 315 / -1267 / -800 / -1240 / 1259 |
| L3M | 615 / -1922 / -992 / -1922 / 2410 | 373 / -1267 / -102 / -1240 / 1392 |
| 2023 | 2262 / -4724 / -2032 / -1252 / 42 | 1080 / -2148 / -1012 / -625 / 19 |
| 2024 | 4476 / -11457 / -3549 / -1205 / 235 | 2446 / -6496 / -1770 / -1192 / 180 |
| 2025 | 4428 / -10223 / -3912 / -3615 / 160 | 1728 / -5154 / -2200 / -1775 / 159 |

Best joint combo TL3_SR_AS_L385f4f2e_P2JCX502_BF2_JT6: {'LOCK.MF1': ['LK', 4], 'TAKE.MF1': ['FR_TAKE', 2], 'ZONE.MF1': ['ZONE', 2], 'SC': ['SC', 2], 'BL': ['BL', 4], 'CAP': ['CAP', 2], 'STK': ['STK', 1], 'SZW': ['SZW', 3], 'NTS': ['NTS', 2]}
Rolling walk-forward vs BARE among the combos 0.846 over 78 periods; fixed-pick persistence 0.902; year bands vs bare (equal-risk $/wk) GREEN/GREEN/GREEN; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU4 loss cut when unrealised <= -60 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF1: LK7 lock at 80% -> stop to entry+0 pts (d ulcer +138, d $/wk +4, fails the guard: weak)
- TAKE.MF1: TK12 take at 95% of target after 30 s without a new extreme (d ulcer -5, d $/wk -96)
- ZONE.MF1: ZONE1 zone no-trade set MF1 Half within 10 pts (d ulcer +27, d $/wk -80, fails the guard: weak)
- DLA: DLA5 per-book day loss halt at -3R (open P&L counts, close the position, halt rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLB: DLB3 stack day loss halt at -$4000 per lot per book (open P&L counts, all books halted, positions closed, rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- DLC: DLC2 per-book halt after 3 consecutive full-stop losses (rest of session) (d ulcer +0, d $/wk +0, fails the guard: weak)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, d $/wk +0, fails the guard: weak)
- BL: BL2 BookLock arm 1.5R give-back 50% (d ulcer -1, d $/wk +20)
- CAP: CAP1 per-book day profit stop +5R ($12000) (d ulcer +0, d $/wk +0, fails the guard: weak)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($9600) (d ulcer +0, d $/wk +0, fails the guard: weak)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -390, d $/wk -1719)
- NTS: NTS2 no-trade-set rule dropped (d ulcer +0, d $/wk +0, fails the guard: weak)
- CG: CGB3 skip after 3 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer +0, d $/wk +0, fails the guard: weak)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -113 / -44 / -67
- LOCK.MF1: -142 / -18 / -65
- TAKE.MF1: -99 / -39 / -86
- ZONE.MF1: -68 / -38 / -117
- DLA: -62 / -122 / -38
- DLB: -66 / -72 / -84
- DLC: -70 / -64 / -88
- SC: -86 / -75 / -62
- BL: -81 / -24 / -118
- CAP: -125 / -22 / -77
- STK: -71 / -67 / -84
- SZW: 170 / -363 / -20
- NTS: -72 / -54 / -97
- CG: -84 / -80 / -59

