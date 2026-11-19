# NY AM ladder: what are the "2,588 old-seed-only cells"? (W-NYENG, order 1850Z section E; research only, nothing queued or parked)

**Answer: all 2,588 are DUPLICATE IDS of cells that are already in the ladder, not untested books.** The "9,081 cells" were 4,557 distinct cell definitions counted under two id schemes: my seed at 22:20Z hashed the cell key with crc32 (ids like Lb73150d7), W-SHORT's current list uses its own ids (L0f11d2f7) for the SAME key (row | module | variant | params | bracket | mode). 4,524 of the 4,557 keys carry two ids; I built the cells of both lists as they were seeded, so some definitions were built twice and the old-only ids never got built.

| reason | cells | evidence |
|---|---|---|
| old-seed-only id never built, SAME cell key built under W-SHORT's id | **2,588 of 2,588** | exact key match (row, module, variant, params, bracket, mode) in the current list for every one; the key also has a BUILT id; untested distinct books among them: **0** |
| ...of which twins in the engine sense (same event stream) | n/a (never built) | their built counterpart is the canonical |
| distinct NY AM cell definitions in both lists | 4,557 (9,081 ids) | all 4,557 have at least one built id (2,621 keys built under 1 id, 1,936 under 2) |

## Cells built under BOTH ids (1,936 keys): duplicate work or different books?
| class | keys | evidence | engine set-months |
|---|---|---|---|
| IDENTICAL event stream (same ts, side, stop; 673 long-mode + 626 both-mode) | 1,299 | event-file comparison of every pair (ts, side, stop_pts identical); W-DEDUP twin map covers 1,661 of the 1,936 keys | duplicate side: 1,548 REPLACE-K7 first-look set-months already DONE (wasted), 3,628 unfinished lines still queued |
| DIFFERENT side mix: one id built BEFORE the mode fix (both-side events of a long/short cell), the other mode-correct (633 long + 4 short) | 637 | stream compared: e.g. Lfc41c8c2 18,222 events vs L30ae34bf 9,177 | NOT duplicates: different books (both-side valid per order 1014Z); DONE 877, queued 5,772 |

## Effect on the date and proposal (NOT applied, nothing queued or parked)
- NO untested book is hiding among the 2,588: nothing to add to the first-look queue; the ladder is 4,557 cells, all built; the first-look work left is the 27,435 queued REPLACE-K7 lines (unchanged).
- PROPOSAL for the lead / Josh: park the 3,628 unfinished first-look lines on the duplicate side of the 1,299 identical-stream pairs (list <tmp> same set of lines W-DEDUP's twin rule would park; keep the side with more DONE months): saves 3,628 set-months = ~0.8 h at 4,500/h; the 1,548 duplicate DONE set-months are sunk. The 637 mode-differing pairs stay (different books).
- The funnel denominators (D8_SPEC_STATUS / NY_AM_DATE_LINE) used 9,081 "cells": corrected to 4,557 distinct definitions (cell counts and the 26k-cell extrapolations shrink by half; set-month queues were always counted from the lines).
