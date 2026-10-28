# DS3_SESSION2_B_tef - T-E/T-F filters on the proxy NQ book entry-clock re-run and session scoring

Written 2026-10-28T21:03:02Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tef/. Prereg l2vast/ds3/prereg/SB3_tef_prereg.md sha256 18f6cd3893356459f85c5872283eb0bc6a57bd702ab056b3ac69354bb9ece7fe; PREHOLD autopilot/DS3_SESSION2_B_tef_PREHOLD.md sha256 5ca2317ca9bb61b32122e692f7aeca56238f762de5a2b0d82aed7dbfa40451fa (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original run_tef.py logic on out/def/te_pairs.pkl (the proxy NQ 5-min Supertrend book, 2 NQ, live-style cost, with entry date and entry minute stored in the book): a filter cell's trade table is the proxy-book trades the filter KEEPS (primary parameter), entry time = entry date + stored entry minute (ET), pnl = stored net $ at 2 NQ; TF3/TF4 are ES (4 contracts) close-to-close books entering at the 15:59 close. Basis MAPPED 5-min proxy book / 1-min ES close. Note: the cells are filters of one common book, so they are nearly the same trades (one cluster).

Reproduction: the daily filtered-book $ series of all 7 cells equals the stored out/TE|TF/<cell>_daily.parquet (rtol 1e-9): 7/7 (100%).

## 2. Multiplicity and counts
- Cells 7; F = cells x 7 sessions = **49**; overlap clusters (Jaccard >= 0.5, PRE entries) **3**, F_eff = **21**. Independent (cluster x session) PRE tests with n >= 100: 5; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 0).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 5 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 5 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 5 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 5 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 5 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE3_BREADTH_NY | NY-PM | 226 | 3.01 | 206 | 711 | 0.81 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -45.4 | 0 |
| TF1_FOMC_NY | NY-PM | 241 | 3.21 | 182 | 644 | 0.79 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -35.4 | 0 |
| TF2_CPI_LON | NY-PM | 254 | 3.39 | 136 | 648 | 0.59 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -53.9 | 0 |
| TE2_ZN_LON | NY-PM | 254 | 3.39 | 136 | 648 | 0.59 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -57.7 | 0 |
| TE1_BTC_ASIA | NY-PM | 254 | 3.39 | 136 | 648 | 0.59 | 0.46 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -35.4 | 0 |
| TF1_FOMC_NY | NY | 617 | 8.23 | 4.29 | 527 | 0.02 | 0.44 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -35.4 | 0 |
| TE1_BTC_ASIA | ASIA | 315 | 4.20 | 1.27 | 196 | 0.02 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -35.4 | 0 |
| TE3_BREADTH_NY | NY | 496 | 6.61 | 1.57 | 606 | 0.01 | 0.44 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -45.4 | 0 |
| TE1_BTC_ASIA | NY | 642 | 8.56 | -22.7 | 519 | -0.12 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -35.4 | 0 |
| TF2_CPI_LON | NY | 642 | 8.56 | -22.7 | 519 | -0.12 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -53.9 | 0 |
| TE2_ZN_LON | NY | 642 | 8.56 | -22.7 | 519 | -0.12 | 0.43 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -57.7 | 0 |
| TE1_BTC_ASIA | LONDON | 665 | 8.87 | -24.5 | 206 | -0.33 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -35.4 | 0 |
| TF2_CPI_LON | LONDON | 645 | 8.60 | -26.7 | 217 | -0.34 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -53.9 | 0 |
| TE3_BREADTH_NY | LONDON | 673 | 8.97 | -25.5 | 203 | -0.35 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -45.4 | 0 |
| TF1_FOMC_NY | LONDON | 673 | 8.97 | -25.5 | 203 | -0.35 | 0.39 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -35.4 | 0 |
| TE2_ZN_LON | LONDON | 366 | 4.88 | -36.6 | 252 | -0.41 | 0.40 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -57.7 | 0 |
| TF1_FOMC_NY | NY-AM | 376 | 5.01 | -109 | 696 | -0.44 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -35.4 | 0 |
| TF2_CPI_LON | NY-AM | 388 | 5.17 | -127 | 682 | -0.52 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -53.9 | 0 |
| TE2_ZN_LON | NY-AM | 388 | 5.17 | -127 | 682 | -0.52 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -57.7 | 0 |
| TE1_BTC_ASIA | NY-AM | 388 | 5.17 | -127 | 682 | -0.52 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -35.4 | 0 |
| TE3_BREADTH_NY | NY-AM | 270 | 3.60 | -170 | 826 | -0.58 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -45.4 | 0 |
| TE3_BREADTH_NY | ASIA | 559 | 7.45 | -69.0 | 158 | -1.23 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -45.4 | 0 |
| TE2_ZN_LON | ASIA | 559 | 7.45 | -69.0 | 158 | -1.23 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -57.7 | 0 |
| TF2_CPI_LON | ASIA | 559 | 7.45 | -69.0 | 158 | -1.23 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -53.9 | 0 |
| TF1_FOMC_NY | ASIA | 559 | 7.45 | -69.0 | 158 | -1.23 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -35.4 | 0 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE3_BREADTH_NY | NY-PM | 226 | 3.01 | 206 | 711 | 0.81 | 0.47 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -45.4 | 0 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).

