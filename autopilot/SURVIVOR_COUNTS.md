# SURVIVOR_COUNTS - the LADDER (cheapest test first; W-SHORT, orders 1845Z + 1932Z), refreshed 2026-11-19 03:40Z

No top-N cap anywhere. A cell leaves only by FAILING a test. Counts are bare (R0) from server-2 results only and PROVISIONAL (grid partitioned over servers until W-S3 merges; data week 189). Rungs not yet run say "n/a (reason)", never zero.

THRESHOLDS (equal risk; R = points / stop, stop = clip(bracket multiple x row bar unit, 10, 120), plain 60/60 = 60): R0 L6M (26 w) > 0; >= 100 trades in L6M; L3M (13 w) > 0; persistence > 0.60 (2-week windows since 2023-10 positive); prior years 2023/24/25 R per week not more than 30% below the cell's own L6M R per week (RED = shown, not delivered; AMBER 15-30% passes, counted). R1 = the same thresholds on the OWN-STOP result (2 stops; 1.5 / 3 shown): cells passing R0 but failing R1 are KEPT and labelled "depends on today's stack". R2 trust (brute-force tape walk) + look-ahead (6 truncation cuts) + fills >= signal + 1 s. R3 30 same-bracket random-entry draws, screen level: PASS = beats >= 27 of 30 (count shown at 24 / 27 / 29). R4 selection-corrected null of the same search (5 full null draws, same own-stop flags; calibration check of R0-R3 on null cells). R5 exact engine, staged.

FAMILIES = connected components of the grid neighbour graph over passing cells (same module.variant on an adjacent bar size of the same bar type, adjacent parameter of the same variant, or the identical parameter with another bracket / side); the best member (highest min(L6M R/wk, weakest prior-year R/wk)) runs first, neighbours after; nothing is dropped.

FLEET: 352 threads (Dallas 64, Frankfurt 128, Singapore 128, box 1 32), 90% busy assumed = 317 screen cores; engine set-months/hour measured 763 (box 1 450 + Dallas 313; A and B have no engine runs yet), projected 2894 with A and B engine-ready (ENGINE_PLAN.md s.11). Unit costs measured on WP10 / XA3 (PHASE2_TOOLING_TEST.md): R2 ~12 CPU-s per cell; R3 ~0.31 core-h per (row, module) pair (30 draws; cells sharing a pair share the draws); R4 ~317 core-h per full null draw = ~1,585 core-h for the 5 draws now planned (order 2042Z; shared by all four sessions; W-GRIDOPS ETA: draws 1-2 inside the real loops ~16 h, draws 3-5 ~62 h at the 25 percent share or ~30 h once real pass 1 is done); R5 engine 0.05 core-h per set-month measured on box 1 / Dallas (Frankfurt measured ~0.30: 1,072 s per month, starved), R5 stage a = 12 set-months per family (L6M as ADD and as replacement of the weakest live book), prior years +72, 30 date-shift controls +180 set-months (7.8 core-h at 0.043). All "hours" below are UPPER BOUNDS (no cell has failed R1-R3 yet) and assume the whole fleet for screen rungs (R4: its 25 percent share of A + B) and the measured 763 set-months/h for the engine.

## UNVERIFIED (stale level result) - notice, refreshed 03:40Z UTC

trig_levels_* grid results written BEFORE 2026-11-18 06:00Z predate the level-module fixes (13 of 17 level modules differ on a fresh re-run, W-GRIDOPS 0145Z); they are being re-run (Dallas from 01:33Z, Frankfurt / Singapore ~02:30Z, null draws 1-2 last). Until the result stamp (code hash on every result file) exists, every row below that touches a level module and a pre-06:00Z result is **UNVERIFIED (stale level result)**; non-level modules are not known to be affected (all-module check pending, order 0143Z). Stage-A p-values of R3 are computed with the CURRENT module code (fresh), but the cell SELECTION (R0) used the stale grid result; cells whose fresh L6M differs from the grid L6M by > 1 point are VOID (excluded).

| session | R0 passing cells | of which stale level cells | family-bests | stale family-bests | real-on-null-coverage tested (stage A) | stale level cells there | null draw tested (stage A) | stale level cells there |
|---|---|---|---|---|---|---|---|---|
| Asia | 4,541 | 211 (4.6%) | 2,902 | 116 | 900 | 36 (4%) | 364 | 68 (19%) |
| London | 2,177 | 51 (2.3%) | 1,672 | 42 | 333 | 17 (5%) | 390 | 52 (13%) |
| NYAM | 15,834 | 924 (5.8%) | 8,510 | 483 | 1814 | 167 (9%) | 399 | 73 (18%) |
| NYPM | 1,152 | 17 (1.5%) | 861 | 16 | 191 | 5 (3%) | 230 | 32 (14%) |

Reading: the stale share is NOT symmetric in the calibration: among tested family-bests 3-11% of the real-search cells but 17-26% of the null-draw cells rest on pre-06:00Z level files (the null draws were run early with the old level code), so the 01:16Z FDR table can be biased by the stale null side; it is redone after the forced re-run of draws 1-2 (last in the queue).


## Asia
| rung | what | cells in | families in | out (failed) | cells out | core-h spent | core-h the NEXT rung needs | hours on the current fleet (next rung) |
|---|---|---|---|---|---|---|---|---|
| R0 | bare rule | 6,461,292 | - | 6,456,751 | by first rule: R1 L6M<=0 3,461,640; R2 trades<100 1,395,903; R3 L3M<=0 526,793; R4 persistence<=0.60 945,197; RED prior year 127,218 | ~0.1 (scoring) | R1: ~0 (re-score; own-stop arrays: see below) | - |
| R1 | OWN-STOP (same thresholds) | 4,541 (R0 passers) | 2,902 | n/a (full-grid A_os arrays not built: only ~1,700 pairs carry them; the grid is re-running the rest, W-GRIDOPS) | n/a | 0 | R2: 15.1 core-h for 4,541 cells | 0.0 h |
| R2 | trust + look-ahead | 4,541 (upper bound: all R1 cells) | 2,902 | not run (sample audit: 47 of 48 shortlisted cells pass, 1 look-ahead fail; XA3 and WP10 pass) | n/a | ~0 | R3: 629 core-h for 2,030 (row, module) pairs | 2.0 h |
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 4,541 (upper bound) | 2,902 | RUNNING: stage A (30 draws, same bracket, equal-risk) 1,885 of 2,902 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 521 / 182 / 31; reached stage B (200 draws) 444, C (1,000) 34, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 2,902 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 1232 / 1621 at q 5% / 10% / 20% | SET 1: 0, SET 2: 1232 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 2,177 (upper bound) | 1,672 | RUNNING: stage A (30 draws, same bracket, equal-risk) 806 of 1,672 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 49 / 9 / 2; reached stage B (200 draws) 187, C (1,000) 10, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 1,672 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 0 / 314 at q 5% / 10% / 20% | SET 1: 0, SET 2: 0 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 15,834 (upper bound) | 8,510 | RUNNING: stage A (30 draws, same bracket, equal-risk) 4,542 of 8,510 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 571 / 164 / 44; reached stage B (200 draws) 1241, C (1,000) 104, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 8,510 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 3474 / 4220 at q 5% / 10% / 20% | SET 1: 0, SET 2: 3474 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 1,152 (upper bound) | 861 | RUNNING: stage A (30 draws, same bracket, equal-risk) 393 of 861 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 92 / 65 / 32; reached stage B (200 draws) 193, C (1,000) 0, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 861 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 296 / 369 at q 5% / 10% / 20% | SET 1: 0, SET 2: 296 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 10,332 set-months = 517 core-h | 13.5 h on the measured fleet (763/h), 3.6 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 861 families (upper bound) | 861 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+61,992 set-months) then 30 date-shift controls (+154,980 set-months = 7749 core-h) for the rows still alive | **81 h (> 48 h: Josh decides between more machines and waiting)** / **203 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 8,043,245; PASS **1,152 cells in 861 families** (non-reversal bars 743, reversal 118 (provisional until the look-ahead gate), other 291; level / S-D modules 271; AMBER prior year(s) 243). Distinct (row, module) files among the passers: 740.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYPM.parquet; passing cells with family id / order / rank in family: pass_bare_NYPM.csv.

## R3 PASS SETS side by side (Benjamini-Hochberg across ALL family-bests of the session; untested cells count as p = 1; the counts grow as draws complete)

SET 1 (strict, current rule) = inside BH on p_L6M (last 26 weeks, equal-risk sum of R). SET 2 (proposed, order 2057Z) = inside BH on p_ALL (whole history, first month to today, L6M included) AND still passing R0 / R1 unchanged (every cell here already passed R0; R1 own-stop pending). Cells in SET 2 with p_L6M > 0.20 are flagged "recent no better than random" (shown, not dropped). p = (1 + k) / (1 + n), k = random draws at least as good, n = draws; weakest prior-year p shown separately. Engine order: SET 1 first, then SET 2 members best p first, no cap; Josh decides which set is the pass rule. Engine cost per passer: R5a 12 set-months + prior years 72 + 30 date-shift controls 180 = 264 set-months = ~13 core-h = 0.35 h at the measured 763 set-months/h. Dated D8 spec estimate: W-PLAN, ENGINE_PLAN.md.

| session | family-bests | tested | SET 1 q5 / q10 / q20 | SET 1 expected false (q10) | SET 1 engine core-h / h | SET 2 q5 / q10 / q20 | SET 2 expected false (q10) | SET 2 engine core-h / h | SET 2 flagged recent no better than random (q10) | smallest p: L6M / ALL |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,890 | 1,885 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 1232 / 1621 | 123.2 | 16262 / 426.3 h | 916 | 0.0249 / 0.0003 |
| London | 808 | 806 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 0 / 314 | 0.0 | 0 / 0.0 h | 0 | 0.0645 / 0.0050 |
| NYAM | 4,556 | 4,542 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 3474 / 4220 | 347.4 | 45857 / 1202.0 h | 3097 | 0.0299 / 0.0002 |
| NYPM | 396 | 393 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 296 / 369 | 29.6 | 3907 / 102.4 h | 227 | 0.0199 / 0.0050 |

## CALIBRATION: measured false-discovery rate from the whole-search null (order 2218Z, partial draw 1)

Label: PARTIAL / coarse (draw p1rand1 only, files that exist so far; the real search is restricted to the same (row, module) files and the pass-1 coverage; one family definition: same file + parameter). FDR(b) = expected null family-bests / real family-bests at the threshold "beats >= b of 30 draws" (p <= (31 - b + 1) / 31). Stage A only (30 draws): the finest p reachable is 0.032, so FDR <= 10% can only be read where it shows below.

| session | R0 pass cells null / real (ratio) | R0 families null / real | tested null / real (sampled family-bests) | stat | b = 24 | 27 | 29 | 30 |
|---|---|---|---|---|---|---|---|---|
| Asia | 380 / 963 (0.39) | 372 / 904 | 364 / 900 | p_L6M (null / real families at threshold = FDR) | 88 / 281 = 31% | 28 / 93 = 30% | 14 / 13 = 110% | 7 / 2 = 356% |
|  |  /  (0.00) |  /  | 364 / 900 | p_ALL (null / real families at threshold = FDR) | 227 / 840 = 27% | 169 / 744 = 23% | 112 / 604 = 19% | 66 / 428 = 16% |
| London | 466 / 347 (1.34) | 457 / 335 | 390 / 333 | p_L6M (null / real families at threshold = FDR) | 45 / 18 = 246% | 14 / 3 = 466% | 4 / 2 = 175% | 4 / 0 = n/a |
|  |  /  (0.00) |  /  | 390 / 333 | p_ALL (null / real families at threshold = FDR) | 318 / 261 = 122% | 247 / 197 = 125% | 168 / 121 = 139% | 100 / 91 = 110% |
| NYAM | 763 / 1,915 (0.40) | 730 / 1,821 | 399 / 1814 | p_L6M (null / real families at threshold = FDR) | 79 / 223 = 35% | 35 / 66 = 52% | 13 / 20 = 64% | 5 / 8 = 68% |
|  |  /  (0.00) |  /  | 399 / 1814 | p_ALL (null / real families at threshold = FDR) | 485 / 1746 = 28% | 397 / 1617 = 25% | 291 / 1328 = 22% | 188 / 994 = 19% |
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

### London (real tested 333 of 335 family-bests, null tested 390 of 457)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| cross-market | 36 / 18 | 5 | 0 | 0% |  | 33 | 15 | 46% |
| bands | 18 / 31 | 2 | 4 |  |  | 14 | 29 | 208% |
| bar-native | 7 / 3 | 0 | 0 |  |  | 6 | 4 | 58% |
| confluence | 3 / 5 | 0 | 1 |  |  | 3 | 5 |  |
| levels:Fibonacci | 45 / 43 | 3 | 5 |  |  | 31 | 32 | 101% |
| levels:VWAP | 23 / 18 | 1 | 0 |  |  | 21 | 15 | 72% |
| levels:pivots | 4 / 3 | 1 | 0 |  |  | 3 | 4 |  |
| levels:profile / stack / walls / UW | 1 / 14 | 0 | 2 |  |  | 1 | 13 |  |
| levels:session / prior / round / opens / gaps | 15 / 21 | 0 | 0 |  |  | 13 | 19 | 143% |
| levels:swing S/R, trendline, channel | 23 / 13 | 0 | 1 |  |  | 17 | 5 | 27% |
| levels:zones / supply-demand | 13 / 47 | 0 | 7 |  |  | 12 | 28 | 233% |
| mean reversion / manual indicators | 6 / 21 | 0 | 6 |  |  | 4 | 18 |  |
| momentum | 33 / 34 | 0 | 4 |  |  | 24 | 29 | 121% |
| order book | 25 / 18 | 1 | 2 |  |  | 20 | 14 | 70% |
| other trigger | 0 / 5 | 0 | 1 |  |  | 0 | 5 |  |
| pullback | 3 / 2 | 0 | 0 |  |  | 1 | 1 |  |
| session structure | 3 / 16 | 0 | 2 |  |  | 2 | 15 |  |
| tape / order flow | 36 / 43 | 2 | 4 |  |  | 27 | 37 | 138% |
| trend | 39 / 35 | 3 | 6 |  |  | 27 | 30 | 112% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| time | 95 / 89 | 9 | 7 | 78% |  | 71 | 76 | 107% |
| composite / micro | 6 / 1 | 0 | 0 |  |  | 5 | 0 | 0% |
| delta | 7 / 9 | 0 | 2 |  |  | 7 | 9 | 133% |
| dollar | 5 / 6 | 1 | 2 |  |  | 4 | 1 |  |
| event / swing / other | 24 / 48 | 2 | 6 |  |  | 16 | 45 | 277% |
| imbalance / run (information) | 36 / 43 | 4 | 5 |  |  | 29 | 42 | 145% |
| kagi / P&F / line-break | 26 / 25 | 0 | 6 |  |  | 19 | 6 | 31% |
| range | 27 / 31 | 0 | 4 |  |  | 21 | 33 | 155% |
| renko-type | 37 / 46 | 0 | 6 |  |  | 29 | 21 | 72% |
| tick | 21 / 14 | 1 | 4 |  |  | 14 | 15 | 108% |
| volume | 49 / 78 | 1 | 4 |  |  | 44 | 69 | 156% |

**(trigger x bar) blocks**: 148 blocks with any tested family-best, 1 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| cross-market | time | 16 / 6 | 5 | 0 | 0% |  | 50% |

### NYAM (real tested 1814 of 1,821 family-bests, null tested 399 of 730)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| bands | 253 / 30 | 15 | 0 | 0% | 0% | 249 | 46 | 18% |
| levels:profile / stack / walls / UW | 284 / 14 | 118 | 11 | 9% | 15% | 280 | 20 | 7% |
| levels:session / prior / round / opens / gaps | 230 / 33 | 15 | 2 | 12% |  | 221 | 40 | 18% |
| momentum | 121 / 23 | 9 | 2 | 20% |  | 116 | 35 | 30% |
| levels:Fibonacci | 210 / 30 | 14 | 4 | 26% |  | 202 | 37 | 18% |
| levels:VWAP | 118 / 9 | 9 | 4 | 41% |  | 114 | 16 | 14% |
| trend | 72 / 24 | 9 | 4 | 41% |  | 69 | 37 | 53% |
| order book | 82 / 21 | 8 | 4 | 46% |  | 75 | 29 | 39% |
| session structure | 115 / 14 | 6 | 4 | 61% |  | 112 | 22 | 20% |
| tape / order flow | 66 / 24 | 5 | 9 | 182% |  | 61 | 31 | 51% |
| bar-native | 17 / 5 | 1 | 0 |  |  | 17 | 5 | 32% |
| confluence | 11 / 4 | 0 | 0 |  |  | 10 | 5 | 55% |
| cross-market | 45 / 23 | 3 | 0 |  |  | 42 | 35 | 82% |
| levels:pivots | 33 / 2 | 1 | 0 |  |  | 30 | 2 | 6% |
| levels:swing S/R, trendline, channel | 86 / 14 | 4 | 4 |  |  | 76 | 11 | 14% |
| levels:zones / supply-demand | 37 / 115 | 4 | 27 |  |  | 36 | 97 | 268% |
| mean reversion / manual indicators | 17 / 10 | 1 | 5 |  |  | 16 | 11 | 68% |
| other trigger | 4 / 0 | 0 | 0 |  |  | 4 | 0 |  |
| pullback | 13 / 4 | 0 | 0 |  |  | 13 | 5 | 42% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| delta | 88 / 9 | 13 | 0 | 0% | 0% | 85 | 15 | 17% |
| range | 95 / 34 | 5 | 0 | 0% |  | 88 | 42 | 48% |
| tick | 134 / 20 | 26 | 0 | 0% |  | 132 | 35 | 26% |
| event / swing / other | 198 / 54 | 24 | 4 | 15% |  | 190 | 73 | 39% |
| volume | 268 / 50 | 32 | 5 | 17% | 18% | 266 | 73 | 28% |
| dollar | 35 / 5 | 7 | 2 | 26% |  | 34 | 2 | 5% |
| imbalance / run (information) | 227 / 67 | 33 | 13 | 39% | 42% | 213 | 79 | 37% |
| renko-type | 271 / 45 | 25 | 15 | 58% | 109% | 260 | 29 | 11% |
| time | 327 / 83 | 40 | 27 | 68% | 73% | 316 | 126 | 40% |
| kagi / P&F / line-break | 171 / 31 | 17 | 13 | 75% | 109% | 162 | 11 | 7% |
| composite / micro | 0 / 1 | 0 | 0 |  |  | 0 | 0 |  |

**(trigger x bar) blocks**: 169 blocks with any tested family-best, 10 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | time | 76 / 7 | 6 | 0 | 0% |  | 15% |
| levels:profile / stack / walls / UW | delta | 16 / 0 | 12 | 0 | 0% | 0% | 0% |
| levels:profile / stack / walls / UW | dollar | 5 / 0 | 5 | 0 | 0% |  | 0% |
| levels:profile / stack / walls / UW | imbalance / run (information) | 32 / 1 | 20 | 0 | 0% | 0% | 6% |
| levels:profile / stack / walls / UW | tick | 23 / 0 | 13 | 0 | 0% |  | 0% |
| levels:profile / stack / walls / UW | volume | 46 / 0 | 17 | 0 | 0% | 0% | 0% |
| levels:profile / stack / walls / UW | renko-type | 44 / 1 | 13 | 2 | 14% |  | 0% |
| levels:profile / stack / walls / UW | kagi / P&F / line-break | 31 / 2 | 8 | 2 | 23% |  | 0% |
| levels:profile / stack / walls / UW | event / swing / other | 45 / 3 | 14 | 4 | 26% |  | 12% |
| levels:profile / stack / walls / UW | time | 19 / 5 | 12 | 4 | 30% | 0% | 57% |

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

