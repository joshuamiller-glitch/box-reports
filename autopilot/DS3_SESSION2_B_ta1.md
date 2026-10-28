# DS3_SESSION2_B_ta1 - T-A1 regime-gated entries: entry-clock re-run and session scoring

Written 2026-10-28T21:04:03Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/ta1/. Prereg l2vast/ds3/prereg/SB3_ta1_prereg.md sha256 fac1d9da8d25e053cde87221320148c96efae2dce638edeeeb683f0a70abe166; PREHOLD autopilot/DS3_SESSION2_B_ta1_PREHOLD.md sha256 62be2b15bf6076136560f9a9f86ec793d5a1eb9bcff0021c76b4cda5c60afaf2 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original code: T-ENTRY sources via ta_lib (CE.build events, regime gate on signals before the busy filter, TC.gen_entries, exact per-book lock engine, mapped corrected-P9, 10-lot-equivalent R); T-B sources via ta_tb (tb_run path monthly-stitched trades, post-hoc regime filter, closed-trade locks). Executed trades only; entry time = Ctx et_in (T-ENTRY, bar END stamp as in the ledger) or entry-bar start (T-B), pnl = engine net $, basis MAPPED. The source's direct L2 re-pricing of 11 cells is not used. Each cell is a regime-gated copy of an entry that is itself a candidate entry; the regime gate is known as-of the session open, so it is a session-conditioned filter (a regime is not an entry session; both sessions of the entry day mix).

Reproduction: regenerated daily $ series equals the stored out/TA/ta1_final_series.pkl series for 120 of 120 cells (rtol 1e-6; 100%). out/sb3/ta1/repro.csv.

## 2. Multiplicity and counts
- Cells 120; F = cells x 7 sessions = **840**; overlap clusters (Jaccard >= 0.5, PRE entries) **119**, F_eff = **833**. Independent (cluster x session) PRE tests with n >= 100: 373; PRE-selected cell-sessions 36 = 36 independent (chance at 2.5% one-sided = about 9).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 5, DEAD-IN-HOLD 31; alive cells 4, alive clusters 4. HOLD sign persistence of the selected list: 53%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 72 | 2 | 2 | 1 | 0 | 1 | TE1B_volclimax_5m|wide | 2751 | 2902 |
| LONDON | 02:00-08:30 | 75 | 1 | 1 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 8 | 1 | 1 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 84 | 14 | 14 | 1 | 0 | 1 | TE3_ofi_w5_q0.97|wide | 864 | 943 |
| NY-PM | 12:00-15:00 | 36 | 5 | 5 | 2 | 0 | 2 | TE7_kelt3m_n14_m1.0|wide | 2218 | 2358 |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 101 | 13 | 13 | 1 | 0 | 1 | TE4_vwb_k1.5_ny|wide | 812 | 1039 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE3_ofi_w3_q0.99|wide | NY | 797 | 10.6 | 1541 | 875 | 4.93 | 0.56 | 513 | 133 | 382 | -607 | 793 | 563 | 1846 | 630 | -607 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF_F:clear | 1527 | 87 |
| TE3_ofi_w3_q0.99|wide | NY-AM | 612 | 8.16 | 1548 | 966 | 4.49 | 0.56 | 433 | 197 | 522 | -791 | 891 | 652 | 1630 | 899 | -791 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF_F:clear | 1527 | 87 |
| TE3_ofi_w5_q0.97|wide | NY | 1009 | 13.5 | 1026 | 783 | 3.67 | 0.54 | 606 | 194 | -6.41 | 845 | 61.6 | -280 | 1203 | 355 | 845 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 944 | 89 |
| TE7_kelt3m_n14_m1.0|wide | NY | 569 | 7.59 | 1470 | 1169 | 3.52 | 0.56 | 322 | -475 | -223 | -1385 | -36.6 | -572 | 1513 | 611 | -1385 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 887 | 116 |
| TE7_boll3m_n30_m1.5|wide | NY | 524 | 6.99 | 1355 | 1141 | 3.32 | 0.55 | 282 | -883 | -1026 | -90.5 | -743 | -1123 | 1359 | 27.1 | -90.5 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 676 | 108 |
| TE7_kelt3m_n20_m1.0|wide | NY | 558 | 7.44 | 1373 | 1171 | 3.28 | 0.55 | 291 | 124 | -124 | 1480 | -1029 | -1516 | 1655 | 244 | 1480 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 1034 | 118 |
| TE1_kelt_3m|quiet | NY-AM | 203 | 2.71 | 2041 | 1954 | 2.92 | 0.59 | 35.0 | -1315 | -1315 |  | -21.7 | 52.0 | 3247 | -63.3 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 421 | 54 |
| TE1B_volclimax_5m|quiet | NY-AM | 162 | 2.16 | 2218 | 2247 | 2.76 | 0.60 | 21.0 | -2501 | -2501 |  | -832 | -917 | 2017 | 1405 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1360 | 46 |
| TE1B_volclimax_5m|wide | ASIA | 100 | 1.33 | 2751 | 2902 | 2.65 | 0.62 | 56.0 | 1129 | 617 | 4716 | -387 | -890 | 2300 | 1992 | 4716 | SESSION-CANDIDATE |  | BOF:not cleared | 522 | 47 |
| TE7_kelt3m_n14_m1.0|wide | NY-PM | 189 | 2.52 | 2218 | 2358 | 2.63 | 0.59 | 94.0 | 223 | 25.4 | 1119 | 179 | -804 | 2357 | 1118 | 1119 | SESSION-CANDIDATE |  | BOF:not cleared | 887 | 116 |
| TE1B_rsi_1m|wide | ASIA | 455 | 6.07 | 1139 | 1221 | 2.61 | 0.55 | 207 | 366 | 731 | -642 | -508 | -582 | 917 | 1056 | -642 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 232 | 45 |
| TE3_ofi_w5_q0.97|wide | NY-AM | 749 | 9.99 | 864 | 943 | 2.57 | 0.54 | 467 | 412 | 147 | 1245 | -104 | -340 | 1099 | 266 | 1245 | SESSION-CANDIDATE |  | BOF:not cleared | 944 | 89 |
| TE3_ofi_w1_q0.99|wide | NY | 882 | 11.8 | 895 | 986 | 2.54 | 0.53 | 555 | 363 | 537 | -167 | 553 | 400 | 1340 | 341 | -167 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 901 | 85 |
| TE1B_volclimax_5m|quiet | NY | 166 | 2.21 | 2021 | 2228 | 2.54 | 0.59 | 22.0 | -2898 | -2898 |  | -714 | -790 | 1701 | 1250 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1360 | 46 |
| TB8_CLIM_k15_T_N|quiet | NY-AM | 211 | 2.81 | 2471 | 2840 | 2.44 | 0.50 | 45.0 | -1023 | -1023 |  | -69.6 | -69.6 | 1395 | 2298 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1002 | 36 |
| TE2_sweep_lb30|wide | LONDON | 413 | 5.51 | 1317 | 1533 | 2.41 | 0.55 | 195 | -1384 | -1964 | 56.9 | -875 | -1170 | 1383 | -148 | 56.9 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 224 | 73 |
| TE7_kelt3m_n20_m1.0|wide | NY-AM | 374 | 4.99 | 1219 | 1455 | 2.35 | 0.55 | 203 | 172 | 308 | -582 | -1162 | -1322 | 1336 | 481 | -582 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1034 | 118 |
| TE3_ofi_w5_q0.97|wide | NY-PM | 260 | 3.47 | 1492 | 1792 | 2.33 | 0.55 | 139 | -538 | -503 | -663 | 604 | -74.0 | 1517 | 616 | -663 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 944 | 89 |
| TE3_ofi_w1_q0.99|wide | NY-AM | 699 | 9.32 | 929 | 1118 | 2.33 | 0.54 | 455 | 410 | 564 | -16.4 | -21.0 | -126 | 1360 | 328 | -16.4 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 901 | 85 |
| TE7_boll3m_n30_m1.5|wide | NY-AM | 330 | 4.40 | 1336 | 1620 | 2.31 | 0.55 | 194 | -886 | -1034 | -137 | -1055 | -1132 | 1222 | -141 | -137 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 676 | 108 |
| TB8_CLIM_k15_T_N|quiet | NY | 233 | 3.11 | 2084 | 2594 | 2.25 | 0.49 | 48.0 | -1238 | -1238 |  | -293 | -293 | 1152 | 1844 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1002 | 36 |
| TE7_kelt3m_n14_m1.0|quiet | NY-AM | 233 | 3.11 | 1540 | 1923 | 2.24 | 0.55 | 44.0 | 1013 | 1013 |  | -558 | -558 | 2188 | 863 |  | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 233 | 115 |
| TE7_boll3m_n30_m1.5|wide | NY-PM | 194 | 2.59 | 1387 | 1745 | 2.22 | 0.55 | 88.0 | -876 | -1008 | 45.5 | -166 | -1105 | 1616 | 318 | 45.5 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 676 | 108 |
| TB1_ST_k15_A3_N|wide | NY | 194 | 2.59 | 4024 | 5072 | 2.22 | 0.45 | 93.0 | -904 | -1457 | 2499 | -839 | -1353 | 4256 | -142 | 2499 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 1395 | 1 |
| TE7_kelt3m_n20_m1.0|wide | NY-PM | 184 | 2.45 | 1686 | 2155 | 2.19 | 0.55 | 88.0 | 11.8 | -1130 | 6045 | -729 | -2009 | 2246 | -300 | 6045 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 1034 | 118 |
| TE4_vwb_k1.5_ny|wide | NY | 672 | 8.96 | 812 | 1039 | 2.19 | 0.53 | 402 | 496 | 160 | 1958 | -303 | -599 | 999 | 378 | 1958 | SESSION-CANDIDATE |  | BOF:not cleared | 812 | 99 |
| TE7_kelt3m_n14_m1.0|wide | NY-AM | 380 | 5.07 | 1097 | 1410 | 2.18 | 0.54 | 228 | -763 | -332 | -2189 | -136 | -476 | 1088 | 366 | -2189 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 887 | 116 |
| TE7_emax5m_f15_s40|wide | NY | 270 | 3.60 | 1421 | 1842 | 2.16 | 0.56 | 133 | -151 | -571 | 2223 | 135 | 22.6 | 1627 | 122 | 2223 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 753 | 110 |
| TE7_boll3m_n20_m2.0|quiet | NY-AM | 180 | 2.40 | 1816 | 2356 | 2.16 | 0.58 | 27.0 | -1838 | -1838 |  | -136 | -136 | 2333 | 392 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 99.7 | 105 |
| TE7_emax5m_f20_s50|quiet | NY | 117 | 1.56 | 1588 | 2107 | 2.11 | 0.58 | 14.0 | -287 | -287 |  | 1384 | 1384 | 1704 | 1013 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1295 | 113 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE3_ofi_w3_q0.99|wide | NY | 797 | 10.6 | 1541 | 875 | 4.93 | 0.56 | 513 | 133 | 382 | -607 | 793 | 563 | 1846 | 630 | -607 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF_F:clear | 1527 | 87 |
| TE3_ofi_w5_q0.97|wide | NY | 1009 | 13.5 | 1026 | 783 | 3.67 | 0.54 | 606 | 194 | -6.41 | 845 | 61.6 | -280 | 1203 | 355 | 845 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 944 | 89 |
| TE7_kelt3m_n14_m1.0|wide | NY | 569 | 7.59 | 1470 | 1169 | 3.52 | 0.56 | 322 | -475 | -223 | -1385 | -36.6 | -572 | 1513 | 611 | -1385 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 887 | 116 |
| TE7_boll3m_n30_m1.5|wide | NY | 524 | 6.99 | 1355 | 1141 | 3.32 | 0.55 | 282 | -883 | -1026 | -90.5 | -743 | -1123 | 1359 | 27.1 | -90.5 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 676 | 108 |
| TE7_kelt3m_n20_m1.0|wide | NY | 558 | 7.44 | 1373 | 1171 | 3.28 | 0.55 | 291 | 124 | -124 | 1480 | -1029 | -1516 | 1655 | 244 | 1480 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 1034 | 118 |
| TE1_kelt_3m|quiet | NY-AM | 203 | 2.71 | 2041 | 1954 | 2.92 | 0.59 | 35.0 | -1315 | -1315 |  | -21.7 | 52.0 | 3247 | -63.3 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 421 | 54 |
| TE1B_volclimax_5m|quiet | NY-AM | 162 | 2.16 | 2218 | 2247 | 2.76 | 0.60 | 21.0 | -2501 | -2501 |  | -832 | -917 | 2017 | 1405 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1360 | 46 |
| TE1B_volclimax_5m|wide | ASIA | 100 | 1.33 | 2751 | 2902 | 2.65 | 0.62 | 56.0 | 1129 | 617 | 4716 | -387 | -890 | 2300 | 1992 | 4716 | SESSION-CANDIDATE |  | BOF:not cleared | 522 | 47 |
| TE1B_rsi_1m|wide | ASIA | 455 | 6.07 | 1139 | 1221 | 2.61 | 0.55 | 207 | 366 | 731 | -642 | -508 | -582 | 917 | 1056 | -642 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 232 | 45 |
| TE3_ofi_w1_q0.99|wide | NY | 882 | 11.8 | 895 | 986 | 2.54 | 0.53 | 555 | 363 | 537 | -167 | 553 | 400 | 1340 | 341 | -167 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 901 | 85 |
| TB8_CLIM_k15_T_N|quiet | NY-AM | 211 | 2.81 | 2471 | 2840 | 2.44 | 0.50 | 45.0 | -1023 | -1023 |  | -69.6 | -69.6 | 1395 | 2298 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1002 | 36 |
| TE2_sweep_lb30|wide | LONDON | 413 | 5.51 | 1317 | 1533 | 2.41 | 0.55 | 195 | -1384 | -1964 | 56.9 | -875 | -1170 | 1383 | -148 | 56.9 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 224 | 73 |
| TE7_kelt3m_n14_m1.0|quiet | NY-AM | 233 | 3.11 | 1540 | 1923 | 2.24 | 0.55 | 44.0 | 1013 | 1013 |  | -558 | -558 | 2188 | 863 |  | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 233 | 115 |
| TB1_ST_k15_A3_N|wide | NY | 194 | 2.59 | 4024 | 5072 | 2.22 | 0.45 | 93.0 | -904 | -1457 | 2499 | -839 | -1353 | 4256 | -142 | 2499 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 1395 | 1 |
| TE4_vwb_k1.5_ny|wide | NY | 672 | 8.96 | 812 | 1039 | 2.19 | 0.53 | 402 | 496 | 160 | 1958 | -303 | -599 | 999 | 378 | 1958 | SESSION-CANDIDATE |  | BOF:not cleared | 812 | 99 |
| TE7_emax5m_f15_s40|wide | NY | 270 | 3.60 | 1421 | 1842 | 2.16 | 0.56 | 133 | -151 | -571 | 2223 | 135 | 22.6 | 1627 | 122 | 2223 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 753 | 110 |
| TE7_boll3m_n20_m2.0|quiet | NY-AM | 180 | 2.40 | 1816 | 2356 | 2.16 | 0.58 | 27.0 | -1838 | -1838 |  | -136 | -136 | 2333 | 392 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 99.7 | 105 |
| TE7_emax5m_f20_s50|quiet | NY | 117 | 1.56 | 1588 | 2107 | 2.11 | 0.58 | 14.0 | -287 | -287 |  | 1384 | 1384 | 1704 | 1013 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1295 | 113 |
| TE1_macd_3m|wide | PREOPEN | 102 | 1.36 | 2300 | 3089 | 2.08 | 0.60 | 35.0 | 412 | -575 | 2879 | 821 | 734 | 3123 | -161 | 2879 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 340 | 57 |
| TE4_orb_ny_15|quiet | NY | 130 | 1.73 | 1723 | 2322 | 2.08 | 0.58 | 21.0 | 954 | 954 |  | -2671 | -2654 | 1587 | 1571 |  | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1723 | 94 |
| TE3_vpin_n20_q0.95|quiet | NY-AM | 261 | 3.48 | 1166 | 1590 | 2.05 | 0.54 | 36.0 | 2189 | 2189 |  | -949 | -949 | 1467 | 1094 |  | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 985 | 90 |
| TB7_ORBNY_k3_P60_N|quiet | NY-AM | 152 | 2.03 | 3245 | 4538 | 2.00 | 0.41 | 19.0 | -874 | -874 |  | 3.57 | 107 | 2348 | 3139 |  | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 2330 | 32 |
| TE1_kelt_3m|wide | NY | 519 | 6.92 | 820 | 1165 | 1.97 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 747 | 55 |
| TE1B_vwapslope_5m|wide | ASIA | 285 | 3.80 | 1108 | 1589 | 1.95 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 127 | 49 |
| TB7_ORBNY_k1_P60_N|quiet | NY-AM | 156 | 2.08 | 3144 | 4554 | 1.93 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 2089 | 30 |
| TE1_st_10m|wide | ASIA | 117 | 1.56 | 2024 | 3027 | 1.87 | 0.60 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 735 | 61 |
| TB5_MACD_k15_P60_N|wide | NY | 165 | 2.20 | 3515 | 5346 | 1.84 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 854 | 21 |
| TE7_emax5m_f15_s40|quiet | ASIA | 124 | 1.65 | 1946 | 2971 | 1.83 | 0.59 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1391 | 109 |
| TE2_big_w5_q0.98|wide | NY-AM | 348 | 4.64 | 1159 | 1783 | 1.82 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 880 | 65 |
| TE7_emax5m_f20_s50|wide | ASIA | 178 | 2.37 | 1376 | 2203 | 1.75 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 517 | 114 |


## 5. Dead pooled, alive in a session
4 cell-sessions (3 cells, 4 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE1B_volclimax_5m|wide | ASIA | 100 | 1.33 | 2751 | 2902 | 2.65 | 56.0 | 1129 | 617 | 4716 | -387 | -890 | 2300 | 1992 | 4716 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 522 | 47 |
| TE3_ofi_w5_q0.97|wide | NY-AM | 749 | 9.99 | 864 | 943 | 2.57 | 467 | 412 | 147 | 1245 | -104 | -340 | 1099 | 266 | 1245 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 944 | 89 |
| TE4_vwb_k1.5_ny|wide | NY | 672 | 8.96 | 812 | 1039 | 2.19 | 402 | 496 | 160 | 1958 | -303 | -599 | 999 | 378 | 1958 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 812 | 99 |
| TE4_vwb_k1.5_ny|wide | NY-PM | 198 | 2.64 | 1554 | 2181 | 1.99 | 99.0 | 1440 | 1402 | 1685 | -530 | -1064 | 1604 | 1536 | 1685 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 812 | 99 |

