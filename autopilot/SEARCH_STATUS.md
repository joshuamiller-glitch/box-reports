# SEARCH_STATUS - full-search programme (plan 1722Z: no Globex deadline), W-GRIDOPS, refreshed 2026-11-19 16:35Z

Plain words. Data end 2026-11-15 (NQ). Research only, no spend. Phases: 1 finish the whole search -> 2 prove it is not luck (30 controls, selection-corrected null, trust) -> 3 gates/layers one by one then jointly -> 4 D8 spec. Every number below is a screen-level number unless it says engine.

## Phase 1 - progress (the grid is not split by session: one job = one bar row x one trigger module x one tag; every session reads the same results, so the percentages below are the same for NY AM, NY PM, London and Asia)

| item | done | todo | jobs/hour (last 60 min) | ETA at that rate |
|---|---|---|---|---|
| pass 1, all tags (real + random-entry nulls 1/2 + extra null draws) | 192526 result files | 17 jobs | 4455 | 0.0 h |
| pass 2 (family cells, exits a2, top cells) | n/a | 16862 (a top cells 121, a2 exit families 569, c family cells 16172) | 1158 | 14.6 h |

NOTE (18:40Z): the grid is partitioned over server 2 (rows 0-1 of 12), A (2-6) and B (7-11) by W-S3; finished results are merged into server 2 every ~5 min (lag <= 10 min), the todo and worker counts are summed over the three servers. A and B also see 172 bar rows that are complete on box 1 but not yet on server 2, so total todo is higher than the earlier single-server figure (about +50%).

Pass-1 results on disk by tag: real 69071, null draw 1 48402, null draw 2 48158, extra draws (3-25) 21133 files. Pass-1 results still waiting for their pass-2 upgrade: real 57379.

Machines (grid partitioned across servers): 207.188.7.103 load 129.66 workers 86; 109.94.96.39 load 257.95 workers 104; 206.223.224.21 load 222.71 workers 104; grid workers 294 (84 computing), engine workers 444; forward-path tables built (summed over servers) 693.

Since 17:23Z: pass-1 todo 80818 -> 17 (-80801), pass-2 todo 25951 -> 16862 (-9089). Pass-2 todo grows when pass 1 delivers cells that earn pass 2.

## R4 - selection-corrected null of the whole search: FIVE draws, calibration check of the ladder (orders 1932Z + 2042Z; prereg sha 125fd12566e72aa6 + amendment)

What it is: 5 random-entry draws (tags p1rand1..p1rand5; draws 6-20 cancelled 20:42Z, files kept) of the SAME pass-1 search (every bar row x trigger module, same flags own-stop + account mask); the share of cells that pass R0-R3 in a null draw versus in the real search is the false-discovery rate, and the best cell of the null search versus the best of the real search is the best-pick comparison. Draws 1-2 run inside the real loops, draws 3-5 in dedicated null loops (A rows 2-6: 24 workers, B rows 7-11: 24 workers, server 2 rows 0-1: 6 workers; nice 8-10, below the engine (nice 0) and R3 (nice 5)). The null cells are also pushed through the same ladder R0-R3 as a CALIBRATION CHECK of the false-discovery rate the ladder claims. Only accepted draws count (null audit: independent side draw, pooled mean pts/trade at plain 60/60 negative and above -6 in every session, identical share under 1%, coverage at least 80%).

| item | now |
|---|---|
| results/hour, REAL search (p1real files, pass 1 and 2 together) | 119 |
| results/hour, NULL draws (p1rand1..20 files) | 4995 |
| null result files on disk, draws 1 / 2 | 48402 / 48158 (real: 69071) |
| null result files, draws 3-20 (all) | 20615 |
| share of the (row, module) files complete incl. error stubs, per draw (total ~65.8k jobs per draw; grid is not split by session, so every session sees the same share) | draw 1 76%, draw 2 76%, draw 3 8%, draw 4 8%, draw 5 7% |
| draws complete (files incl. error stubs >= 99.5 percent of ~65.8k) | 0 of 5 |
| draws accepted by the null audit and counted | see null_summary below |

Estimate: about 18 more full draws at the null share of the fleet (64 threads, ~25% of A + B) is roughly 60 hours (about 4,000 core-hours at the measured pass-1 rate; the order estimated ~6,300 core-hours); if that needs more than ~48 h the null share can be raised at the cost of the real search or machines added (Josh decides). False-discovery rate per session and the best-pick comparison appear here when W-SHORT has run the rule on the first accepted draws.

### False-discovery counts (W-SHORT, rule/null_summary.md: per accepted null draw per session, null cells passing vs the real search on the SAME coverage; ratio null/real = false-discovery ratio)

# NULL DRAWS vs REAL (same coverage) - cells passing R0 (bare) per session, W-SHORT 16:33Z

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
| Dallas | 12 | 1114 | 2473 | 24723 / 16663 / 15170 |
| Frankfurt | 1660 | 1483 | 1986 | 8608 / 4023 / 3439 |
| Singapore | 1657 | 791 | 1293 | 8725 / 6007 / 5258 |

Counts are the files on each host before the merge (A and B results are copied to Dallas every ~5 min); a host shows 0 stale for its own rows when its re-run is complete. Old copies of other hosts rows still on Dallas disappear as the merge overwrites them.

## Machines (hourly; busy % is measured from /proc/stat against the REAL thread count of each machine)

| machine | real threads | busy % | load1 | grid workers (computing) | engine workers | re-rank/other workers | results/hour (this machine) |
|---|---|---|---|---|---|---|---|
| server 2 Dallas | 64 | 100.0 | 129.66 | 294 (84) | 222 | 0 | 5613 |
| A Frankfurt | 128 | 100.0 | 257.95 | 104 (0) | 95 | 0 | 1097 |
| B Singapore | 128 | 100.0 | 222.71 | 104 (22) | 99 | 0 | 1682 |
| box 1 London (lead, engine fillers) | 32 | 100 | 79.12 | 0 | see CORES.md | - | - |

Server 2 has 64 threads (SMT off in firmware, order 1830Z check), A and B 128 each, box 1 32. Total jobs/hour and the phase-1 ETA are in the table above (sum over servers; double counting warning applies until W-S3 merges results). Any machine under 85% busy for 3 readings with work pending gets a one-line explanation in MORNING.md.

## Blocked / cannot run (listed, not skipped silently)

Failed jobs leave an error stub that the loop retries after 4 hours (older stubs are retried automatically). Error files on disk: {'real': 355, 'p1real': 1727, 'p1rand1': 1572, 'p1rand2': 1533, 'p1rand3': 16, 'p1rand4': 16, 'p1rand5': 16}.

| module | failures (files) | why |
|---|---|---|
| trig_book_ofi | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_cancel | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_ice | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_queue | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_pslope | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_dwm | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_imb | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_micro | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_thin | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_wall | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_sweep | 311 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_block | 305 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_run | 305 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_unfinished | 304 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_stack | 304 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_sizemix | 304 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
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

# SURVIVOR_COUNTS - the LADDER (cheapest test first; W-SHORT, orders 1845Z + 1932Z), refreshed 2026-11-19 16:21Z

No top-N cap anywhere. A cell leaves only by FAILING a test. Counts are bare (R0) from server-2 results only and PROVISIONAL (grid partitioned over servers until W-S3 merges; data week 189). Rungs not yet run say "n/a (reason)", never zero.

THRESHOLDS (equal risk; R = points / stop, stop = clip(bracket multiple x row bar unit, 10, 120), plain 60/60 = 60): R0 L6M (26 w) > 0; >= 100 trades in L6M; L3M (13 w) > 0; persistence > 0.60 (2-week windows since 2023-10 positive); prior years 2023/24/25 R per week not more than 30% below the cell's own L6M R per week (RED = shown, not delivered; AMBER 15-30% passes, counted). R1 = the same thresholds on the OWN-STOP result (2 stops; 1.5 / 3 shown): cells passing R0 but failing R1 are KEPT and labelled "depends on today's stack". R2 trust (brute-force tape walk) + look-ahead (6 truncation cuts) + fills >= signal + 1 s. R3 30 same-bracket random-entry draws, screen level: PASS = beats >= 27 of 30 (count shown at 24 / 27 / 29). R4 selection-corrected null of the same search (5 full null draws, same own-stop flags; calibration check of R0-R3 on null cells). R5 exact engine, staged.

FAMILIES = connected components of the grid neighbour graph over passing cells (same module.variant on an adjacent bar size of the same bar type, adjacent parameter of the same variant, or the identical parameter with another bracket / side); the best member (highest min(L6M R/wk, weakest prior-year R/wk)) runs first, neighbours after; nothing is dropped.

FLEET: 352 threads (Dallas 64, Frankfurt 128, Singapore 128, box 1 32), 90% busy assumed = 317 screen cores; engine set-months/hour measured 763 (box 1 450 + Dallas 313; A and B have no engine runs yet), projected 2894 with A and B engine-ready (ENGINE_PLAN.md s.11). Unit costs measured on WP10 / XA3 (PHASE2_TOOLING_TEST.md): R2 ~12 CPU-s per cell; R3 ~0.31 core-h per (row, module) pair (30 draws; cells sharing a pair share the draws); R4 ~317 core-h per full null draw = ~1,585 core-h for the 5 draws now planned (order 2042Z; shared by all four sessions; W-GRIDOPS ETA: draws 1-2 inside the real loops ~16 h, draws 3-5 ~62 h at the 25 percent share or ~30 h once real pass 1 is done); R5 engine 0.05 core-h per set-month measured on box 1 / Dallas (Frankfurt measured ~0.30: 1,072 s per month, starved), R5 stage a = 12 set-months per family (L6M as ADD and as replacement of the weakest live book), prior years +72, 30 date-shift controls +180 set-months (7.8 core-h at 0.043). All "hours" below are UPPER BOUNDS (no cell has failed R1-R3 yet) and assume the whole fleet for screen rungs (R4: its 25 percent share of A + B) and the measured 763 set-months/h for the engine.

## UNVERIFIED (stale level result) - notice, refreshed 16:20Z UTC

trig_levels_* grid results written BEFORE 2026-11-18 06:00Z predate the level-module fixes (13 of 17 level modules differ on a fresh re-run, W-GRIDOPS 0145Z); they are being re-run (Dallas from 01:33Z, Frankfurt / Singapore ~02:30Z, null draws 1-2 last). Until the result stamp (code hash on every result file) exists, every row below that touches a level module and a pre-06:00Z result is **UNVERIFIED (stale level result)**; non-level modules are not known to be affected (all-module check pending, order 0143Z). Stage-A p-values of R3 are computed with the CURRENT module code (fresh), but the cell SELECTION (R0) used the stale grid result; cells whose fresh L6M differs from the grid L6M by > 1 point are VOID (excluded).

| session | R0 passing cells | of which stale level cells | family-bests | stale family-bests | real-on-null-coverage tested (stage A) | stale level cells there | null draw tested (stage A) | stale level cells there |
|---|---|---|---|---|---|---|---|---|
| Asia | 6,487 | 6 (0.1%) | 3,847 | 3 | 900 | 2 (0%) | 364 | 15 (4%) |
| London | 3,158 | 0 (0.0%) | 2,237 | 0 | 333 | 0 (0%) | 454 | 15 (3%) |
| NYAM | 24,702 | 5 (0.0%) | 11,460 | 1 | 1814 | 0 (0%) | 728 | 45 (6%) |
| NYPM | 1,638 | 1 (0.1%) | 1,168 | 1 | 191 | 1 (1%) | 230 | 10 (4%) |

Reading: the stale share is NOT symmetric in the calibration: among tested family-bests 3-11% of the real-search cells but 17-26% of the null-draw cells rest on pre-06:00Z level files (the null draws were run early with the old level code), so the 01:16Z FDR table can be biased by the stale null side; it is redone after the forced re-run of draws 1-2 (last in the queue).


## Asia
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 9,797,654 | - | 9,791,167 | by first rule: R1 L6M<=0 5,284,669; R2 trades<100 2,110,557; R3 L3M<=0 821,434; R4 persistence<=0.60 1,381,960; RED prior year 192,547 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 6,487 (R0 passers) | 3,847 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 21.6 core-h for 6,487 cells | 0.1 h |
| R2 | trust + look-ahead | 6,487 (upper bound: all R1 cells) | 3,847 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 819 core-h for 2,642 (row, module) pairs | 2.6 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 6,487 (upper bound) | 3,847 | RUNNING: stage A (30 draws, same bracket, equal-risk) 1,885 of 3,847 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 521 / 182 / 31; reached stage B (200 draws) 769, C (1,000) 81, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 3,847 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 1240 / 1628 at q 5% / 10% / 20% | SET 1: 0, SET 2: 1240 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 3,158 (upper bound) | 2,237 | RUNNING: stage A (30 draws, same bracket, equal-risk) 806 of 2,237 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 49 / 9 / 2; reached stage B (200 draws) 303, C (1,000) 33, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 2,237 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 0 / 332 at q 5% / 10% / 20% | SET 1: 0, SET 2: 0 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 24,702 (upper bound) | 11,460 | RUNNING: stage A (30 draws, same bracket, equal-risk) 4,542 of 11,460 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 571 / 164 / 44; reached stage B (200 draws) 1515, C (1,000) 281, D (10,000) 2 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 11,460 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 3486 / 4229 at q 5% / 10% / 20% | SET 1: 0, SET 2: 3486 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 1,638 (upper bound) | 1,168 | RUNNING: stage A (30 draws, same bracket, equal-risk) 393 of 1,168 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 92 / 65 / 32; reached stage B (200 draws) 268, C (1,000) 14, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 1,168 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 307 / 370 at q 5% / 10% / 20% | SET 1: 0, SET 2: 307 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 14,016 set-months = 701 core-h | 18.4 h on the measured fleet (763/h), 4.8 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 1,168 families (upper bound) | 1,168 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+84,096 set-months) then 30 date-shift controls (+210,240 set-months = 10512 core-h) for the rows still alive | **110 h (> 48 h: Josh decides between more machines and waiting)** / **276 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 11,753,727; PASS **1,638 cells in 1,168 families** (non-reversal bars 1059, reversal 214 (provisional until the look-ahead gate), other 365; level / S-D modules 562; AMBER prior year(s) 346). Distinct (row, module) files among the passers: 979.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYPM.parquet; passing cells with family id / order / rank in family: pass_bare_NYPM.csv.

## R3 PASS SETS side by side (Benjamini-Hochberg across ALL family-bests of the session; untested cells count as p = 1; the counts grow as draws complete)

SET 1 (strict, current rule) = inside BH on p_L6M (last 26 weeks, equal-risk sum of R). SET 2 (proposed, order 2057Z) = inside BH on p_ALL (whole history, first month to today, L6M included) AND still passing R0 / R1 unchanged (every cell here already passed R0; R1 own-stop pending). Cells in SET 2 with p_L6M > 0.20 are flagged "recent no better than random" (shown, not dropped). p = (1 + k) / (1 + n), k = random draws at least as good, n = draws; weakest prior-year p shown separately. Engine order: SET 1 first, then SET 2 members best p first, no cap; Josh decides which set is the pass rule. Engine cost per passer: R5a 12 set-months + prior years 72 + 30 date-shift controls 180 = 264 set-months = ~13 core-h = 0.35 h at the measured 763 set-months/h. Dated D8 spec estimate: W-PLAN, ENGINE_PLAN.md.

| session | family-bests | tested | SET 1 q5 / q10 / q20 | SET 1 expected false (q10) | SET 1 engine core-h / h | SET 2 q5 / q10 / q20 | SET 2 expected false (q10) | SET 2 engine core-h / h | SET 2 flagged recent no better than random (q10) | smallest p: L6M / ALL |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,890 | 1,885 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 1240 / 1628 | 124.0 | 16368 / 429.0 h | 937 | 0.0249 / 0.0002 |
| London | 808 | 806 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 0 / 332 | 0.0 | 0 / 0.0 h | 0 | 0.0348 / 0.0010 |
| NYAM | 4,556 | 4,542 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 3486 / 4229 | 348.6 | 46015 / 1206.2 h | 3115 | 0.0230 / 0.0001 |
| NYPM | 396 | 393 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 307 / 370 | 30.7 | 4052 / 106.2 h | 237 | 0.0199 / 0.0010 |

## CALIBRATION: measured false-discovery rate from the whole-search null (order 2218Z, partial draw 1)

Label: PARTIAL / coarse (draw p1rand1 only, files that exist so far; the real search is restricted to the same (row, module) files and the pass-1 coverage; one family definition: same file + parameter). FDR(b) = expected null family-bests / real family-bests at the threshold "beats >= b of 30 draws" (p <= (31 - b + 1) / 31). Stage A only (30 draws): the finest p reachable is 0.032, so FDR <= 10% can only be read where it shows below.

| session | R0 pass cells null / real (ratio) | R0 families null / real | tested null / real (sampled family-bests) | stat | b = 24 | 27 | 29 | 30 |
|---|---|---|---|---|---|---|---|---|
| Asia | 380 / 963 (0.39) | 372 / 904 | 364 / 900 | p_L6M (null / real families at threshold = FDR) | 88 / 281 = 31% | 28 / 93 = 30% | 14 / 13 = 110% | 7 / 2 = 356% |
|  |  /  (0.00) |  /  | 364 / 900 | p_ALL (null / real families at threshold = FDR) | 227 / 840 = 27% | 169 / 744 = 23% | 112 / 604 = 19% | 66 / 428 = 16% |
| London | 466 / 347 (1.34) | 457 / 335 | 454 / 333 | p_L6M (null / real families at threshold = FDR) | 48 / 18 = 267% | 13 / 3 = 434% | 4 / 2 = 200% | 4 / 0 = n/a |
|  |  /  (0.00) |  /  | 454 / 333 | p_ALL (null / real families at threshold = FDR) | 316 / 261 = 121% | 242 / 197 = 123% | 164 / 121 = 136% | 93 / 91 = 102% |
| NYAM | 763 / 1,915 (0.40) | 730 / 1,821 | 728 / 1814 | p_L6M (null / real families at threshold = FDR) | 87 / 223 = 39% | 39 / 66 = 59% | 14 / 20 = 70% | 5 / 8 = 62% |
|  |  /  (0.00) |  /  | 728 / 1814 | p_ALL (null / real families at threshold = FDR) | 489 / 1746 = 28% | 397 / 1617 = 25% | 296 / 1328 = 22% | 196 / 994 = 20% |
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

## CALIBRATION, DEEPER RUNGS BY MODE (like with like: both-side cells vs both-side null cells, long vs long; order 1014Z)

| session | mode | statistic | p<=0.02 null / real = FDR | p<=0.005 | p<=0.001 | tested null / real (family-bests) |
|---|---|---|---|---|---|---|
| Asia | both | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 35 / 298 |
| Asia | both | p_ALL | 11 / 179 = 6% | 5 / 76 = 7% | 0 / 1 = 0% | 35 / 298 |
| Asia | long | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 328 / 600 |
| Asia | long | p_ALL | 30 / 198 = 15% | 10 / 86 = 12% | 1 / 5 = 20% | 328 / 600 |
| NYAM | both | p_L6M | 0 / 0 = n/a | 0 / 0 = n/a | 0 / 0 = n/a | 146 / 467 |
| NYAM | both | p_ALL | 70 / 290 = 24% | 34 / 120 = 28% | 1 / 1 = 100% | 146 / 467 |
| NYAM | long | p_L6M | 3 / 0 = n/a | 2 / 0 = n/a | 0 / 0 = n/a | 578 / 1346 |
| NYAM | long | p_ALL | 90 / 553 = 16% | 34 / 255 = 13% | 0 / 10 = 0% | 578 / 1346 |
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
| Asia | p_L6M | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 364 / 900 | 215 / 769 |
| Asia | p_ALL | 42 / 378 | 11% | 15 / 164 | 9% | 1 / 6 | 17% | 364 / 900 | 215 / 769 |
| NYAM | p_L6M | 3 / 0 | n/a | 2 / 0 | n/a | 0 / 0 | n/a | 728 / 1814 | 470 / 1606 |
| NYAM | p_ALL | 161 / 844 | 19% | 68 / 375 | 18% | 1 / 11 | 9% | 728 / 1814 | 470 / 1606 |
| London | p_L6M | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 454 / 333 | 0 / 0 |
| London | p_ALL | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 454 / 333 | 0 / 0 |
| NYPM | p_L6M | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 230 / 191 | 0 / 0 |
| NYPM | p_ALL | 0 / 0 | n/a | 0 / 0 | n/a | 0 / 0 | n/a | 230 / 191 | 0 / 0 |

## CALIBRATION BY FAMILY (order 0125Z; same footing as the table above: null draw 1 through the same stage A, p_L6M and p_ALL)

**UNVERIFIED FOR ALL "levels:*" TRIGGER FAMILIES (W-GRIDOPS 0145Z)**: trig_levels_* results written before 2026-11-18 06:00Z predate the level-module fixes (13 of 17 level modules differ on a fresh re-run); real AND null level cells are partly stale until the forced re-run lands (Dallas from 01:33Z, Frankfurt / Singapore ~02:30Z); read the levels:* rows as provisional and treat level-cell rows on the ladder lists as UNVERIFIED (ranked after verified cells). FDR(b) = null family-bests beating >= b of 30 draws / real family-bests beating >= b, per trigger family, bar family and (trigger x bar) block; counts are scaled to ALL family-bests of each set when only a part is tested (tested n shown). b = 24 / 27 shown on p_L6M with p_ALL beside. FDR < 100% = real > null; a block with real >> null is where the engine and the deeper stages go first; null >= real = last, not dropped. A block needs >= 5 real family-bests at b = 24 to be ranked (small counts give an unstable ratio). The best-of-many effect is shown by the number of blocks tested.

### Asia (real tested 900 of 904 family-bests, null tested 364 of 372)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| pullback | 34 / 9 | 18 | 2 | 11% | 10% | 33 | 5 | 15% |
| bands | 139 / 30 | 61 | 7 | 12% | 13% | 137 | 24 | 17% |
| momentum | 142 / 25 | 47 | 10 | 22% | 13% | 136 | 19 | 14% |
| session structure | 46 / 14 | 9 | 2 | 23% |  | 39 | 10 | 26% |
| levels:Fibonacci | 111 / 40 | 37 | 9 | 25% | 0% | 96 | 26 | 26% |
| levels:VWAP | 43 / 13 | 8 | 2 | 25% |  | 40 | 7 | 18% |
| levels:swing S/R, trendline, channel | 32 / 13 | 11 | 3 | 28% |  | 28 | 8 | 29% |
| trend | 89 / 38 | 27 | 11 | 41% | 85% | 85 | 30 | 35% |
| levels:session / prior / round / opens / gaps | 61 / 25 | 10 | 5 | 51% |  | 57 | 15 | 27% |
| levels:profile / stack / walls / UW | 46 / 17 | 6 | 3 | 51% |  | 45 | 8 | 18% |
| tape / order flow | 41 / 18 | 12 | 6 | 51% | 51% | 39 | 11 | 29% |
| cross-market | 26 / 17 | 15 | 10 | 68% | 41% | 22 | 16 | 74% |
| bar-native | 15 / 5 | 2 | 2 |  |  | 15 | 5 | 34% |
| confluence | 4 / 2 | 2 | 0 |  |  | 4 | 2 |  |
| levels:pivots | 17 / 8 | 4 | 0 |  |  | 15 | 3 | 20% |
| levels:zones / supply-demand | 14 / 55 | 2 | 4 |  |  | 11 | 14 | 129% |
| mean reversion / manual indicators | 13 / 10 | 3 | 2 |  |  | 11 | 8 | 74% |
| order book | 18 / 19 | 2 | 6 |  |  | 16 | 12 | 76% |
| other trigger | 9 / 6 | 4 | 2 |  |  | 9 | 2 | 23% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| imbalance / run (information) | 76 / 20 | 19 | 2 | 11% | 0% | 72 | 12 | 17% |
| volume | 115 / 33 | 45 | 8 | 18% | 7% | 109 | 28 | 25% |
| tick | 45 / 15 | 13 | 3 | 23% |  | 43 | 12 | 28% |
| time | 318 / 89 | 145 | 37 | 25% | 24% | 304 | 64 | 21% |
| event / swing / other | 129 / 71 | 21 | 10 | 48% | 51% | 118 | 47 | 40% |
| delta | 28 / 11 | 5 | 3 | 61% |  | 24 | 10 | 42% |
| kagi / P&F / line-break | 56 / 40 | 13 | 8 | 63% |  | 53 | 12 | 23% |
| renko-type | 87 / 46 | 11 | 9 | 83% |  | 77 | 18 | 24% |
| range | 32 / 36 | 5 | 6 | 122% |  | 25 | 22 | 90% |
| dollar | 14 / 3 | 4 | 1 |  |  | 13 | 0 | 0% |

**(trigger x bar) blocks**: 154 blocks with any tested family-best, 16 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | imbalance / run (information) | 17 / 0 | 5 | 0 | 0% |  | 0% |
| bands | volume | 19 / 3 | 7 | 0 | 0% |  | 11% |
| levels:swing S/R, trendline, channel | time | 11 / 0 | 8 | 0 | 0% |  | 0% |
| momentum | volume | 32 / 2 | 8 | 0 | 0% |  | 3% |
| pullback | time | 15 / 3 | 12 | 1 | 8% | 0% | 14% |
| levels:Fibonacci | time | 52 / 5 | 21 | 2 | 10% | 0% | 9% |
| bands | time | 67 / 7 | 38 | 4 | 11% | 20% | 9% |
| cross-market | volume | 8 / 1 | 6 | 1 | 17% |  | 15% |
| session structure | time | 17 / 4 | 6 | 1 | 17% |  | 24% |
| momentum | tick | 10 / 1 | 5 | 1 | 20% |  | 10% |

### London (real tested 333 of 335 family-bests, null tested 454 of 457)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| cross-market | 36 / 21 | 5 | 0 | 0% |  | 33 | 16 | 49% |
| bands | 18 / 32 | 2 | 3 |  |  | 14 | 26 | 186% |
| bar-native | 7 / 4 | 0 | 0 |  |  | 6 | 4 | 67% |
| confluence | 3 / 5 | 0 | 1 |  |  | 3 | 4 |  |
| levels:Fibonacci | 45 / 51 | 3 | 4 |  |  | 31 | 33 | 107% |
| levels:VWAP | 23 / 20 | 1 | 0 |  |  | 21 | 14 | 67% |
| levels:pivots | 4 / 3 | 1 | 0 |  |  | 3 | 3 |  |
| levels:profile / stack / walls / UW | 1 / 20 | 0 | 3 |  |  | 1 | 16 |  |
| levels:session / prior / round / opens / gaps | 15 / 28 | 0 | 2 |  |  | 13 | 19 | 146% |
| levels:swing S/R, trendline, channel | 23 / 15 | 0 | 1 |  |  | 17 | 5 | 29% |
| levels:zones / supply-demand | 13 / 52 | 0 | 6 |  |  | 12 | 26 | 217% |
| mean reversion / manual indicators | 6 / 22 | 0 | 6 |  |  | 4 | 15 |  |
| momentum | 33 / 41 | 0 | 5 |  |  | 24 | 31 | 129% |
| order book | 25 / 19 | 1 | 2 |  |  | 20 | 13 | 65% |
| other trigger | 0 / 6 | 0 | 1 |  |  | 0 | 4 |  |
| pullback | 3 / 3 | 0 | 0 |  |  | 1 | 2 |  |
| session structure | 3 / 22 | 0 | 3 |  |  | 2 | 17 |  |
| tape / order flow | 36 / 49 | 2 | 4 |  |  | 27 | 36 | 133% |
| trend | 39 / 41 | 3 | 7 |  |  | 27 | 30 | 111% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| time | 95 / 106 | 9 | 8 | 89% |  | 71 | 80 | 111% |
| composite / micro | 6 / 2 | 0 | 0 |  |  | 5 | 1 | 20% |
| delta | 7 / 11 | 0 | 3 |  |  | 7 | 10 | 143% |
| dollar | 5 / 7 | 1 | 2 |  |  | 4 | 1 |  |
| event / swing / other | 24 / 52 | 2 | 6 |  |  | 16 | 42 | 263% |
| imbalance / run (information) | 36 / 50 | 4 | 6 |  |  | 29 | 38 | 131% |
| kagi / P&F / line-break | 26 / 28 | 0 | 5 |  |  | 19 | 6 | 32% |
| range | 27 / 33 | 0 | 3 |  |  | 21 | 29 | 138% |
| renko-type | 37 / 56 | 0 | 7 |  |  | 29 | 22 | 76% |
| tick | 21 / 18 | 1 | 3 |  |  | 14 | 16 | 114% |
| volume | 49 / 91 | 1 | 5 |  |  | 44 | 70 | 159% |

**(trigger x bar) blocks**: 151 blocks with any tested family-best, 1 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| cross-market | time | 16 / 8 | 5 | 0 | 0% |  | 57% |

### NYAM (real tested 1814 of 1,821 family-bests, null tested 728 of 730)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| bands | 253 / 52 | 15 | 1 | 7% | 0% | 249 | 47 | 19% |
| levels:profile / stack / walls / UW | 284 / 22 | 118 | 10 | 8% | 10% | 280 | 16 | 6% |
| levels:VWAP | 118 / 16 | 9 | 2 | 22% |  | 114 | 13 | 11% |
| trend | 72 / 38 | 9 | 2 | 22% |  | 69 | 34 | 49% |
| levels:session / prior / round / opens / gaps | 230 / 69 | 15 | 6 | 40% |  | 221 | 46 | 21% |
| momentum | 121 / 42 | 9 | 5 | 55% |  | 116 | 37 | 32% |
| levels:Fibonacci | 210 / 58 | 14 | 8 | 57% |  | 202 | 42 | 21% |
| order book | 82 / 42 | 8 | 5 | 62% |  | 75 | 29 | 39% |
| session structure | 115 / 24 | 6 | 4 | 67% |  | 112 | 19 | 17% |
| tape / order flow | 66 / 51 | 5 | 7 | 140% |  | 61 | 34 | 56% |
| bar-native | 17 / 10 | 1 | 2 |  |  | 17 | 8 | 47% |
| confluence | 11 / 5 | 0 | 0 |  |  | 10 | 3 | 30% |
| cross-market | 45 / 38 | 3 | 3 |  |  | 42 | 33 | 78% |
| levels:pivots | 33 / 4 | 1 | 0 |  |  | 30 | 2 | 7% |
| levels:swing S/R, trendline, channel | 86 / 25 | 4 | 4 |  |  | 76 | 13 | 17% |
| levels:zones / supply-demand | 37 / 208 | 4 | 24 |  |  | 36 | 94 | 261% |
| mean reversion / manual indicators | 17 / 16 | 1 | 4 |  |  | 16 | 12 | 75% |
| other trigger | 4 / 2 | 0 | 0 |  |  | 4 | 1 |  |
| pullback | 13 / 6 | 0 | 0 |  |  | 13 | 5 | 38% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| tick | 134 / 40 | 26 | 1 | 4% |  | 132 | 34 | 26% |
| dollar | 35 / 9 | 7 | 1 | 14% |  | 34 | 1 | 3% |
| delta | 88 / 24 | 13 | 2 | 15% | 14% | 85 | 20 | 24% |
| volume | 268 / 88 | 32 | 7 | 22% | 30% | 266 | 70 | 26% |
| event / swing / other | 198 / 105 | 24 | 7 | 29% |  | 190 | 76 | 40% |
| range | 95 / 57 | 5 | 2 | 40% |  | 88 | 42 | 48% |
| imbalance / run (information) | 227 / 104 | 33 | 15 | 45% | 46% | 213 | 71 | 33% |
| renko-type | 271 / 90 | 25 | 13 | 52% | 140% | 260 | 34 | 13% |
| time | 327 / 150 | 40 | 25 | 62% | 73% | 316 | 128 | 41% |
| kagi / P&F / line-break | 171 / 57 | 17 | 12 | 71% | 120% | 162 | 11 | 7% |
| composite / micro | 0 / 4 | 0 | 2 |  |  | 0 | 1 |  |

**(trigger x bar) blocks**: 173 blocks with any tested family-best, 10 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| levels:profile / stack / walls / UW | delta | 16 / 0 | 12 | 0 | 0% | 0% | 0% |
| levels:profile / stack / walls / UW | dollar | 5 / 0 | 5 | 0 | 0% |  | 0% |
| levels:profile / stack / walls / UW | tick | 23 / 0 | 13 | 0 | 0% |  | 0% |
| levels:profile / stack / walls / UW | imbalance / run (information) | 32 / 6 | 20 | 1 | 5% | 0% | 16% |
| levels:profile / stack / walls / UW | volume | 46 / 1 | 17 | 1 | 6% | 0% | 0% |
| levels:profile / stack / walls / UW | kagi / P&F / line-break | 31 / 2 | 8 | 1 | 12% |  | 0% |
| levels:profile / stack / walls / UW | renko-type | 44 / 2 | 13 | 2 | 15% |  | 0% |
| bands | time | 76 / 12 | 6 | 1 | 17% |  | 15% |
| levels:profile / stack / walls / UW | time | 19 / 5 | 12 | 2 | 17% | 0% | 31% |
| levels:profile / stack / walls / UW | event / swing / other | 45 / 4 | 14 | 3 | 21% |  | 9% |

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

## D8 spec date: Asia + NY AM only (order 0216Z; from D8_SPEC_STATUS.md, W-NYENG)

Updated 2026-11-19 16:30Z by W-NYENG. **RULE (order 1337Z): NO D8 build spec until the Asia AND NY AM ladders are COMPLETE**: every ladder cell has its first look, and every cell that beats a live book has prior years, controls, layers, exit run and the today / REPLACE / ADD pick. No wave dates. London and NY PM follow (stages 2 and 3). Funnel model redone at 14:00Z from landed data (order 1400Z).

## STAGE 1 COMPLETE (Asia + NY AM): THREE dates from a funnel with explicit stage pass rates, at the current rate **4846 set-months/h** (HEALTH.md fleet rate; tp_admit last hour says a different number at times; W-COMPILED factor not yet available, W-FASTLADDER share not included)

**Funnel stages and rates read from landed NY AM data:** (1) first look: 301 of 9081 ladder cells have REPLACE last-6-month + last-3-month rows; (2) BEATER under the W-ASIA gate (a REPLACE row beats today stack on BOTH L6M and L3M: ulcer lower, mean not lower, worst week and max DD not worse): **0.7% of looked-at cells (2 of 301); 0.3% with a REPLACE-K7 row; the looser rule (ulcer < 0 and mean >= 0 only) gives 3.0% (9)** (uncalibrated, label BETTER; calibration caveat: the whole-search null gives per-mode FDR both-side 8-25%, long-only 12-18%, i.e. a share of these yes rows is noise); (3) PASS prior years + persistence (rule B: no RED year in 2023/24/25; pooled persistence >= 0.58): **6 of 7 yes rows with all three prior years landed pass = 86%** (2 of 3 cells); the 4 REPLACE-K7 beaters: 3 pass (L01811caa, L6a25b155 pass, L0f097450 RED 2023); Asia: 8 passers among the beaters evaluated (W-ASIA); (4) only PASSERS get 30 controls (ADD and REPLACE variants: 2 x 180), layers (347, W-LAYERS cost) and exit rows (438) = 1106 set-months per passer; every beater gets prior years (37 per beating REPLACE set). REPLACE ONLY (order 1407Z): ADD rows are reference, not candidates, and are no longer queued; exit rows = top 3 recipes x REPLACE x (6+37) + 30 controls x 6 = 309.

**Remaining set-months that do NOT depend on the funnel:** NY AM first looks, REPLACE rows only, 41732 (26204 queued + 2588 unbuilt cells x 6; 6493 of 9081 cells built) + NY AM REPLACE vs the other live books for alive cells 148248 + Asia useful work as W-ASIA counts it after its gate (first looks 27k + a2 35k = 62000; follow-ups 4k prior years + 20k controls + 1.6k passer controls + 8 passers x layers/exit = 31880; total ~88k+). GATE applied to NY AM in the advance step at 14:25Z (same as Asia): prior years and controls only for sets that beat today stack on BOTH L6M and L3M; other cells wait in stage A2 for their a2 rows and drop out if none beats; 6,290 prior-year/control lines of non-beating sets were PARKED (parked_gate_1415.txt, 112 cells; 76 cells returned to A2).

| scenario | NY AM beaters share / pass rate | NY AM beaters -> passers | Asia beaters share / pass | NY AM follow-ups | Asia follow-ups | TOTAL set-months | hours | **STAGE 1 COMPLETE** |
|---|---|---|---|---|---|---|---|---|
| LOW (strict gate, half the measured share) | 0.3% / 50% | 30 -> 15 | 2.2% / 50% | 19474 | 15940 | 287394 | 59 | **2026-11-22 03:48Z** |
| BASE (STRICT gate, measured share less mid FDR) | 0.6% / 86% | 50 -> 43 | 3.0% / 86% | 52423 | 21736 | 326140 | 67 | **2026-11-22 11:48Z** |
| HIGH (strict gate, 3x: the a2 other-book rows add chances) | 2.0% / 80% | 181 -> 145 | 4.4% / 80% | 176908 | 31880 | 460768 | 95 | **2026-11-23 15:35Z** |
| VARIANT: LOOSER gate (ulcer < 0 and mean >= 0 only), measured share less mid FDR | 2.5% / 86% | 227 -> 194 | 3.0% / 86% | 235906 | 21736 | 509622 | 105 | **2026-11-24 01:39Z** |
| UPPER BOUND: every REPLACE beater gets everything (10% NY AM / 6.5% Asia) | 10.0% / 100% | 908 -> 908 | 6.5% / 100% | 1088358 | 47095 | 1387433 | 286 | 2026-12-01 14:48Z |

Scenario assumptions (REPLACE ONLY, STRICT gate = ulcer lower, mean not lower, worst week and max DD not worse on L6M and L3M): measured strict share 0.7%; LOW = half of it, 50% pass; BASE = the measured share minus the mid FDR 16.5% (calibration), pass rate = observed on the loose REPLACE yes rows (86%); HIGH = 3x the strict share, 80% pass; the LOOSER-gate row is a variant only. SMALL SAMPLE: 301 REPLACE looks. Asia beater share 2.4% (W-ASIA strict rule: 15 of 614) / 4.4% / 6.5% (looser rule 50 of 766), Asia pass rates as NY AM. First looks alone (NY AM 41732 + Asia 62000) end 2026-11-20 13:54Z. CAVEAT: the observed beater share comes from the cells looked at so far, which are the BEST screen-ranked ones (the ladder runs in rank order), so extrapolating it to all 9,081 cells over-states the BASE and HIGH rows; the true beater share of the tail is probably lower (LOW is the REPLACE-only bound). The biggest remaining uncertainty is the beater and pass share; the null calibration (R4) and the persistence/rule-B gates move it.

## ENGINE-SLOT SPLIT (re-proposed from remaining FIRST LOOKS, then gate-pass follow-ups; NOT applied)

Remaining first looks: Asia 62000 vs NY AM 41732 (+148248 NY AM other-book rows) => **Asia 60% / NY AM 40%** (25% / 75% with the other-book rows) = ~1192 / ~3654 set-months/h at 4846/h; with the base-case follow-ups added the work ratio is NY AM 74% / Asia 26% (NY AM follow-ups 52423 vs Asia 21736): the follow-ups only exist for cells that pass, so they come AFTER the first looks, are small until prior years land, and are taken first by the mix when they appear. Proposal: start at **Asia 60% / NY AM 40%** (remaining first looks only; the other-book REPLACE rows are ordered behind the first looks of both ladders) and re-propose when the funnel is re-measured (each refresh of this page recomputes it). W-ASIA's passer controls (_asi/first.txt) stay first, my gate-pass follow-ups stay first in pending_l.txt / the front of pending_r5.txt; the mix file puts both unmixed ahead of the interleaved block. NY AM at the order's ~120/h would leave 2020 h of work. NOT applied: the QUEUES.txt edit (replace the _asi/pending.txt and _nye/pending_r5.txt lines by /mnt/l2/l2vast/_split/pending_mix.txt, built by code/th_nyeng/ny_mix.py <NYAM share>, e.g. 0.41) waits for the lead.

## Early-rung exits (4c): lines queued for cells that already left the ladder

Cells with stage "out" in the NY advance state: 60. Later-rung lines (other-book, prior-year, control) still queued for them: **0** (the advance step queues a later rung only after the earlier one passes). Park rule: any such line goes to /mnt/l2/l2vast/_nye/parked_out_cells.txt (not deleted). Exclusion list for W-DEDUP: cell ids with stage out = L00ef412d, L01ae185e, L02831614, L0bac981a, L0f097450, L0f11d2f7, L175f93d1, L1801f948, L1a10b4db, L1bd2be11, L21f079b6, L28e7ee31, L30ae34bf, L3516aa98, L36dfa540, L3d5908cd, L3dabd7b1, L47e7770d, L4b441c50, L537ea1d3, L54d8b908, L5ce83827, L617f2c33, L66b909fe, L73b20f78, L7af47322, L7f23f0d5, L81a1349f, L8a8dd5b7, L8e8dc6f4, L928ee468, L966b7824, L98834592, L9f888218, La5a1a5ec, La6a45b1a, La6e1543c, La872937f, La8f7d729, La96d4160, Lb4ee29cb, Lb8fe4f02, Lb9026469, Lc0dd72a1, Lca409c7e, Lce1c241f, Ld40c5e85, Ld6f467f5, Le788e239, Lea3ea462, Lec4e334f, Lf11e08be, Lf24a84da, Lf25a4095, Lf328379c, Lfa5912ed, Lfc41c8c2, Lfd4c2d53, Lfe2dbc4b, Lffb0f715 (file /mnt/l2/l2vast/_nye/ladder_adv_state.json, key stage starting with "out"); W-DEDUP does the sweep, I own the advance logic.

(pick table unavailable: FileNotFoundError(2, 'No such file or directory'))
(rule B table unavailable: FileNotFoundError(2, 'No such file or directory'))

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
| 9 | dib_2000 | momentum_rsi.mom {"len": 21, "lvl": 55} | plain60/60 | +537 | -340 | +0.34 | 727 | ok/ok/ok | also positive on (b) |
| 10 | tsf_10_60 | tape_delta.follow_native {"L": 900, "z": 1.0} | sym15u | +535 | +291 | +0.34 | 251 | ok/ok/ok | depends on today's stack |

## Top 10 London

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | typ_bmsgq_B080 | bands_atrchan.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 2 | typ_bmsgq_B080 | bands_envelope.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 3 | typ_bmsgq_B080 | bands_keltner.fade_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 4 | t3_entropy_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +1034 | +62 | +0.66 | 225 | AMBER/AMBER/ok | L6M @1.5 stops +1034 / @3 stops <=0 or <100 tr |
| 5 | trend_10 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +951 | +1213 | +0.61 | 212 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 6 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +861 | -83 | +0.55 | 230 | ok/ok/AMBER | L6M @1.5 stops +861 / @3 stops +783 |
| 7 | trb_700 | tape_delta.follow_native {"L": 3600, "z": 2.0} | sym15u | +705 | +865 | +0.45 | 156 | ok/ok/ok | L6M @1.5 stops +201 / @3 stops +477 |
| 8 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +687 | +276 | +0.44 | 269 | ok/ok/ok | L6M @1.5 stops +687 / @3 stops +877 |
| 9 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +898 | -1732 | +0.58 | 229 | AMBER/ok/AMBER | L6M @1.5 stops +898 / @3 stops <=0 or <100 tr |
| 10 | tsf_10_120 | xmarket_commod.against_CL {"w": 1, "thr": 1.0} | sym15u | +677 | +1721 | +0.43 | 175 | ok/ok/ok | L6M @1.5 stops +799 / @3 stops <=0 or <100 tr |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | typ_bmsgq_B080 | bands_atrchan.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 2 | typ_bmsgq_B080 | bands_envelope.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 3 | typ_bmsgq_B080 | bands_keltner.fade_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 4 | vnorm_700 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | sym15u | +946 | +1390 | +0.61 | 264 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +783 | -106 | +0.50 | 240 | ok/ok/ok | strong on (b) too |
| 6 | vol_2600 | levels_fib5.retest_native {"M": 10, "tol": 0.5} | plain60/60 | +791 | +384 | +0.51 | 611 | ok/ok/ok | bare only (not positive on own-stop) |
| 7 | dol_750 | levels_fib5.break_native {"n": 3, "k": 0.5} | asym20u/10u | +822 | -260 | +0.53 | 251 | ok/ok/ok | strong on (b) too |
| 8 | med_rngor_B200 | trend_ma_hma.cross {"len": 34, "width": 4, "hyst": 0.0} | sym15u | +736 | -344 | +0.47 | 260 | ok/ok/ok | strong on (b) too |
| 9 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +702 | +131 | +0.45 | 287 | ok/ok/ok | strong on (b) too |
| 10 | trb_400 | levels_piv_floor.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +815 | +8 | +0.52 | 213 | ok/ok/AMBER | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +1175 | +593 | +0.75 | 236 | ok/AMBER/AMBER | also positive on (b) |
| 2 | ha_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 3 | kal_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 4 | med_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 5 | t3_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 6 | typ_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 7 | vnorm_700 | book_ice.follow {"thr": 1} | plain60/60 | +870 | -88 | +0.56 | 472 | ok/ok/AMBER | also positive on (b) |
| 8 | vnorm_700 | book_ice.follow_native {"thr": 1, "sm": 60} | plain60/60 | +870 | -88 | +0.56 | 472 | ok/ok/AMBER | also positive on (b) |
| 9 | volor_B130 | levels_fib5.retest {"M": 6, "tol": 0.5} | sym15u | +924 | +236 | +0.59 | 218 | AMBER/ok/ok | also positive on (b) |
| 10 | rngor_B320 | book_queue.follow_sm {"thr": 0.3, "min": 3, "sm": 3} | sym15u | +704 | +434 | +0.45 | 122 | ok/ok/ok | also positive on (b) |

## Top 10 NY AM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u | +2161 | +1183 | +1.39 | 258 | AMBER/ok/ok | L6M @1.5 stops +2298 / @3 stops <=0 or <100 tr |
| 2 | trb_2000 | levels_vwap.break {"n": 3, "k": 0.5} | sym15u | +1967 | -1066 | +1.26 | 242 | ok/ok/ok | L6M @1.5 stops +1725 / @3 stops +1714 |
| 3 | t3_qmid_B200 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1627 | +1246 | +1.04 | 347 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +991 |
| 4 | med_volor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +1842 | +959 | +1.18 | 289 | ok/ok/ok | L6M @1.5 stops +900 / @3 stops <=0 or <100 tr |
| 5 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +2133 | +679 | +1.37 | 380 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 6 | t3_micro_B200 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1552 | +1171 | +1.00 | 345 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +985 |
| 7 | tsf_2_400 | levels_swsr5.retest_native {"M": 6, "tol": 0.5} | sym15u | +1610 | +1155 | +1.03 | 278 | ok/ok/ok | L6M @1.5 stops +1243 / @3 stops +1523 |
| 8 | volor_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +1537 | +330 | +0.99 | 282 | ok/ok/ok | L6M @1.5 stops +1725 / @3 stops +1263 |
| 9 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +2026 | +333 | +1.30 | 496 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +579 |
| 10 | vrb_1200 | xmarket_fast.revert_ES {"w": 60, "thr": 2.0} | sym15u | +1549 | +422 | +0.99 | 305 | ok/ok/ok | L6M @1.5 stops +1530 / @3 stops +1671 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_dltor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +2402 | +954 | +1.54 | 416 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 2 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1967 | +206 | +1.26 | 379 | AMBER/ok/ok | strong on (b) too |
| 3 | lbrk_5_40 | xmarket_fast.revert_ES {"w": 60, "thr": 2.0} | sym15u | +2111 | +831 | +1.35 | 145 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 4 | vnorm_1500 | momentum_willr.break {"len": 7, "lvl": 10} | sym15u | +1969 | +534 | +1.26 | 522 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 5 | med_micro_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1526 | +1131 | +0.98 | 485 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1711 | +719 | +1.10 | 508 | ok/ok/ok | strong on (b) too |
| 7 | lbrk_4_20 | levels_fibr_dev.break {"n": 1, "k": 0.0} | sym15u | +1691 | -962 | +1.08 | 411 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | lbrk_4_20 | levels_fibr_dev.break_native {"n": 1, "k": 0.0} | sym15u | +1691 | -962 | +1.08 | 411 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1723 | +1816 | +1.10 | 497 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | kal_qmid_B080 | bands_regchan.break_stderr_native {"clk": 20, "k": 2.5} | sym15u | +1956 | +1097 | +1.25 | 316 | AMBER/AMBER/ok | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dol_1700 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | asym20u/10u | +2400 | +1447 | +1.54 | 133 | AMBER/ok/AMBER | depends on today's stack |
| 2 | trb_700 | levels_vwap.break {"n": 2, "k": 0.5} | asym15u/30u | +1601 | -790 | +1.03 | 216 | ok/ok/ok | also positive on (b) |
| 3 | dol_1100 | bands_keltner.walk_native {"clk": 5, "k": 1.0, "N": 2} | sym15u | +1556 | -107 | +1.00 | 204 | ok/ok/ok | also positive on (b) |
| 4 | dol_1100 | book_dwm.drift_follow_native {"L": 1800, "z": 1.5} | sym15u | +2142 | +502 | +1.37 | 299 | AMBER/ok/AMBER | depends on today's stack |
| 5 | trb_700 | levels_vwap.break {"n": 2, "k": 0.25} | asym10u/20u | +1574 | -598 | +1.01 | 216 | ok/ok/ok | depends on today's stack |
| 6 | trb_700 | levels_vwap.break {"n": 2, "k": 0.5} | sym30u | +1496 | -875 | +0.96 | 214 | ok/ok/ok | also positive on (b) |
| 7 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 8 | ha_bmsgq_B200 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1885 | -312 | +1.21 | 318 | ok/AMBER/ok | depends on today's stack |
| 9 | med_volor_B080 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u | +1448 | -307 | +0.93 | 257 | ok/ok/ok | depends on today's stack |
| 10 | vnorm_1500 | levels_fibr_on.false_break_native {"M": 3, "k": 0.5} | sym15u | +1581 | +95 | +1.01 | 228 | ok/ok/ok | also positive on (b) |

## Top 10 NY PM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | micro_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 2 | qmid_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 3 | trb_700 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +1153 | -184 | +0.74 | 217 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +560 |
| 4 | tsf_10_60 | manual_macd.sigcross {"f": 5, "s": 13, "g": 5} | sym15u | +1208 | -331 | +0.77 | 204 | AMBER/AMBER/ok | L6M @1.5 stops +408 / @3 stops <=0 or <100 tr |
| 5 | tsf_10_60 | trend_macd.signal {"len": 6, "width": 0.0} | sym15u | +1176 | -355 | +0.75 | 204 | ok/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 6 | vib_70000 | tape_speed.fade_native {"f": 2.0, "L": 1800} | sym15u | +1013 | -88 | +0.65 | 143 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +347 |
| 7 | trb_700 | manual_macd.sigcross {"f": 12, "s": 26, "g": 9} | sym15u | +937 | +397 | +0.60 | 197 | ok/ok/ok | L6M @1.5 stops +1174 / @3 stops <=0 or <100 tr |
| 8 | ha_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 9 | kal_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 10 | kal_qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_700 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1452 | +1367 | +0.93 | 354 | ok/AMBER/ok | strong on (b) too |
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
| 2 | kal_rngor_B080 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1024 | +671 | +0.66 | 210 | ok/ok/ok | depends on today's stack |
| 3 | micro_B030 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1283 | +430 | +0.82 | 130 | ok/AMBER/ok | depends on today's stack |
| 4 | vol_350 | levels_fibr_dev.break {"n": 3, "k": 0.25} | plain60/60 | +1033 | +694 | +0.66 | 528 | ok/ok/ok | depends on today's stack |
| 5 | volor_B130 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +984 | -925 | +0.63 | 152 | ok/ok/ok | depends on today's stack |
| 6 | kal_sessrng_B200 | levels_round.retest {"M": 6, "tol": 0.5} | plain60/60 | +1186 | +925 | +0.76 | 646 | ok/AMBER/ok | depends on today's stack |
| 7 | vib_10000 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +1003 | -479 | +0.64 | 144 | ok/ok/ok | depends on today's stack |
| 8 | dol_750 | levels_trendline.break_native {"n": 3, "k": 0.25} | asym15u/30u | +1148 | -83 | +0.74 | 131 | AMBER/ok/ok | depends on today's stack |
| 9 | kal_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 10 | med_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |

## Honest limits

- Rankings are best-of-many on the last 6 months; the selection-corrected best-pick null (phase 2b) is not applied yet to any row.
- Screen numbers are naked triggers; the engine rows (NEW_BOOK_ENGINE*.md) show layers and account rules change results both ways.
