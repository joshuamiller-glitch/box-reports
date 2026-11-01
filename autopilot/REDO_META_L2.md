# REDO_META_L2 (D5, T-RECENT-REDO section 4, 2026-11-01)
Builder report for META FS1/FS2, ADDUW B2, L2ENTRY-A/B, UF-ENTRY c1-c4, THL2 L2H, CF-COMBO FOUR, EQR, STRUCT48 and other unowned rows. Cap 2026-10-31 (last trading day 2026-10-30). Programs' own builders, REDO layers, tie-out on the old period first. No approximation, no carry-forward, no PASS claims. Vectors: out/recent_wins/redo/vec/D5__*.parquet (+ D5__tie_*, D5__pend_*); window tables (L1M|L2M|L3M|L6M|HOLD|MID|PRE|X', n, MDE, old L3M, tie status): out/recent_wins/redo/<program>/windows.csv. Code: l2vast/ds3/code/recent_wins_redo/D5/{F1,F2}/; bulk data /mnt/l2/l2vast/ds3_redo_d5/ and ds3_d5_work/.

## Extended and tied
| program | rows extended / in all (ledger) | tied | no stored old L3M | note |
|---|---|---|---|---|
| L2ENTRY-A | 681 / 681 (596) | 681 (pts, live $, n at 1e-6) | 0 | keys2 exact on 47,131 old tids; 211 rules' old-period weights bit-identical incl. 3 placebos; F4 learned = quarterly walk-forward, refits 2026-04-01/07-01/10-01 added; ADAPT_chain not rebuilt (no ledger row) |
| L2ENTRY-B | 156 / 156 (69) | 156 (155 trade lists identical) | 0 | events rebuilt with the program's detector; all 1,649,431 events re-simulated on ds3_g2_redo |
| UF-ENTRY c1 (REDO-4B) | 96 / 107 (76 of 84 ledger) | 87 incl. 19 at rounding tolerance | 9 | 11 regime-feature cells pending (ufe_regime.build_fv); 8 still open |
| UF-ENTRY c2 | 142 / 142 (90) | 131 (1e-4 rel) | 11 (vector == stored D exactly) | hazard walk-forward identical on 27,529 old events; quarterly refits added |
| UF-ENTRY c3 | 29 / 29 | 27 | 2 | not in brief, added |
| UF-ENTRY c4 | 93 / 93 (52) | 87 | 6 (vector == stored D) | bits BL2/BS2/REL_s bit-identical on 36.6M old seconds |
| THL2 L2H (REDO-4A vec) | 132 / 132 (50) | 132 | 0 | windows tables written by D5 |
| CF-COMBO FOUR | 111 / 111 (43) | 60 | 51 | 52 of 88 window rows show 0 fires Feb-Oct for CFA:*, ote705, pd50 members (looks genuine sparseness; second look advised) |

## Pending (cannot be extended now), with reason
| program | rows (ledger) | reason | retry when |
|---|---|---|---|
| META FS1 stack $ | 669 (388) | ledger unit is stack $/wk; the legacy lock-stack engine (e2_joint -> dvg/bk/vs/sl; sl/books.pkl from direct MBO replays, vs/base.pkl frozen weights, struct48 setA_daily 953 days to 20261016, ABR bundle) exists only to 2026-10-16/23 on the ORIGINAL tape. Walk-forward (weekly rolling re-fit, 12 real pipelines) WAS re-run: old-week predictions, tree and W for 1,330 configs bit-identical to stored; only a supplementary pts-level view exists (out/recent_wins/redo/META_FS1/pts_level_windows_SUPPLEMENTARY.parquet, not the ledger unit) | books.pkl replays + frozen weights + setA rebuilt on REDO tape |
| META FS2 | 799 (449) | same engine blocker AND old-period tie fails: EINT tids differ in REDO feature tables (bar_vol_rel 143, monthend 139, monthend3 410, t_corr/c_corr 173) so weekly refits diverge; not tied, hybrid not built | as above + EINT features accepted |
| ADDUW B2 | 412 (353) | sl_lib engine, adduw/engine_rows.pkl, pool_keys/pool_bits gate bits (ldp1s) legacy only | as above |
| EQR lots_factor | 74 | frames B/C/E/F/G/H need L2SL/EXP2 stack, STK weekly series, sl_stack redo, D4's L2SP profit stream | after D4 L2SP/L2SL and the legacy stack |
| STRUCT48 / NM-B | 41 / 20 | struct48 engine is legacy (setA to 20261016, original tape); C's _legacy1016 vectors are NOT certified, not counted as done | engine re-run on REDO |
| CF-COMBO GREEDY / POOL | 9 / 2 | presence members BAR:tc|30s|inside_break, C2:ha|30s|HA_three, C2:ha|45s|HA_nolow2 need CONFIRM-BARS S1 / CONFIRM2 G1 per-trade cell files on REDO (another builder) | when those land |
| THL2 L2P | 15 | not run | next pass |
| UF-ENTRY c1 regime cells | 8 | ufe_regime.build_fv not rebuilt | next pass |

## Observations (descriptive only, no selection)
L2ENTRY-A new L3M: skipTop3_rnd100_ahead [ALL] -0.62 pts vs +1.27 old; 49% of rows positive on new L3M vs 97.5% on old.

## Incidents (disclosed)
1. D5-F2 imported ufe4_div.py (no __main__ guard): rewrote out/uf/entry_c4/div_feats.parquet 17:49Z; restored 17:51Z from the same builder (same size 1,599,499 B, values equal on old tids; original not hashed).
2. Root filesystem hit 99-100%; bulk data moved to /mnt/l2; one scratch script (t_order.py) truncated by ENOSPC and rewritten.
3. REDO-4C's meta_redo/keys2.parquet reused by F1 after tie-out (exact on old tids).
