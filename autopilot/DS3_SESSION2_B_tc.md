# DS3_SESSION2_B_tc - T-C CTA hourly/daily (TC) entry-clock re-run and session scoring

Written 2026-10-28T21:03:53Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/tc/. Prereg l2vast/ds3/prereg/SB3_tc_prereg.md sha256 603db80d64d60ea1b8f063e716a89717ac7b76e2c609ddb3b5e096fb866cb2f4; PREHOLD autopilot/DS3_SESSION2_B_tc_PREHOLD.md sha256 73f963eb1b64e15116e13bd4601c9e1a7243d514791ca1082f5c60950c39d28c (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run with a trade-level copy of tc_engine.sim (sim2: identical arithmetic, per-trade accounting) over the original candidate signals, the original monthly WF selection (tc_engine.wf_select) and the original lots series; each trade segment = bars of one candidate trade falling in the months where that candidate is selected; entry time = open of the entry bar (H1: the hour start in ET; D1: the 18:00 ET label-day open), pnl = sum of bar pnl x point value x lots(day) (back-adjusted 1-contract points, equal-risk lots of $1,000/day), costs inside (1 tick/side + commission proxy, 1 extra tick on stop exits). Basis MAPPED-1MIN-NEXT-OPEN (source's own: fills at next bar open on the 1-min continuous, no L2). Segments of a trade that was already open when its candidate became selected are kept as trades (their entry time = first selected bar) so that the daily series is reproduced exactly; monthly switch costs are not attached to any trade.

Reproduction: for the 10 markets x 5 selections (all-9, ST, DON, TSM at H1; all-9 at D1) = 50 series, the sum of regenerated trade pnl by label day plus the monthly switch cost equals the stored out/TC/mk_<sym>_<hz>.parquet p1/pST/pDON/pTSM daily series (rtol 1e-6): 50/50 (100%); basket cells are sums of those series by construction (build() in tc_score). Trade counts: regenerated trade segments are 1-20% above the stored entry counts because of the carried-in segments described above. out/sb3/tc/repro_markets.csv.

## 2. Multiplicity and counts
- Cells 28; F = cells x 7 sessions = **196**; overlap clusters (Jaccard >= 0.5, PRE entries) **25**, F_eff = **175**. Independent (cluster x session) PRE tests with n >= 100: 17; PRE-selected cell-sessions 0 = 0 independent (chance at 2.5% one-sided = about 0).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 0, DEAD-IN-HOLD 0; alive cells 0, alive clusters 0. HOLD sign persistence of the selected list: nan%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 6 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| LONDON | 02:00-08:30 | 5 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 4 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-PM | 12:00-15:00 | 4 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 1 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 5 | 0 | 0 | 0 | 0 | 0 | - |  |  |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TC_FAM_ST_H1 | LONDON | 201 | 2.68 | 189 | 306 | 1.73 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 40.2 | 11 |
| TC_FAM_ST_H1 | NY-AM | 173 | 2.31 | 70.8 | 313 | 0.63 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 40.2 | 11 |
| TC_B_H1 | ASIA | 184 | 2.45 | 21.2 | 283 | 0.21 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -8.02 | 4 |
| TC_FAM_ST_H1 | ASIA | 173 | 2.31 | 10.7 | 306 | 0.10 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 40.2 | 11 |
| TC_X_H1 | LONDON | 101 | 1.35 | 7.80 | 323 | 0.07 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -68.1 | 4 |
| TC_FAM_TSM_H1 | ASIA | 416 | 5.55 | -2.27 | 119 | -0.05 | 0.29 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -27.5 | 12 |
| TC_B_H1 | LONDON | 163 | 2.17 | -12.9 | 210 | -0.17 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -8.02 | 4 |
| TC_B_ALL | LONDON | 163 | 2.17 | -12.9 | 210 | -0.17 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -38.8 | 4 |
| TC_FAM_TSM_H1 | CLOSE | 146 | 1.95 | -16.4 | 163 | -0.28 | 0.34 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -27.5 | 12 |
| TC_FAM_ST_H1 | NY | 314 | 4.19 | -27.7 | 215 | -0.36 | 0.36 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | 40.2 | 11 |
| TC_B_ALL | ASIA | 315 | 4.20 | -70.9 | 417 | -0.48 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -38.8 | 4 |
| TC_B_D1 | ASIA | 131 | 1.75 | -200 | 898 | -0.62 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -200 | 5 |
| TC_B_H1 | NY-PM | 120 | 1.60 | -76.0 | 254 | -0.84 | 0.29 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -8.02 | 4 |
| TC_B_ALL | NY-PM | 120 | 1.60 | -76.0 | 254 | -0.84 | 0.29 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -38.8 | 4 |
| TC_FAM_TSM_H1 | LONDON | 395 | 5.27 | -33.1 | 85.5 | -1.08 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -27.5 | 12 |
| TC_X_H1 | ASIA | 120 | 1.60 | -100 | 246 | -1.14 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -68.1 | 4 |
| TC_FAM_TSM_H1 | NY-AM | 181 | 2.41 | -60.7 | 142 | -1.20 | 0.28 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -27.5 | 12 |
| TC_FAM_TSM_H1 | NY-PM | 201 | 2.68 | -50.6 | 104 | -1.36 | 0.32 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -27.5 | 12 |
| TC_B_ALL | NY | 230 | 3.07 | -94.3 | 173 | -1.52 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -38.8 | 4 |
| TC_B_H1 | NY | 230 | 3.07 | -94.3 | 173 | -1.52 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -8.02 | 4 |
| TC_B_ALL | NY-AM | 110 | 1.47 | -114 | 205 | -1.56 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -38.8 | 4 |
| TC_B_H1 | NY-AM | 110 | 1.47 | -114 | 205 | -1.56 | 0.33 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -8.02 | 4 |
| TC_FAM_ST_H1 | NY-PM | 141 | 1.88 | -149 | 239 | -1.74 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | 40.2 | 11 |
| TC_FAM_TSM_H1 | NY | 382 | 5.09 | -55.4 | 85.8 | -1.81 | 0.30 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -27.5 | 12 |
| TC_X_H1 | NY | 128 | 1.71 | -150 | 213 | -1.97 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -68.1 | 4 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TC_FAM_ST_H1 | LONDON | 201 | 2.68 | 189 | 306 | 1.73 | 0.42 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | 40.2 | 11 |
| TC_B_H1 | ASIA | 184 | 2.45 | 21.2 | 283 | 0.21 | 0.31 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 |  | -8.02 | 4 |
| TC_FAM_TSM_H1 | ASIA | 416 | 5.55 | -2.27 | 119 | -0.05 | 0.29 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -27.5 | 12 |
| TC_B_D1 | ASIA | 131 | 1.75 | -200 | 898 | -0.62 | 0.35 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 |  | -200 | 5 |


## 5. Dead pooled, alive in a session
None (no cell-session is alive after HOLD with a DEAD label or pooled PRE mean <= 0).


## 6. Notes
- Trades per week are small (0.1-2 per market-horizon; baskets up to 19), so single-market cells cannot reach n >= 100 PRE trades in one session; only baskets can.
