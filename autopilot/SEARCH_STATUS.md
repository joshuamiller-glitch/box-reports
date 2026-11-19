# SEARCH_STATUS - full-search programme (plan 1722Z: no Globex deadline), W-GRIDOPS, refreshed 2026-11-19 02:05Z

Plain words. Data end 2026-11-15 (NQ). Research only, no spend. Phases: 1 finish the whole search -> 2 prove it is not luck (30 controls, selection-corrected null, trust) -> 3 gates/layers one by one then jointly -> 4 D8 spec. Every number below is a screen-level number unless it says engine.

## Phase 1 - progress (the grid is not split by session: one job = one bar row x one trigger module x one tag; every session reads the same results, so the percentages below are the same for NY AM, NY PM, London and Asia)

| item | done | todo | jobs/hour (last 60 min) | ETA at that rate |
|---|---|---|---|---|
| pass 1, all tags (real + random-entry nulls 1/2 + extra null draws) | 132003 result files | 10998 jobs | 3652 | 3.0 h |
| pass 2 (family cells, exits a2, top cells) | n/a | 22992 (a top cells 648, a2 exit families 4165, c family cells 18179) | 982 | 23.4 h |

NOTE (18:40Z): the grid is partitioned over server 2 (rows 0-1 of 12), A (2-6) and B (7-11) by W-S3; finished results are merged into server 2 every ~5 min (lag <= 10 min), the todo and worker counts are summed over the three servers. A and B also see 172 bar rows that are complete on box 1 but not yet on server 2, so total todo is higher than the earlier single-server figure (about +50%).

Pass-1 results on disk by tag: real 60914, null draw 1 27545, null draw 2 27119, extra draws (3-25) 14088 files. Pass-1 results still waiting for their pass-2 upgrade: real 50194.

Machines (grid partitioned across servers): 207.188.7.103 load 116.96 workers 60; 109.94.96.39 load 131.52 workers 60; 206.223.224.21 load 120.78 workers 60; grid workers 180 (174 computing), engine workers 130; forward-path tables built (summed over servers) 583.

Since 17:23Z: pass-1 todo 80818 -> 10998 (-69820), pass-2 todo 25951 -> 22992 (-2959). Pass-2 todo grows when pass 1 delivers cells that earn pass 2.

## R4 - selection-corrected null of the whole search: FIVE draws, calibration check of the ladder (orders 1932Z + 2042Z; prereg sha 125fd12566e72aa6 + amendment)

What it is: 5 random-entry draws (tags p1rand1..p1rand5; draws 6-20 cancelled 20:42Z, files kept) of the SAME pass-1 search (every bar row x trigger module, same flags own-stop + account mask); the share of cells that pass R0-R3 in a null draw versus in the real search is the false-discovery rate, and the best cell of the null search versus the best of the real search is the best-pick comparison. Draws 1-2 run inside the real loops, draws 3-5 in dedicated null loops (A rows 2-6: 24 workers, B rows 7-11: 24 workers, server 2 rows 0-1: 6 workers; nice 8-10, below the engine (nice 0) and R3 (nice 5)). The null cells are also pushed through the same ladder R0-R3 as a CALIBRATION CHECK of the false-discovery rate the ladder claims. Only accepted draws count (null audit: independent side draw, pooled mean pts/trade at plain 60/60 negative and above -6 in every session, identical share under 1%, coverage at least 80%).

| item | now |
|---|---|
| results/hour, REAL search (p1real files, pass 1 and 2 together) | 1956 |
| results/hour, NULL draws (p1rand1..20 files) | 1841 |
| null result files on disk, draws 1 / 2 | 27545 / 27119 (real: 60914) |
| null result files, draws 3-20 (all) | 13585 |
| share of the (row, module) files complete incl. error stubs, per draw (total ~65.8k jobs per draw; grid is not split by session, so every session sees the same share) | draw 1 44%, draw 2 44%, draw 3 4%, draw 4 4%, draw 5 4% |
| draws complete (files incl. error stubs >= 99.5 percent of ~65.8k) | 0 of 5 |
| draws accepted by the null audit and counted | see null_summary below |

Estimate: about 18 more full draws at the null share of the fleet (64 threads, ~25% of A + B) is roughly 60 hours (about 4,000 core-hours at the measured pass-1 rate; the order estimated ~6,300 core-hours); if that needs more than ~48 h the null share can be raised at the cost of the real search or machines added (Josh decides). False-discovery rate per session and the best-pick comparison appear here when W-SHORT has run the rule on the first accepted draws.

### False-discovery counts (W-SHORT, rule/null_summary.md: per accepted null draw per session, null cells passing vs the real search on the SAME coverage; ratio null/real = false-discovery ratio)

# NULL DRAWS vs REAL (same coverage) - cells passing R0 (bare) per session, W-SHORT 02:01Z

| tag | audit | Asia null / real (ratio) | London null / real (ratio) | NYAM null / real (ratio) | NYPM null / real (ratio) |
|---|---|---|---|---|---|

## Grid / engine split per host (order 1932Z item 3; caps owned by W-S3)

Priorities by nice since 22:25Z (order 2218Z): engine slots nice 0 (lead sets) < real pass 1 nice 1 < R3 stages nice 5 (W-SHORT) < pass 2 + exits nice 8 < null draws 1-2 nice 10 < null draws 3-5 nice 12 (parked: 0 workers until draws 1-2 are done) < exit-yield nice 15. Row split: Dallas 0,1,6,11 / A 2,3,4,5 / B 7,8,9,10 of 12. Workers (real p1 / p2 / null 1-2): A 52 / 18 / 26, B 52 / 20 / 26, Dallas 24 / 8 / 12. The filler cron is paused (machines are oversubscribed by R3 + engine). The actual numbers are in the Machines table below.

## ETAs after the 22:25Z priority fix (order 2218Z; static estimates computed 22:25Z; live rates are in the tables above)

Remaining (grid todo function, pass 1 coarse, 22:21Z): REAL pass-1 cells 14.7k jobs (Dallas 1.2k, A 9.7k, B 3.8k before the row move); null draws 1-2 95.5k; null draws 3-5 ~200k; pass 2 + exit families ~26k heavy jobs. The remaining real cells are the heavy fine-bar rows (many bars per row): about 20 jobs per worker-hour, not the 60 of the early fast rows.

Why the real rate fell (measured 22:15Z): A and B ran at load 300-365 on 128 threads: R3 stages (W-SHORT) 192 processes + engine 56 + exit-yield 24 + grid 92; the real loops were at nice 10 (weight 110) against R3 at nice 5 (335) and engine at nice 0 (1024), so real pass 1 got ~2% of the CPU per process of the others; Dallas ran its real loop at nice 0 but had finished most of its own real cells (179 real/h, draws 1-2 at 1.5k/h). Fixed 22:25Z by nice: engine 0 < real pass 1 (nice 1) < R3 (5) < pass 2 + exits (8) < null draws 1-2 (10) < null draws 3-5 (12, parked for now) < exit-yield (15).

| item | estimate |
|---|---|
| REAL pass 1 end (14.7k jobs, ~3-4k jobs/h expected with nice 1; ~2k/h if the share does not improve) | ~4-7 h: about Nov 19 03:00-06:00Z (earlier than the 13:30Z planned); measured at 23:30Z |
| pass 2 + exit families end (~26k heavy jobs at nice 8, 46 workers) | ~30 h (Nov 20 ~04:00Z) unless R3 load drops |
| null draws 1 and 2 (95.5k jobs, 64 workers at nice 10, draws 3-5 parked): both draws are one loop, so they finish together | ~25 h at 60 jobs/h per worker if CPU is available (Nov 19 ~23:00Z), up to ~50 h under the present load; the grid is not split by session, so draw 1 completes for ALL sessions at once; W-SHORT evaluates sessions in clock order (Asia, London, NY AM, NY PM) |
| null draws 3-5 (~200k jobs) | start after draws 1-2 (or when real pass 1 ends and cores free up); ETA moves with that |

Dallas (64 threads) now also owns rows 6 and 11 (from A and B) so its queue is ~15+ h: Dallas real 24 + pass 2 8 + draws 1-2 12 workers. The error stubs: see MORNING.md 22:30Z note (book/tape modules on rows without a book store: now skipped as not applicable, no stub).

## Stale level results (modules trig_levels_*: results written before 2026-11-18 06:00Z are stale; forced re-run since 01:33Z Dallas, ~02:30Z Frankfurt and Singapore)

| host | stale real | stale null draw 1 | stale null draw 2 | fresh level files (real / draw 1 / draw 2) |
|---|---|---|---|---|
| Dallas | 4573 | 4512 | 4527 | 17411 / 5794 / 5612 |
| Frankfurt | 2997 | 2191 | 2189 | 6224 / 1931 / 1909 |
| Singapore | 3030 | 1791 | 1790 | 6598 / 1803 / 1722 |

Counts are the files on each host before the merge (A and B results are copied to Dallas every ~5 min); a host shows 0 stale for its own rows when its re-run is complete. Old copies of other hosts rows still on Dallas disappear as the merge overwrites them.

## Machines (hourly; busy % is measured from /proc/stat against the REAL thread count of each machine)

| machine | real threads | busy % | load1 | grid workers (computing) | engine workers | re-rank/other workers | results/hour (this machine) |
|---|---|---|---|---|---|---|---|
| server 2 Dallas | 64 | 100.0 | 116.96 | 180 (174) | 65 | 0 | 4634 |
| A Frankfurt | 128 | 98.6 | 131.52 | 60 (60) | 28 | 0 | 2381 |
| B Singapore | 128 | 95.1 | 120.78 | 60 (60) | 25 | 0 | 1227 |
| box 1 London (lead, engine fillers) | 32 | 100 | 68.32 | 0 | see CORES.md | - | - |

Server 2 has 64 threads (SMT off in firmware, order 1830Z check), A and B 128 each, box 1 32. Total jobs/hour and the phase-1 ETA are in the table above (sum over servers; double counting warning applies until W-S3 merges results). Any machine under 85% busy for 3 readings with work pending gets a one-line explanation in MORNING.md.

## Blocked / cannot run (listed, not skipped silently)

Failed jobs leave an error stub that the loop retries after 4 hours (older stubs are retried automatically). Error files on disk: {'real': 355, 'p1real': 1711, 'p1rand1': 1556, 'p1rand2': 1512, 'p1rand3': 16, 'p1rand4': 16, 'p1rand5': 16}.

| module | failures (files) | why |
|---|---|---|
| trig_book_ofi | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_cancel | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_ice | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_queue | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_pslope | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_dwm | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_imb | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_micro | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_thin | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_wall | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_sweep | 308 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_block | 301 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_run | 301 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_unfinished | 300 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_stack | 300 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_sizemix | 300 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_levels_sd5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sd15 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sd60 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib60 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sdx5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sdx15 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib15 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sdx3 | 19 | all signal calls raised (cause needs a test) |

## Phase 2 / 3 (running in parallel, from the 1722Z order)

- NY leads to the full standard: WP10 (NY PM money flow, keep K7 and add) and XA3 (NY AM VWAP retest on 5000-tick): autopilot/NEW_BOOK_ENGINE.md. London replacement programme: NEW_BOOK_ENGINE_LONDON.md. Near-target K7 lock controls: DS3_NEAR_TARGET.md. ORB fade controls: DS3_ORB_FADE_LEAD.md.
- Shortlist (bare, equal risk) and its trust audit: NEW_BOOK_SHORTLIST.md. Look-ahead gate for every reversal-type bar: BAR_LOOKAHEAD_GATE.md (all passed).
- Account-rule scoring (DAY-DONE mask from the JL3 day-state): in progress by W-DAYMASK; the side-by-side ranking appears below when its file exists.

## Survivor rule (order 1845Z: NO CAP, rule-based, no top-N anywhere)

A cell goes forward to phases 2-3 if ALL of these hold, judged on the OWN-STOP ranking (stack-independent) with bare and current-stack mask shown beside it:
- positive over the last 6 months (26 weeks to the data end) AND over the last 3 months beside it, on EQUAL RISK (R = points / the cell stop in points);
- prior years 2023 / 2024 / 2025 not a disaster: AMBER = 15-30% worse than the reference (shown, still goes forward flagged), RED = more than 30% worse (shown, NOT delivered as a pick);
- persistence over 60% (share of 2-week periods positive in the rolling pick); at least 100 trades in the last 6 months;
- passes the trust audit (brute-force re-simulation, 6 truncation cuts, fills at least signal + 1 s) and the look-ahead gate.
Engine capacity decides the ORDER cells are tested in (best first), never WHETHER a passing cell is tested. If the count makes phases 2-3 long, the count and the hours are reported here; nothing is trimmed. Near-duplicates (the same trigger on neighbouring bar sizes or parameters) are grouped as one FAMILY for the engine: best member first, neighbours listed with their screen numbers and run after, nothing dropped. Cells that fail the rule stay on disk with the reason so a later 2-week refit can pick them up.

### Counts passing per session (from SURVIVOR_COUNTS.md, W-SHORT)

# SURVIVOR_COUNTS - the LADDER (cheapest test first; W-SHORT, orders 1845Z + 1932Z), refreshed 2026-11-19 02:00Z

No top-N cap anywhere. A cell leaves only by FAILING a test. Counts are bare (R0) from server-2 results only and PROVISIONAL (grid partitioned over servers until W-S3 merges; data week 189). Rungs not yet run say "n/a (reason)", never zero.

THRESHOLDS (equal risk; R = points / stop, stop = clip(bracket multiple x row bar unit, 10, 120), plain 60/60 = 60): R0 L6M (26 w) > 0; >= 100 trades in L6M; L3M (13 w) > 0; persistence > 0.60 (2-week windows since 2023-10 positive); prior years 2023/24/25 R per week not more than 30% below the cell's own L6M R per week (RED = shown, not delivered; AMBER 15-30% passes, counted). R1 = the same thresholds on the OWN-STOP result (2 stops; 1.5 / 3 shown): cells passing R0 but failing R1 are KEPT and labelled "depends on today's stack". R2 trust (brute-force tape walk) + look-ahead (6 truncation cuts) + fills >= signal + 1 s. R3 30 same-bracket random-entry draws, screen level: PASS = beats >= 27 of 30 (count shown at 24 / 27 / 29). R4 selection-corrected null of the same search (5 full null draws, same own-stop flags; calibration check of R0-R3 on null cells). R5 exact engine, staged.

FAMILIES = connected components of the grid neighbour graph over passing cells (same module.variant on an adjacent bar size of the same bar type, adjacent parameter of the same variant, or the identical parameter with another bracket / side); the best member (highest min(L6M R/wk, weakest prior-year R/wk)) runs first, neighbours after; nothing is dropped.

FLEET: 352 threads (Dallas 64, Frankfurt 128, Singapore 128, box 1 32), 90% busy assumed = 317 screen cores; engine set-months/hour measured 763 (box 1 450 + Dallas 313; A and B have no engine runs yet), projected 2894 with A and B engine-ready (ENGINE_PLAN.md s.11). Unit costs measured on WP10 / XA3 (PHASE2_TOOLING_TEST.md): R2 ~12 CPU-s per cell; R3 ~0.31 core-h per (row, module) pair (30 draws; cells sharing a pair share the draws); R4 ~317 core-h per full null draw = ~1,585 core-h for the 5 draws now planned (order 2042Z; shared by all four sessions; W-GRIDOPS ETA: draws 1-2 inside the real loops ~16 h, draws 3-5 ~62 h at the 25 percent share or ~30 h once real pass 1 is done); R5 engine 0.05 core-h per set-month measured on box 1 / Dallas (Frankfurt measured ~0.30: 1,072 s per month, starved), R5 stage a = 12 set-months per family (L6M as ADD and as replacement of the weakest live book), prior years +72, 30 date-shift controls +180 set-months (7.8 core-h at 0.043). All "hours" below are UPPER BOUNDS (no cell has failed R1-R3 yet) and assume the whole fleet for screen rungs (R4: its 25 percent share of A + B) and the measured 763 set-months/h for the engine.

## UNVERIFIED (stale level result) - notice, refreshed 02:00Z UTC

trig_levels_* grid results written BEFORE 2026-11-18 06:00Z predate the level-module fixes (13 of 17 level modules differ on a fresh re-run, W-GRIDOPS 0145Z); they are being re-run (Dallas from 01:33Z, Frankfurt / Singapore ~02:30Z, null draws 1-2 last). Until the result stamp (code hash on every result file) exists, every row below that touches a level module and a pre-06:00Z result is **UNVERIFIED (stale level result)**; non-level modules are not known to be affected (all-module check pending, order 0143Z). Stage-A p-values of R3 are computed with the CURRENT module code (fresh), but the cell SELECTION (R0) used the stale grid result; cells whose fresh L6M differs from the grid L6M by > 1 point are VOID (excluded).

| session | R0 passing cells | of which stale level cells | family-bests | stale family-bests | real-on-null-coverage tested (stage A) | stale level cells there | null draw tested (stage A) | stale level cells there |
|---|---|---|---|---|---|---|---|---|
| Asia | 4,541 | 211 (4.6%) | 2,902 | 116 | 900 | 40 (4%) | 245 | 50 (20%) |
| London | 2,177 | 51 (2.3%) | 1,672 | 42 | 304 | 15 (5%) | 249 | 41 (16%) |
| NYAM | 15,834 | 924 (5.8%) | 8,510 | 483 | 542 | 48 (9%) | 250 | 63 (25%) |
| NYPM | 1,152 | 17 (1.5%) | 861 | 16 | 191 | 5 (3%) | 230 | 46 (20%) |

Reading: the stale share is NOT symmetric in the calibration: among tested family-bests 3-11% of the real-search cells but 17-26% of the null-draw cells rest on pre-06:00Z level files (the null draws were run early with the old level code), so the 01:16Z FDR table can be biased by the stale null side; it is redone after the forced re-run of draws 1-2 (last in the queue).


## Asia
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 6,461,292 | - | 6,456,751 | by first rule: R1 L6M<=0 3,461,640; R2 trades<100 1,395,903; R3 L3M<=0 526,793; R4 persistence<=0.60 945,197; RED prior year 127,218 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 4,541 (R0 passers) | 2,902 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 15.1 core-h for 4,541 cells | 0.0 h |
| R2 | trust + look-ahead | 4,541 (upper bound: all R1 cells) | 2,902 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 629 core-h for 2,030 (row, module) pairs | 2.0 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 4,541 (upper bound) | 2,902 | RUNNING: stage A (30 draws, same bracket, equal-risk) 1,885 of 2,902 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 521 / 182 / 31; reached stage B (200 draws) 379, C (1,000) 29, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 2,902 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 1231 / 1618 at q 5% / 10% / 20% | SET 1: 0, SET 2: 1231 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 34,824 set-months = 1741 core-h | 45.6 h on the measured fleet (763/h), 12.0 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 2,902 families (upper bound) | 2,902 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+208,944 set-months) then 30 date-shift controls (+522,360 set-months = 26118 core-h) for the rows still alive | **274 h (> 48 h: Josh decides between more machines and waiting)** / **685 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 6,461,292; PASS **4,541 cells in 2,902 families** (non-reversal bars 3103, reversal 1082 (provisional until the look-ahead gate), other 356; level / S-D modules 1769; AMBER prior year(s) 847). Distinct (row, module) files among the passers: 2,030.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_Asia.parquet; passing cells with family id / order / rank in family: pass_bare_Asia.csv.

## London
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 7,329,472 | - | 7,327,295 | by first rule: R1 L6M<=0 4,123,672; R2 trades<100 1,740,334; R3 L3M<=0 488,397; R4 persistence<=0.60 893,506; RED prior year 81,386 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 2,177 (R0 passers) | 1,672 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 7.3 core-h for 2,177 cells | 0.0 h |
| R2 | trust + look-ahead | 2,177 (upper bound: all R1 cells) | 1,672 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 418 core-h for 1,348 (row, module) pairs | 1.3 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 2,177 (upper bound) | 1,672 | RUNNING: stage A (30 draws, same bracket, equal-risk) 806 of 1,672 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 49 / 9 / 2; reached stage B (200 draws) 38, C (1,000) 0, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 1,672 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 0 / 304 at q 5% / 10% / 20% | SET 1: 0, SET 2: 0 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 20,064 set-months = 1003 core-h | 26.3 h on the measured fleet (763/h), 6.9 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 1,672 families (upper bound) | 1,672 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+120,384 set-months) then 30 date-shift controls (+300,960 set-months = 15048 core-h) for the rows still alive | **158 h (> 48 h: Josh decides between more machines and waiting)** / **394 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 7,329,472; PASS **2,177 cells in 1,672 families** (non-reversal bars 1350, reversal 329 (provisional until the look-ahead gate), other 498; level / S-D modules 798; AMBER prior year(s) 470). Distinct (row, module) files among the passers: 1,348.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_London.parquet; passing cells with family id / order / rank in family: pass_bare_London.csv.

## NYAM
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 8,027,865 | - | 8,012,031 | by first rule: R1 L6M<=0 4,785,951; R2 trades<100 1,102,417; R3 L3M<=0 632,439; R4 persistence<=0.60 1,374,346; RED prior year 116,878 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 15,834 (R0 passers) | 8,510 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 52.8 core-h for 15,834 cells | 0.2 h |
| R2 | trust + look-ahead | 15,834 (upper bound: all R1 cells) | 8,510 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 1667 core-h for 5,376 (row, module) pairs | 5.3 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 15,834 (upper bound) | 8,510 | RUNNING: stage A (30 draws, same bracket, equal-risk) 4,542 of 8,510 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 571 / 164 / 44; reached stage B (200 draws) 1207, C (1,000) 61, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 8,510 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 3467 / 4220 at q 5% / 10% / 20% | SET 1: 0, SET 2: 3467 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 102,120 set-months = 5106 core-h | **134 h (> 48 h: Josh decides between more machines and waiting)** on the measured fleet (763/h), 35.3 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 8,510 families (upper bound) | 8,510 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+612,720 set-months) then 30 date-shift controls (+1,531,800 set-months = 76590 core-h) for the rows still alive | **803 h (> 48 h: Josh decides between more machines and waiting)** / **2008 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 8,027,865; PASS **15,834 cells in 8,510 families** (non-reversal bars 9898, reversal 3308 (provisional until the look-ahead gate), other 2628; level / S-D modules 8288; AMBER prior year(s) 2710). Distinct (row, module) files among the passers: 5,376.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYAM.parquet; passing cells with family id / order / rank in family: pass_bare_NYAM.csv.

## NYPM
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 8,043,245 | - | 8,042,093 | by first rule: R1 L6M<=0 4,336,708; R2 trades<100 1,739,114; R3 L3M<=0 532,730; R4 persistence<=0.60 1,408,416; RED prior year 25,125 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 1,152 (R0 passers) | 861 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 3.8 core-h for 1,152 cells | 0.0 h |
| R2 | trust + look-ahead | 1,152 (upper bound: all R1 cells) | 861 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 229 core-h for 740 (row, module) pairs | 0.7 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 1,152 (upper bound) | 861 | RUNNING: stage A (30 draws, same bracket, equal-risk) 393 of 861 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 92 / 65 / 32; reached stage B (200 draws) 177, C (1,000) 0, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 861 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 296 / 367 at q 5% / 10% / 20% | SET 1: 0, SET 2: 296 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 10,332 set-months = 517 core-h | 13.5 h on the measured fleet (763/h), 3.6 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 861 families (upper bound) | 861 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+61,992 set-months) then 30 date-shift controls (+154,980 set-months = 7749 core-h) for the rows still alive | **81 h (> 48 h: Josh decides between more machines and waiting)** / **203 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 8,043,245; PASS **1,152 cells in 861 families** (non-reversal bars 743, reversal 118 (provisional until the look-ahead gate), other 291; level / S-D modules 271; AMBER prior year(s) 243). Distinct (row, module) files among the passers: 740.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYPM.parquet; passing cells with family id / order / rank in family: pass_bare_NYPM.csv.

## R3 PASS SETS side by side (Benjamini-Hochberg across ALL family-bests of the session; untested cells count as p = 1; the counts grow as draws complete)

SET 1 (strict, current rule) = inside BH on p_L6M (last 26 weeks, equal-risk sum of R). SET 2 (proposed, order 2057Z) = inside BH on p_ALL (whole history, first month to today, L6M included) AND still passing R0 / R1 unchanged (every cell here already passed R0; R1 own-stop pending). Cells in SET 2 with p_L6M > 0.20 are flagged "recent no better than random" (shown, not dropped). p = (1 + k) / (1 + n), k = random draws at least as good, n = draws; weakest prior-year p shown separately. Engine order: SET 1 first, then SET 2 members best p first, no cap; Josh decides which set is the pass rule. Engine cost per passer: R5a 12 set-months + prior years 72 + 30 date-shift controls 180 = 264 set-months = ~13 core-h = 0.35 h at the measured 763 set-months/h. Dated D8 spec estimate: W-PLAN, ENGINE_PLAN.md.

| session | family-bests | tested | SET 1 q5 / q10 / q20 | SET 1 expected false (q10) | SET 1 engine core-h / h | SET 2 q5 / q10 / q20 | SET 2 expected false (q10) | SET 2 engine core-h / h | SET 2 flagged recent no better than random (q10) | smallest p: L6M / ALL |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,890 | 1,885 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 1231 / 1618 | 123.1 | 16249 / 425.9 h | 912 | 0.0249 / 0.0003 |
| London | 808 | 806 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 0 / 304 | 0.0 | 0 / 0.0 h | 0 | 0.0645 / 0.0100 |
| NYAM | 4,556 | 4,542 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 3467 / 4220 | 346.7 | 45764 / 1199.6 h | 3091 | 0.0299 / 0.0002 |
| NYPM | 396 | 393 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 296 / 367 | 29.6 | 3907 / 102.4 h | 226 | 0.0199 / 0.0050 |

## CALIBRATION: measured false-discovery rate from the whole-search null (order 2218Z, partial draw 1)

Label: PARTIAL / coarse (draw p1rand1 only, files that exist so far; the real search is restricted to the same (row, module) files and the pass-1 coverage; one family definition: same file + parameter). FDR(b) = expected null family-bests / real family-bests at the threshold "beats >= b of 30 draws" (p <= (31 - b + 1) / 31). Stage A only (30 draws): the finest p reachable is 0.032, so FDR <= 10% can only be read where it shows below.

| session | R0 pass cells null / real (ratio) | R0 families null / real | tested null / real (sampled family-bests) | stat | b = 24 | 27 | 29 | 30 |
|---|---|---|---|---|---|---|---|---|
| Asia | 380 / 963 (0.39) | 372 / 904 | 245 / 900 | p_L6M (null / real families at threshold = FDR) | 100 / 281 = 36% | 32 / 93 = 34% | 15 / 13 = 116% | 9 / 2 = 453% |
|  |  /  (0.00) |  /  | 245 / 900 | p_ALL (null / real families at threshold = FDR) | 237 / 840 = 28% | 173 / 744 = 23% | 117 / 604 = 19% | 73 / 428 = 17% |
| London | 466 / 347 (1.34) | 457 / 335 | 249 / 304 | p_L6M (null / real families at threshold = FDR) | 48 / 19 = 255% | 18 / 3 = 555% | 4 / 2 = 167% | 4 / 0 = n/a |
|  |  /  (0.00) |  /  | 249 / 304 | p_ALL (null / real families at threshold = FDR) | 319 / 266 = 120% | 239 / 203 = 118% | 162 / 127 = 127% | 99 / 96 = 103% |
| NYAM | 763 / 1,915 (0.40) | 730 / 1,821 | 250 / 542 | p_L6M (null / real families at threshold = FDR) | 79 / 245 = 32% | 44 / 84 = 52% | 12 / 30 = 39% | 6 / 10 = 58% |
|  |  /  (0.00) |  /  | 250 / 542 | p_ALL (null / real families at threshold = FDR) | 491 / 1737 = 28% | 400 / 1609 = 25% | 298 / 1324 = 22% | 181 / 1038 = 17% |
| NYPM | 238 / 195 (1.22) | 233 / 193 | 230 / 191 | p_L6M (null / real families at threshold = FDR) | 55 / 45 = 120% | 31 / 31 = 100% | 10 / 17 = 59% | 4 / 9 = 45% |
|  |  /  (0.00) |  /  | 230 / 191 | p_ALL (null / real families at threshold = FDR) | 186 / 188 = 99% | 167 / 176 = 95% | 137 / 131 = 104% | 99 / 92 = 108% |

Reading: FDR above 100% = the null produces MORE family-bests than the real search at that threshold (no signal there); a threshold with FDR <= 10% (5% / 20%) is the calibrated pass rule for that session on that statistic. With only 30 draws per cell the table is coarse; stages B/C/D and draws 2-5 refine it.

## LIVE BOOKS AS REFERENCE (W-LIVEREF, 2026-11-19 01:41Z)

Each live D7 book run BARE (its own signal_fn from code/th_swap, on its live bar row: K7 tm180, M7 tm60, U7 tm600, P7/H7/A7/O7 tm60 with nom_s=60), plain 60/60 bracket, both sides, NO layers, through the same R0, own-stop (N = 1.5/2/3 stops per label day), and stages A/B/C of the R3 machinery: 30 / 200 / 1,000 same-count random-entry draws (seeds crc32(row+'live7_<BOOK>'+'r3rand<n>'+'0'), same gjob2.rand_signals), p = (1+k)/(1+n) on the last-26-week equal-risk R sum (stop 60), weakest-prior-year p on the minimum of the 2023/24/25 R per week. 'beats of 30' = draws strictly below the real series. Last data week index 189. Code: code/th_liveref/lr_run.py; raw JSON /mnt/l2/l2vast/_grid/liveref/ (Dallas).

| book | session | L6M trades | R0 pass? | own-stop (R1) pass? (1.5/2/3) | beats of 30 | p at 200 | p at 1,000 | weakest-prior-year p | L6M R | L6M pts | live engine $/wk (engine lots) | x1.75 live lots |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | Asia | 366 | fail | n/n/n | 22 | 0.299 | 0.3257 | 0.050 | -3.7 | -224 | 846 (n=373, 1 lot) | 1,480 |
| A7 | London (not traded live) | 336 | fail | n/n/n | 17 | 0.423 | 0.3916 | 0.259 | 2.9 | 173 | - | - |
| A7 | NYAM (not traded live) | 244 | fail | n/n/n | 11 | 0.612 | 0.5764 | 0.496 | -0.4 | -23 | - | - |
| A7 | NYPM (not traded live) | 204 | fail | n/n/n | 6 | 0.905 | 0.9001 | 0.900 | -23.8 | -1431 | - | - |
| H7 | Asia | 138 | fail | n/n/n | 27 | 0.109 | 0.0929 | 0.238 | 13.0 | 781 | 1,772 (n=143, 2 lot) | 3,101 |
| H7 | London (not traded live) | 133 | fail | n/n/n | 25 | 0.403 | 0.4236 | 0.086 | 1.7 | 104 | - | - |
| H7 | NYAM | 86 | fail | n/n/n | 28 | 0.045 | 0.0360 | 0.869 | 14.5 | 867 | 325 (n=38, 1 lot) | 569 |
| H7 | NYPM (not traded live) | 84 | fail | n/n/n | 14 | 0.562 | 0.5544 | 0.855 | -2.7 | -159 | - | - |
| K7 | Asia | 683 | fail | n/n/n | 28 | 0.025 | 0.0380 | 0.529 | 31.3 | 1875 | 3,416 (n=843, 1 lot) | 5,979 |
| K7 | London | 583 | fail | n/n/n | 5 | 0.761 | 0.7822 | 0.282 | -22.9 | -1371 | -175 (n=458, 1 lot) | -306 |
| K7 | NYAM | 509 | fail | n/n/n | 4 | 0.905 | 0.9161 | 0.270 | -32.7 | -1964 | -378 (n=187, 1 lot) | -662 |
| K7 | NYPM | 476 | fail | n/n/n | 13 | 0.627 | 0.6204 | 0.574 | -9.7 | -584 | 586 (n=156, 1 lot) | 1,025 |
| M7 | Asia (not traded live) | 593 | fail | n/n/n | 29 | 0.020 | 0.0220 | 0.005 | 35.0 | 2102 | - | - |
| M7 | London | 527 | fail | n/n/n | 11 | 0.682 | 0.7053 | 0.947 | -17.2 | -1030 | -380 (n=515, 1 lot) | -666 |
| M7 | NYAM | 469 | fail | n/n/n | 17 | 0.453 | 0.5015 | 0.033 | -3.9 | -232 | 417 (n=227, 1 lot) | 731 |
| M7 | NYPM (not traded live) | 410 | fail | n/n/n | 11 | 0.701 | 0.7103 | 0.423 | -15.9 | -956 | - | - |
| O7 | Asia (not traded live) | 0 | fail | n/n/n | 0 | 1.000 | 1.0000 | 1.000 | 0.0 | 0 | - | - |
| O7 | London (not traded live) | 0 | fail | n/n/n | 0 | 1.000 | 1.0000 | 1.000 | 0.0 | 0 | - | - |
| O7 | NYAM | 65 | fail | n/n/n | 21 | 0.234 | 0.2408 | 0.005 | 4.5 | 269 | 279 (n=45, 1 lot) | 488 |
| O7 | NYPM (not traded live) | 0 | fail | n/n/n | 0 | 1.000 | 1.0000 | 1.000 | 0.0 | 0 | - | - |
| P7 | Asia | 658 | fail | n/n/n | 28 | 0.040 | 0.0500 | 0.247 | 30.6 | 1838 | 8,919 (n=599, 2 lot) | 15,609 |
| P7 | London | 547 | fail | n/n/n | 27 | 0.080 | 0.0789 | 0.722 | 26.1 | 1568 | 998 (n=398, 1 lot) | 1,746 |
| P7 | NYAM | 523 | fail | n/n/n | 0 | 0.896 | 0.8711 | 0.466 | -31.0 | -1862 | 284 (n=43, 1 lot) | 497 |
| P7 | NYPM (not traded live) | 451 | fail | n/n/n | 11 | 0.637 | 0.6164 | 0.946 | -11.4 | -684 | - | - |
| U7 | Asia | 153 | fail | n/n/n | 26 | 0.075 | 0.0679 | 0.047 | 15.3 | 921 | 1,731 (n=155, 2 lot) | 3,029 |
| U7 | London | 131 | fail | n/n/n | 8 | 0.711 | 0.6703 | 0.678 | -4.6 | -277 | 1,093 (n=105, 2 lot) | 1,912 |
| U7 | NYAM (not traded live) | 80 | fail | n/n/n | 14 | 0.652 | 0.7093 | 0.006 | -4.9 | -296 | - | - |
| U7 | NYPM (not traded live) | 39 | fail | n/n/n | 18 | 0.318 | 0.3257 | 0.613 | 2.1 | 124 | - | - |

### Reading it
- No book passes R0 in any session. K7 Asia, P7 Asia/London, M7 Asia (not traded live), H7 NYAM have p(1,000) <= 0.05 on the L6M test, but each fails another R0 clause (prior-year RED in all of 2023-25 for K7 Asia; persistence < 0.60), so as a grid cell they would not survive. The live books are NOT better than the grid survivors on this test; Asia is where they look alive (K7, P7, M7, H7, U7).
- London K7/M7/U7, NYAM K7/P7 bare are negative on plain 60/60: the live dollars in those sessions come from the live bracket/exits/layers, not from the bare trigger.
- Engine $/wk is the JL3 exact engine, last 26 weeks to 2026-11-13 (net of fees, engine base lots; x1.75 = live lot multiplier), NEW_BOOK_ENGINE.md style. It is NOT comparable in size to the bare R column: the bare test is plain 60/60 with no layers.

### Caveats (honest)
- First-order screen. Brackets: live brackets differ (K7 59, P7 58, M7 59.5, engine 60); the harness uses plain 60/60 on every book, so this tests the trigger, not the live exit logic. Live exits (EMA/Supertrend/HMA lines, trails, near-target, cuts) are not in the test. H7's trail line is the HMA20 PROXY and is not used here at all.
- Fills/slippage as the harness ($4.84 RT, first print after bar close). P7/H7/A7/O7 are aggregated inside their signal functions from a 1-min base (tm60, nom_s=60); that matches the live aggregation by construction in th_swb/adapt but was not independently proven on this run. The live bar row for K7 is the tm180 clock-aligned grid row, M7 tm60, U7 tm600.
- The seven books are single parameter sets (live defaults); there is no selection, so the p-values are plain one-test p-values with no search penalty (they are not comparable to the family-best p-values of searched cells, which carry multiplicity).
- O7 trades only NYAM (09:30 start); zero signals in other sessions is by design. Sessions marked 'not traded live' are shown for completeness (the JL3 engine has no live trades there). Live engine session = the entry session in the JL3 trades.
- Own-stop columns use the grid table path (forward-path table) at N = 1.5/2/3; 'n' = fails R0 at that N.

## CALIBRATION BY FAMILY (order 0125Z; same footing as the table above: null draw 1 through the same stage A, p_L6M and p_ALL)

**UNVERIFIED FOR ALL "levels:*" TRIGGER FAMILIES (W-GRIDOPS 0145Z)**: trig_levels_* results written before 2026-11-18 06:00Z predate the level-module fixes (13 of 17 level modules differ on a fresh re-run); real AND null level cells are partly stale until the forced re-run lands (Dallas from 01:33Z, Frankfurt / Singapore ~02:30Z); read the levels:* rows as provisional and treat level-cell rows on the ladder lists as UNVERIFIED (ranked after verified cells). FDR(b) = null family-bests beating >= b of 30 draws / real family-bests beating >= b, per trigger family, bar family and (trigger x bar) block; counts are scaled to ALL family-bests of each set when only a part is tested (tested n shown). b = 24 / 27 shown on p_L6M with p_ALL beside. FDR < 100% = real > null; a block with real >> null is where the engine and the deeper stages go first; null >= real = last, not dropped. A block needs >= 5 real family-bests at b = 24 to be ranked (small counts give an unstable ratio). The best-of-many effect is shown by the number of blocks tested.

### Asia (real tested 900 of 904 family-bests, null tested 245 of 372)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| pullback | 34 / 4 | 18 | 0 | 0% | 0% | 33 | 3 | 9% |
| bands | 139 / 21 | 61 | 9 | 15% | 19% | 137 | 24 | 18% |
| session structure | 46 / 9 | 9 | 2 | 17% |  | 39 | 9 | 23% |
| levels:Fibonacci | 111 / 23 | 37 | 9 | 25% | 0% | 96 | 21 | 22% |
| momentum | 142 / 18 | 47 | 12 | 26% | 19% | 136 | 21 | 16% |
| levels:VWAP | 43 / 9 | 8 | 3 | 38% |  | 40 | 8 | 19% |
| levels:swing S/R, trendline, channel | 32 / 9 | 11 | 5 | 41% |  | 28 | 9 | 32% |
| levels:session / prior / round / opens / gaps | 61 / 17 | 10 | 5 | 45% |  | 57 | 15 | 27% |
| tape / order flow | 41 / 13 | 12 | 6 | 50% | 76% | 39 | 14 | 35% |
| levels:profile / stack / walls / UW | 46 / 10 | 6 | 3 | 50% |  | 45 | 9 | 20% |
| trend | 89 / 28 | 27 | 15 | 56% | 101% | 85 | 33 | 39% |
| cross-market | 26 / 15 | 15 | 14 | 91% | 30% | 22 | 21 | 96% |
| bar-native | 15 / 1 | 2 | 2 |  |  | 15 | 2 | 10% |
| confluence | 4 / 1 | 2 | 0 |  |  | 4 | 2 |  |
| levels:pivots | 17 / 6 | 4 | 0 |  |  | 15 | 3 | 20% |
| levels:zones / supply-demand | 14 / 35 | 2 | 5 |  |  | 11 | 15 | 137% |
| mean reversion / manual indicators | 13 / 8 | 3 | 3 |  |  | 11 | 9 | 82% |
| order book | 18 / 14 | 2 | 6 |  |  | 16 | 15 | 94% |
| other trigger | 9 / 4 | 4 | 3 |  |  | 9 | 3 | 34% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| imbalance / run (information) | 76 / 14 | 19 | 3 | 16% | 0% | 72 | 14 | 19% |
| tick | 45 / 7 | 13 | 3 | 23% |  | 43 | 11 | 25% |
| volume | 115 / 27 | 45 | 11 | 24% | 11% | 109 | 35 | 32% |
| time | 318 / 56 | 145 | 38 | 26% | 23% | 304 | 67 | 22% |
| event / swing / other | 129 / 51 | 21 | 11 | 50% | 76% | 118 | 49 | 41% |
| delta | 28 / 6 | 5 | 3 | 60% |  | 24 | 8 | 31% |
| kagi / P&F / line-break | 56 / 27 | 13 | 11 | 81% |  | 53 | 15 | 29% |
| renko-type | 87 / 32 | 11 | 12 | 110% |  | 77 | 20 | 26% |
| range | 32 / 23 | 5 | 9 | 181% |  | 25 | 20 | 79% |
| dollar | 14 / 2 | 4 | 0 |  |  | 13 | 0 | 0% |

**(trigger x bar) blocks**: 146 blocks with any tested family-best, 16 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | imbalance / run (information) | 17 / 0 | 5 | 0 | 0% |  | 0% |
| bands | volume | 19 / 3 | 7 | 0 | 0% |  | 16% |
| levels:swing S/R, trendline, channel | time | 11 / 0 | 8 | 0 | 0% |  | 0% |
| momentum | volume | 32 / 2 | 8 | 0 | 0% |  | 5% |
| pullback | time | 15 / 1 | 12 | 0 | 0% | 0% | 0% |
| levels:Fibonacci | time | 52 / 2 | 21 | 2 | 7% | 0% | 7% |
| bands | time | 67 / 6 | 38 | 6 | 16% | 30% | 11% |
| momentum | event / swing / other | 28 / 2 | 9 | 2 | 17% |  | 11% |
| cross-market | volume | 8 / 1 | 6 | 2 | 25% |  | 22% |
| session structure | time | 17 / 2 | 6 | 2 | 25% |  | 18% |

### London (real tested 304 of 335 family-bests, null tested 249 of 457)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| cross-market | 36 / 11 | 6 | 0 | 0% |  | 36 | 17 | 45% |
| bands | 16 / 14 | 2 | 4 |  |  | 13 | 20 | 153% |
| bar-native | 7 / 1 | 0 | 0 |  |  | 7 | 2 | 28% |
| confluence | 3 / 3 | 0 | 2 |  |  | 3 | 4 |  |
| levels:Fibonacci | 41 / 35 | 3 | 6 |  |  | 33 | 44 | 133% |
| levels:VWAP | 22 / 14 | 1 | 0 |  |  | 22 | 17 | 75% |
| levels:pivots | 4 / 0 | 1 | 0 |  |  | 3 | 0 |  |
| levels:profile / stack / walls / UW | 1 / 7 | 0 | 2 |  |  | 1 | 9 |  |
| levels:session / prior / round / opens / gaps | 14 / 10 | 0 | 0 |  |  | 14 | 15 | 102% |
| levels:swing S/R, trendline, channel | 19 / 9 | 0 | 2 |  |  | 15 | 4 | 24% |
| levels:zones / supply-demand | 11 / 26 | 0 | 6 |  |  | 12 | 29 | 242% |
| mean reversion / manual indicators | 6 / 12 | 0 | 6 |  |  | 4 | 13 |  |
| momentum | 30 / 23 | 0 | 6 |  |  | 24 | 33 | 136% |
| order book | 22 / 14 | 1 | 2 |  |  | 20 | 17 | 83% |
| other trigger | 0 / 3 | 0 | 2 |  |  | 0 | 4 |  |
| pullback | 2 / 1 | 0 | 0 |  |  | 1 | 2 |  |
| session structure | 2 / 13 | 0 | 2 |  |  | 1 | 18 |  |
| tape / order flow | 32 / 27 | 1 | 2 |  |  | 26 | 37 | 139% |
| trend | 36 / 26 | 3 | 9 |  |  | 28 | 37 | 133% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| time | 88 / 59 | 10 | 7 | 74% |  | 75 | 83 | 110% |
| composite / micro | 5 / 1 | 0 | 0 |  |  | 4 | 0 |  |
| delta | 6 / 6 | 0 | 4 |  |  | 7 | 11 | 167% |
| dollar | 5 / 5 | 1 | 4 |  |  | 4 | 2 |  |
| event / swing / other | 22 / 25 | 2 | 6 |  |  | 17 | 37 | 222% |
| imbalance / run (information) | 30 / 27 | 3 | 6 |  |  | 28 | 40 | 147% |
| kagi / P&F / line-break | 25 / 18 | 0 | 6 |  |  | 20 | 7 | 37% |
| range | 24 / 20 | 0 | 6 |  |  | 21 | 31 | 149% |
| renko-type | 32 / 30 | 0 | 6 |  |  | 29 | 20 | 70% |
| tick | 20 / 9 | 1 | 4 |  |  | 15 | 15 | 95% |
| volume | 47 / 49 | 1 | 2 |  |  | 46 | 73 | 159% |

**(trigger x bar) blocks**: 133 blocks with any tested family-best, 1 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| cross-market | time | 16 / 5 | 6 | 0 | 0% |  | 59% |

### NYAM (real tested 542 of 1,821 family-bests, null tested 250 of 730)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| bands | 83 / 21 | 24 | 0 | 0% | 0% | 272 | 47 | 17% |
| session structure | 36 / 8 | 10 | 0 | 0% |  | 118 | 20 | 17% |
| levels:session / prior / round / opens / gaps | 63 / 21 | 20 | 3 | 14% |  | 192 | 38 | 20% |
| levels:profile / stack / walls / UW | 70 / 10 | 104 | 18 | 17% | 20% | 228 | 23 | 10% |
| levels:VWAP | 38 / 6 | 17 | 3 | 17% |  | 124 | 18 | 14% |
| levels:Fibonacci | 56 / 16 | 10 | 3 | 29% |  | 181 | 35 | 19% |
| tape / order flow | 17 / 14 | 10 | 3 | 29% |  | 54 | 29 | 54% |
| levels:swing S/R, trendline, channel | 27 / 11 | 7 | 3 | 43% |  | 84 | 18 | 21% |
| trend | 31 / 18 | 13 | 6 | 43% |  | 101 | 41 | 41% |
| momentum | 41 / 15 | 7 | 3 | 43% |  | 128 | 38 | 30% |
| order book | 24 / 13 | 10 | 6 | 58% | 0% | 77 | 26 | 34% |
| bar-native | 6 / 4 | 0 | 0 |  |  | 20 | 6 | 29% |
| confluence | 3 / 1 | 0 | 0 |  |  | 7 | 3 | 43% |
| cross-market | 11 / 16 | 3 | 0 |  |  | 37 | 38 | 103% |
| levels:pivots | 15 / 1 | 3 | 0 |  |  | 47 | 0 | 0% |
| levels:zones / supply-demand | 9 / 67 | 3 | 26 |  |  | 27 | 96 | 359% |
| mean reversion / manual indicators | 4 / 5 | 3 | 6 |  |  | 13 | 9 | 65% |
| other trigger | 2 / 0 | 0 | 0 |  |  | 7 | 0 | 0% |
| pullback | 6 / 3 | 0 | 0 |  |  | 20 | 6 | 29% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| delta | 11 / 8 | 7 | 0 | 0% |  | 37 | 20 | 55% |
| dollar | 12 / 3 | 7 | 0 | 0% | 0% | 40 | 3 | 7% |
| tick | 59 / 11 | 37 | 0 | 0% | 0% | 195 | 29 | 15% |
| volume | 75 / 33 | 37 | 3 | 8% | 0% | 249 | 82 | 33% |
| event / swing / other | 55 / 35 | 17 | 6 | 35% |  | 178 | 82 | 46% |
| renko-type | 90 / 25 | 44 | 18 | 40% | 43% | 292 | 29 | 10% |
| imbalance / run (information) | 73 / 41 | 27 | 12 | 43% | 87% | 225 | 73 | 32% |
| kagi / P&F / line-break | 44 / 21 | 20 | 12 | 58% | 130% | 141 | 12 | 8% |
| time | 97 / 55 | 47 | 29 | 62% | 72% | 306 | 128 | 42% |
| range | 26 / 18 | 3 | 0 |  |  | 74 | 32 | 43% |

**(trigger x bar) blocks**: 143 blocks with any tested family-best, 12 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | time | 21 / 5 | 10 | 0 | 0% |  | 17% |
| levels:VWAP | volume | 5 / 1 | 7 | 0 | 0% |  | 17% |
| levels:profile / stack / walls / UW | delta | 2 / 0 | 7 | 0 | 0% |  | 0% |
| levels:profile / stack / walls / UW | dollar | 2 / 0 | 7 | 0 | 0% | 0% | 0% |
| levels:profile / stack / walls / UW | imbalance / run (information) | 7 / 1 | 10 | 0 | 0% | 0% | 12% |
| levels:profile / stack / walls / UW | tick | 9 / 0 | 17 | 0 | 0% |  | 0% |
| levels:session / prior / round / opens / gaps | kagi / P&F / line-break | 7 / 2 | 7 | 0 | 0% |  | 0% |
| levels:profile / stack / walls / UW | volume | 12 / 0 | 20 | 0 | 0% | 0% | 0% |
| order book | imbalance / run (information) | 5 / 0 | 7 | 0 | 0% |  | 0% |
| session structure | tick | 7 / 2 | 7 | 0 | 0% |  | 25% |

### NYPM (real tested 191 of 193 family-bests, null tested 230 of 233)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| momentum | 15 / 14 | 5 | 2 | 40% | 40% | 14 | 14 | 100% |
| trend | 30 / 22 | 6 | 5 | 84% | 67% | 29 | 18 | 62% |
| order book | 23 / 11 | 8 | 7 | 88% | 140% | 23 | 7 | 31% |
| bands | 14 / 24 | 5 | 5 | 100% |  | 14 | 22 | 158% |
| levels:zones / supply-demand | 13 / 23 | 6 | 8 | 134% |  | 13 | 17 | 131% |
| bar-native | 1 / 4 | 0 | 0 |  |  | 1 | 3 |  |
| confluence | 4 / 2 | 1 | 1 |  |  | 4 | 2 |  |
| cross-market | 15 / 14 | 4 | 6 |  |  | 15 | 13 | 87% |
| levels:Fibonacci | 9 / 22 | 1 | 4 |  |  | 7 | 18 | 258% |
| levels:VWAP | 7 / 7 | 0 | 0 |  |  | 7 | 7 | 100% |
| levels:pivots | 0 / 4 | 0 | 0 |  |  | 0 | 3 |  |
| levels:profile / stack / walls / UW | 9 / 15 | 0 | 3 |  |  | 9 | 11 | 123% |
| levels:session / prior / round / opens / gaps | 1 / 28 | 0 | 4 |  |  | 1 | 21 |  |
| levels:swing S/R, trendline, channel | 7 / 8 | 2 | 2 |  |  | 6 | 5 | 84% |
| mean reversion / manual indicators | 18 / 10 | 3 | 1 |  |  | 18 | 8 | 45% |
| other trigger | 1 / 0 | 1 | 0 |  |  | 1 | 0 |  |
| pullback | 1 / 3 | 0 | 2 |  |  | 1 | 3 |  |
| session structure | 4 / 8 | 1 | 0 |  |  | 4 | 5 |  |
| tape / order flow | 19 / 11 | 2 | 4 |  |  | 19 | 7 | 37% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| renko-type | 14 / 22 | 5 | 2 | 40% |  | 14 | 10 | 72% |
| volume | 23 / 22 | 7 | 6 | 86% | 120% | 22 | 21 | 96% |
| imbalance / run (information) | 15 / 26 | 5 | 5 | 100% |  | 15 | 25 | 167% |
| time | 63 / 63 | 14 | 18 | 129% | 100% | 63 | 56 | 89% |
| composite / micro | 0 / 1 | 0 | 0 |  |  | 0 | 0 |  |
| delta | 10 / 12 | 1 | 3 |  |  | 10 | 12 | 120% |
| dollar | 3 / 5 | 2 | 1 |  |  | 3 | 0 |  |
| event / swing / other | 23 / 31 | 4 | 8 |  |  | 22 | 29 | 132% |
| kagi / P&F / line-break | 11 / 18 | 1 | 3 |  |  | 9 | 3 | 33% |
| range | 9 / 11 | 4 | 5 |  |  | 9 | 10 | 111% |
| tick | 20 / 19 | 2 | 3 |  |  | 20 | 19 | 95% |

**(trigger x bar) blocks**: 124 blocks with any tested family-best, 0 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|


## R3 SANITY CHECK (order 2128Z; W-SHORT, 22:08Z) - why stage-A beats sit below the pure-noise rate
Result: NO code mismatch; the below-chance upper tail is a MEASURED selection effect of rule R0, not a defect of the draws.
1. Statistic: beats = number of the 30 draws STRICTLY below the real cell on the last-26-week sum of R (net points / stop, higher = better; ties count against the real cell). Histogram of beats (Asia 695 cells, NY AM 779 at the 21:30Z snapshot): both sit ABOVE chance on average (mean beats 20.8 and 17.6 vs 15 for exchangeable cells) but are concentrated (sd ~4 vs 9 for uniform on 0..30) with almost nothing at 29-30: Asia 0 1 1 1 3 4 5 6 6 10 8 7 7 8 7 8 5 5 3 2 0 % at beats 9..30. The uniform / 22.6-12.9-6.5% benchmark assumes the real cell is exchangeable with its draws (pure noise); selection makes that benchmark wrong in both tails.
2. Draws are fair twins (60 + 60 sampled family-bests, Asia and NY AM): trades real / mean draw trades median 1.00 and 0.94 (p10 0.78 / 0.70: in ~10% of cells the real trigger takes up to ~30% FEWER trades than its draws because real signals cluster and the one-position rule blocks them), long share real - draw +0.000 (max abs 0.002), same costs and fill basis (same simulator, same $4.84, first print >= signal + 1 s), same bracket and same 10..120 clip (same bracket arrays), same session windows. Real R vs draws: median z +0.52 (Asia) and +0.20 (NY AM) (draw R sd ~10-12 R vs real median R +1.7 / +3.4).
3. Same code path: the real cell re-scored through the draw path equals the grid's R0 L6M to 0.001 pt in 100% of NY AM cells and 98.3% of Asia cells; the exceptions (13 Asia cells, modules trig_levels_gaps / trig_levels_stack / trig_levels_book_walls_loose, which changed after their grid result) are marked VOID: excluded from the p-values (p = 1) and to be re-scored by the grid.
4. Order: tested cells are rank-ordered (processing starts at the best family-bests): mean beats falls with family rank (NY AM: 23.3 for ranks 1-100, 21.1, 20.7, 19.1, 18.7, 15.6 for ranks > 1600; Asia 23.5 -> 18.4), so low-ranked family-bests sit at chance and the first-tested ones lift the average; the histogram will move toward chance as lower ranks are tested.
5. Why the tail is cut (measured): random draws that pass R0 (L6M > 0, L3M > 0, >= 100 trades, persistence > 0.60, no RED prior year) are rare (Asia 4 of 7,200 = 0.06%, NY AM 21 of 7,200 = 0.29%) and, scored like real cells, give beats mean 17.0 / 13.7 (chance level) with 0% at >= 27 and 29: the R0 filters themselves compress beats: L6M > 0 and L3M > 0 remove the low tail, and 'prior years not more than 30% below the cell's own L6M R/wk' (RED rule) removes cells whose L6M is an extreme outlier vs their history = the high tail. The real cells therefore cannot show the uniform spread.
6. CONSEQUENCE for BH: p-values computed against UNSELECTED random entries are not a calibrated null for cells that were chosen as the best of ~4 M cells and then filtered on persistence / prior years: p_ALL in particular is biased (persistence since 2023-10 and the prior-year rule are conditions on the same history that p_ALL tests). Treat SET 1 / SET 2 counts as screening, not as calibrated false-discovery control, until the calibration null (5 whole-search draws pushed through the same ladder) shows the actual false-discovery rate.
7. READ THE SET 2 COUNTS WITH THIS: at 22:05Z SET 2 shows 759 (Asia, of 1,160 tested) and 1,484 (NY AM, of 1,935) cells at q = 20% and 0 at q = 10%; they are hundreds of cells tied at the smallest reachable p (0 of 30 draws as good on the whole history, p = 0.032), which BH passes en bloc at q = 20% because m is large. That pattern is what selection bias predicts (selected cells are positive over the whole history by construction, random entries are not): it is not evidence of edge. SET 1 (p_L6M) shows 0 at every q so far. Nothing is final until the calibration null has been run through both sets.
8. PSEUDO-REAL EXTENSION (Asia, 80 sampled family-bests, 9,600 random draws scored like real cells; 16 pass R0): on the L6M statistic the R0-passing random draws beat >= 24 of 30 in 12.5% of cases and >= 27 / 29 / 30 in 0% (mean beats 18.2) vs the real cells 26.2% / 8.8% / 3.8% / 1.2% (mean 20.8). On the WHOLE-HISTORY statistic the R0-passing random draws beat >= 24 / 27 / 29 / 30 of 30 in 87.5% / 56.2% / 37.5% / 12.5% (mean 25.4) vs the real cells 92.5% / 81.2% / 66.2% / 40.0% (mean 28.2): selection on persistence and prior years (R0) alone makes random draws look 'significant' on the whole history in about 2/3 as many cases as the real cells. p_ALL therefore discriminates weakly (thresholds at 29-30 of 30 would still carry a measured false-discovery share of roughly 30-60% on this small sample, n = 16 passing draws); p_L6M discriminates better. These are first estimates; the calibrated numbers come from the whole-search null through the same ladder (order 2218Z).
9. PSEUDO-REAL EXTENSION, NY AM (80 sampled family-bests, 9,600 random draws scored like real cells; 29 pass R0): on the WHOLE-HISTORY statistic the R0-passing random draws beat >= 24 / 27 / 29 / 30 of 30 draws in 93.1% / 93.1% / 69.0% / 44.8% (mean beats 28.1) versus the real NY AM cells 96.2% / 90.0% / 67.5% / 53.8% (mean 28.6): p_ALL does NOT separate real cells from random-entry cells that pass the same R0 filters in NY AM. On the L6M statistic the R0-passing random draws are at 0% for every threshold (mean beats 13.9) vs real 12.5% / 3.8% / 1.2% / 0% (mean 17.4): p_L6M separates, weakly. Consequence: SET 2 (BH on p_ALL) cannot be a pass rule for NY AM; only the whole-search null (R4 calibration) can say which thresholds carry a tolerable measured false-discovery rate.

## Leads already through the engine (for reference; not a rung count)

- **XA3** (NY AM, tick_5000 | levels_vwap.retest_native {M 6, tol 0.5} | plain 60/60 | both): R0 pass. Own-stop (screen, W-DAYMASK arrays): 1.5 stops L6M +1,313 pts (L3M +1,433; 2023 +1,364, 2024 +1,192, 2025 +1,950), 3 stops L6M +1,579 pts (L3M +1,692; +1,932 / +1,643 / +2,342); bare L6M +1,644 (L3M +1,408; +1,810 / +2,669 / +2,566); the 2-stop array is not built for this pair. R2 pass. R3: beats 25/30 same-bracket random draws (pass at the 24 threshold, fail at 27 and 29). Engine date-shift: +$54,428 vs best control +$24,259, beats 30/30. At the FRONT of the queue. K7 / P7 / M7 swap rows: see NEW_BOOK_ENGINE.md.
- **WP10** (NY PM, vol_350 | tape_libvol.cmf {len 10} | asym20u/10u | both): relabelled **lead for add-to-today's-stack at most; NOT a rebuilt-stack candidate**. R3: beats only 15/30 same-bracket random draws (median; random entries with its own wide bracket earn +787 pts on average vs its +1,236), best date-shift control within $135 of it (+$41,748 vs +$41,613), own-stop weak (W-DAYMASK 17:37Z: engine-$ 26 wk bare +24.7k, 1.5 stops +1.7k, 2 stops +4.3k, 3 stops +11.3k; 13 wk bare +10.0k but 2 stops -12.4k: its profits come after a bad start to the day). No more engine spent on it ahead of R3 passers.

## Clock order (addendum 1731Z): sessions are decided Asia -> London -> NY AM -> NY PM

Phase 1 is NOT split by session (one grid job feeds all four sessions), so the grid cores cannot be re-ordered by session without cost; what follows the clock order is the scoring and the later phases: scoring/ranking runs Asia first; in phases 3-4 each session is decided on the exact engine after the earlier session is final. Asia is NOT add-only: replace / add / mixed with a higher bar (drawdown first AND dollars, last 6 and 3 months, no red prior year, 30 controls, selection-corrected test).

## Top 10 Asia

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | mrenko_20 | momentum_er.trend_z {"len": 10, "thr": 0.4} | plain60/60 | +870 | +360 | +0.56 | 432 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 2 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +713 | -429 | +0.46 | 293 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +749 |
| 3 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +634 | +74 | +0.41 | 386 | ok/ok/ok | L6M @1.5 stops +634 / @3 stops +598 |
| 4 | mrenko_20 | momentum_er.trend {"len": 10, "thr": 0.4} | plain60/60 | +603 | +34 | +0.39 | 428 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 5 | tick_500 | levels_vwap.break {"n": 3, "k": 0.0} | plain60/60 | +674 | +1041 | +0.43 | 417 | AMBER/AMBER/AMBER | L6M @1.5 stops +674 / @3 stops +550 |
| 6 | tick_500 | levels_vwap.break_native {"n": 3, "k": 0.0} | plain60/60 | +674 | +1041 | +0.43 | 417 | ok/AMBER/AMBER | L6M @1.5 stops +674 / @3 stops +550 |
| 7 | tick_300 | trend_libstack.ema_stack {"set": "10-20-50"} | plain60/60 | +664 | +550 | +0.43 | 343 | AMBER/AMBER/AMBER | L6M @1.5 stops +664 / @3 stops <=0 or <100 tr |
| 8 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +673 | +70 | +0.43 | 555 | AMBER/ok/ok | L6M @1.5 stops +673 / @3 stops <=0 or <100 tr |
| 9 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +468 | +319 | +0.30 | 404 | ok/ok/ok | L6M @1.5 stops +468 / @3 stops <=0 or <100 tr |
| 10 | rng_20 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +535 | +899 | +0.34 | 500 | ok/ok/ok | L6M @1.5 stops +535 / @3 stops +266 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 | +616 | +1066 | +0.39 | 777 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +605 | +1164 | +0.39 | 562 | ok/ok/ok | strong on (b) too |
| 3 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +561 | -724 | +0.36 | 313 | ok/ok/ok | strong on (b) too |
| 4 | drb_2000 | levels_piv_cama.reject_native {"tol": 0.5, "conf": "body"} | plain60/60 | +764 | +351 | +0.49 | 573 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 5 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +632 | +93 | +0.40 | 806 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 6 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +601 | +126 | +0.38 | 444 | ok/ok/ok | strong on (b) too |
| 7 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +502 | +600 | +0.32 | 483 | ok/ok/ok | strong on (b) too |
| 8 | vsess_30 | bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | strong on (b) too |
| 9 | vsess_30 | bands_atrchan.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | strong on (b) too |
| 10 | vsess_30 | bands_envelope.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +626 | +1202 | +0.40 | 556 | ok/ok/ok | also positive on (b) |
| 2 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +551 | -724 | +0.35 | 312 | ok/ok/ok | also positive on (b) |
| 3 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +622 | +97 | +0.40 | 799 | ok/ok/ok | depends on today's stack |
| 4 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +693 | +194 | +0.44 | 440 | ok/AMBER/AMBER | also positive on (b) |
| 5 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +525 | +600 | +0.34 | 482 | ok/ok/ok | also positive on (b) |
| 6 | vsess_30 | bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | also positive on (b) |
| 7 | vsess_30 | bands_atrchan.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | also positive on (b) |
| 8 | vsess_30 | bands_envelope.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | also positive on (b) |
| 9 | tick_500 | levels_vwap.break {"n": 3, "k": 0.0} | plain60/60 | +474 | +1566 | +0.30 | 533 | ok/ok/ok | also positive on (b) |
| 10 | tick_500 | levels_vwap.break_native {"n": 3, "k": 0.0} | plain60/60 | +474 | +1566 | +0.30 | 533 | ok/ok/ok | also positive on (b) |

## Top 10 London

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +861 | -83 | +0.55 | 230 | ok/ok/AMBER | L6M @1.5 stops +861 / @3 stops +783 |
| 2 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +687 | +276 | +0.44 | 269 | ok/ok/ok | L6M @1.5 stops +687 / @3 stops +877 |
| 3 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +898 | -1732 | +0.58 | 229 | AMBER/ok/AMBER | L6M @1.5 stops +898 / @3 stops <=0 or <100 tr |
| 4 | cusum_28 | trend_macd.hist_turn_native {"len": 26, "width": 0.03} | plain60/60 | +744 | +972 | +0.48 | 364 | ok/ok/ok | L6M @1.5 stops +370 / @3 stops +431 |
| 5 | entropy_B200 | book_micro.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +701 | +653 | +0.45 | 238 | ok/ok/ok | L6M @1.5 stops +701 / @3 stops <=0 or <100 tr |
| 6 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 7 | kal_bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 8 | med_bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 9 | t3_bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 10 | bmsg_B320 | manual_macd.sigcross_native {"f": 20, "s": 45, "g": 15} | sym15u | +784 | +400 | +0.50 | 241 | AMBER/ok/ok | L6M @1.5 stops +784 / @3 stops <=0 or <100 tr |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +783 | -106 | +0.50 | 240 | ok/ok/ok | strong on (b) too |
| 2 | med_rngor_B200 | trend_ma_hma.cross {"len": 34, "width": 4, "hyst": 0.0} | sym15u | +736 | -344 | +0.47 | 260 | ok/ok/ok | strong on (b) too |
| 3 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +702 | +131 | +0.45 | 287 | ok/ok/ok | strong on (b) too |
| 4 | entropy_B200 | book_micro.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +852 | +899 | +0.55 | 255 | ok/AMBER/AMBER | strong on (b) too |
| 5 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +964 | -521 | +0.62 | 225 | ok/AMBER/AMBER | bare only (not positive on own-stop) |
| 6 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +666 | -175 | +0.43 | 140 | ok/ok/ok | strong on (b) too |
| 7 | ha_micro_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +802 | +520 | +0.51 | 260 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 8 | ha_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +743 | +460 | +0.48 | 257 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | kal_bmsg_B200 | trend_ma_hma.cross {"len": 21, "width": 2, "hyst": 0.0} | sym15u | +914 | +1528 | +0.59 | 260 | AMBER/AMBER/AMBER | bare only (not positive on own-stop) |
| 10 | ha_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +623 | +1129 | +0.40 | 502 | ok/ok/ok | bare only (not positive on own-stop) |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +1175 | +593 | +0.75 | 236 | ok/AMBER/AMBER | also positive on (b) |
| 2 | ha_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 3 | kal_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 4 | med_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 5 | t3_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 6 | rngor_B320 | book_queue.follow_sm {"thr": 0.3, "min": 3, "sm": 3} | sym15u | +704 | +434 | +0.45 | 122 | ok/ok/ok | also positive on (b) |
| 7 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +677 | -374 | +0.43 | 189 | ok/ok/ok | also positive on (b) |
| 8 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +674 | -435 | +0.43 | 182 | ok/ok/ok | depends on today's stack |
| 9 | kal_entropy_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +670 | -420 | +0.43 | 193 | ok/ok/ok | also positive on (b) |
| 10 | sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |

## Top 10 NY AM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u | +2161 | +1183 | +1.39 | 258 | AMBER/ok/ok | L6M @1.5 stops +2298 / @3 stops <=0 or <100 tr |
| 2 | med_volor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +1842 | +959 | +1.18 | 289 | ok/ok/ok | L6M @1.5 stops +900 / @3 stops <=0 or <100 tr |
| 3 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +2133 | +679 | +1.37 | 380 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 4 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +2026 | +333 | +1.30 | 496 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +579 |
| 5 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1389 | +271 | +0.89 | 318 | ok/ok/ok | L6M @1.5 stops +1501 / @3 stops <=0 or <100 tr |
| 6 | trend_20 | levels_vwap.reject {"tol": 1.0, "conf": "body"} | sym15u | +1375 | -248 | +0.88 | 260 | ok/ok/ok | L6M @1.5 stops +763 / @3 stops +1879 |
| 7 | qmid_B050 | levels_round.retest_native {"M": 10, "tol": 0.5} | sym15u | +1606 | -181 | +1.03 | 383 | ok/ok/ok | L6M @1.5 stops +1615 / @3 stops <=0 or <100 tr |
| 8 | kal_qmid_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1348 | +276 | +0.86 | 317 | ok/ok/ok | L6M @1.5 stops +1582 / @3 stops <=0 or <100 tr |
| 9 | qmid_B500 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1312 | +359 | +0.84 | 413 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +1083 |
| 10 | med_volor_B200 | bands_keltner.walk {"ema": 10, "atr": 10, "mult": 1.0, "N": 2} | sym15u | +1452 | -520 | +0.93 | 392 | ok/ok/ok | L6M @1.5 stops +1120 / @3 stops +1590 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_dltor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +2402 | +954 | +1.54 | 416 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 2 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1967 | +206 | +1.26 | 379 | AMBER/ok/ok | strong on (b) too |
| 3 | med_micro_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1526 | +1131 | +0.98 | 485 | ok/ok/ok | bare only (not positive on own-stop) |
| 4 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1711 | +719 | +1.10 | 508 | ok/ok/ok | strong on (b) too |
| 5 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1723 | +1816 | +1.10 | 497 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | kal_qmid_B080 | bands_regchan.break_stderr_native {"clk": 20, "k": 2.5} | sym15u | +1956 | +1097 | +1.25 | 316 | AMBER/AMBER/ok | strong on (b) too |
| 7 | trend_20 | levels_vwap.reject {"tol": 1.0, "conf": "body"} | sym15u | +1707 | -264 | +1.09 | 340 | ok/AMBER/ok | strong on (b) too |
| 8 | ha_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |
| 9 | kal_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |
| 10 | kal_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 2 | ha_bmsgq_B200 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1885 | -312 | +1.21 | 318 | ok/AMBER/ok | depends on today's stack |
| 3 | med_volor_B080 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u | +1448 | -307 | +0.93 | 257 | ok/ok/ok | depends on today's stack |
| 4 | t3_dltor_B080 | bands_bollinger.walk_native {"clk": 20, "k": 2.0, "N": 3} | sym15u | +1441 | +781 | +0.92 | 216 | ok/ok/ok | also positive on (b) |
| 5 | t3_sessrng_B080 | levels_round.break_native {"n": 3, "k": 0.5} | sym15u | +1372 | +500 | +0.88 | 121 | ok/ok/ok | also positive on (b) |
| 6 | ha_sessrng_B200 | bands_keltner.walk {"ema": 30, "atr": 10, "mult": 1.5, "N": 3} | sym15u | +1356 | +918 | +0.87 | 235 | ok/ok/ok | depends on today's stack |
| 7 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1835 | +1003 | +1.18 | 323 | AMBER/AMBER/ok | depends on today's stack |
| 8 | dchg_40 | manual_macd.sigcross_native {"f": 5, "s": 13, "g": 4} | plain60/60 | +1357 | -639 | +0.87 | 604 | ok/ok/ok | depends on today's stack |
| 9 | trend_20 | levels_fibr_dev.retest {"M": 3, "tol": 0.0} | sym15u | +1354 | +338 | +0.87 | 234 | ok/ok/ok | depends on today's stack |
| 10 | trend_20 | levels_fibr_dev.retest_native {"M": 3, "tol": 0.0} | sym15u | +1354 | +338 | +0.87 | 234 | ok/ok/ok | depends on today's stack |

## Top 10 NY PM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | micro_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 2 | qmid_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 3 | ha_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 4 | kal_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 5 | kal_qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 6 | med_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 7 | micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 8 | qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 9 | t3_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 10 | t3_qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_400 | tape_libvol.cmf {"len": 10} | plain60/60 | +1160 | +1543 | +0.74 | 1086 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | lbrk_3_10 | momentum_rsi.mom_native {"len": 7, "lvl": 55} | plain60/60 | +1323 | +1957 | +0.85 | 778 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 3 | entropy_B500 | trend_macd.hist_turn_native {"len": 12, "width": 0.01} | plain60/60 | +1133 | +880 | +0.73 | 973 | ok/ok/ok | bare only (not positive on own-stop) |
| 4 | tm1800 | xmarket_ym.follow {"w": 5, "thr": 1.0} | plain60/60 | +981 | +520 | +0.63 | 151 | ok/ok/ok | strong on (b) too |
| 5 | tm900 | xmarket_es.follow {"w": 5, "thr": 1.0} | plain60/60 | +1194 | +1168 | +0.77 | 280 | ok/ok/AMBER | bare only (not positive on own-stop) |
| 6 | entropy_B080 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +957 | -186 | +0.61 | 253 | ok/ok/ok | strong on (b) too |
| 7 | time_s_20 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} | plain60/60 | +1084 | -624 | +0.69 | 893 | ok/ok/ok | strong on (b) too |
| 8 | med_rngor_B200 | barnative_absorb.absorb {"len": 50, "dz": 1.5, "prog": 0.25} | sym15u | +1186 | +3135 | +0.76 | 328 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 9 | kal_volor_B200 | tape_stack.r5_follow {"k": 2} | sym15u | +886 | -623 | +0.57 | 310 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | med_volor_B200 | tape_stack.r5_follow {"k": 2} | sym15u | +886 | -623 | +0.57 | 310 | ok/ok/ok | bare only (not positive on own-stop) |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | kal_rngor_B080 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1024 | +671 | +0.66 | 210 | ok/ok/ok | depends on today's stack |
| 2 | micro_B030 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1283 | +430 | +0.82 | 130 | ok/AMBER/ok | depends on today's stack |
| 3 | kal_sessrng_B200 | levels_round.retest {"M": 6, "tol": 0.5} | plain60/60 | +1186 | +925 | +0.76 | 646 | ok/AMBER/ok | depends on today's stack |
| 4 | kal_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 5 | med_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 6 | rng_10 | levels_fibr_dev.break_native {"n": 3, "k": 0.5} | plain60/60 | +1334 | +361 | +0.86 | 530 | ok/AMBER/AMBER | depends on today's stack |
| 7 | mom_14 | bands_atrchan.break_ext_native {"clk": 5, "k": 1.5} | plain60/60 | +1008 | +1874 | +0.65 | 605 | ok/ok/ok | also positive on (b) |
| 8 | bmsg_B130 | levels_round.reject {"tol": 0.0, "conf": "close"} | sym15u | +1172 | +549 | +0.75 | 196 | ok/AMBER/ok | depends on today's stack |
| 9 | bmsg_B130 | levels_round.reject_native {"tol": 0.0, "conf": "close"} | sym15u | +1172 | +549 | +0.75 | 196 | ok/AMBER/ok | depends on today's stack |
| 10 | renko_10 | tape_delta.cvd_fade {"N": 5, "L": 100, "z": 1.0} | plain60/60 | +1219 | +206 | +0.78 | 527 | AMBER/AMBER/ok | depends on today's stack |

## Honest limits

- Rankings are best-of-many on the last 6 months; the selection-corrected best-pick null (phase 2b) is not applied yet to any row.
- Screen numbers are naked triggers; the engine rows (NEW_BOOK_ENGINE*.md) show layers and account rules change results both ways.

<!-- ENGINE_PLAN_ETAS -->
**Phase ETAs (W-PLAN, from ENGINE_PLAN.md section 11, 2026-11-19 02:05Z):**

- phase 1 pass 1: 11845 jobs left at 5183/h = 2.3 h (rate from the grid line above; sums over machines).
- phase 1 pass 2: 23470 jobs left at 624/h = 37.6 h at today's allocation.
- phases 2-3 engine, N = 6 passing cells per session: 30400 set-months = 19 h at the current fleet (1572/h) or 16.9 h with A and B engine-ready (projected 1798/h). Full table: ENGINE_PLAN.md section 11.
- luck test (order 2042Z): R3 = per-cell p-values with BH at q = 10% (stages A 30 / B 200 / C 1,000 draws); screen cost ~454-1759 core-h in all (hours on the 262 pool 1.7-6.7); R4 = 5 null draws, 1,585 core-h = 38 h at 25% of A+B; engine for the BH passers: ~68 core-h per passer incl. layers, 48 h on the pool for up to ~186 passers; BH passer counts per session come from W-SHORT (SURVIVOR_COUNTS.md). Dated D8-spec estimates: ENGINE_PLAN.md section 0.
- N is not a limit (order 1845Z): N only sizes the estimate; engine capacity decides the ORDER, never whether a passing cell is tested.

**DATED ESTIMATES (W-PLAN, written 2026-11-19 00:10Z; inputs: W-GRIDOPS 22:25Z / 23:05Z, W-SHORT R3 state at 23:32Z, engine queue report 00:00Z; rates change, the script re-prints this block as written until W-PLAN edits it):**

| milestone | estimate | basis |
|---|---|---|
| REAL pass 1 end | Nov 19 ~03:00-08:00Z | W-GRIDOPS 03:00-06:00Z; measured 1,904 real jobs/h at 23:05Z with ~11.5k left at 00:00Z = ~6 h (06:00Z) |
| pass 2 + exit families end | Nov 20 ~04:00-10:00Z | 23.6k jobs left at 690/h = 34 h (SEARCH_STATUS); W-GRIDOPS ~30 h |
| null draws 1-2 end (calibration check, first full table) | Nov 19 ~23:00Z to Nov 21 ~00:00Z (95.5k jobs at nice 10, 25-50 h); a PARTIAL calibration table (sessions covered so far) was due ~23:55Z and is not on SURVIVOR_COUNTS.md yet | W-GRIDOPS |
| null draws 3-5 end (5-draw calibration complete) | ~Nov 21 midday - Nov 22 (200k jobs, parked until real pass 1 ends, then ~5-6k jobs/h) | ASSUMED rate |
| R3 compute end per session (stages A-D, clock order Asia, London, NY AM, NY PM) | stage A for all 7,650 family-bests: Nov 19 ~00:00-02:00Z (restarted 20:59Z, wall 3-5 h); stages B-D: Nov 19 ~08:00Z (ASSUMED, W-SHORT owns); the pass SET decision waits for the calibrated rule (draws 1-2): Nov 20-21 | W-SHORT |
| engine queue (R5a on the 2,333-cell seed: NY AM 1,937 + NY PM 396, XA3 layers, London/Asia stages 2-3, NT2 controls) | 44.4k set-months = 30.7 h at 1,450/h -> drains ~Nov 20 07:00Z if nothing is added (R5a only: 12 set-months per cell; prior years and controls are added only for cells not negative) | lead report 00:00Z |
| engine hours for the passers after calibration: per passer 264 set-months (12 + 72 + 180; W-SHORT) + layers ~1,133 set-months (640 with a validated fast replay) = ~1,400 set-months | at the measured 1,450 set-months/h (engine share today): P = 50 / 100 / 200 / 400 -> 48 / 96 / 193 / 386 h (31 / 62 / 125 / 250 h with the screen); at the whole pool after phase 1 (262 core-eq = ~5,800 set-months/h): 12 / 24 / 48 / 96 h (8 / 16 / 31 / 62 h) | 0.045 core-h per set-month |
| D8 spec page (clock-order chain 4-8 h + 2 h after the last engine link) | P <= 100: Nov 21 ~20:00Z - Nov 22 ~04:00Z; P = 200: Nov 22 ~20:00Z - Nov 23 ~04:00Z; P = 400: Nov 24 ~20:00Z; earliest possible Nov 21 evening; +-12 h; moves with (a) the calibrated pass counts P, (b) the engine rate on A/B (A 69-118, B 132-168 set-months/h, oversubscribed), (c) whether the engine gets the whole pool after phase 1 | assumes phase 1 done Nov 20 ~10:00Z and the engine on the whole pool after it |
48 h flag: the engine queue (30.7 h) is under 48 h; the passer engine work exceeds 48 h of the measured engine share for P >= 50 and of the whole pool for P >= ~200 (no screen). Josh decides between more machines and waiting once P is known.
<!-- /ENGINE_PLAN_ETAS -->
