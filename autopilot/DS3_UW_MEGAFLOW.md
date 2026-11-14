# DS3_UW_MEGAFLOW - W-MF, megacap option flow (net premium, bursts, tape) leading NQ. Built 2026-11-13 23:51Z by code/th_uwmf/mf_page.py. Research only, shadow, NO PASS claim.
## 0. Plain verdict (read first)
PAGE STATUS: first page, engine runs of the finalists are still arriving (section 5 fills in; this page rebuilds every 3 h).
VERDICT (first page): megacap option flow does NOT lead NQ in a usable way: net premium and flow bursts follow the price move (contemporaneous IC 0.3-0.5) and the forward partial IC after removing price is ~0.01-0.03 with no cell beyond chance in both windows; the one thing above its nulls is a prior-day megacap net-premium CARRY filter on the live night books (skip night trades when the prior day's megacap flow was against the trade, first-order p~0.02 vs 41 shifted-flow draws) - exact-engine result below decides its strength. Weak lead at best; no PASS. No exact-engine set yet holds in both the recent and the older window with a smaller drawdown and no loss of mean.
## 1. Data, clocks, what each session can use
- Megacap net premium: /mnt/l2/l2vast/uw/net_prem_ticks (and nprem for QQQ/NDX/SPY/SPX) per ticker NVDA AAPL MSFT AMZN META GOOGL TSLA, 553 UTC days 2024-10-01..2026-11-12, 1-min rows (net call premium, net put premium, ask/bid volumes). Option flow exists only while the options trade: about 09:30-16:00 ET (NYAM and NYPM), a thin PRE sliver (~950 minutes of 7 names in total), and essentially NOTHING in Asia and London (0 minutes in Asia, ~900 in London over 2 years). So for Asia / London / PRE the only honest use of megacap flow is CARRY (the prior completed RTH day's flow, known after 16:03 ET), and that is what is tested for those sessions.
- Tape-derived flow (tape_agg: ask-minus-bid signed premium by DTE bucket, call minus put; tape_big >= $50k trades): files from 2025-08-07; older days are sparse (about every 7th day so far) and are still arriving, so tape results cover roughly 140-180 days; rerun when the downloader finishes. OLDER window for tape series = the part of 2025-08..2026-04 that has tape days.
- Lag: minute row usable at bar start + 60 s + 120 s assumed delivery lag (decision ts = start+180 s); no look-ahead; z-scaling by trailing 20-day mean |flow| (prior days only). Sums: MEGAraw = sum of the seven raw $ flows; MEGAeq = equal-weight mean of the seven z series; MEGAcap = approx static NDX-weight (NVDA .25 MSFT .21 AAPL .21 AMZN .12 GOOGL .10 META .08 TSLA .04, ASSUMED rounded) weighted z sum. NQ/ES 1-min bars (roll jumps >0.4%/min zeroed). Fills: harness measured NQ +0.23/+0.44/+1.36 pts, $4.84 RT; engine numbers use the engine fill model.
- Windows: L3M/L6M from 2026-11-10 (end of NQ 1-min file), HOLD = 365 d, PREUW = 2024-10..2025-06, OLDER = everything before L6M. A result is called a lead only if it holds in BOTH recent (L6M) and older (OLDER / PREUW). Nulls: flow series shifted by 11 / 23 / 37 (lead-lag, bursts) and 30+ other days (filters) with time of day kept.
## 2. Pure lead-lag study (no trading): does megacap option flow LEAD NQ or FOLLOW it?
Method: for flow window w (1/5/15/60 min of summed z-flow, usable at start+180 s) and forward NQ/ES return h (1/5/15/60 min from the usable time), partial information coefficient controlling for the contemporaneous return over the same window, the previous window return and the return during the delivery gap (extra run adds lagged flow as control). Sessions by usable time. 35 flow series x 4 w x 4 h x 2 targets x 3 flow sessions x 5 windows, each with 3 shifted-time placebos; z = real partial IC / family placebo sd (same window, session, w, h, target).
### 2a. Flow FOLLOWS price (contemporaneous IC of 5-min flow with the 5-min NQ return, L6M)
| series | nyam | nypm | pre |
|---|---|---|---|
| MEGAraw|prem | 0.426 | 0.382 | 0.239 |
| MEGAeq|prem | 0.405 | 0.391 | 0.223 |
| MEGAcap|prem | 0.387 | 0.366 | 0.178 |
| MEGAeq|vol | 0.461 | 0.475 | 0.221 |
| MEGAraw|tp_all_bull | 0.389 | 0.321 | 0.24 |
| MEGAraw|tp_d0_bullb | 0.055 | 0.083 |  |
| QQQ|prem | 0.44 | 0.397 | 0.15 |
| NDX|prem | 0.14 | 0.136 |  |
| QQQ|vol | 0.608 | 0.593 | 0.203 |
| NDX|vol | 0.409 | 0.417 |  |
Reading: megacap flow is strongly co-moving with the price move it sits in (IC 0.3-0.5 for the aggregates; the control QQQ/NDX is the same or stronger). This is the W-UB2 finding (flow follows price) reproduced and extended to the megacaps. Net premium follows price; it is not an independent signal until the price part is removed.
### 2b. After removing contemporaneous / previous / gap price, does it LEAD? (partial IC, forward return)
**NYAM**: 1120 (series,target,w,h) cells with both windows; cells with same sign in L6M and OLDER and min(|z|)>2: 2 (chance ~13), >3: 0.
| series | tgt | w | h | ic_partial_L3M | ic_partial_L6M | ic_partial_OLDER | z_L6M | z_OLDER | n_L6M |
|---|---|---|---|---|---|---|---|---|---|
| QQQ|tp_all_bull | ES | 1 | 1 | 0.022 | 0.0198 | 0.0117 | 2.3802 | 2.0658 | 18396.0 |
| QQQ|tp_all_bull | NQ | 1 | 1 | 0.0218 | 0.0242 | 0.0125 | 2.6017 | 2.0409 | 18396.0 |
| QQQ|vol | ES | 1 | 1 | 0.0096 | 0.0196 | 0.0106 | 2.3543 | 1.8743 | 18396.0 |
| QQQ|prem | ES | 1 | 1 | 0.0225 | 0.0201 | 0.0106 | 2.4253 | 1.8591 | 18396.0 |
| MEGAraw|tp_dL_bullb | ES | 15 | 15 | -0.0629 | -0.0462 | -0.0629 | -1.8236 | -2.9921 | 16773.0 |
| MEGAraw|tp_d0_bullb | ES | 15 | 15 | 0.1073 | 0.0458 | 0.0537 | 1.809 | 2.5513 | 10260.0 |
**NYPM**: 1120 (series,target,w,h) cells with both windows; cells with same sign in L6M and OLDER and min(|z|)>2: 0 (chance ~13), >3: 0.
| series | tgt | w | h | ic_partial_L3M | ic_partial_L6M | ic_partial_OLDER | z_L6M | z_OLDER | n_L6M |
|---|---|---|---|---|---|---|---|---|---|
| MEGAeq|prem | ES | 1 | 5 | -0.0176 | -0.0176 | -0.0067 | -1.8496 | -1.3394 | 30240.0 |
| MEGAeq|prem | ES | 5 | 1 | -0.0129 | -0.0135 | -0.0054 | -1.5881 | -1.2314 | 30240.0 |
| QQQ|vol | ES | 15 | 15 | -0.0313 | -0.032 | -0.0181 | -1.3819 | -1.1801 | 30240.0 |
| MEGAeq|prem | NQ | 5 | 15 | 0.0013 | -0.0231 | -0.0124 | -1.1475 | -1.1505 | 30240.0 |
| MEGAcap|prem | NQ | 15 | 5 | -0.0016 | -0.0214 | -0.0109 | -1.1682 | -1.1238 | 30240.0 |
| MEGAcap|prem | NQ | 5 | 15 | 0.0026 | -0.0223 | -0.0133 | -1.1116 | -1.2266 | 30240.0 |
**PRE**: 0 (series,target,w,h) cells with both windows; cells with same sign in L6M and OLDER and min(|z|)>2: 0 (chance ~0), >3: 0.
(none)
Reading: forward partial IC is of order 0.01-0.03 for 1-15 min horizons, the same sign in both windows only for a handful of cells and none clears z>3; the count of cells with min(|z|)>2 is near what chance gives. The control (QQQ net premium 1-min flow vs next-minute ES/NQ) is the strongest and still tiny (IC 0.02). Tape: big (>=$100k) 0DTE bullish megacap premium has a positive 5-15 min forward IC on NQ/ES (NYAM, L6M +0.03, older +0.06..0.07, z 1-4.6) and big longer-dated premium the opposite sign (about -0.03/-0.06): the one pattern with the same sign in both windows - tape coverage is only ~6 months of dense days, treat as LEAD (weak), unproven.
Session note: ASIA / LONDON have no megacap flow (no options trading). PRE has ~950 flow-minutes in 2 years: lead-lag not estimable (n<600 per cell).
## 3. Entry triggers (harness screen; engine numbers in section 5)
Bursts: window w in {1,5,15} min of summed flow above the trailing-20-day q95 / q99 of |flow| (first minute of an excursion), 372 tables (single names, MEGAraw/eq/cap, tape all/0DTE/longer-dated x total/big, QQQ and NDX control), follow and fade both scored (follow = trade in the burst direction). Grid = W-UB1 harness (entry mkt/b1/b3/b5/pullbacks, stops, targets, time exits). Carry: prior-RTH-day flow (full / last 60 min / first 60 min) in top or bottom tercile of trailing 60 days, entry at the next session start. Standalone numbers are $/wk at 1 lot-set; the live stack gates cut standalone profit by roughly 85 percent in the engine, so quote section 5.
**bursts (NYAM, NYPM)**: best (L6M+HOLD)/2 $/wk over the whole family vs the same best-of-family on shifted flow (11/23/37 d + more as they finish) and the every-day clock baseline in the same session:

| session | best_real_rec | null_shift_recs | n_null | null_max | above_null | clock_every_day_best | cells_gated |
|---|---|---|---|---|---|---|---|
| nyam | 3447.0 | 3134,2334,2496,2382,3020,2709 | 6 | 3134.0 | 6 | 2178.0 | 2422 |
| nypm | 2575.0 | 2491,1569,1938,1429,1878,2518 | 6 | 2518.0 | 6 | 1550.0 | 1673 |
best gated cells NYAM:

| kind | dir | follow | cell | n_L6M | mean_L1M | mean_L3M | mean_L6M | mean_HOLD | mean_PREUW | dd_L6M | worst_L6M | stops_wk_L6M | pos_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| MEGAraw|tp_d0_bull_w5_q95_dn | -1 | True | Ep3_Sa2_Ta1_X60 | 51.0 | 1645.5 | 1112.8 | 1278.5 | 396.2 |  | 804.7 | -804.7 | 0.1 | 0.9 |
| MEGAraw|tp_d0_bull_w5_q95_dn | -1 | True | Emkt_Sa2_Ta1_X60 | 56.0 | 1645.5 | 1074.3 | 1273.6 | 423.7 |  | 869.7 | -869.7 | 0.2 | 0.9 |
| NVDA|prem_w5_q95_dn | 1 | False | Ep5_Sa2_Ta1_X15 | 78.0 | 1483.8 | 1024.0 | 1263.7 | 779.5 | -73.9 | 1098.6 | -1098.6 | 0.3 | 0.9 |
| MEGAraw|prem_w15_q99_up | 1 | True | Ep10_S60_Tnone_X60 | 26.0 | 1178.4 | 1200.0 | 1225.3 | 880.5 | -200.4 | 1213.6 | -1213.6 | 0.3 | 0.9 |
| NVDA|prem_w5_q95_dn | 1 | False | Ep3_Sa2_Ta1_X15 | 80.0 | 1803.6 | 896.2 | 1173.3 | 741.0 | -80.8 | 1072.5 | -1072.5 | 0.3 | 0.9 |
best gated cells NYPM:

| kind | dir | follow | cell | n_L6M | mean_L1M | mean_L3M | mean_L6M | mean_HOLD | mean_PREUW | dd_L6M | worst_L6M | stops_wk_L6M | pos_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NDX|prem_w1_q99_up | -1 | False | Ep3_S30_Ta1_X30 | 64.0 | 1999.0 | 1558.0 | 1659.6 | 989.4 | 192.1 | 1227.3 | -1227.3 | 0.5 | 0.8 |
| NDX|prem_w1_q99_up | -1 | False | Emkt_S30_Ta1_X30 | 71.0 | 1811.0 | 1553.7 | 1646.2 | 869.0 | -89.0 | 1227.3 | -1227.3 | 0.6 | 0.8 |
| GOOGL|vol_w5_q95_dn | -1 | True | Emkt_Sa1_T45_XSE | 60.0 | 1552.0 | 1982.4 | 1455.7 | 1105.3 | -106.2 | 1058.6 | -993.7 | 0.6 | 0.8 |
| GOOGL|vol_w5_q95_dn | -1 | True | Emkt_Sa1_T45_X120 | 60.0 | 1552.0 | 1982.4 | 1455.7 | 1105.3 | -106.2 | 1058.6 | -993.7 | 0.6 | 0.8 |
| AMZN|prem_w1_q95_up | -1 | False | Eb3_S30_T60_X60 | 48.0 | 2132.0 | 1233.8 | 1278.4 | 129.1 | 56.5 | 1227.3 | -1227.3 | 0.7 | 0.7 |
**carry (Asia, London, PRE)**: best (L6M+HOLD)/2 $/wk over the whole family vs the same best-of-family on shifted flow (11/23/37 d + more as they finish) and the every-day clock baseline in the same session:

| session | best_real_rec | null_shift_recs | n_null | null_max | above_null | clock_every_day_best | cells_gated |
|---|---|---|---|---|---|---|---|
| asia | 5765.0 | 2954,1917,2808 | 3 | 2954.0 | 3 | 5227.0 | 500 |
| london | 2546.0 | 1366,1287,1267 | 3 | 1366.0 | 3 | 864.0 | 613 |
| pre | 1242.0 | 536,466,546 | 3 | 546.0 | 3 | 1045.0 | 396 |
best gated cells ASIA:

| kind | dir | follow | cell | n_L6M | mean_L1M | mean_L3M | mean_L6M | mean_HOLD | mean_PREUW | dd_L6M | worst_L6M | stops_wk_L6M | pos_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| carry_QQQ|prem_first60_lo_asia | -1 | True | Eb1_Sa1_Tnone_XSE | 21.0 | 3752.5 | 1368.2 | 4369.6 | 1955.0 | -241.0 | 3797.5 | -2567.8 | 0.5 | 0.5 |
| carry_QQQ|vol_last60_lo_asia | -1 | True | Eb1_Sa1_Tnone_XSE | 26.0 | 3162.1 | 1127.7 | 5363.5 | 3058.4 | -628.8 | 5230.6 | -2693.1 | 0.7 | 0.4 |
| carry_NVDA|prem_full_lo_asia | -1 | True | Eb1_Sa1_Tnone_X120 | 24.0 | 5975.6 | 2599.1 | 2602.6 | 1159.8 | 319.3 | 2633.7 | -1417.3 | 0.4 | 0.7 |
| carry_MEGAraw|tp_dL_bullb_full_hi_asia | -1 | False | Emkt_S30_Tnone_X15 | 32.0 | 3003.6 | 1156.9 | 1063.5 | 439.2 |  | 1227.3 | -1227.3 | 0.1 | 0.8 |
| carry_AAPL|prem_first60_hi_asia | -1 | False | Ep3_Sa1_Tnone_XSE | 30.0 | 9790.6 | 3065.2 | 7669.7 | 3860.2 | -304.6 | 9188.8 | -2642.1 | 0.7 | 0.4 |
best gated cells LONDON:

| kind | dir | follow | cell | n_L6M | mean_L1M | mean_L3M | mean_L6M | mean_HOLD | mean_PREUW | dd_L6M | worst_L6M | stops_wk_L6M | pos_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| carry_MEGAraw|tp_dL_bullb_full_lo_london | 1 | False | Emkt_S30_T60_XSE | 38.0 | 1434.2 | 1172.9 | 1086.4 | 464.8 |  | 1355.8 | -1227.3 | 0.6 | 0.6 |
| carry_QQQ|prem_last60_lo_london | 1 | False | Eb1_S60_T90_XSE | 25.0 | 232.6 | 427.1 | 816.3 | 411.2 | -65.4 | 1213.6 | -1213.6 | 0.3 | 0.8 |
| carry_MEGAraw|tp_dL_bullb_full_lo_london | 1 | False | Emkt_Sa2_T60_XSE | 38.0 | 717.1 | 1006.7 | 910.5 | 357.4 |  | 1455.8 | -1455.8 | 0.5 | 0.7 |
| carry_TSLA|prem_last60_lo_london | 1 | False | Emkt_S90_T60_XSE | 38.0 | 230.7 | 939.2 | 738.1 | 441.9 | 224.8 | 1237.0 | -1237.0 | 0.3 | 0.8 |
| carry_MEGAraw|tp_all_bull_full_lo_london | 1 | False | Emkt_S60_T60_XSE | 40.0 | 709.7 | 541.7 | 700.0 | 303.0 |  | 1250.6 | -1232.1 | 0.4 | 0.5 |
best gated cells PRE:

| kind | dir | follow | cell | n_L6M | mean_L1M | mean_L3M | mean_L6M | mean_HOLD | mean_PREUW | dd_L6M | worst_L6M | stops_wk_L6M | pos_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| carry_NVDA|prem_full_hi_pre | -1 | False | Emkt_S30_T90_X30 | 25.0 | 271.2 | 674.1 | 936.2 | 291.4 | 177.7 | 1227.3 | -1227.3 | 0.2 | 0.8 |
| carry_NVDA|prem_first60_lo_pre | -1 | True | Ep3_S30_T90_X120 | 29.0 | 1370.0 | 792.4 | 921.5 | 418.4 | -142.2 | 1227.3 | -1227.3 | 0.5 | 0.6 |
| carry_NVDA|prem_first60_lo_pre | -1 | True | Ep3_S30_T90_X60 | 29.0 | 1370.0 | 792.4 | 921.5 | 418.4 | -142.2 | 1227.3 | -1227.3 | 0.5 | 0.6 |
| carry_NDX|prem_last60_hi_pre | -1 | False | Ep5_S30_T45_X60 | 24.0 | 1299.4 | 752.8 | 889.2 | 222.6 | -181.4 | 1227.3 | -1227.3 | 0.2 | 0.8 |
| carry_NDX|prem_last60_hi_pre | -1 | False | Ep5_S30_T45_X120 | 24.0 | 1299.4 | 752.8 | 889.2 | 222.6 | -181.4 | 1227.3 | -1227.3 | 0.2 | 0.8 |
## 4. Filters on the live books (first order on the exact JN05W2 trade list, 13,512 trades 2024-10..2026-10)
Feature = side-signed z-flow at the signal (intraday sum over 1/5/15/60 min) or prior-day carry; rule = skip / half / press (x1.5) when signed feature <= -t (flow against the trade) or >= t (flow with it), per book and session; t in {0.5,1,2,4} (carry {0.5,1,1.5}). 34,851 rules. Gate: stack maxDD smaller A41D mean not lower in BOTH L6M and OLD (everything before L6M), >= 8 trades touched each. Score = DD relief L6M + OLD ($). Placebo = the same 34,851 rules on flow taken from 7..239 days earlier (41 draws), best-of-family compared.
| family | real_best | real_npass | null_best_max | null_best_med | null_npass_med | null_npass_max | nshift | exceed |
|---|---|---|---|---|---|---|---|---|
| carry-night | 18998.0 | 52.0 | 17321.0 | 0.0 | 0.0 | 57.0 | 41.0 | 0.0 |
| carry-rth | 6242.0 | 13.0 | 6640.0 | 0.0 | 0.0 | 31.0 | 41.0 | 2.0 |
| intraday-nyam | 6280.0 | 337.0 | 8764.0 | 4822.0 | 157.0 | 655.0 | 41.0 | 16.0 |
| intraday-nypm | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 41.0 | 41.0 |
| intraday-rth | 5385.0 | 277.0 | 11409.0 | 5023.0 | 129.0 | 476.0 | 41.0 | 20.0 |
scope night, top gated rules:

| feat | book | tail | thr | act | n_L6M | n_OLD | dmean_L3M | dmean_L6M | dmean_OLD | ddd_L3M | ddd_L6M | ddd_OLD | ddd_HOLD | p_rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| carry|MEGAraw|prem|full | ALL | le | 1.0 | skip | 408 | 899 | 1888.54 | 1361.64 | 1204.56 | -2567.32 | -2567.32 | -16430.88 | -20176.76 | 0.02 |
| carry|MEGAraw|prem|full | ALL | le | 1.5 | skip | 243 | 406 | 1175.3 | 696.85 | 610.7 | -5327.44 | -5327.44 | -7239.52 | -8039.66 | 0.02 |
| carry|MEGAraw|prem|full | ALL | le | 1.0 | half | 408 | 899 | 944.27 | 680.82 | 602.28 | -1283.66 | -1283.66 | -10958.41 | -10998.11 | 0.02 |
| carry|MEGAraw|prem|full | U7 | le | 1.0 | skip | 39 | 101 | 545.25 | 962.54 | 253.08 | -4714.72 | -4714.72 | -4139.68 | -3997.62 | 0.02 |
scope asia, top gated rules:

| feat | book | tail | thr | act | n_L6M | n_OLD | dmean_L3M | dmean_L6M | dmean_OLD | ddd_L3M | ddd_L6M | ddd_OLD | ddd_HOLD | p_rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| carry|MEGAraw|prem|full | ALL | le | 1.0 | skip | 261 | 502 | -429.76 | 340.98 | 100.78 | -132.14 | -132.14 | -8622.2 | -12199.54 | 0.02 |
| carry|MEGAraw|prem|full | ALL | le | 1.5 | skip | 158 | 237 | -17.27 | 198.83 | 4.24 | -5327.44 | -5327.44 | -1260.62 | -8039.66 | 0.02 |
| carry|MEGAraw|prem|full | ALL | le | 1.0 | half | 261 | 502 | -214.88 | 170.49 | 50.39 | -1283.66 | -1283.66 | -4457.57 | -6099.77 | 0.02 |
| carry|MEGAraw|prem|full | K7 | le | 1.0 | skip | 106 | 185 | 811.08 | 312.37 | 121.92 | -3507.3 | -3507.3 | -1276.08 | -1630.92 | 0.05 |
scope london, top gated rules:

| feat | book | tail | thr | act | n_L6M | n_OLD | dmean_L3M | dmean_L6M | dmean_OLD | ddd_L3M | ddd_L6M | ddd_OLD | ddd_HOLD | p_rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| carry|MEGAraw|prem|last60 | M7 | ge | 1.0 | skip | 58 | 162 | 378.8 | 1012.37 | 79.71 | -1311.86 | -1311.86 | -1878.08 | -4116.16 | 0.02 |
| carry|QQQ|prem|full | M7 | le | 0.5 | press | 125 | 346 | -159.46 | 19.78 | 72.32 | -599.41 | -599.41 | -2535.7 | 2214.03 | 0.02 |
| carry|MEGAraw|prem|last60 | M7 | ge | 1.0 | half | 58 | 162 | 189.4 | 506.18 | 39.86 | -655.93 | -655.93 | -1259.75 | -2058.08 | 0.02 |
scope nyam, top gated rules:

| feat | book | tail | thr | act | n_L6M | n_OLD | dmean_L3M | dmean_L6M | dmean_OLD | ddd_L3M | ddd_L6M | ddd_OLD | ddd_HOLD | p_rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AMZN|prem|15 | K7 | le | 1.0 | skip | 82 | 296 | 287.42 | 177.01 | 523.0 | -712.18 | -712.18 | -5567.86 | -4633.4 | 0.02 |
| AMZN|prem|15 | K7 | le | 4.0 | skip | 77 | 276 | 241.87 | 175.85 | 515.4 | -712.18 | -712.18 | -5567.86 | -3731.22 | 0.02 |
| AMZN|prem|15 | K7 | le | 2.0 | skip | 80 | 292 | 287.42 | 265.81 | 554.14 | -712.18 | -712.18 | -5567.86 | -4633.4 | 0.02 |
| MSFT|prem|1 | K7 | le | 0.5 | skip | 54 | 260 | -141.8 | 10.36 | 111.33 | -712.18 | -712.18 | -5427.7 | -2139.9 | 0.05 |
scope nypm, top gated rules:

(none)
scope rth, top gated rules:

| feat | book | tail | thr | act | n_L6M | n_OLD | dmean_L3M | dmean_L6M | dmean_OLD | ddd_L3M | ddd_L6M | ddd_OLD | ddd_HOLD | p_rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| carry|QQQ|prem|last60 | ALL | le | 0.5 | press | 185 | 637 | 102.04 | 41.39 | 243.86 | -815.73 | -815.73 | -5426.35 | 1333.11 | 0.02 |
| NVDA|prem|1 | ALL | ge | 4.0 | press | 207 | 851 | 337.17 | 124.66 | 97.77 | -216.32 | -216.32 | -5168.76 | 1007.45 | 0.02 |
| TSLA|prem|1 | M7 | le | 0.5 | press | 68 | 270 | 226.93 | 176.99 | 231.78 | -599.41 | -599.41 | -4535.02 | 0.0 | 0.02 |
| MEGAeq|vol|5 | M7 | ge | 4.0 | press | 98 | 339 | 11.06 | 112.15 | 114.42 | -599.41 | -599.41 | -4501.23 | 920.43 | 0.02 |

## 5. EXACT ENGINE (JN05W2 base, all layers ON, TP engine via UW admission queue; reference = JN05W2 on the same months)
Identity: TL3_UW_MFID (hook registered, rule threshold unreachable) reproduces JN05W2 202610 = 598 trades, net 25943.82 (checked by mf_score.py at each rebuild: see ).

## 6. What is and is not established
- Lead-lag: see section 2. Plain statement: megacap net premium and flow bursts follow price; their lead over NQ at 1/5/15 min after controlling for price is at most about 0.02-0.03 IC in a handful of cells and not beyond chance across the family. Not a standalone signal.
- Triggers: the harness screens show gated cells in NYAM / NYPM above the shifted-flow family null only marginally (see section 3 for counts of draws exceeded); standalone profit shrinks heavily in the engine (section 5).
- Dealer-exposure (gamma/vanna/charm) direction screens were NOT run (closed). Alert-level features belong to W-FA.
- Still arriving: older tape days (rerun then), exact-engine months (HOLD / PREUW), extra burst-family placebo draws. This page rebuilds every 3 h by code/th_uwmf/mf_loop.sh.

