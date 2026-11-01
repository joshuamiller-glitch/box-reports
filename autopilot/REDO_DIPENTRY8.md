# REDO_DIPENTRY8 (REDO-8, T-RECENT-REDO ledger tail, 2026-11-01)
Builder report: DIPENTRY, UF-PROFIT c1-c4, THPC3 (profit). Cap 2026-10-31 (last session day 2026-10-30), de-duplicated tape only (ds3_g2_redo path, out/tape_dedup, trade index thp_redo / dipentry_redo/trades_arm.parquet), windows from code/cap/windows.py. The programs' own builders, paths and cap only; old windows tied first. Descriptive only, post-hoc, no PASS claims.
Vectors: out/recent_wins/redo/vec/D8__{DIPENTRY,UF-PROFIT-c1..c4,THPC3}.parquet (+ D8__tie_*, D8__pend_*); window tables out/recent_wins/redo/{DIPENTRY,UF-PROFIT,THPC3}/windows_D8.csv. Code: l2vast/ds3/code/recent_wins_redo/D8/ (dipentry/, uf/, thp_c3/, d8_lib.py). Bulk: /mnt/l2/l2vast/ds3_redo_d8/.

## 1. Result table (ledger rows)
| group | ledger rows | extended | tied | not tied / blocked | old L3M -> new L3M (mean) |
|---|---|---|---|---|---|
| DIPENTRY | 38 | 38 | 38 (stack $/wk, float32 rounding 1e-4; the grids are bit-identical) | 0 | +30,130 -> -8,820 $/wk (10 of 38 positive) |
| UF-PROFIT c1 | 6 | 6 | 6 | 0 | 0.309 -> 0.004 pts/trade (2 of 6 positive) |
| UF-PROFIT c2 | 32 | 32 | 32 | 0 | 0.235 -> 0.084 (21 of 32) |
| UF-PROFIT c3 | 14 | 14 | 14 | 0 | 0.139 -> 0.026 (11 of 14) |
| UF-PROFIT c4 | 16 | 16 (pts) | 16 in pts | 6 ledger rows (12 more non-ledger cells) also store a lock-engine stack $: NOT extended, see 3 | 0.097 -> -0.038 (7 of 16) |
| THPC3 profit | 20 | see section 4 | | | |
Non-ledger cells of the same programs were also run (DIPENTRY 41, UF c1 14, c2 67 of 68, c3 92, c4 32 of 33, THPC3 btab+cusum 76): all tie where a stored value exists.

## 2. Tie-out (done before scoring)
* DIPENTRY: de_ticks tick tables rebuilt from ds3_l2feat_redo (dp10s/ldp10s): 340 of 350 old month-book files bit-identical; the 10 Feb-2026 files only gain rows after 02-06 (old rows identical). trades_arm from dipentry_redo (REDO-1; arm_end_s identical on the 47,131 old tids). de_grid phase 1 and 2 (A1/A2/B1/B2/C cells, 2072 cells): NET, FIL, TGT, ADV identical on all 44,370 old trades. Row values recomputed from the grids tie the ledger to 1e-4 (the stored 2026-02 values are float32 sums; recomputing from the ORIGINAL old grids gives the same 2e-5 deviations). One single-book row (WALL_BID SM) uses the weeks in which the row itself has signals as the L6M denominator (27 vs 28), as stored.
* UF-PROFIT: the L2H row store (REDO-4A, bit-identical at old rows) + 12 L2 feature arrays f_* rebuilt from ds3_l2feat_redo (bit-identical at the 39.49 M old rows, all 153 comparable arrays); PRE+X' threshold samples are drawn by position in the store (rng.choice / [::5]); the REDO store interleaves new trades, so the SAME old rows were re-selected by (tid,ts) key: thresholds.json of c1, c2, c3, c4 equal the stored ones exactly. Cell arrays DM, DN, DL, FIRE, XSEC, XPM, XPN: bit-identical on old trades for all 376 / 222 / 225 / 190 cells. c3: X_book, X_path, X_div_raw bit-identical on 5.28 M old G rows (1-s tables via the ext-part reader); walk-forward LightGBM (n_jobs=8, same params): the old 600k fit draws replayed on the old G array and mapped by key, refits 2026-04, -07, -10 added: all 48 model triggers identical on old G rows (two thresholds differ in the 16th digit). Ledger values: pts to the stored 3-decimal rounding, live $ to whole dollars, n = fires, MDE to 0.3-1 percent (stored rounded).
* THPC3: see section 4.

## 3. Not extended
* UF-PROFIT c4 lock-engine stack $: 6 ledger rows (and 12 non-ledger) carry a stored stack $ (L3M_stack_usd_wk). I ported uf_p4_stack/uf_p1_stack_lib build_B onto REDO-5's stackx engine (D5S) and ran the 6 rows; the old-window result does NOT tie (e.g. stored 12,600 / 9,505 / 5,630 $/wk vs rebuilt 14,948 / 11,930 / 6,063), so it is not delivered. Missing input: the legacy UF stack object (dvg_lib.base_B + e2 Ctx KEYS with the UF cm/hold conventions) on the REDO tape; REDO-5's engine uses keys2/frozen weights and differs. The usd column of those rows holds per-contract live $ (pts x 20 x lots) and is flagged; the primary pts values tie.
* UF-PROFIT c2 CH_F9_12m and c4 CH4 chain cells (non-ledger): not built.
* ENSM, EQR, THPC1, ADDUW B1, FIRST-HOUR-DELTA, EXP2 (b)(d), EXP1 chains: reassigned by the lead, not touched.

## 4. THPC3 (profit)
(see below)
