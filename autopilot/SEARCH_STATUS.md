# SEARCH_STATUS - full-search programme (plan 1722Z: no Globex deadline), W-GRIDOPS, refreshed 2026-11-18 21:35Z

Plain words. Data end 2026-11-15 (NQ). Research only, no spend. Phases: 1 finish the whole search -> 2 prove it is not luck (30 controls, selection-corrected null, trust) -> 3 gates/layers one by one then jointly -> 4 D8 spec. Every number below is a screen-level number unless it says engine.

## Phase 1 - progress (the grid is not split by session: one job = one bar row x one trigger module x one tag; every session reads the same results, so the percentages below are the same for NY AM, NY PM, London and Asia)

| item | done | todo | jobs/hour (last 60 min) | ETA at that rate |
|---|---|---|---|---|
| pass 1, all tags (real + random-entry nulls 1/2 + extra null draws) | 93777 result files | 116808 jobs | 3174 | 36.8 h |
| pass 2 (family cells, exits a2, top cells) | n/a | 25368 (a top cells 1253, a2 exit families 6276, c family cells 17839) | 589 | 43.1 h |

NOTE (18:40Z): the grid is partitioned over server 2 (rows 0-1 of 12), A (2-6) and B (7-11) by W-S3; finished results are merged into server 2 every ~5 min (lag <= 10 min), the todo and worker counts are summed over the three servers. A and B also see 172 bar rows that are complete on box 1 but not yet on server 2, so total todo is higher than the earlier single-server figure (about +50%).

Pass-1 results on disk by tag: real 46222, null draw 1 18626, null draw 2 18654, extra draws (3-25) 9284 files. Pass-1 results still waiting for their pass-2 upgrade: real 36422.

Machines (grid partitioned across servers): 207.188.7.103 load 106.07 workers 36; 109.94.96.39 load 263.74 workers 92; 206.223.224.21 load 248.24 workers 88; grid workers 216 (216 computing), engine workers 135; forward-path tables built (summed over servers) 482.

Since 17:23Z: pass-1 todo 80818 -> 116808 (+35990), pass-2 todo 25951 -> 25368 (-583). Pass-2 todo grows when pass 1 delivers cells that earn pass 2.

## R4 - selection-corrected null of the whole search: FIVE draws, calibration check of the ladder (orders 1932Z + 2042Z; prereg sha 125fd12566e72aa6 + amendment)

What it is: 5 random-entry draws (tags p1rand1..p1rand5; draws 6-20 cancelled 20:42Z, files kept) of the SAME pass-1 search (every bar row x trigger module, same flags own-stop + account mask); the share of cells that pass R0-R3 in a null draw versus in the real search is the false-discovery rate, and the best cell of the null search versus the best of the real search is the best-pick comparison. Draws 1-2 run inside the real loops, draws 3-5 in dedicated null loops (A rows 2-6: 24 workers, B rows 7-11: 24 workers, server 2 rows 0-1: 6 workers; nice 8-10, below the engine (nice 0) and R3 (nice 5)). The null cells are also pushed through the same ladder R0-R3 as a CALIBRATION CHECK of the false-discovery rate the ladder claims. Only accepted draws count (null audit: independent side draw, pooled mean pts/trade at plain 60/60 negative and above -6 in every session, identical share under 1%, coverage at least 80%).

| item | now |
|---|---|
| results/hour, REAL search (p1real files, pass 1 and 2 together) | 1164 |
| results/hour, NULL draws (p1rand1..20 files) | 2416 |
| null result files on disk, draws 1 / 2 | 18626 / 18654 (real: 46222) |
| null result files, draws 3-20 (all) | 8828 |
| draws complete (files incl. error stubs >= 99.5 percent of the real search) | 0 of 5 |
| draws accepted by the null audit and counted | see null_summary below |

Estimate: about 18 more full draws at the null share of the fleet (64 threads, ~25% of A + B) is roughly 60 hours (about 4,000 core-hours at the measured pass-1 rate; the order estimated ~6,300 core-hours); if that needs more than ~48 h the null share can be raised at the cost of the real search or machines added (Josh decides). False-discovery rate per session and the best-pick comparison appear here when W-SHORT has run the rule on the first accepted draws.

### False-discovery counts (W-SHORT, rule/null_summary.md: per accepted null draw per session, null cells passing vs the real search on the SAME coverage; ratio null/real = false-discovery ratio)

# NULL DRAWS vs REAL (same coverage) - cells passing R0 (bare) per session, W-SHORT 21:30Z

| tag | audit | Asia null / real (ratio) | London null / real (ratio) | NYAM null / real (ratio) | NYPM null / real (ratio) |
|---|---|---|---|---|---|

## Grid / engine split per host (order 1932Z item 3; caps owned by W-S3)

Since 20:15Z (order 2013Z item 5): priorities by nice level: engine slots nice 0 (lead sets: W-NYENG, W-LONENG, W-NT2), R3 jobs (W-SHORT) nice 5, null draws nice 8, real pass 1 / pass 2 nice 10. Leftover cores go to the R4 NULL draws FIRST, then pass 1: on A and B the real loops stay (A: pass 1 48 + pass 2 20; B: 40 + 24), the dedicated null loops have 32 workers each (nice 8), and a FILLER loop on the NULL tags (p1rand3..20, reverse order, nice 10, same own-stop/account flags) is resized every 5 minutes to 128 - real grid - engine busy - 4 (box-1 cron, filler_ctl.sh). Server 2 (64 threads): pass 1 22 + pass 2 8 + null 6 + engine + re-rank. The actual numbers are in the Machines table below.

## ETAs side by side after the 20:42Z change (static estimates computed 20:40Z; live rates are in the tables above)

R4 is now FIVE complete draws (draws 1-2 inside the real loops, draws 3-5 in the dedicated null loops, 25% of A and B); draws 6-20 cancelled, their result files kept. Remaining work: real cells 20.7k pass-1 jobs; null draws 1-2 99.9k; null draws 3-5 about 201k (67k per draw); pass 2 + exit families 26.3k heavy jobs. Rates: ~60 pass-1 and ~18 pass-2 jobs per worker-hour (nice 10).

| scenario (workers: real pass 1 / real pass 2 / null) | real pass 1 incl. null draws 1-2 | pass 2 + exits | R4 null draws 3-5 (5 draws complete) |
|---|---|---|---|
| 20:15Z split, 20 draws, engine idle (110 / 52 / 122) | ~18 h | ~28 h | ~166 h (draws 3-20) |
| 20:26Z split, 20 draws, null 50% (68+53 / 30 / 78) | ~17 h | ~49 h | ~258 h (draws 3-20) |
| NOW (restored: A p1 48 + p2 20 + null 24, B 40 + 24 + 24, Dallas 22 + 8 + 6; real-tag filler takes the leftover) | ~16 h | ~28 h | ~62 h at the 25% null share; ~30 h because the null filler takes ALL leftover cores once real pass 1 is finished (rule in filler_remote.py) |

Reading: phase 1 real ends in about 16 h (pass 1) and 28 h (pass 2 and exit families); the five-draw null ends in about 30-62 h; the engine holds ~28 workers per host (nice 0) and R3 (nice 5) outranks both; all estimates move with the engine load and the per-job rate, which varies by bar row.

## Machines (hourly; busy % is measured from /proc/stat against the REAL thread count of each machine)

| machine | real threads | busy % | load1 | grid workers (computing) | engine workers | re-rank/other workers | results/hour (this machine) |
|---|---|---|---|---|---|---|---|
| server 2 Dallas | 64 | 100.0 | 106.07 | 216 (216) | 67 | 23 | 3763 |
| A Frankfurt | 128 | 100.0 | 263.74 | 92 (92) | 28 | 0 | 2229 |
| B Singapore | 128 | 100.0 | 248.24 | 88 (88) | 27 | 0 | 3364 |
| box 1 London (lead, engine fillers) | 32 | 100 | 67.79 | 0 | see CORES.md | - | - |

Server 2 has 64 threads (SMT off in firmware, order 1830Z check), A and B 128 each, box 1 32. Total jobs/hour and the phase-1 ETA are in the table above (sum over servers; double counting warning applies until W-S3 merges results). Any machine under 85% busy for 3 readings with work pending gets a one-line explanation in MORNING.md.

## Blocked / cannot run (listed, not skipped silently)

Failed jobs leave an error stub that the loop retries after 4 hours (older stubs are retried automatically). Error files on disk: {'real': 355, 'p1real': 1711, 'p1rand1': 1545, 'p1rand2': 1512, 'p1rand3': 16, 'p1rand4': 16, 'p1rand5': 11}.

| module | failures (files) | why |
|---|---|---|
| trig_book_ofi | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_cancel | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_ice | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_queue | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_pslope | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_dwm | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_imb | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_micro | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_thin | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_wall | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_sweep | 307 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_block | 300 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_run | 300 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_unfinished | 299 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_stack | 299 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_sizemix | 299 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
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

# SURVIVOR_COUNTS - the LADDER (cheapest test first; W-SHORT, orders 1845Z + 1932Z), refreshed 2026-11-18 21:29Z

No top-N cap anywhere. A cell leaves only by FAILING a test. Counts are bare (R0) from server-2 results only and PROVISIONAL (grid partitioned over servers until W-S3 merges; data week 189). Rungs not yet run say "n/a (reason)", never zero.

THRESHOLDS (equal risk; R = points / stop, stop = clip(bracket multiple x row bar unit, 10, 120), plain 60/60 = 60): R0 L6M (26 w) > 0; >= 100 trades in L6M; L3M (13 w) > 0; persistence > 0.60 (2-week windows since 2023-10 positive); prior years 2023/24/25 R per week not more than 30% below the cell's own L6M R per week (RED = shown, not delivered; AMBER 15-30% passes, counted). R1 = the same thresholds on the OWN-STOP result (2 stops; 1.5 / 3 shown): cells passing R0 but failing R1 are KEPT and labelled "depends on today's stack". R2 trust (brute-force tape walk) + look-ahead (6 truncation cuts) + fills >= signal + 1 s. R3 30 same-bracket random-entry draws, screen level: PASS = beats >= 27 of 30 (count shown at 24 / 27 / 29). R4 selection-corrected null of the same search (5 full null draws, same own-stop flags; calibration check of R0-R3 on null cells). R5 exact engine, staged.

FAMILIES = connected components of the grid neighbour graph over passing cells (same module.variant on an adjacent bar size of the same bar type, adjacent parameter of the same variant, or the identical parameter with another bracket / side); the best member (highest min(L6M R/wk, weakest prior-year R/wk)) runs first, neighbours after; nothing is dropped.

FLEET: 352 threads (Dallas 64, Frankfurt 128, Singapore 128, box 1 32), 90% busy assumed = 317 screen cores; engine set-months/hour measured 763 (box 1 450 + Dallas 313; A and B have no engine runs yet), projected 2894 with A and B engine-ready (ENGINE_PLAN.md s.11). Unit costs measured on WP10 / XA3 (PHASE2_TOOLING_TEST.md): R2 ~12 CPU-s per cell; R3 ~0.31 core-h per (row, module) pair (30 draws; cells sharing a pair share the draws); R4 ~317 core-h per full null draw = ~1,585 core-h for the 5 draws now planned (order 2042Z; shared by all four sessions; W-GRIDOPS ETA: draws 1-2 inside the real loops ~16 h, draws 3-5 ~62 h at the 25 percent share or ~30 h once real pass 1 is done); R5 engine 0.05 core-h per set-month measured on box 1 / Dallas (Frankfurt measured ~0.30: 1,072 s per month, starved), R5 stage a = 12 set-months per family (L6M as ADD and as replacement of the weakest live book), prior years +72, 30 date-shift controls +180 set-months (7.8 core-h at 0.043). All "hours" below are UPPER BOUNDS (no cell has failed R1-R3 yet) and assume the whole fleet for screen rungs (R4: its 25 percent share of A + B) and the measured 763 set-months/h for the engine.

## Asia
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 4,386,735 | - | 4,383,743 | by first rule: R1 L6M<=0 2,375,203; R2 trades<100 960,658; R3 L3M<=0 345,052; R4 persistence<=0.60 622,303; RED prior year 80,527 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 2,992 (R0 passers) | 1,890 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 10.0 core-h for 2,992 cells | 0.0 h |
| R2 | trust + look-ahead | 2,992 (upper bound: all R1 cells) | 1,890 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 418 core-h for 1,349 (row, module) pairs | 1.3 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 2,992 (upper bound) | 1,890 | RUNNING: stage A (30 draws, same bracket, equal-risk) 695 of 1,890 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 207 / 67 / 13; reached stage B (200 draws) 26, C (1,000) 0, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 1,890 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 0 / 370 at q 5% / 10% / 20% | SET 1: 0, SET 2: 0 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 22,680 set-months = 1134 core-h | 29.7 h on the measured fleet (763/h), 7.8 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 1,890 families (upper bound) | 1,890 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+136,080 set-months) then 30 date-shift controls (+340,200 set-months = 17010 core-h) for the rows still alive | **178 h (> 48 h: Josh decides between more machines and waiting)** / **446 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 4,386,735; PASS **2,992 cells in 1,890 families** (non-reversal bars 2099, reversal 835 (provisional until the look-ahead gate), other 58; level / S-D modules 1061; AMBER prior year(s) 571). Distinct (row, module) files among the passers: 1,349.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_Asia.parquet; passing cells with family id / order / rank in family: pass_bare_Asia.csv.

## London
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 4,397,570 | - | 4,396,535 | by first rule: R1 L6M<=0 2,458,413; R2 trades<100 1,125,318; R3 L3M<=0 268,528; R4 persistence<=0.60 498,770; RED prior year 45,506 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 1,035 (R0 passers) | 808 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 3.5 core-h for 1,035 cells | 0.0 h |
| R2 | trust + look-ahead | 1,035 (upper bound: all R1 cells) | 808 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 198 core-h for 640 (row, module) pairs | 0.6 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 1,035 (upper bound) | 808 | not started for this session | n/a | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 9,696 set-months = 485 core-h | 12.7 h on the measured fleet (763/h), 3.4 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 808 families (upper bound) | 808 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+58,176 set-months) then 30 date-shift controls (+145,440 set-months = 7272 core-h) for the rows still alive | **76 h (> 48 h: Josh decides between more machines and waiting)** / **191 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 4,397,570; PASS **1,035 cells in 808 families** (non-reversal bars 746, reversal 233 (provisional until the look-ahead gate), other 56; level / S-D modules 349; AMBER prior year(s) 216). Distinct (row, module) files among the passers: 640.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_London.parquet; passing cells with family id / order / rank in family: pass_bare_London.csv.

## NYAM
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 4,828,997 | - | 4,819,493 | by first rule: R1 L6M<=0 2,839,937; R2 trades<100 755,347; R3 L3M<=0 367,009; R4 persistence<=0.60 788,984; RED prior year 68,216 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 9,504 (R0 passers) | 4,556 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 31.7 core-h for 9,504 cells | 0.1 h |
| R2 | trust + look-ahead | 9,504 (upper bound: all R1 cells) | 4,556 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 859 core-h for 2,770 (row, module) pairs | 2.7 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 9,504 (upper bound) | 4,556 | RUNNING: stage A (30 draws, same bracket, equal-risk) 779 of 4,556 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 104 / 32 / 7; reached stage B (200 draws) 55, C (1,000) 4, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 4,556 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 0 / 0 at q 5% / 10% / 20% | SET 1: 0, SET 2: 0 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 54,672 set-months = 2734 core-h | **72 h (> 48 h: Josh decides between more machines and waiting)** on the measured fleet (763/h), 18.9 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 4,556 families (upper bound) | 4,556 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+328,032 set-months) then 30 date-shift controls (+820,080 set-months = 41004 core-h) for the rows still alive | **430 h (> 48 h: Josh decides between more machines and waiting)** / **1075 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 4,828,997; PASS **9,504 cells in 4,556 families** (non-reversal bars 6560, reversal 2430 (provisional until the look-ahead gate), other 514; level / S-D modules 5157; AMBER prior year(s) 1565). Distinct (row, module) files among the passers: 2,770.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYAM.parquet; passing cells with family id / order / rank in family: pass_bare_NYAM.csv.

## NYPM
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 4,842,376 | - | 4,841,845 | by first rule: R1 L6M<=0 2,596,024; R2 trades<100 1,163,063; R3 L3M<=0 294,813; R4 persistence<=0.60 773,890; RED prior year 14,055 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 531 (R0 passers) | 396 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 1.8 core-h for 531 cells | 0.0 h |
| R2 | trust + look-ahead | 531 (upper bound: all R1 cells) | 396 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 107 core-h for 345 (row, module) pairs | 0.3 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 531 (upper bound) | 396 | not started for this session | n/a | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 4,752 set-months = 238 core-h | 6.2 h on the measured fleet (763/h), 1.6 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 396 families (upper bound) | 396 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+28,512 set-months) then 30 date-shift controls (+71,280 set-months = 3564 core-h) for the rows still alive | 37.4 h / **93 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 4,842,376; PASS **531 cells in 396 families** (non-reversal bars 401, reversal 86 (provisional until the look-ahead gate), other 44; level / S-D modules 112; AMBER prior year(s) 116). Distinct (row, module) files among the passers: 345.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYPM.parquet; passing cells with family id / order / rank in family: pass_bare_NYPM.csv.

## R3 PASS SETS side by side (Benjamini-Hochberg across ALL family-bests of the session; untested cells count as p = 1; the counts grow as draws complete)

SET 1 (strict, current rule) = inside BH on p_L6M (last 26 weeks, equal-risk sum of R). SET 2 (proposed, order 2057Z) = inside BH on p_ALL (whole history, first month to today, L6M included) AND still passing R0 / R1 unchanged (every cell here already passed R0; R1 own-stop pending). Cells in SET 2 with p_L6M > 0.20 are flagged "recent no better than random" (shown, not dropped). p = (1 + k) / (1 + n), k = random draws at least as good, n = draws; weakest prior-year p shown separately. Engine order: SET 1 first, then SET 2 members best p first, no cap; Josh decides which set is the pass rule. Engine cost per passer: R5a 12 set-months + prior years 72 + 30 date-shift controls 180 = 264 set-months = ~13 core-h = 0.35 h at the measured 763 set-months/h. Dated D8 spec estimate: W-PLAN, ENGINE_PLAN.md.

| session | family-bests | tested | SET 1 q5 / q10 / q20 | SET 1 expected false (q10) | SET 1 engine core-h / h | SET 2 q5 / q10 / q20 | SET 2 expected false (q10) | SET 2 engine core-h / h | SET 2 flagged recent no better than random (q10) | smallest p: L6M / ALL |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,890 | 695 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 0 / 370 | 0.0 | 0 / 0.0 h | 0 | 0.0323 / 0.0050 |
| London | - | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| NYAM | 4,556 | 779 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 | 0.0323 / 0.0020 |
| NYPM | - | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

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
| 2 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +634 | +74 | +0.41 | 386 | ok/ok/ok | L6M @1.5 stops +634 / @3 stops +598 |
| 3 | mrenko_20 | momentum_er.trend {"len": 10, "thr": 0.4} | plain60/60 | +603 | +34 | +0.39 | 428 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 4 | tick_500 | levels_vwap.break {"n": 3, "k": 0.0} | plain60/60 | +674 | +1041 | +0.43 | 417 | AMBER/AMBER/AMBER | L6M @1.5 stops +674 / @3 stops +550 |
| 5 | tick_500 | levels_vwap.break_native {"n": 3, "k": 0.0} | plain60/60 | +674 | +1041 | +0.43 | 417 | ok/AMBER/AMBER | L6M @1.5 stops +674 / @3 stops +550 |
| 6 | tick_300 | trend_libstack.ema_stack {"set": "10-20-50"} | plain60/60 | +664 | +550 | +0.43 | 343 | AMBER/AMBER/AMBER | L6M @1.5 stops +664 / @3 stops <=0 or <100 tr |
| 7 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +673 | +70 | +0.43 | 555 | AMBER/ok/ok | L6M @1.5 stops +673 / @3 stops <=0 or <100 tr |
| 8 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +468 | +319 | +0.30 | 404 | ok/ok/ok | L6M @1.5 stops +468 / @3 stops <=0 or <100 tr |
| 9 | rng_20 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +535 | +899 | +0.34 | 500 | ok/ok/ok | L6M @1.5 stops +535 / @3 stops +266 |
| 10 | time_s_20 | bands_regchan.fade_linreg {"n": 10, "k": 1.5} | asym10u/20u | +325 | +690 | +0.29 | 372 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 | +616 | +1066 | +0.39 | 777 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +605 | +1164 | +0.39 | 562 | ok/ok/ok | strong on (b) too |
| 3 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +632 | +93 | +0.40 | 806 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 4 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +601 | +126 | +0.38 | 444 | ok/ok/ok | strong on (b) too |
| 5 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +502 | +600 | +0.32 | 483 | ok/ok/ok | strong on (b) too |
| 6 | vsess_30 | bands_envelope.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | strong on (b) too |
| 7 | rng_20 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +476 | +913 | +0.30 | 653 | ok/ok/ok | strong on (b) too |
| 8 | dib_1200 | levels_vwap.break_native {"n": 2, "k": 0.25} | plain60/60 | +458 | +694 | +0.29 | 545 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | renko_10 | trend_libstack.ema_stack {"set": "13-34-89"} | plain60/60 | +455 | +913 | +0.29 | 505 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | time_m_10 | bands_vwap.break_native {"clk": 3, "k": 1.0} | plain60/60 | +481 | +1341 | +0.31 | 394 | ok/ok/ok | bare only (not positive on own-stop) |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +626 | +1202 | +0.40 | 556 | ok/ok/ok | also positive on (b) |
| 2 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +622 | +97 | +0.40 | 799 | ok/ok/ok | depends on today's stack |
| 3 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +693 | +194 | +0.44 | 440 | ok/AMBER/AMBER | also positive on (b) |
| 4 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +525 | +600 | +0.34 | 482 | ok/ok/ok | also positive on (b) |
| 5 | vsess_30 | bands_envelope.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | also positive on (b) |
| 6 | tick_500 | levels_vwap.break {"n": 3, "k": 0.0} | plain60/60 | +474 | +1566 | +0.30 | 533 | ok/ok/ok | also positive on (b) |
| 7 | tick_500 | levels_vwap.break_native {"n": 3, "k": 0.0} | plain60/60 | +474 | +1566 | +0.30 | 533 | ok/ok/ok | also positive on (b) |
| 8 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +467 | +418 | +0.30 | 706 | ok/ok/ok | also positive on (b) |
| 9 | renko_10 | trend_libstack.ema_stack {"set": "13-34-89"} | plain60/60 | +652 | +1013 | +0.42 | 500 | AMBER/AMBER/ok | depends on today's stack |
| 10 | time_m_10 | bands_vwap.break_native {"clk": 3, "k": 1.0} | plain60/60 | +481 | +1341 | +0.31 | 394 | ok/ok/ok | depends on today's stack |

## Top 10 London

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +687 | +276 | +0.44 | 269 | ok/ok/ok | L6M @1.5 stops +687 / @3 stops +877 |
| 2 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +898 | -1732 | +0.58 | 229 | AMBER/ok/AMBER | L6M @1.5 stops +898 / @3 stops <=0 or <100 tr |
| 3 | cusum_28 | trend_macd.hist_turn_native {"len": 26, "width": 0.03} | plain60/60 | +744 | +972 | +0.48 | 364 | ok/ok/ok | L6M @1.5 stops +370 / @3 stops +431 |
| 4 | entropy_B200 | book_micro.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +701 | +653 | +0.45 | 238 | ok/ok/ok | L6M @1.5 stops +701 / @3 stops <=0 or <100 tr |
| 5 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 6 | kal_bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 7 | bmsg_B320 | manual_macd.sigcross_native {"f": 20, "s": 45, "g": 15} | sym15u | +784 | +400 | +0.50 | 241 | AMBER/ok/ok | L6M @1.5 stops +784 / @3 stops <=0 or <100 tr |
| 8 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +618 | +173 | +0.40 | 339 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 9 | dltor_B320 | trend_ma_hma.price {"len": 9, "width": 0.0} | sym15u | +838 | +191 | +0.54 | 297 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 10 | ha_rngor_B200 | trend_ma_hma.cross {"len": 34, "width": 4, "hyst": 0.0} | sym15u | +732 | -494 | +0.47 | 246 | ok/ok/AMBER | L6M @1.5 stops +732 / @3 stops <=0 or <100 tr |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +702 | +131 | +0.45 | 287 | ok/ok/ok | strong on (b) too |
| 2 | entropy_B200 | book_micro.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +852 | +899 | +0.55 | 255 | ok/AMBER/AMBER | strong on (b) too |
| 3 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +964 | -521 | +0.62 | 225 | ok/AMBER/AMBER | bare only (not positive on own-stop) |
| 4 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +666 | -175 | +0.43 | 140 | ok/ok/ok | strong on (b) too |
| 5 | ha_micro_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +802 | +520 | +0.51 | 260 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 6 | ha_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +743 | +460 | +0.48 | 257 | ok/ok/ok | bare only (not positive on own-stop) |
| 7 | kal_bmsg_B200 | trend_ma_hma.cross {"len": 21, "width": 2, "hyst": 0.0} | sym15u | +914 | +1528 | +0.59 | 260 | AMBER/AMBER/AMBER | bare only (not positive on own-stop) |
| 8 | ha_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +623 | +1129 | +0.40 | 502 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | cusum_14 | xmarket_fast.follow_ES {"w": 30, "thr": 1.0} | plain60/60 | +622 | +581 | +0.40 | 827 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | ha_micro_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +621 | +1188 | +0.40 | 506 | ok/ok/ok | bare only (not positive on own-stop) |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +1175 | +593 | +0.75 | 236 | ok/AMBER/AMBER | also positive on (b) |
| 2 | ha_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 3 | kal_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 4 | med_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 5 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +677 | -374 | +0.43 | 189 | ok/ok/ok | depends on today's stack |
| 6 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +674 | -435 | +0.43 | 182 | ok/ok/ok | depends on today's stack |
| 7 | kal_entropy_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +670 | -420 | +0.43 | 193 | ok/ok/ok | depends on today's stack |
| 8 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +647 | +578 | +0.41 | 563 | ok/ok/ok | also positive on (b) |
| 9 | tib_400 | barnative_delta.run {"n": 3, "thr": 0.0} | plain60/60 | +602 | +380 | +0.39 | 630 | ok/ok/ok | depends on today's stack |
| 10 | entropy_B500 | book_ice.follow {"thr": 1} | sym15u | +686 | +153 | +0.44 | 210 | ok/AMBER/ok | depends on today's stack |

## Top 10 NY AM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u | +2161 | +1183 | +1.39 | 258 | AMBER/ok/ok | L6M @1.5 stops +2298 / @3 stops <=0 or <100 tr |
| 2 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +2026 | +333 | +1.30 | 496 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +579 |
| 3 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1389 | +271 | +0.89 | 318 | ok/ok/ok | L6M @1.5 stops +1501 / @3 stops <=0 or <100 tr |
| 4 | trend_20 | levels_vwap.reject {"tol": 1.0, "conf": "body"} | sym15u | +1375 | -248 | +0.88 | 260 | ok/ok/ok | L6M @1.5 stops +763 / @3 stops +1879 |
| 5 | kal_qmid_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1348 | +276 | +0.86 | 317 | ok/ok/ok | L6M @1.5 stops +1582 / @3 stops <=0 or <100 tr |
| 6 | dltor_B080 | book_cancel.canc_follow {"L": 200, "z": 2.0} | sym15u | +1528 | +2013 | +0.98 | 322 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 7 | dltor_B130 | bands_atrchan.break_ema {"n": 10, "atr": 14, "k": 1.5} | sym15u | +1533 | +257 | +0.98 | 388 | ok/AMBER/ok | L6M @1.5 stops +625 / @3 stops +1501 |
| 8 | ha_micro_B200 | barnative_run.cont {"n": 4} | sym15u | +1226 | +241 | +0.79 | 343 | ok/ok/ok | L6M @1.5 stops +1202 / @3 stops +418 |
| 9 | entropy_B200 | levels_swsr5.break {"n": 3, "k": 0.5} | sym15u | +1217 | -1804 | +0.78 | 346 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +1325 |
| 10 | ha_entropy_B200 | levels_round.retest {"M": 10, "tol": 0.5} | sym15u | +1329 | +706 | +0.85 | 364 | ok/ok/ok | L6M @1.5 stops +359 / @3 stops <=0 or <100 tr |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1967 | +206 | +1.26 | 379 | AMBER/ok/ok | strong on (b) too |
| 2 | kal_qmid_B080 | bands_regchan.break_stderr_native {"clk": 20, "k": 2.5} | sym15u | +1956 | +1097 | +1.25 | 316 | AMBER/AMBER/ok | strong on (b) too |
| 3 | trend_20 | levels_vwap.reject {"tol": 1.0, "conf": "body"} | sym15u | +1707 | -264 | +1.09 | 340 | ok/AMBER/ok | strong on (b) too |
| 4 | ha_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |
| 5 | kal_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |
| 6 | bmsgq_B050 | book_cancel.canc_follow {"L": 50, "z": 1.0} | sym15u | +1657 | +307 | +1.06 | 387 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 7 | frenko_40 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 | +1751 | +147 | +1.12 | 582 | AMBER/AMBER/ok | strong on (b) too |
| 8 | kal_qmid_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1641 | +212 | +1.05 | 379 | AMBER/ok/ok | strong on (b) too |
| 9 | renko_10 | momentum_mvote.v3of5_native {"scale": 0.25, "thr": 0.25} | plain60/60 | +1302 | +386 | +0.83 | 1427 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | bmsg_B200 | bands_bollinger.walk {"n": 30, "k": 2.0, "N": 3} | sym15u | +1380 | +1784 | +0.88 | 303 | ok/ok/ok | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 2 | ha_bmsgq_B200 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1885 | -312 | +1.21 | 318 | ok/AMBER/ok | depends on today's stack |
| 3 | med_volor_B080 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u | +1448 | -307 | +0.93 | 257 | ok/ok/ok | depends on today's stack |
| 4 | ha_sessrng_B200 | bands_keltner.walk {"ema": 30, "atr": 10, "mult": 1.5, "N": 3} | sym15u | +1356 | +918 | +0.87 | 235 | ok/ok/ok | depends on today's stack |
| 5 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1835 | +1003 | +1.18 | 323 | AMBER/AMBER/ok | depends on today's stack |
| 6 | dchg_40 | manual_macd.sigcross_native {"f": 5, "s": 13, "g": 4} | plain60/60 | +1357 | -639 | +0.87 | 604 | ok/ok/ok | depends on today's stack |
| 7 | trend_20 | levels_fibr_dev.retest {"M": 3, "tol": 0.0} | sym15u | +1354 | +338 | +0.87 | 234 | ok/ok/ok | depends on today's stack |
| 8 | trend_20 | levels_fibr_dev.retest_native {"M": 3, "tol": 0.0} | sym15u | +1354 | +338 | +0.87 | 234 | ok/ok/ok | depends on today's stack |
| 9 | med_volor_B080 | bands_bollinger.break_native {"clk": 40, "k": 2.5} | sym15u | +1703 | +412 | +1.09 | 152 | AMBER/AMBER/ok | depends on today's stack |
| 10 | ha_sessrng_B080 | bands_keltner.break {"ema": 10, "atr": 10, "mult": 1.5} | sym15u | +1396 | +1013 | +0.89 | 138 | ok/ok/ok | depends on today's stack |

## Top 10 NY PM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | ha_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 2 | kal_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 3 | kal_qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 4 | tm1800 | xmarket_ym.follow {"w": 5, "thr": 1.0} | plain60/60 | +1219 | +433 | +0.78 | 115 | ok/AMBER/ok | L6M @1.5 stops +925 / @3 stops +1181 |
| 5 | time_s_20 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} | plain60/60 | +885 | +115 | +0.57 | 255 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +1152 |
| 6 | tick_2000 | levels_session_hl.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +910 | +444 | +0.58 | 161 | ok/ok/ok | L6M @1.5 stops +886 / @3 stops +293 |
| 7 | ha_sessrng_B080 | xmarket_ym.follow {"w": 1, "thr": 1.0} | sym15u | +824 | +300 | +0.53 | 200 | ok/ok/ok | L6M @1.5 stops +730 / @3 stops +274 |
| 8 | kal_sessrng_B080 | xmarket_ym.follow {"w": 1, "thr": 1.0} | sym15u | +824 | +300 | +0.53 | 200 | ok/ok/ok | L6M @1.5 stops +730 / @3 stops +274 |
| 9 | dlt_70 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | sym15u | +2155 | +808 | +0.69 | 177 | AMBER/AMBER/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 10 | drb_1200 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +972 | +77 | +0.62 | 288 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |

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
| 8 | ha_sessrng_B080 | xmarket_ym.follow {"w": 1, "thr": 1.0} | sym15u | +878 | +353 | +0.56 | 297 | ok/ok/ok | strong on (b) too |
| 9 | ha_volor_B080 | manual_macd.histturn {"f": 5, "s": 13, "g": 5} | plain60/60 | +913 | +1136 | +0.59 | 983 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | swing_pct_8 | momentum_willr.break_native {"len": 7, "lvl": 10} | plain60/60 | +1060 | -783 | +0.68 | 827 | ok/ok/AMBER | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | kal_rngor_B080 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1024 | +671 | +0.66 | 210 | ok/ok/ok | depends on today's stack |
| 2 | kal_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 3 | med_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 4 | mom_14 | bands_atrchan.break_ext_native {"clk": 5, "k": 1.5} | plain60/60 | +1008 | +1874 | +0.65 | 605 | ok/ok/ok | also positive on (b) |
| 5 | bmsg_B130 | levels_round.reject {"tol": 0.0, "conf": "close"} | sym15u | +1172 | +549 | +0.75 | 196 | ok/AMBER/ok | depends on today's stack |
| 6 | bmsg_B130 | levels_round.reject_native {"tol": 0.0, "conf": "close"} | sym15u | +1172 | +549 | +0.75 | 196 | ok/AMBER/ok | depends on today's stack |
| 7 | renko_10 | tape_delta.cvd_fade {"N": 5, "L": 100, "z": 1.0} | plain60/60 | +1219 | +206 | +0.78 | 527 | AMBER/AMBER/ok | depends on today's stack |
| 8 | dltor_B320 | levels_trendline.break_native {"n": 3, "k": 0.5} | sym15u | +842 | -539 | +0.54 | 142 | ok/ok/ok | depends on today's stack |
| 9 | rng_28 | xmarket_commod.with_GC {"w": 1, "thr": 1.0} | plain60/60 | +1101 | +1215 | +0.71 | 445 | AMBER/AMBER/ok | depends on today's stack |
| 10 | dlt_250 | xmarket_commod.with_GC {"w": 1, "thr": 1.0} | plain60/60 | +1074 | +467 | +0.69 | 301 | AMBER/AMBER/ok | depends on today's stack |

## Honest limits

- Rankings are best-of-many on the last 6 months; the selection-corrected best-pick null (phase 2b) is not applied yet to any row.
- Screen numbers are naked triggers; the engine rows (NEW_BOOK_ENGINE*.md) show layers and account rules change results both ways.
