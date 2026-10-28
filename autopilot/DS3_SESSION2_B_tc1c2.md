# DS3_SESSION2_B_tc1c2 - T-C exit alternatives C1/C2 (TC1C2)

Written 2026-10-28T21:03:58Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tc1c2/. Prereg l2vast/ds3/prereg/SB3_tc1c2_prereg.md sha256 529a5f7de82c270256ef9383289eae086cbaecd233ba5d5c3fbab760a6137e69; PREHOLD autopilot/DS3_SESSION2_B_tc1c2_PREHOLD.md sha256 3c71e15c3b21fa1cb6f1d564277ce35bade4825949bd2d6c003ca01a6470dd43 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original D3XT assembly (tcx/dc_score.load_all + dc_asm.sequence/pts_cm/run_locks on the stored nominal-exit table dc_res*.parquet and the direct L2 replay fills R_*/X_* in /mnt/l2/l2vast/ds3_tcx): for each (stream, rule) cell the base entries are sequenced with the busy-skip, exit prices are the direct L2 replay fills (stop exits XJ stop-join, market exits 10-lot market, target exits limit at level), entry = S10x1 gap-2 s direct replay; missing fills fall back to nominal -/+ slip as in the source. Entry time = ET of the entry bar (dc_asm.et, end-stamp convention of the ledger). pnl = (direct pts - 4.84/20) x $200 (10 lots), unlocked per-trade; columns exec/pnl_lock give the lock-engine fill flag and net $ for the replay step. Basis DIRECT-L2-EXITS (the strongest basis in the repository). Trades after 2026-02-06 are dropped at load; the engine run itself covered the full stored span (the replay raw ends 2026-10-09) and was compared only up to 2026-02-06.

Reproduction: the regenerated lock-engine daily $ series of all 48 cells equals the stored _daily_r in out/tcx/score_*_final_v.pkl (rtol 1e-6, label days up to 2026-02-06) and the number of taken trades equals the stored n_taken_r: 48/48 (100%, all cells). out/sb3/tcx_repro.csv.

## 2. Multiplicity and counts
- Cells 48; F = cells x 7 sessions = **336**; overlap clusters (Jaccard >= 0.5, PRE entries) **8**, F_eff = **56**. Independent (cluster x session) PRE tests with n >= 100: 40; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 1).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 42 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 42 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 15 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 48 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 42 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 48 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C2_120_EMA5 | ASIA | 249 | 3.32 | 734 | 1098 | 1.87 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 277 | 0 |
| XT_C2_60_ST10n10 | ASIA | 198 | 2.64 | 586 | 938 | 1.75 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -455 | 4 |
| XT_C2_120_ST10n14 | ASIA | 172 | 2.29 | 827 | 1535 | 1.51 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -130 | 5 |
| XT_C2_120_ST10n10 | ASIA | 198 | 2.64 | 702 | 1332 | 1.47 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -204 | 4 |
| XT_C1_90_HM | ASIA | 489 | 6.52 | 788 | 1639 | 1.35 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 104 | 1 |
| XT_C1_120_HM | ASIA | 487 | 6.49 | 830 | 1754 | 1.33 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 92.7 | 1 |
| XT_C2_120_EMA5 | NY-AM | 183 | 2.44 | 1031 | 2230 | 1.29 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 277 | 0 |
| XT_C1_60_HM | ASIA | 500 | 6.67 | 678 | 1602 | 1.18 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 63.1 | 1 |
| XT_C2_120_ST10n7 | ASIA | 242 | 3.23 | 498 | 1264 | 1.10 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -94.7 | 6 |
| XT_C1_60_ST10n7 | NY-AM | 220 | 2.93 | 1618 | 4499 | 1.01 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -23.0 | 6 |
| XT_C1_90_ST | NY | 600 | 8.00 | 775 | 2168 | 1.00 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -243 | 3 |
| XT_C1_60_TB7 | NY-AM | 439 | 5.85 | 988 | 3256 | 0.85 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 747 | 7 |
| XT_C1_60_ST10n10 | NY-AM | 240 | 3.20 | 1195 | 4116 | 0.81 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -350 | 4 |
| XT_C2_120_EMA5 | NY | 323 | 4.31 | 463 | 1613 | 0.80 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 277 | 0 |
| XT_C1_60_TB7 | NY | 521 | 6.95 | 747 | 2922 | 0.72 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 747 | 7 |
| XT_C1_90_ST | NY-AM | 399 | 5.32 | 784 | 3156 | 0.70 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -243 | 3 |
| XT_C1_90_HM | NY-PM | 242 | 3.23 | 1542 | 6225 | 0.69 | 0.37 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 104 | 1 |
| XT_C1_60_ST | ASIA | 533 | 7.11 | 446 | 1874 | 0.67 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -335 | 3 |
| XT_C1_60_HM | NY-PM | 265 | 3.53 | 1244 | 5289 | 0.66 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 63.1 | 1 |
| XT_C1_120_ST | NY | 576 | 7.68 | 542 | 2375 | 0.64 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -389 | 3 |
| XT_C2_60_ST10n7 | ASIA | 242 | 3.23 | 225 | 1072 | 0.59 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -481 | 6 |
| XT_C2_60_EMA5 | NY-AM | 183 | 2.44 | 430 | 2124 | 0.57 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -13.8 | 0 |
| XT_C1_90_TB7 | NY | 521 | 6.95 | 646 | 3274 | 0.55 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 646 | 7 |
| XT_C1_60_ST10n14 | NY-AM | 251 | 3.35 | 744 | 3995 | 0.52 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -269 | 5 |
| XT_C1_90_ST | NY-PM | 201 | 2.68 | 758 | 4208 | 0.50 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -243 | 3 |
| XT_C1_90_HM | NY | 584 | 7.79 | 553 | 3091 | 0.50 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 104 | 1 |
| XT_C1_120_ST | NY-AM | 380 | 5.07 | 594 | 3321 | 0.50 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -389 | 3 |
| XT_C1_120_HM | NY | 556 | 7.41 | 602 | 3483 | 0.48 | 0.37 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 92.7 | 1 |
| XT_C1_90_ST | ASIA | 519 | 6.92 | 343 | 2031 | 0.47 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -243 | 3 |
| XT_C1_90_TB7 | NY-AM | 439 | 5.85 | 583 | 3545 | 0.46 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 646 | 7 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C2_120_EMA5 | ASIA | 249 | 3.32 | 734 | 1098 | 1.87 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 277 | 0 |
| XT_C2_60_ST10n10 | ASIA | 198 | 2.64 | 586 | 938 | 1.75 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -455 | 4 |
| XT_C2_120_ST10n14 | ASIA | 172 | 2.29 | 827 | 1535 | 1.51 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -130 | 5 |
| XT_C1_90_HM | ASIA | 489 | 6.52 | 788 | 1639 | 1.35 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 104 | 1 |
| XT_C2_120_ST10n7 | ASIA | 242 | 3.23 | 498 | 1264 | 1.10 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -94.7 | 6 |
| XT_C1_90_ST | NY | 600 | 8.00 | 775 | 2168 | 1.00 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -243 | 3 |
| XT_C1_60_TB7 | NY-AM | 439 | 5.85 | 988 | 3256 | 0.85 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 747 | 7 |
| XT_C1_120_KEL3 | NY | 913 | 12.2 | 234 | 2024 | 0.32 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -434 | 2 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).


## 6. Notes
- Paired exit-vs-bracket tests (the source's object) are not repeated here; this report is the per-cell entry-session score of the exit-alternative trade streams. A cell shares its entries with the base bracket of the same stream, so cells cluster with each other and with the stream's base (Jaccard on PRE entries); read the cluster column.
- Fixed-bracket survivors: only rules with a fixed 60-pt stop and fixed target (C4 level targets vary per trade, R4_T15/T20 = 60/90 and 60/120 pt) are plain entry+bracket replay legs; trail/time/flip rules have dynamic exits.
