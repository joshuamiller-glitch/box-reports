# STEP 0 for London and NY PM: coverage vs Asia / NY AM, and what was queued (W-STEP0, 2026-11-24 ~11:30Z)
Research queue only. No spend, no engine/mf_multi edit, no gate/rule/definition change, nothing deleted or parked.

## Finding
London and NY PM already had the SCREEN-level wide search (grid: ~10.7M / 11.75M cells, same R0 gate, 17-shape bracket first look, step 2a bare R0 at best shape, pool complete). The gap is the ENGINE first look list: ladder_cells.json (built by th_short/gcells.py from the local 2026-11-18 copy of pass_bare, read from /mnt/l2/l2vast/_grid/rule/) holds only a fraction of the family-bests that the pulled 2026-11-19 server-2 pass_bare files hold (same gate: reason=pass, persistence >= 0.60, trades >= 100, L3M > 0; the extra cells are mostly trig_levels_* cells from the stale-level re-run and cells of later grid partitions).

| session | grid cells | passers (pulled) | family-bests (pulled) | in ladder_cells.json = engine first look | R3 tested | NOT yet engine-looked |
|---|---|---|---|---|---|---|
| Asia | 9.80M | 6,487 | 3,847 | 1,890 (49%) | 3,936 | 2,051 (R3 tested, no engine rows) |
| NY AM | 11.74M | 24,702 | 11,460 | 4,556 (+1,390 both-side) | 11,767 | 7,226 |
| London | 10.74M | 3,158 | 2,237 | 808 (36%) | 806 | **1,462** (R3 untested) |
| NY PM | 11.75M | 1,638 | 1,168 | 396 (34%) | 393 | **782** (R3 untested; 468 of them sat in ladder_cells_old_seed.json with no state, never built) |

So per cell London/NY PM got the same engine treatment as Asia/NY AM (REPLACE first look L6M 808/808 London done; NY PM 233 of 396 complete, the rest in flight or in the RK7H holiday file; bracket step 2a London 609 of 656 candidates, 46 deliberately D8-invalid, 1 awaits CANC; NY PM 207 of 309). The coverage fraction of the pulled family-best list is LOWER for London (36%) and NY PM (34%) than for Asia (49%) and NY AM (40%), and R3 screen draws were never run on the extra London/NY PM cells (Asia/NY AM had them). Asia and NY AM have the SAME unbuilt remainder (2,051 / 7,226): flagged to LEAD, not built here (outside this order).

Not gaps (checked): ADD rows (replace-only policy, replace_only_park cron), other-book a2 rows (a2() returns 0 by order 1806Z), BASE/CANC all-new rows (Asia/NY AM stack candidates only), R0 at own bracket for cells whose own bracket is best (Asia 54/306, NY AM 86/1577 done: same hole everywhere), both-side B ids (NY AM only, bug restoration).

## What was added (same generators, same gates; only the input list differs)
* Lists (built by code/th_loneng/step0_cells.py: read-only copy of gcells.py logic and ordering, inputs pulled_rule, id = 'L'+md5(key)[:8] as gcells; cells already in ladder_cells.json removed): /mnt/l2/l2vast/_lon/ladder_cells_step0.json (London, 1,462 cells; modes long 1,251 / both 211; brackets plain60/60 581, sym15u 506, sym8u 101, asym20u/10u 91, asym10u/20u 75, sym30u 62, asym15u/30u 46) and /mnt/l2/l2vast/_nye/ladder_cells_step0_nypm.json (NY PM, 782 cells; both 552 / long 166 / short 64; sym15u 362, plain60/60 237, ...). Summary: _lon/ladder_cells_step0_summary.json. Void/stale excluded: 0. 1-minute and bmsg rows kept (the existing ladder keeps them too; D8 filters later).
* London FIRST: code/th_loneng/step0_lon_ladder.py runs lon_ladder.py unchanged (source executed with only the input path swapped), 4 shards, nice 12, started 11:2xZ; REPLACE-weakest (RM7) L6M rows, appended under flock ql_LON to /mnt/l2/l2vast/_lon/pending.txt (the existing London first-look file, already wired in QUEUES.txt and the mix3 London stream; london_session_next flag gives London 70% of the first-look share).
* NY PM SECOND: code/th_loneng/step0_nypm_chain.sh waits for the London builders to exit, then runs ny_ladder.py build --shard=i/3 unchanged with its own NY_LADDER_FILE switch; REPLACE-K7 L6M rows go to the DEDICATED file _nye/pending_nypm_step0.txt via code/th_loneng/step0_nypm_ladder.py (queue path swapped only; 4 shards nice 10; W-GRIDOPS wires it after _lon/pending.txt). London builders: 8 shards nice 10, ~166 rows/min.
* Rows: London 1,462 x 6 = 8,772 set-months, NY PM 782 x 6 = 4,692 (minus months already done/queued). Builders produce ~17 London cells/min, so rows arrive progressively (London build ~85 min, NY PM ~30-40 min after); fleet time at ~10k rows/h: London ~0.9 h, NY PM ~0.5 h.

## Not built / remains
* Stage-after-first-look for the new cells (prior years, controls, 17-shape grid jobs and step 2a R0BR, R3 draws) follow the normal chain only if W-SHORT/W-BRKT/ny_ladder advance pick the cells up: ladder_cells.json itself was NOT rewritten (W-SHORT's file); the proper fix is gcells.py reading the pulled pass_bare instead of the local 11-18 copy (that is a W-SHORT wiring change, not mine). Until then the new cells have first-look rows only.
* Asia 2,051 and NY AM 7,226 family-bests: same unbuilt remainder, not queued (order covers London/NY PM).
* 1 London candidate (vsess) waits for a CANC build; NY PM 81 step-2a candidates now have D8 events but brkt_night does not re-run (canc count unchanged): W-BRKT second pass for nypm would add 486 rows (brkt_second_pass.py nypm; not run by me because it rewrites the BRACKET_FIRSTLOOK page).
* No generator needed an engine or definition change.
