# DS3_SESSION2_B_tc3c4 - T-C exit alternatives C3/C4 (TC3C4)

Written 2026-10-28T21:04:03Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tc3c4/. Prereg l2vast/ds3/prereg/SB3_tc3c4_prereg.md sha256 872d13f8a83b0eaf42ab620401c93c5b44e24b90a1a73e9ee7511574bbe366e2; PREHOLD autopilot/DS3_SESSION2_B_tc3c4_PREHOLD.md sha256 f2bbbd75d0e199221e321f2953b371ede5bd7dd30ac0510b0a30a9ed5fb33afc (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original D3XT assembly (tcx/dc_score.load_all + dc_asm.sequence/pts_cm/run_locks on the stored nominal-exit table dc_res*.parquet and the direct L2 replay fills R_*/X_* in /mnt/l2/l2vast/ds3_tcx): for each (stream, rule) cell the base entries are sequenced with the busy-skip, exit prices are the direct L2 replay fills (stop exits XJ stop-join, market exits 10-lot market, target exits limit at level), entry = S10x1 gap-2 s direct replay; missing fills fall back to nominal -/+ slip as in the source. Entry time = ET of the entry bar (dc_asm.et, end-stamp convention of the ledger). pnl = (direct pts - 4.84/20) x $200 (10 lots), unlocked per-trade; columns exec/pnl_lock give the lock-engine fill flag and net $ for the replay step. Basis DIRECT-L2-EXITS (the strongest basis in the repository). Trades after 2026-02-06 are dropped at load; the engine run itself covered the full stored span (the replay raw ends 2026-10-09) and was compared only up to 2026-02-06.

Reproduction: the regenerated lock-engine daily $ series of all 32 cells equals the stored _daily_r in out/tcx/score_*_final_v.pkl (rtol 1e-6, label days up to 2026-02-06) and the number of taken trades equals the stored n_taken_r: 32/32 (100%, all cells). out/sb3/tcx_repro.csv.

## 2. Multiplicity and counts
- Cells 32; F = cells x 7 sessions = **224**; overlap clusters (Jaccard >= 0.5, PRE entries) **8**, F_eff = **56**. Independent (cluster x session) PRE tests with n >= 100: 40; PRE-selected cell-sessions 1 = 1 independent (chance at 2.5% one-sided = about 1).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 1; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: 100%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 28 | 1 | 1 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 28 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 11 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 32 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 28 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 32 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C4b_ST10n7 | ASIA | 241 | 3.21 | 1890 | 2542 | 2.08 | 0.56 | 113 | 793 | 1627 | -2473 | 1347 | 1048 | 1242 | 2503 | -2473 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 645 | 6 |
| XT_C4b_ST10n10 | ASIA | 198 | 2.64 | 1971 | 2863 | 1.93 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 548 | 4 |
| XT_C4c_ST10n10 | ASIA | 198 | 2.64 | 1621 | 2578 | 1.76 | 0.59 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 284 | 4 |
| XT_C4c_ST10n7 | ASIA | 242 | 3.23 | 1307 | 2270 | 1.61 | 0.59 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 57.0 | 6 |
| XT_C4c_HM | ASIA | 610 | 8.13 | 623 | 1171 | 1.49 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -288 | 1 |
| XT_C4b_ST10n14 | LONDON | 283 | 3.77 | 1215 | 2657 | 1.28 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 357 | 5 |
| XT_C4b_ST10n10 | LONDON | 264 | 3.52 | 1048 | 2444 | 1.20 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 548 | 4 |
| XT_C4b_ST10n7 | LONDON | 253 | 3.37 | 1192 | 2854 | 1.17 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 645 | 6 |
| XT_C4c_EMA5 | NY-AM | 182 | 2.43 | 998 | 2530 | 1.10 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 259 | 0 |
| XT_C4b_ST | ASIA | 682 | 9.09 | 508 | 1343 | 1.06 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -161 | 3 |
| XT_C4b_EMA5 | NY | 301 | 4.01 | 645 | 2010 | 0.90 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 299 | 0 |
| XT_C3_ST10n14 | LONDON | 299 | 3.99 | 880 | 2751 | 0.90 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -104 | 5 |
| XT_C4c_ST10n14 | ASIA | 172 | 2.29 | 927 | 2925 | 0.89 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 140 | 5 |
| XT_C4b_HM | ASIA | 598 | 7.97 | 400 | 1321 | 0.85 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -384 | 1 |
| XT_C4b_ST10n14 | ASIA | 172 | 2.29 | 918 | 3121 | 0.82 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 357 | 5 |
| XT_C4a_ST10n7 | NY-AM | 199 | 2.65 | 754 | 2568 | 0.82 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -218 | 6 |
| XT_C4a_EMA5 | NY-AM | 164 | 2.19 | 728 | 2528 | 0.81 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -241 | 0 |
| XT_C4a_ST10n10 | ASIA | 198 | 2.64 | 787 | 2734 | 0.81 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -466 | 4 |
| XT_C4b_EMA5 | NY-PM | 132 | 1.76 | 797 | 2802 | 0.80 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 299 | 0 |
| XT_C4a_HM | ASIA | 597 | 7.96 | 370 | 1308 | 0.79 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -449 | 1 |
| XT_C3_ST10n7 | ASIA | 242 | 3.23 | 668 | 2445 | 0.77 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -109 | 6 |
| XT_C3_ST10n10 | LONDON | 278 | 3.71 | 751 | 2752 | 0.76 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -236 | 4 |
| XT_C3_ST10n14 | ASIA | 172 | 2.29 | 757 | 2774 | 0.76 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -104 | 5 |
| XT_C4a_ST10n7 | ASIA | 240 | 3.20 | 696 | 2574 | 0.76 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -218 | 6 |
| XT_C4c_ST | ASIA | 699 | 9.32 | 288 | 1113 | 0.72 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -281 | 3 |
| XT_C4c_EMA5 | ASIA | 249 | 3.32 | 462 | 1854 | 0.70 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 259 | 0 |
| XT_C4a_ST | ASIA | 675 | 9.00 | 333 | 1483 | 0.63 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -256 | 3 |
| XT_C4c_ST10n10 | NY-AM | 237 | 3.16 | 488 | 2211 | 0.62 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 284 | 4 |
| XT_C3_ST10n7 | LONDON | 265 | 3.53 | 586 | 2659 | 0.62 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -109 | 6 |
| XT_C4c_EMA5 | NY | 321 | 4.28 | 354 | 1672 | 0.59 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 259 | 0 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C4b_ST10n7 | ASIA | 241 | 3.21 | 1890 | 2542 | 2.08 | 0.56 | 113 | 793 | 1627 | -2473 | 1347 | 1048 | 1242 | 2503 | -2473 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 645 | 6 |
| XT_C4b_ST10n10 | ASIA | 198 | 2.64 | 1971 | 2863 | 1.93 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 548 | 4 |
| XT_C4c_HM | ASIA | 610 | 8.13 | 623 | 1171 | 1.49 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -288 | 1 |
| XT_C4b_ST10n14 | LONDON | 283 | 3.77 | 1215 | 2657 | 1.28 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 357 | 5 |
| XT_C4c_EMA5 | NY-AM | 182 | 2.43 | 998 | 2530 | 1.10 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 259 | 0 |
| XT_C4b_ST | ASIA | 682 | 9.09 | 508 | 1343 | 1.06 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -161 | 3 |
| XT_C4c_KEL3 | NY-AM | 775 | 10.3 | 219 | 1243 | 0.49 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -208 | 2 |
| XT_C4a_TB7 | NY-AM | 439 | 5.85 | -62.1 | 1718 | -0.10 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -342 | 7 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).


## 6. Notes
- Paired exit-vs-bracket tests (the source's object) are not repeated here; this report is the per-cell entry-session score of the exit-alternative trade streams. A cell shares its entries with the base bracket of the same stream, so cells cluster with each other and with the stream's base (Jaccard on PRE entries); read the cluster column.
- Fixed-bracket survivors: only rules with a fixed 60-pt stop and fixed target (C4 level targets vary per trade, R4_T15/T20 = 60/90 and 60/120 pt) are plain entry+bracket replay legs; trail/time/flip rules have dynamic exits.
