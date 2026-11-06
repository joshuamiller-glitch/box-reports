# NQ13_ENGINE_LOOP_FEASIBILITY - engine-in-the-loop signal-parameter variation for the 7 formal NQ pairs (BASE-4, 2026-11-06)
Research only; no data/live/ file read; sealed blind-week page and harness files untouched. Answer to the lead's step (1). All times below are MEASURED on this box in the last hour unless marked "estimate".

## 1. Verdict
FEASIBLE and cheap. Object = the same one ZL-2 calibrates the 1-s object against and used in INTERIM 2: the V13T engine with all components off (TH-L2 off, zones off, 70/30 split off, PE confirmation off, ER off, locks off, signal state off, lots 1 per live-session row, live cost frame), bases V0 and V2. For that object a signal-parameter cell needs only the trade UNIVERSE of the changed book regenerated, not the L2 / THP chain. Estimated per cell about 7 min single-thread (engine runs included); 26 pipelines (22 neighbour cells + 4 live-cell tie-outs) ~ 3 core-hours, under 1 h wall on 6 cores. Far below the 30 h / 12 cores limit, so I proceed with the FULL set of 7 pairs (step 2), in two phases (A: cells buildable today; B: cells that need a small builder first). A full live-stack variant (TH-L2, zones, PE, split on) is a separate, optional phase C (about +35 core-min per cell, see 4).

## 2. What the engine actually reads (audit, not guessed)
I logged every open / np.load / read_parquet / memmap during a full engine run on the blind (superset) tree with the P2 configuration and again with the all-off configuration. The all-off run reads exactly these inputs (th_loss off => the L2SL row table is NOT read):
| store | keyed by | changes with a book's signal parameters? | builder (code/blind/chain copy of the REDO-1 script) | measured time |
|--|--|--|--|--|
| 1-s path SS SH SL SC, l2set glob BL BS ja jb, bars time_1m, bars_store tc/45s, confirm bars 15m, lgb_pred | time / second / month | NO (market data) | shared, symlinked | 0 |
| trade rows of the book: base_KB / base_SM (CE.build events + ba_rows2.gen), HM rows (own_signals variant + ba_rows2.gen), pb7_rows (be_lib.eng_PB7 + pb7_build.signals) | book trade list | YES | blind_rows_base.py, blind_rows_pb7.py (+ a parameter hook, see 5) | events 1.2 s, rows 1.6 s (KB); PB7 variants 0.2-0.4 s + sim ~20 s |
| trade_index (tid = book code x 10^6 + cumcount per book, so only the changed book's tids change) | tid | YES (that book) | thp_index.py (all books, deterministic) | 9 s |
| dipentry trades_arm.parquet (the engine's universe, 63 cols) | row | YES | blind_trades_arm.py | 3 s |
| trendgate universe.parquet + chart_5m.parquet (ER(20) chart store) | row at signal second | YES (rows of that book) | blind_universe_er.py (can reuse unchanged books' rows) | 150 s all books; ~20 s for one book |
| EF-2 masks.pkl (HM/KB/PE signal-state masks) | d row | YES (KB, HM) | blind_masks.py | 18 s |
| poi_store features.npy + index.csv (zone-line features per trade) | tid | YES (rows of that book) | blind_poi_feats.py (streams are market-only and reused) | 8 s |
| ts2 flags cache (A06 slot / B02) | d row | YES (row-aligned) | recomputed per tree by blind_run (tree-specific file) | 15 s |
Not read by the all-off object but read by the full live stack (phase C): l2set loss rows.parquet + tidx_cut.parquet (needs thp_build + l2feat ldp10s for the changed book, then blind_l2s_rows.py), c3 path cache. Measured for ONE book-month (KB, 2025-06): thp_build 18 s (loss+profit), l2feat dp10s+ldp10s 37 s; 45 months => about 14 + 28 min single-thread, month-parallel to under 10 min wall; l2s_rows for one book ~3-5 min.

## 3. Cells (one parameter at a time, one grid step; live cell always included; each book cell serves all its pairs: KB asia/london/nypm, SM asia/london, HM asia, PB asia)
| book | live | one-step neighbours | status |
|--|--|--|--|
| KB (Keltner flip, 3-min) | k3 n14 m1.0 | A: n20, m1.5 (library grid cells; buildable and events tie to stored ev_KB, 45,593 equal). B: n10, m0.75, k2, k5 (not in the library grid: CE.build raised IndexError on the NT8-bar indicator cache at the old length 1,313,215; needs the extended-length indicator cache) | 2 now + 4 |
| SM (Supertrend flip, 10-min) | k10 n7 m3.0 | A: n10, m2.5, m3.5 (library grid). B: k5, k15 (non-grid, same cache issue) | 3 now + 2 |
| HM (HMA(20) vs HMA(55) of close-VWAP, EMA200 side filter) | 20/55/200 | B: fast 16 and 24, slow 44 and 66, EMA 150 and 250 (own_signals has the lengths hard-coded; a parameterised copy must first reproduce the HM part of ev_A exactly) | 6 |
| PB (PB7 shape, bars_eng eng_PB7) | variant G, W 15 min, depth m 0.5 | A: Wmin 10 and 20, m 0.4 and 0.6 (eng_PB7 takes Wmin and m directly; counts 24,009 / 25,200 / 17,328 / 29,132 vs live 24,760) | 4 now |
Total: 9 cells now (A), up to 13 more after builders (B) = 22 neighbour cells, plus 4 live replications (KB, SM, HM, PB) that must tie out. A pair's selector choices = its book's live cell + that book's neighbours (7 to 9 cells).

## 4. Hours
Per cell (all-off object): events+rows 5 s, thp_index 9 s, trades_arm 3 s, universe_er ~20-150 s, poi_feats 8 s, masks 18 s, flags 15 s, two engine runs (V0, V2) 2 x 75-110 s = about 7 min single-thread, 1 core, ~6-8 GB RSS. 26 pipelines about 3 core-hours: wall ~1 h on 6 cores. Phase C (full stack, optional): + thp_build (loss spine) ~7 min + l2feat ldp10s ~14 min + l2s_rows ~4 min = about +25 min per cell, month-parallel to under 10 min wall on 6 cores; 22 cells ~ 9 core-hours. Disk per cell: tid-keyed stores < 1 GB (all-off), + ~1 GB for phase C; /mnt/l2 has 2.0 TB free.

## 5. Approximations (each with its tie-out test; none is silent)
A1. One book changes per cell: other books' rows, tids and stores are the live ones. Tie-out: the live cell regenerated through the cell pipeline must give the stored all-off daily series to the cent (V0 and V2, first 935 days) - the blind tree's first 935 days already equal the redo run exactly (W3 $2,462,264.28 on the full config; all-off to be compared in the same way before any neighbour is run).
A2. ER chart store / universe for the changed book: rebuilt with the same tg_series code; flow columns (bar_delta, cvd) stay NaN for rows after the old cap exactly as in the redo tree; ER is off in the all-off object, so no effect on it; used only in phase C.
A3. Non-grid KB/SM neighbours and the HM variants need new builders (see 3). Their live-parameter instance must reproduce the stored events (KB 45,593, SM 3,375, HM part of ev_A) before a neighbour counts; otherwise that neighbour is dropped and listed.
A4. Percent/hindsight: the live cell was chosen on 2023-26 (bias toward live), stated against every comparison as in DS3_NQ13 interim 1.
A5. Evaluation window: first 935 label days (2023-04-03..2026-10-30) of the blind tree, carrying weeks dropped (2023 W21-41, 2025 W06-09, 2026 W06-08, W29-39), so numbers are comparable with interim 1/2; the four blind-week days are not used.
A6. Phase C only: z-score columns of the L2SL rows are not recomputed for a changed book (the engine's cut uses p5, median level, upnl, ts, cut, ne5 only); tstats-based index columns (n_dec, jade) taken from the cell's own thp_build.

## 6. Plan (step 2 of the order)
Prereg file l2vast/ds3/prereg/NQ13_ENGINE_LOOP_scope.md (cells, tie-out rule, selector = the DS3_NQ13 walk-forward selector (trailing T = 6/12/24 months, criterion trailing net $, min active days 5/10/20, fallback to live, purged, evaluated on E1 2023-26 carry-dropped), placebo = random-parameter selector (forward-only, random neighbour per month), family max-T over all pair x T selectors, win rule as in DS3_NQ13), sha256 in DECISIONS.md before any neighbour cell is run. Order: tie-out of the 4 live cells; phase A (9 cells); builders for B; phase B. Result appended to DS3_NQ13.md (>>) as "INTERIM 5 engine-in-the-loop", V0 and V2 named. ZL-2 is asked (MORNING.md) only for the selector/placebo code reference of interim 1; the stores above are generated by me.

## CORRECTION / UPDATE 2026-11-06 (BASE-4), appended to the feasibility page
Measured after the first version: te_sig.fam_kelt(k,n,m) and fam_st(k,n,m) accept ANY parameters and reproduce the stored live events exactly (KB 45,593 and SM 3,375 equal to ev_KB / ev_SM); all KB (n10, n20, m0.75, m1.5, k2, k5) and SM (n5, n10, m2.5, m3.5, k5, k15) neighbours build in under 1 s each (the CE.build IndexError in section 3 is specific to the CE cell builder and is bypassed by calling te_sig directly). So phase A = KB 6 + SM 6... (SM: n5, n10, m2.5, m3.5, k5, k15 = 6) + PB 4 = 16 cells; only HM (6 cells) needs a new builder. Totals unchanged in order of magnitude (about 7 min per cell).
