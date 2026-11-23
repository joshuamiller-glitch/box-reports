# BAREFIT_NP_STKd893133bd8 - truly bare all-layers fit (W-LAYERS, 2026-11-23 20:47Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 2787 / -12129 / -4283 / -8368 / 4368 | 1447 / -4830 / -3644 / -3384 / 2936 |
| L3M | 2072 / -7272 / -4283 / -4369 / 4359 | 966 / -3870 / -3644 / -2664 / 3032 |
| 2023 | 4065 / -15862 / -8512 / -6553 / 1708 | 3117 / -8808 / -6202 / -3113 / 872 |
| 2024 | 10819 / -29376 / -10817 / -13077 / 1258 | 5578 / -17986 / -7305 / -5655 / 1032 |
| 2025 | 6091 / -17988 / -11441 / -12878 / 2112 | 3108 / -9424 / -6903 / -7436 / 1557 |

Best joint combo TL3_SR_NP_STKd893133bd8_BF2_JT209: {'LOSS.MF2': ['CU', 3], 'LOCK.MF2': ['LK', 5], 'TAKE.MF2': ['SHV', 1], 'ZONE.MF2': ['ZONE', 4], 'LOSS.MF3': ['CU', 4], 'LOCK.MF3': ['LK', 7], 'TAKE.MF3': ['SHV', 2], 'ZONE.MF3': ['ZONE', 1], 'LOSS.MF4': ['CU', 4], 'STK': ['STK', 6], 'SZW': ['SZW', 3], 'NTS': ['NTS', 2], 'CG': ['CGB', 3]}
Rolling walk-forward vs BARE among the combos 0.887 over 80 periods; fixed-pick persistence 0.946; year bands vs bare (equal-risk $/wk) RED/GREEN/GREEN; null: pending (1-lot screen null).

Each factor's best setting ALONE (screen, L6M d ulcer vs bare; negative = better):

- LOSS.MF1: CX3 context cut (fresh) at -24 pts (d ulcer -154, d $/wk +37)
- LOCK.MF1: LK8 lock at 80% -> stop to entry+10 pts (d ulcer -65, d $/wk -341)
- TAKE.MF1: TK3 take at 50% of target after 30 s without a new extreme (d ulcer -296, d $/wk -128)
- ZONE.MF1: ZONE2 zone no-trade set MF1 Half within 30 pts (d ulcer -56, d $/wk -104)
- LOSS.MF2: CU3 loss cut when unrealised <= -96 pts (0.8 x stop) (d ulcer -761, d $/wk +911)
- LOCK.MF2: LK5 lock at 65% -> stop to entry+10 pts (d ulcer -143, d $/wk -1490, fails the guard: weak)
- TAKE.MF2: SHV1 target shave MF2 2 ticks (d ulcer +10, d $/wk -33, fails the guard: weak)
- ZONE.MF2: ZONE4 zone no-trade set MF2 Skip within 20 pts (d ulcer -4, d $/wk +192)
- LOSS.MF3: CU4 loss cut when unrealised <= -80 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF3: LK7 lock at 80% -> stop to entry+0 pts (d ulcer -51, d $/wk +277)
- TAKE.MF3: SHV2 target shave MF3 4 ticks (d ulcer -20, d $/wk -8)
- ZONE.MF3: ZONE1 zone no-trade set MF3 Half within 10 pts (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOSS.MF4: CU4 loss cut when unrealised <= -60 pts (1.0 x stop) (d ulcer +0, d $/wk +0, fails the guard: weak)
- LOCK.MF4: LK7 lock at 80% -> stop to entry+0 pts (d ulcer +216, d $/wk -209, fails the guard: weak)
- TAKE.MF4: TK12 take at 95% of target after 30 s without a new extreme (d ulcer +31, d $/wk -23, fails the guard: weak)
- ZONE.MF4: ZONE1 zone no-trade set MF4 Half within 10 pts (d ulcer -13, d $/wk -8)
- DLA: DLA9 per-book day loss halt at -2R (new entries only, open position runs, rest of session) (d ulcer -725, d $/wk +254)
- DLB: DLB10 stack day loss halt at -$6000 per lot per book (new entries only, open positions run, rest of session) (d ulcer -116, d $/wk +131)
- DLC: DLC2 per-book halt after 3 consecutive full-stop losses (rest of session) (d ulcer -323, d $/wk -88)
- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +1746, d $/wk -1866, fails the guard: weak)
- BL: BL9 BookLock arm 3.0R give-back 67% (d ulcer +8, d $/wk -122, fails the guard: weak)
- CAP: CAP6 per-book day loss stop -3R ($8400) (d ulcer -383, d $/wk +255)
- STK: STK6 WHOLE-STACK day loss stop -4R of one book ($11200) (d ulcer -99, d $/wk +49)
- SZW: SZW3 ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1 (d ulcer -1391, d $/wk -3366)
- NTS: NTS2 no-trade-set rule dropped (d ulcer +0, d $/wk +0, fails the guard: weak)
- CG: CGB3 skip after 3 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer -62, d $/wk +62)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: 602 / 275 / 1676
- LOCK.MF1: 878 / 694 / 991
- TAKE.MF1: 1011 / 794 / 763
- ZONE.MF1: 1184 / 314 / 1077
- LOSS.MF2: 1987 / -193 / 809
- LOCK.MF2: 169 / 1129 / 1239
- TAKE.MF2: 681 / 1225 / 649
- ZONE.MF2: 1108 / 433 / 1031
- LOSS.MF3: 1011 / 845 / 711
- LOCK.MF3: 1044 / 748 / 778
- TAKE.MF3: 783 / 1232 / 545
- ZONE.MF3: 1233 / 658 / 685
- LOSS.MF4: 74 / 254 / 2205
- LOCK.MF4: 487 / 1027 / 1034
- TAKE.MF4: 665 / 970 / 920
- ZONE.MF4: 905 / 393 / 1266
- DLA: 758 / 768 / 1032
- DLB: 522 / 985 / 1042
- DLC: 936 / 685 / 944
- SC: -206 / 1577 / 1151
- BL: 768 / 847 / 943
- CAP: 950 / 673 / 943
- STK: 657 / 1626 / 272
- SZW: 1692 / -156 / 1057
- NTS: 662 / 797 / 1096
- CG: 552 / 768 / 1231

