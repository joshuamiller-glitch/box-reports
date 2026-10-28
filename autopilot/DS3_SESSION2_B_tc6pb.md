# DS3_SESSION2_B_tc6pb - T-C exit alternatives on PB books (TC6PB)

Written 2026-10-28T21:04:21Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tc6pb/. Prereg l2vast/ds3/prereg/SB3_tc6pb_prereg.md sha256 75fb99a9f0cb1559f7d1d217ce9df2cd57144954e3af179333ffc3826a599847; PREHOLD autopilot/DS3_SESSION2_B_tc6pb_PREHOLD.md sha256 5e0c871983a7e43f8ebb79c1db4c147ef5c70798782870ae5115f5e37e2504e7 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original D3XT assembly (tcx/dc_score.load_all + dc_asm.sequence/pts_cm/run_locks on the stored nominal-exit table dc_res*.parquet and the direct L2 replay fills R_*/X_* in /mnt/l2/l2vast/ds3_tcx): for each (stream, rule) cell the base entries are sequenced with the busy-skip, exit prices are the direct L2 replay fills (stop exits XJ stop-join, market exits 10-lot market, target exits limit at level), entry = S10x1 gap-2 s direct replay; missing fills fall back to nominal -/+ slip as in the source. Entry time = ET of the entry bar (dc_asm.et, end-stamp convention of the ledger). pnl = (direct pts - 4.84/20) x $200 (10 lots), unlocked per-trade; columns exec/pnl_lock give the lock-engine fill flag and net $ for the replay step. Basis DIRECT-L2-EXITS (the strongest basis in the repository). Trades after 2026-02-06 are dropped at load; the engine run itself covered the full stored span (the replay raw ends 2026-10-09) and was compared only up to 2026-02-06.

Reproduction: the regenerated lock-engine daily $ series of all 72 cells equals the stored _daily_r in out/tcx/score_*_final_v.pkl (rtol 1e-6, label days up to 2026-02-06) and the number of taken trades equals the stored n_taken_r: 72/72 (100%, all cells). out/sb3/tcx_repro.csv.

## 2. Multiplicity and counts
- Cells 72; F = cells x 7 sessions = **504**; overlap clusters (Jaccard >= 0.5, PRE entries) **7**, F_eff = **49**. Independent (cluster x session) PRE tests with n >= 100: 39; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 1).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 72 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 72 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 40 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 72 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 71 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 72 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_OPP_SM_PBS | NY | 404 | 5.39 | 3359 | 4728 | 1.99 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1580 | 1 |
| XT_OPP_SM_PBS | NY-AM | 264 | 3.52 | 4670 | 6918 | 1.89 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1580 | 1 |
| XT_C1_90_PBS | NY | 365 | 4.87 | 3143 | 4865 | 1.81 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1560 | 1 |
| XT_C2_30_PBS | PREOPEN | 134 | 1.79 | 1355 | 2182 | 1.74 | 0.60 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 101 | 1 |
| XT_C1_120_PBS | NY | 345 | 4.60 | 3073 | 5060 | 1.70 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1438 | 1 |
| XT_OPP_EM_PBS | NY | 386 | 5.15 | 2572 | 4248 | 1.70 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1417 | 1 |
| XT_C1_90_PBS | NY-AM | 231 | 3.08 | 4374 | 7378 | 1.66 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1560 | 1 |
| XT_OPP_SM_ST | NY-AM | 283 | 3.77 | 2919 | 5030 | 1.62 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 727 | 4 |
| XT_C1_120_PBS | NY-AM | 223 | 2.97 | 4266 | 7415 | 1.61 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1438 | 1 |
| XT_C4b_PB3 | ASIA | 688 | 9.17 | 861 | 1543 | 1.56 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -39.8 | 0 |
| XT_OPP_SM_ST | NY | 417 | 5.56 | 1999 | 3624 | 1.54 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 727 | 4 |
| XT_R4_TD30_PBS | PREOPEN | 101 | 1.35 | 3254 | 5924 | 1.54 | 0.37 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 58.2 | 1 |
| XT_OPP_EM_PBS | NY-AM | 232 | 3.09 | 3229 | 6040 | 1.50 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1417 | 1 |
| XT_R4_PL_PBS | NY-AM | 439 | 5.85 | 1180 | 2277 | 1.45 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 326 | 1 |
| XT_R4_CH2_PBS | PREOPEN | 110 | 1.47 | 1702 | 3337 | 1.43 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 318 | 1 |
| XT_R4_CH3_PBS | NY-AM | 395 | 5.27 | 2165 | 4381 | 1.38 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 809 | 1 |
| XT_C2_60_PBS | PREOPEN | 134 | 1.79 | 1323 | 2682 | 1.38 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 284 | 1 |
| XT_OPP_KB_PBS | NY-AM | 409 | 5.45 | 2025 | 4151 | 1.37 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 373 | 1 |
| XT_C1_60_PBS | NY-AM | 270 | 3.60 | 3080 | 6423 | 1.34 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 808 | 1 |
| XT_R4_TNONE_PBS | NY-AM | 270 | 3.60 | 3080 | 6423 | 1.34 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 808 | 1 |
| XT_R4_STB_PBS | NY-AM | 330 | 4.40 | 2577 | 5380 | 1.34 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 897 | 1 |
| XT_R4_CH2_PBS | ASIA | 507 | 6.76 | 679 | 1438 | 1.32 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 318 | 1 |
| XT_R4_MM_PBS | NY-AM | 557 | 7.43 | 678 | 1455 | 1.31 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 175 | 1 |
| XT_C5C_PBS | NY-AM | 572 | 7.63 | 616 | 1321 | 1.31 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 212 | 1 |
| XT_R4_TD60_PBS | ASIA | 507 | 6.76 | 954 | 2056 | 1.30 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 881 | 1 |
| XT_OPP_SM_KEL3 | NY | 401 | 5.35 | 1651 | 3577 | 1.29 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 894 | 3 |
| XT_C4b_PBS | NY-AM | 523 | 6.97 | 719 | 1599 | 1.26 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 294 | 1 |
| XT_R4_TD120_PBS | NY-AM | 307 | 4.09 | 2010 | 4516 | 1.25 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 652 | 1 |
| XT_C2_120_PBS | PREOPEN | 134 | 1.79 | 1243 | 2832 | 1.23 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 201 | 1 |
| XT_C5B_PBS | NY-AM | 574 | 7.65 | 593 | 1351 | 1.23 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 147 | 1 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_OPP_SM_PBS | NY | 404 | 5.39 | 3359 | 4728 | 1.99 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 1580 | 1 |
| XT_OPP_SM_ST | NY-AM | 283 | 3.77 | 2919 | 5030 | 1.62 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 727 | 4 |
| XT_C4b_PB3 | ASIA | 688 | 9.17 | 861 | 1543 | 1.56 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -39.8 | 0 |
| XT_OPP_SM_KEL3 | NY | 401 | 5.35 | 1651 | 3577 | 1.29 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 894 | 3 |
| XT_OPP_SM_HM | ASIA | 429 | 5.72 | 1175 | 2707 | 1.22 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 713 | 2 |
| XT_OPP_EM_ST10n7 | LONDON | 203 | 2.71 | 1475 | 6453 | 0.64 | 0.25 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -501 | 5 |
| XT_OPP_SM_EMA5 | NY-PM | 114 | 1.52 | 1442 | 6882 | 0.59 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -215 | 6 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).


## 6. Notes
- Paired exit-vs-bracket tests (the source's object) are not repeated here; this report is the per-cell entry-session score of the exit-alternative trade streams. A cell shares its entries with the base bracket of the same stream, so cells cluster with each other and with the stream's base (Jaccard on PRE entries); read the cluster column.
- Fixed-bracket survivors: only rules with a fixed 60-pt stop and fixed target (C4 level targets vary per trade, R4_T15/T20 = 60/90 and 60/120 pt) are plain entry+bracket replay legs; trail/time/flip rules have dynamic exits.
