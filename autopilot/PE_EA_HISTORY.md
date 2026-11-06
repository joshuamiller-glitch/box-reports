# PE_EA_HISTORY - exit-aware, unthinned PE history as a PRIVATE research tree (ZL-2, 2026-11-06)
Prereg l2vast/ds3/prereg/PE_EA_HISTORY_prereg.md sha256 4a58995b253f8db6b13e55865363fa26bc75e731ae05b7799ab875201ab623fc (DECISIONS.md, before any statistic). Research only, no P&L here, no PASS claim. The published base and the sealed trees were not touched (manifest below). Hand-off to BASE-4 for the Q1-A stack runs (V0/V2, kfix off and on).

## 1. What the tree is
* Tag **pe_ea**, bulk dirs /mnt/l2/l2vast/ds3_pe_ea/ (trees, logs, keys), /mnt/l2/l2vast/ds3_thp_pe_ea, /mnt/l2/l2vast/ds3_l2feat_pe_ea; the out/ layer (symlinks and private dirs): l2vast/ds3/out/{pe_ea, thp_pe_ea, l2set_pe_ea, dipentry_pe_ea, trendgate_pe_ea, eint1dd_pe_ea, poi_store_pe_ea, bars_pe_ea, bars_store_pe_ea, confirm_pe_ea, tape_rescore_pe_ea} + /mnt/l2/l2vast/ds3_g2_pe_ea, ds3_l2set_pe_ea (same structure as the pe_nb tree that the engine already ran: directory listings identical with the tag replaced). Use it like ZL-1's pe_nb: VTAG=pe_ea (the cell cubes of NQ13: code/blind/run_cells.py with tag pe_ea; the blind-week recipe: code/blind/defects/var_run.py).
* PE rows = every raw PE event with a valid bar over the whole PE tape, generated with `busy=-1` (Q.gen_core2 and R2.gen), i.e. NO library busy-thinning: the engine applies its own one-position rule with its own exits (exit-aware in one pass, PE_BUSY_THINNING Part 2). Rows file out/pe_ea/rows/base_PE_pe_ea.parquet (+ PB3_PB3B_R5_P1_trades_pe_ea.parquet, same rows). Evaluation windows end at the cap; blind-week rows (to 11-05) are in the tree as in the blind superset.
| year | PE rows (unthinned) | of which NOT in the published thinned set |
|--|--|--|
| 2023 (from 04) | 14,834 | 13,731 |
| 2024 | 16,607 | 14,892 |
| 2025 | 16,358 | 13,882 |
| 2026 (to 11-05) | 13,966 | 10,763 |
| all | 61,765 | 53,268 |
Published thinned set: 8,497 rows (all 8,497 found in the unthinned set with identical keys). Trade index: 121,371 trades (blind 70,232), PE 59,422 (blind 8,283): PE rows with a trade-index entry; the other 2,343 of the 61,765 rows have no index entry (the index builder's window filter; not examined further). The extras are flagged by key (ei, side) in /mnt/l2/l2vast/ds3_pe_ea/pe_ea_extra_keys.parquet.
* **Old trade ids are unchanged**: tid = BOOK_CODE x 10^6 + cumcount; the extra PE rows are numbered AFTER all old PE rows (derived thp_index sort key isx, s_in, book, then restored to time order). Every non-PE book keeps every tid.
* Stores rebuilt with the UNCHANGED builders (derived copies in code/blind/chain_cells/pe_ea/, driver code/pe_ea/cell_run_ea.py): thp_index; THP loss rows ldp10s (PE, 2023-02..2026-11, 44 months); L2 features dp10s; trades_arm (tags of the 70,232 blind tids read from dipentry_blind, read-only); c3 path (own cache dir out/thp_pe_ea/wf/c3/cache); l2s_rows (loss rows 58,754,444; tidx_cut 117,853); universe_er; poi_feats; masks.

## 2. Tie-outs (code/pe_ea/verify.py, /mnt/l2/l2vast/ds3_pe_ea/verify.json)
| check | result |
|--|--|
| thinned published PE rows contained in the unthinned set | 8,497 of 8,497 |
| trade_index: every column on all 70,232 old tids vs the blind index | identical (0 columns differ) |
| tidx_cut (loss-row index): all 66,714 old tids, every column | identical (0 columns differ) |
| loss rows on the 63,340 old ids that have rows | rows 23,622,780 = blind 23,622,780; per-id row count, p5 sum, upnl sum, cut sum equal on 63,340 of 63,340 |
| c3 path samples (4,000 random old tids vs the ZL-1-restored blind cache) | 4,000 of 4,000 identical |
| new ids / with loss rows / new loss rows | 51,139 / 50,024 / 35,131,664 |
| md5+size manifest of the published and sealed trees (out/blind, thp_blind, l2set_blind, bars_blind, confirm_blind, bars_store_blind, tape_rescore_blind, dipentry_blind, trendgate_blind, eint1dd_blind, poi_store_blind, thp, l2set, thp_redo, ds3_thp_blind, ds3_l2feat_blind, ds3_g2_blind, ds3_l2set_blind), before and after | 18,638 files, 144.25 GiB, 0 added / 0 removed / 0 changed (files manifest_before.json, manifest_after.json) |
| grep of every derived script for write targets | all writes go to *_pe_ea paths (out/pe_ea, thp_pe_ea, l2set_pe_ea, dipentry_pe_ea, trendgate_pe_ea, eint1dd_pe_ea, poi_store_pe_ea, ds3_thp_pe_ea, ds3_l2feat_pe_ea); the sealed-cache spelling of the 16:51Z incident is rewritten and the c3 cache is the tree's own |
| engine run with the extras dropped reproduces the published PE numbers | NOT done by me (needs the engine): BASE-4's check |

## 3. Cost, disk, time
Build 456 s (first complete run) and 417 s (final run, with the trades_arm tag source corrected); /mnt/l2 use 12.0 GB (ds3_pe_ea 6.1, ds3_thp_pe_ea 2.8, ds3_l2feat_pe_ea 3.0; l2set loss rows 1.7 GB inside). Parallel steps used up to 12 workers with the MemAvailable >= 40 GB guard. A first attempt stalled because the driver read child output only at exit (pipe full); fixed to per-step log files, no data affected (no partial file reused: only completed month files were skipped).

## 4. Limits and cautions for the Q1-A runs
* POI streams (gen_poi) are NOT rebuilt: the zone layer reads the published streams (as in pe_nb). Zone/skip logic for the added PE entries therefore uses the published stream rows.
* The calendar/day-type tags (wd, prev_daytype, vix_prev) and the profit-mode statistics are NaN for the 51,139 extra ids (blind tids carry them); the engine code (d7base) does not read them. Row counts of the unthinned set vs ZL-1's 59,417 raw events differ slightly (61,765 rows = events with a valid bar and both sides).
* Extras interleave in time with old rows but have higher ids; any code that assumes the PE ids are monotone in time will see the extras after the old block (the trade_index file itself is in time order).
* Dropping the extras for the tie-out: filter the rows file by pe_ea_extra_keys (ei, side); the extras' ids remain in the stores but have no rows (not exercised by me).
* The nominal outcome of the added rows flips sign by year (ZL-1); do not read it as an expectation. One-position, locks and caps act on the larger row set: lot-chain and lock effects are the quantities BASE-4 reports.
