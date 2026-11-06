# ALL_EA_HISTORY - exit-aware, unthinned PE + KB + HM + SM history as a PRIVATE research tree (ZL-2, 2026-11-06)
Prereg addendum l2vast/ds3/prereg/ALL_EA_HISTORY_prereg.md sha256 9c38b159e26e2ca08ae624651e47749dd00c5f126212022b0b79301dab68fc59 (to PE_EA_HISTORY_prereg 4a58995b..., both logged in DECISIONS.md before any statistic). Research only, no P&L, no PASS claim. Published base and sealed trees untouched (manifest below). Method = PE_EA_HISTORY.md (read that page for the details); this page gives the all-books numbers.

## 1. The tree
* Tag **all_ea**; bulk /mnt/l2/l2vast/ds3_all_ea/ (keys, logs, trees), ds3_thp_all_ea, ds3_l2feat_all_ea; out/ layer l2vast/ds3/out/{all_ea, thp_all_ea, l2set_all_ea, dipentry_all_ea, trendgate_all_ea, eint1dd_all_ea, poi_store_all_ea, bars_/bars_store_/confirm_/tape_rescore_all_ea (symlinks)} + /mnt/l2/l2vast/ds3_g2_all_ea, ds3_l2set_all_ea. Same structure as pe_nb / pe_ea. Use VTAG=all_ea (run_cells.py, var_run.py). Driver code/pe_ea/cell_run_all.py, checks code/pe_ea/verify_all.py (/mnt/l2/l2vast/ds3_all_ea/verify.json).
* Books rebuilt: **PE, KB, HM, SM** (busy=-1; PE from the pe_ea generator, KB/HM/SM = ZL-1's ob_rows.py output base_<B>_nobusy.parquet, same events and tape). **Skipped, as ordered: ST (not a D7 book); A6/PB7, MV and every other book without a raw-event store (they keep their published rows).** Each published thinned row is contained in the unthinned set with identical fields (asserted).
| book | unthinned rows | published thinned | extras | trade ids blind -> all_ea | rows by year, 2023-04.. (extras) |
|--|--|--|--|--|--|
| PE | 61,765 | 8,497 | 53,268 | 8,283 -> 59,422 | 2023 14,834 (13,731) / 2024 16,607 (14,892) / 2025 16,358 (13,882) / 2026 13,966 (10,763) |
| KB | 42,600 | 8,777 | 33,823 | 8,556 -> 40,993 | 2023 10,241 (9,106) / 2024 11,305 (9,528) / 2025 11,250 (8,729) / 2026 9,804 (6,460) |
| HM | 20,537 | 6,423 | 14,114 | 6,246 -> 19,765 | 2023 4,903 (3,968) / 2024 5,465 (4,088) / 2025 5,420 (3,602) / 2026 4,749 (2,456) |
| SM | 3,168 | 2,421 | 747 | 2,343 -> 3,059 | 2023 761 (292) / 2024 880 (265) / 2025 791 (154) / 2026 736 (36) |
Total 128,070 rows, 101,952 extras; new trade ids 97,811 (trade index 70,232 -> 168,043; tidx_cut 66,714 -> 164,525). Extras keys (book, ei, side): /mnt/l2/l2vast/ds3_all_ea/all_ea_extra_keys.parquet. ZL-1's estimate was ~88k ids; the windowed index gives 97,811 new ids because the unthinned KB set is 4.9x the thinned one.
* Old trade ids unchanged for every book; extras numbered after the old rows of their own book. Loss rows and L2 features rebuilt for PE, KB, HM, SM for 2023-02..2026-11 (44 months); trades_arm tags from dipentry_blind (read-only); c3 path, l2s_rows, universe_er, poi_feats, masks rebuilt with the unchanged builders (derived copies).

## 2. Tie-outs
| check | result |
|--|--|
| thinned rows contained, fields identical (PE, KB, HM, SM) | 8,497 / 8,777 / 6,423 / 2,421 of the same |
| trade_index and tidx_cut: all columns on all 66,714 old tids vs the blind tree | identical (0 columns differ) |
| loss rows on the old ids | rows 23,622,780 = blind 23,622,780; count, p5 sum, upnl sum, cut sum equal on 63,340 of 63,340 ids |
| new ids / with loss rows / new loss rows | 97,811 / 95,731 / 68,863,795 (total loss rows 92,486,575) |
| c3 path samples vs the ZL-1-restored blind cache | 4,000 of 4,000 identical |
| md5+size manifest of the published and sealed trees, before (18:11Z) and after | 18,638 files, 144.25 GiB, 0 added / 0 removed / 0 changed |
| grep of derived scripts for write targets | all writes go to *_all_ea paths |
| engine run with the extras dropped reproduces the published numbers | NOT done by me: BASE-4's check (drop by key from the rows files) |

## 3. Time, disk, incidents
Wall time about 22 minutes for the first complete build plus two corrective reruns (about 25 minutes more): total from start 18:13Z to tied-out 18:40Z. Disk: ds3_all_ea 9.6 GB, ds3_thp_all_ea 6.2 GB, ds3_l2feat_all_ea 7.0 GB = 22.8 GB (l2set loss rows 2.9 GB, c3 cache inside thp_all_ea 6.9 GB). Incidents, all private-tree only: (1) 12 parallel thp_build workers (about 10 GB each) coincided with other jobs and MemAvailable fell to 6 GB; 2 workers were OOM-killed (months 2023-04, 2023-06); restarted with 8 workers and a 60 GB start guard, completed month files kept. (2) The skip-existing test counted other books' real 2026-11 copy files, so the 2026-11 month was not built for the four books in the first pass: the verify step caught it (199 blind-week ids without loss rows), driver fixed, month built, all checks re-run clean. No file of the published or sealed trees was written.

## 4. Limits and cautions (same as pe_ea, plus)
POI streams not rebuilt (zone layer reads the published streams); calendar tags wd, prev_daytype, vix_prev and profit statistics are NaN for the extra ids (not read by d7base); ids of a book are no longer monotone in time (extras after the old block); A6/PB7, MV and ST unchanged and thinned as published: the 'all-books exit-aware' stack still understates the row set of those books. The nominal outcome of added rows is not an expectation; locks, caps and lot chains act on the larger row sets: BASE-4's runs report the effect.