# DS3_SESSION2_B_td - T-D mean reversion entry-clock re-run and session scoring

Written 2026-10-28T21:02:11Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/td/. Prereg l2vast/ds3/prereg/SB3_td_prereg.md sha256 46f6f0dfdb9e23d2f392f1f7bad0e4b469519dcb12cc2af6d4742e57d20f85cb; PREHOLD autopilot/DS3_SESSION2_B_td_PREHOLD.md sha256 439580648917b354e19d1b6872e677cfa3aaab6005d47f140c99474eee6e7eff (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original sims (def_td.c2o/gapfade/zn_vwap/rv_zn_es/basis on def_lib.Sym 1-min back-adjusted series, same parameters as run_td.py) with ONE added field, the entry bar's minute of day (copy def_td_t.py; no logic changed). Entry time = entry date + that minute (ET); TD1/TD2 enter at the 15:59 bar close (16:00), TD6 at the 15:59 close. pnl = stored net $ (contracts x pts x point value - proxy cost model with slip ticks/side and proxy ES fee), lots = contracts, basis MAPPED 1-min proxy-cost (not NQ lots; instruments ES, YM, NQ, ZN). Two-instrument cells (TD6, TD7) are one combined trade with the side of the first leg.

Reproduction: pnl, label day and trade count of all 7 cells equal the stored out/TD/trades.pkl rows exactly: 7/7 (100%). out/sb3/td/repro.csv.

## 2. Multiplicity and counts
- Cells 7; F = cells x 7 sessions = **49**; overlap clusters (Jaccard >= 0.5, PRE entries) **5**, F_eff = **35**. Independent (cluster x session) PRE tests with n >= 100: 8; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 0).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 4 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 1 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 2 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 4 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TD5_NQ_GAPFADE | NY-AM | 188 | 2.51 | 419 | 896 | 1.31 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 419 | 2 |
| TD5_NQ_GAPFADE | NY | 188 | 2.51 | 419 | 896 | 1.31 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 419 | 2 |
| TD4_ES_GAPFADE | NY | 193 | 2.57 | 406 | 1043 | 1.09 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 406 | 2 |
| TD4_ES_GAPFADE | NY-AM | 193 | 2.57 | 406 | 1043 | 1.09 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 406 | 2 |
| TD1_ES_C2O | CLOSE | 147 | 1.96 | 170 | 2133 | 0.22 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 170 | 0 |
| TD2_YM_C2O | CLOSE | 161 | 2.15 | -669 | 2061 | -0.91 | 0.51 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -669 | 0 |
| TD7_NQ_ES_BASIS | NY-AM | 216 | 2.88 | -179 | 282 | -1.78 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -191 | 4 |
| TD7_NQ_ES_BASIS | NY-PM | 153 | 2.04 | -193 | 251 | -2.16 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -191 | 4 |
| TD7_NQ_ES_BASIS | NY | 369 | 4.92 | -185 | 184 | -2.81 | 0.44 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -191 | 4 |
| TD3_ZN_VWAP | NY-AM | 187 | 2.49 | -380 | 269 | -3.96 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -373 | 1 |
| TD3_ZN_VWAP | NY | 261 | 3.48 | -389 | 208 | -5.24 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -373 | 1 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TD5_NQ_GAPFADE | NY-AM | 188 | 2.51 | 419 | 896 | 1.31 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 419 | 2 |
| TD1_ES_C2O | CLOSE | 147 | 1.96 | 170 | 2133 | 0.22 | 0.57 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 170 | 0 |
| TD7_NQ_ES_BASIS | NY-AM | 216 | 2.88 | -179 | 282 | -1.78 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -191 | 4 |
| TD3_ZN_VWAP | NY-AM | 187 | 2.49 | -380 | 269 | -3.96 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -373 | 1 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).

