# REDO_ZONES2 - ZONES-2 (1,455 rows) and ZONES-2 ADDENDUM (65 rows) re-scored on the new windows (D3, 2026-11-01 ~17:40Z)

Research only. Re-read, no re-selection. Frozen definitions (zones2/zl.py, za_lib.py unchanged; code in l2vast/ds3/code/redo_zones2/). No PASS claims; the set is post-hoc-selected (LEAD, shadow) as before.

## 1. Coverage: 1,520 / 1,520 ledger rows extended and TIED (100%)
| program | ledger rows | extended | tied (5 old windows, 1e-6) | stack tied | not extendable |
|---|---|---|---|---|---|
| ZONES-2 | 1,455 | 1,455 | 1,455 | n/a (rows carry pts per signal) | 0 |
| ZONES-2 ADDENDUM | 65 | 65 | 65 | 65 (L3M research and live $/wk at 1e-6; note L6M/HOLD ints) | 0 |
Tie-out = the redo engine on the OLD windows reproduces the stored L3M(old 20251106..20260206), L6M, HOLD, PRE and X' of every row at 1e-6 (all 5 windows x 1,520 rows). Not extended (not in the old ledger, lowest priority, not done): 254 ZONES-2 and 13 ADDENDUM non-ledger cells (incl. tc / r30 / lid cell kinds and rows with no stored value to tie).

## 2. Streams needed and what was built (poi_store_redo)
The 1,520 rows depend on exactly 11 streams (rows by stream: PDX|day|M 186, MAS|ich_kijun|1h 165, PIV|cam_H3|rth 158, CRT|M|4h 143, MAS|kc_up|4h 132, FIB|ote705_up|15m 127, PRF|hvn0|sw1h 79, FIB|ote62_up|15m 76, FIB|ote79_up|15m 58, PRF|lvn1|sw1h 47, PRF|vah|sw15 19, plus the sets SET/S8/S11/S3 and only:/loo: controls built from them). REDO-1 had 8; D3 built the 3 missing: **PRF|lvn1|sw1h (4,029 POIs), PRF|vah|sw15 (22,552), PRF|hvn0|sw1h (5,623)** with the unchanged poi_adapt.adapt_profile logic on REDO-4B's out/confirm_redo/streams/cfa1__* (new files out/poi_store_redo/streams/PRF|...parquet). Store used by the engine: out/poi_store_redo/z2/ (features.npy 11 x 66,133 x 8, index.csv, trades.parquet, streams/ symlinks, build.log, stream_tie.txt, audit.txt). The other ~678 streams of the old store and the rsim arrays are NOT built (no ZONES-2 row reads them; ZONES-3 will need its own).
Tie-out: (a) old trades (44,370) x 11 streams x 8 channels: 3,904,560 feature cells, 0 mismatches; (b) stream rows: old rows are present unchanged in the new streams (ek, lo, hi, dr identical; `end` identical wherever the old end was finite; 0 old never-touched POIs touched later except 1 PIV|cam_H3|rth; `cap` differs on the single last open POI of 7 streams = real extension). Appending 8 months of data changed no old row = builders are causal. (c) Causality audit: 100 random trades (70 new-period, 30 old) x 11 streams, ahead-fresh and mitigated recomputed independently by numpy from the stream rows: 2,200 cells, 0 mismatches; every returned POI has ek <= kin, untouched and uncapped at the signal second (0 leaks).

## 3. Method
zl.simulate / aggregate logic on the redo trade set (66,133 trades, label days 20230403..20261030; 21,763 new), bases MKT/SPL, N basis, gain per signal = rule minus base, all signals in the denominator, windows from code/cap/windows.py (ISO-week ratio estimator, MDE = 2.8 SE; n = signals). Addendum stack = lock engine (6 books) daily delta rule-base at research and live lots (za_lib), $ per calendar week, MDE from weekly sums. PRE and X' recomputed (equal to stored). Per-contract kept (ppc_*) = rule pts per rule lot minus base pts per base lot.

## 4. Outputs (out/recent_wins/redo/zones2/ ; vec copies D3__*.parquet also in out/recent_wins/redo/vec/ for the assembler)
* zones2_windows.csv: one row per ledger row: L1M L2M L3M L6M HOLD MID PRE X', MDE and n per window, ppc_*, fires_*, addendum stack_res_* / stack_live_* with MDE, old_L3M_to_Feb06 beside, old L6M/HOLD, tie status, session ALL.
* D3__ZONES-2.parquet, D3__ZONES-2-ADDENDUM.parquet (rkey, ld, usd [research stack delta, addendum], pts, n, fires, usd_live), vec_pts.parquet / vec_stack.parquet (details), tie_pts.csv, tie_stack.csv, pend_pts.csv (empty).
* Run logs out/recent_wins/redo/zones2_run_pts.log, zones2_run_stack.log.

## 5. First read (a view, not a selection)
Rows positive in both L3M and L6M on the new windows: 474 of 1,520 (ZONES-2 443 of 1,455, ADDENDUM 31 of 65). Headline cell SET fresh D = 20 pts skip, 70/30 base: old L3M +0.47 -> L1M +0.36, L2M +0.55, L3M +0.28 (MDE 0.66), L6M -0.16, HOLD +0.01, MID +0.02 (PRE +0.28, X' +0.45 unchanged); re-target: L3M +0.21, L6M -0.13, HOLD +0.01. So the set's recent months are positive but the new L6M/HOLD/MID are flat to negative, all inside MDE; consistent with the pre-registered verdict (LEAD, shadow only, fails the forward chain).
