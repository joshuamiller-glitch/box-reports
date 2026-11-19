# ID CONVENTIONS for ladder cells (W-NYENG, 2026-11-19 22:5xZ; order 2212Z conditions a+b)
Two DIFFERENT conventions exist; do not mix them.

| session | id pattern | meaning | event file | sets |
|---|---|---|---|---|
| **NY AM** | `L<hex8>` | the cell as W-SHORT defines it, ONE SIDE as labelled by its mode (mode long -> long signals only; mode both -> both sides); the id's event file was rewritten at 17:03Z for long/short cells: results before that are marked stale until re-run | /mnt/l2/l2vast/_nye/ev/L<hex8>.parquet | TL3_NYE_L<hex8>_RK7 (REPLACE-K7), controls ..._RK7CT<k><p/m>, layers TL3_NYL_L<hex8>x<slot>_* |
| **NY AM** | `B<hex8>` (= 'B' + the old id minus its first letter) | the BOTH-SIDE version of a long/short cell: the module's full output on both sides at the book's bracket, as the engine ran the old L ids before the rewrite | /mnt/l2/l2vast/_nye/ev/B<hex8>.parquet (new file, never overwritten) | TL3_NYE_B<hex8>_RK7 |
| **Asia** | `L<hex8>` | BOTH sides as engine-run (old ids kept; event files untouched) | /mnt/l2/l2vast/_asi_lad/ev/ | TL3_ASI_L<hex8>_R* |
| **Asia** | `M<hex8>` (= 'M' + old id minus first letter) | SIDE-ONLY (the mode-filtered version of a long/short cell) | /mnt/l2/l2vast/_asi_lad/ev/M<hex8>... | TL3_ASI_M<hex8>_R* |
Mapping tables: NY AM B ids -> /mnt/l2/l2vast/_nye/bothside_ids.csv (new_id, old_id, key with |both, old mode, old rank, events) and ladder_cells_both.json (cell definitions: mode both, key ends with |both); Asia M ids -> W-ASIA's ladder lists. A book is identified by its KEY (row|module|variant|params|bracket|mode) plus the convention of its session: the same key can carry two ids (my 22:20Z crc ids vs W-SHORT ids; W-DEDUP's id_twins.csv / DEDUP_TWINS.csv list the identical-stream pairs).
Rules: (1) an events file is never overwritten once any month has run on it (ny_ladder.py skips an existing file); a changed definition gets a NEW id. (2) both-side and one-side rows are separate rows in every ranking and are never merged. (3) W-BEST / pass-2 / stack builders: read the id prefix with the table above (NY AM B = both sides, L = one side by mode; Asia L = both, M = side only).
