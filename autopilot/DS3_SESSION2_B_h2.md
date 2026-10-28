# DS3_SESSION2_B_h2 - H2 tape-trigger pullback entries entry-clock re-run and session scoring

Written 2026-10-28T21:08:18Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/h2/. Prereg l2vast/ds3/prereg/SB3_h2_prereg.md sha256 fe38d6009b1068d25ab12f75859a379c239a02cb3933fa99ab1d0bf4b7a312b0; PREHOLD autopilot/DS3_SESSION2_B_h2_PREHOLD.md sha256 8e26bd6ee9070c55bc667a76dc36240ee5ff4dfd8805f7dcd3473c2c4cd161ed (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original h2_run first stage (h2_core.assign trigger + pbx_ord.evaluate variant S1, kept rungs) without the random-in-regime placebos; each kept rung is a trade, entry time = entry minute bar (te_core MIN, END stamp as in the ledger), pnl = stored ptsE x $200 (10 lots; ptsE as computed by the source on the MAPPED conservative basis, costs inside), basis MAPPED-CONSERVATIVE. Fixed 60-pt-stop family for the f60 cells (T3 and SW exits): see survivors note.

Reproduction: the kept-rung entry bar indices and ptsE of all 24 cells equal the stored out/H2/h2_<cell>.pkl _trade vectors exactly (same count, same ei, allclose ptsE): 24/24 (100%).

## 2. Multiplicity and counts
- Cells 24; F = cells x 7 sessions = **168**; overlap clusters (Jaccard >= 0.5, PRE entries) **16**, F_eff = **112**. Independent (cluster x session) PRE tests with n >= 100: 71; PRE-selected cell-sessions 2 = 2 independent (chance at 2.5% one-sided = about 2).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 2, DEAD-IN-HOLD 0; alive cells 2, alive clusters 2. HOLD sign persistence of the selected list: 100%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 11 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 14 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 6 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 23 | 2 | 2 | 2 | 0 | 2 | H2_PB3_f60_T3_DRY | 2693 | 3395 |
| NY-PM | 12:00-15:00 | 22 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 24 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H2_PB3_f60_T3_DRY | NY-AM | 309 | 4.12 | 2693 | 3395 | 2.22 | 0.39 | 144 | 663 | 456 | 1647 | 852 | 987 | 3760 | 725 | 1647 | SESSION-CANDIDATE |  | BOF:not cleared | 296 | 4 |
| H2_PBS_f60_T3_SWR | NY-AM | 233 | 3.11 | 2839 | 3863 | 2.06 | 0.37 | 91.0 | 3872 | 3437 | 5087 | 1261 | 1355 | 3074 | 2743 | 5087 | SESSION-CANDIDATE |  | BOF:not cleared | 962 | 15 |
| H2_PBS_f60_SW_IMB | LONDON | 304 | 4.05 | 1358 | 2078 | 1.83 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 683 | 13 |
| H2_PBS_f60_SW_SWR | LONDON | 361 | 4.81 | 1359 | 2086 | 1.82 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 809 | 15 |
| H2_PB3_f60_T3_SWR | ASIA | 541 | 7.21 | 1320 | 2262 | 1.63 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 261 | 7 |
| H2_PBS_f60_T3_DFL10 | LONDON | 191 | 2.55 | 2291 | 4108 | 1.56 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 544 | 10 |
| H2_PBS_f60_T3_ABS | NY | 542 | 7.23 | 1097 | 2058 | 1.49 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1268 | 8 |
| H2_PBS_f60_SW_SWR | ASIA | 532 | 7.09 | 835 | 1585 | 1.48 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 809 | 15 |
| H2_PBS_f60_SW_ABS | NY-PM | 293 | 3.91 | 1105 | 2245 | 1.38 | 0.53 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 534 | 8 |
| H2_PBS_f60_T3_SWR | NY | 451 | 6.01 | 1290 | 2723 | 1.33 | 0.37 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 962 | 15 |
| H2_PBS_f60_T3_ABS | NY-PM | 201 | 2.68 | 1360 | 2916 | 1.31 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1268 | 8 |
| H2_PB3_f60_T3_DFL10 | ASIA | 437 | 5.83 | 1002 | 2403 | 1.17 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 313 | 2 |
| H2_PB3_f60_T3_DFL30 | NY | 856 | 11.4 | 677 | 1743 | 1.09 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 631 | 3 |
| H2_PBS_f60_T3_ABS | NY-AM | 341 | 4.55 | 942 | 2631 | 1.00 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1268 | 8 |
| H2_PBS_f60_SW_DFL10 | NY-PM | 313 | 4.17 | 797 | 2285 | 0.98 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 101 | 10 |
| H2_PB3_f60_T3_ABS | NY-AM | 548 | 7.31 | 766 | 2223 | 0.96 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 295 | 0 |
| H2_PB3_f60_T3_DFL30 | NY-PM | 314 | 4.19 | 1096 | 3232 | 0.95 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 631 | 3 |
| H2_PB3_f60_T3_IMB | NY-AM | 232 | 3.09 | 1293 | 3945 | 0.92 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 173 | 5 |
| H2_PB3_f60_T3_DFL10 | NY-PM | 322 | 4.29 | 795 | 2504 | 0.89 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 313 | 2 |
| H2_PBS_f60_T3_SWR | ASIA | 455 | 6.07 | 742 | 2406 | 0.86 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 962 | 15 |
| H2_PB3_f60_T3_DFL30 | LONDON | 238 | 3.17 | 1151 | 3940 | 0.82 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 631 | 3 |
| H2_PBS_f60_T3_SWR | LONDON | 178 | 2.37 | 1445 | 4984 | 0.81 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 962 | 15 |
| H2_PBS_f60_SW_IMB | ASIA | 372 | 4.96 | 531 | 1864 | 0.80 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 683 | 13 |
| H2_PB3_f60_T3_ABS | NY | 865 | 11.5 | 420 | 1612 | 0.73 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 295 | 0 |
| H2_PBS_f60_T3_DFL30 | NY | 464 | 6.19 | 538 | 2095 | 0.72 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 172 | 11 |
| H2_PBS_f60_SW_DRY | LONDON | 183 | 2.44 | 887 | 3506 | 0.71 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 739 | 12 |
| H2_PBS_f60_T3_DFL30 | NY-AM | 289 | 3.85 | 731 | 2906 | 0.70 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 172 | 11 |
| H2_PBS_f60_T3_DFL10 | NY | 499 | 6.65 | 556 | 2316 | 0.67 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 544 | 10 |
| H2_PBS_f60_SW_DFL30 | NY-PM | 231 | 3.08 | 657 | 2779 | 0.66 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -271 | 11 |
| H2_PB3_f60_T3_DRY | ASIA | 299 | 3.99 | 688 | 3003 | 0.64 | 0.29 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 296 | 4 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H2_PB3_f60_T3_DRY | NY-AM | 309 | 4.12 | 2693 | 3395 | 2.22 | 0.39 | 144 | 663 | 456 | 1647 | 852 | 987 | 3760 | 725 | 1647 | SESSION-CANDIDATE |  | BOF:not cleared | 296 | 4 |
| H2_PBS_f60_T3_SWR | NY-AM | 233 | 3.11 | 2839 | 3863 | 2.06 | 0.37 | 91.0 | 3872 | 3437 | 5087 | 1261 | 1355 | 3074 | 2743 | 5087 | SESSION-CANDIDATE |  | BOF:not cleared | 962 | 15 |
| H2_PBS_f60_SW_IMB | LONDON | 304 | 4.05 | 1358 | 2078 | 1.83 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 683 | 13 |
| H2_PB3_f60_T3_SWR | ASIA | 541 | 7.21 | 1320 | 2262 | 1.63 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 261 | 7 |
| H2_PBS_f60_T3_DFL10 | LONDON | 191 | 2.55 | 2291 | 4108 | 1.56 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 544 | 10 |
| H2_PBS_f60_T3_ABS | NY | 542 | 7.23 | 1097 | 2058 | 1.49 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1268 | 8 |
| H2_PB3_f60_T3_DFL10 | ASIA | 437 | 5.83 | 1002 | 2403 | 1.17 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 313 | 2 |
| H2_PB3_f60_T3_DFL30 | NY | 856 | 11.4 | 677 | 1743 | 1.09 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 631 | 3 |
| H2_PB3_f60_T3_ABS | NY-AM | 548 | 7.31 | 766 | 2223 | 0.96 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 295 | 0 |
| H2_PB3_f60_T3_IMB | NY-AM | 232 | 3.09 | 1293 | 3945 | 0.92 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 173 | 5 |
| H2_PBS_f60_T3_DFL30 | NY | 464 | 6.19 | 538 | 2095 | 0.72 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 172 | 11 |
| H2_PBS_f60_SW_DRY | LONDON | 183 | 2.44 | 887 | 3506 | 0.71 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 739 | 12 |
| H2_PB3_f60_T3_COMBO | NY | 911 | 12.1 | 303 | 1613 | 0.53 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 425 | 1 |
| H2_PBS_f60_SW_COMBO | NY-PM | 186 | 2.48 | 567 | 3541 | 0.45 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -48.2 | 9 |
| H2_PBS_f60_T3_LP | NY-AM | 106 | 1.41 | 714 | 4895 | 0.41 | 0.38 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -283 | 14 |
| H2_PB3_f60_T3_LP | NY-AM | 296 | 3.95 | 350 | 2808 | 0.35 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 105 | 6 |


## 5. Dead pooled, alive in a session
2 cell-sessions (2 cells, 2 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H2_PB3_f60_T3_DRY | NY-AM | 309 | 4.12 | 2693 | 3395 | 2.22 | 144 | 663 | 456 | 1647 | 852 | 987 | 3760 | 725 | 1647 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 296 | 4 |
| H2_PBS_f60_T3_SWR | NY-AM | 233 | 3.11 | 2839 | 3863 | 2.06 | 91.0 | 3872 | 3437 | 5087 | 1261 | 1355 | 3074 | 2743 | 5087 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 962 | 15 |

