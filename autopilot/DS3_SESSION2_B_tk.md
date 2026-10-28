# DS3_SESSION2_B_tk - T-K intraday momentum entry-clock re-run and session scoring

Written 2026-10-28T21:00:20Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tk/. Prereg l2vast/ds3/prereg/SB3_tk_prereg.md sha256 0ac49d555e68f6787d336c22884c7eb7e845b4e7a24b082f8b32150a9613eb6a; PREHOLD autopilot/DS3_SESSION2_B_tk_PREHOLD.md sha256 6920d7ef343ec1f8dd46d7415970acc52d768089b19b53b5620aaf6e43cb8a89 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original code (tk_run.feats/daily_pnl/build/cell_series with th_engine.Panel risk-parity lots, 1x cost: tick + half commission per side + 1 extra tick): one trade per market-day; entry time = fixed session clock in ET (D1 = session end minus 30 min, D2 = session open; per-market session table SES in tk_run), pnl = lots x (sign x gain x point value - cost) from the original daily_pnl, basis MAPPED daily open/close prints (no intrabar path). Trade side is not stored in the daily engine and is written as +1 (it only enters the cluster-overlap key). Different instruments, so $ are per-market risk-parity $1,000/day style, not NQ lots.

Reproduction: the daily $ series and trade counts of all 19 cells equal the stored out/TK/<cell>_daily.parquet (rtol 1e-6): 19/19 (100%, all cells). out/sb3/tk/repro.csv.

## 2. Multiplicity and counts
- Cells 19; F = cells x 7 sessions = **133**; overlap clusters (Jaccard >= 0.5, PRE entries) **10**, F_eff = **70**. Independent (cluster x session) PRE tests with n >= 100: 22; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 1).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 7 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 3 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 4 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 7 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 5 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 10 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TK_GC_D2 | LONDON | 355 | 4.73 | 11.7 | 53.5 | 0.61 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 11.7 | 1 |
| TK_ES_D2 | NY-AM | 346 | 4.61 | -13.3 | 79.9 | -0.47 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -13.3 | 7 |
| TK_ES_D2 | NY | 346 | 4.61 | -13.3 | 79.9 | -0.47 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -13.3 | 7 |
| TK_6E_D2 | LONDON | 324 | 4.32 | -13.3 | 68.9 | -0.54 | 0.49 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -13.3 | 1 |
| TK_GC_D1 | NY | 356 | 4.75 | -8.04 | 31.2 | -0.72 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -8.04 | 8 |
| TK_GC_D1 | NY-PM | 356 | 4.75 | -8.04 | 31.2 | -0.72 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -8.04 | 8 |
| TK_YM_D1 | CLOSE | 347 | 4.63 | -20.9 | 46.3 | -1.27 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -20.9 | 6 |
| TK_ALL8_BOTH | NY-AM | 693 | 9.24 | -37.6 | 72.8 | -1.44 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -60.8 | 2 |
| TK_ALL8_D2 | NY | 693 | 9.24 | -37.6 | 72.8 | -1.44 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -61.8 | 3 |
| TK_ALL8_D2 | NY-AM | 693 | 9.24 | -37.6 | 72.8 | -1.44 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -61.8 | 3 |
| TK_ES_D1 | CLOSE | 348 | 4.64 | -32.3 | 46.8 | -1.93 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -32.3 | 6 |
| TK_YM_D2 | NY | 347 | 4.63 | -61.8 | 81.2 | -2.13 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -61.8 | 7 |
| TK_YM_D2 | NY-AM | 347 | 4.63 | -61.8 | 81.2 | -2.13 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -61.8 | 7 |
| TK_ZF_D2 | LONDON | 306 | 4.08 | -80.5 | 105 | -2.14 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -80.5 | 1 |
| TK_ALL8_BOTH | PREOPEN | 359 | 4.79 | -59.1 | 75.1 | -2.20 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -60.8 | 2 |
| TK_CL_D2 | PREOPEN | 359 | 4.79 | -59.1 | 75.1 | -2.20 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -59.1 | 5 |
| TK_ALL8_D2 | PREOPEN | 359 | 4.79 | -59.1 | 75.1 | -2.20 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -61.8 | 3 |
| TK_CL_D1 | NY-PM | 358 | 4.77 | -24.8 | 26.0 | -2.67 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -24.8 | 4 |
| TK_CL_D1 | NY | 358 | 4.77 | -24.8 | 26.0 | -2.67 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -24.8 | 4 |
| TK_ALL8_BOTH | CLOSE | 1033 | 13.8 | -31.3 | 26.4 | -3.33 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -60.8 | 2 |
| TK_ALL8_D1 | CLOSE | 1033 | 13.8 | -31.3 | 26.4 | -3.33 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -59.7 | 2 |
| TK_ZN_D2 | LONDON | 294 | 3.92 | -131 | 102 | -3.58 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -131 | 1 |
| TK_ALL8_D2 | LONDON | 1572 | 21.0 | -73.1 | 52.7 | -3.89 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -61.8 | 3 |
| TK_ALL8_BOTH | LONDON | 1572 | 21.0 | -73.1 | 52.7 | -3.89 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -60.8 | 2 |
| TK_ZB_D2 | LONDON | 293 | 3.91 | -177 | 101 | -4.89 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -177 | 1 |
| TK_ALL8_BOTH | NY | 2382 | 31.8 | -65.6 | 23.6 | -7.79 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -60.8 | 2 |
| TK_6E_D1 | CLOSE | 338 | 4.51 | -40.9 | 13.5 | -8.47 | 0.25 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -40.9 | 0 |
| TK_ZF_D1 | NY | 327 | 4.36 | -102 | 25.8 | -11.0 | 0.18 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -102 | 9 |
| TK_ZF_D1 | NY-PM | 327 | 4.36 | -102 | 25.8 | -11.0 | 0.18 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -102 | 9 |
| TK_ALL8_BOTH | NY-PM | 1689 | 22.5 | -77.1 | 16.4 | -13.1 | 0.27 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -60.8 | 2 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TK_GC_D2 | LONDON | 355 | 4.73 | 11.7 | 53.5 | 0.61 | 0.52 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 11.7 | 1 |
| TK_ES_D2 | NY-AM | 346 | 4.61 | -13.3 | 79.9 | -0.47 | 0.50 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -13.3 | 7 |
| TK_GC_D1 | NY | 356 | 4.75 | -8.04 | 31.2 | -0.72 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -8.04 | 8 |
| TK_YM_D1 | CLOSE | 347 | 4.63 | -20.9 | 46.3 | -1.27 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -20.9 | 6 |
| TK_ALL8_BOTH | NY-AM | 693 | 9.24 | -37.6 | 72.8 | -1.44 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -60.8 | 2 |
| TK_ALL8_D2 | NY | 693 | 9.24 | -37.6 | 72.8 | -1.44 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -61.8 | 3 |
| TK_CL_D2 | PREOPEN | 359 | 4.79 | -59.1 | 75.1 | -2.20 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -59.1 | 5 |
| TK_CL_D1 | NY-PM | 358 | 4.77 | -24.8 | 26.0 | -2.67 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -24.8 | 4 |
| TK_6E_D1 | CLOSE | 338 | 4.51 | -40.9 | 13.5 | -8.47 | 0.25 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -40.9 | 0 |
| TK_ZF_D1 | NY | 327 | 4.36 | -102 | 25.8 | -11.0 | 0.18 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -102 | 9 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).

