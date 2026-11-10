# DS3_PRODUCTS_ZONEBOOKS - zone-as-entry books on ES and RTY (T-NEXT Part B2, ZN-BOOK) - 2026-11-10 17:03Z

Research only, Shadow only, post-hoc, no PASS claims, PRE-PROOF. Prereg: ZN_ZBOOKS_PREREG.md (sha line in DECISIONS.md). Code: code/th_zb (zb_master, zb_levels, zb_core, zb_run, zb_export, zb_final). Data: FD-LIQ slim L2 state days (ES, RTY: 2023-08-01..2026-10-30; no prints, so NO delta/absorption triggers and NO VWAP families; X' covers only 2023-08..2024-01; the 11-02..05 live week is not in the data). 13 rolls back-adjusted. Grid per instrument = ZN-TRIG's: 58 level families / 99 lines x triggers touch-reject (TR), break-through (BRK), failed-break fade (FB), break-and-retest (BR) x 1-m/5-m bars x zone width x 6 sessions x 192 brackets (NQ-equivalent points, scale ES 0.2, RTY 0.096), equal-$-risk lots R=$1,200 cap 10, 1 tick slippage each side, $4.84 RT fees (RTY proxy). All numbers first-order on 1-s paths; trades are exported in the FD schema (/mnt/l2/l2vast/_th_zn/zb/trades/).

## ES

**Search:** 735168 cells, 320565 with minimum samples, 9937 pass the tolerant gate (L3M, L6M > 0; PRE, X' >= -0.5 MDE), 3909 of those also have |weekly corr to the stack| <= .30 and a positive HOLD stack-Calmar gain. Family null over the WHOLE grid (200 weekly sign-flip draws applied to every cell jointly): the null max t has median 4.23 / 95th 4.87; the best observed pooled t is 2.738889455795288; the smallest family p of any gate-passing cell is 1.0.

**Finalists (33, top 5 per session + top 10 overall by pooled t, gate + corr + HOLD gain, one bracket per cell)** - SEAT bar = add at the $1,200 unit on the NQ stack at equal mean; STANDALONE bar D8 = the book alone (own L6M/L3M Calmar, maxDD, PRE, placebo, family null, WF).

| id | session | trigger | level family | bar | trades | L6M mean $/wk | L6M maxDD | L6M Calmar | L3M mean | PRE mean | X' mean | corr wk | SEAT add: equal-mean cut L6M/PRE % | seat placebo p L6M | p family (whole search) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES.ZB_TR_PD_RTH.4fb3b26a | nyam | TR | PD_RTH | 1m | 312 | 3492 | 12023 | 15.10 | 1027 | 203 | 1563 | 0.06 | -0.5/2.2 | 0.35 | 1.00 |
| ES.ZB_TR_KC1.5_15m.c78e0414 | pre | TR | KC1.5_15m | 1m | 252 | 1402 | 5147 | 14.17 | 3152 | 248 | -151 | -0.10 | 3.3/7.0 | 0.13 | 1.00 |
| ES.ZB_TR_PD_RTH.decbb54c | nyam | TR | PD_RTH | 1m | 331 | 3302 | 13560 | 12.66 | 173 | 413 | 835 | 0.11 | -2.1/1.6 | 0.56 | 1.00 |
| ES.ZB_TR_ON.b8aa4ff7 | nyam | TR | ON | 5m | 289 | 1213 | 5889 | 10.71 | 468 | 318 | -95 | -0.03 | 0.9/1.7 | 0.30 | 1.00 |
| ES.ZB_TR_KC1.5_5m.6de17c1a | pre | TR | KC1.5_5m | 1m | 435 | 2877 | 17025 | 8.79 | 5399 | -360 | 101 | -0.10 | 4.8/1.1 | 0.09 | 1.00 |
| ES.ZB_TR_KC1.5_15m.11cd92a3 | pre | TR | KC1.5_15m | 1m | 399 | 2149 | 13185 | 8.47 | 2982 | -435 | 1044 | -0.13 | 3.8/11.4 | 0.22 | 1.00 |
| ES.ZB_TR_OR15.57a429fa | nyam | TR | OR15 | 5m | 334 | 441 | 2984 | 7.68 | 142 | 141 | 231 | 0.07 | -0.2/1.6 | 0.50 | 1.00 |
| ES.ZB_BRK_KIJUN60.b22ad23d | nyam | BRK | KIJUN60 | 1m | 612 | 1570 | 11310 | 7.22 | 2020 | 165 | 324 | 0.06 | 2.7/-0.5 | 0.24 | 1.00 |
| ES.ZB_BRK_S_ASIA.060adcaa | close | BRK | S_ASIA | 1m | 363 | 1024 | 7414 | 7.18 | 1002 | 204 | 8 | 0.01 | -3.3/0.7 | 0.67 | 1.00 |
| ES.ZB_FB_KC2.5_5m.338b635e | close | FB | KC2.5_5m | 1m | 289 | 421 | 3136 | 6.99 | 772 | 3 | 54 | 0.06 | -0.4/-1.4 | 0.50 | 1.00 |
| ES.ZB_BRK_PD_FULL.8b9bfbc4 | asia | BRK | PD_FULL | 5m | 450 | 737 | 6631 | 5.78 | 592 | 281 | -13 | -0.01 | -2.6/0.8 | 0.73 | 1.00 |
| ES.ZB_TR_PD_RTH.4aae3af8 | london | TR | PD_RTH | 1m | 346 | 305 | 3393 | 4.68 | 283 | -17 | 118 | 0.00 | 0.7/0.8 | 0.15 | 1.00 |
| ES.ZB_BR_IB30X15.782201c0 | nyam | BR | IB30X15 | 1m | 271 | 1295 | 16398 | 4.11 | 1807 | 780 | -287 | -0.03 | -1.8/7.8 | 0.49 | 1.00 |
| ES.ZB_TR_KC1.5_5m.63647097 | close | TR | KC1.5_5m | 1m | 440 | 931 | 14280 | 3.39 | 1816 | -360 | 397 | -0.10 | -6.0/-0.8 | 0.81 | 1.00 |

**Bi-weekly re-pick WF (restricted to these 33 finalists: every 2 weeks pick the finalist with the best trailing-26-week Calmar, trade the next 2 weeks):** 72 periods, positive in 44% of them, OOS mean -109 $/wk, maxDD 31450, Calmar -0.18. This is a restricted version of the procedure (the full search is not re-run) and fails the >= 60% bar.

**Bars:** SEAT bar (add at equal mean, corr <= .30, placebo p <= .10, both L6M and PRE cuts > 0): 3 finalists clear the first-order screen. STANDALONE bar D8 (L6M and L3M mean > 0, PRE mean > 0, search-level family p <= .10, WF >= 60%): 0 finalists; none clears the whole bar because the WF is 44% and the family p is 1.0.

**ES verdict (plain):** no zone-entry book on ES is distinguishable from the best of the search: the best pooled t (2.738889455795288) is below the median null max (4.23). The highest-Calmar finalist is ES.ZB_TR_PD_RTH.4fb3b26a (nyam session, TR on PD_RTH, 1m bars): L6M 3492 $/wk at maxDD 12023, but PRE 203 and X' 1563 $/wk, seat add cut -0.5% (L6M) with placebo p 0.35. Seat bar: first-order screen only, fails the family null. Standalone: no.

## RTY

**Search:** 738432 cells, 332185 with minimum samples, 10483 pass the tolerant gate (L3M, L6M > 0; PRE, X' >= -0.5 MDE), 4070 of those also have |weekly corr to the stack| <= .30 and a positive HOLD stack-Calmar gain. Family null over the WHOLE grid (200 weekly sign-flip draws applied to every cell jointly): the null max t has median 4.22 / 95th 4.9; the best observed pooled t is 1.8369932174682617; the smallest family p of any gate-passing cell is 1.0.

**Finalists (30, top 5 per session + top 10 overall by pooled t, gate + corr + HOLD gain, one bracket per cell)** - SEAT bar = add at the $1,200 unit on the NQ stack at equal mean; STANDALONE bar D8 = the book alone (own L6M/L3M Calmar, maxDD, PRE, placebo, family null, WF).

| id | session | trigger | level family | bar | trades | L6M mean $/wk | L6M maxDD | L6M Calmar | L3M mean | PRE mean | X' mean | corr wk | SEAT add: equal-mean cut L6M/PRE % | seat placebo p L6M | p family (whole search) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTY.ZB_TR_S_NYAM.dfa64cdb | nypm | TR | S_NYAM | 5m | 219 | 474 | 203 | 121.37 | 838 | 19 | 202 | 0.01 | 2.7/3.0 | 0.08 | 1.00 |
| RTY.ZB_FB_PD_RTH.22167c36 | nyam | FB | PD_RTH | 1m | 602 | 4291 | 12396 | 18.00 | 469 | -302 | -323 | 0.03 | -6.8/3.1 | 0.68 | 1.00 |
| RTY.ZB_FB_PD_RTH.ac68a49a | nyam | FB | PD_RTH | 1m | 602 | 4291 | 12396 | 18.00 | 469 | -302 | -323 | 0.03 | -6.8/3.1 | 0.68 | 1.00 |
| RTY.ZB_BRK_EMA20_60m.17a03712 | pre | BRK | EMA20_60m | 1m | 311 | 455 | 2320 | 10.19 | 660 | 104 | 62 | -0.16 | 2.4/1.9 | 0.09 | 1.00 |
| RTY.ZB_TR_SW5m3.85f8befc | pre | TR | SW5m3 | 1m | 280 | 2866 | 16051 | 9.29 | 2240 | 376 | -666 | -0.06 | -0.7/5.6 | 0.30 | 1.00 |
| RTY.ZB_BRK_PD_FULL.f07cfb2c | nyam | BRK | PD_FULL | 5m | 653 | 2034 | 13783 | 7.67 | 1523 | 121 | -551 | 0.05 | 4.1/-0.2 | 0.10 | 1.00 |
| RTY.ZB_FB_RN5.5de3a61a | close | FB | RN5 | 1m | 1324 | 1628 | 11995 | 7.06 | 1228 | 318 | -443 | -0.03 | -5.6/7.1 | 0.70 | 1.00 |
| RTY.ZB_FB_RN5.76a18e8a | close | FB | RN5 | 1m | 1324 | 1628 | 11995 | 7.06 | 1228 | 318 | -443 | -0.03 | -5.6/7.1 | 0.70 | 1.00 |
| RTY.ZB_TR_KC2.5_5m.95c5130a | nypm | TR | KC2.5_5m | 5m | 240 | 509 | 4152 | 6.37 | 803 | 176 | -42 | 0.11 | 1.1/3.0 | 0.22 | 1.00 |
| RTY.ZB_BR_EMA50_5m.31ba7b53 | nyam | BR | EMA50_5m | 5m | 285 | 1440 | 11995 | 6.24 | 2396 | -40 | -111 | -0.05 | 6.8/6.7 | 0.06 | 1.00 |
| RTY.ZB_BR_EMA50_5m.65434ba4 | nyam | BR | EMA50_5m | 5m | 325 | 1351 | 11392 | 6.17 | 2154 | -48 | -313 | -0.03 | 3.9/5.6 | 0.13 | 1.00 |
| RTY.ZB_TR_KC2.5_60m.5de478b2 | london | TR | KC2.5_60m | 1m | 306 | 903 | 10167 | 4.62 | 686 | 32 | -18 | 0.05 | -0.1/0.0 | 0.34 | 1.00 |
| RTY.ZB_FB_KC2.5_60m.9b4b2d7f | london | FB | KC2.5_60m | 1m | 379 | 281 | 3283 | 4.45 | 24 | 165 | 116 | 0.03 | -0.5/-1.4 | 0.56 | 1.00 |
| RTY.ZB_FB_KC2.5_60m.fcf28d14 | london | FB | KC2.5_60m | 1m | 379 | 281 | 3283 | 4.45 | 24 | 165 | 116 | 0.03 | -0.5/-1.4 | 0.56 | 1.00 |

**Bi-weekly re-pick WF (restricted to these 30 finalists: every 2 weeks pick the finalist with the best trailing-26-week Calmar, trade the next 2 weeks):** 72 periods, positive in 47% of them, OOS mean 144 $/wk, maxDD 35029, Calmar 0.21. This is a restricted version of the procedure (the full search is not re-run) and fails the >= 60% bar.

**Bars:** SEAT bar (add at equal mean, corr <= .30, placebo p <= .10, both L6M and PRE cuts > 0): 6 finalists clear the first-order screen. STANDALONE bar D8 (L6M and L3M mean > 0, PRE mean > 0, search-level family p <= .10, WF >= 60%): 0 finalists; none clears the whole bar because the WF is 47% and the family p is 1.0.

**RTY verdict (plain):** no zone-entry book on RTY is distinguishable from the best of the search: the best pooled t (1.8369932174682617) is below the median null max (4.22). The highest-Calmar finalist is RTY.ZB_TR_S_NYAM.dfa64cdb (nypm session, TR on S_NYAM, 5m bars): L6M 474 $/wk at maxDD 203, but PRE 19 and X' 202 $/wk, seat add cut 2.7% (L6M) with placebo p 0.08. Seat bar: first-order screen only, fails the family null. Standalone: no.

## NQ reference and what is not done yet

- NQ zone-entry books (ZN-TRIG, ZN_TRIG.md, 1.33M cells with delta/absorption triggers): family max-stat p of any cell 0.951; best-of-F rows are not candidates. This ES/RTY grid reproduces the same picture on price-only triggers.
- Dressing with the full D7 layer set (ER sizer, zone HALF, state cut, locks, stack rules; top-K per layer on the book's own trades): the finalist lists are exported for FD-LIQ (registry: /mnt/l2/l2vast/_th_zn/zb/registry_ZBOOKS.csv, trades under /mnt/l2/l2vast/_th_zn/zb/trades/). Not run by me; the dressed rows will be scored on both bars when FD-LIQ publishes them.
- D8 container (FD-CORE) and measured fills / participation cap: this page uses equal-$-risk lots capped at 10 and a 1-tick slippage model; ES/RTY measured fills are not calibrated.
- Structural-zone versions for the no-L2 products (YM GC CL ZN ZB 6E 6J MBT NKD): not started (needs FD-NOL2 1-min bars to 2026-10-16 and the structural level files); ZN-STRUCT's level files can be reused.
- Next refresh: 4 h; FINAL 2026-11-11 18:00Z.
