# SURVIVOR_COUNTS - the LADDER (cheapest test first; W-SHORT, orders 1845Z + 1932Z), refreshed 2026-11-22 11:42Z

No top-N cap anywhere. A cell leaves only by FAILING a test. Counts are bare (R0) from server-2 results only and PROVISIONAL (grid partitioned over servers until W-S3 merges; data week 189). Rungs not yet run say "n/a (reason)", never zero.

THRESHOLDS (equal risk; R = points / stop, stop = clip(bracket multiple x row bar unit, 10, 120), plain 60/60 = 60): R0 L6M (26 w) > 0; >= 100 trades in L6M; L3M (13 w) > 0; persistence > 0.60 (2-week windows since 2023-10 positive); prior years 2023/24/25 R per week not more than 30% below the cell's own L6M R per week (RED = shown, not delivered; AMBER 15-30% passes, counted). R1 = the same thresholds on the OWN-STOP result (2 stops; 1.5 / 3 shown): cells passing R0 but failing R1 are KEPT and labelled "depends on today's stack". R2 trust (brute-force tape walk) + look-ahead (6 truncation cuts) + fills >= signal + 1 s. R3 30 same-bracket random-entry draws, screen level: PASS = beats >= 27 of 30 (count shown at 24 / 27 / 29). R4 selection-corrected null of the same search (5 full null draws, same own-stop flags; calibration check of R0-R3 on null cells). R5 exact engine, staged.

FAMILIES = connected components of the grid neighbour graph over passing cells (same module.variant on an adjacent bar size of the same bar type, adjacent parameter of the same variant, or the identical parameter with another bracket / side); the best member (highest min(L6M R/wk, weakest prior-year R/wk)) runs first, neighbours after; nothing is dropped.

FLEET: 352 threads (Dallas 64, Frankfurt 128, Singapore 128, box 1 32), 90% busy assumed = 317 screen cores; engine set-months/hour measured 763 (box 1 450 + Dallas 313; A and B have no engine runs yet), projected 2894 with A and B engine-ready (ENGINE_PLAN.md s.11). Unit costs measured on WP10 / XA3 (PHASE2_TOOLING_TEST.md): R2 ~12 CPU-s per cell; R3 ~0.31 core-h per (row, module) pair (30 draws; cells sharing a pair share the draws); R4 ~317 core-h per full null draw = ~1,585 core-h for the 5 draws now planned (order 2042Z; shared by all four sessions; W-GRIDOPS ETA: draws 1-2 inside the real loops ~16 h, draws 3-5 ~62 h at the 25 percent share or ~30 h once real pass 1 is done); R5 engine 0.05 core-h per set-month measured on box 1 / Dallas (Frankfurt measured ~0.30: 1,072 s per month, starved), R5 stage a = 12 set-months per family (L6M as ADD and as replacement of the weakest live book), prior years +72, 30 date-shift controls +180 set-months (7.8 core-h at 0.043). All "hours" below are UPPER BOUNDS (no cell has failed R1-R3 yet) and assume the whole fleet for screen rungs (R4: its 25 percent share of A + B) and the measured 763 set-months/h for the engine.

## UNVERIFIED (stale level result) - notice, refreshed 11:40Z UTC

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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 6,487 (upper bound) | 3,847 | RUNNING: stage A (30 draws, same bracket, equal-risk) 3,936 of 3,847 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 922 / 294 / 60; reached stage B (200 draws) 1744, C (1,000) 501, D (10,000) 9 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 3,847 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 2514 / 3316 / 3752 at q 5% / 10% / 20% | SET 1: 0, SET 2: 3316 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 3,158 (upper bound) | 2,237 | RUNNING: stage A (30 draws, same bracket, equal-risk) 806 of 2,237 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 48 / 8 / 2; reached stage B (200 draws) 615, C (1,000) 119, D (10,000) 3 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 2,237 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 126 / 386 at q 5% / 10% / 20% | SET 1: 0, SET 2: 126 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 24,702 (upper bound) | 11,460 | RUNNING: stage A (30 draws, same bracket, equal-risk) 11,767 of 11,460 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 1261 / 311 / 72; reached stage B (200 draws) 4348, C (1,000) 1610, D (10,000) 34 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 11,460 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 7507 / 9550 / 10911 at q 5% / 10% / 20% | SET 1: 0, SET 2: 9550 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 1,638 (upper bound) | 1,168 | RUNNING: stage A (30 draws, same bracket, equal-risk) 393 of 1,168 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 92 / 65 / 32; reached stage B (200 draws) 378, C (1,000) 91, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 1,168 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 149 / 322 / 370 at q 5% / 10% / 20% | SET 1: 0, SET 2: 322 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 14,016 set-months = 701 core-h | 18.4 h on the measured fleet (763/h), 4.8 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 1,168 families (upper bound) | 1,168 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+84,096 set-months) then 30 date-shift controls (+210,240 set-months = 10512 core-h) for the rows still alive | **110 h (> 48 h: Josh decides between more machines and waiting)** / **276 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 11,753,727; PASS **1,638 cells in 1,168 families** (non-reversal bars 1059, reversal 214 (provisional until the look-ahead gate), other 365; level / S-D modules 562; AMBER prior year(s) 346). Distinct (row, module) files among the passers: 979.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYPM.parquet; passing cells with family id / order / rank in family: pass_bare_NYPM.csv.

## R3 PASS SETS side by side (Benjamini-Hochberg across ALL family-bests of the session; untested cells count as p = 1; the counts grow as draws complete)

SET 1 (strict, current rule) = inside BH on p_L6M (last 26 weeks, equal-risk sum of R). SET 2 (proposed, order 2057Z) = inside BH on p_ALL (whole history, first month to today, L6M included) AND still passing R0 / R1 unchanged (every cell here already passed R0; R1 own-stop pending). Cells in SET 2 with p_L6M > 0.20 are flagged "recent no better than random" (shown, not dropped). p = (1 + k) / (1 + n), k = random draws at least as good, n = draws; weakest prior-year p shown separately. Engine order: SET 1 first, then SET 2 members best p first, no cap; Josh decides which set is the pass rule. Engine cost per passer: R5a 12 set-months + prior years 72 + 30 date-shift controls 180 = 264 set-months = ~13 core-h = 0.35 h at the measured 763 set-months/h. Dated D8 spec estimate: W-PLAN, ENGINE_PLAN.md.

| session | family-bests | tested | SET 1 q5 / q10 / q20 | SET 1 expected false (q10) | SET 1 engine core-h / h | SET 2 q5 / q10 / q20 | SET 2 expected false (q10) | SET 2 engine core-h / h | SET 2 flagged recent no better than random (q10) | smallest p: L6M / ALL |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,890 | 3,936 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 2514 / 3316 / 3752 | 331.6 | 43771 / 1147.3 h | 2697 | 0.0212 / 0.0001 |
| London | 808 | 806 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 126 / 386 | 12.6 | 1663 / 43.6 h | 114 | 0.0420 / 0.0002 |
| NYAM | 4,556 | 11,767 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 7507 / 9550 / 10911 | 955.0 | 126060 / 3304.3 h | 8812 | 0.0250 / 0.0001 |
| NYPM | 396 | 393 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 149 / 322 / 370 | 32.2 | 4250 / 111.4 h | 245 | 0.0220 / 0.0001 |

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

