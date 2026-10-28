# DS3_SESSION2_B_tr4 - T-TREND R5/R7A (TR4) entry-clock re-run and session scoring

Written 2026-10-28T20:59:35Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tr4/. Prereg l2vast/ds3/prereg/SB3_tr4_prereg.md sha256 fcf9873bc32e03bc8e6566bc2a9dc5d2a85ac7607a2c4c37635f597b21dcdc94; PREHOLD autopilot/DS3_SESSION2_B_tr4_PREHOLD.md sha256 fe2d2ef33f7d57e18f2adf79c82178aac6b0f4039b520820feafb6bbf8ebb532 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original code (tr4_r5.prep/gate + tr4_lib.book_from for the 30 R5 cells; for R7A the stored walk-forward/CPCV predictions out/TR4/r7_models.pkl assembled with tr4_r7.assemble and thresholded at the cell theta, then tr4_lib.book_from), exact per-book lock engine at 10 lots x event size multiplier (TD x1.5, QUIET-half x0.5), mapped corrected-P9 points. Table = executed (f>0) trades, entry time = Ctx et_in (ET, bar END stamp as in the ledger), pnl = engine net $, lots = 10 x multiplier, basis MAPPED. R7A models were NOT retrained: the stored out-of-fold predictions are the source's own artefact.

Reproduction: regenerated weekly-engine daily $ series equals the stored 'daily' in out/TR4/r5_final.pkl / r7_final.pkl for 56 of 56 cells that have a book (rtol 1e-6); 2 R7A cells (R7_SM_notape_60, R7_EM_notape_60) have < 30 trades and no book in the source either (no trades emitted): 100% of reproducible cells. out/sb3/tr4/repro.csv.

## 2. Multiplicity and counts
- Cells 56; F = cells x 7 sessions = **392**; overlap clusters (Jaccard >= 0.5, PRE entries) **46**, F_eff = **322**. Independent (cluster x session) PRE tests with n >= 100: 96; PRE-selected cell-sessions 14 = 11 independent (chance at 2.5% one-sided = about 2).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 2, DEAD-IN-HOLD 12; alive cells 2, alive clusters 2. HOLD sign persistence of the selected list: 36%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 30 | 3 | 2 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 30 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 8 | 1 | 1 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 26 | 5 | 4 | 1 | 0 | 1 | R5_DW_HM | 1500 | 1837 |
| NY-PM | 12:00-15:00 | 21 | 1 | 1 | 1 | 0 | 1 | R5_QUIET_KB | 2227 | 2369 |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 31 | 4 | 3 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R5_QUIET_KB | NY | 568 | 7.57 | 1415 | 1155 | 3.43 | 0.55 | 326 | -393 | -221 | -996 | 119 | -385 | 1437 | 608 | -996 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 864 | 19 |
| R5_TD_KB | NY | 775 | 10.3 | 1072 | 979 | 3.07 | 0.54 | 345 | -140 | -51.0 | -516 | 106 | -181 | 1227 | 463 | -516 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 709 | 19 |
| R5_QUIET_KB | NY-PM | 188 | 2.51 | 2227 | 2369 | 2.63 | 0.59 | 95.0 | 338 | 168 | 1119 | 318 | -635 | 2369 | 1185 | 1119 | SESSION-CANDIDATE |  | BOF:not cleared | 864 | 19 |
| R5_IM5_EM | NY | 176 | 2.35 | 2155 | 2310 | 2.61 | 0.59 | 60.0 | -290 | -728 | 3654 | -490 | 3.48 | 2175 | 471 | 3654 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 543 | 13 |
| R5_TD_KB | NY-AM | 517 | 6.89 | 1103 | 1227 | 2.52 | 0.54 | 239 | -197 | -27.3 | -839 | 2.62 | -217 | 1107 | 597 | -839 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 709 | 19 |
| R5_IM1_KB | ASIA | 573 | 7.64 | 971 | 1103 | 2.47 | 0.54 | 253 | -411 | -782 | 895 | 707 | 804 | 789 | 291 | 895 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 557 | 11 |
| R5_TD_SM | ASIA | 242 | 3.23 | 1760 | 2151 | 2.29 | 0.58 | 112 | 436 | 690 | -547 | 344 | 189 | 1444 | 1522 | -547 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 741 | 16 |
| R5_DW_HM | NY-AM | 217 | 2.89 | 1500 | 1837 | 2.29 | 0.57 | 79.0 | 1236 | 925 | 3654 | -835 | -845 | 783 | 1740 | 3654 | SESSION-CANDIDATE |  | BOF:not cleared | 774 | 2 |
| R5_DW_HM | NY | 390 | 5.20 | 1015 | 1246 | 2.28 | 0.54 | 144 | -44.7 | -217 | 1331 | -646 | -896 | 1126 | 310 | 1331 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 774 | 2 |
| R5_IM5_SM | ASIA | 178 | 2.37 | 1773 | 2279 | 2.18 | 0.58 | 85.0 | -850 | -396 | -2540 | 101 | -129 | 1211 | 1245 | -2540 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 861 | 16 |
| R5_HTF3_ST | NY-AM | 466 | 6.21 | 1003 | 1314 | 2.14 | 0.53 | 208 | 331 | -24.9 | 2528 | -1062 | -398 | 743 | 226 | 2528 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 323 | 10 |
| R5_TD_EM | NY-AM | 171 | 2.28 | 1791 | 2416 | 2.08 | 0.58 | 74.0 | 168 | -12.5 | 1100 | 731 | 796 | 1608 | 972 | 1100 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 660 | 17 |
| R5_QUIET_KB | NY-AM | 380 | 5.07 | 1013 | 1375 | 2.06 | 0.54 | 231 | -693 | -394 | -1650 | 28.8 | -284 | 971 | 329 | -1650 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 864 | 19 |
| R5_ZNOK_ST | PREOPEN | 125 | 1.67 | 1816 | 2479 | 2.05 | 0.58 | 47.0 | -2571 | -2732 | -1655 | -139 | 383 | 778 | 256 | -1655 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 519 | 0 |
| R5_ZNOK_KB | NY-AM | 471 | 6.28 | 883 | 1253 | 1.97 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 576 | 19 |
| R5_IM5_SM | NY | 200 | 2.67 | 1300 | 1848 | 1.97 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 861 | 16 |
| R5_IM5_ST | ASIA | 436 | 5.81 | 1061 | 1513 | 1.96 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 532 | 12 |
| R5_HTF3_EM | NY | 144 | 1.92 | 1547 | 2237 | 1.94 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 368 | 6 |
| R5_BR70_ST | PREOPEN | 100 | 1.33 | 2038 | 2956 | 1.93 | 0.59 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 430 | 0 |
| R5_TD_EM | NY | 286 | 3.81 | 1163 | 1743 | 1.87 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 660 | 17 |
| R5_QUIET_HM | ASIA | 391 | 5.21 | 869 | 1343 | 1.81 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 426 | 18 |
| R5_IM1_ST | ASIA | 398 | 5.31 | 982 | 1575 | 1.75 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 435 | 12 |
| R5_QUIET_EM | NY | 198 | 2.64 | 1290 | 2077 | 1.74 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 653 | 17 |
| R5_DW_KB | NY | 495 | 6.60 | 779 | 1258 | 1.73 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 407 | 3 |
| R5_HTF3_ST | NY | 691 | 9.21 | 620 | 1032 | 1.68 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 323 | 10 |
| R5_ZNOK_ST | NY-AM | 481 | 6.41 | 850 | 1415 | 1.68 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 519 | 0 |
| R5_QUIET_KB | ASIA | 415 | 5.53 | 946 | 1579 | 1.68 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 864 | 19 |
| R5_ZNOK_KB | NY | 760 | 10.1 | 612 | 1062 | 1.61 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 576 | 19 |
| R5_DW_HM | ASIA | 351 | 4.68 | 860 | 1497 | 1.61 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 774 | 2 |
| R5_HTF3_KB | NY | 634 | 8.45 | 692 | 1223 | 1.58 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 464 | 8 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R5_QUIET_KB | NY | 568 | 7.57 | 1415 | 1155 | 3.43 | 0.55 | 326 | -393 | -221 | -996 | 119 | -385 | 1437 | 608 | -996 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 864 | 19 |
| R5_IM5_EM | NY | 176 | 2.35 | 2155 | 2310 | 2.61 | 0.59 | 60.0 | -290 | -728 | 3654 | -490 | 3.48 | 2175 | 471 | 3654 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 543 | 13 |
| R5_IM1_KB | ASIA | 573 | 7.64 | 971 | 1103 | 2.47 | 0.54 | 253 | -411 | -782 | 895 | 707 | 804 | 789 | 291 | 895 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 557 | 11 |
| R5_TD_SM | ASIA | 242 | 3.23 | 1760 | 2151 | 2.29 | 0.58 | 112 | 436 | 690 | -547 | 344 | 189 | 1444 | 1522 | -547 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 741 | 16 |
| R5_DW_HM | NY-AM | 217 | 2.89 | 1500 | 1837 | 2.29 | 0.57 | 79.0 | 1236 | 925 | 3654 | -835 | -845 | 783 | 1740 | 3654 | SESSION-CANDIDATE |  | BOF:not cleared | 774 | 2 |
| R5_HTF3_ST | NY-AM | 466 | 6.21 | 1003 | 1314 | 2.14 | 0.53 | 208 | 331 | -24.9 | 2528 | -1062 | -398 | 743 | 226 | 2528 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 323 | 10 |
| R5_TD_EM | NY-AM | 171 | 2.28 | 1791 | 2416 | 2.08 | 0.58 | 74.0 | 168 | -12.5 | 1100 | 731 | 796 | 1608 | 972 | 1100 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 660 | 17 |
| R5_ZNOK_ST | PREOPEN | 125 | 1.67 | 1816 | 2479 | 2.05 | 0.58 | 47.0 | -2571 | -2732 | -1655 | -139 | 383 | 778 | 256 | -1655 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 519 | 0 |
| R5_IM5_ST | ASIA | 436 | 5.81 | 1061 | 1513 | 1.96 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 532 | 12 |
| R5_HTF3_EM | NY | 144 | 1.92 | 1547 | 2237 | 1.94 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 368 | 6 |
| R5_QUIET_HM | ASIA | 391 | 5.21 | 869 | 1343 | 1.81 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 426 | 18 |
| R5_DW_KB | NY | 495 | 6.60 | 779 | 1258 | 1.73 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 407 | 3 |
| R5_HTF3_KB | NY | 634 | 8.45 | 692 | 1223 | 1.58 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 464 | 8 |
| R5_HTF3_HM | NY-AM | 298 | 3.97 | 888 | 1582 | 1.57 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 487 | 7 |
| R5_DW_ST | ASIA | 374 | 4.99 | 802 | 1460 | 1.54 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 371 | 5 |
| R5_IM5_HM | LONDON | 370 | 4.93 | 557 | 1814 | 0.86 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 231 | 14 |
| R5_IM5_KB | LONDON | 404 | 5.39 | 563 | 1872 | 0.84 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 283 | 15 |
| R5_DW_SM | NY | 135 | 1.80 | 718 | 2548 | 0.79 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -48.3 | 4 |
| R5_DW_EM | NY | 144 | 1.92 | 647 | 2777 | 0.65 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 156 | 1 |
| R7_POOL_full_55 | NY | 110 | 1.47 | -251 | 2577 | -0.27 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -568 | 35 |
| R5_HTF3_SM | NY | 113 | 1.51 | -430 | 2622 | -0.46 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -311 | 9 |


## 5. Dead pooled, alive in a session
2 cell-sessions (2 cells, 2 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R5_QUIET_KB | NY-PM | 188 | 2.51 | 2227 | 2369 | 2.63 | 95.0 | 338 | 168 | 1119 | 318 | -635 | 2369 | 1185 | 1119 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 864 | 19 |
| R5_DW_HM | NY-AM | 217 | 2.89 | 1500 | 1837 | 2.29 | 79.0 | 1236 | 925 | 3654 | -835 | -845 | 783 | 1740 | 3654 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 774 | 2 |

