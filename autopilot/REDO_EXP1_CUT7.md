# REDO_EXP1_CUT7 (REDO-7, 2026-11-01): EXP1 loss per-stream, CUTWAIT tier B, THP_POLICY joint, THL_HM, SD-B, EXP2(f)

Builder report. Cap 2026-10-31 (last session day 2026-10-30), de-duplicated tape only, windows from code/cap/windows.py (L1M | L2M view | L3M | L6M | HOLD | MID | PRE | X'). The programs' own builders and kernels, only paths and cap changed; the old windows were tied FIRST (every tie below was run before anything was scored). Descriptive only, no PASS claims, post-hoc labels, no approximation, no carry-forward. Old L3M = stored 2025-11-06..2026-02-06; new L3M = 2026-08-01..2026-10-31.

## 1. Coverage (ledger rows)
| program (RECENT_WINS_REDO sec. 8 pending) | ledger rows | extended | TIED | NOT TIED | blocked |
|---|---|---|---|---|---|
| EXP1 loss per-stream fixed | 340 | 340 | 310 (+30 TIED in the old-prefix variant) | 30 (all D6_TB4B_ASIA, redo tick bars, see 3) | 0 |
| CUTWAIT tier B (D6_SM_t60_sst_ASIA 16, D6_TB4B_ASIA 11, CR 6, D6_HM_t75_s90_NYAM 3) | 36 (the pending table lists 36, not 63; 16+11+6+3) | 36 | 25 (+11 TIED in the old-prefix variant) | 11 (D6_TB4B redo) | 0 |
| THP_POLICY joint (L2SE/L2SP/L2SL, sets H and B, 7 components) | 13 (+1 non-ledger) | 13 (+1) | 13 (+1) | 0 | 0 |
| THL_HM | 9 | 9 | 9 | 0 | 0 |
| SD-B | 7 (70 cells of the program) | 7 (70) | 7 (70) | 0 | 0 |
| EXP2 (f) stack/ES-RTY state features | 16 (19 cells) | 16 (19) | 16 (19) | 0 | 0 |
| total | 421 | 421 | 380 + 41 via old-prefix variant | 41 flagged (redo variant) | 0 |
Non-ledger cells of the same programs were also built (EXP1 199, CUTWAIT 160 on 7 books, THP_POLICY 1, SD-B 63, EXP2f 3) so that "turned on since Feb" is visible. Of the 632 pending rows this clears 421; the remaining 211 are not in my list (DIPENTRY 38, UF-PROFIT c1-c4 68, THPC3 20, ENSM 19, EXP1 chains 8, EQR 14, THPC1/C2, ADDUW B1 5, FIRST-HOUR-DELTA 4, EXP2 (b)/(d) 6 ...).

## 2. Tie-outs (old windows, before scoring)
* EXP1 loss: the program's rules() table (code/exp1/exp1_loss.py: 40 L6 + 27 L7m cells) run through d4_thl_lib (REDO copy of thl_lib/thl_kern, unchanged) on the D4-rebuilt REDO stream tables (D4_work/thl/trades_<stream>.parquet; D4 built them with the stack_trades_redo chain from REDO-5 inputs, EM/PB/DN/MV/MA/CR lock-filter tables, D6 members). Stored EXP1 cache loss_cells_<s>.npz vs the rebuilt cells on every old trade, 17 streams x 67 cells: max abs diff 0.0 on 16 streams; D6_TB4B_ASIA differs (12 of 843 old trades are missing/different in the redo stream, 98.8 pts max). Ledger rows: L3M pts, live $, n, MDE (cluster = label day x entry session), L6M, HOLD, PRE, X' all tie (2e-6 abs / 1e-6 rel) on 310 of 340 ledger rows (492 of 539 cells).
* CUTWAIT tier B: cw_run cell logic (cw_redo.py of REDO-4C, itself the program's cw_lib kernel/chain/run_engine under redo_boot) with load_frame replaced by the D4 REDO streams and the frozen stored cells.csv (levels X, lots, stop, tf). Per-day delta (cell minus book base) vs stored res_<book>.pkl on 773 old label days: 0.0 for every cell of CR (98), D6_HM (98), D6_KB (98), D6_PB7 (70), D6_SM (84), D6_TB4W (70), D6_TB4B@old-prefix (70); D6_TB4B (redo bars) 0 of 70 exact (max 17,244 $/day). Rows: live $ sum and L3M/L6M/HOLD/PRE/X' $/wk tie on all rows with an old value (convention of cw_run.wsum: sum / ISO weeks touched, L3M fixed 13).
* THP_POLICY joint: REDO-4C's lj_main3 run (lj_all.py main variants, L2SJ engine under redo_boot, REDO streams _C_streams_redo2.pkl, ds3_g2_redo path arrays checked to end 2026-10-30 20:59:59). All 38 variants (E, P, L, EP, EL, PL, EPL x H/B x M/N + cost variants) equal the stored daily_main.npz on all 745 old days, six books, max abs 0.0 (file D7__tie_lj_variants.csv). NOTE: lj_main (no 2/3) in vec/ used the REDO-1 streams.pkl capped at 20260206, so every P- and L-bearing variant was zero after Feb-06; lj_main2 had no P after Feb-06; lj_main3 is the complete one and is what I used. (If REDO-4C's EQR frame A rows were scored from lj_main or main2 they carry that gap; they should be checked against main3.) 13 of 13 ledger rows tie L3M, L6M, HOLD, PRE, X' and live $.
* THL_HM: 9 L6 cells on the D4 HM stream (stream identical to stored, dM exact): 6 cells equal the D4 table columns exactly; all 9 tie L3M, $, n, MDE (label-day clustering, not day x session; found by testing), L6M/HOLD/PRE/X'.
* SD-B (T-SIGNAL-DECAY section B, code/decay dc_panel/dc_eng/dc_cells unchanged; path arrays from d4_thp_lib): REDO panel (dp1m + ldp1m, 7,973,337 rows) vs stored panel on the 6,722,000 old rows: all 32 columns identical; trades table 47,131 old rows all columns identical; walk-forward edge fit (6 arrays x 6.72 M rows) bit-identical; 68 cells x 47,131 trades dM, dN, dL and touched bit-identical. 70 of 70 cells tie L3M, $ (live lots by book), n, MDE (label-day clusters), L6M/HOLD/PRE/X'.
* EXP2(f): ABR c2 cache (abr_c2/c2_prep.py) and EXP2 bundle (abr_exp2/e2_prep.py) rebuilt from D2's REDO abr data tree (entry, score, score1): M10, MRP, G, TEX, TYP, FX, S, lots, EX, FB and all keys2 columns identical on the 47,131 old trades (only the srow index differs, an ordering index, not a value). e2_run_f.py chains (24 cells, real and reference) equal the stored chains_f.npz on all old trades (0 differences). 19 of 19 cells tie L3M, n, MDE (label day x session clusters).

## 3. Not tied, flagged
* D6_TB4B_ASIA (EXP1 30 rows, CUTWAIT 11 ledger + 59 other cells): the redo tick bars (de-duplicated tape, stray Sunday hour removed) differ from the old bars on 12 of 843 old D6_TB4B trades (D4 found 17 in 10 months; 2 in the old L3M window). Both variants are delivered as in D4: `D7__*` (redo) and `D7__*_tb4b_oldprefix` (old stored trade list for label day <= 20260206 + redo after), which ties 100% (EXP1 47 of 47 rows, CUTWAIT 70 of 70 cells). The new L3M values are identical in the two variants (the difference is confined to the old period).
* Nothing else is NOT TIED. Disclosed small differences: the ABR geometry slip10 (stop-slip calibration by year) differs from the stored cache on 1,106 old rows of Jan-Feb 2026 (max 0.37 pts) because the 2026 calibration now uses more 2026 data; M10 (the measure used by EXP2(f)) is identical and slip10 is not used in the ledger measure.

## 4. Descriptive (mean over ledger rows, old L3M -> new L3M; "pos" = rows with new L3M > 0)
| program | unit | rows | old L3M -> new L3M | pos new | other windows (means) |
|---|---|---|---|---|---|
| EXP1 loss per-stream | pts/trade/contract | 340 | +1.936 -> +0.660 | 230 | L1M +2.02, L6M +1.02 |
| CUTWAIT tier B | stack $/wk | 36 | +3,633 -> -1,855 | 8 | by book: CR +249 -> -1,816 (6), D6_HM +660 -> -684 (3), D6_SM +3,995 -> -2,087 (16), D6_TB4B +5,764 -> -1,858 (11) |
| THP_POLICY joint | stack $/wk | 13 | +48,848 -> +20,086 | 10 | |
| THL_HM | pts/trade/contract | 9 | +2.687 -> +1.598 | 9 | |
| SD-B | pts/trade/contract | 7 | +0.699 -> +0.080 | 4 | |
| EXP2 (f) | pts/lot | 16 | +1.333 -> +0.238 | 8 | |
(The ledger rows were chosen as positive on the old L3M and L6M windows; the old column is positive by construction. All MDE are in the windows tables; most new-L3M means are inside their MDE.)

## 5. Files (all new; REDO-4 loader format: rkey, ld, usd, pts, n[, fires])
vec/ (out/recent_wins/redo/vec/): D7__EXP1-loss.parquet (+ _tb4b_oldprefix), D7__CUTWAIT-tierB.parquet (+ _tb4b_oldprefix), D7__THP-POLICY-joint.parquet, D7__THL_HM.parquet, D7__SD-B.parquet, D7__EXP2f.parquet; each with D7__tie_<name>.csv and D7__pend_<name>.csv (all pend files are empty). Stack-$ rows (CUTWAIT, THP_POLICY): usd = daily stack delta at live lots; per-contract rows: pts = daily sum, n = daily trade count, usd = pts x $20 x live lots (EXP2f: pts per lot, usd 0).
Windows tables (eight windows, n, MDE, old L3M, tie status): out/recent_wins/redo/{exp1_loss/D7__windows_EXP1-loss.csv, cutwait/D7__windows_CUTWAIT-tierB.csv, thp_policy/D7__windows_THP-POLICY-joint.csv + D7__tie_lj_variants.csv, thl_hm/D7__windows_THL_HM.csv, sd_b/D7__windows_SD-B.csv, exp2f/D7__windows_EXP2f.csv} (+ _tb4b_oldprefix where applicable; exp1_loss/D7__tie_EXP1-loss_cells.csv = per-stream cell tie).
Code: code/recent_wins_redo/D7/ (d7_exp1_loss.py, d7_exp1_assemble.py, d7_cw.py, d7_cw_vec.py, d7_thp_policy.py, d7_thl_hm.py, d7_pts.py, d7_lib.py, d7_decay_build.py, d7_sdb_vec.py, d7_exp2f_vec.py, exp2/ with c2_prep_d7, e2_prep_d7, e2_lib, e2_run_f, tie scripts). Bulk (about 3 GB) under /mnt/l2/l2vast/ds3_redo_d7/. Tie json: /mnt/l2/l2vast/ds3_redo_d7/{decay/tie_decay.json, exp2/tie_*.json}.

## 6. Disclosures
1. Inputs I did not rebuild but reused after checking them: D4's THL stream tables (D4_work/thl/trades_*.parquet; each tied to the stored lists by D4 and re-tied here through the EXP1 cache), D2's REDO ABR data tree, REDO-4C's lj_main3 and streams, REDO-1 path arrays (ds3_g2_redo). The D6_TB4B 12-trade difference was found by D4.
2. importing the D4 library (te_core) clears sys.argv; scripts capture ARGV before the import (first run of the EXP1 builder exited silently, re-run).
3. Concurrency: up to 5 short CUTWAIT processes ran together for about 10 s (rule says 3); each under 4 GB. Root filesystem untouched by bulk writes (29 GB free throughout). No frozen corepool slot, no DEAD_CELLS.csv, no download, no purchase, no scratch in /tmp. No file overwritten; no script lacking a __main__ guard was imported (decay dc_eng/dc_cells and abr_exp2 modules have no import-time writes; the exp2 e2_run_f copy has the writes of its autopilot DF md only in the 'pre' stage, which was not run).
