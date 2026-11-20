# ASIA_STAGE1_TABLE - complete stage-1 verdict table, Asia own-checks pool unaffected-bar books (W-LAYERS, 2026-11-20 23:15Z)

Fitted = the four picks (BRK/LOSS/LOCK/TAKE, one per group, drawdown first) together on the book's own all-new base; unfitted = the book's BASE (today's settings). Cells are `ulcer fitted/unfitted; $/wk fitted/unfitted; eq = $/wk at equal risk (fitted scaled to the unfitted ulcer) / unfitted $/wk`, 1 lot. Walk-forward: fixed = share of 93 two-week periods the fitted pick beats unfitted (drawdown first); ROLLING = true trailing-26-week re-pick among top-3 per group + reference (the gate, >= 0.58). Year colours 2023/24/25 on the equal-risk $/wk change (GREEN <= 15%, AMBER 15-30%, RED > 30% fails). Null = real pick beats x of 5 search-aware null draws (needs >= 4; plain60/60 draws, one-book thinned). 27/30 luck controls = information only. KEPT = rolling WF >= 0.58 AND no RED year AND null >= 4/5.

| book | picks | L6M | L3M | WF fixed | WF rolling | years 23/24/25 | null | 27/30 (info) | verdict |
|---|---|---|---|---|---|---|---|---|---|
| L578701ed | BRK: BRK2; LOSS: FR_LOSS9; LOCK: LK2; TAKE: FR_TAKE4 | 3060/5315; 1794/2207; eq 3116/2207 | 2839/6964; 1108/614; eq 2719/614 | 0.581 | 0.588 | GREEN/GREEN/GREEN | 4/5 | 12/30 | KEPT: all gates met |
| Lff52ec0c | LOSS: CX3; LOCK: LK7; TAKE: FR_TAKE4 | 2594/3866; 2354/1882; eq 3509/1882 | 1873/4063; 2280/1357; eq 4947/1357 | 0.624 | 0.529 | GREEN/GREEN/RED | 4/5 | 15/30 | NOT KEPT: rolling WF 0.53 < 0.58; RED year |
| L7c368a4f | BRK: BRK2; LOCK: LK1 | 2415/4075; 2690/2456; eq 4539/2456 | 1914/2028; 2621/2434; eq 2776/2434 | 0.634 | 0.537 | GREEN/GREEN/GREEN | 4/5 | 15/30 | NOT KEPT: rolling WF 0.54 < 0.58 |
| L9aa7805c | LOSS: CX2; TAKE: NRT2 | 2571/3604; 1940/1691; eq 2720/1691 | 3221/3141; 1952/1635; eq 1903/1635 | 0.538 | 0.613 | RED/GREEN/AMBER | 4/5 | 20/30 | NOT KEPT: RED year |
| M7423c0d9 | LOSS: FR_LOSS9; TAKE: TK12 | 2455/3256; 1679/1055; eq 2227/1055 | 2916/3554; 1163/860; eq 1417/860 | 0.57 | 0.588 | AMBER/RED/RED | 4/5 | 19/30 | NOT KEPT: RED year |
| L15f14deb | BRK: BRK1; LOCK: LK8; TAKE: FR_TAKE4 | 4176/3329; 1417/1482; eq 1129/1482 | 3411/3086; 430/1208; eq 389/1208 | 0.538 | 0.562 | RED/GREEN/RED | 2/5 | 12/30 | NOT KEPT: rolling WF 0.56 < 0.58; RED year; null 2/5 |
| L1756b913 | BRK: BRK1; LOCK: LK7; TAKE: NRT3 | 4030/4678; 1238/2107; eq 1437/2107 | 3513/2256; 1107/3272; eq 711/3272 | 0.538 | 0.528 | GREEN/RED/RED | 3/5 | 17/30 | NOT KEPT: rolling WF 0.53 < 0.58; RED year; null 3/5 |
| L1edb9fab | BRK: BRK1; LOCK: LK1; TAKE: NRT3 | 5995/4509; 1210/2167; eq 910/2167 | 4402/2367; 1558/2289; eq 838/2289 | 0.505 | 0.575 | RED/GREEN/GREEN | 2/5 | 16/30 | NOT KEPT: rolling WF 0.57 < 0.58; RED year; null 2/5 |
| L3faac8df | BRK: BRK1; LOSS: CX3; TAKE: NRT4 | 2353/4512; 2571/1314; eq 4930/1314 | 2129/5238; 1998/1186; eq 4916/1186 | 0.677 | 0.693 | RED/GREEN/RED | 5/5 | 17/30 | NOT KEPT: RED year |
| L7f41b347 | LOSS: STC2; LOCK: LK7; TAKE: FR_TAKE4 | 4291/4173; 2374/2095; eq 2308/2095 | 1207/3104; 3020/1738; eq 7763/1738 | 0.71 | 0.562 | GREEN/RED/RED | 2/5 | 14/30 | NOT KEPT: rolling WF 0.56 < 0.58; RED year; null 2/5 |
| Lcbc8a7ec | BRK: BRK2; LOSS: CU2; TAKE: NRT1 | 2852/4828; 1684/1880; eq 2850/1880 | 2863/2664; 1080/2105; eq 1005/2105 | 0.57 | 0.52 | RED/RED/RED | 4/5 | 18/30 | NOT KEPT: rolling WF 0.52 < 0.58; RED year |
| L973b5c8a | LOSS: CX1 | 3078/3886; 1709/1211; eq 2158/1211 | 3038/3189; 1492/1310; eq 1567/1310 | 0.645 | 0.6 | AMBER/GREEN/GREEN | 4/5 | 19/30 | KEPT: all gates met |
| Lb68a132d | BRK: BRK3; LOSS: CX2; LOCK: LK2; TAKE: TK5 | 1890/3158; 833/1090; eq 1393/1090 | 1760/2757; 556/1273; eq 871/1273 | 0.587 | 0.471 | GREEN/AMBER/RED | 4/5 | 17/30 | NOT KEPT: rolling WF 0.47 < 0.58; RED year |
| Lec335094 | none | - | - | - | - | - | - | - | - | NOT KEPT: no setting passed the screen rule; keeps today's |
| L5dee2059 | BRK: BRK4; LOCK: LK1 | 5883/7196; 1173/1142; eq 1435/1142 | 4800/5330; 1303/1986; eq 1447/1986 | 0.591 | 0.722 | RED/GREEN/GREEN | 4/5 | 18/30 | NOT KEPT: RED year |

KEPT: L578701ed, L973b5c8a. Books with a book-level pick kept go forward with top 2-3 settings per layer + the reference row into the JOINT stage regardless (nothing dropped at the screen); the joint verdict decides.
Waiting for _CANC bases: L29b1bc3f, L7ea48296, Lcae177ba. Skipped (broken): 12.
