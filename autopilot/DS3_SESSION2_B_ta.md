# DS3_SESSION2_B_ta - T-A (D3A) entry-clock re-run and session scoring (10 trade-level cells)

Written 2026-10-28T21:03:56Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/ta/. Prereg l2vast/ds3/prereg/SB3_ta_prereg.md sha256 2dfb1cc35a4d601d022c1741731049aca62acb2814bcb49c81d796e31a8e0d49; PREHOLD autopilot/DS3_SESSION2_B_ta_PREHOLD.md sha256 c02d54a2ba2070e4ca58c8da65e32a609dc9215435d5528b3dbb6b7c044c781e (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
The generating engines are the struct48 sleeve engines (1-min NQ/ES; ORB-Asia on the 1-s path), whose per-trade outputs are the stored struct48/out/<cell>_trades.parquet. These were NOT re-simulated: the trade tables were taken from the engine's stored trade files (entry_time_et = the actual order time, e.g. 15:56 ET for the dip-buys, session 'CLOSE'), pnl = engine net_usd at the engine lots (1 lot dip-buy sleeves; ORB 14 lots), basis 1MIN-ENGINE / 1S-ENGINE (live cost 14.84 $/NQ lot RT incl. slippage as in the engine). Frequencies are very low (0.4-0.9 trades/wk for the dip-buys), so most cell-sessions cannot reach the n>=100 PRE rule.

Reproduction: per-exit-day sums of the stored trade rows equal the stored per-lot daily series out/T-A/<cell>.parquet exactly (max abs difference 0.0) for 10 of 10 trade-level cells (100%); the 12 other cells could not be reproduced and are listed in NOT_RERUNNABLE.md.

## 2. Multiplicity and counts
- Cells 10; F = cells x 7 sessions = **154**; overlap clusters (Jaccard >= 0.5, PRE entries) **6**, F_eff = **42**. Independent (cluster x session) PRE tests with n >= 100: 1; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 0).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 1 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TA_NQ_ON_none | CLOSE | 344 | 4.59 | 168 | 635 | 0.74 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 168 | 3 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TA_NQ_ON_none | CLOSE | 344 | 4.59 | 168 | 635 | 0.74 | 0.55 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 168 | 3 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).

