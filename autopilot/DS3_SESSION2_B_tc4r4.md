# DS3_SESSION2_B_tc4r4 - T-C exit alternatives R4 (TC4R4)

Written 2026-10-28T21:04:14Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tc4r4/. Prereg l2vast/ds3/prereg/SB3_tc4r4_prereg.md sha256 c4232f8afef1fb7f2cb79303aa23d1491909496f906c2e989a51c02689e39a48; PREHOLD autopilot/DS3_SESSION2_B_tc4r4_PREHOLD.md sha256 fda8c048adb899bca0c4749238df11bd39dce7dc9b8efda22d07f7515f8a4a54 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original D3XT assembly (tcx/dc_score.load_all + dc_asm.sequence/pts_cm/run_locks on the stored nominal-exit table dc_res*.parquet and the direct L2 replay fills R_*/X_* in /mnt/l2/l2vast/ds3_tcx): for each (stream, rule) cell the base entries are sequenced with the busy-skip, exit prices are the direct L2 replay fills (stop exits XJ stop-join, market exits 10-lot market, target exits limit at level), entry = S10x1 gap-2 s direct replay; missing fills fall back to nominal -/+ slip as in the source. Entry time = ET of the entry bar (dc_asm.et, end-stamp convention of the ledger). pnl = (direct pts - 4.84/20) x $200 (10 lots), unlocked per-trade; columns exec/pnl_lock give the lock-engine fill flag and net $ for the replay step. Basis DIRECT-L2-EXITS (the strongest basis in the repository). Trades after 2026-02-06 are dropped at load; the engine run itself covered the full stored span (the replay raw ends 2026-10-09) and was compared only up to 2026-02-06.

Reproduction: the regenerated lock-engine daily $ series of all 70 cells equals the stored _daily_r in out/tcx/score_*_final_v.pkl (rtol 1e-6, label days up to 2026-02-06) and the number of taken trades equals the stored n_taken_r: 70/70 (100%, all cells). out/sb3/tcx_repro.csv.

## 2. Multiplicity and counts
- Cells 70; F = cells x 7 sessions = **490**; overlap clusters (Jaccard >= 0.5, PRE entries) **5**, F_eff = **35**. Independent (cluster x session) PRE tests with n >= 100: 28; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 1).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 70 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 70 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 31 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 70 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 63 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 70 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_R4_T15_HM | ASIA | 532 | 7.09 | 921 | 1650 | 1.56 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 65.5 | 1 |
| XT_R4_PL_ST | ASIA | 583 | 7.77 | 1121 | 2044 | 1.54 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -33.2 | 3 |
| XT_R4_PL_ST10n7 | ASIA | 239 | 3.19 | 1533 | 2881 | 1.49 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -119 | 4 |
| XT_R4_PL_KEL3 | NY-AM | 612 | 8.16 | 871 | 1695 | 1.44 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 128 | 2 |
| XT_R4_MM_EMA5 | ASIA | 249 | 3.32 | 1085 | 2123 | 1.43 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 293 | 0 |
| XT_R4_MM_ST10n7 | ASIA | 242 | 3.23 | 1115 | 2344 | 1.33 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 195 | 4 |
| XT_R4_T15_ST | ASIA | 597 | 7.96 | 733 | 1716 | 1.20 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -350 | 3 |
| XT_R4_MM_HM | ASIA | 607 | 8.09 | 511 | 1207 | 1.19 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -437 | 1 |
| XT_R4_TNONE_HM | NY-PM | 143 | 1.91 | 2841 | 7020 | 1.13 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -697 | 1 |
| XT_R4_MM_ST | ASIA | 680 | 9.07 | 479 | 1188 | 1.13 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -243 | 3 |
| XT_R4_CH3_EMA5 | ASIA | 249 | 3.32 | 619 | 1570 | 1.10 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -460 | 0 |
| XT_R4_PL_HM | ASIA | 517 | 6.89 | 748 | 1905 | 1.10 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -31.0 | 1 |
| XT_R4_TD60_HM | ASIA | 513 | 6.84 | 591 | 1529 | 1.08 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 175 | 1 |
| XT_R4_TD60_ST10n7 | ASIA | 241 | 3.21 | 893 | 2340 | 1.07 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -2.56 | 4 |
| XT_R4_ONH_HM | NY-PM | 143 | 1.91 | 2485 | 6779 | 1.03 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -781 | 1 |
| XT_R4_T20_ST | ASIA | 563 | 7.51 | 745 | 2049 | 1.02 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -153 | 3 |
| XT_R4_STB_EMA5 | ASIA | 248 | 3.31 | 743 | 2061 | 1.01 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -216 | 0 |
| XT_R4_T15_ST10n7 | ASIA | 240 | 3.20 | 935 | 2609 | 1.00 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -332 | 4 |
| XT_R4_MM_ST10n7 | LONDON | 259 | 3.45 | 701 | 2017 | 0.97 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 195 | 4 |
| XT_R4_T20_KEL3 | NY-AM | 549 | 7.32 | 697 | 2071 | 0.94 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -177 | 2 |
| XT_R4_STB_ST10n7 | NY-AM | 220 | 2.93 | 1378 | 4217 | 0.92 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 262 | 4 |
| XT_R4_CH2_ST10n7 | ASIA | 242 | 3.23 | 663 | 2039 | 0.91 | 0.44 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -901 | 4 |
| XT_R4_TD120_EMA5 | LONDON | 217 | 2.89 | 1625 | 5036 | 0.90 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -4.75 | 0 |
| XT_R4_TD60_EMA5 | ASIA | 249 | 3.32 | 669 | 2118 | 0.88 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -406 | 0 |
| XT_R4_T20_ST10n7 | ASIA | 236 | 3.15 | 959 | 3051 | 0.88 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -540 | 4 |
| XT_R4_PL_EMA5 | ASIA | 247 | 3.29 | 805 | 2631 | 0.86 | 0.44 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -213 | 0 |
| XT_R4_T15_KEL3 | ASIA | 627 | 8.36 | 507 | 1706 | 0.83 | 0.44 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 85.9 | 2 |
| XT_R4_PL_KEL3 | NY | 1047 | 14.0 | 364 | 1232 | 0.83 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 128 | 2 |
| XT_R4_T20_HM | ASIA | 501 | 6.68 | 540 | 1953 | 0.77 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -578 | 1 |
| XT_R4_MM_EMA5 | NY-AM | 182 | 2.43 | 781 | 2875 | 0.76 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 293 | 0 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_R4_T15_HM | ASIA | 532 | 7.09 | 921 | 1650 | 1.56 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 65.5 | 1 |
| XT_R4_PL_ST | ASIA | 583 | 7.77 | 1121 | 2044 | 1.54 | 0.45 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -33.2 | 3 |
| XT_R4_PL_ST10n7 | ASIA | 239 | 3.19 | 1533 | 2881 | 1.49 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -119 | 4 |
| XT_R4_PL_KEL3 | NY-AM | 612 | 8.16 | 871 | 1695 | 1.44 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 128 | 2 |
| XT_R4_MM_EMA5 | ASIA | 249 | 3.32 | 1085 | 2123 | 1.43 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 293 | 0 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).


## 6. Notes
- Paired exit-vs-bracket tests (the source's object) are not repeated here; this report is the per-cell entry-session score of the exit-alternative trade streams. A cell shares its entries with the base bracket of the same stream, so cells cluster with each other and with the stream's base (Jaccard on PRE entries); read the cluster column.
- Fixed-bracket survivors: only rules with a fixed 60-pt stop and fixed target (C4 level targets vary per trade, R4_T15/T20 = 60/90 and 60/120 pt) are plain entry+bracket replay legs; trail/time/flip rules have dynamic exits.
