# DS3_SESSION2_B_tb - T-B (TB1-TB9) entry-clock re-run and session scoring

Written 2026-10-28T20:54:15Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tb/. Prereg l2vast/ds3/prereg/SB3_tb_prereg.md sha256 95ddffc359c0f0033625709b072666a804fe5e94411411a71294566ba099f85d; PREHOLD autopilot/DS3_SESSION2_B_tb_PREHOLD.md sha256 702957c1c9113fbbef98ac0b76b501333e97f2eabb672a07c20bccbdb613fea8 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original engine (tb_lib.run_point/to_table/stitch/apply_locks with tb_cells.cells(pid), same code path as tb_run.work_cell, no placebos): the stitched grid-point trades kept by the closed-trade locks, entry time = start of the k-minute entry bar (B['ts'][ei], UTC converted to ET; market fill at the bar open +0.995 pt), pnl = net $ at the cell's lots (R=12,000), MAPPED/1-min-bar basis (stops/targets on k-min high/low, intrabar order not resolved: the source's own basis, not direct). TB10 (daily Supertrend/weekly-open, 9 cells, label-day-open entries, multi-day holds) is classified not session-scorable. Fixed brackets only for P60/T exits; A3 (3xATR) exits are dynamic, so survivors on A3 cells are not fixed-bracket replay entries.

Reproduction: the regenerated daily $ series of all 270 cells equals the stored out/T-B/<cell>.parquet series (rtol 1e-6) and the trade counts are identical: 270/270 (100%, all cells). out/sb3/tb/repro.csv.

## 2. Multiplicity and counts
- Cells 270; F = cells x 7 sessions = **1890**; overlap clusters (Jaccard >= 0.5, PRE entries) **172**, F_eff = **1204**. Independent (cluster x session) PRE tests with n >= 100: 759; PRE-selected cell-sessions 8 = 8 independent (chance at 2.5% one-sided = about 19).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 3, DEAD-IN-HOLD 5; alive cells 3, alive clusters 3. HOLD sign persistence of the selected list: 75%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 126 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 249 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 158 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 239 | 5 | 5 | 2 | 0 | 2 | TB1_ST_k15_T_N | 2295 | 2116 |
| NY-PM | 12:00-15:00 | 161 | 1 | 1 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 254 | 2 | 2 | 1 | 0 | 1 | TB1_ST_k5_T_N | 1218 | 1601 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB1_ST_k15_T_N | NY-AM | 361 | 4.81 | 2295 | 2116 | 3.04 | 0.49 | 139 | 420 | 68.4 | 2191 | -586 | -576 | 2369 | 806 | 2191 | SESSION-CANDIDATE |  | BOF:not cleared | 411 | 2 |
| TB2_WIL_k2_T_N | NY-AM | 502 | 6.69 | 1243 | 1567 | 2.22 | 0.43 | 167 | 266 | -347 | 3313 | -767 | -919 | 1088 | 588 | 3313 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 25.0 | 30 |
| TB2_WIL_k15_T_N | NY-AM | 327 | 4.36 | 1721 | 2212 | 2.18 | 0.46 | 141 | -352 | -646 | 650 | -157 | -81.5 | 1483 | 503 | 650 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 78.9 | 26 |
| TB1_ST_k2_T_N | NY-AM | 504 | 6.72 | 1190 | 1546 | 2.15 | 0.44 | 222 | 721 | 917 | -1062 | -564 | -653 | 1483 | 546 | -1062 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | -154 | 10 |
| TB9_RENKO_c1_k1_T_N | NY | 747 | 9.96 | 825 | 1080 | 2.14 | 0.41 | 381 | -821 | -1212 | 628 | -586 | -861 | 803 | -291 | 628 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | -33.7 | 155 |
| TB1_ST_k5_T_N | NY | 605 | 8.07 | 1218 | 1601 | 2.13 | 0.45 | 218 | 688 | 200 | 3425 | 34.9 | -139 | 725 | 1363 | 3425 | SESSION-CANDIDATE |  | BOF:not cleared | 245 | 17 |
| TB7_ORBNY_k1_T_N | NY-AM | 609 | 8.12 | 1145 | 1538 | 2.08 | 0.46 | 248 | 567 | 250 | 2264 | 109 | 294 | 1114 | 586 | 2264 | SESSION-CANDIDATE |  | BOF:not cleared | 588 | 131 |
| TB1_ST_k5_T_N | NY-PM | 161 | 2.15 | 2039 | 2750 | 2.08 | 0.51 | 48.0 | 139 | -1745 | 6475 | 193 | -15.6 | 1372 | 1358 | 6475 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 245 | 17 |
| TB5_MACD_k15_P60_N | NY-AM | 160 | 2.13 | 3072 | 4341 | 1.98 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 442 | 80 |
| TB1_ST_k15_T_N | NY | 513 | 6.84 | 1188 | 1701 | 1.96 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 411 | 2 |
| TB3_HMA_k15_A3_FV | PREOPEN | 123 | 1.64 | 4039 | 5816 | 1.94 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 470 | 43 |
| TB3_HMA_k15_P60_FV | PREOPEN | 124 | 1.65 | 3542 | 5135 | 1.93 | 0.26 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -31.6 | 43 |
| TB9_RENKO_c1_k1_T_N | NY-AM | 516 | 6.88 | 921 | 1346 | 1.92 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -33.7 | 155 |
| TB7_ORBNY_k1_P60_N | NY-AM | 449 | 5.99 | 2051 | 3018 | 1.90 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1853 | 130 |
| TB7_ORBNY_k1_P60_N | NY | 501 | 6.68 | 1853 | 2773 | 1.87 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1853 | 130 |
| TB7_ORBNY_k3_P60_N | NY | 490 | 6.53 | 1807 | 2929 | 1.73 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1807 | 132 |
| TB8_CLIM_k15_T_N | NY-AM | 550 | 7.33 | 1096 | 1784 | 1.72 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 399 | 143 |
| TB7_ORBNY_k3_T_N | NY-AM | 602 | 8.03 | 1022 | 1677 | 1.71 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 652 | 132 |
| TB4_KEL_k5_P60_N | ASIA | 498 | 6.64 | 997 | 1677 | 1.67 | 0.37 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 207 | 79 |
| TB1_ST_k2_T_N | PREOPEN | 217 | 2.89 | 1212 | 2047 | 1.66 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -154 | 10 |
| TB8_CLIM_k15_T_N | NY | 604 | 8.05 | 972 | 1643 | 1.66 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 399 | 143 |
| TB7_ORBNY_k3_P60_N | NY-AM | 433 | 5.77 | 1893 | 3215 | 1.65 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1807 | 132 |
| TB1_ST_k2_P60_N | PREOPEN | 188 | 2.51 | 2123 | 3623 | 1.64 | 0.29 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -166 | 10 |
| TB2_PSAR_k15_T_N | NY-AM | 444 | 5.92 | 1038 | 1776 | 1.64 | 0.44 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -82.8 | 20 |
| TB9_RENKO_c2_k1_A3_N | ASIA | 304 | 4.05 | 3530 | 6092 | 1.62 | 0.21 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1122 | 157 |
| TB3_EMA_k3_P60_N | NY | 365 | 4.87 | 1585 | 2744 | 1.62 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 167 | 39 |
| TB1_ST_k5_P60_FV | NY-PM | 223 | 2.97 | 1734 | 3120 | 1.56 | 0.27 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 79.0 | 14 |
| TB2_WIL_k15_T_N | NY | 458 | 6.11 | 1008 | 1820 | 1.55 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 78.9 | 26 |
| TB9_RENKO_c3_k1_P60_N | ASIA | 433 | 5.77 | 1268 | 2310 | 1.54 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 65.6 | 164 |
| TB2_WIL_k5_A3_FV | NY-AM | 314 | 4.19 | 2683 | 4917 | 1.53 | 0.25 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 644 | 31 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB1_ST_k15_T_N | NY-AM | 361 | 4.81 | 2295 | 2116 | 3.04 | 0.49 | 139 | 420 | 68.4 | 2191 | -586 | -576 | 2369 | 806 | 2191 | SESSION-CANDIDATE |  | BOF:not cleared | 411 | 2 |
| TB2_WIL_k2_T_N | NY-AM | 502 | 6.69 | 1243 | 1567 | 2.22 | 0.43 | 167 | 266 | -347 | 3313 | -767 | -919 | 1088 | 588 | 3313 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 25.0 | 30 |
| TB2_WIL_k15_T_N | NY-AM | 327 | 4.36 | 1721 | 2212 | 2.18 | 0.46 | 141 | -352 | -646 | 650 | -157 | -81.5 | 1483 | 503 | 650 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 78.9 | 26 |
| TB1_ST_k2_T_N | NY-AM | 504 | 6.72 | 1190 | 1546 | 2.15 | 0.44 | 222 | 721 | 917 | -1062 | -564 | -653 | 1483 | 546 | -1062 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | -154 | 10 |
| TB9_RENKO_c1_k1_T_N | NY | 747 | 9.96 | 825 | 1080 | 2.14 | 0.41 | 381 | -821 | -1212 | 628 | -586 | -861 | 803 | -291 | 628 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | -33.7 | 155 |
| TB1_ST_k5_T_N | NY | 605 | 8.07 | 1218 | 1601 | 2.13 | 0.45 | 218 | 688 | 200 | 3425 | 34.9 | -139 | 725 | 1363 | 3425 | SESSION-CANDIDATE |  | BOF:not cleared | 245 | 17 |
| TB7_ORBNY_k1_T_N | NY-AM | 609 | 8.12 | 1145 | 1538 | 2.08 | 0.46 | 248 | 567 | 250 | 2264 | 109 | 294 | 1114 | 586 | 2264 | SESSION-CANDIDATE |  | BOF:not cleared | 588 | 131 |
| TB5_MACD_k15_P60_N | NY-AM | 160 | 2.13 | 3072 | 4341 | 1.98 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 442 | 80 |
| TB3_HMA_k15_A3_FV | PREOPEN | 123 | 1.64 | 4039 | 5816 | 1.94 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 470 | 43 |
| TB7_ORBNY_k1_P60_N | NY-AM | 449 | 5.99 | 2051 | 3018 | 1.90 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1853 | 130 |
| TB7_ORBNY_k3_P60_N | NY | 490 | 6.53 | 1807 | 2929 | 1.73 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1807 | 132 |
| TB8_CLIM_k15_T_N | NY-AM | 550 | 7.33 | 1096 | 1784 | 1.72 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 399 | 143 |
| TB4_KEL_k5_P60_N | ASIA | 498 | 6.64 | 997 | 1677 | 1.67 | 0.37 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 207 | 79 |
| TB2_PSAR_k15_T_N | NY-AM | 444 | 5.92 | 1038 | 1776 | 1.64 | 0.44 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -82.8 | 20 |
| TB9_RENKO_c2_k1_A3_N | ASIA | 304 | 4.05 | 3530 | 6092 | 1.62 | 0.21 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1122 | 157 |
| TB3_EMA_k3_P60_N | NY | 365 | 4.87 | 1585 | 2744 | 1.62 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 167 | 39 |
| TB1_ST_k5_P60_FV | NY-PM | 223 | 2.97 | 1734 | 3120 | 1.56 | 0.27 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 79.0 | 14 |
| TB9_RENKO_c3_k1_P60_N | ASIA | 433 | 5.77 | 1268 | 2310 | 1.54 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 65.6 | 164 |
| TB2_WIL_k5_A3_FV | NY-AM | 314 | 4.19 | 2683 | 4917 | 1.53 | 0.25 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 644 | 31 |
| TB9_RENKO_c4_k1_T_FV | PREOPEN | 166 | 2.21 | 1076 | 1974 | 1.53 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -98.0 | 165 |
| TB9_RENKO_c4_k1_P60_N | ASIA | 238 | 3.17 | 1905 | 3514 | 1.52 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 653 | 166 |
| TB9_RENKO_c4_k1_T_N | ASIA | 214 | 2.85 | 1462 | 2726 | 1.50 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -5.65 | 167 |
| TB3_EMA_k5_A3_FV | NY-AM | 279 | 3.72 | 3010 | 5614 | 1.50 | 0.22 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 896 | 40 |
| TB1_ST_k1_T_N | NY-AM | 604 | 8.05 | 594 | 1116 | 1.49 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -252 | 6 |
| TB4_DON_k15_P60_N | ASIA | 272 | 3.63 | 1682 | 3278 | 1.44 | 0.28 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 216 | 60 |
| TB9_RENKO_c5_k1_P60_FV | LONDON | 261 | 3.48 | 1658 | 3243 | 1.43 | 0.17 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 153 | 168 |
| TB5_RSI_k15_P60_N | NY-AM | 181 | 2.41 | 2270 | 4493 | 1.41 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 189 | 91 |
| TB4_KEL_k3_A3_FV | NY-PM | 103 | 1.37 | 6511 | 12979 | 1.40 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 23.5 | 76 |
| TB9_RENKO_c1_k1_A3_N | NY-AM | 197 | 2.63 | 3142 | 6267 | 1.40 | 0.37 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 458 | 153 |
| TB1_ST_k15_T_FV | NY-AM | 578 | 7.71 | 671 | 1350 | 1.39 | 0.37 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -108 | 0 |


## 5. Dead pooled, alive in a session
3 cell-sessions (3 cells, 3 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB1_ST_k15_T_N | NY-AM | 361 | 4.81 | 2295 | 2116 | 3.04 | 139 | 420 | 68.4 | 2191 | -586 | -576 | 2369 | 806 | 2191 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 411 | 2 |
| TB1_ST_k5_T_N | NY | 605 | 8.07 | 1218 | 1601 | 2.13 | 218 | 688 | 200 | 3425 | 34.9 | -139 | 725 | 1363 | 3425 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 245 | 17 |
| TB7_ORBNY_k1_T_N | NY-AM | 609 | 8.12 | 1145 | 1538 | 2.08 | 248 | 567 | 250 | 2264 | 109 | 294 | 1114 | 586 | 2264 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 588 | 131 |

