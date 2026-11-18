# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-18 03:51Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**CORRECTION 02:30Z (read first): every random-entry null file produced by the fast path before 02:30Z was an exact COPY of the real result (the fast runner did not recognise the tag p1randN), so all earlier excess / percentile / null columns and the claim of null draws were INVALID (excess 0.0, percentile 1.00 = no null). 31,413 such files were deleted; the 1,411 legacy-runner null files are valid. Nulls are being regenerated; a null column is shown only when the null pool covers >= 80% of the real pool, otherwise it reads NO NULL YET. Real results are unaffected.**

**NULL AUDIT (assertions: a null file must differ from its real file; null mean pts/trade at plain 60/60 must be negative and above -6; a tag failing is rejected and its columns read NO NULL YET):**
| null tag | files | sampled | identical to real | mean pts/trade London / NYAM / NYPM / Asia | accepted | share of real cells covered (per session) | note |
|---|---|---|---|---|---|---|---|
| p1rand1 | 4532 | 400 | 0.000 | -0.66 / -0.56 / -0.60 / -1.09 | YES | {"London": null, "NYAM": null, "NYPM": null, "Asia": null} |  |
| p1rand2 | 4607 | 400 | 0.000 | -0.68 / -0.55 / -0.57 / -1.07 | YES | {"London": null, "NYAM": null, "NYPM": null, "Asia": null} |  |
| p1rand3 | 43 | 43 | 0.000 | -0.68 / -0.60 / -0.60 / -1.05 | YES | {"London": null, "NYAM": null, "NYPM": null, "Asia": null} |  |
| p1rand4 | 43 | 43 | 0.000 | -0.63 / -0.56 / -0.62 / -1.04 | YES | {"London": null, "NYAM": null, "NYPM": null, "Asia": null} |  |
| p1rand5 | 45 | 45 | 0.000 | -0.66 / -0.61 / -0.59 / -1.07 | YES | {"London": null, "NYAM": null, "NYPM": null, "Asia": null} |  |
Draws per cell = number of accepted null tags covering the pool (see per-session null_cover); needs >= 5 before any LEAD label.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-18 03:51Z):** result files per tag {"p1rand1": 6877, "p1rand2": 6928, "p1rand3": 135, "p1rand4": 135, "p1rand5": 132, "p1real": 18483, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, INFORMATION, PRICE, TIME; null draws per cell (random-entry replicas in the scored sessions): {"London": 0, "NYAM": 0, "NYPM": 0, "Asia": 0}; live-seven baseline: IN (125 rows). Sessions published: London, NYAM, NYPM, Asia (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-18 03:51Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"p1rand1": 6877, "p1rand2": 6928, "p1rand3": 135, "p1rand4": 135, "p1rand5": 132, "p1real": 18483, "rand1": 0, "real": 1654}; loop status: 2026-11-18T03:43Z rows=322 mods=116 todo=72823 running=0. 
Cells scored per session: {"London": 1829656, "NYAM": 2146740, "NYPM": 2189074, "Asia": 2113125}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -25.7 | -0.028 | 1209.1 | 0.49 | -86.9 | -87.9 |  |  |  |  | -27.0 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -17.3 | -0.014 | 1028.8 | 0.52 | -40.3 | -38.2 |  |  |  |  | -30.0 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -25.2 [no null yet] | -36.3 [no null yet] | -38.3 [no null yet] | 4.2 [no null yet] |
| bands (native) | -3.1 [no null yet] | 0.2 [no null yet] | -6.2 [no null yet] | -29.9 [no null yet] |
| barnative | -18.1 [no null yet] | 10.4 [no null yet] | -5.4 [no null yet] | -18.3 [no null yet] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -15.0 [no null yet] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | -11.5 [no null yet] | n/a (no signals by construction) |
| confluence | -17.7 [no null yet] | -26.6 [no null yet] | 2.3 [no null yet] | -11.7 [no null yet] |
| levels | -20.2 [no null yet] | -25.9 [no null yet] | 16.2 [no null yet] | -23.2 [no null yet] |
| levels (native) | -8.5 [no null yet] | -3.2 [no null yet] | -40.8 [no null yet] | -14.9 [no null yet] |
| live | -1.4 [no null yet] | -16.9 [no null yet] | -1.5 [no null yet] | 6.3 [no null yet] |
| manual | -34.8 [no null yet] | -5.2 [no null yet] | -28.7 [no null yet] | -5.0 [no null yet] |
| manual (native) | 13.4 [no null yet] | -30.5 [no null yet] | -10.8 [no null yet] | -27.1 [no null yet] |
| momentum | -16.1 [no null yet] | 16.9 [no null yet] | -28.2 [no null yet] | -6.6 [no null yet] |
| momentum (native) | -31.2 [no null yet] | -23.6 [no null yet] | -10.5 [no null yet] | -11.2 [no null yet] |
| pullback | -8.3 [no null yet] | -9.2 [no null yet] | -36.3 [no null yet] | -4.6 [no null yet] |
| pullback (native) | -19.8 [no null yet] | -0.1 [no null yet] | -3.3 [no null yet] | -39.7 [no null yet] |
| structure | 5.2 [no null yet] | -18.0 [no null yet] | -12.5 [no null yet] | -20.1 [no null yet] |
| structure (native) | -5.4 [no null yet] | -21.0 [no null yet] | -16.1 [no null yet] | -33.3 [no null yet] |
| tape | -11.7 [no null yet] | 5.4 [no null yet] | -14.4 [no null yet] | -24.9 [no null yet] |
| tape (native) | 12.7 [no null yet] | 3.9 [no null yet] | -26.0 [no null yet] | -29.1 [no null yet] |
| trend | -31.0 [no null yet] | -21.6 [no null yet] | -24.2 [no null yet] | -22.2 [no null yet] |
| trend (native) | -14.2 [no null yet] | -12.5 [no null yet] | -7.6 [no null yet] | -14.3 [no null yet] |
| xmarket | 2.3 [no null yet] | 6.0 [no null yet] | -13.1 [no null yet] | 12.2 [no null yet] |
### PASS 1: 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum|INFORMATION | 16.9 | 0.028 | 254.9 | 0.53 | 3.5 | -50.4 | {"2023": -15.5, "2024": 50.5, "2025": -8.6, "2026": 17.8} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels|PRICE | 16.2 | 0.016 | 683.0 | 0.52 | 110.4 | 126.7 | {"2023": -4.0, "2024": -1.0, "2025": -34.9, "2026": 103.6} |  |  |  | {"2023": "AMBER", "2024": "ok", "2025": "RED", "2026": "ok"} |
| manual (native)|ACTIVITY | 13.4 | 0.010 | 396.2 | 0.51 | 57.2 | 21.3 | {"2023": -40.5, "2024": 28.5, "2025": -3.3, "2026": 32.5} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "AMBER", "2026": "ok"} |
| tape (native)|ACTIVITY | 12.7 | 0.007 | 352.8 | 0.48 | 35.0 | -11.3 | {"2023": -32.3, "2024": -11.5, "2025": 17.7, "2026": 49.7} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| xmarket|TIME | 12.2 | 0.011 | 383.6 | 0.53 | 39.2 | 116.5 | {"2023": 25.0, "2024": 20.8, "2025": -1.7, "2026": 14.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| barnative|INFORMATION | 10.4 | 0.008 | 682.8 | 0.53 | 61.9 | 76.1 | {"2023": 29.5, "2024": 27.9, "2025": -17.3, "2026": 16.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| live|TIME | 6.3 | 0.006 | 538.3 | 0.54 | 81.1 | 29.7 | {"2023": -30.4, "2024": -12.7, "2025": -14.9, "2026": 65.7} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| xmarket|INFORMATION | 6.0 | 0.008 | 354.7 | 0.57 | 11.5 | 78.7 | {"2023": -5.3, "2024": 19.1, "2025": 5.5, "2026": -5.4} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| tape|INFORMATION | 5.4 | 0.004 | 670.0 | 0.54 | 85.2 | 71.8 | {"2023": 9.2, "2024": 3.7, "2025": -16.6, "2026": 32.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| structure|ACTIVITY | 5.2 | 0.010 | 683.1 | 0.58 | 37.6 | 85.3 | {"2023": -32.1, "2024": 32.3, "2025": 6.6, "2026": -16.6} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
Live books in London on their live bars (same screen, plain 60/60): K7 tm180 L6M -52.7 pts/wk, rank 5% (top 95.1%); M7 tm60 L6M -39.6 pts/wk, rank 9% (top 91.0%); U7 tm600 L6M -10.7 pts/wk, rank 33% (top 67.4%); P7 tm60 L6M 65.6 pts/wk, rank 99% (top 1.0%); H7 tm60 L6M 2.9 pts/wk, rank 62% (top 37.5%); A7 tm60 L6M 14.3 pts/wk, rank 80% (top 19.6%). Rank = share of ALL London cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| levels|ACTIVITY | 17.6 | 0.027 | 196.5 | 0.56 | 61.5 | -4.7 | {"2023": 4.1, "2024": -2.2, "2025": 7.9, "2026": 56.7} | -10.5 | 28.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| xmarket|TIME | 17.5 | 0.026 | 469.0 | 0.57 | 77.1 | 116.5 | {"2023": 34.5, "2024": 26.0, "2025": 29.2, "2026": -11.8} | 17.0 | 0.5 | 0.50 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| levels (native)|ACTIVITY | 15.2 | 0.027 | 523.4 | 0.57 | 82.1 | 63.5 | {"2023": -18.4, "2024": -23.5, "2025": 11.0, "2026": 76.6} | -4.7 | 19.8 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 15.1 | 0.004 | 354.1 | 0.53 | 99.4 | 151.5 | {"2023": -31.6, "2024": 6.2, "2025": 21.5, "2026": 33.0} | -8.9 | 24.0 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape (native)|INFORMATION | 14.8 | 0.005 | 228.7 | 0.51 | 23.5 | -49.1 | {"2023": -10.6, "2024": -5.8, "2025": 47.4, "2026": 8.8} | -28.8 | 43.6 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| levels (native)|INFORMATION | 8.5 | 0.006 | 716.8 | 0.52 | 89.2 | 64.6 | {"2023": -11.4, "2024": 18.6, "2025": -26.1, "2026": 43.7} | -3.4 | 11.8 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| structure (native)|PRICE | 4.0 | 0.014 | 351.5 | 0.53 | 11.0 | 84.9 | {"2023": -26.2, "2024": 16.1, "2025": -5.6, "2026": 10.4} | -22.9 | 26.8 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| manual (native)|PRICE | 2.1 | -0.003 | 440.6 | 0.51 | 27.5 | -75.3 | {"2023": -8.4, "2024": -4.3, "2025": -9.7, "2026": 26.9} | 6.1 | -4.0 | 0.50 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| pullback|PRICE | 0.7 | -0.004 | 1134.6 | 0.52 | 131.9 | 115.9 | {"2023": -15.9, "2024": -1.3, "2025": -28.4, "2026": 42.9} | -3.9 | 4.7 | 0.50 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| pullback (native)|PRICE | -0.9 | 0.003 | 411.7 | 0.49 | -80.5 | -61.7 | {"2023": 23.3, "2024": 3.5, "2025": 24.3, "2026": -43.7} | -25.3 | 24.4 | 0.50 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5738 | 2473 | 227 | 1.00 | 5 / -290 / 857 / 1.00 | {"2023": 534.0, "2024": -1080.0, "2025": -3184.0, "2026": 7299.0} |
| 2 | tm20 | barnative.barnative_run.rev | {"n": 2} | sym15u | both | 5614 | 2080 | 613 | 0.67 | 5 / -1401 / 1393 / 1.00 | {"2023": -1695.0, "2024": -839.0, "2025": -981.0, "2026": 7113.0} |
| 3 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5529 | 2203 | 230 | 1.00 | 3 / -865 / 1111 / 1.00 | {"2023": 877.0, "2024": 1413.0, "2025": 8.0, "2026": 5170.0} |
| 4 | renko_14 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym15u | both | 5484 | 2321 | 230 | 1.00 | 5 / -350 / 2382 / 1.00 | {"2023": 276.0, "2024": -1123.0, "2025": -2301.0, "2026": 6752.0} |
| 5 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym8u | both | 5463 | 2464 | 237 | 1.00 | 5 / -166 / 2075 / 1.00 | {"2023": 906.0, "2024": -1160.0, "2025": -1158.0, "2026": 5440.0} |
| 6 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | asym20u/10u | both | 5463 | 2464 | 237 | 1.00 | 5 / -166 / 2075 / 1.00 | {"2023": 768.0, "2024": -842.0, "2025": -872.0, "2026": 5499.0} |
| 7 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | asym10u/20u | both | 5463 | 2464 | 237 | 1.00 | 5 / -166 / 2075 / 1.00 | {"2023": 746.0, "2024": -695.0, "2025": -817.0, "2026": 5499.0} |
| 8 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | asym15u/30u | both | 5463 | 2464 | 237 | 1.00 | 5 / -166 / 2075 / 1.00 | {"2023": 830.0, "2024": -717.0, "2025": -822.0, "2026": 5499.0} |
| 9 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym30u | both | 5463 | 2464 | 237 | 1.00 | 5 / -166 / 2075 / 1.00 | {"2023": 826.0, "2024": -692.0, "2025": -822.0, "2026": 5499.0} |
| 10 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5463 | 2464 | 237 | 1.00 | 5 / -166 / 2075 / 1.00 | {"2023": 821.0, "2024": -731.0, "2025": -822.0, "2026": 5499.0} |
| 11 | urenko_20 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym15u | both | 5432 | 2406 | 219 | 1.00 | 2 / -381 / -379 / 1.00 | {"2023": 1248.0, "2024": -1972.0, "2025": -1111.0, "2026": 6190.0} |
| 12 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5312 | 1946 | 232 | 1.00 | 3 / 416 / 1736 / 1.00 | {"2023": 700.0, "2024": 1874.0, "2025": 1442.0, "2026": 5164.0} |
| 13 | time_s_5 | tape.tape_libvol.adline | {"len": 20} | plain60/60 | both | 5303 | 2868 | 836 | 0.67 | 5 / -829 / 482 / 1.00 | {"2023": 371.0, "2024": 263.0, "2025": 552.0, "2026": 6708.0} |
| 14 | tm420 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym8u | both | 5290 | 2420 | 222 | 1.00 | 5 / -415 / 1794 / 1.00 | {"2023": 156.0, "2024": -892.0, "2025": 371.0, "2026": 6926.0} |
| 15 | tm15 | structure.structure_inside.outside | {"cf": 0.6, "filt": 0} | sym15u | both | 5261 | 1540 | 719 | 0.75 | 5 / 377 / 1624 / 1.00 | {"2023": 266.0, "2024": -2665.0, "2025": -2838.0, "2026": 5771.0} |
| 16 | dchg_10 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5243 | 1638 | 244 | 1.00 | 3 / -767 / -274 / 1.00 | {"2023": 196.0, "2024": -2911.0, "2025": 102.0, "2026": 6078.0} |
| 17 | tm20 | bands.bands_regchan.break_linreg | {"n": 10, "k": 2.0} | sym30u | both | 5232 | 2965 | 322 | 0.60 | 2 / -839 / 475 / 1.00 | {"2023": -251.0, "2024": -1460.0, "2025": -830.0, "2026": 4221.0} |
| 18 | tm420 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5217 | 2405 | 222 | 1.00 | 5 / -349 / 1844 / 1.00 | {"2023": -371.0, "2024": -149.0, "2025": -9.0, "2026": 6896.0} |
| 19 | tm420 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym30u | both | 5217 | 2405 | 222 | 1.00 | 5 / -349 / 1844 / 1.00 | {"2023": -433.0, "2024": 337.0, "2025": -25.0, "2026": 6914.0} |
| 20 | tm420 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym10u/20u | both | 5217 | 2405 | 222 | 1.00 | 5 / -349 / 1844 / 1.00 | {"2023": 86.0, "2024": -1076.0, "2025": -645.0, "2026": 6930.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 25.4 | 0.020 | 653.4 | 0.56 | -6.9 | 113.0 |  |  |  |  | -13.9 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 31.5 | 0.025 | 596.1 | 0.56 | 8.8 | 126.6 |  |  |  |  | -9.0 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -2.1 [no null yet] | 15.1 [no null yet] | -8.8 [no null yet] | 21.5 [no null yet] |
| bands (native) | -21.8 [no null yet] | -7.0 [no null yet] | 43.5 [no null yet] | 35.1 [no null yet] |
| barnative | -7.0 [no null yet] | -17.1 [no null yet] | 19.7 [no null yet] | 11.1 [no null yet] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -24.2 [no null yet] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | -10.4 [no null yet] | n/a (no signals by construction) |
| confluence | 13.5 [no null yet] | -5.0 [no null yet] | 54.0 [no null yet] | 12.5 [no null yet] |
| levels | 42.0 [no null yet] | -31.2 [no null yet] | 15.9 [no null yet] | -1.3 [no null yet] |
| levels (native) | 12.2 [no null yet] | 17.5 [no null yet] | 44.8 [no null yet] | -9.2 [no null yet] |
| live | 17.8 [no null yet] | 4.6 [no null yet] | -5.5 [no null yet] | -10.3 [no null yet] |
| manual | -3.7 [no null yet] | 40.1 [no null yet] | -24.2 [no null yet] | 33.3 [no null yet] |
| manual (native) | -61.0 [no null yet] | -58.7 [no null yet] | 11.8 [no null yet] | -16.6 [no null yet] |
| momentum | 9.4 [no null yet] | 1.2 [no null yet] | -9.5 [no null yet] | 38.9 [no null yet] |
| momentum (native) | 7.6 [no null yet] | 14.2 [no null yet] | -4.3 [no null yet] | 35.1 [no null yet] |
| pullback | 20.3 [no null yet] | 22.6 [no null yet] | 33.2 [no null yet] | -1.4 [no null yet] |
| pullback (native) | 32.7 [no null yet] | -4.6 [no null yet] | 8.7 [no null yet] | -18.9 [no null yet] |
| structure | 32.8 [no null yet] | 0.7 [no null yet] | 23.9 [no null yet] | -0.9 [no null yet] |
| structure (native) | 34.7 [no null yet] | 34.3 [no null yet] | 10.4 [no null yet] | 38.2 [no null yet] |
| tape | 5.8 [no null yet] | -13.9 [no null yet] | 0.2 [no null yet] | 30.8 [no null yet] |
| tape (native) | 37.5 [no null yet] | -6.0 [no null yet] | 13.9 [no null yet] | -5.9 [no null yet] |
| trend | -23.4 [no null yet] | -30.3 [no null yet] | -1.1 [no null yet] | 8.7 [no null yet] |
| trend (native) | -20.9 [no null yet] | -10.4 [no null yet] | 20.9 [no null yet] | 40.0 [no null yet] |
| xmarket | 5.3 [no null yet] | -9.9 [no null yet] | -30.4 [no null yet] | -45.4 [no null yet] |
### PASS 1: 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| confluence|PRICE | 54.0 | 0.046 | 317.8 | 0.59 | 49.9 | -139.6 | {"2023": 61.8, "2024": 78.7, "2025": 26.9, "2026": 54.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 44.8 | 0.040 | 250.6 | 0.62 | 18.3 | 6.9 | {"2023": 29.5, "2024": 22.3, "2025": 84.5, "2026": 29.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 43.5 | 0.027 | 734.3 | 0.62 | -2.5 | 17.8 | {"2023": 38.3, "2024": 23.6, "2025": 131.6, "2026": -35.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| levels|ACTIVITY | 42.0 | 0.034 | 764.6 | 0.53 | 64.6 | 10.9 | {"2023": -8.6, "2024": 80.2, "2025": -1.5, "2026": 64.4} |  |  |  | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|INFORMATION | 40.1 | 0.025 | 425.4 | 0.59 | 73.0 | -52.6 | {"2023": 5.5, "2024": 3.9, "2025": 75.2, "2026": 52.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend (native)|TIME | 40.0 | 0.015 | 332.0 | 0.56 | 77.4 | 227.5 | {"2023": -2.0, "2024": 0.5, "2025": 52.2, "2026": 85.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|TIME | 38.9 | 0.022 | 664.8 | 0.57 | 96.6 | 167.5 | {"2023": 17.7, "2024": 68.8, "2025": 52.6, "2026": -6.1} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| structure (native)|TIME | 38.2 | 0.025 | 551.9 | 0.59 | 92.4 | 185.9 | {"2023": -14.3, "2024": 13.7, "2025": 59.5, "2026": 58.8} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape (native)|ACTIVITY | 37.5 | 0.025 | 459.3 | 0.57 | 127.4 | 173.3 | {"2023": 0.6, "2024": 23.1, "2025": 70.1, "2026": 27.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|TIME | 35.1 | 0.022 | 872.8 | 0.54 | 71.5 | 198.2 | {"2023": 17.7, "2024": 84.6, "2025": 52.6, "2026": -38.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
Live books in NYAM on their live bars (same screen, plain 60/60): K7 tm180 L6M -75.5 pts/wk, rank 5% (top 94.8%); M7 tm60 L6M -8.9 pts/wk, rank 43% (top 57.4%); U7 tm600 L6M -11.4 pts/wk, rank 39% (top 60.6%); P7 tm60 L6M -60.7 pts/wk, rank 8% (top 91.6%); H7 tm60 L6M 28.8 pts/wk, rank 88% (top 11.8%); A7 tm60 L6M -17.2 pts/wk, rank 33% (top 67.0%); O7 tm60 L6M 15.1 pts/wk, rank 79% (top 21.0%). Rank = share of ALL NYAM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| levels (native)|ACTIVITY | 65.0 | 0.050 | 339.7 | 0.60 | 144.7 | 127.8 | {"2023": -31.7, "2024": 43.6, "2025": 110.9, "2026": 66.8} | 3.3 | 61.7 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|TIME | 48.7 | 0.024 | 585.7 | 0.52 | -30.1 | -92.1 | {"2023": 15.7, "2024": -14.5, "2025": 136.2, "2026": 30.5} | -28.5 | 77.2 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| levels|ACTIVITY | 42.0 | 0.036 | 390.4 | 0.65 | 148.9 | 116.7 | {"2023": 22.8, "2024": 38.0, "2025": 36.7, "2026": 59.0} | 10.4 | 31.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|PRICE | 39.3 | 0.014 | 368.8 | 0.51 | 53.6 | 56.0 | {"2023": 50.3, "2024": -5.3, "2025": 68.1, "2026": 54.7} | -8.0 | 47.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|ACTIVITY | 38.9 | 0.026 | 495.8 | 0.59 | 20.0 | 125.2 | {"2023": -27.2, "2024": 51.0, "2025": 97.8, "2026": -23.9} | -12.1 | 51.0 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum|TIME | 38.6 | 0.023 | 665.0 | 0.57 | 96.6 | 167.5 | {"2023": 17.7, "2024": 67.9, "2025": 52.6, "2026": -6.1} | 3.5 | 35.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| tape|TIME | 37.7 | 0.017 | 388.0 | 0.54 | 147.6 | 204.2 | {"2023": 15.3, "2024": 14.5, "2025": 28.7, "2026": 82.9} | 16.8 | 20.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|TIME | 35.1 | 0.022 | 872.8 | 0.54 | 71.5 | 198.2 | {"2023": 17.7, "2024": 84.6, "2025": 52.6, "2026": -38.6} | -24.9 | 60.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual|TIME | 33.3 | 0.018 | 623.4 | 0.58 | 27.7 | 281.0 | {"2023": 8.9, "2024": 19.4, "2025": 44.7, "2026": 43.9} | 6.4 | 26.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape (native)|TIME | 28.9 | 0.021 | 470.3 | 0.57 | 175.6 | 99.6 | {"2023": -51.9, "2024": 6.1, "2025": -14.8, "2026": 133.2} | -19.0 | 47.9 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | swing_atr_0.1 | tape.tape_speed.follow_native | {"f": 3.0, "L": 3600} | sym15u | both | 8142 | 2340 | 562 | 1.00 | 3 / -1559 / 400 / 1.00 | {"2023": -2474.0, "2024": -2255.0, "2025": 763.0, "2026": 10386.0} |
| 2 | renko_10 | levels.levels_round.reject | {"tol": 1.0, "conf": "close"} | sym15u | both | 8023 | 656 | 657 | 0.67 | 2 / 2626 / 2906 / 1.00 | {"2023": -600.0, "2024": -3119.0, "2025": -4002.0, "2026": 8822.0} |
| 3 | dib_700 | bands.bands_bollinger.fade | {"n": 30, "k": 2.5} | plain60/60 | both | 7435 | 2353 | 1144 | 1.00 | 3 / -1515 / 3432 / 1.00 | {"2023": -1197.0, "2024": -2377.0, "2025": -3514.0, "2026": 4023.0} |
| 4 | time_m_1 | xmarket.xmarket_ym.follow | {"w": 3, "thr": 1.0} | sym8u | both | 7351 | 4294 | 534 | 1.00 | 5 / 530 / 3387 / 1.00 | {"2023": -1624.0, "2024": 2856.0, "2025": 1532.0, "2026": 5925.0} |
| 5 | urenko_28 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | sym15u | both | 7321 | 200 | 489 | 1.00 | 2 / 2738 / 6472 / 1.00 | {"2023": -590.0, "2024": 2748.0, "2025": -3027.0, "2026": 6089.0} |
| 6 | tm15 | trend.trend_macd.hist_turn_native | {"len": 19, "width": 0.0} | asym15u/30u | both | 7174 | 4038 | 580 | 1.00 | 2 / 2333 / 3664 / 1.00 | {"2023": -146.0, "2024": -557.0, "2025": 1556.0, "2026": 4858.0} |
| 7 | tm15 | trend.trend_macd.hist_turn | {"len": 19, "width": 0.0} | asym15u/30u | both | 7174 | 4038 | 580 | 1.00 | 2 / -3862 / -3591 / 1.00 | {"2023": -146.0, "2024": -557.0, "2025": 1556.0, "2026": 4858.0} |
| 8 | tm10 | bands.bands_regchan.break_stderr | {"n": 40, "k": 2.5} | sym8u | both | 7168 | 4001 | 866 | 0.67 | 5 / -1372 / 2094 / 1.00 | {"2023": 422.0, "2024": 630.0, "2025": 1668.0, "2026": 2987.0} |
| 9 | mom_10 | tape.tape_delta.fade_native | {"L": 1800, "z": 1.5} | plain60/60 | both | 7160 | 3053 | 1702 | 1.00 | 3 / -337 / 9 / 1.00 | {"2023": -3242.0, "2024": -508.0, "2025": -9093.0, "2026": 6877.0} |
| 10 | wrenko_10 | manual.manual_macd.histturn | {"f": 5, "s": 13, "g": 5} | plain60/60 | both | 7125 | 2270 | 1721 | 1.00 | 2 / -1210 / -351 / 1.00 | {"2023": 1069.0, "2024": 1029.0, "2025": -6564.0, "2026": 6771.0} |
| 11 | renko_10 | manual.manual_macd.histturn | {"f": 5, "s": 13, "g": 5} | plain60/60 | both | 7125 | 2270 | 1721 | 1.00 | 3 / -1447 / 741 / 1.00 | {"2023": 1069.0, "2024": 1029.0, "2025": -6564.0, "2026": 6771.0} |
| 12 | vol_350 | levels.levels_round.break_native | {"n": 2, "k": 0.25} | sym15u | both | 7094 | 3963 | 495 | 1.00 | 3 / 443 / 1247 / 1.00 | {"2023": -581.0, "2024": 2932.0, "2025": 5800.0, "2026": 6840.0} |
| 13 | cdr_400 | xmarket.xmarket_etf.follow_IWM | {"w": 5, "thr": 1.5} | sym15u | both | 7083 | 1912 | 230 | 1.00 | 3 / -740 / -116 / 1.00 | {"2023": 0.0, "2024": -297.0, "2025": 17.0, "2026": 7384.0} |
| 14 | dib_240 | momentum.momentum_libosc.mfi | {"len": 7, "lvl": 15} | plain60/60 | both | 7012 | 3214 | 1869 | 1.00 | 3 / -1892 / 791 / 1.00 | {"2023": -1213.0, "2024": -3373.0, "2025": -4932.0, "2026": 7671.0} |
| 15 | tm15 | trend.trend_macd.signal_native | {"len": 6, "width": 0.0} | asym15u/30u | both | 6996 | 3248 | 564 | 0.50 | 2 / -2597 / -1958 / 1.00 | {"2023": -1259.0, "2024": -199.0, "2025": 1151.0, "2026": 8911.0} |
| 16 | tm15 | trend.trend_macd.signal | {"len": 6, "width": 0.0} | asym15u/30u | both | 6996 | 3248 | 564 | 0.50 | 2 / -382 / 1294 / 1.00 | {"2023": -1259.0, "2024": -199.0, "2025": 1151.0, "2026": 8911.0} |
| 17 | cdr_250 | xmarket.xmarket_mega.revert | {"w": 1, "thr": 1.0} | sym15u | both | 6993 | 3548 | 440 | 1.00 | 3 / -1729 / 3293 / 1.00 | {"2023": 0.0, "2024": -1272.0, "2025": -1217.0, "2026": 7229.0} |
| 18 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.25} | sym15u | both | 6988 | 2980 | 501 | 1.00 | 3 / -493 / 1364 / 1.00 | {"2023": -467.0, "2024": 3516.0, "2025": 6085.0, "2026": 5453.0} |
| 19 | tick_300 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "body"} | sym15u | both | 6921 | 2452 | 481 | 1.00 | 3 / 420 / 1760 / 1.00 | {"2023": 265.0, "2024": -1109.0, "2025": 2152.0, "2026": 7293.0} |
| 20 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | sym8u | both | 6921 | 2747 | 391 | 1.00 | 5 / 0 / 0 / 1.00 | {"2023": 231.0, "2024": 57.0, "2025": -1815.0, "2026": 9448.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -9.8 | -0.004 | 867.7 | 0.51 | -5.9 | 69.9 |  |  |  |  | -15.6 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | 1.3 | 0.003 | 733.2 | 0.53 | 21.4 | 69.9 |  |  |  |  | -20.3 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 32.6 [no null yet] | -9.3 [no null yet] | 12.7 [no null yet] | -16.6 [no null yet] |
| bands (native) | -20.6 [no null yet] | 11.6 [no null yet] | -55.4 [no null yet] | -23.9 [no null yet] |
| barnative | -47.3 [no null yet] | -4.6 [no null yet] | 3.3 [no null yet] | -19.2 [no null yet] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -24.1 [no null yet] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 11.6 [no null yet] | n/a (no signals by construction) |
| confluence | 1.5 [no null yet] | -31.3 [no null yet] | -12.0 [no null yet] | -19.2 [no null yet] |
| levels | -8.7 [no null yet] | -40.5 [no null yet] | 2.9 [no null yet] | 9.4 [no null yet] |
| levels (native) | 19.3 [no null yet] | -11.8 [no null yet] | -21.4 [no null yet] | -31.2 [no null yet] |
| live | -31.3 [no null yet] | -33.5 [no null yet] | -16.9 [no null yet] | -16.8 [no null yet] |
| manual | -26.0 [no null yet] | -27.7 [no null yet] | 16.0 [no null yet] | -12.8 [no null yet] |
| manual (native) | -16.0 [no null yet] | 7.4 [no null yet] | -6.4 [no null yet] | -32.2 [no null yet] |
| momentum | 10.6 [no null yet] | -7.7 [no null yet] | -10.7 [no null yet] | 0.7 [no null yet] |
| momentum (native) | 15.1 [no null yet] | -48.7 [no null yet] | 10.0 [no null yet] | -7.5 [no null yet] |
| pullback | -37.6 [no null yet] | -6.7 [no null yet] | -8.6 [no null yet] | -10.2 [no null yet] |
| pullback (native) | -18.4 [no null yet] | -69.1 [no null yet] | -3.1 [no null yet] | -20.2 [no null yet] |
| structure | 38.0 [no null yet] | -14.0 [no null yet] | 4.5 [no null yet] | 22.5 [no null yet] |
| structure (native) | -27.3 [no null yet] | -5.4 [no null yet] | -7.5 [no null yet] | 23.2 [no null yet] |
| tape | -22.1 [no null yet] | 18.0 [no null yet] | -20.7 [no null yet] | -53.2 [no null yet] |
| tape (native) | -11.1 [no null yet] | -13.7 [no null yet] | 7.7 [no null yet] | -3.7 [no null yet] |
| trend | -18.8 [no null yet] | 19.4 [no null yet] | 10.6 [no null yet] | -9.2 [no null yet] |
| trend (native) | 23.9 [no null yet] | -10.4 [no null yet] | 18.1 [no null yet] | 22.2 [no null yet] |
| xmarket | -16.7 [no null yet] | -31.1 [no null yet] | -16.4 [no null yet] | -5.3 [no null yet] |
### PASS 1: 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| structure|ACTIVITY | 38.0 | 0.019 | 998.7 | 0.54 | 155.9 | 189.5 | {"2023": 5.4, "2024": 22.1, "2025": -24.7, "2026": 141.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|ACTIVITY | 32.6 | 0.026 | 341.2 | 0.52 | 1.5 | -16.3 | {"2023": 10.0, "2024": 5.3, "2025": 88.0, "2026": 6.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend (native)|ACTIVITY | 23.9 | 0.023 | 382.9 | 0.53 | 36.5 | 36.7 | {"2023": -32.1, "2024": 15.8, "2025": 47.9, "2026": 23.0} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 23.2 | 0.022 | 469.8 | 0.58 | 40.4 | -3.8 | {"2023": 49.7, "2024": 5.8, "2025": -1.5, "2026": 64.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|TIME | 22.5 | 0.020 | 875.2 | 0.57 | 127.0 | 175.4 | {"2023": -36.0, "2024": 18.3, "2025": -26.9, "2026": 104.6} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| trend (native)|TIME | 22.2 | 0.006 | 828.0 | 0.53 | 135.2 | 114.7 | {"2023": -78.7, "2024": -22.8, "2025": 74.0, "2026": 46.2} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| trend|INFORMATION | 19.4 | 0.008 | 655.1 | 0.53 | 71.1 | -8.4 | {"2023": 65.3, "2024": 43.0, "2025": -6.0, "2026": 6.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels (native)|ACTIVITY | 19.3 | 0.021 | 781.0 | 0.57 | 118.1 | 124.2 | {"2023": 54.6, "2024": 41.0, "2025": -40.4, "2026": 53.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| trend (native)|PRICE | 18.1 | 0.017 | 739.1 | 0.54 | -34.4 | 11.3 | {"2023": 60.1, "2024": 36.4, "2025": -25.7, "2026": 34.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| tape|INFORMATION | 18.0 | 0.008 | 348.6 | 0.53 | -63.6 | -24.0 | {"2023": 54.3, "2024": -7.7, "2025": 51.0, "2026": -2.3} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
Live books in NYPM on their live bars (same screen, plain 60/60): K7 tm180 L6M -22.5 pts/wk, rank 22% (top 78.3%); M7 tm60 L6M -36.8 pts/wk, rank 13% (top 86.9%); U7 tm600 L6M 4.8 pts/wk, rank 62% (top 38.1%); P7 tm60 L6M -35.9 pts/wk, rank 14% (top 86.5%); H7 tm60 L6M -20.1 pts/wk, rank 24% (top 76.5%); A7 tm60 L6M -32.5 pts/wk, rank 15% (top 84.7%). Rank = share of ALL NYPM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| trend (native)|ACTIVITY | 55.6 | 0.051 | 190.5 | 0.58 | 87.1 | 133.4 | {"2023": 0.1, "2024": 48.1, "2025": 79.2, "2026": 54.0} | -15.1 | 70.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|ACTIVITY | 27.0 | 0.020 | 313.7 | 0.57 | 144.0 | 249.3 | {"2023": 17.1, "2024": -7.7, "2025": 12.0, "2026": 88.7} | 5.6 | 21.3 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| structure|ACTIVITY | 24.5 | 0.025 | 706.3 | 0.54 | 238.6 | 189.5 | {"2023": -30.5, "2024": 24.0, "2025": -13.6, "2026": 87.5} | -12.2 | 36.6 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| structure|TIME | 23.9 | 0.023 | 538.1 | 0.56 | 7.2 | 147.4 | {"2023": 23.8, "2024": 51.0, "2025": -11.6, "2026": 33.8} | 1.2 | 22.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels|ACTIVITY | 23.6 | 0.022 | 296.2 | 0.59 | 62.1 | 26.4 | {"2023": 5.0, "2024": -2.8, "2025": 37.6, "2026": 44.4} | -7.1 | 30.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| barnative|INFORMATION | 20.2 | 0.017 | 411.1 | 0.49 | 85.3 | 70.8 | {"2023": -16.9, "2024": -15.0, "2025": 49.6, "2026": 38.7} | -51.8 | 72.0 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| bands|INFORMATION | 20.0 | 0.007 | 851.1 | 0.52 | 96.5 | 47.8 | {"2023": 55.5, "2024": 9.9, "2025": -42.5, "2026": 94.7} | -14.2 | 34.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels (native)|INFORMATION | 19.2 | 0.027 | 244.4 | 0.60 | 23.4 | 47.0 | {"2023": 1.4, "2024": 31.4, "2025": 19.9, "2026": 9.5} | -4.1 | 23.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|PRICE | 19.0 | 0.012 | 500.2 | 0.60 | 20.8 | 127.0 | {"2023": 5.7, "2024": 33.8, "2025": -3.8, "2026": 32.5} | -27.4 | 46.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "AMBER", "2026": "ok"} |
| levels (native)|TIME | 17.0 | 0.024 | 454.9 | 0.51 | 85.7 | -35.8 | {"2023": -59.3, "2024": 12.0, "2025": 11.3, "2026": 54.0} | -18.1 | 35.1 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | plain60/60 | both | 6993 | 1620 | 1029 | 0.50 | 0 /  /  /  | {"2023": 627.0, "2024": 603.0, "2025": -1983.0, "2026": 6898.0} |
| 2 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym15u | both | 6729 | 2188 | 270 | 1.00 | 0 /  /  /  | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 3 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | sym15u | both | 6039 | 2351 | 303 | 1.00 | 0 /  /  /  | {"2023": -93.0, "2024": 1981.0, "2025": -1045.0, "2026": 6138.0} |
| 4 | tm10 | tape.tape_vpin.follow | {"N": 25, "thr": 0.08} | plain60/60 | both | 5867 | 1722 | 855 | 1.00 | 1 / -1356 / -1356 / 1.00 | {"2023": -61.0, "2024": -81.0, "2025": -154.0, "2026": 5010.0} |
| 5 | tm10 | tape.tape_vpin.follow | {"N": 25, "thr": 0.12} | plain60/60 | both | 5838 | 2593 | 867 | 1.00 | 1 / 0 / 0 / 1.00 | {"2023": 500.0, "2024": 1370.0, "2025": 392.0, "2026": 4266.0} |
| 6 | renko_20 | structure.structure_level.round_break | {"grid": 100, "buf": 0.25} | sym15u | both | 5790 | 1514 | 285 | 0.83 | 2 / -949 / -321 / 1.00 | {"2023": -1814.0, "2024": 1098.0, "2025": -3217.0, "2026": 7515.0} |
| 7 | renko_20 | structure.structure_level.round_break | {"grid": 100, "buf": 0.25} | sym30u | both | 5790 | 1514 | 285 | 0.83 | 2 / -949 / -321 / 1.00 | {"2023": -1121.0, "2024": 1056.0, "2025": -2117.0, "2026": 7515.0} |
| 8 | renko_20 | structure.structure_level.round_break | {"grid": 100, "buf": 0.25} | asym15u/30u | both | 5790 | 1514 | 285 | 0.83 | 2 / -949 / -321 / 1.00 | {"2023": -1021.0, "2024": 490.0, "2025": -2330.0, "2026": 7515.0} |
| 9 | tm10 | tape.tape_vpin.follow | {"N": 25, "thr": 0.05} | plain60/60 | both | 5699 | 1614 | 855 | 1.00 | 1 / 0 / 0 / 1.00 | {"2023": -52.0, "2024": -38.0, "2025": 410.0, "2026": 4841.0} |
| 10 | vol_2600 | trend.trend_macd.hist_turn | {"len": 6, "width": 0.0} | sym15u | both | 5696 | 2761 | 331 | 1.00 | 0 /  /  /  | {"2023": -1592.0, "2024": 1832.0, "2025": 1475.0, "2026": 5233.0} |
| 11 | tick_1300 | momentum.momentum_roc.break_native | {"len": 5, "wd": 0.5} | sym15u | both | 5667 | 2136 | 329 | 1.00 | 0 /  /  /  | {"2023": 31.0, "2024": -1701.0, "2025": 174.0, "2026": 6932.0} |
| 12 | tm15 | momentum.momentum_squeeze.hist_turn | {"len": 14, "wd": 3} | plain60/60 | both | 5653 | 3197 | 968 | 1.00 | 2 / 196 / 1584 / 1.00 | {"2023": 364.0, "2024": -1006.0, "2025": 110.0, "2026": 6376.0} |
| 13 | tm15 | momentum.momentum_squeeze.hist_turn_native | {"len": 14, "wd": 3} | plain60/60 | both | 5653 | 3197 | 968 | 1.00 | 2 / 812 / 1078 / 1.00 | {"2023": 364.0, "2024": -1006.0, "2025": 110.0, "2026": 6376.0} |
| 14 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym20u/10u | both | 5651 | 1260 | 278 | 1.00 | 2 / -131 / 1685 / 1.00 | {"2023": -448.0, "2024": 3799.0, "2025": 1764.0, "2026": 5365.0} |
| 15 | vsess_300 | manual.manual_cci.go | {"len": 14, "lvl": 100} | sym15u | both | 5566 | 695 | 338 | 0.50 | 0 /  /  /  | {"2023": -1509.0, "2024": -1137.0, "2025": -1791.0, "2026": 5512.0} |
| 16 | time_s_5 | structure.structure_libpattern.pin | {"k": 2.0, "filt": 0} | plain60/60 | both | 5554 | 2258 | 1029 | 0.50 | 2 / 1681 / 2673 / 1.00 | {"2023": 814.0, "2024": -1934.0, "2025": 3639.0, "2026": 5009.0} |
| 17 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | sym30u | both | 5547 | 1156 | 276 | 1.00 | 2 / -131 / 1685 / 1.00 | {"2023": -571.0, "2024": 3918.0, "2025": 1587.0, "2026": 5256.0} |
| 18 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym15u/30u | both | 5547 | 1156 | 276 | 1.00 | 2 / -131 / 1685 / 1.00 | {"2023": -554.0, "2024": 3950.0, "2025": 1587.0, "2026": 5256.0} |
| 19 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | sym15u | both | 5547 | 1156 | 276 | 1.00 | 2 / -131 / 1685 / 1.00 | {"2023": -299.0, "2024": 3950.0, "2025": 1587.0, "2026": 5256.0} |
| 20 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym10u/20u | both | 5547 | 1156 | 276 | 1.00 | 2 / -134 / 1685 / 1.00 | {"2023": -380.0, "2024": 3758.0, "2025": 1738.0, "2026": 5306.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -14.4 | -0.024 | 1188.7 | 0.53 | -22.5 | -82.2 |  |  |  |  | 7.7 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -10.6 | -0.018 | 1000.9 | 0.56 | -22.5 | -82.2 |  |  |  |  | 10.3 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 15.1 [no null yet] | 29.5 [no null yet] | 18.8 [no null yet] | 9.7 [no null yet] |
| bands (native) | -8.3 [no null yet] | 11.7 [no null yet] | 35.9 [no null yet] | 7.9 [no null yet] |
| barnative | 6.1 [no null yet] | -8.3 [no null yet] | 0.4 [no null yet] | -21.6 [no null yet] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -16.6 [no null yet] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 6.5 [no null yet] | n/a (no signals by construction) |
| confluence | 9.0 [no null yet] | 2.0 [no null yet] | 1.7 [no null yet] | -3.8 [no null yet] |
| levels | 24.5 [no null yet] | -15.0 [no null yet] | 11.6 [no null yet] | -4.0 [no null yet] |
| levels (native) | 24.0 [no null yet] | 24.5 [no null yet] | -0.5 [no null yet] | 11.0 [no null yet] |
| live | 17.0 [no null yet] | -4.1 [no null yet] | 14.0 [no null yet] | 11.7 [no null yet] |
| manual | 10.2 [no null yet] | 3.5 [no null yet] | 5.0 [no null yet] | -36.0 [no null yet] |
| manual (native) | 12.5 [no null yet] | -24.2 [no null yet] | -13.5 [no null yet] | 10.8 [no null yet] |
| momentum | 12.7 [no null yet] | 10.3 [no null yet] | 11.8 [no null yet] | -8.1 [no null yet] |
| momentum (native) | -9.2 [no null yet] | 3.0 [no null yet] | 7.7 [no null yet] | -9.5 [no null yet] |
| pullback | 23.0 [no null yet] | 34.2 [no null yet] | -19.6 [no null yet] | -4.4 [no null yet] |
| pullback (native) | 21.5 [no null yet] | -1.1 [no null yet] | 24.0 [no null yet] | -8.8 [no null yet] |
| structure | 7.5 [no null yet] | 28.1 [no null yet] | 18.0 [no null yet] | 2.3 [no null yet] |
| structure (native) | 1.6 [no null yet] | -14.0 [no null yet] | 17.5 [no null yet] | -10.3 [no null yet] |
| tape | -12.9 [no null yet] | -0.4 [no null yet] | 1.4 [no null yet] | 14.8 [no null yet] |
| tape (native) | -14.0 [no null yet] | -7.3 [no null yet] | -12.1 [no null yet] | -3.9 [no null yet] |
| trend | 16.3 [no null yet] | 34.2 [no null yet] | 26.4 [no null yet] | 18.5 [no null yet] |
| trend (native) | -4.2 [no null yet] | 13.8 [no null yet] | -12.0 [no null yet] | -4.2 [no null yet] |
| xmarket | -6.1 [no null yet] | -9.9 [no null yet] | -26.1 [no null yet] | -4.1 [no null yet] |
### PASS 1: 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bands (native)|PRICE | 35.9 | 0.033 | 208.5 | 0.58 | 9.5 | -17.4 | {"2023": 29.4, "2024": 0.6, "2025": 63.7, "2026": 46.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|INFORMATION | 34.2 | 0.031 | 142.3 | 0.62 | 63.5 | 9.4 | {"2023": 37.4, "2024": 19.8, "2025": 36.0, "2026": 48.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|INFORMATION | 34.2 | 0.035 | 151.4 | 0.57 | 57.8 | -27.2 | {"2023": 22.9, "2024": 35.8, "2025": 41.1, "2026": 27.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|INFORMATION | 29.5 | 0.039 | 279.9 | 0.59 | 121.6 | 25.2 | {"2023": 16.8, "2024": 22.2, "2025": 10.6, "2026": 64.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION | 28.1 | 0.025 | 214.7 | 0.53 | 106.7 | 56.1 | {"2023": 34.0, "2024": 1.3, "2025": 17.9, "2026": 70.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|PRICE | 26.4 | 0.023 | 393.2 | 0.59 | -18.4 | 6.4 | {"2023": 9.4, "2024": 32.7, "2025": 77.1, "2026": -35.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| levels (native)|INFORMATION | 24.5 | 0.034 | 350.0 | 0.60 | 107.2 | 115.9 | {"2023": 36.1, "2024": 26.9, "2025": -13.3, "2026": 62.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels|ACTIVITY | 24.5 | 0.025 | 162.5 | 0.54 | 60.9 | 33.1 | {"2023": -8.8, "2024": -14.0, "2025": 54.3, "2026": 45.3} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| pullback (native)|PRICE | 24.0 | 0.022 | 357.7 | 0.54 | -63.6 | -12.0 | {"2023": 19.9, "2024": 32.6, "2025": 31.2, "2026": 6.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|ACTIVITY | 24.0 | 0.028 | 177.7 | 0.58 | -4.8 | 45.0 | {"2023": 0.7, "2024": -5.9, "2025": 77.1, "2026": 4.0} |  |  |  | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
Live books in Asia on their live bars (same screen, plain 60/60): K7 tm180 L6M 72.1 pts/wk, rank 98% (top 1.7%); M7 tm60 L6M 80.8 pts/wk, rank 99% (top 1.1%); U7 tm600 L6M 35.4 pts/wk, rank 91% (top 9.4%); P7 tm60 L6M 66.1 pts/wk, rank 98% (top 2.3%); H7 tm60 L6M 25.1 pts/wk, rank 85% (top 14.9%); A7 tm60 L6M 6.5 pts/wk, rank 65% (top 34.6%). Rank = share of ALL Asia cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum (native)|PRICE | 39.8 | 0.069 | 161.1 | 0.64 | 42.8 | 5.0 | {"2023": 7.1, "2024": 45.2, "2025": 45.9, "2026": 36.6} | -23.0 | 62.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|ACTIVITY | 36.2 | 0.055 | 180.7 | 0.64 | 67.4 | 9.2 | {"2023": 32.8, "2024": 45.1, "2025": 29.4, "2026": 34.7} | 1.9 | 34.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|INFORMATION | 28.2 | 0.039 | 167.6 | 0.60 | 38.1 | -18.9 | {"2023": 28.8, "2024": 21.6, "2025": 25.5, "2026": 39.0} | -0.5 | 28.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|PRICE | 25.0 | 0.024 | 167.1 | 0.53 | -3.0 | -12.0 | {"2023": 17.0, "2024": 30.9, "2025": 11.6, "2026": 36.2} | 0.7 | 24.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|PRICE | 24.4 | 0.033 | 208.9 | 0.57 | 32.2 | -3.6 | {"2023": -5.6, "2024": -2.1, "2025": 58.7, "2026": 24.8} | -3.7 | 28.1 | 1.00 | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|ACTIVITY | 24.1 | 0.006 | 220.6 | 0.56 | 21.3 | -156.7 | {"2023": -8.5, "2024": 8.9, "2025": 36.7, "2026": 37.5} | -23.0 | 47.1 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|INFORMATION | 22.5 | 0.022 | 153.7 | 0.59 | 31.7 | -2.2 | {"2023": 33.5, "2024": 24.0, "2025": 6.8, "2026": 35.5} | -19.9 | 42.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 18.7 | 0.023 | 272.1 | 0.57 | -53.7 | -79.2 | {"2023": -7.0, "2024": 12.7, "2025": 50.7, "2026": -4.0} | -4.7 | 23.3 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| levels|PRICE | 17.1 | 0.021 | 203.3 | 0.53 | 10.7 | 7.8 | {"2023": 1.3, "2024": 16.5, "2025": 25.9, "2026": 12.3} | -0.1 | 17.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|PRICE | 16.6 | 0.010 | 314.2 | 0.58 | 34.9 | -33.3 | {"2023": 4.0, "2024": 7.9, "2025": 49.8, "2026": -8.2} | -10.6 | 27.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | drb_240 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.01} | sym15u | both | 6751 | 922 | 421 | 1.00 | 0 /  /  /  | {"2023": -77.0, "2024": -853.0, "2025": 1402.0, "2026": 4274.0} |
| 2 | urenko_14 | book.book_pslope.follow_native | {"L": 900, "z": 1.0} | plain60/60 | both | 6194 | 2575 | 1058 | 1.00 | 2 / -1366 / -13 / 1.00 | {"2023": 241.0, "2024": -762.0, "2025": -4489.0, "2026": 6137.0} |
| 3 | dib_1200 | trend.trend_libstack.ema_hold | {"len": 21, "hold": 5} | plain60/60 | both | 6002 | 2374 | 888 | 1.00 | 0 /  /  /  | {"2023": -602.0, "2024": 1979.0, "2025": 1051.0, "2026": 7294.0} |
| 4 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym15u | both | 5982 | 1769 | 272 | 0.50 | 0 /  /  /  | {"2023": -120.0, "2024": -2395.0, "2025": 2657.0, "2026": 5184.0} |
| 5 | time_m_1 | tape.tape_delta.cvd_follow | {"N": 5, "L": 100, "z": 1.0} | plain60/60 | both | 5956 | 1226 | 852 | 1.00 | 2 / -1153 / -417 / 1.00 | {"2023": -796.0, "2024": -290.0, "2025": -494.0, "2026": 5824.0} |
| 6 | renko_10 | tape.tape_vpin.follow | {"N": 10, "thr": 0.05} | asym10u/20u | both | 5955 | 2993 | 541 | 1.00 | 2 / -217 / 336 / 1.00 | {"2023": -1003.0, "2024": -585.0, "2025": 1260.0, "2026": 4197.0} |
| 7 | tm45 | manual.manual_macd.zero_native | {"f": 2, "s": 5, "g": 2} | sym30u | both | 5884 | 2017 | 357 | 1.00 | 2 / 1356 / 2344 / 1.00 | {"2023": -647.0, "2024": 82.0, "2025": 524.0, "2026": 3926.0} |
| 8 | dib_2000 | tape.tape_speed.follow | {"f": 3.0, "L": 200} | sym15u | both | 5833 | 2608 | 339 | 1.00 | 0 /  /  /  | {"2023": -2.0, "2024": 863.0, "2025": -1813.0, "2026": 5362.0} |
| 9 | tm20 | manual.manual_macd.sigcross_native | {"f": 20, "s": 45, "g": 15} | asym10u/20u | both | 5719 | 1587 | 574 | 1.00 | 2 / 23 / 70 / 1.00 | {"2023": -1181.0, "2024": 209.0, "2025": -471.0, "2026": 4530.0} |
| 10 | dib_700 | trend.trend_ma_hma.price | {"len": 25, "width": 0.0} | sym15u | both | 5667 | 2294 | 509 | 1.00 | 0 /  /  /  | {"2023": -142.0, "2024": -2173.0, "2025": -1421.0, "2026": 3380.0} |
| 11 | cusum_14 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5664 | 2189 | 259 | 1.00 | 0 /  /  /  | {"2023": 67.0, "2024": 4.0, "2025": -885.0, "2026": 4943.0} |
| 12 | dib_700 | trend.trend_ma_hma.price | {"len": 9, "width": 0.0} | sym15u | both | 5559 | 2206 | 524 | 1.00 | 0 /  /  /  | {"2023": -188.0, "2024": -434.0, "2025": 455.0, "2026": 2505.0} |
| 13 | time_m_1 | momentum.momentum_stoch.revert | {"len": 5, "lvl": 15} | sym30u | both | 5558 | 3969 | 372 | 1.00 | 2 / 1592 / 3989 / 1.00 | {"2023": -447.0, "2024": -241.0, "2025": -1538.0, "2026": 4926.0} |
| 14 | time_m_1 | momentum.momentum_stoch.revert_native | {"len": 5, "lvl": 15} | sym30u | both | 5558 | 3969 | 372 | 1.00 | 2 / -908 / -429 / 1.00 | {"2023": -447.0, "2024": -241.0, "2025": -1538.0, "2026": 4926.0} |
| 15 | vsess_600 | trend.trend_ma_hma.cross_native | {"len": 21, "width": 0.25, "ratio": 3} | sym15u | both | 5549 | 1933 | 385 | 1.00 | 0 /  /  /  | {"2023": -472.0, "2024": -2419.0, "2025": -726.0, "2026": 5219.0} |
| 16 | time_m_1 | bands.bands_regchan.fade_stderr_native | {"clk": 5, "k": 1.5} | asym10u/20u | both | 5475 | 2410 | 481 | 1.00 | 5 / 407 / 2073 / 1.00 | {"2023": 576.0, "2024": -1904.0, "2025": -3365.0, "2026": 2611.0} |
| 17 | tib_240 | tape.tape_vpin.follow_native | {"N": 600, "thr": 0.05} | sym15u | both | 5466 | 2289 | 678 | 1.00 | 0 /  /  /  | {"2023": -793.0, "2024": -1657.0, "2025": -3030.0, "2026": 5169.0} |
| 18 | vol_350 | tape.tape_speed.follow_native | {"f": 1.5, "L": 900} | sym15u | both | 5460 | 871 | 357 | 1.00 | 0 /  /  /  | {"2023": -107.0, "2024": 2600.0, "2025": 1886.0, "2026": 4406.0} |
| 19 | rng_10 | tape.tape_vpin.follow | {"N": 50, "thr": 0.12} | sym15u | both | 5428 | 1948 | 472 | 0.67 | 2 / -580 / -523 / 1.00 | {"2023": -1240.0, "2024": -1766.0, "2025": -2658.0, "2026": 5060.0} |
| 20 | cusum_40 | xmarket.xmarket_ym.follow | {"w": 1, "thr": 1.0} | sym15u | both | 5396 | 1872 | 313 | 1.00 | 0 /  /  /  | {"2023": -565.0, "2024": -544.0, "2025": 2542.0, "2026": 3380.0} |

## Baseline: the seven live triggers on their live bars (same screen: plain 60/60 bracket, tape fills, measured slippage, $4.84, flat at session end, 1 lot; pts per week)
Live bar per book used here: EXACT live bars: K7 tm180 (3-min), M7 tm60 (1-min), U7 tm600 (10-min), P7 / H7 / A7 / O7 tm60 (engine 1-min bars per W-SWB fidelity); the two time rows either side of each live row are shown as neighbour; weak cells flagged. This is a TRIGGER baseline: no layers, no confluence/conditions.
| session | book | row | kind | L6M pts/wk | L3M pts/wk | since 2023-10 pts/wk | ulcer (wk pts) | persistence | trades L6M | rank (share of all session cells with lower L6M) | weak cell |
|---|---|---|---|---|---|---|---|---|---|---|
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.05 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.98 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.07 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.40 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.11 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.09 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.85 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.85 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.03 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.61 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.33 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.02 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.80 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.79 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.26 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 0.99 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 1.00 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.95 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.90 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.62 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.57 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.28 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.63 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.57 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.80 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.18 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.16 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.84 |  |
| London | A7 | tm180 | neighbour | 12.1 | -7.9 | 6.2 | 280.0 | 0.52 | 185 | 0.78 |  |
| NYAM | K7 | tm180 | LIVE | -75.5 | -76.7 | -13.6 | 2327.5 | 0.49 | 509 | 0.05 | WEAK |
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.16 | WEAK |
| NYAM | K7 | tm120 | neighbour | -30.0 | -123.0 | -10.5 | 1468.1 | 0.49 | 643 | 0.22 | WEAK |
| NYAM | K7 | tm240 | neighbour | -79.8 | -92.5 | -9.8 | 1102.8 | 0.47 | 407 | 0.05 | WEAK |
| NYAM | K7 | tm300 | neighbour | 15.3 | 65.7 | 15.3 | 614.4 | 0.56 | 353 | 0.79 | WEAK |
| NYAM | M7 | tm60 | LIVE | -8.9 | -62.9 | 8.8 | 799.6 | 0.49 | 469 | 0.43 | WEAK |
| NYAM | M7 | tm30 | neighbour | -80.7 | -67.0 | -11.3 | 1320.0 | 0.48 | 691 | 0.04 | WEAK |
| NYAM | M7 | tm45 | neighbour | -56.7 | -96.2 | 4.9 | 873.5 | 0.57 | 550 | 0.10 | WEAK |
| NYAM | M7 | tm120 | neighbour | -59.2 | -52.4 | -4.9 | 928.0 | 0.48 | 350 | 0.09 | WEAK |
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.44 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.39 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.39 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.56 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.71 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.43 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.08 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.01 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.04 | WEAK |
| NYAM | P7 | tm120 | neighbour | -83.3 | -108.9 | -8.8 | 1172.0 | 0.47 | 360 | 0.04 | WEAK |
| NYAM | P7 | tm180 | neighbour | -58.3 | -110.6 | -12.9 | 1064.8 | 0.51 | 297 | 0.09 | WEAK |
| NYAM | H7 | tm60 | LIVE | 28.8 | 20.1 | 6.1 | 506.0 | 0.48 | 86 | 0.88 | WEAK |
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.89 | WEAK |
| NYAM | H7 | tm45 | neighbour | 13.9 | 13.9 | -3.7 | 932.6 | 0.51 | 87 | 0.78 | WEAK |
| NYAM | H7 | tm120 | neighbour | 32.4 | 23.7 | 9.9 | 457.8 | 0.51 | 80 | 0.90 | WEAK |
| NYAM | H7 | tm180 | neighbour | 1.7 | 43.8 | 3.6 | 360.5 | 0.49 | 76 | 0.62 | WEAK |
| NYAM | A7 | tm60 | LIVE | -17.2 | 3.9 | -1.6 | 946.9 | 0.46 | 241 | 0.33 |  |
| NYAM | A7 | tm30 | neighbour | -52.8 | -39.6 | -10.3 | 971.6 | 0.49 | 382 | 0.11 |  |
| NYAM | A7 | tm45 | neighbour | -39.4 | -34.4 | -12.0 | 1445.4 | 0.49 | 299 | 0.17 |  |
| NYAM | A7 | tm120 | neighbour | 16.1 | 37.4 | 2.8 | 451.4 | 0.38 | 116 | 0.80 |  |
| NYAM | A7 | tm180 | neighbour | 11.4 | 8.0 | -0.0 | 509.3 | 0.47 | 85 | 0.75 |  |
| NYAM | O7 | tm60 | LIVE | 15.1 | 12.8 | 16.7 | 224.3 | 0.52 | 61 | 0.79 |  |
| NYAM | O7 | tm30 | neighbour | 8.0 | 17.4 | 16.2 | 173.8 | 0.51 | 64 | 0.72 |  |
| NYAM | O7 | tm45 | neighbour | 15.0 | 8.2 | 17.0 | 147.8 | 0.53 | 63 | 0.79 |  |
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.36 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.31 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.22 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.03 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.85 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.16 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.06 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.13 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.21 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.27 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.81 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.16 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.62 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.31 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.70 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.24 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.31 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.14 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.06 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.10 |  |
| NYPM | P7 | tm120 | neighbour | -23.9 | -61.9 | -4.2 | 1017.5 | 0.48 | 334 | 0.21 |  |
| NYPM | P7 | tm180 | neighbour | -38.7 | -76.0 | -17.9 | 1375.5 | 0.49 | 251 | 0.12 |  |
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.24 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.24 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.49 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.26 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.61 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.15 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.13 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.09 |  |
| NYPM | A7 | tm120 | neighbour | -14.8 | -5.5 | -13.2 | 1971.7 | 0.49 | 133 | 0.28 |  |
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.59 |  |
| Asia | K7 | tm180 | LIVE | 72.1 | 61.6 | 11.3 | 978.2 | 0.56 | 683 | 0.98 |  |
| Asia | K7 | tm60 | neighbour | 82.2 | -34.7 | 23.8 | 585.9 | 0.57 | 896 | 0.99 |  |
| Asia | K7 | tm120 | neighbour | 98.9 | 36.5 | 26.2 | 556.4 | 0.56 | 759 | 1.00 |  |
| Asia | K7 | tm240 | neighbour | 115.3 | 117.7 | 38.9 | 543.2 | 0.65 | 635 | 1.00 |  |
| Asia | K7 | tm300 | neighbour | 97.3 | 106.9 | 35.3 | 360.3 | 0.60 | 570 | 0.99 |  |
| Asia | M7 | tm60 | LIVE | 80.8 | 126.3 | 38.6 | 423.4 | 0.63 | 593 | 0.99 |  |
| Asia | M7 | tm30 | neighbour | 90.3 | 89.8 | 35.0 | 444.9 | 0.65 | 795 | 0.99 |  |
| Asia | M7 | tm45 | neighbour | 49.4 | 102.7 | 29.0 | 480.3 | 0.65 | 697 | 0.95 |  |
| Asia | M7 | tm120 | neighbour | 130.5 | 160.7 | 34.4 | 344.2 | 0.59 | 438 | 1.00 |  |
| Asia | M7 | tm180 | neighbour | 50.4 | 113.2 | 25.0 | 304.0 | 0.59 | 339 | 0.95 |  |
| Asia | U7 | tm600 | LIVE | 35.4 | 16.8 | 13.8 | 169.9 | 0.64 | 153 | 0.91 |  |
| Asia | U7 | tm300 | neighbour | -6.4 | -26.1 | 8.6 | 258.9 | 0.56 | 274 | 0.37 |  |
| Asia | U7 | tm420 | neighbour | 32.2 | 35.3 | 11.1 | 206.8 | 0.59 | 216 | 0.89 |  |
| Asia | U7 | tm780 | neighbour | -39.7 | -29.7 | 2.1 | 400.0 | 0.52 | 119 | 0.10 |  |
| Asia | U7 | tm900 | neighbour | -19.1 | 18.1 | 4.1 | 252.7 | 0.56 | 100 | 0.23 |  |
| Asia | P7 | tm60 | LIVE | 66.1 | 109.3 | 25.7 | 292.4 | 0.60 | 658 | 0.98 |  |
| Asia | P7 | tm30 | neighbour | 41.5 | 67.2 | 13.3 | 602.1 | 0.54 | 799 | 0.93 |  |
| Asia | P7 | tm45 | neighbour | 79.5 | 72.1 | 12.5 | 826.8 | 0.53 | 705 | 0.99 |  |
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.46 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.13 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.85 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.87 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.88 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.93 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.95 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.65 |  |
| Asia | A7 | tm30 | neighbour | -4.3 | -2.8 | 24.3 | 313.1 | 0.57 | 415 | 0.41 |  |
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.30 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.83 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.90 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell renko_14 levels.levels_vwap.break_native sym15u L6M 220.7 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell swing_atr_0.1 tape.tape_speed.follow_native sym15u L6M 313.2 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell dib_2000 barnative.barnative_speed.burst_fade plain60/60 L6M 269.0 pts/wk vs weak baselines K7 -22.5
