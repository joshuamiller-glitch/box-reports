# BAREFIT_AS_STKd8da2eb47b - truly bare all-layers fit (W-LAYERS, 2026-11-24 15:58Z)

Base = TRULY BARE R0 of the stack at each lot basis; every setting added on top of bare and judged AGAINST BARE. Per lot basis: screen = one setting at a time (L6M); joint = top-2 of every factor varied together (OA(81,40,3,2), 80 combos x 42 months). Cells ulcer / max DD / worst week / worst DAY / $ per week (per lot = divided by the lot basis).

## 2 lot(s) per book

| window | truly bare | best joint | |
|---|---|---|
| L6M | 2943 / -10556 / -5111 / -6858 / 7217 | 1000 / -3776 / -2249 / -2251 / 3783 |
| L3M | 3470 / -10556 / 456 / -6858 / 6037 | 993 / -3237 / 253 / -2222 / 3017 |
| 2023 | 2891 / -6436 / -3636 / -2866 / 902 | 2382 / -5159 / -2229 / -1430 / 253 |
| 2024 | 5836 / -15782 / -7343 / -5391 / 1187 | 3829 / -10372 / -4591 / -2764 / 674 |
| 2025 | 6236 / -16098 / -10547 / -7190 / 1285 | 3262 / -11848 / -9100 / -4515 / 553 |

Best joint combo TL3_SR_AS_STKd8da2eb47b_BF2_JT110: {'LOSS.MF1': ['CU', 4], 'TAKE.MF1': ['FR_TAKE', 4], 'ZONE.MF1': ['ZONE', 5], 'LOSS.MF2': ['CU', 4], 'LOCK.MF2': ['LK', 7], 'ZONE.MF2': ['ZONE', 2], 'LOSS.MF3': ['CX', 2], 'TAKE.MF3': ['TK', 2], 'ZONE.MF3': ['ZONE', 3], 'TAKE.MF4': ['SHV', 3], 'ZONE.MF4': ['ZONE', 4], 'BL': ['BL', 1], 'CAP': ['CAP', 2], 'SZW': ['SZW', 3], 'NTS': ['NTS', 2], 'CG': ['CGB', 1], 'DLA': ['DLA', 11], 'DLC': ['DLC', 3]}
Rolling walk-forward vs BARE among the combos 0.875 over 80 periods; fixed-pick persistence 0.839; year bands vs bare (equal-risk $/wk) RED/GREEN/AMBER; null: pending (1-lot screen null).

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
- CG: CGB1 skip after 1 same-side losses (c_gov, governs every new book MF1..MF5) (d ulcer -126, d $/wk +57)
- DLA: DLA4 per-book day loss halt at -2.5R (open P&L counts, close the position, halt rest of session) (d ulcer -650, d $/wk -2438)
- DLB: DLB14 stack day loss halt at -$8000 per lot per book (close positions, pause 60 min then re-arm) (d ulcer +99, d $/wk +10, fails the guard: weak)
- DLC: DLC3 per-book halt after 4 consecutive full-stop losses (rest of session) (d ulcer -408, d $/wk -1089)

Main effects (OA; mean d ulcer vs bare over the combos at level 0 / 1 / 2 of each factor; level 1 = best single setting, 2 = second):

- LOSS.MF1: -2622 / -2943 / -2759
- LOCK.MF1: -2564 / -2963 / -2795
- TAKE.MF1: -2798 / -2781 / -2751
- ZONE.MF1: -2794 / -2717 / -2820
- LOSS.MF2: -2716 / -2715 / -2897
- LOCK.MF2: -2618 / -2822 / -2884
- TAKE.MF2: -2878 / -2723 / -2732
- ZONE.MF2: -2800 / -2781 / -2749
- LOSS.MF3: -2828 / -2789 / -2714
- LOCK.MF3: -2776 / -2847 / -2708
- TAKE.MF3: -2593 / -2883 / -2846
- ZONE.MF3: -2946 / -2719 / -2671
- LOSS.MF4: -2896 / -2725 / -2713
- LOCK.MF4: -2855 / -2697 / -2781
- TAKE.MF4: -2760 / -2821 / -2748
- ZONE.MF4: -2847 / -2814 / -2672
- SC: -2857 / -2593 / -2882
- BL: -2559 / -2992 / -2770
- CAP: -2810 / -2799 / -2722
- STK: -2827 / -2644 / -2861
- SZW: -2192 / -3174 / -2942
- NTS: -2697 / -2819 / -2811
- CG: -2999 / -2419 / -2920
- DLA: -2762 / -2777 / -2790
- DLB: -2895 / -2801 / -2638
- DLC: -2835 / -2820 / -2676

