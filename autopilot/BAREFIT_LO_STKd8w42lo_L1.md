# BAREFIT_LO_STKd8w42lo - truly bare all-layers fit (W-LAYERS, 2026-11-25 19:12Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 1 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 6305 / -19383 / -10078 / -12650 / 10773 | 3210 / -8124 / -6244 / -7522 / 5847 |
| L3M | 7424 / -19383 / -9051 / -10341 / 9954 | 3253 / -8124 / -3461 / -6352 / 7590 |
| 2023 | 14449 / -36148 / -24461 / -12908 / 1617 | 12018 / -24534 / -11957 / -5794 / 293 |
| 2024 | 10615 / -41168 / -20802 / -19277 / 2535 | 11391 / -31437 / -19210 / -11242 / 529 |
| 2025 | 60261 / -107674 / -52465 / -40029 / 1023 | 58444 / -83262 / -30322 / -20570 / -1227 |

Best joint combo TL3_SR_LO_STKd8w42lo_BF1_JT4: {'LOSS.MF1': ['CU', 4], 'LOCK.MF1': ['LK', 3], 'TAKE.MF1': ['TK', 12], 'LOCK.MF2': ['LK', 5], 'TAKE.MF2': ['TK', 12], 'ZONE.MF2': ['ZONE', 3], 'LOSS.MF3': ['FR_LOSS', 7], 'TAKE.MF3': ['TK', 8], 'DLA': ['DLA', 3], 'DLC': ['DLC', 1], 'SC': ['SC', 1], 'BL': ['BL', 4], 'CAP': ['CAP', 1], 'SZW': ['SZW', 2], 'CG': ['CGB', 2]}
Rolling walk-forward vs BARE among the combos 0.775 over 80 periods; fixed-pick persistence 0.753; year bands vs bare (equal-risk $/wk) RED/RED/RED; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CU4 loss cut when unrealised <= -90 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF1: LK3 lock at 50% -> stop to entry+20 pts (d ulcer +852, d $/wk -3502, fails the guard: weak)
- TAKE.MF1: TK10 take at 95% of target after 5 s without a new extreme (d ulcer -189, d $/wk +649)
- ZONE.MF1: ZONE2 zone no-trade set MF1 Half within 30 pts (d ulcer -86, d $/wk -244)
- LOSS.MF2: STC4 state-cut cell MF2 mult 15.0 (d ulcer -1, d $/wk +14)
- LOCK.MF2: LK5 lock at 65% -> stop to entry+10 pts (d ulcer +101, d $/wk -1830, fails the guard: weak)
- TAKE.MF2: SHV2 target shave MF2 4 ticks (d ulcer -48, d $/wk -356)
- ZONE.MF2: ZONE3 zone no-trade set MF2 Half within 50 pts (d ulcer -152, d $/wk -625)
- LOSS.MF3: FR_LOSS9 W-FASTR pick: scratch: after -45 exit at -5 (d ulcer -1025, d $/wk +174)
- LOCK.MF3: LK7 lock at 80% -> stop to entry+0 pts (d ulcer -301, d $/wk +408)
- TAKE.MF3: TK7 take at 80% of target after 5 s without a new extreme (d ulcer -1000, d $/wk +1393)
- ZONE.MF3: ZONE5 zone no-trade set MF3 Skip within 30 pts (d ulcer -194, d $/wk -332)
- DLA: DLA3 per-book day loss halt at -2R (open P&L counts, close the position, halt rest of session) (d ulcer -386, d $/wk +667)
- DLB: DLB10 stack day loss halt at -$6000 per lot per book (new entries only, open positions run, rest of session) (d ulcer -1190, d $/wk -404)
- DLC: DLC1 per-book halt after 2 consecutive full-stop losses (rest of session) (d ulcer -670, d $/wk +256)
- SC: SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +85, d $/wk -316, fails the guard: weak)
- BL: BL4 BookLock arm 2.0R give-back 33% (d ulcer -327, d $/wk -564)
- CAP: CAP8 per-book day loss stop -6R ($14400) (d ulcer +0, d $/wk +0, fails the guard: weak)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($9600) (d ulcer -170, d $/wk -1011)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -1670, d $/wk -4030)
- NTS: NTS2 no-trade-set rule dropped (d ulcer +0, d $/wk +0, fails the guard: weak)
- CG: CGB2 skip after 2 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer -613, d $/wk +249)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -446 / -348 / -6
- LOCK.MF1: -1736 / 360 / 528
- TAKE.MF1: -202 / -390 / -199
- ZONE.MF1: -12 / -488 / -283
- LOSS.MF2: -523 / -166 / -114
- LOCK.MF2: 54 / -990 / 155
- TAKE.MF2: 33 / -377 / -438
- ZONE.MF2: -504 / 176 / -474
- LOSS.MF3: 165 / -380 / -561
- LOCK.MF3: -698 / 287 / -398
- TAKE.MF3: 314 / -939 / -147
- ZONE.MF3: -795 / 343 / -360
- DLA: -101 / -550 / -137
- DLB: -446 / -325 / -29
- DLC: -65 / -518 / -202
- SC: -1262 / 749 / -317
- BL: -202 / -69 / -520
- CAP: -167 / -264 / -358
- STK: -263 / -491 / -39
- SZW: 512 / -987 / -289
- NTS: -389 / -96 / -312
- CG: 509 / -843 / -430

