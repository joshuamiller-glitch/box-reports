# DS3_SESSION2_B_tfootprint - T-FOOTPRINT confirmation cells: entry-clock re-run and session scoring

Written 2026-10-28T21:07:22Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tfootprint/. Prereg l2vast/ds3/prereg/SB3_tfootprint_prereg.md sha256 c2e681994b4aa23d858c469d838ef83bfd4b89cd44db9f01ee82b1a58fff29bf; PREHOLD autopilot/DS3_SESSION2_B_tfootprint_PREHOLD.md sha256 47cccf65d3b78d01671d8fc849c8774fe15c0d1c2e4442864d9d2f2fc696ba34 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original code (fp_conf.load_base + confirm_flags, wo_core.run_book exact per-book lock engine at 10 lots): kept trades of the base entry, entry time = base Ctx et_in (ET, bar END stamp as in the ledger), pnl = conservative net pts x $200 (10 lots; positive mapped credit removed; ST rows with P9 on direct true-P9 points), pure subset as in the source's paired test (trades the base skipped while busy are not recovered). Columns exec/pnl_lock give the lock-engine fill flag and $. Basis CONSERVATIVE-MAPPED (ST: TRUEP9+CONSERVATIVE). 9 cells have zero events.

Reproduction: for the 130 cells with a stored weekly record the regenerated PRE weekly mean, PRE max drawdown (lock engine) and PRE kept-trade count equal the stored values (rtol 1e-6) in 130 of 130; the other 62 cells (source stored only trade-level lifts, no weekly) match on the stored WF kept-trade count 62 of 62. Total 192 of 192 (100%, all cells). out/sb3/tfootprint/repro.csv.

## 2. Multiplicity and counts
- Cells 168; F = cells x 7 sessions = **1344**; overlap clusters (Jaccard >= 0.5, PRE entries) **119**, F_eff = **833**. Independent (cluster x session) PRE tests with n >= 100: 91; PRE-selected cell-sessions 18 = 4 independent (chance at 2.5% one-sided = about 2).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 11, DEAD-IN-HOLD 7; alive cells 6, alive clusters 1. HOLD sign persistence of the selected list: 61%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 31 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 42 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 18 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 66 | 11 | 2 | 6 | 0 | 1 | CF_ST_SI44_t500_k5 | 1725 | 1584 |
| NY-PM | 12:00-15:00 | 55 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 71 | 7 | 2 | 5 | 0 | 1 | CF_ST_CD_t500_k15 | 786 | 856 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CF_ST_SI44_t500_k5 | NY-AM | 439 | 5.85 | 1725 | 1584 | 3.05 | 0.58 | 250 | 463 | 265 | 1136 | 225 | 571 | 2431 | 230 | 1136 | SESSION-CANDIDATE |  | BOF:not cleared | 899 | 106 |
| CF_ST_SI44_1m_k5 | NY-AM | 310 | 4.13 | 1846 | 1891 | 2.73 | 0.58 | 168 | 1725 | 610 | 5292 | 1914 | 2168 | 2833 | 459 | 5292 | SESSION-CANDIDATE |  | BOF:not cleared | 730 | 106 |
| CF_ST_CD_t500_k15 | NY | 1158 | 15.4 | 786 | 856 | 2.57 | 0.54 | 552 | 1325 | 878 | 3026 | 205 | 328 | 1171 | 486 | 3026 | SESSION-CANDIDATE |  | BOF:not cleared | 385 | 106 |
| CF_ST_SI44_1m_k15 | NY-AM | 540 | 7.20 | 1192 | 1335 | 2.50 | 0.56 | 308 | 1493 | 670 | 4190 | 1204 | 1210 | 2037 | 388 | 4190 | SESSION-CANDIDATE |  | BOF:not cleared | 369 | 106 |
| CF_ST_SI44_t500_k5 | NY | 634 | 8.45 | 1103 | 1310 | 2.36 | 0.55 | 325 | 266 | 178 | 540 | 323 | 493 | 1724 | 17.7 | 540 | SESSION-CANDIDATE |  | BOF:not cleared | 899 | 106 |
| CF_ST_SI44_t500_k15 | NY | 1047 | 14.0 | 802 | 970 | 2.31 | 0.54 | 524 | 844 | 419 | 2391 | 233 | 211 | 1279 | 230 | 2391 | SESSION-CANDIDATE |  | BOF:not cleared | 680 | 106 |
| CF_ST_SI44_t500_k15 | NY-AM | 705 | 9.40 | 1020 | 1253 | 2.28 | 0.55 | 386 | 1095 | 550 | 3052 | 356 | 481 | 1546 | 329 | 3052 | SESSION-CANDIDATE |  | BOF:not cleared | 680 | 106 |
| CF_ST_SI44_1m_k5 | NY | 472 | 6.29 | 1185 | 1458 | 2.28 | 0.55 | 234 | 1385 | 692 | 3586 | 1592 | 1584 | 2005 | 320 | 3586 | SESSION-CANDIDATE |  | BOF:not cleared | 730 | 106 |
| CF_ST_SI44_1m_k15 | NY | 811 | 10.8 | 887 | 1109 | 2.24 | 0.54 | 419 | 1006 | 359 | 3241 | 633 | 550 | 1677 | 101 | 3241 | SESSION-CANDIDATE |  | BOF:not cleared | 369 | 106 |
| CF_KB_SI44_t500_k15 | NY | 1158 | 15.4 | 693 | 870 | 2.23 | 0.54 | 499 | -117 | 226 | -1485 | -36.9 | -204 | 1148 | 164 | -1485 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 667 | 16 |
| CF_ST_CD_t500_k15 | NY-AM | 760 | 10.1 | 899 | 1150 | 2.19 | 0.54 | 387 | 1669 | 1175 | 3503 | 235 | 448 | 1325 | 637 | 3503 | SESSION-CANDIDATE |  | BOF:not cleared | 385 | 106 |
| CF_KB_SI33_t500_k15 | NY-AM | 878 | 11.7 | 767 | 987 | 2.17 | 0.54 | 424 | -667 | -305 | -2091 | 219 | 138 | 1048 | 45.9 | -2091 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 324 | 16 |
| CF_ST_CD_1m_k15 | NY-AM | 535 | 7.13 | 1148 | 1503 | 2.14 | 0.56 | 288 | 1858 | 1104 | 4845 | 32.2 | 90.2 | 1342 | 949 | 4845 | SESSION-CANDIDATE |  | BOF:not cleared | 294 | 106 |
| CF_KB_SI33_t500_k5 | NY-AM | 829 | 11.1 | 774 | 1016 | 2.13 | 0.54 | 392 | -641 | -327 | -1845 | 180 | 171 | 1071 | -9.70 | -1845 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 326 | 16 |
| CF_KB_SI44_t500_k15 | NY-AM | 727 | 9.69 | 853 | 1122 | 2.13 | 0.54 | 349 | -671 | -322 | -2012 | -129 | -214 | 1288 | -78.9 | -2012 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 667 | 16 |
| CF_KB_SI33_t500_k15 | NY | 1516 | 20.2 | 547 | 743 | 2.06 | 0.53 | 668 | -326 | -152 | -1049 | -39.8 | -223 | 1016 | -64.1 | -1049 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 324 | 16 |
| CF_KB_SI44_1m_k15 | NY-AM | 574 | 7.65 | 828 | 1150 | 2.01 | 0.54 | 297 | -909 | -603 | -2047 | -587 | -806 | 1335 | -205 | -2047 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 209 | 16 |
| CF_KB_SI44_t500_k5 | NY-AM | 533 | 7.11 | 929 | 1293 | 2.01 | 0.55 | 239 | -972 | -421 | -3001 | -826 | -947 | 1286 | -48.7 | -3001 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 626 | 16 |
| CF_KB_SI44_t500_k5 | NY | 805 | 10.7 | 739 | 1046 | 1.98 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 626 | 16 |
| CF_KB_SI33_5m_k15 | NY-AM | 566 | 7.55 | 895 | 1322 | 1.90 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 263 | 16 |
| CF_ST_SI33_t500_k15 | NY | 1448 | 19.3 | 510 | 776 | 1.84 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 106 | 106 |
| CF_KB_DD_1m_k15 | NY | 112 | 1.49 | 1972 | 3007 | 1.84 | 0.60 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1164 | 20 |
| CF_PB3B_R5_P1_SI33_5m_k15 | ASIA | 262 | 3.49 | 1236 | 1897 | 1.82 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 125 | 35 |
| CF_ST_SI33_5m_k15 | NY-AM | 494 | 6.59 | 1054 | 1637 | 1.80 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 108 | 115 |
| CF_KB_SI33_1m_k15 | NY-AM | 854 | 11.4 | 633 | 993 | 1.79 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 330 | 16 |
| CF_ST_SI33_t500_k5 | NY-AM | 839 | 11.2 | 736 | 1159 | 1.78 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 231 | 106 |
| CF_KB_SI33_t500_k5 | NY | 1371 | 18.3 | 505 | 799 | 1.77 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 326 | 16 |
| CF_ST_SI33_t500_k5 | NY | 1291 | 17.2 | 522 | 826 | 1.77 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 231 | 106 |
| CF_KB_SI33_1m_k15 | NY | 1487 | 19.8 | 456 | 726 | 1.76 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 330 | 16 |
| CF_SBS_SI33_1m_k15 | ASIA | 207 | 2.76 | 1213 | 1936 | 1.75 | 0.20 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 257 | 75 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CF_ST_SI44_t500_k5 | NY-AM | 439 | 5.85 | 1725 | 1584 | 3.05 | 0.58 | 250 | 463 | 265 | 1136 | 225 | 571 | 2431 | 230 | 1136 | SESSION-CANDIDATE |  | BOF:not cleared | 899 | 106 |
| CF_KB_SI44_t500_k15 | NY | 1158 | 15.4 | 693 | 870 | 2.23 | 0.54 | 499 | -117 | 226 | -1485 | -36.9 | -204 | 1148 | 164 | -1485 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 667 | 16 |
| CF_KB_DD_1m_k15 | NY | 112 | 1.49 | 1972 | 3007 | 1.84 | 0.60 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1164 | 20 |
| CF_PB3B_R5_P1_SI33_5m_k15 | ASIA | 262 | 3.49 | 1236 | 1897 | 1.82 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 125 | 35 |
| CF_ST_SI33_5m_k15 | NY-AM | 494 | 6.59 | 1054 | 1637 | 1.80 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 108 | 115 |
| CF_SBS_SI33_1m_k15 | ASIA | 207 | 2.76 | 1213 | 1936 | 1.75 | 0.20 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 257 | 75 |
| CF_KB_CD_5m_k15 | ASIA | 111 | 1.48 | 1842 | 3088 | 1.67 | 0.59 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 125 | 17 |
| CF_KB_DD_t500_k15 | NY | 209 | 2.79 | 1408 | 2433 | 1.62 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 845 | 24 |
| CF_PB3B_R5_P1_SI44_1m_k5 | NY | 369 | 4.92 | 741 | 1465 | 1.42 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 226 | 48 |
| CF_ST_SI44_5m_k5 | NY | 108 | 1.44 | 1396 | 3124 | 1.25 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1203 | 118 |
| CF_ST_DD_t500_k15 | NY-AM | 308 | 4.11 | 656 | 1545 | 1.19 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 302 | 114 |
| CF_ST_DD_1m_k15 | NY-AM | 100 | 1.33 | 1221 | 3115 | 1.10 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 752 | 110 |
| CF_ST_SI33_5m_k5 | NY-AM | 188 | 2.51 | 982 | 2611 | 1.05 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -88.0 | 116 |
| CF_ST_SI44_5m_k15 | NY-AM | 220 | 2.93 | 804 | 2147 | 1.05 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 259 | 117 |
| CF_PB3B_R5_P1_CD_1m_k5 | ASIA | 208 | 2.77 | 700 | 2390 | 0.82 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -164 | 36 |
| CF_PB3B_R5_P1_SI33_5m_k5 | NY | 311 | 4.15 | 459 | 1775 | 0.72 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 188 | 47 |
| CF_SBS_SI44_t500_k5 | NY-AM | 115 | 1.53 | 799 | 3118 | 0.72 | 0.28 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -144 | 91 |
| CF_SBS_CD_t500_k5 | NY-AM | 106 | 1.41 | 673 | 3006 | 0.63 | 0.25 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 184 | 79 |
| CF_PB3B_R5_P1_SI44_t500_k5 | NY-AM | 355 | 4.73 | 438 | 2080 | 0.59 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 79.1 | 51 |
| CF_PB3B_R5_P1_CD_5m_k15 | NY-AM | 160 | 2.13 | 241 | 2607 | 0.26 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -770 | 37 |
| CF_SBS_CD_5m_k15 | LONDON | 150 | 2.00 | 81.5 | 1127 | 0.20 | 0.21 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 67.0 | 77 |
| CF_KB_SI44_5m_k15 | NY-AM | 261 | 3.48 | 31.9 | 2043 | 0.04 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -187 | 26 |
| CF_SBS_SI44_5m_k15 | NY | 126 | 1.68 | 3.68 | 2265 | 0.00 | 0.21 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 7.03 | 89 |
| CF_ST_CD_5m_k15 | NY-AM | 175 | 2.33 | -127 | 2252 | -0.16 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -601 | 107 |
| CF_PB3B_R5_P1_CD_t500_k5 | NY-AM | 427 | 5.69 | -113 | 1953 | -0.16 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -473 | 39 |
| CF_PB3B_R5_P1_DD_t500_k15 | NY-AM | 147 | 1.96 | -335 | 2940 | -0.32 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -409 | 45 |
| CF_PB3B_R5_P1_SI44_5m_k15 | NY-PM | 138 | 1.84 | -734 | 3127 | -0.66 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -801 | 49 |
| CF_SBS_CD_1m_k5 | LONDON | 104 | 1.39 | -551 | 1173 | -1.32 | 0.18 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | 282 | 76 |
| CF_PB3B_R5_P1_DD_1m_k15 | NY | 113 | 1.51 | -1298 | 2691 | -1.35 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -1509 | 41 |


## 5. Dead pooled, alive in a session
11 cell-sessions (6 cells, 2 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CF_ST_SI44_t500_k5 | NY-AM | 439 | 5.85 | 1725 | 1584 | 3.05 | 250 | 463 | 265 | 1136 | 225 | 571 | 2431 | 230 | 1136 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 899 | 106 |
| CF_ST_CD_t500_k15 | NY | 1158 | 15.4 | 786 | 856 | 2.57 | 552 | 1325 | 878 | 3026 | 205 | 328 | 1171 | 486 | 3026 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 385 | 106 |


## 6. Notes
- 6 standalone no-row cells of DS3_TFOOTPRINT (174 standalone declared, 168 scorable) have no trades and are not re-runnable into a table.
