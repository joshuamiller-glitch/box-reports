# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-18 02:32Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**CORRECTION 02:30Z (read first): every random-entry null file produced by the fast path before 02:30Z was an exact COPY of the real result (the fast runner did not recognise the tag p1randN), so all earlier excess / percentile / null columns and the claim of null draws were INVALID (excess 0.0, percentile 1.00 = no null). 31,413 such files were deleted; the 1,411 legacy-runner null files are valid. Nulls are being regenerated; a null column is shown only when the null pool covers >= 80% of the real pool, otherwise it reads NO NULL YET. Real results are unaffected.**

**NULL AUDIT (assertions: a null file must differ from its real file; null mean pts/trade at plain 60/60 must be negative and above -6; a tag failing is rejected and its columns read NO NULL YET):**
| null tag | files | sampled | identical to real | mean pts/trade London / NYAM / NYPM / Asia | accepted | share of real cells covered (per session) | note |
|---|---|---|---|---|---|---|---|
| p1rand1 | 941 | 400 | 0.000 | -0.64 / -0.48 / -0.50 / -1.12 | YES | {"London": null, "NYAM": null} |  |
| p1rand2 | 905 | 400 | 0.000 | -0.69 / -0.48 / -0.54 / -1.13 | YES | {"London": null, "NYAM": null} |  |
Draws per cell = number of accepted null tags covering the pool (see per-session null_cover); needs >= 5 before any LEAD label.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-18 02:32Z):** result files per tag {"p1rand1": 2766, "p1rand2": 2771, "p1real": 17856, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, INFORMATION, PRICE, TIME; null draws per cell (random-entry replicas in the scored sessions): {"London": 0, "NYAM": 0}; live-seven baseline: IN (65 rows). Sessions published: London, NYAM (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-18 02:32Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"p1rand1": 2766, "p1rand2": 2771, "p1real": 17856, "rand1": 0, "real": 1654}; loop status: 2026-11-18T02:08Z rows=322 mods=116 todo=83919 running=0. 
Cells scored per session: {"London": 1459100, "NYAM": 1575182}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -30.3 | -0.029 | 1161.1 | 0.48 | -113.8 | -106.3 |  |  |  |  | -28.3 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -29.7 | -0.022 | 1167.0 | 0.51 | -122.5 | -42.2 |  |  |  |  | -21.3 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -25.2 [no null yet] | -36.3 [no null yet] | -35.6 [no null yet] | 7.8 [no null yet] |
| bands (native) | -3.1 [no null yet] | 0.2 [no null yet] | 1.0 [no null yet] | -26.0 [no null yet] |
| barnative | -18.1 [no null yet] | 10.4 [no null yet] | -11.9 [no null yet] | -28.4 [no null yet] |
| confluence | -17.7 [no null yet] | -26.6 [no null yet] | 1.3 [no null yet] | -5.1 [no null yet] |
| levels | -20.2 [no null yet] | -25.9 [no null yet] | 6.9 [no null yet] | -26.8 [no null yet] |
| levels (native) | -8.5 [no null yet] | -3.2 [no null yet] | -15.2 [no null yet] | -13.9 [no null yet] |
| live | -1.4 [no null yet] | -16.9 [no null yet] | -8.3 [no null yet] | 6.3 [no null yet] |
| manual | -34.8 [no null yet] | -5.2 [no null yet] | -36.3 [no null yet] | -23.8 [no null yet] |
| manual (native) | 13.4 [no null yet] | -30.5 [no null yet] | -5.3 [no null yet] | -13.8 [no null yet] |
| momentum | -16.1 [no null yet] | 16.9 [no null yet] | -27.3 [no null yet] | -2.1 [no null yet] |
| momentum (native) | -31.2 [no null yet] | -23.6 [no null yet] | -18.0 [no null yet] | -19.6 [no null yet] |
| pullback | -8.3 [no null yet] | -9.2 [no null yet] | -11.4 [no null yet] | -16.1 [no null yet] |
| pullback (native) | -19.8 [no null yet] | -0.1 [no null yet] | -4.3 [no null yet] | -37.8 [no null yet] |
| structure | 5.2 [no null yet] | -18.0 [no null yet] | -24.4 [no null yet] | -20.1 [no null yet] |
| structure (native) | -5.4 [no null yet] | -21.0 [no null yet] | -20.2 [no null yet] | -33.3 [no null yet] |
| tape | -11.7 [no null yet] | 5.4 [no null yet] | -13.9 [no null yet] | -33.8 [no null yet] |
| tape (native) | 12.7 [no null yet] | 3.9 [no null yet] | 17.5 [no null yet] | -28.7 [no null yet] |
| trend | -31.0 [no null yet] | -21.6 [no null yet] | -13.2 [no null yet] | -13.7 [no null yet] |
| trend (native) | -14.2 [no null yet] | -12.5 [no null yet] | 1.5 [no null yet] | -0.4 [no null yet] |
| xmarket | 2.3 [no null yet] | 6.0 [no null yet] | -15.2 [no null yet] | 5.3 [no null yet] |
### PASS 1: 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| tape (native)|PRICE | 17.5 | 0.009 | 644.7 | 0.49 | 53.7 | -47.9 | {"2023": -20.2, "2024": 4.2, "2025": -29.9, "2026": 101.3} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| momentum|INFORMATION | 16.9 | 0.028 | 254.9 | 0.53 | 3.5 | -50.4 | {"2023": -15.5, "2024": 50.5, "2025": -8.6, "2026": 17.8} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| manual (native)|ACTIVITY | 13.4 | 0.010 | 396.2 | 0.51 | 57.2 | 21.3 | {"2023": -40.5, "2024": 28.5, "2025": -3.3, "2026": 32.5} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "AMBER", "2026": "ok"} |
| tape (native)|ACTIVITY | 12.7 | 0.007 | 352.8 | 0.48 | 35.0 | -11.3 | {"2023": -32.3, "2024": -11.5, "2025": 17.7, "2026": 49.7} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| barnative|INFORMATION | 10.4 | 0.008 | 682.8 | 0.53 | 61.9 | 76.1 | {"2023": 29.5, "2024": 27.9, "2025": -17.3, "2026": 16.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|TIME | 7.8 | 0.003 | 550.7 | 0.48 | 56.9 | 18.6 | {"2023": -30.1, "2024": -29.8, "2025": 1.5, "2026": 71.6} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| levels|PRICE | 6.9 | 0.008 | 552.0 | 0.53 | 49.5 | 126.7 | {"2023": 12.5, "2024": 2.2, "2025": -32.2, "2026": 56.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| live|TIME | 6.3 | 0.006 | 538.3 | 0.54 | 81.1 | 29.7 | {"2023": -30.4, "2024": -12.7, "2025": -14.9, "2026": 65.7} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| xmarket|INFORMATION | 6.0 | 0.008 | 354.7 | 0.57 | 11.5 | 78.7 | {"2023": -5.3, "2024": 19.1, "2025": 5.5, "2026": -5.4} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| tape|INFORMATION | 5.4 | 0.004 | 670.0 | 0.54 | 85.2 | 71.8 | {"2023": 9.2, "2024": 3.7, "2025": -16.6, "2026": 32.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
Live books in London on their live bars (same screen, plain 60/60): K7 tm180 L6M -52.7 pts/wk, rank 5% (top 95.3%); M7 tm60 L6M -39.6 pts/wk, rank 9% (top 91.3%); U7 tm600 L6M -10.7 pts/wk, rank 32% (top 67.7%); P7 tm60 L6M 65.6 pts/wk, rank 99% (top 0.9%); H7 tm60 L6M 2.9 pts/wk, rank 63% (top 37.3%); A7 tm60 L6M 14.3 pts/wk, rank 81% (top 19.2%). Rank = share of ALL London cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| xmarket|TIME | 14.6 | 0.022 | 358.0 | 0.60 | 20.4 | 55.5 | {"2023": 15.3, "2024": 26.1, "2025": 5.9, "2026": 10.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|TIME | 6.1 | 0.008 | 228.6 | 0.51 | -22.7 | 25.9 | {"2023": -17.9, "2024": -5.9, "2025": 30.1, "2026": -0.5} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| bands|TIME | 1.9 | 0.003 | 871.4 | 0.47 | 63.7 | 18.6 | {"2023": -18.4, "2024": -47.1, "2025": -6.0, "2026": 75.6} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| confluence|TIME | -8.9 | -0.017 | 823.8 | 0.46 | 4.4 | -6.6 | {"2023": -67.1, "2024": 16.0, "2025": -27.5, "2026": 2.1} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| momentum|TIME | -9.5 | -0.003 | 466.0 | 0.49 | -84.5 | -207.3 | {"2023": -6.6, "2024": 23.2, "2025": 0.1, "2026": -60.4} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| barnative|TIME | -14.5 | -0.011 | 672.8 | 0.53 | -70.7 | -53.9 | {"2023": -25.3, "2024": -28.2, "2025": 8.8, "2026": -22.3} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| bands (native)|TIME | -16.5 | -0.017 | 952.4 | 0.38 | -45.5 | -26.5 | {"2023": -39.1, "2024": 6.1, "2025": -16.9, "2026": -35.7} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| tape (native)|TIME | -17.3 | -0.018 | 893.8 | 0.44 | -79.0 | 9.6 | {"2023": 37.1, "2024": -31.7, "2025": 11.0, "2026": -51.0} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
| manual|TIME | -18.4 | -0.021 | 980.2 | 0.41 | -3.6 | 31.8 | {"2023": -45.7, "2024": -13.8, "2025": -17.4, "2026": -16.4} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| structure|TIME | -21.4 | -0.030 | 1167.8 | 0.38 | -19.0 | -13.4 | {"2023": -44.2, "2024": -9.2, "2025": -47.7, "2026": 2.4} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5738 | 2473 | 227 | 1.00 | 0 /  /  /  | {"2023": 534.0, "2024": -1080.0, "2025": -3184.0, "2026": 7299.0} |
| 2 | tm20 | barnative.barnative_run.rev | {"n": 2} | sym15u | both | 5614 | 2080 | 613 | 0.50 | 0 /  /  /  | {"2023": -1695.0, "2024": -839.0, "2025": -981.0, "2026": 7113.0} |
| 3 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5529 | 2203 | 230 | 1.00 | 0 /  /  /  | {"2023": 877.0, "2024": 1413.0, "2025": 8.0, "2026": 5170.0} |
| 4 | renko_14 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym15u | both | 5484 | 2321 | 230 | 1.00 | 0 /  /  /  | {"2023": 276.0, "2024": -1123.0, "2025": -2301.0, "2026": 6752.0} |
| 5 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5463 | 2464 | 237 | 1.00 | 0 /  /  /  | {"2023": 821.0, "2024": -731.0, "2025": -822.0, "2026": 5499.0} |
| 6 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5312 | 1946 | 232 | 1.00 | 0 /  /  /  | {"2023": 700.0, "2024": 1874.0, "2025": 1442.0, "2026": 5164.0} |
| 7 | time_s_5 | tape.tape_libvol.adline | {"len": 20} | plain60/60 | both | 5303 | 2868 | 836 | 0.67 | 0 /  /  /  | {"2023": 371.0, "2024": 263.0, "2025": 552.0, "2026": 6708.0} |
| 8 | tm15 | structure.structure_inside.outside | {"cf": 0.6, "filt": 0} | sym15u | both | 5261 | 1540 | 719 | 0.75 | 0 /  /  /  | {"2023": 266.0, "2024": -2665.0, "2025": -2838.0, "2026": 5771.0} |
| 9 | dchg_10 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5243 | 1638 | 244 | 1.00 | 0 /  /  /  | {"2023": 196.0, "2024": -2911.0, "2025": 102.0, "2026": 6078.0} |
| 10 | tm420 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5217 | 2405 | 222 | 1.00 | 0 /  /  /  | {"2023": -371.0, "2024": -149.0, "2025": -9.0, "2026": 6896.0} |
| 11 | swing_atr_0.4 | levels.levels_round.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5128 | 2732 | 264 | 1.00 | 0 /  /  /  | {"2023": -1159.0, "2024": 392.0, "2025": 2022.0, "2026": 5678.0} |
| 12 | swing_atr_0.25 | levels.levels_vwap.break_native | {"n": 2, "k": 0.25} | sym15u | both | 5123 | 2755 | 227 | 1.00 | 0 /  /  /  | {"2023": 286.0, "2024": -707.0, "2025": -1140.0, "2026": 4730.0} |
| 13 | vsess_50 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5120 | 2049 | 223 | 1.00 | 0 /  /  /  | {"2023": -517.0, "2024": 795.0, "2025": -1956.0, "2026": 5273.0} |
| 14 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym20u/10u | both | 5109 | 2777 | 271 | 0.75 | 0 /  /  /  | {"2023": -338.0, "2024": -1054.0, "2025": -1804.0, "2026": 4824.0} |
| 15 | dlt_45 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5001 | 1293 | 230 | 1.00 | 0 /  /  /  | {"2023": 413.0, "2024": -955.0, "2025": -428.0, "2026": 5205.0} |
| 16 | swing_pct_5 | levels.levels_vwap.break_native | {"n": 2, "k": 0.25} | sym15u | both | 4981 | 2178 | 225 | 1.00 | 0 /  /  /  | {"2023": 755.0, "2024": -732.0, "2025": -2215.0, "2026": 4776.0} |
| 17 | dib_240 | tape.tape_delta.fade | {"L": 50, "z": 1.0} | sym15u | both | 4932 | 927 | 723 | 1.00 | 0 /  /  /  | {"2023": -703.0, "2024": 563.0, "2025": -778.0, "2026": 7233.0} |
| 18 | time_s_5 | structure.structure_inside.inside | {"k": 3, "filt": 0} | plain60/60 | both | 4895 | 1124 | 624 | 0.50 | 0 /  /  /  | {"2023": -1135.0, "2024": 75.0, "2025": 1182.0, "2026": 4003.0} |
| 19 | time_s_15 | structure.structure_inside.outside | {"cf": 0.6, "filt": 0} | sym15u | both | 4880 | 940 | 719 | 0.67 | 2 / 595 / 1824 / 1.00 | {"2023": -199.0, "2024": -3558.0, "2025": -2877.0, "2026": 4789.0} |
| 20 | swing_atr_0.15 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 4849 | 1587 | 241 | 1.00 | 0 /  /  /  | {"2023": -52.0, "2024": -3079.0, "2025": -1016.0, "2026": 5789.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 15.5 | 0.007 | 480.9 | 0.49 | 30.8 | 158.1 |  |  |  |  | -5.9 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| agreed | 16.6 | 0.006 | 448.9 | 0.48 | 10.3 | 93.4 |  |  |  |  | -3.9 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -2.1 [no null yet] | 15.1 [no null yet] | -11.5 [no null yet] | 16.7 [no null yet] |
| bands (native) | -21.8 [no null yet] | -7.0 [no null yet] | 39.7 [no null yet] | 13.8 [no null yet] |
| barnative | -7.0 [no null yet] | -17.1 [no null yet] | 26.0 [no null yet] | -8.5 [no null yet] |
| confluence | 13.5 [no null yet] | -5.0 [no null yet] | 53.2 [no null yet] | 12.5 [no null yet] |
| levels | 42.0 [no null yet] | -31.2 [no null yet] | 25.9 [no null yet] | -0.9 [no null yet] |
| levels (native) | 16.4 [no null yet] | 17.5 [no null yet] | 11.4 [no null yet] | -4.9 [no null yet] |
| live | 17.8 [no null yet] | 4.6 [no null yet] | 13.9 [no null yet] | -10.3 [no null yet] |
| manual | -3.7 [no null yet] | 40.1 [no null yet] | -27.0 [no null yet] | 6.6 [no null yet] |
| manual (native) | -61.0 [no null yet] | -58.7 [no null yet] | 4.0 [no null yet] | -4.7 [no null yet] |
| momentum | 9.4 [no null yet] | 1.2 [no null yet] | -14.4 [no null yet] | 54.7 [no null yet] |
| momentum (native) | 7.6 [no null yet] | 14.2 [no null yet] | -9.4 [no null yet] | 48.7 [no null yet] |
| pullback | 20.3 [no null yet] | 22.6 [no null yet] | 37.5 [no null yet] | 16.4 [no null yet] |
| pullback (native) | 32.7 [no null yet] | -4.6 [no null yet] | 33.0 [no null yet] | -21.4 [no null yet] |
| structure | 32.8 [no null yet] | 0.7 [no null yet] | 33.4 [no null yet] | -0.9 [no null yet] |
| structure (native) | 34.7 [no null yet] | 34.3 [no null yet] | 5.2 [no null yet] | 38.2 [no null yet] |
| tape | 5.8 [no null yet] | -13.9 [no null yet] | -0.8 [no null yet] | 22.2 [no null yet] |
| tape (native) | 37.5 [no null yet] | -6.0 [no null yet] | 16.4 [no null yet] | -0.5 [no null yet] |
| trend | -23.4 [no null yet] | -30.3 [no null yet] | 1.3 [no null yet] | -2.4 [no null yet] |
| trend (native) | -20.9 [no null yet] | -10.4 [no null yet] | 5.4 [no null yet] | 44.4 [no null yet] |
| xmarket | 5.3 [no null yet] | -9.9 [no null yet] | -82.9 [no null yet] | -42.2 [no null yet] |
### PASS 1: 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum|TIME | 54.7 | 0.030 | 651.6 | 0.60 | 88.3 | 142.4 | {"2023": 39.3, "2024": 76.3, "2025": 92.8, "2026": -11.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| confluence|PRICE | 53.2 | 0.039 | 537.9 | 0.60 | 77.9 | -79.0 | {"2023": 91.8, "2024": -29.8, "2025": 68.0, "2026": 121.6} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| momentum (native)|TIME | 48.7 | 0.023 | 755.1 | 0.58 | 49.1 | 55.8 | {"2023": 39.3, "2024": 92.1, "2025": 92.8, "2026": -51.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| trend (native)|TIME | 44.4 | 0.018 | 406.5 | 0.56 | 194.8 | 193.8 | {"2023": -2.0, "2024": 15.1, "2025": -7.2, "2026": 154.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "AMBER", "2026": "ok"} |
| levels|ACTIVITY | 42.0 | 0.034 | 764.6 | 0.53 | 64.6 | 10.9 | {"2023": -8.6, "2024": 80.2, "2025": -1.5, "2026": 64.4} |  |  |  | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|INFORMATION | 40.1 | 0.025 | 425.4 | 0.59 | 73.0 | -52.6 | {"2023": 5.5, "2024": 3.9, "2025": 75.2, "2026": 52.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 39.7 | 0.026 | 724.1 | 0.63 | -47.8 | -79.1 | {"2023": 48.9, "2024": 39.6, "2025": 123.7, "2026": -62.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| structure (native)|TIME | 38.2 | 0.025 | 551.9 | 0.59 | 92.4 | 185.9 | {"2023": -14.3, "2024": 13.7, "2025": 59.5, "2026": 58.8} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape (native)|ACTIVITY | 37.5 | 0.025 | 459.3 | 0.57 | 127.4 | 173.3 | {"2023": 0.6, "2024": 23.1, "2025": 70.1, "2026": 27.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|PRICE | 37.5 | 0.024 | 405.5 | 0.48 | 29.7 | 101.9 | {"2023": -32.6, "2024": 38.4, "2025": 44.3, "2026": 50.7} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in NYAM on their live bars (same screen, plain 60/60): K7 tm180 L6M -75.5 pts/wk, rank 5% (top 94.8%); M7 tm60 L6M -8.9 pts/wk, rank 43% (top 57.1%); U7 tm600 L6M -11.4 pts/wk, rank 40% (top 60.4%); P7 tm60 L6M -60.7 pts/wk, rank 9% (top 91.5%); H7 tm60 L6M 28.8 pts/wk, rank 88% (top 11.7%); A7 tm60 L6M -17.2 pts/wk, rank 33% (top 66.8%); O7 tm60 L6M 15.1 pts/wk, rank 79% (top 21.0%). Rank = share of ALL NYAM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum|TIME | 64.0 | 0.036 | 652.1 | 0.60 | 73.4 | 110.2 | {"2023": 39.3, "2024": 84.0, "2025": 121.4, "2026": -19.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|TIME | 63.7 | 0.034 | 745.8 | 0.59 | 49.1 | 55.8 | {"2023": 39.3, "2024": 110.3, "2025": 121.4, "2026": -51.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| bands (native)|TIME | 52.4 | 0.035 | 469.0 | 0.57 | 10.1 | 162.9 | {"2023": 21.9, "2024": -9.4, "2025": 149.5, "2026": 20.3} |  |  |  | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| trend (native)|TIME | 44.3 | 0.013 | 550.3 | 0.49 | 67.2 | 185.4 | {"2023": -35.9, "2024": -47.3, "2025": 127.8, "2026": 79.5} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| trend|TIME | 31.5 | 0.007 | 716.0 | 0.52 | 146.0 | 185.4 | {"2023": -77.2, "2024": -21.0, "2025": 80.0, "2026": 70.8} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| manual|TIME | 23.5 | 0.015 | 850.1 | 0.58 | -0.2 | 317.2 | {"2023": 23.6, "2024": 3.5, "2025": 50.7, "2026": 15.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 15.5 | 0.014 | 615.0 | 0.57 | 92.4 | 185.9 | {"2023": -1.7, "2024": -8.8, "2025": 7.6, "2026": 58.8} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| confluence|TIME | 10.4 | 0.033 | 321.8 | 0.52 | -23.9 | -14.9 | {"2023": 10.4, "2024": 25.7, "2025": 30.4, "2026": -31.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| tape (native)|TIME | 8.9 | 0.001 | 963.3 | 0.51 | 164.5 | 99.6 | {"2023": -30.8, "2024": 1.7, "2025": -72.3, "2026": 126.0} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|TIME | 8.1 | 0.007 | 921.4 | 0.47 | -17.6 | 40.4 | {"2023": 11.1, "2024": 0.2, "2025": 90.6, "2026": -80.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | swing_atr_0.1 | tape.tape_speed.follow_native | {"f": 3.0, "L": 3600} | sym15u | both | 8142 | 2340 | 562 | 1.00 | 0 /  /  /  | {"2023": -2474.0, "2024": -2255.0, "2025": 763.0, "2026": 10386.0} |
| 2 | dib_700 | bands.bands_bollinger.fade | {"n": 30, "k": 2.5} | plain60/60 | both | 7435 | 2353 | 1144 | 1.00 | 0 /  /  /  | {"2023": -1197.0, "2024": -2377.0, "2025": -3514.0, "2026": 4023.0} |
| 3 | time_m_1 | xmarket.xmarket_ym.follow | {"w": 3, "thr": 1.0} | sym8u | both | 7351 | 4294 | 534 | 1.00 | 2 / 1325 / 3387 / 1.00 | {"2023": -1624.0, "2024": 2856.0, "2025": 1532.0, "2026": 5925.0} |
| 4 | tm10 | bands.bands_regchan.break_stderr | {"n": 40, "k": 2.5} | sym8u | both | 7168 | 4001 | 866 | 0.67 | 0 /  /  /  | {"2023": 422.0, "2024": 630.0, "2025": 1668.0, "2026": 2987.0} |
| 5 | mom_10 | tape.tape_delta.fade_native | {"L": 1800, "z": 1.5} | plain60/60 | both | 7160 | 3053 | 1702 | 1.00 | 0 /  /  /  | {"2023": -3242.0, "2024": -508.0, "2025": -9093.0, "2026": 6877.0} |
| 6 | renko_10 | manual.manual_macd.histturn | {"f": 5, "s": 13, "g": 5} | plain60/60 | both | 7125 | 2270 | 1721 | 1.00 | 0 /  /  /  | {"2023": 1069.0, "2024": 1029.0, "2025": -6564.0, "2026": 6771.0} |
| 7 | vol_350 | levels.levels_round.break_native | {"n": 2, "k": 0.25} | sym15u | both | 7094 | 3963 | 495 | 1.00 | 0 /  /  /  | {"2023": -581.0, "2024": 2932.0, "2025": 5800.0, "2026": 6840.0} |
| 8 | cdr_400 | xmarket.xmarket_etf.follow_IWM | {"w": 5, "thr": 1.5} | sym15u | both | 7083 | 1912 | 230 | 1.00 | 0 /  /  /  | {"2023": 0.0, "2024": -297.0, "2025": 17.0, "2026": 7384.0} |
| 9 | dib_240 | momentum.momentum_libosc.mfi | {"len": 7, "lvl": 15} | plain60/60 | both | 7012 | 3214 | 1869 | 1.00 | 0 /  /  /  | {"2023": -1213.0, "2024": -3373.0, "2025": -4932.0, "2026": 7671.0} |
| 10 | cdr_250 | xmarket.xmarket_mega.revert | {"w": 1, "thr": 1.0} | sym15u | both | 6993 | 3548 | 440 | 1.00 | 0 /  /  /  | {"2023": 0.0, "2024": -1272.0, "2025": -1217.0, "2026": 7229.0} |
| 11 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.25} | sym15u | both | 6988 | 2980 | 501 | 1.00 | 0 /  /  /  | {"2023": -467.0, "2024": 3516.0, "2025": 6085.0, "2026": 5453.0} |
| 12 | tick_300 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "body"} | sym15u | both | 6921 | 2452 | 481 | 1.00 | 0 /  /  /  | {"2023": 265.0, "2024": -1109.0, "2025": 2152.0, "2026": 7293.0} |
| 13 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | sym8u | both | 6921 | 2747 | 391 | 1.00 | 0 /  /  /  | {"2023": 231.0, "2024": 57.0, "2025": -1815.0, "2026": 9448.0} |
| 14 | drb_700 | tape.tape_speed.fade_native | {"f": 1.5, "L": 900} | sym15u | both | 6876 | 239 | 554 | 0.50 | 0 /  /  /  | {"2023": -3217.0, "2024": -3592.0, "2025": 3828.0, "2026": 4002.0} |
| 15 | time_m_4 | tape.tape_delta.fade_sm | {"L": 200, "z": 1.0, "sm": 3} | sym8u | both | 6815 | 2643 | 395 | 1.00 | 0 /  /  /  | {"2023": 948.0, "2024": 3089.0, "2025": 1815.0, "2026": 9270.0} |
| 16 | renko_56 | xmarket.xmarket_optflow.revert_nd_SPY | {"w": 5, "thr": 1.5} | sym15u | both | 6800 | 3271 | 332 | 1.00 | 0 /  /  /  | {"2023": 0.0, "2024": 322.0, "2025": 127.0, "2026": 8530.0} |
| 17 | tm10 | bands.bands_regchan.break_stderr_native | {"clk": 10, "k": 2.0} | sym8u | both | 6800 | 3396 | 941 | 0.60 | 0 /  /  /  | {"2023": -124.0, "2024": -2139.0, "2025": -1288.0, "2026": 3503.0} |
| 18 | time_m_4 | tape.tape_delta.fade | {"L": 200, "z": 1.0} | sym8u | both | 6785 | 2965 | 434 | 1.00 | 0 /  /  /  | {"2023": -440.0, "2024": 231.0, "2025": 2951.0, "2026": 9340.0} |
| 19 | swing_pct_5 | structure.structure_level.round_break | {"grid": 100, "buf": 0.25} | sym15u | both | 6784 | 2529 | 496 | 1.00 | 0 /  /  /  | {"2023": -699.0, "2024": 2017.0, "2025": 3592.0, "2026": 10001.0} |
| 20 | vsess_600 | structure.structure_inside.outside | {"cf": 0.75, "filt": 0} | sym15u | both | 6761 | 2752 | 612 | 0.50 | 0 /  /  /  | {"2023": -1701.0, "2024": -2802.0, "2025": 3461.0, "2026": 9458.0} |

## Baseline: the seven live triggers on their live bars (same screen: plain 60/60 bracket, tape fills, measured slippage, $4.84, flat at session end, 1 lot; pts per week)
Live bar per book used here: EXACT live bars: K7 tm180 (3-min), M7 tm60 (1-min), U7 tm600 (10-min), P7 / H7 / A7 / O7 tm60 (engine 1-min bars per W-SWB fidelity); the two time rows either side of each live row are shown as neighbour; weak cells flagged. This is a TRIGGER baseline: no layers, no confluence/conditions.
| session | book | row | kind | L6M pts/wk | L3M pts/wk | since 2023-10 pts/wk | ulcer (wk pts) | persistence | trades L6M | rank (share of all session cells with lower L6M) | weak cell |
|---|---|---|---|---|---|---|---|---|---|---|
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.05 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.98 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.07 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.39 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.10 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.09 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.85 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.86 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.03 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.62 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.32 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.02 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.80 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.80 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.25 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 0.99 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 1.00 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.95 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.91 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.63 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.57 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.28 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.63 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.57 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.81 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.18 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.16 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.85 |  |
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
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.40 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.39 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.56 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.71 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.44 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.09 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.02 | WEAK |
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

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell renko_14 levels.levels_vwap.break_native sym15u L6M 220.7 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell swing_atr_0.1 tape.tape_speed.follow_native sym15u L6M 313.2 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
