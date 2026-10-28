# DS3_SESSION2_B_tb2 - T-B2 (TB3/TB6/TB7/TB8) entry-clock re-run and session scoring

Written 2026-10-28T20:59:04Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tb2/. Prereg l2vast/ds3/prereg/SB3_tb2_prereg.md sha256 c4af4764616a83aa7f11e74d15cd4408b3f24832d4c53c9ae77252c2bc4050d6; PREHOLD autopilot/DS3_SESSION2_B_tb2_PREHOLD.md sha256 5cf84b8a9efe1df6cfcde3597e7caf708496232d65cc18ddf0ef6ad9a4e199a9 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original T-ENTRY/tb2 path (tb2_common CE.build -> te_core.gen_entries -> DS2 bracket 60 pt stop / 1.0R on the 1-s path -> MAPPED corrected-P9 points -> exact per-book lock engine at 10 lots, te_core.run_rows): trade table = lock-engine executed rows (f>0), entry time = Ctx et_in (ET, bar end stamp as in the ledger), pnl = lock-engine net $ at 10 lots, basis MAPPED. Brackets are fixed 60/60 pt (expressible for the fixed-bracket replay).

Reproduction: the daily $ series of every regenerated cell equals the stored out/tb2/res_<group>_daily.parquet column (rtol 1e-6): 97 of 97 (100%, all cells with >=100 trades). The other 16 declared cells (TB8 CPI/NFP/FOMC with 29-44 events) have <100 trades in total, were not scored by the original ('too few trades') and cannot reach n>=100 in any session; not regenerated into the score table. out/sb3/tb2/repro.csv.

## 2. Multiplicity and counts
- Cells 97; F = cells x 7 sessions = **679**; overlap clusters (Jaccard >= 0.5, PRE entries) **84**, F_eff = **588**. Independent (cluster x session) PRE tests with n >= 100: 247; PRE-selected cell-sessions 13 = 9 independent (chance at 2.5% one-sided = about 6).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 5, DEAD-IN-HOLD 8; alive cells 3, alive clusters 2. HOLD sign persistence of the selected list: 77%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 44 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 39 | 1 | 1 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 25 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 61 | 6 | 4 | 2 | 0 | 2 | TB3W_cdb60_ofiq0.99_W3 | 1339 | 1502 |
| NY-PM | 12:00-15:00 | 35 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 8 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 64 | 6 | 4 | 3 | 0 | 2 | TB3_cdb_ofi_W3 | 1290 | 1374 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB3_cdb_ofi_W3 | NY | 482 | 6.43 | 1290 | 1374 | 2.63 | 0.56 | 293 | 689 | 851 | 96.2 | 92.8 | -112 | 1183 | 1174 | 96.2 | SESSION-CANDIDATE |  | BOF:not cleared | 1248 | 2 |
| TB3W_cdb60_ofiq0.99_W3 | NY | 570 | 7.60 | 1215 | 1308 | 2.60 | 0.56 | 331 | 551 | 666 | 131 | 224 | -20.4 | 1278 | 918 | 131 | SESSION-CANDIDATE |  | BOF:not cleared | 1201 | 2 |
| TB3W_cdb60_ofiq0.99_W3 | NY-AM | 417 | 5.56 | 1339 | 1502 | 2.50 | 0.56 | 270 | 419 | 478 | 189 | 442 | 246 | 1187 | 1003 | 189 | SESSION-CANDIDATE |  | BOF:not cleared | 1201 | 2 |
| TB6_t1000_follow_L31 | NY | 363 | 4.84 | 1325 | 1517 | 2.45 | 0.56 | 157 | 369 | 114 | 1653 | -1083 | -1313 | 1830 | 166 | 1653 | SESSION-CANDIDATE |  | BOF:not cleared | 1325 | 40 |
| TB6_t1000_follow_L31 | NY-AM | 363 | 4.84 | 1325 | 1517 | 2.45 | 0.56 | 157 | 369 | 114 | 1653 | -1083 | -1313 | 1830 | 166 | 1653 | SESSION-CANDIDATE |  | BOF:not cleared | 1325 | 40 |
| TB3_cdb_ofi_W3 | NY-AM | 360 | 4.80 | 1346 | 1555 | 2.42 | 0.56 | 232 | 462 | 733 | -602 | 556 | 512 | 984 | 1281 | -602 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1248 | 2 |
| TB7_ZN_w15_q0.98 | NY | 362 | 4.83 | 1144 | 1350 | 2.37 | 0.55 | 66.0 | -2330 | -1904 | -3779 | 182 | 706 | 785 | 390 | -3779 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 141 | 74 |
| TB7_ES_don3m | NY-AM | 545 | 7.27 | 1043 | 1271 | 2.30 | 0.54 | 235 | 288 | -281 | 3896 | -650 | -226 | 298 | 733 | 3896 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 504 | 64 |
| TB7L_ES_w3_all | LONDON | 146 | 1.95 | 2036 | 2515 | 2.27 | 0.59 | 24.0 | -1706 | -2254 | -62.3 | 2182 | 3743 | 1849 | 1381 | -62.3 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 6.81 | 42 |
| TB3W_cdb240_ofiq0.99_W3 | NY-AM | 330 | 4.40 | 1434 | 1803 | 2.23 | 0.56 | 219 | 136 | 400 | -856 | 254 | 223 | 1044 | 1080 | -856 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1223 | 2 |
| TB7_ZN_w15_q0.98 | NY-AM | 272 | 3.63 | 1260 | 1707 | 2.07 | 0.55 | 50.0 | -3501 | -3382 | -3779 | -217 | 101 | 1254 | -11.0 | -3779 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 141 | 74 |
| TB3W_cdb240_ofiq0.99_W3 | NY | 416 | 5.55 | 1142 | 1599 | 2.00 | 0.55 | 265 | 342 | 551 | -441 | -27.8 | -163 | 1050 | 871 | -441 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1223 | 2 |
| TB7_ES_don3m | NY | 825 | 11.0 | 780 | 1095 | 1.99 | 0.52 | 344 | 478 | -40.5 | 3602 | -274 | -103 | 650 | 341 | 3602 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 504 | 64 |
| TB7_ES_don5m_lag | ASIA | 359 | 4.79 | 1187 | 1698 | 1.96 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 458 | 67 |
| TB7L_RTY_w1_lag | ASIA | 162 | 2.16 | 1618 | 2533 | 1.79 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -125 | 46 |
| TB6_t1000_follow_L16 | NY | 363 | 4.84 | 1084 | 1715 | 1.77 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1084 | 40 |
| TB6_t1000_follow_L16 | NY-AM | 363 | 4.84 | 1084 | 1715 | 1.77 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1084 | 40 |
| TB3_st5_ofi_W3 | NY | 165 | 2.20 | 1667 | 2671 | 1.75 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1451 | 21 |
| TB3_kelt5_ofi_W3 | NY | 303 | 4.04 | 994 | 1618 | 1.72 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1083 | 19 |
| TB7_RTY_don3m | PREOPEN | 115 | 1.53 | 1724 | 2816 | 1.71 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 44.8 | 69 |
| TB7L_RTY_w3_all | LONDON | 142 | 1.89 | 1395 | 2308 | 1.69 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -286 | 47 |
| TB3_hma5_cdb_W3 | NY | 359 | 4.79 | 823 | 1407 | 1.64 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -8.85 | 13 |
| TB7W_ES_don3m_n14 | NY-AM | 547 | 7.29 | 749 | 1294 | 1.62 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 277 | 54 |
| TB3_don3_ofi_W3 | NY-AM | 377 | 5.03 | 897 | 1553 | 1.62 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 736 | 8 |
| TB3_kelt5_ofi_W3 | NY-AM | 218 | 2.91 | 1134 | 1965 | 1.62 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1083 | 19 |
| TB3_don3_ofi_W3 | NY | 512 | 6.83 | 762 | 1409 | 1.51 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 736 | 8 |
| TB3W_cdb120_ofiq0.995_W3 | NY | 289 | 3.85 | 961 | 1779 | 1.51 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1010 | 1 |
| TB7W_ES_don2m_n30 | NY-AM | 516 | 6.88 | 749 | 1427 | 1.47 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 237 | 53 |
| TB7_RTY_don5m_lag | LONDON | 357 | 4.76 | 845 | 1629 | 1.45 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 385 | 72 |
| TB3_don3_ofi_W1 | NY | 167 | 2.23 | 1219 | 2363 | 1.44 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1106 | 7 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB3_cdb_ofi_W3 | NY | 482 | 6.43 | 1290 | 1374 | 2.63 | 0.56 | 293 | 689 | 851 | 96.2 | 92.8 | -112 | 1183 | 1174 | 96.2 | SESSION-CANDIDATE |  | BOF:not cleared | 1248 | 2 |
| TB6_t1000_follow_L31 | NY | 363 | 4.84 | 1325 | 1517 | 2.45 | 0.56 | 157 | 369 | 114 | 1653 | -1083 | -1313 | 1830 | 166 | 1653 | SESSION-CANDIDATE |  | BOF:not cleared | 1325 | 40 |
| TB7_ZN_w15_q0.98 | NY | 362 | 4.83 | 1144 | 1350 | 2.37 | 0.55 | 66.0 | -2330 | -1904 | -3779 | 182 | 706 | 785 | 390 | -3779 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 141 | 74 |
| TB7_ES_don3m | NY-AM | 545 | 7.27 | 1043 | 1271 | 2.30 | 0.54 | 235 | 288 | -281 | 3896 | -650 | -226 | 298 | 733 | 3896 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 504 | 64 |
| TB7L_ES_w3_all | LONDON | 146 | 1.95 | 2036 | 2515 | 2.27 | 0.59 | 24.0 | -1706 | -2254 | -62.3 | 2182 | 3743 | 1849 | 1381 | -62.3 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 6.81 | 42 |
| TB7_ES_don5m_lag | ASIA | 359 | 4.79 | 1187 | 1698 | 1.96 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 458 | 67 |
| TB7L_RTY_w1_lag | ASIA | 162 | 2.16 | 1618 | 2533 | 1.79 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -125 | 46 |
| TB3_st5_ofi_W3 | NY | 165 | 2.20 | 1667 | 2671 | 1.75 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1451 | 21 |
| TB3_kelt5_ofi_W3 | NY | 303 | 4.04 | 994 | 1618 | 1.72 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1083 | 19 |
| TB7_RTY_don3m | PREOPEN | 115 | 1.53 | 1724 | 2816 | 1.71 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 44.8 | 69 |
| TB7L_RTY_w3_all | LONDON | 142 | 1.89 | 1395 | 2308 | 1.69 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -286 | 47 |
| TB3_hma5_cdb_W3 | NY | 359 | 4.79 | 823 | 1407 | 1.64 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -8.85 | 13 |
| TB7W_ES_don3m_n14 | NY-AM | 547 | 7.29 | 749 | 1294 | 1.62 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 277 | 54 |
| TB3_don3_ofi_W3 | NY-AM | 377 | 5.03 | 897 | 1553 | 1.62 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 736 | 8 |
| TB3W_cdb120_ofiq0.995_W3 | NY | 289 | 3.85 | 961 | 1779 | 1.51 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1010 | 1 |
| TB7W_ES_don2m_n30 | NY-AM | 516 | 6.88 | 749 | 1427 | 1.47 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 237 | 53 |
| TB7_RTY_don5m_lag | LONDON | 357 | 4.76 | 845 | 1629 | 1.45 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 385 | 72 |
| TB3_don3_ofi_W1 | NY | 167 | 2.23 | 1219 | 2363 | 1.44 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1106 | 7 |
| TB7W_ES_don3m_n30 | NY-AM | 485 | 6.47 | 673 | 1341 | 1.40 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 280 | 55 |
| TB7_RTY_don5m | ASIA | 646 | 8.61 | 571 | 1168 | 1.37 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 186 | 71 |
| TB3_don5_ofi_W3 | NY-PM | 109 | 1.45 | 1151 | 2383 | 1.35 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 788 | 12 |
| TB6_moc1530_fade_L30 | CLOSE | 347 | 4.63 | 665 | 1417 | 1.31 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 665 | 37 |
| TB3_don3_cdb_W1 | LONDON | 232 | 3.09 | 996 | 2158 | 1.29 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 136 | 5 |
| TB7L_RTY_w3_fade | PREOPEN | 182 | 2.43 | 1103 | 2497 | 1.24 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -310 | 48 |
| TB7W_ES_don4m_n14 | ASIA | 722 | 9.63 | 495 | 1123 | 1.23 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -5.85 | 56 |
| TB7_ES_don3m_lag | LONDON | 339 | 4.52 | 706 | 1657 | 1.19 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 363 | 65 |
| TB6_drive_570_N10 | NY-AM | 363 | 4.84 | 709 | 1679 | 1.18 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 709 | 32 |
| TB3W_cdb60_ofiq0.98_W3 | NY-AM | 605 | 8.07 | 599 | 1462 | 1.15 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 272 | 0 |
| TB7W_ES_don2m_n14 | ASIA | 624 | 8.32 | 485 | 1200 | 1.13 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 188 | 51 |
| TB6_drive_570_N15 | NY-AM | 363 | 4.84 | 631 | 1567 | 1.13 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 631 | 33 |


## 5. Dead pooled, alive in a session
2 cell-sessions (1 cells, 2 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB6_t1000_follow_L31 | NY-AM | 363 | 4.84 | 1325 | 1517 | 2.45 | 157 | 369 | 114 | 1653 | -1083 | -1313 | 1830 | 166 | 1653 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1325 | 40 |
| TB6_t1000_follow_L31 | NY | 363 | 4.84 | 1325 | 1517 | 2.45 | 157 | 369 | 114 | 1653 | -1083 | -1313 | 1830 | 166 | 1653 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1325 | 40 |

