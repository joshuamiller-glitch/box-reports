# JOINT STAGE TABLE - Asia own-checks pool (W-LAYERS, STAMP 2026-11-23 11:05Z; refreshed every 15 min by joint_verdict.py --loop; only rows from the corrected JNT9 array count, the voided 80-combo run feeds nothing)

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
| L1edb9fab | BRK:BRK2, LOSS:CU4, LOCK:LK1, TAKE:ref | 2537/4509; 2147/2167; eq 3818/2167 | 1975/2367; 2326/2289; eq 2787/2289 | 0.56 (fixed 0.634) | GREEN/GREEN/GREEN | 4/5 | NOT KEPT: rolling WF 0.56 < 0.58 |
| L3faac8df | BRK:BRK2, LOSS:STC4, LOCK:LK7, TAKE:ref | 2325/4512; 2597/1314; eq 5041/1314 | 2762/5238; 1970/1186; eq 3735/1186 | 0.66 (fixed 0.677) | RED/GREEN/RED | 5/5 | NOT KEPT: RED year |
| L7f41b347 | BRK:ref, LOSS:FR_LOSS9, LOCK:LK8, TAKE:FR_TAKE4 | 2705/4173; 2331/2095; eq 3597/2095 | 2232/3104; 1763/1738; eq 2452/1738 | 0.49 (fixed 0.634) | GREEN/RED/RED | 4/5 | NOT KEPT: rolling WF 0.49 < 0.58; RED year |
| Lcbc8a7ec | BRK:BRK2, LOSS:CX3, LOCK:ref, TAKE:NRT1 | 1691/4828; 2681/1880; eq 7656/1880 | 1524/2664; 1932/2105; eq 3377/2105 | 0.70 (fixed 0.57) | AMBER/GREEN/RED | 5/5 | NOT KEPT: RED year |
| L973b5c8a | BRK:ref, LOSS:CX1, LOCK:LK5, TAKE:FR_TAKE2 | 3153/3886; 1586/1211; eq 1955/1211 | 2806/3189; 1635/1310; eq 1858/1310 | 0.55 (fixed 0.548) | RED/GREEN/GREEN | 4/5 | NOT KEPT: rolling WF 0.55 < 0.58; RED year |
| Lb68a132d | BRK:ref, LOSS:CX2, LOCK:LK2, TAKE:TK4 | 1581/3158; 1197/1090; eq 2392/1090 | 1557/2757; 909/1273; eq 1610/1273 | 0.38 (fixed 0.576) | GREEN/RED/RED | 5/5 | NOT KEPT: rolling WF 0.38 < 0.58; RED year |
| Lec335094 | none | - | - | - | - | - | NOT KEPT: no combo beats the reference on L6M within the guard; keeps today's |
| L5dee2059 | BRK:BRK4, LOSS:STC4, LOCK:LK6, TAKE:ref | 4360/7196; 1397/1142; eq 2305/1142 | 5163/5330; 991/1986; eq 1023/1986 | 0.70 (fixed 0.688) | RED/GREEN/GREEN | 4/5 | NOT KEPT: RED year |
| L29b1bc3f | BRK:ref, LOSS:STC1, LOCK:LK3, TAKE:TK2 | 2619/4118; 945/1293; eq 1485/1293 | 2032/4744; 1327/954; eq 3099/954 | 0.42 (fixed 0.462) | RED/RED/RED | 4/5 | NOT KEPT: rolling WF 0.42 < 0.58; RED year |
| L40bde9ea | BRK:BRK2, LOSS:ref, LOCK:LK5, TAKE:TK3 | 2894/4695; 893/937; eq 1449/937 | 2784/3391; 622/1664; eq 758/1664 | 0.60 (fixed 0.677) | GREEN/RED/GREEN | 4/5 | NOT KEPT: RED year |
| L7ea48296 | none | - | - | - | - | - | NOT KEPT: no combo beats the reference on L6M within the guard; keeps today's |
| L65a26c02 | BRK:ref, LOSS:CX3, LOCK:LK1, TAKE:FR_TAKE5 | 4475/4969; 1472/1666; eq 1635/1666 | 3736/5487; 2244/2028; eq 3295/2028 | 0.64 (fixed 0.677) | GREEN/GREEN/GREEN | 3/5 | NOT KEPT: null 3/5 |
| La010c3eb | BRK:BRK3, LOSS:ref, LOCK:LK1, TAKE:TK1 | 2767/3973; 801/861; eq 1151/861 | 2916/3181; 678/906; eq 740/906 | 0.66 (fixed 0.581) | RED/GREEN/RED | 4/5 | NOT KEPT: RED year |
| Lc754cf58 | BRK:BRK3, LOSS:STC2, LOCK:ref, TAKE:TK5 | 3249/5349; 921/1368; eq 1516/1368 | 2622/6362; 785/431; eq 1904/431 | 0.46 (fixed 0.462) | GREEN/RED/RED | 4/5 | NOT KEPT: rolling WF 0.46 < 0.58; RED year |
| Ma010c3eb | BRK:BRK2, LOSS:ref, LOCK:LK2, TAKE:TK1 | 2389/3630; 267/705; eq 405/705 | 1501/3441; 643/706; eq 1474/706 | 0.54 (fixed 0.613) | RED/RED/RED | 4/5 | NOT KEPT: rolling WF 0.54 < 0.58; RED year |
| Mcae177ba | BRK:ref, LOSS:CX2, LOCK:LK5, TAKE:FR_TAKE2 | 2997/3657; 270/341; eq 329/341 | 3196/4151; 118/22; eq 153/22 | 0.69 (fixed 0.634) | RED/RED/RED | 4/5 | NOT KEPT: RED year |
| L385f4f2e | BRK:BRK3, LOSS:ref, LOCK:LK2, TAKE:TK1 | 1868/3905; 449/476; eq 938/476 | 1265/2438; 970/457; eq 1870/457 | 0.58 (fixed 0.634) | GREEN/RED/AMBER | 5/5 | NOT KEPT: rolling WF 0.58 < 0.58; RED year |
| M7ea48296 | BRK:ref, LOSS:STC2, LOCK:LK5, TAKE:TK5 | 2515/4797; 915/429; eq 1745/429 | 2259/3328; 1611/862; eq 2374/862 | 0.60 (fixed 0.548) | RED/RED/GREEN | 5/5 | NOT KEPT: RED year |
| L9e4754b9 | BRK:BRK1, LOSS:ref, LOCK:LK7, TAKE:TK1 | 2039/3777; 1452/1218; eq 2691/1218 | 2197/3434; 1933/1118; eq 3021/1118 | 0.59 (fixed 0.57) | RED/GREEN/RED | 5/5 | NOT KEPT: RED year |
| M86781ac0 | BRK:BRK1, LOSS:FR_LOSS9, LOCK:LK7, TAKE:ref | 2033/3477; 1148/734; eq 1964/734 | 1367/3461; 1483/439; eq 3755/439 | 0.60 (fixed 0.645) | RED/GREEN/RED | 4/5 | NOT KEPT: RED year |
| L385f4f2e.J502 | none | - | - | - | - | - | NOT KEPT: no combo beats the reference on L6M within the guard; keeps today's |
| L018fb0c0 | BRK:ref, LOSS:STC2, LOCK:LK1, TAKE:TK8 | 2963/6637; 1443/617; eq 3233/617 | 2428/5968; 1726/1606; eq 4243/1606 | 0.54 (fixed 0.634) | RED/RED/GREEN | 5/5 | NOT KEPT: rolling WF 0.54 < 0.58; RED year |
| L130cb48e | BRK:ref, LOSS:CU4, LOCK:LK2, TAKE:FR_TAKE5 | 3665/4675; 1260/1465; eq 1607/1465 | 3998/5784; 1116/946; eq 1615/946 | 0.67 (fixed 0.667) | GREEN/AMBER/RED | 4/5 | NOT KEPT: RED year |
| L3a2258bd | BRK:BRK2, LOSS:ref, LOCK:LK4, TAKE:TK6 | 4787/6425; 1116/1760; eq 1498/1760 | 4102/3934; 941/1346; eq 902/1346 | 0.52 (fixed 0.538) | GREEN/GREEN/GREEN | 4/5 | NOT KEPT: rolling WF 0.52 < 0.58 |
| L47a9c81c | none | - | - | - | - | - | NOT KEPT: no combo beats the reference on L6M within the guard; keeps today's |
| L92a90948 | none | - | - | - | - | - | NOT KEPT: no combo beats the reference on L6M within the guard; keeps today's |
| La776664b | BRK:BRK1, LOSS:FR_LOSS8, LOCK:LK9, TAKE:ref | 3951/7008; 264/576; eq 468/576 | 2553/6869; 431/579; eq 1161/579 | 0.53 (fixed 0.581) | RED/RED/RED | 4/5 | NOT KEPT: rolling WF 0.53 < 0.58; RED year |
| M817db5df | none | - | - | - | - | - | NOT KEPT: no combo beats the reference on L6M within the guard; keeps today's |

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
| L1edb9fab | rolling | 79 (ref 1; dd ties 7; GATE number 0.56) | 39/0/40 (0.49; 0.49) | 46/0/33 (0.58; 0.58) | 40/7/32 (0.51; 0.56) | 46/11/22 (0.58; 0.68) |
| L1edb9fab | fixed c8 | 80 (ref 0; dd ties 4; GATE number 0.65) | 42/3/35 (0.53; 0.55) | 55/0/25 (0.69; 0.69) | 49/4/27 (0.61; 0.64) | 50/4/26 (0.62; 0.66) |
| L3faac8df | rolling | 65 (ref 15; dd ties 7; GATE number 0.66) | 38/2/25 (0.58; 0.6) | 43/0/22 (0.66; 0.66) | 40/7/18 (0.62; 0.69) | 41/9/15 (0.63; 0.73) |
| L3faac8df | fixed c8 | 80 (ref 0; dd ties 8; GATE number 0.70) | 46/7/27 (0.57; 0.63) | 53/0/27 (0.66; 0.66) | 48/8/24 (0.6; 0.67) | 50/9/21 (0.62; 0.7) |
| L7f41b347 | rolling | 67 (ref 13; dd ties 12; GATE number 0.49) | 34/1/32 (0.51; 0.52) | 38/0/29 (0.57; 0.57) | 28/12/27 (0.42; 0.51) | 35/15/17 (0.52; 0.67) |
| L7f41b347 | fixed c2 | 80 (ref 0; dd ties 41; GATE number 0.61) | 27/21/32 (0.34; 0.46) | 41/0/39 (0.51; 0.51) | 20/41/19 (0.25; 0.51) | 15/53/12 (0.19; 0.56) |
| Lcbc8a7ec | rolling | 56 (ref 24; dd ties 3; GATE number 0.70) | 32/2/22 (0.57; 0.59) | 38/0/18 (0.68; 0.68) | 37/3/16 (0.66; 0.7) | 37/3/16 (0.66; 0.7) |
| Lcbc8a7ec | fixed c5 | 80 (ref 0; dd ties 3; GATE number 0.57) | 42/1/37 (0.53; 0.53) | 50/0/30 (0.62; 0.62) | 45/3/32 (0.56; 0.58) | 47/3/30 (0.59; 0.61) |
| L973b5c8a | rolling | 80 (ref 0; dd ties 12; GATE number 0.55) | 33/0/47 (0.41; 0.41) | 47/0/33 (0.59; 0.59) | 42/12/26 (0.53; 0.62) | 33/26/21 (0.41; 0.61) |
| L973b5c8a | fixed c1 | 80 (ref 0; dd ties 10; GATE number 0.59) | 41/2/37 (0.51; 0.53) | 46/0/34 (0.57; 0.57) | 43/10/27 (0.54; 0.61) | 37/18/25 (0.46; 0.6) |
| Lb68a132d | rolling | 55 (ref 23; dd ties 11; GATE number 0.38) | 14/0/41 (0.25; 0.25) | 23/0/32 (0.42; 0.42) | 20/11/24 (0.36; 0.45) | 23/19/13 (0.42; 0.64) |
| Lb68a132d | fixed c1 | 78 (ref 0; dd ties 12; GATE number 0.54) | 28/0/50 (0.36; 0.36) | 33/0/45 (0.42; 0.42) | 41/12/25 (0.53; 0.62) | 40/24/14 (0.51; 0.74) |
| L5dee2059 | rolling | 79 (ref 1; dd ties 24; GATE number 0.70) | 42/9/28 (0.53; 0.6) | 52/0/27 (0.66; 0.66) | 33/24/22 (0.42; 0.6) | 25/30/24 (0.32; 0.51) |
| L5dee2059 | fixed c4 | 80 (ref 0; dd ties 48; GATE number 0.66) | 39/13/28 (0.49; 0.58) | 46/0/34 (0.57; 0.57) | 18/48/14 (0.23; 0.56) | 10/62/8 (0.12; 0.56) |
| L29b1bc3f | rolling | 66 (ref 14; dd ties 4; GATE number 0.42) | 18/0/48 (0.27; 0.27) | 26/0/40 (0.39; 0.39) | 28/4/34 (0.42; 0.45) | 31/13/22 (0.47; 0.58) |
| L29b1bc3f | fixed c1 | 80 (ref 0; dd ties 12; GATE number 0.49) | 30/0/50 (0.38; 0.38) | 31/0/49 (0.39; 0.39) | 36/12/32 (0.45; 0.53) | 34/25/21 (0.42; 0.62) |
| L40bde9ea | rolling | 67 (ref 12; dd ties 2; GATE number 0.60) | 27/0/40 (0.4; 0.4) | 35/0/32 (0.52; 0.52) | 40/2/25 (0.6; 0.62) | 42/3/22 (0.63; 0.66) |
| L40bde9ea | fixed c6 | 79 (ref 0; dd ties 4; GATE number 0.68) | 38/0/41 (0.48; 0.48) | 38/0/41 (0.48; 0.48) | 51/4/24 (0.65; 0.68) | 49/5/25 (0.62; 0.66) |
| L65a26c02 | rolling | 69 (ref 10; dd ties 8; GATE number 0.64) | 34/3/32 (0.49; 0.52) | 45/0/24 (0.65; 0.65) | 40/8/21 (0.58; 0.66) | 39/12/18 (0.57; 0.68) |
| L65a26c02 | fixed c1 | 79 (ref 0; dd ties 16; GATE number 0.68) | 38/9/32 (0.48; 0.54) | 52/0/27 (0.66; 0.66) | 44/16/19 (0.56; 0.7) | 41/24/14 (0.52; 0.75) |
| La010c3eb | rolling | 65 (ref 15; dd ties 6; GATE number 0.66) | 30/1/34 (0.46; 0.47) | 39/0/26 (0.6; 0.6) | 41/6/18 (0.63; 0.69) | 33/10/22 (0.51; 0.6) |
| La010c3eb | fixed c3 | 80 (ref 0; dd ties 12; GATE number 0.64) | 39/0/41 (0.49; 0.49) | 39/0/41 (0.49; 0.49) | 48/12/20 (0.6; 0.71) | 38/33/9 (0.47; 0.81) |
| Lc754cf58 | rolling | 63 (ref 17; dd ties 18; GATE number 0.46) | 23/2/38 (0.37; 0.38) | 26/0/37 (0.41; 0.41) | 23/18/22 (0.37; 0.51) | 20/30/13 (0.32; 0.61) |
| Lc754cf58 | fixed c7 | 80 (ref 0; dd ties 22; GATE number 0.49) | 31/1/48 (0.39; 0.39) | 31/0/49 (0.39; 0.39) | 31/22/27 (0.39; 0.53) | 32/34/14 (0.4; 0.7) |
| Ma010c3eb | rolling | 65 (ref 14; dd ties 15; GATE number 0.54) | 20/1/44 (0.31; 0.31) | 29/0/36 (0.45; 0.45) | 31/15/19 (0.48; 0.62) | 31/19/15 (0.48; 0.67) |
| Ma010c3eb | fixed c6 | 79 (ref 0; dd ties 13; GATE number 0.62) | 25/2/52 (0.32; 0.32) | 25/0/54 (0.32; 0.32) | 46/13/20 (0.58; 0.7) | 46/13/20 (0.58; 0.7) |
| Mcae177ba | rolling | 75 (ref 4; dd ties 19; GATE number 0.69) | 34/3/38 (0.45; 0.47) | 41/0/34 (0.55; 0.55) | 40/19/16 (0.53; 0.71) | 29/33/13 (0.39; 0.69) |
| Mcae177ba | fixed c2 | 79 (ref 0; dd ties 15; GATE number 0.58) | 32/8/39 (0.41; 0.45) | 38/0/41 (0.48; 0.48) | 37/15/27 (0.47; 0.58) | 29/32/18 (0.37; 0.62) |
| L385f4f2e | rolling | 78 (ref 1; dd ties 14; GATE number 0.58) | 32/3/43 (0.41; 0.43) | 39/0/39 (0.5; 0.5) | 42/14/22 (0.54; 0.66) | 40/22/16 (0.51; 0.71) |
| L385f4f2e | fixed c3 | 79 (ref 0; dd ties 16; GATE number 0.61) | 34/1/44 (0.43; 0.44) | 33/0/46 (0.42; 0.42) | 46/16/17 (0.58; 0.73) | 33/40/6 (0.42; 0.85) |
| M7ea48296 | rolling | 68 (ref 11; dd ties 6; GATE number 0.60) | 35/3/30 (0.51; 0.54) | 37/0/31 (0.54; 0.54) | 38/6/24 (0.56; 0.61) | 38/14/16 (0.56; 0.7) |
| M7ea48296 | fixed c2 | 79 (ref 0; dd ties 28; GATE number 0.52) | 31/4/44 (0.39; 0.41) | 29/0/50 (0.37; 0.37) | 31/28/20 (0.39; 0.61) | 25/47/7 (0.32; 0.78) |
| L9e4754b9 | rolling | 75 (ref 4; dd ties 8; GATE number 0.59) | 35/1/39 (0.47; 0.47) | 37/0/38 (0.49; 0.49) | 41/8/26 (0.55; 0.61) | 48/11/16 (0.64; 0.75) |
| L9e4754b9 | fixed c3 | 79 (ref 0; dd ties 3; GATE number 0.59) | 29/0/50 (0.37; 0.37) | 35/0/44 (0.44; 0.44) | 47/3/29 (0.59; 0.62) | 54/6/19 (0.68; 0.74) |
| M86781ac0 | rolling | 75 (ref 4; dd ties 10; GATE number 0.60) | 32/2/41 (0.43; 0.44) | 40/0/35 (0.53; 0.53) | 40/10/25 (0.53; 0.62) | 43/15/17 (0.57; 0.72) |
| M86781ac0 | fixed c8 | 79 (ref 0; dd ties 9; GATE number 0.65) | 32/2/45 (0.41; 0.42) | 39/0/40 (0.49; 0.49) | 47/9/23 (0.59; 0.67) | 53/11/15 (0.67; 0.78) |
| L018fb0c0 | rolling | 54 (ref 25; dd ties 19; GATE number 0.54) | 25/4/25 (0.46; 0.5) | 28/0/26 (0.52; 0.52) | 17/19/18 (0.31; 0.49) | 14/26/14 (0.26; 0.5) |
| L018fb0c0 | fixed c1 | 79 (ref 0; dd ties 25; GATE number 0.63) | 31/15/33 (0.39; 0.48) | 36/0/43 (0.46; 0.46) | 31/25/23 (0.39; 0.57) | 24/31/24 (0.3; 0.5) |
| L130cb48e | rolling | 63 (ref 16; dd ties 19; GATE number 0.67) | 29/13/21 (0.46; 0.58) | 37/0/26 (0.59; 0.59) | 26/19/18 (0.41; 0.59) | 22/28/13 (0.35; 0.63) |
| L130cb48e | fixed c2 | 79 (ref 0; dd ties 55; GATE number 0.63) | 18/30/31 (0.23; 0.37) | 32/0/47 (0.41; 0.41) | 12/55/12 (0.15; 0.5) | 2/72/5 (0.03; 0.29) |
| L3a2258bd | rolling | 66 (ref 14; dd ties 9; GATE number 0.52) | 30/2/34 (0.45; 0.47) | 33/0/33 (0.5; 0.5) | 31/9/26 (0.47; 0.54) | 29/12/25 (0.44; 0.54) |
| L3a2258bd | fixed c3 | 80 (ref 0; dd ties 9; GATE number 0.54) | 35/2/43 (0.44; 0.45) | 38/0/42 (0.47; 0.47) | 38/9/33 (0.47; 0.54) | 41/11/28 (0.51; 0.59) |
| La776664b | rolling | 79 (ref 1; dd ties 9; GATE number 0.53) | 29/2/48 (0.37; 0.38) | 36/0/43 (0.46; 0.46) | 39/9/31 (0.49; 0.56) | 37/21/21 (0.47; 0.64) |
| La776664b | fixed c4 | 80 (ref 0; dd ties 0; GATE number 0.60) | 28/0/52 (0.35; 0.35) | 28/0/52 (0.35; 0.35) | 48/0/32 (0.6; 0.6) | 64/0/16 (0.8; 0.8) |

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
| L1edb9fab | c8 | 5519 -> 3811 | -17635 -> -11861 | -10067 -> -6431 | 816 -> 851 |
| L3faac8df | c8 | 8631 -> 5701 | -31484 -> -21293 | -8508 -> -6766 | 344 -> 632 |
| L7f41b347 | c2 | 11233 -> 8028 | -39305 -> -24112 | -10332 -> -7705 | 643 -> 639 |
| Lcbc8a7ec | c5 | 10303 -> 5590 | -35613 -> -17336 | -6592 -> -6333 | 590 -> 785 |
| L973b5c8a | c1 | 6118 -> 4233 | -18853 -> -15691 | -9568 -> -7328 | 657 -> 787 |
| Lb68a132d | c1 | 3768 -> 3936 | -16489 -> -11713 | -10932 -> -5718 | 700 -> 539 |
| L5dee2059 | c4 | 8662 -> 7357 | -26333 -> -22971 | -10374 -> -10374 | 568 -> 774 |
| L29b1bc3f | c1 | 10632 -> 11904 | -35939 -> -31141 | -14882 -> -9372 | 495 -> 167 |
| L40bde9ea | c6 | 7366 -> 5049 | -25465 -> -12267 | -11382 -> -5906 | 577 -> 515 |
| L65a26c02 | c1 | 7705 -> 5462 | -21622 -> -18532 | -9537 -> -8503 | 767 -> 851 |
| La010c3eb | c3 | 8437 -> 4322 | -23200 -> -12503 | -13027 -> -7221 | 415 -> 385 |
| Lc754cf58 | c7 | 12523 -> 15286 | -41515 -> -34923 | -7248 -> -7164 | 639 -> 268 |
| Ma010c3eb | c6 | 3861 -> 5016 | -13834 -> -13868 | -6469 -> -7008 | 415 -> 201 |
| Mcae177ba | c2 | 3694 -> 3752 | -11700 -> -11054 | -4804 -> -3925 | 319 -> 279 |
| L385f4f2e | c3 | 5613 -> 5837 | -14755 -> -17731 | -6244 -> -3824 | 282 -> 222 |
| M7ea48296 | c2 | 4414 -> 4653 | -15019 -> -15089 | -6609 -> -5844 | 427 -> 388 |
| L9e4754b9 | c3 | 12374 -> 15510 | -31253 -> -30222 | -15676 -> -11081 | 442 -> 322 |
| M86781ac0 | c8 | 4458 -> 5432 | -13220 -> -17691 | -7783 -> -5358 | 355 -> 319 |
| L018fb0c0 | c1 | 5343 -> 6907 | -15162 -> -24650 | -8829 -> -10290 | 384 -> 276 |
| L130cb48e | c2 | 7888 -> 10901 | -20725 -> -23589 | -7867 -> -7267 | 319 -> 240 |
| L3a2258bd | c3 | 11293 -> 10242 | -34278 -> -38587 | -13119 -> -15748 | 447 -> 405 |
| La776664b | c4 | 4891 -> 8516 | -13257 -> -17943 | -6108 -> -5635 | 465 -> 101 |

### Year table behind the colours (information only)

Per period, unfitted -> joint pick at 1 lot. k = equal-risk factor = unfitted ulcer / pick ulcer in that period; equal-risk $/wk of the pick = pick $/wk x k, compared with the unfitted $/wk. The 30% band (AMBER 15-30, RED > 30) is applied to (unfitted $/wk - pick equal-risk $/wk) / |unfitted $/wk|; positive = pick worse. L6M and L3M have no colour. RED-year TYPE (drawdown = period max DD at 1 lot): (a) pick worse on BOTH drawdown and $/wk, (b) drawdown lower but $/wk lower (the unfitted $/wk of that year is shown so a tiny base is visible), (c) drawdown higher but $/wk higher.

| book | period | ulcer | max DD | worst week | $/wk 1 lot | k | equal-risk $/wk (pick vs unfitted) | band % | colour (RED type) |
|---|---|---|---|---|---|---|---|---|---|
| L578701ed | 2023 | 1637 -> 1539 | -5613 -> -4658 | -2829 -> -2744 | 754 -> 724 | 1.06 | 770 vs 754 | -2% | GREEN |
| L578701ed | 2024 | 13017 -> 7976 | -26575 -> -19113 | -4735 -> -3524 | 40 -> 297 | 1.63 | 485 vs 40 | -1118% | GREEN |
| L578701ed | 2025 | 5360 -> 4332 | -15319 -> -11579 | -6373 -> -7401 | 530 -> 619 | 1.24 | 766 vs 530 | -45% | GREEN |
| L578701ed | L6M | 5315 -> 3060 | -13108 -> -8578 | -6603 -> -6570 | 2207 -> 1794 | 1.74 | 3116 vs 2207 | -41% | shown only |
| L578701ed | L3M | 6964 -> 2839 | -13108 -> -6353 | -5103 -> -3430 | 614 -> 1108 | 2.45 | 2719 vs 614 | -343% | shown only |
| Lff52ec0c | 2023 | 3082 -> 3138 | -7164 -> -7193 | -2894 -> -2894 | 413 -> 401 | 0.98 | 394 vs 413 | +4% | GREEN |
| Lff52ec0c | 2024 | 3646 -> 4093 | -11901 -> -13135 | -4018 -> -3103 | 549 -> 450 | 0.89 | 401 vs 549 | +27% | AMBER |
| Lff52ec0c | 2025 | 10881 -> 12542 | -23231 -> -24047 | -6343 -> -6691 | 569 -> 211 | 0.87 | 183 vs 569 | +68% | RED (a; unfitted \$/wk that year 569) |
| Lff52ec0c | L6M | 3866 -> 2403 | -12103 -> -7088 | -7121 -> -4756 | 1882 -> 2436 | 1.61 | 3919 vs 1882 | -108% | shown only |
| Lff52ec0c | L3M | 4063 -> 1852 | -12103 -> -5583 | -7121 -> -4756 | 1357 -> 2013 | 2.19 | 4417 vs 1357 | -225% | shown only |
| L7c368a4f | 2023 | 4020 -> 4953 | -9990 -> -12239 | -2484 -> -3539 | 203 -> 163 | 0.81 | 132 vs 203 | +35% | RED (a; unfitted \$/wk that year 203) |
| L7c368a4f | 2024 | 4646 -> 5311 | -11465 -> -14284 | -2843 -> -4097 | 654 -> 327 | 0.87 | 286 vs 654 | +56% | RED (a; unfitted \$/wk that year 654) |
| L7c368a4f | 2025 | 5907 -> 15505 | -14312 -> -33026 | -10102 -> -9514 | 528 -> -678 | 0.38 | -258 vs 528 | +149% | RED (a; unfitted \$/wk that year 528) |
| L7c368a4f | L6M | 4075 -> 2890 | -11123 -> -8351 | -7409 -> -5705 | 2456 -> 1632 | 1.41 | 2301 vs 2456 | +6% | shown only |
| L7c368a4f | L3M | 2028 -> 2240 | -5118 -> -6674 | -3617 -> -3034 | 2434 -> 2011 | 0.91 | 1820 vs 2434 | +25% | shown only |
| L9aa7805c | 2023 | 2511 -> 3075 | -5275 -> -5801 | -2454 -> -2578 | 194 -> 184 | 0.82 | 150 vs 194 | +23% | AMBER |
| L9aa7805c | 2024 | 6943 -> 2375 | -15494 -> -6214 | -4279 -> -4279 | 318 -> 568 | 2.92 | 1661 vs 318 | -423% | GREEN |
| L9aa7805c | 2025 | 5890 -> 4755 | -12615 -> -13936 | -8408 -> -6545 | 896 -> 836 | 1.24 | 1036 vs 896 | -16% | GREEN |
| L9aa7805c | L6M | 3604 -> 2748 | -8595 -> -7115 | -6065 -> -5605 | 1691 -> 1987 | 1.31 | 2606 vs 1691 | -54% | shown only |
| L9aa7805c | L3M | 3141 -> 2932 | -6337 -> -7115 | -2953 -> -2327 | 1635 -> 2252 | 1.07 | 2413 vs 1635 | -48% | shown only |
| M7423c0d9 | 2023 | 2167 -> 2537 | -5063 -> -5783 | -2364 -> -2364 | 22 -> -40 | 0.85 | -34 vs 22 | +251% | RED (a; unfitted \$/wk that year 22) |
| M7423c0d9 | 2024 | 6289 -> 6475 | -15815 -> -15540 | -7354 -> -7200 | 74 -> 104 | 0.97 | 101 vs 74 | -36% | GREEN |
| M7423c0d9 | 2025 | 2882 -> 4239 | -8106 -> -9305 | -5229 -> -5229 | 458 -> 131 | 0.68 | 89 vs 458 | +80% | RED (a; unfitted \$/wk that year 458) |
| M7423c0d9 | L6M | 3256 -> 2997 | -9723 -> -7777 | -3649 -> -3717 | 1055 -> 1446 | 1.09 | 1571 vs 1055 | -49% | shown only |
| M7423c0d9 | L3M | 3554 -> 3589 | -9723 -> -7777 | -3329 -> -3717 | 860 -> 733 | 0.99 | 726 vs 860 | +16% | shown only |
| L15f14deb | 2023 | 4570 -> 4991 | -9046 -> -11791 | -3244 -> -4523 | 58 -> -45 | 0.92 | -41 vs 58 | +171% | RED (a; unfitted \$/wk that year 58) |
| L15f14deb | 2024 | 9445 -> 5075 | -20897 -> -11203 | -5823 -> -5143 | 80 -> 129 | 1.86 | 240 vs 80 | -198% | GREEN |
| L15f14deb | 2025 | 9894 -> 9705 | -20054 -> -18144 | -7537 -> -6781 | 795 -> 370 | 1.02 | 377 vs 795 | +53% | RED (b; unfitted \$/wk that year 795) |
| L15f14deb | L6M | 3329 -> 2519 | -9477 -> -7311 | -6922 -> -5391 | 1482 -> 1748 | 1.32 | 2310 vs 1482 | -56% | shown only |
| L15f14deb | L3M | 3086 -> 2711 | -8048 -> -7311 | -6922 -> -5391 | 1208 -> 1250 | 1.14 | 1423 vs 1208 | -18% | shown only |
| L1756b913 | 2023 | 5635 -> 5925 | -12885 -> -13530 | -3669 -> -3669 | 134 -> 111 | 0.95 | 105 vs 134 | +21% | AMBER |
| L1756b913 | 2024 | 4046 -> 8032 | -10075 -> -17185 | -3389 -> -4672 | 236 -> 69 | 0.50 | 35 vs 236 | +85% | RED (a; unfitted \$/wk that year 236) |
| L1756b913 | 2025 | 6325 -> 9063 | -13751 -> -17843 | -6112 -> -9702 | 456 -> -43 | 0.70 | -30 vs 456 | +107% | RED (a; unfitted \$/wk that year 456) |
| L1756b913 | L6M | 4678 -> 3164 | -12916 -> -9855 | -5830 -> -5450 | 2107 -> 2076 | 1.48 | 3069 vs 2107 | -46% | shown only |
| L1756b913 | L3M | 2256 -> 2895 | -8379 -> -9855 | -5830 -> -5450 | 3272 -> 2235 | 0.78 | 1741 vs 3272 | +47% | shown only |
| L3faac8df | 2023 | 1417 -> 1687 | -4361 -> -4346 | -2239 -> -2139 | 278 -> 148 | 0.84 | 124 vs 278 | +55% | RED (b; unfitted \$/wk that year 278) |
| L3faac8df | 2024 | 8911 -> 5282 | -18852 -> -11640 | -8318 -> -5578 | 44 -> 258 | 1.69 | 436 vs 44 | -900% | GREEN |
| L3faac8df | 2025 | 3347 -> 7747 | -9730 -> -20191 | -3724 -> -6766 | 489 -> 171 | 0.43 | 74 vs 489 | +85% | RED (a; unfitted \$/wk that year 489) |
| L3faac8df | L6M | 4512 -> 2325 | -10962 -> -6452 | -6156 -> -3877 | 1314 -> 2597 | 1.94 | 5041 vs 1314 | -284% | shown only |
| L3faac8df | L3M | 5238 -> 2762 | -10962 -> -5763 | -5843 -> -3877 | 1186 -> 1970 | 1.90 | 3735 vs 1186 | -215% | shown only |
| L7f41b347 | 2023 | 2920 -> 2940 | -7194 -> -7223 | -2909 -> -2909 | 452 -> 445 | 0.99 | 442 vs 452 | +2% | GREEN |
| L7f41b347 | 2024 | 3624 -> 4171 | -11841 -> -13001 | -4068 -> -4209 | 546 -> 405 | 0.87 | 352 vs 546 | +36% | RED (a; unfitted \$/wk that year 546) |
| L7f41b347 | 2025 | 11064 -> 12135 | -23671 -> -24112 | -5459 -> -5467 | 463 -> 256 | 0.91 | 234 vs 463 | +49% | RED (a; unfitted \$/wk that year 463) |
| L7f41b347 | L6M | 4173 -> 2705 | -12464 -> -8020 | -8251 -> -5052 | 2095 -> 2331 | 1.54 | 3597 vs 2095 | -72% | shown only |
| L7f41b347 | L3M | 3104 -> 2232 | -10981 -> -5883 | -5640 -> -5052 | 1738 -> 1763 | 1.39 | 2452 vs 1738 | -41% | shown only |
| Lcbc8a7ec | 2023 | 1350 -> 1960 | -3733 -> -5892 | -2769 -> -3769 | 560 -> 577 | 0.69 | 397 vs 560 | +29% | AMBER |
| Lcbc8a7ec | 2024 | 3668 -> 3805 | -9686 -> -11578 | -3938 -> -4008 | 239 -> 227 | 0.96 | 219 vs 239 | +8% | GREEN |
| Lcbc8a7ec | 2025 | 10378 -> 8645 | -22076 -> -17336 | -5459 -> -6333 | 550 -> 262 | 1.20 | 314 vs 550 | +43% | RED (b; unfitted \$/wk that year 550) |
| Lcbc8a7ec | L6M | 4828 -> 1691 | -11760 -> -5243 | -6066 -> -3950 | 1880 -> 2681 | 2.86 | 7656 vs 1880 | -307% | shown only |
| Lcbc8a7ec | L3M | 2664 -> 1524 | -8143 -> -4521 | -6001 -> -3285 | 2105 -> 1932 | 1.75 | 3377 vs 2105 | -60% | shown only |
| L973b5c8a | 2023 | 3462 -> 3593 | -8180 -> -7201 | -1989 -> -2195 | 257 -> 185 | 0.96 | 178 vs 257 | +31% | RED (b; unfitted \$/wk that year 257) |
| L973b5c8a | 2024 | 5262 -> 3349 | -12391 -> -7776 | -3853 -> -3378 | 359 -> 200 | 1.57 | 315 vs 359 | +12% | GREEN |
| L973b5c8a | 2025 | 8839 -> 6126 | -18853 -> -15691 | -9568 -> -5707 | 771 -> 1073 | 1.44 | 1548 vs 771 | -101% | GREEN |
| L973b5c8a | L6M | 3886 -> 3153 | -12660 -> -9655 | -5576 -> -5352 | 1211 -> 1586 | 1.23 | 1955 vs 1211 | -62% | shown only |
| L973b5c8a | L3M | 3189 -> 2806 | -8198 -> -6487 | -5557 -> -2785 | 1310 -> 1635 | 1.14 | 1858 vs 1310 | -42% | shown only |
| Lb68a132d | 2023 | 1878 -> 1388 | -4585 -> -3935 | -2854 -> -2657 | 265 -> 428 | 1.35 | 579 vs 265 | -118% | GREEN |
| Lb68a132d | 2024 | 3708 -> 4543 | -10169 -> -11077 | -2469 -> -3788 | 510 -> 358 | 0.82 | 292 vs 510 | +43% | RED (a; unfitted \$/wk that year 510) |
| Lb68a132d | 2025 | 2747 -> 4132 | -7263 -> -11713 | -4094 -> -5707 | 900 -> 437 | 0.66 | 291 vs 900 | +68% | RED (a; unfitted \$/wk that year 900) |
| Lb68a132d | L6M | 3158 -> 1581 | -8621 -> -4669 | -3718 -> -2987 | 1090 -> 1197 | 2.00 | 2392 vs 1090 | -120% | shown only |
| Lb68a132d | L3M | 2757 -> 1557 | -6498 -> -3628 | -2303 -> -1673 | 1273 -> 909 | 1.77 | 1610 vs 1273 | -26% | shown only |
| L5dee2059 | 2023 | 4780 -> 5341 | -8006 -> -9040 | -2614 -> -2969 | 128 -> 58 | 0.90 | 52 vs 128 | +59% | RED (a; unfitted \$/wk that year 128) |
| L5dee2059 | 2024 | 7954 -> 7037 | -18967 -> -16307 | -8189 -> -7320 | 463 -> 719 | 1.13 | 813 vs 463 | -75% | GREEN |
| L5dee2059 | 2025 | 7553 -> 6416 | -18614 -> -16446 | -10374 -> -10374 | 598 -> 1069 | 1.18 | 1259 vs 598 | -110% | GREEN |
| L5dee2059 | L6M | 7196 -> 4360 | -18906 -> -11539 | -7002 -> -8000 | 1142 -> 1397 | 1.65 | 2305 vs 1142 | -102% | shown only |
| L5dee2059 | L3M | 5330 -> 5163 | -11736 -> -11539 | -4698 -> -3224 | 1986 -> 991 | 1.03 | 1023 vs 1986 | +49% | shown only |
| L29b1bc3f | 2023 | 5094 -> 4712 | -11269 -> -10807 | -4189 -> -3244 | 41 -> 25 | 1.08 | 27 vs 41 | +32% | RED (b; unfitted \$/wk that year 41) |
| L29b1bc3f | 2024 | 7772 -> 7231 | -22011 -> -15916 | -4833 -> -3173 | 301 -> 143 | 1.07 | 153 vs 301 | +49% | RED (b; unfitted \$/wk that year 301) |
| L29b1bc3f | 2025 | 9540 -> 9537 | -19426 -> -18767 | -14882 -> -7577 | 326 -> -82 | 1.00 | -82 vs 326 | +125% | RED (b; unfitted \$/wk that year 326) |
| L29b1bc3f | L6M | 4118 -> 2619 | -12090 -> -6911 | -3767 -> -3743 | 1293 -> 945 | 1.57 | 1485 vs 1293 | -15% | shown only |
| L29b1bc3f | L3M | 4744 -> 2032 | -12090 -> -5907 | -3767 -> -3490 | 954 -> 1327 | 2.33 | 3099 vs 954 | -225% | shown only |
| L40bde9ea | 2023 | 6114 -> 4798 | -11150 -> -8963 | -3278 -> -4403 | 36 -> 90 | 1.27 | 115 vs 36 | -222% | GREEN |
| L40bde9ea | 2024 | 6670 -> 5284 | -15506 -> -12178 | -4899 -> -3668 | 381 -> 207 | 1.26 | 261 vs 381 | +32% | RED (b; unfitted \$/wk that year 381) |
| L40bde9ea | 2025 | 6875 -> 5106 | -16529 -> -11014 | -11382 -> -5906 | 835 -> 586 | 1.35 | 789 vs 835 | +5% | GREEN |
| L40bde9ea | L6M | 4695 -> 2894 | -11790 -> -6338 | -5577 -> -3440 | 937 -> 893 | 1.62 | 1449 vs 937 | -55% | shown only |
| L40bde9ea | L3M | 3391 -> 2784 | -11743 -> -5941 | -3112 -> -1687 | 1664 -> 622 | 1.22 | 758 vs 1664 | +54% | shown only |
| La010c3eb | 2023 | 1423 -> 2157 | -4049 -> -5109 | -2799 -> -2629 | 447 -> 285 | 0.66 | 188 vs 447 | +58% | RED (a; unfitted \$/wk that year 447) |
| La010c3eb | 2024 | 6084 -> 2782 | -16271 -> -9047 | -5479 -> -4728 | 414 -> 534 | 2.19 | 1169 vs 414 | -182% | GREEN |
| La010c3eb | 2025 | 9333 -> 6637 | -19727 -> -12429 | -6193 -> -4598 | 90 -> -89 | 1.41 | -126 vs 90 | +240% | RED (b; unfitted \$/wk that year 90) |
| La010c3eb | L6M | 3973 -> 2767 | -12959 -> -6428 | -3947 -> -3703 | 861 -> 801 | 1.44 | 1151 vs 861 | -34% | shown only |
| La010c3eb | L3M | 3181 -> 2916 | -8483 -> -6428 | -3653 -> -2858 | 906 -> 678 | 1.09 | 740 vs 906 | +18% | shown only |
| Lc754cf58 | 2023 | 1994 -> 1945 | -5606 -> -5891 | -2269 -> -2304 | 491 -> 489 | 1.02 | 501 vs 491 | -2% | GREEN |
| Lc754cf58 | 2024 | 10077 -> 11400 | -26344 -> -27300 | -5064 -> -4782 | 520 -> 31 | 0.88 | 27 vs 520 | +95% | RED (a; unfitted \$/wk that year 520) |
| Lc754cf58 | 2025 | 12157 -> 9132 | -23967 -> -19375 | -7014 -> -7164 | 133 -> 49 | 1.33 | 65 vs 133 | +51% | RED (b; unfitted \$/wk that year 133) |
| Lc754cf58 | L6M | 5349 -> 3249 | -12403 -> -10361 | -7248 -> -5078 | 1368 -> 921 | 1.65 | 1516 vs 1368 | -11% | shown only |
| Lc754cf58 | L3M | 6362 -> 2622 | -11856 -> -5731 | -6519 -> -4397 | 431 -> 785 | 2.43 | 1904 vs 431 | -342% | shown only |
| Ma010c3eb | 2023 | 2726 -> 2313 | -5762 -> -4627 | -3129 -> -1864 | 142 -> 73 | 1.18 | 86 vs 142 | +39% | RED (b; unfitted \$/wk that year 142) |
| Ma010c3eb | 2024 | 5205 -> 5627 | -13834 -> -13868 | -6469 -> -6129 | 254 -> 128 | 0.92 | 118 vs 254 | +53% | RED (a; unfitted \$/wk that year 254) |
| Ma010c3eb | 2025 | 2488 -> 3998 | -8162 -> -8915 | -3199 -> -2878 | 458 -> 148 | 0.62 | 92 vs 458 | +80% | RED (a; unfitted \$/wk that year 458) |
| Ma010c3eb | L6M | 3630 -> 2389 | -9085 -> -5732 | -4849 -> -2598 | 705 -> 267 | 1.52 | 405 vs 705 | +43% | shown only |
| Ma010c3eb | L3M | 3441 -> 1501 | -9085 -> -4616 | -4849 -> -1099 | 706 -> 643 | 2.29 | 1474 vs 706 | -109% | shown only |
| Mcae177ba | 2023 | 2315 -> 2299 | -5102 -> -4922 | -2529 -> -2449 | 147 -> 83 | 1.01 | 84 vs 147 | +43% | RED (b; unfitted \$/wk that year 147) |
| Mcae177ba | 2024 | 2674 -> 3208 | -7291 -> -7504 | -2405 -> -3846 | 503 -> 358 | 0.83 | 299 vs 503 | +41% | RED (a; unfitted \$/wk that year 503) |
| Mcae177ba | 2025 | 4111 -> 4590 | -9515 -> -10680 | -3779 -> -3621 | 182 -> 126 | 0.90 | 113 vs 182 | +38% | RED (a; unfitted \$/wk that year 182) |
| Mcae177ba | L6M | 3657 -> 2997 | -8184 -> -8776 | -4103 -> -3625 | 341 -> 270 | 1.22 | 329 vs 341 | +3% | shown only |
| Mcae177ba | L3M | 4151 -> 3196 | -8184 -> -8776 | -2623 -> -2524 | 22 -> 118 | 1.30 | 153 vs 22 | -598% | shown only |
| L385f4f2e | 2023 | 3702 -> 2967 | -8225 -> -7552 | -3154 -> -3229 | 42 -> 65 | 1.25 | 81 vs 42 | -93% | GREEN |
| L385f4f2e | 2024 | 4946 -> 5366 | -12529 -> -12937 | -2619 -> -3119 | 189 -> 50 | 0.92 | 46 vs 189 | +76% | RED (a; unfitted \$/wk that year 189) |
| L385f4f2e | 2025 | 4191 -> 4109 | -11277 -> -9172 | -6244 -> -3824 | 502 -> 378 | 1.02 | 385 vs 502 | +23% | AMBER |
| L385f4f2e | L6M | 3905 -> 1868 | -9711 -> -5650 | -2988 -> -3163 | 476 -> 449 | 2.09 | 938 vs 476 | -97% | shown only |
| L385f4f2e | L3M | 2438 -> 1265 | -6959 -> -3872 | -2783 -> -2178 | 457 -> 970 | 1.93 | 1870 vs 457 | -309% | shown only |
| M7ea48296 | 2023 | 3183 -> 3604 | -6062 -> -6808 | -3814 -> -3478 | 115 -> 85 | 0.88 | 75 vs 115 | +35% | RED (a; unfitted \$/wk that year 115) |
| M7ea48296 | 2024 | 2918 -> 3127 | -9903 -> -10872 | -6609 -> -5844 | 644 -> 383 | 0.93 | 357 vs 644 | +44% | RED (a; unfitted \$/wk that year 644) |
| M7ea48296 | 2025 | 3756 -> 3185 | -8342 -> -8559 | -4513 -> -4763 | 318 -> 394 | 1.18 | 465 vs 318 | -46% | GREEN |
| M7ea48296 | L6M | 4797 -> 2515 | -10752 -> -7019 | -6272 -> -3512 | 429 -> 915 | 1.91 | 1745 vs 429 | -307% | shown only |
| M7ea48296 | L3M | 3328 -> 2259 | -8673 -> -6223 | -2524 -> -3512 | 862 -> 1611 | 1.47 | 2374 vs 862 | -175% | shown only |
| L9e4754b9 | 2023 | 3067 -> 3703 | -6458 -> -6840 | -3089 -> -3063 | 326 -> 246 | 0.83 | 204 vs 326 | +37% | RED (a; unfitted \$/wk that year 326) |
| L9e4754b9 | 2024 | 10587 -> 10342 | -28099 -> -23292 | -4689 -> -3806 | 257 -> 221 | 1.02 | 226 vs 257 | +12% | GREEN |
| L9e4754b9 | 2025 | 11626 -> 12118 | -24685 -> -18636 | -10527 -> -11081 | 196 -> -129 | 0.96 | -124 vs 196 | +163% | RED (b; unfitted \$/wk that year 196) |
| L9e4754b9 | L6M | 3777 -> 2039 | -9857 -> -5237 | -7285 -> -2603 | 1218 -> 1452 | 1.85 | 2691 vs 1218 | -121% | shown only |
| L9e4754b9 | L3M | 3434 -> 2197 | -9468 -> -5237 | -4287 -> -2326 | 1118 -> 1933 | 1.56 | 3021 vs 1118 | -170% | shown only |
| M86781ac0 | 2023 | 2658 -> 2933 | -6085 -> -5756 | -1949 -> -2119 | 43 -> 27 | 0.91 | 25 vs 43 | +42% | RED (b; unfitted \$/wk that year 43) |
| M86781ac0 | 2024 | 3975 -> 2252 | -10191 -> -6909 | -5364 -> -4404 | 426 -> 372 | 1.76 | 657 vs 426 | -54% | GREEN |
| M86781ac0 | 2025 | 3205 -> 7919 | -8724 -> -15951 | -2919 -> -4676 | 323 -> -32 | 0.40 | -13 vs 323 | +104% | RED (a; unfitted \$/wk that year 323) |
| M86781ac0 | L6M | 3477 -> 2033 | -8810 -> -7354 | -5132 -> -5041 | 734 -> 1148 | 1.71 | 1964 vs 734 | -168% | shown only |
| M86781ac0 | L3M | 3461 -> 1367 | -7592 -> -3569 | -2694 -> -1769 | 439 -> 1483 | 2.53 | 3755 vs 439 | -755% | shown only |
| L018fb0c0 | 2023 | 3334 -> 3747 | -8238 -> -9073 | -3169 -> -3169 | 88 -> -16 | 0.89 | -14 vs 88 | +116% | RED (a; unfitted \$/wk that year 88) |
| L018fb0c0 | 2024 | 2537 -> 3230 | -7547 -> -9453 | -3019 -> -4319 | 510 -> 206 | 0.79 | 162 vs 510 | +68% | RED (a; unfitted \$/wk that year 510) |
| L018fb0c0 | 2025 | 7362 -> 6778 | -14606 -> -19767 | -5019 -> -8421 | 184 -> 200 | 1.09 | 217 vs 184 | -18% | GREEN |
| L018fb0c0 | L6M | 6637 -> 2963 | -15162 -> -8586 | -4854 -> -2601 | 617 -> 1443 | 2.24 | 3233 vs 617 | -424% | shown only |
| L018fb0c0 | L3M | 5968 -> 2428 | -11691 -> -6565 | -4854 -> -2601 | 1606 -> 1726 | 2.46 | 4243 vs 1606 | -164% | shown only |
| L130cb48e | 2023 | 1496 -> 1477 | -3538 -> -3538 | -1694 -> -1694 | 155 -> 163 | 1.01 | 166 vs 155 | -7% | GREEN |
| L130cb48e | 2024 | 5991 -> 6429 | -14665 -> -15429 | -5113 -> -4569 | 115 -> 91 | 0.93 | 85 vs 115 | +26% | AMBER |
| L130cb48e | 2025 | 6809 -> 7194 | -13230 -> -12470 | -4974 -> -4974 | 104 -> -39 | 0.95 | -37 vs 104 | +136% | RED (b; unfitted \$/wk that year 104) |
| L130cb48e | L6M | 4675 -> 3665 | -10940 -> -10220 | -5145 -> -5011 | 1465 -> 1260 | 1.28 | 1607 vs 1465 | -10% | shown only |
| L130cb48e | L3M | 5784 -> 3998 | -10940 -> -10220 | -4592 -> -4157 | 946 -> 1116 | 1.45 | 1615 vs 946 | -71% | shown only |
| La776664b | 2023 | 2935 -> 2283 | -6516 -> -4339 | -3579 -> -1291 | 301 -> 28 | 1.29 | 36 vs 301 | +88% | RED (b; unfitted \$/wk that year 301) |
| La776664b | 2024 | 4001 -> 6402 | -9325 -> -13431 | -3039 -> -3614 | 420 -> -42 | 0.62 | -26 vs 420 | +106% | RED (a; unfitted \$/wk that year 420) |
| La776664b | 2025 | 5556 -> 5601 | -11899 -> -9800 | -5079 -> -2702 | 340 -> -48 | 0.99 | -47 vs 340 | +114% | RED (b; unfitted \$/wk that year 340) |
| La776664b | L6M | 7008 -> 3951 | -13257 -> -7490 | -5084 -> -5635 | 576 -> 264 | 1.77 | 468 vs 576 | +19% | shown only |
| La776664b | L3M | 6869 -> 2553 | -10591 -> -5062 | -5084 -> -2511 | 579 -> 431 | 2.69 | 1161 vs 579 | -101% | shown only |

42-month totals (2023-04..2026-10, 1 lot), unfitted -> pick:

| book | ulcer | max DD | worst week | $/wk |
|---|---|---|---|---|
| L578701ed | 7983 -> 5201 | -26575 -> -19113 | -6603 -> -7401 | 763 -> 798 |
| Lff52ec0c | 8002 -> 8169 | -23231 -> -24047 | -10322 -> -7700 | 702 -> 643 |
| L7c368a4f | 5484 -> 20550 | -17690 -> -48969 | -10102 -> -9514 | 831 -> 284 |
| L9aa7805c | 6342 -> 3707 | -17159 -> -13936 | -8408 -> -9028 | 651 -> 917 |
| M7423c0d9 | 5160 -> 7710 | -16553 -> -19465 | -8104 -> -7200 | 379 -> 329 |
| L15f14deb | 9961 -> 7342 | -30358 -> -20225 | -7537 -> -10959 | 713 -> 553 |
| L1756b913 | 5597 -> 8328 | -13751 -> -24344 | -6112 -> -9702 | 746 -> 520 |
| L3faac8df | 8631 -> 5701 | -31484 -> -21293 | -8508 -> -6766 | 344 -> 632 |
| L7f41b347 | 11233 -> 8028 | -39305 -> -24112 | -10332 -> -7705 | 643 -> 639 |
| Lcbc8a7ec | 10303 -> 5590 | -35613 -> -17336 | -6592 -> -6333 | 590 -> 785 |
| L973b5c8a | 6118 -> 4233 | -18853 -> -15691 | -9568 -> -7328 | 657 -> 787 |
| Lb68a132d | 3768 -> 3936 | -16489 -> -11713 | -10932 -> -5718 | 700 -> 539 |
| L5dee2059 | 8662 -> 7357 | -26333 -> -22971 | -10374 -> -10374 | 568 -> 774 |
| L29b1bc3f | 10632 -> 11904 | -35939 -> -31141 | -14882 -> -9372 | 495 -> 167 |
| L40bde9ea | 7366 -> 5049 | -25465 -> -12267 | -11382 -> -5906 | 577 -> 515 |
| La010c3eb | 8437 -> 4322 | -23200 -> -12503 | -13027 -> -7221 | 415 -> 385 |
| Lc754cf58 | 12523 -> 15286 | -41515 -> -34923 | -7248 -> -7164 | 639 -> 268 |
| Ma010c3eb | 3861 -> 5016 | -13834 -> -13868 | -6469 -> -7008 | 415 -> 201 |
| Mcae177ba | 3694 -> 3752 | -11700 -> -11054 | -4804 -> -3925 | 319 -> 279 |
| L385f4f2e | 5613 -> 5837 | -14755 -> -17731 | -6244 -> -3824 | 282 -> 222 |
| M7ea48296 | 4414 -> 4653 | -15019 -> -15089 | -6609 -> -5844 | 427 -> 388 |
| L9e4754b9 | 12374 -> 15510 | -31253 -> -30222 | -15676 -> -11081 | 442 -> 322 |
| M86781ac0 | 4458 -> 5432 | -13220 -> -17691 | -7783 -> -5358 | 355 -> 319 |
| L018fb0c0 | 5343 -> 6907 | -15162 -> -24650 | -8829 -> -10290 | 384 -> 276 |
| L130cb48e | 7888 -> 10901 | -20725 -> -23589 | -7867 -> -7267 | 319 -> 240 |
| La776664b | 4891 -> 8516 | -13257 -> -17943 | -6108 -> -5635 | 465 -> 101 |

**SUMMARY (35 of 35 books complete, 0 KEPT):** NOT KEPT on rolling walk-forward (any reason incl. others): 18; on the RED-year band ONLY (walk-forward and null pass): 10; on the null ONLY: 1; RED years of the band-only group by type: (a) 9, (b) 8, (c) 0, other 0.
