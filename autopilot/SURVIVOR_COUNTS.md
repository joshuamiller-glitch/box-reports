# SURVIVOR_COUNTS - the LADDER (cheapest test first; W-SHORT, orders 1845Z + 1932Z), refreshed 2026-11-19 01:27Z

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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 2,992 (upper bound) | 1,890 | RUNNING: stage A (30 draws, same bracket, equal-risk) 1,885 of 1,890 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 521 / 182 / 31; reached stage B (200 draws) 362, C (1,000) 26, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 1,890 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 1232 / 1618 at q 5% / 10% / 20% | SET 1: 0, SET 2: 1232 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 1,035 (upper bound) | 808 | RUNNING: stage A (30 draws, same bracket, equal-risk) 803 of 808 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 48 / 9 / 2; reached stage B (200 draws) 27, C (1,000) 0, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 808 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 0 / 302 at q 5% / 10% / 20% | SET 1: 0, SET 2: 0 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 9,504 (upper bound) | 4,556 | RUNNING: stage A (30 draws, same bracket, equal-risk) 4,514 of 4,556 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 571 / 164 / 44; reached stage B (200 draws) 1144, C (1,000) 51, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 4,556 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 3436 / 4185 at q 5% / 10% / 20% | SET 1: 0, SET 2: 3436 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
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
| R3 | per-cell p-value, adaptive 30 -> 200 -> 1,000 -> 10,000 same-bracket random draws, BH q = 10% over all family-bests (smallest p reachable: 30 draws 0.032, 200 0.0050, 1,000 0.0010, 10,000 0.0001; no cell can pass on 30 draws alone) | 531 (upper bound) | 396 | RUNNING: stage A (30 draws, same bracket, equal-risk) 208 of 396 family-bests tested; beat >= 24 / 27 / 29 of 30 on L6M: 46 / 34 / 15; reached stage B (200 draws) 164, C (1,000) 0, D (10,000) 0 (advance if EITHER the L6M or the whole-history statistic meets the stage rule); BH over all 396 family-bests (untested = p 1): SET 1 (p_L6M) 0 / 0 / 0, SET 2 (p_ALL) 0 / 0 / 162 at q 5% / 10% / 20% | SET 1: 0, SET 2: 0 inside BH (q 10%) so far | measured on the run | R4: 1,585 core-h shared by all four sessions, 25% of A+B: 27.5 h; whole fleet 5.0 h | |
| R4 | selection-corrected null (5 full null draws: calibration check = cells passing R0-R3 in a null draw vs real, plus the best-pick comparison) | all | all | not started as a full set (draws 1-2 partly on disk; W-GRIDOPS owns it) | n/a | 0 | R5a: 4,752 set-months = 238 core-h | 6.2 h on the measured fleet (763/h), 1.6 h when A and B are engine-ready (2894/h) |
| R5a | engine L6M (+L3M) as ADD and as replacement, family-best members in rank order | 396 families (upper bound) | 396 | engine rows negative on both -> out; not run for this session | n/a | engine rows on disk only for the leads | prior years (+28,512 set-months) then 30 date-shift controls (+71,280 set-months = 3564 core-h) for the rows still alive | 37.4 h / **93 h (> 48 h: Josh decides between more machines and waiting)** (prior years / controls, at 763/h) |

- R0 detail: cells evaluated 4,842,376; PASS **531 cells in 396 families** (non-reversal bars 401, reversal 86 (provisional until the look-ahead gate), other 44; level / S-D modules 112; AMBER prior year(s) 116). Distinct (row, module) files among the passers: 345.
- cells passing bare but failing own-stop: n/a until R1 runs; they are kept, labelled "depends on today's stack".
- every evaluated cell with its reason (kept for the 2-week refit): server 2 /mnt/l2/l2vast/_grid/rule/bare_NYPM.parquet; passing cells with family id / order / rank in family: pass_bare_NYPM.csv.

## R3 PASS SETS side by side (Benjamini-Hochberg across ALL family-bests of the session; untested cells count as p = 1; the counts grow as draws complete)

SET 1 (strict, current rule) = inside BH on p_L6M (last 26 weeks, equal-risk sum of R). SET 2 (proposed, order 2057Z) = inside BH on p_ALL (whole history, first month to today, L6M included) AND still passing R0 / R1 unchanged (every cell here already passed R0; R1 own-stop pending). Cells in SET 2 with p_L6M > 0.20 are flagged "recent no better than random" (shown, not dropped). p = (1 + k) / (1 + n), k = random draws at least as good, n = draws; weakest prior-year p shown separately. Engine order: SET 1 first, then SET 2 members best p first, no cap; Josh decides which set is the pass rule. Engine cost per passer: R5a 12 set-months + prior years 72 + 30 date-shift controls 180 = 264 set-months = ~13 core-h = 0.35 h at the measured 763 set-months/h. Dated D8 spec estimate: W-PLAN, ENGINE_PLAN.md.

| session | family-bests | tested | SET 1 q5 / q10 / q20 | SET 1 expected false (q10) | SET 1 engine core-h / h | SET 2 q5 / q10 / q20 | SET 2 expected false (q10) | SET 2 engine core-h / h | SET 2 flagged recent no better than random (q10) | smallest p: L6M / ALL |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,890 | 1,885 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 1232 / 1618 | 123.2 | 16262 / 426.3 h | 910 | 0.0249 / 0.0003 |
| London | 808 | 803 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 0 / 302 | 0.0 | 0 / 0.0 h | 0 | 0.0645 / 0.0100 |
| NYAM | 4,556 | 4,514 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 3436 / 4185 | 343.6 | 45355 / 1188.9 h | 3059 | 0.0299 / 0.0002 |
| NYPM | 396 | 208 | 0 / 0 / 0 | 0.0 | 0 / 0.0 h | 0 / 0 / 162 | 0.0 | 0 / 0.0 h | 0 | 0.0323 / 0.0050 |

## CALIBRATION: measured false-discovery rate from the whole-search null (order 2218Z, partial draw 1)

Label: PARTIAL / coarse (draw p1rand1 only, files that exist so far; the real search is restricted to the same (row, module) files and the pass-1 coverage; one family definition: same file + parameter). FDR(b) = expected null family-bests / real family-bests at the threshold "beats >= b of 30 draws" (p <= (31 - b + 1) / 31). Stage A only (30 draws): the finest p reachable is 0.032, so FDR <= 10% can only be read where it shows below.

| session | R0 pass cells null / real (ratio) | R0 families null / real | tested null / real (sampled family-bests) | stat | b = 24 | 27 | 29 | 30 |
|---|---|---|---|---|---|---|---|---|
| Asia | 380 / 963 (0.39) | 372 / 904 | 245 / 276 | p_L6M (null / real families at threshold = FDR) | 100 / 259 = 39% | 32 / 75 = 42% | 15 / 7 = 232% | 9 / 0 = n/a |
|  |  /  (0.00) |  /  | 245 / 276 | p_ALL (null / real families at threshold = FDR) | 237 / 835 = 28% | 173 / 750 = 23% | 117 / 616 = 19% | 73 / 455 = 16% |
| London | 466 / 347 (1.34) | 457 / 335 | 249 / 249 | p_L6M (null / real families at threshold = FDR) | 48 / 22 = 222% | 18 / 4 = 455% | 4 / 3 = 136% | 4 / 0 = n/a |
|  |  /  (0.00) |  /  | 249 / 249 | p_ALL (null / real families at threshold = FDR) | 319 / 261 = 122% | 239 / 198 = 121% | 162 / 121 = 133% | 99 / 96 = 104% |
| NYAM | 763 / 1,915 (0.40) | 730 / 1,821 | 250 / 250 | p_L6M (null / real families at threshold = FDR) | 79 / 240 = 33% | 44 / 95 = 46% | 12 / 22 = 53% | 6 / 0 = n/a |
|  |  /  (0.00) |  /  | 250 / 250 | p_ALL (null / real families at threshold = FDR) | 491 / 1719 = 29% | 400 / 1559 = 26% | 298 / 1260 = 24% | 181 / 954 = 19% |
| NYPM | 238 / 195 (1.22) | 233 / 193 | 230 / 191 | p_L6M (null / real families at threshold = FDR) | 55 / 45 = 120% | 31 / 31 = 100% | 10 / 17 = 59% | 4 / 9 = 45% |
|  |  /  (0.00) |  /  | 230 / 191 | p_ALL (null / real families at threshold = FDR) | 186 / 188 = 99% | 167 / 176 = 95% | 137 / 131 = 104% | 99 / 92 = 108% |

Reading: FDR above 100% = the null produces MORE family-bests than the real search at that threshold (no signal there); a threshold with FDR <= 10% (5% / 20%) is the calibrated pass rule for that session on that statistic. With only 30 draws per cell the table is coarse; stages B/C/D and draws 2-5 refine it.

## CALIBRATION BY FAMILY (order 0125Z; same footing as the table above: null draw 1 through the same stage A, p_L6M and p_ALL)

FDR(b) = null family-bests beating >= b of 30 draws / real family-bests beating >= b, per trigger family, bar family and (trigger x bar) block; counts are scaled to ALL family-bests of each set when only a part is tested (tested n shown). b = 24 / 27 shown on p_L6M with p_ALL beside. FDR < 100% = real > null; a block with real >> null is where the engine and the deeper stages go first; null >= real = last, not dropped. A block needs >= 5 real family-bests at b = 24 to be ranked (small counts give an unstable ratio). The best-of-many effect is shown by the number of blocks tested.

### Asia (real tested 276 of 904 family-bests, null tested 245 of 372)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| levels:pivots | 9 / 6 | 7 | 0 | 0% |  | 26 | 3 | 12% |
| pullback | 8 / 4 | 16 | 0 | 0% | 0% | 26 | 3 | 12% |
| bands | 47 / 21 | 69 | 9 | 13% | 15% | 154 | 24 | 16% |
| session structure | 12 / 9 | 10 | 2 | 15% |  | 36 | 9 | 25% |
| levels:Fibonacci | 41 / 23 | 49 | 9 | 19% | 0% | 111 | 21 | 19% |
| tape / order flow | 17 / 13 | 20 | 6 | 31% | 46% | 49 | 14 | 28% |
| momentum | 40 / 18 | 29 | 12 | 41% | 46% | 121 | 21 | 18% |
| levels:swing S/R, trendline, channel | 11 / 9 | 10 | 5 | 46% |  | 36 | 9 | 25% |
| levels:profile / stack / walls / UW | 14 / 10 | 7 | 3 | 46% |  | 46 | 9 | 20% |
| cross-market | 8 / 15 | 16 | 14 | 83% |  | 23 | 21 | 93% |
| trend | 27 / 28 | 16 | 15 | 93% |  | 85 | 33 | 39% |
| bar-native | 4 / 1 | 0 | 2 |  |  | 13 | 2 | 12% |
| confluence | 0 / 1 | 0 | 0 |  |  | 0 | 2 |  |
| levels:VWAP | 9 / 9 | 3 | 3 |  |  | 23 | 8 | 33% |
| levels:session / prior / round / opens / gaps | 17 / 17 | 3 | 5 |  |  | 52 | 15 | 29% |
| levels:zones / supply-demand | 4 / 35 | 3 | 5 |  |  | 10 | 15 | 155% |
| mean reversion / manual indicators | 3 / 8 | 0 | 3 |  |  | 10 | 9 | 93% |
| order book | 5 / 14 | 0 | 6 |  |  | 13 | 15 | 116% |
| other trigger | 0 / 4 | 0 | 3 |  |  | 0 | 3 |  |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| dollar | 4 / 2 | 7 | 0 | 0% |  | 13 | 0 | 0% |
| imbalance / run (information) | 25 / 14 | 16 | 3 | 19% |  | 82 | 14 | 17% |
| tick | 13 / 7 | 13 | 3 | 23% |  | 39 | 11 | 27% |
| volume | 38 / 27 | 43 | 11 | 25% | 23% | 121 | 35 | 29% |
| time | 100 / 56 | 144 | 38 | 26% | 23% | 311 | 67 | 21% |
| delta | 8 / 6 | 7 | 3 | 46% |  | 16 | 8 | 46% |
| event / swing / other | 41 / 51 | 10 | 11 | 108% |  | 124 | 49 | 39% |
| renko-type | 25 / 32 | 10 | 12 | 124% |  | 69 | 20 | 29% |
| range | 10 / 23 | 7 | 9 | 139% |  | 26 | 20 | 75% |
| kagi / P&F / line-break | 12 / 27 | 3 | 11 |  |  | 33 | 15 | 46% |

**(trigger x bar) blocks**: 125 blocks with any tested family-best, 13 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | tick | 3 / 1 | 7 | 0 | 0% |  | 15% |
| levels:swing S/R, trendline, channel | time | 4 / 0 | 7 | 0 | 0% |  | 0% |
| pullback | time | 3 / 1 | 10 | 0 | 0% | 0% | 0% |
| momentum | volume | 10 / 2 | 7 | 0 | 0% |  | 5% |
| levels:Fibonacci | time | 19 / 2 | 23 | 2 | 7% | 0% | 6% |
| bands | time | 22 / 6 | 46 | 6 | 13% | 23% | 11% |
| cross-market | volume | 4 / 1 | 10 | 2 | 15% |  | 12% |
| levels:Fibonacci | volume | 6 / 4 | 13 | 3 | 23% | 0% | 37% |
| session structure | time | 9 / 2 | 7 | 2 | 23% |  | 10% |
| momentum | time | 10 / 10 | 13 | 6 | 46% |  | 32% |

### London (real tested 249 of 335 family-bests, null tested 249 of 457)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| cross-market | 34 / 11 | 7 | 0 | 0% |  | 42 | 17 | 40% |
| bands | 12 / 14 | 3 | 4 |  |  | 13 | 20 | 150% |
| bar-native | 6 / 1 | 0 | 0 |  |  | 7 | 2 | 27% |
| confluence | 3 / 3 | 0 | 2 |  |  | 4 | 4 |  |
| levels:Fibonacci | 37 / 35 | 4 | 6 |  |  | 35 | 44 | 126% |
| levels:VWAP | 19 / 14 | 1 | 0 |  |  | 23 | 17 | 72% |
| levels:pivots | 3 / 0 | 1 | 0 |  |  | 3 | 0 |  |
| levels:profile / stack / walls / UW | 0 / 7 | 0 | 2 |  |  | 0 | 9 |  |
| levels:session / prior / round / opens / gaps | 12 / 10 | 0 | 0 |  |  | 15 | 15 | 99% |
| levels:swing S/R, trendline, channel | 15 / 9 | 0 | 2 |  |  | 13 | 4 | 27% |
| levels:zones / supply-demand | 7 / 26 | 0 | 6 |  |  | 9 | 29 | 312% |
| mean reversion / manual indicators | 5 / 12 | 0 | 6 |  |  | 4 | 13 |  |
| momentum | 19 / 23 | 0 | 6 |  |  | 20 | 33 | 164% |
| order book | 18 / 14 | 0 | 2 |  |  | 20 | 17 | 82% |
| other trigger | 0 / 3 | 0 | 2 |  |  | 0 | 4 |  |
| pullback | 0 / 1 | 0 | 0 |  |  | 0 | 2 |  |
| session structure | 2 / 13 | 0 | 2 |  |  | 1 | 18 |  |
| tape / order flow | 26 / 27 | 1 | 2 |  |  | 24 | 37 | 152% |
| trend | 31 / 26 | 4 | 9 |  |  | 27 | 37 | 136% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| time | 72 / 59 | 12 | 7 | 61% |  | 71 | 83 | 116% |
| composite / micro | 4 / 1 | 0 | 0 |  |  | 4 | 0 |  |
| delta | 5 / 6 | 0 | 4 |  |  | 7 | 11 | 164% |
| dollar | 5 / 5 | 1 | 4 |  |  | 5 | 2 | 34% |
| event / swing / other | 19 / 25 | 1 | 6 |  |  | 17 | 37 | 210% |
| imbalance / run (information) | 26 / 27 | 4 | 6 |  |  | 28 | 40 | 143% |
| kagi / P&F / line-break | 22 / 18 | 0 | 6 |  |  | 20 | 7 | 36% |
| range | 20 / 20 | 0 | 6 |  |  | 22 | 31 | 145% |
| renko-type | 25 / 30 | 0 | 6 |  |  | 27 | 20 | 75% |
| tick | 14 / 9 | 1 | 4 |  |  | 15 | 15 | 99% |
| volume | 37 / 49 | 1 | 2 |  |  | 44 | 73 | 165% |

**(trigger x bar) blocks**: 128 blocks with any tested family-best, 1 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| cross-market | time | 16 / 5 | 7 | 0 | 0% |  | 49% |

### NYAM (real tested 250 of 1,821 family-bests, null tested 250 of 730)

**by TRIGGER family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| bands | 40 / 21 | 22 | 0 | 0% | 0% | 291 | 47 | 16% |
| cross-market | 5 / 16 | 7 | 0 | 0% |  | 36 | 38 | 104% |
| levels:session / prior / round / opens / gaps | 29 / 21 | 22 | 3 | 13% | 40% | 197 | 38 | 19% |
| levels:profile / stack / walls / UW | 37 / 10 | 117 | 18 | 15% | 16% | 255 | 23 | 9% |
| levels:swing S/R, trendline, channel | 12 / 11 | 15 | 3 | 20% |  | 80 | 18 | 22% |
| levels:VWAP | 16 / 6 | 15 | 3 | 20% |  | 109 | 18 | 16% |
| levels:Fibonacci | 25 / 16 | 7 | 3 | 40% |  | 168 | 35 | 21% |
| tape / order flow | 10 / 14 | 7 | 3 | 40% |  | 66 | 29 | 45% |
| order book | 5 / 13 | 7 | 6 | 80% |  | 36 | 26 | 72% |
| mean reversion / manual indicators | 2 / 5 | 7 | 6 | 80% |  | 15 | 9 | 60% |
| trend | 17 / 18 | 7 | 6 | 80% | 0% | 117 | 41 | 35% |
| levels:zones / supply-demand | 6 / 67 | 7 | 26 | 361% |  | 36 | 96 | 265% |
| bar-native | 1 / 4 | 0 | 0 |  |  | 7 | 6 | 80% |
| confluence | 1 / 1 | 0 | 0 |  |  | 7 | 3 | 40% |
| levels:pivots | 6 / 1 | 0 | 0 |  |  | 36 | 0 | 0% |
| momentum | 18 / 15 | 0 | 3 |  |  | 124 | 38 | 31% |
| other trigger | 1 / 0 | 0 | 0 |  |  | 7 | 0 | 0% |
| pullback | 1 / 3 | 0 | 0 |  |  | 7 | 6 | 80% |
| session structure | 18 / 8 | 0 | 0 |  |  | 124 | 20 | 17% |

**by BAR family**

| family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL: real >= 24 | null >= 24 | FDR |
|---|---|---|---|---|---|---|---|---|
| delta | 10 / 8 | 15 | 0 | 0% | 0% | 73 | 20 | 28% |
| range | 18 / 18 | 7 | 0 | 0% |  | 109 | 32 | 29% |
| volume | 38 / 33 | 58 | 3 | 5% | 0% | 277 | 82 | 30% |
| event / swing / other | 23 / 35 | 22 | 6 | 27% | 80% | 160 | 82 | 51% |
| kagi / P&F / line-break | 23 / 21 | 36 | 12 | 32% | 60% | 168 | 12 | 7% |
| imbalance / run (information) | 29 / 41 | 29 | 12 | 40% | 60% | 182 | 73 | 40% |
| renko-type | 43 / 25 | 29 | 18 | 60% | 80% | 299 | 29 | 10% |
| time | 45 / 55 | 44 | 29 | 67% | 100% | 306 | 128 | 42% |
| dollar | 0 / 3 | 0 | 0 |  |  | 0 | 3 |  |
| tick | 21 / 11 | 0 | 0 |  |  | 146 | 29 | 20% |

**(trigger x bar) blocks**: 125 blocks with any tested family-best, 24 with >= 5 real family-bests at b = 24 (ranked); the 10 lowest measured FDR(24):

| trigger family | bar family | tested real / null | real >= 24 | null >= 24 | FDR(24) | FDR(27) | p_ALL FDR(24) |
|---|---|---|---|---|---|---|---|
| bands | kagi / P&F / line-break | 2 / 1 | 7 | 0 | 0% |  | 0% |
| bands | time | 10 / 5 | 7 | 0 | 0% |  | 16% |
| bands | volume | 8 / 3 | 7 | 0 | 0% | 0% | 15% |
| cross-market | volume | 2 / 6 | 7 | 0 | 0% |  | 100% |
| levels:VWAP | event / swing / other | 4 / 1 | 7 | 0 | 0% |  | 13% |
| levels:VWAP | volume | 1 / 1 | 7 | 0 | 0% |  | 40% |
| levels:profile / stack / walls / UW | delta | 2 / 0 | 15 | 0 | 0% | 0% | 0% |
| levels:profile / stack / walls / UW | imbalance / run (information) | 3 / 1 | 15 | 0 | 0% | 0% | 13% |
| levels:profile / stack / walls / UW | volume | 9 / 0 | 36 | 0 | 0% | 0% | 0% |
| levels:profile / stack / walls / UW | range | 3 / 0 | 7 | 0 | 0% |  | 0% |

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

