# NYAM_WEIGHTED_FILE_SIZE - the weighted 9-book NY AM pick BF1_JT91 at the FILE'S whole-lot sizes (W-LAYERS2, 2026-11-25 03:27Z)

BAND RULE READING (correction 03:30Z): the band number is the pick's equal-risk $/wk SHORTFALL against bare, (bare $/wk - pick $/wk scaled to bare's ulcer) / |bare $/wk|; RED > +30%, AMBER > +15%, else GREEN. A NEGATIVE number means the pick earns MORE than bare at equal risk, so -128% = GREEN is correct (6/3/2 2024: pick $8,433/wk at ulcer 20,245 scales to about $26,000 at bare ulcer 62,415, against bare $11,410). Earlier wording "equal-risk $/wk +x%" read as a gain; it is the shortfall.

Sizes: MF1..MF9 = L43f0cbfb, B7bfd33b7, Bf428c4a1, Le4fede95, Lf0346d55, L8cfda948, L4407508c, L39287638, L64390867. 6/3/1 = lots 6 / 6 / 6 / 6 / 3 / 6 / 1 / 1 / 3 ; 6/3/2 = lots 6 / 6 / 6 / 6 / 3 / 6 / 2 / 2 / 3 (the two 0.25-weight books MF7 and MF8 at 1 or 2 lots). Fit basis (native W-COMBO x4) = 4 / 4 / 4 / 4 / 2 / 4 / 1 / 1 / 2. ALL DOLLARS BELOW ARE WHOLE-STACK TOTALS for the nine books at those lots (not per lot), L6M = 2026-05..10, L3M = 2026-08..10. PICKC = the JT91 pick with its static caps scaled by (file lots / native lots) per book; DLB9 NOT rescaled (its threshold is -$4,000 x the lots of the smallest-lot book not yet halted: -$4,000 at 6/3/1, -$8,000 at 6/3/2). Cells: ulcer / max DD / worst week / worst day / $ per week.

## Size 6 / 3 / 1

| window | bare | pick (PICKC) |
|---|---|---|
| L6M | 46412 / -158219 / -61020 / -126928 / $73016 | 34552 / -91745 / -30501 / -22747 / $23368 |
| L3M | 43303 / -147300 / -24084 / -115299 / $52311 | 12647 / -32768 / -19005 / -18080 / $14373 |
| 2023 | 68603 / -199244 / -76912 / -53675 / $15254 | 78902 / -168346 / -37528 / -21812 / $-603 |
| 2024 | 63228 / -168979 / -131737 / -88018 / $10678 | 26314 / -73488 / -44779 / -24089 / $3557 |
| 2025 | 95219 / -303052 / -190766 / -123944 / $21808 | 43611 / -121163 / -50620 / -30580 / $9844 |

Gates at this size (rows allow): fixed-pick persistence vs bare 0.839; prior-year bands vs bare at equal risk: 2023: ulcer +15%, pick equal-risk $/wk shortfall vs bare +103% = RED; 2024: ulcer -58%, pick equal-risk $/wk shortfall vs bare +20% = AMBER; 2025: ulcer -54%, pick equal-risk $/wk shortfall vs bare +1% = GREEN. Rolling walk-forward at this size: NOT run, see the last section.

## Size 6 / 3 / 2

| window | bare | pick (PICKC) |
|---|---|---|
| L6M | 46667 / -161823 / -60368 / -131362 / $75312 | 20453 / -64115 / -26776 / -22747 / $25395 |
| L3M | 43101 / -146923 / -25828 / -117688 / $54838 | 13792 / -30520 / -8145 / -17787 / $18575 |
| 2023 | 69917 / -197969 / -75366 / -58004 / $15716 | 87425 / -164468 / -42686 / -24950 / $-2949 |
| 2024 | 62415 / -163984 / -130986 / -87228 / $11410 | 20245 / -63854 / -35010 / -25485 / $8433 |
| 2025 | 91703 / -307025 / -195140 / -124954 / $22880 | 52983 / -132214 / -53417 / -30580 / $10501 |

Gates at this size (rows allow): fixed-pick persistence vs bare 0.849; prior-year bands vs bare at equal risk: 2023: ulcer +25%, pick equal-risk $/wk shortfall vs bare +115% = RED; 2024: ulcer -68%, pick equal-risk $/wk shortfall vs bare -128% = GREEN; 2025: ulcer -42%, pick equal-risk $/wk shortfall vs bare +21% = AMBER. Rolling walk-forward at this size: NOT run, see the last section.

## 6/3/1 versus 6/3/2 for L4407508c (MF7) and L39287638 (MF8) (both change together, 1 versus 2 lots)

| window | 6/3/1 ulcer / max DD / $ | 6/3/2 ulcer / max DD / $ |
|---|---|---|
| L6M | 34552 / -91745 / $23368 | 20453 / -64115 / $25395 |
| L3M | 12647 / -32768 / $14373 | 13792 / -30520 / $18575 |

CAVEAT: the two sizes also change DLB9's threshold (-$4,000 vs -$8,000, smallest-lot rule), so this comparison mixes the lots of two small books with the stack halt level; the NODLB rows below separate them.

## DLB9 at each size (L6M, from the same pick with the stack halt removed: sets FS631_NODLB / FS632_NODLB)

- 6/3/1: DLB9 changed 93 of 131 L6M trading days (entries blocked after it fired; days where it fired with nothing left to block are not visible); pick with DLB9: ulcer 34552 / max DD -91745 / $23368 per wk vs without DLB9: 21978 / -58458 / $32273 per wk; sum of the P&L of the changed days: with -188493 vs without 51935.
- 6/3/2: DLB9 changed 73 of 131 L6M trading days (entries blocked after it fired; days where it fired with nothing left to block are not visible); pick with DLB9: ulcer 20453 / max DD -64115 / $25395 per wk vs without DLB9: 21925 / -58458 / $32264 per wk; sum of the P&L of the changed days: with -297058 vs without -111585.

## Rolling walk-forward at the file size: feasible, not started

Only the native-basis joint has a rolling walk-forward (0.775, 242 combos x 42 months). The 0.839 / 0.849 above are fixed-pick persistence (the one pick vs bare per 2-week period), not a re-pick. A true rolling run at 6/3/1 or 6/3/2 = re-run the same 242 combos (levels from the native screen, caps scaled) = 10,164 rows per size (about 20,300 for both), a further 1,536 rows if the level screen is redone at that size. Cost: the native 10,164 rows took about 3-4 h of the shared grid at top priority (queued 22:56Z, landed about 02:15Z including 145 lost rows), so about 3-4 h per size, about 7 h for both, competing with the null (up to 17,010 rows) and the London / NY PM chain. No data spend, compute only. Not started.
