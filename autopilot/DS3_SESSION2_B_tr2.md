# DS3_SESSION2_B_tr2 - T-TREND R2/R3 (TR2) entry-clock re-run and session scoring

Written 2026-10-28T20:59:33Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tr2/. Prereg l2vast/ds3/prereg/SB3_tr2_prereg.md sha256 7fea24d0802bc4953a957f81f57fbe6e4be8de965e73bb2e103a0d63bf31830b; PREHOLD autopilot/DS3_SESSION2_B_tr2_PREHOLD.md sha256 3848ec167b0831e031275007171a3cc6459d60c774b9bbcf795725015a80602b (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original code (tr2_cells.cells + tr2_run.cell_cands + tr2_lib.gen3 + te_core.run_rows exact per-book lock engine at 10 lots, mapped corrected-P9 points). Table = executed (lock-engine f>0) trades: entry time = Ctx row et_in (ET; te_core bar END stamp convention, i.e. entry-bar open + 1 minute, same as the ledger), side, pnl = engine net $ (10 lots; PART cells 5+5 lots), basis MAPPED. The source direct L2 replay was incomplete (3/45 months) so no direct rows are used. Stop-entry (S) cells fill at the level +1 tick by trade-through in the source engine (the source's own basis).

Reproduction: the regenerated daily $ series of all 74 cells equals the stored out/tr2/daily_<R2|R3|W>.parquet series (rtol 1e-6): 74/74 (100%, all cells). out/sb3/tr2/repro.csv.

## 2. Multiplicity and counts
- Cells 74; F = cells x 7 sessions = **518**; overlap clusters (Jaccard >= 0.5, PRE entries) **62**, F_eff = **434**. Independent (cluster x session) PRE tests with n >= 100: 268; PRE-selected cell-sessions 44 = 37 independent (chance at 2.5% one-sided = about 7).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 18, DEAD-IN-HOLD 26; alive cells 14, alive clusters 11. HOLD sign persistence of the selected list: 70%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 66 | 13 | 11 | 8 | 0 | 6 | TR3_KB_S | 1163 | 1091 |
| LONDON | 02:00-08:30 | 63 | 3 | 3 | 2 | 0 | 2 | TR2_KB_NR4 | 946 | 1293 |
| PREOPEN | 08:30-09:30 | 15 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 61 | 13 | 11 | 2 | 0 | 2 | TRW_DON30m_n30_S | 1222 | 1565 |
| NY-PM | 12:00-15:00 | 56 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 65 | 15 | 12 | 6 | 0 | 5 | TRW_DON10m_n30_S | 1284 | 1212 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR2_KB_SWPH | ASIA | 607 | 8.09 | 1519 | 1134 | 3.75 | 0.57 | 299 | 256 | -27.3 | 1338 | -1120 | -1288 | 1076 | 1059 | 1338 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 713 | 23 |
| TRW_DON10m_n30_S | NY-AM | 380 | 5.07 | 1920 | 1507 | 3.57 | 0.58 | 212 | 198 | -70.5 | 1026 | 105 | 235 | 1866 | 668 | 1026 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 823 | 49 |
| TR2_KB_plain | NY | 809 | 10.8 | 1188 | 981 | 3.39 | 0.54 | 355 | -62.6 | 87.7 | -674 | 35.6 | -200 | 1207 | 677 | -674 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 762 | 21 |
| TR3_KB_S | NY-AM | 511 | 6.81 | 1404 | 1234 | 3.19 | 0.56 | 232 | 495 | 1174 | -3078 | -229 | -275 | 987 | 1596 | -3078 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 700 | 42 |
| TR2_KB_ROC2 | NY | 782 | 10.4 | 1118 | 1022 | 3.06 | 0.54 | 327 | -230 | -122 | -702 | -189 | -378 | 1208 | 424 | -702 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 811 | 21 |
| TR3_KB_S | NY | 730 | 9.73 | 1099 | 1020 | 3.02 | 0.54 | 316 | 457 | 1006 | -3031 | 159 | -13.8 | 1108 | 1067 | -3031 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 700 | 42 |
| TR3_KB_S | ASIA | 707 | 9.43 | 1163 | 1091 | 2.99 | 0.55 | 324 | 1040 | 485 | 2762 | -563 | -761 | 1530 | 630 | 2762 | SESSION-CANDIDATE |  | BOF:not cleared | 700 | 42 |
| TRW_DON10m_n30_S | NY | 564 | 7.52 | 1284 | 1212 | 2.97 | 0.55 | 273 | 489 | 364 | 923 | 548 | 442 | 1516 | 589 | 923 | SESSION-CANDIDATE |  | BOF:not cleared | 823 | 49 |
| TRW_kelt3m_n30_m2.0_RT15 | ASIA | 600 | 8.00 | 1173 | 1142 | 2.88 | 0.56 | 278 | -519 | -1150 | 1875 | -476 | -984 | 806 | 518 | 1875 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 718 | 61 |
| TR2_KB_plain | NY-AM | 528 | 7.04 | 1250 | 1242 | 2.82 | 0.55 | 245 | -84.9 | 237 | -1249 | -199 | -299 | 1131 | 820 | -1249 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 762 | 21 |
| TR3_KB20_M | NY | 776 | 10.3 | 1041 | 1036 | 2.81 | 0.53 | 321 | 42.4 | 16.1 | 232 | -525 | -772 | 1433 | 167 | 232 | SESSION-CANDIDATE |  | BOF:not cleared | 776 | 32 |
| TRW_DON10m_n20_S | NY-AM | 378 | 5.04 | 1693 | 1749 | 2.71 | 0.56 | 199 | -547 | -667 | -38.2 | -525 | -552 | 1771 | 197 | -38.2 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 736 | 48 |
| TR2_KB_ROC2 | NY-AM | 510 | 6.80 | 1239 | 1309 | 2.65 | 0.55 | 227 | -607 | -282 | -1920 | -468 | -560 | 1122 | 525 | -1920 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 811 | 21 |
| TR3_KB20_M | NY-AM | 512 | 6.83 | 1252 | 1328 | 2.64 | 0.54 | 219 | 43.9 | 268 | -1622 | -305 | -399 | 1247 | 717 | -1622 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 776 | 32 |
| TR3_DON15_S | NY-AM | 367 | 4.89 | 1537 | 1670 | 2.58 | 0.56 | 173 | -83.5 | -120 | 92.4 | -226 | 83.2 | 1495 | 386 | 92.4 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 903 | 31 |
| TRW_DON15m_n20_S | NY-AM | 367 | 4.89 | 1537 | 1670 | 2.58 | 0.56 | 173 | -83.5 | -120 | 92.4 | -226 | 83.2 | 1495 | 386 | 92.4 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 903 | 31 |
| TR3_KB20_S | ASIA | 681 | 9.08 | 1114 | 1241 | 2.51 | 0.55 | 293 | 459 | -143 | 2305 | -347 | -556 | 2022 | -31.4 | 2305 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 913 | 34 |
| TR3_KB_PART | NY | 1557 | 20.8 | 397 | 442 | 2.51 | 0.52 | 701 | -42.8 | 149 | -927 | 31.9 | -75.0 | 434 | 273 | -927 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 318 | 21 |
| TR3_DON15_S | ASIA | 423 | 5.64 | 1247 | 1491 | 2.34 | 0.56 | 204 | 1861 | 1124 | 5189 | 424 | -75.6 | 1186 | 1460 | 5189 | SESSION-CANDIDATE |  | BOF:not cleared | 903 | 31 |
| TRW_DON15m_n20_S | ASIA | 423 | 5.64 | 1247 | 1491 | 2.34 | 0.56 | 204 | 1861 | 1124 | 5189 | 424 | -75.6 | 1186 | 1460 | 5189 | SESSION-CANDIDATE |  | BOF:not cleared | 903 | 31 |
| TR2_KB_NR4 | NY | 526 | 7.01 | 1175 | 1428 | 2.30 | 0.54 | 227 | 603 | -16.0 | 3409 | -109 | -98.8 | 1307 | 353 | 3409 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 823 | 17 |
| TRW_DON30m_n30_S | NY | 529 | 7.05 | 957 | 1169 | 2.29 | 0.55 | 264 | 1150 | 827 | 2565 | -102 | -15.6 | 1051 | 710 | 2565 | SESSION-CANDIDATE |  | BOF:not cleared | 741 | 54 |
| TRW_DON15m_n30_S | NY-AM | 370 | 4.93 | 1211 | 1494 | 2.27 | 0.55 | 181 | 216 | -213 | 2070 | -238 | 36.3 | 1522 | -101 | 2070 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 763 | 51 |
| TR2_KB_LV2 | NY | 151 | 2.01 | 2187 | 2709 | 2.26 | 0.60 | 65.0 | -821 | -145 | -5637 | -1548 | -1998 | 1719 | 1433 | -5637 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1035 | 16 |
| TRW_DON30m_n20_S | NY | 518 | 6.91 | 981 | 1215 | 2.26 | 0.54 | 261 | 122 | -74.1 | 909 | 94.3 | 135 | 1087 | 297 | 909 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 920 | 53 |
| TRW_DON15m_n14_S | ASIA | 502 | 6.69 | 1191 | 1501 | 2.22 | 0.56 | 235 | 1084 | 555 | 3589 | -820 | -1201 | 886 | 1194 | 3589 | SESSION-CANDIDATE |  | BOF:not cleared | 839 | 50 |
| TRW_DON30m_n14_S | NY | 481 | 6.41 | 1007 | 1270 | 2.22 | 0.54 | 232 | 154 | -84.9 | 1268 | -49.7 | 31.8 | 1488 | -95.6 | 1268 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 718 | 52 |
| TRW_DON30m_n30_S | NY-AM | 343 | 4.57 | 1222 | 1565 | 2.19 | 0.56 | 183 | 1123 | 504 | 3652 | 377 | 660 | 1167 | 702 | 3652 | SESSION-CANDIDATE |  | BOF:not cleared | 741 | 54 |
| TRW_DON10m_n14_S | NY-AM | 379 | 5.05 | 1210 | 1569 | 2.16 | 0.55 | 201 | -1090 | -1288 | -154 | -297 | -292 | 1495 | -489 | -154 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 545 | 47 |
| TRW_DON10m_n14_S | ASIA | 589 | 7.85 | 992 | 1288 | 2.16 | 0.55 | 285 | 299 | -447 | 3218 | -963 | -1294 | 879 | 431 | 3218 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 545 | 47 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR2_KB_SWPH | ASIA | 607 | 8.09 | 1519 | 1134 | 3.75 | 0.57 | 299 | 256 | -27.3 | 1338 | -1120 | -1288 | 1076 | 1059 | 1338 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 713 | 23 |
| TRW_DON10m_n30_S | NY-AM | 380 | 5.07 | 1920 | 1507 | 3.57 | 0.58 | 212 | 198 | -70.5 | 1026 | 105 | 235 | 1866 | 668 | 1026 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 823 | 49 |
| TR2_KB_plain | NY | 809 | 10.8 | 1188 | 981 | 3.39 | 0.54 | 355 | -62.6 | 87.7 | -674 | 35.6 | -200 | 1207 | 677 | -674 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 762 | 21 |
| TR3_KB_S | NY-AM | 511 | 6.81 | 1404 | 1234 | 3.19 | 0.56 | 232 | 495 | 1174 | -3078 | -229 | -275 | 987 | 1596 | -3078 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 700 | 42 |
| TRW_kelt3m_n30_m2.0_RT15 | ASIA | 600 | 8.00 | 1173 | 1142 | 2.88 | 0.56 | 278 | -519 | -1150 | 1875 | -476 | -984 | 806 | 518 | 1875 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 718 | 61 |
| TR3_KB20_M | NY | 776 | 10.3 | 1041 | 1036 | 2.81 | 0.53 | 321 | 42.4 | 16.1 | 232 | -525 | -772 | 1433 | 167 | 232 | SESSION-CANDIDATE |  | BOF:not cleared | 776 | 32 |
| TRW_DON10m_n20_S | NY-AM | 378 | 5.04 | 1693 | 1749 | 2.71 | 0.56 | 199 | -547 | -667 | -38.2 | -525 | -552 | 1771 | 197 | -38.2 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 736 | 48 |
| TR3_DON15_S | NY-AM | 367 | 4.89 | 1537 | 1670 | 2.58 | 0.56 | 173 | -83.5 | -120 | 92.4 | -226 | 83.2 | 1495 | 386 | 92.4 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 903 | 31 |
| TR3_KB20_S | ASIA | 681 | 9.08 | 1114 | 1241 | 2.51 | 0.55 | 293 | 459 | -143 | 2305 | -347 | -556 | 2022 | -31.4 | 2305 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 913 | 34 |
| TR2_KB_NR4 | NY | 526 | 7.01 | 1175 | 1428 | 2.30 | 0.54 | 227 | 603 | -16.0 | 3409 | -109 | -98.8 | 1307 | 353 | 3409 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 823 | 17 |
| TRW_DON30m_n30_S | NY | 529 | 7.05 | 957 | 1169 | 2.29 | 0.55 | 264 | 1150 | 827 | 2565 | -102 | -15.6 | 1051 | 710 | 2565 | SESSION-CANDIDATE |  | BOF:not cleared | 741 | 54 |
| TRW_DON15m_n30_S | NY-AM | 370 | 4.93 | 1211 | 1494 | 2.27 | 0.55 | 181 | 216 | -213 | 2070 | -238 | 36.3 | 1522 | -101 | 2070 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 763 | 51 |
| TR2_KB_LV2 | NY | 151 | 2.01 | 2187 | 2709 | 2.26 | 0.60 | 65.0 | -821 | -145 | -5637 | -1548 | -1998 | 1719 | 1433 | -5637 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1035 | 16 |
| TRW_DON30m_n20_S | NY | 518 | 6.91 | 981 | 1215 | 2.26 | 0.54 | 261 | 122 | -74.1 | 909 | 94.3 | 135 | 1087 | 297 | 909 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 920 | 53 |
| TRW_DON15m_n14_S | ASIA | 502 | 6.69 | 1191 | 1501 | 2.22 | 0.56 | 235 | 1084 | 555 | 3589 | -820 | -1201 | 886 | 1194 | 3589 | SESSION-CANDIDATE |  | BOF:not cleared | 839 | 50 |
| TRW_DON30m_n14_S | NY | 481 | 6.41 | 1007 | 1270 | 2.22 | 0.54 | 232 | 154 | -84.9 | 1268 | -49.7 | 31.8 | 1488 | -95.6 | 1268 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 718 | 52 |
| TRW_DON10m_n14_S | NY-AM | 379 | 5.05 | 1210 | 1569 | 2.16 | 0.55 | 201 | -1090 | -1288 | -154 | -297 | -292 | 1495 | -489 | -154 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 545 | 47 |
| TR2_KB_THIN | LONDON | 243 | 3.24 | 1757 | 2282 | 2.16 | 0.58 | 103 | 1508 | 2029 | -305 | 2651 | 2500 | 1797 | 1925 | -305 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 393 | 24 |
| TR3_KB_C2 | NY | 705 | 9.40 | 800 | 1055 | 2.12 | 0.52 | 331 | -168 | -392 | 1373 | -905 | -1192 | 884 | 134 | 1373 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 587 | 35 |
| TR2_KB_LV1 | NY-AM | 445 | 5.93 | 1025 | 1367 | 2.10 | 0.53 | 196 | 934 | 930 | 950 | -598 | -785 | 1257 | 783 | 950 | SESSION-CANDIDATE |  | BOF:not cleared | 375 | 15 |
| TR2_KB_NR7 | NY-AM | 207 | 2.76 | 1608 | 2239 | 2.01 | 0.57 | 80.0 | 353 | -1187 | 9082 | -1117 | -1144 | 1127 | 546 | 9082 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 425 | 18 |
| TRW_kelt3m_n14_m2.0_RT15 | ASIA | 496 | 6.61 | 1065 | 1496 | 1.99 | 0.55 | 241 | 983 | 808 | 1589 | -202 | -568 | 1280 | 862 | 1589 | SESSION-CANDIDATE |  | BOF:not cleared | 304 | 56 |
| TR3_KB_FH | NY | 556 | 7.41 | 991 | 1440 | 1.93 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 979 | 36 |
| TR3_DON15_RTH15 | ASIA | 210 | 2.80 | 1498 | 2243 | 1.87 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 622 | 30 |
| TRW_kelt3m_n30_m1.0_RT15 | ASIA | 595 | 7.93 | 875 | 1340 | 1.83 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 400 | 59 |
| TRW_kelt3m_n20_m1.0_RT15 | NY-AM | 438 | 5.84 | 932 | 1434 | 1.82 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 423 | 33 |
| TR2_KB_RNG3 | NY-AM | 155 | 2.07 | 1358 | 2135 | 1.78 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 127 | 20 |
| TRW_kelt3m_n20_m1.5_RT15 | ASIA | 603 | 8.04 | 779 | 1235 | 1.77 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 459 | 57 |
| TR2_KB_RNG2 | NY-AM | 319 | 4.25 | 1138 | 1806 | 1.76 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 337 | 19 |
| TR3_KB_RTH5 | LONDON | 371 | 4.95 | 1100 | 1754 | 1.76 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 572 | 41 |


## 5. Dead pooled, alive in a session
1 cell-sessions (1 cells, 1 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR2_KB_LV1 | NY-AM | 445 | 5.93 | 1025 | 1367 | 2.10 | 196 | 934 | 930 | 950 | -598 | -785 | 1257 | 783 | 950 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 375 | 15 |

