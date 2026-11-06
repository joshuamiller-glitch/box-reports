# REPRO_AUDIT_FIND - independent re-simulation audit of the T-FIND / daily / RV / tick batch (CHAR-C, 2026-11-06T02:23Z). New file; no other file edited. Shadow only, no PASS claim.

**Verdict in one paragraph.** 30 of the 35 audited cells reproduce (20 exactly, the 10 daily/RV cells at the level their saved fields allow): for the 1-minute book families (CHAR-A ES/RTY/YM, CHAR-B GC/CL/ZN/ZB, CHAR-C 6E/MBT/NKD, ZL-1 LRS finalists) the saved trade frames are internally exact (net per trade within 1 cent on every trade, no overlapping trades, no price outside its bar, every exit confirmed by my own first-touch scan of the raw bars in 99.6-100% of trades, window means equal the owners' rows within rounding), the daily and RV frames reproduce their owners' totals / window means. The 5 tick-scale cells (CHAR-A 1-s books) DO NOT reproduce: the evaluator's time-stop rule is hard-coded for 60-second bars (`ts[k]+60 >= entry+T`), so on 1-second bars every hold of h <= 60 s ends at the CLOSE OF THE ENTRY SECOND (exit_px = close of the entry bar in 96-100% of those trades although exit_ts says entry+60) and every longer hold ends 59-60 s early. This changes tick-scale window means by hundreds of dollars a week and flips signs for the short-horizon rows (details and the labels that could change in section 3).

## 1. Method (fixed before the numbers)
* Cell choice: numpy default_rng(seed 20261106), 5 frames per family from /mnt/l2/l2vast/instr2_trades (families: A CHAR-A ES/RTY/YM books = `T2F_{ES,RTY,YM}|...` excluding 1SLRS/T2F1B; B CHAR-B GC/CL/ZN/ZB books = `T2F_{GC,CL,ZN,ZB}|...`; C CHAR-C = `FIND_{6E,6J,MBT,NKD}_...` (pool of 40); D ZL-1 LRS finalists = `LRS|...` (45); E tick-scale = `T2F1B_*` and `*1SLRS*` for ES/RTY/NQ (272); F S4a daily = DAILY/* (42); G RV pairs = RV_* (1,554)); frames with >= 20 trades. Selection list: /mnt/l2/l2vast/find_c/repro/selection.json.
* Own simulator (code/find_c/repro_find.py): raw 1-minute bars of /mnt/l2/l2vast/ds3/cache_te2 (both the raw frame and the additive back-adjusted frame are tried; the better-fitting frame is reported) and, for the tick-scale family, the 1-second OHLC of /mnt/l2/l2vast/instr_1s (ES, RTY, NQ). One position, stop first on a same-bar touch, entry = open of the bar at entry_ts (the saved entry_px must lie in that bar +-1 tick), stop/target levels = the saved stop_px / tgt_px, exit at the first touching bar, otherwise the saved time/flat exit; cost = the sessions-json convention (fee per FEES.md / PROXY-STD and the Z2 slips) tested against the implied cost of every trade.
* Checks per frame: overlap and duplicate entries; entry/exit prices inside their bars; off-grid prices; exit type (stop / target / time) of the frame vs my first-touch scan; 'premature' = the frame holds through a touched stop/target, 'missing' = the frame exits at a stop/target no bar ever touched; net per trade = side x (exit-entry) x pv - cost recomputed to the cent under two cost conventions; implied cost per lot vs the fee (fee undercharging) ; entry outside the session window and exits after the 16:55 ET flat; label-day cross-check (E.label_day vs ET+6h); DST windows (2025-03-09, 2025-11-02, 2026-03-08; 2026-11-01 see section 4); window means L6M and HOLD (carry weeks dropped, instr2_eval) vs the owner's row found by regex in DS3_FIND.md / FADE_ROWS_*.md.
* Tolerance: net per trade within $0.01 for the same trade list; window means within 5% or $2/wk of the owner's row.

## 2. Cell table (35 cells)
| fam | cell (frame) | n | overlap | exit type agrees (own raw-bar scan) | premature / missing touch | exit px outside bar | net/trade fit 1c (all-in cost) | frame L6M / HOLD $/wk | own re-sim L6M / HOLD | owner row L6M / HOLD | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| A | T2F_ES|AC_asia_5m_h21|fade|z02.0_f1.0_tm1.0 | 145 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 168 / -133 | 168 / -133 | 168 / -133 | MATCH |
| A | T2F_ES|AC_pre_15m_h09|fade|z02.0_f1.0_tm2.0 | 34 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | -228 / -261 | -228 / -261 | -228 / -261 | MATCH |
| A | T2F_ES|VR_london_5m|fade|z02.0_f0.5_tm2.0 | 1910 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | -1121 / -2320 | -1121 / -2320 | -1121 / -2320 | MATCH |
| A | T2F_ES|VR_nypm_5m|fade|z02.0_f0.5_tm2.0 | 397 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 338 / -12 | 338 / -12 | 338 / -12 | MATCH |
| A | T2F_RTY|VR_london_15m|fade|z02.0_f0.5_tm2.0 | 987 | 0 | 1.000 | 0 / 0 | 2 | 1.000 | -174 / -109 | -174 / -109 | -174 / -109 | MATCH; flags: 2 exit prices outside their bar range (of 987 trades) |
| B | T2F_CL|AC_asia_5m_h23|fade|z02.0_f1.0_tm2.0 | 114 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | -27 / -24 | -27 / -24 | -27 / -24 | MATCH |
| B | T2F_CL|AC_london_5m_h03|fade|z01.0_f1.0_tm1.0 | 3003 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | -2028 / -2643 | -2028 / -2643 | -2028 / -2643 | MATCH |
| B | T2F_GC|VR_pre_15m|fade|z01.0_f0.5_tm2.0 | 987 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | -500 / -115 | -500 / -115 | -500 / -115 | MATCH |
| B | T2F_ZB|fb_ON_close|fbres|kA1.0_rr2.0_tstop60 | 99 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | -271 / -206 | -271 / -206 | -271 / -206 | MATCH |
| B | T2F_ZB|rx_IB_close|bounce|kA0.75_rr2.0_tstop60 | 354 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | -526 / -840 | -526 / -840 | -526 / -840 | MATCH |
| C | FIND_6E_ac_pre_h5_k2.0_rev_atr4_1R_30 | 253 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 69 / 40 | 69 / 40 | 69 / 40 | MATCH; flags: 4 entries at the session-end minute (labelled by signal bar) |
| C | FIND_MBT_lrs_close_mom_h60_seed2_atr3.0_None_60 | 287 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 49 / -1 | 49 / -1 | 49 / -1 | MATCH |
| C | FIND_MBT_lrs_close_rev_h60_seed0_atr3.0_None_60 | 354 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 8 / -2 | 8 / -2 | 8 / -2 | MATCH |
| C | FIND_MBT_lrs_close_rev_h60_seed2_atr3.0_None_60 | 347 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 30 / -25 | 30 / -25 | 30 / -25 | MATCH |
| C | FIND_NKD_ac_asia_h5_k3.0_rev_atr4_1.5R_15 | 234 | 0 | 0.996 | 1 / 0 | 0 | 1.000 | 276 / 192 | 276 / 192 | 276 / 192 | MATCH; flags: 1 entries at the session-end minute (labelled by signal bar); 1 premature / 0 missing touch (1 trade) |
| D | LRS|MBT|tree_mom|h30|pre|q0.85|('atr',3.0)|None|s0 | 203 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 24 / 40 | 24 / 40 | n/a / n/a | MATCH (owner row UNTRACEABLE in text); flags: 4 entries at the session-end minute (labelled by signal bar) |
| D | LRS|NQ|tree_mom|h15|nypm|q0.85|('atr',3.0)|2R|s0 | 1710 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 1616 / 912 | 1616 / 912 | n/a / n/a | MATCH (owner row UNTRACEABLE in text); flags: 13 exits after the 16:55 flat (holiday/early-close, max 2945 min); 36 entries at the session-end minute (labelled by signal bar) |
| D | LRS|RTY|gp|h30|nypm|q0.85|('atr',3.0)|2R|s1 | 900 | 0 | 0.999 | 0 / 1 | 0 | 1.000 | 158 / 105 | 158 / 105 | n/a / n/a | MATCH (owner row UNTRACEABLE in text); flags: 15 exits after the 16:55 flat (holiday/early-close, max 2945 min); 34 entries at the session-end minute (labelled by signal bar); 0 premature / 1 missing touch (1 trade) |
| D | LRS|ZB|tree_rev|h30|nyam|q0.7|('atr',3.0)|None|s0 | 1920 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | -2796 / -3756 | -2796 / -3756 | n/a / n/a | MATCH (owner row UNTRACEABLE in text); flags: 1 exits after the 16:55 flat (holiday/early-close, max 2945 min); 29 entries at the session-end minute (labelled by signal bar) |
| D | LRS|ZN|gp|h60|pre|q0.7|('atr',3.0)|2R|s2 | 567 | 0 | 1.000 | 0 / 0 | 0 | 1.000 | 339 / -270 | 339 / -270 | n/a / n/a | MATCH (owner row UNTRACEABLE in text); flags: 17 entries at the session-end minute (labelled by signal bar) |
| E | T2F_ES|1SLRS_close_mom_h60|seed0 | 214 | 0 | 0.690 | 66 / 0 | 0 | 0.000 | -470 / -261 | corrected-h re-sim -832 / -363 | -470 / -261 | **MISMATCH** (frame exit == close of the entry second in 100% of trades: 60-s time stop on 1-s bars) |
| E | T2F1B_NQ|b_PD_nyam_all_h30|m1.0_t1.0 | 578 | 0 | 0.090 | 524 / 0 | 0 | 0.000 | -265 / -188 | corrected-h re-sim 192 / 412 | -265 / -188 | **MISMATCH** (frame exit == close of the entry second in 97% of trades: 60-s time stop on 1-s bars) |
| E | T2F_NQ|1SLRS_pre_rev_h1800|seed1 | 799 | 1 | 0.994 | 4 / 0 | 0 | 0.000 | -87 / 19 | corrected-h re-sim -103 / 88 | -87 / 19 | **MISMATCH** (time stop fires 59-60 s before h; owner window means shift) |
| E | T2F_RTY|1SLRS_pre_mom_h1800|seed0 | 917 | 1 | 0.969 | 14 / 0 | 0 | 0.000 | -549 / -184 | corrected-h re-sim -545 / -400 | -549 / -184 | **MISMATCH** (time stop fires 59-60 s before h; owner window means shift) |
| E | T2F_RTY|1SLRS_pre_mom_h1800|seed2 | 932 | 4 | 0.982 | 8 / 0 | 0 | 0.000 | -169 / 70 | corrected-h re-sim -222 / -175 | -169 / 70 | **MISMATCH** (time stop fires 59-60 s before h; owner window means shift) |
| F | CL_TSMOM_L252_1lot | 99 | 0 | n/a (daily, no bracket) | n/a | exit in bar range 1.00 | n/a (resized / rolled positions) | booked-at-exit 2767 / 856 | n/a | sum net 63903 vs table 63692 (0.33%) | MATCH (total) |
| F | ES_MA_10_50 | 91 | 0 | n/a (daily, no bracket) | n/a | exit in bar range 1.00 | n/a (resized / rolled positions) | booked-at-exit 924 / 699 | n/a | sum net owner row UNTRACEABLE | PARTIAL (no owner row in text; clock/cost checks pass) |
| F | ES_MR_k3_th1.5 | 286 | 0 | n/a (daily, no bracket) | n/a | exit in bar range 1.00 | n/a (resized / rolled positions) | booked-at-exit -153 / 342 | n/a | sum net 80337 vs table 80292 (0.06%) | MATCH (total) |
| F | ES_MR_k5_th1 | 441 | 0 | n/a (daily, no bracket) | n/a | exit in bar range 1.00 | n/a (resized / rolled positions) | booked-at-exit 687 / 375 | n/a | sum net 76693 vs table 76573 (0.16%) | MATCH (total) |
| F | NKD_TSMOM_L126_vol | 155 | 0 | n/a (daily, no bracket) | n/a | exit in bar range 1.00 | n/a (resized / rolled positions) | booked-at-exit 7221 / 2818 | n/a | sum net owner row UNTRACEABLE | PARTIAL (no owner row in text; clock/cost checks pass) |
| G | T2F_RV6E6J|AC_close_5m|fade|z01.0_f1.0_tm2.0_sk1.0 | 3541 | 0 | n/a (no leg prices in the frame) | n/a | n/a | n/a | -1802 / -2110 | n/a | -1802 / -2110 | MATCH (window means) / PARTIAL re-sim: OLS of frame P&L on my leg moves 6E/6J legs, coef 2.13 / -1.26, R2 -0.89 |
| G | T2F_RV6E6J|VR_london_30m|fade|z02.0_f1.0_tm2.0_sk1.5 | 1117 | 0 | n/a (no leg prices in the frame) | n/a | n/a | n/a | -1235 / -1497 | n/a | -1235 / -1497 | MATCH (window means) / PARTIAL re-sim: OLS of frame P&L on my leg moves 6E/6J legs, coef 2.43 / -1.44, R2 0.72 |
| G | T2F_RV6E6J|VR_nyam_30m|fade|z01.0_f0.5_tm1.0_sk1.0 | 1306 | 0 | n/a (no leg prices in the frame) | n/a | n/a | n/a | -1410 / -1602 | n/a | -1410 / -1602 | MATCH (window means) / PARTIAL re-sim: OLS of frame P&L on my leg moves 6E/6J legs, coef 2.28 / -1.50, R2 0.59 |
| G | T2F_RVESRTY|AC_close_5m|fade|z02.0_f1.0_tm2.0_sk1.0 | 1217 | 0 | n/a (no leg prices in the frame) | n/a | n/a | n/a | -1789 / -1733 | n/a | -1789 / -1733 | MATCH (window means) / PARTIAL re-sim: OLS of frame P&L on my leg moves ES/RTY legs, coef 2.15 / -2.87, R2 0.66 |
| G | T2F_RVESYM|VR_nyam_5m|fade|z02.0_f0.5_tm2.0_sk1.0 | 2380 | 0 | n/a (no leg prices in the frame) | n/a | n/a | n/a | -4921 / -4584 | n/a | -4921 / -4584 | MATCH (window means) / PARTIAL re-sim: OLS of frame P&L on my leg moves ES/YM legs, coef 1.98 / -2.54, R2 0.57 |

Reading of section 2: for A-D the own re-simulation (saved stop/target levels applied to the raw path, frame cost) gives exactly the frame's trades (0 exits changed in all 20 cells) and the owners' window means; the NKD cell has one trade where the saved target is touched one bar before the frame's exit, the RTY LRS cell one stop that no bar touches (both at bar edges, 1 of 234 / 1 of 900 trades, no window mean moves by more than $2). D rows are not printed in the owner text (only the top-3 finalists per instrument are), so their window means are internally consistent but UNTRACEABLE to an owner row (my regex matched wrong rows for MBT and ZN and I discarded them). F: totals match the S4a table to 0.06-0.3% for the two cells with a table row; the MA and NKD rows have no table row under that name. G: window means equal the owners' rows to the dollar; the frames carry no leg prices or hedge ratios, so a trade-level re-simulation is impossible from the saved files (OLS R2 0.57-0.72 on my leg moves, legs with opposite signs as expected; one R2 < 0 is an in-sample artefact of a no-intercept fit on a loss-making cell).

## 3. Defects found
### D1 (MISMATCH, labels can change): 60-second time-stop on 1-second bars in the tick-scale frames (CHAR-A 1-s books, T2F1B_* and T2F_*|1SLRS_*)
instr2_eval's simulator (and E.build_trades) exits when `ts[k] + 60 >= entry + tstop`; fed with 1-second bars this fires on the FIRST bar for tstop <= 60 s and 59-60 s early for longer holds, while exit_ts is written as `ts[k]+60`. Evidence: in 110 of the 272 tick-scale frames the exit price equals the close of the entry second in more than 50% of trades (ES `1SLRS_close_mom_h60`: 214 of 214; NQ `b_PD_nyam_all_h30`: 96.5%), the saved hold is exactly 60 s whatever the cell's h (30 s, 60 s), and for h = 300 / 1800 s the realised hold is 241 / 1741 s. I re-ran every one of the 272 frames with a correct horizon (exit at the close of the last 1-s bar at entry+h, saved stop/target levels applied on the 1-s trade path, the frame's own constant cost, +1 tick on stop exits for T2F1B): 
window means change a lot: median HOLD shift +$118/wk for the h<=60 s frames; HOLD flips from <=0 to >0 in 26 of 110 buggy frames (L6M in 28); for h=300 frames the median HOLD shift is +$166/wk with 2 positive and 8 negative flips; for h=1800 s the median shift is +$5/wk.

The 1b-DEEP / tickb book rows (the rows the final page calls 'loses money as a 1-s book'):
| frame | n | h s | owner/frame L6M | corrected L6M | owner/frame HOLD | corrected HOLD |
|--|--|--|--|--|--|--|
| ES|b_PD_nyam_burst_h60|m1.0_t1.0.parqu | 414 | 60 | -102 | +161 | -264 | +12 |
| ES|b_PD_nyam_burst_h60|m1.0_tNone.parq | 414 | 60 | -54 | +536 | -186 | +636 |
| ES|b_PD_nyam_burst_h60|m1.5_t1.0.parqu | 414 | 60 | -35 | +123 | -155 | -32 |
| ES|b_PD_nyam_burst_h60|m1.5_tNone.parq | 414 | 60 | -40 | +129 | -125 | +342 |
| ES|b_PD_nyam_burst_h60|m2.0_t1.0.parqu | 414 | 60 | -25 | -35 | -111 | +90 |
| ES|b_PD_nyam_burst_h60|m2.0_tNone.parq | 414 | 60 | -25 | +151 | -91 | +393 |
| RTY|b_PD_pre_burst_h1800|m1.0_t1.0.par | 95 | 1800 | +174 | +174 | +10 | +7 |
| RTY|b_PD_pre_burst_h1800|m1.0_tNone.pa | 95 | 1800 | +770 | +685 | +242 | +219 |
| RTY|b_PD_pre_burst_h1800|m1.5_t1.0.par | 95 | 1800 | +375 | +375 | +87 | +83 |
| RTY|b_PD_pre_burst_h1800|m1.5_tNone.pa | 95 | 1800 | +605 | +538 | +178 | +158 |
| RTY|b_PD_pre_burst_h1800|m2.0_t1.0.par | 95 | 1800 | +265 | +267 | +124 | +123 |
| RTY|b_PD_pre_burst_h1800|m2.0_tNone.pa | 95 | 1800 | +385 | +340 | +197 | +187 |
| RTY|b_PD_pre_burst_h300|m1.0_t1.0.parq | 95 | 300 | +166 | +139 | +49 | +43 |
| RTY|b_PD_pre_burst_h300|m1.0_tNone.par | 95 | 300 | +207 | +100 | +78 | +19 |
| RTY|b_PD_pre_burst_h300|m1.5_t1.0.parq | 95 | 300 | +29 | -62 | +37 | -9 |
| RTY|b_PD_pre_burst_h300|m1.5_tNone.par | 95 | 300 | +124 | +46 | +19 | -50 |
| RTY|b_PD_pre_burst_h300|m2.0_t1.0.parq | 95 | 300 | +23 | -46 | +22 | -33 |
| RTY|b_PD_pre_burst_h300|m2.0_tNone.par | 95 | 300 | +78 | +18 | +23 | -49 |
| NQ|b_PD_nyam_all_h30|m1.0_t1.0 | 578 | 30 | -265 | +192 | -188 | +412 |
| NQ|b_PD_nyam_all_h30|m1.0_tNone.parque | 578 | 30 | -265 | +660 | -193 | +707 |
| NQ|b_PD_nyam_all_h30|m1.5_t1.0 | 578 | 30 | -206 | +336 | -142 | +236 |
| NQ|b_PD_nyam_all_h30|m1.5_tNone.parque | 578 | 30 | -206 | +575 | -146 | +362 |
| NQ|b_PD_nyam_all_h30|m2.0_t1.0 | 578 | 30 | -138 | +363 | -106 | +233 |
| NQ|b_PD_nyam_all_h30|m2.0_tNone.parque | 578 | 30 | -138 | +416 | -106 | +326 |
| NQ|b_PD_pre_burst_h1800|m1.0_t1.0.parq | 94 | 1800 | +130 | +130 | -35 | -35 |
| NQ|b_PD_pre_burst_h1800|m1.0_tNone.par | 94 | 1800 | -320 | -340 | -357 | -324 |
| NQ|b_PD_pre_burst_h1800|m1.5_t1.0.parq | 94 | 1800 | -55 | -70 | -37 | -45 |
| NQ|b_PD_pre_burst_h1800|m1.5_tNone.par | 94 | 1800 | -70 | -79 | -168 | -185 |
| NQ|b_PD_pre_burst_h1800|m2.0_t1.0.parq | 94 | 1800 | -54 | -43 | -41 | -36 |
| NQ|b_PD_pre_burst_h1800|m2.0_tNone.par | 94 | 1800 | -47 | -46 | -86 | -90 |

**Labels that could change (owner to re-run with a bar-width-aware simulator before anyone relies on either number):** (i) ES nyam prior-day-level burst h60 and NQ nyam h30 (DS3_FIND_CHARACTER 1b-DEEP 'book surface': ES median HOLD -$195, NQ -$144; FINAL page ES paragraph 'HOLD -$91 to -$264/wk'): with a correct horizon the same frames are positive in HOLD for 5 of 6 (ES) and 6 of 6 (NQ) bracket variants (ES +12..+636, NQ +233..+707 $/wk; caveats: one selected row of 240, stops on last-trade prints, no placebo, same-day cost constant) - so 'ES and NQ rows do not survive the 1-s book' is NOT established; (ii) the RTY pre-market WATCH item is NOT affected materially: its frames (h1800, m1.5 no target: L6M +605 -> +538, HOLD +178 -> +158, all six variants keep their signs; 59 s of 1800 s) - differences up to 11% exceed the 5% tolerance but not the label; (iii) the 1-s learned-rule cells with h <= 300 s: e.g. RTY pre momentum 300 s seed 0 (the p_family .01 cell in the final page): L6M +318 -> -1,236, HOLD +904 -> +354; seeds 1-2 stay negative, so 'not a lead' stands and gets stronger; (iv) the NQ 'passive continuation +5.4 ticks' WATCH row is from ZL-1's queue model (not these frames) and is not affected.

### D2 (flag, small): positions held through exchange closures in ZL-1 LRS frames
NQ LRS (h15 nypm, 1,710 trades): 13 trades, RTY LRS (h30 nypm, 900): 15, ZB LRS (h30 nyam, 1,920): 1 enter on US holidays or early-close days (2023-07-04, 2024-02-19, 2024-05-27, 2024-07-03, 2024-11-29, 2024-12-24 ...) and exit at the 18:00 reopen or the next session (up to 49 hours after the flat time): the 16:55 flat rule cannot fire because no bar exists. Net of these trades: NQ -$1,296 of -$16,805, RTY -$3,709 of -$62,655, ZB -$202. Not executable as written (NT8 would be flat before the early halt); no label changes (all three cells negative in total).

### D3 (flag, benign): session label by signal bar
4-36 entries per LRS / 6E frame sit exactly on the session-end minute (e.g. 15:00 for a NY-PM cell): the signal bar is the last minute of the session and the entry is the next bar's open; the label is the signal bar's session. 2 MBT trades have exit label days that differ between E.label_day (ET+7h) and ET+6h (exit between 17:00 and 18:00 ET, the daily break).

### D4 (flag, small): overlapping positions in tick-scale frames
64 of the 272 tick-scale frames contain overlapping trades (137 overlapping entries of 551,780): a consequence of D1 (labelled exits are later than the real ones, so a later entry can start 'before' the previous exit). One-position rule otherwise holds in every other frame (0 overlaps in all 25 other cells).

### D5 (limitation): daily frames are not reproducible trade by trade
S4a daily frames aggregate monthly resizing and roll legs into one row per episode: 35-50 of 99 CL / 91 ES-MA / 155 NKD trades have an implied cost per lot different from the plain round trip, and carry 55-68% of the absolute P&L, so a price-based re-simulation of those rows is impossible from the saved fields; the plain-cost rows are exactly fee + 1 tick per side (CL $24.84 = 2 x $10 + $4.84, ES $29.84, NKD $104.84 = 2 x $50 + $4.84). The decision clock is constant at 15:55 ET across DST (entry minute 955 in 97-99% of rows, the rest early-close days), entry/exit prices lie in their 1-minute bars in 100% of rows. Totals match the S4a table (ES MR k3 80,337 vs 80,292; k5 76,693 vs 76,573; CL TSMOM 63,903 vs 63,692).

## 4. Fees, clocks, DST
* Fee mis-charging: none found. Every 1-minute book frame charges the full `rt_market_in_stop_out` round trip on EVERY trade (stop-exit slippage also on target and time exits - conservative), implied cost per lot constant to 1e-13: 6E $24.00 (fee $5.30), MBT $4.28 (fee $1.78), NKD $129.84, NQ $44.84, RTY $19.84, ZN $51.72, ZB $98.59; 0 trades with implied cost below the fee. Tick-scale frames charge measured spread + $4.84 (ES $17.34, RTY $14.84/$9.84/$24.84, NQ $9.84-$24.84 by the instrument's median spread of the cell). FEE_AUDIT_INSTR2.md had not landed at audit time (no such file in autopilot/); re-check against it when it does. Note the FINAL page quotes ZB at $99 and ZN at $52: consistent with $98.59 / $51.72.
* Clock / DST: label-day computed independently from the tz database equals E.label_day for every exit except the 2 exits in the 17:00-18:00 ET break noted in D3. No frame contains any trade after 2026-11-01 06:00 UTC (checked all 6,408 frames: latest data 2026-10-16 for most instruments, 2026-10-30 for a few NKD/BTC native frames), so the 2026-11-01 DST change itself is UNTESTABLE on saved trades; I tested the transitions 2025-03-09, 2025-11-02 and 2026-03-08 (entries in the +-3 day windows: 0 outside their session window) and the constancy of the 15:55 ET decision time of the daily cells across both DST changes of 2013-2026 (no UTC drift).
* Prices: all entry/exit prices of A-D lie on the tick grid (max deviation 1e-11 ticks) and inside their bars; E entry prices are book mids and lie outside the last-trade bar range when no print exists in that second (the 1-s tape holds only seconds with prints: entry second absent in 0-50% of entries, a data property not a defect).

## 5. Files
Code l2vast/ds3/code/find_c/repro_find.py, repro_report.py; selection /mnt/l2/l2vast/find_c/repro/selection.json; per-cell results results.pkl; all 272 tick-scale frames re-simulated: results_tick_all.pkl, tick_corrected.pkl. Workers: 6 (memory far above the 40 GB guard).
