# DS3_TICK_BOOKS - new TICK books on NQ (W-TK2), research only, NO PASS claim. Built 2026-11-14 02:20 UTC

**VERDICT (plain):** Standalone NQ screen (5 books x 6 session units, 1,470-cell entry/stop/target/time grid, measured fills, real TICK vs TICK shifted 11/23/37 trading days): 9013 cells pass the both-window gate (L3M,L6M,HOLD,PRE,X' all > 0, enough trades) AND beat the same cell on the shifted-TICK placebos in recent and older windows; but these come from a 1.8M-cell search and only 2 of 22 book/unit families have a best cell above the best placebo-family cell, so the standalone evidence is WEAK (selection-dominated), and the literal directive book B1 at +/-1000 is too rare (<=20 trades/6 months) to pass any gate. Exact-engine injected stack numbers: not yet available (runs queued under admission tag TKB behind UW/UR/RU; box at worker cap).

Data: TICK 2023-04-03..2026-11-13, 911 sessions, 354,080 RTH bars; parse identical to W-TK1 tick_clean.parquet (max abs diff 0). Usable at bar end + 5 s. NQ 1-min price from the 1-s path. ES standalone only (hook NQ-only).

## 1. Books and generators (code/th_tickb/tkb_events.py; prereg sha in DECISIONS.md)
- B1 fade/follow TICK extremes, thr 600/800/1000, regime none / NQ ER(first 30 min)<0.30 / |mean TICK first 30 min|<100 / both.
- B2 persistent TICK (rolling mean L15/L30 >= 100/200/300 with share>0 >= 0.6), regime none or ER>=0.35, trigger onset or resumption (pullback of TICK back through 0); market/confirm entries only (no limit pullbacks: hook limit).
- B3 divergence: NQ new session high/low while TICK 10/20-min mean weak (<0 / <150), or no TICK extreme 400/600 in L minutes, or confirmed (C); fade and follow.
- B4 first-hour trend day: ER over first 30/60 min >= 0.30/0.45 (+ optional TICK confirm), market entry at the first pullback of 25%/40% of the move.
- Units: S1 09:30-10:00, S2 10:00-12:00, S3 12:00-14:30, S4 14:30-15:00 (live no-entry from 15:00), nyam, nypm. CLOCK baseline: every-day entries at 09:35/10:05/12:05/14:35.
- Selection (tolerant gate): L3M, L6M, HOLD > 0 standalone, n_L6M >= 15-20; both-window = PRE>0 and X'>0 too; edge = recents (L6M+HOLD)/2 minus the same cell on shifted TICK (mean of 3), edge_old likewise for (PRE+X')/2. Ranked by L6M Calmar (DD floor $1,200).

## 2. Best per book and per session (NQ standalone, harness; NOT the injected number)

| book | unit | tier | var | cell | dir | n_L6M | L3M | L6M | HOLD | PRE | X | dd_L6M | worst_L6M | edge_vs_placebo | rec_placebo | fam_null_max | beats_family_null | injectable |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B1 | S1 | both-window+placebo-edge | B1_t600_none_fade | Emkt_S90_T60_X120 | 0.0 | 27.0 | 219.0 | 304.0 | 69.0 | 129.0 | 159.0 | 3669.0 | -1814.0 | 150.0 | 36.0 | 1628.0 | False | True |
| B1 | S2 | both-window+placebo-edge | B1_t600_er_fade | Eb1_Sa2_T90_X30 | 0.0 | 20.0 | 343.0 | 721.0 | 542.0 | 104.0 | 5.0 | 749.0 | -749.0 | 679.0 | -47.0 | 1975.0 | False | True |
| B1 | S3 | both-window+placebo-edge | B1_t600_er_follow | Ep10_S60_T30_XSE | -1.0 | 26.0 | 379.0 | 314.0 | 16.0 | 69.0 | 21.0 | 1214.0 | -1214.0 | 136.0 | 29.0 | 927.0 | False | False |
| B1 | S4 | both-window+placebo-edge | B1_t600_none_fade | Emkt_Sa1_Tnone_X15 | 0.0 | 25.0 | 1301.0 | 816.0 | 168.0 | 213.0 | 179.0 | 1660.0 | -1571.0 | 526.0 | -34.0 | 254.0 | True | True |
| B1 | nyam | both-window+placebo-edge | B1_t600_er_fade | Eb1_Sa2_T90_X30 | 0.0 | 20.0 | 343.0 | 721.0 | 542.0 | 65.0 | 83.0 | 749.0 | -749.0 | 691.0 | -59.0 | 1975.0 | False | True |
| B1 | nypm | both-window+placebo-edge | B1_t600_er_follow | Ep10_S90_T30_X15 | -1.0 | 31.0 | 258.0 | 302.0 | 60.0 | 60.0 | 36.0 | 1187.0 | -907.0 | 195.0 | -14.0 | 863.0 | False | False |
| B2 | S1 | both-window+placebo-edge | B2_L15_t100_er_onset | Ep3_Sa1_Tnone_X60 | 0.0 | 22.0 | 1724.0 | 1183.0 | 908.0 | 405.0 | 90.0 | 3366.0 | -2250.0 | 1002.0 | 44.0 | 1061.0 | False | False |
| B2 | S2 | both-window+placebo-edge | B2_L30_t100_none_onset | Eb3_Sa1_T30_X30 | 0.0 | 50.0 | 1151.0 | 830.0 | 449.0 | 232.0 | 149.0 | 831.0 | -831.0 | 681.0 | -42.0 | 1599.0 | False | True |
| B2 | S3 | both-window+placebo-edge | B2_L15_t100_none_resume | Eb1_Sa2_Ta2_XSE | 0.0 | 50.0 | 868.0 | 833.0 | 316.0 | 200.0 | 228.0 | 2247.0 | -2247.0 | 643.0 | -69.0 | 2273.0 | False | True |
| B2 | S4 | recent-only | B2_L15_t100_none_onset | Eb3_Sa2_Ta2_X15 | 0.0 | 29.0 | 61.0 | 290.0 | 126.0 | -60.0 | -74.0 | 1411.0 | -1411.0 | 174.0 | 34.0 | 719.0 | False | True |
| B2 | nyam | both-window+placebo-edge | B2_L15_t100_er_onset | Eb5_Sa2_Tnone_XSE | 0.0 | 25.0 | 1228.0 | 1322.0 | 539.0 | 37.0 | 357.0 | 1492.0 | -1492.0 | 684.0 | 246.0 | 1929.0 | False | True |
| B2 | nypm | both-window+placebo-edge | B2_L15_t100_none_onset | Ep5_S60_Ta2_XSE | -1.0 | 101.0 | 850.0 | 1014.0 | 659.0 | 164.0 | 51.0 | 2400.0 | -2168.0 | 196.0 | 640.0 | 2270.0 | False | False |
| B3 | S1 | both-window+placebo-edge | B3_L10_Am0_fade | Emkt_Sa2_Ta2_XSE | 1.0 | 31.0 | 1179.0 | 1197.0 | 519.0 | 31.0 | 9.0 | 1940.0 | -1940.0 | 642.0 | 216.0 | 2474.0 | False | True |
| B3 | S2 | both-window+placebo-edge | B3_L20_Am0_fade | Eb3_S45_Ta2_X15 | -1.0 | 24.0 | 56.0 | 461.0 | 159.0 | 93.0 | 23.0 | 1233.0 | -1233.0 | 341.0 | -31.0 | 2461.0 | False | True |
| B3 | S3 | both-window+placebo-edge | B3_L20_Am150_follow | Emkt_S60_T30_X120 | 0.0 | 65.0 | 705.0 | 619.0 | 131.0 | 45.0 | 1.0 | 1686.0 | -1068.0 | 39.0 | 336.0 | 1240.0 | False | True |
| B3 | S4 | both-window+placebo-edge | B3_L20_Am150_fade | Emkt_S90_T90_X15 | 0.0 | 22.0 | 667.0 | 320.0 | 243.0 | 29.0 | 72.0 | 1814.0 | -1814.0 | 261.0 | 21.0 | 280.0 | True | True |
| B3 | nyam | both-window+placebo-edge | B3_L10_Am0_fade | Eb3_Sa2_Ta1_X15 | -1.0 | 36.0 | 508.0 | 541.0 | 278.0 | 6.0 | 65.0 | 825.0 | -716.0 | 385.0 | 25.0 | 2503.0 | False | True |
| B3 | nypm | both-window+placebo-edge | B3_L10_Cc150_fade | Ep3_S30_Ta1_X15 | 0.0 | 38.0 | 546.0 | 484.0 | 217.0 | 2.0 | 21.0 | 1968.0 | -1227.0 | 388.0 | -38.0 | 1093.0 | False | False |
| B4 | S2 | recent-only | B4_N30_er30_none_pf40 | Ep5_S60_T60_X120 | 1.0 | 15.0 | 549.0 | 267.0 | 126.0 | -55.0 | -131.0 | 2427.0 | -1214.0 | 0.0 | 196.0 | 299.0 | False | False |
| B4 | S3 | no gated cell |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| B4 | nyam | recent-only | B4_N30_er30_none_pf40 | Ep5_S60_T60_X120 | 1.0 | 15.0 | 549.0 | 267.0 | 126.0 | -55.0 | -131.0 | 2427.0 | -1214.0 | 0.0 | 196.0 | 299.0 | False | False |
| B4 | nypm | no gated cell |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


CLOCK baseline (every-day entry, best gated cell per unit; the TICK books must beat this, not zero):

| unit | dir | var | cell | n_L6M | mean_L3M | mean_L6M | mean_HOLD | mean_PRE | mean_X' | dd_L6M |
|---|---|---|---|---|---|---|---|---|---|---|
| nypm | -1 | CLOCK_c1205 | Ep5_Sa1_Ta1_XSE | 117.0 | 1872.0 | 1232.0 | 818.0 | -261.0 | -431.0 | 1664.0 |
| S3 | -1 | CLOCK_c1205 | Ep5_Sa1_Ta1_XSE | 117.0 | 1872.0 | 1232.0 | 818.0 | -261.0 | -431.0 | 1664.0 |
| nyam | 0 | CLOCK_c1005 | Emkt_Sa1_T90_X30 | 250.0 | 1314.0 | 1195.0 | 485.0 | -875.0 | -674.0 | 3241.0 |
| S2 | 0 | CLOCK_c1005 | Emkt_Sa1_T90_X30 | 250.0 | 1314.0 | 1195.0 | 485.0 | -875.0 | -674.0 | 3241.0 |
| S1 | 1 | CLOCK_c0935 | Emkt_S60_Ta2_X30 | 125.0 | 1397.0 | 1112.0 | 673.0 | -214.0 | -206.0 | 3981.0 |
| S4 | 1 | CLOCK_c1435 | Eb3_Sa2_Tnone_X15 | 58.0 | 518.0 | 619.0 | 54.0 | -149.0 | 152.0 | 2398.0 |


## 3. Delayed TICK 1/5/15 min (standalone, same cell as finalist)

| name | var | unit | cell | real_L6M | real_HOLD | real_PRE | real_X | d1_L6M | d1_HOLD | d1_PRE | d1_X | d5_L6M | d5_HOLD | d5_PRE | d5_X | d15_L6M | d15_HOLD | d15_PRE | d15_X |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1 | B2_L15_t100_er_onset | nyam | Eb5_Sa2_Tnone_XSE | 1322.0 | 539.0 | 37.0 | 357.0 | 972.0 | 304.0 | 63.0 | 230.0 | 555.0 | 48.0 | 191.0 | 157.0 | 148.0 | 81.0 | 252.0 | 316.0 |
| F2 | B2_L30_t100_none_onset | S2 | Eb3_Sa1_T30_X30 | 830.0 | 449.0 | 232.0 | 149.0 | 302.0 | 243.0 | 476.0 | 207.0 | 318.0 | 366.0 | -305.0 | 248.0 | 145.0 | 127.0 | -25.0 | -508.0 |
| F3 | B3_L10_Am0_fade | S1 | Emkt_Sa2_Tnone_XSE | 2843.0 | 1265.0 | 51.0 | 431.0 | 2968.0 | 1263.0 | -69.0 | 669.0 | 1483.0 | 305.0 | -196.0 | 86.0 | 761.0 | 453.0 | -596.0 | 91.0 |
| F4 | B1_t600_er_fade | S2 | Eb1_Sa2_T90_X30 | 721.0 | 542.0 | 104.0 | 5.0 | 288.0 | 308.0 | 162.0 | -85.0 | 92.0 | 40.0 | -160.0 | 189.0 | 296.0 | 161.0 | -265.0 | 14.0 |
| F5 | B2_L15_t100_none_resume | nypm | Eb1_Sa2_Ta2_XSE | 738.0 | 305.0 | 234.0 | 282.0 | 1105.0 | 575.0 | 93.0 | -319.0 | 731.0 | 157.0 | 247.0 | 162.0 | 999.0 | 547.0 | 194.0 | -111.0 |
| F6 | B1_t600_none_fade | S4 | Emkt_Sa1_Tnone_X15 | 816.0 | 168.0 | 213.0 | 179.0 | 165.0 | -135.0 | 244.0 | -12.0 | 221.0 | -79.0 | 203.0 | -227.0 | 64.0 | -60.0 | 49.0 | 339.0 |
| F7 | B3_L20_Am150_follow | S3 | Emkt_S60_T30_X120 | 619.0 | 131.0 | 45.0 | 1.0 | 619.0 | 120.0 | 39.0 | 25.0 | 641.0 | 114.0 | -45.0 | 115.0 | 462.0 | 33.0 | 108.0 | -90.0 |
| F8 | B4_N30_er30_none_pf25 | S2 | Emkt_Sa2_T30_X15 | 141.0 | 150.0 | -120.0 | 86.0 | 141.0 | 150.0 | -120.0 | 90.0 | 141.0 | 150.0 | -120.0 | 90.0 | 141.0 | 150.0 | -120.0 | 91.0 |


## 4. INJECTED STACK numbers (exact engine, JN05W2 base, all layers ON, hook uw_inject, tag TKB). Identity: TL3_TKB_ID must give 598 / 25943.82 for 202610.

No injected run finished yet.


Identity check: 


## 5. ES standalone (harness, 1 tick/side assumed)

| book | unit | tier | var | cell | dir | n_L6M | L3M | L6M | HOLD | PRE | X | dd_L6M | worst_L6M | edge_vs_placebo | rec_placebo | fam_null_max | beats_family_null | injectable |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B1 | S1 | both-window+placebo-edge | B1_t600_none_follow | Emkt_Sa2_Tnone_X15 | 0.0 | 27.0 | 242.0 | 119.0 | 60.0 | 219.0 | 73.0 | 6200.0 | -2068.0 | 2.0 | 88.0 | 1371.0 | False | True |
| B1 | S2 | both-window+placebo-edge | B1_t600_er_fade | Emkt_Sa2_Tnone_X120 | 0.0 | 34.0 | 44.0 | 264.0 | 243.0 | 17.0 | 73.0 | 2375.0 | -1510.0 | 67.0 | 187.0 | 1260.0 | False | True |
| B1 | S3 | both-window+placebo-edge | B1_t600_ercum_follow | Emkt_Sa2_T90_X120 | 0.0 | 32.0 | 488.0 | 270.0 | 105.0 | 188.0 | 64.0 | 3794.0 | -2350.0 | 529.0 | -341.0 | 759.0 | False | True |
| B1 | S4 | both-window+placebo-edge | B1_t600_none_fade | Emkt_S45_Ta1_XSE | 0.0 | 25.0 | 333.0 | 248.0 | 105.0 | 27.0 | 31.0 | 1345.0 | -1345.0 | 203.0 | -26.0 | 95.0 | True | True |
| B1 | nyam | recent-only | B1_t600_er_fade | Eb1_S45_T90_X120 | 0.0 | 17.0 | 456.0 | 647.0 | 673.0 | -436.0 | -26.0 | 1345.0 | -1345.0 | 643.0 | 17.0 | 1177.0 | False | True |
| B1 | nypm | both-window+placebo-edge | B1_t600_ercum_follow | Ep5_S30_Ta2_X60 | -1.0 | 22.0 | 715.0 | 334.0 | 122.0 | 69.0 | 16.0 | 3657.0 | -3657.0 | 363.0 | -136.0 | 723.0 | False | False |
| B2 | S1 | both-window+placebo-edge | B2_L15_t100_none_onset | Ep3_Sa1_Tnone_X120 | -1.0 | 25.0 | 1486.0 | 1228.0 | 561.0 | 35.0 | 9.0 | 7390.0 | -3649.0 | 621.0 | 273.0 | 1922.0 | False | False |
| B2 | S2 | both-window+placebo-edge | B2_L15_t100_none_resume | Emkt_S60_T45_X120 | 1.0 | 34.0 | 238.0 | 285.0 | 33.0 | 112.0 | 22.0 | 1626.0 | -1184.0 | 164.0 | -5.0 | 827.0 | False | True |
| B2 | S3 | both-window+placebo-edge | B2_L30_t100_none_resume | Emkt_S60_T45_X60 | 0.0 | 71.0 | 594.0 | 491.0 | 221.0 | 216.0 | 34.0 | 2208.0 | -1344.0 | 529.0 | -174.0 | 1342.0 | False | True |
| B2 | S4 | recent-only | B2_L15_t100_none_onset | Eb3_Sa1_Ta2_X120 | -1.0 | 19.0 | 170.0 | 208.0 | 64.0 | -111.0 | -478.0 | 1931.0 | -1407.0 | 70.0 | 66.0 | 347.0 | False | True |
| B2 | nyam | both-window+placebo-edge | B2_L30_t100_none_resume | Eb1_S60_Tnone_X120 | 0.0 | 31.0 | 516.0 | 380.0 | 137.0 | 88.0 | 204.0 | 2720.0 | -1444.0 | 361.0 | -103.0 | 1520.0 | False | True |
| B2 | nypm | both-window+placebo-edge | B2_L15_t100_none_resume | Emkt_Sa2_T45_X60 | -1.0 | 67.0 | 227.0 | 388.0 | 177.0 | 171.0 | 261.0 | 2658.0 | -1470.0 | 433.0 | -151.0 | 1260.0 | False | True |
| B3 | S1 | both-window+placebo-edge | B3_L10_Am150_follow | Eb5_S45_Tnone_X30 | 1.0 | 24.0 | 1113.0 | 984.0 | 512.0 | 460.0 | 114.0 | 2690.0 | -2635.0 | 181.0 | 567.0 | 1732.0 | False | True |
| B3 | S2 | both-window+placebo-edge | B3_L20_Bx600_follow | Eb5_S30_T90_X120 | 0.0 | 80.0 | 1519.0 | 2161.0 | 1344.0 | 432.0 | 61.0 | 3701.0 | -3657.0 | 42.0 | 1711.0 | 2565.0 | False | True |
| B3 | S3 | both-window+placebo-edge | B3_L10_Cc150_follow | Eb3_Sa2_Ta2_XSE | 0.0 | 20.0 | 383.0 | 416.0 | 62.0 | 146.0 | 68.0 | 1349.0 | -1349.0 | 208.0 | 31.0 | 1066.0 | False | True |
| B3 | S4 | recent-only | B3_L10_Bx600_follow | Ep3_S30_T30_X30 | 0.0 | 22.0 | 241.0 | 213.0 | 43.0 | -147.0 | -53.0 | 1219.0 | -1219.0 | 21.0 | 107.0 | 387.0 | False | False |
| B3 | nyam | both-window+placebo-edge | B3_L20_Am0_follow | Eb3_S60_T60_X120 | 1.0 | 25.0 | 342.0 | 472.0 | 312.0 | 77.0 | 66.0 | 1229.0 | -1184.0 | 185.0 | 207.0 | 2802.0 | False | True |
| B3 | nypm | both-window+placebo-edge | B3_L10_Cc150_fade | Eb3_S60_T45_X60 | 0.0 | 20.0 | 154.0 | 209.0 | 203.0 | 32.0 | 103.0 | 1010.0 | -1010.0 | 205.0 | 1.0 | 1074.0 | False | True |
| B4 | S2 | recent-only | B4_N30_er30_none_pf40 | Emkt_S90_Ta1_X60 | 0.0 | 24.0 | 336.0 | 144.0 | 54.0 | 20.0 | -99.0 | 1455.0 | -879.0 | 0.0 | 99.0 | 334.0 | False | True |
| B4 | S3 | no gated cell |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| B4 | nyam | recent-only | B4_N30_er30_none_pf40 | Emkt_S90_Ta1_X60 | 0.0 | 24.0 | 336.0 | 144.0 | 54.0 | 20.0 | -99.0 | 1455.0 | -879.0 | 0.0 | 99.0 | 334.0 | False | True |
| B4 | nypm | no gated cell |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


## 6. Caveats
Grid-best cells from a 1.8M-cell search; the placebo columns show what the same cell earns on day-shifted TICK. Standalone profits shrink ~85% under live gates (DS3_UWBOOKS_B1 section 8): only section 4 counts. Delays use the real-time price with a stale TICK. Exact placebos (11/23/37) are run in the engine only for the finalists that pass L6M.
