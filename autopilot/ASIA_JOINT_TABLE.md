# JOINT STAGE TABLE - Asia own-checks pool (W-LAYERS, STAMP 2026-11-21 04:17Z; refreshed every 15 min by joint_verdict.py --loop; only rows from the corrected JNT9 array count, the voided 80-combo run feeds nothing)

Per book: BRK/LOSS/LOCK/TAKE varied TOGETHER (reference + top-2 of the stage-1 screen per group, OA(9,4,3,2) = 8 combos + BASE). PICK = best combo on L6M (ulcer, drawdown first, 15% guard); cells = `ulcer fitted/unfitted; $/wk fitted/unfitted; eq = $/wk at equal risk`, 1 lot. Gates: ROLLING walk-forward among the combos + reference (>= 0.58), year colours 2023/24/25 on equal-risk $/wk (RED > 30% fails), search-aware null >= 4/5; 27/30 info only (stage-1 table). KEPT = all gates; otherwise the book keeps today's settings.

| book | pick (levels) | L6M | L3M | rolling WF (fixed) | years | null | verdict |
|---|---|---|---|---|---|---|---|
| L578701ed | BRK:BRK2, LOSS:ref, LOCK:LK2, TAKE:FR_TAKE4 | 3060/5315; 1794/2207; eq 3116/2207 | 2839/6964; 1108/614; eq 2719/614 | 0.53 (fixed 0.581) | GREEN/GREEN/GREEN | 4/5 | NOT KEPT: rolling WF 0.53 < 0.58 |
| Lff52ec0c | BRK:ref, LOSS:FR_LOSS9, LOCK:LK8, TAKE:FR_TAKE4 | 2403/3866; 2436/1882; eq 3919/1882 | 1852/4063; 2013/1357; eq 4417/1357 | 0.53 (fixed 0.613) | GREEN/AMBER/RED | 4/5 | NOT KEPT: rolling WF 0.53 < 0.58; RED year |
| L7c368a4f | BRK:BRK1, LOSS:CU2, LOCK:ref, TAKE:TK5 | 2890/4075; 1632/2456; eq 2301/2456 | 2240/2028; 2011/2434; eq 1820/2434 | 0.56 (fixed 0.366) | RED/RED/RED | 4/5 | NOT KEPT: rolling WF 0.56 < 0.58; RED year |
| L9aa7805c | BRK:BRK4, LOSS:CX2, LOCK:LK4, TAKE:ref | 2748/3604; 1987/1691; eq 2606/1691 | 2932/3141; 2252/1635; eq 2413/1635 | 0.53 (fixed 0.624) | AMBER/GREEN/GREEN | 4/5 | NOT KEPT: rolling WF 0.53 < 0.58 |
| M7423c0d9 | BRK:BRK4, LOSS:FR_LOSS9, LOCK:ref, TAKE:FR_TAKE2 | 2997/3256; 1446/1055; eq 1571/1055 | 3589/3554; 733/860; eq 726/860 | 0.53 (fixed 0.624) | RED/GREEN/RED | 3/5 | NOT KEPT: rolling WF 0.53 < 0.58; RED year; null 3/5 |
| L15f14deb | BRK:BRK1, LOSS:FR_LOSS9, LOCK:ref, TAKE:FR_TAKE3 | 2519/3329; 1748/1482; eq 2310/1482 | 2711/3086; 1250/1208; eq 1423/1208 | 0.51 (fixed 0.505) | RED/GREEN/RED | 4/5 | NOT KEPT: rolling WF 0.51 < 0.58; RED year |
| L1756b913 | BRK:BRK3, LOSS:STC4, LOCK:ref, TAKE:NRT3 | 3164/4678; 2076/2107; eq 3069/2107 | 2895/2256; 2235/3272; eq 1741/3272 | 0.43 (fixed 0.376) | AMBER/RED/RED | 4/5 | NOT KEPT: rolling WF 0.43 < 0.58; RED year |
| L1edb9fab | pending: 7/8 combos complete (309/336 set-months) | | | | | | |
| L3faac8df | pending: 3/8 combos complete (220/336 set-months) | | | | | | |
| L7f41b347 | pending: 3/8 combos complete (130/336 set-months) | | | | | | |
| Lcbc8a7ec | pending: 2/8 combos complete (90/336 set-months) | | | | | | |
| L973b5c8a | pending: 1/8 combos complete (50/336 set-months) | | | | | | |
| Lb68a132d | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| Lec335094 | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| L5dee2059 | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| L29b1bc3f | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| L40bde9ea | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| L7ea48296 | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| L65a26c02 | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| La010c3eb | BRK:BRK3, LOSS:ref, LOCK:LK1, TAKE:TK1 | 2767/3973; 801/861; eq 1151/861 | 2916/3181; 678/906; eq 740/906 | 0.66 (fixed 0.581) | RED/GREEN/RED | 4/5 | NOT KEPT: RED year |
| Lc754cf58 | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| Ma010c3eb | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| Mcae177ba | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| L385f4f2e | pending: 0/8 combos complete (0/336 set-months) | | | | | | |
| M7ea48296 | pending: 0/8 combos complete (0/336 set-months) | | | | | | |

## INFORMATION FOR JOSH (not a gate)

**Rolling walk-forward, exact definition (wf_gate.rolling).** Periods = 14-day blocks counted from 2023-04-03. For each period P that has at least 182 days of history before it: (i) the TRAILING window is the 182 days before P; (ii) on that window the ULCER (RMS drawdown of the daily P&L at 1 lot) is computed for each of the 8 joint combos and for the reference (the book's own settings); (iii) the combo with the lowest trailing ulcer is chosen if its ulcer is strictly below the reference's, otherwise the REFERENCE is chosen; (iv) when the reference is chosen the period is LEFT OUT (neither win nor loss; it is not in the denominator); (v) otherwise the chosen combo is compared with the reference IN PERIOD P: it WINS when its max drawdown inside the period (cumulative daily P&L from the period start, 1 lot, no scaling) is NOT DEEPER than the reference's (tolerance 1e-9); if the two drawdowns are equal (e.g. both 0), it wins when its period net $ (1 lot) is not lower than the reference's. Periods with no trade in either version are left out. Persistence = wins / counted periods. So 'beats' = period max drawdown first, net $ at 1 lot only as the tie-break; it is NOT equal-risk $, not ulcer of the period, not worst day. A tie on both drawdown and $ counts as a WIN.

Per complete book: (A) ROLLING pick (re-picked each period) and (B) FIXED pick (the L6M pick held in every period, same periods). Cells `win/tie/loss (share ties as losses; share ties left out)`. NOTE the FIXED pick is the L6M pick, so it is in-sample for the last 6 months. Each cell of the counted periods and the share with ties counted as losses / ties left out, for: net $ at 1 lot; $ at equal risk (chosen combo scaled by trailing-window ulcer ratio reference/combo); lower period max drawdown; better worst day (higher min daily P&L in the period). `ref` = periods where the reference was the rolling choice (left out).

| book | mode | periods (ref left out; dd ties) | net $ 1 lot | $ equal risk | lower period max DD | better worst day |
|---|---|---|---|---|---|---|
| L578701ed | rolling | 75 (ref 5; dd ties 8; GATE number 0.53) | 32/2/41 (0.43; 0.44) | 45/0/30 (0.6; 0.6) | 36/8/31 (0.48; 0.54) | 32/23/20 (0.43; 0.62) |
| L578701ed | fixed c3 | 80 (ref 0; dd ties 4; GATE number 0.56) | 38/2/40 (0.47; 0.49) | 42/0/38 (0.53; 0.53) | 43/4/33 (0.54; 0.57) | 46/4/30 (0.57; 0.61) |
| Lff52ec0c | rolling | 79 (ref 1; dd ties 25; GATE number 0.53) | 42/2/35 (0.53; 0.55) | 46/0/33 (0.58; 0.58) | 29/25/25 (0.37; 0.54) | 33/32/14 (0.42; 0.7) |
| Lff52ec0c | fixed c2 | 80 (ref 0; dd ties 45; GATE number 0.59) | 27/21/32 (0.34; 0.46) | 35/0/45 (0.44; 0.44) | 18/45/17 (0.23; 0.51) | 14/55/11 (0.17; 0.56) |
| L7c368a4f | rolling | 79 (ref 1; dd ties 13; GATE number 0.56) | 37/0/42 (0.47; 0.47) | 43/0/36 (0.54; 0.54) | 38/13/28 (0.48; 0.58) | 37/18/24 (0.47; 0.61) |
| L7c368a4f | fixed c7 | 80 (ref 0; dd ties 2; GATE number 0.34) | 27/0/53 (0.34; 0.34) | 27/0/53 (0.34; 0.34) | 27/2/51 (0.34; 0.35) | 35/2/43 (0.44; 0.45) |
| L9aa7805c | rolling | 75 (ref 5; dd ties 11; GATE number 0.53) | 37/1/37 (0.49; 0.5) | 49/0/26 (0.65; 0.65) | 34/11/30 (0.45; 0.53) | 32/16/27 (0.43; 0.54) |
| L9aa7805c | fixed c4 | 80 (ref 0; dd ties 14; GATE number 0.65) | 52/1/27 (0.65; 0.66) | 57/0/23 (0.71; 0.71) | 40/14/26 (0.5; 0.61) | 37/22/21 (0.46; 0.64) |
| M7423c0d9 | rolling | 80 (ref 0; dd ties 34; GATE number 0.53) | 33/5/42 (0.41; 0.44) | 36/0/44 (0.45; 0.45) | 27/34/19 (0.34; 0.59) | 19/51/10 (0.24; 0.66) |
| M7423c0d9 | fixed c7 | 80 (ref 0; dd ties 49; GATE number 0.68) | 38/15/27 (0.47; 0.58) | 39/0/41 (0.49; 0.49) | 17/49/14 (0.21; 0.55) | 8/67/5 (0.1; 0.62) |
| L15f14deb | rolling | 61 (ref 19; dd ties 13; GATE number 0.51) | 23/1/37 (0.38; 0.38) | 27/0/34 (0.44; 0.44) | 25/13/23 (0.41; 0.52) | 23/21/17 (0.38; 0.57) |
| L15f14deb | fixed c5 | 80 (ref 0; dd ties 4; GATE number 0.54) | 37/0/43 (0.46; 0.46) | 40/0/40 (0.5; 0.5) | 40/4/36 (0.5; 0.53) | 41/5/34 (0.51; 0.55) |
| L1756b913 | rolling | 51 (ref 29; dd ties 6; GATE number 0.43) | 17/0/34 (0.33; 0.33) | 26/0/25 (0.51; 0.51) | 22/6/23 (0.43; 0.49) | 23/11/17 (0.45; 0.57) |
| L1756b913 | fixed c5 | 80 (ref 0; dd ties 28; GATE number 0.35) | 23/1/56 (0.29; 0.29) | 28/0/52 (0.35; 0.35) | 22/28/30 (0.28; 0.42) | 17/43/20 (0.21; 0.46) |
| La010c3eb | rolling | 65 (ref 15; dd ties 6; GATE number 0.66) | 30/1/34 (0.46; 0.47) | 39/0/26 (0.6; 0.6) | 41/6/18 (0.63; 0.69) | 33/10/22 (0.51; 0.6) |
| La010c3eb | fixed c3 | 80 (ref 0; dd ties 12; GATE number 0.64) | 39/0/41 (0.49; 0.49) | 39/0/41 (0.49; 0.49) | 48/12/20 (0.6; 0.71) | 38/33/9 (0.47; 0.81) |

Drawdown-first summary over ALL 42 months (2023-04..2026-10), unfitted -> joint L6M pick, 1 lot:

| book | pick | ulcer | max DD | worst week | $/wk |
|---|---|---|---|---|---|
| L578701ed | c3 | 7983 -> 5201 | -26575 -> -19113 | -6603 -> -7401 | 763 -> 798 |
| Lff52ec0c | c2 | 8002 -> 8169 | -23231 -> -24047 | -10322 -> -7700 | 702 -> 643 |
| L7c368a4f | c7 | 5484 -> 20550 | -17690 -> -48969 | -10102 -> -9514 | 831 -> 284 |
| L9aa7805c | c4 | 6342 -> 3707 | -17159 -> -13936 | -8408 -> -9028 | 651 -> 917 |
| M7423c0d9 | c7 | 5160 -> 7710 | -16553 -> -19465 | -8104 -> -7200 | 379 -> 329 |
| L15f14deb | c5 | 9961 -> 7342 | -30358 -> -20225 | -7537 -> -10959 | 713 -> 553 |
| L1756b913 | c5 | 5597 -> 8328 | -13751 -> -24344 | -6112 -> -9702 | 746 -> 520 |
| La010c3eb | c3 | 8437 -> 4322 | -23200 -> -12503 | -13027 -> -7221 | 415 -> 385 |
