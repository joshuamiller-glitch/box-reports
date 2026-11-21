# JOINT STAGE TABLE - Asia own-checks pool (W-LAYERS, STAMP 2026-11-21 05:18Z; refreshed every 15 min by joint_verdict.py --loop; only rows from the corrected JNT9 array count, the voided 80-combo run feeds nothing)

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
| L385f4f2e | pending: 5/8 combos complete (273/336 set-months) | | | | | | |
| M7ea48296 | pending: 3/8 combos complete (186/336 set-months) | | | | | | |
