# DS3_TICK_BOOKS - new TICK books on NQ (W-TK2), research only, NO PASS claim. Built 2026-11-14 10:04 UTC

**VERDICT (plain):** Standalone NQ screen (5 books x 6 session units, 1,470-cell entry/stop/target/time grid, measured fills, real TICK vs TICK shifted 11/23/37 trading days): 9013 cells pass the both-window gate (L3M,L6M,HOLD,PRE,X' all > 0, enough trades) AND beat the same cell on the shifted-TICK placebos in recent and older windows; but these come from a 1.8M-cell search and only 2 of 22 book/unit families have a best cell above the best placebo-family cell, so the standalone evidence is WEAK (selection-dominated), and the literal directive book B1 at +/-1000 is too rare (<=20 trades/6 months) to pass any gate. 8 of 8 finalists have exact-engine L6M injected stack numbers so far; see section 4. Best injected L6M delta mean +865 $/wk (TL3_TKB_F3_real), max DD change -695.

**READING (W-TK2, 2026-11-14, exact engine, JN05W2 base, all layers ON; written by hand from section 4):** No TICK book is a lead by the user's rule. Best one is F2 = B2 follow persistent TICK (L30 mean >= +/-100, share>0 >= 0.6, onset trigger, no regime filter), NQ 10:00-12:00, confirm entry at +3 min, 1x ATR stop, 30-pt target, 30-min time stop, both sides: injected delta mean +994 (L3M), +581 (L6M), +454 (HOLD, 46% covered), +125 (PRE), +39 (X') $/wk vs exact placebos (TICK shifted 11/23/37 days) L6M -563..-38, HOLD -271..-11, PRE +16 (pl23), X' -410 (pl23): above placebo in all five windows, but the older-window gains are about 1% of the stack and max DD is NOT improved (PRE +3,018, X' -6,696, recent unchanged: the single -36.4k week dominates). Delayed TICK: F2 holds at 1 min (+368 L6M) and 5 min (+84) and fails at 15 min (-446), so a real-time feed is needed (a delay of 5 min or less is borderline). Second: F6 = B1 fade TICK high/low >= +/-600 in 14:30-15:00, market entry, 1x ATR stop, no target, 15-min stop: +365 (L3M), +501 (L6M), +260 (HOLD), -30 (PRE), +89 (X') vs placebos -127..+119: recent-only. The literal directive thresholds +/-1000 produce <=20 trades per 6 months and no gated cell. B4 first-hour trend-day (TICK confirm or not) has no gated cell. F1 (B2 ER-gated), F3 (B3 divergence), F7 (B3 follow) have recent gains but exact placebos give the same or more (B3 TICK conditions are barely selective): not TICK effects. Strength: weak. The drawdown ask (max DD, worst week, best-5 kept, winning weeks turned losing) is answered "no change" for every finalist; gains are mean-only and small. F2/F6 exact placebo exists for PRE/X' only as pl23 (one draw). ES: standalone only.

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

| set | window | coverage | weeks | ref_mean | inj_mean | d_mean | ref_dd | inj_dd | ref_worst | inj_worst | ref_stops_wk | inj_stops_wk | best5_kept | win_turned_losing | tkb_mean | tkb_n |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TL3_TKB_F1_pl11 | L3M | 0.8 | 11 | 16819.4 | 17439.8 | 620.4 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.5 | 1.0 | 0 | 620.4 | 5 |
| TL3_TKB_F1_pl11 | L6M | 0.9 | 25 | 23240.9 | 23892.1 | 651.3 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 651.3 | 11 |
| TL3_TKB_F1_pl11 | HOLD | 0.5 | 27 | 24470.4 | 24907.2 | 436.8 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.9 | 1.0 | 0 | 436.8 | 14 |
| TL3_TKB_F1_pl23 | L3M | 0.8 | 11 | 16819.4 | 16958.9 | 139.4 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 139.4 | 1 |
| TL3_TKB_F1_pl23 | L6M | 0.9 | 25 | 23240.9 | 23740.8 | 499.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.5 | 1.0 | 0 | 497.3 | 7 |
| TL3_TKB_F1_pl23 | HOLD | 0.5 | 27 | 24470.4 | 24874.6 | 404.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.7 | 1.0 | 0 | 401.7 | 8 |
| TL3_TKB_F1_pl37 | L3M | 0.8 | 11 | 16819.4 | 17304.5 | 485.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 485.0 | 4 |
| TL3_TKB_F1_pl37 | L6M | 0.9 | 25 | 23240.9 | 23787.3 | 546.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 543.8 | 12 |
| TL3_TKB_F1_pl37 | HOLD | 0.5 | 27 | 24470.4 | 24950.7 | 480.3 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.9 | 1.0 | 0 | 477.8 | 16 |
| TL3_TKB_F1_real | L3M | 0.8 | 11 | 16819.4 | 17083.4 | 264.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.5 | 1.0 | 0 | 264.0 | 5 |
| TL3_TKB_F1_real | L6M | 0.9 | 25 | 23240.9 | 23883.5 | 642.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.7 | 1.0 | 0 | 642.6 | 13 |
| TL3_TKB_F1_real | HOLD | 0.9 | 51 | 17639.8 | 17774.2 | 134.4 | 63185.1 | 64791.3 | -55145.4 | -55476.9 | 10.6 | 10.9 | 1.0 | 0 | 86.0 | 36 |
| TL3_TKB_F2_dly1 | L3M | 0.8 | 11 | 16819.4 | 17730.9 | 911.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.5 | 1.0 | 0 | 911.5 | 20 |
| TL3_TKB_F2_dly1 | L6M | 0.9 | 25 | 23240.9 | 23609.0 | 368.2 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.8 | 1.0 | 0 | 368.2 | 32 |
| TL3_TKB_F2_dly1 | HOLD | 0.5 | 27 | 24470.4 | 24769.1 | 298.7 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 11.0 | 1.0 | 0 | 298.7 | 36 |
| TL3_TKB_F2_dly15 | L3M | 0.8 | 11 | 16819.4 | 15992.2 | -827.2 | 36370.5 | 39224.9 | -36370.5 | -36370.5 | 11.3 | 11.8 | 1.0 | 0 | -345.9 | 14 |
| TL3_TKB_F2_dly15 | L6M | 0.9 | 25 | 23240.9 | 22795.0 | -445.9 | 36370.5 | 39224.9 | -36370.5 | -36370.5 | 10.5 | 10.9 | 1.0 | 0 | -234.1 | 29 |
| TL3_TKB_F2_dly15 | HOLD | 0.5 | 27 | 24470.4 | 23988.5 | -481.9 | 36370.5 | 39224.9 | -36370.5 | -36370.5 | 10.7 | 11.1 | 1.0 | 0 | -285.9 | 33 |
| TL3_TKB_F2_dly5 | L3M | 0.8 | 11 | 16819.4 | 16783.7 | -35.7 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 12.0 | 1.0 | 0 | -35.7 | 19 |
| TL3_TKB_F2_dly5 | L6M | 0.9 | 25 | 23240.9 | 23325.0 | 84.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 11.0 | 1.0 | 0 | 84.1 | 37 |
| TL3_TKB_F2_dly5 | HOLD | 0.5 | 27 | 24470.4 | 24570.5 | 100.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 11.2 | 1.0 | 0 | 100.1 | 38 |
| TL3_TKB_F2_pl11 | L3M | 0.8 | 11 | 16819.4 | 16875.0 | 55.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.5 | 1.0 | 0 | 55.6 | 14 |
| TL3_TKB_F2_pl11 | L6M | 0.9 | 25 | 23240.9 | 23202.9 | -38.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.8 | 1.0 | 0 | 26.4 | 30 |
| TL3_TKB_F2_pl11 | HOLD | 0.5 | 27 | 24470.4 | 24459.8 | -10.7 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 11.0 | 1.0 | 0 | 14.6 | 32 |
| TL3_TKB_F2_pl23 | L3M | 0.8 | 11 | 16819.4 | 15852.0 | -967.4 | 36370.5 | 38136.4 | -36370.5 | -36370.5 | 11.3 | 12.0 | 1.0 | 0 | -486.1 | 13 |
| TL3_TKB_F2_pl23 | L6M | 0.9 | 25 | 23240.9 | 22678.2 | -562.7 | 36370.5 | 38136.4 | -36370.5 | -36370.5 | 10.5 | 11.1 | 1.0 | 0 | -350.9 | 26 |
| TL3_TKB_F2_pl23 | HOLD | 0.5 | 51 | 12954.9 | 12707.6 | -247.4 | 36370.5 | 38136.4 | -36370.5 | -36370.5 | 5.7 | 6.0 | 1.0 | 0 | -161.7 | 29 |
| TL3_TKB_F2_pl23 | PRE | 1.0 | 75 | 10167.9 | 10183.6 | 15.7 | 76186.1 | 79020.9 | -52547.4 | -50643.3 | 9.3 | 10.0 | 1.0 | 0 | 70.7 | 165 |
| TL3_TKB_F2_pl23 | X' | 1.0 | 44 | 3585.1 | 3174.9 | -410.2 | 55325.6 | 53689.9 | -21663.5 | -25431.8 | 10.8 | 11.9 | 1.0 | 0 | -387.7 | 103 |
| TL3_TKB_F2_pl37 | L3M | 0.8 | 11 | 16819.4 | 16547.7 | -271.8 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.8 | 1.0 | 0 | -305.5 | 11 |
| TL3_TKB_F2_pl37 | L6M | 0.9 | 25 | 23240.9 | 22979.3 | -261.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 11.0 | 1.0 | 0 | -312.1 | 24 |
| TL3_TKB_F2_pl37 | HOLD | 0.5 | 27 | 24470.4 | 24199.5 | -271.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 11.3 | 1.0 | 0 | -352.1 | 29 |
| TL3_TKB_F2_real | L3M | 0.8 | 11 | 16819.4 | 17813.8 | 994.4 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 994.4 | 14 |
| TL3_TKB_F2_real | L6M | 0.9 | 25 | 23240.9 | 23822.0 | 581.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 581.1 | 26 |
| TL3_TKB_F2_real | HOLD | 0.9 | 51 | 17639.8 | 18093.4 | 453.6 | 63185.1 | 63185.1 | -55145.4 | -55145.4 | 10.6 | 10.9 | 1.0 | 0 | 375.3 | 67 |
| TL3_TKB_F2_real | PRE | 1.0 | 75 | 10167.9 | 10292.4 | 124.6 | 76186.1 | 79204.1 | -52547.4 | -53845.9 | 9.3 | 9.9 | 1.0 | 0 | 210.3 | 151 |
| TL3_TKB_F2_real | X' | 1.0 | 44 | 3585.1 | 3624.1 | 39.0 | 55325.6 | 48629.9 | -21663.5 | -22042.3 | 10.8 | 11.8 | 1.0 | 1 | 12.8 | 116 |
| TL3_TKB_F3_pl11 | L3M | 0.8 | 11 | 16819.4 | 17097.2 | 277.7 | 36370.5 | 36184.8 | -36370.5 | -36184.8 | 11.3 | 12.2 | 1.0 | 0 | 747.9 | 20 |
| TL3_TKB_F3_pl11 | L6M | 0.9 | 25 | 23240.9 | 23750.8 | 510.0 | 36370.5 | 36184.8 | -36370.5 | -36184.8 | 10.5 | 11.6 | 1.0 | 0 | 701.9 | 49 |
| TL3_TKB_F3_pl11 | HOLD | 0.5 | 27 | 24470.4 | 24988.6 | 518.1 | 36370.5 | 36184.8 | -36370.5 | -36184.8 | 10.7 | 11.8 | 1.0 | 0 | 695.8 | 53 |
| TL3_TKB_F3_pl23 | L3M | 0.8 | 11 | 16819.4 | 16315.2 | -504.3 | 36370.5 | 36731.4 | -36370.5 | -36370.5 | 11.3 | 12.3 | 1.0 | 0 | 86.0 | 20 |
| TL3_TKB_F3_pl23 | L6M | 0.9 | 25 | 23240.9 | 23111.0 | -129.8 | 36370.5 | 36731.4 | -36370.5 | -36370.5 | 10.5 | 11.6 | 1.0 | 0 | -120.6 | 46 |
| TL3_TKB_F3_pl23 | HOLD | 0.5 | 27 | 24470.4 | 24108.8 | -361.6 | 36370.5 | 36731.4 | -36370.5 | -36370.5 | 10.7 | 12.0 | 1.0 | 0 | -353.1 | 53 |
| TL3_TKB_F3_pl37 | L3M | 0.8 | 11 | 16819.4 | 18597.9 | 1778.5 | 36370.5 | 30351.0 | -36370.5 | -30351.0 | 11.3 | 12.1 | 1.0 | 0 | 1658.3 | 20 |
| TL3_TKB_F3_pl37 | L6M | 0.9 | 25 | 23240.9 | 25535.4 | 2294.6 | 36370.5 | 30351.0 | -36370.5 | -30351.0 | 10.5 | 11.3 | 1.1 | 0 | 1991.2 | 46 |
| TL3_TKB_F3_pl37 | HOLD | 0.5 | 27 | 24470.4 | 26631.8 | 2161.4 | 36370.5 | 30351.0 | -36370.5 | -30351.0 | 10.7 | 11.5 | 1.1 | 0 | 1880.5 | 51 |
| TL3_TKB_F3_real | L3M | 0.8 | 11 | 16819.4 | 16870.2 | 50.7 | 36370.5 | 35675.2 | -36370.5 | -30876.5 | 11.3 | 12.2 | 1.0 | 0 | 641.0 | 20 |
| TL3_TKB_F3_real | L6M | 0.9 | 25 | 23240.9 | 24105.7 | 864.8 | 36370.5 | 35675.2 | -36370.5 | -30876.5 | 10.5 | 11.3 | 1.0 | 0 | 1017.8 | 39 |
| TL3_TKB_F3_real | HOLD | 0.9 | 51 | 17639.8 | 18079.8 | 440.0 | 63185.1 | 63185.1 | -55145.4 | -55741.9 | 10.6 | 11.7 | 1.0 | 0 | 494.0 | 95 |
| TL3_TKB_F3_real | PRE | 1.0 | 75 | 10167.9 | 10019.0 | -148.9 | 76186.1 | 82524.3 | -52547.4 | -52547.4 | 9.3 | 10.5 | 1.0 | 0 | -83.3 | 157 |
| TL3_TKB_F4_real | L3M | 0.8 | 11 | 16819.4 | 16938.2 | 118.8 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 118.8 | 3 |
| TL3_TKB_F4_real | L6M | 0.9 | 25 | 23240.9 | 23525.4 | 284.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.5 | 1.0 | 0 | 284.6 | 9 |
| TL3_TKB_F4_real | HOLD | 0.5 | 27 | 24470.4 | 24733.9 | 263.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.7 | 1.0 | 0 | 263.5 | 9 |
| TL3_TKB_F5_real | L3M | 0.8 | 11 | 16819.4 | 16789.5 | -29.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.6 | 1.0 | 0 | -29.9 | 14 |
| TL3_TKB_F5_real | L6M | 0.9 | 25 | 23240.9 | 23103.6 | -137.3 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.9 | 1.0 | 0 | -137.3 | 25 |
| TL3_TKB_F5_real | HOLD | 0.5 | 27 | 24470.4 | 24471.0 | 0.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 11.0 | 1.0 | 0 | 0.5 | 28 |
| TL3_TKB_F6_dly1 | L3M | 0.8 | 11 | 16819.4 | 16854.6 | 35.2 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | 35.2 | 4 |
| TL3_TKB_F6_dly1 | L6M | 0.9 | 25 | 23240.9 | 23323.9 | 83.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.7 | 1.0 | 0 | 83.0 | 11 |
| TL3_TKB_F6_dly1 | HOLD | 0.5 | 27 | 24470.4 | 24567.3 | 96.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.9 | 1.0 | 0 | 96.9 | 12 |
| TL3_TKB_F6_dly15 | L3M | 0.8 | 11 | 16819.4 | 16716.7 | -102.7 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | -102.7 | 3 |
| TL3_TKB_F6_dly15 | L6M | 0.9 | 25 | 23240.9 | 23288.0 | 47.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.5 | 1.0 | 0 | 47.1 | 7 |
| TL3_TKB_F6_dly15 | HOLD | 0.5 | 27 | 24470.4 | 24514.1 | 43.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.7 | 1.0 | 0 | 43.6 | 7 |
| TL3_TKB_F6_dly5 | L3M | 0.8 | 11 | 16819.4 | 16871.0 | 51.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | 51.5 | 4 |
| TL3_TKB_F6_dly5 | L6M | 0.9 | 25 | 23240.9 | 23493.6 | 252.7 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 252.7 | 9 |
| TL3_TKB_F6_dly5 | HOLD | 0.5 | 27 | 24470.4 | 24704.4 | 234.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.8 | 1.0 | 0 | 234.0 | 9 |
| TL3_TKB_F6_pl11 | L3M | 0.8 | 11 | 16819.4 | 16864.6 | 45.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 45.1 | 2 |
| TL3_TKB_F6_pl11 | L6M | 0.9 | 25 | 23240.9 | 23216.0 | -24.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | -24.9 | 8 |
| TL3_TKB_F6_pl11 | HOLD | 0.5 | 27 | 24470.4 | 24467.8 | -2.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.7 | 1.0 | 0 | -2.6 | 9 |
| TL3_TKB_F6_pl23 | L3M | 0.8 | 11 | 16819.4 | 16776.6 | -42.9 | 36370.5 | 37284.1 | -36370.5 | -37284.1 | 11.3 | 11.4 | 1.0 | 0 | -42.9 | 5 |
| TL3_TKB_F6_pl23 | L6M | 0.9 | 25 | 23240.9 | 23301.5 | 60.7 | 36370.5 | 37284.1 | -36370.5 | -37284.1 | 10.5 | 10.6 | 1.0 | 0 | 60.7 | 10 |
| TL3_TKB_F6_pl23 | HOLD | 0.5 | 51 | 12954.9 | 12968.9 | 13.9 | 36370.5 | 37284.1 | -36370.5 | -37284.1 | 5.7 | 5.7 | 1.0 | 0 | 13.9 | 13 |
| TL3_TKB_F6_pl23 | PRE | 1.0 | 75 | 10167.9 | 9838.1 | -329.8 | 76186.1 | 78952.9 | -52547.4 | -53854.5 | 9.3 | 9.9 | 1.0 | 0 | -329.8 | 149 |
| TL3_TKB_F6_pl23 | X' | 1.0 | 44 | 3585.1 | 3418.7 | -166.4 | 55325.6 | 55048.5 | -21663.5 | -21157.0 | 10.8 | 11.6 | 1.0 | 1 | -171.2 | 124 |
| TL3_TKB_F6_pl37 | L3M | 0.8 | 11 | 16819.4 | 16946.3 | 126.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | 126.9 | 3 |
| TL3_TKB_F6_pl37 | L6M | 0.9 | 25 | 23240.9 | 23226.2 | -14.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | -14.6 | 9 |
| TL3_TKB_F6_pl37 | HOLD | 0.5 | 27 | 24470.4 | 24589.8 | 119.4 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.9 | 1.0 | 0 | 119.4 | 15 |
| TL3_TKB_F6_real | L3M | 0.8 | 11 | 16819.4 | 17184.0 | 364.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 364.6 | 4 |
| TL3_TKB_F6_real | L6M | 0.9 | 25 | 23240.9 | 23742.0 | 501.2 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 501.2 | 10 |
| TL3_TKB_F6_real | HOLD | 0.9 | 51 | 17639.8 | 17899.5 | 259.7 | 63185.1 | 60986.0 | -55145.4 | -55145.4 | 10.6 | 10.8 | 1.0 | 0 | 259.7 | 31 |
| TL3_TKB_F6_real | PRE | 1.0 | 75 | 10167.9 | 10137.7 | -30.2 | 76186.1 | 78132.3 | -52547.4 | -52547.4 | 9.3 | 9.8 | 1.0 | 0 | -14.2 | 137 |
| TL3_TKB_F6_real | X' | 1.0 | 44 | 3585.1 | 3674.4 | 89.3 | 55325.6 | 53121.3 | -21663.5 | -21759.4 | 10.8 | 11.6 | 1.0 | 0 | 89.3 | 140 |
| TL3_TKB_F7_pl11 | L3M | 0.8 | 11 | 16819.4 | 17068.5 | 249.1 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 11.3 | 11.5 | 1.0 | 0 | 249.1 | 17 |
| TL3_TKB_F7_pl11 | L6M | 0.9 | 25 | 23240.9 | 23689.4 | 448.5 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.5 | 10.8 | 1.0 | 0 | 448.5 | 40 |
| TL3_TKB_F7_pl11 | HOLD | 0.5 | 27 | 24470.4 | 24820.5 | 350.0 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.7 | 11.0 | 1.0 | 0 | 350.0 | 46 |
| TL3_TKB_F7_pl23 | L3M | 0.8 | 11 | 16819.4 | 17068.5 | 249.1 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 11.3 | 11.5 | 1.0 | 0 | 249.1 | 17 |
| TL3_TKB_F7_pl23 | L6M | 0.9 | 25 | 23240.9 | 23689.4 | 448.5 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.5 | 10.8 | 1.0 | 0 | 448.5 | 40 |
| TL3_TKB_F7_pl23 | HOLD | 0.5 | 27 | 24470.4 | 24820.5 | 350.0 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.7 | 11.0 | 1.0 | 0 | 350.0 | 46 |
| TL3_TKB_F7_pl37 | L3M | 0.8 | 11 | 16819.4 | 17068.5 | 249.1 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 11.3 | 11.5 | 1.0 | 0 | 249.1 | 17 |
| TL3_TKB_F7_pl37 | L6M | 0.9 | 25 | 23240.9 | 23737.0 | 496.2 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.5 | 10.7 | 1.0 | 0 | 496.2 | 39 |
| TL3_TKB_F7_pl37 | HOLD | 0.5 | 27 | 24470.4 | 24864.6 | 394.1 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.7 | 11.0 | 1.0 | 0 | 394.1 | 45 |
| TL3_TKB_F7_real | L3M | 0.8 | 11 | 16819.4 | 17177.7 | 358.3 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 11.3 | 11.5 | 1.0 | 0 | 358.3 | 16 |
| TL3_TKB_F7_real | L6M | 0.9 | 25 | 23240.9 | 23784.1 | 543.2 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.5 | 10.7 | 1.0 | 0 | 543.2 | 38 |
| TL3_TKB_F7_real | HOLD | 0.9 | 51 | 17639.8 | 17703.2 | 63.4 | 63185.1 | 63787.5 | -55145.4 | -55145.4 | 10.6 | 11.0 | 1.0 | 0 | 115.3 | 84 |
| TL3_TKB_F8_real | L3M | 0.8 | 11 | 16819.4 | 16883.1 | 63.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | -20.6 | 6 |
| TL3_TKB_F8_real | L6M | 0.9 | 25 | 23240.9 | 23096.9 | -143.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.7 | 1.0 | 0 | -216.7 | 15 |
| TL3_TKB_F8_real | HOLD | 0.5 | 27 | 24470.4 | 24301.5 | -168.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.9 | 1.0 | 0 | -236.3 | 17 |


### Injected delta mean $/wk: real vs exact placebos (TICK shifted 11/23/37 trading days through the same engine)

| name | window | dly1 | dly15 | dly5 | pl11 | pl23 | pl37 | real |
|---|---|---|---|---|---|---|---|---|
| F1 | HOLD |  |  |  | 437.0 | 404.0 | 480.0 | 134.0 |
| F1 | L3M |  |  |  | 620.0 | 139.0 | 485.0 | 264.0 |
| F1 | L6M |  |  |  | 651.0 | 500.0 | 546.0 | 643.0 |
| F2 | HOLD | 299.0 | -482.0 | 100.0 | -11.0 | -247.0 | -271.0 | 454.0 |
| F2 | L3M | 911.0 | -827.0 | -36.0 | 56.0 | -967.0 | -272.0 | 994.0 |
| F2 | L6M | 368.0 | -446.0 | 84.0 | -38.0 | -563.0 | -262.0 | 581.0 |
| F2 | PRE |  |  |  |  | 16.0 |  | 125.0 |
| F2 | X' |  |  |  |  | -410.0 |  | 39.0 |
| F3 | HOLD |  |  |  | 518.0 | -362.0 | 2161.0 | 440.0 |
| F3 | L3M |  |  |  | 278.0 | -504.0 | 1778.0 | 51.0 |
| F3 | L6M |  |  |  | 510.0 | -130.0 | 2295.0 | 865.0 |
| F3 | PRE |  |  |  |  |  |  | -149.0 |
| F4 | HOLD |  |  |  |  |  |  | 263.0 |
| F4 | L3M |  |  |  |  |  |  | 119.0 |
| F4 | L6M |  |  |  |  |  |  | 285.0 |
| F5 | HOLD |  |  |  |  |  |  | 1.0 |
| F5 | L3M |  |  |  |  |  |  | -30.0 |
| F5 | L6M |  |  |  |  |  |  | -137.0 |
| F6 | HOLD | 97.0 | 44.0 | 234.0 | -3.0 | 14.0 | 119.0 | 260.0 |
| F6 | L3M | 35.0 | -103.0 | 52.0 | 45.0 | -43.0 | 127.0 | 365.0 |
| F6 | L6M | 83.0 | 47.0 | 253.0 | -25.0 | 61.0 | -15.0 | 501.0 |
| F6 | PRE |  |  |  |  | -330.0 |  | -30.0 |
| F6 | X' |  |  |  |  | -166.0 |  | 89.0 |
| F7 | HOLD |  |  |  | 350.0 | 350.0 | 394.0 | 63.0 |
| F7 | L3M |  |  |  | 249.0 | 249.0 | 249.0 | 358.0 |
| F7 | L6M |  |  |  | 449.0 | 449.0 | 496.0 | 543.0 |
| F8 | HOLD |  |  |  |  |  |  | -169.0 |
| F8 | L3M |  |  |  |  |  |  | 64.0 |
| F8 | L6M |  |  |  |  |  |  | -144.0 |


### Injected max-DD change $ (inj - ref): real vs placebos

| name | window | dly1 | dly15 | dly5 | pl11 | pl23 | pl37 | real |
|---|---|---|---|---|---|---|---|---|
| F1 | HOLD |  |  |  | 0.0 | 0.0 | 0.0 | 1606.0 |
| F1 | L3M |  |  |  | 0.0 | 0.0 | 0.0 | 0.0 |
| F1 | L6M |  |  |  | 0.0 | 0.0 | 0.0 | 0.0 |
| F2 | HOLD | 0.0 | 2854.0 | 0.0 | 0.0 | 1766.0 | 0.0 | 0.0 |
| F2 | L3M | 0.0 | 2854.0 | 0.0 | -0.0 | 1766.0 | -0.0 | -0.0 |
| F2 | L6M | 0.0 | 2854.0 | 0.0 | 0.0 | 1766.0 | 0.0 | 0.0 |
| F2 | PRE |  |  |  |  | 2835.0 |  | 3018.0 |
| F2 | X' |  |  |  |  | -1636.0 |  | -6696.0 |
| F3 | HOLD |  |  |  | -186.0 | 361.0 | -6020.0 | 0.0 |
| F3 | L3M |  |  |  | -186.0 | 361.0 | -6019.0 | -695.0 |
| F3 | L6M |  |  |  | -186.0 | 361.0 | -6020.0 | -695.0 |
| F3 | PRE |  |  |  |  |  |  | 6338.0 |
| F4 | HOLD |  |  |  |  |  |  | 0.0 |
| F4 | L3M |  |  |  |  |  |  | 0.0 |
| F4 | L6M |  |  |  |  |  |  | 0.0 |
| F5 | HOLD |  |  |  |  |  |  | 0.0 |
| F5 | L3M |  |  |  |  |  |  | 0.0 |
| F5 | L6M |  |  |  |  |  |  | 0.0 |
| F6 | HOLD | 0.0 | 0.0 | 0.0 | 0.0 | 914.0 | 0.0 | -2199.0 |
| F6 | L3M | 0.0 | 0.0 | 0.0 | 0.0 | 914.0 | -0.0 | 0.0 |
| F6 | L6M | 0.0 | 0.0 | 0.0 | 0.0 | 914.0 | 0.0 | 0.0 |
| F6 | PRE |  |  |  |  | 2767.0 |  | 1946.0 |
| F6 | X' |  |  |  |  | -277.0 |  | -2204.0 |
| F7 | HOLD |  |  |  | 1191.0 | 1191.0 | 1191.0 | 602.0 |
| F7 | L3M |  |  |  | 1191.0 | 1191.0 | 1191.0 | 1191.0 |
| F7 | L6M |  |  |  | 1191.0 | 1191.0 | 1191.0 | 1191.0 |
| F8 | HOLD |  |  |  |  |  |  | 0.0 |
| F8 | L3M |  |  |  |  |  |  | -0.0 |
| F8 | L6M |  |  |  |  |  |  | 0.0 |


Identity check: IDENTITY 202610 598 25943.82 vs 598 25943.82 IDENTICAL



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


## 7. Extra evidence for F2/F6 (lead order 2026-11-14)

### 7a. Bi-weekly walk-forward (trail 26 weeks, re-pick every 2 weeks over the whole 1,470-cell grid, flat if trailing mean <= 0) and best-of null, standalone harness, both sides

| book | mode | wf_mean | wf_dd | wf_worst | wf_picks | wf_pct_pos | bestof_recents | bestof_older |
|---|---|---|---|---|---|---|---|---|
| F2 | real | -312.0 | 68512.0 | -5028.0 | 82 | 0.0 | 1130.0 | 439.0 |
| F2 | pl11 | -38.0 | 30638.0 | -4372.0 | 81 | 1.0 | 424.0 | 107.0 |
| F2 | pl23 | 199.0 | 21844.0 | -4765.0 | 80 | 0.0 | 608.0 | 317.0 |
| F2 | pl37 | -229.0 | 45297.0 | -7380.0 | 78 | 0.0 | 159.0 | 445.0 |
| F6 | real | -71.0 | 24493.0 | -3918.0 | 82 | 0.0 | 495.0 | 324.0 |
| F6 | pl11 | -55.0 | 10574.0 | -1909.0 | 81 | 0.0 | 79.0 | 92.0 |
| F6 | pl23 | -14.0 | 11090.0 | -2906.0 | 79 | 0.0 | 174.0 | 121.0 |
| F6 | pl37 | 12.0 | 10713.0 | -2554.0 | 78 | 0.0 | 198.0 | 101.0 |

wf_* = OOS weekly $ of the walk-forward chain; bestof_* = max over all 1,470 cells of (L6M+HOLD)/2 and (PRE+X')/2 for that var/unit: real vs shifted TICK is the family null for the cell choice.


### 7b. Concentration of the injected gain and stack without the worst reference week (all months present for the set)

| book | months | weeks | tkb_total | best5wk_share | best4mo_share | weeks_pos | weeks_neg | worst_ref_week | worst_ref | delta_mean_all | delta_mean_ex_worst | dd_ref_ex | dd_inj_ex | pl23_delta_all | pl23_delta_ex | pl23_dd_chg_ex | dd_chg_ex_real |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F2 | 39 | 170 | 35678.88 | 0.56 | 0.74 | 86 | 62 | 202606 | -55145.44 | 202.32 | 203.51 | 76186.06 | 79204.08 | -173.46 | -174.48 | 2834.82 | 3018.02 |
| F6 | 39 | 170 | 16695.24 | 1.3 | 1.19 | 72 | 55 | 202606 | -55145.44 | 91.16 | 91.69 | 76186.06 | 78132.3 | -184.39 | -185.48 | 2766.86 | 1946.24 |

ES injection: NOT possible. uw_inject only registers an NQ book inside the NQ-only JN05W2 engine; generalising to ES needs an ES price path and book walk in the engine, which is a separate engine change with its own identity proof and was not attempted. ES is standalone harness only (section 5).


## 6. Caveats
Grid-best cells from a 1.8M-cell search; the placebo columns show what the same cell earns on day-shifted TICK. Standalone profits shrink ~85% under live gates (DS3_UWBOOKS_B1 section 8): only section 4 counts. Delays use the real-time price with a stale TICK. Exact placebos (11/23/37) are run in the engine only for the finalists that pass L6M.
