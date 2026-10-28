# DS3_SESSION2_B_te2 - T-E2E3 (other instruments, trend families) entry-clock re-run and session scoring

Written 2026-10-28T20:57:21Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/te2/. Prereg l2vast/ds3/prereg/SB3_te2_prereg.md sha256 86b588988f199ad4a8dc66df5bdda3ee559dd0e86749f5acacafc66dbbe356a6; PREHOLD autopilot/DS3_SESSION2_B_te2_PREHOLD.md sha256 4234ff2c69a1eaab4b52bf5f9f2d27107855277b1ecdbfae5379a260ca64eeaf (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original engine (te2_lib.tables_for/stitch/assemble/locks via te2_run, same code path as work_cell without the placebo): kept (closed-trade locks) stitched trades, entry time = start of the entry bar (B['ts'][ei] converted to ET), pnl = netR x 12,000 (instrument costs: STD commission, slippage ticks per te2_lib.INSTR), lots = 12,000/(ATR stop x point value). Basis MAPPED-1MIN-BAR (stop 3xATR14, target 1R, reversal exit: dynamic ATR bracket, so these are NOT fixed-bracket replay entries). Baskets = equal-weight union of the 17 member cells (pnl/17), as in te2_p12. Cost variants re-run with the comm override. Sessions are ET clock sessions applied to each instrument's own entry times (GC/CL/FX/rates have their own liquid hours; the NQ session map is applied as the directive requires).

Reproduction: daily $ series of each of the 270 single cells and 8 variants matches stored out/TE2/work_P*.pkl 'd' (rtol 1e-6) and trade counts equal; baskets are built from the members (their stored d = mean of members). See out/sb3/te2/repro.csv.

## 2. Multiplicity and counts
- Cells 293; F = cells x 7 sessions = **2051**; overlap clusters (Jaccard >= 0.5, PRE entries) **286**, F_eff = **2002**. Independent (cluster x session) PRE tests with n >= 100: 1280; PRE-selected cell-sessions 5 = 3 independent (chance at 2.5% one-sided = about 32).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 4, DEAD-IN-HOLD 1; alive cells 2, alive clusters 1. HOLD sign persistence of the selected list: 80%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 272 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 267 | 1 | 1 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 139 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 230 | 2 | 1 | 2 | 0 | 1 | TE2_NQ_ST_k15 | 1293 | 1150 |
| NY-PM | 12:00-15:00 | 143 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 262 | 2 | 1 | 2 | 0 | 1 | TE2_NQ_ST_k15 | 854 | 907 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE2_NQ_ST_k15 | NY-AM | 523 | 6.97 | 1293 | 1150 | 3.15 | 0.50 | 197 | 774 | 503 | 2122 | 246 | 220 | 1448 | 604 | 2122 | SESSION-CANDIDATE |  | BOF:not cleared | 91.3 | 167 |
| TE2_NQ_ST_k15 | NY | 725 | 9.67 | 854 | 907 | 2.63 | 0.49 | 243 | 747 | 473 | 2061 | 342 | 188 | 1159 | 311 | 2061 | SESSION-CANDIDATE |  | BOF:not cleared | 91.3 | 167 |
| TE2_MNQ_ST_k15 | NY-AM | 494 | 6.59 | 1066 | 1239 | 2.41 | 0.50 | 197 | 696 | 422 | 2060 | 113 | 81.7 | 1094 | 605 | 2060 | SESSION-CANDIDATE |  | BOF:not cleared | -74.0 | 167 |
| TE2_GC_DON_k15 | LONDON | 203 | 2.71 | 1588 | 2170 | 2.05 | 0.56 | 168 | -183 | 283 | -4062 | -1651 | -2292 | 1974 | 547 | -4062 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | -189 | 122 |
| TE2_MNQ_ST_k15 | NY | 677 | 9.03 | 709 | 983 | 2.02 | 0.50 | 243 | 673 | 395 | 2002 | 171 | -3.02 | 854 | 410 | 2002 | SESSION-CANDIDATE |  | BOF:not cleared | -74.0 | 167 |
| TE2_ES_EMA_k15 | NY-AM | 216 | 2.88 | 1398 | 1997 | 1.96 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -170 | 108 |
| TE2_ES_KEL_k15 | NY-AM | 263 | 3.51 | 1237 | 1863 | 1.86 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 433 | 112 |
| TE2_MBT_DON_k15 | ASIA | 476 | 6.35 | 686 | 1098 | 1.75 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 110 | 138 |
| TE2_ES_KEL_k15 | ASIA | 157 | 2.09 | 899 | 1541 | 1.63 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 433 | 112 |
| TE2_MES_KEL_k15 | NY-AM | 263 | 3.51 | 1075 | 1863 | 1.62 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 245 | 112 |
| TE2_NQ_KEL_k5 | NY-PM | 177 | 2.36 | 988 | 1766 | 1.57 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -316 | 191 |
| TE2_YM_DON_k5 | NY-PM | 111 | 1.48 | 1483 | 2967 | 1.40 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -738 | 213 |
| TE2_ES_KEL_k15 | NY | 382 | 5.09 | 690 | 1390 | 1.39 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 433 | 112 |
| TE2_MES_KEL_k15 | ASIA | 157 | 2.09 | 740 | 1533 | 1.35 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 245 | 112 |
| TE2_GC_EMA_k15 | LONDON | 334 | 4.45 | 840 | 1772 | 1.33 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -43.4 | 124 |
| TE2_YM_HMA_k5 | PREOPEN | 123 | 1.64 | 1507 | 3295 | 1.28 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -828 | 217 |
| TE2_MBT_DON_k5 | NY | 371 | 4.95 | 680 | 1514 | 1.26 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -371 | 139 |
| TE2_NQ_VWAP_k5 | NY | 487 | 6.49 | 518 | 1164 | 1.25 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -800 | 197 |
| TE2_GC_VWAP_k15 | ASIA | 513 | 6.84 | 404 | 912 | 1.24 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 190 | 135 |
| TE2_ES_EMA_k5 | NY | 458 | 6.11 | 580 | 1312 | 1.24 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -643 | 109 |
| TE2_CL_PSAR_k15 | PREOPEN | 159 | 2.12 | 1003 | 2318 | 1.21 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -1165 | 100 |
| TE2_YM_ST_k5 | NY-PM | 136 | 1.81 | 1028 | 2448 | 1.18 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -1111 | 223 |
| TE2_ES_ST_k15 | NY-AM | 362 | 4.83 | 663 | 1626 | 1.14 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -157 | 117 |
| TE2_ES_DON_k5 | NY-AM | 238 | 3.17 | 953 | 2340 | 1.14 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -945 | 107 |
| TE2_MES_KEL_k15 | NY | 382 | 5.09 | 538 | 1390 | 1.08 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 245 | 112 |
| TE2_MBT_KEL_k15 | ASIA | 394 | 5.25 | 498 | 1289 | 1.08 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -60.7 | 144 |
| TE2_ES_ORB_k5 | NY-AM | 449 | 5.99 | 584 | 1552 | 1.05 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 29.1 | 114 |
| TE2_NQ_KEL_k15 | NY-AM | 388 | 5.17 | 527 | 1416 | 1.04 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -235 | 190 |
| TE2_MBT_EMA_k5 | NY-AM | 270 | 3.60 | 705 | 1911 | 1.03 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -363 | 141 |
| TE2_NQ_VWAP_k5 | NY-PM | 171 | 2.28 | 663 | 1811 | 1.03 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -800 | 197 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE2_NQ_ST_k15 | NY-AM | 523 | 6.97 | 1293 | 1150 | 3.15 | 0.50 | 197 | 774 | 503 | 2122 | 246 | 220 | 1448 | 604 | 2122 | SESSION-CANDIDATE |  | BOF:not cleared | 91.3 | 167 |
| TE2_GC_DON_k15 | LONDON | 203 | 2.71 | 1588 | 2170 | 2.05 | 0.56 | 168 | -183 | 283 | -4062 | -1651 | -2292 | 1974 | 547 | -4062 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | -189 | 122 |
| TE2_ES_EMA_k15 | NY-AM | 216 | 2.88 | 1398 | 1997 | 1.96 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -170 | 108 |
| TE2_ES_KEL_k15 | NY-AM | 263 | 3.51 | 1237 | 1863 | 1.86 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 433 | 112 |
| TE2_MBT_DON_k15 | ASIA | 476 | 6.35 | 686 | 1098 | 1.75 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 110 | 138 |
| TE2_NQ_KEL_k5 | NY-PM | 177 | 2.36 | 988 | 1766 | 1.57 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -316 | 191 |
| TE2_YM_DON_k5 | NY-PM | 111 | 1.48 | 1483 | 2967 | 1.40 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -738 | 213 |
| TE2_GC_EMA_k15 | LONDON | 334 | 4.45 | 840 | 1772 | 1.33 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -43.4 | 124 |
| TE2_YM_HMA_k5 | PREOPEN | 123 | 1.64 | 1507 | 3295 | 1.28 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -828 | 217 |
| TE2_MBT_DON_k5 | NY | 371 | 4.95 | 680 | 1514 | 1.26 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -371 | 139 |
| TE2_NQ_VWAP_k5 | NY | 487 | 6.49 | 518 | 1164 | 1.25 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -800 | 197 |
| TE2_GC_VWAP_k15 | ASIA | 513 | 6.84 | 404 | 912 | 1.24 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 190 | 135 |
| TE2_ES_EMA_k5 | NY | 458 | 6.11 | 580 | 1312 | 1.24 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -643 | 109 |
| TE2_CL_PSAR_k15 | PREOPEN | 159 | 2.12 | 1003 | 2318 | 1.21 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -1165 | 100 |
| TE2_YM_ST_k5 | NY-PM | 136 | 1.81 | 1028 | 2448 | 1.18 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -1111 | 223 |
| TE2_ES_ST_k15 | NY-AM | 362 | 4.83 | 663 | 1626 | 1.14 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -157 | 117 |
| TE2_ES_DON_k5 | NY-AM | 238 | 3.17 | 953 | 2340 | 1.14 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -945 | 107 |
| TE2_MBT_KEL_k15 | ASIA | 394 | 5.25 | 498 | 1289 | 1.08 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -60.7 | 144 |
| TE2_ES_ORB_k5 | NY-AM | 449 | 5.99 | 584 | 1552 | 1.05 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 29.1 | 114 |
| TE2_NQ_KEL_k15 | NY-AM | 388 | 5.17 | 527 | 1416 | 1.04 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -235 | 190 |
| TE2_MBT_EMA_k5 | NY-AM | 270 | 3.60 | 705 | 1911 | 1.03 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -363 | 141 |
| TE2_NQ_ST_k5 | NY | 476 | 6.35 | 414 | 1146 | 1.01 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -430 | 195 |
| TE2_NQ_PSAR_k15 | NY-AM | 514 | 6.85 | 418 | 1163 | 1.01 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -239 | 193 |
| TE2_YM_ST_k15 | NY | 700 | 9.33 | 363 | 1068 | 0.95 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -90.0 | 222 |
| TE2_ES_HMA_k15 | NY-AM | 358 | 4.77 | 553 | 1692 | 0.92 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -411 | 110 |
| TE2_MBT_ST_k15 | LONDON | 401 | 5.35 | 522 | 1615 | 0.90 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 143 | 90 |
| TE2_MBT_VWAP_k15 | ASIA | 453 | 6.04 | 261 | 837 | 0.88 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -140 | 150 |
| TE2_RTY_ST_k5 | NY-AM | 222 | 2.96 | 634 | 2150 | 0.83 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -1126 | 209 |
| TE2_NQ_EMA_k15 | NY-AM | 293 | 3.91 | 483 | 1714 | 0.79 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -445 | 186 |
| TE2_YM_VWAP_k5 | NY-PM | 160 | 2.13 | 501 | 1850 | 0.76 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -1154 | 225 |


## 5. Dead pooled, alive in a session
4 cell-sessions (2 cells, 2 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE2_NQ_ST_k15 | NY-AM | 523 | 6.97 | 1293 | 1150 | 3.15 | 197 | 774 | 503 | 2122 | 246 | 220 | 1448 | 604 | 2122 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 91.3 | 167 |
| TE2_NQ_ST_k15 | NY | 725 | 9.67 | 854 | 907 | 2.63 | 243 | 747 | 473 | 2061 | 342 | 188 | 1159 | 311 | 2061 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 91.3 | 167 |

