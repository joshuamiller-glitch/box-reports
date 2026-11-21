# SEARCH_STATUS - full-search programme (plan 1722Z: no Globex deadline), W-GRIDOPS, refreshed 2026-11-21 06:35Z

Plain words. Data end 2026-11-15 (NQ). Research only, no spend. Phases: 1 finish the whole search -> 2 prove it is not luck (30 controls, selection-corrected null, trust) -> 3 gates/layers one by one then jointly -> 4 D8 spec. Every number below is a screen-level number unless it says engine.

## Phase 1 - progress (the grid is not split by session: one job = one bar row x one trigger module x one tag; every session reads the same results, so the percentages below are the same for NY AM, NY PM, London and Asia)

| item | done | todo | jobs/hour (last 60 min) | ETA at that rate |
|---|---|---|---|---|
| pass 1, all tags (real + random-entry nulls 1/2 + extra null draws) | 269166 result files | 9 jobs | 1071 | 0.0 h |
| pass 2 (family cells, exits a2, top cells) | n/a | 5793 (a top cells 14, a2 exit families 0, c family cells 5779) | 143 | 40.5 h |

NOTE (18:40Z): the grid is partitioned over server 2 (rows 0-1 of 12), A (2-6) and B (7-11) by W-S3; finished results are merged into server 2 every ~5 min (lag <= 10 min), the todo and worker counts are summed over the three servers. A and B also see 172 bar rows that are complete on box 1 but not yet on server 2, so total todo is higher than the earlier single-server figure (about +50%).

Pass-1 results on disk by tag: real 69329, null draw 1 65647, null draw 2 65654, extra draws (3-25) 62401 files. Pass-1 results still waiting for their pass-2 upgrade: real 54036.

Machines (grid partitioned across servers): 207.188.7.103 load 103.17 workers 86; 109.94.96.39 load 184.42 workers 104; 206.223.224.21 load 174.19 workers 104; grid workers 294 (62 computing), engine workers 417; forward-path tables built (summed over servers) 724.

Since 17:23Z: pass-1 todo 80818 -> 9 (-80809), pass-2 todo 25951 -> 5793 (-20158). Pass-2 todo grows when pass 1 delivers cells that earn pass 2.

## R4 - selection-corrected null of the whole search: FIVE draws, calibration check of the ladder (orders 1932Z + 2042Z; prereg sha 125fd12566e72aa6 + amendment)

What it is: 5 random-entry draws (tags p1rand1..p1rand5; draws 6-20 cancelled 20:42Z, files kept) of the SAME pass-1 search (every bar row x trigger module, same flags own-stop + account mask); the share of cells that pass R0-R3 in a null draw versus in the real search is the false-discovery rate, and the best cell of the null search versus the best of the real search is the best-pick comparison. Draws 1-2 run inside the real loops, draws 3-5 in dedicated null loops (A rows 2-6: 24 workers, B rows 7-11: 24 workers, server 2 rows 0-1: 6 workers; nice 8-10, below the engine (nice 0) and R3 (nice 5)). The null cells are also pushed through the same ladder R0-R3 as a CALIBRATION CHECK of the false-discovery rate the ladder claims. Only accepted draws count (null audit: independent side draw, pooled mean pts/trade at plain 60/60 negative and above -6 in every session, identical share under 1%, coverage at least 80%).

| item | now |
|---|---|
| results/hour, REAL search (p1real files, pass 1 and 2 together) | 23 |
| results/hour, NULL draws (p1rand1..20 files) | 1191 |
| null result files on disk, draws 1 / 2 | 65647 / 65654 (real: 69329) |
| null result files, draws 3-20 (all) | 61718 |
| share of the (row, module) files complete incl. error stubs, per draw (total ~65.8k jobs per draw; grid is not split by session, so every session sees the same share) | draw 1 102%, draw 2 102%, draw 3 28%, draw 4 28%, draw 5 28% |
| draws complete (files incl. error stubs >= 99.5 percent of ~65.8k) | 0 of 5 |
| draws accepted by the null audit and counted | see null_summary below |

Estimate: about 18 more full draws at the null share of the fleet (64 threads, ~25% of A + B) is roughly 60 hours (about 4,000 core-hours at the measured pass-1 rate; the order estimated ~6,300 core-hours); if that needs more than ~48 h the null share can be raised at the cost of the real search or machines added (Josh decides). False-discovery rate per session and the best-pick comparison appear here when W-SHORT has run the rule on the first accepted draws.

### False-discovery counts (W-SHORT, rule/null_summary.md: per accepted null draw per session, null cells passing vs the real search on the SAME coverage; ratio null/real = false-discovery ratio)

# NULL DRAWS vs REAL (same coverage) - cells passing R0 (bare) per session, W-SHORT 06:27Z

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
| Dallas | 12 | 0 | 0 | 24825 / 23613 / 23613 |
| Frankfurt | 1660 | 1396 | 1759 | 8608 / 7493 / 7100 |
| Singapore | 1657 | 776 | 1179 | 8727 / 7281 / 6753 |

Counts are the files on each host before the merge (A and B results are copied to Dallas every ~5 min); a host shows 0 stale for its own rows when its re-run is complete. Old copies of other hosts rows still on Dallas disappear as the merge overwrites them.

## Machines (hourly; busy % is measured from /proc/stat against the REAL thread count of each machine)

| machine | real threads | busy % | load1 | grid workers (computing) | engine workers | re-rank/other workers | results/hour (this machine) |
|---|---|---|---|---|---|---|---|
| server 2 Dallas | 64 | 99.6 | 103.17 | 294 (62) | 208 | 0 | 1214 |
| A Frankfurt | 128 | 100.0 | 184.42 | 104 (4) | 91 | 0 | 293 |
| B Singapore | 128 | 99.8 | 174.19 | 104 (6) | 92 | 0 | 322 |
| box 1 London (lead, engine fillers) | 32 | 100 | 58.05 | 0 | see CORES.md | - | - |

Server 2 has 64 threads (SMT off in firmware, order 1830Z check), A and B 128 each, box 1 32. Total jobs/hour and the phase-1 ETA are in the table above (sum over servers; double counting warning applies until W-S3 merges results). Any machine under 85% busy for 3 readings with work pending gets a one-line explanation in MORNING.md.

## Blocked / cannot run (listed, not skipped silently)

Failed jobs leave an error stub that the loop retries after 4 hours (older stubs are retried automatically). Error files on disk: {'real': 355, 'p1real': 1823, 'p1rand1': 1673, 'p1rand2': 1640, 'p1rand3': 16, 'p1rand4': 16, 'p1rand5': 16}.

| module | failures (files) | why |
|---|---|---|
| trig_book_ofi | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_cancel | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_ice | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_queue | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_pslope | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_dwm | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_imb | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_micro | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_thin | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_wall | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_sweep | 330 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_block | 324 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_run | 324 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_unfinished | 323 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_stack | 323 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_sizemix | 323 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
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

# SURVIVOR_COUNTS - the LADDER (cheapest test first; W-SHORT, orders 1845Z + 1932Z), refreshed 2026-11-21 06:22Z

No top-N cap anywhere. A cell leaves only by FAILING a test. Counts are bare (R0) from server-2 results only and PROVISIONAL (grid partitioned over servers until W-S3 merges; data week 189). Rungs not yet run say "n/a (reason)", never zero.

THRESHOLDS (equal risk; R = points / stop, stop = clip(bracket multiple x row bar unit, 10, 120), plain 60/60 = 60): R0 L6M (26 w) > 0; >= 100 trades in L6M; L3M (13 w) > 0; persistence > 0.60 (2-week windows since 2023-10 positive); prior years 2023/24/25 R per week not more than 30% below the cell's own L6M R per week (RED = shown, not delivered; AMBER 15-30% passes, counted). R1 = the same thresholds on the OWN-STOP result (2 stops; 1.5 / 3 shown): cells passing R0 but failing R1 are KEPT and labelled "depends on today's stack". R2 trust (brute-force tape walk) + look-ahead (6 truncation cuts) + fills >= signal + 1 s. R3 30 same-bracket random-entry draws, screen level: PASS = beats >= 27 of 30 (count shown at 24 / 27 / 29). R4 selection-corrected null of the same search (5 full null draws, same own-stop flags; calibration check of R0-R3 on null cells). R5 exact engine, staged.

FAMILIES = connected components of the grid neighbour graph over passing cells (same module.variant on an adjacent bar size of the same bar type, adjacent parameter of the same variant, or the identical parameter with another bracket / side); the best member (highest min(L6M R/wk, weakest prior-year R/wk)) runs first, neighbours after; nothing is dropped.

FLEET: 352 threads (Dallas 64, Frankfurt 128, Singapore 128, box 1 32), 90% busy assumed = 317 screen cores; engine set-months/hour measured 763 (box 1 450 + Dallas 313; A and B have no engine runs yet), projected 2894 with A and B engine-ready (ENGINE_PLAN.md s.11). Unit costs measured on WP10 / XA3 (PHASE2_TOOLING_TEST.md): R2 ~12 CPU-s per cell; R3 ~0.31 core-h per (row, module) pair (30 draws; cells sharing a pair share the draws); R4 ~317 core-h per full null draw = ~1,585 core-h for the 5 draws now planned (order 2042Z; shared by all four sessions; W-GRIDOPS ETA: draws 1-2 inside the real loops ~16 h, draws 3-5 ~62 h at the 25 percent share or ~30 h once real pass 1 is done); R5 engine 0.05 core-h per set-month measured on box 1 / Dallas (Frankfurt measured ~0.30: 1,072 s per month, starved), R5 stage a = 12 set-months per family (L6M as ADD and as replacement of the weakest live book), prior years +72, 30 date-shift controls +180 set-months (7.8 core-h at 0.043). All "hours" below are UPPER BOUNDS (no cell has failed R1-R3 yet) and assume the whole fleet for screen rungs (R4: its 25 percent share of A + B) and the measured 763 set-months/h for the engine.

## UNVERIFIED (stale level result) - notice, refreshed 06:20Z UTC

trig_levels_* grid results written BEFORE 2026-11-18 06:00Z predate the level-module fixes (13 of 17 level modules differ on a fresh re-run, W-GRIDOPS 0145Z); they are being re-run (Dallas from 01:33Z, Frankfurt / Singapore ~02:30Z, null draws 1-2 last). Until the result stamp (code hash on every result file) exists, every row below that touches a level module and a pre-06:00Z result is **UNVERIFIED (stale level result)**; non-level modules are not known to be affected (all-module check pending, order 0143Z). Stage-A p-values of R3 are computed with the CURRENT module code (fresh), but the cell SELECTION (R0) used the stale grid result; cells whose fresh L6M differs from the grid L6M by > 1 point are VOID (excluded).

| session | R0 passing cells | of which stale level cells | family-bests | stale family-bests | real-on-null-coverage tested (stage A) | stale level cells there | null draw tested (stage A) | stale level cells there |
|---|---|---|---|---|---|---|---|---|
| Asia | 6,487 | 6 (0.1%) | 3,847 | 3 | 900 | 2 (0%) | 364 | 0 (0%) |
| London | 3,158 | 0 (0.0%) | 2,237 | 0 | 333 | 0 (0%) | 454 | 0 (0%) |
| NYAM | 24,702 | 5 (0.0%) | 11,460 | 1 | 1814 | 0 (0%) | 728 | 0 (0%) |
| NYPM | 1,638 | 1 (0.1%) | 1,168 | 1 | 191 | 1 (1%) | 230 | 0 (0%) |

Reading: the stale share is NOT symmetric in the calibration: among tested family-bests 3-11% of the real-search cells but 17-26% of the null-draw cells rest on pre-06:00Z level files (the null draws were run early with the old level code), so the 01:16Z FDR table can be biased by the stale null side; it is redone after the forced re-run of draws 1-2 (last in the queue).


## Asia
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 9,797,654 | - | 9,791,167 | by first rule: R1 L6M<=0 5,284,669; R2 trades<100 2,110,557; R3 L3M<=0 821,434; R4 persistence<=0.60 1,381,960; RED prior year 192,547 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 6,487 (R0 passers) | 3,847 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 21.6 core-h for 6,487 cells | 0.1 h |
| R2 | trust + look-ahead | 6,487 (upper bound: all R1 cells) | 3,847 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 819 core-h for 2,642 (row, module) pairs | 2.6 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 6,487 (upper bound) | 3,847 | RUNNING: stage A (30 draws, same bracket, equal-risk) 3,936 of 3,847 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 922 / 294 / 60; reached stage B (200 draws) 1734, C (1,000) 471, D (10,000) 9 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 3,847 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 2514 / 3315 / 3752 at q 5% / 10% / 20% | SET 1: 0, SET 2: 3315 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 46,164 set-months = 2308 core-h | **61 h (> 48 h: Josh decides between more machines and waiting)** on the measured fleet (763/h), 16.0 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 3,847 families (upper bound) | 3,847 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+276,984 set-months) then 30 date-shift controls (+692,460 set-months = 34623 core-h) for the rows still alive | **363 h (> 48 h: Josh decides between more machines and waiting)** / **908 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 9,797,654; PASS **6,487 cells in 3,847 families** (non-reversal bars 3964, reversal 2009 (provisional until the look-ahead gate), other 514; level / S-D modules 3183; AMBER prior year(s) 1190). Distinct (row, module) files among the passers: 2,642.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_Asia.parquet; passing cells with family id / order / rank in family: pass_bare_Asia.csv.

## London
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 10,744,790 | - | 10,741,632 | by first rule: R1 L6M<=0 6,002,643; R2 trades<100 2,596,212; R3 L3M<=0 704,090; R4 persistence<=0.60 1,319,571; RED prior year 119,116 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 3,158 (R0 passers) | 2,237 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 10.5 core-h for 3,158 cells | 0.0 h |
| R2 | trust + look-ahead | 3,158 (upper bound: all R1 cells) | 2,237 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 552 core-h for 1,780 (row, module) pairs | 1.7 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 3,158 (upper bound) | 2,237 | RUNNING: stage A (30 draws, same bracket, equal-risk) 806 of 2,237 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 48 / 8 / 2; reached stage B (200 draws) 599, C (1,000) 112, D (10,000) 3 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 2,237 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 123 / 384 at q 5% / 10% / 20% | SET 1: 0, SET 2: 123 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 26,844 set-months = 1342 core-h | 35.2 h on the measured fleet (763/h), 9.3 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 2,237 families (upper bound) | 2,237 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+161,064 set-months) then 30 date-shift controls (+402,660 set-months = 20133 core-h) for the rows still alive | **211 h (> 48 h: Josh decides between more machines and waiting)** / **528 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 10,744,790; PASS **3,158 cells in 2,237 families** (non-reversal bars 1854, reversal 681 (provisional until the look-ahead gate), other 623; level / S-D modules 1445; AMBER prior year(s) 671). Distinct (row, module) files among the passers: 1,780.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_London.parquet; passing cells with family id / order / rank in family: pass_bare_London.csv.

## NYAM
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 11,735,921 | - | 11,711,219 | by first rule: R1 L6M<=0 6,972,931; R2 trades<100 1,567,955; R3 L3M<=0 929,068; R4 persistence<=0.60 2,047,105; RED prior year 194,160 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 24,702 (R0 passers) | 11,460 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 82.3 core-h for 24,702 cells | 0.3 h |
| R2 | trust + look-ahead | 24,702 (upper bound: all R1 cells) | 11,460 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 2163 core-h for 6,978 (row, module) pairs | 6.8 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 24,702 (upper bound) | 11,460 | RUNNING: stage A (30 draws, same bracket, equal-risk) 11,767 of 11,460 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 1261 / 311 / 72; reached stage B (200 draws) 3414, C (1,000) 1035, D (10,000) 23 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 11,460 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 7433 / 9545 / 10913 at q 5% / 10% / 20% | SET 1: 0, SET 2: 9545 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 137,520 set-months = 6876 core-h | **180 h (> 48 h: Josh decides between more machines and waiting)** on the measured fleet (763/h), 47.5 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 11,460 families (upper bound) | 11,460 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+825,120 set-months) then 30 date-shift controls (+2,062,800 set-months = 103140 core-h) for the rows still alive | **1081 h (> 48 h: Josh decides between more machines and waiting)** / **2704 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 11,735,921; PASS **24,702 cells in 11,460 families** (non-reversal bars 13407, reversal 7711 (provisional until the look-ahead gate), other 3584; level / S-D modules 15343; AMBER prior year(s) 4299). Distinct (row, module) files among the passers: 6,978.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYAM.parquet; passing cells with family id / order / rank in family: pass_bare_NYAM.csv.

## NYPM
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 11,753,727 | - | 11,752,089 | by first rule: R1 L6M<=0 6,288,218; R2 trades<100 2,589,000; R3 L3M<=0 789,063; R4 persistence<=0.60 2,048,864; RED prior year 36,944 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 1,638 (R0 passers) | 1,168 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 5.5 core-h for 1,638 cells | 0.0 h |
| R2 | trust + look-ahead | 1,638 (upper bound: all R1 cells) | 1,168 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 303 core-h for 979 (row, module) pairs | 1.0 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 1,638 (upper bound) | 1,168 | RUNNING: stage A (30 draws, same bracket, equal-risk) 393 of 1,168 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 92 / 65 / 32; reached stage B (200 draws) 368, C (1,000) 81, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 1,168 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 144 / 321 / 370 at q 5% / 10% / 20% | SET 1: 0, SET 2: 321 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 14,016 set-months = 701 core-h | 18.4 h on the measured fleet (763/h), 4.8 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 1,168 families (upper bound) | 1,168 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+84,096 set-months) then 30 date-shift controls (+210,240 set-months = 10512 core-h) for the rows still alive | **110 h (> 48 h: Josh decides between more machines and waiting)** / **276 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 11,753,727; PASS **1,638 cells in 1,168 families** (non-reversal bars 1059, reversal 214 (provisional until the look-ahead gate), other 365; level / S-D modules 562; AMBER prior year(s) 346). Distinct (row, module) files among the passers: 979.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYPM.parquet; passing cells with family id / order / rank in family: pass_bare_NYPM.csv.

## R3 PASS SETS side by side (Benjamini-Hochberg across ALL family-bests of the session; untested cells count as p = 1; the counts grow as draws complete)

SET 1 (strict, current rule) = inside BH on p_L6M (last 26 weeks, equal-risk sum of R). SET 2 (proposed, order 2057Z) = inside BH on p_ALL (whole history, first month to today, L6M included) AND still passing R0 / R1 unchanged (every cell here already passed R0; R1 own-stop pending). Cells in SET 2 with p_L6M > 0.20 are flagged "recent no better than random" (shown, not dropped). p = (1 + k) / (1 + n), k = random draws at least as good, n = draws; weakest prior-year p shown separately. Engine order: SET 1 first, then SET 2 members best p first, no cap; Josh decides which set is the pass rule. Engine cost per passer: R5a 12 set-months + prior years 72 + 30 date-shift controls 180 = 264 set-months = ~13 core-h = 0.35 h at the measured 763 set-months/h. Dated D8 spec estimate: W-PLAN, ENGINE_PLAN.md.

| session | family-bests | tested | SET 1 q5 / q10 / q20 | SET 1 expected false (q10) | SET 1 engine core-h / h | SET 2 q5 / q10 / q20 | SET 2 expected false (q10) | SET 2 engine core-h / h | SET 2 flagged recent no better than random (q10) | smallest p: L6M / ALL |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,890 | 3,936 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 2514 / 3315 / 3752 | 331.5 | 43758 / 1147.0 h | 2695 | 0.0212 / 0.0001 |
| London | 808 | 806 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 123 / 384 | 12.3 | 1624 / 42.6 h | 112 | 0.0420 / 0.0002 |
| NYAM | 4,556 | 11,767 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 7433 / 9545 / 10913 | 954.5 | 125994 / 3302.6 h | 8788 | 0.0250 / 0.0001 |
| NYPM | 396 | 393 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 144 / 321 / 370 | 32.1 | 4237 / 111.1 h | 245 | 0.0220 / 0.0001 |

## CALIBRATION: measured false-discovery rate from the whole-search null (order 2218Z, partial draw 1)

Label: PARTIAL / coarse (draw p1rand1 only, files that exist so far; the real search is restricted to the same (row, module) files and the pass-1 coverage; one family definition: same file + parameter). FDR(b) = expected null family-bests / real family-bests at the threshold "beats >= b of 30 draws" (p <= (31 - b + 1) / 31). Stage A only (30 draws): the finest p reachable is 0.032, so FDR <= 10% can only be read where it shows below.

| session | R0 pass cells null / real (ratio) | R0 families null / real | tested null / real (sampled family-bests) | stat | b = 24 | 27 | 29 | 30 |
|---|---|---|---|---|---|---|---|---|
| Asia | 979 / 2,235 (0.44) | 964 / 2,132 | 364 / 900 | p_L6M (null / real families at threshold = FDR) | 228 / 663 = 34% | 72 / 220 = 32% | 37 / 31 = 120% | 19 / 5 = 391% |
|  |  /  (0.00) |  /  | 364 / 900 | p_ALL (null / real families at threshold = FDR) | 588 / 1980 = 30% | 437 / 1755 = 25% | 291 / 1424 = 20% | 172 / 1009 = 17% |
| London | 1,784 / 1,414 (1.26) | 1,739 / 1,369 | 454 / 333 | p_L6M (null / real families at threshold = FDR) | 184 / 74 = 248% | 50 / 12 = 404% | 15 / 8 = 186% | 15 / 0 = n/a |
|  |  /  (0.00) |  /  | 454 / 333 | p_ALL (null / real families at threshold = FDR) | 1203 / 1065 = 113% | 919 / 806 = 114% | 624 / 493 = 127% | 352 / 370 = 95% |
| NYAM | 2,713 / 7,764 (0.35) | 2,617 / 7,377 | 728 / 1814 | p_L6M (null / real families at threshold = FDR) | 313 / 903 = 35% | 140 / 268 = 52% | 50 / 81 = 62% | 18 / 33 = 55% |
|  |  /  (0.00) |  /  | 728 / 1814 | p_ALL (null / real families at threshold = FDR) | 1754 / 7072 = 25% | 1424 / 6551 = 22% | 1060 / 5380 = 20% | 701 / 4026 = 17% |
| NYPM | 1,037 / 759 (1.37) | 1,008 / 749 | 230 / 191 | p_L6M (null / real families at threshold = FDR) | 237 / 176 = 134% | 136 / 122 = 112% | 44 / 67 = 66% | 18 / 35 = 50% |
|  |  /  (0.00) |  /  | 230 / 191 | p_ALL (null / real families at threshold = FDR) | 806 / 729 = 111% | 723 / 682 = 106% | 592 / 510 = 116% | 429 / 357 = 120% |

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

## CALIBRATION, DEEPER RUNGS BY MODE (like with like: both-side cells vs both-side null cells, long vs long; order 1014Z)

LABEL (lead 1426Z): Asia both-side whole-history FDR 6-7% rests on 35 tested null family-bests = THIN NULL, LEAD, not CONFIRMED.

| session | mode | statistic | p<=0.02 null / real = FDR | p<=0.005 | p<=0.001 | tested null / real (family-bests) |
|---|---|---|---|---|---|---|
| Asia | both | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 35 / 298 |
| Asia | both | p_ALL | 29 / 429 = 7% | 13 / 194 = 7% | 0 / 5 = 0% | 35 / 298 |
| Asia | long | p_L6M | 3 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 328 / 600 |
| Asia | long | p_ALL | 90 / 535 = 17% | 32 / 223 = 14% | 3 / 12 = 22% | 328 / 600 |
| NYAM | both | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 146 / 467 |
| NYAM | both | p_ALL | 255 / 1200 = 21% | 133 / 525 = 25% | 7 / 20 = 35% | 146 / 467 |
| NYAM | long | p_L6M | 11 / 0 = n/a | 7 / 0 = n/a | 4 / 0 = n/a | 578 / 1346 |
| NYAM | long | p_ALL | 352 / 2534 = 14% | 133 / 1179 = 11% | 0 / 57 = 0% | 578 / 1346 |
| London | both | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 76 / 43 |
| London | both | p_ALL | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 76 / 43 |
| London | long | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 378 / 290 |
| London | long | p_ALL | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 378 / 290 |
| NYPM | both | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 139 / 124 |
| NYPM | both | p_ALL | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 139 / 124 |
| NYPM | long | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 55 / 40 |
| NYPM | long | p_ALL | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 55 / 40 |

## CALIBRATION, DEEPER RUNGS (order 0125Z item 3): FDR at p <= 0.02 / 0.005 / 0.001 (null draw 1 vs real search on the same coverage; stage A+B+C records, XC_*; counts scaled to all family-bests of each set)

p = (1+k)/(1+n) on p_L6M (L6M sum of R) and p_ALL (whole history); a cell counts at the threshold when it has reached the stage whose floor allows it (B: 0.005, C: 0.001; p<=0.02 from B). Cells not yet advanced count as not passing; the table is therefore a LOWER bound on both sides until all B/C tasks are done (tasks issued / done shown).

| session | statistic | p<=0.02 null / real | FDR | p<=0.005 null / real | FDR | p<=0.001 null / real | FDR | tested null / real | cells at B+ null / real |
|---|---|---|---|---|---|---|---|---|---|
| Asia | p_L6M | 3 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 364 / 900 | 240 / 841 |
| Asia | p_ALL | 122 / 967 | 13% | 45 / 419 | 11% | 3 / 17 | 16% | 364 / 900 | 240 / 841 |
| NYAM | p_L6M | 11 / 0 | n/a | 7 / 0 | n/a | 4 / 0 | n/a | 728 / 1814 | 518 / 1741 |
| NYAM | p_ALL | 611 / 3737 | 16% | 266 / 1704 | 16% | 7 / 77 | 9% | 728 / 1814 | 518 / 1741 |
| London | p_L6M | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 454 / 333 | 0 / 0 |
| London | p_ALL | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 454 / 333 | 0 / 0 |
| NYPM | p_L6M | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 230 / 191 | 0 / 0 |
| NYPM | p_ALL | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 230 / 191 | 0 / 0 |

## CALIBRATION BY FAMILY (order 0125Z; same footing as the table above: null draw 1 through the same stage A, p_L6M and p_ALL)

**UNVERIFIED FOR ALL "levels:*" TRIGGER FAMILIES (W-GRIDOPS 0145Z)**: trig_levels_* results written before 2026-11-18 06:00Z predate the level-module fixes (13 of 17 level modules differ on a fresh re-run); real AND null level cells are partly stale until the forced re-run lands (Dallas from 01:33Z, Frankfurt / Singapore ~02:30Z); read the levels:* rows as provisional and treat level-cell rows on the ladder lists as UNVERIFIED (ranked after verified cells). FDR(b) = null family-bests beating >= b of 30 draws / real family-bests beating >= b, per trigger family, bar family and (trigger x bar) block; counts are scaled to ALL family-bests of each set when only a part is tested (tested n shown). b = 24 / 27 shown on p_L6M with p_ALL beside. FDR < 100% = real > null; a block with real >> null is where the engine and the deeper stages go first; null >= real = last, not dropped. A block needs >= 5 real family-bests at b = 24 to be ranked (small counts give an unstable ratio). The best-of-many effect is shown by the number of blocks tested.

### Asia (real tested 900 of 2,132 family-bests, null tested 364 of 964)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| levels:pivots | 17 / 8 | 9 | 0 | 0% |  | 36 | 8 | 22% |
| pullback | 34 / 9 | 43 | 5 | 12% | 11% | 78 | 13 | 17% |
| bands | 139 / 30 | 145 | 19 | 13% | 14% | 322 | 61 | 19% |
| momentum | 142 / 25 | 111 | 26 | 24% | 14% | 320 | 50 | 16% |
| session structure | 46 / 14 | 21 | 5 | 25% | 37% | 92 | 26 | 29% |
| levels:Fibonacci | 111 / 40 | 88 | 24 | 27% | 0% | 227 | 66 | 29% |
| levels:VWAP | 43 / 13 | 19 | 5 | 28% |  | 95 | 19 | 20% |
| levels:swing S/R, trendline, channel | 32 / 13 | 26 | 8 | 30% | 0% | 66 | 21 | 32% |
| trend | 89 / 38 | 64 | 29 | 46% | 93% | 201 | 77 | 38% |
| levels:session / prior / round / opens / gaps | 61 / 25 | 24 | 13 | 56% | 56% | 135 | 40 | 29% |
| tape / order flow | 41 / 18 | 28 | 16 | 56% | 56% | 92 | 29 | 32% |
| levels:profile / stack / walls / UW | 46 / 17 | 14 | 8 | 56% | 75% | 107 | 21 | 20% |
| other trigger | 9 / 6 | 9 | 5 | 56% |  | 21 | 5 | 25% |
| cross-market | 26 / 17 | 36 | 26 | 75% | 45% | 52 | 42 | 81% |
| mean reversion / manual indicators | 13 / 10 | 7 | 5 | 75% |  | 26 | 21 | 81% |
| bar-native | 15 / 5 | 5 | 5 |  |  | 36 | 13 | 37% |
| confluence | 4 / 2 | 5 | 0 |  |  | 9 | 5 | 56% |
| levels:zones / supply-demand | 14 / 55 | 5 | 11 |  |  | 26 | 37 | 142% |
| order book | 18 / 19 | 5 | 16 |  |  | 38 | 32 | 84% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| imbalance / run (information) | 76 / 20 | 45 | 5 | 12% | 0% | 171 | 32 | 19% |
| volume | 115 / 33 | 107 | 21 | 20% | 8% | 258 | 72 | 28% |
| tick | 45 / 15 | 31 | 8 | 26% |  | 102 | 32 | 31% |
| dollar | 14 / 3 | 9 | 3 | 28% |  | 31 | 0 | 0% |
| time | 318 / 89 | 341 | 95 | 28% | 27% | 718 | 167 | 23% |
| event / swing / other | 129 / 71 | 50 | 26 | 53% | 56% | 277 | 122 | 44% |
| delta | 28 / 11 | 12 | 8 | 67% |  | 57 | 26 | 47% |
| kagi / P&F / line-break | 56 / 40 | 31 | 21 | 69% | 112% | 126 | 32 | 25% |
| renko-type | 87 / 46 | 26 | 24 | 91% |  | 182 | 48 | 26% |
| range | 32 / 36 | 12 | 16 | 134% |  | 59 | 58 | 98% |

**(trigger x bar) blocks**: 154 blocks with any tested family-best, 27 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | imbalance / run (information) | 17 / 0 | 12 | 0 | 0% | 0% | 0% |
| bands | volume | 19 / 3 | 17 | 0 | 0% |  | 12% |
| levels:Fibonacci | event / swing / other | 10 / 8 | 7 | 0 | 0% |  | 56% |
| momentum | delta | 12 / 0 | 7 | 0 | 0% |  | 0% |
| levels:session / prior / round / opens / gaps | volume | 10 / 1 | 7 | 0 | 0% | 0% | 12% |
| levels:swing S/R, trendline, channel | time | 11 / 0 | 19 | 0 | 0% | 0% | 0% |
| levels:pivots | imbalance / run (information) | 9 / 1 | 7 | 0 | 0% |  | 0% |
| levels:VWAP | time | 10 / 3 | 9 | 0 | 0% |  | 0% |
| pullback | volume | 5 / 1 | 7 | 0 | 0% |  | 22% |
| trend | kagi / P&F / line-break | 7 / 4 | 9 | 0 | 0% |  | 16% |

### London (real tested 333 of 1,369 family-bests, null tested 454 of 1,739)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| cross-market | 36 / 21 | 21 | 0 | 0% |  | 136 | 61 | 45% |
| levels:Fibonacci | 45 / 51 | 12 | 15 | 124% | 93% | 127 | 126 | 99% |
| bands | 18 / 32 | 8 | 11 | 140% |  | 58 | 100 | 173% |
| tape / order flow | 36 / 49 | 8 | 15 | 186% |  | 111 | 138 | 124% |
| trend | 39 / 41 | 12 | 27 | 217% |  | 111 | 115 | 104% |
| bar-native | 7 / 4 | 0 | 0 |  |  | 25 | 15 | 62% |
| confluence | 3 / 5 | 0 | 4 |  |  | 12 | 15 | 124% |
| levels:VWAP | 23 / 20 | 4 | 0 |  |  | 86 | 54 | 62% |
| levels:pivots | 4 / 3 | 4 | 0 |  |  | 12 | 11 | 93% |
| levels:profile / stack / walls / UW | 1 / 20 | 0 | 11 |  |  | 4 | 61 |  |
| levels:session / prior / round / opens / gaps | 15 / 28 | 0 | 8 |  |  | 53 | 73 | 136% |
| levels:swing S/R, trendline, channel | 23 / 15 | 0 | 4 |  |  | 70 | 19 | 27% |
| levels:zones / supply-demand | 13 / 52 | 0 | 23 |  |  | 49 | 100 | 202% |
| mean reversion / manual indicators | 6 / 22 | 0 | 23 |  |  | 16 | 57 | 349% |
| momentum | 33 / 41 | 0 | 19 |  |  | 99 | 119 | 120% |
| order book | 25 / 19 | 4 | 8 |  |  | 82 | 50 | 61% |
| other trigger | 0 / 6 | 0 | 4 |  |  | 0 | 15 |  |
| pullback | 3 / 3 | 0 | 0 |  |  | 4 | 8 |  |
| session structure | 3 / 22 | 0 | 11 |  |  | 8 | 65 | 792% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| time | 95 / 106 | 37 | 31 | 83% | 140% | 292 | 303 | 104% |
| imbalance / run (information) | 36 / 50 | 16 | 23 | 140% |  | 119 | 146 | 122% |
| event / swing / other | 24 / 52 | 8 | 23 | 280% |  | 66 | 161 | 245% |
| composite / micro | 6 / 2 | 0 | 0 |  |  | 21 | 4 | 19% |
| delta | 7 / 11 | 0 | 11 |  |  | 29 | 38 | 133% |
| dollar | 5 / 7 | 4 | 8 |  |  | 16 | 4 | 23% |
| kagi / P&F / line-break | 26 / 28 | 0 | 19 |  |  | 78 | 23 | 29% |
| range | 27 / 33 | 0 | 11 |  |  | 86 | 111 | 129% |
| renko-type | 37 / 56 | 0 | 27 |  |  | 119 | 84 | 71% |
| tick | 21 / 18 | 4 | 11 |  |  | 58 | 61 | 106% |
| volume | 49 / 91 | 4 | 19 |  |  | 181 | 268 | 148% |

**(trigger x bar) blocks**: 151 blocks with any tested family-best, 4 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | imbalance / run (information) | 4 / 1 | 8 | 0 | 0% |  | 23% |
| cross-market | time | 16 / 8 | 21 | 0 | 0% |  | 53% |
| levels:Fibonacci | time | 7 / 14 | 12 | 4 | 31% | 47% | 155% |
| tape / order flow | imbalance / run (information) | 6 / 9 | 8 | 11 | 140% |  | 93% |

### NYAM (real tested 1814 of 7,377 family-bests, null tested 728 of 2,617)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| bands | 253 / 52 | 61 | 4 | 6% | 0% | 1009 | 169 | 17% |
| levels:profile / stack / walls / UW | 284 / 22 | 480 | 36 | 7% | 9% | 1135 | 58 | 5% |
| levels:VWAP | 118 / 16 | 37 | 7 | 20% |  | 464 | 47 | 10% |
| trend | 72 / 38 | 37 | 7 | 20% | 0% | 281 | 122 | 44% |
| levels:session / prior / round / opens / gaps | 230 / 69 | 61 | 22 | 35% | 133% | 895 | 165 | 18% |
| momentum | 121 / 42 | 37 | 18 | 49% |  | 472 | 133 | 28% |
| levels:Fibonacci | 210 / 58 | 57 | 29 | 51% | 177% | 817 | 151 | 18% |
| order book | 82 / 42 | 33 | 18 | 55% | 88% | 305 | 104 | 34% |
| session structure | 115 / 24 | 24 | 14 | 59% |  | 455 | 68 | 15% |
| levels:swing S/R, trendline, channel | 86 / 25 | 16 | 14 | 88% |  | 309 | 47 | 15% |
| cross-market | 45 / 38 | 12 | 11 | 88% |  | 171 | 119 | 69% |
| tape / order flow | 66 / 51 | 20 | 25 | 124% |  | 248 | 122 | 49% |
| levels:zones / supply-demand | 37 / 208 | 16 | 86 | 530% |  | 146 | 338 | 231% |
| bar-native | 17 / 10 | 4 | 7 |  |  | 69 | 29 | 42% |
| confluence | 11 / 5 | 0 | 0 |  |  | 41 | 11 | 27% |
| levels:pivots | 33 / 4 | 4 | 0 |  |  | 122 | 7 | 6% |
| mean reversion / manual indicators | 17 / 16 | 4 | 14 |  |  | 65 | 43 | 66% |
| other trigger | 4 / 2 | 0 | 0 |  |  | 16 | 4 | 22% |
| pullback | 13 / 6 | 0 | 0 |  |  | 53 | 18 | 34% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| tick | 134 / 40 | 106 | 4 | 3% | 22% | 533 | 122 | 23% |
| dollar | 35 / 9 | 28 | 4 | 13% | 22% | 138 | 4 | 3% |
| delta | 88 / 24 | 53 | 7 | 14% | 13% | 346 | 72 | 21% |
| volume | 268 / 88 | 130 | 25 | 19% | 27% | 1078 | 252 | 23% |
| event / swing / other | 198 / 105 | 98 | 25 | 26% | 59% | 769 | 273 | 36% |
| range | 95 / 57 | 20 | 7 | 35% |  | 358 | 151 | 42% |
| imbalance / run (information) | 227 / 104 | 134 | 54 | 40% | 41% | 862 | 255 | 30% |
| renko-type | 271 / 90 | 102 | 47 | 46% | 124% | 1053 | 122 | 12% |
| time | 327 / 150 | 163 | 90 | 55% | 65% | 1281 | 460 | 36% |
| kagi / P&F / line-break | 171 / 57 | 69 | 43 | 62% | 106% | 655 | 40 | 6% |
| composite / micro | 0 / 4 | 0 | 7 |  |  | 0 | 4 |  |

**(trigger x bar) blocks**: 173 blocks with any tested family-best, 38 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | renko-type | 27 / 4 | 8 | 0 | 0% |  | 14% |
| bands | tick | 23 / 3 | 8 | 0 | 0% |  | 12% |
| bands | volume | 60 / 9 | 12 | 0 | 0% | 0% | 13% |
| levels:Fibonacci | event / swing / other | 33 / 3 | 8 | 0 | 0% |  | 8% |
| levels:profile / stack / walls / UW | delta | 16 / 0 | 49 | 0 | 0% | 0% | 0% |
| levels:VWAP | volume | 14 / 1 | 12 | 0 | 0% |  | 6% |
| levels:VWAP | tick | 8 / 0 | 8 | 0 | 0% |  | 0% |
| levels:VWAP | event / swing / other | 19 / 3 | 8 | 0 | 0% |  | 15% |
| levels:profile / stack / walls / UW | dollar | 5 / 0 | 20 | 0 | 0% | 0% | 0% |
| momentum | renko-type | 11 / 4 | 8 | 0 | 0% |  | 27% |

### NYPM (real tested 191 of 749 family-bests, null tested 230 of 1,008)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| mean reversion / manual indicators | 18 / 10 | 12 | 4 | 37% | 37% | 71 | 35 | 50% |
| momentum | 15 / 14 | 20 | 9 | 45% | 45% | 55 | 61 | 112% |
| trend | 30 / 22 | 24 | 22 | 93% | 75% | 114 | 79 | 69% |
| order book | 23 / 11 | 31 | 31 | 98% | 156% | 90 | 31 | 34% |
| levels:swing S/R, trendline, channel | 7 / 8 | 8 | 9 | 112% |  | 24 | 22 | 93% |
| bands | 14 / 24 | 20 | 22 | 112% | 112% | 55 | 96 | 176% |
| levels:zones / supply-demand | 13 / 23 | 24 | 35 | 149% | 56% | 51 | 75 | 146% |
| cross-market | 15 / 14 | 16 | 26 | 168% | 168% | 59 | 57 | 97% |
| tape / order flow | 19 / 11 | 8 | 18 | 224% |  | 75 | 31 | 41% |
| bar-native | 1 / 4 | 0 | 0 |  |  | 4 | 13 |  |
| confluence | 4 / 2 | 4 | 4 |  |  | 16 | 9 | 56% |
| levels:Fibonacci | 9 / 22 | 4 | 18 |  |  | 27 | 79 | 287% |
| levels:VWAP | 7 / 7 | 0 | 0 |  |  | 27 | 31 | 112% |
| levels:pivots | 0 / 4 | 0 | 0 |  |  | 0 | 13 |  |
| levels:profile / stack / walls / UW | 9 / 15 | 0 | 13 |  |  | 35 | 48 | 137% |
| levels:session / prior / round / opens / gaps | 1 / 28 | 0 | 18 |  |  | 4 | 92 |  |
| other trigger | 1 / 0 | 4 | 0 |  |  | 4 | 0 |  |
| pullback | 1 / 3 | 0 | 9 |  |  | 4 | 13 |  |
| session structure | 4 / 8 | 4 | 0 |  |  | 16 | 22 | 140% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| renko-type | 14 / 22 | 20 | 9 | 45% | 37% | 55 | 44 | 80% |
| dollar | 3 / 5 | 8 | 4 | 56% | 56% | 12 | 0 | 0% |
| volume | 23 / 22 | 27 | 26 | 96% | 134% | 86 | 92 | 107% |
| imbalance / run (information) | 15 / 26 | 20 | 22 | 112% | 112% | 59 | 110 | 186% |
| range | 9 / 11 | 16 | 22 | 140% | 56% | 35 | 44 | 124% |
| time | 63 / 63 | 55 | 79 | 144% | 112% | 243 | 241 | 99% |
| tick | 20 / 19 | 8 | 13 | 168% | 56% | 78 | 83 | 106% |
| event / swing / other | 23 / 31 | 16 | 35 | 224% |  | 86 | 127 | 147% |
| composite / micro | 0 / 1 | 0 | 0 |  |  | 0 | 0 |  |
| delta | 10 / 12 | 4 | 13 |  |  | 39 | 53 | 134% |
| kagi / P&F / line-break | 11 / 18 | 4 | 13 |  |  | 35 | 13 | 37% |

**(trigger x bar) blocks**: 124 blocks with any tested family-best, 12 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| levels:zones / supply-demand | renko-type | 4 / 4 | 16 | 0 | 0% | 0% | 56% |
| momentum | range | 4 / 0 | 8 | 0 | 0% | 0% | 0% |
| order book | event / swing / other | 3 / 0 | 8 | 0 | 0% |  | 0% |
| tape / order flow | imbalance / run (information) | 3 / 1 | 8 | 0 | 0% |  | 37% |
| order book | range | 2 / 1 | 8 | 4 | 56% | 56% | 56% |
| cross-market | volume | 2 / 2 | 8 | 4 | 56% |  | 56% |
| trend | time | 12 / 8 | 12 | 9 | 75% | 37% | 65% |
| bands | time | 10 / 7 | 8 | 9 | 112% |  | 78% |
| order book | time | 5 / 2 | 8 | 9 | 112% | 112% | 45% |
| momentum | time | 5 / 5 | 8 | 9 | 112% | 112% | 140% |


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

## D8 spec date: Asia + NY AM only (order 0216Z; from D8_SPEC_STATUS.md, W-NYENG)

Updated 2026-11-21 06:30Z by W-NYENG. **RULE (order 1337Z): NO D8 build spec until the Asia AND NY AM ladders are COMPLETE**: every ladder cell has its first look, and every cell that beats a live book has prior years, controls, layers, exit run and the today / REPLACE / ADD pick. No wave dates. London and NY PM follow (stages 2 and 3). Funnel model redone at 14:00Z from landed data (order 1400Z).

## STAGE 1 COMPLETE (Asia + NY AM): THREE dates from a funnel with explicit stage pass rates, at the current rate **13312 set-months/h** (HEALTH.md fleet rate; tp_admit last hour says a different number at times; W-COMPILED factor not yet available, W-FASTLADDER share not included)

**Funnel stages and rates read from landed NY AM data:** (1) first look: 3222 of 4557 ladder cells have REPLACE last-6-month + last-3-month rows; (2) BEATER under the W-ASIA gate (a REPLACE row beats today stack on BOTH L6M and L3M: ulcer lower, mean not lower, worst week and max DD not worse): **0.4% of looked-at cells (13 of 3222); 0.3% with a REPLACE-K7 row; the looser rule (ulcer < 0 and mean >= 0 only) gives 1.1% (36)** (uncalibrated, label BETTER; calibration caveat: the whole-search null gives per-mode FDR both-side 8-25%, long-only 12-18%, i.e. a share of these yes rows is noise); (3) PASS prior years + persistence (rule B: no RED year in 2023/24/25; pooled persistence >= 0.58): **7 of 14 yes rows with all three prior years landed pass = 50%** (3 of 10 cells); the 4 REPLACE-K7 beaters: 3 pass (L01811caa, L6a25b155 pass, L0f097450 RED 2023); Asia: 8 passers among the beaters evaluated (W-ASIA); (4) only PASSERS get 30 controls (ADD and REPLACE variants: 2 x 180), layers (347, W-LAYERS cost) and exit rows (438) = 877 set-months per passer; every beater gets prior years (37 per beating REPLACE set). REPLACE ONLY (order 1407Z): ADD rows are reference, not candidates, and are no longer queued; exit rows = top 3 recipes x REPLACE x (6+37) + 30 controls x 6 = 309.

**Remaining set-months that do NOT depend on the funnel:** NY AM first looks, REPLACE rows only, 0 (0 queued + -1936 unbuilt cells x 6; 6493 of 4557 cells built) + NY AM REPLACE vs the other live books for alive cells 74394 + Asia useful work as W-ASIA counts it after its gate (first looks 27k + a2 35k = 62000; follow-ups 4k prior years + 20k controls + 1.6k passer controls + 8 passers x layers/exit = 31880; total ~88k+). GATE applied to NY AM in the advance step at 14:25Z (same as Asia): prior years and controls only for sets that beat today stack on BOTH L6M and L3M; other cells wait in stage A2 for their a2 rows and drop out if none beats; 6,290 prior-year/control lines of non-beating sets were PARKED (parked_gate_1415.txt, 112 cells; 76 cells returned to A2).

| scenario | NY AM beaters share / pass rate | NY AM beaters -> passers | Asia beaters share / pass | NY AM follow-ups | Asia follow-ups | TOTAL set-months | hours | **STAGE 1 COMPLETE** |
|---|---|---|---|---|---|---|---|---|
| LOW (strict gate, half the measured share) | 0.2% / 50% | 9 -> 5 | 2.2% / 50% | 4452 | 15940 | 156786 | 12 | **2026-11-21 18:16Z** |
| BASE (STRICT gate, measured share less mid FDR) | 0.3% / 50% | 15 -> 8 | 3.0% / 50% | 7435 | 21736 | 165566 | 12 | **2026-11-21 18:56Z** |
| HIGH (strict gate, 3x: the a2 other-book rows add chances) | 1.2% / 80% | 55 -> 44 | 4.4% / 80% | 41235 | 31880 | 209509 | 16 | **2026-11-21 22:14Z** |
| VARIANT: LOOSER gate (ulcer < 0 and mean >= 0 only), measured share less mid FDR | 0.9% / 50% | 43 -> 21 | 3.0% / 50% | 20590 | 21736 | 178721 | 13 | **2026-11-21 19:55Z** |
| UPPER BOUND: every REPLACE beater gets everything (10% NY AM / 6.5% Asia) | 10.0% / 100% | 456 -> 456 | 6.5% / 100% | 420646 | 47095 | 604136 | 45 | 2026-11-23 03:53Z |

Scenario assumptions (REPLACE ONLY, STRICT gate = ulcer lower, mean not lower, worst week and max DD not worse on L6M and L3M): measured strict share 0.4%; LOW = half of it, 50% pass; BASE = the measured share minus the mid FDR 16.5% (calibration), pass rate = observed on the loose REPLACE yes rows (50%); HIGH = 3x the strict share, 80% pass; the LOOSER-gate row is a variant only. SMALL SAMPLE: 3222 REPLACE looks. Asia beater share 2.4% (W-ASIA strict rule: 15 of 614) / 4.4% / 6.5% (looser rule 50 of 766), Asia pass rates as NY AM. First looks alone (NY AM 0 + Asia 62000) end 2026-11-21 11:09Z. CAVEAT: the observed beater share comes from the cells looked at so far, which are the BEST screen-ranked ones (the ladder runs in rank order), so extrapolating it to all 9,081 cells over-states the BASE and HIGH rows; the true beater share of the tail is probably lower (LOW is the REPLACE-only bound). The biggest remaining uncertainty is the beater and pass share; the null calibration (R4) and the persistence/rule-B gates move it.

## ENGINE-SLOT SPLIT (re-proposed from remaining FIRST LOOKS, then gate-pass follow-ups; NOT applied)

Remaining first looks: Asia 62000 vs NY AM 0 (+74394 NY AM other-book rows) => **Asia 100% / NY AM 0%** (45% / 55% with the other-book rows) = ~6051 / ~7261 set-months/h at 13312/h; with the base-case follow-ups added the work ratio is NY AM 49% / Asia 51% (NY AM follow-ups 7435 vs Asia 21736): the follow-ups only exist for cells that pass, so they come AFTER the first looks, are small until prior years land, and are taken first by the mix when they appear. Proposal: start at **Asia 100% / NY AM 0%** (remaining first looks only; the other-book REPLACE rows are ordered behind the first looks of both ladders) and re-propose when the funnel is re-measured (each refresh of this page recomputes it). W-ASIA's passer controls (_asi/first.txt) stay first, my gate-pass follow-ups stay first in pending_l.txt / the front of pending_r5.txt; the mix file puts both unmixed ahead of the interleaved block. NY AM at the order's ~120/h would leave 682 h of work. NOT applied: the QUEUES.txt edit (replace the _asi/pending.txt and _nye/pending_r5.txt lines by /mnt/l2/l2vast/_split/pending_mix.txt, built by code/th_nyeng/ny_mix.py <NYAM share>, e.g. 0.41) waits for the lead.

## Early-rung exits (4c): lines queued for cells that already left the ladder

Cells with stage "out" in the NY advance state: 2636. Later-rung lines (other-book, prior-year, control) still queued for them: **44751** (the advance step queues a later rung only after the earlier one passes). Park rule: any such line goes to /mnt/l2/l2vast/_nye/parked_out_cells.txt (not deleted). Exclusion list for W-DEDUP: cell ids with stage out = L0002a6c1, L0005282f, L0018ff2b, L002c1849, L0044a103, L0058cdf3, L00850065, L0090f5ed, L00cd0e6d, L00e9ef7d, L00ef412d, L00fef5cb, L0136535f, L0182920f, L0197b199, L019c81b0, L01ae185e, L01b83d93, L01b97dac, L01cd5945, L01e74643, L01f834f4, L021c85b5, L021e14e5, L0224c876, L02307192, L0241909f, L026a3758, L026ad69c, L02723cac, L0273fc34, L02765b1f, L027c6cc7, L02831614, L029c1536, L02a2767a, L02b4f020, L02c1f662, L02cfd74a, L031c8045, L03386b6b, L034ad35a, L037aed2b, L03e7b395, L043a1f2f, L045258ba, L046a6492, L047eebef, L049809e9, L04ea9f43, L051c6e27, L05255e95, L05350e98, L054821e4, L055ac89e, L05a95eff, L05b58f9b, L05b61e71, L05bb5e36, L05bd6871, L05be8bd0, L05cb0fed, L05d10e51, L05da5391, L0603a437, L0612a129, L062d06b7, L06306ccb, L063957e8, L063c1550, L06498824, L064f893e, L065c2291, L065e7073, L065f9d2b, L066b4da5, L067005b1, L06aa5875, L06c57fb0, L06fadbb5, L0705a05d, L075c4f19, L076bc130, L078a5e9a, L0791d70f, L079831f2, L08192843, L081c185d, L084a28d4, L084b4ae5, L087795dd, L0877b982, L08800795, L088b9d9f, L0895d1e3, L08c1815f, L08c38a8a, L08c94e6b, L08ea80ff, L08fb2523, L08fdf737, L094ee8e5, L0954835d, L096ecbf0, L09a970bd, L09c6d6d3, L09c9a917, L09d31203, L09ffb6f6, L0a1cc2d1, L0a25b2c1, L0aa630a7, L0abb7a1b, L0ad0d152, L0ad82266, L0ae4276c, L0affdff7, L0b210a97, L0b3de8bf, L0b5ba349, L0b72deb0, L0b862a92, L0b912968, L0b924ab1, L0bac981a, L0bbad455, L0bd19933, L0bd23639, L0befceef, L0c1c976f, L0c57f821, L0c67403b, L0c9f7504, L0cb34690, L0cfba390, L0cfc9f8e, L0d076b19, L0d6ffbcc, L0d78dc15, L0d7bea1f, L0da1b058, L0db567f9, L0ddd0c84, L0de893ea, L0def03b2, L0e216308, L0e516f52, L0e6580fd, L0e66fc0a, L0e6c0a12, L0ebb3bcd, L0ec49802, L0eea692f, L0eeaa018, L0f097450, L0f0caadd, L0f11d2f7, L0f2d63e9, L0f369180, L0f7bdf78, L0f7fc89d, L0fcc21c7, L1001040b, L1002a0bc, L10034ba2, L1020a386, L1094396c, L10a16ec5, L10d4c341, L11089f98, L112a85d1, L113989a5, L1147431a, L1156cd89, L117e0a69, L11943366, L11a15a3f, L11b5e8ad, L11e9ae70, L121542b3, L122629e3, L12292353, L1229e64c, L12383ab4, L12527145, L125afd0d, L12e4d0fd, L12f5c759, L12fdfc4f, L1302527b, L1324f9a8, L135249e0, L137bee34, L13b168a3, L13e165bc, L140536f7, L141da13c, L143274ab, L14405016, L14536e72, L146cc6fa, L1478e42f, L14902834, L14fc7d8a, L152d3f10, L1531b023, L153a9ab3, L153afb99, L15658e51, L156b74b9, L15865e21, L1589e0b8, L15e18f8b, L16344500, L16638b11, L16653aa0, L16979056, L169b1d2c, L16cc39f8, L16ee356a, L171b4d9e, L1724f3fc, L1742f647, L175f93d1, L177e9dc7, L17b7bdc3, L17ba6352, L17ca8272, L1801f948, L180c47be, L182afd3b, L1839fa62, L183dfd38, L184718f3, L189d197c, L18ab065e, L18b04265, L18eca11f, L18edeabd, L18f42af2, L1920a20b, L1927d468, L19434493, L195228d7, L19724487, L197944f3, L1987f908, L19946d15, L19a46016, L19c3031f, L1a0b0159, L1a10b4db, L1a3942b7, L1a420174, L1a510d7b, L1a7566ab, L1a9381e0, L1aa656d8, L1aae5cce, L1afa7095, L1b0fee34, L1b11d123, L1b413cdd, L1b77a301, L1ba45273, L1bd2be11, L1beb50d9, L1c0f69fd, L1c215fe9, L1c484047, L1c78d4c3, L1ce5c41b, L1ce61a64, L1d01954c, L1d0a98af, L1d10906a, L1d5e03a7, L1dac4bd9, L1dcf9992, L1df6c4c4, L1e0094b0, L1e3eadf0, L1e598bee, L1e5b1425, L1e6c337c, L1ea0ce15, L1ec8e6ba, L1ecfba70, L1ed0fa64, L1edd58aa, L1ef57a6c, L1f11cb77, L1f1d8d7c, L1f54e46c, L1fb4ab90, L1fc11059, L1fcc3433, L2000ea19, L200d27da, L201241f4, L2013a2c5, L203bf57e, L2097d3c9, L20f3be94, L211a58e8, L2140f591, L21758c0c, L21804ff1, L2188c22d, L21bffd7e, L21f079b6, L21fe5256, L221d256d, L222f4157, L2230e4ef, L2256e557, L228a2c4a, L22b351ab, L22b5c5d1, L22c210e2, L22c23a4f, L22cf3215, L22fa6c21, L2370c106, L23837cc5, L2399df41, L23a8ffa7, L23b82a1a, L23e2415c, L24064aed, L241947c7, L2426d282, L242b9316, L2438b7d7, L2442c1b5, L24545c52, L248387e7, L24d39995, L24e2abe5, L24ec3736, L24ff1d01, L252c577e, L2534d6f6, L255279b1, L255ca251, L25b593e6, L25d1f525, L25fbf434, L260d78b5, L2622d15d, L262b1f30, L2630906f, L263240b3, L263b295b, L2645ba76, L264d7e66, L2658360c, L26844754, L268c3ab8, L26926259, L26a61131, L26bc8c42, L26d0772f, L26e54f31, L26e65624, L270b470f, L2716caa9, L27342af5, L27387e3d, L2760ba92, L277f0c3e, L2798c175, L279bb676, L27a925f8, L27a93ead, L27e33fce, L280828cf, L280f1e76, L28226f05, L2825bcb9, L28393d3d, L289938a5, L28c3922b, L28c7b1ec, L28d004bb, L28e26f99, L28e64696, L28e7ee31, L29004296, L29a45bf4, L29b1cd94, L29e37d0c, L29fc1281, L2a1ea5fc, L2a217456, L2a50f8b5, L2a5c0730, L2a5dcfc0, L2a742a35, L2a81cfaa, L2a92b331, L2a991366, L2ab63488, L2ab98e97, L2ac45f15, L2ad8fffe, L2adb7428, L2b046019, L2b270d89, L2b44c03d, L2b4514d3, L2b68e8cf, L2b7aff12, L2bc645bf, L2bc649b6, L2bdb718a, L2becd23c, L2bf347e6, L2c4dd9a2, L2c6e9844, L2c9b9cf7, L2ca4f4a3, L2cc89f59, L2cd163fd, L2cfb1c25, L2d03d6b6, L2d14dd62, L2d1b439e, L2d2c0745, L2d406d8d, L2d5edd35, L2d60df7d, L2d93a1a0, L2da2cbda, L2db929c4, L2db980e5, L2dbb7680, L2e0bed3e, L2e0ef61b, L2e181b44, L2e271e82, L2e2ccd59, L2e34b405, L2e45679e, L2e510b61, L2e5909ab, L2e80c11f, L2e8a8ca4, L2eb9ac1b, L2ebb89be, L2ed2f633, L2ed70e23, L2ee11b5d, L2ef64a84, L2efba6d1, L2f1f3552, L2f2f9eb4, L2f700179, L2f768198, L2f8b34e3, L2f955c5f, L2fa1b60e, L2fa66484, L2fb506f2, L2ff61f0d, L30285fae, L304690ea, L3087d3a6, L30a36b3a, L30ae34bf, L30dbe289, L30e2c8aa, L30e865c1, L30f291d2, L30f722b7, L31000131, L3122d86b, L312ec721, L3149f4d7, L317236ba, L317eb843, L318955eb, L31dfb6e1, L31e12baf, L3202c87d, L32591d74, L326e6dbb, L32bd2144, L32d949ad, L32fa8e4f, L330e8dcd, L3337d437, L334ee144, L3397cce5, L33c8a0f8, L340c2cd7, L3426e2ca, L3459244a, L34838b74, L348beda2, L349f88d1, L34aec419, L34cce709, L34d66961, L34f43745, L34f6f3be, L34fe6878, L35043254, L3516aa98, L3540f9c5, L35543636, L35865eb9, L359f1868, L35c0ca41, L35c3a359, L35d50d23, L35eb6ff8, L35f5eed5, L3639de42, L363a1b3f, L363b2f56, L366139ce, L3675f0b6, L36933b2e, L36a42d88, L36be878c, L36c08e2b, L36c9ab71, L36dfa540, L36fefaed, L3701b464, L370f08ca, L374b6353, L37703a29, L377cfb45, L37897907, L37aabc6f, L37ade7c5, L37d1e65c, L37d1fb4f, L37f97715, L381147e6, L381226e8, L384006e0, L384f5251, L385ef576, L38cb490c, L38ddd353, L38ff2b59, L3918a3d8, L39386b5b, L3972a209, L397666c1, L3976b0fa, L39829b3b, L398e3d35, L39ac1f11, L39b1ea06, L39ed8ccd, L39f71c1e, L39fb2fef, L3a04b806, L3a0ba550, L3a2694e8, L3a526873, L3a715e8f, L3a7c684e, L3aac4ec5, L3ab5aa26, L3ae959b8, L3aeeb473, L3af8be97, L3b3e085e, L3b424220, L3b69ccac, L3b71f2ea, L3bb089b1, L3c82df8a, L3c98eb9c, L3ca17510, L3ca5272c, L3cc1c4af, L3cced7f8, L3cf3cc92, L3d1e7da6, L3d56e554, L3d5908cd, L3d63f42f, L3d9d754d, L3dabd7b1, L3dfe790c, L3e01cb07, L3e09a62d, L3e2e8177, L3e30b414, L3e4745d2, L3e6ebc24, L3eac37a2, L3eb6b968, L3eb8a71c, L3eba69b2, L3efb907a, L3f42e214, L3f67e925, L3f7ccd9b, L3f80559b, L3f835c39, L3fa83ee7, L3fafaa41, L3fbe0f8d, L3fc6be0a, L4018afac, L4023189a, L4031b9d2, L4037ed5d, L40423672, L407b160c, L40924d61, L40a77049, L40b2b4e8, L40c7fa23, L40d2f769, L40d9aa92, L40e5f17a, L40ead751, L40f3022e, L4102de64, L41042978, L413810a9, L414e1c01, L416b3d1d, L416cf628, L417ae1e0, L418da6a8, L41a2726e, L41bfa428, L41c024f6, L41d3a8da, L41d7663a, L41eda10c, L421a104a, L42591c98, L42935176, L42a44cee, L42a84bee, L42a8b984, L42add3cb, L42e3c7b3, L42e4e838, L42efaeee, L42f0934d, L4312e79f, L431ee36f, L4325528b, L433d4e12, L434b9ec2, L43556521, L438d807b, L439967d6, L43a19ea6, L43a40e65, L43b8b5fc, L43e62d10, L43ed564f, L43f0cbfb, L440aa51b, L44290ea7, L4444a4fb, L4458af4a, L446188ad, L4466aa9d, L447dd78d, L4484cfe8, L44bb41a7, L453ecfdf, L454cb838, L455dc536, L456999ee, L4583d9bc, L45bbaa6b, L45e72f8b, L46207331, L4622a6c0, L46579599, L4661e113, L468da8f8, L46b53f6f, L46c24b4c, L46dde331, L46fe4393, L4701dc79, L47264998, L47304010, L474262d9, L4744d92c, L47498498, L475293ca, L476f2cf8, L47869ae0, L4790767b, L47a52047, L47d56981, L47e7770d, L48608497, L48932783, L489fccab, L48d4fb02, L48f47e3d, L4932c506, L494c9c2b, L49567689, L49a8f809, L49d08a7b, L4a24f6da, L4a47ecfe, L4a66271a, L4a797fb6, L4a8e59ae, L4abdf068, L4ad492bf, L4add28dc, L4ae5482c, L4aeda76f, L4b071713, L4b0bad8c, L4b38d852, L4b42fe1c, L4b441c50, L4b51b779, L4b68151c, L4ba451be, L4ba88afd, L4bc7af0e, L4bd61f67, L4c001809, L4c0b33ce, L4c308321, L4c3764e2, L4c537c8e, L4c6f5779, L4c999a55, L4cb2820a, L4cca4db9, L4ce63be3, L4cfde973, L4d02f598, L4d12c13c, L4d1c3ef6, L4d241143, L4d304103, L4d35ed46, L4d45ba78, L4d57892d, L4d6fa935, L4d86003a, L4dc70f06, L4dcb4c69, L4e7ea249, L4e86ff34, L4e89079d, L4ebf6aef, L4edfb499, L4ee926f6, L4f01fd13, L4f53b9d9, L4f8e54af, L4fad2a44, L4fcee346, L4fe05261, L4fe091df, L4feee47d, L502045bc, L50337495, L50480de3, L506c622d, L507be344, L5099d605, L50a5665c, L50ac6ff3, L50acdda1, L50b860ec, L50b89fdd, L50c6d69f, L510156b8, L511c7457, L5143d3f0, L51485330, L516f2dc5, L51770ecd, L518184b0, L51a6d5aa, L51b67adb, L51c8ffb1, L51e50abc, L51e522b3, L52019dcd, L52359bf4, L523f4d50, L52580550, L52599445, L52675c55, L527ded97, L52a72347, L52ac8a88, L52b13447, L52be9ac9, L52d28a9a, L52dbfc0d, L52ed55c7, L5305cf3e, L531ae882, L5328b71c, L53313fde, L533f8078, L534a5566, L537ea1d3, L53aaee00, L53c0e51b, L53efe2d0, L542e900e, L545061cd, L545ccc02, L54780f11, L54adb58c, L54d8b908, L54e0b82a, L54e6b087, L54f03ff2, L54f19bd2, L54f86171, L54f96471, L54fa9622, L5501bfd1, L5508ecfb, L551cd1c1, L552a330d, L553eb8c5, L554584d8, L55b31b0a, L55bd963b, L55d44545, L55df0ab1, L55e1a087, L55ee1500, L55f3b7f3, L55fd7be7, L5605c048, L56183d9a, L565ee1c6, L56645708, L56672b97, L56a7d9c9, L56accca6, L56ba2057, L56be7fe6, L56bef4be, L56d3cea4, L56d48d73, L56dd415f, L56e1fbca, L56e69508, L56e7a475, L56e860f2, L56e8c799, L56ea5eb4, L5709dd1f, L5713a6a9, L573287c3, L5733d1ad, L5761ce13, L5763b9e7, L576d6945, L57a97191, L57b7e03e, L57c78e97, L57d8c47a, L57d8f96b, L57ea3e87, L57ec07af, L58113f1d, L5814d305, L5816339b, L581fe059, L583ee5ee, L58426974, L587b902b, L589f1a47, L58b3a49d, L58f26282, L5916c8ec, L591a4128, L593814e9, L5975d66d, L597837ab, L59855e53, L598b62a5, L59b2e323, L59bcb8a0, L59ccbd13, L59cd944a, L59cedfda, L59db90b2, L5a26bc55, L5a49e86d, L5a4f924e, L5a7e1954, L5a7ea4d3, L5af81987, L5b0afc07, L5b58566d, L5b7d6160, L5b996354, L5b9bdc05, L5bb9ae2f, L5bc2b53f, L5bc2f9e3, L5c416c91, L5c4c8c9a, L5c621a0e, L5c6e8219, L5c734a00, L5c8005eb, L5ca77208, L5cab06cf, L5cb12f8a, L5ce83827, L5d3f1a13, L5d8bc4df, L5d924d7d, L5d9313d2, L5d947160, L5d98fe32, L5da0bf61, L5dbf4e7f, L5e004561, L5e34fba9, L5e609715, L5e791042, L5ea34e54, L5ed26bd1, L5efc8bef, L5f1c5b26, L5f272d80, L5f405e4b, L5f66d676, L5f677061, L5fb756ed, L5fc9aa6f, L5fd6dfa9, L5fdc44f3, L5fea27db, L600996c3, L601993d1, L60367862, L603d0d32, L604d6149, L604f14a8, L60588620, L6062f59c, L608566ab, L60936dc9, L60aed383, L60be582b, L60cd11cd, L6101cbb5, L610ea773, L6118cace, L611eae60, L61543455, L6160ac49, L617920b3, L617f2c33, L61d7e355, L61df5369, L61f26835, L62349ad9, L6280f775, L62858fef, L62a6a6b7, L62be2b4a, L62c40d88, L6316fefb, L631a8535, L632bb3c8, L63551a96, L638c37cf, L63a64a57, L63b1d509, L63cfa534, L63e31d95, L63e6b866, L64299ed3, L64390867, L645461b7, L6458d702, L6462ee07, L649a387a, L64a0b978, L64c39b71, L64f5a99a, L6503f0e4, L652327d9, L652677b2, L652fb177, L653b8ed4, L6554d8fe, L6571e1ac, L65b520d6, L65b8a0b0, L65c83e61, L65e06e99, L6621bbc2, L664e3068, L667e2870, L66832b96, L6690a4ef, L66b83fb4, L66b909fe, L66bdcf83, L673ca764, L6755b324, L676adf74, L6772d676, L67b0a7ce, L67b7724b, L67e9df70, L67f5ffb1, L67fe7ccd, L68052483, L68149535, L68324549, L68413e62, L684e3038, L68e60043, L68f4e8d6, L693cea16, L6943e1cd, L69514a8f, L69657a72, L69833019, L69f41f5a, L69f43e14, L6a860151, L6ae244ca, L6aeeefeb, L6af3e195, L6b5f4955, L6bc3bcfe, L6bc8f3db, L6bd8cb2b, L6beb7056, L6c027ebe, L6c29a05f, L6c30bdda, L6c7a85d4, L6ca4636d, L6cae62c9, L6caeead9, L6cb7d6ca, L6cb86f62, L6cc06261, L6cdb09b8, L6ce392af, L6cef7ca5, L6cfe503f, L6d023c1d, L6d0ae138, L6d0d3174, L6d22ac91, L6d238076, L6d320e88, L6d5f0d02, L6d7acb9f, L6d8f90c3, L6da65507, L6dc04b87, L6dc6bb7f, L6dee05b9, L6df41b86, L6e290953, L6e682703, L6e69b2d4, L6e7f2b8f, L6e8e0aef, L6e9d208b, L6e9ecc8f, L6eab502b, L6ec2719e, L6ed3c9c1, L6ee2777d, L6f15066f, L6f3bf2b9, L6f4eb19e, L6f5e753c, L6f77f23d, L6fef7e64, L6ffc3244, L7011bfdd, L7013e24e, L702e2d6c, L70343c28, L70486bd4, L704d02a2, L70823d25, L70b35a50, L70c61755, L70e4ced2, L70fbd6a7, L70fd7253, L7106c8c6, L7122a284, L71978ea7, L719f5381, L71a10b0f, L71b59d54, L71da7486, L71daf522, L71f4bd2b, L72172308, L7233ea11, L7263432c, L72ab23e1, L72c078f9, L72d58bd5, L72e5c622, L72e6dde2, L72f59729, L72f6e6b1, L72fdc22c, L7306d949, L731f3a21, L732f05d4, L73384090, L7339c1cb, L734ab4c9, L7383ec7a, L73b20f78, L73c56e14, L73dc26df, L7426d18c, L744678cc, L744b42c1, L746d97b0, L74786b57, L74a13309, L74a6c9ef, L74e90c8d, L75016070, L751246a1, L75194540, L751e4540, L752977db, L752a5b0f, L75313db5, L7531e86e, L755b7b45, L758554de, L75ad06c2, L75c2b2e8, L75de4f78, L75ebbf7e, L75f1fdb8, L7603df87, L7610594f, L76410239, L76472828, L766749ca, L767f6180, L769fdf33, L76a18e45, L76abde69, L76af7af3, L76c6e684, L76f6d4d9, L7703bc4f, L77082875, L771520f6, L7726a37e, L774d11d5, L775c6ba4, L77778fbc, L77d6cd95, L77dfcbf5, L77f905c5, L78513dc8, L786677f4, L78a006bc, L78bd81c9, L78d0c5ab, L78f9066d, L79185999, L7950d9dc, L795906ae, L7995a85a, L799c55c6, L799e254f, L79f0d907, L79fa5097, L7a22ed9f, L7a286ca9, L7a4853a6, L7ab44e34, L7aed5f8b, L7af47322, L7b2166a5, L7b4806a7, L7b97a139, L7bba069b, L7bbf8b53, L7beef37c, L7bf847be, L7c06b1a5, L7c0cf7f3, L7c19094f, L7c2c87c0, L7c41d4a6, L7c45db24, L7c4a7e49, L7c4dd17f, L7c72f10a, L7c78e1e0, L7cba8b63, L7ce10fc0, L7ceab7e8, L7d0c2b44, L7d141116, L7d146a6c, L7d2c80d3, L7d3fb55d, L7d45d71f, L7d6c87da, L7d8cd5e5, L7d987156, L7da67f74, L7dda4ced, L7dea73a2, L7e154c0b, L7e538796, L7e574fcb, L7e8ea045, L7ead5d0a, L7ebc49f8, L7edcde91, L7f0cf0be, L7f1a277b, L7f1a615a, L7f20db08, L7f2215b0, L7f23f0d5, L7f9a06b6, L7fa34284, L7fa58b3b, L7fb8e801, L7fbbbbf9, L7fbde8b6, L7fc2dbc1, L7fc55022, L7fc96650, L7fd69700, L803fc54c, L8048f575, L80601a3c, L8075c11f, L80982949, L80d6e0ff, L80daf7f5, L80e064e7, L80f5d118, L81377fdc, L81496bc7, L81563494, L815801d4, L815c404b, L81a1349f, L81aca565, L81c35275, L81c3d1d5, L81c84bd0, L81db65d9, L820b2c05, L821971d5, L825352cb, L82a1b367, L82ccbcfe, L82db62cd, L82e1549a, L82ff8520, L830279e4, L830f88ea, L8310df10, L8320d626, L8320f53b, L833f0033, L834a99a3, L834d6e6e, L8373b6bc, L838b99e4, L83b16e71, L83c1494a, L83cb030b, L83eac794, L83f71c07, L8401f8cb, L840f5f7e, L842f1df8, L84300656, L84427019, L84628858, L8468f260, L8471cc78, L84770a22, L84774342, L84863e53, L848867d4, L84cd04f5, L84d80bf5, L84d859eb, L84e9c82f, L85270851, L85449d5e, L8553d968, L85690f17, L85794fb2, L8580e226, L85a0a1d5, L85b668c2, L85f7d3fc, L8600f960, L861aa3a3, L861e2a8e, L862a0cae, L862d9ab1, L8641fbb7, L86479d0c, L8676df2e, L8680594b, L869f2909, L86d5766b, L86dbdc06, L86e16acd, L86f26d14, L87139436, L871447c2, L87220a58, L8733ef9d, L874ffc0f, L875f55f3, L8771e131, L8788e203, L879b75b9, L87b9fc38, L8820726f, L882e1068, L882f4a43, L885c8a2a, L887adb85, L88861a65, L88947603, L889c761a, L88b80995, L88be8410, L88e1fd2d, L88e35e21, L891a536b, L8922e1d6, L892e594d, L8941725a, L8965c8c7, L8975dd09, L897f65b4, L898956fe, L8989cde7, L899a9f36, L89c3b5af, L89f1e462, L8a3173ce, L8a4907eb, L8a68ae23, L8a7d04c3, L8a8ce12b, L8a8dd5b7, L8a916be1, L8a9b7c25, L8ab51756, L8acd231b, L8aea9772, L8b02f00b, L8b11ff26, L8b3681a5, L8b3c1fb4, L8b83a467, L8b8811f1, L8ba987c8, L8bb2da84, L8bbb0b37, L8bd95264, L8be740c3, L8be7c85c, L8c1a78c9, L8c4b5096, L8c550eff, L8ca48bdb, L8cb749c4, L8cbe83a3, L8d1a5580, L8d47873d, L8d78e68e, L8db3d632, L8dcfb4d2, L8dd00a3a, L8dd34d37, L8dfb9b8c, L8e0bf58c, L8e13a57c, L8e314322, L8e66ea83, L8e8dc6f4, L8e9a233e, L8ea2eab1, L8ea4dca6, L8eca41a9, L8ecd11aa, L8edda2ff, L8f00668e, L8f1d1c5c, L8f47a7f4, L8f47d900, L8f524235, L8f54230d, L8f56aa49, L8f9323d6, L8fdf88d6, L8fe0dc6f, L8fe502ea, L90064134, L9007bfba, L9014a4d5, L901d2bbd, L903563ec, L9041933c, L9054e007, L90842741, L909c8f30, L90ae9c29, L90aedba2, L90bfbec1, L90eb9cc7, L90f58e91, L9106a04a, L9118c160, L911955c6, L9120c667, L9156516a, L91862cb3, L9186778a, L91c36129, L91c467b3, L91d32833, L91e488ce, L91e91c9f, L91f0acb3, L91fd9dfb, L920ac862, L92464b35, L924f68dd, L928ee468, L92b1b0fc, L92dc4be3, L92dd4c51, L92ebdcab, L92ecc227, L9357bdb4, L9365ece7, L93794f0e, L9390e089, L9397d8c8, L93bc1735, L93d2a5a4, L93e7f7e5, L94012503, L94154ff3, L9424721f, L9431446c, L943b82de, L948f2a7e, L9492c749, L9513708b, L952ae1e6, L955779bc, L955d0fb7, L957a0544, L95986343, L95ac925b, L95b1cc17, L95b52595, L95d4d7ee, L96175d42, L962501c9, L9630abdc, L96424791, L9646c770, L964cfc29, L96667a53, L966b7824, L966b7e14, L9695f77a, L96cfe590, L9701bb1c, L973aa7a1, L979d76ad, L97c15119, L97f4935d, L98207abe, L9829add9, L984a3d00, L987e74b3, L98834592, L98a567fd, L98b90b0d, L98bf5082, L98db910f, L98fcd9fc, L99000f8d, L991aed94, L993c0e21, L995c6940, L9978660d, L99c985bf, L99dbb9f5, L9a097924, L9a31fb3f, L9a35d158, L9a40bd37, L9a48dc34, L9a54be1a, L9a60042a, L9a7573ee, L9a7c8987, L9a7c95c7, L9aa810ff, L9aae6a5c, L9acce162, L9ade175b, L9af16dc9, L9b0e3953, L9b369974, L9b47a6dc, L9b484c74, L9b63c11e, L9b6ba45f, L9b75bf6e, L9b82ecb0, L9b8ff1e8, L9b90af09, L9bc58ba8, L9be1b97b, L9c1665fd, L9c2e2756, L9c2f04fe, L9c2f07b6, L9c42dfd9, L9c4e7b7c, L9cac3be9, L9cb68314, L9cd2fb8a, L9cd73d37, L9ce0369c, L9cfefb4b, L9d0de52b, L9d13aad0, L9d3a9b50, L9d4afd2a, L9da0593e, L9df88dd8, L9e449cb7, L9e475d11, L9e706c57, L9ef5b92e, L9ef92fab, L9f205d28, L9f256d43, L9f2736bb, L9f43c17a, L9f5908cc, L9f795897, L9f7c2dc8, L9f82c225, L9f888218, L9f9895ce, L9fb53f3e, L9fc0238e, L9fcce4ee, L9fd6d3cd, La04ccde4, La059a8e8, La087e948, La092861b, La0df2f97, La0e358d7, La1617c6c, La173c238, La18530c1, La1a7dead, La1ad5c72, La1b03f77, La1ed8df7, La1f9c065, La201dd83, La2224db2, La22ae48e, La234f575, La24154d0, La264ac51, La27f1b5a, La2aacea4, La2cff349, La31fed71, La331a9c4, La33ccb77, La372e6e4, La392779d, La3c160fb, La3c6ca2b, La3e5bc8e, La3e7712e, La3f6cc14, La4220a70, La426485f, La43c188c, La4e6e160, La51fe54f, La51ffc94, La52d2c1d, La53db301, La55922ed, La583c5aa, La5a1a5ec, La5b0bcfe, La5b7b137, La6102ffc, La62b0509, La6a18088, La6a45b1a, La6b5a7c5, La6b9c2d7, La6bed6d1, La6c0ac4d, La6c7c86a, La6e1543c, La6fa6db0, La71c16a2, La7669404, La767493f, La77bcc04, La77de14e, La78a1509, La7a2caac, La7b04bd5, La82e4504, La838e0b6, La8600386, La86531b2, La872937f, La894b287, La8a5e841, La8ac7882, La8e5e7e2, La8f7d729, La92090fa, La93b236e, La96512f6, La9673c5c, La96d4160, La9822c36, La995cbb0, La9ab8331, La9ad0fb8, La9d542da, La9df4ffd, La9f18ec3, Laa0b84bc, Laa1822fa, Laaa5ec2f, Laac6b61d, Laaeddf1a, Lab047703, Lab0720e3, Lab0ec3ca, Lab1a7ed7, Lab1d6a4d, Lab2c0fb2, Lab3d9ea7, Lab7654ec, Lab808296, Lab93706f, Lab97c859, Lab985018, Lab9acb32, Lab9d4df1, Laba80657, Labb17390, Labb60ea5, Labbfc6bc, Labc8dbc9, Labf3c62a, Labfb47e3, Labfdfe10, Lac345377, Lac37d7eb, Lac3cf216, Lac579d20, Lac62031d, Lac76994b, Lac7d3921, Lac9e8320, Lacc49455, Lacc87c73, Lacd892bc, Lad2d1395, Lad2ec6e5, Lad357def, Lad63c18b, Lad86b83d, Lad9f94cb, Ladd53a6b, Laddc32be, Lade016da, Ladec93ae, Ladf04af5, Lae05081b, Lae1b59ec, Lae454011, Lae4ef3d8, Lae563906, Lae59160f, Lae82cd6d, Laec06f7b, Laed01acd, Laed493b7, Laed846e4, Laef2ac1b, Laef6b90b, Laf0ef8f6, Laf22310b, Laf2689c9, Laf443816, Laf45b00f, Laf525043, Laf7ca30a, Laf83feb6, Lafa90bf7, Lafae56ed, Lafd12a3a, Lafdf2d92, Lb006906b, Lb0124bd0, Lb02daf8b, Lb03ee94c, Lb071a273, Lb0870020, Lb08e1fc0, Lb0a6bb1a, Lb105aee7, Lb11c2951, Lb12a9333, Lb13de797, Lb15040db, Lb1620e99, Lb1626f1e, Lb18f77f6, Lb1a016ee, Lb1e0132e, Lb23d399b, Lb248e87c, Lb252d301, Lb281c517, Lb28f30c8, Lb309c9b6, Lb329b8db, Lb347f247, Lb3584e58, Lb35e02b8, Lb3716945, Lb37b2695, Lb38d54d5, Lb38d7ace, Lb3b49183, Lb3bbc875, Lb3d8483f, Lb3dbcf28, Lb3fb5d45, Lb418ad44, Lb4194da6, Lb4384927, Lb46b84fb, Lb46d2b5d, Lb47bf96b, Lb485b4db, Lb49349d6, Lb4b1526a, Lb4bab31c, Lb4bbb3a9, Lb4bfbcce, Lb4cf0569, Lb4dc542a, Lb4ee29cb, Lb4efe93c, Lb5101a28, Lb522f24c, Lb52cf323, Lb539046b, Lb549d698, Lb54b40e8, Lb5850682, Lb58f16e0, Lb5d2fb00, Lb5e5250e, Lb5f0a612, Lb6036ca8, Lb64c8095, Lb65d09de, Lb65f30c7, Lb68a4cab, Lb68ca576, Lb6e73388, Lb6eb44c0, Lb6ffbdd5, Lb701d405, Lb72863ed, Lb76182c2, Lb79c223b, Lb7a000dd, Lb7a70f38, Lb7b26a44, Lb7c0b3af, Lb7db97e8, Lb7dbc3eb, Lb7f59af4, Lb809e889, Lb80ebe50, Lb8122687, Lb843f6ae, Lb862970f, Lb878be20, Lb87e482d, Lb8b19f1b, Lb8ca29ce, Lb8da6068, Lb8fe4f02, Lb9026469, Lb9089eb6, Lb9132d05, Lb94871a4, Lb9673779, Lb97b2046, Lb980deee, Lb9818bde, Lb9827593, Lb98e2f4e, Lb99d7519, Lb99d98f2, Lb9c7c06a, Lb9c92372, Lb9ee345f, Lba0c4501, Lba14091f, Lba237eba, Lba29a9af, Lba356762, Lba78e25e, Lbb00ef18, Lbb156ec5, Lbb258b12, Lbb354843, Lbb3ca489, Lbb44a057, Lbb5b84f5, Lbb5e0a25, Lbb6282e1, Lbb790c0d, Lbb87d9d0, Lbb8dc803, Lbbb39855, Lbbb92057, Lbbc4bf98, Lbbcd5cc3, Lbbdd2890, Lbbfe1105, Lbc0346f3, Lbc0381e1, Lbc08b378, Lbc29a2c6, Lbc4ad3b5, Lbc5c1bcd, Lbc5c7d48, Lbc6bff7a, Lbc9fa243, Lbca70336, Lbcc110fa, Lbcc12e95, Lbcd1ab36, Lbcecd6c3, Lbd1a1d57, Lbd1fa46f, Lbd1fcf51, Lbd33e843, Lbdce3113, Lbdf4511e, Lbdf8bcd7, Lbdfee03a, Lbe00943c, Lbe0cbeff, Lbe22da27, Lbe237c25, Lbe3be987, Lbe56327b, Lbe660734, Lbe6afe3a, Lbe6d7430, Lbe72f2c0, Lbe9e3d0d, Lbef29736, Lbf234099, Lbf34e4a3, Lbf3789df, Lbf436b8f, Lbf545353, Lbf6346d0, Lbf9fe75f, Lbfa1e391, Lbfc8df2e, Lbfd07790, Lbfdb7dfe, Lc00ad456, Lc01e072e, Lc022f354, Lc02f38c2, Lc03a46d7, Lc06cbfac, Lc08f2494, Lc0aecc18, Lc0d81f93, Lc0dca47f, Lc0dd72a1, Lc0e4d836, Lc0e7664f, Lc0f729c5, Lc1246056, Lc126250b, Lc128c567, Lc161c6cc, Lc1628066, Lc19b44d0, Lc1a475fa, Lc1a70e6b, Lc1c83446, Lc1d11e40, Lc1d94ba8, Lc1e47628, Lc2011e03, Lc22d07b2, Lc233a071, Lc2584e21, Lc27358c8, Lc2b684bb, Lc2bfc3f9, Lc3390f4f, Lc34e9ecb, Lc3736705, Lc383ca5d, Lc38b4cdf, Lc38d50c0, Lc38f3a49, Lc3a18cab, Lc3ba596b, Lc3c035b6, Lc3caa40f, Lc3d82d67, Lc3ec3a0b, Lc43862b6, Lc43fbb59, Lc4721f8d, Lc4878165, Lc4b22b84, Lc4d48153, Lc4e81ec2, Lc51b2697, Lc55fc137, Lc56d7b55, Lc57a7dc1, Lc594c76e, Lc5e9e51b, Lc5ff363e, Lc63f7485, Lc658590a, Lc66b8fed, Lc67f4861, Lc6c9d811, Lc6d38e17, Lc6ea6ddc, Lc723e512, Lc7333ae2, Lc769c8d4, Lc795ea79, Lc798978c, Lc7c1031a, Lc7e078a6, Lc7edb246, Lc7fe753b, Lc809dcc5, Lc80e2b3b, Lc82a4584, Lc8319f0b, Lc8529cea, Lc855159d, Lc85f0504, Lc86f37e0, Lc87a725d, Lc88102f6, Lc889083d, Lc8bdb4c4, Lc8bdd411, Lc8c4d63c, Lc8d51dc7, Lc8db149b, Lc8ddba19, Lc8ff2505, Lc8ffb3b4, Lc93fc75f, Lc9565815, Lc957f6fa, Lc958d5ae, Lc96321a9, Lc9865b87, Lc988cdd9, Lc98c4c4d, Lc9a8e53d, Lc9ac6a20, Lc9af40e3, Lc9bff453, Lc9f81411, Lc9f984db, Lca05e1bf, Lca12add2, Lca1e2a0f, Lca23d282, Lca2ae877, Lca2b7f90, Lca2ed2a5, Lca3b09f4, Lca409c7e, Lca57ebf7, Lca705912, Lca715459, Lca7966bd, Lcaac4e91, Lcad5dd0b, Lcadfc3ce, Lcb060786, Lcb283002, Lcb28fbe2, Lcb2c3237, Lcb4b073d, Lcb68e5f2, Lcb6ecf59, Lcba8dba8, Lcbc592c1, Lcc0a810c, Lcc20ad67, Lcc5e6521, Lcc795980, Lcc850e75, Lccba36a3, Lccbd2e18, Lcccca0ec, Lccda4993, Lcd1b77c9, Lcd2d936c, Lcd2edf30, Lcd4b0473, Lcd7812d2, Lcd809ef6, Lcd80dfef, Lcd9d9059, Lcdc45c44, Lcdd6a540, Lcddeae3a, Lce0634e3, Lce070e31, Lce1c241f, Lce2e9a54, Lce34df6d, Lce4b6104, Lce4dfd58, Lce5eb359, Lce6950a5, Lceb1434d, Lcedf4347, Lcef44bf0, Lcf257d16, Lcf43b898, Lcf602ca4, Lcf77f890, Lcf7b1bd1, Lcf827520, Lcfb1584f, Lcfba9bac, Lcfbaf18c, Lcfd419bd, Lcfdf6a30, Lcfe53f35, Lcfe9f46f, Lcff778b4, Ld0162d47, Ld0528593, Ld05d76e4, Ld082f5f5, Ld0844984, Ld0858d06, Ld0d7e4a5, Ld0eb2c83, Ld10310dc, Ld119a29a, Ld122e780, Ld1249c5d, Ld13c4137, Ld1499727, Ld1a34233, Ld1a8a78d, Ld1b36b1c, Ld1c1d585, Ld1ca1795, Ld2339be1, Ld2393371, Ld24663d5, Ld2537ef3, Ld26d6b49, Ld2802d77, Ld2ada5cd, Ld2bcca50, Ld2d408f0, Ld2d5b852, Ld320a828, Ld366cdfb, Ld3890c77, Ld3898b7a, Ld3a554ed, Ld3d59cf2, Ld3fc6af5, Ld40210e6, Ld40c5e85, Ld43cc5bf, Ld4434fb1, Ld44453f3, Ld444b7ee, Ld453aa80, Ld45e4a44, Ld4cb48d4, Ld4f4dc11, Ld4ffc994, Ld520d64d, Ld52800f7, Ld52a5e45, Ld52e47f9, Ld5c3069b, Ld5db3fc6, Ld5efeebe, Ld62c5532, Ld6468e0c, Ld67ad4eb, Ld6949339, Ld6aa5f20, Ld6e14222, Ld6f467f5, Ld6f68b8b, Ld71bbcae, Ld7278aa9, Ld72a2543, Ld74b1319, Ld7a70858, Ld7af4e77, Ld7b0b337, Ld7ec0315, Ld816fdb5, Ld87ff441, Ld88184c8, Ld8a641f7, Ld8ca33eb, Ld8d80bea, Ld8fd1fde, Ld8fe2836, Ld9123959, Ld93d1d89, Ld94301ca, Ld95ec786, Ld977e8ae, Ld9b4da69, Ld9bd4b7e, Ld9cf8fc8, Ld9e75522, Ld9ea7454, Ld9efd61c, Ld9f65b85, Lda15a9cc, Lda1f5e90, Lda27b4d8, Lda5f6268, Lda741b04, Lda7d4b8a, Ldabc1ed4, Ldadbce78, Ldae9487b, Ldaec8f96, Ldaf19410, Ldb25cbfa, Ldb267313, Ldb57d502, Ldb7ce956, Ldb7ed572, Ldba12d28, Ldbb73b08, Ldbff49bd, Ldc1b06a0, Ldc1d49d6, Ldc2ae779, Ldc3ee3f7, Ldc56de94, Ldc5c13e5, Ldc68498a, Ldc6df549, Ldcbf4121, Ldccf874e, Ldcdc2f39, Ldcfb3195, Ldd1065dc, Ldd1b1ec8, Ldd2855e4, Ldd296159, Ldd4bfd77, Ldd5dd7c3, Ldd6284ee, Ldda3fdd8, Ldda65708, Lddbec61b, Lddc6c5b6, Lddee4cc4, Lddfb6fae, Lde046d66, Lde1573f8, Lde72d37e, Lde9221c3, Lde98fb81, Ldead827c, Ldeae2644, Ldeb50d1b, Ldeb5660c, Ldecfe020, Ldef7afd4, Ldf0605aa, Ldf2b55e9, Ldf302f57, Ldf38e52e, Ldf3c3956, Ldf51c69e, Ldf7e809e, Ldfb0438d, Ldfb5e2c7, Ldfd909fd, Ldfdf336d, Le0089501, Le018a97b, Le0214115, Le041d086, Le053ab26, Le05bf465, Le06dac74, Le0b8a8ef, Le0bc7ff4, Le0bf852b, Le0c08035, Le0c7dc98, Le0d695f3, Le0da99e2, Le1079bef, Le112193c, Le11e7e50, Le1a69b6c, Le1b9bdf2, Le1cf849f, Le1f36da0, Le2346467, Le27dc486, Le28c737a, Le2af8f09, Le2b0c62d, Le2c3f32b, Le2eca86d, Le2ef9480, Le30d987f, Le30edd5a, Le317b9c3, Le3193838, Le31f3d38, Le336ffa1, Le3677617, Le36ba157, Le379664f, Le3bcec31, Le3d0e260, Le3dd1918, Le40b9abb, Le410524d, Le425f80e, Le44c1a07, Le47f4a12, Le4827e79, Le494ddab, Le4a04da0, Le4bbdc2f, Le4dc99e0, Le4fb6a4a, Le5019545, Le5148785, Le515fbf3, Le524f406, Le534251c, Le5457a79, Le54a1a93, Le552bc50, Le553820b, Le569beb5, Le5b774e7, Le65793f6, Le65a8a1b, Le65f7dfd, Le6693872, Le6986a73, Le6a6e385, Le6ce5a44, Le6edc0a0, Le6fa0109, Le7151d87, Le727d1fa, Le73b152c, Le74aaf47, Le7510c0c, Le7632cf9, Le77940e3, Le788e239, Le7a560ab, Le7ab4d85, Le7df4086, Le81791ca, Le81a4b74, Le8370942, Le8403d39, Le84d9fae, Le86bf5b5, Le8808672, Le89974de, Le8fb57dd, Le93a1391, Le944b0b0, Le96a00db, Le9834b4a, Le9c56380, Le9cfb458, Le9df7c36, Lea2b23bb, Lea3ea462, Lea620d76, Lea76e661, Lea9f7833, Leaa56a12, Leac51c1d, Lead44495, Leadea611, Leadf052f, Leaf446d6, Leafac023, Leaff70d8, Leb17b96f, Leb4047f3, Leb4e2641, Leb6b083d, Leb79ee20, Leb9cbeb1, Lebcc51f5, Lebfbd7b8, Lec1c5f42, Lec367b3d, Lec4e334f, Lec6afe3f, Lec7b8293, Lec804905, Lec8e53a3, Led2c4867, Led33f60f, Led6a9009, Led8d70a3, Ledc65862, Leddd6d68, Lee0bf761, Lee29210c, Lee2d7061, Lee4f43d2, Lee8335cd, Lee87d71d, Lee8c3266, Lee8cb424, Leec2817d, Lef1792aa, Lef27b653, Lefa05e76, Lefa8aa6b, Lefe43a1e, Lefeaf41d, Lf01a7271, Lf024d52e, Lf02da26d, Lf0346d55, Lf04cbe7d, Lf071676b, Lf07baf14, Lf0aacb4f, Lf0ba6915, Lf0bcf2a1, Lf0c5a319, Lf0df3768, Lf0f1b7b4, Lf0f67949, Lf0f73b0d, Lf0fcd6ef, Lf1055f62, Lf1083387, Lf11a3e9a, Lf11a98f1, Lf11c3d85, Lf11e08be, Lf12362f0, Lf1339997, Lf14495be, Lf1449f12, Lf14b023e, Lf1515e4f, Lf1570b83, Lf198a9c6, Lf1d0db15, Lf1dc859d, Lf203a1b0, Lf2043c16, Lf2064fda, Lf24a84da, Lf257a50c, Lf25a4095, Lf27a4540, Lf28d1256, Lf29785c9, Lf29cffba, Lf29d4595, Lf2c2c58b, Lf2dc787e, Lf2e0fe4c, Lf2ec37d9, Lf328379c, Lf33795f9, Lf3466e88, Lf35a96c9, Lf363a0a1, Lf36e66f8, Lf3741df0, Lf3887b14, Lf3c276f9, Lf3c9a017, Lf3e5a367, Lf4015221, Lf4224a5d, Lf426d88e, Lf44d8b80, Lf46de2b6, Lf477c541, Lf4795738, Lf48a2c95, Lf4900ad5, Lf4ab5fb3, Lf4b03b73, Lf4c77e43, Lf4cde066, Lf4ff805f, Lf506479f, Lf519d769, Lf52b86c8, Lf535b77e, Lf54ad81e, Lf55a3150, Lf571998a, Lf5949ffb, Lf5b310af, Lf5b32f60, Lf5f34fdc, Lf6076558, Lf6165940, Lf62e16f5, Lf63aeb97, Lf63c85cf, Lf64b0403, Lf65721df, Lf66a1d60, Lf66c0105, Lf67302ad, Lf67c3049, Lf686cf2f, Lf6930346, Lf6937131, Lf6be7f5f, Lf6cd31d7, Lf6d6383f, Lf6de99d4, Lf6f02ac5, Lf6f51478, Lf6f5d3b2, Lf73471cd, Lf74144f7, Lf7493116, Lf76e3db4, Lf77b6655, Lf7cea791, Lf7f86fbf, Lf837960b, Lf862caf9, Lf873c97b, Lf87c5b7f, Lf880c587, Lf88e6d50, Lf8b83fa0, Lf8c636dd, Lf8cf358d, Lf8e1a552, Lf8e8a5d7, Lf905f710, Lf9060d90, Lf9224ca2, Lf925cabc, Lf928f675, Lf93cb093, Lf94521f7, Lf94730bc, Lf95bb21c, Lf967df3b, Lf9ac1929, Lf9d10dc9, Lf9d93f6b, Lf9ebca18, Lfa0b8527, Lfa3230fb, Lfa39613e, Lfa55d1a9, Lfa5912ed, Lfa59be33, Lfa672475, Lfa7696af, Lfaa4a496, Lfac25d3b, Lfadf2fcc, Lfaf34566, Lfaf84902, Lfb16b890, Lfb69580e, Lfb69b241, Lfb7da229, Lfb80a9ce, Lfb839ae4, Lfb998261, Lfbaee16e, Lfbc5fd62, Lfbc61c74, Lfbcde421, Lfbd48ceb, Lfc0fa772, Lfc41c8c2, Lfc7e914c, Lfc8753c0, Lfc8a41f2, Lfc8bd004, Lfcba7672, Lfcd3db5d, Lfcf3e0b2, Lfd188364, Lfd2c4d16, Lfd3fc422, Lfd4c2d53, Lfd4fbdee, Lfd59fc5b, Lfd6041ef, Lfd763b0d, Lfd863101, Lfda96112, Lfdaf68ab, Lfdce94ab, Lfdcf78c7, Lfdd046b4, Lfddda6fe, Lfdfd3f51, Lfdfe85e4, Lfe00f53f, Lfe090e35, Lfe129efa, Lfe12adb6, Lfe220297, Lfe2a2cd0, Lfe2d14f2, Lfe2dbc4b, Lfe4cf0cb, Lfe63b474, Lfe7a3941, Lfe900eef, Lfea79a99, Lfec96c3d, Lfee6ee88, Lff0074de, Lff154f6c, Lff15ab0c, Lff5072e1, Lff5bd358, Lff7224dd, Lff742a45, Lff888ddf, Lff8cabe0, Lff9aa73b, Lffae2865, Lffb0f715, Lffb1b796, Lffccad6c, Lffd711a2, Lffe0b8bb, Lffe7434b (file /mnt/l2/l2vast/_nye/ladder_adv_state.json, key stage starting with "out"); W-DEDUP does the sweep, I own the advance logic.


## Candidates under the persistence >= 0.58 gate and the ADD-vs-REPLACE rule (order 1324Z)

Rules (order 1407Z): REPLACE ONLY. The pick is always the REPLACE row; the ADD row is shown as a reference, not a candidate (supersedes the 1324Z ADD rule). REPLACE = the ADD stack with K7 switched off in the NY AM session, so the ADD stack WITHOUT K7 already exists as the REPLACE row: NO new "minus K7" engine set is needed (a K7-off-in-every-session set would only matter for K7's other sessions, which these rows leave untouched). Persistence = share of non-overlapping 2-week windows where the new stack is not worse than today's, POOLED over every month the set has run (last 6 months + prior years). Rule B colours from ny_ruleb (RED > 30% worse in a prior year). Stack columns are the whole stack (ulcer / max DD / worst week / mean $ per week, engine base lots, $4.84).

| cell | stack | window | ulcer | max DD | worst wk | mean $/wk | rule-B colour (worst %) |
|---|---|---|---|---|---|---|---|
| L01811caa | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L01811caa | REPLACE (candidate) | L6M | 9342 | -29253 | -15108 | +20510 | n/a (recent window) (-1%) |
| L01811caa | ADD (reference, not a candidate) | L6M | 8963 | -27538 | -14519 | +19873 | n/a (recent window) (-5%) |
| L01811caa | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L01811caa | REPLACE (candidate) | L3M | 10587 | -28995 | -13266 | +18707 | n/a (recent window) (-4%) |
| L01811caa | ADD (reference, not a candidate) | L3M | 10165 | -27538 | -11702 | +17640 | n/a (recent window) (-8%) |
| L01811caa | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L01811caa | REPLACE (candidate) | Y2025 | 29382 | -83155 | -34691 | +7360 | GREEN (-8%) |
| L01811caa | ADD (reference, not a candidate) | Y2025 | 27815 | -78940 | -38025 | +7984 | GREEN (-2%) |
| L01811caa | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L01811caa | REPLACE (candidate) | Y2024 | 24716 | -69388 | -39713 | +5169 | GREEN (+6%) |
| L01811caa | ADD (reference, not a candidate) | Y2024 | 25450 | -71363 | -38560 | +5073 | GREEN (+3%) |
| L01811caa | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L01811caa | REPLACE (candidate) | Y2023 | 15029 | -46397 | -21702 | +2254 | AMBER (+24%) |
| L01811caa | ADD (reference, not a candidate) | Y2023 | 16062 | -40960 | -18785 | +2944 | GREEN (+7%) |
| L6a25b155 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L6a25b155 | REPLACE (candidate) | L6M | 9238 | -29945 | -16733 | +19675 | n/a (recent window) (+6%) |
| L6a25b155 | ADD (reference, not a candidate) | L6M | 8981 | -28489 | -15872 | +19216 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L6a25b155 | REPLACE (candidate) | L3M | 10415 | -29945 | -16733 | +17400 | n/a (recent window) (+6%) |
| L6a25b155 | ADD (reference, not a candidate) | L3M | 10159 | -28489 | -15872 | +17034 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L6a25b155 | REPLACE (candidate) | Y2025 | 34575 | -93892 | -39081 | +7356 | GREEN (+3%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2025 | 31437 | -91723 | -43606 | +8231 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2024 | 28814 | -72026 | -37355 | +4549 | - |
| L6a25b155 | REPLACE (candidate) | Y2024 | 31815 | -69700 | -36113 | +5300 | GREEN (+10%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2024 | 32304 | -71936 | -34960 | +5448 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L6a25b155 | REPLACE (candidate) | Y2023 | 18087 | -48220 | -18408 | +2404 | AMBER (+15%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2023 | 15491 | -42932 | -16215 | +3088 | GREEN (+3%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | Y2025 | 27735 | -77634 | -32511 | +6709 | GREEN (+2%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | Y2025 | 26308 | -76028 | -34457 | +7579 | GREEN (-11%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | Y2024 | 26900 | -63077 | -38237 | +5219 | GREEN (+2%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | Y2024 | 28023 | -66257 | -35122 | +5297 | GREEN (-3%) |
| L0f097450 (twin of L21f079b6) | TODAY (JL3) | Y2023 | 19039 | -41848 | -17538 | +1797 | - |
| L0f097450 (twin of L21f079b6) | REPLACE (candidate) | Y2023 | 17341 | -46048 | -25258 | +1675 | RED (+44%) |
| L0f097450 (twin of L21f079b6) | ADD (reference, not a candidate) | Y2023 | 16744 | -46713 | -19840 | +2334 | GREEN (+13%) |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L3701b464 (twin of L21f079b6) | ADD (reference, not a candidate) | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L3701b464 (twin of L21f079b6) | ADD (reference, not a candidate) | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | Y2025 | 27735 | -77634 | -32511 | +6709 | GREEN (+2%) |
| L3701b464 | ADD | Y2025 | pending | | | | |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | Y2024 | 26900 | -63077 | -38237 | +5219 | GREEN (+2%) |
| L3701b464 | ADD | Y2024 | pending | | | | |
| L3701b464 (twin of L21f079b6) | TODAY (JL3) | Y2023 | 19039 | -41848 | -17538 | +1797 | - |
| L3701b464 (twin of L21f079b6) | REPLACE (candidate) | Y2023 | 17341 | -46048 | -25258 | +1675 | RED (+44%) |
| L3701b464 | ADD | Y2023 | pending | | | | |

| cell | pooled persistence REPLACE (months) | pooled persistence ADD (months) | RED years REPLACE / ADD | PICK | what is still needed |
|---|---|---|---|---|---|
| L01811caa | 0.59 (43 mo) | 0.60 (43 mo) | none / none | **REPLACE** (REPLACE: better on ulcer and mean $/wk, no RED year, pooled persistence 0.59 >= 0.58) [STRICT PASS (ulcer, mean, worst week and max DD all not worse on L6M and L3M)] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L6a25b155 | 0.59 (43 mo) | 0.65 (43 mo) | none / none | **REPLACE** (REPLACE: better on ulcer and mean $/wk, no RED year, pooled persistence 0.59 >= 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $1005; WORST WEEK L3M worse by $1005: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L0f097450 (twin of L21f079b6) | 0.55 (43 mo) | 0.58 (43 mo) | Y2023 / none | **none yet** (REPLACE: RED Y2023; persistence 0.55 < 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $3120; WORST WEEK L3M worse by $3120: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L3701b464 (twin of L21f079b6) | 0.55 (43 mo) | 0.59 (10 mo) | Y2023 / none | **none yet** (REPLACE: RED Y2023; persistence 0.55 < 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $3120; WORST WEEK L3M worse by $3120: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |

**Candidates passing recent months + no RED year + persistence >= 0.58:** L01811caa (REPLACE), L6a25b155 (REPLACE).
**Dates:** 30 controls: queued at the front (landing as the fleet reaches them, ~06 hours at 2,000 sm/h); layers + exit run: the layer programme per candidate is ~1,068 set-months (about 0.5 h of fleet) but needs the automatic layer builder (not built, my ETA 2026-11-20 12:00Z) and the exit engine families (builder not started); so the earliest "through everything" date for L01811caa and L6a25b155 (they stay first) is 2026-11-21 ~12:00Z, later if the exit engine builder starts late. L0f097450 (= L3701b464, same stream) is judged by the same ADD/REPLACE rule.

## STRICT criterion table (Asia / D8 rule: stack ulcer LOWER, mean $/wk NOT LOWER, worst week NOT WORSE, max DD NOT WORSE; L6M with L3M beside; REPLACE-K7 vs TODAY stack; engine base lots, $4.84)
| cell | window | metric | today | REPLACE-K7 | change | pass |
|---|---|---|---|---|---|---|
| L01811caa | L6M | stack ulcer (lower = better) | +9416 | +9342 | -75 | PASS |
| L01811caa | L6M | max drawdown | -31109 | -29253 | +1857 | PASS |
| L01811caa | L6M | worst week | -15728 | -15108 | +620 | PASS |
| L01811caa | L6M | mean $/wk | +18755 | +20510 | +1755 | PASS |
| L01811caa | L3M | stack ulcer (lower = better) | +11035 | +10587 | -448 | PASS |
| L01811caa | L3M | max drawdown | -31109 | -28995 | +2114 | PASS |
| L01811caa | L3M | worst week | -15728 | -13266 | +2462 | PASS |
| L01811caa | L3M | mean $/wk | +16098 | +18707 | +2609 | PASS |
| L01811caa | both | STRICT VERDICT | | | | **PASS** |
| L6a25b155 | L6M | stack ulcer (lower = better) | +9416 | +9238 | -178 | PASS |
| L6a25b155 | L6M | max drawdown | -31109 | -29945 | +1164 | PASS |
| L6a25b155 | L6M | worst week | -15728 | -16733 | -1005 | **FAIL** |
| L6a25b155 | L6M | mean $/wk | +18755 | +19675 | +919 | PASS |
| L6a25b155 | L3M | stack ulcer (lower = better) | +11035 | +10415 | -620 | PASS |
| L6a25b155 | L3M | max drawdown | -31109 | -29945 | +1164 | PASS |
| L6a25b155 | L3M | worst week | -15728 | -16733 | -1005 | **FAIL** |
| L6a25b155 | L3M | mean $/wk | +16098 | +17400 | +1301 | PASS |
| L6a25b155 | both | STRICT VERDICT | | | | **FAIL** |
| L0f097450 (twin of L21f079b6) | L6M | stack ulcer (lower = better) | +9416 | +9358 | -58 | PASS |
| L0f097450 (twin of L21f079b6) | L6M | max drawdown | -31109 | -29253 | +1857 | PASS |
| L0f097450 (twin of L21f079b6) | L6M | worst week | -15728 | -18848 | -3120 | **FAIL** |
| L0f097450 (twin of L21f079b6) | L6M | mean $/wk | +18755 | +21047 | +2291 | PASS |
| L0f097450 (twin of L21f079b6) | L3M | stack ulcer (lower = better) | +11035 | +10531 | -504 | PASS |
| L0f097450 (twin of L21f079b6) | L3M | max drawdown | -31109 | -28828 | +2281 | PASS |
| L0f097450 (twin of L21f079b6) | L3M | worst week | -15728 | -18848 | -3120 | **FAIL** |
| L0f097450 (twin of L21f079b6) | L3M | mean $/wk | +16098 | +19000 | +2902 | PASS |
| L0f097450 (twin of L21f079b6) | both | STRICT VERDICT | | | | **FAIL** |

## SLOT OPTIONS per candidate (REPLACE of one live NY AM book; engine rows, today stack vs REPLACE; base lots, $4.84; strict = ulcer lower, mean not lower, worst week not worse, max DD not worse)
| cell | replaces | window | ulcer today -> new | mean $/wk today -> new | worst week today -> new | max DD today -> new | strict (u / m / w / dd) | rule B colour 2025 / 2024 / 2023 | pooled persistence | STRICT verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| L01811caa | K7 | L6M | 9416 -> 9342 | +18755 -> +20510 | -15728 -> -15108 | -31109 -> -29253 | PASS / PASS / PASS / PASS | GREEN (-8%) / GREEN (+6%) / AMBER (+24%) | 0.59 (43 mo) |  |
| L01811caa | K7 | L3M | 11035 -> 10587 | +16098 -> +18707 | -15728 -> -13266 | -31109 -> -28995 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L01811caa | P7 | L6M | 9416 -> 8703 | +18755 -> +19469 | -15728 -> -14519 | -31109 -> -26864 | PASS / PASS / PASS / PASS | GREEN (+1%) / GREEN (+1%) / AMBER (+18%) | 0.66 (43 mo) |  |
| L01811caa | P7 | L3M | 11035 -> 9670 | +16098 -> +16931 | -15728 -> -11074 | -31109 -> -25684 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L01811caa | M7 | L6M | 9416 -> 8960 | +18755 -> +19318 | -15728 -> -13068 | -31109 -> -28070 | PASS / PASS / PASS / PASS | GREEN (-7%) / GREEN (-2%) / GREEN (-5%) | 0.60 (43 mo) |  |
| L01811caa | M7 | L3M | 11035 -> 10299 | +16098 -> +16604 | -15728 -> -11897 | -31109 -> -28070 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L01811caa | H7 | L6M | 9416 -> 9194 | +18755 -> +19509 | -15728 -> -15409 | -31109 -> -28439 | PASS / PASS / PASS / PASS | GREEN (-6%) / GREEN (+4%) / GREEN (+5%) | 0.61 (43 mo) |  |
| L01811caa | H7 | L3M | 11035 -> 10445 | +16098 -> +17094 | -15728 -> -11819 | -31109 -> -28439 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L6a25b155 | K7 | L6M | 9416 -> 9238 | +18755 -> +19675 | -15728 -> -16733 | -31109 -> -29945 | PASS / PASS / **FAIL** / PASS | GREEN (+3%) / GREEN (+10%) / AMBER (+15%) | 0.59 (43 mo) |  |
| L6a25b155 | K7 | L3M | 11035 -> 10415 | +16098 -> +17400 | -15728 -> -16733 | -31109 -> -29945 | PASS / PASS / **FAIL** / PASS |  |  | **FAIL** |
| L6a25b155 | P7 | L6M | 9416 -> 8733 | +18755 -> +18907 | -15728 -> -15244 | -31109 -> -26864 | PASS / PASS / PASS / PASS | GREEN (+12%) / GREEN (+12%) / GREEN (+15%) | 0.61 (43 mo) |  |
| L6a25b155 | P7 | L3M | 11035 -> 9649 | +16098 -> +16522 | -15728 -> -15244 | -31109 -> -26634 | PASS / PASS / PASS / PASS |  |  | **PASS** |
| L6a25b155 | M7 | L6M | 9416 -> 8807 | +18755 -> +18867 | -15728 -> -16068 | -31109 -> -29020 | PASS / PASS / **FAIL** / PASS | n/a (pending) / n/a (pending) / n/a (pending) | 0.46 (6 mo) |  |
| L6a25b155 | M7 | L3M | 11035 -> 10068 | +16098 -> +16183 | -15728 -> -16068 | -31109 -> -29020 | PASS / PASS / **FAIL** / PASS |  |  | **FAIL** |
| L6a25b155 | H7 | L6M | 9416 -> 9056 | +18755 -> +19068 | -15728 -> -15989 | -31109 -> -29389 | PASS / PASS / **FAIL** / PASS | n/a (pending) / n/a (pending) / n/a (pending) | 0.54 (6 mo) |  |
| L6a25b155 | H7 | L3M | 11035 -> 10237 | +16098 -> +16780 | -15728 -> -15989 | -31109 -> -29389 | PASS / PASS / **FAIL** / PASS |  |  | **FAIL** |

## ENGINE RULE B (prior-year gate) for the 4 NY AM K7 beaters (order 1122Z; full table also on NEW_BOOK_BEATS_LIVE_NYAM.md)

**SIGN CONVENTION (explicit).** Rule B columns below are "% WORSE than today s stack" (positive = WORSE, negative = better): ulcer % = (new-ref)/ref; max DD % and worst week % = (ref-new)/|ref|; mean $/wk % = (ref-new)/|ref| (lower mean = positive = worse). The dollar columns elsewhere on this page: "d ulcer negative = better" (lower ulcer), "d worst week +1,631 = the worst week is $1,631 LESS bad than today s stack", "d max DD positive = less deep", "d mean positive = more $/wk". RED > 30% worse, AMBER 15-30%, GREEN otherwise; cell colour = worst of the four metrics; the verdict needs no RED year; a year with no engine rows yet = pending (not fail).

**Rule B = engine (REPLACE / ADD row vs TODAY s stack, same year).** Rule A (screen: bare stream, prior-year weekly R > 30% worse than the cell s own L6M) only orders the queue and is shown in its own column from the shortlist.

| cell | variant | year | ulcer % worse | max DD % worse | worst wk % worse | mean $/wk % worse | colour | persistence (2-wk windows new stack not worse) | rule A (screen, queue order only) |
|---|---|---|---|---|---|---|---|---|---|
| L01811caa | both sides REPLACE K7 | 2023 | -21% | +11% | +24% | -25% | AMBER | 0.47 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2024 | -14% | -4% | +6% | -14% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2025 | -12% | -9% | -11% | -8% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2023 | -15% | -2% | +7% | -64% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2024 | -12% | -1% | +3% | -12% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides ADD | 2025 | -17% | -14% | -2% | -17% | GREEN | 0.77 | see shortlist |
| L01811caa | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2023 | -12% | +12% | +13% | -30% | GREEN | 0.53 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2024 | -3% | -8% | -6% | -16% | GREEN | 0.54 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2025 | -22% | -17% | -11% | -11% | GREEN | 0.69 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L0f097450 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L3701b464 | both sides ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L3701b464 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | both sides REPLACE K7 | 2023 | -4% | +15% | +5% | -34% | AMBER | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2024 | +10% | -3% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2025 | +3% | +3% | +0% | -7% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides ADD | 2023 | -18% | +3% | -8% | -72% | GREEN | 0.79 | see shortlist |
| L6a25b155 | both sides ADD | 2024 | +12% | -0% | -6% | -20% | GREEN | 0.54 | see shortlist |
| L6a25b155 | both sides ADD | 2025 | -6% | +0% | +12% | -20% | GREEN | 0.65 | see shortlist |
| L6a25b155 | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |

**Rule B verdict per row:**
- L01811caa both sides REPLACE K7: no RED year
- L01811caa both sides ADD: no RED year
- L01811caa long-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa long-only ADD: pending (no prior-year rows yet)
- L01811caa short-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa short-only ADD: pending (no prior-year rows yet)
- L0f097450 both sides REPLACE K7: RED year
- L0f097450 both sides ADD: no RED year
- L0f097450 long-only REPLACE K7: no RED year
- L0f097450 long-only ADD: no RED year
- L0f097450 short-only REPLACE K7: pending (no prior-year rows yet)
- L0f097450 short-only ADD: pending (no prior-year rows yet)
- L3701b464 both sides REPLACE K7: RED year
- L3701b464 both sides ADD: pending (no prior-year rows yet)
- L3701b464 long-only REPLACE K7: no RED year
- L3701b464 long-only ADD: no RED year
- L3701b464 short-only REPLACE K7: pending (no prior-year rows yet)
- L3701b464 short-only ADD: pending (no prior-year rows yet)
- L6a25b155 both sides REPLACE K7: no RED year
- L6a25b155 both sides ADD: no RED year
- L6a25b155 long-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 long-only ADD: pending (no prior-year rows yet)
- L6a25b155 short-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 short-only ADD: pending (no prior-year rows yet)
(date line unavailable: KeyError('A'))

## Clock order (addendum 1731Z): sessions are decided Asia -> London -> NY AM -> NY PM

Phase 1 is NOT split by session (one grid job feeds all four sessions), so the grid cores cannot be re-ordered by session without cost; what follows the clock order is the scoring and the later phases: scoring/ranking runs Asia first; in phases 3-4 each session is decided on the exact engine after the earlier session is final. Asia is NOT add-only: replace / add / mixed with a higher bar (drawdown first AND dollars, last 6 and 3 months, no red prior year, 30 controls, selection-corrected test).

## Top 10 Asia

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_400 | levels_vwap.break {"n": 3, "k": 0.5} | asym20u/10u | +930 | -376 | +0.60 | 254 | AMBER/AMBER/ok | L6M @1.5 stops +810 / @3 stops +866 |
| 2 | vib_700 | pullback_ema.count {"len": 50, "n": 4} | sym15u | +862 | +234 | +0.55 | 360 | AMBER/ok/AMBER | L6M @1.5 stops +624 / @3 stops <=0 or <100 tr |
| 3 | dol_350 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +629 | +930 | +0.40 | 416 | ok/ok/ok | L6M @1.5 stops +629 / @3 stops +616 |
| 4 | mrenko_20 | momentum_er.trend_z {"len": 10, "thr": 0.4} | plain60/60 | +870 | +360 | +0.56 | 432 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 5 | trb_400 | levels_vwap.break {"n": 3, "k": 0.5} | asym15u/30u | +602 | -390 | +0.39 | 226 | ok/ok/ok | L6M @1.5 stops +602 / @3 stops +538 |
| 6 | tsf_5_100 | structure_breakout.brk {"n": 40, "buf": 0.0} | sym15u | +670 | -804 | +0.43 | 236 | ok/ok/ok | L6M @1.5 stops +706 / @3 stops +248 |
| 7 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +713 | -429 | +0.46 | 293 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +749 |
| 8 | tsf_5_100 | bands_donchian.break_native {"clk": 5, "buf": 0.0} | sym15u | +738 | -862 | +0.47 | 260 | AMBER/AMBER/ok | L6M @1.5 stops +620 / @3 stops +386 |
| 9 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +634 | +74 | +0.41 | 386 | ok/ok/ok | L6M @1.5 stops +634 / @3 stops +598 |
| 10 | cusum_40 | momentum_rsi.mom_native {"len": 21, "lvl": 55} | plain60/60 | +562 | -75 | +0.36 | 470 | ok/ok/ok | L6M @1.5 stops +562 / @3 stops <=0 or <100 tr |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_400 | levels_vwap.break {"n": 3, "k": 0.5} | asym20u/10u | +758 | -385 | +0.49 | 271 | ok/ok/ok | strong on (b) too |
| 2 | vnorm_150 | levels_fibr_dev.false_break_native {"M": 2, "k": 0.5} | sym15u | +705 | -631 | +0.45 | 281 | ok/ok/ok | strong on (b) too |
| 3 | vnorm_150 | levels_fib5.break {"n": 1, "k": 0.0} | sym15u | +858 | -469 | +0.55 | 304 | AMBER/AMBER/ok | strong on (b) too |
| 4 | vnorm_150 | levels_fib5.break_native {"n": 1, "k": 0.0} | sym15u | +858 | -469 | +0.55 | 304 | AMBER/AMBER/ok | strong on (b) too |
| 5 | cusum_40 | momentum_rsi.mom_native {"len": 14, "lvl": 55} | plain60/60 | +624 | -45 | +0.40 | 608 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | vnorm_150 | levels_fib15.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +834 | -701 | +0.53 | 302 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 7 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 | +616 | +1066 | +0.39 | 777 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +605 | +1164 | +0.39 | 562 | ok/ok/ok | strong on (b) too |
| 9 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +561 | -724 | +0.36 | 313 | ok/ok/ok | strong on (b) too |
| 10 | trb_400 | levels_vwap.break {"n": 2, "k": 0.5} | asym15u/30u | +632 | +305 | +0.41 | 252 | ok/ok/ok | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_400 | levels_vwap.break {"n": 3, "k": 0.5} | asym20u/10u | +755 | -385 | +0.48 | 270 | ok/ok/ok | also positive on (b) |
| 2 | vnorm_150 | levels_fib5.break {"n": 1, "k": 0.0} | sym15u | +858 | -469 | +0.55 | 304 | AMBER/AMBER/ok | also positive on (b) |
| 3 | vnorm_150 | levels_fib5.break_native {"n": 1, "k": 0.0} | sym15u | +858 | -469 | +0.55 | 304 | AMBER/AMBER/ok | also positive on (b) |
| 4 | vnorm_150 | levels_fibr_dev.false_break_native {"M": 2, "k": 0.5} | sym15u | +741 | -631 | +0.47 | 280 | AMBER/ok/AMBER | also positive on (b) |
| 5 | cusum_40 | momentum_rsi.mom_native {"len": 14, "lvl": 55} | plain60/60 | +723 | +62 | +0.46 | 604 | ok/AMBER/ok | depends on today's stack |
| 6 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +626 | +1202 | +0.40 | 556 | ok/ok/ok | also positive on (b) |
| 7 | trb_400 | levels_vwap.break {"n": 2, "k": 0.5} | asym15u/30u | +688 | +305 | +0.44 | 251 | AMBER/ok/ok | also positive on (b) |
| 8 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +551 | -724 | +0.35 | 312 | ok/ok/ok | also positive on (b) |
| 9 | cusum_20 | bands_bollinger.break_native {"clk": 5, "k": 2.0} | plain60/60 | +682 | -1182 | +0.44 | 748 | ok/AMBER/ok | depends on today's stack |
| 10 | vol_500 | levels_mmove.break {"n": 2, "k": 0.5} | plain60/60 | +675 | -92 | +0.43 | 598 | AMBER/AMBER/AMBER | also positive on (b) |

## Top 10 London

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | typ_bmsgq_B080 | bands_atrchan.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 2 | typ_bmsgq_B080 | bands_envelope.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 3 | typ_bmsgq_B080 | bands_keltner.fade_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 4 | vol_500 | levels_trendline.break {"n": 2, "k": 0.25} | plain60/60 | +977 | -156 | +0.63 | 293 | AMBER/ok/ok | L6M @1.5 stops +908 / @3 stops <=0 or <100 tr |
| 5 | t3_entropy_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +1034 | +62 | +0.66 | 225 | AMBER/AMBER/ok | L6M @1.5 stops +1034 / @3 stops <=0 or <100 tr |
| 6 | trend_10 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +951 | +1213 | +0.61 | 212 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 7 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +861 | -83 | +0.55 | 230 | ok/ok/AMBER | L6M @1.5 stops +861 / @3 stops +783 |
| 8 | trb_700 | tape_delta.follow_native {"L": 3600, "z": 2.0} | sym15u | +705 | +865 | +0.45 | 156 | ok/ok/ok | L6M @1.5 stops +201 / @3 stops +477 |
| 9 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +687 | +276 | +0.44 | 269 | ok/ok/ok | L6M @1.5 stops +687 / @3 stops +877 |
| 10 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +898 | -1732 | +0.58 | 229 | AMBER/ok/AMBER | L6M @1.5 stops +898 / @3 stops <=0 or <100 tr |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | ha_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +908 | -79 | +0.58 | 239 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | typ_bmsgq_B080 | bands_atrchan.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 3 | typ_bmsgq_B080 | bands_envelope.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 4 | typ_bmsgq_B080 | bands_keltner.fade_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 5 | vnorm_700 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | sym15u | +946 | +1390 | +0.61 | 264 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +783 | -106 | +0.50 | 240 | ok/ok/ok | strong on (b) too |
| 7 | vol_2600 | levels_fib5.retest_native {"M": 10, "tol": 0.5} | plain60/60 | +791 | +384 | +0.51 | 611 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | dol_750 | levels_fib5.break_native {"n": 3, "k": 0.5} | asym20u/10u | +822 | -260 | +0.53 | 251 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | med_rngor_B200 | trend_ma_hma.cross {"len": 34, "width": 4, "hyst": 0.0} | sym15u | +736 | -344 | +0.47 | 260 | ok/ok/ok | strong on (b) too |
| 10 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +702 | +131 | +0.45 | 287 | ok/ok/ok | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +1175 | +593 | +0.75 | 236 | ok/AMBER/AMBER | also positive on (b) |
| 2 | vol_500 | levels_trendline.break {"n": 2, "k": 0.25} | plain60/60 | +984 | +224 | +0.63 | 347 | AMBER/ok/ok | also positive on (b) |
| 3 | ha_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 4 | kal_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 5 | med_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 6 | t3_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 7 | typ_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 8 | vnorm_700 | book_ice.follow {"thr": 1} | plain60/60 | +870 | -88 | +0.56 | 472 | ok/ok/AMBER | also positive on (b) |
| 9 | vnorm_700 | book_ice.follow_native {"thr": 1, "sm": 60} | plain60/60 | +870 | -88 | +0.56 | 472 | ok/ok/AMBER | also positive on (b) |
| 10 | volor_B130 | levels_fib5.retest {"M": 6, "tol": 0.5} | sym15u | +924 | +236 | +0.59 | 218 | AMBER/ok/ok | also positive on (b) |

## Top 10 NY AM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_entropy_B080 | levels_round.retest_native {"M": 6, "tol": 0.5} | sym15u | +2501 | +1601 | +1.60 | 348 | AMBER/ok/AMBER | L6M @1.5 stops +1806 / @3 stops +2299 |
| 2 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u | +2161 | +1183 | +1.39 | 258 | AMBER/ok/ok | L6M @1.5 stops +2298 / @3 stops <=0 or <100 tr |
| 3 | trb_2000 | levels_vwap.break {"n": 3, "k": 0.5} | sym15u | +1967 | -1066 | +1.26 | 242 | ok/ok/ok | L6M @1.5 stops +1725 / @3 stops +1714 |
| 4 | sessrng_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +2383 | +969 | +1.53 | 244 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +2096 |
| 5 | t3_qmid_B200 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1627 | +1246 | +1.04 | 347 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +991 |
| 6 | med_volor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +1842 | +959 | +1.18 | 289 | ok/ok/ok | L6M @1.5 stops +900 / @3 stops <=0 or <100 tr |
| 7 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +2133 | +679 | +1.37 | 380 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 8 | t3_micro_B200 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1552 | +1171 | +1.00 | 345 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +985 |
| 9 | tsf_2_400 | levels_swsr5.retest_native {"M": 6, "tol": 0.5} | sym15u | +1610 | +1155 | +1.03 | 278 | ok/ok/ok | L6M @1.5 stops +1243 / @3 stops +1523 |
| 10 | volor_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +1537 | +330 | +0.99 | 282 | ok/ok/ok | L6M @1.5 stops +1725 / @3 stops +1263 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_dltor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +2402 | +954 | +1.54 | 416 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 2 | sessrng_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +1985 | +624 | +1.27 | 296 | ok/ok/ok | strong on (b) too |
| 3 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1967 | +206 | +1.26 | 379 | AMBER/ok/ok | strong on (b) too |
| 4 | lbrk_5_40 | xmarket_fast.revert_ES {"w": 60, "thr": 2.0} | sym15u | +2111 | +831 | +1.35 | 145 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 5 | vnorm_1500 | momentum_willr.break {"len": 7, "lvl": 10} | sym15u | +1969 | +534 | +1.26 | 522 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 6 | med_micro_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1526 | +1131 | +0.98 | 485 | ok/ok/ok | bare only (not positive on own-stop) |
| 7 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1711 | +719 | +1.10 | 508 | ok/ok/ok | strong on (b) too |
| 8 | lbrk_4_20 | levels_fibr_dev.break {"n": 1, "k": 0.0} | sym15u | +1691 | -962 | +1.08 | 411 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | lbrk_4_20 | levels_fibr_dev.break_native {"n": 1, "k": 0.0} | sym15u | +1691 | -962 | +1.08 | 411 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1723 | +1816 | +1.10 | 497 | ok/ok/ok | bare only (not positive on own-stop) |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dol_1700 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | asym20u/10u | +2400 | +1447 | +1.54 | 133 | AMBER/ok/AMBER | depends on today's stack |
| 2 | sessrng_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +1995 | +566 | +1.28 | 181 | ok/ok/ok | also positive on (b) |
| 3 | trb_700 | levels_vwap.break {"n": 2, "k": 0.5} | asym15u/30u | +1601 | -790 | +1.03 | 216 | ok/ok/ok | also positive on (b) |
| 4 | dol_1100 | bands_keltner.walk_native {"clk": 5, "k": 1.0, "N": 2} | sym15u | +1556 | -107 | +1.00 | 204 | ok/ok/ok | also positive on (b) |
| 5 | dol_1100 | book_dwm.drift_follow_native {"L": 1800, "z": 1.5} | sym15u | +2142 | +502 | +1.37 | 299 | AMBER/ok/AMBER | depends on today's stack |
| 6 | trb_700 | levels_vwap.break {"n": 2, "k": 0.25} | asym10u/20u | +1574 | -598 | +1.01 | 216 | ok/ok/ok | depends on today's stack |
| 7 | trb_700 | levels_vwap.break {"n": 2, "k": 0.5} | sym30u | +1496 | -875 | +0.96 | 214 | ok/ok/ok | also positive on (b) |
| 8 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 9 | ha_bmsgq_B200 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1885 | -312 | +1.21 | 318 | ok/AMBER/ok | depends on today's stack |
| 10 | med_volor_B080 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u | +1448 | -307 | +0.93 | 257 | ok/ok/ok | depends on today's stack |

## Top 10 NY PM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | micro_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 2 | qmid_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 3 | trb_700 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +1153 | -184 | +0.74 | 217 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +560 |
| 4 | tsf_10_60 | manual_macd.sigcross {"f": 5, "s": 13, "g": 5} | sym15u | +1208 | -331 | +0.77 | 204 | AMBER/AMBER/ok | L6M @1.5 stops +408 / @3 stops <=0 or <100 tr |
| 5 | tsf_10_60 | trend_macd.signal {"len": 6, "width": 0.0} | sym15u | +1176 | -355 | +0.75 | 204 | ok/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 6 | time_s_5 | bands_bollinger.walk {"n": 20, "k": 2.0, "N": 2} | plain60/60 | +995 | +365 | +0.64 | 353 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +390 |
| 7 | vib_70000 | tape_speed.fade_native {"f": 2.0, "L": 1800} | sym15u | +1013 | -88 | +0.65 | 143 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +347 |
| 8 | trb_700 | manual_macd.sigcross {"f": 12, "s": 26, "g": 9} | sym15u | +937 | +397 | +0.60 | 197 | ok/ok/ok | L6M @1.5 stops +1174 / @3 stops <=0 or <100 tr |
| 9 | ha_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 10 | ha_qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_700 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1452 | +1367 | +0.93 | 354 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 2 | dol_750 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1656 | -504 | +1.06 | 238 | AMBER/ok/ok | strong on (b) too |
| 3 | vib_15000 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1580 | +308 | +1.01 | 224 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 4 | tsf_2_100 | levels_trendline.break {"n": 3, "k": 0.5} | sym15u | +1489 | +512 | +0.95 | 264 | AMBER/AMBER/ok | strong on (b) too |
| 5 | dib_400 | tape_libvol.cmf {"len": 10} | plain60/60 | +1160 | +1543 | +0.74 | 1086 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | vib_70000 | tape_speed.fade_native {"f": 2.0, "L": 1800} | sym15u | +1081 | -253 | +0.69 | 195 | ok/ok/ok | strong on (b) too |
| 7 | vnorm_1000 | structure_level.round_reject {"grid": 50, "buf": 0.0} | sym15u | +1250 | +1252 | +0.80 | 322 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | dol_1700 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1099 | -1207 | +0.70 | 234 | ok/ok/ok | strong on (b) too |
| 9 | t3_sessrng_B200 | tape_libvol.obv {"len": 10} | plain60/60 | +1193 | +1124 | +0.76 | 794 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | vnorm_1500 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1134 | -1187 | +0.73 | 243 | ok/ok/ok | bare only (not positive on own-stop) |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | vib_15000 | book_pslope.follow {"L": 100, "z": 1.5} | sym15u | +1137 | +614 | +0.73 | 173 | ok/ok/ok | also positive on (b) |
| 2 | mrenko_14 | levels_fibr_dev.break {"n": 2, "k": 0.0} | plain60/60 | +1063 | +122 | +0.68 | 499 | ok/ok/ok | also positive on (b) |
| 3 | mrenko_14 | levels_fibr_dev.break_native {"n": 2, "k": 0.0} | plain60/60 | +1063 | +122 | +0.68 | 499 | ok/ok/ok | also positive on (b) |
| 4 | kal_rngor_B080 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1024 | +671 | +0.66 | 210 | ok/ok/ok | depends on today's stack |
| 5 | micro_B030 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1283 | +430 | +0.82 | 130 | ok/AMBER/ok | depends on today's stack |
| 6 | qmid_B030 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1283 | +430 | +0.82 | 130 | ok/AMBER/ok | depends on today's stack |
| 7 | vol_350 | levels_fibr_dev.break {"n": 3, "k": 0.25} | plain60/60 | +1033 | +694 | +0.66 | 528 | ok/ok/ok | depends on today's stack |
| 8 | volor_B130 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +984 | -925 | +0.63 | 152 | ok/ok/ok | depends on today's stack |
| 9 | kal_sessrng_B200 | levels_round.retest {"M": 6, "tol": 0.5} | plain60/60 | +1186 | +925 | +0.76 | 646 | ok/AMBER/ok | depends on today's stack |
| 10 | vib_10000 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +1003 | -479 | +0.64 | 144 | ok/ok/ok | depends on today's stack |

## Honest limits

- Rankings are best-of-many on the last 6 months; the selection-corrected best-pick null (phase 2b) is not applied yet to any row.
- Screen numbers are naked triggers; the engine rows (NEW_BOOK_ENGINE*.md) show layers and account rules change results both ways.
