# REDO_TAIL2 (TAIL-2, 2026-11-01 ~21:55Z). Cap 2026-10-31, last label day 20261030.
| row | ledger rows | status | detail |
|---|---|---|---|
| ADDUW B1 | 5 (7 rkeys incl. 2 non-ledger) | EXTENDED, TIED | Program's own grid (D5S au_grid_redo.py, ADDUW_BASIS=B1, REDO setup) run for cells 5,266,509,941,1373 + base 1728; STACK ci=1022 already in grid_B1. Tie on L6M/HOLD/PRE/X' (tol max(1, 1e-4 rel), same as B2): 7/7. Files vec/T2__ADDUW-B1.parquet, T2__tie_, T2__pend_. Code code/recent_wins_redo/T2/adduw_b1_vec.py |
| FIRST-HOUR-DELTA | 4 | EXTENDED (alias), 3 TIED, 1 flagged | The 4 rows are the same STACK6 e.fhd cells as EINT2 (identical stored L3M usd, L6M, HOLD, PRE, X'), so the vector is the REDO EINT2 vector (C__EINT2) re-keyed. Old-L3M usd rel diff 6e-8, 7e-7, 6e-7, and e.fhd.c0.half 2.9e-6 (abs $0.009; flagged, not bit-exact). Vector starts 20251101 so only the L3M window is retested here. Files vec/T2__FIRST-HOUR-DELTA.*; code .../T2/fhd_alias.py |
| ENSM | 19 | CANNOT EXTEND (by deadline) | see T2__pend_ENSM.csv: needs the whole 139-rule stream set incl. THPC1 decision streams + 7 extractors + 136 weekly refits; no approximation |
| THPC1 (profit) | 4 | CANNOT EXTEND (by deadline) | see T2__pend_THPC1.csv: c1 chain/X matrices/caches not rebuilt on redo tape; GBM walk-forward + bit-exact old-window tie not feasible by 22:25Z |
Untouched: THPC3, DIPENTRY, UF-PROFIT (REDO-8). No breach. Bulk dir /mnt/l2/l2vast/ds3_redo_tail2/ (logs only).
Old-L3M -> new-L3M descriptive means: see REDO-4 ingestion (vectors carry usd by label day; not summarised here).
