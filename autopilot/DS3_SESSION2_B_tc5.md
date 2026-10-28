# DS3_SESSION2_B_tc5 - T-C overnight carry C5 (TC5)

Written 2026-10-28T21:04:08Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tc5/. Prereg l2vast/ds3/prereg/SB3_tc5_prereg.md sha256 2ad76eca5b46a12eebeb0624965a367f574361b5d485debd67ba194b914799af; PREHOLD autopilot/DS3_SESSION2_B_tc5_PREHOLD.md sha256 4d06405c6ed9b3a868cdd31c23fe18f749cf980e585bc0daf6404512277b840f (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original D3XT assembly (tcx/dc_score.load_all + dc_asm.sequence/pts_cm/run_locks on the stored nominal-exit table dc_res*.parquet and the direct L2 replay fills R_*/X_* in /mnt/l2/l2vast/ds3_tcx): for each (stream, rule) cell the base entries are sequenced with the busy-skip, exit prices are the direct L2 replay fills (stop exits XJ stop-join, market exits 10-lot market, target exits limit at level), entry = S10x1 gap-2 s direct replay; missing fills fall back to nominal -/+ slip as in the source. Entry time = ET of the entry bar (dc_asm.et, end-stamp convention of the ledger). pnl = (direct pts - 4.84/20) x $200 (10 lots), unlocked per-trade; columns exec/pnl_lock give the lock-engine fill flag and net $ for the replay step. Basis DIRECT-L2-EXITS (the strongest basis in the repository). Trades after 2026-02-06 are dropped at load; the engine run itself covered the full stored span (the replay raw ends 2026-10-09) and was compared only up to 2026-02-06.

Reproduction: the regenerated lock-engine daily $ series of all 24 cells equals the stored _daily_r in out/tcx/score_*_final_v.pkl (rtol 1e-6, label days up to 2026-02-06) and the number of taken trades equals the stored n_taken_r: 24/24 (100%, all cells). out/sb3/tcx_repro.csv.

## 2. Multiplicity and counts
- Cells 24; F = cells x 7 sessions = **168**; overlap clusters (Jaccard >= 0.5, PRE entries) **8**, F_eff = **56**. Independent (cluster x session) PRE tests with n >= 100: 40; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 1).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 21 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 21 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 9 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 24 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 21 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 24 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C5A_ST10n10 | ASIA | 198 | 2.64 | 1688 | 2554 | 1.85 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 188 | 4 |
| XT_C5B_ST10n10 | ASIA | 198 | 2.64 | 1688 | 2554 | 1.85 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 189 | 4 |
| XT_C5C_ST10n7 | ASIA | 229 | 3.05 | 1472 | 2312 | 1.78 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 297 | 6 |
| XT_C5C_ST10n10 | ASIA | 188 | 2.51 | 1626 | 2683 | 1.70 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 132 | 4 |
| XT_C5A_ST10n7 | ASIA | 242 | 3.23 | 1372 | 2277 | 1.69 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 301 | 6 |
| XT_C5B_ST10n7 | ASIA | 242 | 3.23 | 1372 | 2277 | 1.69 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 302 | 6 |
| XT_C5C_EMA5 | NY-AM | 183 | 2.44 | 1093 | 2354 | 1.30 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 284 | 0 |
| XT_C5C_ST | ASIA | 639 | 8.52 | 592 | 1364 | 1.21 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -170 | 3 |
| XT_C5B_EMA5 | NY-AM | 183 | 2.44 | 949 | 2274 | 1.17 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 199 | 0 |
| XT_C5B_ST10n14 | ASIA | 172 | 2.29 | 1143 | 2833 | 1.13 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 196 | 5 |
| XT_C5A_ST10n14 | ASIA | 172 | 2.29 | 1143 | 2833 | 1.13 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 198 | 5 |
| XT_C5A_EMA5 | NY-AM | 183 | 2.44 | 891 | 2300 | 1.08 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 209 | 0 |
| XT_C5C_EMA5 | NY | 322 | 4.29 | 637 | 1689 | 1.06 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 284 | 0 |
| XT_C5B_ST | ASIA | 712 | 9.49 | 383 | 1185 | 0.90 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -226 | 3 |
| XT_C5A_HM | ASIA | 622 | 8.29 | 364 | 1138 | 0.90 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -309 | 1 |
| XT_C5C_ST10n14 | ASIA | 163 | 2.17 | 963 | 3039 | 0.89 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 213 | 5 |
| XT_C5A_ST | ASIA | 712 | 9.49 | 371 | 1190 | 0.87 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -239 | 3 |
| XT_C5B_HM | ASIA | 622 | 8.29 | 351 | 1140 | 0.86 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -286 | 1 |
| XT_C5A_EMA5 | ASIA | 249 | 3.32 | 585 | 1980 | 0.83 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 209 | 0 |
| XT_C5B_EMA5 | ASIA | 249 | 3.32 | 585 | 1980 | 0.83 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 199 | 0 |
| XT_C5C_EMA5 | ASIA | 233 | 3.11 | 603 | 2064 | 0.82 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 284 | 0 |
| XT_C5B_EMA5 | NY | 323 | 4.31 | 398 | 1639 | 0.68 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 199 | 0 |
| XT_C5A_EMA5 | NY | 323 | 4.31 | 399 | 1666 | 0.67 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 209 | 0 |
| XT_C5C_ST10n14 | LONDON | 297 | 3.96 | 530 | 2280 | 0.65 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 213 | 5 |
| XT_C5C_ST10n7 | NY-AM | 219 | 2.92 | 497 | 2185 | 0.64 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 297 | 6 |
| XT_C5C_HM | ASIA | 557 | 7.43 | 264 | 1217 | 0.61 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -357 | 1 |
| XT_C5A_ST10n14 | LONDON | 302 | 4.03 | 464 | 2231 | 0.58 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 198 | 5 |
| XT_C5B_ST10n14 | LONDON | 302 | 4.03 | 436 | 2226 | 0.55 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 196 | 5 |
| XT_C5B_ST10n7 | NY-AM | 220 | 2.93 | 408 | 2117 | 0.54 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 302 | 6 |
| XT_C5A_ST10n7 | NY-AM | 220 | 2.93 | 362 | 2110 | 0.48 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 301 | 6 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C5A_ST10n10 | ASIA | 198 | 2.64 | 1688 | 2554 | 1.85 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 188 | 4 |
| XT_C5C_ST10n7 | ASIA | 229 | 3.05 | 1472 | 2312 | 1.78 | 0.58 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 297 | 6 |
| XT_C5C_EMA5 | NY-AM | 183 | 2.44 | 1093 | 2354 | 1.30 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 284 | 0 |
| XT_C5C_ST | ASIA | 639 | 8.52 | 592 | 1364 | 1.21 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -170 | 3 |
| XT_C5B_ST10n14 | ASIA | 172 | 2.29 | 1143 | 2833 | 1.13 | 0.56 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 196 | 5 |
| XT_C5A_HM | ASIA | 622 | 8.29 | 364 | 1138 | 0.90 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -309 | 1 |
| XT_C5A_KEL3 | ASIA | 779 | 10.4 | 181 | 1243 | 0.41 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -228 | 2 |
| XT_C5C_TB7 | NY | 521 | 6.95 | -206 | 1702 | -0.34 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -206 | 7 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).


## 6. Notes
- Paired exit-vs-bracket tests (the source's object) are not repeated here; this report is the per-cell entry-session score of the exit-alternative trade streams. A cell shares its entries with the base bracket of the same stream, so cells cluster with each other and with the stream's base (Jaccard on PRE entries); read the cluster column.
- Fixed-bracket survivors: only rules with a fixed 60-pt stop and fixed target (C4 level targets vary per trade, R4_T15/T20 = 60/90 and 60/120 pt) are plain entry+bracket replay legs; trail/time/flip rules have dynamic exits.
